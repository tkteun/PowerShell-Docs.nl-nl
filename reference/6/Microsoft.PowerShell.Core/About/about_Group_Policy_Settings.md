---
description: Beschrijft de groepsbeleid-instellingen voor Power shell
keywords: powershell,cmdlet
Locale: en-US
ms.date: 11/28/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_group_policy_settings?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Group_Policy_Settings
ms.openlocfilehash: 1533908be91703efd8509653b30d30de6b7c4a84
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/13/2020
ms.locfileid: "93252323"
---
# <a name="about-group-policy-settings"></a><span data-ttu-id="43f85-104">Over groepsbeleid-instellingen</span><span class="sxs-lookup"><span data-stu-id="43f85-104">About Group Policy Settings</span></span>

## <a name="short-description"></a><span data-ttu-id="43f85-105">Korte beschrijving</span><span class="sxs-lookup"><span data-stu-id="43f85-105">Short description</span></span>
<span data-ttu-id="43f85-106">Beschrijft de groepsbeleid-instellingen voor Power shell</span><span class="sxs-lookup"><span data-stu-id="43f85-106">Describes the Group Policy settings for PowerShell</span></span>

## <a name="long-description"></a><span data-ttu-id="43f85-107">Lange beschrijving</span><span class="sxs-lookup"><span data-stu-id="43f85-107">Long description</span></span>

<span data-ttu-id="43f85-108">Power shell bevat groepsbeleid instellingen die u helpen bij het definiëren van consistente configuratie waarden voor Windows-computers in een bedrijfs omgeving.</span><span class="sxs-lookup"><span data-stu-id="43f85-108">PowerShell includes Group Policy settings to help you define consistent configuration values for Windows computers in an enterprise environment.</span></span>

<span data-ttu-id="43f85-109">De Power shell-groepsbeleid-instellingen bevinden zich in de volgende groepsbeleid paden:</span><span class="sxs-lookup"><span data-stu-id="43f85-109">The PowerShell Group Policy settings are in the following Group Policy paths:</span></span>

```
Computer Configuration\
  Administrative Templates\
    Windows Components\
      Windows PowerShell

User Configuration\
  Administrative Templates\
    Windows Components\
      Windows PowerShell
```

<span data-ttu-id="43f85-110">Instellingen voor groeps beleid in het pad gebruikers configuratie hebben voor rang op groepsbeleid instellingen in het pad computer configuratie.</span><span class="sxs-lookup"><span data-stu-id="43f85-110">Group policy settings in the User Configuration path take precedence over Group Policy settings in the Computer Configuration path.</span></span>

<span data-ttu-id="43f85-111">Nadat u de sjablonen hebt geïnstalleerd, kunt u deze instellingen bewerken in de groepsbeleid editor ( `gpedit.msc` ).</span><span class="sxs-lookup"><span data-stu-id="43f85-111">After installing the templates, you can edit these settings in the Group Policy editor (`gpedit.msc`).</span></span>

<span data-ttu-id="43f85-112">De beleids regels zijn als volgt:</span><span class="sxs-lookup"><span data-stu-id="43f85-112">The policies are as follows:</span></span>

