---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 03/12/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/get-location?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-Location
ms.openlocfilehash: 235c775e2da4188213f4eb35612c469947b5e2fc
ms.sourcegitcommit: fe1e20f8523e3663d68546093aaf3670182337b8
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 08/14/2020
ms.locfileid: "93251819"
---
# <span data-ttu-id="168c7-103">Get-Location</span><span class="sxs-lookup"><span data-stu-id="168c7-103">Get-Location</span></span>

## <span data-ttu-id="168c7-104">SAMENVATTING</span><span class="sxs-lookup"><span data-stu-id="168c7-104">SYNOPSIS</span></span>
<span data-ttu-id="168c7-105">Hiermee haalt u informatie op over de huidige werk locatie of een locatie stack.</span><span class="sxs-lookup"><span data-stu-id="168c7-105">Gets information about the current working location or a location stack.</span></span>

## <span data-ttu-id="168c7-106">SYNTAXIS</span><span class="sxs-lookup"><span data-stu-id="168c7-106">SYNTAX</span></span>

### <span data-ttu-id="168c7-107">Locatie (standaard)</span><span class="sxs-lookup"><span data-stu-id="168c7-107">Location (Default)</span></span>

```
Get-Location [-PSProvider <String[]>] [-PSDrive <String[]>] [<CommonParameters>]
```

### <span data-ttu-id="168c7-108">Stack</span><span class="sxs-lookup"><span data-stu-id="168c7-108">Stack</span></span>

```
Get-Location [-Stack] [-StackName <String[]>] [<CommonParameters>]
```

## <span data-ttu-id="168c7-109">BESCHRIJVING</span><span class="sxs-lookup"><span data-stu-id="168c7-109">DESCRIPTION</span></span>

<span data-ttu-id="168c7-110">De `Get-Location` cmdlet haalt een object op dat de huidige map vertegenwoordigt, net als de opdracht Print Directory (PWD).</span><span class="sxs-lookup"><span data-stu-id="168c7-110">The `Get-Location` cmdlet gets an object that represents the current directory, much like the print working directory (pwd) command.</span></span>

<span data-ttu-id="168c7-111">Wanneer u overstapt tussen Power Shell-stations, behoudt Power shell uw locatie in elk station.</span><span class="sxs-lookup"><span data-stu-id="168c7-111">When you move between PowerShell drives, PowerShell retains your location in each drive.</span></span> <span data-ttu-id="168c7-112">U kunt deze cmdlet gebruiken om uw locatie in elk station te vinden.</span><span class="sxs-lookup"><span data-stu-id="168c7-112">You can use this cmdlet to find your location in each drive.</span></span>

<span data-ttu-id="168c7-113">U kunt deze cmdlet gebruiken om de huidige map tijdens runtime op te halen en deze te gebruiken in functies en scripts, zoals in een functie die de huidige map in de Power shell-prompt weergeeft.</span><span class="sxs-lookup"><span data-stu-id="168c7-113">You can use this cmdlet to get the current directory at run time and use it in functions and scripts, such as in a function that displays the current directory in the PowerShell prompt.</span></span>

<span data-ttu-id="168c7-114">U kunt deze cmdlet ook gebruiken om de locaties in een locatie stack weer te geven.</span><span class="sxs-lookup"><span data-stu-id="168c7-114">You can also use this cmdlet to display the locations in a location stack.</span></span> <span data-ttu-id="168c7-115">Zie voor meer informatie de opmerkingen en beschrijvingen van de para meters **stack** en **stack** .</span><span class="sxs-lookup"><span data-stu-id="168c7-115">For more information, see the Notes and the descriptions of the **Stack** and **StackName** parameters.</span></span>

## <span data-ttu-id="168c7-116">VOORBEELDEN</span><span class="sxs-lookup"><span data-stu-id="168c7-116">EXAMPLES</span></span>

### <span data-ttu-id="168c7-117">Voor beeld 1: de huidige locatie van uw station weer geven</span><span class="sxs-lookup"><span data-stu-id="168c7-117">Example 1: Display your current drive location</span></span>

<span data-ttu-id="168c7-118">Met deze opdracht wordt uw locatie in het huidige Power Shell-station weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="168c7-118">This command displays your location in the current PowerShell drive.</span></span>

```powershell
PS C:\Windows> Get-Location
```

```Output
Path
----
C:\Windows
```

<span data-ttu-id="168c7-119">Bijvoorbeeld, als u zich in de `Windows` map van het station bevindt `C:` , wordt het pad naar die map weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="168c7-119">For instance, if you are in the `Windows` directory of the `C:` drive, it displays the path to that directory.</span></span>

