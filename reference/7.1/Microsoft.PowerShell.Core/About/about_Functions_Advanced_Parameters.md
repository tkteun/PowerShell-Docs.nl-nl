---
description: Legt uit hoe u parameters toevoegt aan geavanceerde functies.
keywords: powershell,cmdlet
Locale: en-US
ms.date: 04/14/2021
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_functions_advanced_parameters?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Functions_Advanced_Parameters
ms.openlocfilehash: d23ce7469f3df2561530b678192038093af9180e
ms.sourcegitcommit: 366304d096c1caf52f0e17962f6ed23d20f86e7b
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 04/16/2021
ms.locfileid: "107543873"
---
# <a name="about-functions-advanced-parameters"></a><span data-ttu-id="cac26-104">Over geavanceerde functiesparameters</span><span class="sxs-lookup"><span data-stu-id="cac26-104">About Functions Advanced Parameters</span></span>

## <a name="short-description"></a><span data-ttu-id="cac26-105">Korte beschrijving</span><span class="sxs-lookup"><span data-stu-id="cac26-105">Short description</span></span>

<span data-ttu-id="cac26-106">Legt uit hoe u parameters toevoegt aan geavanceerde functies.</span><span class="sxs-lookup"><span data-stu-id="cac26-106">Explains how to add parameters to advanced functions.</span></span>

## <a name="long-description"></a><span data-ttu-id="cac26-107">Lange beschrijving</span><span class="sxs-lookup"><span data-stu-id="cac26-107">Long description</span></span>

<span data-ttu-id="cac26-108">U kunt parameters toevoegen aan de geavanceerde functies die u schrijft en parameterkenmerken en argumenten gebruiken om de parameterwaarden te beperken die functiegebruikers verzenden met de parameter .</span><span class="sxs-lookup"><span data-stu-id="cac26-108">You can add parameters to the advanced functions that you write, and use parameter attributes and arguments to limit the parameter values that function users submit with the parameter.</span></span>

<span data-ttu-id="cac26-109">De parameters die u aan uw functie toevoegt, zijn beschikbaar voor gebruikers, naast de algemene parameters die PowerShell automatisch toevoegt aan alle cmdlets en geavanceerde functies.</span><span class="sxs-lookup"><span data-stu-id="cac26-109">The parameters that you add to your function are available to users in addition to the common parameters that PowerShell adds automatically to all cmdlets and advanced functions.</span></span> <span data-ttu-id="cac26-110">Zie voor meer informatie over de algemene PowerShell-parameters [about_CommonParameters.](about_CommonParameters.md)</span><span class="sxs-lookup"><span data-stu-id="cac26-110">For more information about the PowerShell common parameters, see [about_CommonParameters](about_CommonParameters.md).</span></span>

<span data-ttu-id="cac26-111">Vanaf PowerShell 3.0 kunt u splatting gebruiken met om de parameters in een `@Args` opdracht weer te geven.</span><span class="sxs-lookup"><span data-stu-id="cac26-111">Beginning in PowerShell 3.0, you can use splatting with `@Args` to represent the parameters in a command.</span></span> <span data-ttu-id="cac26-112">Splatting is geldig voor eenvoudige en geavanceerde functies.</span><span class="sxs-lookup"><span data-stu-id="cac26-112">Splatting is valid on simple and advanced functions.</span></span> <span data-ttu-id="cac26-113">Zie voor meer informatie [about_Functions](about_Functions.md) en [about_Splatting.](about_Splatting.md)</span><span class="sxs-lookup"><span data-stu-id="cac26-113">For more information, see [about_Functions](about_Functions.md) and [about_Splatting](about_Splatting.md).</span></span>

## <a name="type-conversion-of-parameter-values"></a><span data-ttu-id="cac26-114">Typeconversie van parameterwaarden</span><span class="sxs-lookup"><span data-stu-id="cac26-114">Type conversion of parameter values</span></span>

<span data-ttu-id="cac26-115">Wanneer u tekenreeksen als argumenten opgeeft voor parameters die een ander type verwachten, converteert PowerShell impliciet de tekenreeksen naar het doeltype van de parameter.</span><span class="sxs-lookup"><span data-stu-id="cac26-115">When you supply strings as arguments to parameters that expect a different type, PowerShell implicitly converts the strings to the parameter target type.</span></span>
<span data-ttu-id="cac26-116">Geavanceerde functies voeren cultuur-invariante parsering van parameterwaarden uit.</span><span class="sxs-lookup"><span data-stu-id="cac26-116">Advanced functions perform culture-invariant parsing of parameter values.</span></span>

<span data-ttu-id="cac26-117">Daarentegen wordt een cultuurgevoelige conversie uitgevoerd tijdens parameterbinding voor gecompileerde cmdlets.</span><span class="sxs-lookup"><span data-stu-id="cac26-117">By contrast, a culture-sensitive conversion is performed during parameter binding for compiled cmdlets.</span></span>

<span data-ttu-id="cac26-118">In dit voorbeeld maken we een cmdlet en een scriptfunctie die een `[datetime]` parameter gebruiken.</span><span class="sxs-lookup"><span data-stu-id="cac26-118">In this example, we create a cmdlet and a script function that take a `[datetime]` parameter.</span></span> <span data-ttu-id="cac26-119">De huidige cultuur wordt gewijzigd om Duitse instellingen te gebruiken.</span><span class="sxs-lookup"><span data-stu-id="cac26-119">The current culture is changed to use German settings.</span></span>
<span data-ttu-id="cac26-120">Een datum in Duits-indeling wordt doorgegeven aan de parameter .</span><span class="sxs-lookup"><span data-stu-id="cac26-120">A German-formatted date is passed to the parameter.</span></span>

```powershell
# Create a cmdlet that accepts a [datetime] argument.
Add-Type @'
  using System;
  using System.Management.Automation;
  [Cmdlet("Get", "Date_Cmdlet")]
  public class GetFooCmdlet : Cmdlet {

    [Parameter(Position=0)]
    public DateTime Date { get; set; }

    protected override void ProcessRecord() {
      WriteObject(Date);
    }
  }
'@ -PassThru | % Assembly | Import-Module

[cultureinfo]::CurrentCulture = 'de-DE'
$dateStr = '19-06-2018'

Get-Date_Cmdlet $dateStr
```

```Output
Dienstag, 19. Juni 2018 00:00:00
```

<span data-ttu-id="cac26-121">Zoals hierboven wordt weergegeven, gebruiken cmdlets cultuurgevoelige parsering om de tekenreeks te converteren.</span><span class="sxs-lookup"><span data-stu-id="cac26-121">As shown above, cmdlets use culture-sensitive parsing to convert the string.</span></span>

```powershell
# Define an equivalent function.
function Get-Date_Func {
  param(
    [DateTime] $Date
  )
  process {
    $Date
  }
}

[cultureinfo]::CurrentCulture = 'de-DE'

# This German-format date string doesn't work with the invariant culture.
# E.g., [datetime] '19-06-2018' breaks.
$dateStr = '19-06-2018'

Get-Date_Func $dateStr
```

<span data-ttu-id="cac26-122">Geavanceerde functies maken gebruik van culture-invariant parsing, wat resulteert in de volgende fout.</span><span class="sxs-lookup"><span data-stu-id="cac26-122">Advanced functions use culture-invariant parsing, which results in the following error.</span></span>

```Output
Get-Date_Func: Cannot process argument transformation on parameter 'Date'.
Cannot convert value "19-06-2018" to type "System.DateTime". Error: "String
'19-06-2018' was not recognized as a valid DateTime."
```

## <a name="static-parameters"></a><span data-ttu-id="cac26-123">Statische parameters</span><span class="sxs-lookup"><span data-stu-id="cac26-123">Static parameters</span></span>

<span data-ttu-id="cac26-124">Statische parameters zijn parameters die altijd beschikbaar zijn in de functie.</span><span class="sxs-lookup"><span data-stu-id="cac26-124">Static parameters are parameters that are always available in the function.</span></span>
<span data-ttu-id="cac26-125">De meeste parameters in PowerShell-cmdlets en -scripts zijn statische parameters.</span><span class="sxs-lookup"><span data-stu-id="cac26-125">Most parameters in PowerShell cmdlets and scripts are static parameters.</span></span>

<span data-ttu-id="cac26-126">In het volgende voorbeeld ziet u de declaratie van een **Parameter ComputerName** met de volgende kenmerken:</span><span class="sxs-lookup"><span data-stu-id="cac26-126">The following example shows the declaration of a **ComputerName** parameter that has the following characteristics:</span></span>

- <span data-ttu-id="cac26-127">Dit is verplicht (vereist).</span><span class="sxs-lookup"><span data-stu-id="cac26-127">It's mandatory (required).</span></span>
- <span data-ttu-id="cac26-128">Er wordt invoer uit de pijplijn gebruikt.</span><span class="sxs-lookup"><span data-stu-id="cac26-128">It takes input from the pipeline.</span></span>
- <span data-ttu-id="cac26-129">Er wordt een matrix met tekenreeksen als invoer gebruikt.</span><span class="sxs-lookup"><span data-stu-id="cac26-129">It takes an array of strings as input.</span></span>

```powershell
Param(
    [Parameter(Mandatory=$true,
    ValueFromPipeline=$true)]
    [String[]]
    $ComputerName
)
```

## <a name="attributes-of-parameters"></a><span data-ttu-id="cac26-130">Kenmerken van parameters</span><span class="sxs-lookup"><span data-stu-id="cac26-130">Attributes of parameters</span></span>

<span data-ttu-id="cac26-131">In deze sectie worden de kenmerken beschreven die u kunt toevoegen aan functieparameters.</span><span class="sxs-lookup"><span data-stu-id="cac26-131">This section describes the attributes that you can add to function parameters.</span></span>

<span data-ttu-id="cac26-132">Alle kenmerken zijn optioneel.</span><span class="sxs-lookup"><span data-stu-id="cac26-132">All attributes are optional.</span></span> <span data-ttu-id="cac26-133">Als u echter het **kenmerk CmdletBinding** weglaat, moet de functie het **kenmerk Parameter** bevatten om te worden herkend als een geavanceerde functie.</span><span class="sxs-lookup"><span data-stu-id="cac26-133">However, if you omit the **CmdletBinding** attribute, then to be recognized as an advanced function, the function must include the **Parameter** attribute.</span></span>

<span data-ttu-id="cac26-134">U kunt een of meer kenmerken toevoegen aan elke parameterdeclaratie.</span><span class="sxs-lookup"><span data-stu-id="cac26-134">You can add one or multiple attributes in each parameter declaration.</span></span> <span data-ttu-id="cac26-135">Er is geen limiet voor het aantal kenmerken dat u aan een parameterdeclaratie kunt toevoegen.</span><span class="sxs-lookup"><span data-stu-id="cac26-135">There's no limit to the number of attributes that you can add to a parameter declaration.</span></span>

### <a name="parameter-attribute"></a><span data-ttu-id="cac26-136">Parameterkenmerk</span><span class="sxs-lookup"><span data-stu-id="cac26-136">Parameter attribute</span></span>

<span data-ttu-id="cac26-137">Het **kenmerk Parameter** wordt gebruikt om de kenmerken van functieparameters te declaren.</span><span class="sxs-lookup"><span data-stu-id="cac26-137">The **Parameter** attribute is used to declare the attributes of function parameters.</span></span>

