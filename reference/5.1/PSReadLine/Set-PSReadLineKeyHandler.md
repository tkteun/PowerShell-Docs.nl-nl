---
external help file: Microsoft.PowerShell.PSReadLine2.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: PSReadline
ms.date: 12/07/2018
online version: https://docs.microsoft.com/powershell/module/psreadline/set-psreadlinekeyhandler?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Set-PSReadLineKeyHandler
ms.openlocfilehash: 8eefd819b59cf8d0050484c6aad3058bc6e7753a
ms.sourcegitcommit: ae8b89e12c6fa2108075888dd6da92788d6c2888
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/21/2020
ms.locfileid: "93253154"
---
# Set-PSReadLineKeyHandler

## SAMENVATTING
Koppelt sleutels aan door de gebruiker gedefinieerde of PSReadLine.

## SYNTAXIS

### Script Block

```
Set-PSReadLineKeyHandler [-ScriptBlock] <ScriptBlock> [-BriefDescription <String>]
 [-Description <String>] [-Chord] <String[]> [-ViMode <ViMode>] [<CommonParameters>]
```

### Functie

```
Set-PSReadLineKeyHandler [-Chord] <String[]> [-ViMode <ViMode>] [-Function] <String>
 [<CommonParameters>]
```

## BESCHRIJVING

Met de `Set-PSReadLineKeyHandler` cmdlet wordt het resultaat aangepast wanneer een toets of reeks sleutels wordt ingedrukt. Met door de gebruiker gedefinieerde sleutel bindingen kunt u bijna alles doen die mogelijk is vanuit een Power shell-script.

## VOORBEELDEN

### Voor beeld 1: de pijl sleutel binden aan een functie

Met deze opdracht wordt de pijl-omhoog gekoppeld aan de functie **HistorySearchBackward** . Met deze functie wordt de opdracht geschiedenis doorzocht op opdracht regels die beginnen met de huidige inhoud van de opdracht regel.

```powershell
Set-PSReadLineKeyHandler -Chord UpArrow -Function HistorySearchBackward
```

### Voor beeld 2: een sleutel binden aan een script blok

In dit voor beeld ziet u hoe een enkele sleutel kan worden gebruikt om een opdracht uit te voeren. Met de opdracht wordt de sleutel gebonden `Ctrl+B` aan een script blok waarmee de regel wordt gewist, wordt het woord build ingevoegd en wordt de regel vervolgens geaccepteerd.

```powershell
Set-PSReadLineKeyHandler -Chord Ctrl+B -ScriptBlock {
    [Microsoft.PowerShell.PSConsoleReadLine]::RevertLine()
    [Microsoft.PowerShell.PSConsoleReadLine]::Insert('build')
    [Microsoft.PowerShell.PSConsoleReadLine]::AcceptLine()
}
```

## PARAMETERS

### -BriefDescription

Een korte beschrijving van de sleutel binding. Deze beschrijving wordt weer gegeven door de `Get-PSReadLineKeyHandler` cmdlet.

```yaml
Type: System.String
Parameter Sets: ScriptBlock
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Koord

De sleutel of reeks sleutels die moeten worden gebonden aan een functie of script blok. Gebruik één teken reeks om één binding op te geven. Als de binding een reeks sleutels is, scheidt u de sleutels met een komma, zoals in het volgende voor beeld:

`Ctrl+X,Ctrl+L`

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

### -Beschrijving

Hiermee geeft u een gedetailleerde beschrijving op van de sleutel binding die zichtbaar is in de uitvoer van de `Get-PSReadLineKeyHandler` cmdlet.

```yaml
Type: System.String
Parameter Sets: ScriptBlock
Aliases: LongDescription

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Functie

Hiermee geeft u de naam op van een bestaande sleutel-handler die wordt opgegeven door PSReadLine. Met deze para meter kunt u bestaande sleutel bindingen opnieuw binden of een handler binden die momenteel niet is gebonden.

```yaml
Type: System.String
Parameter Sets: Function
Aliases:

Required: True
Position: 1
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Script Block

Hiermee geeft u een script blok waarde op die moet worden uitgevoerd wanneer de koorde wordt ingevoerd. PSReadLine geeft een of twee para meters door aan dit script blok. De eerste para meter is een **ConsoleKeyInfo** -object waarmee de toets wordt ingedrukt. Het tweede argument kan elk object zijn, afhankelijk van de context.

```yaml
Type: System.Management.Automation.ScriptBlock
Parameter Sets: ScriptBlock
Aliases:

Required: True
Position: 1
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -ViMode

Geef op op welke VI-modus de binding van toepassing is.

Geldige waarden zijn:

- Invoegen
- Opdracht

```yaml
Type: Microsoft.PowerShell.ViMode
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

### Geen

U kunt geen objecten naar deze cmdlet pipeen.

## UITVOER

### Geen

Met deze cmdlet wordt geen uitvoer gegenereerd.

## OPMERKINGEN

## GERELATEERDE KOPPELINGEN

[Get-PSReadLineKeyHandler](Get-PSReadLineKeyHandler.md)

[Remove-PSReadLineKeyHandler](Remove-PSReadLineKeyHandler.md)

[Get-PSReadLineOption](Get-PSReadLineOption.md)

[Set-PSReadLineOption](Set-PSReadLineOption.md)
