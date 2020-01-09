---
ms.date: 08/15/2019
keywords: DSC, Power shell, configuratie, installatie
title: Aan de slag met de desired state Configuration (DSC) voor Windows
ms.openlocfilehash: 2add2c936e60c0c9446bf4b398fbf7b4bd6407f7
ms.sourcegitcommit: 1b88c280dd0799f225242608f0cbdab485357633
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 12/25/2019
ms.locfileid: "75416168"
---
# <a name="get-started-with-desired-state-configuration-dsc-for-windows"></a><span data-ttu-id="e2a10-103">Aan de slag met de desired state Configuration (DSC) voor Windows</span><span class="sxs-lookup"><span data-stu-id="e2a10-103">Get started with Desired State Configuration (DSC) for Windows</span></span>

<span data-ttu-id="e2a10-104">In dit onderwerp wordt uitgelegd hoe u aan de slag kunt gaan met behulp van Power shell desired state Configuration (DSC) voor Windows.</span><span class="sxs-lookup"><span data-stu-id="e2a10-104">This topic explains how to get started using PowerShell Desired State Configuration (DSC) for Windows.</span></span>
<span data-ttu-id="e2a10-105">Zie [aan de slag met Windows Power shell desired state Configuration](../overview/overview.md)(Engelstalig) voor algemene informatie over DSC.</span><span class="sxs-lookup"><span data-stu-id="e2a10-105">For general information about DSC, see [Get Started with Windows PowerShell Desired State Configuration](../overview/overview.md).</span></span>

## <a name="supported-windows-operation-system-versions"></a><span data-ttu-id="e2a10-106">Ondersteunde versies van Windows-besturings systeem</span><span class="sxs-lookup"><span data-stu-id="e2a10-106">Supported Windows operation system versions</span></span>

<span data-ttu-id="e2a10-107">De volgende versies worden ondersteund:</span><span class="sxs-lookup"><span data-stu-id="e2a10-107">The following versions are supported:</span></span>

- <span data-ttu-id="e2a10-108">Windows Server 2019</span><span class="sxs-lookup"><span data-stu-id="e2a10-108">Windows Server 2019</span></span>
- <span data-ttu-id="e2a10-109">Windows Server 2016</span><span class="sxs-lookup"><span data-stu-id="e2a10-109">Windows Server 2016</span></span>
- <span data-ttu-id="e2a10-110">Windows Server 2012R2</span><span class="sxs-lookup"><span data-stu-id="e2a10-110">Windows Server 2012R2</span></span>
- <span data-ttu-id="e2a10-111">Windows Server 2012</span><span class="sxs-lookup"><span data-stu-id="e2a10-111">Windows Server 2012</span></span>
- <span data-ttu-id="e2a10-112">Windows Server 2008 R2 SP1</span><span class="sxs-lookup"><span data-stu-id="e2a10-112">Windows Server 2008 R2 SP1</span></span>
- <span data-ttu-id="e2a10-113">Windows 10</span><span class="sxs-lookup"><span data-stu-id="e2a10-113">Windows 10</span></span>
- <span data-ttu-id="e2a10-114">Windows 8.1</span><span class="sxs-lookup"><span data-stu-id="e2a10-114">Windows 8.1</span></span>
- <span data-ttu-id="e2a10-115">Windows 7</span><span class="sxs-lookup"><span data-stu-id="e2a10-115">Windows 7</span></span>

<span data-ttu-id="e2a10-116">De zelfstandige product-SKU van [Microsoft Hyper-V Server](/windows-server/virtualization/hyper-v/hyper-v-server-2016) bevat geen implementatie van de desired state configuratie zodat deze niet kan worden beheerd door Power shell DSC of Azure Automation status configuratie.</span><span class="sxs-lookup"><span data-stu-id="e2a10-116">The [Microsoft Hyper-V Server](/windows-server/virtualization/hyper-v/hyper-v-server-2016) standalone product sku doesn't contain an implementation of Desired State Configuration so it cannot be managed by PowerShell DSC or Azure Automation State Configuration.</span></span>

## <a name="installing-dsc"></a><span data-ttu-id="e2a10-117">DSC installeren</span><span class="sxs-lookup"><span data-stu-id="e2a10-117">Installing DSC</span></span>

