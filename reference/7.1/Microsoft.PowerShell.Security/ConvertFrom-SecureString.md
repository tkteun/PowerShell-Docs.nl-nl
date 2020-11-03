---
external help file: Microsoft.PowerShell.Security.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Security
ms.date: 07/27/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.security/convertfrom-securestring?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: ConvertFrom-SecureString
ms.openlocfilehash: ed9ef1102c1e34670b3cb5664a227f86124812a0
ms.sourcegitcommit: b7ff031a12afd04910aeb98345ebee92f5845b0c
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/28/2020
ms.locfileid: "93251683"
---
# ConvertFrom-SecureString

## SAMENVATTING
Converteert een beveiligde teken reeks naar een versleutelde standaard teken reeks.

## SYNTAXIS

### Beveiligd (standaard)

```
ConvertFrom-SecureString [-SecureString] <SecureString> [[-SecureKey] <SecureString>] [<CommonParameters>]
```

### AsPlainText

```
ConvertFrom-SecureString [-SecureString] <SecureString> [-AsPlainText] [<CommonParameters>]
```

### Openen

```
ConvertFrom-SecureString [-SecureString] <SecureString> [-Key <Byte[]>] [<CommonParameters>]
```

## BESCHRIJVING

Met de cmdlet **ConvertFrom-SecureString** wordt een beveiligde teken reeks ( **System. Security. SecureString** ) geconverteerd naar een versleutelde standaard teken reeks ( **System. String** ). In tegens telling tot een beveiligde teken reeks kan een gecodeerde standaard teken reeks worden opgeslagen in een bestand voor later gebruik. De versleutelde standaard teken reeks kan worden teruggeconverteerd naar de beveiligde teken reeks indeling met behulp van de- `ConvertTo-SecureString` cmdlet.

Als een versleutelings sleutel is opgegeven met behulp van de **sleutel** -of **SecureKey** para meters, wordt het versleutelings ALGORITME voor Advanced Encryption Standard (AES) gebruikt. De opgegeven sleutel moet een lengte hebben van 128, 192 of 256 bits, omdat dit de sleutel lengtes zijn die worden ondersteund door de AES-versleutelings algoritme. Als er geen sleutel is opgegeven, wordt de Windows Data Protection API (DPAPI) gebruikt om de standaard teken reeks representatie te versleutelen.

