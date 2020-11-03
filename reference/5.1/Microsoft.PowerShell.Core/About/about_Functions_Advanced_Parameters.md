---
description: Hierin wordt uitgelegd hoe u para meters toevoegt aan geavanceerde functies.
keywords: powershell,cmdlet
Locale: en-US
ms.date: 10/27/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_functions_advanced_parameters?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Functions_Advanced_Parameters
ms.openlocfilehash: 4123d71392f8b32df8d04033d85476cb18b39736
ms.sourcegitcommit: 3b1779890f828130a9d73aebf17ebffae511728f
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/28/2020
ms.locfileid: "93253242"
---
# <a name="about-functions-advanced-parameters"></a><span data-ttu-id="dc8ba-104">Over functies geavanceerde para meters</span><span class="sxs-lookup"><span data-stu-id="dc8ba-104">About Functions Advanced Parameters</span></span>

## <a name="short-description"></a><span data-ttu-id="dc8ba-105">Korte beschrijving</span><span class="sxs-lookup"><span data-stu-id="dc8ba-105">Short description</span></span>

<span data-ttu-id="dc8ba-106">Hierin wordt uitgelegd hoe u para meters toevoegt aan geavanceerde functies.</span><span class="sxs-lookup"><span data-stu-id="dc8ba-106">Explains how to add parameters to advanced functions.</span></span>

## <a name="long-description"></a><span data-ttu-id="dc8ba-107">Lange beschrijving</span><span class="sxs-lookup"><span data-stu-id="dc8ba-107">Long description</span></span>

<span data-ttu-id="dc8ba-108">U kunt para meters toevoegen aan de geavanceerde functies die u schrijft en parameter kenmerken en argumenten gebruiken om de parameter waarden te beperken die door gebruikers worden verzonden met de para meter.</span><span class="sxs-lookup"><span data-stu-id="dc8ba-108">You can add parameters to the advanced functions that you write, and use parameter attributes and arguments to limit the parameter values that function users submit with the parameter.</span></span>

<span data-ttu-id="dc8ba-109">De para meters die u aan de functie toevoegt, zijn beschikbaar voor gebruikers naast de algemene para meters die Power shell automatisch toevoegt aan alle cmdlets en geavanceerde functies.</span><span class="sxs-lookup"><span data-stu-id="dc8ba-109">The parameters that you add to your function are available to users in addition to the common parameters that PowerShell adds automatically to all cmdlets and advanced functions.</span></span> <span data-ttu-id="dc8ba-110">Zie [about_CommonParameters](about_CommonParameters.md)voor meer informatie over de algemene Power shell-para meters.</span><span class="sxs-lookup"><span data-stu-id="dc8ba-110">For more information about the PowerShell common parameters, see [about_CommonParameters](about_CommonParameters.md).</span></span>

<span data-ttu-id="dc8ba-111">Vanaf Power Shell 3,0 kunt u splatting gebruiken `@Args` om de para meters in een opdracht weer te geven.</span><span class="sxs-lookup"><span data-stu-id="dc8ba-111">Beginning in PowerShell 3.0, you can use splatting with `@Args` to represent the parameters in a command.</span></span> <span data-ttu-id="dc8ba-112">Splatting is geldig voor eenvoudige en geavanceerde functies.</span><span class="sxs-lookup"><span data-stu-id="dc8ba-112">Splatting is valid on simple and advanced functions.</span></span> <span data-ttu-id="dc8ba-113">Zie [about_Functions](about_Functions.md) en [about_Splatting](about_Splatting.md)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="dc8ba-113">For more information, see [about_Functions](about_Functions.md) and [about_Splatting](about_Splatting.md).</span></span>

## <a name="type-conversion-of-parameter-values"></a><span data-ttu-id="dc8ba-114">Type conversie van parameter waarden</span><span class="sxs-lookup"><span data-stu-id="dc8ba-114">Type conversion of parameter values</span></span>

<span data-ttu-id="dc8ba-115">Wanneer u teken reeksen opgeeft als argumenten voor para meters die een ander type verwachten, converteert Power shell de teken reeksen impliciet naar het doel type van de para meter.</span><span class="sxs-lookup"><span data-stu-id="dc8ba-115">When you supply strings as arguments to parameters that expect a different type, PowerShell implicitly converts the strings to the parameter target type.</span></span>
<span data-ttu-id="dc8ba-116">Geavanceerde functies voeren Culture-invariant-parsering van parameter waarden uit.</span><span class="sxs-lookup"><span data-stu-id="dc8ba-116">Advanced functions perform culture-invariant parsing of parameter values.</span></span>

<span data-ttu-id="dc8ba-117">Daarentegen wordt een cultuur-gevoelige conversie uitgevoerd tijdens de parameter binding van gecompileerde cmdlets.</span><span class="sxs-lookup"><span data-stu-id="dc8ba-117">By contrast, a culture-sensitive conversion is performed during parameter binding for compiled cmdlets.</span></span>

<span data-ttu-id="dc8ba-118">In dit voor beeld maken we een cmdlet en een script functie die een `[datetime]` para meter gebruiken.</span><span class="sxs-lookup"><span data-stu-id="dc8ba-118">In this example, we create a cmdlet and a script function that take a `[datetime]` parameter.</span></span> <span data-ttu-id="dc8ba-119">De huidige cultuur wordt gewijzigd voor het gebruik van Duitse instellingen.</span><span class="sxs-lookup"><span data-stu-id="dc8ba-119">The current culture is changed to use German settings.</span></span>
<span data-ttu-id="dc8ba-120">Een datum in de Duitse notatie wordt door gegeven aan de para meter.</span><span class="sxs-lookup"><span data-stu-id="dc8ba-120">A German-formatted date is passed to the parameter.</span></span>

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

<span data-ttu-id="dc8ba-121">Zoals hierboven wordt weer gegeven, gebruiken cmdlets cultuur gevoelige parseren om de teken reeks te converteren.</span><span class="sxs-lookup"><span data-stu-id="dc8ba-121">As shown above, cmdlets use culture-sensitive parsing to convert the string.</span></span>

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

<span data-ttu-id="dc8ba-122">Geavanceerde functies gebruiken Culture-invariant-parsering, wat resulteert in de volgende fout.</span><span class="sxs-lookup"><span data-stu-id="dc8ba-122">Advanced functions use culture-invariant parsing, which results in the following error.</span></span>

```Output
Get-Date_Func : Cannot process argument transformation on parameter 'Date'. Cannot convert
 value "19-06-2018" to type "System.DateTime". Error: "String was not recognized as a valid
 DateTime."
At line:13 char:15
+ Get-Date_Func $dateStr
+               ~~~~~~~~
    + CategoryInfo          : InvalidData: (:) [Get-Date_Func], ParameterBindingArgumentTransformationException
    + FullyQualifiedErrorId : ParameterArgumentTransformationError,Get-Date_Func
```

## <a name="static-parameters"></a><span data-ttu-id="dc8ba-123">Statische para meters</span><span class="sxs-lookup"><span data-stu-id="dc8ba-123">Static parameters</span></span>

<span data-ttu-id="dc8ba-124">Statische para meters zijn para meters die altijd beschikbaar zijn in de functie.</span><span class="sxs-lookup"><span data-stu-id="dc8ba-124">Static parameters are parameters that are always available in the function.</span></span>
<span data-ttu-id="dc8ba-125">De meeste para meters in Power shell-cmdlets en-scripts zijn statische para meters.</span><span class="sxs-lookup"><span data-stu-id="dc8ba-125">Most parameters in PowerShell cmdlets and scripts are static parameters.</span></span>

<span data-ttu-id="dc8ba-126">In het volgende voor beeld ziet u de declaratie van een **ComputerName** -para meter met de volgende kenmerken:</span><span class="sxs-lookup"><span data-stu-id="dc8ba-126">The following example shows the declaration of a **ComputerName** parameter that has the following characteristics:</span></span>

- <span data-ttu-id="dc8ba-127">Het is verplicht (vereist).</span><span class="sxs-lookup"><span data-stu-id="dc8ba-127">It's mandatory (required).</span></span>
- <span data-ttu-id="dc8ba-128">Het neemt de invoer van de pijp lijn.</span><span class="sxs-lookup"><span data-stu-id="dc8ba-128">It takes input from the pipeline.</span></span>
- <span data-ttu-id="dc8ba-129">Er wordt een matrix met teken reeksen als invoer gebruikt.</span><span class="sxs-lookup"><span data-stu-id="dc8ba-129">It takes an array of strings as input.</span></span>

```powershell
Param(
    [Parameter(Mandatory=$true,
    ValueFromPipeline=$true)]
    [String[]]
    $ComputerName
)
```

## <a name="attributes-of-parameters"></a><span data-ttu-id="dc8ba-130">Kenmerken van para meters</span><span class="sxs-lookup"><span data-stu-id="dc8ba-130">Attributes of parameters</span></span>

<span data-ttu-id="dc8ba-131">In deze sectie worden de kenmerken beschreven die u kunt toevoegen aan functie parameters.</span><span class="sxs-lookup"><span data-stu-id="dc8ba-131">This section describes the attributes that you can add to function parameters.</span></span>

<span data-ttu-id="dc8ba-132">Alle kenmerken zijn optioneel.</span><span class="sxs-lookup"><span data-stu-id="dc8ba-132">All attributes are optional.</span></span> <span data-ttu-id="dc8ba-133">Als u echter het kenmerk **CmdletBinding** weglaat en vervolgens als een geavanceerde functie wordt herkend, moet de functie het **parameter** kenmerk bevatten.</span><span class="sxs-lookup"><span data-stu-id="dc8ba-133">However, if you omit the **CmdletBinding** attribute, then to be recognized as an advanced function, the function must include the **Parameter** attribute.</span></span>

<span data-ttu-id="dc8ba-134">U kunt een of meer kenmerken in elke parameter declaratie toevoegen.</span><span class="sxs-lookup"><span data-stu-id="dc8ba-134">You can add one or multiple attributes in each parameter declaration.</span></span> <span data-ttu-id="dc8ba-135">Er is geen limiet voor het aantal kenmerken dat u aan een parameter declaratie kunt toevoegen.</span><span class="sxs-lookup"><span data-stu-id="dc8ba-135">There's no limit to the number of attributes that you can add to a parameter declaration.</span></span>

### <a name="parameter-attribute"></a><span data-ttu-id="dc8ba-136">Parameter kenmerk</span><span class="sxs-lookup"><span data-stu-id="dc8ba-136">Parameter attribute</span></span>

<span data-ttu-id="dc8ba-137">Het **parameter** kenmerk wordt gebruikt voor het declareren van de kenmerken van functie parameters.</span><span class="sxs-lookup"><span data-stu-id="dc8ba-137">The **Parameter** attribute is used to declare the attributes of function parameters.</span></span>

