---
ms.date: 06/12/2017
keywords: wmf,powershell,installeren
ms.openlocfilehash: 76aa4a372602d78e013b2138eb6409304a4dfb76
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 05/16/2018
---
# <a name="desired-state-configuration-dsc-known-issues-and-limitations"></a><span data-ttu-id="9d4c2-102">Desired State Configuration (DSC) bekende problemen en beperkingen</span><span class="sxs-lookup"><span data-stu-id="9d4c2-102">Desired State Configuration (DSC) Known Issues and Limitations</span></span>

<a name="breaking-change-certificates-used-to-encryptdecrypt-passwords-in-dsc-configurations-may-not-work-after-installing-wmf-50-rtm"></a><span data-ttu-id="9d4c2-103">Breken wijziging: Certificaten gebruikt voor het versleutelen/ontsleutelen wachtwoorden in DSC-configuraties werken mogelijk niet na het installeren van WMF 5.0 RTM</span><span class="sxs-lookup"><span data-stu-id="9d4c2-103">Breaking Change: Certificates used to encrypt/decrypt passwords in DSC configurations may not work after installing WMF 5.0 RTM</span></span>
--------------------------------------------------------------------------------------------------------------------------------

<span data-ttu-id="9d4c2-104">In de WMF 4.0 en WMF 5.0 Preview-versies, DSC zou niet toestaan dat wachtwoorden in de configuratie van de lengte van meer dan 121 tekens.</span><span class="sxs-lookup"><span data-stu-id="9d4c2-104">In WMF 4.0 and WMF 5.0 Preview releases, DSC would not allow passwords in the configuration to be of length more than 121 characters.</span></span> <span data-ttu-id="9d4c2-105">DSC is geforceerd korte wachtwoorden gebruiken, zelfs als langdurige en een sterk wachtwoord is vereist.</span><span class="sxs-lookup"><span data-stu-id="9d4c2-105">DSC was forcing to use short passwords even if lengthy and strong password was desired.</span></span> <span data-ttu-id="9d4c2-106">Deze laatste wijziging kan wachtwoorden van willekeurige lengte in de DSC-configuratie.</span><span class="sxs-lookup"><span data-stu-id="9d4c2-106">This breaking change allows passwords to be of arbitrary length in the DSC configuration.</span></span>

<span data-ttu-id="9d4c2-107">**Oplossing:** opnieuw maken van het certificaat met gegevenscodering of sleutel uitwisselen sleutel gebruiks- en Document versleuteling Enhanced Key usage (1.3.6.1.4.1.311.80.1).</span><span class="sxs-lookup"><span data-stu-id="9d4c2-107">**Resolution:** Re-create the certificate with Data Encipherment or Key Encipherment Key usage, and Document Encryption Enhanced Key usage (1.3.6.1.4.1.311.80.1).</span></span> <span data-ttu-id="9d4c2-108">TechNet-artikel <https://technet.microsoft.com/library/dn807171.aspx> bevat meer informatie.</span><span class="sxs-lookup"><span data-stu-id="9d4c2-108">Technet article <https://technet.microsoft.com/library/dn807171.aspx> has more information.</span></span>


<a name="dsc-cmdlets-may-fail-after-installing-wmf-50-rtm"></a><span data-ttu-id="9d4c2-109">DSC-cmdlets mislukken na het installeren van WMF 5.0 RTM</span><span class="sxs-lookup"><span data-stu-id="9d4c2-109">DSC cmdlets may fail after installing WMF 5.0 RTM</span></span>
------------------------------------------------------------------------------------
<span data-ttu-id="9d4c2-110">Start DscConfiguration en andere cmdlets DSC mislukken na het installeren van WMF 5.0 RTM met de volgende fout:</span><span class="sxs-lookup"><span data-stu-id="9d4c2-110">Start-DscConfiguration and other DSC cmdlets may fail after installing WMF 5.0 RTM with the following error:</span></span>
```powershell
    LCM failed to retrieve the property PendingJobStep from the object of class dscInternalCache .
    + CategoryInfo : ObjectNotFound: (root/Microsoft/...gurationManager:String) [], CimException
    + FullyQualifiedErrorId : MI RESULT 6
    + PSComputerName : localhost
```

