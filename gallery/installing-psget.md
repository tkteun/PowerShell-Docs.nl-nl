---
ms.date: 06/12/2017
contributor: manikb
keywords: Galerie, Power shell, cmdlet, psget
title: PowerShellGet installeren
ms.openlocfilehash: 2d3ba8c4d4d4c7ee023c7e6a948a29d8f47ea242
ms.sourcegitcommit: 8d47eb41445ffaf10fcd68874e397c9a1703d898
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/29/2019
ms.locfileid: "68601418"
---
# <a name="installing-powershellget"></a>PowerShellGet installeren

## <a name="powershellget-is-an-in-box-module-in-the-following-releases"></a>PowerShellGet is een in-box-module in de volgende releases

- [Windows 10](https://www.microsoft.com/windows) of hoger
- [Windows Server 2016](/windows-server/windows-server) of hoger
- [Windows Management Framework (WMF) 5,0](https://www.microsoft.com/download/details.aspx?id=50395) of hoger
- [Power shell 6](https://github.com/PowerShell/PowerShell/releases)

## <a name="get-powershellget-module-for-powershell-versions-30-and-40"></a>De PowerShellGet-module ophalen voor de Power shell-versie 3,0 en 4,0

- [Package Management MSI](https://www.microsoft.com/download/details.aspx?id=51451)

## <a name="get-the-latest-version-from-powershell-gallery"></a>De nieuwste versie van PowerShell Gallery ophalen

- Voordat u PowerShellGet bijwerkt, moet u altijd de meest recente Nuget-provider installeren. Voer hiertoe de volgende opdracht uit in een Power shell-sessie met verhoogde bevoegdheden.

  ```powershell
  Install-PackageProvider Nuget -Force
  Exit
  ```

### <a name="for-systems-with-powershell-50-or-newer-you-can-install-the-latest-powershellget"></a>Voor systemen met Power shell 5,0 (of hoger) kunt u de meest recente PowerShellGet installeren

- Hiervoor voert u de volgende opdrachten uit vanuit een Power shell-sessie met verhoogde bevoegdheden voor Windows 10, Windows Server 2016, een systeem met WMF 5,0 of 5,1 dat is geïnstalleerd of een systeem met Power shell 6.

  ```powershell
  Install-Module -Name PowerShellGet -Force
  Exit
  ```

- Gebruiken `Update-Module` om nieuwere versies op te halen.

  ```powershell
  Update-Module -Name PowerShellGet
  Exit
  ```

### <a name="for-systems-running-powershell-3-or-powershell-4-that-have-installed-the-packagemanagement-msihttpswwwmicrosoftcomdownloaddetailsaspxid51451"></a>Voor systemen met Power Shell 3 of Power Shell 4 waarop de [Package Management MSI](https://www.microsoft.com/download/details.aspx?id=51451) is geïnstalleerd

- Gebruik de onderstaande PowerShellGet-cmdlet van een Power shell-sessie met verhoogde bevoegdheid om de modules op te slaan in een lokale map

  ```powershell
  Save-Module PowerShellGet -Path C:\LocalFolder
  Exit
  ```

- Zorg ervoor dat de PowerShellGet-en package management-modules niet worden geladen in andere processen.
- Inhoud van `$env:ProgramFiles\WindowsPowerShell\Modules\PowerShellGet\` en `$env:ProgramFiles\WindowsPowerShell\Modules\PackageManagement\` mappen verwijderen.
- Open de PS-console opnieuw met verhoogde machtigingen en voer de volgende opdrachten uit.

  ```powershell
  Copy-Item "C:\LocalFolder\PowerShellGet\*" "$env:ProgramFiles\WindowsPowerShell\Modules\PowerShellGet\" -Recurse -Force
  Copy-Item "C:\LocalFolder\PackageManagement\*" "$env:ProgramFiles\WindowsPowerShell\Modules\PackageManagement\" -Recurse -Force
  ```
