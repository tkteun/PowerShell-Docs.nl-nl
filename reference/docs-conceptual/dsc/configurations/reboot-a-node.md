---
ms.date: 01/17/2019
keywords: DSC, Power shell, configuratie, installatie
title: Een knooppunt opnieuw opstarten
ms.openlocfilehash: 22c63fab9b6646f522f8531b46a43a94ff883552
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 12/05/2019
ms.locfileid: "71941997"
---
# <a name="reboot-a-node"></a><span data-ttu-id="dc168-103">Een knooppunt opnieuw opstarten</span><span class="sxs-lookup"><span data-stu-id="dc168-103">Reboot a Node</span></span>

> [!NOTE]
> <span data-ttu-id="dc168-104">In dit onderwerp vindt u informatie over het opnieuw opstarten van een knoop punt.</span><span class="sxs-lookup"><span data-stu-id="dc168-104">This topic talks about how to reboot a Node.</span></span> <span data-ttu-id="dc168-105">Als u de computer opnieuw wilt opstarten, moeten de instellingen voor **ActionAfterReboot** en **RebootNodeIfNeeded** LCM correct worden geconfigureerd.</span><span class="sxs-lookup"><span data-stu-id="dc168-105">In order for the reboot to be successful the **ActionAfterReboot** and **RebootNodeIfNeeded** LCM settings need to be configured properly.</span></span>
> <span data-ttu-id="dc168-106">Zie [de lokale Configuration Manager configureren](../managing-nodes/metaConfig.md)of [de lokale Configuration Manager (v4) configureren](../managing-nodes/metaConfig4.md)voor meer informatie over de instellingen van lokale Configuration Manager.</span><span class="sxs-lookup"><span data-stu-id="dc168-106">To read about Local Configuration Manager settings, see [Configure the Local Configuration Manager](../managing-nodes/metaConfig.md), or [Configure the Local Configuration Manager (v4)](../managing-nodes/metaConfig4.md).</span></span>

