---
title: Verwenden der Cloud-Wiederherstellung für BitLocker auf einem Surface Hub
description: Verwenden der Cloud-Wiederherstellung für BitLocker auf einem Surface Hub
ms.assetid: c0bde23a-49de-40f3-a675-701e3576d44d
keywords: Barrierefreiheiteinstellungen, Einstellungs-App, Erleichterte Bedienung
ms.prod: surface-hub
ms.sitesec: library
author: v-miegge
ms.author: v-miegge
ms.topic: article
ms.localizationpriority: medium
ms.openlocfilehash: 7912f9d1bab2ba625995c56d6d7da4e6b2d3df37
ms.sourcegitcommit: 109d1d7608ac4667564fa5369e8722e569b8ea36
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/27/2020
ms.locfileid: "10832671"
---
# Zusammenfassung

In diesem Artikel wird beschrieben, wie Sie die Cloud-Wiederherstellungsfunktion verwenden, wenn Sie unerwartet von BitLocker auf einem Surface Hub-Gerät dazu aufgefordert werden.

> [!NOTE]
> Führen Sie die folgenden Schritte nur aus, wenn ein BitLocker-Wiederherstellungsschlüssel nicht verfügbar ist.

> [!WARNING]
> * Durch diesen Wiederherstellungsprozess werden die Inhalte des internen Laufwerks gelöscht. Wenn der Prozess fehlschlägt, wird das interne Laufwerk vollständig unbrauchbar. In diesem Fall müssen Sie bei Microsoft eine Serviceanfrage für eine Lösung protokollieren.
> * Nachdem der Wiederherstellungsvorgang abgeschlossen ist, wird das Gerät auf die Werkseinstellungen zurückgesetzt und wieder in den Zustand "außerhalb des Felds" zurückgesetzt.
> * Nach der Wiederherstellung muss der Surface-Hub vollständig neu konfiguriert werden.

> [!IMPORTANT]
> Dieser Vorgang erfordert eine offene Internet Verbindung, die keinen Proxy oder eine andere Authentifizierungsmethode verwendet.

##  <a name="cloud-recovery-process"></a>Cloud-Wiederherstellungsprozess

Führen Sie die folgenden Schritte aus, um eine Cloud-Wiederherstellung durchzuführen:

1. Wählen Sie **ESC, um weitere Wiederherstellungsoptionen anzuzeigen**.

   ![Screenshot von Escape](images/01-escape.png)

1. Wählen Sie **dieses Laufwerk überspringen**aus.

   ![Screenshot von "dieses Laufwerk überspringen"](images/02-skip-this-drive.png)

1. Wählen Sie **in der Cloud wiederherstellen aus**.

   ![Screenshot der Wiederherstellung aus der Cloud](images/03-recover-from-cloud.png)

1. Wählen Sie **Ja**aus.

   ![Screenshot von "Ja"](images/04-yes.png)

1. Wählen Sie **erneut installieren**aus.

   ![Screenshot der Neuinstallation](images/05a-reinstall.png)

   ![Screenshot des Downloads](images/05b-downloading.png)

1. Nachdem der Cloud-Wiederherstellungsvorgang abgeschlossen ist, starten Sie die Neukonfiguration mithilfe der **out-of-Box-Erfahrung**.

   ![Screenshot von Out-of-the-Box](images/06-out-of-box.png)

##  <a name="something-went-wrong-error-message"></a>Fehlermeldung "etwas ist schief gelaufen"

Dieser Fehler wird in der Regel durch Netzwerkprobleme verursacht, die während des Wiederherstellungs Downloads auftreten. Wenn dieses Problem auftritt, deaktivieren Sie den Hub nicht, da Sie ihn nicht erneut starten können. Wenn diese Fehlermeldung angezeigt wird, kehren Sie zum Schritt "aus der Cloud wiederherstellen" zurück, und starten Sie den Wiederherstellungsprozess erneut.

1. Wählen Sie **Abbrechen**aus.

   ![Screenshot von "Abbrechen"](images/07-cancel.png)

1. Wählen Sie **Problembehandlung**aus.

   ![Screenshot der Problembehandlung](images/08-troubleshoot.png)

1. Wählen Sie **in der Cloud wiederherstellen aus**.

   ![Screenshot der Wiederherstellung aus der Cloud](images/09-recover-from-cloud2.png)

1. Wenn der Fehler " **kabelgebundenes Netzwerk nicht gefunden** " auftritt, wählen Sie **Abbrechen**aus, und lassen Sie den Surface Hub das kabelgebundene Netzwerk wieder entdecken.

   ![Screenshot eines kabelgebundenen Netzwerks wurde nicht gefunden](images/10-cancel.png)