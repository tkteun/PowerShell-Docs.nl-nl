---
ms.date: 04/19/2019
keywords: wmf,powershell,installeren
title: Windows Management Framework (WMF)
ms.openlocfilehash: d581370fd602e03c86aa549eb8b273ff4d01b4e5
ms.sourcegitcommit: 6545c60578f7745be015111052fd7769f8289296
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 04/22/2020
ms.locfileid: "71145248"
---
# <a name="windows-management-framework"></a>Windows Management Framework

Windows Management Framework (WMF) biedt een consistente beheer interface voor Windows. WMF biedt een naadloze manier voor het beheren van verschillende versies van Windows-clients en Windows Server. WMF-installatie pakketten bevatten updates voor de beheer functionaliteit en zijn beschikbaar voor oudere versies van Windows.

WMF-installatie voegt de volgende functies toe en/of werkt deze bij:

- Windows PowerShell
- Windows PowerShell Desired State Configuration (DSC)
- Windows Power shell Integrated Scripting Environment (ISE)
- Windows Remote Management (WinRM)
- Windows Management Instrumentation (WMI)
- Windows Power shell Web Services (Management OData IIS-extensie)
- Registratie van software-inventaris (SIL)
- Serverbeheer CIM-provider

## <a name="wmf-release-notes"></a>Opmerkingen bij de release van WMF

Raadpleeg de onderstaande koppelingen voor meer informatie over verschillende uitbrei dingen in Power shell en andere onderdelen van een bepaalde WMF om de release opmerkingen te bekijken:

- [WMF 5.1](whats-new/release-notes.md#wmf-51-changes)
- [WMF 5.0](whats-new/release-notes.md#wmf-50-changes)
- [WMF 4.0](https://download.microsoft.com/download/3/D/6/3D61D262-8549-4769-A660-230B67E15B25/Windows%20Management%20Framework%204%200%20Release%20Notes.docx)
- [WMF 3.0](https://download.microsoft.com/download/E/7/6/E76850B8-DA6E-4FF5-8CCE-A24FC513FD16/WMF%203%20Release%20Notes.docx)

## <a name="wmf-availability-across-windows-operating-systems"></a>WMF-Beschik baarheid in Windows-besturings systemen

|        Versie van besturingssysteem         | [WMF 5.1][]  | WMF 5.0<br>*Geen ondersteuning meer* | [WMF 4.0][]  | [WMF 3.0][]  | [WMF 2.0][]  |
| --------------------------------------- | ------------ | --------------------------- | ------------ | ------------ | ------------ |
| Windows Server 2019                     | Verzonden in box |                             |              |              |              |
| Windows Server 2016                     | Verzonden in box |                             |              |              |              |
| Windows 10                              | Verzonden in box | Verzonden in box                |              |              |              |
| Windows Server 2012 R2                  | Ja          | Ja                         | Verzonden in box |              |              |
| Windows 8.1                             | Ja          | Ja                         | Verzonden in box |              |              |
| Windows Server 2012                     | Ja          | Ja                         | Ja          | Verzonden in box |              |
| Windows 8<br>*Geen ondersteuning meer*           |              |                             |              | Verzonden in box |              |
| Windows Server 2008 R2 SP1              | Ja          | Ja                         | Ja          | Ja          | Verzonden in box |
| Windows 7 SP1                           | Ja          | Ja                         | Ja          | Ja          | Verzonden in box |
| Windows Server 2008 SP2                 |              |                             |              | Ja          | Ja          |
| Windows Vista<br>*Geen ondersteuning meer*       |              |                             |              |              | Ja          |
| Windows Server 2003<br>*Geen ondersteuning meer* |              |                             |              |              | Ja          |
| Windows XP<br>*Geen ondersteuning meer*          |              |                             |              | Ja          | Ja          |

- Wordt **meegeleverd in box**: de functies van de opgegeven versie van WMF zijn verzonden in de aangegeven versie van Windows-client of Windows Server.
- **Niet meer beschikbaar: deze**producten worden niet meer ondersteund door micro soft. U moet een upgrade uitvoeren naar een nieuwe versie die wordt ondersteund. Zie de pagina [micro soft Lifecycle-beleid][] voor meer informatie.

> [!NOTE]
> Het installatie programma voor WMF 5,0 is niet meer beschikbaar of wordt niet ondersteund. Het is vervangen door WMF 5,1.

[Micro soft Lifecycle-beleid]: https://support.microsoft.com/lifecycle
[WMF 5.1]: https://aka.ms/wmf51download
[WMF 4.0]: https://aka.ms/wmf4download
[WMF 3.0]: https://aka.ms/wmf3download
[WMF 2.0]: https://aka.ms/wmf2download
