---
ms.date: 06/12/2017
keywords: wmf,powershell,installeren
title: Bekende problemen en beperkingen voor desired state Configuration (DSC)
ms.openlocfilehash: a76c5bb336804c5b384e6b6ba6a705c6049ef7fb
ms.sourcegitcommit: 2aec310ad0c0b048400cb56f6fa64c1e554c812a
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 05/23/2020
ms.locfileid: "83810202"
---
# <a name="desired-state-configuration-dsc-known-issues-and-limitations"></a><span data-ttu-id="3efef-103">Bekende problemen en beperkingen voor desired state Configuration (DSC)</span><span class="sxs-lookup"><span data-stu-id="3efef-103">Desired State Configuration (DSC) Known Issues and Limitations</span></span>

## <a name="breaking-change-certificates-used-to-encryptdecrypt-passwords-in-dsc-configurations-may-not-work-after-installing-wmf-50-rtm"></a><span data-ttu-id="3efef-104">Belang rijke wijziging: certificaten die worden gebruikt voor het versleutelen/ontsleutelen van wacht woorden in DSC-configuraties, werken mogelijk niet na installatie van WMF 5,0</span><span class="sxs-lookup"><span data-stu-id="3efef-104">Breaking Change: Certificates used to encrypt/decrypt passwords in DSC configurations may not work after installing WMF 5.0 RTM</span></span>

<span data-ttu-id="3efef-105">In de Preview-versies van WMF 4,0 en WMF 5,0 staat DSC niet toe dat wacht woorden in de configuratie langer zijn dan 121 tekens.</span><span class="sxs-lookup"><span data-stu-id="3efef-105">In WMF 4.0 and WMF 5.0 Preview releases, DSC would not allow passwords in the configuration to be of length more than 121 characters.</span></span> <span data-ttu-id="3efef-106">DSC afdwingt het gebruik van korte wacht woorden, zelfs als de lengte en het sterke wacht woord gewenst zijn.</span><span class="sxs-lookup"><span data-stu-id="3efef-106">DSC was forcing to use short passwords even if lengthy and strong password was desired.</span></span> <span data-ttu-id="3efef-107">Met deze breuk wijziging kunnen wacht woorden een wille keurige lengte hebben in de DSC-configuratie.</span><span class="sxs-lookup"><span data-stu-id="3efef-107">This breaking change allows passwords to be of arbitrary length in the DSC configuration.</span></span>

<span data-ttu-id="3efef-108">**Oplossing:** Maak het certificaat opnieuw met gegevens codering of sleutel codering sleutel gebruik en document versleuteling uitgebreid sleutel gebruik (1.3.6.1.4.1.311.80.1).</span><span class="sxs-lookup"><span data-stu-id="3efef-108">**Resolution:** Re-create the certificate with Data Encipherment or Key Encipherment Key usage, and Document Encryption Enhanced Key usage (1.3.6.1.4.1.311.80.1).</span></span> <span data-ttu-id="3efef-109">Zie [Protect-CmsMessage](/powershell/module/Microsoft.PowerShell.Security/Protect-CmsMessage)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="3efef-109">For more information, see [Protect-CmsMessage](/powershell/module/Microsoft.PowerShell.Security/Protect-CmsMessage).</span></span>

## <a name="dsc-cmdlets-may-fail-after-installing-wmf-50-rtm"></a><span data-ttu-id="3efef-110">DSC-cmdlets kunnen mislukken na de installatie van WMF 5,0 RTM</span><span class="sxs-lookup"><span data-stu-id="3efef-110">DSC cmdlets may fail after installing WMF 5.0 RTM</span></span>

<span data-ttu-id="3efef-111">`Start-DscConfiguration`en andere DSC-cmdlets kunnen mislukken na de installatie van WMF 5,0 RTM met de volgende fout:</span><span class="sxs-lookup"><span data-stu-id="3efef-111">`Start-DscConfiguration` and other DSC cmdlets may fail after installing WMF 5.0 RTM with the following error:</span></span>

```Output
LCM failed to retrieve the property PendingJobStep from the object of class dscInternalCache .
+ CategoryInfo : ObjectNotFound: (root/Microsoft/...gurationManager:String) [], CimException
+ FullyQualifiedErrorId : MI RESULT 6
+ PSComputerName : localhost
```

