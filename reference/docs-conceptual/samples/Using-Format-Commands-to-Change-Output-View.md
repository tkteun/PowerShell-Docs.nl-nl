---
ms.date: 06/05/2017
keywords: PowerShell-cmdlet
title: Format-opdrachten gebruiken om de uitvoerweergave te wijzigen
ms.assetid: 63515a06-a6f7-4175-a45e-a0537f4f6d05
ms.openlocfilehash: fba37b1d0479bf605d8f2171da27cd1bceb9976e
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62058264"
---
# <a name="using-format-commands-to-change-output-view"></a>Format-opdrachten gebruiken om de uitvoerweergave te wijzigen

Windows PowerShell is een set van cmdlets waarmee u kunt om te bepalen welke eigenschappen voor bepaalde objecten worden weergegeven. De namen van alle cmdlets beginnen met de term **indeling**. U kunt selecteren van een of meer eigenschappen om weer te geven.

De **indeling** -cmdlets zijn **indeling hele**, **lijst indeling**, **Format-Table**, en **indeling-aangepaste**. We alleen worden beschreven de **indeling hele**, **lijst indeling**, en **Format-Table** cmdlets in deze handleiding.

Elke cmdlet indeling heeft standaardeigenschappen die worden gebruikt als u geen specifieke eigenschappen weer te geven. Elke cmdlet maakt ook gebruik van dezelfde parameternamen, **eigenschap**om op te geven welke eigenschappen u wilt weergeven. Omdat **indeling hele** ziet u slechts één eigenschap, de **eigenschap** parameter duurt slechts één waarde, maar de Eigenschapsparameters van **lijst indeling** en **Format-Table** accepteert een lijst met namen van eigenschappen.

Als u de opdracht **Get-Process - naam powershell** met twee exemplaren van Windows PowerShell wordt uitgevoerd, ontvangt u uitvoer die er als uitzien volgt:

```output
Handles  NPM(K)    PM(K)      WS(K) VM(M)   CPU(s)     Id ProcessName
-------  ------    -----      ----- -----   ------     -- -----------
    995       9    30308      27996   152     2.73   2760 powershell
    331       9    23284      29084   143     1.06   3448 powershell
```

In de rest van deze sectie wordt toegelicht hoe u **indeling** cmdlets voor het wijzigen van de manier waarop de uitvoer van deze opdracht wordt weergegeven.

## <a name="using-format-wide-for-single-item-output"></a>Met behulp van de indeling hele voor één Item uitvoer

De `Format-Wide` cmdlet, wordt standaard alleen de standaardeigenschap van een object.
De informatie die is gekoppeld aan elk object wordt in één kolom weergegeven:

```powershell
Get-Command -Verb Format | Format-Wide
```

```output
Format-Custom                          Format-Hex
Format-List                            Format-Table
Format-Wide
```

U kunt ook een niet-standaard-eigenschap opgeven:

```powershell
Get-Command -Verb Format | Format-Wide -Property Noun
```

```output
Custom                                 Hex
List                                   Table
Wide
```

### <a name="controlling-format-wide-display-with-column"></a>Indeling hele weergeven met kolom beheren

Met de `Format-Wide` cmdlet, kunt u slechts één eigenschap tegelijk weergeven.
Dit maakt het handig voor het weergeven van eenvoudige lijsten die slechts één element per regel.
Als u een eenvoudige lijst, stel de waarde van de **kolom** parameter 1 door te typen:

```powershell
Get-Command -Verb Format | Format-Wide -Property Noun -Column 1
```

```output
Custom
Hex
List
Table
Wide
```

## <a name="using-format-list-for-a-list-view"></a>Met behulp van de lijst van de indeling voor een lijst weergeven

De **lijst indeling** cmdlet geeft een object in de vorm van een lijst weer met elke eigenschap met het label en wordt weergegeven op een afzonderlijke regel:

```
PS> Get-Process -Name powershell | Format-List

Id      : 2760
Handles : 1242
CPU     : 3.03125
Name    : powershell

Id      : 3448
Handles : 328
CPU     : 1.0625
Name    : powershell
```

U kunt zo veel eigenschappen als u wilt opgeven:

```
PS> Get-Process -Name powershell | Format-List -Property ProcessName,FileVersion
,StartTime,Id

ProcessName : powershell
FileVersion : 1.0.9567.1
StartTime   : 2006-05-24 13:42:00
Id          : 2760

ProcessName : powershell
FileVersion : 1.0.9567.1
StartTime   : 2006-05-24 13:54:28
Id          : 3448
```

