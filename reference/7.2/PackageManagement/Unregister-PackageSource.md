---
external help file: Microsoft.PowerShell.PackageManagement.dll-Help.xml
Locale: en-US
Module Name: PackageManagement
ms.date: 05/24/2019
online version: https://docs.microsoft.com/powershell/module/packagemanagement/unregister-packagesource?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Unregister-PackageSource
ms.openlocfilehash: 6ef89e9143fe8883bc98723d10775bf739fe72f9
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 11/17/2020
ms.locfileid: "94705560"
---
# <span data-ttu-id="42cc4-102">Unregister-PackageSource</span><span class="sxs-lookup"><span data-stu-id="42cc4-102">Unregister-PackageSource</span></span>

## <span data-ttu-id="42cc4-103">SAMENVATTING</span><span class="sxs-lookup"><span data-stu-id="42cc4-103">SYNOPSIS</span></span>
<span data-ttu-id="42cc4-104">Hiermee verwijdert u een geregistreerde pakket bron.</span><span class="sxs-lookup"><span data-stu-id="42cc4-104">Removes a registered package source.</span></span>

## <span data-ttu-id="42cc4-105">SYNTAXIS</span><span class="sxs-lookup"><span data-stu-id="42cc4-105">SYNTAX</span></span>

### <span data-ttu-id="42cc4-106">SourceBySearch</span><span class="sxs-lookup"><span data-stu-id="42cc4-106">SourceBySearch</span></span>

```
Unregister-PackageSource [[-Source] <String>] [-Location <String>] [-Credential <PSCredential>]
 [-Force] [-ForceBootstrap] [-WhatIf] [-Confirm] [-ProviderName <String>] [<CommonParameters>]
```

### <span data-ttu-id="42cc4-107">SourceByInputObject</span><span class="sxs-lookup"><span data-stu-id="42cc4-107">SourceByInputObject</span></span>

```
Unregister-PackageSource -InputObject <PackageSource[]> [-Credential <PSCredential>] [-Force]
 [-ForceBootstrap] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="42cc4-108">NuGet: SourceByInputObject</span><span class="sxs-lookup"><span data-stu-id="42cc4-108">NuGet:SourceByInputObject</span></span>

```
Unregister-PackageSource [-Credential <PSCredential>] [-Force] [-ForceBootstrap] [-WhatIf]
 [-Confirm] [-ConfigFile <String>] [-SkipValidate] [<CommonParameters>]
```

### <span data-ttu-id="42cc4-109">NuGet: SourceBySearch</span><span class="sxs-lookup"><span data-stu-id="42cc4-109">NuGet:SourceBySearch</span></span>

```
Unregister-PackageSource [-Credential <PSCredential>] [-Force] [-ForceBootstrap] [-WhatIf]
 [-Confirm] [-ConfigFile <String>] [-SkipValidate] [<CommonParameters>]
```

### <span data-ttu-id="42cc4-110">PowerShellGet: SourceByInputObject</span><span class="sxs-lookup"><span data-stu-id="42cc4-110">PowerShellGet:SourceByInputObject</span></span>

```
Unregister-PackageSource [-Credential <PSCredential>] [-Force] [-ForceBootstrap] [-WhatIf]
 [-Confirm] [-PackageManagementProvider <String>] [-PublishLocation <String>]
 [-ScriptSourceLocation <String>] [-ScriptPublishLocation <String>] [<CommonParameters>]
```

### <span data-ttu-id="42cc4-111">PowerShellGet: SourceBySearch</span><span class="sxs-lookup"><span data-stu-id="42cc4-111">PowerShellGet:SourceBySearch</span></span>

```
Unregister-PackageSource [-Credential <PSCredential>] [-Force] [-ForceBootstrap] [-WhatIf]
 [-Confirm] [-PackageManagementProvider <String>] [-PublishLocation <String>]
 [-ScriptSourceLocation <String>] [-ScriptPublishLocation <String>] [<CommonParameters>]
