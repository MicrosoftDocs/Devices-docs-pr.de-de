---
title: Migrieren zu Windows 10 Pro oder Enterprise auf Surface Hub 2
description: Migrieren von Windows 10 Team auf Surface Hub 2 zu Windows 10 Pro oder Windows 10 Enterprise.
keywords: Surface Hub Desktop, Surface Hub
ms.prod: surface-hub
ms.sitesec: library
author: greg-lindsay
ms.author: greglin
manager: laurawi
audience: Admin
ms.topic: article
ms.date: 12/14/2020
ms.localizationpriority: Medium
ms.openlocfilehash: 472dc41bd73ace90cccdeb4e52884401c2f9d6d7
ms.sourcegitcommit: 267e12897efd9d11f8c7303eaf780632741cfe77
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/22/2021
ms.locfileid: "11613854"
---
# <a name="migrate-to-windows-10-pro-or-enterprise-on-surface-hub-2"></a>Migrieren zu Windows 10 Pro oder Enterprise auf Surface Hub 2

- [Artikelversionsverlauf](#version-history)

Surface Hub 2S ist mit Windows 10 Team installiert. Diese angepasste Edition von Windows 10 erleichtert die Zusammenarbeit in Besprechungsraumumgebungen. Sie können jetzt stattdessen Windows 10 Pro oder Enterprise ausführen, um Ihre Surface Hub 2S ähnlich wie jeder andere PC zu verwenden.

> [!IMPORTANT]
> Für diesen Migrationsprozess müssen Sie das in diesem Artikel beschriebene Verfahren befolgen. Lesen Sie vor dem Fortfahren [die Lösungskomponenten](#solution-components) und [den Migrations- und Installationsworkflow.](#migration-and-installation-workflow-summary)

> [!NOTE]
> Wenn Sie Windows 10 Pro oder Enterprise auf Ihrem Surface Hub 2S installieren, benötigen Sie eine neue Lizenz, die sich von der vorhandenen Windows 10 Team Lizenz unterscheidet, die mit dem Gerät bereitgestellt wird.

Starten Sie die Migration von Windows 10 Team mithilfe eines separaten PCs und des herunterladbaren *Surface UEFI Configurator-Tools.* Das Tool erstellt ein Paket, das eine neue UEFI-Einstellung enthält, die Sie auf die Surface Hub 2S anwenden.  

Surface UEFI Configurator funktioniert als Schnittstelle im Surface Enterprise Management Mode (SEMM). Es ermöglicht die zentrale Verwaltung von Firmwareeinstellungen auf Surface-Geräten in einer Unternehmensumgebung. Weitere Informationen finden Sie unter [Microsoft Surface Enterprise Verwaltungsmodus.](/surface/surface-enterprise-management-mode)
 
## <a name="solution-components"></a>Lösungskomponenten

- Surface Hub 2S-Gerät, auf dem Windows 10 Team ausgeführt wird
- Separates Gerät, auf dem Windows 10 ausgeführt wird
- Surface UEFI Configurator-Tool zum Erstellen des SEMM-Pakets
- Windows 10 Pro oder Enterprise Betriebssystemimage, Version 1903 oder höher
- Zwei USB-Laufwerke mit 16 GB Speicher, FAT32-Format
- Treiber und Firmware für Windows 10 Pro und Enterprise in einer MSI-Datei (Microsoft Windows Installer) Surface Hub 2
- Internetverbindung
- Imaging-Lösung (optional)
 
## <a name="migration-and-installation-workflow-summary"></a>Zusammenfassung des Migrations- und Installationsworkflows

| Schritt  | Aktion                                                                                                 | Zusammenfassung                                                                                                                                                                                                                                                                                                                                                                                                  |
| - | ------------------------------------------------------------------------------------------------------ | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| 1 | [Überprüfen Sie die UEFI-Version im Surface Hub 2S.](#verify-the-uefi-version-on-surface-hub-2s)                                  | Die UEFI-Version muss Version *694.2938.768.0* oder höher sein.                                                                                                                                                                                                                                                                                                                                                      |
| 2 | [Laden Sie Surface UEFI Configurator und die Treiber und Firmware der Surface Hub 2 herunter.](#download-surface-uefi-configurator-and-surface-hub-2-drivers-and-firmware)                             | Wählen Sie auf der Seite **[Surface Tools for IT](https://www.microsoft.com/download/details.aspx?id=46703)** die Option </a> **"Herunterladen"** aus. Wählen Sie dann die **SURFACE UEFI Configurator-MSI-Datei**aus, laden Sie sie herunter, und installieren Sie sie auf einem separaten PC. Laden Sie außerdem die [Treiber und firmware für Windows 10 Pro und Enterprise Betriebssystem auf Surface Hub 2 MSI-Datei](https://www.microsoft.com/download/details.aspx?id=101974)herunter.</a> Speichern Sie dieses Paket zur Verwendung in Schritt 5. |
| 3 | [Bereiten Sie das SEMM-Zertifikat vor.](#prepare-the-semm-certificate)                                                                          | Bereiten Sie das Zertifikat vor, das zum Ausführen von Surface UEFI Configurator erforderlich ist, oder verwenden Sie das aktuelle Zertifikat.                                                                                                                                                                                                                                                                                                      |
| 4 | [Erstellen Sie ein SEMM-Paket.](#create-a-semm-package)                                                                               | Starten Sie Surface UEFI Configurator, um ein SEMM-Paket auf einem USB-Laufwerk zu erstellen. Dieses Paket enthält die Konfigurationsdateien, die Sie auf Surface Hub 2S anwenden müssen. Kopieren Sie diese SEMM-Paketdateien in einen Ordner auf Ihrem PC.                                                                                                                                                                                          |
| 5 | [Laden Sie einen USB-Speicherstick mit Windows 10 Image, dem SEMM-Paket sowie Treibern und Firmware.](#load-a-usb-flash-drive-with-a-windows-10-image-semm-package-and-surface-hub-2-drivers-and-firmware) | Erstellen Sie ein USB-Laufwerk, das ein Windows 10-Image enthält. In diesem Beispiel heißt das Laufwerk *BOOTME.* Fügen Sie dem *BOOTME-Laufwerk* die Treiber und die Firmware für Windows 10 Pro und Enterprise Betriebssystem unter Surface Hub 2 (aus Schritt 2) und die SEMM-Paketdateien (aus Schritt 4) hinzu.                                                                                                                                                                                                  |
| 6 | [Aktualisieren Sie die UEFI im Surface Hub 2S, um die Betriebssystemmigration zu aktivieren.](#update-uefi-on-surface-hub-2s-to-enable-os-migration)                                              | Verwenden Sie das *BOOTME-Laufwerk,* um die Surface Hub 2S mit dem UEFI-Menü zu starten und das SEMM-Paket zu installieren.|
| 7 | [Installieren Sie Windows 10 Pro oder Enterprise.](#install-windows-10-pro-or-enterprise)                                        | Verwenden Sie das *BOOTME-Laufwerk,* um Windows 10 Pro oder Enterprise Version 1903 oder höher zu installieren.                                                                                                                                                                                                                                                                                 |
| 8 | [Installieren Sie Treiber und Firmware für Windows 10 Pro und Enterprise.](#install-surface-hub-2-drivers-and-firmware)                                        | Um sicherzustellen, dass Ihr Gerät über die neuesten Updates und Treiber verfügt, installieren Sie die <a href="https://www.microsoft.com/download/details.aspx?id=101974" target="_blank"> Treiber und die Firmware für Windows 10 Pro und Enterprise Betriebssystem auf Surface Hub 2 MSI-Datei.</a>                                                                                                                                                                                                                                                                                  |
| 9 | [Konfigurieren Sie Surface Hub 2S als persönliches Produktivitätsgerät.](#configure-recommended-settings)                                        |  Aktivieren Sie die empfohlenen Einstellungen und Anwendungen, um Surface Hub 2S als persönliches Produktivitätsgerät zu optimieren.                                                                                                                                                                                                                                                                    |

### <a name="verify-the-uefi-version-on-surface-hub-2s"></a>Überprüfen der UEFI-Version in Surface Hub 2S

Bevor Sie Surface Hub von Windows 10 Team zu Windows 10 Desktop migrieren, benötigen Sie UEFI-Version *694.2938.768.0* oder höher.
 
**So überprüfen Sie die UEFI-Version auf Ihrem System:**

1. Wählen Sie auf der startseite Surface Hub 2S die Option **"Start"** aus, und öffnen Sie dann die Surface-App (**Alle Apps**  >  **Surface**).

2. Wählen Sie **Surface** aus, um Informationen zu Surface Hub anzuzeigen, einschließlich der aktuellen UEFI-Version auf dem Gerät. 
   - Wenn die UEFI-Version *694.2938.768.0* oder höher ist, wie in der folgenden Abbildung dargestellt, können Sie das SEMM-Paket erstellen, um die Betriebssystemmigration zu aktivieren.

       ![Screenshot der Seite "Ihr Surface" in der Surface-App.](images/shm-fig1.png)
 
   - Wenn die UEFI-Version vor Version *694.2938.768.0*liegt, verwenden Sie eine der folgenden Methoden, um eine neuere Version abzurufen.
   
#### <a name="update-uefi-via-windows-update"></a>Aktualisieren von UEFI über Windows Update

1. Melden Sie sich in Ihrem Surface Hub 2S als **Administrator**an.

    >[!Note]
    > Wenn Sie Ihren Benutzernamen oder Ihr Administratorkennwort nicht kennen, müssen Sie das Gerät zurücksetzen. Weitere Informationen finden Sie unter [Reset and Recovery for Surface Hub 2S](/surface-hub/surface-hub-2s-recover-reset).

1. Wechseln Sie zu **"Alle Apps**  >  **Einstellungen**  >  **Update- und**  >  **Sicherheitsupdates Windows",** und installieren Sie alle Updates.
1. Starten Sie das Gerät neu.
1. Überprüfen Sie die UEFI-Version mithilfe der Surface-App. Wenn die UEFI-Version nicht Version *694.2938.768.0* oder höher ist, wiederholen Sie diese Schritte, oder verwenden Sie das folgende Verfahren, um die neueste UEFI-Version abzurufen.

#### <a name="update-the-uefi-via-bare-metal-recovery-bmr-image"></a>Aktualisieren des UEFI-Images über die Bare-Metal-Wiederherstellung (BMR)

1.  Wechseln Sie zur [Surface-Wiederherstellungswebsite,](https://support.microsoft.com/surfacerecoveryimage) und wählen Sie **Surface Hub 2S**aus.
3.  Geben Sie Ihre Hub-Seriennummer ein. Er befindet sich auf der Rückseite des Hubs neben der Stromversorgung.
4.  Befolgen Sie die Anweisungen, um das Image auf ein formatiertes USB-Laufwerk herunterzuladen, indem Sie das Windows 10 Team 2020 Update installieren.
5.  Nach dem Update wird das Gerät in die Windows-Willkommensseite (OoBE) eingerichtet. Sie müssen das Setup nicht abschließen. Die UEFI-Version wurde bereits aktualisiert. Schalten Sie stattdessen das Gerät ein, indem Sie den Netzschalter gedrückt halten, bis der Bildschirm ausgeschaltet wird.

### <a name="download-surface-uefi-configurator-and-surface-hub-2-drivers-and-firmware"></a>Herunterladen von Surface UEFI Configurator- und Surface Hub 2-Treibern und Firmware

Führen Sie auf einem separaten PC die folgenden Schritte aus:

1. Wählen Sie auf der <a href="https://www.microsoft.com/download/details.aspx?id=46703" target="_blank"> Seite Surface Tools for IT die Option </a> **"Herunterladen"** aus.  
1. Wählen Sie die Surface UEFI Configurator-MSI-Datei aus, laden Sie sie herunter, und installieren Sie sie auf einem separaten PC. Das Surface UEFI Configurator-Tool kann nicht auf einem Surface Hub 2S ausgeführt werden, während Windows 10 Team Edition installiert ist.

1. Laden Sie die [MSI-Datei Surface Hub 2 Treiber und Firmware Windows Installer](https://www.microsoft.com/download/details.aspx?id=101974)herunter. Sie verwenden diese Datei, wenn Sie das neue Betriebssystem installieren.

### <a name="prepare-the-semm-certificate"></a>Vorbereiten des SEMM-Zertifikats

Wenn Sie Surface UEFI Configurator noch nicht verwendet haben, müssen Sie ein Zertifikat vorbereiten. Dieses Zertifikat stellt sicher, dass Sie nach der Registrierung eines Geräts in SEMM UEFI-Einstellungen nur mithilfe von Paketen ändern können, die mit dem genehmigten Zertifikat erstellt wurden.

Wie Sie ein Zertifikat erhalten, hängt von der Größe oder Komplexität Ihrer Organisation ab:

- Enterprise Organisationen verwalten in der Regel ihre eigene Infrastruktur, um Zertifikate gemäß den Standardsicherheitsmethoden zu generieren.

- Mittelständische Unternehmen und andere Unternehmen entscheiden sich häufig dafür, Zertifikate von Partneranbietern zu erhalten. Diese Option wird für Organisationen empfohlen, die nicht über so viel IT-Erfahrung verfügen oder über ein dediziertes IT-Sicherheitsteam verfügen.

- Alternativ können Sie ein selbstsigniertes Zertifikat mithilfe eines PowerShell-Skripts generieren. Weitere Informationen finden Sie unter den [Zertifikatanforderungen für den Surface Enterprise-Verwaltungsmodus.](/surface/surface-enterprise-management-mode#surface-enterprise-management-mode-certificate-requirements) Sie können auch PowerShell verwenden, um Ein eigenes Zertifikat zu erstellen. Weitere Informationen finden Sie in der [Selbstsignierungszertifikatdokumentation.](/dotnet/core/additional-tools/self-signed-certificates-guide#create-a-self-signed-certificate)

Das semm package that Surface UEFI Configurator creates must be secured with a certificate. Das Zertifikat überprüft die Signatur von Konfigurationsdateien, bevor UEFI-Einstellungen angewendet werden können. Weitere Informationen finden Sie in der [SEMM-Dokumentation.](/surface/surface-enterprise-management-mode)
 
### <a name="create-a-semm-package"></a>Erstellen eines SEMM-Pakets

1. Installieren Sie auf einem separaten PC das Surface UEFI Configurator-Tool, das Sie zuvor heruntergeladen haben.

1. Öffnen Sie Surface UEFI Configurator, und wählen Sie dann **Start**aus.

   ![Surface UEFI Configurator-Startbildschirm.](images/shm-fig2.png)
   
1. Wählen Sie **Surface Devices**und dann **"Weiter"** aus.

   ![Der Screenshot zeigt die ausgewählte Surface Devices-Option.](images/shm-fig3.png)
  
1. Wählen Sie **"Konfigurationspaket" aus.**

   ![Screenshot: "Konfigurationspaket auswählen" ausgewählt.](images/shm-fig4.png)
  
1. Wählen Sie **"Zertifikatschutz" aus.**

   ![Screenshot: Wählen Sie "Zertifikatschutz auswählen" aus.](images/shm-fig5.png)

   Sie werden aufgefordert, Ihre PFX-Zertifikatdatei hinzuzufügen.

   ![Der Screenshot zeigt, wo Die Zertifikatdatei hinzugefügt werden soll.](images/shm-fig6.png)
   
1. Geben Sie Ihr Zertifikatkennwort ein, und wählen Sie dann **OK**aus.

   ![Screenshot: Felder zum Eingeben und Bestätigen ihres Zertifikatkennworts.](images/shm-fig7.png)

1. Wählen Sie **"Kennwortschutz"** aus, um surface UEFI ein Kennwort hinzuzufügen. Sie benötigen dieses Kennwort, wenn Sie mit der UEFI starten. *Es wird dringend empfohlen, ein UEFI-Kennwort festzulegen, das Sie für Surface Hub 2S verwenden.*

   ![Screenshot zeigt, wo Kennwortschutz ausgewählt werden soll.](images/shm-fig8.png)
   
1. Legen Sie ein UEFI-Kennwort fest, und wählen Sie dann **OK**aus.

   > [!IMPORTANT]
   > Speichern Sie das Kennwort an einem sicheren Ort, auf den Ihre IT-Administratoren, die Surface Hub verwalten, zugegriffen werden kann. *Wenn dieses Kennwort verloren geht, kann es nicht wiederhergestellt werden.*

   ![Screenshot zeigt, wo Sie das UEFI-Kennwort festlegen.](images/shm-fig9.png)

1. Wählen Sie **Surface Hub 2S**aus, und klicken Sie dann auf **"Weiter".**

    ![Screenshot zeigt, wo Surface Hub 2S ausgewählt werden soll.](images/shm-fig10.png)
   
1. Wählen Sie erneut **"Weiter"** aus.

    ![Screenshot der Option "Weiter" unter "Auswählen der Komponenten".](images/shm-fig10a.png)

1. Um die Installation von Windows 10 Pro oder Enterprise zuzulassen, aktivieren **Sie EnableOsMigration,** und wählen Sie dann **"Weiter"** aus.

    ![Screenshot zeigt, wo Sie O S-Migration aktivieren auswählen können.](images/shm-fig11.png)
    
    ![Screenshot zeigt, wo die Aktivierung der Betriebssystemmigration aktiviert werden soll.](images/shm-fig12.png)

### <a name="manage-semm-enrollment"></a>Verwalten der SEMM-Registrierung

Die Registrierung eines Geräts bei SEMM wirkt sich darauf aus, wie Sie es verwalten können. Beispielsweise sind nach dem Anwenden eines SEMM-Pakets alle UEFI-Einstellungen im UEFI-Menü des Geräts nicht verfügbar (gesperrt). Standardwerte für andere Einstellungen, z. **B. IPv6 für PXE-Start,** sind ebenfalls nicht verfügbar.

Um die UEFI-Einstellungen nach Abschluss der Migration zu ändern, wenden Sie ein anderes SEMM-Paket an, oder heben Sie die Registrierung des Geräts von SEMM auf. Wenn Sie ein anderes SEMM-Paket anwenden, um die UEFI-Einstellungen zu ändern, müssen Sie beim Erstellen des neuen SEMM-Pakets das ursprüngliche Zertifikat verwenden. Verwenden Sie das UEFI-Configurator-Tool, und lassen **Sie EnableOSMigration** *deaktiviert* *(nicht* wie in den ursprünglichen Migrationsschritten).

#### <a name="if-you-work-with-partners"></a>Wenn Sie mit Partnern zusammenarbeiten

Wenn Ihr Unternehmen die Migration Surface Hub 2 an Windows 10 Pro oder Enterprise auslagert, empfiehlt es sich, dass der Partner das SEMM-Zertifikat, das SEMM-Paket und das UEFI-Kennwort an Sie überträgt. Oder Sie können nach der Migration des Hubs die Registrierung sofort von SEMM aufheben. Dieser Schritt ermöglicht die lokale Verwaltung von UEFI und die Übertragung des Geräts an eine andere Partei. Es wird jedoch weiterhin dringend empfohlen, ein UEFI-Kennwort zu verwenden, das nach der Migration konfiguriert werden kann. Weitere Informationen finden Sie unter [Verwalten von Surface UEFI-Einstellungen.](/surface/manage-surface-uefi-settings) 

#### <a name="to-roll-back-to-windows-10-team"></a>So führen Sie ein Rollback auf Windows 10 Team

Wenn Sie ihr Gerät nach der Migration [wie weiter](#to-roll-back-to-windows-10-team)unten in diesem Artikel beschrieben in Windows 10 Team wiederherstellen möchten, wird empfohlen, die Registrierung von Hub von SEMM aufzuheben. Weitere Informationen finden Sie unter [Aufheben der Registrierung von Surface-Geräten aus SEMM.](/surface/unenroll-surface-devices-from-semm)

#### <a name="save-the-semm-package-to-a-usb-drive"></a>Speichern des SEMM-Pakets auf einem USB-Laufwerk

1. Verbinden sie ihrem PC ein USB-Laufwerk zu.
1. Wählen Sie **"Hub 2S"** und dann **"Weiter"** aus.

   ![Screenshot zeigt, wo Hub 2S ausgewählt werden soll](images/shm-fig13.png)

   > [!WARNING]
   > Alle vorhandenen Daten auf dem USB-Laufwerk werden gelöscht, wenn das SEMM-Paket erstellt wird. Entfernen Sie vor dem Erstellen des SEMM-Pakets alle benötigten Dateien vom USB-Laufwerk.
   
1. Wählen Sie **Erstellen** aus.

   ![Screenshot zeigt, wo Build ausgewählt werden soll.](images/shm-fig14.png)

1. Erfassen Sie einen Screenshot dieser Seite, und wählen Sie dann **"Beenden"** aus. Ihr SEMM-Paket ist jetzt bereit. Es enthält das SEMM-Paket *"DfciUpdate.dfi"* und eine Textdatei, die den SEMM-Fingerabdruck enthält, also die letzten beiden Zeichen des Fingerabdrucks des Zertifikats. **

   ![Screenshot zeigt, wo "Ende" ausgewählt werden soll.](images/shm-fig15.png)
   
4. Speichern Sie die letzten beiden Zeichen des Zertifikatfingerabdrucks. Sie benötigen diese Zeichen, um SEMM zu aktivieren, wenn Sie das Paket auf Surface Hub 2S anwenden.

### <a name="load-a-usb-flash-drive-with-a-windows-10-image-semm-package-and-surface-hub-2-drivers-and-firmware"></a>Laden eines USB-Speichersticks mit einem Windows 10-Image, einem SEMM-Paket und Surface Hub 2 Treibern und Firmware

Mit einer der folgenden Optionen können Sie ein Windows 10 Pro- oder Enterprise-Image (Version *1903* oder höher) installieren:

- Ihre aktuelle Imageerstellungslösung.

- [Surface Deployment Accelerator](/surface/microsoft-surface-deployment-accelerator). Verwenden Sie dieses Tool, um ein startbares Windows 10 Image zu erstellen. Das Image kann alle aktuellen Windows 10 Updates, Microsoft Office, andere Apps sowie die erforderlichen Treiber und Firmware enthalten.

- Ein USB-Speicherstick, der ein Windows 10 Pro- oder Enterprise-Image enthält. Diese Option verfügt erst nach der Windows-Willkommensseite (Out-of-Box-Experience, OOBE) über Wi-Fi. Sobald die Einrichtung abgeschlossen ist, installieren Sie die erforderlichen [Surface Hub 2 Treiber und Firmware für Windows 10 Pro und Enterprise](https://www.microsoft.com/download/details.aspx?id=101974) auf dem Gerät.
 
Die folgenden Schritte zeigen, wie Sie einen USB-Speicherstick von Installationsmedien erstellen und dann die SEMM-Paketdateien sowie die Treiber und die Firmware für Windows 10 Pro und Enterprise Betriebssystem auf Surface Hub 2 MSI-Datei hinzufügen. Wenn Sie eine andere Bereitstellungsmethode verwenden, wechseln Sie zum [Abschnitt "Update UEFI on Surface Hub 2S", um](#update-uefi-on-surface-hub-2s-to-enable-os-migration) den Abschnitt zur Betriebssystemmigration in diesem Artikel zu aktivieren.

> [!NOTE]
> Nach Abschluss der Installation benötigen Sie eine gültige Lizenz für Windows 10 Pro oder Windows 10 Enterprise, die von Ihrer vorhandenen Windows 10 Team-Lizenz getrennt ist.

1. Um eine Windows 10 Pro Installation zu erstellen, befolgen Sie die Anweisungen zum Herunterladen des Medienerstellungstools unter [Download Windows 10](https://www.microsoft.com/software-download/windows10). Um Windows 10 Enterprise herunterzuladen, wechseln Sie zum [Microsoft Volume Licensing Service Center.](https://www.microsoft.com/licensing/servicecenter/default.aspx)

1. Fügen Sie ein neues USB-Speicherlaufwerk ein.
1. Öffnen Sie das Medienerstellungstool, wählen **Sie "Installationsmedien erstellen"** und dann **"Weiter"** aus.

   ![Screenshot zeigt die Option zum Erstellen von Installationsmedien.](images/shm-fig16.png)
   
3. Wählen Sie eine Sprache aus, und wählen Sie dann **Windows 10** und **64-Bit (x64)** aus. Klicken Sie dann auf **"Weiter".**

   ![Der Screenshot zeigt, wo Sie die Sprache, die O S-Edition und den Architekturtyp auswählen.](images/shm-fig17.png)
   
4. Wählen Sie **USB-Speicherstick**und dann **"Weiter"** aus.

   ![Der Screenshot zeigt, wo sie den S B-Speicherstick auswählen können.](images/shm-fig18.png)
   
5. Wenn der Download abgeschlossen ist, wählen Sie **Fertig stellen**aus.

   ![Der Bildschirm meldet, dass das U S B-Laufwerk bereit ist, und enthält eine Schaltfläche "Fertig stellen".](images/shm-fig19.png)
   
6. Kopieren Sie die SEMM-Paketdateien sowie die Treiber und die Firmware für Windows 10 Pro und Enterprise Betriebssystem auf Surface Hub 2 (MSI-Datei) in den Stamm des USB-Speichersticks *(BOOTME),* der Ihr Windows 10-Image enthält. Das BOOTME-USB-Laufwerk enthält Folgendes:

    - Ihr Windows 10 startbares Image.
    
    - Die SEMM-Paketdateien, die in den Stamm des USB-Laufwerks kopiert wurden:
    
      - *DfciUpdate.dfi*.
      - Eine Textdatei, die den SEMM-Fingerabdruck enthält. (In diesem Beispiel ist die Datei *SurfaceUEFI_2020Aug25_1058.txt.) * Der automatisch generierte Datum-Uhrzeit-Stempel entspricht dem Datum, an dem Sie die Datei mithilfe von Surface UEFI Configurator erstellt haben.

   - Treiber und Firmware für Windows 10 Pro und Enterprise Betriebssystem unter Surface Hub 2 (SurfaceHub2S_Win10_18362_20.082.25682.0.msi). Kopieren Sie diese Datei in den Stamm des USB-Laufwerks.

### <a name="update-uefi-on-surface-hub-2s-to-enable-os-migration"></a>Aktualisieren von UEFI auf Surface Hub 2S zum Aktivieren der Betriebssystemmigration

1. Fügen Sie ihr BOOTME-Laufwerk an den USB-A-Anschluss auf dem Surface Hub 2S ein. Eine Liste der erforderlichen Inhalte finden Sie im vorherigen Abschnitt.

1. So starten Sie UEFI:

   1. Schalten Sie Ihre Surface Hub 2S aus (herunterfahren).
   1. Drücken und halten **Sie Lautstärke +** und drücken Und lassen Sie dann den Netzschalter los. Halten Sie **weiterhin Volume+ gedrückt,** bis das UEFI-Menü angezeigt wird.
   
      ![Die Zeichnung zeigt die Lautstärke- und Netzschalter.](images/shm-fig20.png)
      
3. Wenn das Gerät neu gestartet wird, geben Sie ggf. das zuvor erstellte UEFI-Kennwort ein.

   ![Bildschirm "Systemkennwort".](images/shm-fig22.png)
   
4. Wählen Sie im UEFI-Menü die Option **"Verwaltung"** aus. Wählen Sie dann **über USB installieren aus.**

   ![Der Screenshot zeigt, wo Sie "Verwaltung" und dann "Aus U S B installieren" auswählen.](images/shm-fig21.png)
   
5. Wählen Sie **jetzt neu starten**aus, wie die folgende Abbildung zeigt. Das Gerät wird neu gestartet. In der Mitte des Fensters wird ein weißes Microsoft-Logo angezeigt und dann heruntergefahren.

   ![Der Screenshot zeigt eine Meldung, in der Sie zum Neustart aufgefordert werden.](images/shm-fig25.png)
   
6. Drücken und lassen Sie den Netzschalter los. Wählen Sie im daraufhin angezeigten roten Dialogfeld die Aktivierung des Surface Enterprise-Verwaltungsmodus aus.

7. Geben Sie ihren aus zwei Zeichen bestehenden Zertifikatfingerabdruck und Ihr Kennwort für die UEFI-Einstellungen ein. Wählen Sie dann **OK**aus.

   ![Der Screenshot zeigt das Dialogfeld "Bestätigungsaktivierung", in dem Sie den Fingerabdruck ihres zweistelligen Zertifikats und Ihr Kennwort für die UEFI-Einstellungen eingeben.](images/shm-fig23.png)
 
   > [!NOTE]
   > Nachdem Sie SEMM auf Ihrem Gerät aktiviert haben, wird die neue UEFI-Einstellung **"EnableOSMigration"** angewendet. Sie können nicht mehr auf Windows 10 Team zugreifen. Stattdessen müssen Sie mit dem nächsten Schritt fortfahren und Windows 10 Pro oder Windows 10 Enterprise installieren.

   Das Gerät wird neu gestartet. Es zeigt das weiße Logo in der Mitte des Bildschirms an und wird dann erneut heruntergefahren.

### <a name="install-windows-10-pro-or-enterprise"></a>Installieren Windows 10 Pro oder Enterprise

1. Wenn sich ihr startbares Windows 10 Pro oder Enterprise Laufwerk noch nicht im Surface Hub 2 USB-A-Anschluss befindet, fügen Sie es jetzt ein. Drücken und lassen Sie dann den Netzschalter los.

    Wenn das Gerät gestartet wird, wird das weiße Logo in der Mitte des Bildschirms angezeigt. Anschließend wird unterhalb des weißen Logos ein kreisförmiger Kreis angezeigt.

3. Wenn das Surface-Gerät nicht automatisch mit dem USB-Laufwerk gestartet wird, schalten Sie das Gerät aus (ziehen Sie das Netzkabel ab, und schließen Sie es wieder an). Nachdem Sie das Netzkabel erneut angeschlossen haben, sollte das Gerät nach ein paar Sekunden gestartet werden. Dann wird das weiße Logo in der Mitte des Bildschirms angezeigt.

    Wenn das Gerät nicht eingeschaltet wird, drücken und lassen Sie den Netzschalter los. Unmittelbar nachdem das Logo in der Mitte des Bildschirms angezeigt wurde, drücken Und halten Sie die Taste "Leiser" gedrückt, bis der kreisende Kreis unterhalb des weißen Logos angezeigt wird.
 
   ![Abbildung der Lautstärke- und Netzschalter.](images/shm-fig26.png)
   
4. Wenn das Setup der Windows-Willkommensseite gestartet wird, befolgen Sie die Anweisungen, um Windows 10 Pro oder Enterprise (Version 1903 oder höher) zu installieren.

### <a name="install-surface-hub-2-drivers-and-firmware"></a>Installieren Surface Hub 2 Treiber und Firmware

Um sicherzustellen, dass Ihre Surface Hub 2 auf dem neuesten Stand ist, installieren Sie [Treiber und Firmware für Windows 10 Pro und Enterprise.](https://www.microsoft.com/download/details.aspx?id=101974) Starten Sie dann das Gerät neu. Lassen Sie das Surface eine Stunde lang eingeschaltet, und starten Sie es dann erneut. Sie werden nicht zum zweiten Neustart aufgefordert. Durch diese Unterbrechung und einen zusätzlichen Neustart wird sichergestellt, dass die Firmware vollständig aktualisiert wurde.
 
## <a name="configure-recommended-settings"></a>Konfigurieren empfohlener Einstellungen

Informationen zum Konfigurieren Surface Hub 2S als persönliches Produktivitätsgerät finden Sie unter [Konfigurieren von Windows 10 Pro oder Enterprise auf Surface Hub 2.](surface-hub-2-post-install.md)

> [!NOTE]
>Wenn Sie Ihr Gerät nicht erfolgreich zu Windows 10 Pro oder Enterprise für Surface Hub 2 migrieren können, indem Sie die in diesem Artikel beschriebenen Schritte ausführen, wenden Sie sich an [Surface Hub Support.](https://support.microsoft.com/help/4037644/surface-contact-surface-warranty-and-software-support)

## <a name="to-roll-back-to-windows-10-team"></a>So führen Sie ein Rollback auf Windows 10 Team

Wenn Sie Ihr Gerät auf Windows 10 Team wiederherstellen möchten, finden Sie unter ["Zurücksetzen und Wiederherstellen" Surface Hub 2S.](surface-hub-2s-recover-reset.md)

> [!NOTE]
> Bevor Sie ein Rollback auf Windows 10 Team ausführen, sollten Sie zunächst die Registrierung der Surface Hub von SEMM aufheben. Weitere Informationen finden Sie unter [Aufheben der Registrierung von Surface-Geräten aus SEMM.](/surface/unenroll-surface-devices-from-semm)

## <a name="version-history"></a>Versionsverlauf

In der folgenden Tabelle sind die Änderungen an diesem Artikel zusammengefasst.

| Version | Datum               | Beschreibung                                                                                           |
| ------- | ------------------ | ----------------------------------------------------------------------------------------------------- |
| V. 1.4  | 14. Dezember 2020 | Enthält [weitere Informationen](#install-surface-hub-2-drivers-and-firmware) zum Installieren der MSI-Datei für "Treiber und Firmware für Windows 10 Pro und Enterprise Betriebssystem unter Surface Hub 2", und weist darauf hinzu, dass je nach Systemstatus ein zweiter Neustart erforderlich sein kann.                                                          |
| V. 1.3  | 3. Dezember 2020 | Aktualisiert mit Anleitungen zum [Verwalten der SEMM-Registrierung.](#manage-semm-enrollment)                                                       |
| V. 1.2  | 29. September 2020 | Verschiedene Updates, die benutzerfreundlichkeitsfeedback behandeln.                                                        |
| V. 1.1  | 15. September 2020 | In der Einführung wurde ein zusätzlicher Hinweis eingefügt, in dem die Lizenzierungsanforderungen für die Installation eines neuen Betriebssystems erläutert werden. |
| V. 1.0  | 1. September 2020  | Neuer Artikel.                                                                                           |
