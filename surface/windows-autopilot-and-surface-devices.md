---
title: Windows Autopilot und Surface-Geräte
ms.reviewer: ''
manager: laurawi
description: Erfahren Sie mehr über die Bereitstellungsoptionen von Windows Autopilot für Surface-Geräte.
keywords: Autopilot, Windows 10, Oberfläche, Bereitstellung
ms.prod: w10
ms.mktglfcycl: deploy
ms.pagetype: surface, devices
ms.sitesec: library
author: coveminer
ms.author: greglin
ms.topic: article
ms.localizationpriority: medium
ms.audience: itpro
ms.date: 9/14/2020
ms.openlocfilehash: 31f11db8c3ab12d1af754267022d9060d3a8c026
ms.sourcegitcommit: 1b86286bd13b13749ddbf454ae78d9a24fec44ee
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/15/2021
ms.locfileid: "11271101"
---
# Windows Autopilot und Surface-Geräte

Windows Autopilot ist eine cloudbasierte Bereitstellungstechnologie in Windows 10. Sie können Windows Autopilot verwenden, um Geräte remote in einem Zero-Touch-Prozess direkt direkt im Einsatz zu bereitstellen und zu konfigurieren.

Traditionell verbringen die IT-Profis viel Zeit mit dem Erstellen und Anpassen von Images, die später auf Geräten bereitgestellt werden, die bereits über ein einwandfreies Betriebssystem verfügen, das bereits auf ihnen installiert ist. Windows Autopilot führt einen neuen Zero-Touch-Bereitstellungsansatz ein, der eine Sammlung von Technologien zum Einrichten und Konfigurieren von Windows-Geräten verwendet. Dies ermöglicht es einer IT-Abteilung, Bilder mit wenig bis keiner zu verwaltende Infrastruktur und einem einfachen Prozess zu konfigurieren/anzupassen. Aus Der Sicht des Benutzers sind nur einige einfache Schritte erforderlich, um Surface in einen produktiven Zustand zu bekommen. Tatsächlich ist die einzige Interaktion, die vom Endbenutzer benötigt wird, die Verbindung mit einem Netzwerk herzustellen und seine Anmeldeinformationen zu überprüfen. Alles danach ist vollständig automatisiert.

Windows Autopilot ermöglicht Ihnen:

- Automatisches Verbinden von Geräten mit Azure Active Directory (Azure AD).
- Automatisches Registrieren von Geräten bei MDM-Diensten, z. B. Microsoft Intune (erfordert ein Azure AD Premium-Abonnement).
- Einschränkung der Administratorkontoerstellung. Autopilot ist die einzige Möglichkeit, die erste Person, die sich bei Windows anmeldet, als Standardbenutzer eingeben zu lassen.
- Erstellen und automatisches Zuweisen von Geräten zu Konfigurationsgruppen basierend auf Geräteprofilen.
- Passen Sie die Inhalte und das Branding der OOBE (Out of Box Experience) an, um die Organisatorischen Anforderungen zu erfüllen.
- Aktivieren sie die vollständige Gerätekonfiguration mit Intune.
- Setzen Sie Geräte remote zurück oder starten Sie sie neu.

##  <a name="how-it-works"></a>Funktionsweise

Windows Autopilot-registrierte Geräte werden beim ersten Start über das Internet durch eine eindeutige Gerätesignatur identifiziert, die als *Hardwarehash bezeichnet wird.* Sie werden automatisch mithilfe moderner Verwaltungslösungen wie Azure Active Directory (Azure AD) und verwaltung mobiler Geräte registriert und konfiguriert.

Sie können die Geräte von Surface zum Zeitpunkt des Kaufs bei einem Surface-Partner registrieren, der für Windows Autopilot aktiviert ist. Diese Partner können neue Geräte direkt an Ihre Benutzer versenden. Die Geräte werden automatisch registriert und konfiguriert, wenn sie zum ersten Mal aktiviert werden. Bei diesem Prozess wird das Reimaging während der Bereitstellung verhindert, wodurch Sie neue, agile Methoden zur Geräteverwaltung und -verteilung implementieren können.

##  <a name="modern-management"></a>Moderne Verwaltung

Autopilot ist die empfohlene Bereitstellungsoption für Surface-Geräte, einschließlich Surface Pro 7+, Surface Laptop 3, Surface Pro 7 und Surface Pro X, die speziell für die Bereitstellung über Autopilot entwickelt wurde.

 Am besten registrieren Sie Ihre Surface-Geräte mithilfe eines Microsoft Cloud-Lösungsanbieters. In diesem Schritt können Sie die UEFI-Firmwareeinstellungen auf Surface direkt über Intune verwalten. Es entfällt die Notwendigkeit, Geräte für die Zertifikatverwaltung physisch zu berühren. Weitere [Informationen finden Sie unter Intune-Verwaltung von Surface-UEFI-Einstellungen.](surface-manage-dfci-guide.md)

