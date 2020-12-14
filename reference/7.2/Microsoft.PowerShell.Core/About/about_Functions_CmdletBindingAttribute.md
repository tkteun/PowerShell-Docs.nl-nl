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
# <a name="about-functions-cmdletbindingattribute"></a><span data-ttu-id="e0031-103">Over functies CmdletBindingAttribute</span><span class="sxs-lookup"><span data-stu-id="e0031-103">About Functions CmdletBindingAttribute</span></span>

## <a name="short-description"></a><span data-ttu-id="e0031-104">Korte beschrijving</span><span class="sxs-lookup"><span data-stu-id="e0031-104">Short description</span></span>
<span data-ttu-id="e0031-105">Beschrijft het kenmerk dat ervoor zorgt dat een functie werkt zoals een gecompileerde cmdlet.</span><span class="sxs-lookup"><span data-stu-id="e0031-105">Describes the attribute that makes a function work like a compiled cmdlet.</span></span>

## <a name="long-description"></a><span data-ttu-id="e0031-106">Lange beschrijving</span><span class="sxs-lookup"><span data-stu-id="e0031-106">Long description</span></span>

<span data-ttu-id="e0031-107">Het `CmdletBinding` kenmerk is een kenmerk van functies waarmee ze kunnen worden uitgevoerd zoals gecompileerde cmdlets die zijn geschreven in C#.</span><span class="sxs-lookup"><span data-stu-id="e0031-107">The `CmdletBinding` attribute is an attribute of functions that makes them operate like compiled cmdlets written in C#.</span></span> <span data-ttu-id="e0031-108">Het biedt toegang tot de functies van cmdlets.</span><span class="sxs-lookup"><span data-stu-id="e0031-108">It provides access to the features of cmdlets.</span></span>

<span data-ttu-id="e0031-109">Power shell bindt de para meters van functies die het `CmdletBinding` kenmerk hebben op dezelfde manier als de para meters van gecompileerde cmdlets.</span><span class="sxs-lookup"><span data-stu-id="e0031-109">PowerShell binds the parameters of functions that have the `CmdletBinding` attribute in the same way that it binds the parameters of compiled cmdlets.</span></span> <span data-ttu-id="e0031-110">De `$PSCmdlet` Automatische variabele is beschikbaar voor functies met het `CmdletBinding` kenmerk, maar de `$Args` variabele is niet beschikbaar.</span><span class="sxs-lookup"><span data-stu-id="e0031-110">The `$PSCmdlet` automatic variable is available to functions with the `CmdletBinding` attribute, but the `$Args` variable is not available.</span></span>

<span data-ttu-id="e0031-111">In functies met het `CmdletBinding` kenmerk, onbekende para meters en positionele argumenten die geen overeenkomende positionele para meters hebben, kan de parameter binding mislukken.</span><span class="sxs-lookup"><span data-stu-id="e0031-111">In functions that have the `CmdletBinding` attribute, unknown parameters and positional arguments that have no matching positional parameters cause parameter binding to fail.</span></span>

> [!NOTE]
> <span data-ttu-id="e0031-112">Gecompileerde cmdlets gebruiken het vereiste `Cmdlet` kenmerk, dat vergelijkbaar is met het `CmdletBinding` kenmerk dat in dit onderwerp wordt beschreven.</span><span class="sxs-lookup"><span data-stu-id="e0031-112">Compiled cmdlets use the required `Cmdlet` attribute, which is similar to the `CmdletBinding` attribute that is described in this topic.</span></span>

## <a name="syntax"></a><span data-ttu-id="e0031-113">Syntax</span><span class="sxs-lookup"><span data-stu-id="e0031-113">Syntax</span></span>

<span data-ttu-id="e0031-114">In het volgende voor beeld ziet u de indeling van een functie die alle optionele argumenten van het `CmdletBinding` kenmerk bevat.</span><span class="sxs-lookup"><span data-stu-id="e0031-114">The following example shows the format of a function that specifies all the optional arguments of the `CmdletBinding` attribute.</span></span> <span data-ttu-id="e0031-115">In dit voor beeld wordt een korte beschrijving van elk argument gevolgd.</span><span class="sxs-lookup"><span data-stu-id="e0031-115">A brief description of each argument follows this example.</span></span>

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

