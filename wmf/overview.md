---
ms.date: 04/19/2019
keywords: wmf,powershell,installeren
title: Windows Management Framework (WMF)
ms.openlocfilehash: 6d25b4025bbc86f6be0e5c74db9f1fbe6705d816
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62055442"
---
# <a name="windows-management-framework"></a>Windows Management Framework

Windows Management Framework (WMF) biedt een interface voor consistent beheer voor Windows. WMF biedt een naadloze manier voor het beheren van verschillende versies van Windows-clients en Windows Server. WMF installer-pakketten bevatten updates voor management-functionaliteit en zijn beschikbaar voor oudere versies van Windows.

Installatie van WMF wordt toegevoegd en/of updates van de volgende functies:

- Windows PowerShell
- Windows PowerShell Desired State Configuration (DSC)
- Windows PowerShell, geïntegreerd Script Environment (ISE)
- Windows Remote Management (WinRM)
- Windows Management Instrumentation (WMI)
- Windows PowerShell-webservices (Management OData IIS-extensie)
- Registratie van software-inventaris (SIL)
- Server Manager CIM Provider

## <a name="wmf-release-notes"></a>Opmerkingen bij de Release van WMF

Voor meer informatie over verschillende verbeteringen in PowerShell en andere onderdelen van een bepaalde WMF, Raadpleeg de onderstaande koppelingen om te controleren van de opmerkingen bij de release:

- [WMF 5.1](5.1/release-notes.md)
- [WMF 5.0](5.0/releasenotes.md)
- [WMF 4.0](https://download.microsoft.com/download/3/D/6/3D61D262-8549-4769-A660-230B67E15B25/Windows%20Management%20Framework%204%200%20Release%20Notes.docx)
- [WMF 3.0](https://download.microsoft.com/download/E/7/6/E76850B8-DA6E-4FF5-8CCE-A24FC513FD16/WMF%203%20Release%20Notes.docx)

## <a name="wmf-availability-across-windows-operating-systems"></a>WMF beschikbaarheid in Windows-besturingssystemen

|        Versie van besturingssysteem         | [WMF 5.1][]  | WMF 5.0<br>*Buiten-ondersteuning* | [WMF 4.0][]  | [WMF 3.0][]  | [WMF 2.0][]  |
| --------------------------------------- | ------------ | --------------------------- | ------------ | ------------ | ------------ |
| Windows Server 2019                     | Wordt verzonden in box |                             |              |              |              |
| Windows Server 2016                     | Wordt verzonden in box |                             |              |              |              |
| Windows 10                              | Wordt verzonden in box | Wordt verzonden in box                |              |              |              |
| Windows Server 2012 R2                  | Ja          | Ja                         | Wordt verzonden in box |              |              |
| Windows 8.1                             | Ja          | Ja                         | Wordt verzonden in box |              |              |
| Windows Server 2012                     | Ja          | Ja                         | Ja          | Wordt verzonden in box |              |
| Windows 8<br>*Buiten-ondersteuning*           |              |                             |              | Wordt verzonden in box |              |
| Windows Server 2008 R2 SP1              | Ja          | Ja                         | Ja          | Ja          | Wordt verzonden in box |
| Windows 7 SP1                           | Ja          | Ja                         | Ja          | Ja          | Wordt verzonden in box |
| Windows Server 2008 SP2                 |              |                             |              | Ja          | Ja          |
| Windows Vista<br>*Buiten-ondersteuning*       |              |                             |              |              | Ja          |
| Windows Server 2003<br>*Buiten-ondersteuning* |              |                             |              |              | Ja          |
| Windows XP<br>*Buiten-ondersteuning*          |              |                             |              | Ja          | Ja          |

- **Wordt geleverd in het vak**: De functies van de opgegeven versie van WMF zijn verzonden in de opgegeven versie van Windows client- of Windows Server.
- **Ondersteuning vervalt**: Deze producten zijn niet meer ondersteund door Microsoft. U moet een upgrade uitvoeren naar een nieuwe versie die wordt ondersteund. Zie voor meer informatie de [Microsoft Lifecycle-beleid][] pagina.

> [!NOTE]
> Het installatieprogramma voor WMF 5.0 is niet langer beschikbaar of wordt ondersteund. Deze is vervangen door WMF 5.1.

[Microsoft Lifecycle-beleid]: https://support.microsoft.com/lifecycle
[WMF 5.1]: https://aka.ms/wmf51download
[WMF 4.0]: https://aka.ms/wmf4download
[WMF 3.0]: https://aka.ms/wmf3download
[WMF 2.0]: https://aka.ms/wmf2download
