---
external help file: System.Management.Automation.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 04/08/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/new-module?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: New-Module
ms.openlocfilehash: 487fd85bdcc918b7fb360f9c9d23388a06b35f86
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 11/17/2020
ms.locfileid: "94706065"
---
# <span data-ttu-id="eb07e-102">New-Module</span><span class="sxs-lookup"><span data-stu-id="eb07e-102">New-Module</span></span>

## <span data-ttu-id="eb07e-103">SAMENVATTING</span><span class="sxs-lookup"><span data-stu-id="eb07e-103">SYNOPSIS</span></span>
<span data-ttu-id="eb07e-104">Hiermee maakt u een nieuwe dynamische module die alleen in het geheugen bestaat.</span><span class="sxs-lookup"><span data-stu-id="eb07e-104">Creates a new dynamic module that exists only in memory.</span></span>

## <span data-ttu-id="eb07e-105">SYNTAXIS</span><span class="sxs-lookup"><span data-stu-id="eb07e-105">SYNTAX</span></span>

### <span data-ttu-id="eb07e-106">Script Block (standaard)</span><span class="sxs-lookup"><span data-stu-id="eb07e-106">ScriptBlock (Default)</span></span>

```
New-Module [-ScriptBlock] <ScriptBlock> [-Function <String[]>] [-Cmdlet <String[]>] [-ReturnResult]
 [-AsCustomObject] [-ArgumentList <Object[]>] [<CommonParameters>]
```

### <span data-ttu-id="eb07e-107">Name</span><span class="sxs-lookup"><span data-stu-id="eb07e-107">Name</span></span>

```
New-Module [-Name] <String> [-ScriptBlock] <ScriptBlock> [-Function <String[]>] [-Cmdlet <String[]>]
 [-ReturnResult] [-AsCustomObject] [-ArgumentList <Object[]>] [<CommonParameters>]
```

## <span data-ttu-id="eb07e-108">BESCHRIJVING</span><span class="sxs-lookup"><span data-stu-id="eb07e-108">DESCRIPTION</span></span>

<span data-ttu-id="eb07e-109">`New-Module`Met de cmdlet wordt een dynamische module gemaakt op basis van een script blok.</span><span class="sxs-lookup"><span data-stu-id="eb07e-109">The `New-Module` cmdlet creates a dynamic module from a script block.</span></span> <span data-ttu-id="eb07e-110">De leden van de dynamische module, zoals functies en variabelen, zijn onmiddellijk beschikbaar in de sessie en blijven beschikbaar totdat u de sessie sluit.</span><span class="sxs-lookup"><span data-stu-id="eb07e-110">The members of the dynamic module, such as functions and variables, are immediately available in the session and remain available until you close the session.</span></span>

<span data-ttu-id="eb07e-111">Net als statische modules worden standaard de cmdlets en functies in een dynamische module geëxporteerd en de variabelen en aliassen niet.</span><span class="sxs-lookup"><span data-stu-id="eb07e-111">Like static modules, by default, the cmdlets and functions in a dynamic module are exported and the variables and aliases are not.</span></span> <span data-ttu-id="eb07e-112">U kunt echter de Export-ModuleMember-cmdlet en de para meters van gebruiken `New-Module` om de standaard instellingen te overschrijven.</span><span class="sxs-lookup"><span data-stu-id="eb07e-112">However, you can use the Export-ModuleMember cmdlet and the parameters of `New-Module` to override the defaults.</span></span>

<span data-ttu-id="eb07e-113">U kunt ook de para meter **AsCustomObject** van gebruiken `New-Module` om de dynamische module als een aangepast object te retour neren.</span><span class="sxs-lookup"><span data-stu-id="eb07e-113">You can also use the **AsCustomObject** parameter of `New-Module` to return the dynamic module as a custom object.</span></span> <span data-ttu-id="eb07e-114">De leden van de modules, zoals functions, worden geïmplementeerd als script methoden van het aangepaste object in plaats van in de sessie te worden geïmporteerd.</span><span class="sxs-lookup"><span data-stu-id="eb07e-114">The members of the modules, such as functions, are implemented as script methods of the custom object instead of being imported into the session.</span></span>

