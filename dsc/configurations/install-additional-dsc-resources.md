---
ms.date: 12/12/2018
keywords: DSC, powershell, resource, galerie, instellen
title: Installeren van extra DSC-Resources
ms.openlocfilehash: ecaf176230ccd934b57b1c27d72ff83e6ba906e9
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 02/03/2019
ms.locfileid: "55686381"
---
# <a name="install-additional-dsc-resources"></a><span data-ttu-id="e3328-103">Installeren van extra DSC-Resources</span><span class="sxs-lookup"><span data-stu-id="e3328-103">Install Additional DSC Resources</span></span>

<span data-ttu-id="e3328-104">PowerShell bevat verschillende Out-of-the-box-resources voor Desired State Configuration (DSC).</span><span class="sxs-lookup"><span data-stu-id="e3328-104">PowerShell includes several Out-of-the-box resources for Desired State Configuration (DSC).</span></span> <span data-ttu-id="e3328-105">De **PSDesiredStateConfiguration** -module bevat alle OOB DSC-resources beschikbaar is op uw specifieke exemplaar van PowerShell.</span><span class="sxs-lookup"><span data-stu-id="e3328-105">The **PSDesiredStateConfiguration** module contains all of the OOB DSC resources available on your specific instance of PowerShell.</span></span>

<span data-ttu-id="e3328-106">Dit is een overzicht van de OOB-resources dat is opgenomen in PowerShell 4.0 en een beschrijving van de mogelijkheden van de resource.</span><span class="sxs-lookup"><span data-stu-id="e3328-106">This is a list of the OOB resources included in PowerShell 4.0 and a description of the resource's capabilities.</span></span>

> [!NOTE]
> <span data-ttu-id="e3328-107">Dit is een onvolledige lijst, zoals het aantal resources OOB is toegenomen bij elke versie van PowerShell.</span><span class="sxs-lookup"><span data-stu-id="e3328-107">This is an incomplete list, as the number of OOB resources has grown with each version of PowerShell.</span></span>

