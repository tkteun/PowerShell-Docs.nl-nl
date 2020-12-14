---
description: Beschrijft het kenmerk dat ervoor zorgt dat een functie werkt zoals een gecompileerde cmdlet.
Locale: en-US
ms.date: 06/11/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_functions_cmdletbindingattribute?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Functions_CmdletBindingAttribute
ms.openlocfilehash: f1463bafc462ae2a266f5b1f6f4d71e3422f5831
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 11/17/2020
ms.locfileid: "94706101"
---
# <a name="about-functions-cmdletbindingattribute"></a>Over functies CmdletBindingAttribute

## <a name="short-description"></a>Korte beschrijving
Beschrijft het kenmerk dat ervoor zorgt dat een functie werkt zoals een gecompileerde cmdlet.

## <a name="long-description"></a>Lange beschrijving

Het `CmdletBinding` kenmerk is een kenmerk van functies waarmee ze kunnen worden uitgevoerd zoals gecompileerde cmdlets die zijn geschreven in C#. Het biedt toegang tot de functies van cmdlets.

Power shell bindt de para meters van functies die het `CmdletBinding` kenmerk hebben op dezelfde manier als de para meters van gecompileerde cmdlets. De `$PSCmdlet` Automatische variabele is beschikbaar voor functies met het `CmdletBinding` kenmerk, maar de `$Args` variabele is niet beschikbaar.

In functies met het `CmdletBinding` kenmerk, onbekende para meters en positionele argumenten die geen overeenkomende positionele para meters hebben, kan de parameter binding mislukken.

> [!NOTE]
> Gecompileerde cmdlets gebruiken het vereiste `Cmdlet` kenmerk, dat vergelijkbaar is met het `CmdletBinding` kenmerk dat in dit onderwerp wordt beschreven.

## <a name="syntax"></a>Syntax

In het volgende voor beeld ziet u de indeling van een functie die alle optionele argumenten van het `CmdletBinding` kenmerk bevat. In dit voor beeld wordt een korte beschrijving van elk argument gevolgd.

```powershell
{
    [CmdletBinding(ConfirmImpact=<String>,
    DefaultParameterSetName=<String>,
    HelpURI=<URI>,
    SupportsPaging=<Boolean>,
    SupportsShouldProcess=<Boolean>,
    PositionalBinding=<Boolean>)]

    Param ($Parameter1)
    Begin{}
    Process{}
    End{}
}
```

## <a name="confirmimpact"></a>ConfirmImpact

Het argument **ConfirmImpact** geeft aan wanneer de actie van de functie moet worden bevestigd door een aanroep van de methode **ShouldProcess** . De aanroep van de methode **ShouldProcess** geeft alleen een bevestigings prompt weer wanneer het argument **ConfirmImpact** gelijk is aan of groter is dan de waarde van de `$ConfirmPreference` Voorkeurs variabele. (De standaard waarde van het argument is **gemiddeld**.) Geef dit argument alleen op als het argument **SupportsShouldProcess** ook is opgegeven.

Zie [bevestiging aanvragen](/powershell/scripting/developer/cmdlet/requesting-confirmation)voor meer informatie over bevestigings aanvragen.

## <a name="defaultparametersetname"></a>DefaultParameterSetName

Het argument **DefaultParameterSetName** geeft de naam van de parameterset op die Power shell probeert te gebruiken, wanneer niet kan worden bepaald welke para meter moet worden gebruikt. U kunt dit probleem vermijden door de unieke para meter van elke para meter in te stellen op een verplichte para meter.

## <a name="helpuri"></a>HelpURI

Met het argument **HelpURI** geeft u het Internet adres op van de online versie van het Help-onderwerp waarin de functie wordt beschreven. De waarde van het argument **HelpURI** moet beginnen met http of https.

De waarde van het argument **HelpURI** wordt gebruikt voor de waarde van de eigenschap **HelpURI** van het object **CommandInfo** dat `Get-Command` retourneert voor de functie.

Als er echter Help-bestanden op de computer zijn geïnstalleerd en de waarde van de eerste koppeling in de sectie **RelatedLinks** van het Help-bestand een URI is, of als de waarde van de eerste `.Link` instructie in op opmerkingen gebaseerde Help een URI is, wordt de URI in het Help-bestand gebruikt als waarde van de eigenschap **HelpUri** van de functie.

De `Get-Help` cmdlet gebruikt de waarde van de eigenschap **HelpURI** om de online versie van het Help-onderwerp van de functie op te sporen wanneer de para meter **online** van `Get-Help` is opgegeven in een opdracht.

## <a name="supportspaging"></a>SupportsPaging

