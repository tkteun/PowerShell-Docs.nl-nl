---
ms.date: 12/12/2018
keywords: DSC, Power shell, resource, Galerie, Setup
title: Aanvullende DSC-resources installeren
description: Dit artikel bevat een overzicht van de DSC-resources die zijn opgenomen in de PSDesiredStateConfiguration-module. Er wordt ook uitgelegd hoe u resources kunt zoeken en installeren vanaf de PowerShell Gallery.
ms.openlocfilehash: e75561ed539e06716c9a103f905b9d1e4f3e71d3
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/27/2020
ms.locfileid: "92645128"
---
# <a name="install-additional-dsc-resources"></a><span data-ttu-id="6810f-105">Aanvullende DSC-resources installeren</span><span class="sxs-lookup"><span data-stu-id="6810f-105">Install Additional DSC Resources</span></span>

<span data-ttu-id="6810f-106">Power shell bevat verschillende out-of-the-box bronnen voor desired state Configuration (DSC).</span><span class="sxs-lookup"><span data-stu-id="6810f-106">PowerShell includes several Out-of-the-box resources for Desired State Configuration (DSC).</span></span> <span data-ttu-id="6810f-107">De **PSDesiredStateConfiguration** -module bevat alle OOB DSC-resources die beschikbaar zijn op uw specifieke instantie van Power shell.</span><span class="sxs-lookup"><span data-stu-id="6810f-107">The **PSDesiredStateConfiguration** module contains all of the OOB DSC resources available on your specific instance of PowerShell.</span></span>

<span data-ttu-id="6810f-108">Dit is een lijst met de OOB-resources die zijn opgenomen in Power Shell 4,0 en een beschrijving van de mogelijkheden van de resource.</span><span class="sxs-lookup"><span data-stu-id="6810f-108">This is a list of the OOB resources included in PowerShell 4.0 and a description of the resource's capabilities.</span></span>

> [!NOTE]
> <span data-ttu-id="6810f-109">Dit is een onvolledige lijst, omdat het aantal OOB-resources is toegenomen met elke versie van Power shell.</span><span class="sxs-lookup"><span data-stu-id="6810f-109">This is an incomplete list, as the number of OOB resources has grown with each version of PowerShell.</span></span>

