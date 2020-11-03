---
external help file: Microsoft.PowerShell.PackageManagement.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: PackageManagement
ms.date: 03/29/2019
online version: https://docs.microsoft.com/powershell/module/packagemanagement/get-packagesource?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-PackageSource
ms.openlocfilehash: 81b6f94be6293733ec75d48b1f9dd7ac4f4f8d96
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/07/2020
ms.locfileid: "93250167"
---
# <span data-ttu-id="4e48a-103">Get-PackageSource</span><span class="sxs-lookup"><span data-stu-id="4e48a-103">Get-PackageSource</span></span>

## <span data-ttu-id="4e48a-104">SAMENVATTING</span><span class="sxs-lookup"><span data-stu-id="4e48a-104">SYNOPSIS</span></span>
<span data-ttu-id="4e48a-105">Hiermee wordt een lijst opgehaald met pakket bronnen die zijn geregistreerd voor een pakket provider.</span><span class="sxs-lookup"><span data-stu-id="4e48a-105">Gets a list of package sources that are registered for a package provider.</span></span>

## <span data-ttu-id="4e48a-106">SYNTAXIS</span><span class="sxs-lookup"><span data-stu-id="4e48a-106">SYNTAX</span></span>

### <span data-ttu-id="4e48a-107">NuGet</span><span class="sxs-lookup"><span data-stu-id="4e48a-107">NuGet</span></span>

```
Get-PackageSource [[-Name] <String>] [-Location <String>] [-Force] [-ForceBootstrap]
 [-ProviderName <String[]>] [-ConfigFile <String>] [-SkipValidate] [<CommonParameters>]
```

### <span data-ttu-id="4e48a-108">PowerShellGet</span><span class="sxs-lookup"><span data-stu-id="4e48a-108">PowerShellGet</span></span>

```
Get-PackageSource [[-Name] <String>] [-Location <String>] [-Force] [-ForceBootstrap]
 [-ProviderName <String[]>] [-PackageManagementProvider <String>] [-PublishLocation <String>]
 [-ScriptSourceLocation <String>] [-ScriptPublishLocation <String>] [<CommonParameters>]
```

## <span data-ttu-id="4e48a-109">BESCHRIJVING</span><span class="sxs-lookup"><span data-stu-id="4e48a-109">DESCRIPTION</span></span>

<span data-ttu-id="4e48a-110">De `Get-PackageSource` cmdlet haalt een lijst op met pakket bronnen die zijn geregistreerd bij **Package Management** op de lokale computer.</span><span class="sxs-lookup"><span data-stu-id="4e48a-110">The `Get-PackageSource` cmdlet gets a list of package sources that are registered with **PackageManagement** on the local computer.</span></span> <span data-ttu-id="4e48a-111">Als u een pakket provider opgeeft, `Get-PackageSource` worden alleen de bronnen opgehaald die aan de opgegeven provider zijn gekoppeld.</span><span class="sxs-lookup"><span data-stu-id="4e48a-111">If you specify a package provider, `Get-PackageSource` gets only those sources that are associated with the specified provider.</span></span> <span data-ttu-id="4e48a-112">Anders retourneert de opdracht alle pakket bronnen die zijn geregistreerd bij **Package Management**.</span><span class="sxs-lookup"><span data-stu-id="4e48a-112">Otherwise, the command returns all package sources that are registered with **PackageManagement**.</span></span>

## <span data-ttu-id="4e48a-113">VOORBEELDEN</span><span class="sxs-lookup"><span data-stu-id="4e48a-113">EXAMPLES</span></span>

### <span data-ttu-id="4e48a-114">Voor beeld 1: alle pakket bronnen ophalen</span><span class="sxs-lookup"><span data-stu-id="4e48a-114">Example 1: Get all package sources</span></span>

<span data-ttu-id="4e48a-115">De `Get-PackageSource` cmdlet haalt alle pakket bronnen op die zijn geregistreerd bij **Package Management** op de lokale computer.</span><span class="sxs-lookup"><span data-stu-id="4e48a-115">The `Get-PackageSource` cmdlet gets all package sources that are registered with **PackageManagement** on the local computer.</span></span>

```powershell
Get-PackageSource
```

```Output
Name                 ProviderName     IsTrusted  Location
----                 ------------     ---------  --------
LocalPackages        NuGet            False      C:\LocalPkg\
MyNuget              NuGet            False      https://www.nuget.org/api/v2
PSGallery            PowerShellGet    False      https://www.powershellgallery.com/api/v2
```

### <span data-ttu-id="4e48a-116">Voor beeld 2: alle pakket bronnen voor een specifieke provider ophalen</span><span class="sxs-lookup"><span data-stu-id="4e48a-116">Example 2: Get all package sources for a specific provider</span></span>

<span data-ttu-id="4e48a-117">Met deze opdracht worden pakket bronnen opgehaald die zijn geregistreerd voor een specifieke provider.</span><span class="sxs-lookup"><span data-stu-id="4e48a-117">This command gets package sources that are registered for a specific provider.</span></span>

```powershell
Get-PackageSource -ProviderName NuGet
```

