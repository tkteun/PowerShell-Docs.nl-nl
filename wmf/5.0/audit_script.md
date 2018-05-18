---
ms.date: 06/12/2017
keywords: wmf,powershell,installeren
ms.openlocfilehash: 2627b9d02788bd31a5384587406df533faf2cfaf
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 05/17/2018
---
# <a name="script-tracing-and-logging"></a><span data-ttu-id="25574-102">Tracering en logboekregistratie voor scripts</span><span class="sxs-lookup"><span data-stu-id="25574-102">Script Tracing and Logging</span></span>

<span data-ttu-id="25574-103">Terwijl Windows PowerShell al heeft het **LogPipelineExecutionDetails** Groepsbeleid van PowerShell-scripttaal instellen voor het aanroepen van cmdlets melden, heeft veel functies die u kunt zich aanmelden en controleren.</span><span class="sxs-lookup"><span data-stu-id="25574-103">While Windows PowerShell already has the **LogPipelineExecutionDetails** Group Policy setting to log the invocation of cmdlets, PowerShell’s scripting language has plenty of features that you might want to log and/or audit.</span></span> <span data-ttu-id="25574-104">De nieuwe functie voor gedetailleerde tracering van Script stelt u gedetailleerde bijhouden en analyseren van Windows PowerShell scripts gebruiken op een systeem.</span><span class="sxs-lookup"><span data-stu-id="25574-104">The new Detailed Script Tracing feature lets you enable detailed tracking and analysis of Windows PowerShell scripting use on a system.</span></span> <span data-ttu-id="25574-105">Nadat u gedetailleerde script tracering ingeschakeld, Windows PowerShell alle scriptblokken registreert in het gebeurtenislogboek ETW **Microsoft-Windows-PowerShell/operationeel**.</span><span class="sxs-lookup"><span data-stu-id="25574-105">After you enable detailed script tracing, Windows PowerShell logs all script blocks to the ETW event log, **Microsoft-Windows-PowerShell/Operational**.</span></span> <span data-ttu-id="25574-106">Als een scriptblok maakt een ander scriptblok (bijvoorbeeld een script waarmee de cmdlet Invoke-Expression op een tekenreeks aangeroepen), wordt die resulterende scriptblok wordt ook vastgelegd.</span><span class="sxs-lookup"><span data-stu-id="25574-106">If a script block creates another script block (for example, a script that calls the Invoke-Expression cmdlet on a string), that resulting script block is logged as well.</span></span>

<span data-ttu-id="25574-107">Registreren van deze gebeurtenissen kan worden ingeschakeld via de **schakelt logboekregistratie van PowerShell-Script blok** instelling voor Groepsbeleid (in Beheersjablonen -> Windows-onderdelen -> Windows PowerShell).</span><span class="sxs-lookup"><span data-stu-id="25574-107">Logging of these events can be enabled through the **Turn on PowerShell Script Block Logging** Group Policy setting (in Administrative Templates -> Windows Components -> Windows PowerShell).</span></span>

<span data-ttu-id="25574-108">De gebeurtenissen zijn:</span><span class="sxs-lookup"><span data-stu-id="25574-108">The events are:</span></span>

| <span data-ttu-id="25574-109">Kanaal</span><span class="sxs-lookup"><span data-stu-id="25574-109">Channel</span></span> | <span data-ttu-id="25574-110">Operationele</span><span class="sxs-lookup"><span data-stu-id="25574-110">Operational</span></span>                                 |
|---------|---------------------------------------------|
| <span data-ttu-id="25574-111">Niveau</span><span class="sxs-lookup"><span data-stu-id="25574-111">Level</span></span>   | <span data-ttu-id="25574-112">Verbose</span><span class="sxs-lookup"><span data-stu-id="25574-112">Verbose</span></span>                                     |
| <span data-ttu-id="25574-113">Opcode</span><span class="sxs-lookup"><span data-stu-id="25574-113">Opcode</span></span>  | <span data-ttu-id="25574-114">Maken</span><span class="sxs-lookup"><span data-stu-id="25574-114">Create</span></span>                                      |
| <span data-ttu-id="25574-115">Taak</span><span class="sxs-lookup"><span data-stu-id="25574-115">Task</span></span>    | <span data-ttu-id="25574-116">CommandStart</span><span class="sxs-lookup"><span data-stu-id="25574-116">CommandStart</span></span>                                |
| <span data-ttu-id="25574-117">Sleutelwoord</span><span class="sxs-lookup"><span data-stu-id="25574-117">Keyword</span></span> | <span data-ttu-id="25574-118">Runspace</span><span class="sxs-lookup"><span data-stu-id="25574-118">Runspace</span></span>                                    |
| <span data-ttu-id="25574-119">Gebeurtenis-id</span><span class="sxs-lookup"><span data-stu-id="25574-119">EventId</span></span> | <span data-ttu-id="25574-120">Engine_ScriptBlockCompiled (0x1008 = 4104)</span><span class="sxs-lookup"><span data-stu-id="25574-120">Engine_ScriptBlockCompiled (0x1008 = 4104)</span></span>  |
| <span data-ttu-id="25574-121">Bericht</span><span class="sxs-lookup"><span data-stu-id="25574-121">Message</span></span> | <span data-ttu-id="25574-122">Het maken van Scriptblock tekst (%1 van %2):</span><span class="sxs-lookup"><span data-stu-id="25574-122">Creating Scriptblock text (%1 of %2):</span></span> </br> <span data-ttu-id="25574-123">%3</span><span class="sxs-lookup"><span data-stu-id="25574-123">%3</span></span> </br> <span data-ttu-id="25574-124">ScriptBlock-ID: %4</span><span class="sxs-lookup"><span data-stu-id="25574-124">ScriptBlock ID: %4</span></span> |


