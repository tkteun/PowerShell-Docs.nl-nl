---
external help file: Microsoft.PowerShell.Utility-help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 01/17/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/format-hex?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Format-Hex
ms.openlocfilehash: 514a66ebee3827de998622a738c75d4f8e0c7279
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/07/2020
ms.locfileid: "93250450"
---
# Format-Hex

## SAMENVATTING

Geeft een bestand of andere invoer weer als hexadecimale notatie.

## SYNTAXIS

### Pad (standaard)

```
Format-Hex [-Path] <string[]> [<CommonParameters>]
```

### LiteralPath

```
Format-Hex -LiteralPath <string[]> [<CommonParameters>]
```

### ByInputObject

```
Format-Hex -InputObject <Object> [-Encoding <string>] [-Raw] [<CommonParameters>]
```

## BESCHRIJVING

De `Format-Hex` cmdlet geeft een bestand of andere invoer weer als hexadecimale waarden. Als u de verschuiving van een teken van de uitvoer wilt bepalen, voegt u het nummer aan de linkerkant van de rij toe aan het getal boven aan de kolom voor dat teken.

De `Format-Hex` cmdlet kan u helpen bij het bepalen van het bestands type van een beschadigd bestand of een bestand dat mogelijk geen bestands extensie heeft. U kunt deze cmdlet uitvoeren en vervolgens de hexadecimale uitvoer lezen om informatie over het bestand op te halen.

Wanneer u `Format-Hex` een bestand gebruikt, negeert de cmdlet nieuwe regel tekens en retourneert de volledige inhoud van een bestand in één teken reeks met de tekens voor de nieuwe regel.

## VOORBEELDEN

### Voor beeld 1: de hexadecimale weer gave van een teken reeks ophalen

Met deze opdracht wordt de hexadecimale waarde van een teken reeks geretourneerd.

```powershell
'Hello World' | Format-Hex
```

```Output
           00 01 02 03 04 05 06 07 08 09 0A 0B 0C 0D 0E 0F

00000000   48 65 6C 6C 6F 20 57 6F 72 6C 64                 Hello World
```

De teken reeks **Hallo wereld** wordt via de pijp lijn naar de `Format-Hex` cmdlet verzonden. De hexadecimale uitvoer van `Format-Hex` bevat de waarden van elk teken in de teken reeks.

### Voor beeld 2: een bestands type zoeken in hexadecimale uitvoer

In dit voor beeld wordt de hexadecimale uitvoer gebruikt om het bestands type te bepalen. Met de cmdlet worden het volledige pad van het bestand en de hexadecimale waarden weer gegeven.

Als u de volgende opdracht wilt testen, maakt u een kopie van een bestaand PDF-bestand op uw lokale computer en wijzigt u de naam van het gekopieerde bestand in **File. t7f**.

```powershell
Format-Hex -Path .\File.t7f
```

```Output
           Path: C:\Test\File.t7f

           00 01 02 03 04 05 06 07 08 09 0A 0B 0C 0D 0E 0F

00000000   25 50 44 46 2D 31 2E 35 0D 0A 25 B5 B5 B5 B5 0D  %PDF-1.5..%????.
00000010   0A 31 20 30 20 6F 62 6A 0D 0A 3C 3C 2F 54 79 70  .1 0 obj..<</Typ
00000020   65 2F 43 61 74 61 6C 6F 67 2F 50 61 67 65 73 20  e/Catalog/Pages
```

De `Format-Hex` cmdlet gebruikt de para meter **Path** om een bestands naam op te geven in de huidige map `File.t7f` . De bestands extensie `.t7f` is ongebruikelijk, maar in de hexadecimale uitvoer `%PDF` ziet u dat het een PDF-bestand is.

### Voor beeld 3: onbewerkte hexadecimale uitvoer weer geven

Standaard `Format-Hex` kiest u voor een compacte uitvoer van numerieke gegevens typen: single-byte of dubbel-byte reeksen worden gebruikt als de waarde klein genoeg is. Met de para meter **RAW** wordt dit gedrag gedeactiveerd.

```
PS> 1,2,3,1000 | Format-Hex

           Path:

           00 01 02 03 04 05 06 07 08 09 0A 0B 0C 0D 0E 0F

00000000   01 02 03 E8 03                                   ...è.


PS> 1,2,3,1000 | Format-Hex -Raw

           Path:

           00 01 02 03 04 05 06 07 08 09 0A 0B 0C 0D 0E 0F

00000000   01 00 00 00 02 00 00 00 03 00 00 00 E8 03 00 00  ............è...
```

Let op het verschil in uitvoer. De **onbewerkte** para meter geeft de getallen weer als 4-byte waarden, True voor hun **Int32** -typen.

