---
title: Verwalten von Windows-Updates auf Surface Hub
description: Beschreibt bewährte Methoden zum Verwalten von Updates auf dem Microsoft Surface Hub oder Surface Hub 2S.
ms.assetid: A737BD50-2D36-4DE5-A604-55053D549045
ms.reviewer: ''
manager: laurawi
keywords: Verwalten von Windows-Updates, Surface Hub, Windows Server Update Services
ms.prod: surface-hub
ms.sitesec: library
author: dansimp
ms.author: dansimp
ms.topic: article
ms.date: 10/27/2020
ms.localizationpriority: medium
ms.openlocfilehash: e5ffefa44560d01135b3ac656d9357f1115110ba
ms.sourcegitcommit: d60f82d9d22fe118f9c8dc24458d2c144b138eb8
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/17/2020
ms.locfileid: "11174725"
---
# Verwalten von Windows-Updates auf Surface Hub

Neue Versionen des Surface Hub-Betriebssystems werden über Windows Update veröffentlicht, genau wie Versionen von Windows10. Auf dieser Seite werden bewährte Methoden zum Verwalten von Updates für Surface-Hub-Geräte erläutert. 

##  <a name="windows-update-for-business"></a>Windows Update for Business

Windows Update for Business ist eine Reihe von Features, die Unternehmen eine zusätzliche Kontrolle darüber bieten, wie und wann Windows Updateversionen installiert, während die Geräte Verwaltungskosten reduziert werden. Bei Verwendung dieser Methode werden Surface Hub-Geräte direkt mit dem Windows Update-Dienst von Microsoft verbunden.

- Empfangen von Updates direkt vom Windows Update-Dienst von Microsoft, ohne dass zusätzliche Infrastruktur erforderlich ist. 
- Rückstellung von Updates, um zusätzliche Zeit für Tests und Evaluierung bereitzustellen. 
- Bereitstellen von Updates für bestimmte Gruppen von Geräten. 
- Definieren von Wartungsfenstern für die Installation von Updates. 

