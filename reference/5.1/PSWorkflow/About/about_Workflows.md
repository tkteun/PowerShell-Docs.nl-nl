---
description: Geeft een korte inleiding tot de Power shell-werk stroom functie.
keywords: powershell,cmdlet
Locale: en-US
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/psworkflow/about/about_workflows?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Workflows
ms.openlocfilehash: fbd8ee62b1e9c6969d489c5024c33f5cca883dc6
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/13/2020
ms.locfileid: "93252391"
---
# <a name="about-workflows"></a><span data-ttu-id="edbcd-104">Over werk stromen</span><span class="sxs-lookup"><span data-stu-id="edbcd-104">About Workflows</span></span>

## <a name="short-description"></a><span data-ttu-id="edbcd-105">Korte beschrijving</span><span class="sxs-lookup"><span data-stu-id="edbcd-105">Short description</span></span>

<span data-ttu-id="edbcd-106">Geeft een korte inleiding tot de Power shell-werk stroom functie.</span><span class="sxs-lookup"><span data-stu-id="edbcd-106">Provides a brief introduction to the PowerShell Workflow feature.</span></span>

## <a name="long-description"></a><span data-ttu-id="edbcd-107">Lange beschrijving</span><span class="sxs-lookup"><span data-stu-id="edbcd-107">Long description</span></span>

<span data-ttu-id="edbcd-108">Power shell workflow biedt de voor delen van de [Windows Workflow Foundation](/dotnet/framework/windows-workflow-foundation) naar Power shell en biedt u de mogelijkheid om werk stromen te schrijven en uit te voeren.</span><span class="sxs-lookup"><span data-stu-id="edbcd-108">PowerShell Workflow brings the benefits of the [Windows Workflow Foundation](/dotnet/framework/windows-workflow-foundation) to PowerShell and enables you to write and run workflows.</span></span>

<span data-ttu-id="edbcd-109">Power shell-werk stroom is geïntroduceerd in Power Shell 3,0 en de module is beschikbaar tot Power shell 5,1.</span><span class="sxs-lookup"><span data-stu-id="edbcd-109">PowerShell Workflow was introduced in PowerShell 3.0 and the module is available up to PowerShell 5.1.</span></span> <span data-ttu-id="edbcd-110">Voor meer informatie over de Power shell-werk stroom raadpleegt u de werk [stromen Guide](/previous-versions/powershell/scripting/components/workflows-guide) en [schrijft u een Windows Power shell-werk stroom](/previous-versions/powershell/scripting/developer/workflow/writing-a-windows-powershell-workflow).</span><span class="sxs-lookup"><span data-stu-id="edbcd-110">For more information about PowerShell Workflow, see the [Workflows Guide](/previous-versions/powershell/scripting/components/workflows-guide) and [Writing a Windows PowerShell Workflow](/previous-versions/powershell/scripting/developer/workflow/writing-a-windows-powershell-workflow).</span></span>

## <a name="about-workflows"></a><span data-ttu-id="edbcd-111">Over werk stromen</span><span class="sxs-lookup"><span data-stu-id="edbcd-111">About workflows</span></span>

<span data-ttu-id="edbcd-112">Werk stromen zijn opdrachten die bestaan uit een geordende reeks gerelateerde activiteiten.</span><span class="sxs-lookup"><span data-stu-id="edbcd-112">Workflows are commands that consist of an ordered sequence of related activities.</span></span> <span data-ttu-id="edbcd-113">Normaal gesp roken worden ze gedurende lange tijd uitgevoerd, waarbij gegevens worden verzameld uit en gewijzigd in honderden computers, vaak in heterogene omgevingen.</span><span class="sxs-lookup"><span data-stu-id="edbcd-113">Typically, they run for an extended period of time, gathering data from and making changes to hundreds of computers, often in heterogeneous environments.</span></span>

