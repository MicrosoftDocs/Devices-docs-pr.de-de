---
title: Verwalten von Surface-Treiberupdates im Konfigurations-Manager
description: In diesem Artikel werden die verfügbaren Optionen zum Verwalten und Bereitstellen von Firmware-und Treiberupdates für Surface-Geräte beschrieben.
ms.assetid: b64879c4-37eb-4fcf-a000-e05cbb3d26ea
ms.reviewer: ''
author: v-miegge
manager: laurawi
keywords: Surface, Surface Pro 3, Firmware, Update, Gerät, verwalten, bereitstellen, Treiber, USB
ms.localizationpriority: medium
ms.prod: w10
ms.mktglfcycl: manage
ms.pagetype: surface, devices
ms.sitesec: library
ms.author: daclark
ms.topic: article
audience: itpro
ms.openlocfilehash: be32309b26ff6a873c36927cc39595022c4dbb90
ms.sourcegitcommit: ed4478dd3c6116a25b1e01a3a0f5ff6c1f940013
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "10897073"
---
# Verwalten von Surface-Treiberupdates im Konfigurations-Manager

##  <a name="summary"></a>Zusammenfassung

Ab [Microsoft System Center Configuration Manager, Version 1710](https://docs.microsoft.com/sccm/core/plan-design/changes/whats-new-in-version-1710#software-updates), können Sie die Microsoft Surface-Firmware und Treiberupdates direkt über den Configuration Manager-Client synchronisieren und bereitstellen. Der Prozess ähnelt dem Bereitstellen regulärer Updates. Einige zusätzliche Konfigurationen sind jedoch erforderlich, um die Oberflächen Treiberaktualisierungen in Ihrem Katalog zu erhalten.

##  <a name="prerequisites"></a>Voraussetzungen

Zum Verwalten von Oberflächen Treiberupdates müssen die folgenden Voraussetzungen erfüllt sein:

- Sie müssen Configuration Manager, Version 1710 oder eine neuere Version, verwenden.
- Für alle Software Update Punkte (SUPs) muss Windows Server 2016 oder eine neuere Version ausgeführt werden. Andernfalls ignoriert Configuration Manager diese Einstellung, und die Oberflächen Treiber werden nicht synchronisiert.

> [!NOTE]
> Wenn Ihre Umgebung die Voraussetzungen nicht erfüllt, finden Sie im Abschnitt [häufig gestellte Fragen](#frequently-asked-questions-faq) die [alternativen Methoden](https://support.microsoft.com/help/4098906/manage-surface-driver-updates-in-configuration-manager#1) zum Bereitstellen von Oberflächen Treiber-und Firmware-Updates.

##  <a name="useful-log-files"></a>Nützliche Protokolldateien

Die folgenden Protokolle sind besonders nützlich, wenn Sie Oberflächen Treiberupdates verwalten.

|Protokollname|Beschreibung|
|---|---|
|WCM. log|Zeichnet Details zur Softwareupdatepunkt-Konfiguration und Verbindungen mit dem WSUS-Server für abonnierte Updatekategorien,-Klassifikationen und-Sprachen auf.|
|WsyncMgr. log|Zeichnet Details zum Synchronisierungsprozess für Softwareupdates auf.|

Diese Protokolle befinden sich auf dem Website Server, der den SUP verwaltet, oder auf dem SUP selbst, wenn er direkt auf einem Website Server installiert ist.
Eine vollständige Liste der Configuration Manager-Protokolle finden Sie unter [Protokolldateien in System Center Configuration Manager](https://docs.microsoft.com/sccm/core/plan-design/hierarchy/log-files).

##  <a name="enabling-surface-driver-updates-management"></a>Aktivieren der Verwaltung von Oberflächen Treiberupdates

Führen Sie die folgenden Schritte aus, um die Verwaltung von Oberflächen Treiberupdates in Configuration Manager zu aktivieren:

1. Wechseln Sie in der Configuration Manager-Konsole **Administration**zu  >  **Overview**  >  **Website Konfigurations**  >  **Websites**für die Verwaltungsübersicht.
1. Wählen Sie die Website aus, die den SUP-Server der obersten Ebene für Ihre Umgebung enthält.
1. Wählen Sie im Menüband **Websitekomponenten konfigurieren**aus, und wählen Sie dann **Software Update Punkt**aus. Oder klicken Sie mit der rechten Maustaste auf die Website, **Configure Site Components**und wählen Sie dann  >  **Software Update Punkt**für Websitekomponenten konfigurieren aus.
1. Aktivieren Sie auf der Registerkarte **Klassifikationen** das Kontrollkästchen **Microsoft-Oberflächen Treiber und Firmware-Updates einbeziehen** .

   ![Eigenschaften von Software Update Punkt-Komponenten](images/manage-surface-driver-updates-1.png)

1. Wenn Sie von der folgenden Warnmeldung aufgefordert werden, wählen Sie **OK**aus.

   ![Konfigurations-Manager](images/manage-surface-driver-updates-2.png)

1. Wählen Sie auf der Registerkarte Produkte die Produkte aus, die Sie aktualisieren möchten, und wählen Sie dann **OK**aus.

   Die meisten Treiber gehören zu den folgenden Produktgruppen:

   - Treiber für Windows 10 und höhere Versionen
   - Aktualisieren von Windows 10-und höher-&-Wartungs Treibern
   - Windows 10 Anniversary Update und spätere Wartungs Treiber
   - Windows 10 Anniversary Update und höheres Upgrade & Wartungs Treiber
   - Windows 10 Creators-Update und spätere Wartungs Treiber
   - Windows 10 Creators-Update und späteres Upgrade & Wartungs Treiber
   - Windows 10 Fall Creators Update und spätere Wartungs Treiber
   - Windows 10 Fall Creators Update-und höheres Upgrade & Wartungs Treiber
   - Windows 10 S und spätere Wartungs Treiber
   - Windows 10 S, Version 1709 und höher, Wartungs Treiber für Tests
   - Windows 10 S, Version 1709 und höher, Upgrade & Wartungs Treiber für Tests

   > [!NOTE]
   > Die meisten Oberflächen Treiber gehören mehreren Windows 10-Produktgruppen an. Sie müssen möglicherweise nicht alle Produkte auswählen, die hier aufgelistet sind. Um die Anzahl der Produkte zu verringern, die ihren Update Katalog füllen, empfehlen wir, dass Sie nur die Produkte auswählen, die für Ihre Umgebung für die Synchronisierung erforderlich sind.

##  <a name="verifying-the-configuration"></a>Überprüfen der Konfiguration

Führen Sie die folgenden Schritte aus, um zu überprüfen, ob der SUP richtig konfiguriert ist:

1. Öffnen Sie WsyncMgr. log, und suchen Sie dann nach dem folgenden Eintrag:

   ```console
   Surface Drivers can be supported in this hierarchy since all SUPs are on Windows Server 2016, WCM SCF property Sync Catalog Drivers is set.

   Sync Catalog Drivers SCF value is set to : 1
   ```

   Wenn einer der folgenden Einträge in WsyncMgr. log protokolliert wird, aktivieren Sie Schritt 4 im vorherigen Abschnitt erneut:

   ```console
   Sync Surface Drivers option is not set

   Sync Catalog Drivers SCF value is set to : 0
   ```

1. Öffnen Sie WCM. log, und suchen Sie dann nach einem Eintrag, der wie folgt aussieht:

   ![WCM. Log-Einstellungen](images/manage-surface-driver-updates-3.png)

   Bei diesem Eintrag handelt es sich um ein XML-Element, in dem alle Produktgruppen und Klassifikationen aufgelistet sind, die aktuell vom SUP-Server synchronisiert sind. Sie können beispielsweise einen Eintrag sehen, der wie folgt aussieht:

   ```xml
   <Categories>
       <Category Id="Product:05eebf61-148b-43cf-80da-1c99ab0b8699"><![CDATA[Windows 10 and later drivers]]></Category>
       <Category Id="Product:06da2f0c-7937-4e28-b46c-a37317eade73"><![CDATA[Windows 10 Creators Update and Later Upgrade & Servicing Drivers]]></Category>
       <Category Id="Product:c1006636-eab4-4b0b-b1b0-d50282c0377e"><![CDATA[Windows 10 S and Later Servicing Drivers]]></Category>
   </Categories>
   ```

   Wenn Sie die Produkte, die Sie in Schritt 6 im vorherigen Abschnitt ausgewählt haben, nicht finden können, überprüfen Sie, ob die SUP-Einstellungen gespeichert sind.

   Sie können auch warten, bis die nächste Synchronisierung abgeschlossen ist, und dann überprüfen, ob die Oberflächen Treiber-und Firmware-Updates in der Configuration Manager-Konsole unter Software Updates aufgeführt sind. Die Konsole zeigt beispielsweise die folgenden Informationen an:

   ![Alle Suchergebnisse für Software Updates](images/manage-surface-driver-updates-4.png)

##  <a name="manual-synchronization"></a>Manuelle Synchronisierung

Wenn Sie nicht bis zur nächsten Synchronisierung warten möchten, führen Sie die folgenden Schritte aus, um eine Synchronisierung zu starten:

1. Wechseln Sie in der Configuration Manager-Konsole zu **Software Library**  >  **Overview**  >  **Softwareupdates**  >  **alle Softwareupdates**.
1. Wählen Sie im Menüband **Software Updates synchronisieren**aus. Oder klicken Sie mit der rechten Maustaste auf **alle Softwareupdates**, und wählen Sie dann **Software Update synchronisieren**aus.
1. Überwachen Sie den Synchronisierungsfortschritt, indem Sie in WsyncMgr. log nach den folgenden Einträgen suchen:

   ```console
   Surface Drivers can be supported in this hierarchy since all SUPs are on Windows Server 2016, WCM SCF property Sync Catalog Drivers is set.

   sync: SMS synchronizing categories 
   sync: SMS synchronizing categories, processed 0 out of 311 items (0%)
   sync: SMS synchronizing categories, processed 311 out of 311 items (100%)
   sync: SMS synchronizing categories, processed 311 out of 311 items (100%)
   sync: SMS synchronizing updates

   Synchronizing update 7eaa0148-c42b-45fd-a1ab-012c82972de6 - Microsoft driver update for Surface Type Cover Integration
   Synchronizing update 2dcb07f8-37ec-41ef-8cd5-030bf24dc1d8 - Surface driver update for Surface Pen Pairing
   Synchronizing update 63067414-ae52-422b-b3d1-0382a4d6519a - Surface driver update for Surface UEFI
   Synchronizing update 8e4e3a41-a784-4dd7-9a42-041f43ddb775 - Surface driver update for Surface Integration
   Synchronizing update 7f8baee8-419f-47e2-918a-045a15a188e7 - Microsoft driver update for Surface DTX
   Synchronizing update aed66e05-719b-48cd-a0e7-059e50f67fdc - Microsoft driver update for Surface Base Firmware Update
   Synchronizing update 8ffe1526-6e66-43cc-86e3-05ad92a24e3a - Surface driver update for Surface UEFI
   Synchronizing update 74102899-0a49-48cf-97e6-05bde18a27ff - Microsoft driver update for Surface UEFI
   ```

##  <a name="deploying-surface-firmware-and-driver-updates"></a>Bereitstellen von Surface-Firmware und Treiberupdates

Sie können DGM-Firmware und Treiberupdates auf die gleiche Weise wie andere Updates bereitstellen.

Weitere Informationen zur Bereitstellung finden Sie unter [System Center 2012 Configuration Manager – Part7: Software Updates (Deploy)](https://blogs.technet.microsoft.com/elie/2012/05/25/system-center-2012-configuration-managerpart7-software-updates-deploy/).

##  <a name="frequently-asked-questions-faq"></a>Häufig gestellte Fragen

**Nachdem ich die in diesem Artikel beschriebenen Schritte ausgeführt habe, sind meine Oberflächen Treiber weiterhin nicht synchronisiert. Woran liegt das?**

Wenn Sie die Synchronisierung von einem Upstream-Server für Windows Server Update Services (WSUS) anstelle von Microsoft Update durchführen, stellen Sie sicher, dass der WSUS-Upstream-Server für die Unterstützung und Synchronisierung von Oberflächen Treiberupdates konfiguriert ist. Alle Downstreamserver sind auf Updates limitiert, die in der WSUS-Upstream-Server Datenbank vorhanden sind.

Es gibt mehr als 68.000-Updates, die in WSUS als Treiber klassifiziert werden. Um zu verhindern, dass nicht mit der Oberfläche Verwandte Treiber mit dem Configuration Manager synchronisiert werden, wird die Treiber Synchronisierung mit einer Zulassungsliste von Microsoft gefiltert. Nachdem die neue Zulassungsliste veröffentlicht und in Configuration Manager integriert wurde, werden die neuen Treiber der Konsole nach der nächsten Synchronisierung hinzugefügt. Microsoft hat sich zum Ziel gesetzt, die Oberflächen Treiber jeden Monat in Übereinstimmung mit monatlichen Updateversionen zur Liste "zulassen" hinzuzufügen, damit Sie für die Synchronisierung mit Configuration Manager zur Verfügung stehen.

Wenn Ihre Configuration Manager-Umgebung offline ist, wird jedes Mal, wenn Sie [Wartungsupdates](https://docs.microsoft.com/mem/configmgr/core/servers/manage/use-the-service-connection-tool) in Configuration Manager importieren, eine neue Zulassungsliste importiert. Darüber hinaus müssen Sie einen [neuen WSUS-Katalog](https://docs.microsoft.com/mem/configmgr/sum/get-started/synchronize-software-updates-disconnected) importieren, der die Treiber enthält, bevor die Updates in der Configuration Manager-Konsole angezeigt werden. Da eine eigenständige WSUS-Umgebung mehr Treiber als ein Configuration Manager-SUP enthält, empfiehlt es sich, eine Configuration Manager-Umgebung mit Online Funktionen zu erstellen und diese für die Synchronisierung von Oberflächen Treibern zu konfigurieren. Dadurch wird ein kleinerer WSUS-Export bereitgestellt, der der Offlineumgebung ähnlich ist.

Wenn Ihre Configuration Manager-Umgebung online ist und neue Updates erkennen kann, erhalten Sie automatisch Updates für die Liste. Wenn die erwarteten Treiber nicht angezeigt werden, überprüfen Sie die Dateien "WCM. log" und "WsyncMgr. log" auf etwaige Synchronisierungsfehler.

**Meine Configuration Manager-Umgebung ist offline. Kann ich Oberflächen Treiber manuell in WSUS importieren?**

Nein. Auch wenn das Update in WSUS importiert wurde, wird das Update nicht in die Configuration Manager-Konsole für die Bereitstellung importiert, wenn es nicht in der Zulassungsliste aufgeführt ist. Sie müssen das [Dienst Verbindungs Tool](https://docs.microsoft.com/mem/configmgr/core/servers/manage/use-the-service-connection-tool) verwenden, um Wartungsupdates in Configuration Manager zu importieren, um die Zulassungsliste zu aktualisieren.

**Welche alternativen Methoden sind für die Bereitstellung von Oberflächen Treiber-und Firmware-Updates verfügbar?**

Informationen zum Bereitstellen von Oberflächen Treiber-und Firmware-Updates über alternative Kanäle finden Sie unter [Verwalten von Oberflächen Treiber-und Firmware-Updates](manage-surface-driver-and-firmware-updates.md). Wenn Sie die MSI-oder exe-Datei herunterladen und dann über herkömmliche Software Bereitstellungskanäle bereitstellen möchten, lesen Sie [Aktualisieren der Surface-Firmware mit Configuration Manager](https://docs.microsoft.com/archive/blogs/thejoncallahan/keeping-surface-firmware-updated-with-configuration-manager).

##  <a name="additional-information"></a>Weitere Informationen

Weitere Informationen zu Oberflächen Treiber-und Firmware-Updates finden Sie in den folgenden Artikeln:

- [Verwalten von Treiber- und Firmwareupdates für Surface](manage-surface-driver-and-firmware-updates.md)
- [Überlegungen für Surface und System Center Configuration Manager](considerations-for-surface-and-system-center-configuration-manager.md)
