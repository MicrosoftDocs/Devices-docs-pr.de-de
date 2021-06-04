---
title: Speichern des BitLocker-Schlüssels (Surface Hub)
description: Jedes Microsoft Surface Hub-Gerät wird automatisch mit BitLocker-Laufwerkverschlüsselungssoftware eingerichtet. Microsoft empfiehlt, die BitLocker-Wiederherstellungsschlüssel unbedingt zu sichern.
ms.assetid: E11E4AB6-B13E-4ACA-BCE1-4EDC9987E4F2
ms.reviewer: ''
manager: laurawi
keywords: Surface Hub, BitLocker, Bitlocker-Wiederherstellungsschlüssel
ms.prod: surface-hub
ms.sitesec: library
author: dansimp
ms.author: dansimp
ms.topic: article
ms.date: 07/08/2019
ms.localizationpriority: medium
ms.openlocfilehash: 73efa418fa80ef90a643d4fb4c457280ab982b38
ms.sourcegitcommit: 109d1d7608ac4667564fa5369e8722e569b8ea36
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/27/2020
ms.locfileid: "10833865"
---
# Speichern des BitLocker-Schlüssels (Surface Hub)


Jedes Microsoft Surface Hub-Gerät wird automatisch mit BitLocker-Laufwerkverschlüsselungssoftware eingerichtet. Microsoft empfiehlt, die BitLocker-Wiederherstellungsschlüssel unbedingt zu sichern.

Es gibt verschiedene Möglichkeiten, den BitLocker-Schlüssel auf dem Surface Hub zu verwalten.

1.  Wenn Sie den Surface Hub mit einer Domäne verbunden haben, sichert das Gerät den Schlüssel in der Domäne und speichert ihn im Computerobjekt.

    Wenn Sie den BitLocker-Schlüssel nach dem Verbinden des Geräts mit einer Domäne nicht finden, unterstützt das Active Directory-Schema die BitLocker-Schlüsselsicherung wahrscheinlich nicht. Wenn Sie das Schema nicht ändern möchten, können Sie den BitLocker-Schlüssel speichern, indem Sie unter „Einstellungen“ die Vorgehensweise für die Verwendung eines lokalen Administratorkontos ausführen, die später in dieser Liste beschrieben wird.

2.  Wenn Sie den Surface Hub mit Azure Active Directory (Azure AD) verbunden haben, wird der BitLocker-Schlüssel in dem Konto gespeichert, das zum Verknüpfen des Geräts verwendet wurde.

3.  Wenn Sie ein lokales Administratorkonto zum Verwalten des Geräts verwenden, können Sie den BitLocker-Schlüssel speichern, indem Sie zur **Einstellungs** -App wechseln und zur **Aktualisierung & Sicherheits** &gt; **Wiederherstellung**navigieren. Schließen Sie ein USB-Laufwerk an, und wählen Sie die Option zum Speichern des BitLocker-Schlüssels aus. Der Schlüssel wird in einer Textdatei auf dem USB-Laufwerk gespeichert.


##  <a name="related-content"></a>Verwandte Themen

[Verwalten von Microsoft Surface Hub](manage-surface-hub.md)

[Microsoft Surface Hub-Administratorhandbuch](surface-hub-administrators-guide.md)

 

 





