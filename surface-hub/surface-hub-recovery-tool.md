---
title: Verwenden des Wiederherstellungstools für Surface Hub
description: So verwenden Sie das Surface Hub-Wiederherstellungstool zum erneuten Abbilden des SSD.
ms.assetid: FDB6182C-1211-4A92-A930-6C106BCD5DC1
ms.reviewer: ''
manager: laurawi
keywords: Surface Hub verwalten
ms.prod: surface-hub
ms.sitesec: library
author: dansimp
ms.author: dansimp
ms.topic: article
ms.date: 02/11/2020
ms.localizationpriority: medium
ms.openlocfilehash: 0cc444eab51e9c3cc0bf2f9c2f0c36ac491906b1
ms.sourcegitcommit: 7b09b4bc757c5385c4f5560713cb03448afde9ea
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/16/2021
ms.locfileid: "11339366"
---
# Verwenden des Wiederherstellungstools für Surface Hub

Das [Microsoft Surface Hub Recovery Tool](https://www.microsoft.com/download/details.aspx?id=52210) hilft Ihnen, ein neues Image ihres Surface Hub Solid State Drive (SSD) mithilfe eines Windows 10-Desktopgeräts zu erstellen, ohne die Unterstützung aufforderen oder ssd ersetzen zu müssen. Mit diesem Tool können Sie ein Reimage einer SSD mit einem unbekannten Administratorkennwort, Startfehlern, nicht abgeschlossenen Cloudwiederherstellungen oder einem Gerät mit einer älteren Version des Betriebssystems durchführen. Das Tool korrigiert nicht physisch beschädigte SSDs.

Zum erneuten Abbilden der Surface Hub-SSD mithilfe des Wiederherstellungstools müssen Sie das SSD vom Surface Hub entfernen, das Laufwerk mit dem USB-zu-SATA-Kabel verbinden und dann das Kabel mit dem Desktop-PC verbinden, auf dem das Wiederherstellungstool installiert ist. Weitere Informationen zum Entfernen des vorhandenen Laufwerks vom Surface Hub finden Sie unter [Surface Hub-SSD-Ersatz.](surface-hub-ssd-replacement.md)

> [!IMPORTANT]
> Lassen Sie das Gerät nicht in den Ruhezustand wechseln oder unterbrechen Sie den Download der Bilddatei.

Wenn das Tool beim Reimaging ihres Laufwerks nicht erfolgreich ist, wenden Sie sich an [den Surface Hub-Support.](https://support.microsoft.com/help/4037644/surface-contact-surface-warranty-and-software-support)

##  <a name="prerequisites"></a>Voraussetzungen

###  <a name="mandatory"></a>Mandatory

- Host-PC mit 64-Bit-Version von Windows 10, Version 1607 oder höher.
- Internetzugriff
- Öffnen von USB 2.0 oder höher
- USB-zu-SATA-Kabel
- 10 GB freier Speicherplatz auf dem Hostcomputer
- SSDs, die mit Surface Hub oder einer SSD ausgeliefert wurden, die vom Support als Ersatz bereitgestellt werden. Von Microsoft nicht bereitgestellte SSDs werden nicht unterstützt.

###  <a name="recommended"></a>Empfohlen

- High-Speed-Internetverbindung
- Öffnen des USB 3.0-Ports
- USB 3.0 oder höher USB-zu-SATA-Kabel
- Das Imageerstellungstool wurde mit der folgenden Kabelerstellung und dem folgenden Modell getestet:
    - Startech USB312SAT3CB
    - Rosawill RCUC16001
    - Ugreen 20231

##  <a name="download-surface-hub-recovery-tool"></a>Surface Hub Recovery Tool herunterladen

Das Surface Hub-Wiederherstellungstool steht unter dem Dateinamen "Surface Hub-Wiederherstellungstool" unter dem Namen "Surface Hub Tools for [IT"](https://www.microsoft.com/download/details.aspx?id=52210) zum **SurfaceHub_Recovery_v2.7.139.0.msi. **

> [!IMPORTANT]
> Diese version, released February 11, 2021, replaces the earlier build, which is no longer functional. Wenn Sie dieses Tool zuvor heruntergeladen haben, deinstallieren Sie es, und installieren Sie die aktuelle Version.

Klicken Sie zum Starten des Downloads auf **"Herunterladen",** **wählenSurfaceHub_Recovery_v2.7.139.0.msi** aus der Liste aus, und klicken Sie auf **"Weiter".** Wählen Sie im Popup eine der folgenden Optionen aus:

- Klicken **Sie auf "Ausführen",** um die Installation sofort zu starten.
- Klicken **Sie auf "Speichern",** um den Download zur späteren Installation auf Ihren Computer zu kopieren.

Installieren Sie das Surface Hub-Wiederherstellungstool auf dem Host-PC.

##  <a name="run-surface-hub-recovery-tool"></a>Ausführen des Surface Hub-Wiederherstellungstools

1. Wählen Sie auf dem Host-PC die **Startschaltfläche** aus, scrollen Sie durch die alphabetische Liste auf der linken Seite, und wählen Sie die Verknüpfung des Wiederherstellungstools aus.

    ![Microsoft Surface Hub Recovery Tool](images/shrt-shortcut.png)

2. Klicken Sie auf **Start**.

    ![Schaltfläche "Wiederherstellungstool starten"](images/shrt-start.png)


3. Klicken Sie **im Fenster "Anleitung"** auf **"Weiter".**

    ![Lassen Sie Ihren Computer nicht in den Ruhezustand wechseln.](images/shrt-guidance.png)

4. Klicken Sie im Fenster "Bild auswählen" entweder **auf RS2** oder dessen Nachfolger **20H2,** wählen Sie **"Weiter"** und dann **"Bild herunterladen" aus.**

     ![Bild "Wiederherstellungstool Auswählen des ](images/shrt-select-image.png) ![ Bildwiederherstellungstools herunterladen"](images/shrt-download-image.png)

5. Die Zeit zum Herunterladen des Wiederherstellungsabbilds hängt von der Geschwindigkeit der Internetverbindung ab. Bei einer durchschnittlichen Unternehmensverbindung kann es bis zu einer Stunde dauern, bis die 8 GB-Bilddatei heruntergeladen wurde.

    ![Bild herunterladen](images/shrt-download.png)



5. Wenn der Download abgeschlossen ist, werden Sie vom Tool angewiesen, ein Laufwerk mit SSD zu verbinden. Wenn das Tool das angeschlossene Laufwerk nicht finden kann, besteht die Wahrscheinlichkeit, dass das verwendete Kabel den Namen der SSD nicht an Windows meldet.  Das Imageerstellungstool muss den Namen des Laufwerks als "LITEON L CH-128V2S USB-Gerät" finden, bevor es fortgesetzt werden kann.  Weitere Informationen zum Entfernen des vorhandenen Laufwerks vom Surface Hub finden Sie unter [Surface Hub-SSD-Ersatz.](surface-hub-ssd-replacement.md)

    ![Verbinden von SSD](images/shrt-drive.png)

6. Wenn das Laufwerk erkannt wird, klicken **Sie auf "Start",** um mit dem erneuten Imageerstellungsprozess zu beginnen. Klicken Sie in der Warnung, dass alle Daten auf dem Laufwerk gelöscht werden, auf **OK**.



    Vor dem Anwenden des Systemimages auf das Laufwerk wird das SSD neupartitioniert und formatiert. Das Kopieren der Systemdateien dauert ca. 30 Minuten, kann jedoch je nach Geschwindigkeit des USB-Bus, des verwendeten Kabels oder der auf dem System installierten Antivirensoftware länger dauern.



##  <a name="troubleshooting-and-common-problems"></a>Problembehandlung und häufige Probleme

Problem | Anmerkungen
--- | ---
Das Tool kann das Image der SSD nicht abbilden. | Stellen Sie sicher, dass Sie ein vom Hersteller bereitgestelltes SSD und eines der getesteten Kabel verwenden.
Der Reimagingprozess wird angehalten/eingefroren angezeigt. | Es ist sicher, das Surface Hub Recovery Tool ohne schlechte Auswirkungen auf das SSD zu schließen und neu zu starten.
Das Laufwerk wird vom Tool nicht erkannt | Stellen Sie sicher, dass die Surface Hub-SSD als Lite-On "LITEON L CH-128V2S-USB-Gerät" aufgezählt wird.  Wenn das Laufwerk als ein anderes benanntes Gerät erkannt wird, ist das aktuelle Kabel nicht kompatibel. Versuchen Sie es mit einem anderen Kabel oder einem der oben aufgeführten getesteten Kabel.
Fehler: -2147024809 | Öffnen Sie den Datenträger-Manager, und entfernen Sie die Partitionen auf dem Surface Hub-Laufwerk.  Trennen Sie das Laufwerk, und stellen Sie es wieder mit dem Hostcomputer wieder her. Starten Sie das Imageerstellungstool erneut.

Wenn das Tool beim Reimaging ihres Laufwerks nicht erfolgreich ist, wenden Sie sich an [den Surface Hub-Support.](https://support.microsoft.com/help/4037644/surface-contact-surface-warranty-and-software-support)

##  <a name="version-history"></a>Versionsverlauf


###  <a name="version-v2.7.139.0"></a>Version v2.7.139.0

*Veröffentlichungsdatum: 11. Februar 2021*<br>
Diese Version des Surface Hub-Wiederherstellungstools bietet Unterstützung für Folgendes:

- Sicherheitsupdate


###  <a name="version-v2.0.139.0"></a>Version v2.0.139.0

> [!IMPORTANT]
> Diese Version ist nicht mehr funktionsfähig. Laden Sie die oben aufgeführte aktuelle Version herunter. 

*Veröffentlichungsdatum: 18. Dezember 2020*<br>
Diese Version des Surface Hub-Wiederherstellungstools bietet Unterstützung für Folgendes:
- Update zur Unterstützung von Windows 10 Team 2020 Update (20H2)
- Verbesserungen der Benutzerfreundlichkeit
- Architekturänderungen
- Telemetrieergungen

