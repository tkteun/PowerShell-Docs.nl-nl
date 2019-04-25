---
ms.date: 06/12/2017
keywords: wmf,powershell,installeren
ms.openlocfilehash: 883f80a5c8c99f2ab9886558a7aebfe1204f3be6
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62085136"
---
# <a name="desired-state-configuration-dsc-known-issues-and-limitations"></a>Desired State Configuration (DSC) bekende problemen en beperkingen

## <a name="breaking-change-certificates-used-to-encryptdecrypt-passwords-in-dsc-configurations-may-not-work-after-installing-wmf-50-rtm"></a>Belangrijke wijziging: Certificaten die worden gebruikt voor het versleutelen/ontsleutelen van wachtwoorden in DSC-configuraties werkt mogelijk niet na de installatie van WMF 5.0 RTM

In WMF 4.0 en WMF 5.0 Preview-versies, DSC zou niet toestaan dat wachtwoorden in de configuratie met een lengte van meer dan 121 tekens. DSC is geforceerd korte om wachtwoorden te gebruiken, zelfs als langdurige en een sterk wachtwoord is gewenst is. Deze belangrijke wijziging kan wachtwoorden van willekeurige lengte in de DSC-configuratie.

**Oplossing:** Opnieuw maken van het certificaat met gegevenscodering of sleutel uitwisselen sleutel gebruik en Document versleuteling Enhanced Key usage (1.3.6.1.4.1.311.80.1). TechNet-artikel <https://technet.microsoft.com/library/dn807171.aspx> bevat meer informatie.

## <a name="dsc-cmdlets-may-fail-after-installing-wmf-50-rtm"></a>DSC-cmdlets kunnen mislukken na de installatie van WMF 5.0 RTM

Start-DscConfiguration en andere cmdlets DSC mislukken na de installatie van WMF 5.0 RTM met de volgende fout:
```powershell
    LCM failed to retrieve the property PendingJobStep from the object of class dscInternalCache .
    + CategoryInfo : ObjectNotFound: (root/Microsoft/...gurationManager:String) [], CimException
    + FullyQualifiedErrorId : MI RESULT 6
    + PSComputerName : localhost
```

**Oplossing:** DSCEngineCache.mof verwijderen door het uitvoeren van de volgende opdracht uit in een verhoogde PowerShell-sessie (als Administrator uitvoeren):

```powershell
Remove-Item -Path $env:SystemRoot\system32\Configuration\DSCEngineCache.mof
```

## <a name="dsc-cmdlets-may-not-work-if-wmf-50-rtm-is-installed-on-top-of-wmf-50-production-preview"></a>DSC-cmdlets werken niet als WMF 5.0 RTM boven op WMF 5.0 productie Preview is geïnstalleerd

**Oplossing:** Voer de volgende opdracht uit in een sessie met verhoogde bevoegdheden PowerShell (als administrator uitvoeren):
```powershell
    mofcomp $env:windir\system32\wbem\DscCoreConfProv.mof
```

## <a name="lcm-can-go-into-an-unstable-state-while-using-get-dscconfiguration-in-debugmode"></a>LCM kunt in tot een instabiele status gaan tijdens het gebruik van Get-DscConfiguration in fouten opsporen-modus

Als LCM fouten opsporen-modus, op CTRL + C om te stoppen van de verwerking van Get-DscConfiguration kan leiden tot LCM om te gaan naar een instabiele status dergelijke die meerderheid van de DSC-cmdlets werken niet.

**Oplossing:** Geen druk op CTRL + C tijdens het opsporen van fouten in de cmdlet Get-DscConfiguration.

## <a name="stop-dscconfiguration-may-not-respond-in-debugmode"></a>Stop-DscConfiguration reageren mogelijk niet in fouten opsporen-modus

Als LCM fouten opsporen-modus, kan Stop-DscConfiguration niet reageren, terwijl bij stoppen van een bewerking aan de slag door Get-DscConfiguration

**Oplossing:** Voltooien van de foutopsporing van de bewerking aan de slag door Get-DscConfiguration, zoals wordt beschreven in de sectie '[foutopsporing DSC-resources](https://msdn.microsoft.com/powershell/dsc/debugresource)'.

## <a name="no-verbose-error-messages-are-shown-in-debugmode"></a>Er is geen uitgebreide foutberichten worden weergegeven in fouten opsporen-modus

