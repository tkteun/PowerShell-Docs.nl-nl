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
# <a name="script-tracing-and-logging"></a><span data-ttu-id="b7bfa-103">Tracering en logboekregistratie voor scripts</span><span class="sxs-lookup"><span data-stu-id="b7bfa-103">Script Tracing and Logging</span></span>

<span data-ttu-id="b7bfa-104">Hoewel Power shell al over de groepsbeleid **LogPipelineExecutionDetails** -instelling beschikt voor het vastleggen van de aanroep van cmdlets, heeft de script taal van Power shell verschillende functies die u mogelijk wilt registreren en controleren.</span><span class="sxs-lookup"><span data-stu-id="b7bfa-104">While PowerShell already has the **LogPipelineExecutionDetails** Group Policy setting to log the invocation of cmdlets, PowerShell's scripting language has several features that you might want to log and audit.</span></span> <span data-ttu-id="b7bfa-105">De nieuwe uitgebreide functie voor het traceren van scripts biedt gedetailleerde tracering en analyse van Power shell-script activiteit op een systeem.</span><span class="sxs-lookup"><span data-stu-id="b7bfa-105">The new Detailed Script Tracing feature provides detailed tracking and analysis of PowerShell script activity on a system.</span></span> <span data-ttu-id="b7bfa-106">Nadat u gedetailleerde script tracering hebt ingeschakeld, worden alle script blokken in Power shell geregistreerd in het ETW-gebeurtenis logboek, **micro soft-Windows-Power shell/operationeel**.</span><span class="sxs-lookup"><span data-stu-id="b7bfa-106">After enabling detailed script tracing, PowerShell logs all script blocks to the ETW event log, **Microsoft-Windows-PowerShell/Operational**.</span></span> <span data-ttu-id="b7bfa-107">Als een script blok een ander script blok maakt, bijvoorbeeld door aanroepen `Invoke-Expression` , wordt het aangeroepen script blok ook vastgelegd.</span><span class="sxs-lookup"><span data-stu-id="b7bfa-107">If a script block creates another script block, for example, by calling `Invoke-Expression`, the invoked script block also logged.</span></span>

<span data-ttu-id="b7bfa-108">Logboek registratie wordt ingeschakeld via de instelling **logboek registratie van Power shell-script blok inschakelen** Groepsbeleid in **Beheersjablonen**  ->  **Windows-onderdelen**  ->  **Windows Power shell**.</span><span class="sxs-lookup"><span data-stu-id="b7bfa-108">Logging is enabled through the **Turn on PowerShell Script Block Logging** Group Policy setting in **Administrative Templates** -> **Windows Components** -> **Windows PowerShell**.</span></span>

<span data-ttu-id="b7bfa-109">De gebeurtenissen zijn:</span><span class="sxs-lookup"><span data-stu-id="b7bfa-109">The events are:</span></span>

| <span data-ttu-id="b7bfa-110">Kanaal</span><span class="sxs-lookup"><span data-stu-id="b7bfa-110">Channel</span></span> |                               <span data-ttu-id="b7bfa-111">Functioneren</span><span class="sxs-lookup"><span data-stu-id="b7bfa-111">Operational</span></span>                               |
| ------- | ----------------------------------------------------------------------- |
| <span data-ttu-id="b7bfa-112">Niveau</span><span class="sxs-lookup"><span data-stu-id="b7bfa-112">Level</span></span>   | <span data-ttu-id="b7bfa-113">Verbose</span><span class="sxs-lookup"><span data-stu-id="b7bfa-113">Verbose</span></span>                                                                 |
| <span data-ttu-id="b7bfa-114">Code</span><span class="sxs-lookup"><span data-stu-id="b7bfa-114">Opcode</span></span>  | <span data-ttu-id="b7bfa-115">Maken</span><span class="sxs-lookup"><span data-stu-id="b7bfa-115">Create</span></span>                                                                  |
| <span data-ttu-id="b7bfa-116">Taak</span><span class="sxs-lookup"><span data-stu-id="b7bfa-116">Task</span></span>    | <span data-ttu-id="b7bfa-117">CommandStart</span><span class="sxs-lookup"><span data-stu-id="b7bfa-117">CommandStart</span></span>                                                            |
| <span data-ttu-id="b7bfa-118">Zoek</span><span class="sxs-lookup"><span data-stu-id="b7bfa-118">Keyword</span></span> | <span data-ttu-id="b7bfa-119">Runs</span><span class="sxs-lookup"><span data-stu-id="b7bfa-119">Runspace</span></span>                                                                |
| <span data-ttu-id="b7bfa-120">Gebeurtenis</span><span class="sxs-lookup"><span data-stu-id="b7bfa-120">EventId</span></span> | <span data-ttu-id="b7bfa-121">Engine_ScriptBlockCompiled (0x1008 = 4104)</span><span class="sxs-lookup"><span data-stu-id="b7bfa-121">Engine_ScriptBlockCompiled (0x1008 = 4104)</span></span>                              |
| <span data-ttu-id="b7bfa-122">Bericht</span><span class="sxs-lookup"><span data-stu-id="b7bfa-122">Message</span></span> | <span data-ttu-id="b7bfa-123">Script Block-tekst maken (%1 van %2):</span><span class="sxs-lookup"><span data-stu-id="b7bfa-123">Creating Scriptblock text (%1 of %2):</span></span> </br> <span data-ttu-id="b7bfa-124">%3</span><span class="sxs-lookup"><span data-stu-id="b7bfa-124">%3</span></span> </br> <span data-ttu-id="b7bfa-125">Script Block-ID: %4</span><span class="sxs-lookup"><span data-stu-id="b7bfa-125">ScriptBlock ID: %4</span></span> |

