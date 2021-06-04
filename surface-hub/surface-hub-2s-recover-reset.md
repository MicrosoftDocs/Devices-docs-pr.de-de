---
title: Zurücksetzen und Wiederherstellung für Surface Hub 2S
description: Erfahren Sie, wie Sie Surface Hub 2S wiederherstellen und zurücksetzen.
keywords: Trennen Sie Werte durch Kommata
ms.prod: surface-hub
ms.sitesec: library
author: greg-lindsay
ms.author: greglin
manager: laurawi
audience: Admin
ms.topic: article
ms.date: 12/05/2019
ms.localizationpriority: Medium
ms.openlocfilehash: 64ceee291d3d3e067f581707d9431fa92398c785
ms.sourcegitcommit: ecb4909c091e69b7bdb1faacfc8c34b480dc884b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/17/2021
ms.locfileid: "11342975"
---
# Zurücksetzen und Wiederherstellung für Surface Hub 2S

Wenn Probleme mit Surface Hub 2S auftreten, können Sie das Gerät auf die Werkseinstellungen zurücksetzen oder mithilfe eines USB-Laufwerks wiederherstellen.

Melden Sie sich zunächst bei Surface Hub 2S mit Administratoranmeldeinformationen an, öffnen Sie die **App** "Einstellungen", wählen Sie **"&** Aktualisieren" und dann "Wiederherstellung" **aus.**

##  <a name="reset-the-device"></a>Setzen Sie das Gerät zurück

   > [!IMPORTANT]
   > Stellen Sie sicher, dass Ihr BitLocker-Schlüssel verfügbar ist, bevor Sie das Gerät zurücksetzen, da Sie später dazu aufgefordert werden. Weitere Informationen finden Sie unter ["Speichern des BitLocker-Schlüssels".](save-bitlocker-key-surface-hub.md)

1. Um das Gerät zurückzusetzen, wählen Sie **"Erste Schritte" aus.**

2. Wenn das **Fenster "Bereit zum Zurücksetzen" dieses Gerätefensters** angezeigt wird, wählen Sie **"Zurücksetzen" aus.** 
  
   > [!IMPORTANT]
   > Wenn der Hub mit der Wiederherstellungspartition neu startet, werden Sie zur Eingabe des BitLocker-Schlüssels aufgefordert. Wenn Sie diese Eingabeaufforderung überspringen, kann die Zurücksetzung fehlschlagen. Sobald Sie den Schlüssel "BitLocker" eingeben, installiert der Hub das Betriebssystem von der Wiederherstellungspartition neu. Dies kann bis zu einer Stunde dauern.
  
3. Führen Sie zum Neukonfigurieren des Geräts das erste Setupprogramm aus.

