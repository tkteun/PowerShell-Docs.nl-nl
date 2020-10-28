---
ms.date: 06/12/2017
keywords: DSC, Power shell, configuratie, installatie
title: Een virtuele machine configureren bij de eerste keer opstarten met behulp van DSC
description: In dit artikel wordt beschreven hoe u een virtuele machine kunt configureren bij de eerste keer opstarten met behulp van DSC
ms.openlocfilehash: 9fa8c4a21486aaef87e1c0a3097e5983a378d98d
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/27/2020
ms.locfileid: "92656192"
---
# <a name="configure-a-virtual-machines-at-initial-boot-up-by-using-dsc"></a><span data-ttu-id="f8300-104">Een virtuele machine configureren bij de eerste keer opstarten met behulp van DSC</span><span class="sxs-lookup"><span data-stu-id="f8300-104">Configure a virtual machines at initial boot-up by using DSC</span></span>

> [!IMPORTANT]
> <span data-ttu-id="f8300-105">Van toepassing op: Windows Power shell 5,0</span><span class="sxs-lookup"><span data-stu-id="f8300-105">Applies To: Windows PowerShell 5.0</span></span>

## <a name="requirements"></a><span data-ttu-id="f8300-106">Vereisten</span><span class="sxs-lookup"><span data-stu-id="f8300-106">Requirements</span></span>

