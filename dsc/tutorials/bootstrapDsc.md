---
ms.date: 06/12/2017
keywords: DSC, powershell, configuratie en installatie
title: Een virtuele machine configureren bij de eerste keer opstarten met behulp van DSC
ms.openlocfilehash: 2ae6f7a85af3d08bad9e97b90efaefb2ff8410ca
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 02/03/2019
ms.locfileid: "55686906"
---
# <a name="configure-a-virtual-machines-at-initial-boot-up-by-using-dsc"></a><span data-ttu-id="469d7-103">Een virtuele machine configureren bij de eerste keer opstarten met behulp van DSC</span><span class="sxs-lookup"><span data-stu-id="469d7-103">Configure a virtual machines at initial boot-up by using DSC</span></span>

> [!IMPORTANT]
> <span data-ttu-id="469d7-104">Van toepassing op: Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="469d7-104">Applies To: Windows PowerShell 5.0</span></span>

## <a name="requirements"></a><span data-ttu-id="469d7-105">Vereisten</span><span class="sxs-lookup"><span data-stu-id="469d7-105">Requirements</span></span>

> [!NOTE]
> <span data-ttu-id="469d7-106">De **DSCAutomationHostEnabled** registersleutel die worden beschreven in dit onderwerp is niet beschikbaar in PowerShell 4.0.</span><span class="sxs-lookup"><span data-stu-id="469d7-106">The **DSCAutomationHostEnabled** registry key described in this topic is not available in PowerShell 4.0.</span></span>
> <span data-ttu-id="469d7-107">Zie voor meer informatie over het configureren van nieuwe virtuele machines bij de eerste keer opstarten in PowerShell 4.0 [wilt automatisch configureren van uw Machines met behulp van DSC bij de eerste keer opstarten?](https://blogs.msdn.microsoft.com/powershell/2014/02/28/want-to-automatically-configure-your-machines-using-dsc-at-initial-boot-up/)</span><span class="sxs-lookup"><span data-stu-id="469d7-107">For information on how to configure new virtual machines at initial boot-up in PowerShell 4.0, see [Want to Automatically Configure Your Machines Using DSC at Initial Boot-up?](https://blogs.msdn.microsoft.com/powershell/2014/02/28/want-to-automatically-configure-your-machines-using-dsc-at-initial-boot-up/)</span></span>

<span data-ttu-id="469d7-108">Om uit te voeren van deze voorbeelden, hebt u het volgende nodig:</span><span class="sxs-lookup"><span data-stu-id="469d7-108">To run these examples, you will need:</span></span>

- <span data-ttu-id="469d7-109">Een opstartbare virtuele harde schijf om te werken met.</span><span class="sxs-lookup"><span data-stu-id="469d7-109">A bootable VHD to work with.</span></span> <span data-ttu-id="469d7-110">U kunt een ISO met een evaluatieversie van Windows Server 2016 op downloaden [TechNet Evaluation Center](https://www.microsoft.com/en-us/evalcenter/evaluate-windows-server-2016).</span><span class="sxs-lookup"><span data-stu-id="469d7-110">You can download an ISO with an evaluation copy of Windows Server 2016 at [TechNet Evaluation Center](https://www.microsoft.com/en-us/evalcenter/evaluate-windows-server-2016).</span></span>
  <span data-ttu-id="469d7-111">U vindt instructies over het maken van een VHD van een ISO-installatiekopie op [opstartbare virtuele Hardeschijven maken](/previous-versions/windows/it-pro/windows-7/gg318049(v=ws.10)).</span><span class="sxs-lookup"><span data-stu-id="469d7-111">You can find instructions on how to create a VHD from an ISO image at [Creating Bootable Virtual Hard Disks](/previous-versions/windows/it-pro/windows-7/gg318049(v=ws.10)).</span></span>
- <span data-ttu-id="469d7-112">Een hostcomputer waarop Hyper-V is ingeschakeld.</span><span class="sxs-lookup"><span data-stu-id="469d7-112">A host computer that has Hyper-V enabled.</span></span> <span data-ttu-id="469d7-113">Zie voor meer informatie, [overzicht van Hyper-V](/previous-versions/windows/it-pro/windows-server-2012-R2-and-2012/hh831531(v=ws.11)).</span><span class="sxs-lookup"><span data-stu-id="469d7-113">For information, see [Hyper-V overview](/previous-versions/windows/it-pro/windows-server-2012-R2-and-2012/hh831531(v=ws.11)).</span></span>

  <span data-ttu-id="469d7-114">U kunt software-installatie en configuratie voor een computer bij de eerste keer opstarten automatiseren met behulp van DSC.</span><span class="sxs-lookup"><span data-stu-id="469d7-114">By using DSC, you can automate software installation and configuration for a computer at initial boot-up.</span></span>
  <span data-ttu-id="469d7-115">U doen dit door een van beide injecteren van een MOF-configuratiebestand of een metaconfiguration in opstartbare media (zoals een VHD) zodat ze worden uitgevoerd tijdens de eerste keer opstarten.</span><span class="sxs-lookup"><span data-stu-id="469d7-115">You do this by either injecting a configuration MOF document or a metaconfiguration into bootable media (such as a VHD) so that they are run during the initial boot-up process.</span></span>
  <span data-ttu-id="469d7-116">Dit gedrag is opgegeven door de [de registersleutel dscautomationhostenabled](DSCAutomationHostEnabled.md) registersleutel onder `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion\Policies\System`.</span><span class="sxs-lookup"><span data-stu-id="469d7-116">This behavior is specified by the [DSCAutomationHostEnabled registry key](DSCAutomationHostEnabled.md) registry key under `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion\Policies\System`.</span></span>
  <span data-ttu-id="469d7-117">Standaard is de waarde van deze sleutel 2, waarmee DSC om uit te voeren bij het opstarten.</span><span class="sxs-lookup"><span data-stu-id="469d7-117">By default, the value of this key is 2, which allows DSC to run at boot time.</span></span>

  <span data-ttu-id="469d7-118">Als u niet dat DSC om uit te voeren bij het opstarten wilt, stel de waarde van de [de registersleutel dscautomationhostenabled](DSCAutomationHostEnabled.md) registersleutel in op 0.</span><span class="sxs-lookup"><span data-stu-id="469d7-118">If you do not want DSC to run at boot time, set the value of the [DSCAutomationHostEnabled registry key](DSCAutomationHostEnabled.md) registry key to 0.</span></span>

- <span data-ttu-id="469d7-119">Een MOF-configuratiebestand invoeren in een VHD</span><span class="sxs-lookup"><span data-stu-id="469d7-119">Inject a configuration MOF document into a VHD</span></span>
- <span data-ttu-id="469d7-120">Een DSC-metaconfiguration invoeren in een VHD</span><span class="sxs-lookup"><span data-stu-id="469d7-120">Inject a DSC metaconfiguration into a VHD</span></span>
- <span data-ttu-id="469d7-121">DSC bij het opstarten uitschakelen</span><span class="sxs-lookup"><span data-stu-id="469d7-121">Disable DSC at boot time</span></span>

> [!NOTE]
> <span data-ttu-id="469d7-122">U kunt beide invoeren `Pending.mof` en `MetaConfig.mof` bij een computer op hetzelfde moment.</span><span class="sxs-lookup"><span data-stu-id="469d7-122">You can inject both `Pending.mof` and `MetaConfig.mof` into a computer at the same time.</span></span>
> <span data-ttu-id="469d7-123">Als beide bestanden aanwezig zijn, de instellingen zijn opgegeven in `MetaConfig.mof` voorrang.</span><span class="sxs-lookup"><span data-stu-id="469d7-123">If both files are present, the settings specified in `MetaConfig.mof` take precedence.</span></span>

## <a name="inject-a-configuration-mof-document-into-a-vhd"></a><span data-ttu-id="469d7-124">Een MOF-configuratiebestand invoeren in een VHD</span><span class="sxs-lookup"><span data-stu-id="469d7-124">Inject a configuration MOF document into a VHD</span></span>

<span data-ttu-id="469d7-125">Als u wilt een configuratie bij de eerste keer opstarten gerapporteerd, kunt u een gecompileerde configuratie MOF-document invoeren in de VHD als de `Pending.mof` bestand.</span><span class="sxs-lookup"><span data-stu-id="469d7-125">To enact a configuration at initial boot-up, you can inject a compiled configuration MOF document into the VHD as its `Pending.mof` file.</span></span>
<span data-ttu-id="469d7-126">Als de **DSCAutomationHostEnabled** registersleutel is ingesteld op 2 (standaardwaarde), DSC geldt de configuratie die is gedefinieerd door `Pending.mof` wanneer de computer voor de eerste keer wordt opgestart.</span><span class="sxs-lookup"><span data-stu-id="469d7-126">If the **DSCAutomationHostEnabled** registry key is set to 2 (the default value), DSC will apply the configuration defined by `Pending.mof` when the computer boots up for the first time.</span></span>

<span data-ttu-id="469d7-127">Voor dit voorbeeld gebruiken we de volgende configuratie, waarop IIS wordt geïnstalleerd op de nieuwe computer:</span><span class="sxs-lookup"><span data-stu-id="469d7-127">For this example, we will use the following configuration, which will install IIS on the new computer:</span></span>

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

### <a name="to-inject-the-configuration-mof-document-on-the-vhd"></a><span data-ttu-id="469d7-128">Naar het MOF-configuratiebestand op de VHD invoeren</span><span class="sxs-lookup"><span data-stu-id="469d7-128">To inject the configuration MOF document on the VHD</span></span>

1. <span data-ttu-id="469d7-129">Koppel de VHD waarnaar u invoeren van de configuratie wilt door het aanroepen van de [VHD koppelen](/powershell/module/hyper-v/mount-vhd) cmdlet.</span><span class="sxs-lookup"><span data-stu-id="469d7-129">Mount the VHD into which you want to inject the configuration by calling the [Mount-VHD](/powershell/module/hyper-v/mount-vhd) cmdlet.</span></span> <span data-ttu-id="469d7-130">Bijvoorbeeld:</span><span class="sxs-lookup"><span data-stu-id="469d7-130">For example:</span></span>

   ```powershell
   Mount-VHD -Path C:\users\public\documents\vhd\Srv16.vhd
   ```

2. <span data-ttu-id="469d7-131">Op een computer waarop PowerShell 5.0 of hoger, sla de bovenstaande configuratie (**SampleIISInstall**) als een PowerShell-script (.ps1)-bestand.</span><span class="sxs-lookup"><span data-stu-id="469d7-131">On a computer running PowerShell 5.0 or later, save the above configuration (**SampleIISInstall**) as a PowerShell script (.ps1) file.</span></span>

3. <span data-ttu-id="469d7-132">Navigeer naar de map waar u de .ps1-bestand hebt opgeslagen in een PowerShell-console.</span><span class="sxs-lookup"><span data-stu-id="469d7-132">In a PowerShell console, navigate to the folder where you saved the .ps1 file.</span></span>

4. <span data-ttu-id="469d7-133">Voer de volgende PowerShell-opdrachten voor het compileren van het MOF-document (Zie voor meer informatie over DSC-configuraties compileren [DSC-configuraties](../configurations/configurations.md):</span><span class="sxs-lookup"><span data-stu-id="469d7-133">Run the following PowerShell commands to compile the MOF document (for information about compiling DSC configurations, see [DSC Configurations](../configurations/configurations.md):</span></span>

   ```powershell
   . .\SampleIISInstall.ps1
   SampleIISInstall
   ```

5. <span data-ttu-id="469d7-134">Hiermee maakt u een `localhost.mof` bestand in een nieuwe map met de naam `SampleIISInstall`.</span><span class="sxs-lookup"><span data-stu-id="469d7-134">This will create a `localhost.mof` file in a new folder named `SampleIISInstall`.</span></span>
   <span data-ttu-id="469d7-135">Wijzig de naam en dat bestand verplaatsen naar de juiste locatie op de VHD als `Pending.mof` met behulp van de [Item verplaatsen](/powershell/module/microsoft.powershell.management/move-item) cmdlet.</span><span class="sxs-lookup"><span data-stu-id="469d7-135">Rename and move that file into the proper location on the VHD as `Pending.mof` by using the [Move-Item](/powershell/module/microsoft.powershell.management/move-item) cmdlet.</span></span> <span data-ttu-id="469d7-136">Bijvoorbeeld:</span><span class="sxs-lookup"><span data-stu-id="469d7-136">For example:</span></span>

   ```powershell
       Move-Item -Path C:\DSCTest\SampleIISInstall\localhost.mof -Destination E:\Windows\System32\Configuration\Pending.mof
   ```

6. <span data-ttu-id="469d7-137">Ontkoppelen van de VHD door het aanroepen van de [Dismount-VHD](/powershell/module/hyper-v/dismount-vhd) cmdlet.</span><span class="sxs-lookup"><span data-stu-id="469d7-137">Dismount the VHD by calling the [Dismount-VHD](/powershell/module/hyper-v/dismount-vhd) cmdlet.</span></span> <span data-ttu-id="469d7-138">Bijvoorbeeld:</span><span class="sxs-lookup"><span data-stu-id="469d7-138">For example:</span></span>

   ```powershell
   Dismount-VHD -Path C:\users\public\documents\vhd\Srv16.vhd
   ```

7. <span data-ttu-id="469d7-139">Een virtuele machine maken met behulp van de installatie van de DSC MOF-document VHD.</span><span class="sxs-lookup"><span data-stu-id="469d7-139">Create a VM by using the VHD where you installed the DSC MOF document.</span></span>

<span data-ttu-id="469d7-140">Na het eerste boot-up en installatie van besturingssysteem, wordt IIS geïnstalleerd.</span><span class="sxs-lookup"><span data-stu-id="469d7-140">After intial boot-up and operating system installation, IIS will be installed.</span></span>
<span data-ttu-id="469d7-141">U kunt dit controleren door het aanroepen van de [Get-WindowsFeature](/powershell/module/servermanager/get-windowsfeature) cmdlet.</span><span class="sxs-lookup"><span data-stu-id="469d7-141">You can verify this by calling the [Get-WindowsFeature](/powershell/module/servermanager/get-windowsfeature) cmdlet.</span></span>

## <a name="inject-a-dsc-metaconfiguration-into-a-vhd"></a><span data-ttu-id="469d7-142">Een DSC-metaconfiguration invoeren in een VHD</span><span class="sxs-lookup"><span data-stu-id="469d7-142">Inject a DSC metaconfiguration into a VHD</span></span>

<span data-ttu-id="469d7-143">U kunt ook een computer om op te halen van een configuratie bij de eerste keer opstarten door het injecteren van een metaconfiguration configureren (Zie [de lokale Configuration Manager (LCM) configureren](../managing-nodes/metaConfig.md)) in de VHD als de `MetaConfig.mof` bestand.</span><span class="sxs-lookup"><span data-stu-id="469d7-143">You can also configure a computer to pull a configuration at intial boot-up by injecting a metaconfiguration (see [Configuring the Local Configuration Manager (LCM)](../managing-nodes/metaConfig.md)) into the VHD as its `MetaConfig.mof` file.</span></span>
<span data-ttu-id="469d7-144">Als de **DSCAutomationHostEnabled** registersleutel is ingesteld op 2 (standaardwaarde), DSC geldt de metaconfiguration gedefinieerd door `MetaConfig.mof` naar de LCM wanneer de computer voor de eerste keer wordt opgestart.</span><span class="sxs-lookup"><span data-stu-id="469d7-144">If the **DSCAutomationHostEnabled** registry key is set to 2 (the default value),  DSC will apply the metaconfiguration defined by `MetaConfig.mof` to the LCM when the computer boots up for the first time.</span></span>
<span data-ttu-id="469d7-145">Als de metaconfiguration geeft aan dat de LCM-configuraties van een pull-server moet halen, probeert de computer voor het ophalen van een configuratie van die pull-server bij de eerste keer opstarten.</span><span class="sxs-lookup"><span data-stu-id="469d7-145">If the metaconfiguration specifies that the LCM should pull configurations from a pull server, the computer will attempt to pull a configuration from that pull server at inital boot-up.</span></span>
<span data-ttu-id="469d7-146">Zie voor meer informatie over het instellen van een DSC-pull-server [instellen van een DSC-pull-endwebserver](../pull-server/pullServer.md).</span><span class="sxs-lookup"><span data-stu-id="469d7-146">For information about setting up a DSC pull server, see [Setting up a DSC web pull server](../pull-server/pullServer.md).</span></span>

<span data-ttu-id="469d7-147">Voor dit voorbeeld gebruiken we zowel de configuratie wordt beschreven in de vorige sectie (**SampleIISInstall**), en de volgende metaconfiguration:</span><span class="sxs-lookup"><span data-stu-id="469d7-147">For this example, we will use both the configuration described in the previous section (**SampleIISInstall**), and the following metaconfiguration:</span></span>

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

### <a name="to-inject-the-metaconfiguration-mof-document-on-the-vhd"></a><span data-ttu-id="469d7-148">Aan de metaconfiguration MOF-document op de VHD invoeren</span><span class="sxs-lookup"><span data-stu-id="469d7-148">To inject the metaconfiguration MOF document on the VHD</span></span>

1. <span data-ttu-id="469d7-149">Koppel de VHD waarnaar u de metaconfiguration invoeren wilt door het aanroepen van de [VHD koppelen](/powershell/module/hyper-v/mount-vhd) cmdlet.</span><span class="sxs-lookup"><span data-stu-id="469d7-149">Mount the VHD into which you want to inject the metaconfiguration by calling the [Mount-VHD](/powershell/module/hyper-v/mount-vhd) cmdlet.</span></span> <span data-ttu-id="469d7-150">Bijvoorbeeld:</span><span class="sxs-lookup"><span data-stu-id="469d7-150">For example:</span></span>

   ```powershell
   Mount-VHD -Path C:\users\public\documents\vhd\Srv16.vhd
   ```

2. <span data-ttu-id="469d7-151">[Instellen van een DSC-pull-endwebserver](../pull-server/pullServer.md), en sla de **SampleIISInistall** configuratie naar de juiste map.</span><span class="sxs-lookup"><span data-stu-id="469d7-151">[Set up a DSC web pull server](../pull-server/pullServer.md), and save the **SampleIISInistall** configuration to the appropriate folder.</span></span>

3. <span data-ttu-id="469d7-152">Op een computer waarop PowerShell 5.0 of hoger, sla de bovenstaande metaconfiguration (**PullClientBootstrap**) als een PowerShell-script (.ps1)-bestand.</span><span class="sxs-lookup"><span data-stu-id="469d7-152">On a computer running PowerShell 5.0 or later, save the above metaconfiguration (**PullClientBootstrap**) as a PowerShell script (.ps1) file.</span></span>

4. <span data-ttu-id="469d7-153">Navigeer naar de map waar u de .ps1-bestand hebt opgeslagen in een PowerShell-console.</span><span class="sxs-lookup"><span data-stu-id="469d7-153">In a PowerShell console, navigate to the folder where you saved the .ps1 file.</span></span>

5. <span data-ttu-id="469d7-154">Voer de volgende PowerShell-opdrachten voor het compileren van het metaconfiguration MOF-document (Zie voor meer informatie over DSC-configuraties compileren [DSC-configuraties](../configurations/configurations.md):</span><span class="sxs-lookup"><span data-stu-id="469d7-154">Run the following PowerShell commands to compile the  metaconfiguration MOF document (for information about compiling DSC configurations, see [DSC Configurations](../configurations/configurations.md):</span></span>

   ```powershell
   . .\PullClientBootstrap.ps1
   PullClientBootstrap
   ```

6. <span data-ttu-id="469d7-155">Hiermee maakt u een `localhost.meta.mof` bestand in een nieuwe map met de naam `PullClientBootstrap`.</span><span class="sxs-lookup"><span data-stu-id="469d7-155">This will create a `localhost.meta.mof` file in a new folder named `PullClientBootstrap`.</span></span>
   <span data-ttu-id="469d7-156">Wijzig de naam en dat bestand verplaatsen naar de juiste locatie op de VHD als `MetaConfig.mof` met behulp van de [Item verplaatsen](/powershell/module/microsoft.powershell.management/move-item) cmdlet.</span><span class="sxs-lookup"><span data-stu-id="469d7-156">Rename and move that file into the proper location on the VHD as `MetaConfig.mof` by using the [Move-Item](/powershell/module/microsoft.powershell.management/move-item) cmdlet.</span></span>

   ```powershell
   Move-Item -Path C:\DSCTest\PullClientBootstrap\localhost.meta.mof -Destination E:\Windows\System32\Configuration\MetaConfig.mof
   ```

7. <span data-ttu-id="469d7-157">Ontkoppelen van de VHD door het aanroepen van de [Dismount-VHD](/powershell/module/hyper-v/dismount-vhd) cmdlet.</span><span class="sxs-lookup"><span data-stu-id="469d7-157">Dismount the VHD by calling the [Dismount-VHD](/powershell/module/hyper-v/dismount-vhd) cmdlet.</span></span> <span data-ttu-id="469d7-158">Bijvoorbeeld:</span><span class="sxs-lookup"><span data-stu-id="469d7-158">For example:</span></span>

   ```powershell
   Dismount-VHD -Path C:\users\public\documents\vhd\Srv16.vhd
   ```

8. <span data-ttu-id="469d7-159">Een virtuele machine maken met behulp van de installatie van de DSC MOF-document VHD.</span><span class="sxs-lookup"><span data-stu-id="469d7-159">Create a VM by using the VHD where you installed the DSC MOF document.</span></span>

<span data-ttu-id="469d7-160">Na het eerste boot-up en installatie van besturingssysteem, DSC klikt, wordt de configuratie van de pull-server en IIS wordt geïnstalleerd.</span><span class="sxs-lookup"><span data-stu-id="469d7-160">After intial boot-up and operating system installation, DSC will pull the configuration from the pull server, and IIS will be installed.</span></span>
<span data-ttu-id="469d7-161">U kunt dit controleren door het aanroepen van de [Get-WindowsFeature](/powershell/module/servermanager/get-windowsfeature) cmdlet.</span><span class="sxs-lookup"><span data-stu-id="469d7-161">You can verify this by calling the [Get-WindowsFeature](/powershell/module/servermanager/get-windowsfeature) cmdlet.</span></span>

## <a name="disable-dsc-at-boot-time"></a><span data-ttu-id="469d7-162">DSC bij het opstarten uitschakelen</span><span class="sxs-lookup"><span data-stu-id="469d7-162">Disable DSC at boot time</span></span>

<span data-ttu-id="469d7-163">Standaard is de waarde van de `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion\Policies\System\DSCAutomationHostEnabled` sleutel is ingesteld op 2, waarmee een DSC-configuratie voor het uitvoeren als de computer is in behandeling of de huidige status.</span><span class="sxs-lookup"><span data-stu-id="469d7-163">By default, the value of the `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion\Policies\System\DSCAutomationHostEnabled` key is set to 2, which allows a DSC configuration to run if the computer is in pending or current state.</span></span> <span data-ttu-id="469d7-164">Als u niet dat een configuratie om uit te voeren bij de eerste keer opstarten wilt, moet u dus de waarde van deze sleutel instellen op 0:</span><span class="sxs-lookup"><span data-stu-id="469d7-164">If you do not want a configuration to run at initial boot-up, you need so set the value of this key to 0:</span></span>

1. <span data-ttu-id="469d7-165">De VHD koppelen door het aanroepen van de [VHD koppelen](/powershell/module/hyper-v/mount-vhd) cmdlet.</span><span class="sxs-lookup"><span data-stu-id="469d7-165">Mount the VHD by calling the [Mount-VHD](/powershell/module/hyper-v/mount-vhd) cmdlet.</span></span> <span data-ttu-id="469d7-166">Bijvoorbeeld:</span><span class="sxs-lookup"><span data-stu-id="469d7-166">For example:</span></span>

   ```powershell
   Mount-VHD -Path C:\users\public\documents\vhd\Srv16.vhd
   ```

2. <span data-ttu-id="469d7-167">Laden van het register `HKLM\Software` subsleutel van de VHD door het aanroepen van `reg load`.</span><span class="sxs-lookup"><span data-stu-id="469d7-167">Load the registry `HKLM\Software` subkey from the VHD by calling `reg load`.</span></span>

   ```powershell
   reg load HKLM\Vhd E:\Windows\System32\Config\Software`
   ```

3. <span data-ttu-id="469d7-168">Navigeer naar de `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion\Policies\System` met behulp van de PowerShell-registerprovider.</span><span class="sxs-lookup"><span data-stu-id="469d7-168">Navigate to the `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion\Policies\System` by using the PowerShell Registry provider.</span></span>

   ```powershell
   Set-Location HKLM:\Software\Microsoft\Windows\CurrentVersion\Policies\System`
   ```

4. <span data-ttu-id="469d7-169">Wijzig de waarde van `DSCAutomationHostEnabled` op 0.</span><span class="sxs-lookup"><span data-stu-id="469d7-169">Change the value of `DSCAutomationHostEnabled` to 0.</span></span>

   ```powershell
   Set-ItemProperty -Path . -Name DSCAutomationHostEnabled -Value 0
   ```

5. <span data-ttu-id="469d7-170">Het register verwijderen door het uitvoeren van de volgende opdrachten:</span><span class="sxs-lookup"><span data-stu-id="469d7-170">Unload the registry by running the following commands:</span></span>

   ```powershell
   [gc]::Collect()
   reg unload HKLM\Vhd
   ```

## <a name="see-also"></a><span data-ttu-id="469d7-171">Zie ook</span><span class="sxs-lookup"><span data-stu-id="469d7-171">See Also</span></span>

[<span data-ttu-id="469d7-172">DSC-configuraties</span><span class="sxs-lookup"><span data-stu-id="469d7-172">DSC Configurations</span></span>](../configurations/configurations.md)

[<span data-ttu-id="469d7-173">De registersleutel DSCAutomationHostEnabled</span><span class="sxs-lookup"><span data-stu-id="469d7-173">DSCAutomationHostEnabled registry key</span></span>](DSCAutomationHostEnabled.md)

[<span data-ttu-id="469d7-174">De Local Configuration Manager (LCM) configureren</span><span class="sxs-lookup"><span data-stu-id="469d7-174">Configuring the Local Configuration Manager (LCM)</span></span>](../managing-nodes/metaConfig.md)

[<span data-ttu-id="469d7-175">Instellen van een DSC-pull-endwebserver</span><span class="sxs-lookup"><span data-stu-id="469d7-175">Setting up a DSC web pull server</span></span>](../pull-server/pullServer.md)
