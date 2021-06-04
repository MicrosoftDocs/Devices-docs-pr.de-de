---
title: Einstellung für den Akkugrenzwert (Surface)
description: Der Akkugrenzwert ist eine UEFI-Einstellung, die ändert, wie der Akku des Surface-Geräts aufgeladen wird und die Lebensdauer verlängern kann.
ms.prod: w10
ms.mktglfcycl: manage
ms.pagetype: surface, devices
ms.sitesec: library
author: coveminer
ms.reviewer: jesko
ms.author: greglin
ms.topic: article
ms.localizationpriority: medium
manager: laurawi
audience: itpro
ms.date: 1/15/2021
ms.openlocfilehash: 8ce1dcfc621a547aca9ca1db322f3ed2ce082728
ms.sourcegitcommit: 1b86286bd13b13749ddbf454ae78d9a24fec44ee
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/15/2021
ms.locfileid: "11271142"
---
# Einstellungen für Akkulimit

Die Option "Akkulimit" ist eine UEFI-Einstellung, die ändert, wie der Akku des Surface-Geräts aufgeladen wird und die Lebensdauer verlängern kann. Diese Einstellung wird in Fällen empfohlen, in denen das Gerät ständig an die Stromversorgung angeschlossen ist, z. B. wenn Geräte in Kiosklösungen integriert sind.  

##  <a name="how-battery-limit-works"></a>Funktionsweise des Akkugrenzwerts

Wenn Sie das Gerät auf "Akkulimit" festlegen, wird das Protokoll zum Aufladen des Geräteakku geändert. Wenn der Akkugrenzwert aktiviert ist, ist der Akkustand auf 50 % der maximalen Kapazität beschränkt. Die in Windows gemeldete Gebührenstufe spiegelt diesen Grenzwert wider. Daher wird gezeigt, dass der Akku bis zu 50 % aufgeladen wird und nicht über diesen Grenzwert hinaus aufgeladen wird. Wenn Sie den Akkugrenzwert aktivieren, während das Gerät über 50 % aufgeladen ist, zeigt das Symbol "Akku" an, dass das Gerät eingesteckt ist, aber entladen wird, bis das Gerät 50 % seiner maximalen Ladekapazität erreicht.  

##  <a name="supported-devices"></a>Unterstützte Geräte

Die Einstellung "Battery Limit UEFI" ist in die neuesten Surface-Geräte, einschließlich Surface Pro 7+, Surface Pro 7 und Surface Laptop 3, integrierte. Frühere Geräte erfordern ein [Surface UEFI-Firmwareupdate,](manage-surface-driver-and-firmware-updates.md)das über Windows Update oder die MSI-Treiber- und Firmwarepakete auf der [Surface Support-Website verfügbar ist.](https://support.microsoft.com/help/4023482/surface-download-drivers-and-firmware-for-surface) Aktivieren [Sie "Akkulimit" für Surface-Geräte,](https://support.microsoft.com/help/4464941) die für die spezifische Surface -UEFI-Version, die für jedes unterstützte Gerät erforderlich ist, über einen längeren Zeitraum angeschlossen werden müssen. 

##  <a name="enabling-battery-limit-in-surface-uefi-(surface-pro-4-and-later)"></a>Aktivieren des Akkugrenzwerts auf Surface UEFI (Surface Pro 4 und höher)

Die Einstellung für den Surface -UEFI-Akkugrenzwert kann durch Starten auf Surface UEFI konfiguriert werden (**Ein- und** Aufladen beim Einschalten des Geräts). Wählen **Sie die Startkonfiguration**aus, und schalten Sie dann unter **"Erweiterte**Optionen" den Akkugrenzmodus aktivieren **auf** **"Ein" um.**  

![Erweiterte Optionen für den Akkugrenzwert](images/enable-bl.png) 

##  <a name="enabling-battery-limit-on-surface-go-and-surface-go-2"></a>Aktivieren des Akkulimits auf Surface Go und Surface Go 2
Die Einstellung "Surface Battery Limit" kann durch Starten von Surface UEFI **(Power + Vol Up** beim Einschalten des Geräts) konfiguriert werden. Wählen **Sie die Startkonfiguration**aus, und verschieben Sie dann unter **Kioskmodus**den Schieberegler nach rechts, um den Akkugrenzwert auf **"Aktiviert" festzulegen.**  

![Akkugrenzwert des Kioskmodus auf Surface Go](images/go-batterylimit.png) 

##  <a name="enabling-battery-limit-in-surface-uefi-(surface-pro-3)"></a>Aktivieren des Akkugrenzwerts auf Surface UEFI (Surface Pro 3)

Die Einstellung für den Surface -UEFI-Akkugrenzwert kann durch Starten auf Surface UEFI konfiguriert werden (**Ein- und** Aufladen beim Einschalten des Geräts). Wählen **Sie "Kioskmodus",** **"Akkulimit"** und dann "Aktiviert" **aus.**

![Screenshot der erweiterten Optionen](images/enable-bl-sp3.png) 

![Erweiterte Optionen](images/enable-bl-sp3-2.png) 

##  <a name="enabling-battery-limit-using-surface-enterprise-management-mode-(semm)-or-surface-pro-3-firmware-powershell-scripts"></a>Aktivieren des Akkulimits mithilfe von Surface Enterprise Management Mode (SEMM) oder Surface Pro 3 Firmware-PowerShell-Skripts

Der Surface -UEFI-Akkugrenzwert ist auch für die Konfiguration über die folgenden Methoden verfügbar:

- Surface Pro 4 und höher 
    - [Microsoft Surface UEFI Configurator](https://docs.microsoft.com/surface/surface-enterprise-management-mode)  
    - Surface UEFI Manager –Powershell-Skripts (SEMM_Powershell.zip) in den [Surface Tools für IT-Downloads](https://www.microsoft.com/download/details.aspx?id=46703)
- Surface Pro 3 
    - [SP3_Firmware_Powershell_Scripts.zip](https://www.microsoft.com/download/details.aspx?id=46703)

###  <a name="using-microsoft-surface-uefi-configurator"></a>Verwenden Microsoft Surface UEFI Configurator

Um den Akkugrenzmodus zu konfigurieren, legen Sie die Einstellung "Außerkraftsetzungen für **Kiosk"** auf der Konfigurationsseite "Erweiterte **Einstellungen"** in SEMM (Surface Pro 4 und höher) ein.

![Screenshot der erweiterten Einstellungen](images/semm-bl.png)

###  <a name="using-surface-uefi-manager-powershell-scripts"></a>Verwenden von Surface UEFI Manager -PowerShell-Skripts

Die Funktion für den Akkugrenzwert wird über die folgende Einstellung gesteuert:  

`407 = Battery Profile`

**Beschreibung:** Aktives Verwaltungsschema für das Akkunutzungsmuster

**Standard:**  `0` 

Legen Sie diese Option `1` so ein, dass der Akkugrenzwert aktiviert wird.

###  <a name="using-surface-pro-3-firmware-tools"></a>Verwenden Surface Pro 3 Firmwaretools

Die Funktion für den Akkugrenzwert wird über die folgende Einstellung gesteuert:  

**Name**: BatteryLimitEnable

**Beschreibung**: BatteryLimit

**Aktueller Wert:**  `0` 

**Standardwert:** `0`

**Vorgeschlagener Wert:** `0` 

Legen Sie diese Option `1` so ein, dass der Akkugrenzwert aktiviert wird.

>[!NOTE]
>Um diese Einstellung zu konfigurieren, müssen Sie [SP3_Firmware_Powershell_Scripts.zip](https://www.microsoft.com/download/details.aspx?id=46703). 

