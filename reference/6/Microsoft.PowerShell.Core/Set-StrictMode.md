---
external help file: System.Management.Automation.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 04/09/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/set-strictmode?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Set-StrictMode
ms.openlocfilehash: f1cb30b34dcb86049c7818a2f8dd9b789f686cd9
ms.sourcegitcommit: 2c311274ce721cd1072dcf2dc077226789e21868
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 11/10/2020
ms.locfileid: "94387240"
---
# <span data-ttu-id="55fac-103">Set-StrictMode</span><span class="sxs-lookup"><span data-stu-id="55fac-103">Set-StrictMode</span></span>

## <span data-ttu-id="55fac-104">SAMENVATTING</span><span class="sxs-lookup"><span data-stu-id="55fac-104">SYNOPSIS</span></span>
<span data-ttu-id="55fac-105">Hiermee worden code regels in expressies, scripts en script blokken vastgelegd en afgedwongen.</span><span class="sxs-lookup"><span data-stu-id="55fac-105">Establishes and enforces coding rules in expressions, scripts, and script blocks.</span></span>

## <span data-ttu-id="55fac-106">SYNTAXIS</span><span class="sxs-lookup"><span data-stu-id="55fac-106">SYNTAX</span></span>

### <span data-ttu-id="55fac-107">Versie (standaard)</span><span class="sxs-lookup"><span data-stu-id="55fac-107">Version (Default)</span></span>

```
Set-StrictMode -Version <Version> [<CommonParameters>]
```

### <span data-ttu-id="55fac-108">Aan</span><span class="sxs-lookup"><span data-stu-id="55fac-108">Off</span></span>

```
Set-StrictMode [-Off] [<CommonParameters>]
```

## <span data-ttu-id="55fac-109">BESCHRIJVING</span><span class="sxs-lookup"><span data-stu-id="55fac-109">DESCRIPTION</span></span>

<span data-ttu-id="55fac-110">`Set-StrictMode`Met de cmdlet configureert u de strikte modus voor het huidige bereik en alle onderliggende bereiken, en schakelt u deze in en uit.</span><span class="sxs-lookup"><span data-stu-id="55fac-110">The `Set-StrictMode` cmdlet configures strict mode for the current scope and all child scopes, and turns it on and off.</span></span> <span data-ttu-id="55fac-111">Als de strikte modus is ingeschakeld, genereert Power shell een afsluit fout wanneer de inhoud van een expressie, script of script blok in strijd is met de basis regels voor Best Practice-code ring.</span><span class="sxs-lookup"><span data-stu-id="55fac-111">When strict mode is on, PowerShell generates a terminating error when the content of an expression, script, or script block violates basic best-practice coding rules.</span></span>

<span data-ttu-id="55fac-112">Gebruik de **versie** parameter om te bepalen welke code regels worden afgedwongen.</span><span class="sxs-lookup"><span data-stu-id="55fac-112">Use the **Version** parameter to determine which coding rules are enforced.</span></span>

<span data-ttu-id="55fac-113">`Set-PSDebug -Strict` met cmdlet schakelt u de strikte modus in voor het globale bereik.</span><span class="sxs-lookup"><span data-stu-id="55fac-113">`Set-PSDebug -Strict` cmdlet turns on strict mode for the global scope.</span></span> <span data-ttu-id="55fac-114">`Set-StrictMode` alleen van invloed op het huidige bereik en de onderliggende bereiken.</span><span class="sxs-lookup"><span data-stu-id="55fac-114">`Set-StrictMode` affects only the current scope and its child scopes.</span></span> <span data-ttu-id="55fac-115">Daarom kunt u deze in een script of functie gebruiken om de instelling te overschrijven die is overgenomen van het globale bereik.</span><span class="sxs-lookup"><span data-stu-id="55fac-115">Therefore, you can use it in a script or function to override the setting inherited from the global scope.</span></span>

<span data-ttu-id="55fac-116">Als `Set-StrictMode` is uitgeschakeld, heeft Power shell het volgende gedrag:</span><span class="sxs-lookup"><span data-stu-id="55fac-116">When `Set-StrictMode` is off, PowerShell has the following behaviors:</span></span>

