---
external help file: Microsoft.PowerShell.PackageManagement.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: PackageManagement
ms.date: 03/29/2019
online version: https://docs.microsoft.com/powershell/module/packagemanagement/get-packagesource?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-PackageSource
ms.openlocfilehash: 8428f51c27cf52a7e0910a7b6c759e1f75b89339
ms.sourcegitcommit: 22c93550c87af30c4895fcb9e9dd65e30d60ada0
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 11/19/2020
ms.locfileid: "94890110"
---
# <span data-ttu-id="2bf88-103">Get-PackageSource</span><span class="sxs-lookup"><span data-stu-id="2bf88-103">Get-PackageSource</span></span>

## <span data-ttu-id="2bf88-104">SAMENVATTING</span><span class="sxs-lookup"><span data-stu-id="2bf88-104">SYNOPSIS</span></span>
<span data-ttu-id="2bf88-105">Hiermee wordt een lijst opgehaald met pakket bronnen die zijn geregistreerd voor een pakket provider.</span><span class="sxs-lookup"><span data-stu-id="2bf88-105">Gets a list of package sources that are registered for a package provider.</span></span>

## <span data-ttu-id="2bf88-106">SYNTAXIS</span><span class="sxs-lookup"><span data-stu-id="2bf88-106">SYNTAX</span></span>

### <span data-ttu-id="2bf88-107">NuGet</span><span class="sxs-lookup"><span data-stu-id="2bf88-107">NuGet</span></span>

```
Get-PackageSource [[-Name] <String>] [-Location <String>] [-Force] [-ForceBootstrap]
 [-ProviderName <String[]>] [-ConfigFile <String>] [-SkipValidate] [<CommonParameters>]
```

### <span data-ttu-id="2bf88-108">PowerShellGet</span><span class="sxs-lookup"><span data-stu-id="2bf88-108">PowerShellGet</span></span>

```
Get-PackageSource [[-Name] <String>] [-Location <String>] [-Force] [-ForceBootstrap]
 [-ProviderName <String[]>] [-PackageManagementProvider <String>] [-PublishLocation <String>]
 [-ScriptSourceLocation <String>] [-ScriptPublishLocation <String>] [<CommonParameters>]
```

## <span data-ttu-id="2bf88-109">BESCHRIJVING</span><span class="sxs-lookup"><span data-stu-id="2bf88-109">DESCRIPTION</span></span>

<span data-ttu-id="2bf88-110">De `Get-PackageSource` cmdlet haalt een lijst op met pakket bronnen die zijn geregistreerd bij **Package Management** op de lokale computer.</span><span class="sxs-lookup"><span data-stu-id="2bf88-110">The `Get-PackageSource` cmdlet gets a list of package sources that are registered with **PackageManagement** on the local computer.</span></span> <span data-ttu-id="2bf88-111">Als u een pakket provider opgeeft, `Get-PackageSource` worden alleen de bronnen opgehaald die aan de opgegeven provider zijn gekoppeld.</span><span class="sxs-lookup"><span data-stu-id="2bf88-111">If you specify a package provider, `Get-PackageSource` gets only those sources that are associated with the specified provider.</span></span> <span data-ttu-id="2bf88-112">Anders retourneert de opdracht alle pakket bronnen die zijn geregistreerd bij **Package Management**.</span><span class="sxs-lookup"><span data-stu-id="2bf88-112">Otherwise, the command returns all package sources that are registered with **PackageManagement**.</span></span>

## <span data-ttu-id="2bf88-113">VOORBEELDEN</span><span class="sxs-lookup"><span data-stu-id="2bf88-113">EXAMPLES</span></span>

### <span data-ttu-id="2bf88-114">Voor beeld 1: alle pakket bronnen ophalen</span><span class="sxs-lookup"><span data-stu-id="2bf88-114">Example 1: Get all package sources</span></span>

<span data-ttu-id="2bf88-115">De `Get-PackageSource` cmdlet haalt alle pakket bronnen op die zijn geregistreerd bij **Package Management** op de lokale computer.</span><span class="sxs-lookup"><span data-stu-id="2bf88-115">The `Get-PackageSource` cmdlet gets all package sources that are registered with **PackageManagement** on the local computer.</span></span>

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

