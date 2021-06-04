---
title: Ethernet-Adapter und Surface-Bereitstellung (Surface)
description: Dieser Artikel enthält eine Reihe von Hinweisen und Antworten, auf die Sie bei der Netzwerkbereitstellung auf Surface-Geräten zurückgreifen können.
ms.assetid: 5273C59E-6039-4E50-96B3-426BB38A64C0
ms.reviewer: ''
manager: laurawi
keywords: Ethernet, bereitstellen, austauschbar, Netzwerk, Konnektivität, starten, Firmware, Gerät, Adapter, PXE-Start, USB
ms.localizationpriority: medium
ms.prod: w10
ms.mktglfcycl: deploy
ms.pagetype: surface, devices
ms.sitesec: library
author: coveminer
ms.author: greglin
ms.topic: article
ms.audience: itpro
ms.openlocfilehash: 4b0cfd9cadab33d82ae3d0acaa83e007229c6fb8
ms.sourcegitcommit: 109d1d7608ac4667564fa5369e8722e569b8ea36
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/27/2020
ms.locfileid: "10832548"
---
# Ethernet-Adapter und Surface-Bereitstellung


Dieser Artikel enthält Anleitungen und Antworten, die Ihnen bei der Durchführung einer Netzwerkbereitstellung auf Surface-Geräten einschließlich Surface pro 3 und höher helfen.

Die Netzwerkbereitstellung auf Surface-Geräten kann für Systemadministratoren eine Herausforderung darstellen. Da Surface-Geräte keine systemeigenen Ethernet-Adapter haben, müssen Sie die Konnektivität über einen austauschbaren Ethernet-Adapter herstellen.

##  <a name="select-an-ethernet-adapter-for-surface-devices"></a>Auswählen eines Ethernet-Adapters für Surface-Geräte


Bevor Sie entscheiden, wie Sie in der Bereitstellungsumgebung starten oder wie die Geräte von der Bereitstellungslösung erkannt werden, müssen Sie einen Adapter für Kabelnetzwerke verwenden.

