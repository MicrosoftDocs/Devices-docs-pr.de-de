---
title: Verbinden anderer Geräte und deren Anzeige mit Surface Hub
description: Sie können andere Geräte mit Ihrem Surface Hub verbinden, um Inhalte anzuzeigen.
ms.assetid: 8BB80FA3-D364-4A90-B72B-65F0F0FC1F0D
ms.reviewer: ''
manager: laurawi
ms.prod: surface-hub
ms.sitesec: library
author: dansimp
ms.author: dansimp
ms.topic: article
ms.date: 07/27/2017
ms.localizationpriority: medium
ms.openlocfilehash: 2d8d814d5e33a878fab066321a0d7800ae5104c0
ms.sourcegitcommit: 109d1d7608ac4667564fa5369e8722e569b8ea36
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/27/2020
ms.locfileid: "10834045"
---
# Verbinden anderer Geräte und deren Anzeige mit Surface Hub


Sie können andere Geräte mit Ihrem Microsoft Surface Hub verbinden, um Inhalte anzuzeigen. In diesem Thema werden die Funktionen des Gastmodus, Ersatz-PC-Modus und Videoausgangs beschrieben, die per Kabelverbindung verfügbar sind, sowie das Zubehör, das Sie mithilfe von [Bluetooth](#bluetooth-accessories) an den Surface Hub anschließen können.

>[!NOTE]
>Surface Hub verwendet die Video Eingabe, die Sie auswählen, bis eine neue Verbindung hergestellt wird, die vorhandene Verbindung unterbrochen wird oder die Connect-app geschlossen ist.

##  <a name="which-method-should-i-choose"></a>Welche Methode soll ich auswählen?

Für die Verbindung externer Geräte und Anzeigen mit einem Surface Hub sind mehrere Optionen verfügbar. Welche Methode Sie verwenden, hängt von Ihrem Szenario und Ihren Anforderungen ab. 

| Zweck: | Methode: |
| --- | --- |
| Spiegeln der Surface Hub-Anzeige auf ein anderes Gerät | [Videoausgang](#video-out) |
| Projizieren der Anzeige eines anderen Geräts auf den Surface Hub-Bildschirm und Interaktion sowohl mit dem Inhalt des Geräts als auch mit der integrierten Surface Hub-Oberfläche | [Gastmodus](#guest-mode) |
| Einschalten des Surface Hub von einem externen Windows 10-PC, Ausschalten des eingebetteten Surface Hub-Computers. Zusätzlich zu Stift- und Toucheingaben werden Daten von Kameras, Mikrofonen, Lautsprechern und anderen Peripheriegeräten an den externen PC gesendet. | [Ersatz-PC-Modus](#replacement-pc-mode) |


## <a name="guest-mode"></a>Gastmodus


Der Gastmodus verwendet eine Kabelverbindung, damit Benutzer Inhalte von ihren Geräten auf dem Surface Hub anzeigen können. Ist das Quellgerät Windows-basiert ist, kann das Gerät außerdem Touchback und Inkback bereitstellen. Der interne Surface Hub-PC verarbeitet Video- und Audioinhalte des verbundenen Geräts und stellt sie auf dem Surface Hub dar. Wenn Surface Hub auf ein digitales Content Protection-Signal (HDCP) mit hoher Bandbreite stößt, wird die Quelle als schwarzes Bild angezeigt. Um Ihren Inhalt anzuzeigen, ohne gegen die HDCP-Anforderungen zu verstoßen, verwenden Sie die Zehnertastatur auf der rechten Seite des Surface Hub, um direkt die externe Quelle auszuwählen.

>[!NOTE]
>Wenn eine HDCP-Datenquelle verbunden ist, verwenden Sie das seitliche Tastenfeld zum Ändern von Quelleingaben.

###  <a name="ports"></a>Anschlüsse

Verwenden Sie diese Anschlüsse auf dem Surface Hub für den Gastmodus.

<table>
<colgroup>
<col width="25%" />
<col width="25%" />
<col width="25%" />
<col width="25%" />
</colgroup>
<thead>
<tr class="header">
<th>Schnittstelle</th>
<th>Typ</th>
<th>Beschreibung</th>
<th>Funktionen</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Displayanschluss 1.1a</p></td>
<td><p>Videoeingang</p></td>
<td><p>Gast-Eingang Nr. 1</p></td>
<td><ul>
<li><p>Unterstützt die gleichzeitige Anzeige des Gasteingangs mit Gasteingang Nr. 2 und Gasteingang Nr. 3 (eine volle Auflösung, zwei Miniaturansichten).</p></li>
<li><p>HDCP-kompatibel im Umgehungsmodus</p></li>
<li><p>Touchback aktiviert</p></li>
</ul></td>
</tr>
<tr class="even">
<td><p>HDMI 1.4</p></td>
<td><p>Videoeingang</p></td>
<td><p>Gast-Eingang Nr. 2</p></td>
<td><ul>
<li><p>Unterstützt die gleichzeitige Anzeige des Gast-Eingangs mit Gast-Eingang Nr. 1 und Gast-Eingang Nr. 3 (eine volle Auflösung, zwei Miniaturansichten).</p></li>
<li><p>HDCP-kompatibel im Umgehungsmodus</p></li>
<li><p>Touchback aktiviert</p></li>
</ul></td>
</tr>
<tr class="odd">
<td><p>VGA</p></td>
<td><p>Videoeingang</p></td>
<td><p>Gast-Eingang Nr. 3</p></td>
<td><ul>
<li><p>Unterstützt die gleichzeitige Anzeige des Gast-Eingangs mit Gast-Eingang Nr. 1 und Gast-Eingang Nr. 2 (eine volle Auflösung, zwei Miniaturansichten).</p></li>
<li><p>HDCP-kompatibel im Umgehungsmodus</p></li>
<li><p>Touchback aktiviert</p></li>
</ul></td>
</tr>
<tr class="even">
<td><p>3,5-mm-Buchse</p></td>
<td><p>Audioeingang</p></td>
<td><p>Analoger Audioeingang</p></td>
<td><ul>
<li><p>Aufnahme in Surface Hub-PC, in der Regel über den VGA-Videoeingang.</p></li>
</ul></td>
</tr>
<tr class="odd">
<td><p>USB 2.0, Typ B</p></td>
<td><p>USB-Ausgang</p></td>
<td><p>Touchback</p></td>
<td><ul>
<li><p>Gibt die Steuerung der HID-Eingabegeräte Maus, Touchscreen, Tastatur und Eingabestift an den Gast-PC zurück.</p></li>
</ul></td>
</tr>
</tbody>
</table>

 

###  <a name="port-locations"></a>Anschlusspositionen

Hierbei handelt es sich um die Anschlussverbindungen, die für den Gastmodus auf dem 55"- und 84"-Surface Hub verwendet werden.

![Bild mit Gastanschlüssen am 55"-Surface Hub.](images/sh-55-guest-ports.png)

Kabelanschlüsse am 55"-Surface Hub

![Bild mit Gast-Anschlüssen am 84"-Surface Hub.](images/sh-84-guest-ports.png)

Kabelanschlüsse am 84"-Surface Hub

###  <a name="port-enumeration"></a>Anschlussaufzählung

Wenn ein Surface Hub per Kabel über den USB-Anschluss mit dem Gastcomputer verbunden ist, werden einige USB-Geräte erkannt und konfiguriert. Diese Peripheriegeräte werden für Touchback und Inkback erstellt. Die Peripheriegeräte können im Geräte-Manager angezeigt werden. Der Geräte-Manager zeigt für einige Geräte doppelte Namen an.

**Eingabegeräte (HID)**

-   HID-kompatibles Benutzersteuergerät

-   HID-kompatibler Stift

-   HID-kompatibler Stift (doppeltes Element)

-   HID-kompatibler Stift (doppeltes Element)

-   HID-kompatibler Touchscreen

-   USB-Eingabegerät

-   USB-Eingabegerät (doppeltes Element)

**Tastaturen**

-   PS/2-Standardtastatur

**Mäuse und andere Zeigegeräte**

-   HID-kompatible Maus

**USB-Controller**

-   Generischer USB-Hub

-   USB-Verbundgerät

###  <a name="guest-mode-connectivity"></a>Gastmodus-Konnektivität

Die Wahl des Videokabels hängt von der verfügbaren Eingangsquelle ab. Der Surface Hub verfügt über drei Videoeingänge: DisplayPort, HDMI und VGA. Die verfügbaren Auflösungen können Sie dem folgenden Diagramm entnehmen.

<table style="width:100%;">
<colgroup>
<col width="16%" />
<col width="16%" />
<col width="16%" />
<col width="16%" />
<col width="16%" />
<col width="16%" />
</colgroup>
<thead>
<tr class="header">
<th>Signalart</th>
<th>Auflösung</th>
<th>Bildfrequenz</th>
<th>HDMI – RGB</th>
<th>DisplayPort</th>
<th>VGA</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>PC</p></td>
<td><p>640x480</p></td>
<td><p>59,94/60</p></td>
<td><p>X</p></td>
<td><p>X</p></td>
<td><p>X</p></td>
</tr>
<tr class="even">
<td><p>PC</p></td>
<td><p>720x480</p></td>
<td><p>59,94/60</p></td>
<td><p>X</p></td>
<td><p>X</p></td>
<td></td>
</tr>
<tr class="odd">
<td><p>PC</p></td>
<td><p>1024x768</p></td>
<td><p>60</p></td>
<td><p>X</p></td>
<td><p>X</p></td>
<td><p>X</p></td>
</tr>
<tr class="even">
<td><p>HDTV</p></td>
<td><p>720p</p></td>
<td><p>59,94/60</p></td>
<td><p>X</p></td>
<td><p>X</p></td>
<td><p>X</p></td>
</tr>
<tr class="odd">
<td><p>HDTV</p></td>
<td><p>1080p</p></td>
<td><p>59,94/60</p></td>
<td><p>X</p></td>
<td><p>X</p></td>
<td><p>X</p></td>
</tr>
</tbody>
</table>

 

Die Audioquelle wird vom DisplayPort- und HDMI-Kabel bereitgestellt. Wenn Sie VGA verwenden müssen, verfügt der Surface Hub über einen Audioeingang für einen 3,5-mm-Stecker. Der Surface Hub verwendet außerdem ein USB-Kabel, das Touchback und Inkback vom Surface Hub auf kompatible Windows10-Geräte ermöglicht. Das USB-Kabel kann mit einem beliebigen Videoeingang verwendet werden, der bereits über ein Kabel angeschlossen ist.

Ein Benutzer, der zum Verbinden eines PCs den Gastmodus verwendet, würde eine der folgenden Optionen verwenden:

**DisplayPort** -- DisplayPort-Kabel und USB 2.0-Kabel

**HDMI** -- HDMI-Kabel und USB 2.0-Kabel

**VGA** -- VGA-Kabel, 3,5-mm-Audiokabel und USB 2.0-Kabel

Wenn der von Ihnen für den Gastmodus verwendete Computer nicht mit Touchback und Inkback kompatibel ist, benötigen Sie das USB-Kabel nicht.

## <a name="replacement-pc-mode"></a>Ersatz-PC-Modus


Im Ersatz-PC-Modus ist der eingebettete Computer des Surface Hub ausgeschaltet, und ein externer PC ist mit dem Surface Hub verbunden. Über Verbindungen mit Ersatz-PC-Anschlüssen erhalten Sie Zugriff auf wichtige Peripheriegeräte am Surface Hub, einschließlich Bildschirm-, Stift- und Touch-Features. Dies bedeutet, dass Ihr Surface Hub nicht über die Vorteile der Windows Team-Benutzeroberfläche verfügt, Sie verfügen jedoch über die Flexibilität, die die Bereitstellung und Verwaltung eines eigenen Windows-Computers mit sich bringt.

###  <a name="software-requirements"></a>Softwareanforderungen

Sie können den Surface Hub im Ersatz-PC-Modus mit 64-Bit-Versionen von Windows10 Home, Windows10 Pro und Windows10 Enterprise ausführen. Sie können das [Surface Hub-Ersatz-PC Treiberpaket](https://www.microsoft.com/download/details.aspx?id=52210) aus dem Microsoft Download Center herunterladen. Es wird empfohlen, dass Sie diese Treiber auf einem beliebigen Computer installieren, den Sie als Ersatz-PC verwenden möchten.

###  <a name="hardware-requirements"></a>Hardwareanforderungen

Surface Hub ist mit unterschiedlicher Hardware kompatibel. Wählen Sie die Prozessor- und Speicher-Bestätigung für Ihren Ersatz-PC, sodass er die von Ihnen verwendeten Programme unterstützt. Die Ersatz-PC-Hardware muss 64-Bit-Versionen von Windows10 unterstützen.

###  <a name="graphics-adapter"></a>Grafikkarte

Im Ersatz-PC-Modus unterstützt der Surface Hub alle Grafikkarten, die ein DisplayPort-Signal erzeugen können. Sie können die Leistung mit einer Grafikkarte verbessern, die auf die Auflösung und Aktualisierungsrate des Surface Hub abgestimmt ist. Die beste und empfohlene Ersatz-PC-Leistung auf dem Surface Hub wird beispielsweise mit einem Videosignal von 120Hz erreicht.

**55"-Surface Hubs** – Damit die beste Leistung erreicht wird, muss die Grafikkarte eine Auflösung von 1080p bei 120 Hz haben.

**84"-Surface Hubs** – Damit die beste Leistung erreicht wird, muss die Grafikkarte die Ausgabe von vier DisplayPort 1.2-Streams zur Erzeugung von 2160p bei 120 Hz (3840 x 2160 bei 120Hz vertikale Aktualisierungsrate) leisten können. Die Funktion wurde mit der NVIDIA Quadro K2200, NVIDIA Quadro K4200, NVIDIA Quadro M6000, AMD FirePro W5100, AMD FirePro W7100 und AMD FirePro W9100 überprüft. Das sind nicht die einzigen Grafikkarten – andere sind bei anderen Anbietern erhältlich. 

Fragen Sie direkt beim Anbieter nach den neuesten Treibern für die Grafikkarte.

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th>Grafikkarten-Anbieter</th>
<th>Downloadseite für Treiber</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>NVIDIA</p></td>
<td><p><a href="http://nvidia.com/Download/index.aspx" data-raw-source="[http://nvidia.com/Download/index.aspx](http://nvidia.com/Download/index.aspx)">http://nvidia.com/Download/index.aspx</a></p></td>
</tr>
<tr class="even">
<td><p>AMD</p></td>
<td><p><a href="http://support.amd.com/en-us/download" data-raw-source="[http://support.amd.com/en-us/download](http://support.amd.com/en-us/download)">http://support.amd.com/en-us/download</a></p></td>
</tr>
<tr class="odd">
<td><p>Intel</p></td>
<td><p><a href="https://downloadcenter.intel.com/" data-raw-source="[https://downloadcenter.intel.com/](https://downloadcenter.intel.com/)">https://downloadcenter.intel.com/</a></p></td>
</tr>
</tbody>
</table>

 

###  <a name="ports"></a>Anschlüsse

Ersatz-PC-Anschlüsse am 55"-Surface Hub.

![Bild mit Ersatz-PC-Anschlüssen am 55"-Surface Hub](images/sh-55-rpc-ports.png)

<table>
<colgroup>
<col width="25%" />
<col width="25%" />
<col width="25%" />
<col width="25%" />
</colgroup>
<thead>
<tr class="header">
<th>Beschreibung</th>
<th>Typ</th>
<th>Schnittstelle</th>
<th>Details</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>PC-Videoeingang</p></td>
<td><p>Videoeingang</p></td>
<td><p>DP 1.2</p></td>
<td><ul>
<li><p>Vollbildanzeige mit 1080p bei 120 Hz und Audio</p></li>
<li><p>HDCP-kompatibel</p></li>
</ul></td>
</tr>
<tr class="even">
<td><p>Interne Peripheriegeräte</p></td>
<td><p>USB-Ausgang</p></td>
<td><p>USB 2.0 Typ B</p></td>
<td><ul>
<li><p>Toucheingabe</p></li>
<li><p>Stift</p></li>
<li><p>Lautsprecher</p></li>
<li><p>Mikrofon</p></li>
<li><p>Kameras</p></li>
<li><p>NFC-Sensor</p></li>
<li><p>Umgebungslichtsensor</p></li>
<li><p>Passiver Infrarot-Sensor</p></li>
</ul></td>
</tr>
<tr class="odd">
<td><p>USB-Hub</p></td>
<td><p>USB-Ausgang</p></td>
<td><p>USB 2.0 Typ B</p></td>
<td><ul>
<li><p>Darunterliegende USB-Anschlüsse</p></li>
</ul></td>
</tr>
</tbody>
</table>

 

Ersatz-PC-Anschlüsse am 84"-Surface Hub

![Bild mit Ersatz-PC-Anschlüssen am 84"-Surface Hub](images/sh-84-rpc-ports.png)

<table>
<colgroup>
<col width="25%" />
<col width="25%" />
<col width="25%" />
<col width="25%" />
</colgroup>
<thead>
<tr class="header">
<th>Beschreibung</th>
<th>Typ</th>
<th>Schnittstelle</th>
<th>Details</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>PC-Videoeingang</p></td>
<td><p>Videoeingang</p></td>
<td><p>DP 1.2 (2x)</p></td>
<td><ul>
<li><p>Vollbildanzeige mit 2160p bei 120 Hz und Audio</p></li>
<li><p>HDCP-kompatibel</p></li>
</ul></td>
</tr>
<tr class="even">
<td><p>Interne Peripheriegeräte</p></td>
<td><p>USB-Ausgang</p></td>
<td><p>USB 2.0 Typ B</p></td>
<td><ul>
<li><p>Toucheingabe</p></li>
<li><p>Stift</p></li>
<li><p>Lautsprecher</p></li>
<li><p>Mikrofon</p></li>
<li><p>Kameras</p></li>
<li><p>NFC-Sensor</p></li>
<li><p>Umgebungslichtsensor</p></li>
<li><p>Passiver Infrarot-Sensor</p></li>
</ul></td>
</tr>
<tr class="odd">
<td><p>USB-Hub</p></td>
<td><p>USB-Ausgang</p></td>
<td><p>USB 2.0 Typ B</p></td>
<td><ul>
<li><p>Darunterliegende USB-Anschlüsse</p></li>
</ul></td>
</tr>
</tbody>
</table>

 

###  <a name="replacement-pc-setup-instructions"></a>Anweisungen zum Einrichten des Ersatz-PCs

**So verwenden Sie den Ersatz-PC-Modus**

1.  Laden Sie das [Surface Hub-Ersatz-PC-Treiberpaket](https://www.microsoft.com/download/details.aspx?id=52210) auf den Ersatz-PC herunter, und installieren Sie es.

    >[!NOTE]
    >Es wird empfohlen, den Ersatz-PC in den Standbymodus oder Ruhezustand zu versetzen, damit der Surface Hub die Anzeige ausschaltet, wenn sie nicht verwendet wird.

2.  Schalten Sie den Surface Hub über den Netzschalter neben dem Netzkabel aus.

3.  Schließen Sie die Kabel von den Ersatz-PC-Anschlüssen am Surface Hub am Ersatz-PC an. Diese Anschlüsse sind in der Regel mit einer abnehmbaren Kunststoffabdeckung versehen.

    55"-Surface Hub – schließen Sie ein DisplayPort-Kabel und zwei USB-Kabel an.

    84"-Surface Hub – schließen Sie zwei DisplayPort-Kabel und zwei USB-Kabel an.

4.  Stellen Sie den Modusschalter auf **Ersatz-PC**. Der Modusschalter befindet sich neben den Anschlüssen für den Ersatz-PC.

5.  Schalten Sie den Surface Hub über den Netzschalter neben dem Netzkabel ein.

6.  Drücken Sie den Netzschalter auf der rechten Seite des Surface Hub.

Sie können vom Surface Hub auf den internen PC wechseln.

**So wechseln Sie zurück zum internen PC**

1.  Schalten Sie den Surface Hub über den Netzschalter neben dem Netzkabel aus.

2.  Stellen Sie den Modusschalter auf „Interner PC. Der Modusschalter befindet sich neben den Anschlüssen für den Ersatz-PC.

3.  Schalten Sie den Surface Hub über den Netzschalter neben dem Netzkabel ein.

 
## <a name="video-out"></a>Videoausgang
 
Der Surface Hub umfasst einen Videoausgang für die Spiegelung visueller Inhalte vom Surface Hub auf eine andere Anzeige.

###  <a name="ports"></a>Anschlüsse

Videoausgang am 55"-Surface Hub

![Abbildungdes Videoausgangs](images/video-out-55.png)

Videoausgang am 84"-Surface Hub

![Abbildungdes Videoausgangs](images/video-out-84.png)

<table>
<thead>
<tr class="header">
<th>Beschreibung</th>
<th>Typ</th>
<th>Schnittstelle</th>
<th>Funktionen</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Spiegelung des Videoausgangs</p></td>
<td><p>Videoausgang</p></td>
<td><p>Videoausgang</p></td>
<td><ul>
<li><p>Unterstützt die Verbindung mit einem DisplayPort-Standardmonitor (unterstützt nur X4-Links mit einer Auflösung von 1080 x 60 bei 24 bpp)</p></li>
<li><p>Unterstützt die Verwendung mit HDMI-Monitoren (unterstützte Auflösung: 1080 x 60) mithilfe eines DisplayPort-zu-HDMI-Adapters</p></li>
</ul></td>
</tr>
</tbody>
</table>

##  <a name="cables"></a>Kabel

Sowohl das 55-Zoll- als auch das 84-Zoll-Surface Hub-Gerät wurden auf die Funktion mit Certified DisplayPort- und HDMI-Kabeln überprüft.  Obwohl bei Händlern auch längere Kabel erhältlich sind, die möglicherweise mit dem Surface Hub funktionieren, sind nur Kabel, die von Testlabors zertifiziert wurden, zweifelsfrei zur Verwendung mit dem Hub geeignet. DisplayPort-Kabel z.B. sind nur für eine Länge von bis zu 3m zertifiziert. Viele Händler verkaufen jedoch Kabel, die dreimal so lang sind. Wenn Sie ein langes Kabel benötigen, raten wir dringend zur Verwendung von HDMI.  HDMI bietet viele kostengünstige Lösungen zu Kabeln für große Entfernungen, z.B. die Verwendung von Repeatern. Nahezu jede DisplayPort-Quelle schaltet automatisch auf HDMI-Signalisierung um, wenn ein HDMI-Sink erkannt wird.


## <a name="bluetooth-accessories"></a>Bluetooth-Zubehör

Sie können folgendes Zubehör über Bluetooth mit dem Surface Hub verbinden:

- Mäuse
- Tastaturen
- Headsets
- Lautsprecher

>[!NOTE]
>Nachdem Sie ein Bluetooth-Headset oder einen Bluetooth-Lautsprecher angeschlossen haben, müssen Sie möglicherweise die [Standardeinstellungen für Mikrofon und Lautsprecher ändern](local-management-surface-hub-settings.md).