## <a name="confirmimpact"></a><span data-ttu-id="e0031-116">ConfirmImpact</span><span class="sxs-lookup"><span data-stu-id="e0031-116">ConfirmImpact</span></span>

<span data-ttu-id="e0031-117">Het argument **ConfirmImpact** geeft aan wanneer de actie van de functie moet worden bevestigd door een aanroep van de methode **ShouldProcess** .</span><span class="sxs-lookup"><span data-stu-id="e0031-117">The **ConfirmImpact** argument specifies when the action of the function should be confirmed by a call to the **ShouldProcess** method.</span></span> <span data-ttu-id="e0031-118">De aanroep van de methode **ShouldProcess** geeft alleen een bevestigings prompt weer wanneer het argument **ConfirmImpact** gelijk is aan of groter is dan de waarde van de `$ConfirmPreference` Voorkeurs variabele.</span><span class="sxs-lookup"><span data-stu-id="e0031-118">The call to the **ShouldProcess** method displays a confirmation prompt only when the **ConfirmImpact** argument is equal to or greater than the value of the `$ConfirmPreference` preference variable.</span></span> <span data-ttu-id="e0031-119">(De standaard waarde van het argument is **gemiddeld**.) Geef dit argument alleen op als het argument **SupportsShouldProcess** ook is opgegeven.</span><span class="sxs-lookup"><span data-stu-id="e0031-119">(The default value of the argument is **Medium**.) Specify this argument only when the **SupportsShouldProcess** argument is also specified.</span></span>

<span data-ttu-id="e0031-120">Zie [bevestiging aanvragen](/powershell/scripting/developer/cmdlet/requesting-confirmation)voor meer informatie over bevestigings aanvragen.</span><span class="sxs-lookup"><span data-stu-id="e0031-120">For more information about confirmation requests, see [Requesting Confirmation](/powershell/scripting/developer/cmdlet/requesting-confirmation).</span></span>

## <a name="defaultparametersetname"></a><span data-ttu-id="e0031-121">DefaultParameterSetName</span><span class="sxs-lookup"><span data-stu-id="e0031-121">DefaultParameterSetName</span></span>

<span data-ttu-id="e0031-122">Het argument **DefaultParameterSetName** geeft de naam van de parameterset op die Power shell probeert te gebruiken, wanneer niet kan worden bepaald welke para meter moet worden gebruikt.</span><span class="sxs-lookup"><span data-stu-id="e0031-122">The **DefaultParameterSetName** argument specifies the name of the parameter set that PowerShell will attempt to use when it cannot determine which parameter set to use.</span></span> <span data-ttu-id="e0031-123">U kunt dit probleem vermijden door de unieke para meter van elke para meter in te stellen op een verplichte para meter.</span><span class="sxs-lookup"><span data-stu-id="e0031-123">You can avoid this issue by making the unique parameter of each parameter set a mandatory parameter.</span></span>

## <a name="helpuri"></a><span data-ttu-id="e0031-124">HelpURI</span><span class="sxs-lookup"><span data-stu-id="e0031-124">HelpURI</span></span>

<span data-ttu-id="e0031-125">Met het argument **HelpURI** geeft u het Internet adres op van de online versie van het Help-onderwerp waarin de functie wordt beschreven.</span><span class="sxs-lookup"><span data-stu-id="e0031-125">The **HelpURI** argument specifies the internet address of the online version of the help topic that describes the function.</span></span> <span data-ttu-id="e0031-126">De waarde van het argument **HelpURI** moet beginnen met http of https.</span><span class="sxs-lookup"><span data-stu-id="e0031-126">The value of the **HelpURI** argument must begin with "http" or "https".</span></span>

<span data-ttu-id="e0031-127">De waarde van het argument **HelpURI** wordt gebruikt voor de waarde van de eigenschap **HelpURI** van het object **CommandInfo** dat `Get-Command` retourneert voor de functie.</span><span class="sxs-lookup"><span data-stu-id="e0031-127">The **HelpURI** argument value is used for the value of the **HelpURI** property of the **CommandInfo** object that `Get-Command` returns for the function.</span></span>

