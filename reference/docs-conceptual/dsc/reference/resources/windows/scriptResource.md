---
ms.date: 07/16/2020
keywords: DSC, Power shell, configuratie, installatie
title: DSC-script resource
ms.openlocfilehash: 9b89981c17e87b3681c6416c7dee44a75c432ea1
ms.sourcegitcommit: eb6a7c01e6385809656ac828b9211683e0b1a6fe
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 08/27/2020
ms.locfileid: "89041126"
---
# <a name="dsc-script-resource"></a>DSC-script resource

> Van toepassing op: Windows Power Shell 4,0, Windows Power shell 5. x

De `Script` resource in Windows Power shell desired state Configuration (DSC) biedt een mechanisme voor het uitvoeren van Windows Power shell-script blokken op doel knooppunten. De `Script` resource gebruikt `GetScript` 
 `SetScript` en `TestScript` eigenschappen die script blokken bevatten die u definieert om de bijbehorende DSC-status bewerkingen uit te voeren.

## <a name="syntax"></a>Syntax

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
> `GetScript``TestScript`en `SetScript` blokken worden opgeslagen als teken reeksen.

## <a name="properties"></a>Eigenschappen

|  Eigenschap  |                                          Beschrijving                                          |
| ---------- | --------------------------------------------------------------------------------------------- |
| GetScript  | Een script blok dat de huidige status van het knoop punt retourneert.                                    |
| SetScript  | Een script blok dat door DSC wordt gebruikt om naleving af te dwingen wanneer het knoop punt niet de gewenste status heeft. |
| TestScript | Een script blok dat bepaalt of het knoop punt de gewenste status heeft.                           |
| Referentie | Hiermee geeft u de referenties op die moeten worden gebruikt voor het uitvoeren van dit script, indien referenties vereist zijn.        |

## <a name="common-properties"></a>Algemene eigenschappen

|       Eigenschap       |                                            Beschrijving                                            |
| -------------------- | ------------------------------------------------------------------------------------------------- |
| DependsOn            | Geeft aan dat de configuratie van een andere bron moet worden uitgevoerd voordat deze resource wordt geconfigureerd. |
| PsDscRunAsCredential | Hiermee stelt u de referentie in voor het uitvoeren van de gehele resource als.                                           |

> [!NOTE]
> De algemene eigenschap **PsDscRunAsCredential** is toegevoegd aan WMF 5,0 om het uitvoeren van een DSC-resource in de context van andere referenties toe te staan. Zie [referenties gebruiken met DSC-resources](../../../configurations/runasuser.md)voor meer informatie.

### <a name="additional-information"></a>Aanvullende informatie

#### <a name="getscript"></a>GetScript

DSC maakt geen gebruik van de uitvoer van `GetScript` de cmdlet [Get-DscConfiguration](/powershell/module/PSDesiredStateConfiguration/Get-DscConfiguration) wordt uitgevoerd `GetScript` om de huidige status van een knoop punt op te halen. Een retour waarde is niet vereist `GetScript` Als u een retour waarde opgeeft, moet deze een hashtabel zijn met een **resultaat** sleutel waarvan de waarde een teken reeks is.

#### <a name="testscript"></a>TestScript

`TestScript` wordt uitgevoerd door DSC om te bepalen of het `SetScript` moet worden uitgevoerd. Als `TestScript` `$false` u retourneert, wordt DSC uitgevoerd `SetScript` om het knoop punt weer in de gewenste staat te brengen. Deze moet een Booleaanse waarde Retour neren. Een resultaat van `$true` geeft aan dat het knoop punt compatibel is en `SetScript` niet moet worden uitgevoerd.

De cmdlet [test-DscConfiguration](/powershell/module/PSDesiredStateConfiguration/Test-DscConfiguration) wordt uitgevoerd `TestScript` voor het ophalen van de knoop punten die voldoen aan de `Script` resources. In dit geval `SetScript` wordt echter niet uitgevoerd, ongeacht welk `TestScript` blok wordt geretourneerd.

