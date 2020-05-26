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
# <a name="getting-information-about-commands"></a>Informatie over opdrachten verkrijgen

De Power shell- `Get-Command` opdrachten die beschikbaar zijn in uw huidige sessie worden weer gegeven.
Wanneer u de `Get-Command` cmdlet uitvoert, ziet u iets zoals in de volgende uitvoer:

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

Deze uitvoer lijkt veel op de Help-uitvoer van **cmd. exe**: een samen vatting van interne opdrachten in tabel vorm. In het fragment van de `Get-Command` opdracht uitvoer die hierboven wordt weer gegeven, heeft elke opdracht die wordt weer gegeven een CommandType van cmdlet. Een cmdlet is het intrinsieke opdracht type van Power shell. Dit type komt ongeveer overeen met opdrachten als `dir` en `cd` in **cmd. exe** of de ingebouwde opdrachten van UNIX-shells, zoals bash.

De `Get-Command` cmdlet heeft een **syntaxis** parameter die de syntaxis van elke cmdlet retourneert. In het volgende voor beeld ziet u hoe u de syntaxis van de cmdlet kunt ophalen `Get-Help` :

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

## <a name="displaying-available-command-by-type"></a>De beschik bare opdracht wordt weer gegeven op type

De `Get-Command` opdracht bevat alleen de cmdlets in de huidige sessie. Power shell ondersteunt diverse andere soorten opdrachten:

- Aliassen
- Functions
- Scripts

Externe uitvoer bare bestanden of bestanden met een geregistreerde bestands type-handler worden ook als opdrachten geclassificeerd.

Als u alle opdrachten in de sessie wilt ophalen, typt u:

```powershell
Get-Command *
```

Deze lijst bevat externe opdrachten in uw zoekpad, zodat deze duizenden items kan bevatten.
Het is handiger om een gereduceerde reeks opdrachten te bekijken.

> [!NOTE]
> Het sterretje ( \* ) wordt gebruikt voor het vergelijken van joker tekens in Power shell-opdracht argumenten. De \* betekent ' overeenkomen met een of meer wille keurige tekens '. U kunt typen `Get-Command a*` om te zoeken naar alle opdrachten die beginnen met de letter "a". In tegens telling tot joker tekens in **cmd. exe**komt het Joker teken van Power shell ook overeen met een punt.

Gebruik de **CommandType** -para meter van `Get-Command` om systeem eigen opdrachten van andere typen op te halen.
cmdlet.

Om opdracht aliassen te verkrijgen, zoals de toegewezen bijnamen van opdrachten, typt u:

```powershell
Get-Command -CommandType Alias
```

Als u de functies in de huidige sessie wilt ophalen, typt u:

```powershell
Get-Command -CommandType Function
```

Als u scripts wilt weer geven in het zoekpad van Power shell, typt u:

```powershell
Get-Command -CommandType Script
```
