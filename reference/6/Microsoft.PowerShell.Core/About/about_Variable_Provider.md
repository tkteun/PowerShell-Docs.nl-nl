---
description: Variabele
keywords: powershell,cmdlet
Locale: en-US
ms.date: 10/18/2018
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_variable_provider?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Variabele provider
ms.openlocfilehash: c58ec641db0902088bf931d8bf4a48f5f7fa2ab8
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/13/2020
ms.locfileid: "93252193"
---
# <a name="variable-provider"></a>Variabele provider

## <a name="provider-name"></a>Provider naam
Variabele

## <a name="drives"></a>Aandrijfeenheden

`Variable:`

## <a name="capabilities"></a>Functies

**ShouldProcess**

## <a name="short-description"></a>Korte beschrijving

Biedt toegang tot de Power shell-variabelen en de waarden ervan.

## <a name="detailed-description"></a>Gedetailleerde beschrijving

Met de provider van de Power shell- **variabele** kunt u Power shell-variabelen in de huidige console ophalen, toevoegen, wijzigen, wissen en verwijderen.

De provider van de Power shell- **variabele** ondersteunt de variabelen die Power Shell maakt, met inbegrip van de automatische variabelen, de voorkeurs variabelen en de variabelen die u maakt.

Het **variabele** station is een platte naam ruimte die alleen de variabele-objecten bevat. De variabelen hebben geen onderliggende items.

De **variabelen** provider ondersteunt de volgende cmdlets, die in dit artikel worden besproken.

- [Get-locatie](xref:Microsoft.PowerShell.Management.Get-Location)
- [Set-Location](xref:Microsoft.PowerShell.Management.Set-Location)
- [Get-item](xref:Microsoft.PowerShell.Management.Get-Item)
- [Nieuw-item](xref:Microsoft.PowerShell.Management.New-Item)
- [Verwijderen-item](xref:Microsoft.PowerShell.Management.Remove-Item)
- [Wissen-item](xref:Microsoft.PowerShell.Management.Clear-Item)

Power shell bevat ook een set cmdlets die speciaal zijn ontworpen voor het weer geven en wijzigen van variabelen. Wanneer u **variabelen** -cmdlets gebruikt, hoeft u het station niet op te geven `Variable:` in de naam. Dit artikel is niet van belang voor het werken met **variabele** cmdlets.

- [Get-variabele](xref:Microsoft.PowerShell.Utility.Get-Variable)
- [Nieuwe variabele](xref:Microsoft.PowerShell.Utility.New-Variable)
- [Set-variabele](xref:Microsoft.PowerShell.Utility.Set-Variable)
- [Remove-variabele](xref:Microsoft.PowerShell.Utility.Remove-Variable)
- [Clear-variabele](xref:Microsoft.PowerShell.Utility.Clear-Variable)

> [!NOTE]
> U kunt ook de Power shell-expressie-parser gebruiken om de waarden van variabelen te maken, weer te geven en te wijzigen zonder de-cmdlets te gebruiken. Wanneer u rechtstreeks met variabelen werkt, gebruikt u een dollar teken ( `$` ) om de naam te identificeren als een variabele en de toewijzings operator ( `=` ) om de waarde te bepalen en te wijzigen. `$p = Get-Process`De variabele wordt bijvoorbeeld gemaakt `p` en de resultaten van een opdracht worden opgeslagen `Get-Process` .

## <a name="types-exposed-by-this-provider"></a>Typen die door deze provider worden weer gegeven

Variabelen kunnen een van de verschillende typen zijn. De meeste variabelen zijn exemplaren van de `PSVariable` klasse. Andere variabelen en hun typen worden hieronder weer gegeven.

- De `?` variabele is een exemplaar van de `QuestionMarkVariable` klasse.
- De `null` variabele is een exemplaar van de `NullVariable` klasse.
- De variabelen voor het maximum aantal zijn exemplaren van de `SessionStateCapacityVariable` klasse.
- `LocalVariable` instanties bevatten informatie over de huidige uitvoering, zoals:
  - `MyInvocation`
  - `PSCommandPath`
  - `PSScriptRoot`
  - `PSBoundParameters`
  - `args`
  - `input`

## <a name="navigating-the-variable-drives"></a>Navigeren door de variabele stations

De provider van de **variabele** geeft het gegevens archief van het `Variable:` station beschikbaar. Als u met variabelen wilt werken, kunt u uw locatie wijzigen in het `Variable:` station ( `Set-Location Variable:` ) of u kunt werken vanuit elk ander Power Shell-station. Als u wilt verwijzen naar een variabele van een andere locatie, gebruikt u de station naam ( `Variable:` ) in het pad.

```powershell
Set-Location Variable:
```

Als u wilt terugkeren naar een bestandssysteem station, typt u de naam van het station. Typ bijvoorbeeld:

```powershell
Set-Location C:
```

U kunt ook met de **variabelen** provider werken vanuit elk ander Power Shell-station. Als u wilt verwijzen naar een variabele van een andere locatie, gebruikt u de naam van het station `Variable:` in het pad.

> [!NOTE]
> In Power shell worden aliassen gebruikt om u een vertrouwde manier te bieden om met provider paden te werken. Opdrachten zoals `dir` en `ls` zijn nu aliassen voor [Get-Child item](xref:Microsoft.PowerShell.Management.Get-ChildItem), `cd` is een alias voor [Set-Location](xref:Microsoft.PowerShell.Management.Set-Location). en `pwd` is een alias voor [Get-location](xref:Microsoft.PowerShell.Management.Get-Location).

## <a name="displaying-the-value-of-variables"></a>De waarde van variabelen weer geven