<span data-ttu-id="eb07e-115">Dynamische modules bestaan alleen in het geheugen, niet op schijf.</span><span class="sxs-lookup"><span data-stu-id="eb07e-115">Dynamic modules exist only in memory, not on disk.</span></span> <span data-ttu-id="eb07e-116">Net als alle modules worden de leden van dynamische modules uitgevoerd in een persoonlijk module bereik dat een onderliggend element is van het globale bereik.</span><span class="sxs-lookup"><span data-stu-id="eb07e-116">Like all modules, the members of dynamic modules run in a private module scope that is a child of the global scope.</span></span> <span data-ttu-id="eb07e-117">Get-Module kan geen dynamische module ophalen, maar Get-Command kan de geëxporteerde leden ophalen.</span><span class="sxs-lookup"><span data-stu-id="eb07e-117">Get-Module cannot get a dynamic module, but Get-Command can get the exported members.</span></span>

<span data-ttu-id="eb07e-118">Als u een dynamische module beschikbaar wilt maken voor `Get-Module` , pipet u een `New-Module` opdracht naar import-module of pipet u het module-object dat `New-Module` retourneert naar `Import-Module` .</span><span class="sxs-lookup"><span data-stu-id="eb07e-118">To make a dynamic module available to `Get-Module`, pipe a `New-Module` command to Import-Module, or pipe the module object that `New-Module` returns to `Import-Module`.</span></span> <span data-ttu-id="eb07e-119">Met deze actie wordt de dynamische module aan de `Get-Module` lijst toegevoegd, maar wordt de module niet op schijf opgeslagen of kan deze permanent worden gemaakt.</span><span class="sxs-lookup"><span data-stu-id="eb07e-119">This action adds the dynamic module to the `Get-Module` list, but it does not save the module to disk or make it persistent.</span></span>

## <span data-ttu-id="eb07e-120">VOORBEELDEN</span><span class="sxs-lookup"><span data-stu-id="eb07e-120">EXAMPLES</span></span>

### <span data-ttu-id="eb07e-121">Voor beeld 1: een dynamische module maken</span><span class="sxs-lookup"><span data-stu-id="eb07e-121">Example 1: Create a dynamic module</span></span>

<span data-ttu-id="eb07e-122">In dit voor beeld wordt een nieuwe dynamische module gemaakt met een functie met de naam `Hello` .</span><span class="sxs-lookup"><span data-stu-id="eb07e-122">This example creates a new dynamic module with a function called `Hello`.</span></span> <span data-ttu-id="eb07e-123">De opdracht retourneert een module-object dat de nieuwe dynamische module vertegenwoordigt.</span><span class="sxs-lookup"><span data-stu-id="eb07e-123">The command returns a module object that represents the new dynamic module.</span></span>

```powershell
New-Module -ScriptBlock {function Hello {"Hello!"}}
```

```Output
Name              : __DynamicModule_2ceb1d0a-990f-45e4-9fe4-89f0f6ead0e5
Path              : 2ceb1d0a-990f-45e4-9fe4-89f0f6ead0e5
Description       :
Guid              : 00000000-0000-0000-0000-000000000000
Version           : 0.0
ModuleBase        :
ModuleType        : Script
PrivateData       :
AccessMode        : ReadWrite
ExportedAliases   : {}
ExportedCmdlets   : {}
ExportedFunctions : {[Hello, Hello]}
ExportedVariables : {}
NestedModules     : {}
```

### <span data-ttu-id="eb07e-124">Voor beeld 2: werken met dynamische modules en Get-Module en Get-Command</span><span class="sxs-lookup"><span data-stu-id="eb07e-124">Example 2: Working with dynamic modules and Get-Module and Get-Command</span></span>

<span data-ttu-id="eb07e-125">In dit voor beeld wordt gedemonstreerd dat dynamische modules niet worden geretourneerd door de `Get-Module` cmdlet.</span><span class="sxs-lookup"><span data-stu-id="eb07e-125">This example demonstrates that dynamic modules are not returned by the `Get-Module` cmdlet.</span></span> <span data-ttu-id="eb07e-126">De leden die ze exporteren, worden geretourneerd door de `Get-Command` cmdlet.</span><span class="sxs-lookup"><span data-stu-id="eb07e-126">The members that they export are returned by the `Get-Command` cmdlet.</span></span>

```powershell
new-module -scriptblock {function Hello {"Hello!"}}
```

