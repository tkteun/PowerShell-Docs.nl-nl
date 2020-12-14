---
external help file: PSModule-help.xml
Locale: en-US
Module Name: PowerShellGet
ms.date: 07/08/2019
online version: https://docs.microsoft.com/powershell/module/powershellget/update-modulemanifest?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Update-ModuleManifest
ms.openlocfilehash: 4f00450257178cac72d03303358150fd9f5cd26b
ms.sourcegitcommit: 22c93550c87af30c4895fcb9e9dd65e30d60ada0
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 11/19/2020
ms.locfileid: "94891820"
---
# <span data-ttu-id="141af-102">Update-ModuleManifest</span><span class="sxs-lookup"><span data-stu-id="141af-102">Update-ModuleManifest</span></span>

## <span data-ttu-id="141af-103">SAMENVATTING</span><span class="sxs-lookup"><span data-stu-id="141af-103">SYNOPSIS</span></span>
<span data-ttu-id="141af-104">Hiermee wordt een manifest bestand van de module bijgewerkt.</span><span class="sxs-lookup"><span data-stu-id="141af-104">Updates a module manifest file.</span></span>

## <span data-ttu-id="141af-105">SYNTAXIS</span><span class="sxs-lookup"><span data-stu-id="141af-105">SYNTAX</span></span>

### <span data-ttu-id="141af-106">Alles</span><span class="sxs-lookup"><span data-stu-id="141af-106">All</span></span>

```
Update-ModuleManifest [-Path] <String> [-NestedModules <Object[]>] [-Guid <Guid>] [-Author <String>]
 [-CompanyName <String>] [-Copyright <String>] [-RootModule <String>] [-ModuleVersion <Version>]
 [-Description <String>] [-ProcessorArchitecture <ProcessorArchitecture>]
 [-CompatiblePSEditions <String[]>] [-PowerShellVersion <Version>] [-ClrVersion <Version>]
 [-DotNetFrameworkVersion <Version>] [-PowerShellHostName <String>]
 [-PowerShellHostVersion <Version>] [-RequiredModules <Object[]>] [-TypesToProcess <String[]>]
 [-FormatsToProcess <String[]>] [-ScriptsToProcess <String[]>] [-RequiredAssemblies <String[]>]
 [-FileList <String[]>] [-ModuleList <Object[]>] [-FunctionsToExport <String[]>]
 [-AliasesToExport <String[]>] [-VariablesToExport <String[]>] [-CmdletsToExport <String[]>]
 [-DscResourcesToExport <String[]>] [-PrivateData <Hashtable>] [-Tags <String[]>]
 [-ProjectUri <Uri>] [-LicenseUri <Uri>] [-IconUri <Uri>] [-ReleaseNotes <String[]>]
 [-Prerelease <String>] [-HelpInfoUri <Uri>] [-PassThru] [-DefaultCommandPrefix <String>]
 [-ExternalModuleDependencies <String[]>] [-PackageManagementProviders <String[]>]
 [-RequireLicenseAcceptance] [-WhatIf] [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="141af-107">BESCHRIJVING</span><span class="sxs-lookup"><span data-stu-id="141af-107">DESCRIPTION</span></span>

<span data-ttu-id="141af-108">Met de `Update-ModuleManifest` cmdlet wordt een module manifest `.psd1` bestand () bijgewerkt.</span><span class="sxs-lookup"><span data-stu-id="141af-108">The `Update-ModuleManifest` cmdlet updates a module manifest (`.psd1`) file.</span></span>

## <span data-ttu-id="141af-109">VOORBEELDEN</span><span class="sxs-lookup"><span data-stu-id="141af-109">EXAMPLES</span></span>

### <span data-ttu-id="141af-110">Voor beeld 1: een module manifest bijwerken</span><span class="sxs-lookup"><span data-stu-id="141af-110">Example 1: Update a module manifest</span></span>

<span data-ttu-id="141af-111">In dit voor beeld wordt een bestaand module manifest bestand bijgewerkt.</span><span class="sxs-lookup"><span data-stu-id="141af-111">This example updates an existing module manifest file.</span></span> <span data-ttu-id="141af-112">Splatting wordt gebruikt om parameter waarden door te geven aan `Update-ModuleManifest` .</span><span class="sxs-lookup"><span data-stu-id="141af-112">Splatting is used to pass parameter values to `Update-ModuleManifest`.</span></span> <span data-ttu-id="141af-113">Zie [about_Splatting](../Microsoft.PowerShell.Core/About/about_Splatting.md)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="141af-113">For more information, see [about_Splatting](../Microsoft.PowerShell.Core/About/about_Splatting.md).</span></span>

```powershell
$Parms = @{
  Path = "C:\Test\TestManifest.psd1"
  Author = "TestUser1"
  CompanyName = "Contoso Corporation"
  Copyright = "(c) 2019 Contoso Corporation. All rights reserved."
}

