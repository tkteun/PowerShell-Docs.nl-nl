---
ms.date: 12/12/2018
keywords: DSC, Power shell, resource, Galerie, Setup
title: Aanvullende DSC-resources installeren
ms.openlocfilehash: ecaf176230ccd934b57b1c27d72ff83e6ba906e9
ms.sourcegitcommit: 18985d07ef024378c8590dc7a983099ff9225672
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/04/2019
ms.locfileid: "71942319"
---
# <a name="install-additional-dsc-resources"></a><span data-ttu-id="5ff45-103">Aanvullende DSC-resources installeren</span><span class="sxs-lookup"><span data-stu-id="5ff45-103">Install Additional DSC Resources</span></span>

<span data-ttu-id="5ff45-104">Power shell bevat verschillende out-of-the-box bronnen voor desired state Configuration (DSC).</span><span class="sxs-lookup"><span data-stu-id="5ff45-104">PowerShell includes several Out-of-the-box resources for Desired State Configuration (DSC).</span></span> <span data-ttu-id="5ff45-105">De **PSDesiredStateConfiguration** -module bevat alle OOB DSC-resources die beschikbaar zijn op uw specifieke instantie van Power shell.</span><span class="sxs-lookup"><span data-stu-id="5ff45-105">The **PSDesiredStateConfiguration** module contains all of the OOB DSC resources available on your specific instance of PowerShell.</span></span>

<span data-ttu-id="5ff45-106">Dit is een lijst met de OOB-resources die zijn opgenomen in Power Shell 4,0 en een beschrijving van de mogelijkheden van de resource.</span><span class="sxs-lookup"><span data-stu-id="5ff45-106">This is a list of the OOB resources included in PowerShell 4.0 and a description of the resource's capabilities.</span></span>

> [!NOTE]
> <span data-ttu-id="5ff45-107">Dit is een onvolledige lijst, omdat het aantal OOB-resources is toegenomen met elke versie van Power shell.</span><span class="sxs-lookup"><span data-stu-id="5ff45-107">This is an incomplete list, as the number of OOB resources has grown with each version of PowerShell.</span></span>