<span data-ttu-id="3efef-112">**Oplossing:** Verwijder DSCEngineCache. MOF door de volgende opdracht uit te voeren in een Power shell-sessie met verhoogde bevoegdheden (als administrator uitvoeren):</span><span class="sxs-lookup"><span data-stu-id="3efef-112">**Resolution:** Delete DSCEngineCache.mof by running the following command in an elevated PowerShell session (Run as Administrator):</span></span>

```powershell
Remove-Item -Path $env:SystemRoot\system32\Configuration\DSCEngineCache.mof
```

## <a name="dsc-cmdlets-may-not-work-if-wmf-50-rtm-is-installed-on-top-of-wmf-50-production-preview"></a><span data-ttu-id="3efef-113">DSC-cmdlets werken mogelijk niet als WMF 5,0 RTM boven op de WMF-5,0-productie preview is geïnstalleerd</span><span class="sxs-lookup"><span data-stu-id="3efef-113">DSC cmdlets may not work if WMF 5.0 RTM is installed on top of WMF 5.0 Production Preview</span></span>

<span data-ttu-id="3efef-114">**Oplossing:** Voer de volgende opdracht uit in een Power shell-sessie met verhoogde bevoegdheden (als administrator uitvoeren):</span><span class="sxs-lookup"><span data-stu-id="3efef-114">**Resolution:** Run the following command in an elevated PowerShell session (run as administrator):</span></span>

```powershell
mofcomp $env:windir\system32\wbem\DscCoreConfProv.mof
```

## <a name="lcm-can-go-into-an-unstable-state-while-using-get-dscconfiguration-in-debugmode"></a><span data-ttu-id="3efef-115">LCM kan de status Insta Biel maken terwijl Get-DscConfiguration in DebugMode wordt gebruikt</span><span class="sxs-lookup"><span data-stu-id="3efef-115">LCM can go into an unstable state while using Get-DscConfiguration in DebugMode</span></span>

<span data-ttu-id="3efef-116">Als LCM zich in DebugMode bevindt, drukt u op CTRL + C om te stoppen met het verwerken van `Get-DscConfiguration` een instabiele status, zodat de meeste DSC-cmdlets niet werken.</span><span class="sxs-lookup"><span data-stu-id="3efef-116">If LCM is in DebugMode, pressing CTRL+C to stop the processing of `Get-DscConfiguration` can cause LCM to go into an unstable state such that majority of DSC cmdlets won’t work.</span></span>

<span data-ttu-id="3efef-117">**Oplossing:** Druk niet op CTRL + C tijdens de cmdlet voor fout opsporing `Get-DscConfiguration` .</span><span class="sxs-lookup"><span data-stu-id="3efef-117">**Resolution:** Don’t press CTRL+C while debugging `Get-DscConfiguration` cmdlet.</span></span>

## <a name="stop-dscconfiguration-may-not-respond-in-debugmode"></a><span data-ttu-id="3efef-118">Stop-DscConfiguration reageert mogelijk niet in DebugMode</span><span class="sxs-lookup"><span data-stu-id="3efef-118">Stop-DscConfiguration may not respond in DebugMode</span></span>

<span data-ttu-id="3efef-119">Als LCM zich in DebugMode bevindt, reageert `Stop-DscConfiguration` niet tijdens het stoppen van een bewerking die is gestart door`Get-DscConfiguration`</span><span class="sxs-lookup"><span data-stu-id="3efef-119">If LCM is in DebugMode, `Stop-DscConfiguration` may not respond while trying to stop an operation started by `Get-DscConfiguration`</span></span>

<span data-ttu-id="3efef-120">**Oplossing:** Voltooi de fout opsporing van de bewerking die is gestart door `Get-DscConfiguration` zoals beschreven in [DSC-resources voor fout opsporing](/powershell/scripting/dsc/troubleshooting/debugResource).</span><span class="sxs-lookup"><span data-stu-id="3efef-120">**Resolution:** Finish the debugging of the operation started by `Get-DscConfiguration` as outlined in [Debugging DSC resources](/powershell/scripting/dsc/troubleshooting/debugResource).</span></span>