Update-ModuleManifest @Parms
```

<span data-ttu-id="141af-114">`$Parms` is een splat die de parameter waarden voor **pad**, **Auteur**, **Bedrijfs naam** en **copyright** opslaat.</span><span class="sxs-lookup"><span data-stu-id="141af-114">`$Parms` is a splat that stores the parameter values for **Path**, **Author**, **CompanyName**, and **Copyright**.</span></span> <span data-ttu-id="141af-115">`Update-ModuleManifest` Hiermee worden de parameter waarden opgehaald uit `@Parms` en wordt het module manifest bijgewerkt **TestManifest.psd1**.</span><span class="sxs-lookup"><span data-stu-id="141af-115">`Update-ModuleManifest` gets the parameter values from `@Parms` and updates the module manifest, **TestManifest.psd1**.</span></span>

## <span data-ttu-id="141af-116">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="141af-116">PARAMETERS</span></span>

### <span data-ttu-id="141af-117">-AliasesToExport</span><span class="sxs-lookup"><span data-stu-id="141af-117">-AliasesToExport</span></span>

<span data-ttu-id="141af-118">Hiermee geeft u de aliassen op die de module exporteert.</span><span class="sxs-lookup"><span data-stu-id="141af-118">Specifies the aliases that the module exports.</span></span> <span data-ttu-id="141af-119">Joker tekens zijn toegestaan.</span><span class="sxs-lookup"><span data-stu-id="141af-119">Wildcards are permitted.</span></span>

<span data-ttu-id="141af-120">Gebruik deze para meter om de aliassen te beperken die door de module worden geëxporteerd.</span><span class="sxs-lookup"><span data-stu-id="141af-120">Use this parameter to restrict the aliases that are exported by the module.</span></span> <span data-ttu-id="141af-121">**AliasesToExport** kan aliassen uit de lijst met geëxporteerde aliassen verwijderen, maar kan geen aliassen toevoegen aan de lijst.</span><span class="sxs-lookup"><span data-stu-id="141af-121">**AliasesToExport** can remove aliases from the list of exported aliases, but it can't add aliases to the list.</span></span>

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

### <span data-ttu-id="141af-122">-Author</span><span class="sxs-lookup"><span data-stu-id="141af-122">-Author</span></span>

<span data-ttu-id="141af-123">Hiermee geeft u de auteur van de module.</span><span class="sxs-lookup"><span data-stu-id="141af-123">Specifies the module author.</span></span>

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

### <span data-ttu-id="141af-124">-ClrVersion</span><span class="sxs-lookup"><span data-stu-id="141af-124">-ClrVersion</span></span>

<span data-ttu-id="141af-125">Hiermee geeft u de minimale versie van common language runtime (CLR) op van het Microsoft .NET Framework dat vereist is voor de module.</span><span class="sxs-lookup"><span data-stu-id="141af-125">Specifies the minimum version of the Common Language Runtime (CLR) of the Microsoft .NET Framework that the module requires.</span></span>

```yaml
Type: System.Version
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="141af-126">-CmdletsToExport</span><span class="sxs-lookup"><span data-stu-id="141af-126">-CmdletsToExport</span></span>

<span data-ttu-id="141af-127">Hiermee geeft u de cmdlets op die de module exporteert.</span><span class="sxs-lookup"><span data-stu-id="141af-127">Specifies the cmdlets that the module exports.</span></span> <span data-ttu-id="141af-128">Joker tekens zijn toegestaan.</span><span class="sxs-lookup"><span data-stu-id="141af-128">Wildcards are permitted.</span></span>

<span data-ttu-id="141af-129">Gebruik deze para meter om de cmdlets te beperken die door de module worden geëxporteerd.</span><span class="sxs-lookup"><span data-stu-id="141af-129">Use this parameter to restrict the cmdlets that are exported by the module.</span></span> <span data-ttu-id="141af-130">**CmdletsToExport** kan cmdlets uit de lijst geëxporteerde cmdlets verwijderen, maar kan geen cmdlets toevoegen aan de lijst.</span><span class="sxs-lookup"><span data-stu-id="141af-130">**CmdletsToExport** can remove cmdlets from the list of exported cmdlets, but it can't add cmdlets to the list.</span></span>

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

### <span data-ttu-id="141af-131">-CompanyName</span><span class="sxs-lookup"><span data-stu-id="141af-131">-CompanyName</span></span>

<span data-ttu-id="141af-132">Hiermee geeft u het bedrijf of de leverancier op die de module heeft gemaakt.</span><span class="sxs-lookup"><span data-stu-id="141af-132">Specifies the company or vendor who created the module.</span></span>

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

### <span data-ttu-id="141af-133">-CompatiblePSEditions</span><span class="sxs-lookup"><span data-stu-id="141af-133">-CompatiblePSEditions</span></span>

<span data-ttu-id="141af-134">Hiermee geeft u de compatibele **PSEditions** van de module op.</span><span class="sxs-lookup"><span data-stu-id="141af-134">Specifies the compatible **PSEditions** of the module.</span></span> <span data-ttu-id="141af-135">Zie [modules met compatibele Power shell-edities](/powershell/scripting/gallery/concepts/module-psedition-support)voor meer informatie over **PSEdition**.</span><span class="sxs-lookup"><span data-stu-id="141af-135">For information about **PSEdition**, see [Modules with compatible PowerShell Editions](/powershell/scripting/gallery/concepts/module-psedition-support).</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:
Accepted values: Desktop, Core

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="141af-136">-Confirm</span><span class="sxs-lookup"><span data-stu-id="141af-136">-Confirm</span></span>

<span data-ttu-id="141af-137">Vraagt u om bevestiging voordat deze wordt uitgevoerd `Update-ModuleManifest` .</span><span class="sxs-lookup"><span data-stu-id="141af-137">Prompts you for confirmation before running `Update-ModuleManifest`.</span></span>

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

### <span data-ttu-id="141af-138">-Copyright</span><span class="sxs-lookup"><span data-stu-id="141af-138">-Copyright</span></span>

<span data-ttu-id="141af-139">Hiermee geeft u een copyright verklaring voor de module op.</span><span class="sxs-lookup"><span data-stu-id="141af-139">Specifies a copyright statement for the module.</span></span>

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

### <span data-ttu-id="141af-140">-DefaultCommandPrefix</span><span class="sxs-lookup"><span data-stu-id="141af-140">-DefaultCommandPrefix</span></span>

<span data-ttu-id="141af-141">Hiermee geeft u het standaard voorvoegsel voor de opdracht op.</span><span class="sxs-lookup"><span data-stu-id="141af-141">Specifies the default command prefix.</span></span>

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

