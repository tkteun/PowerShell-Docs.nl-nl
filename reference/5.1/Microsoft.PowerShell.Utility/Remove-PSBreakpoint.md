---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/remove-psbreakpoint?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Remove-PSBreakpoint
ms.openlocfilehash: b12913cd10c2c505322c1f922a05ecc98987e830
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/07/2020
ms.locfileid: "93250384"
---
# <span data-ttu-id="c6514-103">Remove-PSBreakpoint</span><span class="sxs-lookup"><span data-stu-id="c6514-103">Remove-PSBreakpoint</span></span>

## <span data-ttu-id="c6514-104">SAMENVATTING</span><span class="sxs-lookup"><span data-stu-id="c6514-104">SYNOPSIS</span></span>
<span data-ttu-id="c6514-105">Hiermee worden onderbrekings punten uit de huidige console verwijderd.</span><span class="sxs-lookup"><span data-stu-id="c6514-105">Deletes breakpoints from the current console.</span></span>

## <span data-ttu-id="c6514-106">SYNTAXIS</span><span class="sxs-lookup"><span data-stu-id="c6514-106">SYNTAX</span></span>

### <span data-ttu-id="c6514-107">Onderbrekings punt (standaard)</span><span class="sxs-lookup"><span data-stu-id="c6514-107">Breakpoint (Default)</span></span>