<span data-ttu-id="dc8ba-138">Het **parameter** kenmerk is optioneel en u kunt het weglaten als geen van de para meters van uw functies kenmerken nodig heeft.</span><span class="sxs-lookup"><span data-stu-id="dc8ba-138">The **Parameter** attribute is optional, and you can omit it if none of the parameters of your functions need attributes.</span></span> <span data-ttu-id="dc8ba-139">Maar om te worden herkend als een geavanceerde functie in plaats van een eenvoudige functie, moet een functie het kenmerk **CmdletBinding** of het kenmerk **para meter** of beide hebben.</span><span class="sxs-lookup"><span data-stu-id="dc8ba-139">But, to be recognized as an advanced function, rather than a simple function, a function must have either the **CmdletBinding** attribute or the **Parameter** attribute, or both.</span></span>

<span data-ttu-id="dc8ba-140">Het **parameter** kenmerk heeft argumenten waarmee de kenmerken van de para meter worden gedefinieerd, bijvoorbeeld of de para meter verplicht of optioneel is.</span><span class="sxs-lookup"><span data-stu-id="dc8ba-140">The **Parameter** attribute has arguments that define the characteristics of the parameter, such as whether the parameter is mandatory or optional.</span></span>

<span data-ttu-id="dc8ba-141">Gebruik de volgende syntaxis om het **parameter** kenmerk, een argument en een argument waarde te declareren.</span><span class="sxs-lookup"><span data-stu-id="dc8ba-141">Use the following syntax to declare the **Parameter** attribute, an argument, and an argument value.</span></span> <span data-ttu-id="dc8ba-142">De haakjes tussen het argument en de bijbehorende waarde moeten de **para meter** zonder tussenliggende ruimte volgen.</span><span class="sxs-lookup"><span data-stu-id="dc8ba-142">The parentheses that enclose the argument and its value must follow **Parameter** with no intervening space.</span></span>

```powershell
Param(
    [Parameter(Argument=value)]
    $ParameterName
)
```

<span data-ttu-id="dc8ba-143">Gebruik komma's om de argumenten tussen de haakjes te scheiden.</span><span class="sxs-lookup"><span data-stu-id="dc8ba-143">Use commas to separate arguments within the parentheses.</span></span> <span data-ttu-id="dc8ba-144">Gebruik de volgende syntaxis om twee argumenten van het **parameter** kenmerk te declareren.</span><span class="sxs-lookup"><span data-stu-id="dc8ba-144">Use the following syntax to declare two arguments of the **Parameter** attribute.</span></span>

```powershell
Param(
    [Parameter(Argument1=value1,
    Argument2=value2)]
)
```

<span data-ttu-id="dc8ba-145">De Boole-argument typen van het **parameter** kenmerk zijn standaard ingesteld op **Onwaar** als u het **parameter** kenmerk weglaat.</span><span class="sxs-lookup"><span data-stu-id="dc8ba-145">The boolean argument types of the **Parameter** attribute default to **False** when omitted from the **Parameter** attribute.</span></span> <span data-ttu-id="dc8ba-146">Stel de waarde van het argument in op `$true` of alleen een lijst met de naam van het argument.</span><span class="sxs-lookup"><span data-stu-id="dc8ba-146">Set the argument value to `$true` or just list the argument by name.</span></span> <span data-ttu-id="dc8ba-147">De volgende **parameter** kenmerken zijn bijvoorbeeld gelijkwaardig.</span><span class="sxs-lookup"><span data-stu-id="dc8ba-147">For example, the following **Parameter** attributes are equivalent.</span></span>

```powershell
Param(
    [Parameter(Mandatory=$true)]
)

# Boolean arguments can be defined using this shorthand syntax

Param(
    [Parameter(Mandatory)]
)
```

<span data-ttu-id="dc8ba-148">Als u het **parameter** kenmerk zonder argumenten gebruikt als alternatief voor het gebruik van het kenmerk **CmdletBinding** , moeten de haakjes die de kenmerk naam volgen, nog steeds vereist zijn.</span><span class="sxs-lookup"><span data-stu-id="dc8ba-148">If you use the **Parameter** attribute without arguments, as an alternative to using the **CmdletBinding** attribute, the parentheses that follow the attribute name are still required.</span></span>

```powershell
Param(
    [Parameter()]
    $ParameterName
)
```

#### <a name="mandatory-argument"></a><span data-ttu-id="dc8ba-149">Verplicht argument</span><span class="sxs-lookup"><span data-stu-id="dc8ba-149">Mandatory argument</span></span>

<span data-ttu-id="dc8ba-150">Het `Mandatory` argument geeft aan dat de para meter is vereist.</span><span class="sxs-lookup"><span data-stu-id="dc8ba-150">The `Mandatory` argument indicates that the parameter is required.</span></span> <span data-ttu-id="dc8ba-151">Als dit argument niet wordt opgegeven, is de para meter optioneel.</span><span class="sxs-lookup"><span data-stu-id="dc8ba-151">If this argument isn't specified, the parameter is optional.</span></span>

<span data-ttu-id="dc8ba-152">In het volgende voor beeld wordt de para meter **ComputerName** gedeclareerd.</span><span class="sxs-lookup"><span data-stu-id="dc8ba-152">The following example declares the **ComputerName** parameter.</span></span> <span data-ttu-id="dc8ba-153">Het argument wordt gebruikt `Mandatory` om de para meter verplicht te maken.</span><span class="sxs-lookup"><span data-stu-id="dc8ba-153">It uses the `Mandatory` argument to make the parameter mandatory.</span></span>

```powershell
Param(
    [Parameter(Mandatory=$true)]
    [String[]]
    $ComputerName
)
```

#### <a name="position-argument"></a><span data-ttu-id="dc8ba-154">Argument positie</span><span class="sxs-lookup"><span data-stu-id="dc8ba-154">Position argument</span></span>

<span data-ttu-id="dc8ba-155">Het `Position` argument bepaalt of de parameter naam vereist is wanneer de para meter in een opdracht wordt gebruikt.</span><span class="sxs-lookup"><span data-stu-id="dc8ba-155">The `Position` argument determines whether the parameter name is required when the parameter is used in a command.</span></span> <span data-ttu-id="dc8ba-156">Wanneer een parameter declaratie het `Position` argument bevat, kan de parameter naam worden wegge laten en Power shell de niet-gegroepeerde parameter waarde identificeren met behulp van de positie of volg orde in de lijst met niet-genaamde parameter waarden in de opdracht.</span><span class="sxs-lookup"><span data-stu-id="dc8ba-156">When a parameter declaration includes the `Position` argument, the parameter name can be omitted and PowerShell identifies the unnamed parameter value by its position, or order, in the list of unnamed parameter values in the command.</span></span>

<span data-ttu-id="dc8ba-157">Als het `Position` argument niet is opgegeven, de parameter naam of een alias naam of afkorting van de para meter moet vóór de parameter waarde worden voorafgegaan wanneer de para meter wordt gebruikt in een opdracht.</span><span class="sxs-lookup"><span data-stu-id="dc8ba-157">If the `Position` argument isn't specified, the parameter name, or a parameter name alias or abbreviation, must precede the parameter value whenever the parameter is used in a command.</span></span>

<span data-ttu-id="dc8ba-158">Standaard zijn alle functie parameters positioneel.</span><span class="sxs-lookup"><span data-stu-id="dc8ba-158">By default, all function parameters are positional.</span></span> <span data-ttu-id="dc8ba-159">Power shell wijst positie nummers toe aan para meters in de volg orde waarin de para meters in de functie zijn gedeclareerd.</span><span class="sxs-lookup"><span data-stu-id="dc8ba-159">PowerShell assigns position numbers to parameters in the order in which the parameters are declared in the function.</span></span> <span data-ttu-id="dc8ba-160">Als u deze functie wilt uitschakelen, stelt u de waarde van het `PositionalBinding` argument van het kenmerk **CmdletBinding** in op `$False` .</span><span class="sxs-lookup"><span data-stu-id="dc8ba-160">To disable this feature, set the value of the `PositionalBinding` argument of the **CmdletBinding** attribute to `$False`.</span></span> <span data-ttu-id="dc8ba-161">Het `Position` argument heeft voor rang op de waarde van het `PositionalBinding` argument van het kenmerk **CmdletBinding** .</span><span class="sxs-lookup"><span data-stu-id="dc8ba-161">The `Position` argument takes precedence over the value of the `PositionalBinding` argument of the **CmdletBinding** attribute.</span></span> <span data-ttu-id="dc8ba-162">Zie `PositionalBinding` in [about_Functions_CmdletBindingAttribute](about_Functions_CmdletBindingAttribute.md)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="dc8ba-162">For more information, see `PositionalBinding` in [about_Functions_CmdletBindingAttribute](about_Functions_CmdletBindingAttribute.md).</span></span>

<span data-ttu-id="dc8ba-163">De waarde van het `Position` argument wordt opgegeven als een geheel getal.</span><span class="sxs-lookup"><span data-stu-id="dc8ba-163">The value of the `Position` argument is specified as an integer.</span></span> <span data-ttu-id="dc8ba-164">Een positie waarde van **0** vertegenwoordigt de eerste positie in de opdracht, een positie waarde van **1** vertegenwoordigt de tweede positie in de opdracht, enzovoort.</span><span class="sxs-lookup"><span data-stu-id="dc8ba-164">A position value of **0** represents the first position in the command, a position value of **1** represents the second position in the command, and so on.</span></span>

<span data-ttu-id="dc8ba-165">Als een functie geen positionele para meters heeft, wijst Power shell posities toe aan elke para meter op basis van de volg orde waarin de para meters worden gedeclareerd.</span><span class="sxs-lookup"><span data-stu-id="dc8ba-165">If a function has no positional parameters, PowerShell assigns positions to each parameter based on the order in which the parameters are declared.</span></span>
<span data-ttu-id="dc8ba-166">Als best practice, vertrouwt u echter niet op deze toewijzing.</span><span class="sxs-lookup"><span data-stu-id="dc8ba-166">However, as a best practice, don't rely on this assignment.</span></span> <span data-ttu-id="dc8ba-167">Gebruik het argument als u wilt dat de para meters positioneel zijn `Position` .</span><span class="sxs-lookup"><span data-stu-id="dc8ba-167">When you want parameters to be positional, use the `Position` argument.</span></span>

