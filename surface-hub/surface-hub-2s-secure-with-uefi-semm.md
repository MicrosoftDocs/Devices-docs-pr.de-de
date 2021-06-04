---
title: Sichern und Verwalten von Surface Hub 2S mit Semm
description: Weitere Informationen zum Sichern des Surface Hub 2S mit Semm.
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
ms.openlocfilehash: 03ce1dfa48ade8aade545c63818ca5ae8947e6b7
ms.sourcegitcommit: 109d1d7608ac4667564fa5369e8722e569b8ea36
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/27/2020
ms.locfileid: "10832971"
---
# Sichern und verwalten von Surface Hub 2S mit SEMM und UEFI

Neu in Surface Hub 2S können Sie Semm verwenden, um die UEFI-Einstellung des Geräts zu verwalten.
Verwenden Sie den Microsoft Surface UEFI-Konfigurator, um die folgenden Komponenten zu steuern:

- Kabelgebundenes LAN
- Kameras
- Bluetooth
- WLAN
- Anwesenheitssensor

Verwenden Sie den Microsoft Surface UEFI-Konfigurator, um die folgenden UEFI-Einstellungen zu aktivieren oder zu deaktivieren:

- Start

    - IPv6 für PXE-Start
    - Alternativer Start
    - Sperre дер Startreihenfolge
    - USB-Start
- UEFI-Startseite

    - Geräte
    - Start
    - Datum/Uhrzeit

##  <a name="create-uefi-configuration-image"></a>Erstellen eines UEFI-Konfigurations Bilds

Im Gegensatz zu anderen Surface-Geräten können Sie keine MSI-Datei oder ein Win PE-Bild verwenden, um diese Einstellungen auf Surface Hub 2S anzuwenden. Stattdessen müssen Sie ein USB-Bild erstellen, das in das Gerät geladen werden soll. Laden Sie die neueste Version des Microsoft Surface UEFI-Konfigurators auf der Seite [Surface Tools für IT](https://www.microsoft.com/download/details.aspx?id=46703) im Microsoft Download Center herunter, und installieren Sie die aktuelle Version des Microsoft Surface UEFI-Konfigurators, um ein DGM-UEFI-Konfigurationsbild zu erstellen. Weitere Informationen zur Verwendung von UEFI und Semm finden Sie unter [Microsoft Surface Enterprise-Verwaltungsmodus](https://docs.microsoft.com/surface/surface-enterprise-management-mode).

##  <a name="to-configure-uefi-on-surface-hub-2s"></a>So konfigurieren Sie UEFI auf Surface Hub 2S

1. Starten Sie den UEFI-Konfigurator, und wählen Sie auf dem ersten Bildschirm **Konfigurationspaket**aus.<br><br>
![* Starten Sie den UEFI-Konfigurator und wählen Sie das Konfigurationspaket *](images/sh2-uefi1.png) <br> <br>
2. Um das Zertifikat zu Ihrem Paket hinzuzufügen, müssen Sie über ein gültiges Zertifikat mit dem privaten Schlüssel in einem PFX-Dateiformat verfügen, um das Paket zu signieren und zu schützen. Wählen Sie **+ Zertifikatschutz aus.** <br>
![* Wählen Sie + Zertifikatschutz *](images/sh2-uefi2.png) <br><br>
3. Geben Sie das Kennwort für den privaten Schlüssel des Zertifikats ein.<br>
![* Geben Sie das Kennwort des privaten Schlüssels des Zertifikats ein *](images/sh2-uefi3.png) <br><br>
4. Nachdem Sie den privaten Schlüssel importiert haben, fahren Sie mit dem Erstellen des Pakets fort.<br>
![* Fortsetzen des Erstellens des Pakets *](images/sh2-uefi4.png) <br><br>
5. Wählen Sie **Hub** und **Surface Hub 2S** als Ziel für das UEFI-Konfigurationspaket aus.<br>
![* Wählen Sie Hub und Surface Hub 2S als Ziel für das UEFI-Konfigurationspaket * aus.](images/sh2-uefi5.png) <br><br>
6. Wählen Sie die Komponenten und Einstellungen aus, die Sie auf Surface Hub 2S aktivieren oder deaktivieren möchten.<br>
![* Wählen Sie die Komponenten und Einstellungen aus, die Sie aktivieren oder deaktivieren möchten *](images/sh2-uefi6.png) <br><br>
7. Verwenden Sie die USB-Option, um die Datei zu exportieren.<br>
![* Verwenden Sie die USB-Option, um die Datei zu exportieren *](images/sh2-uefi8.png) <br><br>
8. Legen Sie das USB-Laufwerk ein, das Sie für dieses Paket verwenden möchten, und wählen Sie es aus. Das USB-Laufwerk wird formatiert, und Sie verlieren alle Informationen, die Sie dazu haben.<br>
![* Einfügen und auswählen des USB-Laufwerks für Ihr Paket *](images/sh2-uefi9.png) <br><br>
9. Nach erfolgreicher Erstellung des Pakets werden im Konfigurator die letzten beiden Zeichen des Fingerabdrucks des Zertifikats angezeigt. Sie benötigen diese Zeichen beim Importieren in die Konfiguration in Surface Hub 2S.<br>
![* Erfolgreiche Konfiguration des Pakets *](images/sh2-uefi10.png) <br>

##  <a name="to-boot-into-uefi"></a>So starten Sie in UEFI

Deaktivieren Sie Surface Hub 2S. Drücken Sie die **Lautstärke** Taste und halten Sie sie gedrückt, und drücken Sie die **Power** -Taste. Halten Sie die Lautstärketaste gedrückt, bis das UEFI-Menü angezeigt wird.
