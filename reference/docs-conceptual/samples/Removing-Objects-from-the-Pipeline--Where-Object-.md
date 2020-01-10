---
ms.date: 12/23/2019
keywords: Power shell, cmdlet
title: Objecten verwijderen uit de pijp lijn waarbij het object
ms.openlocfilehash: 370e7745341b70c0794352a690d5750d21f53ac2
ms.sourcegitcommit: 058a6e86eac1b27ca57a11687019df98709ed709
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 01/08/2020
ms.locfileid: "75737182"
---
# <a name="removing-objects-from-the-pipeline-where-object"></a>Objecten uit de pijp lijn verwijderen (where-object)

In Power shell genereert u vaak meerdere objecten naar een pijp lijn dan u wilt. U kunt de eigenschappen van bepaalde objecten opgeven die moeten worden weer gegeven met behulp van de `Format-*`-cmdlets, maar dit biedt geen ondersteuning voor het probleem van het verwijderen van volledige objecten uit de weer gave. Misschien wilt u objecten filteren vóór het einde van een pijp lijn, zodat u alleen acties kunt uitvoeren op een subset van de eerste gegenereerde objecten.

Power shell bevat een `Where-Object`-cmdlet waarmee u elk object in de pijp lijn kunt testen en dit alleen door geven aan de pijp lijn als het voldoet aan een bepaalde test voorwaarde. Objecten die de test niet door lopen, worden uit de pijp lijn verwijderd. U geeft de test voorwaarde op als de waarde van de para meter **FilterScript** .

## <a name="performing-simple-tests-with-where-object"></a>Eenvoudige tests uitvoeren met where-object

De waarde van **FilterScript** is een *script blok* : een of meer Power shell-opdrachten omgeven door accolades (`{}`)-die als waar of ONWAAR worden geëvalueerd. Deze script blokken kunnen zeer eenvoudig zijn, maar het maken ervan vereist dat u weet wat een ander Power shell-concept, vergelijkings operators is. Een vergelijkings operator vergelijkt de items die aan elkaar worden weer gegeven. Vergelijkings operatoren beginnen met een koppel teken (`-`) en worden gevolgd door een naam. Eenvoudige vergelijkings operators werken aan bijna elk soort object. De geavanceerde vergelijkings operators kunnen alleen werken met tekst of matrices.

> [!NOTE]
> Wanneer u werkt met tekst, zijn de Power shell-vergelijkings operatoren standaard niet hoofdletter gevoelig.

Als gevolg van het parseren van overwegingen, zoals `<`,`>`en `=` worden niet gebruikt als vergelijkings operators. In plaats daarvan bestaan vergelijkings operatoren uit letters. De basis-vergelijkings operatoren worden weer gegeven in de volgende tabel.

| Vergelijkingsoperator |                  Betekenis                   |    Voor beeld (retourneert waar)    |
| ------------------- | ------------------------------------------ | ---------------------------- |
| -eq                 | is gelijk aan                                | 1-EQ 1                      |
| -ne                 | Is niet gelijk aan                            | 1-ne 2                      |
| -lt                 | Is kleiner dan                               | 1-lt 2                      |
| -Le                 | is kleiner dan of gelijk aan                   | 1-Le 2                      |
| -gt                 | Is groter dan                            | 2-gt 1                      |
| -ge                 | is groter dan of gelijk zijn aan                | 2-ge 1                      |
| -like               | Is vergelijkbaar (vergelijking van joker tekens voor tekst)     | "file. doc"-like "f *. do?"    |
| -notlike            | Is niet hetzelfde (vergelijking van joker tekens voor tekst) | "file. doc"-notlike "p*. doc" |
| -bevat           | Contains                                   | 1, 2, 3-bevat 1            |
| -notcontains        | Bevat niet                           | 1, 2, 3-notcontains 4         |

`Where-Object`-script blokken gebruiken de speciale variabele `$_` om te verwijzen naar het huidige object in de pijp lijn. Hier volgt een voor beeld van hoe het werkt. Als u een lijst met getallen hebt en alleen deze wilt retour neren die kleiner zijn dan 3, kunt u `Where-Object` gebruiken om de getallen te filteren door het volgende te typen:

