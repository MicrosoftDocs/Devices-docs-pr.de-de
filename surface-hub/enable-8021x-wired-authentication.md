---
title: Aktivieren der kabelgebundenen 802.1x-Authentifizierung
description: Die MDM-Richtlinien für die 802.1x kabelgebundene Authentifizierung wurde auf Surface Hub-Geräten aktiviert.
ms.prod: surface-hub
ms.sitesec: library
author: dansimp
ms.author: dansimp
ms.topic: article
ms.date: 11/15/2017
ms.reviewer: ''
manager: laurawi
ms.localizationpriority: medium
ms.openlocfilehash: 119f879d74ccda5d53da27d842413346a50693f1
ms.sourcegitcommit: 109d1d7608ac4667564fa5369e8722e569b8ea36
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/27/2020
ms.locfileid: "10833706"
---
# Aktivieren Sie 802.1x kabelgebundene Authentifizierung

Das [Update vom 14 November2017 auf Windows10](https://support.microsoft.com/help/4048954/windows-10-update-kb4048954) (Build 15063.726) ermöglicht die MDM-Richtlinien für die 802.1x kabelgebundene Authentifizierung auf Surface Hub-Geräten. Das Feature ermöglicht Organisationen, standardisierte Kabelnetzwerkauthentifizierungen mithilfe des [IEEE 802.1x-Authentifizierungsprotokolls](http://www.ieee802.org/1/pages/802.1x-2010.html) zu verwenden. Diese Option besteht bereits für die drahtlose Authentifizierung mithilfe von WLAN-Profilen per MDM. In diesem Thema wird erläutert, wie Sie einen Surface Hub für die Verwendung mit kabelgebundenen Authentifizierung konfigurieren. 

Die Erzwingung und Aktivierung der 802.1x kabelgebundenen Authentifizierung auf Surface Hub kann über die MDM [OMA-URI-Definition](https://docs.microsoft.com/intune-classic/deploy-use/windows-10-policy-settings-in-microsoft-intune#oma-uri-settings) durchgeführt werden. 

Die primäre Konfiguration ist auf die Richtlinie **LanProfile** festgelegt. Je nach ausgewählter Authentifizierungsmethode sind andere Richtlinien möglicherweise erforderlich, entweder die **EapUserData**-Richtlinie oder die MDM-Richtlinien für das Hinzufügen von Benutzer- oder Computerzertifikaten (z.B. [ClientCertificateInstall](https://docs.microsoft.com/windows/client-management/mdm/clientcertificateinstall-csp) für Benutzer/Gerätezertifikate oder [RootCATrustedCertificates](https://docs.microsoft.com/windows/client-management/mdm/rootcacertificates-csp) für Gerätezertifikate). 

##  <a name="lanprofile-policy-element"></a>LanProfile-Richtlinienelement

Um Surface Hub zum Verwenden der unterstützten 802.1 x-Authentifizierungsmethoden zu konfigurieren, verwenden Sie die folgende OMA-URI. 

```
./Vendor/MSFT/SurfaceHub/Dot3/LanProfile
```

Dieser OMA-URI-Knoten verwendet eine XML-Textzeichenfolge als Parameter. Der als Parameter bereitgestellte XML-Code sollte dem [verkabelten LAN-Profilschema](https://msdn.microsoft.com/library/cc233002.aspx) einschließlich der Elemente des [802.1X-Schemas](https://msdn.microsoft.com/library/cc233003.aspx) entsprechen. 

In den meisten Fällen kann ein Administrator oder Benutzer die LanProfile XML von einem vorhandenen PC exportieren, der bereits im Netzwerk für 802.1X mit dem folgenden NETSH-Befehl konfiguriert ist. 

```
netsh lan export profile folder=.
```

Das Ausführung dieses Befehls ergibt die folgende Ausgabe und platziert eine Datei mit dem Titel **Ethernet.xml** in das aktuelle Verzeichnis. 

```
Interface: Ethernet
Profile File Name: .\Ethernet.xml
1 profile(s) were exported successfully.
```

##  <a name="eapuserdata-policy-element"></a>EapUserData-Richtlinienelement

Wenn die ausgewählte Authentifizierungsmethode einen Benutzernamen und Kennwort im Gegensatz zu einem Zertifikat erfordert, können Sie das **EapUserData**-Elements zur Angabe der Anmeldeinformationen für das Gerät verwenden, um sich beim Netzwerk zu authentifizieren. 

```
./Vendor/MSFT/SurfaceHub/Dot3/EapUserData 
```

Dieser OMA-URI-Knoten verwendet eine XML-Textzeichenfolge als Parameter. Der als Parameter bereitgestellte XML-Code sollte dem [Beispiel der Benutzereigenschaften für PEAP-MS-CHAPv2](https://msdn.microsoft.com/library/windows/desktop/bb891979) entsprechen. In diesem Beispiel müssen Sie alle Instanzen von *test* und *ias-domain* durch Ihre Informationen ersetzen.



##  <a name="adding-certificates"></a>Hinzufügen von Zertifikaten

Wenn die ausgewählte Authentifizierungsmethode Zertifikat basiert ist, müssen Sie [ein Bereitstellungspaket erstellen](provisioning-packages-for-surface-hub.md), [MDM verwenden](https://docs.microsoft.com/windows/client-management/mdm/clientcertificateinstall-csp)oder ein Zertifikat aus den Einstellungen (**Einstellungen**  >  **aktualisieren und Sicherheits**  >  **Zertifikate**) importieren, um diese Zertifikate auf dem Surface Hub-Gerät im entsprechenden Zertifikatspeicher bereitzustellen. Wenn Sie ein Zertifikat hinzufügen möchten, muss jeder PFX nur ein Zertifikat enthalten (PFX kann nicht mehrere Zertifikate enthalten).

