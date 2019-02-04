---
ms.date: 06/12/2017
keywords: wmf,powershell,installeren
ms.openlocfilehash: 28cd186ab3a08a0da4ff81f5a21514f239770d13
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 02/03/2019
ms.locfileid: "55684659"
---
# <a name="script-tracing-and-logging"></a><span data-ttu-id="178dc-102">Tracering en logboekregistratie voor scripts</span><span class="sxs-lookup"><span data-stu-id="178dc-102">Script Tracing and Logging</span></span>

<span data-ttu-id="178dc-103">Het Windows PowerShell al is de **LogPipelineExecutionDetails** Groepsbeleid van de PowerShell-scripttaal instellen om aan te melden het aanroepen van cmdlets, heeft veel functies die u wilt aanmelden en/of gecontroleerd.</span><span class="sxs-lookup"><span data-stu-id="178dc-103">While Windows PowerShell already has the **LogPipelineExecutionDetails** Group Policy setting to log the invocation of cmdlets, PowerShell’s scripting language has plenty of features that you might want to log and/or audit.</span></span> <span data-ttu-id="178dc-104">De nieuwe functie voor gedetailleerde tracering van Script kunt u gedetailleerde bijhouden en analyseren van Windows PowerShell scripts gebruiken op een systeem inschakelen.</span><span class="sxs-lookup"><span data-stu-id="178dc-104">The new Detailed Script Tracing feature lets you enable detailed tracking and analysis of Windows PowerShell scripting use on a system.</span></span> <span data-ttu-id="178dc-105">Nadat u gedetailleerde script tracering ingeschakeld, Windows PowerShell-alle scriptblokken logboeken naar het gebeurtenislogboek ETW **Microsoft-Windows-PowerShell/Operational**.</span><span class="sxs-lookup"><span data-stu-id="178dc-105">After you enable detailed script tracing, Windows PowerShell logs all script blocks to the ETW event log, **Microsoft-Windows-PowerShell/Operational**.</span></span> <span data-ttu-id="178dc-106">Als een scriptblok maakt een andere scriptblok (bijvoorbeeld een script waarmee de cmdlet Invoke-Expression wordt aangeroepen op een tekenreeks), wordt die resulterende scriptblok wordt ook vastgelegd.</span><span class="sxs-lookup"><span data-stu-id="178dc-106">If a script block creates another script block (for example, a script that calls the Invoke-Expression cmdlet on a string), that resulting script block is logged as well.</span></span>

<span data-ttu-id="178dc-107">Logboekregistratie van deze gebeurtenissen kan worden ingeschakeld via de **PowerShell-Script blok logboekregistratie kunnen inschakelen** groepsbeleidsinstelling (in Beheersjablonen -> Windows-onderdelen -> Windows PowerShell).</span><span class="sxs-lookup"><span data-stu-id="178dc-107">Logging of these events can be enabled through the **Turn on PowerShell Script Block Logging** Group Policy setting (in Administrative Templates -> Windows Components -> Windows PowerShell).</span></span>

<span data-ttu-id="178dc-108">De gebeurtenissen zijn:</span><span class="sxs-lookup"><span data-stu-id="178dc-108">The events are:</span></span>

| <span data-ttu-id="178dc-109">Kanaal</span><span class="sxs-lookup"><span data-stu-id="178dc-109">Channel</span></span> | <span data-ttu-id="178dc-110">Operational</span><span class="sxs-lookup"><span data-stu-id="178dc-110">Operational</span></span>                                 |
|---------|---------------------------------------------|
| <span data-ttu-id="178dc-111">Niveau</span><span class="sxs-lookup"><span data-stu-id="178dc-111">Level</span></span>   | <span data-ttu-id="178dc-112">Verbose</span><span class="sxs-lookup"><span data-stu-id="178dc-112">Verbose</span></span>                                     |
| <span data-ttu-id="178dc-113">Opcode</span><span class="sxs-lookup"><span data-stu-id="178dc-113">Opcode</span></span>  | <span data-ttu-id="178dc-114">Maken</span><span class="sxs-lookup"><span data-stu-id="178dc-114">Create</span></span>                                      |
| <span data-ttu-id="178dc-115">Taak</span><span class="sxs-lookup"><span data-stu-id="178dc-115">Task</span></span>    | <span data-ttu-id="178dc-116">CommandStart</span><span class="sxs-lookup"><span data-stu-id="178dc-116">CommandStart</span></span>                                |
| <span data-ttu-id="178dc-117">Trefwoord</span><span class="sxs-lookup"><span data-stu-id="178dc-117">Keyword</span></span> | <span data-ttu-id="178dc-118">runspace</span><span class="sxs-lookup"><span data-stu-id="178dc-118">Runspace</span></span>                                    |
| <span data-ttu-id="178dc-119">Gebeurtenis-id</span><span class="sxs-lookup"><span data-stu-id="178dc-119">EventId</span></span> | <span data-ttu-id="178dc-120">Engine_ScriptBlockCompiled (0x1008 = 4104)</span><span class="sxs-lookup"><span data-stu-id="178dc-120">Engine_ScriptBlockCompiled (0x1008 = 4104)</span></span>  |
| <span data-ttu-id="178dc-121">Bericht</span><span class="sxs-lookup"><span data-stu-id="178dc-121">Message</span></span> | <span data-ttu-id="178dc-122">Het maken van Scriptblock tekst (%1% 2):</span><span class="sxs-lookup"><span data-stu-id="178dc-122">Creating Scriptblock text (%1 of %2):</span></span> </br> <span data-ttu-id="178dc-123">%3</span><span class="sxs-lookup"><span data-stu-id="178dc-123">%3</span></span> </br> <span data-ttu-id="178dc-124">ScriptBlock-ID: %4</span><span class="sxs-lookup"><span data-stu-id="178dc-124">ScriptBlock ID: %4</span></span> |


