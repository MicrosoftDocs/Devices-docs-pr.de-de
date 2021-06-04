---
title: Anpassen der Windows-Willkommensseite für die Bereitstellung von Surface-Geräten (Surface)
description: Dieser Artikel beschreibt, wie Sie die Windows-Willkommensseite von Surface für Endbenutzer in Ihrer Organisation anpassen.
ms.assetid: F6910315-9FA9-4297-8FA8-2C284A4B1D87
ms.reviewer: ''
manager: laurawi
keywords: bereitstellen, anpassen, automatisieren, Netzwerk, Stift, koppeln, starten
ms.localizationpriority: medium
ms.prod: w10
ms.mktglfcycl: deploy
ms.pagetype: surface, devices
ms.sitesec: library
author: coveminer
ms.author: greglin
ms.topic: article
ms.audience: itpro
ms.openlocfilehash: 97cc262d803875a76427d04c8f9b70547152f895
ms.sourcegitcommit: 109d1d7608ac4667564fa5369e8722e569b8ea36
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/27/2020
ms.locfileid: "10833268"
---
# Anpassen der Windows-Willkommensseite für die Bereitstellung von Surface-Geräten

In diesem Artikel wird beschrieben, wie Sie die Oberfläche außerhalb der Box für Endbenutzer in Ihrer Organisation anpassen.

Üblicherweise wird bei der Windows-Bereitstellung die erste Seite angepasst, die der Benutzer beim Start eines bereitgestellten Computers sieht – die Windows-Willkommensseite.

