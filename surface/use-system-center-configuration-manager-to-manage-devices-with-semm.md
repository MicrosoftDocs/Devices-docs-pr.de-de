---
title: Verwenden von Microsoft Endpoint Configuration Manager zum Verwalten von Geräten mit Semm (Surface)
description: Erfahren Sie, wie Sie den Microsoft Surface Enterprise Management Mode (Semm) mit Endpoint Configuration Manager verwalten.
keywords: registrieren, aktualisieren, Skripts, Einstellungen
ms.prod: w10
ms.mktglfcycl: manage
ms.pagetype: surface, devices
ms.sitesec: library
author: coveminer
ms.author: greglin
ms.topic: article
ms.reviewer: hachidan
manager: laurawi
ms.localizationpriority: medium
ms.audience: itpro
ms.date: 10/28/2020
ms.openlocfilehash: 2d31f520d8c4da54f47b2b89b58b43e2cb983f1a
ms.sourcegitcommit: 7f5b97275fe301ef700f9c77954a1054e2e8d046
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/30/2020
ms.locfileid: "11145616"
---
# Verwenden von Microsoft-Endpunkt-Konfigurations-Manager zum Verwalten von Geräten mit SEMM

Mit dem Microsoft Surface Enterprise Management Mode (Semm)-Feature von Surface UEFI-Geräten können Administratoren die Konfiguration von Surface UEFI-Einstellungen verwalten und schützen. Für die meisten Organisationen wird dieser Vorgang durch Erstellen von Windows Installer-Paketen (MSI) mit dem Microsoft Surface UEFI Configurator-Tool ausgeführt. Diese Pakete werden dann auf den Client Oberflächen Geräten ausgeführt oder bereitgestellt, um die Geräte in Semm zu registrieren und die Konfiguration der Oberflächen UEFI-Einstellungen zu aktualisieren.

Für Organisationen mit Microsoft Endpoint Configuration Manager gibt es eine Alternative zur Verwendung des Microsoft Surface UEFI Configurator. msi-Prozesses zum Bereitstellen und Verwalten von Semm. Microsoft Surface UEFI Manager ist ein einfaches Installationsprogramm, mit dem erforderliche Assemblys für die Semm-Verwaltung auf einem Gerät verfügbar sind. Durch Installieren dieser Assemblys mit Microsoft Surface UEFI Manager auf einem verwalteten Client kann Semm vom Configuration Manager mit PowerShell-Skripts verwaltet werden, die als Anwendungen bereitgestellt werden. Bei diesem Verfahren wird die Semm-Verwaltung innerhalb von Configuration Manager durchgeführt, wodurch die Notwendigkeit des externen Microsoft Surface UEFI Configurator-Tools beseitigt wird.

> [!Note]
> Obwohl der in diesem Artikel beschriebene Prozess möglicherweise mit früheren Versionen von Endpoint Configuration Manager oder mit anderen Verwaltungslösungen von Drittanbietern funktioniert, wird die Verwaltung von Semm mit Microsoft Surface UEFI Manager und PowerShell nur mit der aktuellen Verzweigung des Endpunkt Konfigurations-Managers unterstützt.

####  <a name="prerequisites"></a>Voraussetzungen

Bevor Sie mit dem in diesem Artikel beschriebenen Verfahren beginnen, sollten Sie sich mit den folgenden Technologien und Tools vertraut machen:

* [DGM-UEFI](https://technet.microsoft.com/itpro/surface/manage-surface-uefi-settings)
* [Surface Enterprise Management Mode (SEMM)](https://technet.microsoft.com/itpro/surface/surface-enterprise-management-mode)
* [PowerShell-Skripting](https://technet.microsoft.com/scriptcenter/dd742419)
* [System Center Configuration Manager-Anwendungsbereitstellung](https://docs.microsoft.com/sccm/apps/deploy-use/deploy-applications)
* Zertifikatverwaltung

> [!Note]
> Außerdem benötigen Sie Zugriff auf das Zertifikat, das Sie zum Sichern von Semm verwenden möchten. Details zu den Anforderungen für dieses Zertifikat finden Sie unter [Anforderungen für das Surface Enterprise Management Mode-Zertifikat](https://technet.microsoft.com/itpro/surface/surface-enterprise-management-mode#surface-enterprise-management-mode-certificate-requirements).
> 
> Es ist sehr wichtig, dass dieses Zertifikat an einem sicheren Ort aufbewahrt und ordnungsgemäß gesichert wird. Wenn dieses Zertifikat verloren geht oder nicht verwendet werden kann, ist es nicht möglich, die UEFI-Oberfläche zurückzusetzen, die UEFI-Einstellungen für verwaltete Oberflächen zu ändern oder Semm aus einem eingeschriebenen Surface-Gerät zu entfernen.

#### <a name="deploy-microsoft-surface-uefi-manager"></a>Herunterladen des Microsoft Surface UEFI-Managers

Die Verwaltung von Semm mit Configuration Manager setzt die Installation von Microsoft Surface UEFI Manager auf jedem Client Oberflächengerät voraus. Sie können den Microsoft Surface UEFI-Manager (SurfaceUEFIManager.msi) über die Seite [Surface Tools für IT](https://www.microsoft.com/download/details.aspx?id=46703) im Microsoft Download Center herunterladen.

#### Herunterladen von Semm-Skripts für Configuration Manager

Nachdem Microsoft Surface UEFI Manager auf dem Client Oberflächengerät installiert wurde, wird Semm mit PowerShell-Skripts bereitgestellt und verwaltet. Sie können Beispiele der Semm- [Verwaltungsskripts](https://www.microsoft.com/download/details.aspx?id=46703) aus dem Download Center herunterladen.

## Bereitstellen des Microsoft Surface UEFI-Managers

Die Bereitstellung des Microsoft Surface UEFI-Managers ist eine typische Anwendungsbereitstellung. Die Microsoft Surface UEFI Manager-Installationsdatei ist eine standardmäßige Windows Installer-Datei, die Sie mit der [standardmäßigen Option quiet](https://msdn.microsoft.com/library/windows/desktop/aa367988)installieren können.

Der Befehl zum Installieren des Microsoft Surface UEFI-Managers lautet wie folgt:

`msiexec /i "SurfaceUEFIManagerSetup.msi" /q`

Der Befehl zum Deinstallieren des Microsoft Surface UEFI-Managers lautet wie folgt:

`msiexec /x {541DA890-1AEB-446D-B3FD-D5B3BB18F9AF} /q`

Führen Sie die folgenden Schritte aus, um eine neue Anwendung zu erstellen und diese in einer Sammlung bereitzustellen, die ihre Surface-Geräte enthält:

1. Öffnen Sie die Configuration Manager-Konsole auf dem **Start** Bildschirm oder im **Startmenü** .
2. Wählen Sie in der unteren linken Ecke des Fensters **Software Bibliothek** aus.
3. Erweitern Sie den Knoten **Anwendungsverwaltung** der Software Bibliothek, und wählen Sie dann **Anwendungen**aus.
4. Wählen Sie die Schaltfläche " **Anwendung erstellen** " unter der Registerkarte " **Start** " oben im Fenster aus. Damit wird der Assistent zum Erstellen von Anwendungen gestartet.
5. Der Assistent zum Erstellen von Anwendungen enthält eine Reihe von Schritten:

   * **Allgemein** – standardmäßig ist die Option **Informationen über diese Anwendung aus Installationsdateien automatisch erkennen** aktiviert. Im Feld **Typ** ist **Windows Installer (MSI-Datei)** ebenfalls standardmäßig aktiviert. Wählen Sie **Durchsuchen** aus, um zu navigieren, und wählen Sie **SurfaceUEFIManagerSetup.msi**aus, und wählen Sie dann **weiter**aus.
   
      > [!Note]
      > Der Speicherort von SurfaceUEFIManagerSetup.msi muss sich auf einer Netzwerkfreigabe befinden und sich in einem Ordner befinden, der keine anderen Dateien enthält. Ein lokaler Dateispeicherort kann nicht verwendet werden.

   * **Importieren von Informationen** – der Assistent zum Erstellen von Anwendungen analysiert die MSI-Datei und liest den **Anwendungsnamen** und den **Produkt Code**. SurfaceUEFIManagerSetup.msi sollten als einzige Datei unter den Linien **Inhaltsdateien**aufgeführt werden, wie in Abbildung 1 zu sehen ist. Wählen Sie **weiter** aus, um fortzufahren.

      ![Informationen aus dem Surface UEFI Manager-Setup werden automatisch analysiert](images/config-mgr-semm-fig1.png "Information from Surface UEFI Manager setup is automatically parsed")

      *Abbildung1. Informationen aus dem Microsoft Surface UEFI Manager-Setup werden automatisch analysiert*

   * **Allgemeine Informationen** : Sie können den Namen der Anwendung sowie Informationen zu Publisher und Version ändern oder Kommentare auf dieser Seite hinzufügen. Der Installationsbefehl für Microsoft Surface UEFI Manager wird im Feld Installationsprogramm angezeigt. Das Standard Installationsverhalten von installieren für System ermöglicht es dem Microsoft Surface UEFI-Manager, die erforderlichen Assemblys für Semm zu installieren, auch wenn ein Benutzer nicht am Surface-Gerät angemeldet ist. Wählen Sie **weiter** aus, um fortzufahren.
   * **Zusammenfassung** – die Informationen, die im Schritt " **Import Informationen** " analysiert wurden, und Ihre Auswahl aus dem Schritt " **Allgemeine Informationen** " werden auf dieser Seite angezeigt. Wählen Sie **weiter** aus, um Ihre Auswahl zu bestätigen und die Anwendung zu erstellen.
   * **Status – zeigt** eine Statusleiste und den Status an, während die Anwendung importiert und der Software Bibliothek hinzugefügt wird.
   * **Fertigstellung** – die Bestätigung der erfolgreichen Anwendungserstellung wird angezeigt, wenn der Anwendungs Erstellungsprozess abgeschlossen ist. Wählen Sie **Schließen** aus, um den Assistenten zum Erstellen von Anwendungen abzuschließen.

Nachdem die Anwendung in Configuration Manager erstellt wurde, können Sie Sie an Ihre Verteilungspunkte verteilen und Sie auf die Sammlungen einschließlich ihrer Surface-Geräte bereitstellen. Diese Anwendung kann Semm auf dem Surface-Gerät nicht installieren oder aktivieren. Es werden nur die Assemblys bereitgestellt, die für die Aktivierung von Semm mit dem PowerShell-Skript erforderlich sind.

Wenn Sie die Microsoft Surface UEFI Manager-Assemblys nicht auf Geräten installieren möchten, die nicht mit Semm verwaltet werden, können Sie den Microsoft Surface UEFI Manager als eine Abhängigkeit der Semm-Konfigurations-Manager-Skripts konfigurieren. Dieses Szenario wird im Abschnitt [Deploy Semm Configuration Manager-Skripts](#deploy-semm-configuration-manager-scripts) weiter unten in diesem Artikel behandelt.

## <a name="create-or-modify-the-semm-configuration-manager-scripts"></a>Erstellen oder Ändern der Semm-Konfigurations-Manager-Skripts

Nachdem die erforderlichen Assemblys auf den Geräten installiert wurden, erfolgt der Registriervorgang für die Geräte in Semm und das Konfigurieren des Oberflächen UEFI mit PowerShell-Skripts, die als Skriptanwendung mit Configuration Manager bereitgestellt werden. Diese Skripts können an die Anforderungen Ihrer Organisation und Umgebung angepasst werden. So können Sie beispielsweise mehrere Konfigurationen für verwaltete Surface-Geräte in verschiedenen Abteilungen oder Rollen erstellen. Sie können Beispiele der Skripts für Semm und Configuration Manager über den Link im Abschnitt [Voraussetzungen](#prerequisites) am Anfang dieses Artikels herunterladen.

Es gibt zwei primäre Skripts, die Sie benötigen, um eine Semm-Bereitstellung mit Configuration Manager durchzuführen:

* **ConfigureSEMM.ps1** – mit diesem Skript können Sie Konfigurationspakete für Ihre Surface-Geräte mit den gewünschten Oberflächen UEFI-Einstellungen erstellen, um die angegebenen Einstellungen auf ein Surface-Gerät anzuwenden, um das Gerät in Semm zu registrieren und einen Registrierungsschlüssel festzulegen, der zur Identifizierung der Registrierung des Geräts in Semm verwendet wird.
* **ResetSEMM.ps1** – verwenden Sie dieses Skript zum Zurücksetzen von Semm auf einem Surface-Gerät, das die Registrierung von Semm aufhebt und das Steuerelement über die UEFI-Oberflächeneinstellungen entfernt.

Die Beispielskripts umfassen Beispiele für das Festlegen von UEFI-Einstellungen für die Oberfläche und das Steuern von Berechtigungen für diese Einstellungen. Diese Einstellungen können geändert werden, um die UEFI-Oberfläche zu sichern und die UEFI-Einstellungen entsprechend den Anforderungen Ihrer Umgebung festzulegen. In den folgenden Abschnitten dieses Artikels wird das ConfigureSEMM.ps1-Skript erläutert, und es werden die Änderungen erläutert, die Sie an dem Skript vornehmen müssen, damit Sie Ihren Anforderungen entsprechen.

> [!NOTE]
> Die Semm-Konfigurations-Manager-Skripts und die exportierte Semm-Zertifikatsdatei (. pfx) sollten sich im gleichen Ordner wie keine anderen Dateien befinden, bevor Sie dem Configuration Manager hinzugefügt werden.

###  <a name="specify-certificate-and-package-names"></a>Angeben von Zertifikats-und Paketnamen

Der erste Bereich des Skripts, den Sie ändern müssen, ist der Teil, der das Semm-Zertifikat angibt und lädt, und auch die SurfaceUEFIManager-Version sowie die Namen für das Semm-Konfigurationspaket und das Semm-Zurücksetzungs Paket. Der Zertifikatname und die SurfaceUEFIManager-Version werden in Zeilen 56 bis 73 im ConfigureSEMM.ps1-Skript angegeben.

  ```powershell
  56    $WorkingDirPath = split-path -parent $MyInvocation.MyCommand.Definition
  57    $packageRoot = "$WorkingDirPath\Config"
  58    $certName = "FabrikamSEMMSample.pfx"
  59  $DllVersion = "2.26.136.0"
  60
  61  $certNameOnly = [System.IO.Path]::GetFileNameWithoutExtension($certName)
  62  $ProvisioningPackage = $certNameOnly + "ProvisioningPackage.pkg"
  63  $ResetPackage = $certNameOnly + "ResetPackage.pkg"
  64
  65    if (-not (Test-Path $packageRoot))  { New-Item -ItemType Directory -Force -Path $packageRoot }
  66    Copy-Item "$WorkingDirPath\$certName" $packageRoot
  67    
  68    $privateOwnerKey = Join-Path -Path $packageRoot -ChildPath $certName
  69    $ownerPackageName = Join-Path -Path $packageRoot -ChildPath $ProvisioningPackage
  70    $resetPackageName = Join-Path -Path $packageRoot -ChildPath $ResetPackage
  71    
  72    # If your PFX file requires a password then it can be set here, otherwise use a blank string.
  73    $password = "1234" 
  ```

Ersetzen Sie den Wert **FabrikamSEMMSample. pfx** für die **$certName** -Variable durch den Namen Ihrer Semm-Zertifikatsdatei in Zeile 58. Das Skript erstellt ein Arbeitsverzeichnis (mit dem Namen config) in dem Ordner, in dem sich Ihre Skripts befinden, und kopiert dann die Zertifikatdatei in dieses Arbeitsverzeichnis.

Das Paket "Besitzer Paket und-Zurücksetzen" wird auch im Verzeichnis "config" erstellt und die Konfiguration für Oberflächen UEFI-Einstellungen und-Berechtigungen enthalten, die vom Skript generiert wurden.

Ersetzen Sie in Zeile 73 den Wert der **$Password** -Variablen von **1234** in das Kennwort für Ihre Zertifikatsdatei. Wenn kein Kennwort erforderlich ist, löschen Sie den **1234** -Text.

> [!Note]
> Die letzten beiden Zeichen des Zertifikat Fingerabdrucks sind zum Registrieren eines Geräts in Semm erforderlich. Dieses Skript zeigt diese Ziffern dem Benutzer an, sodass der Benutzer oder Techniker diese Ziffern aufzeichnen kann, bevor das System neu gestartet wird, um das Gerät in Semm zu registrieren. Das Skript verwendet den folgenden Code, der in Zeilen 150-155 zu finden ist, um dies zu erreichen.

```powershell
150 # Device owners will need the last two characters of the thumbprint to accept SEMM ownership.
151 # For convenience we get the thumbprint here and present to the user.
152 $pw = ConvertTo-SecureString $password -AsPlainText -Force
153 $certPrint = New-Object System.Security.Cryptography.X509Certificates.X509Certificate2
154 $certPrint.Import($privateOwnerKey, $pw, [System.Security.Cryptography.X509Certificates.X509KeyStorageFlags]::DefaultKeySet)
155 Write-Host "Thumbprint =" $certPrint.Thumbprint
```

Administratoren mit Zugriff auf die Zertifikatsdatei (. pfx) können den Fingerabdruck jederzeit lesen, indem Sie die PFX-Datei in certmgr öffnen. Gehen Sie folgendermaßen vor, um den Fingerabdruck mit certmgr anzuzeigen:

1. Klicken Sie mit der rechten Maustaste auf die PFX-Datei, und wählen Sie dann **Öffnen**aus.
2. Erweitern Sie den Ordner im Navigationsbereich.
3. Wählen Sie **Zertifikate**aus.
4. Klicken Sie im Hauptfenster mit der rechten Maustaste auf das Zertifikat, und wählen Sie dann **Öffnen**aus.
5. Wählen Sie die Registerkarte **Details** aus.
6. Im Dropdownmenü **anzeigen** muss nur **alle** oder **nur Eigenschaften** ausgewählt sein.
7. Wählen Sie das Feld **Daumenabdruck**aus.

> [!NOTE]
> Der Semm-Zertifikatname und das Kennwort müssen ebenfalls in diesem Abschnitt des ResetSEMM.ps1 Skripts eingegeben werden, damit Configuration Manager Semm vom Gerät mit der Deinstallations Aktion Entfernen kann.

###  <a name="configure-permissions"></a>Konfigurieren von Berechtigungen

Der erste Bereich des Skripts, in dem Sie die Konfiguration für Surface UEFI angeben, ist der Bereich " **Berechtigungen konfigurieren** ". Dieser Bereich beginnt bei Zeile 210 im Beispielskript mit dem Kommentar **# configure-Berechtigungen** und fährt mit Zeile 247 fort. Das folgende Codefragment legt zunächst Berechtigungen für alle DGM-UEFI-Einstellungen fest, sodass Sie nur von Semm geändert werden können, und fügt dann explizite Berechtigungen hinzu, um dem lokalen Benutzer das Ändern des UEFI-Kennworts, des TPM und der Front-und rückkamera zu ermöglichen.

```powershell
210 # Configure Permissions
211 foreach ($uefiV2 IN $surfaceDevices.Values) {
212 if ($uefiV2.SurfaceUefiFamily -eq $Device.Model) {
213 Write-Host "Configuring permissions"
214 Write-Host $Device.Model
215 Write-Host "======================="
216
217 # Here we define which "identities" will be allowed to modify which settings
218 #   PermissionSignerOwner = The primary SEMM enterprise owner identity
219 #   PermissionLocal = The user when booting to the UEFI pre-boot GUI
220 #   PermissionSignerUser, PermissionSignerUser1, PermissionSignerUser2 =
221 #     Additional user identities created so that the signer owner
222 #     can delegate permission control for some settings.
223 $ownerOnly = [Microsoft.Surface.IUefiSetting]::PermissionSignerOwner
224 $ownerAndLocalUser = ([Microsoft.Surface.IUefiSetting]::PermissionSignerOwner -bor [Microsoft.Surface.IUefiSetting]::PermissionLocal)
225 
226 # Make all permissions owner only by default
227 foreach ($setting IN $uefiV2.Settings.Values) {
228 $setting.ConfiguredPermissionFlags = $ownerOnly
229 }
230 
231 # Allow the local user to change their own password
232 $uefiV2.SettingsById[501].ConfiguredPermissionFlags = $ownerAndLocalUser
233
234 Write-Host ""
235  
236 # Create a unique package name based on family and LSV.
237 # We will choose a name that can be parsed by later scripts.
238 $packageName = $uefiV2.SurfaceUefiFamily + "^Permissions^" + $lsv + ".pkg"
239 $fullPackageName = Join-Path -Path $packageRoot -ChildPath $packageName
240 
241 # Build and sign the Permission package then save it to a file.
242 $permissionPackageStream =  $uefiV2.BuildAndSignPermissionPackage($privateOwnerKey, $password, "", $null, $lsv)
243 $permissionPackage = New-Object System.IO.Filestream($fullPackageName, [System.IO.FileMode]::CreateNew, [System.IO.FileAccess]::Write)
244 $permissionPackageStream.CopyTo($permissionPackage)
245 $permissionPackage.Close()
246 }
247 }
```

Jede **$uefiV 2** -Variable kennzeichnet eine DGM-UEFI-Einstellung durch Festlegen von Name oder ID und konfiguriert dann die Berechtigungen auf einen der folgenden Werte:

* **$ownerOnly** – die Berechtigung zum Ändern dieser Einstellung wird nur Semm gewährt.
* **$ownerAndLocalUser** – die Berechtigung zum Ändern dieser Einstellung wird einem lokalen Benutzer gewährt, der auf Surface UEFI und Semm.

Informationen zu den verfügbaren Einstellungsnamen und IDs für Surface UEFI finden Sie im Abschnitt [Settings Names and IDs](#settings-names-and-ids) in diesem Artikel.

###  <a name="configure-settings"></a>Konfigurieren von Einstellungen

Der zweite Bereich des Skripts, in dem Sie die Konfiguration für Surface UEFI angeben, ist der Bereich " **Einstellungen konfigurieren** " des ConfigureSEMM.ps1 Skripts, mit dem konfiguriert wird, ob jede Einstellung aktiviert oder deaktiviert ist. Das Beispielskript enthält Anweisungen zum Festlegen aller Einstellungen auf die Standardwerte. Das Skript enthält dann explizite Anweisungen, um IPv6 für PXE-Start zu deaktivieren und das Surface UEFI-Administrator Kennwort unverändert zu lassen. Sie finden diese Region beginnend mit dem Kommentar **# Configure Settings** in Zeile 291 bis Zeile 335 im Beispielskript. Der Bereich wird wie folgt angezeigt:

```powershell
291 # Configure Settings
292 foreach ($uefiV2 IN $surfaceDevices.Values) {
293 if ($uefiV2.SurfaceUefiFamily -eq $Device.Model) {
294 Write-Host "Configuring settings"
295 Write-Host $Device.Model
296 Write-Host "===================="
297
298 # In this demo, we will start by setting every setting to the default factory setting.
299 # You may want to start by doing this in your scripts
300 # so that every setting gets set to a known state.
301 foreach ($setting IN $uefiV2.Settings.Values) {
302 $setting.ConfiguredValue = $setting.DefaultValue
303 }
304 
305 $EnabledValue = "Enabled"
306 $DisabledValue = "Disabled"
307
308 # If you want to set something to a different value from the default,
309 # here are examples of how to accomplish this.
310 # This disables IPv6 PXE boot by name:
311 $uefiV2.Settings["IPv6 for PXE Boot"].ConfiguredValue = $DisabledValue
312
313 # This disables IPv6 PXE Boot by ID:
314 $uefiV2.SettingsById[400].ConfiguredValue = $DisabledValue
315
316 Write-Host ""
317
318 # If you want to leave the setting unmodified, set it to $null
319 # PowerShell has issues setting things to $null so ClearConfiguredValue()
320 # is supplied to do this explicitly.
321 # Here is an example of leaving the UEFI administrator password as-is,
322 # even after we initially set it to factory default above.
323 $uefiV2.SettingsById[501].ClearConfiguredValue()
324 
325 # Create a unique package name based on family and LSV.
326 # We will choose a name that can be parsed by later scripts.
327 $packageName = $uefiV2.SurfaceUefiFamily + "^Settings^" + $lsv + ".pkg"
328 $fullPackageName = Join-Path -Path $packageRoot -ChildPath $packageName
329 
330 # Build and sign the Settings package then save it to a file.
331 $settingsPackageStream =  $uefiV2.BuildAndSignSecuredSettingsPackage($privateOwnerKey, $password, "", $null, $lsv)
332 $settingsPackage = New-Object System.IO.Filestream($fullPackageName, [System.IO.FileMode]::CreateNew, [System.IO.FileAccess]::Write)
333 $settingsPackageStream.CopyTo($settingsPackage)
334 $settingsPackage.Close()
335 }
```

Wie die Berechtigungen, die im Abschnitt " **Berechtigungen konfigurieren** " des Skripts festgelegt sind, wird die Konfiguration der einzelnen DGM-UEFI-Einstellungen durch Definieren der **$uefiV 2** -Variablen ausgeführt. Für jede Zeile, die die Variable **$uefiV 2** definiert, wird eine DGM-UEFI-Einstellung durch Festlegen des Namens oder der ID identifiziert, und der konfigurierte Wert ist auf **Enabled** oder **disabled**festgelegt.

Wenn Sie die Konfiguration einer Oberflächen UEFI-Einstellung nicht ändern möchten, beispielsweise um sicherzustellen, dass das Kennwort des Surface UEFI-Administrators nicht durch die Aktion zurückgesetzt wird, die alle DGM-UEFI-Einstellungen auf Ihren Standard zurücksetzen, können Sie **ClearConfiguredValue ()** verwenden, um zu erzwingen, dass diese Einstellung nicht geändert wird. Im Beispielskript wird dies in Zeile 323 verwendet, um das Löschen des Oberflächen-UEFI-Administrator Kennworts zu verhindern, das im Beispielskript anhand der Einstellungs-ID **501**identifiziert wurde.

Informationen zu den verfügbaren Einstellungsnamen und IDs für Surface UEFI finden Sie im Abschnitt [Einstellungsnamen und IDs](#settings-names-and-ids) weiter unten in diesem Artikel.

###  <a name="settings-registry-key"></a>Registrierungsschlüssel "Einstellungen"

Zum Identifizieren von eingeschriebenen Systemen für Configuration Manager schreibt das ConfigureSEMM.ps1-Skriptregistrierungsschlüssel, die zum Identifizieren von eingeschriebenen Systemen verwendet werden können, wenn Sie mit dem Semm-Konfigurationsskript installiert wurden. Diese Schlüssel finden Sie am folgenden Standort.

`HKLM\SOFTWARE\Microsoft\Surface\SEMM`

Das folgende Codefragment, das in Zeilen 380-477 zu finden ist, wird zum Schreiben dieser Registrierungsschlüssel verwendet.

```powershell
380 # For Endpoint Configuration Manager or other management solutions that wish to know what version is applied, tattoo the LSV and current DateTime (in UTC) to the registry:
381 $UTCDate = (Get-Date).ToUniversalTime().ToString()
382 $certIssuer = $certPrint.Issuer
383 $certSubject = $certPrint.Subject
384 
385 $SurfaceRegKey = "HKLM:\SOFTWARE\Microsoft\Surface\SEMM"
386 New-RegKey $SurfaceRegKey
387 $LSVRegValue = Get-ItemProperty $SurfaceRegKey LSV -ErrorAction SilentlyContinue
388 $DateTimeRegValue = Get-ItemProperty $SurfaceRegKey LastConfiguredUTC -ErrorAction SilentlyContinue
389 $OwnershipSessionIdRegValue = Get-ItemProperty $SurfaceRegKey OwnershipSessionId -ErrorAction SilentlyContinue
390 $PermissionSessionIdRegValue = Get-ItemProperty $SurfaceRegKey PermissionSessionId -ErrorAction SilentlyContinue
391 $SettingsSessionIdRegValue = Get-ItemProperty $SurfaceRegKey SettingsSessionId -ErrorAction SilentlyContinue
392 $IsResetRegValue = Get-ItemProperty $SurfaceRegKey IsReset -ErrorAction SilentlyContinue
393 $certUsedRegValue = Get-ItemProperty $SurfaceRegKey CertName -ErrorAction SilentlyContinue
394 $certIssuerRegValue = Get-ItemProperty $SurfaceRegKey CertIssuer -ErrorAction SilentlyContinue
395 $certSubjectRegValue = Get-ItemProperty $SurfaceRegKey CertSubject -ErrorAction SilentlyContinue
396 
397 
398 If ($LSVRegValue -eq $null)
399 {
400     New-ItemProperty -Path $SurfaceRegKey -Name LSV -PropertyType DWORD -Value $lsv | Out-Null
401 }
402 Else
403 {
404     Set-ItemProperty -Path $SurfaceRegKey -Name LSV -Value $lsv
405 }
406 
407 If ($DateTimeRegValue -eq $null)
408 {
409     New-ItemProperty -Path $SurfaceRegKey -Name LastConfiguredUTC -PropertyType String -Value $UTCDate | Out-Null
410 }
411 Else
412 {
413     Set-ItemProperty -Path $SurfaceRegKey -Name LastConfiguredUTC -Value $UTCDate
414 }
415 
416 If ($OwnershipSessionIdRegValue -eq $null)
417 {
418     New-ItemProperty -Path $SurfaceRegKey -Name OwnershipSessionId -PropertyType String -Value $ownerSessionIdValue | Out-Null
419 }
420 Else
421 {
422     Set-ItemProperty -Path $SurfaceRegKey -Name OwnershipSessionId -Value $ownerSessionIdValue
423 }
424 
425 If ($PermissionSessionIdRegValue -eq $null)
426 {
427     New-ItemProperty -Path $SurfaceRegKey -Name PermissionSessionId -PropertyType String -Value $permissionSessionIdValue | Out-Null
428 }
429 Else
430 {
431     Set-ItemProperty -Path $SurfaceRegKey -Name PermissionSessionId -Value $permissionSessionIdValue
432 }
433 
434 If ($SettingsSessionIdRegValue -eq $null)
435 {
436     New-ItemProperty -Path $SurfaceRegKey -Name SettingsSessionId -PropertyType String -Value $settingsSessionIdValue | Out-Null
437 }
438 Else
439 {
440     Set-ItemProperty -Path $SurfaceRegKey -Name SettingsSessionId -Value $settingsSessionIdValue
441 }
442 
443 If ($IsResetRegValue -eq $null)
444 {
445     New-ItemProperty -Path $SurfaceRegKey -Name IsReset -PropertyType DWORD -Value 0 | Out-Null
446 }
447 Else
448 {
449     Set-ItemProperty -Path $SurfaceRegKey -Name IsReset -Value 0
450 }
451 
452 If ($certUsedRegValue -eq $null)
453 {
454     New-ItemProperty -Path $SurfaceRegKey -Name CertName -PropertyType String -Value $certName | Out-Null
455 }
456 Else
457 {
458     Set-ItemProperty -Path $SurfaceRegKey -Name CertName -Value $certName
459 }
460 
461 If ($certIssuerRegValue -eq $null)
462 {
463     New-ItemProperty -Path $SurfaceRegKey -Name CertIssuer -PropertyType String -Value $certIssuer | Out-Null
464 }
465 Else
466 {
467     Set-ItemProperty -Path $SurfaceRegKey -Name CertIssuer -Value $certIssuer
468 }
469 
470 If ($certSubjectRegValue -eq $null)
471 {
472     New-ItemProperty -Path $SurfaceRegKey -Name CertSubject -PropertyType String -Value $certSubject | Out-Null
473 }
474 Else
475 {
476     Set-ItemProperty -Path $SurfaceRegKey -Name CertSubject -Value $certSubject
477 }
```

### <a name="settings-names-and-ids"></a>Einstellungsnamen und IDs

Wenn Sie die Oberflächen-UEFI-Einstellungen oder-Berechtigungen für die Oberflächen-UEFI-Einstellungen konfigurieren möchten, müssen Sie entweder den Einstellungsnamen oder die Einstellungs-ID verwenden. Bei jedem neuen Update für Surface UEFI können neue Einstellungen hinzugefügt werden. Die beste Methode, um eine vollständige Liste der auf einem Surface-Gerät verfügbaren Einstellungen zusammen mit dem Einstellungsnamen und den Einstellungen-IDs abzurufen, besteht darin, das ShowSettingsOptions.ps1-Skript aus SEMM_Powershell.zip in [Surface Tools für IT-Downloads](https://www.microsoft.com/download/details.aspx?id=46703) zu verwenden. 

Auf dem Computer, auf dem ShowSettingsOptions.ps1 ausgeführt wird, muss Microsoft Surface UEFI Manager installiert sein, das Skript erfordert jedoch kein Surface-Gerät.


## <a name="deploy-semm-configuration-manager-scripts"></a>Bereitstellen von Semm-Konfigurations-Manager-Skripts

Nachdem Ihre Skripts bereit sind, Semm auf dem Clientgerät zu konfigurieren und zu aktivieren, besteht der nächste Schritt darin, diese Skripts als Anwendung in Configuration Manager hinzuzufügen. Bevor Sie Configuration Manager öffnen, stellen Sie sicher, dass sich die folgenden Dateien in einem freigegebenen Ordner befinden, in dem keine anderen Dateien enthalten sind:

* ConfigureSEMM.ps1
* ResetSEMM.ps1
* Ihr Semm-Zertifikat (beispielsweise SEMMCertificate. pfx)

Die Semm-Konfigurations-Manager-Skripts werden dem Configuration Manager als Skriptanwendung hinzugefügt. Der Befehl zum Installieren von Semm mit ConfigureSEMM.ps1 lautet wie folgt:

`Powershell.exe -file ".\ConfigureSEMM.ps1"`

Der Befehl zum Deinstallieren von Semm mit ResetSEMM.ps1 lautet wie folgt:

`Powershell.exe -file ".\ResetSEMM.ps1"`

Verwenden Sie zum Hinzufügen der Semm-Konfigurations-Manager-Skripts zu Configuration Manager als Anwendung den folgenden Prozess:

1. Starten Sie den Assistenten zum Erstellen von Anwendungen mit Schritt 1 bis Schritt 5 aus dem Abschnitt [Microsoft Surface UEFI Manager bereitstellen](#deploy-microsoft-surface-uefi-manager) weiter oben in diesem Artikel.

2. Gehen Sie mit dem Assistenten zum Erstellen von Anwendungen wie folgt vor:

   - **Allgemein** – wählen Sie **die Anwendungsinformationen manuell angeben**aus, und wählen Sie dann **weiter**aus.

   - **Allgemeine Informationen** : Geben Sie einen Namen für die Anwendung (beispielsweise Semm) und alle weiteren gewünschten Informationen wie Publisher, Version oder Kommentare auf dieser Seite ein. Wählen Sie **weiter** aus, um fortzufahren.

   - **Anwendungskatalog** – die Felder auf dieser Seite können mit ihren Standardwerten verbleibt. Wählen Sie **Weiter** aus.

   - **Bereitstellungstypen** – wählen Sie **Hinzufügen** aus, um den Assistenten zum Erstellen von Bereitstellungstypen zu starten.

   - Führen Sie die Schritte des Assistenten zum Erstellen von Bereitstellungstypen wie folgt aus:

     * **Allgemein** – wählen Sie im Dropdownmenü **Typ** den Eintrag **Skript Installationsprogramm** aus. Die Option " **Bereitstellungsinformationen manuell angeben** " wird automatisch ausgewählt. Wählen Sie **weiter** aus, um fortzufahren.
     * **Allgemeine Informationen** : Geben Sie einen Namen für den Bereitstellungs ein (beispielsweise Semm-Konfigurationsskripts), und wählen Sie dann **weiter** aus, um fortzufahren.
     * **Inhalt** – wählen Sie neben dem Feld **Inhaltsspeicherort** die Option **Durchsuchen** aus, und wählen Sie dann den Ordner aus, in dem sich die Semm-Konfigurations-Manager-Skripts befinden. Geben Sie im Feld **Installationsprogramm** den oben in diesem Artikel gefundenen [Installationsbefehl](#deploy-semm-configuration-manager-scripts) ein. Geben Sie im Feld **Programm deinstallieren** den zuvor in diesem Artikel gefundenen [Deinstallationsbefehl](#deploy-semm-configuration-manager-scripts) ein (siehe Abbildung 2). Wählen Sie **weiter** aus, um zur nächsten Seite zu wechseln.
    
     ![Einrichten der Semm-Konfigurations-Manager-Skripts als Befehle zum Installieren und deinstallieren](images/config-mgr-semm-fig2.png "Set the SEMM Configuration Manager scripts as the install and uninstall commands")

     *Abbildung2. Einrichten der Semm-Konfigurations-Manager-Skripts als Befehle zum Installieren und deinstallieren*

     * **Detection-Methode** – wählen Sie **Add-Klausel** aus, um die Erkennungsregel des Semm-Konfigurations-Manager-Skript Registrierungsschlüssels hinzuzufügen. Das Fenster **Erkennungsregel** wird angezeigt, wie in Abbildung 3 dargestellt. Verwenden Sie die folgenden Einstellungen:

       - Wählen Sie im Dropdownmenü **Einstellungstyp** die Option **Registrierung** aus.
       - Wählen Sie im Dropdownmenü **Hive** den Eintrag **HKEY_LOCAL_MACHINE** aus.
       - Geben Sie **SOFTWARE\Microsoft\Surface\SEMM** in das **Schlüssel** Feld ein.
       - Geben Sie im Feld **Wert den Wert** **CertName** ein.
       - Wählen Sie im Dropdownmenü **Datentyp** die Option **Zeichenfolge** aus.
       - Wählen Sie die **Registrierungseinstellung muss die folgende Regel erfüllen, um das vorhanden sein dieser Anwendungsschaltfläche anzugeben** .
       - Geben Sie den Namen des Zertifikats ein, das Sie in Zeile 58 des Skripts im Feld **Wert** eingegeben haben.
       - Wählen Sie **OK** aus, um das Fenster **Erkennungsregel** zu schließen.

     ![Verwenden eines Registrierungsschlüssels zum Identifizieren von in Semm registrierten Geräten](images/config-mgr-semm-fig3.png "Use a registry key to identify devices enrolled in SEMM")
     
     *Abbildung3. Verwenden eines Registrierungsschlüssels zum Identifizieren von in Semm registrierten Geräten*

     * Wählen Sie **weiter** aus, um zur nächsten Seite zu gelangen.
     
     * **Benutzererfahrung** : Wählen Sie im Dropdownmenü **Installationsverhalten** die Option **für System installieren** aus. Wenn Sie möchten, dass die Benutzer den Fingerabdruck des Zertifikats selbst aufzeichnen und eingeben können, lassen Sie die Anmeldeanforderung **nur dann fest, wenn ein Benutzer angemeldet ist**. Wenn Sie möchten, dass Ihre Administratoren den Fingerabdruck für Benutzer eingeben und die Benutzer den Fingerabdruck nicht sehen müssen, wählen Sie aus dem Dropdownmenü **Anmeldeanforderung** aus, **ob ein Benutzer angemeldet ist** .

     * **Anforderungen** – das ConfigureSEMM.ps1-Skript überprüft automatisch, ob es sich bei dem Gerät um ein Surface-Device handelt, bevor Sie versuchen, Semm zu aktivieren. Wenn Sie jedoch beabsichtigen, diese Skriptanwendung für eine Sammlung mit anderen Geräten als denjenigen bereitzustellen, die mit Semm verwaltet werden sollen, können Sie hier Anforderungen hinzufügen, um sicherzustellen, dass diese Anwendung nur auf Surface-Geräten oder-Geräten ausgeführt wird, die Sie mit Semm verwalten möchten. Wählen Sie **weiter** aus, um fortzufahren.
     
     * **Abhängigkeiten** – wählen Sie **Hinzufügen** aus, um das Fenster **Abhängigkeit hinzufügen** zu öffnen.

       * Wählen Sie **Hinzufügen** aus, um das Fenster **erforderliche Anwendung angeben** zu öffnen.

          - Geben Sie im Feld **Name der Abhängigkeitsgruppe** einen Namen für die Semm-Abhängigkeiten ein (beispielsweise *Semm-Assemblys*).

          - Wählen Sie **Microsoft Surface UEFI Manager** aus der Liste der **verfügbaren Anwendungen** und dem MSI-Bereitstellungs aus, und wählen Sie dann **OK** aus, um das Fenster **erforderliche Anwendung angeben** zu schließen.
          
         *   Aktivieren Sie das Kontrollkästchen **Automatische Installation** , wenn Microsoft Surface UEFI Manager automatisch auf Geräten installiert werden soll, wenn Sie versuchen, Semm mit den Configuration Manager-Skripts zu aktivieren. Wählen Sie **OK** aus, um das Fenster **Abhängigkeit hinzufügen** zu schließen.

     * Wählen Sie **weiter** aus, um fortzufahren.
     
     * **Zusammenfassung** – die Informationen, die Sie im Assistenten zum Erstellen von Bereitstellungstypen eingegeben haben, werden auf dieser Seite angezeigt. Wählen Sie **weiter** aus, um Ihre Auswahl zu bestätigen.
     
     * **Fortschritt** – auf dieser Seite wird eine Statusanzeige und ein Status angezeigt, während der Bereitstellungs für die Semm-Skriptanwendung hinzugefügt wird.
     
     * **Fertigstellung** – Bestätigung der Erstellung des Bereitstellungstyps wird angezeigt, wenn der Prozess abgeschlossen ist. Wählen Sie **Schließen** aus, um den Assistenten zum Erstellen von Bereitstellungstypen abzuschließen.

   - **Zusammenfassung** – die Informationen, die Sie im Assistenten zum Erstellen von Anwendungen eingegeben haben, werden angezeigt. Wählen Sie **weiter** aus, um die Anwendung zu erstellen.

   - **Fortschritt** – auf dieser Seite wird eine Statusanzeige und ein Status angezeigt, während die Anwendung zur Software Bibliothek hinzugefügt wird.

   - **Fertigstellung** – die Bestätigung der erfolgreichen Anwendungserstellung wird angezeigt, wenn der Anwendungs Erstellungsprozess abgeschlossen ist. Wählen Sie **Schließen** aus, um den Assistenten zum Erstellen von Anwendungen abzuschließen.

Nachdem die Skriptanwendung in der Software Bibliothek von Configuration Manager verfügbar ist, können Sie Semm mithilfe der Skripts, die Sie auf Geräte oder Sammlungen vorbereitet haben, verteilen und bereitstellen. Wenn Sie die Microsoft Surface UEFI Manager-Assemblys als eine Abhängigkeit konfiguriert haben, die automatisch installiert wird, können Sie Semm in einem einzigen Schritt bereitstellen. Wenn Sie die Assemblys nicht als Abhängigkeit konfiguriert haben, müssen Sie auf den Geräten installiert werden, die Sie verwalten möchten, bevor Sie Semm aktivieren.

Wenn Sie Semm mithilfe dieser Skriptanwendung und einer für den Endbenutzer sichtbaren Konfiguration bereitstellen, wird das PowerShell-Skript gestartet, und der Fingerabdruck für das Zertifikat wird vom PowerShell-Fenster angezeigt. Sie können feststellen, dass Ihre Benutzer diesen Fingerabdruck aufzeichnen und beim erneuten Booten des Geräts nach der Eingabeaufforderung von Surface UEFI eingeben.

Alternativ können Sie die Anwendungsinstallation so konfigurieren, dass Sie automatisch neu gestartet und für den Benutzer unsichtbar installiert wird. In diesem Szenario muss ein Techniker den Fingerabdruck auf jedem Gerät eingeben, während er neu gestartet wird. Jeder Techniker, der Zugriff auf die Zertifikatsdatei hat, kann den Fingerabdruck lesen, indem Sie das Zertifikat mit CertMgr anzeigen. Anweisungen zum Anzeigen des Fingerabdrucks mit certmgr finden Sie im Abschnitt [erstellen oder Ändern der Semm-Konfigurations-Manager-Skripts](#create-or-modify-the-semm-configuration-manager-scripts) in diesem Artikel.

Das Entfernen von Semm von einem Gerät, das mit Configuration Manager mithilfe dieser Skripts bereitgestellt wird, ist so einfach wie das Deinstallieren der Anwendung mit Configuration Manager. Mit dieser Aktion wird das ResetSEMM.ps1 Skript gestartet, und die Registrierung des Geräts mit der gleichen Zertifikatdatei, die während der Bereitstellung von Semm verwendet wurde, wird ordnungsgemäß abgemeldet.

> [!NOTE]
> Microsoft Surface empfiehlt, dass Sie Pakete nur zurücksetzen erstellen, wenn Sie die Registrierung eines Geräts aufheben müssen. Diese Reset-Pakete gelten in der Regel nur für ein Gerät, das durch seine Seriennummer gekennzeichnet ist. Sie können jedoch ein universelles Reset-Paket erstellen, das für jedes Gerät, das mit diesem Zertifikat in Semm registriert ist, funktionieren würde.
> 
> Wir empfehlen dringend, das universelle Reset-Paket so sorgfältig wie das Zertifikat zu schützen, das Sie für die Registrierung von Geräten in Semm verwendet haben. Beachten Sie bitte, dass dieses universelle Reset-Paket genauso wie das Zertifikat selbst verwendet werden kann, um die Registrierung von Surface-Geräten Ihrer Organisation von Semm zu entbinden.
> 
> Wenn Sie ein Reset-Paket installieren, wird der niedrigste unterstützte Wert (LSV) auf den Wert 1 zurückgesetzt. Sie können ein Gerät mithilfe eines vorhandenen Konfigurationspakets erneut registrieren. Das Gerät fordert den Fingerabdruck des Zertifikats auf, bevor der Besitz übernommen wird.
> 
> Aus diesem Grund würde die erneute Registrierung eines Geräts in Semm erfordern, dass ein neues Paket auf dem Gerät erstellt und installiert wird. Da es sich bei dieser Aktion um eine neue Registrierung und nicht um eine Änderung der Konfiguration auf einem Gerät handelt, das bereits in Semm registriert ist, wird das Gerät zum Fingerabdruck des Zertifikats aufgefordert, bevor der Besitz übernommen wird.
