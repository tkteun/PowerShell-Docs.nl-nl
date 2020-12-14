---
external help file: System.Management.Automation.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 09/11/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/new-psrolecapabilityfile?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: New-PSRoleCapabilityFile
ms.openlocfilehash: 3ef54618e065a5fca3d52415897b3042d6ba4c65
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 11/17/2020
ms.locfileid: "94706190"
---
# <span data-ttu-id="897ba-102">New-PSRoleCapabilityFile</span><span class="sxs-lookup"><span data-stu-id="897ba-102">New-PSRoleCapabilityFile</span></span>

## <span data-ttu-id="897ba-103">SAMENVATTING</span><span class="sxs-lookup"><span data-stu-id="897ba-103">SYNOPSIS</span></span>
<span data-ttu-id="897ba-104">Hiermee maakt u een bestand dat een set mogelijkheden definieert die moeten worden weer gegeven via een sessie configuratie.</span><span class="sxs-lookup"><span data-stu-id="897ba-104">Creates a file that defines a set of capabilities to be exposed through a session configuration.</span></span>

## <span data-ttu-id="897ba-105">SYNTAXIS</span><span class="sxs-lookup"><span data-stu-id="897ba-105">SYNTAX</span></span>

```
New-PSRoleCapabilityFile [-Path] <String> [-Guid <Guid>] [-Author <String>] [-Description <String>]
 [-CompanyName <String>] [-Copyright <String>] [-ModulesToImport <Object[]>] [-VisibleAliases <String[]>]
 [-VisibleCmdlets <Object[]>] [-VisibleFunctions <Object[]>] [-VisibleExternalCommands <String[]>]
 [-VisibleProviders <String[]>] [-ScriptsToProcess <String[]>] [-AliasDefinitions <IDictionary[]>]
 [-FunctionDefinitions <IDictionary[]>] [-VariableDefinitions <Object>] [-EnvironmentVariables <IDictionary>]
 [-TypesToProcess <String[]>] [-FormatsToProcess <String[]>] [-AssembliesToLoad <String[]>]
 [<CommonParameters>]
```

## <span data-ttu-id="897ba-106">BESCHRIJVING</span><span class="sxs-lookup"><span data-stu-id="897ba-106">DESCRIPTION</span></span>

<span data-ttu-id="897ba-107">Met de `New-PSRoleCapabilityFile` cmdlet wordt een bestand gemaakt dat een reeks gebruikers mogelijkheden definieert die kunnen worden weer gegeven via sessie configuratie bestanden.</span><span class="sxs-lookup"><span data-stu-id="897ba-107">The `New-PSRoleCapabilityFile` cmdlet creates a file that defines a set of user capabilities that can be exposed through session configuration files.</span></span> <span data-ttu-id="897ba-108">Dit omvat het bepalen van de cmdlets, functies en scripts die beschikbaar zijn voor gebruikers.</span><span class="sxs-lookup"><span data-stu-id="897ba-108">This includes determining which cmdlets, functions, and scripts are available to users.</span></span> <span data-ttu-id="897ba-109">Het Capability-bestand is een bestand met lees bare tekst dat een hash-tabel met eigenschappen en waarden van sessie configuratie bevat.</span><span class="sxs-lookup"><span data-stu-id="897ba-109">The capability file is a human-readable text file that contains a hash table of session configuration properties and values.</span></span> <span data-ttu-id="897ba-110">Het bestand heeft de bestandsnaam extensie. psrc en kan worden gebruikt door meer dan één sessie configuratie.</span><span class="sxs-lookup"><span data-stu-id="897ba-110">The file has a .psrc file name extension, and can be used by more than one session configuration.</span></span>

<span data-ttu-id="897ba-111">Alle para meters van `New-PSRoleCapabilityFile` zijn optioneel, met uitzonde ring van de para meter **Path** , waarmee het bestandspad voor het bestand wordt opgegeven.</span><span class="sxs-lookup"><span data-stu-id="897ba-111">All the parameters of `New-PSRoleCapabilityFile` are optional except for the **Path** parameter, which specifies the file path for the file.</span></span> <span data-ttu-id="897ba-112">Als u geen para meter opneemt tijdens het uitvoeren van de cmdlet, wordt de bijbehorende sleutel in het bestand met de sessie configuratie commentaar gegeven, behalve wanneer vermeld in de parameter beschrijving.</span><span class="sxs-lookup"><span data-stu-id="897ba-112">If you do not include a parameter when you run the cmdlet, the corresponding key in the session configuration file is commented-out, except where noted in the parameter description.</span></span> <span data-ttu-id="897ba-113">Bijvoorbeeld, als u de para meter **AssembliesToLoad** niet opneemt, wordt die sectie van het sessie configuratie bestand uit commentaar genomen.</span><span class="sxs-lookup"><span data-stu-id="897ba-113">For example, if you do not include the **AssembliesToLoad** parameter then that section of the session configuration file is commented out.</span></span>

