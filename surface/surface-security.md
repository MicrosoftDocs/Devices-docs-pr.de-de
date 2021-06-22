---
title: Übersicht über die Surface-Sicherheit
description: Dieser Artikel bietet eine Übersicht über die Sicherheit von Surface-Geräten.
ms.prod: w10
ms.mktglfcycl: manage
ms.localizationpriority: medium
ms.sitesec: library
author: coveminer
ms.author: greglin
ms.topic: article
ms.date: 06/04/2021
ms.reviewer: brrecord
manager: laurawi
audience: itpro
ms.openlocfilehash: 67ba96129d69cafaa7a1b24ce3dde98767b676ef
ms.sourcegitcommit: 267e12897efd9d11f8c7303eaf780632741cfe77
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/22/2021
ms.locfileid: "11614092"
---
# <a name="surface-security-overview"></a>Übersicht über die Surface-Sicherheit

Aktuelle Fortschritte bei der Sicherheitssuche zeigen, dass Angreifer, wenn mehr Schutzmaßnahmen in das Betriebssystem und verbundene Dienste integriert sind, nach anderen Möglichkeiten der Nutzung von Firmware suchen, die als oberstes Ziel fungiert.

Heute ist die Verwaltung der Gerätefirmware eine inkonsistente Erfahrung und umfasst häufig Drittanbieter, die die Überwachung und Wartung der Firmware erschweren. Letztendlich kann dies die Fähigkeit von Hardwareherstellern einschränken, updates als Reaktion auf Bedrohungen rechtzeitig zu erkennen und zu übertragen.

Microsoft Surface verwendet seit 2015 einen einheitlichen Ansatz zum Firmwareschutz und zur Gerätesicherheit durch den vollständigen End-to-End-Besitz des Hardwaredesigns, die unternehmensinterne Firmwareentwicklung und einen ganzheitlichen Ansatz für Geräteupdates und -verwaltung.