- <span data-ttu-id="43f85-113">Module logboek registratie inschakelen: Hiermee wordt de eigenschap **LogPipelineExecutionDetails** van modules ingesteld.</span><span class="sxs-lookup"><span data-stu-id="43f85-113">Turn on Module Logging: Sets the **LogPipelineExecutionDetails** property of modules.</span></span>
- <span data-ttu-id="43f85-114">Power shell-script blok logboek registratie inschakelen: Hiermee wordt gedetailleerde logboek registratie van alle Power shell-scripts ingeschakeld.</span><span class="sxs-lookup"><span data-stu-id="43f85-114">Turn on PowerShell Script Block Logging: Enables detailed logging of all PowerShell scripts.</span></span>
- <span data-ttu-id="43f85-115">Script uitvoering inschakelen: Hiermee stelt u het Power shell-uitvoerings beleid in.</span><span class="sxs-lookup"><span data-stu-id="43f85-115">Turn on Script Execution: Sets the PowerShell execution policy.</span></span>
- <span data-ttu-id="43f85-116">Power shell transcriptie inschakelen: Hiermee wordt de invoer en uitvoer van Power shell-opdrachten vastgelegd in Transcripten op basis van tekst.</span><span class="sxs-lookup"><span data-stu-id="43f85-116">Turn on PowerShell Transcription: enables capturing of input and output of PowerShell commands into text-based transcripts.</span></span>
- <span data-ttu-id="43f85-117">Het standaardpad voor de bron instellen `Update-Help` : Hiermee stelt u de bron in op Help-informatie voor een directory, niet via internet.</span><span class="sxs-lookup"><span data-stu-id="43f85-117">Set the default source path for `Update-Help`: Sets the source for Updatable Help to a directory, not the Internet.</span></span>

<span data-ttu-id="43f85-118">Voor meer informatie over het verkrijgen van andere sjablonen en het configureren van groeps beleid raadpleegt [u het centraal archief maken en beheren voor groepsbeleid Beheersjablonen in Windows][gpstore].</span><span class="sxs-lookup"><span data-stu-id="43f85-118">For more information about acquiring other templates and configuring Group policy, see [How to create and manage the Central Store for Group Policy Administrative Templates in Windows][gpstore].</span></span>

## <a name="turn-on-module-logging"></a><span data-ttu-id="43f85-119">Module logboek registratie inschakelen</span><span class="sxs-lookup"><span data-stu-id="43f85-119">Turn on module logging</span></span>

<span data-ttu-id="43f85-120">Met de beleids instelling **module logboek registratie inschakelen** wordt logboek registratie ingeschakeld voor geselecteerde Power shell-modules.</span><span class="sxs-lookup"><span data-stu-id="43f85-120">The **Turn on Module Logging** policy setting turns on logging for selected PowerShell modules.</span></span> <span data-ttu-id="43f85-121">De instelling is effectief in alle sessies op alle betrokken computers.</span><span class="sxs-lookup"><span data-stu-id="43f85-121">The setting is effective in all sessions on all affected computers.</span></span>

<span data-ttu-id="43f85-122">Als u deze beleids instelling inschakelt en een of meer modules opgeeft, worden de pijplijn uitvoerings gebeurtenissen voor de opgegeven modules vastgelegd in het Windows Power shell-aanmeld Logboeken.</span><span class="sxs-lookup"><span data-stu-id="43f85-122">If you enable this policy setting and specify one or more modules, pipeline execution events for the specified modules are recorded in the Windows PowerShell log in Event Viewer.</span></span>

<span data-ttu-id="43f85-123">Als u deze beleids instelling uitschakelt, wordt het vastleggen van uitvoerings gebeurtenissen uitgeschakeld voor alle Power shell-modules.</span><span class="sxs-lookup"><span data-stu-id="43f85-123">If you disable this policy setting, logging of execution events is disabled for all PowerShell modules.</span></span>

<span data-ttu-id="43f85-124">Als deze beleids instelling niet is geconfigureerd, bepaalt de eigenschap **LogPipelineExecutionDetails** van elke module of de uitvoerings gebeurtenissen van een module worden vastgelegd.</span><span class="sxs-lookup"><span data-stu-id="43f85-124">If this policy setting is not configured, the **LogPipelineExecutionDetails** property of each module determines whether the execution events of a module are logged.</span></span> <span data-ttu-id="43f85-125">De eigenschap **LogPipelineExecutionDetails** van alle modules is standaard ingesteld op ONWAAR.</span><span class="sxs-lookup"><span data-stu-id="43f85-125">By default, the **LogPipelineExecutionDetails** property of all modules is set to False.</span></span>