<span data-ttu-id="e0031-128">Als er echter Help-bestanden op de computer zijn geïnstalleerd en de waarde van de eerste koppeling in de sectie **RelatedLinks** van het Help-bestand een URI is, of als de waarde van de eerste `.Link` instructie in op opmerkingen gebaseerde Help een URI is, wordt de URI in het Help-bestand gebruikt als waarde van de eigenschap **HelpUri** van de functie.</span><span class="sxs-lookup"><span data-stu-id="e0031-128">However, when help files are installed on the computer and the value of the first link in the **RelatedLinks** section of the help file is a URI, or the value of the first `.Link` directive in comment-based help is a URI, the URI in the help file is used as the value of the **HelpUri** property of the function.</span></span>

<span data-ttu-id="e0031-129">De `Get-Help` cmdlet gebruikt de waarde van de eigenschap **HelpURI** om de online versie van het Help-onderwerp van de functie op te sporen wanneer de para meter **online** van `Get-Help` is opgegeven in een opdracht.</span><span class="sxs-lookup"><span data-stu-id="e0031-129">The `Get-Help` cmdlet uses the value of the **HelpURI** property to locate the online version of the function help topic when the **Online** parameter of `Get-Help` is specified in a command.</span></span>

## <a name="supportspaging"></a><span data-ttu-id="e0031-130">SupportsPaging</span><span class="sxs-lookup"><span data-stu-id="e0031-130">SupportsPaging</span></span>

<span data-ttu-id="e0031-131">Het argument **SupportsPaging** voegt de para meters **voor de eerste**, **Skip** en **IncludeTotalCount** toe aan de functie.</span><span class="sxs-lookup"><span data-stu-id="e0031-131">The **SupportsPaging** argument adds the **First**, **Skip**, and **IncludeTotalCount** parameters to the function.</span></span> <span data-ttu-id="e0031-132">Met deze para meters kunnen gebruikers uitvoer selecteren uit een zeer grote resultatenset.</span><span class="sxs-lookup"><span data-stu-id="e0031-132">These parameters allow users to select output from a very large result set.</span></span> <span data-ttu-id="e0031-133">Dit argument is ontworpen voor cmdlets en functies die gegevens retour neren uit grote gegevens archieven die ondersteuning bieden voor gegevens selectie, zoals een SQL database.</span><span class="sxs-lookup"><span data-stu-id="e0031-133">This argument is designed for cmdlets and functions that return data from large data stores that support data selection, such as an SQL database.</span></span>

<span data-ttu-id="e0031-134">Dit argument is geïntroduceerd in Windows Power Shell 3,0.</span><span class="sxs-lookup"><span data-stu-id="e0031-134">This argument was introduced in Windows PowerShell 3.0.</span></span>

- <span data-ttu-id="e0031-135">**First**: alleen de eerste n-objecten worden opgehaald.</span><span class="sxs-lookup"><span data-stu-id="e0031-135">**First**: Gets only the first 'n' objects.</span></span>
- <span data-ttu-id="e0031-136">**Overs Laan**: de eerste n-objecten worden genegeerd en vervolgens worden de resterende objecten opgehaald.</span><span class="sxs-lookup"><span data-stu-id="e0031-136">**Skip**:  Ignores the first 'n' objects and then gets the remaining objects.</span></span>
- <span data-ttu-id="e0031-137">**IncludeTotalCount**: rapporteert het aantal objecten in de gegevensset (een geheel getal), gevolgd door de objecten.</span><span class="sxs-lookup"><span data-stu-id="e0031-137">**IncludeTotalCount**: Reports the number of objects in the data set (an integer) followed by the objects.</span></span> <span data-ttu-id="e0031-138">Als het totale aantal niet kan worden vastgesteld met de cmdlet, wordt ' onbekend totaal aantal ' geretourneerd.</span><span class="sxs-lookup"><span data-stu-id="e0031-138">If the cmdlet cannot determine the total count, it returns "Unknown total count".</span></span>

<span data-ttu-id="e0031-139">Power shell bevat **NewTotalCount**, een hulp methode waarmee de totale waarde voor aantal te retour neren wordt opgehaald en een schatting wordt opgenomen van de nauw keurigheid van de totale waarde voor Count.</span><span class="sxs-lookup"><span data-stu-id="e0031-139">PowerShell includes **NewTotalCount**, a helper method that gets the total count value to return and includes an estimate of the accuracy of the total count value.</span></span>

