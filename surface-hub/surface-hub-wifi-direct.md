---
title: Wie Surface Hub Wi-Fi Direct-Sicherheitsprobleme behebt
description: Anleitungen zu WLAN-direkten Sicherheitsrisiken.
keywords: Änderungsverlauf
ms.prod: surface-hub
ms.sitesec: library
author: dansimp
ms.author: dansimp
ms.topic: article
ms.date: 11/27/2019
ms.reviewer: ''
manager: laurawi
ms.localizationpriority: medium
ms.openlocfilehash: d877d9b6a4e330a74a9d79cf1150487d89c0da23
ms.sourcegitcommit: 109d1d7608ac4667564fa5369e8722e569b8ea36
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/27/2020
ms.locfileid: "10832767"
---
# Behandlung von Wi-Fi Direct-Sicherheitsproblemen durch Surface Hub

Microsoft Surface Hub ist ein All-in-One-Produktivitätsgerät, mit dem Teams ihr Brainstorming, Zusammenarbeit und Gedankenaustausch verbessern können. Surface Hub basiert auf Miracast für drahtlose Projektion über Wi-Fi Direct.

In diesem Artikel werden die WLAN-direkten Sicherheitsrisiken, die Art und Weise, wie Surface Hub diese Risiken behebt, und die Art und Weise beschrieben, wie Administratoren Surface Hub für höchste Sicherheit konfigurieren können. Mithilfe dieser Informationen können Kunden, die über höchste Sicherheitsanforderungen verfügen, ihre mit dem Surface Hub verbundenen Netzwerke und Daten bei der Übertragung schützen.

Die beabsichtigten Zielgruppen für diesen Artikel sind IT-und Netzwerkadministratoren, die Surface Hub in ihrer Unternehmensumgebung mit optimalen Sicherheitseinstellungen bereitstellen möchten.

##  <a name="overview"></a>Übersicht

Die Sicherheit für Surface Hub hängt umfassend von WLAN-direkt-Miracast und den zugehörigen 802,11-, Wi-Fi Protected Access (WPA2)-und Wireless Protected Setup (WPS)-Standards ab. Da das Gerät nur WPS unterstützt (im Gegensatz zu WPA2-vorinstalliertem Schlüssel [PSK] oder WPA2 Enterprise), werden die Probleme, die häufig mit der 802,11-Verschlüsselung verbunden sind, vereinfacht.

Surface Hub funktioniert auf Augenhöhe mit dem Feld der Miracast-Empfänger. Daher ist es anfällig für einen ähnlichen Satz von Exploits wie alle WPS-basierten drahtlosnetzwerkgeräte. Die Surface Hub-Implementierung von WPS enthält jedoch zusätzliche Vorsichtsmaßnahmen. Darüber hinaus kann die interne Architektur verhindern, dass ein Angreifer, der die Wi-Fi Direct/Miracast-Schicht beeinträchtigt hat, die Netzwerkschnittstelle auf andere Angriffsflächen und verbundene Unternehmensnetzwerke übertragen wird.

##  <a name="wi-fi-direct-background"></a>Wi-Fi Direct-Hintergrund

Miracast ist Teil des Wi-Fi-Anzeigestandards, der vom Wi-Fi Direct-Protokoll unterstützt wird. Diese Standards werden in modernen Mobilgeräten für die Bildschirmfreigabe und Zusammenarbeit unterstützt.

Wi-Fi Direct oder Wi-Fi "Peer-to-Peer" (P2P) ist ein Standard der Wi-Fi-Allianz für "Ad-hoc"-Netzwerke. Unterstützte Geräte können direkt kommunizieren und Gruppen von Netzwerken ohne einen herkömmlichen WLAN-Zugangspunkt oder eine Internet Verbindung erstellen.