<span data-ttu-id="b7bfa-126">De Inge sloten tekst in het bericht is de omvang van het gecompileerde script blok.</span><span class="sxs-lookup"><span data-stu-id="b7bfa-126">The text embedded in the message is the extent of the script block compiled.</span></span> <span data-ttu-id="b7bfa-127">De ID is een GUID die wordt bewaard voor de levens duur van het script blok.</span><span class="sxs-lookup"><span data-stu-id="b7bfa-127">The ID is a GUID that is retained for the life of the script block.</span></span>

<span data-ttu-id="b7bfa-128">Als u uitgebreide logboek registratie inschakelt, schrijft de functie begin-en eind Markeringen:</span><span class="sxs-lookup"><span data-stu-id="b7bfa-128">When you enable verbose logging, the feature writes begin and end markers:</span></span>

| <span data-ttu-id="b7bfa-129">Kanaal</span><span class="sxs-lookup"><span data-stu-id="b7bfa-129">Channel</span></span> |                                 <span data-ttu-id="b7bfa-130">Functioneren</span><span class="sxs-lookup"><span data-stu-id="b7bfa-130">Operational</span></span>                                |
| ------- | -------------------------------------------------------------------------- |
| <span data-ttu-id="b7bfa-131">Niveau</span><span class="sxs-lookup"><span data-stu-id="b7bfa-131">Level</span></span>   | <span data-ttu-id="b7bfa-132">Verbose</span><span class="sxs-lookup"><span data-stu-id="b7bfa-132">Verbose</span></span>                                                                    |
| <span data-ttu-id="b7bfa-133">Code</span><span class="sxs-lookup"><span data-stu-id="b7bfa-133">Opcode</span></span>  | <span data-ttu-id="b7bfa-134">Openen/sluiten</span><span class="sxs-lookup"><span data-stu-id="b7bfa-134">Open / Close</span></span>                                                               |
| <span data-ttu-id="b7bfa-135">Taak</span><span class="sxs-lookup"><span data-stu-id="b7bfa-135">Task</span></span>    | <span data-ttu-id="b7bfa-136">CommandStart / CommandStop</span><span class="sxs-lookup"><span data-stu-id="b7bfa-136">CommandStart / CommandStop</span></span>                                                 |
| <span data-ttu-id="b7bfa-137">Zoek</span><span class="sxs-lookup"><span data-stu-id="b7bfa-137">Keyword</span></span> | <span data-ttu-id="b7bfa-138">Runs</span><span class="sxs-lookup"><span data-stu-id="b7bfa-138">Runspace</span></span>                                                                   |
| <span data-ttu-id="b7bfa-139">Gebeurtenis</span><span class="sxs-lookup"><span data-stu-id="b7bfa-139">EventId</span></span> | <span data-ttu-id="b7bfa-140">Script Block \_ roep \_ Start \_ detail (0x1009 = 4105)/</span><span class="sxs-lookup"><span data-stu-id="b7bfa-140">ScriptBlock\_Invoke\_Start\_Detail (0x1009 = 4105) /</span></span> </br> <span data-ttu-id="b7bfa-141">Script Block \_ aanroepen \_ volledige \_ Details (0x100A = 4106)</span><span class="sxs-lookup"><span data-stu-id="b7bfa-141">ScriptBlock\_Invoke\_Complete\_Detail (0x100A = 4106)</span></span> |
| <span data-ttu-id="b7bfa-142">Bericht</span><span class="sxs-lookup"><span data-stu-id="b7bfa-142">Message</span></span> | <span data-ttu-id="b7bfa-143">Gestart/voltooide aanroep van script Block-ID: %1</span><span class="sxs-lookup"><span data-stu-id="b7bfa-143">Started / Completed invocation of ScriptBlock ID: %1</span></span> </br> <span data-ttu-id="b7bfa-144">Runs Pace-ID: %2</span><span class="sxs-lookup"><span data-stu-id="b7bfa-144">Runspace ID: %2</span></span> |

