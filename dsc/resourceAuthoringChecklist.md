---
ms.date: 2017-06-12
ms.topic: conceptual
keywords: DSC, powershell, configuratie, setup
title: Controlelijst voor het ontwerpen van resource
ms.openlocfilehash: 8f6ea79ec4936b13f54d2b2a5c6974a180735344
ms.sourcegitcommit: a444406120e5af4e746cbbc0558fe89a7e78aef6
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 01/17/2018
---
# <a name="resource-authoring-checklist"></a>Controlelijst voor het ontwerpen van resource
Deze controlelijst is een lijst met aanbevolen procedures bij het ontwerpen van een nieuwe DSC-Resource.
## <a name="resource-module-contains-psd1-file-and-schemamof-for-every-resource"></a>Resource-module bevat .psd1 bestands- en schema.mof voor elke resource 
Controleer of de resource heeft de juiste structuur en alle vereiste bestanden bevat. Elke resource-module een .psd1-bestand moet bevatten en elke resource niet-samengestelde schema.mof bestand moet hebben. Resources die geen schema bevatten worden niet weergegeven door **Get-DscResource** en gebruikers zich niet intellisense gebruiken bij het schrijven van code voor deze modules in ISE. De mapstructuur voor xRemoteFile resource die deel uitmaakt van de [xPSDesiredStateConfiguration bronmodule](https://github.com/PowerShell/xPSDesiredStateConfiguration), ziet er als volgt uit:


```
xPSDesiredStateConfiguration
    DSCResources
        MSFT_xRemoteFile
            MSFT_xRemoteFile.psm1
            MSFT_xRemoteFile.schema.mof
    Examples
        xRemoteFile_DownloadFile.ps1
    ResourceDesignerScripts
        GenerateXRemoteFileSchema.ps1
    Tests
        ResourceDesignerTests.ps1
    xPSDesiredStateConfiguration.psd1
```

## <a name="resource-and-schema-are-correct"></a>Bron en het schema kloppen ##
Controleer het schema van de resource (*. schema.mof) bestand. U kunt de [DSC-Resource Designer](https://www.powershellgallery.com/packages/xDSCResourceDesigner/) te ontwikkelen en testen van uw schema. Zorg ervoor dat:
- Typen eigenschappen juist zijn (bijvoorbeeld tekenreeks niet gebruiken voor eigenschappen die numerieke waarden accepteert, moet u UInt32 of andere numerieke typen in plaats daarvan)
- Eigenschapskenmerken juist zijn opgegeven als: ([key], [vereist], [schrijven], [lezen])
- Ten minste één parameter in het schema heeft zijn gemarkeerd als [sleutel]
- [lezen] eigenschap niet naast elkaar worden gebruikt samen met een van: [vereist], [key], [schrijven]
- Als meerdere kwalificaties zijn opgegeven, behalve [lezen], klikt u vervolgens prioriteit]
- Als [schrijven] en [vereist] zijn opgegeven, wordt de [vereist] heeft een hogere prioriteit
- ValueMap is opgegeven, indien van toepassing

Voorbeeld:
```
[Read, ValueMap{"Present", "Absent"}, Values{"Present", "Absent"}, Description("Says whether DestinationPath exists on the machine")] String Ensure;
```

- Beschrijvende naam is opgegeven en bevestigt aan de naamgeving DSC

Voorbeeld: ```[ClassVersion("1.0.0.0"), FriendlyName("xRemoteFile")]```

- Elk veld heeft een duidelijke beschrijving. De PowerShell-GitHub-opslagplaats is een goede voorbeelden zoals [de. schema.mof voor xRemoteFile](https://github.com/PowerShell/xPSDesiredStateConfiguration/blob/dev/DSCResources/MSFT_xRemoteFile/MSFT_xRemoteFile.schema.mof)

Bovendien moet u **Test xDscResource** en **Test xDscSchema** cmdlets uit [DSC-Resource Designer](https://www.powershellgallery.com/packages/xDSCResourceDesigner/) automatisch te controleren of de bron en het schema:
```
Test-xDscResource <Resource_folder>
Test-xDscSchema <Path_to_resource_schema_file>
```
Bijvoorbeeld:
```powershell
Test-xDscResource ..\DSCResources\MSFT_xRemoteFile
Test-xDscSchema ..\DSCResources\MSFT_xRemoteFile\MSFT_xRemoteFile.schema.mof
```

## <a name="resource-loads-without-errors"></a>Resource wordt geladen zonder fouten ##
Controleer of de module resources kan worden geladen.
Dit kan handmatig worden gerealiseerd door het uitvoeren van `Import-Module <resource_module> -force ` en bevestigt dat geen fouten zijn opgetreden, of door schrijven test automation. In geval van de laatste kunt u deze structuur te volgen in uw testscenario:
```powershell
$error = $null
Import-Module <resource_module> –force
If ($error.count –ne 0) {
    Throw “Module was not imported correctly. Errors returned: $error”
}
```
## <a name="resource-is-idempotent-in-the-positive-case"></a>Bron is idempotent in het geval is positief 
Een van de fundamentele kenmerken van DSC-resources is idempotence worden. Dit betekent dat het toepassen van een DSC-configuratie die resource met meerdere keren wordt altijd hetzelfde resultaat bereiken. Bijvoorbeeld, als we een configuratie met de volgende bestandsbron maken:
```powershell
File file {
    DestinationPath = "C:\test\test.txt"
    Contents = "Sample text"
} 
```
Bestand test.txt worden na het toepassen van voor het eerst wordt weergegeven in de map C:\test. Latere uitvoeringen van dezelfde configuratie moeten echter niet wijzigen voor de status van de machine (bijvoorbeeld geen kopieën van het bestand test.txt moeten worden gemaakt).
Om te controleren of een resource idempotent kunt u meerdere keren aanroepen **Set TargetResource** bij het testen van de resource direct of bel **Start DscConfiguration** meerdere keren bij het uitvoeren van end-to-end testen. Het resultaat moet hetzelfde na elke uitvoeren. 


## <a name="test-user-modification-scenario"></a>Testscenario gebruiker wijziging ##
Door het wijzigen van de status van de machine en vervolgens opnieuw uit te voeren DSC, kunt u controleren of **Set TargetResource** en **Test TargetResource** naar behoren. Hier vindt u stappen die u moet uitvoeren:
1.  Beginnen met de resource niet in de gewenste status.
2.  Configuratie uitvoeren met de bron
3.  Controleer of **Test DscConfiguration** retourneert True
4.  Het geconfigureerde item om te worden uit de gewenste status wijzigen
5.  Controleer of **Test DscConfiguration** retourneert onwaar Hier volgt een voorbeeld van een concrete Resourcegebruik register:
1.  Beginnen met de registersleutel niet in de gewenste status
2.  Voer **Start DscConfiguration** met een configuratie wilt plaatsen in de gewenste status en controleer of deze is geslaagd.
3.  Voer **Test DscConfiguration** en controleer of wordt true geretourneerd
4.  De waarde van de sleutel wijzigen zodat deze zich niet in de gewenste status
5.  Voer **Test DscConfiguration** en controleer of het resultaat is false
6.  Get-TargetResource functionaliteit is geverifieerd met behulp van Get-DscConfiguration

Details van de huidige status van de resource moet worden geretourneerd door Get-TargetResource. Zorg ervoor dat deze te testen op aanroepen van Get-DscConfiguration na het toepassen van de configuratie en te verifiëren dat uitvoer correct de huidige status van de machine weerspiegelt. Het is belangrijk afzonderlijk testen omdat eventuele problemen op dit gebied wordt niet weergegeven bij het aanroepen van Start DscConfiguration.

## <a name="call-getsettest-targetresource-functions-directly"></a>Roep **Get/Set/Test-TargetResource** rechtstreeks fungeert ##

Zorg ervoor dat u testen de **Get/Set/Test-TargetResource** functies die zijn geïmplementeerd in de bron door ze rechtstreeks aanroepen en verifiëren dat ze werken zoals verwacht.

## <a name="verify-end-to-end-using-start-dscconfiguration"></a>Controleren of de complete **Start DscConfiguration** ##

Testen **Get/Set/Test-TargetResource** functies door het aanroepen van deze rechtstreeks is belangrijk, maar niet alle problemen op deze manier worden gedetecteerd. U moet zich richten aanzienlijk deel van uw tests over het gebruik van **Start DscConfiguration** of de pull-server. Dit is in feite hoe gebruikers de resource, zodat de betekenis van dit type tests Onderschat niet gebruiken. Mogelijke typen problemen:
- Referentie/sessie mogelijk anders werken omdat de DSC-agent wordt uitgevoerd als een service.  Zorg ervoor dat alle functies hier complete testen.
- Fouten uitvoeren door **Start DscConfiguration** mogelijk anders uit dan bij het aanroepen van de **Set TargetResource** rechtstreeks werken.

## <a name="test-compatability-on-all-dsc-supported-platforms"></a>Ondersteunde platforms voor test-compatibiliteit van alle DSC ##
Resource moet werken op alle platforms van DSC ondersteund (Windows Server 2008 R2 en nieuwer). De meest recente WMF (Windows Management Framework) installeren op uw besturingssysteem naar de nieuwste versie van DSC. Als de bron aan het ontwerp niet op sommige van deze platformen werkt, kan een specifiek foutbericht moet worden geretourneerd. Controleer ook of dat de resource controleert of u verbinding maakt met cmdlets aanwezig op bepaalde machine zijn. Windows Server 2012 toegevoegd een groot aantal nieuwe cmdlets die niet beschikbaar op Windows Server 2008 R2, zelfs met WMF is geïnstalleerd. 

## <a name="verify-on-windows-client-if-applicable"></a>Controleer of op Windows-Client (indien van toepassing) ##
Een zeer gangbaar gat in de test controleert de resource alleen op serverversies van Windows. Veel resources ook zijn ontworpen om te werken op Client-SKU's, zodat als die true in het geval is, vergeet niet om deze te testen op deze platforms ook. 
## <a name="get-dscresource-lists-the-resource"></a>Get-DSCResource geeft een lijst van de resource ##
Na implementatie van de module, moet aanroepen van Get-DscResource aanbieden uw resource onder andere als gevolg hiervan. Als u uw resource in de lijst vinden kunt, controleert u dat bestand schema.mof voor die bron bestaat. 
## <a name="resource-module-contains-examples"></a>Resource-module bevat voorbeelden ##
Maken kwaliteitsvoorbeelden waarmee anderen te begrijpen hoe deze gebruiken. Dit is essentieel, vooral omdat voorbeeldcode als documentatie worden beschouwd door veel gebruikers. 
- Eerst moet u de voorbeelden die opgenomen met de module – minimaal worden bepalen, dient u belangrijkste gebruiksvoorbeelden omvatten voor uw resource:
- Als uw module verschillende bronnen die nodig is om samen te werken voor een end-to-end-scenario bevat, is de elementaire end-to-end-voorbeeld in het ideale geval eerste.
- De eerste voorbeelden moet zeer eenvoudig--het aan de slag met uw resources in kleine beheerbare segmenten (bijvoorbeeld een nieuwe VHD maken)
- Opeenvolgende voorbeelden moeten bouwen in deze voorbeelden (bijvoorbeeld een virtuele machine maken vanaf een VHD, verwijderen van de virtuele machine, VM wijzigen) en weergeven van geavanceerde functionaliteit (bv. maken van een virtuele machine met dynamisch geheugen)
- Voorbeeldconfiguraties parameters moeten worden gebruikt (alle waarden als parameters voor de configuratie moeten worden doorgegeven en er mag geen waarden hardcoded):
```powershell
configuration Sample_xRemoteFile_DownloadFile
{
    param
    (
        [string[]] $nodeName = 'localhost',

        [parameter(Mandatory = $true)]
        [ValidateNotNullOrEmpty()]
        [String] $destinationPath,

        [parameter(Mandatory = $true)]
        [ValidateNotNullOrEmpty()]
        [String] $uri,

        [String] $userAgent,

        [Hashtable] $headers
    )

    Import-DscResource -Name MSFT_xRemoteFile -ModuleName xPSDesiredStateConfiguration

    Node $nodeName
    {
        xRemoteFile DownloadFile
        {
            DestinationPath = $destinationPath
            Uri = $uri
            UserAgent = $userAgent
            Headers = $headers
        }
    }
} 
```
- Het is raadzaam om op te nemen (opmerkingen uitgaand) voorbeeld van hoe u de configuratie met de werkelijke waarden aan het einde van het voorbeeldscript niet aanroepen. Bijvoorbeeld, in de bovenstaande configuratie is het niet altijd duidelijk dat de beste manier om op te geven UserAgent is:

`UserAgent = [Microsoft.PowerShell.Commands.PSUserAgent]::InternetExplorer`  
Een opmerking kan in dat geval verduidelijken dat de beoogde uitvoering van de configuratie:
```
<# 
Sample use (parameter values need to be changed according to your scenario):

Sample_xRemoteFile_DownloadFile -destinationPath "$env:SystemDrive\fileName.jpg" -uri "http://www.contoso.com/image.jpg"

Sample_xRemoteFile_DownloadFile -destinationPath "$env:SystemDrive\fileName.jpg" -uri "http://www.contoso.com/image.jpg" `
-userAgent [Microsoft.PowerShell.Commands.PSUserAgent]::InternetExplorer -headers @{"Accept-Language" = "en-US"}
#>  
```
- Elke bijvoorbeeld, een korte beschrijving waarin wordt uitgelegd wat het doet en de betekenis van de parameters te schrijven. 
- Zorg ervoor dat voorbeelden hebben betrekking op de meeste belangrijke scenario's voor uw resource en als er niets ontbreekt, Controleer of ze alle uitvoeren machine in de gewenste status geplaatst.  

## <a name="error-messages-are-easy-to-understand-and-help-users-solve-problems"></a>Foutberichten zijn gemakkelijk te begrijpen en oplossen van problemen met gebruikers helpen ##
Goede foutberichten worden:
- : Het grootste probleem met de foutberichten bestaat dat ze vaak niet bestaan, zorg er dus dat er zijn. 
- Gemakkelijker te begrijpen: menselijke leesbare, niet verborgen foutcodes
- Nauwkeurig: Is beschreven wat er precies het probleem
- Feitelijke: Advies hoe het probleem op te lossen
- Beleefd: Niet schuldig gebruiker of maken ze van mening bent dat ongeldige Zorg ervoor dat u fouten in de complete scenario's controleren (met behulp van **Start DscConfiguration**), omdat ze van die afwijken kunnen bij het uitvoeren van functies van de resource direct geretourneerd. 

## <a name="log-messages-are-easy-to-understand-and-informative-including-verbose-debug-and-etw-logs"></a>Berichten in het logboek zijn gemakkelijker te begrijpen en informatieve (inclusief-verbose,-ETW-logboeken en foutopsporing) ##
Zorg ervoor dat Logboeken die zijn gegenereerd door de resource gemakkelijk zijn te begrijpen en geef een waarde voor de gebruiker. Resources moeten uitvoer alle informatie die nuttig voor de gebruiker zijn kan, maar meer logboeken is niet altijd beter. U moet voorkomen van redundantie en gegevens die niet worden uitgevoerd bieden aanvullende waarde – Maak iemand honderden logboekvermeldingen doorlopen om te kunnen vinden wat ze zoekt niet. Er worden geen logboeken is natuurlijk niet een aanvaardbare oplossing voor dit probleem ofwel. 

Bij het testen, moet u ook uitgebreide analyseren en foutopsporing van Logboeken (door het uitvoeren van **Start DscConfiguration** met-verbose en -switches op de juiste wijze voor foutopsporing), ook als ETW-Logboeken. Als u DSC ETW-Logboeken, gaat u naar Logboeken en open de volgende map: toepassingen en Services van Microsoft - Windows - Desired State Configuration.  Er standaard worden operationele kanaal, maar zorg ervoor dat het inschakelen van analyse en foutopsporing kanalen voordat de configuratie wordt uitgevoerd. U kunt de onderstaande script uitvoeren zodat analysen/Debug kanalen:
```powershell
$statusEnabled = $true
# Use "Analytic" to enable Analytic channel
$eventLogFullName = "Microsoft-Windows-Dsc/Debug" 
$commandToExecute = "wevtutil set-log $eventLogFullName /e:$statusEnabled /q:$statusEnabled   "
$log = New-Object System.Diagnostics.Eventing.Reader.EventLogConfiguration $eventLogFullName
if($statusEnabled -eq $log.IsEnabled)
{
    Write-Host -Verbose "The channel event log is already enabled"
    return
}     
Invoke-Expression $commandToExecute 
```
## <a name="resource-implementation-does-not-contain-hardcoded-paths"></a>Resource-implementatie bevat geen hardcoded paden ##
Zorg ervoor dat er zijn geen paden vastgelegd in de resource-implementatie, met name als ze taal wordt ervan uitgegaan dat (en-us), of wanneer er systeemvariabelen die kunnen worden gebruikt.
Als de bron moet toegang tot bepaalde paden, omgevingsvariabelen gebruiken in plaats van hardcoderen wordt het pad, zoals deze afwijken op andere computers.

Voorbeeld:

In plaats van:
```
$tempPath = "C:\Users\kkaczma\AppData\Local\Temp\MyResource"
$programFilesPath = "C:\Program Files (x86)"
 ```
U kunt schrijven:
```
$tempPath = Join-Path $env:temp "MyResource"
$programFilesPath = ${env:ProgramFiles(x86)} 
```
## <a name="resource-implementation-does-not-contain-user-information"></a>Implementatie van resource bevatten geen gebruikersgegevens ##
Zorg ervoor dat er zijn geen e-namen, accountgegevens of namen van mensen in de code.
## <a name="resource-was-tested-with-validinvalid-credentials"></a>Resource is getest met de referenties geldig/ongeldig ##
Als de resource een referentie als parameter:
- Controleer of de resource-werkt als lokaal systeem (of het computeraccount voor de externe bronnen) geen toegang heeft.
- Controleer of de resource werkt met een referentie die is opgegeven voor u, ingesteld en testen 
- Als de bron naar shares, test u alle varianten die u ondersteunen wilt, zoals:
  - Standaard windows-bestandsshares.
  - DFS-shares.
  - SAMBA-shares (als u ondersteuning voor Linux.)

## <a name="resource-does-not-require-interactive-input"></a>Resource vereist geen interactieve invoer ##
**Get/Set/Test-TargetResource** functies automatisch moet worden uitgevoerd en voor gebruikers in elk stadium van de uitvoering van de invoer niet opgeschort (bv. Gebruik geen **Get-Credential** binnen deze functies). Als u leveren de invoer van gebruiker wilt, moet u deze doorgeven aan de configuratie als parameter tijdens de compilatiefase. 
## <a name="resource-functionality-was-thoroughly-tested"></a>Resourcefunctionaliteit is uitgebreid getest. ##
Deze controlelijst bevat de items die zijn belangrijk om te worden getest en/of vaak zijn gemist. Er zijn bunch van tests, hoofdzakelijk functionele die zijn die specifiek zijn voor de resource die u wilt testen en niet hier worden vermeld. Vergeet niet over negatieve testcases. 
## <a name="best-practice-resource-module-contains-tests-folder-with-resourcedesignertestsps1-script"></a>Kunt u beter: Resource-module bevat de map Tests met ResourceDesignerTests.ps1 script ##
Het is raadzaam map 'Tests' create binnen bronmodule, ResourceDesignerTests.ps1-bestand maken en toevoegen van testen met behulp van **Test xDscResource** en **Test xDscSchema** voor alle resources in bepaalde module. Op deze manier kunt u snel schema's van alle resources uit het opgegeven modules en voert u een sanity controleren voordat u publiceert valideren.
XRemoteFile, kan ResourceTests.ps1 Zoek net zo eenvoudig als:
```powershell
Test-xDscResource ..\DSCResources\MSFT_xRemoteFile
Test-xDscSchema ..\DSCResources\MSFT_xRemoteFile\MSFT_xRemoteFile.schema.mof 
```
##<a name="best-practice-resource-folder-contains-resource-designer-script-for-generating-schema"></a>Kunt u beter: resourcemap resource designer script voor het genereren van schema ## bevat
Elke bron moet een resource designer script een mof-schema van de resource genereert bevatten. Dit bestand moet worden geplaatst <ResourceName>\ResourceDesignerScripts en de naam genereren<ResourceName>Schema.ps1 voor xRemoteFile resource dit bestand GenerateXRemoteFileSchema.ps1 zou worden aangeroepen en bevat:
```powershell 
$DestinationPath = New-xDscResourceProperty -Name DestinationPath -Type String -Attribute Key -Description 'Path under which downloaded or copied file should be accessible after operation.'
$Uri = New-xDscResourceProperty -Name Uri -Type String -Attribute Required -Description 'Uri of a file which should be copied or downloaded. This parameter supports HTTP and HTTPS values.'
$Headers = New-xDscResourceProperty -Name Headers -Type Hashtable[] -Attribute Write -Description 'Headers of the web request.'
$UserAgent = New-xDscResourceProperty -Name UserAgent -Type String -Attribute Write -Description 'User agent for the web request.' 
$Ensure = New-xDscResourceProperty -Name Ensure -Type String -Attribute Read -ValidateSet "Present", "Absent" -Description 'Says whether DestinationPath exists on the machine'
$Credential = New-xDscResourceProperty -Name Credential -Type PSCredential -Attribute Write -Description 'Specifies a user account that has permission to send the request.'
$CertificateThumbprint = New-xDscResourceProperty -Name CertificateThumbprint -Type String -Attribute Write -Description 'Digital public key certificate that is used to send the request.'

New-xDscResource -Name MSFT_xRemoteFile -Property @($DestinationPath, $Uri, $Headers, $UserAgent, $Ensure, $Credential, $CertificateThumbprint) -ModuleName xPSDesiredStateConfiguration2 -FriendlyName xRemoteFile 
```
## <a name="best-practice-resource-supports--whatif"></a>Kunt u beter: bron - whatif wordt ondersteund ##
Als uw resource 'gevaarlijke' bewerkingen uitvoert, is het raadzaam om - whatif-functionaliteit te implementeren. Nadat deze voltooid, zorg er dan voor dat bewerkingen waarvoor er gebeuren zou als de opdracht is uitgevoerd zonder whatif switch hierin wordt beschreven whatif uitvoer.
Controleer ook of bewerkingen wordt niet uitgevoerd (de status van het knooppunt worden niet gewijzigd) wanneer-whatif switch aanwezig is. Bijvoorbeeld, Stel dat we bestandsbron wilt testen. Hieronder vindt u eenvoudige configuratie gemaakt van bestand 'test.txt' met inhoud 'test':
```powershell
configuration config
{
    node localhost 
    {
        File file
        {
            Contents="test"
            DestinationPath="C:\test\test.txt"
        }
    }
}
config 
```
Als wij compileren en vervolgens de configuratie met de schakeloptie-whatif wordt uitgevoerd, is de uitvoer vertellen ons precies wat er gebeurt wanneer we de configuratie uitvoert. Tot maar is niet worden uitgevoerd door de configuratie zelf (test.txt bestand is niet gemaakt).
```powershell 
Start-DscConfiguration -path .\config -ComputerName localhost -wait -verbose -whatif
VERBOSE: Perform operation 'Invoke CimMethod' with following parameters, ''methodName' =
SendConfigurationApply,'className' = MSFT_DSCLocalConfigurationManager,'namespaceName' =
root/Microsoft/Windows/DesiredStateConfiguration'.
VERBOSE: An LCM method call arrived from computer CHARLESX1 with user sid
S-1-5-21-397955417-626881126-188441444-5179871.
What if: [X]: LCM:  [ Start  Set      ]
What if: [X]: LCM:  [ Start  Resource ]  [[File]file]
What if: [X]: LCM:  [ Start  Test     ]  [[File]file]
What if: [X]:                            [[File]file] The system cannot find the file specified.
What if: [X]:                            [[File]file] The related file/directory is: C:\test\test.txt.
What if: [X]: LCM:  [ End    Test     ]  [[File]file]  in 0.0270 seconds.
What if: [X]: LCM:  [ Start  Set      ]  [[File]file]
What if: [X]:                            [[File]file] The system cannot find the file specified.
What if: [X]:                            [[File]file] The related file/directory is: C:\test\test.txt.
What if: [X]:                            [C:\test\test.txt] Creating and writing contents and setting attributes.
What if: [X]: LCM:  [ End    Set      ]  [[File]file]  in 0.0180 seconds.
What if: [X]: LCM:  [ End    Resource ]  [[File]file]
What if: [X]: LCM:  [ End    Set      ]
VERBOSE: [X]: LCM:  [ End    Set      ]    in  0.1050 seconds.
VERBOSE: Operation 'Invoke CimMethod' complete.
```

Deze lijst is niet volledig, maar deze bevat veel belangrijke problemen die kunnen worden aangetroffen tijdens het ontwerpen, ontwikkelen en testen van DSC-resources.

