---
title: Aktivieren von Wake on Power für Surface
ms.author: v-todmc
author: mccoybot
audience: ITPro
search.appverid:
- SPO160
- MET150
appliesto:
- Surface Book 3
- Surface Pro 7+
- Surface Pro 7
- Surface Laptop 3
- Surface Pro X
- Surface Laptop Go
ms.custom:
- CI 121602
ms.reviewer: hachidan
description: Beschreibt das Aktivieren und Deaktivieren von Wake on Power für Surface-Geräte.
keywords: update, deploy, driver, wol, wake-on-lan
ms.prod: w10
ms.mktglfcycl: manage
ms.pagetype: surface, devices
ms.sitesec: library
ms.localizationpriority: medium
ms.topic: article
manager: laurawi
ms.audience: itpro
ms.date: 01/15/2021
ms.openlocfilehash: 6ad359861f6af29c567bf0fbf26878ec15c7c642
ms.sourcegitcommit: 1053479c191fd10651d31a466fad1769fb0cd28b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/16/2021
ms.locfileid: "11271559"
---
# Wake-on-Power für Surface-Geräte

Surface-Geräte können ausgeschaltet werden, während Sie sich nicht am Schreibtisch befinden, oder sie können in den Ruhezustand versetzt werden, um die Akkulaufzeit zu sparen. Um die Verwaltbarkeit dieser Geräte zu verbessern, ermöglicht Wake on Power das automatische Starten kompatibler Surface-Geräte, wenn sie wieder mit der Stromversorgung verbunden werden. Zum Konfigurieren von Wake on Power können Sie den Surface Enterprise Management Mode (SEMM) entweder über den Surface UEFI Configurator oder den UEFI Manager verwenden.

Das Aktivierungsfeature ist auf den folgenden Geräten verfügbar:

- Surface Pro 7+
- Surface Book 3
- Surface Pro 7
- Surface Laptop 3
- Surface Laptop Go
- Surface Pro X 


## Übersicht und Voraussetzungen

Mit dem Surface -UEFI-Konfigurator können Sie einzelne UEFI-Einstellungen in einem Windows Installer-MSI-Paket für die Verteilung auf Zielgeräte speichern. 

> [!NOTE]
> In diesem Artikel wird davon ausgegangen, dass Sie mit der Verwendung von SEMM wissen. Weitere Informationen finden Sie in der [Dokumentation zum Surface Enterprise Management Mode (SEMM).](surface-enterprise-management-mode.md)

## So aktivieren Sie Wake on Power

1.  Laden Sie die neueste Version von [Surface UEFI Configurator herunter.](https://www.microsoft.com/download/confirmation.aspx?id=46703)
2.  Melden Sie sich als Administrator bei Ihrem Surface-Gerät an, öffnen Sie **den Surface UEFI-Konfigurator,** wählen Sie **"Surface Devices"** aus, und wählen Sie dann **"Weiter" aus.**

    :::image type="content" source="images/wake-on-power-for-surface/wake-on-power-for-surface-1.png" alt-text="Wählen Sie Surface-Geräte und "Weiter" aus.":::
3.  Wählen **Sie "Start"** und dann **"Erstellen"** unter **"Konfigurationspaket" aus.**

    :::image type="content" source="images/wake-on-power-for-surface/wake-on-power-for-surface-2.png" alt-text="Wählen Sie Konfigurationspaket erstellen aus.":::
4.  Wählen **Sie Zertifikatschutz**aus, und fügen Sie die ZERTIFIKAT-PFX-Datei hinzu. 
5. Geben Sie Ihr Kennwort ein, wählen **Sie "Weiter",** **fügen**Sie gegebenenfalls Den Kennwortschutz hinzu, und wählen Sie dann **"Weiter" aus.**
6.  Wählen Sie **auf der Seite "Wählen Sie aus,** welchen Surface-Typ Sie als Ziel verwenden möchten" ihre Zielgeräte aus. Wählen Sie beispielsweise Surface Pro **7 aus.**
7.  On the **Advanced Features** page, select Wake **on Power,** set the feature to **On**, and then select **Next**.

    :::image type="content" source="images/wake-on-power-for-surface/wake-on-power-for-surface-3.png" alt-text="Wählen Sie Aktivierung aktivieren aus, und legen Sie es auf "Ein" festgelegt."::: 
8.  Wählen Sie **auf der Seite "Erfolgreich"** die Option **"Ende" aus.**

    > [!NOTE]
    > Wenn Sie zum ersten Mal Einstellungen für Ihr Gerät bereitstellen, werden Sie aufgefordert, auch die letzten beiden Zeichen des Zertifikatfingerabdrucks ein. 
9.  Speichern Sie das MSI-Paket. 

## Anwenden des MSI-Pakets 

Sie können das MSI-Paket mithilfe von Softwareverteilungstools wie Microsoft Endpoint Configuration Manager auf Geräte in Ihrem Netzwerk anwenden. Dieses Verfahren umfasst Schritte zum Installieren des Pakets auf dem lokalen Computer. 

1.  Geben Sie an einer Eingabeaufforderung mit erhöhten Rechten den vollständigen Pfad der MSI-Datei ein, um das .msi-Paket auszuführen. 

    ```
    C:\SEMM\wake-on-power.msi 
    ```

2.  Wählen Sie **im Dialogfeld "Warnung"** die Option **"OK"** aus, oder deaktivieren Sie BitLocker.

    :::image type="content" source="images/wake-on-power-for-surface/wake-on-power-for-surface-4.png" alt-text="Wählen Sie OK aus, oder deaktivieren Sie BitLocker.":::
3.  Wählen Sie auf der Willkommensseite **"Weiter"** aus, um das Paket ausführen und die neu konfigurierte Einstellung für UEFI anzuwenden.

    :::image type="content" source="images/wake-on-power-for-surface/wake-on-power-for-surface-5.png" alt-text="Wählen Sie auf der Willkommensseite Weiter aus.":::
4.  Starten Sie Das Gerät neu. 

Wake on Power ist jetzt konfiguriert. Um die Einstellungen zu testen, schalten Sie Ihr Gerät aus, trennen Sie das Netzgerät, und verbinden Sie es erneut. Das Gerät sollte automatisch gestartet werden. 

## Verweise

Weitere Informationen finden Sie in den folgenden Artikeln. 

- [Surface Enterprise Management-Modus](surface-enterprise-management-mode.md)
- [Wake-on-LAN für Surface-Geräte](wake-on-lan-for-surface-devices.md)

Benötigen Sie weitere Hilfe? Wechseln Sie zur [Microsoft Community](https://answers.microsoft.com/).