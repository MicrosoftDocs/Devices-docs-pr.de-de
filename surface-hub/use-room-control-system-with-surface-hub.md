---
title: Verwenden eines Raumsteuerungssystems (Surface Hub)
description: Raumsteuerungssysteme können mit Microsoft Surface Hub verwendet werden.
ms.assetid: DC365002-6B35-45C5-A2B8-3E1EB0CB8B50
ms.reviewer: ''
manager: laurawi
keywords: Verwenden eines Raumsteuerungssystems, Surface Hub
ms.prod: surface-hub
ms.sitesec: library
author: dansimp
ms.author: dansimp
ms.topic: article
ms.date: 07/27/2017
ms.localizationpriority: medium
ms.openlocfilehash: 0e3b1706e58edb6e37156eda8d06fb0faefa4c91
ms.sourcegitcommit: 109d1d7608ac4667564fa5369e8722e569b8ea36
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/27/2020
ms.locfileid: "10832653"
---
# Verwenden eines Raumsteuerungssystems (Surface Hub)


Raumsteuerungssysteme können mit Microsoft Surface Hub verwendet werden.

Die Verwendung eines Raumsteuerungssystems mit Surface Hub umfasst die Verbindung von Raumsteuerungshardware mit Surface Hub. Diese wird in der Regel über den seriellen RJ11-Anschluss unten an Surface Hub hergestellt.

##  <a name="terminal-settings"></a>Terminaleinstellungen

Zum Herstellen der Verbindung mit einem Raumsteuerungssystem ist keine Konfiguration von Terminaleinstellungen an Surface Hub erforderlich. Wenn Sie einen PC oder Laptop mit Surface Hub verbinden und serielle Befehle von Surface Hub senden möchten, können Sie ein Terminalemulationsprogramm wie Tera Term oder PuTTY verwenden. 

| Einstellung | Wert |
| --- | --- |
| Baudrate | 115200 |
| Datenbits | 8 | 
| Stoppbits | 1 |
| Parität | keine |
| Flusssteuerung | keine |
| Zeilenvorschub | bei jedem Wagenrücklauf |
 

##  <a name="wiring-diagram"></a>Verdrahtungsdiagramm

Sie können mit einem standardmäßigen RJ-11 (6P6C)-Stecker den seriellen Surface Hub-Anschluss mit einem Raumsteuerungssystem verbinden. Dies ist die empfohlene Methode. Sie können auch ein RJ-11-Kabel mit vier Leitern verwenden, aber diese Methode wird nicht empfohlen.

In diesem Diagramm ist die korrekte Pinbelegung dargestellt, die für ein RJ-11 (6P6C)-auf-DB9-Kabel verwendet wird.

![Abbildung des Verdrahtungsdiagramms](images/room-control-wiring-diagram.png)

##  <a name="command-sets"></a>Befehlssätze

Raumsteuerungssysteme verwenden gängige Besprechungsraumszenarien für Befehle. Befehle stammen vom Raumsteuerungssystem und werden über eine serielle Verbindung an einen Surface Hub kommuniziert. Befehle sind ASCII-basiert, und der Surface Hub bestätigt auftretende Zustandsänderungen.

Der folgende Befehlsmodifizierer sind verfügbar. Befehle werden mit einem Neue-Zeile-Zeichen (\n) beendet. Antworten können zu einem beliebigen Zeitpunkt als Reaktion auf Zustandsänderungen erfolgen, die nicht direkt von einem Verwaltungsport-Befehl ausgelöst wurden.

| Modifizierer | Ergebnis |
| --- | --- |
| + | Erhöhen eines Werts |
| - | Verringern eines Werts |
| = | Festlegen eines einzelnen Werts |
| ? | Abfragen für einen aktuellen Wert |
 

##  <a name="power"></a>Ein/Aus

Der Surface Hub kann sich in einem der folgenden Ein/Aus-Zustände befinden.

| Zustand | Energy Star-Zustand| Beschreibung |
| --- | --- | --- |
| 0 | S5 | Aus |
| 1 | - | Einschalten (unbestimmt) |
| 2 | S3 | Ruhezustand |
| 5 | S0 | Bereit |


Im Ersatz-PC-Modus stehen nur die Energiezustände „Bereit“ und „Aus“ zur Verfügung, die lediglich die Anzeige ändern. Der Verwaltungsport kann nicht zum Einschalten des Ersatz-PCs verwendet werden. 

| Zustand | Energy Star-Zustand| Beschreibung |
| --- | --- | --- |
| 0 | S5 | Aus |
| 5 | S0 | Bereit |

Bei Steuerungsgeräten müssen alle Zustände außer „5/Bereit" als deaktiviert betrachtet werden. Jeder PowerOn-Befehl führt zu zweizustands Änderungen und Antworten. 

| Befehl | Zustandsänderung| Antwort |
| --- | --- | --- |
| PowerOn | Das Gerät wird eingeschaltet (Anzeige + PC).</br></br>Der PC-Dienst benachrichtigt den SMC darüber, dass der PC bereit ist. |  Power=0</br></br>Power=5 |
| PowerOff | Das Gerät wechselt in den Umgebungszustand (PC eingeschaltet, Anzeige abgeblendet). |  Power=0 |
| Power? |  Der SMC meldet den zuletzt bekannten Energiezustand. |  Leistung=<#> |



##  <a name="brightness"></a>Helligkeit

