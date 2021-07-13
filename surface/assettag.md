---
title: Surface Asset Tag-Tool
description: In diesem Thema wird die Verwendung des Surface Asset Tag-Tools erläutert.
ms.prod: w10
ms.mktglfcycl: manage
ms.localizationpriority: medium
ms.sitesec: library
author: coveminer
ms.author: greglin
ms.topic: article
ms.reviewer: carlol
ms.date: 06/29/2021
manager: laurawi
ms.openlocfilehash: b130f6b0bf52dc1c3a28231a2330cae51a5ef44a
ms.sourcegitcommit: d020d899e9c7e1eb0b85193ecb0a17a85bb39fe6
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/12/2021
ms.locfileid: "11643831"
---
# <a name="surface-asset-tag-tool"></a>Surface Asset Tag-Tool

Surface Asset Tag ist ein Befehlszeilenschnittstellen-Hilfsprogramm (CLI), mit dem Sie einen zugewiesenen Ressourcentagwert für Surface-Geräte anzeigen, zuweisen und ändern können. Es funktioniert auf Surface Pro 3 und allen neueren Surface-Geräten.

## <a name="system-requirements"></a>Systemanforderungen

- Surface Pro 3 oder höher

- UEFI-Firmwareversion 3.9.150.0 oder höher

## <a name="using-surface-asset-tag"></a>Verwenden des Surface Asset-Tags

So führen Sie das Surface Asset-Tag aus:

1. Laden Sie auf dem Surface-Gerät **surface Asset Tag.zip** aus dem Microsoft Download [Center](https://www.microsoft.com/download/details.aspx?id=46703)herunter, extrahieren Sie die ZIP-Datei, und speichern Sie AssetTag.exe im gewünschten Ordner (in diesem Beispiel C:\\assets).

    > [!NOTE]
    > Verwenden Sie für Surface Pro X die Anwendung mit dem Namen **AssetTag_x86** in der ZIP-Datei.

2. Öffnen Sie eine Befehlskonsole als Administrator, und führen Sie AssetTag.exe aus, und geben Sie den vollständigen Pfad zum Tool ein.

3. Starten Sie Surface neu.

    > [!NOTE]
    > Nach dem Festlegen des Ressourcentags ist ein zweiter Neustart erforderlich, bevor er in WMI angezeigt wird.

### <a name="asset-tag-tool-commands"></a>Ressourcentag-Toolbefehle

In den folgenden Beispielen wird AssetTag.exe in einem Verzeichnis auf einem lokalen Computer (C:\Assets) gespeichert.

Um das vorgeschlagene Asset-Tag abzurufen, führen Sie **AssetTag -g**aus:

```console
C:\assets\AssetTag.exe -g
```

Um das vorgeschlagene Asset-Tag zu löschen, führen Sie **AssetTag -s aus:**

```console
C:\assets\AssetTag.exe -s
```

Um das vorgeschlagene Objekttag festzulegen, führen Sie **"AssetTag -s testassettag12" aus:**

```
C:\assets\AssetTag.exe -s testassettag12
```

>[!NOTE]
>Der Wert des Objekttags muss zwischen 1 und 36 Zeichen enthalten. Gültige Zeichen sind A-Z, a-z, 0-9, Punkt (.) und Bindestrich (-).

## <a name="managing-asset-tags"></a>Verwalten von Ressourcentags

You can view the existing asset tag in the UEFI settings under Device Information (**Control Panel > Recovery > Advanced Startup > Restart now**.)

Die folgende Abbildung zeigt die Ergebnisse der Ausführung des Ressourcentag-Tools auf Surface Go.

![Ergebnisse der Ausführung des Surface Asset Tag-Tools auf Surface Go.](images/assettag-fig1.png)

> **Abbildung1.** Ergebnisse der Ausführung des Surface Asset Tag-Tools auf Surface Go

Alternativ können Sie WMI verwenden, um das vorhandene Objekttag auf einem Gerät abfragt:

(Get-WmiObject -query "Select * from Win32_SystemEnclosure")

### <a name="example"></a>Beispiel

```console
C:\Windows\System32> (Get-WmiObject -query "Select * from Win32_SystemEnclosure")
```
  
### <a name="using-powershell"></a>Mithilfe von PowerShell

Sie können das nachstehende Skript verwenden, um den vorgeschlagenen Wert abzurufen und Fehler zu interpretieren.

```powershell
AssetTag -g \> $asset\_tag 2\> $error\_message  
$asset\_tag\_return\_code = $LASTEXITCODE  
$asset\_tag = $asset\_tag.Trim("\`r\`n")

if ($asset\_tag\_return\_code -eq 0) {  
Write-Output ("Good Tag = " + $asset\_tag)  
} else {  
Write-Output (  
"Failure: Code = " + $asset\_tag\_return\_code +  
"Tag = " + $asset\_tag +  
"Message = " + $error\_message)

}
```