```Output
Name              : __DynamicModule_2ceb1d0a-990f-45e4-9fe4-89f0f6ead0e5
Path              : 2ceb1d0a-990f-45e4-9fe4-89f0f6ead0e5
Description       :
Guid              : 00000000-0000-0000-0000-000000000000
Version           : 0.0
ModuleBase        :
ModuleType        : Script
PrivateData       :
AccessMode        : ReadWrite
ExportedAliases   : {}
ExportedCmdlets   : {}
ExportedFunctions : {[Hello, Hello]}
ExportedVariables : {}
NestedModules     : {}
```

```powershell
Get-Module

Get-Command Hello
```

```Output
CommandType     Name   Definition
-----------     ----   ----------
Function        Hello  "Hello!"
```

### <span data-ttu-id="eb07e-127">Voor beeld 3: een variabele exporteren naar de huidige sessie</span><span class="sxs-lookup"><span data-stu-id="eb07e-127">Example 3: Export a variable into the current session</span></span>

<span data-ttu-id="eb07e-128">In dit voor beeld wordt de `Export-ModuleMember` cmdlet gebruikt om een variabele te exporteren naar de huidige sessie.</span><span class="sxs-lookup"><span data-stu-id="eb07e-128">This example uses the `Export-ModuleMember` cmdlet to export a variable into the current session.</span></span>
<span data-ttu-id="eb07e-129">Zonder de `Export-ModuleMember` opdracht wordt alleen de functie geëxporteerd.</span><span class="sxs-lookup"><span data-stu-id="eb07e-129">Without the `Export-ModuleMember` command, only the function is exported.</span></span>

```powershell
New-Module -ScriptBlock {$SayHelloHelp="Type 'SayHello', a space, and a name."; function SayHello ($name) { "Hello, $name" }; Export-ModuleMember -function SayHello -Variable SayHelloHelp}
$SayHelloHelp
```

```Output
Type 'SayHello', a space, and a name.
```

```powershell
SayHello Jeffrey
```

```Output
Hello, Jeffrey
```

<span data-ttu-id="eb07e-130">In de uitvoer ziet u dat zowel de variabele als de functie zijn geëxporteerd naar de sessie.</span><span class="sxs-lookup"><span data-stu-id="eb07e-130">The output shows that both the variable and the function were exported into the session.</span></span>

### <span data-ttu-id="eb07e-131">Voor beeld 4: een dynamische module beschikbaar maken voor Get-Module</span><span class="sxs-lookup"><span data-stu-id="eb07e-131">Example 4: Make a dynamic module available to Get-Module</span></span>

<span data-ttu-id="eb07e-132">In dit voor beeld wordt gedemonstreerd dat u een dynamische module beschikbaar kunt maken voor `Get-Module` door de dynamische module te pijpleidingen naar `Import-Module` .</span><span class="sxs-lookup"><span data-stu-id="eb07e-132">This example demonstrates that you can make a dynamic module available to `Get-Module` by piping the dynamic module to `Import-Module`.</span></span>

<span data-ttu-id="eb07e-133">`New-Module` Hiermee maakt u een module object dat is gesluisd met de `Import-Module` cmdlet.</span><span class="sxs-lookup"><span data-stu-id="eb07e-133">`New-Module` creates a module object that is piped to the `Import-Module` cmdlet.</span></span> <span data-ttu-id="eb07e-134">De para meter **name** van `New-Module` wijst een beschrijvende naam toe aan de module.</span><span class="sxs-lookup"><span data-stu-id="eb07e-134">The **Name** parameter of `New-Module` assigns a friendly name to the module.</span></span> <span data-ttu-id="eb07e-135">Omdat `Import-Module` er geen objecten worden geretourneerd, is er geen uitvoer van deze opdracht.</span><span class="sxs-lookup"><span data-stu-id="eb07e-135">Because `Import-Module` does not return any objects by default, there is no output from this command.</span></span> <span data-ttu-id="eb07e-136">`Get-Module` of de **GreetingModule** is geïmporteerd in de huidige sessie.</span><span class="sxs-lookup"><span data-stu-id="eb07e-136">`Get-Module` that the **GreetingModule** has been imported into the current session.</span></span>

```powershell
New-Module -ScriptBlock {function Hello {"Hello!"}} -name GreetingModule | Import-Module
Get-Module
```

