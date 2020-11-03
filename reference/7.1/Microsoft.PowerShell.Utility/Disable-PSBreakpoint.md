---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/disable-psbreakpoint?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Disable-PSBreakpoint
ms.openlocfilehash: 2f89be6b2ae9973b060a8562b5815b4e44b56ad8
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/07/2020
ms.locfileid: "93250904"
---
# <span data-ttu-id="9ad3d-103">Disable-PSBreakpoint</span><span class="sxs-lookup"><span data-stu-id="9ad3d-103">Disable-PSBreakpoint</span></span>

## <span data-ttu-id="9ad3d-104">SAMENVATTING</span><span class="sxs-lookup"><span data-stu-id="9ad3d-104">SYNOPSIS</span></span>
<span data-ttu-id="9ad3d-105">Hiermee schakelt u de onderbrekings punten in de huidige console uit.</span><span class="sxs-lookup"><span data-stu-id="9ad3d-105">Disables the breakpoints in the current console.</span></span>

## <span data-ttu-id="9ad3d-106">SYNTAXIS</span><span class="sxs-lookup"><span data-stu-id="9ad3d-106">SYNTAX</span></span>

### <span data-ttu-id="9ad3d-107">Onderbrekings punt (standaard)</span><span class="sxs-lookup"><span data-stu-id="9ad3d-107">Breakpoint (Default)</span></span>

