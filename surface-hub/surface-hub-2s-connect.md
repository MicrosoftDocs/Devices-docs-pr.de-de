---
title: Verbinden von Geräten mit Surface Hub 2S
description: Auf dieser Seite wird erläutert, wie externe Geräte an Surface Hub 2S angeschlossen werden.
keywords: Trennen Sie Werte durch Kommata
ms.prod: surface-hub
ms.sitesec: library
author: greg-lindsay
ms.author: greglin
manager: laurawi
audience: Admin
ms.topic: article
ms.date: 02/24/2020
ms.localizationpriority: Medium
ms.openlocfilehash: 1c4f9b4a74b50edb5587185f28a18163a02d62f9
ms.sourcegitcommit: 109d1d7608ac4667564fa5369e8722e569b8ea36
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/27/2020
ms.locfileid: "10833325"
---
# Verbinden von Geräten mit Surface Hub 2S
Surface Hub 2S ermöglicht Ihnen, externe Geräte anzuschließen, die Anzeige auf Surface Hub 2S auf ein anderes Gerät zu überführen und mehrere Drittanbieter-Peripheriegeräte wie Videokonferenz Kameras, Konferenztelefone und Raumsystem Geräte zu verbinden.

Sie können Inhalte von ihren Geräten auf Surface Hub 2S anzeigen. Wenn das Quellgerät Windows-basiert ist, kann dieses Gerät auch TouchBack und InkBack zur Verfügung stellen, die Video-und Audiofunktionen vom angeschlossenen Gerät abspielen und auf Surface Hub 2S präsentieren. Wenn Surface Hub 2S auf ein digitales Content Protection-Signal (HDCP) mit hoher Bandbreite wie einem Blu-Ray-DVD-Player stößt, wird die Quelle als schwarzes Bild angezeigt.

> [!NOTE]
> Surface Hub 2S verwendet die ausgewählte Video Eingabe, bis eine neue Verbindung hergestellt wird, die vorhandene Verbindung unterbrochen wird oder die Connect-app geschlossen ist.

##  <a name="recommended-wired-configurations"></a>Empfohlene kabelgebundene Konfigurationen 

Im Allgemeinen empfiehlt es sich, nach Möglichkeit Native Kabelverbindungen wie USB-c zu USB-c oder HDMI zu HDMI zu verwenden. Andere Kombinationen wie MiniDP zu HDMI oder MiniDP zu USB-C funktionieren ebenfalls. Möglicherweise ist eine zusätzliche Konfiguration erforderlich, um das Videoerlebnis zu optimieren, wie es auf dieser Seite beschrieben ist.

| **Verbindung** | **Funktion** | **Beschreibung**|
| --- | --- | ---|
| HDMI + USB-C | HDMI-Eingang für Audio und Video<br><br>USB-C für TouchBack und InkBack | USB-C unterstützt TouchBack und InkBack mit der HDMI A/V-Verbindung.<br><br>Verwenden Sie USB-C für USB-A, um eine Verbindung mit Legacy Computern herzustellen.<br><br>**Hinweis:** Die besten Ergebnisse erzielen Sie, wenn Sie HDMI anschließen, bevor Sie ein USB-C-Kabel anschließen. Wenn der Computer, den Sie für HDMI verwenden, nicht mit TouchBack und InkBack kompatibel ist, benötigen Sie kein USB-C-Kabel. |
| USB-C <br> (über Compute-Modul) | Video-in <br>Audio-Eingang | Einzelnes Kabel für A/V erforderlich<br><br>TouchBack und InkBack werden unterstützt<br><br>HDCP aktiviert |
| HDMI (im Anschluss) | Video, Audio in Surface Hub 2S | Einzelnes Kabel für A/V erforderlich<br><br>TouchBack und InkBack werden nicht unterstützt<br><br>HDCP aktiviert |
| MiniDP 1,2-Ausgabe | Video Übertragung wie Spiegelung an einen größeren Projektor. | Einzelnes Kabel für A/V erforderlich |