### <a name="get-all-variables-in-the-current-session"></a>Alle variabelen ophalen in de huidige sessie

Met deze opdracht wordt de lijst met alle variabelen en hun waarden in de huidige sessie opgehaald. U kunt deze opdracht vanuit elk Power Shell-station gebruiken.

```powershell
Get-ChildItem -Path Variable:
```

### <a name="get-a-variable-using-its-provider-path"></a>Een variabele ophalen met behulp van het pad van de provider

Met deze opdracht wordt een variabelen waarde opgehaald met behulp van het pad van de provider, voorafgegaan door het dollar teken ( `$` ). Dit heeft hetzelfde effect als het voor voegsel van de variabelen naam met het dollar teken ( `$` ).

```powershell
$variable:home
```

### <a name="get-variables-using-wildcards"></a>Variabelen ophalen met behulp van joker tekens

Met deze opdracht worden de variabelen opgehaald met een naam die begint met "Max". U kunt deze opdracht vanuit elk Power Shell-station gebruiken.

```powershell
Get-ChildItem -Path Variable:max*
```

### <a name="get-the-value-of-the--variable"></a>Haal de waarde van de? variabeletype

Met deze opdracht wordt de `-LiteralPath` para meter [Get-Child item](xref:Microsoft.PowerShell.Management.Get-ChildItem) gebruikt om de waarde van de `?` variabele in het station op te halen `Variable:` . Het `?` is een Joker teken in paden, maar `Get-ChildItem` probeert geen joker tekens op te lossen in de waarden van `-LiteralPath` de para meter.

```powershell
Get-ChildItem -Literalpath ?
```

### <a name="get-readonly-and-constant-variables"></a>Alleen-lezen en constante variabelen ophalen

Met deze opdracht worden de variabelen opgehaald die de waarden van `ReadOnly` of `Constant` voor de eigenschap **Options** hebben.

```powershell
Get-ChildItem -Path Variable: | Where-Object {
   $_.options -Match "Constant" `
   -or $_.options -Match "ReadOnly"
 } | Format-List -Property name, value, options
```

## <a name="creating-variables"></a>Variabelen maken

### <a name="create-a-new-variable"></a>Een nieuwe variabele maken

Met deze opdracht wordt de `services` variabele gemaakt en worden de resultaten van een `Get-Service` opdracht erin opgeslagen. Omdat de huidige locatie zich in het station bevindt `Variable:` , is de waarde van de `-Path` para meter een punt ( `.` ), die de huidige locatie vertegenwoordigt.

De haakjes rond de `Get-Service` opdracht zorgen ervoor dat de opdracht wordt uitgevoerd voordat de variabele wordt gemaakt. Zonder haakjes is de waarde van de nieuwe variabele een ' Get-service ' teken reeks.

```powershell
New-Item -Path . -Name services -Value (Get-Service)
```

### <a name="create-a-variable-using-an-absolute-path"></a>Een variabele maken met een absoluut pad

Met deze opdracht wordt een `services` variabele gemaakt en wordt het resultaat van een `Get-Service` opdracht erin opgeslagen.

```powershell
New-Item -Path Variable:services -Value Get-Service
```

 Als u een variabele zonder waarde wilt maken, laat u de toewijzings operator weg.

## <a name="changing-variables"></a>Variabelen wijzigen

### <a name="rename-a-variable"></a>De naam van een variabele wijzigen

Met deze opdracht wordt de `Rename-Item` cmdlet gebruikt om de naam van de `a` variabele te wijzigen in `processes` .

```powershell
Rename-Item -Path Variable:a -NewName processes
```

### <a name="change-the-value-of-a-variable"></a>De waarde van een variabele wijzigen

Met deze opdracht wordt de `Set-Item` cmdlet gebruikt om de waarde van de `ErrorActionPreference` variabele te wijzigen in ' Stop '.

```powershell
Set-Item -Path Variable:ErrorActionPreference -Value Stop
```

## <a name="copy-a-variable"></a>Een variabele kopiëren

Met deze opdracht wordt de- `Copy-Item` cmdlet gebruikt om de `processes` variabele naar te kopiëren `old_processes` . Hiermee maakt u een nieuwe variabele `old_processes` met de naam die dezelfde waarde heeft als de `processes` variabele.

```powershell
Copy-Item -Path Variable:processes -Destination Variable:old_processes
```

## <a name="delete-a-variable"></a>Een variabele verwijderen

Met deze opdracht wordt de `serv` variabele uit de huidige sessie verwijderd. U kunt deze opdracht in elk Power Shell-station gebruiken.

```powershell
Remove-Variable -Path Variable:serv
```

### <a name="delete-variables-using-the--force-parameter"></a>Variabelen verwijderen met de para meter-Force

Met deze opdracht worden alle variabelen uit de huidige sessie verwijderd, met uitzonde ring van de variabelen waarvan de eigenschap **Options** de waarde `Constant` . Zonder de `-Force` para meter verwijdert de opdracht geen variabelen waarvan de eigenschap **Options** de waarde `ReadOnly` .

```powershell
Remove-Item Variable:* -Force
```

## <a name="setting-the-value-of-a-variable-to-null"></a>De waarde van een variabele instellen op NULL

Met deze opdracht wordt de `Clear-Item` cmdlet gebruikt om de waarde van de `processes` variabele te wijzigen in null.

```powershell
Clear-Item -Path Variable:processes
```

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
Get-Help Get-ChildItem -Path variable:
```

## <a name="see-also"></a>Zie ook

[about_Variables](../About/about_Variables.md)

[about_Automatic_Variables](../About/about_Automatic_Variables.md)

[about_Providers](../About/about_Providers.md)