Achten Sie beim Auswählen eines Ethernet-Adapters darauf, wie der Adapter Ihr Surface-Gerät aus dem Netzwerk startet. Wenn Sie Clients mit Windows-Bereitstellungsdiensten (Windows Deployment Services, WDS) Pre-Staging oder wenn Sie Microsoft Endpoint Configuration Manager verwenden, sollten Sie auch prüfen, ob die Wechsel-Ethernet-Adapter für ein bestimmtes Surface-Gerät dediziert sind oder von mehreren Geräten freigegeben werden. Weitere Informationen zu potenziellen Konflikten mit freigegebenen Adaptern finden Sie unter [Verwalten von Mac-Adressen mit entfernbaren Ethernet-Adaptern](#manage-mac-addresses) weiter unten in diesem Artikel.

Der Netzwerkstart (PXE-Start) wird nur unterstützt, wenn Sie einen Ethernet-Adapter oder eine Dockingstation von Microsoft verwenden. Um vom Netzwerk zu starten, muss der Chipsatz im Ethernet-Adapter oder in der Dockingstation erkannt und als Startgerät in der Firmware des Surface-Geräts konfiguriert werden. Microsoft-Ethernet-Adapter, beispielsweise der Surface-Ethernet-Adapter und [Surface Dock](https://www.microsoft.com/surface/accessories/surface-dock), verwenden einen Chipsatz, der mit der Surface-Firmware kompatibel ist.

Die folgenden Ethernet-Geräte werden für den Netzwerkstart auf Surface-Geräten unterstützt:

-   Surface USB-C zu Ethernet und USB 3,0-Adapter

-   Surface USB 3,0-Gigabit-Ethernet-Adapter

-   Surface Dock

-   Surface 3-Dockingstation

-   Surface Pro 3-Dockingstation

-   Dockingstation für Surface Pro und Surface Pro 2

Ethernet-Adapter von Drittanbietern werden auch für die Netzwerkbereitstellung unterstützt, bieten aber keine Unterstützung für den PXE-Start. Um einen Ethernet-Adapter eines Drittanbieters zu verwenden, müssen Sie die Treiber in das Startimage für die Bereitstellung laden und das Startimage von einem separaten Speichergerät, z.B. einem USB-Stick, starten.

##  <a name="boot-surface-devices-from-the-network"></a>Starten von Surface-Geräten vom Netzwerk

Um vom Netzwerk oder einem angeschlossenen USB-Stick zu starten, müssen Sie das Surface-Gerät dazu anweisen, von einem alternativen Startgerät zu starten. Sie können die Startreihenfolge in der Systemfirmware ändern, um USB-Startgeräten den Vorrang zu geben, oder aber Sie weisen das Gerät während des Systemstarts an, von einem alternativen Startgerät zu starten.

Führen Sie zum Starten eines Surface-Geräts von einem alternativen Startgerät die folgenden Schritte aus:

1.  Stellen Sie sicher, dass das Surface-Gerät ausgeschaltet ist.
2.  Halten Sie die **Leiser**-Taste gedrückt.
3.  Drücken Sie die **Ein/Aus**-Taste, und lassen Sie sie wieder los.
4.  Wenn das System vom USB-Stick oder Ethernet-Adapter zu starten beginnt, lassen Sie die **Leiser**-Taste los.

>[!NOTE]
>Zusätzlich zu einem Ethernet-Adapter muss auch eine Tastatur mit dem Surface verbunden sein, damit Sie in die Vorinstallationsumgebung gelangen und durch den Bereitstellungs-Assistenten navigieren können.

 
Bei Windows 10, Version 1511, und höher (einschließlich Windows Assessment and Deployment Kit (Windows ADK) für Windows10, Version 1511) sind die Treiber für Microsoft Surface-Ethernet-Adapter standardmäßig enthalten. Wenn Sie eine auf Windows Preinstallation Environment (WinPE) basierende Bereitstellungslösung (etwa das Microsoft Deployment Toolkit) verwenden und mit PXE einen Systemstart über das Netzwerk durchführen, müssen Sie sicherstellen, dass die Bereitstellungslösung die aktuelle Version des Windows ADK verwendet.

## <a href="" id="manage-mac-addresses"></a>Verwalten von MAC-Adressen mit austauschbaren Ethernet-Adaptern

Administratoren, die Windows über das Netzwerk bereitstellen, müssen entscheiden, wie sie die Computer identifizieren, wenn sie für die Bereitstellung auf mehreren Computern den gleichen Ethernet-Adapter verwenden. Ein oft von Bereitstellungstechnologien herangezogener Bezeichner ist die Media Access Control (MAC)-Adresse, die einzelnen Ethernet-Adaptern zugeordnet ist. Wenn Sie allerdings den gleichen Ethernet-Adapter für die Bereitstellung auf mehreren Computern verwenden, können Sie keine Bereitstellungstechnologie verwenden, die MAC-Adressen prüft, da die MAC-Adresse des austauschbaren Adapters nicht eindeutig identifiziert werden kann, wenn er auf verschiedenen Computern verwendet wird.

Um MAC-Adressenkonflikte zu vermeiden, stellen Sie im Idealfall für jedes Surface-Gerät einen dedizierten austauschbaren Ethernet-Adapter bereit. Dies ist immer dann sinnvoll, wenn der Ethernet-Adapter oder die zusätzliche Funktionalität der Dockingstation regelmäßig verwendet werden sollen. Allerdings ist die zusätzliche Nutzung einer Dockingstation bzw. die Unterstützung für Kabelnetzwerke nicht immer erforderlich.

Konflikte können Sie bei der gemeinsamen Nutzung von Adaptern auch vermeiden, indem Sie für die Bereitstellung auf Surface-Geräten das [Microsoft Deployment Toolkit (MDT)](https://technet.microsoft.com/windows/dn475741) verwenden. MDT identifiziert einzelne Computer nicht anhand der MAC-Adresse und ist daher von dieser Einschränkung nicht betroffen. MDT verwendet allerdings Windows-Bereitstellungsdienste, um die Funktionalität von PXE-Starts zu gewährleisten, und ist daher Einschränkungen bezüglich vorab bereitgestellter Clients unterworfen, die weiter unten in diesem Abschnitt behandelt werden.

Wenn Sie einen gemeinsam genutzten Adapter für die Bereitstellung verwenden, sollten Sie Systeme auf andere Art und Weise eindeutig identifizieren, falls Sie die genannten Technologien einsetzen. Für Configuration Manager und WDS bietet es sich an, den System Universal Unique Identifier (System UUID) zu verwenden, der bei der Herstellung des Computers in der Firmware eingebettet wurde. Diesen Eintrag in die Firmware des Computers finden Sie bei Surface-Geräte unter **Geräteinformationen**.

Gehen Sie wie folgt vor, um auf die Firmware eines Surface-Geräts zuzugreifen:

1.  Stellen Sie sicher, dass das Surface-Gerät ausgeschaltet ist.
2.  Halten Sie die **Lauter**-Taste gedrückt.
3.  Drücken Sie die **Ein/Aus**-Taste, und lassen Sie sie wieder los.
4.  Wenn das Gerät hochfährt, lassen Sie die **Lauter**-Taste los.

Wenn Sie die Bereitstellung mit WDS durchführen, wird ein Computer nur anhand der MAC-Adresse identifiziert, wenn der Bereitstellungsserver so konfiguriert ist, dass er nur auf bekannte, vorab bereitgestellte Clients reagiert. Um einen Client vorab bereitzustellen, erstellt der Administrator ein Computerkonto in Active Directory und definiert diesen Computer anhand der MAC-Adresse oder des System UUID. Wenn Sie eventuelle Identitätskonflikte vermeiden möchten, die durch die gemeinsame Nutzung von Ethernet-Adaptern entstehen, sollten Sie den [System UUID zum Definieren von vorab bereitgestellten Clients verwenden](https://technet.microsoft.com/library/cc742034). Alternativ können Sie WDS so konfigurieren, dass auf unbekannte Clients reagiert wird, die weder eine MAC-Adresse oder System UUID für die Identifikation erfordern. Wählen Sie hierfür auf der Registerkarte [**PXE-Antwort**](https://technet.microsoft.com/library/cc732360) in den **Eigenschaften des Windows-Bereitstellungsservers** die Option **Allen Clientcomputern antworten (bekannten und unbekannten)**.

Konflikte zwischen gemeinsam genutzten Ethernet-Adaptern sind bei der Verwendung von Configuration Manager noch wahrscheinlicher. Während WDS einzelne Systeme nur bei entsprechender Konfiguration anhand der MAC-Adresse identifiziert, verwendet Configuration Manager bei jeder Bereitstellung auf neuen oder unbekannten Computern die MAC-Adresse zur Identifizierung der einzelnen Systeme. Dies führt möglicherweise zu nicht ordnungsgemäß konfigurierten Geräten oder sogar dazu, dass immer nur ein System mit einem gemeinsam genutzten Ethernet-Adapter bereitgestellt werden kann. Es gibt mehrere mögliche Lösungen für diese Situation, die ausführlich unter [Verwenden desselben externen Ethernet-Adapters für mehrere SCCM-OSD](https://techcommunity.microsoft.com/t5/core-infrastructure-and-security/how-to-use-the-same-external-ethernet-adapter-for-multiple-sccm/ba-p/257374), einen Blogbeitrag im Core Infrastructure and Security-Blog beschrieben werden.

 

 





