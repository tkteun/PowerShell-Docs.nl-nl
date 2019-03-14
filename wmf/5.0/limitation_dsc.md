---
ms.date: 06/12/2017
keywords: wmf,powershell,installeren
ms.openlocfilehash: 883f80a5c8c99f2ab9886558a7aebfe1204f3be6
ms.sourcegitcommit: 5990f04b8042ef2d8e571bec6d5b051e64c9921c
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 03/12/2019
ms.locfileid: "57795144"
---
# <a name="desired-state-configuration-dsc-known-issues-and-limitations"></a><span data-ttu-id="ab880-102">Desired State Configuration (DSC) bekende problemen en beperkingen</span><span class="sxs-lookup"><span data-stu-id="ab880-102">Desired State Configuration (DSC) Known Issues and Limitations</span></span>

## <a name="breaking-change-certificates-used-to-encryptdecrypt-passwords-in-dsc-configurations-may-not-work-after-installing-wmf-50-rtm"></a><span data-ttu-id="ab880-103">Belangrijke wijziging: Certificaten die worden gebruikt voor het versleutelen/ontsleutelen van wachtwoorden in DSC-configuraties werkt mogelijk niet na de installatie van WMF 5.0 RTM</span><span class="sxs-lookup"><span data-stu-id="ab880-103">Breaking Change: Certificates used to encrypt/decrypt passwords in DSC configurations may not work after installing WMF 5.0 RTM</span></span>

<span data-ttu-id="ab880-104">In WMF 4.0 en WMF 5.0 Preview-versies, DSC zou niet toestaan dat wachtwoorden in de configuratie met een lengte van meer dan 121 tekens.</span><span class="sxs-lookup"><span data-stu-id="ab880-104">In WMF 4.0 and WMF 5.0 Preview releases, DSC would not allow passwords in the configuration to be of length more than 121 characters.</span></span> <span data-ttu-id="ab880-105">DSC is geforceerd korte om wachtwoorden te gebruiken, zelfs als langdurige en een sterk wachtwoord is gewenst is.</span><span class="sxs-lookup"><span data-stu-id="ab880-105">DSC was forcing to use short passwords even if lengthy and strong password was desired.</span></span> <span data-ttu-id="ab880-106">Deze belangrijke wijziging kan wachtwoorden van willekeurige lengte in de DSC-configuratie.</span><span class="sxs-lookup"><span data-stu-id="ab880-106">This breaking change allows passwords to be of arbitrary length in the DSC configuration.</span></span>

<span data-ttu-id="ab880-107">**Oplossing:** Opnieuw maken van het certificaat met gegevenscodering of sleutel uitwisselen sleutel gebruik en Document versleuteling Enhanced Key usage (1.3.6.1.4.1.311.80.1).</span><span class="sxs-lookup"><span data-stu-id="ab880-107">**Resolution:** Re-create the certificate with Data Encipherment or Key Encipherment Key usage, and Document Encryption Enhanced Key usage (1.3.6.1.4.1.311.80.1).</span></span> <span data-ttu-id="ab880-108">TechNet-artikel <https://technet.microsoft.com/library/dn807171.aspx> bevat meer informatie.</span><span class="sxs-lookup"><span data-stu-id="ab880-108">Technet article <https://technet.microsoft.com/library/dn807171.aspx> has more information.</span></span>

## <a name="dsc-cmdlets-may-fail-after-installing-wmf-50-rtm"></a><span data-ttu-id="ab880-109">DSC-cmdlets kunnen mislukken na de installatie van WMF 5.0 RTM</span><span class="sxs-lookup"><span data-stu-id="ab880-109">DSC cmdlets may fail after installing WMF 5.0 RTM</span></span>

