---
title: Aktivieren von PEAP, EAP-FAST und Cisco LEAP auf Surface-Geräten (Surface)
description: Erfahren Sie, wie Sie Unterstützung für PEAP-, EAP-FAST- oder Cisco LEAP-Protokolle auf Ihrem Surface-Gerät bereitstellen.
ms.assetid: A281EFA3-1552-467D-8A21-EB151E58856D
ms.reviewer: ''
manager: laurawi
keywords: Netzwerk, drahtlos, Gerät, bereitstellen, Authentifizierung, Protokoll
ms.localizationpriority: medium
ms.prod: w10
ms.mktglfcycl: deploy
ms.pagetype: surface, devices
ms.sitesec: library
author: coveminer
ms.author: greglin
ms.topic: article
ms.openlocfilehash: 1a9bef0a6e0bfdd4bede1b508b4013fd14e1a0bd
ms.sourcegitcommit: 109d1d7608ac4667564fa5369e8722e569b8ea36
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/27/2020
ms.locfileid: "10833496"
---
# Aktivieren von PEAP, EAP-FAST und Cisco LEAP auf Surface-Geräten


Erfahren Sie, wie Sie Unterstützung für PEAP-, EAP-FAST- oder Cisco LEAP-Protokolle auf Ihrem Surface-Gerät bereitstellen.