## <a name="no-verbose-error-messages-are-shown-in-debugmode"></a><span data-ttu-id="3efef-121">Er worden geen uitgebreide fout berichten weer gegeven in DebugMode</span><span class="sxs-lookup"><span data-stu-id="3efef-121">No Verbose Error Messages are shown in DebugMode</span></span>

<span data-ttu-id="3efef-122">Als LCM zich in **DebugMode**bevindt, worden er geen uitgebreide fout berichten weer gegeven uit DSC-resources.</span><span class="sxs-lookup"><span data-stu-id="3efef-122">If LCM is in **DebugMode**, no verbose error messages are displayed from DSC Resources.</span></span>

<span data-ttu-id="3efef-123">**Oplossing:** **DebugMode** uitschakelen om uitgebreide berichten van de resource weer te geven</span><span class="sxs-lookup"><span data-stu-id="3efef-123">**Resolution:** Disable **DebugMode** to see verbose messages from the resource</span></span>

## <a name="invoke-dscresource-operations-cannot-be-retrieved-by-get-dscconfigurationstatus-cmdlet"></a><span data-ttu-id="3efef-124">Invoke-Dscresource bieden-bewerkingen kunnen niet worden opgehaald met de cmdlet Get-DscConfigurationStatus</span><span class="sxs-lookup"><span data-stu-id="3efef-124">Invoke-DscResource operations cannot be retrieved by Get-DscConfigurationStatus cmdlet</span></span>

<span data-ttu-id="3efef-125">Nadat `Invoke-DscResource` de cmdlet is gebruikt om alle methoden van een resource rechtstreeks aan te roepen, kunnen de records van een dergelijke bewerking niet worden opgehaald via `Get-DscConfigurationStatus` .</span><span class="sxs-lookup"><span data-stu-id="3efef-125">After using `Invoke-DscResource` cmdlet to directly invoke any resource’s methods, the records of such operation cannot be retrieved through `Get-DscConfigurationStatus`.</span></span>

<span data-ttu-id="3efef-126">**Oplossing:** Geen.</span><span class="sxs-lookup"><span data-stu-id="3efef-126">**Resolution:** None.</span></span>

## <a name="get-dscconfigurationstatus-returns-pull-cycle-operations-as-type-consistency"></a><span data-ttu-id="3efef-127">Get-DscConfigurationStatus retourneert pull-cyclus bewerkingen als type **consistentie**</span><span class="sxs-lookup"><span data-stu-id="3efef-127">Get-DscConfigurationStatus returns pull cycle operations as type **Consistency**</span></span>

<span data-ttu-id="3efef-128">Wanneer een knoop punt is ingesteld op PULL-vernieuwings modus, voor elke uitgevoerde pull-bewerking `Get-DscConfigurationStatus` rapporteert de cmdlet het bewerkings type als **consistentie** in plaats van de *eerste*</span><span class="sxs-lookup"><span data-stu-id="3efef-128">When a node is set to PULL refresh mode, for each pull operation performed, `Get-DscConfigurationStatus` cmdlet reports the operation type as **Consistency** instead of *Initial*</span></span>

<span data-ttu-id="3efef-129">**Oplossing:** Geen.</span><span class="sxs-lookup"><span data-stu-id="3efef-129">**Resolution:** None.</span></span>

## <a name="invoke-dscresource-cmdlet-does-not-return-message-in-the-order-they-were-produced"></a><span data-ttu-id="3efef-130">De cmdlet invoke-Dscresource bieden retourneert geen bericht in de volg orde waarin ze zijn gemaakt</span><span class="sxs-lookup"><span data-stu-id="3efef-130">Invoke-DscResource cmdlet does not return message in the order they were produced</span></span>

<span data-ttu-id="3efef-131">De `Invoke-DscResource` cmdlet retourneert geen uitgebreide, waarschuwings-en fout berichten in de volg orde waarin ze zijn gemaakt door LCM of de DSC-resource.</span><span class="sxs-lookup"><span data-stu-id="3efef-131">The `Invoke-DscResource` cmdlet does not return verbose, warning, and error messages in the order they were produced by LCM or the DSC resource.</span></span>

<span data-ttu-id="3efef-132">**Oplossing:** Geen.</span><span class="sxs-lookup"><span data-stu-id="3efef-132">**Resolution:** None.</span></span>