Sicherheit für Wi-Fi Direct wird von WPA2 unter dem WPS-Standard bereitgestellt. Der Authentifizierungsmechanismus für Geräte kann eine numerische PIN (WPS-PIN), eine physikalische oder virtuelle Drucktaste (WPS-PBC) oder eine Out-of-Band-Nachricht sein, beispielsweise die Near Field Communication (WPS-OOO). Surface Hub unterstützt sowohl die PIN-Methode als auch die Push-Button-Methode, die die Standardeinstellung ist.

In Wi-Fi Direct werden Gruppen als einer der folgenden Typen erstellt:
- *Persistent*, in der die automatische Wiederherstellung mithilfe von gespeichertem Schlüsselmaterial erfolgen kann
- *Temporär*, in dem Geräte ohne Benutzeraktion nicht erneut authentifiziert werden können

Wi-Fi Direct-Gruppen ermitteln einen *Gruppenbesitzer* (go) über ein Verhandlungsprotokoll, das die Funktionalität "Station" oder "Zugriffspunkt" für die eingerichtete Wi-Fi Direct-Gruppe imitiert. Die Wi-Fi Direct go-Authentifizierung (über eine "interne Registrierungsstelle") ermöglicht die Bereitstellung von Upstream-Netzwerkverbindungen. Für Surface Hub tritt diese go-Aushandlung nicht auf. Das Netzwerk funktioniert nur im "autonomen" Modus, und Surface Hub ist immer der Gruppenbesitzer. Schließlich fügt Surface Hub selbst keine anderen WLAN-direkt Netzwerke als Client hinzu.

##  <a name="how-surface-hub-addresses-wi-fi-direct-vulnerabilities"></a>So behebt Surface Hub WLAN-direkt Anfälligkeiten

**Sicherheitsanfälligkeiten und Angriffe im WLAN-Direct-Einladungs-, Broadcast-und Discovery-Prozess:** WLAN-direkt-Miracast-Angriffe können auf Schwächen in der Gruppeneinrichtung, Peer Discovery, Geräte Übertragung oder Einladungs Prozesse abzielen.

|Wi-Fi-direkt Anfälligkeit | Begrenzung des Oberflächen Hubs |
| --- | --- |
| Der Erkennungsprozess kann über einen längeren Zeitraum aktiv bleiben, wodurch Einladungen und Verbindungen ohne Genehmigung des Geräte Besitzers eingerichtet werden können. | Surface Hub fungiert nur als Gruppenbesitzer, der keine Client Ermittlungs-oder go-Aushandlungsprozesse ausführt. Sie können die drahtlose Projektion vollständig deaktivieren, um die Übertragung zu deaktivieren. |
| Einladung und Erkennung über PBC ermöglicht einem nicht authentifizierten Angreifer, wiederholte Verbindungsversuche durchzuführen, oder nicht authentifizierte Verbindungen werden automatisch akzeptiert. | Durch den Einsatz von WPS-PIN-Sicherheit können Administratoren das Potenzial solcher unbefugten Verbindungen oder "Einladungs Bomben" reduzieren, in denen Einladungen wiederholt gesendet werden, bis ein Nutzer fälschlicherweise einen akzeptiert. |

**WLAN-geschützte Setup (WPS)-Taste Connect (PBC) vs Pin-Eintrag:** Bei der Erstellung und Implementierung von WPS-Pin-Methoden wurden öffentliche Schwächen aufgezeigt. WPS-PBC weist andere Sicherheitsanfälligkeiten auf, die aktive Angriffe auf ein Protokoll ermöglichen, das für die einmalige Verwendung entwickelt wurde.

