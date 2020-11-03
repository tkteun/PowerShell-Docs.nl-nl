---
external help file: Microsoft.PowerShell.PackageManagement.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: PackageManagement
ms.date: 05/24/2019
online version: https://docs.microsoft.com/powershell/module/packagemanagement/unregister-packagesource?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Unregister-PackageSource
ms.openlocfilehash: 7f923c3d1b35f956479abd17e14861835dc80497
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/07/2020
ms.locfileid: "93250882"
---
# <span data-ttu-id="c4160-103">Unregister-PackageSource</span><span class="sxs-lookup"><span data-stu-id="c4160-103">Unregister-PackageSource</span></span>

## <span data-ttu-id="c4160-104">SAMENVATTING</span><span class="sxs-lookup"><span data-stu-id="c4160-104">SYNOPSIS</span></span>
<span data-ttu-id="c4160-105">Hiermee verwijdert u een geregistreerde pakket bron.</span><span class="sxs-lookup"><span data-stu-id="c4160-105">Removes a registered package source.</span></span>

## <span data-ttu-id="c4160-106">SYNTAXIS</span><span class="sxs-lookup"><span data-stu-id="c4160-106">SYNTAX</span></span>

### <span data-ttu-id="c4160-107">SourceBySearch</span><span class="sxs-lookup"><span data-stu-id="c4160-107">SourceBySearch</span></span>

```
Unregister-PackageSource [[-Source] <String>] [-Location <String>] [-Credential <PSCredential>]
 [-Force] [-ForceBootstrap] [-WhatIf] [-Confirm] [-ProviderName <String>] [<CommonParameters>]
```

### <span data-ttu-id="c4160-108">SourceByInputObject</span><span class="sxs-lookup"><span data-stu-id="c4160-108">SourceByInputObject</span></span>

```
Unregister-PackageSource -InputObject <PackageSource[]> [-Credential <PSCredential>] [-Force]
 [-ForceBootstrap] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="c4160-109">NuGet: SourceByInputObject</span><span class="sxs-lookup"><span data-stu-id="c4160-109">NuGet:SourceByInputObject</span></span>

```
Unregister-PackageSource [-Credential <PSCredential>] [-Force] [-ForceBootstrap] [-WhatIf]
 [-Confirm] [-ConfigFile <String>] [-SkipValidate] [<CommonParameters>]
```

### <span data-ttu-id="c4160-110">NuGet: SourceBySearch</span><span class="sxs-lookup"><span data-stu-id="c4160-110">NuGet:SourceBySearch</span></span>

```
Unregister-PackageSource [-Credential <PSCredential>] [-Force] [-ForceBootstrap] [-WhatIf]
 [-Confirm] [-ConfigFile <String>] [-SkipValidate] [<CommonParameters>]
```

### <span data-ttu-id="c4160-111">PowerShellGet: SourceByInputObject</span><span class="sxs-lookup"><span data-stu-id="c4160-111">PowerShellGet:SourceByInputObject</span></span>

```
Unregister-PackageSource [-Credential <PSCredential>] [-Force] [-ForceBootstrap] [-WhatIf]
 [-Confirm] [-PackageManagementProvider <String>] [-PublishLocation <String>]
 [-ScriptSourceLocation <String>] [-ScriptPublishLocation <String>] [<CommonParameters>]
```

### <span data-ttu-id="c4160-112">PowerShellGet: SourceBySearch</span><span class="sxs-lookup"><span data-stu-id="c4160-112">PowerShellGet:SourceBySearch</span></span>

```
Unregister-PackageSource [-Credential <PSCredential>] [-Force] [-ForceBootstrap] [-WhatIf]
 [-Confirm] [-PackageManagementProvider <String>] [-PublishLocation <String>]
 [-ScriptSourceLocation <String>] [-ScriptPublishLocation <String>] [<CommonParameters>]
