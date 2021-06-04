---
title: Optimieren der WLAN-Konnektivität für Surface-Geräte
description: In diesem Thema werden die empfohlenen Wi-Fi beschrieben, um sicherzustellen, dass die Geräte von Surface in überlasteten Netzwerkumgebungen und mobilen Szenarien verbunden bleiben.
ms.prod: w10
ms.mktglfcycl: manage
ms.sitesec: library
author: coveminer
ms.audience: itpro
ms.localizationpriority: medium
ms.author: greglin
ms.topic: article
ms.reviewer: tokatz
manager: laurawi
ms.date: 01/15/2021
ms.openlocfilehash: 69ca7bc7383a122dfd4f069135319b92ff7edfb0
ms.sourcegitcommit: 1053479c191fd10651d31a466fad1769fb0cd28b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/16/2021
ms.locfileid: "11271379"
---
# Optimieren der WLAN-Konnektivität für Surface-Geräte


Um mit der Akkulaufzeit des ganzen Tages in Verbindung zu bleiben, implementieren die Surface-Geräte Drahtlosverbindungseinstellungen, die Leistung und Leistungssteigerungen ausgleichen. Außerhalb der anspruchsvollesten Mobilitätsszenarien können Benutzer eine ausreichende Drahtlose Konnektivität beibehalten, ohne den Standardnetzwerkadapter oder die zugehörigen Einstellungen zu ändern. Auf dieser Seite werden wichtige Überlegungen zur Drahtlosen Konnektivität in mobilen Szenarien mit den neuesten Surface-Geräten wie Surface Pro 7 und höher, Surface Laptop Go, Surface Go 2, Surface Pro X, Surface Laptop 3, Surface Book 3 und Surface Pro 7 beschrieben.

##  <a name="prerequisites"></a>Voraussetzungen

In diesem Dokument wird davon ausgegangen, dass Sie erfolgreich ein Drahtlosnetzwerk bereitgestellt haben, das 802.11n (WLAN 4) oder höher gemäß den Empfehlungen führender Gerätehersteller unterstützt.

##  <a name="configuring-access-points-for-optimal-roaming-capabilities"></a>Konfigurieren von Zugriffpunkten für optimale Roamingfunktionen

