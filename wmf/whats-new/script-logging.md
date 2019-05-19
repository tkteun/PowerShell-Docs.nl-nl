---
ms.date: 06/12/2017
keywords: wmf,powershell,installeren
title: Tracering en logboekregistratie voor scripts
ms.openlocfilehash: 6b7e5022cb4c974da5ddb3d670b5808dc9fb7bdc
ms.sourcegitcommit: 01b81317029b28dd9b61d167045fd31f1ec7bc06
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 05/17/2019
ms.locfileid: "65856152"
---
# <a name="script-tracing-and-logging"></a><span data-ttu-id="cef8f-103">Tracering en logboekregistratie voor scripts</span><span class="sxs-lookup"><span data-stu-id="cef8f-103">Script Tracing and Logging</span></span>

<span data-ttu-id="cef8f-104">Hoewel PowerShell al heeft het **LogPipelineExecutionDetails** Groepsbeleid instellen om aan te melden het aanroepen van cmdlets, de PowerShell-scripttaal beschikt over verschillende functies die u wilt mogelijk aanmelden en controleren.</span><span class="sxs-lookup"><span data-stu-id="cef8f-104">While PowerShell already has the **LogPipelineExecutionDetails** Group Policy setting to log the invocation of cmdlets, PowerShell's scripting language has several features that you might want to log and audit.</span></span> <span data-ttu-id="cef8f-105">De nieuwe functie voor gedetailleerde tracering van Script biedt gedetailleerde bijhouden en analyseren van PowerShell-script-activiteit op een systeem.</span><span class="sxs-lookup"><span data-stu-id="cef8f-105">The new Detailed Script Tracing feature provides detailed tracking and analysis of PowerShell script activity on a system.</span></span> <span data-ttu-id="cef8f-106">Na het inschakelen van gedetailleerde script tracering PowerShell alle scriptblokken logboeken naar het gebeurtenislogboek ETW **Microsoft-Windows-PowerShell/Operational**.</span><span class="sxs-lookup"><span data-stu-id="cef8f-106">After enabling detailed script tracing, PowerShell logs all script blocks to the ETW event log, **Microsoft-Windows-PowerShell/Operational**.</span></span> <span data-ttu-id="cef8f-107">Als een scriptblok een andere scriptblok, bijvoorbeeld door het aanroepen van maakt `Invoke-Expression`, het aangeroepen scriptblok ook wordt geregistreerd.</span><span class="sxs-lookup"><span data-stu-id="cef8f-107">If a script block creates another script block, for example, by calling `Invoke-Expression`, the invoked script block also logged.</span></span>

<span data-ttu-id="cef8f-108">Logboekregistratie is ingeschakeld via de **PowerShell-Script blok logboekregistratie kunnen inschakelen** instelling voor Groepsbeleid in **Beheersjablonen** -> **Windows-onderdelen**  ->  **Windows PowerShell**.</span><span class="sxs-lookup"><span data-stu-id="cef8f-108">Logging is enabled through the **Turn on PowerShell Script Block Logging** Group Policy setting in **Administrative Templates** -> **Windows Components** -> **Windows PowerShell**.</span></span>

<span data-ttu-id="cef8f-109">De gebeurtenissen zijn:</span><span class="sxs-lookup"><span data-stu-id="cef8f-109">The events are:</span></span>

