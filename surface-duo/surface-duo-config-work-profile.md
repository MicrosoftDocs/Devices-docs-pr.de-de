---
title: Konfigurieren des Android Enterprise-Arbeitsprofils für Surface Duo
description: In diesem Artikel wird das Einrichten eines Arbeitsprofils auf Surface Duo erläutert.
ms.technology: windows
ms.prod: surface
ms.mktglfcycl: manage
ms.sitesec: library
author: coveminer
ms.author: greglin
ms.topic: article
ms.date: 9/25/2020
ms.reviewer: karand
manager: laurawi
ms.audience: itpro
audience: ITPro
ms.localizationpriority: medium
appliesto:
- Surface Duo
ms.openlocfilehash: 393844a4e4f0f06f16d11d1313ec9aacfa109d57
ms.sourcegitcommit: 37e0994e2b8ae62b0352b016b698edcc7ca500fb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/10/2021
ms.locfileid: "11326175"
---
# Konfigurieren des Android Enterprise-Arbeitsprofils für Surface Duo

Arbeitsprofile, die auf die Bereitstellung von BYOD ausgerichtet sind, bieten auf Duo einen separaten Platz für Arbeits-Apps und -Daten, damit Organisationen die vollständige Kontrolle über ihre Daten, Apps und Sicherheitsrichtlinien haben, ohne dass Mitarbeiter ihr Gerät für persönliche Apps und Daten verwenden können.

###  <a name="set-up-android-enterprise-work-profile"></a>Einrichten des Android Enterprise-Arbeitsprofils

Verwenden Sie Arbeitsprofile zum Verwalten von Unternehmensdaten und Apps auf Geräten im Besitz des Benutzers. Standardmäßig ist die Registrierung von persönlichen Arbeitsprofilgeräten aktiviert und erfordert keine weitere Administratorkonfiguration.  

**So aktivieren Sie das Unternehmensarbeitsprofil:**

- Wählen Sie im **** Endpunkt-Manager  >  **"Geräte Android**  >  **Android-Registrierung"** und dann **"Persönliche Geräte mit Arbeitsprofil" aus.**
<br><br>
 ![Aktivieren des Unternehmensarbeitsprofils](images/enroll-start.png)

 
**Anmelden bei Surface Duo mit dem Android Enterprise Work Profile**

1. Installieren Sie die Unternehmensportal-App aus dem Google Play Store, und melden Sie sich mit Ihrem Microsoft-Firmen- oder Schulkonto an.<br><br>
![Anmelden bei Surface Duo](images/duo-wp-1.png)
 
2. Wählen Sie auf der Seite "Access-Setup" die Option **"Beginnen" aus.**<br><br>
![Begin](images/duo-wp-2.png)

3. Überprüfen Sie die Informationen auf der Seite "Datenschutz", und wählen Sie **"Weiter" aus.**<br><br>
 ![Weiter](images/duo-wp-3.png)
<br><br>
 ![Wählen Sie "Weiter" aus.](images/duo-wp-4.png)
 
4. Wenn das Setup des Arbeitsprofils abgeschlossen ist, wählen **Sie "Weiter** aktivieren" aus, und registrieren Sie das Gerät.<br><br>
 ![Wählen Sie "Weiter aktivieren" aus, und registrieren Sie das Gerät.](images/duo-wp-5.png)

5. Wählen Sie **Weiter** aus.<br><br>
 ![Wählen Sie erneut "Weiter" aus.](images/duo-wp-6.png)

6. Wenn Sie das Arbeitsprofil aktiviert haben, wählen **Sie "Weiter** zum Aktualisieren der Geräteeinstellungen" aus. In diesem Beispiel wendet das Arbeitsprofil eine MDM-Einstellung an, um ein stärkeres alphanumerisches Kennwort mit 6 Ziffern zu erfordern. <br><br>

     ![Beispiel für ein alphanumerisches Kennwort](images/duo-wp-7.png)<br><br>
7. Wählen **Sie "Auflösen"** aus, um die erforderliche Authentifizierung ein, und wählen Sie dann **"Weiter,** um die Einrichtung des Arbeitsprofils abzuschließen" aus. <br><br>
     ![Select continue to complete setup](images/duo-wp-8.png)<br><br>
     ![Abschließen des Setups](images/duo-wp-9.png)<br><br>

##  <a name="additional-information"></a>Weitere Informationen

- [Einrichten der Registrierung von Android Enterprise-Arbeitsprofilgeräten](https://docs.microsoft.com/mem/intune/enrollment/android-work-profile-enroll)

