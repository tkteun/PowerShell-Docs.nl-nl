---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 02/04/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/push-location?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Push-Location
ms.openlocfilehash: abc40f3ae388a915c9df42d0c2df24f848e45e73
ms.sourcegitcommit: 01a1c253f48b61c943f6d6aca4e603118014015f
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 08/06/2020
ms.locfileid: "93251729"
---
# <span data-ttu-id="000de-103">Push-Location</span><span class="sxs-lookup"><span data-stu-id="000de-103">Push-Location</span></span>

## <span data-ttu-id="000de-104">SAMENVATTING</span><span class="sxs-lookup"><span data-stu-id="000de-104">SYNOPSIS</span></span>
<span data-ttu-id="000de-105">De huidige locatie wordt toegevoegd aan de bovenkant van een locatie stack.</span><span class="sxs-lookup"><span data-stu-id="000de-105">Adds the current location to the top of a location stack.</span></span>

## <span data-ttu-id="000de-106">SYNTAXIS</span><span class="sxs-lookup"><span data-stu-id="000de-106">SYNTAX</span></span>

### <span data-ttu-id="000de-107">Pad (standaard)</span><span class="sxs-lookup"><span data-stu-id="000de-107">Path (Default)</span></span>

```
Push-Location [[-Path] <String>] [-PassThru] [-StackName <String>] [-UseTransaction] [<CommonParameters>]
```

### <span data-ttu-id="000de-108">LiteralPath</span><span class="sxs-lookup"><span data-stu-id="000de-108">LiteralPath</span></span>

```
Push-Location [-LiteralPath <String>] [-PassThru] [-StackName <String>] [-UseTransaction] [<CommonParameters>]
```

## <span data-ttu-id="000de-109">BESCHRIJVING</span><span class="sxs-lookup"><span data-stu-id="000de-109">DESCRIPTION</span></span>

<span data-ttu-id="000de-110">De `Push-Location` cmdlet voegt de huidige locatie (' pushes ') toe aan een locatie stack.</span><span class="sxs-lookup"><span data-stu-id="000de-110">The `Push-Location` cmdlet adds ("pushes") the current location onto a location stack.</span></span> <span data-ttu-id="000de-111">Als u een pad opgeeft, wordt `Push-Location` de huidige locatie naar een locatie stack gepusht en wordt de huidige locatie gewijzigd in de locatie die is opgegeven door het pad.</span><span class="sxs-lookup"><span data-stu-id="000de-111">If you specify a path, `Push-Location` pushes the current location onto a location stack and then changes the current location to the location specified by the path.</span></span> <span data-ttu-id="000de-112">U kunt de `Pop-Location` cmdlet gebruiken om locaties op te halen uit de locatie stack.</span><span class="sxs-lookup"><span data-stu-id="000de-112">You can use the `Pop-Location` cmdlet to get locations from the location stack.</span></span>

<span data-ttu-id="000de-113">Standaard `Push-Location` duwt de cmdlet de huidige locatie naar de huidige locatie stack, maar u kunt de para meter van de **stacknaam** gebruiken om een alternatieve locatie-stack op te geven.</span><span class="sxs-lookup"><span data-stu-id="000de-113">By default, the `Push-Location` cmdlet pushes the current location onto the current location stack, but you can use the **StackName** parameter to specify an alternate location stack.</span></span> <span data-ttu-id="000de-114">Als de stack niet bestaat, `Push-Location` wordt deze gemaakt.</span><span class="sxs-lookup"><span data-stu-id="000de-114">If the stack does not exist, `Push-Location` creates it.</span></span>

