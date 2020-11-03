---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 12/21/2018
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/convertfrom-csv?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: ConvertFrom-Csv
ms.openlocfilehash: 483f3767af4df9e5e044ab3b46811f22b63a5723
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/07/2020
ms.locfileid: "93250481"
---
# ConvertFrom-Csv

## SAMENVATTING
Converteert object eigenschappen in CSV-indeling (door komma's gescheiden waarden) naar CSV-versies van de oorspronkelijke objecten.

## SYNTAXIS

### Scheidings teken (standaard)

```
ConvertFrom-Csv [-InputObject] <psobject[]> [[-Delimiter] <char>] [-Header <string[]>]
 [<CommonParameters>]
```

### UseCulture

```
ConvertFrom-Csv [-InputObject] <psobject[]> -UseCulture [-Header <string[]>] [<CommonParameters>]
```

## BESCHRIJVING

De `ConvertFrom-Csv` cmdlet maakt objecten van teken reeksen met variabele lengte van CSV die door de `ConvertTo-Csv` cmdlet worden gegenereerd.

U kunt de para meters van deze cmdlet gebruiken om de rij met kolom koppen op te geven, waarmee de eigenschapnamen van de resulterende objecten worden bepaald, het scheidings teken voor het item moet worden opgegeven, of deze cmdlet moet worden omgeleid om het lijst scheidings teken voor de huidige cultuur als scheidings teken te gebruiken.

De objecten die `ConvertFrom-Csv` worden gemaakt, zijn CSV-versies van de oorspronkelijke objecten. De eigenschaps waarden van de CSV-objecten zijn teken reeks versies van de eigenschaps waarden van de oorspronkelijke objecten. De CSV-versies van de objecten hebben geen enkele methode.

U kunt ook de `Export-Csv` `Import-Csv` cmdlets en gebruiken om objecten te converteren naar CSV-teken reeksen in een bestand (en terug). Deze cmdlets zijn hetzelfde als de `ConvertTo-Csv` -en `ConvertFrom-Csv` -cmdlets, behalve dat ze de CSV-teken reeksen in een bestand opslaan.

## VOORBEELDEN

### Voor beeld 1: processen op de lokale computer converteren naar CSV-indeling

In dit voor beeld ziet u hoe u de processen op de lokale computer converteert naar CSV-indeling en deze vervolgens herstelt in een object formulier.

```powershell
$P = Get-Process | ConvertTo-Csv
$P | ConvertFrom-Csv
```

De `Get-Process` cmdlet verstuurt de processen van de pijp lijn naar `ConvertTo-Csv` . `ConvertTo-Csv`Met de cmdlet worden de proces objecten geconverteerd naar een reeks CSV-teken reeksen. De `ConvertFrom-Csv` cmdlet converteert de CSV-teken reeksen naar CSV-versies van de oorspronkelijke proces objecten. De CSV-teken reeksen worden opgeslagen in de `$P` variabele.

### Voor beeld 2: een gegevens object converteren naar de CSV-indeling en vervolgens naar de CSV-object indeling

In dit voor beeld ziet u hoe u een gegevens object converteert naar CSV-indeling en vervolgens naar CSV-object indeling.

```powershell
$Date = Get-Date | ConvertTo-Csv -Delimiter ';'
ConvertFrom-Csv -InputObject $Date -Delimiter ';'
```

Met de eerste opdracht wordt `Get-Date` de huidige datum en tijd naar beneden verzonden in de pijp lijn `ConvertTo-Csv` . `ConvertTo-Csv`Met de cmdlet wordt het object Date geconverteerd naar een reeks CSV-teken reeksen.
De para meter **scheidings teken** wordt gebruikt om een punt komma als scheidings teken op te geven. De teken reeksen worden opgeslagen in de `$Date` variabele.

### Voor beeld 3: de para meter header gebruiken om de namen van eigenschappen te wijzigen

In dit voor beeld ziet u hoe u de para meter **header** van kunt gebruiken `ConvertFrom-Csv` om de namen van eigenschappen in het resulterende geïmporteerde object te wijzigen.

```powershell
$J = Start-Job -ScriptBlock { Get-Process } | ConvertTo-Csv  -NoTypeInformation
$Header = 'State', 'MoreData', 'StatusMessage', 'Location', 'Command', 'StateInfo', 'Finished', 'InstanceId', 'Id', 'Name', 'ChildJobs', 'BeginTime', 'EndTime', 'JobType', 'Output', 'Error', 'Progress', 'Verbose', 'Debug', 'Warning', 'Information'
# Delete the default header from $J
$J = $J[1..($J.count - 1)]
$J | ConvertFrom-Csv -Header $Header
```

```Output
State         : Running
MoreData      : True
StatusMessage :
Location      : localhost
Command       : Get-Process
StateInfo     : Running
Finished      : System.Threading.ManualResetEvent
InstanceId    : a259eb63-6824-4b97-a033-305108ae1c2e
Id            : 1
Name          : Job1
ChildJobs     : System.Collections.Generic.List`1[System.Management.Automation.Job]
BeginTime     : 12/20/2018 18:59:57
EndTime       :
JobType       : BackgroundJob
Output        : System.Management.Automation.PSDataCollection`1[System.Management.Automation.PSObject]
Error         : System.Management.Automation.PSDataCollection`1[System.Management.Automation.ErrorRecord]
Progress      : System.Management.Automation.PSDataCollection`1[System.Management.Automation.ProgressRecord]
Verbose       : System.Management.Automation.PSDataCollection`1[System.Management.Automation.VerboseRecord]
Debug         : System.Management.Automation.PSDataCollection`1[System.Management.Automation.DebugRecord]
Warning       : System.Management.Automation.PSDataCollection`1[System.Management.Automation.WarningRecord]
Information   : System.Management.Automation.PSDataCollection`1[System.Management.Automation.InformationRecord]
```

`Start-Job`Met de cmdlet wordt een achtergrond taak gestart die wordt uitgevoerd `Get-Process` . Er wordt een taak object naar de pijp lijn verzonden naar `ConvertTo-Csv` en geconverteerd naar een CSV-teken reeks. Met de para meter **NoTypeInformation** wordt de type-informatie header uit de CSV-uitvoer verwijderd en is deze optioneel in Power shell core. De `$Header` variabele bevat een aangepaste koptekst waarmee de volgende standaard waarden worden vervangen: **HasMoreData** , **JobStateInfo** , **PSBeginTime** , **PSEndTime** en **PSJobTypeName**. De `$J` variabele bevat de CSV-teken reeks en wordt gebruikt om de standaard header te verwijderen. De `ConvertFrom-Csv` cmdlet converteert de CSV-teken reeks naar een **PSCustomObject** en gebruikt de para meter **header** om de variabele toe te passen `$Header` .

### Voor beeld 4: CSV-teken reeksen van service objecten converteren

In dit voor beeld ziet u hoe u de `ConvertFrom-Csv` cmdlet gebruikt met de para meter **UseCulture** .

```powershell
(Get-Culture).TextInfo.ListSeparator
$Services = (Get-Service | ConvertTo-Csv)
ConvertFrom-Csv -InputObject $Services -UseCulture
```

De `Get-Culture` cmdlet gebruikt de geneste eigenschappen **Eigenschappen** en **ListSeparator** om het standaard lijst scheidings teken van de huidige cultuur op te halen. De `Get-Service` cmdlet verzendt service objecten naar beneden de pijp lijn naar `ConvertTo-Csv` . De `ConvertTo-Csv` service objecten worden geconverteerd naar een reeks CSV-teken reeksen. De CSV-teken reeksen worden opgeslagen in de `$Services` variabele. De `ConvertFrom-Csv` cmdlet gebruikt de para meter **input object** en converteert de CSV-teken reeksen uit de `$Services` variabele. De para meter **UseCulture** maakt gebruik van het standaard lijst scheidings teken van de huidige cultuur.

Wanneer de para meter **UseCulture** wordt gebruikt, moet u ervoor zorgen dat het standaard scheidings teken van de huidige cultuur overeenkomt met het scheidings teken dat wordt gebruikt in de CSV-teken reeksen. Anders `ConvertFrom-Csv` kan er geen objecten worden gegenereerd op basis van de CSV-teken reeksen.

## PARAMETERS

### -Scheidings teken

Hiermee geeft u het scheidings teken op waarmee de eigenschaps waarden in de CSV-teken reeksen worden gescheiden.
De standaard waarde is een komma (,).

Voer een teken in, bijvoorbeeld een dubbele punt (:).
Een punt komma (;)) opgeven plaats de invoeg toepassing tussen enkele aanhalings tekens.