<span data-ttu-id="cac26-138">Het **kenmerk Parameter** is optioneel en u kunt dit weglaten als geen van de parameters van uw functies kenmerken nodig heeft.</span><span class="sxs-lookup"><span data-stu-id="cac26-138">The **Parameter** attribute is optional, and you can omit it if none of the parameters of your functions need attributes.</span></span> <span data-ttu-id="cac26-139">Maar om te worden herkend als een geavanceerde functie, in plaats van een eenvoudige functie, moet een functie ofwel het **kenmerk CmdletBinding,** het **kenmerk Parameter** of beide hebben.</span><span class="sxs-lookup"><span data-stu-id="cac26-139">But, to be recognized as an advanced function, rather than a simple function, a function must have either the **CmdletBinding** attribute or the **Parameter** attribute, or both.</span></span>

<span data-ttu-id="cac26-140">Het **kenmerk Parameter** bevat argumenten die de kenmerken van de parameter definiëren, zoals of de parameter verplicht of optioneel is.</span><span class="sxs-lookup"><span data-stu-id="cac26-140">The **Parameter** attribute has arguments that define the characteristics of the parameter, such as whether the parameter is mandatory or optional.</span></span>

<span data-ttu-id="cac26-141">Gebruik de volgende syntaxis om het **kenmerk Parameter,** een argument en een argumentwaarde te declareer.</span><span class="sxs-lookup"><span data-stu-id="cac26-141">Use the following syntax to declare the **Parameter** attribute, an argument, and an argument value.</span></span> <span data-ttu-id="cac26-142">De haakjes die het argument en de waarde ervan omsluiten, moeten **parameter** volgen zonder tussenliggende spatie.</span><span class="sxs-lookup"><span data-stu-id="cac26-142">The parentheses that enclose the argument and its value must follow **Parameter** with no intervening space.</span></span>

```powershell
Param(
    [Parameter(Argument=value)]
    $ParameterName
)
```

<span data-ttu-id="cac26-143">Gebruik komma's om argumenten tussen haakjes te scheiden.</span><span class="sxs-lookup"><span data-stu-id="cac26-143">Use commas to separate arguments within the parentheses.</span></span> <span data-ttu-id="cac26-144">Gebruik de volgende syntaxis om twee argumenten van het kenmerk **Parameter te** declaren.</span><span class="sxs-lookup"><span data-stu-id="cac26-144">Use the following syntax to declare two arguments of the **Parameter** attribute.</span></span>

```powershell
Param(
    [Parameter(Argument1=value1,
    Argument2=value2)]
)
```

<span data-ttu-id="cac26-145">De booleaanse argumenttypen van het **kenmerk Parameter** worden standaard ingesteld op **Onwaar** wanneer dit wordt weggelaten uit het **kenmerk Parameter.**</span><span class="sxs-lookup"><span data-stu-id="cac26-145">The boolean argument types of the **Parameter** attribute default to **False** when omitted from the **Parameter** attribute.</span></span> <span data-ttu-id="cac26-146">Stel de argumentwaarde in op `$true` of vermeld het argument op naam.</span><span class="sxs-lookup"><span data-stu-id="cac26-146">Set the argument value to `$true` or just list the argument by name.</span></span> <span data-ttu-id="cac26-147">De volgende parameterkenmerken **zijn** bijvoorbeeld gelijkwaardig.</span><span class="sxs-lookup"><span data-stu-id="cac26-147">For example, the following **Parameter** attributes are equivalent.</span></span>

```powershell
Param(
    [Parameter(Mandatory=$true)]
)

# Boolean arguments can be defined using this shorthand syntax

Param(
    [Parameter(Mandatory)]
)
```

<span data-ttu-id="cac26-148">Als u het **kenmerk Parameter** zonder argumenten gebruikt, als alternatief voor het gebruik van het kenmerk **CmdletBinding,** zijn de haakjes die de kenmerknaam volgen nog steeds vereist.</span><span class="sxs-lookup"><span data-stu-id="cac26-148">If you use the **Parameter** attribute without arguments, as an alternative to using the **CmdletBinding** attribute, the parentheses that follow the attribute name are still required.</span></span>

```powershell
Param(
    [Parameter()]
    $ParameterName
)
```

#### <a name="mandatory-argument"></a><span data-ttu-id="cac26-149">Verplicht argument</span><span class="sxs-lookup"><span data-stu-id="cac26-149">Mandatory argument</span></span>

<span data-ttu-id="cac26-150">Het `Mandatory` argument geeft aan dat de parameter vereist is.</span><span class="sxs-lookup"><span data-stu-id="cac26-150">The `Mandatory` argument indicates that the parameter is required.</span></span> <span data-ttu-id="cac26-151">Als dit argument niet is opgegeven, is de parameter optioneel.</span><span class="sxs-lookup"><span data-stu-id="cac26-151">If this argument isn't specified, the parameter is optional.</span></span>

<span data-ttu-id="cac26-152">In het volgende voorbeeld wordt de **parameter ComputerName gedeclareert.**</span><span class="sxs-lookup"><span data-stu-id="cac26-152">The following example declares the **ComputerName** parameter.</span></span> <span data-ttu-id="cac26-153">Het argument wordt `Mandatory` gebruikt om de parameter verplicht te maken.</span><span class="sxs-lookup"><span data-stu-id="cac26-153">It uses the `Mandatory` argument to make the parameter mandatory.</span></span>

```powershell
Param(
    [Parameter(Mandatory=$true)]
    [String[]]
    $ComputerName
)
```

#### <a name="position-argument"></a><span data-ttu-id="cac26-154">Argument position</span><span class="sxs-lookup"><span data-stu-id="cac26-154">Position argument</span></span>

<span data-ttu-id="cac26-155">Het `Position` argument bepaalt of de parameternaam vereist is wanneer de parameter wordt gebruikt in een opdracht.</span><span class="sxs-lookup"><span data-stu-id="cac26-155">The `Position` argument determines whether the parameter name is required when the parameter is used in a command.</span></span> <span data-ttu-id="cac26-156">Wanneer een parameterdeclaratie het argument bevat, kan de parameternaam worden weggelaten en identificeert PowerShell de naamloze parameterwaarde op basis van de positie of volgorde in de lijst met niet-naamloze parameterwaarden in de `Position` opdracht.</span><span class="sxs-lookup"><span data-stu-id="cac26-156">When a parameter declaration includes the `Position` argument, the parameter name can be omitted and PowerShell identifies the unnamed parameter value by its position, or order, in the list of unnamed parameter values in the command.</span></span>

<span data-ttu-id="cac26-157">Als het argument niet is opgegeven, moet de parameternaam of een parameternaamalias of -afkorting voorafgaan aan de parameterwaarde wanneer de parameter wordt gebruikt in een `Position` opdracht.</span><span class="sxs-lookup"><span data-stu-id="cac26-157">If the `Position` argument isn't specified, the parameter name, or a parameter name alias or abbreviation, must precede the parameter value whenever the parameter is used in a command.</span></span>

<span data-ttu-id="cac26-158">Standaard zijn alle functieparameters positioneel.</span><span class="sxs-lookup"><span data-stu-id="cac26-158">By default, all function parameters are positional.</span></span> <span data-ttu-id="cac26-159">PowerShell wijst positienummers toe aan parameters in de volgorde waarin de parameters in de functie worden gedeclareerd.</span><span class="sxs-lookup"><span data-stu-id="cac26-159">PowerShell assigns position numbers to parameters in the order in which the parameters are declared in the function.</span></span> <span data-ttu-id="cac26-160">Als u deze functie wilt uitschakelen, stelt u de waarde van `PositionalBinding` het argument van het kenmerk **CmdletBinding** in op `$False` .</span><span class="sxs-lookup"><span data-stu-id="cac26-160">To disable this feature, set the value of the `PositionalBinding` argument of the **CmdletBinding** attribute to `$False`.</span></span> <span data-ttu-id="cac26-161">Het `Position` argument heeft voorrang op de waarde van het argument van het kenmerk `PositionalBinding` **CmdletBinding.**</span><span class="sxs-lookup"><span data-stu-id="cac26-161">The `Position` argument takes precedence over the value of the `PositionalBinding` argument of the **CmdletBinding** attribute.</span></span> <span data-ttu-id="cac26-162">Zie in about_Functions_CmdletBindingAttribute `PositionalBinding` voor [meer informatie.](about_Functions_CmdletBindingAttribute.md)</span><span class="sxs-lookup"><span data-stu-id="cac26-162">For more information, see `PositionalBinding` in [about_Functions_CmdletBindingAttribute](about_Functions_CmdletBindingAttribute.md).</span></span>

<span data-ttu-id="cac26-163">De waarde van het `Position` argument wordt opgegeven als een geheel getal.</span><span class="sxs-lookup"><span data-stu-id="cac26-163">The value of the `Position` argument is specified as an integer.</span></span> <span data-ttu-id="cac26-164">Een positiewaarde **van 0** vertegenwoordigt de eerste positie in de opdracht, een positiewaarde **van 1** vertegenwoordigt de tweede positie in de opdracht, en meer.</span><span class="sxs-lookup"><span data-stu-id="cac26-164">A position value of **0** represents the first position in the command, a position value of **1** represents the second position in the command, and so on.</span></span>

<span data-ttu-id="cac26-165">Als een functie geen positionele parameters heeft, wijst PowerShell posities toe aan elke parameter op basis van de volgorde waarin de parameters worden gedeclareerd.</span><span class="sxs-lookup"><span data-stu-id="cac26-165">If a function has no positional parameters, PowerShell assigns positions to each parameter based on the order in which the parameters are declared.</span></span>
<span data-ttu-id="cac26-166">Als een best practice, vertrouwt u echter niet op deze toewijzing.</span><span class="sxs-lookup"><span data-stu-id="cac26-166">However, as a best practice, don't rely on this assignment.</span></span> <span data-ttu-id="cac26-167">Als u wilt dat parameters positioneel zijn, gebruikt u het `Position` argument .</span><span class="sxs-lookup"><span data-stu-id="cac26-167">When you want parameters to be positional, use the `Position` argument.</span></span>

<span data-ttu-id="cac26-168">In het volgende voorbeeld wordt de **parameter ComputerName gedeclareert.**</span><span class="sxs-lookup"><span data-stu-id="cac26-168">The following example declares the **ComputerName** parameter.</span></span> <span data-ttu-id="cac26-169">Hierbij wordt het `Position` argument met een waarde van **0 gebruikt.**</span><span class="sxs-lookup"><span data-stu-id="cac26-169">It uses the `Position` argument with a value of **0**.</span></span> <span data-ttu-id="cac26-170">Als gevolg hiervan, wanneer wordt weggelaten uit de opdracht, moet de waarde ervan de eerste of alleen `-ComputerName` naamloze parameterwaarde in de opdracht.</span><span class="sxs-lookup"><span data-stu-id="cac26-170">As a result, when `-ComputerName` is omitted from command, its value must be the first or only unnamed parameter value in the command.</span></span>

```powershell
Param(
    [Parameter(Position=0)]
    [String[]]
    $ComputerName
)
```

#### <a name="parametersetname-argument"></a><span data-ttu-id="cac26-171">Argument ParameterSetName</span><span class="sxs-lookup"><span data-stu-id="cac26-171">ParameterSetName argument</span></span>