| Wi-Fi-direkt Anfälligkeit | Begrenzung des Oberflächen Hubs |
| --- | --- |
| WPS-PBC ist anfällig für aktive Angreifer. Die WPS-Spezifikation besagt: "die PBC-Methode hat keine Entropie-Bits und schützt nur vor Angriffen mit passivem lauschen. PBC schützt vor Lauschangriffen und ergreift Maßnahmen um zu verhindern, dass ein Gerät einem Netzwerk beitritt, das nicht vom Gerätebesitzer ausgewählt wurde. Das Fehlen einer Authentifizierung bedeutet jedoch, dass PBC nicht vor aktiven Angriffen schützt. " Angreifer können selektives Wireless-Jamming oder andere Denial-of-Service-Techniken verwenden, um einen unbeabsichtigten Wi-Fi Direct Go oder eine Verbindung auszulösen. Darüber hinaus kann ein aktiver Angreifer, der lediglich die physische Nähe besitzt, wiederholt jede WLAN-direkt Gruppe abreißen und den Angriff versuchen, bis er erfolgreich ist. | Aktivieren Sie die WPS-PIN-Sicherheit in der Surface Hub-Konfiguration. Die Wi-Fi-WPS-Spezifikation besagt: "die PBC-Methode sollte nur verwendet werden, wenn keine PIN-fähige Registrierungsstelle verfügbar ist und der WLAN-Benutzer bereit ist, die mit PBC verbundenen Risiken zu akzeptieren." |
| WPS-Pin-Implementierungen können Brute-Force-Angriffen unterliegen, die auf eine Sicherheitsanfälligkeit im WPS-Standard ausgerichtet sind. Das Design einer Split-Pin-Verifizierung führte in den letzten Jahren zu einer Reihe von Problemen mit der Implementierung von verschiedenen Anbietern von WLAN-Hardware. In 2011 veröffentlichten die Forscher Stefan Viehböck und Craig Heffner Informationen zu dieser Sicherheitsanfälligkeit und Tools wie "Häscher" als Machbarkeitsstudie. |   Die Microsoft-Implementierung von WPS in Surface Hub ändert die PIN alle 30 Sekunden. Um die PIN zu knacken, muss ein Angreifer den gesamten Exploit in weniger als 30 Sekunden abschließen. Angesichts des aktuellen Status von Tools und Recherchen in diesem Bereich ist ein Brute-Force-Pin-Cracking-Angriff über WPS wahrscheinlich nicht erfolgreich. |
| WPS-PIN kann aufgrund einer schwachen Initiale (e-S1, e S2)-Entropie durch einen Offline Angriff geknackt werden. In 2014 beschrieb Dominique Bongard einen "Pixie Dust"-Angriff, bei dem die schlechte anfängliche Zufallszahl für den Pseudo-Zufallszahlengenerator (PRNG) im Drahtlosgerät einen Offline-Brute-Force-Angriff ermöglichte. | Die Microsoft-Implementierung von WPS in Surface Hub ist nicht anfällig für diesen Offline-Pin-Brute-Force-Angriff. Die WPS-PIN wird für jede Verbindung zufällig festgelegt. |

**Unbeabsichtigte Belichtung von Netzwerkdiensten:** Netzwerk-Daemons, die für Ethernet-oder WLAN-Dienste vorgesehen sind, werden möglicherweise aufgrund einer Fehlkonfiguration (wie Bindung an "alle"/0.0.0.0-Schnittstellen) versehentlich verfügbar gemacht. Zu den anderen möglichen Ursachen gehören eine schlecht konfigurierte Geräte Firewall oder fehlende Firewall-Regeln.

| Wi-Fi-direkt Anfälligkeit | Begrenzung des Oberflächen Hubs |
| --- | --- |
| Eine fehlerhafte Konfiguration bindet anfällige oder nicht authentifizierte Netzwerkdienste auf „alle” Schnittstellen, darunter auch die Wi-Fi Direct-Schnittstelle. Dadurch können Dienste verfügbar gemacht werden, die für WLAN-direkt Clients nicht zugänglich sein sollten, die möglicherweise schwach oder automatisch authentifiziert werden. | In Surface Hub erlauben die standardmäßigen Firewallregeln nur die erforderlichen TCP-und UDP-Netzwerkports und verweigern standardmäßig alle eingehenden Verbindungen. Konfigurieren Sie eine starke Authentifizierung, indem Sie den WPS-Pin-Modus aktivieren.|

