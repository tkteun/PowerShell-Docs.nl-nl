---
ms.date: 06/05/2017
keywords: PowerShell-cmdlet
title: Informatie over opdrachten verkrijgen
ms.assetid: 56f8e5b4-d97c-4e59-abbe-bf13e464eb0d
ms.openlocfilehash: c51579fe2cdf4f2a0d3248d1aaf3f1f9cac83868
ms.sourcegitcommit: 735ccab3fb3834ccd8559fab6700b798e8e5ffbf
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 05/25/2018
---
# <a name="getting-information-about-commands"></a>Informatie over opdrachten verkrijgen
De Windows PowerShell `Get-Command` cmdlet haalt alle opdrachten die beschikbaar in de huidige sessie zijn. Wanneer u typt `Get-Command` achter de PowerShell-prompt, ziet u uitvoer die vergelijkbaar is met het volgende:

```
PS> Get-Command
CommandType     Name                            Definition
-----------     ----                            ----------
Cmdlet          Add-Content                     Add-Content [-Path] <String[...
Cmdlet          Add-History                     Add-History [[-InputObject] ...
Cmdlet          Add-Member                      Add-Member [-MemberType] <PS...
...
```

Dit lijkt veel uitvoer zoals de uitvoer van de Help van Cmd.exe: een tabellaire samenvatting van interne opdrachten. In het fragment van de **Get-Command** opdracht uitvoer hierboven, om de opdracht heeft een CommandType Cmdlet. Een cmdlet zich van Windows PowerShell intrinsieke opdrachttype - een type dat overeenkomt met ongeveer tot de **dir** en **cd** opdrachten van Cmd.exe en dient te worden in de houders UNIX zoals BASH.

In de uitvoer van de `Get-Command` opdracht, de definities eindigen op de weglatingstekens (...) om aan te geven dat de inhoud door PowerShell kan niet worden weergegeven in de beschikbare ruimte. Wanneer de uitvoer wordt weergegeven in Windows PowerShell, de uitvoer als tekst indelingen en vervolgens rangschikt zodat de gegevens correct in het venster past. We zullen hebben over deze later in de sectie op formatters.

De `Get-Command` cmdlet heeft een **syntaxis** parameter die de syntaxis van elke cmdlet opgehaald. Als u de syntaxis van de cmdlet Get-Help, gebruikt u de volgende opdracht:

```
Get-Command Get-Help -Syntax

Get-Help [[-Name] <String>] [-Path <String>] [-Category <String[]>] [-Component <String[]>] [-Functionality <String[]>]
 [-Role <String[]>] [-Full] [-Online] [-Verbose] [-Debug] [-ErrorAction <ActionPreference>] [-WarningAction <ActionPreference>] [-ErrorVariable <String>] [-WarningVariable <String>] [-OutVariable <String>] [-OutBuffer <Int32>]

Get-Help [[-Name] <String>] [-Path <String>] [-Category <String[]>] [-Component <String[]>] [-Functionality <String[]>]
 [-Role <String[]>] [-Detailed] [-Online] [-Verbose] [-Debug] [-ErrorAction <ActionPreference>] [-WarningAction <ActionPreference>] [-ErrorVariable <String>] [-WarningVariable <String>] [-OutVariable <String>] [-OutBuffer <Int32>]

Get-Help [[-Name] <String>] [-Path <String>] [-Category <String[]>] [-Component <String[]>] [-Functionality <String[]>]
 [-Role <String[]>] [-Examples] [-Online] [-Verbose] [-Debug] [-ErrorAction <ActionPreference>] [-WarningAction <ActionPreference>] [-ErrorVariable <String>] [-WarningVariable <String>] [-OutVariable <String>] [-OutBuffer <Int32>]

Get-Help [[-Name] <String>] [-Path <String>] [-Category <String[]>] [-Component <String[]>] [-Functionality <String[]>]
 [-Role <String[]>] [-Parameter <String>] [-Online] [-Verbose] [-Debug] [-ErrorAction <ActionPreference>] [-WarningAction <ActionPreference>] [-ErrorVariable <String>] [-WarningVariable <String>] [-OutVariable <String>] [-OutBuffer <Int32>]
```

### <a name="displaying-available-command-types"></a>Beschikbare opdrachttypen weergeven
De **Get-Command** opdracht de lijst bevat niet alle opdrachten die beschikbaar is in Windows PowerShell. In plaats daarvan de **Get-Command** opdracht geeft alleen de cmdlets in de huidige sessie. Enkele andere soorten opdrachten daadwerkelijk wordt ondersteund door Windows PowerShell. Aliassen, functies en scripts zijn ook Windows PowerShell-opdrachten, hoewel ze niet in de Windows PowerShell User's Guide in detail worden besproken. Externe bestanden die uitvoerbare zijn of een handler van het type geregistreerd bestand ook worden ingedeeld als opdrachten.

Als u alle opdrachten in de sessie, typt u:

```powershell
Get-Command *
```

Omdat deze lijst externe bestanden in uw zoekpad bevat, kan het duizenden items bevatten. Dit is meer handig om te kijken naar een beperkte reeks opdrachten.

Als u ingebouwde opdrachten van andere typen, gebruikt de **CommandType** parameter van de `Get-Command` cmdlet.

> [!NOTE]
> Het sterretje (\*) wordt gebruikt voor de vergelijking argumenten in Windows PowerShell-opdracht met jokertekens. De \* betekent 'overeenkomstig met een of meer van de tekens'. U kunt typen `Get-Command a*` vinden alle opdrachten die met de letter beginnen "a". In tegenstelling tot jokerteken identieke in Cmd.exe jokertekens van Windows PowerShell ook overeen met een periode.

Als u de opdracht-aliassen die de toegewezen bijnaam van opdrachten, typt u:

```powershell
Get-Command -CommandType Alias
```

Als u de functies in de huidige sessie, typt u:

```powershell
Get-Command -CommandType Function
```

Als scripts in de Windows PowerShell-zoekpad weergeven, typt u:

```powershell
Get-Command -CommandType Script
```