### <a name="getting-detailed-information-by-using-format-list-with-wildcards"></a>Om gedetailleerde informatie met behulp van lijst indelen met jokertekens

De **lijst indeling** cmdlet kunt u een jokerteken gebruiken als de waarde van de **eigenschap** parameter. Hiermee kunt u gedetailleerde informatie weergegeven. Objecten bevatten vaak meer gegevens dan u nodig hebt, daarom zijn Windows PowerShell wordt alle eigenschapswaarden niet standaard weergegeven. Als u alle eigenschappen van een object, gebruiken de **Format-List-eigenschap \&#42;** opdracht. Meer dan 60 regels van de uitvoer voor een enkel proces worden gegenereerd door de volgende opdracht uit:

```powershell
Get-Process -Name powershell | Format-List -Property *
```

Hoewel de **lijst indeling** opdracht is handig voor het weergeven van details, als u een overzicht van de uitvoer die veel objecten bevat, een eenvoudigere tabellarische weergave is het vaak nuttig.

## <a name="using-format-table-for-tabular-output"></a>Met behulp van de tabel opmaken voor uitvoer in tabelvorm

Als u de **Format-Table** cmdlet met geen namen van eigenschappen die zijn opgegeven om de uitvoer van de **Get-Process** opdracht, krijgt u exact dezelfde uitvoer zoals u dat wel doet zonder uit te voeren zonder opmaak. De reden is dat processen meestal worden weergegeven in tabelvorm, omdat de meeste Windows PowerShell-objecten zijn.

```
PS> Get-Process -Name powershell | Format-Table

Handles  NPM(K)    PM(K)      WS(K) VM(M)   CPU(s)     Id ProcessName
-------  ------    -----      ----- -----   ------     -- -----------
   1488       9    31568      29460   152     3.53   2760 powershell
    332       9    23140        632   141     1.06   3448 powershell
```

### <a name="improving-format-table-output-autosize"></a>Verbetering van Format-Table-uitvoer (AutoSize)

Hoewel een tabellarische weergave handig is voor het weergeven van een groot aantal vergelijkbare informatie, kan het lastig zijn om te interpreteren als de weergave te klein voor de gegevens is. Bijvoorbeeld, als u probeert om Procespad, -ID, naam en bedrijf weer te geven, krijgt u afgekapte uitvoer voor de Procespad en de kolom van het bedrijf:

```
PS> Get-Process -Name powershell | Format-Table -Property Path,Name,Id,Company

Path                Name                                 Id Company
----                ----                                 -- -------
C:\Program Files... powershell                         2836 Microsoft Corpor...
```

Als u opgeeft de **AutoSize** parameter tijdens het uitvoeren van de **Format-Table** opdracht, berekent Windows PowerShell kolombreedten op basis van de werkelijke gegevens die u wilt weergeven. Dit maakt het **pad** kolom kan worden gelezen, maar de kolom bedrijf blijft afgekapt:

```
PS> Get-Process -Name powershell | Format-Table -Property Path,Name,Id,Company -
AutoSize

Path                                                    Name         Id Company
----                                                    ----         -- -------
C:\Program Files\Windows PowerShell\v1.0\powershell.exe powershell 2836 Micr...
```

De **Format-Table** cmdlet mogelijk nog steeds gegevens worden afgekapt, maar dit zal alleen dit doen aan het einde van het scherm. Eigenschappen dan de laatste weergegeven, krijgen zoveel grootte als ze nodig hebben voor hun langste gegevenselement om correct weer te geven. U kunt zien dat bedrijfsnaam weergegeven wordt, maar pad wordt afgekapt als u de locaties van wisselen **pad** en **bedrijf** in de **eigenschap** lijst met waarden:

```
PS> Get-Process -Name powershell | Format-Table -Property Company,Name,Id,Path -
AutoSize

Company               Name         Id Path
-------               ----         -- ----
Microsoft Corporation powershell 2836 C:\Program Files\Windows PowerShell\v1...
```

De **Format-Table** opdracht wordt ervan uitgegaan dat de nearer is een eigenschap aan het begin van de lijst met eigenschappen, met hoe belangrijk het is. Zo wordt geprobeerd om weer te geven van de eigenschappen dichtst bij het begin volledig. Als de **Format-Table** opdracht kan niet alle eigenschappen weergeven, het aantal kolommen uit de weergave verwijderen en een waarschuwing wordt weergegeven. U kunt dit gedrag zien als u **naam** de laatste eigenschap in de lijst:

```
PS> Get-Process -Name powershell | Format-Table -Property Company,Path,Id,Name -
AutoSize

WARNING: column "Name" does not fit into the display and was removed.

Company               Path                                                    I
                                                                              d
-------               ----                                                    -
Microsoft Corporation C:\Program Files\Windows PowerShell\v1.0\powershell.exe 6
```

De ID-kolom is afgebroken zodat het past binnen de vermelding in de bovenstaande uitvoer en de kolomkoppen zijn gestapeld van. Automatisch vergroten of verkleinen van de kolommen doet niet altijd wat u wilt.

### <a name="wrapping-format-table-output-in-columns-wrap"></a>Tekstterugloop Format-Table uitvoer in de kolommen (terugloop)

U kunt afdwingen dat lange **Format-Table** gegevens om in te verpakken in de kolom weergeven met behulp van de **verpakken** parameter. Met behulp van de **verpakken** parameter alleen niet per se doet wat u verwacht, omdat deze standaardinstellingen gebruikt als u niet ook opgeeft **AutoSize**:

```
PS> Get-Process -Name powershell | Format-Table -Wrap -Property Name,Id,Company,
Path

Name                                 Id Company             Path
----                                 -- -------             ----
powershell                         2836 Microsoft Corporati C:\Program Files\Wi
                                        on                  ndows PowerShell\v1
                                                            .0\powershell.exe
```

Een voordeel van het gebruik van de **verpakken** parameter op zichzelf is dat deze niet wordt vertraagd verwerking van zeer veel. Als u een overzicht van het bestand recursieve van een grote directory-systeem uitvoert, kan lange tijd in beslag nemen en kunt u een grote hoeveelheid geheugen gebruiken voordat de eerste Uitvoeritems wordt weergegeven als u **AutoSize**.

Als u vervolgens niet betrokken zijn bij het laden van het systeem, **AutoSize** werkt goed samen met de **verpakken** parameter. De oorspronkelijke kolommen worden altijd zoveel breedte die ze nodig hebben om weer te geven items op één regel, net zoals wanneer u opgeeft toegewezen **AutoSize** zonder de **verpakken** parameter. Het enige verschil is dat de laatste kolom zal worden verpakt, indien nodig:

```
PS> Get-Process -Name powershell | Format-Table -Wrap -AutoSize -Property Name,I
d,Company,Path

Name         Id Company               Path
----         -- -------               ----
powershell 2836 Microsoft Corporation C:\Program Files\Windows PowerShell\v1.0\
                                      powershell.exe
```

Sommige kolommen mogelijk niet weergegeven als u eerst de breedste kolommen opgeeft dus is het verstandig om op te geven van de kleinste gegevenselementen eerst. In het volgende voorbeeld geven we de zeer grote padelement eerst en zelfs met onmiddellijke, verliezen we nog steeds de laatste **naam** kolom:

```
PS> Get-Process -Name powershell | Format-Table -Wrap -AutoSize -Property Path,I
d,Company,Name

WARNING: column "Name" does not fit into the display and was removed.

Path                                                      Id Company
----                                                      -- -------
C:\Program Files\Windows PowerShell\v1.0\powershell.exe 2836 Microsoft Corporat
                                                             ion
```

### <a name="organizing-table-output--groupby"></a>Tabeluitvoer ordenen (-GroupBy)

Is een andere handige parameter voor uitvoer in tabelvorm besturingselement **GroupBy**. Meer in tabelvorm vermeldingen in het bijzonder mogelijk moeilijk om te vergelijken. De **GroupBy** parameter gegroepeerd op basis van een eigenschapswaarde uitvoer. We kunnen bijvoorbeeld processen door bedrijf voor eenvoudiger inspectie, als de waarde van het bedrijf in de lijst in de eigenschap groeperen:

```
PS> Get-Process -Name powershell | Format-Table -Wrap -AutoSize -Property Name,I
d,Path -GroupBy Company

   Company: Microsoft Corporation

Name         Id Path
----         -- ----
powershell 1956 C:\Program Files\Windows PowerShell\v1.0\powershell.exe
powershell 2656 C:\Program Files\Windows PowerShell\v1.0\powershell.exe
```