<span data-ttu-id="dc168-107">Knoop punten kunnen opnieuw worden opgestart vanuit een resource met behulp van de `$global:DSCMachineStatus` vlag.</span><span class="sxs-lookup"><span data-stu-id="dc168-107">Nodes can be rebooted from within a resource, by using the `$global:DSCMachineStatus` flag.</span></span> <span data-ttu-id="dc168-108">Als u deze vlag instelt op `1` in de functie `Set-TargetResource`, wordt het knoop punt direct opnieuw opgestart na de **set** -methode van de huidige resource.</span><span class="sxs-lookup"><span data-stu-id="dc168-108">Setting this flag to `1` in the `Set-TargetResource` function forces the LCM to reboot the Node directly after the **Set** method of the current resource.</span></span> <span data-ttu-id="dc168-109">Als u deze vlag gebruikt, detecteert de **PendingReboot** -resource in de DSC-resource module van [ComputerManagementDsc](https://github.com/PowerShell/ComputerManagementDsc) dat een herstart in behandeling is buiten DSC.</span><span class="sxs-lookup"><span data-stu-id="dc168-109">Using this flag, the **PendingReboot** resource in the [ComputerManagementDsc](https://github.com/PowerShell/ComputerManagementDsc) DSC Resource module detects if a reboot is pending outside of DSC.</span></span>

<span data-ttu-id="dc168-110">Uw [configuraties](configurations.md) kunnen stappen uitvoeren waarvoor het knoop punt opnieuw moet worden opgestart.</span><span class="sxs-lookup"><span data-stu-id="dc168-110">Your [configurations](configurations.md) may perform steps that require the Node to reboot.</span></span> <span data-ttu-id="dc168-111">Dit kan bijvoorbeeld de volgende oorzaken hebben:</span><span class="sxs-lookup"><span data-stu-id="dc168-111">This could include things such as:</span></span>

- <span data-ttu-id="dc168-112">Windows-updates</span><span class="sxs-lookup"><span data-stu-id="dc168-112">Windows updates</span></span>
- <span data-ttu-id="dc168-113">Software-installatie</span><span class="sxs-lookup"><span data-stu-id="dc168-113">Software install</span></span>
- <span data-ttu-id="dc168-114">Hernoemingen van bestanden</span><span class="sxs-lookup"><span data-stu-id="dc168-114">File renames</span></span>
- <span data-ttu-id="dc168-115">Computer naam wijzigen</span><span class="sxs-lookup"><span data-stu-id="dc168-115">Computer rename</span></span>

<span data-ttu-id="dc168-116">De **PendingReboot** -resource controleert specifieke computer locaties om te bepalen of opnieuw opstarten in behandeling is.</span><span class="sxs-lookup"><span data-stu-id="dc168-116">The **PendingReboot** resource checks specific computer locations to determine if a reboot is pending.</span></span> <span data-ttu-id="dc168-117">Als het knoop punt opnieuw moet worden opgestart buiten DSC, wordt met de **PendingReboot** -resource de `$global:DSCMachineStatus` vlag ingesteld op `1` geforceerd opnieuw opstarten en het oplossen van de voor waarde in behandeling.</span><span class="sxs-lookup"><span data-stu-id="dc168-117">If the Node requires a reboot outside of DSC, the **PendingReboot** resource sets the `$global:DSCMachineStatus` flag to `1` forcing a reboot and resolving the pending condition.</span></span>

> [!NOTE]
> <span data-ttu-id="dc168-118">Een DSC-resource kan de LCM de opdracht geven het knoop punt opnieuw op te starten door deze vlag in te stellen in de functie `Set-TargetResource`.</span><span class="sxs-lookup"><span data-stu-id="dc168-118">Any DSC resource can instruct the LCM to reboot the node by setting this flag in the `Set-TargetResource` function.</span></span> <span data-ttu-id="dc168-119">Zie [een aangepaste DSC-resource schrijven met MOF](../resources/authoringResourceMOF.md)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="dc168-119">For more information, see [Writing a custom DSC resource with MOF](../resources/authoringResourceMOF.md).</span></span>

## <a name="syntax"></a><span data-ttu-id="dc168-120">Syntaxis</span><span class="sxs-lookup"><span data-stu-id="dc168-120">Syntax</span></span>

```
PendingReboot [String] #ResourceName
{
    Name = [string]
    [DependsOn = [string[]]]
    [PsDscRunAsCredential = [PSCredential]]
    [SkipCcmClientSDK = [bool]]
    [SkipComponentBasedServicing = [bool]]
    [SkipPendingComputerRename = [bool]]
    [SkipPendingFileRename = [bool]]
    [SkipWindowsUpdate = [bool]]
}
```

## <a name="properties"></a><span data-ttu-id="dc168-121">Eigenschappen</span><span class="sxs-lookup"><span data-stu-id="dc168-121">Properties</span></span>

| <span data-ttu-id="dc168-122">Eigenschap</span><span class="sxs-lookup"><span data-stu-id="dc168-122">Property</span></span> | <span data-ttu-id="dc168-123">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="dc168-123">Description</span></span> |
| --- | --- |
| <span data-ttu-id="dc168-124">Naam</span><span class="sxs-lookup"><span data-stu-id="dc168-124">Name</span></span>| <span data-ttu-id="dc168-125">De vereiste para meter die uniek moet zijn per exemplaar van de resource in een configuratie.</span><span class="sxs-lookup"><span data-stu-id="dc168-125">Required parameter that must be unique per instance of the resource within a configuration.</span></span>|
| <span data-ttu-id="dc168-126">SkipComponentBasedServicing</span><span class="sxs-lookup"><span data-stu-id="dc168-126">SkipComponentBasedServicing</span></span> | <span data-ttu-id="dc168-127">Overs Laan keer opnieuw opstarten geactiveerd door het onderdeel op basis van onderhoud.</span><span class="sxs-lookup"><span data-stu-id="dc168-127">Skip reboots triggered by the Component-Based Servicing component.</span></span> |
| <span data-ttu-id="dc168-128">SkipWindowsUpdate</span><span class="sxs-lookup"><span data-stu-id="dc168-128">SkipWindowsUpdate</span></span> | <span data-ttu-id="dc168-129">Overs Laan keer opnieuw opstarten geactiveerd door Windows Update.</span><span class="sxs-lookup"><span data-stu-id="dc168-129">Skip reboots triggered by Windows Update.</span></span>|
| <span data-ttu-id="dc168-130">SkipPendingFileRename</span><span class="sxs-lookup"><span data-stu-id="dc168-130">SkipPendingFileRename</span></span> | <span data-ttu-id="dc168-131">Overs Laan herstart van bestand in behandeling.</span><span class="sxs-lookup"><span data-stu-id="dc168-131">Skip pending file rename reboots.</span></span> |
| <span data-ttu-id="dc168-132">SkipCcmClientSDK</span><span class="sxs-lookup"><span data-stu-id="dc168-132">SkipCcmClientSDK</span></span> | <span data-ttu-id="dc168-133">Sla opnieuw opstarten dat door de Configuration Manager-client wordt geactiveerd.</span><span class="sxs-lookup"><span data-stu-id="dc168-133">Skip reboots triggered by the ConfigMgr client.</span></span> |
| <span data-ttu-id="dc168-134">SkipComputerRename</span><span class="sxs-lookup"><span data-stu-id="dc168-134">SkipComputerRename</span></span> | <span data-ttu-id="dc168-135">Overs Laan keer opnieuw opstarten geactiveerd door het wijzigen van de naam van de computer.</span><span class="sxs-lookup"><span data-stu-id="dc168-135">Skip reboots triggered by Computer renames.</span></span> |
| <span data-ttu-id="dc168-136">PSDSCRunAsCredential</span><span class="sxs-lookup"><span data-stu-id="dc168-136">PSDSCRunAsCredential</span></span> | <span data-ttu-id="dc168-137">Ondersteund in V5.</span><span class="sxs-lookup"><span data-stu-id="dc168-137">Supported in v5.</span></span> <span data-ttu-id="dc168-138">Hiermee wordt de resource uitgevoerd als de opgegeven gebruiker.</span><span class="sxs-lookup"><span data-stu-id="dc168-138">Executes the resource as the specified user.</span></span> |
| <span data-ttu-id="dc168-139">DependsOn</span><span class="sxs-lookup"><span data-stu-id="dc168-139">DependsOn</span></span> | <span data-ttu-id="dc168-140">Geeft aan dat de configuratie van een andere bron moet worden uitgevoerd voordat deze resource wordt geconfigureerd.</span><span class="sxs-lookup"><span data-stu-id="dc168-140">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="dc168-141">Als de ID van het resource-configuratie script blok dat u eerst wilt uitvoeren bijvoorbeeld de naam **ResourceName** is, en het type van de **bron resource is, is**de syntaxis voor het gebruik van deze eigenschap `DependsOn = "[ResourceType]ResourceName"`.</span><span class="sxs-lookup"><span data-stu-id="dc168-141">For example, if the ID of the resource configuration script block that you want to run first is **ResourceName** and its type is **ResourceType**, the syntax for using this property is `DependsOn = "[ResourceType]ResourceName"`.</span></span> <span data-ttu-id="dc168-142">Zie [using DependsOn](resource-depends-on.md) voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="dc168-142">For more information, see [Using DependsOn](resource-depends-on.md)</span></span>|

## <a name="example"></a><span data-ttu-id="dc168-143">Voorbeeld</span><span class="sxs-lookup"><span data-stu-id="dc168-143">Example</span></span>

<span data-ttu-id="dc168-144">In het volgende voor beeld wordt micro soft Exchange geïnstalleerd met behulp van de [xExchange](https://github.com/PowerShell/xExchange) -resource.</span><span class="sxs-lookup"><span data-stu-id="dc168-144">The following example installs Microsoft Exchange using the [xExchange](https://github.com/PowerShell/xExchange) resource.</span></span>
<span data-ttu-id="dc168-145">Tijdens de installatie wordt de **PendingReboot** -resource gebruikt om het knoop punt opnieuw op te starten.</span><span class="sxs-lookup"><span data-stu-id="dc168-145">Throughout the install, the **PendingReboot** resource is used to reboot the Node.</span></span>

> [!NOTE]
> <span data-ttu-id="dc168-146">In dit voor beeld is de referentie vereist van een account met rechten voor het toevoegen van een Exchange-server aan het forest.</span><span class="sxs-lookup"><span data-stu-id="dc168-146">This example requires the credential of an account that has rights to add an Exchange server to the forest.</span></span> <span data-ttu-id="dc168-147">Zie [referenties afhandelen in DSC](../configurations/configDataCredentials.md) voor meer informatie over het gebruik van referenties in DSC</span><span class="sxs-lookup"><span data-stu-id="dc168-147">For more information on using credentials in DSC, see [Handling Credentials in DSC](../configurations/configDataCredentials.md)</span></span>

```powershell
$ConfigurationData = @{
    AllNodes = @(
        @{
            NodeName                    = '*'
            PSDSCAllowPlainTextPassword = $true
        },
        @{
            NodeName = 'DSCPULL-1'
        }
    )
}

Configuration Example
{
    param
    (
        [Parameter(Mandatory = $true)]
        [System.Management.Automation.PSCredential]
        $ExchangeAdminCredential
    )

    Import-DscResource -Module xExchange
    Import-DscResource -Module ComputerManagementDsc

    Node $AllNodes.NodeName
    {
        # Copy the Exchange setup files locally
        File ExchangeBinaries
        {
            Ensure          = 'Present'
            Type            = 'Directory'
            Recurse         = $true
            SourcePath      = '\\rras-1\Binaries\E15CU6'
            DestinationPath = 'C:\Binaries\E15CU6'
        }

        # Check if a reboot is needed before installing Exchange
        PendingReboot BeforeExchangeInstall
        {
            Name       = 'BeforeExchangeInstall'
            DependsOn  = '[File]ExchangeBinaries'
        }

        # Do the Exchange install
        xExchInstall InstallExchange
        {
            Path       = 'C:\Binaries\E15CU6\Setup.exe'
            Arguments  = '/mode:Install /role:Mailbox /Iacceptexchangeserverlicenseterms'
            Credential = $ExchangeAdminCredential
            DependsOn  = '[PendingReboot]BeforeExchangeInstall'
        }

        # See if a reboot is required after installing Exchange
        PendingReboot AfterExchangeInstall
        {
            Name      = 'AfterExchangeInstall'
            DependsOn = '[xExchInstall]InstallExchange'
        }
    }
}
```

> [!NOTE]
> <span data-ttu-id="dc168-148">In dit voor beeld wordt ervan uitgegaan dat u de lokale Configuration Manager zo hebt geconfigureerd dat deze opnieuw wordt opgestart en de configuratie kan worden voortgezet nadat de computer opnieuw is opgestart.</span><span class="sxs-lookup"><span data-stu-id="dc168-148">This example assumes that you have configured your Local Configuration Manager to allow reboots and continue the configuration after a reboot.</span></span>

## <a name="where-to-download"></a><span data-ttu-id="dc168-149">Waar downloaden?</span><span class="sxs-lookup"><span data-stu-id="dc168-149">Where to Download</span></span>

<span data-ttu-id="dc168-150">U kunt de resources downloaden die in dit onderwerp worden gebruikt op de volgende locaties of met behulp van de Power shell-galerie.</span><span class="sxs-lookup"><span data-stu-id="dc168-150">You can download the resources used in this topic at the following locations, or by using the PowerShell gallery.</span></span>

- [<span data-ttu-id="dc168-151">ComputerManagementDsc</span><span class="sxs-lookup"><span data-stu-id="dc168-151">ComputerManagementDsc</span></span>](https://github.com/PowerShell/ComputerManagementDsc)
- [<span data-ttu-id="dc168-152">xExchange</span><span class="sxs-lookup"><span data-stu-id="dc168-152">xExchange</span></span>](https://github.com/PowerShell/xExchange)