<span data-ttu-id="897ba-114">Als u het bestand voor de functie wilt gebruiken in een sessie configuratie, plaatst u het bestand eerst in een submap **RoleCapabilities** van een geldige map voor de Power shell-module.</span><span class="sxs-lookup"><span data-stu-id="897ba-114">To use the role capability file in a session configuration, first place the file in a **RoleCapabilities** subfolder of a valid PowerShell module folder.</span></span> <span data-ttu-id="897ba-115">Ga vervolgens naar het bestand met de naam in het veld **RoleDefinitions** in een Power shell-sessie configuratie bestand (. pssc).</span><span class="sxs-lookup"><span data-stu-id="897ba-115">Then reference the file by name in the **RoleDefinitions** field in a PowerShell Session Configuration (.pssc) file.</span></span>

<span data-ttu-id="897ba-116">Deze cmdlet is geïntroduceerd in Windows Power shell 5,0.</span><span class="sxs-lookup"><span data-stu-id="897ba-116">This cmdlet was introduced in Windows PowerShell 5.0.</span></span>

## <span data-ttu-id="897ba-117">VOORBEELDEN</span><span class="sxs-lookup"><span data-stu-id="897ba-117">EXAMPLES</span></span>

### <span data-ttu-id="897ba-118">Voor beeld 1: een functie bestand met een lege rol maken</span><span class="sxs-lookup"><span data-stu-id="897ba-118">Example 1: Create a blank role capability file</span></span>

<span data-ttu-id="897ba-119">In dit voor beeld wordt een nieuw bestand met een functie gemaakt waarin de standaard waarden (leeg) worden gebruikt.</span><span class="sxs-lookup"><span data-stu-id="897ba-119">This example creates a new role capability file that uses the default (blank) values.</span></span> <span data-ttu-id="897ba-120">Het bestand kan later worden bewerkt in een tekst editor om deze configuratie-instellingen te wijzigen.</span><span class="sxs-lookup"><span data-stu-id="897ba-120">The file can later be edited in a text editor to change these configuration settings.</span></span>

```powershell
New-PSRoleCapabilityFile -Path ".\ExampleFile.psrc"
```

### <span data-ttu-id="897ba-121">Voor beeld 2: een functie mogelijkheidsprofiel maken waarmee gebruikers services en een VDI-computer opnieuw kunnen starten</span><span class="sxs-lookup"><span data-stu-id="897ba-121">Example 2: Create a role capability file allowing users to restart services and any VDI computer</span></span>

<span data-ttu-id="897ba-122">In dit voor beeld wordt een mogelijkheidsprofiel gemaakt waarmee gebruikers services en computers die overeenkomen met een specifiek naam patroon, opnieuw kunnen starten.</span><span class="sxs-lookup"><span data-stu-id="897ba-122">This example creates a sample role capability file that enables users to restart services and computers that match a specific name pattern.</span></span> <span data-ttu-id="897ba-123">Naam filtering wordt gedefinieerd door de para meter **ValidatePattern** in te stellen op de reguliere expressie `VDI\d+` .</span><span class="sxs-lookup"><span data-stu-id="897ba-123">Name filtering is defined by setting the **ValidatePattern** parameter to the regular expression `VDI\d+`.</span></span>

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

## <span data-ttu-id="897ba-124">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="897ba-124">PARAMETERS</span></span>

### <span data-ttu-id="897ba-125">-AliasDefinitions</span><span class="sxs-lookup"><span data-stu-id="897ba-125">-AliasDefinitions</span></span>

<span data-ttu-id="897ba-126">Voegt de opgegeven aliassen toe aan sessies die gebruikmaken van het functie-functionaliteits bestand.</span><span class="sxs-lookup"><span data-stu-id="897ba-126">Adds the specified aliases to sessions that use the role capability file.</span></span> <span data-ttu-id="897ba-127">Voer een hash-tabel in met de volgende sleutels:</span><span class="sxs-lookup"><span data-stu-id="897ba-127">Enter a hash table with the following keys:</span></span>