|<span data-ttu-id="5ff45-108">Resource</span><span class="sxs-lookup"><span data-stu-id="5ff45-108">Resource</span></span>  |<span data-ttu-id="5ff45-109">Description</span><span class="sxs-lookup"><span data-stu-id="5ff45-109">Description</span></span>  |
|---------|---------|
|<span data-ttu-id="5ff45-110">**File**</span><span class="sxs-lookup"><span data-stu-id="5ff45-110">**File**</span></span>|<span data-ttu-id="5ff45-111">Hiermee bepaalt u de status van bestanden en mappen.</span><span class="sxs-lookup"><span data-stu-id="5ff45-111">Controls the state of files and directories.</span></span> <span data-ttu-id="5ff45-112">Kopieert bestanden van een **bron** naar een **doel** en werkt deze bij wanneer de **bron** wordt gewijzigd door datums, controle sommen en hashes te vergelijken.</span><span class="sxs-lookup"><span data-stu-id="5ff45-112">Copies files from a **Source** to a **Destination** and updates them when the **Source** changes by comparing dates, checksums, and hashes.</span></span>|
|<span data-ttu-id="5ff45-113">**Archief**</span><span class="sxs-lookup"><span data-stu-id="5ff45-113">**Archive**</span></span>|<span data-ttu-id="5ff45-114">De archieven en een opgegeven locatie worden uitgepakt.</span><span class="sxs-lookup"><span data-stu-id="5ff45-114">Unpacks archives and a specified location.</span></span> <span data-ttu-id="5ff45-115">Valideert de archieven met een opgegeven **controlesom**.</span><span class="sxs-lookup"><span data-stu-id="5ff45-115">Validates the archives with a specified **Checksum**.</span></span>|
|<span data-ttu-id="5ff45-116">**Variabelen**</span><span class="sxs-lookup"><span data-stu-id="5ff45-116">**Environment**</span></span>|<span data-ttu-id="5ff45-117">Hiermee beheert u omgevings variabelen.</span><span class="sxs-lookup"><span data-stu-id="5ff45-117">Manages environment variables.</span></span>|
|<span data-ttu-id="5ff45-118">**Groep**</span><span class="sxs-lookup"><span data-stu-id="5ff45-118">**Group**</span></span>|<span data-ttu-id="5ff45-119">Beheert lokale groepen en beheert groepslid maatschap.</span><span class="sxs-lookup"><span data-stu-id="5ff45-119">Manages local groups and controls group membership.</span></span>|
|<span data-ttu-id="5ff45-120">**Log**</span><span class="sxs-lookup"><span data-stu-id="5ff45-120">**Log**</span></span>|<span data-ttu-id="5ff45-121">Hiermee worden berichten naar het gebeurtenis logboek van @no__t 0 geschreven.</span><span class="sxs-lookup"><span data-stu-id="5ff45-121">Writes messages to the `Microsoft-Windows-Desired State Configuration/Analytic` event log.</span></span>|
|<span data-ttu-id="5ff45-122">**Pakket**</span><span class="sxs-lookup"><span data-stu-id="5ff45-122">**Package**</span></span>|<span data-ttu-id="5ff45-123">Installeert of verwijdert pakketten met behulp van **argumenten**, **logPath**, **return code**en andere instellingen.</span><span class="sxs-lookup"><span data-stu-id="5ff45-123">Installs or uninstalls packages using **Arguments**, **LogPath**, **ReturnCode**, other settings.</span></span>|
|<span data-ttu-id="5ff45-124">**Registersubsleutel**</span><span class="sxs-lookup"><span data-stu-id="5ff45-124">**Registry**</span></span>|<span data-ttu-id="5ff45-125">Beheert register sleutels en-waarden.</span><span class="sxs-lookup"><span data-stu-id="5ff45-125">Manages registry keys and values.</span></span>|
|<span data-ttu-id="5ff45-126">**Schriften**</span><span class="sxs-lookup"><span data-stu-id="5ff45-126">**Script**</span></span>|<span data-ttu-id="5ff45-127">Met kunt u uw eigen script blokken voor [Get-test-set](../resources/get-test-set.md) ontwerpen.</span><span class="sxs-lookup"><span data-stu-id="5ff45-127">Allows you to design your own [get-test-set](../resources/get-test-set.md) script blocks.</span></span>|
|<span data-ttu-id="5ff45-128">**Service**</span><span class="sxs-lookup"><span data-stu-id="5ff45-128">**Service**</span></span>|<span data-ttu-id="5ff45-129">Hiermee configureert u Windows-Services.</span><span class="sxs-lookup"><span data-stu-id="5ff45-129">Configures Windows services.</span></span>|
|<span data-ttu-id="5ff45-130">**Gebruiker**</span><span class="sxs-lookup"><span data-stu-id="5ff45-130">**User**</span></span> |<span data-ttu-id="5ff45-131">Hiermee beheert u lokale gebruikers en kenmerken.</span><span class="sxs-lookup"><span data-stu-id="5ff45-131">Manages local users and attributes.</span></span>|
|<span data-ttu-id="5ff45-132">**WindowsFeature**</span><span class="sxs-lookup"><span data-stu-id="5ff45-132">**WindowsFeature**</span></span>|<span data-ttu-id="5ff45-133">Beheert functies en onderdelen.</span><span class="sxs-lookup"><span data-stu-id="5ff45-133">Manages roles and features.</span></span>|
|<span data-ttu-id="5ff45-134">**WindowsProcess**</span><span class="sxs-lookup"><span data-stu-id="5ff45-134">**WindowsProcess**</span></span>|<span data-ttu-id="5ff45-135">Configureert Windows-processen.</span><span class="sxs-lookup"><span data-stu-id="5ff45-135">Configures Windows processes.</span></span>|

<span data-ttu-id="5ff45-136">De OOB-resources bieden een goed uitgangs punt voor veelvoorkomende bewerkingen.</span><span class="sxs-lookup"><span data-stu-id="5ff45-136">The OOB resources allow a good starting point for common operations.</span></span> <span data-ttu-id="5ff45-137">Als de OOB-resources niet aan uw behoeften voldoen, kunt u uw eigen [aangepaste resource](../resources/authoringResource.md)schrijven.</span><span class="sxs-lookup"><span data-stu-id="5ff45-137">If the OOB resources do not meet your needs, you can write your own [Custom Resource](../resources/authoringResource.md).</span></span> <span data-ttu-id="5ff45-138">Voordat u een aangepaste resource schrijft om uw probleem op te lossen, moet u het grote aantal DSC-resources dat u al hebt gemaakt door zowel micro soft als de Power shell-community bekijken.</span><span class="sxs-lookup"><span data-stu-id="5ff45-138">Before you write a custom resource to solve your problem, you should look through the vast number of DSC resources that have already been created by both Microsoft and the PowerShell community.</span></span>

