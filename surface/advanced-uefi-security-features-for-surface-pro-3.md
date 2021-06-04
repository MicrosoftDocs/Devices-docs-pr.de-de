---
title: Erweiterte UEFI-Sicherheitsfeatures für Surface Pro 3 (Surface)
description: In diesem Artikel wird beschrieben, wie Sie das UEFI-Update v3.11.760.0 installieren und konfigurieren, um zusätzliche Sicherheitsoptionen für Surface Pro 3-Geräte zu aktivieren.
ms.assetid: 90F790C0-E5FC-4482-AD71-60589E3C9C93
ms.reviewer: ''
manager: laurawi
keywords: Sicherheit, Features, konfigurieren, Hardware, Gerät, benutzerdefiniert, Skript, Update
ms.localizationpriority: medium
ms.prod: w10
ms.mktglfcycl: manage
ms.pagetype: surface, devices, security
ms.sitesec: library
author: coveminer
ms.author: greglin
ms.topic: article
ms.openlocfilehash: 6a5c53c3e161bd4c49069a0665896762ce587618
ms.sourcegitcommit: e9190a6fe68b8a7cd9b024aea4be9f885f0de388
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/10/2020
ms.locfileid: "11163178"
---
# Erweiterte UEFI-Sicherheitsfeatures für Surface Pro 3


In diesem Artikel wird beschrieben, wie Sie das UEFI-Update v3.11.760.0 installieren und konfigurieren, um zusätzliche Sicherheitsoptionen für Surface Pro 3-Geräte zu aktivieren.

Das UEFI-Update v3.11.760.0 bietet zusätzliche Optionen zur präziseren Kontrolle über die Sicherheit von Surface-Geräten. So können Sie beispielsweise bestimmte Hardwaregeräte deaktivieren und das Starten von diesen Geräten verhindern. Nachdem das UEFI-Update auf einem Gerät installiert wurde, können Sie es manuell oder automatisch durch Ausführung eines Skripts konfigurieren.

##  <a name="manually-install-the-uefi-update"></a>Manuelle Installation des UEFI-Updates


