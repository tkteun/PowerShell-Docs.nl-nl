---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/remove-psbreakpoint?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Remove-PSBreakpoint
ms.openlocfilehash: a56b9041c0ae70def7df619f2a4d265cb631fe7b
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 11/17/2020
ms.locfileid: "94704752"
---
# <span data-ttu-id="7e7e2-102">Remove-PSBreakpoint</span><span class="sxs-lookup"><span data-stu-id="7e7e2-102">Remove-PSBreakpoint</span></span>

## <span data-ttu-id="7e7e2-103">SAMENVATTING</span><span class="sxs-lookup"><span data-stu-id="7e7e2-103">SYNOPSIS</span></span>
<span data-ttu-id="7e7e2-104">Hiermee worden onderbrekings punten uit de huidige console verwijderd.</span><span class="sxs-lookup"><span data-stu-id="7e7e2-104">Deletes breakpoints from the current console.</span></span>

## <span data-ttu-id="7e7e2-105">SYNTAXIS</span><span class="sxs-lookup"><span data-stu-id="7e7e2-105">SYNTAX</span></span>

### <span data-ttu-id="7e7e2-106">Onderbrekings punt (standaard)</span><span class="sxs-lookup"><span data-stu-id="7e7e2-106">Breakpoint (Default)</span></span>

