---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 03/12/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/convert-path?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Convert-Path
ms.openlocfilehash: fa66e42e182a7dea830ab30373682e4d1e6601e3
ms.sourcegitcommit: de63e9481cf8024883060aae61fb02c59c2de662
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/03/2020
ms.locfileid: "93249616"
---
# Convert-Path

## SAMENVATTING
Converteert een pad van een Power shell-pad naar een Power shell-provider pad.

## SYNTAXIS

### Pad (standaard)

```
Convert-Path [-Path] <String[]> [<CommonParameters>]
```

### LiteralPath

```
Convert-Path -LiteralPath <String[]> [<CommonParameters>]
```

## BESCHRIJVING

De `Convert-Path` cmdlet converteert een pad van een Power shell-pad naar een Power shell-provider pad.

## VOORBEELDEN

### Voor beeld 1: de werkmap converteren naar een standaard bestandssysteempad

In dit voor beeld wordt de huidige werkmap, die wordt vertegenwoordigd door een punt ( `.` ), geconverteerd naar een standaard bestandssysteempad.

```
PS C:\> Convert-Path .
C:\
```

### Voor beeld 2: een pad naar een provider converteren naar een standaard registerpad

In dit voor beeld wordt het pad van de Power shell-provider geconverteerd naar een standaardpad voor het REGI ster.

```powershell
PS C:\> Convert-Path HKLM:\Software\Microsoft
HKEY_LOCAL_MACHINE\Software\Microsoft
```

### Voor beeld 3: een pad naar een teken reeks converteren

In dit voor beeld wordt het pad naar de basismap van de huidige provider, de bestandssysteem provider, geconverteerd naar een teken reeks.

```powershell
PS C:\> Convert-Path ~
C:\Users\User01
```

## PARAMETERS

### -LiteralPath

Hiermee geeft u als een teken reeks matrix het pad op dat moet worden geconverteerd. De waarde van de para meter **LiteralPath** wordt precies zo gebruikt als deze wordt getypt. Geen tekens worden geïnterpreteerd als joker tekens. Als het pad escape tekens bevat, plaatst u het tussen enkele aanhalings tekens. Enkele aanhalings tekens geven aan dat Power shell geen karakters interpreteert als escape reeksen.

```yaml
Type: System.String[]
Parameter Sets: LiteralPath
Aliases: PSPath, LP

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -Path

Hiermee geeft u het Power shell-pad op dat moet worden geconverteerd.

```yaml
Type: System.String[]
Parameter Sets: Path
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### CommonParameters

Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable. Zie [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)voor meer informatie.

## INVOER

### System. String

U kunt een pad, maar geen letterlijk pad, naar deze cmdlet sluizen.

## UITVOER

### System. String

Deze cmdlet retourneert een teken reeks die het geconverteerde pad bevat.

## OPMERKINGEN

De cmdlets die het pad van de naam van het zelfstandige bestand bevatten en retour neren de namen in een beknopt formaat dat alle Power shell-providers kunnen interpreteren. Ze zijn ontworpen voor gebruik in Program ma's en scripts waarvoor u de volledige of gedeeltelijke naam van een pad wilt weer geven in een bepaalde indeling. Gebruik deze zoals u **mapnaam** , **Normpath** , **realpath** , **join's** of andere pad-werkers zou gebruiken.

U kunt de pad-cmdlets gebruiken met verschillende providers, waaronder het bestands systeem, het REGI ster en de certificaat providers.

Deze cmdlet is ontworpen om te werken met de gegevens die door elke provider worden weer gegeven. Als u een lijst wilt weer geven van de providers die beschikbaar zijn in uw sessie, typt u `Get-PSProvider` . Zie [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md)voor meer informatie.

`Convert-Path` alleen bestaande paden worden geconverteerd. Het kan niet worden gebruikt om een locatie te converteren die nog niet bestaat.

## GERELATEERDE KOPPELINGEN

[Pad voor samen voegen](Join-Path.md)

[Oplossen-pad](Resolve-Path.md)

[Split-pad](Split-Path.md)

[Test-pad](Test-Path.md)

[Get-PSProvider](Get-PSProvider.md)