```Output
Name              : GreetingModule
Path              : d54dfdac-4531-4db2-9dec-0b4b9c57a1e5
Description       :
Guid              : 00000000-0000-0000-0000-000000000000
Version           : 0.0
ModuleBase        :
ModuleType        : Script
PrivateData       :
AccessMode        : ReadWrite
ExportedAliases   : {}
ExportedCmdlets   : {}
ExportedFunctions : {[Hello, Hello]}
ExportedVariables : {}
NestedModules     : {}
```

```powershell
Get-Command hello
```

```Output
CommandType     Name                                                               Definition
-----------     ----                                                               ----------
Function        Hello                                                              "Hello!"
```

<span data-ttu-id="eb07e-137">De `Get-Command` cmdlet toont de `Hello` functie die de dynamische module exporteert.</span><span class="sxs-lookup"><span data-stu-id="eb07e-137">The `Get-Command` cmdlet shows the `Hello` function that the dynamic module exports.</span></span>

### <span data-ttu-id="eb07e-138">Voor beeld 5: een aangepast object met geëxporteerde functies genereren</span><span class="sxs-lookup"><span data-stu-id="eb07e-138">Example 5: Generate a custom object that has exported functions</span></span>

<span data-ttu-id="eb07e-139">In dit voor beeld ziet u hoe u de para meter **AsCustomObject** van gebruikt `New-Module` om een aangepast object te genereren dat script methoden heeft die de geëxporteerde functies vertegenwoordigen.</span><span class="sxs-lookup"><span data-stu-id="eb07e-139">This example shows how to use the **AsCustomObject** parameter of `New-Module` to generate a custom object that has script methods that represent the exported functions.</span></span>

<span data-ttu-id="eb07e-140">De `New-Module` cmdlet maakt een dynamische module met twee functies, `Hello` en `Goodbye` .</span><span class="sxs-lookup"><span data-stu-id="eb07e-140">The `New-Module` cmdlet creates a dynamic module with two functions, `Hello` and `Goodbye`.</span></span> <span data-ttu-id="eb07e-141">Met de para meter **AsCustomObject** maakt u een aangepast object in plaats van het **PSModuleInfo** -object dat `New-Module` Standaard wordt gegenereerd.</span><span class="sxs-lookup"><span data-stu-id="eb07e-141">The **AsCustomObject** parameter creates a custom object instead of the **PSModuleInfo** object that `New-Module` generates by default.</span></span> <span data-ttu-id="eb07e-142">Dit aangepaste object wordt opgeslagen in de `$m` variabele.</span><span class="sxs-lookup"><span data-stu-id="eb07e-142">This custom object is saved in the `$m` variable.</span></span>
<span data-ttu-id="eb07e-143">De `$m` variabele lijkt geen waarde toegewezen te hebben.</span><span class="sxs-lookup"><span data-stu-id="eb07e-143">The `$m` variable appears to have no assigned value.</span></span>

```powershell
$m = New-Module -ScriptBlock {
  function Hello ($name) {"Hello, $name"}
  function Goodbye ($name) {"Goodbye, $name"}
} -AsCustomObject
$m
$m | Get-Member
```

```Output
TypeName: System.Management.Automation.PSCustomObject

Name        MemberType   Definition
----        ----------   ----------
Equals      Method       bool Equals(System.Object obj)
GetHashCode Method       int GetHashCode()
GetType     Method       type GetType()
ToString    Method       string ToString()
Goodbye     ScriptMethod System.Object Goodbye();
Hello       ScriptMethod System.Object Hello();
```

```powershell
$m.goodbye("Jane")
```

```Output
Goodbye, Jane
```

```powershell
$m.hello("Manoj")
```

```Output
Hello, Manoj
```

<span data-ttu-id="eb07e-144">De `$m` `Get-Member` Eigenschappen en methoden van het aangepaste object worden weer gegeven in sluizen naar de cmdlet.</span><span class="sxs-lookup"><span data-stu-id="eb07e-144">Piping `$m` to the `Get-Member` cmdlet displays the properties and methods of the custom object.</span></span> <span data-ttu-id="eb07e-145">In de uitvoer ziet u dat het object script methoden heeft die `Hello` de `Goodbye` functies en vertegenwoordigen.</span><span class="sxs-lookup"><span data-stu-id="eb07e-145">The output shows that the object has script methods that represent the `Hello` and `Goodbye` functions.</span></span>
<span data-ttu-id="eb07e-146">Ten slotte noemen we deze script methoden en worden de resultaten weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="eb07e-146">Finally, we call these script methods and display the results.</span></span>

