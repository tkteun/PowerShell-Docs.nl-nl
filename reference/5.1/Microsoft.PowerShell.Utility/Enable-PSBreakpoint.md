---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 10/09/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/enable-psbreakpoint?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Enable-PSBreakpoint
ms.openlocfilehash: 9530e3bc15360245de334a6f45ff35883181a41e
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/07/2020
ms.locfileid: "93250463"
---
# <span data-ttu-id="fd302-103">Enable-PSBreakpoint</span><span class="sxs-lookup"><span data-stu-id="fd302-103">Enable-PSBreakpoint</span></span>

## <span data-ttu-id="fd302-104">SAMENVATTING</span><span class="sxs-lookup"><span data-stu-id="fd302-104">SYNOPSIS</span></span>
<span data-ttu-id="fd302-105">Hiermee schakelt u de onderbrekings punten in de huidige console in.</span><span class="sxs-lookup"><span data-stu-id="fd302-105">Enables the breakpoints in the current console.</span></span>

## <span data-ttu-id="fd302-106">SYNTAXIS</span><span class="sxs-lookup"><span data-stu-id="fd302-106">SYNTAX</span></span>

### <span data-ttu-id="fd302-107">Id (standaard)</span><span class="sxs-lookup"><span data-stu-id="fd302-107">Id (Default)</span></span>

```
Enable-PSBreakpoint [-PassThru] [-Id] <Int32[]> [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="fd302-108">Stopt</span><span class="sxs-lookup"><span data-stu-id="fd302-108">Breakpoint</span></span>

```
Enable-PSBreakpoint [-PassThru] [-Breakpoint] <Breakpoint[]> [-WhatIf] [-Confirm]
 [<CommonParameters>]
