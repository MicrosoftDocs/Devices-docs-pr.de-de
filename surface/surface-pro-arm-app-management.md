---
title: Bereitstellen, Verwalten und Warten von Surface Pro X
description: Dieser Artikel enthält eine Übersicht über wichtige Überlegungen zur Bereitstellung, Verwaltung und Wartung des Surface Pro X.
ms.prod: w10
ms.mktglfcycl: manage
ms.localizationpriority: high
ms.sitesec: library
author: coveminer
ms.author: greglin
ms.topic: article
ms.date: 1/15/2021
ms.reviewer: jessko
manager: laurawi
ms.audience: itpro
ms.openlocfilehash: 30f7cd7d861b6497cd536aeb0ea348b6946a2674
ms.sourcegitcommit: 1053479c191fd10651d31a466fad1769fb0cd28b
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/16/2021
ms.locfileid: "11271359"
---
# Bereitstellen, Verwalten und Warten von Surface Pro X

##  <a name="introduction"></a>Einführung

Surface Pro X ist für hohe kommerzielle Leistungsanforderungen konzipiert und beschreitet neue Wege durch den integrierten leistungsstärksten Prozessor seiner Klasse, den Microsoft SQ1 und Microsoft SQ1 ARM-Chipsatz.

Mit einer CPU mit 3 GHz und einer GPU mit 2,1 Teraflops bietet Surface Pro X eine vollständige Windows-Umgebung. Dank der integrierten Gigabit-LTE-Batterie mit einer Laufzeit von 15 Stunden und der Vielseitigkeit von Touch, Stift, Tablett und Laptop eignet es sich für mobile Mitarbeiter und Profis in den Bereichen Finanzen, Recht und Medizin oder in allen Bereichen, in denen eine längere Akkulaufzeit und kontinuierliche Konnektivität erforderlich sind.

Surface Pro X ist fast ausschließlich für eine moderne, cloudbasierte Umgebung konzipiert und funktioniert am besten in Verbindung mit Microsoft 365, Intune und Windows Autopilot. Dieser Artikel beschreibt, wie das im Einzelnen aussieht, und führt die wichtigsten Überlegungen zur Bereitstellung, Verwaltung und Wartung des Surface Pro X aus.

##  <a name="deploying-surface-pro-x"></a>Bereitstellen von Surface Pro X

Um eine optimale Leistung zu erzielen, stellen Sie Surface Pro X mithilfe von Windows Autopilot und entweder mit Unterstützung eines Microsoft Cloud Solution Providers oder eigenständig bereit, indem Sie Autopilot-Bereitstellungsprofile und verwandte Funktionen verwenden. Weitere Informationen finden Sie unter:

- [Windows Autopilot und Surface-Geräte](windows-autopilot-and-surface-devices.md)
- [Übersicht über Windows Autopilot](https://docs.microsoft.com/windows/deployment/windows-autopilot/windows-autopilot)

Die Autopilot-Bereitstellung bietet mehrere Vorteile: Sie ermöglicht Ihnen die Verwendung des werkseitig bereitgestellten Betriebssystems, das für die Zero Touch-Bereitstellung optimiert ist, um die Vorinstallation von Office Pro Plus einzuschließen.

Organisationen, die bereits moderne Management-, Sicherheits- und Produktivitätslösungen einsetzen, sind gut positioniert, um von den einzigartigen Leistungsmerkmalen von Surface Pro X zu profitieren. Auch Kunden, die branchenspezifische Apps, Microsoft Store-Apps (UWP) oder Remotedesktop-Lösungen einsetzen, profitieren davon.

##  <a name="image-based-deployment-considerations"></a>Überlegungen zur imagebasierten Bereitstellung

Microsoft Deployment Toolkit (MDT)) und Microsoft Endpoint Configuration Manager (ehemals System Center Configuration Manager) unterstützen Surface Pro X derzeit nicht für die Bereitstellung von Betriebssystemen. Kunden, die sich auf die imagebasierte Bereitstellung verlassen, sollten Surface Pro 7+ berücksichtigen, während sie den richtigen Zeitpunkt für den Übergang zu modernen Bereitstellungslösungen bewerten. 

##  <a name="managing-surface-pro-x-devices"></a>Verwalten von Surface Pro X-Geräten

###  <a name="intune"></a>Intune

