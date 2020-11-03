---
external help file: System.Management.Automation.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 05/13/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/add-history?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Add-History
ms.openlocfilehash: bbc5b6590dc97413350c19c91dbca0b4d08e9bce
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/07/2020
ms.locfileid: "93249868"
---
# Add-History

## SAMENVATTING
Hiermee worden items toegevoegd aan de sessie geschiedenis.

## SYNTAXIS

```
Add-History [[-InputObject] <PSObject[]>] [-Passthru] [<CommonParameters>]
```

## BESCHRIJVING

De `Add-History` cmdlet voegt vermeldingen toe aan het einde van de sessie geschiedenis, dat wil zeggen, de lijst met opdrachten die tijdens de huidige sessie zijn ingevoerd.

De sessie geschiedenis is een lijst met opdrachten die tijdens de sessie zijn ingevoerd. De sessie geschiedenis vertegenwoordigt de volg orde van de uitvoering, de status en de begin-en eind tijd van de opdracht. Bij het invoeren van elke opdracht voegt Power shell deze toe aan de geschiedenis zodat u deze opnieuw kunt gebruiken. Zie [about_History](About/about_History.md)voor meer informatie over de sessie geschiedenis.

De sessie geschiedenis wordt afzonderlijk beheerd vanaf de geschiedenis die wordt onderhouden door de **PSReadLine** -module.
Beide geschiedenissen zijn beschikbaar in sessies waarin **PSReadLine** wordt geladen. Deze cmdlet werkt alleen met de sessie geschiedenis. Zie [about_PSReadLine](../PSReadLine/About/about_PSReadLine.md)voor meer informatie.

U kunt de `Get-History` cmdlet gebruiken om de opdrachten op te halen en door te geven aan `Add-History` , of u kunt de opdrachten exporteren naar een CSV-of XML-bestand, de opdrachten vervolgens importeren en het geïmporteerde bestand door geven aan `Add-History` . U kunt deze cmdlet gebruiken om specifieke opdrachten toe te voegen aan de geschiedenis of om één geschiedenis bestand te maken dat opdrachten uit meer dan één sessie bevat.

## VOORBEELDEN

### Voor beeld 1: opdrachten toevoegen aan de geschiedenis van een andere sessie

In dit voor beeld worden de opdrachten die in één Power shell-sessie zijn getypt, toegevoegd aan de geschiedenis van een andere Power shell-sessie.

```powershell
Get-History | Export-Csv c:\testing\history.csv -IncludeTypeInformation
Import-Csv c:\testing\history.csv | Add-History
```

De eerste opdracht haalt objecten op die de opdrachten in de geschiedenis vertegenwoordigen en exporteert deze naar het `History.csv` bestand.

De tweede opdracht wordt op de opdracht regel van een andere sessie getypt. De cmdlet wordt gebruikt `Import-Csv` om de objecten in het bestand te importeren `History.csv` . De pijplijn operator ( `|` ) geeft de objecten door aan de `Add-History` cmdlet, waarmee de objecten die de opdrachten in het bestand vertegenwoordigen, `History.csv` worden toegevoegd aan de huidige sessie geschiedenis.

### Voor beeld 2: opdrachten importeren en uitvoeren

In dit voor beeld worden opdrachten uit het `History.xml` bestand geïmporteerd, worden deze toegevoegd aan de huidige sessie geschiedenis en worden de opdrachten in de gecombineerde geschiedenis uitgevoerd.

```powershell
Import-Clixml c:\temp\history.xml | Add-History -PassThru | ForEach-Object -Process {Invoke-History}
```

Met de eerste opdracht wordt de `Import-Clixml` cmdlet gebruikt voor het importeren van een opdracht geschiedenis die naar het bestand is geëxporteerd `History.xml` . De pijplijn operator geeft de opdrachten door aan de `Add-History` cmdlet, waarmee de opdrachten worden toegevoegd aan de huidige sessie geschiedenis. De **PassThru** para meter geeft de objecten weer die de toegevoegde opdrachten van de pijp lijn vertegenwoordigen.

De opdracht gebruikt vervolgens de `ForEach-Object` cmdlet om de `Invoke-History` opdracht toe te passen op elk van de opdrachten in de gecombineerde geschiedenis. De `Invoke-History` opdracht wordt opgemaakt als een script blok tussen accolades ( `{}` ), zoals vereist door de **proces** parameter van de `ForEach-Object` cmdlet.

### Voor beeld 3: opdrachten in de geschiedenis toevoegen aan het einde van de geschiedenis

In dit voor beeld worden de eerste vijf opdrachten in de geschiedenis toegevoegd aan het einde van de geschiedenis lijst.

```powershell
Get-History -Id 5 -Count 5 | Add-History
```

De `Get-History` cmdlet haalt de vijf opdrachten op die eindigen op de opdracht 5. De pipeline-operator geeft deze door aan de `Add-History` cmdlet, waarmee deze worden toegevoegd aan de huidige geschiedenis. De `Add-History` opdracht bevat geen para meters, maar Power shell koppelt de objecten die worden door gegeven via de pijp lijn met de para meter **input object** van `Add-History` .

### Voor beeld 4: opdrachten in een CSV-bestand toevoegen aan de huidige geschiedenis

