---
title: Bewährte Energieeinstellungen für Surface-Geräte
description: Dieses Thema enthält Empfehlungen zu bewährten Vorgehensweisen für die Aufrechterhaltung optimaler Energieeinstellungen und erläutert, wie Surface die Energieverwaltung optimiert. Dieser Artikel bezieht sich auf alle derzeit unterstützten Surface-Geräte, einschließlich Surface Pro 7+, Surface Pro 7, Surface Pro X und Surface Laptop 3.
ms.prod: w10
ms.mktglfcycl: manage
ms.sitesec: library
author: coveminer
ms.author: greglin
ms.topic: article
ms.reviewer: ''
manager: laurawi
ms.localizationpriority: medium
ms.audience: itpro
ms.date: 1/15/2021
ms.openlocfilehash: 54aff228e8a72d413fc53bd14fe15d8ad7b15ab0
ms.sourcegitcommit: 1053479c191fd10651d31a466fad1769fb0cd28b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/16/2021
ms.locfileid: "11271399"
---
# Bewährte Energieeinstellungen für Surface-Geräte

Surface Geräte sind so konzipiert, dass sie die neuesten Fortschritte beim Energieverbrauch mobiler Geräte nutzen, um eine optimierte Oberfläche für alle Workloads zu bieten. Je nachdem, was Sie tun, passt Surface dynamisch an, wie der Strom zu einzelnen Hardwarekomponenten fließt. Dabei werden systemkomponenten zur Verarbeitung von Hintergrundaufgaben (z. B. eingehender E-Mail- oder Netzwerkdatenverkehr) vor der Rückkehr zu einem niedrigen Energieleerzustand (S0ix) für einen Moment auf die Systemkomponenten aktualisiert.

##  <a name="summary-of-recommendations-for-it-administrators"></a>Zusammenfassung der Empfehlungen für IT-Administratoren

So stellen Sie sicher, dass surface-Geräte in Ihrer gesamten Organisation vollständig von den Features der Surface-Energieoptimierung profitieren:

-  Installieren Sie die neuesten Treiber und Firmware von Windows Update oder surface Driver and Firmware MSI. Dadurch wird der Energieplan (auch als Energieprofil bezeichnet) standardmäßig erstellt und optimale Energieeinstellungen konfiguriert.  Weitere Informationen finden Sie unter Verwalten und Bereitstellen von Treiber- und [Firmwareupdates für Surface.](manage-surface-driver-and-firmware-updates.md)
- Vermeiden Sie das Erstellen von benutzerdefinierten Energieprofilen oder das Anpassen erweiterter Energieeinstellungen, die nicht in der Standardbenutzeroberfläche angezeigt werden (**System**  >  **Power & Ruhezustand).**
- Wenn Sie das Energieprofil von Geräten im Netzwerk verwalten müssen (z. B. in stark verwalteten Organisationen), verwenden Sie das Powercfg-Befehlstool, um den Energieplan aus dem Werksimage des Surface-Geräts zu exportieren und ihn dann in das Bereitstellungspaket für Ihre Surface-Geräte zu importieren. 

    >[!NOTE]
    >Sie können einen Energieplan nur über den gleichen Typ von Surface-Gerät exportieren.  Beispielsweise können Sie einen Energieplan nicht vom Surface Laptop exportieren und auf einem Computer Surface Pro.  Weitere Informationen finden Sie unter ["Energieeinstellungen konfigurieren".](https://docs.microsoft.com/windows-hardware/customize/power-settings/configure-power-settings)

- Schließen Sie die Geräte von Surface von vorhandenen Richtlinieneinstellungen für die Energieverwaltung aus. 

##  <a name="background"></a>Hintergrund

Die Art und Weise, wie Surface die Energieverwaltung implementiert, unterscheidet sich erheblich von dem früheren Betriebssystemstandard, der die Energie durch eine Reihe von Ruhezustandszuständen schrittweise reduziert und deaktiviert. Beispielsweise durch S1, S2, S3 und so weiter.

Surface wird stattdessen mit einem benutzerdefinierten Energieprofil abbilden, das ältere Funktionen für Ruhezustand und Energieverbrauch durch moderne Standbyfunktionen und dynamische Optimierung ersetzt. Dieses benutzerdefinierte Energieprofil wird über den Surface Serial Hub Driver und das Systemaggregatormodul (Sam) implementiert. Der SAM-Chip fungiert als Besitzer der Energierichtlinie des Surface-Geräts und verwendet Algorithmen, um optimale Energieanforderungen zu berechnen. In Verbindung mit Dem Windows Power Manager wird nur die genaue Energiemenge zugewiesen oder gedrosselt, die für die Funktion von Hardwarekomponenten erforderlich ist. Dieser Artikel bezieht sich auf alle derzeit unterstützten Surface-Geräte, einschließlich Surface Pro 7 und höher, Surface Laptop Go, Surface Pro 7, Surface Pro X und Surface Laptop 3.

##  <a name="utilizing-the-custom-power-profile-in-surface"></a>Verwenden des benutzerdefinierten Energieprofils in Surface

Wenn Sie die Energieoptionen auf einem Oberflächengerät verwenden, werden Sie sehen, dass ein einzelner Energieplan verfügbar ist. Dies ist das benutzerdefinierte Energieprofil. Und wenn Sie zu den erweiterten Energieeinstellungen wechseln, sehen Sie im Vergleich zu einem generischen PC unter Windows 10 eine wesentlich kleinere Teilmenge der Energieoptionen. Im Gegensatz zu generischen Geräten verfügt Surface über Firmware und benutzerdefinierte Komponenten, um diese Energieoptionen zu verwalten.


##  <a name="modern-standby"></a>Moderner Standbymodus

Das algorithmisch eingebettete benutzerdefinierte Energieprofil ermöglicht eine moderne Standbyverbindung für Surface, indem ein niedriger Energiezustand für die für Smartphones typische Sofort-/Sofortbetriebsfunktionen beibehalten wird. S0ix, auch bekannt als DEEPS (Deepest Runtime Idle Platform State), ist der Standardmäßige Energiemodus für Surface-Geräte. Der moderne Standbymodus verfügt über zwei Modi:

- **Verbundener Standbymodus.** Der Standardmodus für die minutenweise Zustellung von E-Mails, Nachrichten und cloudsynchronen Daten, verbundener Standbymodus, hält Wi-Fi und behält die Netzwerkkonnektivität bei.

- **Getrennter Standbymodus.** Ein optionaler Modus für eine längere Akkulaufzeit, getrennter Standbymodus bietet die gleiche Sofortbetriebserfahrung und spart Energie durch Deaktivieren von WLAN, Bluetooth und zugehöriger Netzwerkkonnektivität.

Weitere Informationen zum modernen Standbymodus finden Sie im [Microsoft Hardware Dev Center.](https://docs.microsoft.com/windows-hardware/design/device-experiences/modern-standby-wake-sources)

##  <a name="how-surface-streamlines-the-power-management-experience"></a>Optimieren der Energieverwaltung durch Surface 

Surface integriert die folgenden Features, mit deren Hilfe Benutzer die Energieverwaltung optimieren können:

- [Singular Power Plan](#singular-power-plan)

- [Benutzeroberfläche für vereinfachte Energieeinstellungen](#simplified-power-settings-user-interface)

- [Windows-Leistungs-Power-Schieberegler](#windows-performance-power-slider)

### Singular Power Plan

Surface ist für eine optimierte Energieverwaltung ausgelegt, die das Erstellen benutzerdefinierter Energiepläne oder das manuelle Konfigurieren von Energieeinstellungen entfällt. Microsoft optimiert die Benutzerfreundlichkeit, indem ein einzelner Energieplan (ausgeglichen) zur Vererbung der verschiedenen Energiepläne aus standardmäßigen Windows-Builds erstellt wird.

###  <a name="user-interface"></a>Benutzeroberfläche für vereinfachte Energieeinstellungen

Surface bietet eine vereinfachte Benutzeroberfläche in Übereinstimmung mit empfehlungen für die Energieeinstellung mit bewährten Vorgehensweisen. Im Allgemeinen wird empfohlen, nur einstellungen anzupassen, die auf der Standardbenutzerschnittstelle angezeigt werden, und die Konfiguration erweiterter Energieeinstellungen oder Gruppenrichtlinieneinstellungen zu vermeiden. Die Verwendung der Standardtimeouts für Bildschirm und Ruhezustand bei gleichzeitiger Vermeidung von maximalen Helligkeitsstufen ist die effektivste Methode für Benutzer, um eine längere Akkulaufzeit auf sich zu nehmen.

![Abbildung1. Vereinfachte Einstellungen & Energiemodus](images/powerintrofig1.png)

Abbildung1. Vereinfachte Energie- und Ruhezustandseinstellungen

### Windows-Leistungs-Power-Schieberegler

Surface-Geräte, auf denen Windows 10 Build 1709 und höher ausgeführt wird, verfügen über einen Netzschieberegler, mit dem Sie bei Bedarf die Akkulaufzeit priorisieren oder die Leistung bei Bedarf bevorzugen können. Sie können über die Taskleiste auf den Netzschieberegler zugreifen, indem Sie auf das Akkusymbol klicken. Ziehen Sie für eine längere Akkulaufzeit nach links (Stromsparmodus) oder ziehen Sie nach rechts, um eine schnellere Leistung zu erzielen.

![Abbildung2. Netzschieberegler](images/powerintrofig2a.png)

Abbildung2. Netzschieberegler

Der Netzschieberegler aktiviert vier Zustände, wie in der folgenden Tabelle beschrieben:

| Schiebereglermodus| Beschreibung |
|---|---|
| Stromsparmodus| Spart Energie und verlängert die Akkulaufzeit, wenn das System von einer Stromquelle getrennt ist. Wenn der Stromsparen aktiviert ist, sind einige Windows-Features deaktiviert, gedrosselt oder verhalten sich anders. Die Helligkeit des Bildschirms wird ebenfalls verringert. Der Stromsparen ist nur verfügbar, wenn der Akkustrom (DC) verwendet wird. Weitere Informationen finden Sie unter ["Stromsparen".](https://docs.microsoft.com/windows-hardware/design/component-guidelines/battery-saver)|
| Empfohlen | Bietet eine längere Akkulaufzeit als die Standardeinstellungen in früheren Versionen von Windows. |
| Bessere Leistung | Etwas bevorzugt die Leistung gegenüber der Akkulaufzeit, die als Standardschiebereglermodus funktioniert. |
| Beste Leistung | Bevorzugt Leistung gegenüber Leistung für Workloads, die eine maximale Leistung und Reaktionsfähigkeit erfordern, unabhängig vom Akkuverbrauch.|

Power Slider-Modi steuern direkt bestimmte Hardwarekomponenten, die in der folgenden Tabelle dargestellt sind.

| Komponente | Schiebereglerfunktionalität |
|---|---|
| Intel Speed Shift (CPU Energy Registers) und Hinweise zur Energieleistungseinstellung. | Wählt für optimale Leistung und Leistung die beste Betriebshäufigkeit und -leistung aus. Die Energieleistungseinstellung (Energy Performance Preference, PERFEPP) ist ein globaler Hinweis zur Energieeffizienz für die CPU. |
| Fächergeschwindigkeit (RPM)| Passt sich ggf. an geänderte Bedingungen an, z. B. das Automatische Halten des Fächers im Schiebereglermodus des Stromsparmodus.|
| Prozessorpaket-Energielimits (PL1/PL2).| Erfordert, dass die CPU ihre Frequenzoptionen verwaltet, um einen laufenden durchschnittlichen Leistungsgrenzwert sowohl für Stabile Zustands- (PL1)- als auch für geschwindigkeitsgeladene Workloads (PL2) zu verwenden.|
| Grenzwerte für die Prozessorfrequenz (IA-Grenzwerte). | Passt die Prozessor- und Grafikleistung an, sodass Prozessorkerne schneller oder langsamer als die bewertete Betriebshäufigkeit ausgeführt werden können.                                                |

>[!NOTE]
>Der Netzschieberegler ist unabhängig von den Energieeinstellungen des Betriebssystems, unabhängig davon, ob er über die Systemsteuerung/Energieoptionen, Gruppenrichtlinien oder verwandte Methoden konfiguriert ist.

Weitere Informationen finden Sie unter:

-   [Anpassen des Schiebereglers für die Leistung von Windows](https://docs.microsoft.com/windows-hardware/customize/desktop/customize-power-slider)

-   [Stromsparen.](https://docs.microsoft.com/windows-hardware/design/component-guidelines/battery-saver)

##  <a name="best-practices-for-extended-battery-life"></a>Bewährte Methoden für eine längere Akkulaufzeit


| Bewährte Methode | Wechseln Sie zu | Nächste Schritte |
|---|---|---|                                                                                                                                    
| Sicherstellen, dass Ihr Surface Gerät auf dem neuesten Stand ist| Windows Update | Geben Sie im Suchfeld der Taskleiste **Windows Update ein,** und wählen **Sie "Nach Updates suchen" aus.** |
| Wählen Sie die beste Energieeinstellung für Ihre Arbeit aus. | Netzschieberegler | Wählen Sie in der Taskleiste das Akkusymbol aus, und wählen Sie dann **"Beste**Leistung", **"Beste Akkulaufzeit"** oder irgendwo dazwischen aus.|
| Sparen von Akku bei niedrigem Akkustand | Stromsparmodus | Wählen Sie in der Taskleiste das Akkusymbol aus, und klicken Sie auf **"Akkueinstellungen".** Wählen **Sie "Stromsparen automatisch aktivieren"** aus, wenn mein Akku unter den Strom fällt, und bewegen Sie dann den Schieberegler für eine längere Akkulaufzeit weiter nach rechts. |
| Konfigurieren der optimalen Bildschirmhelligkeit | Stromsparmodus | Wählen Sie in der Taskleiste das Akkusymbol aus, und klicken Sie auf **"Akkueinstellungen",** wählen Sie "Helligkeit des unteren Bildschirms" im **Stromsparmodus aus.** |
| Energie sparen, wenn Sie nicht angeschlossen sind | Stromsparmodus| Wählen **Sie den Status "Stromsparen aktivieren" bis zum nächsten Ladezustand aus.**|
| Untersuchen Sie Probleme mit Ihren Energieeinstellungen. | Energieproblemebehandlung | Wählen Sie in der Taskleistensuche nach Einer Problembehandlung die Option **"Problembehandlung"** aus, und wählen Sie dann **"Ein/Aus"** aus, und folgen Sie den Anweisungen.|
| Überprüfen der App-Nutzung | Ihre Apps | Schließen Sie Apps.|
| Überprüfen Sie Ihr Netzkabel auf Beschädigungen.| Ihr Netzkabel | Ersetzen Sie das Netzkabel, wenn es beschädigt oder beschädigt ist.|

##  <a name="learn-more"></a>Mehr erfahren 

- [Moderner Standbymodus](https://docs.microsoft.com/windows-hardware/design/device-experiences/modern-standby-wake-sources)

<!-- -->

- [Anpassen des Schiebereglers für die Leistung von Windows](https://docs.microsoft.com/windows-hardware/customize/desktop/customize-power-slider)

- [Stromsparen](https://docs.microsoft.com/windows-hardware/design/component-guidelines/battery-saver)
- [Verwalten und Bereitstellen von Treiber- und Firmwareupdates für Surface](manage-surface-driver-and-firmware-updates.md)
