---
title: Surface-Diagnosetoolkit für Unternehmen bereitstellen
description: In diesem Thema wird die Verwendung des Surface Diagnostic Toolkit for Business erläutert.
ms.prod: w10
ms.mktglfcycl: manage
ms.localizationpriority: medium
ms.sitesec: library
author: coveminer
ms.author: greglin
ms.topic: article
ms.date: 01/15/2021
ms.reviewer: hachidan
manager: laurawi
audience: itpro
ms.openlocfilehash: 227463e484a6f3b933fc1118d9dec058f93074a8
ms.sourcegitcommit: 1053479c191fd10651d31a466fad1769fb0cd28b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/16/2021
ms.locfileid: "11271579"
---
# Surface-Diagnosetoolkit für Unternehmen bereitstellen

Das Microsoft Surface Diagnostic Toolkit for Business (SDT) ermöglicht es IT-Administratoren, Hardware-, Software- und Firmwareprobleme mit Surface-Geräten schnell zu untersuchen, zu beheben und zu beheben. Sie können eine Reihe von Diagnosetests und Softwarereparaturen ausführen, zusätzlich zum Abrufen von Einblicken in die Geräteintegdaten und Anleitungen zur Behebung von Problemen. 

SdT for Business ermöglicht Ihnen insbesondere:

- [Passen Sie das Paket an.](#preparing-the-sdt-package-for-distribution)
- [Führen Sie die App mithilfe von Befehlen aus.](surface-diagnostic-toolkit-command-line.md)
- [Führen Sie mehrere Hardwaretests aus, um Probleme zu beheben.](surface-diagnostic-toolkit-desktop-mode.md#multiple)
- [Generieren sie Protokolle für die Analyse von Problemen.](surface-diagnostic-toolkit-desktop-mode.md#logs)
- [Erhalten Sie einen detaillierten Bericht, in dem das Gerät mit der optimalen Konfiguration verglichen wird.](surface-diagnostic-toolkit-desktop-mode.md#detailed-report)


##  <a name="primary-scenarios-and-download-resources-"></a>Primäre Szenarien und Downloadressourcen 

Laden Sie zum Ausführen von SDT for Business die in der folgenden Tabelle aufgeführten Komponenten herunter.


Modus |  Primäre Szenarien | Herunterladen | Mehr erfahren
--- | --- | --- | ---
Desktopmodus |  Unterstützen Sie Benutzer bei der Ausführung von SDT auf ihren Surface-Geräten, um Probleme zu beheben.<br>Erstellen Sie ein benutzerdefiniertes Paket für die Bereitstellung auf einem oder mehreren Surface-Geräten, sodass Benutzer bestimmte Protokolle zum Sammeln und Analysieren auswählen können. | Verteilbares SDT-MSI-Paket:<br>Microsoft Surface Diagnostic Toolkit for Business Installer<br>[Surface-Tools für IT](https://www.microsoft.com/download/details.aspx?id=46703) | [Verwenden des Surface Diagnostic Toolkits im Desktopmodus](surface-diagnostic-toolkit-desktop-mode.md)
Befehlszeile |  Direkte Problembehandlung für Surface-Geräte remote ohne Benutzerinteraktion mithilfe von Standardtools wie Configuration Manager. Sie enthält die folgenden Befehle:<br>`-DataCollector` sammelt alle Protokolldateien<br>`-bpa` Führt Integritätsdiagnosen mit Best Practice Analyzer aus.<br>`-windowsupdate` Überprüft Windows Update auf fehlende Firmware- oder Treiberupdates.<br>`-warranty` überprüft Garantieinformationen. <br><br>| SDT-Konsolen-App:<br>Microsoft Surface Diagnostics App Console<br>[Surface-Tools für IT](https://www.microsoft.com/download/details.aspx?id=46703) | [Ausführen des Surface Diagnostic Toolkit mithilfe von Befehlen](surface-diagnostic-toolkit-command-line.md)

##  <a name="supported-devices"></a>Unterstützte Geräte 

SDT for Business wird auf Surface 3 und höher unterstützt, einschließlich:

- Surface Book – alle Generationen
- Surface Go – alle Generationen
- Surface Laptop – alle Generationen
- Surface Pro 3 und höher
- Surface Pro X – alle Generationen
- Surface Studio – alle Generationen
- Surface 3 LTE
- Surface3


##  <a name="installing-surface-diagnostic-toolkit-for-business"></a>Installieren des Surface Diagnostic Toolkit for Business

So erstellen Sie ein SDT-Paket, das Sie an Benutzer in Ihrer Organisation verteilen können:

1. Melden Sie sich mit dem Administratorkonto bei Ihrem Surface-Gerät an.
2. Laden Sie das SDT Windows Installer Package (MSI) von der Downloadseite der [Surface Tools für IT](https://www.microsoft.com/download/details.aspx?id=46703) herunter, und kopieren Sie es an einen bevorzugten Speicherort auf Ihrem Surface-Gerät, z. B. Desktop.
3. Der SDT-Setup-Assistent wird angezeigt, wie in Abbildung 1 dargestellt. Klicken Sie auf **Weiter**. 

    >[!NOTE]
    >Wenn der Setup-Assistent nicht angezeigt wird, stellen Sie sicher, dass Sie beim Administratorkonto auf Ihrem Computer angemeldet sind. 

    ![Willkommen beim Surface Diagnostic Toolkit-Setup-Assistenten](images/sdt-1.png)

    *Abbildung1. Surface Diagnostic Toolkit-Setup-Assistent*

4. Wenn der SDT-Setup-Assistent angezeigt wird, klicken Sie auf **"Weiter",** und akzeptieren Sie den Endbenutzer-Lizenzvertrag.

5. Ändern Sie auf dem Bildschirm "Installationsoptionen" bei Bedarf den Standardinstallationsspeicherort. 
6. Wählen Sie unter "Setuptyp" die Option **"Erweitert" aus.** 

    >[!NOTE]
    >Mit der Standardoption können Benutzer das Diagnosetool direkt auf ihrem Surface-Gerät ausführen, sofern sie über ein Administratorkonto bei ihrem Gerät angemeldet sind. 
    
     ![Installationsoptionen: Erweitert](images/sdt-install.png)

7. Klicken Sie **auf "Weiter",** und klicken Sie dann auf **"Installieren".** 

##  <a name="installing-using-the-command-line"></a>Installieren über die Befehlszeile
Bei Bedarf können Sie SDT an einer Eingabeaufforderung installieren und ein benutzerdefiniertes Flag festlegen, um das Tool im Administratormodus zu installieren. SDT enthält die folgenden Installationsoptionsflags:

- `SENDTELEMETRY` sendet Telemetriedaten an Microsoft. Das Flag akzeptiert `0` "Deaktiviert" oder `1` "Aktiviert". Der Standardwert ist das `1` Senden von Telemetrie.
- `ADMINMODE` konfiguriert das Tool für die Installation im Administratormodus. Das Flag akzeptiert `0` den Clientmodus oder `1` den IT-Administratormodus. Der Standardwert lautet `0`.

###  <a name="to-install-sdt-from-the-command-line:"></a>So installieren Sie SDT über die Befehlszeile:

1. Öffnen Sie eine Eingabeaufforderung, und geben Sie folgenden Befehl ein:

    ```
    msiexec.exe /i <the path of installer> ADMINMODE=1. 
    ```
    **Beispiel:**

    ```
    C:\Users\Administrator> msiexec.exe/I"C:\Users\Administrator\Desktop\Microsoft_Surface_Diagnostic_Toolkit_for_Business_Installer.msi" ADMINMODE=1
    ```

##  <a name="locating-sdt-on-your-surface-device"></a>Suchen von SDT auf Ihrem Surface-Gerät

Sowohl SDT als auch die SDT-App-Konsole werden unter `C:\Program Files\Microsoft\Surface\Microsoft Surface Diagnostic Toolkit for Business` installiert.

Neben der EXE-Datei installiert SDT eine JSON-Datei und eine admin.dll (modules\admin.dll), wie in Abbildung 2 dargestellt.

![Liste der installierten SDT-Dateien im Datei-Explorer](images/sdt-2.png)

*Abbildung2. Von SDT installierte Dateien*

## Vorbereiten des SDT-Pakets für die Verteilung

Durch das Erstellen eines benutzerdefinierten Pakets können Sie das Tool auf bestimmte bekannte Probleme konzentrieren.

1. Klicken **Sie auf > Ausführen,** geben Sie Surface **ein,** und klicken Sie dann auf **Surface Diagnostic Toolkit for Business**. 
2. Klicken Sie beim Öffnen des Tools auf "Benutzerdefiniertes **Paket erstellen",** wie in Abbildung 3 dargestellt.

    ![Option "Benutzerdefiniertes Paket erstellen"](images/sdt-3.png)

    *Abbildung3. Erstellen eines benutzerdefinierten Pakets*

###  <a name="language-and-telemetry-settings"></a>Sprach- und Telemetrieeinstellungen

  Beim Erstellen eines Pakets können Sie Spracheinstellungen auswählen oder das Senden von Telemetrieinformationen an Microsoft deaktivieren. Standardmäßig sendet SDT Telemetrie an Microsoft, die verwendet wird, um die Anwendung in Übereinstimmung mit den Datenschutzbestimmungen von [Microsoft zu verbessern.](https://privacy.microsoft.com/privacystatement) Wenn Sie dies ablehnen möchten, müssen Sie das Kontrollkästchen beim Erstellen eines benutzerdefinierten Pakets wie unten dargestellt aktivieren. Oder aktivieren Sie das **Kontrollkästchen "Telemetrie** an Microsoft senden" auf der Seite **"Installationsoptionen"** während des SDT-Setups. 

>[!NOTE]
>Diese Einstellung wirkt sich nicht auf die minimale Telemetrie aus, die automatisch auf den Servern von Microsoft gespeichert wird, wenn Tests und Reparaturen ausgeführt werden, die eine Internetverbindung erfordern, z. B. Windows Update und Softwarereparatur, oder geben Feedback über die Schaltflächen "Smile" oder "Stirnrunzeln" in der Symbolleiste der App. 


![Auswählen von Sprach- und Telemetrieeinstellungen](images/sdt-4.png)

*Abbildung 4. Auswählen von Sprach- und Telemetrieeinstellungen*


###  <a name="windows-update-page"></a>Windows Update-Seite

Wählen Sie die für Ihre Organisation geeignete Option aus. Die meisten Organisationen mit mehreren Benutzern wählen in der Regel updates über Windows Server Update Services (WSUS) aus, wie in Abbildung 5 dargestellt. Wenn Sie lokale Windows Update-Pakete oder WSUS verwenden, geben Sie den Pfad entsprechend ein. 

![Option "Windows Update auswählen"](images/sdt-5.png)

*Abbildung5. Windows Update-Option*

###  <a name="software-repair-page"></a>Seite "Softwarereparatur"

Auf diese Weise können Sie die Option zum Ausführen von Softwarereparaturupdates auswählen oder entfernen. 

![Softwarereparaturoption auswählen](images/sdt-6.png)

*Abbildung6. Softwarereparaturoption*

###  <a name="collecting-logs-and-saving-package-page"></a>Sammeln von Protokollen und Speichern der Paketseite

Sie können eine Vielzahl von Protokollen für Anwendungen, Treiber, Hardware und das Betriebssystem ausführen. Klicken Sie auf den entsprechenden Bereich, und wählen Sie im Menü der verfügbaren Protokolle aus. Anschließend können Sie das Paket an einem Softwareverteilungspunkt oder einem gleichwertigen Speicherort speichern, auf den Benutzer zugreifen können. 

![Auswählen von Protokolloptionen](images/sdt-7.png)

*Abbildung7. Protokollierungsoption und Paket speichern*

##  <a name="next-steps"></a>Nächste Schritte

- [Surface-Diagnosetoolkit für Unternehmen im Desktopmodus verwenden](surface-diagnostic-toolkit-desktop-mode.md)
- [Verwenden des Surface Diagnostic Toolkit for Business mithilfe von Befehlen](surface-diagnostic-toolkit-command-line.md)

##  <a name="changes-and-updates"></a>Änderungen und Updates

###  <a name="version-2.131.139.0"></a>Version 2.131.139.0

Diese Version des Surface Diagnostic Toolkit for Business bietet Unterstützung für Folgendes:

- Unterstützung für Surface Pro 7+
- Nahtlose Supporterfahrung auf Surface Pro X
- Sicherheitsverbesserungen
- Verbesserungen der inklusiven Benutzerfreundlichkeit

###  <a name="version-2.124.139.0"></a>Version 2.124.139.0

Diese Version des Surface Diagnostic Toolkit for Business bietet Unterstützung für Folgendes:

- Nahtlose integrierte Unterstützung
- Speichern aller Testergebnisse
- Überprüfen, ob das Bild benutzerdefinierte erstellt wurde
- Schließen Sie Warnungen vom Gerätemanager ein
- Dock Firmware version
- Kennzeichnen von Laufwerken als potenzielle Fehler beim Speichertest
- Entfernen eines Informationsspeicherlinks 

###  <a name="version-2.121.139"></a>Version 2.121.139
*Veröffentlichungsdatum: 31. Juli 2020*<br>
Diese Version des Surface Diagnostic Toolkit for Business bietet Unterstützung für Folgendes:

- Nahtlose Supporterfahrung
- Fehlerbehebungen

###  <a name="version-2.94.139.0"></a>Version 2.94.139.0
*Veröffentlichungsdatum: 11. Mai 2020*<br>
Diese Version des Surface Diagnostic Toolkit for Business bietet Unterstützung für Folgendes:

- Möglichkeit, Windows Update zu überspringen, um eine Hardwareprüfung durchzuführen.
- Möglichkeit zum Empfangen von Benachrichtigungen über das neueste Versionsupdate
- Surface Go 2
- Surface Book 3
- Statusanzeige anzeigen


###  <a name="version-2.43.139.0"></a>Version 2.43.139.0
*Veröffentlichungsdatum: 21. Oktober 2019*<br>
Diese Version des Surface Diagnostic Toolkit for Business bietet Unterstützung für Folgendes:

- Surface Pro 7
- Surface Laptop 3

###  <a name="version-2.42.139.0"></a>Version 2.42.139.0
*Veröffentlichungsdatum: 24. September 2019*<br>
Diese Version des Surface Diagnostic Toolkit for Business bietet Unterstützung für Folgendes: 
- Möglichkeit zum Herunterladen von Hardwareberichten.
- Möglichkeit, den Microsoft Support direkt über das Tool zu kontaktieren. <br>

###  <a name="version-2.41.139.0"></a>Version 2.41.139.0
*Veröffentlichungsdatum: 24. Juni 2019*<br>
Diese Version des Surface Diagnostic Toolkit for Business bietet Unterstützung für Folgendes: 
- Informationen zur Treiberversion, die in Protokollen und Berichten enthalten sind.
- Möglichkeit, Feedback zur App zu geben.<br>


###  <a name="version-2.36.139.0"></a>Version 2.36.139.0
*Veröffentlichungsdatum: 26. April 2019*<br>
Diese Version des Surface Diagnostic Toolkit for Business bietet Unterstützung für Folgendes: 
- Erweiterte Setupoption zum Entsperren von Administratorfunktionen über die Installer-Benutzeroberfläche, ohne dass eine Befehlszeilenkonfiguration erforderlich ist.
- Verbesserte Barrierefreiheit.
- Einstellungen für die Oberflächenhelligkeitssteuerung, die in Protokollen enthalten sind.
- Link zur Unterstützung der externen Monitorkompatibilität im Berichtsgenerator.
