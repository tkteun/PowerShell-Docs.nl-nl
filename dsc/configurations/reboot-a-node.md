---
ms.date: 1/17/2019
keywords: DSC, powershell, configuratie en installatie
title: Een knooppunt opnieuw opstarten
ms.openlocfilehash: 015b82a32caefc420973651c72e272fd85baf880
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62080115"
---
# <a name="reboot-a-node"></a><span data-ttu-id="96aa2-103">Een knooppunt opnieuw opstarten</span><span class="sxs-lookup"><span data-stu-id="96aa2-103">Reboot a Node</span></span>

> [!NOTE]
> <span data-ttu-id="96aa2-104">In dit onderwerp wordt besproken hoe u een knooppunt opnieuw opstarten.</span><span class="sxs-lookup"><span data-stu-id="96aa2-104">This topic talks about how to reboot a Node.</span></span> <span data-ttu-id="96aa2-105">In de volgorde voor het opnieuw opstarten om succesvol te zijn de **ActionAfterReboot** en **RebootNodeIfNeeded** LCM instellingen moeten correct worden geconfigureerd.</span><span class="sxs-lookup"><span data-stu-id="96aa2-105">In order for the reboot to be successful the **ActionAfterReboot** and **RebootNodeIfNeeded** LCM settings need to be configured properly.</span></span>
> <span data-ttu-id="96aa2-106">Zie voor meer informatie over de lokale Configuration Manager-instellingen, [de Local Configuration Manager configureren](../managing-nodes/metaConfig.md), of [configureren de Local Configuration Manager (v4)](../managing-nodes/metaConfig4.md).</span><span class="sxs-lookup"><span data-stu-id="96aa2-106">To read about Local Configuration Manager settings, see [Configure the Local Configuration Manager](../managing-nodes/metaConfig.md), or [Configure the Local Configuration Manager (v4)](../managing-nodes/metaConfig4.md).</span></span>

<span data-ttu-id="96aa2-107">Knooppunten kunnen opnieuw worden opgestart vanaf binnen een resource, met behulp van de `$global:DSCMachineStatus` vlag.</span><span class="sxs-lookup"><span data-stu-id="96aa2-107">Nodes can be rebooted from within a resource, by using the `$global:DSCMachineStatus` flag.</span></span> <span data-ttu-id="96aa2-108">Als deze vlag instelt op `1` in de `Set-TargetResource` functie zorgt ervoor dat de LCM om het knooppunt rechtstreeks na opnieuw opstarten de **ingesteld** methode van de huidige resourcegroep.</span><span class="sxs-lookup"><span data-stu-id="96aa2-108">Setting this flag to `1` in the `Set-TargetResource` function forces the LCM to reboot the Node directly after the **Set** method of the current resource.</span></span> <span data-ttu-id="96aa2-109">Met deze markering de **xPendingReboot** resource wordt gedetecteerd of een opnieuw opstarten in behandeling is buiten DSC.</span><span class="sxs-lookup"><span data-stu-id="96aa2-109">Using this flag, the **xPendingReboot** resource detects if a reboot is pending outside of DSC.</span></span>

<span data-ttu-id="96aa2-110">Uw [configuraties](configurations.md) voeren stappen waarvoor het knooppunt opnieuw op te starten.</span><span class="sxs-lookup"><span data-stu-id="96aa2-110">Your [configurations](configurations.md) may perform steps that require the Node to reboot.</span></span> <span data-ttu-id="96aa2-111">Dit kan bijvoorbeeld dingen omvatten:</span><span class="sxs-lookup"><span data-stu-id="96aa2-111">This could include things such as:</span></span>

- <span data-ttu-id="96aa2-112">Windows-updates</span><span class="sxs-lookup"><span data-stu-id="96aa2-112">Windows updates</span></span>
- <span data-ttu-id="96aa2-113">Software-installatie</span><span class="sxs-lookup"><span data-stu-id="96aa2-113">Software install</span></span>
- <span data-ttu-id="96aa2-114">De naam van bestand wijzigen</span><span class="sxs-lookup"><span data-stu-id="96aa2-114">File renames</span></span>
- <span data-ttu-id="96aa2-115">Computer wijzigen</span><span class="sxs-lookup"><span data-stu-id="96aa2-115">Computer rename</span></span>

<span data-ttu-id="96aa2-116">De **xPendingReboot** resource controleert locaties van de specifieke computer om te bepalen of een opnieuw opstarten in behandeling is.</span><span class="sxs-lookup"><span data-stu-id="96aa2-116">The **xPendingReboot** resource checks specific computer locations to determine if a reboot is pending.</span></span> <span data-ttu-id="96aa2-117">Als het knooppunt opnieuw worden opgestart buiten DSC moet, de **xPendingReboot** resource stelt de `$global:DSCMachineStatus` markering `1` forceren van opnieuw opstarten en het oplossen van de voorwaarde in behandeling.</span><span class="sxs-lookup"><span data-stu-id="96aa2-117">If the Node requires a reboot outside of DSC, the **xPendingReboot** resource sets the `$global:DSCMachineStatus` flag to `1` forcing a reboot and resolving the pending condition.</span></span>