### <span data-ttu-id="141af-142">-Beschrijving</span><span class="sxs-lookup"><span data-stu-id="141af-142">-Description</span></span>

<span data-ttu-id="141af-143">Hiermee geeft u een beschrijving van de module.</span><span class="sxs-lookup"><span data-stu-id="141af-143">Specifies a description of the module.</span></span>

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

### <span data-ttu-id="141af-144">-DotNetFrameworkVersion</span><span class="sxs-lookup"><span data-stu-id="141af-144">-DotNetFrameworkVersion</span></span>

<span data-ttu-id="141af-145">Hiermee geeft u de minimale versie van het Microsoft .NET Framework op dat voor de module nodig is.</span><span class="sxs-lookup"><span data-stu-id="141af-145">Specifies the minimum version of the Microsoft .NET Framework that the module requires.</span></span>

```yaml
Type: System.Version
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="141af-146">-DscResourcesToExport</span><span class="sxs-lookup"><span data-stu-id="141af-146">-DscResourcesToExport</span></span>

<span data-ttu-id="141af-147">Hiermee geeft u de resources voor desired state Configuration (DSC) op die de module exporteert.</span><span class="sxs-lookup"><span data-stu-id="141af-147">Specifies the Desired State Configuration (DSC) resources that the module exports.</span></span> <span data-ttu-id="141af-148">Joker tekens zijn toegestaan.</span><span class="sxs-lookup"><span data-stu-id="141af-148">Wildcards are permitted.</span></span>

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

### <span data-ttu-id="141af-149">-ExternalModuleDependencies</span><span class="sxs-lookup"><span data-stu-id="141af-149">-ExternalModuleDependencies</span></span>

<span data-ttu-id="141af-150">Hiermee geeft u een matrix met externe module-afhankelijkheden op.</span><span class="sxs-lookup"><span data-stu-id="141af-150">Specifies an array of external module dependencies.</span></span>

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

### <span data-ttu-id="141af-151">-File List</span><span class="sxs-lookup"><span data-stu-id="141af-151">-FileList</span></span>

<span data-ttu-id="141af-152">Hiermee geeft u alle items die zijn opgenomen in de module.</span><span class="sxs-lookup"><span data-stu-id="141af-152">Specifies all items that are included in the module.</span></span>

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

### <span data-ttu-id="141af-153">-FormatsToProcess</span><span class="sxs-lookup"><span data-stu-id="141af-153">-FormatsToProcess</span></span>

<span data-ttu-id="141af-154">Hiermee geeft u de indelings bestanden ( `.ps1xml` ) op die worden uitgevoerd wanneer de module wordt geïmporteerd.</span><span class="sxs-lookup"><span data-stu-id="141af-154">Specifies the formatting files (`.ps1xml`) that run when the module is imported.</span></span>

<span data-ttu-id="141af-155">Wanneer u een module importeert, voert Power shell de `Update-FormatData` cmdlet uit met de opgegeven bestanden.</span><span class="sxs-lookup"><span data-stu-id="141af-155">When you import a module, PowerShell runs the `Update-FormatData` cmdlet with the specified files.</span></span>
<span data-ttu-id="141af-156">Omdat de indelings bestanden geen bereik hebben, hebben ze invloed op alle sessie statussen in de sessie.</span><span class="sxs-lookup"><span data-stu-id="141af-156">Because formatting files aren't scoped, they affect all session states in the session.</span></span>

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

### <span data-ttu-id="141af-157">-FunctionsToExport</span><span class="sxs-lookup"><span data-stu-id="141af-157">-FunctionsToExport</span></span>

<span data-ttu-id="141af-158">Hiermee geeft u de functies op die de module exporteert.</span><span class="sxs-lookup"><span data-stu-id="141af-158">Specifies the functions that the module exports.</span></span> <span data-ttu-id="141af-159">Joker tekens zijn toegestaan.</span><span class="sxs-lookup"><span data-stu-id="141af-159">Wildcards are permitted.</span></span>

<span data-ttu-id="141af-160">Gebruik deze para meter om de functies te beperken die door de module worden geëxporteerd.</span><span class="sxs-lookup"><span data-stu-id="141af-160">Use this parameter to restrict the functions that are exported by the module.</span></span> <span data-ttu-id="141af-161">**FunctionsToExport** kan functies uit de lijst met geëxporteerde aliassen verwijderen, maar kan geen functies toevoegen aan de lijst.</span><span class="sxs-lookup"><span data-stu-id="141af-161">**FunctionsToExport** can remove functions from the list of exported aliases, but it can't add functions to the list.</span></span>

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

### <span data-ttu-id="141af-162">-GUID</span><span class="sxs-lookup"><span data-stu-id="141af-162">-Guid</span></span>

<span data-ttu-id="141af-163">Hiermee geeft u een unieke id op voor de module.</span><span class="sxs-lookup"><span data-stu-id="141af-163">Specifies a unique identifier for the module.</span></span> <span data-ttu-id="141af-164">De GUID kan worden gebruikt om onderscheid te maken tussen modules met dezelfde naam.</span><span class="sxs-lookup"><span data-stu-id="141af-164">The GUID can be used to distinguish among modules with the same name.</span></span>

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

### <span data-ttu-id="141af-165">-HelpInfoUri</span><span class="sxs-lookup"><span data-stu-id="141af-165">-HelpInfoUri</span></span>

<span data-ttu-id="141af-166">Hiermee geeft u het Internet adres op van het **HelpInfo XML-** bestand van de module.</span><span class="sxs-lookup"><span data-stu-id="141af-166">Specifies the internet address of the module's **HelpInfo XML** file.</span></span> <span data-ttu-id="141af-167">Voer een URI (Uniform Resource Identifier) in die begint met **http** of **https**.</span><span class="sxs-lookup"><span data-stu-id="141af-167">Enter a Uniform Resource Identifier (URI) that begins with **http** or **https**.</span></span>

<span data-ttu-id="141af-168">Het **XML-bestand HelpInfo** ondersteunt de bijwerk bare Help-functie die is geïntroduceerd in Power shell versie 3,0.</span><span class="sxs-lookup"><span data-stu-id="141af-168">The **HelpInfo XML** file supports the Updatable Help feature that was introduced in PowerShell version 3.0.</span></span> <span data-ttu-id="141af-169">Het bevat informatie over de locatie van de Download bare Help bestanden van de module en de versie nummers van de nieuwste Help-bestanden voor elke ondersteunde land instelling.</span><span class="sxs-lookup"><span data-stu-id="141af-169">It contains information about the location of the module's downloadable help files and the version numbers of the newest help files for each supported locale.</span></span>

<span data-ttu-id="141af-170">Zie [about_Updatable_Help](../Microsoft.PowerShell.Core/About/about_Updatable_Help.md)voor meer informatie over de Help die kan worden bijgewerkt.</span><span class="sxs-lookup"><span data-stu-id="141af-170">For information about Updatable Help, see [about_Updatable_Help](../Microsoft.PowerShell.Core/About/about_Updatable_Help.md).</span></span>
<span data-ttu-id="141af-171">Zie voor meer informatie over het **HelpInfo XML-** bestand [ondersteunende Help](/powershell/scripting/developer/module/supporting-updatable-help).</span><span class="sxs-lookup"><span data-stu-id="141af-171">For information about the **HelpInfo XML** file, see [Supporting Updatable Help](/powershell/scripting/developer/module/supporting-updatable-help).</span></span>

```yaml
Type: System.Uri
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="141af-172">-IconUri</span><span class="sxs-lookup"><span data-stu-id="141af-172">-IconUri</span></span>