<span data-ttu-id="000de-115">Zie de [opmerkingen](#notes)voor meer informatie over locatie stacks.</span><span class="sxs-lookup"><span data-stu-id="000de-115">For more information about location stacks, see the [Notes](#notes).</span></span>

## <span data-ttu-id="000de-116">VOORBEELDEN</span><span class="sxs-lookup"><span data-stu-id="000de-116">EXAMPLES</span></span>

### <span data-ttu-id="000de-117">Voorbeeld 1</span><span class="sxs-lookup"><span data-stu-id="000de-117">Example 1</span></span>

<span data-ttu-id="000de-118">In dit voor beeld wordt de huidige locatie naar de standaard locatie stack gepusht. vervolgens wordt de locatie gewijzigd in `C:\Windows` .</span><span class="sxs-lookup"><span data-stu-id="000de-118">This example pushes the current location onto the default location stack and then changes the location to `C:\Windows`.</span></span>

```
PS C:\> Push-Location C:\Windows
```

### <span data-ttu-id="000de-119">Voorbeeld 2</span><span class="sxs-lookup"><span data-stu-id="000de-119">Example 2</span></span>

<span data-ttu-id="000de-120">In dit voor beeld wordt de huidige locatie naar de RegFunction-stack gepusht en wordt de huidige locatie gewijzigd in de `HKLM:\Software\Policies` locatie.</span><span class="sxs-lookup"><span data-stu-id="000de-120">This example pushes the current location onto the RegFunction stack and changes the current location to the `HKLM:\Software\Policies` location.</span></span>

```
PS C:\> Push-Location HKLM:\Software\Policies -StackName RegFunction
```

<span data-ttu-id="000de-121">U kunt de locatie-cmdlets gebruiken in een Power Shell-station (PSDrive).</span><span class="sxs-lookup"><span data-stu-id="000de-121">You can use the Location cmdlets in any PowerShell drive (PSDrive).</span></span>

### <span data-ttu-id="000de-122">Voorbeeld 3</span><span class="sxs-lookup"><span data-stu-id="000de-122">Example 3</span></span>

<span data-ttu-id="000de-123">Met deze opdracht wordt de huidige locatie naar de standaard stack gepusht.</span><span class="sxs-lookup"><span data-stu-id="000de-123">This command pushes the current location onto the default stack.</span></span> <span data-ttu-id="000de-124">De locatie wordt niet gewijzigd.</span><span class="sxs-lookup"><span data-stu-id="000de-124">It does not change the location.</span></span>

```
PS C:\> Push-Location
```

### <span data-ttu-id="000de-125">Voor beeld 4: een benoemde stack maken en gebruiken</span><span class="sxs-lookup"><span data-stu-id="000de-125">Example 4 - Create and use a named stack</span></span>

<span data-ttu-id="000de-126">Deze opdrachten laten zien hoe u een benoemde locatie stapel maakt en gebruikt.</span><span class="sxs-lookup"><span data-stu-id="000de-126">These commands show how to create and use a named location stack.</span></span>

```
PS C:\> Push-Location ~ -StackName Stack2
PS C:\Users\User01> Pop-Location -StackName Stack2
PS C:\>
```

<span data-ttu-id="000de-127">De eerste opdracht duwt de huidige locatie naar een nieuwe stack met de naam Stack2 en wijzigt vervolgens de huidige locatie naar de basismap, die wordt weer gegeven in de opdracht door het tilde-symbool ( `~` ), die wordt gebruikt voor de stations van een bestands systeem provider en die gelijk is aan `$HOME` en `$env:USERPROFILE` .</span><span class="sxs-lookup"><span data-stu-id="000de-127">The first command pushes the current location onto a new stack named Stack2, and then changes the current location to the home directory, represented in the command by the tilde symbol (`~`), which when used on a FileSystem provider drives is equivalent to `$HOME` and `$env:USERPROFILE`.</span></span>

<span data-ttu-id="000de-128">Als Stack2 al in de sessie bestaat, `Push-Location` wordt deze gemaakt.</span><span class="sxs-lookup"><span data-stu-id="000de-128">If Stack2 does not already exist in the session, `Push-Location` creates it.</span></span> <span data-ttu-id="000de-129">Met de tweede opdracht wordt de `Pop-Location` cmdlet gebruikt om de oorspronkelijke locatie ( `C:\` ) van de Stack2-stack te pop.</span><span class="sxs-lookup"><span data-stu-id="000de-129">The second command uses the `Pop-Location` cmdlet to pop the original location (`C:\`) from the Stack2 stack.</span></span> <span data-ttu-id="000de-130">Zonder de para meter ' **stuurprogrammastack** ' `Pop-Location` zou de locatie van de niet-genaamde standaard stack zouden pop-en.</span><span class="sxs-lookup"><span data-stu-id="000de-130">Without the **StackName** parameter, `Pop-Location` would pop the location from the unnamed default stack.</span></span>

<span data-ttu-id="000de-131">Zie de [opmerkingen](#notes)voor meer informatie over locatie stacks.</span><span class="sxs-lookup"><span data-stu-id="000de-131">For more information about location stacks, see the [Notes](#notes).</span></span>

## <span data-ttu-id="000de-132">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="000de-132">PARAMETERS</span></span>

### <span data-ttu-id="000de-133">-LiteralPath</span><span class="sxs-lookup"><span data-stu-id="000de-133">-LiteralPath</span></span>

<span data-ttu-id="000de-134">Hiermee geeft u het pad naar de nieuwe locatie.</span><span class="sxs-lookup"><span data-stu-id="000de-134">Specifies the path to the new location.</span></span> <span data-ttu-id="000de-135">In tegens telling tot de para meter **Path** wordt de waarde van de para meter **LiteralPath** exact gebruikt terwijl deze wordt getypt.</span><span class="sxs-lookup"><span data-stu-id="000de-135">Unlike the **Path** parameter, the value of the **LiteralPath** parameter is used exactly as it is typed.</span></span> <span data-ttu-id="000de-136">Geen tekens worden geïnterpreteerd als joker tekens.</span><span class="sxs-lookup"><span data-stu-id="000de-136">No characters are interpreted as wildcards.</span></span> <span data-ttu-id="000de-137">Als het pad escape tekens bevat, plaatst u het tussen enkele aanhalings tekens.</span><span class="sxs-lookup"><span data-stu-id="000de-137">If the path includes escape characters, enclose it in single quotation marks.</span></span> <span data-ttu-id="000de-138">Enkele aanhalings tekens geven aan dat Power shell geen karakters interpreteert als escape reeksen.</span><span class="sxs-lookup"><span data-stu-id="000de-138">Single quotation marks tell PowerShell not to interpret any characters as escape sequences.</span></span>

```yaml
Type: System.String
Parameter Sets: LiteralPath
Aliases: PSPath

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="000de-139">-PassThru</span><span class="sxs-lookup"><span data-stu-id="000de-139">-PassThru</span></span>

<span data-ttu-id="000de-140">Hiermee wordt een object door gegeven dat de locatie naar de pijp lijn vertegenwoordigt.</span><span class="sxs-lookup"><span data-stu-id="000de-140">Passes an object representing the location to the pipeline.</span></span> <span data-ttu-id="000de-141">Deze cmdlet genereert standaard geen uitvoer.</span><span class="sxs-lookup"><span data-stu-id="000de-141">By default, this cmdlet does not generate any output.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="000de-142">-Path</span><span class="sxs-lookup"><span data-stu-id="000de-142">-Path</span></span>

<span data-ttu-id="000de-143">Hiermee wordt uw locatie gewijzigd in de locatie die is opgegeven door dit pad nadat deze de huidige locatie boven aan de stack heeft toegevoegd (pushes).</span><span class="sxs-lookup"><span data-stu-id="000de-143">Changes your location to the location specified by this path after it adds (pushes) the current location onto the top of the stack.</span></span> <span data-ttu-id="000de-144">Geef een pad op naar een locatie waarvan de provider deze cmdlet ondersteunt.</span><span class="sxs-lookup"><span data-stu-id="000de-144">Enter a path to any location whose provider supports this cmdlet.</span></span> <span data-ttu-id="000de-145">Joker tekens zijn toegestaan.</span><span class="sxs-lookup"><span data-stu-id="000de-145">Wildcards are permitted.</span></span> <span data-ttu-id="000de-146">De parameter naam is optioneel.</span><span class="sxs-lookup"><span data-stu-id="000de-146">The parameter name is optional.</span></span>

```yaml
Type: System.String
Parameter Sets: Path
Aliases:

Required: False
Position: 1
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: True
```

### <span data-ttu-id="000de-147">-Stacknaam</span><span class="sxs-lookup"><span data-stu-id="000de-147">-StackName</span></span>

<span data-ttu-id="000de-148">Hiermee geeft u de locatie stack op waaraan de huidige locatie wordt toegevoegd.</span><span class="sxs-lookup"><span data-stu-id="000de-148">Specifies the location stack to which the current location is added.</span></span> <span data-ttu-id="000de-149">Voer de naam van de locatie stack in.</span><span class="sxs-lookup"><span data-stu-id="000de-149">Enter a location stack name.</span></span>
<span data-ttu-id="000de-150">Als de stack niet bestaat, `Push-Location` wordt deze gemaakt.</span><span class="sxs-lookup"><span data-stu-id="000de-150">If the stack does not exist, `Push-Location` creates it.</span></span>

<span data-ttu-id="000de-151">Zonder deze para meter `Push-Location` voegt de locatie toe aan de huidige locatie stack.</span><span class="sxs-lookup"><span data-stu-id="000de-151">Without this parameter, `Push-Location` adds the location to the current location stack.</span></span> <span data-ttu-id="000de-152">Standaard is de huidige locatie stack de niet-genaamde standaard locatie stack die Power Shell maakt.</span><span class="sxs-lookup"><span data-stu-id="000de-152">By default, the current location stack is the unnamed default location stack that PowerShell creates.</span></span>
<span data-ttu-id="000de-153">Als u wilt dat een locatie stack de huidige locatie stack is, gebruikt u de para meter ' **stacknaam** ' van de `Set-Location` cmdlet.</span><span class="sxs-lookup"><span data-stu-id="000de-153">To make a location stack the current location stack, use the **StackName** parameter of the `Set-Location` cmdlet.</span></span> <span data-ttu-id="000de-154">Zie de [opmerkingen](#notes)voor meer informatie over locatie stacks.</span><span class="sxs-lookup"><span data-stu-id="000de-154">For more information about location stacks, see the [Notes](#notes).</span></span>

> [!NOTE]
> <span data-ttu-id="000de-155">`Push-Location` kan geen locatie toevoegen aan de niet-genaamde standaard stack, tenzij dit de huidige locatie stack is.</span><span class="sxs-lookup"><span data-stu-id="000de-155">`Push-Location` cannot add a location to the unnamed default stack unless it is the current location stack.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: Default stack
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="000de-156">-UseTransaction</span><span class="sxs-lookup"><span data-stu-id="000de-156">-UseTransaction</span></span>

<span data-ttu-id="000de-157">Hiermee wordt de opdracht opgenomen in de actieve transactie.</span><span class="sxs-lookup"><span data-stu-id="000de-157">Includes the command in the active transaction.</span></span> <span data-ttu-id="000de-158">Deze parameter is alleen geldig wanneer een transactie wordt uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="000de-158">This parameter is valid only when a transaction is in progress.</span></span> <span data-ttu-id="000de-159">Zie [about_Transactions](../Microsoft.PowerShell.Core/About/about_transactions.md)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="000de-159">For more information, see [about_Transactions](../Microsoft.PowerShell.Core/About/about_transactions.md).</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: usetx

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="000de-160">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="000de-160">CommonParameters</span></span>

<span data-ttu-id="000de-161">Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="000de-161">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="000de-162">Zie [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="000de-162">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="000de-163">INVOER</span><span class="sxs-lookup"><span data-stu-id="000de-163">INPUTS</span></span>

### <span data-ttu-id="000de-164">System. String</span><span class="sxs-lookup"><span data-stu-id="000de-164">System.String</span></span>

<span data-ttu-id="000de-165">U kunt een teken reeks die een pad (maar geen letterlijk pad) bevat, door sluizen naar `Push-Location` .</span><span class="sxs-lookup"><span data-stu-id="000de-165">You can pipe a string that contains a path (but not a literal path) to `Push-Location`.</span></span>

## <span data-ttu-id="000de-166">UITVOER</span><span class="sxs-lookup"><span data-stu-id="000de-166">OUTPUTS</span></span>

### <span data-ttu-id="000de-167">Geen of System. Management. Automation. PathInfo</span><span class="sxs-lookup"><span data-stu-id="000de-167">None or System.Management.Automation.PathInfo</span></span>

<span data-ttu-id="000de-168">Wanneer u de para meter **PassThru** gebruikt, `Push-Location` genereert een **System. Management. Automation. PathInfo** -object dat de locatie vertegenwoordigt.</span><span class="sxs-lookup"><span data-stu-id="000de-168">When you use the **PassThru** parameter, `Push-Location` generates a **System.Management.Automation.PathInfo** object that represents the location.</span></span> <span data-ttu-id="000de-169">Anders wordt met deze cmdlet geen uitvoer gegenereerd.</span><span class="sxs-lookup"><span data-stu-id="000de-169">Otherwise, this cmdlet does not generate any output.</span></span>

## <span data-ttu-id="000de-170">OPMERKINGEN</span><span class="sxs-lookup"><span data-stu-id="000de-170">NOTES</span></span>

<span data-ttu-id="000de-171">Power shell ondersteunt meerdere runspaces per proces.</span><span class="sxs-lookup"><span data-stu-id="000de-171">PowerShell supports multiple runspaces per process.</span></span> <span data-ttu-id="000de-172">Elke runs Pace heeft zijn eigen _huidige map_.</span><span class="sxs-lookup"><span data-stu-id="000de-172">Each runspace has its own _current directory_.</span></span>
<span data-ttu-id="000de-173">Dit is niet hetzelfde als `[System.Environment]::CurrentDirectory` .</span><span class="sxs-lookup"><span data-stu-id="000de-173">This is not the same as `[System.Environment]::CurrentDirectory`.</span></span> <span data-ttu-id="000de-174">Dit gedrag kan een probleem zijn bij het aanroepen van .NET-Api's of het uitvoeren van systeem eigen toepassingen zonder expliciete mappaden te bieden.</span><span class="sxs-lookup"><span data-stu-id="000de-174">This behavior can be an issue when calling .NET APIs or running native applications without providing explicit directory paths.</span></span>

<span data-ttu-id="000de-175">Zelfs als de locatie-cmdlets de huidige map voor het gehele proces hebben ingesteld, kunt u er niet op vertrouwen, omdat deze op elk gewenst moment door een andere runs Pace kan worden gewijzigd.</span><span class="sxs-lookup"><span data-stu-id="000de-175">Even if the location cmdlets did set the process-wide current directory, you can't depend on it because another runspace might change it at any time.</span></span> <span data-ttu-id="000de-176">U moet de locatie-cmdlets gebruiken om op paden gebaseerde bewerkingen uit te voeren op basis van de huidige werkmap die specifiek is voor de huidige-runs Pace.</span><span class="sxs-lookup"><span data-stu-id="000de-176">You should use the location cmdlets to perform path-based operations using the current working directory specific to the current runspace.</span></span>

<span data-ttu-id="000de-177">Een stack is een vervolg keuzelijst die het laatst is toegevoegd en die alleen toegankelijk is voor het laatst toegevoegde item.</span><span class="sxs-lookup"><span data-stu-id="000de-177">A stack is a last-in, first-out list in which only the most recently added item is accessible.</span></span>
<span data-ttu-id="000de-178">U voegt items toe aan een stack in de volg orde waarin u ze gebruikt en haalt deze vervolgens op voor gebruik in de omgekeerde volg orde.</span><span class="sxs-lookup"><span data-stu-id="000de-178">You add items to a stack in the order that you use them, and then retrieve them for use in the reverse order.</span></span> <span data-ttu-id="000de-179">Met Power shell kunt u locatie locaties opslaan in site-stacks.</span><span class="sxs-lookup"><span data-stu-id="000de-179">PowerShell lets you store provider locations in location stacks.</span></span>

<span data-ttu-id="000de-180">In Power shell wordt een niet-benoemde standaard locatie stack gemaakt en u kunt meerdere naam locatie stacks maken.</span><span class="sxs-lookup"><span data-stu-id="000de-180">PowerShell creates an unnamed default location stack and you can create multiple named location stacks.</span></span> <span data-ttu-id="000de-181">Als u geen stack naam opgeeft, gebruikt Power shell de huidige locatie stack.</span><span class="sxs-lookup"><span data-stu-id="000de-181">If you do not specify a stack name, PowerShell uses the current location stack.</span></span> <span data-ttu-id="000de-182">Standaard is de niet-naam standaard locatie de huidige locatie stack, maar u kunt de `Set-Location` cmdlet gebruiken om de huidige locatie stack te wijzigen.</span><span class="sxs-lookup"><span data-stu-id="000de-182">By default, the unnamed default location is the current location stack, but you can use the `Set-Location` cmdlet to change the current location stack.</span></span>

<span data-ttu-id="000de-183">Als u locatie stacks wilt beheren, gebruikt u de Power shell location-cmdlets, als volgt.</span><span class="sxs-lookup"><span data-stu-id="000de-183">To manage location stacks, use the PowerShell Location cmdlets, as follows.</span></span>

- <span data-ttu-id="000de-184">Gebruik de cmdlet om een locatie aan een locatie stack toe te voegen `Push-Location` .</span><span class="sxs-lookup"><span data-stu-id="000de-184">To add a location to a location stack, use the `Push-Location` cmdlet.</span></span>

- <span data-ttu-id="000de-185">Als u een locatie wilt ophalen uit een locatie stack, gebruikt u de `Pop-Location` cmdlet.</span><span class="sxs-lookup"><span data-stu-id="000de-185">To get a location from a location stack, use the `Pop-Location` cmdlet.</span></span>

- <span data-ttu-id="000de-186">Als u de locaties wilt weer geven in de huidige locatie stack, gebruikt u de para meter **stack** van de `Get-Location` cmdlet.</span><span class="sxs-lookup"><span data-stu-id="000de-186">To display the locations in the current location stack, use the **Stack** parameter of the `Get-Location` cmdlet.</span></span>

- <span data-ttu-id="000de-187">Als u de locaties wilt weer geven in een benoemde locatie stack, gebruikt u de para meter ' **stack** naam ' van de `Get-Location` cmdlet.</span><span class="sxs-lookup"><span data-stu-id="000de-187">To display the locations in a named location stack, use the **StackName** parameter of the `Get-Location` cmdlet.</span></span>

- <span data-ttu-id="000de-188">Als u een nieuwe locatie stack wilt maken, gebruikt u de para meter ' Stacknaam ' van de `Push-Location` cmdlet.</span><span class="sxs-lookup"><span data-stu-id="000de-188">To create a new location stack, use the StackName parameter of the `Push-Location` cmdlet.</span></span> <span data-ttu-id="000de-189">Als u een stack opgeeft die niet bestaat, `Push-Location` maakt de stack.</span><span class="sxs-lookup"><span data-stu-id="000de-189">If you specify a stack that does not exist, `Push-Location` creates the stack.</span></span>

- <span data-ttu-id="000de-190">Als u wilt dat een locatie stack de huidige locatie stack is, gebruikt u de para meter ' Stacknaam ' van de `Set-Location` cmdlet.</span><span class="sxs-lookup"><span data-stu-id="000de-190">To make a location stack the current location stack, use the StackName parameter of the `Set-Location` cmdlet.</span></span>

<span data-ttu-id="000de-191">De niet-genaamde standaard locatie stack is alleen volledig toegankelijk wanneer het de huidige locatie-stack is.</span><span class="sxs-lookup"><span data-stu-id="000de-191">The unnamed default location stack is fully accessible only when it is the current location stack.</span></span>
<span data-ttu-id="000de-192">Als u een benoemde locatie stapelt de huidige locatie stack, kunt u de-cmdlets niet meer gebruiken `Push-Location` `Pop-Location` om items toe te voegen aan of te ontvangen van de standaard stack of gebruikt u de `Get-Location` cmdlet om de locaties in de niet-benoemde stack weer te geven.</span><span class="sxs-lookup"><span data-stu-id="000de-192">If you make a named location stack the current location stack, you can no longer use the `Push-Location` or `Pop-Location` cmdlets to add or get items from the default stack or use the `Get-Location` cmdlet to display the locations in the unnamed stack.</span></span> <span data-ttu-id="000de-193">Gebruik de para meter van de **stack** naam van de `Set-Location` cmdlet met een waarde van `$null` of een lege teken reeks () om de ongewijzigde stack de huidige stack te maken `""` .</span><span class="sxs-lookup"><span data-stu-id="000de-193">To make the unnamed stack the current stack, use the **StackName** parameter of the `Set-Location` cmdlet with a value of `$null` or an empty string (`""`).</span></span>

<span data-ttu-id="000de-194">U kunt ook verwijzen naar `Push-Location` de ingebouwde alias `pushd` .</span><span class="sxs-lookup"><span data-stu-id="000de-194">You can also refer to `Push-Location` by its built-in alias, `pushd`.</span></span> <span data-ttu-id="000de-195">Zie [about_Aliases](../Microsoft.PowerShell.Core/About/about_Aliases.md)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="000de-195">For more information, see [about_Aliases](../Microsoft.PowerShell.Core/About/about_Aliases.md).</span></span>

<span data-ttu-id="000de-196">De `Push-Location` cmdlet is ontworpen om te werken met de gegevens die door elke provider worden weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="000de-196">The `Push-Location` cmdlet is designed to work with the data exposed by any provider.</span></span> <span data-ttu-id="000de-197">Als u een lijst wilt weer geven van de providers die beschikbaar zijn in uw sessie, typt u `Get-PSProvider` .</span><span class="sxs-lookup"><span data-stu-id="000de-197">To list the providers available in your session, type `Get-PSProvider`.</span></span> <span data-ttu-id="000de-198">Zie [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="000de-198">For more information, see [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md).</span></span>

## <span data-ttu-id="000de-199">GERELATEERDE KOPPELINGEN</span><span class="sxs-lookup"><span data-stu-id="000de-199">RELATED LINKS</span></span>

[<span data-ttu-id="000de-200">Get-locatie</span><span class="sxs-lookup"><span data-stu-id="000de-200">Get-Location</span></span>](Get-Location.md)

[<span data-ttu-id="000de-201">Pop-locatie</span><span class="sxs-lookup"><span data-stu-id="000de-201">Pop-Location</span></span>](Pop-Location.md)

[<span data-ttu-id="000de-202">Set-Location</span><span class="sxs-lookup"><span data-stu-id="000de-202">Set-Location</span></span>](Set-Location.md)

[<span data-ttu-id="000de-203">about_Aliases</span><span class="sxs-lookup"><span data-stu-id="000de-203">about_Aliases</span></span>](../Microsoft.PowerShell.Core/About/about_Aliases.md)

[<span data-ttu-id="000de-204">about_Providers</span><span class="sxs-lookup"><span data-stu-id="000de-204">about_Providers</span></span>](../Microsoft.PowerShell.Core/About/about_Providers.md)
