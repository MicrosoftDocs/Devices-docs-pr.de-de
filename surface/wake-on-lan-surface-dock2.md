---
title: Wake-On-LAN mit Surface Dock 2
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
ms.date: 7/02/2021
ms.openlocfilehash: 4a74efb8af776e9805ad3148ea656f0a65d5d09c
ms.sourcegitcommit: d020d899e9c7e1eb0b85193ecb0a17a85bb39fe6
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/12/2021
ms.locfileid: "11643851"
---
# <a name="wake-on-lan-with-surface-dock-2"></a><span data-ttu-id="2f829-104">Wake-On-LAN mit Surface Dock 2</span><span class="sxs-lookup"><span data-stu-id="2f829-104">Wake On LAN with Surface Dock 2</span></span>

<span data-ttu-id="2f829-105">Um Geräte vollständig auf dem neuesten Stand zu halten, müssen IT-Administratoren In der Lage sein, Geräte zu verwalten, wenn sie nicht verwendet werden, in der Regel während der Nachtwartungsfenster.</span><span class="sxs-lookup"><span data-stu-id="2f829-105">To keep devices fully up to date, IT admins need to be able to manage devices when they’re not in use, typically during nightly maintenance windows.</span></span> <span data-ttu-id="2f829-106">Surface Dock 2 bietet die beste Unterstützung für Wake on LAN (DOPPELKLICK), damit Administratoren Geräte remote reaktivieren und Verwaltungsaufgaben automatisch mit Microsoft Endpoint Manager oder anderen Lösungen von Drittanbietern ausführen können.</span><span class="sxs-lookup"><span data-stu-id="2f829-106">Surface Dock 2 provides the best support for Wake on LAN (WOL) enabling admins to remotely wake up devices and automatically perform management tasks with Microsoft Endpoint Manager or other third party solutions.</span></span>

## <a name="requirements"></a><span data-ttu-id="2f829-107">Anforderungen</span><span class="sxs-lookup"><span data-stu-id="2f829-107">Requirements</span></span>

<span data-ttu-id="2f829-108">Geräte müssen über eine kabelgebundene Verbindung mit Surface Dock 2 verfügen und mit dem Netzbetrieb verbunden bleiben.</span><span class="sxs-lookup"><span data-stu-id="2f829-108">Devices must have a wired connection with Surface Dock 2 and stay connected to AC Power.</span></span>

> [!div class="mx-imgBorder"]
> ![Surface Dock 2](images/surface-dock2-angled.png)

## <a name="supported-surface-devices"></a><span data-ttu-id="2f829-110">Unterstützte Surface-Geräte</span><span class="sxs-lookup"><span data-stu-id="2f829-110">Supported Surface devices</span></span>

- <span data-ttu-id="2f829-111">Surface Laptop 4 (Intel-Prozessoren)</span><span class="sxs-lookup"><span data-stu-id="2f829-111">Surface Laptop 4 (Intel processors)</span></span>
- <span data-ttu-id="2f829-112">Surface Laptop 4 (AMD-Prozessoren)</span><span class="sxs-lookup"><span data-stu-id="2f829-112">Surface Laptop 4 (AMD processors)</span></span>
- <span data-ttu-id="2f829-113">Surface Laptop 3 (Intel-Prozessoren)</span><span class="sxs-lookup"><span data-stu-id="2f829-113">Surface Laptop 3 (Intel processors)</span></span>
- <span data-ttu-id="2f829-114">Surface Pro 7+</span><span class="sxs-lookup"><span data-stu-id="2f829-114">Surface Pro 7+</span></span>
- <span data-ttu-id="2f829-115">Surface Pro 7</span><span class="sxs-lookup"><span data-stu-id="2f829-115">Surface Pro 7</span></span>
- <span data-ttu-id="2f829-116">Surface Pro X</span><span class="sxs-lookup"><span data-stu-id="2f829-116">Surface Pro X</span></span>
- <span data-ttu-id="2f829-117">Surface Go 2</span><span class="sxs-lookup"><span data-stu-id="2f829-117">Surface Go 2</span></span>
- <span data-ttu-id="2f829-118">Surface Laptop Gehen</span><span class="sxs-lookup"><span data-stu-id="2f829-118">Surface Laptop Go</span></span>
- <span data-ttu-id="2f829-119">Surface Book 3</span><span class="sxs-lookup"><span data-stu-id="2f829-119">Surface Book 3</span></span>