```
Disable-PSBreakpoint [-PassThru] [-Breakpoint] <Breakpoint[]> [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="9ad3d-108">Id</span><span class="sxs-lookup"><span data-stu-id="9ad3d-108">Id</span></span>

```
Disable-PSBreakpoint [-PassThru] [-Id] <Int32[]> [-WhatIf] [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="9ad3d-109">BESCHRIJVING</span><span class="sxs-lookup"><span data-stu-id="9ad3d-109">DESCRIPTION</span></span>

<span data-ttu-id="9ad3d-110">Met de cmdlet **Disable-PSBreakpoint** worden onderbrekings punten uitgeschakeld. Dit zorgt ervoor dat ze niet worden weer bereikt wanneer het script wordt uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="9ad3d-110">The **Disable-PSBreakpoint** cmdlet disables breakpoints, which assures that they are not hit when the script runs.</span></span>
<span data-ttu-id="9ad3d-111">U kunt deze gebruiken om alle onderbrekings punten uit te scha kelen of u kunt onderbrekings punten opgeven door Break Point-objecten of onderbrekings punt-Id's in te dienen.</span><span class="sxs-lookup"><span data-stu-id="9ad3d-111">You can use it to disable all breakpoints, or you can specify breakpoints by submitting breakpoint objects or breakpoint IDs.</span></span>

<span data-ttu-id="9ad3d-112">Technisch gesp roken wijzigt deze cmdlet de waarde van de eigenschap Enabled van een onderbrekings punt-object in ONWAAR.</span><span class="sxs-lookup"><span data-stu-id="9ad3d-112">Technically, this cmdlet changes the value of the Enabled property of a breakpoint object to False.</span></span>
<span data-ttu-id="9ad3d-113">Als u een onderbrekings punt opnieuw wilt inschakelen, gebruikt u de cmdlet Enable-PSBreakpoint.</span><span class="sxs-lookup"><span data-stu-id="9ad3d-113">To re-enable a breakpoint, use the Enable-PSBreakpoint cmdlet.</span></span>
<span data-ttu-id="9ad3d-114">Onderbrekings punten worden standaard ingeschakeld wanneer u deze maakt met behulp van de cmdlet Set-PSBreakpoint.</span><span class="sxs-lookup"><span data-stu-id="9ad3d-114">Breakpoints are enabled by default when you create them by using the Set-PSBreakpoint cmdlet.</span></span>

<span data-ttu-id="9ad3d-115">Een onderbrekings punt is een Point in een script waar de uitvoering tijdelijk wordt gestopt zodat u de instructies in het script kunt onderzoeken.</span><span class="sxs-lookup"><span data-stu-id="9ad3d-115">A breakpoint is a point in a script where execution stops temporarily so that you can examine the instructions in the script.</span></span>
<span data-ttu-id="9ad3d-116">**Disable-PSBreakpoint** is een van de verschillende cmdlets die zijn ontworpen voor het opsporen van fouten in Power shell-scripts.</span><span class="sxs-lookup"><span data-stu-id="9ad3d-116">**Disable-PSBreakpoint** is one of several cmdlets designed for debugging PowerShell scripts.</span></span>
<span data-ttu-id="9ad3d-117">Zie about_Debuggers voor meer informatie over de Power Shell-fout opsporing.</span><span class="sxs-lookup"><span data-stu-id="9ad3d-117">For more information about the PowerShell debugger, see about_Debuggers.</span></span>

## <span data-ttu-id="9ad3d-118">VOORBEELDEN</span><span class="sxs-lookup"><span data-stu-id="9ad3d-118">EXAMPLES</span></span>

### <span data-ttu-id="9ad3d-119">Voor beeld 1: een onderbrekings punt instellen en deze uitschakelen</span><span class="sxs-lookup"><span data-stu-id="9ad3d-119">Example 1: Set a breakpoint and disable it</span></span>

```
PS C:\> $B = Set-PSBreakpoint -Script "sample.ps1" -Variable "name"
PS C:\> $B | Disable-PSBreakpoint
```

<span data-ttu-id="9ad3d-120">Met deze opdrachten wordt een nieuw gemaakt onderbrekings punt uitgeschakeld.</span><span class="sxs-lookup"><span data-stu-id="9ad3d-120">These commands disable a newly-created breakpoint.</span></span>

<span data-ttu-id="9ad3d-121">De eerste opdracht gebruikt de cmdlet Set-PSBreakpoint om een onderbrekings punt te maken op de *naam* variabele in het Sample.ps1 script.</span><span class="sxs-lookup"><span data-stu-id="9ad3d-121">The first command uses the Set-PSBreakpoint cmdlet to create a breakpoint on the *Name* variable in the Sample.ps1 script.</span></span>
<span data-ttu-id="9ad3d-122">Vervolgens wordt het object onderbrekings punt opgeslagen in de variabele $B.</span><span class="sxs-lookup"><span data-stu-id="9ad3d-122">Then, it saves the breakpoint object in the $B variable.</span></span>

<span data-ttu-id="9ad3d-123">De tweede opdracht maakt gebruik van de cmdlet **Disable-PSBreakpoint** om het nieuwe onderbrekings punt uit te scha kelen.</span><span class="sxs-lookup"><span data-stu-id="9ad3d-123">The second command uses the **Disable-PSBreakpoint** cmdlet to disable the new breakpoint.</span></span>
<span data-ttu-id="9ad3d-124">Er wordt een pijplijn operator (|) gebruikt om het Break Point-object in $B te verzenden naar de cmdlet **Disable-PSBreakpoint** .</span><span class="sxs-lookup"><span data-stu-id="9ad3d-124">It uses a pipeline operator (|) to send the breakpoint object in $B to the **Disable-PSBreakpoint** cmdlet.</span></span>

<span data-ttu-id="9ad3d-125">Als gevolg van deze opdracht is de waarde van de eigenschap ingeschakeld van het object onderbrekings punt in $B onwaar.</span><span class="sxs-lookup"><span data-stu-id="9ad3d-125">As a result of this command, the value of the Enabled property of the breakpoint object in $B is False.</span></span>

### <span data-ttu-id="9ad3d-126">Voor beeld 2: een onderbrekings punt uitschakelen</span><span class="sxs-lookup"><span data-stu-id="9ad3d-126">Example 2: Disable a breakpoint</span></span>

```
PS C:\> Disable-PSBreakpoint -Id 0
```

<span data-ttu-id="9ad3d-127">Met deze opdracht wordt het onderbrekings punt met onderbrekings punt-ID 0 uitgeschakeld.</span><span class="sxs-lookup"><span data-stu-id="9ad3d-127">This command disables the breakpoint with breakpoint ID 0.</span></span>

### <span data-ttu-id="9ad3d-128">Voor beeld 3: een uitgeschakeld onderbrekings punt maken</span><span class="sxs-lookup"><span data-stu-id="9ad3d-128">Example 3: Create a disabled breakpoint</span></span>

```
PS C:\> Disable-PSBreakpoint -Breakpoint ($B = Set-PSBreakpoint -Script "sample.ps1" -Line 5)
PS C:\> $B
```

<span data-ttu-id="9ad3d-129">Met deze opdracht maakt u een nieuw onderbrekings punt dat is uitgeschakeld totdat u het inschakelt.</span><span class="sxs-lookup"><span data-stu-id="9ad3d-129">This command creates a new breakpoint that is disabled until you enable it.</span></span>

<span data-ttu-id="9ad3d-130">De cmdlet **Disable-PSBreakpoint** wordt gebruikt om het onderbrekings punt uit te scha kelen.</span><span class="sxs-lookup"><span data-stu-id="9ad3d-130">It uses the **Disable-PSBreakpoint** cmdlet to disable the breakpoint.</span></span>
<span data-ttu-id="9ad3d-131">De waarde van de para meter *Break Point* is een Set-PSBreakpoint opdracht waarmee een nieuw onderbrekings punt wordt ingesteld, een onderbrekings punt object wordt gegenereerd en het object wordt opgeslagen in de variabele $B.</span><span class="sxs-lookup"><span data-stu-id="9ad3d-131">The value of the *Breakpoint* parameter is a Set-PSBreakpoint command that sets a new breakpoint, generates a breakpoint object, and saves the object in the $B variable.</span></span>

<span data-ttu-id="9ad3d-132">Cmdlet-para meters die objecten als waarden aannemen, kunnen een variabele accepteren die het object bevat of een opdracht waarmee het object wordt opgehaald of gegenereerd.</span><span class="sxs-lookup"><span data-stu-id="9ad3d-132">Cmdlet parameters that take objects as their values can accept a variable that contains the object or a command that gets or generates the object.</span></span>
<span data-ttu-id="9ad3d-133">In dit geval, omdat **set-PSBreakpoint** een Break Point-object genereert, kan worden gebruikt als de waarde van de para meter *Break Point* .</span><span class="sxs-lookup"><span data-stu-id="9ad3d-133">In this case, because **Set-PSBreakpoint** generates a breakpoint object, it can be used as the value of the *Breakpoint* parameter.</span></span>

<span data-ttu-id="9ad3d-134">Met de tweede opdracht wordt het Break Point-object weer gegeven in de waarde van de variabele $B.</span><span class="sxs-lookup"><span data-stu-id="9ad3d-134">The second command displays the breakpoint object in the value of the $B variable.</span></span>

### <span data-ttu-id="9ad3d-135">Voor beeld 4: alle onderbrekings punten in de huidige console uitschakelen</span><span class="sxs-lookup"><span data-stu-id="9ad3d-135">Example 4: Disable all breakpoints in the current console</span></span>

```
PS C:\> Get-PSBreakpoint | Disable-PSBreakpoint
```

<span data-ttu-id="9ad3d-136">Met deze opdracht worden alle onderbrekings punten in de huidige console uitgeschakeld.</span><span class="sxs-lookup"><span data-stu-id="9ad3d-136">This command disables all breakpoints in the current console.</span></span>
<span data-ttu-id="9ad3d-137">U kunt deze opdracht afkorten als: "GBP | dbp".</span><span class="sxs-lookup"><span data-stu-id="9ad3d-137">You can abbreviate this command as: "gbp | dbp".</span></span>

## <span data-ttu-id="9ad3d-138">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="9ad3d-138">PARAMETERS</span></span>

### <span data-ttu-id="9ad3d-139">-Onderbrekings punt</span><span class="sxs-lookup"><span data-stu-id="9ad3d-139">-Breakpoint</span></span>

<span data-ttu-id="9ad3d-140">Hiermee geeft u de onderbrekings punten die moeten worden uitgeschakeld.</span><span class="sxs-lookup"><span data-stu-id="9ad3d-140">Specifies the breakpoints to disable.</span></span>
<span data-ttu-id="9ad3d-141">Voer een variabele in die Break Point-objecten bevat of een opdracht die Break Point-objecten, zoals een Get-PSBreakpoint opdracht.</span><span class="sxs-lookup"><span data-stu-id="9ad3d-141">Enter a variable that contains breakpoint objects or a command that gets breakpoint objects, such as a Get-PSBreakpoint command.</span></span>
<span data-ttu-id="9ad3d-142">U kunt ook pipet-objecten naar de cmdlet **Disable-PSBreakpoint** .</span><span class="sxs-lookup"><span data-stu-id="9ad3d-142">You can also pipe breakpoint objects to the **Disable-PSBreakpoint** cmdlet.</span></span>

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

### <span data-ttu-id="9ad3d-143">-Id</span><span class="sxs-lookup"><span data-stu-id="9ad3d-143">-Id</span></span>

<span data-ttu-id="9ad3d-144">Hiermee worden de onderbrekings punten met de opgegeven onderbrekings punt-Id's uitgeschakeld.</span><span class="sxs-lookup"><span data-stu-id="9ad3d-144">Disables the breakpoints with the specified breakpoint IDs.</span></span>
<span data-ttu-id="9ad3d-145">Voer de Id's of een variabele in die de Id's bevat.</span><span class="sxs-lookup"><span data-stu-id="9ad3d-145">Enter the IDs or a variable that contains the IDs.</span></span>
<span data-ttu-id="9ad3d-146">U kunt geen pipe-Id's naar **Disable-PSBreakpoint**.</span><span class="sxs-lookup"><span data-stu-id="9ad3d-146">You cannot pipe IDs to **Disable-PSBreakpoint**.</span></span>

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

### <span data-ttu-id="9ad3d-147">-PassThru</span><span class="sxs-lookup"><span data-stu-id="9ad3d-147">-PassThru</span></span>

<span data-ttu-id="9ad3d-148">Retourneert een object dat de ingeschakelde onderbrekings punten vertegenwoordigt.</span><span class="sxs-lookup"><span data-stu-id="9ad3d-148">Returns an object representing the enabled breakpoints.</span></span>
<span data-ttu-id="9ad3d-149">Deze cmdlet genereert standaard geen uitvoer.</span><span class="sxs-lookup"><span data-stu-id="9ad3d-149">By default, this cmdlet does not generate any output.</span></span>

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

### <span data-ttu-id="9ad3d-150">-Confirm</span><span class="sxs-lookup"><span data-stu-id="9ad3d-150">-Confirm</span></span>

<span data-ttu-id="9ad3d-151">Hiermee wordt u gevraagd om bevestiging voordat u de cmdlet uitvoert.</span><span class="sxs-lookup"><span data-stu-id="9ad3d-151">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="9ad3d-152">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="9ad3d-152">-WhatIf</span></span>

<span data-ttu-id="9ad3d-153">Hiermee wordt weergegeven wat er zou gebeuren als u de cmdlet uitvoert.</span><span class="sxs-lookup"><span data-stu-id="9ad3d-153">Shows what would happen if the cmdlet runs.</span></span>
<span data-ttu-id="9ad3d-154">De cmdlet wordt niet uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="9ad3d-154">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="9ad3d-155">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="9ad3d-155">CommonParameters</span></span>

<span data-ttu-id="9ad3d-156">Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="9ad3d-156">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="9ad3d-157">Zie [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="9ad3d-157">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="9ad3d-158">INVOER</span><span class="sxs-lookup"><span data-stu-id="9ad3d-158">INPUTS</span></span>

### <span data-ttu-id="9ad3d-159">System. Management. Automation. Break Point</span><span class="sxs-lookup"><span data-stu-id="9ad3d-159">System.Management.Automation.Breakpoint</span></span>

<span data-ttu-id="9ad3d-160">U kunt een Break Point-object door sluizen naar **Disable-PSBreakpoint**.</span><span class="sxs-lookup"><span data-stu-id="9ad3d-160">You can pipe a breakpoint object to **Disable-PSBreakpoint**.</span></span>

## <span data-ttu-id="9ad3d-161">UITVOER</span><span class="sxs-lookup"><span data-stu-id="9ad3d-161">OUTPUTS</span></span>

### <span data-ttu-id="9ad3d-162">Geen of System. Management. Automation. Break Point</span><span class="sxs-lookup"><span data-stu-id="9ad3d-162">None or System.Management.Automation.Breakpoint</span></span>

<span data-ttu-id="9ad3d-163">Wanneer u de para meter *PassThru* gebruikt, retourneert **Disable-PSBreakpoint** een object dat het uitgeschakelde onderbrekings punt vertegenwoordigt.</span><span class="sxs-lookup"><span data-stu-id="9ad3d-163">When you use the *PassThru* parameter, **Disable-PSBreakpoint** returns an object that represents the disabled breakpoint.</span></span>
<span data-ttu-id="9ad3d-164">Anders wordt met deze cmdlet geen uitvoer gegenereerd.</span><span class="sxs-lookup"><span data-stu-id="9ad3d-164">Otherwise, this cmdlet does not generate any output.</span></span>

## <span data-ttu-id="9ad3d-165">OPMERKINGEN</span><span class="sxs-lookup"><span data-stu-id="9ad3d-165">NOTES</span></span>

## <span data-ttu-id="9ad3d-166">GERELATEERDE KOPPELINGEN</span><span class="sxs-lookup"><span data-stu-id="9ad3d-166">RELATED LINKS</span></span>

[<span data-ttu-id="9ad3d-167">Enable-PSBreakpoint</span><span class="sxs-lookup"><span data-stu-id="9ad3d-167">Enable-PSBreakpoint</span></span>](Enable-PSBreakpoint.md)

[<span data-ttu-id="9ad3d-168">Get-PSBreakpoint</span><span class="sxs-lookup"><span data-stu-id="9ad3d-168">Get-PSBreakpoint</span></span>](Get-PSBreakpoint.md)

[<span data-ttu-id="9ad3d-169">Get-PSCallStack</span><span class="sxs-lookup"><span data-stu-id="9ad3d-169">Get-PSCallStack</span></span>](Get-PSCallStack.md)

[<span data-ttu-id="9ad3d-170">Remove-PSBreakpoint</span><span class="sxs-lookup"><span data-stu-id="9ad3d-170">Remove-PSBreakpoint</span></span>](Remove-PSBreakpoint.md)

[<span data-ttu-id="9ad3d-171">Set-PSBreakpoint</span><span class="sxs-lookup"><span data-stu-id="9ad3d-171">Set-PSBreakpoint</span></span>](Set-PSBreakpoint.md)

