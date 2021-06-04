---
title: Problembehandlung für Miracast auf Surface Hub
description: Enthält Informationen zur Problembehandlung von Miracast auf Surface Hub.
ms.prod: surface-hub
ms.sitesec: library
author: dansimp
ms.author: dansimp
ms.topic: article
ms.date: 06/20/2019
ms.reviewer: ''
manager: laurawi
ms.localizationpriority: medium
ms.openlocfilehash: 96c7c42fe0176f275a8657165d88bf447e57772b
ms.sourcegitcommit: 109d1d7608ac4667564fa5369e8722e569b8ea36
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/27/2020
ms.locfileid: "10834191"
---
# Problembehandlung von Miracast auf Surface Hub

Surface Hub unterstützt die drahtlose Projektion über das Miracast-Protokoll. Die meisten drahtlosen Monitore und Adapter auf dem Markt verwenden heute die ursprüngliche Implementierung von Miracast. Surface Hub verwendet eine etwas andere Version von Miracast,die **Miracast Autonomous Group Owner (AGO)** genannt wird. Ein allgemeiner Schritt zur Problembehandlung bei der fehlerhaften Projektion auf Surface Hub ist das Testen der Projektion auf einen anderen drahtlosen Monitor oder Adapter. Allerdings verwenden diese Geräte in den meisten Fällen nicht Miracast AGO und verarbeiten drahtlose Projektion nicht auf die gleiche Weise, wie Surface Hub sie behandelt.

Bei herkömmlichem Miracast verbindet das projizierende Gerät die Installation des Zugangspunkts mit einem Miracast-fähigen Monitor. Der Monitor sendet anschließend den Datenverkehr an das projizierte Gerät zurück, indem er den Netzwerkkanal des projizierten Geräts verwendet. Miracast AGO ist ein Verbindungsprozess in zwei Schritten:

- Der erste Schritt besteht aus einer erstmalige Verbindung mit 2,4 GHz. 
- Nach diesem ersten Handshake sendet das projizierende Gerät den Datenverkehr an den Monitor mithilfe der Wireless-Kanal-Einstellungen auf dem Bildschirm. Wenn Surface Hub mit einem WLAN-Netzwerk verbunden ist, wird der Zugangspunkt denselben Kanal wie das verbundene Netzwerk verwenden, andernfalls verwendet er den Miracast-Kanal der Einstellungen.

