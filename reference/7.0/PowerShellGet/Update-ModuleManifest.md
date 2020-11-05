---
external help file: PSModule-help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: PowerShellGet
ms.date: 07/08/2019
online version: https://docs.microsoft.com/powershell/module/powershellget/update-modulemanifest?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Update-ModuleManifest
ms.openlocfilehash: 81c58a09cb6c4e6cedcc7abfa832af7bb694b0e1
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/07/2020
ms.locfileid: "93251397"
---
# <span data-ttu-id="afedb-103">Update-ModuleManifest</span><span class="sxs-lookup"><span data-stu-id="afedb-103">Update-ModuleManifest</span></span>

## <span data-ttu-id="afedb-104">SAMENVATTING</span><span class="sxs-lookup"><span data-stu-id="afedb-104">SYNOPSIS</span></span>
<span data-ttu-id="afedb-105">Hiermee wordt een manifest bestand van de module bijgewerkt.</span><span class="sxs-lookup"><span data-stu-id="afedb-105">Updates a module manifest file.</span></span>

## <span data-ttu-id="afedb-106">SYNTAXIS</span><span class="sxs-lookup"><span data-stu-id="afedb-106">SYNTAX</span></span>

### <span data-ttu-id="afedb-107">Alles</span><span class="sxs-lookup"><span data-stu-id="afedb-107">All</span></span>

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

## <span data-ttu-id="afedb-108">BESCHRIJVING</span><span class="sxs-lookup"><span data-stu-id="afedb-108">DESCRIPTION</span></span>

<span data-ttu-id="afedb-109">Met de `Update-ModuleManifest` cmdlet wordt een module manifest `.psd1` bestand () bijgewerkt.</span><span class="sxs-lookup"><span data-stu-id="afedb-109">The `Update-ModuleManifest` cmdlet updates a module manifest (`.psd1`) file.</span></span>

## <span data-ttu-id="afedb-110">VOORBEELDEN</span><span class="sxs-lookup"><span data-stu-id="afedb-110">EXAMPLES</span></span>

### <span data-ttu-id="afedb-111">Voor beeld 1: een module manifest bijwerken</span><span class="sxs-lookup"><span data-stu-id="afedb-111">Example 1: Update a module manifest</span></span>

<span data-ttu-id="afedb-112">In dit voor beeld wordt een bestaand module manifest bestand bijgewerkt.</span><span class="sxs-lookup"><span data-stu-id="afedb-112">This example updates an existing module manifest file.</span></span> <span data-ttu-id="afedb-113">Splatting wordt gebruikt om parameter waarden door te geven aan `Update-ModuleManifest` .</span><span class="sxs-lookup"><span data-stu-id="afedb-113">Splatting is used to pass parameter values to `Update-ModuleManifest`.</span></span> <span data-ttu-id="afedb-114">Zie [about_Splatting](../Microsoft.PowerShell.Core/About/about_Splatting.md)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="afedb-114">For more information, see [about_Splatting](../Microsoft.PowerShell.Core/About/about_Splatting.md).</span></span>

```powershell
$Parms = @{
  Path = "C:\Test\TestManifest.psd1"
  Author = "TestUser1"
  CompanyName = "Contoso Corporation"
  Copyright = "(c) 2019 Contoso Corporation. All rights reserved."
}

Update-ModuleManifest @Parms
```

<span data-ttu-id="afedb-115">`$Parms` is een splat die de parameter waarden voor **pad** , **Auteur** , **Bedrijfs naam** en **copyright** opslaat.</span><span class="sxs-lookup"><span data-stu-id="afedb-115">`$Parms` is a splat that stores the parameter values for **Path** , **Author** , **CompanyName** , and **Copyright**.</span></span> <span data-ttu-id="afedb-116">`Update-ModuleManifest` Hiermee worden de parameter waarden opgehaald uit `@Parms` en wordt het module manifest bijgewerkt **TestManifest.psd1**.</span><span class="sxs-lookup"><span data-stu-id="afedb-116">`Update-ModuleManifest` gets the parameter values from `@Parms` and updates the module manifest, **TestManifest.psd1**.</span></span>

## <span data-ttu-id="afedb-117">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="afedb-117">PARAMETERS</span></span>

### <span data-ttu-id="afedb-118">-AliasesToExport</span><span class="sxs-lookup"><span data-stu-id="afedb-118">-AliasesToExport</span></span>

<span data-ttu-id="afedb-119">Hiermee geeft u de aliassen op die de module exporteert.</span><span class="sxs-lookup"><span data-stu-id="afedb-119">Specifies the aliases that the module exports.</span></span> <span data-ttu-id="afedb-120">Joker tekens zijn toegestaan.</span><span class="sxs-lookup"><span data-stu-id="afedb-120">Wildcards are permitted.</span></span>

<span data-ttu-id="afedb-121">Gebruik deze para meter om de aliassen te beperken die door de module worden geëxporteerd.</span><span class="sxs-lookup"><span data-stu-id="afedb-121">Use this parameter to restrict the aliases that are exported by the module.</span></span> <span data-ttu-id="afedb-122">**AliasesToExport** kan aliassen uit de lijst met geëxporteerde aliassen verwijderen, maar kan geen aliassen toevoegen aan de lijst.</span><span class="sxs-lookup"><span data-stu-id="afedb-122">**AliasesToExport** can remove aliases from the list of exported aliases, but it can't add aliases to the list.</span></span>

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

