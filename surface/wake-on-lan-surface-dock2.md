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
# <a name="wake-on-lan-with-surface-dock-2"></a>Wake-On-LAN mit Surface Dock 2

Um Geräte vollständig auf dem neuesten Stand zu halten, müssen IT-Administratoren In der Lage sein, Geräte zu verwalten, wenn sie nicht verwendet werden, in der Regel während der Nachtwartungsfenster. Surface Dock 2 bietet die beste Unterstützung für Wake on LAN (DOPPELKLICK), damit Administratoren Geräte remote reaktivieren und Verwaltungsaufgaben automatisch mit Microsoft Endpoint Manager oder anderen Lösungen von Drittanbietern ausführen können.

## <a name="requirements"></a>Anforderungen

Geräte müssen über eine kabelgebundene Verbindung mit Surface Dock 2 verfügen und mit dem Netzbetrieb verbunden bleiben.

> [!div class="mx-imgBorder"]
> ![Surface Dock 2](images/surface-dock2-angled.png)

## <a name="supported-surface-devices"></a>Unterstützte Surface-Geräte

- Surface Laptop 4 (Intel-Prozessoren)
- Surface Laptop 4 (AMD-Prozessoren)
- Surface Laptop 3 (Intel-Prozessoren)
- Surface Pro 7+
- Surface Pro 7
- Surface Pro X
- Surface Go 2
- Surface Laptop Gehen
- Surface Book 3

Surface Dock 2 bietet VON Unterstützung für Geräte in den folgenden Energiezuständen:

- Verbundener Standbymodus
- Ruhezustand (S4-Energiezustand)
- Herunterfahren (S5 -Energiezustand "ausgeschaltet")

Weitere Informationen zu Energiezuständen finden Sie unter ["System Power States".](/windows/win32/power/system-power-states)

## <a name="how-it-works"></a>Funktionsweise

Wenn Surface-Geräte nicht verwendet werden, treten sie in einen leerlauffähigen, energiesparend zustandsarmen Zustand ein, der als moderner Standbymodus oder verbundener Standbymodus bezeichnet wird. IT-Administratoren können Geräte mithilfe einer Reaktivierungsanforderung (Paket), die die MAC-Adresse (Media Access Control) des Surface-Zielgeräts enthält, remote auslösen. Viele Verwaltungslösungen, z. B. Microsoft Endpoint Configuration Manager- und Drittanbieter-Microsoft Store-Apps, bieten integrierte Unterstützung für XAML.

Informationen zum Aktivieren von SODASS auf Geräten ohne Surface Dock 2 finden Sie unter ["Wake on LAN" für Surface-Geräte.](wake-on-lan-for-surface-devices.md)

## <a name="learn-more"></a>Weitere Informationen

- [Surface Dock 2](https://www.microsoft.com/p/surface-dock-2-for-business/8q4hgc6kbmdq?)
- [Wake-On-LAN für Surface-Geräte](wake-on-lan-for-surface-devices.md)
- [Systemstromzustände](/windows/win32/power/system-power-states)
- [Konfigurieren der Aktivierung im LAN – Configuration Manager](/mem/configmgr/core/clients/deploy/configure-wake-on-lan)