```

## <span data-ttu-id="fd302-109">BESCHRIJVING</span><span class="sxs-lookup"><span data-stu-id="fd302-109">DESCRIPTION</span></span>

<span data-ttu-id="fd302-110">`Enable-PSBreakpoint`Met de cmdlet worden uitgeschakelde onderbrekings punten opnieuw ingeschakeld.</span><span class="sxs-lookup"><span data-stu-id="fd302-110">The `Enable-PSBreakpoint` cmdlet re-enables disabled breakpoints.</span></span> <span data-ttu-id="fd302-111">U kunt deze gebruiken om alle onderbrekings punten of specifieke onderbrekings punten in te scha kelen door Break Point-objecten of-Id's op te geven.</span><span class="sxs-lookup"><span data-stu-id="fd302-111">You can use it to enable all breakpoints, or specific breakpoints by providing breakpoint objects or IDs.</span></span>

<span data-ttu-id="fd302-112">Een onderbrekings punt is een Point in een script waar de uitvoering tijdelijk wordt gestopt, zodat u de status van het script kunt controleren.</span><span class="sxs-lookup"><span data-stu-id="fd302-112">A breakpoint is a point in a script where execution stops temporarily so that you can examine the state of the script.</span></span> <span data-ttu-id="fd302-113">Nieuw gemaakte onderbrekings punten worden automatisch ingeschakeld, maar kunnen worden uitgeschakeld met `Disable-PSBreakpoint` .</span><span class="sxs-lookup"><span data-stu-id="fd302-113">Newly created breakpoints are automatically enabled, but can be disabled using `Disable-PSBreakpoint`.</span></span>

<span data-ttu-id="fd302-114">Technisch gesp roken wijzigt deze cmdlet de waarde van de eigenschap **enabled** van een Break Point-object in **True**.</span><span class="sxs-lookup"><span data-stu-id="fd302-114">Technically, this cmdlet changes the value of the **Enabled** property of a breakpoint object to **True**.</span></span>

<span data-ttu-id="fd302-115">`Enable-PSBreakpoint` is een van de verschillende cmdlets die zijn ontworpen voor fout opsporing in Power shell-scripts.</span><span class="sxs-lookup"><span data-stu-id="fd302-115">`Enable-PSBreakpoint` is one of several cmdlets designed for debugging PowerShell scripts.</span></span> <span data-ttu-id="fd302-116">Zie [about_Debuggers](../Microsoft.PowerShell.Core/About/about_Debuggers.md)voor meer informatie over de Power Shell-fout opsporing.</span><span class="sxs-lookup"><span data-stu-id="fd302-116">For more information about the PowerShell debugger, see [about_Debuggers](../Microsoft.PowerShell.Core/About/about_Debuggers.md).</span></span>

## <span data-ttu-id="fd302-117">VOORBEELDEN</span><span class="sxs-lookup"><span data-stu-id="fd302-117">EXAMPLES</span></span>

### <span data-ttu-id="fd302-118">Voor beeld 1: alle onderbrekings punten inschakelen</span><span class="sxs-lookup"><span data-stu-id="fd302-118">Example 1: Enable all breakpoints</span></span>

<span data-ttu-id="fd302-119">In dit voor beeld worden alle onderbrekings punten in de huidige sessie ingeschakeld.</span><span class="sxs-lookup"><span data-stu-id="fd302-119">This example enables all breakpoints in the current session.</span></span>

```powershell
Get-PSBreakpoint | Enable-PSBreakpoint
```

<span data-ttu-id="fd302-120">Met behulp van aliassen kan dit voor beeld worden afgekort tot `gbp | ebp` .</span><span class="sxs-lookup"><span data-stu-id="fd302-120">Using aliases, this example can be abbreviated as `gbp | ebp`.</span></span>

### <span data-ttu-id="fd302-121">Voor beeld 2: onderbrekings punten op ID inschakelen</span><span class="sxs-lookup"><span data-stu-id="fd302-121">Example 2: Enable breakpoints by ID</span></span>

<span data-ttu-id="fd302-122">In dit voor beeld worden meerdere onderbrekings punten met de onderbrekings punt-Id's ingeschakeld.</span><span class="sxs-lookup"><span data-stu-id="fd302-122">This example enables multiple breakpoints using their breakpoint IDs.</span></span>

```powershell
Enable-PSBreakpoint -Id 0, 1, 5
```

### <span data-ttu-id="fd302-123">Voor beeld 3: een uitgeschakeld onderbrekings punt inschakelen</span><span class="sxs-lookup"><span data-stu-id="fd302-123">Example 3: Enable a disabled breakpoint</span></span>

<span data-ttu-id="fd302-124">In dit voor beeld wordt een onderbrekings punt dat is uitgeschakeld opnieuw ingeschakeld.</span><span class="sxs-lookup"><span data-stu-id="fd302-124">This example re-enables a breakpoint that has been disabled.</span></span>

```powershell
$B = Set-PSBreakpoint -Script "sample.ps1" -Variable Name -PassThru
$B | Enable-PSBreakpoint -PassThru
```

```Output
AccessMode : Write
Variable   : Name
Action     :
Enabled    : False
HitCount   : 0
Id         : 0
Script     : C:\ps-test\sample.ps1
ScriptName : C:\ps-test\sample.ps1

