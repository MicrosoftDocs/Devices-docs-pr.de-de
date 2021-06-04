---
title: Sitzung beenden – Beenden einer Surface Hub-Besprechung
description: Tippen Sie zum Beenden einer Surface Hub-Besprechung auf „Sitzung beenden“. Surface Hub bereinigt den Status der Anwendung und des Betriebssystems und die Benutzeroberfläche, sodass Surface Hub für die nächste Besprechung bereit ist.
keywords: Fertig, Surface Hub-Besprechung beenden, Surface Hub-Besprechung bereinigen
ms.prod: surface-hub
ms.sitesec: library
author: dansimp
ms.author: dansimp
ms.topic: article
ms.date: 07/27/2017
ms.reviewer: ''
manager: laurawi
ms.localizationpriority: medium
ms.openlocfilehash: b18bc4b15b8a3925aeecdd9999b09b61011d1db5
ms.sourcegitcommit: 109d1d7608ac4667564fa5369e8722e569b8ea36
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/27/2020
ms.locfileid: "10833694"
---
# Beenden einer Surface Hub-Besprechung mit „Sitzung beenden“.
Surface Hub ist ein Gerät für die Zusammenarbeit, das in Besprechungsräumen von verschiedenen Gruppen von Personen verwendet werden kann. Am Ende einer Besprechung können Benutzer auf **Sitzung beenden** tippen, um vertrauliche Daten zu entfernen und das Gerät für die nächste Besprechung vorzubereiten. Der Surface Hub bereinigt bzw. setzt folgende Komponenten zurück:
- Anwendungen
- Betriebssystem
- Benutzeroberfläche

In diesem Thema wird beschrieben, welche Elemente der einzelnen Komponenten mittels **Sitzung beenden** zurückgesetzt werden.

##  <a name="applications"></a>Anwendungen
Wenn Sie Apps auf Surface Hub starten, werden sie im Arbeitsspeicher gespeichert. Die Daten werden auf der Anwendungsebene gespeichert. Während einer Sitzung (oder Besprechung) sind die Daten für alle Benutzer verfügbar, bis sie entfernt oder überschrieben werden. Wenn **Sitzung beenden** ausgewählt ist, wird der Surface Hub-Anwendungszustand bereinigt, indem Anwendungen geschlossen, Browserverlauf gelöscht, Anwendungen zurückgesetzt und Skype-Protokolle entfernt werden.

###  <a name="close-applications"></a>Schließen von Anwendungen
Surface Hub schließt alle sichtbaren Fenster, einschließlich der Win32-Anwendung und der Universellen Windows-Plattform (UWP). Wenn die Anwendung geschlossen ist, wird die Multitasking-Ansicht verwendet, um die angezeigten Fenster abzufragen. Win32-Fenster, die innerhalb eines bestimmten Zeitrahmens nicht schließen, werden mit **TerminateProcess** geschlossen. 
   
###  <a name="delete-browser-history"></a>Löschen des Browserverlaufs
Surface Hub verwendet die Funktion zum Löschen des Bildverlaufs (Delete Browser History, DBH) in Microsoft Edge, um den Edge-Verlauf und die zwischengespeicherten Daten zu löschen. Das ist vergleichbar damit, wenn ein Benutzer den Browserverlauf manuell löscht. Mit **Sitzung beenden** wird jedoch sichergestellt, dass auch die Anwendungszustände gelöscht und die Daten vor Beginn der nächsten Sitzung oder Besprechung entfernt werden. 
 
###  <a name="reset-applications"></a>Zurücksetzen von Anwendungen
**Sitzung beenden** setzt den Status jeder Anwendung zurück, die auf Surface Hub installiert ist. Durch das Zurücksetzen einer Anwendung werden alle Hintergrundaufgaben, Anwendungsdaten, Benachrichtigungen und Benutzerzustimmungs-Dialogfelder gelöscht. Anwendungen werden für die nächsten Benutzer in den Zustand der ersten Ausführung zurückgesetzt, die Surface Hub verwenden.  
 
###  <a name="remove-skype-logs"></a>Entfernen von Skype-Protokollen
Skype speichert keine personenbezogenen Informationen auf Surface Hub. Informationen werden im Skype-Dienst gespeichert, um vorhandene Skype for Business-Richtlinien zu erfüllen. Lokale Skype-Protokollinformationen sind die einzigen Daten, die entfernt werden, wenn **Sitzung beenden** ausgewählt wird. Dazu zählen Protokolle von Unified Communications Client Platform (UCCP) und Medien-Protokolle.   

