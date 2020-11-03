---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/convert-string?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Convert-String
ms.openlocfilehash: 29ec9e21277bae02ab94ce5e862787c86a87b439
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/07/2020
ms.locfileid: "93250480"
---
# Convert-String

## SAMENVATTING
Hiermee wordt een teken reeks opgemaakt die overeenkomt met voor beelden.

## SYNTAXIS

```
Convert-String [-Example <System.Collections.Generic.List`1[System.Management.Automation.PSObject]>]
 -InputObject <String> [<CommonParameters>]
```

## BESCHRIJVING

Met de cmdlet **Convert-string** wordt een teken reeks opgemaakt die overeenkomt met de indeling van voor beelden.

## VOORBEELDEN

### Voor beeld 1: indeling van een teken reeks converteren

```powershell
"Mu Han", "Jim Hance", "David Ahs", "Kim Akers" | Convert-String -Example "Ed Wilson=Wilson, E."
```

```output
Han, M.
Hance, J.
Ahs, D.
Akers, K.
```

Met de eerste opdracht maakt u een matrix die de voor-en achternaam bevat.

Met de tweede opdracht worden de namen op basis van het voor beeld opgemaakt.
De achternaam wordt eerst in de uitvoer geplaatst, gevolgd door een eerste.

### Voor beeld 2: de indeling van een teken reeks vereenvoudigen

```powershell
$composers = @("Johann Sebastian Bach", "Wolfgang Amadeus Mozart", "Frederic Francois Chopin", "Johannes Brahms")
$composers | Convert-String -Example "first middle last=last, first"
```

```output
Bach, Johann
Mozart, Wolfgang
Chopin, Frederic
Brahms, Johannes
```

Met de eerste opdracht maakt u een matrix die de eerste, middelste en achternaam bevat.
Houd er rekening mee dat de laatste vermelding geen middelste naam heeft.

Met de tweede opdracht worden de namen op basis van het voor beeld opgemaakt.
De laatste naam wordt eerst in de uitvoer geplaatst, gevolgd door de voor naam.
Alle middelste namen worden verwijderd. invoer zonder middelste naam wordt correct afgehandeld.

### Voor beeld 3: uitvoer beheer als teken reeksen niet overeenkomen met voor beeld

```powershell
$composers = @("Johann Sebastian Bach", "Wolfgang Amadeus Mozart", "Frederic Francois Chopin", "Johannes Brahms")
$composers | Convert-String -Example "first middle last=middle, first"
```

```output
Sebastian, Johann
Amadeus, Wolfgang
Francois, Frederic
```

Met de eerste opdracht maakt u een matrix die de eerste, middelste en achternaam bevat.
Houd er rekening mee dat de laatste vermelding geen middelste naam heeft.

Met de tweede opdracht worden de namen op basis van het voor beeld opgemaakt.
De **tweede naam** wordt eerst in de uitvoer geplaatst, gevolgd door de voor naam.
De laatste vermelding in **$Composers** wordt overgeslagen, omdat deze niet overeenkomt met het voorbeeld patroon: er is geen middelste naam.

### Voor beeld 4: waarschuwing met mooie Spaces

```powershell
$composers = @("Antonio Vivaldi", "Richard Wagner ", "Franz Schubert", "Johannes Brahms ")
$composers | Convert-String -Example "Patti Fuller = Fuller, P."
```

```output
 Wagner, R.
 Brahms, J.
