---
title: Miracast auf vorhandenen Funknetzwerken oder LAN
description: Sie können mit Windows10 einen Miracast-Datenstrom über ein lokales Netzwerk senden.
ms.prod: surface-hub
ms.sitesec: library
author: dansimp
ms.author: dansimp
ms.topic: article
ms.date: 04/24/2020
ms.reviewer: ''
manager: laurawi
ms.localizationpriority: medium
ms.openlocfilehash: d63b3de0f76cb70fe86fff246d82cbe166278461
ms.sourcegitcommit: 109d1d7608ac4667564fa5369e8722e569b8ea36
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/27/2020
ms.locfileid: "10834206"
---
# Miracast über Infrastruktur

In Windows10, Version 1703, hat Microsoft die Möglichkeit erweitert, einen Miracast-Datenstrom über ein lokales Netzwerk anstatt über eine direkte drahtlose Verbindung zu senden. Diese Funktion basiert auf [Miracast over Infrastructure Connection Establishment Protocol (MS-MICE)](https://msdn.microsoft.com/library/mt796768.aspx).

Miracast über Infrastruktur bietet eine Reihe von Vorteilen an:

- Windows erkennt automatisch, ob das Senden von Videodaten über diesen Pfad anwendbar ist.
- Windows wählt diese Route nur, wenn die Verbindung über Ethernet oder ein sicheres WLAN-Netzwerk durchgeführt wird.
- Benutzer müssen die Art und Weise nicht ändern, wie sie eine Verbindung mit einem Miracast-Empfänger herstellen. Sie verwenden die gleiche Benutzerumgebung wie bei standardmäßigen Miracast-Verbindungen.
- Es sind keine Änderungen am aktuellen drahtlosen Treiber oder an der PC-Hardware erforderlich.
- Sie funktioniert gut mit älterer drahtloser Hardware, die nicht über Wi-Fi Direct für Miracast optimiert ist.
- Sie nutzt eine vorhandene Verbindung, die die Zeit für die Verbindung reduziert und einen sehr stabilen Stream bereitstellt.


##  <a name="how-it-works"></a>Funktionsweise

Benutzer versuchen, über Ihren WLAN-Adapter eine Verbindung mit einem Miracast-Receiver herzustellen, wie zuvor. Wenn die Liste der Miracast-Empfänger gefüllt wird, erkennt Windows10, dass der Empfänger eine Verbindung über die Infrastruktur unterstützen kann. Wählt der Benutzer einen Miracast-Empfänger, versucht Windows10, den Hostnamen des Geräts über standardmäßige DNS-Protokolle und Multicast DNS (mDNS) aufzulösen. Wenn der Name nicht über beide DNS-Methoden aufgelöst werden kann, greift Windows10 auf das Erstellen einer Miracast-Sitzung mit der standardmäßigen Wi-Fi Direct-Verbindung zurück.

> [!NOTE]
> Weitere Informationen zur Verbindungs Aushandlungs Sequenz finden Sie unter [Miracast over Infrastructure Connection Establishment Protocol (MS-Mäuse)](https://msdn.microsoft.com/library/mt796768.aspx) .




##  <a name="enabling-miracast-over-infrastructure-"></a>Aktivieren von Miracast über Infrastruktur 

Wenn Sie ein Surface Hub- oder ein anderes Windows10-Gerät haben, das auf Windows10, Version 1703, aktualisiert wurde, erhalten Sie automatisch diese neue Funktionen. Um diese in Ihrer Umgebung zu nutzen, müssen Sie sicherstellen, dass folgende Elemente zu Ihrer Bereitstellung gehören:

- Der Surface Hub oder das Gerät (Windows-PC oder Smartphone) muss Windows10, Version 1703 ausführen.
- Öffnen Sie den TCP-Port: **7250**.
- Ein Surface Hub oder Windows-PC kann als Miracast über Infrastruktur *Empfänger* dienen. Ein PC oder Telefon kann als Miracast über Infrastruktur *Quelle* dienen.
    - Als Miracast-Empfänger muss der Surface Hub oder das Gerät mit Ihrem Unternehmensnetzwerk über Ethernet oder eine sichere WLAN-Verbindung (z.B. mit WPA2-PSK oder WPA2-Enterprise-Sicherheit) verbunden sein. Wenn der Surface-Hub oder das Gerät mit einer offenen WLAN-Verbindung verbunden ist, wird sich Miracast over Infrastructure selbst deaktivieren.
    - Als Miracast-Quelle muss der Windows-PC oder Smartphone mit dem gleichen Netzwerk des Unternehmens über Ethernet oder eine sichere WLAN-Verbindung verbunden sein.
- Der DNS-Hostname (Gerätename) des Surface-Hubs oder-Geräts muss über Ihre DNS-Server aufgelöst werden können. Sie können dies erreichen, indem Sie entweder den Surface Hub automatisch über die dynamische DNS registrieren oder manuell einen A oder AAAA-Eintrag für den Surface Hub-Hostnamen erstellen. 
- Windows 10-PCs müssen mit dem gleichen Netzwerk des Unternehmens über Ethernet oder eine sichere WLAN-Verbindung verbunden sein. 
-   Auf Windows 10-PCs muss das Feature **für die Projektion auf diesen PC** in den System Einstellungen aktiviert sein, und auf dem Gerät muss eine WLAN-Schnittstelle aktiviert sein, damit Sie auf Ermittlungsanforderungen reagieren können, die nur über den WLAN-Adapter erfolgen.


Es ist wichtig zu beachten, dass Miracast über Infrastruktur kein Ersatz für das standardmäßige Miracast ist. Stattdessen ist die Funktionalität eine Ergänzung und bietet einen Vorteil für Benutzer, die dem Unternehmensnetzwerk angehören. Benutzer, die Gäste auf einem bestimmten Speicherort sind und keinen Zugriff auf das Unternehmensnetzwerk haben können auch weiterhin über die Verbindungsmethode Wi-Fi Direct eine Verbindung herstellen.

Die Einstellung **InBoxApps/WirelessProjection/PinRequired** des [SurfaceHub-Konfigurationsdienstanbieters (CSP)](https://msdn.microsoft.com/windows/hardware/commercialize/customize/mdm/surfacehub-csp) ist nicht für Miracast für Infrastruktur erforderlich. Dies liegt daran, dass Miracast über Infrastruktur nur dann funktioniert, wenn beide Geräte mit dem gleichen Netzwerk des Unternehmens verbunden sind. Dadurch wird die Sicherheitseinschränkung, die zuvor bei Miracast fehlte, entfernt. Es wird empfohlen, dass Sie auch weiterhin diese Einstellung verwenden (falls sie zuvor verwendet wurde) da Miracast auf die reguläre Miracast zurückgreift, wenn die Infrastruktur-Verbindung nicht möglich ist. 

##  <a name="faq"></a>Häufig gestellte Fragen
**Warum benötige ich weiterhin WLAN, um Miracast über die Infrastruktur zu nutzen?**<br>
Ermittlungsanforderungen zur Identifizierung von Miracast-Empfängern können nur über den WLAN-Adapter erfolgen. Nachdem die Empfänger identifiziert wurden, kann Windows 10 die Verbindung mit dem Netzwerk versuchen.