<span data-ttu-id="edbcd-114">Werk stromen kunnen worden geschreven in XAML, de taal die wordt gebruikt in Windows Workflow Foundation of in de Power shell-taal.</span><span class="sxs-lookup"><span data-stu-id="edbcd-114">Workflows can be written in XAML, the language used in Windows Workflow Foundation, or in the PowerShell language.</span></span> <span data-ttu-id="edbcd-115">Werk stromen worden meestal verpakt in modules en bevatten Help-onderwerpen.</span><span class="sxs-lookup"><span data-stu-id="edbcd-115">Workflows are typically packaged in modules and include help topics.</span></span> <span data-ttu-id="edbcd-116">Zie [XAML Overview (WPF)](/dotnet/framework/wpf/advanced/xaml-overview-wpf)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="edbcd-116">For more information, see [XAML Overview (WPF)](/dotnet/framework/wpf/advanced/xaml-overview-wpf).</span></span>

<span data-ttu-id="edbcd-117">Werk stromen zijn kritiek in een IT-omgeving, omdat ze niet meer opnieuw kunnen worden opgestart en automatisch moeten worden hersteld van veelvoorkomende fouten.</span><span class="sxs-lookup"><span data-stu-id="edbcd-117">Workflows are critical in an IT environment because they can survive reboots and recover automatically from common failures.</span></span> <span data-ttu-id="edbcd-118">U kunt de verbinding verbreken en opnieuw verbinden met sessies en computers waarop werk stromen worden uitgevoerd zonder de werk stroom verwerking te onderbreken, en werk stromen transparant te onderbreken en uit te scha kelen zonder gegevens verlies.</span><span class="sxs-lookup"><span data-stu-id="edbcd-118">You can disconnect and reconnect from sessions and computers running workflows without interrupting workflow processing, and suspend and resume workflows transparently without data loss.</span></span> <span data-ttu-id="edbcd-119">Elke activiteit in een werk stroom kan worden vastgelegd en gecontroleerd ter referentie.</span><span class="sxs-lookup"><span data-stu-id="edbcd-119">Each activity in a workflow can be logged and audited for reference.</span></span>
<span data-ttu-id="edbcd-120">Werk stromen kunnen worden uitgevoerd als taken en kunnen worden gepland met behulp van de functie voor geplande taken van Power shell.</span><span class="sxs-lookup"><span data-stu-id="edbcd-120">Workflows can run as jobs and can be scheduled by using the Scheduled Jobs feature of PowerShell.</span></span>

<span data-ttu-id="edbcd-121">De status en de gegevens in een werk stroom worden opgeslagen of bewaard aan het begin en het einde van de werk stroom en op de punten die u opgeeft.</span><span class="sxs-lookup"><span data-stu-id="edbcd-121">The state and data in a workflow is saved or persisted at the beginning and end of the workflow and at points that you specify.</span></span> <span data-ttu-id="edbcd-122">Persistentie punten van werk stromen werken zoals moment opnamen van data bases of Program ma's voor programma controle om de werk stroom te beschermen tegen de gevolgen van onderbrekingen en storingen.</span><span class="sxs-lookup"><span data-stu-id="edbcd-122">Workflow persistence points work like database snapshots or program checkpoints to protect the workflow from the effects of interruptions and failures.</span></span> <span data-ttu-id="edbcd-123">Als de werk stroom niet kan worden hersteld na een storing, kunt u de permanente gegevens gebruiken en hervatten vanaf het laatste persistentie punt, in plaats van een uitgebreide werk stroom vanaf het begin opnieuw uit te voeren.</span><span class="sxs-lookup"><span data-stu-id="edbcd-123">If the workflow is unable to recover from a failure, you can use the persisted data and resume from the last persistence point, instead of rerunning an extensive workflow from the beginning.</span></span>

## <a name="workflow-requirements-and-configuration"></a><span data-ttu-id="edbcd-124">Werk stroom vereisten en configuratie</span><span class="sxs-lookup"><span data-stu-id="edbcd-124">Workflow requirements and configuration</span></span>

<span data-ttu-id="edbcd-125">Een Power shell-werk stroom configuratie bestaat uit de volgende elementen:</span><span class="sxs-lookup"><span data-stu-id="edbcd-125">A PowerShell Workflow configuration consists of the following elements:</span></span>

