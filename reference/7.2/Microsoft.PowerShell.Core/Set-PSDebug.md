---
external help file: System.Management.Automation.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 08/22/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/set-psdebug?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Set-PSDebug
ms.openlocfilehash: 45764b09bfa1f632fe5c36ca76b32b4a1b54874c
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 11/17/2020
ms.locfileid: "94705610"
---
# <span data-ttu-id="b90d8-102">Set-PSDebug</span><span class="sxs-lookup"><span data-stu-id="b90d8-102">Set-PSDebug</span></span>

## <span data-ttu-id="b90d8-103">SAMENVATTING</span><span class="sxs-lookup"><span data-stu-id="b90d8-103">SYNOPSIS</span></span>
<span data-ttu-id="b90d8-104">Schakelt functies voor fout opsporing in scripts in-en uitschakelen, stelt het tracerings niveau in en schakelt de strikte modus in.</span><span class="sxs-lookup"><span data-stu-id="b90d8-104">Turns script debugging features on and off, sets the trace level, and toggles strict mode.</span></span>

## <span data-ttu-id="b90d8-105">SYNTAXIS</span><span class="sxs-lookup"><span data-stu-id="b90d8-105">SYNTAX</span></span>

### <span data-ttu-id="b90d8-106">op</span><span class="sxs-lookup"><span data-stu-id="b90d8-106">on</span></span>

```
Set-PSDebug [-Trace <Int32>] [-Step] [-Strict] [<CommonParameters>]
```

### <span data-ttu-id="b90d8-107">uit</span><span class="sxs-lookup"><span data-stu-id="b90d8-107">off</span></span>

```
Set-PSDebug [-Off] [<CommonParameters>]
```

## <span data-ttu-id="b90d8-108">BESCHRIJVING</span><span class="sxs-lookup"><span data-stu-id="b90d8-108">DESCRIPTION</span></span>

<span data-ttu-id="b90d8-109">Met de `Set-PSDebug` cmdlet worden functies voor fout opsporing in scripts in-en uitgeschakeld, wordt het tracerings niveau ingesteld en wordt de strikte modus ingeschakeld.</span><span class="sxs-lookup"><span data-stu-id="b90d8-109">The `Set-PSDebug` cmdlet turns script debugging features on and off, sets the trace level, and toggles strict mode.</span></span> <span data-ttu-id="b90d8-110">De Power shell-functies voor fout opsporing zijn standaard uitgeschakeld.</span><span class="sxs-lookup"><span data-stu-id="b90d8-110">By default, the PowerShell debug features are off.</span></span>

<span data-ttu-id="b90d8-111">Wanneer de **tracerings** parameter een waarde van heeft `1` , wordt elke regel van het script getraceerd wanneer deze wordt uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="b90d8-111">When the **Trace** parameter has a value of `1`, each line of script is traced as it runs.</span></span> <span data-ttu-id="b90d8-112">Wanneer de para meter een waarde heeft `2` , worden er ook variabele toewijzingen, functie aanroepen en script aanroepen getraceerd.</span><span class="sxs-lookup"><span data-stu-id="b90d8-112">When the parameter has a value of `2`, variable assignments, function calls, and script calls are also traced.</span></span> <span data-ttu-id="b90d8-113">Als de **stap** parameter is opgegeven, wordt u gevraagd om elke regel van het script wordt uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="b90d8-113">If the **Step** parameter is specified, you're prompted before each line of the script runs.</span></span>

## <span data-ttu-id="b90d8-114">VOORBEELDEN</span><span class="sxs-lookup"><span data-stu-id="b90d8-114">EXAMPLES</span></span>

### <span data-ttu-id="b90d8-115">Voor beeld 1: het tracerings niveau instellen</span><span class="sxs-lookup"><span data-stu-id="b90d8-115">Example 1: Set the trace level</span></span>

<span data-ttu-id="b90d8-116">In dit voor beeld wordt het tracerings niveau ingesteld op `2` en wordt vervolgens een script uitgevoerd dat de getallen 1, 2 en bevat.</span><span class="sxs-lookup"><span data-stu-id="b90d8-116">This example sets the trace level to `2`, and then runs a script that displays the numbers 1, 2, and</span></span>
3.

```powershell
Set-PSDebug -Trace 2; foreach ($i in 1..3) {$i}
```

```Output
DEBUG:    1+ Set-PSDebug -Trace 2; foreach ($i in  >>>> 1..3) {$i}
DEBUG:     ! SET $foreach = 'IEnumerator'.
DEBUG:    1+ Set-PSDebug -Trace 2; foreach ( >>>> $i in 1..3) {$i}
DEBUG:     ! SET $i = '1'.
DEBUG:    1+ Set-PSDebug -Trace 2; foreach ($i in 1..3) { >>>> $i}
1
DEBUG:    1+ Set-PSDebug -Trace 2; foreach ( >>>> $i in 1..3) {$i}
DEBUG:     ! SET $i = '2'.
DEBUG:    1+ Set-PSDebug -Trace 2; foreach ($i in 1..3) { >>>> $i}
2
DEBUG:    1+ Set-PSDebug -Trace 2; foreach ( >>>> $i in 1..3) {$i}
DEBUG:     ! SET $i = '3'.
DEBUG:    1+ Set-PSDebug -Trace 2; foreach ($i in 1..3) { >>>> $i}
3
DEBUG:    1+ Set-PSDebug -Trace 2; foreach ( >>>> $i in 1..3) {$i}
DEBUG:     ! SET $foreach = ''.
```