<span data-ttu-id="b7bfa-145">De ID is de GUID die het script blok vertegenwoordigt (dat kan worden gecorreleerd met gebeurtenis-ID 0x1008) en de runs Pace-ID vertegenwoordigt de runs Pace waarin dit script blok is uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="b7bfa-145">The ID is the GUID representing the script block (that can be correlated with event ID 0x1008), and the Runspace ID represents the runspace in which this script block was run.</span></span>

<span data-ttu-id="b7bfa-146">Procent tekens in het aanroep bericht vertegenwoordigen Structured ETW-eigenschappen.</span><span class="sxs-lookup"><span data-stu-id="b7bfa-146">Percent signs in the invocation message represent structured ETW properties.</span></span> <span data-ttu-id="b7bfa-147">Hoewel ze worden vervangen door de werkelijke waarden in de tekst van het bericht, is een krachtigere manier om ze te openen, het bericht op te halen met de cmdlet Get-Wine vent en vervolgens de **Eigenschappen** matrix van het bericht te gebruiken.</span><span class="sxs-lookup"><span data-stu-id="b7bfa-147">While they are replaced with the actual values in the message text, a more robust way to access them is to retrieve the message with the Get-WinEvent cmdlet, and then use the **Properties** array of the message.</span></span>

<span data-ttu-id="b7bfa-148">Hier volgt een voor beeld van hoe deze functionaliteit kan helpen bij het inpakken van een schadelijke poging om een script te versleutelen en af te schrijven:</span><span class="sxs-lookup"><span data-stu-id="b7bfa-148">Here's an example of how this functionality can help unwrap a malicious attempt to encrypt and obfuscate a script:</span></span>

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

<span data-ttu-id="b7bfa-149">Als u dit uitvoert, worden de volgende logboek vermeldingen gegenereerd:</span><span class="sxs-lookup"><span data-stu-id="b7bfa-149">Running this generates the following log entries:</span></span>

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

Als de lengte van het script blok de capaciteit van één gebeurtenis overschrijdt, wordt het script door Power shell in meerdere delen opgesplitst. <span data-ttu-id="b7bfa-151">Hier volgt een voorbeeld code voor het opnieuw combi neren van een script uit de logboek berichten:</span><span class="sxs-lookup"><span data-stu-id="b7bfa-151">Here is sample code to recombine a script from its log messages:</span></span>

```powershell
$created = Get-WinEvent -FilterHashtable @{ ProviderName="Microsoft-Windows-PowerShell"; Id = 4104 } |
  Where-Object { $_.<...> }
$sortedScripts = $created | sort { $_.Properties[0].Value }
$mergedScript = -join ($sortedScripts | % { $_.Properties[2].Value })
```

<span data-ttu-id="b7bfa-152">Net als bij alle logboek registratie systemen die een beperkte Bewaar buffer hebben, is een manier om deze infra structuur aan te vallen, het logboek te flooden met onlogische gebeurtenissen om eerdere bewijzen te verbergen.</span><span class="sxs-lookup"><span data-stu-id="b7bfa-152">As with all logging systems that have a limited retention buffer, one way to attack this infrastructure is to flood the log with spurious events to hide earlier evidence.</span></span> <span data-ttu-id="b7bfa-153">Als u van deze aanval wilt beveiligen, moet u ervoor zorgen dat u een vorm van de verzameling gebeurtenis Logboeken hebt voor het door sturen van Windows-gebeurtenissen.</span><span class="sxs-lookup"><span data-stu-id="b7bfa-153">To protect yourself from this attack, ensure that you have some form of event log collection set up Windows Event Forwarding.</span></span> <span data-ttu-id="b7bfa-154">Zie [herkennen de kwaadwillende persoon met Windows-gebeurtenis logboek bewaking](https://apps.nsa.gov/iaarchive/library/reports/spotting-the-adversary-with-windows-event-log-monitoring.cfm)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="b7bfa-154">For more information, see [Spotting the Adversary with Windows Event Log Monitoring](https://apps.nsa.gov/iaarchive/library/reports/spotting-the-adversary-with-windows-event-log-monitoring.cfm).</span></span>
