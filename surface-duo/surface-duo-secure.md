---
title: Surface Duo – Sicherheitsübersicht
description: In diesem Artikel wird erläutert, wie Surface Duo Sicherheit auf einem mobilen Gerät auf Unternehmensstufe über das Betriebssystem Android und die von Microsoft entwickelt UEFI bietet.
ms.technology: windows
ms.prod: surface
ms.mktglfcycl: manage
ms.sitesec: library
author: coveminer
ms.author: greglin
ms.topic: article
ms.date: 8/12/2020
ms.reviewer: karand
manager: laurawi
ms.audience: itpro
audience: ITPro
ms.localizationpriority: medium
appliesto:
- Surface Duo
ms.openlocfilehash: 91eb893dbdc6dae93cf402a602b64a83309388e8
ms.sourcegitcommit: 37e0994e2b8ae62b0352b016b698edcc7ca500fb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/10/2021
ms.locfileid: "11326174"
---
# Surface Duo – Sicherheitsübersicht

Surface Duo verfügt über integrierten Schutz auf jeder Ebene mit tief integrierter Hardware, Firmware und Software, um Ihre Geräte, Identitäten und Daten zu schützen. Als Android 10-Gerät nutzt Surface Duo Android-Sicherheitsfeatures auf Betriebssystemebene und auf der Ebene der Google-Dienste. Das Betriebssystem Android nutzt herkömmliche Steuerelemente für die Betriebssystemsicherheit, um Benutzerdaten und Systemressourcen zu schützen, schützt die Geräteintegrität vor Schadsoftware und bietet Anwendungsisolation. Darüber hinaus stellt Google über dem Betriebssystem eine Reihe von Diensten zur Verfügung, die in Kombination mit der Sicherheit des Android-Betriebssystems dazu beitragen, den Benutzer von Android kontinuierlich zu schützen.

