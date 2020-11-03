---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 01/17/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/format-hex?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Format-Hex
ms.openlocfilehash: 64275e72f8c21942179431b3aed4a17d328aa2e9
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/07/2020
ms.locfileid: "93251117"
---
# Format-Hex

## SAMENVATTING

Geeft een bestand of andere invoer weer als hexadecimale notatie.

## SYNTAXIS

### Pad (standaard)

```
Format-Hex [-Path] <string[]> [-Count <long>] [-Offset <long>] [<CommonParameters>]
```

### LiteralPath

```
Format-Hex -LiteralPath <string[]> [-Count <long>] [-Offset <long>] [<CommonParameters>]
```

### Input object

```
Format-Hex -InputObject <psobject> [-Encoding <Encoding>] [-Count <long>] [-Offset <long>] [-Raw] [<CommonParameters>]
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

Als u de volgende opdracht wilt testen, maakt u een kopie van een bestaand PDF-bestand op uw lokale computer en wijzigt u de naam van het gekopieerde bestand in `File.t7f` .

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

De `Format-Hex` cmdlet gebruikt de para meter **Path** om een bestands naam op te geven in de huidige map **File. t7f**. De bestands extensie **. t7f** is ongebruikelijk, maar de hexadecimale uitvoer **% PDF** geeft aan dat het een PDF-bestand is.

## PARAMETERS

### -Encoding

Hiermee geeft u de code ring van de uitvoer op. Dit is alleen van toepassing op `[string]` invoer. De para meter heeft geen invloed op numerieke typen. De standaardwaarde is `utf8NoBOM`.

De acceptabele waarden voor deze para meter zijn als volgt:

- `ascii`: Gebruikt de code ring voor de ASCII-tekenset (7-bits).
- `bigendianunicode`: Wordt gecodeerd in UTF-16-indeling met behulp van de byte volgorde big endian.
- `oem`: Maakt gebruik van de standaard codering voor MS-DOS-en console Programma's.
- `unicode`: Wordt gecodeerd in UTF-16-indeling met behulp van de byte volgorde little endian.
- `utf7`: Wordt gecodeerd in de indeling UTF-7.
- `utf8`: Wordt gecodeerd in UTF-8-indeling.
- `utf8BOM`: Code ring in UTF-8-indeling met byte order Mark (BOM)
- `utf8NoBOM`: Code ring in UTF-8-indeling zonder byte order Mark (BOM)
- `utf32`: Gecodeerd in UTF-32-indeling.

Vanaf Power shell 6,2 kunnen met de para meter **Encoding** ook numerieke id's van geregistreerde code pagina's (zoals `-Encoding 1251` ) of teken reeks namen van geregistreerde code pagina's (zoals) worden toegestaan `-Encoding "windows-1251"` . Zie de .NET-documentatie voor [code ring. code tabel](/dotnet/api/system.text.encoding.codepage?view=netcore-2.2)voor meer informatie.

```yaml
Type: Encoding
Parameter Sets: ByInputObject
Aliases:
Accepted values: ASCII, BigEndianUnicode, OEM, Unicode, UTF7, UTF8, UTF8BOM, UTF8NoBOM, UTF32

Required: False
Position: Named
Default value: UTF8NoBOM
Accept pipeline input: False
Accept wildcard characters: False
```

### -Input object

Wordt gebruikt voor de invoer van de pijp lijn. Pijplijn invoer ondersteunt alleen bepaalde scalaire typen en `[system.io.fileinfo]` instanties voor sluizen van `Get-ChildItem` .

De ondersteunde scalaire typen zijn:

- `[string]`, `[char]`
- `[byte]`, `[sbyte]`
- `[int16]`, `[uint16]`, `[short]`, `[ushort]`
- `[int]`, `[uint]`, `[int32]`, `[uint32]`,
- `[long]`, `[ulong]`, `[int64]`, `[uint64]`
- `[single]`, `[float]`, `[double]`

```yaml
Type: System.Management.Automation.PSObject
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
Aliases: PSPath, LP

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

Deze para meter heeft niets meer. Het wordt bewaard voor compatibiliteit met scripts.

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

### -Offset

Hiermee wordt het aantal bytes dat moet worden overgeslagen, opgenomen in de hexadecimale uitvoer.

Deze para meter is geïntroduceerd in Power shell 6,2.

```yaml
Type: System.Int64
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: 0
Accept pipeline input: False
Accept wildcard characters: False
```

### -Aantal

Hiermee wordt het aantal bytes aangegeven dat moet worden meegenomen in de hexadecimale uitvoer.

Deze para meter is geïntroduceerd in Power shell 6,2.

```yaml
Type: System.Int64
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: Int64.MaxValue
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

De meest rechtse kolom van uitvoer probeert de bytes weer te geven als ASCII-tekens:

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