- <span data-ttu-id="55fac-117">Bij niet-geïnitialiseerde variabelen wordt ervan uitgegaan dat de waarde 0 (nul) of `$Null` , afhankelijk van het type</span><span class="sxs-lookup"><span data-stu-id="55fac-117">Uninitialized variables are assumed to have a value of 0 (zero) or `$Null`, depending on type</span></span>
- <span data-ttu-id="55fac-118">Verwijzingen naar niet-bestaande eigenschappen retour neren `$Null`</span><span class="sxs-lookup"><span data-stu-id="55fac-118">References to non-existent properties return `$Null`</span></span>
- <span data-ttu-id="55fac-119">De resultaten van een onjuiste functie syntaxis zijn afhankelijk van de fout voorwaarden</span><span class="sxs-lookup"><span data-stu-id="55fac-119">Results of improper function syntax vary with the error conditions</span></span>
- <span data-ttu-id="55fac-120">Er wordt geprobeerd een waarde op te halen met een ongeldige index in een matrix `$Null`</span><span class="sxs-lookup"><span data-stu-id="55fac-120">Attempting to retrieve a value using an invalid index in an array returns `$Null`</span></span>

## <span data-ttu-id="55fac-121">VOORBEELDEN</span><span class="sxs-lookup"><span data-stu-id="55fac-121">EXAMPLES</span></span>

### <span data-ttu-id="55fac-122">Voor beeld 1: de strikte modus inschakelen als versie 1,0</span><span class="sxs-lookup"><span data-stu-id="55fac-122">Example 1: Turn on strict mode as version 1.0</span></span>

```powershell
# Strict mode is off by default.
$a -gt 5
```

```Output
False
```

```powershell
Set-StrictMode -Version 1.0
$a -gt 5
```

```Output
The variable $a cannot be retrieved because it has not been set yet.

At line:1 char:3
+ $a <<<<  -gt 5
+ CategoryInfo          : InvalidOperation: (a:Token) [], RuntimeException
+ FullyQualifiedErrorId : VariableIsUndefined
```

<span data-ttu-id="55fac-123">Wanneer de strikte modus is ingesteld op versie 1,0, wordt geprobeerd te verwijzen naar variabelen die niet zijn geïnitialiseerd.</span><span class="sxs-lookup"><span data-stu-id="55fac-123">With strict mode set to version 1.0, attempts to reference variables that are not initialized fail.</span></span>

### <span data-ttu-id="55fac-124">Voor beeld 2: de strikte modus inschakelen als versie 2,0</span><span class="sxs-lookup"><span data-stu-id="55fac-124">Example 2: Turn on strict mode as version 2.0</span></span>

```powershell
# Strict mode is off by default.
function add ($a, $b) {
    '$a = ' + $a
    '$b = ' + $b
    '$a+$b = ' + ($a + $b)
}
add 3 4
```

```Output
$a = 3
$b = 4
$a+$b = 7
```

```powershell
add(3,4)
```

```Output
$a = 3 4
$b =
$a+$b = 3 4
```

```powershell
Set-StrictMode -Version 2.0
add(3,4)
```

```Output
The function or command was called like a method. Parameters should be separated by spaces,
as described in 'Get-Help about_Parameter.'
At line:1 char:4
+ add <<<< (3,4)
+ CategoryInfo          : InvalidOperation: (:) [], RuntimeException
+ FullyQualifiedErrorId : StrictModeFunctionCallWithParens
```

```powershell
Set-StrictMode -Off
$string = "This is a string."
$null -eq $string.Month
```

```Output
True
```

```powershell
Set-StrictMode -Version 2.0
$string = "This is a string."
$null -eq $string.Month
```

```Output
Property 'Month' cannot be found on this object; make sure it exists.
At line:1 char:9
+ $string. <<<< month
+ CategoryInfo          : InvalidOperation: (.:OperatorToken) [], RuntimeException
+ FullyQualifiedErrorId : PropertyNotFoundStrict
```

<span data-ttu-id="55fac-125">Met deze opdracht wordt de strikte modus ingeschakeld en wordt deze ingesteld op versie 2,0.</span><span class="sxs-lookup"><span data-stu-id="55fac-125">This command turns strict mode on and sets it to version 2.0.</span></span> <span data-ttu-id="55fac-126">Als gevolg hiervan retourneert Power shell een fout melding als u syntaxis van de methode gebruikt, waarbij gebruik wordt gemaakt van haakjes en komma's, voor een functie aanroep of verwijzing naar niet-geïnitialiseerde variabelen of niet-bestaande eigenschappen.</span><span class="sxs-lookup"><span data-stu-id="55fac-126">As a result, PowerShell returns an error if you use method syntax, which uses parentheses and commas, for a function call or reference uninitialized variables or non-existent properties.</span></span>