In dit voor beeld worden de opdrachten in het `History.csv` bestand toegevoegd aan de geschiedenis van de huidige sessie.

```powershell
$a = Import-Csv c:\testing\history.csv
Add-History -InputObject $a -PassThru
```

De `Import-Csv` cmdlet importeert de opdrachten in het `History.csv` bestand en slaat de inhoud op in de variabele `$a` .

De tweede opdracht gebruikt de `Add-History` cmdlet om de opdrachten toe te voegen `History.csv` aan de huidige sessie geschiedenis. De para meter **input object** wordt gebruikt om de `$a` variabele en de para meter **PassThru** op te geven om een object te genereren dat wordt weer gegeven op de opdracht regel. Zonder de para meter **PassThru** wordt door de `Add-History` cmdlet geen uitvoer gegenereerd.

### Voor beeld 5: opdrachten in een XML-bestand toevoegen aan de huidige geschiedenis

In dit voor beeld worden de opdrachten in het `history.xml` bestand toegevoegd aan de huidige sessie geschiedenis.

```powershell
Add-History -InputObject (Import-Clixml c:\temp\history.xml)
```

De **input object** para meter geeft de resultaten van de opdracht tussen haakjes naar de `Add-History` cmdlet. De opdracht tussen haakjes, die als eerste wordt uitgevoerd, importeert het `history.xml` bestand in Power shell. De `Add-History` cmdlet voegt vervolgens de opdrachten in het bestand toe aan de sessie geschiedenis.

## PARAMETERS

### -Input object

Hiermee geeft u een matrix op met vermeldingen die aan de geschiedenis moeten worden toegevoegd als **HistoryInfo** -object aan de sessie geschiedenis.
U kunt deze para meter gebruiken om een **HistoryInfo** -object in te dienen, zoals de waarden die door de `Get-History` -, `Import-Clixml` -of-cmdlets worden geretourneerd `Import-Csv` `Add-History` .

```yaml
Type: System.Management.Automation.PSObject[]
Parameter Sets: (All)
Aliases:

Required: False
Position: 0
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### -PassThru

Geeft aan dat deze cmdlet een **HistoryInfo** -object voor elk geschiedenis item retourneert. Deze cmdlet genereert standaard geen uitvoer.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
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

### Micro soft. Power shell. commands. HistoryInfo

U kunt een **HistoryInfo** -object door sluizen naar deze cmdlet.

## UITVOER

### Geen of Microsoft. Power shell. commands. HistoryInfo

Met deze cmdlet wordt een **HistoryInfo** -object geretourneerd als u de para meter **PassThru** opgeeft. Anders wordt met deze cmdlet geen uitvoer gegenereerd.

## OPMERKINGEN

De sessie geschiedenis is een lijst met de opdrachten die tijdens de sessie worden ingevoerd samen met de ID. De sessie geschiedenis vertegenwoordigt de volg orde van de uitvoering, de status en de begin-en eind tijd van de opdracht. Bij het invoeren van elke opdracht voegt Power shell deze toe aan de geschiedenis zodat u deze opnieuw kunt gebruiken. Zie [about_History](About/about_History.md)voor meer informatie over de sessie geschiedenis.

Als u de opdrachten die u aan de geschiedenis wilt toevoegen wilt opgeven, gebruikt u de para meter **input object** . De `Add-History` opdracht accepteert alleen **HistoryInfo** -objecten, zoals die voor elke opdracht door de cmdlet worden geretourneerd `Get-History` . U kunt het pad en de bestands naam of een lijst met opdrachten niet door geven.

U kunt de para meter **input object** gebruiken om een bestand met **HistoryInfo** -objecten door te geven aan `Add-History` . Als u dit wilt doen, exporteert u de resultaten van een `Get-History` opdracht naar een bestand met behulp van de- `Export-Csv` of- `Export-Clixml` cmdlet en importeert u vervolgens het bestand met behulp van de- `Import-Csv` of- `Import-Clixml` cmdlets. U kunt het bestand met geïmporteerde **HistoryInfo** -objecten vervolgens door geven aan de `Add-History` hand van een pijp lijn of een variabele. Zie de voor beelden voor meer informatie.

Het bestand met **HistoryInfo** -objecten dat u doorgeeft aan de `Add-History` cmdlet moet het type gegevens, de kolom koppen en alle eigenschappen van de **HistoryInfo** -objecten bevatten. Als u van plan bent om de objecten weer aan te geven, moet u `Add-History` niet de para meter **NoTypeInformation** van de `Export-Csv` cmdlet gebruiken en de type gegevens, kolom koppen of andere velden in het bestand niet verwijderen.

Als u de sessie geschiedenis wilt wijzigen, exporteert u de sessie naar een CSV-of XML-bestand, wijzigt u het bestand, importeert u het bestand en gebruikt u dit om het toe `Add-History` te voegen aan de huidige sessie geschiedenis.

## GERELATEERDE KOPPELINGEN

[Wissen-geschiedenis](Clear-History.md)

[Get-geschiedenis](Get-History.md)

[Invoke-geschiedenis](Invoke-History.md)

[about_PSReadLine](../PSReadLine/About/about_PSReadLine.md)

[Get-PSReadLineOption](/powershell/module/psreadline/get-psreadlineoption)

[Set-PSReadLineOption](/powershell/module/psreadline/set-psreadlineoption)

