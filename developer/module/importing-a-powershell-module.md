---
title: Importeren van een PowerShell-Module | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 697791b3-2135-4a39-b9d7-8566ed67acf2
caps.latest.revision: 13
ms.openlocfilehash: bb5d036e5658c365a4fafa2cac05c0bba9f87019
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62082240"
---
# <a name="importing-a-powershell-module"></a>Een PowerShell-module importeren

Zodra uw een module hebt geïnstalleerd op een systeem, wilt u wellicht de module te importeren. Importeren is het proces dat wordt de module in het actieve geheugen geladen, zodat een gebruiker toegang heeft tot die module in de PowerShell-sessie. In PowerShell 2.0, kunt u met een aanroep naar een door de zojuist geïnstalleerde PowerShell-module importeren [Import-Module](/powershell/module/Microsoft.PowerShell.Core/Import-Module) cmdlet. PowerShell is PowerShell 3.0, kunnen impliciet een module importeren als een van de functies of cmdlets in de module wordt aangeroepen door een gebruiker. Houd er rekening mee dat beide versies wordt ervan uitgegaan dat u aan de module te installeren op een locatie waar PowerShell kunnen vinden. Zie voor meer informatie, [een PowerShell-Module installeren](./installing-a-powershell-module.md). U kunt een module-manifest gebruiken om te beperken welke onderdelen van de module worden geëxporteerd en kunt u parameters van de `Import-Module` aanroep om te beperken welke onderdelen worden geïmporteerd.

## <a name="importing-a-snap-in-powershell-10"></a>Importeren van een module (PowerShell 1.0)

Modules bestaat niet in PowerShell 1.0: in plaats daarvan, moest u te registreren en -modules gebruiken. Echter is het niet aanbevolen dat u deze technologie op dit moment modules zijn meestal gemakkelijker te installeren en te importeren. Zie voor meer informatie, [over het maken van een Windows PowerShell-Snap-in](../cmdlet/how-to-create-a-windows-powershell-snap-in.md).

## <a name="importing-a-module-with-import-module-powershell-20"></a>Importeren van een Module met de Import-Module (PowerShell 2.0)

PowerShell 2.0 maakt gebruik van de op de juiste wijze benoemde [Import-Module](/powershell/module/Microsoft.PowerShell.Core/Import-Module) cmdlet-modules importeren. Wanneer deze cmdlet wordt uitgevoerd, Windows PowerShell gezocht naar de opgegeven module binnen de mappen die zijn opgegeven de `PSModulePath` variabele. Als de opgegeven map wordt gevonden, Windows PowerShell wordt gezocht naar bestanden in de volgende volgorde: module-manifestbestanden (.psd1), een script module-bestanden (.psm1), binaire module-bestanden (.dll). Zie voor meer informatie over het mappen toevoegen aan de zoekopdracht [wijzigen van het installatiepad PSModulePath](./modifying-the-psmodulepath-installation-path.md). De volgende code wordt beschreven hoe u een module importeren:

```powershell
Import-Module myModule
```

Ervan uitgaande dat myModule bevond zich de `PSModulePath`, PowerShell myModule wilt laden in het actieve geheugen. Als myModule is niet bevindt op een `PSModulePath` pad, bericht kunt u nog steeds expliciet PowerShell waar u deze kunt vinden:

```powershell
Import-Module -Name C:\myRandomDirectory\myModule -Verbose
```

U kunt ook de - uitgebreide parameter om te bepalen wat buiten de module wordt geëxporteerd en wat wordt geïmporteerd in het actieve geheugen. Zowel invoer als uitvoer beperken wat wordt blootgesteld aan de gebruiker: het verschil is wie de zichtbaarheid. In principe worden uitvoer beheerd door de code in de module. Daarentegen invoer worden beheerd door de `Import-Module` aanroepen. Zie voor meer informatie, **beperken van de leden die zijn geïmporteerd**hieronder.

## <a name="implicitly-importing-a-module-powershell-30"></a>Impliciet importeren van een Module (PowerShell 3.0)

Vanaf Windows PowerShell 3.0 worden modules automatisch geïmporteerd wanneer een cmdlet of functie in de module wordt gebruikt in een opdracht. Deze functie werkt op alle modules in een map die deze in de waarde van opgenomen de **PSModulePath** omgevingsvariabele. Als u niet uw module op een geldig pad echter opslaat, kunt u nog steeds laden met behulp van de expliciete [Import-Module](/powershell/module/Microsoft.PowerShell.Core/Import-Module) optie, zoals hierboven beschreven.

Activeren van de volgende acties automatisch importeren van een module, ook wel bekend als '-module automatisch geladen."

