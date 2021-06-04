---
title: Überlegungen zu Surface und Microsoft Endpoint Configuration Manager
description: Die Verwaltung und Bereitstellung von Surface-Geräten mit Configuration Manager ist im Grunde mit allen anderen PCs identisch. in diesem Artikel werden Szenarien beschrieben, in denen weitere Überlegungen erforderlich sind.
keywords: verwalten, Bereitstellung, Updates, Treiber, Firmware
ms.prod: w10
ms.mktglfcycl: deploy
ms.pagetype: surface, devices
ms.sitesec: library
author: coveminer
ms.author: greglin
ms.topic: article
ms.localizationpriority: medium
ms.audience: itpro
ms.reviewer: ''
manager: laurawi
ms.openlocfilehash: 4fa62d227deb0b0b07fa0fbc6552ea5b04c1b87b
ms.sourcegitcommit: 109d1d7608ac4667564fa5369e8722e569b8ea36
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/27/2020
ms.locfileid: "10832566"
---
# Überlegungen zu Surface und Microsoft Endpoint Configuration Manager

Im Grunde ist das Management und die Bereitstellung von Surface-Geräten mit Microsoft Endpoint Configuration Manager mit der Verwaltung und Bereitstellungeines beliebigen anderen PCs identisch. Wie bei jedem anderen PC umfasst eine Bereitstellung auf Surface-Geräten den Import von Treibern, das Importieren eines Windows-Abbilds, das Vorbereiten einer Bereitstellungstasksequenz und das anschließende Bereitstellen der Tasksequenz in einer Sammlung. Nach der Bereitstellung sind Surface-Geräte wie alle anderen Windows-Clients; zum Veröffentlichen von apps, Einstellungen und Richtlinien verwenden Sie denselben Prozess wie für andere Geräte.

