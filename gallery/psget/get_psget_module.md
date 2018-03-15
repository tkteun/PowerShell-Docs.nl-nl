---
ms.date: 2017-06-12
contributor: manikb
ms.topic: reference
keywords: Galerie, powershell, cmdlet, psget
title: PowerShellGet Module ophalen
ms.openlocfilehash: 7224cf5d71b98d51ca22c47a00ca382d34864bfb
ms.sourcegitcommit: 99227f62dcf827354770eb2c3e95c5cf6a3118b4
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 03/15/2018
---
<a name="get-powershellget-module"></a>PowerShellGet Module ophalen
========================

### <a name="powershellget-is-an-in-box-module-in-the-following-releases"></a>PowerShellGet is een module in het vak in de volgende versies
- [Windows 10](https://www.microsoft.com/windows/get-windows-10) of hoger
- [Windows Server 2016](https://technet.microsoft.com/windows-server-docs/get-started/windows-server-2016) of hoger
- [Windows Management Framework (WMF) 5.0](https://www.microsoft.com/download/details.aspx?id=50395) of hoger
- [PowerShell 6](https://github.com/PowerShell/PowerShell/releases)

### <a name="get-powershellget-module-for-powershell-versions-30-and-40"></a>PowerShellGet module ophalen voor PowerShell versie 3.0 en 4.0
- [PackageManagement MSI](http://go.microsoft.com/fwlink/?LinkID=746217&clcid=0x409) 

### <a name="get-the-latest-version-from-powershell-gallery"></a>Ophalen van de meest recente versie van PowerShell Gallery

- Voordat u PowerShellGet bijwerkt, moet u altijd de meest recente Nuget-provider installeren. Voer hiertoe de volgende in een PowerShell-sessie met verhoogde bevoegdheden.
```powershell
Install-PackageProvider Nuget –Force
Exit
```

#### <a name="for-systems-with-powershell-50-or-newer-you-can-install-the-latest-powershellget"></a>Voor systemen met PowerShell 5.0 (of nieuwer) kunt u de meest recente PowerShellGet installeren 
- Voer de volgende opdrachten vanuit een PowerShell-sessie met verhoogde bevoegdheden om dit te doen op Windows 10, Windows Server 2016, elk systeem met WMF 5.0 of 5.1 is geïnstalleerd of een systeem met PowerShell-6.
```powershell
Install-Module –Name PowerShellGet –Force
Exit
```

- Update-Module gebruiken om nieuwe versies.
```powershell
Update-Module -Name PowerShellGet
Exit
```

#### <a name="for-systems-running-powershell-3-or-powershell-4-that-have-installed-the-packagemanagement-msihttpgomicrosoftcomfwlinklinkid746217clcid0x409"></a>Voor systemen met PowerShell 3 of 4 PowerShell, die beschikken over de [PackageManagement MSI](http://go.microsoft.com/fwlink/?LinkID=746217&clcid=0x409)

- Gebruik onderstaande PowerShellGet cmdlet vanuit een PowerShell-sessie met verhoogde bevoegdheid de modules opslaan naar een lokale map

```powershell
Save-Module PowerShellGet -Path C:\LocalFolder
Exit
```

- Zorg ervoor dat PowerShellGet en PackageManagment modules niet worden geladen in andere processen.
- Verwijderen van de inhoud van `$env:ProgramFiles\WindowsPowerShell\Modules\PowerShellGet\` en `$env:ProgramFiles\WindowsPowerShell\Modules\PackageManagement\` mappen.
- Open deze opnieuw de PS-Console met verhoogde bevoegdheden en voer vervolgens de volgende opdrachten.

```powershell
Copy-Item "C:\LocalFolder\PowerShellGet\*" "$env:ProgramFiles\WindowsPowerShell\Modules\PowerShellGet\" -Recurse -Force
Copy-Item "C:\LocalFolder\PackageManagement\*" "$env:ProgramFiles\WindowsPowerShell\Modules\PackageManagement\" -Recurse -Force