Intune ist eine Komponente von Microsoft Enterprise Mobility + Security, die für die Identitäts- und Zugriffssteuerung in Azure Active Directory integriert ist und eine präzise Verwaltung von registrierten Surface Pro X-Geräten ermöglicht. Intune-Richtlinien für die Mobile Geräteverwaltung (Mobile Device Management, MDM) bieten gegenüber älteren lokalen Tools wie der Windows-Gruppenrichtlinie eine Reihe von Vorteilen. Dazu gehören schnellere Geräteanmeldezeiten und ein optimierter Richtlinienkatalog, der eine vollständige Geräteverwaltung über die Cloud ermöglicht. Sie können beispielsweise LTE mithilfe von eSIM-Profilen verwalten, um Datentarife zu konfigurieren und Aktivierungscodes auf mehreren Geräten bereitzustellen.<br> 

Weitere Informationen zur Verwendung von Intune erhalten Sie in der [Intune-Dokumentation](https://docs.microsoft.com/intune/).

###  <a name="co-management"></a>Gemeinsame Verwaltung

Nach der Bereitstellung in Autopilot können Sie Surface Pro X-Geräte mit Azure AD oder Active Directory (Azure AD Hybrid Join) verknüpfen, wo Sie die Geräte mit Intune oder gemeinsam mit Endpoint Configuration Manager verwalten können, wodurch der ConfigMgr-Client (32-Bit x86) installiert wird.

###  <a name="third-party-mdm-solutions"></a>MDM-Lösungen von Drittanbietern

Sie können Surface Pro X-Geräte möglicherweise mit MDM-Tools von Drittanbietern verwalten. Weitere Informationen erhalten Sie von Ihrem MDM-Anbieter.

###  <a name="antivirus-software"></a>Antivirensoftware

Windows Defender trägt während der unterstützten Lebensdauer Ihres Windows 10-Geräts zum Schutz von Windows 10 auf ARM-basierten PCs bei. 

Die Antivirensoftware eines Drittanbieters kann nicht auf einem Windows 10-PC installiert werden, auf dem ein ARM-basierter Prozessor ausgeführt wird. Die Zusammenarbeit mit Drittanbietern von Antivirensoftware wird fortgesetzt, um die AV-App-Vorbereitung auf ARM-basierten PCs zu gewährleisten. Wenden Sie sich den Anbieter der Antivirensoftware, um weitere Informationen zur Verfügbarkeit ihrer Apps zu erhalten.

##  <a name="servicing-surface-pro-x"></a>Warten von Surface Pro X

Surface Pro X wird mit Windows 10 Version 2004 ausgeliefert und unterstützt Windows 10, Version 1903 und höher. Als ARM-basiertes Gerät stellt es bestimmte Anforderungen an die Aktualität der Treiber und Firmware. 

Surface Pro X ist auf Windows Update ausgelegt, um das Aktualisieren von Treibern und Firmware für Privatbenutzer und Benutzer in Kleinunternehmen zu vereinfachen. Verwenden Sie die Standardeinstellungen, um automatische Updates zu erhalten.  Führen Sie zur Überprüfung die folgenden Schritte aus:

1. Navigieren Sie zu **Start** > **Einstellungen > Update und Sicherheit > Windows Update** > **Erweiterte Optionen**.
2. Wählen Sie unter **Auswählen der Installationsmethode für Updates** die Option **Automatisch (empfohlen)** aus.

###  <a name="recommendations-for-commercial-customers"></a>Empfehlungen für Geschäftskunden

- Verwenden Sie Windows Update oder Windows Update for Business zum Aktualisieren auf die neueste(n) Treiber und Firmware. Weitere Informationen finden Sie unter [Bereitstellen von Updates mit Windows Update for Business](https://docs.microsoft.com/windows/deployment/update/waas-manage-updates-wufb).
- Weitere Informationen zum Bereitstellen und Verwalten von Updates auf Surface-Geräten finden Sie unter [Verwalten und Bereitstellen der neuesten Firmware und Treiber für Surface](manage-surface-driver-and-firmware-updates.md).
- Beachten Sie, dass Windows Server Update Services (WSUS) die Bereitstellung von Treibern und Firmware für Surface Pro X nicht unterstützt.

##  <a name="running-apps-on-surface-pro-x"></a>Ausführen von Apps auf Surface Pro X

Bis auf einige Ausnahmen, werden die meisten Apps auf ARM-basierten Windows 10-PCs ausgeführt.

###  <a name="supported-apps"></a>Unterstützte Apps

- Die meisten x86 Win32-Apps werden auf Surface Pro X ausgeführt.
- Native ARM64- und UWP-Apps für den Microsoft Store bieten eine hervorragende Benutzerfreundlichkeit durch die Nutzung der vollständig nativen Geschwindigkeit des ARM-basierten Prozessors, und dies bei gleichzeitiger Optimierung der Akkulaufzeit.
- Apps, die Treiber verwenden, die für einen Windows 10-PC mit einem ARM-basierten Prozessor ausgelegt sind.

> [!NOTE]
> Mit der 64-Bit-Emulation, die demnächst in der Vorschau über das Windows-Insider-Programm eingeführt wird, können Sie 64-Bit (x64) Apps auf Surface Pro X ausführen.

###  <a name="fasttrack-app-assure"></a>FastTrack App Assure 

Das App Assure-Programm steht kommerziellen Kunden für ihre LOB-, ISV- und Microsoft First Party-Apps zur Verfügung, die auf Windows 10 auf ARM ausgerichtet sind. Wenn bei kommerziellen Kunden ein Kompatibilitätsproblem mit einer Anwendung bei der Verwendung von Windows 10 auf ARM auftritt, stellt Microsoft Entwicklerressourcen zur Fehlerbehebung und Unterstützung bei der Behebung von Problemen mit Anwendungen zur Verfügung, und zwar ohne zusätzliche Kosten. Weitere Informationen finden Sie unter [aka.ms/AppAssure](https://docs.microsoft.com/fasttrack/products-and-capabilities#app-assure).

Weitere Informationen zum Ausführen von Apps auf Surface Pro X finden Sie unter:

- [Häufig gestellte Fragen zu Windows 10 ARM-basierten PCs](https://support.microsoft.com/help/4521606)
- [Dokumentation zu Windows 10 auf ARM](https://docs.microsoft.com/windows/arm)

##  <a name="virtual-desktops-(vdi)"></a>Virtuelle Desktops (VDI)

Windows Virtual Desktop ermöglicht den Zugriff auf Windows-Desktopcomputer, -Anwendungen und -Daten auf allen Computergeräten oder -plattformen von jedem Standort aus. Weitere Informationen finden Sie auf der [Windows Virtual Desktop-Website](https://aka.ms/wvd). 

##  <a name="browsing-with-surface-pro-x"></a>Surfen mit Surface Pro X

Gängige auf Surface Pro X ausgeführte Browser:

- Integrierte Browser wie Edge, Firefox, Chrome und Internet Explorer werden auf Surface Pro X ausgeführt.
- Firefox und Microsoft Edge, die auf Chrome basieren, sind direkt ausführbar und bieten somit eine höhere Leistung auf einem Windows 10-PC mit ARM-basiertem Prozessor.

##  <a name="installing-and-using-microsoft-office"></a>Installieren und Verwenden von Microsoft Office

- Verwenden Sie Office 365 auf einem Windows 10-PC mit ARM-basiertem Prozessor, um optimale Ergebnisse zu erzielen.
- Office 365 "Klick-und-Los" installiert Outlook, Word, Excel und PowerPoint, optimiert für die Ausführung auf einem Windows 10-PC auf einem ARM-basierten Prozessor.
- Microsoft Teams wird problemlos auf Surface Pro X ausgeführt.
- Installieren Sie für "unbefristete Versionen" von Office wie Office 2019 die 32-Bit-Version.

##  <a name="vpn"></a>VPN

Um zu ermitteln, ob ein bestimmtes VPN eines Drittanbieters einen Windows 10 PC auf einem ARM-basierten Prozessor unterstützt, wenden Sie sich an den VPN-Anbieter.

##  <a name="feature-summary"></a>Featurezusammenfassung

Die folgenden Tabellen zeigen die Verfügbarkeit ausgewählter wichtiger Features auf Surface Pro X mit Windows 10 auf ARM.


**Bereitstellung**

| Feature                                                           | J/N | Anmerkungen                                                                                                                             |
| ----------------------------------------------------------------- | --- | --------------------------------------------------------------------------------------------------------------------------------- |
| Windows Autopilot                                                 | Ja |                                                                                                                                   |
| Unterstützung für Netzwerkstart (PXE)                                    | Nein  |                                                                                                                                   |
| Windows Configuration Designer                                    | Nein  | Wird nicht für Surface Pro X empfohlen                                                                                                |
| WinPE                                                             | Ja | Wird nicht für Surface Pro X empfohlen. Microsoft stellt nicht die erforderliche(n) ISO-Datei und Treiber zur Unterstützung von WinPE mit Surface Pro X bereit. |
| Endpoint Configuration Manager: Betriebssystembereitstellung | Nein  | Wird auf Surface Pro X nicht unterstützt                                                                                                   |
| MDT                                                               | Nein  | Wird auf Surface Pro X nicht unterstützt                                                                                                   |

 
 
 **Management**
 

| Feature                                       | J/N     | Anmerkungen                                                                                 |
| --------------------------------------------- | ------- | ------------------------------------------------------------------------------------- |
| Intune                                        | Ja     | Verwaltung von LTE mit eSIM-Profilen                                                        |
| Windows Autopilot                             | Ja     |                                                                                       |
| Azure AD (gemeinsame Verwaltung)                      | Ja     | Ermöglicht die Verknüpfung von Surface Pro X mit Azure AD oder Active Directory (Azure AD Hybrid Join) |
| Endpoint Configuration Manager                | Ja     |                                                                                       |
| Einschalten bei Wiederherstellung im Netzbetrieb                      | Ja     |                                                                                       |
| Surface-Diagnosetoolkit für Unternehmen | Ja     |                                                                                       |
| Surface Asset-Tag-Tool                        | Ja     |                                                                                       |
| Surface Enterprise Management Mode (SEMM)     | Teilweise | Hardware auf Surface Pro X kann auf Firmwareebene nicht deaktiviert werden                 |
| Surface UEFI-Konfigurator                     | Nein      | Hardware auf Surface Pro X kann auf Firmwareebene nicht deaktiviert werden                |
| Surface UEFI-Manager                          | Teilweise | Hardware auf Surface Pro X kann auf Firmwareebene nicht deaktiviert werden                 |

 

**Sicherheit**
 

 Feature                                       | J/N     | Anmerkungen                                                                                 |
| --------------------------------------------- | ------- | ------------------------------------------------------------------------------------- |
| BitLocker                                     | Ja     |                                                       |
| Windows Defender                              | Ja     |                                                                                       |
| Unterstützung für Antivirensoftware von Drittanbietern             | Siehe Hinweis| Die Antivirensoftware eines Drittanbieters kann nicht auf einem Windows 10-PC installiert werden, auf dem ein ARM-basierter Prozessor ausgeführt wird. Die Zusammenarbeit mit Drittanbietern von Antivirensoftware wird fortgesetzt, um die AV-App-Vorbereitung auf ARM-basierten PCs zu gewährleisten. Wenden Sie sich den Anbieter der Antivirensoftware, um weitere Informationen zur Verfügbarkeit ihrer Apps zu erhalten. |
| Sicherer Start               | Ja     |                                                                                       |
| Windows Information Protection                      | Ja     |                                                                                       |
| Surface Data Eraser (SDE)     | Ja     |                                                                                       |




##  <a name="faq"></a>Häufig gestellte Fragen

###  <a name="can-i-deploy-surface-pro-x-with-mdt-or-endpoint-configuration-manager"></a>Kann ich Surface Pro X mit MDT oder Endpoint Configuration Manager bereitstellen?

Das Microsoft Deployment Toolkit (MDT) und Microsoft Endpoint Configuration Manager unterstützen derzeit keine Surface Pro X für die Betriebssystembereitstellung. Kunden, die sich auf die imagebasierte Bereitstellung verlassen, sollten Surface Pro 7+ berücksichtigen, während sie den richtigen Zeitpunkt für den Wechsel zur Cloud bewerten.

###  <a name="how-can-i-deploy-surface-pro-x"></a>Wie kann ich Surface Pro X bereitstellen?

Stellen Sie Surface Pro X mithilfe von Windows Autopilot bereit.

###  <a name="is-a-bmr-available"></a>Ist ein BMR verfügbar?

Ja. Weitere Informationen finden Sie unter [Herunterladen eines Wiederherstellungsbilds für Ihr Surface](https://support.microsoft.com/surfacerecoveryimage).

###  <a name="is-intune-required-to-manage-surface-pro-x"></a>Ist Intune erforderlich, um Surface Pro X zu verwalten?

Intune wird empfohlen, ist aber nicht erforderlich. Nach der Bereitstellung in Autopilot können Sie Surface Pro X-Geräte mit Azure AD oder Active Directory (Azure AD Hybrid Join) verknüpfen, wo Sie die Geräte mit Intune oder gemeinsam mit Endpoint Configuration Manager verwalten können, wodurch der ConfigMgr-Client (32-Bit x86) installiert wird.