Wenn Sie ein Drahtlosnetzwerk verwalten, auf das normalerweise von vielen verschiedenen Clientgerätentypen zugegriffen wird, wird empfohlen, bestimmte Protokolle für Zugriffspunkte (Access Points, APs) in Ihrem WLAN zu aktivieren, wie in Fast Roaming mit [802.11k, 802.11v und 802.11r](https://docs.microsoft.com/windows-hardware/drivers/network/fast-roaming-with-802-11k--802-11v--and-802-11r)beschrieben. Surface-Geräte können die folgenden Drahtlosprotokolle nutzen:

- **802.11r.** "Schneller**BSS-Übergang"** beschleunigt die Verbindung mit neuen Funkzugriffspunkten, indem die Anzahl der frames reduziert wird, die erforderlich sind, bevor Ihr Gerät auf einen anderen AP zugreifen kann, während Sie sich mit Ihrem Gerät bewegen. In der neuen Generation von Surface-Geräten, die seit 2019 veröffentlicht wurden, können Endbenutzer Zugriff auf Einstellungen für die Roaming-Aggressivität auf ihrem Gerät erhalten. Auch wenn das Ändern von Standardeinstellungen nicht empfohlen wird, sollten Benutzer diese Funktion kennen und wissen, wie sich bestimmte Einstellungen auf ihre Fähigkeit auswirken können, verbunden zu bleiben.
- **802.11k.** **"Neighbor Reports"** stellt Geräten Informationen zu aktuellen Bedingungen an benachbarten Zugriffpunkten zur Verfügung. Es kann Ihrem Surface-Gerät helfen, den besten AP mit anderen Kriterien als der Signalstärke wie z. B. ap-Auslastung zu wählen.

Bestimmte Surface-Geräte können auch 802.11v "BSS Transition Management Frames" verwenden, die ähnlich wie 802.11k bei der Bereitstellung von Informationen zu Kandidaten-APs in der Nähe verwendet werden. Dazu gehören Surface Pro 7+, Surface Go, Surface Go 2, Surface Pro 7, Surface Pro X und Surface Laptop 3. 

##  <a name="managing-user-settings"></a>Verwalten von Benutzereinstellungen

Sie können optimale Roamingfunktionen über ein gut entworfenes Netzwerk erreichen, das 802.11r und 802.11k über alle Zugriffspunkte hinweg unterstützt. Es wird empfohlen, nicht zu versuchen, Benutzereinstellungen auf einzelnen Geräten zu verwalten, um sicherzustellen, dass Ihr Netzwerk ordnungsgemäß konfiguriert ist, um Benutzern eine optimale Drahtloserfahrung zu bieten. 

###  <a name="recommended-user-settings-and-best-practices"></a>Empfohlene Benutzereinstellungen und bewährte Methoden

In bestimmten Situationen kann das Ändern erweiterter Netzwerkadaptereinstellungen, die in die Geräte von Surface integrierte sind, eine zuverlässigere Verbindung erleichtern. Bedenken Sie jedoch, dass eine Verbindung mit Drahtlosressourcen häufiger aufgrund eines Problems mit Zugriffspunkt, Netzwerkentwurfsfehlern oder Umgebungsstandorten nicht hergestellt werden kann.

> [!NOTE]
> Die Art und Weise, wie Surface Pro Oder Surface Go halten, kann sich auch auf die Signalstärke auswirken. Wenn Sie einen Bandbreitenverlust haben, überprüfen Sie, ob Sie den oberen Rand der Anzeige, in der sich der Wi-Fi befindet, nicht halten. Auch wenn das Halten des oberen Bildschirms keine Drahtlosen Signale blockiert, kann es dazu kommen, dass der Gerätetreiber Änderungen initiiert, die die Konnektivität reduzieren.

###  <a name="keep-default-auto-setting-for-dual-bandwidth-capability"></a>Behalten Sie die Standardeinstellung "Automatisch" für die Dualbandbreite bei

Auf den meisten Surface-Geräten können Sie die Einstellungen des Clientnetzwerkadapters so konfigurieren, dass nur eine Verbindung mit drahtlosen APs über 5 GHz hergestellt wird, nur eine Verbindung über 2,4 GHz hergestellt wird oder das Betriebssystem die beste Option auswählen kann (Automatische Standardeinstellung).

**Gehen Sie zum Zugreifen auf die Netzwerkadaptereinstellungen zu:**

- **Start**  >  **Systemsteuerung**  >  **Netzwerk- und Freigabecenter**  >  **Ihr Wi-Fi Adapter**  >  **Eigenschaften**  >  **Konfigurieren**  >  **Erweitert**.

![* Wifi-Band-Einstellungen*](images/wifi-band.png) <br>

Beachten Sie, dass 2,4 GHz einige Vorteile gegenüber 5 GHz bietet: Es erweitert sich weiter und lässt sich leichter durch Wände oder andere vollfarbige Objekte dringen. Es wird empfohlen, die Bandeinstellung im Standardzustand zu be lassen, um mögliche nachteilige Folgen zu vermeiden, es sei denn, Sie verfügen über einen eindeutigen Verwendungsfall, der eine Verbindung mit 5 GHz garantiert. Zum Beispiel:


- Viele Hotspots in Hotels, Cafés und Flughäfen verwenden immer noch nur 2,4 GHz, was den Zugriff auf Geräte effektiv blockiert, wenn Band nur auf 5 GHz festgelegt ist.
- Da für drahtlose Miracast-Anzeigeverbindungen der erste Handshake über 2,4-GHz-Kanäle abgeschlossen werden muss, können Geräte keine Verbindung nur mit 5 GHz herstellen.

> [!NOTE]
> Standardmäßig verwenden Surface-Geräte eine Verbindung mit 5 GHz, wenn verfügbar. Um jedoch den Strom in einem niedrigen Akkuzustand zu erhalten, sucht Surface zunächst nach einer 2,4-GHz-Verbindung.

Sie können die Bandeinstellung auch entsprechend Ihrer Umgebung umschalten. Beispielsweise profitieren Benutzer, die in Gebäuden mit hoher Dichte mit mehreren Wi-Fi-Hotspots leben , die alle Überträgt über 2,4 GHz übertragen, wahrscheinlich davon, dass ihr Surface Gerät nur auf 5 GHz und bei Bedarf auf Auto zurückgesetzt wird.

###  <a name="roaming-aggressiveness-settings-on-surface-devices-with-intel-adapters"></a>Roaming-Aggressivitätseinstellungen auf Surface-Geräten mit Intel-Adaptern 

Benutzer möchten möglicherweise einen Schwellenwert für die Signalstärke auswählen, mit dem das Gerät aufgefordert wird, nach einem neuen Zugriffspunkt zu suchen, wenn das Signal abstürzt (Roaming-Aggressivität). Standardmäßig versuchen Surface-Geräte mit Intel-Adaptern, das Roaming zu einem neuen Zugriffspunkt zu versuchen, wenn die Signalstärke unter **"Mittel"** (72 Prozent Signalstärke) fällt. Beachten Sie auch, dass Organisationen zwecksgef?hnte Drahtlosprotokolle über mehrere Netzwerkzugriffspunkte hinweg implementieren können, um roamingüberlastete Netzwerkumgebungen zu vereinfachen, wie weiter oben auf dieser Seite erläutert. 

Während eine höhere Roaming-Aggressivität über **"Medium"** zu einer verbesserten Konnektivität in stark überlasteten Geschäfts- oder Privatumgebungen führen kann, kann dies zu einer beeinträchtigten Konnektivität führen, wenn sie außerhalb dieser Umgebungen abgestuft wird. 

Es wird empfohlen, die Einstellung für die Aggressivität des Roamings im Standardzustand zu be lassen, es sei denn, in bestimmten mobilen Szenarien konnektivitätsprobleme auftreten, z. B. die Durchführung von Standortuntersuchungen in der Umgebung und gleichzeitig die Aufrechterhaltung der Sprach- und Videokonnektivität während einer Konferenzbesprechung. Wenn Sie keine Verbesserung bemerken, kehren Sie zum Standardzustand "Mittel" zurück. Beachten Sie: Wenn Sie die Roaming aggressiver machen, beschleunigen Sie auch den Akkuverbrauch. 

**So aktivieren Sie die Roaming-Aggressivität auf Surface:**

1. Wechseln Sie zu **"Geräte-Manager**  >  **starten".**
2. Wählen **Sie unter Netzwerkadapter** **Intel Wi-Fi 6** aus, und klicken Sie dann mit der rechten Maustaste auf **"Eigenschaften".**
3. Wählen Sie die **Registerkarte "Erweitert"** aus.
4. Wählen **Sie "Roaming-Aggressivität"** aus, und wählen Sie ihren bevorzugten Wert aus dem Dropdownmenü aus.

![* Roaming-Aggressivitätseinstellungen-Intel *](images/wifi-roaming-int.png) <br>

###  <a name="roaming-aggressiveness-settings-on-surface-go-and-surface-pro-x"></a>Einstellungen für die Roaming-Aggressivität auf Surface Go und Surface Pro X

Front-Line-Mitarbeiter, die Surface Go verwenden, möchten möglicherweise einen Schwellenwert für die Signalstärke auswählen, der das Gerät dazu veranlasst, nach einem neuen Zugriffspunkt zu suchen, wenn die Signalstärke abstürzt (Roaming-Aggressivität). Standardmäßig versuchen Surface-Geräte, ein Roam zu einem neuen Zugriffspunkt zu verwenden, wenn die Signalstärke unter **"Mittel"** (50 Prozent Signalstärke) fällt. Beachten Sie, dass Sie immer dann, wenn Sie die Aggressivität des Roamings erhöhen, den Akkuverbrauch beschleunigen.

Lassen Sie die Einstellung für die Roaming-Aggressivität im Standardzustand, es sei denn, in bestimmten mobilen Szenarien stoßen Sie auf Konnektivitätsprobleme, wie z. B. die Durchführung von Standortuntersuchungen in der Umgebung und gleichzeitig die Aufrechterhaltung der Sprach- und Videokonnektivität während einer Konferenzbesprechung. Wenn Sie keine Verbesserung bemerken, wird der Standardzustand **"Mittel"** wiederhergestellt.

**So aktivieren Sie die Roaming-Aggressivität auf Surface Go:**

1. Wechseln Sie **zu "Start > Systemsteuerungsnetzwerk**  >  **und**  >  **Internetnetzwerk und Freigabecenter".**
2. Wählen **Sie** unter **"Verbindungen" WLAN und** dann **"Eigenschaften" aus.**
3. Wählen Sie **"Client für Microsoft Networks"** und dann **"Konfigurieren" aus.**
4. Wählen **Sie advanced**Roaming  >  **Aggressiveness** aus, und wählen Sie ihren bevorzugten Wert aus dem Dropdownmenü aus.

![* Roaming aggressiveness settings-QualComm *](images/wifi-roaming.png) <br>


##  <a name="conclusion"></a>Fazit

Surface Geräte sind mit Standardeinstellungen für eine optimale Drahtlose Konnektivität ausgelegt, während gleichzeitig die Akkulaufzeit erhalten bleiben muss. Die effektivste Möglichkeit, zuverlässige Verbindungen für Surface-Geräte zu ermöglichen, ist ein gut entworfenes Netzwerk, das 802.11r und 802.11k unterstützt. Benutzer können die Netzwerkadaptereinstellungen oder die Aggressivität des Roamings anpassen, sollten dies jedoch nur als Reaktion auf bestimmte Umgebungsfaktoren tun und den Standardzustand wiederherstellen, wenn keine spürbare Verbesserung vor sich geht.
