---
ms.date: 06/12/2017
contributor: manikb
keywords: Galerie, powershell, cmdlet, psget
title: PowerShellGet installeren
ms.openlocfilehash: 23a53a9117c9f6a7ad157b635cd7ff4b3b3444c5
ms.sourcegitcommit: caac7d098a448232304c9d6728e7340ec7517a71
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 03/16/2019
ms.locfileid: "58054819"
---
# <a name="installing-powershellget"></a>PowerShellGet installeren

## <a name="powershellget-is-an-in-box-module-in-the-following-releases"></a>PowerShellGet is een module in het vak in de volgende versies

- [Windows 10](https://www.microsoft.com/windows) of hoger
- [Windows Server 2016](/windows-server/windows-server) of hoger
- [Windows Management Framework (WMF) 5.0](https://www.microsoft.com/download/details.aspx?id=50395) of hoger
- [PowerShell 6](https://github.com/PowerShell/PowerShell/releases)

## <a name="get-powershellget-module-for-powershell-versions-30-and-40"></a>PowerShellGet-module voor PowerShell versie 3.0 en 4.0 ophalen

- [PackageManagement MSI](https://www.microsoft.com/download/details.aspx?id=51451)

## <a name="get-the-latest-version-from-powershell-gallery"></a>Download de nieuwste versie van PowerShell Gallery

- Voordat u PowerShellGet bijwerkt, moet u altijd de meest recente Nuget-provider installeren. Om dit te doen, voer de volgende in een PowerShell-sessie met verhoogde bevoegdheden.

  ```powershell
  Install-PackageProvider Nuget –Force
  Exit
  ```

### <a name="for-systems-with-powershell-50-or-newer-you-can-install-the-latest-powershellget"></a>Voor systemen met PowerShell 5.0 (of hoger) kunt u de meest recente PowerShellGet installeren

- Voer de volgende opdrachten vanuit een PowerShell-sessie met verhoogde bevoegdheden om dit te doen in Windows 10, Windows Server 2016, elk systeem met WMF 5.0 of 5.1 is geïnstalleerd of een systeem met PowerShell 6.

  ```powershell
  Install-Module –Name PowerShellGet –Force
  Exit
  ```

- Gebruik `Update-Module` om nieuwere versies.

  ```powershell
  Update-Module -Name PowerShellGet
  Exit
  ```

### <a name="for-systems-running-powershell-3-or-powershell-4-that-have-installed-the-packagemanagement-msihttpswwwmicrosoftcomdownloaddetailsaspxid51451"></a>Voor systemen waarop PowerShell 3 of PowerShell 4 wordt uitgevoerd, die beschikken over de [PackageManagement MSI](https://www.microsoft.com/download/details.aspx?id=51451)

- Gebruik de onderstaande PowerShellGet-cmdlet uit een PowerShell-sessie met verhoogde bevoegdheden om op te slaan van de modules naar een lokale map

  ```powershell
  Save-Module PowerShellGet -Path C:\LocalFolder
  Exit
  ```

- Zorg ervoor dat PowerShellGet en PackageManagement-modules niet worden geladen in de andere processen.
- Verwijderen van de inhoud van `$env:ProgramFiles\WindowsPowerShell\Modules\PowerShellGet\` en `$env:ProgramFiles\WindowsPowerShell\Modules\PackageManagement\` mappen.
- Open opnieuw het PS-Console met verhoogde bevoegdheden en voer de volgende opdrachten uit.

  ```powershell
  Copy-Item "C:\LocalFolder\PowerShellGet\*" "$env:ProgramFiles\WindowsPowerShell\Modules\PowerShellGet\" -Recurse -Force
  Copy-Item "C:\LocalFolder\PackageManagement\*" "$env:ProgramFiles\WindowsPowerShell\Modules\PackageManagement\" -Recurse -Force
  ```