<span data-ttu-id="25574-125">De tekst die is ingesloten in het bericht is de omvang van het scriptblok gecompileerd.</span><span class="sxs-lookup"><span data-stu-id="25574-125">The text embedded in the message is the extent of the script block compiled.</span></span> <span data-ttu-id="25574-126">De ID is een GUID die de levensduur van het scriptblok wordt bewaard.</span><span class="sxs-lookup"><span data-stu-id="25574-126">The ID is a GUID that is retained for the life of the script block.</span></span>

<span data-ttu-id="25574-127">Wanneer u uitgebreide logboekregistratie inschakelt, wordt de functie voor schrijfbewerkingen beginnen en eindigen markeringen:</span><span class="sxs-lookup"><span data-stu-id="25574-127">When you enable verbose logging, the feature writes begin and end markers:</span></span>

| <span data-ttu-id="25574-128">Kanaal</span><span class="sxs-lookup"><span data-stu-id="25574-128">Channel</span></span> | <span data-ttu-id="25574-129">Operationele</span><span class="sxs-lookup"><span data-stu-id="25574-129">Operational</span></span>                                            |
|---------|--------------------------------------------------------|
| <span data-ttu-id="25574-130">Niveau</span><span class="sxs-lookup"><span data-stu-id="25574-130">Level</span></span>   | <span data-ttu-id="25574-131">Verbose</span><span class="sxs-lookup"><span data-stu-id="25574-131">Verbose</span></span>                                                |
| <span data-ttu-id="25574-132">Opcode</span><span class="sxs-lookup"><span data-stu-id="25574-132">Opcode</span></span>  | <span data-ttu-id="25574-133">Open (/ sluiten)</span><span class="sxs-lookup"><span data-stu-id="25574-133">Open (/ Close)</span></span>                                         |
| <span data-ttu-id="25574-134">Taak</span><span class="sxs-lookup"><span data-stu-id="25574-134">Task</span></span>    | <span data-ttu-id="25574-135">CommandStart (/ CommandStop)</span><span class="sxs-lookup"><span data-stu-id="25574-135">CommandStart (/ CommandStop)</span></span>                           |
| <span data-ttu-id="25574-136">Sleutelwoord</span><span class="sxs-lookup"><span data-stu-id="25574-136">Keyword</span></span> | <span data-ttu-id="25574-137">Runspace</span><span class="sxs-lookup"><span data-stu-id="25574-137">Runspace</span></span>                                               |
| <span data-ttu-id="25574-138">Gebeurtenis-id</span><span class="sxs-lookup"><span data-stu-id="25574-138">EventId</span></span> | <span data-ttu-id="25574-139">ScriptBlock\_aanroepen\_Start\_Detail (0x1009 = 4105) /</span><span class="sxs-lookup"><span data-stu-id="25574-139">ScriptBlock\_Invoke\_Start\_Detail (0x1009 = 4105) /</span></span> </br> <span data-ttu-id="25574-140">ScriptBlock\_aanroepen\_voltooid\_Detail (0x100A = 4106)</span><span class="sxs-lookup"><span data-stu-id="25574-140">ScriptBlock\_Invoke\_Complete\_Detail (0x100A = 4106)</span></span> |
| <span data-ttu-id="25574-141">Bericht</span><span class="sxs-lookup"><span data-stu-id="25574-141">Message</span></span> | <span data-ttu-id="25574-142">Gestarte (/ voltooide)-aanroep van ScriptBlock-ID: %1</span><span class="sxs-lookup"><span data-stu-id="25574-142">Started (/ Completed) invocation of ScriptBlock ID: %1</span></span> </br> <span data-ttu-id="25574-143">Runspace-ID: %2</span><span class="sxs-lookup"><span data-stu-id="25574-143">Runspace ID: %2</span></span> |