### <span data-ttu-id="168c7-120">Voor beeld 2: uw huidige locatie weer geven voor verschillende stations</span><span class="sxs-lookup"><span data-stu-id="168c7-120">Example 2: Display your current location for different drives</span></span>

<span data-ttu-id="168c7-121">In dit voor beeld ziet u hoe `Get-Location` u uw huidige locatie in verschillende Power Shell-stations kunt weer geven.</span><span class="sxs-lookup"><span data-stu-id="168c7-121">This example demonstrates the use of `Get-Location` to display your current location in different PowerShell drives.</span></span> <span data-ttu-id="168c7-122">`Set-Location` wordt gebruikt om de locatie te wijzigen in verschillende paden op verschillende PSDrives.</span><span class="sxs-lookup"><span data-stu-id="168c7-122">`Set-Location` is used to change the location to several different paths on different PSDrives.</span></span>

```powershell
PS C:\> Set-Location C:\Windows
PS C:\Windows> Set-Location HKLM:\Software\Microsoft
PS HKLM:\Software\Microsoft> Set-Location "HKCU:\Control Panel\Input Method"
PS HKCU:\Control Panel\Input Method> Get-Location -PSDrive C

Path
----
C:\Windows

PS HKCU:\Control Panel\Input Method> Get-Location -PSDrive HKLM

Path
----
HKLM:\Software\Microsoft

PS HKCU:\Control Panel\Input Method> Set-Location C:
PS C:\Windows> Get-Location -PSProvider Registry

Path
----
HKCU:\Control Panel\Input Method
```

### <span data-ttu-id="168c7-123">Voor beeld 3: locaties ophalen met stacks</span><span class="sxs-lookup"><span data-stu-id="168c7-123">Example 3: Get locations using stacks</span></span>

<span data-ttu-id="168c7-124">Dit voor beeld laat zien hoe u de **stack** -en **stack** -para meters van `Get-Location` kunt gebruiken om de locaties in de huidige locatie stack en alternatieve locatie stacks weer te geven.</span><span class="sxs-lookup"><span data-stu-id="168c7-124">This example shows how to use the **Stack** and **StackName** parameters of `Get-Location` to list the locations in the current location stack and alternate location stacks.</span></span>

<span data-ttu-id="168c7-125">De `Push-Location` cmdlet wordt gebruikt om te wijzigen in drie verschillende locaties.</span><span class="sxs-lookup"><span data-stu-id="168c7-125">The `Push-Location` cmdlet is used to change into three different locations.</span></span> <span data-ttu-id="168c7-126">De derde push maakt gebruik van een andere stack naam.</span><span class="sxs-lookup"><span data-stu-id="168c7-126">The third push uses a different stack name.</span></span> <span data-ttu-id="168c7-127">Met de **stack** parameter van `Get-Location` wordt de inhoud van de standaard stack weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="168c7-127">The **Stack** parameter of `Get-Location` displays the contents of the default stack.</span></span> <span data-ttu-id="168c7-128">Met de para meter ' **stack** naam `Get-Location` ' wordt de inhoud van de stack weer gegeven `Stack2` .</span><span class="sxs-lookup"><span data-stu-id="168c7-128">The **StackName** parameter of `Get-Location` displays the contents of the stack named `Stack2`.</span></span>

```powershell
PS C:\> Push-Location C:\Windows
PS C:\Windows>Push-Location System32
PS C:\Windows\System32>Push-Location WindowsPowerShell -StackName Stack2
C:\Windows\System32\WindowsPowerShell>Get-Location -Stack

Path
----
C:\Windows
C:\

C:\Windows\System32\WindowsPowerShell>Get-Location -StackName Stack2

Path
----
C:\Windows\System32
```

### <span data-ttu-id="168c7-129">Voor beeld 4: de Power shell-prompt aanpassen</span><span class="sxs-lookup"><span data-stu-id="168c7-129">Example 4: Customize the PowerShell prompt</span></span>

<span data-ttu-id="168c7-130">In dit voor beeld ziet u hoe u de Power shell-prompt aanpast.</span><span class="sxs-lookup"><span data-stu-id="168c7-130">This example shows how to customize the PowerShell prompt.</span></span>

```powershell
PS C:\>
function prompt { 'PowerShell: ' + (Get-Location) + '> '}
PowerShell: C:\>
```

