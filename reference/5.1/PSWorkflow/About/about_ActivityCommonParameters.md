---
description: Hierin worden de para meters beschreven die met Windows Power shell workflow worden toegevoegd aan activiteiten.
keywords: powershell,cmdlet
Locale: en-US
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/psworkflow/about/about_activitycommonparameters?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_ActivityCommonParameters
ms.openlocfilehash: b745bf17e4ae26156042ecdc25211830177bc692
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/13/2020
ms.locfileid: "93252408"
---
# <a name="about-activitycommonparameters"></a><span data-ttu-id="4c5cc-104">Over ActivityCommonParameters</span><span class="sxs-lookup"><span data-stu-id="4c5cc-104">About ActivityCommonParameters</span></span>

## <a name="short-description"></a><span data-ttu-id="4c5cc-105">KORTE BESCHRIJVING</span><span class="sxs-lookup"><span data-stu-id="4c5cc-105">SHORT DESCRIPTION</span></span>

<span data-ttu-id="4c5cc-106">Hierin worden de para meters beschreven die met Windows Power shell workflow worden toegevoegd aan activiteiten.</span><span class="sxs-lookup"><span data-stu-id="4c5cc-106">Describes the parameters that Windows PowerShell Workflow adds to activities.</span></span>

## <a name="long-description"></a><span data-ttu-id="4c5cc-107">LANGE BESCHRIJVING</span><span class="sxs-lookup"><span data-stu-id="4c5cc-107">LONG DESCRIPTION</span></span>

<span data-ttu-id="4c5cc-108">De Windows Power shell-werk stroom voegt de algemene para meters voor de activiteit toe aan activiteiten die zijn afgeleid van de basis klasse PSActivity.</span><span class="sxs-lookup"><span data-stu-id="4c5cc-108">Windows PowerShell Workflow adds the activity common parameters to activities that are derived from the PSActivity base class.</span></span> <span data-ttu-id="4c5cc-109">Deze categorie bevat de InlineScript-activiteit en Windows Power shell-cmdlets die worden geïmplementeerd als activiteiten, zoals Get-Process en Get-Wine vent.</span><span class="sxs-lookup"><span data-stu-id="4c5cc-109">This category includes the InlineScript activity and Windows PowerShell cmdlets that are implemented as activities, such as Get-Process and Get-WinEvent.</span></span>

<span data-ttu-id="4c5cc-110">De algemene para meters voor de activiteit zijn niet geldig voor de Suspend-Workflow en Checkpoint-Workflow activiteiten en ze worden niet toegevoegd aan cmdlets of expressies die automatisch worden uitgevoerd in een InlineScript-script blok of vergelijk bare activiteit.</span><span class="sxs-lookup"><span data-stu-id="4c5cc-110">The activity common parameters are not valid on the Suspend-Workflow and Checkpoint-Workflow activities and they are not added to cmdlets or expressions that Windows PowerShell Workflow automatically runs in an InlineScript script block or similar activity.</span></span> <span data-ttu-id="4c5cc-111">De algemene para meters voor de activiteit zijn beschikbaar voor de activiteit InlineScript, maar niet voor opdrachten in het InlineScript-script blok.</span><span class="sxs-lookup"><span data-stu-id="4c5cc-111">The activity common parameters are available on the InlineScript activity, but not on commands in the InlineScript script block.</span></span>

<span data-ttu-id="4c5cc-112">Verschillende algemene para meters voor de activiteit zijn ook algemene werk stroom parameters of Windows Power shell common para meters.</span><span class="sxs-lookup"><span data-stu-id="4c5cc-112">Several of the activity common parameters are also workflow common parameters or Windows PowerShell common parameters.</span></span> <span data-ttu-id="4c5cc-113">De algemene para meters voor andere activiteiten zijn uniek voor activiteiten.</span><span class="sxs-lookup"><span data-stu-id="4c5cc-113">Other activity common parameters are unique to activities.</span></span>

<span data-ttu-id="4c5cc-114">Zie about_WorkflowCommonParameters voor meer informatie over de algemene werk stroom parameters.</span><span class="sxs-lookup"><span data-stu-id="4c5cc-114">For information about the workflow common parameters, see about_WorkflowCommonParameters.</span></span> <span data-ttu-id="4c5cc-115">Zie about_CommonParameters voor meer informatie over de algemene para meters van Windows Power shell.</span><span class="sxs-lookup"><span data-stu-id="4c5cc-115">For information about the Windows PowerShell common parameters, see about_CommonParameters.</span></span>

### <a name="list-of-activity-common-parameters"></a><span data-ttu-id="4c5cc-116">LIJST MET ALGEMENE PARA METERS VOOR ACTIVITEIT</span><span class="sxs-lookup"><span data-stu-id="4c5cc-116">LIST OF ACTIVITY COMMON PARAMETERS</span></span>

```
AppendOutput                      PSDebug
Debug                             PSDisableSerialization
DisplayName                       PSDisableSerializationPreference
ErrorAction                       PSError
Input                             PSPersist
MergeErrorToOutput                PSPort
PSActionRetryCount                PSProgress
PSActionRetryIntervalSec          PSProgressMessage
PSActionRunningTimeoutSec         PSRemotingBehavior
PSApplicationName                 PSRequiredModules
PSAuthentication                  PSSessionOption
PSCertificateThumbprint           PSUseSSL
PSComputerName                    PSVerbose
PSConfigurationName               PSWarning
PSConnectionRetryCount            Result
PSConnectionRetryIntervalSec      UseDefaultInput
PSConnectionURI                   Verbose
PSCredential                      WarningAction
```

### <a name="parameter-descriptions"></a><span data-ttu-id="4c5cc-117">PARAMETER BESCHRIJVINGEN</span><span class="sxs-lookup"><span data-stu-id="4c5cc-117">PARAMETER DESCRIPTIONS</span></span>

<span data-ttu-id="4c5cc-118">In deze sectie worden de algemene para meters voor de activiteit beschreven.</span><span class="sxs-lookup"><span data-stu-id="4c5cc-118">This section describes the activity common parameters.</span></span>

#### <a name="appendoutput-boolean"></a><span data-ttu-id="4c5cc-119">AppendOutput \<Boolean\></span><span class="sxs-lookup"><span data-stu-id="4c5cc-119">AppendOutput \<Boolean\></span></span>

<span data-ttu-id="4c5cc-120">De waarde van de `$True` uitvoer van de activiteit wordt toegevoegd aan de waarde van de variabele.</span><span class="sxs-lookup"><span data-stu-id="4c5cc-120">A value of `$True` adds the output of the activity to the value of the variable.</span></span>
<span data-ttu-id="4c5cc-121">De waarde van `$False` heeft geen effect.</span><span class="sxs-lookup"><span data-stu-id="4c5cc-121">A value of `$False` has no effect.</span></span> <span data-ttu-id="4c5cc-122">Als u een waarde aan een variabele toewijst, wordt de waarde van de variabele standaard vervangen.</span><span class="sxs-lookup"><span data-stu-id="4c5cc-122">By default, assigning a value to a variable replaces the variable value.</span></span>

<span data-ttu-id="4c5cc-123">Met de volgende opdrachten wordt bijvoorbeeld een proces object toegevoegd aan het Service object in de `$x` variabele.</span><span class="sxs-lookup"><span data-stu-id="4c5cc-123">For example, the following commands add a process object to the service object in the `$x` variable.</span></span>

```powershell
Workflow Test-Workflow
{
    $x = Get-Service
    $x = Get-Process -AppendOutput $true
}
```

<span data-ttu-id="4c5cc-124">Deze para meter is bedoeld voor op XAML gebaseerde werk stromen.</span><span class="sxs-lookup"><span data-stu-id="4c5cc-124">This parameter is designed for XAML-based workflows.</span></span> <span data-ttu-id="4c5cc-125">In script werk stromen kunt u ook de operator + = toewijzen gebruiken om uitvoer toe te voegen aan de waarde van een variabele, zoals wordt weer gegeven in het volgende voor beeld.</span><span class="sxs-lookup"><span data-stu-id="4c5cc-125">In script workflows, you can also use the += assignment operator to add output to the value of a variable, as shown in the following example.</span></span>

```powershell
Workflow Test-Workflow
{
    $x = Get-Service
    $x += Get-Process
}
```

#### <a name="debug-switchparameter"></a><span data-ttu-id="4c5cc-126">Fout opsporing \<SwitchParameter\></span><span class="sxs-lookup"><span data-stu-id="4c5cc-126">Debug \<SwitchParameter\></span></span>

<span data-ttu-id="4c5cc-127">Geeft details op programmeer niveau weer over de bewerking die door de opdracht wordt uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="4c5cc-127">Displays programmer-level detail about the operation performed by the command.</span></span>
<span data-ttu-id="4c5cc-128">De para meter debug overschrijft de waarde van de variabele $DebugPreference voor de huidige opdracht.</span><span class="sxs-lookup"><span data-stu-id="4c5cc-128">The Debug parameter overrides the value of the $DebugPreference variable for the current command.</span></span> <span data-ttu-id="4c5cc-129">Deze para meter werkt alleen als de opdracht fout opsporingsgegevens genereert.</span><span class="sxs-lookup"><span data-stu-id="4c5cc-129">This parameter works only when the command generates debugging messages.</span></span> <span data-ttu-id="4c5cc-130">Deze para meter is ook een gemeen schappelijke Windows Power shell-para meter.</span><span class="sxs-lookup"><span data-stu-id="4c5cc-130">This parameter is also a Windows PowerShell common parameter.</span></span>

#### <a name="displayname-string"></a><span data-ttu-id="4c5cc-131">DisplayName \<String\></span><span class="sxs-lookup"><span data-stu-id="4c5cc-131">DisplayName \<String\></span></span>

<span data-ttu-id="4c5cc-132">Hiermee geeft u een beschrijvende naam op voor de activiteit.</span><span class="sxs-lookup"><span data-stu-id="4c5cc-132">Specifies a friendly name for the activity.</span></span> <span data-ttu-id="4c5cc-133">De waarde DisplayName wordt weer gegeven in de voortgangs balk terwijl de werk stroom wordt uitgevoerd en in de waarde van de eigenschap Progress van de werk stroom taak.</span><span class="sxs-lookup"><span data-stu-id="4c5cc-133">The DisplayName value appears in the progress bar while the workflow runs and in the value of the Progress property of the workflow job.</span></span> <span data-ttu-id="4c5cc-134">Wanneer de para meter PSProgressMessage ook is opgenomen in de opdracht, wordt de inhoud van de voortgangs balk weer gegeven in \<DisplayName\> : \<PSProgressMessage\> Format.</span><span class="sxs-lookup"><span data-stu-id="4c5cc-134">When the PSProgressMessage parameter is also included in the command, the progress bar content appears in \<DisplayName\>:\<PSProgressMessage\> format.</span></span>