> [!NOTE]
> <span data-ttu-id="f8300-107">De register sleutel **DSCAutomationHostEnabled** die in dit onderwerp wordt beschreven, is niet beschikbaar in power Shell 4,0.</span><span class="sxs-lookup"><span data-stu-id="f8300-107">The **DSCAutomationHostEnabled** registry key described in this topic is not available in PowerShell 4.0.</span></span> <span data-ttu-id="f8300-108">Voor informatie over het configureren van nieuwe virtuele machines bij de eerste keer opstarten in Power Shell 4,0, raadpleegt [u uw machines automatisch configureren met DSC bij de eerste keer opstarten?](https://blogs.msdn.microsoft.com/powershell/2014/02/28/want-to-automatically-configure-your-machines-using-dsc-at-initial-boot-up/)</span><span class="sxs-lookup"><span data-stu-id="f8300-108">For information on how to configure new virtual machines at initial boot-up in PowerShell 4.0, see [Want to Automatically Configure Your Machines Using DSC at Initial Boot-up?](https://blogs.msdn.microsoft.com/powershell/2014/02/28/want-to-automatically-configure-your-machines-using-dsc-at-initial-boot-up/)</span></span>

<span data-ttu-id="f8300-109">Als u deze voor beelden wilt uitvoeren, hebt u het volgende nodig:</span><span class="sxs-lookup"><span data-stu-id="f8300-109">To run these examples, you will need:</span></span>

- <span data-ttu-id="f8300-110">Een opstart bare VHD om mee te werken.</span><span class="sxs-lookup"><span data-stu-id="f8300-110">A bootable VHD to work with.</span></span> <span data-ttu-id="f8300-111">U kunt een ISO downloaden met een evaluatie versie van Windows Server 2016 op [TechNet Evaluation Center](https://www.microsoft.com/evalcenter/evaluate-windows-server-2016).</span><span class="sxs-lookup"><span data-stu-id="f8300-111">You can download an ISO with an evaluation copy of Windows Server 2016 at [TechNet Evaluation Center](https://www.microsoft.com/evalcenter/evaluate-windows-server-2016).</span></span>
  <span data-ttu-id="f8300-112">U vindt instructies over het maken van een VHD op basis van een ISO-installatie kopie bij [het maken van opstart bare virtuele harde schijven](/previous-versions/windows/it-pro/windows-7/gg318049(v=ws.10)).</span><span class="sxs-lookup"><span data-stu-id="f8300-112">You can find instructions on how to create a VHD from an ISO image at [Creating Bootable Virtual Hard Disks](/previous-versions/windows/it-pro/windows-7/gg318049(v=ws.10)).</span></span>
- <span data-ttu-id="f8300-113">Een hostcomputer waarop Hyper-V is ingeschakeld.</span><span class="sxs-lookup"><span data-stu-id="f8300-113">A host computer that has Hyper-V enabled.</span></span> <span data-ttu-id="f8300-114">Zie [Hyper-V Overview](/previous-versions/windows/it-pro/windows-server-2012-R2-and-2012/hh831531(v=ws.11))(Engelstalig) voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="f8300-114">For information, see [Hyper-V overview](/previous-versions/windows/it-pro/windows-server-2012-R2-and-2012/hh831531(v=ws.11)).</span></span>

  <span data-ttu-id="f8300-115">Met behulp van DSC kunt u software-installatie en-configuratie automatiseren voor een computer bij de eerste keer dat deze wordt opgestart.</span><span class="sxs-lookup"><span data-stu-id="f8300-115">By using DSC, you can automate software installation and configuration for a computer at initial boot-up.</span></span> <span data-ttu-id="f8300-116">U doet dit door een configuratie-MOF-document of een-configuratie in te voegen in opstart bare media (zoals een VHD), zodat ze tijdens het eerste opstart proces worden uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="f8300-116">You do this by either injecting a configuration MOF document or a metaconfiguration into bootable media (such as a VHD) so that they are run during the initial boot-up process.</span></span> <span data-ttu-id="f8300-117">Dit gedrag wordt opgegeven door de register sleutel [DSCAutomationHostEnabled register sleutel](DSCAutomationHostEnabled.md) onder `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion\Policies\System` .</span><span class="sxs-lookup"><span data-stu-id="f8300-117">This behavior is specified by the [DSCAutomationHostEnabled registry key](DSCAutomationHostEnabled.md) registry key under `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion\Policies\System`.</span></span>
  <span data-ttu-id="f8300-118">De waarde van deze sleutel is standaard 2, zodat DSC tijdens het opstarten kan worden uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="f8300-118">By default, the value of this key is 2, which allows DSC to run at boot time.</span></span>

  <span data-ttu-id="f8300-119">Als u niet wilt dat DSC tijdens de opstart tijd wordt uitgevoerd, stelt u de waarde van de register sleutel [DSCAutomationHostEnabled register sleutel](DSCAutomationHostEnabled.md) in op 0.</span><span class="sxs-lookup"><span data-stu-id="f8300-119">If you do not want DSC to run at boot time, set the value of the [DSCAutomationHostEnabled registry key](DSCAutomationHostEnabled.md) registry key to 0.</span></span>

- <span data-ttu-id="f8300-120">Een configuratie-MOF-document in een VHD injecteren</span><span class="sxs-lookup"><span data-stu-id="f8300-120">Inject a configuration MOF document into a VHD</span></span>
- <span data-ttu-id="f8300-121">Een DSC-mailconfiguratie in een VHD injecteren</span><span class="sxs-lookup"><span data-stu-id="f8300-121">Inject a DSC metaconfiguration into a VHD</span></span>
- <span data-ttu-id="f8300-122">DSC op het moment van opstarten uitschakelen</span><span class="sxs-lookup"><span data-stu-id="f8300-122">Disable DSC at boot time</span></span>

> [!NOTE]
> <span data-ttu-id="f8300-123">U kunt zowel `Pending.mof` als `MetaConfig.mof` op een computer tegelijk injecteren.</span><span class="sxs-lookup"><span data-stu-id="f8300-123">You can inject both `Pending.mof` and `MetaConfig.mof` into a computer at the same time.</span></span>
> <span data-ttu-id="f8300-124">Als beide bestanden aanwezig zijn, hebben de instellingen die zijn opgegeven in `MetaConfig.mof` prioriteit.</span><span class="sxs-lookup"><span data-stu-id="f8300-124">If both files are present, the settings specified in `MetaConfig.mof` take precedence.</span></span>

## <a name="inject-a-configuration-mof-document-into-a-vhd"></a><span data-ttu-id="f8300-125">Een configuratie-MOF-document in een VHD injecteren</span><span class="sxs-lookup"><span data-stu-id="f8300-125">Inject a configuration MOF document into a VHD</span></span>

<span data-ttu-id="f8300-126">Als u een configuratie bij de eerste keer opstarten wilt instellen, kunt u een gecompileerd configuratie-MOF-document als bestand in de VHD injecteren `Pending.mof` .</span><span class="sxs-lookup"><span data-stu-id="f8300-126">To enact a configuration at initial boot-up, you can inject a compiled configuration MOF document into the VHD as its `Pending.mof` file.</span></span> <span data-ttu-id="f8300-127">Als de register sleutel **DSCAutomationHostEnabled** is ingesteld op 2 (de standaard waarde), past DSC de configuratie toe die is gedefinieerd door `Pending.mof` wanneer de computer voor de eerste keer wordt opgestart.</span><span class="sxs-lookup"><span data-stu-id="f8300-127">If the **DSCAutomationHostEnabled** registry key is set to 2 (the default value), DSC will apply the configuration defined by `Pending.mof` when the computer boots up for the first time.</span></span>

<span data-ttu-id="f8300-128">In dit voor beeld gebruiken we de volgende configuratie, waarmee IIS wordt geïnstalleerd op de nieuwe computer:</span><span class="sxs-lookup"><span data-stu-id="f8300-128">For this example, we will use the following configuration, which will install IIS on the new computer:</span></span>

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

### <a name="to-inject-the-configuration-mof-document-on-the-vhd"></a><span data-ttu-id="f8300-129">Het MOF-document voor de configuratie op de VHD injecteren</span><span class="sxs-lookup"><span data-stu-id="f8300-129">To inject the configuration MOF document on the VHD</span></span>

1. <span data-ttu-id="f8300-130">Koppel de VHD waarin u de configuratie wilt injecteren door de cmdlet [Mount-VHD](/powershell/module/hyper-v/mount-vhd) aan te roepen.</span><span class="sxs-lookup"><span data-stu-id="f8300-130">Mount the VHD into which you want to inject the configuration by calling the [Mount-VHD](/powershell/module/hyper-v/mount-vhd) cmdlet.</span></span> <span data-ttu-id="f8300-131">Bijvoorbeeld:</span><span class="sxs-lookup"><span data-stu-id="f8300-131">For example:</span></span>

   ```powershell
   Mount-VHD -Path C:\users\public\documents\vhd\Srv16.vhd
   ```

1. <span data-ttu-id="f8300-132">Op een computer waarop Power shell 5,0 of hoger wordt uitgevoerd, slaat u de bovenstaande configuratie ( **SampleIISInstall** ) op als een Power shell-script bestand (. ps1).</span><span class="sxs-lookup"><span data-stu-id="f8300-132">On a computer running PowerShell 5.0 or later, save the above configuration ( **SampleIISInstall** ) as a PowerShell script (.ps1) file.</span></span>

1. <span data-ttu-id="f8300-133">Navigeer in een Power shell-console naar de map waar u het. ps1-bestand hebt opgeslagen.</span><span class="sxs-lookup"><span data-stu-id="f8300-133">In a PowerShell console, navigate to the folder where you saved the .ps1 file.</span></span>

1. <span data-ttu-id="f8300-134">Voer de volgende Power shell-opdrachten uit om het MOF-document te compileren (Zie DSC- [configuraties](../configurations/configurations.md)voor informatie over het compileren van DSC-configuraties:</span><span class="sxs-lookup"><span data-stu-id="f8300-134">Run the following PowerShell commands to compile the MOF document (for information about compiling DSC configurations, see [DSC Configurations](../configurations/configurations.md):</span></span>

   ```powershell
   . .\SampleIISInstall.ps1
   SampleIISInstall
   ```

1. <span data-ttu-id="f8300-135">Hiermee maakt u een `localhost.mof` bestand in een nieuwe map met de naam `SampleIISInstall` .</span><span class="sxs-lookup"><span data-stu-id="f8300-135">This will create a `localhost.mof` file in a new folder named `SampleIISInstall`.</span></span> <span data-ttu-id="f8300-136">Wijzig de naam en verplaats dat bestand naar de juiste locatie op de VHD als met `Pending.mof` behulp van de cmdlet [Move-item](/powershell/module/microsoft.powershell.management/move-item) .</span><span class="sxs-lookup"><span data-stu-id="f8300-136">Rename and move that file into the proper location on the VHD as `Pending.mof` by using the [Move-Item](/powershell/module/microsoft.powershell.management/move-item) cmdlet.</span></span> <span data-ttu-id="f8300-137">Bijvoorbeeld:</span><span class="sxs-lookup"><span data-stu-id="f8300-137">For example:</span></span>

   ```powershell
   Move-Item -Path C:\DSCTest\SampleIISInstall\localhost.mof -Destination E:\Windows\System32\Configuration\Pending.mof
   ```

1. <span data-ttu-id="f8300-138">Ontkoppel de VHD door de cmdlet [dismount-VHD](/powershell/module/hyper-v/dismount-vhd) aan te roepen.</span><span class="sxs-lookup"><span data-stu-id="f8300-138">Dismount the VHD by calling the [Dismount-VHD](/powershell/module/hyper-v/dismount-vhd) cmdlet.</span></span>
   <span data-ttu-id="f8300-139">Bijvoorbeeld:</span><span class="sxs-lookup"><span data-stu-id="f8300-139">For example:</span></span>

   ```powershell
   Dismount-VHD -Path C:\users\public\documents\vhd\Srv16.vhd
   ```

1. <span data-ttu-id="f8300-140">Maak een virtuele machine met behulp van de VHD waar u het DSC MOF-document hebt geïnstalleerd.</span><span class="sxs-lookup"><span data-stu-id="f8300-140">Create a VM by using the VHD where you installed the DSC MOF document.</span></span>

<span data-ttu-id="f8300-141">Na de eerste opstart-en installatie van het besturings systeem wordt IIS geïnstalleerd.</span><span class="sxs-lookup"><span data-stu-id="f8300-141">After initial boot-up and operating system installation, IIS will be installed.</span></span> <span data-ttu-id="f8300-142">U kunt dit controleren door de cmdlet [Get-WindowsFeature aan](/powershell/module/servermanager/get-windowsfeature) te roepen.</span><span class="sxs-lookup"><span data-stu-id="f8300-142">You can verify this by calling the [Get-WindowsFeature](/powershell/module/servermanager/get-windowsfeature) cmdlet.</span></span>

## <a name="inject-a-dsc-metaconfiguration-into-a-vhd"></a><span data-ttu-id="f8300-143">Een DSC-mailconfiguratie in een VHD injecteren</span><span class="sxs-lookup"><span data-stu-id="f8300-143">Inject a DSC metaconfiguration into a VHD</span></span>

<span data-ttu-id="f8300-144">U kunt ook een computer configureren voor het ophalen van een configuratie bij de eerste keer opstarten door een meta configuratie in te voeren (Zie [de lokale Configuration Manager (LCM) configureren](../managing-nodes/metaConfig.md)in de VHD als `MetaConfig.mof` bestand.</span><span class="sxs-lookup"><span data-stu-id="f8300-144">You can also configure a computer to pull a configuration at initial boot-up by injecting a metaconfiguration (see [Configuring the Local Configuration Manager (LCM)](../managing-nodes/metaConfig.md)) into the VHD as its `MetaConfig.mof` file.</span></span> <span data-ttu-id="f8300-145">Als de register sleutel **DSCAutomationHostEnabled** is ingesteld op 2 (de standaard waarde), wordt de door DSC gedefinieerde configuratie toegepast op `MetaConfig.mof` de LCM wanneer de computer voor de eerste keer wordt opgestart.</span><span class="sxs-lookup"><span data-stu-id="f8300-145">If the **DSCAutomationHostEnabled** registry key is set to 2 (the default value), DSC will apply the metaconfiguration defined by `MetaConfig.mof` to the LCM when the computer boots up for the first time.</span></span> <span data-ttu-id="f8300-146">Als de-configuratie opgeeft dat de LCM configuraties moet ophalen van een pull-server, probeert de computer tijdens het opstarten een configuratie te halen van die pull-server.</span><span class="sxs-lookup"><span data-stu-id="f8300-146">If the metaconfiguration specifies that the LCM should pull configurations from a pull server, the computer will attempt to pull a configuration from that pull server at initial boot-up.</span></span> <span data-ttu-id="f8300-147">Zie [een DSC Web-pull-server instellen](../pull-server/pullServer.md)voor meer informatie over het instellen van een DSC-pull-server.</span><span class="sxs-lookup"><span data-stu-id="f8300-147">For information about setting up a DSC pull server, see [Setting up a DSC web pull server](../pull-server/pullServer.md).</span></span>

<span data-ttu-id="f8300-148">Voor dit voor beeld gebruiken we zowel de configuratie die wordt beschreven in de vorige sectie ( **SampleIISInstall** ) als de volgende-configuratie:</span><span class="sxs-lookup"><span data-stu-id="f8300-148">For this example, we will use both the configuration described in the previous section ( **SampleIISInstall** ), and the following metaconfiguration:</span></span>

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

### <a name="to-inject-the-metaconfiguration-mof-document-on-the-vhd"></a><span data-ttu-id="f8300-149">Het MOF-document van de configuratie voor de virtuele harde schijf injecteren</span><span class="sxs-lookup"><span data-stu-id="f8300-149">To inject the metaconfiguration MOF document on the VHD</span></span>

1. <span data-ttu-id="f8300-150">Koppel de VHD waarin u de-configuratie wilt injecteren door de cmdlet [Mount-VHD](/powershell/module/hyper-v/mount-vhd) aan te roepen.</span><span class="sxs-lookup"><span data-stu-id="f8300-150">Mount the VHD into which you want to inject the metaconfiguration by calling the [Mount-VHD](/powershell/module/hyper-v/mount-vhd) cmdlet.</span></span> <span data-ttu-id="f8300-151">Bijvoorbeeld:</span><span class="sxs-lookup"><span data-stu-id="f8300-151">For example:</span></span>

   ```powershell
   Mount-VHD -Path C:\users\public\documents\vhd\Srv16.vhd
   ```

1. <span data-ttu-id="f8300-152">[Stel een DSC Web-pull-server](../pull-server/pullServer.md)in en sla de **SampleIISInstall** -configuratie op in de juiste map.</span><span class="sxs-lookup"><span data-stu-id="f8300-152">[Set up a DSC web pull server](../pull-server/pullServer.md), and save the **SampleIISInstall** configuration to the appropriate folder.</span></span>

1. <span data-ttu-id="f8300-153">Op een computer waarop Power shell 5,0 of hoger wordt uitgevoerd, slaat u de bovenstaande meta configuratie ( **PullClientBootstrap** ) op als een Power shell-script bestand (. ps1).</span><span class="sxs-lookup"><span data-stu-id="f8300-153">On a computer running PowerShell 5.0 or later, save the above metaconfiguration ( **PullClientBootstrap** ) as a PowerShell script (.ps1) file.</span></span>

1. <span data-ttu-id="f8300-154">Navigeer in een Power shell-console naar de map waar u het. ps1-bestand hebt opgeslagen.</span><span class="sxs-lookup"><span data-stu-id="f8300-154">In a PowerShell console, navigate to the folder where you saved the .ps1 file.</span></span>

1. <span data-ttu-id="f8300-155">Voer de volgende Power shell-opdrachten uit voor het compileren van het MOF-document met de eigen configuratie (Zie [DSC-configuraties](../configurations/configurations.md)voor meer informatie over het compileren van DSC-configuraties:</span><span class="sxs-lookup"><span data-stu-id="f8300-155">Run the following PowerShell commands to compile the metaconfiguration MOF document (for information about compiling DSC configurations, see [DSC Configurations](../configurations/configurations.md):</span></span>

   ```powershell
   . .\PullClientBootstrap.ps1
   PullClientBootstrap
   ```

1. <span data-ttu-id="f8300-156">Hiermee maakt u een `localhost.meta.mof` bestand in een nieuwe map met de naam `PullClientBootstrap` .</span><span class="sxs-lookup"><span data-stu-id="f8300-156">This will create a `localhost.meta.mof` file in a new folder named `PullClientBootstrap`.</span></span> <span data-ttu-id="f8300-157">Wijzig de naam en verplaats dat bestand naar de juiste locatie op de VHD als met `MetaConfig.mof` behulp van de cmdlet [Move-item](/powershell/module/microsoft.powershell.management/move-item) .</span><span class="sxs-lookup"><span data-stu-id="f8300-157">Rename and move that file into the proper location on the VHD as `MetaConfig.mof` by using the [Move-Item](/powershell/module/microsoft.powershell.management/move-item) cmdlet.</span></span>

   ```powershell
   Move-Item -Path C:\DSCTest\PullClientBootstrap\localhost.meta.mof -Destination E:\Windows\System32\Configuration\MetaConfig.mof
   ```

1. <span data-ttu-id="f8300-158">Ontkoppel de VHD door de cmdlet [dismount-VHD](/powershell/module/hyper-v/dismount-vhd) aan te roepen.</span><span class="sxs-lookup"><span data-stu-id="f8300-158">Dismount the VHD by calling the [Dismount-VHD](/powershell/module/hyper-v/dismount-vhd) cmdlet.</span></span>
   <span data-ttu-id="f8300-159">Bijvoorbeeld:</span><span class="sxs-lookup"><span data-stu-id="f8300-159">For example:</span></span>

   ```powershell
   Dismount-VHD -Path C:\users\public\documents\vhd\Srv16.vhd
   ```

1. <span data-ttu-id="f8300-160">Maak een virtuele machine met behulp van de VHD waar u het DSC MOF-document hebt geïnstalleerd.</span><span class="sxs-lookup"><span data-stu-id="f8300-160">Create a VM by using the VHD where you installed the DSC MOF document.</span></span>

<span data-ttu-id="f8300-161">Na de eerste opstart-en installatie van het besturings systeem haalt DSC de configuratie van de pull-server en wordt IIS geïnstalleerd.</span><span class="sxs-lookup"><span data-stu-id="f8300-161">After initial boot-up and operating system installation, DSC will pull the configuration from the pull server, and IIS will be installed.</span></span> <span data-ttu-id="f8300-162">U kunt dit controleren door de cmdlet [Get-WindowsFeature aan](/powershell/module/servermanager/get-windowsfeature) te roepen.</span><span class="sxs-lookup"><span data-stu-id="f8300-162">You can verify this by calling the [Get-WindowsFeature](/powershell/module/servermanager/get-windowsfeature) cmdlet.</span></span>

## <a name="disable-dsc-at-boot-time"></a><span data-ttu-id="f8300-163">DSC op het moment van opstarten uitschakelen</span><span class="sxs-lookup"><span data-stu-id="f8300-163">Disable DSC at boot time</span></span>

<span data-ttu-id="f8300-164">Standaard is dit de waarde van de `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion\Policies\System\DSCAutomationHostEnabled`</span><span class="sxs-lookup"><span data-stu-id="f8300-164">By default, the value of the `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion\Policies\System\DSCAutomationHostEnabled`</span></span>
<span data-ttu-id="f8300-165">de sleutel is ingesteld op 2, waardoor een DSC-configuratie kan worden uitgevoerd als de computer de status in behandeling of actief heeft.</span><span class="sxs-lookup"><span data-stu-id="f8300-165">key is set to 2, which allows a DSC configuration to run if the computer is in pending or current state.</span></span> <span data-ttu-id="f8300-166">Als u niet wilt dat een configuratie wordt uitgevoerd bij de eerste keer opstarten, moet u de waarde van deze sleutel instellen op 0:</span><span class="sxs-lookup"><span data-stu-id="f8300-166">If you do not want a configuration to run at initial boot-up, you need so set the value of this key to 0:</span></span>

1. <span data-ttu-id="f8300-167">Koppel de VHD door de cmdlet [Mount-VHD](/powershell/module/hyper-v/mount-vhd) aan te roepen.</span><span class="sxs-lookup"><span data-stu-id="f8300-167">Mount the VHD by calling the [Mount-VHD](/powershell/module/hyper-v/mount-vhd) cmdlet.</span></span> <span data-ttu-id="f8300-168">Bijvoorbeeld:</span><span class="sxs-lookup"><span data-stu-id="f8300-168">For example:</span></span>

   ```powershell
   Mount-VHD -Path C:\users\public\documents\vhd\Srv16.vhd
   ```

1. <span data-ttu-id="f8300-169">Laad de `HKLM\Software` registersubsleutel van de VHD door aan te roepen `reg load` .</span><span class="sxs-lookup"><span data-stu-id="f8300-169">Load the registry `HKLM\Software` subkey from the VHD by calling `reg load`.</span></span>

   ```powershell
   reg load HKLM\Vhd E:\Windows\System32\Config\Software`
   ```

1. <span data-ttu-id="f8300-170">Ga naar de `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion\Policies\System` door de Power shell-register provider te gebruiken.</span><span class="sxs-lookup"><span data-stu-id="f8300-170">Navigate to the `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion\Policies\System` by using the PowerShell Registry provider.</span></span>

   ```powershell
   Set-Location HKLM:\Software\Microsoft\Windows\CurrentVersion\Policies\System`
   ```

1. <span data-ttu-id="f8300-171">Wijzig de waarde van `DSCAutomationHostEnabled` in 0.</span><span class="sxs-lookup"><span data-stu-id="f8300-171">Change the value of `DSCAutomationHostEnabled` to 0.</span></span>

   ```powershell
   Set-ItemProperty -Path . -Name DSCAutomationHostEnabled -Value 0
   ```

5. <span data-ttu-id="f8300-172">Verwijder het REGI ster door de volgende opdrachten uit te voeren:</span><span class="sxs-lookup"><span data-stu-id="f8300-172">Unload the registry by running the following commands:</span></span>

   ```powershell
   [gc]::Collect()
   reg unload HKLM\Vhd
   ```

## <a name="see-also"></a><span data-ttu-id="f8300-173">Zie ook</span><span class="sxs-lookup"><span data-stu-id="f8300-173">See Also</span></span>

[<span data-ttu-id="f8300-174">DSC-configuraties</span><span class="sxs-lookup"><span data-stu-id="f8300-174">DSC Configurations</span></span>](../configurations/configurations.md)

[<span data-ttu-id="f8300-175">De registersleutel DSCAutomationHostEnabled</span><span class="sxs-lookup"><span data-stu-id="f8300-175">DSCAutomationHostEnabled registry key</span></span>](DSCAutomationHostEnabled.md)

[<span data-ttu-id="f8300-176">De Local Configuration Manager (LCM) configureren</span><span class="sxs-lookup"><span data-stu-id="f8300-176">Configuring the Local Configuration Manager (LCM)</span></span>](../managing-nodes/metaConfig.md)

[<span data-ttu-id="f8300-177">Een DSC Web-pull-server instellen</span><span class="sxs-lookup"><span data-stu-id="f8300-177">Setting up a DSC web pull server</span></span>](../pull-server/pullServer.md)