4. Wenn Sie das Gerät mithilfe von Microsoft Intune oder einer anderen Verwaltungslösung für mobile Geräte verwalten, ziehen Sie den vorherigen Eintrag zurück, löschen Sie ihn, und registrieren Sie das neue Gerät erneut. Weitere Informationen finden Sie unter ["Entfernen von Geräten mithilfe von Wipe", "Zurückziehen" oder "Manuelles](https://docs.microsoft.com/intune/devices-wipe)Entfernen der Registrierung des Geräts".

   > [!div class="mx-imgBorder"]
   > ![*Zurücksetzen und Wiederherstellung für Surface Hub 2S*](images/sh2-reset.png)
   <br/>*Abbildung1. Zurücksetzen und Wiederherstellung für Surface Hub 2S* 

##  <a name="recover-surface-hub-2s-by-using-a-usb-recovery-drive"></a>Wiederherstellen von Surface Hub 2S mithilfe eines USB-Wiederherstellungslaufwerks

Neu in Surface Hub 2S: Sie können das Gerät jetzt mithilfe eines Wiederherstellungsabbilds neu installieren.

###  <a name="recovery-from-a-usb-drive"></a>Wiederherstellung von einem USB-Laufwerk

Mit Surface Hub 2S können Sie das Gerät mithilfe eines Wiederherstellungsabbilds neu installieren. Dadurch können Sie das Gerät in den Werkseinstellungen neu installieren, wenn Sie den BitLocker-Schlüssel verloren haben oder wenn Sie nicht mehr über Administratoranmeldeinformationen für die Einstellungs-App verfügen.

>[!NOTE]
>Verwenden Sie ein USB 3.0-Laufwerk mit 8 GB oder 16 GB Speicher, formatiert als FAT32.

1. Laden Sie von einem separaten PC das Wiederherstellungsimage der ZIP-Datei von der [Surface -Wiederherstellungswebsite](https://support.microsoft.com/surfacerecoveryimage?devicetype=surfacehub2s) herunter, und kehren Sie dann zu diesen Anweisungen zurück. 

1. Geben Sie in das Suchfeld auf der Taskleiste **** das Wiederherstellungslaufwerk **ein,** und wählen Sie dann in den Ergebnissen ein Wiederherstellungslaufwerk oder Wiederherstellungslaufwerk erstellen aus. **** Möglicherweise müssen Sie ein Administratorkennwort eingeben oder Ihre Auswahl bestätigen.

1. Wählen Sie **im Feld Benutzerkontensteuerung** **"Ja" aus.**

1. Stellen Sie sicher, dass Sie das **Kontrollkästchen "Systemdateien auf dem** Wiederherstellungslaufwerk sichern" aktivieren und dann **"Weiter" auswählen.**

1. Wählen Sie Ihr USB-Laufwerk aus, und wählen Sie dann **"Weiter > Erstellen" aus.**  Einige Hilfsprogramme müssen auf das Wiederherstellungslaufwerk kopiert werden, sodass dies einige Minuten dauern kann.

1. Wenn das Wiederherstellungslaufwerk bereit ist, wählen Sie **"Fertig stellen" aus.**

1. Doppelklicken Sie auf die ZIP-Wiederherstellungsabbilddatei, die Sie zuvor heruntergeladen haben, um sie zu öffnen.

1. Wählen Sie alle Dateien aus dem Wiederherstellungsimageordner aus, kopieren Sie sie in das Stammverzeichnis Ihres USB-Laufwerks, und wählen Sie dann "Auswählen, um die Dateien im Ziel **zu ersetzen" aus.**

1. Sobald die Dateien kopiert wurden, wählen Sie auf der Taskleiste das Symbol "Hardware sicher entfernen" und **"Eject Media"** aus, und entfernen Sie das USB-Laufwerk.

1. Schließen Sie das #A0 an einen beliebigen USB-C- oder #A1 auf dem Surface Hub 2S an.

1. Deaktivieren Sie den Hub, und gehen Sie dann wie im Folgenden vor, um vom USB-Laufwerk zu starten:

   1. Drücken Sie beim Drücken der Taste "Lautstärke nach unten" die Ein-/Aus-Taste.
   1. Drücken Sie weiterhin beide Tasten, bis das Windows-Logo angezeigt wird.
   1. Lassen Sie die Ein/Aus-Taste los, halten Sie jedoch die Schaltfläche "Volume down" gedrückt, bis die Installation der Benutzeroberfläche beginnt.

      ![*Verwenden der Tasten "Volume down" und "Power", um die Wiederherstellung zu initiieren*](images/sh2-keypad.png)
      <br>*Abbildung2. Lautstärke- und Netztasten*

1. Wählen Sie auf dem Sprachauswahlbildschirm die Anzeigesprache für Surface Hub 2S aus.

1. Wählen **Sie "Von einem Laufwerk wiederherstellen"** aus, und **bereinigen**Sie das Laufwerk vollständig, und wählen Sie dann "Wiederherstellen" **aus.** Wenn Sie zur Eingabe eines BitLocker-Schlüssels aufgefordert werden, wählen Sie **"Dieses Laufwerk überspringen" aus.** Surface Hub 2S wird mehrmals neu gestartet und benötigt ca. 30 Minuten, um den Wiederherstellungsvorgang abschließen zu können.

Wenn der Bildschirm zum ersten Einrichten angezeigt wird, entfernen Sie das USB-Laufwerk.

##  <a name="contact-support"></a>Hilfe und Support zu Windows

Wenn Sie Fragen haben oder Hilfe benötigen, können [Sie eine Supportanfrage erstellen.](https://support.microsoft.com/supportforbusiness/productselection)