```

## <span data-ttu-id="42cc4-112">BESCHRIJVING</span><span class="sxs-lookup"><span data-stu-id="42cc4-112">DESCRIPTION</span></span>

<span data-ttu-id="42cc4-113">Met de `Unregister-PackageSource` cmdlet wordt een geregistreerde pakket bron verwijderd.</span><span class="sxs-lookup"><span data-stu-id="42cc4-113">The `Unregister-PackageSource` cmdlet removes a registered package source.</span></span> <span data-ttu-id="42cc4-114">Pakket bronnen worden altijd beheerd door een pakket provider.</span><span class="sxs-lookup"><span data-stu-id="42cc4-114">Package sources are always managed by a package provider.</span></span> <span data-ttu-id="42cc4-115">Als u pakket bronnen wilt zoeken, gebruikt u de `Get-PackageSource` cmdlet.</span><span class="sxs-lookup"><span data-stu-id="42cc4-115">To find package sources, use the `Get-PackageSource` cmdlet.</span></span>

## <span data-ttu-id="42cc4-116">VOORBEELDEN</span><span class="sxs-lookup"><span data-stu-id="42cc4-116">EXAMPLES</span></span>

### <span data-ttu-id="42cc4-117">Voor beeld 1: de registratie van een pakket bron voor de Nuget-provider opheffen</span><span class="sxs-lookup"><span data-stu-id="42cc4-117">Example 1: Unregister a package source for the Nuget provider</span></span>

<span data-ttu-id="42cc4-118">Met de cmdlet wordt de `Unregister-PackageSource` registratie van een pakket bron van de lokale computer ongedaan gemaakt.</span><span class="sxs-lookup"><span data-stu-id="42cc4-118">The `Unregister-PackageSource` cmdlet unregisters a package source from the local computer.</span></span> <span data-ttu-id="42cc4-119">De para meters **locatie** en **provider** kunnen worden gebruikt om de bron die moet worden verwijderd, nader op te geven.</span><span class="sxs-lookup"><span data-stu-id="42cc4-119">The **Location** and **Provider** parameters can be used to further specify the source to remove.</span></span>

```
PS> Unregister-PackageSource -Source MyNuGet
```

<span data-ttu-id="42cc4-120">De `Unregister-PackageSource` cmdlet gebruikt de para meter **Source** om op te geven welke bron moet worden verwijderd.</span><span class="sxs-lookup"><span data-stu-id="42cc4-120">The `Unregister-PackageSource` cmdlet uses the **Source** parameter to specify which source to remove.</span></span>

### <span data-ttu-id="42cc4-121">Voor beeld 2: een PackageSource-object gebruiken om de registratie van een pakket op te heffen</span><span class="sxs-lookup"><span data-stu-id="42cc4-121">Example 2: Use a PackageSource object to unregister a package</span></span>

<span data-ttu-id="42cc4-122">In dit voor beeld wordt de `Get-PackageSource` en gebruikt `Unregister-PackageSource` om de registratie van een pakket bron ongedaan te maken.</span><span class="sxs-lookup"><span data-stu-id="42cc4-122">This example uses the `Get-PackageSource` and `Unregister-PackageSource` to unregister a package source.</span></span> <span data-ttu-id="42cc4-123">Het **PackageSource** -object wordt opgeslagen in een variabele.</span><span class="sxs-lookup"><span data-stu-id="42cc4-123">The **PackageSource** object is stored in a variable.</span></span>

```
PS> $pkgsource = Get-PackageSource -Name MyNuGet
PS> Unregister-PackageSource -InputObject $pkgsource
```

<span data-ttu-id="42cc4-124">De `$pkgsource` variabele bevat de **PackageSource** die door de `Get-PackageSource` cmdlet is gemaakt.</span><span class="sxs-lookup"><span data-stu-id="42cc4-124">The `$pkgsource` variable stores the **PackageSource** created by the `Get-PackageSource` cmdlet.</span></span>
<span data-ttu-id="42cc4-125">`Unregister-PackageSource` gebruikt de `$pkgsource` als-invoer voor de para meter **input object** .</span><span class="sxs-lookup"><span data-stu-id="42cc4-125">`Unregister-PackageSource` uses the `$pkgsource` as input to the **InputObject** parameter.</span></span>

<span data-ttu-id="42cc4-126">Als alternatief `Unregister-PackageSource` kan de cmdlet een waarde opgeven voor de para meter **input object** :</span><span class="sxs-lookup"><span data-stu-id="42cc4-126">As an alternative, the `Unregister-PackageSource` cmdlet can specify a value for the **InputObject** parameter:</span></span>

`Unregister-PackageSource -InputObject ( Get-PackageSource -Name MyNuGet )`

## <span data-ttu-id="42cc4-127">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="42cc4-127">PARAMETERS</span></span>

### <span data-ttu-id="42cc4-128">-ConfigFile</span><span class="sxs-lookup"><span data-stu-id="42cc4-128">-ConfigFile</span></span>

<span data-ttu-id="42cc4-129">Hiermee geeft u een configuratie bestand op.</span><span class="sxs-lookup"><span data-stu-id="42cc4-129">Specifies a configuration file.</span></span>

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

### <span data-ttu-id="42cc4-130">-Credential</span><span class="sxs-lookup"><span data-stu-id="42cc4-130">-Credential</span></span>

<span data-ttu-id="42cc4-131">Hiermee geeft u een gebruikers account op dat is gemachtigd om toegang te krijgen tot de computer en om opdrachten uit te voeren.</span><span class="sxs-lookup"><span data-stu-id="42cc4-131">Specifies a user account that has permission to access the computer and run commands.</span></span> <span data-ttu-id="42cc4-132">Typ een gebruikers naam, zoals **gebruiker01**, **Domain01\User01**, of voer een **PSCredential** -object in dat door de `Get-Credential` cmdlet wordt gegenereerd.</span><span class="sxs-lookup"><span data-stu-id="42cc4-132">Type a user name, such as **User01**, **Domain01\User01**, or enter a **PSCredential** object, generated by the `Get-Credential` cmdlet.</span></span> <span data-ttu-id="42cc4-133">Als u een gebruikers naam typt, wordt u gevraagd een wacht woord op te vragen.</span><span class="sxs-lookup"><span data-stu-id="42cc4-133">If you type a user name, you're prompted for a password.</span></span>

<span data-ttu-id="42cc4-134">Als de para meter **Credential** niet is opgegeven, wordt het huidige gebruikers account gebruikt.</span><span class="sxs-lookup"><span data-stu-id="42cc4-134">When the **Credential** parameter isn't specified, the current user account is used.</span></span>

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

### <span data-ttu-id="42cc4-135">-Force</span><span class="sxs-lookup"><span data-stu-id="42cc4-135">-Force</span></span>

<span data-ttu-id="42cc4-136">Hiermee wordt de opdracht uitgevoerd zonder dat de gebruiker om bevestiging wordt gevraagd.</span><span class="sxs-lookup"><span data-stu-id="42cc4-136">Forces the command to run without asking for user confirmation.</span></span> <span data-ttu-id="42cc4-137">Onderdrukkingen van beperkingen die voor komen dat `Unregister-PackageSource` de slagen worden voltooid, met uitzonde ring van beveiliging.</span><span class="sxs-lookup"><span data-stu-id="42cc4-137">Overrides restrictions that prevent `Unregister-PackageSource` from succeeding, with the exception of security.</span></span>

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

### <span data-ttu-id="42cc4-138">-ForceBootstrap</span><span class="sxs-lookup"><span data-stu-id="42cc4-138">-ForceBootstrap</span></span>

<span data-ttu-id="42cc4-139">Geeft aan `Unregister-PackageSource` dat **Package Management** automatisch de pakket provider voor de opgegeven pakket bron verwijdert.</span><span class="sxs-lookup"><span data-stu-id="42cc4-139">Indicates that `Unregister-PackageSource` forces **PackageManagement** to automatically uninstall the package provider for the specified package source.</span></span>

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

### <span data-ttu-id="42cc4-140">-Input object</span><span class="sxs-lookup"><span data-stu-id="42cc4-140">-InputObject</span></span>

<span data-ttu-id="42cc4-141">Hiermee wordt een pijplijn invoer geaccepteerd die het **PackageSource** -object van de cmdlet specificeert `Get-PackageSource` .</span><span class="sxs-lookup"><span data-stu-id="42cc4-141">Accepts pipeline input that specifies the **PackageSource** object from the `Get-PackageSource` cmdlet.</span></span> <span data-ttu-id="42cc4-142">**Input object** accepteert het **PackageSource** -object als een `Get-PackageSource` waarde of een variabele die het object bevat.</span><span class="sxs-lookup"><span data-stu-id="42cc4-142">**InputObject** accepts the **PackageSource** object as a `Get-PackageSource` value or a variable that contains the object.</span></span>

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

### <span data-ttu-id="42cc4-143">-Locatie</span><span class="sxs-lookup"><span data-stu-id="42cc4-143">-Location</span></span>

<span data-ttu-id="42cc4-144">Hiermee geeft u de locatie op van de pakket bron punten.</span><span class="sxs-lookup"><span data-stu-id="42cc4-144">Specifies the location to which a package source points.</span></span> <span data-ttu-id="42cc4-145">De waarde van deze para meter kan een URI, een bestandspad of een andere bestemmings indeling zijn die wordt ondersteund door de pakket provider.</span><span class="sxs-lookup"><span data-stu-id="42cc4-145">The value of this parameter can be a URI, a file path, or any other destination format that is supported by the package provider.</span></span>

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

### <span data-ttu-id="42cc4-146">-PackageManagementProvider</span><span class="sxs-lookup"><span data-stu-id="42cc4-146">-PackageManagementProvider</span></span>

<span data-ttu-id="42cc4-147">Hiermee geeft u de **Package Management** -provider.</span><span class="sxs-lookup"><span data-stu-id="42cc4-147">Specifies the **PackageManagement** provider.</span></span>

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

### <span data-ttu-id="42cc4-148">-ProviderName</span><span class="sxs-lookup"><span data-stu-id="42cc4-148">-ProviderName</span></span>

<span data-ttu-id="42cc4-149">Hiermee geeft u de naam van de provider.</span><span class="sxs-lookup"><span data-stu-id="42cc4-149">Specifies the provider name.</span></span>

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

### <span data-ttu-id="42cc4-150">-PublishLocation</span><span class="sxs-lookup"><span data-stu-id="42cc4-150">-PublishLocation</span></span>

<span data-ttu-id="42cc4-151">Hiermee geeft u de publicatie locatie op.</span><span class="sxs-lookup"><span data-stu-id="42cc4-151">Specifies the publish location.</span></span>

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

### <span data-ttu-id="42cc4-152">-ScriptPublishLocation</span><span class="sxs-lookup"><span data-stu-id="42cc4-152">-ScriptPublishLocation</span></span>

<span data-ttu-id="42cc4-153">Hiermee geeft u de publicatie locatie van het script op.</span><span class="sxs-lookup"><span data-stu-id="42cc4-153">Specifies the script publish location.</span></span>

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

### <span data-ttu-id="42cc4-154">-ScriptSourceLocation</span><span class="sxs-lookup"><span data-stu-id="42cc4-154">-ScriptSourceLocation</span></span>

<span data-ttu-id="42cc4-155">Hiermee geeft u de bron locatie van het script op.</span><span class="sxs-lookup"><span data-stu-id="42cc4-155">Specifies the script source location.</span></span>

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

### <span data-ttu-id="42cc4-156">-SkipValidate</span><span class="sxs-lookup"><span data-stu-id="42cc4-156">-SkipValidate</span></span>

<span data-ttu-id="42cc4-157">Switch waarmee de validatie van de referenties van een pakket bron wordt overgeslagen.</span><span class="sxs-lookup"><span data-stu-id="42cc4-157">Switch that skips validating the credentials of a package source.</span></span>

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

### <span data-ttu-id="42cc4-158">-Source</span><span class="sxs-lookup"><span data-stu-id="42cc4-158">-Source</span></span>

<span data-ttu-id="42cc4-159">Hiermee geeft u de beschrijvende naam van de pakket bron op.</span><span class="sxs-lookup"><span data-stu-id="42cc4-159">Specifies the friendly name of the package source.</span></span>

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

### <span data-ttu-id="42cc4-160">-Confirm</span><span class="sxs-lookup"><span data-stu-id="42cc4-160">-Confirm</span></span>

<span data-ttu-id="42cc4-161">Vraagt u om bevestiging voordat deze `Unregister-PackageSource` wordt uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="42cc4-161">Prompts you for confirmation before `Unregister-PackageSource` is run.</span></span>

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

### <span data-ttu-id="42cc4-162">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="42cc4-162">-WhatIf</span></span>

<span data-ttu-id="42cc4-163">Laat zien wat er zou gebeuren als de `Unregister-PackageSource` cmdlet wordt uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="42cc4-163">Shows what would happen if `Unregister-PackageSource` cmdlet is run.</span></span> <span data-ttu-id="42cc4-164">De cmdlet wordt niet uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="42cc4-164">The cmdlet isn't run.</span></span>

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

### <span data-ttu-id="42cc4-165">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="42cc4-165">CommonParameters</span></span>

<span data-ttu-id="42cc4-166">Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="42cc4-166">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="42cc4-167">Zie [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="42cc4-167">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="42cc4-168">INVOER</span><span class="sxs-lookup"><span data-stu-id="42cc4-168">INPUTS</span></span>

### <span data-ttu-id="42cc4-169">`Unregister-PackageSource` Hiermee worden **PackageSource** -objecten van de pijp lijn geaccepteerd als invoer.</span><span class="sxs-lookup"><span data-stu-id="42cc4-169">`Unregister-PackageSource` accepts **PackageSource** objects from the pipeline as input.</span></span>

## <span data-ttu-id="42cc4-170">UITVOER</span><span class="sxs-lookup"><span data-stu-id="42cc4-170">OUTPUTS</span></span>

### <span data-ttu-id="42cc4-171">`Unregister-PackageSource` Er wordt geen uitvoer gegenereerd.</span><span class="sxs-lookup"><span data-stu-id="42cc4-171">`Unregister-PackageSource` doesn't generate any output.</span></span>

## <span data-ttu-id="42cc4-172">OPMERKINGEN</span><span class="sxs-lookup"><span data-stu-id="42cc4-172">NOTES</span></span>

<span data-ttu-id="42cc4-173">Het opnemen van een pakket provider in een opdracht kan dynamische para meters beschikbaar maken voor een cmdlet.</span><span class="sxs-lookup"><span data-stu-id="42cc4-173">Including a package provider in a command can make dynamic parameters available to a cmdlet.</span></span> <span data-ttu-id="42cc4-174">Dynamische para meters zijn specifiek voor een pakket provider.</span><span class="sxs-lookup"><span data-stu-id="42cc4-174">Dynamic parameters are specific to a package provider.</span></span> <span data-ttu-id="42cc4-175">De `Get-Help` cmdlet geeft een lijst van de parameter sets van de cmdlet en bevat de parameterset van de provider.</span><span class="sxs-lookup"><span data-stu-id="42cc4-175">The `Get-Help` cmdlet lists a cmdlet's parameter sets and includes the provider's parameter set.</span></span>

## <span data-ttu-id="42cc4-176">GERELATEERDE KOPPELINGEN</span><span class="sxs-lookup"><span data-stu-id="42cc4-176">RELATED LINKS</span></span>

[<span data-ttu-id="42cc4-177">about_PackageManagement</span><span class="sxs-lookup"><span data-stu-id="42cc4-177">about_PackageManagement</span></span>](../Microsoft.PowerShell.Core/About/about_PackageManagement.md)

[<span data-ttu-id="42cc4-178">Get-Credential</span><span class="sxs-lookup"><span data-stu-id="42cc4-178">Get-Credential</span></span>](../Microsoft.PowerShell.Security/Get-Credential.md)

[<span data-ttu-id="42cc4-179">Get-PackageSource</span><span class="sxs-lookup"><span data-stu-id="42cc4-179">Get-PackageSource</span></span>](Get-PackageSource.md)

[<span data-ttu-id="42cc4-180">REGI ster-PackageSource</span><span class="sxs-lookup"><span data-stu-id="42cc4-180">Register-PackageSource</span></span>](Register-PackageSource.md)

[<span data-ttu-id="42cc4-181">Set-PackageSource</span><span class="sxs-lookup"><span data-stu-id="42cc4-181">Set-PackageSource</span></span>](Set-PackageSource.md)