>[!NOTE]
>Als Windows-Willkommensseite wird auch häufig die Konfigurationsphase von Windows Setup bezeichnet, während der die Benutzeroberfläche angezeigt wird. Weitere Informationen zu dieser Konfigurationsphase von Windows Setup finden Sie unter [Funktionsweise von Konfigurationsphasen](https://msdn.microsoft.com/library/windows/hardware/dn898581.aspx).

In bestimmten Fällen sollten Sie die vollständige Automatisierung ermöglichen, um sicherzustellen, dass die Computer im Anschluss an die Bereitstellung ohne eine weitere Interaktion des Benutzers verwendet werden können. In anderen Fällen ist es sinnvoller, die Konfiguration der wichtigsten Elemente der Willkommensseite dem Benutzer zu überlassen, z.B. falls Benutzereingaben erforderlich sind oder eine Auswahl zwischen wichtigen Optionen getroffen werden muss. Für Administratoren, die Surface-Geräte bereitstellen, stellen beide Szenarien eine Herausforderung dar.

> [!NOTE]
> Dieser Artikel gilt nicht für Surface pro X. Weitere Informationen finden Sie unter [bereitstellen, verwalten und warten von Surface pro X](surface-pro-arm-app-management.md)

In diesem Artikel werden die Szenarien vorgestellt, die bei der Bereitstellung u.U. zusätzliche Schritte erforderlich machen. Darüber hinaus liefert er Informationen dazu, wie Sie sicherstellen, dass die Benutzer in Ihrer Organisation mit der Willkommensseite ihres neu bereitgestellten Surface-Geräts zufrieden sind. Dieser Artikel ist insbesondere für Administratoren gedacht, die mit dem Bereitstellungsprozess und Konzepten wie beispielsweise Antwortdateien und [Referenzimages](https://technet.microsoft.com/itpro/windows/deploy/create-a-windows-10-reference-image) vertraut sind.

>[!NOTE]
>Obwohl die OOBE-Phase des Setups während einer Bereitstellung mit einer automatisierten Bereitstellungslösung wie dem [Microsoft Deployment Toolkit (MDT)](https://go.microsoft.com/fwlink/p/?LinkId=618117) oder der Microsoft Endpoint Configuration Manager-Betriebs System Bereitstellung (OSD) weiterhin ausgeführt wird, erfolgt die Automatisierung durch die Einstellungen, die im Bereitstellungs-Assistenten und in der Tasksequenz bereitgestellt werden. Weitere Informationen finden Sie unter:<br/>
>- [Bereitstellen von Windows 10 mit dem Microsoft Deployment Toolkit](https://technet.microsoft.com/itpro/windows/deploy/deploy-windows-10-with-the-microsoft-deployment-toolkit)
>- [Bereitstellen von Windows10 mit System Center2012R2 Configuration Manager](https://technet.microsoft.com/itpro/windows/deploy/deploy-windows-10-with-system-center-2012-r2-configuration-manager)

 

##  <a name="scenario-1:-wireless-networking-in-oobe-with-mdt-2013"></a>Szenario 1: Drahtlosnetzwerke und die Konfiguration der Windows-Willkommensseite mit MDT 2013


Wenn ein Drahtlosnetzwerkadapter vorhanden ist, wird während der Konfiguration der Windows-Willkommensseite die Option **Einem Drahtlosnetzwerk beitreten** angezeigt. Der Benutzer wird aufgefordert, eine Verbindung mit einem Drahtlosnetzwerk herzustellen. Diese Seite wird nicht automatisch von Bereitstellungstechnologien wie MDT 2013 ausgeblendet. Sie wird daher auch angezeigt, wenn die Bereitstellung als vollständig automatisiert konfiguriert ist.

Um sicherzustellen, dass eine automatisierte Bereitstellung von dieser Seite nicht angehalten wird, müssen Sie die Seite ausblenden, indem Sie eine zusätzliche Einstellung in der Antwortdatei konfigurieren: **HideWirelessSetupInOOBE**. Weitere Informationen zur Einstellung **HideWirelessSetupInOOBE** finden Sie unter [Referenz für das unbeaufsichtigte Windows Setup](https://technet.microsoft.com/library/ff716213.aspx).

##  <a name="scenario-2:-surface-pen-pairing-in-oobe"></a>Szenario 2: Koppeln mit dem Surface-Stift auf der Windows-Willkommensseite


Wenn Sie ein Surface Pro 3, Surface Pro 4, Surface Book oder Surface Studio zum ersten Mal auspacken und starten, wird bei der ersten Ausführung des Standardimages eine Meldung mit der Aufforderung angezeigt, den im Paket enthaltenen Surface-Stift mit dem Gerät zu koppeln. Diese Aufforderung wird zwar in dem mit dem Gerät gelieferten Standardimage angezeigt, nicht aber in anderen Bereitstellungsimages, wie etwa den Windows Enterprise-Installationsmedien, die im Volume Licensing Service Center zum Download bereitstehen. Die Kopplung des Bluetooth-Surface-Stifts außerhalb der Konfiguration der Windows-Willkommensseite macht es erforderlich, die Systemsteuerungseinstellungen bzw. die PC-Einstellungen einzugeben und die Kopplung mit einem Bluetooth-Gerät manuell durchzuführen. Aus diesem Grund kann es sinnvoll sein, den Kopplungsvorgang über diese Aufforderung von dem Benutzer oder einem Techniker durchführen zu lassen.

Um den Standardkopplungsvorgang mit dem Surface-Stift auf der Windows-Willkommensseite bereitzustellen, müssen Sie vier Dateien aus dem Surface-Standardimage in das Referenzimage kopieren. Sie können diese Dateien in die Referenzumgebung kopieren, bevor Sie das Referenzimage erfassen, oder Sie können sie später mithilfe der Abbildverwaltung für die Bereitstellung (Deployment Image Servicing and Management, DISM) zum Einbinden des Image hinzufügen. Die vier erforderlichen Dateien sind:

-   %windir%\\system32\\oobe\\info\\default\\1033\\oobe.xml
-   %windir%\\system32\\oobe\\info\\default\\1033\\PenPairing\_en-US.png
-   %windir%\\system32\\oobe\\info\\default\\1033\\PenError\_en-US.png
-   %windir%\\system32\\oobe\\info\\default\\1033\\PenSuccess\_en-US.png

>[!NOTE]
>Sie sollten die Dateien aus einem Standardimage eines Surface-Gerätemodells kopieren, das identisch ist mit dem, das Sie bereitstellen möchten. Beispielsweise sollten Sie die Dateien von Surface pro 7 für die Bereitstellung auf Surface pro 7 und die Dateien von Surface Book 2 zum Bereitstellen von Surface Book 2 verwenden, Sie sollten jedoch die Dateien von Surface pro 7 nicht verwenden, um Surface Book oder Surface pro 6 bereitzustellen.

 

Unter [Deploying Surface Pro 3 Pen and OneNote Tips](https://blogs.technet.microsoft.com/askcore/2014/07/15/deploying-surface-pro-3-pen-and-onenote-tips/) (Tipps zum Bereitstellen des SurfacePro3-Stifts und von OneNote) finden Sie Informationen, wie Sie diese erforderlichen Dateien schrittweise einem Image hinzufügen. Dieser Blogbeitrag enthält auch Tipps zur Installation der erforderlichen Updates zum schnellen Festhalten von Notizen mit dem Surface-Stift. Benutzer können so auf Knopfdruck Notizen an OneNote schicken.

 

 