### <span data-ttu-id="afedb-123">-Author</span><span class="sxs-lookup"><span data-stu-id="afedb-123">-Author</span></span>

<span data-ttu-id="afedb-124">Hiermee geeft u de auteur van de module.</span><span class="sxs-lookup"><span data-stu-id="afedb-124">Specifies the module author.</span></span>

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

### <span data-ttu-id="afedb-125">-ClrVersion</span><span class="sxs-lookup"><span data-stu-id="afedb-125">-ClrVersion</span></span>

<span data-ttu-id="afedb-126">Hiermee geeft u de minimale versie van common language runtime (CLR) op van het Microsoft .NET Framework dat vereist is voor de module.</span><span class="sxs-lookup"><span data-stu-id="afedb-126">Specifies the minimum version of the Common Language Runtime (CLR) of the Microsoft .NET Framework that the module requires.</span></span>

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

### <span data-ttu-id="afedb-127">-CmdletsToExport</span><span class="sxs-lookup"><span data-stu-id="afedb-127">-CmdletsToExport</span></span>

<span data-ttu-id="afedb-128">Hiermee geeft u de cmdlets op die de module exporteert.</span><span class="sxs-lookup"><span data-stu-id="afedb-128">Specifies the cmdlets that the module exports.</span></span> <span data-ttu-id="afedb-129">Joker tekens zijn toegestaan.</span><span class="sxs-lookup"><span data-stu-id="afedb-129">Wildcards are permitted.</span></span>

<span data-ttu-id="afedb-130">Gebruik deze para meter om de cmdlets te beperken die door de module worden geëxporteerd.</span><span class="sxs-lookup"><span data-stu-id="afedb-130">Use this parameter to restrict the cmdlets that are exported by the module.</span></span> <span data-ttu-id="afedb-131">**CmdletsToExport** kan cmdlets uit de lijst geëxporteerde cmdlets verwijderen, maar kan geen cmdlets toevoegen aan de lijst.</span><span class="sxs-lookup"><span data-stu-id="afedb-131">**CmdletsToExport** can remove cmdlets from the list of exported cmdlets, but it can't add cmdlets to the list.</span></span>

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

### <span data-ttu-id="afedb-132">-CompanyName</span><span class="sxs-lookup"><span data-stu-id="afedb-132">-CompanyName</span></span>

<span data-ttu-id="afedb-133">Hiermee geeft u het bedrijf of de leverancier op die de module heeft gemaakt.</span><span class="sxs-lookup"><span data-stu-id="afedb-133">Specifies the company or vendor who created the module.</span></span>

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

### <span data-ttu-id="afedb-134">-CompatiblePSEditions</span><span class="sxs-lookup"><span data-stu-id="afedb-134">-CompatiblePSEditions</span></span>

<span data-ttu-id="afedb-135">Hiermee geeft u de compatibele **PSEditions** van de module op.</span><span class="sxs-lookup"><span data-stu-id="afedb-135">Specifies the compatible **PSEditions** of the module.</span></span> <span data-ttu-id="afedb-136">Zie [modules met compatibele Power shell-edities](/powershell/scripting/gallery/concepts/module-psedition-support)voor meer informatie over **PSEdition**.</span><span class="sxs-lookup"><span data-stu-id="afedb-136">For information about **PSEdition** , see [Modules with compatible PowerShell Editions](/powershell/scripting/gallery/concepts/module-psedition-support).</span></span>

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

### <span data-ttu-id="afedb-137">-Confirm</span><span class="sxs-lookup"><span data-stu-id="afedb-137">-Confirm</span></span>

<span data-ttu-id="afedb-138">Vraagt u om bevestiging voordat deze wordt uitgevoerd `Update-ModuleManifest` .</span><span class="sxs-lookup"><span data-stu-id="afedb-138">Prompts you for confirmation before running `Update-ModuleManifest`.</span></span>

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

### <span data-ttu-id="afedb-139">-Copyright</span><span class="sxs-lookup"><span data-stu-id="afedb-139">-Copyright</span></span>

<span data-ttu-id="afedb-140">Hiermee geeft u een copyright verklaring voor de module op.</span><span class="sxs-lookup"><span data-stu-id="afedb-140">Specifies a copyright statement for the module.</span></span>

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

### <span data-ttu-id="afedb-141">-DefaultCommandPrefix</span><span class="sxs-lookup"><span data-stu-id="afedb-141">-DefaultCommandPrefix</span></span>

<span data-ttu-id="afedb-142">Hiermee geeft u het standaard voorvoegsel voor de opdracht op.</span><span class="sxs-lookup"><span data-stu-id="afedb-142">Specifies the default command prefix.</span></span>

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

### <span data-ttu-id="afedb-143">-Beschrijving</span><span class="sxs-lookup"><span data-stu-id="afedb-143">-Description</span></span>

<span data-ttu-id="afedb-144">Hiermee geeft u een beschrijving van de module.</span><span class="sxs-lookup"><span data-stu-id="afedb-144">Specifies a description of the module.</span></span>

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

### <span data-ttu-id="afedb-145">-DotNetFrameworkVersion</span><span class="sxs-lookup"><span data-stu-id="afedb-145">-DotNetFrameworkVersion</span></span>

<span data-ttu-id="afedb-146">Hiermee geeft u de minimale versie van het Microsoft .NET Framework op dat voor de module nodig is.</span><span class="sxs-lookup"><span data-stu-id="afedb-146">Specifies the minimum version of the Microsoft .NET Framework that the module requires.</span></span>

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