## PARAMETERS

### -Encoding

Hiermee geeft u de code ring van de uitvoer op. Dit is alleen van toepassing op `[string]` invoer. De para meter heeft geen invloed op numerieke typen. De standaardwaarde is `ASCII`.

De acceptabele waarden voor deze para meter zijn als volgt:

- `Ascii` Maakt gebruik van ASCII-tekenset (7-bits).
- `BigEndianUnicode` Maakt gebruik van UTF-16 met de byte volgorde big endian.
- `Unicode` Maakt gebruik van UTF-16 met de byte volgorde little endian.
- `UTF7` Maakt gebruik van UTF-7.
- `UTF8` Maakt gebruik van UTF-8.
- `UTF32` Maakt gebruik van UTF-32 met de byte volgorde little endian.

Niet-ASCII-tekens in de invoer worden uitgevoerd als letterlijke `?` tekens als gevolg van gegevens verlies.

```yaml
Type: System.String
Parameter Sets: ByInputObject
Aliases:
Accepted values: ASCII, BigEndianUnicode, Unicode, UTF7, UTF8, UTF32

Required: False
Position: Named
Default value: ASCII
Accept pipeline input: False
Accept wildcard characters: False
```

### -Input object

Wordt gebruikt voor de invoer van de pijp lijn. Pijplijn invoer ondersteunt alleen bepaalde scalaire typen en `[system.io.fileinfo]` instanties voor sluizen van `Get-ChildItem` .

De ondersteunde scalaire typen zijn:

- `[string]`
- `[byte]`
- `[int]`, `[int32]`
- `[long]`, `[int64]`

```yaml
Type: System.Object
Parameter Sets: ByInputObject
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### -LiteralPath

Hiermee geeft u het volledige pad naar een bestand. De waarde van **LiteralPath** wordt precies zo gebruikt als deze wordt getypt.
Deze para meter accepteert geen joker tekens. Als u meerdere paden naar bestanden wilt opgeven, scheidt u de paden met een komma. Als de para meter **LiteralPath** escape-tekens bevat, plaatst u het pad tussen enkele aanhalings tekens. Power shell interpreteert geen tekens in één aanhalings teken reeks als escape-reeksen. Zie [about_Quoting_Rules](../Microsoft.Powershell.Core/About/about_Quoting_Rules.md)voor meer informatie.

```yaml
Type: System.String[]
Parameter Sets: LiteralPath
Aliases: PSPath

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Path

Hiermee geeft u het pad naar de bestanden. Gebruik een punt ( `.` ) om de huidige locatie op te geven. Het Joker teken ( `*` ) wordt geaccepteerd en kan worden gebruikt om alle items op een locatie op te geven. Als de para meter **Path** escape tekens bevat, plaatst u het pad tussen enkele aanhalings tekens. Als u meerdere paden naar bestanden wilt opgeven, scheidt u de paden met een komma.

```yaml
Type: System.String[]
Parameter Sets: Path
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: True
```

### -RAW

Standaard `Format-Hex` kiest u voor een compacte uitvoer van numerieke gegevens typen: single-byte of dubbel-byte reeksen worden gebruikt als de waarde klein genoeg is. Met de para meter **RAW** wordt dit gedrag gedeactiveerd.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: ByInputObject
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

### System. String

U kunt een teken reeks door sluizen naar deze cmdlet.

## UITVOER

### Micro soft. Power shell. commands. ByteCollection

Met deze cmdlet wordt een **ByteCollection** geretourneerd. Dit object vertegenwoordigt een verzameling van bytes. Het bevat methoden die het verzamelen van bytes converteren naar een teken reeks die is opgemaakt als elke regel van uitvoer die wordt geretourneerd door `Format-Hex` . Als u de para meter **Path** of **LiteralPath** opgeeft, bevat het object ook het pad van het bestand dat elke byte bevat.

## OPMERKINGEN

De meest rechtse kolom van uitvoer probeert de bytes als tekens weer te geven:

Over het algemeen wordt elke byte geïnterpreteerd als een Unicode-code punt, wat betekent dat:

- Afdruk bare ASCII-tekens worden altijd correct weer gegeven
- Multi-byte UTF-8 tekens worden nooit correct weer gegeven
- UTF-16-tekens worden alleen correct weer gegeven als er een hoge byte is `NUL` .

## GERELATEERDE KOPPELINGEN

[about_Quoting_Rules](../Microsoft.Powershell.Core/About/about_Quoting_Rules.md)

[Format-Custom](Format-Custom.md)

[Format-List](Format-List.md)

[Format-Table](Format-Table.md)

[Format-Wide](Format-Wide.md)
