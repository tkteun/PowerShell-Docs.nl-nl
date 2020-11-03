---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 02/04/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/set-location?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Set-Location
ms.openlocfilehash: 06b1596366c9c9e20857b55aa9a17342bab07028
ms.sourcegitcommit: fe1e20f8523e3663d68546093aaf3670182337b8
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 08/14/2020
ms.locfileid: "93251821"
---
# <span data-ttu-id="edfc1-103">Set-Location</span><span class="sxs-lookup"><span data-stu-id="edfc1-103">Set-Location</span></span>

## <span data-ttu-id="edfc1-104">SAMENVATTING</span><span class="sxs-lookup"><span data-stu-id="edfc1-104">SYNOPSIS</span></span>
<span data-ttu-id="edfc1-105">Hiermee stelt u de huidige werk locatie in op een opgegeven locatie.</span><span class="sxs-lookup"><span data-stu-id="edfc1-105">Sets the current working location to a specified location.</span></span>

## <span data-ttu-id="edfc1-106">SYNTAXIS</span><span class="sxs-lookup"><span data-stu-id="edfc1-106">SYNTAX</span></span>

### <span data-ttu-id="edfc1-107">Pad (standaard)</span><span class="sxs-lookup"><span data-stu-id="edfc1-107">Path (Default)</span></span>

```
Set-Location [[-Path] <String>] [-PassThru] [-UseTransaction] [<CommonParameters>]
```

### <span data-ttu-id="edfc1-108">LiteralPath</span><span class="sxs-lookup"><span data-stu-id="edfc1-108">LiteralPath</span></span>

```
Set-Location -LiteralPath <String> [-PassThru] [-UseTransaction] [<CommonParameters>]
```

### <span data-ttu-id="edfc1-109">Stack</span><span class="sxs-lookup"><span data-stu-id="edfc1-109">Stack</span></span>

```
Set-Location [-PassThru] [-StackName <String>] [-UseTransaction] [<CommonParameters>]
```

## <span data-ttu-id="edfc1-110">BESCHRIJVING</span><span class="sxs-lookup"><span data-stu-id="edfc1-110">DESCRIPTION</span></span>

<span data-ttu-id="edfc1-111">`Set-Location`Met de cmdlet wordt de werk locatie ingesteld op een opgegeven locatie.</span><span class="sxs-lookup"><span data-stu-id="edfc1-111">The `Set-Location` cmdlet sets the working location to a specified location.</span></span> <span data-ttu-id="edfc1-112">Deze locatie kan een map, een submap, een register locatie of een pad naar de provider zijn.</span><span class="sxs-lookup"><span data-stu-id="edfc1-112">That location could be a directory, a subdirectory, a registry location, or any provider path.</span></span>

<span data-ttu-id="edfc1-113">U kunt ook de para meter ' **stack** naam ' gebruiken om een benoemde locatie van de huidige locatie stack te maken.</span><span class="sxs-lookup"><span data-stu-id="edfc1-113">You can also use the **StackName** parameter to make a named location stack the current location stack.</span></span> <span data-ttu-id="edfc1-114">Zie de opmerkingen voor meer informatie over locatie stacks.</span><span class="sxs-lookup"><span data-stu-id="edfc1-114">For more information about location stacks, see the Notes.</span></span>

## <span data-ttu-id="edfc1-115">VOORBEELDEN</span><span class="sxs-lookup"><span data-stu-id="edfc1-115">EXAMPLES</span></span>

### <span data-ttu-id="edfc1-116">Voor beeld 1: de huidige locatie instellen</span><span class="sxs-lookup"><span data-stu-id="edfc1-116">Example 1: Set the current location</span></span>

```powershell
PS C:\> Set-Location -Path "HKLM:\"
```

```output
PS HKLM:\>
```

<span data-ttu-id="edfc1-117">Met deze opdracht wordt de huidige locatie ingesteld op de hoofdmap van het `HKLM:` station.</span><span class="sxs-lookup"><span data-stu-id="edfc1-117">This command sets the current location to the root of the `HKLM:` drive.</span></span>

### <span data-ttu-id="edfc1-118">Voor beeld 2: de huidige locatie instellen en de locatie weer geven</span><span class="sxs-lookup"><span data-stu-id="edfc1-118">Example 2: Set the current location and display that location</span></span>

```powershell
PS C:\> Set-Location -Path "Env:\" -PassThru
```

```output
Path
----
Env:\

PS Env:\>
```