Für Surface wird unsere Unified Extensible Firmware Interface (UEFI) <sup> [1](#references) </sup> intern verwaltet, regelmäßig über Windows Update aktualisiert und nahtlos für die Verwaltung über Windows Autopilot bereitgestellt, wodurch das Risiko minimiert und die Steuerung auf Firmwareebene maximiert wird, bevor das Gerät gestartet wird. Microsoft bietet vollständige Transparenz der Codebasis in unserer UEFI über die Open Source [Project Mu](https://microsoft.github.io/mu/) on GitHub, die von Microsoft Endpoint Manager verwaltet wird.

## <a name="microsoft-designed-and-built-components"></a>Von Microsoft entworfene und erstellte Komponenten

Jede Surface-Ebene von Chip zu Cloud wird von Microsoft entwickelt und verwaltet, sodass Sie die ultimative Kontrolle, proaktiven Schutz und Gesinnungssicherheit überall und unabhängig davon erhalten, wo und wie viel Arbeit erledigt wird. Surface-Geräte werden mit den stärksten Sicherheitsprotokollen ausgeliefert, die Microsoft anbietet, und ermöglichen eine optimierte Verwaltung, die die IT-Komplexität reduziert, sodass Benutzer sich auf ihre Arbeit konzentrieren können.

Surface treibt die Sicherheit durch einen umfassenden Verteidigungsansatz voran, indem eine Schichtung unabhängiger untergeordneter Komponenten verwendet wird. Vom Chip in die Cloud oder einer UEFI, die einen Vertrauensstamm für den KI-unterstützten Microsoft Defender für Endpunkt bereitstellt, der dazu dient, erweiterte Bedrohungen zu verhindern, zu erkennen, zu untersuchen und darauf zu reagieren, erzwingt Surface die Position, die in Microsoft integriert ist, ist besser als das Anschalten.

| Feature                         | Beschreibung                                                                                                                                                                                                                                                                                                                         | Mehr erfahren                                                                                                                                                                   |
| ------------------------------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Microsoft Built UEFI            | Software, die das Gerät konfiguriert und Windows 10 startet<br>Steuert den anfänglichen Start des Geräts und Windows 10 und stellt dann Firmwarelaufzeitdienste für das Betriebssystem bereit. stellt über die lokale SEMM-Verwaltung und die cloudbasierte DFCI-Verwaltung über Microsoft Endpoint Manager deutlich mehr Kontrolle über die Hardware eines Geräts sicher. | [Verwalten von Surface UEFI-Einstellungen](manage-surface-uefi-settings.md)                                                                        |
| Physisches TPM 2.0                | Trusted Platform Module – Dedizierter Mikrocontroller, der zur Sicherung von Hardware über integrierte kryptografische Schlüssel entwickelt wurde.<br>Verschlüsselt und speichert Schlüssel (BitLocker, Windows Hello, AD-Anmeldeinformationen,)<br>PCR – Plattformkonfigurationsregister, die Messungen und relevante Metriken sichern, um Änderungen an der vorherigen Konfiguration zu erkennen  | [Trusted Platform Module – Technologieübersicht](/windows/security/information-protection/tpm/trusted-platform-module-overview)                 |
| Windows Hello for Business      | Ersetzt Kennwörter durch eine sichere zweistufige Authentifizierung auf PCs und mobilen Geräten. Diese biometrische Authentifizierung besteht aus einem neuen Benutzeranmeldeinformationstyp, der an ein Gerät gebunden ist und ein biometrisches Element oder eine PIN verwendet.                                                                                                                   | [Funktionsweise von Windows Hello for Business – Microsoft 365 Sicherheit](/windows/security/identity-protection/hello-for-business/hello-how-it-works) |
| Integrierte Verschlüsselung           | Die integrierte Verschlüsselung wird von BitLocker aktiviert, um Ihre Daten zu sichern und zu verschlüsseln, und Windows Hello, um die kennwortlose Anmeldung in Kombination mit physischem TPM und UEFI zu ermöglichen.                                                                                                                                                                 | [BitLocker (Windows 10) – Microsoft 365 Sicherheit](/windows/security/information-protection/bitlocker/bitlocker-overview)                     |
| Microsoft Defender für Endpunkt | Stellt eine Sicherheitsplattform für Endpunkte für Unternehmen bereit, die Unternehmensnetzwerke dabei unterstützt, fortgeschrittene Bedrohungen zu verhindern, zu erkennen, zu untersuchen und darauf zu reagieren.                                                                                                                                                                               | [Microsoft Defender für Endpunkt](/microsoft-365/security/defender-endpoint/microsoft-defender-endpoint)                 |

## <a name="factory-level-security-protocols-and-inspection"></a>Sicherheitsprotokolle und Überprüfung auf Factoryebene

Von der Firmware über das Betriebssystem bis hin zu allen Komponenten der Hardware vor der endgültigen Assembly sind Surface-Geräte in unseren physisch gesicherten Entwicklungs- und Produktionsanlagen sicher vor Lieferkettenangriffen.

Per Definition liefert eine sichere Lieferkette Fertigprodukte, die qualität, leistung und betriebsbereite Ziele erfüllen. Einfach ausgedrückt, stellt eine sichere Lieferkette sicher, dass alle Komponenten echt sind und frei von nicht autorisierten oder böswilligen Manipulationen oder Senkungen sind. Wir stellen Geräte in streng gesicherten Fabriken her, in denen alles von der UEFI-Firmware bis zum Betriebssystem direkt von Microsoft stammt. Es sind keine BIOS-Drittanbieter beteiligt. Dies ist ein wesentlicher Bestandteil der Art und Weise, wie wir uns vor Angriffen in der Lieferkette für Surface-Produkte schützen. Wir haben die Angriffsoberfläche in unserer UEFI reduziert, indem nicht verwendeter Code entfernt wurde, einschließlich SMM-Funktionen im Systemverwaltungsmodus, die Geräte sind, die nicht benötigt werden.

Der Schutz von Einrichtungen vor externen internetbasierten Angriffen, Eindringversuchen und anderen Bedrohungen erfordert fortlaufende Investitionen in wichtigen Bereichen, einschließlich:

- Strenge Überprüfung und Prüfung aller Komponenten an endgültigen Assemblystandorten.
- Aufrechterhaltung eines hohen Grads an physischer Sicherheit im Werk.
- Nur von Microsoft entwickelte & verwalteten Firmware, Treibern und Betriebssystemen.
- Sichere Logistik und vertrauenswürdige Netzbetreiberbereitstellung von Surface-Geräten direkt an Microsoft-Händler.

Beim Verlassen des Werks werden Surface for Business Geräte während des gesamten Lebenszyklus über Windows Update geschützt.

## <a name="advanced-windows-security-features"></a>Erweiterte Sicherheitsfeatures Windows

Die Eskalation von Rechteangriffen ist der beste Freund eines böswilligen Akteurs und zielen häufig auf vertrauliche Informationen ab, die im Speicher gespeichert sind. Diese Art von Angriffen kann eine Kompromittieren des Geringfügigkeitsbenutzermodus in eine vollständige Gefährdung Ihres Betriebssystems und Geräts umwandeln. Um diese Art von Angriffen zu verhindern, hat Microsoft virtualisierungsbasierte Sicherheit (VBS) und hypervisorgeschützte Codeintegrität (HVCI, auch allgemein als Speicherintegrität bezeichnet) entwickelt. VBS und HVCI nutzen die Leistungsfähigkeit von Hardwarefunktionen wie Virtualisierung, um einen besseren Schutz vor gängiger und komplexer Schadsoftware zu bieten, indem vertrauliche Sicherheitsvorgänge in einer isolierten Umgebung ausgeführt werden.

Surface wird mit diesen Windows erweiterten Hardwaresicherheitsfunktionen ausgeliefert, die sofort aktiviert sind, um Kunden noch mehr Sicherheit zu bieten, die integriert und standardmäßig aktiviert ist.

## <a name="virtualization-based-security"></a>Virtualisierungsbasierte Sicherheit

Virtualisierungsbasierte Sicherheit (VBS) verwendet Hardwarevirtualisierungsfeatures, um einen sicheren Speicherbereich vom normalen Betriebssystem zu erstellen und zu isolieren. Windows können diesen "virtuellen sicherheitssicheren Modus" verwenden, um eine Reihe von Sicherheitslösungen zu hosten, wodurch der Schutz vor Sicherheitsrisiken im Betriebssystem erheblich erhöht wird und die Verwendung von böswilligen Exploits verhindert wird, die versuchen, Schutzmechanismen zu verhindern.

### <a name="hypervisor-enforced-code-integrity-hvci"></a>Hypervisor-Enforced Codeintegrität (HVCI)

HVCI verwendet VBS, um die Erzwingung von Codeintegritätsrichtlinien erheblich zu stärken. Die Codeintegrität des Kernelmodus überprüft alle Kernelmodustreiber und Binärdateien, bevor sie gestartet werden, und verhindert, dass nicht signierte Treiber oder Systemdateien in den Systemspeicher geladen werden. Wie im folgenden Diagramm dargestellt, wird HVCI in einer isolierten Ausführungsumgebung ausgeführt und überprüft die Integrität des Kernelcodes gemäß der Kernelsignierungsrichtlinie.

Sowohl VBS als auch HVCI sind in den folgenden Surface-Geräten sofort aktiviert:

- Surface Laptop 4
- Surface Pro 7+
- Surface Book 3,
- Surface Laptop Gehen
- Surface Pro X

## <a name="secure-boot-and-boot-guard"></a>Sicherer Start und Startschutz

Das Root of Trust von Surface-Geräten überprüft Signaturen und Messungen, um sicherzustellen, dass jede Phase sicher und authentifiziert ist, bevor die nächste Startphase fortgesetzt werden kann. Der sichere Start ist durch UEFI und TPM 2.0 aktiviert und stellt sicher, dass nur code, der signiert, gemessen und richtig implementiert ist, auf einem Surface-Gerät ausgeführt werden kann.

Wie in Abbildung 2 dargestellt, wird die Integrität der Firmware in jeder Phase vom Drücken des Netzschalters bis zur Ausführung des Betriebssystems überprüft.

 > [!div class="mx-imgBorder"]
 > ![Abbildung1. Sicherer Start für Surface-Geräte ](images/secboot.png)
  *Abbildung 1. Sicherer Start für Surface-Geräte*

| Schritt  | Phase des sicheren Starts                                                                                                                                                                                                                                      |
| ----- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| **1** | Die Sicherheit wird jedes Mal instanziiert, wenn der Netzschalter aus einem vom TPM bereitgestellten Vertrauensstamm gedrückt wird. Wenn ein Gerät zum ersten Mal eingeschaltet wird, führt das System eine Reihe von Sicherheitsüberprüfungen aus, um sicherzustellen, dass die Gerätefirmware nicht manipuliert oder beschädigt wurde. |
| **2** | Wenn der SoC eingeschaltet wird, verwendet der SoC einen Chipsatzanbieterschlüssel, um das Laden von Microcode mithilfe des authentifizierten Codemoduls (ACM) (auf Intel-basierten Geräten) zu überprüfen und zu initiieren.                                                                              |
| **3** | Der ACM misst den UEFI-Code vor dem Laden und vergleicht ihn mit der bekannten Messung im Plattformkonfigurationsregister (PCR) des TPM, um sicherzustellen, dass der UEFI-Code nicht geändert wurde.                                                                |
| **4** | Bevor UEFI ausgeführt werden kann, überprüft Boot Guard, ob die UEFI mit einem Surface OEM-Schlüssel signiert ist. Das anfänglich überprüfte UEFI-Modul ist die SEC-Sicherheit und die pei Pre-EFI-Abschnitte, die im Diagramm dargestellt sind.                                                |
| **5** | Der PEI-Abschnitt sucht nach einer Surface-Signatur in der Treiberausführungsumgebung, dem DXE-Modul, während sie geladen wird. Das DXE-Modul enthält die Startgeräteauswahlphase.                                                                          |
| **6** | Sobald das Startgerät ausgewählt ist, liest UEFI das Startgerät und überprüft die Signatur des Betriebssystem-Startladeprogramms, bevor es ausgeführt werden kann.                                                                                                             |
| **7** | Das Betriebssystem überprüft dann seine Signaturen für die Hauptkomponente, während es das Betriebssystem öffnet.

### <a name="malware-protection"></a>Schutz vor Schadsoftware

Um Ihr Gerät vor Angriffen durch Schadsoftware zu schützen, ermöglicht Surface den sicheren Start, um sicherzustellen, dass eine authentifizierte Version von Windows 10 gestartet wird und die Firmware so original ist wie beim Verlassen der Factory.

Der SoC auf Surface-Geräten verfügt über einen Sicherheitsprozessor, der von jedem anderen Kern getrennt ist. Wenn Sie das Surface-Gerät zum ersten Mal starten, wird nur der Sicherheitsprozessor gestartet, bevor alles andere geladen werden kann. Der sichere Start wird verwendet, um zu überprüfen, ob die Komponenten des Startprozesses, einschließlich der Treiber und des Betriebssystems, anhand einer Datenbank mit gültigen und bekannten Signaturen überprüft werden. Auf diese Weise kann verhindert werden, dass Angriffe durch ein geklontes oder geändertes System bösartigen Code ausführen, der in einer ansonsten normalen Benutzeroberfläche angezeigt wird. Weitere Informationen finden Sie unter [Übersicht des sicheren Starts](/windows-hardware/design/device-experiences/oem-secure-boot).

Nachdem das Betriebssystem als von Microsoft stammend überprüft wurde und das Surface-Gerät den Startvorgang erfolgreich abgeschlossen hat, überprüft das Gerät den ausführbaren Code. Unser Ansatz zur Sicherung des Betriebssystems umfasst die Identifizierung der Codesignatur aller ausführbaren Dateien, so dass nur diejenigen in die Laufzeit geladen werden können, die unseren Einschränkungen entsprechen. Mit dieser Methode zum Codesignieren kann das Betriebssystem den Autor überprüfen und bestätigen, dass der Code nicht geändert wurde, bevor er auf dem Gerät ausgeführt wird.

## <a name="drtm-protection-in-amd-devices"></a>DRTM-Schutz in AMD-Geräten

Surface-Geräte mit AMD-Prozessoren implementieren den sicheren Start auf äquivalente Weise. Surface Laptop 4 mit AMD- Und Amd-Prozessoren schützt die Firmware vor dem anfänglichen Einschalten mithilfe von Dynamic Root of Trust Measurements (DRTM). DRTM steuert alle CPUs, erzwingt die Ausführung entlang eines gemessenen Pfads und setzt die Vertrauensstellung in verschiedenen Phasen wieder her, um die Integrität der Systemfirmware/-software zu überprüfen. Ein frühzeitiger Übergang in diesen vertrauenswürdigen Zustand bietet zusätzlichen Schutz vor potenziellen Angriffen in den Startphasen.

DRTM schützt Messungen, indem sichergestellt wird, dass sie mithilfe der Gesamtsystemspeicherverschlüsselung (Total System Memory Encryption, TSME) verschlüsselt werden. Sobald TSME festgelegt ist, wenn es nicht gelöscht werden kann, außer durch zurücksetzen des Systems. Ein neuer Verschlüsselungsschlüssel für jede Zurücksetzung stellt die Verschlüsselung mit einmaliger Verwendung für die Sicherheit sicher.

Laufzeitaufrufe an den Systemverwaltungsmodus (System Management Mode, SMM) werden auf der höchsten Ebene ausgeführt, was riskant sein kann, wenn der SMM-Code Probleme aufweist. Surface Laptop 4 mit AMD Guard schützt das System durch Abfangen der Systemverwaltungsunterbrechungen (System Management Interrupts, SMI) und verteilt die Ausführung des SMM-Codes an eine kleinere Ebene (Benutzer), um das System vor ungültigen Zugriffen auf Code und Daten zu schützen. Der SMM-Schutz verwendet Hardwareschutz, um den Zugriff auf Code, Daten und Systemressourcen einzuschränken und den Schutz vor versehentlichen oder böswilligen Vorfällen weiter zu erzwingen.

Surface Laptop 4 mit AMD-Unterstützung unterstützt zusätzlich zur robusten Firmwareupdate-Unterstützung [NIST 800-193 Platform Firmware Resiliency Guidelines.](https://nvlpubs.nist.gov/nistpubs/SpecialPublications/NIST.SP.800-193.pdf) Der Robuste Updatemechanismus für die Startfirmware verwendet einen A-B-Wiederherstellungsmechanismus, der eine automatische Wiederherstellung für eine Sicherungskopie der Firmware bereitstellt, wenn die Startsequenz während des Starts eine beschädigte Kopie der Firmware erkennt.

Weitere Informationen zu DRTM und SMM finden Sie unter ["So schützt ein Windows Defender System Guard Windows 10 – Windows Sicherheit | Microsoft-Dokumente](/windows/security/threat-protection/windows-defender-system-guard/how-hardware-based-root-of-trust-helps-protect-windows)

## <a name="remote-device-management-control"></a>Remotegeräteverwaltungssteuerung

IT-Administratoren können Surface-Geräte remote verwalten, ohne jedes Gerät physisch berühren zu müssen. Microsoft Endpoint Manager mit Intune und Windows Autopilot ermöglicht die vollständige Remoteverwaltung von Surface-Geräten aus der Azure Cloud und stellt benutzern beim Start vollständig konfigurierte Geräte bereit. Mit features wipe and retire it to repurpose a device easily for a new remote user and wipe a device that's been stolen. Dies ermöglicht schnelle und sichere Reaktionsfunktionen im Falle eines Verlusts oder Diebstahls eines Surface-Geräts, sodass Sie alle Unternehmensdaten remote entfernen und Surface als völlig neues Gerät neu konfigurieren können.

| Feature                                        | Beschreibung                                                                                                                                                                                                                                                                                                                                                                                                        | Mehr erfahren                                                                                                                                                                                                                                                              |
| ---------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| DCFI (Device Firmware Configuration Interface) | Bietet cloudweite Remotefirmwareverwaltung mit Zero-Touch-Gerätebereitstellung. Die eigene UEFI von Microsoft ermöglicht eine stärkere DCFI-Implementierung, sodass Organisationen Hardwareelemente deaktivieren und UEFI mit Intune remote sperren können. ¹                                                                                                                                                                          | [Intune-Verwaltung von Surface UEFI-Einstellungen](surface-manage-dfci-guide.md)<br> <br>[Verwalten von Surface UEFI-Einstellungen](manage-surface-uefi-settings.md)                                          |
| SEMM (Surface Enterprise Management Mode)      | Ermöglicht die zentrale Unternehmensaktivierung von UEFI-Firmwareeinstellungen in lokalen, Hybrid- und Cloudumgebungen.                                                                                                                                                                                                                                                                                           | [Surface Enterprise Management-Modus](surface-enterprise-management-mode.md)                                                                                                                                                       |
| Windows Update for Business                    | Ermöglicht IT-Administratoren, die Windows 10 Geräte in ihrer Organisation immer mit den neuesten Sicherheitsmaßnahmen, Windows Features und Surface-Firmware auf dem neuesten Stand zu halten, indem sie diese Systeme direkt mit Windows Update-Dienst verbinden. Sie können Gruppenrichtlinien oder MDM-Lösungen wie Microsoft Intune verwenden, um die Einstellungen Windows Update for Business zu konfigurieren, die steuern, wie und wann Surface-Geräte aktualisiert werden. | [Windows Update for Business](/windows/deployment/update/waas-manage-updates-wufb)<br> <br>[Verwalten und Bereitstellen von Treiber- und Firmwareupdates für Surface](manage-surface-driver-and-firmware-updates.md) |

## <a name="references"></a>Verweise

1. Surface Go und Surface Go 2 verwenden eine UEFI eines Drittanbieters und unterstützen dfci nicht. DFCI ist derzeit für Surface Laptop 4, Surface Laptop Go, Surface Book 3, Surface Laptop 3, Surface Pro 7+, Surface Pro 7 und Surface Pro X verfügbar. 

## <a name="learn-more"></a>Mehr erfahren

- [Neue Surface-PCs ermöglichen standardmäßig virtualisierungsbasierte Sicherheit (VBS), um Kunden mehr Sicherheit zu bieten.](https://www.microsoft.com/security/blog/2021/01/11/new-surface-pcs-enable-virtualization-based-security-vbs-by-default-to-empower-customers-to-do-more-securely/)
- [Studie hebt kritische Rolle des Surface-Firmwareschutzes hervor](https://techcommunity.microsoft.com/t5/surface-it-pro-blog/study-highlights-critical-role-of-surface-firmware-protection/ba-p/2245244)
- [Verbessern der Sicherheit und Compliance mit Microsoft Surface und Microsoft 365](https://techcommunity.microsoft.com/t5/surface-it-pro-blog/enhancing-security-and-compliance-with-microsoft-surface-and/ba-p/2283062)
- [Verwalten von Surface UEFI-Einstellungen](manage-surface-uefi-settings.md)
- [Intune-Verwaltung von Surface UEFI-Einstellungen](surface-manage-dfci-guide.md)
- [Project Mu](https://microsoft.github.io/mu/)