- <span data-ttu-id="897ba-128">Naam.</span><span class="sxs-lookup"><span data-stu-id="897ba-128">Name.</span></span> <span data-ttu-id="897ba-129">De naam van de alias.</span><span class="sxs-lookup"><span data-stu-id="897ba-129">Name of the alias.</span></span> <span data-ttu-id="897ba-130">Deze sleutel is vereist.</span><span class="sxs-lookup"><span data-stu-id="897ba-130">This key is required.</span></span>
- <span data-ttu-id="897ba-131">Waarde.</span><span class="sxs-lookup"><span data-stu-id="897ba-131">Value.</span></span> <span data-ttu-id="897ba-132">De opdracht die wordt vertegenwoordigd door de alias.</span><span class="sxs-lookup"><span data-stu-id="897ba-132">The command that the alias represents.</span></span> <span data-ttu-id="897ba-133">Deze sleutel is vereist.</span><span class="sxs-lookup"><span data-stu-id="897ba-133">This key is required.</span></span>
- <span data-ttu-id="897ba-134">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="897ba-134">Description.</span></span> <span data-ttu-id="897ba-135">Een teken reeks waarmee de alias wordt beschreven.</span><span class="sxs-lookup"><span data-stu-id="897ba-135">A text string that describes the alias.</span></span> <span data-ttu-id="897ba-136">Deze sleutel is optioneel.</span><span class="sxs-lookup"><span data-stu-id="897ba-136">This key is optional.</span></span>
- <span data-ttu-id="897ba-137">Opties.</span><span class="sxs-lookup"><span data-stu-id="897ba-137">Options.</span></span> <span data-ttu-id="897ba-138">Alias opties.</span><span class="sxs-lookup"><span data-stu-id="897ba-138">Alias options.</span></span> <span data-ttu-id="897ba-139">Deze sleutel is optioneel.</span><span class="sxs-lookup"><span data-stu-id="897ba-139">This key is optional.</span></span> <span data-ttu-id="897ba-140">De standaard waarde is geen.</span><span class="sxs-lookup"><span data-stu-id="897ba-140">The default value is None.</span></span> <span data-ttu-id="897ba-141">De acceptabele waarden voor deze para meter zijn: geen, alleen-lezen, constant, privé of AllScope.</span><span class="sxs-lookup"><span data-stu-id="897ba-141">The acceptable values for this parameter are: None, ReadOnly, Constant, Private, or AllScope.</span></span>

<span data-ttu-id="897ba-142">Bijvoorbeeld: `@{Name="hlp";Value="Get-Help";Description="Gets help";Options="ReadOnly"}`</span><span class="sxs-lookup"><span data-stu-id="897ba-142">For example: `@{Name="hlp";Value="Get-Help";Description="Gets help";Options="ReadOnly"}`</span></span>

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

### <span data-ttu-id="897ba-143">-AssembliesToLoad</span><span class="sxs-lookup"><span data-stu-id="897ba-143">-AssembliesToLoad</span></span>

<span data-ttu-id="897ba-144">Hiermee geeft u de assembly's op die moeten worden geladen in de sessies die gebruikmaken van het functie-functionaliteits bestand.</span><span class="sxs-lookup"><span data-stu-id="897ba-144">Specifies the assemblies to load into the sessions that use the role capability file.</span></span>

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

### <span data-ttu-id="897ba-145">-Author</span><span class="sxs-lookup"><span data-stu-id="897ba-145">-Author</span></span>

<span data-ttu-id="897ba-146">Hiermee geeft u de gebruiker die het functie bestand heeft gemaakt.</span><span class="sxs-lookup"><span data-stu-id="897ba-146">Specifies the user that created the role capability file.</span></span>

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

### <span data-ttu-id="897ba-147">-CompanyName</span><span class="sxs-lookup"><span data-stu-id="897ba-147">-CompanyName</span></span>

<span data-ttu-id="897ba-148">Hiermee wordt het bedrijf geïdentificeerd dat het functie gegevensbestand heeft gemaakt.</span><span class="sxs-lookup"><span data-stu-id="897ba-148">Identifies the company that created the role capability file.</span></span>
<span data-ttu-id="897ba-149">De standaard waarde is onbekend.</span><span class="sxs-lookup"><span data-stu-id="897ba-149">The default value is Unknown.</span></span>

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

### <span data-ttu-id="897ba-150">-Copyright</span><span class="sxs-lookup"><span data-stu-id="897ba-150">-Copyright</span></span>

<span data-ttu-id="897ba-151">Hiermee geeft u een copyright op voor het functie-functionaliteits bestand.</span><span class="sxs-lookup"><span data-stu-id="897ba-151">Specifies a copyright for the role capability file.</span></span> <span data-ttu-id="897ba-152">Als u deze para meter weglaat, `New-PSRoleCapabilityFile` genereert een copyright verklaring met behulp van de waarde van de para meter **Auteur** .</span><span class="sxs-lookup"><span data-stu-id="897ba-152">If you omit this parameter, `New-PSRoleCapabilityFile` generates a copyright statement by using the value of the **Author** parameter.</span></span>

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

### <span data-ttu-id="897ba-153">-Beschrijving</span><span class="sxs-lookup"><span data-stu-id="897ba-153">-Description</span></span>

<span data-ttu-id="897ba-154">Hiermee geeft u een beschrijving op voor het bestand met de functie mogelijkheid.</span><span class="sxs-lookup"><span data-stu-id="897ba-154">Specifies a description for the role capability file.</span></span>

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

### <span data-ttu-id="897ba-155">-Omgevings variabelen</span><span class="sxs-lookup"><span data-stu-id="897ba-155">-EnvironmentVariables</span></span>

