---
title: Bereitstellen von Apps für Surface Hub 2S mithilfe von Intune
description: Erfahren Sie, wie Sie Apps auf Surface Hub 2S mithilfe von InTune bereitstellen können.
keywords: Trennen Sie Werte durch Kommata
ms.prod: surface-hub
ms.sitesec: library
author: greg-lindsay
ms.author: greglin
manager: laurawi
audience: Admin
ms.topic: article
ms.date: 06/20/2019
ms.localizationpriority: Medium
ms.openlocfilehash: 51e54a5b2881519f2fc361675253c9e50bad0864
ms.sourcegitcommit: 109d1d7608ac4667564fa5369e8722e569b8ea36
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/27/2020
ms.locfileid: "10833283"
---
# Bereitstellen von Apps für Surface Hub 2S mithilfe von Intune

Sie können zusätzliche apps installieren, um den Anforderungen Ihres Teams oder Ihrer Organisation zu entsprechen.

##  <a name="developer-guidelines"></a>Richtlinien für Entwickler

- Surface Hub führt ausschließlich [Apps für die universelle Windows-Plattform (UWP)](https://msdn.microsoft.com/windows/uwp/get-started/whats-a-uwp) aus. Apps, die mit [Desktop App Converter](https://docs.microsoft.com/windows/uwp/porting/desktop-to-uwp-run-desktop-app-converter) erstellt wurden, führen Surface Hub nicht aus.
- Die Apps müssen für die [universelle Gerätefamilie](https://msdn.microsoft.com/library/windows/apps/dn894631) oder die Windows Team-Gerätefamilie entwickelt worden sein.
- Surface Hub unterstützt nur [Offline lizenzierte apps](https://docs.microsoft.com/microsoft-store/distribute-offline-apps) aus dem [Microsoft Store for Business](https://businessstore.microsoft.com/store).
- Standardmäßig gilt, dass Apps Store-signiert sein müssen, um installiert werden zu können. Während Test und Entwicklung können Sie auch entwicklersignierte UWP-Apps ausführen, indem Sie das Gerät im Entwicklermodus ausführen.
- Beim entwickeln und Übermitteln von apps an den Microsoft Store legen Sie die Optionen für die Verfügbarkeit von Gerätefamilien und die organisatorische Lizenzierung fest, um sicherzustellen, dass Apps für die Ausführung auf Surface Hub verfügbar sind.
- Sie benötigen Administratoranmeldeinformationen, um apps auf Surface Hub zu installieren. Surface Hub wurde für die Verwendung in Besprechungsräumen und anderen freigegebenen Räumen entwickelt und verhindert, dass reguläre Benutzer auf den Microsoft Store zugreifen, um apps herunterzuladen und zu installieren.

##  <a name="deployment-guidelines"></a>Bereitstellungsrichtlinien

Sie können UWP-Apps (universelle Windows-Plattform) für die Oberfläche von Hub 2S mithilfe von InTune bereitstellen, um die APP-Bereitstellung auf Geräten zu vereinfachen.

1. Wenn Sie apps bereitstellen möchten, aktivieren Sie MDM für Ihre Organisation. Wählen Sie im InTune-Portal **InTune** als ihre MDM-Autorität (empfohlen) aus. <br>

    ![Wählen Sie MDM Authority aus.](images/sh2-set-intune5.png)

2. Aktivieren Sie den Microsoft Store for Business in InTune. Öffnen Sie InTune, und wählen Sie **Client**  >  **-Apps Microsoft Store for Business aus.** <br>

    ![Aktivieren von Store for Business](images/sh2-deploy-apps-sync.png)

3. Öffnen Sie in InTune **Microsoft Store for Business** , und wählen Sie **Einstellungen**  >  **Distribute**  >  **Management Tools**aus. Wählen Sie **Microsoft InTune** als Verwaltungstool aus. <br>

    ![Hinzufügen von InTune als Verwaltungstool](images/sh2-set-intune8.png)

4. Wählen Sie in Microsoft Store für Unternehmen die Option **Einstellungen**  >  **Shop**  >  **Shopping Experience**aus, und wählen Sie dann **Offline-Apps anzeigen**aus. Offline-Apps beziehen sich auf apps, die mit InTune synchronisiert und zentral auf einem Gerät bereitgestellt werden können.
5. Nach dem Aktivieren des Offline Einkaufs können Sie offline Lizenzen für apps erwerben, die Sie mit InTune synchronisieren und als Geräte Lizenzierung bereitstellen können.
6. Wählen Sie in **InTune**  >  -**Client-apps**  >  **Microsoft Store für Unternehmen**die Option **Synchronisieren**aus.
7. Suchen Sie auf der Seite Client-apps in der Liste apps nach der app. Weisen Sie die apps der gewünschten Gerätegruppe oder den gewünschten Gruppen zu. Wählen Sie **Zuordnungen**  >  **Gruppe hinzufügen**aus. <br>

![* Zuweisen von apps zu Gruppen *](images/sh2-assign-group.png) <br>

8. Wählen Sie unter Zuordnungstyp die Option **erforderlich**aus. <br>

![* Zuweisen von apps zu Gruppen *](images/sh2-add-group.png) <br>

9. Wählen Sie für die ausgewählten Gruppen die Option **Geräte Lizenzierung** aus, und wählen Sie dann **OK** aus, und speichern Sie die Aufgabe. <br>
 
![* Zuweisen von apps zu Gruppen *](images/sh2-apps-assign.png)
