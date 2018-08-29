---
ms.date: 08/27/2018
keywords: PowerShell-cmdlet
title: Informatie over opdrachten verkrijgen
ms.assetid: 56f8e5b4-d97c-4e59-abbe-bf13e464eb0d
ms.openlocfilehash: f4238927f10b4204cd3e23f0b0453011f54cb04a
ms.sourcegitcommit: 59727f71dc204785a1bcdedc02716d8340a77aeb
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 08/28/2018
ms.locfileid: "43134007"
---
# <a name="getting-information-about-commands"></a><span data-ttu-id="6a940-103">Informatie over opdrachten verkrijgen</span><span class="sxs-lookup"><span data-stu-id="6a940-103">Getting information about commands</span></span>

<span data-ttu-id="6a940-104">De PowerShell `Get-Command` geeft opdrachten die beschikbaar in uw huidige sessie zijn.</span><span class="sxs-lookup"><span data-stu-id="6a940-104">The PowerShell `Get-Command` displays commands that are available in your current session.</span></span>
<span data-ttu-id="6a940-105">Bij het uitvoeren van de `Get-Command` cmdlet, ziet u iets die vergelijkbaar is met de volgende uitvoer:</span><span class="sxs-lookup"><span data-stu-id="6a940-105">When you run the `Get-Command` cmdlet, you see something similar to the following output:</span></span>

```output
CommandType     Name                    Version    Source
-----------     ----                    -------    ------
Cmdlet          Add-Computer            3.1.0.0    Microsoft.PowerShell.Management
Cmdlet          Add-Content             3.1.0.0    Microsoft.PowerShell.Management
Cmdlet          Add-History             3.0.0.0    Microsoft.PowerShell.Core
Cmdlet          Add-JobTrigger          1.1.0.0    PSScheduledJob
Cmdlet          Add-LocalGroupMember    1.0.0.0    Microsoft.PowerShell.LocalAccounts
Cmdlet          Add-Member              3.1.0.0    Microsoft.PowerShell.Utility
Cmdlet          Add-PSSnapin            3.0.0.0    Microsoft.PowerShell.Core
Cmdlet          Add-Type                3.1.0.0    Microsoft.PowerShell.Utility
...
```

<span data-ttu-id="6a940-106">Dit ziet er veel uitvoer als in het Help-informatie van Cmd.exe: een tabellaire overzicht van interne opdrachten.</span><span class="sxs-lookup"><span data-stu-id="6a940-106">This output looks a lot like the Help output of Cmd.exe: a tabular summary of internal commands.</span></span> <span data-ttu-id="6a940-107">In het fragment van het `Get-Command` opdracht uitvoer hierboven, elke opdracht die wordt weergegeven een CommandType Cmdlet heeft.</span><span class="sxs-lookup"><span data-stu-id="6a940-107">In the excerpt of the `Get-Command` command output shown above, every command shown has a CommandType of Cmdlet.</span></span> <span data-ttu-id="6a940-108">Een cmdlet is van PowerShell intrinsieke opdrachttype.</span><span class="sxs-lookup"><span data-stu-id="6a940-108">A cmdlet is PowerShell's intrinsic command type.</span></span> <span data-ttu-id="6a940-109">Dit type komt overeen met ongeveer naar opdrachten zoals `dir` en `cd` in Cmd.exe of de ingebouwde opdrachten van Unix shells zoals bash.</span><span class="sxs-lookup"><span data-stu-id="6a940-109">This type corresponds roughly to commands like `dir` and `cd` in Cmd.exe or the built-in commands of Unix shells like bash.</span></span>

<span data-ttu-id="6a940-110">De `Get-Command` cmdlet heeft een **syntaxis** parameter die de syntaxis van elke cmdlet retourneert.</span><span class="sxs-lookup"><span data-stu-id="6a940-110">The `Get-Command` cmdlet has a **Syntax** parameter that returns syntax of each cmdlet.</span></span> <span data-ttu-id="6a940-111">Het volgende voorbeeld laat zien hoe de syntaxis van de `Get-Help` cmdlet:</span><span class="sxs-lookup"><span data-stu-id="6a940-111">The following example shows how to get the syntax of the `Get-Help` cmdlet:</span></span>

```powershell
Get-Command Get-Help -Syntax
```

```output
Get-Help [[-Name] <String>] [-Path <String>] [-Category <String[]>] [-Component <String[]>] [-Functionality <String[]>]
 [-Role <String[]>] [-Full] [-Online] [-Verbose] [-Debug] [-ErrorAction <ActionPreference>] [-WarningAction <ActionPreference>] [-ErrorVariable <String>] [-WarningVariable <String>] [-OutVariable <String>] [-OutBuffer <Int32>]

Get-Help [[-Name] <String>] [-Path <String>] [-Category <String[]>] [-Component <String[]>] [-Functionality <String[]>]
 [-Role <String[]>] [-Detailed] [-Online] [-Verbose] [-Debug] [-ErrorAction <ActionPreference>] [-WarningAction <ActionPreference>] [-ErrorVariable <String>] [-WarningVariable <String>] [-OutVariable <String>] [-OutBuffer <Int32>]

Get-Help [[-Name] <String>] [-Path <String>] [-Category <String[]>] [-Component <String[]>] [-Functionality <String[]>]
 [-Role <String[]>] [-Examples] [-Online] [-Verbose] [-Debug] [-ErrorAction <ActionPreference>] [-WarningAction <ActionPreference>] [-ErrorVariable <String>] [-WarningVariable <String>] [-OutVariable <String>] [-OutBuffer <Int32>]

Get-Help [[-Name] <String>] [-Path <String>] [-Category <String[]>] [-Component <String[]>] [-Functionality <String[]>]
 [-Role <String[]>] [-Parameter <String>] [-Online] [-Verbose] [-Debug] [-ErrorAction <ActionPreference>] [-WarningAction <ActionPreference>] [-ErrorVariable <String>] [-WarningVariable <String>] [-OutVariable <String>] [-OutBuffer <Int32>]
```

