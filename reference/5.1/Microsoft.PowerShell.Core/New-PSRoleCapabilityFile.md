---
external help file: System.Management.Automation.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 09/11/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/new-psrolecapabilityfile?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: New-PSRoleCapabilityFile
ms.openlocfilehash: 3dca5f922f31690bb78ccc610b4ed44b7423ca47
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/07/2020
ms.locfileid: "93250165"
---
# <span data-ttu-id="029dc-103">New-PSRoleCapabilityFile</span><span class="sxs-lookup"><span data-stu-id="029dc-103">New-PSRoleCapabilityFile</span></span>

## <span data-ttu-id="029dc-104">SAMENVATTING</span><span class="sxs-lookup"><span data-stu-id="029dc-104">SYNOPSIS</span></span>
<span data-ttu-id="029dc-105">Hiermee maakt u een bestand dat een set mogelijkheden definieert die moeten worden weer gegeven via een sessie configuratie.</span><span class="sxs-lookup"><span data-stu-id="029dc-105">Creates a file that defines a set of capabilities to be exposed through a session configuration.</span></span>

## <span data-ttu-id="029dc-106">SYNTAXIS</span><span class="sxs-lookup"><span data-stu-id="029dc-106">SYNTAX</span></span>

```
New-PSRoleCapabilityFile [-Path] <String> [-Guid <Guid>] [-Author <String>] [-Description <String>]
 [-CompanyName <String>] [-Copyright <String>] [-ModulesToImport <Object[]>] [-VisibleAliases <String[]>]
 [-VisibleCmdlets <Object[]>] [-VisibleFunctions <Object[]>] [-VisibleExternalCommands <String[]>]
 [-VisibleProviders <String[]>] [-ScriptsToProcess <String[]>] [-AliasDefinitions <IDictionary[]>]
 [-FunctionDefinitions <IDictionary[]>] [-VariableDefinitions <Object>] [-EnvironmentVariables <IDictionary>]
 [-TypesToProcess <String[]>] [-FormatsToProcess <String[]>] [-AssembliesToLoad <String[]>]
 [<CommonParameters>]
```

## <span data-ttu-id="029dc-107">BESCHRIJVING</span><span class="sxs-lookup"><span data-stu-id="029dc-107">DESCRIPTION</span></span>

<span data-ttu-id="029dc-108">Met de `New-PSRoleCapabilityFile` cmdlet wordt een bestand gemaakt dat een reeks gebruikers mogelijkheden definieert die kunnen worden weer gegeven via sessie configuratie bestanden.</span><span class="sxs-lookup"><span data-stu-id="029dc-108">The `New-PSRoleCapabilityFile` cmdlet creates a file that defines a set of user capabilities that can be exposed through session configuration files.</span></span> <span data-ttu-id="029dc-109">Dit omvat het bepalen van de cmdlets, functies en scripts die beschikbaar zijn voor gebruikers.</span><span class="sxs-lookup"><span data-stu-id="029dc-109">This includes determining which cmdlets, functions, and scripts are available to users.</span></span> <span data-ttu-id="029dc-110">Het Capability-bestand is een bestand met lees bare tekst dat een hash-tabel met eigenschappen en waarden van sessie configuratie bevat.</span><span class="sxs-lookup"><span data-stu-id="029dc-110">The capability file is a human-readable text file that contains a hash table of session configuration properties and values.</span></span> <span data-ttu-id="029dc-111">Het bestand heeft de bestandsnaam extensie. psrc en kan worden gebruikt door meer dan één sessie configuratie.</span><span class="sxs-lookup"><span data-stu-id="029dc-111">The file has a .psrc file name extension, and can be used by more than one session configuration.</span></span>

<span data-ttu-id="029dc-112">Alle para meters van `New-PSRoleCapabilityFile` zijn optioneel, met uitzonde ring van de para meter **Path** , waarmee het bestandspad voor het bestand wordt opgegeven.</span><span class="sxs-lookup"><span data-stu-id="029dc-112">All the parameters of `New-PSRoleCapabilityFile` are optional except for the **Path** parameter, which specifies the file path for the file.</span></span> <span data-ttu-id="029dc-113">Als u geen para meter opneemt tijdens het uitvoeren van de cmdlet, wordt de bijbehorende sleutel in het bestand met de sessie configuratie commentaar gegeven, behalve wanneer vermeld in de parameter beschrijving.</span><span class="sxs-lookup"><span data-stu-id="029dc-113">If you do not include a parameter when you run the cmdlet, the corresponding key in the session configuration file is commented-out, except where noted in the parameter description.</span></span> <span data-ttu-id="029dc-114">Bijvoorbeeld, als u de para meter **AssembliesToLoad** niet opneemt, wordt die sectie van het sessie configuratie bestand uit commentaar genomen.</span><span class="sxs-lookup"><span data-stu-id="029dc-114">For example, if you do not include the **AssembliesToLoad** parameter then that section of the session configuration file is commented out.</span></span>