<span data-ttu-id="cac26-172">Het `ParameterSetName` argument geeft de parameterset aan waar een parameter bij hoort.</span><span class="sxs-lookup"><span data-stu-id="cac26-172">The `ParameterSetName` argument specifies the parameter set to which a parameter belongs.</span></span> <span data-ttu-id="cac26-173">Als er geen parameterset is opgegeven, behoort de parameter tot alle parametersets die door de functie zijn gedefinieerd.</span><span class="sxs-lookup"><span data-stu-id="cac26-173">If no parameter set is specified, the parameter belongs to all the parameter sets defined by the function.</span></span> <span data-ttu-id="cac26-174">Om uniek te zijn, moet elke parameterset ten minste één parameter hebben die geen lid is van een andere parameterset.</span><span class="sxs-lookup"><span data-stu-id="cac26-174">Therefore, to be unique, each parameter set must have at least one parameter that isn't a member of any other parameter set.</span></span>

> [!NOTE]
> <span data-ttu-id="cac26-175">Voor een cmdlet of functie geldt een limiet van 32 parametersets.</span><span class="sxs-lookup"><span data-stu-id="cac26-175">For a cmdlet or function, there is a limit of 32 parameter sets.</span></span>

<span data-ttu-id="cac26-176">In het volgende voorbeeld wordt een **computernaam** parameter in de parameterset, een Gebruikersnaam parameter in de parameterset en een Samenvatting `Computer` parameter in beide  `User` parametersets gedeclareert. </span><span class="sxs-lookup"><span data-stu-id="cac26-176">The following example declares a **ComputerName** parameter in the `Computer` parameter set, a **UserName** parameter in the `User` parameter set, and a **Summary** parameter in both parameter sets.</span></span>

```powershell
Param(
    [Parameter(Mandatory=$true,
    ParameterSetName="Computer")]
    [String[]]
    $ComputerName,

    [Parameter(Mandatory=$true,
    ParameterSetName="User")]
    [String[]]
    $UserName,

    [Parameter(Mandatory=$false)]
    [Switch]
    $Summary
)
```

<span data-ttu-id="cac26-177">U kunt slechts één waarde `ParameterSetName` opgeven in elk argument en slechts één argument in elk `ParameterSetName` **parameterkenmerk.**</span><span class="sxs-lookup"><span data-stu-id="cac26-177">You can specify only one `ParameterSetName` value in each argument and only one `ParameterSetName` argument in each **Parameter** attribute.</span></span> <span data-ttu-id="cac26-178">Als u wilt aangeven dat een parameter wordt weergegeven in meer dan één parameterset, voegt u aanvullende **parameterkenmerken** toe.</span><span class="sxs-lookup"><span data-stu-id="cac26-178">To indicate that a parameter appears in more than one parameter set, add additional **Parameter** attributes.</span></span>

<span data-ttu-id="cac26-179">In het volgende voorbeeld wordt de parameter **Summary** expliciet toegevoegd aan de `Computer` `User` parametersets en .</span><span class="sxs-lookup"><span data-stu-id="cac26-179">The following example explicitly adds the **Summary** parameter to the `Computer` and `User` parameter sets.</span></span> <span data-ttu-id="cac26-180">De **samenvatting** parameter is optioneel in de `Computer` parameterset en verplicht in de `User` parameterset.</span><span class="sxs-lookup"><span data-stu-id="cac26-180">The **Summary** parameter is optional in the `Computer` parameter set and mandatory in the `User` parameter set.</span></span>

```powershell
Param(
    [Parameter(Mandatory=$true,
    ParameterSetName="Computer")]
    [String[]]
    $ComputerName,

    [Parameter(Mandatory=$true,
    ParameterSetName="User")]
    [String[]]
    $UserName,

    [Parameter(Mandatory=$false, ParameterSetName="Computer")]
    [Parameter(Mandatory=$true, ParameterSetName="User")]
    [Switch]
    $Summary
)
```

<span data-ttu-id="cac26-181">Zie Over parametersets voor meer informatie [over parametersets.](about_parameter_sets.md)</span><span class="sxs-lookup"><span data-stu-id="cac26-181">For more information about parameter sets, see [About Parameter Sets](about_parameter_sets.md).</span></span>

#### <a name="valuefrompipeline-argument"></a><span data-ttu-id="cac26-182">Argument ValueFromPipeline</span><span class="sxs-lookup"><span data-stu-id="cac26-182">ValueFromPipeline argument</span></span>

<span data-ttu-id="cac26-183">Het `ValueFromPipeline` argument geeft aan dat de parameter invoer van een pijplijnobject accepteert.</span><span class="sxs-lookup"><span data-stu-id="cac26-183">The `ValueFromPipeline` argument indicates that the parameter accepts input from a pipeline object.</span></span> <span data-ttu-id="cac26-184">Geef dit argument op als de functie het hele object accepteert, niet alleen een eigenschap van het object.</span><span class="sxs-lookup"><span data-stu-id="cac26-184">Specify this argument if the function accepts the entire object, not just a property of the object.</span></span>

<span data-ttu-id="cac26-185">In het volgende voorbeeld wordt een **parameter ComputerName** gedeclareert die verplicht is en een object accepteert dat vanuit de pijplijn wordt doorgegeven aan de functie.</span><span class="sxs-lookup"><span data-stu-id="cac26-185">The following example declares a **ComputerName** parameter that's mandatory and accepts an object that's passed to the function from the pipeline.</span></span>

```powershell
Param(
    [Parameter(Mandatory=$true,
    ValueFromPipeline=$true)]
    [String[]]
    $ComputerName
)
```

#### <a name="valuefrompipelinebypropertyname-argument"></a><span data-ttu-id="cac26-186">Argument ValueFromPipelineByPropertyName</span><span class="sxs-lookup"><span data-stu-id="cac26-186">ValueFromPipelineByPropertyName argument</span></span>

<span data-ttu-id="cac26-187">Het `ValueFromPipelineByPropertyName` argument geeft aan dat de parameter invoer accepteert van een eigenschap van een pijplijnobject.</span><span class="sxs-lookup"><span data-stu-id="cac26-187">The `ValueFromPipelineByPropertyName` argument indicates that the parameter accepts input from a property of a pipeline object.</span></span> <span data-ttu-id="cac26-188">De eigenschap object moet dezelfde naam of alias hebben als de parameter .</span><span class="sxs-lookup"><span data-stu-id="cac26-188">The object property must have the same name or alias as the parameter.</span></span>

<span data-ttu-id="cac26-189">Als de functie bijvoorbeeld een parameter **ComputerName** heeft en het object piped een **eigenschap ComputerName** heeft, wordt de waarde van de eigenschap **ComputerName** toegewezen aan de parameter **ComputerName** van de functie.</span><span class="sxs-lookup"><span data-stu-id="cac26-189">For example, if the function has a **ComputerName** parameter, and the piped object has a **ComputerName** property, the value of the **ComputerName** property is assigned to the function's **ComputerName** parameter.</span></span>

<span data-ttu-id="cac26-190">In het volgende voorbeeld wordt een **parameter ComputerName** gedeclareert die verplicht is en invoer accepteert van de **eigenschap ComputerName** van het object die via de pijplijn aan de functie wordt doorgegeven.</span><span class="sxs-lookup"><span data-stu-id="cac26-190">The following example declares a **ComputerName** parameter that's mandatory and accepts input from the object's **ComputerName** property that's passed to the function through the pipeline.</span></span>

```powershell
Param(
    [Parameter(Mandatory=$true,
    ValueFromPipelineByPropertyName=$true)]
    [String[]]
    $ComputerName
)
```

> [!NOTE]
> <span data-ttu-id="cac26-191">Een getypte parameter die pijplijninvoer ( ) of ( ) accepteert, maakt het gebruik van `by Value` `by PropertyName` _scriptblokken voor vertragingsbinding_ op de parameter mogelijk.</span><span class="sxs-lookup"><span data-stu-id="cac26-191">A typed parameter that accepts pipeline input (`by Value`) or (`by PropertyName`) enables use of _delay-bind_ script blocks on the parameter.</span></span>
>
> <span data-ttu-id="cac26-192">Het _scriptblok delay-bind_ wordt automatisch uitgevoerd tijdens **ParameterBinding.**</span><span class="sxs-lookup"><span data-stu-id="cac26-192">The _delay-bind_ script block is run automatically during **ParameterBinding**.</span></span> <span data-ttu-id="cac26-193">Het resultaat is gebonden aan de parameter .</span><span class="sxs-lookup"><span data-stu-id="cac26-193">The result is bound to the parameter.</span></span> <span data-ttu-id="cac26-194">Vertragingsbinding werkt niet voor parameters die zijn gedefinieerd als type `ScriptBlock` of `System.Object` .</span><span class="sxs-lookup"><span data-stu-id="cac26-194">Delay binding does not work for parameters defined as type `ScriptBlock` or `System.Object`.</span></span> <span data-ttu-id="cac26-195">Het scriptblok wordt doorgegeven zonder _dat het_ wordt aangeroepen.</span><span class="sxs-lookup"><span data-stu-id="cac26-195">The script block is passed through _without_ being invoked.</span></span>
>
> <span data-ttu-id="cac26-196">U kunt hier meer lezen _over scriptblokken voor_ vertragingsbinding [about_Script_Blocks.md.](about_Script_Blocks.md)</span><span class="sxs-lookup"><span data-stu-id="cac26-196">You can read about _delay-bind_ script blocks here [about_Script_Blocks.md](about_Script_Blocks.md).</span></span>

#### <a name="valuefromremainingarguments-argument"></a><span data-ttu-id="cac26-197">Argument ValueFromRemainingArguments</span><span class="sxs-lookup"><span data-stu-id="cac26-197">ValueFromRemainingArguments argument</span></span>

<span data-ttu-id="cac26-198">Het argument geeft aan dat de parameter alle waarden van de parameter in de opdracht accepteert die niet zijn toegewezen aan andere `ValueFromRemainingArguments` parameters van de functie.</span><span class="sxs-lookup"><span data-stu-id="cac26-198">The `ValueFromRemainingArguments` argument indicates that the parameter accepts all the parameter's values in the command that aren't assigned to other parameters of the function.</span></span>

<span data-ttu-id="cac26-199">In het volgende  voorbeeld wordt een waardeparameter gedeclareert die verplicht is en een parameter **Remaining** die alle resterende parameterwaarden accepteert die naar de functie worden verzonden.</span><span class="sxs-lookup"><span data-stu-id="cac26-199">The following example declares a **Value** parameter that's mandatory and a **Remaining** parameter that accepts all the remaining parameter values that are submitted to the function.</span></span>

```powershell
function Test-Remainder
{
     param(
         [string]
         [Parameter(Mandatory = $true, Position=0)]
         $Value,
         [string[]]
         [Parameter(Position=1, ValueFromRemainingArguments)]
         $Remaining)
     "Found $($Remaining.Count) elements"
     for ($i = 0; $i -lt $Remaining.Count; $i++)
     {
        "${i}: $($Remaining[$i])"
     }
}
Test-Remainder first one,two
```

```Output
Found 2 elements
0: one
1: two
```

> [!NOTE]
> <span data-ttu-id="cac26-200">Vóór PowerShell 6.2 werd de verzameling **ValueFromRemainingArguments** toegevoegd als één entiteit onder index **0**.</span><span class="sxs-lookup"><span data-stu-id="cac26-200">Prior to PowerShell 6.2, the **ValueFromRemainingArguments** collection was joined as single entity under index **0**.</span></span>

#### <a name="helpmessage-argument"></a><span data-ttu-id="cac26-201">Argument HelpMessage</span><span class="sxs-lookup"><span data-stu-id="cac26-201">HelpMessage argument</span></span>

