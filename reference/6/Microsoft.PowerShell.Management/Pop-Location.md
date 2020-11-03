---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 02/04/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/pop-location?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Pop-Location
ms.openlocfilehash: 42a5c9c75c11a40b5bb842d86894688a354bed15
ms.sourcegitcommit: 01a1c253f48b61c943f6d6aca4e603118014015f
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 08/06/2020
ms.locfileid: "93251728"
---
# <span data-ttu-id="72162-103">Pop-Location</span><span class="sxs-lookup"><span data-stu-id="72162-103">Pop-Location</span></span>

## <span data-ttu-id="72162-104">SAMENVATTING</span><span class="sxs-lookup"><span data-stu-id="72162-104">SYNOPSIS</span></span>
<span data-ttu-id="72162-105">Hiermee wordt de huidige locatie gewijzigd in de locatie die het laatst is gepusht naar de stack.</span><span class="sxs-lookup"><span data-stu-id="72162-105">Changes the current location to the location most recently pushed onto the stack.</span></span>

## <span data-ttu-id="72162-106">SYNTAXIS</span><span class="sxs-lookup"><span data-stu-id="72162-106">SYNTAX</span></span>

```
Pop-Location [-PassThru] [-StackName <String>] [<CommonParameters>]
```

## <span data-ttu-id="72162-107">BESCHRIJVING</span><span class="sxs-lookup"><span data-stu-id="72162-107">DESCRIPTION</span></span>

<span data-ttu-id="72162-108">`Pop-Location`Met de cmdlet wordt de huidige locatie gewijzigd in de locatie die het laatst is gepusht naar de stack met behulp van de- `Push-Location` cmdlet.</span><span class="sxs-lookup"><span data-stu-id="72162-108">The `Pop-Location` cmdlet changes the current location to the location most recently pushed onto the stack by using the `Push-Location` cmdlet.</span></span> <span data-ttu-id="72162-109">U kunt een locatie van de standaard stack of van een stack die u maakt met behulp van een `Push-Location` opdracht.</span><span class="sxs-lookup"><span data-stu-id="72162-109">You can pop a location from the default stack or from a stack that you create by using a `Push-Location` command.</span></span>

## <span data-ttu-id="72162-110">VOORBEELDEN</span><span class="sxs-lookup"><span data-stu-id="72162-110">EXAMPLES</span></span>

### <span data-ttu-id="72162-111">Voor beeld 1: overschakelen naar de meest recente locatie</span><span class="sxs-lookup"><span data-stu-id="72162-111">Example 1: Change to most recent location</span></span>

```
PS C:\> Pop-Location
```

<span data-ttu-id="72162-112">Met deze opdracht wordt uw locatie gewijzigd in de locatie die het laatst aan de huidige stack is toegevoegd.</span><span class="sxs-lookup"><span data-stu-id="72162-112">This command changes your location to the location most recently added to the current stack.</span></span>

### <span data-ttu-id="72162-113">Voor beeld 2: wijzigen naar de meest recente locatie in een benoemde stack</span><span class="sxs-lookup"><span data-stu-id="72162-113">Example 2: Change to most recent location in a named stack</span></span>

```
PS C:\> Pop-Location -StackName "Stack2"
```

<span data-ttu-id="72162-114">Met deze opdracht wordt uw locatie gewijzigd in de locatie die het laatst is toegevoegd aan de Stack2-locatie stack.</span><span class="sxs-lookup"><span data-stu-id="72162-114">This command changes your location to the location most recently added to the Stack2 location stack.</span></span>

