---
ms.date: 06/12/2017
ms.topic: conceptual
keywords: wmf,powershell,installeren
contributor: keithb
title: Installeren en configureren van WMF 5.1
ms.openlocfilehash: c439d0851189a89a81fa38194632dc54475a001d
ms.sourcegitcommit: caac7d098a448232304c9d6728e7340ec7517a71
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 03/16/2019
ms.locfileid: "58055983"
---
# <a name="install-and-configure-wmf-51"></a><span data-ttu-id="b0770-103">Installeren en configureren van WMF 5.1</span><span class="sxs-lookup"><span data-stu-id="b0770-103">Install and Configure WMF 5.1</span></span>

## <a name="download-and-install-the-wmf-51-package"></a><span data-ttu-id="b0770-104">Download en installeer het pakket WMF 5.1</span><span class="sxs-lookup"><span data-stu-id="b0770-104">Download and install the WMF 5.1 package</span></span>

<span data-ttu-id="b0770-105">Download het WMF 5.1-pakket voor het besturingssysteem en de architectuur die u installeren wilt op:</span><span class="sxs-lookup"><span data-stu-id="b0770-105">Download the WMF 5.1 package for the operating system and architecture you wish to install it on:</span></span>

| <span data-ttu-id="b0770-106">Besturingssysteem</span><span class="sxs-lookup"><span data-stu-id="b0770-106">Operating System</span></span>       | <span data-ttu-id="b0770-107">Vereisten</span><span class="sxs-lookup"><span data-stu-id="b0770-107">Prerequisites</span></span>           | <span data-ttu-id="b0770-108">Pakket-koppelingen</span><span class="sxs-lookup"><span data-stu-id="b0770-108">Package Links</span></span>                          |
|------------------------|-------------------------|----------------------------------------|
| <span data-ttu-id="b0770-109">Windows Server 2012 R2</span><span class="sxs-lookup"><span data-stu-id="b0770-109">Windows Server 2012 R2</span></span> |                         | <span data-ttu-id="b0770-110">[Win8.1AndW2K12R2-KB3191564-x64.msu][]</span><span class="sxs-lookup"><span data-stu-id="b0770-110">[Win8.1AndW2K12R2-KB3191564-x64.msu][]</span></span> |
| <span data-ttu-id="b0770-111">Windows Server 2012</span><span class="sxs-lookup"><span data-stu-id="b0770-111">Windows Server 2012</span></span>    |                         | <span data-ttu-id="b0770-112">[W2K12-KB3191565-x64.msu][]</span><span class="sxs-lookup"><span data-stu-id="b0770-112">[W2K12-KB3191565-x64.msu][]</span></span>            |
| <span data-ttu-id="b0770-113">Windows Server 2008 R2</span><span class="sxs-lookup"><span data-stu-id="b0770-113">Windows Server 2008 R2</span></span> | <span data-ttu-id="b0770-114">[.NET Framework 4.5.2][]</span><span class="sxs-lookup"><span data-stu-id="b0770-114">[.NET Framework 4.5.2][]</span></span>| <span data-ttu-id="b0770-115">[Win7AndW2K8R2-KB3191566-x64.ZIP][]</span><span class="sxs-lookup"><span data-stu-id="b0770-115">[Win7AndW2K8R2-KB3191566-x64.ZIP][]</span></span>    |
| <span data-ttu-id="b0770-116">Windows 8.1</span><span class="sxs-lookup"><span data-stu-id="b0770-116">Windows 8.1</span></span>            |                         | <span data-ttu-id="b0770-117">**x64:** [Win8.1AndW2K12R2-KB3191564-x64.msu][]</span><span class="sxs-lookup"><span data-stu-id="b0770-117">**x64:** [Win8.1AndW2K12R2-KB3191564-x64.msu][]</span></span></br><span data-ttu-id="b0770-118">**x86:** [Win8.1-KB3191564-x86.msu][]</span><span class="sxs-lookup"><span data-stu-id="b0770-118">**x86:** [Win8.1-KB3191564-x86.msu][]</span></span> |
| <span data-ttu-id="b0770-119">Windows 7 SP1</span><span class="sxs-lookup"><span data-stu-id="b0770-119">Windows 7 SP1</span></span>          | <span data-ttu-id="b0770-120">[.NET Framework 4.5.2][]</span><span class="sxs-lookup"><span data-stu-id="b0770-120">[.NET Framework 4.5.2][]</span></span>| <span data-ttu-id="b0770-121">**x64:** [Win7AndW2K8R2-KB3191566-x64.ZIP][]</span><span class="sxs-lookup"><span data-stu-id="b0770-121">**x64:** [Win7AndW2K8R2-KB3191566-x64.ZIP][]</span></span></br><span data-ttu-id="b0770-122">**x86:** [Win7-KB3191566-x86.ZIP][]</span><span class="sxs-lookup"><span data-stu-id="b0770-122">**x86:** [Win7-KB3191566-x86.ZIP][]</span></span> |

