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
# <a name="desired-state-configuration-dsc-known-issues-and-limitations"></a>Bekende problemen en beperkingen voor desired state Configuration (DSC)

## <a name="breaking-change-certificates-used-to-encryptdecrypt-passwords-in-dsc-configurations-may-not-work-after-installing-wmf-50-rtm"></a>Belang rijke wijziging: certificaten die worden gebruikt voor het versleutelen/ontsleutelen van wacht woorden in DSC-configuraties, werken mogelijk niet na installatie van WMF 5,0

In de Preview-versies van WMF 4,0 en WMF 5,0 staat DSC niet toe dat wacht woorden in de configuratie langer zijn dan 121 tekens. DSC afdwingt het gebruik van korte wacht woorden, zelfs als de lengte en het sterke wacht woord gewenst zijn. Met deze breuk wijziging kunnen wacht woorden een wille keurige lengte hebben in de DSC-configuratie.

**Oplossing:** Maak het certificaat opnieuw met gegevens codering of sleutel codering sleutel gebruik en document versleuteling uitgebreid sleutel gebruik (1.3.6.1.4.1.311.80.1). Zie [Protect-CmsMessage](/powershell/module/Microsoft.PowerShell.Security/Protect-CmsMessage)voor meer informatie.

## <a name="dsc-cmdlets-may-fail-after-installing-wmf-50-rtm"></a>DSC-cmdlets kunnen mislukken na de installatie van WMF 5,0 RTM

`Start-DscConfiguration`en andere DSC-cmdlets kunnen mislukken na de installatie van WMF 5,0 RTM met de volgende fout:

```Output
LCM failed to retrieve the property PendingJobStep from the object of class dscInternalCache .
+ CategoryInfo : ObjectNotFound: (root/Microsoft/...gurationManager:String) [], CimException
+ FullyQualifiedErrorId : MI RESULT 6
+ PSComputerName : localhost
```

**Oplossing:** Verwijder DSCEngineCache. MOF door de volgende opdracht uit te voeren in een Power shell-sessie met verhoogde bevoegdheden (als administrator uitvoeren):

```powershell
Remove-Item -Path $env:SystemRoot\system32\Configuration\DSCEngineCache.mof
```

## <a name="dsc-cmdlets-may-not-work-if-wmf-50-rtm-is-installed-on-top-of-wmf-50-production-preview"></a>DSC-cmdlets werken mogelijk niet als WMF 5,0 RTM boven op de WMF-5,0-productie preview is geïnstalleerd

**Oplossing:** Voer de volgende opdracht uit in een Power shell-sessie met verhoogde bevoegdheden (als administrator uitvoeren):

```powershell
mofcomp $env:windir\system32\wbem\DscCoreConfProv.mof
```

## <a name="lcm-can-go-into-an-unstable-state-while-using-get-dscconfiguration-in-debugmode"></a>LCM kan de status Insta Biel maken terwijl Get-DscConfiguration in DebugMode wordt gebruikt

Als LCM zich in DebugMode bevindt, drukt u op CTRL + C om te stoppen met het verwerken van `Get-DscConfiguration` een instabiele status, zodat de meeste DSC-cmdlets niet werken.

**Oplossing:** Druk niet op CTRL + C tijdens de cmdlet voor fout opsporing `Get-DscConfiguration` .

## <a name="stop-dscconfiguration-may-not-respond-in-debugmode"></a>Stop-DscConfiguration reageert mogelijk niet in DebugMode

Als LCM zich in DebugMode bevindt, reageert `Stop-DscConfiguration` niet tijdens het stoppen van een bewerking die is gestart door`Get-DscConfiguration`

**Oplossing:** Voltooi de fout opsporing van de bewerking die is gestart door `Get-DscConfiguration` zoals beschreven in [DSC-resources voor fout opsporing](/powershell/scripting/dsc/troubleshooting/debugResource).

## <a name="no-verbose-error-messages-are-shown-in-debugmode"></a>Er worden geen uitgebreide fout berichten weer gegeven in DebugMode

Als LCM zich in **DebugMode**bevindt, worden er geen uitgebreide fout berichten weer gegeven uit DSC-resources.

**Oplossing:** **DebugMode** uitschakelen om uitgebreide berichten van de resource weer te geven