Weitere Informationen zum Verwenden von Configuration Manager zum Bereitstellen und Verwalten von Geräten finden Sie in der [Dokumentation für Microsoft Endpoint Configuration Manager](https://docs.microsoft.com/sccm/index).

Obwohl die Bereitstellung und Verwaltung von Surface-Geräten im Grunde mit jedem anderen PC identisch ist, gibt es einige Szenarien, in denen zusätzliche Überlegungen oder Schritte erforderlich sind. Dieser Artikel enthält Beschreibungen und Anleitungen für diese Szenarien. Die in diesem Artikel beschriebenen Lösungen gelten möglicherweise auch für andere Geräte und Hersteller.

> [!NOTE]
> Für die Verwaltung von Surface-Geräten empfiehlt es sich, die aktuelle Verzweigung des Microsoft Endpoint Configuration Manager zu verwenden.

##  <a name="updating-surface-device-drivers-and-firmware"></a>Aktualisieren von Surface-Gerätetreibern und-Firmware

Bei Geräten, die Updates über Windows Update erhalten, werden Treiber für Surface-Komponenten (und sogar Firmware-Updates) automatisch als Teil des Windows Update-Prozesses übernommen. Informationen zu Geräten mit verwalteten Updates, die über Windows Server Update Services (WSUS) oder Configuration Manager aktualisiert wurden, finden Sie unter [Verwalten von Oberflächen Treiber-und Firmware-Updates](https://docs.microsoft.com/surface/manage-surface-driver-and-firmware-updates/).

> [!NOTE]
> Surface-Gerätetreiber und-Firmware sind mit SHA-256 signiert, das nicht von Windows Server 2008 R2 nativ unterstützt wird. Eine Problemumgehung ist für Configuration Manager-Umgebungen verfügbar, die unter Windows Server 2008 R2 ausgeführt werden. Weitere Informationen finden Sie unter [nicht importieren von Treibern in Microsoft Endpoint Configuration Manager (KB3025419)](https://support.microsoft.com/kb/3025419).

##  <a name="surface-ethernet-adapters-and-configuration-manager-deployment"></a>Surface Ethernet-Adapter und Configuration Manager-Bereitstellung

Der Standardmechanismus, der von Configuration Manager zur Identifizierung von Geräten während der Bereitstellung verwendet wird, ist die Mac-Adresse (Media Access Control). Da die Mac-Adresse dem Ethernet-Controller zugeordnet ist, führt ein von mehreren Geräten geteilter Ethernet-Adapter dazu, dass Configuration Manager die einzelnen Geräte als nur ein einzelnes Gerät erkennt. Dies kann dazu führen, dass eine Configuration Manager-Bereitstellung von Windows nicht auf bestimmte Geräte angewendet wird.

Um sicherzustellen, dass Oberflächen Geräte, die denselben Ethernet-Adapter verwenden, während der Bereitstellung als eindeutige Geräte erkannt werden, können Sie Configuration Manager anweisen, Geräte mithilfe einer anderen Methode zu identifizieren. Bei dieser anderen Methode kann es sich um die Mac-Adresse des Drahtlosnetzwerkadapters oder die universelle eindeutige Kennung des Systems (System UUID) handeln. Sie können angeben, dass Configuration Manager andere Identifikationsmethoden mit den folgenden Optionen verwenden soll:

* Fügen Sie einen Ausschluss für die Mac-Adressen von Surface Ethernet-Adaptern hinzu, die den Configuration Manager dazu zwingen, die Mac-Adresse in der Präferenz der System-UUID zu übersehen, wie in der wieder [Verwendung derselben NIC für mehrere PXE-initiierte Bereitstellungen im SMicrosoft Endpoint Configuration Manager OSD-](https://blogs.technet.microsoft.com/system_center_configuration_manager_operating_system_deployment_support_blog/2015/08/27/reusing-the-same-nic-for-multiple-pxe-initiated-deployments-in-system-center-configuration-manger-osd/) Blogbeitrag dokumentiert.

* Vorstufen von Geräten nach System-UUID, wie in der wieder [Verwendung derselben NIC für mehrere PXE-initiierte Bereitstellungen im Microsoft Endpoint Configuration Manager-OSD-](https://blogs.technet.microsoft.com/system_center_configuration_manager_operating_system_deployment_support_blog/2015/08/27/reusing-the-same-nic-for-multiple-pxe-initiated-deployments-in-system-center-configuration-manger-osd/) Blogbeitrag dokumentiert.

* Verwenden Sie ein Skript, um ein neu bereitgestelltes Surface-Gerät anhand der Mac-Adresse seines WLAN-Adapters zu identifizieren, wie in der [Verwendung desselben externen Ethernet-Adapters für mehrere SCCM OSD](https://blogs.technet.microsoft.com/askpfeplat/2014/07/27/how-to-use-the-same-external-ethernet-adapter-for-multiple-sccm-osd/) -Blogbeiträge dokumentiert.

Ein weiterer Aspekt des Surface Ethernet-Adapters während der Bereitstellung mit Configuration Manager ist der Treiber für den Ethernet-Controller. Ab Windows 10, Version 1511, ist der Treiber für den Surface Ethernet-Adapter standardmäßig in Windows enthalten. Für Organisationen, die die neueste Version von Windows 10 bereitstellen und die neueste Version von WinPE verwenden möchten, erfordert die Verwendung des Surface Ethernet-Adapters keine zusätzlichen Aktionen.

Für Windows-Versionen vor Windows 10, Version 1511 (einschließlich Windows 10 RTM und Windows 8,1), müssen Sie möglicherweise den Surface Ethernet-Adaptertreiber installieren und den Treiber in Ihr WinPE-Startmedium aufnehmen. Mit der Aufnahme in Windows 10 steht der Treiber nicht mehr im Microsoft Download Center zum Download zur Verfügung. Zum Herunterladen des Surface-Ethernet-Adaptertreibers laden Sie ihn aus dem Microsoft Update-Katalog herunter, wie er im Blogbeitrag [Surface Ethernet Drivers](https://blogs.technet.microsoft.com/askcore/2016/08/18/surface-ethernet-drivers/) vom Blog Ask the Core Team dokumentiert ist.

##  <a name="deploy-surface-app-with-configuration-manager"></a>Bereitstelleneiner Surface-App mit Configuration Manager

Mit der Veröffentlichung von Microsoft Store für Unternehmen steht Surface APP nicht mehr als Treiber-und Firmware-Download zur Verfügung. Organisationen, die Surface-apps auf verwalteten Surface-Geräten oder während der Bereitstellung mit der Verwendung von Configuration Manager bereitstellen möchten, müssen Surface-App über Microsoft Store for Business erwerben und dann Surface-App mit PowerShell bereitstellen. In der TechNet-Bibliothek finden Sie die PowerShell-Befehle für die Bereitstellung der Surface-APP, Anweisungen zum Herunterladen der Surface-APP und erforderliche Frameworks aus dem Microsoft Store für Unternehmen im Artikel [Bereitstellen von Surface-apps mit Microsoft Store for Business](https://technet.microsoft.com/itpro/surface/deploy-surface-app-with-windows-store-for-business) .

##  <a name="use-prestaged-media-with-surface-clients"></a>Verwenden von vorinszenierten Medien mit Surface-Clients

Wenn Ihre Organisation Pre-Staging-Medien verwendet, um Bereitstellungsressourcen vor der Bereitstellung mit Configuration Manager auf Computern vorab zu laden, müssen Sie möglicherweise zusätzliche Schritte Unternehmen, wenn Sie für die Verwendung von UEFI-Geräten über Oberflächen Geräte verfügen. Insbesondere erfordert eine systemeigene UEFI-Umgebung, dass Sie mehrere Partitionen auf dem Startdatenträger des Systems erstellen. Wenn Sie zusammen mit der Dokumentation zu [vorab](https://technet.microsoft.com/library/79465d90-4831-4872-96c2-2062d80f5583?f=255&MSPPError=-2147217396#BKMK_CreatePrestagedMedia)bereitgestellten Medien arbeiten, finden Sie in den Anweisungen nur einzelne Partitions Startdisketten, die bei der Anwendung auf Surface-Geräte daher fehlschlagen.

Anweisungen zum Anwenden von vorab bereitgestellten Medien auf UEFI-Geräte wie Surface-Geräte finden Sie unter [so wird es gemacht: Anwenden von vorinszenierten Medien auf mehr partitionierte Datenträger für BIOS-oder UEFI-PCs im Microsoft Endpoint Configuration Manager-](https://blogs.technet.microsoft.com/system_center_configuration_manager_operating_system_deployment_support_blog/2014/04/02/how-to-apply-task-sequence-prestaged-media-on-multi-partitioned-disks-for-bios-or-uefi-pcs-in-system-center-configuration-manager/) Blogbeitrag.

##  <a name="licensing-conflicts-with-oem-activation-3.0"></a>Lizenzierungs Konflikte mit OEM-Aktivierung 3,0

Surface-Geräte sind mit einer lizenzierten Kopie von Windows vorinstalliert. Beispielsweise ist Surface pro 4 mit Windows 10 Professional vorinstalliert. Der Lizenzschlüssel für diese vorinstallierte Kopie von Windows ist in die Firmware des Geräts mit der OEM-Aktivierung 3,0 (OA 3,0) eingebettet. Wenn Sie Windows-Installationsmedien auf einem Gerät mit einem OA 3,0-Schlüssel ausführen, liest Windows Setup automatisch den Lizenzschlüssel und verwendet ihn zum Installieren und Aktivieren von Windows. In den meisten Fällen wird dadurch die Neuinstallation von Windows vereinfacht, da der Benutzer keinen Lizenzschlüssel finden oder eingeben muss.

Wenn Sie ein Gerät mithilfe von Windows Enterprise umbilden, verursacht dieser eingebettete Lizenzschlüssel keinen Konflikt. Dies liegt daran, dass das Installationsmedium für Windows Enterprise so konfiguriert ist, dass nur eine Enterprise Edition von Windows installiert wird und daher mit dem in der System-Firmware eingebetteten Lizenzschlüssel nicht kompatibel ist. Wenn kein Product Key angegeben wird (beispielsweise, wenn Sie beabsichtigen, mit Key Management Services [KMS] oder Active Directory-basierter Aktivierung zu aktivieren), wird ein generischer Volumenlizenzschlüssel (gvlks) verwendet, bis Windows von einer dieser Technologien aktiviert wird.

Probleme können jedoch auftreten, wenn Unternehmen beabsichtigen, Windows-Versionen zu verwenden, die mit dem Embedded-Schlüssel der Firmware kompatibel sind. So kann beispielsweise eine Organisation, die Windows 10 Professional auf einem Surface 3-Gerät installieren möchte, das ursprünglich mit Windows 10 Home Edition ausgeliefert wurde, möglicherweise Schwierigkeiten haben, wenn Windows Setup während der Installation automatisch den Home Edition-Schlüssel liest und als Home Edition statt als Professional installiert wird. Um diesen Konflikt zu vermeiden, können Sie die Datei Ei. cfg oder Pid.txt verwenden, um Windows Setup explizit anzuweisen, einen Product Key einzugeben, oder Sie können einen bestimmten Product Key in die Bereitstellungstasksequenz eingeben. Weitere Informationen finden Sie unter [Windows Setup Edition-Konfigurations-und Produkt-ID-Dateien](https://technet.microsoft.com/library/hh824952.aspx). Wenn Sie nicht über einen bestimmten Schlüssel verfügen, können Sie die standardmäßigen Product Keys für Windows verwenden, die Sie unter [anpassen und Bereitstellen eines Windows 10-Betriebssystems](https://dpcenter.microsoft.com/en/Windows/Build/cp-Windows-10-build) im Geräte Partner Center finden können.

##  <a name="apply-an-asset-tag-during-deployment"></a>Anwenden einer Ressourcenkategorie während der Bereitstellung

Surface Studio-, Surface Book-, Surface pro 4-, Surface pro 3-und Surface 3-Geräte unterstützen die Anwendung einer Asset-Kategorie in UEFI. Mit dieser Asset-Kategorie kann das Gerät aus UEFI identifiziert werden, selbst wenn das Betriebssystem ausfällt, und es kann auch innerhalb des Betriebssystems abgefragt werden. Weitere Informationen zur Funktion Surface Asset Tag finden Sie im Blogbeitrag [Surface pro 3](https://blogs.technet.microsoft.com/askcore/2014/10/20/asset-tag-tool-for-surface-pro-3/) unter dem Posten-Tag-Tool.

Verwenden Sie das Skript und die Anweisungen, die Sie während einer Configuration Manager- [Tasksequenz während eines Blogbeitrags zur Configuration Manager-Tasksequenz](https://blogs.technet.microsoft.com/jchalfant/set-surface-pro-3-asset-tag-during-a-configuration-manager-task-sequence/) gefunden haben, um eine Ressourcenkategorie mit dem [Surface Asset Tag CLI-Dienstprogramm](https://www.microsoft.com/download/details.aspx?id=44076) für die Configuration Manager-Bereitstellungsaufgabe anzuwenden.

##  <a name="configure-push-button-reset"></a>Konfigurieren des Zurücksetzens der Push-Taste

Wenn Sie Windows auf einem Surface-Gerät bereitstellen, ist die Funktion zum Zurücksetzen des Push-Buttons von Windows standardmäßig so konfiguriert, dass das System wieder in einen Zustand versetzt wird, in dem die Umgebung noch nicht konfiguriert ist. Wenn die Reset-Funktion verwendet wird, verwirft das System alle installierten Anwendungen und Einstellungen. Auch wenn es in einigen Situationen vorteilhaft sein kann, das System ohne Anwendungen und Einstellungen in einen Zustand zu versetzen, wird das System in einer professionellen Umgebung effektiv für den Endbenutzer unbrauchbar dargestellt.

Die Reset-Taste kann jedoch so konfiguriert werden, dass die Systemkonfiguration in einem Zustand wiederhergestellt wird, in dem Sie vom Endbenutzer zur Verwendung bereit ist. Führen Sie die Schritte unter [Bereitstellen von Funktionen zum Zurücksetzen von Push-Schaltflächen](https://msdn.microsoft.com/windows/hardware/commercialize/manufacture/desktop/deploy-push-button-reset-features) aus, um die Funktion zum Zurücksetzen des Push-Buttons für Ihre Geräte anzupassen.