<span data-ttu-id="141af-173">Hiermee geeft u de URL op van een pictogram voor de module.</span><span class="sxs-lookup"><span data-stu-id="141af-173">Specifies the URL of an icon for the module.</span></span> <span data-ttu-id="141af-174">Het opgegeven pictogram wordt weer gegeven op de galerie webpagina voor de module.</span><span class="sxs-lookup"><span data-stu-id="141af-174">The specified icon is displayed on the gallery web page for the module.</span></span>

```yaml
Type: System.Uri
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="141af-175">-LicenseUri</span><span class="sxs-lookup"><span data-stu-id="141af-175">-LicenseUri</span></span>

<span data-ttu-id="141af-176">Hiermee geeft u de URL op van de licentie voorwaarden voor de module.</span><span class="sxs-lookup"><span data-stu-id="141af-176">Specifies the URL of licensing terms for the module.</span></span>

```yaml
Type: System.Uri
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="141af-177">-ModuleList</span><span class="sxs-lookup"><span data-stu-id="141af-177">-ModuleList</span></span>

<span data-ttu-id="141af-178">Hiermee geeft u een matrix met modules op die zijn opgenomen in de module.</span><span class="sxs-lookup"><span data-stu-id="141af-178">Specifies an array of modules that are included in the module.</span></span>

<span data-ttu-id="141af-179">Voer elke module naam in als een teken reeks of als een hash- **tabel met de** **ModuleVersion** -sleutels.</span><span class="sxs-lookup"><span data-stu-id="141af-179">Enter each module name as a string or as a hash table with **ModuleName** and **ModuleVersion** keys.</span></span> <span data-ttu-id="141af-180">De hash-tabel kan ook een optionele **GUID** -sleutel hebben.</span><span class="sxs-lookup"><span data-stu-id="141af-180">The hash table can also have an optional **GUID** key.</span></span> <span data-ttu-id="141af-181">U kunt teken reeksen en hash-tabellen combi neren in de parameter waarde.</span><span class="sxs-lookup"><span data-stu-id="141af-181">You can combine strings and hash tables in the parameter value.</span></span>

<span data-ttu-id="141af-182">Deze sleutel is ontworpen om te fungeren als een module-inventarisatie.</span><span class="sxs-lookup"><span data-stu-id="141af-182">This key is designed to act as a module inventory.</span></span> <span data-ttu-id="141af-183">De modules die in de waarde van deze sleutel worden vermeld, worden niet automatisch verwerkt.</span><span class="sxs-lookup"><span data-stu-id="141af-183">The modules that are listed in the value of this key aren't automatically processed.</span></span>

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

### <span data-ttu-id="141af-184">-ModuleVersion</span><span class="sxs-lookup"><span data-stu-id="141af-184">-ModuleVersion</span></span>

<span data-ttu-id="141af-185">Hiermee geeft u de versie van de module.</span><span class="sxs-lookup"><span data-stu-id="141af-185">Specifies the version of the module.</span></span>