### <span data-ttu-id="afedb-147">-DscResourcesToExport</span><span class="sxs-lookup"><span data-stu-id="afedb-147">-DscResourcesToExport</span></span>

<span data-ttu-id="afedb-148">Hiermee geeft u de resources voor desired state Configuration (DSC) op die de module exporteert.</span><span class="sxs-lookup"><span data-stu-id="afedb-148">Specifies the Desired State Configuration (DSC) resources that the module exports.</span></span> <span data-ttu-id="afedb-149">Joker tekens zijn toegestaan.</span><span class="sxs-lookup"><span data-stu-id="afedb-149">Wildcards are permitted.</span></span>

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

### <span data-ttu-id="afedb-150">-ExternalModuleDependencies</span><span class="sxs-lookup"><span data-stu-id="afedb-150">-ExternalModuleDependencies</span></span>

<span data-ttu-id="afedb-151">Hiermee geeft u een matrix met externe module-afhankelijkheden op.</span><span class="sxs-lookup"><span data-stu-id="afedb-151">Specifies an array of external module dependencies.</span></span>

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

### <span data-ttu-id="afedb-152">-File List</span><span class="sxs-lookup"><span data-stu-id="afedb-152">-FileList</span></span>

<span data-ttu-id="afedb-153">Hiermee geeft u alle items die zijn opgenomen in de module.</span><span class="sxs-lookup"><span data-stu-id="afedb-153">Specifies all items that are included in the module.</span></span>

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

### <span data-ttu-id="afedb-154">-FormatsToProcess</span><span class="sxs-lookup"><span data-stu-id="afedb-154">-FormatsToProcess</span></span>

<span data-ttu-id="afedb-155">Hiermee geeft u de indelings bestanden ( `.ps1xml` ) op die worden uitgevoerd wanneer de module wordt geïmporteerd.</span><span class="sxs-lookup"><span data-stu-id="afedb-155">Specifies the formatting files (`.ps1xml`) that run when the module is imported.</span></span>

<span data-ttu-id="afedb-156">Wanneer u een module importeert, voert Power shell de `Update-FormatData` cmdlet uit met de opgegeven bestanden.</span><span class="sxs-lookup"><span data-stu-id="afedb-156">When you import a module, PowerShell runs the `Update-FormatData` cmdlet with the specified files.</span></span>
<span data-ttu-id="afedb-157">Omdat de indelings bestanden geen bereik hebben, hebben ze invloed op alle sessie statussen in de sessie.</span><span class="sxs-lookup"><span data-stu-id="afedb-157">Because formatting files aren't scoped, they affect all session states in the session.</span></span>

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

### <span data-ttu-id="afedb-158">-FunctionsToExport</span><span class="sxs-lookup"><span data-stu-id="afedb-158">-FunctionsToExport</span></span>

<span data-ttu-id="afedb-159">Hiermee geeft u de functies op die de module exporteert.</span><span class="sxs-lookup"><span data-stu-id="afedb-159">Specifies the functions that the module exports.</span></span> <span data-ttu-id="afedb-160">Joker tekens zijn toegestaan.</span><span class="sxs-lookup"><span data-stu-id="afedb-160">Wildcards are permitted.</span></span>

<span data-ttu-id="afedb-161">Gebruik deze para meter om de functies te beperken die door de module worden geëxporteerd.</span><span class="sxs-lookup"><span data-stu-id="afedb-161">Use this parameter to restrict the functions that are exported by the module.</span></span> <span data-ttu-id="afedb-162">**FunctionsToExport** kan functies uit de lijst met geëxporteerde aliassen verwijderen, maar kan geen functies toevoegen aan de lijst.</span><span class="sxs-lookup"><span data-stu-id="afedb-162">**FunctionsToExport** can remove functions from the list of exported aliases, but it can't add functions to the list.</span></span>

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

### <span data-ttu-id="afedb-163">-GUID</span><span class="sxs-lookup"><span data-stu-id="afedb-163">-Guid</span></span>

<span data-ttu-id="afedb-164">Hiermee geeft u een unieke id op voor de module.</span><span class="sxs-lookup"><span data-stu-id="afedb-164">Specifies a unique identifier for the module.</span></span> <span data-ttu-id="afedb-165">De GUID kan worden gebruikt om onderscheid te maken tussen modules met dezelfde naam.</span><span class="sxs-lookup"><span data-stu-id="afedb-165">The GUID can be used to distinguish among modules with the same name.</span></span>

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

### <span data-ttu-id="afedb-166">-HelpInfoUri</span><span class="sxs-lookup"><span data-stu-id="afedb-166">-HelpInfoUri</span></span>

<span data-ttu-id="afedb-167">Hiermee geeft u het Internet adres op van het **HelpInfo XML-** bestand van de module.</span><span class="sxs-lookup"><span data-stu-id="afedb-167">Specifies the internet address of the module's **HelpInfo XML** file.</span></span> <span data-ttu-id="afedb-168">Voer een URI (Uniform Resource Identifier) in die begint met **http** of **https**.</span><span class="sxs-lookup"><span data-stu-id="afedb-168">Enter a Uniform Resource Identifier (URI) that begins with **http** or **https**.</span></span>