### <span data-ttu-id="2bf88-116">Voor beeld 2: alle pakket bronnen voor een specifieke provider ophalen</span><span class="sxs-lookup"><span data-stu-id="2bf88-116">Example 2: Get all package sources for a specific provider</span></span>

<span data-ttu-id="2bf88-117">Met deze opdracht worden pakket bronnen opgehaald die zijn geregistreerd voor een specifieke provider.</span><span class="sxs-lookup"><span data-stu-id="2bf88-117">This command gets package sources that are registered for a specific provider.</span></span>

```powershell
Get-PackageSource -ProviderName NuGet
```

```Output
Name                 ProviderName     IsTrusted  Location
----                 ------------     ---------  --------
LocalPackages        NuGet            False      C:\LocalPkg\
MyNuget              NuGet            False      https://www.nuget.org/api/v2
```

<span data-ttu-id="2bf88-118">`Get-PackageSource` maakt gebruik van de para meter **ProviderName** om pakket bronnen op te halen die zijn geregistreerd voor de **NuGet** -provider.</span><span class="sxs-lookup"><span data-stu-id="2bf88-118">`Get-PackageSource` uses the **ProviderName** parameter to get package sources that are registered for the **NuGet** provider.</span></span>

### <span data-ttu-id="2bf88-119">Voor beeld 3: bronnen van een pakket provider ophalen</span><span class="sxs-lookup"><span data-stu-id="2bf88-119">Example 3: Get sources from a package provider</span></span>

<span data-ttu-id="2bf88-120">Met deze opdracht wordt een pakket provider gebruikt om pakket bronnen op te halen.</span><span class="sxs-lookup"><span data-stu-id="2bf88-120">This command uses a package provider to get package sources.</span></span>

```powershell
Get-PackageProvider -Name NuGet | Get-PackageSource
```

```Output
Name                 ProviderName     IsTrusted  Location
----                 ------------     ---------  --------
LocalPackages        NuGet            False      C:\LocalPkg\
MyNuget              NuGet            False      https://www.nuget.org/api/v2
```

<span data-ttu-id="2bf88-121">`Get-PackageProvider` Hiermee gebruikt u de para meter **name** om de naam van de provider op te geven, **NuGet**.</span><span class="sxs-lookup"><span data-stu-id="2bf88-121">`Get-PackageProvider` uses the **Name** parameter specify the provider name, **NuGet**.</span></span> <span data-ttu-id="2bf88-122">Het object wordt naar de pijp lijn verzonden `Get-PackageSource` .</span><span class="sxs-lookup"><span data-stu-id="2bf88-122">The object is sent down the pipeline to `Get-PackageSource`.</span></span>

## <span data-ttu-id="2bf88-123">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="2bf88-123">PARAMETERS</span></span>

### <span data-ttu-id="2bf88-124">-ConfigFile</span><span class="sxs-lookup"><span data-stu-id="2bf88-124">-ConfigFile</span></span>

<span data-ttu-id="2bf88-125">Hiermee geeft u een configuratie bestand op.</span><span class="sxs-lookup"><span data-stu-id="2bf88-125">Specifies a configuration file.</span></span>

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

### <span data-ttu-id="2bf88-126">-Force</span><span class="sxs-lookup"><span data-stu-id="2bf88-126">-Force</span></span>

<span data-ttu-id="2bf88-127">Hiermee wordt de opdracht uitgevoerd zonder dat de gebruiker om bevestiging wordt gevraagd.</span><span class="sxs-lookup"><span data-stu-id="2bf88-127">Forces the command to run without asking for user confirmation.</span></span>

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

### <span data-ttu-id="2bf88-128">-ForceBootstrap</span><span class="sxs-lookup"><span data-stu-id="2bf88-128">-ForceBootstrap</span></span>

<span data-ttu-id="2bf88-129">Geeft aan dat met deze cmdlet **Package Management** automatisch een pakket provider moet worden geïnstalleerd.</span><span class="sxs-lookup"><span data-stu-id="2bf88-129">Indicates that this cmdlet forces **PackageManagement** to automatically install a package provider.</span></span>

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