AccessMode : Write
Variable   : Name
Action     :
Enabled    : True
HitCount   : 0
Id         : 0
Script     : C:\ps-test\sample.ps1
ScriptName : C:\ps-test\sample.ps1
```

<span data-ttu-id="fd302-125">`Set-PSBreakpoint` Hiermee maakt u een onderbrekings punt in de variabele **naam** in het `Sample.ps1` script om het onderbrekings punt object in de variabele op te slaan `$B` .</span><span class="sxs-lookup"><span data-stu-id="fd302-125">`Set-PSBreakpoint` creates a breakpoint on the **Name** variable in the `Sample.ps1` script saving the breakpoint object in the `$B` variable.</span></span> <span data-ttu-id="fd302-126">De para meter **PassThru** geeft de waarde weer van de eigenschap **enabled** van het onderbrekings punt is **Onwaar**.</span><span class="sxs-lookup"><span data-stu-id="fd302-126">The **PassThru** parameter displays the value of the **Enabled** property of the breakpoint is **False**.</span></span>

<span data-ttu-id="fd302-127">`Enable-PSBreakpoint` Hiermee schakelt u het onderbrekings punt opnieuw in.</span><span class="sxs-lookup"><span data-stu-id="fd302-127">`Enable-PSBreakpoint` re-enables the breakpoint.</span></span> <span data-ttu-id="fd302-128">Ook als u de para meter **PassThru** gebruikt, ziet u dat de waarde van de eigenschap **ingeschakeld is ingesteld** op **True**.</span><span class="sxs-lookup"><span data-stu-id="fd302-128">Again, using the **PassThru** parameter we see that the value of the **Enabled** property is **True**.</span></span>

### <span data-ttu-id="fd302-129">Voor beeld 4: onderbrekings punten inschakelen met behulp van een variabele</span><span class="sxs-lookup"><span data-stu-id="fd302-129">Example 4: Enable breakpoints using a variable</span></span>

<span data-ttu-id="fd302-130">In dit voor beeld wordt een set onderbrekings punten ingeschakeld met behulp van de Break Point-objecten.</span><span class="sxs-lookup"><span data-stu-id="fd302-130">This example enables a set of breakpoints using the breakpoint objects.</span></span>

```powershell
$B = Get-PSBreakpoint -Id 3, 5
Enable-PSBreakpoint -Breakpoint $B
```

<span data-ttu-id="fd302-131">`Get-PSBreakpoint` Hiermee worden de onderbrekings punten opgehaald en opgeslagen in de `$B` variabele.</span><span class="sxs-lookup"><span data-stu-id="fd302-131">`Get-PSBreakpoint` gets the breakpoints and saves them in the `$B` variable.</span></span> <span data-ttu-id="fd302-132">Met de para meter **Break Point** worden `Enable-PSBreakpoint` de onderbrekings punten ingeschakeld.</span><span class="sxs-lookup"><span data-stu-id="fd302-132">Using the **Breakpoint** parameter, `Enable-PSBreakpoint` enables the breakpoints.</span></span>

<span data-ttu-id="fd302-133">Dit voor beeld is gelijk aan het uitvoeren van `Enable-PSBreakpoint -Id 3, 5` .</span><span class="sxs-lookup"><span data-stu-id="fd302-133">This example is equivalent to running `Enable-PSBreakpoint -Id 3, 5`.</span></span>

## <span data-ttu-id="fd302-134">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="fd302-134">PARAMETERS</span></span>

### <span data-ttu-id="fd302-135">-Onderbrekings punt</span><span class="sxs-lookup"><span data-stu-id="fd302-135">-Breakpoint</span></span>

<span data-ttu-id="fd302-136">Hiermee geeft u de onderbrekings punten die moeten worden ingeschakeld.</span><span class="sxs-lookup"><span data-stu-id="fd302-136">Specifies the breakpoints to enable.</span></span> <span data-ttu-id="fd302-137">Geef een variabele op die onderbrekings punten bevat of een opdracht die Break Point-objecten (bijvoorbeeld) ophaalt `Get-PSBreakpoint` .</span><span class="sxs-lookup"><span data-stu-id="fd302-137">Provide a variable containing breakpoints or a command that gets breakpoint objects, such as `Get-PSBreakpoint`.</span></span> <span data-ttu-id="fd302-138">U kunt ook pipet-objecten naar `Enable-PSBreakpoint` .</span><span class="sxs-lookup"><span data-stu-id="fd302-138">You can also pipe breakpoint objects to `Enable-PSBreakpoint`.</span></span>

```yaml
Type: System.Management.Automation.Breakpoint[]
Parameter Sets: Breakpoint
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="fd302-139">-Id</span><span class="sxs-lookup"><span data-stu-id="fd302-139">-Id</span></span>

