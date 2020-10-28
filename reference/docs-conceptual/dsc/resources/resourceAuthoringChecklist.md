---
ms.date: 07/08/2020
keywords: DSC, Power shell, configuratie, installatie
title: Controlelijst voor het ontwerpen van resource
description: Dit artikel bevat een controle lijst met aanbevolen procedures die moeten worden gebruikt bij het ontwerpen van een nieuwe DSC-resource.
ms.openlocfilehash: 5b618511f730c80104620c84e693c13ae4f536ac
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/27/2020
ms.locfileid: "92656340"
---
# <a name="resource-authoring-checklist"></a>Controlelijst voor het ontwerpen van resource

Deze controle lijst bevat de aanbevolen procedures voor het ontwerpen van een nieuwe DSC-resource.

## <a name="resource-module-contains-psd1-file-and-schemamof-for-every-resource"></a>De resource module bevat het. psd1-bestand en het schema. MOF voor elke resource

Controleer of de resource de juiste structuur heeft en alle vereiste bestanden bevat. Elke resource module moet een. psd1-bestand bevatten en elke niet-samengestelde resource moet het bestand schema. MOF hebben.
Resources die geen schema bevatten, worden niet weer gegeven door `Get-DscResource` en gebruikers kunnen de IntelliSense niet gebruiken bij het schrijven van code voor die modules in ISE. De directory-structuur voor de resource xRemoteFile, die deel uitmaakt van de [xPSDesiredStateConfiguration-resource module](https://github.com/PowerShell/xPSDesiredStateConfiguration), ziet er als volgt uit:

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

## <a name="resource-and-schema-are-correct"></a>De resource en het schema zijn juist

Controleer het resource schema `*.schema.mof` bestand (). U kunt de [DSC resource Designer](https://www.powershellgallery.com/packages/xDSCResourceDesigner/1.12.0.0) gebruiken om uw schema te ontwikkelen en te testen. Zorg voor het volgende:

- Eigenschaps typen zijn juist (bijvoorbeeld: geen teken reeks gebruiken voor eigenschappen die numerieke waarden accepteren, moet u in plaats daarvan UInt32 of andere numerieke typen gebruiken)
- Eigenschaps kenmerken zijn correct opgegeven als: ([sleutel], [vereist], [schrijven], [lezen])
- Ten minste één para meter in het schema moet worden gemarkeerd als [sleutel]
- de eigenschap [Read] bestaat niet samen met een van de volgende waarden: [vereist], [sleutel], [schrijven]
- Als er meerdere kwalificaties zijn opgegeven, behalve [lezen], heeft [sleutel] prioriteit
- Als [write] en [required] zijn opgegeven, is [required] prioriteit
- ValueMap wordt opgegeven, waar van toepassing voor beeld:

  ```
  [Read, ValueMap{"Present", "Absent"}, Values{"Present", "Absent"}, Description("Says whether DestinationPath exists on the machine")] String Ensure;
  ```

- Beschrijvende naam is opgegeven en wordt bevestigd aan DSC-naamgevings regels

  Voorbeeld: `[ClassVersion("1.0.0.0"), FriendlyName("xRemoteFile")]`

- Elk veld heeft een zinvolle beschrijving. De Power shell GitHub-opslag plaats heeft goede voor beelden, zoals het [. schema. MOF voor xRemoteFile](https://github.com/dsccommunity/xPSDesiredStateConfiguration/blob/master/source/DSCResources/DSC_xRemoteFile/DSC_xRemoteFile.schema.mof)

Daarnaast moet u `Test-xDscResource` `Test-xDscSchema` cmdlets van [DSC resource Designer](https://www.powershellgallery.com/packages/xDSCResourceDesigner/1.12.0.0) gebruiken om automatisch de resource en het schema te controleren:

```
Test-xDscResource <Resource_folder>
Test-xDscSchema <Path_to_resource_schema_file>
```

Bijvoorbeeld:

```powershell
Test-xDscResource ..\DSCResources\MSFT_xRemoteFile
Test-xDscSchema ..\DSCResources\MSFT_xRemoteFile\MSFT_xRemoteFile.schema.mof
```

## <a name="resource-loads-without-errors"></a>Resource belasting zonder fouten

Controleer of de resource module kan worden geladen. Dit kan hand matig worden bereikt door uit `Import-Module <resource_module> -force` te voeren en te bevestigen dat er geen fouten zijn opgetreden of door test Automation te schrijven. In het geval van de laatste kunt u deze structuur in uw test case volgen:

```powershell
$error = $null
Import-Module <resource_module> –force
If ($error.count –ne 0) {
    Throw "Module was not imported correctly. Errors returned: $error"
}
```

## <a name="resource-is-idempotent-in-the-positive-case"></a>De resource is in het positieve geval idempotent

Een van de fundamentele kenmerken van DSC-resources is idempotence. Het betekent dat het Toep assen van een DSC-configuratie met die resource meerdere keren altijd hetzelfde resultaat oplevert. Als we bijvoorbeeld een configuratie maken die de volgende bestands resource bevat:

```powershell
File file {
    DestinationPath = "C:\test\test.txt"
    Contents = "Sample text"
}
```

Nadat de toepassing voor de eerste keer is toegepast, moet de bestands test.txt worden weer gegeven in de `C:\test` map. Volgende uitvoeringen van dezelfde configuratie mogen echter niet de status van de machine wijzigen (bijvoorbeeld, er moeten geen kopieën van het `test.txt` bestand worden gemaakt). Om ervoor te zorgen dat een resource idempotent is, kunt u herhaaldelijk aanroepen `Set-TargetResource` Wanneer u de resource rechtstreeks test of `Start-DscConfiguration` meerdere keren aanroept wanneer u de test beëindigt. Het resultaat moet hetzelfde zijn na elke uitvoering.

## <a name="test-user-modification-scenario"></a>Scenario voor het aanpassen van gebruikers testen

Door de status van de machine te wijzigen en DSC opnieuw uit te voeren, kunt u controleren of `Set-TargetResource` en `Test-TargetResource` goed functioneren. Hier volgen de stappen die u moet uitvoeren:

1. Begin met de resource en niet de gewenste status.
1. Configuratie uitvoeren met uw resource
1. Verify `Test-DscConfiguration` retourneert True
1. Wijzig het geconfigureerde item in de gewenste status
1. Verify `Test-DscConfiguration` retourneert False

Hier volgt een meer concrete voor beeld van het gebruik van een register resource:

1. Beginnen met de register sleutel heeft niet de gewenste status
1. Voer uit `Start-DscConfiguration` met een configuratie om deze in de gewenste staat te zetten en controleer of deze wordt door gegeven.
1. Uitvoeren `Test-DscConfiguration` en controleren of het resultaat True retourneert
1. Wijzig de waarde van de sleutel zodat deze niet de gewenste status heeft
1. Uitvoeren `Test-DscConfiguration` en controleren of retourneert False
1. `Get-TargetResource` de functionaliteit is geverifieerd met `Get-DscConfiguration`

`Get-TargetResource` de details van de huidige status van de resource moeten worden geretourneerd. Zorg ervoor dat u deze test door aan te roepen `Get-DscConfiguration` nadat u de configuratie hebt toegepast en controleer of de uitvoer correct overeenkomt met de huidige status van de machine. Het is belang rijk om deze afzonderlijk te testen, omdat eventuele problemen in dit gebied niet worden weer gegeven wanneer u aanroept `Start-DscConfiguration` .

## <a name="call-getsettest-targetresource-functions-directly"></a>**Get/set/test-TargetResource-** functies rechtstreeks aanroepen

Zorg ervoor dat u de `Get/Set/Test-TargetResource` functies in uw Resource test door deze rechtstreeks aan te roepen en te controleren of ze werken zoals verwacht.

## <a name="verify-end-to-end-using-start-dscconfiguration"></a>End-to-end controleren met behulp van Start-DscConfiguration

`Get/Set/Test-TargetResource`Het is belang rijk om functies te testen door ze rechtstreeks aan te roepen, maar niet alle problemen worden op deze manier gedetecteerd. Het is belang rijk dat u zich richt op `Start-DscConfiguration` het gebruik of de pull-server. Dit is in feite hoe gebruikers de resource gaan gebruiken, dus te laag inschatten de significantie van dit type tests niet op. Mogelijke typen problemen:

- Referentie/sessie kan anders werken omdat de DSC-agent wordt uitgevoerd als een service. Zorg ervoor dat u alle functies hier kunt testen.
- Het resultaat van `Start-DscConfiguration` de uitvoer door kan afwijken van de fouten die worden weer gegeven wanneer u de `Set-TargetResource` functie rechtstreeks aanroept.

## <a name="test-compatibility-on-all-dsc-supported-platforms"></a>Test compatibiliteit op alle door DSC ondersteunde platforms

De resource moet werken op alle door DSC ondersteunde platforms (Windows Server 2008 R2 en nieuwer). Installeer de meest recente WMF (Windows Management Framework) in uw besturings systeem om de meest recente versie van DSC op te halen. Als uw resource niet op een aantal van deze platformen werkt, is het mogelijk dat er een specifiek fout bericht wordt geretourneerd. Zorg er ook voor dat uw resource controleert of cmdlets die u aanroept, aanwezig zijn op een bepaalde computer. Windows Server 2012 heeft een groot aantal nieuwe cmdlets toegevoegd die niet beschikbaar zijn in Windows Server 2008R2, zelfs niet als WMF is geïnstalleerd.

## <a name="verify-on-windows-client-if-applicable"></a>Controleren op Windows-client (indien van toepassing)

Een zeer veelvoorkomende test hiaat is het verifiëren van de bron alleen op Server versies van Windows. Veel resources zijn ook ontworpen om te werken met client-Sku's, dus als dat in uw geval waar is, vergeet dan niet om deze ook op deze platforms te testen.

## <a name="get-dscresource-lists-the-resource"></a>Get-DSCResource bevat de resource

Nadat u de module hebt geïmplementeerd, `Get-DscResource` moet u de resource onder andere aanroepen als gevolg van een lijst. Als u uw resource niet kunt vinden in de lijst, moet u ervoor zorgen dat het schema. MOF-bestand voor die bron bestaat.

## <a name="resource-module-contains-examples"></a>Resource module bevat voor beelden

Het maken van kwaliteits voorbeelden waarmee anderen inzicht krijgen in hoe u deze kunt gebruiken. Dit is cruciaal, vooral omdat veel gebruikers voorbeeld code behandelen als documentatie.

- Eerst moet u de voor beelden bepalen die in de module worden opgenomen. u moet mini maal de meest belang rijke use cases voor uw resource best rijken:
- Als uw module verschillende resources bevat die moeten samen werken voor een end-to-end-scenario, zou het Basic-end-to-end-voor beeld het eerst in het ideale geval moeten zijn.
- De eerste voor beelden zijn heel eenvoudig: hoe u aan de slag kunt gaan met uw resources in kleine, beheersbare segmenten (bijvoorbeeld het maken van een nieuwe VHD)
- De volgende voor beelden moeten worden gebouwd op basis van deze voor beelden (bijvoorbeeld het maken van een VM van een VHD, het verwijderen van de VM, het wijzigen van de virtuele machine) en het weer geven van geavanceerde functionaliteit (bijvoorbeeld het maken van een virtuele machine met dynamisch geheugen)
- Voorbeeld configuraties moeten worden para meters (alle waarden moeten worden door gegeven aan de configuratie als para meters en er mogen geen hardcoded waarden zijn):

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

- Het is een goed idee om een voor beeld van een invoeging van de configuratie met de werkelijke waarden aan het einde van het voorbeeld script uit te voeren. Zo is in de configuratie hierboven niet nood zakelijk duidelijk dat de beste manier om agents op te geven:

  `UserAgent = [Microsoft.PowerShell.Commands.PSUserAgent]::InternetExplorer` In dat geval kan een opmerking de beoogde uitvoering van de configuratie verduidelijken:

```powershell
<#
Sample use (parameter values need to be changed according to your scenario):

Sample_xRemoteFile_DownloadFile -destinationPath "$env:SystemDrive\fileName.jpg" -uri "http://www.contoso.com/image.jpg"

Sample_xRemoteFile_DownloadFile -destinationPath "$env:SystemDrive\fileName.jpg" -uri "http://www.contoso.com/image.jpg" `
-userAgent [Microsoft.PowerShell.Commands.PSUserAgent]::InternetExplorer -headers @{"Accept-Language" = "en-US"}
#>
```

- Voor elk voor beeld moet u een korte beschrijving schrijven waarin wordt uitgelegd wat het doet en wat de betekenis van de para meters zijn.
- Zorg ervoor dat de voor beelden de meeste belang rijke scenario's voor uw resource dekken. als er niets mis gaat, controleert u of ze alle computers in de gewenste status uitvoeren en plaatsen.

## <a name="error-messages-are-easy-to-understand-and-help-users-solve-problems"></a>Fout berichten zijn eenvoudig te begrijpen en helpen gebruikers problemen op te lossen

Goede fout berichten moeten zijn:

- Er is sprake van het grootste probleem met fout berichten dat ze vaak niet bestaan, dus zorg ervoor dat ze daar zijn.
- Eenvoudig te begrijpen: menselijk leesbaar, geen onduidelijke fout codes
- Nauw keurig: beschrijven wat het probleem precies is
- Feitelijke: advies over het oplossen van het probleem
- Vermoeden: liggen niet op de gebruiker of zorg ervoor dat ze slecht zijn

Controleer of u fouten in end-to-end-scenario's controleert (met `Start-DscConfiguration` ), omdat deze kunnen verschillen van de waarden die worden geretourneerd bij het rechtstreeks uitvoeren van resource functies.

## <a name="log-messages-are-easy-to-understand-and-informative-including-verbose-debug-and-etw-logs"></a>Logboek berichten zijn eenvoudig te begrijpen en info (inclusief – uitgebreid, fouten opsporen en ETW-Logboeken)

Zorg ervoor dat de logboeken die zijn gegenereerd door de resource eenvoudig te begrijpen zijn en waarde aan de gebruiker kunnen geven.
Resources moeten alle informatie uitvoeren die nuttig kan zijn voor de gebruiker, maar meer logboeken zijn niet altijd beter. Vermijd het gebruik van redundantie en het uitvoeren van gegevens die geen extra waarde bieden: laat iemand niet meer dan honderden logboek vermeldingen bezoeken om te vinden wat ze zoeken. Uiteraard is er geen logboeken die een geschikte oplossing voor dit probleem zijn.

Bij het testen moet u ook uitgebreide logboeken en fouten opsporen analyseren (door op de juiste wijze uit te voeren `Start-DscConfiguration` `–Verbose` en te `–Debug` scha kelen), evenals etw-Logboeken. Als u DSC ETW-logboeken wilt weer geven, gaat u naar Logboeken en opent u de volgende map: toepassingen en services-micro soft-Windows-desired state Configuration. Standaard zal er een operationeel kanaal zijn, maar zorg ervoor dat u analytische en probleemoplossings kanalen inschakelt voordat u de configuratie uitvoert. Als u kanalen voor analyse en fout opsporing wilt inschakelen, kunt u hieronder een script uitvoeren:

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

## <a name="resource-implementation-does-not-contain-hardcoded-paths"></a>De resource-implementatie bevat geen hardcoded paden

Zorg ervoor dat er geen hardcoded paden aanwezig zijn in de resource-implementatie, met name als er een taal (en-US) wordt gebruikt, of als er systeem variabelen zijn die u kunt gebruiken. Als uw resource toegang moet hebben tot specifieke paden, gebruikt u omgevings variabelen in plaats van hardcoding het pad, omdat het mogelijk op andere computers kan verschillen.

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

## <a name="resource-implementation-does-not-contain-user-information"></a>De resource-implementatie bevat geen gebruikers gegevens

Zorg ervoor dat er geen e-mail namen, account gegevens of namen van personen in de code zijn.

## <a name="resource-was-tested-with-validinvalid-credentials"></a>De resource is getest met geldige/ongeldige referenties

Als de resource een referentie als para meter heeft:

- Controleer of de resource werkt wanneer het lokale systeem (of het computer account voor externe bronnen) geen toegang heeft.
- Controleren of de resource werkt met een referentie die is opgegeven voor Get, set en test
- Als uw resource toegang heeft tot shares, test u alle varianten die u nodig hebt om te ondersteunen, zoals:
  - Standaard Windows-shares.
  - DFS-shares.
  - SAMBA-shares (als u Linux wilt ondersteunen.)

## <a name="resource-does-not-require-interactive-input"></a>Voor de resource is geen interactieve invoer vereist

`Get/Set/Test-TargetResource` functies moeten automatisch worden uitgevoerd en moeten niet wachten op invoer van de gebruiker tijdens een wille keurige fase (bijvoorbeeld omdat u niet `Get-Credential` in deze functies moet worden gebruikt). Als u de invoer van de gebruiker moet opgeven, moet u deze door geven aan de configuratie als para meter tijdens de compilatie fase.

## <a name="resource-functionality-was-thoroughly-tested"></a>De resource functionaliteit is uitgebreid getest

Deze controle lijst bevat items die belang rijk zijn om te worden getest en/of vaak ontbreekt. Er is een aantal tests, voornamelijk functionele functies die specifiek zijn voor de resource die u wilt testen en die hier niet worden vermeld. Vergeet niet om te zien wat negatieve test cases zijn.

## <a name="best-practice-resource-module-contains-tests-folder-with-resourcedesignertestsps1-script"></a>Best practice: de resource module bevat de map tests met ResourceDesignerTests.ps1 script

Het is een goed idee om de map ' tests ' te maken in de resource module, het bestand te maken `ResourceDesignerTests.ps1` en tests toe te voegen met `Test-xDscResource` en `Test-xDscSchema` voor alle resources in de betreffende module. Op deze manier kunt u snel schema's valideren van alle resources uit de opgegeven modules en een Sanity controleren voordat u publiceert. Voor xRemoteFile `ResourceTests.ps1` kan het er zo eenvoudig uitzien als:

```powershell
Test-xDscResource ..\DSCResources\MSFT_xRemoteFile
Test-xDscSchema ..\DSCResources\MSFT_xRemoteFile\MSFT_xRemoteFile.schema.mof
```

## <a name="best-practice-resource-supports--whatif"></a>Aanbevolen procedure: Resource ondersteunt-WhatIf

Als uw resource ' gevaarlijk ' bewerkingen uitvoert, is het een goed idee om functionaliteit te implementeren `-WhatIf` . Nadat de bewerking is uitgevoerd, moet u ervoor zorgen dat uitvoer op de `-WhatIf` juiste wijze bewerkingen beschrijft die zouden gebeuren als de opdracht zonder switch is voltooid `-WhatIf` . Controleer ook of de bewerkingen niet worden uitgevoerd (er worden geen wijzigingen aangebracht in de status van het knoop punt) wanneer `–WhatIf` Switch aanwezig is. Stel dat we de bestands resource testen. Hieronder vindt u eenvoudige configuratie waarmee bestanden `test.txt` met de inhoud ' test ' worden gemaakt:

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

Als we de configuratie met de switch compileren en vervolgens uitvoeren `-WhatIf` , vertelt de uitvoer precies wat er zou gebeuren wanneer de configuratie wordt uitgevoerd. De configuratie zelf is echter niet uitgevoerd (het `test.txt` bestand is niet gemaakt).

```powershell
Start-DscConfiguration -Path .\config -ComputerName localhost -Wait -Verbose -WhatIf
```

```Output
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

Deze lijst is niet volledig, maar hierin worden veel belang rijke problemen besproken die kunnen optreden tijdens het ontwerpen, ontwikkelen en testen van DSC-resources.