```
Remove-PSBreakpoint [-Breakpoint] <Breakpoint[]> [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="c6514-108">Id</span><span class="sxs-lookup"><span data-stu-id="c6514-108">Id</span></span>

```
Remove-PSBreakpoint [-Id] <Int32[]> [-WhatIf] [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="c6514-109">BESCHRIJVING</span><span class="sxs-lookup"><span data-stu-id="c6514-109">DESCRIPTION</span></span>
<span data-ttu-id="c6514-110">Met de cmdlet **Remove-PSBreakpoint** wordt een onderbrekings punt verwijderd.</span><span class="sxs-lookup"><span data-stu-id="c6514-110">The **Remove-PSBreakpoint** cmdlet deletes a breakpoint.</span></span>
<span data-ttu-id="c6514-111">Voer een onderbrekings punt object of een onderbrekings punt-ID in.</span><span class="sxs-lookup"><span data-stu-id="c6514-111">Enter a breakpoint object or a breakpoint ID.</span></span>

<span data-ttu-id="c6514-112">Wanneer u een onderbrekings punt verwijdert, is het object onderbrekings punt niet meer beschikbaar of werkt het niet meer.</span><span class="sxs-lookup"><span data-stu-id="c6514-112">When you remove a breakpoint, the breakpoint object is no longer available or functional.</span></span>
<span data-ttu-id="c6514-113">Als u een onderbrekings punt object in een variabele hebt opgeslagen, bestaat de verwijzing nog steeds, maar werkt het onderbrekings punt niet.</span><span class="sxs-lookup"><span data-stu-id="c6514-113">If you have saved a breakpoint object in a variable, the reference still exists, but the breakpoint does not function.</span></span>

<span data-ttu-id="c6514-114">**Remove-PSBreakpoint** is een van de verschillende cmdlets die zijn ontworpen voor het opsporen van fouten in Windows Power shell-scripts.</span><span class="sxs-lookup"><span data-stu-id="c6514-114">**Remove-PSBreakpoint** is one of several cmdlets designed for debugging Windows PowerShell scripts.</span></span>
<span data-ttu-id="c6514-115">Zie about_Debuggers voor meer informatie over de Windows Power Shell-fout opsporing.</span><span class="sxs-lookup"><span data-stu-id="c6514-115">For more information about the Windows PowerShell debugger, see about_Debuggers.</span></span>

## <span data-ttu-id="c6514-116">VOORBEELDEN</span><span class="sxs-lookup"><span data-stu-id="c6514-116">EXAMPLES</span></span>

### <span data-ttu-id="c6514-117">Voor beeld 1: alle onderbrekings punten verwijderen</span><span class="sxs-lookup"><span data-stu-id="c6514-117">Example 1: Remove all breakpoints</span></span>

```
PS C:\> Get-PSBreakpoint | Remove-PSBreakpoint
```

<span data-ttu-id="c6514-118">Met deze opdracht worden alle onderbrekings punten in de huidige console verwijderd.</span><span class="sxs-lookup"><span data-stu-id="c6514-118">This command deletes all of the breakpoints in the current console.</span></span>

### <span data-ttu-id="c6514-119">Voor beeld 2: een opgegeven onderbrekings punt verwijderen</span><span class="sxs-lookup"><span data-stu-id="c6514-119">Example 2: Remove a specified breakpoint</span></span>

```
PS C:\> $B = Set-PSBreakpoint -Script "sample.ps1" -Variable "Name"
PS C:\> $B | Remove-PSBreakpoint
```

<span data-ttu-id="c6514-120">Met deze opdracht wordt een onderbrekings punt verwijderd.</span><span class="sxs-lookup"><span data-stu-id="c6514-120">This command deletes a breakpoint.</span></span>

<span data-ttu-id="c6514-121">De eerste opdracht gebruikt de cmdlet Set-PSBreakpoint om een onderbrekings punt te maken op de naam variabele in het Sample.ps1 script.</span><span class="sxs-lookup"><span data-stu-id="c6514-121">The first command uses the Set-PSBreakpoint cmdlet to create a breakpoint on the Name variable in the Sample.ps1 script.</span></span>
<span data-ttu-id="c6514-122">Vervolgens wordt het object onderbrekings punt opgeslagen in de variabele $B.</span><span class="sxs-lookup"><span data-stu-id="c6514-122">Then, it saves the breakpoint object in the $B variable.</span></span>

<span data-ttu-id="c6514-123">De tweede opdracht maakt gebruik van de cmdlet **Remove-PSBreakpoint** om het nieuwe onderbrekings punt te verwijderen.</span><span class="sxs-lookup"><span data-stu-id="c6514-123">The second command uses the **Remove-PSBreakpoint** cmdlet to delete the new breakpoint.</span></span>
<span data-ttu-id="c6514-124">Er wordt een pijplijn operator (|) gebruikt om het Break Point-object in de $B variabele te verzenden naar de cmdlet **Remove-PSBreakpoint** .</span><span class="sxs-lookup"><span data-stu-id="c6514-124">It uses a pipeline operator (|) to send the breakpoint object in the $B variable to the **Remove-PSBreakpoint** cmdlet.</span></span>

<span data-ttu-id="c6514-125">Als gevolg van deze opdracht, als u het script uitvoert, wordt het uitgevoerd om te worden voltooid zonder te stoppen.</span><span class="sxs-lookup"><span data-stu-id="c6514-125">As a result of this command, if you run the script, it runs to completion without stopping.</span></span>
<span data-ttu-id="c6514-126">De cmdlet **Get-PSBreakpoint** retourneert dit onderbrekings punt ook niet.</span><span class="sxs-lookup"><span data-stu-id="c6514-126">Also, the **Get-PSBreakpoint** cmdlet does not return this breakpoint.</span></span>

### <span data-ttu-id="c6514-127">Voor beeld 3: een onderbrekings punt verwijderen op basis van ID</span><span class="sxs-lookup"><span data-stu-id="c6514-127">Example 3: Remove a breakpoint by ID</span></span>

```
PS C:\> Remove-PSBreakpoint -Id 2
```

<span data-ttu-id="c6514-128">Met deze opdracht wordt het onderbrekings punt met onderbrekings punt-ID 2 verwijderd.</span><span class="sxs-lookup"><span data-stu-id="c6514-128">This command deletes the breakpoint with breakpoint ID 2.</span></span>

### <span data-ttu-id="c6514-129">Voor beeld 4: een functie gebruiken om alle onderbrekings punten te verwijderen</span><span class="sxs-lookup"><span data-stu-id="c6514-129">Example 4: Use a function to remove all breakpoints</span></span>

```
PS C:\> function del-psb { get-psbreakpoint | remove-psbreakpoint }
```

<span data-ttu-id="c6514-130">Met deze eenvoudige functie worden alle onderbrekings punten in de huidige console verwijderd.</span><span class="sxs-lookup"><span data-stu-id="c6514-130">This simple function deletes all of the breakpoints in the current console.</span></span>
<span data-ttu-id="c6514-131">De Get-PSBreakpoint cmdlet wordt gebruikt om de onderbrekings punten op te halen.</span><span class="sxs-lookup"><span data-stu-id="c6514-131">It uses the Get-PSBreakpoint cmdlet to get the breakpoints.</span></span>
<span data-ttu-id="c6514-132">Vervolgens wordt een pijplijn operator (|) gebruikt om de onderbrekings punten te verzenden naar de cmdlet **Remove-PSBreakpoint** , waarmee deze worden verwijderd.</span><span class="sxs-lookup"><span data-stu-id="c6514-132">Then, it uses a pipeline operator (|) to send the breakpoints to the **Remove-PSBreakpoint** cmdlet, which deletes them.</span></span>

<span data-ttu-id="c6514-133">Als gevolg hiervan kunt u `del-psb` in plaats van de langere opdracht typen.</span><span class="sxs-lookup"><span data-stu-id="c6514-133">As a result, you can type `del-psb` instead of the longer command.</span></span>

<span data-ttu-id="c6514-134">Als u de functie wilt opslaan, voegt u deze toe aan uw Windows Power shell-profiel.</span><span class="sxs-lookup"><span data-stu-id="c6514-134">To save the function, add it to your Windows PowerShell profile.</span></span>

## <span data-ttu-id="c6514-135">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="c6514-135">PARAMETERS</span></span>

### <span data-ttu-id="c6514-136">-Onderbrekings punt</span><span class="sxs-lookup"><span data-stu-id="c6514-136">-Breakpoint</span></span>
<span data-ttu-id="c6514-137">Hiermee geeft u de onderbrekings punten die moeten worden verwijderd.</span><span class="sxs-lookup"><span data-stu-id="c6514-137">Specifies the breakpoints to delete.</span></span>
<span data-ttu-id="c6514-138">Voer een variabele in die Break Point-objecten bevat of een opdracht die Break Point-objecten, zoals een **Get-PSBreakpoint-** opdracht, ontvangt.</span><span class="sxs-lookup"><span data-stu-id="c6514-138">Enter a variable that contains breakpoint objects or a command that gets breakpoint objects, such as a **Get-PSBreakpoint** command.</span></span>
<span data-ttu-id="c6514-139">U kunt ook pipet-objecten voor onderbrekingen voor **het verwijderen van-PSBreakpoint**.</span><span class="sxs-lookup"><span data-stu-id="c6514-139">You can also pipe breakpoint objects to **Remove-PSBreakpoint**.</span></span>

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

### <span data-ttu-id="c6514-140">-Id</span><span class="sxs-lookup"><span data-stu-id="c6514-140">-Id</span></span>
<span data-ttu-id="c6514-141">Hiermee geeft u onderbrekings punt-Id's op waarvoor deze cmdlet onderbrekings punten verwijdert.</span><span class="sxs-lookup"><span data-stu-id="c6514-141">Specifies breakpoint IDs for which this cmdlet deletes breakpoints.</span></span>

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

### <span data-ttu-id="c6514-142">-Confirm</span><span class="sxs-lookup"><span data-stu-id="c6514-142">-Confirm</span></span>
<span data-ttu-id="c6514-143">Hiermee wordt u gevraagd om bevestiging voordat u de cmdlet uitvoert.</span><span class="sxs-lookup"><span data-stu-id="c6514-143">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="c6514-144">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="c6514-144">-WhatIf</span></span>
<span data-ttu-id="c6514-145">Hiermee wordt weergegeven wat er zou gebeuren als u de cmdlet uitvoert.</span><span class="sxs-lookup"><span data-stu-id="c6514-145">Shows what would happen if the cmdlet runs.</span></span>
<span data-ttu-id="c6514-146">De cmdlet wordt niet uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="c6514-146">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="c6514-147">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="c6514-147">CommonParameters</span></span>
<span data-ttu-id="c6514-148">Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="c6514-148">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="c6514-149">Zie [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="c6514-149">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="c6514-150">INVOER</span><span class="sxs-lookup"><span data-stu-id="c6514-150">INPUTS</span></span>

### <span data-ttu-id="c6514-151">System. Management. Automation. Break Point</span><span class="sxs-lookup"><span data-stu-id="c6514-151">System.Management.Automation.Breakpoint</span></span>
<span data-ttu-id="c6514-152">U kunt **PSBreakpoint-** onderbrekings punten verwijderen.</span><span class="sxs-lookup"><span data-stu-id="c6514-152">You can pipe breakpoint objects to **Remove-PSBreakpoint**.</span></span>

## <span data-ttu-id="c6514-153">UITVOER</span><span class="sxs-lookup"><span data-stu-id="c6514-153">OUTPUTS</span></span>

### <span data-ttu-id="c6514-154">Geen</span><span class="sxs-lookup"><span data-stu-id="c6514-154">None</span></span>
<span data-ttu-id="c6514-155">De cmdlet genereert geen uitvoer.</span><span class="sxs-lookup"><span data-stu-id="c6514-155">The cmdlet does not generate any output.</span></span>

## <span data-ttu-id="c6514-156">OPMERKINGEN</span><span class="sxs-lookup"><span data-stu-id="c6514-156">NOTES</span></span>

## <span data-ttu-id="c6514-157">GERELATEERDE KOPPELINGEN</span><span class="sxs-lookup"><span data-stu-id="c6514-157">RELATED LINKS</span></span>

[<span data-ttu-id="c6514-158">Disable-PSBreakpoint</span><span class="sxs-lookup"><span data-stu-id="c6514-158">Disable-PSBreakpoint</span></span>](Disable-PSBreakpoint.md)

[<span data-ttu-id="c6514-159">Enable-PSBreakpoint</span><span class="sxs-lookup"><span data-stu-id="c6514-159">Enable-PSBreakpoint</span></span>](Enable-PSBreakpoint.md)

[<span data-ttu-id="c6514-160">Get-PSBreakpoint</span><span class="sxs-lookup"><span data-stu-id="c6514-160">Get-PSBreakpoint</span></span>](Get-PSBreakpoint.md)

[<span data-ttu-id="c6514-161">Get-PSCallStack</span><span class="sxs-lookup"><span data-stu-id="c6514-161">Get-PSCallStack</span></span>](Get-PSCallStack.md)

[<span data-ttu-id="c6514-162">Set-PSBreakpoint</span><span class="sxs-lookup"><span data-stu-id="c6514-162">Set-PSBreakpoint</span></span>](Set-PSBreakpoint.md)