```

## <span data-ttu-id="c4160-113">BESCHRIJVING</span><span class="sxs-lookup"><span data-stu-id="c4160-113">DESCRIPTION</span></span>

<span data-ttu-id="c4160-114">Met de `Unregister-PackageSource` cmdlet wordt een geregistreerde pakket bron verwijderd.</span><span class="sxs-lookup"><span data-stu-id="c4160-114">The `Unregister-PackageSource` cmdlet removes a registered package source.</span></span> <span data-ttu-id="c4160-115">Pakket bronnen worden altijd beheerd door een pakket provider.</span><span class="sxs-lookup"><span data-stu-id="c4160-115">Package sources are always managed by a package provider.</span></span> <span data-ttu-id="c4160-116">Als u pakket bronnen wilt zoeken, gebruikt u de `Get-PackageSource` cmdlet.</span><span class="sxs-lookup"><span data-stu-id="c4160-116">To find package sources, use the `Get-PackageSource` cmdlet.</span></span>

## <span data-ttu-id="c4160-117">VOORBEELDEN</span><span class="sxs-lookup"><span data-stu-id="c4160-117">EXAMPLES</span></span>

### <span data-ttu-id="c4160-118">Voor beeld 1: de registratie van een pakket bron voor de Nuget-provider opheffen</span><span class="sxs-lookup"><span data-stu-id="c4160-118">Example 1: Unregister a package source for the Nuget provider</span></span>

<span data-ttu-id="c4160-119">Met de cmdlet wordt de `Unregister-PackageSource` registratie van een pakket bron van de lokale computer ongedaan gemaakt.</span><span class="sxs-lookup"><span data-stu-id="c4160-119">The `Unregister-PackageSource` cmdlet unregisters a package source from the local computer.</span></span> <span data-ttu-id="c4160-120">De para meters **locatie** en **provider** kunnen worden gebruikt om de bron die moet worden verwijderd, nader op te geven.</span><span class="sxs-lookup"><span data-stu-id="c4160-120">The **Location** and **Provider** parameters can be used to further specify the source to remove.</span></span>

```
PS> Unregister-PackageSource -Source MyNuGet
```

<span data-ttu-id="c4160-121">De `Unregister-PackageSource` cmdlet gebruikt de para meter **Source** om op te geven welke bron moet worden verwijderd.</span><span class="sxs-lookup"><span data-stu-id="c4160-121">The `Unregister-PackageSource` cmdlet uses the **Source** parameter to specify which source to remove.</span></span>

### <span data-ttu-id="c4160-122">Voor beeld 2: een PackageSource-object gebruiken om de registratie van een pakket op te heffen</span><span class="sxs-lookup"><span data-stu-id="c4160-122">Example 2: Use a PackageSource object to unregister a package</span></span>

<span data-ttu-id="c4160-123">In dit voor beeld wordt de `Get-PackageSource` en gebruikt `Unregister-PackageSource` om de registratie van een pakket bron ongedaan te maken.</span><span class="sxs-lookup"><span data-stu-id="c4160-123">This example uses the `Get-PackageSource` and `Unregister-PackageSource` to unregister a package source.</span></span> <span data-ttu-id="c4160-124">Het **PackageSource** -object wordt opgeslagen in een variabele.</span><span class="sxs-lookup"><span data-stu-id="c4160-124">The **PackageSource** object is stored in a variable.</span></span>

```
PS> $pkgsource = Get-PackageSource -Name MyNuGet
PS> Unregister-PackageSource -InputObject $pkgsource
```

<span data-ttu-id="c4160-125">De `$pkgsource` variabele bevat de **PackageSource** die door de `Get-PackageSource` cmdlet is gemaakt.</span><span class="sxs-lookup"><span data-stu-id="c4160-125">The `$pkgsource` variable stores the **PackageSource** created by the `Get-PackageSource` cmdlet.</span></span>
<span data-ttu-id="c4160-126">`Unregister-PackageSource` gebruikt de `$pkgsource` als-invoer voor de para meter **input object** .</span><span class="sxs-lookup"><span data-stu-id="c4160-126">`Unregister-PackageSource` uses the `$pkgsource` as input to the **InputObject** parameter.</span></span>

<span data-ttu-id="c4160-127">Als alternatief `Unregister-PackageSource` kan de cmdlet een waarde opgeven voor de para meter **input object** :</span><span class="sxs-lookup"><span data-stu-id="c4160-127">As an alternative, the `Unregister-PackageSource` cmdlet can specify a value for the **InputObject** parameter:</span></span>

`Unregister-PackageSource -InputObject ( Get-PackageSource -Name MyNuGet )`

## <span data-ttu-id="c4160-128">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="c4160-128">PARAMETERS</span></span>

### <span data-ttu-id="c4160-129">-ConfigFile</span><span class="sxs-lookup"><span data-stu-id="c4160-129">-ConfigFile</span></span>

<span data-ttu-id="c4160-130">Hiermee geeft u een configuratie bestand op.</span><span class="sxs-lookup"><span data-stu-id="c4160-130">Specifies a configuration file.</span></span>

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

### <span data-ttu-id="c4160-131">-Credential</span><span class="sxs-lookup"><span data-stu-id="c4160-131">-Credential</span></span>

<span data-ttu-id="c4160-132">Hiermee geeft u een gebruikers account op dat is gemachtigd om toegang te krijgen tot de computer en om opdrachten uit te voeren.</span><span class="sxs-lookup"><span data-stu-id="c4160-132">Specifies a user account that has permission to access the computer and run commands.</span></span> <span data-ttu-id="c4160-133">Typ een gebruikers naam, zoals **gebruiker01** , **Domain01\User01** , of voer een **PSCredential** -object in dat door de `Get-Credential` cmdlet wordt gegenereerd.</span><span class="sxs-lookup"><span data-stu-id="c4160-133">Type a user name, such as **User01** , **Domain01\User01** , or enter a **PSCredential** object, generated by the `Get-Credential` cmdlet.</span></span> <span data-ttu-id="c4160-134">Als u een gebruikers naam typt, wordt u gevraagd een wacht woord op te vragen.</span><span class="sxs-lookup"><span data-stu-id="c4160-134">If you type a user name, you're prompted for a password.</span></span>

<span data-ttu-id="c4160-135">Als de para meter **Credential** niet is opgegeven, wordt het huidige gebruikers account gebruikt.</span><span class="sxs-lookup"><span data-stu-id="c4160-135">When the **Credential** parameter isn't specified, the current user account is used.</span></span>

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

### <span data-ttu-id="c4160-136">-Force</span><span class="sxs-lookup"><span data-stu-id="c4160-136">-Force</span></span>

<span data-ttu-id="c4160-137">Hiermee wordt de opdracht uitgevoerd zonder dat de gebruiker om bevestiging wordt gevraagd.</span><span class="sxs-lookup"><span data-stu-id="c4160-137">Forces the command to run without asking for user confirmation.</span></span> <span data-ttu-id="c4160-138">Onderdrukkingen van beperkingen die voor komen dat `Unregister-PackageSource` de slagen worden voltooid, met uitzonde ring van beveiliging.</span><span class="sxs-lookup"><span data-stu-id="c4160-138">Overrides restrictions that prevent `Unregister-PackageSource` from succeeding, with the exception of security.</span></span>

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

### <span data-ttu-id="c4160-139">-ForceBootstrap</span><span class="sxs-lookup"><span data-stu-id="c4160-139">-ForceBootstrap</span></span>

<span data-ttu-id="c4160-140">Geeft aan `Unregister-PackageSource` dat **Package Management** automatisch de pakket provider voor de opgegeven pakket bron verwijdert.</span><span class="sxs-lookup"><span data-stu-id="c4160-140">Indicates that `Unregister-PackageSource` forces **PackageManagement** to automatically uninstall the package provider for the specified package source.</span></span>

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

### <span data-ttu-id="c4160-141">-Input object</span><span class="sxs-lookup"><span data-stu-id="c4160-141">-InputObject</span></span>

<span data-ttu-id="c4160-142">Hiermee wordt een pijplijn invoer geaccepteerd die het **PackageSource** -object van de cmdlet specificeert `Get-PackageSource` .</span><span class="sxs-lookup"><span data-stu-id="c4160-142">Accepts pipeline input that specifies the **PackageSource** object from the `Get-PackageSource` cmdlet.</span></span> <span data-ttu-id="c4160-143">**Input object** accepteert het **PackageSource** -object als een `Get-PackageSource` waarde of een variabele die het object bevat.</span><span class="sxs-lookup"><span data-stu-id="c4160-143">**InputObject** accepts the **PackageSource** object as a `Get-PackageSource` value or a variable that contains the object.</span></span>

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

### <span data-ttu-id="c4160-144">-Locatie</span><span class="sxs-lookup"><span data-stu-id="c4160-144">-Location</span></span>

<span data-ttu-id="c4160-145">Hiermee geeft u de locatie op van de pakket bron punten.</span><span class="sxs-lookup"><span data-stu-id="c4160-145">Specifies the location to which a package source points.</span></span> <span data-ttu-id="c4160-146">De waarde van deze para meter kan een URI, een bestandspad of een andere bestemmings indeling zijn die wordt ondersteund door de pakket provider.</span><span class="sxs-lookup"><span data-stu-id="c4160-146">The value of this parameter can be a URI, a file path, or any other destination format that is supported by the package provider.</span></span>

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

### <span data-ttu-id="c4160-147">-PackageManagementProvider</span><span class="sxs-lookup"><span data-stu-id="c4160-147">-PackageManagementProvider</span></span>

<span data-ttu-id="c4160-148">Hiermee geeft u de **Package Management** -provider.</span><span class="sxs-lookup"><span data-stu-id="c4160-148">Specifies the **PackageManagement** provider.</span></span>

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

### <span data-ttu-id="c4160-149">-ProviderName</span><span class="sxs-lookup"><span data-stu-id="c4160-149">-ProviderName</span></span>

<span data-ttu-id="c4160-150">Hiermee geeft u de naam van de provider.</span><span class="sxs-lookup"><span data-stu-id="c4160-150">Specifies the provider name.</span></span>

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

### <span data-ttu-id="c4160-151">-PublishLocation</span><span class="sxs-lookup"><span data-stu-id="c4160-151">-PublishLocation</span></span>

<span data-ttu-id="c4160-152">Hiermee geeft u de publicatie locatie op.</span><span class="sxs-lookup"><span data-stu-id="c4160-152">Specifies the publish location.</span></span>

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

### <span data-ttu-id="c4160-153">-ScriptPublishLocation</span><span class="sxs-lookup"><span data-stu-id="c4160-153">-ScriptPublishLocation</span></span>

<span data-ttu-id="c4160-154">Hiermee geeft u de publicatie locatie van het script op.</span><span class="sxs-lookup"><span data-stu-id="c4160-154">Specifies the script publish location.</span></span>

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

### <span data-ttu-id="c4160-155">-ScriptSourceLocation</span><span class="sxs-lookup"><span data-stu-id="c4160-155">-ScriptSourceLocation</span></span>

<span data-ttu-id="c4160-156">Hiermee geeft u de bron locatie van het script op.</span><span class="sxs-lookup"><span data-stu-id="c4160-156">Specifies the script source location.</span></span>

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

### <span data-ttu-id="c4160-157">-SkipValidate</span><span class="sxs-lookup"><span data-stu-id="c4160-157">-SkipValidate</span></span>

<span data-ttu-id="c4160-158">Switch waarmee de validatie van de referenties van een pakket bron wordt overgeslagen.</span><span class="sxs-lookup"><span data-stu-id="c4160-158">Switch that skips validating the credentials of a package source.</span></span>

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

### <span data-ttu-id="c4160-159">-Source</span><span class="sxs-lookup"><span data-stu-id="c4160-159">-Source</span></span>

<span data-ttu-id="c4160-160">Hiermee geeft u de beschrijvende naam van de pakket bron op.</span><span class="sxs-lookup"><span data-stu-id="c4160-160">Specifies the friendly name of the package source.</span></span>

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

### <span data-ttu-id="c4160-161">-Confirm</span><span class="sxs-lookup"><span data-stu-id="c4160-161">-Confirm</span></span>

<span data-ttu-id="c4160-162">Vraagt u om bevestiging voordat deze `Unregister-PackageSource` wordt uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="c4160-162">Prompts you for confirmation before `Unregister-PackageSource` is run.</span></span>

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

### <span data-ttu-id="c4160-163">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="c4160-163">-WhatIf</span></span>

<span data-ttu-id="c4160-164">Laat zien wat er zou gebeuren als de `Unregister-PackageSource` cmdlet wordt uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="c4160-164">Shows what would happen if `Unregister-PackageSource` cmdlet is run.</span></span> <span data-ttu-id="c4160-165">De cmdlet wordt niet uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="c4160-165">The cmdlet isn't run.</span></span>

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

### <span data-ttu-id="c4160-166">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="c4160-166">CommonParameters</span></span>

<span data-ttu-id="c4160-167">Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="c4160-167">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="c4160-168">Zie [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="c4160-168">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="c4160-169">INVOER</span><span class="sxs-lookup"><span data-stu-id="c4160-169">INPUTS</span></span>

### <span data-ttu-id="c4160-170">`Unregister-PackageSource` Hiermee worden **PackageSource** -objecten van de pijp lijn geaccepteerd als invoer.</span><span class="sxs-lookup"><span data-stu-id="c4160-170">`Unregister-PackageSource` accepts **PackageSource** objects from the pipeline as input.</span></span>

## <span data-ttu-id="c4160-171">UITVOER</span><span class="sxs-lookup"><span data-stu-id="c4160-171">OUTPUTS</span></span>

### <span data-ttu-id="c4160-172">`Unregister-PackageSource` Er wordt geen uitvoer gegenereerd.</span><span class="sxs-lookup"><span data-stu-id="c4160-172">`Unregister-PackageSource` doesn't generate any output.</span></span>

## <span data-ttu-id="c4160-173">OPMERKINGEN</span><span class="sxs-lookup"><span data-stu-id="c4160-173">NOTES</span></span>

<span data-ttu-id="c4160-174">Het opnemen van een pakket provider in een opdracht kan dynamische para meters beschikbaar maken voor een cmdlet.</span><span class="sxs-lookup"><span data-stu-id="c4160-174">Including a package provider in a command can make dynamic parameters available to a cmdlet.</span></span> <span data-ttu-id="c4160-175">Dynamische para meters zijn specifiek voor een pakket provider.</span><span class="sxs-lookup"><span data-stu-id="c4160-175">Dynamic parameters are specific to a package provider.</span></span> <span data-ttu-id="c4160-176">De `Get-Help` cmdlet geeft een lijst van de parameter sets van de cmdlet en bevat de parameterset van de provider.</span><span class="sxs-lookup"><span data-stu-id="c4160-176">The `Get-Help` cmdlet lists a cmdlet's parameter sets and includes the provider's parameter set.</span></span>

## <span data-ttu-id="c4160-177">GERELATEERDE KOPPELINGEN</span><span class="sxs-lookup"><span data-stu-id="c4160-177">RELATED LINKS</span></span>

[<span data-ttu-id="c4160-178">about_PackageManagement</span><span class="sxs-lookup"><span data-stu-id="c4160-178">about_PackageManagement</span></span>](../Microsoft.PowerShell.Core/About/about_PackageManagement.md)

[<span data-ttu-id="c4160-179">Get-Credential</span><span class="sxs-lookup"><span data-stu-id="c4160-179">Get-Credential</span></span>](../Microsoft.PowerShell.Security/Get-Credential.md)

[<span data-ttu-id="c4160-180">Get-PackageSource</span><span class="sxs-lookup"><span data-stu-id="c4160-180">Get-PackageSource</span></span>](Get-PackageSource.md)

[<span data-ttu-id="c4160-181">REGI ster-PackageSource</span><span class="sxs-lookup"><span data-stu-id="c4160-181">Register-PackageSource</span></span>](Register-PackageSource.md)

[<span data-ttu-id="c4160-182">Set-PackageSource</span><span class="sxs-lookup"><span data-stu-id="c4160-182">Set-PackageSource</span></span>](Set-PackageSource.md)

