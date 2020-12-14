---
external help file: System.Management.Automation.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 10/06/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/get-history?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-History
ms.openlocfilehash: be47925211c57760ddbd0bd4c8e985e161d24593
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 11/17/2020
ms.locfileid: "94705499"
---
# Get-History

## SAMENVATTING
Hiermee wordt een lijst opgehaald met de opdrachten die tijdens de huidige sessie zijn ingevoerd.

## SYNTAXIS

```
Get-History [[-Id] <Int64[]>] [[-Count] <Int32>] [<CommonParameters>]
```

## BESCHRIJVING

Met de `Get-History` cmdlet krijgt u de sessie geschiedenis, dat wil zeggen, de lijst met opdrachten die tijdens de huidige sessie zijn ingevoerd.

Power shell onderhoudt automatisch een geschiedenis van elke sessie. Het aantal vermeldingen in de sessie geschiedenis wordt bepaald door de waarde van de `$MaximumHistoryCount` Voorkeurs variabele. Met ingang van Windows Power Shell 3,0 is de standaard waarde `4096` . Standaard worden geschiedenis bestanden opgeslagen in de hoofdmap, maar u kunt het bestand opslaan op elke locatie. Zie [about_History](About/about_History.md)voor meer informatie over de geschiedenis functies in Power shell.

De sessie geschiedenis wordt afzonderlijk beheerd vanaf de geschiedenis die wordt onderhouden door de **PSReadLine** -module.
Beide geschiedenissen zijn beschikbaar in sessies waarin **PSReadLine** wordt geladen. Deze cmdlet werkt alleen met de sessie geschiedenis. Zie [about_PSReadLine](../PSReadLine/About/about_PSReadLine.md)voor meer informatie.

## VOORBEELDEN

### Voor beeld 1: de sessie geschiedenis ophalen

In dit voor beeld worden de vermeldingen in de sessie geschiedenis opgehaald. De standaard weergave toont elke opdracht en de bijbehorende ID, die de volg orde aangeeft waarin ze zijn uitgevoerd.

```powershell
Get-History
```

### Voor beeld 2: gegevens ophalen die een teken reeks bevatten

In dit voor beeld worden gegevens in de opdracht geschiedenis met de teken reeks service opgehaald. Met de eerste opdracht worden alle vermeldingen in de sessie geschiedenis opgehaald. De pijplijn operator ( `|` ) geeft de resultaten door aan de `Where-Object` cmdlet, waarmee alleen de opdrachten worden geselecteerd die service bevatten.

```powershell
Get-History | Where-Object {$_.CommandLine -like "*Service*"}
```

### Voor beeld 3: geschiedenis vermeldingen naar een specifieke ID exporteren

In dit voor beeld worden de vijf meest recente geschiedenis vermeldingen opgehaald die eindigen op entry 7. Met de pijplijn operator wordt het resultaat door gegeven aan de `Export-Csv` cmdlet, die de geschiedenis opmaakt als tekst met scheidings tekens en opslaat in het History.csv bestand. Het bestand bevat de gegevens die worden weer gegeven wanneer u de geschiedenis opmaakt als een lijst. Dit omvat de status en de begin-en eind tijd van de opdracht.

```powershell
Get-History -ID 7 -Count 5 | Export-Csv History.csv
```

### Voor beeld 4: de meest recente opdracht weer geven

In dit voor beeld wordt de laatste opdracht in de opdracht geschiedenis opgehaald. De laatste opdracht is de laatst ingevoerde opdracht. Met deze opdracht wordt de para meter **aantal** gebruikt om slechts één opdracht weer te geven. Standaard worden `Get-History` de meest recente opdrachten opgehaald. Deze opdracht kan worden afgekort tot ' h-c 1 ' en heeft hetzelfde effect als het drukken op de pijl toets.

```powershell
Get-History -Count 1
```

### Voor beeld 5: alle eigenschappen van de vermeldingen in de geschiedenis weer geven

In dit voor beeld worden alle eigenschappen van vermeldingen in de sessie geschiedenis weer gegeven. De pijplijn operator geeft de resultaten van een `Get-History` opdracht door aan de `Format-List` cmdlet, waarin alle eigenschappen van elk geschiedenis item worden weer gegeven. Dit omvat de ID, de status en de begin-en eind tijd van de opdracht.

```powershell
Get-History | Format-List -Property *
```

## PARAMETERS

### -Aantal

Hiermee geeft u het aantal van de meest recente geschiedenis vermeldingen op die met deze cmdlet worden opgehaald. Met standaard `Get-History` haalt alle vermeldingen in de sessie geschiedenis. Als u de para meters **Count** en **id** in een opdracht gebruikt, wordt de weer gave beëindigd met de opdracht die is opgegeven door de **id-** para meter.

In Windows Power Shell 2,0 worden standaard `Get-History` de 32 meest recente vermeldingen opgehaald.

```yaml
Type: System.Int32
Parameter Sets: (All)
Aliases:

Required: False
Position: 1
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Id

Hiermee geeft u een matrix met de Id's van vermeldingen in de sessie geschiedenis. `Get-History` Hiermee worden alleen opgegeven vermeldingen opgehaald. Als u de para meters **id** en **aantal** in een opdracht gebruikt, worden `Get-History` de meest recente vermeldingen opgehaald die eindigen op de vermelding die is opgegeven door de **id-** para meter.

```yaml
Type: System.Int64[]
Parameter Sets: (All)
Aliases:

Required: False
Position: 0
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### CommonParameters

Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable. Zie [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)voor meer informatie.

## INVOER

### System. Int64

U kunt een geschiedenis-ID door sluizen naar deze cmdlet.

## UITVOER

### Micro soft. Power shell. commands. HistoryInfo

Met deze cmdlet wordt een geschiedenis object geretourneerd voor elk geschiedenis item dat wordt opgehaald.

## OPMERKINGEN

De sessie geschiedenis is een lijst met opdrachten die tijdens de sessie zijn ingevoerd. De sessie geschiedenis vertegenwoordigt de uitvoerings volgorde, de status en de begin-en eind tijd van de opdracht. Bij het invoeren van elke opdracht voegt Power shell deze toe aan de geschiedenis zodat u deze opnieuw kunt gebruiken. Zie [about_History](About/about_History.md)voor meer informatie over de opdracht geschiedenis.

Vanaf Windows Power Shell 3,0 is de standaard waarde van de `$MaximumHistoryCount` Voorkeurs variabele `4096` . In Windows Power Shell 2,0 is de standaard waarde `64` . Zie about_Preference_Variables voor meer informatie over de `$MaximumHistoryCount` variabele [](About/about_Preference_Variables.md).

## GERELATEERDE KOPPELINGEN

[Toevoegen-geschiedenis](Add-History.md)

[Wissen-geschiedenis](Clear-History.md)

[Invoke-geschiedenis](Invoke-History.md)

[about_History](About/about_History.md)