<span data-ttu-id="897ba-156">Hiermee geeft u de omgevings variabelen op voor sessies die dit functie gegevensbestand beschikbaar maken.</span><span class="sxs-lookup"><span data-stu-id="897ba-156">Specifies the environment variables for sessions that expose this role capability file.</span></span> <span data-ttu-id="897ba-157">Voer een hash-tabel in waarin de sleutels de namen van omgevings variabelen zijn en de waarden zijn de waarden van omgevings variabelen.</span><span class="sxs-lookup"><span data-stu-id="897ba-157">Enter a hash table in which the keys are the environment variable names and the values are the environment variable values.</span></span>

<span data-ttu-id="897ba-158">Bijvoorbeeld: `EnvironmentVariables=@{TestShare="\\\\Server01\TestShare"}`</span><span class="sxs-lookup"><span data-stu-id="897ba-158">For example: `EnvironmentVariables=@{TestShare="\\\\Server01\TestShare"}`</span></span>

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

### <span data-ttu-id="897ba-159">-FormatsToProcess</span><span class="sxs-lookup"><span data-stu-id="897ba-159">-FormatsToProcess</span></span>

<span data-ttu-id="897ba-160">Hiermee geeft u de indelings bestanden (. ps1xml) op die worden uitgevoerd in sessies die gebruikmaken van het functie-functionaliteits bestand.</span><span class="sxs-lookup"><span data-stu-id="897ba-160">Specifies the formatting files (.ps1xml) that run in sessions that use the role capability file.</span></span> <span data-ttu-id="897ba-161">De waarde van deze para meter moet een volledig of absoluut pad van de indelings bestanden zijn.</span><span class="sxs-lookup"><span data-stu-id="897ba-161">The value of this parameter must be a full or absolute path of the formatting files.</span></span>

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

### <span data-ttu-id="897ba-162">-FunctionDefinitions</span><span class="sxs-lookup"><span data-stu-id="897ba-162">-FunctionDefinitions</span></span>

<span data-ttu-id="897ba-163">Voegt de opgegeven functies toe aan sessies die de functie mogelijkheid beschikbaar maken.</span><span class="sxs-lookup"><span data-stu-id="897ba-163">Adds the specified functions to sessions that expose the role capability.</span></span> <span data-ttu-id="897ba-164">Voer een hash-tabel in met de volgende sleutels:</span><span class="sxs-lookup"><span data-stu-id="897ba-164">Enter a hash table with the following keys:</span></span>

- <span data-ttu-id="897ba-165">Naam.</span><span class="sxs-lookup"><span data-stu-id="897ba-165">Name.</span></span> <span data-ttu-id="897ba-166">Naam van de functie.</span><span class="sxs-lookup"><span data-stu-id="897ba-166">Name of the function.</span></span> <span data-ttu-id="897ba-167">Deze sleutel is vereist.</span><span class="sxs-lookup"><span data-stu-id="897ba-167">This key is required.</span></span>
- <span data-ttu-id="897ba-168">Script Block.</span><span class="sxs-lookup"><span data-stu-id="897ba-168">ScriptBlock.</span></span> <span data-ttu-id="897ba-169">Hoofd tekst van functie.</span><span class="sxs-lookup"><span data-stu-id="897ba-169">Function body.</span></span> <span data-ttu-id="897ba-170">Voer een script blok in.</span><span class="sxs-lookup"><span data-stu-id="897ba-170">Enter a script block.</span></span> <span data-ttu-id="897ba-171">Deze sleutel is vereist.</span><span class="sxs-lookup"><span data-stu-id="897ba-171">This key is required.</span></span>
- <span data-ttu-id="897ba-172">Opties.</span><span class="sxs-lookup"><span data-stu-id="897ba-172">Options.</span></span> <span data-ttu-id="897ba-173">Functie opties.</span><span class="sxs-lookup"><span data-stu-id="897ba-173">Function options.</span></span> <span data-ttu-id="897ba-174">Deze sleutel is optioneel.</span><span class="sxs-lookup"><span data-stu-id="897ba-174">This key is optional.</span></span> <span data-ttu-id="897ba-175">De standaard waarde is geen.</span><span class="sxs-lookup"><span data-stu-id="897ba-175">The default value is None.</span></span> <span data-ttu-id="897ba-176">De acceptabele waarden voor deze para meter zijn: zijn geen, alleen-lezen, constant, privé of AllScope.</span><span class="sxs-lookup"><span data-stu-id="897ba-176">The acceptable values for this parameter are: are None, ReadOnly, Constant, Private, or AllScope.</span></span>

<span data-ttu-id="897ba-177">Bijvoorbeeld:</span><span class="sxs-lookup"><span data-stu-id="897ba-177">For example:</span></span>

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

### <span data-ttu-id="897ba-178">-GUID</span><span class="sxs-lookup"><span data-stu-id="897ba-178">-Guid</span></span>