<span data-ttu-id="9d4c2-111">**Oplossing:** DSCEngineCache.mof verwijderen met de volgende opdracht in een verhoogde PowerShell-sessie (als Administrator uitvoeren):</span><span class="sxs-lookup"><span data-stu-id="9d4c2-111">**Resolution:** Delete DSCEngineCache.mof by running the following command in an elevated PowerShell session (Run as Administrator):</span></span>

```powershell
Remove-Item -Path $env:SystemRoot\system32\Configuration\DSCEngineCache.mof
```


<a name="dsc-cmdlets-may-not-work-if-wmf-50-rtm-is-installed-on-top-of-wmf-50-production-preview"></a><span data-ttu-id="9d4c2-112">DSC-cmdlets werkt mogelijk niet als WMF 5.0 RTM bovenop WMF 5.0 productie Preview is geïnstalleerd</span><span class="sxs-lookup"><span data-stu-id="9d4c2-112">DSC cmdlets may not work if WMF 5.0 RTM is installed on top of WMF 5.0 Production Preview</span></span>
------------------------------------------------------
<span data-ttu-id="9d4c2-113">**Oplossing:** Voer de volgende opdracht in een verhoogde PowerShell-sessie (als administrator uitvoeren):</span><span class="sxs-lookup"><span data-stu-id="9d4c2-113">**Resolution:** Run the following command in an elevated PowerShell session (run as administrator):</span></span>
```powershell
    mofcomp $env:windir\system32\wbem\DscCoreConfProv.mof
```


<a name="lcm-can-go-into-an-unstable-state-while-using-get-dscconfiguration-in-debugmode"></a><span data-ttu-id="9d4c2-114">LCM kunt in instabiel gaan tijdens het gebruik van Get-DscConfiguration in fouten opsporen-modus</span><span class="sxs-lookup"><span data-stu-id="9d4c2-114">LCM can go into an unstable state while using Get-DscConfiguration in DebugMode</span></span>
-------------------------------------------------------------------------------

<span data-ttu-id="9d4c2-115">Als LCM in fouten opsporen-modus is, drukt u op CTRL + C om de verwerking van Get-DscConfiguration stoppen kan leiden tot LCM om te gaan naar instabiel dergelijke die meerderheid van de DSC-cmdlets, werken niet.</span><span class="sxs-lookup"><span data-stu-id="9d4c2-115">If LCM is in DebugMode, pressing CTRL+C to stop the processing of Get-DscConfiguration can cause LCM to go into an unstable state such that majority of DSC cmdlets won’t work.</span></span>

<span data-ttu-id="9d4c2-116">**Oplossing:** niet druk op CTRL + C tijdens het opsporen van de cmdlet Get-DscConfiguration.</span><span class="sxs-lookup"><span data-stu-id="9d4c2-116">**Resolution:** Don’t press CTRL+C while debugging Get-DscConfiguration cmdlet.</span></span>


<a name="stop-dscconfiguration-may-hang-in-debugmode"></a><span data-ttu-id="9d4c2-117">Stop DscConfiguration loopt in fouten opsporen-modus</span><span class="sxs-lookup"><span data-stu-id="9d4c2-117">Stop-DscConfiguration may hang in DebugMode</span></span>
------------------------------------------------------------------------------------------------------------------------
<span data-ttu-id="9d4c2-118">Als LCM fouten opsporen-modus, loopt Stop DscConfiguration terwijl bij stoppen van een bewerking door Get-DscConfiguration gestart</span><span class="sxs-lookup"><span data-stu-id="9d4c2-118">If LCM is in DebugMode, Stop-DscConfiguration may hang while trying to stop an operation started by Get-DscConfiguration</span></span>

