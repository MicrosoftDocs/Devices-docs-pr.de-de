---
title: Neuigkeiten in Windows 10, Version1703, für Surface Hub
description: Windows10, Version1703 (Creators Update) enthält neue Features für Microsoft Surface Hub.
ms.prod: surface-hub
ms.sitesec: library
author: dansimp
ms.author: dansimp
ms.topic: article
ms.date: 01/18/2018
ms.reviewer: ''
manager: laurawi
ms.localizationpriority: medium
ms.openlocfilehash: 722309a6b018c32bde329cb7b2cdd68b859fc1ca
ms.sourcegitcommit: 8e809e8481023fe4421abcdaa1e055a6f2f74f5f
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/11/2020
ms.locfileid: "10924941"
---
# Neuigkeiten in Windows10, Version1703, für Microsoft Surface Hub

Hier ist Surface Hub-Techniker Jordanien Marchese bei der Präsentation von Updates für Microsoft Surface Hub mit Windows10, Version 1703 (Creators Update). 

<a href="https://www.youtube.com/watch?v=R8tX10VIgq0" target="_blank"> <img src="images/whats-new-video-thumbnail.png" alt="Link to Surface Hub video on Youtube" /></a>

Windows10, Version1703 (auch als das Creators Update bezeichnet) führt die folgenden Änderungen für Microsoft Surface Hub ein.

##  <a name="new-settings"></a>Neue Einstellungen

Der Verwaltung mobiler Geräte (Mobile Device Management, MDM) und den Konfigurationsdienstanbietern (Configuration Service Providers, CSPs) wurden zur Erweiterung der Surface Hub-Verwaltungsfunktionen Einstellungen hinzugefügt. [Die neuen Einstellungen umfassen](manage-settings-with-mdm-for-surface-hub.md):

- InBoxApps/SkypeForBusiness/DomainName
- InBoxApps/Connect/AutoLaunch
- Properties/DefaultVolume
- Properties/ScreenTimeout
- Properties/SessionTimeout
- Properties/SleepTimeout
- Properties/AllowSessionResume
- Properties/AllowAutoProxyAuth
- Properties/DisableSigninSuggestions
- Properties/DoNotShowMyMeetingsAndFiles
- System/AllowStorageCard

Sowie Einstellungen, basierend auf der neuen [NetworkQoSPolicy CSP](https://msdn.microsoft.com/windows/hardware/commercialize/customize/mdm/networkqospolicy-csp) und [NetworkProxy CSP](https://msdn.microsoft.com/windows/hardware/commercialize/customize/mdm/networkproxy-csp).
</br>

##  <a name="provisioning-wizard"></a>Bereitstellungs-Assistent

Ein benutzerfreundlicher Assistent unterstützt Sie beim schnellen Erstellen von Bereitstellungspaketen, die Sie auf mehrere Surface Hub-Geräte anwenden können. Darüber hinaus umfasst er Massenbeitritt zu Azure Active Directory. [Hier erfahren Sie, wie Sie ein Bereitstellungspaket für Surface Hub erstellen können.](provisioning-packages-for-certificates-surface-hub.md)

![Schritte beim Bereitstellungsassistenten für Surface Hub-Geräte](images/wcd-wizard.png)
    
##  <a name="miracast-on-your-existing-wireless-network-or-lan"></a>Miracast auf Ihren vorhandenen Funknetzwerken oder LAN 

Microsoft hat Microsoft die Möglichkeit erweitert, [einen Miracast-Datenstrom über ein lokales Netzwerk](miracast-over-infrastructure.md) anstatt über eine direkte drahtlose Verbindung zu senden. 
    
##  <a name="cloud-recovery"></a>Cloud-Wiederherstellung

Beim Zurücksetzen eines Surface Hub-Geräts besteht jetzt die Möglichkeit, einen Werksbuild des Betriebssystems aus der Cloud herunterzuladen und zu installieren. [Hier erfahren Sie mehr über die Cloud-Wiederherstellung.](device-reset-surface-hub.md#cloud-recovery)

>[!NOTE]
>Die Cloud-Wiederherstellung funktioniert nicht, wenn Sie Proxyserver verwenden.
    
![Neuinstallation](images/reinstall.png)
    
##  <a name="end-session"></a>Sitzung beenden

**Fertig** ist jetzt **Sitzung beenden**. [Hier erfahren Sie, wie Sie „Sitzung beenden” verwenden können.](finishing-your-surface-hub-meeting.md) 

![Sitzung beenden](images/end-session.png)



 

 