## <a name="displaying-available-command-by-type"></a><span data-ttu-id="6a940-112">Beschikbare opdracht weergeven per type</span><span class="sxs-lookup"><span data-stu-id="6a940-112">Displaying available command by type</span></span>

<span data-ttu-id="6a940-113">De `Get-Command` opdracht geeft alleen de cmdlets in de huidige sessie.</span><span class="sxs-lookup"><span data-stu-id="6a940-113">The `Get-Command` command lists only the cmdlets in the current session.</span></span> <span data-ttu-id="6a940-114">PowerShell ondersteunt daadwerkelijk diverse andere soorten opdrachten:</span><span class="sxs-lookup"><span data-stu-id="6a940-114">PowerShell actually supports several other types of commands:</span></span>

- <span data-ttu-id="6a940-115">Aliassen</span><span class="sxs-lookup"><span data-stu-id="6a940-115">Aliases</span></span>
- <span data-ttu-id="6a940-116">Functies</span><span class="sxs-lookup"><span data-stu-id="6a940-116">Functions</span></span>
- <span data-ttu-id="6a940-117">Scripts</span><span class="sxs-lookup"><span data-stu-id="6a940-117">Scripts</span></span>

<span data-ttu-id="6a940-118">Externe uitvoerbare bestanden of bestanden waarvoor een geregistreerde type handler, zijn ook geclassificeerd als opdrachten.</span><span class="sxs-lookup"><span data-stu-id="6a940-118">External executable files, or files that have a registered file type handler, are also classified as commands.</span></span>

<span data-ttu-id="6a940-119">Als alle opdrachten in de sessie, typt u:</span><span class="sxs-lookup"><span data-stu-id="6a940-119">To get all commands in the session, type:</span></span>

```powershell
Get-Command *
```

<span data-ttu-id="6a940-120">Deze lijst bevat externe opdrachten in het pad voor de zoekopdracht, zodat deze duizenden items kan bevatten.</span><span class="sxs-lookup"><span data-stu-id="6a940-120">This list includes external commands in your search path so it can contain thousands of items.</span></span>
<span data-ttu-id="6a940-121">Dit is meer handig om te kijken naar een lagere reeks opdrachten.</span><span class="sxs-lookup"><span data-stu-id="6a940-121">It is more useful to look at a reduced set of commands.</span></span>

> [!NOTE]
> <span data-ttu-id="6a940-122">Het sterretje (\*) wordt gebruikt voor vergelijking in PowerShell opdrachtargumenten met jokertekens.</span><span class="sxs-lookup"><span data-stu-id="6a940-122">The asterisk (\*) is used for wildcard matching in PowerShell command arguments.</span></span> <span data-ttu-id="6a940-123">De \* betekent 'overeenkomstig met een of meer van de tekens'.</span><span class="sxs-lookup"><span data-stu-id="6a940-123">The \* means "match one or more of any characters".</span></span> <span data-ttu-id="6a940-124">U kunt typen `Get-Command a*` vinden alle opdrachten die met de letter beginnen "a".</span><span class="sxs-lookup"><span data-stu-id="6a940-124">You can type `Get-Command a*` to find all commands that begin with the letter "a".</span></span> <span data-ttu-id="6a940-125">In tegenstelling tot vergelijking in Cmd.exe met jokertekens, wordt de PowerShell-jokertekens ook overeenkomen met een periode.</span><span class="sxs-lookup"><span data-stu-id="6a940-125">Unlike wildcard matching in Cmd.exe, PowerShell's wildcard will also match a period.</span></span>

<span data-ttu-id="6a940-126">Gebruik de **CommandType** parameter van `Get-Command` om op te halen van systeemeigen opdrachten van andere typen.</span><span class="sxs-lookup"><span data-stu-id="6a940-126">Use the **CommandType** parameter of `Get-Command` to get native commands of other types.</span></span>
<span data-ttu-id="6a940-127">cmdlet.</span><span class="sxs-lookup"><span data-stu-id="6a940-127">cmdlet.</span></span>

<span data-ttu-id="6a940-128">Als Opdrachtaliassen, die de toegewezen bijnamen van opdrachten, typt u:</span><span class="sxs-lookup"><span data-stu-id="6a940-128">To get command aliases, which are the assigned nicknames of commands, type:</span></span>

```powershell
Get-Command -CommandType Alias
```

<span data-ttu-id="6a940-129">Als u de functies in de huidige sessie, typt u:</span><span class="sxs-lookup"><span data-stu-id="6a940-129">To get the functions in the current session, type:</span></span>

```powershell
Get-Command -CommandType Function
```

<span data-ttu-id="6a940-130">Als scripts in de PowerShell-zoekpad weergeven, typt u:</span><span class="sxs-lookup"><span data-stu-id="6a940-130">To display scripts in PowerShell's search path, type:</span></span>

```powershell
Get-Command -CommandType Script
```