<span data-ttu-id="afedb-169">Het **XML-bestand HelpInfo** ondersteunt de bijwerk bare Help-functie die is geïntroduceerd in Power shell versie 3,0.</span><span class="sxs-lookup"><span data-stu-id="afedb-169">The **HelpInfo XML** file supports the Updatable Help feature that was introduced in PowerShell version 3.0.</span></span> <span data-ttu-id="afedb-170">Het bevat informatie over de locatie van de Download bare Help bestanden van de module en de versie nummers van de nieuwste Help-bestanden voor elke ondersteunde land instelling.</span><span class="sxs-lookup"><span data-stu-id="afedb-170">It contains information about the location of the module's downloadable help files and the version numbers of the newest help files for each supported locale.</span></span>

<span data-ttu-id="afedb-171">Zie [about_Updatable_Help](../Microsoft.PowerShell.Core/About/about_Updatable_Help.md)voor meer informatie over de Help die kan worden bijgewerkt.</span><span class="sxs-lookup"><span data-stu-id="afedb-171">For information about Updatable Help, see [about_Updatable_Help](../Microsoft.PowerShell.Core/About/about_Updatable_Help.md).</span></span>
<span data-ttu-id="afedb-172">Zie voor meer informatie over het **HelpInfo XML-** bestand [ondersteunende Help](/powershell/scripting/developer/module/supporting-updatable-help).</span><span class="sxs-lookup"><span data-stu-id="afedb-172">For information about the **HelpInfo XML** file, see [Supporting Updatable Help](/powershell/scripting/developer/module/supporting-updatable-help).</span></span>

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

### <span data-ttu-id="afedb-173">-IconUri</span><span class="sxs-lookup"><span data-stu-id="afedb-173">-IconUri</span></span>

<span data-ttu-id="afedb-174">Hiermee geeft u de URL op van een pictogram voor de module.</span><span class="sxs-lookup"><span data-stu-id="afedb-174">Specifies the URL of an icon for the module.</span></span> <span data-ttu-id="afedb-175">Het opgegeven pictogram wordt weer gegeven op de galerie webpagina voor de module.</span><span class="sxs-lookup"><span data-stu-id="afedb-175">The specified icon is displayed on the gallery web page for the module.</span></span>

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

### <span data-ttu-id="afedb-176">-LicenseUri</span><span class="sxs-lookup"><span data-stu-id="afedb-176">-LicenseUri</span></span>

<span data-ttu-id="afedb-177">Hiermee geeft u de URL op van de licentie voorwaarden voor de module.</span><span class="sxs-lookup"><span data-stu-id="afedb-177">Specifies the URL of licensing terms for the module.</span></span>

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

### <span data-ttu-id="afedb-178">-ModuleList</span><span class="sxs-lookup"><span data-stu-id="afedb-178">-ModuleList</span></span>

<span data-ttu-id="afedb-179">Hiermee geeft u een matrix met modules op die zijn opgenomen in de module.</span><span class="sxs-lookup"><span data-stu-id="afedb-179">Specifies an array of modules that are included in the module.</span></span>

<span data-ttu-id="afedb-180">Voer elke module naam in als een teken reeks of als een hash- **tabel met de** **ModuleVersion** -sleutels.</span><span class="sxs-lookup"><span data-stu-id="afedb-180">Enter each module name as a string or as a hash table with **ModuleName** and **ModuleVersion** keys.</span></span> <span data-ttu-id="afedb-181">De hash-tabel kan ook een optionele **GUID** -sleutel hebben.</span><span class="sxs-lookup"><span data-stu-id="afedb-181">The hash table can also have an optional **GUID** key.</span></span> <span data-ttu-id="afedb-182">U kunt teken reeksen en hash-tabellen combi neren in de parameter waarde.</span><span class="sxs-lookup"><span data-stu-id="afedb-182">You can combine strings and hash tables in the parameter value.</span></span>

<span data-ttu-id="afedb-183">Deze sleutel is ontworpen om te fungeren als een module-inventarisatie.</span><span class="sxs-lookup"><span data-stu-id="afedb-183">This key is designed to act as a module inventory.</span></span> <span data-ttu-id="afedb-184">De modules die in de waarde van deze sleutel worden vermeld, worden niet automatisch verwerkt.</span><span class="sxs-lookup"><span data-stu-id="afedb-184">The modules that are listed in the value of this key aren't automatically processed.</span></span>

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

### <span data-ttu-id="afedb-185">-ModuleVersion</span><span class="sxs-lookup"><span data-stu-id="afedb-185">-ModuleVersion</span></span>

<span data-ttu-id="afedb-186">Hiermee geeft u de versie van de module.</span><span class="sxs-lookup"><span data-stu-id="afedb-186">Specifies the version of the module.</span></span>

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

### <span data-ttu-id="afedb-187">-NestedModules</span><span class="sxs-lookup"><span data-stu-id="afedb-187">-NestedModules</span></span>

<span data-ttu-id="afedb-188">Hiermee geeft u script modules ( `.psm1` ) en binaire modules ( `.dll` ) op die worden geïmporteerd in de sessie status van de module.</span><span class="sxs-lookup"><span data-stu-id="afedb-188">Specifies script modules (`.psm1`) and binary modules (`.dll`) that are imported into the module's session state.</span></span> <span data-ttu-id="afedb-189">De bestanden in de **NestedModules** -sleutel worden uitgevoerd in de volg orde waarin ze worden weer gegeven in de waarde.</span><span class="sxs-lookup"><span data-stu-id="afedb-189">The files in the **NestedModules** key run in the order in which they're listed in the value.</span></span>