<span data-ttu-id="cac26-202">Het `HelpMessage` argument geeft een tekenreeks op die een korte beschrijving van de parameter of de waarde ervan bevat.</span><span class="sxs-lookup"><span data-stu-id="cac26-202">The `HelpMessage` argument specifies a string that contains a brief description of the parameter or its value.</span></span> <span data-ttu-id="cac26-203">PowerShell geeft dit bericht weer in de prompt die wordt weergegeven wanneer een verplichte parameterwaarde ontbreekt in een opdracht.</span><span class="sxs-lookup"><span data-stu-id="cac26-203">PowerShell displays this message in the prompt that appears when a mandatory parameter value is missing from a command.</span></span> <span data-ttu-id="cac26-204">Dit argument heeft geen invloed op optionele parameters.</span><span class="sxs-lookup"><span data-stu-id="cac26-204">This argument has no effect on optional parameters.</span></span>

<span data-ttu-id="cac26-205">In het volgende voorbeeld wordt een verplichte **ComputerName-parameter** en een Help-bericht gedeclareert waarin de verwachte parameterwaarde wordt uitgelegd.</span><span class="sxs-lookup"><span data-stu-id="cac26-205">The following example declares a mandatory **ComputerName** parameter and a help message that explains the expected parameter value.</span></span>

<span data-ttu-id="cac26-206">Als er geen andere [helpsyntaxis](./about_comment_based_help.md) op basis van opmerkingen is voor de functie (bijvoorbeeld ) wordt dit bericht `.SYNOPSIS` ook weergegeven in de `Get-Help` uitvoer.</span><span class="sxs-lookup"><span data-stu-id="cac26-206">If there is no other [comment-based help](./about_comment_based_help.md) syntax for the function (for example, `.SYNOPSIS`) then this message also shows up in `Get-Help` output.</span></span>

```powershell
Param(
    [Parameter(Mandatory=$true,
    HelpMessage="Enter one or more computer names separated by commas.")]
    [String[]]
    $ComputerName
)
```

### <a name="alias-attribute"></a><span data-ttu-id="cac26-207">Aliaskenmerk</span><span class="sxs-lookup"><span data-stu-id="cac26-207">Alias attribute</span></span>

<span data-ttu-id="cac26-208">Met **het kenmerk Alias** wordt een alternatieve naam voor de parameter gemaakt.</span><span class="sxs-lookup"><span data-stu-id="cac26-208">The **Alias** attribute establishes an alternate name for the parameter.</span></span>
<span data-ttu-id="cac26-209">Er is geen limiet voor het aantal aliassen dat u aan een parameter kunt toewijzen.</span><span class="sxs-lookup"><span data-stu-id="cac26-209">There's no limit to the number of aliases that you can assign to a parameter.</span></span>

<span data-ttu-id="cac26-210">In het volgende voorbeeld ziet u een parameterdeclaratie die de **aliassen CN** en **MachineName** toevoegt aan de verplichte **parameter ComputerName.**</span><span class="sxs-lookup"><span data-stu-id="cac26-210">The following example shows a parameter declaration that adds the **CN** and **MachineName** aliases to the mandatory **ComputerName** parameter.</span></span>

```powershell
Param(
    [Parameter(Mandatory=$true)]
    [Alias("CN","MachineName")]
    [String[]]
    $ComputerName
)
```

### <a name="supportswildcards-attribute"></a><span data-ttu-id="cac26-211">Ondersteunt het kenmerk SupportsWildcards</span><span class="sxs-lookup"><span data-stu-id="cac26-211">SupportsWildcards attribute</span></span>

<span data-ttu-id="cac26-212">Het **kenmerk SupportsWildcards** wordt gebruikt om aan te geven dat de parameter jokertekenwaarden accepteert.</span><span class="sxs-lookup"><span data-stu-id="cac26-212">The **SupportsWildcards** attribute is used to indicate that the parameter accepts wildcard values.</span></span> <span data-ttu-id="cac26-213">In het volgende voorbeeld ziet u een parameterdeclaratie voor een verplichte **padparameter** die jokertekenwaarden ondersteunt.</span><span class="sxs-lookup"><span data-stu-id="cac26-213">The following example shows a parameter declaration for a mandatory **Path** parameter that supports wildcard values.</span></span>

```powershell
Param(
    [Parameter(Mandatory=$true)]
    [SupportsWildcards()]
    [String[]]
    $Path
)
```

<span data-ttu-id="cac26-214">Als u dit kenmerk gebruikt, wordt ondersteuning voor jokertekens niet automatisch ingeschakeld.</span><span class="sxs-lookup"><span data-stu-id="cac26-214">Using this attribute does not automatically enable wildcard support.</span></span> <span data-ttu-id="cac26-215">De cmdlet-ontwikkelaar moet de code implementeren om de invoer met jokertekens te verwerken.</span><span class="sxs-lookup"><span data-stu-id="cac26-215">The cmdlet developer must implement the code to handle the wildcard input.</span></span> <span data-ttu-id="cac26-216">De ondersteunde jokertekens kunnen variëren afhankelijk van de onderliggende API of PowerShell-provider.</span><span class="sxs-lookup"><span data-stu-id="cac26-216">The wildcards supported can vary according to the underlying API or PowerShell provider.</span></span> <span data-ttu-id="cac26-217">Zie voor meer informatie [about_Wildcards](about_Wildcards.md).</span><span class="sxs-lookup"><span data-stu-id="cac26-217">For more information, see [about_Wildcards](about_Wildcards.md).</span></span>

### <a name="parameter-and-variable-validation-attributes"></a><span data-ttu-id="cac26-218">Parameter- en variabelevalidatiekenmerken</span><span class="sxs-lookup"><span data-stu-id="cac26-218">Parameter and variable validation attributes</span></span>

<span data-ttu-id="cac26-219">Validatiekenmerken zorgen ervoor dat PowerShell de parameterwaarden test die gebruikers verzenden wanneer ze de geavanceerde functie aanroepen.</span><span class="sxs-lookup"><span data-stu-id="cac26-219">Validation attributes direct PowerShell to test the parameter values that users submit when they call the advanced function.</span></span> <span data-ttu-id="cac26-220">Als de parameterwaarden mislukken voor de test, wordt er een fout gegenereerd en wordt de functie niet aangeroepen.</span><span class="sxs-lookup"><span data-stu-id="cac26-220">If the parameter values fail the test, an error is generated and the function isn't called.</span></span> <span data-ttu-id="cac26-221">Parametervalidatie wordt alleen toegepast op de opgegeven invoer en andere waarden, zoals standaardwaarden, worden niet gevalideerd.</span><span class="sxs-lookup"><span data-stu-id="cac26-221">Parameter validation is only applied to the input provided and any other values like default values are not validated.</span></span>

<span data-ttu-id="cac26-222">U kunt ook de validatiekenmerken gebruiken om de waarden te beperken die gebruikers voor variabelen kunnen opgeven.</span><span class="sxs-lookup"><span data-stu-id="cac26-222">You can also use the validation attributes to restrict the values that users can specify for variables.</span></span> <span data-ttu-id="cac26-223">Wanneer u een typeconverter gebruikt samen met een validatiekenmerk, moet de typeconverter worden gedefinieerd vóór het kenmerk .</span><span class="sxs-lookup"><span data-stu-id="cac26-223">When you use a type converter along with a validation attribute, the type converter has to be defined before the attribute.</span></span>

```powershell
[int32][AllowNull()] $number = 7
```

### <a name="allownull-validation-attribute"></a><span data-ttu-id="cac26-224">AllowNull-validatiekenmerk</span><span class="sxs-lookup"><span data-stu-id="cac26-224">AllowNull validation attribute</span></span>

<span data-ttu-id="cac26-225">Met **het kenmerk AllowNull** kan de waarde van een verplichte parameter `$null` zijn.</span><span class="sxs-lookup"><span data-stu-id="cac26-225">The **AllowNull** attribute allows the value of a mandatory parameter to be `$null`.</span></span> <span data-ttu-id="cac26-226">In het volgende voorbeeld wordt een **computerinfoparameter met hashtabel** gedeclareert die een **null-waarde kan** hebben.</span><span class="sxs-lookup"><span data-stu-id="cac26-226">The following example declares a hashtable **ComputerInfo** parameter that can have a **null** value.</span></span>

```powershell
Param(
    [Parameter(Mandatory=$true)]
    [AllowNull()]
    [hashtable]
    $ComputerInfo
)
```

> [!NOTE]
> <span data-ttu-id="cac26-227">Het **kenmerk AllowNull** werkt niet als de typeconverter is ingesteld op tekenreeks omdat het tekenreekstype geen null-waarde accepteert.</span><span class="sxs-lookup"><span data-stu-id="cac26-227">The **AllowNull** attribute doesn't work if the type converter is set to string as the string type will not accept a null value.</span></span> <span data-ttu-id="cac26-228">U kunt het **kenmerk AllowEmptyString gebruiken** voor dit scenario.</span><span class="sxs-lookup"><span data-stu-id="cac26-228">You can use the **AllowEmptyString** attribute for this scenario.</span></span>

### <a name="allowemptystring-validation-attribute"></a><span data-ttu-id="cac26-229">Validatiekenmerk AllowEmptyString</span><span class="sxs-lookup"><span data-stu-id="cac26-229">AllowEmptyString validation attribute</span></span>

<span data-ttu-id="cac26-230">Met **het kenmerk AllowEmptyString** kan de waarde van een verplichte parameter een lege tekenreeks ( ) `""` zijn.</span><span class="sxs-lookup"><span data-stu-id="cac26-230">The **AllowEmptyString** attribute allows the value of a mandatory parameter to be an empty string (`""`).</span></span> <span data-ttu-id="cac26-231">In het volgende voorbeeld wordt een **parameter ComputerName gedeclareert** die een lege tekenreekswaarde kan hebben.</span><span class="sxs-lookup"><span data-stu-id="cac26-231">The following example declares a **ComputerName** parameter that can have an empty string value.</span></span>

```powershell
Param(
    [Parameter(Mandatory=$true)]
    [AllowEmptyString()]
    [String]
    $ComputerName
)
```

### <a name="allowemptycollection-validation-attribute"></a><span data-ttu-id="cac26-232">Validatiekenmerk AllowEmptyCollection</span><span class="sxs-lookup"><span data-stu-id="cac26-232">AllowEmptyCollection validation attribute</span></span>

<span data-ttu-id="cac26-233">Met **het kenmerk AllowEmptyCollection** kan de waarde van een verplichte parameter een lege verzameling `@()` zijn.</span><span class="sxs-lookup"><span data-stu-id="cac26-233">The **AllowEmptyCollection** attribute allows the value of a mandatory parameter to be an empty collection `@()`.</span></span> <span data-ttu-id="cac26-234">In het volgende voorbeeld wordt een **parameter ComputerName gedeclareert** die een lege verzamelingswaarde kan hebben.</span><span class="sxs-lookup"><span data-stu-id="cac26-234">The following example declares a **ComputerName** parameter that can have an empty collection value.</span></span>

```powershell
Param(
    [Parameter(Mandatory=$true)]
    [AllowEmptyCollection()]
    [String[]]
    $ComputerName
)
```

### <a name="validatecount-validation-attribute"></a><span data-ttu-id="cac26-235">Validatiekenmerk ValidateCount</span><span class="sxs-lookup"><span data-stu-id="cac26-235">ValidateCount validation attribute</span></span>

<span data-ttu-id="cac26-236">Het **kenmerk ValidateCount** geeft het minimum- en maximum aantal parameterwaarden aan dat een parameter accepteert.</span><span class="sxs-lookup"><span data-stu-id="cac26-236">The **ValidateCount** attribute specifies the minimum and maximum number of parameter values that a parameter accepts.</span></span> <span data-ttu-id="cac26-237">PowerShell genereert een fout als het aantal parameterwaarden in de opdracht die de functie aanroept, buiten dat bereik ligt.</span><span class="sxs-lookup"><span data-stu-id="cac26-237">PowerShell generates an error if the number of parameter values in the command that calls the function is outside that range.</span></span>

