---
title: Problembehandlung in Microsoft Surface Hub
description: Behandeln Sie allgemeine Probleme, u.a. Probleme bei der Einrichtung und Exchange ActiveSync-Fehler.
ms.assetid: CF58F74D-8077-48C3-981E-FCFDCA34B34A
ms.reviewer: ''
manager: laurawi
keywords: Behandeln Sie allgemeine Probleme, Probleme bei der Einrichtung und Exchange ActiveSync-Fehler.
ms.prod: surface-hub
ms.sitesec: library
author: dansimp
ms.author: dansimp
ms.topic: article
ms.date: 03/16/2018
ms.localizationpriority: medium
ms.openlocfilehash: fe87c56474a05152f991a5b63f6abf0cf05e8b03
ms.sourcegitcommit: 109d1d7608ac4667564fa5369e8722e569b8ea36
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/27/2020
ms.locfileid: "10832686"
---
# Problembehandlung bei Microsoft Surface Hub


Behandeln Sie allgemeine Probleme, u.a. Probleme bei der Einrichtung und Exchange ActiveSync-Fehler.

Das [Diagnosetool für die Surface Hub-Hardware](https://www.microsoft.com/store/p/surface-hub-hardware-diagnostic/9nblggh51f2g?rtc=1&activetab=pivot%3aoverviewtab) enthält interaktive Tests, mit denen Sie prüfen können, ob wichtige Funktionen des Hub wie vorgesehen funktionieren. Zudem kann das Diagnosetool das Ressourcenkonto testen, um sicherzustellen, dass es ordnungsgemäß für Ihre Umgebung konfiguriert ist. Wenn Probleme auftreten, können Ergebnisse gespeichert und für das Surface Hub-Support-Team freigegeben werden. Weitere Informationen zur Verwendung finden Sie unter [Using the Surface Hub Hardware Diagnostic Tool to test a device account](https://support.microsoft.com/help/4077574/using-the-surface-hub-hardware-diagnostic-tool-to-test-a-device-accoun).

Allgemeine Probleme sowie Ursachen und mögliche Problembehebungen sind in der folgenden Tabelle aufgeführt. Im Abschnitt [Setup-Problembehandlung](#setup-troubleshooting) sind gerätebezogene Probleme sowie diverse andere Probleme aufgeführt, die während der ersten Ausführung auftreten können. Im Abschnitt [Exchange ActiveSync-Fehler](#exchange-activesync-errors) sind allgemeine Fehler aufgeführt, die bei der Synchronisierung mit Microsoft Exchange ActiveSync-Servern auftreten können.




## Setup-Problembehandlung


In diesem Abschnitt werden Ursachen und Behebungen für Probleme aufgeführt, die beim Einrichten von Microsoft Surface Hub auftreten können.

###  <a name="on-device"></a>Gerätebezogen

Mögliche Behebungen für Probleme mit Surface Hub, nachdem Sie das Programm für die Erstausführung abgeschlossen haben.

<table>
<tr>
<th>Problem</th>
<th>Ursachen</th>
<th>Mögliche Problembehebungen</th>
</tr>
<tr>
<td rowspan="2">
<p>Nachrichten werden nicht automatisch akzeptiert/abgelehnt.</p>
</td>
<td>
<p>Das Gerätekonto ist nicht konfiguriert, um Nachrichten automatisch zu akzeptieren/abzulehnen.</p>
</td>
<td>
<p>Verwenden Sie das PowerShell-Cmdlet <code>Set-CalendarProcessing $upn -AutomateProcessing AutoAccept</code>.</p>
</td>
</tr>
<tr>
<td>
<p>Das Gerätekonto ist nicht zum Verarbeiten externer Besprechungsanfragen konfiguriert.</p>
</td>
<td>
<p>Verwenden Sie das PowerShell-Cmdlet <code>Set-CalendarProcessing $upn -ProcessExternalMeetingMessages $true</code>.</p>
</td>
</tr>
<tr>
<td>
<p>Der Kalender wird nicht auf der Willkommensseite angezeigt, oder die Meldung „Termine sind möglicherweise nicht mehr aktuell (kein Konto bereitgestellt)“ wird angezeigt.</p>
</td>
<td>
<p>Auf Surface Hub ist kein Gerätekonto eingerichtet.</p>
</td>
<td>
<p>Geben Sie in den Einstellungen ein Gerätekonto an.</p>
</td>
</tr>
<tr>
<td>
<p>Der Kalender wird nicht auf der Willkommensseite angezeigt, oder die Meldung „Termine sind möglicherweise nicht mehr aktuell (zu häufig bereitgestellt)“ wird angezeigt.</p>
</td>
<td>
<p>Das Gerätekonto wird auf zu vielen Geräten bereitgestellt.</p>
</td>
<td>
<p>Entfernen Sie das Gerätekonto von anderen Geräten, auf denen es bereitgestellt wird. Dies kann im Exchange-Verwaltungsportal vorgenommen werden.</p>
</td>
</tr>
<tr>
<td>
<p>Der Kalender wird nicht auf der Willkommensseite angezeigt, oder die Meldung „Termine sind möglicherweise nicht mehr aktuell (ungültige Anmeldeinformationen)“ wird angezeigt.</p>
</td>
<td>
<p>Das Kennwort des Gerätekontos ist abgelaufen und nicht mehr gültig.</p>
</td>
<td>
<p>Aktualisieren Sie das Kennwort des Kontos in den Einstellungen. Weitere Informationen finden Sie unter <a href="password-management-for-surface-hub-device-accounts.md">Kennwortverwaltung</a>.</p>
</td>
</tr>
<tr>
<td>
<p>Der Kalender wird nicht auf der Willkommensseite angezeigt, oder die Meldung „Termine sind möglicherweise nicht mehr aktuell (Kontorichtlinie)“ wird angezeigt.</p>
</td>
<td>
<p>Für das Gerätekonto wird eine ungültige ActiveSync-Richtlinie verwendet.</p>
</td>
<td>
<p>Stellen Sie sicher, dass die ActiveSync-Richtlinie des Gerätekontos auf den Wert <code>PasswordEnabled == False</code> festgelegt ist.</p>
</td>
</tr>
<tr>
<td>
<p>Der Kalender wird nicht auf der Willkommensseite angezeigt, oder die Meldung „Termine sind möglicherweise nicht mehr aktuell“ wird angezeigt.</p>
</td>
<td>
<p>Exchange ist nicht aktiviert.</p>
</td>
<td>Aktivieren Sie das Gerätekonto für Exchange-Dienste in den Einstellungen. Sie müssen über die richtigen ActiveSync-Richtlinien verfügen, und alle erforderlichen Zertifikate für Exchange-Dienste müssen installiert sein.</td>
</tr>
<tr>
<td>
<p>Die Anmeldung bei Skype for Business ist nicht möglich.</p>
</td>
<td>
<p>Das Gerätekonto weist keine Session Initiation-Protokoll (SIP)-Adresseigenschaft auf.</p>
</td>
<td>
<p>Das Konto weist keine SIP-Adresseigenschaft auf, und der Benutzerprinzipalname (UPN) entspricht nicht der tatsächlichen SIP-Adresse. Im Konto muss eine SIP-Adresse festgelegt sein, oder die SIP-Adresse muss in der Einstellungs-App hinzugefügt werden.</p>
</td>
</tr>
<tr>
<td>
<p>Die Anmeldung bei Skype for Business ist nicht möglich.</p>
</td>
<td>
<p>Das Gerätekonto erfordert ein Zertifikat zur Authentifizierung in Skype for Business.</p>
</td>
<td>
<p>Installieren Sie das richtige Zertifikat mithilfe von Bereitstellungspaketen.</p>
</td>
</tr>
</table>
 

###  <a name="first-run"></a>Erstausführung

Mögliche Behebungen für Probleme mit dem Programm für die Erstausführung des Surface Hub.

<table>
<colgroup>
<col width="33%" />
<col width="33%" />
<col width="33%" />
</colgroup>
<thead>
<tr class="header">
<th align="left">Problem</th>
<th align="left">Ursachen</th>
<th align="left">Mögliche Problembehebungen</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left"><p>Bei Eingabe von Domäne und Benutzername wird das Konto nicht gefunden.</p></td>
<td align="left"><p>Für die Domäne muss der vollqualifizierte Domänenname (FQDN) angegeben werden.</p></td>
<td align="left"><p>Der vollqualifizierte Domänenname muss in das Feld für die Domäne eingegeben werden.</p></td>
</tr>
</tbody>
</table>

 

### <a href="" id="first-run-device-acct-page"></a>Seite „Gerätekonto“, Probleme bei neuen Kontoeinstellungen

<table>
<colgroup>
<col width="33%" />
<col width="33%" />
<col width="33%" />
</colgroup>
<thead>
<tr class="header">
<th align="left">Problem</th>
<th align="left">Ursachen</th>
<th align="left">Mögliche Problembehebungen</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left"><p>Das bereitgestellte Konto kann nicht in Azure AD gefunden werden.</p></td>
<td align="left"><p>Der angegebene Benutzerprinzipalname (UPN) des Kontos weist einen Mandanten auf, der in Azure AD nicht erreicht werden kann.</p></td>
<td align="left"><p>Stellen Sie sicher, dass eine funktionierende Internetverbindung besteht und das Gerät auf Microsoft Online Services zugreifen kann. Stellen Sie sicher, dass die Kontoanmeldeinformationen richtig eingegeben wurden.</p></td>
</tr>
<tr class="even">
<td align="left"><p>Das angegebene Verzeichnis kann nicht erreicht werden.</p></td>
<td align="left"><p>Die bereitgestellte Kontodomäne gibt eine Domäne an, die nicht erreicht werden kann.</p></td>
<td align="left"><p>Stellen Sie sicher, dass eine Netzwerkverbindung besteht und das Gerät auf den Domänencontroller zugreifen kann. Stellen Sie sicher, dass die Kontoanmeldeinformationen richtig eingegeben wurden. Sie können auch versuchen, stattdessen den FQDN zu verwenden.</p></td>
</tr>
<tr class="odd">
<td align="left"><p>Der Exchange-Server kann nicht automatisch erkannt werden.</p></td>
<td align="left"><p>Der Exchange-Server ist nicht für die automatische Erkennung konfiguriert.</p></td>
<td align="left"><p>Aktivieren Sie die automatische Erkennung des Exchange-Servers für das Gerätekonto, oder geben Sie die Adresse des Exchange-Servers manuell ein.</p></td>
</tr>
<tr class="even">
<td align="left"><p>Die SIP-Adresse konnte nach der Eingabe der Kontoanmeldeinformationen nicht gefunden werden.</p></td>
<td align="left"><p>In Active Directory oder Azure AD besteht kein SIP-Adresseintrag.</p></td>
<td align="left"><p>Stellen Sie sicher, dass Skype for Business für das Konto aktiviert ist und eine SIP-Adresse vorhanden ist. Wenn dies nicht der Fall ist, können Sie die SIP-Adresse manuell in das Textfeld eingeben.</p></td>
</tr>
</tbody>
</table>

 

###  <a name="device-account-page,-issues-for-existing-account-settings"></a>Seite „Gerätekonto“, Probleme bei bestehenden Kontoeinstellungen

<table>
<tr>
<th>Problem</th>
<th>Ursachen</th>
<th>Fehlercodes</th>
<th>Mögliche Problembehebungen</th>
</tr>
<tr>
<td>
<p>Das Konto konnte nicht mit den angegebenen Anmeldeinformationen authentifiziert werden.</p>
</td>
<td>
<p>Das Konto ist nicht als Benutzer in Active Directory (AD) aktiviert, es ist ein Kennwort zur Authentifizierung erforderlich, oder das Kennwort ist falsch.</p>
</td>
<td>
<p>Keine</p>
</td>
<td>
<p>Stellen Sie sicher, dass die Anmeldeinformationen richtig eingegeben wurden. Aktivieren Sie das Konto als Benutzer in Active Directory, und fügen Sie ein Kennwort hinzu, oder legen Sie das „RoomMailboxPassword“ fest</p>. </td>
</tr>
<tr>
<td>
<p>Bei Bereitstellung eines Exchange-Servers wird Fehler 0x800C0019 angezeigt.</p>
</td>
<td>
<p>Das Gerätekonto erfordert ein Zertifikat zur Authentifizierung.</p>
</td>
<td>
<p>0x800C0019</p>
</td>
<td>
<p>Installieren Sie das richtige Zertifikat mithilfe von Bereitstellungspaketen.</p>
</td>
</tr>
<tr>
<td>
<p>Die Gerätekonto-Anmeldeinformationen gelten nicht für den angegebenen Exchange-Server.</p>
</td>
<td>
<p>Das Postfach des Gerätekontos wird nicht auf dem angegebenen Exchange-Server gehostet.</p>
</td>
<td>
<p>Keine</p>
</td>
<td>
<p>Stellen Sie sicher, dass Sie den richtigen Exchange-Mail-Server für das Gerätekonto angeben.</p>
</td>
</tr>
<tr>
<td>
<p>HTTP-Zeitüberschreitung beim Versuch, den Exchange-Server zu erreichen.</p>
</td>
<td></td>
<td>
<p>0x80072EE2</p>
</td>
<td></td>
</tr>
<tr>
<td>
<p>Der angegebene Exchange-Server wurde nicht gefunden.</p>
</td>
<td>
<p>Der angegebene Exchange-Server konnte nicht gefunden werden.</p>
</td>
<td>
<p>Keiner</p>
</td>
<td>
<p>Stellen Sie sicher, dass eine Netzwerk- oder Internetverbindung besteht und der Exchange-Server richtig angegeben ist.</p>
</td>
</tr>
<tr>
<td>
<p>HTTP wird nicht unterstützt.</p>
</td>
<td>
<p>Ein Exchange-Server mit <i>http://</i> anstelle von <i>https://</i> wurde angegeben.</p>
</td>
<td>
<p>Keiner</p>
</td>
<td>
<p>Verwenden Sie einen Exchange-Server mit HTTPS.</p>
</td>
</tr>
<tr>
<td rowspan="3">
<div><p>Benutzer werden auf die Seite „Es ist ein Problem mit diesem Konto aufgetreten“ in Bezug auf ActiveSync weitergeleitet.</p>
</div>
<div> </div>
</td>
<td>
<p>Die ActiveSync-Richtlinie „PasswordEnabled“ ist auf „True“ (oder 1) festgelegt.</p>
</td>
<td>
<p>Keine</p>
</td>
<td>
<p>Erstellen Sie eine neue ActiveSync-Richtlinie, bei der PasswordEnabled auf „False“ (oder 0) festgelegt ist, und übernehmen Sie anschließend die Richtlinie für das Konto.</p>
</td>
</tr>
<tr>
<td>
<p>Zwischen Surface Hub und Exchange besteht keine Verbindung.</p>
</td>
<td>
<p>Keins</p>
</td>
<td>
<p>Stellen Sie sicher, dass eine Netzwerk- oder Internetverbindung besteht.</p>
</td>
</tr>
<tr>
<td>
<p>Exchange gibt einen Statuscode zurück, der auf einen Fehler hinweist.</p>
</td>
<td>
<p>Keins</p>
</td>
<td>
<p>Stellen Sie sicher, dass eine Netzwerk- oder Internetverbindung besteht.</p>
</td>
</tr>
</table>
 

### <a href="" id="first-run-domain-join-page"></a>Erstausführung, Probleme mit dem Domänenbeitritt

<table>
<colgroup>
<col width="33%" />
<col width="33%" />
<col width="33%" />
</colgroup>
<thead>
<tr class="header">
<th align="left">Problem</th>
<th align="left">Ursachen</th>
<th align="left">Mögliche Problembehebungen</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left"><p>Beim Versuch einer Domäne beizutreten, wird anhand einer Fehlermeldung angezeigt, dass das Konto nicht anhand der angegebenen Anmeldeinformationen authentifiziert werden konnte.</p></td>
<td align="left"><p>Mit den angegebenen Anmeldeinformationen kann der angegebenen Domäne nicht beigetreten werden.</p></td>
<td align="left"><p>Geben Sie die richtigen Anmeldeinformationen für ein Konto in der angegebenen Domäne an.</p></td>
</tr>
<tr class="even">
<td align="left"><p>Beim Angeben einer Gruppe einer Domäne wird anhand einer Fehlermeldung angezeigt, dass die Gruppe in der Domäne nicht gefunden werden konnte.</p></td>
<td align="left"><p>Die Gruppe wurde möglicherweise entfernt oder ist nicht mehr vorhanden.</p></td>
<td align="left"><p>Stellen Sie sicher, dass die Gruppe in der Domäne vorhanden ist.</p></td>
</tr>
</tbody>
</table>

 

###  <a name="first-run,-exchange-server-page"></a>Erstausführung, Exchange-Server-Seite

<table>
<colgroup>
<col width="33%" />
<col width="33%" />
<col width="33%" />
</colgroup>
<thead>
<tr class="header">
<th align="left">Problem</th>
<th align="left">Ursachen</th>
<th align="left">Mögliche Problembehebungen</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left"><p>Die Benutzer werden auf diese Seite geleitet und zur Eingabe der Exchange Server-Adresse aufgefordert.</p></td>
<td align="left"><p>Der Exchange-Server ist nicht für die automatische Erkennung konfiguriert.</p></td>
<td align="left"><p>Aktivieren Sie die automatische Erkennung des Exchange-Servers für das Gerätekonto, oder geben Sie die Adresse des Exchange-Servers manuell ein.</p></td>
</tr>
</tbody>
</table>

 

### <a href="" id="first-run-on-device"></a>Erstausführung, gerätebezogene Probleme

<table>
<colgroup>
<col width="25%" />
<col width="25%" />
<col width="25%" />
<col width="25%" />
</colgroup>
<thead>
<tr class="header">
<th align="left">Problem</th>
<th align="left">Ursachen</th>
<th align="left">Fehlercodes</th>
<th align="left">Mögliche Problembehebungen</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left"><p>E-Mail/Kalender können nicht synchronisiert werden.</p></td>
<td align="left"><p>Das Surface Hub ist nicht als zulässiges Gerät im Konto angegeben.</p></td>
<td align="left"><p>0x86000C1C</p></td>
<td align="left"><p>Fügen Sie die Surface Hub-Geräte-ID zur zulässigen Liste hinzu, indem Sie die <strong> ActiveSyncAllowedDeviceIds </strong> -Eigenschaft für das Postfach festlegen.</p></td>
</tr>
</tbody>
</table>

 



 

## Exchange ActiveSync-Fehler


In diesem Abschnitt werden Statuscodes, Zuordnung, Benutzermeldungen und Maßnahmen aufgeführt, die ein Administrator zur Behebung von Exchange ActiveSync-Fehlern ergreifen kann.

<table>
<colgroup>
<col width="20%" />
<col width="20%" />
<col width="20%" />
<col width="20%" />
</colgroup>
<thead>
<tr class="header">
<th align="left">Hexadezimalcode</th>
<th align="left">Zuordnung</th>
<th align="left">Benutzerfreundliche Meldung</th>
<th align="left">Vom Administrator zu ergreifende Maßnahme</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left"><p>0x85010002</p></td>
<td align="left"><p>E_HTTP_DENIED</p></td>
<td align="left"><p>Das Kennwort muss aktualisiert werden.</p></td>
<td align="left"><p>Aktualisieren Sie das Kennwort.</p></td>
</tr>
<tr class="even">
<td align="left"><p>0x80072EFD</p></td>
<td align="left"><p>WININET_E_CANNOT_CONNECT</p></td>
<td align="left"><p>Im Moment kann keine Verbindung mit dem Server hergestellt werden. Warten Sie etwas, und versuchen Sie es dann erneut, oder prüfen Sie die Kontoeinstellungen.</p></td>
<td align="left"><p>Stellen Sie sicher, dass der Servername korrekt ist und der Server erreichbar ist. Stellen Sie sicher, dass das Gerät mit dem Netzwerk verbunden ist.</p></td>
</tr>
<tr class="odd">
<td align="left"><p>0x86000C29</p></td>
<td align="left"><p>E_NEXUS_STATUS_DEVICE_NOTPROVISIONED (Richtlinien stimmen nicht überein)</p></td>
<td align="left"><p>Das Konto ist mit Richtlinien konfiguriert, die nicht mit Surface Hub kompatibel sind.</p></td>
<td align="left"><p>Deaktivieren Sie die <strong>PasswordEnabled</strong> -Richtlinie für dieses Konto.</p>
<p>Wir haben einen Fehler, bei dem die Richtlinien Fehler auftreten, wenn das Konto im Richtlinien Aktualisierungsintervall keine Server Benachrichtigungen erhält.</p></td>
</tr>
<tr class="even">
<td align="left"><p>0x86000C4C</p></td>
<td align="left"><p>E_NEXUS_STATUS_MAXIMUMDEVICESREACHED</p></td>
<td align="left"><p>Das Konto weist zu viele Gerätepartnerschaften auf.</p></td>
<td align="left"><p>Löschen Sie eine oder mehrere Partnerschaften auf dem Server.</p></td>
</tr>
<tr class="odd">
<td align="left"><p>0x86000C0A</p></td>
<td align="left"><p>E_NEXUS_STATUS_SERVERERROR_RETRYLATER</p></td>
<td align="left"><p>Im Moment kann keine Verbindung mit dem Server hergestellt werden.</p></td>
<td align="left"><p>Warten Sie, bis der Server wieder online ist. Wenn das Problem weiterhin besteht, stellen Sie das Konto erneut bereit.</p></td>
</tr>
<tr class="even">
<td align="left"><p>0x85050003</p></td>
<td align="left"><p>E_CREDENTIALS_EXPIRED (Anmeldeinformationen sind abgelaufen und müssen aktualisiert werden.)</p></td>
<td align="left"><p>Das Kennwort muss aktualisiert werden.</p></td>
<td align="left"><p>Aktualisieren Sie das Kennwort.</p></td>
</tr>
<tr class="odd">
<td align="left"><p>0x8505000D</p></td>
<td align="left"><p>E_AIRSYNC_RESET_RETRY</p></td>
<td align="left"><p>Im Moment kann keine Verbindung mit dem Server hergestellt werden. Warten Sie eine Weile, oder überprüfen Sie die Kontoeinstellungen.</p></td>
<td align="left"><p>Dies ist normalerweise ein vorübergehender Fehler. Wenn das Problem jedoch weiterhin besteht, prüfen Sie die Anzahl der mit dem Konto verknüpften Geräte, und löschen Sie ggf. einige, wenn die Anzahl zu groß ist.</p></td>
</tr>
<tr class="even">
<td align="left"><p>0x86000C16</p></td>
<td align="left"><p>E_NEXUS_STATUS_USER_HASNOMAILBOX</p></td>
<td align="left"><p>Das Postfach wurde zu einem anderen Server migriert.</p></td>
<td align="left"><p>Dieser Fehler sollte nie angezeigt werden. Wenn das Problem weiterhin besteht, stellen Sie das Konto erneut bereit.</p></td>
</tr>
<tr class="odd">
<td align="left"><p>0x85010004</p></td>
<td align="left"><p>E_HTTP_FORBIDDEN</p></td>
<td align="left"><p>Im Moment kann keine Verbindung mit dem Server hergestellt werden. Warten Sie eine Weile, und versuchen Sie es erneut, oder überprüfen Sie die Einstellungen des Kontos.</p></td>
<td align="left"><p>Überprüfen Sie den Servernamen, um sicherzustellen, dass er richtig ist. Wenn das Konto zertifikatbasierte Authentifizierung verwendet, stellen Sie sicher, dass das Zertifikat noch gültig ist, und aktualisieren Sie es ggf.</p></td>
</tr>
<tr class="even">
<td align="left"><p>0x85030028</p></td>
<td align="left"><p>E_ACTIVESYNC_PASSWORD_OR_GETCERT</p></td>
<td align="left"><p>Das Kennwort oder das Clientzertifikat des Kontos fehlt oder ist ungültig.</p></td>
<td align="left"><p>Aktualisieren Sie das Kennwort, und/oder stellen Sie das Clientzertifikat bereit.</p></td>
</tr>
<tr class="odd">
<td align="left"><p>0x86000C2A</p></td>
<td align="left"><p>E_NEXUS_STATUS_DEVICE_POLICYREFRESH</p></td>
<td align="left"><p>Das Konto ist mit Richtlinien konfiguriert, die nicht mit Surface Hub kompatibel sind.</p></td>
<td align="left"><p>Deaktivieren Sie die PasswordEnabled-Richtlinie für dieses Konto.</p></td>
</tr>
<tr class="even">
<td align="left"><p>0x85050002</p></td>
<td align="left"><p>E_CREDENTIALS_UNAVAILABLE</p></td>
<td align="left"><p>Das Kennwort muss aktualisiert werden.</p></td>
<td align="left"><p>Aktualisieren Sie das Kennwort.</p></td>
</tr>
<tr class="odd">
<td align="left"><p>0x80072EE2</p></td>
<td align="left"><p>WININET_E_TIMEOUT</p></td>
<td align="left"><p>Das Netzwerk unterstützt nicht das minimale Leerlauftimeout, das für den Empfang der Serverbenachrichtigung erforderlich ist, oder der Server ist offline.</p></td>
<td align="left"><p>Stellen Sie sicher, dass der Server online ist. Überprüfen Sie die NAT-Einstellungen.</p></td>
</tr>
<tr class="even">
<td align="left"><p>0x85002004</p></td>
<td align="left"><p>E_FAIL_ABORT</p></td>
<td align="left"><p>Dieser Fehler unterbricht die ausstehende Synchronisierung und wird den Benutzern nicht angezeigt. Er wird in den Diagnosedaten angezeigt, wenn Sie eine interaktive Synchronisierung erzwingen, das Konto löschen oder die Einstellungen aktualisieren.</p></td>
<td align="left"><p>Nichts.</p></td>
</tr>
<tr class="odd">
<td align="left"><p>0x85010017</p></td>
<td align="left"><p>E_HTTP_SERVICE_UNAVAIL</p></td>
<td align="left"><p>Im Moment kann keine Verbindung mit dem Server hergestellt werden. Warten Sie eine Weile, oder überprüfen Sie die Kontoeinstellungen.</p></td>
<td align="left"><p>Überprüfen Sie den Servernamen, um sicherzustellen, dass er richtig ist. Warten Sie, bis der Server wieder online ist. Wenn das Problem weiterhin besteht, stellen Sie das Konto erneut bereit.</p></td>
</tr>
<tr class="even">
<td align="left"><p>0x86000C0D</p></td>
<td align="left"><p>E_NEXUS_STATUS_MAILBOX_SERVEROFFLINE</p></td>
<td align="left"><p>Im Moment kann keine Verbindung mit dem Server hergestellt werden. Warten Sie eine Weile, oder überprüfen Sie die Kontoeinstellungen.</p></td>
<td align="left"><p>Überprüfen Sie den Servernamen, um sicherzustellen, dass er richtig ist. Warten Sie, bis der Server wieder online ist. Wenn das Problem weiterhin besteht, stellen Sie das Konto erneut bereit.</p></td>
</tr>
<tr class="odd">
<td align="left"><p>0x85030027</p></td>
<td align="left"><p>E_ACTIVESYNC_GETCERT</p></td>
<td align="left"><p>Der Exchange-Server erfordert ein Zertifikat.</p></td>
<td align="left"><p>Importieren Sie das entsprechende EAS-Zertifikat in Surface Hub.</p></td>
</tr>
<tr class="even">
<td align="left"><p>0x86000C2B</p></td>
<td align="left"><p>E_NEXUS_STATUS_INVALID_POLICYKEY</p></td>
<td align="left"><p>Das Konto ist mit Richtlinien konfiguriert, die nicht mit Surface Hub kompatibel sind.</p></td>
<td align="left"><p>Deaktivieren Sie die PasswordEnabled-Richtlinie für dieses Konto.</p>
<p>Wir haben einen Fehler, bei dem die Richtlinien Fehler auftreten, wenn das Konto im Richtlinien Aktualisierungsintervall keine Server Benachrichtigungen erhält.</p></td>
</tr>
<tr class="odd">
<td align="left"><p>0x85010005</p></td>
<td align="left"><p>E_HTTP_NOT_FOUND</p></td>
<td align="left"><p>Der Servername ist ungültig.</p></td>
<td align="left"><p>Überprüfen Sie den Servernamen, um sicherzustellen, dass er richtig ist. Wenn das Problem weiterhin besteht, stellen Sie das Konto erneut bereit.</p></td>
</tr>
<tr class="even">
<td align="left"><p>0x85010014</p></td>
<td align="left"><p>E_HTTP_SERVER_ERROR</p></td>
<td align="left"><p>Es kann keine Verbindung zum Server hergestellt werden.</p></td>
<td align="left"><p>Überprüfen Sie den Servernamen, um sicherzustellen, dass er richtig ist. Lösen Sie eine Synchronisierung aus. Wenn das Problem weiterhin besteht, stellen Sie das Konto erneut bereit.</p></td>
</tr>
<tr class="odd">
<td align="left"><p>0x80072EE7</p></td>
<td align="left"><p>WININET_E_NAME_NOT_RESOLVED</p></td>
<td align="left"><p>Der Servername oder die Serveradresse konnte nicht verarbeitet werden.</p></td>
<td align="left"><p>Stellen Sie sicher, dass der Servername korrekt eingegeben wurde.</p></td>
</tr>
<tr class="even">
<td align="left"><p>0x8007052F</p></td>
<td align="left"><p>ERROR_ACCOUNT_RESTRICTION</p></td>
<td align="left"><p>Beim automatischen Erkennen des Exchange-Servers wird eine Richtlinie angewendet, die verhindert, dass sich der angemeldete Benutzer beim Server anmelden kann.</p></td>
<td align="left"><p>Dies ist ein Zeitsteuerungsproblem. Überprüfen Sie die Anmeldeinformationen des Kontos. Versuchen Sie die erneute Bereitstellung, wenn sie richtig sind.</p></td>
</tr>
<tr class="odd">
<td align="left"><p>0x800C0019</p></td>
<td align="left"><p>INET_E_INVALID_CERTIFICATE</p></td>
<td align="left"><p>Das für den Zugriff auf diese Ressource erforderliche Sicherheitszertifikat ist ungültig.</p></td>
<td align="left"><p>Installieren Sie das richtige ActiveSync-Zertifikat für das angegebene Gerätekonto.</p></td>
</tr>
<tr class="even">
<td align="left"><p>0x80072F0D</p></td>
<td align="left"><p>WININET_E_INVALID_CA</p></td>
<td align="left"><p>Die Zertifizierungsstelle ist ungültig oder falsch. Der Exchange-Server konnte nicht automatisch erkannt werden, da ein Zertifikat fehlt.</p></td>
<td align="left"><p>Installieren Sie das richtige ActiveSync-Zertifikat für das angegebene Gerätekonto.</p></td>
</tr>
<tr class="odd">
<td align="left"><p>0x80004005</p></td>
<td align="left"><p>E_FAIL</p></td>
<td align="left"><p>Die angegebene Domäne konnte nicht gefunden werden. Der Exchange-Server konnte nicht automatisch erkannt werden und wurde nicht in den Einstellungen angegeben.</p></td>
<td align="left"><p>Stellen Sie sicher, dass die angegebene Domäne der vollqualifizierte Domänenname ist und ein Exchange-Server in das Exchange Server-Textfeld eingegeben wurde.</p></td>
</tr>
</tbody>
</table>

##  <a name="contact-support"></a>Support kontaktieren

Wenn Sie Fragen haben oder Hilfe benötigen, können Sie [eine Supportanfrage erstellen](https://support.microsoft.com/supportforbusiness/productselection).


 
##  <a name="related-content"></a>Verwandte Themen

- [Problembehandlung bei Miracast-Verbindung mit dem Surface Hub](https://docs.microsoft.com/surface-hub/miracast-troubleshooting)
 





