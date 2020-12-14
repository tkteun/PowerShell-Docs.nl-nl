---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 02/04/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/set-location?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Set-Location
ms.openlocfilehash: ec6f69d1d4a0b382ceec26b9409d01501edb814f
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 11/17/2020
ms.locfileid: "94706031"
---
# <span data-ttu-id="f7e1f-102">Set-Location</span><span class="sxs-lookup"><span data-stu-id="f7e1f-102">Set-Location</span></span>

## <span data-ttu-id="f7e1f-103">SAMENVATTING</span><span class="sxs-lookup"><span data-stu-id="f7e1f-103">SYNOPSIS</span></span>
<span data-ttu-id="f7e1f-104">Hiermee stelt u de huidige werk locatie in op een opgegeven locatie.</span><span class="sxs-lookup"><span data-stu-id="f7e1f-104">Sets the current working location to a specified location.</span></span>

## <span data-ttu-id="f7e1f-105">SYNTAXIS</span><span class="sxs-lookup"><span data-stu-id="f7e1f-105">SYNTAX</span></span>

### <span data-ttu-id="f7e1f-106">Pad (standaard)</span><span class="sxs-lookup"><span data-stu-id="f7e1f-106">Path (Default)</span></span>

```
Set-Location [[-Path] <String>] [-PassThru] [<CommonParameters>]
```

### <span data-ttu-id="f7e1f-107">LiteralPath</span><span class="sxs-lookup"><span data-stu-id="f7e1f-107">LiteralPath</span></span>

```
Set-Location -LiteralPath <String> [-PassThru] [<CommonParameters>]
```

### <span data-ttu-id="f7e1f-108">Stack</span><span class="sxs-lookup"><span data-stu-id="f7e1f-108">Stack</span></span>

```
Set-Location [-PassThru] [-StackName <String>] [<CommonParameters>]
```

## <span data-ttu-id="f7e1f-109">BESCHRIJVING</span><span class="sxs-lookup"><span data-stu-id="f7e1f-109">DESCRIPTION</span></span>

<span data-ttu-id="f7e1f-110">`Set-Location`Met de cmdlet wordt de werk locatie ingesteld op een opgegeven locatie.</span><span class="sxs-lookup"><span data-stu-id="f7e1f-110">The `Set-Location` cmdlet sets the working location to a specified location.</span></span> <span data-ttu-id="f7e1f-111">Deze locatie kan een map, een submap, een register locatie of een pad naar de provider zijn.</span><span class="sxs-lookup"><span data-stu-id="f7e1f-111">That location could be a directory, a subdirectory, a registry location, or any provider path.</span></span>

<span data-ttu-id="f7e1f-112">Power shell 6,2 heeft ondersteuning toegevoegd voor `-` en `+` als waarde voor de para meter **Path** .</span><span class="sxs-lookup"><span data-stu-id="f7e1f-112">PowerShell 6.2 added support for `-` and `+` as a values for the **Path** parameter.</span></span> <span data-ttu-id="f7e1f-113">Power shell houdt een geschiedenis bij van de laatste 20 locaties die kunnen worden gebruikt met `-` en `+` .</span><span class="sxs-lookup"><span data-stu-id="f7e1f-113">PowerShell maintains a history of the last 20 locations that can be accessed with `-` and `+`.</span></span> <span data-ttu-id="f7e1f-114">Deze lijst is onafhankelijk van de locatie stack die wordt geopend met behulp van de para meter ' **stacknaam** '.</span><span class="sxs-lookup"><span data-stu-id="f7e1f-114">This list is independent from the location stack that is accessed using the **StackName** parameter.</span></span>

## <span data-ttu-id="f7e1f-115">VOORBEELDEN</span><span class="sxs-lookup"><span data-stu-id="f7e1f-115">EXAMPLES</span></span>

### <span data-ttu-id="f7e1f-116">Voor beeld 1: de huidige locatie instellen</span><span class="sxs-lookup"><span data-stu-id="f7e1f-116">Example 1: Set the current location</span></span>

```
PS C:\> Set-Location -Path "HKLM:\"
PS HKLM:\>
```

<span data-ttu-id="f7e1f-117">Met deze opdracht wordt de huidige locatie ingesteld op de hoofdmap van het `HKLM:` station.</span><span class="sxs-lookup"><span data-stu-id="f7e1f-117">This command sets the current location to the root of the `HKLM:` drive.</span></span>