|<span data-ttu-id="e3328-108">Informatiebron</span><span class="sxs-lookup"><span data-stu-id="e3328-108">Resource</span></span>  |<span data-ttu-id="e3328-109">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="e3328-109">Description</span></span>  |
|---------|---------|
|<span data-ttu-id="e3328-110">**File**</span><span class="sxs-lookup"><span data-stu-id="e3328-110">**File**</span></span>|<span data-ttu-id="e3328-111">Hiermee bepaalt u de status van bestanden en mappen.</span><span class="sxs-lookup"><span data-stu-id="e3328-111">Controls the state of files and directories.</span></span> <span data-ttu-id="e3328-112">Kopieert bestanden van een **bron** naar een **bestemming** en wordt deze bijgewerkt wanneer de **bron** wijzigingen door het vergelijken van datums, controlesommen en hashes.</span><span class="sxs-lookup"><span data-stu-id="e3328-112">Copies files from a **Source** to a **Destination** and updates them when the **Source** changes by comparing dates, checksums, and hashes.</span></span>|
|<span data-ttu-id="e3328-113">**Archiveren**</span><span class="sxs-lookup"><span data-stu-id="e3328-113">**Archive**</span></span>|<span data-ttu-id="e3328-114">Hiermee wordt de archieven en een opgegeven locatie.</span><span class="sxs-lookup"><span data-stu-id="e3328-114">Unpacks archives and a specified location.</span></span> <span data-ttu-id="e3328-115">Valideert de archieven met een opgegeven **controlesom**.</span><span class="sxs-lookup"><span data-stu-id="e3328-115">Validates the archives with a specified **Checksum**.</span></span>|
|<span data-ttu-id="e3328-116">**Omgeving**</span><span class="sxs-lookup"><span data-stu-id="e3328-116">**Environment**</span></span>|<span data-ttu-id="e3328-117">Hiermee beheert u omgevingsvariabelen.</span><span class="sxs-lookup"><span data-stu-id="e3328-117">Manages environment variables.</span></span>|
|<span data-ttu-id="e3328-118">**Groep**</span><span class="sxs-lookup"><span data-stu-id="e3328-118">**Group**</span></span>|<span data-ttu-id="e3328-119">Lokale groepen worden beheerd en besturingselementen van groepslidmaatschap.</span><span class="sxs-lookup"><span data-stu-id="e3328-119">Manages local groups and controls group membership.</span></span>|
|<span data-ttu-id="e3328-120">**Log**</span><span class="sxs-lookup"><span data-stu-id="e3328-120">**Log**</span></span>|<span data-ttu-id="e3328-121">Schrijft berichten naar de `Microsoft-Windows-Desired State Configuration/Analytic` gebeurtenislogboek.</span><span class="sxs-lookup"><span data-stu-id="e3328-121">Writes messages to the `Microsoft-Windows-Desired State Configuration/Analytic` event log.</span></span>|
|<span data-ttu-id="e3328-122">**Package**</span><span class="sxs-lookup"><span data-stu-id="e3328-122">**Package**</span></span>|<span data-ttu-id="e3328-123">Installeert of verwijdert met behulp van pakketten **argumenten**, **LogPath**, **ReturnCode**, andere instellingen.</span><span class="sxs-lookup"><span data-stu-id="e3328-123">Installs or uninstalls packages using **Arguments**, **LogPath**, **ReturnCode**, other settings.</span></span>|
|<span data-ttu-id="e3328-124">**Registry**</span><span class="sxs-lookup"><span data-stu-id="e3328-124">**Registry**</span></span>|<span data-ttu-id="e3328-125">Hiermee beheert u sleutels en waarden.</span><span class="sxs-lookup"><span data-stu-id="e3328-125">Manages registry keys and values.</span></span>|
|<span data-ttu-id="e3328-126">**Script**</span><span class="sxs-lookup"><span data-stu-id="e3328-126">**Script**</span></span>|<span data-ttu-id="e3328-127">U ontwerpt waarmee u uw eigen [get-test-set](../resources/get-test-set.md) scriptblokken.</span><span class="sxs-lookup"><span data-stu-id="e3328-127">Allows you to design your own [get-test-set](../resources/get-test-set.md) script blocks.</span></span>|
|<span data-ttu-id="e3328-128">**Service**</span><span class="sxs-lookup"><span data-stu-id="e3328-128">**Service**</span></span>|<span data-ttu-id="e3328-129">Hiermee configureert u Windows-services.</span><span class="sxs-lookup"><span data-stu-id="e3328-129">Configures Windows services.</span></span>|
|<span data-ttu-id="e3328-130">**User**</span><span class="sxs-lookup"><span data-stu-id="e3328-130">**User**</span></span> |<span data-ttu-id="e3328-131">Hiermee beheert u lokale gebruikers en -kenmerken.</span><span class="sxs-lookup"><span data-stu-id="e3328-131">Manages local users and attributes.</span></span>|
|<span data-ttu-id="e3328-132">**WindowsFeature**</span><span class="sxs-lookup"><span data-stu-id="e3328-132">**WindowsFeature**</span></span>|<span data-ttu-id="e3328-133">Hiermee beheert u functies en onderdelen.</span><span class="sxs-lookup"><span data-stu-id="e3328-133">Manages roles and features.</span></span>|
|<span data-ttu-id="e3328-134">**WindowsProcess**</span><span class="sxs-lookup"><span data-stu-id="e3328-134">**WindowsProcess**</span></span>|<span data-ttu-id="e3328-135">Hiermee configureert u Windows-processen.</span><span class="sxs-lookup"><span data-stu-id="e3328-135">Configures Windows processes.</span></span>|

<span data-ttu-id="e3328-136">De OOB-resources kunnen een goed uitgangspunt voor algemene bewerkingen.</span><span class="sxs-lookup"><span data-stu-id="e3328-136">The OOB resources allow a good starting point for common operations.</span></span> <span data-ttu-id="e3328-137">Als de OOB-resources niet voldoen aan uw behoeften, kunt u uw eigen [aangepaste Resource](../resources/authoringResource.md).</span><span class="sxs-lookup"><span data-stu-id="e3328-137">If the OOB resources do not meet your needs, you can write your own [Custom Resource](../resources/authoringResource.md).</span></span> <span data-ttu-id="e3328-138">Voordat u schrijft een aangepaste bron uit voor het probleem kunt oplossen, moet u zoeken door het grote aantal van de DSC-resources die al zijn gemaakt door zowel Microsoft als de PowerShell-community.</span><span class="sxs-lookup"><span data-stu-id="e3328-138">Before you write a custom resource to solve your problem, you should look through the vast number of DSC resources that have already been created by both Microsoft and the PowerShell community.</span></span>

