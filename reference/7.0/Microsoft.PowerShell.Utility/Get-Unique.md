---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 03/12/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/get-unique?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-Unique
ms.openlocfilehash: 15a3905359a14b26dc98ad7462cc40420e111981
ms.sourcegitcommit: de63e9481cf8024883060aae61fb02c59c2de662
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/03/2020
ms.locfileid: "93249447"
---
# Get-Unique

## SAMENVATTING
Retourneert unieke items uit een gesorteerde lijst.

## SYNTAXIS

### AsString (standaard)

```
Get-Unique [-InputObject <PSObject>] [-AsString] [<CommonParameters>]
```

### UniqueByType

```
Get-Unique [-InputObject <PSObject>] [-OnType] [<CommonParameters>]
```

## BESCHRIJVING

De `Get-Unique` cmdlet vergelijkt elk item in een gesorteerde lijst met het volgende item, elimineert dubbele waarden en retourneert slechts één exemplaar van elk item. De lijst moet worden gesorteerd om de cmdlet goed te laten werken.

`Get-Unique` is hoofdletter gevoelig. Als gevolg hiervan worden teken reeksen die alleen in Character-hoofdletter verschillen, als uniek beschouwd.

## VOORBEELDEN

### Voor beeld 1: unieke woorden in een tekst bestand ophalen

Met deze opdrachten wordt het aantal unieke woorden in een tekst bestand gevonden.

```powershell
$A = $( foreach ($line in Get-Content C:\Test1\File1.txt) {
    $line.tolower().split(" ")
  }) | Sort-Object | Get-Unique
$A.count
```

Met de eerste opdracht wordt de inhoud van het File.txt bestand opgehaald. Hiermee wordt elke tekst regel geconverteerd naar kleine letters en vervolgens elk woord gesplitst op een afzonderlijke regel aan de spatie (""). Vervolgens wordt de resulterende lijst alfabetisch gesorteerd (de standaard instelling) en wordt de `Get-Unique` cmdlet gebruikt voor het elimineren van dubbele woorden. De resultaten worden opgeslagen in de `$A` variabele.

De tweede opdracht maakt gebruik van de eigenschap **Count** van de verzameling teken reeksen in `$A` om te bepalen hoeveel items zich in bevinden `$A` .

### Voor beeld 2: unieke gehele getallen in een matrix ophalen

Met deze opdracht vindt u de unieke leden van de set met gehele getallen.

```powershell
1,1,1,1,12,23,4,5,4643,5,3,3,3,3,3,3,3 | Sort-Object | Get-Unique
```

```Output
1
3
4
5
12
23
4643
```

De eerste opdracht neemt een matrix van gehele getallen op op de opdracht regel, stuurt deze door naar de `Sort-Object` cmdlet die moet worden gesorteerd en sluizen deze naar `Get-Unique` , waardoor dubbele vermeldingen worden geëlimineerd.

### Voor beeld 3: unieke object typen in een directory ophalen

Met deze opdracht wordt de `Get-ChildItem` cmdlet gebruikt om de inhoud van de lokale map op te halen, inclusief bestanden en mappen.

```powershell
Get-ChildItem | Sort-Object {$_.GetType()} | Get-Unique -OnType
```

De pijplijn operator (|) verzendt de resultaten naar de `Sort-Object` cmdlet. `$_.GetType()`Met de instructie wordt de **gettype** -methode toegepast op elk bestand of elke map. Vervolgens worden `Sort-Object` de items gesorteerd op type. Een andere pijplijn operator stuurt de resultaten naar `Get-Unique` . De **OnType** para meter direct `Get-Unique` retourneert slechts één object van elk type.

### Voor beeld 4: unieke processen ophalen

Met deze opdracht worden de namen opgehaald van processen die op de computer worden uitgevoerd, waarbij duplicaten worden verwijderd.

```powershell
Get-Process | Sort-Object | Select-Object processname | Get-Unique -AsString
```

`Get-Process`Met de opdracht worden alle processen op de computer opgehaald. Met de pijplijn operator (|) wordt het resultaat door gegeven aan `Sort-Object` , dat standaard de processen alfabetisch op procesnaam sorteert. De resultaten worden door gegeven aan de `Select-Object` cmdlet, waarmee alleen de waarden van de eigenschap proces naam van elk object worden geselecteerd. De resultaten worden vervolgens gepiped om `Get-Unique` dubbele waarden te elimineren.

De para meter **AsString** geeft `Get-Unique` aan dat de **Procesnaam** waarden moeten worden behandeld als teken reeksen.
Zonder deze para meter worden `Get-Unique` de waarden van de **proces** naam als objecten behandeld en wordt slechts één exemplaar van het object geretourneerd, dat wil zeggen, de eerste proces naam in de lijst.

## PARAMETERS

### -AsString

Geeft aan dat deze cmdlet de gegevens als een teken reeks gebruikt. Als u deze para meter niet opgeeft, worden gegevens behandeld als een object, dus wanneer u een verzameling objecten van hetzelfde type verzendt naar `Get-Unique` , bijvoorbeeld een verzameling bestanden, wordt er slechts één (de eerste) geretourneerd. U kunt deze para meter gebruiken om de unieke waarden van object eigenschappen, zoals de bestands namen, te vinden.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: AsString
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Input object

Hiermee geeft u de invoer voor `Get-Unique` . Voer een variabele in die de objecten bevat of typ een opdracht of expressie waarmee de objecten worden opgehaald.

Met deze cmdlet wordt de invoer behandeld die is verzonden met behulp van **input object** als een-verzameling. Er worden geen afzonderlijke items in de verzameling opgesomd. Omdat de verzameling één item is, wordt de invoer die is verzonden met behulp van **input object** altijd ongewijzigd geretourneerd.

```yaml
Type: System.Management.Automation.PSObject
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### -OnType

Geeft aan dat deze cmdlet slechts één object van elk type retourneert.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: UniqueByType
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### CommonParameters

Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable. Zie [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)voor meer informatie.

## INVOER

### System. Management. Automation. PSObject

U kunt elk type object door sluizen naar `Get-Unique` .

## UITVOER

### System. Management. Automation. PSObject

Het type van het object dat wordt `Get-Unique` geretourneerd, wordt bepaald door de invoer.

## OPMERKINGEN

U kunt ook verwijzen naar `Get-Unique` de ingebouwde alias `gu` . Zie [about_Aliases](../Microsoft.PowerShell.Core/About/about_Aliases.md)voor meer informatie.

Als u een lijst wilt sorteren, gebruikt u sorteer-object. U kunt ook de **unieke** para meter van gebruiken `Sort-Object` om de unieke items in een lijst te vinden.

## GERELATEERDE KOPPELINGEN

[Select-Object](Select-Object.md)

[Sorteer object](Sort-Object.md)