> [!NOTE]
> <span data-ttu-id="96aa2-118">Een DSC-resource kan de opdracht geven de LCM om het knooppunt opnieuw opstarten met deze markering instellen de `Set-TargetResource` functie.</span><span class="sxs-lookup"><span data-stu-id="96aa2-118">Any DSC resource can instruct the LCM to reboot the node by setting this flag in the `Set-TargetResource` function.</span></span> <span data-ttu-id="96aa2-119">Zie voor meer informatie, [schrijven van een aangepaste DSC-resource met MOF](../resources/authoringResourceMOF.md).</span><span class="sxs-lookup"><span data-stu-id="96aa2-119">For more information, see [Writing a custom DSC resource with MOF](../resources/authoringResourceMOF.md).</span></span>

## <a name="syntax"></a><span data-ttu-id="96aa2-120">Syntaxis</span><span class="sxs-lookup"><span data-stu-id="96aa2-120">Syntax</span></span>

```
xPendingReboot [String] #ResourceName
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

## <a name="properties"></a><span data-ttu-id="96aa2-121">Eigenschappen</span><span class="sxs-lookup"><span data-stu-id="96aa2-121">Properties</span></span>

| <span data-ttu-id="96aa2-122">Eigenschap</span><span class="sxs-lookup"><span data-stu-id="96aa2-122">Property</span></span> | <span data-ttu-id="96aa2-123">Description</span><span class="sxs-lookup"><span data-stu-id="96aa2-123">Description</span></span> |
| --- | --- |
| <span data-ttu-id="96aa2-124">Naam</span><span class="sxs-lookup"><span data-stu-id="96aa2-124">Name</span></span>| <span data-ttu-id="96aa2-125">De vereiste parameter moet uniek zijn per exemplaar van de resource in een configuratie.</span><span class="sxs-lookup"><span data-stu-id="96aa2-125">Required parameter that must be unique per instance of the resource within a configuration.</span></span>|
| <span data-ttu-id="96aa2-126">SkipComponentBasedServicing</span><span class="sxs-lookup"><span data-stu-id="96aa2-126">SkipComponentBasedServicing</span></span> | <span data-ttu-id="96aa2-127">Overslaan opnieuw wordt opgestart door het onderdeel Component-Based Servicing geactiveerd.</span><span class="sxs-lookup"><span data-stu-id="96aa2-127">Skip reboots triggered by the Component-Based Servicing component.</span></span> |
| <span data-ttu-id="96aa2-128">SkipWindowsUpdate</span><span class="sxs-lookup"><span data-stu-id="96aa2-128">SkipWindowsUpdate</span></span> | <span data-ttu-id="96aa2-129">Overslaan opnieuw wordt opgestart geactiveerd door Windows Update.</span><span class="sxs-lookup"><span data-stu-id="96aa2-129">Skip reboots triggered by Windows Update.</span></span>|
| <span data-ttu-id="96aa2-130">SkipPendingFileRename</span><span class="sxs-lookup"><span data-stu-id="96aa2-130">SkipPendingFileRename</span></span> | <span data-ttu-id="96aa2-131">Opnieuw opstarten in behandeling zijnde-naam overslaan.</span><span class="sxs-lookup"><span data-stu-id="96aa2-131">Skip pending file rename reboots.</span></span> |
| <span data-ttu-id="96aa2-132">SkipCcmClientSDK</span><span class="sxs-lookup"><span data-stu-id="96aa2-132">SkipCcmClientSDK</span></span> | <span data-ttu-id="96aa2-133">Overslaan opnieuw wordt opgestart geactiveerd door de ConfigMgr-client.</span><span class="sxs-lookup"><span data-stu-id="96aa2-133">Skip reboots triggered by the ConfigMgr client.</span></span> |
| <span data-ttu-id="96aa2-134">SkipComputerRename</span><span class="sxs-lookup"><span data-stu-id="96aa2-134">SkipComputerRename</span></span> | <span data-ttu-id="96aa2-135">Overslaan opnieuw wordt opgestart door de naam van de Computer geactiveerd.</span><span class="sxs-lookup"><span data-stu-id="96aa2-135">Skip reboots triggered by Computer renames.</span></span> |
| <span data-ttu-id="96aa2-136">PSDSCRunAsCredential</span><span class="sxs-lookup"><span data-stu-id="96aa2-136">PSDSCRunAsCredential</span></span> | <span data-ttu-id="96aa2-137">Ondersteund in versie 5.</span><span class="sxs-lookup"><span data-stu-id="96aa2-137">Supported in v5.</span></span> <span data-ttu-id="96aa2-138">De resource als de opgegeven gebruiker uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="96aa2-138">Executes the resource as the specified user.</span></span> |
| <span data-ttu-id="96aa2-139">DependsOn</span><span class="sxs-lookup"><span data-stu-id="96aa2-139">DependsOn</span></span> | <span data-ttu-id="96aa2-140">Geeft aan dat de configuratie van een andere resource uitvoeren moet voordat deze resource is geconfigureerd.</span><span class="sxs-lookup"><span data-stu-id="96aa2-140">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="96aa2-141">Bijvoorbeeld, als de ID van de resourceconfiguratie scriptblok die u wilt uitvoeren eerst is **ResourceName** en het type **ResourceType**, de syntaxis voor het gebruik van deze eigenschap is `DependsOn = "[ResourceType]ResourceName"`.</span><span class="sxs-lookup"><span data-stu-id="96aa2-141">For example, if the ID of the resource configuration script block that you want to run first is **ResourceName** and its type is **ResourceType**, the syntax for using this property is `DependsOn = "[ResourceType]ResourceName"`.</span></span> <span data-ttu-id="96aa2-142">Zie voor meer informatie, [DependsOn gebruiken](resource-depends-on.md)</span><span class="sxs-lookup"><span data-stu-id="96aa2-142">For more information, see [Using DependsOn](resource-depends-on.md)</span></span>|

## <a name="example"></a><span data-ttu-id="96aa2-143">Voorbeeld</span><span class="sxs-lookup"><span data-stu-id="96aa2-143">Example</span></span>

<span data-ttu-id="96aa2-144">Het volgende voorbeeld installeert met behulp van Microsoft Exchange de [xExchange](https://github.com/PowerShell/xExchange) resource.</span><span class="sxs-lookup"><span data-stu-id="96aa2-144">The following example installs Microsoft Exchange using the [xExchange](https://github.com/PowerShell/xExchange) resource.</span></span>
<span data-ttu-id="96aa2-145">Tijdens de installatie de **xPendingReboot** bron wordt gebruikt om het knooppunt opnieuw opstarten.</span><span class="sxs-lookup"><span data-stu-id="96aa2-145">Throughout the install, the **xPendingReboot** resource is used to reboot the Node.</span></span>

> [!NOTE]
> <span data-ttu-id="96aa2-146">In dit voorbeeld is de referentie van een account met machtigingen voor het toevoegen van een Exchange-server aan het forest vereist.</span><span class="sxs-lookup"><span data-stu-id="96aa2-146">This example requires the credential of an account that has rights to add an Exchange server to the forest.</span></span> <span data-ttu-id="96aa2-147">Zie voor meer informatie over het gebruik van referenties in DSC [verwerken van de referenties in DSC](../configurations/configDataCredentials.md)</span><span class="sxs-lookup"><span data-stu-id="96aa2-147">For more information on using credentials in DSC, see [Handling Credentials in DSC](../configurations/configDataCredentials.md)</span></span>

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
    Import-DscResource -Module xPendingReboot

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
        xPendingReboot BeforeExchangeInstall
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
            DependsOn  = '[xPendingReboot]BeforeExchangeInstall'
        }

        # See if a reboot is required after installing Exchange
        xPendingReboot AfterExchangeInstall
        {
            Name      = 'AfterExchangeInstall'
            DependsOn = '[xExchInstall]InstallExchange'
        }
    }
}
```