### <span data-ttu-id="eb07e-147">Voor beeld 6: de resultaten van het script blok ophalen</span><span class="sxs-lookup"><span data-stu-id="eb07e-147">Example 6: Get the results of the script block</span></span>

<span data-ttu-id="eb07e-148">In dit voor beeld wordt de para meter **ReturnResult** gebruikt om de resultaten van het uitvoeren van het script blok op te vragen in plaats van een module object aan te vragen.</span><span class="sxs-lookup"><span data-stu-id="eb07e-148">This example uses the **ReturnResult** parameter to request the results of running the script block instead of requesting a module object.</span></span> <span data-ttu-id="eb07e-149">Het script blok in de nieuwe module definieert de `SayHello` functie en roept vervolgens de functie aan.</span><span class="sxs-lookup"><span data-stu-id="eb07e-149">The script block in the new module defines the `SayHello` function and then calls the function.</span></span>

```powershell
New-Module -ScriptBlock {function SayHello {"Hello, World!"}; SayHello} -ReturnResult
```

```Output
Hello, World!
```

## <span data-ttu-id="eb07e-150">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="eb07e-150">PARAMETERS</span></span>

### <span data-ttu-id="eb07e-151">-Argument List</span><span class="sxs-lookup"><span data-stu-id="eb07e-151">-ArgumentList</span></span>