<span data-ttu-id="897ba-179">Hiermee geeft u een unieke id op voor het bestand met de functie mogelijkheid.</span><span class="sxs-lookup"><span data-stu-id="897ba-179">Specifies a unique identifier for the role capability file.</span></span> <span data-ttu-id="897ba-180">Als u deze para meter weglaat, `New-PSRoleCapabilityFile` genereert een GUID voor het bestand.</span><span class="sxs-lookup"><span data-stu-id="897ba-180">If you omit this parameter, `New-PSRoleCapabilityFile` generates a GUID for the file.</span></span> <span data-ttu-id="897ba-181">Als u een nieuwe GUID wilt maken in Power shell, typt u `[guid]::NewGuid()` .</span><span class="sxs-lookup"><span data-stu-id="897ba-181">To create a new GUID in PowerShell, type `[guid]::NewGuid()`.</span></span>

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

### <span data-ttu-id="897ba-182">-ModulesToImport</span><span class="sxs-lookup"><span data-stu-id="897ba-182">-ModulesToImport</span></span>

<span data-ttu-id="897ba-183">Hiermee geeft u de modules op die automatisch worden geïmporteerd in sessies die gebruikmaken van het functie-functionaliteits bestand.</span><span class="sxs-lookup"><span data-stu-id="897ba-183">Specifies the modules that are automatically imported into sessions that use the role capability file.</span></span> <span data-ttu-id="897ba-184">Standaard zijn alle opdrachten in de weer gegeven modules zichtbaar.</span><span class="sxs-lookup"><span data-stu-id="897ba-184">By default, all the commands in listed modules are visible.</span></span> <span data-ttu-id="897ba-185">In combi natie met **VisibleCmdlets** of **VisibleFunctions** kunnen de opdrachten die zichtbaar zijn in de opgegeven modules worden beperkt.</span><span class="sxs-lookup"><span data-stu-id="897ba-185">When used with **VisibleCmdlets** or **VisibleFunctions**, the commands visible from the specified modules can be restricted.</span></span>

<span data-ttu-id="897ba-186">Elke module die in de waarde van deze para meter wordt gebruikt, kan worden vertegenwoordigd door een teken reeks of een hash-tabel.</span><span class="sxs-lookup"><span data-stu-id="897ba-186">Each module used in the value of this parameter can be represented by a string or by a hash table.</span></span> <span data-ttu-id="897ba-187">Een module teken reeks bestaat alleen uit de naam van de module.</span><span class="sxs-lookup"><span data-stu-id="897ba-187">A module string consists only of the name of the module.</span></span> <span data-ttu-id="897ba-188">Een module-hash-tabel kan **module**-, **ModuleVersion**-en **GUID** -sleutels bevatten.</span><span class="sxs-lookup"><span data-stu-id="897ba-188">A module hash table can include **ModuleName**, **ModuleVersion**, and **GUID** keys.</span></span> <span data-ttu-id="897ba-189">Alleen de **module** sleutel is vereist.</span><span class="sxs-lookup"><span data-stu-id="897ba-189">Only the **ModuleName** key is required.</span></span>

<span data-ttu-id="897ba-190">De volgende waarde bestaat bijvoorbeeld uit een teken reeks en een hash-tabel.</span><span class="sxs-lookup"><span data-stu-id="897ba-190">For example, the following value consists of a string and a hash table.</span></span> <span data-ttu-id="897ba-191">Een combi natie van teken reeksen en hash-tabellen, in een wille keurige volg orde, is geldig.</span><span class="sxs-lookup"><span data-stu-id="897ba-191">Any combination of strings and hash tables, in any order, is valid.</span></span>

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

### <span data-ttu-id="897ba-192">-Path</span><span class="sxs-lookup"><span data-stu-id="897ba-192">-Path</span></span>

<span data-ttu-id="897ba-193">Hiermee geeft u het pad en de bestands naam van het functie gegevensbestand.</span><span class="sxs-lookup"><span data-stu-id="897ba-193">Specifies the path and filename of the role capability file.</span></span> <span data-ttu-id="897ba-194">Het bestand moet een `.psrc` bestands extensie hebben.</span><span class="sxs-lookup"><span data-stu-id="897ba-194">The file must have a `.psrc` filename extension.</span></span>

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

### <span data-ttu-id="897ba-195">-ScriptsToProcess</span><span class="sxs-lookup"><span data-stu-id="897ba-195">-ScriptsToProcess</span></span>

<span data-ttu-id="897ba-196">Hiermee geeft u scripts op die moeten worden toegevoegd aan sessies die gebruikmaken van het functie-functionaliteits bestand.</span><span class="sxs-lookup"><span data-stu-id="897ba-196">Specifies scripts to add to sessions that use the role capability file.</span></span> <span data-ttu-id="897ba-197">Geef het pad en de bestands namen van de scripts op.</span><span class="sxs-lookup"><span data-stu-id="897ba-197">Enter the path and file names of the scripts.</span></span> <span data-ttu-id="897ba-198">De waarde van deze para meter moet een volledig of absoluut pad zijn van de namen van het script bestand.</span><span class="sxs-lookup"><span data-stu-id="897ba-198">The value of this parameter must be a full or absolute path of the script file names.</span></span>

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