Als LCM fouten opsporen-modus, worden er geen uitgebreide foutberichten van DSC-Resources weergegeven.

**Oplossing:** Uitschakelen *fouten opsporen-modus* om te zien uitgebreide berichten uit de bron

## <a name="invoke-dscresource-operations-cannot-be-retrieved-by-get-dscconfigurationstatus-cmdlet"></a>Sleutelwoorden Invoke-dscresource bieden bewerkingen kunnen niet worden opgehaald door de cmdlet Get-DscConfigurationStatus

Nadat u de cmdlet Invoke-sleutelwoorden dscresource bieden rechtstreeks aanroepen van een resource-methoden, kunnen niet de records van deze bewerking worden opgehaald via Get-DscConfigurationStatus op een later tijdstip.

**Oplossing:** Geen.

## <a name="get-dscconfigurationstatus-returns-pull-cycle-operations-as-type-consistency"></a>Get-DscConfigurationStatus retourneert pull cyclus bewerkingen als type *consistentie*

Wanneer een knooppunt is ingesteld op PULL vernieuwen-modus, voor elke pullbewerking uitgevoerd, de cmdlet Get-DscConfigurationStatus rapporten van het bewerkingstype als *consistentie* in plaats van *initiële*

**Oplossing:** Geen.

## <a name="invoke-dscresource-cmdlet-does-not-return-message-in-the-order-they-were-produced"></a>Sleutelwoorden Invoke-dscresource bieden cmdlet retourneert geen bericht in de volgorde waarin die ze zijn gemaakt

De cmdlet Invoke-sleutelwoorden dscresource bieden retourneert geen uitgebreide, waarschuwing, en foutberichten in de volgorde waarin die ze zijn geproduceerd door LCM of de DSC-resource.

**Oplossing:** Geen.

## <a name="dsc-resources-cannot-be-debugged-easily-when-used-with-invoke-dscresource"></a>DSC-Resources kan niet eenvoudig worden opgespoord gebruikt in combinatie met sleutelwoorden Invoke-dscresource bieden