[.NET Framework 4.5.2]: https://www.microsoft.com/download/details.aspx?id=42642
[W2K12-KB3191565-x64.msu]: https://go.microsoft.com/fwlink/?linkid=839513
[Win7-KB3191566-x86.ZIP]: https://go.microsoft.com/fwlink/?linkid=839522
[Win7AndW2K8R2-KB3191566-x64.ZIP]: https://go.microsoft.com/fwlink/?linkid=839523
[Win8.1-KB3191564-x86.msu]: https://go.microsoft.com/fwlink/?linkid=839521
[Win8.1AndW2K12R2-KB3191564-x64.msu]: https://go.microsoft.com/fwlink/?linkid=839516

## <a name="install-wmf-51-for-windows-server-2008-r2-and-windows-7"></a><span data-ttu-id="b0770-129">WMF 5.1 voor Windows Server 2008 R2 en Windows 7 installeren</span><span class="sxs-lookup"><span data-stu-id="b0770-129">Install WMF 5.1 for Windows Server 2008 R2 and Windows 7</span></span>

> [!NOTE]
> <span data-ttu-id="b0770-130">Installatie-instructies voor Windows Server 2008 R2 en Windows 7 zijn gewijzigd en verschillen van de instructies voor de andere pakketten.</span><span class="sxs-lookup"><span data-stu-id="b0770-130">Installation instructions for Windows Server 2008 R2 and Windows 7 have changed, and differ from the instructions for the other packages.</span></span> <span data-ttu-id="b0770-131">Installatie-instructies voor Windows Server 2012 R2, Windows Server 2012 en Windows 8.1 staan hieronder.</span><span class="sxs-lookup"><span data-stu-id="b0770-131">Installation instructions for Windows Server 2012 R2, Windows Server 2012, and Windows 8.1 are below.</span></span>

<span data-ttu-id="b0770-132">**WMF 5.1 installeren op Windows Server 2008 R2 en Windows 7**</span><span class="sxs-lookup"><span data-stu-id="b0770-132">**Installing WMF 5.1 on Windows Server 2008 R2 and Windows 7**</span></span>

1. <span data-ttu-id="b0770-133">Navigeer naar de map waarin u het ZIP-bestand hebt gedownload.</span><span class="sxs-lookup"><span data-stu-id="b0770-133">Navigate to the folder into which you downloaded the ZIP file.</span></span>

2. <span data-ttu-id="b0770-134">Met de rechtermuisknop op het ZIP-bestand en selecteer 'Ophalen van alle...'.</span><span class="sxs-lookup"><span data-stu-id="b0770-134">Right-click on the ZIP file, and select "Extract All...".</span></span> <span data-ttu-id="b0770-135">Het ZIP-bestand bevat bestanden 2: een MSU- en het scriptbestand voor installatie-WMF5.1.PS1.</span><span class="sxs-lookup"><span data-stu-id="b0770-135">The Zip contains 2 files: an MSU and the Install-WMF5.1.PS1 script file.</span></span>
<span data-ttu-id="b0770-136">Zodra u het ZIP-bestand hebt uitgepakt, kunt u de inhoud kopiëren naar een machine met Windows 7 of Windows Server 2008 R2.</span><span class="sxs-lookup"><span data-stu-id="b0770-136">Once you have unpacked the ZIP file, you can copy the contents to any machine running Windows 7 or Windows Server 2008 R2.</span></span>