```

Met de eerste opdracht maakt u een matrix met de voor-en achternaam.
Houd er rekening mee dat tweede en vierde items een extra spatie hebben na de achternaam.

Met de tweede opdracht worden alle teken reeksen die overeenkomen met het voorbeeld patroon geconverteerd: _woord, spatie, woord en laatste Volg spatie_ , alle voor het gelijkteken.
Let ook op de voorloop ruimte in de uitvoer.

### Voor beeld 5: proces gegevens opmaken met meerdere patronen

```powershell
$ExamplePatterns = @(
    @{before='"Hello","World"'; after='World: Hello'},
    @{before='"Hello","1"'; after='1: Hello'},
    @{before='"Hello-World","22"'; after='22: Hello-World'},
    @{before='"hello world","333"'; after='333: hello world'}
)
$Processes = Get-Process   | Select-Object -Property ProcessName, Id | ConvertTo-Csv -NoTypeInformation
$Processes | Convert-String -Example $ExamplePatterns
```

```output
Id: ProcessName
4368: AGSService
8896: Amazon Music Helper
4420: AppleMobileDeviceService
...
11140: git-bash
0: Idle
...
56: Secure System
...
13028: WmiPrvSE
2724: WUDFHost
2980: WUDFHost
3348: WUDFHost
```

**$ExamplePatterns** definieert verschillende verwachte patronen in de gegevens, via voor beelden.

Het eerste patroon, `@{before='"Hello","World"'; after='World: Hello'}` , lezen als volgt: er worden _teken reeksen verwacht waarbij een woord tussen dubbele aanhalings tekens, gevolgd door een komma_ 
 _en vervolgens de tweede en laatste woord tussen aanhalings tekens_ is geplaatst. 
 _zonder spaties in de teken reeks. In de uitvoer: plaats het tweede woord eerst,_ 
 _zonder aanhalings tekens, vervolgens één spatie en vervolgens het eerste woord, zonder aanhalings tekens._

Het tweede patroon, `@{before='"Hello","1"'; after='1: Hello'}` , lezen als volgt: _er worden teken reeksen verwacht waarbij een woord tussen dubbele aanhalings tekens, gevolgd door een komma_ 
 _en een getal tussen aanhalings tekens_ is geplaatst. 
 _zonder spaties in de teken reeks. In de uitvoer: plaats het getal eerst,_ 
 _zonder aanhalings tekens, één spatie en vervolgens het woord, zonder aanhalings tekens._

Het derde patroon, `@{before='"Hello-World","22"'; after='22: Hello-World'}` , lezen als volgt: _er worden teken reeksen verwacht waarbij twee woorden met een afbreek streepje tussen_ 
 _dubbele aanhalings tekens, gevolgd door een komma en een getal tussen aanhalings tekens staan._ 
 _zonder spaties tussen de komma en de derde dubbele aanhalings tekens._ 
 _In de uitvoer: plaats het getal eerst, zonder aanhalings tekens, vervolgens één spatie,_ 
 _en vervolgens de woord afbreek streepjes, zonder aanhalings tekens._

Het vierde en laatste patroon, `@{before='"hello world","333"'; after='333: hello world'}` worden als volgt gelezen: er _worden teken reeksen verwacht waarbij twee woorden met een spatie tussen_ 
 _dubbele aanhalings tekens, gevolgd door een komma en een getal tussen aanhalings tekens staan._ 
 _zonder spaties tussen de komma en de derde dubbele aanhalings tekens._ 
 _In de uitvoer: plaats het getal eerst, zonder aanhalings tekens, vervolgens één spatie,_ 
 _en vervolgens de woorden met de spatie tussen en zonder aanhalings tekens._

Met de eerste opdracht worden alle processen opgehaald met behulp van de cmdlet Get-Process.
De opdracht geeft deze door aan de cmdlet Select-Object, waarmee de proces naam en proces-ID worden geselecteerd. Aan het einde van de pijp lijn converteert de opdracht de uitvoer naar door komma's gescheiden waarden, zonder type gegevens, met behulp van de ConvertTo-Csv-cmdlet.
Met de opdracht worden de resultaten opgeslagen in de variabele **$processes** .
**$Processes** bevat nu proces namen en PID.

Met de tweede opdracht wordt een voorbeeld variabele opgegeven waarmee de volg orde van de invoer items wordt gewijzigd.
De opdracht keert elke teken reeks om in **$processes**.

>**Opmerking** Het vierde patroon geeft impliciet aan dat twee of meer woorden die worden gescheiden door spaties, overeenkomen.
>
>Zonder het vierde patroon komt alleen het eerste woord van de teken reeks tussen dubbele aanhalings tekens overeen.

## PARAMETERS

### -Voor beeld

Hiermee geeft u een lijst met voor beelden van de doel indeling op.
Geef paren op, gescheiden door het gelijkteken (=), met het bron patroon aan de linkerkant en het doel patroon aan de rechter kant, zoals in de volgende voor beelden:

* `-Example "Hello World=World, Hello"`
* `-Example "Hello World=World: Hello",'"Hello","1"=1: Hello'`

>**Opmerking** In het tweede voor beeld wordt een lijst met patronen gebruikt

U kunt ook een lijst met hash-tabellen opgeven die **vóór** en **na** de eigenschappen bevatten.

* `-Example @{before='"Hello","World"'; after='World: Hello'}, @{before='"Hello","1"'; after='1: Hello'}`

>**Waarschuwing** Vermijd het gebruik van spaties rond het gelijkteken, aangezien deze worden beschouwd als onderdeel van het patroon.

```yaml
Type: System.Collections.Generic.List`1[System.Management.Automation.PSObject]
Parameter Sets: (All)
Aliases: E

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Input object

Geeft een teken reeks op die moet worden opgemaakt.

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### CommonParameters

Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable. Zie [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)voor meer informatie.

## INVOER

### Tekenreeks

U kunt teken reeksen naar deze cmdlet pipeen.

## UITVOER

### Tekenreeks

Met deze cmdlet wordt een teken reeks geretourneerd.

## OPMERKINGEN

## GERELATEERDE KOPPELINGEN

[ConvertFrom-teken reeks](ConvertFrom-String.md)

[ConvertTo-Csv](ConvertTo-Csv.md)

[Get-Process](../Microsoft.PowerShell.Management/Get-Process.md)

[Out-teken reeks](Out-String.md)

[Select-Object](Select-Object.md)