Bevor Sie die erweiterten Sicherheitsfeatures des Surface-Geräts konfigurieren können, müssen Sie zunächst das UEFI-Update v3.11.760.0 installieren. Über Windows Update wird dieses Update automatisch installiert. Weitere Informationen zum Konfigurieren von Windows zur automatischen Aktualisierung über Windows Update finden Sie unter [Konfigurieren und Verwenden des Features „Automatische Updates“ in Windows](https://support.microsoft.com/kb/306525).

Zum Aktualisieren der UEFI auf Surface Pro 3 können Sie die Surface UEFI-Updates als Teil der Firmware und des Treiberpakets für Surface Pro 3 herunterladen und installieren. Diese Firmware- und Treiberpakete stehen auf der [Surface Pro 3-Seite](https://www.microsoft.com/download/details.aspx?id=38826) im Microsoft Download Center zur Verfügung. Weitere Informationen zu den Firmware- und Treiberpaketen finden Sie unter [Herunterladen der neuesten Firmware und Treiber für Surface-Geräte](https://technet.microsoft.com/itpro/surface/deploy-the-latest-firmware-and-drivers-for-surface-devices). Die Firmware- und Treiberpakete stehen sowohl als eigenständige Windows Installer-Datei (.msi) als auch als Archivdatei (.zip) zur Verfügung. Weitere Informationen zu diesen beiden Formaten sowie zum Aktualisieren ihrer Pakete mithilfe dieser Formate finden Sie unter [Verwalten von Treiber- und Firmwareupdates für Surface](https://technet.microsoft.com/itpro/surface/manage-surface-pro-3-firmware-updates).

##  <a name="manually-configure-additional-security-settings"></a>Manuelles Konfigurieren zusätzlicher Sicherheitseinstellungen


>[!NOTE]
>Auf einem Surface-Gerät können Sie das Firmwaresetup aufrufen, indem Sie das Gerät zunächst ausschalten, die **Lauter**-Taste gedrückt halten, und dann die **Ein/Aus**-Taste drücken und loslassen. Wenn das Gerät zu starten begonnen hat, lassen Sie die **Lauter**-Taste los.

Nachdem das UEFI-Update v3.11.760.0 auf einem Surface-Gerät installiert wurde, wird ein zusätzliches UEFI-Menü mit dem Namen **Advanced Device Security** verfügbar. Wenn Sie auf dieses Menü klicken, werden die folgenden Optionen angezeigt:

| Option         | Beschreibung                                                                                                                                                                          | Verfügbare Einstellungen (Standardeinstellungen fett formatiert) |
|----------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|---------------------------------------------|
| Netzwerkstart   | Aktiviert oder deaktiviert die Fähigkeit des Surface-Geräts, vom Netzwerk zu starten (PXE-Start).                                                                            | **Aktiviert**, nicht startbar                   |
| Side USB       | Aktiviert oder deaktiviert den seitlichen USB-Anschluss am Surface-Gerät. Zusätzlich kann der USB-Port aktiviert werden, aber das Starten über USB wird nicht zugelassen.                                                | **Aktiviert**, nicht startbar, deaktiviert         |
| Docking Port   | Aktiviert oder deaktiviert die Anschlüsse an der Surface-Dockingstation. Zusätzlich kann der Dockinganschluss aktiviert, aber das Starten über einen beliebigen USB- oder Ethernet-Anschluss an der Dockingstation blockiert werden. | **Aktiviert**, nicht startbar, deaktiviert         |
| Frontkamera   | Aktiviert oder deaktiviert die Kamera an der Vorderseite des Surface-Geräts.                                                                                                                   | **Aktiviert**, deaktiviert                       |
| Rückwärtige Kamera    | Aktiviert oder deaktiviert die Kamera an der Rückseite des Surface-Geräts.                                                                                                                    | **Aktiviert**, deaktiviert                       |
| On Board Audio | Aktiviert oder deaktiviert die Wiedergabe von Audioinhalten auf dem Surface-Gerät.                                                                                                                                     | **Aktiviert**, deaktiviert                       |
| microSD        | Aktiviert oder deaktiviert den MicroSD-Kartensteckplatz am Surface-Gerät.                                                                                                                          | **Aktiviert**, deaktiviert                       |
| WLAN           | Aktiviert oder deaktiviert den integrierten WLAN-Transceiver des Surface-Geräts. Dadurch wird auch Bluetooth deaktiviert.                                                                              | **Aktiviert**, deaktiviert                       |
| Bluetooth      | Aktiviert oder deaktiviert den integrierten Bluetooth-Transceiver des Surface-Geräts.                                                                                                        | **Aktiviert**, deaktiviert                       |

 

##  <a name="automate-additional-security-settings"></a>Automatisieren zusätzlicher Sicherheitseinstellungen


Mithilfe der [Surface Pro 3 Firmware Tools (476 KB)](https://go.microsoft.com/fwlink/p/?LinkID=618038) aus dem Microsoft Download Center können IT-Experten mit Administratorrechten die Konfiguration der UEFI-Einstellungen automatisieren. Diese Tools installieren eine .NET-Assembly, die über eine benutzerdefinierte Anwendung oder ein Skript aufgerufen werden kann.

**Voraussetzungen**

-   Die folgenden Beispielskripts nutzen die oben erwähnte Erweiterung und nehmen daher an, dass das Tool auf dem Gerät installiert wurde, das verwaltet wird.
-   Die Skripts müssen mit Administratorrechten ausgeführt werden.
-   Der Windows PowerShell-Befehl [**Set-ExecutionPolicy Unrestricted**](https://technet.microsoft.com/library/ee176961.aspx) muss vor der Ausführung von Beispielskripts aufgerufen werden, wenn diese nicht digital signiert sind.

**Beispielskripts**

> [!NOTE]
> Das in den folgenden Beispielskripts verwendete UEFI-Kennwort wird als Klartext angezeigt. Wir empfehlen dringend, die Skripts an einem geschützten Speicherort abzulegen und sie in einer kontrollierten Umgebung auszuführen.


Alle konfigurierbaren Optionen anzeigen:

```powershell
# Load the extension 
[System.Reflection.Assembly]::Load("SurfaceUefiManager, Version=1.0.5483.22783, Culture=neutral, PublicKeyToken=20606f4b5276c705")  
 
# Get the collection of all configurable settings 
$uefiOptions = [Microsoft.Surface.FirmwareOption]::All() 
 
foreach ($uefiOption in $uefiOptions) 
{ 
    Write-Host "Name:" $uefiOption.Name 
    Write-Host " Description =" $uefiOption.Description 
    Write-Host " Current Value =" $uefiOption.CurrentValue 
    Write-Host " Default Value =" $uefiOption.DefaultValue 
    Write-Host " Proposed Value =" $uefiOption.ProposedValue 
     
    # This gives usage and validation information 
    Write-Host " Allowed Values =" $uefiOption.FriendlyRegEx 
    Write-Host " Regular Expression =" $uefiOption.RegEx 
     
    Write-Host 
}
```

UEFI-Kennwort festlegen oder ändern:

```powershell
# Load the extension 
[System.Reflection.Assembly]::Load("SurfaceUefiManager, Version=1.0.5483.22783, Culture=neutral, PublicKeyToken=20606f4b5276c705")  
 
# Must supply UEFI administrator Password if set 
# If it is not currently set this is ignored 
[Microsoft.Surface.FirmwareOption]::Unlock("1234") 
 
$Password = [Microsoft.Surface.FirmwareOption]::Find("Password") 
 
# Set New value to 12345 
$Password.ProposedValue = "12345"
```

Status der vorgeschlagenen Änderungen prüfen:

```powershell
# Load the extension 
[System.Reflection.Assembly]::Load("SurfaceUefiManager, Version=1.0.5483.22783, Culture=neutral, PublicKeyToken=20606f4b5276c705")  
 
# Check update status 
$updateStatus = [Microsoft.Surface.FirmwareOption]::UpdateStatus 
$updateIteration = [Microsoft.Surface.FirmwareOption]::UpdateIteration 
Write-Host "Last Update Status =" $updateStatus 
Write-Host "Last Update Iteration =" $updateIteration 
 
# Get the individual results for the last proposed update 
# If the device has never had an update attempt this will be an empty list 
$details = [Microsoft.Surface.FirmwareOption]::UpdateStatusDetails 
Write-Host $details.Count "Settings were proposed" 
if ($details.Count -gt 0) 
{ 
    Write-Host "Result Details" 
    foreach ($detail in $details.GetEnumerator()) 
    { 
        Write-Host " " $detail.Key "=" $detail.Value 
    } 
}
```

UEFI-Standardwerte wiederherstellen:

```powershell
# Load the extension 
[System.Reflection.Assembly]::Load("SurfaceUefiManager, Version=1.0.5483.22783, Culture=neutral, PublicKeyToken=20606f4b5276c705")  
 
# Must supply UEFI administrator Password if set 
# If it is not currently set this is ignored 
[Microsoft.Surface.FirmwareOption]::Unlock("1234") 
 
# Get the collection of all configurable settings 
$uefiOptions = [Microsoft.Surface.FirmwareOption]::All() 
 
# Reset all options to the factory default 
foreach ($uefiOption in $uefiOptions) 
{ 
    $uefiOption.ProposedValue = $uefiOption.DefaultValue 
}
```

Interpretation des Statuscodes

-   00 - Das vorgeschlagene Update war erfolgreich.
-   02 - Einer der vorgeschlagenen Werte besaß einen ungültigen Wert.
-   03 - Ein Satz vorgeschlagener Werte wurde nicht erkannt.
-   0F - Das Kennwort zum Entsperren stimmt nicht mit dem aktuell festgelegten Kennwort überein.

 