<span data-ttu-id="afedb-190">Voer elke module naam in als een teken reeks of als een hash- **tabel met de** **ModuleVersion** -sleutels.</span><span class="sxs-lookup"><span data-stu-id="afedb-190">Enter each module name as a string or as a hash table with **ModuleName** and **ModuleVersion** keys.</span></span> <span data-ttu-id="afedb-191">De hash-tabel kan ook een optionele **GUID** -sleutel hebben.</span><span class="sxs-lookup"><span data-stu-id="afedb-191">The hash table can also have an optional **GUID** key.</span></span> <span data-ttu-id="afedb-192">U kunt teken reeksen en hash-tabellen combi neren in de parameter waarde.</span><span class="sxs-lookup"><span data-stu-id="afedb-192">You can combine strings and hash tables in the parameter value.</span></span>

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

### <span data-ttu-id="afedb-193">-PackageManagementProviders</span><span class="sxs-lookup"><span data-stu-id="afedb-193">-PackageManagementProviders</span></span>

<span data-ttu-id="afedb-194">Hiermee wordt een matrix met pakket beheer providers opgegeven.</span><span class="sxs-lookup"><span data-stu-id="afedb-194">Specifies an array of package management providers.</span></span>

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

### <span data-ttu-id="afedb-195">-PassThru</span><span class="sxs-lookup"><span data-stu-id="afedb-195">-PassThru</span></span>

<span data-ttu-id="afedb-196">Retourneert een object dat het item vertegenwoordigt waarmee u werkt.</span><span class="sxs-lookup"><span data-stu-id="afedb-196">Returns an object representing the item with which you're working.</span></span> <span data-ttu-id="afedb-197">Standaard genereert geen `Update-ModuleManifest` uitvoer.</span><span class="sxs-lookup"><span data-stu-id="afedb-197">By default, `Update-ModuleManifest` doesn't generate any output.</span></span>

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

### <span data-ttu-id="afedb-198">-Path</span><span class="sxs-lookup"><span data-stu-id="afedb-198">-Path</span></span>

<span data-ttu-id="afedb-199">Hiermee geeft u het pad en de bestands naam van het module manifest.</span><span class="sxs-lookup"><span data-stu-id="afedb-199">Specifies the path and file name of the module manifest.</span></span> <span data-ttu-id="afedb-200">Voer een pad en een bestands naam in met een `.psd1` bestands extensie, zoals `$PSHOME\Modules\MyModule\MyModule.psd1` .</span><span class="sxs-lookup"><span data-stu-id="afedb-200">Enter a path and file name with a `.psd1` file name extension, such as `$PSHOME\Modules\MyModule\MyModule.psd1`.</span></span>

<span data-ttu-id="afedb-201">Als u het pad naar een bestaand bestand opgeeft, wordt `Update-ModuleManifest` het bestand vervangen zonder waarschuwing tenzij het bestand het kenmerk alleen-lezen heeft.</span><span class="sxs-lookup"><span data-stu-id="afedb-201">If you specify the path to an existing file, `Update-ModuleManifest` replaces the file without warning unless the file has the read-only attribute.</span></span>

<span data-ttu-id="afedb-202">Het manifest moet zich in de map van de module bevinden en de naam van het manifest bestand moet hetzelfde zijn als de mapnaam, maar met een `.psd1` extensie.</span><span class="sxs-lookup"><span data-stu-id="afedb-202">The manifest should be located in the module's directory, and the manifest file name should be the same as the module directory name, but with a `.psd1` extension.</span></span>

<span data-ttu-id="afedb-203">U kunt geen variabelen, zoals `$PSHOME` of, gebruiken als `$HOME` antwoord op een prompt voor een **pad** parameter waarde.</span><span class="sxs-lookup"><span data-stu-id="afedb-203">You can't use variables, such as `$PSHOME` or `$HOME`, in response to a prompt for a **Path** parameter value.</span></span> <span data-ttu-id="afedb-204">Als u een variabele wilt gebruiken, neemt u de para meter **Path** op in de opdracht.</span><span class="sxs-lookup"><span data-stu-id="afedb-204">To use a variable, include the **Path** parameter in the command.</span></span>

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

### <span data-ttu-id="afedb-205">-PowerShellHostName</span><span class="sxs-lookup"><span data-stu-id="afedb-205">-PowerShellHostName</span></span>

<span data-ttu-id="afedb-206">Hiermee geeft u de naam op van het Power shell-hostprogramma dat is vereist voor de module.</span><span class="sxs-lookup"><span data-stu-id="afedb-206">Specifies the name of the PowerShell host program that the module requires.</span></span> <span data-ttu-id="afedb-207">Voer de naam van het hostprogramma in, zoals Power shell ISE host of ConsoleHost.</span><span class="sxs-lookup"><span data-stu-id="afedb-207">Enter the name of the host program, such as PowerShell ISE Host or ConsoleHost.</span></span> <span data-ttu-id="afedb-208">Joker tekens zijn niet toegestaan.</span><span class="sxs-lookup"><span data-stu-id="afedb-208">Wildcards aren't permitted.</span></span>

<span data-ttu-id="afedb-209">Als u de naam van een hostprogramma wilt zoeken, typt u in het programma `$Host.Name` .</span><span class="sxs-lookup"><span data-stu-id="afedb-209">To find the name of a host program, in the program, type `$Host.Name`.</span></span>

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

### <span data-ttu-id="afedb-210">-PowerShellHostVersion</span><span class="sxs-lookup"><span data-stu-id="afedb-210">-PowerShellHostVersion</span></span>