<span data-ttu-id="e0031-140">De volgende voorbeeld functie laat zien hoe u ondersteuning voor de paginerings parameters toevoegt aan een geavanceerde functie.</span><span class="sxs-lookup"><span data-stu-id="e0031-140">The following sample function shows how to add support for the paging parameters to an advanced function.</span></span>

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

## <a name="supportsshouldprocess"></a><span data-ttu-id="e0031-141">SupportsShouldProcess</span><span class="sxs-lookup"><span data-stu-id="e0031-141">SupportsShouldProcess</span></span>

<span data-ttu-id="e0031-142">Het argument **SupportsShouldProcess** voegt de para meters **confirm** en **WhatIf** toe aan de functie.</span><span class="sxs-lookup"><span data-stu-id="e0031-142">The **SupportsShouldProcess** argument adds **Confirm** and **WhatIf** parameters to the function.</span></span> <span data-ttu-id="e0031-143">De para meter **confirm** vraagt de gebruiker voordat de opdracht wordt uitgevoerd op elk object in de pijp lijn.</span><span class="sxs-lookup"><span data-stu-id="e0031-143">The **Confirm** parameter prompts the user before it runs the command on each object in the pipeline.</span></span> <span data-ttu-id="e0031-144">De para meter **WhatIf** geeft een lijst van de wijzigingen die door de opdracht zouden worden aangebracht, in plaats van de opdracht uit te voeren.</span><span class="sxs-lookup"><span data-stu-id="e0031-144">The **WhatIf** parameter lists the changes that the command would make, instead of running the command.</span></span>

## <a name="positionalbinding"></a><span data-ttu-id="e0031-145">PositionalBinding</span><span class="sxs-lookup"><span data-stu-id="e0031-145">PositionalBinding</span></span>

<span data-ttu-id="e0031-146">Het argument **PositionalBinding** bepaalt of para meters in de functie standaard positioneel zijn.</span><span class="sxs-lookup"><span data-stu-id="e0031-146">The **PositionalBinding** argument determines whether parameters in the function are positional by default.</span></span> <span data-ttu-id="e0031-147">De standaardwaarde is `$True`.</span><span class="sxs-lookup"><span data-stu-id="e0031-147">The default value is `$True`.</span></span> <span data-ttu-id="e0031-148">U kunt het argument **PositionalBinding** gebruiken met de waarde `$False` om positie binding uit te scha kelen.</span><span class="sxs-lookup"><span data-stu-id="e0031-148">You can use the **PositionalBinding** argument with a value of `$False` to disable positional binding.</span></span>

<span data-ttu-id="e0031-149">Het argument **PositionalBinding** is geïntroduceerd in Windows power Shell 3,0.</span><span class="sxs-lookup"><span data-stu-id="e0031-149">The **PositionalBinding** argument is introduced in Windows PowerShell 3.0.</span></span>

<span data-ttu-id="e0031-150">Wanneer para meters positioneel zijn, is de parameter naam optioneel.</span><span class="sxs-lookup"><span data-stu-id="e0031-150">When parameters are positional, the parameter name is optional.</span></span>
<span data-ttu-id="e0031-151">Power shell koppelt geen naam parameter waarden met de functie parameters volgens de volg orde of positie van de niet-genaamde parameter waarden in de functie opdracht.</span><span class="sxs-lookup"><span data-stu-id="e0031-151">PowerShell associates unnamed parameter values with the function parameters according to the order or position of the unnamed parameter values in the function command.</span></span>

<span data-ttu-id="e0031-152">Wanneer para meters niet positioneel zijn (deze zijn ' naam '), is de parameter naam (of een afkorting of alias van de naam) vereist in de opdracht.</span><span class="sxs-lookup"><span data-stu-id="e0031-152">When parameters are not positional (they are "named"), the parameter name (or an abbreviation or alias of the name) is required in the command.</span></span>

<span data-ttu-id="e0031-153">Wanneer **PositionalBinding** is `$True` , zijn functie parameters standaard positioneel.</span><span class="sxs-lookup"><span data-stu-id="e0031-153">When **PositionalBinding** is `$True`, function parameters are positional by default.</span></span> <span data-ttu-id="e0031-154">Power shell wijst positie nummer toe aan de para meters in de volg orde waarin ze worden gedeclareerd in de functie.</span><span class="sxs-lookup"><span data-stu-id="e0031-154">PowerShell assigns position number to the parameters in the order in which they are declared in the function.</span></span>