<span data-ttu-id="168c7-131">De functie die de prompt definieert, bevat een `Get-Location` opdracht, die wordt uitgevoerd wanneer de prompt wordt weer gegeven in de-console.</span><span class="sxs-lookup"><span data-stu-id="168c7-131">The function that defines the prompt includes a `Get-Location` command, which is run whenever the prompt appears in the console.</span></span>

<span data-ttu-id="168c7-132">De indeling van de standaard Power shell-prompt wordt gedefinieerd door een speciale functie met de naam `prompt` .</span><span class="sxs-lookup"><span data-stu-id="168c7-132">The format of the default PowerShell prompt is defined by a special function named `prompt`.</span></span> <span data-ttu-id="168c7-133">U kunt de prompt in uw console wijzigen door een nieuwe functie te maken met de naam `prompt` .</span><span class="sxs-lookup"><span data-stu-id="168c7-133">You can change the prompt in your console by creating a new function named `prompt`.</span></span>

<span data-ttu-id="168c7-134">Typ de volgende opdracht om de huidige prompt functie te bekijken: `Get-Content Function:\prompt`</span><span class="sxs-lookup"><span data-stu-id="168c7-134">To see the current prompt function, type the following command: `Get-Content Function:\prompt`</span></span>

## <span data-ttu-id="168c7-135">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="168c7-135">PARAMETERS</span></span>

### <span data-ttu-id="168c7-136">-PSDrive</span><span class="sxs-lookup"><span data-stu-id="168c7-136">-PSDrive</span></span>

<span data-ttu-id="168c7-137">Hiermee wordt de huidige locatie in het opgegeven Power Shell-station opgehaald.</span><span class="sxs-lookup"><span data-stu-id="168c7-137">Gets the current location in the specified PowerShell drive.</span></span>

<span data-ttu-id="168c7-138">Als u bijvoorbeeld zich in het station bevindt `Cert:` , kunt u deze para meter gebruiken om uw huidige locatie in het station te vinden `C:` .</span><span class="sxs-lookup"><span data-stu-id="168c7-138">For instance, if you are in the `Cert:` drive, you can use this parameter to find your current location in the `C:` drive.</span></span>

```yaml
Type: System.String[]
Parameter Sets: Location
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="168c7-139">-PSProvider</span><span class="sxs-lookup"><span data-stu-id="168c7-139">-PSProvider</span></span>

<span data-ttu-id="168c7-140">Hiermee wordt de huidige locatie opgehaald in het station dat wordt ondersteund door de opgegeven Power shell-provider.</span><span class="sxs-lookup"><span data-stu-id="168c7-140">Gets the current location in the drive supported by the specified PowerShell provider.</span></span>
<span data-ttu-id="168c7-141">Als de opgegeven provider meer dan één station ondersteunt, retourneert deze cmdlet de locatie op het meest recent geopende station.</span><span class="sxs-lookup"><span data-stu-id="168c7-141">If the specified provider supports more than one drive, this cmdlet returns the location on the most recently accessed drive.</span></span>

<span data-ttu-id="168c7-142">Als u zich bijvoorbeeld in het station bevindt `C:` , kunt u deze para meter gebruiken om uw huidige locatie te vinden in de stations van de Power shell- **register** provider.</span><span class="sxs-lookup"><span data-stu-id="168c7-142">For example, if you are in the `C:` drive, you can use this parameter to find your current location in the drives of the PowerShell **Registry** provider.</span></span>

```yaml
Type: System.String[]
Parameter Sets: Location
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="168c7-143">-Stack</span><span class="sxs-lookup"><span data-stu-id="168c7-143">-Stack</span></span>

<span data-ttu-id="168c7-144">Geeft aan dat met deze cmdlet de locaties worden weer gegeven die worden toegevoegd aan de huidige locatie stack.</span><span class="sxs-lookup"><span data-stu-id="168c7-144">Indicates that this cmdlet displays the locations added to the current location stack.</span></span> <span data-ttu-id="168c7-145">U kunt locaties toevoegen aan stacks met behulp van de- `Push-Location` cmdlet.</span><span class="sxs-lookup"><span data-stu-id="168c7-145">You can add locations to stacks by using the `Push-Location` cmdlet.</span></span>