> [!NOTE]
> Alle uitvoer van uw `TestScript` maakt deel uit van de geretourneerde waarde. Power shell interpreteert niet-onderdrukte uitvoer als niet-nul, wat betekent dat uw `TestScript` knoop punt wordt geretourneerd, `$true` ongeacht de staat van de node. Dit resulteert in onvoorspelbare resultaten, fout-positieven en veroorzaakt problemen tijdens het oplossen van problemen.

#### <a name="setscript"></a>SetScript

`SetScript` Hiermee wijzigt u het knoop punt om de gewenste status af te dwingen. Deze wordt aangeroepen door DSC als het `TestScript` script blok retourneert `$false` . De `SetScript` mag geen retour waarde hebben.

## <a name="examples"></a>Voorbeelden

### <a name="example-1-write-sample-text-using-a-script-resource"></a>Voor beeld 1: voorbeeld tekst schrijven met behulp van een script resource

In dit voor beeld wordt getest of `C:\TempFolder\TestFile.txt` op elk knoop punt bestaat. Als deze niet bestaat, wordt deze gemaakt met behulp van de `SetScript` . Het `GetScript` retourneert de inhoud van het bestand en de geretourneerde waarde wordt niet gebruikt.

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

In dit voor beeld worden de gegevens van de _compatibele_ versie opgehaald uit een tekst bestand op de ontwerp computer en opgeslagen in de `$version` variabele. Bij het genereren van het MOF-bestand van het knoop punt vervangt DSC de `$using:version` variabelen in elk script blok met de waarde van de `$version` variabele.
Tijdens de uitvoering wordt de _compatibele_ versie opgeslagen in een tekst bestand op elk knoop punt en vergeleken en bijgewerkt bij de volgende uitvoeringen.

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

                if( $state.Result -eq $using:version )
                {
                    Write-Verbose -Message ('{0} -eq {1}' -f $state.Result,$using:version)
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

### <a name="example-3-utilizing-parameters-in-a-script-resource"></a>Voor beeld 3: para meters gebruiken in een script bron

In dit voor beeld worden para meters uit de script resource geopend door het `using` bereik te gebruiken.
Houd er rekening mee dat **ConfigurationData** op een vergelijk bare manier kan worden benaderd. Net als voor beeld 2 wordt een versie naar verwachting opgeslagen in een lokaal bestand op het doel knooppunt. Zowel het pad naar het lokale bestand als de versie kunnen worden geconfigureerd, maar ook code uit configuratie gegevens ontkoppelen.

```powershell
Configuration ScriptTest
{
    param
    (
        [Version]
        $Version,

        [string]
        $FilePath
    )

    Import-DscResource -ModuleName 'PSDesiredStateConfiguration'

    Node localhost
    {
        Script UpdateConfigurationVersion
        {
            GetScript = {
                $currentVersion = Get-Content -Path $using:FilePath
                return @{ 'Result' = "$currentVersion" }
            }
            TestScript = {
                # Create and invoke a scriptblock using the $GetScript automatic variable, which contains a string representation of the GetScript.
                $state = [scriptblock]::Create($GetScript).Invoke()

                if( $state['Result'] -eq $using:Version )
                {
                    Write-Verbose -Message ('{0} -eq {1}' -f $state['Result'],$using:version)
                    return $true
                }

                Write-Verbose -Message ('Version up-to-date: {0}' -f $using:version)
                return $false
            }
            SetScript = {
                Set-Content -Path $using:FilePath -Value $using:Version
            }
        }
    }
}
```

Het resulterende MOF-bestand bevat de variabelen en hun waarden die worden geopend via het `using` bereik.
Ze worden toegevoegd aan elke script Block die gebruikmaakt van de variabelen. Testen en instellen van scripts zijn verwijderd voor de boog:

```Output
instance of MSFT_ScriptResource as $MSFT_ScriptResource1ref
{
 GetScript = "$FilePath ='C:\\Config.ini'\n\n $currentVersion = Get-Content -Path $FilePath\n return @{ 'Result' = \"$currentVersion\" }\n";
 TestScript = ...;
 SetScript = ...;
};
```

### <a name="known-limitations"></a>Bekende beperkingen

- Referenties die worden door gegeven binnen een script resource zijn niet altijd betrouwbaar wanneer een pull-of push server-model wordt gebruikt. Het is raadzaam om een volledige resource te gebruiken in plaats van een script bron in dit geval te gebruiken.