```
1,2,3,4 | Where-Object {$_ -lt 3}
1
2
```

## <a name="filtering-based-on-object-properties"></a>Filteren op basis van object eigenschappen

Omdat `$_` naar het huidige pijplijn object verwijst, hebben we toegang tot de eigenschappen van de tests.

U kunt bijvoorbeeld de klasse **Win32_SystemDriver** in WMI bekijken. Er zijn mogelijk honderden systeem Stuur Programma's op een bepaald systeem, maar u bent mogelijk alleen geïnteresseerd in een bepaalde set van de systeem Stuur Programma's, zoals die op dit moment worden uitgevoerd. De relevante eigenschap is **status**voor de **Win32_SystemDriver** klasse. U kunt de systeem Stuur Programma's filteren en alleen de actieve items selecteren door het volgende te typen:

```powershell
Get-CimInstance -Class Win32_SystemDriver |
  Where-Object {$_.State -eq 'Running'}
```

Er wordt nog steeds een lange lijst gegenereerd. U kunt filteren op alleen de ingestelde Stuur Programma's selecteren om automatisch te starten door de **Start** modus-waarde te testen:

```powershell
Get-CimInstance -Class Win32_SystemDriver |
  Where-Object {$_.State -eq "Running"} |
    Where-Object {$_.StartMode -eq "Auto"}
```

```Output
DisplayName : RAS Asynchronous Media Driver
Name        : AsyncMac
State       : Running
Status      : OK
Started     : True

DisplayName : Audio Stub Driver
Name        : audstub
State       : Running
Status      : OK
Started     : True
...
```

Dit biedt ons veel informatie die we niet meer nodig hebben omdat we weten dat de Stuur Programma's worden uitgevoerd.
De enige informatie die we waarschijnlijk op dit moment nodig hebben, zijn de naam en de weergave naam. De volgende opdracht bevat alleen die twee eigenschappen, wat resulteert in veel eenvoudiger uitvoer:

```powershell
Get-CimInstance -Class Win32_SystemDriver |
  Where-Object {$_.State -eq "Running"} |
    Where-Object {$_.StartMode -eq "Manual"} |
      Format-Table -Property Name,DisplayName
```

```Output
Name              DisplayName
----              -----------
AsyncMac               RAS Asynchronous Media Driver
bindflt                Windows Bind Filter Driver
bowser                 Browser
CompositeBus           Composite Bus Enumerator Driver
condrv                 Console Driver
HdAudAddService        Microsoft 1.1 UAA Function Driver for High Definition Audio Service
HDAudBus               Microsoft UAA Bus Driver for High Definition Audio
HidUsb                 Microsoft HID Class Driver
HTTP                   HTTP Service
igfx                   igfx
IntcDAud               Intel(R) Display Audio
intelppm               Intel Processor Driver
...
```

De bovenstaande opdracht bevat twee `Where-Object` elementen, maar deze kunnen worden uitgedrukt in één `Where-Object` element met behulp van de logische operator `-and`, zoals:

```powershell
Get-CimInstance -Class Win32_SystemDriver |
  Where-Object {($_.State -eq 'Running') -and ($_.StartMode -eq 'Manual')} |
    Format-Table -Property Name,DisplayName
```

De standaard logische Opera tors worden weer gegeven in de volgende tabel.

| Logische operator |                 Betekenis                  |  Voor beeld (retourneert waar)  |
| ---------------- | ---------------------------------------- | ------------------------ |
| -en             | Logische en; waar als beide zijden waar zijn | (1-EQ 1)-en (2-EQ 2) |
| -of              | Logische of; waar als een van beide zijden waar is  | (1-EQ 1)-of (1-EQ 2)  |
| -niet             | Logische niet; keert waar en ONWAAR om     | -niet (1-EQ 2)           |
| \!               | Logische niet; keert waar en ONWAAR om     | \!(1-EQ 2)              |