<span data-ttu-id="55fac-127">De voorbeeld uitvoer toont het effect van de strikte modus versie 2,0.</span><span class="sxs-lookup"><span data-stu-id="55fac-127">The sample output shows the effect of version 2.0 strict mode.</span></span>

<span data-ttu-id="55fac-128">Zonder versie 2,0 Strict-modus wordt de waarde ' (3, 4) ' geïnterpreteerd als één matrix object waaraan niets is toegevoegd.</span><span class="sxs-lookup"><span data-stu-id="55fac-128">Without version 2.0 strict mode, the "(3,4)" value is interpreted as a single array object to which nothing is added.</span></span> <span data-ttu-id="55fac-129">Door de strikte modus versie 2,0 te gebruiken, wordt deze juist geïnterpreteerd als een fout syntaxis voor het verzenden van twee waarden.</span><span class="sxs-lookup"><span data-stu-id="55fac-129">By using version 2.0 strict mode, it is correctly interpreted as faulty syntax for submitting two values.</span></span>

<span data-ttu-id="55fac-130">Zonder versie 2,0 wordt de verwijzing naar de niet-bestaande eigenschap **Month** van een teken reeks alleen geretourneerd `$Null` .</span><span class="sxs-lookup"><span data-stu-id="55fac-130">Without version 2.0, the reference to the non-existent **Month** property of a string returns only `$Null`.</span></span> <span data-ttu-id="55fac-131">Door versie 2,0 te gebruiken, wordt deze correct geïnterpreteerd als een verwijzings fout.</span><span class="sxs-lookup"><span data-stu-id="55fac-131">By using version 2.0, it is interpreted correctly as a reference error.</span></span>

### <span data-ttu-id="55fac-132">Voor beeld 3: de strikte modus inschakelen als versie 3,0</span><span class="sxs-lookup"><span data-stu-id="55fac-132">Example 3: Turn on strict mode as version 3.0</span></span>

<span data-ttu-id="55fac-133">Als de strikte modus is ingesteld op **uit** , is het resultaat van een ongeldige of buiten grenzende indexen Null-waarden.</span><span class="sxs-lookup"><span data-stu-id="55fac-133">With strict mode set to **Off** , invalid or out of bounds indexes result return null values.</span></span>

```powershell
# Strict mode is off by default.
$a = @(1)
$null -eq $a[2]
$null -eq $a['abc']
```

```Output
True
True
```

```powershell
Set-StrictMode -Version 3
$a = @(1)
$null -eq $a[2]
$null -eq $a['abc']
```

```Output
Index was outside the bounds of the array.
At line:1 char:1
+ $null -eq $a[2]
+ ~~~~~~~~~~~~~~~
    + CategoryInfo          : OperationStopped: (:) [], IndexOutOfRangeException
    + FullyQualifiedErrorId : System.IndexOutOfRangeException

Cannot convert value "abc" to type "System.Int32". Error: "Input string was not in a correct format."
At line:1 char:1
+ $null -eq $a['abc']
+ ~~~~~~~~~~~~~~~~~~~
    + CategoryInfo          : InvalidArgument: (:) [], RuntimeException
    + FullyQualifiedErrorId : InvalidCastFromStringToInteger
```

<span data-ttu-id="55fac-134">Als de strikte modus is ingesteld op versie 3 of hoger, zijn ongeldige of buiten grenzende indexen resulteren in fouten.</span><span class="sxs-lookup"><span data-stu-id="55fac-134">With strict mode set to version 3 or higher, invalid or out of bounds indexes result in errors.</span></span>

## <span data-ttu-id="55fac-135">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="55fac-135">PARAMETERS</span></span>

### <span data-ttu-id="55fac-136">-Uit</span><span class="sxs-lookup"><span data-stu-id="55fac-136">-Off</span></span>

<span data-ttu-id="55fac-137">Geeft aan dat met deze cmdlet de strikte modus voor het huidige bereik en voor alle onderliggende bereiken wordt uitgeschakeld.</span><span class="sxs-lookup"><span data-stu-id="55fac-137">Indicates that this cmdlet turns strict mode off for the current scope and all child scopes.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: Off
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="55fac-138">-Versie</span><span class="sxs-lookup"><span data-stu-id="55fac-138">-Version</span></span>