## <a name="dsc-resources-cannot-be-debugged-easily-when-used-with-invoke-dscresource"></a><span data-ttu-id="3efef-133">DSC-resources kunnen niet eenvoudig worden opgespoord wanneer ze worden gebruikt met invoke-Dscresource bieden</span><span class="sxs-lookup"><span data-stu-id="3efef-133">DSC Resources cannot be debugged easily when used with Invoke-DscResource</span></span>

<span data-ttu-id="3efef-134">Als LCM wordt uitgevoerd in de foutopsporingsmodus, `Invoke-DscResource` geeft cmdlet geen informatie over runs Pace waarmee verbinding kan worden gemaakt voor fout opsporing.</span><span class="sxs-lookup"><span data-stu-id="3efef-134">When LCM is running in debug mode, `Invoke-DscResource` cmdlet does not give information about runspace to connect to for debugging.</span></span> <span data-ttu-id="3efef-135">Zie [fout opsporing voor DSC-resources](/powershell/scripting/dsc/troubleshooting/debugResource)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="3efef-135">For more information, see [Debugging DSC resources](/powershell/scripting/dsc/troubleshooting/debugResource).</span></span>

<span data-ttu-id="3efef-136">**Oplossing:** De runs Pace detecteren en koppelen met behulp van cmdlets `Get-PSHostProcessInfo` , `Enter-PSHostProcess` `Get-Runspace` en `Debug-Runspace` om fouten op te sporen in de DSC-resource.</span><span class="sxs-lookup"><span data-stu-id="3efef-136">**Resolution:** Discover and attach to the runspace using cmdlets `Get-PSHostProcessInfo`, `Enter-PSHostProcess` , `Get-Runspace` and `Debug-Runspace` to debug the DSC resource.</span></span>

```powershell
# Find all the processes hosting PowerShell
Get-PSHostProcessInfo

ProcessName    ProcessId AppDomainName
-----------    --------- -------------
powershell          3932 DefaultAppDomain
powershell_ise      2304 DefaultAppDomain
WmiPrvSE            3396 DscPsPluginWkr_AppDomain

# Enter the process that is hosting DSC engine (WMI process with DscPsPluginWkr_Appdomain)
Enter-PSHostProcess -Id 3396 -AppDomainName DscPsPluginWkr_AppDomain

# Find all the available rusnspaces in that process
Get-Runspace

Id Name       ComputerName Type  State  Availability
-- ----       ------------ ----  -----  ------------
 2 Runspace2  localhost    Local Opened InBreakpoint
 5 RemoteHost localhost    Local Opened Busy

# Debug the runspace that is in **InBreakpoint** availability state
Debug-Runspace -Id 2
```

## <a name="various-partial-configuration-documents-for-same-node-cannot-have-identical-resource-names"></a><span data-ttu-id="3efef-137">Verschillende gedeeltelijke configuratie documenten voor hetzelfde knoop punt kunnen geen identieke resource namen hebben</span><span class="sxs-lookup"><span data-stu-id="3efef-137">Various Partial Configuration documents for same node cannot have identical resource names</span></span>

<span data-ttu-id="3efef-138">Voor verschillende gedeeltelijke configuraties die worden geïmplementeerd op één knoop punt, hebben identieke namen van resources een fout tijdens de uitvoering.</span><span class="sxs-lookup"><span data-stu-id="3efef-138">For several partial configurations that are deployed onto a single node, identical names of resources cause run time error.</span></span>

<span data-ttu-id="3efef-139">**Oplossing:** Gebruik verschillende namen voor zelfs dezelfde resources in verschillende gedeeltelijke configuraties.</span><span class="sxs-lookup"><span data-stu-id="3efef-139">**Resolution:** Use different names for even same resources in different partial configurations.</span></span>

## <a name="start-dscconfiguration-useexisting-does-not-work-with--credential"></a><span data-ttu-id="3efef-140">Start-DscConfiguration – UseExisting werkt niet met-referentie</span><span class="sxs-lookup"><span data-stu-id="3efef-140">Start-DscConfiguration –UseExisting does not work with -Credential</span></span>

