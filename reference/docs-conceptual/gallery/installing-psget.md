---
ms.date: 09/19/2019
contributor: manikb
keywords: Galerie, Power shell, cmdlet, psget
title: PowerShellGet installeren
ms.openlocfilehash: 4a10699be9ff2b64e5848c6749bdd3dedf55e3c7
ms.sourcegitcommit: f05f18154913d346012527c23020d48d87ccac74
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 08/13/2020
ms.locfileid: "88162508"
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
```

### <a name="for-systems-with-powershell-50-or-newer-you-can-install-the-latest-powershellget"></a>Voor systemen met Power shell 5,0 (of hoger) kunt u de meest recente PowerShellGet installeren

Voer de volgende opdrachten uit vanuit een Power shell-sessie met verhoogde bevoegdheid om PowerShellGet te installeren op Windows 10, Windows Server 2016, een systeem met WMF 5,0 of 5,1 dat is geïnstalleerd of een systeem met Power shell 6.

```powershell
Install-Module -Name PowerShellGet -Force
```

Gebruiken `Update-Module` om nieuwere versies op te halen.

```powershell
Update-Module -Name PowerShellGet
Exit
```

### <a name="for-computers-running-powershell-30-or-powershell-40"></a>Voor computers met Power Shell 3,0 of Power Shell 4,0

Deze instructies zijn van toepassing op computers waarop de **Package Management-preview** is geïnstalleerd of waarvoor geen versie van **PowerShellGet** is geïnstalleerd.

De `Save-Module` cmdlet wordt gebruikt in beide sets instructies. `Save-Module` Hiermee worden een module en eventuele afhankelijkheden uit een geregistreerde opslag plaats gedownload en opgeslagen. De meest recente versie van de module wordt opgeslagen op een opgegeven pad op de lokale computer, maar is niet geïnstalleerd. Als u de modules in Power Shell 3,0 of 4,0 wilt installeren, kopieert u de mappen in de module opgeslagen naar `$env:ProgramFiles\WindowsPowerShell\Modules` .

Zie [Save-module](/powershell/module/PowershellGet/Save-Module)voor meer informatie.

> [!NOTE]
> Power Shell 3,0 en Power Shell 4,0 ondersteunen slechts één versie van een module. Vanaf Power shell 5,0 worden modules geïnstalleerd in `<modulename>\<version>` . Zo kunt u meerdere versies naast elkaar installeren. Nadat u de module hebt gedownload met behulp `Save-Module` van, moet u de bestanden kopiëren van de `<modulename>\<version>` naar de `<modulename>` map op de doel computer, zoals wordt weer gegeven in de onderstaande instructies.

#### <a name="preparatory-step-on-computers-running-powershell-30"></a>Voorbereidende stap op computers met Power Shell 3,0

Met de instructies in de volgende secties worden de modules in Directory geïnstalleerd `$env:ProgramFiles\WindowsPowerShell\Modules` .
In Power Shell 3,0 wordt deze map niet `$env:PSModulePath` standaard vermeld, dus moet u deze toevoegen om de modules automatisch te laden. 

Open een Power shell-sessie met verhoogde bevoegdheden en voer de volgende opdracht uit (die wordt toegepast tijdens toekomstige sessies):

```powershell
[Environment]::SetEnvironmentVariable(
  'PSModulePath',
  ((([Environment]::GetEnvironmentVariable('PSModulePath', 'Machine') -split ';') + "$env:ProgramFiles\WindowsPowerShell\Modules") -join ';'),
  'Machine'
)
```

#### <a name="computers-with-the-packagemanagement-preview-installed"></a>Computers waarop het package management-voor beeld is geïnstalleerd

> [!NOTE] 
> De preview-versie van Package Management is een downloadbaar onderdeel dat PowerShellGet beschikbaar maakte voor Power shell-versie 3 en 4, maar niet langer beschikbaar is.
> Voer uit om te testen of het op een bepaalde computer is geïnstalleerd `Get-Module -ListAvailable PowerShellGet` .

1. Gebruik vanuit een Power shell-sessie `Save-Module` om de huidige versie van **PowerShellGet**te downloaden. Er worden twee mappen gedownload: **PowerShellGet** en **Package Management**. Elke map bevat een submap met een versie nummer.

   ```powershell
   Save-Module -Name PowerShellGet -Path C:\LocalFolder -Repository PSGallery
   ```

1. Zorg ervoor dat de **PowerShellGet** -en **Package Management** -modules niet zijn geladen in andere processen.

1. Open de Power shell-console opnieuw met verhoogde machtigingen en voer de volgende opdracht uit.

   ```powershell
   'PowerShellGet', 'PackageManagement' | % { 
     $targetDir = "$env:ProgramFiles\WindowsPowerShell\Modules\$_"
     Remove-Item $targetDir\* -Recurse -Force
     Copy-Item C:\LocalFolder\$_\*\* $targetDir\ -Recurse -Force
   }
   ```

#### <a name="computers-without-powershellget"></a>Computers zonder PowerShellGet

Voor computers waarop geen versie van **PowerShellGet** is geïnstalleerd (testen met `Get-Module -ListAvailable PowerShellGet` ), is een computer met **PowerShellGet** geïnstalleerd nodig om de modules te downloaden.

1. Op de computer waarop **PowerShellGet** is geïnstalleerd, gebruikt `Save-Module` u om de huidige versie van **PowerShellGet**te downloaden. Er worden twee mappen gedownload: **PowerShellGet** en **Package Management**. Elke map bevat een submap met een versie nummer.

   ```powershell
   Save-Module -Name PowerShellGet -Path C:\LocalFolder -Repository PSGallery
   ```

1. Kopieer de desbetreffende `<version>` submap in de **PowerShellGet** -en **Package Management** -mappen naar de computer waarop geen **PowerShellGet** is geïnstalleerd, naar mappen `$env:ProgramFiles\WindowsPowerShell\Modules\PowerShellGet\` en `$env:ProgramFiles\WindowsPowerShell\Modules\PackageManagement\` een verhoogde sessie.
   
1. Als u bijvoorbeeld toegang hebt tot de downloadmap op de andere computer, zegt u `ws1` , vanaf de doel computer via een UNC-pad, `\\ws1\C$\LocalFolder` een Power shell-console openen met verhoogde machtigingen en voert u de volgende opdracht uit:

   ```powershell
   'PowerShellGet', 'PackageManagement' | % {
     $targetDir = "$env:ProgramFiles\WindowsPowerShell\Modules\$_"
     $null = New-Item -Type Directory -Force $targetDir
     $fromComputer = 'ws1'  # Specify the name of the other computer here.
     Copy-Item \\$fromComputer\C$\LocalFolder\$_\*\* $targetDir -Recurse -Force
     if (-not (Get-ChildItem $targetDir)) { Throw "Copying failed." }
   }
   ```
