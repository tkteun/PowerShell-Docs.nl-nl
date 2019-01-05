---
ms.date: 08/24/2018
keywords: DSC, powershell, configuratie en installatie
title: Script voor DSC-Resource
ms.openlocfilehash: ef84239820a44aab2a028f7f0fe17653a851b72e
ms.sourcegitcommit: e04292a9c10de9a8391d529b7f7aa3753b362dbe
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 01/04/2019
ms.locfileid: "54048311"
---
# <a name="dsc-script-resource"></a>Script voor DSC-Resource

> Van toepassing op: Windows PowerShell 4.0, Windows PowerShell 5.x

De **Script** resource in Windows PowerShell Desired State Configuration (DSC) biedt een mechanisme voor het uitvoeren van Windows PowerShell-scriptblokken op doelknooppunten. De **Script** maakt gebruik van resource `GetScript`, `SetScript`, en `TestScript` -eigenschappen die u definieert om uit te voeren van de bijbehorende DSC scriptblokken bevatten status bewerkingen.

## <a name="syntax"></a>Syntaxis

```
Script [string] #ResourceName
{
    GetScript = [string]
    SetScript = [string]
    TestScript = [string]
    [ Credential = [PSCredential] ]
    [ DependsOn = [string[]] ]
}
```

> [!NOTE]
> De `GetScript`, `TestScript`, en `SetScript` blokken worden opgeslagen als tekenreeksen.

## <a name="properties"></a>Eigenschappen

|Eigenschap|Beschrijving|
|--------|-----------|
|Ophalen script|Een scriptblok waarmee de huidige status van het knooppunt wordt geretourneerd.|
|SetScript|Een scriptblok die DSC gebruikt voor het afdwingen van naleving bij het knooppunt niet is opgenomen in de gewenste status.|
|TestScript|Een scriptblok die bepaalt of het knooppunt in de gewenste status.|
|Referentie| Geeft aan dat de referenties wilt gebruiken voor het uitvoeren van dit script als referenties vereist zijn.|
|DependsOn| Geeft aan dat de configuratie van een andere resource uitvoeren moet voordat deze resource is geconfigureerd. Bijvoorbeeld, als de ID van de resourceconfiguratie scriptblok die u wilt uitvoeren eerst is **ResourceName** en het type **ResourceType**, de syntaxis voor het gebruik van deze eigenschap is `DependsOn = "[ResourceType]ResourceName"`.

### <a name="getscript"></a>Ophalen script

DSC maakt geen gebruik van de uitvoer van `GetScript`. De [Get-DscConfiguration](/powershell/module/PSDesiredStateConfiguration/Get-DscConfiguration) cmdlet voert de `GetScript` om op te halen van de huidige status van een knooppunt. Een retourwaarde hoeft niet uit `GetScript`. Als u een retourwaarde opgeeft, moet dit een `hashtable` met een **resultaat** sleutel waarvan de waarde is een `String`.

### <a name="testscript"></a>TestScript

De `TestScript` wordt uitgevoerd door DSC om te bepalen of de `SetScript` moet worden uitgevoerd. Als de `TestScript` retourneert `$false`, DSC wordt uitgevoerd de `SetScript` om het knooppunt terug naar de gewenste status. De App moet retourneren een `boolean` waarde. Een resultaat van `$true` geeft aan dat het knooppunt voldoet en `SetScript` moet niet worden uitgevoerd.

De [Test-DscConfiguration](/powershell/module/PSDesiredStateConfiguration/Test-DscConfiguration) -cmdlet voert de `TestScript` om op te halen van de naleving van de knooppunten van de **Script** resources. Echter, in dit geval de `SetScript` niet wordt uitgevoerd, ongeacht wat de `TestScript` retourneert blokkeren.

> [!NOTE]
> Alle uitvoer van uw `TestScript` maakt deel uit van de geretourneerde waarde. PowerShell interpreteert unsuppressed uitvoer als niet-nul, wat dat betekent uw `TestScript` retourneert `$true` , ongeacht de status van het knooppunt.
> Dit leidt tot onvoorspelbare resultaten, fout-positieven, en zorgt ervoor dat problemen tijdens het oplossen van problemen.

### <a name="setscript"></a>SetScript

De `SetScript` Hiermee wijzigt u het knooppunt enfore de gewenste status. Deze wordt aangeroepen door DSC als de `TestScript` script blok retourneert `$false`. De `SetScript` moet retourneren geen waarde hebben.

## <a name="examples"></a>Voorbeelden

### <a name="example-1-write-sample-text-using-a-script-resource"></a>Voorbeeld 1: Voorbeeldtekst met behulp van de bron van een Script schrijven

In dit voorbeeld test sprake is van `C:\TempFolder\TestFile.txt` op elk knooppunt. Als deze niet bestaat, wordt gemaakt met behulp van de `SetScript`. De `GetScript` retourneert de inhoud van het bestand en de geretourneerde waarde wordt niet gebruikt.

```powershell
Configuration ScriptTest
{
    Import-DscResource –ModuleName 'PSDesiredStateConfiguration'

    Node localhost
    {
        Script ScriptExample
        {
            SetScript = {
                $sw = New-Object System.IO.StreamWriter("C:\TempFolder\TestFile.txt")
                $sw.WriteLine("Some sample string")
                $sw.Close()
            }
            TestScript = { Test-Path "C:\TempFolder\TestFile.txt" }
            GetScript = { @{ Result = (Get-Content C:\TempFolder\TestFile.txt) } }
        }
    }
}
```

### <a name="example-2-compare-version-information-using-a-script-resource"></a>Voorbeeld 2: Versie-informatie met behulp van een bron van het Script vergelijken

In dit voorbeeld wordt de *compatibel* versie-informatie uit een tekstbestand op de computer ontwerpen en slaat deze op in de `$version` variabele. Bij het genereren van het knooppunt MOF-bestand, DSC vervangt de `$using:version` variabelen in elk script blokkeren met de waarde van de `$version` variabele. Tijdens de uitvoering, de *compatibel* versie is opgeslagen in een tekstbestand op elk knooppunt en vergeleken en op de volgende uitvoeringen worden bijgewerkt.

```powershell
$version = Get-Content 'version.txt'

Configuration ScriptTest
{
    Import-DscResource –ModuleName 'PSDesiredStateConfiguration'

    Node localhost
    {
        Script UpdateConfigurationVersion
        {
            GetScript = {
                $currentVersion = Get-Content (Join-Path -Path $env:SYSTEMDRIVE -ChildPath 'version.txt')
                return @{ 'Result' = "$currentVersion" }
            }
            TestScript = {
                # Create and invoke a scriptblock using the $GetScript automatic variable, which contains a string representation of the GetScript.
                $state = [scriptblock]::Create($GetScript).Invoke()

                if( $state['Result'] -eq $using:version )
                {
                    Write-Verbose -Message ('{0} -eq {1}' -f $state['Result'],$using:version)
                    return $true
                }
                Write-Verbose -Message ('Version up-to-date: {0}' -f $using:version)
                return $false
            }
            SetScript = {
                $using:version | Set-Content -Path (Join-Path -Path $env:SYSTEMDRIVE -ChildPath 'version.txt')
            }
        }
    }
}
```