### <span data-ttu-id="b90d8-117">Voor beeld 2: Step Ping inschakelen</span><span class="sxs-lookup"><span data-stu-id="b90d8-117">Example 2: Turn on stepping</span></span>

<span data-ttu-id="b90d8-118">In dit voor beeld wordt Step ping ingeschakeld en wordt vervolgens een script uitgevoerd waarin de getallen 1, 2 en 3 worden weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="b90d8-118">This example turns on stepping, and then runs a script that displays the numbers 1, 2, and 3.</span></span>

```powershell
Set-PSDebug -Step; foreach ($i in 1..3) {$i}
```

```Output
Continue with this operation?
   1+ Set-PSDebug -Step; foreach ($i in  >>>> 1..3) {$i}
[Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "Y"): A
DEBUG:    1+ Set-PSDebug -Step; foreach ($i in  >>>> 1..3) {$i}
1
2
3
```

### <span data-ttu-id="b90d8-119">Voor beeld 3: strikte modus gebruiken</span><span class="sxs-lookup"><span data-stu-id="b90d8-119">Example 3: Use strict mode</span></span>

<span data-ttu-id="b90d8-120">In dit voor beeld wordt Power shell in de strikte modus geplaatst en wordt geprobeerd toegang te krijgen tot een variabele waaraan geen waarde is toegewezen.</span><span class="sxs-lookup"><span data-stu-id="b90d8-120">This example puts PowerShell in strict mode and attempts to access a variable that doesn't have an assigned value.</span></span>

```powershell
Set-PSDebug -Strict; $NewVar
```

```Output
The variable '$NewVar' cannot be retrieved because it has not been set.
At line:1 char:22
+ Set-PSDebug -Strict; $NewVar
```

### <span data-ttu-id="b90d8-121">Voor beeld 4: functies voor fout opsporing uitschakelen</span><span class="sxs-lookup"><span data-stu-id="b90d8-121">Example 4: Turn off debug features</span></span>

<span data-ttu-id="b90d8-122">In dit voor beeld worden alle functies voor fout opsporing uitgeschakeld en wordt vervolgens een script uitgevoerd waarin de getallen 1, 2 en 3 worden weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="b90d8-122">This example turns off all debugging features, and then runs a script that displays the numbers 1, 2, and 3.</span></span>

```powershell
Set-PSDebug -Off; foreach ($i in 1..3) {$i}
```

```Output
1
2
3
```

## <span data-ttu-id="b90d8-123">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="b90d8-123">PARAMETERS</span></span>

### <span data-ttu-id="b90d8-124">-Uit</span><span class="sxs-lookup"><span data-stu-id="b90d8-124">-Off</span></span>

<span data-ttu-id="b90d8-125">Hiermee schakelt u alle functies voor fout opsporing in scripts uit.</span><span class="sxs-lookup"><span data-stu-id="b90d8-125">Turns off all script debugging features.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: off
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="b90d8-126">-Stap</span><span class="sxs-lookup"><span data-stu-id="b90d8-126">-Step</span></span>

<span data-ttu-id="b90d8-127">Hiermee schakelt u script steping in.</span><span class="sxs-lookup"><span data-stu-id="b90d8-127">Turns on script stepping.</span></span> <span data-ttu-id="b90d8-128">Voordat elke regel wordt uitgevoerd, wordt u door Power shell gevraagd om te stoppen, door te gaan of een nieuw interpreter niveau in te voeren om de status van het script te controleren.</span><span class="sxs-lookup"><span data-stu-id="b90d8-128">Before each line runs, PowerShell prompts you to stop, continue, or enter a new interpreter level to inspect the state of the script.</span></span>

<span data-ttu-id="b90d8-129">Als u de para meter **stap** opgeeft, wordt automatisch een tracerings niveau ingesteld `1` .</span><span class="sxs-lookup"><span data-stu-id="b90d8-129">Specifying the **Step** parameter automatically sets a trace level of `1`.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: on
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="b90d8-130">-Strikte</span><span class="sxs-lookup"><span data-stu-id="b90d8-130">-Strict</span></span>

