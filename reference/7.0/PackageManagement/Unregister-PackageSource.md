---
external help file: Microsoft.PowerShell.PackageManagement.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: PackageManagement
ms.date: 05/24/2019
online version: https://docs.microsoft.com/powershell/module/packagemanagement/unregister-packagesource?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Unregister-PackageSource
ms.openlocfilehash: 06a4649d0d2f0912807219f25e60d85ba22564b0
ms.sourcegitcommit: de63e9481cf8024883060aae61fb02c59c2de662
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/03/2020
ms.locfileid: "93249496"
---
# <span data-ttu-id="ba1aa-103">Unregister-PackageSource</span><span class="sxs-lookup"><span data-stu-id="ba1aa-103">Unregister-PackageSource</span></span>

## <span data-ttu-id="ba1aa-104">SAMENVATTING</span><span class="sxs-lookup"><span data-stu-id="ba1aa-104">SYNOPSIS</span></span>
<span data-ttu-id="ba1aa-105">Hiermee verwijdert u een geregistreerde pakket bron.</span><span class="sxs-lookup"><span data-stu-id="ba1aa-105">Removes a registered package source.</span></span>

## <span data-ttu-id="ba1aa-106">SYNTAXIS</span><span class="sxs-lookup"><span data-stu-id="ba1aa-106">SYNTAX</span></span>

### <span data-ttu-id="ba1aa-107">SourceBySearch</span><span class="sxs-lookup"><span data-stu-id="ba1aa-107">SourceBySearch</span></span>

```
Unregister-PackageSource [[-Source] <String>] [-Location <String>] [-Credential <PSCredential>]
 [-Force] [-ForceBootstrap] [-WhatIf] [-Confirm] [-ProviderName <String>] [<CommonParameters>]
```

### <span data-ttu-id="ba1aa-108">SourceByInputObject</span><span class="sxs-lookup"><span data-stu-id="ba1aa-108">SourceByInputObject</span></span>

```
Unregister-PackageSource -InputObject <PackageSource[]> [-Credential <PSCredential>] [-Force]
 [-ForceBootstrap] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="ba1aa-109">NuGet: SourceByInputObject</span><span class="sxs-lookup"><span data-stu-id="ba1aa-109">NuGet:SourceByInputObject</span></span>

```
Unregister-PackageSource [-Credential <PSCredential>] [-Force] [-ForceBootstrap] [-WhatIf]
 [-Confirm] [-ConfigFile <String>] [-SkipValidate] [<CommonParameters>]
```

### <span data-ttu-id="ba1aa-110">NuGet: SourceBySearch</span><span class="sxs-lookup"><span data-stu-id="ba1aa-110">NuGet:SourceBySearch</span></span>

```
Unregister-PackageSource [-Credential <PSCredential>] [-Force] [-ForceBootstrap] [-WhatIf]
 [-Confirm] [-ConfigFile <String>] [-SkipValidate] [<CommonParameters>]
```

### <span data-ttu-id="ba1aa-111">PowerShellGet: SourceByInputObject</span><span class="sxs-lookup"><span data-stu-id="ba1aa-111">PowerShellGet:SourceByInputObject</span></span>

```
Unregister-PackageSource [-Credential <PSCredential>] [-Force] [-ForceBootstrap] [-WhatIf]
 [-Confirm] [-PackageManagementProvider <String>] [-PublishLocation <String>]
 [-ScriptSourceLocation <String>] [-ScriptPublishLocation <String>] [<CommonParameters>]
```

### <span data-ttu-id="ba1aa-112">PowerShellGet: SourceBySearch</span><span class="sxs-lookup"><span data-stu-id="ba1aa-112">PowerShellGet:SourceBySearch</span></span>

```
Unregister-PackageSource [-Credential <PSCredential>] [-Force] [-ForceBootstrap] [-WhatIf]
 [-Confirm] [-PackageManagementProvider <String>] [-PublishLocation <String>]
 [-ScriptSourceLocation <String>] [-ScriptPublishLocation <String>] [<CommonParameters>]
