---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 12/09/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/measure-command?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Measure-Command
ms.openlocfilehash: 4fb4553a75bf6cd5e458cc7d87c37e9a13ce0ea2
ms.sourcegitcommit: 165d10405d9db3a68c417a239d3181378fd02b9b
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 12/09/2020
ms.locfileid: "96935932"
---
# <span data-ttu-id="75629-103">Measure-Command</span><span class="sxs-lookup"><span data-stu-id="75629-103">Measure-Command</span></span>

## <span data-ttu-id="75629-104">SAMENVATTING</span><span class="sxs-lookup"><span data-stu-id="75629-104">SYNOPSIS</span></span>
<span data-ttu-id="75629-105">Meet de tijd die nodig is voor het uitvoeren van script blokken en-cmdlets.</span><span class="sxs-lookup"><span data-stu-id="75629-105">Measures the time it takes to run script blocks and cmdlets.</span></span>

## <span data-ttu-id="75629-106">SYNTAXIS</span><span class="sxs-lookup"><span data-stu-id="75629-106">SYNTAX</span></span>

```
Measure-Command [-InputObject <PSObject>] [-Expression] <ScriptBlock> [<CommonParameters>]
```

## <span data-ttu-id="75629-107">BESCHRIJVING</span><span class="sxs-lookup"><span data-stu-id="75629-107">DESCRIPTION</span></span>

<span data-ttu-id="75629-108">De `Measure-Command` cmdlet voert een script blok of cmdlet intern uit, keer de uitvoering van de bewerking en retourneert de uitvoerings tijd.</span><span class="sxs-lookup"><span data-stu-id="75629-108">The `Measure-Command` cmdlet runs a script block or cmdlet internally, times the execution of the operation, and returns the execution time.</span></span>

> [!NOTE]
> <span data-ttu-id="75629-109">Script blokken worden uitgevoerd door uit te `Measure-Command` voeren in het huidige bereik, niet op een onderliggend bereik.</span><span class="sxs-lookup"><span data-stu-id="75629-109">Script blocks run by `Measure-Command` run in the current scope, not a child scope.</span></span>

## <span data-ttu-id="75629-110">VOORBEELDEN</span><span class="sxs-lookup"><span data-stu-id="75629-110">EXAMPLES</span></span>

### <span data-ttu-id="75629-111">Voor beeld 1: een opdracht meten</span><span class="sxs-lookup"><span data-stu-id="75629-111">Example 1: Measure a command</span></span>

<span data-ttu-id="75629-112">In dit voor beeld wordt de tijd gemeten die nodig is om een opdracht uit te voeren `Get-EventLog` waarmee de gebeurtenissen in het gebeurtenis logboek van Windows Power shell worden opgehaald.</span><span class="sxs-lookup"><span data-stu-id="75629-112">This example measures the time it takes to run a `Get-EventLog` command that gets the events in the Windows PowerShell event log.</span></span>

```powershell
Measure-Command { Get-EventLog "windows powershell" }
```

### <span data-ttu-id="75629-113">Voor beeld 2: twee uitvoer van Measure-Command vergelijken</span><span class="sxs-lookup"><span data-stu-id="75629-113">Example 2: Compare two outputs from Measure-Command</span></span>

<span data-ttu-id="75629-114">De eerste opdracht meet de tijd die nodig is voor het verwerken van een recursieve `Get-ChildItem` opdracht die gebruikmaakt van de para meter **Path** om alleen `.txt` bestanden in de `C:\Windows` map en de bijbehorende submappen op te halen.</span><span class="sxs-lookup"><span data-stu-id="75629-114">The first command measures the time it takes to process a recursive `Get-ChildItem` command that uses the **Path** parameter to get only `.txt` files in the `C:\Windows` directory and its subdirectories.</span></span>

