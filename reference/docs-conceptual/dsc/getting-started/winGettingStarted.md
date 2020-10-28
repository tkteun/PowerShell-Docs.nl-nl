---
ms.date: 08/15/2019
keywords: DSC, Power shell, configuratie, installatie
title: Aan de slag met de desired state Configuration (DSC) voor Windows
description: In dit onderwerp wordt uitgelegd hoe u aan de slag kunt gaan met behulp van Power shell desired state Configuration (DSC) voor Windows.
ms.openlocfilehash: 2b9ddba2023a3933e3ad70d7bfee798ff07f0484
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/27/2020
ms.locfileid: "92662821"
---
# <a name="get-started-with-desired-state-configuration-dsc-for-windows"></a><span data-ttu-id="adaad-104">Aan de slag met de desired state Configuration (DSC) voor Windows</span><span class="sxs-lookup"><span data-stu-id="adaad-104">Get started with Desired State Configuration (DSC) for Windows</span></span>

<span data-ttu-id="adaad-105">In dit onderwerp wordt uitgelegd hoe u aan de slag kunt gaan met behulp van Power shell desired state Configuration (DSC) voor Windows.</span><span class="sxs-lookup"><span data-stu-id="adaad-105">This topic explains how to get started using PowerShell Desired State Configuration (DSC) for Windows.</span></span> <span data-ttu-id="adaad-106">Zie [aan de slag met Windows Power shell desired state Configuration](../overview/overview.md)(Engelstalig) voor algemene informatie over DSC.</span><span class="sxs-lookup"><span data-stu-id="adaad-106">For general information about DSC, see [Get Started with Windows PowerShell Desired State Configuration](../overview/overview.md).</span></span>

## <a name="supported-windows-operation-system-versions"></a><span data-ttu-id="adaad-107">Ondersteunde versies van Windows-besturings systeem</span><span class="sxs-lookup"><span data-stu-id="adaad-107">Supported Windows operation system versions</span></span>

<span data-ttu-id="adaad-108">De volgende versies worden ondersteund:</span><span class="sxs-lookup"><span data-stu-id="adaad-108">The following versions are supported:</span></span>

- <span data-ttu-id="adaad-109">Windows Server 2019</span><span class="sxs-lookup"><span data-stu-id="adaad-109">Windows Server 2019</span></span>
- <span data-ttu-id="adaad-110">Windows Server 2016</span><span class="sxs-lookup"><span data-stu-id="adaad-110">Windows Server 2016</span></span>
- <span data-ttu-id="adaad-111">Windows Server-2012R2</span><span class="sxs-lookup"><span data-stu-id="adaad-111">Windows Server 2012R2</span></span>
- <span data-ttu-id="adaad-112">Windows Server 2012</span><span class="sxs-lookup"><span data-stu-id="adaad-112">Windows Server 2012</span></span>
- <span data-ttu-id="adaad-113">Windows Server 2008 R2 SP1</span><span class="sxs-lookup"><span data-stu-id="adaad-113">Windows Server 2008 R2 SP1</span></span>
- <span data-ttu-id="adaad-114">Windows 10</span><span class="sxs-lookup"><span data-stu-id="adaad-114">Windows 10</span></span>
- <span data-ttu-id="adaad-115">Windows 8.1</span><span class="sxs-lookup"><span data-stu-id="adaad-115">Windows 8.1</span></span>
- <span data-ttu-id="adaad-116">Windows 7</span><span class="sxs-lookup"><span data-stu-id="adaad-116">Windows 7</span></span>

<span data-ttu-id="adaad-117">De zelfstandige product-SKU van [Microsoft Hyper-V Server](/windows-server/virtualization/hyper-v/hyper-v-server-2016) bevat geen implementatie van de desired state configuratie zodat deze niet kan worden beheerd door Power shell DSC of Azure Automation status configuratie.</span><span class="sxs-lookup"><span data-stu-id="adaad-117">The [Microsoft Hyper-V Server](/windows-server/virtualization/hyper-v/hyper-v-server-2016) standalone product sku doesn't contain an implementation of Desired State Configuration so it cannot be managed by PowerShell DSC or Azure Automation State Configuration.</span></span>

## <a name="installing-dsc"></a><span data-ttu-id="adaad-118">DSC installeren</span><span class="sxs-lookup"><span data-stu-id="adaad-118">Installing DSC</span></span>

