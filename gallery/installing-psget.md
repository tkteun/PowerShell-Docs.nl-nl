---
ms.date: 06/12/2017
contributor: manikb
keywords: Galerie, Power shell, cmdlet, psget
title: PowerShellGet installeren
ms.openlocfilehash: a0ef46a9ee4bbf668a58067256d098967bde48c5
ms.sourcegitcommit: 0a6b562a497860caadba754c75a83215315d37a1
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 09/19/2019
ms.locfileid: "71143595"
---
# <a name="installing-powershellget"></a>PowerShellGet installeren

## <a name="powershellget-is-an-in-box-module-in-the-following-releases"></a>PowerShellGet is een in-box-module in de volgende releases

- [Windows 10](https://www.microsoft.com/windows) of hoger
- [Windows Server 2016](/windows-server/windows-server) of hoger
- [Windows Management Framework (WMF) 5,0](https://www.microsoft.com/download/details.aspx?id=50395) of hoger
- [Power shell 6](https://github.com/PowerShell/PowerShell/releases)

## <a name="get-the-latest-version-from-powershell-gallery"></a>De nieuwste versie van PowerShell Gallery ophalen

Voordat u **PowerShellGet**bijwerkt, moet u altijd de meest recente **NuGet** -provider installeren. Voer de volgende opdracht uit vanuit een Power shell-sessie met verhoogde bevoegdheden.

```powershell
Install-PackageProvider -Name NuGet -Force
Exit
```

### <a name="for-systems-with-powershell-50-or-newer-you-can-install-the-latest-powershellget"></a>Voor systemen met Power shell 5,0 (of hoger) kunt u de meest recente PowerShellGet installeren

Voer de volgende opdrachten uit vanuit een Power shell-sessie met verhoogde bevoegdheid om PowerShellGet te installeren op Windows 10, Windows Server 2016, een systeem met WMF 5,0 of 5,1 dat is geïnstalleerd of een systeem met Power shell 6.

```powershell
Install-Module -Name PowerShellGet -Force
Exit
```

Gebruiken `Update-Module` om nieuwere versies op te halen.

```powershell
Update-Module -Name PowerShellGet
Exit
```

### <a name="for-systems-running-powershell-3-or-powershell-4-that-have-installed-the-packagemanagement-preview"></a>Voor systemen met Power Shell 3 of Power Shell 4 waarop de Package Management-preview is geïnstalleerd

1. Gebruik `Save-Module` vanuit een Power shell-sessie met verhoogde bevoegdheid om de modules op te slaan in een lokale map.

   ```powershell
   Save-Module -Name PowerShellGet -Path C:\LocalFolder
   Exit
   ```

1. Zorg ervoor dat de **PowerShellGet** -en **Package Management** -modules niet zijn geladen in andere processen.
1. Verwijder de inhoud van de mappen: `$env:ProgramFiles\WindowsPowerShell\Modules\PowerShellGet\` en `$env:ProgramFiles\WindowsPowerShell\Modules\PackageManagement\`.
1. Open de Power shell-console opnieuw met verhoogde machtigingen en voer de volgende opdrachten uit.

   ```powershell
   Copy-Item "C:\LocalFolder\PowerShellGet\*" "$env:ProgramFiles\WindowsPowerShell\Modules\PowerShellGet\" -Recurse -Force
   Copy-Item "C:\LocalFolder\PackageManagement\*" "$env:ProgramFiles\WindowsPowerShell\Modules\PackageManagement\" -Recurse -Force
   ```