#### <a name="erroraction-actionpreference"></a><span data-ttu-id="4c5cc-135">Error Action \<ActionPreference\></span><span class="sxs-lookup"><span data-stu-id="4c5cc-135">ErrorAction \<ActionPreference\></span></span>

<span data-ttu-id="4c5cc-136">Hiermee wordt bepaald hoe de activiteit reageert op een niet-afsluit fout van de opdracht.</span><span class="sxs-lookup"><span data-stu-id="4c5cc-136">Determines how the activity responds to a non-terminating error from the command.</span></span> <span data-ttu-id="4c5cc-137">Dit heeft geen invloed op beëindigings fouten.</span><span class="sxs-lookup"><span data-stu-id="4c5cc-137">It has no effect on termination errors.</span></span> <span data-ttu-id="4c5cc-138">Deze para meter werkt alleen als de opdracht een niet-afsluit fout genereert, zoals die van de Write-Error-cmdlet.</span><span class="sxs-lookup"><span data-stu-id="4c5cc-138">This parameter works only when the command generates a non-terminating error, such as those from the Write-Error cmdlet.</span></span> <span data-ttu-id="4c5cc-139">De para meter error Action overschrijft de waarde van de variabele $ErrorActionPreference voor de huidige opdracht.</span><span class="sxs-lookup"><span data-stu-id="4c5cc-139">The ErrorAction parameter overrides the value of the $ErrorActionPreference variable for the current command.</span></span> <span data-ttu-id="4c5cc-140">Deze para meter is ook een gemeen schappelijke Windows Power shell-para meter.</span><span class="sxs-lookup"><span data-stu-id="4c5cc-140">This parameter is also a Windows PowerShell common parameter.</span></span>

<span data-ttu-id="4c5cc-141">Geldige waarden:</span><span class="sxs-lookup"><span data-stu-id="4c5cc-141">Valid values:</span></span>

- <span data-ttu-id="4c5cc-142">Doen.</span><span class="sxs-lookup"><span data-stu-id="4c5cc-142">Continue.</span></span> <span data-ttu-id="4c5cc-143">Hiermee wordt het fout bericht weer gegeven en wordt de opdracht verder uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="4c5cc-143">Displays the error message and continues executing the command.</span></span> <span data-ttu-id="4c5cc-144">' Door gaan ' is de standaard waarde.</span><span class="sxs-lookup"><span data-stu-id="4c5cc-144">"Continue" is the default value.</span></span>

- <span data-ttu-id="4c5cc-145">Negeren.</span><span class="sxs-lookup"><span data-stu-id="4c5cc-145">Ignore.</span></span> <span data-ttu-id="4c5cc-146">Onderdrukt het fout bericht en gaat door met het uitvoeren van de opdracht.</span><span class="sxs-lookup"><span data-stu-id="4c5cc-146">Suppresses the error message and continues executing the command.</span></span>
  <span data-ttu-id="4c5cc-147">In tegens telling tot SilentlyContinue, voegt negeren het fout bericht niet toe aan de automatische variabele $Error.</span><span class="sxs-lookup"><span data-stu-id="4c5cc-147">Unlike SilentlyContinue, Ignore does not add the error message to the $Error automatic variable.</span></span> <span data-ttu-id="4c5cc-148">De waarde ignore is geïntroduceerd in Windows Power Shell 3,0.</span><span class="sxs-lookup"><span data-stu-id="4c5cc-148">The Ignore value is introduced in Windows PowerShell 3.0.</span></span>

- <span data-ttu-id="4c5cc-149">Inquire.</span><span class="sxs-lookup"><span data-stu-id="4c5cc-149">Inquire.</span></span> <span data-ttu-id="4c5cc-150">Hiermee wordt het fout bericht weer gegeven en wordt u gevraagd om bevestiging voordat u doorgaat met de uitvoering.</span><span class="sxs-lookup"><span data-stu-id="4c5cc-150">Displays the error message and prompts you for confirmation before continuing execution.</span></span> <span data-ttu-id="4c5cc-151">Deze waarde wordt zelden gebruikt.</span><span class="sxs-lookup"><span data-stu-id="4c5cc-151">This value is rarely used.</span></span>

- <span data-ttu-id="4c5cc-152">Tot.</span><span class="sxs-lookup"><span data-stu-id="4c5cc-152">Suspend.</span></span> <span data-ttu-id="4c5cc-153">Onderbreekt automatisch een werk stroom taak zodat deze verder kan worden onderzocht.</span><span class="sxs-lookup"><span data-stu-id="4c5cc-153">Automatically suspends a workflow job to allow for further investigation.</span></span> <span data-ttu-id="4c5cc-154">Na onderzoek kan de werk stroom worden hervat.</span><span class="sxs-lookup"><span data-stu-id="4c5cc-154">After investigation, the workflow can be resumed.</span></span>

- <span data-ttu-id="4c5cc-155">SilentlyContinue.</span><span class="sxs-lookup"><span data-stu-id="4c5cc-155">SilentlyContinue.</span></span> <span data-ttu-id="4c5cc-156">Onderdrukt het fout bericht en gaat door met het uitvoeren van de opdracht.</span><span class="sxs-lookup"><span data-stu-id="4c5cc-156">Suppresses the error message and continues executing the command.</span></span>

- <span data-ttu-id="4c5cc-157">Stoppen.</span><span class="sxs-lookup"><span data-stu-id="4c5cc-157">Stop.</span></span> <span data-ttu-id="4c5cc-158">Geeft het fout bericht weer en stopt met het uitvoeren van de opdracht.</span><span class="sxs-lookup"><span data-stu-id="4c5cc-158">Displays the error message and stops executing the command.</span></span>

#### <a name="input-object"></a><span data-ttu-id="4c5cc-159">Ingevoerd \<Object[]\></span><span class="sxs-lookup"><span data-stu-id="4c5cc-159">Input \<Object[]\></span></span>

<span data-ttu-id="4c5cc-160">Hiermee wordt een verzameling objecten verzonden naar een activiteit.</span><span class="sxs-lookup"><span data-stu-id="4c5cc-160">Submits a collection of objects to an activity.</span></span> <span data-ttu-id="4c5cc-161">Dit is een alternatief voor pijpleiding objecten per keer naar de activiteit.</span><span class="sxs-lookup"><span data-stu-id="4c5cc-161">This is an alternative to piping objects to the activity one at a time.</span></span>

#### <a name="mergeerrortooutput-boolean"></a><span data-ttu-id="4c5cc-162">MergeErrorToOutput \<Boolean\></span><span class="sxs-lookup"><span data-stu-id="4c5cc-162">MergeErrorToOutput \<Boolean\></span></span>

<span data-ttu-id="4c5cc-163">Een waarde voor `$True` het toevoegen van fouten aan de uitvoer stroom.</span><span class="sxs-lookup"><span data-stu-id="4c5cc-163">A value of `$True` adds errors to the output stream.</span></span> <span data-ttu-id="4c5cc-164">Een waarde van `$False` is niet van invloed op.</span><span class="sxs-lookup"><span data-stu-id="4c5cc-164">A value of `$False` has not effect.</span></span> <span data-ttu-id="4c5cc-165">Gebruik deze para meter met de parallelle `ForEach -Parallel` sleutel en tref woorden voor het verzamelen van fouten en uitvoer van meerdere parallelle opdrachten in één verzameling.</span><span class="sxs-lookup"><span data-stu-id="4c5cc-165">Use this parameter with the Parallel and `ForEach -Parallel` keywords to collect errors and output from multiple parallel commands in a single collection.</span></span>

#### <a name="psactionretrycount-int32"></a><span data-ttu-id="4c5cc-166">PSActionRetryCount \<Int32\></span><span class="sxs-lookup"><span data-stu-id="4c5cc-166">PSActionRetryCount \<Int32\></span></span>

<span data-ttu-id="4c5cc-167">Herhaalde pogingen om de activiteit uit te voeren als de eerste poging mislukt.</span><span class="sxs-lookup"><span data-stu-id="4c5cc-167">Tries repeatedly to run the activity if the first attempt fails.</span></span> <span data-ttu-id="4c5cc-168">De standaard waarde, 0, probeert niet.</span><span class="sxs-lookup"><span data-stu-id="4c5cc-168">The default value, 0, does not retry.</span></span>

#### <a name="psactionretryintervalsec-int32"></a><span data-ttu-id="4c5cc-169">PSActionRetryIntervalSec \<Int32\></span><span class="sxs-lookup"><span data-stu-id="4c5cc-169">PSActionRetryIntervalSec \<Int32\></span></span>

<span data-ttu-id="4c5cc-170">Bepaalt het interval tussen nieuwe pogingen in seconden.</span><span class="sxs-lookup"><span data-stu-id="4c5cc-170">Determines the interval between action retries in seconds.</span></span> <span data-ttu-id="4c5cc-171">De standaard waarde, 0, probeert de actie onmiddellijk opnieuw uit te proberen.</span><span class="sxs-lookup"><span data-stu-id="4c5cc-171">The default value, 0, retries the action immediately.</span></span> <span data-ttu-id="4c5cc-172">Deze para meter is alleen geldig als de para meter PSActionRetryCount ook in de opdracht wordt gebruikt.</span><span class="sxs-lookup"><span data-stu-id="4c5cc-172">This parameter is valid only when the PSActionRetryCount parameter is also used in the command.</span></span>

#### <a name="psactionrunningtimeoutsec-int32"></a><span data-ttu-id="4c5cc-173">PSActionRunningTimeoutSec \<Int32\></span><span class="sxs-lookup"><span data-stu-id="4c5cc-173">PSActionRunningTimeoutSec \<Int32\></span></span>

<span data-ttu-id="4c5cc-174">Hiermee wordt bepaald hoe lang de activiteit op elke doel computer kan worden uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="4c5cc-174">Determines how long the activity can run on each target computer.</span></span> <span data-ttu-id="4c5cc-175">Als de activiteit niet wordt voltooid voordat de time-out is verlopen, genereert de Windows Power shell-werk stroom een afsluit fout en stopt de verwerking van de werk stroom op de betrokken doel computer.</span><span class="sxs-lookup"><span data-stu-id="4c5cc-175">If the activity does not complete before the timeout expires, Windows PowerShell Workflow generates a terminating error and stops processing the workflow on the affected target computer.</span></span>

#### <a name="psallowredirection-boolean"></a><span data-ttu-id="4c5cc-176">PSAllowRedirection \<Boolean\></span><span class="sxs-lookup"><span data-stu-id="4c5cc-176">PSAllowRedirection \<Boolean\></span></span>