```

## <span data-ttu-id="ba1aa-113">BESCHRIJVING</span><span class="sxs-lookup"><span data-stu-id="ba1aa-113">DESCRIPTION</span></span>

<span data-ttu-id="ba1aa-114">Met de `Unregister-PackageSource` cmdlet wordt een geregistreerde pakket bron verwijderd.</span><span class="sxs-lookup"><span data-stu-id="ba1aa-114">The `Unregister-PackageSource` cmdlet removes a registered package source.</span></span> <span data-ttu-id="ba1aa-115">Pakket bronnen worden altijd beheerd door een pakket provider.</span><span class="sxs-lookup"><span data-stu-id="ba1aa-115">Package sources are always managed by a package provider.</span></span> <span data-ttu-id="ba1aa-116">Als u pakket bronnen wilt zoeken, gebruikt u de `Get-PackageSource` cmdlet.</span><span class="sxs-lookup"><span data-stu-id="ba1aa-116">To find package sources, use the `Get-PackageSource` cmdlet.</span></span>

## <span data-ttu-id="ba1aa-117">VOORBEELDEN</span><span class="sxs-lookup"><span data-stu-id="ba1aa-117">EXAMPLES</span></span>

### <span data-ttu-id="ba1aa-118">Voor beeld 1: de registratie van een pakket bron voor de Nuget-provider opheffen</span><span class="sxs-lookup"><span data-stu-id="ba1aa-118">Example 1: Unregister a package source for the Nuget provider</span></span>

<span data-ttu-id="ba1aa-119">Met de cmdlet wordt de `Unregister-PackageSource` registratie van een pakket bron van de lokale computer ongedaan gemaakt.</span><span class="sxs-lookup"><span data-stu-id="ba1aa-119">The `Unregister-PackageSource` cmdlet unregisters a package source from the local computer.</span></span> <span data-ttu-id="ba1aa-120">De para meters **locatie** en **provider** kunnen worden gebruikt om de bron die moet worden verwijderd, nader op te geven.</span><span class="sxs-lookup"><span data-stu-id="ba1aa-120">The **Location** and **Provider** parameters can be used to further specify the source to remove.</span></span>

```
PS> Unregister-PackageSource -Source MyNuGet
```

<span data-ttu-id="ba1aa-121">De `Unregister-PackageSource` cmdlet gebruikt de para meter **Source** om op te geven welke bron moet worden verwijderd.</span><span class="sxs-lookup"><span data-stu-id="ba1aa-121">The `Unregister-PackageSource` cmdlet uses the **Source** parameter to specify which source to remove.</span></span>

### <span data-ttu-id="ba1aa-122">Voor beeld 2: een PackageSource-object gebruiken om de registratie van een pakket op te heffen</span><span class="sxs-lookup"><span data-stu-id="ba1aa-122">Example 2: Use a PackageSource object to unregister a package</span></span>

<span data-ttu-id="ba1aa-123">In dit voor beeld wordt de `Get-PackageSource` en gebruikt `Unregister-PackageSource` om de registratie van een pakket bron ongedaan te maken.</span><span class="sxs-lookup"><span data-stu-id="ba1aa-123">This example uses the `Get-PackageSource` and `Unregister-PackageSource` to unregister a package source.</span></span> <span data-ttu-id="ba1aa-124">Het **PackageSource** -object wordt opgeslagen in een variabele.</span><span class="sxs-lookup"><span data-stu-id="ba1aa-124">The **PackageSource** object is stored in a variable.</span></span>

```
PS> $pkgsource = Get-PackageSource -Name MyNuGet
PS> Unregister-PackageSource -InputObject $pkgsource
```

<span data-ttu-id="ba1aa-125">De `$pkgsource` variabele bevat de **PackageSource** die door de `Get-PackageSource` cmdlet is gemaakt.</span><span class="sxs-lookup"><span data-stu-id="ba1aa-125">The `$pkgsource` variable stores the **PackageSource** created by the `Get-PackageSource` cmdlet.</span></span>
<span data-ttu-id="ba1aa-126">`Unregister-PackageSource` gebruikt de `$pkgsource` als-invoer voor de para meter **input object** .</span><span class="sxs-lookup"><span data-stu-id="ba1aa-126">`Unregister-PackageSource` uses the `$pkgsource` as input to the **InputObject** parameter.</span></span>

<span data-ttu-id="ba1aa-127">Als alternatief `Unregister-PackageSource` kan de cmdlet een waarde opgeven voor de para meter **input object** :</span><span class="sxs-lookup"><span data-stu-id="ba1aa-127">As an alternative, the `Unregister-PackageSource` cmdlet can specify a value for the **InputObject** parameter:</span></span>

`Unregister-PackageSource -InputObject ( Get-PackageSource -Name MyNuGet )`

## <span data-ttu-id="ba1aa-128">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="ba1aa-128">PARAMETERS</span></span>

### <span data-ttu-id="ba1aa-129">-ConfigFile</span><span class="sxs-lookup"><span data-stu-id="ba1aa-129">-ConfigFile</span></span>

<span data-ttu-id="ba1aa-130">Hiermee geeft u een configuratie bestand op.</span><span class="sxs-lookup"><span data-stu-id="ba1aa-130">Specifies a configuration file.</span></span>

```yaml
Type: System.String
Parameter Sets: NuGet:SourceByInputObject, NuGet:SourceBySearch
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="ba1aa-131">-Credential</span><span class="sxs-lookup"><span data-stu-id="ba1aa-131">-Credential</span></span>

