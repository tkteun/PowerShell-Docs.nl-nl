---
ms.date: 06/12/2017
author: JKeithB
ms.topic: reference
keywords: wmf,powershell,installeren
ms.openlocfilehash: b440ea4a8208d5c576fa566a19e2de377bf5f475
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 04/09/2018
---
# <a name="script-tracing-and-logging"></a>Tracering en logboekregistratie voor scripts

Terwijl Windows PowerShell al heeft het **LogPipelineExecutionDetails** Groepsbeleid van PowerShell-scripttaal instellen voor het aanroepen van cmdlets melden, heeft veel functies die u kunt zich aanmelden en controleren. De nieuwe functie voor gedetailleerde tracering van Script stelt u gedetailleerde bijhouden en analyseren van Windows PowerShell scripts gebruiken op een systeem. Nadat u gedetailleerde script tracering ingeschakeld, Windows PowerShell alle scriptblokken registreert in het gebeurtenislogboek ETW **Microsoft-Windows-PowerShell/operationeel**. Als een scriptblok maakt een ander scriptblok (bijvoorbeeld een script waarmee de cmdlet Invoke-Expression op een tekenreeks aangeroepen), wordt die resulterende scriptblok wordt ook vastgelegd.

Registreren van deze gebeurtenissen kan worden ingeschakeld via de **schakelt logboekregistratie van PowerShell-Script blok** instelling voor Groepsbeleid (in Beheersjablonen -> Windows-onderdelen -> Windows PowerShell).

De gebeurtenissen zijn:

| Kanaal | Operationele                                 |
|---------|---------------------------------------------|
| Niveau   | Verbose                                     |
| Opcode  | Maken                                      |
| Taak    | CommandStart                                |
| Sleutelwoord | Runspace                                    |
| Gebeurtenis-id | Engine_ScriptBlockCompiled (0x1008 = 4104)  |
| Bericht | Het maken van Scriptblock tekst (%1 van %2): </br> %3 </br> ScriptBlock-ID: %4 |


De tekst die is ingesloten in het bericht is de omvang van het scriptblok gecompileerd. De ID is een GUID die de levensduur van het scriptblok wordt bewaard.

Wanneer u uitgebreide logboekregistratie inschakelt, wordt de functie voor schrijfbewerkingen beginnen en eindigen markeringen:

| Kanaal | Operationele                                            |
|---------|--------------------------------------------------------|
| Niveau   | Verbose                                                |
| Opcode  | Open (/ sluiten)                                         |
| Taak    | CommandStart (/ CommandStop)                           |
| Sleutelwoord | Runspace                                               |
| Gebeurtenis-id | ScriptBlock\_aanroepen\_Start\_Detail (0x1009 = 4105) / </br> ScriptBlock\_aanroepen\_voltooid\_Detail (0x100A = 4106) |
| Bericht | Gestarte (/ voltooide)-aanroep van ScriptBlock-ID: %1 </br> Runspace-ID: %2 |

De ID is de GUID die vertegenwoordigt het scriptblok (die kan worden gecorreleerd met gebeurtenis-ID 0x1008) en de Runspace-ID vertegenwoordigt de runspace op waarin dit scriptblok is uitgevoerd.

Procenttekens in het bericht het aanroepen van vertegenwoordigen gestructureerde ETW-eigenschappen. Terwijl ze worden vervangen door de werkelijke waarden in de berichttekst, een krachtigere manier toegang tot deze worden opgehaald van het bericht met de cmdlet Get-WinEvent en gebruik vervolgens de **eigenschappen** matrix van het bericht.

Hier volgt een voorbeeld van hoe deze functie uitpakken een schadelijke poging kunt voor het versleutelen en verbergen, een script weergeven:

```powershell
## Malware
function SuperDecrypt
{
    param($script)
    $bytes = [Convert]::FromBase64String($script)

    ## XOR “encryption”
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

Dit uitgevoerd, wordt de volgende logboekvermeldingen gegenereerd:

```
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

Windows PowerShell verbroken als het script bloklengte groter is dan wat ETW is geschikt voor bedrijf in één gebeurtenis, het script in meerdere delen. Hier volgt voorbeeldcode voor een script van de berichten in het logboek elke:

```powershell
$created = Get-WinEvent -FilterHashtable @{ ProviderName="Microsoft-Windows-PowerShell"; Id = 4104 } | Where-Object { $_.<...> }
$sortedScripts = $created | sort { $_.Properties[0].Value }
$mergedScript = -join ($sortedScripts | % { $_.Properties[2].Value })
```

Net als bij alle logboekregistratie systemen waarvoor een buffer beperkt bewaren (dat wil zeggen ETW-Logboeken) is een aanval op deze infrastructuur voor het logboek met onnodig gebeurtenissen voor het verbergen van eerdere bewijs overspoelen. Om u te beschermen tegen deze aanval, zorg ervoor dat er een vorm van gebeurtenislogboek verzameling instellen (dat wil zeggen, Windows Event Forwarding, [ontdekken van de Adversary met bewaking van Windows-gebeurtenislogboek](http://www.nsa.gov/ia/_files/app/Spotting_the_Adversary_with_Windows_Event_Log_Monitoring.pdf)) gebeurtenislogboeken af bij de computer als verplaatsen snel mogelijk.