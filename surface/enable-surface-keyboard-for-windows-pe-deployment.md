---
title: So aktivieren Sie die Surface Laptop-Tastatur während der MDT-Bereitstellung
description: Wenn Sie MDT zum Bereitstellen von Windows 10 auf Surface-Laptops verwenden, müssen Sie Tastaturtreiber importieren, die in der Windows PE-Umgebung verwendet werden.
keywords: Windows 10 Surface, automatisieren, anpassen, mdt
ms.prod: w10
ms.mktglfcycl: deploy
ms.pagetype: surface
ms.sitesec: library
author: coveminer
ms.author: v-tea
ms.topic: article
ms.reviewer: carlol
ms.localizationpriority: medium
ms.audience: itpro
manager: jarrettr
ms.date: 06/21/2021
appliesto:
- Surface Laptop (1st Gen)
- Surface Laptop 2
- Surface Laptop 3
- Surface Laptop 4
ms.openlocfilehash: c02837b0cfda72c6f2a447b99ff4c94a027bb29c
ms.sourcegitcommit: 267e12897efd9d11f8c7303eaf780632741cfe77
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/22/2021
ms.locfileid: "11613864"
---
# <a name="how-to-enable-the-surface-laptop-keyboard-during-mdt-deployment"></a>So aktivieren Sie die Surface Laptop-Tastatur während der MDT-Bereitstellung

