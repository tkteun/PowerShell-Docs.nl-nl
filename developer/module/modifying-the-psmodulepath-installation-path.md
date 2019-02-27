---
title: Het installatiepad PSModulePath wijzigen | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: dc5ce5a2-50e9-4c88-abf1-ac148a8a6b7b
caps.latest.revision: 15
ms.openlocfilehash: 639d3a28dd2af09fcc498caedc5fe74c1493445d
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 02/03/2019
ms.locfileid: "56846506"
---
# <a name="modifying-the-psmodulepath-installation-path"></a>Het PSModulePath-installatiepad wijzigen

De `PSModulePath` omgevingsvariabele de paden naar de locaties van de modules die zijn geïnstalleerd op de schijf worden opgeslagen. Windows PowerShell wordt deze variabele om te zoeken modules wanneer de gebruiker heeft niet het volledige pad naar een module opgeven. De paden in deze variabele wordt gezocht in de volgorde waarin ze worden weergegeven.

Wanneer Windows PowerShell wordt gestart, `PSModulePath` gemaakt als een systeem-omgevingsvariabele met de volgende standaardwaarde: `$home\Documents\WindowsPowerShell\Modules; $pshome\Modules`.

## <a name="to-view-the-psmodulepath-variable"></a>Om de variabele PSModulePath weer te geven

Om weer te geven van de paden die zijn opgegeven in de `PSModulePath` variabele, typt u de volgende opdracht:

`$env:PSModulePath`

## <a name="to-add-locations-to-the-psmodulepath-variable"></a>Locaties toevoegen aan de variabele PSModulePath

Paden naar deze variabele toevoegen, moet u een van de volgende methoden gebruiken:

- Als u wilt toevoegen een tijdelijke waarde die is alleen beschikbaar voor de huidige sessie, moet u de volgende opdracht uitvoeren op de opdrachtregel:

  `$env:PSModulePath = $env:PSModulePath + ";c:\ModulePath"`

- Als u wilt toevoegen een permanente waarde die beschikbaar is wanneer een sessie wordt geopend, toevoegen de volgende opdracht aan een Windows PowerShell-profiel:

  `$env:PSModulePath = $env:PSModulePath + ";c:\ModulePath"`

  Zie voor meer informatie over profielen [about_Profiles](/powershell/module/microsoft.powershell.core/about/about_profiles) in de Microsoft TechNet-bibliotheek.

- Als u wilt een permanente variabele toevoegen aan het register, maakt u een nieuwe omgevingsvariabele met de naam `PSModulePath` met behulp van de Editor van de variabelen voor de omgeving in de **Systeemeigenschappen** in het dialoogvenster.

- U kunt een permanente variabele toevoegen met behulp van een script met de **SetEnvironmentVariable** methode voor de klasse omgeving. Het volgende script wordt bijvoorbeeld toegevoegd voor het "C:\Program Files\Fabrikam\Module pad naar de waarde van de omgevingsvariabele PSModulePath voor de computer. Het pad toevoegen aan de omgevingsvariabele van de gebruiker PSModulePath, stelt u het doel 'Gebruiker'.

  ```powershell
  $CurrentValue = [Environment]::GetEnvironmentVariable("PSModulePath", "Machine")
  [Environment]::SetEnvironmentVariable("PSModulePath", $CurrentValue + ";C:\Program Files\Fabrikam\Modules", "Machine")

  ```

## <a name="to-remove-locations-from-the-psmodulepath"></a>Locaties van de PSModulePath verwijderen

Kunt u de paden van de variabele met behulp van vergelijkbare methoden verwijderen: bijvoorbeeld `$env:PSModulePath = $env:PSModulePath -replace ";c:\\ModulePath"` verwijdert de **c:\ModulePath** pad van de huidige sessie.

## <a name="see-also"></a>Zie ook

[Een Windows PowerShell-Module schrijven](./writing-a-windows-powershell-module.md)