<span data-ttu-id="3efef-141">Bij gebruik `Start-DscConfiguration` met de para meter **UseExisting** wordt de para meter **Credential** genegeerd.</span><span class="sxs-lookup"><span data-stu-id="3efef-141">When using `Start-DscConfiguration` with **UseExisting** parameter, the **Credential** parameter is ignored.</span></span> <span data-ttu-id="3efef-142">DSC maakt gebruik van de standaard proces identiteit om de bewerking voort te zetten.</span><span class="sxs-lookup"><span data-stu-id="3efef-142">DSC uses default process identity to proceed the operation.</span></span> <span data-ttu-id="3efef-143">Dit veroorzaakt een fout wanneer er een andere referentie nodig is om door te gaan op het externe knoop punt.</span><span class="sxs-lookup"><span data-stu-id="3efef-143">This causes error when a different credential is needed to proceed on remote node.</span></span>

<span data-ttu-id="3efef-144">**Oplossing:** CIM-sessie gebruiken voor externe DSC-bewerkingen:</span><span class="sxs-lookup"><span data-stu-id="3efef-144">**Resolution:** Use CIM session for remote DSC operations:</span></span>

```powershell
$session = New-CimSession -ComputerName $node -Credential $credential
Start-DscConfiguration -UseExisting -CimSession $session
```

## <a name="ipv6-addresses-as-node-names-in-dsc-configurations"></a><span data-ttu-id="3efef-145">IPv6-adressen als knooppunt namen in DSC-configuraties</span><span class="sxs-lookup"><span data-stu-id="3efef-145">IPv6 Addresses as Node Names in DSC configurations</span></span>

<span data-ttu-id="3efef-146">IPv6-adressen als knooppunt namen in DSC-configuratie scripts worden niet ondersteund in deze release.</span><span class="sxs-lookup"><span data-stu-id="3efef-146">IPv6 addresses as node names in DSC configuration scripts are not supported in this release.</span></span>

<span data-ttu-id="3efef-147">**Oplossing:** Geen.</span><span class="sxs-lookup"><span data-stu-id="3efef-147">**Resolution:** None.</span></span>

## <a name="debugging-of-class-based-dsc-resources"></a><span data-ttu-id="3efef-148">Fout opsporing voor `Class-Based` DSC-resources</span><span class="sxs-lookup"><span data-stu-id="3efef-148">Debugging of `Class-Based` DSC Resources</span></span>

<span data-ttu-id="3efef-149">Fout opsporing van DSC-resources op basis van klassen wordt niet ondersteund in deze release.</span><span class="sxs-lookup"><span data-stu-id="3efef-149">Debugging of class-based DSC Resources is not supported in this release.</span></span>

<span data-ttu-id="3efef-150">**Oplossing:** Geen.</span><span class="sxs-lookup"><span data-stu-id="3efef-150">**Resolution:** None.</span></span>

## <a name="variables-and-functions-defined-in-script-scope-in-dsc-class-based-resource-are-not-preserved-across-multiple-calls-to-a-dsc-resource"></a><span data-ttu-id="3efef-151">Variabelen en functies die zijn gedefinieerd in $script bereik in DSC-klasse-resources blijven niet behouden in meerdere aanroepen naar een DSC-resource</span><span class="sxs-lookup"><span data-stu-id="3efef-151">Variables and functions defined in $script scope in DSC Class-Based Resource are not preserved across multiple calls to a DSC Resource</span></span>

<span data-ttu-id="3efef-152">Meerdere opeenvolgende aanroepen om te `Start-DSCConfiguration` mislukken als de configuratie gebruikmaakt van een op klassen gebaseerde resource met variabelen of functies die in het bereik zijn gedefinieerd `$script` .</span><span class="sxs-lookup"><span data-stu-id="3efef-152">Multiple consecutive calls to `Start-DSCConfiguration` fails if the configuration is using any class-based resource which has variables or functions defined in `$script` scope.</span></span>

<span data-ttu-id="3efef-153">**Oplossing:** Definieer alle variabelen en functies in de DSC-resource klasse zelf.</span><span class="sxs-lookup"><span data-stu-id="3efef-153">**Resolution:** Define all variables and functions in DSC Resource class itself.</span></span> <span data-ttu-id="3efef-154">Geen `$script` bereik variabelen/-functies.</span><span class="sxs-lookup"><span data-stu-id="3efef-154">No `$script` scope variables/functions.</span></span>