<span data-ttu-id="e3328-139">U kunt DSC-resources zoeken in zowel de [PowerShell Gallery](https://www.powershellgallery.com/) en [GitHub](https://github.com/).</span><span class="sxs-lookup"><span data-stu-id="e3328-139">You can find DSC resources in both the [PowerShell Gallery](https://www.powershellgallery.com/) and [GitHub](https://github.com/).</span></span> <span data-ttu-id="e3328-140">U kunt ook DSC-resources rechtstreeks vanuit de PowerShell-console via installeren [PowerShellGet](/powershell/module/powershellget/).</span><span class="sxs-lookup"><span data-stu-id="e3328-140">You can also install DSC resources directly from the PowerShell console using [PowerShellGet](/powershell/module/powershellget/).</span></span>

## <a name="installing-powershellget"></a><span data-ttu-id="e3328-141">PowerShellGet installeren</span><span class="sxs-lookup"><span data-stu-id="e3328-141">Installing PowerShellGet</span></span>

<span data-ttu-id="e3328-142">Om te bepalen of u al hebt **PowerShell** ophalen of hulp bij het installeren, Zie de volgende handleiding: [PowerShellGet installeren](/powershell/gallery/installing-psget).</span><span class="sxs-lookup"><span data-stu-id="e3328-142">To determine if you already have **PowerShell** get, or to get help installing it, see the following guide: [Installing PowerShellGet](/powershell/gallery/installing-psget).</span></span>

## <a name="finding-dsc-resources-using-powershellget"></a><span data-ttu-id="e3328-143">DSC-resources met behulp van PowerShellGet zoeken</span><span class="sxs-lookup"><span data-stu-id="e3328-143">Finding DSC resources using PowerShellGet</span></span>

<span data-ttu-id="e3328-144">Eenmaal **PowerShellGet** is geïnstalleerd op uw systeem, kunt u zoeken en installeren van de DSC-resources die worden gehost de [PowerShell Gallery](https://www.powershellgallery.com/).</span><span class="sxs-lookup"><span data-stu-id="e3328-144">Once **PowerShellGet** is installed on your system, you can find and install DSC resources hosted in the [PowerShell Gallery](https://www.powershellgallery.com/).</span></span>

<span data-ttu-id="e3328-145">Gebruik eerst de [sleutelwoorden zoeken-dscresource bieden](/powershell/module/powershellget/find-dscresource) cmdlet DSC-resources vinden.</span><span class="sxs-lookup"><span data-stu-id="e3328-145">First, use the [Find-DSCResource](/powershell/module/powershellget/find-dscresource) cmdlet to find DSC resources.</span></span> <span data-ttu-id="e3328-146">Bij het uitvoeren van `Find-DSCResource` voor het eerst, ziet u het volgende bericht voor het installeren van de 'NuGet-provider'.</span><span class="sxs-lookup"><span data-stu-id="e3328-146">When you run `Find-DSCResource` for the first time, you see the following prompt to install the "NuGet provider".</span></span>

```
PS> Find-DSCResource

NuGet provider is required to continue
PowerShellGet requires NuGet provider version '2.8.5.201' or newer to interact with NuGet-based repositories. The
NuGet provider must be available in 'C:\Program Files\PackageManagement\ProviderAssemblies' or
'C:\Users\xAdministrator\AppData\Local\PackageManagement\ProviderAssemblies'. You can also install the NuGet provider
 by running 'Install-PackageProvider -Name NuGet -MinimumVersion 2.8.5.201 -Force'. Do you want PowerShellGet to
install and import the NuGet provider now?
[Y] Yes  [N] No  [?] Help (default is "Y"):
```

<span data-ttu-id="e3328-147">Nadat te drukken "y", de 'NuGet'-provider is geïnstalleerd, ziet u een lijst van DSC-resources die u vanuit de PowerShell Gallery installeren kunt.</span><span class="sxs-lookup"><span data-stu-id="e3328-147">After pressing 'y', the "NuGet" provider is installed, you see a list of DSC resources that you can install from the PowerShell Gallery.</span></span>

> [!NOTE]
> <span data-ttu-id="e3328-148">Lijst wordt niet weergegeven omdat het erg groot is.</span><span class="sxs-lookup"><span data-stu-id="e3328-148">List is not shown because it is very large.</span></span>

<span data-ttu-id="e3328-149">U kunt ook opgeven de `-Name` met jokertekens, parameter of `-Filter` parameter zonder jokertekens aan uw zoekopdracht verfijnen.</span><span class="sxs-lookup"><span data-stu-id="e3328-149">You can also specify the `-Name` parameter using wildcards, or `-Filter` parameter without wildcards to narrow down your search.</span></span> <span data-ttu-id="e3328-150">In dit voorbeeld wordt gezocht naar een "Tijdzone" DSC-resource met behulp van de jokertekens.</span><span class="sxs-lookup"><span data-stu-id="e3328-150">This example attempts to find a "TimeZone" DSC resource using the wildcards.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="e3328-151">Er is momenteel een bug in de `Find-DSCResource` cmdlet waarmee wordt voorkomen dat het gebruik van jokertekens in zowel de `-Name` en `-Filter` parameters.</span><span class="sxs-lookup"><span data-stu-id="e3328-151">Currently there is a bug in the `Find-DSCResource` cmdlet that prevents using wildcards in both the `-Name` and `-Filter` parameters.</span></span> <span data-ttu-id="e3328-152">Het tweede voorbeeld hieronder ziet u een tijdelijke oplossing met `Where-Object`.</span><span class="sxs-lookup"><span data-stu-id="e3328-152">The second example below shows a workaround using `Where-Object`.</span></span>

```
PS> Find-DSCResource -Name *Time*

Name                                Version    ModuleName                          Repository
----                                -------    ----------                          ----------
Carbon_EnvironmentVariable          2.6.0      Carbon                              PSGallery
Carbon_FirewallRule                 2.6.0      Carbon                              PSGallery
Carbon_Group                        2.6.0      Carbon                              PSGallery
Carbon_IniFile                      2.6.0      Carbon                              PSGallery
Carbon_Permission                   2.6.0      Carbon                              PSGallery
Carbon_Privilege                    2.6.0      Carbon                              PSGallery
Carbon_ScheduledTask                2.6.0      Carbon                              PSGallery
Carbon_Service                      2.6.0      Carbon                              PSGallery
TimeZone                            6.0.0.0    ComputerManagementDsc               PSGallery
xTimeZone                           1.8.0.0    xTimeZone                           PSGallery
xSqlServerDefaultDir                1.0.0      mlSqlServerDSC                      PSGallery
xSqlServerMoveDatabaseFiles         1.0.0      mlSqlServerDSC                      PSGallery
xSqlServerSQLDataRoot               1.0.0      mlSqlServerDSC                      PSGallery
xSqlServerStartupParam              1.0.0      mlSqlServerDSC                      PSGallery
```

<span data-ttu-id="e3328-153">U kunt ook `Where-Object` DSC-resources met gedetailleerdere filteren vinden.</span><span class="sxs-lookup"><span data-stu-id="e3328-153">You can also use `Where-Object` to find DSC resources with more granular filtering.</span></span> <span data-ttu-id="e3328-154">Deze aanpak is langzamer dan het gebruik van ingebouwde parameters filteren.</span><span class="sxs-lookup"><span data-stu-id="e3328-154">This approach will be slower than using built in filtering parameters.</span></span>

```
PS> Find-DSCResource | Where-Object {$_.Name -like "Time*"}

Name                                Version    ModuleName                          Repository
----                                -------    ----------                          ----------
TimeZone                            6.0.0.0    ComputerManagementDsc               PSGallery
```

<span data-ttu-id="e3328-155">Zie voor meer informatie over het filteren van [Where-Object](/powershell/module/microsoft.powershell.core/where-object).</span><span class="sxs-lookup"><span data-stu-id="e3328-155">For more information on filtering, see [Where-Object](/powershell/module/microsoft.powershell.core/where-object).</span></span>

## <a name="installing-dsc-resources-using-powershellget"></a><span data-ttu-id="e3328-156">DSC-Resources met behulp van PowerShellGet installeren</span><span class="sxs-lookup"><span data-stu-id="e3328-156">Installing DSC Resources using PowerShellGet</span></span>

<span data-ttu-id="e3328-157">Voor het installeren van een DSC-resource, gebruikt u de [Install-Module](/powershell/module/PowershellGet/Install-Module) cmdlet, op te geven de naam van de module die wordt weergegeven onder **Module** naam in de lijst met zoekresultaten.</span><span class="sxs-lookup"><span data-stu-id="e3328-157">To install a DSC resource, use the [Install-Module](/powershell/module/PowershellGet/Install-Module) cmdlet, specifying the name of the module shown under **Module** name in your search results.</span></span>

<span data-ttu-id="e3328-158">De resource "Tijdzone" bestaat dus dat wil zeggen dat de module in dit voorbeeld wordt geïnstalleerd in de module 'ComputerManagementDSC'.</span><span class="sxs-lookup"><span data-stu-id="e3328-158">The "TimeZone" resource exists in the "ComputerManagementDSC" module, so that is the module this example installs.</span></span>

> [!NOTE]
> <span data-ttu-id="e3328-159">Als u hebt de PowerShell gallery niet wordt vertrouwd, ziet u de waarschuwing onder dat om bevestiging wordt gevraagd en dat u hoe u om te voorkomen dat verdere aanwijzingen op geïnstalleerd.</span><span class="sxs-lookup"><span data-stu-id="e3328-159">If you have not trusted the PowerShell gallery, you see the warning below asking for confirmation, and instructing you how to avoid subsequent prompts on installs.</span></span>

```
PS> Install-Module -Name ComputerManagementDSC

Untrusted repository
You are installing the modules from an untrusted repository. If you trust this repository, change its
InstallationPolicy value by running the Set-PSRepository cmdlet. Are you sure you want to install the modules from
'PSGallery'?
[Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "N"):
```

<span data-ttu-id="e3328-160">Druk op 'y' om door te gaan met het installeren van de module.</span><span class="sxs-lookup"><span data-stu-id="e3328-160">Press 'y' to continue installing the module.</span></span> <span data-ttu-id="e3328-161">Na de installatie, kunt u controleren of uw nieuwe resource is geïnstalleerd met behulp van [sleutelwoorden Get-dscresource bieden](/powershell/module/PSDesiredStateConfiguration/Get-DscResource).</span><span class="sxs-lookup"><span data-stu-id="e3328-161">After install, you can verify that your new resource is installed using [Get-DSCResource](/powershell/module/PSDesiredStateConfiguration/Get-DscResource).</span></span>

```
PS> Get-DSCResource -Name TimeZone -Syntax

TimeZone [String] #ResourceName
{
    IsSingleInstance = [string]{ Yes }
    TimeZone = [string]
    [DependsOn = [string[]]]
    [PsDscRunAsCredential = [PSCredential]]
}
```

<span data-ttu-id="e3328-162">U kunt ook andere resources in uw geïnstalleerde module weergeven door op te geven de `-ModuleName` parameter.</span><span class="sxs-lookup"><span data-stu-id="e3328-162">You can also view other resources in your newly installed module, by specifying the `-ModuleName` parameter.</span></span>

```
PS> Get-DSCResource -Module ComputerManagementDSC

ImplementedAs   Name                      ModuleName                     Version    Properties
-------------   ----                      ----------                     -------    ----------
PowerShell      Computer                  ComputerManagementDsc          6.0.0.0    {Name, Credential, DependsOn, ...
PowerShell      OfflineDomainJoin         ComputerManagementDsc          6.0.0.0    {IsSingleInstance, RequestFile...
PowerShell      PowerPlan                 ComputerManagementDsc          6.0.0.0    {IsSingleInstance, Name, Depen...
PowerShell      PowerShellExecutionPolicy ComputerManagementDsc          6.0.0.0    {ExecutionPolicy, ExecutionPol...
PowerShell      ScheduledTask             ComputerManagementDsc          6.0.0.0    {TaskName, ActionArguments, Ac...
PowerShell      TimeZone                  ComputerManagementDsc          6.0.0.0    {IsSingleInstance, TimeZone, D...
PowerShell      VirtualMemory             ComputerManagementDsc          6.0.0.0    {Drive, Type, DependsOn, Initi...
```

## <a name="see-also"></a><span data-ttu-id="e3328-163">Zie ook</span><span class="sxs-lookup"><span data-stu-id="e3328-163">See also</span></span>

- [<span data-ttu-id="e3328-164">Wat zijn Resources?</span><span class="sxs-lookup"><span data-stu-id="e3328-164">What are Resources?</span></span>](../resources/resources.md)
