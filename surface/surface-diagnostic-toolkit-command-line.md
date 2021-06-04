---
title: Ausführen von Surface-Diagnosetoolkit für Unternehmen mithilfe von Befehlen
description: So führen Sie das Surface Diagnostic Toolkit in einer Befehlskonsole aus
ms.prod: w10
ms.mktglfcycl: manage
ms.sitesec: library
author: coveminer
ms.author: greglin
ms.topic: article
ms.reviewer: hachidan
manager: laurawi
ms.localizationpriority: medium
ms.audience: itpro
ms.openlocfilehash: f3856499bd769b96e22c0a47323c984eb38d8a18
ms.sourcegitcommit: 7e028c1e66fb393dc0e8917dac257ce95e5e9ce7
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/12/2021
ms.locfileid: "11327329"
---
# Ausführen von Surface-Diagnosetoolkit für Unternehmen mithilfe von Befehlen

Zum Ausführen des Surface Diagnostic Toolkit (SDT) an einer Eingabeaufforderung muss die SDT-App-Konsole heruntergeladen werden. Nach der Installation können Sie SDT an einer Eingabeaufforderung über die Windows-Befehlskonsole (cmd.exe) oder mithilfe von Windows PowerShell ausführen, einschließlich PowerShell Integrated Scripting Environment (ISE), die Unterstützung für die automatische Kompletierung von Befehlen, Kopieren/Einfügen und andere Features bietet.  Eine Liste der unterstützten Surface-Geräte in SDT finden Sie unter [Bereitstellen des Surface Diagnostic Toolkit for Business](surface-diagnostic-toolkit-business.md).

>[!NOTE]
>Um SDT mithilfe von Befehlen auszuführen, müssen Sie beim Administratorkonto oder bei einem Konto angemeldet sein, das Mitglied der Administratorgruppe auf Ihrem Surface Gerät ist.

##  <a name="running-sdt-app-console"></a>Ausführen der SDT-App-Konsole