**Überbrückung von WLAN-direkt-und anderen drahtgebundenen oder drahtlosen Netzwerken:** Die Netzwerküberbrückung zwischen WLAN-oder Ethernet-Netzwerken stellt eine Verletzung der Wi-Fi Direct-Spezifikation dar. Eine solche Brücke oder Fehlkonfiguration kann die Steuerung von drahtlos Zugriffen für das interne Unternehmensnetzwerk effektiv senken oder entfernen.

| Wi-Fi-direkt Anfälligkeit | Begrenzung des Oberflächen Hubs |
| --- | --- |
| Wi-Fi Direct-Geräten können nicht authentifizierte oder schlecht authentifizierte Zugriffe auf überbrückte Netzwerkverbindungen ermöglichen. Auf diese Weise können WLAN-direkt Netzwerke Datenverkehr an internes Ethernet-LAN oder andere Infrastrukturen oder an Enterprise-WLAN-Netzwerke weiterleiten, wobei vorhandene IT-Sicherheitsprotokolle verletzt werden. | Surface Hub kann nicht so konfiguriert werden, dass drahtlose Schnittstellen überbrückt oder Routing zwischen unterschiedlichen Netzwerken zugelassen wird. Die Firewall-Standardregeln fügen für ein solche Routing- oder Überbrückungsverbindungen detaillierte Verteidigungsmaßnahmen hinzu. |

**Nutzung des Wi-Fi Direct "Legacy"-Modus:** Die Exposition gegenüber unbeabsichtigten Netzwerken oder Geräten kann auftreten, wenn Sie im "Legacy"-Modus arbeiten. Gerätespoofing oder unbeabsichtigte Verbindungen können auftreten, wenn WPS-PIN nicht aktiviert ist.

| Wi-Fi-direkt Anfälligkeit | Begrenzung des Oberflächen Hubs |
| --- | --- |
| Durch die Unterstützung von Wi-Fi Direct und 802.11-Infrastruktur-Clients, wird das System im „Legacy”-Unterstützungsmodus ausgeführt. Dadurch kann die Verbindungs Einrichtungsphase unbegrenzt verfügbar gemacht werden, sodass Gruppen verbunden werden oder Geräte eingeladen werden, um nach der geplanten Setupphase eine Verbindung herzustellen. |    Surface Hub unterstützt keine Wi-Fi Direct Legacy-Clients. Es können nur Wi-Fi Direct-Verbindungen zur Surface Hub aufgestellt werden, auch wenn der WPS-PIN-Modus aktiviert ist. |

**Wi-Fi Direct go-Aushandlung während der Verbindungseinrichtung:** Der Gruppenbesitzer in Wi-Fi Direct ist analog zum "Access Point" in einem herkömmlichen 802,11-Drahtlosnetzwerk. Die Aushandlung kann von einem böswilligen Gerät manipuliert werden.

|Wi-Fi-direkt Anfälligkeit |   Begrenzung des Oberflächen Hubs |
| --- | --- |
| Wenn Gruppen dynamisch eingerichtet werden oder das Wi-Fi Direct-Gerät für die Teilnahme an neuen Gruppen bereitgestellt werden kann, kann die Verhandlung des Gruppen Besitzers von einem böswilligen Gerät gewonnen werden, das immer den Maximalwert des Gruppen Besitzers von 15 angibt. (Die Verbindung schlägt jedoch fehl, wenn das Gerät so konfiguriert ist, dass es immer ein Gruppenbesitzer ist.)  | Surface Hub nutzt den Wi-Fi Direct "autonomen Modus", der die go-Aushandlungs Phase der Verbindungseinrichtung überspringt. Und Surface Hub ist immer der Gruppenbesitzer. |

**Unbeabsichtigte oder böswillige Wi-Fi-deauthentifizierung:** Bei der WLAN-deauthentifizierung handelt es sich um einen alten Angriff, bei dem ein lokaler Angreifer Informationslecks beim Verbindungsaufbau beschleunigen, neue vier-Wege-Handshakes auslösen, eine WLAN-Direct-WPS-PBC-Funktion für aktive Angriffe nutzen oder Denial-of-Service-Angriffe erstellen kann.