3. <span data-ttu-id="b0770-137">Nadat de inhoud van het ZIP-bestand uitpakken, open PowerShell als beheerder en navigeer naar de map met de inhoud van het ZIP-bestand.</span><span class="sxs-lookup"><span data-stu-id="b0770-137">After extracting the ZIP file contents, open PowerShell as administrator, then navigate to the folder containing the contents of the ZIP file.</span></span>

4. <span data-ttu-id="b0770-138">Het script Install-Wmf5.1.ps1 uitvoeren in die map en volg de instructies.</span><span class="sxs-lookup"><span data-stu-id="b0770-138">Run the Install-Wmf5.1.ps1 script in that folder, and follow the instructions.</span></span> <span data-ttu-id="b0770-139">Dit script wordt Controleer de vereisten op de lokale computer en WMF 5.1 installeren als de vereisten wordt voldaan.</span><span class="sxs-lookup"><span data-stu-id="b0770-139">This script will check the prerequisites on the local machine, and install WMF 5.1 if the prerequisites have been met.</span></span> <span data-ttu-id="b0770-140">De vereisten worden hieronder vermeld.</span><span class="sxs-lookup"><span data-stu-id="b0770-140">The prerequisites are listed below.</span></span>

<span data-ttu-id="b0770-141">Installatie-WMF5.1.ps1 bevat de volgende parameters om de automatisering van de installatie op Windows Server 2008 R2 en Windows 7:</span><span class="sxs-lookup"><span data-stu-id="b0770-141">Install-WMF5.1.ps1 takes the following parameters to ease automating the installation on Windows Server 2008 R2 and Windows 7:</span></span>

- <span data-ttu-id="b0770-142">AcceptEula: Als deze parameter opgenomen is, wordt de gebruiksrechtovereenkomst wordt automatisch geaccepteerd en worden niet weergegeven.</span><span class="sxs-lookup"><span data-stu-id="b0770-142">AcceptEula: When this parameter is included, the EULA is automatically accepted and will not be displayed.</span></span>
- <span data-ttu-id="b0770-143">AllowRestart: Deze parameter kan alleen worden gebruikt als AcceptEula is opgegeven.</span><span class="sxs-lookup"><span data-stu-id="b0770-143">AllowRestart: This parameter can only be used if AcceptEula is specified.</span></span> <span data-ttu-id="b0770-144">Als deze parameter opgenomen is en een moet opnieuw opgestart worden na de installatie van WMF 5.1, gebeurt het opnieuw opstarten zonder tussenkomst van onmiddellijk nadat de installatie is voltooid.</span><span class="sxs-lookup"><span data-stu-id="b0770-144">If this parameter is included, and a restart is required after installing WMF 5.1, the restart will happen without prompting immediately after the installation is completed.</span></span>

<span data-ttu-id="b0770-145">**WMF 5.1 vereisten voor Windows Server 2008 R2 SP1 en Windows 7 SP1**</span><span class="sxs-lookup"><span data-stu-id="b0770-145">**WMF 5.1 Prerequisites for Windows Server 2008 R2 SP1 and Windows 7 SP1**</span></span>

