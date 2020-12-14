---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 02/04/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/pop-location?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Pop-Location
ms.openlocfilehash: 8a44849f27de80ece486b573f1adccafab51972a
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 11/17/2020
ms.locfileid: "94705965"
---
# <span data-ttu-id="aee2f-102">Pop-Location</span><span class="sxs-lookup"><span data-stu-id="aee2f-102">Pop-Location</span></span>

## <span data-ttu-id="aee2f-103">SAMENVATTING</span><span class="sxs-lookup"><span data-stu-id="aee2f-103">SYNOPSIS</span></span>
<span data-ttu-id="aee2f-104">Hiermee wordt de huidige locatie gewijzigd in de locatie die het laatst is gepusht naar de stack.</span><span class="sxs-lookup"><span data-stu-id="aee2f-104">Changes the current location to the location most recently pushed onto the stack.</span></span>

## <span data-ttu-id="aee2f-105">SYNTAXIS</span><span class="sxs-lookup"><span data-stu-id="aee2f-105">SYNTAX</span></span>

```
Pop-Location [-PassThru] [-StackName <String>] [<CommonParameters>]
```

## <span data-ttu-id="aee2f-106">BESCHRIJVING</span><span class="sxs-lookup"><span data-stu-id="aee2f-106">DESCRIPTION</span></span>

<span data-ttu-id="aee2f-107">`Pop-Location`Met de cmdlet wordt de huidige locatie gewijzigd in de locatie die het laatst is gepusht naar de stack met behulp van de- `Push-Location` cmdlet.</span><span class="sxs-lookup"><span data-stu-id="aee2f-107">The `Pop-Location` cmdlet changes the current location to the location most recently pushed onto the stack by using the `Push-Location` cmdlet.</span></span> <span data-ttu-id="aee2f-108">U kunt een locatie van de standaard stack of van een stack die u maakt met behulp van een `Push-Location` opdracht.</span><span class="sxs-lookup"><span data-stu-id="aee2f-108">You can pop a location from the default stack or from a stack that you create by using a `Push-Location` command.</span></span>

## <span data-ttu-id="aee2f-109">VOORBEELDEN</span><span class="sxs-lookup"><span data-stu-id="aee2f-109">EXAMPLES</span></span>

### <span data-ttu-id="aee2f-110">Voor beeld 1: overschakelen naar de meest recente locatie</span><span class="sxs-lookup"><span data-stu-id="aee2f-110">Example 1: Change to most recent location</span></span>

```
PS C:\> Pop-Location
```

<span data-ttu-id="aee2f-111">Met deze opdracht wordt uw locatie gewijzigd in de locatie die het laatst aan de huidige stack is toegevoegd.</span><span class="sxs-lookup"><span data-stu-id="aee2f-111">This command changes your location to the location most recently added to the current stack.</span></span>

### <span data-ttu-id="aee2f-112">Voor beeld 2: wijzigen naar de meest recente locatie in een benoemde stack</span><span class="sxs-lookup"><span data-stu-id="aee2f-112">Example 2: Change to most recent location in a named stack</span></span>

```
PS C:\> Pop-Location -StackName "Stack2"
```

<span data-ttu-id="aee2f-113">Met deze opdracht wordt uw locatie gewijzigd in de locatie die het laatst is toegevoegd aan de Stack2-locatie stack.</span><span class="sxs-lookup"><span data-stu-id="aee2f-113">This command changes your location to the location most recently added to the Stack2 location stack.</span></span>