<span data-ttu-id="b90d8-131">Hiermee geeft u aan dat aan variabelen een waarde moet worden toegewezen voordat ernaar wordt verwezen in een script.</span><span class="sxs-lookup"><span data-stu-id="b90d8-131">Specifies that variables must be assigned a value before being referenced in a script.</span></span> <span data-ttu-id="b90d8-132">Als er wordt verwezen naar een variabele voordat een waarde wordt toegewezen, retourneert Power shell een uitzonderings fout.</span><span class="sxs-lookup"><span data-stu-id="b90d8-132">If a variable is referenced before a value is assigned, PowerShell returns an exception error.</span></span> <span data-ttu-id="b90d8-133">Dit is gelijk aan `Set-StrictMode -Version 1` .</span><span class="sxs-lookup"><span data-stu-id="b90d8-133">This is equivalent to `Set-StrictMode -Version 1`.</span></span> <span data-ttu-id="b90d8-134">Zie [set-StrictMode](Set-StrictMode.md)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="b90d8-134">For more information, see [Set-StrictMode](Set-StrictMode.md).</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: on
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="b90d8-135">-Traceren</span><span class="sxs-lookup"><span data-stu-id="b90d8-135">-Trace</span></span>

<span data-ttu-id="b90d8-136">Hiermee geeft u het tracerings niveau voor elke regel in een script.</span><span class="sxs-lookup"><span data-stu-id="b90d8-136">Specifies the trace level for each line in a script.</span></span> <span data-ttu-id="b90d8-137">Elke regel wordt getraceerd terwijl deze wordt uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="b90d8-137">Each line is traced as it's run.</span></span>

<span data-ttu-id="b90d8-138">De acceptabele waarden voor deze para meter zijn als volgt:</span><span class="sxs-lookup"><span data-stu-id="b90d8-138">The acceptable values for this parameter are as follows:</span></span>

- <span data-ttu-id="b90d8-139">0: script tracering uitschakelen.</span><span class="sxs-lookup"><span data-stu-id="b90d8-139">0: Turn script tracing off.</span></span>
- <span data-ttu-id="b90d8-140">1: Traceer script regels wanneer ze worden uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="b90d8-140">1: Trace script lines as they run.</span></span>
- <span data-ttu-id="b90d8-141">2: Traceer script regels, toewijzing van variabelen, functie aanroepen en scripts.</span><span class="sxs-lookup"><span data-stu-id="b90d8-141">2: Trace script lines, variable assignments, function calls, and scripts.</span></span>

```yaml
Type: System.Int32
Parameter Sets: on
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="b90d8-142">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="b90d8-142">CommonParameters</span></span>

<span data-ttu-id="b90d8-143">Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="b90d8-143">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="b90d8-144">Zie [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="b90d8-144">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="b90d8-145">INVOER</span><span class="sxs-lookup"><span data-stu-id="b90d8-145">INPUTS</span></span>

### <span data-ttu-id="b90d8-146">Geen</span><span class="sxs-lookup"><span data-stu-id="b90d8-146">None</span></span>

<span data-ttu-id="b90d8-147">U kunt geen pijplijn invoer voor deze cmdlet.</span><span class="sxs-lookup"><span data-stu-id="b90d8-147">You can't pipeline input to this cmdlet.</span></span>

## <span data-ttu-id="b90d8-148">UITVOER</span><span class="sxs-lookup"><span data-stu-id="b90d8-148">OUTPUTS</span></span>

### <span data-ttu-id="b90d8-149">Geen</span><span class="sxs-lookup"><span data-stu-id="b90d8-149">None</span></span>

<span data-ttu-id="b90d8-150">Met deze cmdlet wordt geen uitvoer geretourneerd.</span><span class="sxs-lookup"><span data-stu-id="b90d8-150">This cmdlet doesn't return any output.</span></span>

## <span data-ttu-id="b90d8-151">OPMERKINGEN</span><span class="sxs-lookup"><span data-stu-id="b90d8-151">NOTES</span></span>

## <span data-ttu-id="b90d8-152">GERELATEERDE KOPPELINGEN</span><span class="sxs-lookup"><span data-stu-id="b90d8-152">RELATED LINKS</span></span>

[<span data-ttu-id="b90d8-153">about_Debuggers</span><span class="sxs-lookup"><span data-stu-id="b90d8-153">about_Debuggers</span></span>](./About/about_Debuggers.md)

[<span data-ttu-id="b90d8-154">Debug-proces</span><span class="sxs-lookup"><span data-stu-id="b90d8-154">Debug-Process</span></span>](../Microsoft.PowerShell.Management/Debug-Process.md)

[<span data-ttu-id="b90d8-155">Set-PSBreakpoint</span><span class="sxs-lookup"><span data-stu-id="b90d8-155">Set-PSBreakpoint</span></span>](../Microsoft.PowerShell.Utility/Set-PSBreakpoint.md)

[<span data-ttu-id="b90d8-156">Set-StrictMode</span><span class="sxs-lookup"><span data-stu-id="b90d8-156">Set-StrictMode</span></span>](Set-StrictMode.md)

[<span data-ttu-id="b90d8-157">Schrijf fouten opsporen</span><span class="sxs-lookup"><span data-stu-id="b90d8-157">Write-Debug</span></span>](../Microsoft.PowerShell.Utility/Write-Debug.md)