<span data-ttu-id="fd302-140">Hiermee geeft u de **id-** nummers op van de onderbrekings punten die moeten worden ingeschakeld.</span><span class="sxs-lookup"><span data-stu-id="fd302-140">Specifies the **Id** numbers of the breakpoints to enable.</span></span> <span data-ttu-id="fd302-141">De standaard waarde is alle onderbrekings punten.</span><span class="sxs-lookup"><span data-stu-id="fd302-141">The default value is all breakpoints.</span></span>
<span data-ttu-id="fd302-142">Geef de **id** op per getal of in een variabele.</span><span class="sxs-lookup"><span data-stu-id="fd302-142">Provide the **Id** by number or in a variable.</span></span> <span data-ttu-id="fd302-143">U kunt geen **id-** nummers door sluizen naar `Enable-PSBreakpoint` .</span><span class="sxs-lookup"><span data-stu-id="fd302-143">You can't pipe **Id** numbers to `Enable-PSBreakpoint`.</span></span> <span data-ttu-id="fd302-144">Als u de **id** van een onderbrekings punt wilt zoeken, gebruikt u de `Get-PSBreakpoint` cmdlet.</span><span class="sxs-lookup"><span data-stu-id="fd302-144">To find the **Id** of a breakpoint, use the `Get-PSBreakpoint` cmdlet.</span></span>