<span data-ttu-id="aee2f-114">Zie de [opmerkingen](#notes)voor meer informatie over locatie stacks.</span><span class="sxs-lookup"><span data-stu-id="aee2f-114">For more information about location stacks, see the [Notes](#notes).</span></span>

### <span data-ttu-id="aee2f-115">Voor beeld 3: verplaatsen tussen locaties voor verschillende providers</span><span class="sxs-lookup"><span data-stu-id="aee2f-115">Example 3: Move between locations for different providers</span></span>

```
PS C:\> pushd HKLM:\Software\Microsoft\PowerShell
PS HKLM:\Software\Microsoft\PowerShell> pushd Cert:\LocalMachine\TrustedPublisher
PS cert:\LocalMachine\TrustedPublisher> popd
PS HKLM:\Software\Microsoft\PowerShell> popd
PS C:\>
```

<span data-ttu-id="aee2f-116">Met deze opdrachten worden de- `Push-Location` en- `Pop-Location` cmdlets gebruikt om te scha kelen tussen locaties die door verschillende Power shell-providers worden ondersteund.</span><span class="sxs-lookup"><span data-stu-id="aee2f-116">These commands use the `Push-Location` and `Pop-Location` cmdlets to move between locations supported by different PowerShell providers.</span></span> <span data-ttu-id="aee2f-117">De opdrachten gebruiken de `pushd` alias voor `Push-Location` en de `popd` alias voor `Pop-Location` .</span><span class="sxs-lookup"><span data-stu-id="aee2f-117">The commands use the `pushd` alias for `Push-Location` and the `popd` alias for `Pop-Location`.</span></span>

<span data-ttu-id="aee2f-118">Met de eerste opdracht wordt de huidige locatie van het bestands systeem naar de stack gepusht en verplaatst naar het HKLM-station dat wordt ondersteund door de Power shell-register provider.</span><span class="sxs-lookup"><span data-stu-id="aee2f-118">The first command pushes the current file system location onto the stack and moves to the HKLM drive supported by the PowerShell Registry provider.</span></span>

<span data-ttu-id="aee2f-119">Met de tweede opdracht wordt de register locatie naar de stack gepusht en verplaatst naar een locatie die wordt ondersteund door de Power shell-certificaat provider.</span><span class="sxs-lookup"><span data-stu-id="aee2f-119">The second command pushes the registry location onto the stack and moves to a location supported by the PowerShell certificate provider.</span></span>

<span data-ttu-id="aee2f-120">De laatste twee opdrachten hebben een pop die de locaties van de stack.</span><span class="sxs-lookup"><span data-stu-id="aee2f-120">The last two commands pop those locations off the stack.</span></span> <span data-ttu-id="aee2f-121">De eerste `popd` opdracht keert terug naar het register station en de tweede opdracht keert terug naar het bestandssysteem station.</span><span class="sxs-lookup"><span data-stu-id="aee2f-121">The first `popd` command returns to the Registry drive, and the second command returns to the file system drive.</span></span>

## <span data-ttu-id="aee2f-122">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="aee2f-122">PARAMETERS</span></span>

### <span data-ttu-id="aee2f-123">-PassThru</span><span class="sxs-lookup"><span data-stu-id="aee2f-123">-PassThru</span></span>

<span data-ttu-id="aee2f-124">Hiermee wordt een object door gegeven dat de locatie van de pijp lijn vertegenwoordigt.</span><span class="sxs-lookup"><span data-stu-id="aee2f-124">Passes an object that represents the location to the pipeline.</span></span> <span data-ttu-id="aee2f-125">Deze cmdlet genereert standaard geen uitvoer.</span><span class="sxs-lookup"><span data-stu-id="aee2f-125">By default, this cmdlet does not generate any output.</span></span>

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

### <span data-ttu-id="aee2f-126">-Stacknaam</span><span class="sxs-lookup"><span data-stu-id="aee2f-126">-StackName</span></span>

<span data-ttu-id="aee2f-127">Hiermee geeft u de locatie stapel op van waaruit de locatie wordt opvolgd.</span><span class="sxs-lookup"><span data-stu-id="aee2f-127">Specifies the location stack from which the location is popped.</span></span> <span data-ttu-id="aee2f-128">Voer de naam van de locatie stack in.</span><span class="sxs-lookup"><span data-stu-id="aee2f-128">Enter a location stack name.</span></span>

<span data-ttu-id="aee2f-129">Zonder deze para meter wordt `Pop-Location` een locatie uit de huidige locatie stack weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="aee2f-129">Without this parameter, `Pop-Location` pops a location from the current location stack.</span></span> <span data-ttu-id="aee2f-130">Standaard is de huidige locatie stack de niet-genaamde standaard locatie stack die Power Shell maakt.</span><span class="sxs-lookup"><span data-stu-id="aee2f-130">By default, the current location stack is the unnamed default location stack that PowerShell creates.</span></span> <span data-ttu-id="aee2f-131">Als u wilt dat een locatie stack de huidige locatie stack is, gebruikt u de para meter ' **stacknaam** ' van de `Set-Location` cmdlet.</span><span class="sxs-lookup"><span data-stu-id="aee2f-131">To make a location stack the current location stack, use the **StackName** parameter of the `Set-Location` cmdlet.</span></span> <span data-ttu-id="aee2f-132">Zie de [opmerkingen](#notes)voor meer informatie over locatie stacks.</span><span class="sxs-lookup"><span data-stu-id="aee2f-132">For more information about location stacks, see the [Notes](#notes).</span></span>

<span data-ttu-id="aee2f-133">`Pop-Location` kan geen locatie van de niet-genaamde standaard stack hebben als dit de huidige locatie stack is.</span><span class="sxs-lookup"><span data-stu-id="aee2f-133">`Pop-Location` cannot pop a location from the unnamed default stack unless it is the current location stack.</span></span>

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

### <span data-ttu-id="aee2f-134">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="aee2f-134">CommonParameters</span></span>

<span data-ttu-id="aee2f-135">Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="aee2f-135">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="aee2f-136">Zie [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="aee2f-136">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="aee2f-137">INVOER</span><span class="sxs-lookup"><span data-stu-id="aee2f-137">INPUTS</span></span>

### <span data-ttu-id="aee2f-138">Geen</span><span class="sxs-lookup"><span data-stu-id="aee2f-138">None</span></span>

<span data-ttu-id="aee2f-139">U kunt geen invoer van een pipe naar deze cmdlet.</span><span class="sxs-lookup"><span data-stu-id="aee2f-139">You cannot pipe input to this cmdlet.</span></span>

## <span data-ttu-id="aee2f-140">UITVOER</span><span class="sxs-lookup"><span data-stu-id="aee2f-140">OUTPUTS</span></span>

### <span data-ttu-id="aee2f-141">Geen, System. Management. Automation. PathInfo</span><span class="sxs-lookup"><span data-stu-id="aee2f-141">None, System.Management.Automation.PathInfo</span></span>

<span data-ttu-id="aee2f-142">Met deze cmdlet wordt een **System. Management. Automation. PathInfo** -object gegenereerd dat de locatie vertegenwoordigt, als u de para meter **PassThru** opgeeft.</span><span class="sxs-lookup"><span data-stu-id="aee2f-142">This cmdlet generates a **System.Management.Automation.PathInfo** object that represents the location, if you specify the **PassThru** parameter.</span></span> <span data-ttu-id="aee2f-143">Anders wordt met deze cmdlet geen uitvoer gegenereerd.</span><span class="sxs-lookup"><span data-stu-id="aee2f-143">Otherwise, this cmdlet does not generate any output.</span></span>

## <span data-ttu-id="aee2f-144">OPMERKINGEN</span><span class="sxs-lookup"><span data-stu-id="aee2f-144">NOTES</span></span>

<span data-ttu-id="aee2f-145">Power shell ondersteunt meerdere runspaces per proces.</span><span class="sxs-lookup"><span data-stu-id="aee2f-145">PowerShell supports multiple runspaces per process.</span></span> <span data-ttu-id="aee2f-146">Elke runs Pace heeft zijn eigen _huidige map_.</span><span class="sxs-lookup"><span data-stu-id="aee2f-146">Each runspace has its own _current directory_.</span></span>
<span data-ttu-id="aee2f-147">Dit is niet hetzelfde als `[System.Environment]::CurrentDirectory` .</span><span class="sxs-lookup"><span data-stu-id="aee2f-147">This is not the same as `[System.Environment]::CurrentDirectory`.</span></span> <span data-ttu-id="aee2f-148">Dit gedrag kan een probleem zijn bij het aanroepen van .NET-Api's of het uitvoeren van systeem eigen toepassingen zonder expliciete mappaden te bieden.</span><span class="sxs-lookup"><span data-stu-id="aee2f-148">This behavior can be an issue when calling .NET APIs or running native applications without providing explicit directory paths.</span></span>

<span data-ttu-id="aee2f-149">Zelfs als de locatie-cmdlets de huidige map voor het gehele proces hebben ingesteld, kunt u er niet op vertrouwen, omdat deze op elk gewenst moment door een andere runs Pace kan worden gewijzigd.</span><span class="sxs-lookup"><span data-stu-id="aee2f-149">Even if the location cmdlets did set the process-wide current directory, you can't depend on it because another runspace might change it at any time.</span></span> <span data-ttu-id="aee2f-150">U moet de locatie-cmdlets gebruiken om op paden gebaseerde bewerkingen uit te voeren op basis van de huidige werkmap die specifiek is voor de huidige-runs Pace.</span><span class="sxs-lookup"><span data-stu-id="aee2f-150">You should use the location cmdlets to perform path-based operations using the current working directory specific to the current runspace.</span></span>

<span data-ttu-id="aee2f-151">Een stack is een laatste-in-lijst waarin alleen het laatst toegevoegde item kan worden geopend.</span><span class="sxs-lookup"><span data-stu-id="aee2f-151">A stack is a last-in, first-out list in which only the most recently added item can be accessed.</span></span> <span data-ttu-id="aee2f-152">U voegt items toe aan een stack in de volg orde waarin u ze gebruikt en haalt deze vervolgens op voor gebruik in de omgekeerde volg orde.</span><span class="sxs-lookup"><span data-stu-id="aee2f-152">You add items to a stack in the order that you use them, and then retrieve them for use in the reverse order.</span></span> <span data-ttu-id="aee2f-153">Met Power shell kunt u locatie locaties opslaan in site-stacks.</span><span class="sxs-lookup"><span data-stu-id="aee2f-153">PowerShell lets you store provider locations in location stacks.</span></span>

<span data-ttu-id="aee2f-154">In Power shell wordt een niet-benoemde standaard locatie stack gemaakt en u kunt meerdere naam locatie stacks maken.</span><span class="sxs-lookup"><span data-stu-id="aee2f-154">PowerShell creates an unnamed default location stack and you can create multiple named location stacks.</span></span> <span data-ttu-id="aee2f-155">Als u geen stack naam opgeeft, gebruikt Power shell de huidige locatie stack.</span><span class="sxs-lookup"><span data-stu-id="aee2f-155">If you do not specify a stack name, PowerShell uses the current location stack.</span></span> <span data-ttu-id="aee2f-156">Standaard is de niet-naam standaard locatie de huidige locatie stack, maar u kunt de `Set-Location` cmdlet gebruiken om de huidige locatie stack te wijzigen.</span><span class="sxs-lookup"><span data-stu-id="aee2f-156">By default, the unnamed default location is the current location stack, but you can use the `Set-Location` cmdlet to change the current location stack.</span></span>

<span data-ttu-id="aee2f-157">Als u locatie stacks wilt beheren, gebruikt u de Power shell `*-Location` -cmdlets, als volgt:</span><span class="sxs-lookup"><span data-stu-id="aee2f-157">To manage location stacks, use the PowerShell `*-Location` cmdlets, as follows:</span></span>

- <span data-ttu-id="aee2f-158">Gebruik de cmdlet om een locatie aan een locatie stack toe te voegen `Push-Location` .</span><span class="sxs-lookup"><span data-stu-id="aee2f-158">To add a location to a location stack, use the `Push-Location` cmdlet.</span></span>

- <span data-ttu-id="aee2f-159">Als u een locatie wilt ophalen uit een locatie stack, gebruikt u de `Pop-Location` cmdlet.</span><span class="sxs-lookup"><span data-stu-id="aee2f-159">To get a location from a location stack, use the `Pop-Location` cmdlet.</span></span>

- <span data-ttu-id="aee2f-160">Als u de locaties wilt weer geven in de huidige locatie stack, gebruikt u de para meter **stack** van de `Get-Location` cmdlet.</span><span class="sxs-lookup"><span data-stu-id="aee2f-160">To display the locations in the current location stack, use the **Stack** parameter of the `Get-Location` cmdlet.</span></span>

- <span data-ttu-id="aee2f-161">Als u de locaties wilt weer geven in een benoemde locatie stack, gebruikt u de para meter ' **stack** naam ' van de `Get-Location` cmdlet.</span><span class="sxs-lookup"><span data-stu-id="aee2f-161">To display the locations in a named location stack, use the **StackName** parameter of the `Get-Location` cmdlet.</span></span>

- <span data-ttu-id="aee2f-162">Als u een nieuwe locatie stack wilt maken, gebruikt u de para meter ' **stacknaam** ' van de `Push-Location` cmdlet.</span><span class="sxs-lookup"><span data-stu-id="aee2f-162">To create a new location stack, use the **StackName** parameter of the `Push-Location` cmdlet.</span></span> <span data-ttu-id="aee2f-163">Als u een stack opgeeft die niet bestaat, `Push-Location` maakt de stack.</span><span class="sxs-lookup"><span data-stu-id="aee2f-163">If you specify a stack that does not exist, `Push-Location` creates the stack.</span></span>

- <span data-ttu-id="aee2f-164">Als u wilt dat een locatie stack de huidige locatie stack is, gebruikt u de para meter ' **stacknaam** ' van de `Set-Location` cmdlet.</span><span class="sxs-lookup"><span data-stu-id="aee2f-164">To make a location stack the current location stack, use the **StackName** parameter of the `Set-Location` cmdlet.</span></span>

<span data-ttu-id="aee2f-165">De niet-genaamde standaard locatie stack is alleen volledig toegankelijk wanneer het de huidige locatie-stack is.</span><span class="sxs-lookup"><span data-stu-id="aee2f-165">The unnamed default location stack is fully accessible only when it is the current location stack.</span></span>
<span data-ttu-id="aee2f-166">Als u een benoemde locatie stapelt de huidige locatie stack, kunt u de-cmdlets niet meer gebruiken `Push-Location` `Pop-Location` om items toe te voegen aan of te ontvangen van de standaard stack of gebruikt u de `Get-Location` cmdlet om de locaties in de niet-benoemde stack weer te geven.</span><span class="sxs-lookup"><span data-stu-id="aee2f-166">If you make a named location stack the current location stack, you can no longer use the `Push-Location` or `Pop-Location` cmdlets to add or get items from the default stack or use the `Get-Location` cmdlet to display the locations in the unnamed stack.</span></span> <span data-ttu-id="aee2f-167">Gebruik de para meter van de **stack** naam van de `Set-Location` cmdlet met een waarde van `$Null` of een lege teken reeks () om de ongewijzigde stack de huidige stack te maken `""` .</span><span class="sxs-lookup"><span data-stu-id="aee2f-167">To make the unnamed stack the current stack, use the **StackName** parameter of the `Set-Location` cmdlet with a value of `$Null` or an empty string (`""`).</span></span>

<span data-ttu-id="aee2f-168">U kunt ook verwijzen naar `Pop-Location` de ingebouwde alias `popd` .</span><span class="sxs-lookup"><span data-stu-id="aee2f-168">You can also refer to `Pop-Location` by its built-in alias, `popd`.</span></span> <span data-ttu-id="aee2f-169">Zie [about_Aliases](../Microsoft.PowerShell.Core/About/about_Aliases.md)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="aee2f-169">For more information, see [about_Aliases](../Microsoft.PowerShell.Core/About/about_Aliases.md).</span></span>

<span data-ttu-id="aee2f-170">`Pop-Location` is ontworpen om te werken met de gegevens die door elke provider worden weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="aee2f-170">`Pop-Location` is designed to work with the data exposed by any provider.</span></span> <span data-ttu-id="aee2f-171">Als u een lijst wilt weer geven van de providers die beschikbaar zijn in uw sessie, typt u `Get-PSProvider` .</span><span class="sxs-lookup"><span data-stu-id="aee2f-171">To list the providers available in your session, type `Get-PSProvider`.</span></span> <span data-ttu-id="aee2f-172">Zie [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="aee2f-172">For more information, see [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md).</span></span>

## <span data-ttu-id="aee2f-173">GERELATEERDE KOPPELINGEN</span><span class="sxs-lookup"><span data-stu-id="aee2f-173">RELATED LINKS</span></span>

[<span data-ttu-id="aee2f-174">Get-locatie</span><span class="sxs-lookup"><span data-stu-id="aee2f-174">Get-Location</span></span>](Get-Location.md)

[<span data-ttu-id="aee2f-175">Push-locatie</span><span class="sxs-lookup"><span data-stu-id="aee2f-175">Push-Location</span></span>](Push-Location.md)

[<span data-ttu-id="aee2f-176">Set-Location</span><span class="sxs-lookup"><span data-stu-id="aee2f-176">Set-Location</span></span>](Set-Location.md)

[<span data-ttu-id="aee2f-177">about_Aliases</span><span class="sxs-lookup"><span data-stu-id="aee2f-177">about_Aliases</span></span>](../Microsoft.PowerShell.Core/About/about_Aliases.md)

[<span data-ttu-id="aee2f-178">about_Providers</span><span class="sxs-lookup"><span data-stu-id="aee2f-178">about_Providers</span></span>](../Microsoft.PowerShell.Core/About/about_Providers.md)
