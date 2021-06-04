---
title: Konfigurieren der Kenn Wort losen Anmeldung auf Surface Hub
description: Hier erfahren Sie, wie Sie die Anmeldung bei Surface Hub vereinfachen.
keywords: Trennen Sie Werte durch Kommata
ms.prod: surface-hub
ms.sitesec: library
author: greg-lindsay
ms.author: greglin
manager: laurawi
audience: Admin
ms.topic: article
ms.date: 07/21/2020
ms.localizationpriority: Medium
ms.openlocfilehash: 0eaa48200be9ff3c8087530b6dfddeb9aa4620d8
ms.sourcegitcommit: 8738f44f2f4c86e3a45e9fbcbe6469388fc15924
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/22/2020
ms.locfileid: "10893047"
---
# Konfigurieren der kennwortbasierten Anmeldung auf Surface Hub

 
Durch die Kenn Wort lose Anmeldung wird der Zugriff auf Ihre apps, Besprechungen und Dateien vereinfacht. Surface Hub unterstützt die Anmeldung mit der Microsoft Authenticator-APP und den FIDO2-Sicherheitsschlüsseln, die von Ihrer Organisation bereitgestellt werden.

**Wichtig:** Dieser Inhalt ist für Benutzer vorgesehen. Wenn Sie die Kenn Wort lose Anmeldung verwenden möchten, muss Ihr IT-Administrator die kennwortgeschützte Authentifizierung für Ihre Organisation aktivieren. Weitere Informationen finden Sie unter:

