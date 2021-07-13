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
# <a name="surface-asset-tag-tool"></a><span data-ttu-id="c6669-103">Surface Asset Tag-Tool</span><span class="sxs-lookup"><span data-stu-id="c6669-103">Surface Asset Tag Tool</span></span>

<span data-ttu-id="c6669-104">Surface Asset Tag ist ein Befehlszeilenschnittstellen-Hilfsprogramm (CLI), mit dem Sie einen zugewiesenen Ressourcentagwert für Surface-Geräte anzeigen, zuweisen und ändern können.</span><span class="sxs-lookup"><span data-stu-id="c6669-104">Surface Asset Tag is a command line interface (CLI) utility that allows you to view, assign, and modify an assigned asset tag value for Surface devices.</span></span> <span data-ttu-id="c6669-105">Es funktioniert auf Surface Pro 3 und allen neueren Surface-Geräten.</span><span class="sxs-lookup"><span data-stu-id="c6669-105">It works on Surface Pro 3 and all newer Surface devices.</span></span>

## <a name="system-requirements"></a><span data-ttu-id="c6669-106">Systemanforderungen</span><span class="sxs-lookup"><span data-stu-id="c6669-106">System requirements</span></span>

- <span data-ttu-id="c6669-107">Surface Pro 3 oder höher</span><span class="sxs-lookup"><span data-stu-id="c6669-107">Surface Pro 3 or later</span></span>

- <span data-ttu-id="c6669-108">UEFI-Firmwareversion 3.9.150.0 oder höher</span><span class="sxs-lookup"><span data-stu-id="c6669-108">UEFI firmware version 3.9.150.0 or later</span></span>

## <a name="using-surface-asset-tag"></a><span data-ttu-id="c6669-109">Verwenden des Surface Asset-Tags</span><span class="sxs-lookup"><span data-stu-id="c6669-109">Using Surface Asset Tag</span></span>

<span data-ttu-id="c6669-110">So führen Sie das Surface Asset-Tag aus:</span><span class="sxs-lookup"><span data-stu-id="c6669-110">To run Surface Asset Tag:</span></span>