Wenn Sie einen Gastcomputer an Surface Hub 2S über den USB-C-Port anschließen, werden mehrere USB-Geräte erkannt und konfiguriert. Diese Peripheriegeräte werden für TouchBack und InkBack erstellt. Wie in der folgenden Tabelle dargestellt, können die Peripheriegeräte im Geräte-Manager angezeigt werden, in dem doppelte Namen für einige Geräte angezeigt werden, wie in der folgenden Tabelle dargestellt.

 
|**Peripherie**| **Eintrag im Geräte-Manager** |
| ---------------------------- |------------- | ------------------------------|
| Eingabegeräte (HID) | HID-kompatibles Benutzersteuergerät<br>HID-kompatibler Stift<br>HID-kompatibler Stift (doppeltes Element)<br>HID-kompatibler Stift (doppeltes Element)<br>HID-kompatibler Touchscreen<br>USB-Eingabegerät<br>USB-Eingabegerät (doppeltes Element) |
| Tastaturen | PS/2-Standardtastatur |
| Mäuse und andere Zeigegeräte | HID-kompatible Maus |
| USB-Controller | Generischer USB-Hub<br>USB-Verbundgerät |

##  <a name="connecting-video-in-to-surface-hub-2s"></a>Anschließen von Video-in an Surface Hub 2S

Sie können Video in Surface Hub 2S mithilfe von USB-C oder HDMI eingeben, wie in der nachstehenden Tabelle angegeben.  

###  <a name="surface-hub-2s-video-in-settings"></a>Surface Hub 2S – Video-in-Einstellungen

| **Signalart** | **Auflösung** | **Bildfrequenz** | **HDMI** | **USB-C** |
| --------------- | -------------- | -------------- | -------- | --------- |
| PC              | 640x480      | 60             | X        | X         |
| PC              | 720x480      | 60             | X        | X         |
| PC              | 1024x768     | 60             | X        | X         |
| PC              | 1920 x 1080    | 60             | X        | X         |
| PC              | 3840x2560      | 30             | X        | X         |
| HDTV            | 720p           | 60             | X        | X         |
| HDTV            | 1080p          | 60             | X        | X         |
| 4K-uhd          | 3840x2560      | 30             | X        | X         |

> [!NOTE]
> Die 4K-uhd-Auflösung (3840 × 2560) wird nur unterstützt, wenn eine Verbindung mit Ports im Compute-Modul hergestellt wird. Sie wird auf den USB-Anschlüssen "Guest", die sich auf der linken, oberen und rechten Seite des Geräts befinden, nicht unterstützt.

> [!NOTE]
> Videos von einem verbundenen externen PC werden möglicherweise kleiner angezeigt, wenn Sie auf Surface Hub 2S angezeigt werden.

##  <a name="mirroring-surface-hub-2s-display-on-another-device"></a>Spiegelung von Surface Hub 2S auf einem anderen Gerät

Sie können Video an eine andere Anzeige mithilfe von MiniDP ausgeben, wie in der folgenden Tabelle angegeben.

###  <a name="surface-hub-2s-video-out-settings"></a>Surface Hub 2S – Video-Out-Einstellungen

| **Signalart** | **Auflösung** | **Bildfrequenz** | **MiniDP** |
| --------------- | -------------- | -------------- | ---------- |
| PC              | 640x480      | 60             | X          |
| PC              | 720x480      | 60             | X          |
| PC              | 1024x768     | 60             | X          |
| PC              | 1920 x 1080    | 60             | X          |
| PC              | 3840 x 2560    | 60             | X          |
| HDTV            | 720p           | 60             | X          |
| HDTV            | 1080p          | 60             | X          |
| 4K-uhd          | 3840 x 2560    | 60             | X          |


 
Surface Hub 2S umfasst einen MiniDP-Videoausgang für die Projektion von visuellem Inhalt von Surface Hub 2S auf eine andere Anzeige. Wenn Sie beabsichtigen, Surface Hub 2S zu verwenden, um zu einer anderen Anzeige zu projizieren, beachten Sie die folgenden Empfehlungen:

- **Tastatur erforderlich.** Bevor Sie beginnen, müssen Sie eine kabelgebundene oder Bluetooth-fähige externe Tastatur an Surface Hub 2S anschließen. Beachten Sie, dass eine Tastatur für Surface Hub 2S im Gegensatz zum ursprünglichen Surface Hub separat verkauft wird und nicht in der Versand Verpackung enthalten ist.<br><br>
- **Setzen Sie den doppelten Modus.** Surface Hub 2S unterstützt nur die Videoübertragung im doppelten Modus. Sie müssen den Anzeigemodus jedoch weiterhin manuell konfigurieren, wenn Sie die Verbindung zum ersten Mal herstellen:
    1. Geben Sie die **Windows-Logo-Taste**  +  **P**ein, die den Projektbereich auf der rechten Seite des Surface Hub 2S öffnet, und wählen Sie dann **doppelter** Modus aus.
    2. Wenn Sie mit ihrer Surface Hub 2S-Sitzung fertig sind, wählen Sie **Sitzung beenden**aus. Dadurch wird sichergestellt, dass die doppelte Einstellung für die nächste Sitzung gespeichert wird.<br><br>