<span data-ttu-id="4c5cc-177">Met de waarde $True kan de verbinding met de doel computers worden omgeleid.</span><span class="sxs-lookup"><span data-stu-id="4c5cc-177">A value of $True allows redirection of the connection to the target computers.</span></span>
<span data-ttu-id="4c5cc-178">Een waarde van $False heeft geen effect.</span><span class="sxs-lookup"><span data-stu-id="4c5cc-178">A value of $False has no effect.</span></span> <span data-ttu-id="4c5cc-179">Deze algemene activiteit para meter is ook een algemene werk stroom parameter.</span><span class="sxs-lookup"><span data-stu-id="4c5cc-179">This activity common parameter is also a workflow common parameter.</span></span>

<span data-ttu-id="4c5cc-180">Wanneer u de para meter PSConnectionURI gebruikt, kan de externe bestemming een instructie retour neren die wordt omgeleid naar een andere URI.</span><span class="sxs-lookup"><span data-stu-id="4c5cc-180">When you use the PSConnectionURI parameter, the remote destination can return an instruction to redirect to a different URI.</span></span> <span data-ttu-id="4c5cc-181">Standaard worden verbindingen niet door Windows Power shell omgeleid, maar u kunt de para meter PSAllowRedirection gebruiken met de waarde $True om omleiding van de verbinding met de doel computer toe te staan.</span><span class="sxs-lookup"><span data-stu-id="4c5cc-181">By default, Windows PowerShell does not redirect connections, but you can use the PSAllowRedirection parameter with a value of $True to allow redirection of the connection to the target computer.</span></span>

<span data-ttu-id="4c5cc-182">U kunt ook het aantal keren beperken dat de verbinding wordt omgeleid door de eigenschap MaximumConnectionRedirectionCount van de `$PSSessionOption` Voorkeurs variabele in te stellen of de eigenschap MaximumConnectionRedirectionCount van de waarde van de SSessionOption para meter van cmdlets waarmee een sessie wordt gemaakt.</span><span class="sxs-lookup"><span data-stu-id="4c5cc-182">You can also limit the number of times that the connection is redirected by setting the MaximumConnectionRedirectionCount property of the `$PSSessionOption` preference variable, or the MaximumConnectionRedirectionCount property of the value of the SSessionOption parameter of cmdlets that create a session.</span></span> <span data-ttu-id="4c5cc-183">De standaard waarde is 5.</span><span class="sxs-lookup"><span data-stu-id="4c5cc-183">The default value is 5.</span></span>

#### <a name="psapplicationname-string"></a><span data-ttu-id="4c5cc-184">PSApplicationName \<String\></span><span class="sxs-lookup"><span data-stu-id="4c5cc-184">PSApplicationName \<String\></span></span>

<span data-ttu-id="4c5cc-185">Hiermee geeft u het segment van de toepassings naam op van de verbindings-URI die wordt gebruikt om verbinding te maken met de doel computers.</span><span class="sxs-lookup"><span data-stu-id="4c5cc-185">Specifies the application name segment of the connection URI that is used to connect to the target computers.</span></span> <span data-ttu-id="4c5cc-186">Gebruik deze para meter om de naam van de toepassing op te geven wanneer u de para meter ConnectionURI niet gebruikt in de opdracht.</span><span class="sxs-lookup"><span data-stu-id="4c5cc-186">Use this parameter to specify the application name when you are not using the ConnectionURI parameter in the command.</span></span> <span data-ttu-id="4c5cc-187">Deze algemene activiteit para meter is ook een algemene werk stroom parameter.</span><span class="sxs-lookup"><span data-stu-id="4c5cc-187">This activity common parameter is also a workflow common parameter.</span></span>

<span data-ttu-id="4c5cc-188">De standaard waarde is de waarde van de `$PSSessionApplicationName` Voorkeurs variabele op de doel computer.</span><span class="sxs-lookup"><span data-stu-id="4c5cc-188">The default value is the value of the `$PSSessionApplicationName` preference variable on the target computer.</span></span> <span data-ttu-id="4c5cc-189">Als deze voorkeurs variabele niet is gedefinieerd, is de standaard waarde WSMAN.</span><span class="sxs-lookup"><span data-stu-id="4c5cc-189">If this preference variable is not defined, the default value is WSMAN.</span></span> <span data-ttu-id="4c5cc-190">Deze waarde is geschikt voor de meeste toepassingen.</span><span class="sxs-lookup"><span data-stu-id="4c5cc-190">This value is appropriate for most uses.</span></span> <span data-ttu-id="4c5cc-191">Zie [about_Preference_Variables](../../Microsoft.PowerShell.Core/About/about_Preference_Variables.md)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="4c5cc-191">For more information, see [about_Preference_Variables](../../Microsoft.PowerShell.Core/About/about_Preference_Variables.md).</span></span>

<span data-ttu-id="4c5cc-192">De WinRM-service gebruikt de naam van de toepassing om een listener te selecteren om de verbindings aanvraag te onderhouden.</span><span class="sxs-lookup"><span data-stu-id="4c5cc-192">The WinRM service uses the application name to select a listener to service the connection request.</span></span> <span data-ttu-id="4c5cc-193">De waarde van deze para meter moet overeenkomen met de waarde van de eigenschap URLPrefix van een listener op de externe computer.</span><span class="sxs-lookup"><span data-stu-id="4c5cc-193">The value of this parameter should match the value of the URLPrefix property of a listener on the remote computer.</span></span>

#### <a name="psauthentication-authenticationmechanism"></a><span data-ttu-id="4c5cc-194">PSAuthentication \<AuthenticationMechanism\></span><span class="sxs-lookup"><span data-stu-id="4c5cc-194">PSAuthentication \<AuthenticationMechanism\></span></span>

<span data-ttu-id="4c5cc-195">Hiermee geeft u het mechanisme op dat wordt gebruikt om de referenties van de gebruiker te verifiëren wanneer er verbinding wordt gemaakt met de doel computers.</span><span class="sxs-lookup"><span data-stu-id="4c5cc-195">Specifies the mechanism that is used to authenticate the user's credentials when connecting to the target computers.</span></span> <span data-ttu-id="4c5cc-196">Geldige waarden zijn default, Basic, CredSSP, Digest, Kerberos, Negotiate en NegotiateWithImplicitCredential.</span><span class="sxs-lookup"><span data-stu-id="4c5cc-196">Valid values are Default, Basic, Credssp, Digest, Kerberos, Negotiate, and NegotiateWithImplicitCredential.</span></span> <span data-ttu-id="4c5cc-197">De standaard waarde is standaard.</span><span class="sxs-lookup"><span data-stu-id="4c5cc-197">The default value is Default.</span></span> <span data-ttu-id="4c5cc-198">Deze algemene activiteit para meter is ook een algemene werk stroom parameter.</span><span class="sxs-lookup"><span data-stu-id="4c5cc-198">This activity common parameter is also a workflow common parameter.</span></span>

<span data-ttu-id="4c5cc-199">Voor informatie over de waarden van deze para meter raadpleegt u de beschrijving van de inventarisatie **System. Management. Automation. Runspaces. AuthenticationMechanism** in MSDN.</span><span class="sxs-lookup"><span data-stu-id="4c5cc-199">For information about the values of this parameter, see the description of the **System.Management.Automation.Runspaces.AuthenticationMechanism** enumeration in MSDN.</span></span>

> [!WARNING]
> <span data-ttu-id="4c5cc-200">CredSSP-verificatie (Credential Security service provider), waarbij de referenties van de gebruiker worden door gegeven aan een externe computer die moet worden geverifieerd, is ontworpen voor opdrachten waarvoor verificatie is vereist voor meer dan één bron, zoals het openen van een externe netwerk share.</span><span class="sxs-lookup"><span data-stu-id="4c5cc-200">Credential Security Service Provider (CredSSP) authentication, in which the user's credentials are passed to a remote computer to be authenticated, is designed for commands that require authentication on more than one resource, such as accessing a remote network share.</span></span> <span data-ttu-id="4c5cc-201">Dit mechanisme verhoogt het beveiligings risico van de externe bewerking.</span><span class="sxs-lookup"><span data-stu-id="4c5cc-201">This mechanism increases the security risk of the remote operation.</span></span> <span data-ttu-id="4c5cc-202">Als er is geknoeid met de externe computer, kunnen de referenties die aan worden door gegeven, worden gebruikt om de netwerk sessie te beheren.</span><span class="sxs-lookup"><span data-stu-id="4c5cc-202">If the remote computer is compromised, the credentials that are passed to it can be used to control the network session.</span></span>

#### <a name="pscertificatethumbprint-string"></a><span data-ttu-id="4c5cc-203">PSCertificateThumbprint \<String\></span><span class="sxs-lookup"><span data-stu-id="4c5cc-203">PSCertificateThumbprint \<String\></span></span>

<span data-ttu-id="4c5cc-204">Hiermee geeft u het digitale open bare-sleutel certificaat (x509) op van een gebruikers account dat is gemachtigd om deze actie uit te voeren.</span><span class="sxs-lookup"><span data-stu-id="4c5cc-204">Specifies the digital public key certificate (X509) of a user account that has permission to perform this action.</span></span> <span data-ttu-id="4c5cc-205">Voer de vinger afdruk van het certificaat in.</span><span class="sxs-lookup"><span data-stu-id="4c5cc-205">Enter the certificate thumbprint of the certificate.</span></span> <span data-ttu-id="4c5cc-206">Deze algemene activiteit para meter is ook een algemene werk stroom parameter.</span><span class="sxs-lookup"><span data-stu-id="4c5cc-206">This activity common parameter is also a workflow common parameter.</span></span>

<span data-ttu-id="4c5cc-207">Certificaten worden gebruikt in authenticatie op basis van client certificaten.</span><span class="sxs-lookup"><span data-stu-id="4c5cc-207">Certificates are used in client certificate-based authentication.</span></span> <span data-ttu-id="4c5cc-208">Ze kunnen alleen worden toegewezen aan lokale gebruikers accounts. ze werken niet met domein accounts.</span><span class="sxs-lookup"><span data-stu-id="4c5cc-208">They can only be mapped to local user accounts; they do not work with domain accounts.</span></span>

<span data-ttu-id="4c5cc-209">Als u een certificaat wilt ophalen, gebruikt u de cmdlets [Get-item](xref:Microsoft.PowerShell.Management.Get-Item) of [Get-Child item](xref:Microsoft.PowerShell.Management.Get-ChildItem) in het Windows Power shell-certificaat: station.</span><span class="sxs-lookup"><span data-stu-id="4c5cc-209">To get a certificate, use the [Get-Item](xref:Microsoft.PowerShell.Management.Get-Item) or [Get-ChildItem](xref:Microsoft.PowerShell.Management.Get-ChildItem) cmdlets in the Windows PowerShell Cert: drive.</span></span>