> [!NOTE]
> <span data-ttu-id="96aa2-148">In dit voorbeeld wordt ervan uitgegaan dat u de Local Configuration Manager als u wilt toestaan dat opnieuw wordt opgestart en doorgaan met de configuratie na het opnieuw opstarten hebt geconfigureerd.</span><span class="sxs-lookup"><span data-stu-id="96aa2-148">This example assumes that you have configured your Local Configuration Manager to allow reboots and continue the configuration after a reboot.</span></span>

## <a name="where-to-download"></a><span data-ttu-id="96aa2-149">Het downloaden</span><span class="sxs-lookup"><span data-stu-id="96aa2-149">Where to Download</span></span>

<span data-ttu-id="96aa2-150">U kunt de resources die worden gebruikt in dit onderwerp op de volgende locaties of met behulp van de PowerShell gallery downloaden.</span><span class="sxs-lookup"><span data-stu-id="96aa2-150">You can download the resources used in this topic at the following locations, or by using the PowerShell gallery.</span></span>

- [<span data-ttu-id="96aa2-151">xPendingReboot</span><span class="sxs-lookup"><span data-stu-id="96aa2-151">xPendingReboot</span></span>](https://github.com/PowerShell/xPendingReboot)
- [<span data-ttu-id="96aa2-152">xExchange</span><span class="sxs-lookup"><span data-stu-id="96aa2-152">xExchange</span></span>](https://github.com/PowerShell/xExchange)