- [Aktivieren der Anmeldefunktion für das kennwortgeschützte Telefon](https://docs.microsoft.com/azure/active-directory/authentication/howto-authentication-passwordless-phone)
- [Aktivieren der Kennwortsicherheit bei der Anmeldung](https://docs.microsoft.com/azure/active-directory/authentication/howto-authentication-passwordless-security-key)


##  <a name="configure-sign-in-using-microsoft-authenticator-app"></a>Konfigurieren der Anmeldung mit der Microsoft Authenticator-App

**Hinweis:** Ab Windows 10 Team 2020-Update können Benutzer Ihre bevorzugten e-Mail-Aliase in Azure AD sowie deren Benutzerprinzipalnamen (User Principal Name, UPN) verwenden, um sich mit Microsoft Authenticator zu anmelden. Beispielsweise kann ein Benutzer entweder seinen bevorzugten Alias (John.Doe@contoso.com) oder seinen UPN (jdoe@contoso.com) für die Anmeldung verwenden.
 
Die Microsoft Authenticator-App unterstützt Sie bei der Anmeldung bei Surface Hub mithilfe Ihres mobilen Geräts. So konfigurieren Sie die Anmeldung mit Microsoft Authenticator:


1. Laden Sie die Microsoft Authenticator-App auf Ihrem mobilen Gerät herunter.
    - Google Android: Wechseln Sie auf Ihrem Android-Gerät zu Google Play, um [die Microsoft Authenticator-APP herunterzuladen und zu installieren](https://app.adjust.com/e3rxkc_7lfdtm?fallback=https%3A%2F%2Fplay.google.com%2Fstore%2Fapps%2Fdetails%3Fid%3Dcom.azure.authenticator).
    - Apple ios: Wechseln Sie auf Ihrem Apple IOS-Gerät zum App Store, um [die Microsoft Authenticator-APP herunterzuladen und zu installieren](https://app.adjust.com/e3rxkc_7lfdtm?fallback=https%3A%2F%2Fitunes.apple.com%2Fus%2Fapp%2Fmicrosoft-authenticator%2Fid983156458).
2. Richten Sie auf Ihrem PC [die Microsoft Authenticator-App auf der Seite "Sicherheitsinformationen"](https://docs.microsoft.com/azure/active-directory/user-help/security-info-setup-auth-app#set-up-the-microsoft-authenticator-app-from-the-security-info-page) für Ihr Geschäfts-oder Schulkonto ein.
3. Aktivieren Sie die Microsoft Authenticator-App auf Ihrem mobilen Gerät, [und verwenden Sie die Telefonanmeldung](https://docs.microsoft.com/azure/active-directory/user-help/user-help-auth-app-sign-in#turn-on-and-use-phone-sign-in-for-your-work-or-school-account) für Ihr Geschäfts-oder Schulkonto.

 
##  <a name="configure-sign-in-using-fido2-security-keys"></a>Konfigurieren der Anmeldung mithilfe von FIDO2-Sicherheitsschlüsseln

> [!NOTE]
>  Die Kenn Wort lose Anmeldung auf Surface Hub mithilfe von FIDO2-Sicherheitsschlüsseln erfordert das Windows 10 Team 2020-Update.

> [!IMPORTANT]
> Surface Hub unterstützt nur USB-Sicherheits Tasten.
 
Sie können sich auch mit einem von Ihrer Organisation bereitgestellten FIDO2-Sicherheitsschlüssel bei Surface Hub anmelden. 

###  <a name="to-configure-sign-in-using-a-security-key"></a>So konfigurieren Sie die Anmeldung mit einem Sicherheitsschlüssel:


1. Wechseln Sie auf Ihrem PC zu Ihrer [https://myprofile.microsoft.com/](https://myprofile.microsoft.com/) Seite, und registrieren Sie sich bei Ihrem Firmen-oder Schulkonto.
2. Wählen Sie im linken Navigationsbereich oder über den Link im **Sicherheits Informations** Block **Sicherheitsinformationen** aus, und wählen Sie dann auf der Seite **Sicherheitsinformationen** die Option **Methode hinzufügen** aus.
3. Wählen Sie auf der Seite **Methode hinzufügen** in der Dropdownliste den Eintrag **Sicherheitsschlüssel** aus, und wählen Sie dann **Hinzufügen**aus.
4. Wählen Sie auf der Seite **Sicherheitsschlüssel** die Option **USB-Gerät**aus.
5. Halten Sie Ihren Sicherheitsschlüssel bereit, und wählen Sie **weiter**aus.
6. Befolgen Sie in dem nun angezeigten Dialogfeld die Anweisungen, um den Sicherheitsschlüssel einzufügen, eine PIN zu erstellen oder einzugeben, und führen Sie die erforderliche Geste aus (entweder biometrische oder Fingereingabe).
7. Geben Sie auf der Seite **Sicherheitsschlüssel** Ihrem Sicherheitsschlüssel einen Namen, und wählen Sie dann **weiter**aus.
8. Wählen Sie **Fertig** aus, um den Vorgang abzuschließen.

##  <a name="sign-in-to-surface-hub"></a>Anmelden beim Surface Hub

Nachdem Sie die Kenn Wort lose Anmeldung konfiguriert haben, können Sie Sie verwenden, um den Zugriff auf Ihre apps, Besprechungen und Dateien auf dem Surface Hub zu vereinfachen:

- Nehmen Sie schnell an Ihren Besprechungen Teil und öffnen Sie die zuletzt verwendeten Microsoft 365-Dateien. Weitere Informationen finden Sie unter [**anmelden, um Ihre Besprechungen und Dateien anzuzeigen**](https://support.microsoft.com/help/4506480/sign-in-to-see-your-meetings-and-files-on-surface-hub).
- Sie können sich schnell bei Microsoft-apps wie Whiteboard, PowerPoint, Word, Excel, OneDrive und Power BI anmelden.
- Sie können sich schnell beim neuen Microsoft Edge anmelden, um auf Ihre Favoriten und Browsereinstellungen zuzugreifen. Weitere Informationen finden Sie unter [Installieren und Konfigurieren des neuen Microsoft Edge](surface-hub-install-chromium-edge.md).
- Nachdem Sie sich bei Surface Hub angemeldet haben, können Sie andere apps verwenden, ohne sich erneut anmelden zu müssen, bis Sie **Sitzung beenden**auswählen. Wenn Sie **Sitzung beenden** auswählen, werden Ihre Anmeldeinformationen, Dateien und persönlichen Daten auf dem Gerät gelöscht. Weitere Informationen finden Sie unter [Beenden der Sitzung](finishing-your-surface-hub-meeting.md).


##  <a name="learn-more"></a>Mehr erfahren

- [Kennwortlos-Authentifizierungsoptionen für Azure Active Directory](https://docs.microsoft.com/azure/active-directory/authentication/concept-authentication-passwordless)
- [Kenn Wort lose Anmeldung mit der Microsoft Authenticator-App](https://docs.microsoft.com/azure/active-directory/authentication/howto-authentication-passwordless-phone)
- [Kenn Wort lose Anmeldung mithilfe von FIDO2-Sicherheitsschlüsseln](https://docs.microsoft.com/azure/active-directory/authentication/howto-authentication-passwordless-security-key#user-registration-and-management-of-fido2-security-keys)

