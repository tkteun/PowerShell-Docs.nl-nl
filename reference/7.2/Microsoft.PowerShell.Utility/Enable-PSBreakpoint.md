---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 10/09/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/enable-psbreakpoint?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Enable-PSBreakpoint
ms.openlocfilehash: 28cda7a2fa4435092b647e43a250222a852114b0
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 11/17/2020
ms.locfileid: "94705832"
---
# <span data-ttu-id="9cb66-102">Enable-PSBreakpoint</span><span class="sxs-lookup"><span data-stu-id="9cb66-102">Enable-PSBreakpoint</span></span>

## <span data-ttu-id="9cb66-103">SAMENVATTING</span><span class="sxs-lookup"><span data-stu-id="9cb66-103">SYNOPSIS</span></span>
<span data-ttu-id="9cb66-104">Hiermee schakelt u de onderbrekings punten in de huidige console in.</span><span class="sxs-lookup"><span data-stu-id="9cb66-104">Enables the breakpoints in the current console.</span></span>

## <span data-ttu-id="9cb66-105">SYNTAXIS</span><span class="sxs-lookup"><span data-stu-id="9cb66-105">SYNTAX</span></span>

### <span data-ttu-id="9cb66-106">Id (standaard)</span><span class="sxs-lookup"><span data-stu-id="9cb66-106">Id (Default)</span></span>

```
Enable-PSBreakpoint [-PassThru] [-Id] <Int32[]> [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="9cb66-107">Stopt</span><span class="sxs-lookup"><span data-stu-id="9cb66-107">Breakpoint</span></span>

```
Enable-PSBreakpoint [-PassThru] [-Breakpoint] <Breakpoint[]> [-WhatIf] [-Confirm]
 [<CommonParameters>]