<span data-ttu-id="edfc1-119">Met deze opdracht wordt de huidige locatie ingesteld op de hoofdmap van het `Env:` station.</span><span class="sxs-lookup"><span data-stu-id="edfc1-119">This command sets the current location to the root of the `Env:` drive.</span></span> <span data-ttu-id="edfc1-120">De para meter **PassThru** wordt gebruikt om Power shell te sturen naar een **PathInfo** -object dat de `Env:\` locatie vertegenwoordigt.</span><span class="sxs-lookup"><span data-stu-id="edfc1-120">It uses the **PassThru** parameter to direct PowerShell to return a **PathInfo** object that represents the `Env:\` location.</span></span>

### <span data-ttu-id="edfc1-121">Voor beeld 3: locatie instellen op de huidige locatie in station C:</span><span class="sxs-lookup"><span data-stu-id="edfc1-121">Example 3: Set location to the current location in the C: drive</span></span>

```powershell
PS C:\Windows\> Set-Location HKLM:\
PS HKLM:\> Set-Location C:
PS C:\Windows\>
```

<span data-ttu-id="edfc1-122">Met de eerste opdracht wordt de locatie ingesteld op de hoofdmap van het `HKLM:` station in de register provider.</span><span class="sxs-lookup"><span data-stu-id="edfc1-122">The first command sets the location to the root of the `HKLM:` drive in the Registry provider.</span></span>
<span data-ttu-id="edfc1-123">Met de tweede opdracht wordt de locatie ingesteld op de huidige locatie van het `C:` station in de File System Provider.</span><span class="sxs-lookup"><span data-stu-id="edfc1-123">The second command sets the location to the current location of the `C:` drive in the FileSystem provider.</span></span>
<span data-ttu-id="edfc1-124">Als de naam van het station is opgegeven in de vorm `<DriveName>:` (zonder back slash), stelt de cmdlet de locatie in op de huidige locatie in de PSDrive.</span><span class="sxs-lookup"><span data-stu-id="edfc1-124">When the drive name is specified in the form `<DriveName>:` (without backslash), the cmdlet sets the location to the current location in the PSDrive.</span></span>
<span data-ttu-id="edfc1-125">Als u de huidige locatie wilt ophalen in de PSDrive use- `Get-Location -PSDrive <DriveName>` opdracht.</span><span class="sxs-lookup"><span data-stu-id="edfc1-125">To get the current location in the PSDrive use `Get-Location -PSDrive <DriveName>` command.</span></span>

### <span data-ttu-id="edfc1-126">Voor beeld 4: de huidige locatie instellen op een benoemde stack</span><span class="sxs-lookup"><span data-stu-id="edfc1-126">Example 4: Set the current location to a named stack</span></span>

```powershell
PS C:\> Push-Location -Path 'C:\Program Files\PowerShell\' -StackName "Paths"
PS C:\Program Files\PowerShell\> Set-Location -StackName "Paths"
PS C:\Program Files\PowerShell\> Get-Location -Stack
```

```Output
Path
----
C:\
```

<span data-ttu-id="edfc1-127">Met de eerste opdracht wordt de huidige locatie toegevoegd aan de paden-stack.</span><span class="sxs-lookup"><span data-stu-id="edfc1-127">The first command adds the current location to the Paths stack.</span></span>
<span data-ttu-id="edfc1-128">Met de tweede opdracht wordt de locatie van de paden stack de huidige locatie stack.</span><span class="sxs-lookup"><span data-stu-id="edfc1-128">The second command makes the Paths location stack the current location stack.</span></span>
<span data-ttu-id="edfc1-129">Met de derde opdracht worden de locaties in de huidige locatie stack weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="edfc1-129">The third command displays the locations in the current location stack.</span></span>

<span data-ttu-id="edfc1-130">De `*-Location` cmdlets gebruiken de huidige locatie stack, tenzij er een andere locatie stack is opgegeven in de opdracht.</span><span class="sxs-lookup"><span data-stu-id="edfc1-130">The `*-Location` cmdlets use the current location stack unless a different location stack is specified in the command.</span></span> <span data-ttu-id="edfc1-131">Zie de [opmerkingen](#notes)voor informatie over locatie stacks.</span><span class="sxs-lookup"><span data-stu-id="edfc1-131">For information about location stacks, see the [Notes](#notes).</span></span>

## <span data-ttu-id="edfc1-132">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="edfc1-132">PARAMETERS</span></span>

### <span data-ttu-id="edfc1-133">-LiteralPath</span><span class="sxs-lookup"><span data-stu-id="edfc1-133">-LiteralPath</span></span>

<span data-ttu-id="edfc1-134">Hiermee geeft u een pad naar de locatie.</span><span class="sxs-lookup"><span data-stu-id="edfc1-134">Specifies a path of the location.</span></span> <span data-ttu-id="edfc1-135">De waarde van de para meter **LiteralPath** wordt precies zo gebruikt als deze wordt getypt.</span><span class="sxs-lookup"><span data-stu-id="edfc1-135">The value of the **LiteralPath** parameter is used exactly as it is typed.</span></span> <span data-ttu-id="edfc1-136">Er worden geen tekens geïnterpreteerd als joker tekens.</span><span class="sxs-lookup"><span data-stu-id="edfc1-136">No characters are interpreted as wildcard characters.</span></span> <span data-ttu-id="edfc1-137">Als het pad escape tekens bevat, plaatst u het tussen enkele aanhalings tekens.</span><span class="sxs-lookup"><span data-stu-id="edfc1-137">If the path includes escape characters, enclose it in single quotation marks.</span></span> <span data-ttu-id="edfc1-138">Enkele aanhalings tekens geven aan dat Power shell geen karakters interpreteert als escape reeksen.</span><span class="sxs-lookup"><span data-stu-id="edfc1-138">Single quotation marks tell PowerShell not to interpret any characters as escape sequences.</span></span>

<span data-ttu-id="edfc1-139">Enkele aanhalings tekens geven aan dat Windows Power shell geen tekens interpreteert als escape reeksen.</span><span class="sxs-lookup"><span data-stu-id="edfc1-139">Single quotation marks tell Windows PowerShell not to interpret any characters as escape sequences.</span></span>

```yaml
Type: System.String
Parameter Sets: LiteralPath
Aliases: PSPath

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="edfc1-140">-PassThru</span><span class="sxs-lookup"><span data-stu-id="edfc1-140">-PassThru</span></span>