<span data-ttu-id="25574-144">De ID is de GUID die vertegenwoordigt het scriptblok (die kan worden gecorreleerd met gebeurtenis-ID 0x1008) en de Runspace-ID vertegenwoordigt de runspace op waarin dit scriptblok is uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="25574-144">The ID is the GUID representing the script block (that can be correlated with event ID 0x1008), and the Runspace ID represents the runspace in which this script block was run.</span></span>

<span data-ttu-id="25574-145">Procenttekens in het bericht het aanroepen van vertegenwoordigen gestructureerde ETW-eigenschappen.</span><span class="sxs-lookup"><span data-stu-id="25574-145">Percent signs in the invocation message represent structured ETW properties.</span></span> <span data-ttu-id="25574-146">Terwijl ze worden vervangen door de werkelijke waarden in de berichttekst, een krachtigere manier toegang tot deze worden opgehaald van het bericht met de cmdlet Get-WinEvent en gebruik vervolgens de **eigenschappen** matrix van het bericht.</span><span class="sxs-lookup"><span data-stu-id="25574-146">While they are replaced with the actual values in the message text, a more robust way to access them is to retrieve the message with the Get-WinEvent cmdlet, and then use the **Properties** array of the message.</span></span>

<span data-ttu-id="25574-147">Hier volgt een voorbeeld van hoe deze functie uitpakken een schadelijke poging kunt voor het versleutelen en verbergen, een script weergeven:</span><span class="sxs-lookup"><span data-stu-id="25574-147">Here's an example of how this functionality can help unwrap a malicious attempt to encrypt and obfuscate a script:</span></span>

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

<span data-ttu-id="25574-148">Dit uitgevoerd, wordt de volgende logboekvermeldingen gegenereerd:</span><span class="sxs-lookup"><span data-stu-id="25574-148">Running this generates the following log entries:</span></span>

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

Windows PowerShell verbroken als het script bloklengte groter is dan wat ETW is geschikt voor bedrijf in één gebeurtenis, het script in meerdere delen. <span data-ttu-id="25574-150">Hier volgt voorbeeldcode voor een script van de berichten in het logboek elke:</span><span class="sxs-lookup"><span data-stu-id="25574-150">Here is sample code to recombine a script from its log messages:</span></span>

```powershell
$created = Get-WinEvent -FilterHashtable @{ ProviderName="Microsoft-Windows-PowerShell"; Id = 4104 } | Where-Object { $_.<...> }
$sortedScripts = $created | sort { $_.Properties[0].Value }
$mergedScript = -join ($sortedScripts | % { $_.Properties[2].Value })
```

<span data-ttu-id="25574-151">Net als bij alle logboekregistratie systemen waarvoor een buffer beperkt bewaren (dat wil zeggen ETW-Logboeken) is een aanval op deze infrastructuur voor het logboek met onnodig gebeurtenissen voor het verbergen van eerdere bewijs overspoelen.</span><span class="sxs-lookup"><span data-stu-id="25574-151">As with all logging systems that have a limited retention buffer (i.e. ETW logs), one attack against this infrastructure is to flood the log with spurious events to hide earlier evidence.</span></span> <span data-ttu-id="25574-152">Om u te beschermen tegen deze aanval, zorg ervoor dat er een vorm van gebeurtenislogboek verzameling instellen (dat wil zeggen, Windows Event Forwarding, [ontdekken van de Adversary met bewaking van Windows-gebeurtenislogboek](http://www.nsa.gov/ia/_files/app/Spotting_the_Adversary_with_Windows_Event_Log_Monitoring.pdf)) gebeurtenislogboeken af bij de computer als verplaatsen snel mogelijk.</span><span class="sxs-lookup"><span data-stu-id="25574-152">To protect yourself from this attack, ensure that you have some form of event log collection set up (i.e., Windows Event Forwarding, [Spotting the Adversary with Windows Event Log Monitoring](http://www.nsa.gov/ia/_files/app/Spotting_the_Adversary_with_Windows_Event_Log_Monitoring.pdf)) to move event logs off of the computer as soon as possible.</span></span>
