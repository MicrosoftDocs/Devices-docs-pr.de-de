---
title: Sicherheitsübersicht für Surface Hub
description: Auf dieser Seite wird der tiefgreifende Abwehr von Surface Hub erläutert und es werden Sicherheitsverbesserungen in Surface Hub 2S, Sicherheitsvorkehrungen für die drahtlose Verbindung und zugehörigen Features beschrieben.
keywords: Trennen Sie Werte durch Kommata
ms.prod: surface-hub
ms.sitesec: library
author: coveminer
ms.author: greglin
manager: laurawi
audience: Admin
ms.topic: article
ms.date: 01/26/2021
ms.localizationpriority: High
ms.openlocfilehash: 446166618161fc54a77bab94b2d61ad85359a082
ms.sourcegitcommit: 25b8d880c6438f94b008f47b4fecc3aa4c473e85
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/28/2021
ms.locfileid: "11304848"
---
# Sicherheitsübersicht für Surface Hub

Surface Hub bietet eine gesperrte Appliance-übliche Oberfläche mit benutzerdefinierter Plattformfirmware, auf der das Windows 10 Team-Betriebssystem ausgeführt wird. Das daraus resultierende Gerät nimmt die traditionelle Philosophie des "sicheren Einwegkiosks", "nur das ausführen, was Sie brauchen", auf und liefert eine moderne Sichtweise darauf. Der Surface Hub wurde zur Unterstützung der Zusammenarbeit der Benutzer entwickelt und ist gegen die sich ständig weiterentwickelnden Sicherheitsbedrohungen geschützt.

Das auf Windows 10 basierende Sufrace Hub bietet moderne Sicherheit auf Unternehmensniveau, die IT-Administratoren das Erzwingen des Datenschutzes durch BitLocker, Trusted Platform Module 2.0 (TPM) und Cloud-basierte Sicherheit mit Windows Defender (auch bekannt als Microsoft Defender) ermöglicht.

##  <a name="defense-in-depth-security"></a>Sicherheit durch tiefgreifende Abwehr

Die Sicherheitsprotokolle starten, sobald Surface Hub eingeschaltet ist. Von der Firmware-Ebene ausgehend, lädt Surface Hub das Betriebssystem und seine Komponenten nur als Reaktion auf mehrere Sicherheitsprüfungen. Surface Hub setzt eine Strategie namens "Defense in Depth" (tiefgreifende Abwehr) ein, die die Überlagerung unabhängiger defensiver Unterkomponenten umfasst, um das gesamte System bei Teilfehlern zu schützen. Diese Branchenpraxis hat sich als äußerst effektiv erwiesen, um potenziellen einseitigen Exploits und Schwachstellen in Unterkomponenten entgegenzuwirken.

Die moderne Unified Extensible Firmware Interface (UEFI) wird von Microsoft statisch und sicher so konfiguriert, dass nur ein authentifiziertes Windows 10 -Team-Betriebssystem aus dem internen Speicher gestartet wird.  Jede Codezeile, die auf dem Surface Hub läuft, wird vor der Ausführung auf ihre Signatur überprüft. Nur Anwendungen, die von Microsoft signiert wurden, entweder als Teil des Betriebssystems oder über den Microsoft Store installiert sind, können auf dem Surface Hub ausgeführt werden. Code oder Apps, die diese Anforderungen nicht erfüllen, werden blockiert.

Zu den Sicherheitssystemen von Surface Hub gehören:

- **Startzeitschutz.** Lädt nur vertraute Surface Hub-Betriebssystemkomponenten.
- **Betriebssystemschutzmaßnahmen.** Schutz vor der Ausführung von unerwünschten oder bösartigen Software oder Code.
- **Schutzmaßnahmen für die Benutzeroberfläche.** Bietet eine Benutzeroberfläche, die für Endbenutzer sicher ist, und den Zugriff auf potenziell riskante Aktivitäten wie das Ausführen von ausführbaren Dateien über die Befehlszeile verhindern.

###  <a name="boot-time-defenses"></a>Startzeitschutz

Das SoC hat einen Sicherheitsprozessor, der von jedem anderen Kern getrennt ist. Wenn Sie Surface Hub zum ersten Mal starten, wird nur der Sicherheitsprozessor gestartet, bevor alles andere geladen werden kann.

