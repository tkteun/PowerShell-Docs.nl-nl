---
ms.date: 08/15/2019
keywords: dsc,powershell,configuration,setup
title: Get started with Desired State Configuration (DSC) for Windows
ms.openlocfilehash: a9346b96693acdbad9bacbd4b6ca85971e17a3d1
ms.sourcegitcommit: d43f66071f1f33b350d34fa1f46f3a35910c5d24
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 11/23/2019
ms.locfileid: "74417763"
---
# <a name="get-started-with-desired-state-configuration-dsc-for-windows"></a><span data-ttu-id="3ba76-103">Get started with Desired State Configuration (DSC) for Windows</span><span class="sxs-lookup"><span data-stu-id="3ba76-103">Get started with Desired State Configuration (DSC) for Windows</span></span>

<span data-ttu-id="3ba76-104">This topic explains how to get started using PowerShell Desired State Configuration (DSC) for Windows.</span><span class="sxs-lookup"><span data-stu-id="3ba76-104">This topic explains how to get started using PowerShell Desired State Configuration (DSC) for Windows.</span></span>
<span data-ttu-id="3ba76-105">For general information about DSC, see [Get Started with Windows PowerShell Desired State Configuration](../overview/overview.md).</span><span class="sxs-lookup"><span data-stu-id="3ba76-105">For general information about DSC, see [Get Started with Windows PowerShell Desired State Configuration](../overview/overview.md).</span></span>

## <a name="supported-windows-operation-system-versions"></a><span data-ttu-id="3ba76-106">Supported Windows operation system versions</span><span class="sxs-lookup"><span data-stu-id="3ba76-106">Supported Windows operation system versions</span></span>

<span data-ttu-id="3ba76-107">The following versions are supported:</span><span class="sxs-lookup"><span data-stu-id="3ba76-107">The following versions are supported:</span></span>

- <span data-ttu-id="3ba76-108">Windows Server 2019</span><span class="sxs-lookup"><span data-stu-id="3ba76-108">Windows Server 2019</span></span>
- <span data-ttu-id="3ba76-109">Windows Server 2016</span><span class="sxs-lookup"><span data-stu-id="3ba76-109">Windows Server 2016</span></span>
- <span data-ttu-id="3ba76-110">Windows Server 2012R2</span><span class="sxs-lookup"><span data-stu-id="3ba76-110">Windows Server 2012R2</span></span>
- <span data-ttu-id="3ba76-111">Windows Server 2012</span><span class="sxs-lookup"><span data-stu-id="3ba76-111">Windows Server 2012</span></span>
- <span data-ttu-id="3ba76-112">Windows Server 2008 R2 SP1</span><span class="sxs-lookup"><span data-stu-id="3ba76-112">Windows Server 2008 R2 SP1</span></span>
- <span data-ttu-id="3ba76-113">Windows 10</span><span class="sxs-lookup"><span data-stu-id="3ba76-113">Windows 10</span></span>
- <span data-ttu-id="3ba76-114">Windows 8.1</span><span class="sxs-lookup"><span data-stu-id="3ba76-114">Windows 8.1</span></span>
- <span data-ttu-id="3ba76-115">Windows 7</span><span class="sxs-lookup"><span data-stu-id="3ba76-115">Windows 7</span></span>

<span data-ttu-id="3ba76-116">The [Microsoft Hyper-V Server](/windows-server/virtualization/hyper-v/hyper-v-server-2016) standalone product sku does not contain an implementation of Desired State Configuraion so it cannot be managed by PowerShell DSC or Azure Automation State Configuration.</span><span class="sxs-lookup"><span data-stu-id="3ba76-116">The [Microsoft Hyper-V Server](/windows-server/virtualization/hyper-v/hyper-v-server-2016) standalone product sku does not contain an implementation of Desired State Configuraion so it cannot be managed by PowerShell DSC or Azure Automation State Configuration.</span></span>

## <a name="installing-dsc"></a><span data-ttu-id="3ba76-117">Installing DSC</span><span class="sxs-lookup"><span data-stu-id="3ba76-117">Installing DSC</span></span>

