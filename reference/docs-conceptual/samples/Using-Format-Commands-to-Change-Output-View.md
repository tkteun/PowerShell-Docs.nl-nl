---
ms.date: 11/22/2019
keywords: Power shell, cmdlet
title: Format-opdrachten gebruiken om de uitvoerweergave te wijzigen
ms.openlocfilehash: f270d5ec5efe5caf506d6a8a45285990996f6ae6
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 12/05/2019
ms.locfileid: "74417585"
---
# <a name="using-format-commands-to-change-output-view"></a>Format-opdrachten gebruiken om de uitvoerweergave te wijzigen

Power Shell heeft een set cmdlets waarmee u kunt bepalen hoe eigenschappen voor bepaalde objecten worden weer gegeven. De namen van alle cmdlets beginnen met de term `Format`. Hiermee kunt u selecteren welke eigenschappen u wilt weer geven.

```powershell
Get-Command -Verb Format -Module Microsoft.PowerShell.Utility
```

```Output
CommandType     Name               Version    Source
-----------     ----               -------    ------
Cmdlet          Format-Custom      6.1.0.0    Microsoft.PowerShell.Utility
Cmdlet          Format-Hex         6.1.0.0    Microsoft.PowerShell.Utility
Cmdlet          Format-List        6.1.0.0    Microsoft.PowerShell.Utility
Cmdlet          Format-Table       6.1.0.0    Microsoft.PowerShell.Utility
Cmdlet          Format-Wide        6.1.0.0    Microsoft.PowerShell.Utility
```

In dit artikel worden de cmdlets `Format-Wide`, `Format-List`en `Format-Table` beschreven.

Elk object type in Power Shell heeft standaard eigenschappen die worden gebruikt wanneer u niet opgeeft welke eigenschappen moeten worden weer gegeven. Elke cmdlet gebruikt ook dezelfde **eigenschaps** parameter om op te geven welke eigenschappen u wilt weer geven. Omdat `Format-Wide` slechts één eigenschap toont, neemt de **eigenschaps** parameter slechts één waarde in beslag, maar de eigenschaps parameters van `Format-List` en `Format-Table` een lijst met eigenschaps namen accepteren.

In dit voor beeld toont de standaard uitvoer van `Get-Process`-cmdlet dat er twee exemplaren van Internet Explorer worden uitgevoerd.

```powershell
Get-Process -Name iexplore
```

De standaard indeling voor **proces** objecten toont de eigenschappen die hier worden weer gegeven:

```Output
 NPM(K)    PM(M)      WS(M)     CPU(s)      Id  SI ProcessName
 ------    -----      -----     ------      --  -- -----------
     32    25.52      10.25      13.11   12808   1 iexplore
     52    11.46      26.46       3.55   21748   1 iexplore
```

## <a name="using-format-wide-for-single-item-output"></a>Indeling-breed gebruiken voor uitvoer met één item

De cmdlet `Format-Wide` geeft standaard alleen de eigenschap default van een object weer. De gegevens die aan elk object zijn gekoppeld, worden in één kolom weer gegeven:

```powershell
Get-Command -Verb Format | Format-Wide
```

```Output
Format-Custom          Format-Hex
Format-List            Format-Table
Format-Wide
```

U kunt ook een niet-standaard eigenschap opgeven:

```powershell
Get-Command -Verb Format | Format-Wide -Property Noun
```

```Output
Custom                 Hex
List                   Table
Wide
```

### <a name="controlling-format-wide-display-with-column"></a>Weer gave met volledige indeling beheren met kolom

Met de `Format-Wide` cmdlet kunt u slechts één eigenschap tegelijk weer geven. Dit maakt het handig voor het weer geven van grote lijsten in meerdere kolommen.

```powershell
Get-Command -Verb Format | Format-Wide -Property Noun -Column 3
```

```Output
Custom                 Hex                  List
Table                  Wide

```

## <a name="using-format-list-for-a-list-view"></a>Indelings lijst gebruiken voor een lijst weergave

Met de cmdlet `Format-List` wordt een object in de vorm van een vermelding weer gegeven, waarbij elke eigenschap wordt aangeduid en op een afzonderlijke regel wordt weer gegeven:

```powershell
Get-Process -Name iexplore | Format-List
```

```Output
Id      : 12808
Handles : 578
CPU     : 13.140625
SI      : 1
Name    : iexplore

Id      : 21748
Handles : 641
CPU     : 3.59375
SI      : 1
Name    : iexplore
```

