---
ms.date: 08/27/2018
keywords: powershell,cmdlet
title: Informatie over opdrachten verkrijgen
ms.openlocfilehash: eb918c6f89d8369db775258263a8f7a7902a6cc7
ms.sourcegitcommit: 2aec310ad0c0b048400cb56f6fa64c1e554c812a
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 05/23/2020
ms.locfileid: "83810104"
---
# <a name="getting-information-about-commands"></a><span data-ttu-id="e468e-103">Informatie over opdrachten verkrijgen</span><span class="sxs-lookup"><span data-stu-id="e468e-103">Getting information about commands</span></span>

<span data-ttu-id="e468e-104">De Power shell- `Get-Command` opdrachten die beschikbaar zijn in uw huidige sessie worden weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="e468e-104">The PowerShell `Get-Command` displays commands that are available in your current session.</span></span>
<span data-ttu-id="e468e-105">Wanneer u de `Get-Command` cmdlet uitvoert, ziet u iets zoals in de volgende uitvoer:</span><span class="sxs-lookup"><span data-stu-id="e468e-105">When you run the `Get-Command` cmdlet, you see something similar to the following output:</span></span>

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

<span data-ttu-id="e468e-106">Deze uitvoer lijkt veel op de Help-uitvoer van **cmd. exe**: een samen vatting van interne opdrachten in tabel vorm.</span><span class="sxs-lookup"><span data-stu-id="e468e-106">This output looks a lot like the Help output of **cmd.exe**: a tabular summary of internal commands.</span></span> <span data-ttu-id="e468e-107">In het fragment van de `Get-Command` opdracht uitvoer die hierboven wordt weer gegeven, heeft elke opdracht die wordt weer gegeven een CommandType van cmdlet.</span><span class="sxs-lookup"><span data-stu-id="e468e-107">In the excerpt of the `Get-Command` command output shown above, every command shown has a CommandType of Cmdlet.</span></span> <span data-ttu-id="e468e-108">Een cmdlet is het intrinsieke opdracht type van Power shell.</span><span class="sxs-lookup"><span data-stu-id="e468e-108">A cmdlet is PowerShell's intrinsic command type.</span></span> <span data-ttu-id="e468e-109">Dit type komt ongeveer overeen met opdrachten als `dir` en `cd` in **cmd. exe** of de ingebouwde opdrachten van UNIX-shells, zoals bash.</span><span class="sxs-lookup"><span data-stu-id="e468e-109">This type corresponds roughly to commands like `dir` and `cd` in **cmd.exe** or the built-in commands of Unix shells like bash.</span></span>

<span data-ttu-id="e468e-110">De `Get-Command` cmdlet heeft een **syntaxis** parameter die de syntaxis van elke cmdlet retourneert.</span><span class="sxs-lookup"><span data-stu-id="e468e-110">The `Get-Command` cmdlet has a **Syntax** parameter that returns syntax of each cmdlet.</span></span> <span data-ttu-id="e468e-111">In het volgende voor beeld ziet u hoe u de syntaxis van de cmdlet kunt ophalen `Get-Help` :</span><span class="sxs-lookup"><span data-stu-id="e468e-111">The following example shows how to get the syntax of the `Get-Help` cmdlet:</span></span>

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

## <a name="displaying-available-command-by-type"></a><span data-ttu-id="e468e-112">De beschik bare opdracht wordt weer gegeven op type</span><span class="sxs-lookup"><span data-stu-id="e468e-112">Displaying available command by type</span></span>

<span data-ttu-id="e468e-113">De `Get-Command` opdracht bevat alleen de cmdlets in de huidige sessie.</span><span class="sxs-lookup"><span data-stu-id="e468e-113">The `Get-Command` command lists only the cmdlets in the current session.</span></span> <span data-ttu-id="e468e-114">Power shell ondersteunt diverse andere soorten opdrachten:</span><span class="sxs-lookup"><span data-stu-id="e468e-114">PowerShell actually supports several other types of commands:</span></span>

