---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 09/21/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/get-clipboard?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-Clipboard
ms.openlocfilehash: 2885b2624f8334e8699e0baea5fc41b3f025fe2a
ms.sourcegitcommit: d757d64ea8c8af4d92596e8fbe15f2f40d48d3ac
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 09/22/2020
ms.locfileid: "93251941"
---
# Get-Clipboard

## SAMENVATTING
Hiermee wordt de huidige Windows klem bord-vermelding opgehaald.

## SYNTAXIS

```
Get-Clipboard [-Format <ClipboardFormat>] [-TextFormatType <TextDataFormat>] [-Raw] [<CommonParameters>]
```

## BESCHRIJVING

De `Get-Clipboard` cmdlet haalt het huidige Windows klem bord-item op. Meerdere tekst regels worden geretourneerd als een matrix met teken reeksen die vergelijkbaar zijn met `Get-Content` .

## VOORBEELDEN

### Voor beeld 1: de inhoud van het klem bord ophalen en weer geven op de opdracht regel

In dit voor beeld hebben we met de rechter muisknop op een afbeelding in een browser geklikt en de **Kopieer** actie gekozen. De volgende opdracht wordt de koppeling als een URL van de afbeelding die op het klem bord is opgeslagen weer gegeven.

```powershell
Get-Clipboard
```

```Output
https://en.wikipedia.org/wiki/PowerShell
```

### Voor beeld 2: de inhoud van het klem bord in een specifieke indeling ophalen

In dit voor beeld hebben we bestanden gekopieerd naar het klem bord in Windows Explorerby ze te selecteren en op <kbd>CTRL + C</kbd>te drukken. Met de volgende opdracht kunt u de inhoud van het klem bord openen als een lijst met bestanden:

```powershell
Get-Clipboard -Format FileDropList
```

```Output
    Directory: C:\Git\PS-Docs\PowerShell-Docs\wmf

Mode                LastWriteTime         Length Name
----                -------------         ------ ----
-a----         5/7/2019   1:11 PM          10010 TOC.yml
-a----       11/18/2016  10:10 AM             53 md.style
-a----         5/6/2019   9:32 AM           4177 overview.md
-a----        6/28/2018   2:28 PM            345 README.md
```

## PARAMETERS

### -Indeling

Hiermee wordt het type of de indeling van het klem bord opgegeven. De aanvaardbare waarden voor deze parameter zijn:

- Tekst
- FileDropList
- Installatiekopie
- Audio

```yaml
Type: Microsoft.PowerShell.Commands.ClipboardFormat
Parameter Sets: (All)
Aliases:
Accepted values: Text, FileDropList, Image, Audio

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -RAW

Hiermee haalt u de volledige inhoud van het klem bord. Tekst met meerdere regels wordt geretourneerd als één teken reeks in plaats van een matrix met teken reeksen.

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

### -TextFormatType

Geeft het type tekst gegevens indeling van het klem bord aan. De aanvaardbare waarden voor deze parameter zijn:

- Tekst
- UnicodeText
- Formatting
- HTML
- CommaSeparatedValue

```yaml
Type: System.Windows.Forms.TextDataFormat
Parameter Sets: (All)
Aliases:
Accepted values: Text, UnicodeText, Rtf, Html, CommaSeparatedValue

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### CommonParameters

Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable. Zie [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)voor meer informatie.

## INVOER

## UITVOER

### System. String, System. IO. file info, System. IO. Stream, System. Drawing. image

## OPMERKINGEN

## GERELATEERDE KOPPELINGEN

[Set-klem bord](Set-Clipboard.md)
