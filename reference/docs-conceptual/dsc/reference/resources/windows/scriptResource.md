---
ms.date: 09/20/2019
keywords: DSC, Power shell, configuratie, installatie
title: DSC-script resource
ms.openlocfilehash: e09e86011fa7dbb2a4d7f28b5032b4328b6f6ec2
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 12/05/2019
ms.locfileid: "71941325"
---
# <a name="dsc-script-resource"></a>DSC-script resource

> Van toepassing op: Windows Power Shell 4,0, Windows Power shell 5. x

De **script** bron in Windows Power shell desired state Configuration (DSC) biedt een mechanisme voor het uitvoeren van Windows Power shell-script blokken op doel knooppunten. De **script** bron maakt gebruik van **GetScript**-, **SetScript**-en **TestScript** -eigenschappen die script blokken bevatten die u definieert om de bijbehorende DSC-status bewerkingen uit te voeren.

## <a name="syntax"></a>Syntaxis

```Syntax
Script [string] #ResourceName
{
    GetScript = [string]
    SetScript = [string]
    TestScript = [string]
    [ Credential = [PSCredential] ]
    [ DependsOn = [string[]] ]
    [ PsDscRunAsCredential = [PSCredential] ]
}
```

> [!NOTE]
> **GetScript**-, **TestScript**-en **SetScript** -blokken worden opgeslagen als teken reeksen.

## <a name="properties"></a>Eigenschappen

|Eigenschap |Beschrijving |
|---|---|
|GetScript |Een script blok dat de huidige status van het knoop punt retourneert. |
|SetScript |Een script blok dat door DSC wordt gebruikt om naleving af te dwingen wanneer het knoop punt niet de gewenste status heeft. |
|TestScript |Een script blok dat bepaalt of het knoop punt de gewenste status heeft. |
|Referentie |Hiermee geeft u de referenties op die moeten worden gebruikt voor het uitvoeren van dit script, indien referenties vereist zijn. |

## <a name="common-properties"></a>Algemene eigenschappen

|Eigenschap |Beschrijving |
|---|---|
|DependsOn |Geeft aan dat de configuratie van een andere bron moet worden uitgevoerd voordat deze resource wordt geconfigureerd. Als de ID van het resource-configuratie script blok dat u eerst wilt uitvoeren bijvoorbeeld de naam ResourceName is, en het type van de bron resource is, is de syntaxis voor het gebruik van deze eigenschap `DependsOn = "[ResourceType]ResourceName"`. |
|PsDscRunAsCredential |Hiermee stelt u de referentie in voor het uitvoeren van de gehele resource als. |

> [!NOTE]
> De algemene eigenschap **PsDscRunAsCredential** is toegevoegd aan WMF 5,0 om het uitvoeren van een DSC-resource in de context van andere referenties toe te staan. Zie [referenties gebruiken met DSC-resources](../../../configurations/runasuser.md)voor meer informatie.

### <a name="additional-information"></a>Meer informatie

#### <a name="getscript"></a>GetScript

DSC maakt geen gebruik van de uitvoer van **GetScript**. De cmdlet [Get-DscConfiguration](/powershell/module/PSDesiredStateConfiguration/Get-DscConfiguration) voert **GetScript** uit om de huidige status van een knoop punt op te halen. Er is geen retour waarde vereist vanuit **GetScript**. Als u een retour waarde opgeeft, moet deze een hashtabel zijn met een **resultaat** sleutel waarvan de waarde een teken reeks is.

#### <a name="testscript"></a>TestScript

**TestScript** wordt uitgevoerd door DSC om te bepalen of **SetScript** moet worden uitgevoerd. Als **TestScript** retourneert `$false`, voert DSC **SetScript** uit om het knoop punt weer in de gewenste staat te brengen. Deze moet een Booleaanse waarde Retour neren. Een resultaat van `$true` geeft aan dat het knoop punt compatibel is en dat **SetScript** niet moet worden uitgevoerd.

Met de cmdlet [test-DscConfiguration](/powershell/module/PSDesiredStateConfiguration/Test-DscConfiguration) wordt **TestScript** uitgevoerd om de knoop punten te verkrijgen die voldoen aan de **script** bronnen.
In dit geval wordt **SetScript** echter niet uitgevoerd, ongeacht welk **TestScript** Block retourneert.

> [!NOTE]
> Alle uitvoer van uw **TestScript** maakt deel uit van de geretourneerde waarde. Power shell interpreteert niet-onderdrukte uitvoer als niet-nul, wat betekent dat uw **TestScript** retour neren `$true`, ongeacht de status van uw knoop punt. Dit resulteert in onvoorspelbare resultaten, fout-positieven en veroorzaakt problemen tijdens het oplossen van problemen.

#### <a name="setscript"></a>SetScript

**SetScript** wijzigt het knoop punt om de gewenste status af te dwingen. Deze wordt aangeroepen door DSC als het **TestScript** -script blok `$false`retourneert. De **SetScript** mag geen retour waarde hebben.

## <a name="examples"></a>Voorbeelden

### <a name="example-1-write-sample-text-using-a-script-resource"></a>Voor beeld 1: voorbeeld tekst schrijven met behulp van een script resource

In dit voor beeld wordt getest op het bestaan van `C:\TempFolder\TestFile.txt` op elk knoop punt. Als deze niet bestaat, wordt deze gemaakt met behulp van de `SetScript`. De `GetScript` retourneert de inhoud van het bestand en de bijbehorende retour waarde wordt niet gebruikt.

```powershell
Configuration ScriptTest
{
    Import-DscResource -ModuleName 'PSDesiredStateConfiguration'

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

### <a name="example-2-compare-version-information-using-a-script-resource"></a>Voor beeld 2: versie-informatie vergelijken met een script resource

In dit voor beeld worden de gegevens van de *compatibele* versie opgehaald uit een tekst bestand op de ontwerp computer en opgeslagen in de variabele `$version`. Bij het genereren van het MOF-bestand van het knoop punt worden de `$using:version` variabelen in elk script blok vervangen door de waarde van de `$version` variabele.
Tijdens de uitvoering wordt de *compatibele* versie opgeslagen in een tekst bestand op elk knoop punt en vergeleken en bijgewerkt bij de volgende uitvoeringen.

```powershell
$version = Get-Content 'version.txt'

Configuration ScriptTest
{
    Import-DscResource -ModuleName 'PSDesiredStateConfiguration'

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