U kunt zoveel eigenschappen opgeven als u wilt:

```powershell
Get-Process -Name iexplore | Format-List -Property ProcessName,FileVersion,StartTime,Id
```

```Output
ProcessName : iexplore
FileVersion : 11.00.18362.1 (WinBuild.160101.0800)
StartTime   : 10/22/2019 11:23:58 AM
Id          : 12808

ProcessName : iexplore
FileVersion : 11.00.18362.1 (WinBuild.160101.0800)
StartTime   : 10/22/2019 11:23:57 AM
Id          : 21748
```

### <a name="getting-detailed-information-by-using-format-list-with-wildcards"></a>Gedetailleerde informatie ophalen met behulp van de indelings lijst met Joker tekens

Met de cmdlet `Format-List` kunt u een Joker teken gebruiken als de waarde van de **eigenschaps** parameter. Hiermee kunt u gedetailleerde gegevens weer geven. Objecten bevatten vaak meer informatie dan u nodig hebt, waarom Power shell niet alle eigenschaps waarden standaard weergeeft. Als u alle eigenschappen van een object wilt weer geven, gebruikt u de opdracht `Format-List -Property *`. Met de volgende opdracht worden meer dan 60 regels uitvoer voor één proces gegenereerd:

```powershell
Get-Process -Name iexplore | Format-List -Property *
```

Hoewel de `Format-List` opdracht nuttig is voor het weer geven van Details als u een overzicht wilt van de uitvoer die veel items bevat, is een eenvoudigere tabellaire weer gave vaak handiger.

## <a name="using-format-table-for-tabular-output"></a>Indelings tabel gebruiken voor tabel uitvoer

Als u de cmdlet `Format-Table` zonder eigenschaps namen hebt opgegeven om de uitvoer van de `Get-Process` opdracht op te maken, krijgt u precies dezelfde uitvoer als u zonder een `Format`-cmdlet. Standaard worden **proces** objecten in Power shell weer gegeven in tabel vorm.

```powershell
Get-Service -Name win* | Format-Table
```

```Output
Status   Name               DisplayName
------   ----               -----------
Running  WinDefend          Windows Defender Antivirus Service
Running  WinHttpAutoProx... WinHTTP Web Proxy Auto-Discovery Se...
Running  Winmgmt            Windows Management Instrumentation
Running  WinRM              Windows Remote Management (WS-Manag...
```

### <a name="improving-format-table-output-autosize"></a>De indeling van de tabel uitvoer verbeteren (AutoSize)

Hoewel een tabellarische weer gave nuttig is voor het weer geven van veel informatie, kan het lastig zijn om te interpreteren of de weer gave te smal is voor de gegevens. In het vorige voor beeld wordt de uitvoer afgekapt. Als u de para meter **AutoSize** opgeeft wanneer u de `Format-Table` opdracht uitvoert, worden in Power shell kolom breedten berekend op basis van de werkelijke gegevens die worden weer gegeven. Hierdoor kunnen de kolommen worden gelezen.

```powershell
Get-Service -Name win* | Format-Table -AutoSize
```

```Output
Status  Name                DisplayName
------  ----                -----------
Running WinDefend           Windows Defender Antivirus Service
Running WinHttpAutoProxySvc WinHTTP Web Proxy Auto-Discovery Service
Running Winmgmt             Windows Management Instrumentation
Running WinRM               Windows Remote Management (WS-Management)
```

De `Format-Table`-cmdlet kan echter nog steeds gegevens afkappen, maar deze worden alleen afgekapt aan het einde van het scherm. Andere eigenschappen dan de laatste die worden weer gegeven, krijgen een groot deel van de grootte, zoals ze nodig hebben voor een juiste weer gave van het langste gegevens element.

```powershell
Get-Service -Name win* | Format-Table -Property Name,Status,StartType,DisplayName,DependentServices -AutoSize
```

```Output
Name                 Status StartType DisplayName                               DependentServi
                                                                                ces
----                 ------ --------- -----------                               --------------
WinDefend           Running Automatic Windows Defender Antivirus Service        {}
WinHttpAutoProxySvc Running    Manual WinHTTP Web Proxy Auto-Discovery Service  {NcaSvc, iphl…
Winmgmt             Running Automatic Windows Management Instrumentation        {vmms, TPHKLO…
WinRM               Running Automatic Windows Remote Management (WS-Management) {}
```