<span data-ttu-id="178dc-125">De tekst die is ingesloten in het bericht is de omvang van het scriptblok gecompileerd.</span><span class="sxs-lookup"><span data-stu-id="178dc-125">The text embedded in the message is the extent of the script block compiled.</span></span> <span data-ttu-id="178dc-126">De ID is een GUID die voor de levensduur van het scriptblok worden bewaard.</span><span class="sxs-lookup"><span data-stu-id="178dc-126">The ID is a GUID that is retained for the life of the script block.</span></span>

<span data-ttu-id="178dc-127">Wanneer u uitgebreide logboekregistratie inschakelt, wordt de functie schrijfbewerkingen beginnen en eindigen van markeringen:</span><span class="sxs-lookup"><span data-stu-id="178dc-127">When you enable verbose logging, the feature writes begin and end markers:</span></span>

| <span data-ttu-id="178dc-128">Kanaal</span><span class="sxs-lookup"><span data-stu-id="178dc-128">Channel</span></span> | <span data-ttu-id="178dc-129">Operational</span><span class="sxs-lookup"><span data-stu-id="178dc-129">Operational</span></span>                                            |
|---------|--------------------------------------------------------|
| <span data-ttu-id="178dc-130">Niveau</span><span class="sxs-lookup"><span data-stu-id="178dc-130">Level</span></span>   | <span data-ttu-id="178dc-131">Verbose</span><span class="sxs-lookup"><span data-stu-id="178dc-131">Verbose</span></span>                                                |
| <span data-ttu-id="178dc-132">Opcode</span><span class="sxs-lookup"><span data-stu-id="178dc-132">Opcode</span></span>  | <span data-ttu-id="178dc-133">Open (/ afsluiten)</span><span class="sxs-lookup"><span data-stu-id="178dc-133">Open (/ Close)</span></span>                                         |
| <span data-ttu-id="178dc-134">Taak</span><span class="sxs-lookup"><span data-stu-id="178dc-134">Task</span></span>    | <span data-ttu-id="178dc-135">CommandStart (/ CommandStop)</span><span class="sxs-lookup"><span data-stu-id="178dc-135">CommandStart (/ CommandStop)</span></span>                           |
| <span data-ttu-id="178dc-136">Trefwoord</span><span class="sxs-lookup"><span data-stu-id="178dc-136">Keyword</span></span> | <span data-ttu-id="178dc-137">runspace</span><span class="sxs-lookup"><span data-stu-id="178dc-137">Runspace</span></span>                                               |
| <span data-ttu-id="178dc-138">Gebeurtenis-id</span><span class="sxs-lookup"><span data-stu-id="178dc-138">EventId</span></span> | <span data-ttu-id="178dc-139">ScriptBlock\_aanroepen\_Start\_details (0x1009 = 4105) /</span><span class="sxs-lookup"><span data-stu-id="178dc-139">ScriptBlock\_Invoke\_Start\_Detail (0x1009 = 4105) /</span></span> </br> <span data-ttu-id="178dc-140">ScriptBlock\_aanroepen\_voltooid\_details (0x100A = 4106)</span><span class="sxs-lookup"><span data-stu-id="178dc-140">ScriptBlock\_Invoke\_Complete\_Detail (0x100A = 4106)</span></span> |
| <span data-ttu-id="178dc-141">Bericht</span><span class="sxs-lookup"><span data-stu-id="178dc-141">Message</span></span> | <span data-ttu-id="178dc-142">Gestart (/ voltooide) aanroepen van ScriptBlock-ID: %1</span><span class="sxs-lookup"><span data-stu-id="178dc-142">Started (/ Completed) invocation of ScriptBlock ID: %1</span></span> </br> <span data-ttu-id="178dc-143">Runspace-ID: %2</span><span class="sxs-lookup"><span data-stu-id="178dc-143">Runspace ID: %2</span></span> |