<span data-ttu-id="43f85-126">Als u module logboek registratie wilt inschakelen voor een module, gebruikt u de volgende opdracht indeling.</span><span class="sxs-lookup"><span data-stu-id="43f85-126">To turn on module logging for a module, use the following command format.</span></span> <span data-ttu-id="43f85-127">De module moet in de sessie worden geïmporteerd en de instelling is alleen effectief in de huidige sessie.</span><span class="sxs-lookup"><span data-stu-id="43f85-127">The module must be imported into the session and the setting is effective only in the current session.</span></span>

```powershell
Import-Module <Module-Name>
(Get-Module <Module-Name>).LogPipelineExecutionDetails = $true
```

<span data-ttu-id="43f85-128">Als u module logboek registratie wilt inschakelen voor alle sessies op een bepaalde computer, voegt u de vorige opdrachten toe aan het Power shell-profiel ' alle gebruikers ' ( `$Profile.AllUsersAllHosts` ).</span><span class="sxs-lookup"><span data-stu-id="43f85-128">To turn on module logging for all sessions on a particular computer, add the previous commands to the 'All Users' PowerShell profile (`$Profile.AllUsersAllHosts`).</span></span>

<span data-ttu-id="43f85-129">Zie [about_Modules](about_Modules.md)voor meer informatie over het vastleggen van module-Logboeken.</span><span class="sxs-lookup"><span data-stu-id="43f85-129">For more information about module logging, see [about_Modules](about_Modules.md).</span></span>

## <a name="turn-on-powershell-script-block-logging"></a><span data-ttu-id="43f85-130">Logboek registratie van Power shell-script blokken inschakelen</span><span class="sxs-lookup"><span data-stu-id="43f85-130">Turn on PowerShell script block logging</span></span>

<span data-ttu-id="43f85-131">Met de beleids instelling **logboek registratie van Power shell-script blok inschakelen** wordt logboek registratie van alle Power shell-script invoer naar het gebeurtenis logboek van micro soft-Windows-Power shell/operationeel ingeschakeld.</span><span class="sxs-lookup"><span data-stu-id="43f85-131">The **Turn on PowerShell Script Block Logging** policy setting enables logging of all PowerShell script input to the Microsoft-Windows-PowerShell/Operational event log.</span></span> <span data-ttu-id="43f85-132">Als u deze beleids instelling inschakelt, wordt de verwerking van opdrachten, script blokken, functies en scripts door Power shell core geregistreerd, ongeacht of deze interactief of via Automation is aangeroepen.</span><span class="sxs-lookup"><span data-stu-id="43f85-132">If you enable this policy setting, PowerShell Core will log the processing of commands, script blocks, functions, and scripts - whether invoked interactively, or through automation.</span></span>

<span data-ttu-id="43f85-133">Als u deze beleidsinstelling uitschakelt, wordt logboekregistratie van PowerShell-scriptinvoer uitgeschakeld.</span><span class="sxs-lookup"><span data-stu-id="43f85-133">If you disable this policy setting, logging of PowerShell script input is disabled.</span></span> <span data-ttu-id="43f85-134">Als u de logboekregistratie voor het aanroepen van script blokkeren inschakelt, worden gebeurtenissen door PowerShell vastgelegd bij het aanroepen van een opdracht, scriptblokkering, functie of bij het starten of stoppen van een script.</span><span class="sxs-lookup"><span data-stu-id="43f85-134">If you enable the Script Block Invocation Logging, PowerShell additionally logs events when invocation of a command, script block, function, or script starts or stops.</span></span> <span data-ttu-id="43f85-135">Als het aanroeplogbestand wordt ingeschakeld, wordt er een groot aantal gebeurtenislogboeken gegenereerd.</span><span class="sxs-lookup"><span data-stu-id="43f85-135">Enabling Invocation Logging generates a high volume of event logs.</span></span>

