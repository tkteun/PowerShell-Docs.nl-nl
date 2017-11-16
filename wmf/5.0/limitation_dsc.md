---
ms.date: 2017-06-12
author: JKeithB
ms.topic: reference
keywords: WMF, powershell, setup
ms.openlocfilehash: f39328b240a36deb40d484c4aedb889cee91dc8d
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 06/12/2017
---
# <a name="desired-state-configuration-dsc-known-issues-and-limitations"></a>Desired State Configuration (DSC) bekende problemen en beperkingen

<a name="breaking-change-certificates-used-to-encryptdecrypt-passwords-in-dsc-configurations-may-not-work-after-installing-wmf-50-rtm"></a>Breken wijziging: Certificaten gebruikt voor het versleutelen/ontsleutelen wachtwoorden in DSC-configuraties werken mogelijk niet na het installeren van WMF 5.0 RTM
--------------------------------------------------------------------------------------------------------------------------------

In de WMF 4.0 en WMF 5.0 Preview-versies, DSC zou niet toestaan dat wachtwoorden in de configuratie van de lengte van meer dan 121 tekens. DSC is geforceerd korte wachtwoorden gebruiken, zelfs als langdurige en een sterk wachtwoord is vereist. Deze laatste wijziging kan wachtwoorden van willekeurige lengte in de DSC-configuratie.

**Oplossing:** opnieuw maken van het certificaat met gegevenscodering of sleutel uitwisselen sleutel gebruiks- en Document versleuteling Enhanced Key usage (1.3.6.1.4.1.311.80.1). TechNet-artikel <https://technet.microsoft.com/en-us/library/dn807171.aspx> bevat meer informatie.


<a name="dsc-cmdlets-may-fail-after-installing-wmf-50-rtm"></a>DSC-cmdlets mislukken na het installeren van WMF 5.0 RTM
------------------------------------------------------------------------------------
Start DscConfiguration en andere cmdlets DSC mislukken na het installeren van WMF 5.0 RTM met de volgende fout:
```powershell
    LCM failed to retrieve the property PendingJobStep from the object of class dscInternalCache .
    + CategoryInfo : ObjectNotFound: (root/Microsoft/...gurationManager:String) [], CimException
    + FullyQualifiedErrorId : MI RESULT 6
    + PSComputerName : localhost
```

**Oplossing:** DSCEngineCache.mof verwijderen met de volgende opdracht in een verhoogde PowerShell-sessie (als Administrator uitvoeren):
    
```powershell
Remove-Item -Path $env:SystemRoot\system32\Configuration\DSCEngineCache.mof
```


<a name="dsc-cmdlets-may-not-work-if-wmf-50-rtm-is-installed-on-top-of-wmf-50-production-preview"></a>DSC-cmdlets werkt mogelijk niet als WMF 5.0 RTM bovenop WMF 5.0 productie Preview is geïnstalleerd
------------------------------------------------------
**Oplossing:** Voer de volgende opdracht in een verhoogde PowerShell-sessie (als administrator uitvoeren):
```powershell
    mofcomp $env:windir\system32\wbem\DscCoreConfProv.mof
```


<a name="lcm-can-go-into-an-unstable-state-while-using-get-dscconfiguration-in-debugmode"></a>LCM kunt in instabiel gaan tijdens het gebruik van Get-DscConfiguration in fouten opsporen-modus
-------------------------------------------------------------------------------

Als LCM in fouten opsporen-modus is, drukt u op CTRL + C om de verwerking van Get-DscConfiguration stoppen kan leiden tot LCM om te gaan naar instabiel dergelijke die meerderheid van de DSC-cmdlets, werken niet.

**Oplossing:** niet druk op CTRL + C tijdens het opsporen van de cmdlet Get-DscConfiguration.


<a name="stop-dscconfiguration-may-hang-in-debugmode"></a>Stop DscConfiguration loopt in fouten opsporen-modus
------------------------------------------------------------------------------------------------------------------------
Als LCM fouten opsporen-modus, loopt Stop DscConfiguration terwijl bij stoppen van een bewerking door Get-DscConfiguration gestart

**Oplossing:** voltooien foutopsporing van de bewerking gestart door Get-DscConfiguration, zoals wordt beschreven in de sectie '[foutopsporing DSC-resources](https://msdn.microsoft.com/powershell/dsc/debugresource)'.


<a name="no-verbose-error-messages-are-shown-in-debugmode"></a>Er is geen uitgebreide foutberichten worden weergegeven in fouten opsporen-modus
-----------------------------------------------------------------------------------
Als LCM in fouten opsporen-modus is, worden er geen uitgebreide foutberichten van DSC-Resources weergegeven.