<span data-ttu-id="dc8ba-168">In het volgende voor beeld wordt de para meter **ComputerName** gedeclareerd.</span><span class="sxs-lookup"><span data-stu-id="dc8ba-168">The following example declares the **ComputerName** parameter.</span></span> <span data-ttu-id="dc8ba-169">Het argument wordt gebruikt `Position` met de waarde **0**.</span><span class="sxs-lookup"><span data-stu-id="dc8ba-169">It uses the `Position` argument with a value of **0**.</span></span> <span data-ttu-id="dc8ba-170">Als dit het geval `-ComputerName` is, moet de waarde van de opdracht worden wegge laten door de eerste of enige niet-genaamde parameter waarde in de opdracht.</span><span class="sxs-lookup"><span data-stu-id="dc8ba-170">As a result, when `-ComputerName` is omitted from command, its value must be the first or only unnamed parameter value in the command.</span></span>

```powershell
Param(
    [Parameter(Position=0)]
    [String[]]
    $ComputerName
)
```

#### <a name="parametersetname-argument"></a><span data-ttu-id="dc8ba-171">ParameterSetName-argument</span><span class="sxs-lookup"><span data-stu-id="dc8ba-171">ParameterSetName argument</span></span>

<span data-ttu-id="dc8ba-172">Het `ParameterSetName` argument geeft de parameterset op waarvan een para meter deel uitmaakt.</span><span class="sxs-lookup"><span data-stu-id="dc8ba-172">The `ParameterSetName` argument specifies the parameter set to which a parameter belongs.</span></span> <span data-ttu-id="dc8ba-173">Als er geen parameterset is opgegeven, hoort de para meter bij alle parameter sets die zijn gedefinieerd door de functie.</span><span class="sxs-lookup"><span data-stu-id="dc8ba-173">If no parameter set is specified, the parameter belongs to all the parameter sets defined by the function.</span></span> <span data-ttu-id="dc8ba-174">Daarom moet elke parameterset ten minste één para meter hebben die geen lid is van een andere parameterset.</span><span class="sxs-lookup"><span data-stu-id="dc8ba-174">Therefore, to be unique, each parameter set must have at least one parameter that isn't a member of any other parameter set.</span></span>

> [!NOTE]
> <span data-ttu-id="dc8ba-175">Voor een cmdlet of functie geldt een limiet van 32 parameter sets.</span><span class="sxs-lookup"><span data-stu-id="dc8ba-175">For a cmdlet or function, there is a limit of 32 parameter sets.</span></span>

<span data-ttu-id="dc8ba-176">In het volgende voor beeld wordt de para meter **ComputerName** gedeclareerd in de `Computer` parameterset, een **gebruikers naam** parameter in de `User` parameterset en een **samenvattings** parameter in beide parameter sets.</span><span class="sxs-lookup"><span data-stu-id="dc8ba-176">The following example declares a **ComputerName** parameter in the `Computer` parameter set, a **UserName** parameter in the `User` parameter set, and a **Summary** parameter in both parameter sets.</span></span>

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

<span data-ttu-id="dc8ba-177">U kunt slechts één `ParameterSetName` waarde opgeven in elk argument en slechts één `ParameterSetName` argument in elk **parameter** kenmerk.</span><span class="sxs-lookup"><span data-stu-id="dc8ba-177">You can specify only one `ParameterSetName` value in each argument and only one `ParameterSetName` argument in each **Parameter** attribute.</span></span> <span data-ttu-id="dc8ba-178">Voeg extra **parameter** kenmerken toe om aan te geven dat een para meter in meer dan één parameterset wordt weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="dc8ba-178">To indicate that a parameter appears in more than one parameter set, add additional **Parameter** attributes.</span></span>

<span data-ttu-id="dc8ba-179">In het volgende voor beeld wordt de **samenvattings** parameter expliciet aan de `Computer` `User` para meters en ingesteld.</span><span class="sxs-lookup"><span data-stu-id="dc8ba-179">The following example explicitly adds the **Summary** parameter to the `Computer` and `User` parameter sets.</span></span> <span data-ttu-id="dc8ba-180">De **samenvattings** parameter is optioneel in de `Computer` parameterset en verplicht in de `User` parameterset.</span><span class="sxs-lookup"><span data-stu-id="dc8ba-180">The **Summary** parameter is optional in the `Computer` parameter set and mandatory in the `User` parameter set.</span></span>

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

<span data-ttu-id="dc8ba-181">Zie [about para meters](about_parameter_sets.md)voor meer informatie over parameter sets.</span><span class="sxs-lookup"><span data-stu-id="dc8ba-181">For more information about parameter sets, see [About Parameter Sets](about_parameter_sets.md).</span></span>

#### <a name="valuefrompipeline-argument"></a><span data-ttu-id="dc8ba-182">ValueFromPipeline-argument</span><span class="sxs-lookup"><span data-stu-id="dc8ba-182">ValueFromPipeline argument</span></span>

<span data-ttu-id="dc8ba-183">Het `ValueFromPipeline` argument geeft aan dat de para meter invoer accepteert van een pijplijn object.</span><span class="sxs-lookup"><span data-stu-id="dc8ba-183">The `ValueFromPipeline` argument indicates that the parameter accepts input from a pipeline object.</span></span> <span data-ttu-id="dc8ba-184">Geef dit argument op als de functie het volledige object accepteert, niet alleen een eigenschap van het object.</span><span class="sxs-lookup"><span data-stu-id="dc8ba-184">Specify this argument if the function accepts the entire object, not just a property of the object.</span></span>

<span data-ttu-id="dc8ba-185">In het volgende voor beeld wordt een para meter **ComputerName** gedeclareerd die verplicht is en wordt een object geaccepteerd dat wordt door gegeven aan de functie vanuit de pijp lijn.</span><span class="sxs-lookup"><span data-stu-id="dc8ba-185">The following example declares a **ComputerName** parameter that's mandatory and accepts an object that's passed to the function from the pipeline.</span></span>

```powershell
Param(
    [Parameter(Mandatory=$true,
    ValueFromPipeline=$true)]
    [String[]]
    $ComputerName
)
```

#### <a name="valuefrompipelinebypropertyname-argument"></a><span data-ttu-id="dc8ba-186">ValueFromPipelineByPropertyName-argument</span><span class="sxs-lookup"><span data-stu-id="dc8ba-186">ValueFromPipelineByPropertyName argument</span></span>

<span data-ttu-id="dc8ba-187">Het `ValueFromPipelineByPropertyName` argument geeft aan dat de para meter invoer accepteert van een eigenschap van een pijplijn object.</span><span class="sxs-lookup"><span data-stu-id="dc8ba-187">The `ValueFromPipelineByPropertyName` argument indicates that the parameter accepts input from a property of a pipeline object.</span></span> <span data-ttu-id="dc8ba-188">De object eigenschap moet dezelfde naam of alias hebben als de para meter.</span><span class="sxs-lookup"><span data-stu-id="dc8ba-188">The object property must have the same name or alias as the parameter.</span></span>

<span data-ttu-id="dc8ba-189">Als de functie bijvoorbeeld de para meter **ComputerName** heeft en het object piped een eigenschap **ComputerName** heeft, wordt de waarde van de eigenschap **ComputerName** toegewezen aan de para meter **ComputerName** van de functie.</span><span class="sxs-lookup"><span data-stu-id="dc8ba-189">For example, if the function has a **ComputerName** parameter, and the piped object has a **ComputerName** property, the value of the **ComputerName** property is assigned to the function's **ComputerName** parameter.</span></span>

<span data-ttu-id="dc8ba-190">In het volgende voor beeld wordt een para meter **ComputerName** gedeclareerd die verplicht is en accepteert de invoer van de eigenschap **ComputerName** van het object die wordt door gegeven aan de functie via de pijp lijn.</span><span class="sxs-lookup"><span data-stu-id="dc8ba-190">The following example declares a **ComputerName** parameter that's mandatory and accepts input from the object's **ComputerName** property that's passed to the function through the pipeline.</span></span>

```powershell
Param(
    [Parameter(Mandatory=$true,
    ValueFromPipelineByPropertyName=$true)]
    [String[]]
    $ComputerName
)
```

> [!NOTE]
> <span data-ttu-id="dc8ba-191">Een getypeerde para meter die pijplijn invoer ( `by Value` ) of () accepteert, `by PropertyName` maakt het gebruik van script blokken met _vertragings bindingen_ mogelijk voor de para meter.</span><span class="sxs-lookup"><span data-stu-id="dc8ba-191">A typed parameter that accepts pipeline input (`by Value`) or (`by PropertyName`) enables use of _delay-bind_ script blocks on the parameter.</span></span>
>
> <span data-ttu-id="dc8ba-192">Het script blok voor de _vertragings binding_ wordt automatisch uitgevoerd tijdens **ParameterBinding**.</span><span class="sxs-lookup"><span data-stu-id="dc8ba-192">The _delay-bind_ script block is run automatically during **ParameterBinding**.</span></span> <span data-ttu-id="dc8ba-193">Het resultaat is gebonden aan de para meter.</span><span class="sxs-lookup"><span data-stu-id="dc8ba-193">The result is bound to the parameter.</span></span> <span data-ttu-id="dc8ba-194">De vertraagde binding werkt niet voor para meters die zijn gedefinieerd als type `ScriptBlock` of `System.Object` .</span><span class="sxs-lookup"><span data-stu-id="dc8ba-194">Delay binding does not work for parameters defined as type `ScriptBlock` or `System.Object`.</span></span> <span data-ttu-id="dc8ba-195">Het script blok is door gegeven _zonder te_ worden aangeroepen.</span><span class="sxs-lookup"><span data-stu-id="dc8ba-195">The script block is passed through _without_ being invoked.</span></span>
>
> <span data-ttu-id="dc8ba-196">U kunt hier meer lezen over de script blokken _met vertragings bindingen_ [about_Script_Blocks. MD](about_Script_Blocks.md).</span><span class="sxs-lookup"><span data-stu-id="dc8ba-196">You can read about _delay-bind_ script blocks here [about_Script_Blocks.md](about_Script_Blocks.md).</span></span>

#### <a name="valuefromremainingarguments-argument"></a><span data-ttu-id="dc8ba-197">ValueFromRemainingArguments-argument</span><span class="sxs-lookup"><span data-stu-id="dc8ba-197">ValueFromRemainingArguments argument</span></span>

<span data-ttu-id="dc8ba-198">Het `ValueFromRemainingArguments` argument geeft aan dat de para meter alle waarden van de para meter in de opdracht accepteert die niet zijn toegewezen aan andere para meters van de functie.</span><span class="sxs-lookup"><span data-stu-id="dc8ba-198">The `ValueFromRemainingArguments` argument indicates that the parameter accepts all the parameter's values in the command that aren't assigned to other parameters of the function.</span></span>