<span data-ttu-id="edfc1-141">Retourneert een **PathInfo** -object dat de locatie vertegenwoordigt.</span><span class="sxs-lookup"><span data-stu-id="edfc1-141">Returns a **PathInfo** object that represents the location.</span></span> <span data-ttu-id="edfc1-142">Deze cmdlet genereert standaard geen uitvoer.</span><span class="sxs-lookup"><span data-stu-id="edfc1-142">By default, this cmdlet does not generate any output.</span></span>

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

### <span data-ttu-id="edfc1-143">-Path</span><span class="sxs-lookup"><span data-stu-id="edfc1-143">-Path</span></span>

<span data-ttu-id="edfc1-144">Geef het pad op van een nieuwe werk locatie.</span><span class="sxs-lookup"><span data-stu-id="edfc1-144">Specify the path of a new working location.</span></span> <span data-ttu-id="edfc1-145">Als u geen pad opgeeft, wordt `Set-Location` standaard de basismap van de huidige gebruiker gebruikt.</span><span class="sxs-lookup"><span data-stu-id="edfc1-145">If no path is provided, `Set-Location` defaults to the current user's home directory.</span></span> <span data-ttu-id="edfc1-146">Wanneer joker tekens worden gebruikt, kiest de cmdlet het eerste pad dat overeenkomt met het Joker teken patroon.</span><span class="sxs-lookup"><span data-stu-id="edfc1-146">When wildcards are used, the cmdlet chooses the first path that matches the wildcard pattern.</span></span>

```yaml
Type: System.String
Parameter Sets: Path
Aliases:

Required: False
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: True
```

### <span data-ttu-id="edfc1-147">-Stacknaam</span><span class="sxs-lookup"><span data-stu-id="edfc1-147">-StackName</span></span>

<span data-ttu-id="edfc1-148">Hiermee geeft u de naam van de bestaande locatie stapel op die met deze cmdlet de huidige locatie stack maakt.</span><span class="sxs-lookup"><span data-stu-id="edfc1-148">Specifies the existing location stack name that this cmdlet makes the current location stack.</span></span> <span data-ttu-id="edfc1-149">Voer de naam van de locatie stack in.</span><span class="sxs-lookup"><span data-stu-id="edfc1-149">Enter a location stack name.</span></span> <span data-ttu-id="edfc1-150">Typ `$null` of een lege teken reeks () om de niet-naam standaard locatie stack aan te duiden `""` .</span><span class="sxs-lookup"><span data-stu-id="edfc1-150">To indicate the unnamed default location stack, type `$null` or an empty string (`""`).</span></span>

