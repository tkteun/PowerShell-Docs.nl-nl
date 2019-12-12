---
title: Het installatiepad van PSModulePath wijzigen | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: dc5ce5a2-50e9-4c88-abf1-ac148a8a6b7b
caps.latest.revision: 15
ms.openlocfilehash: 5957ea4c15cd3778bd09b67c4b97de0ef0cfdd2a
ms.sourcegitcommit: 0e4c69d8b5cf71431592fe41da816dec9b70f1f9
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 12/09/2019
ms.locfileid: "74953837"
---
# <a name="modifying-the-psmodulepath-installation-path"></a>Het PSModulePath-installatiepad wijzigen

De variabele `PSModulePath` omgeving slaat de paden op naar de locaties van de modules die op schijf zijn geïnstalleerd. Power shell gebruikt deze variabele om modules te zoeken wanneer de gebruiker niet het volledige pad naar een module opgeeft. De paden in deze variabele worden doorzocht in de volg orde waarin ze worden weer gegeven.

Wanneer Power shell wordt gestart, wordt `PSModulePath` gemaakt als een systeem omgevingsvariabele met de volgende standaard waarde: `$HOME\Documents\PowerShell\Modules; $PSHOME\Modules` of `$HOME\Documents\WindowsPowerShell\Modules; $PSHOME\Modules` voor Windows Power shell.

## <a name="to-view-the-psmodulepath-variable"></a>De variabele PSModulePath weer geven

Als u de paden wilt weer geven die zijn opgegeven in de variabele `PSModulePath`, typt u de volgende opdracht:

`$env:PSModulePath`

## <a name="to-add-locations-to-the-psmodulepath-variable"></a>Locaties toevoegen aan de variabele PSModulePath

Gebruik een van de volgende methoden om paden aan deze variabele toe te voegen:

- Als u een tijdelijke waarde wilt toevoegen die alleen beschikbaar is voor de huidige sessie, voert u de volgende opdracht uit op de opdracht regel:

  `$env:PSModulePath = $env:PSModulePath + "$([System.IO.Path]::PathSeparator)$MyModulePath"`

- Als u een permanente waarde wilt toevoegen die beschikbaar is wanneer een sessie wordt geopend, voegt u de bovenstaande opdracht toe aan een Power shell-profiel bestand (`$PROFILE`) >

  Zie [about_Profiles](/powershell/module/microsoft.powershell.core/about/about_profiles)voor meer informatie over profielen.

- Als u een permanente variabele wilt toevoegen aan het REGI ster, maakt u een nieuwe gebruikers omgevings variabele met de naam `PSModulePath` met behulp van de editor voor omgevings variabelen in het dialoog venster **systeem eigenschappen** .

- Als u een permanente variabele wilt toevoegen met behulp van een script, gebruikt u de .net-methode [SetEnvironmentVariable](https://docs.microsoft.com/dotnet/api/system.environment.setenvironmentvariable) in de klasse [System. Environment](https://docs.microsoft.com/dotnet/api/system.environment) . Het volgende script voegt bijvoorbeeld het `C:\Program Files\Fabrikam\Module` pad toe aan de waarde van de omgevings variabele `PSModulePath` voor de computer. Als u het pad wilt toevoegen aan de gebruiker `PSModulePath` omgevings variabele, stelt u het doel in op ' gebruiker '.

  ```powershell
  $CurrentValue = [Environment]::GetEnvironmentVariable("PSModulePath", "Machine")
  [Environment]::SetEnvironmentVariable("PSModulePath", $CurrentValue + [System.IO.Path]::PathSeparator + "C:\Program Files\Fabrikam\Modules", "Machine")

  ```

## <a name="to-remove-locations-from-the-psmodulepath"></a>Locaties verwijderen uit de PSModulePath

U kunt paden uit de variabele verwijderen met soort gelijke methoden: `$env:PSModulePath = $env:PSModulePath -replace "$([System.IO.Path]::PathSeparator)c:\\ModulePath"` verwijdert bijvoorbeeld het pad **c:\ModulePath** uit de huidige sessie.

## <a name="see-also"></a>Zie ook

[Een Windows Power shell-module schrijven](./writing-a-windows-powershell-module.md)