<span data-ttu-id="cac26-238">Met de volgende parameterdeclaratie maakt u **een ComputerName-parameter** die één tot vijf parameterwaarden nodig heeft.</span><span class="sxs-lookup"><span data-stu-id="cac26-238">The following parameter declaration creates a **ComputerName** parameter that takes one to five parameter values.</span></span>

```powershell
Param(
    [Parameter(Mandatory=$true)]
    [ValidateCount(1,5)]
    [String[]]
    $ComputerName
)
```

### <a name="validatelength-validation-attribute"></a><span data-ttu-id="cac26-239">Validatiekenmerk ValidateLength</span><span class="sxs-lookup"><span data-stu-id="cac26-239">ValidateLength validation attribute</span></span>

<span data-ttu-id="cac26-240">Het **kenmerk ValidateLength** specificeert het minimum- en maximumaantal tekens in een parameter of variabele waarde.</span><span class="sxs-lookup"><span data-stu-id="cac26-240">The **ValidateLength** attribute specifies the minimum and maximum number of characters in a parameter or variable value.</span></span> <span data-ttu-id="cac26-241">PowerShell genereert een fout als de lengte van een waarde die is opgegeven voor een parameter of een variabele buiten het bereik valt.</span><span class="sxs-lookup"><span data-stu-id="cac26-241">PowerShell generates an error if the length of a value specified for a parameter or a variable is outside of the range.</span></span>

<span data-ttu-id="cac26-242">In het volgende voorbeeld moet elke computernaam één tot tien tekens bevatten.</span><span class="sxs-lookup"><span data-stu-id="cac26-242">In the following example, each computer name must have one to ten characters.</span></span>

```powershell
Param(
    [Parameter(Mandatory=$true)]
    [ValidateLength(1,10)]
    [String[]]
    $ComputerName
)
```

<span data-ttu-id="cac26-243">In het volgende voorbeeld moet de waarde van de variabele minimaal één teken lang en maximaal tien `$number` tekens zijn.</span><span class="sxs-lookup"><span data-stu-id="cac26-243">In the following example, the value of the variable `$number` must be a minimum of one character in length, and a maximum of ten characters.</span></span>

```powershell
[Int32][ValidateLength(1,10)]$number = '01'
```

> [!NOTE]
> <span data-ttu-id="cac26-244">In dit voorbeeld wordt de waarde van `01` tussen enkele aanhalingstekens verpakt.</span><span class="sxs-lookup"><span data-stu-id="cac26-244">In this example, the value of `01` is wrapped in single quotes.</span></span> <span data-ttu-id="cac26-245">Het **kenmerk ValidateLength** accepteert geen getal zonder tussen aanhalingstekens te worden verpakt.</span><span class="sxs-lookup"><span data-stu-id="cac26-245">The **ValidateLength** attribute won't accept a number without being wrapped in quotes.</span></span>

### <a name="validatepattern-validation-attribute"></a><span data-ttu-id="cac26-246">Validatiekenmerk ValidatePattern</span><span class="sxs-lookup"><span data-stu-id="cac26-246">ValidatePattern validation attribute</span></span>

<span data-ttu-id="cac26-247">Het **kenmerk ValidatePattern** geeft een reguliere expressie op die wordt vergeleken met de parameter of variabele waarde.</span><span class="sxs-lookup"><span data-stu-id="cac26-247">The **ValidatePattern** attribute specifies a regular expression that's compared to the parameter or variable value.</span></span> <span data-ttu-id="cac26-248">PowerShell genereert een fout als de waarde niet overeen komt met het patroon van de reguliere expressie.</span><span class="sxs-lookup"><span data-stu-id="cac26-248">PowerShell generates an error if the value doesn't match the regular expression pattern.</span></span>

<span data-ttu-id="cac26-249">In het volgende voorbeeld moet de parameterwaarde een viercijferig getal bevatten en moet elk cijfer een getal van nul tot negen zijn.</span><span class="sxs-lookup"><span data-stu-id="cac26-249">In the following example, the parameter value must contain a four-digit number, and each digit must be a number zero to nine.</span></span>

```powershell
Param(
    [Parameter(Mandatory=$true)]
    [ValidatePattern("[0-9][0-9][0-9][0-9]")]
    [String[]]
    $ComputerName
)
```

<span data-ttu-id="cac26-250">In het volgende voorbeeld moet de waarde van de variabele exact een getal van vier cijfers zijn en moet elk cijfer een getal nul tot `$number` negen zijn.</span><span class="sxs-lookup"><span data-stu-id="cac26-250">In the following example, the value of the variable `$number` must be exactly a four-digit number, and each digit must be a number zero to nine.</span></span>

```powershell
[Int32][ValidatePattern("^[0-9][0-9][0-9][0-9]$")]$number = 1111
```

### <a name="validaterange-validation-attribute"></a><span data-ttu-id="cac26-251">Validatiekenmerk ValidateRange</span><span class="sxs-lookup"><span data-stu-id="cac26-251">ValidateRange validation attribute</span></span>

<span data-ttu-id="cac26-252">Het **kenmerk ValidateRange** geeft een numeriek bereik of een **validateRangeKind-enumwaarde** op voor elke parameter of variabele waarde.</span><span class="sxs-lookup"><span data-stu-id="cac26-252">The **ValidateRange** attribute specifies a numeric range or a **ValidateRangeKind** enum value for each parameter or variable value.</span></span>
<span data-ttu-id="cac26-253">PowerShell genereert een fout als een waarde buiten dat bereik valt.</span><span class="sxs-lookup"><span data-stu-id="cac26-253">PowerShell generates an error if any value is outside that range.</span></span>

<span data-ttu-id="cac26-254">De **enum ValidateRangeKind** staat de volgende waarden toe:</span><span class="sxs-lookup"><span data-stu-id="cac26-254">The **ValidateRangeKind** enum allows for the following values:</span></span>

- <span data-ttu-id="cac26-255">**Positief:** een getal dat groter is dan nul.</span><span class="sxs-lookup"><span data-stu-id="cac26-255">**Positive** - A number greater than zero.</span></span>
- <span data-ttu-id="cac26-256">**Negatief:** een getal dat kleiner is dan nul.</span><span class="sxs-lookup"><span data-stu-id="cac26-256">**Negative** - A number less than zero.</span></span>
- <span data-ttu-id="cac26-257">**Niet-gevoelig:** een getal dat kleiner is dan of gelijk is aan nul.</span><span class="sxs-lookup"><span data-stu-id="cac26-257">**NonPositive** - A number less than or equal to zero.</span></span>
- <span data-ttu-id="cac26-258">**Niet-nul:** een getal dat groter is dan of gelijk is aan nul.</span><span class="sxs-lookup"><span data-stu-id="cac26-258">**NonNegative** - A number greater than or equal to zero.</span></span>

<span data-ttu-id="cac26-259">In het volgende voorbeeld moet de waarde van de parameter **Attempts** tussen nul en tien zijn.</span><span class="sxs-lookup"><span data-stu-id="cac26-259">In the following example, the value of the **Attempts** parameter must be between zero and ten.</span></span>

```powershell
Param(
    [Parameter(Mandatory=$true)]
    [ValidateRange(0,10)]
    [Int]
    $Attempts
)
```

<span data-ttu-id="cac26-260">In het volgende voorbeeld moet de waarde van de variabele `$number` tussen nul en tien zijn.</span><span class="sxs-lookup"><span data-stu-id="cac26-260">In the following example, the value of the variable `$number` must be between zero and ten.</span></span>

```powershell
[Int32][ValidateRange(0,10)]$number = 5
```

<span data-ttu-id="cac26-261">In het volgende voorbeeld moet de waarde van de `$number` variabele groter zijn dan nul.</span><span class="sxs-lookup"><span data-stu-id="cac26-261">In the following example, the value of the variable `$number` must be greater than zero.</span></span>

```powershell
[Int32][ValidateRange("Positive")]$number = 1
```

### <a name="validatescript-validation-attribute"></a><span data-ttu-id="cac26-262">Validatiekenmerk ValidateScript</span><span class="sxs-lookup"><span data-stu-id="cac26-262">ValidateScript validation attribute</span></span>

<span data-ttu-id="cac26-263">Het **kenmerk ValidateScript** bevat een script dat wordt gebruikt om een parameter of variabele waarde te valideren.</span><span class="sxs-lookup"><span data-stu-id="cac26-263">The **ValidateScript** attribute specifies a script that is used to validate a parameter or variable value.</span></span> <span data-ttu-id="cac26-264">PowerShell geeft de waarde door aan het script en genereert een fout als het script retourneert of als het `$false` script een uitzondering genereert.</span><span class="sxs-lookup"><span data-stu-id="cac26-264">PowerShell pipes the value to the script, and generates an error if the script returns `$false` or if the script throws an exception.</span></span>

<span data-ttu-id="cac26-265">Wanneer u het **kenmerk ValidateScript** gebruikt, wordt de waarde die wordt gevalideerd, aan de variabele `$_` weergegeven.</span><span class="sxs-lookup"><span data-stu-id="cac26-265">When you use the **ValidateScript** attribute, the value that's being validated is mapped to the `$_` variable.</span></span> <span data-ttu-id="cac26-266">U kunt de variabele `$_` gebruiken om te verwijzen naar de waarde in het script.</span><span class="sxs-lookup"><span data-stu-id="cac26-266">You can use the `$_` variable to refer to the value in the script.</span></span>

<span data-ttu-id="cac26-267">In het volgende voorbeeld moet de waarde van de parameter **EventDate** groter zijn dan of gelijk zijn aan de huidige datum.</span><span class="sxs-lookup"><span data-stu-id="cac26-267">In the following example, the value of the **EventDate** parameter must be greater than or equal to the current date.</span></span>

```powershell
Param(
    [Parameter(Mandatory=$true)]
    [ValidateScript({$_ -ge (Get-Date)})]
    [DateTime]
    $EventDate
)
```

<span data-ttu-id="cac26-268">In het volgende voorbeeld moet de waarde van de variabele groter zijn dan of gelijk `$date` zijn aan de huidige datum en tijd.</span><span class="sxs-lookup"><span data-stu-id="cac26-268">In the following example, the value of the variable `$date` must be greater than or equal to the current date and time.</span></span>

```powershell
[DateTime][ValidateScript({$_ -ge (Get-Date)})]$date = (Get-Date)
```

> [!NOTE]
> <span data-ttu-id="cac26-269">Als u **ValidateScript gebruikt,** kunt u geen waarde `$null` aan de parameter doorgeven.</span><span class="sxs-lookup"><span data-stu-id="cac26-269">If you use **ValidateScript**, you cannot pass a `$null` value to the parameter.</span></span> <span data-ttu-id="cac26-270">Wanneer u een null-waarde door **te geven, kan ValidateScript** het argument niet valideren.</span><span class="sxs-lookup"><span data-stu-id="cac26-270">When you pass a null value **ValidateScript** can't validate the argument.</span></span>

### <a name="validateset-attribute"></a><span data-ttu-id="cac26-271">ValidateSet-kenmerk</span><span class="sxs-lookup"><span data-stu-id="cac26-271">ValidateSet attribute</span></span>

