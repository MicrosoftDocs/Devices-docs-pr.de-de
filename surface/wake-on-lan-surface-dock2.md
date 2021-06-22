---
title: Aktivieren des LAN mit Surface Dock 2
description: Surface Dock 2 bietet die beste Unterstützung für Wake on LAN (DOPPELKLICK), damit Administratoren Geräte remote reaktivieren und Verwaltungsaufgaben automatisch ausführen können.
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
ms.date: 6/03/2021
ms.openlocfilehash: 74b36b60cb58ecb9042b73b8cdba7271d0af8c80
ms.sourcegitcommit: 267e12897efd9d11f8c7303eaf780632741cfe77
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/22/2021
ms.locfileid: "11614082"
---
# <a name="wake-on-lan-with-surface-dock-2"></a><span data-ttu-id="313a8-104">Aktivieren des LAN mit Surface Dock 2</span><span class="sxs-lookup"><span data-stu-id="313a8-104">Wake On LAN with Surface Dock 2</span></span>

<span data-ttu-id="313a8-105">Um Geräte vollständig auf dem neuesten Stand zu halten, müssen IT-Administratoren In der Lage sein, Geräte zu verwalten, wenn sie nicht verwendet werden, in der Regel während der Nachtwartungsfenster.</span><span class="sxs-lookup"><span data-stu-id="313a8-105">To keep devices fully up to date, IT admins need to be able to manage devices when they’re not in use, typically during nightly maintenance windows.</span></span> <span data-ttu-id="313a8-106">Surface Dock 2 bietet die beste Unterstützung für Wake on LAN (DOPPELKLICK), damit Administratoren Geräte remote reaktivieren und Verwaltungsaufgaben automatisch mit Microsoft Endpoint Manager oder anderen Lösungen von Drittanbietern ausführen können.</span><span class="sxs-lookup"><span data-stu-id="313a8-106">Surface Dock 2 provides the best support for Wake on LAN (WOL) enabling admins to remotely wake up devices and automatically perform management tasks with Microsoft Endpoint Manager or other third party solutions.</span></span>

## <a name="requirements"></a><span data-ttu-id="313a8-107">Anforderungen</span><span class="sxs-lookup"><span data-stu-id="313a8-107">Requirements</span></span>

<span data-ttu-id="313a8-108">Geräte müssen über eine kabelgebundene Verbindung mit Surface Dock 2 verfügen und mit dem Netzbetrieb verbunden bleiben.</span><span class="sxs-lookup"><span data-stu-id="313a8-108">Devices must have a wired connection with Surface Dock 2 and stay connected to AC Power.</span></span>

> [!div class="mx-imgBorder"]
> ![Surface Dock 2](images/surface-dock2-angled.png)

## <a name="supported-surface-devices"></a><span data-ttu-id="313a8-110">Unterstützte Surface-Geräte</span><span class="sxs-lookup"><span data-stu-id="313a8-110">Supported Surface devices</span></span>

- <span data-ttu-id="313a8-111">Surface Laptop 4 (Intel-Prozessoren)</span><span class="sxs-lookup"><span data-stu-id="313a8-111">Surface Laptop 4 (Intel processors)</span></span>
- <span data-ttu-id="313a8-112">Surface Laptop 4 (AMD-Prozessoren)</span><span class="sxs-lookup"><span data-stu-id="313a8-112">Surface Laptop 4 (AMD processors)</span></span>
- <span data-ttu-id="313a8-113">Surface Laptop 3 (Intel-Prozessoren)</span><span class="sxs-lookup"><span data-stu-id="313a8-113">Surface Laptop 3 (Intel processors)</span></span>
- <span data-ttu-id="313a8-114">Surface Pro 7+</span><span class="sxs-lookup"><span data-stu-id="313a8-114">Surface Pro 7+</span></span>
- <span data-ttu-id="313a8-115">Surface Pro 7</span><span class="sxs-lookup"><span data-stu-id="313a8-115">Surface Pro 7</span></span>
- <span data-ttu-id="313a8-116">Surface Pro X</span><span class="sxs-lookup"><span data-stu-id="313a8-116">Surface Pro X</span></span>
- <span data-ttu-id="313a8-117">Surface Go 2</span><span class="sxs-lookup"><span data-stu-id="313a8-117">Surface Go 2</span></span>
- <span data-ttu-id="313a8-118">Surface Laptop Gehen</span><span class="sxs-lookup"><span data-stu-id="313a8-118">Surface Laptop Go</span></span>
- <span data-ttu-id="313a8-119">Surface Book 3</span><span class="sxs-lookup"><span data-stu-id="313a8-119">Surface Book 3</span></span>

