---
title: Ändern des Microsoft Surface Hub-Gerätekontos
description: Sie können das Gerätekonto unter „Einstellungen“ ändern, indem Sie entweder ein Konto hinzufügen, wenn es noch nicht bereitgestellt wurde, oder die Eigenschaften eines bereits bereitgestellten Kontos ändern.
ms.assetid: AFC43043-3319-44BC-9310-29B1F375E672
ms.reviewer: ''
manager: laurawi
keywords: Gerätekonto ändern, Eigenschaften ändern, Surface Hub
ms.prod: surface-hub
ms.sitesec: library
author: dansimp
ms.author: dansimp
ms.topic: article
ms.date: 07/27/2017
ms.localizationpriority: medium
ms.openlocfilehash: b90ef3e208f1e76e4b02fb9f49e3e24030947bc7
ms.sourcegitcommit: 109d1d7608ac4667564fa5369e8722e569b8ea36
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/27/2020
ms.locfileid: "10834081"
---
# Ändern des Microsoft Surface Hub-Gerätekontos


Sie können das Gerätekonto unter „Einstellungen“ ändern, indem Sie entweder ein Konto hinzufügen, wenn es noch nicht bereitgestellt wurde, oder die Eigenschaften eines bereits bereitgestellten Kontos ändern.

##  <a name="details"></a>Details


<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th align="left">Wert</th>
<th align="left">Beschreibung</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left"><p>Benutzerprinzipalname</p></td>
<td align="left"><p>Der Benutzerprinzipalname (UPN) des Gerätekontos</p></td>
</tr>
<tr class="even">
<td align="left"><p>Kennwort</p></td>
<td align="left"><p>Das entsprechende Kennwort des Gerätekontos</p></td>
</tr>
<tr class="odd">
<td align="left"><p>Domäne</p></td>
<td align="left"><p>Die Domäne, zu der das Gerätekonto gehört. Dieses Feld muss für Office 365-Konten nicht bereitgestellt werden.</p></td>
</tr>
<tr class="even">
<td align="left"><p>Benutzername</p></td>
<td align="left"><p>Der Benutzername des Gerätekontos. Dieses Feld muss für Office 365-Konten nicht bereitgestellt werden.</p></td>
</tr>
<tr class="odd">
<td align="left"><p>Session Initiation-Protokoll (SIP)-Adresse</p></td>
<td align="left"><p>Die SIP-Adresse des Gerätekontos</p></td>
</tr>
<tr class="even">
<td align="left"><p>Microsoft Exchange-Server</p></td>
<td align="left"><p>Dies ist der Exchange-Server des Gerätekontos. Der Benutzername und das Kennwort des Gerätekontos müssen sich beim angegebenen Exchange-Server authentifizieren können.</p></td>
</tr>
<tr class="odd">
<td align="left"><p>Exchange-Dienste aktivieren</p></td>
<td align="left"><p>Ist diese Option aktiviert, werden alle Exchange-Dienste (z. B. Kalender auf der Willkommensseite, Senden von Whiteboards per E-Mail) aktiviert. Ist diese Option nicht aktiviert, werden alle Exchange-Dienste deaktiviert, und der Exchange-Server muss nicht angegeben werden.</p></td>
</tr>
</tbody>
</table>

 

##  <a name="what-happened"></a>Folgendes passiert:


Der Benutzerprinzipalname und das Kennwort werden zur Überprüfung des Kontos in AD oder Azure AD verwendet. Schlägt die Überprüfung fehl, müssen Sie möglicherweise die Domäne und den Benutzernamen bereitstellen.

Mithilfe der bereitgestellten Anmeldeinformationen versuchen wir, die SIP-Adresse zu ermitteln. Wenn keine SIP-Adresse gefunden wird, verwendet Skype for Business den UPN als SIP-Adresse. Ist dies nicht die SIP-Adresse für das Konto, müssen Sie die SIP-Adresse angeben.

Die Exchange Server-Adresse muss angegeben werden, wenn das Gerät keinen den Anmeldeinformationen zugeordneten Server findet. Microsoft Surface Hub verwendet den Exchange-Server für die Kommunikation mit ActiveSync, wodurch mehrere wichtige Features auf dem Gerät aktiviert werden.

##  <a name="related-content"></a>Verwandte Themen


[Verwalten von Microsoft Surface Hub](manage-surface-hub.md)

[Microsoft Surface Hub-Administratorhandbuch](surface-hub-administrators-guide.md)

 

 





