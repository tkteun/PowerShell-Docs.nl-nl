---
ms.date: 06/12/2017
keywords: wmf,powershell,installeren
title: Windows Management Framework (WMF)
ms.openlocfilehash: ae50e8d1495d7075163714ed873940d2d1d19b8e
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 05/17/2018
ms.locfileid: "34221864"
---
# <a name="windows-management-framework"></a>Windows Management Framework

Windows Management Framework (WMF) is het mechanisme voor levering die voorziet in een consistente interface tussen de verschillende versies van Windows en Windows Server.
Klanten krijgen met de installatie van WMF, een naadloze manier kunnen samenwerken tussen combinaties van besturingssystemen in hun omgeving.
WMF beschikbaar de updates voor de management-functionaliteit in een bepaalde versie van Windows en Windows Server voor installatie op lagere versies (meestal 2 lagere versies) van Windows en Windows Server.

WMF installatie worden toegevoegd en/of updates van de volgende functies:

- Windows PowerShell
- Windows PowerShell Desired State Configuration (DSC)
- Windows PowerShell Integrated Script Environment (ISE)
- Windows Remote Management (WinRM)
- Windows Management Instrumentation (WMI)
- Windows PowerShell-webservices (Management OData IIS-extensie)
- Registratie van software-inventaris (SIL)
- CIM-Provider van Serverbeheer

## <a name="wmf-release-notes"></a>WMF Release-opmerkingen

Voor meer informatie over verschillende verbeteringen in PowerShell en andere onderdelen van een bepaalde WMF, Raadpleeg de onderstaande koppelingen om te controleren van de release-opmerkingen:

- [WMF 5.1](5.1/release-notes.md)
- [WMF 5.0](5.0/releasenotes.md)
- [WMF 4.0](https://download.microsoft.com/download/3/D/6/3D61D262-8549-4769-A660-230B67E15B25/Windows%20Management%20Framework%204%200%20Release%20Notes.docx)
- [WMF 3.0](https://download.microsoft.com/download/E/7/6/E76850B8-DA6E-4FF5-8CCE-A24FC513FD16/WMF%203%20Release%20Notes.docx)

## <a name="wmf-availability-across-windows-operating-systems"></a>Beschikbaarheid van WMF volledige Windows-besturingssystemen

| Versie van besturingssysteem | [WMF 5.1](https://aka.ms/wmf51download) | [WMF 5.0](https://aka.ms/wmf5download) | [WMF 4.0](https://aka.ms/wmf4download) |  [WMF 3.0](https://aka.ms/wmf3download) | [WMF 2.0](https://aka.ms/wmf2download) |
| ------------------------ | ----------- | ----------- | ----------- | ------------ |  ------------- |
| Windows Server 2016 | Wordt verzonden in-box |  |  |  |  |
| Windows 10 | Wordt verzonden in-box | Wordt verzonden in-box  | | | |
| Windows Server 2012 R2| Ja | Ja | Wordt verzonden in-box |  |  |
| Windows 8.1 | Ja | Ja |  Wordt verzonden in-box |  |  |
| Windows Server 2012 | Ja | Ja | Ja |  Wordt verzonden in-box | |
| Windows 8 |  |  |  | Wordt verzonden in-box | |
| Windows Server 2008 R2 SP1 | Ja | Ja | Ja |  Ja| Wordt verzonden in-box |
| Windows 7 SP1  | Ja | Ja | Ja | Ja | Wordt verzonden in-box |
| Windows Server 2008 SP2 | | | | Ja | Ja |
| Windows Vista | | | | | Ja |
| Windows Server 2003| | | |  | Ja |
| Windows XP | | | |  | Ja |

**'Wordt geleverd in het vak'**: de functies van de `specified WMF` zijn verzonden in de opgegeven versie van Windows en Windows Server.
Daarom de `specified WMF` hoeven niet te worden geïnstalleerd op de aangegeven besturingssysteemversies.