<span data-ttu-id="cac26-272">Het **kenmerk ValidateSet** specificeert een set geldige waarden voor een parameter of variabele en maakt tab-voltooiing mogelijk.</span><span class="sxs-lookup"><span data-stu-id="cac26-272">The **ValidateSet** attribute specifies a set of valid values for a parameter or variable and enables tab completion.</span></span> <span data-ttu-id="cac26-273">PowerShell genereert een fout als een parameter of variabele waarde niet overeen komt met een waarde in de set.</span><span class="sxs-lookup"><span data-stu-id="cac26-273">PowerShell generates an error if a parameter or variable value doesn't match a value in the set.</span></span> <span data-ttu-id="cac26-274">In het volgende voorbeeld kan de waarde van de parameter **Details** alleen Laag, Gemiddeld of Hoog zijn.</span><span class="sxs-lookup"><span data-stu-id="cac26-274">In the following example, the value of the **Detail** parameter can only be Low, Average, or High.</span></span>

```powershell
Param(
    [Parameter(Mandatory=$true)]
    [ValidateSet("Low", "Average", "High")]
    [String[]]
    $Detail
)
```

<span data-ttu-id="cac26-275">In het volgende voorbeeld moet de waarde van de variabele Chocolade, Aardbeien of `$flavor` Vanille zijn.</span><span class="sxs-lookup"><span data-stu-id="cac26-275">In the following example, the value of the variable `$flavor` must be either Chocolate, Strawberry, or Vanilla.</span></span>

```powershell
[ValidateSet("Chocolate", "Strawberry", "Vanilla")]
[String]$flavor = "Strawberry"
```

<span data-ttu-id="cac26-276">De validatie vindt plaats wanneer die variabele zelfs binnen het script wordt toegewezen.</span><span class="sxs-lookup"><span data-stu-id="cac26-276">The validation occurs whenever that variable is assigned even within the script.</span></span> <span data-ttu-id="cac26-277">Het volgende resulteert bijvoorbeeld in een fout tijdens runtime:</span><span class="sxs-lookup"><span data-stu-id="cac26-277">For example, the following results in an error at runtime:</span></span>

```powershell
Param(
    [ValidateSet("hello", "world")]
    [String]$Message
)

$Message = "bye"
```

#### <a name="dynamic-validateset-values"></a><span data-ttu-id="cac26-278">Dynamische validateSet-waarden</span><span class="sxs-lookup"><span data-stu-id="cac26-278">Dynamic validateSet values</span></span>

<span data-ttu-id="cac26-279">U kunt een klasse **gebruiken om** de waarden voor **ValidateSet** dynamisch te genereren tijdens runtime.</span><span class="sxs-lookup"><span data-stu-id="cac26-279">You can use a **Class** to dynamically generate the values for **ValidateSet** at runtime.</span></span> <span data-ttu-id="cac26-280">In het volgende voorbeeld worden de geldige waarden voor de variabele gegenereerd via een klasse met de naam SoundNames die drie bestandssysteempaden controleert op `$Sound` beschikbare geluidsbestanden:  </span><span class="sxs-lookup"><span data-stu-id="cac26-280">In the following example, the valid values for the variable `$Sound` are generated via a **Class** named **SoundNames** that checks three filesystem paths for available sound files:</span></span>

```powershell
Class SoundNames : System.Management.Automation.IValidateSetValuesGenerator {
    [String[]] GetValidValues() {
        $SoundPaths = '/System/Library/Sounds/',
            '/Library/Sounds','~/Library/Sounds'
        $SoundNames = ForEach ($SoundPath in $SoundPaths) {
            If (Test-Path $SoundPath) {
                (Get-ChildItem $SoundPath).BaseName
            }
        }
        return [String[]] $SoundNames
    }
}
```

<span data-ttu-id="cac26-281">De klasse wordt vervolgens als volgt geïmplementeerd als een dynamische `[SoundNames]` **ValidateSet-waarde:**</span><span class="sxs-lookup"><span data-stu-id="cac26-281">The `[SoundNames]` class is then implemented as a dynamic **ValidateSet** value as follows:</span></span>

```powershell
Param(
    [ValidateSet([SoundNames])]
    [String]$Sound
)
```

> [!NOTE]
> <span data-ttu-id="cac26-282">De `IValidateSetValuesGenerator` klasse is geïntroduceerd in PowerShell 6.0</span><span class="sxs-lookup"><span data-stu-id="cac26-282">The `IValidateSetValuesGenerator` class was introduced in PowerShell 6.0</span></span>

### <a name="validatenotnull-validation-attribute"></a><span data-ttu-id="cac26-283">Validatiekenmerk ValidateNotNull</span><span class="sxs-lookup"><span data-stu-id="cac26-283">ValidateNotNull validation attribute</span></span>

<span data-ttu-id="cac26-284">Het **kenmerk ValidateNotNull** geeft aan dat de parameterwaarde niet mag `$null` zijn.</span><span class="sxs-lookup"><span data-stu-id="cac26-284">The **ValidateNotNull** attribute specifies that the parameter value can't be `$null`.</span></span> <span data-ttu-id="cac26-285">PowerShell genereert een fout als de parameterwaarde `$null` is.</span><span class="sxs-lookup"><span data-stu-id="cac26-285">PowerShell generates an error if the parameter value is `$null`.</span></span>

<span data-ttu-id="cac26-286">Het **kenmerk ValidateNotNull** is ontworpen om te worden gebruikt wanneer de parameter optioneel is en het type niet is gedefinieerd of een typeconverter heeft die een null-waarde zoals object niet impliciet kan **converteren.**</span><span class="sxs-lookup"><span data-stu-id="cac26-286">The **ValidateNotNull** attribute is designed to be used when the parameter is optional and the type is undefined or has a type converter that can't implicitly convert a null value like **object**.</span></span> <span data-ttu-id="cac26-287">Als u een type opgeeft dat impliciet een null-waarde converteert, zoals een tekenreeks, wordt de null-waarde geconverteerd naar een lege tekenreeks, zelfs wanneer u het kenmerk **ValidateNotNull** gebruikt.</span><span class="sxs-lookup"><span data-stu-id="cac26-287">If you specify a type that that will implicitly convert a null value such as a **string**, the null value is converted to an empty string even when using the **ValidateNotNull** attribute.</span></span> <span data-ttu-id="cac26-288">Gebruik voor dit scenario **validateNotNullOrEmpty**</span><span class="sxs-lookup"><span data-stu-id="cac26-288">For this scenario use the **ValidateNotNullOrEmpty**</span></span>

<span data-ttu-id="cac26-289">In het volgende voorbeeld mag de waarde van de **id-parameter** niet `$null` zijn.</span><span class="sxs-lookup"><span data-stu-id="cac26-289">In the following example, the value of the **ID** parameter can't be `$null`.</span></span>

```powershell
Param(
    [Parameter(Mandatory=$false)]
    [ValidateNotNull()]
    $ID
)
```

### <a name="validatenotnullorempty-validation-attribute"></a><span data-ttu-id="cac26-290">Validatiekenmerk ValidateNotNullOrEmpty</span><span class="sxs-lookup"><span data-stu-id="cac26-290">ValidateNotNullOrEmpty validation attribute</span></span>

<span data-ttu-id="cac26-291">Het **kenmerk ValidateNotNullOrEmpty** geeft aan dat de parameterwaarde niet mag zijn en geen lege `$null` tekenreeks () mag `""` zijn.</span><span class="sxs-lookup"><span data-stu-id="cac26-291">The **ValidateNotNullOrEmpty** attribute specifies that the parameter value can't be `$null` and can't be an empty string (`""`).</span></span> <span data-ttu-id="cac26-292">PowerShell genereert een fout als de parameter wordt gebruikt in een functie-aanroep, maar de waarde ervan is , een lege tekenreeks `$null` ( ) of een lege matrix `""` `@()` .</span><span class="sxs-lookup"><span data-stu-id="cac26-292">PowerShell generates an error if the parameter is used in a function call, but its value is `$null`, an empty string (`""`), or an empty array `@()`.</span></span>

```powershell
Param(
    [Parameter(Mandatory=$true)]
    [ValidateNotNullOrEmpty()]
    [String[]]
    $UserName
)
```

### <a name="validatedrive-validation-attribute"></a><span data-ttu-id="cac26-293">Validatiekenmerk ValidateDrive</span><span class="sxs-lookup"><span data-stu-id="cac26-293">ValidateDrive validation attribute</span></span>

<span data-ttu-id="cac26-294">Het **kenmerk ValidateDrive** geeft aan dat de parameterwaarde het pad moet vertegenwoordigen, dat alleen verwijst naar toegestane stations.</span><span class="sxs-lookup"><span data-stu-id="cac26-294">The **ValidateDrive** attribute specifies that the parameter value must represent the path, that's referring to allowed drives only.</span></span> <span data-ttu-id="cac26-295">PowerShell genereert een fout als de parameterwaarde verwijst naar andere stations dan de toegestane.</span><span class="sxs-lookup"><span data-stu-id="cac26-295">PowerShell generates an error if the parameter value refers to drives other than the allowed.</span></span> <span data-ttu-id="cac26-296">Het bestaan van het pad, met uitzondering van het station zelf, wordt niet geverifieerd.</span><span class="sxs-lookup"><span data-stu-id="cac26-296">Existence of the path, except for the drive itself, isn't verified.</span></span>

<span data-ttu-id="cac26-297">Als u een relatief pad gebruikt, moet het huidige station in de lijst met toegestane station.</span><span class="sxs-lookup"><span data-stu-id="cac26-297">If you use relative path, the current drive must be in the allowed drive list.</span></span>

```powershell
Param(
    [ValidateDrive("C", "D", "Variable", "Function")]
    [String]$Path
)
```

### <a name="validateuserdrive-validation-attribute"></a><span data-ttu-id="cac26-298">Validatiekenmerk ValidateUserDrive</span><span class="sxs-lookup"><span data-stu-id="cac26-298">ValidateUserDrive validation attribute</span></span>

<span data-ttu-id="cac26-299">Het **kenmerk ValidateUserDrive** geeft aan dat de parameterwaarde het pad moet vertegenwoordigen, dat verwijst naar `User` station.</span><span class="sxs-lookup"><span data-stu-id="cac26-299">The **ValidateUserDrive** attribute specifies that the parameter value must represent the path, that is referring to `User` drive.</span></span> <span data-ttu-id="cac26-300">PowerShell genereert een fout als het pad naar een ander station verwijst.</span><span class="sxs-lookup"><span data-stu-id="cac26-300">PowerShell generates an error if the path refers to a different drive.</span></span> <span data-ttu-id="cac26-301">Het validatiekenmerk test alleen of het stationgedeelte van het pad bestaat.</span><span class="sxs-lookup"><span data-stu-id="cac26-301">The validation attribute only tests for the existence of the drive portion of the path.</span></span>

<span data-ttu-id="cac26-302">Als u een relatief pad gebruikt, moet het huidige station `User` zijn.</span><span class="sxs-lookup"><span data-stu-id="cac26-302">If you use relative path, the current drive must be `User`.</span></span>

```powershell
function Test-UserDrivePath{
    [OutputType([bool])]
    Param(
      [Parameter(Mandatory=, Position=0)][ValidateUserDrive()][String]$Path
      )
    $True
}

Test-UserDrivePath -Path C:\
```

```Output
Test-UserDrivePath: Cannot validate argument on parameter 'Path'. The path
argument drive C does not belong to the set of approved drives: User.
Supply a path argument with an approved drive.
```

```powershell
Test-UserDrivePath -Path 'User:\A_folder_that_does_not_exist'
```

