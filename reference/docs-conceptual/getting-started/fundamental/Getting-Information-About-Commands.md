---
ms.date: 2017-06-05
keywords: PowerShell-cmdlet
title: Informatie ophalen over opdrachten
ms.assetid: 56f8e5b4-d97c-4e59-abbe-bf13e464eb0d
ms.openlocfilehash: 98e449110860ea81939d6ec0b7b1a8534a2da2aa
ms.sourcegitcommit: 74255f0b5f386a072458af058a15240140acb294
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 08/03/2017
---
# <a name="getting-information-about-commands"></a>Informatie ophalen over opdrachten
De Windows PowerShell **Get-Command** cmdlet haalt alle opdrachten die beschikbaar in de huidige sessie zijn. Wanneer u typt **Get-Command** bij een Windows PowerShell-prompt ziet u uitvoer die vergelijkbaar is met het volgende:

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

In de uitvoer van de **Get-Command** opdracht, de definities eindigen op de weglatingstekens (...) om aan te geven dat de inhoud door PowerShell kan niet worden weergegeven in de beschikbare ruimte. Wanneer de uitvoer wordt weergegeven in Windows PowerShell, de uitvoer als tekst indelingen en vervolgens rangschikt zodat de gegevens correct in het venster past. We zullen hebben over deze later in de sectie op formatters.

De **Get-Command** cmdlet heeft een **syntaxis** parameter die de syntaxis van elke cmdlet opgehaald. Als u de syntaxis van de cmdlet Get-Help, gebruikt u de volgende opdracht:

**GET-opdracht Get-Help-syntaxis**

```
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

```
Get-Command *
```

Omdat deze lijst externe bestanden in uw zoekpad bevat, kan het duizenden items bevatten. Dit is meer handig om te kijken naar een beperkte reeks opdrachten.

Als u ingebouwde opdrachten van andere typen, gebruikt de **CommandType** parameter van de **Get-Command** cmdlet.

> [!NOTE]
> Het sterretje (\*) wordt gebruikt voor de vergelijking argumenten in Windows PowerShell-opdracht met jokertekens. De \* betekent 'overeenkomstig met een of meer van de tekens'. U kunt typen **Get-Command een\&#42;** vinden alle opdrachten die met de letter beginnen "a". In tegenstelling tot jokerteken identieke in Cmd.exe jokertekens van Windows PowerShell ook overeen met een periode.

Als u de opdracht-aliassen die de toegewezen bijnaam van opdrachten, typt u:

```
Get-Command -CommandType Alias
```

Als u de functies in de huidige sessie, typt u:

```
Get-Command -CommandType Function
```

Als scripts in de Windows PowerShell-zoekpad weergeven, typt u:

```
Get-Command -CommandType Script
```