Als u in het bestand een ander teken dan het teken voor de werkelijke waarde opgeeft, `ConvertFrom-Csv` kan de objecten niet maken op basis van de CSV-teken reeksen en worden de CSV-teken reeksen geretourneerd.

```yaml
Type: System.Char
Parameter Sets: Delimiter
Aliases:

Required: False
Position: 1
Default value: comma (,)
Accept pipeline input: False
Accept wildcard characters: False
```

### -Header

Hiermee wordt een rij met een alternatieve kolom koppen opgegeven voor de geïmporteerde teken reeks. De kolomkop bepaalt de eigenschapnamen van de objecten die zijn gemaakt door `ConvertFrom-Csv` .

Voer kolom koppen in als een door komma's gescheiden lijst. Plaats de teken reeks van de header niet tussen aanhalings tekens. Plaats elke kolomkop tussen enkele aanhalings tekens.

Als u minder kolom koppen opgeeft dan er gegevens kolommen zijn, worden de resterende gegevens kolommen verwijderd. Als u meer kolom koppen opgeeft dan er gegevens kolommen zijn, worden de aanvullende kolom koppen gemaakt met lege gegevens kolommen.

Wanneer u de para meter **header** gebruikt, laat u de teken reeks voor de kolomkop weg uit de CSV-teken reeksen. Anders wordt met deze cmdlet een extra object gemaakt op basis van de items in de rij met koppen.

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Input object