<span data-ttu-id="ab880-110">Start-DscConfiguration en andere cmdlets DSC mislukken na de installatie van WMF 5.0 RTM met de volgende fout:</span><span class="sxs-lookup"><span data-stu-id="ab880-110">Start-DscConfiguration and other DSC cmdlets may fail after installing WMF 5.0 RTM with the following error:</span></span>
```powershell
    LCM failed to retrieve the property PendingJobStep from the object of class dscInternalCache .
    + CategoryInfo : ObjectNotFound: (root/Microsoft/...gurationManager:String) [], CimException
    + FullyQualifiedErrorId : MI RESULT 6
    + PSComputerName : localhost
```

<span data-ttu-id="ab880-111">**Oplossing:** DSCEngineCache.mof verwijderen door het uitvoeren van de volgende opdracht uit in een verhoogde PowerShell-sessie (als Administrator uitvoeren):</span><span class="sxs-lookup"><span data-stu-id="ab880-111">**Resolution:** Delete DSCEngineCache.mof by running the following command in an elevated PowerShell session (Run as Administrator):</span></span>

```powershell
Remove-Item -Path $env:SystemRoot\system32\Configuration\DSCEngineCache.mof
```

## <a name="dsc-cmdlets-may-not-work-if-wmf-50-rtm-is-installed-on-top-of-wmf-50-production-preview"></a><span data-ttu-id="ab880-112">DSC-cmdlets werken niet als WMF 5.0 RTM boven op WMF 5.0 productie Preview is geïnstalleerd</span><span class="sxs-lookup"><span data-stu-id="ab880-112">DSC cmdlets may not work if WMF 5.0 RTM is installed on top of WMF 5.0 Production Preview</span></span>

<span data-ttu-id="ab880-113">**Oplossing:** Voer de volgende opdracht uit in een sessie met verhoogde bevoegdheden PowerShell (als administrator uitvoeren):</span><span class="sxs-lookup"><span data-stu-id="ab880-113">**Resolution:** Run the following command in an elevated PowerShell session (run as administrator):</span></span>
```powershell
    mofcomp $env:windir\system32\wbem\DscCoreConfProv.mof
```

## <a name="lcm-can-go-into-an-unstable-state-while-using-get-dscconfiguration-in-debugmode"></a><span data-ttu-id="ab880-114">LCM kunt in tot een instabiele status gaan tijdens het gebruik van Get-DscConfiguration in fouten opsporen-modus</span><span class="sxs-lookup"><span data-stu-id="ab880-114">LCM can go into an unstable state while using Get-DscConfiguration in DebugMode</span></span>

<span data-ttu-id="ab880-115">Als LCM fouten opsporen-modus, op CTRL + C om te stoppen van de verwerking van Get-DscConfiguration kan leiden tot LCM om te gaan naar een instabiele status dergelijke die meerderheid van de DSC-cmdlets werken niet.</span><span class="sxs-lookup"><span data-stu-id="ab880-115">If LCM is in DebugMode, pressing CTRL+C to stop the processing of Get-DscConfiguration can cause LCM to go into an unstable state such that majority of DSC cmdlets won’t work.</span></span>

<span data-ttu-id="ab880-116">**Oplossing:** Geen druk op CTRL + C tijdens het opsporen van fouten in de cmdlet Get-DscConfiguration.</span><span class="sxs-lookup"><span data-stu-id="ab880-116">**Resolution:** Don’t press CTRL+C while debugging Get-DscConfiguration cmdlet.</span></span>

## <a name="stop-dscconfiguration-may-not-respond-in-debugmode"></a><span data-ttu-id="ab880-117">Stop-DscConfiguration reageren mogelijk niet in fouten opsporen-modus</span><span class="sxs-lookup"><span data-stu-id="ab880-117">Stop-DscConfiguration may not respond in DebugMode</span></span>

<span data-ttu-id="ab880-118">Als LCM fouten opsporen-modus, kan Stop-DscConfiguration niet reageren, terwijl bij stoppen van een bewerking aan de slag door Get-DscConfiguration</span><span class="sxs-lookup"><span data-stu-id="ab880-118">If LCM is in DebugMode, Stop-DscConfiguration may not respond while trying to stop an operation started by Get-DscConfiguration</span></span>