##  <a name="operating-system"></a>Betriebssystem
Im Betriebssystem wird eine Vielzahl von Informationen über den Zustand der Sitzungen gehostet, die nach jeder Surface Hub-Besprechung gelöscht werden müssen. 

###  <a name="file-system"></a>Dateisystem
Die Teilnehmer einer Besprechung haben Zugriff auf eine begrenzte Zahl an Verzeichnissen auf dem Surface Hub. Wenn **Sitzung beenden** ausgewählt wird, löscht Surface Hub diese Verzeichnisse:<br>
- Musik
- Videos
- Dokumente
- Bilder
- Downloads

Surface Hub löscht auch diese Verzeichnisse, da viele Anwendungen oft in diese schreiben:
- Desktop
- Favoriten
- Zuletzt verwendet
- Öffentliche Dokumente
- Öffentliche Musik
- Öffentliche Videos
- Öffentliche Downloads

###  <a name="credentials"></a>Anmeldeinformationen
Benutzeranmeldeinformationen, die in **TokenBroker**, **PasswordVault** oder in der **Anmeldeinformationsverwaltung** gespeichert sind, werden gelöscht, wenn Sie auf **Sitzung beenden** tippen.

##  <a name="user-interface"></a>Benutzeroberfläche
Die Einstellungen der Benutzeroberfläche (UI) werden auf die jeweiligen Standardwerte zurückgesetzt, wenn **Sitzung beenden** ausgewählt wird. 

###  <a name="ui-items"></a>Benutzeroberflächenelemente
- Reset Quick Actions to default state
- Clear Toast notifications
- Reset volume levels
- Reset sidebar width
- Reset tablet mode layout
- Abmelden von Benutzern aus Office365-Besprechungen und -Dateien

###  <a name="accessibility"></a>Barrierefreiheit
Wenn **Sitzung beenden** ausgewählt wird, werden Barrierefreiheitsfeatures und Apps auf die Standardeinstellungen zurückgesetzt.
- Anschlagverzögerung
- Hoher Kontrast
- Einrastfunktion
- Umschalttasten
- Tastaturmaus
- Bildschirmlupe
- Sprachausgabe

###  <a name="clipboard"></a>Zwischenablage
Die Zwischenablage wird gelöscht, um Daten zu entfernen, die während der Sitzung in die Zwischenablage kopiert wurden. 

##  <a name="faq"></a>Häufig gestellte Fragen
**Was geschieht, wenn ich am Ende einer Besprechung vergesse, auf „Sitzung beenden“ zu tippen, und später eine andere Person den Surface Hub verwendet?**<br>
Surface Hub bereinigt Besprechungsinhalte nur, wenn Benutzer auf **Sitzung beenden** tippen. Wenn Sie die Besprechung verlassen, ohne auf **Sitzung beenden** zu tippen, zeigt das Gerät nach einiger Zeit erneut die Willkommensseite an. Über die Willkommensseite können Benutzer die vorherige Sitzung fortsetzen oder eine neue Sitzung starten. Sie können auch die Funktion zum Fortsetzen einer Sitzung deaktivieren, wenn **Sitzung beenden** nicht gedrückt wird.

**Können Dokumente wiederhergestellt werden?**<br> Das Entfernen von Dateien von der Festplatte bei Auswahl von **Sitzung beenden** führt zum gleichen Ergebnis wie das Löschen von Dateien von einer Festplatte. Die Daten können möglicherweise mithilfe einer Drittanbietersoftware von der Festplatte wiederhergestellt werden. Die Dateiwiederherstellung wird von Surface Hub jedoch nicht unterstützt. Um den Verlust von Daten zu verhindern, sollten Sie benötigte Daten stets speichern, bevor Sie eine Besprechung verlassen.

**Entsprechen die Bereinigungsvorgänge über „Sitzung beenden“ dem Lösch- und Bereinigungsstandard DoD 5220.22-M des US-Verteidigungsministeriums?**<br>
Nein. Derzeit erfüllen die mit **Sitzung beenden** ausgeführten Bereinigungsvorgängen nicht diesen Standard.  
  