```
Remove-PSBreakpoint [-Breakpoint] <Breakpoint[]> [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="7e7e2-107">Id</span><span class="sxs-lookup"><span data-stu-id="7e7e2-107">Id</span></span>

```
Remove-PSBreakpoint [-Id] <Int32[]> [-WhatIf] [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="7e7e2-108">BESCHRIJVING</span><span class="sxs-lookup"><span data-stu-id="7e7e2-108">DESCRIPTION</span></span>
<span data-ttu-id="7e7e2-109">Met de cmdlet **Remove-PSBreakpoint** wordt een onderbrekings punt verwijderd.</span><span class="sxs-lookup"><span data-stu-id="7e7e2-109">The **Remove-PSBreakpoint** cmdlet deletes a breakpoint.</span></span>
<span data-ttu-id="7e7e2-110">Voer een onderbrekings punt object of een onderbrekings punt-ID in.</span><span class="sxs-lookup"><span data-stu-id="7e7e2-110">Enter a breakpoint object or a breakpoint ID.</span></span>

<span data-ttu-id="7e7e2-111">Wanneer u een onderbrekings punt verwijdert, is het object onderbrekings punt niet meer beschikbaar of werkt het niet meer.</span><span class="sxs-lookup"><span data-stu-id="7e7e2-111">When you remove a breakpoint, the breakpoint object is no longer available or functional.</span></span>
<span data-ttu-id="7e7e2-112">Als u een onderbrekings punt object in een variabele hebt opgeslagen, bestaat de verwijzing nog steeds, maar werkt het onderbrekings punt niet.</span><span class="sxs-lookup"><span data-stu-id="7e7e2-112">If you have saved a breakpoint object in a variable, the reference still exists, but the breakpoint does not function.</span></span>

<span data-ttu-id="7e7e2-113">**Remove-PSBreakpoint** is een van de verschillende cmdlets die zijn ontworpen voor het opsporen van fouten in Power shell-scripts.</span><span class="sxs-lookup"><span data-stu-id="7e7e2-113">**Remove-PSBreakpoint** is one of several cmdlets designed for debugging PowerShell scripts.</span></span>
<span data-ttu-id="7e7e2-114">Zie about_Debuggers voor meer informatie over de Power Shell-fout opsporing.</span><span class="sxs-lookup"><span data-stu-id="7e7e2-114">For more information about the PowerShell debugger, see about_Debuggers.</span></span>

## <span data-ttu-id="7e7e2-115">VOORBEELDEN</span><span class="sxs-lookup"><span data-stu-id="7e7e2-115">EXAMPLES</span></span>

### <span data-ttu-id="7e7e2-116">Voor beeld 1: alle onderbrekings punten verwijderen</span><span class="sxs-lookup"><span data-stu-id="7e7e2-116">Example 1: Remove all breakpoints</span></span>

```
PS C:\> Get-PSBreakpoint | Remove-PSBreakpoint
```

<span data-ttu-id="7e7e2-117">Met deze opdracht worden alle onderbrekings punten in de huidige console verwijderd.</span><span class="sxs-lookup"><span data-stu-id="7e7e2-117">This command deletes all of the breakpoints in the current console.</span></span>

### <span data-ttu-id="7e7e2-118">Voor beeld 2: een opgegeven onderbrekings punt verwijderen</span><span class="sxs-lookup"><span data-stu-id="7e7e2-118">Example 2: Remove a specified breakpoint</span></span>

```
PS C:\> $B = Set-PSBreakpoint -Script "sample.ps1" -Variable "Name"
PS C:\> $B | Remove-PSBreakpoint
```

<span data-ttu-id="7e7e2-119">Met deze opdracht wordt een onderbrekings punt verwijderd.</span><span class="sxs-lookup"><span data-stu-id="7e7e2-119">This command deletes a breakpoint.</span></span>

<span data-ttu-id="7e7e2-120">De eerste opdracht gebruikt de cmdlet Set-PSBreakpoint om een onderbrekings punt te maken op de naam variabele in het Sample.ps1 script.</span><span class="sxs-lookup"><span data-stu-id="7e7e2-120">The first command uses the Set-PSBreakpoint cmdlet to create a breakpoint on the Name variable in the Sample.ps1 script.</span></span>
<span data-ttu-id="7e7e2-121">Vervolgens wordt het object onderbrekings punt opgeslagen in de variabele $B.</span><span class="sxs-lookup"><span data-stu-id="7e7e2-121">Then, it saves the breakpoint object in the $B variable.</span></span>

<span data-ttu-id="7e7e2-122">De tweede opdracht maakt gebruik van de cmdlet **Remove-PSBreakpoint** om het nieuwe onderbrekings punt te verwijderen.</span><span class="sxs-lookup"><span data-stu-id="7e7e2-122">The second command uses the **Remove-PSBreakpoint** cmdlet to delete the new breakpoint.</span></span>
<span data-ttu-id="7e7e2-123">Er wordt een pijplijn operator (|) gebruikt om het Break Point-object in de $B variabele te verzenden naar de cmdlet **Remove-PSBreakpoint** .</span><span class="sxs-lookup"><span data-stu-id="7e7e2-123">It uses a pipeline operator (|) to send the breakpoint object in the $B variable to the **Remove-PSBreakpoint** cmdlet.</span></span>

<span data-ttu-id="7e7e2-124">Als gevolg van deze opdracht, als u het script uitvoert, wordt het uitgevoerd om te worden voltooid zonder te stoppen.</span><span class="sxs-lookup"><span data-stu-id="7e7e2-124">As a result of this command, if you run the script, it runs to completion without stopping.</span></span>
<span data-ttu-id="7e7e2-125">De cmdlet **Get-PSBreakpoint** retourneert dit onderbrekings punt ook niet.</span><span class="sxs-lookup"><span data-stu-id="7e7e2-125">Also, the **Get-PSBreakpoint** cmdlet does not return this breakpoint.</span></span>

### <span data-ttu-id="7e7e2-126">Voor beeld 3: een onderbrekings punt verwijderen op basis van ID</span><span class="sxs-lookup"><span data-stu-id="7e7e2-126">Example 3: Remove a breakpoint by ID</span></span>

```
PS C:\> Remove-PSBreakpoint -Id 2
```

<span data-ttu-id="7e7e2-127">Met deze opdracht wordt het onderbrekings punt met onderbrekings punt-ID 2 verwijderd.</span><span class="sxs-lookup"><span data-stu-id="7e7e2-127">This command deletes the breakpoint with breakpoint ID 2.</span></span>

### <span data-ttu-id="7e7e2-128">Voor beeld 4: een functie gebruiken om alle onderbrekings punten te verwijderen</span><span class="sxs-lookup"><span data-stu-id="7e7e2-128">Example 4: Use a function to remove all breakpoints</span></span>

```
PS C:\> function del-psb { get-psbreakpoint | remove-psbreakpoint }
```

<span data-ttu-id="7e7e2-129">Met deze eenvoudige functie worden alle onderbrekings punten in de huidige console verwijderd.</span><span class="sxs-lookup"><span data-stu-id="7e7e2-129">This simple function deletes all of the breakpoints in the current console.</span></span>
<span data-ttu-id="7e7e2-130">De Get-PSBreakpoint cmdlet wordt gebruikt om de onderbrekings punten op te halen.</span><span class="sxs-lookup"><span data-stu-id="7e7e2-130">It uses the Get-PSBreakpoint cmdlet to get the breakpoints.</span></span>
<span data-ttu-id="7e7e2-131">Vervolgens wordt een pijplijn operator (|) gebruikt om de onderbrekings punten te verzenden naar de cmdlet **Remove-PSBreakpoint** , waarmee deze worden verwijderd.</span><span class="sxs-lookup"><span data-stu-id="7e7e2-131">Then, it uses a pipeline operator (|) to send the breakpoints to the **Remove-PSBreakpoint** cmdlet, which deletes them.</span></span>

<span data-ttu-id="7e7e2-132">Als gevolg hiervan kunt u `del-psb` in plaats van de langere opdracht typen.</span><span class="sxs-lookup"><span data-stu-id="7e7e2-132">As a result, you can type `del-psb` instead of the longer command.</span></span>

<span data-ttu-id="7e7e2-133">Als u de functie wilt opslaan, voegt u deze toe aan uw Power shell-profiel.</span><span class="sxs-lookup"><span data-stu-id="7e7e2-133">To save the function, add it to your PowerShell profile.</span></span>

## <span data-ttu-id="7e7e2-134">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="7e7e2-134">PARAMETERS</span></span>

### <span data-ttu-id="7e7e2-135">-Onderbrekings punt</span><span class="sxs-lookup"><span data-stu-id="7e7e2-135">-Breakpoint</span></span>
<span data-ttu-id="7e7e2-136">Hiermee geeft u de onderbrekings punten die moeten worden verwijderd.</span><span class="sxs-lookup"><span data-stu-id="7e7e2-136">Specifies the breakpoints to delete.</span></span>
<span data-ttu-id="7e7e2-137">Voer een variabele in die Break Point-objecten bevat of een opdracht die Break Point-objecten, zoals een **Get-PSBreakpoint-** opdracht, ontvangt.</span><span class="sxs-lookup"><span data-stu-id="7e7e2-137">Enter a variable that contains breakpoint objects or a command that gets breakpoint objects, such as a **Get-PSBreakpoint** command.</span></span>
<span data-ttu-id="7e7e2-138">U kunt ook pipet-objecten voor onderbrekingen voor **het verwijderen van-PSBreakpoint**.</span><span class="sxs-lookup"><span data-stu-id="7e7e2-138">You can also pipe breakpoint objects to **Remove-PSBreakpoint**.</span></span>

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

### <span data-ttu-id="7e7e2-139">-Id</span><span class="sxs-lookup"><span data-stu-id="7e7e2-139">-Id</span></span>
<span data-ttu-id="7e7e2-140">Hiermee geeft u onderbrekings punt-Id's op waarvoor deze cmdlet onderbrekings punten verwijdert.</span><span class="sxs-lookup"><span data-stu-id="7e7e2-140">Specifies breakpoint IDs for which this cmdlet deletes breakpoints.</span></span>

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

### <span data-ttu-id="7e7e2-141">-Confirm</span><span class="sxs-lookup"><span data-stu-id="7e7e2-141">-Confirm</span></span>
<span data-ttu-id="7e7e2-142">Hiermee wordt u gevraagd om bevestiging voordat u de cmdlet uitvoert.</span><span class="sxs-lookup"><span data-stu-id="7e7e2-142">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="7e7e2-143">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="7e7e2-143">-WhatIf</span></span>
<span data-ttu-id="7e7e2-144">Hiermee wordt weergegeven wat er zou gebeuren als u de cmdlet uitvoert.</span><span class="sxs-lookup"><span data-stu-id="7e7e2-144">Shows what would happen if the cmdlet runs.</span></span>
<span data-ttu-id="7e7e2-145">De cmdlet wordt niet uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="7e7e2-145">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="7e7e2-146">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="7e7e2-146">CommonParameters</span></span>
<span data-ttu-id="7e7e2-147">Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="7e7e2-147">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="7e7e2-148">Zie [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="7e7e2-148">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="7e7e2-149">INVOER</span><span class="sxs-lookup"><span data-stu-id="7e7e2-149">INPUTS</span></span>

### <span data-ttu-id="7e7e2-150">System. Management. Automation. Break Point</span><span class="sxs-lookup"><span data-stu-id="7e7e2-150">System.Management.Automation.Breakpoint</span></span>
<span data-ttu-id="7e7e2-151">U kunt **PSBreakpoint-** onderbrekings punten verwijderen.</span><span class="sxs-lookup"><span data-stu-id="7e7e2-151">You can pipe breakpoint objects to **Remove-PSBreakpoint**.</span></span>

## <span data-ttu-id="7e7e2-152">UITVOER</span><span class="sxs-lookup"><span data-stu-id="7e7e2-152">OUTPUTS</span></span>

### <span data-ttu-id="7e7e2-153">Geen</span><span class="sxs-lookup"><span data-stu-id="7e7e2-153">None</span></span>
<span data-ttu-id="7e7e2-154">De cmdlet genereert geen uitvoer.</span><span class="sxs-lookup"><span data-stu-id="7e7e2-154">The cmdlet does not generate any output.</span></span>

## <span data-ttu-id="7e7e2-155">OPMERKINGEN</span><span class="sxs-lookup"><span data-stu-id="7e7e2-155">NOTES</span></span>

## <span data-ttu-id="7e7e2-156">GERELATEERDE KOPPELINGEN</span><span class="sxs-lookup"><span data-stu-id="7e7e2-156">RELATED LINKS</span></span>

[<span data-ttu-id="7e7e2-157">Disable-PSBreakpoint</span><span class="sxs-lookup"><span data-stu-id="7e7e2-157">Disable-PSBreakpoint</span></span>](Disable-PSBreakpoint.md)

[<span data-ttu-id="7e7e2-158">Enable-PSBreakpoint</span><span class="sxs-lookup"><span data-stu-id="7e7e2-158">Enable-PSBreakpoint</span></span>](Enable-PSBreakpoint.md)

[<span data-ttu-id="7e7e2-159">Get-PSBreakpoint</span><span class="sxs-lookup"><span data-stu-id="7e7e2-159">Get-PSBreakpoint</span></span>](Get-PSBreakpoint.md)

[<span data-ttu-id="7e7e2-160">Get-PSCallStack</span><span class="sxs-lookup"><span data-stu-id="7e7e2-160">Get-PSCallStack</span></span>](Get-PSCallStack.md)

[<span data-ttu-id="7e7e2-161">Set-PSBreakpoint</span><span class="sxs-lookup"><span data-stu-id="7e7e2-161">Set-PSBreakpoint</span></span>](Set-PSBreakpoint.md)

