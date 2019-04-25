---
ms.date: 08/27/2018
keywords: PowerShell-cmdlet
title: Informatie over opdrachten verkrijgen
ms.assetid: 56f8e5b4-d97c-4e59-abbe-bf13e464eb0d
ms.openlocfilehash: 7af83e3a0e776d96e580b442430357b4ea063a72
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62057703"
---
# <a name="getting-information-about-commands"></a>Informatie over opdrachten verkrijgen

De PowerShell `Get-Command` geeft opdrachten die beschikbaar in uw huidige sessie zijn.
Bij het uitvoeren van de `Get-Command` cmdlet, ziet u iets die vergelijkbaar is met de volgende uitvoer:

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

Dit ziet er veel uitvoer als in het Help-informatie van **cmd.exe**: een tabellaire overzicht van interne opdrachten. In het fragment van het `Get-Command` opdracht uitvoer hierboven, elke opdracht die wordt weergegeven een CommandType Cmdlet heeft. Een cmdlet is van PowerShell intrinsieke opdrachttype. Dit type komt overeen met ongeveer naar opdrachten zoals `dir` en `cd` in **cmd.exe** of de ingebouwde opdrachten van de Unix-houders zoals bash.

De `Get-Command` cmdlet heeft een **syntaxis** parameter die de syntaxis van elke cmdlet retourneert. Het volgende voorbeeld laat zien hoe de syntaxis van de `Get-Help` cmdlet:

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

## <a name="displaying-available-command-by-type"></a>Beschikbare opdracht weergeven per type

De `Get-Command` opdracht geeft alleen de cmdlets in de huidige sessie. PowerShell ondersteunt daadwerkelijk diverse andere soorten opdrachten:

- Aliassen
- Functies
- Scripts

Externe uitvoerbare bestanden of bestanden waarvoor een geregistreerde type handler, zijn ook geclassificeerd als opdrachten.

Als alle opdrachten in de sessie, typt u:

```powershell
Get-Command *
```

Deze lijst bevat externe opdrachten in het pad voor de zoekopdracht, zodat deze duizenden items kan bevatten.
Dit is meer handig om te kijken naar een lagere reeks opdrachten.

> [!NOTE]
> Het sterretje (\*) wordt gebruikt voor vergelijking in PowerShell opdrachtargumenten met jokertekens. De \* betekent 'overeenkomstig met een of meer van de tekens'. U kunt typen `Get-Command a*` vinden alle opdrachten die met de letter beginnen "a". In tegenstelling tot jokertekens **cmd.exe**, van PowerShell jokerteken wordt ook overeenkomen met een punt.

Gebruik de **CommandType** parameter van `Get-Command` om op te halen van systeemeigen opdrachten van andere typen.
cmdlet.

Als Opdrachtaliassen, die de toegewezen bijnamen van opdrachten, typt u:

```powershell
Get-Command -CommandType Alias
```

Als u de functies in de huidige sessie, typt u:

```powershell
Get-Command -CommandType Function
```

Als scripts in de PowerShell-zoekpad weergeven, typt u:

```powershell
Get-Command -CommandType Script
```