<span data-ttu-id="dc8ba-199">Er is een bekend probleem met het gebruik van verzamelingen met **ValueFromRemainingArguments** waarbij de door gegeven verzameling wordt behandeld als één element.</span><span class="sxs-lookup"><span data-stu-id="dc8ba-199">There's a known issue for using collections with **ValueFromRemainingArguments** where the passed-in collection is treated as a single element.</span></span>

<span data-ttu-id="dc8ba-200">In het volgende voor beeld wordt dit bekende probleem gedemonstreerd.</span><span class="sxs-lookup"><span data-stu-id="dc8ba-200">The following example demonstrates this known issue.</span></span> <span data-ttu-id="dc8ba-201">De **resterende** para meter moet **een** bevatten bij **index 0** en **twee** bij **index 1**.</span><span class="sxs-lookup"><span data-stu-id="dc8ba-201">The **Remaining** parameter should contain **one** at **index 0** and **two** at **index 1**.</span></span>
<span data-ttu-id="dc8ba-202">In plaats daarvan worden beide elementen gecombineerd tot één entiteit.</span><span class="sxs-lookup"><span data-stu-id="dc8ba-202">Instead, both elements are combined into a single entity.</span></span>

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
Found 1 elements
0: one two
```

> [!NOTE]
> <span data-ttu-id="dc8ba-203">Dit probleem wordt opgelost in Power shell 6,2.</span><span class="sxs-lookup"><span data-stu-id="dc8ba-203">This issue is resolved in PowerShell 6.2.</span></span>

#### <a name="helpmessage-argument"></a><span data-ttu-id="dc8ba-204">HelpMessage-argument</span><span class="sxs-lookup"><span data-stu-id="dc8ba-204">HelpMessage argument</span></span>

<span data-ttu-id="dc8ba-205">Het `HelpMessage` argument geeft een teken reeks die een korte beschrijving van de para meter of de waarde ervan bevat.</span><span class="sxs-lookup"><span data-stu-id="dc8ba-205">The `HelpMessage` argument specifies a string that contains a brief description of the parameter or its value.</span></span> <span data-ttu-id="dc8ba-206">In Power shell wordt dit bericht weer gegeven in de prompt die wordt weer gegeven wanneer een verplichte parameter waarde ontbreekt in een opdracht.</span><span class="sxs-lookup"><span data-stu-id="dc8ba-206">PowerShell displays this message in the prompt that appears when a mandatory parameter value is missing from a command.</span></span> <span data-ttu-id="dc8ba-207">Dit argument heeft geen effect op optionele para meters.</span><span class="sxs-lookup"><span data-stu-id="dc8ba-207">This argument has no effect on optional parameters.</span></span>

<span data-ttu-id="dc8ba-208">In het volgende voor beeld declareert u een verplichte para meter **ComputerName** en een Help-bericht waarin de verwachte parameter waarde wordt uitgelegd.</span><span class="sxs-lookup"><span data-stu-id="dc8ba-208">The following example declares a mandatory **ComputerName** parameter and a help message that explains the expected parameter value.</span></span>

<span data-ttu-id="dc8ba-209">Als er geen andere [Help-syntaxis op basis van opmerkingen](./about_comment_based_help.md) is voor de functie (bijvoorbeeld `.SYNOPSIS` ), wordt dit bericht ook weer gegeven in `Get-Help` uitvoer.</span><span class="sxs-lookup"><span data-stu-id="dc8ba-209">If there is no other [comment-based help](./about_comment_based_help.md) syntax for the function (for example, `.SYNOPSIS`) then this message also shows up in `Get-Help` output.</span></span>

```powershell
Param(
    [Parameter(Mandatory=$true,
    HelpMessage="Enter one or more computer names separated by commas.")]
    [String[]]
    $ComputerName
)
```

### <a name="alias-attribute"></a><span data-ttu-id="dc8ba-210">Alias kenmerk</span><span class="sxs-lookup"><span data-stu-id="dc8ba-210">Alias attribute</span></span>

<span data-ttu-id="dc8ba-211">Met het **alias** kenmerk wordt een alternatieve naam voor de para meter gemaakt.</span><span class="sxs-lookup"><span data-stu-id="dc8ba-211">The **Alias** attribute establishes an alternate name for the parameter.</span></span>
<span data-ttu-id="dc8ba-212">Er is geen limiet voor het aantal aliassen dat u aan een para meter kunt toewijzen.</span><span class="sxs-lookup"><span data-stu-id="dc8ba-212">There's no limit to the number of aliases that you can assign to a parameter.</span></span>

<span data-ttu-id="dc8ba-213">In het volgende voor beeld ziet u een parameter declaratie waarmee de **CN** -en **MachineName** -aliassen worden toegevoegd aan de verplichte para meter **ComputerName** .</span><span class="sxs-lookup"><span data-stu-id="dc8ba-213">The following example shows a parameter declaration that adds the **CN** and **MachineName** aliases to the mandatory **ComputerName** parameter.</span></span>

```powershell
Param(
    [Parameter(Mandatory=$true)]
    [Alias("CN","MachineName")]
    [String[]]
    $ComputerName
)
```

### <a name="supportswildcards-attribute"></a><span data-ttu-id="dc8ba-214">SupportsWildcards-kenmerk</span><span class="sxs-lookup"><span data-stu-id="dc8ba-214">SupportsWildcards attribute</span></span>

<span data-ttu-id="dc8ba-215">Het kenmerk **SupportsWildcards** wordt gebruikt om aan te geven dat de para meter Joker teken waarden accepteert.</span><span class="sxs-lookup"><span data-stu-id="dc8ba-215">The **SupportsWildcards** attribute is used to indicate that the parameter accepts wildcard values.</span></span> <span data-ttu-id="dc8ba-216">In het volgende voor beeld ziet u een parameter declaratie voor een verplichte para meter **Path** die waarden voor joker tekens ondersteunt.</span><span class="sxs-lookup"><span data-stu-id="dc8ba-216">The following example shows a parameter declaration for a mandatory **Path** parameter that supports wildcard values.</span></span>

```powershell
Param(
    [Parameter(Mandatory=$true)]
    [SupportsWildcards()]
    [String[]]
    $Path
)
```

<span data-ttu-id="dc8ba-217">Als u dit kenmerk gebruikt, wordt ondersteuning voor joker tekens niet automatisch ingeschakeld.</span><span class="sxs-lookup"><span data-stu-id="dc8ba-217">Using this attribute does not automatically enable wildcard support.</span></span> <span data-ttu-id="dc8ba-218">De cmdlet-ontwikkelaar moet de code implementeren voor het afhandelen van de invoer van het Joker teken.</span><span class="sxs-lookup"><span data-stu-id="dc8ba-218">The cmdlet developer must implement the code to handle the wildcard input.</span></span> <span data-ttu-id="dc8ba-219">De ondersteunde joker tekens kunnen variëren, afhankelijk van de onderliggende API of Power shell-provider.</span><span class="sxs-lookup"><span data-stu-id="dc8ba-219">The wildcards supported can vary according to the underlying API or PowerShell provider.</span></span> <span data-ttu-id="dc8ba-220">Zie [about_Wildcards](about_Wildcards.md)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="dc8ba-220">For more information, see [about_Wildcards](about_Wildcards.md).</span></span>

### <a name="parameter-and-variable-validation-attributes"></a><span data-ttu-id="dc8ba-221">Validatie kenmerken voor para meters en variabelen</span><span class="sxs-lookup"><span data-stu-id="dc8ba-221">Parameter and variable validation attributes</span></span>

<span data-ttu-id="dc8ba-222">Validatie kenmerken direct Power shell voor het testen van de parameter waarden die gebruikers verzenden wanneer ze de functie Advanced aanroepen.</span><span class="sxs-lookup"><span data-stu-id="dc8ba-222">Validation attributes direct PowerShell to test the parameter values that users submit when they call the advanced function.</span></span> <span data-ttu-id="dc8ba-223">Als de parameter waarden de test niet uitvoeren, wordt er een fout gegenereerd en wordt de functie niet aangeroepen.</span><span class="sxs-lookup"><span data-stu-id="dc8ba-223">If the parameter values fail the test, an error is generated and the function isn't called.</span></span> <span data-ttu-id="dc8ba-224">Parameter validatie wordt alleen toegepast op de opgegeven invoer en andere waarden, zoals standaard waarden, worden niet gevalideerd.</span><span class="sxs-lookup"><span data-stu-id="dc8ba-224">Parameter validation is only applied to the input provided and any other values like default values are not validated.</span></span>

<span data-ttu-id="dc8ba-225">U kunt ook de validatie kenmerken gebruiken om de waarden te beperken die gebruikers voor variabelen kunnen opgeven.</span><span class="sxs-lookup"><span data-stu-id="dc8ba-225">You can also use the validation attributes to restrict the values that users can specify for variables.</span></span> <span data-ttu-id="dc8ba-226">Wanneer u een type-Converter gebruikt in combi natie met een validatie kenmerk, moet het type Converter worden gedefinieerd vóór het kenmerk.</span><span class="sxs-lookup"><span data-stu-id="dc8ba-226">When you use a type converter along with a validation attribute, the type converter has to be defined before the attribute.</span></span>

```powershell
[int32][AllowNull()] $number = 7
```

### <a name="allownull-validation-attribute"></a><span data-ttu-id="dc8ba-227">Validatie kenmerk AllowNull</span><span class="sxs-lookup"><span data-stu-id="dc8ba-227">AllowNull validation attribute</span></span>

<span data-ttu-id="dc8ba-228">Met het kenmerk **AllowNull** kan de waarde van een verplichte para meter zijn `$null` .</span><span class="sxs-lookup"><span data-stu-id="dc8ba-228">The **AllowNull** attribute allows the value of a mandatory parameter to be `$null`.</span></span> <span data-ttu-id="dc8ba-229">In het volgende voor beeld wordt een hashtabel **ComputerInfo** -para meter gedeclareerd die een **Null** -waarde kan hebben.</span><span class="sxs-lookup"><span data-stu-id="dc8ba-229">The following example declares a hashtable **ComputerInfo** parameter that can have a **null** value.</span></span>

```powershell
Param(
    [Parameter(Mandatory=$true)]
    [AllowNull()]
    [hashtable]
    $ComputerInfo
)
```

> [!NOTE]
> <span data-ttu-id="dc8ba-230">Het kenmerk **AllowNull** werkt niet als het type Converter is ingesteld op teken reeks, omdat het teken reeks type geen null-waarde accepteert.</span><span class="sxs-lookup"><span data-stu-id="dc8ba-230">The **AllowNull** attribute doesn't work if the type converter is set to string as the string type will not accept a null value.</span></span> <span data-ttu-id="dc8ba-231">U kunt het kenmerk **AllowEmptyString** gebruiken voor dit scenario.</span><span class="sxs-lookup"><span data-stu-id="dc8ba-231">You can use the **AllowEmptyString** attribute for this scenario.</span></span>

### <a name="allowemptystring-validation-attribute"></a><span data-ttu-id="dc8ba-232">Validatie kenmerk AllowEmptyString</span><span class="sxs-lookup"><span data-stu-id="dc8ba-232">AllowEmptyString validation attribute</span></span>

<span data-ttu-id="dc8ba-233">Met het kenmerk **AllowEmptyString** kan de waarde van een verplichte para meter een lege teken reeks ( `""` ) zijn.</span><span class="sxs-lookup"><span data-stu-id="dc8ba-233">The **AllowEmptyString** attribute allows the value of a mandatory parameter to be an empty string (`""`).</span></span> <span data-ttu-id="dc8ba-234">In het volgende voor beeld wordt een **ComputerName** -para meter gedeclareerd die een lege teken reeks waarde kan hebben.</span><span class="sxs-lookup"><span data-stu-id="dc8ba-234">The following example declares a **ComputerName** parameter that can have an empty string value.</span></span>

```powershell
Param(
    [Parameter(Mandatory=$true)]
    [AllowEmptyString()]
    [String]
    $ComputerName
)
```

### <a name="allowemptycollection-validation-attribute"></a><span data-ttu-id="dc8ba-235">Validatie kenmerk AllowEmptyCollection</span><span class="sxs-lookup"><span data-stu-id="dc8ba-235">AllowEmptyCollection validation attribute</span></span>

<span data-ttu-id="dc8ba-236">Met het kenmerk **AllowEmptyCollection** kan de waarde van een verplichte para meter een lege verzameling zijn `@()` .</span><span class="sxs-lookup"><span data-stu-id="dc8ba-236">The **AllowEmptyCollection** attribute allows the value of a mandatory parameter to be an empty collection `@()`.</span></span> <span data-ttu-id="dc8ba-237">In het volgende voor beeld wordt een **ComputerName** -para meter gedeclareerd die een lege verzamelings waarde kan hebben.</span><span class="sxs-lookup"><span data-stu-id="dc8ba-237">The following example declares a **ComputerName** parameter that can have an empty collection value.</span></span>

```powershell
Param(
    [Parameter(Mandatory=$true)]
    [AllowEmptyCollection()]
    [String[]]
    $ComputerName
)
```

### <a name="validatecount-validation-attribute"></a><span data-ttu-id="dc8ba-238">Validatie kenmerk ValidateCount</span><span class="sxs-lookup"><span data-stu-id="dc8ba-238">ValidateCount validation attribute</span></span>

<span data-ttu-id="dc8ba-239">Het kenmerk **ValidateCount** geeft het minimale en maximale aantal parameter waarden op dat door een para meter wordt geaccepteerd.</span><span class="sxs-lookup"><span data-stu-id="dc8ba-239">The **ValidateCount** attribute specifies the minimum and maximum number of parameter values that a parameter accepts.</span></span> <span data-ttu-id="dc8ba-240">In Power shell wordt een fout gegenereerd als het aantal parameter waarden in de opdracht die de functie aanroept buiten dat bereik valt.</span><span class="sxs-lookup"><span data-stu-id="dc8ba-240">PowerShell generates an error if the number of parameter values in the command that calls the function is outside that range.</span></span>

<span data-ttu-id="dc8ba-241">Met de volgende parameter declaratie wordt een **ComputerName** -para meter gemaakt die één tot vijf parameter waarden nodig heeft.</span><span class="sxs-lookup"><span data-stu-id="dc8ba-241">The following parameter declaration creates a **ComputerName** parameter that takes one to five parameter values.</span></span>

```powershell
Param(
    [Parameter(Mandatory=$true)]
    [ValidateCount(1,5)]
    [String[]]
    $ComputerName
)
```

### <a name="validatelength-validation-attribute"></a><span data-ttu-id="dc8ba-242">Validatie kenmerk ValidateLength</span><span class="sxs-lookup"><span data-stu-id="dc8ba-242">ValidateLength validation attribute</span></span>

<span data-ttu-id="dc8ba-243">Het kenmerk **ValidateLength** geeft het minimale en maximale aantal tekens in een para meter of variabele waarde aan.</span><span class="sxs-lookup"><span data-stu-id="dc8ba-243">The **ValidateLength** attribute specifies the minimum and maximum number of characters in a parameter or variable value.</span></span> <span data-ttu-id="dc8ba-244">Power shell genereert een fout als de lengte van een opgegeven waarde voor een para meter of variabele buiten het bereik valt.</span><span class="sxs-lookup"><span data-stu-id="dc8ba-244">PowerShell generates an error if the length of a value specified for a parameter or a variable is outside of the range.</span></span>

<span data-ttu-id="dc8ba-245">In het volgende voor beeld moet elke computer naam een tot tien tekens bevatten.</span><span class="sxs-lookup"><span data-stu-id="dc8ba-245">In the following example, each computer name must have one to ten characters.</span></span>

```powershell
Param(
    [Parameter(Mandatory=$true)]
    [ValidateLength(1,10)]
    [String[]]
    $ComputerName
)
```

<span data-ttu-id="dc8ba-246">In het volgende voor beeld moet de waarde van de variabele `$number` Mini maal één teken lang zijn en Maxi maal tien tekens bevatten.</span><span class="sxs-lookup"><span data-stu-id="dc8ba-246">In the following example, the value of the variable `$number` must be a minimum of one character in length, and a maximum of ten characters.</span></span>

```powershell
[Int32][ValidateLength(1,10)]$number = '01'
```

> [!NOTE]
> <span data-ttu-id="dc8ba-247">In dit voor beeld is de waarde van `01` wordt ingepakt in enkele aanhalings tekens.</span><span class="sxs-lookup"><span data-stu-id="dc8ba-247">In this example, the value of `01` is wrapped in single quotes.</span></span> <span data-ttu-id="dc8ba-248">Het kenmerk **ValidateLength** accepteert geen getal zonder aanhalings tekens.</span><span class="sxs-lookup"><span data-stu-id="dc8ba-248">The **ValidateLength** attribute won't accept a number without being wrapped in quotes.</span></span>

### <a name="validatepattern-validation-attribute"></a><span data-ttu-id="dc8ba-249">Validatie kenmerk ValidatePattern</span><span class="sxs-lookup"><span data-stu-id="dc8ba-249">ValidatePattern validation attribute</span></span>

<span data-ttu-id="dc8ba-250">Het kenmerk **ValidatePattern** geeft een reguliere expressie aan die wordt vergeleken met de waarde van de para meter of variabele.</span><span class="sxs-lookup"><span data-stu-id="dc8ba-250">The **ValidatePattern** attribute specifies a regular expression that's compared to the parameter or variable value.</span></span> <span data-ttu-id="dc8ba-251">Power shell genereert een fout als de waarde niet overeenkomt met het reguliere-expressie patroon.</span><span class="sxs-lookup"><span data-stu-id="dc8ba-251">PowerShell generates an error if the value doesn't match the regular expression pattern.</span></span>

<span data-ttu-id="dc8ba-252">In het volgende voor beeld moet de parameter waarde een getal van vier cijfers bevatten en elk cijfer moet een getal van nul tot negen zijn.</span><span class="sxs-lookup"><span data-stu-id="dc8ba-252">In the following example, the parameter value must contain a four-digit number, and each digit must be a number zero to nine.</span></span>

```powershell
Param(
    [Parameter(Mandatory=$true)]
    [ValidatePattern("[0-9][0-9][0-9][0-9]")]
    [String[]]
    $ComputerName
)
```

<span data-ttu-id="dc8ba-253">In het volgende voor beeld moet de waarde van de variabele `$number` exact een getal van vier cijfers zijn en moet elk cijfer een getal van nul tot negen zijn.</span><span class="sxs-lookup"><span data-stu-id="dc8ba-253">In the following example, the value of the variable `$number` must be exactly a four-digit number, and each digit must be a number zero to nine.</span></span>

```powershell
[Int32][ValidatePattern("^[0-9][0-9][0-9][0-9]$")]$number = 1111
```

### <a name="validaterange-validation-attribute"></a><span data-ttu-id="dc8ba-254">Validatie kenmerk ValidateRange</span><span class="sxs-lookup"><span data-stu-id="dc8ba-254">ValidateRange validation attribute</span></span>

<span data-ttu-id="dc8ba-255">Het kenmerk **ValidateRange** geeft een numeriek bereik voor elke para meter of variabele waarde aan.</span><span class="sxs-lookup"><span data-stu-id="dc8ba-255">The **ValidateRange** attribute specifies a numeric range for each parameter or variable value.</span></span> <span data-ttu-id="dc8ba-256">Power shell genereert een fout als een wille keurige waarde buiten dat bereik valt.</span><span class="sxs-lookup"><span data-stu-id="dc8ba-256">PowerShell generates an error if any value is outside that range.</span></span> <span data-ttu-id="dc8ba-257">In het volgende voor beeld moet de waarde van de para meter **pogingen** tussen nul en tien zijn.</span><span class="sxs-lookup"><span data-stu-id="dc8ba-257">In the following example, the value of the **Attempts** parameter must be between zero and ten.</span></span>

```powershell
Param(
    [Parameter(Mandatory=$true)]
    [ValidateRange(0,10)]
    [Int]
    $Attempts
)
```

<span data-ttu-id="dc8ba-258">In het volgende voor beeld moet de waarde van de variabele `$number` tussen 0 en tien zijn.</span><span class="sxs-lookup"><span data-stu-id="dc8ba-258">In the following example, the value of the variable `$number` must be between zero and ten.</span></span>

```powershell
[Int32][ValidateRange(0,10)]$number = 5
```

### <a name="validatescript-validation-attribute"></a><span data-ttu-id="dc8ba-259">Validatie kenmerk ValidateScript</span><span class="sxs-lookup"><span data-stu-id="dc8ba-259">ValidateScript validation attribute</span></span>

<span data-ttu-id="dc8ba-260">Het kenmerk **ValidateScript** geeft een script op dat wordt gebruikt om een para meter of variabele waarde te valideren.</span><span class="sxs-lookup"><span data-stu-id="dc8ba-260">The **ValidateScript** attribute specifies a script that is used to validate a parameter or variable value.</span></span> <span data-ttu-id="dc8ba-261">Power shell Pipet de waarde naar het script en genereert een fout als het script wordt geretourneerd `$false` of als het script een uitzonde ring genereert.</span><span class="sxs-lookup"><span data-stu-id="dc8ba-261">PowerShell pipes the value to the script, and generates an error if the script returns `$false` or if the script throws an exception.</span></span>

<span data-ttu-id="dc8ba-262">Wanneer u het kenmerk **ValidateScript** gebruikt, wordt de te valideren waarde toegewezen aan de `$_` variabele.</span><span class="sxs-lookup"><span data-stu-id="dc8ba-262">When you use the **ValidateScript** attribute, the value that's being validated is mapped to the `$_` variable.</span></span> <span data-ttu-id="dc8ba-263">U kunt de `$_` variabele gebruiken om te verwijzen naar de waarde in het script.</span><span class="sxs-lookup"><span data-stu-id="dc8ba-263">You can use the `$_` variable to refer to the value in the script.</span></span>

<span data-ttu-id="dc8ba-264">In het volgende voor beeld moet de waarde van de para meter **EventDate** groter zijn dan of gelijk zijn aan de huidige datum.</span><span class="sxs-lookup"><span data-stu-id="dc8ba-264">In the following example, the value of the **EventDate** parameter must be greater than or equal to the current date.</span></span>

```powershell
Param(
    [Parameter(Mandatory=$true)]
    [ValidateScript({$_ -ge (Get-Date)})]
    [DateTime]
    $EventDate
)
```

<span data-ttu-id="dc8ba-265">In het volgende voor beeld moet de waarde van de variabele `$date` groter zijn dan of gelijk zijn aan de huidige datum en tijd.</span><span class="sxs-lookup"><span data-stu-id="dc8ba-265">In the following example, the value of the variable `$date` must be greater than or equal to the current date and time.</span></span>

```powershell
[DateTime][ValidateScript({$_ -ge (Get-Date)})]$date = (Get-Date)
```

> [!NOTE]
> <span data-ttu-id="dc8ba-266">Als u **ValidateScript** gebruikt, kunt u geen waarde door geven `$null` aan de para meter.</span><span class="sxs-lookup"><span data-stu-id="dc8ba-266">If you use **ValidateScript** , you cannot pass a `$null` value to the parameter.</span></span> <span data-ttu-id="dc8ba-267">Wanneer u een null-waarde doorgeeft **ValidateScript** kan het argument niet valideren.</span><span class="sxs-lookup"><span data-stu-id="dc8ba-267">When you pass a null value **ValidateScript** can't validate the argument.</span></span>

### <a name="validateset-attribute"></a><span data-ttu-id="dc8ba-268">Het kenmerk validate</span><span class="sxs-lookup"><span data-stu-id="dc8ba-268">ValidateSet attribute</span></span>

<span data-ttu-id="dc8ba-269">Het kenmerk **Validate** bevat een set geldige waarden voor een para meter of variabele en schakelt het volt ooien van het tabblad in.</span><span class="sxs-lookup"><span data-stu-id="dc8ba-269">The **ValidateSet** attribute specifies a set of valid values for a parameter or variable and enables tab completion.</span></span> <span data-ttu-id="dc8ba-270">Power shell genereert een fout als een para meter of variabele waarde niet overeenkomt met een waarde in de set.</span><span class="sxs-lookup"><span data-stu-id="dc8ba-270">PowerShell generates an error if a parameter or variable value doesn't match a value in the set.</span></span> <span data-ttu-id="dc8ba-271">In het volgende voor beeld kan de waarde van de para meter **detail** alleen laag, gemiddeld of hoog zijn.</span><span class="sxs-lookup"><span data-stu-id="dc8ba-271">In the following example, the value of the **Detail** parameter can only be Low, Average, or High.</span></span>

```powershell
Param(
    [Parameter(Mandatory=$true)]
    [ValidateSet("Low", "Average", "High")]
    [String[]]
    $Detail
)
```

<span data-ttu-id="dc8ba-272">In het volgende voor beeld moet de waarde van de variabele `$flavor` Choco lade, aard beien of vanille zijn.</span><span class="sxs-lookup"><span data-stu-id="dc8ba-272">In the following example, the value of the variable `$flavor` must be either Chocolate, Strawberry, or Vanilla.</span></span>

```powershell
[ValidateSet("Chocolate", "Strawberry", "Vanilla")]
[String]$flavor = "Strawberry"
```

<span data-ttu-id="dc8ba-273">De validatie wordt uitgevoerd wanneer deze variabele wordt toegewezen, zelfs binnen het script.</span><span class="sxs-lookup"><span data-stu-id="dc8ba-273">The validation occurs whenever that variable is assigned even within the script.</span></span> <span data-ttu-id="dc8ba-274">Het volgende resulteert bijvoorbeeld in een fout tijdens runtime:</span><span class="sxs-lookup"><span data-stu-id="dc8ba-274">For example, the following results in an error at runtime:</span></span>

```powershell
Param(
    [ValidateSet("hello", "world")]
    [String]$Message
)