### <span data-ttu-id="897ba-199">-TypesToProcess</span><span class="sxs-lookup"><span data-stu-id="897ba-199">-TypesToProcess</span></span>

<span data-ttu-id="897ba-200">Hiermee geeft u type bestanden (. ps1xml) op die moeten worden toegevoegd aan sessies die gebruikmaken van het functie-Capability-bestand.</span><span class="sxs-lookup"><span data-stu-id="897ba-200">Specifies type files (.ps1xml) to add to sessions that use the role capability file.</span></span> <span data-ttu-id="897ba-201">Voer de bestands namen van het type in.</span><span class="sxs-lookup"><span data-stu-id="897ba-201">Enter the type filenames.</span></span> <span data-ttu-id="897ba-202">De waarde van deze para meter moet een volledig of absoluut pad van het type filenames zijn.</span><span class="sxs-lookup"><span data-stu-id="897ba-202">The value of this parameter must be a full or absolute path of the type filenames.</span></span>

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

### <span data-ttu-id="897ba-203">-VariableDefinitions</span><span class="sxs-lookup"><span data-stu-id="897ba-203">-VariableDefinitions</span></span>

<span data-ttu-id="897ba-204">Hiermee geeft u variabelen op die moeten worden toegevoegd aan sessies die gebruikmaken van het functie-functionaliteits bestand.</span><span class="sxs-lookup"><span data-stu-id="897ba-204">Specifies variables to add to sessions that use the role capability file.</span></span> <span data-ttu-id="897ba-205">Voer een hash-tabel in met de volgende sleutels:</span><span class="sxs-lookup"><span data-stu-id="897ba-205">Enter a hash table with the following keys:</span></span>

- <span data-ttu-id="897ba-206">Naam.</span><span class="sxs-lookup"><span data-stu-id="897ba-206">Name.</span></span> <span data-ttu-id="897ba-207">De naam van de variabele.</span><span class="sxs-lookup"><span data-stu-id="897ba-207">Name of the variable.</span></span> <span data-ttu-id="897ba-208">Deze sleutel is vereist.</span><span class="sxs-lookup"><span data-stu-id="897ba-208">This key is required.</span></span>
- <span data-ttu-id="897ba-209">Waarde.</span><span class="sxs-lookup"><span data-stu-id="897ba-209">Value.</span></span> <span data-ttu-id="897ba-210">Waarde van variabele.</span><span class="sxs-lookup"><span data-stu-id="897ba-210">Variable value.</span></span> <span data-ttu-id="897ba-211">Deze sleutel is vereist.</span><span class="sxs-lookup"><span data-stu-id="897ba-211">This key is required.</span></span>
- <span data-ttu-id="897ba-212">Opties.</span><span class="sxs-lookup"><span data-stu-id="897ba-212">Options.</span></span> <span data-ttu-id="897ba-213">Variabele opties.</span><span class="sxs-lookup"><span data-stu-id="897ba-213">Variable options.</span></span> <span data-ttu-id="897ba-214">Deze sleutel is optioneel.</span><span class="sxs-lookup"><span data-stu-id="897ba-214">This key is optional.</span></span> <span data-ttu-id="897ba-215">De standaard waarde is geen.</span><span class="sxs-lookup"><span data-stu-id="897ba-215">The default value is None.</span></span> <span data-ttu-id="897ba-216">De acceptabele waarden voor deze para meter zijn: zijn geen, alleen-lezen, constant, privé of AllScope.</span><span class="sxs-lookup"><span data-stu-id="897ba-216">The acceptable values for this parameter are: are None, ReadOnly, Constant, Private, or AllScope.</span></span>

<span data-ttu-id="897ba-217">Bijvoorbeeld: `@{Name="WarningPreference";Value="SilentlyContinue";Options="AllScope"}`</span><span class="sxs-lookup"><span data-stu-id="897ba-217">For example: `@{Name="WarningPreference";Value="SilentlyContinue";Options="AllScope"}`</span></span>

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

### <span data-ttu-id="897ba-218">-VisibleAliases</span><span class="sxs-lookup"><span data-stu-id="897ba-218">-VisibleAliases</span></span>

<span data-ttu-id="897ba-219">Beperkt de aliassen in de sessie met de aliassen die zijn opgegeven in de waarde van deze para meter, plus alle aliassen die u definieert in de para meter **AliasDefinition** .</span><span class="sxs-lookup"><span data-stu-id="897ba-219">Limits the aliases in the session to those aliases specified in the value of this parameter, plus any aliases that you define in the **AliasDefinition** parameter.</span></span> <span data-ttu-id="897ba-220">Joker tekens worden ondersteund.</span><span class="sxs-lookup"><span data-stu-id="897ba-220">Wildcard characters are supported.</span></span>
<span data-ttu-id="897ba-221">Standaard worden alle aliassen die zijn gedefinieerd door de Power shell-engine en alle aliassen die modules exporteren, weer gegeven in de sessie.</span><span class="sxs-lookup"><span data-stu-id="897ba-221">By default, all aliases that are defined by the PowerShell engine and all aliases that modules export are visible in the session.</span></span>