<span data-ttu-id="ba1aa-132">Hiermee geeft u een gebruikers account op dat is gemachtigd om toegang te krijgen tot de computer en om opdrachten uit te voeren.</span><span class="sxs-lookup"><span data-stu-id="ba1aa-132">Specifies a user account that has permission to access the computer and run commands.</span></span> <span data-ttu-id="ba1aa-133">Typ een gebruikers naam, zoals **gebruiker01** , **Domain01\User01** , of voer een **PSCredential** -object in dat door de `Get-Credential` cmdlet wordt gegenereerd.</span><span class="sxs-lookup"><span data-stu-id="ba1aa-133">Type a user name, such as **User01** , **Domain01\User01** , or enter a **PSCredential** object, generated by the `Get-Credential` cmdlet.</span></span> <span data-ttu-id="ba1aa-134">Als u een gebruikers naam typt, wordt u gevraagd een wacht woord op te vragen.</span><span class="sxs-lookup"><span data-stu-id="ba1aa-134">If you type a user name, you're prompted for a password.</span></span>

<span data-ttu-id="ba1aa-135">Als de para meter **Credential** niet is opgegeven, wordt het huidige gebruikers account gebruikt.</span><span class="sxs-lookup"><span data-stu-id="ba1aa-135">When the **Credential** parameter isn't specified, the current user account is used.</span></span>

```yaml
Type: System.Management.Automation.PSCredential
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="ba1aa-136">-Force</span><span class="sxs-lookup"><span data-stu-id="ba1aa-136">-Force</span></span>

<span data-ttu-id="ba1aa-137">Hiermee wordt de opdracht uitgevoerd zonder dat de gebruiker om bevestiging wordt gevraagd.</span><span class="sxs-lookup"><span data-stu-id="ba1aa-137">Forces the command to run without asking for user confirmation.</span></span> <span data-ttu-id="ba1aa-138">Onderdrukkingen van beperkingen die voor komen dat `Unregister-PackageSource` de slagen worden voltooid, met uitzonde ring van beveiliging.</span><span class="sxs-lookup"><span data-stu-id="ba1aa-138">Overrides restrictions that prevent `Unregister-PackageSource` from succeeding, with the exception of security.</span></span>

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

### <span data-ttu-id="ba1aa-139">-ForceBootstrap</span><span class="sxs-lookup"><span data-stu-id="ba1aa-139">-ForceBootstrap</span></span>

<span data-ttu-id="ba1aa-140">Geeft aan `Unregister-PackageSource` dat **Package Management** automatisch de pakket provider voor de opgegeven pakket bron verwijdert.</span><span class="sxs-lookup"><span data-stu-id="ba1aa-140">Indicates that `Unregister-PackageSource` forces **PackageManagement** to automatically uninstall the package provider for the specified package source.</span></span>

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

### <span data-ttu-id="ba1aa-141">-Input object</span><span class="sxs-lookup"><span data-stu-id="ba1aa-141">-InputObject</span></span>

<span data-ttu-id="ba1aa-142">Hiermee wordt een pijplijn invoer geaccepteerd die het **PackageSource** -object van de cmdlet specificeert `Get-PackageSource` .</span><span class="sxs-lookup"><span data-stu-id="ba1aa-142">Accepts pipeline input that specifies the **PackageSource** object from the `Get-PackageSource` cmdlet.</span></span> <span data-ttu-id="ba1aa-143">**Input object** accepteert het **PackageSource** -object als een `Get-PackageSource` waarde of een variabele die het object bevat.</span><span class="sxs-lookup"><span data-stu-id="ba1aa-143">**InputObject** accepts the **PackageSource** object as a `Get-PackageSource` value or a variable that contains the object.</span></span>

```yaml
Type: Microsoft.PackageManagement.Packaging.PackageSource[]
Parameter Sets: SourceByInputObject
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="ba1aa-144">-Locatie</span><span class="sxs-lookup"><span data-stu-id="ba1aa-144">-Location</span></span>