| Wi-Fi-direkt Anfälligkeit | Begrenzung des Oberflächen Hubs |
| --- | --- |
| Deauthentifizierungs Pakete können von einem nicht authentifizierten Angreifer gesendet werden, damit sich die Station erneut authentifiziert, um den resultierenden Handshake zu schnüffeln. Kryptografische oder Brute-Force-Angriffe können auf den resultierenden Handshake ausgeführt werden. Zu den Abschwächungsmaßnahmen für diese Angriffe gehören das Erzwingen von Längen-und Komplexitäts Richtlinien für vorinstallierte Schlüssel, das Konfigurieren des Zugriffspunkts (falls zutreffend) zum erkennen bösartiger Ebenen von Deauthentifizierungs Paketen und die Verwendung von WPS zum automatischen Generieren von starken Schlüsseln. Im PBC-Modus interagiert der Benutzer mit einer physischen oder virtuellen Schaltfläche, um eine beliebige Gerätezuordnung zu ermöglichen. Dieser Vorgang sollte nur bei der Einrichtung innerhalb eines kurzen Fensters erfolgen. Nachdem die Schaltfläche automatisch "gedrückt" wurde, akzeptiert das Gerät alle Stationen, die über einen kanonischen PIN-Wert (alle Nullen) zugeordnet werden. Deauthentifizierung kann einen wiederholten Einrichtungsprozess erzwingen. |   Surface Hub verwendet WPS im PIN-oder PBC-Modus. Eine PSK-Konfiguration ist nicht zulässig. Mit dieser Methode kann die Generierung von starken Schlüsseln erzwungen werden. Es empfiehlt sich, die WPS-PIN-Sicherheit für Surface Hub zu aktivieren. |
| Neben Denial-of-Service-Angriffen können Deauthentifizierungs Pakete verwendet werden, um eine erneute Verbindung auszulösen, die das Fenster der Möglichkeit für aktive Angriffe auf WPS-PBC wieder öffnet. |   Aktivieren Sie die WPS-PIN-Sicherheit in der Surface Hub-Konfiguration. |

**Einfache Offenlegung von drahtlos Informationen:** Drahtlose Netzwerke, 802,11 oder auf andere Weise, sind von Natur aus Gefahr einer Offenlegung von Informationen. Obwohl diese Informationen hauptsächlich Verbindungs-oder Geräte Metadaten sind, bleibt dieses Problem ein bekanntes Risiko für jeden 802,11-Netzwerkadministrator. Wi-Fi Direct mit Geräteauthentifizierung über WPS-PIN legt effektiv die gleichen Informationen offen wie ein PSK- oder Enterprise 802.11-Netzwerk.

| Wi-Fi-direkt Anfälligkeit | Begrenzung des Oberflächen Hubs |
| --- | --- |
| Während der Übertragung, der Verbindungseinrichtung oder sogar des normalen Betriebs von bereits verschlüsselten Verbindungen werden grundlegende Informationen zu Geräten und Paketgrößen drahtlos übertragen. Auf grundlegender Ebene kann ein lokaler Angreifer, der sich im Funkbereich befindet, die relevanten 802,11-Informationselemente überprüfen, um die Namen von Drahtlosgeräten, die Mac-Adressen von Kommunikationsgeräten und möglicherweise andere Details wie die Version des drahtlos Stapels, die Paketgrößen oder die konfigurierten Zugriffspunkt-oder Gruppenbesitzer Optionen zu ermitteln.  | Das Wi-Fi-direkt Netzwerk, das von Surface Hub verwendet wird, kann nicht weiter vor Undichtigkeiten durch Metadaten geschützt werden, genau wie bei 802,11 Enterprise-oder PSK-Drahtlosnetzwerken. Die physische Sicherheit und die Entfernung potenzieller Bedrohungen durch drahtlose Nachbarschaft können dazu beitragen, potenzielle Informationslecks zu verringern. |

