---
ms.date: 2017-06-12
author: JKeithB
ms.topic: reference
keywords: wmf,powershell,installeren
title: Releaseopmerkingen WMF 5.1
ms.openlocfilehash: fa3d9a3563ecf1bfc76d82b027641d19c9a4ff4e
ms.sourcegitcommit: 99227f62dcf827354770eb2c3e95c5cf6a3118b4
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 03/15/2018
---
# <a name="windows-management-framework-wmf-51-release-notes"></a>Windows Management Framework (WMF) 5.1 Release-opmerkingen #

WMF 5.1 bevat de onderdelen die PowerShell, WMI, WinRM en Software Inventory Logging (SIL) die zijn uitgebracht met Windows Server 2016.
WMF 5.1 kan worden geïnstalleerd op Windows 7, Windows 8.1, Windows Server 2008 R2, 2012 en 2012 R2 en biedt een aantal verbeteringen ten opzichte van WMF 5.0 RTM, waaronder:

- Nieuwe cmdlets: lokale gebruikers en groepen; Get-ComputerInfo
- PowerShellGet-verbeteringen, waaronder het afdwingen van ondertekende modules en het installeren van JEA-modules
- Ondersteuning in PackageManagement toegevoegd voor Containers, CBS Setup, EXE-installatie en CAB-pakketten
- Verbeteringen in foutopsporing voor DSC- en PowerShell-klassen
- Beveiligingsverbeteringen, waaronder de handhaving van door catalogus ondertekende modules die afkomstig zijn van de pull-server, gebruikt in combinatie met PowerShellGet-cmdlets
- Antwoorden op een aantal gebruikersaanvragen en -problemen

**Belangrijke opmerkingen:**

- **WMF 5.1 vereist .NET Framework 4.5.2** (of hoger). Installatie wordt voltooid, maar de belangrijkste functies mislukken als .NET 4.5.2 (of hoger) is niet geïnstalleerd. Instructies zijn beschikbaar in de [installeren en configureren van WMF 5.1 ](https://msdn.microsoft.com/powershell/wmf/5.1/install-configure) onderwerp.
- WMF 5.1 Preview moet worden verwijderd voordat het installeren van WMF 5.1 RTM.
- WMF 5.1 kan rechtstreeks via WMF 5.0 of WMF 4.0 worden geïnstalleerd.
- Het is __niet vereist__ WMF 4.0 installeren voordat u WMF 5.1 op Windows 7 en Windows Server 2008 R2 installeert. Die was een probleem voor de evaluatieversie van WMF 5.1 en opgelost.  