<span data-ttu-id="029dc-115">Als u het bestand voor de functie wilt gebruiken in een sessie configuratie, plaatst u het bestand eerst in een submap **RoleCapabilities** van een geldige map voor de Power shell-module.</span><span class="sxs-lookup"><span data-stu-id="029dc-115">To use the role capability file in a session configuration, first place the file in a **RoleCapabilities** subfolder of a valid PowerShell module folder.</span></span> <span data-ttu-id="029dc-116">Ga vervolgens naar het bestand met de naam in het veld **RoleDefinitions** in een Power shell-sessie configuratie bestand (. pssc).</span><span class="sxs-lookup"><span data-stu-id="029dc-116">Then reference the file by name in the **RoleDefinitions** field in a PowerShell Session Configuration (.pssc) file.</span></span>

<span data-ttu-id="029dc-117">Deze cmdlet is geïntroduceerd in Windows Power shell 5,0.</span><span class="sxs-lookup"><span data-stu-id="029dc-117">This cmdlet was introduced in Windows PowerShell 5.0.</span></span>

## <span data-ttu-id="029dc-118">VOORBEELDEN</span><span class="sxs-lookup"><span data-stu-id="029dc-118">EXAMPLES</span></span>

### <span data-ttu-id="029dc-119">Voor beeld 1: een functie bestand met een lege rol maken</span><span class="sxs-lookup"><span data-stu-id="029dc-119">Example 1: Create a blank role capability file</span></span>

<span data-ttu-id="029dc-120">In dit voor beeld wordt een nieuw bestand met een functie gemaakt waarin de standaard waarden (leeg) worden gebruikt.</span><span class="sxs-lookup"><span data-stu-id="029dc-120">This example creates a new role capability file that uses the default (blank) values.</span></span> <span data-ttu-id="029dc-121">Het bestand kan later worden bewerkt in een tekst editor om deze configuratie-instellingen te wijzigen.</span><span class="sxs-lookup"><span data-stu-id="029dc-121">The file can later be edited in a text editor to change these configuration settings.</span></span>

```powershell
New-PSRoleCapabilityFile -Path ".\ExampleFile.psrc"
```

### <span data-ttu-id="029dc-122">Voor beeld 2: een functie mogelijkheidsprofiel maken waarmee gebruikers services en een VDI-computer opnieuw kunnen starten</span><span class="sxs-lookup"><span data-stu-id="029dc-122">Example 2: Create a role capability file allowing users to restart services and any VDI computer</span></span>

<span data-ttu-id="029dc-123">In dit voor beeld wordt een mogelijkheidsprofiel gemaakt waarmee gebruikers services en computers die overeenkomen met een specifiek naam patroon, opnieuw kunnen starten.</span><span class="sxs-lookup"><span data-stu-id="029dc-123">This example creates a sample role capability file that enables users to restart services and computers that match a specific name pattern.</span></span> <span data-ttu-id="029dc-124">Naam filtering wordt gedefinieerd door de para meter **ValidatePattern** in te stellen op de reguliere expressie `VDI\d+` .</span><span class="sxs-lookup"><span data-stu-id="029dc-124">Name filtering is defined by setting the **ValidatePattern** parameter to the regular expression `VDI\d+`.</span></span>

```powershell
$roleParameters = @{
    Path = ".\Maintenance.psrc"
    Author = "User01"
    CompanyName = "Fabrikam Corporation"
    Description = "This role enables users to restart any service and restart any VDI computer."
    ModulesToImport = "Microsoft.PowerShell.Core"
    VisibleCmdlets = "Restart-Service", @{
                      Name = "Restart-Computer"
                      Parameters = @{ Name = "ComputerName"; ValidatePattern = "VDI\d+" }
    }
}
New-PSRoleCapabilityFile @roleParameters
```

## <span data-ttu-id="029dc-125">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="029dc-125">PARAMETERS</span></span>

### <span data-ttu-id="029dc-126">-AliasDefinitions</span><span class="sxs-lookup"><span data-stu-id="029dc-126">-AliasDefinitions</span></span>

<span data-ttu-id="029dc-127">Voegt de opgegeven aliassen toe aan sessies die gebruikmaken van het functie-functionaliteits bestand.</span><span class="sxs-lookup"><span data-stu-id="029dc-127">Adds the specified aliases to sessions that use the role capability file.</span></span> <span data-ttu-id="029dc-128">Voer een hash-tabel in met de volgende sleutels:</span><span class="sxs-lookup"><span data-stu-id="029dc-128">Enter a hash table with the following keys:</span></span>