- **Custom engineered UEFI.** Einzigartig für Surface Duo unter Android-Geräten ist die benutzerdefinierte Unified Extensible Firmware Interface (UEFI) von Microsoft, die die vollständige Kontrolle über Firmwarekomponenten ermöglicht. Microsoft bietet Sicherheit auf Unternehmensstufe für Surface Duo, indem jede Zeile von Firmwarecode im Unternehmen geschrieben oder überprüft wird, sodass Microsoft direkt und agil auf potenzielle Firmwarebedrohungen reagieren und Sicherheitsrisiken der Lieferkette mindern kann.
- **Überprüfter Start.** Ab der Hardwareebene bei der Anmeldung ist der überprüfte Start bestrebt, sicherzustellen, dass ausgeführter Code nur von einer vertrauenswürdigen Quelle stammt. Es richtet eine vollständige Vertrauenskette ein – vom hardwaregeschützten Vertrauensstamm über das Startladegerät, die Startpartition und andere überprüfte Partitionen. Wenn Surface Duo gestartet wird, überprüft jede Stufe die Integrität und Authentizität der nächsten Stufe, bevor die Ausführung übergaben wird.
- **App-Trennung.** Das Anwendungs-Sandboxing isoliert und wehrt Android-Apps, um zu verhindern, dass schädliche Apps auf private Informationen zugreifen. Obligatorische, immer aktivierende Verschlüsselung und Schlüsselverarbeitung schützen Daten während der Übertragung und im Ruhefall – auch wenn Geräte in die falschen Hände geraten. Die Verschlüsselung ist durch Keystoreschlüssel geschützt, die kryptografische Schlüssel in einem Container speichern, wodurch das Extrahieren von einem Gerät erschwert wird.
- **Google Play Protect.** Auf der Softwareebene verwendet Surface Duo die Bedrohungserkennung Google Play Protect, die alle Anwendungen überprüft, einschließlich öffentlicher Apps von Google Play, von Microsoft und Netzbetreibern aktualisierter System-Apps und sideloaded-Apps.
- **Microsoft Defender ATP.** Die Antiviren- und Schadsoftware der Unternehmensklasse für Windows 10 ist jetzt für Android-Geräte verfügbar, die von Intune verwaltet werden. Weitere Informationen finden Sie unter [Microsoft Defender ATP für Android.](https://docs.microsoft.com/windows/security/threat-protection/microsoft-defender-atp/microsoft-defender-atp-android) 


##  <a name="mobile-device-management-security"></a>Verwaltung mobiler Geräte

Surface Duo wird in einer Unternehmensumgebung mithilfe einer Enterprise Mobility Management (EMM)-Lösung gesichert, die einen konsistenten Satz von Schutztools, Technologien und bewährten Methoden bietet, die Sie an Ihre Organisatorischen und Complianceanforderungen anpassen können. Eine breite Palette von Verwaltungs-APIs bietet it-Abteilungen tools, um Datenlecks zu verhindern und compliance in einer Vielzahl von Szenarien durchzusetzen. Die Unterstützung mit mehreren Profilen und Geräteverwaltungsoptionen ermöglichen die Trennung von Arbeits- und personenbezogenen Daten, um Unternehmensdaten zu schützen.

Die Sicherheit von MDM baut auf einer erweiterten Reihe von Konfigurationstechnologien auf, mit denen Benutzer unterwegs produktiv arbeiten und gleichzeitig kritisches geistiges Eigentum des Unternehmens schützen können. Dazu gehören App-Schutzrichtlinien, Geräteeinschränkungsrichtlinien und verwandte Technologien, mit denen Sie bestimmte Ziele in Abhängigkeit von Ihrer Umgebung erreichen können – unabhängig davon, ob Ihr Unternehmen aus der Bereitstellung von Restaurantbestellungen, der Verwaltung von IT-Diensten für Filialen oder dem Umgang mit vertraulichen nationalen Sicherheitsinformationen besteht. 

Sie können beispielsweise die Geräteauthentifizierung stärken, indem Sie die Benutzer zur Eingabe einer 6-stelligen alphanumerischen Pin zusammen mit der 2-Faktor-Authentifizierung verlangen.  Sie können die Geräte einschränken, die Benutzer registrieren können, um sicherzustellen, dass Sie die Lizenzbeschränkungen einhalten oder den Zugriff auf "jailbroken"-Telefone oder andere nicht unterstützte Gerätetypen vermeiden.
Intune und andere EMMs bieten Organisationen die Flexibilität, Geräte entsprechend ihren Anforderungen zu verwalten.

##  <a name="app-protection-policies"></a>Richtlinien zum Schutz von Apps

App-Schutz-Richtlinien (APP) sind Regeln, die sicherstellen, dass die Daten einer Organisation sicher oder in einer verwalteten App enthalten bleiben. Eine Richtlinie kann eine Regel sein, die erzwungen wird, wenn der Benutzer versucht, auf "Unternehmensdaten" zu zugreifen oder diese zu verschieben, oder eine Reihe von Aktionen, die verboten oder überwacht werden, wenn sich der Benutzer innerhalb der App befindet. Eine verwaltete App ist eine App, auf die App-Schutzrichtlinien angewendet wurden und die von Intune verwaltet werden kann.

Mit Richtlinien zum Schutz von Apps können Sie die Daten Ihrer Organisation innerhalb einer Anwendung verwalten und schützen. Viele Produktivitäts-Apps, wie Microsoft Office Apps, können von Intune MAM verwaltet werden. Sehen Sie sich die offizielle Liste der [microsoft Intune-geschützten Apps an,](https://docs.microsoft.com/mem/intune/apps/apps-supported-intune-apps) die für die öffentliche Verwendung verfügbar sind.

##  <a name="security-considerations-for-managing-surface-duo"></a>Sicherheitsüberlegungen für die Verwaltung von Surface Duo

Die wachsende Anzahl von Richtlinieneinstellungen, die in Lösungen für die Verwaltung mobiler Geräte verfügbar sind, ermöglicht Es Organisationen, die Schutzebenen an ihre spezifischen Anforderungen anzupassen. Um Organisationen bei der Priorisierung von Sicherheitseinstellungen für Surface Duo (oder ein anderes Android-Gerät) zu unterstützen, hat Intune sein Sicherheitskonfigurationsframework für [Android Enterprise](https://docs.microsoft.com/mem/intune/enrollment/android-configuration-framework) eingeführt, das in mehrere unterschiedliche Konfigurationsszenarien organisiert ist und Anleitungen für Arbeitsprofil- und vollständig verwaltete Szenarien bietet.
 

| Sicherheitsstufe                                                                                                       | Ziel                                                                                                                                                                      | Zusammenfassung                                                                                                                                                                                     | Einstellungsinformationen                                                                                                                                                                                                                                     |
| -------------------------------------------------------------------------------------------------------------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Grundlegende Sicherheit für Arbeitsprofile – Ebene 1                                                                                | Persönliche Geräte mit Zugriff auf Arbeits- oder Schuldaten.                                                                                                                             | Führt Kennwortanforderungen ein, trennt Arbeits- und personenbezogene Daten und überprüft den Android-Geräte-Nachweis.                                                                               | [Einstellungen der Arbeitsprofilebene 1](https://microsoft.sharepoint.com/teams/EpsilonAdminGuide/Shared%20Documents/General/•%09https:/docs.microsoft.com/mem/intune/enrollment/android-work-profile-security-settings#work-profile-basic-security) |
| Hohe Arbeitsprofilsicherheit – Ebene 3<br>(Aufgrund von Frameworkkonventionen ist dies die nächste Ebene über Ebene 1.)<br> ** | Geräte, die von Benutzern oder Gruppen mit einem eindeutig hohen Risiko verwendet werden. Beispielsweise benutzer, die hochgradig vertrauliche Daten verarbeiten, wenn die nicht autorisierte Offenlegung erheblichen Materialverlust verursacht. | Führt die mobile Bedrohungsabwehr oder Microsoft Defender ATP ein, legt die Mindestversion von Android auf 8.0 fest, setzt stärkere Kennwortrichtlinien und schränkt die Arbeits- und persönliche Trennung weiter ein. | [Einstellungen für Arbeitsprofilebene 3](https://docs.microsoft.com/mem/intune/enrollment/android-work-profile-security-settings#work-profile-high-security)                                                                                         |
| Vollständig verwaltete Grundlegende Sicherheit –Stufe 1                                                                                | Mindestsicherheitskonfiguration für ein Unternehmensgerät, gilt für die meisten mobilen Benutzer, die auf Arbeits- oder Schuldaten zugreifen.                                                          | Führt Kennwortanforderungen ein, legt die Mindestversion von Android auf 8.0 fest und setzt bestimmte Geräteeinschränkungen fest.                                                                          | [Einstellungen der vollständig verwalteten Ebene 1](https://docs.microsoft.com/mem/intune/enrollment/android-fully-managed-security-settings#fully-managed-basic-security)                                                                                     |
| Vollständig verwaltete erweiterte Sicherheitsstufe 2                                                                              | Geräte, auf denen Benutzer auf vertrauliche oder vertrauliche Informationen zugreifen.                                                                                                                | Erlässt stärkere Kennwortrichtlinien und deaktiviert Benutzer-/Kontofunktionen.                                                                                                                   | [Vollständig verwaltete Ebene 2-Settngs](https://docs.microsoft.com/mem/intune/enrollment/android-fully-managed-security-settings#fully-managed-enhanced-security)                                                                                   |
| Vollständig verwaltete hohe Sicherheitsstufe 3                                                                                  | Geräte, die von Benutzern oder Gruppen mit einem eindeutig hohen Risiko verwendet werden. Beispielsweise benutzer, die hochgradig vertrauliche Daten verarbeiten, wenn die nicht autorisierte Offenlegung erheblichen Materialverlust verursacht. | Erhöht die Mindestversion von Android auf 10.0, führt eine mobile Bedrohungsabwehr oder Microsoft Defender ATP ein und erzwingt zusätzliche Geräteeinschränkungen.                                     | [Vollständig verwaltete Einstellungen der Stufe 3](https://docs.microsoft.com/mem/intune/enrollment/android-fully-managed-security-settings#fully-managed-high-security)                                                                                      |
 
Wie bei jedem Framework müssen Einstellungen innerhalb einer entsprechenden Ebene möglicherweise basierend auf den Anforderungen der Organisation angepasst werden, da die Sicherheit die Bedrohungsumgebung, die Risikobereitschaft und die Auswirkungen auf die Benutzerfreundlichkeit bewerten muss.
 
 
**Weitere Informationen**


- [Android Enterprise Security Configuration Framework](https://docs.microsoft.com/mem/intune/enrollment/android-configuration-framework)
- [Übersicht über App-Schutzrichtlinien](https://docs.microsoft.com/mem/intune/apps/app-protection-policy)
- [Richtlinieneinstellungen für den Schutz von Android-Apps in Microsoft Intune](https://docs.microsoft.com/mem/intune/apps/app-protection-policy-settings-android)
- [Festlegen von Registrierungseinschränkungen](https://docs.microsoft.com/mem/intune/enrollment/enrollment-restrictions-set)
- [Whitepaper "Android Enterprise Security"](https://static.googleusercontent.com/media/www.android.com/en//static/2016/pdfs/enterprise/Android_Enterprise_Security_White_Paper_2019.pdf)
 