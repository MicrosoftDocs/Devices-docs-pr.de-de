---
title: Aufteilen der Registrierung von Surface Devices von Semm (Surface)
description: Erfahren Sie, wie Sie die Registrierung eines Geräts von Semm mithilfe eines UEFI-Reset-Pakets oder der Wiederherstellungs Anforderungs Option aufheben.
keywords: Surface Enterprise-Verwaltung
ms.prod: w10
ms.mktglfcycl: manage
ms.pagetype: surface, devices, security
ms.sitesec: library
author: coveminer
ms.author: greglin
ms.topic: article
ms.reviewer: ''
manager: laurawi
ms.localizationpriority: medium
ms.audience: itpro
ms.openlocfilehash: aa24ff1ac8a93ebc8078490c5e0c8fa34c940a25
ms.sourcegitcommit: 109d1d7608ac4667564fa5369e8722e569b8ea36
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/27/2020
ms.locfileid: "10832473"
---
# Aufheben der Registrierung von Surface-Geräten bei SEMM

Wenn ein Surface-Gerät im Surface Enterprise Management Mode (Semm) registriert ist, wird ein Zertifikat in der Firmware dieses Geräts gespeichert. Das vorhanden sein dieses Zertifikats und die Registrierung in Semm verhindern, dass unbefugte Änderungen an den Oberflächen UEFI-Einstellungen oder-Optionen durchgeführt werden, während das Gerät in Semm registriert ist. Wenn Sie die Steuerung der UEFI-Oberflächeneinstellungen für den Benutzer wiederherstellen möchten, muss das Surface-Gerät von Semm, einem Vorgang, der manchmal als zurücksetzen oder Wiederherstellen beschrieben wird, nicht registriert werden. Es gibt zwei Methoden, mit denen Sie die Registrierung eines Geräts von Semm aufheben können: ein Oberflächen-UEFI-Zurücksetzungs Paket und eine Wiederherstellungsanforderung.

>[!WARNING]
>Um die Registrierung eines Geräts von Semm zu entbinden und die Benutzersteuerung der Oberflächen UEFI-Einstellungen wiederherzustellen, müssen Sie über das Semm-Zertifikat verfügen, das zum Registrieren des Geräts in Semm verwendet wurde. Wenn dieses Zertifikat verloren geht oder beschädigt wird, können Sie die Registrierung von Semm nicht aufheben. Sichern und schützen Sie Ihr Semm-Zertifikat entsprechend.