- <span data-ttu-id="029dc-129">Naam.</span><span class="sxs-lookup"><span data-stu-id="029dc-129">Name.</span></span> <span data-ttu-id="029dc-130">De naam van de alias.</span><span class="sxs-lookup"><span data-stu-id="029dc-130">Name of the alias.</span></span> <span data-ttu-id="029dc-131">Deze sleutel is vereist.</span><span class="sxs-lookup"><span data-stu-id="029dc-131">This key is required.</span></span>
- <span data-ttu-id="029dc-132">Waarde.</span><span class="sxs-lookup"><span data-stu-id="029dc-132">Value.</span></span> <span data-ttu-id="029dc-133">De opdracht die wordt vertegenwoordigd door de alias.</span><span class="sxs-lookup"><span data-stu-id="029dc-133">The command that the alias represents.</span></span> <span data-ttu-id="029dc-134">Deze sleutel is vereist.</span><span class="sxs-lookup"><span data-stu-id="029dc-134">This key is required.</span></span>
- <span data-ttu-id="029dc-135">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="029dc-135">Description.</span></span> <span data-ttu-id="029dc-136">Een teken reeks waarmee de alias wordt beschreven.</span><span class="sxs-lookup"><span data-stu-id="029dc-136">A text string that describes the alias.</span></span> <span data-ttu-id="029dc-137">Deze sleutel is optioneel.</span><span class="sxs-lookup"><span data-stu-id="029dc-137">This key is optional.</span></span>
- <span data-ttu-id="029dc-138">Opties.</span><span class="sxs-lookup"><span data-stu-id="029dc-138">Options.</span></span> <span data-ttu-id="029dc-139">Alias opties.</span><span class="sxs-lookup"><span data-stu-id="029dc-139">Alias options.</span></span> <span data-ttu-id="029dc-140">Deze sleutel is optioneel.</span><span class="sxs-lookup"><span data-stu-id="029dc-140">This key is optional.</span></span> <span data-ttu-id="029dc-141">De standaard waarde is geen.</span><span class="sxs-lookup"><span data-stu-id="029dc-141">The default value is None.</span></span> <span data-ttu-id="029dc-142">De acceptabele waarden voor deze para meter zijn: geen, alleen-lezen, constant, privé of AllScope.</span><span class="sxs-lookup"><span data-stu-id="029dc-142">The acceptable values for this parameter are: None, ReadOnly, Constant, Private, or AllScope.</span></span>

<span data-ttu-id="029dc-143">Bijvoorbeeld: `@{Name="hlp";Value="Get-Help";Description="Gets help";Options="ReadOnly"}`</span><span class="sxs-lookup"><span data-stu-id="029dc-143">For example: `@{Name="hlp";Value="Get-Help";Description="Gets help";Options="ReadOnly"}`</span></span>

```yaml
Type: System.Collections.IDictionary[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="029dc-144">-AssembliesToLoad</span><span class="sxs-lookup"><span data-stu-id="029dc-144">-AssembliesToLoad</span></span>

<span data-ttu-id="029dc-145">Hiermee geeft u de assembly's op die moeten worden geladen in de sessies die gebruikmaken van het functie-functionaliteits bestand.</span><span class="sxs-lookup"><span data-stu-id="029dc-145">Specifies the assemblies to load into the sessions that use the role capability file.</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="029dc-146">-Author</span><span class="sxs-lookup"><span data-stu-id="029dc-146">-Author</span></span>

<span data-ttu-id="029dc-147">Hiermee geeft u de gebruiker die het functie bestand heeft gemaakt.</span><span class="sxs-lookup"><span data-stu-id="029dc-147">Specifies the user that created the role capability file.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="029dc-148">-CompanyName</span><span class="sxs-lookup"><span data-stu-id="029dc-148">-CompanyName</span></span>

<span data-ttu-id="029dc-149">Hiermee wordt het bedrijf geïdentificeerd dat het functie gegevensbestand heeft gemaakt.</span><span class="sxs-lookup"><span data-stu-id="029dc-149">Identifies the company that created the role capability file.</span></span>
<span data-ttu-id="029dc-150">De standaard waarde is onbekend.</span><span class="sxs-lookup"><span data-stu-id="029dc-150">The default value is Unknown.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="029dc-151">-Copyright</span><span class="sxs-lookup"><span data-stu-id="029dc-151">-Copyright</span></span>

<span data-ttu-id="029dc-152">Hiermee geeft u een copyright op voor het functie-functionaliteits bestand.</span><span class="sxs-lookup"><span data-stu-id="029dc-152">Specifies a copyright for the role capability file.</span></span> <span data-ttu-id="029dc-153">Als u deze para meter weglaat, `New-PSRoleCapabilityFile` genereert een copyright verklaring met behulp van de waarde van de para meter **Auteur** .</span><span class="sxs-lookup"><span data-stu-id="029dc-153">If you omit this parameter, `New-PSRoleCapabilityFile` generates a copyright statement by using the value of the **Author** parameter.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="029dc-154">-Beschrijving</span><span class="sxs-lookup"><span data-stu-id="029dc-154">-Description</span></span>

<span data-ttu-id="029dc-155">Hiermee geeft u een beschrijving op voor het bestand met de functie mogelijkheid.</span><span class="sxs-lookup"><span data-stu-id="029dc-155">Specifies a description for the role capability file.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="029dc-156">-Omgevings variabelen</span><span class="sxs-lookup"><span data-stu-id="029dc-156">-EnvironmentVariables</span></span>

<span data-ttu-id="029dc-157">Hiermee geeft u de omgevings variabelen op voor sessies die dit functie gegevensbestand beschikbaar maken.</span><span class="sxs-lookup"><span data-stu-id="029dc-157">Specifies the environment variables for sessions that expose this role capability file.</span></span> <span data-ttu-id="029dc-158">Voer een hash-tabel in waarin de sleutels de namen van omgevings variabelen zijn en de waarden zijn de waarden van omgevings variabelen.</span><span class="sxs-lookup"><span data-stu-id="029dc-158">Enter a hash table in which the keys are the environment variable names and the values are the environment variable values.</span></span>

<span data-ttu-id="029dc-159">Bijvoorbeeld: `EnvironmentVariables=@{TestShare="\\\\Server01\TestShare"}`</span><span class="sxs-lookup"><span data-stu-id="029dc-159">For example: `EnvironmentVariables=@{TestShare="\\\\Server01\TestShare"}`</span></span>

```yaml
Type: System.Collections.IDictionary
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="029dc-160">-FormatsToProcess</span><span class="sxs-lookup"><span data-stu-id="029dc-160">-FormatsToProcess</span></span>