<span data-ttu-id="313a8-120">Surface Dock 2 bietet VON Unterstützung für Geräte in den folgenden Energiezuständen:</span><span class="sxs-lookup"><span data-stu-id="313a8-120">Surface Dock 2 provides WOL support for devices in the following power states:</span></span>

- <span data-ttu-id="313a8-121">Verbundener Standbymodus</span><span class="sxs-lookup"><span data-stu-id="313a8-121">Connected standby</span></span>
- <span data-ttu-id="313a8-122">Ruhezustand (S4-Energiezustand)</span><span class="sxs-lookup"><span data-stu-id="313a8-122">Hibernation (S4 power state)</span></span>
- <span data-ttu-id="313a8-123">Ruhezustand (S5-Energiezustand "ausgeschaltet")</span><span class="sxs-lookup"><span data-stu-id="313a8-123">Hibernation (S5 “soft off” power state)</span></span>

<span data-ttu-id="313a8-124">Weitere Informationen zu Energiezuständen finden Sie unter ["System Power States".](/windows/win32/power/system-power-states)</span><span class="sxs-lookup"><span data-stu-id="313a8-124">To learn more about power states, see [System Power States](/windows/win32/power/system-power-states).</span></span>

## <a name="how-it-works"></a><span data-ttu-id="313a8-125">Funktionsweise</span><span class="sxs-lookup"><span data-stu-id="313a8-125">How it works</span></span>

<span data-ttu-id="313a8-126">Wenn Surface-Geräte nicht verwendet werden, treten sie in einen leerlauffähigen, energiesparend zustandsarmen Zustand ein, der als moderner Standbymodus oder verbundener Standbymodus bezeichnet wird.</span><span class="sxs-lookup"><span data-stu-id="313a8-126">When not in use, Surface devices enter an idle, low powered state known as Modern Standby or Connected Standby.</span></span> <span data-ttu-id="313a8-127">IT-Administratoren können Geräte mithilfe einer Reaktivierungsanforderung (Paket), die die MAC-Adresse (Media Access Control) des Surface-Zielgeräts enthält, remote auslösen.</span><span class="sxs-lookup"><span data-stu-id="313a8-127">IT admins can remotely trigger devices using a wake request (magic packet) that contains the Media Access Control (MAC) address of the target Surface device.</span></span> <span data-ttu-id="313a8-128">Viele Verwaltungslösungen, z. B. Microsoft Endpoint Configuration Manager- und Drittanbieter-Microsoft Store-Apps, bieten integrierte Unterstützung für CSV.</span><span class="sxs-lookup"><span data-stu-id="313a8-128">Many management solutions, such as Microsoft Endpoint Configuration Manager and third-party Microsoft Store apps provide built-in support for WOL.</span></span>

<span data-ttu-id="313a8-129">Informationen zum Aktivieren von SODASS auf Geräten ohne Surface Dock 2 finden Sie unter ["Wake on LAN" für Surface-Geräte.](wake-on-lan-for-surface-devices.md)</span><span class="sxs-lookup"><span data-stu-id="313a8-129">To enable WOL on devices without Surface Dock 2, see [Wake on LAN for Surface devices](wake-on-lan-for-surface-devices.md).</span></span>

## <a name="learn-more"></a><span data-ttu-id="313a8-130">Mehr erfahren</span><span class="sxs-lookup"><span data-stu-id="313a8-130">Learn more</span></span>

- [<span data-ttu-id="313a8-131">Surface Dock 2</span><span class="sxs-lookup"><span data-stu-id="313a8-131">Surface Dock 2</span></span>](https://www.microsoft.com/p/surface-dock-2-for-business/8q4hgc6kbmdq?)
- [<span data-ttu-id="313a8-132">Wake-On-LAN für Surface-Geräte</span><span class="sxs-lookup"><span data-stu-id="313a8-132">Wake On LAN for Surface devices</span></span>](wake-on-lan-for-surface-devices.md)
- [<span data-ttu-id="313a8-133">Systemstromzustände</span><span class="sxs-lookup"><span data-stu-id="313a8-133">System Power States</span></span>](/windows/win32/power/system-power-states)
- [<span data-ttu-id="313a8-134">Konfigurieren der Aktivierung im LAN – Configuration Manager</span><span class="sxs-lookup"><span data-stu-id="313a8-134">Configure Wake on LAN - Configuration Manager</span></span>](/mem/configmgr/core/clients/deploy/configure-wake-on-lan)