<span data-ttu-id="afedb-211">Hiermee geeft u de minimale versie van het Power shell-hostprogramma op dat met de module werkt.</span><span class="sxs-lookup"><span data-stu-id="afedb-211">Specifies the minimum version of the PowerShell host program that works with the module.</span></span> <span data-ttu-id="afedb-212">Voer een versie nummer in, bijvoorbeeld 1,1.</span><span class="sxs-lookup"><span data-stu-id="afedb-212">Enter a version number, such as 1.1.</span></span>

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

### <span data-ttu-id="afedb-213">-PowerShellVersion</span><span class="sxs-lookup"><span data-stu-id="afedb-213">-PowerShellVersion</span></span>

<span data-ttu-id="afedb-214">Hiermee geeft u de minimale versie van Power shell op die met deze module kan worden gebruikt.</span><span class="sxs-lookup"><span data-stu-id="afedb-214">Specifies the minimum version of PowerShell that will work with this module.</span></span> <span data-ttu-id="afedb-215">U kunt bijvoorbeeld 3,0, 4,0 of 5,0 opgeven als de waarde van deze para meter.</span><span class="sxs-lookup"><span data-stu-id="afedb-215">For example, you can specify 3.0, 4.0, or 5.0 as the value of this parameter.</span></span>

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

### <span data-ttu-id="afedb-216">-Prerelease</span><span class="sxs-lookup"><span data-stu-id="afedb-216">-Prerelease</span></span>

<span data-ttu-id="afedb-217">Hiermee wordt aangegeven dat de module Prerelease is.</span><span class="sxs-lookup"><span data-stu-id="afedb-217">Indicates the module is prerelease.</span></span>

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

### <span data-ttu-id="afedb-218">-PrivateData</span><span class="sxs-lookup"><span data-stu-id="afedb-218">-PrivateData</span></span>

<span data-ttu-id="afedb-219">Hiermee geeft u de gegevens op die worden door gegeven aan de module wanneer deze wordt geïmporteerd.</span><span class="sxs-lookup"><span data-stu-id="afedb-219">Specifies data that is passed to the module when it's imported.</span></span>

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

### <span data-ttu-id="afedb-220">-ProcessorArchitecture</span><span class="sxs-lookup"><span data-stu-id="afedb-220">-ProcessorArchitecture</span></span>

<span data-ttu-id="afedb-221">Hiermee geeft u de processor architectuur op die de module vereist.</span><span class="sxs-lookup"><span data-stu-id="afedb-221">Specifies the processor architecture that the module requires.</span></span>

<span data-ttu-id="afedb-222">De aanvaardbare waarden voor deze parameter zijn:</span><span class="sxs-lookup"><span data-stu-id="afedb-222">The acceptable values for this parameter are:</span></span>

- <span data-ttu-id="afedb-223">Amd64</span><span class="sxs-lookup"><span data-stu-id="afedb-223">Amd64</span></span>
- <span data-ttu-id="afedb-224">Scherp</span><span class="sxs-lookup"><span data-stu-id="afedb-224">Arm</span></span>
- <span data-ttu-id="afedb-225">64</span><span class="sxs-lookup"><span data-stu-id="afedb-225">IA64</span></span>
- <span data-ttu-id="afedb-226">MSIL</span><span class="sxs-lookup"><span data-stu-id="afedb-226">MSIL</span></span>
- <span data-ttu-id="afedb-227">Geen (onbekend of niet opgegeven)</span><span class="sxs-lookup"><span data-stu-id="afedb-227">None (unknown or unspecified)</span></span>
- <span data-ttu-id="afedb-228">X86</span><span class="sxs-lookup"><span data-stu-id="afedb-228">X86</span></span>

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

### <span data-ttu-id="afedb-229">-ProjectUri</span><span class="sxs-lookup"><span data-stu-id="afedb-229">-ProjectUri</span></span>

<span data-ttu-id="afedb-230">Hiermee geeft u de URL van een webpagina over dit project op.</span><span class="sxs-lookup"><span data-stu-id="afedb-230">Specifies the URL of a web page about this project.</span></span>

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

### <span data-ttu-id="afedb-231">-ReleaseNotes</span><span class="sxs-lookup"><span data-stu-id="afedb-231">-ReleaseNotes</span></span>

<span data-ttu-id="afedb-232">Hiermee geeft u een teken reeks matrix met release opmerkingen of opmerkingen die u beschikbaar wilt stellen voor deze versie van het script.</span><span class="sxs-lookup"><span data-stu-id="afedb-232">Specifies a string array that contains release notes or comments that you want available for this version of the script.</span></span>

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

### <span data-ttu-id="afedb-233">-RequiredAssemblies</span><span class="sxs-lookup"><span data-stu-id="afedb-233">-RequiredAssemblies</span></span>

<span data-ttu-id="afedb-234">Hiermee geeft u de assembly ( `.dll` )-bestanden op die de module vereist.</span><span class="sxs-lookup"><span data-stu-id="afedb-234">Specifies the assembly (`.dll`) files that the module requires.</span></span> <span data-ttu-id="afedb-235">Voer de namen van de assembly bestanden in.</span><span class="sxs-lookup"><span data-stu-id="afedb-235">Enter the assembly file names.</span></span>
<span data-ttu-id="afedb-236">Power shell laadt de opgegeven assembly's vóór het bijwerken van typen of indelingen, het importeren van geneste modules of het importeren van het module bestand dat is opgegeven in de waarde van de sleutel **RootModule** .</span><span class="sxs-lookup"><span data-stu-id="afedb-236">PowerShell loads the specified assemblies before updating types or formats, importing nested modules, or importing the module file that is specified in the value of the **RootModule** key.</span></span>