<span data-ttu-id="029dc-161">Hiermee geeft u de indelings bestanden (. ps1xml) op die worden uitgevoerd in sessies die gebruikmaken van het functie-functionaliteits bestand.</span><span class="sxs-lookup"><span data-stu-id="029dc-161">Specifies the formatting files (.ps1xml) that run in sessions that use the role capability file.</span></span> <span data-ttu-id="029dc-162">De waarde van deze para meter moet een volledig of absoluut pad van de indelings bestanden zijn.</span><span class="sxs-lookup"><span data-stu-id="029dc-162">The value of this parameter must be a full or absolute path of the formatting files.</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="029dc-163">-FunctionDefinitions</span><span class="sxs-lookup"><span data-stu-id="029dc-163">-FunctionDefinitions</span></span>

<span data-ttu-id="029dc-164">Voegt de opgegeven functies toe aan sessies die de functie mogelijkheid beschikbaar maken.</span><span class="sxs-lookup"><span data-stu-id="029dc-164">Adds the specified functions to sessions that expose the role capability.</span></span> <span data-ttu-id="029dc-165">Voer een hash-tabel in met de volgende sleutels:</span><span class="sxs-lookup"><span data-stu-id="029dc-165">Enter a hash table with the following keys:</span></span>

- <span data-ttu-id="029dc-166">Naam.</span><span class="sxs-lookup"><span data-stu-id="029dc-166">Name.</span></span> <span data-ttu-id="029dc-167">Naam van de functie.</span><span class="sxs-lookup"><span data-stu-id="029dc-167">Name of the function.</span></span> <span data-ttu-id="029dc-168">Deze sleutel is vereist.</span><span class="sxs-lookup"><span data-stu-id="029dc-168">This key is required.</span></span>
- <span data-ttu-id="029dc-169">Script Block.</span><span class="sxs-lookup"><span data-stu-id="029dc-169">ScriptBlock.</span></span> <span data-ttu-id="029dc-170">Hoofd tekst van functie.</span><span class="sxs-lookup"><span data-stu-id="029dc-170">Function body.</span></span> <span data-ttu-id="029dc-171">Voer een script blok in.</span><span class="sxs-lookup"><span data-stu-id="029dc-171">Enter a script block.</span></span> <span data-ttu-id="029dc-172">Deze sleutel is vereist.</span><span class="sxs-lookup"><span data-stu-id="029dc-172">This key is required.</span></span>
- <span data-ttu-id="029dc-173">Opties.</span><span class="sxs-lookup"><span data-stu-id="029dc-173">Options.</span></span> <span data-ttu-id="029dc-174">Functie opties.</span><span class="sxs-lookup"><span data-stu-id="029dc-174">Function options.</span></span> <span data-ttu-id="029dc-175">Deze sleutel is optioneel.</span><span class="sxs-lookup"><span data-stu-id="029dc-175">This key is optional.</span></span> <span data-ttu-id="029dc-176">De standaard waarde is geen.</span><span class="sxs-lookup"><span data-stu-id="029dc-176">The default value is None.</span></span> <span data-ttu-id="029dc-177">De acceptabele waarden voor deze para meter zijn: zijn geen, alleen-lezen, constant, privé of AllScope.</span><span class="sxs-lookup"><span data-stu-id="029dc-177">The acceptable values for this parameter are: are None, ReadOnly, Constant, Private, or AllScope.</span></span>

<span data-ttu-id="029dc-178">Bijvoorbeeld:</span><span class="sxs-lookup"><span data-stu-id="029dc-178">For example:</span></span>

`@{Name="Get-PowerShellProcess";ScriptBlock={Get-Process PowerShell};Options="AllScope"}`