```Output
Name                 ProviderName     IsTrusted  Location
----                 ------------     ---------  --------
LocalPackages        NuGet            False      C:\LocalPkg\
MyNuget              NuGet            False      https://www.nuget.org/api/v2
```

<span data-ttu-id="4e48a-118">`Get-PackageSource` maakt gebruik van de para meter **ProviderName** om pakket bronnen op te halen die zijn geregistreerd voor de **NuGet** -provider.</span><span class="sxs-lookup"><span data-stu-id="4e48a-118">`Get-PackageSource` uses the **ProviderName** parameter to get package sources that are registered for the **NuGet** provider.</span></span>

### <span data-ttu-id="4e48a-119">Voor beeld 3: bronnen van een pakket provider ophalen</span><span class="sxs-lookup"><span data-stu-id="4e48a-119">Example 3: Get sources from a package provider</span></span>

<span data-ttu-id="4e48a-120">Met deze opdracht wordt een pakket provider gebruikt om pakket bronnen op te halen.</span><span class="sxs-lookup"><span data-stu-id="4e48a-120">This command uses a package provider to get package sources.</span></span>

```powershell
Get-PackageProvider -Name NuGet | Get-PackageSource
```

```Output
Name                 ProviderName     IsTrusted  Location
----                 ------------     ---------  --------
LocalPackages        NuGet            False      C:\LocalPkg\
MyNuget              NuGet            False      https://www.nuget.org/api/v2
```

<span data-ttu-id="4e48a-121">`Get-PackageProvider` Hiermee gebruikt u de para meter **name** om de naam van de provider op te geven, **NuGet**.</span><span class="sxs-lookup"><span data-stu-id="4e48a-121">`Get-PackageProvider` uses the **Name** parameter specify the provider name, **NuGet**.</span></span> <span data-ttu-id="4e48a-122">Het object wordt naar de pijp lijn verzonden `Get-PackageSource` .</span><span class="sxs-lookup"><span data-stu-id="4e48a-122">The object is sent down the pipeline to `Get-PackageSource`.</span></span>

## <span data-ttu-id="4e48a-123">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="4e48a-123">PARAMETERS</span></span>

### <span data-ttu-id="4e48a-124">-ConfigFile</span><span class="sxs-lookup"><span data-stu-id="4e48a-124">-ConfigFile</span></span>

<span data-ttu-id="4e48a-125">Hiermee geeft u een configuratie bestand op.</span><span class="sxs-lookup"><span data-stu-id="4e48a-125">Specifies a configuration file.</span></span>

```yaml
Type: System.String
Parameter Sets: NuGet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="4e48a-126">-Force</span><span class="sxs-lookup"><span data-stu-id="4e48a-126">-Force</span></span>

<span data-ttu-id="4e48a-127">Hiermee wordt de opdracht uitgevoerd zonder dat de gebruiker om bevestiging wordt gevraagd.</span><span class="sxs-lookup"><span data-stu-id="4e48a-127">Forces the command to run without asking for user confirmation.</span></span>

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

### <span data-ttu-id="4e48a-128">-ForceBootstrap</span><span class="sxs-lookup"><span data-stu-id="4e48a-128">-ForceBootstrap</span></span>

<span data-ttu-id="4e48a-129">Geeft aan dat met deze cmdlet **Package Management** automatisch een pakket provider moet worden geïnstalleerd.</span><span class="sxs-lookup"><span data-stu-id="4e48a-129">Indicates that this cmdlet forces **PackageManagement** to automatically install a package provider.</span></span>

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

### <span data-ttu-id="4e48a-130">-Locatie</span><span class="sxs-lookup"><span data-stu-id="4e48a-130">-Location</span></span>

<span data-ttu-id="4e48a-131">Hiermee geeft u de locatie van een pakket beheer bron of opslag plaats.</span><span class="sxs-lookup"><span data-stu-id="4e48a-131">Specifies the location of a package management source or repository.</span></span>

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

### <span data-ttu-id="4e48a-132">-Name</span><span class="sxs-lookup"><span data-stu-id="4e48a-132">-Name</span></span>

<span data-ttu-id="4e48a-133">Hiermee geeft u de naam van een pakket beheer bron op.</span><span class="sxs-lookup"><span data-stu-id="4e48a-133">Specifies the name of a package management source.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="4e48a-134">-PackageManagementProvider</span><span class="sxs-lookup"><span data-stu-id="4e48a-134">-PackageManagementProvider</span></span>

<span data-ttu-id="4e48a-135">Hiermee geeft u een pakket beheer provider.</span><span class="sxs-lookup"><span data-stu-id="4e48a-135">Specifies a package management provider.</span></span>

```yaml
Type: System.String
Parameter Sets: PowerShellGet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="4e48a-136">-ProviderName</span><span class="sxs-lookup"><span data-stu-id="4e48a-136">-ProviderName</span></span>