| <span data-ttu-id="cef8f-110">Kanaal</span><span class="sxs-lookup"><span data-stu-id="cef8f-110">Channel</span></span> |                               <span data-ttu-id="cef8f-111">Operational</span><span class="sxs-lookup"><span data-stu-id="cef8f-111">Operational</span></span>                               |
| ------- | ----------------------------------------------------------------------- |
| <span data-ttu-id="cef8f-112">Niveau</span><span class="sxs-lookup"><span data-stu-id="cef8f-112">Level</span></span>   | <span data-ttu-id="cef8f-113">Verbose</span><span class="sxs-lookup"><span data-stu-id="cef8f-113">Verbose</span></span>                                                                 |
| <span data-ttu-id="cef8f-114">Opcode</span><span class="sxs-lookup"><span data-stu-id="cef8f-114">Opcode</span></span>  | <span data-ttu-id="cef8f-115">Maken</span><span class="sxs-lookup"><span data-stu-id="cef8f-115">Create</span></span>                                                                  |
| <span data-ttu-id="cef8f-116">Taak</span><span class="sxs-lookup"><span data-stu-id="cef8f-116">Task</span></span>    | <span data-ttu-id="cef8f-117">CommandStart</span><span class="sxs-lookup"><span data-stu-id="cef8f-117">CommandStart</span></span>                                                            |
| <span data-ttu-id="cef8f-118">Trefwoord</span><span class="sxs-lookup"><span data-stu-id="cef8f-118">Keyword</span></span> | <span data-ttu-id="cef8f-119">Runspace</span><span class="sxs-lookup"><span data-stu-id="cef8f-119">Runspace</span></span>                                                                |
| <span data-ttu-id="cef8f-120">Gebeurtenis-id</span><span class="sxs-lookup"><span data-stu-id="cef8f-120">EventId</span></span> | <span data-ttu-id="cef8f-121">Engine_ScriptBlockCompiled (0x1008 = 4104)</span><span class="sxs-lookup"><span data-stu-id="cef8f-121">Engine_ScriptBlockCompiled (0x1008 = 4104)</span></span>                              |
| <span data-ttu-id="cef8f-122">Bericht</span><span class="sxs-lookup"><span data-stu-id="cef8f-122">Message</span></span> | <span data-ttu-id="cef8f-123">Het maken van Scriptblock tekst (%1% 2):</span><span class="sxs-lookup"><span data-stu-id="cef8f-123">Creating Scriptblock text (%1 of %2):</span></span> </br> <span data-ttu-id="cef8f-124">%3</span><span class="sxs-lookup"><span data-stu-id="cef8f-124">%3</span></span> </br> <span data-ttu-id="cef8f-125">ScriptBlock-ID: %4</span><span class="sxs-lookup"><span data-stu-id="cef8f-125">ScriptBlock ID: %4</span></span> |


<span data-ttu-id="cef8f-126">De tekst die is ingesloten in het bericht is de omvang van het scriptblok gecompileerd.</span><span class="sxs-lookup"><span data-stu-id="cef8f-126">The text embedded in the message is the extent of the script block compiled.</span></span> <span data-ttu-id="cef8f-127">De ID is een GUID die voor de levensduur van het scriptblok worden bewaard.</span><span class="sxs-lookup"><span data-stu-id="cef8f-127">The ID is a GUID that is retained for the life of the script block.</span></span>

<span data-ttu-id="cef8f-128">Wanneer u uitgebreide logboekregistratie inschakelt, wordt de functie schrijfbewerkingen beginnen en eindigen van markeringen:</span><span class="sxs-lookup"><span data-stu-id="cef8f-128">When you enable verbose logging, the feature writes begin and end markers:</span></span>

| <span data-ttu-id="cef8f-129">Kanaal</span><span class="sxs-lookup"><span data-stu-id="cef8f-129">Channel</span></span> |                                 <span data-ttu-id="cef8f-130">Operational</span><span class="sxs-lookup"><span data-stu-id="cef8f-130">Operational</span></span>                                |
| ------- | -------------------------------------------------------------------------- |
| <span data-ttu-id="cef8f-131">Niveau</span><span class="sxs-lookup"><span data-stu-id="cef8f-131">Level</span></span>   | <span data-ttu-id="cef8f-132">Verbose</span><span class="sxs-lookup"><span data-stu-id="cef8f-132">Verbose</span></span>                                                                    |
| <span data-ttu-id="cef8f-133">Opcode</span><span class="sxs-lookup"><span data-stu-id="cef8f-133">Opcode</span></span>  | <span data-ttu-id="cef8f-134">Open / sluiten</span><span class="sxs-lookup"><span data-stu-id="cef8f-134">Open / Close</span></span>                                                               |
| <span data-ttu-id="cef8f-135">Taak</span><span class="sxs-lookup"><span data-stu-id="cef8f-135">Task</span></span>    | <span data-ttu-id="cef8f-136">CommandStart / CommandStop</span><span class="sxs-lookup"><span data-stu-id="cef8f-136">CommandStart / CommandStop</span></span>                                                 |
| <span data-ttu-id="cef8f-137">Trefwoord</span><span class="sxs-lookup"><span data-stu-id="cef8f-137">Keyword</span></span> | <span data-ttu-id="cef8f-138">Runspace</span><span class="sxs-lookup"><span data-stu-id="cef8f-138">Runspace</span></span>                                                                   |
| <span data-ttu-id="cef8f-139">Gebeurtenis-id</span><span class="sxs-lookup"><span data-stu-id="cef8f-139">EventId</span></span> | <span data-ttu-id="cef8f-140">ScriptBlock\_aanroepen\_Start\_details (0x1009 = 4105) /</span><span class="sxs-lookup"><span data-stu-id="cef8f-140">ScriptBlock\_Invoke\_Start\_Detail (0x1009 = 4105) /</span></span> </br> <span data-ttu-id="cef8f-141">ScriptBlock\_aanroepen\_voltooid\_details (0x100A = 4106)</span><span class="sxs-lookup"><span data-stu-id="cef8f-141">ScriptBlock\_Invoke\_Complete\_Detail (0x100A = 4106)</span></span> |
| <span data-ttu-id="cef8f-142">Bericht</span><span class="sxs-lookup"><span data-stu-id="cef8f-142">Message</span></span> | <span data-ttu-id="cef8f-143">Aan de slag / voltooid aanroep van ScriptBlock-ID: %1</span><span class="sxs-lookup"><span data-stu-id="cef8f-143">Started / Completed invocation of ScriptBlock ID: %1</span></span> </br> <span data-ttu-id="cef8f-144">Runspace-ID: %2</span><span class="sxs-lookup"><span data-stu-id="cef8f-144">Runspace ID: %2</span></span> |