<span data-ttu-id="adaad-119">De gewenste status configuratie van Power shell is opgenomen in Windows en bijgewerkt via Windows Management Framework.</span><span class="sxs-lookup"><span data-stu-id="adaad-119">PowerShell Desired State Configuration is included in Windows and updated through Windows Management Framework.</span></span> <span data-ttu-id="adaad-120">De nieuwste versie is [Windows Management Framework 5,1](https://www.microsoft.com/download/details.aspx?id=54616).</span><span class="sxs-lookup"><span data-stu-id="adaad-120">The latest version is [Windows Management Framework 5.1](https://www.microsoft.com/download/details.aspx?id=54616).</span></span>

> [!NOTE]
> <span data-ttu-id="adaad-121">U hoeft de Windows Server-functie DSC-service niet in te scha kelen om een machine te beheren met behulp van DSC.</span><span class="sxs-lookup"><span data-stu-id="adaad-121">You do not need to enable the Windows Server feature 'DSC-Service' to manage a machine using DSC.</span></span>
> <span data-ttu-id="adaad-122">Deze functie is alleen nodig bij het bouwen van een Windows pull-Server exemplaar.</span><span class="sxs-lookup"><span data-stu-id="adaad-122">That feature is only needed when building a Windows Pull Server instance.</span></span>

## <a name="using-dsc-for-windows"></a><span data-ttu-id="adaad-123">DSC voor Windows gebruiken</span><span class="sxs-lookup"><span data-stu-id="adaad-123">Using DSC for Windows</span></span>

<span data-ttu-id="adaad-124">In de volgende secties wordt uitgelegd hoe u DSC-configuraties maakt en uitvoert op Windows-computers.</span><span class="sxs-lookup"><span data-stu-id="adaad-124">The following sections explain how to create and run DSC configurations on Windows computers.</span></span>

### <a name="creating-a-configuration-mof-document"></a><span data-ttu-id="adaad-125">Een configuratie-MOF-document maken</span><span class="sxs-lookup"><span data-stu-id="adaad-125">Creating a configuration MOF document</span></span>

<span data-ttu-id="adaad-126">Het sleutel woord Windows Power shell `Configuration` wordt gebruikt om een configuratie te maken.</span><span class="sxs-lookup"><span data-stu-id="adaad-126">The Windows PowerShell `Configuration` keyword is used to create a configuration.</span></span>
<span data-ttu-id="adaad-127">De volgende stappen beschrijven het maken van een configuratie document met behulp van Windows Power shell.</span><span class="sxs-lookup"><span data-stu-id="adaad-127">The following steps describe the creation of a configuration document using Windows PowerShell.</span></span>

#### <a name="define-a-configuration-and-generate-the-configuration-document"></a><span data-ttu-id="adaad-128">Definieer een configuratie en Genereer het configuratie document:</span><span class="sxs-lookup"><span data-stu-id="adaad-128">Define a configuration and generate the configuration document:</span></span>

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

#### <a name="install-a-module-containing-dsc-resources"></a><span data-ttu-id="adaad-129">Een module met DSC-resources installeren</span><span class="sxs-lookup"><span data-stu-id="adaad-129">Install a module containing DSC resources</span></span>

<span data-ttu-id="adaad-130">Windows Power shell desired state Configuration bevat ingebouwde modules met DSC-resources.</span><span class="sxs-lookup"><span data-stu-id="adaad-130">Windows PowerShell Desired State Configuration includes built-in modules containing DSC resources.</span></span>
<span data-ttu-id="adaad-131">U kunt ook modules laden vanuit externe bronnen, zoals de PowerShell Gallery, met behulp van de PowerShellGet-cmdlets.</span><span class="sxs-lookup"><span data-stu-id="adaad-131">You can also load modules from external sources such as the PowerShell Gallery, using the PowerShellGet cmdlets.</span></span>

```PowerShell
Install-Module 'PSDscResources' -Verbose
```

#### <a name="apply-the-configuration-to-the-machine"></a><span data-ttu-id="adaad-132">De configuratie Toep assen op de computer</span><span class="sxs-lookup"><span data-stu-id="adaad-132">Apply the configuration to the machine</span></span>

> [!NOTE]
> <span data-ttu-id="adaad-133">Om DSC te kunnen uitvoeren, moet Windows worden geconfigureerd om externe Power shell-opdrachten te ontvangen, zelfs wanneer u een `localhost` configuratie uitvoert.</span><span class="sxs-lookup"><span data-stu-id="adaad-133">To allow DSC to run, Windows needs to be configured to receive PowerShell remote commands even when you're running a `localhost` configuration.</span></span> <span data-ttu-id="adaad-134">Als u uw omgeving eenvoudig op de juiste wijze wilt configureren, voert u de opdracht `Set-WsManQuickConfig -Force` uit in een Power shell-terminal met verhoogde bevoegdheden.</span><span class="sxs-lookup"><span data-stu-id="adaad-134">To easily configure your environment correctly, just run `Set-WsManQuickConfig -Force` in an elevated PowerShell Terminal.</span></span>

<span data-ttu-id="adaad-135">Configuratie documenten (MOF-bestanden) kunnen worden toegepast op de machineusing van de cmdlet [Start-DscConfiguration](/powershell/module/psdesiredstateconfiguration/start-dscconfiguration) .</span><span class="sxs-lookup"><span data-stu-id="adaad-135">Configuration documents (MOF files) can be applied to the machineusing the [Start-DscConfiguration](/powershell/module/psdesiredstateconfiguration/start-dscconfiguration) cmdlet.</span></span>

```powershell
Start-DscConfiguration -Path 'C:\EnvironmentVariable_Path' -Wait -Verbose
```

#### <a name="get-the-current-state-of-the-configuration"></a><span data-ttu-id="adaad-136">De huidige status van de configuratie ophalen</span><span class="sxs-lookup"><span data-stu-id="adaad-136">Get the current state of the configuration</span></span>

<span data-ttu-id="adaad-137">De cmdlet [Get-DscConfiguration](/powershell/module/psdesiredstateconfiguration/get-dscconfiguration) voert een query uit op de huidige status van de machine en retourneert de huidige waarden voor de configuratie.</span><span class="sxs-lookup"><span data-stu-id="adaad-137">The [Get-DscConfiguration](/powershell/module/psdesiredstateconfiguration/get-dscconfiguration) cmdlet queries the current status of the machine and returns the current values for the configuration.</span></span>

```powershell
Get-DscConfiguration
```

<span data-ttu-id="adaad-138">De cmdlet [Get-DscLocalConfigurationManager](/powershell/module/psdesiredstateconfiguration/get-dscLocalConfigurationManager) retourneert de huidige meta-configuratie die is toegepast op de computer.</span><span class="sxs-lookup"><span data-stu-id="adaad-138">The [Get-DscLocalConfigurationManager](/powershell/module/psdesiredstateconfiguration/get-dscLocalConfigurationManager) cmdlet returns the current meta-configuration applied to the machine.</span></span>

```powershell
Get-DscLocalConfigurationManager
```

#### <a name="remove-the-current-configuration-from-a-machine"></a><span data-ttu-id="adaad-139">De huidige configuratie van een machine verwijderen</span><span class="sxs-lookup"><span data-stu-id="adaad-139">Remove the current configuration from a machine</span></span>

<span data-ttu-id="adaad-140">De [Remove-DscConfigurationDocument](/powershell/module/psdesiredstateconfiguration/remove-dscconfigurationdocument)</span><span class="sxs-lookup"><span data-stu-id="adaad-140">The [Remove-DscConfigurationDocument](/powershell/module/psdesiredstateconfiguration/remove-dscconfigurationdocument)</span></span>

```powershell
Remove-DscConfigurationDocument -Stage Current -Verbose
```

#### <a name="configure-settings-in-local-configuration-manager"></a><span data-ttu-id="adaad-141">Instellingen in lokale Configuration Manager configureren</span><span class="sxs-lookup"><span data-stu-id="adaad-141">Configure settings in Local Configuration Manager</span></span>

<span data-ttu-id="adaad-142">Pas een MOF-bestand met de meta configuratie toe met de cmdlet [set-DSCLocalConfigurationManager](/powershell/module/PSDesiredStateConfiguration/Set-DscLocalConfigurationManager) .</span><span class="sxs-lookup"><span data-stu-id="adaad-142">Apply a Meta Configuration MOF file to the machine using the [Set-DSCLocalConfigurationManager](/powershell/module/PSDesiredStateConfiguration/Set-DscLocalConfigurationManager) cmdlet.</span></span> <span data-ttu-id="adaad-143">Vereist het pad naar de meta configuratie-MOF.</span><span class="sxs-lookup"><span data-stu-id="adaad-143">Requires the path to the Meta Configuration MOF.</span></span>

```powershell
Set-DSCLocalConfigurationManager -Path 'c:\metaconfig\localhost.meta.mof' -Verbose
```

## <a name="windows-powershell-desired-state-configuration-log-files"></a><span data-ttu-id="adaad-144">Windows Power shell desired state Configuration-logboek bestanden</span><span class="sxs-lookup"><span data-stu-id="adaad-144">Windows PowerShell Desired State Configuration log files</span></span>

<span data-ttu-id="adaad-145">Logboeken voor DSC worden in het pad naar het Windows-gebeurtenis logboek geschreven `Microsoft-Windows-Dsc/Operational` .</span><span class="sxs-lookup"><span data-stu-id="adaad-145">Logs for DSC are written to Windows Event Log in the path `Microsoft-Windows-Dsc/Operational`.</span></span>
<span data-ttu-id="adaad-146">Aanvullende logboeken voor fout opsporing kunnen worden ingeschakeld Volg de stappen in [waar vindt u de logboeken van DSC-gebeurtenissen](/powershell/scripting/dsc/troubleshooting/troubleshooting#where-are-dsc-event-logs).</span><span class="sxs-lookup"><span data-stu-id="adaad-146">Additional logs for debugging purposes can be enabled following the steps in [Where Are DSC Event Logs](/powershell/scripting/dsc/troubleshooting/troubleshooting#where-are-dsc-event-logs).</span></span>