- <span data-ttu-id="edbcd-126">Een client computer waarop de werk stroom wordt uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="edbcd-126">A client computer, which runs the workflow.</span></span>
- <span data-ttu-id="edbcd-127">Een werk stroom sessie, **PSSession** , op de client computer of op een externe computer.</span><span class="sxs-lookup"><span data-stu-id="edbcd-127">A workflow session, **PSSession** , on the client computer or on a remote computer.</span></span>
- <span data-ttu-id="edbcd-128">Beheerde knoop punten, de doel computers die worden beïnvloed door de werk stroom activiteiten.</span><span class="sxs-lookup"><span data-stu-id="edbcd-128">Managed nodes, the target computers that are affected by the workflow activities.</span></span>

<span data-ttu-id="edbcd-129">De werk stroom sessie is niet vereist, maar wordt aanbevolen.</span><span class="sxs-lookup"><span data-stu-id="edbcd-129">The workflow session isn't required, but is recommended.</span></span> <span data-ttu-id="edbcd-130">**PSSessions** kan profiteren van de functies van de robuuste herstel-en verbroken sessies van Power shell om niet-verbonden werk stroom sessies te herstellen.</span><span class="sxs-lookup"><span data-stu-id="edbcd-130">**PSSessions** can take advantage of the robust recovery and Disconnected Sessions features of PowerShell to recover disconnected workflow sessions.</span></span> <span data-ttu-id="edbcd-131">Zie [about_Remote_Disconnected_Sessions](../../Microsoft.PowerShell.Core/About/about_Remote_Disconnected_Sessions.md) voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="edbcd-131">For more information, see [about_Remote_Disconnected_Sessions](../../Microsoft.PowerShell.Core/About/about_Remote_Disconnected_Sessions.md)</span></span>

<span data-ttu-id="edbcd-132">Omdat de client computer en de computer waarop de werk stroom sessie wordt uitgevoerd, beheerde knoop punten kunnen zijn, kunt u een werk stroom uitvoeren op één computer die voldoet aan alle rollen.</span><span class="sxs-lookup"><span data-stu-id="edbcd-132">Because the client computer and the computer on which the workflow session runs can be managed nodes, you can run a workflow on a single computer that fulfills all roles.</span></span>

<span data-ttu-id="edbcd-133">Op de client computer en de computer waarop de werk stroom sessie wordt uitgevoerd, moet Power Shell 3,0 worden uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="edbcd-133">The client computer and the computer on which the workflow session runs must be running PowerShell 3.0.</span></span> <span data-ttu-id="edbcd-134">Alle in aanmerking komende systemen worden ondersteund, met inbegrip van de Server Core-installatie opties van Windows Server-besturings systemen.</span><span class="sxs-lookup"><span data-stu-id="edbcd-134">All eligible systems are supported, including the Server Core installation options of Windows Server operating systems.</span></span>

<span data-ttu-id="edbcd-135">Voor het uitvoeren van werk stromen die cmdlets bevatten, moeten de beheerde knoop punten beschikken over Windows Power Shell 2,0 of hoger.</span><span class="sxs-lookup"><span data-stu-id="edbcd-135">To run workflows that include cmdlets, the managed nodes must have Windows PowerShell 2.0 or later.</span></span> <span data-ttu-id="edbcd-136">Voor beheerde knoop punten is Power shell niet vereist, tenzij de werk stroom cmdlets bevat.</span><span class="sxs-lookup"><span data-stu-id="edbcd-136">Managed nodes don't require PowerShell unless the workflow includes cmdlets.</span></span> <span data-ttu-id="edbcd-137">U kunt werk stromen uitvoeren met Windows Management Instrumentation (WMI) en Common Information Model (CIM)-opdrachten op computers die geen Power shell bevatten.</span><span class="sxs-lookup"><span data-stu-id="edbcd-137">You can run workflows that include Windows Management Instrumentation (WMI) and Common Information Model (CIM) commands on computers that don't have PowerShell.</span></span>

