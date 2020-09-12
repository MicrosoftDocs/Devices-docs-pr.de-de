---
title: Betriebssystem-Grundlagen (Surface Hub)
description: In diesem Thema werden die eindeutigen Aspekte des Windows 10-Team Betriebssystems und die Unterschiede zu Windows 10 Enterprise erläutert.
keywords: Änderungsverlauf
ms.prod: surface-hub
ms.sitesec: library
author: dansimp
ms.author: dansimp
ms.topic: article
ms.date: 09/11/2020
ms.reviewer: ''
manager: laurawi
ms.localizationpriority: medium
ms.openlocfilehash: cae09fa3a21fe497d021f38621085b639b15c4da
ms.sourcegitcommit: ae0dae16e0b7bb9c906de78095634c3070a58c61
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/11/2020
ms.locfileid: "11013405"
---
# Betriebssystem-Grundlagen (Surface Hub)

Das Surface Hub-Betriebssystem Windows10 Team basiert auf Windows10 Enterprise und bietet umfassende Unterstützung für Unternehmensverwaltung, Sicherheit und weitere Features. Dennoch gibt es wichtige Unterschiede zwischen den beiden Betriebssystemen. Während die Enterprise-Edition für PCs entwickelt wurde, ist Windows 10 Team von Grund auf für Großbildschirme und Konferenzräume konzipiert. Bei der Evaluierung der Sicherheits- und Verwaltungsanforderungen empfiehlt es sich daher, das Surface Hub-Betriebssystem als vollständig neues Betriebssystem zu betrachten. Dieser Artikel befasst sich mit den wesentlichen Unterschieden zwischen Windows 10 Team auf Surface Hub und Windows 10 Enterprise sowie den Auswirkungen auf Ihre Organisation.

Ab September 2020 haben Kunden die Möglichkeit, auf Surface Hub 2S zu Windows 10 pro oder Enterprise zu migrieren. Weitere Informationen hierzu finden Sie unter den folgenden Themen:

- [Ankündigung der Verfügbarkeit von Windows 10 pro und Enterprise auf Surface Hub 2](https://techcommunity.microsoft.com/t5/surface-it-pro-blog/announcing-the-availability-of-windows-10-pro-and-enterprise-on/ba-p/1624107).

- [Migrieren zu Windows 10 Pro oder Enterprise auf Surface Hub 2](surface-hub-2s-migrate-os.md)

## Benutzeroberfläche

### Shell (Betriebssystem-Benutzeroberfläche)

Die Surface Hub-Shell wurde von Grund auf für Großbildschirme entwickelt und für die Touchbedienung optimiert. Die Shell ist nicht identisch mit der von Windows10 Enterprise.

*Mögliche Auswirkungen auf Richtlinien Ihrer Organisation:* <br> Die Einstellungen für Steuerelemente in der Windows 10 Enterprise-Shell gelten nicht für Surface Hub.

### Sperrbildschirm und Bildschirmschoner

Surface Hub verfügt über keinen Sperrbildschirm oder Bildschirmschoner, sondern über ein ähnliches Feature mit dem Namen Willkommensseite. Auf der Willkommensseite werden geplante Besprechungen aus dem Kalender des Gerätekontos angezeigt und sie bietet einfachen Zugang zu den Top-Apps von Surface Hub wie Skype for Business, Whiteboard und Verbinden.

*Mögliche Auswirkungen auf Richtlinien Ihrer Organisation:* <br> Einstellungen für Sperrbildschirm, Bildschirmtimeout und Bildschirmschoner gelten nicht für Surface Hub.

### Benutzeranmeldung

Surface Hub ist für die Nutzung in gemeinschaftlichen Bereichen, z. B. Konferenzräumen, ausgelegt. Im Unterschied zu Windows-PCs kann jeder Surface Hub nutzen, ohne sich anzumelden. Zum Aktivieren dieser Community-Funktion unterstützt Surface Hub keine Windows-Anmeldung in der Weise wie Windows10 Enterprise (z.B. Anmelden eines Benutzers am Betriebssystem und verwenden Sie dieser Anmeldeinformationen im gesamten Betriebssystem). Stattdessen wird immer ein lokaler, automatisch angemeldeter, mit geringen Rechten ausgestatteter Benutzer verwendet. Das Anmelden weiterer Benutzer, einschließlich Administratoren, wird nicht unterstützt (z.B. wenn sich ein Administrator anmeldet, ist die nicht am Betriebssystem angemeldet).

Benutzer können sich bei Surface Hub anmelden, aber sie werden nicht im Betriebssystem angemeldet. Wenn sich beispielsweise ein Benutzer für Apps oder Meine Besprechungen und Dateien anmeldet, wird der Benutzer für die Apps oder Dienste angemeldet, aber nicht beim Betriebssystem. Daher kann der angemeldeten Benutzer Cloud-Dateien und persönlichen Besprechungen in der Cloud abrufen und diese Anmeldeinformationen werden verworfen. wenn **Sitzung beenden** aktiviert ist.


*Mögliche Auswirkungen auf Richtlinien Ihrer Organisation:* <br> Statt der Benutzerzugriffssteuerung verwendet Surface Hub normalerweise Sperrmodusfeatures, um die Sicherheit durchzusetzen. Richtlinien für Kennwortanforderungen, interaktive Anmeldung, Benutzerkonten und Zugriffssteuerung gelten nicht für Surface Hub.

### Speichern und Durchsuchen von Dateien

Die Benutzer haben Zugriff auf eine begrenzte Zahl von Verzeichnissen auf dem Surface Hub:
- Musik
- Videos
- Dokumente
- Bilder
- Downloads

Die lokal in diesen Verzeichnissen gespeicherten Dateien werden gelöscht, wenn der Benutzer **Sitzung beenden** drückt. Zum Speichern von Inhalten, die während einer Besprechung erstellt wurden, sollten Benutzer Dateien auf einem USB-Laufwerk oder auf OneDrive ablegen.

*Mögliche Auswirkungen auf Richtlinien Ihrer Organisation:* <br> Richtlinien in Zusammenhang mit Zugriffsberechtigungen und dem Besitz von Dateien und Ordnern gelten nicht für Surface Hub. Dateien können von Benutzern nicht durchsucht und nicht in Systemverzeichnissen und Netzwerkordnern gespeichert werden.

## Anwendungen

### Standardanwendungen

Die Standard-Apps für die universelle Windows-Plattform (UWP) auf dem Surface Hub sind mit wenigen Ausnahmen auch für Windows10-PCs verfügbar.

Auf Surface Hub vorinstallierte UWP-Apps:
- Alarm & Uhr
- Rechner
- Verbinden
- Excel Mobile
- Feedback-Hub
- Datei-Explorer*
- Erste Schritte
- Karten
- Microsoft Edge
- Microsoft Power BI
- OneDrive
- Fotos
- PowerPoint Mobile
- Einstellungen*
- Skype for Business*
- Store
- Whiteboard*
- Word Mobile

*Die mit einem Sternchen (&ast;) gekennzeichneten Apps gelten ausschließlich für Surface Hub.*

*Mögliche Auswirkungen auf Richtlinien Ihrer Organisation:* <br> Verwenden Sie Richtlinien für Windows10 Enterprise, um die Features und Netzwerkanforderungen für Standard-Apps auf dem Surface Hub zu ermitteln.

### Installieren von Apps, Treibern und Diensten

Damit das Appliance-ähnliche Gerätekonzept gewahrt bleibt, unterstützt Surface Hub nur die Installation von Apps für die universelle Windows-Plattform (UWP), nicht aber die Installation klassischer Win32-Apps, -Dienste und -Treiber. Darüber hinaus ist die Installation von UWP-Apps nur Administratoren erlaubt.

*Mögliche Auswirkungen auf Richtlinien Ihrer Organisation:* <br> Die Mitarbeiter dürfen nur Apps verwenden, die von den Administratoren installiert wurden. Auf diese Weise lässt sich die Nutzung unerwünschter Apps vermeiden. Die Installation von Win32-Agents, die von den meisten herkömmlichen PC-Verwaltungs- und -Überwachungstools benötigt werden, wird von Surface Hub nicht unterstützt.

## Sicherheit und Sperrmodus

Damit Surface Hub in gemeinschaftlichen Bereichen wie Konferenzräumen eingesetzt werden kann, wurden viele der in Windows10 verfügbaren Sicherheits- und Sperrmodusfeatures im angepassten Betriebssystem implementiert.

Die folgenden Sicherheitsfeatures von Windows10 wurden für Surface Hub implementiert:
- [Sicherer UEFI-Start](https://msdn.microsoft.com/windows/hardware/commercialize/manufacture/desktop/secure-boot-overview)
- [Benutzermodus-Codeintegrität (User Mode Code Integrity, UMCI) mit Device Guard](https://technet.microsoft.com/itpro/windows/keep-secure/introduction-to-device-guard-virtualization-based-security-and-code-integrity-policies)
- [AppLocker-Richtlinien für die App-Einschränkung](https://technet.microsoft.com/itpro/windows/keep-secure/applocker-overview)
- [BitLocker-Laufwerkverschlüsselung](https://technet.microsoft.com/itpro/windows/keep-secure/bitlocker-overview)
- [Trusted Platform Module (TPM)](https://technet.microsoft.com/itpro/windows/keep-secure/trusted-platform-module-overview)
- [Windows Defender](https://technet.microsoft.com/itpro/windows/keep-secure/windows-defender-in-windows-10)
- [Benutzerkontensteuerung (UAC)](https://technet.microsoft.com/itpro/windows/keep-secure/user-account-control-overview) für den Zugriff auf die Einstellungs-App

Die folgenden Surface Hub-Features bieten zusätzliche Sicherheit:
- Angepasste UEFI-Firmware
- Benutzerdefinierte Shell und Startmenü beschränken die Gerätefunktionalität auf Besprechungsfunktionen.
- Der benutzerdefinierte Datei-Explorer gewährt nur Zugriff auf Dateien und Ordner unter „Eigene Dokumente“.
- Die benutzerdefinierte Einstellungs-App erlaubt nur Administratoren die Änderung von Geräteeinstellungen.
- Das Herunterladen von weiterentwickelten Plug & Play-Treibern ist deaktiviert.

*Mögliche Auswirkungen auf Richtlinien Ihrer Organisation:* <br> Beziehen Sie die folgenden Features in Ihre Sicherheitsüberlegungen für den Surface Hub ein:

## Verwaltung

### Geräteeinstellungen

Geräteeinstellungen können über die Einstellungs-App konfiguriert werden. Die Einstellungs-App wurde für den Surface Hub angepasst, enthält jedoch auch viele vertraute Einstellungen aus Windows10 Desktop. Beim Öffnen der Einstellungs-App wird eine Eingabeaufforderung der Benutzerkontensteuerung angezeigt, um die Anmeldeinformationen des Administrators zu bestätigen. Dadurch wird der Administrator jedoch nicht angemeldet.

*Mögliche Auswirkungen auf Richtlinien Ihrer Organisation:* <br> Mitarbeiter können den Surface Hub für Besprechungen verwenden, jedoch keine Geräteeinstellungen ändern. So wird sichergestellt, dass die Mitarbeiter zusätzlich zu den Sperrmodusfeatures nur Besprechungsfunktionen auf dem Gerät nutzen.

### Administrative Features

Die administrativen Features in Windows10 Enterprise, z.B. die Microsoft Management Console, Ausführen, Eingabeaufforderung, PowerShell, Registrierungs-Editor, die Ereignisanzeige und der Task-Manager, werden auf dem Surface Hub nicht unterstützt. Die Einstellungs-App enthält alle administrativen Features, die lokal auf dem Surface Hub zur Verfügung stehen.

*Mögliche Auswirkungen auf Richtlinien Ihrer Organisation:* <br> Surface Hubs werden nicht wie herkömmliche PCs verwaltet. Verwenden Sie MDM zum Konfigurieren von Einstellungen und OMS zur Überwachung des Surface Hub.

### Remoteverwaltung und -überwachung

Surface Hub unterstützt die Remoteverwaltung mithilfe von MDM-Lösungen (Mobile Device Management) wie [Microsoft InTune](https://docs.microsoft.com/intune/) und Überwachung über [Azure Monitor](https://azure.microsoft.com/services/monitor/). 

*Mögliche Auswirkungen auf Richtlinien Ihrer Organisation:* <br> Die Installation von Win32-Agents, die von den meisten herkömmlichen PC-Verwaltungs- und -Überwachungstools benötigt werden (z. B. System Center Operations Manager), wird vom Surface Hub nicht unterstützt.

### Gruppenrichtlinie

Surface Hub unterstützt keine Windows-Gruppenrichtlinien, einschließlich Überwachung. Verwenden Sie stattdessen MDM, um Richtlinien auf Ihren Surface Hub anzuwenden. Weitere Informationen zu MDM finden Sie unter [Verwalten von Einstellungen mit einem MDM-Anbieter](manage-settings-with-mdm-for-surface-hub.md).

*Mögliche Auswirkungen auf Richtlinien Ihrer Organisation:* <br> Verwenden Sie MDM anstelle der Gruppenrichtlinie, um den Surface Hub zu verwalten.

### Remoteunterstützung

Die Remoteunterstützung wird vom Surface Hub nicht unterstützt.

*Mögliche Auswirkungen auf Richtlinien Ihrer Organisation:* <br> Die mit der Remoteunterstützung verbundenen Richtlinien gelten nicht für den Surface Hub.

## Netzwerk

### Domänenbeitritt und Beitritt zu Azure Active Directory (Azure AD) 

Der Surface Hub verwendet den Domänen- und Azure AD-Beitritt in erster Linie, um eine durch Active Directory gesicherte Administratorgruppe bereitzustellen. Benutzer können sich nicht mit einem Domänenkonto anmelden. Weitere Informationen finden Sie unter [Administratorgruppenverwaltung](admin-group-management-for-surface-hub.md).

*Mögliche Auswirkungen auf Richtlinien Ihrer Organisation:* <br> Gruppenrichtlinien werden nicht angewendet, wenn ein Surface Hub mit Ihrer Domäne verbunden ist. Richtlinien für die Domänenmitgliedschaft gelten nicht für den Surface Hub.

### Zugriff auf Domänenressourcen

Benutzer können sich bei Microsoft Edge anmelden, um auf Intranetsites und Onlineressourcen (wie Office 365) zuzugreifen. Wenn Ihr Surface Hub mit einem Gerätekonto konfiguriert wurde, wird dieses vom System für den Zugriff auf Exchange und Skype for Business verwendet. Der Surface Hub unterstützt jedoch nicht den Zugriff auf Domänenressourcen wie Dateifreigaben und Drucker.

*Mögliche Auswirkungen auf Richtlinien Ihrer Organisation:* <br> Richtlinien für den Zugriff auf Domänenobjekte gelten nicht für den Surface Hub.

<!--
### Endpoints



*Organization policies that this may affect:* <br> 
-->

### Diagnosedaten

Das Surface Hub-Betriebssystem verwendet die Windows10-Komponente „Benutzererfahrung und Telemetrie im verbundenen Modus“, um Diagnosedaten zu sammeln und zu übertragen. Weitere Informationen finden Sie unter [Konfigurieren von Windows-Diagnosedaten in Ihrer Organisation](https://technet.microsoft.com/itpro/windows/manage/configure-windows-diagnostic-data-in-your-organization).

*Mögliche Auswirkungen auf Richtlinien Ihrer Organisation:* <br> Konfigurieren Sie die Diagnosedaten für den Surface Hub auf die gleiche Weise wie für Windows 10 Enterprise.
