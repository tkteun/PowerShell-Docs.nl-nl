---
ms.date: 2017-06-12
author: eslesar
ms.topic: conceptual
keywords: DSC, powershell, configuratie, setup
title: Bron van het DSC-Script
ms.openlocfilehash: 81718de0b0c8463189e33e565dc9ff39692dbe8b
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 06/12/2017
---
# <a name="dsc-script-resource"></a>Bron van het DSC-Script

 
> Van toepassing op: Windows PowerShell 4.0, Windows PowerShell 5.0

De **Script** resource in Windows PowerShell Desired State Configuration (DSC) biedt een mechanisme voor het uitvoeren van Windows PowerShell-scriptblokken op de doelknooppunten. De `Script` resource heeft `GetScript`, `SetScript`, en `TestScript` eigenschappen. Deze eigenschappen moeten worden ingesteld op scriptblokken dat wordt uitgevoerd op elk doelknooppunt. 

De `GetScript` scriptblok als resultaat moet een hashtabel die vertegenwoordigt de status van het huidige knooppunt. De hash-tabel mag slechts één sleutelveld bevatten `Result` en de waarde moet van het type `String`. Het is niet vereist voor het resultaat opgeleverd. DSC geen reactie met de uitvoer van deze scriptblok.

De `TestScript` scriptblok moet bepalen of het huidige knooppunt moet worden gewijzigd. Er moet worden geretourneerd `$true` als het knooppunt bijgewerkt is. Er moet worden geretourneerd `$false` als de configuratie van het knooppunt verouderd is en moet worden bijgewerkt door de `SetScript` scriptblok. De `TestScript` scriptblok wordt aangeroepen door DSC.

De `SetScript` scriptblok het knooppunt moet wijzigen. Deze wordt aangeroepen door DSC als de `TestScript` blokkeren return `$false`.

Als u wilt gebruiken van variabelen uit het configuratiescript in de `GetScript`, `TestScript`, of `SetScript` scriptblokken, gebruikt u de `$using:` bereik (Zie hieronder voor een voorbeeld).


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

## <a name="properties"></a>Eigenschappen

|  Eigenschap  |  Beschrijving   | 
|---|---| 
| Ophalen script| Biedt een blok van Windows PowerShell-script dat wordt uitgevoerd wanneer u aanroept de [Get-DscConfiguration](https://technet.microsoft.com/en-us/library/dn407379.aspx) cmdlet. Dit blok moet een hashtabel retourneren. De hash-tabel mag slechts één sleutelveld bevatten **resultaat** en de waarde moet van het type **tekenreeks**.| 
| SetScript| Biedt een blok van Windows PowerShell-script. Wanneer u aanroept de [Start DscConfiguration](https://technet.microsoft.com/en-us/library/dn521623.aspx) -cmdlet de **TestScript** blok als eerste wordt gestart. Als de **TestScript** blokkeren retourneert **$false**, wordt de **SetScript** blok wordt uitgevoerd. Als de **TestScript** blokkeren retourneert **$true**, wordt de **SetScript** blok wordt niet uitgevoerd.| 
| TestScript| Biedt een blok van Windows PowerShell-script. Wanneer u aanroept de [Start DscConfiguration](https://technet.microsoft.com/en-us/library/dn521623.aspx) cmdlet dit blok wordt uitgevoerd. Als het resultaat **$false**, het blok SetScript wordt uitgevoerd. Als het resultaat **$true**, SetScript blok wordt niet uitgevoerd. De **TestScript** blok wordt ook uitgevoerd wanneer u aanroept de [Test DscConfiguration](https://technet.microsoft.com/en-us/library/dn407382.aspx) cmdlet. Echter, in dit geval de **SetScript** blok wordt niet uitgevoerd, ongeacht welke het TestScript waarde blokkeren retourneert. De **TestScript** blok moet True worden geretourneerd als de configuratie van de werkelijke overeenkomt met de huidige configuratie van de gewenste status en False als komt niet overeen met. (De huidige configuratie van de gewenste status is de laatste configuratie van kracht op het knooppunt dat van DSC gebruikmaakt.)| 
| referentie| Hiermee geeft u de referenties gebruiken om dit script uit te voeren als de referenties zijn vereist.| 
| dependsOn| Hiermee wordt aangegeven dat de configuratie van een andere resource uitvoeren moet voordat deze bron is geconfigureerd. Bijvoorbeeld, als de ID van de resourceconfiguratie scriptblok die u wilt uitvoeren eerst is **ResourceName** en het type **ResourceType**, de syntaxis voor het gebruik van deze eigenschap is `DependsOn = "[ResourceType]ResourceName"`.

## <a name="example-1"></a>Voorbeeld 1
```powershell
$version = Get-Content 'version.txt'

Configuration ScriptTest
{
    Import-DscResource –ModuleName 'PSDesiredStateConfiguration'

    Script ScriptExample
    {
        SetScript = 
        { 
            $sw = New-Object System.IO.StreamWriter("C:\TempFolder\TestFile.txt")
            $sw.WriteLine("Some sample string")
            $sw.Close()
        }
        TestScript = { Test-Path "C:\TempFolder\TestFile.txt" }
        GetScript = { @{ Result = (Get-Content C:\TempFolder\TestFile.txt) } }          
    }
}
```

## <a name="example-2"></a>Voorbeeld 2
```powershell
$version = Get-Content 'version.txt'

Configuration ScriptTest
{
    Import-DscResource –ModuleName 'PSDesiredStateConfiguration'

    Script UpdateConfigurationVersion
    {
        GetScript = { 
            $currentVersion = Get-Content (Join-Path -Path $env:SYSTEMDRIVE -ChildPath 'version.txt')
            return @{ 'Version' = "$currentVersion" }
        }          
        TestScript = { 
            $state = $GetScript
            if( $state['Version'] -eq $using:version )
            {
                Write-Verbose -Message ('{0} -eq {1}' -f $state['Version'],$using:version)
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
```

Deze bron is de versie van de configuratie naar een tekstbestand schrijven. Deze versie beschikbaar is op de clientcomputer, maar bevindt zich niet op een van de knooppunten, dus het moet worden doorgegeven aan elk van de `Script` scriptblokken van de resource met de PowerShell `using` bereik. Wanneer het genereren van het knooppunt MOF-bestand, de waarde van de `$version` variabele wordt gelezen uit een tekstbestand op de clientcomputer. DSC-vervangt de `$using:version` variabelen in elk script blokkeren met de waarde van de `$version` variabele.