Als LCM wordt uitgevoerd in de foutopsporingsmodus (Zie [foutopsporing DSC-resources](https://msdn.microsoft.com/powershell/dsc/debugresource) voor meer informatie), sleutelwoorden Invoke-dscresource bieden cmdlet geeft geen informatie over runspace verbinding maakt met voor foutopsporing.
**Oplossing:** Detecteren en te koppelen aan de runspace met behulp van cmdlets **Get-PSHostProcessInfo**, **Enter PSHostProcess** , **Get-Runspace** en **Debug-Runspace** fouten opsporen in de DSC-resource.

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

## <a name="various-partial-configuration-documents-for-same-node-cannot-have-identical-resource-names"></a>Verschillende gedeeltelijke configuratie documenten voor hetzelfde knooppunt geen identieke resourcenamen

Voor verschillende gedeeltelijke configuraties die zijn geïmplementeerd op één knooppunt, runtimefout identieke namen van resources oorzaak.

**Oplossing:** Gebruik verschillende namen voor zelfs dezelfde resources in verschillende gedeeltelijke configuraties.

## <a name="start-dscconfiguration-useexisting-does-not-work-with--credential"></a>Start-DscConfiguration – UseExisting werkt niet met - referentie

Als u de Start-DscConfiguration voor de parameter – UseExisting, de referentie parameter wordt genegeerd. DSC gebruikt standaard procesidentiteit om door te gaan van de bewerking. Dit veroorzaakt fout als een andere referentie nodig is om door te gaan op een extern knooppunt.

**Oplossing:** Gebruik CIM-sessie voor externe DSC-bewerkingen:
```powershell
$session = New-CimSession -ComputerName $node -Credential $credential
Start-DscConfiguration -UseExisting -CimSession $session
```

## <a name="ipv6-addresses-as-node-names-in-dsc-configurations"></a>IPv6-adressen aan de namen in de DSC-configuraties van knooppunt

IPv6-adressen als knooppuntnamen in scripts voor DSC-configuratie worden niet ondersteund in deze release.

**Oplossing:** Geen.

## <a name="debugging-of-class-based-dsc-resources"></a>Foutopsporing op basis van een klasse DSC-resources

Foutopsporing voor DSC-Resources op basis van een klasse wordt niet ondersteund in deze release.

**Oplossing:** Geen.

## <a name="variables--functions-defined-in-script-scope-in-dsc-class-based-resource-are-not-preserved-across-multiple-calls-to-a-dsc-resource"></a>Variabelen en functies die zijn gedefinieerd binnen het bereik van $script in DSC-Resource op basis van een klasse zijn niet behouden in meerdere aanroepen naar een DSC-Resource

Meerdere opeenvolgende aanroepen naar Start-DSCConfiguration mislukt als de configuratie met behulp van een resource op basis van een klasse die variabelen of functies die zijn gedefinieerd in $script bereik heeft.

**Oplossing:** Definieer alle variabelen en -functies in DSC-Resource-klasse zelf. Functies/No $script bereik variabelen.

## <a name="dsc-resource-debugging-when-a-resource-is-using-psdscrunascredential"></a>DSC-Resource foutopsporing als een resource PSDscRunAsCredential

DSC-Resource foutopsporing bij het gebruik van een resource de *PSDscRunAsCredential* eigenschap in de configuratie is niet suported in deze release.

**Oplossing:** Geen.

## <a name="psdscrunascredential-is-not-supported-for-dsc-composite-resources"></a>PsDscRunAsCredential wordt niet ondersteund voor samengestelde DSC-Resources

**Oplossing:** Referentie-eigenschap gebruiken indien beschikbaar. Voorbeeld van de ServiceSet en WindowsFeatureSet

## <a name="get-dscresource--syntax-does-not-reflect-psdscrunascredential-correctly"></a>*Sleutelwoorden Get-dscresource bieden-syntaxis* PsDscRunAsCredential niet correct wordt weergegeven

Sleutelwoorden Get-dscresource bieden-syntaxis komt niet overeen met PsDscRunAsCredential correct als resource gemarkeerd als verplicht of dit wordt niet ondersteund.

**Oplossing:** Geen. Echter weerspiegelt ontwerpen configuratie in ISE juiste metagegevens over PsDscRunAsCredential eigenschap bij het gebruik van IntelliSense.

## <a name="windowsoptionalfeature-is-not-available-in-windows-7"></a>WindowsOptionalFeature is niet beschikbaar in Windows 7

De DSC WindowsOptionalFeature-resource is niet beschikbaar in Windows 7. Deze resource is vereist voor de DISM-module en de DISM-cmdlets zijn beschikbaar vanaf Windows 8 en nieuwere versies van het Windows-besturingssysteem.

## <a name="for-class-based-dsc-resources-import-dscresource--moduleversion-may-not-work-as-expected"></a>Voor klasse op basis van DSC-resources, sleutelwoorden Import-dscresource bieden - ModuleVersion werkt mogelijk niet zoals verwacht

Als de compilatie-knooppunt meerdere versies van een module DSC-resource op basis van een klasse heeft `Import-DscResource -ModuleVersion` heeft niet de opgegeven versie kiezen en resulteert in de volgende fout bij schemacompilatie.

```
ImportClassResourcesFromModule : Exception calling "ImportClassResourcesFromModule" with "3" argument(s): "Keyword 'MyTestResource' already defined in the configuration."
At C:\Windows\system32\WindowsPowerShell\v1.0\Modules\PSDesiredStateConfiguration\PSDesiredStateConfiguration.psm1:2035 char:35
+ ... rcesFound = ImportClassResourcesFromModule -Module $mod -Resources $r ...
+                 ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
    + CategoryInfo          : NotSpecified: (:) [ImportClassResourcesFromModule], MethodInvocationException
    + FullyQualifiedErrorId : PSInvalidOperationException,ImportClassResourcesFromModule
```

**Oplossing:** De vereiste versie importeren door te definiëren de *ModuleSpecification* object toe aan de `-ModuleName` met `RequiredVersion` sleutel die is opgegeven als volgt:

``` PowerShell
Import-DscResource -ModuleName @{ModuleName='MyModuleName';RequiredVersion='1.2'}
```

## <a name="some-dsc-resources-like-registry-resource-may-start-to-take-a-long-time-to-process-the-request"></a>Sommige DSC-resources, zoals registerresource kunnen beginnen met een lang duren om de aanvraag te verwerken.

**Resolution1:** Een geplande taak periodiek opschonen van de volgende map maken.

``` PowerShell
$env:windir\system32\config\systemprofile\AppData\Local\Microsoft\Windows\PowerShell\CommandAnalysis
```

**Resolution2:** Wijzigen van de DSC-configuratie voor het opschonen van de *CommandAnalysis* map aan het einde van de configuratie.

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