- Met behulp van een cmdlet in de opdracht. Typ bijvoorbeeld `Get-ExecutionPolicy` importeert de Microsoft.PowerShell.Security-module met de `Get-ExecutionPolicy` cmdlet.

- Met behulp van de [Get-Command](/powershell/module/Microsoft.PowerShell.Core/Get-Command) cmdlet om op te halen van de opdracht.  Typ bijvoorbeeld `Get-Command Get-JobTrigger` importeert de **PSScheduledJob** module met de `Get-JobTrigger` cmdlet. Een `Get-Command` opdracht met jokertekens wordt beschouwd als detectie en wordt niet geactiveerd voor het importeren van een module.

- Met behulp van de [Get-Help](/powershell/module/Microsoft.PowerShell.Core/Get-Help) cmdlet om hulp te krijgen voor een cmdlet. Typ bijvoorbeeld `Get-Help Get-WinEvent` importeert de Microsoft.PowerShell.Diagnostics-module met de `Get-WinEvent` cmdlet.

Ter ondersteuning van automatische importeren van modules, de `Get-Command` cmdlet haalt alle cmdlets en -functies in alle geïnstalleerde modules, zelfs als de module is niet geïmporteerd in de sessie. Zie voor meer informatie het help-onderwerp voor de [Get-Command](/powershell/module/Microsoft.PowerShell.Core/Get-Command) cmdlet.

## <a name="the-importing-process"></a>Het importeren van proces

Wanneer een module is geïmporteerd, wordt de status van een nieuwe sessie gemaakt voor de module en een [System.Management.Automation.PSModuleInfo](/dotnet/api/System.Management.Automation.PSModuleInfo) object wordt gemaakt in het geheugen. Een sessiestatus is gemaakt voor elke module die is geïmporteerd (dit omvat de root-module en alle geneste modules). De leden die zijn geëxporteerd uit de basismodule, met inbegrip van alle leden die zijn geëxporteerd naar de hoofdmap-module door eventuele geneste modules worden vervolgens geïmporteerd in de sessiestatus van de oproepende functie.

De metagegevens van de leden die zijn geëxporteerd uit een module ModuleName eigenschap zijn. Deze eigenschap wordt gevuld met de naam van de module die ze geëxporteerd.

> [!WARNING]
> Als de naam van een geëxporteerde lid maakt gebruik van een niet-goedgekeurde bewerking of als de naam van het lid maakt gebruik van tekens, een waarschuwing wordt weergegeven wanneer de [Import-Module](/powershell/module/Microsoft.PowerShell.Core/Import-Module) cmdlet wordt uitgevoerd.

Standaard de [Import-Module](/powershell/module/Microsoft.PowerShell.Core/Import-Module) cmdlet retourneert geen objecten aan de pijplijn. De cmdlet ondersteunt echter een `PassThru` parameter die kan worden gebruikt om terug te keren een [System.Management.Automation.PSModuleInfo](/dotnet/api/System.Management.Automation.PSModuleInfo) -object voor elke module die is geïmporteerd. Voor het verzenden van uitvoer naar de host, gebruikers moeten worden uitgevoerd de [Write-Host](/powershell/module/Microsoft.PowerShell.Utility/Write-Host) cmdlet.

## <a name="restricting--the-members-that-are-imported"></a>Beperken van de leden die worden geïmporteerd

Wanneer een module wordt geïmporteerd met behulp van de [Import-Module](/powershell/module/Microsoft.PowerShell.Core/Import-Module) cmdlet standaard alle geëxporteerde module leden worden geïmporteerd in de sessie, met inbegrip van alle opdrachten worden geëxporteerd naar de module door een geneste module. Standaard, variabelen en aliassen niet worden geëxporteerd. Als u wilt voorkomen dat de leden die zijn geëxporteerd, gebruikt u een [module-manifest](./how-to-write-a-powershell-module-manifest.md). Als u wilt voorkomen dat de leden die worden geïmporteerd, gebruik de volgende parameters van de `Import-Module` cmdlet.

- `Function`: Deze parameter Hiermee beperkt u de functies die zijn geëxporteerd. (Als u een module-manifest gebruikt, raadpleegt u de sleutel FunctionsToExport.)

- `Cmdlet`: Deze parameter wordt beperkt de cmdlets die zijn geëxporteerd (als u een module-manifest, Zie de sleutel CmdletsToExport.)

- `Variable`: Deze parameter wordt beperkt de variabelen die zijn geëxporteerd (als u een module-manifest, Zie de sleutel VariablesToExport.)

- `Alias`: Deze parameter wordt beperkt de aliassen die zijn geëxporteerd (als u een module-manifest, Zie de sleutel AliasesToExport.)

## <a name="see-also"></a>Zie ook

[Een Windows PowerShell-Module schrijven](./writing-a-windows-powershell-module.md)