<span data-ttu-id="55fac-139">Hiermee geeft u de voor waarden op die een fout veroorzaken in de strikte modus.</span><span class="sxs-lookup"><span data-stu-id="55fac-139">Specifies the conditions that cause an error in strict mode.</span></span> <span data-ttu-id="55fac-140">Deze para meter accepteert een geldig Power shell-versie nummer.</span><span class="sxs-lookup"><span data-stu-id="55fac-140">This parameter accepts any valid PowerShell version number.</span></span> <span data-ttu-id="55fac-141">Een getal hoger dan 3 wordt als **laatste** beschouwd.</span><span class="sxs-lookup"><span data-stu-id="55fac-141">Any number higher than 3 is treated as **Latest**.</span></span>

<span data-ttu-id="55fac-142">De ingangs waarden voor deze para meter zijn:</span><span class="sxs-lookup"><span data-stu-id="55fac-142">The effective values for this parameter are:</span></span>

- <span data-ttu-id="55fac-143">1.0</span><span class="sxs-lookup"><span data-stu-id="55fac-143">1.0</span></span>
  - <span data-ttu-id="55fac-144">Verbiedt verwijzingen naar niet-geïnitialiseerde variabelen, met uitzonde ring van niet-geïnitialiseerde variabelen in teken reeksen.</span><span class="sxs-lookup"><span data-stu-id="55fac-144">Prohibits references to uninitialized variables, except for uninitialized variables in strings.</span></span>
- <span data-ttu-id="55fac-145">2,0</span><span class="sxs-lookup"><span data-stu-id="55fac-145">2.0</span></span>
  - <span data-ttu-id="55fac-146">Verbiedt verwijzingen naar niet-geïnitialiseerde variabelen.</span><span class="sxs-lookup"><span data-stu-id="55fac-146">Prohibits references to uninitialized variables.</span></span> <span data-ttu-id="55fac-147">Dit omvat niet-geïnitialiseerde variabelen in teken reeksen.</span><span class="sxs-lookup"><span data-stu-id="55fac-147">This includes uninitialized variables in strings.</span></span>
  - <span data-ttu-id="55fac-148">Verbiedt verwijzingen naar niet-bestaande eigenschappen van een object.</span><span class="sxs-lookup"><span data-stu-id="55fac-148">Prohibits references to non-existent properties of an object.</span></span>
  - <span data-ttu-id="55fac-149">Verbiedt functie aanroepen die gebruikmaken van de syntaxis voor het aanroepen van methoden.</span><span class="sxs-lookup"><span data-stu-id="55fac-149">Prohibits function calls that use the syntax for calling methods.</span></span>
- <span data-ttu-id="55fac-150">3,0</span><span class="sxs-lookup"><span data-stu-id="55fac-150">3.0</span></span>
  - <span data-ttu-id="55fac-151">Verbiedt verwijzingen naar niet-geïnitialiseerde variabelen.</span><span class="sxs-lookup"><span data-stu-id="55fac-151">Prohibits references to uninitialized variables.</span></span> <span data-ttu-id="55fac-152">Dit omvat niet-geïnitialiseerde variabelen in teken reeksen.</span><span class="sxs-lookup"><span data-stu-id="55fac-152">This includes uninitialized variables in strings.</span></span>
  - <span data-ttu-id="55fac-153">Verbiedt verwijzingen naar niet-bestaande eigenschappen van een object.</span><span class="sxs-lookup"><span data-stu-id="55fac-153">Prohibits references to non-existent properties of an object.</span></span>
  - <span data-ttu-id="55fac-154">Verbiedt functie aanroepen die gebruikmaken van de syntaxis voor het aanroepen van methoden.</span><span class="sxs-lookup"><span data-stu-id="55fac-154">Prohibits function calls that use the syntax for calling methods.</span></span>
  - <span data-ttu-id="55fac-155">Geen grenzen of onherleidbare matrix indexen.</span><span class="sxs-lookup"><span data-stu-id="55fac-155">Prohibit out of bounds or unresolvable array indexes.</span></span>
