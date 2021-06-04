---
title: DGM-Inventar-Tag-Tool
description: In diesem Thema wird die Verwendung des Surface-Asset-Tag-Tools erläutert.
ms.prod: w10
ms.mktglfcycl: manage
ms.localizationpriority: medium
ms.sitesec: library
author: coveminer
ms.author: greglin
ms.topic: article
ms.reviewer: hachidan
manager: laurawi
ms.openlocfilehash: ca6a71a6b864692953fcd96eb687c2752527c9f5
ms.sourcegitcommit: 109d1d7608ac4667564fa5369e8722e569b8ea36
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/27/2020
ms.locfileid: "10832578"
---
# DGM-Inventar-Tag-Tool

Surface-Ressourcen-Tag ist ein Befehlszeilen-Interface-Dienstprogramm, mit dem Sie einen zugewiesenen Ressourcen-Tag-Wert für Surface-Geräte anzeigen, zuweisen und ändern können. Es funktioniert auf Surface pro 3 und auf allen neueren Surface-Geräten.

##  <a name="system-requirements"></a>Systemanforderungen

- Surface pro 3 oder höher

- UEFI-Firmwareversion 3.9.150.0 oder höher

##  <a name="using-surface-asset-tag-"></a>Verwenden der Surface-Ressourcenkategorie 

So führen Sie eine DGM-Anlagen Kategorie aus:

1.  Laden Sie auf dem Surface-Gerät **Surface Asset Tag.zip** aus dem [Microsoft Download Center](https://www.microsoft.com/download/details.aspx?id=46703)herunter, extrahieren Sie die ZIP-Datei, und speichern Sie AssetTag.exe im gewünschten Ordner (in diesem Beispiel C:\\assets).

    > [!NOTE]
    > Verwenden Sie für Surface pro X die Anwendung mit dem Namen **AssetTag_x86** in der ZIP-Datei. 

2.  Öffnen Sie eine Befehlskonsole als Administrator, und führen Sie AssetTag.exe aus, und geben Sie den vollständigen Pfad zum Tool ein.

3.  Oberfläche neu starten

###  <a name="asset-tag-tool-commands"></a>Befehle für das Element-Tag-Tool   
In den folgenden Beispielen wird AssetTag.exe in einem Verzeichnis auf einem lokalen Computer (C:\assets) gespeichert. 

Führen Sie AssetTag-g aus, um die vorgeschlagene Inventar Kategorie zu erhalten.

**Beispiel**

   ```
 C:\assets\AssetTag.exe -g
  ```
 
 Führen Sie AssetTag-s aus, um die vorgeschlagene Ressourcenkategorie zu löschen.
 
 **Beispiel**
 
   ```
C:\assets\AssetTag.exe -s
  ```
Führen Sie AssetTag-s testassettag12 aus, um die vorgeschlagene Ressourcenkategorie einzurichten.

**Beispiel**

```
C:\assets\AssetTag.exe -s testassettag12
```

>[!NOTE]
>Der Wert für das Elementtag muss zwischen 1 und 36 Zeichen enthalten. Gültige Zeichen sind a-z, a-z, 0-9, Punkt (.) und Bindestrich (-).


##  <a name="managing-asset-tags"></a>Verwalten von Inventar Kategorien

Sie können die vorhandene Objektkategorie in den UEFI-Einstellungen unter Geräteinformationen anzeigen (**Systemsteuerung > Wiederherstellung > Advanced Startup > jetzt neu starten**.)

Die folgende Abbildung zeigt die Ergebnisse der Ausführung des Asset-Tag-Tools auf Surface go.

![Ergebnisse des laufenden Surface-Asset-Tag-Tools auf Surface go.
](images/assettag-fig1.png)

> **Abbildung1.** Ergebnisse des laufenden Surface-Asset-Tag-Tools auf Surface go

Alternativ können Sie mithilfe von WMI die vorhandene Objektkategorie auf einem Gerät Abfragen:

(Get-WMIObject-Query "Select * from Win32_SystemEnclosure")

**Beispiel**

   ```
C:\Windows\System32> (Get-WmiObject -query “Select * from Win32_SystemEnclosure”)
  ```
  
###  <a name="using-powershell"></a>Mithilfe von PowerShell

Mit dem folgenden Skript können Sie den vorgeschlagenen Wert abrufen und Fehler interpretieren.

 ```
AssetTag -g \> $asset\_tag 2\> $error\_message  
$asset\_tag\_return\_code = $LASTEXITCODE  
$asset\_tag = $asset\_tag.Trim(“\`r\`n”)

if ($asset\_tag\_return\_code -eq 0) {  
Write-Output (“Good Tag = ” + $asset\_tag)  
} else {  
Write-Output (  
“Failure: Code = ” + $asset\_tag\_return\_code +  
“Tag = ” + $asset\_tag +  
“Message = ” + $error\_message)

}
 ```