<span data-ttu-id="4e48a-137">Hiermee geeft u een of meer pakket provider namen op.</span><span class="sxs-lookup"><span data-stu-id="4e48a-137">Specifies one or more package provider names.</span></span> <span data-ttu-id="4e48a-138">Scheid meerdere pakket provider namen met komma's.</span><span class="sxs-lookup"><span data-stu-id="4e48a-138">Separate multiple package provider names with commas.</span></span>
<span data-ttu-id="4e48a-139">Gebruiken `Get-PackageProvider` om een lijst met beschik bare pakket providers op te halen.</span><span class="sxs-lookup"><span data-stu-id="4e48a-139">Use `Get-PackageProvider` to get a list of available package providers.</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases: Provider
Accepted values: Bootstrap, NuGet, PowerShellGet

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="4e48a-140">-PublishLocation</span><span class="sxs-lookup"><span data-stu-id="4e48a-140">-PublishLocation</span></span>

<span data-ttu-id="4e48a-141">Hiermee geeft u de publicatie locatie voor de pakket bron op.</span><span class="sxs-lookup"><span data-stu-id="4e48a-141">Specifies the publish location for the package source.</span></span>

```yaml
Type: System.String
Parameter Sets: PowerShellGet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="4e48a-142">-ScriptPublishLocation</span><span class="sxs-lookup"><span data-stu-id="4e48a-142">-ScriptPublishLocation</span></span>

<span data-ttu-id="4e48a-143">Hiermee geeft u de publicatie locatie van het script op.</span><span class="sxs-lookup"><span data-stu-id="4e48a-143">Specifies the script publish location.</span></span>

```yaml
Type: System.String
Parameter Sets: PowerShellGet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="4e48a-144">-ScriptSourceLocation</span><span class="sxs-lookup"><span data-stu-id="4e48a-144">-ScriptSourceLocation</span></span>

<span data-ttu-id="4e48a-145">Hiermee geeft u de bron locatie van het script op.</span><span class="sxs-lookup"><span data-stu-id="4e48a-145">Specifies the script source location.</span></span>

```yaml
Type: System.String
Parameter Sets: PowerShellGet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="4e48a-146">-SkipValidate</span><span class="sxs-lookup"><span data-stu-id="4e48a-146">-SkipValidate</span></span>

<span data-ttu-id="4e48a-147">Switch waarmee de validatie van de referenties van een pakket bron wordt overgeslagen.</span><span class="sxs-lookup"><span data-stu-id="4e48a-147">Switch that skips validating the credentials of a package source.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: NuGet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="4e48a-148">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="4e48a-148">CommonParameters</span></span>

<span data-ttu-id="4e48a-149">Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="4e48a-149">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="4e48a-150">Zie [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="4e48a-150">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="4e48a-151">INVOER</span><span class="sxs-lookup"><span data-stu-id="4e48a-151">INPUTS</span></span>

## <span data-ttu-id="4e48a-152">UITVOER</span><span class="sxs-lookup"><span data-stu-id="4e48a-152">OUTPUTS</span></span>

### <span data-ttu-id="4e48a-153">PackageSource[]</span><span class="sxs-lookup"><span data-stu-id="4e48a-153">PackageSource[]</span></span>

<span data-ttu-id="4e48a-154">Hiermee geeft u een of meer pakket bronnen op.</span><span class="sxs-lookup"><span data-stu-id="4e48a-154">Specifies one or more package sources.</span></span>

## <span data-ttu-id="4e48a-155">OPMERKINGEN</span><span class="sxs-lookup"><span data-stu-id="4e48a-155">NOTES</span></span>

## <span data-ttu-id="4e48a-156">GERELATEERDE KOPPELINGEN</span><span class="sxs-lookup"><span data-stu-id="4e48a-156">RELATED LINKS</span></span>

[<span data-ttu-id="4e48a-157">about_PackageManagement</span><span class="sxs-lookup"><span data-stu-id="4e48a-157">about_PackageManagement</span></span>](../Microsoft.PowerShell.Core/About/about_PackageManagement.md)

[<span data-ttu-id="4e48a-158">Zoeken-pakket</span><span class="sxs-lookup"><span data-stu-id="4e48a-158">Find-Package</span></span>](Find-Package.md)

[<span data-ttu-id="4e48a-159">Get-Package</span><span class="sxs-lookup"><span data-stu-id="4e48a-159">Get-Package</span></span>](Get-Package.md)

[<span data-ttu-id="4e48a-160">Get-PackageProvider</span><span class="sxs-lookup"><span data-stu-id="4e48a-160">Get-PackageProvider</span></span>](Get-PackageProvider.md)

[<span data-ttu-id="4e48a-161">REGI ster-PackageSource</span><span class="sxs-lookup"><span data-stu-id="4e48a-161">Register-PackageSource</span></span>](Register-PackageSource.md)

[<span data-ttu-id="4e48a-162">Set-PackageSource</span><span class="sxs-lookup"><span data-stu-id="4e48a-162">Set-PackageSource</span></span>](Set-PackageSource.md)

[<span data-ttu-id="4e48a-163">Registratie ongedaan maken-PackageSource</span><span class="sxs-lookup"><span data-stu-id="4e48a-163">Unregister-PackageSource</span></span>](Unregister-PackageSource.md)

