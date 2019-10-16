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
ms.openlocfilehash: 639d3a28dd2af09fcc498caedc5fe74c1493445d
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/15/2019
ms.locfileid: "72352883"
---
# <a name="modifying-the-psmodulepath-installation-path"></a>Het PSModulePath-installatiepad wijzigen

De omgevings variabele `PSModulePath` slaat de paden op naar de locaties van de modules die op schijf zijn geïnstalleerd. Windows Power shell gebruikt deze variabele om modules te zoeken wanneer de gebruiker niet het volledige pad naar een module opgeeft. De paden in deze variabele worden doorzocht in de volg orde waarin ze worden weer gegeven.

Als Windows Power shell wordt gestart, wordt `PSModulePath` gemaakt als een systeem omgevingsvariabele met de volgende standaard waarde: `$home\Documents\WindowsPowerShell\Modules; $pshome\Modules`.

## <a name="to-view-the-psmodulepath-variable"></a>De variabele PSModulePath weer geven

Als u de paden wilt weer geven die zijn opgegeven in de variabele `PSModulePath`, typt u de volgende opdracht:

`$env:PSModulePath`

## <a name="to-add-locations-to-the-psmodulepath-variable"></a>Locaties toevoegen aan de variabele PSModulePath

Gebruik een van de volgende methoden om paden aan deze variabele toe te voegen:

- Als u een tijdelijke waarde wilt toevoegen die alleen beschikbaar is voor de huidige sessie, voert u de volgende opdracht uit op de opdracht regel:

  `$env:PSModulePath = $env:PSModulePath + ";c:\ModulePath"`

- Als u een permanente waarde wilt toevoegen die beschikbaar is wanneer een sessie wordt geopend, voegt u de volgende opdracht toe aan een Windows Power shell-profiel:

  `$env:PSModulePath = $env:PSModulePath + ";c:\ModulePath"`

  Zie [about_Profiles](/powershell/module/microsoft.powershell.core/about/about_profiles) in de micro soft TechNet-bibliotheek voor meer informatie over profielen.

- Als u een permanente variabele wilt toevoegen aan het REGI ster, maakt u een nieuwe gebruikers omgevings variabele met de naam `PSModulePath` met behulp van de editor voor omgevings variabelen in het dialoog venster **systeem eigenschappen** .

- Als u een permanente variabele wilt toevoegen met behulp van een script, gebruikt u de methode **SetEnvironmentVariable** voor de omgevings klasse. Het volgende script voegt bijvoorbeeld het pad C:\Program Files\Fabrikam\Module toe aan de waarde van de PSModulePath-omgevings variabele voor de computer. Als u het pad wilt toevoegen aan de omgevings variabele gebruiker PSModulePath, stelt u het doel in op ' gebruiker '.

  ```powershell
  $CurrentValue = [Environment]::GetEnvironmentVariable("PSModulePath", "Machine")
  [Environment]::SetEnvironmentVariable("PSModulePath", $CurrentValue + ";C:\Program Files\Fabrikam\Modules", "Machine")

  ```

## <a name="to-remove-locations-from-the-psmodulepath"></a>Locaties verwijderen uit de PSModulePath

U kunt paden uit de variabele verwijderen met soort gelijke methoden: als u bijvoorbeeld `$env:PSModulePath = $env:PSModulePath -replace ";c:\\ModulePath"`, wordt het pad **c:\ModulePath** uit de huidige sessie verwijderd.

## <a name="see-also"></a>Zie ook

[Een Windows Power shell-module schrijven](./writing-a-windows-powershell-module.md)
