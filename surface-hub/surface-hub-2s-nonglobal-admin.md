---
title: Konfigurieren nicht globaler Administratorkonten auf Surface Hub
description: In diesem Artikel wird beschrieben, wie Sie nicht globale Administratorkonten zum Verwalten von Surface Hub und Surface Hub 2S konfigurieren.
keywords: Surface Hub, Surface Hub v1, Surface Hub 2S
ms.prod: surface-hub
ms.sitesec: library
author: greg-lindsay
ms.author: greglin
manager: laurawi
audience: Admin
ms.topic: article
ms.date: 03/22/2021
ms.localizationpriority: Medium
appliesto:
- Surface Hub
- Surface Hub 2S
ms.openlocfilehash: 11170f6c202faef7aa3dddcb8aa8c6fa84bea80f
ms.sourcegitcommit: d020d899e9c7e1eb0b85193ecb0a17a85bb39fe6
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/12/2021
ms.locfileid: "11643861"
---
# <a name="configure-non-global-admin-accounts-on-surface-hub"></a>Konfigurieren nicht globaler Administratorkonten auf Surface Hub

Mit dem Windows 10 Team 2020 Update wird Unterstützung für die Konfiguration von nicht globalen Administratorkonten hinzugefügt, die die Berechtigungen für die Verwaltung der Einstellungen-App auf Surface Hub Geräten einschränken, die mit einer Azure AD-Domäne verbunden sind. Auf diese Weise können Sie Administratorberechtigungen nur für Surface Hub eingrenzen und potenziell unerwünschten Administratorzugriff über eine gesamte Azure AD-Domäne hinweg verhindern. Bevor Sie beginnen, stellen Sie sicher, dass Ihre Surface Hub mit Azure AD verknüpft ist und Intune automatisch registriert ist. Andernfalls müssen Sie Surface Hub zurücksetzen und das Setupprogramm für die erstmalige Out-of-the-Box (OOBE) abschließen und die Option zum Beitritt zu Azure AD auswählen.

## <a name="summary"></a>Zusammenfassung 

Das Erstellen von nicht globalen Administratorkonten umfasst die folgenden Schritte: 

1. Erstellen Sie in Microsoft Intune eine Sicherheitsgruppe mit den Administratoren, die zum Verwalten Surface Hub bestimmt sind.
2. Abrufen der Azure AD-Gruppen-SID mithilfe von PowerShell.
3. Erstellen Sie eine XML-Datei, die die Azure AD-Gruppen-SID enthält.
4. Erstellen Sie eine Sicherheitsgruppe, die die Surface Hub Geräte enthält, die von der Sicherheitsgruppe der nicht globalen Administratoren verwaltet werden.
5. Erstellen Sie ein benutzerdefiniertes Konfigurationsprofil für die Sicherheitsgruppe, die Ihre Surface Hub Geräte enthält. 


## <a name="create-azure-ad-security-groups"></a>Erstellen von Azure AD-Sicherheitsgruppen

Erstellen Sie zunächst eine Sicherheitsgruppe mit den Administratorkonten. Erstellen Sie dann eine weitere Sicherheitsgruppe für Surface Hub Geräte.  

### <a name="create-security-group-for-admin-accounts"></a>Erstellen einer Sicherheitsgruppe für Administratorkonten

1. Melden Sie sich über das [Microsoft Endpoint Manager Admin Center](https://go.microsoft.com/fwlink/?linkid=2109431)bei Intune an, wählen Sie ****  >  **gruppenneue Gruppe** > und wählen Sie unter "Gruppentyp" die Option **"Sicherheit" aus.** 
2. Geben Sie einen Gruppennamen ein, z. **B. Surface Hub lokale Administratoren,** und wählen Sie dann **"Erstellen" aus.** 

     ![Erstellen einer Sicherheitsgruppe für Hubadministratoren](images/sh-create-sec-group.png)

3. Öffnen Sie die Gruppe, wählen Sie **"Mitglieder"** und dann **"Mitglieder hinzufügen"** aus, um die Administratorkonten einzugeben, die Sie als nicht globale Administratoren auf Surface Hub festlegen möchten. Weitere Informationen zum Erstellen von Gruppen in Intune finden Sie unter Hinzufügen von Gruppen zum Organisieren von [Benutzern und Geräten.](/mem/intune/fundamentals/groups-add)

### <a name="create-security-group-for-surface-hub-devices"></a>Erstellen einer Sicherheitsgruppe für Surface Hub Geräte

1. Wiederholen Sie das vorherige Verfahren, um eine separate Sicherheitsgruppe für Hubgeräte zu erstellen. beispielsweise **Surface Hub Geräte.** 

     ![Erstellen einer Sicherheitsgruppe für Hubgeräte](images/sh-create-sec-group-devices.png) 

## <a name="obtain-azure-ad-group-sid-using-powershell"></a>Abrufen der Azure AD-Gruppen-SID mithilfe von PowerShell

1. Starten Sie PowerShell mit erhöhten Kontoberechtigungen (**Als Administrator ausführen),** und stellen Sie sicher, dass Ihr System für die Ausführung von PowerShell-Skripts konfiguriert ist. Weitere Informationen finden Sie unter "Informationen zu [Ausführungsrichtlinien".](/powershell/module/microsoft.powershell.core/about/about_execution_policies?) 
2. [Installieren Sie Azure PowerShell Modul.](/powershell/azure/install-az-ps)
3. Melden Sie sich bei Ihrem Azure AD-Mandanten an.

    ```powershell
    Connect-AzureAD
    ```