<span data-ttu-id="ba1aa-145">Hiermee geeft u de locatie op van de pakket bron punten.</span><span class="sxs-lookup"><span data-stu-id="ba1aa-145">Specifies the location to which a package source points.</span></span> <span data-ttu-id="ba1aa-146">De waarde van deze para meter kan een URI, een bestandspad of een andere bestemmings indeling zijn die wordt ondersteund door de pakket provider.</span><span class="sxs-lookup"><span data-stu-id="ba1aa-146">The value of this parameter can be a URI, a file path, or any other destination format that is supported by the package provider.</span></span>

```yaml
Type: System.String
Parameter Sets: SourceBySearch
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="ba1aa-147">-PackageManagementProvider</span><span class="sxs-lookup"><span data-stu-id="ba1aa-147">-PackageManagementProvider</span></span>

<span data-ttu-id="ba1aa-148">Hiermee geeft u de **Package Management** -provider.</span><span class="sxs-lookup"><span data-stu-id="ba1aa-148">Specifies the **PackageManagement** provider.</span></span>

```yaml
Type: System.String
Parameter Sets: PowerShellGet:SourceByInputObject, PowerShellGet:SourceBySearch
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="ba1aa-149">-ProviderName</span><span class="sxs-lookup"><span data-stu-id="ba1aa-149">-ProviderName</span></span>

<span data-ttu-id="ba1aa-150">Hiermee geeft u de naam van de provider.</span><span class="sxs-lookup"><span data-stu-id="ba1aa-150">Specifies the provider name.</span></span>

```yaml
Type: System.String
Parameter Sets: SourceBySearch
Aliases: Provider
Accepted values: Bootstrap, NuGet, PowerShellGet

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="ba1aa-151">-PublishLocation</span><span class="sxs-lookup"><span data-stu-id="ba1aa-151">-PublishLocation</span></span>

<span data-ttu-id="ba1aa-152">Hiermee geeft u de publicatie locatie op.</span><span class="sxs-lookup"><span data-stu-id="ba1aa-152">Specifies the publish location.</span></span>

```yaml
Type: System.String
Parameter Sets: PowerShellGet:SourceByInputObject, PowerShellGet:SourceBySearch
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="ba1aa-153">-ScriptPublishLocation</span><span class="sxs-lookup"><span data-stu-id="ba1aa-153">-ScriptPublishLocation</span></span>

<span data-ttu-id="ba1aa-154">Hiermee geeft u de publicatie locatie van het script op.</span><span class="sxs-lookup"><span data-stu-id="ba1aa-154">Specifies the script publish location.</span></span>

```yaml
Type: System.String
Parameter Sets: PowerShellGet:SourceByInputObject, PowerShellGet:SourceBySearch
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="ba1aa-155">-ScriptSourceLocation</span><span class="sxs-lookup"><span data-stu-id="ba1aa-155">-ScriptSourceLocation</span></span>

<span data-ttu-id="ba1aa-156">Hiermee geeft u de bron locatie van het script op.</span><span class="sxs-lookup"><span data-stu-id="ba1aa-156">Specifies the script source location.</span></span>

```yaml
Type: System.String
Parameter Sets: PowerShellGet:SourceByInputObject, PowerShellGet:SourceBySearch
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="ba1aa-157">-SkipValidate</span><span class="sxs-lookup"><span data-stu-id="ba1aa-157">-SkipValidate</span></span>

<span data-ttu-id="ba1aa-158">Switch waarmee de validatie van de referenties van een pakket bron wordt overgeslagen.</span><span class="sxs-lookup"><span data-stu-id="ba1aa-158">Switch that skips validating the credentials of a package source.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: NuGet:SourceByInputObject, NuGet:SourceBySearch
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="ba1aa-159">-Source</span><span class="sxs-lookup"><span data-stu-id="ba1aa-159">-Source</span></span>

<span data-ttu-id="ba1aa-160">Hiermee geeft u de beschrijvende naam van de pakket bron op.</span><span class="sxs-lookup"><span data-stu-id="ba1aa-160">Specifies the friendly name of the package source.</span></span>