<span data-ttu-id="72162-115">Zie de [opmerkingen](#notes)voor meer informatie over locatie stacks.</span><span class="sxs-lookup"><span data-stu-id="72162-115">For more information about location stacks, see the [Notes](#notes).</span></span>

### <span data-ttu-id="72162-116">Voor beeld 3: verplaatsen tussen locaties voor verschillende providers</span><span class="sxs-lookup"><span data-stu-id="72162-116">Example 3: Move between locations for different providers</span></span>

```
PS C:\> pushd HKLM:\Software\Microsoft\PowerShell
PS HKLM:\Software\Microsoft\PowerShell> pushd Cert:\LocalMachine\TrustedPublisher
PS cert:\LocalMachine\TrustedPublisher> popd
PS HKLM:\Software\Microsoft\PowerShell> popd
PS C:\>
```

<span data-ttu-id="72162-117">Met deze opdrachten worden de- `Push-Location` en- `Pop-Location` cmdlets gebruikt om te scha kelen tussen locaties die door verschillende Power shell-providers worden ondersteund.</span><span class="sxs-lookup"><span data-stu-id="72162-117">These commands use the `Push-Location` and `Pop-Location` cmdlets to move between locations supported by different PowerShell providers.</span></span> <span data-ttu-id="72162-118">De opdrachten gebruiken de `pushd` alias voor `Push-Location` en de `popd` alias voor `Pop-Location` .</span><span class="sxs-lookup"><span data-stu-id="72162-118">The commands use the `pushd` alias for `Push-Location` and the `popd` alias for `Pop-Location`.</span></span>

<span data-ttu-id="72162-119">Met de eerste opdracht wordt de huidige locatie van het bestands systeem naar de stack gepusht en verplaatst naar het HKLM-station dat wordt ondersteund door de Power shell-register provider.</span><span class="sxs-lookup"><span data-stu-id="72162-119">The first command pushes the current file system location onto the stack and moves to the HKLM drive supported by the PowerShell Registry provider.</span></span>

<span data-ttu-id="72162-120">Met de tweede opdracht wordt de register locatie naar de stack gepusht en verplaatst naar een locatie die wordt ondersteund door de Power shell-certificaat provider.</span><span class="sxs-lookup"><span data-stu-id="72162-120">The second command pushes the registry location onto the stack and moves to a location supported by the PowerShell certificate provider.</span></span>

<span data-ttu-id="72162-121">De laatste twee opdrachten hebben een pop die de locaties van de stack.</span><span class="sxs-lookup"><span data-stu-id="72162-121">The last two commands pop those locations off the stack.</span></span> <span data-ttu-id="72162-122">De eerste `popd` opdracht keert terug naar het register station en de tweede opdracht keert terug naar het bestandssysteem station.</span><span class="sxs-lookup"><span data-stu-id="72162-122">The first `popd` command returns to the Registry drive, and the second command returns to the file system drive.</span></span>

## <span data-ttu-id="72162-123">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="72162-123">PARAMETERS</span></span>

### <span data-ttu-id="72162-124">-PassThru</span><span class="sxs-lookup"><span data-stu-id="72162-124">-PassThru</span></span>

<span data-ttu-id="72162-125">Hiermee wordt een object door gegeven dat de locatie van de pijp lijn vertegenwoordigt.</span><span class="sxs-lookup"><span data-stu-id="72162-125">Passes an object that represents the location to the pipeline.</span></span> <span data-ttu-id="72162-126">Deze cmdlet genereert standaard geen uitvoer.</span><span class="sxs-lookup"><span data-stu-id="72162-126">By default, this cmdlet does not generate any output.</span></span>

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

### <span data-ttu-id="72162-127">-Stacknaam</span><span class="sxs-lookup"><span data-stu-id="72162-127">-StackName</span></span>

<span data-ttu-id="72162-128">Hiermee geeft u de locatie stapel op van waaruit de locatie wordt opvolgd.</span><span class="sxs-lookup"><span data-stu-id="72162-128">Specifies the location stack from which the location is popped.</span></span> <span data-ttu-id="72162-129">Voer de naam van de locatie stack in.</span><span class="sxs-lookup"><span data-stu-id="72162-129">Enter a location stack name.</span></span>

<span data-ttu-id="72162-130">Zonder deze para meter wordt `Pop-Location` een locatie uit de huidige locatie stack weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="72162-130">Without this parameter, `Pop-Location` pops a location from the current location stack.</span></span> <span data-ttu-id="72162-131">Standaard is de huidige locatie stack de niet-genaamde standaard locatie stack die Power Shell maakt.</span><span class="sxs-lookup"><span data-stu-id="72162-131">By default, the current location stack is the unnamed default location stack that PowerShell creates.</span></span> <span data-ttu-id="72162-132">Als u wilt dat een locatie stack de huidige locatie stack is, gebruikt u de para meter ' **stacknaam** ' van de `Set-Location` cmdlet.</span><span class="sxs-lookup"><span data-stu-id="72162-132">To make a location stack the current location stack, use the **StackName** parameter of the `Set-Location` cmdlet.</span></span> <span data-ttu-id="72162-133">Zie de [opmerkingen](#notes)voor meer informatie over locatie stacks.</span><span class="sxs-lookup"><span data-stu-id="72162-133">For more information about location stacks, see the [Notes](#notes).</span></span>

<span data-ttu-id="72162-134">`Pop-Location` kan geen locatie van de niet-genaamde standaard stack hebben als dit de huidige locatie stack is.</span><span class="sxs-lookup"><span data-stu-id="72162-134">`Pop-Location` cannot pop a location from the unnamed default stack unless it is the current location stack.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="72162-135">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="72162-135">CommonParameters</span></span>

<span data-ttu-id="72162-136">Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="72162-136">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="72162-137">Zie [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="72162-137">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="72162-138">INVOER</span><span class="sxs-lookup"><span data-stu-id="72162-138">INPUTS</span></span>

### <span data-ttu-id="72162-139">Geen</span><span class="sxs-lookup"><span data-stu-id="72162-139">None</span></span>

<span data-ttu-id="72162-140">U kunt geen invoer van een pipe naar deze cmdlet.</span><span class="sxs-lookup"><span data-stu-id="72162-140">You cannot pipe input to this cmdlet.</span></span>

## <span data-ttu-id="72162-141">UITVOER</span><span class="sxs-lookup"><span data-stu-id="72162-141">OUTPUTS</span></span>

### <span data-ttu-id="72162-142">Geen, System. Management. Automation. PathInfo</span><span class="sxs-lookup"><span data-stu-id="72162-142">None, System.Management.Automation.PathInfo</span></span>

<span data-ttu-id="72162-143">Met deze cmdlet wordt een **System. Management. Automation. PathInfo** -object gegenereerd dat de locatie vertegenwoordigt, als u de para meter **PassThru** opgeeft.</span><span class="sxs-lookup"><span data-stu-id="72162-143">This cmdlet generates a **System.Management.Automation.PathInfo** object that represents the location, if you specify the **PassThru** parameter.</span></span> <span data-ttu-id="72162-144">Anders wordt met deze cmdlet geen uitvoer gegenereerd.</span><span class="sxs-lookup"><span data-stu-id="72162-144">Otherwise, this cmdlet does not generate any output.</span></span>

## <span data-ttu-id="72162-145">OPMERKINGEN</span><span class="sxs-lookup"><span data-stu-id="72162-145">NOTES</span></span>

<span data-ttu-id="72162-146">Power shell ondersteunt meerdere runspaces per proces.</span><span class="sxs-lookup"><span data-stu-id="72162-146">PowerShell supports multiple runspaces per process.</span></span> <span data-ttu-id="72162-147">Elke runs Pace heeft zijn eigen _huidige map_.</span><span class="sxs-lookup"><span data-stu-id="72162-147">Each runspace has its own _current directory_.</span></span>
<span data-ttu-id="72162-148">Dit is niet hetzelfde als `[System.Environment]::CurrentDirectory` .</span><span class="sxs-lookup"><span data-stu-id="72162-148">This is not the same as `[System.Environment]::CurrentDirectory`.</span></span> <span data-ttu-id="72162-149">Dit gedrag kan een probleem zijn bij het aanroepen van .NET-Api's of het uitvoeren van systeem eigen toepassingen zonder expliciete mappaden te bieden.</span><span class="sxs-lookup"><span data-stu-id="72162-149">This behavior can be an issue when calling .NET APIs or running native applications without providing explicit directory paths.</span></span>

<span data-ttu-id="72162-150">Zelfs als de locatie-cmdlets de huidige map voor het gehele proces hebben ingesteld, kunt u er niet op vertrouwen, omdat deze op elk gewenst moment door een andere runs Pace kan worden gewijzigd.</span><span class="sxs-lookup"><span data-stu-id="72162-150">Even if the location cmdlets did set the process-wide current directory, you can't depend on it because another runspace might change it at any time.</span></span> <span data-ttu-id="72162-151">U moet de locatie-cmdlets gebruiken om op paden gebaseerde bewerkingen uit te voeren op basis van de huidige werkmap die specifiek is voor de huidige-runs Pace.</span><span class="sxs-lookup"><span data-stu-id="72162-151">You should use the location cmdlets to perform path-based operations using the current working directory specific to the current runspace.</span></span>

<span data-ttu-id="72162-152">Een stack is een laatste-in-lijst waarin alleen het laatst toegevoegde item kan worden geopend.</span><span class="sxs-lookup"><span data-stu-id="72162-152">A stack is a last-in, first-out list in which only the most recently added item can be accessed.</span></span> <span data-ttu-id="72162-153">U voegt items toe aan een stack in de volg orde waarin u ze gebruikt en haalt deze vervolgens op voor gebruik in de omgekeerde volg orde.</span><span class="sxs-lookup"><span data-stu-id="72162-153">You add items to a stack in the order that you use them, and then retrieve them for use in the reverse order.</span></span> <span data-ttu-id="72162-154">Met Power shell kunt u locatie locaties opslaan in site-stacks.</span><span class="sxs-lookup"><span data-stu-id="72162-154">PowerShell lets you store provider locations in location stacks.</span></span>

<span data-ttu-id="72162-155">In Power shell wordt een niet-benoemde standaard locatie stack gemaakt en u kunt meerdere naam locatie stacks maken.</span><span class="sxs-lookup"><span data-stu-id="72162-155">PowerShell creates an unnamed default location stack and you can create multiple named location stacks.</span></span> <span data-ttu-id="72162-156">Als u geen stack naam opgeeft, gebruikt Power shell de huidige locatie stack.</span><span class="sxs-lookup"><span data-stu-id="72162-156">If you do not specify a stack name, PowerShell uses the current location stack.</span></span> <span data-ttu-id="72162-157">Standaard is de niet-naam standaard locatie de huidige locatie stack, maar u kunt de `Set-Location` cmdlet gebruiken om de huidige locatie stack te wijzigen.</span><span class="sxs-lookup"><span data-stu-id="72162-157">By default, the unnamed default location is the current location stack, but you can use the `Set-Location` cmdlet to change the current location stack.</span></span>

<span data-ttu-id="72162-158">Als u locatie stacks wilt beheren, gebruikt u de Power shell `*-Location` -cmdlets, als volgt:</span><span class="sxs-lookup"><span data-stu-id="72162-158">To manage location stacks, use the PowerShell `*-Location` cmdlets, as follows:</span></span>

- <span data-ttu-id="72162-159">Gebruik de cmdlet om een locatie aan een locatie stack toe te voegen `Push-Location` .</span><span class="sxs-lookup"><span data-stu-id="72162-159">To add a location to a location stack, use the `Push-Location` cmdlet.</span></span>

- <span data-ttu-id="72162-160">Als u een locatie wilt ophalen uit een locatie stack, gebruikt u de `Pop-Location` cmdlet.</span><span class="sxs-lookup"><span data-stu-id="72162-160">To get a location from a location stack, use the `Pop-Location` cmdlet.</span></span>

- <span data-ttu-id="72162-161">Als u de locaties wilt weer geven in de huidige locatie stack, gebruikt u de para meter **stack** van de `Get-Location` cmdlet.</span><span class="sxs-lookup"><span data-stu-id="72162-161">To display the locations in the current location stack, use the **Stack** parameter of the `Get-Location` cmdlet.</span></span>

- <span data-ttu-id="72162-162">Als u de locaties wilt weer geven in een benoemde locatie stack, gebruikt u de para meter ' **stack** naam ' van de `Get-Location` cmdlet.</span><span class="sxs-lookup"><span data-stu-id="72162-162">To display the locations in a named location stack, use the **StackName** parameter of the `Get-Location` cmdlet.</span></span>

- <span data-ttu-id="72162-163">Als u een nieuwe locatie stack wilt maken, gebruikt u de para meter ' **stacknaam** ' van de `Push-Location` cmdlet.</span><span class="sxs-lookup"><span data-stu-id="72162-163">To create a new location stack, use the **StackName** parameter of the `Push-Location` cmdlet.</span></span> <span data-ttu-id="72162-164">Als u een stack opgeeft die niet bestaat, `Push-Location` maakt de stack.</span><span class="sxs-lookup"><span data-stu-id="72162-164">If you specify a stack that does not exist, `Push-Location` creates the stack.</span></span>

- <span data-ttu-id="72162-165">Als u wilt dat een locatie stack de huidige locatie stack is, gebruikt u de para meter ' **stacknaam** ' van de `Set-Location` cmdlet.</span><span class="sxs-lookup"><span data-stu-id="72162-165">To make a location stack the current location stack, use the **StackName** parameter of the `Set-Location` cmdlet.</span></span>

<span data-ttu-id="72162-166">De niet-genaamde standaard locatie stack is alleen volledig toegankelijk wanneer het de huidige locatie-stack is.</span><span class="sxs-lookup"><span data-stu-id="72162-166">The unnamed default location stack is fully accessible only when it is the current location stack.</span></span>
<span data-ttu-id="72162-167">Als u een benoemde locatie stapelt de huidige locatie stack, kunt u de-cmdlets niet meer gebruiken `Push-Location` `Pop-Location` om items toe te voegen aan of te ontvangen van de standaard stack of gebruikt u de `Get-Location` cmdlet om de locaties in de niet-benoemde stack weer te geven.</span><span class="sxs-lookup"><span data-stu-id="72162-167">If you make a named location stack the current location stack, you can no longer use the `Push-Location` or `Pop-Location` cmdlets to add or get items from the default stack or use the `Get-Location` cmdlet to display the locations in the unnamed stack.</span></span> <span data-ttu-id="72162-168">Gebruik de para meter van de **stack** naam van de `Set-Location` cmdlet met een waarde van `$Null` of een lege teken reeks () om de ongewijzigde stack de huidige stack te maken `""` .</span><span class="sxs-lookup"><span data-stu-id="72162-168">To make the unnamed stack the current stack, use the **StackName** parameter of the `Set-Location` cmdlet with a value of `$Null` or an empty string (`""`).</span></span>

<span data-ttu-id="72162-169">U kunt ook verwijzen naar `Pop-Location` de ingebouwde alias `popd` .</span><span class="sxs-lookup"><span data-stu-id="72162-169">You can also refer to `Pop-Location` by its built-in alias, `popd`.</span></span> <span data-ttu-id="72162-170">Zie [about_Aliases](../Microsoft.PowerShell.Core/About/about_Aliases.md)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="72162-170">For more information, see [about_Aliases](../Microsoft.PowerShell.Core/About/about_Aliases.md).</span></span>

<span data-ttu-id="72162-171">`Pop-Location` is ontworpen om te werken met de gegevens die door elke provider worden weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="72162-171">`Pop-Location` is designed to work with the data exposed by any provider.</span></span> <span data-ttu-id="72162-172">Als u een lijst wilt weer geven van de providers die beschikbaar zijn in uw sessie, typt u `Get-PSProvider` .</span><span class="sxs-lookup"><span data-stu-id="72162-172">To list the providers available in your session, type `Get-PSProvider`.</span></span> <span data-ttu-id="72162-173">Zie [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="72162-173">For more information, see [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md).</span></span>

## <span data-ttu-id="72162-174">GERELATEERDE KOPPELINGEN</span><span class="sxs-lookup"><span data-stu-id="72162-174">RELATED LINKS</span></span>

[<span data-ttu-id="72162-175">Get-locatie</span><span class="sxs-lookup"><span data-stu-id="72162-175">Get-Location</span></span>](Get-Location.md)

[<span data-ttu-id="72162-176">Push-locatie</span><span class="sxs-lookup"><span data-stu-id="72162-176">Push-Location</span></span>](Push-Location.md)

[<span data-ttu-id="72162-177">Set-Location</span><span class="sxs-lookup"><span data-stu-id="72162-177">Set-Location</span></span>](Set-Location.md)

[<span data-ttu-id="72162-178">about_Aliases</span><span class="sxs-lookup"><span data-stu-id="72162-178">about_Aliases</span></span>](../Microsoft.PowerShell.Core/About/about_Aliases.md)

[<span data-ttu-id="72162-179">about_Providers</span><span class="sxs-lookup"><span data-stu-id="72162-179">about_Providers</span></span>](../Microsoft.PowerShell.Core/About/about_Providers.md)