## <a name="dsc-resource-debugging-when-a-resource-is-using-psdscrunascredential"></a><span data-ttu-id="3efef-155">Fout opsporing voor DSC-resources wanneer een resource gebruikmaakt van PSDscRunAsCredential</span><span class="sxs-lookup"><span data-stu-id="3efef-155">DSC Resource Debugging when a resource is using PSDscRunAsCredential</span></span>

<span data-ttu-id="3efef-156">Fout opsporing voor DSC-resources wanneer een resource de eigenschap **PSDscRunAsCredential** in de configuratie gebruikt, wordt niet ondersteund in deze release.</span><span class="sxs-lookup"><span data-stu-id="3efef-156">DSC Resource debugging when a resource is using the **PSDscRunAsCredential** property in the configuration is not supported in this release.</span></span>

<span data-ttu-id="3efef-157">**Oplossing:** Geen.</span><span class="sxs-lookup"><span data-stu-id="3efef-157">**Resolution:** None.</span></span>

## <a name="psdscrunascredential-is-not-supported-for-dsc-composite-resources"></a><span data-ttu-id="3efef-158">PsDscRunAsCredential wordt niet ondersteund voor DSC-samengestelde resources</span><span class="sxs-lookup"><span data-stu-id="3efef-158">PsDscRunAsCredential is not supported for DSC Composite Resources</span></span>

<span data-ttu-id="3efef-159">**Oplossing:** Gebruik de eigenschap Credential als deze beschikbaar is.</span><span class="sxs-lookup"><span data-stu-id="3efef-159">**Resolution:** Use Credential property if available.</span></span> <span data-ttu-id="3efef-160">Voor beeld van serviceset en WindowsFeatureSet</span><span class="sxs-lookup"><span data-stu-id="3efef-160">Example ServiceSet and WindowsFeatureSet</span></span>

## <a name="get-dscresource--syntax-does-not-reflect-psdscrunascredential-correctly"></a><span data-ttu-id="3efef-161">Get-Dscresource bieden-syntaxis geeft niet de juiste PsDscRunAsCredential weer</span><span class="sxs-lookup"><span data-stu-id="3efef-161">Get-DscResource -Syntax does not reflect PsDscRunAsCredential correctly</span></span>

<span data-ttu-id="3efef-162">De **syntaxis** parameter geeft **PsDscRunAsCredential** niet op de juiste wijze weer wanneer de bron deze markeert als verplicht of niet ondersteunt.</span><span class="sxs-lookup"><span data-stu-id="3efef-162">The **Syntax** parameter does not reflect **PsDscRunAsCredential** correctly when resource marks it as mandatory or does not support it.</span></span>

<span data-ttu-id="3efef-163">**Oplossing:** Geen.</span><span class="sxs-lookup"><span data-stu-id="3efef-163">**Resolution:** None.</span></span> <span data-ttu-id="3efef-164">Het ontwerpen van configuratie in ISE weerspiegelt echter de juiste meta gegevens over de eigenschap **PsDscRunAsCredential** wanneer IntelliSense wordt gebruikt.</span><span class="sxs-lookup"><span data-stu-id="3efef-164">However, authoring configuration in ISE reflects correct metadata about **PsDscRunAsCredential** property when using IntelliSense.</span></span>

## <a name="windowsoptionalfeature-is-not-available-in-windows-7"></a><span data-ttu-id="3efef-165">WindowsOptionalFeature is niet beschikbaar in Windows 7</span><span class="sxs-lookup"><span data-stu-id="3efef-165">WindowsOptionalFeature is not available in Windows 7</span></span>

<span data-ttu-id="3efef-166">De **WindowsOptionalFeature** DSC-resource is niet beschikbaar in Windows 7.</span><span class="sxs-lookup"><span data-stu-id="3efef-166">The **WindowsOptionalFeature** DSC resource is not available in Windows 7.</span></span> <span data-ttu-id="3efef-167">Voor deze resource zijn de DISM-module en DISM-cmdlets vereist die vanaf Windows 8 en nieuwere versies van het Windows-besturings systeem beschikbaar zijn.</span><span class="sxs-lookup"><span data-stu-id="3efef-167">This resource requires the DISM module, and DISM cmdlets that are available starting in Windows 8 and newer releases of the Windows operating system.</span></span>