#### <a name="pscomputername-string"></a><span data-ttu-id="4c5cc-210">PSComputerName \<String[]\></span><span class="sxs-lookup"><span data-stu-id="4c5cc-210">PSComputerName \<String[]\></span></span>

<span data-ttu-id="4c5cc-211">Hiermee geeft u de doel computers op waarop de activiteit wordt uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="4c5cc-211">Specifies the target computers on which the activity run.</span></span> <span data-ttu-id="4c5cc-212">Standaard is dit de lokale computer.</span><span class="sxs-lookup"><span data-stu-id="4c5cc-212">The default is the local computer.</span></span> <span data-ttu-id="4c5cc-213">Deze algemene activiteit para meter is ook een algemene werk stroom parameter.</span><span class="sxs-lookup"><span data-stu-id="4c5cc-213">This activity common parameter is also a workflow common parameter.</span></span>

<span data-ttu-id="4c5cc-214">Typ de NETBIOS-naam, het IP-adres of de FQDN-naam (Fully Qualified Domain Name) van een of meer computers in een door komma's gescheiden lijst.</span><span class="sxs-lookup"><span data-stu-id="4c5cc-214">Type the NETBIOS name, IP address, or fully-qualified domain name of one or more computers in a comma-separated list.</span></span> <span data-ttu-id="4c5cc-215">Typ de computer naam, ' localhost ' of een punt (.) om de lokale computer op te geven.</span><span class="sxs-lookup"><span data-stu-id="4c5cc-215">To specify the local computer, type the computer name, "localhost", or a dot (.).</span></span>

<span data-ttu-id="4c5cc-216">Als u de lokale computer in de waarde van de para meter PSComputerName wilt toevoegen, opent u Windows Power shell met de optie als administrator uitvoeren.</span><span class="sxs-lookup"><span data-stu-id="4c5cc-216">To include the local computer in the value of the PSComputerName parameter, open Windows PowerShell with the "Run as administrator" option.</span></span>

<span data-ttu-id="4c5cc-217">Als deze para meter wordt wegge laten uit de opdracht, of als de waarde $null of een lege teken reeks is, is het werk stroom doel de lokale computer en wordt Windows Power shell Remoting niet gebruikt om de opdracht uit te voeren.</span><span class="sxs-lookup"><span data-stu-id="4c5cc-217">If this parameter is omitted from the command, or it value is $null or an empty string, the workflow target is the local computer and Windows PowerShell remoting is not used to run the command.</span></span>

<span data-ttu-id="4c5cc-218">Als u een IP-adres wilt gebruiken in de waarde van de para meter ComputerName, moet de opdracht de para meter PSCredential bevatten.</span><span class="sxs-lookup"><span data-stu-id="4c5cc-218">To use an IP address in the value of the ComputerName parameter, the command must include the PSCredential parameter.</span></span> <span data-ttu-id="4c5cc-219">De computer moet ook worden geconfigureerd voor HTTPS-Trans Port of het IP-adres van de externe computer moet worden opgenomen in de WinRM TrustedHosts-lijst op de lokale computer.</span><span class="sxs-lookup"><span data-stu-id="4c5cc-219">Also, the computer must be configured for HTTPS transport or the IP address of the remote computer must be included in the WinRM TrustedHosts list on the local computer.</span></span> <span data-ttu-id="4c5cc-220">Zie "een computer toevoegen aan de lijst met vertrouwde hosts" in [about_Remote_Troubleshooting](../../Microsoft.PowerShell.Core/About/about_Remote_Troubleshooting.md)voor instructies voor het toevoegen van een computer naam aan de lijst TrustedHosts.</span><span class="sxs-lookup"><span data-stu-id="4c5cc-220">For instructions for adding a computer name to the TrustedHosts list, see "How to Add a Computer to the Trusted Host List" in [about_Remote_Troubleshooting](../../Microsoft.PowerShell.Core/About/about_Remote_Troubleshooting.md).</span></span>

#### <a name="psconfigurationname-string"></a><span data-ttu-id="4c5cc-221">PSConfigurationName \<String\></span><span class="sxs-lookup"><span data-stu-id="4c5cc-221">PSConfigurationName \<String\></span></span>

