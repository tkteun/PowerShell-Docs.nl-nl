---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/import-alias?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Import-Alias
ms.openlocfilehash: 438f089c1cd6e647ae5ee858234a3919bdc0328d
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/07/2020
ms.locfileid: "93250959"
---
# Import-Alias

## SAMENVATTING
Hiermee wordt een alias lijst uit een bestand geïmporteerd.

## SYNTAXIS

### ByPath (standaard)

```
Import-Alias [-Path] <String> [-Scope <String>] [-PassThru] [-Force] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### ByLiteralPath

```
Import-Alias -LiteralPath <String> [-Scope <String>] [-PassThru] [-Force] [-WhatIf] [-Confirm]
 [<CommonParameters>]
```

## BESCHRIJVING

Met de `Import-Alias` cmdlet wordt een alias lijst uit een bestand geïmporteerd.

Als er in Windows Power Shell 3,0 een beveiligings functie wordt gebruikt, `Import-Alias` worden bestaande aliassen standaard niet overschreven.
Als u een bestaande alias wilt overschrijven, gebruikt u de para meter Force om te **zorgen** dat de inhoud van het alias bestand veilig is.

## VOORBEELDEN

### Voor beeld 1: aliassen importeren uit een bestand

```powershell
Import-Alias test.txt
```

Met deze opdracht worden alias gegevens uit een bestand met de naam test.txt geïmporteerd.

## PARAMETERS

### -Force

Hiermee kan de cmdlet een alias importeren die al is gedefinieerd of alleen-lezen is.
U kunt de volgende opdracht gebruiken om informatie weer te geven over de momenteel gedefinieerde aliassen:

`Get-Alias | Select-Object Name, Options`

Als de bijbehorende alias alleen-lezen is, wordt deze weer gegeven in de waarde van de eigenschap **Options** .

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

### -LiteralPath

Hiermee geeft u het pad naar een bestand met geëxporteerde alias gegevens.
In tegens telling tot de para meter **Path** wordt de waarde van de para meter **LiteralPath** exact gebruikt terwijl deze wordt getypt.
Geen tekens worden geïnterpreteerd als joker tekens.
Als het pad escape tekens bevat, plaatst u het tussen enkele aanhalings tekens.
Enkele aanhalings tekens geven aan dat Power shell geen karakters interpreteert als escape reeksen.

```yaml
Type: System.String
Parameter Sets: ByLiteralPath
Aliases: PSPath, LP

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### -PassThru

Retourneert een object dat het item vertegenwoordigt waarmee u werkt.
Deze cmdlet genereert standaard geen uitvoer.

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

### -Path

Hiermee geeft u het pad naar een bestand met geëxporteerde alias gegevens.
Joker tekens zijn toegestaan, maar moeten worden omgezet in één naam.

```yaml
Type: System.String
Parameter Sets: ByPath
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: True
```

### -Bereik

Hiermee geeft u het bereik op waarin de aliassen worden geïmporteerd.
De aanvaardbare waarden voor deze parameter zijn:

- Globaal
- Lokaal
- Script
- Een getal dat relatief is ten opzichte van het huidige bereik (0 tot en met het aantal bereiken, waarbij 0 het huidige bereik is en 1 de bovenliggende scope)

De standaard waarde is lokaal.
Zie about_Scopes voor meer informatie.

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Confirm

Hiermee wordt u gevraagd om bevestiging voordat u de cmdlet uitvoert.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: cf

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### -WhatIf

Hiermee wordt weergegeven wat er zou gebeuren als u de cmdlet uitvoert.
De cmdlet wordt niet uitgevoerd.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: wi

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### CommonParameters

Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable. Zie [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)voor meer informatie.

## INVOER

### System. String

U kunt een teken reeks met een pad naar door sluizen `Import-Alias` .

## UITVOER

### Geen of System. Management. Automation. AliasInfo

Wanneer u de para meter **PassThru** gebruikt, `Import-Alias` retourneert een **System. Management. Automation. AliasInfo** -object dat de alias vertegenwoordigt.
Anders wordt met deze cmdlet geen uitvoer gegenereerd.

## OPMERKINGEN

## GERELATEERDE KOPPELINGEN

[Exporteren-alias](Export-Alias.md)

[Get-alias](Get-Alias.md)

[Nieuwe alias](New-Alias.md)

[Set-alias](Set-Alias.md)
