---
title: Registrieren und Konfigurieren von Surface-Geräten mit SEMM (Surface)
description: Erfahren Sie, wie Sie ein Surface -UEFI-Konfigurationspaket erstellen, um die Einstellungen von Surface UEFI zu steuern, und wie Sie ein Surface-Gerät in SEMM registrieren.
keywords: Surface Enterprise Management
ms.prod: w10
ms.mktglfcycl: manage
ms.pagetype: surface, devices, security
ms.sitesec: library
author: coveminer
ms.author: greglin
ms.topic: article
ms.localizationpriority: medium
ms.audience: itpro
ms.reviewer: hachinda
manager: laurawi
ms.date: 1/15/2021
ms.openlocfilehash: f310b4a43a8a0fc0e77295344ac723770ce821bc
ms.sourcegitcommit: 1b86286bd13b13749ddbf454ae78d9a24fec44ee
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/15/2021
ms.locfileid: "11271062"
---
# Registrieren und Konfigurieren von Surface-Geräten mit SEMM

Mit Microsoft Surface Enterprise Management Mode (SEMM) können Sie die Einstellungen von Surface UEFI auf einem Surface-Gerät sicher konfigurieren und diese Einstellungen auf den Geräten mit Surface in Ihrer Organisation verwalten. Wenn ein Surface-Gerät von SEMM verwaltet wird, gilt dieses Gerät als registriert *(manchmal* auch als aktiviert bezeichnet). In diesem Artikel wird beschrieben, wie Sie ein Surface -UEFI-Konfigurationspaket erstellen, das nicht nur die Einstellungen von Surface UEFI steuern, sondern auch ein Surface-Gerät bei SEMM registriert.

