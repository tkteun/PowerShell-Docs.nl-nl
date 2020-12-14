---
external help file: Microsoft.PowerShell.PSReadLine2.dll-Help.xml
Locale: en-US
Module Name: PSReadLine
ms.date: 12/07/2018
online version: https://docs.microsoft.com/powershell/module/psreadline/remove-psreadlinekeyhandler?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Remove-PSReadLineKeyHandler
ms.openlocfilehash: d280eba2e717ccfb0b896d62f42079390d1db848
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 11/17/2020
ms.locfileid: "94705575"
---
# Remove-PSReadLineKeyHandler

## SAMENVATTING
Hiermee verwijdert u een sleutel binding.

## SYNTAXIS

```
Remove-PSReadLineKeyHandler [-Chord] <String[]> [-ViMode <ViMode>] [<CommonParameters>]
```

## BESCHRIJVING

Met de `Remove-PSReadLineKeyHandler` cmdlet wordt een opgegeven toetsbinding verwijderd.

## VOORBEELDEN

### Voor beeld 1: een binding verwijderen

```powershell
Remove-PSReadLineKeyHandler -Chord Ctrl+B
```

Met deze opdracht wordt de binding van de toetscombinatie, of koorde, verwijderd `Ctrl+B` . De `Ctrl+B` koorde wordt in het `Set-PSReadLineKeyHandler` artikel gemaakt.

## PARAMETERS

### -Koord

Hiermee geeft u een matrix op met sleutels of reeksen van sleutels die moeten worden verwijderd. Er wordt één binding opgegeven met behulp van één teken reeks. Als de binding een reeks sleutels is, scheidt u de sleutels met een komma, zoals in het volgende voor beeld:

`Ctrl+x,Ctrl+l`

Deze para meter accepteert een matrix met teken reeksen. Elke teken reeks is een afzonderlijke binding, geen reeks sleutels voor één binding.

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases: Key

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -ViMode

Geef op op welke VI-modus de binding van toepassing is. Mogelijke waarden zijn: insert en Command.

```yaml
Type: Microsoft.PowerShell.ViMode
Parameter Sets: (All)
Aliases:
Accepted values: Insert, Command

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### CommonParameters

Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable. Zie [about_CommonParameters](http://go.microsoft.com/fwlink/?LinkID=113216)voor meer informatie.

## INVOER

### Geen

U kunt geen objecten naar deze cmdlet pipeen.

## UITVOER

### Geen

## OPMERKINGEN

## GERELATEERDE KOPPELINGEN

[Get-PSReadLineKeyHandler](Get-PSReadLineKeyHandler.md)

[Get-PSReadLineOption](Get-PSReadLineOption.md)

[Set-PSReadLineOption](Set-PSReadLineOption.md)

[Set-PSReadLineKeyHandler](Set-PSReadLineKeyHandler.md)