```yaml
Type: System.Version
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="141af-186">-NestedModules</span><span class="sxs-lookup"><span data-stu-id="141af-186">-NestedModules</span></span>

<span data-ttu-id="141af-187">Hiermee geeft u script modules ( `.psm1` ) en binaire modules ( `.dll` ) op die worden geïmporteerd in de sessie status van de module.</span><span class="sxs-lookup"><span data-stu-id="141af-187">Specifies script modules (`.psm1`) and binary modules (`.dll`) that are imported into the module's session state.</span></span> <span data-ttu-id="141af-188">De bestanden in de **NestedModules** -sleutel worden uitgevoerd in de volg orde waarin ze worden weer gegeven in de waarde.</span><span class="sxs-lookup"><span data-stu-id="141af-188">The files in the **NestedModules** key run in the order in which they're listed in the value.</span></span>

<span data-ttu-id="141af-189">Voer elke module naam in als een teken reeks of als een hash- **tabel met de** **ModuleVersion** -sleutels.</span><span class="sxs-lookup"><span data-stu-id="141af-189">Enter each module name as a string or as a hash table with **ModuleName** and **ModuleVersion** keys.</span></span> <span data-ttu-id="141af-190">De hash-tabel kan ook een optionele **GUID** -sleutel hebben.</span><span class="sxs-lookup"><span data-stu-id="141af-190">The hash table can also have an optional **GUID** key.</span></span> <span data-ttu-id="141af-191">U kunt teken reeksen en hash-tabellen combi neren in de parameter waarde.</span><span class="sxs-lookup"><span data-stu-id="141af-191">You can combine strings and hash tables in the parameter value.</span></span>

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

### <span data-ttu-id="141af-192">-PackageManagementProviders</span><span class="sxs-lookup"><span data-stu-id="141af-192">-PackageManagementProviders</span></span>

<span data-ttu-id="141af-193">Hiermee wordt een matrix met pakket beheer providers opgegeven.</span><span class="sxs-lookup"><span data-stu-id="141af-193">Specifies an array of package management providers.</span></span>

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

### <span data-ttu-id="141af-194">-PassThru</span><span class="sxs-lookup"><span data-stu-id="141af-194">-PassThru</span></span>

<span data-ttu-id="141af-195">Retourneert een object dat het item vertegenwoordigt waarmee u werkt.</span><span class="sxs-lookup"><span data-stu-id="141af-195">Returns an object representing the item with which you're working.</span></span> <span data-ttu-id="141af-196">Standaard genereert geen `Update-ModuleManifest` uitvoer.</span><span class="sxs-lookup"><span data-stu-id="141af-196">By default, `Update-ModuleManifest` doesn't generate any output.</span></span>

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

### <span data-ttu-id="141af-197">-Path</span><span class="sxs-lookup"><span data-stu-id="141af-197">-Path</span></span>

<span data-ttu-id="141af-198">Hiermee geeft u het pad en de bestands naam van het module manifest.</span><span class="sxs-lookup"><span data-stu-id="141af-198">Specifies the path and file name of the module manifest.</span></span> <span data-ttu-id="141af-199">Voer een pad en een bestands naam in met een `.psd1` bestands extensie, zoals `$PSHOME\Modules\MyModule\MyModule.psd1` .</span><span class="sxs-lookup"><span data-stu-id="141af-199">Enter a path and file name with a `.psd1` file name extension, such as `$PSHOME\Modules\MyModule\MyModule.psd1`.</span></span>

<span data-ttu-id="141af-200">Als u het pad naar een bestaand bestand opgeeft, wordt `Update-ModuleManifest` het bestand vervangen zonder waarschuwing tenzij het bestand het kenmerk alleen-lezen heeft.</span><span class="sxs-lookup"><span data-stu-id="141af-200">If you specify the path to an existing file, `Update-ModuleManifest` replaces the file without warning unless the file has the read-only attribute.</span></span>

<span data-ttu-id="141af-201">Het manifest moet zich in de map van de module bevinden en de naam van het manifest bestand moet hetzelfde zijn als de mapnaam, maar met een `.psd1` extensie.</span><span class="sxs-lookup"><span data-stu-id="141af-201">The manifest should be located in the module's directory, and the manifest file name should be the same as the module directory name, but with a `.psd1` extension.</span></span>

<span data-ttu-id="141af-202">U kunt geen variabelen, zoals `$PSHOME` of, gebruiken als `$HOME` antwoord op een prompt voor een **pad** parameter waarde.</span><span class="sxs-lookup"><span data-stu-id="141af-202">You can't use variables, such as `$PSHOME` or `$HOME`, in response to a prompt for a **Path** parameter value.</span></span> <span data-ttu-id="141af-203">Als u een variabele wilt gebruiken, neemt u de para meter **Path** op in de opdracht.</span><span class="sxs-lookup"><span data-stu-id="141af-203">To use a variable, include the **Path** parameter in the command.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="141af-204">-PowerShellHostName</span><span class="sxs-lookup"><span data-stu-id="141af-204">-PowerShellHostName</span></span>

<span data-ttu-id="141af-205">Hiermee geeft u de naam op van het Power shell-hostprogramma dat is vereist voor de module.</span><span class="sxs-lookup"><span data-stu-id="141af-205">Specifies the name of the PowerShell host program that the module requires.</span></span> <span data-ttu-id="141af-206">Voer de naam van het hostprogramma in, zoals Power shell ISE host of ConsoleHost.</span><span class="sxs-lookup"><span data-stu-id="141af-206">Enter the name of the host program, such as PowerShell ISE Host or ConsoleHost.</span></span> <span data-ttu-id="141af-207">Joker tekens zijn niet toegestaan.</span><span class="sxs-lookup"><span data-stu-id="141af-207">Wildcards aren't permitted.</span></span>

<span data-ttu-id="141af-208">Als u de naam van een hostprogramma wilt zoeken, typt u in het programma `$Host.Name` .</span><span class="sxs-lookup"><span data-stu-id="141af-208">To find the name of a host program, in the program, type `$Host.Name`.</span></span>

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

### <span data-ttu-id="141af-209">-PowerShellHostVersion</span><span class="sxs-lookup"><span data-stu-id="141af-209">-PowerShellHostVersion</span></span>

<span data-ttu-id="141af-210">Hiermee geeft u de minimale versie van het Power shell-hostprogramma op dat met de module werkt.</span><span class="sxs-lookup"><span data-stu-id="141af-210">Specifies the minimum version of the PowerShell host program that works with the module.</span></span> <span data-ttu-id="141af-211">Voer een versie nummer in, bijvoorbeeld 1,1.</span><span class="sxs-lookup"><span data-stu-id="141af-211">Enter a version number, such as 1.1.</span></span>

```yaml
Type: System.Version
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="141af-212">-PowerShellVersion</span><span class="sxs-lookup"><span data-stu-id="141af-212">-PowerShellVersion</span></span>