##  <a name="windows-version-considerations"></a>Überlegungen zur Windows-Version

Die umfassende Bereitstellung von Surface-Geräten über Windows Autopilot, einschließlich der Registrierung durch Surface-Partner zum Zeitpunkt des Kaufs, erfordert Windows 10 Version 1709 (Fall Creators Update) oder höher.

Diese #A0 unterstützen einen Hashwert von 4.000 Byte (4.000 Byte), der Geräte für Windows Autopilot eindeutig identifiziert, was für Bereitstellungen im großen Maßstab erforderlich ist. Alle neuen Surface-Geräte, einschließlich Surface Pro 7+, Surface Pro X und Surface Laptop 3, sind mit Windows 10 Version 1903 oder höher erhältlich.

##  <a name="exchange-experience-on-surface-devices-in-need-of-repair-or-replacement"></a>Exchange auf Surface-Geräten, die repariert oder ersetzt werden müssen

Microsoft überprüft jedes Surface automatisch auf die Registrierung von Autopilot und entfernt die Registrierung des Geräts vom Mandanten des Kunden.  Microsoft stellt sicher, dass das Ersatzgerät bei Windows Autopilot registriert ist, sobald ein Ersatz an den Kunden zurück versendet wird. Dieser Dienst ist für alle Geräteaustauschdienstbestellungen direkt bei Microsoft verfügbar.

> [!NOTE]
> Wenn Kunden einen Partner zum Zurückgeben von Geräten verwenden, ist der Partner für die Verwaltung des Austauschprozesses verantwortlich, einschließlich der Deregistrierung und Registrierung von Geräten bei Windows Autopilot.

##  <a name="microsoft-support-registration"></a>Registrierung des Microsoft -Support

Kunden und Microsoft Cloud Solution Providers (CSPs) haben die Möglichkeit, Surface Geräte zu registrieren, indem Sie Anforderungen an den Microsoft Support senden. Weitere Informationen finden Sie unter [Surface Registration Support für Windows Autopilot](surface-autopilot-registration-support.md).

##  <a name="surface-partners-enabled-for-windows-autopilot"></a>Für Windows Autopilot aktivierte Surface-Partner

Select Surface partners can enroll Surface devices in Windows Autopilot for you at the time of purchase. Sie können registrierte Geräte auch direkt an Ihre Benutzer versenden. Die Geräte können vollständig über einen Zero-Touch-Prozess mithilfe von Windows Autopilot, Azure AD und der Verwaltung mobiler Geräte konfiguriert werden.

Surface-Partner, die für Windows Autopilot aktiviert sind, sind:

| Partner in den USA | Globale Partner | US-Händler |
|--------------|---------------|-------------------|
| * [CDW](https://www.cdw.com/) | * [AUCH](https://www.also.com/ec/cms5/de_1010/1010_anbieter/microsoft/windows-autopilot/index.jsp) | * [Synnex](https://www.synnexcorp.com/us/microsoft/surface-autopilot/)  |
| * [Verbindung](https://www.connection.com/brand/microsoft/microsoft-surface)   | * [ATEA](https://www.atea.com/) | * [Techdata](https://www.techdata.com/)  |
| * [Insight](https://www.insight.com/en_US/buy/partner/microsoft/surface/windows-autopilot.html)  | * [Bechtle](https://www.bechtle.com/marken/microsoft/microsoft-windows-autopilot) | * [Ingram](https://go.microsoft.com/fwlink/p/?LinkID=2128954)   |
| * [15.](https://www.shi.com/Surface) | * [Cancom](https://www.cancom.de/) |    |
| * [LDI Connect](https://www.myldi.com/managed-it/)  | * [Computacenter](https://www.computacenter.com/uk) |    |
| * [F1](https://www.functiononeit.com/#empower)  |   |  |
| * [Geschützte Vertrauensstellung](https://go.microsoft.com/fwlink/p/?LinkID=2129005) | | | 

##  <a name="learn-more"></a>Mehr erfahren

Weitere Informationen zu Windows Autopilot finden Sie unter:
- [Übersicht über Windows Autopilot](https://docs.microsoft.com/windows/deployment/windows-autopilot/windows-10-autopilot)
- [Anforderungen für Windows Autopilot](https://docs.microsoft.com/windows/deployment/windows-autopilot/windows-autopilot-requirements)
- [Surface-Registrierungsunterstützung für Windows-Autopilot](surface-autopilot-registration-support.md)