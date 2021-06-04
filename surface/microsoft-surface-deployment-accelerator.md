---
title: Microsoft Surface Deployment Accelerator (Surface)
description: Microsoft Surface Deployment Accelerator bietet einen schnellen und einfachen Bereitstellungsmechanismus für Organisationen, die ein Reimaging von Surface-Geräten durchführen möchten.
ms.assetid: E7991E90-4AAE-44B6-8822-58BFDE3EADE4
ms.reviewer: hachidan
manager: laurawi
ms.localizationpriority: medium
keywords: bereitstellen, installieren, Tool
ms.prod: w10
ms.mktglfcycl: deploy
ms.pagetype: surface, devices
ms.sitesec: library
author: coveminer
ms.author: greglin
ms.topic: article
ms.audience: itpro
ms.date: 5/08/2020
ms.openlocfilehash: 3ede7311289dc4bc720735c0142ff3a46fbb69e7
ms.sourcegitcommit: 582c5a79881c58c4f1aa66cfcab46db966ca9f24
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/16/2020
ms.locfileid: "11016556"
---
# Microsoft Surface Deployment Accelerator

Microsoft Surface Deployment Accelerator (SDA) automatisiert die Erstellung und Konfiguration einer von Microsoft empfohlenen Bereitstellungsumgebung mithilfe von kostenlosen Microsoft-Bereitstellungstools.

Im April 2020 neu gestaltet, um die Bereitstellung von Surface-Images in einer Unternehmensumgebung zu vereinfachen und zu automatisieren, können Sie mit dem SDA-Tool ein Windows-Abbild erstellen, das Sie an Ihre organisatorischen Anforderungen anpassen können.

Das Open Source-skriptgesteuerte SDA-Tool nutzt das Windows Assessment and Deployment Kit (ADK) für Windows 10, wodurch die Erstellung von Windows-Images (WIM) in Test-oder Produktionsumgebungen vereinfacht wird. Wenn das neueste ADK noch nicht installiert ist, wird es heruntergeladen und installiert, wenn das SDA-Tool ausgeführt wird.

Das resultierende Bild entspricht in engem Zusammenhang mit der Konfiguration von grundlegendem (Bare Metal Recovery)-Bildern ohne vorinstallierte Anwendungen wie Microsoft Office oder die Surface UWP-Anwendung.

##  <a name="requirements"></a>Anforderungen

1. Ein USB-Stick mit einer Größe von mindestens 16 GB. Das USB-Laufwerk wird formatiert.
2. Eine ISO-Datei mit Windows 10 pro oder Windows 10 Enterprise. Das Medien Erstellungstool kann zum Herunterladen von Windows 10 und zum Erstellen einer ISO-Datei verwendet werden. Weitere Informationen finden Sie unter [Herunterladen von Windows 10](https://www.microsoft.com/software-download/windows10).
3. Ein Gerät, auf dem Windows 10, Version 2004 oder höher, mit Internet Zugriff ausgeführt wird.

Eine detaillierte Liste der Anforderungen finden Sie im Abschnitt [Voraussetzungen](https://github.com/microsoft/SurfaceDeploymentAccelerator/blob/master/README.md#prerequisites) des Readme-Dokuments.

##  <a name="how-to-run-the-sda"></a>Ausführen des SDA

**So führen Sie SDA aus:**

1. Wechseln Sie zu [SurfaceDeploymentAccelerator](https://github.com/microsoft/SurfaceDeploymentAccelerator) auf GitHub. 
2. Lesen Sie die [Readme](https://github.com/microsoft/SurfaceDeploymentAccelerator/blob/master/README.md) -Dokumentation.
3. Klicken Sie auf der [SurfaceDeploymentAccelerator](https://github.com/microsoft/SurfaceDeploymentAccelerator) -Seite auf die Schaltfläche **Code** , und wählen Sie dann **ZIP herunterladen** aus, um die Dateien lokal auf Ihrem Computer zu speichern.
4. Klicken Sie mit der rechten Maustaste auf die ZIP-Datei, und klicken Sie dann auf **Eigenschaften**.
5. Aktivieren Sie auf der Registerkarte **Allgemein** das Kontrollkästchen **Blockierung aufheben** , und klicken Sie dann auf **OK**.
6. Extrahieren Sie die ZIP-Datei an einen Speicherort auf Ihrer Festplatte (z. b.: C:\SDA).
7. Öffnen Sie eine Windows PowerShell-Eingabeaufforderung mit erhöhten Rechten, und legen Sie ExecutionPolicy für die aktuelle Sitzung auf Unrestricted.

    ```powershell
    Set-ExecutionPolicy -Scope Process -ExecutionPolicy Unrestricted -Force
    ```
8. Führen Sie das SDA-Skript aus, das Parameter für Ihre Umgebung angibt. Mithilfe des Skripts können Bilder erstellt werden, um Windows 10 auf einer Vielzahl von Surface-Geräten zu installieren. Eine vollständige Liste der unterstützten Geräte finden Sie im Readme-Artikel zu SDA unter [Geräteparameter](https://github.com/microsoft/SurfaceDeploymentAccelerator/blob/master/README.md#full-parameter-documentation) . 

    Mit dem folgenden Befehl wird beispielsweise ein bootfähiges USB-Laufwerk erstellt, das zum [Installieren von Windows 10 auf Surface Hub 2](https://docs.microsoft.com/surface-hub/surface-hub-2s-migrate-os)verwendet werden kann:

    ```powershell
    .\CreateSurfaceWindowsImage.ps1 -ISO C:\SDA\enterprise_client.iso -OSSKU Enterprise -DestinationFolder C:\Output -Device SurfaceHub2 -CreateUSB $True
    ```
    Beispiel für eine Skriptausgabe:

   ![Tool zum Ausführen des Surface-Bereitstellungs Beschleunigers](images/sda1.png)

    Das Skript erfordert etwa 45 Minuten für die Ausführung, kann aber je nach verfügbarer CPU-und Datenträgerressourcen länger dauern. 

    Nach dem Erstellen eines Windows-Abbilds werden Sie vom Skript aufgefordert, den Laufwerkbuchstaben Ihres USB-Laufwerks einzufügen und zu bestätigen. Das USB-Laufwerk wird dann formatiert, als bootfähig konfiguriert und Dateien kopiert, um die Installation des benutzerdefinierten Windows 10-Bilds für Surface-Geräte zu ermöglichen.

9. Legen Sie das USB-Laufwerk in das Gerät ein, auf dem Sie Windows 10 installieren möchten, und starten Sie die Installation von Windows 10. USB-Start muss im BIOS aktiviert sein, was eine vorübergehende Deaktivierung des sicheren Starts erfordern kann.

> [!IMPORTANT]
> Das Booten vom USB-Laufwerk beginnt sofort mit der Installation von Windows 10. Stellen Sie sicher, dass Ihr Gerät bereit ist, bevor Sie den USB-Anschluss einfügen und neu starten. 

##  <a name="related-links"></a>Verwandte Links

 - [Open-Source-Image-Bereitstellungstool auf GitHub veröffentlicht](https://techcommunity.microsoft.com/t5/surface-it-pro-blog/open-source-image-deployment-tool-released-on-github/ba-p/1314115)
 - [Herunterladen und Installieren des Windows ADK](https://docs.microsoft.com/windows-hardware/get-started/adk-install)