<span data-ttu-id="cef8f-145">De ID is de GUID voor het scriptblok (die kan worden gecorreleerd met gebeurtenis-ID 0x1008) en de Runspace-ID vertegenwoordigt de runspace waarin deze scriptblok is uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="cef8f-145">The ID is the GUID representing the script block (that can be correlated with event ID 0x1008), and the Runspace ID represents the runspace in which this script block was run.</span></span>

<span data-ttu-id="cef8f-146">Procenttekens in het bericht aanroep vertegenwoordigen gestructureerde ETW-eigenschappen.</span><span class="sxs-lookup"><span data-stu-id="cef8f-146">Percent signs in the invocation message represent structured ETW properties.</span></span> <span data-ttu-id="cef8f-147">Terwijl ze worden vervangen door de werkelijke waarden in de berichttekst, een robuustere manier toegang tot deze wordt het bericht met de cmdlet Get-WinEvent ophalen en gebruik vervolgens de **eigenschappen** matrix van het bericht.</span><span class="sxs-lookup"><span data-stu-id="cef8f-147">While they are replaced with the actual values in the message text, a more robust way to access them is to retrieve the message with the Get-WinEvent cmdlet, and then use the **Properties** array of the message.</span></span>

<span data-ttu-id="cef8f-148">Hier volgt een voorbeeld van hoe deze functie kunt uitpakken een schadelijke poging voor het versleutelen en een script, onleesbaar maakt:</span><span class="sxs-lookup"><span data-stu-id="cef8f-148">Here's an example of how this functionality can help unwrap a malicious attempt to encrypt and obfuscate a script:</span></span>

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

<span data-ttu-id="cef8f-149">Uitvoeren van dit genereert de volgende vermeldingen:</span><span class="sxs-lookup"><span data-stu-id="cef8f-149">Running this generates the following log entries:</span></span>

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

PowerShell verbroken als het script bloklengte groter is dan de capaciteit van één gebeurtenis, het script in meerdere delen. <span data-ttu-id="cef8f-151">Hier volgt een voorbeeldcode om een script uit de logboekberichten weer:</span><span class="sxs-lookup"><span data-stu-id="cef8f-151">Here is sample code to recombine a script from its log messages:</span></span>

```powershell
$created = Get-WinEvent -FilterHashtable @{ ProviderName="Microsoft-Windows-PowerShell"; Id = 4104 } |
  Where-Object { $_.<...> }
$sortedScripts = $created | sort { $_.Properties[0].Value }
$mergedScript = -join ($sortedScripts | % { $_.Properties[2].Value })
```

<span data-ttu-id="cef8f-152">Net als bij alle logboekregistratie systemen waarvoor een beperkte retentie-buffer is één manier om aan te vallen deze infrastructuur aan het logboek met onnodig gebeurtenissen om te verbergen oudere bewijs overspoelen.</span><span class="sxs-lookup"><span data-stu-id="cef8f-152">As with all logging systems that have a limited retention buffer, one way to attack this infrastructure is to flood the log with spurious events to hide earlier evidence.</span></span> <span data-ttu-id="cef8f-153">Als u wilt beschermen tegen deze aanval, zorg ervoor dat u een vorm van gebeurtenis logboekverzameling instellen van Windows Event Forwarding hebt.</span><span class="sxs-lookup"><span data-stu-id="cef8f-153">To protect yourself from this attack, ensure that you have some form of event log collection set up Windows Event Forwarding.</span></span> <span data-ttu-id="cef8f-154">Zie voor meer informatie, [ontdekken van de kwaadwillende persoon met bewaking van Windows-gebeurtenislogboek](https://apps.nsa.gov/iaarchive/library/reports/spotting-the-adversary-with-windows-event-log-monitoring.cfm).</span><span class="sxs-lookup"><span data-stu-id="cef8f-154">For more information, see [Spotting the Adversary with Windows Event Log Monitoring](https://apps.nsa.gov/iaarchive/library/reports/spotting-the-adversary-with-windows-event-log-monitoring.cfm).</span></span>