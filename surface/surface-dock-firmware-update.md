---
title: Microsoft Surface Dock 1-Firmwareupdate
description: In diesem Artikel wird erläutert, wie Microsoft Surface Dock Firmware Update zum Installieren und Verwalten der Firmware auf dem ursprünglichen Surface Dock 1 verwendet wird. Wenn sie auf Ihrem Surface Gerät installiert ist, werden Surface Dock 1-Geräte aktualisiert, die an Ihr Surface Gerät angeschlossen sind.
ms.localizationpriority: medium
ms.prod: w10
ms.mktglfcycl: manage
ms.sitesec: library
author: greg-lindsay
ms.author: greglin
ms.topic: article
ms.reviewer: scottmca
manager: laurawi
ms.audience: itpro
ms.date: 2/08/2021
ms.openlocfilehash: a0acaaf0676c3f4403a2b233297781579ca1f4ae
ms.sourcegitcommit: 7029e80d9ca1a3de5c336cf662e566ed4b6b3e7a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/09/2021
ms.locfileid: "11319209"
---
# Microsoft Surface Dock Firmware Update

> [!IMPORTANT]
> Dieser Artikel enthält technische Anweisungen für IT-Administratoren. Wenn Sie ein Privatbenutzer sind, lesen Sie die Informationen zum Aktualisieren der [Surface Dock Firmware](https://support.microsoft.com/help/4023478/surface-update-your-surface-dock)auf der Microsoft   Support-Website. Die Anweisungen auf der Supportwebsite sind mit den allgemeinen Installationsschritten unten identisch, aber dieser Artikel enthält zusätzliche Informationen zum Überwachen, Überprüfen und Bereitstellen des Updates auf mehreren Geräten in einem Netzwerk.

In diesem Artikel wird erläutert, wie Microsoft Surface Dock Firmware Update zum Installieren und Verwalten der Firmware auf dem ursprünglichen Surface Dock 1 verwendet wird. Bei der Installation auf dem Surface-Gerät werden Surface Dock 1-Geräte aktualisiert, die an das Surface Gerät angeschlossen sind.

> [!NOTE]
> Dieser Artikel gilt nicht für Surface Dock 2, das Updates automatisch über Windows Update oder mithilfe von Microsoft Endpoint Configuration Manager oder anderen MSI-Bereitstellungstools empfängt. Weitere Informationen finden Sie unter ["Neues" in Surface Dock.](surface-dock-whats-new.md)

Dieses Tool ersetzt das frühere Microsoft Surface Dock Updater-Tool, das zuvor als Teil der Surface Tools für die IT zum Download verfügbar war. Das frühere Tool hieß Surface_Dock_Updater_vx.xx.xxx.x.msi (wobei x die Versionsnummer angibt) und ist nicht mehr zum Download verfügbar und sollte nicht verwendet werden.

## Installieren des Surface Dock Firmware Update

In diesem Abschnitt wird beschrieben, wie Sie das Firmwareupdate manuell installieren.

> [!NOTE]
> Microsoft veröffentlicht regelmäßig neue Versionen des Surface Dock Firmware Update. Die MSI-Datei wird nicht automatisch aktualisiert. Wenn Sie die MSI auf den Geräten von Surface bereitgestellt haben und eine neue Version der Firmware veröffentlicht wird, müssen Sie die neue Version bereitstellen.

1. Laden Sie das Dock [Firmware Update Microsoft Surface herunter, und installieren Sie es.](https://www.microsoft.com/download/details.aspx?id=46703)
    - Das Update erfordert ein Surface-Gerät mit Windows 10, Version 1803 oder höher.
    - Beim Installieren der MSI-Datei werden Sie möglicherweise aufgefordert, Surface neu zu starten. Ein Neustart ist jedoch nicht erforderlich, um das Update durchzuführen.

2. Trennen Sie das #A0 von Surface Dock, warten Sie ca. 5 Sekunden, und stellen Sie dann erneut eine Verbindung her. Das Surface Dock Firmware Update aktualisiert das Dock automatisch im Hintergrund. Der Vorgang kann einige Minuten dauern und wird auch dann fortgesetzt, wenn er unterbrochen wird. 

##  <a name="monitor-the-surface-dock-firmware-update"></a>Überwachen des Surface Dock-Firmwareupdates

Dieser Abschnitt ist optional und bietet eine Übersicht über die Überwachung der Installation des Firmwareupdates. 

So überwachen Sie das Update:

1. Öffnen Sie die Ereignisanzeige, navigieren Sie zu **"Windows-Protokolle >-Anwendung",** und klicken Sie dann im rechten Bereich unter "Aktionen" auf "Aktuelles Protokoll **filtern",** geben Sie **"SurfaceDockFwUpdate"** neben **"Ereignisquellen"** ein, und klicken Sie dann auf **"OK".** ****

2. Geben Sie an einer Eingabeaufforderung mit erhöhten Rechten den folgenden Befehl ein:

    ```console
    Reg query "HKLM\SOFTWARE\Microsoft\Windows NT\CurrentVersion\WUDF\Services\SurfaceDockFwUpdate\Parameters"
    ```
3. Installieren Sie das Update wie im [nächsten Abschnitt dieses](#install-the-surface-dock-firmware-update) Artikels beschrieben.

4. Ereignis 2007 mit dem folgenden Text weist auf ein erfolgreiches Update hin: **Firmwareupdate abgeschlossen. hr=0 DriverTelementry EventCode = 2007**. 

   Wenn das Update nicht erfolgreich ist, wird die Ereignis-ID 2007 als Fehlerereignis und nicht als **Information angezeigt.** **** Darüber hinaus ist die in der Registrierung von Windows gemeldete Version nicht aktuell.
   
5. Nach Abschluss des Updates werden aktualisierte DWORD-Werte in der Windows-Registrierung angezeigt, die der aktuellen Version des Tools entspricht. Weitere Informationen finden Sie im Abschnitt ["Versionsreferenz"](#versions-reference) in diesem Artikel. Zum Beispiel:

    - Component10CurrentFwVersion 0x04ac3970 (78395760)
    - Component20CurrentFwVersion 0x04915a70 (76634736)

>[!TIP]
>Wenn im Ereignistext "Die Beschreibung für die Ereignis-ID xxxx aus der SurfaceDockFwUpdate-Quelle wurde nicht gefunden" angezeigt wird, wird dies erwartet und kann ignoriert werden.

Weitere Informationen finden Sie in den folgenden Abschnitten in diesem Artikel: 
  - [So überprüfen Sie den Abschluss des Firmwareupdates](#how-to-verify-completion-of-the-firmware-update)
  - [Ereignisprotokollierung](#event-logging)
  - [Hinweise zur Problembehandlung](#troubleshooting-tips)
  - [Versionsreferenz](#versions-reference)

##  <a name="network-deployment"></a>Netzwerkbereitstellung

Sie können Windows Installer-Befehle (Msiexec.exe) verwenden, um Surface Dock Firmware Update auf mehreren Geräten in Ihrem Netzwerk bereitstellen. Wenn Sie Microsoft Endpoint Configuration Manager oder ein anderes Bereitstellungstool verwenden, geben Sie die folgende Syntax ein, um sicherzustellen, dass die Installation automatisch ist:

- **Msiexec.exe /i \<path to msi file\> /quiet /norestart** 

Zum Beispiel:

```console
msiexec /i "\\share\folder\Surface_Dock_FwUpdate_1.42.139_Win10_17134_19.084.31680_0.msi" /quiet /norestart
```

> [!NOTE]
> Eine Protokolldatei wird standardmäßig nicht erstellt. Zum Erstellen einer Protokolldatei müssen Sie "/l*v [path]" anfügen. Beispiel: Msiexec.exe /i \<path to msi file\> /l*v %windir%\logs\ SurfaceDockFWI.log"

Weitere Informationen finden Sie in der [Dokumentation zu Befehlszeilenoptionen.](https://docs.microsoft.com/windows/win32/msi/command-line-options)

> [!IMPORTANT]
> Wenn Sie Surface Dock mit einer anderen Methode aktualisieren möchten, finden Sie weitere Informationen unter ["Aktualisieren](https://support.microsoft.com/help/4023478/surface-update-your-surface-dock) von Surface Dock".

##  <a name="intune-deployment"></a>Bereitstellung von Intune

Sie können Intune verwenden, um Surface Dock Firmware Update auf Ihre Geräte zu verteilen. Zuerst müssen Sie die MSI-Datei in das .intunewin-Format konvertieren, wie in der folgenden Dokumentation beschrieben: [Intune Eigenständig – Win32-App-Verwaltung.](https://docs.microsoft.com/intune/apps/apps-win32-app-management)

Verwenden Sie den folgenden Befehl:
  - **msiexec /i \<path to msi file\> /quiet /q**

## So überprüfen Sie den Abschluss des Firmwareupdates

Die Surface Dock Firmware besteht aus zwei Komponenten:

- **Komponente10:** Firmware der Microcontrollereinheit (McU)
- **Komponente20:** Firmware des Anzeigeports (DP).

Der erfolgreiche Abschluss des Surface Dock Firmware Update führt zu neuen Registrierungsschlüsselwerten für diese Firmwarekomponenten.

**So überprüfen Sie Updates:**

1. Öffnen Sie Regedit, und navigieren Sie zum folgenden Registrierungspfad:

    - **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows NT\CurrentVersion\WUDF\Services\SurfaceDockFwUpdate\Parameters**

2. Suchen Sie nach den Registrierungsschlüsseln **Component10CurrentFwVersion und Component20CurrentFwVersion,** die auf die Firmware verweisen, die sich derzeit auf dem Gerät befindet.

   ![Installationsvorgang für das Surface Dock Firmware Update](images/regeditDock.png)

3. Überprüfen Sie, ob die neuen Registrierungsschlüsselwerte mit den aktualisierten Registrierungsschlüsselwerten übereinstimmen, die in der Versionsreferenz am Ende dieses Dokuments aufgeführt sind. Wenn die Werte übereinstimmen, wurde die Firmware erfolgreich aktualisiert.

4. Wenn die Überprüfung nicht möglich ist, lesen Sie die Tipps zur Ereignisprotokollierung und Problembehandlung im nächsten Abschnitt.

## Ereignisprotokollierung

**Tabelle1. Protokolldateien für Surface Dock Firmware Update**

| Log                              | Pfad                               | Anmerkungen                                                                                                                                                                                                         |
| -------------------------------- | --------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Surface Dock Firmware Update log | Pfad muss angegeben werden (siehe Hinweis) | In früheren Versionen dieses Tools wurden Ereignisse in Anwendungs- und Dienstprotokolle\Microsoft Surface Dock Updater geschrieben.                                                                                                  |
| Windows Device Install log       | %windir%\inf\setupapi.dev.log           | Weitere Informationen zur Verwendung des Geräteinstallationsprotokolls finden Sie in der [SetupAPI-Protokollierungsdokumentation.](https://docs.microsoft.com/windows-hardware/drivers/install/setupapi-logging--windows-vista-and-later-) |


**Tabelle 2 Ereignisprotokoll-IDs für Surface Dock Firmware Update**<br>
Ereignisse werden im Anwendungsereignisprotokoll protokolliert.  Hinweis: In früheren Versionen dieses Tools wurden Ereignisse in Anwendungs- und Dienstprotokolle\Microsoft Surface Dock Updater geschrieben.

| Ereignis-ID | Ereignistyp                                                           |
| -------- | -------------------------------------------------------------------- |
| 2001     | Das Firmwareupdate für Dock wurde gestartet.                                    |
| 2002     | Dock Firmware update skipped because dock is known to be up to date. |
| 2003     | Fehler beim Herunterladen der Firmwareversion durch das Dock-Firmware-Update.                 |
| 2004     | Abfragen der Firmwareversion.                                       |
| 2005     | Die Firmware von Dock konnte das Update nicht starten.                                |
| 2006     | Fehler beim Senden von Angebots-/Nutzlastpaaren.                                  |
| 2007     | Das Firmwareupdate wurde abgeschlossen.                                            |
| 2008     | BEGIN Dock-Telemetrie.                                                |
| 2011     | End dock telemetry.                                                  |

## Hinweise zur Problembehandlung

- Trennen Sie die Stromversorgung für Surface Dock vollständig vom Netzstrom, um Surface Dock zurückzusetzen.
- Trennen Sie alle Peripheriegeräte mit Ausnahme von Surface Dock.
- Deinstallieren Sie alle aktuellen Surface Dock-Firmwareupdates, und installieren Sie dann die neueste Version.
- Stellen Sie sicher, dass das Surface Dock getrennt ist, und lassen Sie dann genügend Zeit, bis das Update wie über eine LED im Ethernetport des Docks überwacht wird. Warten Sie, bis die LED nicht mehr blinkt, bevor Sie Surface Dock von der Stromversorgung trennen.
- Verbinden Sie Surface Dock mit einem anderen Gerät, um zu sehen, ob das Dock aktualisiert werden kann.

## Versionsreferenz

>[!NOTE]
>Die Installationsdatei wird im folgenden Namensformat veröffentlicht: **Surface_Dock_FwUpdate_X.XX.XXX_Win10_XXXXX_XX.XXX.XXXXX_X.MSI** (z. B. Surface_Dock_FwUpdate_1.42.139_Win10_17134_19.084.31680_0.msi) und wird standardmäßig unter "C:\Programme\SurfaceUpdate" installiert.

###  <a name="version-1.53.139.0"></a>Version 1.53.139.0
*Veröffentlichungsdatum: 4. August 2020*

Diese Version des Surface #A0 enthält Fehlerbehebungen und Unterstützung für:
- Aktualisieren von Surface Dock 1 mit Surface Pro X. 
   > [!NOTE]
   > Wenn Sie Surface Pro X ausführen, laden Sie das herunter. ARM64-Build. Verwenden Sie für alle anderen Geräte den AMD64-Build. 

#### Registrierungsschlüsselwerte

Die Registrierungswerte, die den Status von Firmwareupdates angeben, sind gegenüber der vorherigen Version dieses Tools unverändert: 

- Component10CurrentFwVersion wurde auf **4ac3970 aktualisiert.**
- Component20CurrentFwVersion wurde auf **4a1d570 aktualisiert.**
 
###  <a name="version-1.42.139"></a>Version 1.42.139 
*Veröffentlichungsdatum: 18. September 2019*

Diese version, contained in Surface_Dock_FwUpdate_1.42.139_Win10_17134_19.084.31680_0.MSI, updates firmware in the background. 

#### Aktualisierte Registrierungsschlüsselwerte

- Component10CurrentFwVersion wurde auf **4ac3970 aktualisiert.**
- Component20CurrentFwVersion wurde auf **4a1d570 aktualisiert.**

Es bietet Unterstützung für Surface Pro 7 und Surface Laptop 3.

##  <a name="legacy-versions"></a>Legacyversionen

###  <a name="version-2.23.139.0"></a>Version 2.23.139.0
*Veröffentlichungsdatum: 10. Oktober 2018*

Diese Version von Surface Dock Updater fügt Unterstützung für Folgendes hinzu:

- Hinzufügen von Unterstützung für Surface Pro 6
- Hinzufügen von Unterstützung für Surface Laptop 2


###  <a name="version-2.22.139.0"></a>Version 2.22.139.0
*Veröffentlichungsdatum: 26. Juli 2018*

Diese Version von Surface Dock Updater fügt Unterstützung für Folgendes hinzu:

- Erhöhen der Updatezuverlässigkeit
- Hinzufügen von Unterstützung für Surface Go

###  <a name="version-2.12.136.0"></a>Version2.12.136.0
*Veröffentlichungsdatum: 29.Januar2018*

Diese Version von Surface Dock Updater fügt Unterstützung für Folgendes hinzu:
* Update für Surface Dock Hauptchipsatz-Firmware
* Update für Surface Dock DisplayPort-Firmware
* Verbesserte Anzeigestabilität für externe Displays bei Verwendung mit Surface Book oder Surface Book 2

Darüber hinaus umfasst die Installation dieser Version von Surface Dock Updater auf Surface Book-Geräten Folgendes:
* Update für Surface Book Basis-Firmware
* Neue Unterstützung für Surface Dock Firmware-Updates mit Verbesserungen für Surface Book-Geräte


###  <a name="version-2.9.136.0"></a>Version2.9.136.0
*Veröffentlichungsdatum: 3. November2017*

Diese Version von Surface Dock Updater fügt Unterstützung für Folgendes hinzu:

* Update für Surface Dock DisplayPort-Firmware
* Behebt ein Problem bei der Audiowiedergabe über passive Anzeigeport-Adapter

###  <a name="version-2.1.15.0"></a>Version2.1.15.0
*Veröffentlichungsdatum: 19.06.2017*

Diese Version von Surface Dock Updater fügt Unterstützung für Folgendes hinzu:

* Surface Laptop
* Surface Pro

###  <a name="version-2.1.6.0"></a>Version2.1.6.0
*Veröffentlichungsdatum: 7.April2017*

Diese Version von Surface Dock Updater fügt Unterstützung für Folgendes hinzu:

* Update für Surface Dock DisplayPort-Firmware
* Erfordert Windows10

###  <a name="version-2.0.22.0"></a>Version2.0.22.0
*Veröffentlichungsdatum: 21.Oktober2016*

Diese Version von Surface Dock Updater fügt Unterstützung für Folgendes hinzu:

* Update für SurfaceDock-USB-Firmware
* Verbesserte Zuverlässigkeit von Ethernet-, Audio- und USB-Anschlüssen

###  <a name="version-1.0.8.0"></a>Version1.0.8.0
*Veröffentlichungsdatum: 26.April2016*

Diese Version von Surface Dock Updater fügt Unterstützung für Folgendes hinzu:

* Firmwareupdate für Surface Dock Main-Chipsatz
* Update für Surface Dock DisplayPort-Firmware