<span data-ttu-id="168c7-146">Als u de locaties wilt weer geven in een andere locatie stack, gebruikt u de para meter ' **stacknaam** '.</span><span class="sxs-lookup"><span data-stu-id="168c7-146">To display the locations in a different location stack, use the **StackName** parameter.</span></span> <span data-ttu-id="168c7-147">Zie de [opmerkingen](#notes)voor informatie over locatie stacks.</span><span class="sxs-lookup"><span data-stu-id="168c7-147">For information about location stacks, see the [Notes](#notes).</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: Stack
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="168c7-148">-Stacknaam</span><span class="sxs-lookup"><span data-stu-id="168c7-148">-StackName</span></span>

<span data-ttu-id="168c7-149">Hiermee geeft u als een teken reeks matrix de benoemde locatie stapels op.</span><span class="sxs-lookup"><span data-stu-id="168c7-149">Specifies, as a string array, the named location stacks.</span></span> <span data-ttu-id="168c7-150">Voer een of meer locatie-stack namen in.</span><span class="sxs-lookup"><span data-stu-id="168c7-150">Enter one or more location stack names.</span></span>

<span data-ttu-id="168c7-151">Als u de locaties in de huidige locatie stack wilt weer geven, gebruikt u de **stack** -para meter.</span><span class="sxs-lookup"><span data-stu-id="168c7-151">To display the locations in the current location stack, use the **Stack** parameter.</span></span> <span data-ttu-id="168c7-152">Als u een locatie wilt stapelen de huidige locatie stack, gebruikt u de `Set-Location` cmdlet.</span><span class="sxs-lookup"><span data-stu-id="168c7-152">To make a location stack the current location stack, use the `Set-Location` cmdlet.</span></span>

<span data-ttu-id="168c7-153">Met deze cmdlet kunnen de locaties in de niet-genaamde standaard stack niet worden weer gegeven, tenzij dit de huidige stack is.</span><span class="sxs-lookup"><span data-stu-id="168c7-153">This cmdlet cannot display the locations in the unnamed default stack unless it is the current stack.</span></span>

```yaml
Type: System.String[]
Parameter Sets: Stack
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="168c7-154">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="168c7-154">CommonParameters</span></span>

<span data-ttu-id="168c7-155">Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="168c7-155">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="168c7-156">Zie [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="168c7-156">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="168c7-157">INVOER</span><span class="sxs-lookup"><span data-stu-id="168c7-157">INPUTS</span></span>

### <span data-ttu-id="168c7-158">Geen</span><span class="sxs-lookup"><span data-stu-id="168c7-158">None</span></span>

<span data-ttu-id="168c7-159">U kunt geen invoer van een pipe naar deze cmdlet.</span><span class="sxs-lookup"><span data-stu-id="168c7-159">You cannot pipe input to this cmdlet.</span></span>

## <span data-ttu-id="168c7-160">UITVOER</span><span class="sxs-lookup"><span data-stu-id="168c7-160">OUTPUTS</span></span>

### <span data-ttu-id="168c7-161">System. Management. Automation. PathInfo of System. Management. Automation. PathInfoStack</span><span class="sxs-lookup"><span data-stu-id="168c7-161">System.Management.Automation.PathInfo or System.Management.Automation.PathInfoStack</span></span>

<span data-ttu-id="168c7-162">Als u de **stack** -of para meters voor de **stack** naam gebruikt, retourneert deze cmdlet een **PathInfoStack** -object.</span><span class="sxs-lookup"><span data-stu-id="168c7-162">If you use the **Stack** or **StackName** parameters, this cmdlet returns a **PathInfoStack** object.</span></span> <span data-ttu-id="168c7-163">Anders wordt een **PathInfo** -object geretourneerd.</span><span class="sxs-lookup"><span data-stu-id="168c7-163">Otherwise, it returns a **PathInfo** object.</span></span>

## <span data-ttu-id="168c7-164">OPMERKINGEN</span><span class="sxs-lookup"><span data-stu-id="168c7-164">NOTES</span></span>

<span data-ttu-id="168c7-165">Power shell ondersteunt meerdere runspaces per proces.</span><span class="sxs-lookup"><span data-stu-id="168c7-165">PowerShell supports multiple runspaces per process.</span></span> <span data-ttu-id="168c7-166">Elke runs Pace heeft zijn eigen _huidige map_.</span><span class="sxs-lookup"><span data-stu-id="168c7-166">Each runspace has its own _current directory_.</span></span>
<span data-ttu-id="168c7-167">Dit is niet hetzelfde als `[System.Environment]::CurrentDirectory` .</span><span class="sxs-lookup"><span data-stu-id="168c7-167">This is not the same as `[System.Environment]::CurrentDirectory`.</span></span> <span data-ttu-id="168c7-168">Dit gedrag kan een probleem zijn bij het aanroepen van .NET-Api's of het uitvoeren van systeem eigen toepassingen zonder expliciete mappaden te bieden.</span><span class="sxs-lookup"><span data-stu-id="168c7-168">This behavior can be an issue when calling .NET APIs or running native applications without providing explicit directory paths.</span></span>
<span data-ttu-id="168c7-169">`Get-Location`Met de cmdlet wordt de huidige map van de huidige Power shell-runs Pace geretourneerd.</span><span class="sxs-lookup"><span data-stu-id="168c7-169">The `Get-Location` cmdlet returns the current directory of the current PowerShell runspace.</span></span>

<span data-ttu-id="168c7-170">Deze cmdlet is ontworpen om te werken met de gegevens die door elke provider worden weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="168c7-170">This cmdlet is designed to work with the data exposed by any provider.</span></span> <span data-ttu-id="168c7-171">Typ om de providers in uw sessie weer te geven `Get-PSProvider` .</span><span class="sxs-lookup"><span data-stu-id="168c7-171">To list the providers in your session, type `Get-PSProvider`.</span></span> <span data-ttu-id="168c7-172">Zie [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="168c7-172">For more information, see [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md).</span></span>

<span data-ttu-id="168c7-173">De manieren waarop de **PSProvider** -, **PSDrive** -, **stack** -en **stack** -para meters communiceren, zijn afhankelijk van de provider.</span><span class="sxs-lookup"><span data-stu-id="168c7-173">The ways that the **PSProvider** , **PSDrive** , **Stack** , and **StackName** parameters interact depends on the provider.</span></span> <span data-ttu-id="168c7-174">Sommige combi Naties leiden tot fouten, zoals het opgeven van een station en een provider die dat station niet beschikbaar maakt.</span><span class="sxs-lookup"><span data-stu-id="168c7-174">Some combinations will result in errors, such as specifying both a drive and a provider that does not expose that drive.</span></span> <span data-ttu-id="168c7-175">Als er geen para meters zijn opgegeven, retourneert deze cmdlet het **PathInfo** -object voor de provider die de huidige werk locatie bevat.</span><span class="sxs-lookup"><span data-stu-id="168c7-175">If no parameters are specified, this cmdlet returns the **PathInfo** object for the provider that contains the current working location.</span></span>

<span data-ttu-id="168c7-176">Een stack is een vervolg keuzelijst die het laatst is toegevoegd en die alleen toegankelijk is voor het laatst toegevoegde item.</span><span class="sxs-lookup"><span data-stu-id="168c7-176">A stack is a last-in, first-out list in which only the most recently added item is accessible.</span></span> <span data-ttu-id="168c7-177">U voegt items toe aan een stack in de volg orde waarin u ze gebruikt en haalt deze vervolgens op voor gebruik in de omgekeerde volg orde.</span><span class="sxs-lookup"><span data-stu-id="168c7-177">You add items to a stack in the order that you use them, and then retrieve them for use in the reverse order.</span></span> <span data-ttu-id="168c7-178">Met Power shell kunt u locatie locaties opslaan in site-stacks.</span><span class="sxs-lookup"><span data-stu-id="168c7-178">PowerShell lets you store provider locations in location stacks.</span></span> <span data-ttu-id="168c7-179">In Power shell wordt een niet-benoemde standaard locatie stack gemaakt en u kunt meerdere naam locatie stacks maken.</span><span class="sxs-lookup"><span data-stu-id="168c7-179">PowerShell creates an unnamed default location stack and you can create multiple named location stacks.</span></span> <span data-ttu-id="168c7-180">Als u geen stack naam opgeeft, gebruikt Power shell de huidige locatie stack.</span><span class="sxs-lookup"><span data-stu-id="168c7-180">If you do not specify a stack name, PowerShell uses the current location stack.</span></span> <span data-ttu-id="168c7-181">Standaard is de niet-naam standaard locatie de huidige locatie stack, maar u kunt de `Set-Location` cmdlet gebruiken om de huidige locatie stack te wijzigen.</span><span class="sxs-lookup"><span data-stu-id="168c7-181">By default, the unnamed default location is the current location stack, but you can use the `Set-Location` cmdlet to change the current location stack.</span></span>

<span data-ttu-id="168c7-182">Als u locatie stacks wilt beheren, gebruikt u de Power shell `*-Location` -cmdlets, als volgt.</span><span class="sxs-lookup"><span data-stu-id="168c7-182">To manage location stacks, use the PowerShell `*-Location` cmdlets, as follows.</span></span>

- <span data-ttu-id="168c7-183">Gebruik de cmdlet om een locatie aan een locatie stack toe te voegen `Push-Location` .</span><span class="sxs-lookup"><span data-stu-id="168c7-183">To add a location to a location stack, use the `Push-Location` cmdlet.</span></span>

- <span data-ttu-id="168c7-184">Als u een locatie wilt ophalen uit een locatie stack, gebruikt u de `Pop-Location` cmdlet.</span><span class="sxs-lookup"><span data-stu-id="168c7-184">To get a location from a location stack, use the `Pop-Location` cmdlet.</span></span>

- <span data-ttu-id="168c7-185">Als u de locaties wilt weer geven in de huidige locatie stack, gebruikt u de para meter **stack** van de `Get-Location` cmdlet.</span><span class="sxs-lookup"><span data-stu-id="168c7-185">To display the locations in the current location stack, use the **Stack** parameter of the `Get-Location` cmdlet.</span></span> <span data-ttu-id="168c7-186">Als u de locaties wilt weer geven in een benoemde locatie stack, gebruikt u de para meter ' **stack** naam ' van de `Get-Location` cmdlet.</span><span class="sxs-lookup"><span data-stu-id="168c7-186">To display the locations in a named location stack, use the **StackName** parameter of the `Get-Location` cmdlet.</span></span>

- <span data-ttu-id="168c7-187">Als u een nieuwe locatie stack wilt maken, gebruikt u de para meter ' **stacknaam** ' van de `Push-Location` cmdlet.</span><span class="sxs-lookup"><span data-stu-id="168c7-187">To create a new location stack, use the **StackName** parameter of the `Push-Location` cmdlet.</span></span>
  <span data-ttu-id="168c7-188">Als u een stack opgeeft die niet bestaat, `Push-Location` maakt de stack.</span><span class="sxs-lookup"><span data-stu-id="168c7-188">If you specify a stack that does not exist, `Push-Location` creates the stack.</span></span>

- <span data-ttu-id="168c7-189">Als u wilt dat een locatie stack de huidige locatie stack is, gebruikt u de para meter ' **stacknaam** ' van de `Set-Location` cmdlet.</span><span class="sxs-lookup"><span data-stu-id="168c7-189">To make a location stack the current location stack, use the **StackName** parameter of the `Set-Location` cmdlet.</span></span>

<span data-ttu-id="168c7-190">De niet-genaamde standaard locatie stack is alleen volledig toegankelijk wanneer het de huidige locatie-stack is.</span><span class="sxs-lookup"><span data-stu-id="168c7-190">The unnamed default location stack is fully accessible only when it is the current location stack.</span></span>
<span data-ttu-id="168c7-191">Als u een benoemde locatie stapelt de huidige locatie stack, kunt u de-cmdlets niet meer gebruiken `Push-Location` `Pop-Location` om items toe te voegen aan of te ontvangen van de standaard stack of gebruikt u deze cmdlet om de locaties in de niet-benoemde stack weer te geven.</span><span class="sxs-lookup"><span data-stu-id="168c7-191">If you make a named location stack the current location stack, you can no longer use the `Push-Location` or `Pop-Location` cmdlets to add or get items from the default stack or use this cmdlet to display the locations in the unnamed stack.</span></span> <span data-ttu-id="168c7-192">Gebruik de para meter van de **stack** naam van de `Set-Location` cmdlet met een waarde van `$null` of een lege teken reeks () om de ongewijzigde stack de huidige stack te maken `""` .</span><span class="sxs-lookup"><span data-stu-id="168c7-192">To make the unnamed stack the current stack, use the **StackName** parameter of the `Set-Location` cmdlet with a value of `$null` or an empty string (`""`).</span></span>

## <span data-ttu-id="168c7-193">GERELATEERDE KOPPELINGEN</span><span class="sxs-lookup"><span data-stu-id="168c7-193">RELATED LINKS</span></span>

[<span data-ttu-id="168c7-194">Pop-locatie</span><span class="sxs-lookup"><span data-stu-id="168c7-194">Pop-Location</span></span>](Pop-Location.md)

[<span data-ttu-id="168c7-195">Push-locatie</span><span class="sxs-lookup"><span data-stu-id="168c7-195">Push-Location</span></span>](Push-Location.md)

[<span data-ttu-id="168c7-196">Set-Location</span><span class="sxs-lookup"><span data-stu-id="168c7-196">Set-Location</span></span>](Set-Location.md)