<span data-ttu-id="4c5cc-222">Hiermee geeft u de sessie configuraties op die worden gebruikt voor het maken van sessies op de doel computers.</span><span class="sxs-lookup"><span data-stu-id="4c5cc-222">Specifies the session configurations that are used to create sessions on the target computers.</span></span> <span data-ttu-id="4c5cc-223">Voer de naam in van een sessie configuratie op de doel computers (niet op de computer waarop de werk stroom wordt uitgevoerd).</span><span class="sxs-lookup"><span data-stu-id="4c5cc-223">Enter the name of a session configuration on the target computers (not on the computer that is running the workflow.</span></span> <span data-ttu-id="4c5cc-224">De standaard instelling is micro soft. Power shell.</span><span class="sxs-lookup"><span data-stu-id="4c5cc-224">The default is Microsoft.PowerShell.</span></span> <span data-ttu-id="4c5cc-225">Deze algemene activiteit para meter is ook een algemene werk stroom parameter.</span><span class="sxs-lookup"><span data-stu-id="4c5cc-225">This activity common parameter is also a workflow common parameter.</span></span>

#### <a name="psconnectionretrycount-uint"></a><span data-ttu-id="4c5cc-226">PSConnectionRetryCount \<UInt\></span><span class="sxs-lookup"><span data-stu-id="4c5cc-226">PSConnectionRetryCount \<UInt\></span></span>

<span data-ttu-id="4c5cc-227">Hiermee geeft u het maximum aantal pogingen op om verbinding te maken met elke doel computer als de eerste verbindings poging mislukt.</span><span class="sxs-lookup"><span data-stu-id="4c5cc-227">Specifies the maximum number of attempts to connect to each target computer if the first connection attempt fails.</span></span> <span data-ttu-id="4c5cc-228">Voer een getal tussen 1 en 4.294.967.295 (UInt. MaxValue) in.</span><span class="sxs-lookup"><span data-stu-id="4c5cc-228">Enter a number between 1 and 4,294,967,295 (UInt.MaxValue).</span></span> <span data-ttu-id="4c5cc-229">De standaard waarde, nul (0), vertegenwoordigt geen nieuwe pogingen.</span><span class="sxs-lookup"><span data-stu-id="4c5cc-229">The default value, zero (0), represents no retry attempts.</span></span>
<span data-ttu-id="4c5cc-230">Deze algemene activiteit para meter is ook een algemene werk stroom parameter.</span><span class="sxs-lookup"><span data-stu-id="4c5cc-230">This activity common parameter is also a workflow common parameter.</span></span>

#### <a name="psconnectionretryintervalsec-uint"></a><span data-ttu-id="4c5cc-231">PSConnectionRetryIntervalSec \<UInt\></span><span class="sxs-lookup"><span data-stu-id="4c5cc-231">PSConnectionRetryIntervalSec \<UInt\></span></span>

<span data-ttu-id="4c5cc-232">Hiermee geeft u de vertraging tussen nieuwe pogingen in seconden op.</span><span class="sxs-lookup"><span data-stu-id="4c5cc-232">Specifies the delay between connection retry attempts in seconds.</span></span> <span data-ttu-id="4c5cc-233">De standaardwaarde is nul (0).</span><span class="sxs-lookup"><span data-stu-id="4c5cc-233">The default value is zero (0).</span></span> <span data-ttu-id="4c5cc-234">Deze para meter is alleen geldig wanneer de waarde van PSConnectionRetryCount ten minste 1 is.</span><span class="sxs-lookup"><span data-stu-id="4c5cc-234">This parameter is valid only when the value of PSConnectionRetryCount is at least 1.</span></span> <span data-ttu-id="4c5cc-235">Deze algemene activiteit para meter is ook een algemene werk stroom parameter.</span><span class="sxs-lookup"><span data-stu-id="4c5cc-235">This activity common parameter is also a workflow common parameter.</span></span>

#### <a name="psconnectionuri-systemuri"></a><span data-ttu-id="4c5cc-236">PSConnectionURI \<System.Uri\></span><span class="sxs-lookup"><span data-stu-id="4c5cc-236">PSConnectionURI \<System.Uri\></span></span>

<span data-ttu-id="4c5cc-237">Hiermee geeft u een URI (Uniform Resource Identifier) op waarmee het verbindings eindpunt voor de activiteit op de doel computer wordt gedefinieerd.</span><span class="sxs-lookup"><span data-stu-id="4c5cc-237">Specifies a Uniform Resource Identifier (URI) that defines the connection endpoint for the activity on the target computer.</span></span> <span data-ttu-id="4c5cc-238">De URI moet volledig gekwalificeerd zijn.</span><span class="sxs-lookup"><span data-stu-id="4c5cc-238">The URI must be fully qualified.</span></span> <span data-ttu-id="4c5cc-239">Deze algemene activiteit para meter is ook een algemene werk stroom parameter.</span><span class="sxs-lookup"><span data-stu-id="4c5cc-239">This activity common parameter is also a workflow common parameter.</span></span>

<span data-ttu-id="4c5cc-240">De indeling van deze teken reeks is als volgt:</span><span class="sxs-lookup"><span data-stu-id="4c5cc-240">The format of this string is as follows:</span></span>

```
<Transport>://<ComputerName>:<Port>/<ApplicationName>
```

<span data-ttu-id="4c5cc-241">De standaardwaarde is `http://localhost:5985/WSMAN`.</span><span class="sxs-lookup"><span data-stu-id="4c5cc-241">The default value is `http://localhost:5985/WSMAN`.</span></span>

<span data-ttu-id="4c5cc-242">Als u geen PSConnectionURI opgeeft, kunt u de para meters PSUseSSL, PSComputerName, PSPort en PSApplicationName gebruiken om de PSConnectionURI waarden op te geven.</span><span class="sxs-lookup"><span data-stu-id="4c5cc-242">If you do not specify a PSConnectionURI, you can use the PSUseSSL, PSComputerName, PSPort, and PSApplicationName parameters to specify the PSConnectionURI values.</span></span>

<span data-ttu-id="4c5cc-243">Geldige waarden voor het transport segment van de URI zijn HTTP en HTTPS.</span><span class="sxs-lookup"><span data-stu-id="4c5cc-243">Valid values for the Transport segment of the URI are HTTP and HTTPS.</span></span> <span data-ttu-id="4c5cc-244">Als u een verbindings-URI met een transport segment opgeeft, maar geen poort opgeeft, wordt de sessie gemaakt met standaard poorten: 80 voor HTTP en 443 voor HTTPS.</span><span class="sxs-lookup"><span data-stu-id="4c5cc-244">If you specify a connection URI with a Transport segment, but do not specify a port, the session is created with standards ports: 80 for HTTP and 443 for HTTPS.</span></span> <span data-ttu-id="4c5cc-245">Als u de standaard poorten voor externe communicatie van Windows Power shell wilt gebruiken, geeft u poort 5985 op voor HTTP of 5986 voor HTTPS.</span><span class="sxs-lookup"><span data-stu-id="4c5cc-245">To use the default ports for Windows PowerShell remoting, specify port 5985 for HTTP or 5986 for HTTPS.</span></span>

#### <a name="pscredential-pscredential"></a><span data-ttu-id="4c5cc-246">PSCredential \<PSCredential\></span><span class="sxs-lookup"><span data-stu-id="4c5cc-246">PSCredential \<PSCredential\></span></span>

<span data-ttu-id="4c5cc-247">Hiermee geeft u een gebruikers account op dat gemachtigd is om de activiteit op de doel computer uit te voeren.</span><span class="sxs-lookup"><span data-stu-id="4c5cc-247">Specifies a user account that has permission to run the activity on the target computer.</span></span> <span data-ttu-id="4c5cc-248">Standaard is dit de huidige gebruiker.</span><span class="sxs-lookup"><span data-stu-id="4c5cc-248">The default is the current user.</span></span> <span data-ttu-id="4c5cc-249">Deze para meter is alleen geldig als de para meter PSComputerName is opgenomen in de opdracht.</span><span class="sxs-lookup"><span data-stu-id="4c5cc-249">This parameter is valid only when the PSComputerName parameter is included in the command.</span></span> <span data-ttu-id="4c5cc-250">Deze algemene activiteit para meter is ook een algemene werk stroom parameter.</span><span class="sxs-lookup"><span data-stu-id="4c5cc-250">This activity common parameter is also a workflow common parameter.</span></span>

<span data-ttu-id="4c5cc-251">Typ een gebruikers naam, zoals "gebruiker01" of "Domain01\User01", of voer een variabele in die een PSCredential-object bevat, zoals een item dat door de Get-Credential-cmdlet wordt geretourneerd.</span><span class="sxs-lookup"><span data-stu-id="4c5cc-251">Type a user name, such as "User01" or "Domain01\User01", or enter a variable that contains a PSCredential object, such as one that the Get-Credential cmdlet returns.</span></span> <span data-ttu-id="4c5cc-252">Als u alleen een gebruikers naam opgeeft, wordt u gevraagd een wacht woord op te geven.</span><span class="sxs-lookup"><span data-stu-id="4c5cc-252">If you enter only a user name, you will be prompted for a password.</span></span>

#### <a name="psdebug-psdatacollectiondebugrecord"></a><span data-ttu-id="4c5cc-253">PSDebug \<PSDataCollection[DebugRecord]\></span><span class="sxs-lookup"><span data-stu-id="4c5cc-253">PSDebug \<PSDataCollection[DebugRecord]\></span></span>

<span data-ttu-id="4c5cc-254">Hiermee worden fout opsporingsgegevens van de activiteit toegevoegd aan de opgegeven verzameling record voor fout opsporing, in plaats van het schrijven van fout berichten naar de console of naar de waarde van de eigenschap debug van de werk stroom taak.</span><span class="sxs-lookup"><span data-stu-id="4c5cc-254">Adds debug messages from the activity to the specified debug record collection, instead of writing the debug messages to the console or to the value of the Debug property of the workflow job.</span></span> <span data-ttu-id="4c5cc-255">U kunt fout opsporingsgegevens van meerdere activiteiten toevoegen aan hetzelfde verzamelings object voor fout opsporing.</span><span class="sxs-lookup"><span data-stu-id="4c5cc-255">You can add debug messages from multiple activities to the same debug record collection object.</span></span>

<span data-ttu-id="4c5cc-256">Als u deze algemene activiteit wilt gebruiken, gebruikt u de cmdlet New-Object om een PSDataCollection-object met een type DebugRecord te maken en het object in een variabele op te slaan.</span><span class="sxs-lookup"><span data-stu-id="4c5cc-256">To use this activity common parameter, use the New-Object cmdlet to create a PSDataCollection object with a type of DebugRecord and save the object in a variable.</span></span> <span data-ttu-id="4c5cc-257">Gebruik vervolgens de variabele als de waarde van de para meter PSDebug van een of meer activiteiten, zoals wordt weer gegeven in het volgende voor beeld.</span><span class="sxs-lookup"><span data-stu-id="4c5cc-257">Then, use the variable as the value of the PSDebug parameter of one or more activities, as shown in the following example.</span></span>

```powershell
Workflow Test-Workflow
{
    $debugCollection = New-Object -Type `
    System.Management.Automation.PSDataCollection[System.Management.Automation.DebugRecord]
    InlineScript {\Server01\Share01\Get-AssetData.ps1} -PSDebug $debugCollection -Debug $True
    InlineScript {\Server01\Share01\Set-AssetData.ps1} -PSDebug $debugCollection -Debug $True
    if ($debugCollection -like "Missing") { ...}
}
```

#### <a name="psdisableserialization-boolean"></a><span data-ttu-id="4c5cc-258">PSDisableSerialization \<Boolean\></span><span class="sxs-lookup"><span data-stu-id="4c5cc-258">PSDisableSerialization \<Boolean\></span></span>

<span data-ttu-id="4c5cc-259">Stuurt de activiteit om live-objecten (niet geserialiseerd) naar de werk stroom te retour neren.</span><span class="sxs-lookup"><span data-stu-id="4c5cc-259">Directs the activity to return "live" (not serialized) objects to the workflow.</span></span>
<span data-ttu-id="4c5cc-260">De resulterende objecten hebben methoden, evenals eigenschappen, maar ze kunnen niet worden opgeslagen wanneer een controle punt wordt gemaakt.</span><span class="sxs-lookup"><span data-stu-id="4c5cc-260">The resulting objects have methods, as well as properties, but they cannot be saved when a checkpoint is taken.</span></span>

#### <a name="psdisableserializationpreference-boolean"></a><span data-ttu-id="4c5cc-261">PSDisableSerializationPreference \<Boolean\></span><span class="sxs-lookup"><span data-stu-id="4c5cc-261">PSDisableSerializationPreference \<Boolean\></span></span>

<span data-ttu-id="4c5cc-262">Hiermee wordt het equivalent van de para meter PSDisableSerialization toegepast op de hele werk stroom, niet alleen de activiteit.</span><span class="sxs-lookup"><span data-stu-id="4c5cc-262">Applies the equivalent of the PSDisableSerialization parameter to the entire workflow, not just the activity.</span></span> <span data-ttu-id="4c5cc-263">Het toevoegen van deze para meter wordt over het algemeen niet aanbevolen, omdat een werk stroom die de objecten niet serialiseren, niet kan worden hervat of niet kan worden bewaard.</span><span class="sxs-lookup"><span data-stu-id="4c5cc-263">Adding this parameter is generally not recommended, because a workflow that doesn't serialize its objects cannot be resumed or persisted.</span></span>

<span data-ttu-id="4c5cc-264">Geldige waarden:</span><span class="sxs-lookup"><span data-stu-id="4c5cc-264">Valid values:</span></span>

- <span data-ttu-id="4c5cc-265">Prijs Als u dit weglaat, en u de para meter PSDisableSerialization ook niet hebt toegevoegd aan een activiteit, worden de objecten geserialiseerd.</span><span class="sxs-lookup"><span data-stu-id="4c5cc-265">(Default) If omitted, and you have also not added the PSDisableSerialization parameter to an activity, objects are serialized.</span></span>

- <span data-ttu-id="4c5cc-266">`$True`.</span><span class="sxs-lookup"><span data-stu-id="4c5cc-266">`$True`.</span></span> <span data-ttu-id="4c5cc-267">Stuurt alle activiteiten in een werk stroom om objecten met ' live ' (geen serieel) te retour neren.</span><span class="sxs-lookup"><span data-stu-id="4c5cc-267">Directs all activities within a workflow to return "live" (not serialized) objects.</span></span> <span data-ttu-id="4c5cc-268">De resulterende objecten hebben methoden, evenals eigenschappen, maar ze kunnen niet worden opgeslagen wanneer een controle punt wordt gemaakt.</span><span class="sxs-lookup"><span data-stu-id="4c5cc-268">The resulting objects have methods, as well as properties, but they cannot be saved when a checkpoint is taken.</span></span>
- <span data-ttu-id="4c5cc-269">`$False`.</span><span class="sxs-lookup"><span data-stu-id="4c5cc-269">`$False`.</span></span> <span data-ttu-id="4c5cc-270">Werk stroom objecten worden geserialiseerd.</span><span class="sxs-lookup"><span data-stu-id="4c5cc-270">Workflow objects are serialized.</span></span>

#### <a name="pserror-psdatacollectionerrorrecord"></a><span data-ttu-id="4c5cc-271">PSError \<PSDataCollection[ErrorRecord]\></span><span class="sxs-lookup"><span data-stu-id="4c5cc-271">PSError \<PSDataCollection[ErrorRecord]\></span></span>

<span data-ttu-id="4c5cc-272">Voegt fout berichten van de activiteit toe aan de opgegeven verzameling van fouten records, in plaats van de fout berichten naar de console of naar de waarde van de eigenschap Error van de werk stroom taak te schrijven.</span><span class="sxs-lookup"><span data-stu-id="4c5cc-272">Adds error messages from the activity to the specified error record collection, instead of writing the error messages to the console or to the value of the Error property of the workflow job.</span></span> <span data-ttu-id="4c5cc-273">U kunt fout berichten van meerdere activiteiten toevoegen aan hetzelfde verzamelings object van de fout record.</span><span class="sxs-lookup"><span data-stu-id="4c5cc-273">You can add error messages from multiple activities to the same error record collection object.</span></span>

<span data-ttu-id="4c5cc-274">Als u deze algemene activiteit wilt gebruiken, gebruikt u de `New-Object` cmdlet om een PSDataCollection-object te maken met het type ErrorRecord en slaat u het object op in een variabele.</span><span class="sxs-lookup"><span data-stu-id="4c5cc-274">To use this activity common parameter, use the `New-Object` cmdlet to create a PSDataCollection object with a type of ErrorRecord and save the object in a variable.</span></span> <span data-ttu-id="4c5cc-275">Gebruik vervolgens de variabele als de waarde van de para meter PSError van een of meer activiteiten, zoals wordt weer gegeven in het volgende voor beeld.</span><span class="sxs-lookup"><span data-stu-id="4c5cc-275">Then, use the variable as the value of the PSError parameter of one or more activities, as shown in the following example.</span></span>

```powershell
Workflow Test-Workflow
{
   $typeName = "System.Management.Automation.PSDataCollection"
   $typeName += '[System.Management.Automation.ErrorRecord]'
   $ec = New-Object $typeName
   InlineScript {\Server01\Share01\Get-AssetData.ps1} -PSError $ec
   InlineScript {\Server01\Share01\Set-AssetData.ps1} -PSError $ec
   if ($ec.Count -gt 2)
   {
      # Do Some Work.
   }
}
```

#### <a name="pspersist-boolean"></a><span data-ttu-id="4c5cc-276">PSPersist \<Boolean\></span><span class="sxs-lookup"><span data-stu-id="4c5cc-276">PSPersist \<Boolean\></span></span>

<span data-ttu-id="4c5cc-277">Neemt een controle punt na de activiteit.</span><span class="sxs-lookup"><span data-stu-id="4c5cc-277">Takes a checkpoint after the activity.</span></span> <span data-ttu-id="4c5cc-278">Dit controle punt is een aanvulling op de controle punten die in de werk stroom zijn opgegeven.</span><span class="sxs-lookup"><span data-stu-id="4c5cc-278">This checkpoint is in addition to any checkpoints that are specified in the workflow.</span></span> <span data-ttu-id="4c5cc-279">Deze algemene activiteit para meter is ook een algemene werk stroom parameter.</span><span class="sxs-lookup"><span data-stu-id="4c5cc-279">This activity common parameter is also a workflow common parameter.</span></span>

<span data-ttu-id="4c5cc-280">Een ' controle punt ' of ' persistentie punt ' is een moment opname van de werk stroom status en gegevens die zijn vastgelegd terwijl de werk stroom wordt uitgevoerd en wordt opgeslagen in een opslag voor persistentie op schijf.</span><span class="sxs-lookup"><span data-stu-id="4c5cc-280">A "checkpoint" or "persistence point" is a snapshot of the workflow state and data that is captured while the workflow runs and is saved to a persistence store on disk.</span></span> <span data-ttu-id="4c5cc-281">De Windows Power shell-werk stroom gebruikt de opgeslagen gegevens om een onderbroken of onderbroken werk stroom te hervatten vanaf het laatste persistentie punt, in plaats van de werk stroom opnieuw te starten.</span><span class="sxs-lookup"><span data-stu-id="4c5cc-281">Windows PowerShell Workflow uses the saved data to resume a suspended or interrupted workflow from the last persistence point, rather than to restart the workflow.</span></span>

<span data-ttu-id="4c5cc-282">Geldige waarden:</span><span class="sxs-lookup"><span data-stu-id="4c5cc-282">Valid values:</span></span>

- <span data-ttu-id="4c5cc-283">Prijs Als u deze para meter weglaat, worden er geen controle punten toegevoegd.</span><span class="sxs-lookup"><span data-stu-id="4c5cc-283">(Default) If you omit this parameter, no checkpoints are added.</span></span> <span data-ttu-id="4c5cc-284">Controle punten worden gemaakt op basis van de instellingen voor de werk stroom.</span><span class="sxs-lookup"><span data-stu-id="4c5cc-284">Checkpoints are taken based on the settings for the workflow.</span></span>

- <span data-ttu-id="4c5cc-285">`$True`.</span><span class="sxs-lookup"><span data-stu-id="4c5cc-285">`$True`.</span></span> <span data-ttu-id="4c5cc-286">Neemt een controle punt nadat de activiteit is voltooid.</span><span class="sxs-lookup"><span data-stu-id="4c5cc-286">Takes a checkpoint after the activity completes.</span></span>
  <span data-ttu-id="4c5cc-287">Dit controle punt is een aanvulling op de controle punten die in de werk stroom zijn opgegeven.</span><span class="sxs-lookup"><span data-stu-id="4c5cc-287">This checkpoint is in addition to any checkpoints that are specified in the workflow.</span></span>

- <span data-ttu-id="4c5cc-288">`$False`.</span><span class="sxs-lookup"><span data-stu-id="4c5cc-288">`$False`.</span></span> <span data-ttu-id="4c5cc-289">Er zijn geen controle punten toegevoegd.</span><span class="sxs-lookup"><span data-stu-id="4c5cc-289">No checkpoints are added.</span></span> <span data-ttu-id="4c5cc-290">Controle punten worden alleen genomen wanneer deze zijn opgegeven in de werk stroom.</span><span class="sxs-lookup"><span data-stu-id="4c5cc-290">Checkpoints are taken only when specified in the workflow.</span></span>

#### <a name="psport-int32"></a><span data-ttu-id="4c5cc-291">PSPort \<Int32\></span><span class="sxs-lookup"><span data-stu-id="4c5cc-291">PSPort \<Int32\></span></span>

<span data-ttu-id="4c5cc-292">Hiermee geeft u de netwerk poort op de doel computers.</span><span class="sxs-lookup"><span data-stu-id="4c5cc-292">Specifies the network port on the target computers.</span></span> <span data-ttu-id="4c5cc-293">De standaard poorten zijn 5985 (de WinRM-poort voor HTTP) en 5986 (de WinRM-poort voor HTTPS).</span><span class="sxs-lookup"><span data-stu-id="4c5cc-293">The default ports are 5985 (the WinRM port for HTTP) and 5986 (the WinRM port for HTTPS).</span></span> <span data-ttu-id="4c5cc-294">Deze algemene activiteit para meter is ook een algemene werk stroom parameter.</span><span class="sxs-lookup"><span data-stu-id="4c5cc-294">This activity common parameter is also a workflow common parameter.</span></span>

<span data-ttu-id="4c5cc-295">Gebruik de para meter PSPort alleen als dat nodig is.</span><span class="sxs-lookup"><span data-stu-id="4c5cc-295">Do not use the PSPort parameter unless you must.</span></span> <span data-ttu-id="4c5cc-296">De poort die in de opdracht is ingesteld, is van toepassing op alle computers of sessies waarop de opdracht wordt uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="4c5cc-296">The port set in the command applies to all computers or sessions on which the command runs.</span></span> <span data-ttu-id="4c5cc-297">Een alternatieve poort instelling kan verhinderen dat de opdracht wordt uitgevoerd op alle computers.</span><span class="sxs-lookup"><span data-stu-id="4c5cc-297">An alternate port setting might prevent the command from running on all computers.</span></span> <span data-ttu-id="4c5cc-298">Voordat u een andere poort gebruikt, moet u de WinRM-listener op de externe computer configureren om op die poort te Luis teren.</span><span class="sxs-lookup"><span data-stu-id="4c5cc-298">Before using an alternate port, you must configure the WinRM listener on the remote computer to listen at that port.</span></span>

#### <a name="psprogress-psdatacollectionprogressrecord"></a><span data-ttu-id="4c5cc-299">PSProgress \<PSDataCollection[ProgressRecord]\></span><span class="sxs-lookup"><span data-stu-id="4c5cc-299">PSProgress \<PSDataCollection[ProgressRecord]\></span></span>

<span data-ttu-id="4c5cc-300">Hiermee worden voortgangs berichten van de activiteit toegevoegd aan de opgegeven verzameling van voortgangs records, in plaats van de voortgangs berichten naar de console of naar de waarde van de eigenschap Progress van de werk stroom taak te schrijven.</span><span class="sxs-lookup"><span data-stu-id="4c5cc-300">Adds progress messages from the activity to the specified progress record collection, instead of writing the progress messages to the console or to the value of the Progress property of the workflow job.</span></span> <span data-ttu-id="4c5cc-301">U kunt voortgangs berichten uit meerdere activiteiten toevoegen aan hetzelfde verzamelings object voor voortgangs records.</span><span class="sxs-lookup"><span data-stu-id="4c5cc-301">You can add progress messages from multiple activities to the same progress record collection object.</span></span>

#### <a name="psprogressmessage-string"></a><span data-ttu-id="4c5cc-302">PSProgressMessage \<String\></span><span class="sxs-lookup"><span data-stu-id="4c5cc-302">PSProgressMessage \<String\></span></span>

<span data-ttu-id="4c5cc-303">Hiermee geeft u een beschrijvende beschrijving van de activiteit.</span><span class="sxs-lookup"><span data-stu-id="4c5cc-303">Specifies a friendly description of the activity.</span></span> <span data-ttu-id="4c5cc-304">De waarde PSProgressMessage wordt weer gegeven in de voortgangs balk terwijl de werk stroom wordt uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="4c5cc-304">The PSProgressMessage value appears in the progress bar while the workflow runs.</span></span> <span data-ttu-id="4c5cc-305">Wanneer de DisplayName ook is opgenomen in de opdracht, wordt de inhoud van de voortgangs balk weer gegeven in \<DisplayName\> : \<PSProgressMessage\> Format.</span><span class="sxs-lookup"><span data-stu-id="4c5cc-305">When the DisplayName is also included in the command, the progress bar content appears in \<DisplayName\>:\<PSProgressMessage\> format.</span></span>

<span data-ttu-id="4c5cc-306">Deze para meter is met name handig voor het identificeren van activiteiten in een ForEach-parallel-script blok.</span><span class="sxs-lookup"><span data-stu-id="4c5cc-306">This parameter is particularly useful for identifying activities in a ForEach -Parallel script block.</span></span> <span data-ttu-id="4c5cc-307">Zonder dit bericht worden activiteiten in alle parallelle vertakkingen aangeduid met dezelfde naam.</span><span class="sxs-lookup"><span data-stu-id="4c5cc-307">Without this message, activities in all parallel branches are identified by the same name.</span></span>

#### <a name="psremotingbehavior-remotingbehavior"></a><span data-ttu-id="4c5cc-308">PSRemotingBehavior \<RemotingBehavior\></span><span class="sxs-lookup"><span data-stu-id="4c5cc-308">PSRemotingBehavior \<RemotingBehavior\></span></span>

<span data-ttu-id="4c5cc-309">Hiermee geeft u op hoe externe toegang wordt beheerd wanneer de activiteit wordt uitgevoerd op de doel computers.</span><span class="sxs-lookup"><span data-stu-id="4c5cc-309">Specifies how remoting is managed when the activity is run on target computers.</span></span>
<span data-ttu-id="4c5cc-310">Power shell is de standaard instelling.</span><span class="sxs-lookup"><span data-stu-id="4c5cc-310">PowerShell is the default.</span></span>

<span data-ttu-id="4c5cc-311">Geldige waarden zijn:</span><span class="sxs-lookup"><span data-stu-id="4c5cc-311">Valid values are:</span></span>

- <span data-ttu-id="4c5cc-312">Geen: de activiteit wordt niet uitgevoerd op externe computers.</span><span class="sxs-lookup"><span data-stu-id="4c5cc-312">None: The activity is not run on remote computers.</span></span>

- <span data-ttu-id="4c5cc-313">Power shell: externe toegang van Windows Power shell wordt gebruikt om de activiteit uit te voeren op doel computers.</span><span class="sxs-lookup"><span data-stu-id="4c5cc-313">PowerShell: Windows PowerShell remoting is used to run the activity on target computers.</span></span>

- <span data-ttu-id="4c5cc-314">Aangepast: de activiteit ondersteunt een eigen type externe communicatie.</span><span class="sxs-lookup"><span data-stu-id="4c5cc-314">Custom: The activity supports its own type of remoting.</span></span> <span data-ttu-id="4c5cc-315">Deze waarde is geldig wanneer de cmdlet die wordt geïmplementeerd als activiteit, de waarde van het kenmerk RemotingCapability instelt op SupportedByCommand en de opdracht de para meter ComputerName bevat.</span><span class="sxs-lookup"><span data-stu-id="4c5cc-315">This value is valid when the cmdlet that is being implemented as an activity sets the value of the RemotingCapability attribute to SupportedByCommand and the command includes the ComputerName parameter.</span></span>

#### <a name="psrequiredmodules-string"></a><span data-ttu-id="4c5cc-316">PSRequiredModules \<String[]\></span><span class="sxs-lookup"><span data-stu-id="4c5cc-316">PSRequiredModules \<String[]\></span></span>

<span data-ttu-id="4c5cc-317">Hiermee worden de opgegeven modules geïmporteerd voordat de opdracht wordt uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="4c5cc-317">Imports the specified modules before running the command.</span></span> <span data-ttu-id="4c5cc-318">Voer de module namen in.</span><span class="sxs-lookup"><span data-stu-id="4c5cc-318">Enter the module names.</span></span> <span data-ttu-id="4c5cc-319">De modules moeten worden geïnstalleerd op de doel computer.</span><span class="sxs-lookup"><span data-stu-id="4c5cc-319">The modules must be installed on the target computer.</span></span>

<span data-ttu-id="4c5cc-320">Modules die zijn geïnstalleerd in een pad dat is opgegeven in de omgevings variabele PSModulePath, worden automatisch geïmporteerd bij het eerste gebruik van een opdracht in de module.</span><span class="sxs-lookup"><span data-stu-id="4c5cc-320">Modules that are installed in a path specified in the PSModulePath environment variable are automatically imported on first use of any command in the module.</span></span>
<span data-ttu-id="4c5cc-321">Gebruik deze para meter om modules te importeren die zich niet in een PSModulePath-locatie bevinden.</span><span class="sxs-lookup"><span data-stu-id="4c5cc-321">Use this parameter to import modules that are not in a PSModulePath location.</span></span>

<span data-ttu-id="4c5cc-322">Omdat elke activiteit in een werk stroom wordt uitgevoerd in een eigen sessie, wordt met een Import-Module-opdracht een module alleen geïmporteerd in de sessie waarin deze wordt uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="4c5cc-322">Because each activity in a workflow runs in its own session, an Import-Module command imports a module only into the session in which it runs.</span></span> <span data-ttu-id="4c5cc-323">De module wordt niet geïmporteerd in sessies waarin andere activiteiten worden uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="4c5cc-323">It does not import the module into sessions in which other activities run.</span></span>

#### <a name="pssessionoption-pssessionoption"></a><span data-ttu-id="4c5cc-324">PSSessionOption \<PSSessionOption\></span><span class="sxs-lookup"><span data-stu-id="4c5cc-324">PSSessionOption \<PSSessionOption\></span></span>

<span data-ttu-id="4c5cc-325">Hiermee stelt u geavanceerde opties in voor de sessies op de doel computers.</span><span class="sxs-lookup"><span data-stu-id="4c5cc-325">Sets advanced options for the sessions to the target computers.</span></span> <span data-ttu-id="4c5cc-326">Voer een PSSessionOption-object in, zoals een, dat u maakt met behulp van de cmdlet New-PSSessionOption.</span><span class="sxs-lookup"><span data-stu-id="4c5cc-326">Enter a PSSessionOption object, such as one that you create by using the New-PSSessionOption cmdlet.</span></span> <span data-ttu-id="4c5cc-327">Deze algemene activiteit para meter is ook een algemene werk stroom parameter.</span><span class="sxs-lookup"><span data-stu-id="4c5cc-327">This activity common parameter is also a workflow common parameter.</span></span>

<span data-ttu-id="4c5cc-328">De standaard waarden voor de sessie opties worden bepaald door de waarde van de `$PSSessionOption` Voorkeurs variabele, als deze is ingesteld.</span><span class="sxs-lookup"><span data-stu-id="4c5cc-328">The default values for the session options are determined by the value of the `$PSSessionOption` preference variable, if it is set.</span></span> <span data-ttu-id="4c5cc-329">Anders gebruikt de sessie de waarden die zijn opgegeven in de sessie configuratie.</span><span class="sxs-lookup"><span data-stu-id="4c5cc-329">Otherwise, the session uses the values specified in the session configuration.</span></span>

<span data-ttu-id="4c5cc-330">Zie het Help-onderwerp voor de New-PSSessionOption [-cmdlet New-PSSessionOption](xref:Microsoft.PowerShell.Core.New-PSSessionOption)voor een beschrijving van de sessie opties, met inbegrip van de standaard waarden.</span><span class="sxs-lookup"><span data-stu-id="4c5cc-330">For a description of the session options, including the default values, see the help topic for the New-PSSessionOption cmdlet [New-PSSessionOption](xref:Microsoft.PowerShell.Core.New-PSSessionOption).</span></span>

<span data-ttu-id="4c5cc-331">Zie [about_Preference_Variables](../../Microsoft.PowerShell.Core/About/about_Preference_Variables.md)voor meer informatie over de $PSSessionOption voorkeurs variabele.</span><span class="sxs-lookup"><span data-stu-id="4c5cc-331">For more information about the $PSSessionOption preference variable, see [about_Preference_Variables](../../Microsoft.PowerShell.Core/About/about_Preference_Variables.md).</span></span>

#### <a name="psusessl-boolean"></a><span data-ttu-id="4c5cc-332">PSUseSSL \<Boolean\></span><span class="sxs-lookup"><span data-stu-id="4c5cc-332">PSUseSSL \<Boolean\></span></span>

<span data-ttu-id="4c5cc-333">Een waarde van $True maakt gebruik van het Secure Sockets Layer (SSL)-protocol om verbinding te maken met de doel computer.</span><span class="sxs-lookup"><span data-stu-id="4c5cc-333">A value of $True uses the Secure Sockets Layer (SSL) protocol to establish a connection to the target computer.</span></span> <span data-ttu-id="4c5cc-334">Standaard wordt SSL niet gebruikt.</span><span class="sxs-lookup"><span data-stu-id="4c5cc-334">By default, SSL is not used.</span></span> <span data-ttu-id="4c5cc-335">Een waarde van $False heeft geen effect.</span><span class="sxs-lookup"><span data-stu-id="4c5cc-335">A value of $False has no effect.</span></span> <span data-ttu-id="4c5cc-336">Deze algemene activiteit para meter is ook een algemene werk stroom parameter.</span><span class="sxs-lookup"><span data-stu-id="4c5cc-336">This activity common parameter is also a workflow common parameter.</span></span>

<span data-ttu-id="4c5cc-337">WS-Management versleutelt alle Windows Power shell-inhoud die via het netwerk wordt verzonden.</span><span class="sxs-lookup"><span data-stu-id="4c5cc-337">WS-Management encrypts all Windows PowerShell content transmitted over the network.</span></span> <span data-ttu-id="4c5cc-338">UseSSL is een extra bescherming waarmee de gegevens worden verzonden via een HTTPS in plaats van HTTP.</span><span class="sxs-lookup"><span data-stu-id="4c5cc-338">UseSSL is an additional protection that sends the data across an HTTPS, instead of HTTP.</span></span> <span data-ttu-id="4c5cc-339">Als u deze para meter gebruikt maar SSL is niet beschikbaar op de poort die wordt gebruikt voor de opdracht, mislukt de opdracht.</span><span class="sxs-lookup"><span data-stu-id="4c5cc-339">If you use this parameter, but SSL is not available on the port used for the command, the command fails.</span></span>

#### <a name="psverbose-psdatacollectionverboserecord"></a><span data-ttu-id="4c5cc-340">PSVerbose \<PSDataCollection[VerboseRecord]\></span><span class="sxs-lookup"><span data-stu-id="4c5cc-340">PSVerbose \<PSDataCollection[VerboseRecord]\></span></span>

<span data-ttu-id="4c5cc-341">Hiermee worden uitgebreide berichten van de activiteit toegevoegd aan de opgegeven verzameling uitgebreide records, in plaats van de uitgebreide berichten naar de console of naar de waarde van de eigenschap uitgebreid van de werk stroom taak te schrijven.</span><span class="sxs-lookup"><span data-stu-id="4c5cc-341">Adds verbose messages from the activity to the specified verbose record collection, instead of writing the verbose messages to the console or to the value of the Verbose property of the workflow job.</span></span> <span data-ttu-id="4c5cc-342">U kunt uitgebreide berichten van meerdere activiteiten toevoegen aan hetzelfde verzamelings object voor uitgebreide records.</span><span class="sxs-lookup"><span data-stu-id="4c5cc-342">You can add verbose messages from multiple activities to the same verbose record collection object.</span></span>

#### <a name="pswarning-psdatacollectionwarningrecord"></a><span data-ttu-id="4c5cc-343">PSWarning \<PSDataCollection[WarningRecord]\></span><span class="sxs-lookup"><span data-stu-id="4c5cc-343">PSWarning \<PSDataCollection[WarningRecord]\></span></span>

<span data-ttu-id="4c5cc-344">Hiermee worden waarschuwings berichten van de activiteit toegevoegd aan de opgegeven verzameling waarschuwings records, in plaats van de waarschuwings berichten naar de console of naar de waarde van de eigenschap Warning van de werk stroom taak te schrijven.</span><span class="sxs-lookup"><span data-stu-id="4c5cc-344">Adds warning messages from the activity to the specified warning record collection, instead of writing the warning messages to the console or to the value of the Warning property of the workflow job.</span></span> <span data-ttu-id="4c5cc-345">U kunt waarschuwings berichten van meerdere activiteiten toevoegen aan hetzelfde verzamelings object voor waarschuwings records.</span><span class="sxs-lookup"><span data-stu-id="4c5cc-345">You can add warning messages from multiple activities to the same warning record collection object.</span></span>

#### <a name="result"></a><span data-ttu-id="4c5cc-346">Resultaat</span><span class="sxs-lookup"><span data-stu-id="4c5cc-346">Result</span></span>

<span data-ttu-id="4c5cc-347">Deze para meter is alleen geldig in XAML-werk stromen.</span><span class="sxs-lookup"><span data-stu-id="4c5cc-347">This parameter is valid only in XAML workflows.</span></span>

#### <a name="usedefaultinput-boolean"></a><span data-ttu-id="4c5cc-348">UseDefaultInput \<Boolean\></span><span class="sxs-lookup"><span data-stu-id="4c5cc-348">UseDefaultInput \<Boolean\></span></span>

<span data-ttu-id="4c5cc-349">Hiermee wordt alle invoer van de werk stroom geaccepteerd als invoer voor de activiteit op waarde.</span><span class="sxs-lookup"><span data-stu-id="4c5cc-349">Accepts all workflow input as input to the activity by value.</span></span>

<span data-ttu-id="4c5cc-350">De Get-Process-activiteit in de volgende voorbeeld werk stroom maakt bijvoorbeeld gebruik van de algemene para meter UseDefaultInput voor het ophalen van invoer die wordt door gegeven aan de werk stroom.</span><span class="sxs-lookup"><span data-stu-id="4c5cc-350">For example, the Get-Process activity in the following sample workflow uses the UseDefaultInput activity common parameter to get input that is passed to the workflow.</span></span> <span data-ttu-id="4c5cc-351">Wanneer u de werk stroom met invoer uitvoert, wordt die invoer gebruikt door de activiteit.</span><span class="sxs-lookup"><span data-stu-id="4c5cc-351">When you run the workflow with input, that input is used by the activity.</span></span>

```powershell
workflow Test-Workflow
{
    Get-Service -UseDefaultInput $True
}