<span data-ttu-id="2f829-120">Surface Dock 2 bietet VON Unterstützung für Geräte in den folgenden Energiezuständen:</span><span class="sxs-lookup"><span data-stu-id="2f829-120">Surface Dock 2 provides WOL support for devices in the following power states:</span></span>

- <span data-ttu-id="2f829-121">Verbundener Standbymodus</span><span class="sxs-lookup"><span data-stu-id="2f829-121">Connected standby</span></span>
- <span data-ttu-id="2f829-122">Ruhezustand (S4-Energiezustand)</span><span class="sxs-lookup"><span data-stu-id="2f829-122">Hibernation (S4 power state)</span></span>
- <span data-ttu-id="2f829-123">Herunterfahren (S5 -Energiezustand "ausgeschaltet")</span><span class="sxs-lookup"><span data-stu-id="2f829-123">Shutdown (S5 “soft off” power state)</span></span>

<span data-ttu-id="2f829-124">Weitere Informationen zu Energiezuständen finden Sie unter ["System Power States".](/windows/win32/power/system-power-states)</span><span class="sxs-lookup"><span data-stu-id="2f829-124">To learn more about power states, see [System Power States](/windows/win32/power/system-power-states).</span></span>

## <a name="how-it-works"></a><span data-ttu-id="2f829-125">Funktionsweise</span><span class="sxs-lookup"><span data-stu-id="2f829-125">How it works</span></span>

<span data-ttu-id="2f829-126">Wenn Surface-Geräte nicht verwendet werden, treten sie in einen leerlauffähigen, energiesparend zustandsarmen Zustand ein, der als moderner Standbymodus oder verbundener Standbymodus bezeichnet wird.</span><span class="sxs-lookup"><span data-stu-id="2f829-126">When not in use, Surface devices enter an idle, low powered state known as Modern Standby or Connected Standby.</span></span> <span data-ttu-id="2f829-127">IT-Administratoren können Geräte mithilfe einer Reaktivierungsanforderung (Paket), die die MAC-Adresse (Media Access Control) des Surface-Zielgeräts enthält, remote auslösen.</span><span class="sxs-lookup"><span data-stu-id="2f829-127">IT admins can remotely trigger devices using a wake request (magic packet) that contains the Media Access Control (MAC) address of the target Surface device.</span></span> <span data-ttu-id="2f829-128">Viele Verwaltungslösungen, z. B. Microsoft Endpoint Configuration Manager- und Drittanbieter-Microsoft Store-Apps, bieten integrierte Unterstützung für XAML.</span><span class="sxs-lookup"><span data-stu-id="2f829-128">Many management solutions, such as Microsoft Endpoint Configuration Manager and third-party Microsoft Store apps provide built-in support for WOL.</span></span>

<span data-ttu-id="2f829-129">Informationen zum Aktivieren von SODASS auf Geräten ohne Surface Dock 2 finden Sie unter ["Wake on LAN" für Surface-Geräte.](wake-on-lan-for-surface-devices.md)</span><span class="sxs-lookup"><span data-stu-id="2f829-129">To enable WOL on devices without Surface Dock 2, see [Wake on LAN for Surface devices](wake-on-lan-for-surface-devices.md).</span></span>

## <a name="learn-more"></a><span data-ttu-id="2f829-130">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="2f829-130">Learn more</span></span>

- [<span data-ttu-id="2f829-131">Surface Dock 2</span><span class="sxs-lookup"><span data-stu-id="2f829-131">Surface Dock 2</span></span>](https://www.microsoft.com/p/surface-dock-2-for-business/8q4hgc6kbmdq?)
- [<span data-ttu-id="2f829-132">Wake-On-LAN für Surface-Geräte</span><span class="sxs-lookup"><span data-stu-id="2f829-132">Wake On LAN for Surface devices</span></span>](wake-on-lan-for-surface-devices.md)
- [<span data-ttu-id="2f829-133">Systemstromzustände</span><span class="sxs-lookup"><span data-stu-id="2f829-133">System Power States</span></span>](/windows/win32/power/system-power-states)
- [<span data-ttu-id="2f829-134">Konfigurieren der Aktivierung im LAN – Configuration Manager</span><span class="sxs-lookup"><span data-stu-id="2f829-134">Configure Wake on LAN - Configuration Manager</span></span>](/mem/configmgr/core/clients/deploy/configure-wake-on-lan)
