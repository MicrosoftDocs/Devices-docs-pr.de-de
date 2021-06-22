---
title: Wake-On-LAN für Surface-Geräte
description: Erfahren Sie, wie Sie Wake On LAN zum Remotereaktivieren von Geräten verwenden können, um Verwaltungsaufgaben automatisch auszuführen.
keywords: update, deploy, driver, doppelklicken, wake-on-lan
ms.prod: w10
ms.mktglfcycl: manage
ms.pagetype: surface, devices
ms.sitesec: library
ms.localizationpriority: medium
author: coveminer
ms.author: greglin
ms.topic: article
ms.reviewer: jesko
manager: laurawi
ms.audience: itpro
ms.date: 6/04/2021
ms.openlocfilehash: 83989461ca557d27740252149418056688774d3f
ms.sourcegitcommit: 267e12897efd9d11f8c7303eaf780632741cfe77
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/22/2021
ms.locfileid: "11613799"
---
# <a name="wake-on-lan-for-surface-devices"></a><span data-ttu-id="fc2d9-104">Wake-On-LAN für Surface-Geräte</span><span class="sxs-lookup"><span data-stu-id="fc2d9-104">Wake On LAN for Surface devices</span></span>

<span data-ttu-id="fc2d9-105">Um Geräte vollständig auf dem neuesten Stand zu halten, müssen IT-Administratoren In der Lage sein, Geräte zu verwalten, wenn sie nicht verwendet werden, in der Regel während der Nachtwartungsfenster.</span><span class="sxs-lookup"><span data-stu-id="fc2d9-105">To keep devices fully up to date, IT admins need to be able to manage devices when they’re not in use, typically during nightly maintenance windows.</span></span> <span data-ttu-id="fc2d9-106">Wake on LAN (MAUSTASTE) ermöglicht Administratoren das Remotereaktivieren von Geräten und das automatische Ausführen von Verwaltungsaufgaben mit Microsoft Endpoint Manager- oder Drittanbieterlösungen.</span><span class="sxs-lookup"><span data-stu-id="fc2d9-106">Wake on LAN (WOL) enables admins to remotely wake up devices and automatically perform management tasks with Microsoft Endpoint Manager or third-party solutions.</span></span>

## <a name="requirements"></a><span data-ttu-id="fc2d9-107">Anforderungen</span><span class="sxs-lookup"><span data-stu-id="fc2d9-107">Requirements</span></span>

<span data-ttu-id="fc2d9-108">Geräte müssen an die Stromversorgung angeschlossen sein und über eine kabelgebundene Verbindung mit einem der folgenden kompatiblen Ethernet-Adapter verfügen:</span><span class="sxs-lookup"><span data-stu-id="fc2d9-108">Devices must be connected to AC power and have a wired connection with one of the following compatible Ethernet adapters:</span></span>

- <span data-ttu-id="fc2d9-109">Surface USB 3.0-Ethernet-Adapter für Ethernet-Ethernet</span><span class="sxs-lookup"><span data-stu-id="fc2d9-109">Surface USB 3.0 Gigabit Ethernet Adapter</span></span>
- <span data-ttu-id="fc2d9-110">Surface Ethernet-Adapter</span><span class="sxs-lookup"><span data-stu-id="fc2d9-110">Surface Ethernet Adapter</span></span>
- <span data-ttu-id="fc2d9-111">Surface USB-C zu Ethernet und USB-Adapter</span><span class="sxs-lookup"><span data-stu-id="fc2d9-111">Surface USB-C to Ethernet and USB Adapter</span></span>
- <span data-ttu-id="fc2d9-112">Microsoft USB-C-Reiseadapter-Hub</span><span class="sxs-lookup"><span data-stu-id="fc2d9-112">Microsoft USB-C Travel Adapter Hub</span></span>
- <span data-ttu-id="fc2d9-113">Surface Dock</span><span class="sxs-lookup"><span data-stu-id="fc2d9-113">Surface Dock</span></span>
- <span data-ttu-id="fc2d9-114">Surface Dock 2</span><span class="sxs-lookup"><span data-stu-id="fc2d9-114">Surface Dock 2</span></span>