<span data-ttu-id="afedb-237">Gebruik deze para meter om alle assembly's op te geven die de module vereist, inclusief de assembly's die moeten worden geladen voor het bijwerken van de opmaak of het type van bestanden die worden vermeld in de sleutels **FormatsToProcess** of **TypesToProcess** , zelfs als deze assembly's ook worden vermeld als binaire modules in de **NestedModules** -sleutel.</span><span class="sxs-lookup"><span data-stu-id="afedb-237">Use this parameter to specify all the assemblies that the module requires, including assemblies that must be loaded to update any formatting or type files that are listed in the **FormatsToProcess** or **TypesToProcess** keys, even if those assemblies are also listed as binary modules in the **NestedModules** key.</span></span>

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

### <span data-ttu-id="afedb-238">-RequiredModules</span><span class="sxs-lookup"><span data-stu-id="afedb-238">-RequiredModules</span></span>

<span data-ttu-id="afedb-239">Hiermee worden modules opgegeven die de algemene sessie status moeten hebben.</span><span class="sxs-lookup"><span data-stu-id="afedb-239">Specifies modules that must be in the global session state.</span></span> <span data-ttu-id="afedb-240">Als de vereiste modules zich niet in de globale sessie status bevinden, worden ze door Power shell geïmporteerd.</span><span class="sxs-lookup"><span data-stu-id="afedb-240">If the required modules aren't in the global session state, PowerShell imports them.</span></span> <span data-ttu-id="afedb-241">Als de vereiste modules niet beschikbaar zijn, `Import-Module` mislukt de opdracht.</span><span class="sxs-lookup"><span data-stu-id="afedb-241">If the required modules aren't available, the `Import-Module` command fails.</span></span>

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

### <span data-ttu-id="afedb-242">-RequireLicenseAcceptance</span><span class="sxs-lookup"><span data-stu-id="afedb-242">-RequireLicenseAcceptance</span></span>

<span data-ttu-id="afedb-243">Hiermee geeft u op dat een acceptatie van de licentie is vereist voor de module.</span><span class="sxs-lookup"><span data-stu-id="afedb-243">Specifies that a license acceptance is required for the module.</span></span>

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

### <span data-ttu-id="afedb-244">-RootModule</span><span class="sxs-lookup"><span data-stu-id="afedb-244">-RootModule</span></span>

<span data-ttu-id="afedb-245">Hiermee geeft u het primaire of hoofd bestand van de module op.</span><span class="sxs-lookup"><span data-stu-id="afedb-245">Specifies the primary or root file of the module.</span></span> <span data-ttu-id="afedb-246">Voer de bestands naam van een script ( `.ps1` ), een script module ( `.psm1` ), een module manifest ( `.psd1` ), een assembly ( `.dll` ), een XML-bestand voor de cmdlet-definitie ( `.cdxml` ) of een werk stroom ( `.xaml` ) in.</span><span class="sxs-lookup"><span data-stu-id="afedb-246">Enter the file name of a script (`.ps1`), a script module (`.psm1`), a module manifest (`.psd1`), an assembly (`.dll`), a cmdlet definition XML file (`.cdxml`), or a workflow (`.xaml`).</span></span> <span data-ttu-id="afedb-247">Wanneer de module wordt geïmporteerd, worden de leden die worden geëxporteerd uit het hoofd module bestand geïmporteerd in de sessie status van de aanroeper.</span><span class="sxs-lookup"><span data-stu-id="afedb-247">When the module is imported, the members that are exported from the root module file are imported into the caller's session state.</span></span>

<span data-ttu-id="afedb-248">Als een module een manifest bestand heeft en er geen hoofd bestand is opgegeven in de **RootModule** -sleutel, wordt het manifest het primaire bestand voor de module.</span><span class="sxs-lookup"><span data-stu-id="afedb-248">If a module has a manifest file and no root file has been specified in the **RootModule** key, the manifest becomes the primary file for the module.</span></span> <span data-ttu-id="afedb-249">En wordt de module een manifest module (module type = manifest).</span><span class="sxs-lookup"><span data-stu-id="afedb-249">And, the module becomes a manifest module (ModuleType = Manifest).</span></span>

<span data-ttu-id="afedb-250">Als u leden wilt exporteren uit `.psm1` of `.dll` bestanden in een module met een manifest, moeten de namen van die bestanden worden opgegeven in de waarden van de sleutels **RootModule** of **NestedModules** in het manifest.</span><span class="sxs-lookup"><span data-stu-id="afedb-250">To export members from `.psm1` or `.dll` files in a module that has a manifest, the names of those files must be specified in the values of the **RootModule** or **NestedModules** keys in the manifest.</span></span> <span data-ttu-id="afedb-251">Anders worden de leden niet geëxporteerd.</span><span class="sxs-lookup"><span data-stu-id="afedb-251">Otherwise, their members aren't exported.</span></span>

<span data-ttu-id="afedb-252">In Power Shell 2,0 is deze sleutel **ModuleToProcess** genoemd.</span><span class="sxs-lookup"><span data-stu-id="afedb-252">In PowerShell 2.0, this key was called **ModuleToProcess**.</span></span>

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