<span data-ttu-id="141af-213">Hiermee geeft u de minimale versie van Power shell op die met deze module kan worden gebruikt.</span><span class="sxs-lookup"><span data-stu-id="141af-213">Specifies the minimum version of PowerShell that will work with this module.</span></span> <span data-ttu-id="141af-214">U kunt bijvoorbeeld 3,0, 4,0 of 5,0 opgeven als de waarde van deze para meter.</span><span class="sxs-lookup"><span data-stu-id="141af-214">For example, you can specify 3.0, 4.0, or 5.0 as the value of this parameter.</span></span>

```yaml
Type: System.Version
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="141af-215">-Prerelease</span><span class="sxs-lookup"><span data-stu-id="141af-215">-Prerelease</span></span>

<span data-ttu-id="141af-216">Hiermee wordt aangegeven dat de module Prerelease is.</span><span class="sxs-lookup"><span data-stu-id="141af-216">Indicates the module is prerelease.</span></span>

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

### <span data-ttu-id="141af-217">-PrivateData</span><span class="sxs-lookup"><span data-stu-id="141af-217">-PrivateData</span></span>

<span data-ttu-id="141af-218">Hiermee geeft u de gegevens op die worden door gegeven aan de module wanneer deze wordt geïmporteerd.</span><span class="sxs-lookup"><span data-stu-id="141af-218">Specifies data that is passed to the module when it's imported.</span></span>

```yaml
Type: System.Collections.Hashtable
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="141af-219">-ProcessorArchitecture</span><span class="sxs-lookup"><span data-stu-id="141af-219">-ProcessorArchitecture</span></span>

<span data-ttu-id="141af-220">Hiermee geeft u de processor architectuur op die de module vereist.</span><span class="sxs-lookup"><span data-stu-id="141af-220">Specifies the processor architecture that the module requires.</span></span>

<span data-ttu-id="141af-221">De aanvaardbare waarden voor deze parameter zijn:</span><span class="sxs-lookup"><span data-stu-id="141af-221">The acceptable values for this parameter are:</span></span>

- <span data-ttu-id="141af-222">Amd64</span><span class="sxs-lookup"><span data-stu-id="141af-222">Amd64</span></span>
- <span data-ttu-id="141af-223">Scherp</span><span class="sxs-lookup"><span data-stu-id="141af-223">Arm</span></span>
- <span data-ttu-id="141af-224">64</span><span class="sxs-lookup"><span data-stu-id="141af-224">IA64</span></span>
- <span data-ttu-id="141af-225">MSIL</span><span class="sxs-lookup"><span data-stu-id="141af-225">MSIL</span></span>
- <span data-ttu-id="141af-226">Geen (onbekend of niet opgegeven)</span><span class="sxs-lookup"><span data-stu-id="141af-226">None (unknown or unspecified)</span></span>
- <span data-ttu-id="141af-227">X86</span><span class="sxs-lookup"><span data-stu-id="141af-227">X86</span></span>

```yaml
Type: System.Reflection.ProcessorArchitecture
Parameter Sets: (All)
Aliases:
Accepted values: None, MSIL, X86, IA64, Amd64, Arm

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="141af-228">-ProjectUri</span><span class="sxs-lookup"><span data-stu-id="141af-228">-ProjectUri</span></span>

<span data-ttu-id="141af-229">Hiermee geeft u de URL van een webpagina over dit project op.</span><span class="sxs-lookup"><span data-stu-id="141af-229">Specifies the URL of a web page about this project.</span></span>

```yaml
Type: System.Uri
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="141af-230">-ReleaseNotes</span><span class="sxs-lookup"><span data-stu-id="141af-230">-ReleaseNotes</span></span>

<span data-ttu-id="141af-231">Hiermee geeft u een teken reeks matrix met release opmerkingen of opmerkingen die u beschikbaar wilt stellen voor deze versie van het script.</span><span class="sxs-lookup"><span data-stu-id="141af-231">Specifies a string array that contains release notes or comments that you want available for this version of the script.</span></span>

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

### <span data-ttu-id="141af-232">-RequireLicenseAcceptance</span><span class="sxs-lookup"><span data-stu-id="141af-232">-RequireLicenseAcceptance</span></span>

<span data-ttu-id="141af-233">Hiermee geeft u op dat een acceptatie van de licentie is vereist voor de module.</span><span class="sxs-lookup"><span data-stu-id="141af-233">Specifies that a license acceptance is required for the module.</span></span>

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

### <span data-ttu-id="141af-234">-RequiredAssemblies</span><span class="sxs-lookup"><span data-stu-id="141af-234">-RequiredAssemblies</span></span>

<span data-ttu-id="141af-235">Hiermee geeft u de assembly ( `.dll` )-bestanden op die de module vereist.</span><span class="sxs-lookup"><span data-stu-id="141af-235">Specifies the assembly (`.dll`) files that the module requires.</span></span> <span data-ttu-id="141af-236">Voer de namen van de assembly bestanden in.</span><span class="sxs-lookup"><span data-stu-id="141af-236">Enter the assembly file names.</span></span>
<span data-ttu-id="141af-237">Power shell laadt de opgegeven assembly's vóór het bijwerken van typen of indelingen, het importeren van geneste modules of het importeren van het module bestand dat is opgegeven in de waarde van de sleutel **RootModule** .</span><span class="sxs-lookup"><span data-stu-id="141af-237">PowerShell loads the specified assemblies before updating types or formats, importing nested modules, or importing the module file that is specified in the value of the **RootModule** key.</span></span>