### <span data-ttu-id="f7e1f-118">Voor beeld 2: de huidige locatie instellen en de locatie weer geven</span><span class="sxs-lookup"><span data-stu-id="f7e1f-118">Example 2: Set the current location and display that location</span></span>

```
PS C:\> Set-Location -Path "Env:\" -PassThru
```

```Output
Path
----
Env:\

PS Env:\>
```

<span data-ttu-id="f7e1f-119">Met deze opdracht wordt de huidige locatie ingesteld op de hoofdmap van het `Env:` station.</span><span class="sxs-lookup"><span data-stu-id="f7e1f-119">This command sets the current location to the root of the `Env:` drive.</span></span> <span data-ttu-id="f7e1f-120">De para meter **PassThru** wordt gebruikt om Power shell te sturen naar een **PathInfo** -object dat de `Env:\` locatie vertegenwoordigt.</span><span class="sxs-lookup"><span data-stu-id="f7e1f-120">It uses the **PassThru** parameter to direct PowerShell to return a **PathInfo** object that represents the `Env:\` location.</span></span>

### <span data-ttu-id="f7e1f-121">Voor beeld 3: locatie instellen op de huidige locatie in station C:</span><span class="sxs-lookup"><span data-stu-id="f7e1f-121">Example 3: Set location to the current location in the C: drive</span></span>

```powershell
PS C:\Windows\> Set-Location HKLM:\
PS HKLM:\> Set-Location C:
PS C:\Windows\>
```

<span data-ttu-id="f7e1f-122">Met de eerste opdracht wordt de locatie ingesteld op de hoofdmap van het `HKLM:` station in de register provider.</span><span class="sxs-lookup"><span data-stu-id="f7e1f-122">The first command sets the location to the root of the `HKLM:` drive in the Registry provider.</span></span>
<span data-ttu-id="f7e1f-123">Met de tweede opdracht wordt de locatie ingesteld op de huidige locatie van het `C:` station in de File System Provider.</span><span class="sxs-lookup"><span data-stu-id="f7e1f-123">The second command sets the location to the current location of the `C:` drive in the FileSystem provider.</span></span>
<span data-ttu-id="f7e1f-124">Als de naam van het station is opgegeven in de vorm `<DriveName>:` (zonder back slash), stelt de cmdlet de locatie in op de huidige locatie in de PSDrive.</span><span class="sxs-lookup"><span data-stu-id="f7e1f-124">When the drive name is specified in the form `<DriveName>:` (without backslash), the cmdlet sets the location to the current location in the PSDrive.</span></span>
<span data-ttu-id="f7e1f-125">Als u de huidige locatie wilt ophalen in de PSDrive use- `Get-Location -PSDrive <DriveName>` opdracht.</span><span class="sxs-lookup"><span data-stu-id="f7e1f-125">To get the current location in the PSDrive use `Get-Location -PSDrive <DriveName>` command.</span></span>

### <span data-ttu-id="f7e1f-126">Voor beeld 4: de huidige locatie instellen op een benoemde stack</span><span class="sxs-lookup"><span data-stu-id="f7e1f-126">Example 4: Set the current location to a named stack</span></span>

```
PS C:\> Push-Location -Path 'C:\Program Files\PowerShell\' -StackName "Paths"
PS C:\Program Files\PowerShell\> Set-Location -StackName "Paths"
PS C:\Program Files\PowerShell\> Get-Location -Stack
```

```Output
Path
----
C:\
```

<span data-ttu-id="f7e1f-127">Met de eerste opdracht wordt de huidige locatie toegevoegd aan de paden-stack.</span><span class="sxs-lookup"><span data-stu-id="f7e1f-127">The first command adds the current location to the Paths stack.</span></span>
<span data-ttu-id="f7e1f-128">Met de tweede opdracht wordt de locatie van de paden stack de huidige locatie stack.</span><span class="sxs-lookup"><span data-stu-id="f7e1f-128">The second command makes the Paths location stack the current location stack.</span></span>
<span data-ttu-id="f7e1f-129">Met de derde opdracht worden de locaties in de huidige locatie stack weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="f7e1f-129">The third command displays the locations in the current location stack.</span></span>

<span data-ttu-id="f7e1f-130">De `*-Location` cmdlets gebruiken de huidige locatie stack, tenzij er een andere locatie stack is opgegeven in de opdracht.</span><span class="sxs-lookup"><span data-stu-id="f7e1f-130">The `*-Location` cmdlets use the current location stack unless a different location stack is specified in the command.</span></span> <span data-ttu-id="f7e1f-131">Zie de [opmerkingen](#notes)voor informatie over locatie stacks.</span><span class="sxs-lookup"><span data-stu-id="f7e1f-131">For information about location stacks, see the [Notes](#notes).</span></span>

### <span data-ttu-id="f7e1f-132">Voor beeld 5: Navigeer naar locatie geschiedenis met `+` of `-`</span><span class="sxs-lookup"><span data-stu-id="f7e1f-132">Example 5: Navigate location history using `+` or `-`</span></span>

```
PS C:\> Set-Location -Path $env:SystemRoot
PS C:\Windows> Set-Location -Path Cert:\
PS Cert:\> Set-Location -Path HKLM:\
PS HKLM:\>