```yaml
Type: System.String
Parameter Sets: SourceBySearch
Aliases: Name

Required: False
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="ba1aa-161">-Confirm</span><span class="sxs-lookup"><span data-stu-id="ba1aa-161">-Confirm</span></span>

<span data-ttu-id="ba1aa-162">Vraagt u om bevestiging voordat deze `Unregister-PackageSource` wordt uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="ba1aa-162">Prompts you for confirmation before `Unregister-PackageSource` is run.</span></span>

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

### <span data-ttu-id="ba1aa-163">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="ba1aa-163">-WhatIf</span></span>

<span data-ttu-id="ba1aa-164">Laat zien wat er zou gebeuren als de `Unregister-PackageSource` cmdlet wordt uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="ba1aa-164">Shows what would happen if `Unregister-PackageSource` cmdlet is run.</span></span> <span data-ttu-id="ba1aa-165">De cmdlet wordt niet uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="ba1aa-165">The cmdlet isn't run.</span></span>

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

### <span data-ttu-id="ba1aa-166">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="ba1aa-166">CommonParameters</span></span>

<span data-ttu-id="ba1aa-167">Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="ba1aa-167">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="ba1aa-168">Zie [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="ba1aa-168">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="ba1aa-169">INVOER</span><span class="sxs-lookup"><span data-stu-id="ba1aa-169">INPUTS</span></span>

### <span data-ttu-id="ba1aa-170">`Unregister-PackageSource` Hiermee worden **PackageSource** -objecten van de pijp lijn geaccepteerd als invoer.</span><span class="sxs-lookup"><span data-stu-id="ba1aa-170">`Unregister-PackageSource` accepts **PackageSource** objects from the pipeline as input.</span></span>

## <span data-ttu-id="ba1aa-171">UITVOER</span><span class="sxs-lookup"><span data-stu-id="ba1aa-171">OUTPUTS</span></span>

### <span data-ttu-id="ba1aa-172">`Unregister-PackageSource` Er wordt geen uitvoer gegenereerd.</span><span class="sxs-lookup"><span data-stu-id="ba1aa-172">`Unregister-PackageSource` doesn't generate any output.</span></span>

## <span data-ttu-id="ba1aa-173">OPMERKINGEN</span><span class="sxs-lookup"><span data-stu-id="ba1aa-173">NOTES</span></span>

<span data-ttu-id="ba1aa-174">Het opnemen van een pakket provider in een opdracht kan dynamische para meters beschikbaar maken voor een cmdlet.</span><span class="sxs-lookup"><span data-stu-id="ba1aa-174">Including a package provider in a command can make dynamic parameters available to a cmdlet.</span></span> <span data-ttu-id="ba1aa-175">Dynamische para meters zijn specifiek voor een pakket provider.</span><span class="sxs-lookup"><span data-stu-id="ba1aa-175">Dynamic parameters are specific to a package provider.</span></span> <span data-ttu-id="ba1aa-176">De `Get-Help` cmdlet geeft een lijst van de parameter sets van de cmdlet en bevat de parameterset van de provider.</span><span class="sxs-lookup"><span data-stu-id="ba1aa-176">The `Get-Help` cmdlet lists a cmdlet's parameter sets and includes the provider's parameter set.</span></span>

## <span data-ttu-id="ba1aa-177">GERELATEERDE KOPPELINGEN</span><span class="sxs-lookup"><span data-stu-id="ba1aa-177">RELATED LINKS</span></span>

[<span data-ttu-id="ba1aa-178">about_PackageManagement</span><span class="sxs-lookup"><span data-stu-id="ba1aa-178">about_PackageManagement</span></span>](../Microsoft.PowerShell.Core/About/about_PackageManagement.md)

[<span data-ttu-id="ba1aa-179">Get-Credential</span><span class="sxs-lookup"><span data-stu-id="ba1aa-179">Get-Credential</span></span>](../Microsoft.PowerShell.Security/Get-Credential.md)

[<span data-ttu-id="ba1aa-180">Get-PackageSource</span><span class="sxs-lookup"><span data-stu-id="ba1aa-180">Get-PackageSource</span></span>](Get-PackageSource.md)

[<span data-ttu-id="ba1aa-181">REGI ster-PackageSource</span><span class="sxs-lookup"><span data-stu-id="ba1aa-181">Register-PackageSource</span></span>](Register-PackageSource.md)

[<span data-ttu-id="ba1aa-182">Set-PackageSource</span><span class="sxs-lookup"><span data-stu-id="ba1aa-182">Set-PackageSource</span></span>](Set-PackageSource.md)