### <span data-ttu-id="afedb-253">-ScriptsToProcess</span><span class="sxs-lookup"><span data-stu-id="afedb-253">-ScriptsToProcess</span></span>

<span data-ttu-id="afedb-254">Hiermee geeft u script ( `.ps1` )-bestanden op die worden uitgevoerd in de sessie status van de aanroeper wanneer de module wordt geïmporteerd.</span><span class="sxs-lookup"><span data-stu-id="afedb-254">Specifies script (`.ps1`) files that run in the caller's session state when the module is imported.</span></span>
<span data-ttu-id="afedb-255">U kunt deze scripts gebruiken om een omgeving voor te bereiden, net zoals u een aanmeldings script zou kunnen gebruiken.</span><span class="sxs-lookup"><span data-stu-id="afedb-255">You can use these scripts to prepare an environment, just as you might use a login script.</span></span>

<span data-ttu-id="afedb-256">Als u scripts wilt opgeven die worden uitgevoerd in de sessie status van de module, gebruikt u de sleutel **NestedModules** .</span><span class="sxs-lookup"><span data-stu-id="afedb-256">To specify scripts that run in the module's session state, use the **NestedModules** key.</span></span>

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

### <span data-ttu-id="afedb-257">-Tags</span><span class="sxs-lookup"><span data-stu-id="afedb-257">-Tags</span></span>

<span data-ttu-id="afedb-258">Hiermee geeft u een matrix met tags op.</span><span class="sxs-lookup"><span data-stu-id="afedb-258">Specifies an array of tags.</span></span>

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

### <span data-ttu-id="afedb-259">-TypesToProcess</span><span class="sxs-lookup"><span data-stu-id="afedb-259">-TypesToProcess</span></span>

<span data-ttu-id="afedb-260">Hiermee geeft u het type bestanden ( `.ps1xml` ) op dat wordt uitgevoerd wanneer de module wordt geïmporteerd.</span><span class="sxs-lookup"><span data-stu-id="afedb-260">Specifies the type files (`.ps1xml`) that run when the module is imported.</span></span>

<span data-ttu-id="afedb-261">Wanneer u de module importeert, voert Power shell de `Update-TypeData` cmdlet uit met de opgegeven bestanden.</span><span class="sxs-lookup"><span data-stu-id="afedb-261">When you import the module, PowerShell runs the `Update-TypeData` cmdlet with the specified files.</span></span>
<span data-ttu-id="afedb-262">Omdat type bestanden geen bereik hebben, hebben ze invloed op alle sessie statussen in de sessie.</span><span class="sxs-lookup"><span data-stu-id="afedb-262">Because type files aren't scoped, they affect all session states in the session.</span></span>

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

### <span data-ttu-id="afedb-263">-VariablesToExport</span><span class="sxs-lookup"><span data-stu-id="afedb-263">-VariablesToExport</span></span>

<span data-ttu-id="afedb-264">Hiermee geeft u de variabelen op die de module exporteert.</span><span class="sxs-lookup"><span data-stu-id="afedb-264">Specifies the variables that the module exports.</span></span> <span data-ttu-id="afedb-265">Joker tekens zijn toegestaan.</span><span class="sxs-lookup"><span data-stu-id="afedb-265">Wildcards are permitted.</span></span>

<span data-ttu-id="afedb-266">Gebruik deze para meter om de variabelen te beperken die door de module worden geëxporteerd.</span><span class="sxs-lookup"><span data-stu-id="afedb-266">Use this parameter to restrict the variables that are exported by the module.</span></span> <span data-ttu-id="afedb-267">**VariablesToExport** kan variabelen uit de lijst geëxporteerde variabelen verwijderen, maar kan geen variabelen toevoegen aan de lijst.</span><span class="sxs-lookup"><span data-stu-id="afedb-267">**VariablesToExport** can remove variables from the list of exported variables, but it can't add variables to the list.</span></span>

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

### <span data-ttu-id="afedb-268">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="afedb-268">-WhatIf</span></span>

<span data-ttu-id="afedb-269">Hier wordt weer gegeven wat er gebeurt als er `Update-ModuleManifest` wordt uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="afedb-269">Shows what would happen if `Update-ModuleManifest` runs.</span></span> <span data-ttu-id="afedb-270">De cmdlet wordt niet uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="afedb-270">The cmdlet isn't run.</span></span>

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

### <span data-ttu-id="afedb-271">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="afedb-271">CommonParameters</span></span>

<span data-ttu-id="afedb-272">Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="afedb-272">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="afedb-273">Zie [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="afedb-273">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="afedb-274">INVOER</span><span class="sxs-lookup"><span data-stu-id="afedb-274">INPUTS</span></span>

### <span data-ttu-id="afedb-275">System. String</span><span class="sxs-lookup"><span data-stu-id="afedb-275">System.String</span></span>

## <span data-ttu-id="afedb-276">UITVOER</span><span class="sxs-lookup"><span data-stu-id="afedb-276">OUTPUTS</span></span>

### <span data-ttu-id="afedb-277">System. object</span><span class="sxs-lookup"><span data-stu-id="afedb-277">System.Object</span></span>

## <span data-ttu-id="afedb-278">OPMERKINGEN</span><span class="sxs-lookup"><span data-stu-id="afedb-278">NOTES</span></span>

## <span data-ttu-id="afedb-279">GERELATEERDE KOPPELINGEN</span><span class="sxs-lookup"><span data-stu-id="afedb-279">RELATED LINKS</span></span>