<span data-ttu-id="eb07e-152">Hiermee wordt een matrix met argumenten opgegeven die parameter waarden zijn die worden door gegeven aan het script blok.</span><span class="sxs-lookup"><span data-stu-id="eb07e-152">Specifies an array of arguments which are parameter values that are passed to the script block.</span></span> <span data-ttu-id="eb07e-153">Zie [about_Splatting](about/about_Splatting.md#splatting-with-arrays)voor meer informatie over het gedrag van **argument List**.</span><span class="sxs-lookup"><span data-stu-id="eb07e-153">For more information about the behavior of **ArgumentList**, see [about_Splatting](about/about_Splatting.md#splatting-with-arrays).</span></span>

```yaml
Type: System.Object[]
Parameter Sets: (All)
Aliases: Args

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="eb07e-154">-AsCustomObject</span><span class="sxs-lookup"><span data-stu-id="eb07e-154">-AsCustomObject</span></span>

<span data-ttu-id="eb07e-155">Geeft aan dat deze cmdlet een aangepast object retourneert dat de dynamische module vertegenwoordigt.</span><span class="sxs-lookup"><span data-stu-id="eb07e-155">Indicates that this cmdlet returns a custom object that represents the dynamic module.</span></span> <span data-ttu-id="eb07e-156">De module leden worden geïmplementeerd als script methoden van het aangepaste object, maar ze worden niet in de sessie geïmporteerd.</span><span class="sxs-lookup"><span data-stu-id="eb07e-156">The module members are implemented as script methods of the custom object, but they are not imported into the session.</span></span> <span data-ttu-id="eb07e-157">U kunt het aangepaste object opslaan in een variabele en de punt notatie gebruiken om de leden aan te roepen.</span><span class="sxs-lookup"><span data-stu-id="eb07e-157">You can save the custom object in a variable and use dot notation to invoke the members.</span></span>

<span data-ttu-id="eb07e-158">Als de module meerdere leden met dezelfde naam heeft, zoals een functie en een variabele die beide de naam A hebben, kan slechts één lid met elke naam worden geopend vanuit het aangepaste object.</span><span class="sxs-lookup"><span data-stu-id="eb07e-158">If the module has multiple members with the same name, such as a function and a variable that are both named A, only one member with each name can be accessed from the custom object.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="eb07e-159">-Cmdlet</span><span class="sxs-lookup"><span data-stu-id="eb07e-159">-Cmdlet</span></span>

<span data-ttu-id="eb07e-160">Hiermee geeft u een matrix met cmdlets op die met deze cmdlet wordt geëxporteerd van de module naar de huidige sessie.</span><span class="sxs-lookup"><span data-stu-id="eb07e-160">Specifies an array of cmdlets that this cmdlet exports from the module into the current session.</span></span>
<span data-ttu-id="eb07e-161">Voer een door komma's gescheiden lijst met cmdlets in.</span><span class="sxs-lookup"><span data-stu-id="eb07e-161">Enter a comma-separated list of cmdlets.</span></span> <span data-ttu-id="eb07e-162">Joker tekens zijn toegestaan.</span><span class="sxs-lookup"><span data-stu-id="eb07e-162">Wildcard characters are permitted.</span></span> <span data-ttu-id="eb07e-163">Standaard worden alle cmdlets in de module geëxporteerd.</span><span class="sxs-lookup"><span data-stu-id="eb07e-163">By default, all cmdlets in the module are exported.</span></span>

<span data-ttu-id="eb07e-164">U kunt geen cmdlets definiëren in een script blok, maar een dynamische module kan cmdlets bevatten als de cmdlets uit een binaire module worden geïmporteerd.</span><span class="sxs-lookup"><span data-stu-id="eb07e-164">You cannot define cmdlets in a script block, but a dynamic module can include cmdlets if it imports the cmdlets from a binary module.</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="eb07e-165">-Functie</span><span class="sxs-lookup"><span data-stu-id="eb07e-165">-Function</span></span>

<span data-ttu-id="eb07e-166">Hiermee geeft u een matrix op met functies die met deze cmdlet worden geëxporteerd van de module naar de huidige sessie.</span><span class="sxs-lookup"><span data-stu-id="eb07e-166">Specifies an array of functions that this cmdlet exports from the module into the current session.</span></span>
<span data-ttu-id="eb07e-167">Voer een door komma's gescheiden lijst met functies in.</span><span class="sxs-lookup"><span data-stu-id="eb07e-167">Enter a comma-separated list of functions.</span></span> <span data-ttu-id="eb07e-168">Joker tekens zijn toegestaan.</span><span class="sxs-lookup"><span data-stu-id="eb07e-168">Wildcard characters are permitted.</span></span> <span data-ttu-id="eb07e-169">Standaard worden alle functies die in een module zijn gedefinieerd, geëxporteerd.</span><span class="sxs-lookup"><span data-stu-id="eb07e-169">By default, all functions defined in a module are exported.</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: True
```

### <span data-ttu-id="eb07e-170">-Name</span><span class="sxs-lookup"><span data-stu-id="eb07e-170">-Name</span></span>

<span data-ttu-id="eb07e-171">Hiermee geeft u een naam op voor de nieuwe module.</span><span class="sxs-lookup"><span data-stu-id="eb07e-171">Specifies a name for the new module.</span></span> <span data-ttu-id="eb07e-172">U kunt ook een module naam naar een nieuwe module pipeen.</span><span class="sxs-lookup"><span data-stu-id="eb07e-172">You can also pipe a module name to New-Module.</span></span>

<span data-ttu-id="eb07e-173">De standaard waarde is een automatisch gegenereerde naam die begint met `__DynamicModule_` en wordt gevolgd door een GUID die het pad van de dynamische module opgeeft.</span><span class="sxs-lookup"><span data-stu-id="eb07e-173">The default value is an autogenerated name that starts with `__DynamicModule_` and is followed by a GUID that specifies the path of the dynamic module.</span></span>

```yaml
Type: System.String
Parameter Sets: Name
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="eb07e-174">-ReturnResult</span><span class="sxs-lookup"><span data-stu-id="eb07e-174">-ReturnResult</span></span>

<span data-ttu-id="eb07e-175">Geeft aan dat met deze cmdlet het script blok wordt uitgevoerd en de resultaten van het script blok worden geretourneerd in plaats van een module object te retour neren.</span><span class="sxs-lookup"><span data-stu-id="eb07e-175">Indicates that this cmdlet runs the script block and returns the script block results instead of returning a module object.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="eb07e-176">-Script Block</span><span class="sxs-lookup"><span data-stu-id="eb07e-176">-ScriptBlock</span></span>

<span data-ttu-id="eb07e-177">Hiermee geeft u de inhoud van de dynamische module op.</span><span class="sxs-lookup"><span data-stu-id="eb07e-177">Specifies the contents of the dynamic module.</span></span> <span data-ttu-id="eb07e-178">Plaats de inhoud tussen accolades ( `{}` ) om een script blok te maken.</span><span class="sxs-lookup"><span data-stu-id="eb07e-178">Enclose the contents in braces (`{}`) to create a script block.</span></span> <span data-ttu-id="eb07e-179">Deze parameter is vereist.</span><span class="sxs-lookup"><span data-stu-id="eb07e-179">This parameter is required.</span></span>

```yaml
Type: System.Management.Automation.ScriptBlock
Parameter Sets: (All)
Aliases:

Required: True
Position: 1
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="eb07e-180">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="eb07e-180">CommonParameters</span></span>

<span data-ttu-id="eb07e-181">Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="eb07e-181">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="eb07e-182">Zie [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="eb07e-182">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="eb07e-183">INVOER</span><span class="sxs-lookup"><span data-stu-id="eb07e-183">INPUTS</span></span>

### <span data-ttu-id="eb07e-184">System. String</span><span class="sxs-lookup"><span data-stu-id="eb07e-184">System.String</span></span>

<span data-ttu-id="eb07e-185">U kunt een module naam door sluizen naar deze cmdlet.</span><span class="sxs-lookup"><span data-stu-id="eb07e-185">You can pipe a module name to this cmdlet.</span></span>

## <span data-ttu-id="eb07e-186">UITVOER</span><span class="sxs-lookup"><span data-stu-id="eb07e-186">OUTPUTS</span></span>

### <span data-ttu-id="eb07e-187">System. Management. Automation. PSModuleInfo, System. Management. Automation. PSCustomObject of geen</span><span class="sxs-lookup"><span data-stu-id="eb07e-187">System.Management.Automation.PSModuleInfo, System.Management.Automation.PSCustomObject, or None</span></span>

<span data-ttu-id="eb07e-188">Met deze cmdlet wordt standaard een **PSModuleInfo** -object gegenereerd.</span><span class="sxs-lookup"><span data-stu-id="eb07e-188">This cmdlet generates a **PSModuleInfo** object, by default.</span></span> <span data-ttu-id="eb07e-189">Als u de para meter **AsCustomObject** gebruikt, wordt er een **PSCustomObject** -object gegenereerd.</span><span class="sxs-lookup"><span data-stu-id="eb07e-189">If you use the **AsCustomObject** parameter, it generates a **PSCustomObject** object.</span></span> <span data-ttu-id="eb07e-190">Als u de para meter **ReturnResult** gebruikt, wordt het resultaat van het evalueren van het script blok in de dynamische module geretourneerd.</span><span class="sxs-lookup"><span data-stu-id="eb07e-190">If you use the **ReturnResult** parameter, it returns the result of evaluating the script block in the dynamic module.</span></span>

## <span data-ttu-id="eb07e-191">OPMERKINGEN</span><span class="sxs-lookup"><span data-stu-id="eb07e-191">NOTES</span></span>

<span data-ttu-id="eb07e-192">U kunt ook verwijzen naar `New-Module` de alias `nmo` .</span><span class="sxs-lookup"><span data-stu-id="eb07e-192">You can also refer to `New-Module` by its alias, `nmo`.</span></span> <span data-ttu-id="eb07e-193">Zie [about_Aliases](About/about_Aliases.md)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="eb07e-193">For more information, see [about_Aliases](About/about_Aliases.md).</span></span>

## <span data-ttu-id="eb07e-194">GERELATEERDE KOPPELINGEN</span><span class="sxs-lookup"><span data-stu-id="eb07e-194">RELATED LINKS</span></span>

[<span data-ttu-id="eb07e-195">Exporteren-ModuleMember</span><span class="sxs-lookup"><span data-stu-id="eb07e-195">Export-ModuleMember</span></span>](Export-ModuleMember.md)

[<span data-ttu-id="eb07e-196">Get-module</span><span class="sxs-lookup"><span data-stu-id="eb07e-196">Get-Module</span></span>](Get-Module.md)

[<span data-ttu-id="eb07e-197">Import-module</span><span class="sxs-lookup"><span data-stu-id="eb07e-197">Import-Module</span></span>](Import-Module.md)

[<span data-ttu-id="eb07e-198">Remove-module</span><span class="sxs-lookup"><span data-stu-id="eb07e-198">Remove-Module</span></span>](Remove-Module.md)