Es gibt in der Regel zwei Arten von Problemen mit Miracast auf Surface Hub: [Verbindung](#connect-issues) und [Leistung](#performance-issues). In beiden Fällen empfiehlt es sich, eine allgemeine Übersicht über die Drahtlosnetzwerk Aktivitäten am Standort des Surface Hub zu erhalten. Wenn Sie ein Netzwerk-Überprüfungstool durchführen, werden die verfügbaren Netzwerke und die Channelverwendung in der Umgebung angezeigt.

## Probleme bei der Verbindung

Stellen Sie sicher, dass sowohl WLAN als auch Miracast in den Einstellungen auf Surface Hub aktiviert sind. 

Wenn ein Netzwerkscan ausgeführt wurde, sollte Surface Hub Miracast als Zugangspunkt aufführen. Wenn das Miracast-Netzwerk von Surface Hub bei der Überprüfung angezeigt wird, es aber nicht als verfügbares Gerät angezeigt wird, können Sie versuchen, den von Surface Hub verwendeten Miracast-Kanal anzupassen. 

Wenn Surface Hub mit einem WLAN-Netzwerk verbunden ist werden die gleichen Kanaleinstellungen als der WLAN-Zugangspunkt für den Miracast-Zugangspunkt verwendet. Trennen Sie Surface Hub für die Problembehandlung von WLAN-Netzwerken (lassen Sie WLAN aktiviert), damit Sie den Kanal für Miracast kontrollieren können. Sie können manuell in den Einstellungen den Miracast-Kanal auswählen. Sie müssen Surface Hub nach jeder Änderung neu starten. Im Allgemeinen sollten Sie Kanäle verwenden, die die hohe Auslastung des Netzwerk-Scans nicht anzeigen.

Es ist auch möglich, dass das Verbindungsproblem auf dem Gerät das Ergebnis eines Problems des verbundenen Geräts ist. Wenn das projizierende Gerät Windows ausführt, sollte dies Windows8.1 oder höher sein, um Miracast vollständig zu unterstützen. In diesem Fall sollten Sie für die Problembehandlung das projizierende Gerät vom WLAN-Netzwerk trennen. Dadurch vermeiden Sie jeglichen Kanalwechsel zwischen dem Kanal des Zugangspunkts und dem festgelegten Miracast-Kanal auf Surface Hub. Außerdem können einige der Gruppenrichtlinien und Firewall-Einstellungen an ein WLAN-Netzwerk gebunden sein.

###  <a name="check-drivers"></a>Überprüfen von Treibern

Es wird auch empfohlen, sicherzustellen, dass die neuesten Treiber und Updates auf dem projizierten Gerät installiert sind. Öffnen Sie im Geräte-Manager den WLAN-Adapter und die Grafikkarte und suchen Sie nach einer aktualisierten Treiber-Version. [Hotfix 3120232](https://support.microsoft.com/help/3120232/poor-wireless-performance-on-5-ghz-connections-on-surface-pro-3-and-surface-3) wird für Surface Pro 3 und Surface Pro 4 dringend empfohlen, wenn sie einen älteren WLAN-Treiber haben. 

###  <a name="check-for-miracast-support"></a>Überprüfen Sie die Miracast-Unterstützung

Als Nächstes stellen Sie sicher, dass Miracast auf dem Gerät unterstützt wird. 

1. Drücken Sie die Windows-Taste + R und geben Sie `dxdiag` ein. 
2. Klicken Sie auf "alle Informationen speichern". 
3. Öffnen Sie die gespeicherten dxdiag.txt und suchen Sie nach **Miracast**. Es sollte **Verfügbar, mit HDCP** angezeigt werden. 
    
###  <a name="check-firewall"></a>Firewallüberprüfung
    
Die Windows-Firewall kann den Miracast-Datenverkehr blockieren. Am einfachsten testen Sie dies, indem Sie die Firewall deaktivieren und die Projektion testen. Wenn die Firewall deaktiviert ist und Miracast funktioniert, fügen Sie eine Ausnahme für

    C:\Windows\System32\WUDFHost.exe
    Allow In/Out connections for TCP and UDP, Ports: All.

###  <a name="check-group-policy-settings"></a>Gruppenrichtlinieneinstellungen überprüfen

Bei in die Domäne eingebundenen Geräten können Gruppenrichtlinien auch Miracast blockieren. 

1. Verwenden Sie die Windows-Taste + R und geben Sie `rsop.msc` zum Ausführen des **Resultant Set of Policy**-Snap-Ins ein. Dadurch werden die aktuellen angewendeten Richtlinien auf dem PC angezeigt. 
2. Überprüfen Sie **Computerkonfiguration** > **Windows-Einstellungen** > **Sicherheitseinstellungen** > **Drahtlosnetzwerkrichtlinien (IEEE 802.11)**. Es sollte eine Einstellung für die WLAN-Richtlinien vorhanden sein. 
3. Doppelklicken Sie auf die Einstellung für die WLAN-Richtlinien, damit ein Dialogfeld angezeigt wird. 
4. Öffnen Sie die Registerkarte **Netzwerkberechtigungen** und wählen Sie **Erstellen von Profilen für alle Benutzer für jeden zulassen**.

###  <a name="check-event-logs"></a>Prüfen Sie die Ereignisprotokolle

Als letztes sollten Sie die Ereignisprotokolle überprüfen. Miracast-Ereignisse werden unter **Wlanautoconfig** aufgezeichnet. Dies trifft für den Surface Hub und das projizierte Gerät zu. Wenn Sie Surface Hub-Protokolle exportieren, können Sie die Wlanautoconfig des Surface-Hubs im Ordner **WindowsEventLog** anzeigen. Fehler im Ereignisprotokoll können zusätzliche Details aufzeigen, wo die Verbindung fehlschlägt.

## Leistungsprobleme

Nachdem die drahtlose Projektion verbunden ist, können Sie Leistungsprobleme sehen, die Latenzen verursachen. Dies ist im Allgemeinen die Folge einer allgemeinen Kanalüberlastung oder einer Situation, die bewirkt, dass der Kanal gewechselt wird. 

Wenden Sie sich bei Kanalüberlastungen an die Netzwerk-Überprüfung und versuchen Sie, Kanäle mit weniger Datenverkehr zu verwenden.

Ein Kanalwechsel wird generell dadurch verursacht, dass der WLAN-Adapter zum Senden von Datenverkehr mehrere Kanäle verwenden muss. Bestimmte Kanäle unterstützen Dynamic Frequency Selection (DFS). DFS wird auf den Kanälen 49 bis 148 verwendet. Einige WLAN-Treiber zeigen eine schlechte Leistung an, wenn sie mit einem DFS-Kanal verbunden sind. Wenn Sie Miracast-Leistungseinbußen auf einem verbundenen DFS-Kanal sehen, versuchen Sie die Projektion auf einem nicht mit DFS verbundenen Kanal durchzuführen. Sowohl Surface Hub als auch das projizierte Gerät sollten einen nicht mit DFS verbundenen Kanal verwenden.

Wenn Surface Hub und das projizierte Gerät beide mit WLAN verbunden sind, aber unterschiedliche Zugangspunkte mit verschiedenen Kanälen verwenden, zwingt dies Surface Hub und das projizierte Gerät den Kanal zu wechseln, während Miracast verbunden ist. Dies führt zu einer schlechten drahtlosen Projektion und schlechter Netzwerkleistung über WLAN. Das Umschalten zwischen den Kanälen wirkt sich auf die Leistung des gesamten WLAN-Datenverkehrs und nicht nur auf die drahtlose Projektion aus. 

Das Umschalten zwischen Kanälen tritt auch dann auf, wenn das projizierte Gerät mit einem WLAN-Netzwerk verbunden ist, das einen anderen Kanal als den Kanal nutze, den Surface Hub für Miracast verwendet. Daher empfiehlt es sich, den Miracast-Kanal des Surface Hub auf denselben Kanal wie den am häufigsten verwendeten Zugriffspunkt festzulegen. 

Wenn mehrere WLAN-Netzwerke oder Zugangspunkte in der Umgebung vorhanden sind, ist das Umschalten zwischen den Kanälen unvermeidbar. Dies wird am besten behandelt, indem Sie sicherstellen, dass alle WLAN-Treiber auf dem neuesten Stand sind.

##  <a name="contact-support"></a>Support kontaktieren

Wenn Sie Fragen haben oder Hilfe benötigen, können Sie [eine Supportanfrage erstellen](https://support.microsoft.com/supportforbusiness/productselection).