<span data-ttu-id="897ba-222">Als u bijvoorbeeld de beschik bare aliassen wilt beperken tot GM en GCM, gebruikt u de volgende syntaxis: `VisibleAliases="gcm", "gp"`</span><span class="sxs-lookup"><span data-stu-id="897ba-222">For example, to limit the available aliases to gm and gcm use this syntax: `VisibleAliases="gcm", "gp"`</span></span>

<span data-ttu-id="897ba-223">Wanneer een **zicht bare** para meter is opgenomen in het functie-Capability-bestand, verwijdert Power shell de `Import-Module` cmdlet en de bijbehorende `ipmo` alias uit de sessie.</span><span class="sxs-lookup"><span data-stu-id="897ba-223">When any **Visible** parameter is included in the role capability file, PowerShell removes the `Import-Module` cmdlet and its `ipmo` alias from the session.</span></span>

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

### <span data-ttu-id="897ba-224">-VisibleCmdlets</span><span class="sxs-lookup"><span data-stu-id="897ba-224">-VisibleCmdlets</span></span>

<span data-ttu-id="897ba-225">Hiermee worden de cmdlets in de sessie beperkt tot die welke zijn opgegeven in de waarde van deze para meter.</span><span class="sxs-lookup"><span data-stu-id="897ba-225">Limits the cmdlets in the session to those specified in the value of this parameter.</span></span> <span data-ttu-id="897ba-226">Joker tekens en modules met gekwalificeerde namen worden ondersteund.</span><span class="sxs-lookup"><span data-stu-id="897ba-226">Wildcard characters and Module Qualified Names are supported.</span></span>

<span data-ttu-id="897ba-227">Standaard worden alle cmdlets die de modules in de sessie exporteren, weer gegeven in de sessie.</span><span class="sxs-lookup"><span data-stu-id="897ba-227">By default, all cmdlets that the modules in the session export are visible in the session.</span></span> <span data-ttu-id="897ba-228">Gebruik de para meters **SessionType** en **ModulesToImport** om te bepalen welke modules en modules in de sessie worden geïmporteerd.</span><span class="sxs-lookup"><span data-stu-id="897ba-228">Use the **SessionType** and **ModulesToImport** parameters to determine which modules and snap-ins are imported into the session.</span></span> <span data-ttu-id="897ba-229">Als er geen modules in **ModulesToImport** de cmdlet beschikbaar maken, `New-PSRoleCapabilityFile` probeert de juiste module te laden.</span><span class="sxs-lookup"><span data-stu-id="897ba-229">If no modules in **ModulesToImport** expose the cmdlet, `New-PSRoleCapabilityFile` tries to load the appropriate module.</span></span>

<span data-ttu-id="897ba-230">Wanneer een **zicht bare** para meter is opgenomen in het configuratie bestand van de sessie, verwijdert Power shell de `Import-Module` cmdlet en de bijbehorende `ipmo` alias uit de sessie.</span><span class="sxs-lookup"><span data-stu-id="897ba-230">When any **Visible** parameter is included in the session configuration file, PowerShell removes the `Import-Module` cmdlet and its `ipmo` alias from the session.</span></span>

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

### <span data-ttu-id="897ba-231">-VisibleExternalCommands</span><span class="sxs-lookup"><span data-stu-id="897ba-231">-VisibleExternalCommands</span></span>

<span data-ttu-id="897ba-232">Hiermee beperkt u de externe binaire bestanden, scripts en opdrachten die in de sessie kunnen worden uitgevoerd en die zijn opgegeven in de waarde van deze para meter.</span><span class="sxs-lookup"><span data-stu-id="897ba-232">Limits the external binaries, scripts and commands that can be executed in the session to those specified in the value of this parameter.</span></span>

<span data-ttu-id="897ba-233">Standaard zijn er in deze sessie geen externe opdrachten zichtbaar.</span><span class="sxs-lookup"><span data-stu-id="897ba-233">By default, no external commands are visible in this session.</span></span>

<span data-ttu-id="897ba-234">Wanneer een **zicht bare** para meter is opgenomen in het configuratie bestand van de sessie, verwijdert Power shell de `Import-Module` cmdlet en de bijbehorende `ipmo` alias uit de sessie.</span><span class="sxs-lookup"><span data-stu-id="897ba-234">When any **Visible** parameter is included in the session configuration file, PowerShell removes the `Import-Module` cmdlet and its `ipmo` alias from the session.</span></span>

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