<span data-ttu-id="141af-238">Gebruik deze para meter om alle assembly's op te geven die de module vereist, inclusief de assembly's die moeten worden geladen voor het bijwerken van de opmaak of het type van bestanden die worden vermeld in de sleutels **FormatsToProcess** of **TypesToProcess** , zelfs als deze assembly's ook worden vermeld als binaire modules in de **NestedModules** -sleutel.</span><span class="sxs-lookup"><span data-stu-id="141af-238">Use this parameter to specify all the assemblies that the module requires, including assemblies that must be loaded to update any formatting or type files that are listed in the **FormatsToProcess** or **TypesToProcess** keys, even if those assemblies are also listed as binary modules in the **NestedModules** key.</span></span>

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

### <span data-ttu-id="141af-239">-RequiredModules</span><span class="sxs-lookup"><span data-stu-id="141af-239">-RequiredModules</span></span>

<span data-ttu-id="141af-240">Hiermee worden modules opgegeven die de algemene sessie status moeten hebben.</span><span class="sxs-lookup"><span data-stu-id="141af-240">Specifies modules that must be in the global session state.</span></span> <span data-ttu-id="141af-241">Als de vereiste modules zich niet in de globale sessie status bevinden, worden ze door Power shell geïmporteerd.</span><span class="sxs-lookup"><span data-stu-id="141af-241">If the required modules aren't in the global session state, PowerShell imports them.</span></span> <span data-ttu-id="141af-242">Als de vereiste modules niet beschikbaar zijn, `Import-Module` mislukt de opdracht.</span><span class="sxs-lookup"><span data-stu-id="141af-242">If the required modules aren't available, the `Import-Module` command fails.</span></span>

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

### <span data-ttu-id="141af-243">-RootModule</span><span class="sxs-lookup"><span data-stu-id="141af-243">-RootModule</span></span>

<span data-ttu-id="141af-244">Hiermee geeft u het primaire of hoofd bestand van de module op.</span><span class="sxs-lookup"><span data-stu-id="141af-244">Specifies the primary or root file of the module.</span></span> <span data-ttu-id="141af-245">Voer de bestands naam van een script ( `.ps1` ), een script module ( `.psm1` ), een module manifest ( `.psd1` ), een assembly ( `.dll` ), een XML-bestand voor de cmdlet-definitie ( `.cdxml` ) of een werk stroom ( `.xaml` ) in.</span><span class="sxs-lookup"><span data-stu-id="141af-245">Enter the file name of a script (`.ps1`), a script module (`.psm1`), a module manifest (`.psd1`), an assembly (`.dll`), a cmdlet definition XML file (`.cdxml`), or a workflow (`.xaml`).</span></span> <span data-ttu-id="141af-246">Wanneer de module wordt geïmporteerd, worden de leden die worden geëxporteerd uit het hoofd module bestand geïmporteerd in de sessie status van de aanroeper.</span><span class="sxs-lookup"><span data-stu-id="141af-246">When the module is imported, the members that are exported from the root module file are imported into the caller's session state.</span></span>

<span data-ttu-id="141af-247">Als een module een manifest bestand heeft en er geen hoofd bestand is opgegeven in de **RootModule** -sleutel, wordt het manifest het primaire bestand voor de module.</span><span class="sxs-lookup"><span data-stu-id="141af-247">If a module has a manifest file and no root file has been specified in the **RootModule** key, the manifest becomes the primary file for the module.</span></span> <span data-ttu-id="141af-248">En wordt de module een manifest module (module type = manifest).</span><span class="sxs-lookup"><span data-stu-id="141af-248">And, the module becomes a manifest module (ModuleType = Manifest).</span></span>

<span data-ttu-id="141af-249">Als u leden wilt exporteren uit `.psm1` of `.dll` bestanden in een module met een manifest, moeten de namen van die bestanden worden opgegeven in de waarden van de sleutels **RootModule** of **NestedModules** in het manifest.</span><span class="sxs-lookup"><span data-stu-id="141af-249">To export members from `.psm1` or `.dll` files in a module that has a manifest, the names of those files must be specified in the values of the **RootModule** or **NestedModules** keys in the manifest.</span></span> <span data-ttu-id="141af-250">Anders worden de leden niet geëxporteerd.</span><span class="sxs-lookup"><span data-stu-id="141af-250">Otherwise, their members aren't exported.</span></span>

<span data-ttu-id="141af-251">In Power Shell 2,0 is deze sleutel **ModuleToProcess** genoemd.</span><span class="sxs-lookup"><span data-stu-id="141af-251">In PowerShell 2.0, this key was called **ModuleToProcess**.</span></span>

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

### <span data-ttu-id="141af-252">-ScriptsToProcess</span><span class="sxs-lookup"><span data-stu-id="141af-252">-ScriptsToProcess</span></span>

<span data-ttu-id="141af-253">Hiermee geeft u script ( `.ps1` )-bestanden op die worden uitgevoerd in de sessie status van de aanroeper wanneer de module wordt geïmporteerd.</span><span class="sxs-lookup"><span data-stu-id="141af-253">Specifies script (`.ps1`) files that run in the caller's session state when the module is imported.</span></span>
<span data-ttu-id="141af-254">U kunt deze scripts gebruiken om een omgeving voor te bereiden, net zoals u een aanmeldings script zou kunnen gebruiken.</span><span class="sxs-lookup"><span data-stu-id="141af-254">You can use these scripts to prepare an environment, just as you might use a login script.</span></span>

<span data-ttu-id="141af-255">Als u scripts wilt opgeven die worden uitgevoerd in de sessie status van de module, gebruikt u de sleutel **NestedModules** .</span><span class="sxs-lookup"><span data-stu-id="141af-255">To specify scripts that run in the module's session state, use the **NestedModules** key.</span></span>

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