> [!NOTE]
> <span data-ttu-id="fc2d9-115">Surface Dock 2 bietet die beste Unterstützung für Wake on LAN, ohne dass eine zusätzliche IT-Konfiguration erforderlich ist.</span><span class="sxs-lookup"><span data-stu-id="fc2d9-115">Surface Dock 2 provides the best support for Wake on LAN without the need for any additional IT configuration.</span></span> <span data-ttu-id="fc2d9-116">Weitere Informationen finden Sie unter ["Wake on LAN" für Surface Dock 2.](wake-on-lan-surface-dock2.md)</span><span class="sxs-lookup"><span data-stu-id="fc2d9-116">To learn more, see [Wake on LAN for Surface Dock 2](wake-on-lan-surface-dock2.md)</span></span>

## <a name="how-it-works"></a><span data-ttu-id="fc2d9-117">Funktionsweise</span><span class="sxs-lookup"><span data-stu-id="fc2d9-117">How it works</span></span>

<span data-ttu-id="fc2d9-118">Wenn Surface-Geräte nicht verwendet werden, treten sie in einen leerlauffähigen, energiesparend zustandsarmen Zustand ein, der als moderner Standbymodus oder verbundener Standbymodus bezeichnet wird.</span><span class="sxs-lookup"><span data-stu-id="fc2d9-118">When not in use, Surface devices enter an idle, low powered state known as Modern Standby or Connected Standby.</span></span> <span data-ttu-id="fc2d9-119">IT-Administratoren können Geräte mithilfe einer Reaktivierungsanforderung (Paket), die die MAC-Adresse (Media Access Control) des Surface-Zielgeräts enthält, remote auslösen.</span><span class="sxs-lookup"><span data-stu-id="fc2d9-119">IT admins can remotely trigger devices using a wake request (magic packet) that contains the Media Access Control (MAC) address of the target Surface device.</span></span> <span data-ttu-id="fc2d9-120">Viele Verwaltungslösungen, z. B. Microsoft Endpoint Configuration Manager- und Drittanbieter-Microsoft Store-Apps, bieten integrierte Unterstützung für XAML.</span><span class="sxs-lookup"><span data-stu-id="fc2d9-120">Many management solutions, such as Microsoft Endpoint Configuration Manager and third-party Microsoft Store apps provide built-in support for WOL.</span></span> <span data-ttu-id="fc2d9-121">Weitere Informationen zum Aufwachen von Geräten mit Endpoint Configuration Manager finden Sie unter [Konfigurieren der Aktivierung im LAN – Configuration Manager.](/mem/configmgr/core/clients/deploy/configure-wake-on-lan)</span><span class="sxs-lookup"><span data-stu-id="fc2d9-121">To learn more about waking devices with Endpoint Configuration Manager, see [Configure Wake on LAN - Configuration Manager](/mem/configmgr/core/clients/deploy/configure-wake-on-lan).</span></span>

<span data-ttu-id="fc2d9-122">Die Unterstützung für Wake on LAN variiert je nach Ruhezustand: Verbundener Standbymodus oder Ruhezustand (S4-Energiezustand).</span><span class="sxs-lookup"><span data-stu-id="fc2d9-122">Support for Wake on LAN varies depending on sleep state:  Connected Standby or Hibernation (S4 power state).</span></span>

## <a name="connected-standby"></a><span data-ttu-id="fc2d9-123">Verbundener Standbymodus</span><span class="sxs-lookup"><span data-stu-id="fc2d9-123">Connected Standby</span></span>

<span data-ttu-id="fc2d9-124">Standardmäßig unterstützt Windows 10 Wake on LAN für Surface-Geräte im verbundenen Standbymodus.</span><span class="sxs-lookup"><span data-stu-id="fc2d9-124">By default, Windows 10 supports Wake on LAN for Surface devices in Connected Standby.</span></span>

### <a name="supported-surface-devices---connected-standby"></a><span data-ttu-id="fc2d9-125">Unterstützte Surface-Geräte – Verbundener Standbymodus</span><span class="sxs-lookup"><span data-stu-id="fc2d9-125">Supported Surface devices - Connected Standby</span></span>