Dieser Artikel befasst sich mit einem Bereitstellungsansatz, der das Microsoft Deployment Toolkit (MDT) verwendet. Sie können diese Informationen auch auf andere Bereitstellungsmethoden anwenden. Auf den meisten Surface-Geräten sollte die Tastatur während der Lite Touch-Installation (LTI) funktionieren. Surface Laptop erfordert jedoch einige zusätzliche Treiber, um die Tastatur zu aktivieren. Für geräte Surface Laptop (1. Generation) und Surface Laptop 2 müssen Sie die Ordnerstruktur und Auswahlprofile vorbereiten, mit denen Sie Tastaturtreiber für die Verwendung während der Phase Windows Preinstallation Environment (Windows PE) von LTI angeben können. Weitere Informationen zu dieser Ordnerstruktur finden Sie unter [Deploy a Windows 10 image using MDT: Step 5: Prepare the drivers repository](/windows/deployment/deploy-windows-mdt/deploy-a-windows-10-image-using-mdt?redirectedfrom=MSDN#step-5-prepare-the-drivers-repository).

> [!TIP]
> Wenn Sie Tastaturtreiber für Surface Laptop 2 und Surface Laptop 3 in derselben Windows PE-Startinstanz verwenden, müssen Sie die Firmware möglicherweise manuell zurücksetzen, wenn die Tastatur oder das Touchpad in Windows PE nicht funktionieren:
>
> - Halten Sie den Netzschalter 30 Sekunden lang gedrückt. Wenn Sie mit einer Stromversorgungseinheit (Power Supply Unit, PSU) verbunden sind, drücken und halten Sie den Netzschalter gedrückt, bis das Licht am Ende des PSU-Kabels kurz ausgeschaltet wird, bevor Sie wieder einschalten.

> [!IMPORTANT]
> Wenn Sie ein Windows 10-Image für eine Surface Laptop bereitstellen, für die Windows 10 im S-Modus vorinstalliert ist, lesen Sie KB [4032347, Probleme bei der Bereitstellung von Windows auf Surface-Geräten mit vorinstalliertem Windows 10 im S-Modus.](https://support.microsoft.com/help/4032347/surface-preinstall-windows10-s-mode-issues)

## <a name="add-keyboard-drivers-to-the-selection-profile"></a>Hinzufügen von Tastaturtreibern zum Auswahlprofil

1. Laden Sie die neueste Surface Laptop .msi-Datei von den entsprechenden Speicherorten herunter:
    - [Treiber und Firmware für Surface Laptop (1. Generation)](https://www.microsoft.com/download/details.aspx?id=55489)
    - [Surface Laptop 2 Treiber und Firmware](https://www.microsoft.com/download/details.aspx?id=57515)
    - [Surface Laptop 3 mit Intel-Prozessortreibern und Firmware](https://www.microsoft.com/download/details.aspx?id=100429)
    - [Surface Laptop 4 mit Intel Prozessortreibern und Firmware](https://www.microsoft.com/download/102924)
    - [Surface Laptop 4 mit AMD-Prozessortreibern und Firmware](https://www.microsoft.com/download/102923)
2. Extrahieren Sie den Inhalt der Surface Laptop .msi-Datei in einen Ordner, den Sie leicht finden können (z. B. c:\surface_laptop_drivers). Um den Inhalt zu extrahieren, öffnen Sie ein Eingabeaufforderungsfenster mit erhöhten Rechten, und führen Sie den Befehl aus dem folgenden Beispiel aus:

   ```cmd
   Msiexec.exe /a SurfaceLaptop_Win10_15063_1703008_1.msi targetdir=c:\surface_laptop_drivers /qn
   ```

3. Öffnen Sie die Deployment Workbench, erweitern Sie den Knoten **"Deployment Shares"** und Ihre Bereitstellungsfreigabe, und navigieren Sie dann zum Ordner **"WindowsPEX64".**
4. Klicken Sie mit der rechten Maustaste auf den **Ordner "WindowsPEX64",** und wählen Sie **"Treiber importieren" aus.**
5. Folgen Sie den Anweisungen im Treiberimport-Assistenten, um die Treiberordner in den WindowsPEX64-Ordner zu importieren.

 > [!NOTE]
 > Überprüfen Sie das heruntergeladene .msi-Paket, um das Format und die Verzeichnisstruktur zu ermitteln.  Die Verzeichnisstruktur beginnt entweder mit SurfacePlatformInstaller (ältere .msi-Dateien) oder SurfaceUpdate (neuere .msi-Dateien), je nachdem, wann die .msi Datei freigegeben wurde.

## <a name="import-drivers-for-surface-devices"></a>Importieren von Treibern für Surface-Geräte

Importieren Sie die folgenden Ordner nach Bedarf für Ihr Surface Laptop Gerät.  

| Gerät                                | Importieren von Ordnern                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                 | Weitere Informationen                                                                                                                                                                                                                                                                                                                                                                                                                            |
| ------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Surface Laptop 4 mit Intel-Prozessor | TglSerial<br>IntelPreciseTouch<br>SurfaceEthernetAdapter<br>SurfaceBattery<br>SurfaceHidMini<br>SurfaceHotPlug<br>SurfaceSerialHub<br>SurfaceTconDriver<br>surfacetimealarmacpifilter<br>surfacevirtualfunctionenum<br>TglChipset<br>ManagementEngine                                                                                                                                                                                                                                                                                                                          |n.a.                                                                                                                                                                                                                                                                                                                                                                                                                                             |
| Surface Laptop 4 mit AMD-Prozessor   | U0361415<br>AMDfendr<br>AMDGpio2<br>AMDI2c<br>AMDLpcFilterDriverAMDMicroPEP<br>AMDPsp<br>AMDSmf<br>AMDSpi<br>AMDUart<br>SurfaceEthernetAdapter<br>Smbus<br>SurfaceBattery<br>SurfaceButton<br>SurfaceDigitizerHidSpiExtnPackage<br>SurfaceHIDFriendlyNames<br>SurfaceHidMini<br>SurfaceHotPlug<br>SurfaceOemPanel<br>SurfacePowerMeter<br>SurfacePowerTrackerCore<br>SurfaceSerialHub<br>SurfaceSMFClient<br>SurfaceSmfDisplayClient<br>SurfaceSystemManagementFramework<br>SurfaceTconDriver<br>SurfacePolicy<br>Surfacetimealarmacpifilter<br>SurfaceUcmUcsiHidClient |n.a.                                                                                                                                                                                                                                                                                                                                                                                                                                             |
| Surface Laptop 3 mit Intel-Prozessor | SurfaceUpdate\SerialIOGPIO<br>SurfaceUpdate\SerialIOI2C<br>SurfaceUpdate\SerialIOSPI<br>SurfaceUpdate\SerialIOUART<br>SurfaceUpdate\SurfaceHidMini<br>SurfaceUpdate\SurfaceSerialHub<br>SurfaceUpdate\SurfaceHotPlug<br>SurfaceUpdate\Itouch                                                                                                                                                                                                                                                                                                                                   | Durch das Importieren der folgenden Ordner werden vollständige Tastatur-, Trackpad- und Touchfunktionen in PE aktiviert:<br><br>SerialIOGPIO<br>SerialIOI2C<br>SerialIOSPI<br>SerialIOUART<br>Itouch<br>Chipsatz<br>Chipsatz-LPSS<br>ChipsatzNorthpeak<br>ManagementEngine<br>SurfaceAcpiNotify<br>SurfaceBattery<br>SurfaceDockIntegration<br>SurfaceHidMini<br>SurfaceHotPlug<br>SurfaceIntegration<br>SurfaceSerialHub<br>SurfaceService<br>SurfaceStorageFwUpdat |
| Surface Laptop 2                      | SurfacePlatformInstaller\Drivers\System\GPIO<br>SurfacePlatformInstaller\Drivers\System\SurfaceHIDMiniDriver<br>SurfacePlatformInstaller\Drivers\System\SurfaceSerialHubDriver<br>SurfacePlatformInstaller\Drivers\System\I2C<br>SurfacePlatformInstaller\Drivers\System\SPI<br>SurfacePlatformInstaller\Drivers\System\UART<br>SurfacePlatformInstaller\Drivers\System\PreciseTouch                                                                                                                                                                                           | Verwenden Sie für neuere .msi Dateien, die mit "SurfaceUpdate" beginnen, Folgendes:<br>SurfaceUpdate\SerialIOGPIO<br>SurfaceUpdate\serialioi2c<br>SurfaceUpdate\SerialIOSPI<br>SurfaceUpdate\SerialIOUART<br>SurfaceUpdate\SurfaceHidMini<br>SurfaceUpdate\SurfaceSerialHub<br>SurfaceUpdate\Itouch                                                                                                                                                                    |
| Surface Laptop (1. Generation)              | SurfacePlatformInstaller\Drivers\System\GPIO<br>SurfacePlatformInstaller\Drivers\System\SurfaceHidMiniDriver<br>SurfacePlatformInstaller\Drivers\System\SurfaceSerialHubDriver<br>SurfacePlatformInstaller\Drivers\System\PreciseTouch                                                                                                                                                                                                                                                                                                                                         | Verwenden Sie für neuere .msi Dateien, die mit "SurfaceUpdate" beginnen, Folgendes:<br>SurfaceUpdate\SerialIOGPIO<br>SurfaceUpdate\SurfaceHidMiniDriver<br>SurfaceUpdate\SurfaceSerialHubDriver<br>SurfaceUpdate\Itouch                                                                                                                                                                                                                                                |

  > [!TIP]
  > Überprüfen Sie das heruntergeladene .msi-Paket, um das Format und die Verzeichnisstruktur zu ermitteln.  Die Verzeichnisstruktur beginnt entweder mit SurfacePlatformInstaller (ältere .msi-Dateien) oder SurfaceUpdate (Neuere .msi-Dateien), je nachdem, wann die .msi veröffentlicht wurde.

## <a name="verify-imported-drivers--configure-windows-pe-properties"></a>Überprüfen importierter Treiber & Konfigurieren Windows PE-Eigenschaften

1. Stellen Sie sicher, dass der WindowsPEX64-Ordner jetzt die importierten Treiber enthält, wie in der folgenden Abbildung dargestellt:

   ![Abbildung der neu importierten Treiber im WindowsPEX64-Ordner der Deployment Workbench](./images/surface-laptop-keyboard-2.png)
1. Konfigurieren Sie ein Auswahlprofil, das den WindowsPEX64-Ordner verwendet, wie in der folgenden Abbildung dargestellt:

   ![Abbildung des WindowsPEX64-Ordners, der als Teil eines Auswahlprofils ausgewählt wurde](./images/surface-laptop-keyboard-3.png)
1. Konfigurieren Sie die Windows PE-Eigenschaften der MDT-Bereitstellungsfreigabe wie folgt für die Verwendung des neuen Auswahlprofils:
    - Wählen Sie für **"Plattform"** **x64**aus.
    - Wählen Sie für das **Auswahlprofil**das neue Profil aus.
    - Wählen Sie **"Alle Treiber aus dem Auswahlprofil einschließen" aus.**

    ![Abbildung der Windows PE-Eigenschaften der MDT-Bereitstellungsfreigabe](./images/surface-laptop-keyboard-4.png)
4. Stellen Sie sicher, dass Sie die verbleibenden Surface Laptop Treiber mithilfe eines Auswahlprofils oder einer **DriverGroup001-Variablen** konfiguriert haben.
    - Für Surface Laptop (1. Generation) ist das Modell **Surface Laptop.** Die verbleibenden Surface Laptop Treiber sollten sich im Ordner "\MDT Deployment Share\Out-of-Box Drivers\Windows10\X64\Surface Laptop" befinden, wie in der folgenden Abbildung dargestellt.
    - Für Surface Laptop 2 ist das Modell **Surface Laptop 2.** Die verbleibenden Surface Laptop Treiber sollten sich im Ordner "\MDT Deployment Share\Out-of-Box Drivers\Windows10\X64\Surface Laptop 2" befinden.
    - Für Surface Laptop 3 mit Intel-Prozessor ist das Modell Surface Laptop 3. Die verbleibenden Surface Laptop Treiber befinden sich im Ordner "\MDT Deployment Share\Out-of-Box Drivers\Windows10\X64\Surface Laptop 3".

    ![Abbildung der regulären Treiber für Surface Laptop (1. Generation) im Ordner Surface Laptop der Deployment Workbench](./images/surface-laptop-keyboard-5.png)

Nachdem Sie die MDT-Bereitstellungsfreigabe für die Verwendung des neuen Auswahlprofils und der zugehörigen Einstellungen konfiguriert haben, setzen Sie den Bereitstellungsprozess wie unter ["Bereitstellen eines Windows 10 images mit MDT: Schritt 6: Erstellen der Bereitstellungstasksequenz"](/deployment/deploy-windows-mdt/deploy-a-windows-10-image-using-mdt#step-6-create-the-deployment-task-sequence)beschrieben fort.