De `Format-Table` opdracht gaat ervan uit dat de eigenschappen worden weer gegeven in volg orde van belang. Hiermee wordt geprobeerd de eigenschappen die het dichtst bij het begin liggen volledig weer te geven. Als met de `Format-Table` opdracht niet alle eigenschappen kunnen worden weer gegeven, worden sommige kolommen uit de weer gave verwijderd. U kunt dit gedrag zien in het vorige voor beeld van de eigenschap **DependentServices** .

### <a name="wrapping-format-table-output-in-columns-wrap"></a>Terugloop indeling-tabel uitvoer in kolommen (terugloop)

U kunt met behulp van de para meter voor langdurige `Format-Table` gegevens afdwingen in **de weergave** kolom. Het gebruik van de para meter **wrap** kan niet wat u verwacht, omdat deze standaard instellingen gebruikt als u niet ook **AutoSize**opgeeft:

```powershell
Get-Service -Name win* | Format-Table -Property Name,Status,StartType,DisplayName,DependentServices -Wrap
```

```Output
Name                 Status StartType DisplayName                               DependentServi
                                                                                ces
----                 ------ --------- -----------                               --------------
WinDefend           Running Automatic Windows Defender Antivirus Service        {}
WinHttpAutoProxySvc Running    Manual WinHTTP Web Proxy Auto-Discovery Service  {NcaSvc,
                                                                                iphlpsvc}
Winmgmt             Running Automatic Windows Management Instrumentation        {vmms,
                                                                                TPHKLOAD,
                                                                                SUService,
                                                                                smstsmgr…}
WinRM               Running Automatic Windows Remote Management (WS-Management) {}
```

**Het gebruik** van de para meter voor hand matig vertraagt de verwerking zeer veel. Het gebruik van **AutoSize** voor het opmaken van een recursieve bestands vermelding van een grote mappen structuur kan echter lang duren en veel geheugen gebruiken voordat de eerste uitvoer items worden weer gegeven.

Als u zich geen zorgen maakt over systeem belasting, werkt **AutoSize** goed met de para meter voor de **Terugloop** .
De oorspronkelijke kolommen gebruiken nog steeds zoveel breedte als nodig is om items op één regel weer te geven, maar de laatste kolom wordt zo nodig verpakt.

> [!NOTE]
> Sommige kolommen worden mogelijk niet weer gegeven wanneer u eerst de breedste kolommen opgeeft. Geef eerst de kleinste gegevens elementen op voor de beste resultaten.

In het volgende voor beeld geven we eerst de breedste eigenschappen op.

```powershell
Get-Process -Name iexplore | Format-Table -Wrap -AutoSize -Property FileVersion,Path,Name,Id
```

Zelfs bij het inpakken wordt de kolom laatste **id** wegge laten:

```Output
FileVersion                          Path                                                  Nam
                                                                                           e
-----------                          ----                                                  ---
11.00.18362.1 (WinBuild.160101.0800) C:\Program Files (x86)\Internet Explorer\IEXPLORE.EXE iex
                                                                                           plo
                                                                                           re
11.00.18362.1 (WinBuild.160101.0800) C:\Program Files\Internet Explorer\iexplore.exe       iex
                                                                                           plo
                                                                                           re
```

### <a name="organizing-table-output--groupby"></a>Tabel uitvoer (-GroupBy) ordenen

Een andere handige para meter voor de besturings elementen voor tabellarische uitvoer is **GroupBy**. Het is mogelijk dat er meer gegevens in de tabel in de lijst worden vergeleken. De **GroupBy** -parameter groepen worden uitgevoerd op basis van een eigenschaps waarde. We kunnen bijvoorbeeld services groeperen op **starttype** voor een betere inspectie, waarbij de **starttype** -waarde wordt wegge laten uit de eigenschaps vermelding:

```powershell
Get-Service -Name win* | Sort-Object StartType | Format-Table -GroupBy StartType
```

```Output
   StartType: Automatic
Status   Name               DisplayName
------   ----               -----------
Running  WinDefend          Windows Defender Antivirus Service
Running  Winmgmt            Windows Management Instrumentation
Running  WinRM              Windows Remote Management (WS-Managem…

   StartType: Manual
Status   Name               DisplayName
------   ----               -----------
Running  WinHttpAutoProxyS… WinHTTP Web Proxy Auto-Discovery Serv…
```