- <span data-ttu-id="55fac-156">Laatste</span><span class="sxs-lookup"><span data-stu-id="55fac-156">Latest</span></span>
  - <span data-ttu-id="55fac-157">Hiermee selecteert u de meest recente versie die beschikbaar is.</span><span class="sxs-lookup"><span data-stu-id="55fac-157">Selects the latest version available.</span></span> <span data-ttu-id="55fac-158">De meest recente versie is de meest strikte.</span><span class="sxs-lookup"><span data-stu-id="55fac-158">The latest version is the most strict.</span></span> <span data-ttu-id="55fac-159">Gebruik deze waarde om ervoor te zorgen dat scripts de striktst beschik bare versie gebruiken, zelfs wanneer er nieuwe versies worden toegevoegd aan Power shell.</span><span class="sxs-lookup"><span data-stu-id="55fac-159">Use this value to make sure that scripts use the strictest available version, even when new versions are added to PowerShell.</span></span>

> [!CAUTION]
> <span data-ttu-id="55fac-160">Het gebruik van een **nieuwste** **versie** in scripts.</span><span class="sxs-lookup"><span data-stu-id="55fac-160">Using a **Version** of **Latest** in scripts.</span></span> <span data-ttu-id="55fac-161">De betekenis van de **laatste** wijziging kan worden gewijzigd in nieuwe releases van Power shell.</span><span class="sxs-lookup"><span data-stu-id="55fac-161">The meaning of **Latest** can change in new releases of PowerShell.</span></span> <span data-ttu-id="55fac-162">Daarom is voor een script dat is geschreven voor een oudere versie van Power shell die wordt gebruikt, `Set-StrictMode -Version Latest` onderhevig aan meer beperkende regels wanneer ze in een nieuwere versie van Power shell worden uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="55fac-162">Therefore, a script written for an older version of PowerShell that uses `Set-StrictMode -Version Latest` is subject to more restrictive rules when run in a newer version of PowerShell.</span></span>

```yaml
Type: System.Version
Parameter Sets: Version
Aliases: v

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="55fac-163">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="55fac-163">CommonParameters</span></span>

<span data-ttu-id="55fac-164">Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="55fac-164">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="55fac-165">Zie [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="55fac-165">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="55fac-166">INVOER</span><span class="sxs-lookup"><span data-stu-id="55fac-166">INPUTS</span></span>

### <span data-ttu-id="55fac-167">Geen</span><span class="sxs-lookup"><span data-stu-id="55fac-167">None</span></span>

<span data-ttu-id="55fac-168">U kunt geen invoer van een pipe naar deze cmdlet.</span><span class="sxs-lookup"><span data-stu-id="55fac-168">You cannot pipe input to this cmdlet.</span></span>

## <span data-ttu-id="55fac-169">UITVOER</span><span class="sxs-lookup"><span data-stu-id="55fac-169">OUTPUTS</span></span>

### <span data-ttu-id="55fac-170">Geen</span><span class="sxs-lookup"><span data-stu-id="55fac-170">None</span></span>

<span data-ttu-id="55fac-171">Met deze cmdlet wordt geen uitvoer geretourneerd.</span><span class="sxs-lookup"><span data-stu-id="55fac-171">This cmdlet does not return any output.</span></span>

## <span data-ttu-id="55fac-172">OPMERKINGEN</span><span class="sxs-lookup"><span data-stu-id="55fac-172">NOTES</span></span>

<span data-ttu-id="55fac-173">`Set-StrictMode` is alleen effectief in het bereik waarin het is ingesteld en in het onderliggende bereik.</span><span class="sxs-lookup"><span data-stu-id="55fac-173">`Set-StrictMode` is effective only in the scope in which it is set and in its child scopes.</span></span> <span data-ttu-id="55fac-174">Zie [about_Scopes](about/about_Scopes.md)voor meer informatie over bereiken in Power shell.</span><span class="sxs-lookup"><span data-stu-id="55fac-174">For more information about scopes in PowerShell, see [about_Scopes](about/about_Scopes.md).</span></span>

## <span data-ttu-id="55fac-175">GERELATEERDE KOPPELINGEN</span><span class="sxs-lookup"><span data-stu-id="55fac-175">RELATED LINKS</span></span>

[<span data-ttu-id="55fac-176">Set-PSDebug</span><span class="sxs-lookup"><span data-stu-id="55fac-176">Set-PSDebug</span></span>](Set-PSDebug.md)