Die aktuelle Helligkeitsstufe umfasst einen Bereich von 0 bis 100.

Änderungen der Helligkeitsstufen können durch ein Raumsteuerungssystem oder ein anderes System gesendet werden.

| Befehl | Zustandsänderung |Antwort |
| --- | --- | --- |
| Brightness+ | Der System-Managementcontroller (SMC) sendet den Befehl zum Erhöhen der Helligkeit.</br></br>Der PC-Dienst im Raumsteuerungssystem benachrichtigt den SMC über die neue Helligkeitsstufe. |  Brightness = 51 |
| Brightness- |  Der SMC sendet den Befehl zum Verringern der Helligkeit.</br></br>Der PC-Dienst benachrichtigt den SMC über die neue Helligkeitsstufe. | Brightness = 50 |

##  <a name="volume"></a>Volume

Die aktuelle Lautstärkestufe ist ein Bereich von 0 bis 100.

Änderungen der Lautstärkestufen können durch ein Raumsteuerungssystem oder ein anderes System gesendet werden.

>[!NOTE]
>Der Befehl „Volume” steuert nur die Lautstärke für den eingebetteten oder den Ersatz-PC-Modus, nicht über [Gastquellen](connect-and-display-with-surface-hub.md).

| Befehl | Zustandsänderung | Antwort</br>(Aktiviert im [Ersatz-PC-Modus](connect-and-display-with-surface-hub.md#replacement-pc-mode)) |
| --- | --- | --- |
| Volume+ |  Der SMC sendet den Befehl zum Erhöhen der Lautstärke.</br></br>Der PC-Dienst benachrichtigt den SMC über die neue Lautstärkestufe. |  Volume = 51 |
| Volume- |  Der SMC sendet den Befehl zum Verringern der Lautstärke.</br></br>Der PC-Dienst benachrichtigt den SMC über die neue Lautstärkestufe. |  Volume = 50 |


 

##  <a name="mute-for-audio"></a>Stummschalten für Audio

Audio kann stummgeschaltet werden.

| Befehl | Zustandsänderung | Antwort |
| --- | --- | --- |
| AudioMute+ |  Der SMC sendet den Befehl zum Stummschalten von Audioinhalten.</br></br>Der PC-Dienst benachrichtigt den SMC darüber, dass Audioinhalte stummgeschaltet sind. |  keine |


 

##  <a name="video-source"></a>Videoquelle

Es können mehrere Anzeigequellen verwendet werden.

| Zustand | Beschreibung | 
| --- | --- |
| 0 |  Integrierter PC |
| 1 |  DisplayPort |
| 2 |  HDMI |
| 3 |  VGA |


 

Änderungen der Anzeigequelle können durch ein Raumsteuerungssystem oder ein anderes System gesendet werden.

| Befehl | Zustandsänderung | Antwort |
| --- | --- | --- |
| Quelle=# |  Der SMC wechselt zur gewünschten Quelle.</br></br>Der PC-Dienst benachrichtigt den SMC darüber, dass die Anzeigequelle gewechselt wurde. |  Source=&lt;#&gt; |
| Source+ |  Der SMC wechselt zur nächsten aktiven Eingabequelle.</br></br>Der PC-Dienst benachrichtigt den SMC über die aktuelle Eingabequelle. |  Source=&lt;#&gt; |
| Source- | Der SMC wechselt zur vorherigen aktiven Eingabequelle.</br></br>Der PC-Dienst benachrichtigt den SMC über die aktuelle Eingabequelle. |  Source=&lt;#&gt; |
| Source? |  Der SMC fragt beim PC-Dienst die aktive Eingabequelle ab.</br></br>Der PC-Dienst benachrichtigt den SMC über die aktuelle Eingabequelle. | Source=&lt;#&gt; |

##  <a name="errors"></a>Fehler

Fehler werden entsprechend dem Format in dieser Tabelle zurückgegeben.

| Fehler | Hinweise |
| --- | --- |
| Fehler: Unbekannter Befehl '&lt;Eingabe&gt;'. |  Die Anweisung enthält einen unbekannten anfänglichen Befehl. Beispielsweise wäre „VOL+“ ungültig und würde „Fehler: Unbekannter Befehl 'VOL'“ zurückgeben. |
| Fehler: Unbekannter Operator '&lt;Eingabe&gt;'. |  Die Anweisung enthält einen unbekannten Operator. Beispielsweise wäre &quot;Volume!&quot; ungültig und würde &quot; Fehler: Unbekannter Operator '!'&quot; zurückgeben. |
| Fehler: Unbekannter Parameter '&lt;Eingabe&gt;'. |  Die Anweisung enthält einen unbekannten Parameter. Beispielsweise wäre „Volume=abc“ ungültig und würde „Fehler: Unbekannter Parameter 'abc'“ zurückgeben. |
| Fehler: Befehl nicht verfügbar, wenn aus '&lt;Eingabe&gt;'. |  Wenn Surface Hub ausgeschaltet ist, geben andere Befehle als „Ein/Aus“ diesen Fehler zurück. Beispielsweise wäre „Volume+“ ungültig und würde „Fehler: Befehl nicht verfügbar, wenn aus 'Volume'“ zurückgeben. |


 

##  <a name="related-content"></a>Verwandte Themen


[Verwalten von Microsoft Surface Hub](manage-surface-hub.md)

[Microsoft Surface Hub-Administratorhandbuch](surface-hub-administrators-guide.md)

 

 