<span data-ttu-id="e0031-155">Wanneer **PositionalBinding** is `$False` , zijn functie parameters standaard niet positioneel.</span><span class="sxs-lookup"><span data-stu-id="e0031-155">When **PositionalBinding** is `$False`, function parameters are not positional by default.</span></span> <span data-ttu-id="e0031-156">Tenzij het **positie** argument van het **parameter** kenmerk is gedeclareerd voor de para meter, moet de parameter naam (of een alias of afkorting) worden opgenomen wanneer de para meter wordt gebruikt in een functie.</span><span class="sxs-lookup"><span data-stu-id="e0031-156">Unless the **Position** argument of the **Parameter** attribute is declared on the parameter, the parameter name (or an alias or abbreviation) must be included when the parameter is used in a function.</span></span>

<span data-ttu-id="e0031-157">Het **positie** argument van het **parameter** kenmerk heeft voor rang op de standaard waarde van **PositionalBinding** .</span><span class="sxs-lookup"><span data-stu-id="e0031-157">The **Position** argument of the **Parameter** attribute takes precedence over the **PositionalBinding** default value.</span></span> <span data-ttu-id="e0031-158">U kunt het argument **positie** gebruiken om een positie waarde voor een para meter op te geven.</span><span class="sxs-lookup"><span data-stu-id="e0031-158">You can use the **Position** argument to specify a position value for a parameter.</span></span> <span data-ttu-id="e0031-159">Zie [about_Functions_Advanced_Parameters](about_Functions_Advanced_Parameters.md)voor meer informatie over het argument **positie** .</span><span class="sxs-lookup"><span data-stu-id="e0031-159">For more information about the **Position** argument, see [about_Functions_Advanced_Parameters](about_Functions_Advanced_Parameters.md).</span></span>

## <a name="notes"></a><span data-ttu-id="e0031-160">Notities</span><span class="sxs-lookup"><span data-stu-id="e0031-160">Notes</span></span>

<span data-ttu-id="e0031-161">Het argument **SupportsTransactions** wordt niet ondersteund in geavanceerde functies.</span><span class="sxs-lookup"><span data-stu-id="e0031-161">The **SupportsTransactions** argument is not supported in advanced functions.</span></span>

## <a name="keywords"></a><span data-ttu-id="e0031-162">Trefwoorden</span><span class="sxs-lookup"><span data-stu-id="e0031-162">Keywords</span></span>

<span data-ttu-id="e0031-163">about_Functions_CmdletBinding_Attribute</span><span class="sxs-lookup"><span data-stu-id="e0031-163">about_Functions_CmdletBinding_Attribute</span></span>

## <a name="see-also"></a><span data-ttu-id="e0031-164">Zie ook</span><span class="sxs-lookup"><span data-stu-id="e0031-164">See also</span></span>

[<span data-ttu-id="e0031-165">about_Functions</span><span class="sxs-lookup"><span data-stu-id="e0031-165">about_Functions</span></span>](about_Functions.md)

[<span data-ttu-id="e0031-166">about_Functions_Advanced</span><span class="sxs-lookup"><span data-stu-id="e0031-166">about_Functions_Advanced</span></span>](about_Functions_Advanced.md)

[<span data-ttu-id="e0031-167">about_Functions_Advanced_Methods</span><span class="sxs-lookup"><span data-stu-id="e0031-167">about_Functions_Advanced_Methods</span></span>](about_Functions_Advanced_Methods.md)

[<span data-ttu-id="e0031-168">about_Functions_Advanced_Parameters</span><span class="sxs-lookup"><span data-stu-id="e0031-168">about_Functions_Advanced_Parameters</span></span>](about_Functions_Advanced_Parameters.md)

[<span data-ttu-id="e0031-169">about_Functions_OutputTypeAttribute</span><span class="sxs-lookup"><span data-stu-id="e0031-169">about_Functions_OutputTypeAttribute</span></span>](about_Functions_OutputTypeAttribute.md)