## <a name="turn-on-script-execution"></a><span data-ttu-id="43f85-136">Script uitvoering inschakelen</span><span class="sxs-lookup"><span data-stu-id="43f85-136">Turn on script execution</span></span>

<span data-ttu-id="43f85-137">Met de instelling **Script Execution** Policy wordt het uitvoerings beleid voor computers en gebruikers ingesteld, waarmee wordt bepaald welke scripts mogen worden uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="43f85-137">The **Turn on Script Execution** policy setting sets the execution policy for computers and users, which determines which scripts are permitted to run.</span></span>

<span data-ttu-id="43f85-138">Als u de beleids instelling inschakelt, kunt u een van de volgende beleids instellingen selecteren.</span><span class="sxs-lookup"><span data-stu-id="43f85-138">If you enable the policy setting, you can select from among the following policy settings.</span></span>

- <span data-ttu-id="43f85-139">**Alleen ondertekende scripts toestaan** dat scripts alleen kunnen worden uitgevoerd als ze door een vertrouwde uitgever zijn ondertekend.</span><span class="sxs-lookup"><span data-stu-id="43f85-139">**Allow only signed scripts** allows scripts to execute only if they are signed by a trusted publisher.</span></span> <span data-ttu-id="43f85-140">Deze beleids instelling is gelijk aan het alles ondertekend-uitvoerings beleid.</span><span class="sxs-lookup"><span data-stu-id="43f85-140">This policy setting is equivalent to the AllSigned execution policy.</span></span>

- <span data-ttu-id="43f85-141">Met **lokale scripts en externe ondertekende scripts** kunnen alle lokale scripts worden uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="43f85-141">**Allow local scripts and remote signed scripts** allows all local scripts to run.</span></span> <span data-ttu-id="43f85-142">Scripts die afkomstig zijn van Internet, moeten zijn ondertekend door een vertrouwde uitgever.</span><span class="sxs-lookup"><span data-stu-id="43f85-142">Scripts that originate from the Internet must be signed by a trusted publisher.</span></span> <span data-ttu-id="43f85-143">Deze beleids instelling is gelijk aan het RemoteSigned-uitvoerings beleid.</span><span class="sxs-lookup"><span data-stu-id="43f85-143">This policy setting is equivalent to the RemoteSigned execution policy.</span></span>

- <span data-ttu-id="43f85-144">**Alle scripts toestaan** dat alle scripts kunnen worden uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="43f85-144">**Allow all scripts** allows all scripts to run.</span></span> <span data-ttu-id="43f85-145">Deze beleids instelling is gelijk aan het beleid voor onbeperkte uitvoering.</span><span class="sxs-lookup"><span data-stu-id="43f85-145">This policy setting is equivalent to the Unrestricted execution policy.</span></span>

<span data-ttu-id="43f85-146">Als u deze beleids instelling uitschakelt, mogen er geen scripts worden uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="43f85-146">If you disable this policy setting, no scripts are allowed to run.</span></span> <span data-ttu-id="43f85-147">Deze beleids instelling is gelijk aan het beleid voor beperkte uitvoering.</span><span class="sxs-lookup"><span data-stu-id="43f85-147">This policy setting is equivalent to the Restricted execution policy.</span></span>

<span data-ttu-id="43f85-148">Als u deze beleids instelling uitschakelt of niet configureert, bepaalt het uitvoerings beleid dat is ingesteld voor de computer of gebruiker door de `Set-ExecutionPolicy` cmdlet, of scripts mogen worden uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="43f85-148">If you disable or do not configure this policy setting, the execution policy that is set for the computer or user by the `Set-ExecutionPolicy` cmdlet determines whether scripts are permitted to run.</span></span> <span data-ttu-id="43f85-149">De standaard waarde is beperkt.</span><span class="sxs-lookup"><span data-stu-id="43f85-149">The default value is Restricted.</span></span>