- **Planen Sie unterschiedliche Seitenverhältnisse.** Wie bei anderen Surface-Geräten verwendet Surface Hub 2S ein 3:2-Display-Seitenverhältnis (die Beziehung zwischen der Breite und der Höhe des Displays). Das Projizieren von Surface Hub 2S auf Displays mit unterschiedlichen Seitenverhältnissen wird unterstützt. Beachten Sie jedoch, dass die MiniDP-Ausgabe, da Surface Hub 2S die Anzeige dupliziert, auch nur in einem 3:2-Seitenverhältnis angezeigt wird, was je nach dem Seitenverhältnis der empfangenden Anzeige zu einem Briefkasten-oder Gardinen Effekt führen kann. 

> [!NOTE]
> Wenn der zweite Monitor ein 16:9-Seitenverhältnis (das vorherrschende Verhältnis für die meisten Fernsehmonitore) verwendet, werden auf der linken und rechten Seite der gespiegelten Anzeige schwarze Balken angezeigt. In diesem Fall möchten Sie möglicherweise Ihre Benutzer informieren, dass es nicht erforderlich ist, die zweite Anzeige anzupassen.

##  <a name="selecting-cables"></a>Auswählen von Kabeln

Beachten Sie die folgenden Empfehlungen:

- **USB.** USB-3,1-Gen 2-Kabel.
- **MiniDP.** DisplayPort-Kabel für bis zu 3 Meter langes Zertifikat.
- **HDMI.** Wenn ein langes Kabel erforderlich ist, empfiehlt es sich, HDMI wegen der breiten Verfügbarkeit von kostengünstigen Langstrecken-Kabeln zu empfehlen, die bei Bedarf Repeater installieren können.

> [!NOTE]
> Die meisten DisplayPort-Quellen wechseln automatisch zu HDMI-Signalen, wenn HDMI erkannt wird.

##  <a name="wirelessly-connect-to-surface-hub-2s"></a>Drahtlose Verbindung mit Surface Hub 2S

Windows 10 unterstützt nativ Miracast, mit dem Sie eine drahtlose Verbindung mit Surface Hub 2S herstellen können.<br><br>

###  <a name="to-connect-using-miracast"></a>So stellen Sie eine Verbindung mit Miracast her:

1. Geben Sie auf Ihrem Windows 10-Gerät die **Windows-Logo-Taste**  +  **K**ein. 
2. Suchen Sie im Fenster Verbinden nach dem Namen des Surface Hub 2S in der Liste der Geräte in der Nähe. Sie finden den Namen des Surface Hub 2S in der unteren linken Ecke des Displays.
3. Geben Sie eine PIN ein, wenn Ihr System Administrator die PIN-Einstellung für Miracast-Verbindungen aktiviert hat. Dies erfordert, dass Sie beim erstmaligen Herstellen einer Verbindung mit Surface Hub 2S eine PIN-Nummer eingeben.

> [!NOTE]
>Wenn der Name des Surface Hub 2S-Geräts nicht wie erwartet angezeigt wird, ist es möglich, dass die vorherige Sitzung vorzeitig geschlossen wurde. Wenn dies der Fall ist, melden Sie sich direkt bei Surface Hub 2S an, um die vorherige Sitzung zu beenden und dann eine Verbindung mit Ihrem externen Gerät herzustellen.

##  <a name="connecting-peripherals-to-surface-hub-2s"></a>Anschließen von Peripheriegeräten an Surface Hub 2S

###  <a name="bluetooth-accessories"></a>Bluetooth-Zubehör

Sie können das folgende Zubehör an Surface Hub-2S über Bluetooth anschließen:

- Mäuse
- Tastaturen
- Headsets
- Lautsprecher
- Surface Hub 2 Stifte

> [!NOTE]
> Nachdem Sie ein Bluetooth-Headset oder einen Bluetooth-Lautsprecher angeschlossen haben, müssen Sie möglicherweise die Standardeinstellungen für Mikrofon und Lautsprecher ändern. Weitere Informationen finden Sie unter [**lokale Verwaltung für Surface Hub-Einstellungen**](https://docs.microsoft.com/surface-hub/local-management-surface-hub-settings).