```yaml
Type: System.Collections.IDictionary[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="029dc-179">-GUID</span><span class="sxs-lookup"><span data-stu-id="029dc-179">-Guid</span></span>

<span data-ttu-id="029dc-180">Hiermee geeft u een unieke id op voor het bestand met de functie mogelijkheid.</span><span class="sxs-lookup"><span data-stu-id="029dc-180">Specifies a unique identifier for the role capability file.</span></span> <span data-ttu-id="029dc-181">Als u deze para meter weglaat, `New-PSRoleCapabilityFile` genereert een GUID voor het bestand.</span><span class="sxs-lookup"><span data-stu-id="029dc-181">If you omit this parameter, `New-PSRoleCapabilityFile` generates a GUID for the file.</span></span> <span data-ttu-id="029dc-182">Als u een nieuwe GUID wilt maken in Power shell, typt u `[guid]::NewGuid()` .</span><span class="sxs-lookup"><span data-stu-id="029dc-182">To create a new GUID in PowerShell, type `[guid]::NewGuid()`.</span></span>

```yaml
Type: System.Guid
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="029dc-183">-ModulesToImport</span><span class="sxs-lookup"><span data-stu-id="029dc-183">-ModulesToImport</span></span>

<span data-ttu-id="029dc-184">Hiermee geeft u de modules op die automatisch worden geïmporteerd in sessies die gebruikmaken van het functie-functionaliteits bestand.</span><span class="sxs-lookup"><span data-stu-id="029dc-184">Specifies the modules that are automatically imported into sessions that use the role capability file.</span></span> <span data-ttu-id="029dc-185">Standaard zijn alle opdrachten in de weer gegeven modules zichtbaar.</span><span class="sxs-lookup"><span data-stu-id="029dc-185">By default, all the commands in listed modules are visible.</span></span> <span data-ttu-id="029dc-186">In combi natie met **VisibleCmdlets** of **VisibleFunctions** kunnen de opdrachten die zichtbaar zijn in de opgegeven modules worden beperkt.</span><span class="sxs-lookup"><span data-stu-id="029dc-186">When used with **VisibleCmdlets** or **VisibleFunctions** , the commands visible from the specified modules can be restricted.</span></span>

<span data-ttu-id="029dc-187">Elke module die in de waarde van deze para meter wordt gebruikt, kan worden vertegenwoordigd door een teken reeks of een hash-tabel.</span><span class="sxs-lookup"><span data-stu-id="029dc-187">Each module used in the value of this parameter can be represented by a string or by a hash table.</span></span> <span data-ttu-id="029dc-188">Een module teken reeks bestaat alleen uit de naam van de module.</span><span class="sxs-lookup"><span data-stu-id="029dc-188">A module string consists only of the name of the module.</span></span> <span data-ttu-id="029dc-189">Een module-hash-tabel kan **module** -, **ModuleVersion** -en **GUID** -sleutels bevatten.</span><span class="sxs-lookup"><span data-stu-id="029dc-189">A module hash table can include **ModuleName** , **ModuleVersion** , and **GUID** keys.</span></span> <span data-ttu-id="029dc-190">Alleen de **module** sleutel is vereist.</span><span class="sxs-lookup"><span data-stu-id="029dc-190">Only the **ModuleName** key is required.</span></span>

<span data-ttu-id="029dc-191">De volgende waarde bestaat bijvoorbeeld uit een teken reeks en een hash-tabel.</span><span class="sxs-lookup"><span data-stu-id="029dc-191">For example, the following value consists of a string and a hash table.</span></span> <span data-ttu-id="029dc-192">Een combi natie van teken reeksen en hash-tabellen, in een wille keurige volg orde, is geldig.</span><span class="sxs-lookup"><span data-stu-id="029dc-192">Any combination of strings and hash tables, in any order, is valid.</span></span>

`"TroubleshootingPack", @{ModuleName="PSDiagnostics"; ModuleVersion="1.0.0.0";GUID="c61d6278-02a3-4618-ae37-a524d40a7f44"}`