## <a name="how-to-get-workflows"></a><span data-ttu-id="edbcd-138">Werk stromen ophalen</span><span class="sxs-lookup"><span data-stu-id="edbcd-138">How to get workflows</span></span>

<span data-ttu-id="edbcd-139">Werk stromen worden meestal verpakt in modules.</span><span class="sxs-lookup"><span data-stu-id="edbcd-139">Workflows are typically packaged in modules.</span></span> <span data-ttu-id="edbcd-140">Als u de module wilt importeren die een werk stroom bevat, gebruikt u een wille keurige opdracht in de module of gebruikt u de `Import-Module` cmdlet.</span><span class="sxs-lookup"><span data-stu-id="edbcd-140">To import the module that includes a workflow, use any command in the module or use the `Import-Module` cmdlet.</span></span>
<span data-ttu-id="edbcd-141">Modules worden automatisch geïmporteerd bij het eerste gebruik van een opdracht in de module.</span><span class="sxs-lookup"><span data-stu-id="edbcd-141">Modules are imported automatically on first use of any command in the module.</span></span>

<span data-ttu-id="edbcd-142">Gebruik de `Get-Command` **CommandType** -para meter van de cmdlet om de werk stromen te vinden in modules die op uw computer zijn geïnstalleerd.</span><span class="sxs-lookup"><span data-stu-id="edbcd-142">To find the workflows in modules installed on your computer, use the `Get-Command` cmdlet's **CommandType** parameter.</span></span>

```powershell
Get-Command -CommandType Workflow
```

## <a name="how-to-run-workflows"></a><span data-ttu-id="edbcd-143">Werk stromen uitvoeren</span><span class="sxs-lookup"><span data-stu-id="edbcd-143">How to run workflows</span></span>

<span data-ttu-id="edbcd-144">Gebruik de volgende procedure om een werk stroom uit te voeren.</span><span class="sxs-lookup"><span data-stu-id="edbcd-144">To run a workflow, use the following procedure.</span></span>

1. <span data-ttu-id="edbcd-145">Wanneer het beheerde knoop punt de lokale computer is, is deze stap niet vereist.</span><span class="sxs-lookup"><span data-stu-id="edbcd-145">When the managed node is the local computer, this step isn't required.</span></span>
   <span data-ttu-id="edbcd-146">Als dat niet het geval is, start u Power shell op de client computer met de optie **als administrator uitvoeren** .</span><span class="sxs-lookup"><span data-stu-id="edbcd-146">Otherwise, on the client computer, start PowerShell with the **Run as administrator** option.</span></span>

   ```powershell
   Start-Process PowerShell -Verb RunAs
   ```

1. <span data-ttu-id="edbcd-147">Schakel externe communicatie van Power shell in op de computer waarop de werk stroom sessie wordt uitgevoerd en op beheerde knoop punten die worden beïnvloed door werk stromen die cmdlets bevatten.</span><span class="sxs-lookup"><span data-stu-id="edbcd-147">Enable PowerShell remoting on the computer that runs the workflow session and on managed nodes affected by workflows that include cmdlets.</span></span>

   <span data-ttu-id="edbcd-148">U hoeft deze stap maar één keer op elke deelnemende computer uit te voeren.</span><span class="sxs-lookup"><span data-stu-id="edbcd-148">You only need to do this step once on each participating computer.</span></span>

   <span data-ttu-id="edbcd-149">Deze stap is alleen vereist bij het uitvoeren van werk stromen die cmdlets bevatten.</span><span class="sxs-lookup"><span data-stu-id="edbcd-149">This step is required only when running workflows that include cmdlets.</span></span> <span data-ttu-id="edbcd-150">U hoeft externe toegang niet in te scha kelen op de client computer, tenzij de werk stroom sessie wordt uitgevoerd op de client computer of op alle beheerde knoop punten waarop Power Shell 3,0 wordt uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="edbcd-150">You don't need to enable remoting on the client computer, unless the workflows session runs on the client computer, or on any managed nodes that are running PowerShell 3.0.</span></span>

   <span data-ttu-id="edbcd-151">Als u externe toegang wilt inschakelen, gebruikt u de `Enable-PSRemoting` cmdlet.</span><span class="sxs-lookup"><span data-stu-id="edbcd-151">To enable remoting, use the `Enable-PSRemoting` cmdlet.</span></span>

   ```powershell
   Enable-PSRemoting -Force
   ```

   <span data-ttu-id="edbcd-152">U kunt externe toegang inschakelen met de instelling **script uitvoering inschakelen** Groepsbeleid.</span><span class="sxs-lookup"><span data-stu-id="edbcd-152">You can enable remoting by using the **Turn on Script Execution** Group Policy setting.</span></span> <span data-ttu-id="edbcd-153">Zie [about_Group_Policy_Settings](../../Microsoft.PowerShell.Core/About/about_Group_Policy_Settings.md) en [about_Execution_Policies](../../Microsoft.PowerShell.Core/About/about_Execution_Policies.md)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="edbcd-153">For more information, see [about_Group_Policy_Settings](../../Microsoft.PowerShell.Core/About/about_Group_Policy_Settings.md) and [about_Execution_Policies](../../Microsoft.PowerShell.Core/About/about_Execution_Policies.md).</span></span>