![Startphasen des Hub-Starts mit Sicherheitsprozessorschutz](images/hub-sec-1.png)

#### Sicherer Start

Der sichere Start wird verwendet, um zu überprüfen, ob die Komponenten des Startprozesses, einschließlich der Treiber und des Betriebssystems, anhand einer Datenbank mit gültigen und bekannten Signaturen überprüft werden. Auf Surface Hub muss eine plattformspezifische Signatur zuerst überprüft werden, bevor das autorisierte Windows Team Betriebssystem geladen werden kann. Auf diese Weise kann verhindert werden, dass Angriffe durch ein geklontes oder geändertes System bösartigen Code ausführen, der in einer ansonsten normalen Benutzeroberfläche angezeigt wird.  Weitere Informationen finden Sie unter [Übersicht des sicheren Starts](https://docs.microsoft.com/windows-hardware/design/device-experiences/oem-secure-boot).

###  <a name="operating-system-defenses"></a>Betriebssystemschutzmaßnahmen

Sobald das Betriebssystem als von Microsoft stammend verifiziert ist und Surface Hub den Startvorgang erfolgreich abgeschlossen hat, überprüft das Gerät den ausführbaren Code. Unser Ansatz zur Sicherung des Betriebssystems umfasst die Identifizierung der Codesignatur aller ausführbaren Dateien, so dass nur diejenigen in die Laufzeit geladen werden können, die unseren Einschränkungen entsprechen. Mit dieser Methode zum Codesignieren kann das Betriebssystem den Autor überprüfen und bestätigen, dass der Code nicht geändert wurde, bevor er auf dem Gerät ausgeführt wird.

Surface Hub verwendet eine Funktion zum Codesignieren, das als "User Mode Code Integrity" (UMCI) im Windows Application Control  (vormals Device Guard) bezeichnet wird. Richtlinieneinstellungen sind so konfiguriert, dass nur Apps zulässig sind, die eine der folgenden Bedingungen erfüllen:

- Apps von der Universal Windows Platform (Microsoft Store), die [offiziell zertifiziert](https://docs.microsoft.com/windows/uwp/publish/the-app-certification-process) sind.
- Apps, die mit der eindeutigen Microsoft Production Root Certification Authority (CA) signiert wurden, die nur von Microsoft-Mitarbeitern mit autorisiertem Zugriff auf diese Zertifikate signiert werden kann.
- Apps, die mit dem eindeutigen Surface Hub Production Root C signiert sind.

Die Konfigurationsdatei wird mithilfe des Microsoft Production Root CA signiert, um zu verhindern, dass Beschränkungen durch Dritte entfernt oder geändert werden. Alle anderen ausführbaren Dateien an diesem Punkt werden nur auf der Laufzeitebene des Betriebssystems blockiert und am Zugriff auf die Rechenleistung gehindert. Diese Reduzierung der Angriffsfläche bietet folgende Schutzmaßnahmen:

- Keine älteren Dokumentmodi
- Keine älteren Skriptmodule
- Keine Vector Markup Language
- Keine Browserhilfsobjekte
- Keine ActiveX-Steuerelemente

Zusätzlich zum Blockieren von nicht signiertem oder falsch signiertem Code über UMCI verwendet Surface Hub Windows Application Control zum Blockieren von Windows-Komponenten wie der Eingabeaufforderung, PowerShell und Task-Manager. Diese Sicherheitsvorkehrungen stellen eine wichtige Entwurfsfunktion von Surface Hub als sicheres EDV-Gerät dar. Weitere Informationen finden Sie in den folgenden Themen:

- [Übersicht über die Anwendungssteuerung](https://docs.microsoft.com/windows/security/threat-protection/windows-defender-application-control/windows-defender-application-control)

- [Windows Defender-Anwendungssteuerung und virtualisierungsbasierter Schutz der Codeintegrität](https://docs.microsoft.com/windows/security/threat-protection/device-guard/introduction-to-device-guard-virtualization-based-security-and-windows-defender-application-control)

###  <a name="user-interface-defenses"></a>Schutzmaßnahmen für die Benutzeroberfläche

Neben den Abwehrmechanismen für die Startzeit und den Sperrmechanismen des Betriebssystems, die eine grundlegende Sicherheit bieten, bietet die Benutzeroberfläche eine zusätzliche Schicht, die das Risiko weiter reduziert. Um zu verhindern, dass bösartiger Code das Gerät über Treiber erreicht, lädt Surface Hub keine erweiterten Treiber für PNP-Geräte. Geräte, die grundlegende Treiber nutzen, wie z. B. USB-Laufwerke oder zertifizierte Surface Hub-Peripheriegeräte (Lautsprecher, Mikrofone und Kameras) funktionieren erwartungsgemäß, aber fortgeschrittene Systeme wie Drucker werden nicht funktionieren.

Außerdem wird die Benutzeroberfläche durch die Schutzmaßnahmen vereinfacht, wodurch die Ausführung von bösartiger Software oder Code weiter verhindert wird. Die folgenden Surface Hub-Oberflächenelemente bilden die Kernsicherheit, die durch Codesignierung bereitgestellt wird:

- **Datei-Explorer.** Surface Hub hat einen benutzerdefinierten Datei-Explorer, der den schnellen Zugriff auf die Ordner "Musik", "Videos", "Dokumente", "Bilder" und "Downloads" ermöglicht, ohne dass die Benutzer Zugriff auf System- oder Programmdateien erhalten. Andere Speicherorte auf der lokalen Festplatte sind im Datei-Explorer nicht verfügbar. Darüber hinaus können viele Dateitypen, die wie .exe- und .msi-Installationsdateien ausgeführt werden, keine weitere Sicherheitsstufe gegen potenziell schädliche ausführbare Dateien bereitstellen.

- **Start & alle Apps.** Mit den Komponenten "Start" und "Alle Apps" von Surface Hub wird der Zugriff auf Eingabeaufforderung, PowerShell oder andere Windows-Komponenten, die über die Anwendungssteuerung blockiert sind, nicht angezeigt. Darüber hinaus ist die Windows-Ausführungsfunktionalität, auf die normalerweise auf PCs über das Suchfeld zugegriffen wird, für den Surface Hub deaktiviert.

##  <a name="security-enhancements-in-surface-hub-2s"></a>Sicherheitsverbesserungen in Surface Hub 2S

Obwohl Surface Hub und Surface Hub 2S die gleiche Betriebssystemsoftware ausführen, bieten einige Features, die für Surface Hub 2S spezifisch sind, zusätzliche Verwaltungs- und Sicherheitsfunktionen, die IT-Administratoren die folgenden Aufgaben ermöglichen:

- Verwalten von UEFI-Einstellungen mit SEMM
- Recover Hub mit startbaren USB-Laufwerken
- Härten des Gerätekontos über eine Kennwort-Rotation

###  <a name="manage-uefi-settings-with-semm"></a>Verwalten von UEFI-Einstellungen mit SEMM

UEFI ist eine Schnittstelle zwischen den zugrunde liegenden Hardwareplattformen und dem Betriebssystem. Eine benutzerdefinierte UEFI-Implementierung in Surface Hub ermöglicht eine granulare Kontrolle über diese Einstellungen und verhindert, dass nicht von Microsoft stammende Entitäten die UEFI-Einstellungen des Geräts ändern oder auf einem Wechseldatenträger starten, um das Betriebssystem zu modifizieren oder zu ändern.

Auf hoher Ebene ist Surface Hub UEFI während des Werkbereitstellungsprozesses vorkonfiguriert, um einen sicheren Start zu ermöglichen, und ist so festgelegt, dass nur vom internen Solid-State-Laufwerk (SSD) gestartet wird, und der Zugriff auf die UEFI-Menüs wird gesperrt und die Verknüpfungen entfernt. Damit wird der UEFI-Zugriff versiegelt und es wird sichergestellt, dass das Gerät nur in das Windows Team-Betriebssystem starten kann, das auf Surface Hub installiert ist.

Bei der Verwaltung über den Microsoft Surface Enterprise Management Mode (SEMM) können IT-Administratoren UEFI-Einstellungen auf Hub-Geräten in der gesamten Organisation bereitstellen. Dazu gehört auch die Möglichkeit, integrierte Hardwarekomponenten zu aktivieren oder zu deaktivieren, die UEFI-Einstellungen vor nicht autorisierten Benutzern zu ändern und die Starteinstellungen anzupassen.

![Surface Hub UEFI-Einstellungen](images/hub-sec-2.png)

Administratoren können SEMM und registrierte Surface Hub 2S-Geräte mithilfe des herunterladbaren [Microsoft Surface UEFI-Konfigurators](https://www.microsoft.com/download/details.aspx?id=46703) implementieren. Weitere Informationen finden Sie unter [Sichern und verwalten von Surface Hub 2S mit SEMM und UEFI](https://docs.microsoft.com/surface-hub/surface-hub-2s-secure-with-uefi-semm).
Durch die Verwendung eines Zertifikats, das die Konfiguration vor unbefugter Manipulation oder Entfernung schützt, ermöglicht SEMM die Verwaltung der folgenden Komponenten:

- Kabelgebundenes LAN
- Kamera
- Bluetooth
- WLAN
- Anwesenheitssensor
- IPv6 für PXE-Start
- Alternativer Start
- Sperre дер Startreihenfolge
- USB-Start
- Benutzeroberfläche der Vorderseite von "UEFI"
    - Geräte
    - Start
    - Datum/Uhrzeit

    
###  <a name="recover-hub-with-bootable-usb"></a>Recover Hub mit startbaren USB-Laufwerken

Surface Hub 2S ermöglicht Administratoren das erneute Installieren des Geräts auf Werkseinstellungen mithilfe eines Wiederherstellungsbilds in nur 20 Minuten. Dies ist normalerweise nur erforderlich, wenn Ihr Surface Hub nicht mehr funktioniert. Die Wiederherstellung ist auch hilfreich, wenn Sie den BitLocker-Schlüssel verloren haben oder keine Administratoranmeldeinformationen für die App "Einstellungen" besitzen.

###  <a name="harden-device-account-with-password-rotation"></a>Härten des Gerätekontos über eine Kennwort-Rotation

Surface Hub verwendet ein Gerätekonto, das auch als "Raumkonto" bezeichnet wird, um sich bei Exchange, Microsoft Teams und anderen Diensten zu authentifizieren. Wenn Sie die Kennwortrotation aktivieren, generiert Hub 2S automatisch ein neues Kennwort alle 7 Tage, bestehend aus 15-32 Zeichen mit einer Kombination aus Groß- und Kleinbuchstaben, Zahlen und Sonderzeichen. Da das Kennwort für das Gerätekonto keiner Person bekannt ist, wird das zugehörige Risiko durch menschliche Fehler und potenzielle Sicherheitsangriffe auf soziale Netzwerke effektiv abgefedert.

##  <a name="windows-10-enterprise-grade-security"></a>Sicherheit auf der Basis von Windows 10 Enterprise

Zusätzlich zu den in diesem Dokument adressierten Konfigurationen und Funktionen, die für Surface Hub spezifisch sind, verwendet Surface Hub auch die Standardsicherheitsfunktionen von Windows 10. Dazu gehören:

- **BitLocker**. Das Surface Hub-SSD ist mit BitLocker ausgerüstet, um die Daten auf dem Gerät zu schützen. Seine Konfiguration folgt den Branchenstandards. Weitere Informationen finden Sie unter [Übersicht über BitLocker](https://docs.microsoft.com/windows-hardware/design/device-experiences/oem-secure-boot).
- **WindowsDefender.** Die Windows Defender Engine zur Bekämpfung von schädlicher Software läuft kontinuierlich auf dem Surface Hub und arbeitet an der automatischen Behebung von Bedrohungen, die auf dem Surface Hub gefunden werden. Die Windows Defender-Engine empfängt Updates automatisch und kann über Fernverwaltungstools für IT-Administratoren verwaltet werden. Die Windows Defender-Engine ist ein perfektes Beispiel für unseren Ansatz der tiefgreifende Abwehr: Wenn Schadsoftware einen Weg um unsere grundlegende Codesignierungsbasierte Sicherheitslösung findet, wird sie hier abgefangen. Weitere Informationen hierzu finden Sie unter [Windows Defender-Anwendungssteuerung und virtualisierungsbasierter Schutz der Codeintegrität](https://docs.microsoft.com/windows/security/threat-protection/device-guard/introduction-to-device-guard-virtualization-based-security-and-windows-defender-application-control).
- **Plug&Play-Treiber.** Um zu verhindern, dass bösartiger Code das Gerät über Treiber erreicht, lädt Surface Hub keine erweiterten Treiber für PNP-Geräte. Auf diese Weise können Geräte, die grundlegende Treiber nutzen, wie USB-Laufwerke, erwartungsgemäß funktionieren, während fortgeschrittene Systeme wie Drucker blockiert werden.
- **Trusted Platform Module 2.0.** Surface Hub verfügt über ein branchenweites, diskretes Trusted Platform Module (dTPM) zum Generieren und Speichern von kryptografischen Schlüsseln und Hashes. Das dTPM schützt die für die Überprüfung von Startphasen verwendeten Schlüssel, den BitLocker-Hauptschlüssel, Anmeldeschlüssel ohne Kennwortschutz und vieles mehr. Der dTPM erfüllt den Anforderungen der [FIPS 140-2, Stufe 2](https://docs.microsoft.com/windows/security/threat-protection/fips-140-validation)-Zertifizierung, den US-amerikanischen Sicherheitsstandard für Computersicherheit und entspricht den Anforderungen der weltweiten [Common Criteria](https://docs.microsoft.com/windows/security/threat-protection/windows-platform-common-criteria) Zertifizierung.

##  <a name="wireless-security-for-surface-hub"></a>Drahtlose Sicherheit für Surface Hub

Surface Hub verwendet eine Wi-Fi Direct- / Miracast-Technologie und dem zugehörigen 802.11, Wi-Fi Protected Access (WPA2) und Wireless Protected Setup (WPS)-Standard. Da das Gerät nur WPS (im Gegensatz zu WPA2 vorinstallierter Schlüssel (PSK) oder WPA2-Enterprise) unterstützt, werden die Probleme mit der 802.11-Verschlüsselung entwurfsbedingt vereinfacht.

Miracast ist Teil des WLAN-Anzeigestandards, der wiederum vom Wi-Fi Direct-Protokoll unterstützt wird. Diese Standards werden in modernen Mobilgeräten für die Bildschirmfreigabe und Zusammenarbeit unterstützt.

Wi-Fi Direct oder Wi-Fi „Peer-zu-Peer” (P2P) ist ein Standard, der von der Wi-Fi Alliance für „Ad-hoc”-Netzwerke freigegeben wird. Dadurch können unterstützte Geräte direkt kommunizieren und Netzwerkgruppen erstellen, ohne dass ein herkömmlicher WLAN-Zugriffspunkt oder eine Internetverbindung benötigt wird.

Sicherheit für Wi-Fi Direct wird von WPA2 mithilfe des WPS-Standards bereitgestellt. Authentifizierungsmechanismen für Geräte können aus einem numerischen Pin, einer physischen oder virtuellen Schaltfläche oder einer Out-of-Band-Nachricht wie Near Field Communication bestehen. Surface Hub unterstützt standardmäßig sowohl die Schaltfläche als auch die Pin-Methode. Weitere Informationen hierzu finden Sie unter [Wie Surface Hub Wi-Fi Direct-Sicherheitsprobleme behebt](https://docs.microsoft.com/surface-hub/surface-hub-wifi-direct).

##  <a name="learn-more"></a>Mehr erfahren

- [Übersicht über den sicheren Start](https://docs.microsoft.com/windows-hardware/design/device-experiences/oem-secure-boot)

- [BitLocker-Übersicht](https://docs.microsoft.com/windows/security/information-protection/bitlocker/bitlocker-overview)

- [Übersicht über die Anwendungssteuerung](https://docs.microsoft.com/windows/security/threat-protection/windows-defender-application-control/windows-defender-application-control)

- [Sichern und verwalten von Surface Hub 2S mit SEMM und UEFI](https://docs.microsoft.com/surface-hub/surface-hub-2s-secure-with-uefi-semm)

- [Wie Surface Hub Wi-Fi Direct-Sicherheitsprobleme behebt](https://docs.microsoft.com/surface-hub/surface-hub-wifi-direct)

- [Windows Defender-Anwendungssteuerung und virtualisierungsbasierter Schutz der Codeintegrität](https://docs.microsoft.com/windows/security/threat-protection/device-guard/introduction-to-device-guard-virtualization-based-security-and-windows-defender-application-control)

- [Surface-Tools für IT](https://www.microsoft.com/download/details.aspx?id=46703)

- [FIPS 140-2, Stufe 2](https://docs.microsoft.com/windows/security/threat-protection/fips-140-validation)

- [Common Criteria-Zertifizierung](https://docs.microsoft.com/windows/security/threat-protection/windows-platform-common-criteria)