- <span data-ttu-id="e468e-115">Aliassen</span><span class="sxs-lookup"><span data-stu-id="e468e-115">Aliases</span></span>
- <span data-ttu-id="e468e-116">Functions</span><span class="sxs-lookup"><span data-stu-id="e468e-116">Functions</span></span>
- <span data-ttu-id="e468e-117">Scripts</span><span class="sxs-lookup"><span data-stu-id="e468e-117">Scripts</span></span>

<span data-ttu-id="e468e-118">Externe uitvoer bare bestanden of bestanden met een geregistreerde bestands type-handler worden ook als opdrachten geclassificeerd.</span><span class="sxs-lookup"><span data-stu-id="e468e-118">External executable files, or files that have a registered file type handler, are also classified as commands.</span></span>

<span data-ttu-id="e468e-119">Als u alle opdrachten in de sessie wilt ophalen, typt u:</span><span class="sxs-lookup"><span data-stu-id="e468e-119">To get all commands in the session, type:</span></span>

```powershell
Get-Command *
```

<span data-ttu-id="e468e-120">Deze lijst bevat externe opdrachten in uw zoekpad, zodat deze duizenden items kan bevatten.</span><span class="sxs-lookup"><span data-stu-id="e468e-120">This list includes external commands in your search path so it can contain thousands of items.</span></span>
<span data-ttu-id="e468e-121">Het is handiger om een gereduceerde reeks opdrachten te bekijken.</span><span class="sxs-lookup"><span data-stu-id="e468e-121">It is more useful to look at a reduced set of commands.</span></span>

> [!NOTE]
> <span data-ttu-id="e468e-122">Het sterretje ( \* ) wordt gebruikt voor het vergelijken van joker tekens in Power shell-opdracht argumenten.</span><span class="sxs-lookup"><span data-stu-id="e468e-122">The asterisk (\*) is used for wildcard matching in PowerShell command arguments.</span></span> <span data-ttu-id="e468e-123">De \* betekent ' overeenkomen met een of meer wille keurige tekens '.</span><span class="sxs-lookup"><span data-stu-id="e468e-123">The \* means "match one or more of any characters".</span></span> <span data-ttu-id="e468e-124">U kunt typen `Get-Command a*` om te zoeken naar alle opdrachten die beginnen met de letter "a".</span><span class="sxs-lookup"><span data-stu-id="e468e-124">You can type `Get-Command a*` to find all commands that begin with the letter "a".</span></span> <span data-ttu-id="e468e-125">In tegens telling tot joker tekens in **cmd. exe**komt het Joker teken van Power shell ook overeen met een punt.</span><span class="sxs-lookup"><span data-stu-id="e468e-125">Unlike wildcard matching in **cmd.exe**, PowerShell's wildcard will also match a period.</span></span>

<span data-ttu-id="e468e-126">Gebruik de **CommandType** -para meter van `Get-Command` om systeem eigen opdrachten van andere typen op te halen.</span><span class="sxs-lookup"><span data-stu-id="e468e-126">Use the **CommandType** parameter of `Get-Command` to get native commands of other types.</span></span>
<span data-ttu-id="e468e-127">cmdlet.</span><span class="sxs-lookup"><span data-stu-id="e468e-127">cmdlet.</span></span>

<span data-ttu-id="e468e-128">Om opdracht aliassen te verkrijgen, zoals de toegewezen bijnamen van opdrachten, typt u:</span><span class="sxs-lookup"><span data-stu-id="e468e-128">To get command aliases, which are the assigned nicknames of commands, type:</span></span>

```powershell
Get-Command -CommandType Alias
```

<span data-ttu-id="e468e-129">Als u de functies in de huidige sessie wilt ophalen, typt u:</span><span class="sxs-lookup"><span data-stu-id="e468e-129">To get the functions in the current session, type:</span></span>

```powershell
Get-Command -CommandType Function
```

<span data-ttu-id="e468e-130">Als u scripts wilt weer geven in het zoekpad van Power shell, typt u:</span><span class="sxs-lookup"><span data-stu-id="e468e-130">To display scripts in PowerShell's search path, type:</span></span>

```powershell
Get-Command -CommandType Script
```