```yaml
Type: System.Int32[]
Parameter Sets: Id
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="fd302-145">-PassThru</span><span class="sxs-lookup"><span data-stu-id="fd302-145">-PassThru</span></span>

<span data-ttu-id="fd302-146">Retourneert een object dat het onderbrekings punt vertegenwoordigt dat wordt ingeschakeld.</span><span class="sxs-lookup"><span data-stu-id="fd302-146">Returns an object representing the breakpoint being enabled.</span></span> <span data-ttu-id="fd302-147">Deze cmdlet genereert standaard geen uitvoer.</span><span class="sxs-lookup"><span data-stu-id="fd302-147">By default, this cmdlet doesn't generate any output.</span></span>

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

### <span data-ttu-id="fd302-148">-Confirm</span><span class="sxs-lookup"><span data-stu-id="fd302-148">-Confirm</span></span>

<span data-ttu-id="fd302-149">Hiermee wordt u gevraagd om bevestiging voordat u de cmdlet uitvoert.</span><span class="sxs-lookup"><span data-stu-id="fd302-149">Prompts you for confirmation before running the cmdlet.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: cf

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="fd302-150">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="fd302-150">-WhatIf</span></span>

<span data-ttu-id="fd302-151">Hiermee wordt weergegeven wat er zou gebeuren als u de cmdlet uitvoert.</span><span class="sxs-lookup"><span data-stu-id="fd302-151">Shows what would happen if the cmdlet runs.</span></span> <span data-ttu-id="fd302-152">De cmdlet wordt niet uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="fd302-152">The cmdlet isn't run.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: wi

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="fd302-153">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="fd302-153">CommonParameters</span></span>

<span data-ttu-id="fd302-154">Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="fd302-154">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="fd302-155">Zie [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="fd302-155">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="fd302-156">INVOER</span><span class="sxs-lookup"><span data-stu-id="fd302-156">INPUTS</span></span>

### <span data-ttu-id="fd302-157">System. Management. Automation. Break Point</span><span class="sxs-lookup"><span data-stu-id="fd302-157">System.Management.Automation.Breakpoint</span></span>

<span data-ttu-id="fd302-158">U kunt een onderbrekings punt object door sluizen naar `Enable-PSBreakpoint` .</span><span class="sxs-lookup"><span data-stu-id="fd302-158">You can pipe a breakpoint object to `Enable-PSBreakpoint`.</span></span>

## <span data-ttu-id="fd302-159">UITVOER</span><span class="sxs-lookup"><span data-stu-id="fd302-159">OUTPUTS</span></span>

### <span data-ttu-id="fd302-160">Geen of System. Management. Automation. Break Point</span><span class="sxs-lookup"><span data-stu-id="fd302-160">None or System.Management.Automation.Breakpoint</span></span>

<span data-ttu-id="fd302-161">Wanneer u de para meter **PassThru** gebruikt, `Enable-PSBreakpoint` retourneert een Break Point-object dat de ingeschakelde onderbrekings punt vertegenwoordigt.</span><span class="sxs-lookup"><span data-stu-id="fd302-161">When you use the **PassThru** parameter, `Enable-PSBreakpoint` returns a breakpoint object that represents that breakpoint that was enabled.</span></span> <span data-ttu-id="fd302-162">Anders wordt met deze cmdlet geen uitvoer gegenereerd.</span><span class="sxs-lookup"><span data-stu-id="fd302-162">Otherwise, this cmdlet doesn't generate any output.</span></span>

## <span data-ttu-id="fd302-163">OPMERKINGEN</span><span class="sxs-lookup"><span data-stu-id="fd302-163">NOTES</span></span>

- <span data-ttu-id="fd302-164">De `Enable-PSBreakpoint` cmdlet genereert geen fout als u probeert een onderbrekings punt in te scha kelen dat al is ingeschakeld.</span><span class="sxs-lookup"><span data-stu-id="fd302-164">The `Enable-PSBreakpoint` cmdlet doesn't generate an error if you try to enable a breakpoint that is already enabled.</span></span> <span data-ttu-id="fd302-165">Zo kunt u alle onderbrekings punten zonder fouten inschakelen, zelfs wanneer er slechts enkele zijn uitgeschakeld.</span><span class="sxs-lookup"><span data-stu-id="fd302-165">As such, you can enable all breakpoints without error, even when only a few are disabled.</span></span>

- <span data-ttu-id="fd302-166">Onderbrekings punten worden ingeschakeld wanneer u deze maakt met behulp van de- `Set-PSBreakpoint` cmdlet.</span><span class="sxs-lookup"><span data-stu-id="fd302-166">Breakpoints are enabled when you create them by using the `Set-PSBreakpoint` cmdlet.</span></span> <span data-ttu-id="fd302-167">U hoeft geen nieuw gemaakte onderbrekings punten in te scha kelen.</span><span class="sxs-lookup"><span data-stu-id="fd302-167">You don't need to enable newly created breakpoints.</span></span>

## <span data-ttu-id="fd302-168">GERELATEERDE KOPPELINGEN</span><span class="sxs-lookup"><span data-stu-id="fd302-168">RELATED LINKS</span></span>

[<span data-ttu-id="fd302-169">Disable-PSBreakpoint</span><span class="sxs-lookup"><span data-stu-id="fd302-169">Disable-PSBreakpoint</span></span>](Disable-PSBreakpoint.md)

[<span data-ttu-id="fd302-170">Get-PSBreakpoint</span><span class="sxs-lookup"><span data-stu-id="fd302-170">Get-PSBreakpoint</span></span>](Get-PSBreakpoint.md)

[<span data-ttu-id="fd302-171">Get-PSCallStack</span><span class="sxs-lookup"><span data-stu-id="fd302-171">Get-PSCallStack</span></span>](Get-PSCallStack.md)

[<span data-ttu-id="fd302-172">Remove-PSBreakpoint</span><span class="sxs-lookup"><span data-stu-id="fd302-172">Remove-PSBreakpoint</span></span>](Remove-PSBreakpoint.md)

[<span data-ttu-id="fd302-173">Set-PSBreakpoint</span><span class="sxs-lookup"><span data-stu-id="fd302-173">Set-PSBreakpoint</span></span>](Set-PSBreakpoint.md)
