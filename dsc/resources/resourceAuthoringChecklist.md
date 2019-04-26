---
ms.date: 06/12/2017
keywords: DSC, powershell, configuratie en installatie
title: Controlelijst voor het ontwerpen van resource
ms.openlocfilehash: 7b1a096bba1b729c096b6689178ee022e12e4634
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62076579"
---
# <a name="resource-authoring-checklist"></a>Controlelijst voor het ontwerpen van resource

Deze controlelijst is een lijst met aanbevolen procedures bij het ontwerpen van een nieuwe DSC-Resource.

## <a name="resource-module-contains-psd1-file-and-schemamof-for-every-resource"></a>Resource-module bevat .psd1-bestand en schema.mof voor elke resource

Controleer of de bron de juiste structuur heeft en alle vereiste bestanden bevat. Elke resource-module een .psd1-bestand moet bevatten en elke niet-samengestelde resource schema.mof bestand moet hebben. Resources die geen schema bevatten, niet worden weergegeven door `Get-DscResource` en gebruikers niet mogelijk de intellisense gebruiken bij het schrijven van code op basis van deze modules in ISE.
De mapstructuur voor xRemoteFile resource, die deel uitmaakt van de [xPSDesiredStateConfiguration resource module](https://github.com/PowerShell/xPSDesiredStateConfiguration), ziet er als volgt uit:

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

## <a name="resource-and-schema-are-correct"></a>Bron en het schema zijn juist

Controleer of de resource-schema (*. schema.mof) bestand. U kunt de [Designer voor DSC-Resource](https://www.powershellgallery.com/packages/xDSCResourceDesigner/1.12.0.0) voor het ontwikkelen en testen van uw schema.
Zorg ervoor dat:

- Typen eigenschappen voor correct zijn (bijvoorbeeld tekenreeks niet gebruiken voor eigenschappen die numerieke waarden accepteert, moet u UInt32 of andere numerieke typen in plaats daarvan)
- Eigenschapskenmerken correct zijn opgegeven als: ([-toets], [vereist], [schrijven], [lezen])
- Ten minste één parameter in het schema moet worden gemarkeerd als [-toets]
- [meer] eigenschap niet samen voorkomen, samen met een van: (vereist), [key], [schrijven]
- Als meerdere kwalificaties zijn opgegeven, met uitzondering [lezen], klikt u vervolgens prioriteit]
- Als [schrijven] en [vereist] zijn opgegeven, wordt heeft een hogere prioriteit (vereist)
- ValueMap is opgegeven voorbeeld indien van toepassing:

  ```
  [Read, ValueMap{"Present", "Absent"}, Values{"Present", "Absent"}, Description("Says whether DestinationPath exists on the machine")] String Ensure;
  ```

- Beschrijvende naam is opgegeven en wordt bevestigd dat aan de naamgevingsconventies DSC

  Voorbeeld: `[ClassVersion("1.0.0.0"), FriendlyName("xRemoteFile")]`

- Elk veld heeft een duidelijke beschrijving. De PowerShell-GitHub-opslagplaats is een goede voorbeelden zoals [de. schema.mof voor xRemoteFile](https://github.com/PowerShell/xPSDesiredStateConfiguration/blob/dev/DSCResources/MSFT_xRemoteFile/MSFT_xRemoteFile.schema.mof)

Bovendien moet u **Test xDscResource** en **Test xDscSchema** -cmdlets van [Designer voor DSC-Resource](https://www.powershellgallery.com/packages/xDSCResourceDesigner/1.12.0.0) automatisch te controleren of de bron en het schema:

```
Test-xDscResource <Resource_folder>
Test-xDscSchema <Path_to_resource_schema_file>
```

Bijvoorbeeld:

```powershell
Test-xDscResource ..\DSCResources\MSFT_xRemoteFile
Test-xDscSchema ..\DSCResources\MSFT_xRemoteFile\MSFT_xRemoteFile.schema.mof
```

## <a name="resource-loads-without-errors"></a>Resource zonder fouten wordt geladen

Controleer of de resource-module is kan worden geladen.
Dit kan handmatig worden bereikt door het uitvoeren van `Import-Module <resource_module> -force` en bevestigen dat er geen fouten zijn opgetreden, of door schrijven test automation. U kunt deze structuur in uw testscenario volgen in het geval van de laatste:

```powershell
$error = $null
Import-Module <resource_module> –force
If ($error.count –ne 0) {
    Throw “Module was not imported correctly. Errors returned: $error”
}
```

## <a name="resource-is-idempotent-in-the-positive-case"></a>Resource is idempotent zijn in het geval is positief

Een van de basiskenmerken van DSC-resources is idempotence. Dit betekent dat het toepassen van een DSC-configuratie met die bron meerdere keren wordt altijd hetzelfde resultaat bereiken. Bijvoorbeeld, als we een configuratie waarin de resource van het volgende bestand maken:

```powershell
File file {
    DestinationPath = "C:\test\test.txt"
    Contents = "Sample text"
}
```

Na het toepassen van deze voor de eerste keer, bestand test.txt, moet worden weergegeven in `C:\test` map. Volgende uitvoeringen van dezelfde configuratie moeten echter niet wijzigen de status van de machine (bijvoorbeeld geen kopieën van de `test.txt` -bestand moet worden gemaakt).
Om te controleren of een resource is idempotent zijn, kunt u herhaaldelijk aanroepen `Set-TargetResource` bij het testen van de resource direct of bel `Start-DscConfiguration` meerdere keren bij het maken van end-to-end-testen. Het resultaat moet hetzelfde na elke uitvoering.

## <a name="test-user-modification-scenario"></a>Testscenario gebruiker wijzigen

Door het wijzigen van de status van de machine en vervolgens opnieuw uit te voeren DSC, kunt u controleren of `Set-TargetResource` en `Test-TargetResource` laten functioneren. Hier vindt u stappen die u moet uitvoeren:

1. Beginnen met de resource niet in de gewenste status.
2. Configuratie uitvoeren met de resource
3. Controleer of `Test-DscConfiguration` resulteert in waar
4. Wijzigen van de geconfigureerde item om te worden uit de gewenste status
5. Controleer of `Test-DscConfiguration` retourneert ' false '

Hier volgt een meer concrete voorbeeld met behulp van registerresource:

1. Beginnen met de registersleutel niet in de gewenste status
2. Voer `Start-DscConfiguration` met een configuratie plaatst deze in de gewenste status en controleer of deze is geslaagd.
3. Voer `Test-DscConfiguration` en controleer of deze retourneert ' True '
4. De waarde van de sleutel wijzigen zodat deze zich niet in de gewenste status
5. Voer `Test-DscConfiguration` en controleer of het resultaat false
6. `Get-TargetResource` functionaliteit is geverifieerd met behulp van `Get-DscConfiguration`

`Get-TargetResource` details van de huidige status van de resource moet worden geretourneerd. Zorg ervoor dat u deze testen door het aanroepen van `Get-DscConfiguration` nadat u de configuratie toepassen en verifiëren die correct uitvoer de huidige status van de machine geeft. Het is belangrijk dat de afzonderlijk testen omdat eventuele problemen op dit gebied wordt niet weergegeven bij het aanroepen van `Start-DscConfiguration`.

## <a name="call-getsettest-targetresource-functions-directly"></a>Bel **Get/Set/Test-TargetResource** rechtstreeks functies

Zorg ervoor dat u test de **Get/Set/Test-TargetResource** functies die zijn geïmplementeerd in uw resource door ze voor het rechtstreeks aanroepen en verifiëren dat ze werken zoals verwacht.

## <a name="verify-end-to-end-using-start-dscconfiguration"></a>Controleer of met behulp van End-to-End **Start-DscConfiguration**

Testen **Get/Set/Test-TargetResource** functies door ze rechtstreeks aan te roepen is belangrijk, maar niet alle problemen op deze manier worden gedetecteerd. U moet erop zijn gericht aanzienlijk deel van de controle over het gebruik van `Start-DscConfiguration` of de pull-server. Dit is in feite hoe gebruikers de resource, zodat de betekenis van dit type tests Onderschat niet wordt gebruikt.
Mogelijke typen problemen:

- Referentie/sessie mogelijk anders werken omdat de DSC-agent wordt uitgevoerd als een service.  Zorg ervoor dat testen functies hier end-to-end.
- Fouten uitvoeren door `Start-DscConfiguration` mogelijk anders dan die worden weergegeven bij het aanroepen van de `Set-TargetResource` rechtstreeks werken.

## <a name="test-compatability-on-all-dsc-supported-platforms"></a>Ondersteunde platforms voor test-compatibiliteit op alle DSC

Resource moet werken op alle DSC ondersteunde platforms (Windows Server 2008 R2 en hoger). Installeer de meest recente WMF (Windows Management Framework) van het besturingssysteem naar de meest recente versie van DSC. Als uw resource standaard niet op sommige van deze platformen werkt, kan een specifiek foutbericht moet worden geretourneerd. Zorg er ook dat uw resource controleert of de cmdlets die u aanroept op bepaalde machine aanwezig zijn. Windows Server 2012 toegevoegd een groot aantal nieuwe cmdlets die niet beschikbaar op Windows Server 2008R2, zelfs met WMF is geïnstalleerd zijn.

## <a name="verify-on-windows-client-if-applicable"></a>Controleer of op Windows-Client (indien van toepassing)

Een heel normaal test tussenruimte met het controleren van de resource alleen op server-versies van Windows. Veel resources ook zijn ontworpen om te werken op Client-SKU's, dus als dat is waar in uw geval, vergeet dan niet om dit te testen op deze platforms ook.

## <a name="get-dscresource-lists-the-resource"></a>Sleutelwoorden Get-dscresource bieden geeft een lijst van de resource

Na de implementatie van de module aanroepen `Get-DscResource` uw resource onder andere als gevolg hiervan moet weergeven. Als u de resource niet in de lijst vinden, ervoor zorgen dat bestand schema.mof voor die bron bestaat.

## <a name="resource-module-contains-examples"></a>Resource-module bevat voorbeelden

Het maken van het kwaliteitsvoorbeelden waarmee anderen te begrijpen hoe u deze. Dit is essentieel, met name omdat veel gebruikers voorbeeldcode als documentatie behandelen.

- Eerst moet u de voorbeelden die wordt opgenomen met de module: ten minste bepalen, moet u belangrijkste use-cases dekking voor uw resource:
- Als uw module verschillende bronnen die nodig is om samen te werken voor een end-to-end-scenario bevat, zou de eenvoudige end-to-end-voorbeeld in het ideale geval eerste.
- De eerste voorbeelden zeer eenvoudig--moeten zijn aan de slag met uw resources in kleine beheerbare segmenten (bijvoorbeeld het maken van een nieuwe VHD)
- Opeenvolgende voorbeelden te bouwen op deze voorbeelden (bijvoorbeeld een virtuele machine maken vanaf een VHD, VM, het wijzigen van de virtuele machine verwijderen) en geavanceerde functionaliteit (bijvoorbeeld een virtuele machine maken met het dynamisch geheugen)
- Van de voorbeeldconfiguraties als parameters moeten worden gebruikt (alle waarden moeten worden doorgegeven aan de configuratie als parameters en er mag geen waarden vastgelegd):

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

- Het is raadzaam om op te nemen (opmerkingen van) voorbeeld van hoe u de configuratie met de werkelijke waarden aan het einde van de voorbeeld-script aanroept.
  Bijvoorbeeld, in de bovenstaande configuratie is niet altijd duidelijk dat de beste manier om op te geven van de UserAgent is:

  `UserAgent = [Microsoft.PowerShell.Commands.PSUserAgent]::InternetExplorer` Een opmerking kunt in dat geval de beoogde uitvoering van de configuratie te verduidelijken:

  ```powershell
  <#
  Sample use (parameter values need to be changed according to your scenario):

  Sample_xRemoteFile_DownloadFile -destinationPath "$env:SystemDrive\fileName.jpg" -uri "http://www.contoso.com/image.jpg"

  Sample_xRemoteFile_DownloadFile -destinationPath "$env:SystemDrive\fileName.jpg" -uri "http://www.contoso.com/image.jpg" `
  -userAgent [Microsoft.PowerShell.Commands.PSUserAgent]::InternetExplorer -headers @{"Accept-Language" = "en-US"}
  #>
  ```

- Voor elk voorbeeld een korte beschrijving waarin wordt uitgelegd wat het doet en de betekenis van de parameters te schrijven.
- Zorg ervoor dat de voorbeelden voor de meeste belangrijke scenario's voor uw resource en als er niets ontbreekt, Controleer of ze al worden uitgevoerd en machine in de gewenste status geplaatst.

## <a name="error-messages-are-easy-to-understand-and-help-users-solve-problems"></a>Foutberichten zijn eenvoudig te begrijpen en oplossen van problemen met gebruikers helpen

Goede foutberichten moeten worden:

- Er zijn: Het grootste probleem met foutberichten is dat ze vaak niet bestaan, dus zorg ervoor dat ze zijn er.
- Gemakkelijk te begrijpen: Mens leesbaar, niet verborgen foutcodes
- Nauwkeurige: Wat is er precies het probleem beschrijven
- Feitelijke: Advies over het oplossen van het probleem
- Beleefd: Geen gebruiker zal of zodat ze ongeldige denkt

Zorg ervoor dat u fouten in de End-to-End scenario's controleren (met behulp van `Start-DscConfiguration`), omdat ze van die afwijken kunnen bij het uitvoeren van functies van resource rechtstreeks geretourneerd.

## <a name="log-messages-are-easy-to-understand-and-informative-including-verbose-debug-and-etw-logs"></a>Logboekberichten zijn gemakkelijk te begrijpen en informatieve (inclusief-verbose,-foutopsporing en ETW-Logboeken)

Zorg ervoor dat logboeken gegenereerd door de resource die eenvoudig te begrijpen en geef de waarde voor de gebruiker. Resources moeten alle informatie die nuttig voor de gebruiker zijn kan uitvoeren, maar meer logboeken is niet altijd beter. U moet voorkomen van redundantie en gegevens die niet worden uitgevoerd bieden een extra waarde: iemand anders gaat u door de honderden logboekvermeldingen om te zoeken wat ze zoekt niet maken. Er zijn geen logboeken is natuurlijk niet een aanvaardbare oplossing voor dit probleem ofwel.

Wanneer u test, u moet ook uitgebreide analyseren en fouten opsporen in Logboeken (door het uitvoeren van `Start-DscConfiguration` met `–Verbose` en `–Debug` op de juiste wijze verandert), ook als ETW-Logboeken. DSC-ETW-logboeken bekijken, gaat u naar Logboeken en opent u de volgende map: Applications and Services- Microsoft - Windows - Desired State Configuration.  Er standaard worden operationele kanaal, maar zorg ervoor dat u inschakelt analytische en foutopsporing van kanalen voordat de configuratie wordt uitgevoerd.
Om in te schakelen analytische/Debug kanalen, kunt u onderstaande script uitvoeren:

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

## <a name="resource-implementation-does-not-contain-hardcoded-paths"></a>Resource-implementatie bevat geen vastgelegd paden

Zorg ervoor dat er zijn geen paden vastgelegd in de resource-implementatie, met name als ze gaan ervan uit taal (en-us), of wanneer er systeemvariabelen die kunnen worden gebruikt.
Als de bron nodig hebt voor toegang tot specifieke paden, omgevingsvariabelen gebruiken in plaats van hardcoderen het pad, omdat dit anders op andere computers zijn kan.

Voorbeeld:

In plaats van:

```powershell
$tempPath = "C:\Users\kkaczma\AppData\Local\Temp\MyResource"
$programFilesPath = "C:\Program Files (x86)"
```

U kunt schrijven:

```powershell
$tempPath = Join-Path $env:temp "MyResource"
$programFilesPath = ${env:ProgramFiles(x86)}
```

## <a name="resource-implementation-does-not-contain-user-information"></a>Resource-implementatie bevatten geen gebruikersgegevens

Zorg ervoor dat er zijn geen e-namen, accountgegevens of namen van personen in de code.

## <a name="resource-was-tested-with-validinvalid-credentials"></a>Resource is getest met de referenties geldig/ongeldig

Als de resource een referentie als parameter:

- Controleer of de resource-werkt als lokaal systeem (of het computeraccount voor de externe bronnen) heeft geen toegang.
- Controleer of de resource werkt met een referentie opgegeven voor ophalen, instellen en testen
- Als uw resource toegang heeft tot de shares, test u alle varianten die u ondersteunen wilt, zoals:
  - Standaard windows-shares.
  - DFS-shares.
  - SAMBA-shares (als u ondersteuning voor Linux.)

## <a name="resource-does-not-require-interactive-input"></a>Resource is niet vereist voor interactieve invoer

**Get/Set/Test-TargetResource** functies automatisch moet worden uitgevoerd en moet u niet wachten voor de invoer van gebruiker tijdens elke fase van de uitvoering (bijv. Gebruik geen `Get-Credential` binnen deze functies). Als u nodig hebt voor de invoer van gebruiker, moet u deze doorgeven aan de configuratie als parameter tijdens de compilatie-fase.

## <a name="resource-functionality-was-thoroughly-tested"></a>Resourcefunctionaliteit is uitgebreid getest.

Deze controlelijst bevat de items die zijn belangrijk om te worden getest en/of vaak zijn gemist. Er is aantal tests, voornamelijk functionele labels die specifiek zijn voor de resource die u wilt testen en niet hier worden vermeld. Vergeet niet over negatieve Testscenario's.

## <a name="best-practice-resource-module-contains-tests-folder-with-resourcedesignertestsps1-script"></a>Aanbevolen: Resource-module bevat de map Tests met ResourceDesignerTests.ps1 script

Het is raadzaam om te maken van de map 'Test' in resource-module, maken `ResourceDesignerTests.ps1` bestand en voeg toe met behulp van tests **Test xDscResource** en **Test xDscSchema** voor alle resources in bepaalde module.
Op deze manier kunt u snel schema's van alle resources uit het opgegeven modules en voert u een sanity controleren voordat u publiceert valideren.
Voor xRemoteFile, `ResourceTests.ps1` kan net zo eenvoudig als zoeken:

```powershell
Test-xDscResource ..\DSCResources\MSFT_xRemoteFile
Test-xDscSchema ..\DSCResources\MSFT_xRemoteFile\MSFT_xRemoteFile.schema.mof
```

## <a name="best-practice-resource-folder-contains-resource-designer-script-for-generating-schema"></a>Aanbevolen: Resource-map bevat de ontwerperscript resource voor het genereren van schema

Elke bron moet een resource designer script een mof-schema van de resource genereert bevatten. Dit bestand moet worden geplaatst `<ResourceName>\ResourceDesignerScripts` en de naam genereren `<ResourceName>Schema.ps1` voor xRemoteFile resource dit bestand kan worden aangeroepen `GenerateXRemoteFileSchema.ps1` en bevatten:

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

## <a name="best-practice-resource-supports--whatif"></a>Aanbevolen: Resource ondersteunt - WhatIf

Als uw resource 'gevaarlijke' bewerkingen uitvoert, is het raadzaam om te implementeren `-WhatIf` functionaliteit. Nadat dit voltooid, controleert u of `-WhatIf` uitvoer beschrijft correct bewerkingen die er gebeuren zou als de opdracht is uitgevoerd zonder `-WhatIf` overschakelen.
Controleer ook of bewerkingen wordt niet uitgevoerd (de status van het knooppunt worden niet gewijzigd) als `–WhatIf` switch aanwezig is.
Bijvoorbeeld, Stel dat we bestandsresource test. Hieronder vindt u eenvoudige configuratie die zorgt voor bestand `test.txt` met inhoud van 'test':

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

Als we compileren en uitvoeren van de configuratie met de `-WhatIf` switch, de uitvoer is laat ons weten dat precies wat gebeurt er wanneer we de configuratie uitvoert. Tot wel is niet worden uitgevoerd door de configuratie zelf (`test.txt` bestand is niet gemaakt).

```powershell
Start-DscConfiguration -Path .\config -ComputerName localhost -Wait -Verbose -WhatIf
```

```output
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

Deze lijst is niet volledig, maar het geeft veel belangrijke problemen die kunnen worden aangetroffen tijdens het ontwerpen, ontwikkelen en testen van DSC-resources.