> [!NOTE]
> Houd er rekening mee dat de inhoud van een SecureString per [DotNet](/dotnet/api/system.security.securestring?view=netcore-2.1#remarks)niet wordt versleuteld op niet-Windows-systemen.

## VOORBEELDEN

### Voor beeld 1: een veilige teken reeks maken

```powershell
$SecureString = Read-Host -AsSecureString
```

Met deze opdracht maakt u een beveiligde teken reeks van tekens die u typt bij de opdracht prompt. Nadat u de opdracht hebt ingevoerd, typt u de teken reeks die u wilt opslaan als een veilige teken reeks. Er wordt een asterisk ( `*` ) weer gegeven voor elk teken dat u typt.

### Voor beeld 2: een beveiligde teken reeks converteren naar een versleutelde standaard teken reeks

```powershell
$StandardString = ConvertFrom-SecureString $SecureString
```

Met deze opdracht wordt de beveiligde teken reeks in de `$SecureString` variabele geconverteerd naar een versleutelde standaard teken reeks. De resulterende versleutelde standaard teken reeks wordt opgeslagen in de `$StandardString` variabele.

### Voor beeld 3: een beveiligde teken reeks converteren naar een versleutelde standaard teken reeks met een 192-bits sleutel

```powershell
$Key = (3,4,2,3,56,34,254,222,1,1,2,23,42,54,33,233,1,34,2,7,6,5,35,43)
$StandardString = ConvertFrom-SecureString $SecureString -Key $Key
```

Deze opdrachten gebruiken het Advanced Encryption Standard (AES)-algoritme voor het converteren van de beveiligde teken reeks die is opgeslagen in de `$SecureString` variabele naar een versleutelde standaard teken reeks met een 192-bits sleutel. De resulterende versleutelde standaard teken reeks wordt opgeslagen in de `$StandardString` variabele.

Met de eerste opdracht wordt een sleutel in de `$Key` variabele opgeslagen. De sleutel is een matrix van 24 decimale cijfers, die elk kleiner dan 256 moeten zijn om te passen binnen één niet-ondertekende byte.

Omdat elk decimaal getal bestaat uit één byte (8 bits), heeft de sleutel 24 cijfers voor een totaal van 192 bits (8 x 24). Dit is een geldige sleutel lengte voor het AES-algoritme.

Met de tweede opdracht wordt de sleutel in de `$Key` variabele gebruikt om de beveiligde teken reeks om te zetten in een versleutelde standaard teken reeks.

### Voor beeld 4: een beveiligde teken reeks rechtstreeks naar een teken reeks met lees bare tekst converteren

```powershell
$secureString = ConvertTo-SecureString -String 'Example' -AsPlainText
$secureString # 'System.Security.SecureString'
ConvertFrom-SecureString -SecureString $secureString -AsPlainText # 'Example'
```

## PARAMETERS

### -AsPlainText

Als deze instelling is ingesteld, `ConvertFrom-SecureString` worden beveiligde teken reeksen geconverteerd naar de ontsleutelde teken reeks als uitvoer.

Deze para meter is toegevoegd aan Power shell 7,0.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: AsPlainText
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Sleutel

Hiermee geeft u de versleutelings sleutel als een byte matrix.

```yaml
Type: System.Byte[]
Parameter Sets: Open
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -SecureKey

Hiermee geeft u de versleutelings sleutel als een beveiligde teken reeks. De waarde van de beveiligde teken reeks wordt geconverteerd naar een byte matrix voordat deze wordt gebruikt als de sleutel.

```yaml
Type: System.Security.SecureString
Parameter Sets: Secure
Aliases:

Required: False
Position: 1
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -SecureString

Hiermee geeft u de beveiligde teken reeks op die moet worden geconverteerd naar een versleutelde standaard teken reeks.

```yaml
Type: System.Security.SecureString
Parameter Sets: (All)
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### CommonParameters

Deze cmdlet biedt ondersteuning voor de algemene para meters: `-Debug` , `-ErrorAction` , `-ErrorVariable` , `-InformationAction` , `-InformationVariable` , `-OutVariable` , `-OutBuffer` , `-PipelineVariable` , `-Verbose` , `-WarningAction` en `-WarningVariable` .
Zie [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)voor meer informatie.

## INVOER

### System. Security. SecureString

U kunt een **SecureString** -object door sluizen naar ConvertFrom-SecureString.

## UITVOER

### System. String

ConvertFrom-SecureString retourneert een standaard teken reeks object.

## OPMERKINGEN

- Gebruik de para meter **AsSecureString** van de cmdlet om een beveiligde teken reeks te maken van tekens die worden getypt bij de opdracht prompt `Read-Host` .
- Wanneer u de para meters **Key** of **SecureKey** gebruikt om een sleutel op te geven, moet de sleutel lengte juist zijn. Een sleutel van 128 bits kan bijvoorbeeld worden opgegeven als een byte matrix van 16 decimalen.
  Op dezelfde manier komen 192 bits-en 256-bits sleutels overeen met een byte matrix van respectievelijk 24 en 32 decimale cijfers.
- Sommige tekens, zoals emoticons, komen overeen met verschillende code punten in de teken reeks die ze bevatten. Vermijd het gebruik van deze tekens omdat deze problemen kunnen veroorzaken en de oorzaak is van het gebruik van een wacht woord.

## GERELATEERDE KOPPELINGEN

[ConvertTo-SecureString](ConvertTo-SecureString.md)

[Read-host](../Microsoft.PowerShell.Utility/Read-Host.md)