1. <span data-ttu-id="edbcd-154">Gebruik de `New-PSWorkflowSession` `New-PSSession` cmdlets of om de werk stroom sessie te maken.</span><span class="sxs-lookup"><span data-stu-id="edbcd-154">Use the `New-PSWorkflowSession` or `New-PSSession` cmdlets to create the workflow session.</span></span>

   <span data-ttu-id="edbcd-155">De `New-PSWorkflowSession` cmdlet start een sessie die gebruikmaakt van de ingebouwde **micro soft. Power shell. werk stroom** sessie configuratie op de doel computer.</span><span class="sxs-lookup"><span data-stu-id="edbcd-155">The `New-PSWorkflowSession` cmdlet starts a session that uses the built-in **Microsoft.PowerShell.Workflow** session configuration on the destination computer.</span></span> <span data-ttu-id="edbcd-156">Deze sessie configuratie bevat scripts, bestands typen en Format teren, en opties die zijn ontworpen voor werk stromen.</span><span class="sxs-lookup"><span data-stu-id="edbcd-156">This session configuration includes scripts, type and formatting files, and options that are designed for workflows.</span></span>

   <span data-ttu-id="edbcd-157">U kunt ook de `New-PSSession` cmdlet gebruiken.</span><span class="sxs-lookup"><span data-stu-id="edbcd-157">Or, use the `New-PSSession` cmdlet.</span></span> <span data-ttu-id="edbcd-158">Gebruik de para meter **configuratiepad** om de configuratie van **micro soft. Power shell. werk stroom** sessie op te geven.</span><span class="sxs-lookup"><span data-stu-id="edbcd-158">Use the **ConfigurationName** parameter to specify the **Microsoft.PowerShell.Workflow** session configuration.</span></span> <span data-ttu-id="edbcd-159">Deze opdracht is hetzelfde als het gebruik van de `New-PSWorkflowSession` cmdlet.</span><span class="sxs-lookup"><span data-stu-id="edbcd-159">This command is the same as using the `New-PSWorkflowSession` cmdlet.</span></span>

   <span data-ttu-id="edbcd-160">U kunt ook de cmdlet gebruiken `New-PSSession` .</span><span class="sxs-lookup"><span data-stu-id="edbcd-160">An alternative is to use the `New-PSSession` cmdlet.</span></span> <span data-ttu-id="edbcd-161">Gebruik de para meter **configuratiepad** om de configuratie van **micro soft. Power shell. werk stroom** sessie op te geven.</span><span class="sxs-lookup"><span data-stu-id="edbcd-161">Use the **ConfigurationName** parameter to specify the **Microsoft.PowerShell.Workflow** session configuration.</span></span>

   <span data-ttu-id="edbcd-162">Op de lokale computer:</span><span class="sxs-lookup"><span data-stu-id="edbcd-162">On the local computer:</span></span>

   ```powershell
   $ws = New-PSWorkflowSession
   ```

   <span data-ttu-id="edbcd-163">Op een externe computer:</span><span class="sxs-lookup"><span data-stu-id="edbcd-163">On a remote computer:</span></span>

   ```powershell
   $ws = New-PSWorkflowSession -ComputerName Server01 `
   -Credential Domain01\Admin01
   ```

   <span data-ttu-id="edbcd-164">Als u een beheerder bent van de werk stroom sessie computer, kunt u de `New-PSWorkflowExecutionOption` cmdlet gebruiken om aangepaste optie-instellingen te maken voor de werk stroom sessie configuratie.</span><span class="sxs-lookup"><span data-stu-id="edbcd-164">If you are an Administrator on the workflow session computer, you can use the `New-PSWorkflowExecutionOption` cmdlet to create custom option settings for the workflow session configuration.</span></span> <span data-ttu-id="edbcd-165">En gebruik de `Set-PSSessionConfiguration` cmdlet om de sessie configuratie te wijzigen.</span><span class="sxs-lookup"><span data-stu-id="edbcd-165">And, use the `Set-PSSessionConfiguration` cmdlet to change the session configuration.</span></span>

   ```powershell
   $sto = New-PSWorkflowExecutionOption -MaxConnectedSessions 150
   Invoke-Command -ComputerName Server01 `
   {Set-PSSessionConfiguration Microsoft.PowerShell.Workflow `
   -SessionTypeOption $Using:sto}
   $ws = New-PSWorkflowSession -ComputerName Server01 `
   -Credential Domain01\Admin01
   ```

