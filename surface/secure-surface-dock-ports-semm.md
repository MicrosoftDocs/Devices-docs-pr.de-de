---
title: Sichere Surface Dock 2-Anschlüsse mit Surface Enterprise Management Mode (Semm)
description: Dieses Dokument enthält Anleitungen zum Konfigurieren von UEFI-Porteinstellungen für Surface Dock 2, wenn Sie mit kompatiblen Oberflächen Geräten wie Surface Book 3, Surface Laptop 3 und Surface pro 7 verbunden sind.
ms.assetid: 2808a8be-e2d4-4cb6-bd53-9d10c0d3e1d6
ms.reviewer: ''
manager: laurawi
keywords: Behandeln von allgemeinen Problemen oder Problemen mit der Einrichtung
ms.prod: w10
ms.mktglfcycl: support
ms.sitesec: library
ms.pagetype: surfacehub
author: v-miegge
ms.author: jesko
ms.topic: article
ms.date: 06/08/2020
ms.localizationpriority: medium
ms.audience: itpro
ms.openlocfilehash: 641d023b59426582130dcfb7e0d86c6f3af456e8
ms.sourcegitcommit: c1efb75e8524193bdc0a5f7496dc23a92ac665c8
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/12/2020
ms.locfileid: "11114693"
---
# Sichere Surface Dock 2-Anschlüsse mit Surface Enterprise Management Mode (Semm)

##  <a name="introduction"></a>Einführung

Surface Enterprise Management Mode (Semm) ermöglicht IT-Administratoren das Sichern und Verwalten von Surface Dock 2-Anschlüssen durch Konfigurieren von UEFI-Einstellungen in einem Windows Installer-Konfigurationspaket (. MSI-Datei), die für kompatible Surface-Geräte in einer Unternehmensumgebung bereitgestellt wird.

###  <a name="supported-devices"></a>Unterstützte Geräte

Das Verwalten von Surface Dock 2 mit Semm ist für Docks verfügbar, die mit Surface Book 3, Surface Laptop 3, Surface Laptop go, Surface pro 7 und Surface pro X verbunden sind. Diese kompatiblen Surface-Geräte werden gemeinhin als **Host-Devices**bezeichnet. Ein Paket wird auf Hostgeräte angewendet, basierend auf, wenn ein Host Gerät **authentifiziert** oder nicht **authentifiziert**ist. Die konfigurierten Einstellungen befinden sich auf der UEFI-Ebene auf Hostgeräten, sodass Sie – der IT-Administrator – das Surface Dock 2 genauso wie jedes andere integrierte Peripheriegerät wie die Kamera verwalten können.

>[!NOTE]
>Sie können Surface Dock 2-Anschlüsse nur verwalten, wenn das Dock mit einem der folgenden kompatiblen Geräte verbunden ist: Surface Book 3, Surface Laptop 3 und Surface pro 7. Jedes Gerät, das die Einstellungen für UEFI-authentifizierte Richtlinien nicht erhält, ist inhärent ein nicht authentifiziertes Gerät.

###  <a name="scenarios"></a>Szenarien