- <span data-ttu-id="fc2d9-126">Surface Laptop 4 (nur Intel-Prozessoren)</span><span class="sxs-lookup"><span data-stu-id="fc2d9-126">Surface Laptop 4 (Intel processors only)</span></span>
- <span data-ttu-id="fc2d9-127">Surface Laptop 3 (nur Intel-Prozessoren)</span><span class="sxs-lookup"><span data-stu-id="fc2d9-127">Surface Laptop 3 (Intel processors only)</span></span>
- <span data-ttu-id="fc2d9-128">Surface Pro 7+</span><span class="sxs-lookup"><span data-stu-id="fc2d9-128">Surface Pro 7+</span></span>
- <span data-ttu-id="fc2d9-129">Surface Pro 7</span><span class="sxs-lookup"><span data-stu-id="fc2d9-129">Surface Pro 7</span></span>
- <span data-ttu-id="fc2d9-130">Surface Pro X</span><span class="sxs-lookup"><span data-stu-id="fc2d9-130">Surface Pro X</span></span>
- <span data-ttu-id="fc2d9-131">Surface Go 2</span><span class="sxs-lookup"><span data-stu-id="fc2d9-131">Surface Go 2</span></span>
- <span data-ttu-id="fc2d9-132">Surface Laptop Gehen</span><span class="sxs-lookup"><span data-stu-id="fc2d9-132">Surface Laptop Go</span></span>
- <span data-ttu-id="fc2d9-133">Surface Book 3</span><span class="sxs-lookup"><span data-stu-id="fc2d9-133">Surface Book 3</span></span>

## <a name="hibernation"></a><span data-ttu-id="fc2d9-134">Ruhezustand</span><span class="sxs-lookup"><span data-stu-id="fc2d9-134">Hibernation</span></span>

<span data-ttu-id="fc2d9-135">Um Geräte aus dem Ruhezustand zu reaktivieren, muss eine UEFI-Richtlinieneinstellung über [surface Enterprise Management Mode](surface-enterprise-management-mode.md) (SEMM) aktiviert werden (nicht erforderlich für Geräte, die mit Surface Dock 2 verbunden sind).</span><span class="sxs-lookup"><span data-stu-id="fc2d9-135">To wake devices out of Hibernation requires enabling a UEFI policy setting via [Surface Enterprise Management Mode](surface-enterprise-management-mode.md) (SEMM) (not required for devices connected to Surface Dock 2).</span></span>

### <a name="supported-surface-devices---hibernation"></a><span data-ttu-id="fc2d9-136">Unterstützte Surface-Geräte – Ruhezustand</span><span class="sxs-lookup"><span data-stu-id="fc2d9-136">Supported Surface devices - Hibernation</span></span>

- <span data-ttu-id="fc2d9-137">Surface Laptop 4 (nur Intel-Prozessoren)</span><span class="sxs-lookup"><span data-stu-id="fc2d9-137">Surface Laptop 4 (Intel processors only)</span></span>
- <span data-ttu-id="fc2d9-138">Surface Laptop 3 (nur Intel-Prozessoren)</span><span class="sxs-lookup"><span data-stu-id="fc2d9-138">Surface Laptop 3 (Intel processors only)</span></span>
- <span data-ttu-id="fc2d9-139">Surface Pro 7+</span><span class="sxs-lookup"><span data-stu-id="fc2d9-139">Surface Pro 7+</span></span>
- <span data-ttu-id="fc2d9-140">Surface Pro 7</span><span class="sxs-lookup"><span data-stu-id="fc2d9-140">Surface Pro 7</span></span>
- <span data-ttu-id="fc2d9-141">Surface Laptop Gehen</span><span class="sxs-lookup"><span data-stu-id="fc2d9-141">Surface Laptop Go</span></span>
- <span data-ttu-id="fc2d9-142">Surface Book 3</span><span class="sxs-lookup"><span data-stu-id="fc2d9-142">Surface Book 3</span></span>

### <a name="to-enable-wake-on-lan-uefi-setting"></a><span data-ttu-id="fc2d9-143">So aktivieren Sie die UEFI-Einstellung "Wake on LAN"</span><span class="sxs-lookup"><span data-stu-id="fc2d9-143">To enable Wake on LAN UEFI setting</span></span>