## <a name="invoke-dscresource-operations-cannot-be-retrieved-by-get-dscconfigurationstatus-cmdlet"></a>Invoke-Dscresource bieden-bewerkingen kunnen niet worden opgehaald met de cmdlet Get-DscConfigurationStatus

Nadat `Invoke-DscResource` de cmdlet is gebruikt om alle methoden van een resource rechtstreeks aan te roepen, kunnen de records van een dergelijke bewerking niet worden opgehaald via `Get-DscConfigurationStatus` .

**Oplossing:** Geen.

## <a name="get-dscconfigurationstatus-returns-pull-cycle-operations-as-type-consistency"></a>Get-DscConfigurationStatus retourneert pull-cyclus bewerkingen als type **consistentie**

Wanneer een knoop punt is ingesteld op PULL-vernieuwings modus, voor elke uitgevoerde pull-bewerking `Get-DscConfigurationStatus` rapporteert de cmdlet het bewerkings type als **consistentie** in plaats van de *eerste*

**Oplossing:** Geen.

## <a name="invoke-dscresource-cmdlet-does-not-return-message-in-the-order-they-were-produced"></a>De cmdlet invoke-Dscresource bieden retourneert geen bericht in de volg orde waarin ze zijn gemaakt

De `Invoke-DscResource` cmdlet retourneert geen uitgebreide, waarschuwings-en fout berichten in de volg orde waarin ze zijn gemaakt door LCM of de DSC-resource.

**Oplossing:** Geen.

## <a name="dsc-resources-cannot-be-debugged-easily-when-used-with-invoke-dscresource"></a>DSC-resources kunnen niet eenvoudig worden opgespoord wanneer ze worden gebruikt met invoke-Dscresource bieden

Als LCM wordt uitgevoerd in de foutopsporingsmodus, `Invoke-DscResource` geeft cmdlet geen informatie over runs Pace waarmee verbinding kan worden gemaakt voor fout opsporing. Zie [fout opsporing voor DSC-resources](/powershell/scripting/dsc/troubleshooting/debugResource)voor meer informatie.

**Oplossing:** De runs Pace detecteren en koppelen met behulp van cmdlets `Get-PSHostProcessInfo` , `Enter-PSHostProcess` `Get-Runspace` en `Debug-Runspace` om fouten op te sporen in de DSC-resource.

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

## <a name="various-partial-configuration-documents-for-same-node-cannot-have-identical-resource-names"></a>Verschillende gedeeltelijke configuratie documenten voor hetzelfde knoop punt kunnen geen identieke resource namen hebben

Voor verschillende gedeeltelijke configuraties die worden geïmplementeerd op één knoop punt, hebben identieke namen van resources een fout tijdens de uitvoering.

**Oplossing:** Gebruik verschillende namen voor zelfs dezelfde resources in verschillende gedeeltelijke configuraties.

## <a name="start-dscconfiguration-useexisting-does-not-work-with--credential"></a>Start-DscConfiguration – UseExisting werkt niet met-referentie

Bij gebruik `Start-DscConfiguration` met de para meter **UseExisting** wordt de para meter **Credential** genegeerd. DSC maakt gebruik van de standaard proces identiteit om de bewerking voort te zetten. Dit veroorzaakt een fout wanneer er een andere referentie nodig is om door te gaan op het externe knoop punt.

**Oplossing:** CIM-sessie gebruiken voor externe DSC-bewerkingen:

```powershell
$session = New-CimSession -ComputerName $node -Credential $credential
Start-DscConfiguration -UseExisting -CimSession $session
```

## <a name="ipv6-addresses-as-node-names-in-dsc-configurations"></a>IPv6-adressen als knooppunt namen in DSC-configuraties

IPv6-adressen als knooppunt namen in DSC-configuratie scripts worden niet ondersteund in deze release.

**Oplossing:** Geen.

## <a name="debugging-of-class-based-dsc-resources"></a>Fout opsporing voor `Class-Based` DSC-resources

Fout opsporing van DSC-resources op basis van klassen wordt niet ondersteund in deze release.

**Oplossing:** Geen.

## <a name="variables-and-functions-defined-in-script-scope-in-dsc-class-based-resource-are-not-preserved-across-multiple-calls-to-a-dsc-resource"></a>Variabelen en functies die zijn gedefinieerd in $script bereik in DSC-klasse-resources blijven niet behouden in meerdere aanroepen naar een DSC-resource