<span data-ttu-id="edfc1-151">De `*-Location` cmdlets handelen op de huidige stack, tenzij u de para meter van de **stacknaam** gebruikt om een andere stack op te geven.</span><span class="sxs-lookup"><span data-stu-id="edfc1-151">The `*-Location` cmdlets act on the current stack unless you use the **StackName** parameter to specify a different stack.</span></span>

```yaml
Type: System.String
Parameter Sets: Stack
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="edfc1-152">-UseTransaction</span><span class="sxs-lookup"><span data-stu-id="edfc1-152">-UseTransaction</span></span>

<span data-ttu-id="edfc1-153">Hiermee wordt de opdracht opgenomen in de actieve transactie.</span><span class="sxs-lookup"><span data-stu-id="edfc1-153">Includes the command in the active transaction.</span></span>
<span data-ttu-id="edfc1-154">Deze parameter is alleen geldig wanneer een transactie wordt uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="edfc1-154">This parameter is valid only when a transaction is in progress.</span></span>
<span data-ttu-id="edfc1-155">Zie about_Transactions voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="edfc1-155">For more information, see about_Transactions.</span></span>

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

### <span data-ttu-id="edfc1-156">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="edfc1-156">CommonParameters</span></span>

<span data-ttu-id="edfc1-157">Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="edfc1-157">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="edfc1-158">Zie [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="edfc1-158">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="edfc1-159">INVOER</span><span class="sxs-lookup"><span data-stu-id="edfc1-159">INPUTS</span></span>

### <span data-ttu-id="edfc1-160">System. String</span><span class="sxs-lookup"><span data-stu-id="edfc1-160">System.String</span></span>

<span data-ttu-id="edfc1-161">U kunt een teken reeks die een pad bevat, maar geen letterlijk pad, naar deze cmdlet pipet.</span><span class="sxs-lookup"><span data-stu-id="edfc1-161">You can pipe a string that contains a path, but not a literal path, to this cmdlet.</span></span>

## <span data-ttu-id="edfc1-162">UITVOER</span><span class="sxs-lookup"><span data-stu-id="edfc1-162">OUTPUTS</span></span>

### <span data-ttu-id="edfc1-163">Geen, System. Management. Automation. PathInfo, System. Management. Automation. PathInfoStack</span><span class="sxs-lookup"><span data-stu-id="edfc1-163">None, System.Management.Automation.PathInfo, System.Management.Automation.PathInfoStack</span></span>

<span data-ttu-id="edfc1-164">Met deze cmdlet wordt geen uitvoer gegenereerd tenzij u de para meter **PassThru** opgeeft.</span><span class="sxs-lookup"><span data-stu-id="edfc1-164">This cmdlet does not generate any output unless you specify the **PassThru** parameter.</span></span> <span data-ttu-id="edfc1-165">Met behulp van **PassThru** met **Path** of **LiteralPath** wordt een **PathInfo** -object gegenereerd dat de nieuwe locatie vertegenwoordigt.</span><span class="sxs-lookup"><span data-stu-id="edfc1-165">Using **PassThru** with **Path** or **LiteralPath** generates a **PathInfo** object that represents the new location.</span></span> <span data-ttu-id="edfc1-166">Het gebruik van **PassThru** met de **stack** naam genereert een **PathInfoStack** -object dat de nieuwe stack context vertegenwoordigt.</span><span class="sxs-lookup"><span data-stu-id="edfc1-166">Using **PassThru** with **StackName** generates a **PathInfoStack** object representing the new stack context.</span></span>

## <span data-ttu-id="edfc1-167">OPMERKINGEN</span><span class="sxs-lookup"><span data-stu-id="edfc1-167">NOTES</span></span>

<span data-ttu-id="edfc1-168">Power shell ondersteunt meerdere runspaces per proces.</span><span class="sxs-lookup"><span data-stu-id="edfc1-168">PowerShell supports multiple runspaces per process.</span></span> <span data-ttu-id="edfc1-169">Elke runs Pace heeft zijn eigen _huidige map_.</span><span class="sxs-lookup"><span data-stu-id="edfc1-169">Each runspace has its own _current directory_.</span></span>
<span data-ttu-id="edfc1-170">Dit is niet hetzelfde als `[System.Environment]::CurrentDirectory` .</span><span class="sxs-lookup"><span data-stu-id="edfc1-170">This is not the same as `[System.Environment]::CurrentDirectory`.</span></span> <span data-ttu-id="edfc1-171">Dit gedrag kan een probleem zijn bij het aanroepen van .NET-Api's of het uitvoeren van systeem eigen toepassingen zonder expliciete mappaden te bieden.</span><span class="sxs-lookup"><span data-stu-id="edfc1-171">This behavior can be an issue when calling .NET APIs or running native applications without providing explicit directory paths.</span></span>

<span data-ttu-id="edfc1-172">Zelfs als de locatie-cmdlets de huidige map voor het gehele proces hebben ingesteld, kunt u er niet op vertrouwen, omdat deze op elk gewenst moment door een andere runs Pace kan worden gewijzigd.</span><span class="sxs-lookup"><span data-stu-id="edfc1-172">Even if the location cmdlets did set the process-wide current directory, you can't depend on it because another runspace might change it at any time.</span></span> <span data-ttu-id="edfc1-173">U moet de locatie-cmdlets gebruiken om op paden gebaseerde bewerkingen uit te voeren op basis van de huidige werkmap die specifiek is voor de huidige-runs Pace.</span><span class="sxs-lookup"><span data-stu-id="edfc1-173">You should use the location cmdlets to perform path-based operations using the current working directory specific to the current runspace.</span></span>

<span data-ttu-id="edfc1-174">De `Set-Location` cmdlet is ontworpen om te werken met de gegevens die door elke provider worden weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="edfc1-174">The `Set-Location` cmdlet is designed to work with the data exposed by any provider.</span></span> <span data-ttu-id="edfc1-175">Als u een lijst wilt weer geven van de providers die beschikbaar zijn in uw sessie, typt u `Get-PSProvider` .</span><span class="sxs-lookup"><span data-stu-id="edfc1-175">To list the providers available in your session, type `Get-PSProvider`.</span></span> <span data-ttu-id="edfc1-176">Zie [about_Providers](../Microsoft.PowerShell.Core/about/about_Providers.md)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="edfc1-176">For more information, see [about_Providers](../Microsoft.PowerShell.Core/about/about_Providers.md).</span></span>

<span data-ttu-id="edfc1-177">Een stack is een laatste-in-lijst waarin alleen het laatst toegevoegde item kan worden geopend.</span><span class="sxs-lookup"><span data-stu-id="edfc1-177">A stack is a last-in, first-out list in which only the most recently added item can be accessed.</span></span> <span data-ttu-id="edfc1-178">U voegt items toe aan een stack in de volg orde waarin u ze gebruikt en haalt deze vervolgens op voor gebruik in de omgekeerde volg orde.</span><span class="sxs-lookup"><span data-stu-id="edfc1-178">You add items to a stack in the order that you use them, and then retrieve them for use in the reverse order.</span></span> <span data-ttu-id="edfc1-179">Met Power shell kunt u locatie locaties opslaan in site-stacks.</span><span class="sxs-lookup"><span data-stu-id="edfc1-179">PowerShell lets you store provider locations in location stacks.</span></span> <span data-ttu-id="edfc1-180">Power Shell maakt een niet-genaamde standaard locatie van de stack.</span><span class="sxs-lookup"><span data-stu-id="edfc1-180">PowerShell creates an unnamed default location stack.</span></span> <span data-ttu-id="edfc1-181">U kunt meerdere benoemde locatie stapels maken.</span><span class="sxs-lookup"><span data-stu-id="edfc1-181">You can create multiple named location stacks.</span></span> <span data-ttu-id="edfc1-182">Als u geen stack naam opgeeft, gebruikt Power shell de huidige locatie stack.</span><span class="sxs-lookup"><span data-stu-id="edfc1-182">If you do not specify a stack name, PowerShell uses the current location stack.</span></span> <span data-ttu-id="edfc1-183">Standaard is de niet-naam standaard locatie de huidige locatie stack, maar u kunt de `Set-Location` cmdlet gebruiken om de huidige locatie stack te wijzigen.</span><span class="sxs-lookup"><span data-stu-id="edfc1-183">By default, the unnamed default location is the current location stack, but you can use the `Set-Location` cmdlet to change the current location stack.</span></span>

<span data-ttu-id="edfc1-184">Als u locatie stacks wilt beheren, gebruikt u de `*-Location` -cmdlets, als volgt:</span><span class="sxs-lookup"><span data-stu-id="edfc1-184">To manage location stacks, use the `*-Location` cmdlets, as follows:</span></span>

- <span data-ttu-id="edfc1-185">Gebruik de cmdlet om een locatie aan een locatie stack toe te voegen `Push-Location` .</span><span class="sxs-lookup"><span data-stu-id="edfc1-185">To add a location to a location stack, use the `Push-Location` cmdlet.</span></span>

- <span data-ttu-id="edfc1-186">Als u een locatie wilt ophalen uit een locatie stack, gebruikt u de `Pop-Location` cmdlet.</span><span class="sxs-lookup"><span data-stu-id="edfc1-186">To get a location from a location stack, use the `Pop-Location` cmdlet.</span></span>

- <span data-ttu-id="edfc1-187">Als u de locaties wilt weer geven in de huidige locatie stack, gebruikt u de para meter **stack** van de `Get-Location` cmdlet.</span><span class="sxs-lookup"><span data-stu-id="edfc1-187">To display the locations in the current location stack, use the **Stack** parameter of the `Get-Location` cmdlet.</span></span> <span data-ttu-id="edfc1-188">Als u de locaties wilt weer geven in een benoemde locatie stack, gebruikt u de para meter ' **stack** naam ' van `Get-Location` .</span><span class="sxs-lookup"><span data-stu-id="edfc1-188">To display the locations in a named location stack, use the **StackName** parameter of `Get-Location`.</span></span>

- <span data-ttu-id="edfc1-189">Als u een nieuwe locatie stapel wilt maken, gebruikt u de para meter ' **stacknaam** ' van `Push-Location` .</span><span class="sxs-lookup"><span data-stu-id="edfc1-189">To create a new location stack, use the **StackName** parameter of `Push-Location`.</span></span> <span data-ttu-id="edfc1-190">Als u een stack opgeeft die niet bestaat, `Push-Location` maakt de stack.</span><span class="sxs-lookup"><span data-stu-id="edfc1-190">If you specify a stack that does not exist, `Push-Location` creates the stack.</span></span>

- <span data-ttu-id="edfc1-191">Als u een locatie wilt stapelen de huidige locatie stack, gebruikt u de para meter ' **stacknaam** ' van `Set-Location` .</span><span class="sxs-lookup"><span data-stu-id="edfc1-191">To make a location stack the current location stack, use the **StackName** parameter of `Set-Location`.</span></span>

<span data-ttu-id="edfc1-192">De niet-genaamde standaard locatie stack is alleen volledig toegankelijk wanneer het de huidige locatie-stack is.</span><span class="sxs-lookup"><span data-stu-id="edfc1-192">The unnamed default location stack is fully accessible only when it is the current location stack.</span></span>
<span data-ttu-id="edfc1-193">Als u een benoemde locatie stapelt de huidige locatie stack, kunt u de-cmdlets niet meer gebruiken `Push-Location` `Pop-Location` om items toe te voegen aan of te ontvangen van de standaard stack of gebruikt u de `Get-Location` cmdlet om de locaties in de niet-benoemde stack weer te geven.</span><span class="sxs-lookup"><span data-stu-id="edfc1-193">If you make a named location stack the current location stack, you can no longer use the `Push-Location` or `Pop-Location` cmdlets to add or get items from the default stack or use the `Get-Location` cmdlet to display the locations in the unnamed stack.</span></span> <span data-ttu-id="edfc1-194">Gebruik de para meter van de **stack** naam van de `Set-Location` cmdlet met een waarde van `$null` of een lege teken reeks () om de ongewijzigde stack de huidige stack te maken `""` .</span><span class="sxs-lookup"><span data-stu-id="edfc1-194">To make the unnamed stack the current stack, use the **StackName** parameter of the `Set-Location` cmdlet with a value of `$null` or an empty string (`""`).</span></span>

## <span data-ttu-id="edfc1-195">GERELATEERDE KOPPELINGEN</span><span class="sxs-lookup"><span data-stu-id="edfc1-195">RELATED LINKS</span></span>

[<span data-ttu-id="edfc1-196">Get-locatie</span><span class="sxs-lookup"><span data-stu-id="edfc1-196">Get-Location</span></span>](Get-Location.md)

[<span data-ttu-id="edfc1-197">Pop-locatie</span><span class="sxs-lookup"><span data-stu-id="edfc1-197">Pop-Location</span></span>](Pop-Location.md)

[<span data-ttu-id="edfc1-198">Push-locatie</span><span class="sxs-lookup"><span data-stu-id="edfc1-198">Push-Location</span></span>](Push-Location.md)