**Oplossing:** uitschakelen *fouten opsporen-modus* om te zien van uitgebreide berichten uit de bron


<a name="invoke-dscresource-operations-cannot-be-retrieved-by-get-dscconfigurationstatus-cmdlet"></a>Aanroepen DscResource bewerkingen kunnen niet worden opgehaald door de cmdlet Get-DscConfigurationStatus
--------------------------------------------------------------------------------------
Als u met de cmdlet Invoke-DscResource rechtstreeks aanroepen van een resource-methoden, kunnen niet de records van deze bewerking worden opgehaald via de Get-DscConfigurationStatus op een later tijdstip.

**Oplossing:** geen.


<a name="get-dscconfigurationstatus-returns-pull-cycle-operations-as-type-consistency"></a>Get-DscConfigurationStatus retourneert pull cyclus bewerkingen als type *consistentie*
---------------------------------------------------------------------------------
Wanneer een knooppunt is ingesteld op PULL vernieuwingsmodus voor elk pullbewerking uitgevoerd, de cmdlet Get-DscConfigurationStatus rapporten van het bewerkingstype als *consistentie* in plaats van *initiële*

**Oplossing:** geen.

<a name="invoke-dscresource-cmdlet-does-not-return-message-in-the-order-they-were-produced"></a>Aanroepen DscResource cmdlet retourneert geen bericht in de volgorde waarin die ze zijn geproduceerd
---------------------------------------------------------------------------------
De cmdlet Invoke-DscResource retourneert geen uitgebreide, waarschuwing, en foutberichten in de volgorde waarin die ze zijn geproduceerd door LCM of de DSC-resource.

**Oplossing:** geen.