Wenn Sie das Surface Dock 2 auf autorisierte Personen beschränken, die bei einem Firmen-Host-Gerät angemeldet sind, erhalten Sie eine weitere Datenschutzebene. Diese Möglichkeit zum Sperren von Surface Dock 2 ist für bestimmte Kunden in äußerst sicheren Umgebungen von entscheidender Bedeutung, die die Funktionalität und Produktivitätsvorteile des Docks nutzen möchten, wobei die Einhaltung strenger Sicherheitsprotokolle gewährleistet ist. Wir gehen davon aus, dass Semm, das mit Surface Dock 2 verwendet wird, besonders für Kunden, die USB-Ports aus Sicherheitsgründen sperren möchten, besonders nützlich für offene Büros und freigegebene Räume sind. Eine Video Demo finden Sie unter [Semm für Surface Dock 2](https://youtu.be/VLV19ISvq_s).

##  <a name="configuring-and-deploying-uefi-settings-for-surface-dock-2"></a>Konfigurieren und Bereitstellen von UEFI-Einstellungen für Surface Dock 2

In diesem Abschnitt finden Sie Schritt-für-Schritt-Anleitungen für die folgenden Aufgaben:

1. Installieren des [**Surface UEFI-Konfigurators**](https://www.microsoft.com/download/details.aspx?id=46703)
1. Erstellen oder Anfordern von Zertifikaten für öffentliche Schlüssel
1. Erstellen Sie eine. MSI-Konfigurationspaket.
   1. Fügen Sie Ihre Zertifikate hinzu.
   1. Geben Sie die 16-stellige RN-Nummer für Ihre Surface Dock 2-Geräte ein.
   1. Konfigurieren Sie die UEFI-Einstellungen.
1. Erstellen Sie das Konfigurationspaket, und wenden Sie es auf Ziel Oberflächen Geräte an (Surface Book 3, Surface Laptop 3 oder Surface pro 7).

>[!NOTE]
>Bei der **Zufallszahl (RN)** handelt es sich um eine eindeutige 16-stellige Hex-Code Kennung, die im Werk bereitgestellt und auf der Unterseite des Docks in kleinem Format gedruckt wird. Die RN unterscheidet sich von den meisten Seriennummern dadurch, dass Sie nicht elektronisch gelesen werden können. Dadurch wird sichergestellt, dass der Besitznachweis in erster Linie nur durchlesen des RN beim physikalischen Zugriff auf das Gerät festgelegt wird. Das RN kann auch während der Kauftransaktion abgerufen und in Microsoft Inventory Systems aufgezeichnet werden.

###  <a name="install-semm-and-surface-uefi-configurator"></a>Installieren von Semm und Surface UEFI Configurator

Installieren Sie Semm, indem Sie **SurfaceUEFI_Configurator_v2.71.139.0.msi**ausführen. Hierbei handelt es sich um einen eigenständigen Installer, der alles enthält, was Sie zum Erstellen und Verteilen von Konfigurationspaketen für Surface Dock 2 benötigen.

- Laden Sie den **Surface UEFI Configurator** von [Surface Tools](https://www.microsoft.com/en-us/download/details.aspx?id=46703)herunter.

##  <a name="create-public-key-certificates"></a>Erstellen von Zertifikaten für öffentliche Schlüssel

Dieser Abschnitt enthält Spezifikationen zum Erstellen der Zertifikate, die zum Verwalten von Ports für Surface Dock 2 erforderlich sind.

###  <a name="prerequisites"></a>Voraussetzungen

In diesem Artikel wird davon ausgegangen, dass Sie entweder Zertifikate von einem Drittanbieter erhalten oder dass Sie bereits über Expertenwissen in PKI-Zertifikatdiensten verfügen und wissen, wie Sie eigene Zertifikate erstellen können.  Mit einer Ausnahme sollten Sie sich mit den allgemeinen Empfehlungen zum Erstellen von Zertifikaten vertraut machen, wie Sie in der Dokumentation zum [Surface Enterprise Management Mode (Semm)](https://docs.microsoft.com/surface/surface-enterprise-management-mode) beschrieben sind. Die auf dieser Seite dokumentierten Zertifikate erfordern Ablaufzeiten von 30 Jahren für die **Dock-Zertifizierungsstelle**und 20 Jahre für das **Host Authentifizierungszertifikat**.

Weitere Informationen finden Sie unter Dokumentation zur [Zertifikatsdienste-Architektur](https://docs.microsoft.com/windows/win32/seccrypto/certificate-services-architecture) und Überprüfen der entsprechenden Kapitel in [Windows Server 2019 Inside Out](https://www.microsoftpressstore.com/store/windows-server-2019-inside-out-9780135492277)oder [Windows Server 2008 PKI und Zertifikatsicherheit](https://www.microsoftpressstore.com/store/windows-server-2008-pki-and-certificate-security-9780735640788) , die von Microsoft Press zur Verfügung stehen.

###  <a name="root-and-host-certificate-requirements"></a>Stamm-und Host Zertifikatanforderungen

Vor dem Erstellen des Konfigurationspakets müssen Sie Zertifikate mit öffentlichen Schlüsseln vorbereiten, die den Besitz von Surface Dock 2 authentifizieren und spätere Änderungen des Besitzers während des Gerätelebenszyklus vereinfachen. Für das Host-und Bereitstellungszertifikat ist die Eingabe von EKU-IDs erforderlich, die auch als Objekt-IDs **(Enhanced Key Usage, EKU) der Client Authentifizierung**bezeichnet werden.

Die erforderlichen EKU-Werte sind in Tabelle 1 und Tabelle 2 aufgeführt.

####  <a name="surface-hub-2-fingerprint-reader-tech-specs"></a>Tabelle1. Zertifikatanforderungen für root und Dock

|Zertifikat|Algorithmus|Beschreibung|Ablauf|EKU-OID|
|---|---|---|---|---|
|Stammzertifizierungsstelle|ECDSA_P384|-Root-Zertifikat mit 384-Bit-Prime elliptischer Curve-Digitalsignatur-Algorithmus (ECDSA)<br>-SHA 256-Schlüsselverwendung:<br>CERT_DIGITAL_SIGNATURE_KEY_USAGE<br>-CERT_KEY_CERT_SIGN_KEY_USAGE<br>CERT_CRL_SIGN_KEY_USAGE|30 Jahre|n.a.
|Dock-Zertifizierungsstelle|ECC-P256-Kurve|-Host Zertifikat mit 256-Bit-elliptischer Kurvenverschlüsselung (ECC)<br>-SHA 256-Schlüsselverwendung:<br>CERT_KEY_CERT_SIGN_KEY_USAGE<br>-Pfadlängenbeschränkung = 0|20 Jahre|1.3.6.1.4.1.311.76.9.21.2<br>1.3.6.1.4.1.311.76.9.21.3|

   >[!NOTE]
   >Die Dock-Zertifizierungsstelle muss als P7B-Datei exportiert werden.

###  <a name="provisioning-administration-certificate-requirements"></a>Bereitstellungszertifikat Anforderungen

Jedes Host-Gerät muss die doc-Zertifizierungsstelle und zwei Zertifikate aufweisen, wie in Tabelle 2 zu sehen ist.

#### Tabelle 2 Bereitstellungszertifikat Anforderungen

|Zertifikat|Algorithmus|Beschreibung|EKU-OID|
|---|---|---|---|
|Host Authentifizierungszertifikat|ECC-P256<br>SHA 256|Weist die Identität des Hostgeräts auf.|1.3.6.1.4.1.311.76.9.21.2|
|Bereitstellungs Verwaltungszertifikat|ECC-P256<br>SHA256|Ermöglicht es Ihnen, den Besitz von Dock und/oder die Richtlinieneinstellungen zu ändern, indem Sie die derzeit auf dem Dock installierte Zertifizierungsstelle ersetzen können.|1.3.6.1.4.1.311.76.9.21.3<br>1.3.6.1.4.1.311.76.9.21.4|

   >[!NOTE]
   >Die Host Authentifizierungs-und Bereitstellungszertifikate müssen als PFX-Dateien exportiert werden.

###  <a name="create-configuration-package"></a>Konfigurationspaket erstellen

Wenn Sie die Zertifikate erhalten oder erstellt haben, können Sie das MSI-Konfigurationspaket erstellen, das auf Ziel Oberflächen Geräte angewendet wird.

1. Führen Sie den DGM- **UEFI-Konfigurator**aus.

   ![Oberflächen-UEFI-Konfigurator ausführen](images/secure-surface-dock-ports-semm-1.png)

1. Wählen Sie **Surface Dock**aus.

   ![Surface Dock auswählen](images/secure-surface-dock-ports-semm-2.png)

1. Geben Sie auf der Seite Zertifikat die entsprechenden **Zertifikate**ein.

   ![Geben Sie die entsprechenden Zertifikate ein.](images/secure-surface-dock-ports-semm-3.png)

1. Fügen Sie der Liste die entsprechende Dock-RNS hinzu.

   >[!NOTE]
   >Beim Erstellen eines Konfigurationspakets für mehrere Surface Dock 2-Geräte können Sie eine CSV-Datei verwenden, die eine Liste von RNS enthält, anstatt die einzelnen RN manuell einzugeben.

1. Geben Sie Ihre Richtlinieneinstellungen für USB-Daten, Ethernet-und Audioanschlüsse an. Mit dem UEFI-Konfigurator können Sie Richtlinieneinstellungen für authentifizierte Benutzer (authentifizierte Richtlinie) und nicht authentifizierte Benutzer (nicht authentifizierte Richtlinie) konfigurieren. Die folgende Abbildung zeigt, wie der Port Zugriff für authentifizierte Benutzer aktiviert und für nicht authentifizierte Benutzer deaktiviert wurde.

   ![Wählen Sie aus, welche Komponenten Sie aktivieren oder deaktivieren möchten.](images/secure-surface-dock-ports-semm-4.png)

   - Der authentifizierte Benutzer bezieht sich auf ein Surface-Gerät, auf dem die entsprechenden Zertifikate installiert sind, wie in. MSI-Konfigurationspaket, das Sie auf Zielgeräte angewendet haben. Sie bezieht sich auf jeden Benutzer authentifizierten Benutzer, der sich beim Gerät anmeldet. 
   - Nicht authentifizierter Benutzer bezieht sich auf ein anderes Gerät.
   - Wählen Sie **Zurücksetzen** aus, um ein spezielles Paket "Zurücksetzen" zu erstellen, mit dem alle vorherigen Konfigurationspakete entfernt werden, die vom Dock akzeptiert wurden.

1. Wählen Sie **Erstellen** aus, um das Paket wie angegeben zu erstellen.

###  <a name="apply-the-configuration-package-to-a-surface-dock-2"></a>Anwenden des Konfigurationspakets auf ein Surface Dock 2

1. Übernehmen Sie die MSI-Datei, die vom Surface UEFI-Konfigurator generiert wurde, und installieren Sie Sie auf einem Surface-Host-Gerät. Kompatible Hostgeräte sind Surface Book 3, Surface Laptop 3 oder Surface pro 7.
1. Verbinden Sie das Host-Gerät mit dem Surface Dock 2. Wenn Sie die Dock-UEFI-Richtlinieneinstellungen verbinden, werden diese übernommen.

##  <a name="verify-managed-state-using-the-surface-app"></a>Überprüfen des verwalteten Zustands mithilfe der Surface-App

Nachdem Sie das Konfigurationspaket angewendet haben, können Sie den resultierenden Richtlinienzustand des Docks direkt aus der Surface-APP überprüfen, die standardmäßig auf allen Surface-Geräten installiert ist. Wenn die Surface-App auf dem Gerät nicht vorhanden ist, können Sie Sie aus dem Microsoft Store herunterladen und installieren.

###  <a name="test-scenario"></a>Test Szenario

Ziel: Konfigurieren Sie Richtlinieneinstellungen so, dass der Port Zugriff nur von authentifizierten Benutzern zugelassen wird.

1. Aktivieren Sie alle Ports für authentifizierte Benutzer, und deaktivieren Sie Sie für nicht authentifizierte Benutzer.

   ![Aktivieren von Ports für authentifizierte Benutzer](images/secure-surface-dock-ports-semm-4.png)

1. Wenden Sie das Konfigurationspaket auf Ihr Zielgerät an, und verbinden Sie dann Surface Dock 2.

1. Öffnen Sie **Surface-App** , und wählen Sie **Surface Dock** aus, um den resultierenden Richtlinienzustand Ihres Surface Dock anzuzeigen. Wenn die Richtlinieneinstellungen angewendet werden, gibt Surface APP an, dass Ports verfügbar sind.

   ![Surface-APP zeigt an, dass alle Ports für authentifizierte Benutzer verfügbar sind](images/secure-surface-dock-ports-semm-5.png)

1. Nun müssen Sie sicherstellen, dass die Richtlinieneinstellungen alle Ports für nicht authentifizierte Benutzer erfolgreich deaktiviert haben. Verbinden Sie das Surface Dock 2 mit einem nicht verwalteten Gerät, also einem beliebigen Surface-Gerät außerhalb des Verwaltungsbereichs für das von Ihnen erstellte Konfigurationspaket.

1. Öffnen Sie **Surface-App** , und wählen Sie **Surface Dock**aus. Der resultierende Richtlinienzustand gibt an, dass Ports deaktiviert sind.

   ![Surface-App mit deaktivierten Anschlüssen für nicht authentifizierte Benutzer ](images/secure-surface-dock-ports-semm-6.png)

>[!NOTE]
>Wenn Sie den Besitz des Geräts behalten, aber allen Benutzern den Vollzugriff gestatten möchten, können Sie ein neues Paket mit aktiviertem Inhalt erstellen. Wenn Sie die Einschränkungen und den Besitz des Geräts vollständig entfernen möchten (damit es nicht verwaltet wird), wählen Sie in Surface UEFI Configurator **Zurücksetzen** aus, um ein Paket zu erstellen, das auf die Zielgeräte angewendet werden soll.

Herzlichen Glückwunsch. Sie haben erfolgreich Surface Dock 2-Ports auf zielgerichteten Hostgeräten verwaltet.

##  <a name="learn-more"></a>Mehr erfahren

- [Dokumentation zu Surface Enterprise Management Mode (Semm)](https://docs.microsoft.com/surface/surface-enterprise-management-mode)
- [Architektur der Zertifikatdienste](https://docs.microsoft.com/windows/win32/seccrypto/certificate-services-architecture)
- [Windows Server 2019 von innen nach außen](https://www.microsoftpressstore.com/store/windows-server-2019-inside-out-9780135492277)
- [Windows Server 2008 PKI-und Zertifikatsicherheit](https://www.microsoftpressstore.com/store/windows-server-2008-pki-and-certificate-security-9780735640788)