<span data-ttu-id="3ba76-118">PowerShell Desired State Configuration is included in Windows and updated through Windows Management Framework.</span><span class="sxs-lookup"><span data-stu-id="3ba76-118">PowerShell Desired State Configuration is included in Windows and updated through Windows Management Framework.</span></span>
<span data-ttu-id="3ba76-119">The latest version is [Windows Management Framework 5.1](https://www.microsoft.com/en-us/download/details.aspx?id=54616).</span><span class="sxs-lookup"><span data-stu-id="3ba76-119">The latest version is [Windows Management Framework 5.1](https://www.microsoft.com/en-us/download/details.aspx?id=54616).</span></span>

> [!NOTE]
> <span data-ttu-id="3ba76-120">You do not need to enable the Windows Server feature 'DSC-Service' to manage a machine using DSC.</span><span class="sxs-lookup"><span data-stu-id="3ba76-120">You do not need to enable the Windows Server feature 'DSC-Service' to manage a machine using DSC.</span></span>
> <span data-ttu-id="3ba76-121">That feature is only needed when building a Windows Pull Server instance.</span><span class="sxs-lookup"><span data-stu-id="3ba76-121">That feature is only needed when building a Windows Pull Server instance.</span></span>

## <a name="using-dsc-for-windows"></a><span data-ttu-id="3ba76-122">Using DSC for Windows</span><span class="sxs-lookup"><span data-stu-id="3ba76-122">Using DSC for Windows</span></span>

<span data-ttu-id="3ba76-123">The following sections explain how to create and run DSC configurations on Windows computers.</span><span class="sxs-lookup"><span data-stu-id="3ba76-123">The following sections explain how to create and run DSC configurations on Windows computers.</span></span>

### <a name="creating-a-configuration-mof-document"></a><span data-ttu-id="3ba76-124">Creating a configuration MOF document</span><span class="sxs-lookup"><span data-stu-id="3ba76-124">Creating a configuration MOF document</span></span>

<span data-ttu-id="3ba76-125">The Windows PowerShell Configuration keyword is used to create a configuration.</span><span class="sxs-lookup"><span data-stu-id="3ba76-125">The Windows PowerShell Configuration keyword is used to create a configuration.</span></span>
<span data-ttu-id="3ba76-126">The following steps describe the creation of a configuration document using Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="3ba76-126">The following steps describe the creation of a configuration document using Windows PowerShell.</span></span>

#### <a name="define-a-configuration-and-generate-the-configuration-document"></a><span data-ttu-id="3ba76-127">Define a configuration and generate the configuration document:</span><span class="sxs-lookup"><span data-stu-id="3ba76-127">Define a configuration and generate the configuration document:</span></span>

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
#### <a name="install-a-module-containing-dsc-resources"></a><span data-ttu-id="3ba76-128">Install a module containing DSC resources</span><span class="sxs-lookup"><span data-stu-id="3ba76-128">Install a module containing DSC resources</span></span>

<span data-ttu-id="3ba76-129">Windows PowerShell Desired State Configuration includes built-in modules containing DSC resources.</span><span class="sxs-lookup"><span data-stu-id="3ba76-129">Windows PowerShell Desired State Configuration includes built-in modules containing DSC resources.</span></span>
<span data-ttu-id="3ba76-130">You can also load modules from external sources such as the PowerShell Gallery, using the PowerShellGet cmdlets.</span><span class="sxs-lookup"><span data-stu-id="3ba76-130">You can also load modules from external sources such as the PowerShell Gallery, using the PowerShellGet cmdlets.</span></span>

`Install-Module 'PSDscResources' -Verbose`

#### <a name="apply-the-configuration-to-the-machine"></a><span data-ttu-id="3ba76-131">Apply the configuration to the machine</span><span class="sxs-lookup"><span data-stu-id="3ba76-131">Apply the configuration to the machine</span></span>

<span data-ttu-id="3ba76-132">Configuration documents (MOF files) can be applied to the machine using the [Start-DscConfiguration](/powershell/module/psdesiredstateconfiguration/start-dscconfiguration) cmdlet.</span><span class="sxs-lookup"><span data-stu-id="3ba76-132">Configuration documents (MOF files) can be applied to the machine using the [Start-DscConfiguration](/powershell/module/psdesiredstateconfiguration/start-dscconfiguration) cmdlet.</span></span>

`Start-DscConfiguration -Path 'C:\EnvironmentVariable_Path' -Wait -Verbose`

#### <a name="get-the-current-state-of-the-configuration"></a><span data-ttu-id="3ba76-133">Get the current state of the configuration</span><span class="sxs-lookup"><span data-stu-id="3ba76-133">Get the current state of the configuration</span></span>

<span data-ttu-id="3ba76-134">The [Get-DscConfiguration](/powershell/module/psdesiredstateconfiguration/get-dscconfiguration) cmdlet queries the current status of the machine and returns the current values for the configuration.</span><span class="sxs-lookup"><span data-stu-id="3ba76-134">The [Get-DscConfiguration](/powershell/module/psdesiredstateconfiguration/get-dscconfiguration) cmdlet queries the current status of the machine and returns the current values for the configuration.</span></span>

`Get-DscConfiguration`

<span data-ttu-id="3ba76-135">The [Get-DscLocalConfigurationManager](/powershell/module/psdesiredstateconfiguration/get-dscLocalConfigurationManager) cmdlet returns the current meta-configuration applied to the machine.</span><span class="sxs-lookup"><span data-stu-id="3ba76-135">The [Get-DscLocalConfigurationManager](/powershell/module/psdesiredstateconfiguration/get-dscLocalConfigurationManager) cmdlet returns the current meta-configuration applied to the machine.</span></span>

`Get-DscLocalConfigurationManager`

#### <a name="remove-the-current-configuration-from-a-machine"></a><span data-ttu-id="3ba76-136">Remove the current configuration from a machine</span><span class="sxs-lookup"><span data-stu-id="3ba76-136">Remove the current configuration from a machine</span></span>

<span data-ttu-id="3ba76-137">The [Remove-DscConfigurationDocument](/powershell/module/psdesiredstateconfiguration/remove-dscconfigurationdocument)</span><span class="sxs-lookup"><span data-stu-id="3ba76-137">The [Remove-DscConfigurationDocument](/powershell/module/psdesiredstateconfiguration/remove-dscconfigurationdocument)</span></span>

`Remove-DscConfigurationDocument -Stage Current -Verbose`

#### <a name="configure-settings-in-local-configuration-manager"></a><span data-ttu-id="3ba76-138">Configure settings in Local Configuration Manager</span><span class="sxs-lookup"><span data-stu-id="3ba76-138">Configure settings in Local Configuration Manager</span></span>

<span data-ttu-id="3ba76-139">Apply a Meta Configuration MOF file to the machine using the [Set-DSCLocalConfigurationManager](/powershell/module/PSDesiredStateConfiguration/Set-DscLocalConfigurationManager) cmdlet.</span><span class="sxs-lookup"><span data-stu-id="3ba76-139">Apply a Meta Configuration MOF file to the machine using the [Set-DSCLocalConfigurationManager](/powershell/module/PSDesiredStateConfiguration/Set-DscLocalConfigurationManager) cmdlet.</span></span>
<span data-ttu-id="3ba76-140">Requires the path to the Meta Configuration MOF.</span><span class="sxs-lookup"><span data-stu-id="3ba76-140">Requires the path to the Meta Configuration MOF.</span></span>

`Set-DSCLocalConfigurationManager -Path 'c:\metaconfig\localhost.meta.mof' -Verbose`

## <a name="windows-powershell-desired-state-configuration-log-files"></a><span data-ttu-id="3ba76-141">Windows PowerShell Desired State Configuration log files</span><span class="sxs-lookup"><span data-stu-id="3ba76-141">Windows PowerShell Desired State Configuration log files</span></span>

<span data-ttu-id="3ba76-142">Logs for DSC are written to Windows Event Log in the path `Microsoft-Windows-Dsc/Operational`.</span><span class="sxs-lookup"><span data-stu-id="3ba76-142">Logs for DSC are written to Windows Event Log in the path `Microsoft-Windows-Dsc/Operational`.</span></span>
<span data-ttu-id="3ba76-143">Additional logs for debugging purposes can be enabled following the steps in [Where Are DSC Event Logs](/powershell/scripting/dsc/troubleshooting/troubleshooting#where-are-dsc-event-logs).</span><span class="sxs-lookup"><span data-stu-id="3ba76-143">Additional logs for debugging purposes can be enabled following the steps in [Where Are DSC Event Logs](/powershell/scripting/dsc/troubleshooting/troubleshooting#where-are-dsc-event-logs).</span></span>