Eine übersicht über SEMM finden Sie unter Microsoft Surface [Enterprise Management Mode](https://technet.microsoft.com/itpro/surface/surface-enterprise-management-mode).

Als Alternative zu SEMM unterstützen neuere Surface-Geräte die Remoteverwaltung einer Teilmenge der Firmwareeinstellungen über Microsoft Intune. Weitere Informationen finden Sie unter [Intune-Verwaltung von Surface UEFI-Einstellungen.](surface-manage-dfci-guide.md)

> [!NOTE]
> SEMM wird auf Surface Pro X nur über den UEFI-Manager unterstützt. Weitere Informationen finden Sie unter [Bereitstellen, Verwalten](surface-pro-arm-app-management.md)und Warten von Surface Pro X .

#### Herunterladen und Installieren Microsoft Surface UEFI Configurator

Das tool zum Erstellen von SEMM-Paketen wird Microsoft Surface UEFI Configurator verwendet. Sie können den Microsoft Surface UEFI Configurator von der Seite ["Surface Tools für IT"](https://www.microsoft.com/download/details.aspx?id=46703) im Microsoft Download Center herunterladen.
Führen Sie Microsoft Surface Windows Installer (MSI)-Datei des UEFI-Konfigurators aus, um die Installation des Tools zu starten. Wenn das Installationsprogramm abgeschlossen ist, Microsoft Surface im Abschnitt "Alle Apps" des Startmenüs nach dem UEFI-Konfigurator.

>[!NOTE]
>Microsoft Surface UEFI Configurator wird nur unter Windows 10 unterstützt.

##  <a name="create-a-surface-uefi-configuration-package"></a>Erstellen eines Surface -UEFI-Konfigurationspakets

Das Surface -UEFI-Konfigurationspaket übernimmt sowohl die Rolle des Anwendens einer neuen Konfiguration von Surface -UEFI-Einstellungen auf ein surface-Gerät, das mit SEMM verwaltet wird, als auch die Rolle der Registrierung von Surface-Geräten bei SEMM. Zum Erstellen eines Konfigurationspakets benötigen Sie ein Signaturzertifikat, das mit SEMM verwendet werden muss, um die Konfiguration der UEFI-Einstellungen auf jedem Surface-Gerät zu sichern. Weitere Informationen zu den Anforderungen für das SEMM-Zertifikat finden Sie unter [Microsoft Surface Enterprise Management Mode](https://technet.microsoft.com/itpro/surface/surface-enterprise-management-mode).

Führen Sie die folgenden Schritte aus, um ein Surface -UEFI-Konfigurationspaket zu erstellen:

1. Öffnen Microsoft Surface im Startmenü den UEFI-Konfigurator.
2. Klicken Sie auf **Start**.
3. Klicken **Sie auf "Konfigurationspaket",** wie in Abbildung 1 dargestellt.

   ![Erstellen eines Pakets für die REGISTRIERUNG von SEMM](images/surface-ent-mgmt-fig1-uefi-configurator.png "Create a package for SEMM enrollment")

   *Abbildung1. Auswählen des Konfigurationspakets zum Erstellen eines Pakets für die Registrierung und Konfiguration von SEMM*

4. Klicken **Sie auf "Zertifikatschutz",** um die exportierte Zertifikatdatei mit privatem Schlüssel (PFX) hinzuzufügen, wie in Abbildung 2 dargestellt. Navigieren Sie zum Speicherort Der Zertifikatsdatei, wählen Sie die Datei aus, und klicken Sie dann auf **OK**.

   ![Hinzufügen des SEM-Zertifikats und des Surface -UEFI-Kennworts zum Konfigurationspaket](images/surface-ent-mgmt-fig2-securepackage.png "Add the SEM certificate and Surface UEFI password to configuration package")

   *Abbildung2. Hinzufügen des ZERTIFIKATs und des Surface -UEFI-Kennworts zu einem Surface -UEFI-Konfigurationspaket*

5. Wenn Sie aufgefordert werden, das Zertifikatkennwort zu bestätigen, geben Sie das Kennwort für Ihre Zertifikatdatei ein, bestätigen Sie es, und klicken Sie dann auf **OK**.
6. Klicken **Sie auf "Kennwortschutz",** um Surface UEFI ein Kennwort hinzuzufügen. Dieses Kennwort ist immer dann erforderlich, wenn Sie mit UEFI starten. Wenn dieses Kennwort nicht eingegeben wird, werden nur die **PC-Informationen**, Die Seite **"Info",** **"Unternehmensverwaltung"** und **"Beenden"** angezeigt. Dieser Schritt ist optional.
7. Wenn Sie dazu aufgefordert werden, geben Sie das ausgewählte Kennwort für Surface UEFI ein, bestätigen Sie es, und klicken Sie dann auf **OK.** Wenn Sie ein vorhandenes Surface -UEFI-Kennwort löschen möchten, lassen Sie das Kennwortfeld leer.
8. Wenn Sie nicht möchten, dass das Surface -UEFI-Paket auf ein bestimmtes Gerät angewendet wird, klicken Sie auf der Seite "Surface-Typ **** auswählen" auf den Schieberegler unter dem entsprechenden Surface Book- oder Surface Pro 4-Bild, sodass es sich in der Aus-Position befindet. **** (Wie in Abbildung 3 dargestellt.)
   > [!NOTE] 
   > Sie müssen ein Gerät auswählen, da standardmäßig keines ausgewählt ist.

   ![Auswählen von Geräten für paketkompatibilität](images/surface-semm-enroll-fig3.jpg "Choose devices for package compatibility")

   *Abbildung3. Auswählen der Geräte für die Paketkompatibilität*

9. Klicken Sie auf **Weiter**.
10. Wenn Sie eine Komponente auf verwalteten Surface-Geräten deaktivieren möchten, klicken Sie auf der Seite "Wählen Sie, welche Komponenten Aktiviert oder deaktiviert **** werden soll" auf den Schieberegler neben einem beliebigen Gerät oder einer Gruppe von Geräten, die Sie deaktivieren möchten, damit sich der Schieberegler in der Aus-Position befindet. **** (In Abbildung 4 dargestellt.) Die Standardkonfiguration für jedes Gerät ist **ein .** Klicken Sie **auf die** Schaltfläche "Zurücksetzen", um alle Schieberegler an die Standardposition zurückzusetzen.

    ![Deaktivieren oder Aktivieren von Surface-Komponenten](images/surface-ent-mgmt-fig3-enabledisable.png "Disable or enable Surface components")

    *Abbildung 4. Deaktivieren oder Aktivieren einzelner Surface-Komponenten*

11. Klicken Sie auf **Weiter**.
12. Um erweiterte Optionen auf Surface UEFI oder die Anzeige von Surface **** -UEFI-Seiten zu aktivieren oder zu deaktivieren, klicken **** Sie auf der Seite "Erweiterte Einstellungen für Ihre Geräte auswählen" auf den Schieberegler neben der gewünschten Einstellung, um diese Option auf "Ein" oder "Aus" zu konfigurieren **(siehe** Abbildung 5). Im Abschnitt **"UEFI-Startseite"** können Sie die **** Schieberegler für **Sicherheit,** Geräte und **Start** verwenden, um zu steuern, welche Seiten für Benutzer verfügbar sind, die mit Surface UEFI starten. (Weitere Informationen zu Surface -UEFI-Einstellungen finden Sie unter [Verwalten von Surface -UEFI-Einstellungen.)](https://technet.microsoft.com/itpro/surface/manage-surface-uefi-settings) Klicken **Sie auf "Erstellen",** wenn Sie die Optionen zum Generieren und Speichern des Pakets ausgewählt haben.

    ![Steuern erweiterter Surface -UEFI-Einstellungen und Surface -UEFI-Seiten](images/surface-ent-mgmt-fig4-advancedsettings.png "Control advanced Surface UEFI settings and Surface UEFI pages")

    *Abbildung5. Steuern erweiterter Surface -UEFI-Einstellungen und Surface -UEFI-Seiten mit SEMM*

13. Geben Sie im Dialogfeld "Speichern **unter"** einen Namen für das Surface -UEFI-Konfigurationspaket an, navigieren Sie zu dem Speicherort, an dem Sie die Datei speichern möchten, und klicken Sie dann auf **"Speichern".**
14. Wenn das Paket erstellt und gespeichert wird, wird die Seite **"Erfolgreich"** angezeigt.

>[!NOTE]
>Zeichnen Sie die auf dieser Seite angezeigten Zertifikatfingerabdruckzeichen auf, wie in Abbildung 6 dargestellt. Sie benötigen diese Zeichen, um die Registrierung neuer Surface Geräte in SEMM zu bestätigen. Klicken **Sie auf "Ende",** um die Paketerstellung zu beenden und Microsoft Surface UEFI Configurator zu schließen.

![Anzeigen von Zertifikatfingerabdruckzeichen](images/surface-ent-mgmt-fig5-success.png "Display of certificate thumbprint characters")

*Abbildung6. Die letzten beiden Zeichen des Zertifikatfingerabdrucks werden auf der Seite "Erfolgreich" angezeigt.*

Nachdem Sie das Surface -UEFI-Konfigurationspaket erstellt haben, können Sie die Geräte von Surface registrieren oder konfigurieren.

>[!NOTE]
>Wenn ein Surface -UEFI-Konfigurationspaket erstellt wird, wird auf dem Desktop eine Protokolldatei mit Details zu den Konfigurationspaketeinstellungen und -optionen erstellt.

##  <a name="enroll-a-surface-device-in-semm"></a>Registrieren eines Surface-Geräts in SEMM
Wenn das Surface -UEFI-Konfigurationspaket ausgeführt wird, werden das SEMM-Zertifikat und die Surface -UEFI-Konfigurationsdateien im Firmwarespeicher des Surface-Geräts mehrstufige. Beim Neustart des Surface-Geräts verarbeitet Surface UEFI diese Dateien und beginnt mit dem Anwenden der Surface -UEFI-Konfiguration oder der Registrierung des Surface-Geräts in SEMM, wie in Abbildung 7 dargestellt.

![SEMM-Prozess für die Konfiguration von Surface UEFI oder Registrierung](images/surface-semm-enroll-fig7.png "SEMM process for configuration of Surface UEFI or enrollment")

*Abbildung7. Der SEMM-Prozess für die Konfiguration von Surface UEFI oder die Registrierung eines Surface-Geräts.*

Bevor Sie mit der Registrierung eines Surface-Geräts bei SEMM beginnen, stellen Sie sicher, dass sie die letzten beiden Zeichen des Zertifikatfingerabdrucks zur Hand haben. Sie benötigen diese Zeichen, um die Registrierung des Geräts zu bestätigen (siehe Abbildung 6).

Führen Sie die folgenden Schritte aus, um ein Surface-Gerät bei SEMM mit einem Surface -UEFI-Konfigurationspaket zu registrieren:

1. Führen Sie die Surface -UEFI-Konfigurationspaket-MSI-Datei auf dem Surface-Gerät aus, das Sie bei SEMM registrieren möchten. Dadurch wird die Surface -UEFI-Konfigurationsdatei in der Firmware des Geräts bereitgestellt.
2. Aktivieren Sie **das Kontrollkästchen** "Ich akzeptiere die Bedingungen im Lizenzvertrag", **** um den Endbenutzer-Lizenzvertrag zu akzeptieren, und klicken Sie dann auf "Installieren", um den Installationsvorgang zu starten.
3. Klicken **Sie auf "Fertig** stellen", um die Installation des Surface -UEFI-Konfigurationspakets abzuschließen, und starten Sie das Surface-Gerät neu, wenn Sie dazu aufgefordert werden.
4. Surface UEFI wird die Konfigurationsdatei laden und feststellen, dass SEMM auf dem Gerät nicht aktiviert ist. Surface UEFI startet dann den SEMM-Registrierungsprozess wie folgt:
   * Surface UEFI überprüft, ob die SEMM-Konfigurationsdatei ein SEMM-Zertifikat enthält.
   * Surface UEFI fordert Sie zur Eingabe der letzten beiden Zeichen des Zertifikatfingerabdrucks auf, um die Registrierung des Surface-Geräts in SEMM zu bestätigen, wie in Abbildung 8 dargestellt.

      ![Für die REGISTRIERUNG von SEMM sind die letzten beiden Zeichen des Zertifikatfingerabdrucks erforderlich.](images/surface-semm-enroll-fig8.png "SEMM enrollment requires last two characters of certificate thumbprint")

      *Abbildung8. Für die Registrierung bei SEMM sind die letzten beiden Zeichen des Zertifikatfingerabdrucks erforderlich.*

   * Surface UEFI speichern das ZERTIFIKAT in der Firmware und wenden die Konfigurationseinstellungen an, die in der Surface -UEFI-Konfigurationsdatei angegeben sind.
   
5. Das Surface-Gerät ist jetzt in SEMM registriert und wird mit Windows gestartet.

Sie können überprüfen, ob ein Surface-Gerät erfolgreich bei **** SEMM registriert wurde, indem Sie in der Ereignisanzeige nach einem Microsoft Surface-Konfigurationspaket **(wie** in Abbildung 9 dargestellt) oder in den ereignissen suchen, die im **Microsoft Surface -UEFI-Konfiguratorprotokoll** gespeichert sind( siehe Anwendungs- und Dienstprotokolle **in** der Ereignisanzeige).

![Überprüfen der Registrierung des Surface-Geräts in SEMM in "Programme und Features"](images/surface-semm-enroll-fig9.png "Verify enrollment of Surface device in SEMM in Programs and Features")

*Abbildung9. Überprüfen der Registrierung eines Surface-Geräts in SEMM in "Programme und Features"*

![Überprüfen der Registrierung des Surface-Geräts in SEMM in der Ereignisanzeige](images/surface-semm-enroll-fig10.png "Verify enrollment of Surface device in SEMM in Event Viewer")

*Abbildung10. Überprüfen der Registrierung eines Surface-Geräts in SEMM in der Ereignisanzeige*

Sie können auch überprüfen, ob das Gerät in SEMM auf Surface UEFI registriert ist– **** Während das Gerät registriert ist, enthält Surface UEFI die Enterprise-Verwaltungsseite (wie in Abbildung 11 dargestellt).

![Surface UEFI Enterprise -Verwaltungsseite](images/surface-semm-enroll-fig11.png "Surface UEFI Enterprise management page")

*Abbildung11. Die Verwaltungsseite von Surface UEFI Enterprise*


##  <a name="configure-surface-uefi-settings-with-semm"></a>Konfigurieren von Surface -UEFI-Einstellungen mit SEMM

Nachdem ein Gerät bei SEMM registriert wurde, können Sie Surface -UEFI-Konfigurationspakete ausführen, die mit demselben SEMM-Zertifikat signiert sind, um neue Surface -UEFI-Einstellungen anzuwenden. Diese Einstellungen werden automatisch angewendet, wenn das Gerät das nächste Mal gestartet wird, ohne dass der Benutzer eine Interaktion vor sich hat. Mithilfe von Anwendungsbereitstellungslösungen wie Microsoft Endpoint Configuration Manager können Sie Surface -UEFI-Konfigurationspakete auf Surface-Geräten bereitstellen, um die Einstellungen in Surface UEFI zu ändern oder zu verwalten.

Weitere Informationen zum Bereitstellen von Windows Installer (MSI)-Dateien mit Configuration Manager finden Sie unter Bereitstellen und Verwalten von Anwendungen [mit Microsoft Endpoint Configuration Manager.](https://technet.microsoft.com/library/mt627959)

Wenn Sie Surface UEFI mit einem Kennwort gesichert haben, werden Benutzern ohne Kennwort, die versuchen, **** surface UEFI zu starten, nur die **PC-Informationen**, **Informationen,** Enterprise-Verwaltung und Beendigungsseiten angezeigt. ****

Wenn Sie Surface UEFI nicht mit einem Kennwort gesichert haben oder ein Benutzer das Kennwort richtig einzugeben hat, werden die mit SEMM konfigurierten Einstellungen abgeblendet (nicht verfügbar) und der Text einige Einstellungen werden von Ihrer Organisation verwaltet, wie in Abbildung 12 dargestellt.

![Von SEMM verwaltete Einstellungen, die auf Surface UEFI deaktiviert sind](images/surface-semm-enroll-fig12.png "Settings managed by SEMM disabled in Surface UEFI")

*Abbildung 12 Einstellungen, die von SEMM verwaltet werden, werden auf Surface UEFI deaktiviert.*