### <span data-ttu-id="141af-256">-Tags</span><span class="sxs-lookup"><span data-stu-id="141af-256">-Tags</span></span>

<span data-ttu-id="141af-257">Hiermee geeft u een matrix met tags op.</span><span class="sxs-lookup"><span data-stu-id="141af-257">Specifies an array of tags.</span></span>

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

### <span data-ttu-id="141af-258">-TypesToProcess</span><span class="sxs-lookup"><span data-stu-id="141af-258">-TypesToProcess</span></span>

<span data-ttu-id="141af-259">Hiermee geeft u het type bestanden ( `.ps1xml` ) op dat wordt uitgevoerd wanneer de module wordt geïmporteerd.</span><span class="sxs-lookup"><span data-stu-id="141af-259">Specifies the type files (`.ps1xml`) that run when the module is imported.</span></span>

<span data-ttu-id="141af-260">Wanneer u de module importeert, voert Power shell de `Update-TypeData` cmdlet uit met de opgegeven bestanden.</span><span class="sxs-lookup"><span data-stu-id="141af-260">When you import the module, PowerShell runs the `Update-TypeData` cmdlet with the specified files.</span></span>
<span data-ttu-id="141af-261">Omdat type bestanden geen bereik hebben, hebben ze invloed op alle sessie statussen in de sessie.</span><span class="sxs-lookup"><span data-stu-id="141af-261">Because type files aren't scoped, they affect all session states in the session.</span></span>

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

### <span data-ttu-id="141af-262">-VariablesToExport</span><span class="sxs-lookup"><span data-stu-id="141af-262">-VariablesToExport</span></span>

<span data-ttu-id="141af-263">Hiermee geeft u de variabelen op die de module exporteert.</span><span class="sxs-lookup"><span data-stu-id="141af-263">Specifies the variables that the module exports.</span></span> <span data-ttu-id="141af-264">Joker tekens zijn toegestaan.</span><span class="sxs-lookup"><span data-stu-id="141af-264">Wildcards are permitted.</span></span>

<span data-ttu-id="141af-265">Gebruik deze para meter om de variabelen te beperken die door de module worden geëxporteerd.</span><span class="sxs-lookup"><span data-stu-id="141af-265">Use this parameter to restrict the variables that are exported by the module.</span></span> <span data-ttu-id="141af-266">**VariablesToExport** kan variabelen uit de lijst geëxporteerde variabelen verwijderen, maar kan geen variabelen toevoegen aan de lijst.</span><span class="sxs-lookup"><span data-stu-id="141af-266">**VariablesToExport** can remove variables from the list of exported variables, but it can't add variables to the list.</span></span>

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

### <span data-ttu-id="141af-267">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="141af-267">-WhatIf</span></span>

<span data-ttu-id="141af-268">Hier wordt weer gegeven wat er gebeurt als er `Update-ModuleManifest` wordt uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="141af-268">Shows what would happen if `Update-ModuleManifest` runs.</span></span> <span data-ttu-id="141af-269">De cmdlet wordt niet uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="141af-269">The cmdlet isn't run.</span></span>

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

### <span data-ttu-id="141af-270">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="141af-270">CommonParameters</span></span>

<span data-ttu-id="141af-271">Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="141af-271">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="141af-272">Zie [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="141af-272">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="141af-273">INVOER</span><span class="sxs-lookup"><span data-stu-id="141af-273">INPUTS</span></span>

### <span data-ttu-id="141af-274">System. String</span><span class="sxs-lookup"><span data-stu-id="141af-274">System.String</span></span>

## <span data-ttu-id="141af-275">UITVOER</span><span class="sxs-lookup"><span data-stu-id="141af-275">OUTPUTS</span></span>

### <span data-ttu-id="141af-276">System. object</span><span class="sxs-lookup"><span data-stu-id="141af-276">System.Object</span></span>

## <span data-ttu-id="141af-277">OPMERKINGEN</span><span class="sxs-lookup"><span data-stu-id="141af-277">NOTES</span></span>

> [!IMPORTANT]
> <span data-ttu-id="141af-278">Vanaf april 2020 biedt de PowerShell Gallery niet langer ondersteuning voor Transport Layer Security (TLS) versie 1,0 en 1,1.</span><span class="sxs-lookup"><span data-stu-id="141af-278">As of April 2020, the PowerShell Gallery no longer supports Transport Layer Security (TLS) versions 1.0 and 1.1.</span></span> <span data-ttu-id="141af-279">Als u geen TLS 1,2 of hoger gebruikt, wordt er een fout bericht weer gegeven wanneer u probeert toegang te krijgen tot de PowerShell Gallery.</span><span class="sxs-lookup"><span data-stu-id="141af-279">If you are not using TLS 1.2 or higher, you will receive an error when trying to access the PowerShell Gallery.</span></span> <span data-ttu-id="141af-280">Gebruik de volgende opdracht om ervoor te zorgen dat u TLS 1,2 gebruikt:</span><span class="sxs-lookup"><span data-stu-id="141af-280">Use the following command to ensure you are using TLS 1.2:</span></span>
>
> `[Net.ServicePointManager]::SecurityProtocol = [Net.SecurityProtocolType]::Tls12`
>
> <span data-ttu-id="141af-281">Zie de [aankondiging](https://devblogs.microsoft.com/powershell/powershell-gallery-tls-support/) in het Power shell-blog voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="141af-281">For more information, see the [announcement](https://devblogs.microsoft.com/powershell/powershell-gallery-tls-support/) in the PowerShell blog.</span></span>

## <span data-ttu-id="141af-282">GERELATEERDE KOPPELINGEN</span><span class="sxs-lookup"><span data-stu-id="141af-282">RELATED LINKS</span></span>