Wenn Sie in Ihrem Unternehmensnetzwerk PEAP, EAP-FAST oder Cisco LEAP verwenden, wissen Sie wahrscheinlich bereits, dass diese drei Drahtlosauthentifizierungsprotokolle von Surface-Geräten nicht ohne weitere Konfiguration unterstützt werden. Benutzer stellen dies möglicherweise fest, wenn sie versuchen, eine Verbindung mit Ihrem Drahtlosnetzwerk herzustellen, oder wenn sie nicht auf Ressourcen innerhalb des Netzwerks zugreifen können, wie z.B. Dateifreigaben und interne Websites. Weitere Informationen finden Sie unter [Extensible Authentication-Protokoll](https://technet.microsoft.com/network/bb643147).

Sie können Unterstützung für diese Protokolle bereitstellen, indem Sie ein kleines MSI-Paket von einem USB-Stick oder von einer Dateifreigabe ausführen. Für Organisationen, die EAP-Unterstützung auf Ihren Surface-Geräten aktivieren möchten, unterstützt das MSI-Paketformat die Bereitstellung mit zahlreichen Verwaltungs-und Bereitstellungstools wie dem Microsoft Deployment Toolkit (MDT) und dem Microsoft Endpoint Configuration Manager.

## <a href="" id="download-peap--eap-fast--or-cisco-leap-installation-files--"></a>PEAP-, EAP-FAST- oder Cisco-LEAP-Installationsdateien herunterladen


Sie können die MSI-Installationsdateien für PEAP, EAP-FAST oder Cisco LEAP in einer einzelnen ZIP-Archivdatei aus dem Microsoft Download Center herunterladen. Um diese Datei herunterzuladen, besuchen Sie die Seite [Surface Tools for IT](https://www.microsoft.com/download/details.aspx?id=46703) (Surface-Tools für IT-Experten) im Microsoft Download Center, klicken Sie auf **Download**, und wählen Sie dann die Datei **Cisco EAP-Supplicant Installer.zip** aus.

##  <a name="deploy-peap,-eap-fast,-or-cisco-leap-with-mdt"></a>Bereitstellen von PEAP, EAP-FAST oder Cisco LEAP mit MDT


Wenn Sie in Ihrer Organisation bereits Windows auf Surface-Geräten bereitstellen, können Sie die Installationsdateien für die Protokolle einfach zur Bereitstellungsfreigabe hinzufügen und während der Bereitstellung die automatische Installation konfigurieren. Sie können sogar eine Tasksequenz konfigurieren, die zuvor bereitgestellte Surface-Geräte aktualisiert, damit für diese Protokolle auf die gleiche Weise Unterstützung bereitgestellt werden kann.

Führen Sie die folgenden Schritte aus, um Unterstützung für PEAP, EAP-FAST oder Cisco LEAP auf neu bereitgestellten Surface-Geräten zu bieten:

1.  Wenn Sie die Installationsdateien für die Protokolle heruntergeladen haben, extrahieren Sie sie in getrennten Ordnern an einem leicht zugänglichen Speicherort.

2.  Öffnen Sie die Deployment Workbench von MDT, und erweitern Sie die Bereitstellungsfreigabe für den Ordner **Anwendungen**.

3.  Wählen Sie im Bereich **Aktion** die Option **Neue Anwendung** aus.

4.  Wählen Sie die Option **Anwendung mit Quelldateien** aus, um die MSI-Dateien in die Bereitstellungsfreigabe zu kopieren.

5.  Wählen Sie den Ordner aus, den Sie in Schritt1 für das gewünschte Protokoll erstellt haben.

6.  Benennen Sie den Ordner in der Bereitstellungsfreigabe, in dem die Installationsdateien gespeichert werden.

7.  Geben Sie die Befehlszeile an, um die Anwendung bereitzustellen:

    -   Für PEAP: **EAP-PEAP.msi/qn/norestart**.

    -   Für LEAP: **EAP-LEAP.msi/qn/norestart**.

    -   Für EAP-FAST: **EAP-FAST.msi/qn/norestart**.

8.  Verwenden Sie die Standardoptionen, um den Assistenten für neue Anwendungen abzuschließen.

9.  Wiederholen Sie die Schritte 3 bis 8 für jedes gewünschte Protokoll.

Nachdem Sie diese Schritte ausgeführt und die drei MSI-Pakete als Anwendungen in MDT importiert haben, können sie auf der Anwendungsseite des Windows-Bereitstellungs-Assistenten ausgewählt werden. Obwohl es in einfachen Bereitstellungsszenarien u.U. möglich ist, dass Techniker jedes Paket zum Zeitpunkt der Bereitstellung auswählen, ist dies nicht zu empfehlen. Da man menschliches Versagen nicht ausschließen kann, besteht die Möglichkeit, dass ein Techniker diese Pakete auf anderen Computern als Surface-Geräten anwendet oder ein Surface-Gerät ohne EAP-Unterstützung bereitstellt.

Wenn Sie diese Anwendungen auf der Seite zum Installieren von Anwendungen ausblenden möchten, aktivieren Sie das Kontrollkästchen **Hide this application in the Deployment Wizard **in den Eigenschaften der einzelnen Anwendungen. Nachdem die Anwendungen ausgeblendet wurden, werden sie während der Bereitstellung nicht als optionale Anwendungen angezeigt. Um sie in der Tasksequenz für die Bereitstellung eines Surface-Geräts installieren zu können, müssen sie über einen separaten Schritt explizit für die Installation in der Tasksequenz definiert werden.

Wenn Sie die Protokolle explizit angeben möchten, gehen Sie wie folgt vor:

1.  Öffnen Sie über die MDT Deployment Workbench die Eigenschaften der Tasksequenz für die Bereitstellung des Surface-Geräts.

2.  Wählen Sie auf der Registerkarte **Tasksequenz** unter **Status wiederherstellen** den Schritt **Anwendungen installieren**. Dieser Abschnitt befindet sich in der Regel zwischen den Schritten für Windows Update (Pre-Application) und Windows Update (Post-Application).

3.  Verwenden Sie die Schaltfläche **Hinzufügen**, um einen neuen Schritt **Anwendung installieren** in der Kategorie **Allgemein** zu erstellen.

4.  Wählen Sie auf der Registerkarte **Eigenschaften** die Option **Eine einzelne Anwendung installieren** aus.

5.  Wählen Sie das gewünschte EAP-Protokoll aus der Liste aus.

6.  Wiederholen Sie die Schritte 2 bis 5 für jedes gewünschte Protokoll.

##  <a name="deploy-peap,-eap-fast,-or-cisco-leap-with-configuration-manager"></a>Bereitstellen von PEAP, EAP-FAST oder Cisco LEAP mit Configuration Manager


Für Unternehmen, die Surface-Geräte mit Configuration Manager verwalten, ist es noch einfacher, Unterstützung für PEAP, EAP-FAST oder Cisco LEAP auf Surface-Geräten bereitzustellen. Importieren Sie lediglich jede MSI-Datei als Anwendung aus der Softwarebibliothek, und konfigurieren Sie die Bereitstellung auf Ihren Surface-Geräten.

Weitere Informationen zum Bereitstellen von Anwendungen mit Configuration Manager finden Sie unter [Erstellen von Anwendungen in Configuration Manager](https://technet.microsoft.com/library/gg682159.aspx) und [Bereitstellen von Anwendungen in Configuration Manager](https://technet.microsoft.com/library/gg682082.aspx).

 

 