<span data-ttu-id="ab880-119">**Oplossing:** Voltooien van de foutopsporing van de bewerking aan de slag door Get-DscConfiguration, zoals wordt beschreven in de sectie '[foutopsporing DSC-resources](https://msdn.microsoft.com/powershell/dsc/debugresource)'.</span><span class="sxs-lookup"><span data-stu-id="ab880-119">**Resolution:** Finish the debugging of the operation started by Get-DscConfiguration as outlined in section ‘[Debugging DSC resources](https://msdn.microsoft.com/powershell/dsc/debugresource)’.</span></span>

## <a name="no-verbose-error-messages-are-shown-in-debugmode"></a><span data-ttu-id="ab880-120">Er is geen uitgebreide foutberichten worden weergegeven in fouten opsporen-modus</span><span class="sxs-lookup"><span data-stu-id="ab880-120">No Verbose Error Messages are shown in DebugMode</span></span>

<span data-ttu-id="ab880-121">Als LCM fouten opsporen-modus, worden er geen uitgebreide foutberichten van DSC-Resources weergegeven.</span><span class="sxs-lookup"><span data-stu-id="ab880-121">If LCM is in DebugMode, no verbose error messages are displayed from DSC Resources.</span></span>

<span data-ttu-id="ab880-122">**Oplossing:** Uitschakelen *fouten opsporen-modus* om te zien uitgebreide berichten uit de bron</span><span class="sxs-lookup"><span data-stu-id="ab880-122">**Resolution:** Disable *DebugMode* to see verbose messages from the resource</span></span>

## <a name="invoke-dscresource-operations-cannot-be-retrieved-by-get-dscconfigurationstatus-cmdlet"></a><span data-ttu-id="ab880-123">Sleutelwoorden Invoke-dscresource bieden bewerkingen kunnen niet worden opgehaald door de cmdlet Get-DscConfigurationStatus</span><span class="sxs-lookup"><span data-stu-id="ab880-123">Invoke-DscResource operations cannot be retrieved by Get-DscConfigurationStatus cmdlet</span></span>

<span data-ttu-id="ab880-124">Nadat u de cmdlet Invoke-sleutelwoorden dscresource bieden rechtstreeks aanroepen van een resource-methoden, kunnen niet de records van deze bewerking worden opgehaald via Get-DscConfigurationStatus op een later tijdstip.</span><span class="sxs-lookup"><span data-stu-id="ab880-124">After using Invoke-DscResource cmdlet to directly invoke any resource’s methods, the records of such operation cannot be retrieved through Get-DscConfigurationStatus at a later time.</span></span>

<span data-ttu-id="ab880-125">**Oplossing:** Geen.</span><span class="sxs-lookup"><span data-stu-id="ab880-125">**Resolution:** None.</span></span>

## <a name="get-dscconfigurationstatus-returns-pull-cycle-operations-as-type-consistency"></a><span data-ttu-id="ab880-126">Get-DscConfigurationStatus retourneert pull cyclus bewerkingen als type *consistentie*</span><span class="sxs-lookup"><span data-stu-id="ab880-126">Get-DscConfigurationStatus returns pull cycle operations as type *Consistency*</span></span>

<span data-ttu-id="ab880-127">Wanneer een knooppunt is ingesteld op PULL vernieuwen-modus, voor elke pullbewerking uitgevoerd, de cmdlet Get-DscConfigurationStatus rapporten van het bewerkingstype als *consistentie* in plaats van *initiële*</span><span class="sxs-lookup"><span data-stu-id="ab880-127">When a node is set to PULL refresh mode, for each pull operation performed, Get-DscConfigurationStatus cmdlet reports the operation type as *Consistency* instead of *Initial*</span></span>

<span data-ttu-id="ab880-128">**Oplossing:** Geen.</span><span class="sxs-lookup"><span data-stu-id="ab880-128">**Resolution:** None.</span></span>

## <a name="invoke-dscresource-cmdlet-does-not-return-message-in-the-order-they-were-produced"></a><span data-ttu-id="ab880-129">Sleutelwoorden Invoke-dscresource bieden cmdlet retourneert geen bericht in de volgorde waarin die ze zijn gemaakt</span><span class="sxs-lookup"><span data-stu-id="ab880-129">Invoke-DscResource cmdlet does not return message in the order they were produced</span></span>

<span data-ttu-id="ab880-130">De cmdlet Invoke-sleutelwoorden dscresource bieden retourneert geen uitgebreide, waarschuwing, en foutberichten in de volgorde waarin die ze zijn geproduceerd door LCM of de DSC-resource.</span><span class="sxs-lookup"><span data-stu-id="ab880-130">The Invoke-DscResource cmdlet does not return verbose, warning, and error messages in the order they were produced by LCM or the DSC resource.</span></span>

<span data-ttu-id="ab880-131">**Oplossing:** Geen.</span><span class="sxs-lookup"><span data-stu-id="ab880-131">**Resolution:** None.</span></span>

## <a name="dsc-resources-cannot-be-debugged-easily-when-used-with-invoke-dscresource"></a><span data-ttu-id="ab880-132">DSC-Resources kan niet eenvoudig worden opgespoord gebruikt in combinatie met sleutelwoorden Invoke-dscresource bieden</span><span class="sxs-lookup"><span data-stu-id="ab880-132">DSC Resources cannot be debugged easily when used with Invoke-DscResource</span></span>

<span data-ttu-id="ab880-133">Als LCM wordt uitgevoerd in de foutopsporingsmodus (Zie [foutopsporing DSC-resources](https://msdn.microsoft.com/powershell/dsc/debugresource) voor meer informatie), sleutelwoorden Invoke-dscresource bieden cmdlet geeft geen informatie over runspace verbinding maakt met voor foutopsporing.</span><span class="sxs-lookup"><span data-stu-id="ab880-133">When LCM is running in debug mode (see [Debugging DSC resources](https://msdn.microsoft.com/powershell/dsc/debugresource) for more details), Invoke-DscResource cmdlet does not give information about runspace to connect to for debugging.</span></span>
<span data-ttu-id="ab880-134">**Oplossing:** Detecteren en te koppelen aan de runspace met behulp van cmdlets **Get-PSHostProcessInfo**, **Enter PSHostProcess** , **Get-Runspace** en **Debug-Runspace** fouten opsporen in de DSC-resource.</span><span class="sxs-lookup"><span data-stu-id="ab880-134">**Resolution:** Discover and attach to the runspace using cmdlets **Get-PSHostProcessInfo**, **Enter-PSHostProcess** , **Get-Runspace** and **Debug-Runspace** to debug the DSC resource.</span></span>

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

## <a name="various-partial-configuration-documents-for-same-node-cannot-have-identical-resource-names"></a><span data-ttu-id="ab880-135">Verschillende gedeeltelijke configuratie documenten voor hetzelfde knooppunt geen identieke resourcenamen</span><span class="sxs-lookup"><span data-stu-id="ab880-135">Various Partial Configuration documents for same node cannot have identical resource names</span></span>

<span data-ttu-id="ab880-136">Voor verschillende gedeeltelijke configuraties die zijn geïmplementeerd op één knooppunt, runtimefout identieke namen van resources oorzaak.</span><span class="sxs-lookup"><span data-stu-id="ab880-136">For several partial configurations that are deployed onto a single node, identical names of resources cause run time error.</span></span>

<span data-ttu-id="ab880-137">**Oplossing:** Gebruik verschillende namen voor zelfs dezelfde resources in verschillende gedeeltelijke configuraties.</span><span class="sxs-lookup"><span data-stu-id="ab880-137">**Resolution:** Use different names for even same resources in different partial configurations.</span></span>

## <a name="start-dscconfiguration-useexisting-does-not-work-with--credential"></a><span data-ttu-id="ab880-138">Start-DscConfiguration – UseExisting werkt niet met - referentie</span><span class="sxs-lookup"><span data-stu-id="ab880-138">Start-DscConfiguration –UseExisting does not work with -Credential</span></span>

<span data-ttu-id="ab880-139">Als u de Start-DscConfiguration voor de parameter – UseExisting, de referentie parameter wordt genegeerd.</span><span class="sxs-lookup"><span data-stu-id="ab880-139">When using Start-DscConfiguration with –UseExisting parameter, the –Credential parameter is ignored.</span></span> <span data-ttu-id="ab880-140">DSC gebruikt standaard procesidentiteit om door te gaan van de bewerking.</span><span class="sxs-lookup"><span data-stu-id="ab880-140">DSC uses default process identity to proceed the operation.</span></span> <span data-ttu-id="ab880-141">Dit veroorzaakt fout als een andere referentie nodig is om door te gaan op een extern knooppunt.</span><span class="sxs-lookup"><span data-stu-id="ab880-141">This causes error when a different credential is needed to proceed on remote node.</span></span>

<span data-ttu-id="ab880-142">**Oplossing:** Gebruik CIM-sessie voor externe DSC-bewerkingen:</span><span class="sxs-lookup"><span data-stu-id="ab880-142">**Resolution:** Use CIM session for remote DSC operations:</span></span>
```powershell
$session = New-CimSession -ComputerName $node -Credential $credential
Start-DscConfiguration -UseExisting -CimSession $session
```

## <a name="ipv6-addresses-as-node-names-in-dsc-configurations"></a><span data-ttu-id="ab880-143">IPv6-adressen aan de namen in de DSC-configuraties van knooppunt</span><span class="sxs-lookup"><span data-stu-id="ab880-143">IPv6 Addresses as Node Names in DSC configurations</span></span>

<span data-ttu-id="ab880-144">IPv6-adressen als knooppuntnamen in scripts voor DSC-configuratie worden niet ondersteund in deze release.</span><span class="sxs-lookup"><span data-stu-id="ab880-144">IPv6 addresses as node names in DSC configuration scripts are not supported in this release.</span></span>

<span data-ttu-id="ab880-145">**Oplossing:** Geen.</span><span class="sxs-lookup"><span data-stu-id="ab880-145">**Resolution:** None.</span></span>

## <a name="debugging-of-class-based-dsc-resources"></a><span data-ttu-id="ab880-146">Foutopsporing op basis van een klasse DSC-resources</span><span class="sxs-lookup"><span data-stu-id="ab880-146">Debugging of Class-Based DSC Resources</span></span>

<span data-ttu-id="ab880-147">Foutopsporing voor DSC-Resources op basis van een klasse wordt niet ondersteund in deze release.</span><span class="sxs-lookup"><span data-stu-id="ab880-147">Debugging of class-based DSC Resources is not supported in this release.</span></span>

<span data-ttu-id="ab880-148">**Oplossing:** Geen.</span><span class="sxs-lookup"><span data-stu-id="ab880-148">**Resolution:** None.</span></span>

## <a name="variables--functions-defined-in-script-scope-in-dsc-class-based-resource-are-not-preserved-across-multiple-calls-to-a-dsc-resource"></a><span data-ttu-id="ab880-149">Variabelen en functies die zijn gedefinieerd binnen het bereik van $script in DSC-Resource op basis van een klasse zijn niet behouden in meerdere aanroepen naar een DSC-Resource</span><span class="sxs-lookup"><span data-stu-id="ab880-149">Variables & Functions defined in $script scope in DSC Class-Based Resource are not preserved across multiple calls to a DSC Resource</span></span>

<span data-ttu-id="ab880-150">Meerdere opeenvolgende aanroepen naar Start-DSCConfiguration mislukt als de configuratie met behulp van een resource op basis van een klasse die variabelen of functies die zijn gedefinieerd in $script bereik heeft.</span><span class="sxs-lookup"><span data-stu-id="ab880-150">Multiple consecutive calls to Start-DSCConfiguration will fail if configuration is using any class-based resource which has variables or functions defined in $script scope.</span></span>

<span data-ttu-id="ab880-151">**Oplossing:** Definieer alle variabelen en -functies in DSC-Resource-klasse zelf.</span><span class="sxs-lookup"><span data-stu-id="ab880-151">**Resolution:** Define all variables and functions in DSC Resource class itself.</span></span> <span data-ttu-id="ab880-152">Functies/No $script bereik variabelen.</span><span class="sxs-lookup"><span data-stu-id="ab880-152">No $script scope variables/functions.</span></span>

## <a name="dsc-resource-debugging-when-a-resource-is-using-psdscrunascredential"></a><span data-ttu-id="ab880-153">DSC-Resource foutopsporing als een resource PSDscRunAsCredential</span><span class="sxs-lookup"><span data-stu-id="ab880-153">DSC Resource Debugging when a resource is using PSDscRunAsCredential</span></span>

<span data-ttu-id="ab880-154">DSC-Resource foutopsporing bij het gebruik van een resource de *PSDscRunAsCredential* eigenschap in de configuratie is niet suported in deze release.</span><span class="sxs-lookup"><span data-stu-id="ab880-154">DSC Resource debugging when a resource is using the *PSDscRunAsCredential* property in the configuration is not suported in this release.</span></span>

<span data-ttu-id="ab880-155">**Oplossing:** Geen.</span><span class="sxs-lookup"><span data-stu-id="ab880-155">**Resolution:** None.</span></span>

## <a name="psdscrunascredential-is-not-supported-for-dsc-composite-resources"></a><span data-ttu-id="ab880-156">PsDscRunAsCredential wordt niet ondersteund voor samengestelde DSC-Resources</span><span class="sxs-lookup"><span data-stu-id="ab880-156">PsDscRunAsCredential is not supported for DSC Composite Resources</span></span>

<span data-ttu-id="ab880-157">**Oplossing:** Referentie-eigenschap gebruiken indien beschikbaar.</span><span class="sxs-lookup"><span data-stu-id="ab880-157">**Resolution:** Use Credential property if available.</span></span> <span data-ttu-id="ab880-158">Voorbeeld van de ServiceSet en WindowsFeatureSet</span><span class="sxs-lookup"><span data-stu-id="ab880-158">Example ServiceSet and WindowsFeatureSet</span></span>

## <a name="get-dscresource--syntax-does-not-reflect-psdscrunascredential-correctly"></a><span data-ttu-id="ab880-159">*Sleutelwoorden Get-dscresource bieden-syntaxis* PsDscRunAsCredential niet correct wordt weergegeven</span><span class="sxs-lookup"><span data-stu-id="ab880-159">*Get-DscResource -Syntax* does not reflect PsDscRunAsCredential correctly</span></span>

<span data-ttu-id="ab880-160">Sleutelwoorden Get-dscresource bieden-syntaxis komt niet overeen met PsDscRunAsCredential correct als resource gemarkeerd als verplicht of dit wordt niet ondersteund.</span><span class="sxs-lookup"><span data-stu-id="ab880-160">Get-DscResource -Syntax does not reflect PsDscRunAsCredential correctly when resource marks it as mandatory or does not support it.</span></span>

<span data-ttu-id="ab880-161">**Oplossing:** Geen.</span><span class="sxs-lookup"><span data-stu-id="ab880-161">**Resolution:** None.</span></span> <span data-ttu-id="ab880-162">Echter weerspiegelt ontwerpen configuratie in ISE juiste metagegevens over PsDscRunAsCredential eigenschap bij het gebruik van IntelliSense.</span><span class="sxs-lookup"><span data-stu-id="ab880-162">However, authoring configuration in ISE reflects correct metadata about PsDscRunAsCredential property when using IntelliSense.</span></span>

## <a name="windowsoptionalfeature-is-not-available-in-windows-7"></a><span data-ttu-id="ab880-163">WindowsOptionalFeature is niet beschikbaar in Windows 7</span><span class="sxs-lookup"><span data-stu-id="ab880-163">WindowsOptionalFeature is not available in Windows 7</span></span>

<span data-ttu-id="ab880-164">De DSC WindowsOptionalFeature-resource is niet beschikbaar in Windows 7.</span><span class="sxs-lookup"><span data-stu-id="ab880-164">The WindowsOptionalFeature DSC resource is not available in Windows 7.</span></span> <span data-ttu-id="ab880-165">Deze resource is vereist voor de DISM-module en de DISM-cmdlets zijn beschikbaar vanaf Windows 8 en nieuwere versies van het Windows-besturingssysteem.</span><span class="sxs-lookup"><span data-stu-id="ab880-165">This resource requires the DISM module, and DISM cmdlets that are available starting in Windows 8 and newer releases of the Windows operating system.</span></span>

## <a name="for-class-based-dsc-resources-import-dscresource--moduleversion-may-not-work-as-expected"></a><span data-ttu-id="ab880-166">Voor klasse op basis van DSC-resources, sleutelwoorden Import-dscresource bieden - ModuleVersion werkt mogelijk niet zoals verwacht</span><span class="sxs-lookup"><span data-stu-id="ab880-166">For Class-based DSC resources, Import-DscResource -ModuleVersion may not work as expected</span></span>

<span data-ttu-id="ab880-167">Als de compilatie-knooppunt meerdere versies van een module DSC-resource op basis van een klasse heeft `Import-DscResource -ModuleVersion` heeft niet de opgegeven versie kiezen en resulteert in de volgende fout bij schemacompilatie.</span><span class="sxs-lookup"><span data-stu-id="ab880-167">If the compilation node has multiple version of a class-based DSC resource module, `Import-DscResource -ModuleVersion` does not pick the specified version and results in following compilation error.</span></span>

```
ImportClassResourcesFromModule : Exception calling "ImportClassResourcesFromModule" with "3" argument(s): "Keyword 'MyTestResource' already defined in the configuration."
At C:\Windows\system32\WindowsPowerShell\v1.0\Modules\PSDesiredStateConfiguration\PSDesiredStateConfiguration.psm1:2035 char:35
+ ... rcesFound = ImportClassResourcesFromModule -Module $mod -Resources $r ...
+                 ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
    + CategoryInfo          : NotSpecified: (:) [ImportClassResourcesFromModule], MethodInvocationException
    + FullyQualifiedErrorId : PSInvalidOperationException,ImportClassResourcesFromModule
```

<span data-ttu-id="ab880-168">**Oplossing:** De vereiste versie importeren door te definiëren de *ModuleSpecification* object toe aan de `-ModuleName` met `RequiredVersion` sleutel die is opgegeven als volgt:</span><span class="sxs-lookup"><span data-stu-id="ab880-168">**Resolution:** Import the required version by defining the *ModuleSpecification* object to the `-ModuleName` with `RequiredVersion` key specified as follows:</span></span>

``` PowerShell
Import-DscResource -ModuleName @{ModuleName='MyModuleName';RequiredVersion='1.2'}
```

## <a name="some-dsc-resources-like-registry-resource-may-start-to-take-a-long-time-to-process-the-request"></a><span data-ttu-id="ab880-169">Sommige DSC-resources, zoals registerresource kunnen beginnen met een lang duren om de aanvraag te verwerken.</span><span class="sxs-lookup"><span data-stu-id="ab880-169">Some DSC resources like registry resource may start to take a long time to process the request.</span></span>

<span data-ttu-id="ab880-170">**Resolution1:** Een geplande taak periodiek opschonen van de volgende map maken.</span><span class="sxs-lookup"><span data-stu-id="ab880-170">**Resolution1:** Create a schedule task that cleans up the following folder periodically.</span></span>

``` PowerShell
$env:windir\system32\config\systemprofile\AppData\Local\Microsoft\Windows\PowerShell\CommandAnalysis
```

<span data-ttu-id="ab880-171">**Resolution2:** Wijzigen van de DSC-configuratie voor het opschonen van de *CommandAnalysis* map aan het einde van de configuratie.</span><span class="sxs-lookup"><span data-stu-id="ab880-171">**Resolution2:** Change the DSC configuration to clean up the *CommandAnalysis* folder at the end of the configuration.</span></span>

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
