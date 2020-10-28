---
ms.date: 08/28/2019
ms.topic: reference
title: Cmdlets importeren met modules
description: Cmdlets importeren met modules
ms.openlocfilehash: 485a4be4d2accaf050a6536e7f92a0673f62a30b
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/27/2020
ms.locfileid: "92657290"
---
# <a name="how-to-import-cmdlets-using-modules"></a>Cmdlets importeren met modules

In dit artikel wordt beschreven hoe u cmdlets importeert in een Power shell-sessie met behulp van een binaire module.

> [!NOTE]
> De leden van modules kunnen cmdlets, providers, functies, variabelen, aliassen en nog veel meer bevatten. Modules kunnen alleen cmdlets en providers bevatten.

## <a name="how-to-load-cmdlets-using-a-module"></a>Cmdlets laden met behulp van een module

1. Maak een map met de naam van het assembly-bestand waarin de cmdlets worden geïmplementeerd. In deze procedure wordt de map module gemaakt in de map Windows `system32` .

   `%SystemRoot%\system32\WindowsPowerShell\v1.0\Modules\mymodule`

1. Zorg ervoor dat de `PSModulePath` omgevings variabele het pad naar de nieuwe module map bevat. Standaard wordt de systeemmap al toegevoegd aan de `PSModulePath` omgevings variabele. Als u wilt weer geven `PSModulePath` , typt u: `$env:PSModulePath` .

1. Kopieer de cmdlet-assembly naar de module map.

1. Voeg een module manifest bestand ( `.psd1` ) toe aan de hoofdmap van de module. Power shell gebruikt het module manifest om uw module te importeren. Zie [een Power shell-module manifest schrijven](../module/how-to-write-a-powershell-module-manifest.md)voor meer informatie.

1. Voer de volgende opdracht uit om de cmdlets toe te voegen aan de sessie:

   `Import-Module [Module_Name]`

   Deze procedure kan worden gebruikt om uw cmdlets te testen. Alle cmdlets in de assembly worden toegevoegd aan de sessie. Zie [een Windows Power shell-module schrijven](../module/writing-a-windows-powershell-module.md)voor meer informatie over modules.

## <a name="see-also"></a>Zie ook

[Een manifest voor een PowerShell-module schrijven](../module/how-to-write-a-powershell-module-manifest.md)

[Een PowerShell-module importeren](../module/importing-a-powershell-module.md)

[Import-module](/powershell/module/Microsoft.PowerShell.Core/Import-Module)

[Modules installeren](../module/installing-a-powershell-module.md)

[Het PSModulePath-installatiepad wijzigen](../module/modifying-the-psmodulepath-installation-path.md)

[Een Windows PowerShell-cmdlet schrijven](../cmdlet/cmdlet-overview.md)