### <span data-ttu-id="2bf88-130">-Locatie</span><span class="sxs-lookup"><span data-stu-id="2bf88-130">-Location</span></span>

<span data-ttu-id="2bf88-131">Hiermee geeft u de locatie van een pakket beheer bron of opslag plaats.</span><span class="sxs-lookup"><span data-stu-id="2bf88-131">Specifies the location of a package management source or repository.</span></span>

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

### <span data-ttu-id="2bf88-132">-Name</span><span class="sxs-lookup"><span data-stu-id="2bf88-132">-Name</span></span>

<span data-ttu-id="2bf88-133">Hiermee geeft u de naam van een pakket beheer bron op.</span><span class="sxs-lookup"><span data-stu-id="2bf88-133">Specifies the name of a package management source.</span></span>

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

### <span data-ttu-id="2bf88-134">-PackageManagementProvider</span><span class="sxs-lookup"><span data-stu-id="2bf88-134">-PackageManagementProvider</span></span>

<span data-ttu-id="2bf88-135">Hiermee geeft u een pakket beheer provider.</span><span class="sxs-lookup"><span data-stu-id="2bf88-135">Specifies a package management provider.</span></span>

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

### <span data-ttu-id="2bf88-136">-ProviderName</span><span class="sxs-lookup"><span data-stu-id="2bf88-136">-ProviderName</span></span>

<span data-ttu-id="2bf88-137">Hiermee geeft u een of meer pakket provider namen op.</span><span class="sxs-lookup"><span data-stu-id="2bf88-137">Specifies one or more package provider names.</span></span> <span data-ttu-id="2bf88-138">Scheid meerdere pakket provider namen met komma's.</span><span class="sxs-lookup"><span data-stu-id="2bf88-138">Separate multiple package provider names with commas.</span></span>
<span data-ttu-id="2bf88-139">Gebruiken `Get-PackageProvider` om een lijst met beschik bare pakket providers op te halen.</span><span class="sxs-lookup"><span data-stu-id="2bf88-139">Use `Get-PackageProvider` to get a list of available package providers.</span></span>

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

### <span data-ttu-id="2bf88-140">-PublishLocation</span><span class="sxs-lookup"><span data-stu-id="2bf88-140">-PublishLocation</span></span>

<span data-ttu-id="2bf88-141">Hiermee geeft u de publicatie locatie voor de pakket bron op.</span><span class="sxs-lookup"><span data-stu-id="2bf88-141">Specifies the publish location for the package source.</span></span>

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

### <span data-ttu-id="2bf88-142">-ScriptPublishLocation</span><span class="sxs-lookup"><span data-stu-id="2bf88-142">-ScriptPublishLocation</span></span>

<span data-ttu-id="2bf88-143">Hiermee geeft u de publicatie locatie van het script op.</span><span class="sxs-lookup"><span data-stu-id="2bf88-143">Specifies the script publish location.</span></span>

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

### <span data-ttu-id="2bf88-144">-ScriptSourceLocation</span><span class="sxs-lookup"><span data-stu-id="2bf88-144">-ScriptSourceLocation</span></span>

<span data-ttu-id="2bf88-145">Hiermee geeft u de bron locatie van het script op.</span><span class="sxs-lookup"><span data-stu-id="2bf88-145">Specifies the script source location.</span></span>

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

### <span data-ttu-id="2bf88-146">-SkipValidate</span><span class="sxs-lookup"><span data-stu-id="2bf88-146">-SkipValidate</span></span>

<span data-ttu-id="2bf88-147">Switch waarmee de validatie van de referenties van een pakket bron wordt overgeslagen.</span><span class="sxs-lookup"><span data-stu-id="2bf88-147">Switch that skips validating the credentials of a package source.</span></span>

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

### <span data-ttu-id="2bf88-148">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="2bf88-148">CommonParameters</span></span>