```yaml
Type: System.Object[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="029dc-193">-Path</span><span class="sxs-lookup"><span data-stu-id="029dc-193">-Path</span></span>

<span data-ttu-id="029dc-194">Hiermee geeft u het pad en de bestands naam van het functie gegevensbestand.</span><span class="sxs-lookup"><span data-stu-id="029dc-194">Specifies the path and filename of the role capability file.</span></span> <span data-ttu-id="029dc-195">Het bestand moet een `.psrc` bestands extensie hebben.</span><span class="sxs-lookup"><span data-stu-id="029dc-195">The file must have a `.psrc` filename extension.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="029dc-196">-ScriptsToProcess</span><span class="sxs-lookup"><span data-stu-id="029dc-196">-ScriptsToProcess</span></span>

<span data-ttu-id="029dc-197">Hiermee geeft u scripts op die moeten worden toegevoegd aan sessies die gebruikmaken van het functie-functionaliteits bestand.</span><span class="sxs-lookup"><span data-stu-id="029dc-197">Specifies scripts to add to sessions that use the role capability file.</span></span> <span data-ttu-id="029dc-198">Geef het pad en de bestands namen van de scripts op.</span><span class="sxs-lookup"><span data-stu-id="029dc-198">Enter the path and file names of the scripts.</span></span> <span data-ttu-id="029dc-199">De waarde van deze para meter moet een volledig of absoluut pad zijn van de namen van het script bestand.</span><span class="sxs-lookup"><span data-stu-id="029dc-199">The value of this parameter must be a full or absolute path of the script file names.</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="029dc-200">-TypesToProcess</span><span class="sxs-lookup"><span data-stu-id="029dc-200">-TypesToProcess</span></span>

<span data-ttu-id="029dc-201">Hiermee geeft u type bestanden (. ps1xml) op die moeten worden toegevoegd aan sessies die gebruikmaken van het functie-Capability-bestand.</span><span class="sxs-lookup"><span data-stu-id="029dc-201">Specifies type files (.ps1xml) to add to sessions that use the role capability file.</span></span> <span data-ttu-id="029dc-202">Voer de bestands namen van het type in.</span><span class="sxs-lookup"><span data-stu-id="029dc-202">Enter the type filenames.</span></span> <span data-ttu-id="029dc-203">De waarde van deze para meter moet een volledig of absoluut pad van het type filenames zijn.</span><span class="sxs-lookup"><span data-stu-id="029dc-203">The value of this parameter must be a full or absolute path of the type filenames.</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="029dc-204">-VariableDefinitions</span><span class="sxs-lookup"><span data-stu-id="029dc-204">-VariableDefinitions</span></span>

<span data-ttu-id="029dc-205">Hiermee geeft u variabelen op die moeten worden toegevoegd aan sessies die gebruikmaken van het functie-functionaliteits bestand.</span><span class="sxs-lookup"><span data-stu-id="029dc-205">Specifies variables to add to sessions that use the role capability file.</span></span> <span data-ttu-id="029dc-206">Voer een hash-tabel in met de volgende sleutels:</span><span class="sxs-lookup"><span data-stu-id="029dc-206">Enter a hash table with the following keys:</span></span>

- <span data-ttu-id="029dc-207">Naam.</span><span class="sxs-lookup"><span data-stu-id="029dc-207">Name.</span></span> <span data-ttu-id="029dc-208">De naam van de variabele.</span><span class="sxs-lookup"><span data-stu-id="029dc-208">Name of the variable.</span></span> <span data-ttu-id="029dc-209">Deze sleutel is vereist.</span><span class="sxs-lookup"><span data-stu-id="029dc-209">This key is required.</span></span>
- <span data-ttu-id="029dc-210">Waarde.</span><span class="sxs-lookup"><span data-stu-id="029dc-210">Value.</span></span> <span data-ttu-id="029dc-211">Waarde van variabele.</span><span class="sxs-lookup"><span data-stu-id="029dc-211">Variable value.</span></span> <span data-ttu-id="029dc-212">Deze sleutel is vereist.</span><span class="sxs-lookup"><span data-stu-id="029dc-212">This key is required.</span></span>
- <span data-ttu-id="029dc-213">Opties.</span><span class="sxs-lookup"><span data-stu-id="029dc-213">Options.</span></span> <span data-ttu-id="029dc-214">Variabele opties.</span><span class="sxs-lookup"><span data-stu-id="029dc-214">Variable options.</span></span> <span data-ttu-id="029dc-215">Deze sleutel is optioneel.</span><span class="sxs-lookup"><span data-stu-id="029dc-215">This key is optional.</span></span> <span data-ttu-id="029dc-216">De standaard waarde is geen.</span><span class="sxs-lookup"><span data-stu-id="029dc-216">The default value is None.</span></span> <span data-ttu-id="029dc-217">De acceptabele waarden voor deze para meter zijn: zijn geen, alleen-lezen, constant, privé of AllScope.</span><span class="sxs-lookup"><span data-stu-id="029dc-217">The acceptable values for this parameter are: are None, ReadOnly, Constant, Private, or AllScope.</span></span>

<span data-ttu-id="029dc-218">Bijvoorbeeld: `@{Name="WarningPreference";Value="SilentlyContinue";Options="AllScope"}`</span><span class="sxs-lookup"><span data-stu-id="029dc-218">For example: `@{Name="WarningPreference";Value="SilentlyContinue";Options="AllScope"}`</span></span>

```yaml
Type: System.Object
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="029dc-219">-VisibleAliases</span><span class="sxs-lookup"><span data-stu-id="029dc-219">-VisibleAliases</span></span>