$Message = "bye"
```

### <a name="validatenotnull-validation-attribute"></a><span data-ttu-id="dc8ba-275">Validatie kenmerk ValidateNotNull</span><span class="sxs-lookup"><span data-stu-id="dc8ba-275">ValidateNotNull validation attribute</span></span>

<span data-ttu-id="dc8ba-276">Het kenmerk **ValidateNotNull** geeft aan dat de parameter waarde niet kan zijn `$null` .</span><span class="sxs-lookup"><span data-stu-id="dc8ba-276">The **ValidateNotNull** attribute specifies that the parameter value can't be `$null`.</span></span> <span data-ttu-id="dc8ba-277">Power shell genereert een fout als de waarde van de para meter `$null` .</span><span class="sxs-lookup"><span data-stu-id="dc8ba-277">PowerShell generates an error if the parameter value is `$null`.</span></span>

<span data-ttu-id="dc8ba-278">Het kenmerk **ValidateNotNull** is ontworpen om te worden gebruikt wanneer de para meter optioneel is en het type is niet gedefinieerd of een type Converter heeft dat een null-waarde zoals een **object** niet impliciet kan converteren.</span><span class="sxs-lookup"><span data-stu-id="dc8ba-278">The **ValidateNotNull** attribute is designed to be used when the parameter is optional and the type is undefined or has a type converter that can't implicitly convert a null value like **object**.</span></span> <span data-ttu-id="dc8ba-279">Als u een type opgeeft dat impliciet een null-waarde, zoals een **teken reeks** , converteert, wordt de null-waarde omgezet in een lege teken reeks, zelfs wanneer het kenmerk **ValidateNotNull** wordt gebruikt.</span><span class="sxs-lookup"><span data-stu-id="dc8ba-279">If you specify a type that that will implicitly convert a null value such as a **string** , the null value is converted to an empty string even when using the **ValidateNotNull** attribute.</span></span> <span data-ttu-id="dc8ba-280">Voor dit scenario gebruikt u de **ValidateNotNullOrEmpty**</span><span class="sxs-lookup"><span data-stu-id="dc8ba-280">For this scenario use the **ValidateNotNullOrEmpty**</span></span>

<span data-ttu-id="dc8ba-281">In het volgende voor beeld kan de waarde van de para meter **id** niet zijn `$null` .</span><span class="sxs-lookup"><span data-stu-id="dc8ba-281">In the following example, the value of the **ID** parameter can't be `$null`.</span></span>

```powershell
Param(
    [Parameter(Mandatory=$false)]
    [ValidateNotNull()]
    $ID
)
```

### <a name="validatenotnullorempty-validation-attribute"></a><span data-ttu-id="dc8ba-282">Validatie kenmerk ValidateNotNullOrEmpty</span><span class="sxs-lookup"><span data-stu-id="dc8ba-282">ValidateNotNullOrEmpty validation attribute</span></span>

<span data-ttu-id="dc8ba-283">Het kenmerk **ValidateNotNullOrEmpty** geeft aan dat de parameter waarde niet kan zijn `$null` en mag geen lege teken reeks ( `""` ) zijn.</span><span class="sxs-lookup"><span data-stu-id="dc8ba-283">The **ValidateNotNullOrEmpty** attribute specifies that the parameter value can't be `$null` and can't be an empty string (`""`).</span></span> <span data-ttu-id="dc8ba-284">Power shell genereert een fout als de para meter wordt gebruikt in een functie aanroep, maar de waarde hiervan is `$null` , een lege teken reeks ( `""` ) of een lege matrix `@()` .</span><span class="sxs-lookup"><span data-stu-id="dc8ba-284">PowerShell generates an error if the parameter is used in a function call, but its value is `$null`, an empty string (`""`), or an empty array `@()`.</span></span>

```powershell
Param(
    [Parameter(Mandatory=$true)]
    [ValidateNotNullOrEmpty()]
    [String[]]
    $UserName
)
```

### <a name="validatedrive-validation-attribute"></a><span data-ttu-id="dc8ba-285">Validatie kenmerk ValidateDrive</span><span class="sxs-lookup"><span data-stu-id="dc8ba-285">ValidateDrive validation attribute</span></span>

<span data-ttu-id="dc8ba-286">Het kenmerk **ValidateDrive** geeft aan dat de parameter waarde het pad moet vertegenwoordigen, dat alleen verwijst naar de toegestane stations.</span><span class="sxs-lookup"><span data-stu-id="dc8ba-286">The **ValidateDrive** attribute specifies that the parameter value must represent the path, that's referring to allowed drives only.</span></span> <span data-ttu-id="dc8ba-287">Power shell genereert een fout als de waarde van de para meter verwijst naar andere stations dan toegestaan.</span><span class="sxs-lookup"><span data-stu-id="dc8ba-287">PowerShell generates an error if the parameter value refers to drives other than the allowed.</span></span> <span data-ttu-id="dc8ba-288">Het bestaan van het pad, met uitzonde ring van het station zelf, wordt niet gecontroleerd.</span><span class="sxs-lookup"><span data-stu-id="dc8ba-288">Existence of the path, except for the drive itself, isn't verified.</span></span>

<span data-ttu-id="dc8ba-289">Als u een relatief pad gebruikt, moet het huidige station zich in de lijst met toegestane stations bevinden.</span><span class="sxs-lookup"><span data-stu-id="dc8ba-289">If you use relative path, the current drive must be in the allowed drive list.</span></span>

```powershell
Param(
    [ValidateDrive("C", "D", "Variable", "Function")]
    [String]$Path
)
```

### <a name="validateuserdrive-validation-attribute"></a><span data-ttu-id="dc8ba-290">Validatie kenmerk ValidateUserDrive</span><span class="sxs-lookup"><span data-stu-id="dc8ba-290">ValidateUserDrive validation attribute</span></span>

<span data-ttu-id="dc8ba-291">Het kenmerk **ValidateUserDrive** geeft aan dat de parameter waarde het pad moet vertegenwoordigen dat verwijst naar een `User` station.</span><span class="sxs-lookup"><span data-stu-id="dc8ba-291">The **ValidateUserDrive** attribute specifies that the parameter value must represent the path, that is referring to `User` drive.</span></span> <span data-ttu-id="dc8ba-292">Power shell genereert een fout melding als het pad naar een ander station verwijst.</span><span class="sxs-lookup"><span data-stu-id="dc8ba-292">PowerShell generates an error if the path refers to a different drive.</span></span> <span data-ttu-id="dc8ba-293">Het validatie kenmerk test alleen op het bestaan van het station gedeelte van het pad.</span><span class="sxs-lookup"><span data-stu-id="dc8ba-293">The validation attribute only tests for the existence of the drive portion of the path.</span></span>

<span data-ttu-id="dc8ba-294">Als u een relatief pad gebruikt, moet het huidige station zijn `User` .</span><span class="sxs-lookup"><span data-stu-id="dc8ba-294">If you use relative path, the current drive must be `User`.</span></span>

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

<span data-ttu-id="dc8ba-295">U kunt een `User` station definiëren in net voldoende beheer-en JEA-sessie configuraties.</span><span class="sxs-lookup"><span data-stu-id="dc8ba-295">You can define `User` drive in Just Enough Administration (JEA) session configurations.</span></span> <span data-ttu-id="dc8ba-296">Voor dit voor beeld maken we de gebruiker: station.</span><span class="sxs-lookup"><span data-stu-id="dc8ba-296">For this example, we create the User: drive.</span></span>

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

### <a name="validatetrusteddata-validation-attribute"></a><span data-ttu-id="dc8ba-297">Validatie kenmerk ValidateTrustedData</span><span class="sxs-lookup"><span data-stu-id="dc8ba-297">ValidateTrustedData validation attribute</span></span>

<span data-ttu-id="dc8ba-298">Dit kenmerk is toegevoegd aan Power shell 6.1.1.</span><span class="sxs-lookup"><span data-stu-id="dc8ba-298">This attribute was added in PowerShell 6.1.1.</span></span>

<span data-ttu-id="dc8ba-299">Op dit moment wordt het kenmerk intern gebruikt door Power shell zelf en is het niet bedoeld voor extern gebruik.</span><span class="sxs-lookup"><span data-stu-id="dc8ba-299">At this time, the attribute is used internally by PowerShell itself and is not intended for external usage.</span></span>

## <a name="dynamic-parameters"></a><span data-ttu-id="dc8ba-300">Dynamische parameters</span><span class="sxs-lookup"><span data-stu-id="dc8ba-300">Dynamic parameters</span></span>

<span data-ttu-id="dc8ba-301">Dynamische para meters zijn para meters van een cmdlet, functie of script die alleen beschikbaar zijn onder bepaalde voor waarden.</span><span class="sxs-lookup"><span data-stu-id="dc8ba-301">Dynamic parameters are parameters of a cmdlet, function, or script that are available only under certain conditions.</span></span>

<span data-ttu-id="dc8ba-302">Meerdere provider-cmdlets hebben bijvoorbeeld para meters die alleen beschikbaar zijn wanneer de cmdlet wordt gebruikt in het provider station of in een bepaald pad van het provider station.</span><span class="sxs-lookup"><span data-stu-id="dc8ba-302">For example, several provider cmdlets have parameters that are available only when the cmdlet is used in the provider drive, or in a particular path of the provider drive.</span></span> <span data-ttu-id="dc8ba-303">De para meter **Encoding** is bijvoorbeeld alleen beschikbaar in de `Add-Content` `Get-Content` `Set-Content` cmdlets, en alleen als deze wordt gebruikt in een bestandssysteem station.</span><span class="sxs-lookup"><span data-stu-id="dc8ba-303">For example, the **Encoding** parameter is available on the `Add-Content`, `Get-Content`, and `Set-Content` cmdlets only when it's used in a file system drive.</span></span>

<span data-ttu-id="dc8ba-304">U kunt ook een para meter maken die alleen wordt weer gegeven wanneer een andere para meter wordt gebruikt in de functie opdracht of wanneer een andere para meter een bepaalde waarde heeft.</span><span class="sxs-lookup"><span data-stu-id="dc8ba-304">You can also create a parameter that appears only when another parameter is used in the function command or when another parameter has a certain value.</span></span>

<span data-ttu-id="dc8ba-305">Dynamische para meters kunnen nuttig zijn, maar alleen gebruiken wanneer dat nodig is, omdat ze moeilijk kunnen worden gedetecteerd door gebruikers.</span><span class="sxs-lookup"><span data-stu-id="dc8ba-305">Dynamic parameters can be useful, but use them only when necessary, because they can be difficult for users to discover.</span></span> <span data-ttu-id="dc8ba-306">Als u een dynamische para meter wilt zoeken, moet de gebruiker zich in het pad van de provider bevinden, de para meter **argument List** van de `Get-Command` cmdlet gebruiken of de para meter **Path** van gebruiken `Get-Help` .</span><span class="sxs-lookup"><span data-stu-id="dc8ba-306">To find a dynamic parameter, the user must be in the provider path, use the **ArgumentList** parameter of the `Get-Command` cmdlet, or use the **Path** parameter of `Get-Help`.</span></span>

<span data-ttu-id="dc8ba-307">Als u een dynamische para meter voor een functie of script wilt maken, gebruikt u het `DynamicParam` sleutel woord.</span><span class="sxs-lookup"><span data-stu-id="dc8ba-307">To create a dynamic parameter for a function or script, use the `DynamicParam` keyword.</span></span>

<span data-ttu-id="dc8ba-308">De syntaxis is als volgt:</span><span class="sxs-lookup"><span data-stu-id="dc8ba-308">The syntax is as follows:</span></span>

`DynamicParam {<statement-list>}`

<span data-ttu-id="dc8ba-309">Gebruik in de lijst overzicht een `If` instructie om de voor waarden op te geven waaronder de para meter beschikbaar is in de functie.</span><span class="sxs-lookup"><span data-stu-id="dc8ba-309">In the statement list, use an `If` statement to specify the conditions under which the parameter is available in the function.</span></span>

<span data-ttu-id="dc8ba-310">Gebruik de `New-Object` cmdlet om een **System. Management. Automation. RuntimeDefinedParameter** -object te maken dat de para meter weergeeft en geef de naam op.</span><span class="sxs-lookup"><span data-stu-id="dc8ba-310">Use the `New-Object` cmdlet to create a **System.Management.Automation.RuntimeDefinedParameter** object to represent the parameter and specify its name.</span></span>

<span data-ttu-id="dc8ba-311">U kunt een `New-Object` opdracht gebruiken om een **System. Management. Automation. ParameterAttribute** -object te maken om kenmerken van de para meter weer te geven, zoals **verplicht** , **positie** of **ValueFromPipeline** of de bijbehorende parameterset.</span><span class="sxs-lookup"><span data-stu-id="dc8ba-311">You can use a `New-Object` command to create a **System.Management.Automation.ParameterAttribute** object to represent attributes of the parameter, such as **Mandatory** , **Position** , or **ValueFromPipeline** or its parameter set.</span></span>

<span data-ttu-id="dc8ba-312">In het volgende voor beeld ziet u een voorbeeld functie met de standaard parameters **name** en **Path** en een optionele dynamische para meter met de naam **DP1**.</span><span class="sxs-lookup"><span data-stu-id="dc8ba-312">The following example shows a sample function with standard parameters named **Name** and **Path** , and an optional dynamic parameter named **DP1**.</span></span> <span data-ttu-id="dc8ba-313">De **DP1** -para meter bevindt zich in de `PSet1` parameterset en heeft een type van `Int32` .</span><span class="sxs-lookup"><span data-stu-id="dc8ba-313">The **DP1** parameter is in the `PSet1` parameter set and has a type of `Int32`.</span></span>
<span data-ttu-id="dc8ba-314">De para meter **DP1** is alleen beschikbaar in de `Get-Sample` functie wanneer de waarde van de para meter **Path** begint met `HKLM:` , wat aangeeft dat deze wordt gebruikt in het `HKEY_LOCAL_MACHINE` register station.</span><span class="sxs-lookup"><span data-stu-id="dc8ba-314">The **DP1** parameter is available in the `Get-Sample` function only when the value of the **Path** parameter starts with `HKLM:`, indicating that it's being used in the `HKEY_LOCAL_MACHINE` registry drive.</span></span>

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

<span data-ttu-id="dc8ba-315">Zie [RuntimeDefinedParameter](/dotnet/api/system.management.automation.runtimedefinedparameter)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="dc8ba-315">For more information, see [RuntimeDefinedParameter](/dotnet/api/system.management.automation.runtimedefinedparameter).</span></span>

## <a name="switch-parameters"></a><span data-ttu-id="dc8ba-316">Switch parameters</span><span class="sxs-lookup"><span data-stu-id="dc8ba-316">Switch parameters</span></span>

<span data-ttu-id="dc8ba-317">Switch parameters zijn para meters zonder parameter waarde.</span><span class="sxs-lookup"><span data-stu-id="dc8ba-317">Switch parameters are parameters with no parameter value.</span></span> <span data-ttu-id="dc8ba-318">Ze zijn alleen effectief als ze worden gebruikt en slechts één effect hebben.</span><span class="sxs-lookup"><span data-stu-id="dc8ba-318">They're effective only when they're used and have only one effect.</span></span>

<span data-ttu-id="dc8ba-319">De para meter geen **profiel** van **powershell.exe** is bijvoorbeeld een para meter switch.</span><span class="sxs-lookup"><span data-stu-id="dc8ba-319">For example, the **NoProfile** parameter of **powershell.exe** is a switch parameter.</span></span>

<span data-ttu-id="dc8ba-320">Als u een switch parameter in een functie wilt maken, geeft u het `Switch` type op in de parameter definitie.</span><span class="sxs-lookup"><span data-stu-id="dc8ba-320">To create a switch parameter in a function, specify the `Switch` type in the parameter definition.</span></span>

<span data-ttu-id="dc8ba-321">Bijvoorbeeld:</span><span class="sxs-lookup"><span data-stu-id="dc8ba-321">For example:</span></span>

```powershell
Param([Switch]<ParameterName>)
```

<span data-ttu-id="dc8ba-322">U kunt ook een andere methode gebruiken:</span><span class="sxs-lookup"><span data-stu-id="dc8ba-322">Or, you can use an another method:</span></span>

```powershell
Param(
    [Parameter(Mandatory=$false)]
    [Switch]
    $<ParameterName>
)
```

<span data-ttu-id="dc8ba-323">Switch parameters zijn gemakkelijk te gebruiken en hebben de voor keur boven Boole-para meters, die een moeilijkerere syntaxis hebben.</span><span class="sxs-lookup"><span data-stu-id="dc8ba-323">Switch parameters are easy to use and are preferred over Boolean parameters, which have a more difficult syntax.</span></span>

<span data-ttu-id="dc8ba-324">Als u bijvoorbeeld een para meter switch wilt gebruiken, typt de gebruiker de para meter in de opdracht.</span><span class="sxs-lookup"><span data-stu-id="dc8ba-324">For example, to use a switch parameter, the user types the parameter in the command.</span></span>

`-IncludeAll`

<span data-ttu-id="dc8ba-325">Als u een Boole-para meter wilt gebruiken, typt de gebruiker de para meter en een Booleaanse waarde.</span><span class="sxs-lookup"><span data-stu-id="dc8ba-325">To use a Boolean parameter, the user types the parameter and a Boolean value.</span></span>

`-IncludeAll:$true`

<span data-ttu-id="dc8ba-326">Wanneer u switch parameters maakt, moet u de parameter naam zorgvuldig kiezen.</span><span class="sxs-lookup"><span data-stu-id="dc8ba-326">When creating switch parameters, choose the parameter name carefully.</span></span> <span data-ttu-id="dc8ba-327">Zorg ervoor dat de parameter naam het effect van de para meter communiceert naar de gebruiker.</span><span class="sxs-lookup"><span data-stu-id="dc8ba-327">Be sure that the parameter name communicates the effect of the parameter to the user.</span></span>
<span data-ttu-id="dc8ba-328">Vermijd dubbel zinnige termen, zoals het **filter** of het **maximum** waarmee een waarde kan worden opgelegd.</span><span class="sxs-lookup"><span data-stu-id="dc8ba-328">Avoid ambiguous terms, such as **Filter** or **Maximum** that might imply a value is required.</span></span>

## <a name="argumentcompleter-attribute"></a><span data-ttu-id="dc8ba-329">ArgumentCompleter-kenmerk</span><span class="sxs-lookup"><span data-stu-id="dc8ba-329">ArgumentCompleter attribute</span></span>

<span data-ttu-id="dc8ba-330">Met het kenmerk **ArgumentCompleter** kunt u waarden voor het volt ooien van tabs toevoegen aan een specifieke para meter.</span><span class="sxs-lookup"><span data-stu-id="dc8ba-330">The **ArgumentCompleter** attribute allows you to add tab completion values to a specific parameter.</span></span> <span data-ttu-id="dc8ba-331">Er moet een **ArgumentCompleter** -kenmerk worden gedefinieerd voor elke para meter die het tabblad moet volt ooien.</span><span class="sxs-lookup"><span data-stu-id="dc8ba-331">An **ArgumentCompleter** attribute must be defined for each parameter that needs tab completion.</span></span> <span data-ttu-id="dc8ba-332">Net als bij **DynamicParameters** worden de beschik bare waarden tijdens runtime berekend wanneer de gebruiker op <kbd>Tab</kbd> drukt na de parameter naam.</span><span class="sxs-lookup"><span data-stu-id="dc8ba-332">Similar to **DynamicParameters** , the available values are calculated at runtime when the user presses <kbd>Tab</kbd> after the parameter name.</span></span>

<span data-ttu-id="dc8ba-333">Om een **ArgumentCompleter** -kenmerk toe te voegen, moet u een script blok definiëren waarmee de waarden worden bepaald.</span><span class="sxs-lookup"><span data-stu-id="dc8ba-333">To add an **ArgumentCompleter** attribute, you need to define a script block that determines the values.</span></span> <span data-ttu-id="dc8ba-334">Het script blok moet de volgende para meters in de opgegeven volg orde volgen.</span><span class="sxs-lookup"><span data-stu-id="dc8ba-334">The script block must take the following parameters in the order specified below.</span></span> <span data-ttu-id="dc8ba-335">De namen van de para meters zijn niet belang rijk, omdat de waarden positioneel worden gegeven.</span><span class="sxs-lookup"><span data-stu-id="dc8ba-335">The parameter's names don't matter as the values are provided positionally.</span></span>

<span data-ttu-id="dc8ba-336">De syntaxis is als volgt:</span><span class="sxs-lookup"><span data-stu-id="dc8ba-336">The syntax is as follows:</span></span>

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

### <a name="argumentcompleter-script-block"></a><span data-ttu-id="dc8ba-337">ArgumentCompleter-script blok</span><span class="sxs-lookup"><span data-stu-id="dc8ba-337">ArgumentCompleter script block</span></span>

<span data-ttu-id="dc8ba-338">De script Block-para meters worden ingesteld op de volgende waarden:</span><span class="sxs-lookup"><span data-stu-id="dc8ba-338">The script block parameters are set to the following values:</span></span>

- <span data-ttu-id="dc8ba-339">`$commandName` (Positie 0): deze para meter is ingesteld op de naam van de opdracht waarvoor het script blok het volt ooien van het tabblad oplevert.</span><span class="sxs-lookup"><span data-stu-id="dc8ba-339">`$commandName` (Position 0) - This parameter is set to the name of the command for which the script block is providing tab completion.</span></span>
- <span data-ttu-id="dc8ba-340">`$parameterName` (Positie 1)-deze para meter wordt ingesteld op de para meter waarvan de waarde het volt ooien van het tabblad vereist.</span><span class="sxs-lookup"><span data-stu-id="dc8ba-340">`$parameterName` (Position 1) - This parameter is set to the parameter whose value requires tab completion.</span></span>
- <span data-ttu-id="dc8ba-341">`$wordToComplete` (Positie 2): deze para meter is ingesteld op waarde die de gebruiker heeft opgegeven voordat deze <kbd>Tab</kbd>werd ingedrukt. Het script blok moet deze waarde gebruiken om de waarden voor het volt ooien van tabs te bepalen.</span><span class="sxs-lookup"><span data-stu-id="dc8ba-341">`$wordToComplete` (Position 2) - This parameter is set to value the user has provided before they pressed <kbd>Tab</kbd>. Your script block should use this value to determine tab completion values.</span></span>
- <span data-ttu-id="dc8ba-342">`$commandAst` (Positie 3): deze para meter is ingesteld op de abstracte syntaxis structuur (AST) voor de huidige invoer regel.</span><span class="sxs-lookup"><span data-stu-id="dc8ba-342">`$commandAst` (Position 3) - This parameter is set to the Abstract Syntax Tree (AST) for the current input line.</span></span> <span data-ttu-id="dc8ba-343">Zie [AST class](/dotnet/api/system.management.automation.language.ast)(Engelstalig) voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="dc8ba-343">For more information, see [Ast Class](/dotnet/api/system.management.automation.language.ast).</span></span>
- <span data-ttu-id="dc8ba-344">`$fakeBoundParameters` (Positie 4): deze para meter is ingesteld op een hashtabel die de `$PSBoundParameters` voor de cmdlet bevat, voordat het <kbd>tabblad</kbd>van de gebruiker wordt ingedrukt. Zie [about_Automatic_Variables](about_Automatic_Variables.md)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="dc8ba-344">`$fakeBoundParameters` (Position 4) - This parameter is set to a hashtable containing the `$PSBoundParameters` for the cmdlet, before the user pressed <kbd>Tab</kbd>. For more information, see [about_Automatic_Variables](about_Automatic_Variables.md).</span></span>

<span data-ttu-id="dc8ba-345">Het **ArgumentCompleter** -script blok moet de waarden van de pijp lijn, zoals `ForEach-Object` , `Where-Object` of een andere geschikte methode, ongedaan maken.</span><span class="sxs-lookup"><span data-stu-id="dc8ba-345">The **ArgumentCompleter** script block must unroll the values using the pipeline, such as `ForEach-Object`, `Where-Object`, or another suitable method.</span></span>
<span data-ttu-id="dc8ba-346">Als u een matrix met waarden retourneert, wordt de gehele matrix als **één** waarde voor het volt ooien van een tab behandeld.</span><span class="sxs-lookup"><span data-stu-id="dc8ba-346">Returning an array of values causes PowerShell to treat the entire array as **one** tab completion value.</span></span>

<span data-ttu-id="dc8ba-347">In het volgende voor beeld wordt Tab-aanvulling toegevoegd aan de **waarde** -para meter.</span><span class="sxs-lookup"><span data-stu-id="dc8ba-347">The following example adds tab completion to the **Value** parameter.</span></span> <span data-ttu-id="dc8ba-348">Als alleen de **waarde** para meter is opgegeven, worden alle mogelijke waarden, of argumenten, voor **waarde** weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="dc8ba-348">If only the **Value** parameter is specified, all possible values, or arguments, for **Value** are displayed.</span></span> <span data-ttu-id="dc8ba-349">Als de para meter **type** is opgegeven, geeft de para meter **Value** alleen de mogelijke waarden voor dat type weer.</span><span class="sxs-lookup"><span data-stu-id="dc8ba-349">When the **Type** parameter is specified, the **Value** parameter only displays the possible values for that type.</span></span>

<span data-ttu-id="dc8ba-350">De operator zorgt er ook voor `-like` dat als de gebruiker de volgende opdracht typt en het <kbd>tabblad</kbd> aanvulling gebruikt, alleen **Apple** wordt geretourneerd.</span><span class="sxs-lookup"><span data-stu-id="dc8ba-350">In addition, the `-like` operator ensures that if the user types the following command and uses <kbd>Tab</kbd> completion, only **Apple** is returned.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="dc8ba-351">Zie ook</span><span class="sxs-lookup"><span data-stu-id="dc8ba-351">See also</span></span>

[<span data-ttu-id="dc8ba-352">about_Automatic_Variables</span><span class="sxs-lookup"><span data-stu-id="dc8ba-352">about_Automatic_Variables</span></span>](about_Automatic_Variables.md)

[<span data-ttu-id="dc8ba-353">about_Functions</span><span class="sxs-lookup"><span data-stu-id="dc8ba-353">about_Functions</span></span>](about_Functions.md)

[<span data-ttu-id="dc8ba-354">about_Functions_Advanced</span><span class="sxs-lookup"><span data-stu-id="dc8ba-354">about_Functions_Advanced</span></span>](about_Functions_Advanced.md)

[<span data-ttu-id="dc8ba-355">about_Functions_Advanced_Methods</span><span class="sxs-lookup"><span data-stu-id="dc8ba-355">about_Functions_Advanced_Methods</span></span>](about_Functions_Advanced_Methods.md)

[<span data-ttu-id="dc8ba-356">about_Functions_CmdletBindingAttribute</span><span class="sxs-lookup"><span data-stu-id="dc8ba-356">about_Functions_CmdletBindingAttribute</span></span>](about_Functions_CmdletBindingAttribute.md)

[<span data-ttu-id="dc8ba-357">about_Functions_OutputTypeAttribute</span><span class="sxs-lookup"><span data-stu-id="dc8ba-357">about_Functions_OutputTypeAttribute</span></span>](about_Functions_OutputTypeAttribute.md)