<span data-ttu-id="43f85-150">Zie [about_Execution_Policies](about_Execution_Policies.md)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="43f85-150">For more information, see [about_Execution_Policies](about_Execution_Policies.md).</span></span>

## <a name="turn-on-powershell-transcription"></a><span data-ttu-id="43f85-151">Power shell transcriptie inschakelen</span><span class="sxs-lookup"><span data-stu-id="43f85-151">Turn on powershell transcription</span></span>

<span data-ttu-id="43f85-152">Met de beleids instelling **Power shell transcriptie inschakelen** kunt u de invoer en uitvoer van Power shell core-opdrachten vastleggen in Transcripten op basis van tekst.</span><span class="sxs-lookup"><span data-stu-id="43f85-152">The **Turn on PowerShell Transcription** policy setting lets you capture the input and output of PowerShell Core commands into text-based transcripts.</span></span> <span data-ttu-id="43f85-153">Als u deze beleids instelling inschakelt, schakelt Power shell core transcriptie-logboek registratie in voor Power shell core en andere toepassingen die gebruikmaken van de Power shell Core-Engine.</span><span class="sxs-lookup"><span data-stu-id="43f85-153">If you enable this policy setting, PowerShell Core will enable transcription logging for PowerShell Core and any other applications that leverage the PowerShell Core engine.</span></span> <span data-ttu-id="43f85-154">Power shell core registreert standaard transcript uitvoer naar de map Mijn documenten van elke gebruiker, met een bestands naam die ' PowerShell_transcript ' bevat, samen met de computer naam en tijd gestart.</span><span class="sxs-lookup"><span data-stu-id="43f85-154">By default, PowerShell Core will record transcript output to each users' My Documents directory, with a file name that includes 'PowerShell_transcript', along with the computer name and time started.</span></span>
<span data-ttu-id="43f85-155">Het inschakelen van dit beleid is gelijk aan het aanroepen van de Start-Transcript cmdlet op elke Power shell-kern sessie.</span><span class="sxs-lookup"><span data-stu-id="43f85-155">Enabling this policy is equivalent to calling the Start-Transcript cmdlet on each PowerShell Core session.</span></span>

<span data-ttu-id="43f85-156">Als u deze beleids instelling uitschakelt, wordt de transcriptie-logboek registratie van op Power shell gebaseerde toepassingen standaard uitgeschakeld, maar u kunt transcripten nog steeds inschakelen via de Start-Transcript-cmdlet.</span><span class="sxs-lookup"><span data-stu-id="43f85-156">If you disable this policy setting, transcription logging of PowerShell-based applications is disabled by default, although transcripting can still be enabled through the Start-Transcript cmdlet.</span></span>

<span data-ttu-id="43f85-157">Als u de instelling output directory gebruikt om logboek registratie van transcriptie in te scha kelen op een gedeelde locatie, moet u ervoor zorgen dat u de toegang tot die Directory beperkt om te voor komen dat gebruikers de transcripten van andere gebruikers of computers weer geven.</span><span class="sxs-lookup"><span data-stu-id="43f85-157">If you use the OutputDirectory setting to enable transcription logging to a shared location, be sure to limit access to that directory to prevent users from viewing the transcripts of other users or computers.</span></span>

## <a name="set-the-default-source-path-for-update-help"></a><span data-ttu-id="43f85-158">Het standaard bronpad instellen voor Update-Help</span><span class="sxs-lookup"><span data-stu-id="43f85-158">Set the default source path for Update-Help</span></span>

<span data-ttu-id="43f85-159">Het **standaard bronpad instellen voor update-Help** beleids instelling stelt een standaard waarde in voor de para meter **SourcePath** van de `Update-Help` cmdlet.</span><span class="sxs-lookup"><span data-stu-id="43f85-159">The **Set the Default Source Path for Update-Help** policy setting sets a default value for the **SourcePath** parameter of the `Update-Help` cmdlet.</span></span>
<span data-ttu-id="43f85-160">Deze instelling voor komt dat gebruikers de `Update-Help` cmdlet gebruiken om Help-bestanden van Internet te downloaden.</span><span class="sxs-lookup"><span data-stu-id="43f85-160">This setting prevents users from using the `Update-Help` cmdlet to download help files from the Internet.</span></span>