|      <span data-ttu-id="6810f-110">Resource</span><span class="sxs-lookup"><span data-stu-id="6810f-110">Resource</span></span>      |                                                                                       <span data-ttu-id="6810f-111">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="6810f-111">Description</span></span>                                                                                        |
| ------------------ | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| <span data-ttu-id="6810f-112">**File**</span><span class="sxs-lookup"><span data-stu-id="6810f-112">**File**</span></span>           | <span data-ttu-id="6810f-113">Hiermee bepaalt u de status van bestanden en mappen.</span><span class="sxs-lookup"><span data-stu-id="6810f-113">Controls the state of files and directories.</span></span> <span data-ttu-id="6810f-114">Kopieert bestanden van een **bron** naar een **doel** en werkt deze bij wanneer de **bron** wordt gewijzigd door datums, controle sommen en hashes te vergelijken.</span><span class="sxs-lookup"><span data-stu-id="6810f-114">Copies files from a **Source** to a **Destination** and updates them when the **Source** changes by comparing dates, checksums, and hashes.</span></span> |
| <span data-ttu-id="6810f-115">**Archiveren**</span><span class="sxs-lookup"><span data-stu-id="6810f-115">**Archive**</span></span>        | <span data-ttu-id="6810f-116">De archieven en een opgegeven locatie worden uitgepakt.</span><span class="sxs-lookup"><span data-stu-id="6810f-116">Unpacks archives and a specified location.</span></span> <span data-ttu-id="6810f-117">Valideert de archieven met een opgegeven **controlesom** .</span><span class="sxs-lookup"><span data-stu-id="6810f-117">Validates the archives with a specified **Checksum** .</span></span>                                                                                         |
| <span data-ttu-id="6810f-118">**Omgeving**</span><span class="sxs-lookup"><span data-stu-id="6810f-118">**Environment**</span></span>    | <span data-ttu-id="6810f-119">Hiermee beheert u omgevings variabelen.</span><span class="sxs-lookup"><span data-stu-id="6810f-119">Manages environment variables.</span></span>                                                                                                                                                           |
| <span data-ttu-id="6810f-120">**Groep**</span><span class="sxs-lookup"><span data-stu-id="6810f-120">**Group**</span></span>          | <span data-ttu-id="6810f-121">Beheert lokale groepen en beheert groepslid maatschap.</span><span class="sxs-lookup"><span data-stu-id="6810f-121">Manages local groups and controls group membership.</span></span>                                                                                                                                      |
| <span data-ttu-id="6810f-122">**Logbestand**</span><span class="sxs-lookup"><span data-stu-id="6810f-122">**Log**</span></span>            | <span data-ttu-id="6810f-123">Hiermee worden berichten naar het `Microsoft-Windows-Desired State Configuration/Analytic` gebeurtenis logboek geschreven.</span><span class="sxs-lookup"><span data-stu-id="6810f-123">Writes messages to the `Microsoft-Windows-Desired State Configuration/Analytic` event log.</span></span>                                                                                               |
| <span data-ttu-id="6810f-124">**Pakket**</span><span class="sxs-lookup"><span data-stu-id="6810f-124">**Package**</span></span>        | <span data-ttu-id="6810f-125">Installeert of verwijdert pakketten met behulp van **argumenten** , **logPath** , **return code** en andere instellingen.</span><span class="sxs-lookup"><span data-stu-id="6810f-125">Installs or uninstalls packages using **Arguments** , **LogPath** , **ReturnCode** , other settings.</span></span>                                                                                        |
| <span data-ttu-id="6810f-126">**Register**</span><span class="sxs-lookup"><span data-stu-id="6810f-126">**Registry**</span></span>       | <span data-ttu-id="6810f-127">Beheert register sleutels en-waarden.</span><span class="sxs-lookup"><span data-stu-id="6810f-127">Manages registry keys and values.</span></span>                                                                                                                                                        |
| <span data-ttu-id="6810f-128">**Script**</span><span class="sxs-lookup"><span data-stu-id="6810f-128">**Script**</span></span>         | <span data-ttu-id="6810f-129">Met kunt u uw eigen script blokken voor [Get-test-set](../resources/get-test-set.md) ontwerpen.</span><span class="sxs-lookup"><span data-stu-id="6810f-129">Allows you to design your own [get-test-set](../resources/get-test-set.md) script blocks.</span></span>                                                                                                |
| <span data-ttu-id="6810f-130">**Service**</span><span class="sxs-lookup"><span data-stu-id="6810f-130">**Service**</span></span>        | <span data-ttu-id="6810f-131">Hiermee configureert u Windows-Services.</span><span class="sxs-lookup"><span data-stu-id="6810f-131">Configures Windows services.</span></span>                                                                                                                                                             |
| <span data-ttu-id="6810f-132">**Gebruiker**</span><span class="sxs-lookup"><span data-stu-id="6810f-132">**User**</span></span>           | <span data-ttu-id="6810f-133">Hiermee beheert u lokale gebruikers en kenmerken.</span><span class="sxs-lookup"><span data-stu-id="6810f-133">Manages local users and attributes.</span></span>                                                                                                                                                      |
| <span data-ttu-id="6810f-134">**WindowsFeature**</span><span class="sxs-lookup"><span data-stu-id="6810f-134">**WindowsFeature**</span></span> | <span data-ttu-id="6810f-135">Beheert functies en onderdelen.</span><span class="sxs-lookup"><span data-stu-id="6810f-135">Manages roles and features.</span></span>                                                                                                                                                              |
| <span data-ttu-id="6810f-136">**WindowsProcess**</span><span class="sxs-lookup"><span data-stu-id="6810f-136">**WindowsProcess**</span></span> | <span data-ttu-id="6810f-137">Configureert Windows-processen.</span><span class="sxs-lookup"><span data-stu-id="6810f-137">Configures Windows processes.</span></span>                                                                                                                                                            |