<span data-ttu-id="fc2d9-144">Um die UEFI-Einstellung "Wake on LAN" zu aktivieren, müssen Sie Zielgeräte bei SEMM registrieren, ein Konfigurationspaket erstellen und das Paket auf die Geräte anwenden.</span><span class="sxs-lookup"><span data-stu-id="fc2d9-144">To enable the Wake on LAN UEFI setting you need to enroll target devices into SEMM, create a configuration package, and apply the package to the devices.</span></span> <span data-ttu-id="fc2d9-145">Weitere Informationen finden Sie unter:</span><span class="sxs-lookup"><span data-stu-id="fc2d9-145">For more information, refer to:</span></span>

- [<span data-ttu-id="fc2d9-146">Surface Enterprise Management-Modus</span><span class="sxs-lookup"><span data-stu-id="fc2d9-146">Surface Enterprise Management Mode</span></span>](surface-enterprise-management-mode.md)
- [<span data-ttu-id="fc2d9-147">Registrieren und Konfigurieren von Surface-Geräten mit SEMM</span><span class="sxs-lookup"><span data-stu-id="fc2d9-147">Enroll and configure Surface devices with SEMM</span></span>](enroll-and-configure-surface-devices-with-semm.md)

1. <span data-ttu-id="fc2d9-148">Laden Sie [**Surface UEFI Configurator**](https://www.microsoft.com/download/details.aspx?id=46703)herunter, und installieren Sie es.</span><span class="sxs-lookup"><span data-stu-id="fc2d9-148">Download and install [**Surface UEFI Configurator**](https://www.microsoft.com/download/details.aspx?id=46703).</span></span>
2. <span data-ttu-id="fc2d9-149">Wählen \*\*\*\* Sie  >  **Start Configuration Package**  >  **Create**+ Certificate  > **Protection**aus.</span><span class="sxs-lookup"><span data-stu-id="fc2d9-149">Select **Start** > **Configuration Package** > **Create** >**+ Certificate Protection**.</span></span>
3. <span data-ttu-id="fc2d9-150">Wechseln Sie zu **"Erweiterte Einstellungen",** und wechseln Sie **"Wake on LAN"** zu **"Ein".**</span><span class="sxs-lookup"><span data-stu-id="fc2d9-150">Go to **Advanced settings** and switch **Wake on LAN** to **On**.</span></span>
4. <span data-ttu-id="fc2d9-151">Wenden Sie das Paket auf Zielgeräte an.</span><span class="sxs-lookup"><span data-stu-id="fc2d9-151">Apply the package to target devices.</span></span>

    > [!div class="mx-imgBorder"]
    > ![Aktivieren der UEFI-Richtlinieneinstellung für die Aktivierung im LAN](images/wol-uefi.png)

## <a name="learn-more"></a><span data-ttu-id="fc2d9-153">Mehr erfahren</span><span class="sxs-lookup"><span data-stu-id="fc2d9-153">Learn more</span></span>

- [<span data-ttu-id="fc2d9-154">Aktivieren von LAN für Surface Dock 2</span><span class="sxs-lookup"><span data-stu-id="fc2d9-154">Wake on LAN for Surface Dock 2</span></span>](wake-on-lan-surface-dock2.md)
- [<span data-ttu-id="fc2d9-155">Microsoft Surface USB-C zu Ethernet und USB-Adapter</span><span class="sxs-lookup"><span data-stu-id="fc2d9-155">Microsoft Surface USB-C to Ethernet and USB Adapter</span></span>](https://www.microsoft.com/p/surface-usb-c-to-ethernet-and-usb-adapter/8wt81cglrblp?)
- [<span data-ttu-id="fc2d9-156">Surface USB 3.0-Ethernet-Adapter für Ethernet-Ethernet</span><span class="sxs-lookup"><span data-stu-id="fc2d9-156">Surface USB 3.0 Gigabit Ethernet Adapter</span></span>](https://www.microsoft.com/p/surface-usb-30-gigabit-ethernet-adapter/8xn9fqvzbvq0?)