## <a name="for-class-based-dsc-resources-import-dscresource--moduleversion-may-not-work-as-expected"></a><span data-ttu-id="3efef-168">Voor DSC-resources op basis van een klasse werkt import-Dscresource bieden-ModuleVersion mogelijk niet zoals verwacht</span><span class="sxs-lookup"><span data-stu-id="3efef-168">For Class-based DSC resources, Import-DscResource -ModuleVersion may not work as expected</span></span>

<span data-ttu-id="3efef-169">Als het compilatie knooppunt meerdere versies van een DSC-resource module op basis van een klasse bevat, `Import-DscResource -ModuleVersion` wordt niet de opgegeven versie gekozen en worden de volgende compilatie fouten weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="3efef-169">If the compilation node has multiple versions of a class-based DSC resource module, `Import-DscResource -ModuleVersion` does not pick the specified version and results in following compilation error.</span></span>

```Output
ImportClassResourcesFromModule : Exception calling "ImportClassResourcesFromModule" with "3" argument(s):
 "Keyword 'MyTestResource' already defined in the configuration."
At C:\Windows\system32\WindowsPowerShell\v1.0\Modules\PSDesiredStateConfiguration\PSDesiredStateConfiguration.psm1:2035 char:35
+ ... rcesFound = ImportClassResourcesFromModule -Module $mod -Resources $r ...
+                 ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
    + CategoryInfo          : NotSpecified: (:) [ImportClassResourcesFromModule], MethodInvocationException
    + FullyQualifiedErrorId : PSInvalidOperationException,ImportClassResourcesFromModule
```

<span data-ttu-id="3efef-170">**Oplossing:** Importeer de vereiste versie door het **ModuleSpecification** -object te definiëren voor de para meter **module** met de **RequiredVersion** -sleutel die als volgt is opgegeven:</span><span class="sxs-lookup"><span data-stu-id="3efef-170">**Resolution:** Import the required version by defining the **ModuleSpecification** object to the **ModuleName** parameter with **RequiredVersion** key specified as follows:</span></span>

```powershell
Import-DscResource -ModuleName @{ModuleName='MyModuleName';RequiredVersion='1.2'}
```

## <a name="some-dsc-resources-like-registry-resource-may-start-to-take-a-long-time-to-process-the-request"></a><span data-ttu-id="3efef-171">Het kan even duren voordat sommige DSC-resources zoals een register resource lang duurt om de aanvraag te verwerken.</span><span class="sxs-lookup"><span data-stu-id="3efef-171">Some DSC resources like registry resource may start to take a long time to process the request.</span></span>

<span data-ttu-id="3efef-172">**Oplossing 1:** Maak een plannings taak waarmee regel matig de volgende map wordt opgeschoond.</span><span class="sxs-lookup"><span data-stu-id="3efef-172">**Resolution 1:** Create a schedule task that cleans up the following folder periodically.</span></span>

```powershell
$env:windir\system32\config\systemprofile\AppData\Local\Microsoft\Windows\PowerShell\CommandAnalysis
```

<span data-ttu-id="3efef-173">**Oplossing 2:** Wijzig de DSC-configuratie om de map *CommandAnalysis* op het einde van de configuratie op te schonen.</span><span class="sxs-lookup"><span data-stu-id="3efef-173">**Resolution 2:** Change the DSC configuration to clean up the *CommandAnalysis* folder at the end of the configuration.</span></span>

```powershell
Configuration $configName
{

   # User Data
    Registry SetRegisteredOwner
    {
        Ensure = 'Present'
        Force = $True
        Key = $Node.RegisteredKey
        ValueName = $Node.RegisteredOwnerValue
        ValueType = 'String'
        ValueData = $Node.RegisteredOwnerData
    }
    #
    # Script to delete the config
    #
    script DeleteCommandAnalysisCache
    {
        DependsOn = "[Registry]SetRegisteredOwner"
        getscript = "@{}"
        testscript = 'Remove-Item -Path $env:windir\system32\config\systemprofile\AppData\Local\Microsoft\Windows\PowerShell\CommandAnalysis -Force -Recurse -ErrorAction SilentlyContinue -ErrorVariable ev | out-null;$true'
        setscript = '$true'
    }
}
```