> [!TIP]
> Verwenden Sie die Peer-to-Peer-Inhaltsfreigabe, um Bandbreitenprobleme während Aktualisierungen zu reduzieren. Details hierzu finden Sie unter [Optimieren der Updatebereitstellung für Windows10-Updates](https://technet.microsoft.com/itpro/windows/manage/waas-optimize-windows-10-updates).

> [!NOTE]
> Surface Hub unterstützt zurzeit das Zurücksetzen von Updates nicht.


##  <a name="surface-hub-servicing-model"></a>Surface Hub-Wartungsmodell

Surface Hub verwendet das Windows10-Wartungsmodell, das als [Windows as a Service (WaaS)](https://docs.microsoft.com/windows/deployment/update/waas-overview) bezeichnet wird. Herkömmlicherweise werden neue Features nur in neuen Versionen von Windows hinzugefügt, die in Abständen von einigen Jahren veröffentlicht werden. Jede neue Version erforderte langwierige und kostspielige Bereitstellungsvorgänge in Unternehmen. Dies führte dazu, dass Endbenutzer und Unternehmen die Vorteile von Innovationen häufig nicht nutzten. Das Ziel von Windows as a Service besteht darin, kontinuierlich neue Funktionen bereitzustellen und gleichzeitig eine hohe Qualität zu wahren.

Microsoft veröffentlicht allgemein kontinuierlich zwei Arten von Surface Hub-Versionen:
- **Featureupdates** – Updates, mit denen die neuesten Features, Umgebungen und Funktionen installiert werden Microsoft rechnet mit der Veröffentlichung von zwei neuen Funktionsupdates pro Jahr.
- **Qualitätsupdates** – Updates, bei denen der Schwerpunkt auf der Installation von Sicherheitspatches, Treibern und anderen Wartungsaktualisierungen liegt. Microsoft geht davon aus, ein kumulatives Qualitätsupdate pro Monat zu veröffentlichen.

Um die Versionsqualität zu verbessern und die Bereitstellung zu vereinfachen, werden alle neuen Versionen kumulativ sein, die Microsoft für Windows10 einschließlich Surface Hub veröffentlicht. Dies bedeutet, dass Feature- und Qualitätsupdates die Nutzlast aller vorherigen Versionen enthalten (in optimierter Form, um Speicherplatz zu sparen und Netzwerkanforderungen zu berücksichtigen) und die Installation der Version auf einem Gerät dieses vollständig aktualisiert. Anders als bei früheren Versionen von Windows ist es nicht möglich, lediglich einen Teil eines Qualitätsupdates für Windows10 zu installieren. Wenn zum Beispiel ein Qualitätsupdate Patches für drei Sicherheitsrisiken und ein Zuverlässigkeitsproblem enthält, führt die Bereitstellung der Aktualisierung zur Installation von allen vier Patches.

Das Surface Hub-Betriebssystem empfängt Updates über den [Semi-Annual Channel](https://docs.microsoft.com/windows/deployment/update/waas-overview#naming-changes). Wie andere Editionen von Windows 10 ist die Wartungs Lebensdauer endlich. Sie müssen auf Computern mit diesen Branches neue Featureupdates installieren, um weiterhin Qualitätsupdates zu erhalten.

Weitere Informationen zu Windows as a Service finden Sie unter [Übersicht über Windows as a Service](https://technet.microsoft.com/itpro/windows/manage/waas-overview).


##  <a name="use-windows-update-for-business"></a>Verwenden von Windows Update for Business

Surface Hub-Geräte enthalten, wie alle Windows10-Geräte, **Windows Update for Business (WUfB)**, damit Sie steuern können, wie Ihre Geräte aktualisiert werden. Windows Update for Business hilft, die Kosten für die Geräteverwaltung zu reduzieren, die Kontrolle über die Bereitstellung von Updates zu wahren, einen schnelleren Zugriff auf Sicherheitsupdates zu erhalten und kontinuierlich die neuesten Innovationen von Microsoft bereitzustellen. Weitere Informationen finden Sie unter [Verwalten von Updates mit Windows Update for Business](https://technet.microsoft.com/itpro/windows/manage/waas-manage-updates-wufb).

**So richten Sie Windows Update for Business ein**
1. [Gruppieren von Surface Hub in Bereitstellungsringe](#group-surface-hub-into-deployment-rings)
2. [Konfigurieren des Zeitpunkts, an dem Surface Hub Updates empfängt](#configure-when-surface-hub-receives-updates).

> [!NOTE]
> Sie können Microsoft InTune, Microsoft Endpoint Configuration Manager oder einen unterstützten MDM-Anbieter von Drittanbietern verwenden, um WUfB einzurichten. [Exemplarische Vorgehensweise: Konfigurieren von Windows Update for Business mit Microsoft Intune](https://docs.microsoft.com/windows/deployment/update/waas-wufb-intune)


### Gruppieren von Surface Hub in Bereitstellungsringe

Verwenden Sie Bereitstellungsringe, um zu steuern, wann Updates auf Surface Hub-Geräten installiert werden, damit Sie Zeit für deren Prüfung haben. Beispielsweise können Sie einen kleinen Pool von Geräten zuerst aktualisieren, um die Qualität zu überprüfen, bevor Sie das Update umfassender für Ihr Unternehmen bereitstellen. Abhängig davon, wer die Surface Hub-Geräte in Ihrer Organisation verwaltet, sollten Sie die Integration von Surface Hub in die Bereitstellungsringe in Betracht ziehen, die Sie für andere Windows10-Geräten erstellt haben. Weitere Informationen zu Bereitstellungsringen finden Sie unter [Erstellen von Bereitstellungsringen für Windows10-Updates](https://technet.microsoft.com/itpro/windows/manage/waas-deployment-rings-windows-10-updates).

Beispiele für Bereitstellungs Ringe finden Sie in der folgenden Tabelle.

| Bereitstellungsring | Ringgröße | Wartungszweig | Rückstellung für Featureupdates | Rückstellung für Qualitätsupdates (Sicherheitsupdates, Treiber und andere Updates) | Überprüfungsschritt |
| --------- | --------- | --------- | --------- | --------- | --------- |
| Vorschau (z.B. nicht kritisch oder Testgeräte) | Klein | Windows Insider Preview | Keine  | Keine  | Manuelles Testen und Evaluieren neuer Funktionen. Unterbrechen von Updates bei Problemen. |
| Version (z.B. Geräte, die von bestimmten Teams verwendet werden) | Mittel | Semi-Annual Channel  | Keine | Keine  | Überwachen von Gerätenutzung und Benutzerfeedback. Unterbrechen von Updates bei Problemen. |
| Umfassende Bereitstellung (z.B. auf der Mehrzahl der Geräte in Ihrer Organisation) | Groß | Semi-Annual Channel |  120Tage nach Veröffentlichung. | 7-14Tage nach Veröffentlichung. | Überwachen von Gerätenutzung und Benutzerfeedback. Unterbrechen von Updates bei Problemen. |
| Unternehmenskritisch (z.B. Geräte Besprechungsräumen von Führungskräften) | Klein | Semi-Annual Channel |  180Tage nach der Veröffentlichung (maximale Rückstellung für Featureupdates). | 30Tage nach der Veröffentlichung (maximale Rückstellung für Qualitätsupdates). | Überwachen von Gerätenutzung und Benutzerfeedback. |


### Konfigurieren des Zeitpunkts, an dem Surface Hub Updates empfängt

Nachdem Sie Bereitstellungsringe für die Surface Hub-Geräte festgelegt haben, konfigurieren Sie für die einzelnen Ringe Rückstellungsrichtlinien für Updates:
- Um Featureupdates zurückzustellen, legen Sie eine entsprechende [Update/DeferFeatureUpdatesPeriodInDays](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-update#update-deferfeatureupdatesperiodindays)-Richtlinie für jeden Ring fest.
- Um Qualitätsupdates zurückzustellen, legen Sie eine entsprechende [Update/DeferQualityUpdatesPeriodInDays](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-update#update-deferqualityupdatesperiodindays)-Richtlinie für jeden Ring fest.

> [!NOTE]
> Bei Problemen während des Updaterollouts können Sie Updates mit [Update/PauseFeatureUpdates](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-update#update-pausefeatureupdates) und [Update/PauseQualityUpdates](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-update#update-pausequalityupdates) unterbrechen.

**Wenn Sie über einen Proxyserver oder mit einer anderen Methode URLs blockieren**

Fügen Sie der Liste "zulassen" die folgenden Windows Update-URLs für vertrauenswürdige Websites hinzu:
- `http(s)://*.update.microsoft.com`
- `http://download.windowsupdate.com` 
- `http://windowsupdate.microsoft.com`

Sobald das Windows10 Team Anniversary Update installiert ist, können Sie diese Adressen entfernen, um den vorherigen Zustand Ihres Surface Hub wiederherzustellen.

## Wartungsfenster

Um sicherzustellen, dass das Gerät während der Geschäftszeiten stets zur Verfügung steht, führt Surface Hub Verwaltungsfunktionen in einen angegebenen Wartungsfenster aus. Während des Wartungsfensters installiert der Surface Hub automatisch Updates über Windows Update und startet das Gerät 20 Minuten vor dem Ende des Fensters neu.

Surface Hub befolgt für die Anwendung von Updates die folgenden Richtlinien:
- Das Update wird während des nächsten Wartungsfensters installiert. Wenn der Start einer Besprechung während eines Wartungsfensters geplant ist, oder die Surface Hub-Sensoren erkennen, dass das Gerät verwendet wird, wird das ausstehende Update zum folgenden Wartungsfenster verschoben.
- Wenn das nächste Wartungsfenster nach dem zulässigen Zeitraum für die Installation des Updates liegt, berechnet das Gerät den nächsten verfügbaren freien Zeitraum während der Geschäftszeiten mithilfe der anhand der Updatemetadaten geschätzten Installationszeit. Das Update wird erneut verschoben, wenn eine Besprechung geplant ist oder die Surface Hub-Sensoren erkennen, dass das Gerät verwendet wird.
- Wenn das nächste Wartungsfenster **nicht** über die Kulanzzeit des Updates hinausgeht, verschiebt der Surface-Hub das Update weiterhin.
- Wenn ein Neustart erforderlich ist, wird der Surface Hub automatisch während des nächsten Wartungsfensters neu gestartet.

> [!NOTE]
> Lassen Sie bei der Ersteinrichtung des Surface Hub genügend Zeit für Updates. Möglicherweise sind neue Virusdefinitionen verfügbar, die sofort installiert werden sollten.

Für alle neuen Surface Hub-Geräte ist ein Standardwartungsfenster festgelegt:
-   **Startzeit:** 2:00 am
-   **Dauer:** 2 Stunden

**So ändern Sie das Standardwartungsfenster manuell**
1.  Öffnen Sie auf dem Surface Hub **Einstellungen**.
2.  Navigieren Sie zu **Update und Sicherheit** > **Windows Update** > **Erweiterte Optionen**.
3.  Wählen Sie unter **Wartungsstunden** **Ändern** aus.

Wenn Sie das Wartungsfenster mithilfe von MDM ändern möchten, setzen Sie den **MaintenanceHoursSimple** -Knoten im [SurfaceHub-Konfigurationsdienst Anbieter](https://msdn.microsoft.com/library/windows/hardware/mt608323.aspx). Weitere Details hierzu finden Sie unter [Verwalten von Einstellungen mit einem MDM-Anbieter](manage-settings-with-mdm-for-surface-hub.md).


##  <a name="additional-information"></a>Weitere Informationen

- [Blog Beitrag: warten, flighten und Verwalten von Updates für Surface Hub (natürlich mit InTune!)](https://blogs.technet.microsoft.com/y0av/2018/05/31/7-3/)


##  <a name="related-content"></a>Verwandte Themen

[Verwalten von Microsoft Surface Hub](manage-surface-hub.md)

[Microsoft Surface Hub-Administratorhandbuch](surface-hub-administrators-guide.md)