<span data-ttu-id="029dc-220">Beperkt de aliassen in de sessie met de aliassen die zijn opgegeven in de waarde van deze para meter, plus alle aliassen die u definieert in de para meter **AliasDefinition** .</span><span class="sxs-lookup"><span data-stu-id="029dc-220">Limits the aliases in the session to those aliases specified in the value of this parameter, plus any aliases that you define in the **AliasDefinition** parameter.</span></span> <span data-ttu-id="029dc-221">Joker tekens worden ondersteund.</span><span class="sxs-lookup"><span data-stu-id="029dc-221">Wildcard characters are supported.</span></span>
<span data-ttu-id="029dc-222">Standaard worden alle aliassen die zijn gedefinieerd door de Power shell-engine en alle aliassen die modules exporteren, weer gegeven in de sessie.</span><span class="sxs-lookup"><span data-stu-id="029dc-222">By default, all aliases that are defined by the PowerShell engine and all aliases that modules export are visible in the session.</span></span>

<span data-ttu-id="029dc-223">Als u bijvoorbeeld de beschik bare aliassen wilt beperken tot GM en GCM, gebruikt u de volgende syntaxis: `VisibleAliases="gcm", "gp"`</span><span class="sxs-lookup"><span data-stu-id="029dc-223">For example, to limit the available aliases to gm and gcm use this syntax: `VisibleAliases="gcm", "gp"`</span></span>