Meerdere opeenvolgende aanroepen om te `Start-DSCConfiguration` mislukken als de configuratie gebruikmaakt van een op klassen gebaseerde resource met variabelen of functies die in het bereik zijn gedefinieerd `$script` .

**Oplossing:** Definieer alle variabelen en functies in de DSC-resource klasse zelf. Geen `$script` bereik variabelen/-functies.

## <a name="dsc-resource-debugging-when-a-resource-is-using-psdscrunascredential"></a>Fout opsporing voor DSC-resources wanneer een resource gebruikmaakt van PSDscRunAsCredential

Fout opsporing voor DSC-resources wanneer een resource de eigenschap **PSDscRunAsCredential** in de configuratie gebruikt, wordt niet ondersteund in deze release.

**Oplossing:** Geen.

## <a name="psdscrunascredential-is-not-supported-for-dsc-composite-resources"></a>PsDscRunAsCredential wordt niet ondersteund voor DSC-samengestelde resources

**Oplossing:** Gebruik de eigenschap Credential als deze beschikbaar is. Voor beeld van serviceset en WindowsFeatureSet

## <a name="get-dscresource--syntax-does-not-reflect-psdscrunascredential-correctly"></a>Get-Dscresource bieden-syntaxis geeft niet de juiste PsDscRunAsCredential weer

De **syntaxis** parameter geeft **PsDscRunAsCredential** niet op de juiste wijze weer wanneer de bron deze markeert als verplicht of niet ondersteunt.

**Oplossing:** Geen. Het ontwerpen van configuratie in ISE weerspiegelt echter de juiste meta gegevens over de eigenschap **PsDscRunAsCredential** wanneer IntelliSense wordt gebruikt.

## <a name="windowsoptionalfeature-is-not-available-in-windows-7"></a>WindowsOptionalFeature is niet beschikbaar in Windows 7

De **WindowsOptionalFeature** DSC-resource is niet beschikbaar in Windows 7. Voor deze resource zijn de DISM-module en DISM-cmdlets vereist die vanaf Windows 8 en nieuwere versies van het Windows-besturings systeem beschikbaar zijn.

## <a name="for-class-based-dsc-resources-import-dscresource--moduleversion-may-not-work-as-expected"></a>Voor DSC-resources op basis van een klasse werkt import-Dscresource bieden-ModuleVersion mogelijk niet zoals verwacht

Als het compilatie knooppunt meerdere versies van een DSC-resource module op basis van een klasse bevat, `Import-DscResource -ModuleVersion` wordt niet de opgegeven versie gekozen en worden de volgende compilatie fouten weer gegeven.

```Output
ImportClassResourcesFromModule : Exception calling "ImportClassResourcesFromModule" with "3" argument(s):
 "Keyword 'MyTestResource' already defined in the configuration."
At C:\Windows\system32\WindowsPowerShell\v1.0\Modules\PSDesiredStateConfiguration\PSDesiredStateConfiguration.psm1:2035 char:35
+ ... rcesFound = ImportClassResourcesFromModule -Module $mod -Resources $r ...
+                 ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
    + CategoryInfo          : NotSpecified: (:) [ImportClassResourcesFromModule], MethodInvocationException
    + FullyQualifiedErrorId : PSInvalidOperationException,ImportClassResourcesFromModule
```

**Oplossing:** Importeer de vereiste versie door het **ModuleSpecification** -object te definiëren voor de para meter **module** met de **RequiredVersion** -sleutel die als volgt is opgegeven:

```powershell
Import-DscResource -ModuleName @{ModuleName='MyModuleName';RequiredVersion='1.2'}
```

## <a name="some-dsc-resources-like-registry-resource-may-start-to-take-a-long-time-to-process-the-request"></a>Het kan even duren voordat sommige DSC-resources zoals een register resource lang duurt om de aanvraag te verwerken.

**Oplossing 1:** Maak een plannings taak waarmee regel matig de volgende map wordt opgeschoond.

```powershell
$env:windir\system32\config\systemprofile\AppData\Local\Microsoft\Windows\PowerShell\CommandAnalysis
```

**Oplossing 2:** Wijzig de DSC-configuratie om de map *CommandAnalysis* op het einde van de configuratie op te schonen.

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