<span data-ttu-id="6810f-138">De OOB-resources bieden een goed uitgangs punt voor veelvoorkomende bewerkingen.</span><span class="sxs-lookup"><span data-stu-id="6810f-138">The OOB resources allow a good starting point for common operations.</span></span> <span data-ttu-id="6810f-139">Als de OOB-resources niet aan uw behoeften voldoen, kunt u uw eigen [aangepaste resource](../resources/authoringResource.md)schrijven.</span><span class="sxs-lookup"><span data-stu-id="6810f-139">If the OOB resources do not meet your needs, you can write your own [Custom Resource](../resources/authoringResource.md).</span></span> <span data-ttu-id="6810f-140">Voordat u een aangepaste resource schrijft om uw probleem op te lossen, moet u het grote aantal DSC-resources dat u al hebt gemaakt door zowel micro soft als de Power shell-community bekijken.</span><span class="sxs-lookup"><span data-stu-id="6810f-140">Before you write a custom resource to solve your problem, you should look through the vast number of DSC resources that have already been created by both Microsoft and the PowerShell community.</span></span>

<span data-ttu-id="6810f-141">U kunt DSC-resources vinden in zowel de [PowerShell Gallery](https://www.powershellgallery.com/) als de [github](https://github.com/).</span><span class="sxs-lookup"><span data-stu-id="6810f-141">You can find DSC resources in both the [PowerShell Gallery](https://www.powershellgallery.com/) and [GitHub](https://github.com/).</span></span> <span data-ttu-id="6810f-142">U kunt DSC-resources ook rechtstreeks installeren vanuit de Power shell-console met behulp van [PowerShellGet](/powershell/module/powershellget/).</span><span class="sxs-lookup"><span data-stu-id="6810f-142">You can also install DSC resources directly from the PowerShell console using [PowerShellGet](/powershell/module/powershellget/).</span></span>

## <a name="installing-powershellget"></a><span data-ttu-id="6810f-143">PowerShellGet installeren</span><span class="sxs-lookup"><span data-stu-id="6810f-143">Installing PowerShellGet</span></span>

<span data-ttu-id="6810f-144">Als u wilt weten of u al **Power shell** Get hebt of als u hulp nodig hebt bij de installatie, raadpleegt u de volgende hand leiding: [Installing PowerShellGet](/powershell/scripting/gallery/installing-psget).</span><span class="sxs-lookup"><span data-stu-id="6810f-144">To determine if you already have **PowerShell** get, or to get help installing it, see the following guide: [Installing PowerShellGet](/powershell/scripting/gallery/installing-psget).</span></span>

## <a name="finding-dsc-resources-using-powershellget"></a><span data-ttu-id="6810f-145">DSC-resources zoeken met PowerShellGet</span><span class="sxs-lookup"><span data-stu-id="6810f-145">Finding DSC resources using PowerShellGet</span></span>

<span data-ttu-id="6810f-146">Zodra **PowerShellGet** op uw systeem is geïnstalleerd, kunt u DSC-resources zoeken en installeren die worden gehost in de [PowerShell Gallery](https://www.powershellgallery.com/).</span><span class="sxs-lookup"><span data-stu-id="6810f-146">Once **PowerShellGet** is installed on your system, you can find and install DSC resources hosted in the [PowerShell Gallery](https://www.powershellgallery.com/).</span></span>

<span data-ttu-id="6810f-147">Gebruik eerst de cmdlet [Find-dscresource bieden](/powershell/module/powershellget/find-dscresource) om DSC-resources te zoeken.</span><span class="sxs-lookup"><span data-stu-id="6810f-147">First, use the [Find-DSCResource](/powershell/module/powershellget/find-dscresource) cmdlet to find DSC resources.</span></span> <span data-ttu-id="6810f-148">Wanneer u `Find-DSCResource` voor de eerste keer uitvoert, ziet u de volgende prompt om de NuGet-provider te installeren.</span><span class="sxs-lookup"><span data-stu-id="6810f-148">When you run `Find-DSCResource` for the first time, you see the following prompt to install the "NuGet provider".</span></span>

```
PS> Find-DSCResource

NuGet provider is required to continue
PowerShellGet requires NuGet provider version '2.8.5.201' or newer to interact with NuGet-based
repositories. The NuGet provider must be available in 'C:\Program Files\PackageManagement\ProviderAssemblies'
or 'C:\Users\xAdministrator\AppData\Local\PackageManagement\ProviderAssemblies'. You can also install
the NuGet provider by running 'Install-PackageProvider -Name NuGet -MinimumVersion 2.8.5.201
-Force'. Do you want PowerShellGet to install and import the NuGet provider now?
[Y] Yes  [N] No  [?] Help (default is "Y"):
```

<span data-ttu-id="6810f-149">Nadat u op y hebt gedrukt, wordt de NuGet-provider geïnstalleerd en ziet u een lijst met DSC-resources die u vanuit de PowerShell Gallery kunt installeren.</span><span class="sxs-lookup"><span data-stu-id="6810f-149">After pressing 'y', the "NuGet" provider is installed, you see a list of DSC resources that you can install from the PowerShell Gallery.</span></span>

> [!NOTE]
> <span data-ttu-id="6810f-150">De lijst wordt niet weer gegeven omdat deze erg groot is.</span><span class="sxs-lookup"><span data-stu-id="6810f-150">List is not shown because it is very large.</span></span>

<span data-ttu-id="6810f-151">U kunt de `-Name` para meter ook opgeven met Joker tekens of `-Filter` para meter zonder joker tekens om uw zoek opdracht te verfijnen.</span><span class="sxs-lookup"><span data-stu-id="6810f-151">You can also specify the `-Name` parameter using wildcards, or `-Filter` parameter without wildcards to narrow down your search.</span></span> <span data-ttu-id="6810f-152">In dit voor beeld wordt geprobeerd een ' time zone ' DSC-resource te vinden met behulp van de joker tekens.</span><span class="sxs-lookup"><span data-stu-id="6810f-152">This example attempts to find a "TimeZone" DSC resource using the wildcards.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="6810f-153">Er is momenteel een fout in de `Find-DSCResource` cmdlet die voor komt dat Joker tekens worden gebruikt in de `-Name` `-Filter` para meters en.</span><span class="sxs-lookup"><span data-stu-id="6810f-153">Currently there is a bug in the `Find-DSCResource` cmdlet that prevents using wildcards in both the `-Name` and `-Filter` parameters.</span></span> <span data-ttu-id="6810f-154">In het tweede voor beeld hieronder ziet u een tijdelijke oplossing met behulp van `Where-Object` .</span><span class="sxs-lookup"><span data-stu-id="6810f-154">The second example below shows a workaround using `Where-Object`.</span></span>

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

<span data-ttu-id="6810f-155">U kunt ook gebruiken `Where-Object` om DSC-resources te zoeken met nauw keurigere filters.</span><span class="sxs-lookup"><span data-stu-id="6810f-155">You can also use `Where-Object` to find DSC resources with more granular filtering.</span></span> <span data-ttu-id="6810f-156">Deze aanpak is trager dan het gebruik van ingebouwde filter parameters.</span><span class="sxs-lookup"><span data-stu-id="6810f-156">This approach will be slower than using built in filtering parameters.</span></span>

```
PS> Find-DSCResource | Where-Object {$_.Name -like "Time*"}

Name                                Version    ModuleName                          Repository
----                                -------    ----------                          ----------
TimeZone                            6.0.0.0    ComputerManagementDsc               PSGallery
```

<span data-ttu-id="6810f-157">Zie voor meer informatie over filteren [where-object](/powershell/module/microsoft.powershell.core/where-object).</span><span class="sxs-lookup"><span data-stu-id="6810f-157">For more information on filtering, see [Where-Object](/powershell/module/microsoft.powershell.core/where-object).</span></span>

## <a name="installing-dsc-resources-using-powershellget"></a><span data-ttu-id="6810f-158">DSC-resources installeren met behulp van PowerShellGet</span><span class="sxs-lookup"><span data-stu-id="6810f-158">Installing DSC Resources using PowerShellGet</span></span>

<span data-ttu-id="6810f-159">Als u een DSC-resource wilt installeren, gebruikt u de cmdlet [install-module](/powershell/module/PowershellGet/Install-Module) , waarbij u de naam opgeeft van de module die wordt weer gegeven onder **module** naam in uw zoek resultaten.</span><span class="sxs-lookup"><span data-stu-id="6810f-159">To install a DSC resource, use the [Install-Module](/powershell/module/PowershellGet/Install-Module) cmdlet, specifying the name of the module shown under **Module** name in your search results.</span></span>

<span data-ttu-id="6810f-160">De resource ' tijd zone ' bevindt zich in de module ' ComputerManagementDSC ', dus de module die in dit voor beeld wordt geïnstalleerd.</span><span class="sxs-lookup"><span data-stu-id="6810f-160">The "TimeZone" resource exists in the "ComputerManagementDSC" module, so that is the module this example installs.</span></span>

> [!NOTE]
> <span data-ttu-id="6810f-161">Als u de Power shell-galerie niet hebt vertrouwd, ziet u de onderstaande waarschuwing, waarna u wordt gevraagd hoe u volgende prompts voor de installatie wilt voor komen.</span><span class="sxs-lookup"><span data-stu-id="6810f-161">If you have not trusted the PowerShell gallery, you see the warning below asking for confirmation, and instructing you how to avoid subsequent prompts on installs.</span></span>

```
PS> Install-Module -Name ComputerManagementDSC

Untrusted repository
You are installing the modules from an untrusted repository. If you trust this repository, change
its InstallationPolicy value by running the Set-PSRepository cmdlet. Are you sure you want to
install the modules from 'PSGallery'?
[Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "N"):
```

<span data-ttu-id="6810f-162">Druk op y om door te gaan met de installatie van de module.</span><span class="sxs-lookup"><span data-stu-id="6810f-162">Press 'y' to continue installing the module.</span></span> <span data-ttu-id="6810f-163">Na de installatie kunt u controleren of de nieuwe resource is geïnstalleerd met behulp van [Get-dscresource bieden](/powershell/module/PSDesiredStateConfiguration/Get-DscResource).</span><span class="sxs-lookup"><span data-stu-id="6810f-163">After install, you can verify that your new resource is installed using [Get-DSCResource](/powershell/module/PSDesiredStateConfiguration/Get-DscResource).</span></span>

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

<span data-ttu-id="6810f-164">U kunt ook andere resources in de zojuist geïnstalleerde module bekijken door de para meter op te geven `-ModuleName` .</span><span class="sxs-lookup"><span data-stu-id="6810f-164">You can also view other resources in your newly installed module, by specifying the `-ModuleName` parameter.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="6810f-165">Zie ook</span><span class="sxs-lookup"><span data-stu-id="6810f-165">See also</span></span>

- [<span data-ttu-id="6810f-166">Wat zijn resources?</span><span class="sxs-lookup"><span data-stu-id="6810f-166">What are Resources?</span></span>](../resources/resources.md)