<span data-ttu-id="029dc-224">Wanneer een **zicht bare** para meter is opgenomen in het functie-Capability-bestand, verwijdert Power shell de `Import-Module` cmdlet en de bijbehorende `ipmo` alias uit de sessie.</span><span class="sxs-lookup"><span data-stu-id="029dc-224">When any **Visible** parameter is included in the role capability file, PowerShell removes the `Import-Module` cmdlet and its `ipmo` alias from the session.</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: True
```

### <span data-ttu-id="029dc-225">-VisibleCmdlets</span><span class="sxs-lookup"><span data-stu-id="029dc-225">-VisibleCmdlets</span></span>

<span data-ttu-id="029dc-226">Hiermee worden de cmdlets in de sessie beperkt tot die welke zijn opgegeven in de waarde van deze para meter.</span><span class="sxs-lookup"><span data-stu-id="029dc-226">Limits the cmdlets in the session to those specified in the value of this parameter.</span></span> <span data-ttu-id="029dc-227">Joker tekens en modules met gekwalificeerde namen worden ondersteund.</span><span class="sxs-lookup"><span data-stu-id="029dc-227">Wildcard characters and Module Qualified Names are supported.</span></span>

<span data-ttu-id="029dc-228">Standaard worden alle cmdlets die de modules in de sessie exporteren, weer gegeven in de sessie.</span><span class="sxs-lookup"><span data-stu-id="029dc-228">By default, all cmdlets that the modules in the session export are visible in the session.</span></span> <span data-ttu-id="029dc-229">Gebruik de para meters **SessionType** en **ModulesToImport** om te bepalen welke modules en modules in de sessie worden geïmporteerd.</span><span class="sxs-lookup"><span data-stu-id="029dc-229">Use the **SessionType** and **ModulesToImport** parameters to determine which modules and snap-ins are imported into the session.</span></span> <span data-ttu-id="029dc-230">Als er geen modules in **ModulesToImport** de cmdlet beschikbaar maken, `New-PSRoleCapabilityFile` probeert de juiste module te laden.</span><span class="sxs-lookup"><span data-stu-id="029dc-230">If no modules in **ModulesToImport** expose the cmdlet, `New-PSRoleCapabilityFile` tries to load the appropriate module.</span></span>

<span data-ttu-id="029dc-231">Wanneer een **zicht bare** para meter is opgenomen in het configuratie bestand van de sessie, verwijdert Power shell de `Import-Module` cmdlet en de bijbehorende `ipmo` alias uit de sessie.</span><span class="sxs-lookup"><span data-stu-id="029dc-231">When any **Visible** parameter is included in the session configuration file, PowerShell removes the `Import-Module` cmdlet and its `ipmo` alias from the session.</span></span>

```yaml
Type: System.Object[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: True
```

### <span data-ttu-id="029dc-232">-VisibleExternalCommands</span><span class="sxs-lookup"><span data-stu-id="029dc-232">-VisibleExternalCommands</span></span>

<span data-ttu-id="029dc-233">Hiermee beperkt u de externe binaire bestanden, scripts en opdrachten die in de sessie kunnen worden uitgevoerd en die zijn opgegeven in de waarde van deze para meter.</span><span class="sxs-lookup"><span data-stu-id="029dc-233">Limits the external binaries, scripts and commands that can be executed in the session to those specified in the value of this parameter.</span></span>

<span data-ttu-id="029dc-234">Standaard zijn er in deze sessie geen externe opdrachten zichtbaar.</span><span class="sxs-lookup"><span data-stu-id="029dc-234">By default, no external commands are visible in this session.</span></span>

<span data-ttu-id="029dc-235">Wanneer een **zicht bare** para meter is opgenomen in het configuratie bestand van de sessie, verwijdert Power shell de `Import-Module` cmdlet en de bijbehorende `ipmo` alias uit de sessie.</span><span class="sxs-lookup"><span data-stu-id="029dc-235">When any **Visible** parameter is included in the session configuration file, PowerShell removes the `Import-Module` cmdlet and its `ipmo` alias from the session.</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="029dc-236">-VisibleFunctions</span><span class="sxs-lookup"><span data-stu-id="029dc-236">-VisibleFunctions</span></span>

<span data-ttu-id="029dc-237">Hiermee beperkt u de functies in de sessie die zijn opgegeven in de waarde van deze para meter, plus de functies die u definieert in de para meter **FunctionDefinitions** .</span><span class="sxs-lookup"><span data-stu-id="029dc-237">Limits the functions in the session to those specified in the value of this parameter, plus any functions that you define in the **FunctionDefinitions** parameter.</span></span> <span data-ttu-id="029dc-238">Joker tekens worden ondersteund.</span><span class="sxs-lookup"><span data-stu-id="029dc-238">Wildcard characters are supported.</span></span>

<span data-ttu-id="029dc-239">Standaard zijn alle functies die door modules in de sessie worden geëxporteerd, zichtbaar in die sessie.</span><span class="sxs-lookup"><span data-stu-id="029dc-239">By default, all functions exported by modules in the session are visible in that session.</span></span> <span data-ttu-id="029dc-240">Gebruik de para meters **SessionType** en **ModulesToImport** om te bepalen welke modules in de sessie worden geïmporteerd.</span><span class="sxs-lookup"><span data-stu-id="029dc-240">Use the **SessionType** and **ModulesToImport** parameters to determine which modules are imported into the session.</span></span>

<span data-ttu-id="029dc-241">Wanneer een **zicht bare** para meter is opgenomen in het configuratie bestand van de sessie, verwijdert Power shell de `Import-Module` cmdlet en de bijbehorende `ipmo` alias uit de sessie.</span><span class="sxs-lookup"><span data-stu-id="029dc-241">When any **Visible** parameter is included in the session configuration file, PowerShell removes the `Import-Module` cmdlet and its `ipmo` alias from the session.</span></span>

```yaml
Type: System.Object[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: True
```

### <span data-ttu-id="029dc-242">-VisibleProviders</span><span class="sxs-lookup"><span data-stu-id="029dc-242">-VisibleProviders</span></span>

<span data-ttu-id="029dc-243">Hiermee worden de Power shell-providers in de sessie beperkt tot die welke zijn opgegeven in de waarde van deze para meter.</span><span class="sxs-lookup"><span data-stu-id="029dc-243">Limits the PowerShell providers in the session to those specified in the value of this parameter.</span></span>
<span data-ttu-id="029dc-244">Joker tekens worden ondersteund.</span><span class="sxs-lookup"><span data-stu-id="029dc-244">Wildcard characters are supported.</span></span>

<span data-ttu-id="029dc-245">Standaard worden alle providers die zijn geëxporteerd door een module in de sessie, weer gegeven in de sessie.</span><span class="sxs-lookup"><span data-stu-id="029dc-245">By default, all providers exported by a module in the session are visible in the session.</span></span> <span data-ttu-id="029dc-246">Gebruik de para meters **SessionType** en **ModulesToImport** om te bepalen welke modules in de sessie worden geïmporteerd.</span><span class="sxs-lookup"><span data-stu-id="029dc-246">Use the **SessionType** and **ModulesToImport** parameters to determine which modules are imported into the session.</span></span>

<span data-ttu-id="029dc-247">Wanneer een **zicht bare** para meter is opgenomen in het configuratie bestand van de sessie, verwijdert Power shell de `Import-Module` cmdlet en de bijbehorende `ipmo` alias uit de sessie.</span><span class="sxs-lookup"><span data-stu-id="029dc-247">When any **Visible** parameter is included in the session configuration file, PowerShell removes the `Import-Module` cmdlet and its `ipmo` alias from the session.</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: True
```

### <span data-ttu-id="029dc-248">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="029dc-248">CommonParameters</span></span>

<span data-ttu-id="029dc-249">Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="029dc-249">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="029dc-250">Zie [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="029dc-250">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="029dc-251">INVOER</span><span class="sxs-lookup"><span data-stu-id="029dc-251">INPUTS</span></span>

## <span data-ttu-id="029dc-252">UITVOER</span><span class="sxs-lookup"><span data-stu-id="029dc-252">OUTPUTS</span></span>

## <span data-ttu-id="029dc-253">OPMERKINGEN</span><span class="sxs-lookup"><span data-stu-id="029dc-253">NOTES</span></span>

## <span data-ttu-id="029dc-254">GERELATEERDE KOPPELINGEN</span><span class="sxs-lookup"><span data-stu-id="029dc-254">RELATED LINKS</span></span>

[<span data-ttu-id="029dc-255">New-PSSessionConfigurationFile</span><span class="sxs-lookup"><span data-stu-id="029dc-255">New-PSSessionConfigurationFile</span></span>](New-PSSessionConfigurationFile.md)

[<span data-ttu-id="029dc-256">Get-PSSessionCapability</span><span class="sxs-lookup"><span data-stu-id="029dc-256">Get-PSSessionCapability</span></span>](Get-PSSessionCapability.md)