<span data-ttu-id="75629-115">De tweede opdracht meet de tijd die nodig is voor het verwerken van een recursieve `Get-ChildItem` opdracht die gebruikmaakt van de para meter voor de provider.</span><span class="sxs-lookup"><span data-stu-id="75629-115">The second command measures the time it takes to process a recursive `Get-ChildItem` command that uses the provider-specific \` parameter.</span></span>

<span data-ttu-id="75629-116">Met deze opdrachten wordt de waarde weer gegeven van het gebruik van een provider-specifiek filter in Power shell-opdrachten.</span><span class="sxs-lookup"><span data-stu-id="75629-116">These commands show the value of using a provider-specific filter in PowerShell commands.</span></span>

```powershell
Measure-Command { Get-ChildItem -Path C:\Windows\*.txt -Recurse }
```

```Output
Days              : 0
Hours             : 0
Minutes           : 0
Seconds           : 8
Milliseconds      : 618
Ticks             : 86182763
TotalDays         : 9.9748568287037E-05
TotalHours        : 0.00239396563888889
TotalMinutes      : 0.143637938333333
TotalSeconds      : 8.6182763
TotalMilliseconds : 8618.2763
```

```powershell
Measure-Command {Get-ChildItem C:\Windows -Filter "*.txt" -Recurse}
```

```Output
Days              : 0
Hours             : 0
Minutes           : 0
Seconds           : 1
Milliseconds      : 140
Ticks             : 11409189
TotalDays         : 1.32050798611111E-05
TotalHours        : 0.000316921916666667
TotalMinutes      : 0.019015315
TotalSeconds      : 1.1409189
TotalMilliseconds : 1140.9189
```

### <span data-ttu-id="75629-117">Voor beeld 3: pijpleiding invoer naar Measure-Command</span><span class="sxs-lookup"><span data-stu-id="75629-117">Example 3: Piping input to Measure-Command</span></span>

<span data-ttu-id="75629-118">Objecten waarnaar wordt gepiped `Measure-Command` , zijn beschikbaar voor het script blok dat wordt door gegeven aan de para meter **Expression** .</span><span class="sxs-lookup"><span data-stu-id="75629-118">Objects that are piped to `Measure-Command` are available to the script block that is passed to the **Expression** parameter.</span></span> <span data-ttu-id="75629-119">Het script blok wordt één keer uitgevoerd voor elk object in de pijp lijn.</span><span class="sxs-lookup"><span data-stu-id="75629-119">The script block is executed once for each object on the pipeline.</span></span>

```powershell
# Perform a simple operation to demonstrate the InputObject parameter
# Note that no output is displayed.
10, 20, 50 | Measure-Command -Expression { for ($i=0; $i -lt $_; $i++) {$i} }
```

```Output
Days              : 0
Hours             : 0
Minutes           : 0
Seconds           : 0
Milliseconds      : 12
Ticks             : 122672
TotalDays         : 1.41981481481481E-07
TotalHours        : 3.40755555555556E-06
TotalMinutes      : 0.000204453333333333
TotalSeconds      : 0.0122672
TotalMilliseconds : 12.2672
```

### <span data-ttu-id="75629-120">Voor beeld 4: uitvoer van gemeten opdracht weer geven</span><span class="sxs-lookup"><span data-stu-id="75629-120">Example 4: Displaying output of measured command</span></span>

<span data-ttu-id="75629-121">Als u de uitvoer van de expressie in wilt weer geven, `Measure-Command` kunt u een pipe gebruiken `Out-Default` .</span><span class="sxs-lookup"><span data-stu-id="75629-121">To display output of expression in `Measure-Command` you can use a pipe to `Out-Default`.</span></span>

```powershell
# Perform the same operation as above adding Out-Default to every execution.
# This will show that the ScriptBlock is in fact executing for every item.
10, 20, 50 | Measure-Command -Expression {for ($i=0; $i -lt $_; $i++) {$i}; "$($_)" | Out-Default }
```

```Output
10
20
50