<span data-ttu-id="2bf88-149">Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="2bf88-149">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="2bf88-150">Zie [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="2bf88-150">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="2bf88-151">INVOER</span><span class="sxs-lookup"><span data-stu-id="2bf88-151">INPUTS</span></span>

## <span data-ttu-id="2bf88-152">UITVOER</span><span class="sxs-lookup"><span data-stu-id="2bf88-152">OUTPUTS</span></span>

### <span data-ttu-id="2bf88-153">PackageSource[]</span><span class="sxs-lookup"><span data-stu-id="2bf88-153">PackageSource[]</span></span>

<span data-ttu-id="2bf88-154">Hiermee geeft u een of meer pakket bronnen op.</span><span class="sxs-lookup"><span data-stu-id="2bf88-154">Specifies one or more package sources.</span></span>

## <span data-ttu-id="2bf88-155">OPMERKINGEN</span><span class="sxs-lookup"><span data-stu-id="2bf88-155">NOTES</span></span>

> [!IMPORTANT]
> <span data-ttu-id="2bf88-156">Vanaf april 2020 biedt de PowerShell Gallery niet langer ondersteuning voor Transport Layer Security (TLS) versie 1,0 en 1,1.</span><span class="sxs-lookup"><span data-stu-id="2bf88-156">As of April 2020, the PowerShell Gallery no longer supports Transport Layer Security (TLS) versions 1.0 and 1.1.</span></span> <span data-ttu-id="2bf88-157">Als u geen TLS 1,2 of hoger gebruikt, wordt er een fout bericht weer gegeven wanneer u probeert toegang te krijgen tot de PowerShell Gallery.</span><span class="sxs-lookup"><span data-stu-id="2bf88-157">If you are not using TLS 1.2 or higher, you will receive an error when trying to access the PowerShell Gallery.</span></span> <span data-ttu-id="2bf88-158">Gebruik de volgende opdracht om ervoor te zorgen dat u TLS 1,2 gebruikt:</span><span class="sxs-lookup"><span data-stu-id="2bf88-158">Use the following command to ensure you are using TLS 1.2:</span></span>
>
> `[Net.ServicePointManager]::SecurityProtocol = [Net.SecurityProtocolType]::Tls12`
>
> <span data-ttu-id="2bf88-159">Zie de [aankondiging](https://devblogs.microsoft.com/powershell/powershell-gallery-tls-support/) in het Power shell-blog voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="2bf88-159">For more information, see the [announcement](https://devblogs.microsoft.com/powershell/powershell-gallery-tls-support/) in the PowerShell blog.</span></span>

## <span data-ttu-id="2bf88-160">GERELATEERDE KOPPELINGEN</span><span class="sxs-lookup"><span data-stu-id="2bf88-160">RELATED LINKS</span></span>

[<span data-ttu-id="2bf88-161">about_PackageManagement</span><span class="sxs-lookup"><span data-stu-id="2bf88-161">about_PackageManagement</span></span>](../Microsoft.PowerShell.Core/About/about_PackageManagement.md)

[<span data-ttu-id="2bf88-162">Zoeken-pakket</span><span class="sxs-lookup"><span data-stu-id="2bf88-162">Find-Package</span></span>](Find-Package.md)

[<span data-ttu-id="2bf88-163">Get-Package</span><span class="sxs-lookup"><span data-stu-id="2bf88-163">Get-Package</span></span>](Get-Package.md)

[<span data-ttu-id="2bf88-164">Get-PackageProvider</span><span class="sxs-lookup"><span data-stu-id="2bf88-164">Get-PackageProvider</span></span>](Get-PackageProvider.md)

[<span data-ttu-id="2bf88-165">REGI ster-PackageSource</span><span class="sxs-lookup"><span data-stu-id="2bf88-165">Register-PackageSource</span></span>](Register-PackageSource.md)

[<span data-ttu-id="2bf88-166">Set-PackageSource</span><span class="sxs-lookup"><span data-stu-id="2bf88-166">Set-PackageSource</span></span>](Set-PackageSource.md)

[<span data-ttu-id="2bf88-167">Registratie ongedaan maken-PackageSource</span><span class="sxs-lookup"><span data-stu-id="2bf88-167">Unregister-PackageSource</span></span>](Unregister-PackageSource.md)