Het argument **SupportsPaging** voegt de para meters **voor de eerste**, **Skip** en **IncludeTotalCount** toe aan de functie. Met deze para meters kunnen gebruikers uitvoer selecteren uit een zeer grote resultatenset. Dit argument is ontworpen voor cmdlets en functies die gegevens retour neren uit grote gegevens archieven die ondersteuning bieden voor gegevens selectie, zoals een SQL database.

Dit argument is geïntroduceerd in Windows Power Shell 3,0.

- **First**: alleen de eerste n-objecten worden opgehaald.
- **Overs Laan**: de eerste n-objecten worden genegeerd en vervolgens worden de resterende objecten opgehaald.
- **IncludeTotalCount**: rapporteert het aantal objecten in de gegevensset (een geheel getal), gevolgd door de objecten. Als het totale aantal niet kan worden vastgesteld met de cmdlet, wordt ' onbekend totaal aantal ' geretourneerd.

Power shell bevat **NewTotalCount**, een hulp methode waarmee de totale waarde voor aantal te retour neren wordt opgehaald en een schatting wordt opgenomen van de nauw keurigheid van de totale waarde voor Count.

De volgende voorbeeld functie laat zien hoe u ondersteuning voor de paginerings parameters toevoegt aan een geavanceerde functie.

```powershell
function Get-Numbers {
    [CmdletBinding(SupportsPaging = $true)]
    param()

    $FirstNumber = [Math]::Min($PSCmdlet.PagingParameters.Skip, 100)
    $LastNumber = [Math]::Min($PSCmdlet.PagingParameters.First +
      $FirstNumber - 1, 100)

    if ($PSCmdlet.PagingParameters.IncludeTotalCount) {
        $TotalCountAccuracy = 1.0
        $TotalCount = $PSCmdlet.PagingParameters.NewTotalCount(100,
          $TotalCountAccuracy)
        Write-Output $TotalCount
    }
    $FirstNumber .. $LastNumber | Write-Output
}
```

## <a name="supportsshouldprocess"></a>SupportsShouldProcess

Het argument **SupportsShouldProcess** voegt de para meters **confirm** en **WhatIf** toe aan de functie. De para meter **confirm** vraagt de gebruiker voordat de opdracht wordt uitgevoerd op elk object in de pijp lijn. De para meter **WhatIf** geeft een lijst van de wijzigingen die door de opdracht zouden worden aangebracht, in plaats van de opdracht uit te voeren.

## <a name="positionalbinding"></a>PositionalBinding

Het argument **PositionalBinding** bepaalt of para meters in de functie standaard positioneel zijn. De standaardwaarde is `$True`. U kunt het argument **PositionalBinding** gebruiken met de waarde `$False` om positie binding uit te scha kelen.

Het argument **PositionalBinding** is geïntroduceerd in Windows power Shell 3,0.

Wanneer para meters positioneel zijn, is de parameter naam optioneel.
Power shell koppelt geen naam parameter waarden met de functie parameters volgens de volg orde of positie van de niet-genaamde parameter waarden in de functie opdracht.

Wanneer para meters niet positioneel zijn (deze zijn ' naam '), is de parameter naam (of een afkorting of alias van de naam) vereist in de opdracht.

Wanneer **PositionalBinding** is `$True` , zijn functie parameters standaard positioneel. Power shell wijst positie nummer toe aan de para meters in de volg orde waarin ze worden gedeclareerd in de functie.

Wanneer **PositionalBinding** is `$False` , zijn functie parameters standaard niet positioneel. Tenzij het **positie** argument van het **parameter** kenmerk is gedeclareerd voor de para meter, moet de parameter naam (of een alias of afkorting) worden opgenomen wanneer de para meter wordt gebruikt in een functie.

Het **positie** argument van het **parameter** kenmerk heeft voor rang op de standaard waarde van **PositionalBinding** . U kunt het argument **positie** gebruiken om een positie waarde voor een para meter op te geven. Zie [about_Functions_Advanced_Parameters](about_Functions_Advanced_Parameters.md)voor meer informatie over het argument **positie** .

## <a name="notes"></a>Notities

Het argument **SupportsTransactions** wordt niet ondersteund in geavanceerde functies.

## <a name="keywords"></a>Trefwoorden

about_Functions_CmdletBinding_Attribute

## <a name="see-also"></a>Zie ook

[about_Functions](about_Functions.md)

[about_Functions_Advanced](about_Functions_Advanced.md)

[about_Functions_Advanced_Methods](about_Functions_Advanced_Methods.md)

[about_Functions_Advanced_Parameters](about_Functions_Advanced_Parameters.md)

[about_Functions_OutputTypeAttribute](about_Functions_OutputTypeAttribute.md)