### <span data-ttu-id="897ba-235">-VisibleFunctions</span><span class="sxs-lookup"><span data-stu-id="897ba-235">-VisibleFunctions</span></span>

<span data-ttu-id="897ba-236">Hiermee beperkt u de functies in de sessie die zijn opgegeven in de waarde van deze para meter, plus de functies die u definieert in de para meter **FunctionDefinitions** .</span><span class="sxs-lookup"><span data-stu-id="897ba-236">Limits the functions in the session to those specified in the value of this parameter, plus any functions that you define in the **FunctionDefinitions** parameter.</span></span> <span data-ttu-id="897ba-237">Joker tekens worden ondersteund.</span><span class="sxs-lookup"><span data-stu-id="897ba-237">Wildcard characters are supported.</span></span>

<span data-ttu-id="897ba-238">Standaard zijn alle functies die door modules in de sessie worden geëxporteerd, zichtbaar in die sessie.</span><span class="sxs-lookup"><span data-stu-id="897ba-238">By default, all functions exported by modules in the session are visible in that session.</span></span> <span data-ttu-id="897ba-239">Gebruik de para meters **SessionType** en **ModulesToImport** om te bepalen welke modules in de sessie worden geïmporteerd.</span><span class="sxs-lookup"><span data-stu-id="897ba-239">Use the **SessionType** and **ModulesToImport** parameters to determine which modules are imported into the session.</span></span>

<span data-ttu-id="897ba-240">Wanneer een **zicht bare** para meter is opgenomen in het configuratie bestand van de sessie, verwijdert Power shell de `Import-Module` cmdlet en de bijbehorende `ipmo` alias uit de sessie.</span><span class="sxs-lookup"><span data-stu-id="897ba-240">When any **Visible** parameter is included in the session configuration file, PowerShell removes the `Import-Module` cmdlet and its `ipmo` alias from the session.</span></span>

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

### <span data-ttu-id="897ba-241">-VisibleProviders</span><span class="sxs-lookup"><span data-stu-id="897ba-241">-VisibleProviders</span></span>

<span data-ttu-id="897ba-242">Hiermee worden de Power shell-providers in de sessie beperkt tot die welke zijn opgegeven in de waarde van deze para meter.</span><span class="sxs-lookup"><span data-stu-id="897ba-242">Limits the PowerShell providers in the session to those specified in the value of this parameter.</span></span>
<span data-ttu-id="897ba-243">Joker tekens worden ondersteund.</span><span class="sxs-lookup"><span data-stu-id="897ba-243">Wildcard characters are supported.</span></span>

<span data-ttu-id="897ba-244">Standaard worden alle providers die zijn geëxporteerd door een module in de sessie, weer gegeven in de sessie.</span><span class="sxs-lookup"><span data-stu-id="897ba-244">By default, all providers exported by a module in the session are visible in the session.</span></span> <span data-ttu-id="897ba-245">Gebruik de para meters **SessionType** en **ModulesToImport** om te bepalen welke modules in de sessie worden geïmporteerd.</span><span class="sxs-lookup"><span data-stu-id="897ba-245">Use the **SessionType** and **ModulesToImport** parameters to determine which modules are imported into the session.</span></span>

<span data-ttu-id="897ba-246">Wanneer een **zicht bare** para meter is opgenomen in het configuratie bestand van de sessie, verwijdert Power shell de `Import-Module` cmdlet en de bijbehorende `ipmo` alias uit de sessie.</span><span class="sxs-lookup"><span data-stu-id="897ba-246">When any **Visible** parameter is included in the session configuration file, PowerShell removes the `Import-Module` cmdlet and its `ipmo` alias from the session.</span></span>

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

### <span data-ttu-id="897ba-247">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="897ba-247">CommonParameters</span></span>

<span data-ttu-id="897ba-248">Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="897ba-248">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="897ba-249">Zie [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="897ba-249">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="897ba-250">INVOER</span><span class="sxs-lookup"><span data-stu-id="897ba-250">INPUTS</span></span>

## <span data-ttu-id="897ba-251">UITVOER</span><span class="sxs-lookup"><span data-stu-id="897ba-251">OUTPUTS</span></span>

## <span data-ttu-id="897ba-252">OPMERKINGEN</span><span class="sxs-lookup"><span data-stu-id="897ba-252">NOTES</span></span>

## <span data-ttu-id="897ba-253">GERELATEERDE KOPPELINGEN</span><span class="sxs-lookup"><span data-stu-id="897ba-253">RELATED LINKS</span></span>

[<span data-ttu-id="897ba-254">New-PSSessionConfigurationFile</span><span class="sxs-lookup"><span data-stu-id="897ba-254">New-PSSessionConfigurationFile</span></span>](New-PSSessionConfigurationFile.md)

[<span data-ttu-id="897ba-255">Get-PSSessionCapability</span><span class="sxs-lookup"><span data-stu-id="897ba-255">Get-PSSessionCapability</span></span>](Get-PSSessionCapability.md)