1. <span data-ttu-id="c6669-111">Laden Sie auf dem Surface-Gerät **surface Asset Tag.zip** aus dem Microsoft Download [Center](https://www.microsoft.com/download/details.aspx?id=46703)herunter, extrahieren Sie die ZIP-Datei, und speichern Sie AssetTag.exe im gewünschten Ordner (in diesem Beispiel C:\\assets).</span><span class="sxs-lookup"><span data-stu-id="c6669-111">On the Surface device, download **Surface Asset Tag.zip** from the [Microsoft Download  Center](https://www.microsoft.com/download/details.aspx?id=46703),  extract the zip file, and save AssetTag.exe in desired folder (in  this example, C:\\assets).</span></span>

    > [!NOTE]
    > <span data-ttu-id="c6669-112">Verwenden Sie für Surface Pro X die Anwendung mit dem Namen **AssetTag_x86** in der ZIP-Datei.</span><span class="sxs-lookup"><span data-stu-id="c6669-112">For Surface Pro X, use the application named **AssetTag_x86**  in the ZIP file.</span></span>

2. <span data-ttu-id="c6669-113">Öffnen Sie eine Befehlskonsole als Administrator, und führen Sie AssetTag.exe aus, und geben Sie den vollständigen Pfad zum Tool ein.</span><span class="sxs-lookup"><span data-stu-id="c6669-113">Open a command console as an Administrator and run AssetTag.exe, entering the full path to the tool.</span></span>

3. <span data-ttu-id="c6669-114">Starten Sie Surface neu.</span><span class="sxs-lookup"><span data-stu-id="c6669-114">Restart Surface.</span></span>

    > [!NOTE]
    > <span data-ttu-id="c6669-115">Nach dem Festlegen des Ressourcentags ist ein zweiter Neustart erforderlich, bevor er in WMI angezeigt wird.</span><span class="sxs-lookup"><span data-stu-id="c6669-115">After setting the asset tag, a second reboot is required before it appears in WMI.</span></span>

### <a name="asset-tag-tool-commands"></a><span data-ttu-id="c6669-116">Ressourcentag-Toolbefehle</span><span class="sxs-lookup"><span data-stu-id="c6669-116">Asset Tag tool commands</span></span>

<span data-ttu-id="c6669-117">In den folgenden Beispielen wird AssetTag.exe in einem Verzeichnis auf einem lokalen Computer (C:\Assets) gespeichert.</span><span class="sxs-lookup"><span data-stu-id="c6669-117">In the following examples, AssetTag.exe is saved in a directory on a local machine (C:\assets).</span></span>

<span data-ttu-id="c6669-118">Um das vorgeschlagene Asset-Tag abzurufen, führen Sie **AssetTag -g**aus:</span><span class="sxs-lookup"><span data-stu-id="c6669-118">To get the proposed asset tag, run **AssetTag -g**:</span></span>

```console
C:\assets\AssetTag.exe -g
```

<span data-ttu-id="c6669-119">Um das vorgeschlagene Asset-Tag zu löschen, führen Sie **AssetTag -s aus:**</span><span class="sxs-lookup"><span data-stu-id="c6669-119">To clear the proposed asset tag, run **AssetTag -s**:</span></span>

```console
C:\assets\AssetTag.exe -s
```

<span data-ttu-id="c6669-120">Um das vorgeschlagene Objekttag festzulegen, führen Sie **"AssetTag -s testassettag12" aus:**</span><span class="sxs-lookup"><span data-stu-id="c6669-120">To set the proposed asset tag, run **AssetTag -s testassettag12**:</span></span>

```
C:\assets\AssetTag.exe -s testassettag12
```

>[!NOTE]
><span data-ttu-id="c6669-121">Der Wert des Objekttags muss zwischen 1 und 36 Zeichen enthalten.</span><span class="sxs-lookup"><span data-stu-id="c6669-121">The asset tag value must contain between 1 and 36 characters.</span></span> <span data-ttu-id="c6669-122">Gültige Zeichen sind A-Z, a-z, 0-9, Punkt (.) und Bindestrich (-).</span><span class="sxs-lookup"><span data-stu-id="c6669-122">Valid characters include A-Z, a-z, 0-9, period (.) and hyphen (-).</span></span>

## <a name="managing-asset-tags"></a><span data-ttu-id="c6669-123">Verwalten von Ressourcentags</span><span class="sxs-lookup"><span data-stu-id="c6669-123">Managing asset tags</span></span>

<span data-ttu-id="c6669-124">You can view the existing asset tag in the UEFI settings under Device Information (**Control Panel > Recovery > Advanced Startup > Restart now**.)</span><span class="sxs-lookup"><span data-stu-id="c6669-124">You can view the existing asset tag in the UEFI settings under Device Information (**Control Panel > Recovery > Advanced Startup > Restart now**.)</span></span>

<span data-ttu-id="c6669-125">Die folgende Abbildung zeigt die Ergebnisse der Ausführung des Ressourcentag-Tools auf Surface Go.</span><span class="sxs-lookup"><span data-stu-id="c6669-125">The figure below shows the results of running the Asset Tag Tool on Surface Go.</span></span>

![Ergebnisse der Ausführung des Surface Asset Tag-Tools auf Surface Go.](images/assettag-fig1.png)

> **<span data-ttu-id="c6669-127&quot;>Abbildung1.</span><span class=&quot;sxs-lookup&quot;><span data-stu-id=&quot;c6669-127&quot;>Figure 1.</span></span>** <span data-ttu-id=&quot;c6669-128&quot;>Ergebnisse der Ausführung des Surface Asset Tag-Tools auf Surface Go</span><span class=&quot;sxs-lookup&quot;><span data-stu-id=&quot;c6669-128&quot;>Results of running Surface Asset Tag tool on Surface Go</span></span>

<span data-ttu-id=&quot;c6669-129&quot;>Alternativ können Sie WMI verwenden, um das vorhandene Objekttag auf einem Gerät abfragt:</span><span class=&quot;sxs-lookup&quot;><span data-stu-id=&quot;c6669-129&quot;>Alternately, you can use WMI to query the existing asset tag on a device:</span></span>

<span data-ttu-id=&quot;c6669-130&quot;>(Get-WmiObject -query &quot;Select \* from Win32_SystemEnclosure")</span><span class="sxs-lookup"><span data-stu-id="c6669-130">(Get-WmiObject -query "Select \* from Win32_SystemEnclosure")</span></span>

### <a name="example"></a><span data-ttu-id="c6669-131">Beispiel</span><span class="sxs-lookup"><span data-stu-id="c6669-131">Example</span></span>

```console
C:\Windows\System32> (Get-WmiObject -query "Select * from Win32_SystemEnclosure")
```
  
### <a name="using-powershell"></a><span data-ttu-id="c6669-132">Mithilfe von PowerShell</span><span class="sxs-lookup"><span data-stu-id="c6669-132">Using PowerShell</span></span>

<span data-ttu-id="c6669-133">Sie können das nachstehende Skript verwenden, um den vorgeschlagenen Wert abzurufen und Fehler zu interpretieren.</span><span class="sxs-lookup"><span data-stu-id="c6669-133">You can use the script below as a way of getting the proposed value and interpreting any errors.</span></span>

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