```

## <span data-ttu-id="9cb66-108">BESCHRIJVING</span><span class="sxs-lookup"><span data-stu-id="9cb66-108">DESCRIPTION</span></span>

<span data-ttu-id="9cb66-109">`Enable-PSBreakpoint`Met de cmdlet worden uitgeschakelde onderbrekings punten opnieuw ingeschakeld.</span><span class="sxs-lookup"><span data-stu-id="9cb66-109">The `Enable-PSBreakpoint` cmdlet re-enables disabled breakpoints.</span></span> <span data-ttu-id="9cb66-110">U kunt deze gebruiken om alle onderbrekings punten of specifieke onderbrekings punten in te scha kelen door Break Point-objecten of-Id's op te geven.</span><span class="sxs-lookup"><span data-stu-id="9cb66-110">You can use it to enable all breakpoints, or specific breakpoints by providing breakpoint objects or IDs.</span></span>

<span data-ttu-id="9cb66-111">Een onderbrekings punt is een Point in een script waar de uitvoering tijdelijk wordt gestopt, zodat u de status van het script kunt controleren.</span><span class="sxs-lookup"><span data-stu-id="9cb66-111">A breakpoint is a point in a script where execution stops temporarily so that you can examine the state of the script.</span></span> <span data-ttu-id="9cb66-112">Nieuw gemaakte onderbrekings punten worden automatisch ingeschakeld, maar kunnen worden uitgeschakeld met `Disable-PSBreakpoint` .</span><span class="sxs-lookup"><span data-stu-id="9cb66-112">Newly created breakpoints are automatically enabled, but can be disabled using `Disable-PSBreakpoint`.</span></span>

<span data-ttu-id="9cb66-113">Technisch gesp roken wijzigt deze cmdlet de waarde van de eigenschap **enabled** van een Break Point-object in **True**.</span><span class="sxs-lookup"><span data-stu-id="9cb66-113">Technically, this cmdlet changes the value of the **Enabled** property of a breakpoint object to **True**.</span></span>

<span data-ttu-id="9cb66-114">`Enable-PSBreakpoint` is een van de verschillende cmdlets die zijn ontworpen voor fout opsporing in Power shell-scripts.</span><span class="sxs-lookup"><span data-stu-id="9cb66-114">`Enable-PSBreakpoint` is one of several cmdlets designed for debugging PowerShell scripts.</span></span> <span data-ttu-id="9cb66-115">Zie [about_Debuggers](../Microsoft.PowerShell.Core/About/about_Debuggers.md)voor meer informatie over de Power Shell-fout opsporing.</span><span class="sxs-lookup"><span data-stu-id="9cb66-115">For more information about the PowerShell debugger, see [about_Debuggers](../Microsoft.PowerShell.Core/About/about_Debuggers.md).</span></span>

## <span data-ttu-id="9cb66-116">VOORBEELDEN</span><span class="sxs-lookup"><span data-stu-id="9cb66-116">EXAMPLES</span></span>

### <span data-ttu-id="9cb66-117">Voor beeld 1: alle onderbrekings punten inschakelen</span><span class="sxs-lookup"><span data-stu-id="9cb66-117">Example 1: Enable all breakpoints</span></span>

<span data-ttu-id="9cb66-118">In dit voor beeld worden alle onderbrekings punten in de huidige sessie ingeschakeld.</span><span class="sxs-lookup"><span data-stu-id="9cb66-118">This example enables all breakpoints in the current session.</span></span>

```powershell
Get-PSBreakpoint | Enable-PSBreakpoint
```

<span data-ttu-id="9cb66-119">Met behulp van aliassen kan dit voor beeld worden afgekort tot `gbp | ebp` .</span><span class="sxs-lookup"><span data-stu-id="9cb66-119">Using aliases, this example can be abbreviated as `gbp | ebp`.</span></span>

### <span data-ttu-id="9cb66-120">Voor beeld 2: onderbrekings punten op ID inschakelen</span><span class="sxs-lookup"><span data-stu-id="9cb66-120">Example 2: Enable breakpoints by ID</span></span>

<span data-ttu-id="9cb66-121">In dit voor beeld worden meerdere onderbrekings punten met de onderbrekings punt-Id's ingeschakeld.</span><span class="sxs-lookup"><span data-stu-id="9cb66-121">This example enables multiple breakpoints using their breakpoint IDs.</span></span>

```powershell
Enable-PSBreakpoint -Id 0, 1, 5
```

### <span data-ttu-id="9cb66-122">Voor beeld 3: een uitgeschakeld onderbrekings punt inschakelen</span><span class="sxs-lookup"><span data-stu-id="9cb66-122">Example 3: Enable a disabled breakpoint</span></span>

<span data-ttu-id="9cb66-123">In dit voor beeld wordt een onderbrekings punt dat is uitgeschakeld opnieuw ingeschakeld.</span><span class="sxs-lookup"><span data-stu-id="9cb66-123">This example re-enables a breakpoint that has been disabled.</span></span>

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

<span data-ttu-id="9cb66-124">`Set-PSBreakpoint` Hiermee maakt u een onderbrekings punt in de variabele **naam** in het `Sample.ps1` script om het onderbrekings punt object in de variabele op te slaan `$B` .</span><span class="sxs-lookup"><span data-stu-id="9cb66-124">`Set-PSBreakpoint` creates a breakpoint on the **Name** variable in the `Sample.ps1` script saving the breakpoint object in the `$B` variable.</span></span> <span data-ttu-id="9cb66-125">De para meter **PassThru** geeft de waarde weer van de eigenschap **enabled** van het onderbrekings punt is **Onwaar**.</span><span class="sxs-lookup"><span data-stu-id="9cb66-125">The **PassThru** parameter displays the value of the **Enabled** property of the breakpoint is **False**.</span></span>

<span data-ttu-id="9cb66-126">`Enable-PSBreakpoint` Hiermee schakelt u het onderbrekings punt opnieuw in.</span><span class="sxs-lookup"><span data-stu-id="9cb66-126">`Enable-PSBreakpoint` re-enables the breakpoint.</span></span> <span data-ttu-id="9cb66-127">Ook als u de para meter **PassThru** gebruikt, ziet u dat de waarde van de eigenschap **ingeschakeld is ingesteld** op **True**.</span><span class="sxs-lookup"><span data-stu-id="9cb66-127">Again, using the **PassThru** parameter we see that the value of the **Enabled** property is **True**.</span></span>

### <span data-ttu-id="9cb66-128">Voor beeld 4: onderbrekings punten inschakelen met behulp van een variabele</span><span class="sxs-lookup"><span data-stu-id="9cb66-128">Example 4: Enable breakpoints using a variable</span></span>

<span data-ttu-id="9cb66-129">In dit voor beeld wordt een set onderbrekings punten ingeschakeld met behulp van de Break Point-objecten.</span><span class="sxs-lookup"><span data-stu-id="9cb66-129">This example enables a set of breakpoints using the breakpoint objects.</span></span>

```powershell
$B = Get-PSBreakpoint -Id 3, 5
Enable-PSBreakpoint -Breakpoint $B
```

<span data-ttu-id="9cb66-130">`Get-PSBreakpoint` Hiermee worden de onderbrekings punten opgehaald en opgeslagen in de `$B` variabele.</span><span class="sxs-lookup"><span data-stu-id="9cb66-130">`Get-PSBreakpoint` gets the breakpoints and saves them in the `$B` variable.</span></span> <span data-ttu-id="9cb66-131">Met de para meter **Break Point** worden `Enable-PSBreakpoint` de onderbrekings punten ingeschakeld.</span><span class="sxs-lookup"><span data-stu-id="9cb66-131">Using the **Breakpoint** parameter, `Enable-PSBreakpoint` enables the breakpoints.</span></span>

<span data-ttu-id="9cb66-132">Dit voor beeld is gelijk aan het uitvoeren van `Enable-PSBreakpoint -Id 3, 5` .</span><span class="sxs-lookup"><span data-stu-id="9cb66-132">This example is equivalent to running `Enable-PSBreakpoint -Id 3, 5`.</span></span>

## <span data-ttu-id="9cb66-133">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="9cb66-133">PARAMETERS</span></span>

### <span data-ttu-id="9cb66-134">-Onderbrekings punt</span><span class="sxs-lookup"><span data-stu-id="9cb66-134">-Breakpoint</span></span>

<span data-ttu-id="9cb66-135">Hiermee geeft u de onderbrekings punten die moeten worden ingeschakeld.</span><span class="sxs-lookup"><span data-stu-id="9cb66-135">Specifies the breakpoints to enable.</span></span> <span data-ttu-id="9cb66-136">Geef een variabele op die onderbrekings punten bevat of een opdracht die Break Point-objecten (bijvoorbeeld) ophaalt `Get-PSBreakpoint` .</span><span class="sxs-lookup"><span data-stu-id="9cb66-136">Provide a variable containing breakpoints or a command that gets breakpoint objects, such as `Get-PSBreakpoint`.</span></span> <span data-ttu-id="9cb66-137">U kunt ook pipet-objecten naar `Enable-PSBreakpoint` .</span><span class="sxs-lookup"><span data-stu-id="9cb66-137">You can also pipe breakpoint objects to `Enable-PSBreakpoint`.</span></span>

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

### <span data-ttu-id="9cb66-138">-Id</span><span class="sxs-lookup"><span data-stu-id="9cb66-138">-Id</span></span>

<span data-ttu-id="9cb66-139">Hiermee geeft u de **id-** nummers op van de onderbrekings punten die moeten worden ingeschakeld.</span><span class="sxs-lookup"><span data-stu-id="9cb66-139">Specifies the **Id** numbers of the breakpoints to enable.</span></span> <span data-ttu-id="9cb66-140">De standaard waarde is alle onderbrekings punten.</span><span class="sxs-lookup"><span data-stu-id="9cb66-140">The default value is all breakpoints.</span></span>
<span data-ttu-id="9cb66-141">Geef de **id** op per getal of in een variabele.</span><span class="sxs-lookup"><span data-stu-id="9cb66-141">Provide the **Id** by number or in a variable.</span></span> <span data-ttu-id="9cb66-142">U kunt geen **id-** nummers door sluizen naar `Enable-PSBreakpoint` .</span><span class="sxs-lookup"><span data-stu-id="9cb66-142">You can't pipe **Id** numbers to `Enable-PSBreakpoint`.</span></span> <span data-ttu-id="9cb66-143">Als u de **id** van een onderbrekings punt wilt zoeken, gebruikt u de `Get-PSBreakpoint` cmdlet.</span><span class="sxs-lookup"><span data-stu-id="9cb66-143">To find the **Id** of a breakpoint, use the `Get-PSBreakpoint` cmdlet.</span></span>

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

### <span data-ttu-id="9cb66-144">-PassThru</span><span class="sxs-lookup"><span data-stu-id="9cb66-144">-PassThru</span></span>

<span data-ttu-id="9cb66-145">Retourneert een object dat het onderbrekings punt vertegenwoordigt dat wordt ingeschakeld.</span><span class="sxs-lookup"><span data-stu-id="9cb66-145">Returns an object representing the breakpoint being enabled.</span></span> <span data-ttu-id="9cb66-146">Deze cmdlet genereert standaard geen uitvoer.</span><span class="sxs-lookup"><span data-stu-id="9cb66-146">By default, this cmdlet doesn't generate any output.</span></span>

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

### <span data-ttu-id="9cb66-147">-Confirm</span><span class="sxs-lookup"><span data-stu-id="9cb66-147">-Confirm</span></span>

<span data-ttu-id="9cb66-148">Hiermee wordt u gevraagd om bevestiging voordat u de cmdlet uitvoert.</span><span class="sxs-lookup"><span data-stu-id="9cb66-148">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="9cb66-149">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="9cb66-149">-WhatIf</span></span>

<span data-ttu-id="9cb66-150">Hiermee wordt weergegeven wat er zou gebeuren als u de cmdlet uitvoert.</span><span class="sxs-lookup"><span data-stu-id="9cb66-150">Shows what would happen if the cmdlet runs.</span></span> <span data-ttu-id="9cb66-151">De cmdlet wordt niet uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="9cb66-151">The cmdlet isn't run.</span></span>

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

### <span data-ttu-id="9cb66-152">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="9cb66-152">CommonParameters</span></span>

<span data-ttu-id="9cb66-153">Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="9cb66-153">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="9cb66-154">Zie [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="9cb66-154">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="9cb66-155">INVOER</span><span class="sxs-lookup"><span data-stu-id="9cb66-155">INPUTS</span></span>

### <span data-ttu-id="9cb66-156">System. Management. Automation. Break Point</span><span class="sxs-lookup"><span data-stu-id="9cb66-156">System.Management.Automation.Breakpoint</span></span>

<span data-ttu-id="9cb66-157">U kunt een onderbrekings punt object door sluizen naar `Enable-PSBreakpoint` .</span><span class="sxs-lookup"><span data-stu-id="9cb66-157">You can pipe a breakpoint object to `Enable-PSBreakpoint`.</span></span>

## <span data-ttu-id="9cb66-158">UITVOER</span><span class="sxs-lookup"><span data-stu-id="9cb66-158">OUTPUTS</span></span>

### <span data-ttu-id="9cb66-159">Geen of System. Management. Automation. Break Point</span><span class="sxs-lookup"><span data-stu-id="9cb66-159">None or System.Management.Automation.Breakpoint</span></span>

<span data-ttu-id="9cb66-160">Wanneer u de para meter **PassThru** gebruikt, `Enable-PSBreakpoint` retourneert een Break Point-object dat de ingeschakelde onderbrekings punt vertegenwoordigt.</span><span class="sxs-lookup"><span data-stu-id="9cb66-160">When you use the **PassThru** parameter, `Enable-PSBreakpoint` returns a breakpoint object that represents that breakpoint that was enabled.</span></span> <span data-ttu-id="9cb66-161">Anders wordt met deze cmdlet geen uitvoer gegenereerd.</span><span class="sxs-lookup"><span data-stu-id="9cb66-161">Otherwise, this cmdlet doesn't generate any output.</span></span>

## <span data-ttu-id="9cb66-162">OPMERKINGEN</span><span class="sxs-lookup"><span data-stu-id="9cb66-162">NOTES</span></span>

- <span data-ttu-id="9cb66-163">De `Enable-PSBreakpoint` cmdlet genereert geen fout als u probeert een onderbrekings punt in te scha kelen dat al is ingeschakeld.</span><span class="sxs-lookup"><span data-stu-id="9cb66-163">The `Enable-PSBreakpoint` cmdlet doesn't generate an error if you try to enable a breakpoint that is already enabled.</span></span> <span data-ttu-id="9cb66-164">Zo kunt u alle onderbrekings punten zonder fouten inschakelen, zelfs wanneer er slechts enkele zijn uitgeschakeld.</span><span class="sxs-lookup"><span data-stu-id="9cb66-164">As such, you can enable all breakpoints without error, even when only a few are disabled.</span></span>

- <span data-ttu-id="9cb66-165">Onderbrekings punten worden ingeschakeld wanneer u deze maakt met behulp van de- `Set-PSBreakpoint` cmdlet.</span><span class="sxs-lookup"><span data-stu-id="9cb66-165">Breakpoints are enabled when you create them by using the `Set-PSBreakpoint` cmdlet.</span></span> <span data-ttu-id="9cb66-166">U hoeft geen nieuw gemaakte onderbrekings punten in te scha kelen.</span><span class="sxs-lookup"><span data-stu-id="9cb66-166">You don't need to enable newly created breakpoints.</span></span>

## <span data-ttu-id="9cb66-167">GERELATEERDE KOPPELINGEN</span><span class="sxs-lookup"><span data-stu-id="9cb66-167">RELATED LINKS</span></span>

[<span data-ttu-id="9cb66-168">Disable-PSBreakpoint</span><span class="sxs-lookup"><span data-stu-id="9cb66-168">Disable-PSBreakpoint</span></span>](Disable-PSBreakpoint.md)

[<span data-ttu-id="9cb66-169">Get-PSBreakpoint</span><span class="sxs-lookup"><span data-stu-id="9cb66-169">Get-PSBreakpoint</span></span>](Get-PSBreakpoint.md)

[<span data-ttu-id="9cb66-170">Get-PSCallStack</span><span class="sxs-lookup"><span data-stu-id="9cb66-170">Get-PSCallStack</span></span>](Get-PSCallStack.md)

[<span data-ttu-id="9cb66-171">Remove-PSBreakpoint</span><span class="sxs-lookup"><span data-stu-id="9cb66-171">Remove-PSBreakpoint</span></span>](Remove-PSBreakpoint.md)

[<span data-ttu-id="9cb66-172">Set-PSBreakpoint</span><span class="sxs-lookup"><span data-stu-id="9cb66-172">Set-PSBreakpoint</span></span>](Set-PSBreakpoint.md)