<span data-ttu-id="e2a10-118">De gewenste status configuratie van Power shell is opgenomen in Windows en bijgewerkt via Windows Management Framework.</span><span class="sxs-lookup"><span data-stu-id="e2a10-118">PowerShell Desired State Configuration is included in Windows and updated through Windows Management Framework.</span></span> <span data-ttu-id="e2a10-119">De nieuwste versie is [Windows Management Framework 5,1](https://www.microsoft.com/en-us/download/details.aspx?id=54616).</span><span class="sxs-lookup"><span data-stu-id="e2a10-119">The latest version is [Windows Management Framework 5.1](https://www.microsoft.com/en-us/download/details.aspx?id=54616).</span></span>

> [!NOTE]
> <span data-ttu-id="e2a10-120">U hoeft de Windows Server-functie DSC-service niet in te scha kelen om een machine te beheren met behulp van DSC.</span><span class="sxs-lookup"><span data-stu-id="e2a10-120">You do not need to enable the Windows Server feature 'DSC-Service' to manage a machine using DSC.</span></span>
> <span data-ttu-id="e2a10-121">Deze functie is alleen nodig bij het bouwen van een Windows pull-Server exemplaar.</span><span class="sxs-lookup"><span data-stu-id="e2a10-121">That feature is only needed when building a Windows Pull Server instance.</span></span>

## <a name="using-dsc-for-windows"></a><span data-ttu-id="e2a10-122">DSC voor Windows gebruiken</span><span class="sxs-lookup"><span data-stu-id="e2a10-122">Using DSC for Windows</span></span>

<span data-ttu-id="e2a10-123">In de volgende secties wordt uitgelegd hoe u DSC-configuraties maakt en uitvoert op Windows-computers.</span><span class="sxs-lookup"><span data-stu-id="e2a10-123">The following sections explain how to create and run DSC configurations on Windows computers.</span></span>

### <a name="creating-a-configuration-mof-document"></a><span data-ttu-id="e2a10-124">Een configuratie-MOF-document maken</span><span class="sxs-lookup"><span data-stu-id="e2a10-124">Creating a configuration MOF document</span></span>

<span data-ttu-id="e2a10-125">Het sleutel woord `Configuration` van Windows Power shell wordt gebruikt om een configuratie te maken.</span><span class="sxs-lookup"><span data-stu-id="e2a10-125">The Windows PowerShell `Configuration` keyword is used to create a configuration.</span></span>
<span data-ttu-id="e2a10-126">De volgende stappen beschrijven het maken van een configuratie document met behulp van Windows Power shell.</span><span class="sxs-lookup"><span data-stu-id="e2a10-126">The following steps describe the creation of a configuration document using Windows PowerShell.</span></span>

#### <a name="define-a-configuration-and-generate-the-configuration-document"></a><span data-ttu-id="e2a10-127">Definieer een configuratie en Genereer het configuratie document:</span><span class="sxs-lookup"><span data-stu-id="e2a10-127">Define a configuration and generate the configuration document:</span></span>

```powershell
Configuration EnvironmentVariable_Path
{
    param ()

    Import-DscResource -ModuleName 'PSDscResources'

    Node localhost
    {
        Environment CreatePathEnvironmentVariable
        {
            Name = 'TestPathEnvironmentVariable'
            Value = 'TestValue'
            Ensure = 'Present'
            Path = $true
            Target = @('Process', 'Machine')
        }
    }
}

EnvironmentVariable_Path -OutputPath:"C:\EnvironmentVariable_Path"
```

#### <a name="install-a-module-containing-dsc-resources"></a><span data-ttu-id="e2a10-128">Een module met DSC-resources installeren</span><span class="sxs-lookup"><span data-stu-id="e2a10-128">Install a module containing DSC resources</span></span>

<span data-ttu-id="e2a10-129">Windows Power shell desired state Configuration bevat ingebouwde modules met DSC-resources.</span><span class="sxs-lookup"><span data-stu-id="e2a10-129">Windows PowerShell Desired State Configuration includes built-in modules containing DSC resources.</span></span>
<span data-ttu-id="e2a10-130">U kunt ook modules laden vanuit externe bronnen, zoals de PowerShell Gallery, met behulp van de PowerShellGet-cmdlets.</span><span class="sxs-lookup"><span data-stu-id="e2a10-130">You can also load modules from external sources such as the PowerShell Gallery, using the PowerShellGet cmdlets.</span></span>

```PowerShell
Install-Module 'PSDscResources' -Verbose
```

#### <a name="apply-the-configuration-to-the-machine"></a><span data-ttu-id="e2a10-131">De configuratie Toep assen op de computer</span><span class="sxs-lookup"><span data-stu-id="e2a10-131">Apply the configuration to the machine</span></span>

> [!NOTE]
> <span data-ttu-id="e2a10-132">Om DSC te kunnen uitvoeren, moet Windows worden geconfigureerd om externe Power shell-opdrachten te ontvangen, zelfs wanneer u een `localhost` configuratie uitvoert.</span><span class="sxs-lookup"><span data-stu-id="e2a10-132">To allow DSC to run, Windows needs to be configured to receive PowerShell remote commands even when you're running a `localhost` configuration.</span></span> <span data-ttu-id="e2a10-133">Als u uw omgeving eenvoudig wilt configureren, voert u `Set-WsManQuickConfig -Force` uit in een Power shell-terminal met verhoogde bevoegdheden.</span><span class="sxs-lookup"><span data-stu-id="e2a10-133">To easily configure your environment correctly, just run `Set-WsManQuickConfig -Force` in an elevated PowerShell Terminal.</span></span>

<span data-ttu-id="e2a10-134">Configuratie documenten (MOF-bestanden) kunnen worden toegepast op de machineusing van de cmdlet [Start-DscConfiguration](/powershell/module/psdesiredstateconfiguration/start-dscconfiguration) .</span><span class="sxs-lookup"><span data-stu-id="e2a10-134">Configuration documents (MOF files) can be applied to the machineusing the [Start-DscConfiguration](/powershell/module/psdesiredstateconfiguration/start-dscconfiguration) cmdlet.</span></span>

```powershell
Start-DscConfiguration -Path 'C:\EnvironmentVariable_Path' -Wait -Verbose
```

#### <a name="get-the-current-state-of-the-configuration"></a><span data-ttu-id="e2a10-135">De huidige status van de configuratie ophalen</span><span class="sxs-lookup"><span data-stu-id="e2a10-135">Get the current state of the configuration</span></span>

<span data-ttu-id="e2a10-136">De cmdlet [Get-DscConfiguration](/powershell/module/psdesiredstateconfiguration/get-dscconfiguration) voert een query uit op de huidige status van de machine en retourneert de huidige waarden voor de configuratie.</span><span class="sxs-lookup"><span data-stu-id="e2a10-136">The [Get-DscConfiguration](/powershell/module/psdesiredstateconfiguration/get-dscconfiguration) cmdlet queries the current status of the machine and returns the current values for the configuration.</span></span>

```powershell
Get-DscConfiguration
```

<span data-ttu-id="e2a10-137">De cmdlet [Get-DscLocalConfigurationManager](/powershell/module/psdesiredstateconfiguration/get-dscLocalConfigurationManager) retourneert de huidige meta-configuratie die is toegepast op de computer.</span><span class="sxs-lookup"><span data-stu-id="e2a10-137">The [Get-DscLocalConfigurationManager](/powershell/module/psdesiredstateconfiguration/get-dscLocalConfigurationManager) cmdlet returns the current meta-configuration applied to the machine.</span></span>

```powershell
Get-DscLocalConfigurationManager
```

#### <a name="remove-the-current-configuration-from-a-machine"></a><span data-ttu-id="e2a10-138">De huidige configuratie van een machine verwijderen</span><span class="sxs-lookup"><span data-stu-id="e2a10-138">Remove the current configuration from a machine</span></span>

<span data-ttu-id="e2a10-139">De [Remove-DscConfigurationDocument](/powershell/module/psdesiredstateconfiguration/remove-dscconfigurationdocument)</span><span class="sxs-lookup"><span data-stu-id="e2a10-139">The [Remove-DscConfigurationDocument](/powershell/module/psdesiredstateconfiguration/remove-dscconfigurationdocument)</span></span>

```powershell
Remove-DscConfigurationDocument -Stage Current -Verbose
```

#### <a name="configure-settings-in-local-configuration-manager"></a><span data-ttu-id="e2a10-140">Instellingen in lokale Configuration Manager configureren</span><span class="sxs-lookup"><span data-stu-id="e2a10-140">Configure settings in Local Configuration Manager</span></span>

<span data-ttu-id="e2a10-141">Pas een MOF-bestand met de meta configuratie toe met de cmdlet [set-DSCLocalConfigurationManager](/powershell/module/PSDesiredStateConfiguration/Set-DscLocalConfigurationManager) .</span><span class="sxs-lookup"><span data-stu-id="e2a10-141">Apply a Meta Configuration MOF file to the machine using the [Set-DSCLocalConfigurationManager](/powershell/module/PSDesiredStateConfiguration/Set-DscLocalConfigurationManager) cmdlet.</span></span>
<span data-ttu-id="e2a10-142">Vereist het pad naar de meta configuratie-MOF.</span><span class="sxs-lookup"><span data-stu-id="e2a10-142">Requires the path to the Meta Configuration MOF.</span></span>

```powershell
Set-DSCLocalConfigurationManager -Path 'c:\metaconfig\localhost.meta.mof' -Verbose
```

## <a name="windows-powershell-desired-state-configuration-log-files"></a><span data-ttu-id="e2a10-143">Windows Power shell desired state Configuration-logboek bestanden</span><span class="sxs-lookup"><span data-stu-id="e2a10-143">Windows PowerShell Desired State Configuration log files</span></span>

<span data-ttu-id="e2a10-144">Logboeken voor DSC worden naar het Windows-gebeurtenis logboek geschreven in het pad `Microsoft-Windows-Dsc/Operational`.</span><span class="sxs-lookup"><span data-stu-id="e2a10-144">Logs for DSC are written to Windows Event Log in the path `Microsoft-Windows-Dsc/Operational`.</span></span>
<span data-ttu-id="e2a10-145">Aanvullende logboeken voor fout opsporing kunnen worden ingeschakeld Volg de stappen in [waar vindt u de logboeken van DSC-gebeurtenissen](/powershell/scripting/dsc/troubleshooting/troubleshooting#where-are-dsc-event-logs).</span><span class="sxs-lookup"><span data-stu-id="e2a10-145">Additional logs for debugging purposes can be enabled following the steps in [Where Are DSC Event Logs](/powershell/scripting/dsc/troubleshooting/troubleshooting#where-are-dsc-event-logs).</span></span>