**Drahtlose Evil Twin-oder Spoofing-Angriffe:**  Das Spoofing des WLAN-namens ist ein einfacher, bekannter Exploit, mit dem ein lokaler Angreifer ahnungslose oder falsche Benutzer anlocken kann, um eine Verbindung herzustellen.

| Wi-Fi-direkt Anfälligkeit | Begrenzung des Oberflächen Hubs |
| --- | --- |
| Durch Spoofing oder Klonen des drahtlos namens oder der "SSID" des Zielnetzwerks kann ein Angreifer den Benutzer dazu verleiten, sich mit einem gefälschten, bösartigen Netzwerk zu verbinden. Durch die Unterstützung von nicht authentifizierten, automatischen Join-Miracast kann ein Angreifer die beabsichtigten Anzeige Materialien erfassen oder Netzwerkangriffe auf dem Verbindungsgerät starten. | Es gibt zwar keine spezifischen Schutzmaßnahmen gegen den Beitritt zu einem gefälschten Surface-Hub, doch wird diese Sicherheitsanfälligkeit teilweise auf zweierlei Weise verringert. Erstens muss jeder potenzieller Angriff innerhalb der WLAN-Reichweite erfolgen. Zweitens ist dieser Angriff nur während der ersten Verbindung möglich. Nachfolgende Verbindungen verwenden eine persistente Wi-Fi Direct-Gruppe, und Windows wird diese vorherige Verbindung während der zukünftigen Verwendung des Hubs behalten und priorisieren. (Hinweis: die gleichzeitige Spoofing der Mac-Adresse, des WLAN-Kanals und der SSID wurde für diesen Bericht nicht berücksichtigt und kann zu einem uneinheitlichen WLAN-Verhalten führen.) Insgesamt handelt es sich hierbei um ein grundlegendes Problem für alle 802,11-Drahtlosnetzwerke, die nicht über Enterprise-WPA2-Protokolle wie EAP-TLS oder EAP-pwd verfügen, die von Wi-Fi Direct nicht unterstützt werden. |

##  <a name="surface-hub-hardening-guidelines"></a>Surface Hub-Sicherungsrichtlinien

Surface Hub dient zum der Zusammenarbeit und ermöglicht dem Benutzer, Besprechungen schnell und effizient zu starten und beizutreten.. Die standardmäßigen Wi-Fi Direct-Einstellungen für Surface Hub sind für dieses Szenario optimiert.

Für zusätzliche Wireless-Schnittstellen Sicherheit sollten Surface Hub-Benutzer die WPS-Pin-Sicherheitseinstellung aktivieren. Mit dieser Einstellung wird der WPS-PBC-Modus deaktiviert und die Clientauthentifizierung angeboten. Es bietet das höchste Maß an Schutz, da nicht autorisierte Verbindungen mit Surface Hub verhindert werden.

Wenn Sie weiterhin Bedenken bezüglich Authentifizierung und Autorisierung für Surface Hub haben, empfiehlt es sich, das Gerät mit einem separaten Netzwerk zu verbinden. Sie können WLAN verwenden (beispielsweise ein "Guest"-Wi-Fi-Netzwerk) oder ein separates Ethernet-Netzwerk, vorzugsweise ein völlig anderes physikalisches Netzwerk. Ein VLAN kann aber auch zusätzliche Sicherheit bieten. Dieser Ansatz kann natürlich Verbindungen mit internen Netzwerkressourcen oder-Diensten ausschließen und erfordert möglicherweise zusätzliche Netzwerkkonfiguration, um wieder Zugriff zu erhalten.

Auch empfohlen:
- [Installieren regulärer System Updates](manage-windows-updates-for-surface-hub.md) 
- Aktualisieren der Miracast-Einstellungen zum Deaktivieren des automatischen Präsentationsmodus

##  <a name="additional-information"></a>Weitere Informationen

- [Wi-Fi Direct-Spezifikationen](http://www.wi-fi.org/discover-wi-fi/wi-fi-direct)
- [Wireless Protected Setup (WPS)-Spezifikation](http://www.wi-fi.org/discover-wi-fi/wi-fi-protected-setup)



