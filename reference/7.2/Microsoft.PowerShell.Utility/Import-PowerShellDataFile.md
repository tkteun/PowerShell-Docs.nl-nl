---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 10/25/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/import-powershelldatafile?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Import-PowerShellDataFile
ms.openlocfilehash: 2853c5757b12e75e50948192e5a9e29889553b8e
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 11/17/2020
ms.locfileid: "94705428"
---
# Import-PowerShellDataFile

## SAMENVATTING
Hiermee worden waarden uit een `.PSD1` bestand geïmporteerd zonder dat de inhoud ervan wordt aangeroepen.

## SYNTAXIS

### ByPath (standaard)

```
Import-PowerShellDataFile [-Path] <String[]> [<CommonParameters>]
```

### ByLiteralPath

```
Import-PowerShellDataFile [-LiteralPath] <String[]> [<CommonParameters>]
```

## BESCHRIJVING

Met de `Import-PowerShellDataFile` cmdlet worden sleutel-waardeparen van hashtabellen die in een bestand zijn gedefinieerd, veilig geïmporteerd `.PSD1` . De waarden kunnen worden geïmporteerd `Invoke-Expression` op basis van de inhoud van het bestand.
Voert echter `Invoke-Expression` alle code in het bestand uit. Dit kan ongewenste resultaten opleveren of onveilige code uitvoeren. `Import-PowerShellDataFile` Hiermee importeert u de gegevens zonder de code aan te roepen.

## VOORBEELDEN

### Voor beeld 1: waarden ophalen uit PSD1

In dit voor beeld worden de sleutel-waardeparen opgehaald die zijn opgeslagen in de hashtabel die in het bestand worden bewaard `Configuration.psd1` . `Get-Content` wordt gebruikt om de inhoud van het bestand weer te geven `Configuration.psd1` .

```powershell
Get-Content .\Configuration.psd1
$config = Import-PowerShellDataFile .\Configuration.psd1
$config.AllNodes
```

```Output
@{
    AllNodes = @(
        @{
            NodeName = 'DSC-01'
        }
        @{
            NodeName = 'DSC-02'
        }
    )
}

Name                           Value
----                           -----
NodeName                       DSC-01
NodeName                       DSC-02
```

## PARAMETERS

### -LiteralPath

Het pad naar het bestand dat wordt geïmporteerd. Alle tekens in het pad worden beschouwd als letterlijke waarden.
Joker tekens worden niet verwerkt.

```yaml
Type: System.String[]
Parameter Sets: ByLiteralPath
Aliases: PSPath, LP

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -Path

Het pad naar het bestand dat wordt geïmporteerd. Joker tekens zijn toegestaan, maar alleen het eerste overeenkomende bestand wordt geïmporteerd.

```yaml
Type: System.String[]
Parameter Sets: ByPath
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: True
```

### CommonParameters

Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable. Zie [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md)voor meer informatie.

## INVOER

## UITVOER

### System. Collections. hashtabel

## OPMERKINGEN

## GERELATEERDE KOPPELINGEN

[Invoke-expressie](Invoke-Expression.md)

[Import-LocalizedData](Import-LocalizedData.md)