4. Wenn Sie bei Ihrem Mandanten angemeldet sind, führen Sie das folgende Commandlet aus. Sie werden aufgefordert, "Geben Sie die Objekt-ID Ihrer Azure AD-Gruppe ein".

    ```powershell
    function Convert-ObjectIdToSid
    {    param([String] $ObjectId)   
         $d=[UInt32[]]::new(4);[Buffer]::BlockCopy([Guid]::Parse($ObjectId).ToByteArray(),0,$d,0,16);"S-1-12-1-$d".Replace(' ','-')
         
    }
    ```

5. Wählen Sie in Intune die Gruppe aus, die Sie zuvor erstellt haben, und kopieren Sie die Objekt-ID, wie in der folgenden Abbildung dargestellt. 

     ![Objekt-ID der Sicherheitsgruppe kopieren](images/sh-objectid.png)

6. Führen Sie das folgende Commandlet aus, um die SID der Sicherheitsgruppe abzurufen:

    ```powershell
    $AADGroup = Read-Host "Please type the Object ID of your Azure AD Group"
    $Result = Convert-ObjectIdToSid $AADGroup
    Write-Host "Your Azure Ad Group SID is" -ForegroundColor Yellow $Result
    ```
    
7. Fügen Sie die Objekt-ID in das PowerShell-Commandlet ein, drücken Sie die **EINGABETASTE,** und kopieren Sie dann die **Azure AD-Gruppen-SID** in einen Text-Editor. 

## <a name="create-xml-file-containing-azure-ad-group-sid"></a>Erstellen einer XML-Datei, die die Azure AD-Gruppen-SID enthält

1. Kopieren Sie Folgendes in einen Text-Editor: 

    ```xml
      <groupmembership>   
      <accessgroup desc = "S-1-5-32-544">        
      <member name = "Administrator" />        
      <member name = "S-1-12-1-XXXXXXXXXX-XXXXXXXXXX-XXXXXXXXXX-XXXXXXXXXX" />  
      </accessgroup>
      </groupmembership>
      ```
      > [!IMPORTANT]
      > Möglicherweise müssen Sie den [lokalisierten Namen für das Administratorkonto](https://social.technet.microsoft.com/wiki/contents/articles/13813.localized-names-for-administrator-account-in-windows.aspx)verwenden. Entfernen Sie das Standardadministratormitglied nicht aus der XML-Datei.

2. Ersetzen Sie die Platzhalter-SID (beginnend mit S-1-12-1) durch Ihre **Azure AD-Gruppen-SID,** und speichern Sie die Datei als XML. Beispielsweise **aad-local-admin.xml**. 

      > [!NOTE]
      > Gruppen sollten zwar über ihre SID angegeben werden, aber wenn Sie Azure-Benutzer direkt hinzufügen möchten, können sie durch Angeben ihres Benutzerprinzipalnamens (User Principal Name, UPN) in folgendem Format hinzugefügt werden: `<member name = "AzureAD\user@contoso.com" />`

## <a name="create-custom-configuration-profile"></a>Erstellen eines benutzerdefinierten Konfigurationsprofils

1. Wählen Sie in **** Endpoint Manager  >  **Gerätekonfigurationsprofile**  >  **Profil erstellen**aus. 
2. Wählen Sie **unter "Plattform" Windows 10 und höher aus.** Wählen Sie unter "Profil" die Option **"Benutzerdefiniert"** und dann **"Erstellen" aus.**
3. Fügen Sie einen Namen und eine Beschreibung hinzu, und wählen Sie dann **"Weiter" aus.**
4. Wählen Sie unter **"Konfigurationseinstellungen**  >  **OMA-URI Einstellungen"** die Option **"Hinzufügen"** aus.
5. Fügen Sie im Bereich "Zeile hinzufügen" einen Namen hinzu, und fügen Sie unter     **OMA-URI**die folgende Zeichenfolge hinzu: 

    ```OMA-URI
    ./Device/Vendor/MSFT/Policy/Config/RestrictedGroups/ConfigureGroupMembership
    ```
6. Wählen Sie unter Datentyp **Zeichenfolgen-XML** aus, und navigieren Sie zum Öffnen der XML-Datei, die Sie im vorherigen Schritt erstellt haben. 

     ![Hochladen der xml-Konfigurationsdatei des lokalen Administrators](images/sh-local-admin-config.png)

7. Klicken Sie auf **Speichern**.
8. Klicken Sie auf **"Gruppen auswählen", um** die [sicherheitsgruppe](#create-security-group-for-surface-hub-devices) einzuschließen und auszuwählen, die Sie zuvor erstellt haben (**Surface Hub Geräte).** Klicken Sie auf **Weiter**.
9. Fügen Sie unter "Anwendbarkeitsregeln" bei Bedarf eine Regel hinzu. Wählen Sie andernfalls **"Weiter"** und dann **"Erstellen"** aus.

Weitere Informationen zu benutzerdefinierten Konfigurationsprofilen mithilfe von OMA-URI-Zeichenfolgen finden Sie unter [Verwenden von benutzerdefinierten Einstellungen für Windows 10 Geräte in Intune.](/mem/intune/configuration/custom-settings-windows-10)


## <a name="non-global-admins-managing-surface-hub"></a>Nicht-globale Administratoren, die Surface Hub verwalten

Mitglieder der **Gruppe "Surface Hub Lokale Administratorensicherheit"** können sich jetzt bei der Einstellungen-App auf Surface Hub anmelden und Einstellungen verwalten.

> [!IMPORTANT]
> Der Standardzugriff globaler Administratoren auf die Einstellungen App wird entfernt (es sei denn, sie sind auch Mitglieder dieser neuen Sicherheitsgruppe).