```Output
Test-UserDrivePath: Cannot validate argument on parameter 'Path'. Cannot
find drive. A drive with the name 'User' does not exist.
```

<span data-ttu-id="cac26-303">U kunt station `User` definiëren in JEA-sessieconfiguraties (Just Enough Administration).</span><span class="sxs-lookup"><span data-stu-id="cac26-303">You can define `User` drive in Just Enough Administration (JEA) session configurations.</span></span> <span data-ttu-id="cac26-304">Voor dit voorbeeld maken we het station Gebruiker: .</span><span class="sxs-lookup"><span data-stu-id="cac26-304">For this example, we create the User: drive.</span></span>

```powershell
New-PSDrive -Name 'User' -PSProvider FileSystem -Root $env:HOMEPATH
```

```Output
Name           Used (GB)     Free (GB) Provider      Root
----           ---------     --------- --------      ----
User               75.76         24.24 FileSystem    C:\Users\ExampleUser

```powershell
Test-UserDrivePath -Path 'User:\A_folder_that_does_not_exist'
```

```Output
True
```

### <a name="validatetrusteddata-validation-attribute"></a><span data-ttu-id="cac26-305">Validatiekenmerk ValidateTrustedData</span><span class="sxs-lookup"><span data-stu-id="cac26-305">ValidateTrustedData validation attribute</span></span>

<span data-ttu-id="cac26-306">Dit kenmerk is toegevoegd in PowerShell 6.1.1.</span><span class="sxs-lookup"><span data-stu-id="cac26-306">This attribute was added in PowerShell 6.1.1.</span></span>

<span data-ttu-id="cac26-307">Op dit moment wordt het kenmerk intern gebruikt door PowerShell zelf en is het niet bedoeld voor extern gebruik.</span><span class="sxs-lookup"><span data-stu-id="cac26-307">At this time, the attribute is used internally by PowerShell itself and is not intended for external usage.</span></span>

## <a name="dynamic-parameters"></a><span data-ttu-id="cac26-308">Dynamische parameters</span><span class="sxs-lookup"><span data-stu-id="cac26-308">Dynamic parameters</span></span>

<span data-ttu-id="cac26-309">Dynamische parameters zijn parameters van een cmdlet, functie of script die alleen onder bepaalde voorwaarden beschikbaar zijn.</span><span class="sxs-lookup"><span data-stu-id="cac26-309">Dynamic parameters are parameters of a cmdlet, function, or script that are available only under certain conditions.</span></span>

<span data-ttu-id="cac26-310">Zo hebben verschillende provider-cmdlets parameters die alleen beschikbaar zijn wanneer de cmdlet wordt gebruikt in het providerstation of in een bepaald pad van het providerstation.</span><span class="sxs-lookup"><span data-stu-id="cac26-310">For example, several provider cmdlets have parameters that are available only when the cmdlet is used in the provider drive, or in a particular path of the provider drive.</span></span> <span data-ttu-id="cac26-311">De parameter **Encoding** is bijvoorbeeld alleen beschikbaar op de cmdlets , en wanneer deze worden gebruikt `Add-Content` `Get-Content` in een `Set-Content` bestandssysteemstation.</span><span class="sxs-lookup"><span data-stu-id="cac26-311">For example, the **Encoding** parameter is available on the `Add-Content`, `Get-Content`, and `Set-Content` cmdlets only when it's used in a file system drive.</span></span>

<span data-ttu-id="cac26-312">U kunt ook een parameter maken die alleen wordt weergegeven wanneer een andere parameter wordt gebruikt in de functieopdracht of wanneer een andere parameter een bepaalde waarde heeft.</span><span class="sxs-lookup"><span data-stu-id="cac26-312">You can also create a parameter that appears only when another parameter is used in the function command or when another parameter has a certain value.</span></span>

<span data-ttu-id="cac26-313">Dynamische parameters kunnen nuttig zijn, maar ze alleen gebruiken wanneer dat nodig is, omdat ze moeilijk te ontdekken zijn voor gebruikers.</span><span class="sxs-lookup"><span data-stu-id="cac26-313">Dynamic parameters can be useful, but use them only when necessary, because they can be difficult for users to discover.</span></span> <span data-ttu-id="cac26-314">Als u een dynamische parameter wilt vinden, moet de gebruiker zich in het pad van de provider, de parameter **ArgumentList** van de `Get-Command` cmdlet gebruiken of de parameter **Path** van `Get-Help` gebruiken.</span><span class="sxs-lookup"><span data-stu-id="cac26-314">To find a dynamic parameter, the user must be in the provider path, use the **ArgumentList** parameter of the `Get-Command` cmdlet, or use the **Path** parameter of `Get-Help`.</span></span>

<span data-ttu-id="cac26-315">Gebruik het trefwoord om een dynamische parameter voor een functie of script `DynamicParam` te maken.</span><span class="sxs-lookup"><span data-stu-id="cac26-315">To create a dynamic parameter for a function or script, use the `DynamicParam` keyword.</span></span>

<span data-ttu-id="cac26-316">De syntaxis is als volgt:</span><span class="sxs-lookup"><span data-stu-id="cac26-316">The syntax is as follows:</span></span>

`DynamicParam {<statement-list>}`

<span data-ttu-id="cac26-317">Gebruik in de lijst met -instructie een `If` -instructie om de voorwaarden op te geven waaronder de parameter beschikbaar is in de functie .</span><span class="sxs-lookup"><span data-stu-id="cac26-317">In the statement list, use an `If` statement to specify the conditions under which the parameter is available in the function.</span></span>

<span data-ttu-id="cac26-318">Gebruik de `New-Object` cmdlet om een **System.Management.Automation.RuntimeDefinedParameter-object** te maken dat de parameter vertegenwoordigt en de naam opgeeft.</span><span class="sxs-lookup"><span data-stu-id="cac26-318">Use the `New-Object` cmdlet to create a **System.Management.Automation.RuntimeDefinedParameter** object to represent the parameter and specify its name.</span></span>

<span data-ttu-id="cac26-319">U kunt een opdracht gebruiken om een `New-Object` **System.Management.Automation.ParameterAttribute-object** te maken om kenmerken van de parameter weer te geven, zoals **Verplicht**, **Positie** of **ValueFromPipeline** of de parameterset.</span><span class="sxs-lookup"><span data-stu-id="cac26-319">You can use a `New-Object` command to create a **System.Management.Automation.ParameterAttribute** object to represent attributes of the parameter, such as **Mandatory**, **Position**, or **ValueFromPipeline** or its parameter set.</span></span>

<span data-ttu-id="cac26-320">In het volgende voorbeeld ziet u een voorbeeldfunctie met standaardparameters met de naam **Naam** en **Pad** en een optionele dynamische parameter met de **naam DP1.**</span><span class="sxs-lookup"><span data-stu-id="cac26-320">The following example shows a sample function with standard parameters named **Name** and **Path**, and an optional dynamic parameter named **DP1**.</span></span> <span data-ttu-id="cac26-321">De **parameter DP1** staat in de `PSet1` parameterset en heeft het type `Int32` .</span><span class="sxs-lookup"><span data-stu-id="cac26-321">The **DP1** parameter is in the `PSet1` parameter set and has a type of `Int32`.</span></span>
<span data-ttu-id="cac26-322">De **DP1** parameter is alleen beschikbaar in de functie wanneer de waarde van de pad parameter begint met , waarmee wordt aangegeven dat deze wordt gebruikt `Get-Sample` in het  `HKLM:` `HKEY_LOCAL_MACHINE` registerstation.</span><span class="sxs-lookup"><span data-stu-id="cac26-322">The **DP1** parameter is available in the `Get-Sample` function only when the value of the **Path** parameter starts with `HKLM:`, indicating that it's being used in the `HKEY_LOCAL_MACHINE` registry drive.</span></span>

```powershell
function Get-Sample {
  [CmdletBinding()]
  Param([String]$Name, [String]$Path)

  DynamicParam
  {
    if ($Path.StartsWith("HKLM:"))
    {
      $attributes = New-Object -Type `
        System.Management.Automation.ParameterAttribute
      $attributes.ParameterSetName = "PSet1"
      $attributes.Mandatory = $false
      $attributeCollection = New-Object `
        -Type System.Collections.ObjectModel.Collection[System.Attribute]
      $attributeCollection.Add($attributes)

      $dynParam1 = New-Object -Type `
        System.Management.Automation.RuntimeDefinedParameter("DP1", [Int32],
          $attributeCollection)

      $paramDictionary = New-Object `
        -Type System.Management.Automation.RuntimeDefinedParameterDictionary
      $paramDictionary.Add("DP1", $dynParam1)
      return $paramDictionary
    }
  }
}
```

<span data-ttu-id="cac26-323">Zie [RuntimeDefinedParameter voor meer informatie.](/dotnet/api/system.management.automation.runtimedefinedparameter)</span><span class="sxs-lookup"><span data-stu-id="cac26-323">For more information, see [RuntimeDefinedParameter](/dotnet/api/system.management.automation.runtimedefinedparameter).</span></span>

## <a name="switch-parameters"></a><span data-ttu-id="cac26-324">Schakelen tussen parameters</span><span class="sxs-lookup"><span data-stu-id="cac26-324">Switch parameters</span></span>

<span data-ttu-id="cac26-325">Switchparameters zijn parameters zonder parameterwaarde.</span><span class="sxs-lookup"><span data-stu-id="cac26-325">Switch parameters are parameters with no parameter value.</span></span> <span data-ttu-id="cac26-326">Ze zijn alleen effectief wanneer ze worden gebruikt en slechts één effect hebben.</span><span class="sxs-lookup"><span data-stu-id="cac26-326">They're effective only when they're used and have only one effect.</span></span>

<span data-ttu-id="cac26-327">De parameter **NoProfile** van **powershell.exe** is bijvoorbeeld een switchparameter.</span><span class="sxs-lookup"><span data-stu-id="cac26-327">For example, the **NoProfile** parameter of **powershell.exe** is a switch parameter.</span></span>

<span data-ttu-id="cac26-328">Als u een switchparameter in een functie wilt maken, geeft u het `Switch` type op in de parameterdefinitie.</span><span class="sxs-lookup"><span data-stu-id="cac26-328">To create a switch parameter in a function, specify the `Switch` type in the parameter definition.</span></span>

<span data-ttu-id="cac26-329">Bijvoorbeeld:</span><span class="sxs-lookup"><span data-stu-id="cac26-329">For example:</span></span>

```powershell
Param([Switch]<ParameterName>)
```

<span data-ttu-id="cac26-330">U kunt ook een andere methode gebruiken:</span><span class="sxs-lookup"><span data-stu-id="cac26-330">Or, you can use an another method:</span></span>

```powershell
Param(
    [Parameter(Mandatory=$false)]
    [Switch]
    $<ParameterName>
)
```

<span data-ttu-id="cac26-331">Switchparameters zijn eenvoudig te gebruiken en hebben de voorkeur boven Booleaanse parameters, die een moeilijkere syntaxis hebben.</span><span class="sxs-lookup"><span data-stu-id="cac26-331">Switch parameters are easy to use and are preferred over Boolean parameters, which have a more difficult syntax.</span></span>

<span data-ttu-id="cac26-332">Als u bijvoorbeeld een switchparameter wilt gebruiken, moet de gebruiker de parameter in de opdracht typen.</span><span class="sxs-lookup"><span data-stu-id="cac26-332">For example, to use a switch parameter, the user types the parameter in the command.</span></span>

`-IncludeAll`

<span data-ttu-id="cac26-333">Als u een Booleaanse parameter wilt gebruiken, moet de gebruiker de parameter en een Booleaanse waarde typen.</span><span class="sxs-lookup"><span data-stu-id="cac26-333">To use a Boolean parameter, the user types the parameter and a Boolean value.</span></span>

`-IncludeAll:$true`

<span data-ttu-id="cac26-334">Kies bij het maken van switchparameters zorgvuldig de parameternaam.</span><span class="sxs-lookup"><span data-stu-id="cac26-334">When creating switch parameters, choose the parameter name carefully.</span></span> <span data-ttu-id="cac26-335">Zorg ervoor dat de parameternaam het effect van de parameter aan de gebruiker doorgeeft.</span><span class="sxs-lookup"><span data-stu-id="cac26-335">Be sure that the parameter name communicates the effect of the parameter to the user.</span></span>
<span data-ttu-id="cac26-336">Vermijd niet-eenduidige termen, zoals **Filter** of **Maximum,** die kunnen impliceren dat een waarde vereist is.</span><span class="sxs-lookup"><span data-stu-id="cac26-336">Avoid ambiguous terms, such as **Filter** or **Maximum** that might imply a value is required.</span></span>

## <a name="argumentcompleter-attribute"></a><span data-ttu-id="cac26-337">Kenmerk ArgumentCompleter</span><span class="sxs-lookup"><span data-stu-id="cac26-337">ArgumentCompleter attribute</span></span>

<span data-ttu-id="cac26-338">Met **het kenmerk ArgumentCompleter** kunt u tabinvullingswaarden toevoegen aan een specifieke parameter.</span><span class="sxs-lookup"><span data-stu-id="cac26-338">The **ArgumentCompleter** attribute allows you to add tab completion values to a specific parameter.</span></span> <span data-ttu-id="cac26-339">Er **moet een kenmerk ArgumentCompleter** worden gedefinieerd voor elke parameter die tab-voltooiing nodig heeft.</span><span class="sxs-lookup"><span data-stu-id="cac26-339">An **ArgumentCompleter** attribute must be defined for each parameter that needs tab completion.</span></span> <span data-ttu-id="cac26-340">Net als **bij DynamicParameters** worden de beschikbare waarden berekend tijdens runtime wanneer de gebruiker op <kbd>Tab</kbd> na de parameternaam drukt.</span><span class="sxs-lookup"><span data-stu-id="cac26-340">Similar to **DynamicParameters**, the available values are calculated at runtime when the user presses <kbd>Tab</kbd> after the parameter name.</span></span>

<span data-ttu-id="cac26-341">Als u een **argumentcompleter-kenmerk** wilt toevoegen, moet u een scriptblok definiëren dat de waarden bepaalt.</span><span class="sxs-lookup"><span data-stu-id="cac26-341">To add an **ArgumentCompleter** attribute, you need to define a script block that determines the values.</span></span> <span data-ttu-id="cac26-342">Het scriptblok moet de volgende parameters hebben in de onderstaande volgorde.</span><span class="sxs-lookup"><span data-stu-id="cac26-342">The script block must take the following parameters in the order specified below.</span></span> <span data-ttu-id="cac26-343">De namen van de parameter zijn niet van belang omdat de waarden positioneel worden opgegeven.</span><span class="sxs-lookup"><span data-stu-id="cac26-343">The parameter's names don't matter as the values are provided positionally.</span></span>

<span data-ttu-id="cac26-344">De syntaxis is als volgt:</span><span class="sxs-lookup"><span data-stu-id="cac26-344">The syntax is as follows:</span></span>

```powershell
Param(
    [Parameter(Mandatory)]
    [ArgumentCompleter({
        param ( $commandName,
                $parameterName,
                $wordToComplete,
                $commandAst,
                $fakeBoundParameters )
        # Perform calculation of tab completed values here.
    })]
)
```

### <a name="argumentcompleter-script-block"></a><span data-ttu-id="cac26-345">Scriptblok ArgumentCompleter</span><span class="sxs-lookup"><span data-stu-id="cac26-345">ArgumentCompleter script block</span></span>

<span data-ttu-id="cac26-346">De parameters voor het scriptblok zijn ingesteld op de volgende waarden:</span><span class="sxs-lookup"><span data-stu-id="cac26-346">The script block parameters are set to the following values:</span></span>

- <span data-ttu-id="cac26-347">`$commandName` (Positie 0) - Deze parameter wordt ingesteld op de naam van de opdracht waarvoor het scriptblok tab-voltooiing biedt.</span><span class="sxs-lookup"><span data-stu-id="cac26-347">`$commandName` (Position 0) - This parameter is set to the name of the command for which the script block is providing tab completion.</span></span>
- <span data-ttu-id="cac26-348">`$parameterName` (Positie 1) - Deze parameter is ingesteld op de parameter waarvan de waarde tab-voltooiing vereist.</span><span class="sxs-lookup"><span data-stu-id="cac26-348">`$parameterName` (Position 1) - This parameter is set to the parameter whose value requires tab completion.</span></span>
- <span data-ttu-id="cac26-349">`$wordToComplete` (Positie 2) - Deze parameter is ingesteld op de waarde die de gebruiker heeft opgegeven voordat deze op <kbd>Tab drukt.</kbd> Uw scriptblok moet deze waarde gebruiken om de voltooiingswaarden van het tabblad te bepalen.</span><span class="sxs-lookup"><span data-stu-id="cac26-349">`$wordToComplete` (Position 2) - This parameter is set to value the user has provided before they pressed <kbd>Tab</kbd>. Your script block should use this value to determine tab completion values.</span></span>
- <span data-ttu-id="cac26-350">`$commandAst` (Positie 3) - Deze parameter is ingesteld op de abstracte syntaxisstructuur (AST) voor de huidige invoerregel.</span><span class="sxs-lookup"><span data-stu-id="cac26-350">`$commandAst` (Position 3) - This parameter is set to the Abstract Syntax Tree (AST) for the current input line.</span></span> <span data-ttu-id="cac26-351">Zie [Ast Class voor meer informatie.](/dotnet/api/system.management.automation.language.ast)</span><span class="sxs-lookup"><span data-stu-id="cac26-351">For more information, see [Ast Class](/dotnet/api/system.management.automation.language.ast).</span></span>
- <span data-ttu-id="cac26-352">`$fakeBoundParameters` (Positie 4) - Deze parameter is ingesteld op een hashtabel met de voor de `$PSBoundParameters` cmdlet voordat de gebruiker op <kbd>Tab heeft gedrukt.</kbd> Zie voor meer informatie [about_Automatic_Variables](about_Automatic_Variables.md).</span><span class="sxs-lookup"><span data-stu-id="cac26-352">`$fakeBoundParameters` (Position 4) - This parameter is set to a hashtable containing the `$PSBoundParameters` for the cmdlet, before the user pressed <kbd>Tab</kbd>. For more information, see [about_Automatic_Variables](about_Automatic_Variables.md).</span></span>

<span data-ttu-id="cac26-353">Het **scriptblok ArgumentCompleter** moet de waarden uitschrijven met behulp van de pijplijn, `ForEach-Object` zoals , of een andere geschikte `Where-Object` methode.</span><span class="sxs-lookup"><span data-stu-id="cac26-353">The **ArgumentCompleter** script block must unroll the values using the pipeline, such as `ForEach-Object`, `Where-Object`, or another suitable method.</span></span>
<span data-ttu-id="cac26-354">Het retourneren van een matrix met waarden  zorgt ervoor dat PowerShell de hele matrix als één tab-voltooiingswaarde behandelt.</span><span class="sxs-lookup"><span data-stu-id="cac26-354">Returning an array of values causes PowerShell to treat the entire array as **one** tab completion value.</span></span>

<span data-ttu-id="cac26-355">In het volgende voorbeeld wordt tab-aanvulling toegevoegd aan de parameter **Value.**</span><span class="sxs-lookup"><span data-stu-id="cac26-355">The following example adds tab completion to the **Value** parameter.</span></span> <span data-ttu-id="cac26-356">Als alleen de **parameter Waarde** is opgegeven, worden alle mogelijke waarden of argumenten voor **Waarde** weergegeven.</span><span class="sxs-lookup"><span data-stu-id="cac26-356">If only the **Value** parameter is specified, all possible values, or arguments, for **Value** are displayed.</span></span> <span data-ttu-id="cac26-357">Wanneer de **parameter Type** is opgegeven, geeft de parameter **Waarde** alleen de mogelijke waarden voor dat type weer.</span><span class="sxs-lookup"><span data-stu-id="cac26-357">When the **Type** parameter is specified, the **Value** parameter only displays the possible values for that type.</span></span>

<span data-ttu-id="cac26-358">Bovendien zorgt de operator ervoor dat als de gebruiker de volgende opdracht intypen en `-like` <kbd>Tab-voltooiing</kbd> gebruikt, alleen **Apple** wordt geretourneerd.</span><span class="sxs-lookup"><span data-stu-id="cac26-358">In addition, the `-like` operator ensures that if the user types the following command and uses <kbd>Tab</kbd> completion, only **Apple** is returned.</span></span>

`Test-ArgumentCompleter -Type Fruits -Value A`

```powershell
function Test-ArgumentCompleter {
[CmdletBinding()]
 param (
        [Parameter(Mandatory=$true)]
        [ValidateSet('Fruits', 'Vegetables')]
        $Type,
        [Parameter(Mandatory=$true)]
        [ArgumentCompleter( {
            param ( $commandName,
                    $parameterName,
                    $wordToComplete,
                    $commandAst,
                    $fakeBoundParameters )

            $possibleValues = @{
                Fruits = @('Apple', 'Orange', 'Banana')
                Vegetables = @('Tomato', 'Squash', 'Corn')
            }
            if ($fakeBoundParameters.ContainsKey('Type'))
            {
                $possibleValues[$fakeBoundParameters.Type] | Where-Object {
                    $_ -like "$wordToComplete*"
                }
            }
            else
            {
                $possibleValues.Values | ForEach-Object {$_}
            }
        } )]
        $Value
      )
}
```

## <a name="see-also"></a><span data-ttu-id="cac26-359">Zie ook</span><span class="sxs-lookup"><span data-stu-id="cac26-359">See also</span></span>

[<span data-ttu-id="cac26-360">about_Automatic_Variables</span><span class="sxs-lookup"><span data-stu-id="cac26-360">about_Automatic_Variables</span></span>](about_Automatic_Variables.md)

[<span data-ttu-id="cac26-361">about_Functions</span><span class="sxs-lookup"><span data-stu-id="cac26-361">about_Functions</span></span>](about_Functions.md)

[<span data-ttu-id="cac26-362">about_Functions_Advanced</span><span class="sxs-lookup"><span data-stu-id="cac26-362">about_Functions_Advanced</span></span>](about_Functions_Advanced.md)

[<span data-ttu-id="cac26-363">about_Functions_Advanced_Methods</span><span class="sxs-lookup"><span data-stu-id="cac26-363">about_Functions_Advanced_Methods</span></span>](about_Functions_Advanced_Methods.md)

[<span data-ttu-id="cac26-364">about_Functions_CmdletBindingAttribute</span><span class="sxs-lookup"><span data-stu-id="cac26-364">about_Functions_CmdletBindingAttribute</span></span>](about_Functions_CmdletBindingAttribute.md)

[<span data-ttu-id="cac26-365">about_Functions_OutputTypeAttribute</span><span class="sxs-lookup"><span data-stu-id="cac26-365">about_Functions_OutputTypeAttribute</span></span>](about_Functions_OutputTypeAttribute.md)