> [!NOTE]
> <span data-ttu-id="43f85-161">Deze groepsbeleid instelling wordt weer gegeven onder **computer configuratie** en **gebruikers configuratie**.</span><span class="sxs-lookup"><span data-stu-id="43f85-161">This Group Policy setting appears under **Computer Configuration** and **User Configuration**.</span></span> <span data-ttu-id="43f85-162">Maar alleen de instelling groepsbeleid onder **computer configuratie** is van kracht.</span><span class="sxs-lookup"><span data-stu-id="43f85-162">However, only the Group Policy setting under **Computer Configuration** is effective.</span></span> <span data-ttu-id="43f85-163">De instelling groepsbeleid onder **gebruikers configuratie** wordt genegeerd.</span><span class="sxs-lookup"><span data-stu-id="43f85-163">The Group Policy setting under **User Configuration** is ignored.</span></span>

<span data-ttu-id="43f85-164">De `Update-Help` cmdlet downloadt en installeert de nieuwste Help-bestanden voor Power shell-modules en installeert deze op de computer.</span><span class="sxs-lookup"><span data-stu-id="43f85-164">The `Update-Help` cmdlet downloads and installs the newest help files for PowerShell modules and installs them on the computer.</span></span> <span data-ttu-id="43f85-165">Standaard `Update-Help` downloadt nieuwe Help-bestanden van een Internet locatie die is opgegeven door de module.</span><span class="sxs-lookup"><span data-stu-id="43f85-165">By default, `Update-Help` downloads new help files from an Internet location specified by the module.</span></span>

<span data-ttu-id="43f85-166">U kunt de cmdlet echter gebruiken `Save-Help` om de nieuwste Help-bestanden te downloaden naar een bestandssysteem locatie, zoals een netwerk share. vervolgens gebruikt u de `Update-Help` cmdlet om de Help-bestanden van de bestandssysteem locatie op te halen en te installeren op de computer.</span><span class="sxs-lookup"><span data-stu-id="43f85-166">However, you can use the `Save-Help` cmdlet to download the newest help files to a file system location, such as a network share, and then use the `Update-Help` cmdlet to get the help files from the file system location and install them on the computer.</span></span> <span data-ttu-id="43f85-167">De para meter **SourcePath** van de `Update-Help` cmdlet specificeert de locatie van het bestands systeem.</span><span class="sxs-lookup"><span data-stu-id="43f85-167">The **SourcePath** parameter of the `Update-Help` cmdlet specifies the file system location.</span></span>

<span data-ttu-id="43f85-168">Als u een standaard waarde voor de para meter **SourcePath** opgeeft, voegt deze Groepsbeleid impliciet de para meter **SourcePath** toe aan alle `Update-Help` opdrachten.</span><span class="sxs-lookup"><span data-stu-id="43f85-168">By providing a default value for the **SourcePath** parameter, this Group Policy setting implicitly adds the **SourcePath** parameter to all `Update-Help` commands.</span></span> <span data-ttu-id="43f85-169">Gebruikers kunnen de specifieke locatie van het bestands systeem die is opgegeven als de standaard waarde overschrijven door een andere locatie voor het bestands systeem in te voeren.</span><span class="sxs-lookup"><span data-stu-id="43f85-169">Users can override the particular file system location specified as the default value by entering a different file system location.</span></span>
<span data-ttu-id="43f85-170">Maar ze kunnen de para meter **SourcePath** niet uit de `Update-Help` opdracht verwijderen.</span><span class="sxs-lookup"><span data-stu-id="43f85-170">But they cannot remove the **SourcePath** parameter from the `Update-Help` command.</span></span>

