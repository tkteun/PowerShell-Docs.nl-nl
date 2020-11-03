---
description: Functie
keywords: powershell,cmdlet
Locale: en-US
ms.date: 10/18/2018
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_function_provider?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Functie provider
ms.openlocfilehash: ac2f09c6352f936a0b0fece108e87e3fe15b5998
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/13/2020
ms.locfileid: "93252615"
---
# <a name="function-provider"></a>Functie provider

## <a name="provider-name"></a>Provider naam

Functie

## <a name="drives"></a>Aandrijfeenheden

`Function:`

## <a name="capabilities"></a>Functies

**ShouldProcess**

## <a name="short-description"></a>Korte beschrijving

Biedt toegang tot de functies die zijn gedefinieerd in Power shell.

## <a name="detailed-description"></a>Gedetailleerde beschrijving

Met de **functie** provider van Power shell kunt u de functies en filters in Power shell ophalen, toevoegen, wijzigen, wissen en verwijderen.

Een functie is een named code blok waarmee een actie wordt uitgevoerd. Wanneer u de naam van de functie typt, wordt de code in de functie uitgevoerd. Een filter is een benoemd code blok waarmee voor waarden voor een actie worden vastgelegd. U kunt de naam van het filter in plaats van de voor waarde typen, bijvoorbeeld in een `Where-Object` opdracht.

Het **functie** station is een platte naam ruimte die alleen de functie-en filter objecten bevat. Geen van de functies en filters hebben onderliggende items.

De **functie** provider ondersteunt de volgende cmdlets, die in dit artikel worden besproken.

- [Get-locatie](xref:Microsoft.PowerShell.Management.Get-Location)
- [Set-Location](xref:Microsoft.PowerShell.Management.Set-Location)
- [Get-item](xref:Microsoft.PowerShell.Management.Get-Item)
- [Nieuw-item](xref:Microsoft.PowerShell.Management.New-Item)
- [Verwijderen-item](xref:Microsoft.PowerShell.Management.Remove-Item)
- [Wissen-item](xref:Microsoft.PowerShell.Management.Clear-Item)

## <a name="types-exposed-by-this-provider"></a>Typen die door deze provider worden weer gegeven

Elke functie is een instantie van de klasse [System. Management. Automation. FunctionInfo](/dotnet/api/system.management.automation.functioninfo) . Elk filter is een instantie van de klasse [System. Management. Automation. FilterInfo](/dotnet/api/system.management.automation.filterinfo) .

## <a name="navigating-the-function-drive"></a>Navigeren door het functie station

De **functie** provider toont de gegevens opslag in het `Function:` station. Als u wilt werken met functions, kunt u uw locatie wijzigen in het `Function:` station ( `Set-Location Function:` ). U kunt ook een ander Power Shell-station gebruiken. Als u wilt verwijzen naar een functie vanaf een andere locatie, gebruikt u de naam van het station ( `Function:` ) in het pad.

```powershell
Set-Location Function:
```

Als u wilt terugkeren naar een bestandssysteem station, typt u de naam van het station. Typ bijvoorbeeld:

```powershell
Set-Location C:
```

U kunt ook met de **functie** provider werken vanuit elk ander Power Shell-station. Als u wilt verwijzen naar een functie vanaf een andere locatie, gebruikt u de naam van het station `Function:` in het pad.

> [!NOTE]
> In Power shell worden aliassen gebruikt om u een vertrouwde manier te bieden om met provider paden te werken. Opdrachten zoals `dir` en `ls` zijn nu aliassen voor [Get-Child item](xref:Microsoft.PowerShell.Management.Get-ChildItem), `cd` is een alias voor [Set-Location](xref:Microsoft.PowerShell.Management.Set-Location). en `pwd` is een alias voor [Get-location](xref:Microsoft.PowerShell.Management.Get-Location).

## <a name="getting-functions"></a>Functies ophalen

Met deze opdracht wordt de lijst met alle functies in de huidige sessie opgehaald. U kunt deze opdracht vanuit elk Power Shell-station gebruiken.

```powershell
Get-ChildItem -Path Function:
```

De functie provider heeft geen containers, dus de bovenstaande opdracht heeft hetzelfde effect als het wordt gebruikt in combi natie met `Get-ChildItem` .

```powershell
Get-ChildItem -Path Function:
```

U kunt de definitie van een functie ophalen door de eigenschap **definitie** te openen, zoals hieronder wordt weer gegeven.

```powershell
(Get-Item -Path function:more).Definition
```

U kunt ook de definitie van een functie ophalen met behulp van het pad naar de provider, voorafgegaan door het dollar teken ( `$` ).

```powershell
$function:more
```

### <a name="getting-selected-functions"></a>Geselecteerde functies ophalen

Met deze opdracht wordt de `man` functie van het `Function:` station opgehaald. De cmdlet wordt gebruikt `Get-Item` om de functie op te halen. De pijplijn operator ( `|` ) stuurt het resultaat naar `Format-Table` . De `-Wrap` para meter leidt tekst die niet op de regel past, naar de volgende regel. De `-Autosize` para meter verg root of verkleint de tabel kolommen om de tekst aan te passen.

```powershell
Get-Item -Path man | Format-Table -Wrap -Autosize
```

### <a name="working-with-function-provider-paths"></a>Werken met paden naar functie providers

