---
ms.date: 2017-06-05
keywords: PowerShell-cmdlet
title: Met behulp van de indeling opdrachten moeten worden gewijzigd uitvoer weergeven
ms.assetid: 63515a06-a6f7-4175-a45e-a0537f4f6d05
ms.openlocfilehash: 0163fcb21d586fc98902d9bdcfab6fe4eb97c225
ms.sourcegitcommit: 74255f0b5f386a072458af058a15240140acb294
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 08/03/2017
---
# <a name="using-format-commands-to-change-output-view"></a>Met behulp van de indeling opdrachten moeten worden gewijzigd uitvoer weergeven
Windows PowerShell is een set cmdlets waarmee u kunt bepalen welke eigenschappen voor bepaalde objecten worden weergegeven. De namen van alle cmdlets beginnen met de term **indeling**. Ze kunnen u selecteren van een of meer eigenschappen om weer te geven.

De **indeling** -cmdlets zijn **indeling hele**, **lijst indelen**, **Format-Table**, en **indeling-aangepaste**. Er wordt alleen beschreven de **indeling hele**, **lijst indelen**, en **Format-Table** cmdlets in deze handleiding.

Elke cmdlet indeling heeft standaardeigenschappen die worden gebruikt als u geen specifieke eigenschappen weer te geven. Elke cmdlet gebruikt ook de parameternaam dezelfde **eigenschap**, om op te geven welke eigenschappen u wilt weergeven. Omdat **indeling hele** ziet u slechts één eigenschap, de **eigenschap** parameter duurt slechts een enkele waarde, maar de Eigenschapsparameters van **lijst indelen** en **Format-Table** accepteert een lijst met namen van eigenschappen.

Als u de opdracht **Get-Process - naam powershell** met twee exemplaren van Windows PowerShell wordt uitgevoerd, beschikt u uitvoer die er als volgt uit:

```
Handles  NPM(K)    PM(K)      WS(K) VM(M)   CPU(s)     Id ProcessName
-------  ------    -----      ----- -----   ------     -- -----------
    995       9    30308      27996   152     2.73   2760 powershell
    331       9    23284      29084   143     1.06   3448 powershell
```

In de rest van deze sectie wordt besproken hoe u **indeling** -cmdlets voor het wijzigen van de manier waarop de uitvoer van deze opdracht wordt weergegeven.

### <a name="using-format-wide-for-single-item-output"></a>Gebruik van de hele indeling voor één Item uitvoer
De **indeling hele** cmdlet, wordt standaard alleen de standaardeigenschap van een object. De informatie die is gekoppeld aan elk object wordt in één kolom weergegeven:

```
PS> Get-Process -Name powershell | Format-Wide

powershell                              powershell
```

U kunt ook een niet-standaard-eigenschap opgeven:

```
PS> Get-Process -Name powershell | Format-Wide -Property Id

2760                                    3448
```

#### <a name="controlling-format-wide-display-with-column"></a>Indeling Wide weergeven met kolom beheren
Met de **indeling hele** cmdlet, kunt u slechts één eigenschap tegelijk weergeven. Hierdoor is het nuttig voor het weergeven van eenvoudige lijsten die slechts één element per regel. Als u een eenvoudige lijst, stel de waarde van de **kolom** parameter 1 door te typen:

```
Get-Command Format-Wide -Property Name -Column 1
```

### <a name="using-format-list-for-a-list-view"></a>Met behulp van de lijst van de indeling voor een lijst weergeven
De **lijst indelen** cmdlet geeft een object in de vorm van een lijst weer met elke eigenschap met het label en wordt weergegeven op een afzonderlijke regel:

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

U kunt zoveel eigenschappen als u wilt opgeven:

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

#### <a name="getting-detailed-information-by-using-format-list-with-wildcards"></a>Gedetailleerde informatie van de ophalen met behulp van de lijst indelen met jokertekens
De **lijst indelen** cmdlet kunt u een jokerteken gebruiken als de waarde van de **eigenschap** parameter. Hiermee kunt u gedetailleerde informatie weergeven. Objecten bevatten vaak meer gegevens dan u nodig hebt, dat is waarom Windows PowerShell biedt niet alle eigenschapswaarden standaard weergegeven. Als u alle eigenschappen van een object, gebruiken de **lijst indelen-eigenschap \&#42;** opdracht. Meer dan 60 regels van de uitvoer voor een enkel proces worden gegenereerd door de volgende opdracht:

```
Get-Process -Name powershell | Format-List -Property *
```

Hoewel de **lijst indelen** opdracht is handig voor het weergeven van details over als u een overzicht van de uitvoer die veel objecten bevat wilt, een eenvoudigere tabelweergave is het vaak nuttig.

### <a name="using-format-table-for-tabular-output"></a>Gebruik tabel opmaken voor uitvoer in tabelvorm
Als u de **Format-Table** cmdlet met de eigenschapnamen van geen opgegeven voor het formatteren van de uitvoer van de **Get-Process** opdracht, krijgt u exact dezelfde uitvoer als zonder uit te voeren zonder opmaak. De reden is dat processen worden gewoonlijk weergegeven in tabelvorm, omdat de meeste Windows PowerShell-objecten.

```
PS> Get-Process -Name powershell | Format-Table

Handles  NPM(K)    PM(K)      WS(K) VM(M)   CPU(s)     Id ProcessName
-------  ------    -----      ----- -----   ------     -- -----------
   1488       9    31568      29460   152     3.53   2760 powershell
    332       9    23140        632   141     1.06   3448 powershell
```

#### <a name="improving-format-table-output-autosize"></a>Verbetering van de uitvoer van de tabel opmaken (AutoSize)
Hoewel een tabellarische weergave nuttig is voor het weergeven van een groot aantal vergelijkbare informatie, kan het moeilijk te interpreteren als de weergave te klein voor de gegevens is zijn. Bijvoorbeeld als u probeert om weer te geven Procespad, -ID, naam en bedrijf, krijgt u ingekorte uitvoer van het Procespad van het en de kolom bedrijf:

```
PS> Get-Process -Name powershell | Format-Table -Property Path,Name,Id,Company

Path                Name                                 Id Company
----                ----                                 -- -------
C:\Program Files... powershell                         2836 Microsoft Corpor...
```

Als u opgeeft de **AutoSize** parameter tijdens het uitvoeren van de **Format-Table** opdracht, berekent Windows PowerShell kolombreedte op basis van de feitelijke gegevens die u wilt weergeven. Hierdoor kan de **pad** kolom kan worden gelezen, maar de kolom van het bedrijf blijft ingekorte:

```
PS> Get-Process -Name powershell | Format-Table -Property Path,Name,Id,Company -
AutoSize

Path                                                    Name         Id Company
----                                                    ----         -- -------
C:\Program Files\Windows PowerShell\v1.0\powershell.exe powershell 2836 Micr...
```

De **Format-Table** cmdlet mogelijk nog steeds gegevens afkappen, maar alleen daartoe zal aan het einde van het scherm. Eigenschappen dan laatste die wordt weergegeven, krijgen zoveel grootte als ze nodig hebben voor hun langste gegevenselement goed worden weergegeven. U kunt zien dat bedrijfsnaam weergegeven wordt, maar pad wordt afgekapt als u de locaties van wisselen **pad** en **bedrijf** in de **eigenschap** lijst met waarden:

```
PS> Get-Process -Name powershell | Format-Table -Property Company,Name,Id,Path -
AutoSize

Company               Name         Id Path
-------               ----         -- ----
Microsoft Corporation powershell 2836 C:\Program Files\Windows PowerShell\v1...
```

De **Format-Table** opdracht wordt ervan uitgegaan dat de nearer is een eigenschap aan het begin van de lijst met eigenschappen met hoe belangrijk het is. Daarom wordt geprobeerd om weer te geven van de eigenschappen dichtstbijzijnde het begin volledig. Als de **Format-Table** opdracht kan niet alle eigenschappen die worden weergegeven, wordt een aantal kolommen verwijderen uit de weergave en een waarschuwing. U kunt dit gedrag zien als u **naam** de laatste eigenschap in de lijst:

```
PS> Get-Process -Name powershell | Format-Table -Property Company,Path,Id,Name -
AutoSize

WARNING: column "Name" does not fit into the display and was removed.

Company               Path                                                    I
                                                                              d
-------               ----                                                    -
Microsoft Corporation C:\Program Files\Windows PowerShell\v1.0\powershell.exe 6
```

De kolom-ID is afgekapt zodat het past binnen de vermelding in de bovenstaande uitvoer en de kolomkoppen zijn gestapeld. Automatisch vergroten of verkleinen van de kolommen biedt niet altijd wat u wilt.

#### <a name="wrapping-format-table-output-in-columns-wrap"></a>Onmiddellijke Format-Table-uitvoer in kolommen (terugloop)
U kunt afdwingen langdurige **Format-Table** gegevens om in te verpakken in de kolom weergeven met behulp van de **teruglopen** parameter. Met behulp van de **teruglopen** parameter alleen wordt niet per se te doen wat u verwacht, omdat deze standaardinstellingen gebruikt als u geen ook opgeeft **AutoSize**:

```
PS> Get-Process -Name powershell | Format-Table -Wrap -Property Name,Id,Company,
Path

Name                                 Id Company             Path
----                                 -- -------             ----
powershell                         2836 Microsoft Corporati C:\Program Files\Wi
                                        on                  ndows PowerShell\v1
                                                            .0\powershell.exe
```

Een voordeel van het gebruik van de **teruglopen** parameter door zichzelf is dat deze niet wordt vertraagd veel verwerken. Als u een overzicht van het bestand recursieve van een grote directory-systeem uitvoert, kan erg lang duren en kunt u veel geheugen gebruiken voordat de eerste Uitvoeritems wordt weergegeven als u **AutoSize**.

Als u vervolgens niet betrokken zijn bij de systeembelasting **AutoSize** werkt goed samen met de **teruglopen** parameter. De eerste kolommen worden altijd toegewezen zoveel breedte als ze nodig hebben voor het weergeven van items op één regel, net zoals bij het opgeven van **AutoSize** zonder de **teruglopen** parameter. Het enige verschil is dat de laatste kolom wordt ingepakt indien nodig:

```
PS> Get-Process -Name powershell | Format-Table -Wrap -AutoSize -Property Name,I
d,Company,Path

Name         Id Company               Path
----         -- -------               ----
powershell 2836 Microsoft Corporation C:\Program Files\Windows PowerShell\v1.0\
                                      powershell.exe
```

Sommige kolommen mogelijk niet weergegeven als u eerst de breedste kolommen opgeven zodat u veiligste eerst de kleinste gegevenselementen opgeven. In het volgende voorbeeld wordt het zeer breed padelement eerst specificeren, en zelfs met tekstterugloop, we nog steeds het uiteindelijke verliezen **naam** kolom:

```
PS> Get-Process -Name powershell | Format-Table -Wrap -AutoSize -Property Path,I
d,Company,Name

WARNING: column "Name" does not fit into the display and was removed.

Path                                                      Id Company
----                                                      -- -------
C:\Program Files\Windows PowerShell\v1.0\powershell.exe 2836 Microsoft Corporat
                                                             ion
```

#### <a name="organizing-table-output--groupby"></a>Tabeluitvoer ordenen (-GroupBy)
Is een andere handige parameter voor uitvoer in tabelvorm besturingselement **GroupBy**. Meer in tabelvorm aanbiedingen in het bijzonder mogelijk moeilijk te vergelijken. De **GroupBy** parameter gegroepeerd op basis van een waarde van de eigenschap uitvoer. We kunnen bijvoorbeeld processen door bedrijf voor gemakkelijker inspectie als de waarde van het bedrijf van de eigenschap aanbieding weggelaten groeperen:

```
PS> Get-Process -Name powershell | Format-Table -Wrap -AutoSize -Property Name,I
d,Path -GroupBy Company

   Company: Microsoft Corporation

Name         Id Path
----         -- ----
powershell 1956 C:\Program Files\Windows PowerShell\v1.0\powershell.exe
powershell 2656 C:\Program Files\Windows PowerShell\v1.0\powershell.exe
```

