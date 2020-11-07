---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 10/28/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/out-printer?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Out-Printer
ms.openlocfilehash: bd9a141537c7f075d3c02827af4694813d6f0db6
ms.sourcegitcommit: 177ae45034b58ead716853096b2e72e4864e6df6
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 11/07/2020
ms.locfileid: "94346918"
---
# Out-Printer

## SAMENVATTING
Hiermee wordt uitvoer naar een printer verzonden.

## SYNTAXIS

```
Out-Printer [[-Name] <String>] [-InputObject <PSObject>] [<CommonParameters>]
```

## BESCHRIJVING

De `Out-Printer` cmdlet verzendt uitvoer naar de standaard printer of naar een andere printer, als deze is opgegeven.

> [!NOTE]
> Deze cmdlet is opnieuw geïntroduceerd in Power shell 7. Deze cmdlet is alleen beschikbaar op Windows-systemen die ondersteuning bieden voor het Windows-bureau blad.

## VOORBEELDEN

### Voor beeld 1: een bestand verzenden dat moet worden afgedrukt op de standaard printer

In dit voor beeld ziet u hoe u een bestand afdrukt, zelfs als dit `Out-Printer` geen **pad** -para meter heeft.

```powershell
Get-Content -Path ./readme.txt | Out-Printer
```

`Get-Content`Hiermee wordt de inhoud van het `readme.txt` bestand in de huidige map opgehaald en `Out-Printer` verzonden naar de standaard printer.

### Voor beeld 2: een teken reeks naar een externe printer afdrukken

In dit voor beeld wordt `Hello, World` de **PRT-6b Color-** printer op Server01 afgedrukt.

```powershell
"Hello, World" | Out-Printer -Name "\\Server01\Prt-6B Color"
```

De para meter **name** selecteert een specifieke printer in plaats van de standaard instelling.

### Voor beeld 3: een Help-onderwerp naar de standaard printer afdrukken

In dit voor beeld wordt de volledige versie van het Help-onderwerp voor beschreven `Get-CimInstance` .

```powershell
$H = Get-Help -Full Get-CimInstance
Out-Printer -InputObject $H
```

`Get-Help` Hiermee haalt u de volledige versie van het Help-onderwerp op `Get-CimInstance` en slaat u deze op in de `$H` variabele. De para meter **input object** geeft de waarde `$H` aan van to `Out-Printer` .

## PARAMETERS

### -Input object

Hiermee geeft u de objecten die naar de printer moeten worden verzonden. Voer een variabele in die de objecten bevat, of typ een opdracht of expressie waarmee de objecten worden opgehaald.

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

### -Name

Hiermee wordt de uitvoer naar de opgegeven printer verzonden. De parameter naam **naam** is optioneel.

```yaml
Type: System.String
Parameter Sets: (All)
Aliases: PrinterName

Required: False
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### CommonParameters

Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable. Zie [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)voor meer informatie.

## INVOER

### System. Management. Automation. PSObject

U kunt elk object door sluizen naar `Out-Printer` .

## UITVOER

### Geen

`Out-Printer` retourneert geen objecten.

## OPMERKINGEN

Deze cmdlet is alleen beschikbaar op Windows-platforms.

De cmdlets die de term bevatten, `Out` hebben geen-objecten. Ze worden alleen weer gegeven en verzonden naar de opgegeven weergave bestemming. Als u een niet-opgemaakt object naar een `Out` cmdlet verzendt, verzendt de cmdlet het naar een format-cmdlet voordat deze wordt weer gegeven.

`Out-Printer` Hiermee verzendt u gegevens naar de printer, maar worden er geen uitvoer objecten naar de pijp lijn verzonden. Als u de uitvoer van naar toesluist `Out-Printer` `Get-Member` , `Get-Member` rapporten dat er geen objecten zijn opgegeven.

## GERELATEERDE KOPPELINGEN

[Out-file](Out-File.md)

[Out-teken reeks](Out-String.md)