<span data-ttu-id="9d4c2-119">**Oplossing:** voltooien foutopsporing van de bewerking gestart door Get-DscConfiguration, zoals wordt beschreven in de sectie '[foutopsporing DSC-resources](https://msdn.microsoft.com/powershell/dsc/debugresource)'.</span><span class="sxs-lookup"><span data-stu-id="9d4c2-119">**Resolution:** Finish the debugging of the operation started by Get-DscConfiguration as outlined in section ‘[Debugging DSC resources](https://msdn.microsoft.com/powershell/dsc/debugresource)’.</span></span>


<a name="no-verbose-error-messages-are-shown-in-debugmode"></a><span data-ttu-id="9d4c2-120">Er is geen uitgebreide foutberichten worden weergegeven in fouten opsporen-modus</span><span class="sxs-lookup"><span data-stu-id="9d4c2-120">No Verbose Error Messages are shown in DebugMode</span></span>
-----------------------------------------------------------------------------------
<span data-ttu-id="9d4c2-121">Als LCM in fouten opsporen-modus is, worden er geen uitgebreide foutberichten van DSC-Resources weergegeven.</span><span class="sxs-lookup"><span data-stu-id="9d4c2-121">If LCM is in DebugMode, no verbose error messages are displayed from DSC Resources.</span></span>

<span data-ttu-id="9d4c2-122">**Oplossing:** uitschakelen *fouten opsporen-modus* om te zien van uitgebreide berichten uit de bron</span><span class="sxs-lookup"><span data-stu-id="9d4c2-122">**Resolution:** Disable *DebugMode* to see verbose messages from the resource</span></span>


<a name="invoke-dscresource-operations-cannot-be-retrieved-by-get-dscconfigurationstatus-cmdlet"></a><span data-ttu-id="9d4c2-123">Aanroepen DscResource bewerkingen kunnen niet worden opgehaald door de cmdlet Get-DscConfigurationStatus</span><span class="sxs-lookup"><span data-stu-id="9d4c2-123">Invoke-DscResource operations cannot be retrieved by Get-DscConfigurationStatus cmdlet</span></span>
--------------------------------------------------------------------------------------
<span data-ttu-id="9d4c2-124">Als u met de cmdlet Invoke-DscResource rechtstreeks aanroepen van een resource-methoden, kunnen niet de records van deze bewerking worden opgehaald via de Get-DscConfigurationStatus op een later tijdstip.</span><span class="sxs-lookup"><span data-stu-id="9d4c2-124">After using Invoke-DscResource cmdlet to directly invoke any resource’s methods, the records of such operation cannot be retrieved through Get-DscConfigurationStatus at a later time.</span></span>

<span data-ttu-id="9d4c2-125">**Oplossing:** geen.</span><span class="sxs-lookup"><span data-stu-id="9d4c2-125">**Resolution:** None.</span></span>


<a name="get-dscconfigurationstatus-returns-pull-cycle-operations-as-type-consistency"></a><span data-ttu-id="9d4c2-126">Get-DscConfigurationStatus retourneert pull cyclus bewerkingen als type *consistentie*</span><span class="sxs-lookup"><span data-stu-id="9d4c2-126">Get-DscConfigurationStatus returns pull cycle operations as type *Consistency*</span></span>
---------------------------------------------------------------------------------
<span data-ttu-id="9d4c2-127">Wanneer een knooppunt is ingesteld op PULL vernieuwingsmodus voor elk pullbewerking uitgevoerd, de cmdlet Get-DscConfigurationStatus rapporten van het bewerkingstype als *consistentie* in plaats van *initiële*</span><span class="sxs-lookup"><span data-stu-id="9d4c2-127">When a node is set to PULL refresh mode, for each pull operation performed, Get-DscConfigurationStatus cmdlet reports the operation type as *Consistency* instead of *Initial*</span></span>

<span data-ttu-id="9d4c2-128">**Oplossing:** geen.</span><span class="sxs-lookup"><span data-stu-id="9d4c2-128">**Resolution:** None.</span></span>

<a name="invoke-dscresource-cmdlet-does-not-return-message-in-the-order-they-were-produced"></a><span data-ttu-id="9d4c2-129">Aanroepen DscResource cmdlet retourneert geen bericht in de volgorde waarin die ze zijn geproduceerd</span><span class="sxs-lookup"><span data-stu-id="9d4c2-129">Invoke-DscResource cmdlet does not return message in the order they were produced</span></span>
---------------------------------------------------------------------------------
<span data-ttu-id="9d4c2-130">De cmdlet Invoke-DscResource retourneert geen uitgebreide, waarschuwing, en foutberichten in de volgorde waarin die ze zijn geproduceerd door LCM of de DSC-resource.</span><span class="sxs-lookup"><span data-stu-id="9d4c2-130">The Invoke-DscResource cmdlet does not return verbose, warning, and error messages in the order they were produced by LCM or the DSC resource.</span></span>

<span data-ttu-id="9d4c2-131">**Oplossing:** geen.</span><span class="sxs-lookup"><span data-stu-id="9d4c2-131">**Resolution:** None.</span></span>


<a name="dsc-resources-cannot-be-debugged-easily-when-used-with-invoke-dscresource"></a><span data-ttu-id="9d4c2-132">Foutopsporing eenvoudig DSC-Resources kan niet worden uitgevoerd in combinatie met Invoke-DscResource</span><span class="sxs-lookup"><span data-stu-id="9d4c2-132">DSC Resources cannot be debugged easily when used with Invoke-DscResource</span></span>
-----------------------------------------------------------------------
<span data-ttu-id="9d4c2-133">Wanneer LCM wordt uitgevoerd in de foutopsporingsmodus (Zie [foutopsporing DSC-resources](https://msdn.microsoft.com/powershell/dsc/debugresource) voor meer informatie), de cmdlet Invoke-DscResource geeft geen informatie over runspace verbinding maken met voor foutopsporing.</span><span class="sxs-lookup"><span data-stu-id="9d4c2-133">When LCM is running in debug mode (see [Debugging DSC resources](https://msdn.microsoft.com/powershell/dsc/debugresource) for more details), Invoke-DscResource cmdlet does not give information about runspace to connect to for debugging.</span></span>
<span data-ttu-id="9d4c2-134">**Oplossing:** ontdekken en te koppelen aan de runspace met behulp van cmdlets **Get-PSHostProcessInfo**, **Enter PSHostProcess** , **Get Runspace** en **Foutopsporing Runspace** voor foutopsporing van de DSC-resource.</span><span class="sxs-lookup"><span data-stu-id="9d4c2-134">**Resolution:** Discover and attach to the runspace using cmdlets **Get-PSHostProcessInfo**, **Enter-PSHostProcess** , **Get-Runspace** and **Debug-Runspace** to debug the DSC resource.</span></span>

```powershell
# Find all the processes hosting PowerShell
Get-PSHostProcessInfo

ProcessName ProcessId AppDomainName
----------- --------- -------------
powershell 3932 DefaultAppDomain
powershell_ise 2304 DefaultAppDomain
WmiPrvSE 3396 DscPsPluginWkr_AppDomain

# Enter the process that is hosting DSC engine (WMI process with DscPsPluginWkr_Appdomain)
Enter-PSHostProcess -Id 3396 -AppDomainName DscPsPluginWkr_AppDomain

# Find all the available rusnspaces in that process
Get-Runspace

Id Name ComputerName Type State Availability
-- ---- ------------ ---- ----- ------------
2 Runspace2 localhost Local Opened InBreakpoint
5 RemoteHost localhost Local Opened Busy

# Debug the runspace that is in **InBreakpoint** availability state
Debug-Runspace -Id 2
```


<a name="various-partial-configuration-documents-for-same-node-cannot-have-identical-resource-names"></a><span data-ttu-id="9d4c2-135">Verschillende gedeeltelijke configuratie documenten voor hetzelfde knooppunt geen identieke resourcenamen</span><span class="sxs-lookup"><span data-stu-id="9d4c2-135">Various Partial Configuration documents for same node cannot have identical resource names</span></span>
------------------------------------------------------------------------------------------

<span data-ttu-id="9d4c2-136">Voor verschillende gedeeltelijke configuraties die zijn geïmplementeerd op één knooppunt, runtimefout identieke namen van bronnen oorzaak.</span><span class="sxs-lookup"><span data-stu-id="9d4c2-136">For several partial configurations that are deployed onto a single node, identical names of resources cause run time error.</span></span>

<span data-ttu-id="9d4c2-137">**Oplossing:** Gebruik verschillende namen voor zelfs dezelfde bronnen in de andere gedeeltelijke configuraties.</span><span class="sxs-lookup"><span data-stu-id="9d4c2-137">**Resolution:** Use different names for even same resources in different partial configurations.</span></span>


<a name="start-dscconfiguration-useexisting-does-not-work-with--credential"></a><span data-ttu-id="9d4c2-138">Start DscConfiguration – UseExisting werkt niet met de - referenties</span><span class="sxs-lookup"><span data-stu-id="9d4c2-138">Start-DscConfiguration –UseExisting does not work with -Credential</span></span>
------------------------------------------------------------------

<span data-ttu-id="9d4c2-139">Als u Start DscConfiguration met de parameter – UseExisting, de – referentie parameter wordt genegeerd.</span><span class="sxs-lookup"><span data-stu-id="9d4c2-139">When using Start-DscConfiguration with –UseExisting parameter, the –Credential parameter is ignored.</span></span> <span data-ttu-id="9d4c2-140">Standaard-procesidentiteit DSC gebruikt om door te gaan van de bewerking.</span><span class="sxs-lookup"><span data-stu-id="9d4c2-140">DSC uses default process identity to proceed the operation.</span></span> <span data-ttu-id="9d4c2-141">Hiermee wordt de fout veroorzaakt wanneer er een andere referentie nodig is om door te gaan op een extern knooppunt.</span><span class="sxs-lookup"><span data-stu-id="9d4c2-141">This causes error when a different credential is needed to proceed on remote node.</span></span>

<span data-ttu-id="9d4c2-142">**Oplossing:** gebruik CIM-sessie voor externe DSC-bewerkingen:</span><span class="sxs-lookup"><span data-stu-id="9d4c2-142">**Resolution:** Use CIM session for remote DSC operations:</span></span>
```powershell
$session = New-CimSession -ComputerName $node -Credential $credential
Start-DscConfiguration -UseExisting -CimSession $session
```


<a name="ipv6-addresses-as-node-names-in-dsc-configurations"></a><span data-ttu-id="9d4c2-143">IPv6-adressen als knooppuntnamen in DSC-configuraties</span><span class="sxs-lookup"><span data-stu-id="9d4c2-143">IPv6 Addresses as Node Names in DSC configurations</span></span>
--------------------------------------------------
<span data-ttu-id="9d4c2-144">IPv6-adressen als knooppuntnamen in scripts voor DSC-configuratie worden niet ondersteund in deze release.</span><span class="sxs-lookup"><span data-stu-id="9d4c2-144">IPv6 addresses as node names in DSC configuration scripts are not supported in this release.</span></span>

<span data-ttu-id="9d4c2-145">**Oplossing:** geen.</span><span class="sxs-lookup"><span data-stu-id="9d4c2-145">**Resolution:** None.</span></span>


<a name="debugging-of-class-based-dsc-resources"></a><span data-ttu-id="9d4c2-146">Foutopsporing van een klasse gebaseerde DSC-Resources</span><span class="sxs-lookup"><span data-stu-id="9d4c2-146">Debugging of Class-Based DSC Resources</span></span>
--------------------------------------
<span data-ttu-id="9d4c2-147">Foutopsporing van DSC-Resources op basis van een klasse wordt niet ondersteund in deze release.</span><span class="sxs-lookup"><span data-stu-id="9d4c2-147">Debugging of class-based DSC Resources is not supported in this release.</span></span>

<span data-ttu-id="9d4c2-148">**Oplossing:** geen.</span><span class="sxs-lookup"><span data-stu-id="9d4c2-148">**Resolution:** None.</span></span>


<a name="variables--functions-defined-in-script-scope-in-dsc-class-based-resource-are-not-preserved-across-multiple-calls-to-a-dsc-resource"></a><span data-ttu-id="9d4c2-149">Variabelen & functies die zijn gedefinieerd in het bereik van $script in DSC-Resource op basis van een klasse zijn niet behouden in meerdere aanroepen naar een DSC-Resource</span><span class="sxs-lookup"><span data-stu-id="9d4c2-149">Variables & Functions defined in $script scope in DSC Class-Based Resource are not preserved across multiple calls to a DSC Resource</span></span>
-------------------------------------------------------------------------------------------------------------------------------------

<span data-ttu-id="9d4c2-150">Meerdere opeenvolgende aanroepen naar Start DSCConfiguration mislukt als de configuratie met behulp van een resource op basis van een klasse die variabelen of functies die zijn gedefinieerd in $script bereik heeft.</span><span class="sxs-lookup"><span data-stu-id="9d4c2-150">Multiple consecutive calls to Start-DSCConfiguration will fail if configuration is using any class-based resource which has variables or functions defined in $script scope.</span></span>

<span data-ttu-id="9d4c2-151">**Oplossing:** Definieer alle variabelen en functies in DSC-Resource klasse zelf.</span><span class="sxs-lookup"><span data-stu-id="9d4c2-151">**Resolution:** Define all variables and functions in DSC Resource class itself.</span></span> <span data-ttu-id="9d4c2-152">Functies/No $script bereik variabelen.</span><span class="sxs-lookup"><span data-stu-id="9d4c2-152">No $script scope variables/functions.</span></span>


<a name="dsc-resource-debugging-when-a-resource-is-using-psdscrunascredential"></a><span data-ttu-id="9d4c2-153">DSC-Resource foutopsporing bij gebruik van een resource PSDscRunAsCredential</span><span class="sxs-lookup"><span data-stu-id="9d4c2-153">DSC Resource Debugging when a resource is using PSDscRunAsCredential</span></span>
----------------------------------------------------------------------
<span data-ttu-id="9d4c2-154">DSC-Resource foutopsporing bij het gebruik van een resource de *PSDscRunAsCredential* eigenschap in de configuratie is niet suported in deze release.</span><span class="sxs-lookup"><span data-stu-id="9d4c2-154">DSC Resource debugging when a resource is using the *PSDscRunAsCredential* property in the configuration is not suported in this release.</span></span>

<span data-ttu-id="9d4c2-155">**Oplossing:** geen.</span><span class="sxs-lookup"><span data-stu-id="9d4c2-155">**Resolution:** None.</span></span>


<a name="psdscrunascredential-is-not-supported-for-dsc-composite-resources"></a><span data-ttu-id="9d4c2-156">PsDscRunAsCredential wordt niet ondersteund voor samengestelde DSC-Resources</span><span class="sxs-lookup"><span data-stu-id="9d4c2-156">PsDscRunAsCredential is not supported for DSC Composite Resources</span></span>
----------------------------------------------------------------

<span data-ttu-id="9d4c2-157">**Oplossing:** gebruik referentie-eigenschap indien beschikbaar.</span><span class="sxs-lookup"><span data-stu-id="9d4c2-157">**Resolution:** Use Credential property if available.</span></span> <span data-ttu-id="9d4c2-158">Voorbeeld van de ServiceSet en WindowsFeatureSet</span><span class="sxs-lookup"><span data-stu-id="9d4c2-158">Example ServiceSet and WindowsFeatureSet</span></span>


<a name="get-dscresource--syntax-does-not-reflect-psdscrunascredential-correctly"></a><span data-ttu-id="9d4c2-159">*Get-DscResource-syntaxis* komt niet overeen met PsDscRunAsCredential correct</span><span class="sxs-lookup"><span data-stu-id="9d4c2-159">*Get-DscResource -Syntax* does not reflect PsDscRunAsCredential correctly</span></span>
-------------------------------------------------------------------------
<span data-ttu-id="9d4c2-160">Get-DscResource-syntaxis komt niet overeen met PsDscRunAsCredential correct wanneer bron is gemarkeerd als verplicht of dit niet wordt ondersteund.</span><span class="sxs-lookup"><span data-stu-id="9d4c2-160">Get-DscResource -Syntax does not reflect PsDscRunAsCredential correctly when resource marks it as mandatory or does not support it.</span></span>

<span data-ttu-id="9d4c2-161">**Oplossing:** geen.</span><span class="sxs-lookup"><span data-stu-id="9d4c2-161">**Resolution:** None.</span></span> <span data-ttu-id="9d4c2-162">Echter weerspiegelt authoring configuratie in ISE juiste metagegevens over PsDscRunAsCredential eigenschap bij gebruik van IntelliSense.</span><span class="sxs-lookup"><span data-stu-id="9d4c2-162">However, authoring configuration in ISE reflects correct metadata about PsDscRunAsCredential property when using IntelliSense.</span></span>


<a name="windowsoptionalfeature-is-not-available-in-windows-7"></a><span data-ttu-id="9d4c2-163">WindowsOptionalFeature is niet beschikbaar in Windows 7</span><span class="sxs-lookup"><span data-stu-id="9d4c2-163">WindowsOptionalFeature is not available in Windows 7</span></span>
-----------------------------------------------------

<span data-ttu-id="9d4c2-164">De WindowsOptionalFeature DSC-resource is niet beschikbaar in Windows 7.</span><span class="sxs-lookup"><span data-stu-id="9d4c2-164">The WindowsOptionalFeature DSC resource is not available in Windows 7.</span></span> <span data-ttu-id="9d4c2-165">Deze bron moet DISM-cmdlets die beschikbaar zijn in Windows 8 en nieuwere versies van het Windows-besturingssysteem wordt gestart en de DISM-module.</span><span class="sxs-lookup"><span data-stu-id="9d4c2-165">This resource requires the DISM module, and DISM cmdlets that are available starting in Windows 8 and newer releases of the Windows operating system.</span></span>

<a name="for-class-based-dsc-resources-import-dscresource--moduleversion-may-not-work-as-expected"></a><span data-ttu-id="9d4c2-166">Voor klasse gebaseerde DSC-resources importeren DscResource - ModuleVersion werkt mogelijk niet zoals verwacht</span><span class="sxs-lookup"><span data-stu-id="9d4c2-166">For Class-based DSC resources, Import-DscResource -ModuleVersion may not work as expected</span></span>
------------------------------------------------------------------------------------------
<span data-ttu-id="9d4c2-167">Als de compilatie-knooppunt meerdere versies van een module DSC resource op basis van een klasse heeft `Import-DscResource -ModuleVersion` niet de opgegeven versie opneemt en de resultaten in de volgende fout bij schemacompilatie.</span><span class="sxs-lookup"><span data-stu-id="9d4c2-167">If the compilation node has multiple version of a class-based DSC resource module, `Import-DscResource -ModuleVersion` does not pick the specified version and results in following compilation error.</span></span>

```
ImportClassResourcesFromModule : Exception calling "ImportClassResourcesFromModule" with "3" argument(s): "Keyword 'MyTestResource' already defined in the configuration."
At C:\Windows\system32\WindowsPowerShell\v1.0\Modules\PSDesiredStateConfiguration\PSDesiredStateConfiguration.psm1:2035 char:35
+ ... rcesFound = ImportClassResourcesFromModule -Module $mod -Resources $r ...
+                 ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
    + CategoryInfo          : NotSpecified: (:) [ImportClassResourcesFromModule], MethodInvocationException
    + FullyQualifiedErrorId : PSInvalidOperationException,ImportClassResourcesFromModule
```

<span data-ttu-id="9d4c2-168">**Oplossing:** importeren van de vereiste versie door te definiëren de *ModuleSpecification* object toe aan de `-ModuleName` met `RequiredVersion` sleutel die is opgegeven als volgt:</span><span class="sxs-lookup"><span data-stu-id="9d4c2-168">**Resolution:** Import the required version by defining the *ModuleSpecification* object to the `-ModuleName` with `RequiredVersion` key specified as follows:</span></span>
``` PowerShell
Import-DscResource -ModuleName @{ModuleName='MyModuleName';RequiredVersion='1.2'}
```

<a name="some-dsc-resources-like-registry-resource-may-start-to-take-a-long-time-to-process-the-request"></a><span data-ttu-id="9d4c2-169">Sommige DSC-resources zoals register resource gaan kunnen lang duren om de aanvraag te verwerken.</span><span class="sxs-lookup"><span data-stu-id="9d4c2-169">Some DSC resources like registry resource may start to take a long time to process the request.</span></span>
--------------------------------------------------------------------------------------------------------------------------------

<span data-ttu-id="9d4c2-170">**Resolution1:** een geplande taak periodiek opruimen van de volgende map maken.</span><span class="sxs-lookup"><span data-stu-id="9d4c2-170">**Resolution1:** Create a schedule task that cleans up the following folder periodically.</span></span>
``` PowerShell
$env:windir\system32\config\systemprofile\AppData\Local\Microsoft\Windows\PowerShell\CommandAnalysis
```

<span data-ttu-id="9d4c2-171">**Resolution2:** wijzigen van de DSC-configuratie om op te schonen de *CommandAnalysis* map aan het einde van de configuratie.</span><span class="sxs-lookup"><span data-stu-id="9d4c2-171">**Resolution2:** Change the DSC configuration to clean up the *CommandAnalysis* folder at the end of the configuration.</span></span>
``` PowerShell
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
        DependsOn="[Registry]SetRegisteredOwner"
        getscript="@{}"
        testscript = 'Remove-Item -Path $env:windir\system32\config\systemprofile\AppData\Local\Microsoft\Windows\PowerShell\CommandAnalysis -Force -Recurse -ErrorAction SilentlyContinue -ErrorVariable ev | out-null;$true'
        setscript = '$true'
    }
}
```
