---
ms.date: 06/12/2017
keywords: wmf,powershell,installeren
ms.openlocfilehash: 28cd186ab3a08a0da4ff81f5a21514f239770d13
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62058077"
---
# <a name="script-tracing-and-logging"></a>Tracering en logboekregistratie voor scripts

Het Windows PowerShell al is de **LogPipelineExecutionDetails** Groepsbeleid van de PowerShell-scripttaal instellen om aan te melden het aanroepen van cmdlets, heeft veel functies die u wilt aanmelden en/of gecontroleerd. De nieuwe functie voor gedetailleerde tracering van Script kunt u gedetailleerde bijhouden en analyseren van Windows PowerShell scripts gebruiken op een systeem inschakelen. Nadat u gedetailleerde script tracering ingeschakeld, Windows PowerShell-alle scriptblokken logboeken naar het gebeurtenislogboek ETW **Microsoft-Windows-PowerShell/Operational**. Als een scriptblok maakt een andere scriptblok (bijvoorbeeld een script waarmee de cmdlet Invoke-Expression wordt aangeroepen op een tekenreeks), wordt die resulterende scriptblok wordt ook vastgelegd.

Logboekregistratie van deze gebeurtenissen kan worden ingeschakeld via de **PowerShell-Script blok logboekregistratie kunnen inschakelen** groepsbeleidsinstelling (in Beheersjablonen -> Windows-onderdelen -> Windows PowerShell).

De gebeurtenissen zijn:

| Kanaal | Operational                                 |
|---------|---------------------------------------------|
| Niveau   | Uitgebreid                                     |
| Opcode  | Maken                                      |
| Taak    | CommandStart                                |
| Trefwoord | Runspace                                    |
| Gebeurtenis-id | Engine_ScriptBlockCompiled (0x1008 = 4104)  |
| Bericht | Het maken van Scriptblock tekst (%1% 2): </br> %3 </br> ScriptBlock-ID: %4 |


De tekst die is ingesloten in het bericht is de omvang van het scriptblok gecompileerd. De ID is een GUID die voor de levensduur van het scriptblok worden bewaard.

Wanneer u uitgebreide logboekregistratie inschakelt, wordt de functie schrijfbewerkingen beginnen en eindigen van markeringen:

| Kanaal | Operational                                            |
|---------|--------------------------------------------------------|
| Niveau   | Uitgebreid                                                |
| Opcode  | Open (/ afsluiten)                                         |
| Taak    | CommandStart (/ CommandStop)                           |
| Trefwoord | Runspace                                               |
| Gebeurtenis-id | ScriptBlock\_aanroepen\_Start\_details (0x1009 = 4105) / </br> ScriptBlock\_aanroepen\_voltooid\_details (0x100A = 4106) |
| Bericht | Gestart (/ voltooide) aanroepen van ScriptBlock-ID: %1 </br> Runspace-ID: %2 |

De ID is de GUID voor het scriptblok (die kan worden gecorreleerd met gebeurtenis-ID 0x1008) en de Runspace-ID vertegenwoordigt de runspace waarin deze scriptblok is uitgevoerd.

Procenttekens in het bericht aanroep vertegenwoordigen gestructureerde ETW-eigenschappen. Terwijl ze worden vervangen door de werkelijke waarden in de berichttekst, een robuustere manier toegang tot deze wordt het bericht met de cmdlet Get-WinEvent ophalen en gebruik vervolgens de **eigenschappen** matrix van het bericht.

Hier volgt een voorbeeld van hoe deze functie kunt uitpakken een schadelijke poging voor het versleutelen en een script, onleesbaar maakt:

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

Uitvoeren van dit genereert de volgende vermeldingen:

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

Windows PowerShell verbroken als het script bloklengte groter is dan wat ETW is geschikt voor bedrijf in één gebeurtenis, het script in meerdere delen. Hier volgt een voorbeeldcode om een script uit de logboekberichten weer:

```powershell
$created = Get-WinEvent -FilterHashtable @{ ProviderName="Microsoft-Windows-PowerShell"; Id = 4104 } | Where-Object { $_.<...> }
$sortedScripts = $created | sort { $_.Properties[0].Value }
$mergedScript = -join ($sortedScripts | % { $_.Properties[2].Value })
```

Net als bij alle logboekregistratie-systemen waarvoor een beperkte retentie buffer (dat wil zeggen ETW-Logboeken), is een aanval op deze infrastructuur aan het logboek met onnodig gebeurtenissen om te verbergen oudere bewijs overspoelen. Zorg ervoor dat u een vorm van gebeurtenis logboekverzameling instellen hebt om uzelf te beschermen tegen deze aanvallen, (dat wil zeggen Windows Event Forwarding, [ontdekken van de kwaadwillende persoon met bewaking van Windows-gebeurtenislogboek](https://www.iad.gov/iad/library/reports/spotting-the-adversary-with-windows-event-log-monitoring.cfm)) te verplaatsen van gebeurtenislogboeken af bij de computer als snel mogelijk.