1. <span data-ttu-id="edbcd-166">Voer de werk stroom uit in de werk stroom sessie.</span><span class="sxs-lookup"><span data-stu-id="edbcd-166">Run the workflow in the workflow session.</span></span> <span data-ttu-id="edbcd-167">Als u de namen van de beheerde knoop punten, doel computers wilt opgeven, gebruikt u de algemene para meter **PSComputerName** workflow.</span><span class="sxs-lookup"><span data-stu-id="edbcd-167">To specify the names of the managed nodes, target computers, use the **PSComputerName** workflow common parameter.</span></span>

   <span data-ttu-id="edbcd-168">In de volgende voor beelden wordt de werk stroom met de naam **test-werk stroom** uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="edbcd-168">The following examples run the workflow named **Test-Workflow**.</span></span>

   <span data-ttu-id="edbcd-169">Waarbij het beheerde knoop punt de computer is die als host fungeert voor de werk stroom sessie:</span><span class="sxs-lookup"><span data-stu-id="edbcd-169">Where the managed node is the computer that hosts the workflow session:</span></span>

   ```powershell
   Invoke-Command -Session $ws {Test-Workflow}
   ```

   <span data-ttu-id="edbcd-170">Waar de beheerde knoop punten externe computers zijn.</span><span class="sxs-lookup"><span data-stu-id="edbcd-170">Where the managed nodes are remote computers.</span></span>

   ```powershell
   Invoke-Command -Session $ws{
   Test-Workflow -PSComputerName Server01, Server02 }
   ```

   <span data-ttu-id="edbcd-171">In het volgende voor beeld wordt de **test werk stroom** op honderden computers uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="edbcd-171">The following example runs the **Test-Workflow** on hundreds of computers.</span></span> <span data-ttu-id="edbcd-172">De `Get-Content` cmdlet haalt de computer namen op uit een tekst bestand en slaat ze op in de `$Servers` variabele op de lokale computer.</span><span class="sxs-lookup"><span data-stu-id="edbcd-172">The `Get-Content` cmdlet gets the computer names from a text file and saves them in the `$Servers` variable on the local computer.</span></span>

   <span data-ttu-id="edbcd-173">`Invoke-Command` gebruikt de `$Using` aanpassings functie van het bereik om de `$Servers` variabele in de lokale sessie te definiëren.</span><span class="sxs-lookup"><span data-stu-id="edbcd-173">`Invoke-Command` uses the `$Using` scope modifier to define the `$Servers` variable in the local session.</span></span> <span data-ttu-id="edbcd-174">Zie about_Remote_Variables voor meer informatie over de `$Using` aanpassing van het [about_Remote_Variables](../../Microsoft.PowerShell.Core/About/about_Remote_Variables.md)bereik.</span><span class="sxs-lookup"><span data-stu-id="edbcd-174">For more information about the `$Using` scope modifier, see [about_Remote_Variables](../../Microsoft.PowerShell.Core/About/about_Remote_Variables.md).</span></span>

   ```powershell
   $Servers = Get-Content Servers.txt
   Invoke-Command -Session $ws {Test-Workflow -PSComputerName $Using:Servers }
   ```