Days              : 0
Hours             : 0
Minutes           : 0
Seconds           : 0
Milliseconds      : 11
Ticks             : 113745
TotalDays         : 1.31649305555556E-07
TotalHours        : 3.15958333333333E-06
TotalMinutes      : 0.000189575
TotalSeconds      : 0.0113745
TotalMilliseconds : 11.3745
```

### <span data-ttu-id="75629-122">Voor beeld 5: uitvoering meten in een onderliggend bereik</span><span class="sxs-lookup"><span data-stu-id="75629-122">Example 5: Measuring execution in a child scope</span></span>

<span data-ttu-id="75629-123">`Measure-Command` Hiermee wordt het script blok in het huidige bereik uitgevoerd, zodat het script blok waarden in het huidige bereik kan wijzigen.</span><span class="sxs-lookup"><span data-stu-id="75629-123">`Measure-Command` runs the script block in the current scope, so the script block can modify values in the current scope.</span></span> <span data-ttu-id="75629-124">Als u wilt voor komen dat de huidige scope wordt gewijzigd, moet u het script blok in accolades ( `{}` ) plaatsen en de aanroep operator ( `&` ) gebruiken om het blok in een onderliggend bereik uit te voeren.</span><span class="sxs-lookup"><span data-stu-id="75629-124">To avoid changes to the current scope, you must wrap the script block in braces (`{}`) and use the invocation operator (`&`) to execute the block in a child scope.</span></span>

```powershell
$foo = 'Value 1'
$null = Measure-Command { $foo = 'Value 2' }
$foo
$null = Measure-Command { & { $foo = 'Value 3' } }
$foo
```

```Output
Value 2
Value 2
```

<span data-ttu-id="75629-125">Zie [about_Operators](../Microsoft.PowerShell.Core/About/about_Operators.md#call-operator-)voor meer informatie over de aanroep operator.</span><span class="sxs-lookup"><span data-stu-id="75629-125">For more information about the invocation operator, see [about_Operators](../Microsoft.PowerShell.Core/About/about_Operators.md#call-operator-).</span></span>

## <span data-ttu-id="75629-126">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="75629-126">PARAMETERS</span></span>

### <span data-ttu-id="75629-127">-Expressie</span><span class="sxs-lookup"><span data-stu-id="75629-127">-Expression</span></span>

<span data-ttu-id="75629-128">Hiermee geeft u de expressie op waarvoor een time-out is ingesteld.</span><span class="sxs-lookup"><span data-stu-id="75629-128">Specifies the expression that is being timed.</span></span> <span data-ttu-id="75629-129">Plaats de expressie tussen accolades ( `{}` ).</span><span class="sxs-lookup"><span data-stu-id="75629-129">Enclose the expression in braces (`{}`).</span></span>

```yaml
Type: System.Management.Automation.ScriptBlock
Parameter Sets: (All)
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="75629-130">-Input object</span><span class="sxs-lookup"><span data-stu-id="75629-130">-InputObject</span></span>

<span data-ttu-id="75629-131">Objecten die zijn gekoppeld aan de para meter **input object** zijn optionele invoer voor het script blok dat is door gegeven aan de para meter **Expression** .</span><span class="sxs-lookup"><span data-stu-id="75629-131">Objects bound to the **InputObject** parameter are optional input for the script block passed to the **Expression** parameter.</span></span> <span data-ttu-id="75629-132">In het-script blok `$_` kan worden gebruikt om te verwijzen naar het huidige object in de pijp lijn.</span><span class="sxs-lookup"><span data-stu-id="75629-132">Inside the script block, `$_` can be used to reference the current object in the pipeline.</span></span>

```yaml
Type: System.Management.Automation.PSObject
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="75629-133">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="75629-133">CommonParameters</span></span>

<span data-ttu-id="75629-134">Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="75629-134">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="75629-135">Zie [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="75629-135">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="75629-136">INVOER</span><span class="sxs-lookup"><span data-stu-id="75629-136">INPUTS</span></span>

### <span data-ttu-id="75629-137">System. Management. Automation. PSObject</span><span class="sxs-lookup"><span data-stu-id="75629-137">System.Management.Automation.PSObject</span></span>

<span data-ttu-id="75629-138">U kunt een object door sluizen naar `Measure-Command` .</span><span class="sxs-lookup"><span data-stu-id="75629-138">You can pipe an object to `Measure-Command`.</span></span>

## <span data-ttu-id="75629-139">UITVOER</span><span class="sxs-lookup"><span data-stu-id="75629-139">OUTPUTS</span></span>

### <span data-ttu-id="75629-140">System. time span</span><span class="sxs-lookup"><span data-stu-id="75629-140">System.TimeSpan</span></span>

<span data-ttu-id="75629-141">`Measure-Command` retourneert een time span-object dat het resultaat voor stelt.</span><span class="sxs-lookup"><span data-stu-id="75629-141">`Measure-Command` returns a time span object that represents the result.</span></span>

## <span data-ttu-id="75629-142">OPMERKINGEN</span><span class="sxs-lookup"><span data-stu-id="75629-142">NOTES</span></span>

## <span data-ttu-id="75629-143">GERELATEERDE KOPPELINGEN</span><span class="sxs-lookup"><span data-stu-id="75629-143">RELATED LINKS</span></span>

[<span data-ttu-id="75629-144">Invoke-opdracht</span><span class="sxs-lookup"><span data-stu-id="75629-144">Invoke-Command</span></span>](../Microsoft.PowerShell.Core/Invoke-Command.md)

[<span data-ttu-id="75629-145">Tracering-opdracht</span><span class="sxs-lookup"><span data-stu-id="75629-145">Trace-Command</span></span>](Trace-Command.md)