<a name="dsc-resources-cannot-be-debugged-easily-when-used-with-invoke-dscresource"></a>Foutopsporing eenvoudig DSC-Resources kan niet worden uitgevoerd in combinatie met Invoke-DscResource
-----------------------------------------------------------------------
Wanneer LCM wordt uitgevoerd in de foutopsporingsmodus (Zie [foutopsporing DSC-resources](https://msdn.microsoft.com/powershell/dsc/debugresource) voor meer informatie), de cmdlet Invoke-DscResource geeft geen informatie over runspace verbinding maken met voor foutopsporing.
**Oplossing:** ontdekken en te koppelen aan de runspace met behulp van cmdlets **Get-PSHostProcessInfo**, **Enter PSHostProcess** , **Get Runspace** en  **Foutopsporing Runspace** voor foutopsporing van de DSC-resource.

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


<a name="various-partial-configuration-documents-for-same-node-cannot-have-identical-resource-names"></a>Verschillende gedeeltelijke configuratie documenten voor hetzelfde knooppunt geen identieke resourcenamen
------------------------------------------------------------------------------------------

Voor verschillende gedeeltelijke configuraties die zijn geïmplementeerd op één knooppunt, runtimefout identieke namen van bronnen oorzaak.

**Oplossing:** Gebruik verschillende namen voor zelfs dezelfde bronnen in de andere gedeeltelijke configuraties.


<a name="start-dscconfiguration-useexisting-does-not-work-with--credential"></a>Start DscConfiguration – UseExisting werkt niet met de - referenties
------------------------------------------------------------------

Als u Start DscConfiguration met de parameter – UseExisting, de – referentie parameter wordt genegeerd. Standaard-procesidentiteit DSC gebruikt om door te gaan van de bewerking. Hiermee wordt de fout veroorzaakt wanneer er een andere referentie nodig is om door te gaan op een extern knooppunt.

**Oplossing:** gebruik CIM-sessie voor externe DSC-bewerkingen:
```powershell
$session = New-CimSession -ComputerName $node -Credential $credential
Start-DscConfiguration -UseExisting -CimSession $session
```


<a name="ipv6-addresses-as-node-names-in-dsc-configurations"></a>IPv6-adressen als knooppuntnamen in DSC-configuraties
--------------------------------------------------
IPv6-adressen als knooppuntnamen in scripts voor DSC-configuratie worden niet ondersteund in deze release.

**Oplossing:** geen.


<a name="debugging-of-class-based-dsc-resources"></a>Foutopsporing van een klasse gebaseerde DSC-Resources
--------------------------------------
Foutopsporing van DSC-Resources op basis van een klasse wordt niet ondersteund in deze release.

**Oplossing:** geen.


<a name="variables--functions-defined-in-script-scope-in-dsc-class-based-resource-are-not-preserved-across-multiple-calls-to-a-dsc-resource"></a>Variabelen & functies die zijn gedefinieerd in het bereik van $script in DSC-Resource op basis van een klasse zijn niet behouden in meerdere aanroepen naar een DSC-Resource 
-------------------------------------------------------------------------------------------------------------------------------------

Meerdere opeenvolgende aanroepen naar Start DSCConfiguration mislukt als de configuratie met behulp van een resource op basis van een klasse die variabelen of functies die zijn gedefinieerd in $script bereik heeft.

**Oplossing:** Definieer alle variabelen en functies in DSC-Resource klasse zelf. Functies/No $script bereik variabelen.


<a name="dsc-resource-debugging-when-a-resource-is-using-psdscrunascredential"></a>DSC-Resource foutopsporing bij gebruik van een resource PSDscRunAsCredential
----------------------------------------------------------------------
DSC-Resource foutopsporing bij het gebruik van een resource de *PSDscRunAsCredential* eigenschap in de configuratie is niet suported in deze release.

**Oplossing:** geen.


<a name="psdscrunascredential-is-not-supported-for-dsc-composite-resources"></a>PsDscRunAsCredential wordt niet ondersteund voor samengestelde DSC-Resources
----------------------------------------------------------------

**Oplossing:** gebruik referentie-eigenschap indien beschikbaar. Voorbeeld van de ServiceSet en WindowsFeatureSet


<a name="get-dscresource--syntax-does-not-reflect-psdscrunascredential-correctly"></a>*Get-DscResource-syntaxis* komt niet overeen met PsDscRunAsCredential correct
-------------------------------------------------------------------------
Get-DscResource-syntaxis komt niet overeen met PsDscRunAsCredential correct wanneer bron is gemarkeerd als verplicht of dit niet wordt ondersteund.

**Oplossing:** geen. Echter weerspiegelt authoring configuratie in ISE juiste metagegevens over PsDscRunAsCredential eigenschap bij gebruik van IntelliSense.


<a name="windowsoptionalfeature-is-not-available-in-windows-7"></a>WindowsOptionalFeature is niet beschikbaar in Windows 7
-----------------------------------------------------

De WindowsOptionalFeature DSC-resource is niet beschikbaar in Windows 7. Deze bron moet DISM-cmdlets die beschikbaar zijn in Windows 8 en nieuwere versies van het Windows-besturingssysteem wordt gestart en de DISM-module.

<a name="for-class-based-dsc-resources-import-dscresource--moduleversion-may-not-work-as-expected"></a>Voor klasse gebaseerde DSC-resources importeren DscResource - ModuleVersion werkt mogelijk niet zoals verwacht   
------------------------------------------------------------------------------------------
Als de compilatie-knooppunt meerdere versies van een module DSC resource op basis van een klasse heeft `Import-DscResource -ModuleVersion` niet de opgegeven versie opneemt en de resultaten in de volgende fout bij schemacompilatie.

```
ImportClassResourcesFromModule : Exception calling "ImportClassResourcesFromModule" with "3" argument(s): "Keyword 'MyTestResource' already defined in the configuration."
At C:\Windows\system32\WindowsPowerShell\v1.0\Modules\PSDesiredStateConfiguration\PSDesiredStateConfiguration.psm1:2035 char:35
+ ... rcesFound = ImportClassResourcesFromModule -Module $mod -Resources $r ...
+                 ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
    + CategoryInfo          : NotSpecified: (:) [ImportClassResourcesFromModule], MethodInvocationException
    + FullyQualifiedErrorId : PSInvalidOperationException,ImportClassResourcesFromModule
```

**Oplossing:** importeren van de vereiste versie door te definiëren de *ModuleSpecification* object toe aan de `-ModuleName` met `RequiredVersion` sleutel die is opgegeven als volgt:
``` PowerShell  
Import-DscResource -ModuleName @{ModuleName='MyModuleName';RequiredVersion='1.2'}  
```  

<a name="some-dsc-resources-like-registry-resource-may-start-to-take-a-long-time-to-process-the-request"></a>Sommige DSC-resources zoals register resource gaan kunnen lang duren om de aanvraag te verwerken.
--------------------------------------------------------------------------------------------------------------------------------

**Resolution1:** een geplande taak periodiek opruimen van de volgende map maken.
``` PowerShell 
$env:windir\system32\config\systemprofile\AppData\Local\Microsoft\Windows\PowerShell\CommandAnalysis 
```

**Resolution2:** wijzigen van de DSC-configuratie om op te schonen de *CommandAnalysis* map aan het einde van de configuratie.
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