## <a name="using-workflow-common-parameters"></a><span data-ttu-id="edbcd-175">Algemene werk stroom parameters gebruiken</span><span class="sxs-lookup"><span data-stu-id="edbcd-175">Using workflow common parameters</span></span>

<span data-ttu-id="edbcd-176">De algemene werk stroom parameters zijn een set para meters die door Power shell automatisch aan alle werk stromen worden toegevoegd.</span><span class="sxs-lookup"><span data-stu-id="edbcd-176">The workflow common parameters are a set of parameters that PowerShell adds automatically to all workflows.</span></span> <span data-ttu-id="edbcd-177">Power shell voegt de algemene cmdlet-para meters toe aan alle werk stromen, zelfs als de werk stroom geen gebruik maakt van het kenmerk **CmdletBinding** .</span><span class="sxs-lookup"><span data-stu-id="edbcd-177">PowerShell adds the cmdlet common parameters to all workflows, even if the workflow doesn't use the **CmdletBinding** attribute.</span></span>

<span data-ttu-id="edbcd-178">Met de volgende werk stroom worden bijvoorbeeld geen para meters gedefinieerd.</span><span class="sxs-lookup"><span data-stu-id="edbcd-178">For example, the following workflow defines no parameters.</span></span> <span data-ttu-id="edbcd-179">Wanneer u de werk stroom uitvoert, heeft deze echter zowel de **CommonParameters** als de **WorkflowCommonParameters**.</span><span class="sxs-lookup"><span data-stu-id="edbcd-179">However, when you run the workflow, it has both the **CommonParameters** and **WorkflowCommonParameters**.</span></span>

```powershell
workflow Test-Workflow {Get-Process}
Get-Command Test-Workflow -Syntax
```

```powershell
Test-Workflow [<WorkflowCommonParameters>] [<CommonParameters>]
```

<span data-ttu-id="edbcd-180">De algemene werk stroom parameters bevatten verschillende para meters die essentieel zijn voor het uitvoeren van werk stromen.</span><span class="sxs-lookup"><span data-stu-id="edbcd-180">The workflow common parameters include several parameters that are essential to running workflows.</span></span> <span data-ttu-id="edbcd-181">De gemeen schappelijke para meter **PSComputerName** geeft bijvoorbeeld de beheerde knoop punten waarop de werk stroom invloed heeft.</span><span class="sxs-lookup"><span data-stu-id="edbcd-181">For example, the **PSComputerName** common parameter specifies the managed nodes that the workflow affects.</span></span>

```powershell
Invoke-Command -Session $ws {
  Test-Workflow -PSComputerName Server01, Server02
}
```

<span data-ttu-id="edbcd-182">De algemene para meter **PSPersist** workflow bepaalt wanneer werk stroom gegevens worden bewaard.</span><span class="sxs-lookup"><span data-stu-id="edbcd-182">The **PSPersist** workflow common parameter determines when workflow data is persisted.</span></span> <span data-ttu-id="edbcd-183">U kunt hiermee het persistentie punt tussen activiteiten toevoegen aan werk stromen die geen persistentie punten definiëren.</span><span class="sxs-lookup"><span data-stu-id="edbcd-183">It enables you to add persistence point between activities to workflows that don't define persistence points.</span></span>

