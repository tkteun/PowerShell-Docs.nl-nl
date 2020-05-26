---
ms.date: 06/12/2017
keywords: wmf,powershell,installeren
title: Tracering en logboekregistratie voor scripts
ms.openlocfilehash: dd18453c041428d5a6537c413c3ebe324a62dfee
ms.sourcegitcommit: 2aec310ad0c0b048400cb56f6fa64c1e554c812a
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 05/23/2020
ms.locfileid: "83811196"
---
# <a name="script-tracing-and-logging"></a>Tracering en logboekregistratie voor scripts

Hoewel Power shell al over de groepsbeleid **LogPipelineExecutionDetails** -instelling beschikt voor het vastleggen van de aanroep van cmdlets, heeft de script taal van Power shell verschillende functies die u mogelijk wilt registreren en controleren. De nieuwe uitgebreide functie voor het traceren van scripts biedt gedetailleerde tracering en analyse van Power shell-script activiteit op een systeem. Nadat u gedetailleerde script tracering hebt ingeschakeld, worden alle script blokken in Power shell geregistreerd in het ETW-gebeurtenis logboek, **micro soft-Windows-Power shell/operationeel**. Als een script blok een ander script blok maakt, bijvoorbeeld door aanroepen `Invoke-Expression` , wordt het aangeroepen script blok ook vastgelegd.

Logboek registratie wordt ingeschakeld via de instelling **logboek registratie van Power shell-script blok inschakelen** Groepsbeleid in **Beheersjablonen**  ->  **Windows-onderdelen**  ->  **Windows Power shell**.

De gebeurtenissen zijn:

| Kanaal |                               Functioneren                               |
| ------- | ----------------------------------------------------------------------- |
| Niveau   | Verbose                                                                 |
| Code  | Maken                                                                  |
| Taak    | CommandStart                                                            |
| Zoek | Runs                                                                |
| Gebeurtenis | Engine_ScriptBlockCompiled (0x1008 = 4104)                              |
| Bericht | Script Block-tekst maken (%1 van %2): </br> %3 </br> Script Block-ID: %4 |

De Inge sloten tekst in het bericht is de omvang van het gecompileerde script blok. De ID is een GUID die wordt bewaard voor de levens duur van het script blok.

Als u uitgebreide logboek registratie inschakelt, schrijft de functie begin-en eind Markeringen:

| Kanaal |                                 Functioneren                                |
| ------- | -------------------------------------------------------------------------- |
| Niveau   | Verbose                                                                    |
| Code  | Openen/sluiten                                                               |
| Taak    | CommandStart / CommandStop                                                 |
| Zoek | Runs                                                                   |
| Gebeurtenis | Script Block \_ roep \_ Start \_ detail (0x1009 = 4105)/ </br> Script Block \_ aanroepen \_ volledige \_ Details (0x100A = 4106) |
| Bericht | Gestart/voltooide aanroep van script Block-ID: %1 </br> Runs Pace-ID: %2 |

De ID is de GUID die het script blok vertegenwoordigt (dat kan worden gecorreleerd met gebeurtenis-ID 0x1008) en de runs Pace-ID vertegenwoordigt de runs Pace waarin dit script blok is uitgevoerd.

Procent tekens in het aanroep bericht vertegenwoordigen Structured ETW-eigenschappen. Hoewel ze worden vervangen door de werkelijke waarden in de tekst van het bericht, is een krachtigere manier om ze te openen, het bericht op te halen met de cmdlet Get-Wine vent en vervolgens de **Eigenschappen** matrix van het bericht te gebruiken.

Hier volgt een voor beeld van hoe deze functionaliteit kan helpen bij het inpakken van een schadelijke poging om een script te versleutelen en af te schrijven:

```powershell
## Malware
function SuperDecrypt
{
    param($script)
    $bytes = [Convert]::FromBase64String($script)

    ## XOR "encryption"
    $xorKey = 0x42
    for($counter = 0; $counter -lt $bytes.Length; $counter++)
    {
        $bytes[$counter] = $bytes[$counter] -bxor $xorKey
    }
    [System.Text.Encoding]::Unicode.GetString($bytes)
}

$decrypted = SuperDecrypt "FUIwQitCNkInQm9CCkItQjFCNkJiQmVCEkI1QixCJkJlQg=="
Invoke-Expression $decrypted
```

Als u dit uitvoert, worden de volgende logboek vermeldingen gegenereerd:

```Output
Compiling Scriptblock text (1 of 1):
function SuperDecrypt
{
    param($script)
    $bytes = [Convert]::FromBase64String($script)
    ## XOR "encryption"
    $xorKey = 0x42
    for($counter = 0; $counter -lt $bytes.Length; $counter++)
    {
        $bytes[$counter] = $bytes[$counter] -bxor $xorKey
    }
    [System.Text.Encoding]::Unicode.GetString($bytes)

}
ScriptBlock ID: ad8ae740-1f33-42aa-8dfc-1314411877e3

Compiling Scriptblock text (1 of 1):
$decrypted = SuperDecrypt "FUIwQitCNkInQm9CCkItQjFCNkJiQmVCEkI1QixCJkJlQg=="
ScriptBlock ID: ba11c155-d34c-4004-88e3-6502ecb50f52

Compiling Scriptblock text (1 of 1):
Invoke-Expression $decrypted
ScriptBlock ID: 856c01ca-85d7-4989-b47f-e6a09ee4eeb3

Compiling Scriptblock text (1 of 1):
Write-Host 'Pwnd'
ScriptBlock ID: 5e618414-4e77-48e3-8f65-9a863f54b4c8
```

Als de lengte van het script blok de capaciteit van één gebeurtenis overschrijdt, wordt het script door Power shell in meerdere delen opgesplitst. Hier volgt een voorbeeld code voor het opnieuw combi neren van een script uit de logboek berichten:

```powershell
$created = Get-WinEvent -FilterHashtable @{ ProviderName="Microsoft-Windows-PowerShell"; Id = 4104 } |
  Where-Object { $_.<...> }
$sortedScripts = $created | sort { $_.Properties[0].Value }
$mergedScript = -join ($sortedScripts | % { $_.Properties[2].Value })
```

Net als bij alle logboek registratie systemen die een beperkte Bewaar buffer hebben, is een manier om deze infra structuur aan te vallen, het logboek te flooden met onlogische gebeurtenissen om eerdere bewijzen te verbergen. Als u van deze aanval wilt beveiligen, moet u ervoor zorgen dat u een vorm van de verzameling gebeurtenis Logboeken hebt voor het door sturen van Windows-gebeurtenissen. Zie [herkennen de kwaadwillende persoon met Windows-gebeurtenis logboek bewaking](https://apps.nsa.gov/iaarchive/library/reports/spotting-the-adversary-with-windows-event-log-monitoring.cfm)voor meer informatie.