# Navigate back through the history using "-"
PS HKLM:\> Set-Location -Path -
PS Cert:\> Set-Location -Path -
PS C:\Windows>

# Navigate using the Set-Location alias "cd" and the implicit positional Path parameter
PS C:\Windows> cd -
PS C:\> cd +
PS C:\Windows> cd +
PS Cert:\>
```

<span data-ttu-id="f7e1f-133">Met behulp van de alias `cd -` of `cd +` is een eenvoudige manier om door uw locatie geschiedenis te navigeren in uw Terminal.</span><span class="sxs-lookup"><span data-stu-id="f7e1f-133">Using the alias, `cd -` or `cd +` is an easy way to navigate through your location history while in your terminal.</span></span> <span data-ttu-id="f7e1f-134">`-` / `+` Zie de para meter **Path** voor meer informatie over navigeren met.</span><span class="sxs-lookup"><span data-stu-id="f7e1f-134">For more information on navigating with `-`/`+`, see the **Path** parameter.</span></span>

## <span data-ttu-id="f7e1f-135">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="f7e1f-135">PARAMETERS</span></span>

### <span data-ttu-id="f7e1f-136">-LiteralPath</span><span class="sxs-lookup"><span data-stu-id="f7e1f-136">-LiteralPath</span></span>

<span data-ttu-id="f7e1f-137">Hiermee geeft u een pad naar de locatie.</span><span class="sxs-lookup"><span data-stu-id="f7e1f-137">Specifies a path of the location.</span></span> <span data-ttu-id="f7e1f-138">De waarde van de para meter **LiteralPath** wordt precies zo gebruikt als deze wordt getypt.</span><span class="sxs-lookup"><span data-stu-id="f7e1f-138">The value of the **LiteralPath** parameter is used exactly as it is typed.</span></span> <span data-ttu-id="f7e1f-139">Er worden geen tekens geïnterpreteerd als joker tekens.</span><span class="sxs-lookup"><span data-stu-id="f7e1f-139">No characters are interpreted as wildcard characters.</span></span> <span data-ttu-id="f7e1f-140">Als het pad escape tekens bevat, plaatst u het tussen enkele aanhalings tekens.</span><span class="sxs-lookup"><span data-stu-id="f7e1f-140">If the path includes escape characters, enclose it in single quotation marks.</span></span> <span data-ttu-id="f7e1f-141">Enkele aanhalings tekens geven aan dat Power shell geen karakters interpreteert als escape reeksen.</span><span class="sxs-lookup"><span data-stu-id="f7e1f-141">Single quotation marks tell PowerShell not to interpret any characters as escape sequences.</span></span>

```yaml
Type: System.String
Parameter Sets: LiteralPath
Aliases: PSPath, LP

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="f7e1f-142">-PassThru</span><span class="sxs-lookup"><span data-stu-id="f7e1f-142">-PassThru</span></span>

<span data-ttu-id="f7e1f-143">Retourneert een **PathInfo** -object dat de locatie vertegenwoordigt.</span><span class="sxs-lookup"><span data-stu-id="f7e1f-143">Returns a **PathInfo** object that represents the location.</span></span> <span data-ttu-id="f7e1f-144">Deze cmdlet genereert standaard geen uitvoer.</span><span class="sxs-lookup"><span data-stu-id="f7e1f-144">By default, this cmdlet does not generate any output.</span></span>

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