PS C:> Test-Workflow -InputObject WinRm
```

```output
Status   Name        DisplayName                            PSComputerName
------   ----        -----------                            --------------
Running  winrm       Windows Remote Management (WS-Manag... localhost
```

#### <a name="verbose-switchparameter"></a><span data-ttu-id="4c5cc-352">Uitgebreide \<SwitchParameter\></span><span class="sxs-lookup"><span data-stu-id="4c5cc-352">Verbose \<SwitchParameter\></span></span>

<span data-ttu-id="4c5cc-353">Geeft gedetailleerde informatie weer over de bewerking die door de opdracht wordt uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="4c5cc-353">Displays detailed information about the operation performed by the command.</span></span>
<span data-ttu-id="4c5cc-354">Deze informatie komt overeen met de informatie in een tracering of in een transactie logboek.</span><span class="sxs-lookup"><span data-stu-id="4c5cc-354">This information resembles the information in a trace or in a transaction log.</span></span>
<span data-ttu-id="4c5cc-355">De para meter uitgebreid overschrijft de waarde van de variabele $VerbosePreference voor de huidige opdracht.</span><span class="sxs-lookup"><span data-stu-id="4c5cc-355">The Verbose parameter overrides the value of the $VerbosePreference variable for the current command.</span></span> <span data-ttu-id="4c5cc-356">Deze para meter werkt alleen als de opdracht een uitgebreid bericht genereert.</span><span class="sxs-lookup"><span data-stu-id="4c5cc-356">This parameter works only when the command generates a verbose message.</span></span> <span data-ttu-id="4c5cc-357">Deze para meter is ook een gemeen schappelijke Windows Power shell-para meter.</span><span class="sxs-lookup"><span data-stu-id="4c5cc-357">This parameter is also a Windows PowerShell common parameter.</span></span>

#### <a name="warningaction-actionpreference"></a><span data-ttu-id="4c5cc-358">WarningAction \<ActionPreference\></span><span class="sxs-lookup"><span data-stu-id="4c5cc-358">WarningAction \<ActionPreference\></span></span>

<span data-ttu-id="4c5cc-359">Hiermee wordt bepaald hoe de activiteit reageert op een waarschuwing.</span><span class="sxs-lookup"><span data-stu-id="4c5cc-359">Determines how the activity responds to a warning.</span></span> <span data-ttu-id="4c5cc-360">' Door gaan ' is de standaard waarde.</span><span class="sxs-lookup"><span data-stu-id="4c5cc-360">"Continue" is the default value.</span></span> <span data-ttu-id="4c5cc-361">De para meter WarningAction overschrijft de waarde van de variabele $WarningPreference voor de huidige opdracht.</span><span class="sxs-lookup"><span data-stu-id="4c5cc-361">The WarningAction parameter overrides the value of the $WarningPreference variable for the current command.</span></span> <span data-ttu-id="4c5cc-362">Deze para meter werkt alleen als er een waarschuwings bericht wordt gegenereerd door de opdracht.</span><span class="sxs-lookup"><span data-stu-id="4c5cc-362">This parameter works only when the command generates a warning message.</span></span> <span data-ttu-id="4c5cc-363">Deze para meter is ook een gemeen schappelijke Windows Power shell-para meter.</span><span class="sxs-lookup"><span data-stu-id="4c5cc-363">This parameter is also a Windows PowerShell common parameter.</span></span>

<span data-ttu-id="4c5cc-364">Geldige waarden:</span><span class="sxs-lookup"><span data-stu-id="4c5cc-364">Valid Values:</span></span>

- <span data-ttu-id="4c5cc-365">SilentlyContinue.</span><span class="sxs-lookup"><span data-stu-id="4c5cc-365">SilentlyContinue.</span></span> <span data-ttu-id="4c5cc-366">Onderdrukt het waarschuwings bericht en gaat door met het uitvoeren van de opdracht.</span><span class="sxs-lookup"><span data-stu-id="4c5cc-366">Suppresses the warning message and continues executing the command.</span></span>

- <span data-ttu-id="4c5cc-367">Doen.</span><span class="sxs-lookup"><span data-stu-id="4c5cc-367">Continue.</span></span> <span data-ttu-id="4c5cc-368">Geeft het waarschuwings bericht weer en voert de opdracht verder uit.</span><span class="sxs-lookup"><span data-stu-id="4c5cc-368">Displays the warning message and continues executing the command.</span></span>
  <span data-ttu-id="4c5cc-369">' Door gaan ' is de standaard waarde.</span><span class="sxs-lookup"><span data-stu-id="4c5cc-369">"Continue" is the default value.</span></span>

- <span data-ttu-id="4c5cc-370">Inquire.</span><span class="sxs-lookup"><span data-stu-id="4c5cc-370">Inquire.</span></span> <span data-ttu-id="4c5cc-371">Hiermee wordt het waarschuwings bericht weer gegeven en wordt u gevraagd om bevestiging voordat u doorgaat met de uitvoering.</span><span class="sxs-lookup"><span data-stu-id="4c5cc-371">Displays the warning message and prompts you for confirmation before continuing execution.</span></span> <span data-ttu-id="4c5cc-372">Deze waarde wordt zelden gebruikt.</span><span class="sxs-lookup"><span data-stu-id="4c5cc-372">This value is rarely used.</span></span>

- <span data-ttu-id="4c5cc-373">Stoppen.</span><span class="sxs-lookup"><span data-stu-id="4c5cc-373">Stop.</span></span> <span data-ttu-id="4c5cc-374">Geeft het waarschuwings bericht weer en stopt met het uitvoeren van de opdracht.</span><span class="sxs-lookup"><span data-stu-id="4c5cc-374">Displays the warning message and stops executing the command.</span></span>

> [!NOTE]
> <span data-ttu-id="4c5cc-375">De para meter WarningAction overschrijft de waarde van de $WarningAction voorkeurs variabele niet wanneer de para meter wordt gebruikt in een opdracht voor het uitvoeren van een script of functie.</span><span class="sxs-lookup"><span data-stu-id="4c5cc-375">The WarningAction parameter does not override the value of the $WarningAction preference variable when the parameter is used in a command to run a script or function.</span></span>

### <a name="examples"></a><span data-ttu-id="4c5cc-376">VOORBEELDEN</span><span class="sxs-lookup"><span data-stu-id="4c5cc-376">EXAMPLES</span></span>

<span data-ttu-id="4c5cc-377">De algemene para meters voor de activiteit zijn erg nuttig.</span><span class="sxs-lookup"><span data-stu-id="4c5cc-377">The activity common parameters are extremely useful.</span></span> <span data-ttu-id="4c5cc-378">U kunt bijvoorbeeld de para meter PSComputerName gebruiken om bepaalde activiteiten uit te voeren op slechts een subset van de doel computers.</span><span class="sxs-lookup"><span data-stu-id="4c5cc-378">For example, you can use the PSComputerName parameter to run particular activities on only a subset of the target computers.</span></span>

<span data-ttu-id="4c5cc-379">U kunt ook de para meters PSConnectionRetryCount en PSConnectionRetryIntervalSec gebruiken om de waarden voor nieuwe pogingen voor bepaalde activiteiten aan te passen.</span><span class="sxs-lookup"><span data-stu-id="4c5cc-379">Or, you might use the PSConnectionRetryCount and PSConnectionRetryIntervalSec parameters to adjust the retry values for particular activities.</span></span>

<span data-ttu-id="4c5cc-380">In het volgende voor beeld ziet u hoe u de algemene para meters voor de activiteit PSComputerName gebruikt om een Get-EventLog-activiteit alleen uit te voeren op computers die een bepaald domein.</span><span class="sxs-lookup"><span data-stu-id="4c5cc-380">The following example shows how to use the PSComputerName activity common parameters to run a Get-EventLog activity only on computers it a particular domain.</span></span>

```powershell
Workflow Test-Workflow
{
    $UserDomain = Get-Content -Path '.\UserComputers.txt'
    $Log = (Get-EventLog -LogName "Windows PowerShell" `
      -PSComputerName $UserDomain)

    if ($Log)
    {
        # Do Work Here.
    }
}
```

<!--
# KEYWORDS
[about_Activity_Common_Parameters](about_Activity_Common_Parameters.md)
[about_Activity_Parameters](about_Activity_Parameters.md)
[about_ActivityParameters]()about_ActivityParameters.md) -->

## <a name="see-also"></a><span data-ttu-id="4c5cc-381">ZIE OOK</span><span class="sxs-lookup"><span data-stu-id="4c5cc-381">SEE ALSO</span></span>

<span data-ttu-id="4c5cc-382">[about_Workflows](about_workflows.md) 
 [about_WorkflowCommonParameters](about_WorkflowCommonParameters.md)</span><span class="sxs-lookup"><span data-stu-id="4c5cc-382">[about_Workflows](about_workflows.md)
[about_WorkflowCommonParameters](about_WorkflowCommonParameters.md)</span></span>