<span data-ttu-id="178dc-144">De ID is de GUID voor het scriptblok (die kan worden gecorreleerd met gebeurtenis-ID 0x1008) en de Runspace-ID vertegenwoordigt de runspace waarin deze scriptblok is uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="178dc-144">The ID is the GUID representing the script block (that can be correlated with event ID 0x1008), and the Runspace ID represents the runspace in which this script block was run.</span></span>

<span data-ttu-id="178dc-145">Procenttekens in het bericht aanroep vertegenwoordigen gestructureerde ETW-eigenschappen.</span><span class="sxs-lookup"><span data-stu-id="178dc-145">Percent signs in the invocation message represent structured ETW properties.</span></span> <span data-ttu-id="178dc-146">Terwijl ze worden vervangen door de werkelijke waarden in de berichttekst, een robuustere manier toegang tot deze wordt het bericht met de cmdlet Get-WinEvent ophalen en gebruik vervolgens de **eigenschappen** matrix van het bericht.</span><span class="sxs-lookup"><span data-stu-id="178dc-146">While they are replaced with the actual values in the message text, a more robust way to access them is to retrieve the message with the Get-WinEvent cmdlet, and then use the **Properties** array of the message.</span></span>

<span data-ttu-id="178dc-147">Hier volgt een voorbeeld van hoe deze functie kunt uitpakken een schadelijke poging voor het versleutelen en een script, onleesbaar maakt:</span><span class="sxs-lookup"><span data-stu-id="178dc-147">Here's an example of how this functionality can help unwrap a malicious attempt to encrypt and obfuscate a script:</span></span>

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

<span data-ttu-id="178dc-148">Uitvoeren van dit genereert de volgende vermeldingen:</span><span class="sxs-lookup"><span data-stu-id="178dc-148">Running this generates the following log entries:</span></span>

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

Windows PowerShell verbroken als het script bloklengte groter is dan wat ETW is geschikt voor bedrijf in één gebeurtenis, het script in meerdere delen. <span data-ttu-id="178dc-150">Hier volgt een voorbeeldcode om een script uit de logboekberichten weer:</span><span class="sxs-lookup"><span data-stu-id="178dc-150">Here is sample code to recombine a script from its log messages:</span></span>

```powershell
$created = Get-WinEvent -FilterHashtable @{ ProviderName="Microsoft-Windows-PowerShell"; Id = 4104 } | Where-Object { $_.<...> }
$sortedScripts = $created | sort { $_.Properties[0].Value }
$mergedScript = -join ($sortedScripts | % { $_.Properties[2].Value })
```

<span data-ttu-id="178dc-151">Net als bij alle logboekregistratie-systemen waarvoor een beperkte retentie buffer (dat wil zeggen ETW-Logboeken), is een aanval op deze infrastructuur aan het logboek met onnodig gebeurtenissen om te verbergen oudere bewijs overspoelen.</span><span class="sxs-lookup"><span data-stu-id="178dc-151">As with all logging systems that have a limited retention buffer (i.e. ETW logs), one attack against this infrastructure is to flood the log with spurious events to hide earlier evidence.</span></span> <span data-ttu-id="178dc-152">Zorg ervoor dat u een vorm van gebeurtenis logboekverzameling instellen hebt om uzelf te beschermen tegen deze aanvallen, (dat wil zeggen Windows Event Forwarding, [ontdekken van de kwaadwillende persoon met bewaking van Windows-gebeurtenislogboek](https://www.iad.gov/iad/library/reports/spotting-the-adversary-with-windows-event-log-monitoring.cfm)) te verplaatsen van gebeurtenislogboeken af bij de computer als snel mogelijk.</span><span class="sxs-lookup"><span data-stu-id="178dc-152">To protect yourself from this attack, ensure that you have some form of event log collection set up (i.e., Windows Event Forwarding, [Spotting the Adversary with Windows Event Log Monitoring](https://www.iad.gov/iad/library/reports/spotting-the-adversary-with-windows-event-log-monitoring.cfm)) to move event logs off of the computer as soon as possible.</span></span>