### <span data-ttu-id="f7e1f-145">-Path</span><span class="sxs-lookup"><span data-stu-id="f7e1f-145">-Path</span></span>

<span data-ttu-id="f7e1f-146">Geef het pad op van een nieuwe werk locatie.</span><span class="sxs-lookup"><span data-stu-id="f7e1f-146">Specify the path of a new working location.</span></span> <span data-ttu-id="f7e1f-147">Als u geen pad opgeeft, wordt `Set-Location` standaard de basismap van de huidige gebruiker gebruikt.</span><span class="sxs-lookup"><span data-stu-id="f7e1f-147">If no path is provided, `Set-Location` defaults to the current user's home directory.</span></span> <span data-ttu-id="f7e1f-148">Wanneer joker tekens worden gebruikt, kiest de cmdlet het eerste pad dat overeenkomt met het Joker teken patroon.</span><span class="sxs-lookup"><span data-stu-id="f7e1f-148">When wildcards are used, the cmdlet chooses the first path that matches the wildcard pattern.</span></span>

<span data-ttu-id="f7e1f-149">Power shell houdt een geschiedenis bij van de laatste 20 locaties die u hebt ingesteld.</span><span class="sxs-lookup"><span data-stu-id="f7e1f-149">PowerShell keeps a history of the last 20 locations you have set.</span></span> <span data-ttu-id="f7e1f-150">Als de waarde van de para meter **Path** het `-` teken is, wordt de nieuwe werk locatie de vorige werk locatie in de geschiedenis (als deze bestaat).</span><span class="sxs-lookup"><span data-stu-id="f7e1f-150">If the **Path** parameter value is the `-` character, then the new working location will be the previous working location in history (if it exists).</span></span> <span data-ttu-id="f7e1f-151">Op dezelfde manier geldt dat als de waarde het `+` teken is, de nieuwe werk locatie de volgende werk locatie in de geschiedenis is (indien aanwezig).</span><span class="sxs-lookup"><span data-stu-id="f7e1f-151">Similarly, if the value is the `+` character, then the new working location will be the next working location in history (if it exists).</span></span> <span data-ttu-id="f7e1f-152">Dit is vergelijkbaar met `Pop-Location` en `Push-Location` behalve dat de geschiedenis een lijst is, niet een stack en wordt impliciet gevolgd en niet hand matig wordt gecontroleerd.</span><span class="sxs-lookup"><span data-stu-id="f7e1f-152">This is similar to using `Pop-Location` and `Push-Location` except that the history is a list, not a stack, and is implicitly tracked, not manually controlled.</span></span> <span data-ttu-id="f7e1f-153">Op dit moment is er geen manier om de geschiedenis lijst weer te geven.</span><span class="sxs-lookup"><span data-stu-id="f7e1f-153">Currently, there is no way to view the history list.</span></span>

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

### <span data-ttu-id="f7e1f-154">-Stacknaam</span><span class="sxs-lookup"><span data-stu-id="f7e1f-154">-StackName</span></span>

<span data-ttu-id="f7e1f-155">Hiermee geeft u de naam van de bestaande locatie stapel op die met deze cmdlet de huidige locatie stack maakt.</span><span class="sxs-lookup"><span data-stu-id="f7e1f-155">Specifies the existing location stack name that this cmdlet makes the current location stack.</span></span> <span data-ttu-id="f7e1f-156">Voer de naam van de locatie stack in.</span><span class="sxs-lookup"><span data-stu-id="f7e1f-156">Enter a location stack name.</span></span> <span data-ttu-id="f7e1f-157">Typ `$null` of een lege teken reeks () om de niet-naam standaard locatie stack aan te duiden `""` .</span><span class="sxs-lookup"><span data-stu-id="f7e1f-157">To indicate the unnamed default location stack, type `$null` or an empty string (`""`).</span></span>

