---
title: Surface Helligkeitsregler
description: In diesem Thema wird beschrieben, wie Sie die APP für die Oberflächen Helligkeitssteuerung verwenden können, um die Anzeigehelligkeit In Point-of-Sale-und Kiosk Szenarien zu verwalten.
ms.prod: w10
ms.mktglfcycl: manage
ms.pagetype: surface, devices
ms.sitesec: library
author: coveminer
ms.author: greglin
ms.topic: article
ms.reviewer: hachidan
manager: laurawi
ms.localizationpriority: medium
ms.audience: itpro
ms.openlocfilehash: 197ed9fe1abc880779ad6bb0f85d2970086395f6
ms.sourcegitcommit: 109d1d7608ac4667564fa5369e8722e569b8ea36
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/27/2020
ms.locfileid: "10833373"
---
# Surface Helligkeitsregler

Beim Bereitstellen von Surface-Geräten in Point-of-Sale oder in anderen "Always-on"-Kiosk Szenarien können Sie die Energieverwaltung mithilfe der neuen App zur Oberflächen Helligkeitssteuerung optimieren.

Verfügbar für den Download mit [Surface-Tools dafür](https://www.microsoft.com/download/details.aspx?id=46703).
Die Oberflächen-Helligkeitssteuerung dient dazu, die thermische Belastung zu verringern und den gesamten CO2-Fußabdruck für bereitgestellte Surface-Geräte zu senken.
Wenn Sie beabsichtigen, nur dieses Tool von der Download Seite abzurufen, wählen Sie die Datei **Surface_Brightness_Control_v1.16.137.0.msi** in der Liste Verfügbare Dateien aus.
Das Tool verdunkelt den Bildschirm automatisch, wenn es nicht verwendet wird, und umfasst die folgenden Konfigurationsoptionen:

- Zeitraum der Inaktivität vor dem Dimmen der Anzeige.

- Helligkeitsstufe beim Dimmen

- Maximale Helligkeitsstufe bei Verwendung.

**So führen Sie die Oberflächen Helligkeitssteuerung aus:**

- Installieren Sie surfacebrightnesscontrol.msi auf dem Zielgerät, und die Oberfläche für die Helligkeitssteuerung wird sofort gestartet.

##  <a name="configuring-surface-brightness-control"></a>Konfigurieren der Oberflächen Helligkeitssteuerung

Sie können die Standardwerte über die Windows-Registrierung anpassen. Weitere Informationen zur Verwendung der Windows-Registrierung finden Sie in der [Registrierungs Dokumentation](https://docs.microsoft.com/windows/desktop/sysinfo/registry).

1.  Führen Sie regedit an einer Eingabeaufforderung aus, um den Windows-Registrierungs-Editor zu öffnen.
    
      - Computer\HKEY\ _LOCAL \ _MACHINE \software\wow6432node\microsoft\surface\surface Helligkeitssteuerung \ 
    
    Wenn Sie eine ältere Version der Oberflächen Helligkeitssteuerung ausführen, führen Sie stattdessen den folgenden Befehl aus:
    
      - Computer\HKEY\ _LOCAL \ _MACHINE \software\microsoft\surface\surface Helligkeitssteuerung \


| Registrierungseinstellung | Daten| Beschreibung  
|-----------|------------|---------------
| Helligkeitssteuerung aktiviert  |  Standard: 01  <br> Option: 01, 00 <br> Geben Sie Folgendes ein: REG_BINARY |  Mit dieser Einstellung können Sie die Oberflächen Helligkeitssteuerung aktivieren oder deaktivieren. Um die Oberflächen-Helligkeitssteuerung zu deaktivieren, setzen Sie den Wert auf 00. Wenn Sie diese Einstellung nicht konfigurieren, ist die Oberflächen Helligkeitssteuerung aktiviert. |
| Helligkeitsregelung bei aktivierter Stromversorgung| Standard: 01 <br> Optionen: 01, 00 <br> Geben Sie Folgendes ein: REG_BINARY | Mit dieser Einstellung können Sie die Oberflächen Helligkeitssteuerung deaktivieren, wenn das Gerät direkt an die Stromversorgung angeschlossen ist. Um die Oberflächen Helligkeitssteuerung zu deaktivieren, wenn Strom angeschlossen ist, setzen Sie den Wert auf 00. Wenn Sie diese Einstellung nicht konfigurieren, ist die Oberflächen Helligkeitssteuerung aktiviert. |
| Abgeblendete Helligkeit   | Standard: 20  <br>Option: Bereich von 0-100 Prozent der Bildschirmhelligkeit <br> Datentyp: positive Ganzzahl <br> Geben Sie Folgendes ein: REG_DWORD | Mit dieser Einstellung können Sie den Helligkeitsbereich in Zeiten der Inaktivität verwalten. Wenn Sie diese Einstellung nicht konfigurieren, sinkt die Helligkeitsstufe nach 30 Sekunden Inaktivität auf 20 Prozent der vollen Helligkeit. |
Vollständige Helligkeit   | Standard: 100  <br>Option: Bereich von 0-100 Prozent der Bildschirmhelligkeit <br> Datentyp: positive Ganzzahl <br> Geben Sie Folgendes ein: REG_DWORD  | Mit dieser Einstellung können Sie den maximalen Helligkeitsbereich für das Gerät verwalten. Wenn Sie diese Einstellung nicht konfigurieren, beträgt der maximale Helligkeitsbereich 100 Prozent.|  
| Zeitüberschreitung nach Inaktivität| Standard: 30 Sekunden <br>Option: beliebiger numerischer Wert  <br>Datentyp: Ganzzahl  <br> Geben Sie Folgendes ein: REG_DWORD | Mit dieser Einstellung können Sie den Zeitraum der Inaktivität vor dem Dimmen des Geräts verwalten. Wenn Sie diese Einstellung nicht konfigurieren, beträgt das Timeout für die Inaktivität 30 Sekunden.|
| Telemetrie aktiviert | Standard: 01 <br>Option: 01, 00 <br> Geben Sie Folgendes ein: REG_BINARY  | Mit dieser Einstellung können Sie die Freigabe von Informationen zur APP-Nutzung verwalten, um die Software zu verbessern und eine bessere Benutzererfahrung bereitzustellen. Um die Telemetrie zu deaktivieren, setzen Sie den Wert auf 00. Wenn Sie diese Einstellung nicht konfigurieren, werden Telemetrie-Informationen in Übereinstimmung mit den [Microsoft-Datenschutzbestimmungen](https://privacy.microsoft.com/privacystatement)für Microsoft freigegeben. |

##  <a name="changes-and-updates"></a>Änderungen und Updates

###  <a name="version-1.16.137"></a>Version 1.16.137<br>
*Veröffentlichungsdatum: 22 Oktober 2019*<br>
Diese Version der Oberflächen Helligkeitssteuerung bietet Unterstützung für die folgenden Optionen:-neu kompiliert für x86, Hinzufügen von Unterstützung für Surface pro 7, Surface pro X und Surface Laptop 3. 

###  <a name="version-1.12.239.0"></a>Version 1.12.239.0
*Veröffentlichungsdatum: 26 April 2019*<br>
Diese Version der Oberflächen Helligkeitssteuerung bietet folgende Unterstützung:
- Touch Delay-Korrekturen.


##  <a name="related-content"></a>Verwandte Themen

- [Einstellung der Batterie Grenze](battery-limit.md)