Weitere Informationen zu Semm finden Sie unter [Microsoft Surface Enterprise-Verwaltungsmodus](https://technet.microsoft.com/itpro/surface/surface-enterprise-management-mode).

##  <a name="unenroll-a-surface-device-from-semm-with-a-surface-uefi-reset-package"></a>Aufheben der Registrierung eines Surface-Geräts aus Semm mit einem Surface UEFI-Reset-Paket

Das Oberflächen-UEFI-Zurücksetzungs Paket ist die primäre Methode, mit der Sie die Registrierung eines Surface-Geräts von Semm aufheben. Wie bei einem Oberflächen UEFI-Konfigurationspaket handelt es sich bei dem Zurücksetzungs Paket um eine Windows Installer-Datei (MSI), die Semm auf dem Gerät konfiguriert. Im Gegensatz zum Konfigurationspaket setzt das Reset-Paket die Oberflächen UEFI-Konfiguration auf einem Surface-Gerät auf die Standardeinstellungen zurück, entfernt das Semm-Zertifikat und die Registrierung des Geräts von Semm.

Reset-Pakete werden speziell für ein einzelnes Surface-Gerät erstellt. Um mit dem Erstellen eines Reset-Pakets zu beginnen, benötigen Sie die Seriennummer des Geräts, dessen Registrierung Sie aufheben möchten, sowie das Semm-Zertifikat, das zum Registrieren des Geräts verwendet wird. Die Seriennummer Ihres Surface-Geräts finden Sie auf der Seite **PC-Informationen** von Surface UEFI, wie in Abbildung 1 dargestellt. Diese Seite wird auch dann angezeigt, wenn das DGM-UEFI-Kennwort geschützt ist und das falsche Kennwort eingegeben wurde.

![Die Seriennummer des Surface-Geräts wird angezeigt.](images/surface-semm-unenroll-fig1.png "Serial number of Surface device is displayed")

*Abbildung1. Die Seriennummer des Surface-Geräts wird auf der Surface UEFI PC-Informationsseite angezeigt.*

>[!NOTE]
>Wenn Sie mit dem Surface UEFI booten möchten, drücken Sie gleichzeitig die **Lautstärke** und die **Stromversorgung** , während das Gerät ausgeschaltet ist. Halten **Sie die Lautstärke auf** , bis das Surface-Logo angezeigt wird und das Gerät gestartet wird.

Führen Sie die folgenden Schritte aus, um ein Oberflächen UEFI-Zurücksetzungs Paket zu erstellen:

1. Öffnen Sie den Microsoft Surface UEFI-Konfigurator über das Startmenü.
2. Klicken Sie auf **Start**.
3. Klicken Sie auf **Paket zurücksetzen**, wie in Abbildung 2 gezeigt.

   ![Wählen Sie Paket zurücksetzen aus, um ein Paket zum Aufheben der Registrierung des Surface-Geräts von Semm zu erstellen.](images/surface-semm-unenroll-fig2.png "Select Reset Package to create a package to unenroll Surface device from SEMM")

   *Abbildung2. Klicken Sie auf Paket zurücksetzen, um ein Paket zum Aufheben der Registrierung eines Surface-Geräts von Semm zu erstellen.*

4. Klicken Sie auf **Zertifikatschutz** , um Ihre Semm-Zertifikatdatei mit privatem Schlüssel (. pfx) hinzuzufügen, wie in Abbildung 3 dargestellt. Navigieren Sie zum Speicherort der Zertifikatsdatei, wählen Sie die Datei aus, und klicken Sie dann auf **OK**.

   ![Hinzufügen des Semm-Zertifikats zum UEFI-Reset-Paket für die Oberfläche](images/surface-semm-unenroll-fig3.png "Add the SEMM certificate to Surface UEFI reset package")

   *Abbildung3. Hinzufügen des Semm-Zertifikats zu einem Surface UEFI-Zurücksetzungs Paket*

5. Klicken Sie auf **Weiter**.
6. Geben Sie die Seriennummer des Geräts ein, für das Sie die Registrierung von Semm aufheben möchten (siehe Abbildung 4), und klicken Sie dann auf **Erstellen** , um das UEFI-Zurücksetzungs Paket für das DGM zu generieren.

   ![Erstellen eines Oberflächen-UEFI-Reset-Pakets mit der Seriennummer des Surface-Geräts](images/surface-semm-unenroll-fig4.png "Create a Surface UEFI reset package with serial number of Surface device")

   *Abbildung 4. Verwenden der Seriennummer Ihres Surface-Geräts zum Erstellen eines UEFI-Reset-Pakets für Flächen*

7. Geben Sie im Dialogfeld **Speichern** unter einen Namen für das Oberflächen UEFI-Zurücksetzungs Paket an, navigieren Sie zu dem Speicherort, an dem Sie die Datei speichern möchten, und klicken Sie dann auf **Speichern**.
8. Nach Abschluss der Paket Generierung wird die **erfolgreiche** Seite angezeigt. Klicken Sie auf **Beenden** , um die Paketerstellung abzuschließen, und schließen Sie den Microsoft Surface UEFI-Konfigurator.

Führen Sie die Windows Installer-Datei (MSI-Datei) des Surface UEFI-Pakets auf dem Surface-Gerät aus, um die Registrierung des Geräts von Semm aufzuheben. Für das Zurücksetzen-Paket ist ein Neustart erforderlich, um den Vorgang zum Aufheben der Registrierung durchzuführen. Nachdem die Registrierung des Geräts aufgehoben wurde, können Sie die erfolgreiche Entfernung überprüfen, indem Sie sicherstellen, dass das **Microsoft Surface-Konfigurationspaket** Element in " **Programme und Features** " (siehe Abbildung 5) nicht mehr vorhanden ist.

![Auf dem Bildschirm wird das Gerät in Semm registriert.](images/surface-semm-unenroll-fig5.png "Screen that shows device is enrolled in SEMM")

*Abbildung5. Das vorhanden sein des Microsoft Surface-Konfigurationspaket Elements in "Programme und Features" gibt an, dass das Gerät in Semm registriert ist.*

##  <a name="unenroll-a-surface-device-from-semm-with-a-recovery-request"></a>Aufhebung der Registrierung eines Surface-Geräts von Semm mit einer Wiederherstellungsanforderung

In einigen Szenarien ist ein Oberflächen UEFI-Zurücksetzungs Paket möglicherweise keine gangbare Option zum Aufheben der Registrierung eines Surface-Geräts von Semm (beispielsweise, wenn Windows nicht mehr verwendet werden kann). In diesen Szenarien können Sie die Registrierung des Geräts mithilfe einer Wiederherstellungsanforderung, die innerhalb von Surface UEFI generiert wurde, Aufhebung. Der Wiederherstellungs Anforderungsprozess kann auch auf Geräten initiiert werden, auf denen Sie nicht über das UEFI-Kennwort für die Oberfläche verfügen.

Der Wiederherstellungs Anforderungsprozess wird vom Surface UEFI auf dem Surface-Gerät initiiert, mit dem Microsoft Surface UEFI-Konfigurator auf einem anderen Computer genehmigt und dann im Surface UEFI abgeschlossen. Wie das Zurücksetzen-Paket erfordert das Genehmigen einer Wiederherstellungsanforderung mit dem Microsoft Surface UEFI-Konfigurator Zugriff auf das Semm-Zertifikat, das zum Registrieren des Surface-Geräts verwendet wurde.

Führen Sie die folgenden Schritte aus, um eine Wiederherstellungsanforderung zu initiieren:

1. Starten Sie das Surface-Gerät, für das die Registrierung von Semm nicht registriert werden soll, auf Surface UEFI.
2. Geben Sie das DGM-UEFI-Kennwort ein, wenn Sie dazu aufgefordert werden.
3. Klicken Sie auf die Seite **Unternehmensverwaltung** , wie in Abbildung 6 dargestellt.

   ![Seite "Unternehmensverwaltung"](images/surface-semm-unenroll-fig6.png "Enterprise Management page")

   *Abbildung6. Die Seite "Unternehmensverwaltung" wird in "Surface UEFI" auf Geräten angezeigt, die in Semm registriert sind.*

4. Klicken oder klicken Sie auf **Erste Schritte**.
5. Klicken oder klicken Sie auf **weiter** , um den Wiederherstellungs Anforderungsprozess zu starten.
   >[!NOTE]
   >Eine Wiederherstellungsanforderung verfällt zwei Stunden, nachdem Sie erstellt wurde. Wenn eine Wiederherstellungsanforderung in dieser Zeit nicht abgeschlossen ist, müssen Sie den Wiederherstellungs Anforderungsprozess erneut starten.
6. Wählen Sie **Semm-Zertifikat** aus der Liste der Zertifikate aus, die auf der Seite **Semm Zurücksetzen des Schlüssels auswählen** angezeigt wird (siehe Abbildung 7), und klicken oder drücken Sie dann auf **weiter**.

   ![Auswählen des Semm-Zertifikats für Ihre Wiederherstellungsanforderung](images/surface-semm-unenroll-fig7.png "Select SEMM certificate for your Recovery Request")

   *Abbildung7. Auswählen des Semm-Zertifikats für Ihre Wiederherstellungsanforderung (Anforderung zurücksetzen)*

7. Auf der Seite **Semm-Bestätigungscode eingeben** können Sie auf die **QR-Code** -oder **Text** Schaltflächen klicken, um Ihre Wiederherstellungsanforderung (Reset Request) wie in Abbildung 8 dargestellt anzuzeigen, oder auf die Schaltfläche **USB** , um Ihre Wiederherstellungsanforderung (Reset Request) als Datei auf einem USB-Laufwerk zu speichern, wie in Abbildung 9 dargestellt.

   ![Wiederherstellungsanforderung als QR-Code angezeigt](images/surface-semm-unenroll-fig8.png "Recovery Request displayed as a QR Code")

   *Abbildung8. Eine Wiederherstellungsanforderung (Reset Request) wird als QR-Code angezeigt*

   ![Speichern einer Wiederherstellungsanforderung auf einem USB-Laufwerk](images/surface-semm-unenroll-fig9.png "Save a recovery request to a USB drive")

   *Abbildung9. Speichern einer Wiederherstellungsanforderung (Anforderung zurücksetzen) auf ein USB-Laufwerk*

   * Wenn Sie eine QR-Code Wiederherstellungsanforderung (Reset Request) verwenden möchten, verwenden Sie eine QR Reader-App auf einem mobilen Gerät, um den Code zu lesen. Die QR-Reader-App übersetzt den QR-Code in eine alphanumerische Zeichenfolge. Sie können die Zeichenfolge dann per e-Mail oder Nachricht an den Administrator senden, der den Bestätigungscode Zurücksetzen mit dem Microsoft Surface UEFI Configurator erstellt.
   * Wenn Sie eine Wiederherstellungsanforderung (Reset Request) verwenden möchten, die auf einem USB-Laufwerk als Datei gespeichert wurde, verwenden Sie das USB-Laufwerk, um die Datei auf den Computer zu übertragen, auf dem Microsoft Surface UEFI Configurator verwendet wird, um den Code zum Zurücksetzen der Bestätigung zu erstellen. Die Datei kann auch vom USB-Laufwerk auf einem anderen Gerät kopiert werden, um Sie per e-Mail zu senden oder über das Netzwerk zu übertragen.
   * Wenn Sie die Wiederherstellungsanforderung (Anforderung zurücksetzen) als Text verwenden möchten, geben Sie den Text einfach direkt in den Microsoft Surface UEFI-Konfigurator ein.

8. Öffnen Sie den Microsoft Surface UEFI Configurator über das Menü "Start" auf einem anderen Computer.
    >[!NOTE]
    >Der Microsoft Surface UEFI-Konfigurator muss in einer Umgebung ausgeführt werden, die die Zertifikatkette für das Semm-Zertifikat authentifizieren kann.
9. Klicken Sie auf **Start**.
10. Klicken Sie auf **Wiederherstellungsanforderung**, wie in Abbildung 10 dargestellt.

    ![Starten des Prozesses zum Genehmigen einer Wiederherstellungsanforderung](images/surface-semm-unenroll-fig10.png "Start process to approve a Recovery Request")

    *Abbildung10. Klicken Sie auf Wiederherstellungsanforderung, um den Vorgang zum Genehmigen einer Wiederherstellungsanforderung zu starten*

11. Klicken Sie auf **Zertifikatschutz** , um die Wiederherstellungsanforderung mit dem Semm-Zertifikat zu authentifizieren.
12. Navigieren Sie zu ihrer Semm-Zertifikatdatei, wählen Sie Sie aus, und klicken Sie dann auf **OK**.
13. Wenn Sie aufgefordert werden, das Zertifikat Kennwort einzugeben, wie in Abbildung 11 dargestellt, geben Sie das Kennwort für die Zertifikatdatei ein, bestätigen Sie es, und klicken Sie dann auf **OK**.

    ![Kennwort für Semm-Zertifikat eingeben](images/surface-semm-unenroll-fig11.png "Type password for SEMM certificate")

    *Abbildung11. Geben Sie das Kennwort für das Semm-Zertifikat ein.*

14. Klicken Sie auf **Weiter**.
15. Geben Sie die Wiederherstellungsanforderung ein (Reset Request), und klicken Sie dann auf **generieren** , um einen Bestätigungscode für das Zurücksetzen zu erstellen (siehe Abbildung 12).

    ![Eingeben der Wiederherstellungsanforderung](images/surface-semm-unenroll-fig12.png "Enter the recovery request")

    *Abbildung 12 Eingeben der Wiederherstellungsanforderung (Anforderung zurücksetzen)*

    * Wenn Sie die Wiederherstellungsanforderung (Reset Request) als Text auf dem zurückgesetzten Surface-Gerät angezeigt haben, verwenden Sie die Tastatur, um die Wiederherstellungsanforderung (Reset Request) in das bereitgestellte Feld einzugeben.
    * Wenn Sie die Wiederherstellungsanforderung (Reset Request) als QR-Code angezeigt und dann eine Messaging-oder e-Mail-Anwendung verwendet haben, um den Code mit Microsoft Surface UEFI Configurator an den Computer zu senden, kopieren Sie den Code, und fügen Sie ihn in das bereitgestellte Feld ein.
    * Wenn Sie die Wiederherstellungsanforderung (Reset Request) als Datei auf einem USB-Laufwerk gespeichert haben, klicken Sie auf die Schaltfläche **importieren** , navigieren Sie zu der Wiederherstellungs Anforderungsdatei (Reset Request), wählen Sie Sie aus, und klicken Sie dann auf **OK**.

16. Der Code zum Zurücksetzen der Bestätigung wird im Microsoft Surface UEFI-Konfigurator angezeigt, wie in Abbildung 13 dargestellt.

    ![Anzeige des Reset-Bestätigungscodes](images/surface-semm-unenroll-fig13.png "Display of the reset verification code")

    *Abbildung 13 Der in Microsoft Surface UEFI Configurator angezeigte Bestätigungscode zurücksetzen*

    * Klicken Sie auf die Schaltfläche **Freigeben** , um den zurückgesetzten Bestätigungscode per e-Mail zu senden.

17. Geben Sie den Bestätigungscode für das Zurücksetzen in das bereitgestellte Feld auf dem Surface-Gerät ein (siehe Abbildung 8), und klicken oder drücken Sie dann auf **überprüfen** , um das Gerät zurückzusetzen und die Registrierung des Geräts von Semm aufzuheben.
18. Klicken oder drücken Sie jetzt auf der **Semm Seite erfolgreich zurücksetzen** auf **neu starten** , um die Registrierung von Semm abzuschließen, wie in Abbildung 14 dargestellt.

    ![Beispiel für die Anzeige einer erfolgreichen Registrierung von Semm](images/surface-semm-unenroll-fig14.png "Example display of successful unenrollment from SEMM")

    *Abbildung 14 Erfolgreiche Registrierung von Semm*

19. Klicken Sie im Microsoft Surface UEFI-Konfigurator auf **Beenden** , um den Prozess der Wiederherstellungsanforderung (Anforderung zurücksetzen) abzuschließen und den Microsoft Surface UEFI Configurator zu schließen.