<span data-ttu-id="43f85-171">Als u deze beleids instelling inschakelt, kunt u een standaard waarde opgeven voor de para meter **SourcePath** .</span><span class="sxs-lookup"><span data-stu-id="43f85-171">If you enable this policy setting, you can specify a default value for the **SourcePath** parameter.</span></span> <span data-ttu-id="43f85-172">Voer een locatie voor het bestands systeem in.</span><span class="sxs-lookup"><span data-stu-id="43f85-172">Enter a file system location.</span></span>

<span data-ttu-id="43f85-173">Als u deze beleids instelling uitschakelt of niet configureert, is er geen standaard waarde voor de para meter **SourcePath** van de `Update-Help` cmdlet.</span><span class="sxs-lookup"><span data-stu-id="43f85-173">If this policy setting is disabled or not configured, there is no default value for the **SourcePath** parameter of the `Update-Help` cmdlet.</span></span> <span data-ttu-id="43f85-174">Gebruikers kunnen Help downloaden van Internet of vanaf elke locatie van een bestands systeem.</span><span class="sxs-lookup"><span data-stu-id="43f85-174">Users can download help from the Internet or from any file system location.</span></span>

<span data-ttu-id="43f85-175">Zie [about_Updatable_Help](about_Updatable_Help.md) voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="43f85-175">For more information, see [about_Updatable_Help](about_Updatable_Help.md).</span></span>

## <a name="keywords"></a><span data-ttu-id="43f85-176">Trefwoorden</span><span class="sxs-lookup"><span data-stu-id="43f85-176">Keywords</span></span>

<span data-ttu-id="43f85-177">about_Group_Policies about_GroupPolicy</span><span class="sxs-lookup"><span data-stu-id="43f85-177">about_Group_Policies about_GroupPolicy</span></span>

## <a name="see-also"></a><span data-ttu-id="43f85-178">Zie ook</span><span class="sxs-lookup"><span data-stu-id="43f85-178">See also</span></span>

[<span data-ttu-id="43f85-179">about_Execution_Policies</span><span class="sxs-lookup"><span data-stu-id="43f85-179">about_Execution_Policies</span></span>](about_Execution_Policies.md)

[<span data-ttu-id="43f85-180">about_Modules</span><span class="sxs-lookup"><span data-stu-id="43f85-180">about_Modules</span></span>](about_Modules.md)

[<span data-ttu-id="43f85-181">about_Updatable_Help</span><span class="sxs-lookup"><span data-stu-id="43f85-181">about_Updatable_Help</span></span>](about_Updatable_Help.md)

[<span data-ttu-id="43f85-182">Get-ExecutionPolicy</span><span class="sxs-lookup"><span data-stu-id="43f85-182">Get-ExecutionPolicy</span></span>](xref:Microsoft.PowerShell.Security.Get-ExecutionPolicy)

[<span data-ttu-id="43f85-183">Set-ExecutionPolicy</span><span class="sxs-lookup"><span data-stu-id="43f85-183">Set-ExecutionPolicy</span></span>](xref:Microsoft.PowerShell.Security.Set-ExecutionPolicy)

[<span data-ttu-id="43f85-184">Get-module</span><span class="sxs-lookup"><span data-stu-id="43f85-184">Get-Module</span></span>](xref:Microsoft.PowerShell.Core.Get-Module)

[<span data-ttu-id="43f85-185">Update-Help</span><span class="sxs-lookup"><span data-stu-id="43f85-185">Update-Help</span></span>](xref:Microsoft.PowerShell.Core.Update-Help)

[<span data-ttu-id="43f85-186">Opslaan-Help</span><span class="sxs-lookup"><span data-stu-id="43f85-186">Save-Help</span></span>](xref:Microsoft.PowerShell.Core.Save-Help)

<!-- link references -->
[gpstore]: https://support.microsoft.com/help/3087759