Met deze opdrachten wordt de functie met de naam opgehaald `c:` . De eerste opdracht kan worden gebruikt in een wille keurige schijf. De tweede opdracht wordt gebruikt in het `Function:` station. Omdat de naam eindigt met een dubbele punt, wat de syntaxis voor een station is, moet u het pad kwalificeren met de naam van het station. Binnen het `Function:` station kunt u een van beide indelingen gebruiken. In de tweede opdracht vertegenwoordigt de punt ( `.` ) de huidige locatie.

```
PS C:\> Get-Item -Path Function:c:
PS Function:\> Get-Item -Path .\c:
```

## <a name="creating-a-function"></a>Een functie maken

Met deze opdracht wordt de `New-Item` cmdlet gebruikt voor het maken van een functie met de naam `Win32:` .
De expressie tussen accolades is het script blok dat wordt vertegenwoordigd door de functie naam.

```powershell
New-Item -Path Function:Win32: -Value {Set-Location C:\Windows\System32}
```

U kunt ook een functie maken door deze te typen op de Power shell-opdracht regel. Bijvoorbeeld TPE `Function:Win32: {Set-Location C:\Windows\System32}` . Als u zich in het station bevindt `Function:` , kunt u de naam van het station weglaten.

## <a name="deleting-a-function"></a>Een functie verwijderen

Met deze opdracht wordt de `more:` functie uit de huidige sessie verwijderd.

```powershell
Remove-Item Function:more:
```

## <a name="changing-a-function"></a>Een functie wijzigen

Met deze opdracht wordt de- `Set-Item` cmdlet `prompt` zo gewijzigd dat de tijd voor het pad wordt weer gegeven.

```powershell
Set-Item -Path Function:prompt -Value {
  'PS '+ (Get-Date -Format t) + " " + (Get-Location) + '> '
  }
```

### <a name="rename-a-function"></a>De naam van een functie wijzigen

Met deze opdracht wordt de `Rename-Item` cmdlet gebruikt om de naam van de `help` functie te wijzigen in `gh` .

```powershell
Rename-Item -Path Function:help -NewName gh
```

## <a name="copying-a-function"></a>Een functie kopiëren

Met deze opdracht `prompt` wordt de functie gekopieerd naar en wordt in `oldPrompt` feite een nieuwe naam gemaakt voor het script blok dat is gekoppeld aan de functie prompt.
U kunt dit gebruiken om de oorspronkelijke prompt functie op te slaan als u deze wilt wijzigen.
De eigenschap **Options** van de nieuwe functie heeft de waarde `None` . Als u de waarde van de eigenschap **Options** wilt wijzigen, gebruikt u `Set-Item` .

```powershell
Copy-Item -Path Function:prompt -Destination Function:oldPrompt
```

## <a name="dynamic-parameters"></a>Dynamische parameters

Dynamische para meters zijn cmdlet-para meters die worden toegevoegd door een Power shell-provider en zijn alleen beschikbaar wanneer de cmdlet wordt gebruikt in het station waarvoor de provider is ingeschakeld.

### <a name="options-systemmanagementautomationscopeditemoptions"></a>Opties < [System. Management. Automation. ScopedItemOptions] >

Bepaalt de waarde van de eigenschap **Options** van een functie.

- `None`: Geen opties. `None` is de standaardwaarde.
- `Constant`: De functie kan niet worden verwijderd en de eigenschappen kunnen niet worden gewijzigd. `Constant` is alleen beschikbaar wanneer u een functie maakt.
  U kunt de optie van een bestaande functie niet wijzigen in `Constant` .
- `Private`: De functie is alleen zichtbaar in het huidige bereik
- (niet in onderliggende bereiken).
- `ReadOnly`: De eigenschappen van de functie kunnen niet worden gewijzigd, behalve door gebruik te maken van de `-Force` para meter. U kunt gebruiken `Remove-Item` om de functie te verwijderen.
- `AllScope`: De functie wordt gekopieerd naar nieuwe bereiken die worden gemaakt.

### <a name="cmdlets-supported"></a>Ondersteunde cmdlets

- [Nieuw-item](xref:Microsoft.PowerShell.Management.New-Item)

- [Set-item](xref:Microsoft.PowerShell.Management.Set-Item)

## <a name="using-the-pipeline"></a>De pijp lijn gebruiken

Provider-cmdlets accepteren de invoer van de pijp lijn. U kunt de pijp lijn gebruiken om de taak te vereenvoudigen door provider gegevens van de ene cmdlet naar een andere provider-cmdlet te verzenden.
Zie de cmdlet-verwijzingen die in dit artikel worden vermeld voor meer informatie over het gebruik van de pijp lijn met provider-cmdlets.

## <a name="getting-help"></a>Ondersteuning vragen

Vanaf Windows Power Shell 3,0 kunt u aangepaste Help-onderwerpen voor provider-cmdlets krijgen waarin wordt uitgelegd hoe deze cmdlets zich gedragen in een bestandssysteem station.

Als u de Help-onderwerpen wilt ophalen die zijn aangepast voor het bestandssysteem station, voert u de opdracht [Get-Help](xref:Microsoft.PowerShell.Core.Get-Help) uit in een bestandssysteem station of gebruikt `-Path` u de para meter [Get-Help](xref:Microsoft.PowerShell.Core.Get-Help) om een bestandssysteem station op te geven.

```powershell
Get-Help Get-ChildItem
```

```powershell
Get-Help Get-ChildItem -Path function:
```

## <a name="see-also"></a>Zie ook

[about_Functions](../About/about_Functions.md)

[about_Providers](../About/about_Providers.md)