Hiermee geeft u de CSV-teken reeksen op die moeten worden geconverteerd naar objecten. Voer een variabele in die de CSV-teken reeksen bevat of typ een opdracht of expressie waarmee de CSV-teken reeksen worden opgehaald. U kunt ook de CSV-teken reeksen door sluizen naar `ConvertFrom-Csv` .

```yaml
Type: System.Management.Automation.PSObject[]
Parameter Sets: (All)
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### -UseCulture

Maakt gebruik van het lijst scheidings teken voor de huidige cultuur als item scheidings teken. Als u het lijst scheidings teken voor een cultuur wilt zoeken, gebruikt u de volgende opdracht: `(Get-Culture).TextInfo.ListSeparator` .

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: UseCulture
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### CommonParameters

Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable. Zie [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)voor meer informatie.

## INVOER

### System. String

U kunt CSV-teken reeksen door sluizen naar deze cmdlet.

## UITVOER

### System. Management. Automation. PSObject

Deze cmdlet retourneert de objecten die worden beschreven door de eigenschappen in de CSV-teken reeksen.

## OPMERKINGEN

Omdat de geïmporteerde objecten CSV-versies zijn van het object type, worden ze niet herkend en opgemaakt door de Power shell-type-indelings vermeldingen die de niet-CSV-versies van het object type Format teren.

In CSV-indeling wordt elk object vertegenwoordigd door een door komma's gescheiden lijst van de eigenschaps waarden van het object. De eigenschaps waarden worden geconverteerd naar teken reeksen (door de methode **toString ()** van het object te gebruiken), zodat ze worden vertegenwoordigd door de naam van de eigenschaps waarde. Met deze cmdlet worden niet de methoden van het object geëxporteerd.

## GERELATEERDE KOPPELINGEN

[ConvertTo-Csv](ConvertTo-Csv.md)

[Exporteren-CSV](Export-Csv.md)

[Import-Csv](Import-Csv.md)