Laden Sie die SDT-App-Konsole von der Downloadseite der [Surface Tools für IT herunter, und installieren Sie sie.](https://www.microsoft.com/download/details.aspx?id=46703) Sie können die Windows-Eingabeaufforderung (cmd.exe) oder Windows PowerShell verwenden: 

- Erfassen Sie alle Protokolldateien.
- Führen Sie die Integritätsdiagnose mit Best Practice Analyzer aus.
- Überprüfen Sie das Update auf fehlende Firmware- oder Treiberupdates.

>[!NOTE]
>In dieser Version unterstützt die SDT-App-Konsole nur einzelne Befehle. Für die Ausführung mehrerer Befehlszeilenoptionen muss die Konsolen-EXE für jeden Befehl separat ausgeführt werden. 

Standardmäßig werden Ausgabedateien am gleichen Speicherort wie die Konsolen-App gespeichert. Eine vollständige Liste der Befehle finden Sie in der folgenden Tabelle.

Befehl | Anmerkungen
--- | ---
-DataCollector "Ausgabedatei" | Sammelt Systemdetails in einer ZIP-Datei. "Ausgabedatei" ist der Dateipfad zum Erstellen einer Zip-Datei mit Systemdetails.<br><br>**Beispiel**:<br>`Microsoft.Surface.Diagnostics.App.Console.exe -DataCollector SDT_DataCollection.zip`
-bpa "Ausgabedatei" | Überprüft verschiedene Einstellungen und Integritätsindikatoren auf dem Gerät. "Ausgabedatei" ist der Dateipfad zum Erstellen des HTML-Berichts.<br><br>**Beispiel**:<br>`Microsoft.Surface.Diagnostics.App.Console.exe -bpa BPA.html`
-windowsupdate | Überprüft Windows Update-Onlineserver auf fehlende Firmware- und/oder Treiberupdates.<br><br>**Beispiel**:<br>Microsoft.Surface.Diagnostics.App.Console.exe -windowsupdate
-warranty "output file" | Überprüft Garantieinformationen auf dem Gerät (gültig oder ungültig). Die optionale "Ausgabedatei" ist der Dateipfad zum Erstellen der XML-Datei. <br><br>**Beispiel**: <br>Microsoft.Surface.Diagnostics.App.Console.exe –warranty "warranty.xml"


>[!NOTE]
>Um die SDT-App-Konsole remote auf Zielgeräten ausführen zu können, können Sie ein Konfigurationsverwaltungstool wie Microsoft Endpoint Configuration Manager verwenden. Alternativ können Sie eine ZIP-Datei mit der Konsolen-App und den entsprechenden Konsolenbefehlen erstellen und entsprechend den Softwareverteilungsprozessen Ihrer Organisation bereitstellen. 

##  <a name="running-best-practice-analyzer"></a>Ausführen von Best Practice Analyzer 

Sie können BPA-Tests für wichtige Komponenten wie BitLocker, secure Boot und Trusted Platform Module (TPM) ausführen und die Ergebnisse dann in eine freigabefähige Datei ausgibt. Das Tool generiert eine Reihe von Tabellen mit farblich codierten Überschriften und Bedingungsbeschreibungen sowie Anleitungen zur Lösung des Problems. 

- Grün gibt an, dass die Komponente in einem optimalen Zustand (optimal) ausgeführt wird.
- Orange gibt an, dass die Komponente nicht in einem optimalen Zustand ausgeführt wird (nicht optimal).
- Rot gibt an, dass sich die Komponente in einem anormalen Zustand befindet. 

###  <a name="sample-bpa-results-output"></a>Beispielausgabe für BPA-Ergebnisse

<table>
<tr><th colspan="2"><font color="00ff00">BitLocker</font></th></tr>
<tr><td><strong>Beschreibung:</strong></td><td>Überprüft, ob BitLocker auf dem Systemlaufwerk aktiviert ist.</td></tr>
<tr><td><strong>Wert:</strong></td><td>Schutz ein</td></tr>
<tr><td><strong>Bedingung:</strong></td><td><font color="00ff00">Optimal</font></td></tr>
<tr><td><strong>Anleitung:</strong></td><td>Es wird dringend empfohlen, BitLocker zum Schutz Ihrer Daten zu aktivieren.</td></tr>
</table>

<table>
<tr><th colspan="2"><font color="00ff00">Sicherer Start</font></th></tr>
<tr><td><strong>Beschreibung:</strong></td><td>Überprüft, ob der sichere Start aktiviert ist.</td></tr>
<tr><td><strong>Wert:</strong></td><td>Wahr</td></tr>
<tr><td><strong>Bedingung:</strong></td><td><font color="00ff00">Optimal</font></td></tr>
<tr><td><strong>Anleitung:</strong></td><td>Es wird dringend empfohlen, den sicheren Start zu aktivieren, um Ihren PC zu schützen.</td></tr>
</table>

<table>
<tr><th colspan="2"><font color="00ff00">Trusted Platform Module</font></th></tr>
<tr><td><strong>Beschreibung:</strong></td><td>Stellt sicher, dass das TPM funktionsfähig ist.</td></tr>
<tr><td><strong>Wert:</strong></td><td>Wahr</td></tr>
<tr><td><strong>Bedingung:</strong></td><td><font color="00ff00">Optimal</font></td></tr>
<tr><td><strong>Anleitung:</strong></td><td>Ohne ein funktionsfähiges TPM funktionieren sicherheitsbasierte Funktionen wie BitLocker möglicherweise nicht ordnungsgemäß.</td></tr>
</table>

<table>
<tr><th colspan="2"><font color="00ff00">Verbundener Standbymodus</font></th></tr>
<tr><td><strong>Beschreibung:</strong></td><td>Überprüft, ob der verbundene Standbymodus aktiviert ist.</td></tr>
<tr><td><strong>Wert:</strong></td><td>Wahr</td></tr>
<tr><td><strong>Bedingung:</strong></td><td><font color="00ff00">Optimal</font></td></tr>
<tr><td><strong>Anleitung:</strong></td><td>Der verbundene Standbymodus ermöglicht einem Surface-Gerät, Updates und Benachrichtigungen zu empfangen, ohne verwendet zu werden. Für eine optimale Benutzererfahrung sollte der verbundene Standbymodus aktiviert sein.</td></tr>
</table>

<table>
<tr><th colspan="2"><font color="00ff00">Bluetooth</font></th></tr>
<tr><td><strong>Beschreibung:</strong></td><td>Überprüft, Bluetooth aktiviert ist.</td></tr>
<tr><td><strong>Wert:</strong></td><td>Aktiviert</td></tr>
<tr><td><strong>Bedingung:</strong></td><td><font color="00ff00">Optimal</font></td></tr>
<tr><td><strong>Anleitung:</strong></td><td></td></tr>
</table>

<table>
<tr><th colspan="2"><font color="00ff00">Debugmodus</font></th></tr>
<tr><td><strong>Beschreibung:</strong></td><td>Überprüft, ob sich das Betriebssystem im Debugmodus befindet.</td></tr>
<tr><td><strong>Wert:</strong></td><td>Normal</td></tr>
<tr><td><strong>Bedingung:</strong></td><td><font color="00ff00">Optimal</font></td></tr>
<tr><td><strong>Anleitung:</strong></td><td>Die Debugstartoption aktiviert oder deaktiviert das Kerneldebuggern des Windows-Betriebssystems. Wenn Sie diese Option aktivieren, kann dies zu Systeminstabilität führen und die Wiedergabe geschützter Medien durch DRM (Digital Rights Managemend) verhindern.</td></tr>
</table>

<table>
<tr><th colspan="2"><font color="00ff00">Testen der Signierung</font></th></tr>
<tr><td><strong>Beschreibung:</strong></td><td>Überprüft, ob die Testsignierung aktiviert ist.</td></tr>
<tr><td><strong>Wert:</strong></td><td>Normal</td></tr>
<tr><td><strong>Bedingung:</strong></td><td><font color="00ff00">Optimal</font></td></tr>
<tr><td><strong>Anleitung:</strong></td><td>Die Testsignierung ist eine Windows-Starteinstellung, die nur zum Testen von Vorabversionstreibern verwendet werden sollte.</td></tr>
</table>

<table>
<tr><th colspan="2"><font color="00ff00">Aktiver Energieplan</font></th></tr>
<tr><td><strong>Beschreibung:</strong></td><td>Überprüft, ob der richtige Energieplan aktiv ist.</td></tr>
<tr><td><strong>Wert:</strong></td><td>Ausgeglichen</td></tr>
<tr><td><strong>Bedingung:</strong></td><td><font color="00ff00">Optimal</font></td></tr>
<tr><td><strong>Anleitung:</strong></td><td>Es wird dringend empfohlen, den Energieplan "Balanced" zu verwenden, um die Produktivität und Akkulaufzeit zu maximieren.</td></tr>
</table>

<table>
<tr><th colspan="2"><font color="ff9500">Windows Update</font></th></tr>
<tr><td><strong>Beschreibung:</strong></td><td>Überprüft, ob das Gerät mit den Windows-Updates auf dem neuesten Stand ist.</td></tr>
<tr><td><strong>Wert:</strong></td><td>Microsoft Silverlight (KB4023307), Definitionsupdate für Windows Defender Antivirus - KB2267602 (Definition 1.279.1433.0)</td></tr>
<tr><td><strong>Bedingung:</strong></td><td><font color="ff9500">Nicht optimal</font></td></tr>
<tr><td><strong>Anleitung:</strong></td><td>Wenn Sie auf die neuesten Fenster aktualisieren, stellen Sie sicher, dass Sie über die neueste Firmware und die neuesten Treiber auf dem neuesten Stand sind. Es wird empfohlen, Ihr Gerät immer auf dem neuesten Stand zu halten.</td></tr>
</table>

<table>
<tr><th colspan="2"><font color="00ff00">Freier Festplattenspeicher</font></th></tr>
<tr><td><strong>Beschreibung:</strong></td><td>Sucht nach wenig freiem Festplattenspeicherplatz.</td></tr>
<tr><td><strong>Wert:</strong></td><td>66%</td></tr>
<tr><td><strong>Bedingung:</strong></td><td><font color="00ff00">Optimal</font></td></tr>
<tr><td><strong>Anleitung:</strong></td><td>Um eine optimale Leistung zu erzielen, sollte die Festplatte mindestens 10 % der Kapazität als freier Speicherplatz haben.</td></tr>
</table>

<table>
<tr><th colspan="2"><font color="00ff00">Nicht funktionierende Geräte</font></th></tr>
<tr><td><strong>Beschreibung:</strong></td><td>Liste der nicht funktionierenden Geräte im Geräte-Manager.</td></tr>
<tr><td><strong>Wert:</strong></td><td></td></tr>
<tr><td><strong>Bedingung:</strong></td><td><font color="00ff00">Optimal</font></td></tr>
<tr><td><strong>Anleitung:</strong></td><td>Nicht funktionsfähige Geräte im Device Manager können zu unvorhersehbaren Problemen mit Surface-Geräten führen, z. B. keine Stromeinsparungen für die jeweilige Hardwarekomponente.</td></tr>
</table>

<table>
<tr><th colspan="2"><font color="00ff00">Externer Monitor</font></th></tr>
<tr><td><strong>Beschreibung:</strong></td><td>Sucht nach einem externen Monitor, bei dem Kompatibilitätsprobleme auftreten können.</td></tr>
<tr><td><strong>Wert:</strong></td><td></td></tr>
<tr><td><strong>Bedingung:</strong></td><td><font color="00ff00">Optimal</font></td></tr>
<tr><td><strong>Anleitung:</strong></td><td>Überprüfen Sie beim Originalgerätehersteller nach der Kompatibilität mit Ihrem Surface-Gerät.</td></tr>
</table>