```powershell
Invoke-Command -Session $ws {
  Test-Workflow -PSComputerName Server01, Server02 -PSPersist:$True
}
```

<span data-ttu-id="edbcd-184">Met andere algemene werk stroom parameters kunt u de kenmerken van de externe verbinding met de beheerde knoop punten opgeven.</span><span class="sxs-lookup"><span data-stu-id="edbcd-184">Other workflow common parameters let you specify the characteristics of the remote connection to the managed nodes.</span></span> <span data-ttu-id="edbcd-185">Hun namen en functionaliteit zijn vergelijkbaar met de para meters van externe cmdlets, waaronder `Invoke-Command` .</span><span class="sxs-lookup"><span data-stu-id="edbcd-185">Their names and functionality are similar to the parameters of remoting cmdlets, including `Invoke-Command`.</span></span>

```powershell
Invoke-Command -Session $ws {
  Test-Workflow -PSComputerName Server01, Server02 -PSPort 443
}
```

<span data-ttu-id="edbcd-186">Zorg ervoor dat u de externe para meters die de verbinding voor de werk stroom sessie definieert **,** onderscheidt van de algemene para meters voor de vaste workflow die de verbinding met de beheerde knoop punten definiëren.</span><span class="sxs-lookup"><span data-stu-id="edbcd-186">Take care to distinguish the remoting parameters that define the connection for the workflow session from the **PS-prefixed** workflow common parameters that define the connection to the managed nodes.</span></span>

```powershell
$ws = New-PSSession -ComputerName Server01 -ConfigurationName Microsoft.PowerShell.Workflow

Invoke-Command -Session $ws {
  Test-Workflow -PSComputerName Server01, Server02 -PSConfigurationName Microsoft.PowerShell.Workflow
}
```

<span data-ttu-id="edbcd-187">Sommige algemene werk stroom parameters zijn uniek voor werk stromen, zoals de **PSParameterCollection** -para meter waarmee u verschillende algemene parameter waarden van werk stromen kunt opgeven voor verschillende externe knoop punten.</span><span class="sxs-lookup"><span data-stu-id="edbcd-187">Some workflow common parameters are unique to workflows, such as the **PSParameterCollection** parameter that lets you specify different workflow common parameter values for different remote nodes.</span></span> <span data-ttu-id="edbcd-188">Zie [about_WorkflowCommonParameters](about_WorkflowCommonParameters.md)voor een lijst en een beschrijving van de algemene werk stroom parameters.</span><span class="sxs-lookup"><span data-stu-id="edbcd-188">For a list and description of the workflow common parameters, see [about_WorkflowCommonParameters](about_WorkflowCommonParameters.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="edbcd-189">Zie ook</span><span class="sxs-lookup"><span data-stu-id="edbcd-189">See also</span></span>

[<span data-ttu-id="edbcd-190">Invoke-AsWorkflow</span><span class="sxs-lookup"><span data-stu-id="edbcd-190">Invoke-AsWorkflow</span></span>](xref:PSWorkflowUtility.Invoke-AsWorkflow)

[<span data-ttu-id="edbcd-191">New-PSSession</span><span class="sxs-lookup"><span data-stu-id="edbcd-191">New-PSSession</span></span>](xref:Microsoft.PowerShell.Core.New-PSSession)

<span data-ttu-id="edbcd-192">[PSWorkflow](xref:PSWorkflow) -cmdlets</span><span class="sxs-lookup"><span data-stu-id="edbcd-192">[PSWorkflow](xref:PSWorkflow) cmdlets</span></span>

[<span data-ttu-id="edbcd-193">Handleiding voor werkstromen</span><span class="sxs-lookup"><span data-stu-id="edbcd-193">Workflows Guide</span></span>](/previous-versions/powershell/scripting/components/workflows-guide)

[<span data-ttu-id="edbcd-194">Een Windows PowerShell-werkstroom schrijven</span><span class="sxs-lookup"><span data-stu-id="edbcd-194">Writing a Windows PowerShell Workflow</span></span>](/previous-versions/powershell/scripting/developer/workflow/writing-a-windows-powershell-workflow)