<span data-ttu-id="f7e1f-158">De `*-Location` cmdlets handelen op de huidige stack, tenzij u de para meter van de **stacknaam** gebruikt om een andere stack op te geven.</span><span class="sxs-lookup"><span data-stu-id="f7e1f-158">The `*-Location` cmdlets act on the current stack unless you use the **StackName** parameter to specify a different stack.</span></span> <span data-ttu-id="f7e1f-159">Zie de [opmerkingen](#notes)voor meer informatie over locatie stacks.</span><span class="sxs-lookup"><span data-stu-id="f7e1f-159">For more information about location stacks, see the [Notes](#notes).</span></span>

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

### <span data-ttu-id="f7e1f-160">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="f7e1f-160">CommonParameters</span></span>

<span data-ttu-id="f7e1f-161">Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="f7e1f-161">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="f7e1f-162">Zie [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="f7e1f-162">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="f7e1f-163">INVOER</span><span class="sxs-lookup"><span data-stu-id="f7e1f-163">INPUTS</span></span>

### <span data-ttu-id="f7e1f-164">System. String</span><span class="sxs-lookup"><span data-stu-id="f7e1f-164">System.String</span></span>

<span data-ttu-id="f7e1f-165">U kunt een teken reeks die een pad bevat, maar geen letterlijk pad, naar deze cmdlet pipet.</span><span class="sxs-lookup"><span data-stu-id="f7e1f-165">You can pipe a string that contains a path, but not a literal path, to this cmdlet.</span></span>

## <span data-ttu-id="f7e1f-166">UITVOER</span><span class="sxs-lookup"><span data-stu-id="f7e1f-166">OUTPUTS</span></span>

### <span data-ttu-id="f7e1f-167">Geen, System. Management. Automation. PathInfo, System. Management. Automation. PathInfoStack</span><span class="sxs-lookup"><span data-stu-id="f7e1f-167">None, System.Management.Automation.PathInfo, System.Management.Automation.PathInfoStack</span></span>

<span data-ttu-id="f7e1f-168">Met deze cmdlet wordt geen uitvoer gegenereerd tenzij u de para meter **PassThru** opgeeft.</span><span class="sxs-lookup"><span data-stu-id="f7e1f-168">This cmdlet does not generate any output unless you specify the **PassThru** parameter.</span></span> <span data-ttu-id="f7e1f-169">Met behulp van **PassThru** met **Path** of **LiteralPath** wordt een **PathInfo** -object gegenereerd dat de nieuwe locatie vertegenwoordigt.</span><span class="sxs-lookup"><span data-stu-id="f7e1f-169">Using **PassThru** with **Path** or **LiteralPath** generates a **PathInfo** object that represents the new location.</span></span> <span data-ttu-id="f7e1f-170">Het gebruik van **PassThru** met de **stack** naam genereert een **PathInfoStack** -object dat de nieuwe stack context vertegenwoordigt.</span><span class="sxs-lookup"><span data-stu-id="f7e1f-170">Using **PassThru** with **StackName** generates a **PathInfoStack** object representing the new stack context.</span></span>

## <span data-ttu-id="f7e1f-171">OPMERKINGEN</span><span class="sxs-lookup"><span data-stu-id="f7e1f-171">NOTES</span></span>

<span data-ttu-id="f7e1f-172">Power shell ondersteunt meerdere runspaces per proces.</span><span class="sxs-lookup"><span data-stu-id="f7e1f-172">PowerShell supports multiple runspaces per process.</span></span> <span data-ttu-id="f7e1f-173">Elke runs Pace heeft zijn eigen _huidige map_.</span><span class="sxs-lookup"><span data-stu-id="f7e1f-173">Each runspace has its own _current directory_.</span></span>
<span data-ttu-id="f7e1f-174">Dit is niet hetzelfde als `[System.Environment]::CurrentDirectory` .</span><span class="sxs-lookup"><span data-stu-id="f7e1f-174">This is not the same as `[System.Environment]::CurrentDirectory`.</span></span> <span data-ttu-id="f7e1f-175">Dit gedrag kan een probleem zijn bij het aanroepen van .NET-Api's of het uitvoeren van systeem eigen toepassingen zonder expliciete mappaden te bieden.</span><span class="sxs-lookup"><span data-stu-id="f7e1f-175">This behavior can be an issue when calling .NET APIs or running native applications without providing explicit directory paths.</span></span>

<span data-ttu-id="f7e1f-176">Zelfs als de locatie-cmdlets de huidige map voor het gehele proces hebben ingesteld, kunt u er niet op vertrouwen, omdat deze op elk gewenst moment door een andere runs Pace kan worden gewijzigd.</span><span class="sxs-lookup"><span data-stu-id="f7e1f-176">Even if the location cmdlets did set the process-wide current directory, you can't depend on it because another runspace might change it at any time.</span></span> <span data-ttu-id="f7e1f-177">U moet de locatie-cmdlets gebruiken om op paden gebaseerde bewerkingen uit te voeren op basis van de huidige werkmap die specifiek is voor de huidige-runs Pace.</span><span class="sxs-lookup"><span data-stu-id="f7e1f-177">You should use the location cmdlets to perform path-based operations using the current working directory specific to the current runspace.</span></span>

<span data-ttu-id="f7e1f-178">De `Set-Location` cmdlet is ontworpen om te werken met de gegevens die door elke provider worden weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="f7e1f-178">The `Set-Location` cmdlet is designed to work with the data exposed by any provider.</span></span> <span data-ttu-id="f7e1f-179">Als u een lijst wilt weer geven van de providers die beschikbaar zijn in uw sessie, typt u `Get-PSProvider` .</span><span class="sxs-lookup"><span data-stu-id="f7e1f-179">To list the providers available in your session, type `Get-PSProvider`.</span></span> <span data-ttu-id="f7e1f-180">Zie [about_Providers](../Microsoft.PowerShell.Core/about/about_Providers.md)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="f7e1f-180">For more information, see [about_Providers](../Microsoft.PowerShell.Core/about/about_Providers.md).</span></span>

<span data-ttu-id="f7e1f-181">Een stack is een laatste-in-lijst waarin alleen het laatst toegevoegde item kan worden geopend.</span><span class="sxs-lookup"><span data-stu-id="f7e1f-181">A stack is a last-in, first-out list in which only the most recently added item can be accessed.</span></span> <span data-ttu-id="f7e1f-182">U voegt items toe aan een stack in de volg orde waarin u ze gebruikt en haalt deze vervolgens op voor gebruik in de omgekeerde volg orde.</span><span class="sxs-lookup"><span data-stu-id="f7e1f-182">You add items to a stack in the order that you use them, and then retrieve them for use in the reverse order.</span></span> <span data-ttu-id="f7e1f-183">Met Power shell kunt u locatie locaties opslaan in site-stacks.</span><span class="sxs-lookup"><span data-stu-id="f7e1f-183">PowerShell lets you store provider locations in location stacks.</span></span> <span data-ttu-id="f7e1f-184">Power Shell maakt een niet-genaamde standaard locatie van de stack.</span><span class="sxs-lookup"><span data-stu-id="f7e1f-184">PowerShell creates an unnamed default location stack.</span></span> <span data-ttu-id="f7e1f-185">U kunt meerdere benoemde locatie stapels maken.</span><span class="sxs-lookup"><span data-stu-id="f7e1f-185">You can create multiple named location stacks.</span></span> <span data-ttu-id="f7e1f-186">Als u geen stack naam opgeeft, gebruikt Power shell de huidige locatie stack.</span><span class="sxs-lookup"><span data-stu-id="f7e1f-186">If you do not specify a stack name, PowerShell uses the current location stack.</span></span> <span data-ttu-id="f7e1f-187">Standaard is de niet-naam standaard locatie de huidige locatie stack, maar u kunt de `Set-Location` cmdlet gebruiken om de huidige locatie stack te wijzigen.</span><span class="sxs-lookup"><span data-stu-id="f7e1f-187">By default, the unnamed default location is the current location stack, but you can use the `Set-Location` cmdlet to change the current location stack.</span></span>

<span data-ttu-id="f7e1f-188">Als u locatie stacks wilt beheren, gebruikt u de `*-Location` -cmdlets, als volgt:</span><span class="sxs-lookup"><span data-stu-id="f7e1f-188">To manage location stacks, use the `*-Location` cmdlets, as follows:</span></span>

- <span data-ttu-id="f7e1f-189">Gebruik de cmdlet om een locatie aan een locatie stack toe te voegen `Push-Location` .</span><span class="sxs-lookup"><span data-stu-id="f7e1f-189">To add a location to a location stack, use the `Push-Location` cmdlet.</span></span>

- <span data-ttu-id="f7e1f-190">Als u een locatie wilt ophalen uit een locatie stack, gebruikt u de `Pop-Location` cmdlet.</span><span class="sxs-lookup"><span data-stu-id="f7e1f-190">To get a location from a location stack, use the `Pop-Location` cmdlet.</span></span>

- <span data-ttu-id="f7e1f-191">Als u de locaties wilt weer geven in de huidige locatie stack, gebruikt u de para meter **stack** van de `Get-Location` cmdlet.</span><span class="sxs-lookup"><span data-stu-id="f7e1f-191">To display the locations in the current location stack, use the **Stack** parameter of the `Get-Location` cmdlet.</span></span> <span data-ttu-id="f7e1f-192">Als u de locaties wilt weer geven in een benoemde locatie stack, gebruikt u de para meter ' **stack** naam ' van `Get-Location` .</span><span class="sxs-lookup"><span data-stu-id="f7e1f-192">To display the locations in a named location stack, use the **StackName** parameter of `Get-Location`.</span></span>

- <span data-ttu-id="f7e1f-193">Als u een nieuwe locatie stapel wilt maken, gebruikt u de para meter ' **stacknaam** ' van `Push-Location` .</span><span class="sxs-lookup"><span data-stu-id="f7e1f-193">To create a new location stack, use the **StackName** parameter of `Push-Location`.</span></span> <span data-ttu-id="f7e1f-194">Als u een stack opgeeft die niet bestaat, `Push-Location` maakt de stack.</span><span class="sxs-lookup"><span data-stu-id="f7e1f-194">If you specify a stack that does not exist, `Push-Location` creates the stack.</span></span>

- <span data-ttu-id="f7e1f-195">Als u een locatie wilt stapelen de huidige locatie stack, gebruikt u de para meter ' **stacknaam** ' van `Set-Location` .</span><span class="sxs-lookup"><span data-stu-id="f7e1f-195">To make a location stack the current location stack, use the **StackName** parameter of `Set-Location`.</span></span>

<span data-ttu-id="f7e1f-196">De niet-genaamde standaard locatie stack is alleen volledig toegankelijk wanneer het de huidige locatie-stack is.</span><span class="sxs-lookup"><span data-stu-id="f7e1f-196">The unnamed default location stack is fully accessible only when it is the current location stack.</span></span>
<span data-ttu-id="f7e1f-197">Als u een benoemde locatie stapelt de huidige locatie stack, kunt u de-cmdlets niet meer gebruiken `Push-Location` `Pop-Location` om items toe te voegen aan of te ontvangen van de standaard stack of gebruikt u de `Get-Location` cmdlet om de locaties in de niet-benoemde stack weer te geven.</span><span class="sxs-lookup"><span data-stu-id="f7e1f-197">If you make a named location stack the current location stack, you can no longer use the `Push-Location` or `Pop-Location` cmdlets to add or get items from the default stack or use the `Get-Location` cmdlet to display the locations in the unnamed stack.</span></span> <span data-ttu-id="f7e1f-198">Gebruik de para meter van de **stack** naam van de `Set-Location` cmdlet met een waarde van `$null` of een lege teken reeks () om de ongewijzigde stack de huidige stack te maken `""` .</span><span class="sxs-lookup"><span data-stu-id="f7e1f-198">To make the unnamed stack the current stack, use the **StackName** parameter of the `Set-Location` cmdlet with a value of `$null` or an empty string (`""`).</span></span>

## <span data-ttu-id="f7e1f-199">GERELATEERDE KOPPELINGEN</span><span class="sxs-lookup"><span data-stu-id="f7e1f-199">RELATED LINKS</span></span>

[<span data-ttu-id="f7e1f-200">Get-locatie</span><span class="sxs-lookup"><span data-stu-id="f7e1f-200">Get-Location</span></span>](Get-Location.md)

[<span data-ttu-id="f7e1f-201">Pop-locatie</span><span class="sxs-lookup"><span data-stu-id="f7e1f-201">Pop-Location</span></span>](Pop-Location.md)

[<span data-ttu-id="f7e1f-202">Push-locatie</span><span class="sxs-lookup"><span data-stu-id="f7e1f-202">Push-Location</span></span>](Push-Location.md)