<span data-ttu-id="5ff45-139">U kunt DSC-resources vinden in zowel de [PowerShell Gallery](https://www.powershellgallery.com/) als de [github](https://github.com/).</span><span class="sxs-lookup"><span data-stu-id="5ff45-139">You can find DSC resources in both the [PowerShell Gallery](https://www.powershellgallery.com/) and [GitHub](https://github.com/).</span></span> <span data-ttu-id="5ff45-140">U kunt DSC-resources ook rechtstreeks installeren vanuit de Power shell-console met behulp van [PowerShellGet](/powershell/module/powershellget/).</span><span class="sxs-lookup"><span data-stu-id="5ff45-140">You can also install DSC resources directly from the PowerShell console using [PowerShellGet](/powershell/module/powershellget/).</span></span>

## <a name="installing-powershellget"></a><span data-ttu-id="5ff45-141">PowerShellGet installeren</span><span class="sxs-lookup"><span data-stu-id="5ff45-141">Installing PowerShellGet</span></span>

<span data-ttu-id="5ff45-142">Raadpleeg de volgende hand leiding om te bepalen of u al **Power shell** Get hebt of om hulp te krijgen: [PowerShellGet installeren](/powershell/gallery/installing-psget).</span><span class="sxs-lookup"><span data-stu-id="5ff45-142">To determine if you already have **PowerShell** get, or to get help installing it, see the following guide: [Installing PowerShellGet](/powershell/gallery/installing-psget).</span></span>

## <a name="finding-dsc-resources-using-powershellget"></a><span data-ttu-id="5ff45-143">DSC-resources zoeken met PowerShellGet</span><span class="sxs-lookup"><span data-stu-id="5ff45-143">Finding DSC resources using PowerShellGet</span></span>

<span data-ttu-id="5ff45-144">Zodra **PowerShellGet** op uw systeem is geïnstalleerd, kunt u DSC-resources zoeken en installeren die worden gehost in de [PowerShell Gallery](https://www.powershellgallery.com/).</span><span class="sxs-lookup"><span data-stu-id="5ff45-144">Once **PowerShellGet** is installed on your system, you can find and install DSC resources hosted in the [PowerShell Gallery](https://www.powershellgallery.com/).</span></span>

<span data-ttu-id="5ff45-145">Gebruik eerst de cmdlet [Find-dscresource bieden](/powershell/module/powershellget/find-dscresource) om DSC-resources te zoeken.</span><span class="sxs-lookup"><span data-stu-id="5ff45-145">First, use the [Find-DSCResource](/powershell/module/powershellget/find-dscresource) cmdlet to find DSC resources.</span></span> <span data-ttu-id="5ff45-146">Wanneer u `Find-DSCResource` voor de eerste keer uitvoert, ziet u de volgende prompt om de NuGet-provider te installeren.</span><span class="sxs-lookup"><span data-stu-id="5ff45-146">When you run `Find-DSCResource` for the first time, you see the following prompt to install the "NuGet provider".</span></span>

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

<span data-ttu-id="5ff45-147">Nadat u op y hebt gedrukt, wordt de NuGet-provider geïnstalleerd en ziet u een lijst met DSC-resources die u vanuit de PowerShell Gallery kunt installeren.</span><span class="sxs-lookup"><span data-stu-id="5ff45-147">After pressing 'y', the "NuGet" provider is installed, you see a list of DSC resources that you can install from the PowerShell Gallery.</span></span>

> [!NOTE]
> <span data-ttu-id="5ff45-148">De lijst wordt niet weer gegeven omdat deze erg groot is.</span><span class="sxs-lookup"><span data-stu-id="5ff45-148">List is not shown because it is very large.</span></span>

<span data-ttu-id="5ff45-149">U kunt ook de para meter `-Name` opgeven met behulp van joker tekens of met de para meter `-Filter` zonder joker tekens om uw zoek opdracht te verfijnen.</span><span class="sxs-lookup"><span data-stu-id="5ff45-149">You can also specify the `-Name` parameter using wildcards, or `-Filter` parameter without wildcards to narrow down your search.</span></span> <span data-ttu-id="5ff45-150">In dit voor beeld wordt geprobeerd een ' time zone ' DSC-resource te vinden met behulp van de joker tekens.</span><span class="sxs-lookup"><span data-stu-id="5ff45-150">This example attempts to find a "TimeZone" DSC resource using the wildcards.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="5ff45-151">Er is momenteel een fout in de `Find-DSCResource`-cmdlet waarmee u geen gebruik kunt maken van joker tekens in de para meters `-Name` en `-Filter`.</span><span class="sxs-lookup"><span data-stu-id="5ff45-151">Currently there is a bug in the `Find-DSCResource` cmdlet that prevents using wildcards in both the `-Name` and `-Filter` parameters.</span></span> <span data-ttu-id="5ff45-152">In het tweede voor beeld hieronder ziet u een tijdelijke oplossing met `Where-Object`.</span><span class="sxs-lookup"><span data-stu-id="5ff45-152">The second example below shows a workaround using `Where-Object`.</span></span>

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

<span data-ttu-id="5ff45-153">U kunt ook `Where-Object` gebruiken om DSC-resources te zoeken met nauw keurigere filters.</span><span class="sxs-lookup"><span data-stu-id="5ff45-153">You can also use `Where-Object` to find DSC resources with more granular filtering.</span></span> <span data-ttu-id="5ff45-154">Deze aanpak is trager dan het gebruik van ingebouwde filter parameters.</span><span class="sxs-lookup"><span data-stu-id="5ff45-154">This approach will be slower than using built in filtering parameters.</span></span>

```
PS> Find-DSCResource | Where-Object {$_.Name -like "Time*"}

Name                                Version    ModuleName                          Repository
----                                -------    ----------                          ----------
TimeZone                            6.0.0.0    ComputerManagementDsc               PSGallery
```

<span data-ttu-id="5ff45-155">Zie voor meer informatie over filteren [where-object](/powershell/module/microsoft.powershell.core/where-object).</span><span class="sxs-lookup"><span data-stu-id="5ff45-155">For more information on filtering, see [Where-Object](/powershell/module/microsoft.powershell.core/where-object).</span></span>

## <a name="installing-dsc-resources-using-powershellget"></a><span data-ttu-id="5ff45-156">DSC-resources installeren met behulp van PowerShellGet</span><span class="sxs-lookup"><span data-stu-id="5ff45-156">Installing DSC Resources using PowerShellGet</span></span>

<span data-ttu-id="5ff45-157">Als u een DSC-resource wilt installeren, gebruikt u de cmdlet [install-module](/powershell/module/PowershellGet/Install-Module) , waarbij u de naam opgeeft van de module die wordt weer gegeven onder **module** naam in uw zoek resultaten.</span><span class="sxs-lookup"><span data-stu-id="5ff45-157">To install a DSC resource, use the [Install-Module](/powershell/module/PowershellGet/Install-Module) cmdlet, specifying the name of the module shown under **Module** name in your search results.</span></span>

<span data-ttu-id="5ff45-158">De resource ' tijd zone ' bevindt zich in de module ' ComputerManagementDSC ', dus de module die in dit voor beeld wordt geïnstalleerd.</span><span class="sxs-lookup"><span data-stu-id="5ff45-158">The "TimeZone" resource exists in the "ComputerManagementDSC" module, so that is the module this example installs.</span></span>

> [!NOTE]
> <span data-ttu-id="5ff45-159">Als u de Power shell-galerie niet hebt vertrouwd, ziet u de onderstaande waarschuwing, waarna u wordt gevraagd hoe u volgende prompts voor de installatie wilt voor komen.</span><span class="sxs-lookup"><span data-stu-id="5ff45-159">If you have not trusted the PowerShell gallery, you see the warning below asking for confirmation, and instructing you how to avoid subsequent prompts on installs.</span></span>

```
PS> Install-Module -Name ComputerManagementDSC

Untrusted repository
You are installing the modules from an untrusted repository. If you trust this repository, change its
InstallationPolicy value by running the Set-PSRepository cmdlet. Are you sure you want to install the modules from
'PSGallery'?
[Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "N"):
```

<span data-ttu-id="5ff45-160">Druk op y om door te gaan met de installatie van de module.</span><span class="sxs-lookup"><span data-stu-id="5ff45-160">Press 'y' to continue installing the module.</span></span> <span data-ttu-id="5ff45-161">Na de installatie kunt u controleren of de nieuwe resource is geïnstalleerd met behulp van [Get-dscresource bieden](/powershell/module/PSDesiredStateConfiguration/Get-DscResource).</span><span class="sxs-lookup"><span data-stu-id="5ff45-161">After install, you can verify that your new resource is installed using [Get-DSCResource](/powershell/module/PSDesiredStateConfiguration/Get-DscResource).</span></span>

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

<span data-ttu-id="5ff45-162">U kunt ook andere resources in de zojuist geïnstalleerde module weer geven door de para meter `-ModuleName` op te geven.</span><span class="sxs-lookup"><span data-stu-id="5ff45-162">You can also view other resources in your newly installed module, by specifying the `-ModuleName` parameter.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="5ff45-163">Zie ook</span><span class="sxs-lookup"><span data-stu-id="5ff45-163">See also</span></span>

- [<span data-ttu-id="5ff45-164">Wat zijn bronnen?</span><span class="sxs-lookup"><span data-stu-id="5ff45-164">What are Resources?</span></span>](../resources/resources.md)
