---
ms.date: 2017-06-12
author: eslesar
ms.topic: conceptual
keywords: DSC, powershell, configuratie, setup
title: Een virtuele machines op de eerste boot-up configureren met behulp van DSC
ms.openlocfilehash: a3592c50fa7f2232538fbec07129fac86c1d00b5
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 06/12/2017
---
><span data-ttu-id="25ff5-103">Van toepassing op: Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="25ff5-103">Applies To: Windows PowerShell 5.0</span></span>

><span data-ttu-id="25ff5-104">**Opmerking:** de **DSCAutomationHostEnabled** registersleutel beschreven in dit onderwerp is niet beschikbaar in PowerShell 4.0.</span><span class="sxs-lookup"><span data-stu-id="25ff5-104">**Note:** The **DSCAutomationHostEnabled** registry key described in this topic is not available in PowerShell 4.0.</span></span>
<span data-ttu-id="25ff5-105">Zie voor meer informatie over het configureren van nieuwe virtuele machines op de eerste boot-up in PowerShell 4.0 [automatisch configureren van uw Machines met behulp van DSC op initiële Boot-up wilt?](https://blogs.msdn.microsoft.com/powershell/2014/02/28/want-to-automatically-configure-your-machines-using-dsc-at-initial-boot-up/)</span><span class="sxs-lookup"><span data-stu-id="25ff5-105">For information on how to configure new virtual machines at initial boot-up in PowerShell 4.0, see [Want to Automatically Configure Your Machines Using DSC at Initial Boot-up?](https://blogs.msdn.microsoft.com/powershell/2014/02/28/want-to-automatically-configure-your-machines-using-dsc-at-initial-boot-up/)</span></span>

# <a name="configure-a-virtual-machines-at-initial-boot-up-by-using-dsc"></a><span data-ttu-id="25ff5-106">Een virtuele machines op de eerste boot-up configureren met behulp van DSC</span><span class="sxs-lookup"><span data-stu-id="25ff5-106">Configure a virtual machines at initial boot-up by using DSC</span></span>

## <a name="requirements"></a><span data-ttu-id="25ff5-107">Vereisten</span><span class="sxs-lookup"><span data-stu-id="25ff5-107">Requirements</span></span>

<span data-ttu-id="25ff5-108">Voor het uitvoeren van deze voorbeelden, moet u het:</span><span class="sxs-lookup"><span data-stu-id="25ff5-108">To run these examples, you will need:</span></span>

- <span data-ttu-id="25ff5-109">Een opstartbare VHD werken met.</span><span class="sxs-lookup"><span data-stu-id="25ff5-109">A bootable VHD to work with.</span></span> <span data-ttu-id="25ff5-110">U kunt geen ISO met een evaluatieversie van Windows Server 2016 op downloaden   [TechNet Evaluation Center](https://www.microsoft.com/en-us/evalcenter/evaluate-windows-server-2016).</span><span class="sxs-lookup"><span data-stu-id="25ff5-110">You can download an ISO with an evaluation copy of Windows Server 2016 at   [TechNet Evaluation Center](https://www.microsoft.com/en-us/evalcenter/evaluate-windows-server-2016).</span></span> <span data-ttu-id="25ff5-111">U vindt instructies over het maken van een VHD van een ISO-installatiekopie op [opstartbare virtuele harde schijven maken](https://technet.microsoft.com/en-us/library/gg318049.aspx).</span><span class="sxs-lookup"><span data-stu-id="25ff5-111">You can find instructions on how to create a VHD from an ISO image at [Creating Bootable Virtual Hard Disks](https://technet.microsoft.com/en-us/library/gg318049.aspx).</span></span>
- <span data-ttu-id="25ff5-112">Een hostcomputer waarop Hyper-V is ingeschakeld.</span><span class="sxs-lookup"><span data-stu-id="25ff5-112">A host computer that has Hyper-V enabled.</span></span> <span data-ttu-id="25ff5-113">Zie voor informatie [overzicht Hyper-V](https://technet.microsoft.com/library/hh831531.aspx).</span><span class="sxs-lookup"><span data-stu-id="25ff5-113">For information, see [Hyper-V overview](https://technet.microsoft.com/library/hh831531.aspx).</span></span>

<span data-ttu-id="25ff5-114">U kunt software-installatie en configuratie van een computer op initiële boot-up automatiseren met behulp van DSC.</span><span class="sxs-lookup"><span data-stu-id="25ff5-114">By using DSC, you can automate software installation and configuration for a computer at initial boot-up.</span></span>
<span data-ttu-id="25ff5-115">U doen dit door beide injecteren van een document van de MOF-configuratie of een metaconfiguratie in opstartbare media (zoals een VHD) zodat ze worden uitgevoerd wanneer de eerste keer opstarten-up.</span><span class="sxs-lookup"><span data-stu-id="25ff5-115">You do this by either injecting a configuration MOF document or a metaconfiguration into bootable media (such as a VHD) so that they are run during the initial boot-up process.</span></span>
<span data-ttu-id="25ff5-116">Dit gedrag wordt opgegeven door de [DSCAutomationHostEnabled registersleutel](DSCAutomationHostEnabled.md) registersleutel onder **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion\Policies**.</span><span class="sxs-lookup"><span data-stu-id="25ff5-116">This behavior is specified by the [DSCAutomationHostEnabled registry key](DSCAutomationHostEnabled.md) registry key under **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion\Policies**.</span></span>
<span data-ttu-id="25ff5-117">Standaard is de waarde van deze sleutel 2, waardoor DSC om uit te voeren tijdens het opstarten.</span><span class="sxs-lookup"><span data-stu-id="25ff5-117">By default, the value of this key is 2, which allows DSC to run at boot time.</span></span>

<span data-ttu-id="25ff5-118">Als u niet dat DSC om uit te voeren tijdens het opstarten wilt, stel de waarde van de [DSCAutomationHostEnabled registersleutel](DSCAutomationHostEnabled.md) registersleutel in op 0.</span><span class="sxs-lookup"><span data-stu-id="25ff5-118">If you do not want DSC to run at boot time, set the value of the [DSCAutomationHostEnabled registry key](DSCAutomationHostEnabled.md) registry key to 0.</span></span>

- <span data-ttu-id="25ff5-119">Een configuratie MOF document invoeren in een VHD</span><span class="sxs-lookup"><span data-stu-id="25ff5-119">Inject a configuration MOF document into a VHD</span></span>
- <span data-ttu-id="25ff5-120">DSC-metaconfiguratie toe invoeren in een VHD</span><span class="sxs-lookup"><span data-stu-id="25ff5-120">Inject a DSC metaconfiguration into a VHD</span></span>
- <span data-ttu-id="25ff5-121">DSC tijdens het opstarten uitschakelen</span><span class="sxs-lookup"><span data-stu-id="25ff5-121">Disable DSC at boot time</span></span>

><span data-ttu-id="25ff5-122">**Opmerking:** kunt u beide injecteren `Pending.mof` en `MetaConfig.mof` in een computer op hetzelfde moment.</span><span class="sxs-lookup"><span data-stu-id="25ff5-122">**Note:** You can inject both `Pending.mof` and `MetaConfig.mof` into a computer at the same time.</span></span>
<span data-ttu-id="25ff5-123">Als beide bestanden aanwezig zijn, worden de opgegeven instellingen `MetaConfig.mof` voorrang.</span><span class="sxs-lookup"><span data-stu-id="25ff5-123">If both files are present, the settings specified in `MetaConfig.mof` take precedence.</span></span>

## <a name="inject-a-configuration-mof-document-into-a-vhd"></a><span data-ttu-id="25ff5-124">Een configuratie MOF document invoeren in een VHD</span><span class="sxs-lookup"><span data-stu-id="25ff5-124">Inject a configuration MOF document into a VHD</span></span>

<span data-ttu-id="25ff5-125">Om door te nemen in een configuratie op de eerste boot-up, kunt u een MOF-document gecompileerde configuratie invoeren in de VHD als de `Pending.mof` bestand.</span><span class="sxs-lookup"><span data-stu-id="25ff5-125">To enact a configuration at initial boot-up, you can inject a compiled configuration MOF document into the VHD as its `Pending.mof` file.</span></span>
<span data-ttu-id="25ff5-126">Als de **DSCAutomationHostEnabled** registersleutel is ingesteld op 2 (de standaardwaarde), DSC geldt de configuratie die is gedefinieerd door `Pending.mof` wanneer de computer voor het eerst wordt opgestart.</span><span class="sxs-lookup"><span data-stu-id="25ff5-126">If the **DSCAutomationHostEnabled** registry key is set to 2 (the default value), DSC will apply the configuration defined by `Pending.mof` when the computer boots up for the first time.</span></span>

<span data-ttu-id="25ff5-127">We gebruiken de volgende configuratie waarop IIS wordt geïnstalleerd op de nieuwe computer voor dit voorbeeld:</span><span class="sxs-lookup"><span data-stu-id="25ff5-127">For this example, we will use the following configuration, which will install IIS on the new computer:</span></span>

```powershell
Configuration SampleIISInstall
{
    Import-DscResource -ModuleName 'PSDesiredStateConfiguration'

    node ('localhost')
    {
        WindowsFeature IIS
        {
            Ensure = 'Present'
            Name   = 'Web-Server'
        }
    }
}
```

### <a name="to-inject-the-configuration-mof-document-on-the-vhd"></a><span data-ttu-id="25ff5-128">Het MOF-document van de configuratie op de VHD invoeren</span><span class="sxs-lookup"><span data-stu-id="25ff5-128">To inject the configuration MOF document on the VHD</span></span>

1. <span data-ttu-id="25ff5-129">Koppelen van de VHD waaraan u invoeren van de configuratie wilt door het aanroepen van de [Mount-VHD](https://technet.microsoft.com/library/hh848551.aspx) cmdlet.</span><span class="sxs-lookup"><span data-stu-id="25ff5-129">Mount the VHD into which you want to inject the configuration by calling the [Mount-VHD](https://technet.microsoft.com/library/hh848551.aspx) cmdlet.</span></span> <span data-ttu-id="25ff5-130">Bijvoorbeeld:</span><span class="sxs-lookup"><span data-stu-id="25ff5-130">For example:</span></span>

    ```powershell
    Mount-VHD -Path C:\users\public\documents\vhd\Srv16.vhd
    ```
2. <span data-ttu-id="25ff5-131">Op een computer waarop PowerShell 5.0 of hoger, sla de bovenstaande configuratie (**SampleIISInstall**) als een PowerShell-script (.ps1)-bestand.</span><span class="sxs-lookup"><span data-stu-id="25ff5-131">On a computer running PowerShell 5.0 or later, save the above configuration (**SampleIISInstall**) as a PowerShell script (.ps1) file.</span></span>

3. <span data-ttu-id="25ff5-132">Ga naar de map waar u de .ps1-bestand opgeslagen in een PowerShell-console.</span><span class="sxs-lookup"><span data-stu-id="25ff5-132">In a PowerShell console, navigate to the folder where you saved the .ps1 file.</span></span>

4. <span data-ttu-id="25ff5-133">Voer de volgende PowerShell-opdrachten voor het compileren van het MOF-document (Zie voor meer informatie over het compileren van DSC-configuraties [DSC-configuraties](configurations.md):</span><span class="sxs-lookup"><span data-stu-id="25ff5-133">Run the following PowerShell commands to compile the MOF document (for information about compiling DSC configurations, see [DSC Configurations](configurations.md):</span></span>

    ```powershell
    . .\SampleIISInstall.ps1
    SampleIISInstall
    ```

5. <span data-ttu-id="25ff5-134">Hiermee maakt u een `localhost.mof` bestand in een nieuwe map met de naam `SampleIISInstall`.</span><span class="sxs-lookup"><span data-stu-id="25ff5-134">This will create a `localhost.mof` file in a new folder named `SampleIISInstall`.</span></span>
<span data-ttu-id="25ff5-135">Wijzig de naam en dat het bestand verplaatsen naar de juiste locatie op de VHD als `Pending.mof` met behulp van de [Item verplaatsen](https://technet.microsoft.comlibrary/hh849852.aspx) cmdlet.</span><span class="sxs-lookup"><span data-stu-id="25ff5-135">Rename and move that file into the proper location on the VHD as `Pending.mof` by using the [Move-Item](https://technet.microsoft.comlibrary/hh849852.aspx) cmdlet.</span></span> <span data-ttu-id="25ff5-136">Bijvoorbeeld:</span><span class="sxs-lookup"><span data-stu-id="25ff5-136">For example:</span></span>

    ```powershell
        Move-Item -Path C:\DSCTest\SampleIISInstall\localhost.mof -Destination E:\Windows\Sytem32\Configuration\Pending.mof
    ```
6. <span data-ttu-id="25ff5-137">Ontkoppelen van de VHD door het aanroepen van de [Dismount-VHD](https://technet.microsoft.com/library/hh848562.aspx) cmdlet.</span><span class="sxs-lookup"><span data-stu-id="25ff5-137">Dismount the VHD by calling the [Dismount-VHD](https://technet.microsoft.com/library/hh848562.aspx) cmdlet.</span></span> <span data-ttu-id="25ff5-138">Bijvoorbeeld:</span><span class="sxs-lookup"><span data-stu-id="25ff5-138">For example:</span></span>

    ```powershell
    Dismount-VHD -Path C:\users\public\documents\vhd\Srv16.vhd
    ```

7. <span data-ttu-id="25ff5-139">Een virtuele machine maken met behulp van de VHD waar u het document DSC MOF hebt geïnstalleerd.</span><span class="sxs-lookup"><span data-stu-id="25ff5-139">Create a VM by using the VHD where you installed the DSC MOF document.</span></span> <span data-ttu-id="25ff5-140">Na de eerste boot-up en besturingssysteeminstallatie wordt IIS geïnstalleerd.</span><span class="sxs-lookup"><span data-stu-id="25ff5-140">After intial boot-up and operating system installation, IIS will be installed.</span></span>
<span data-ttu-id="25ff5-141">U kunt dit controleren door het aanroepen van de [Get-WindowsFeature](https://technet.microsoft.com/library/jj205469.aspx) cmdlet.</span><span class="sxs-lookup"><span data-stu-id="25ff5-141">You can verify this by calling the [Get-WindowsFeature](https://technet.microsoft.com/library/jj205469.aspx) cmdlet.</span></span>

## <a name="inject-a-dsc-metaconfiguration-into-a-vhd"></a><span data-ttu-id="25ff5-142">DSC-metaconfiguratie toe invoeren in een VHD</span><span class="sxs-lookup"><span data-stu-id="25ff5-142">Inject a DSC metaconfiguration into a VHD</span></span>

<span data-ttu-id="25ff5-143">U kunt ook configureren met een computer om op te halen van een configuratie op de eerste boot-up door het injecteren van een metaconfiguratie (Zie [configureren van de lokale Configuration Manager (LCM)](metaConfig.md)) in de VHD als de `MetaConfig.mof` bestand.</span><span class="sxs-lookup"><span data-stu-id="25ff5-143">You can also configure a computer to pull a configuration at intial boot-up by injecting a metaconfiguration (see [Configuring the Local Configuration Manager (LCM)](metaConfig.md)) into the VHD as its `MetaConfig.mof` file.</span></span>
<span data-ttu-id="25ff5-144">Als de **DSCAutomationHostEnabled** registersleutel is ingesteld op 2 (de standaardwaarde), DSC gelden de metaconfiguratie gedefinieerd door `MetaConfig.mof` naar de LCM wanneer de computer voor het eerst wordt opgestart.</span><span class="sxs-lookup"><span data-stu-id="25ff5-144">If the **DSCAutomationHostEnabled** registry key is set to 2 (the default value),  DSC will apply the metaconfiguration defined by `MetaConfig.mof` to the LCM when the computer boots up for the first time.</span></span>
<span data-ttu-id="25ff5-145">Als de metaconfiguratie wordt opgegeven dat de LCM moet pull-configuraties van een pull-server, probeert de computer voor het ophalen van een configuratie van die pull-server op de eerste boot-up.</span><span class="sxs-lookup"><span data-stu-id="25ff5-145">If the metaconfiguration specifies that the LCM should pull configurations from a pull server, the computer will attempt to pull a configuration from that pull server at inital boot-up.</span></span>
<span data-ttu-id="25ff5-146">Zie voor meer informatie over het instellen van een DSC-pull-server [instellen van een DSC-webserver pull](pullServer.md).</span><span class="sxs-lookup"><span data-stu-id="25ff5-146">For information about setting up a DSC pull server, see [Setting up a DSC web pull server](pullServer.md).</span></span>

<span data-ttu-id="25ff5-147">In dit voorbeeld gebruiken we beide de in de vorige sectie beschreven configuratie (**SampleIISInstall**), en de volgende metaconfiguratie toe:</span><span class="sxs-lookup"><span data-stu-id="25ff5-147">For this example, we will use both the configuration described in the previous section (**SampleIISInstall**), and the following metaconfiguration:</span></span>

```powershell
[DSCLocalConfigurationManager()]
configuration PullClientBootstrap
{
    Node localhost
    {
        Settings
        {
            RefreshMode = 'Pull'
            RefreshFrequencyMins = 30
            RebootNodeIfNeeded = $true
        }
        ConfigurationRepositoryWeb CONTOSO-PullSrv
        {
            ServerURL = 'https://CONTOSO-PullSrv:8080/PSDSCPullServer.svc'
            RegistrationKey = '140a952b-b9d6-406b-b416-e0f759c9c0e4'
            ConfigurationNames = @('SampleIISInstall')
        }
    }
}
```

### <a name="to-inject-the-metaconfiguration-mof-document-on-the-vhd"></a><span data-ttu-id="25ff5-148">Het document van de MOF metaconfiguratie toe op de VHD invoeren</span><span class="sxs-lookup"><span data-stu-id="25ff5-148">To inject the metaconfiguration MOF document on the VHD</span></span>

1. <span data-ttu-id="25ff5-149">Koppelen van de VHD waaraan u de metaconfiguratie invoeren wilt door het aanroepen van de [Mount-VHD](https://technet.microsoft.com/library/hh848551.aspx) cmdlet.</span><span class="sxs-lookup"><span data-stu-id="25ff5-149">Mount the VHD into which you want to inject the metaconfiguration by calling the [Mount-VHD](https://technet.microsoft.com/library/hh848551.aspx) cmdlet.</span></span> <span data-ttu-id="25ff5-150">Bijvoorbeeld:</span><span class="sxs-lookup"><span data-stu-id="25ff5-150">For example:</span></span>

    ```powershell
    Mount-VHD -Path C:\users\public\documents\vhd\Srv16.vhd
    ```

2. <span data-ttu-id="25ff5-151">[Instellen van een DSC-webserver pull](pullServer.md), en sla de **SampleIISInistall** configuratie naar de juiste map.</span><span class="sxs-lookup"><span data-stu-id="25ff5-151">[Set up a DSC web pull server](pullServer.md), and save the **SampleIISInistall** configuration to the appropriate folder.</span></span>

3. <span data-ttu-id="25ff5-152">Op een computer waarop PowerShell 5.0 of hoger, sla de bovenstaande metaconfiguratie (**PullClientBootstrap**) als een PowerShell-script (.ps1)-bestand.</span><span class="sxs-lookup"><span data-stu-id="25ff5-152">On a computer running PowerShell 5.0 or later, save the above metaconfiguration (**PullClientBootstrap**) as a PowerShell script (.ps1) file.</span></span>

4. <span data-ttu-id="25ff5-153">Ga naar de map waar u de .ps1-bestand opgeslagen in een PowerShell-console.</span><span class="sxs-lookup"><span data-stu-id="25ff5-153">In a PowerShell console, navigate to the folder where you saved the .ps1 file.</span></span>

5. <span data-ttu-id="25ff5-154">Voer de volgende PowerShell-opdrachten voor het compileren van het MOF-metaconfiguratie document (Zie voor meer informatie over het compileren van DSC-configuraties [DSC-configuraties](configurations.md):</span><span class="sxs-lookup"><span data-stu-id="25ff5-154">Run the following PowerShell commands to compile the  metaconfiguration MOF document (for information about compiling DSC configurations, see [DSC Configurations](configurations.md):</span></span>

    ```powershell
    . .\PullClientBootstrap.ps1
    PullClientBootstrap
    ```

6. <span data-ttu-id="25ff5-155">Hiermee maakt u een `localhost.meta.mof` bestand in een nieuwe map met de naam `PullClientBootstrap`.</span><span class="sxs-lookup"><span data-stu-id="25ff5-155">This will create a `localhost.meta.mof` file in a new folder named `PullClientBootstrap`.</span></span>
<span data-ttu-id="25ff5-156">Wijzig de naam en dat het bestand verplaatsen naar de juiste locatie op de VHD als `MetaConfig.mof` met behulp van de [Item verplaatsen](https://technet.microsoft.comlibrary/hh849852.aspx) cmdlet.</span><span class="sxs-lookup"><span data-stu-id="25ff5-156">Rename and move that file into the proper location on the VHD as `MetaConfig.mof` by using the [Move-Item](https://technet.microsoft.comlibrary/hh849852.aspx) cmdlet.</span></span>

    ```powershell
    Move-Item -Path C:\DSCTest\PullClientBootstrap\localhost.meta.mof -Destination E:\Windows\Sytem32\Configuration\MetaConfig.mof
    ```

7. <span data-ttu-id="25ff5-157">Ontkoppelen van de VHD door het aanroepen van de [Dismount-VHD](https://technet.microsoft.com/library/hh848562.aspx) cmdlet.</span><span class="sxs-lookup"><span data-stu-id="25ff5-157">Dismount the VHD by calling the [Dismount-VHD](https://technet.microsoft.com/library/hh848562.aspx) cmdlet.</span></span> <span data-ttu-id="25ff5-158">Bijvoorbeeld:</span><span class="sxs-lookup"><span data-stu-id="25ff5-158">For example:</span></span>

    ```powershell
    Dismount-VHD -Path C:\users\public\documents\vhd\Srv16.vhd
    ```

8. <span data-ttu-id="25ff5-159">Een virtuele machine maken met behulp van de VHD waar u het document DSC MOF hebt geïnstalleerd.</span><span class="sxs-lookup"><span data-stu-id="25ff5-159">Create a VM by using the VHD where you installed the DSC MOF document.</span></span>
<span data-ttu-id="25ff5-160">Na de eerste boot-up- en installatie van besturingssysteem DSC klikt, wordt de configuratie van de pull-server en IIS wordt geïnstalleerd.</span><span class="sxs-lookup"><span data-stu-id="25ff5-160">After intial boot-up and operating system installation, DSC will pull the configuration from the pull server, and IIS will be installed.</span></span>
<span data-ttu-id="25ff5-161">U kunt dit controleren door het aanroepen van de [Get-WindowsFeature](https://technet.microsoft.com/library/jj205469.aspx) cmdlet.</span><span class="sxs-lookup"><span data-stu-id="25ff5-161">You can verify this by calling the [Get-WindowsFeature](https://technet.microsoft.com/library/jj205469.aspx) cmdlet.</span></span>

## <a name="disable-dsc-at-boot-time"></a><span data-ttu-id="25ff5-162">DSC tijdens het opstarten uitschakelen</span><span class="sxs-lookup"><span data-stu-id="25ff5-162">Disable DSC at boot time</span></span>

<span data-ttu-id="25ff5-163">Standaard wordt de waarde van de **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion\Policies\DSCAutomationHostEnabled** sleutel is ingesteld op 2, waarmee een DSC-configuratie voor het uitvoeren als de computer in behandeling of huidige is status.</span><span class="sxs-lookup"><span data-stu-id="25ff5-163">By default, the value of the **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion\Policies\DSCAutomationHostEnabled** key is set to 2, which allows a DSC configuration to run if the computer is in pending or current state.</span></span> <span data-ttu-id="25ff5-164">Als u niet dat een configuratie op de eerste boot-up wordt uitgevoerd wilt, moet u de waarde van deze sleutel dus ingesteld op 0:</span><span class="sxs-lookup"><span data-stu-id="25ff5-164">If you do not want a configuration to run at initial boot-up, you need so set the value of this key to 0:</span></span>

1. <span data-ttu-id="25ff5-165">De VHD koppelen door het aanroepen van de [Mount-VHD](https://technet.microsoft.com/library/hh848551.aspx) cmdlet.</span><span class="sxs-lookup"><span data-stu-id="25ff5-165">Mount the VHD by calling the [Mount-VHD](https://technet.microsoft.com/library/hh848551.aspx) cmdlet.</span></span> <span data-ttu-id="25ff5-166">Bijvoorbeeld:</span><span class="sxs-lookup"><span data-stu-id="25ff5-166">For example:</span></span>

    ```powershell
    Mount-VHD -Path C:\users\public\documents\vhd\Srv16.vhd
    ```

2. <span data-ttu-id="25ff5-167">Laden van het register **HKLM\Software** subsleutels van de VHD door het aanroepen van `reg load`.</span><span class="sxs-lookup"><span data-stu-id="25ff5-167">Load the registry **HKLM\Software** subkey from the VHD by calling `reg load`.</span></span>

    ```
    reg load HKLM\Vhd E:\Windows\System32\Config\Software`
    ```

3. <span data-ttu-id="25ff5-168">Navigeer naar de **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion\Policies\***  met behulp van de PowerShell-registerprovider.</span><span class="sxs-lookup"><span data-stu-id="25ff5-168">Navigate to the **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion\Policies\*** by using the PowerShell Registry provider.</span></span>

    ```powershell
    Set-Location HKLM:\Software\Microsoft\Windows\CurrentVersion\Policies`
    ```

4. <span data-ttu-id="25ff5-169">Wijzig de waarde van `DSCAutomationHostEnabled` op 0.</span><span class="sxs-lookup"><span data-stu-id="25ff5-169">Change the value of `DSCAutomationHostEnabled` to 0.</span></span>

    ```powershell
    Set-ItemProperty -Path . -Name DSCAutomationHostEnabled -Value 0
    ```

5. <span data-ttu-id="25ff5-170">Het register laden door het uitvoeren van de volgende opdrachten:</span><span class="sxs-lookup"><span data-stu-id="25ff5-170">Unload the registry by running the following commands:</span></span>

    ```powershell
    [gc]::Collect()
    reg unload HKLM\Vhd
    ```

## <a name="see-also"></a><span data-ttu-id="25ff5-171">Zie ook</span><span class="sxs-lookup"><span data-stu-id="25ff5-171">See Also</span></span>

- [<span data-ttu-id="25ff5-172">DSC-configuraties</span><span class="sxs-lookup"><span data-stu-id="25ff5-172">DSC Configurations</span></span>](configurations.md)
- [<span data-ttu-id="25ff5-173">De registersleutel DSCAutomationHostEnabled</span><span class="sxs-lookup"><span data-stu-id="25ff5-173">DSCAutomationHostEnabled registry key</span></span>](DSCAutomationHostEnabled.md)
- [<span data-ttu-id="25ff5-174">Configureren van de lokale Configuration Manager (LCM)</span><span class="sxs-lookup"><span data-stu-id="25ff5-174">Configuring the Local Configuration Manager (LCM)</span></span>](metaConfig.md)
- [<span data-ttu-id="25ff5-175">Een DSC web pull-server instellen</span><span class="sxs-lookup"><span data-stu-id="25ff5-175">Setting up a DSC web pull server</span></span>](pullServer.md)