<span data-ttu-id="b0770-146">Installatie van WMF 5.1 op Windows Server 2008 R2 SP1 of Windows 7 SP1, is het volgende vereist:</span><span class="sxs-lookup"><span data-stu-id="b0770-146">Installation of WMF 5.1 on either Windows Server 2008 R2 SP1 or Windows 7 SP1, requires the following:</span></span>
- <span data-ttu-id="b0770-147">Meest recente servicepack moet worden geïnstalleerd.</span><span class="sxs-lookup"><span data-stu-id="b0770-147">Latest service pack must be installed.</span></span>
- <span data-ttu-id="b0770-148">WMF 3.0 **moet niet** worden geïnstalleerd.</span><span class="sxs-lookup"><span data-stu-id="b0770-148">WMF 3.0 **must not** be installed.</span></span> <span data-ttu-id="b0770-149">WMF 5.1 installeren via WMF 3.0 zal leiden tot verlies van de PSModulePath, wat leiden andere toepassingen tot kan mislukken.</span><span class="sxs-lookup"><span data-stu-id="b0770-149">Installing WMF 5.1 over WMF 3.0 will result in the loss of the PSModulePath, which can cause other applications to fail.</span></span> <span data-ttu-id="b0770-150">Voor de installatie van WMF 5.1, een van beide ongedaan maken-Installeer WMF 3.0, moet u of de PSModulePath opslaan en vervolgens handmatig herstellen nadat WMF 5.1-installatie voltooid is.</span><span class="sxs-lookup"><span data-stu-id="b0770-150">Before installing WMF 5.1, you must either un-install WMF 3.0, or save the PSModulePath and then restore it manually after WMF 5.1 installation is complete.</span></span>
- <span data-ttu-id="b0770-151">WMF 5.1 vereist ten minste [.NET Framework 4.5.2](https://www.microsoft.com/en-ca/download/details.aspx?id=42642).</span><span class="sxs-lookup"><span data-stu-id="b0770-151">WMF 5.1 requires at least [.NET Framework 4.5.2](https://www.microsoft.com/en-ca/download/details.aspx?id=42642).</span></span>
<span data-ttu-id="b0770-152">U kunt Microsoft .NET Framework 4.5.2 installeren door de instructies op de downloadlocatie.</span><span class="sxs-lookup"><span data-stu-id="b0770-152">You can install Microsoft .NET Framework 4.5.2 by following the instructions at the download location.</span></span>

<span data-ttu-id="b0770-153">**WinRM Dependency**</span><span class="sxs-lookup"><span data-stu-id="b0770-153">**WinRM Dependency**</span></span>

<span data-ttu-id="b0770-154">Windows PowerShell Desired State Configuration (DSC), is afhankelijk van WinRM.</span><span class="sxs-lookup"><span data-stu-id="b0770-154">Windows PowerShell Desired State Configuration (DSC) depends on WinRM.</span></span>
<span data-ttu-id="b0770-155">WinRM is niet standaard ingeschakeld op Windows Server 2008 R2 en Windows 7.</span><span class="sxs-lookup"><span data-stu-id="b0770-155">WinRM is not enabled by default on Windows Server 2008 R2 and Windows 7.</span></span>
<span data-ttu-id="b0770-156">Voer `Set-WSManQuickConfig`, in een Windows PowerShell met verhoogde bevoegdheden om in te schakelen WinRM-sessie.</span><span class="sxs-lookup"><span data-stu-id="b0770-156">Run `Set-WSManQuickConfig`, in a Windows PowerShell elevated session, to enable WinRM.</span></span>

## <a name="install-wmf-51-for-windows-server-2012-r2-windows-server-2012-and-windows-81"></a><span data-ttu-id="b0770-157">WMF 5.1 installeren voor Windows Server 2012 R2, WindowsServer 2012 en Windows 8.1</span><span class="sxs-lookup"><span data-stu-id="b0770-157">Install WMF 5.1 for Windows Server 2012 R2, Windows Server 2012, and Windows 8.1</span></span>

<span data-ttu-id="b0770-158">**Installeren in Windows Explorer (of een Verkenner in Windows Server 2012 R2 of Windows 8.1)**</span><span class="sxs-lookup"><span data-stu-id="b0770-158">**Install from Windows Explorer (or File Explorer in Windows Server 2012 R2 or Windows 8.1)**</span></span>

1. <span data-ttu-id="b0770-159">Navigeer naar de map waarin u het MSU-bestand hebt gedownload.</span><span class="sxs-lookup"><span data-stu-id="b0770-159">Navigate to the folder into which you downloaded the MSU file.</span></span>
2. <span data-ttu-id="b0770-160">Dubbelklik op de MSU uit te voeren.</span><span class="sxs-lookup"><span data-stu-id="b0770-160">Double-click the MSU to run it.</span></span>

<span data-ttu-id="b0770-161">**Installeren vanuit de opdrachtprompt**</span><span class="sxs-lookup"><span data-stu-id="b0770-161">**Installing from the Command Prompt**</span></span>

1. <span data-ttu-id="b0770-162">Na het downloaden van het juiste pakket voor de architectuur van de computer, open een opdrachtpromptvenster met verhoogde gebruikersrechten (als Administrator uitvoeren).</span><span class="sxs-lookup"><span data-stu-id="b0770-162">After downloading the correct package for your computer's architecture, open a Command Prompt window with elevated user rights (Run as Administrator).</span></span> <span data-ttu-id="b0770-163">Op de Server Core-installatieopties van Windows Server 2012 R2, Windows Server 2012 of Windows Server 2008 R2 SP1, opdrachtprompt standaard geopend met verhoogde gebruikersrechten.</span><span class="sxs-lookup"><span data-stu-id="b0770-163">On the Server Core installation options of Windows Server 2012 R2, Windows Server 2012, or Windows Server 2008 R2 SP1, Command Prompt opens with elevated user rights by default.</span></span>
2. <span data-ttu-id="b0770-164">Wijzig de mappen in de map waarin u hebt gedownload of gekopieerd van het installatiepakket van WMF 5.1.</span><span class="sxs-lookup"><span data-stu-id="b0770-164">Change directories to the folder into which you have downloaded or copied the WMF 5.1 installation package.</span></span>
3. <span data-ttu-id="b0770-165">Voer een van de volgende opdrachten:</span><span class="sxs-lookup"><span data-stu-id="b0770-165">Run one of the following commands:</span></span>
   - <span data-ttu-id="b0770-166">Voer op de computers waarop Windows Server 2012 R2 of Windows 8.1 x64, `Win8.1AndW2K12R2-KB3191564-x64.msu /quiet`.</span><span class="sxs-lookup"><span data-stu-id="b0770-166">On computers that are running Windows Server 2012 R2 or Windows 8.1 x64, run `Win8.1AndW2K12R2-KB3191564-x64.msu /quiet`.</span></span>
   - <span data-ttu-id="b0770-167">Voer op de computers waarop Windows Server 2012, `W2K12-KB3191565-x64.msu /quiet`.</span><span class="sxs-lookup"><span data-stu-id="b0770-167">On computers that are running Windows Server 2012, run `W2K12-KB3191565-x64.msu /quiet`.</span></span>
   - <span data-ttu-id="b0770-168">Voer op de computers waarop Windows 8.1 x86, `Win8.1-KB3191564-x86.msu /quiet`.</span><span class="sxs-lookup"><span data-stu-id="b0770-168">On computers that are running Windows 8.1 x86, run `Win8.1-KB3191564-x86.msu /quiet`.</span></span>

> [!NOTE]
> <span data-ttu-id="b0770-169">De installatie van WMF 5.1 moeten opnieuw worden opgestart.</span><span class="sxs-lookup"><span data-stu-id="b0770-169">Installing WMF 5.1 requires a reboot.</span></span> <span data-ttu-id="b0770-170">Met behulp van de `/quiet` optie wordt het systeem zonder waarschuwing opnieuw.</span><span class="sxs-lookup"><span data-stu-id="b0770-170">Using the `/quiet` option will reboot the system without warning.</span></span>
> <span data-ttu-id="b0770-171">Gebruik de `/norestart` optie om te voorkomen dat opnieuw wordt opgestart.</span><span class="sxs-lookup"><span data-stu-id="b0770-171">Use the `/norestart` option to avoid rebooting.</span></span> <span data-ttu-id="b0770-172">WMF 5.1 wordt echter niet worden geïnstalleerd totdat u opnieuw hebt opgestart.</span><span class="sxs-lookup"><span data-stu-id="b0770-172">However, WMF 5.1 will not be installed until you have rebooted.</span></span>
