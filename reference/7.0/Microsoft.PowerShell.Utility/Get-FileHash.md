---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 05/16/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/get-filehash?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-FileHash
ms.openlocfilehash: 6b6b0bdfe635ba0d11c4694efa8af6c23d9acdcd
ms.sourcegitcommit: de63e9481cf8024883060aae61fb02c59c2de662
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/03/2020
ms.locfileid: "93249658"
---
# Get-FileHash

## SAMENVATTING
Hiermee wordt de hash-waarde voor een bestand berekend met behulp van een opgegeven hash-algoritme.

## SYNTAXIS

### Pad (standaard)

```
Get-FileHash [-Path] <String[]> [[-Algorithm] <String>] [<CommonParameters>]
```

### LiteralPath

```
Get-FileHash [-LiteralPath] <String[]> [[-Algorithm] <String>] [<CommonParameters>]
```

### StreamParameterSet

```
Get-FileHash [-InputStream] <Stream> [[-Algorithm] <String>] [<CommonParameters>]
```

## BESCHRIJVING

De `Get-FileHash` cmdlet berekent de hash-waarde voor een bestand met behulp van een opgegeven hash-algoritme.
Een hash-waarde is een unieke waarde die overeenkomt met de inhoud van het bestand. In plaats van de inhoud van een bestand te identificeren met behulp van de bestands naam, extensie of andere aanduiding, wijst een hash een unieke waarde toe aan de inhoud van een bestand. Bestands namen en extensies kunnen worden gewijzigd zonder de inhoud van het bestand te wijzigen en zonder de hash-waarde te wijzigen. De inhoud van het bestand kan ook worden gewijzigd zonder de naam of extensie te wijzigen. Als er echter maar één teken in de inhoud van een bestand wordt gewijzigd, wordt de hash-waarde van het bestand gewijzigd.

Hash-waarden zijn bedoeld om een cryptografische veilige manier te bieden om te controleren of de inhoud van een bestand niet is gewijzigd. Hoewel sommige hash-algoritmen, met inbegrip van MD5 en SHA1, niet meer worden beschouwd als beveiligd tegen aanvallen, is het doel van een beveiligd hash-algoritme het onmogelijk om de inhoud van een bestand te wijzigen, hetzij per ongeluk, hetzij door kwaad aardige of niet-geautoriseerde pogingen, en dezelfde hash-waarde te onderhouden. U kunt ook hash-waarden gebruiken om te bepalen of twee verschillende bestanden precies dezelfde inhoud hebben. Als de hash-waarden van twee bestanden identiek zijn, is de inhoud van de bestanden ook identiek.

De `Get-FileHash` cmdlet maakt standaard gebruik van het sha256-algoritme, hoewel elk hash-algoritme dat wordt ondersteund door het besturings systeem van de doel groep kan worden gebruikt.

## VOORBEELDEN

### Voor beeld 1: de hash-waarde voor een bestand berekenen

In dit voor beeld wordt de `Get-FileHash` cmdlet gebruikt om de hash-waarde voor het bestand te berekenen `/etc/apt/sources.list` . Het hash-algoritme dat wordt gebruikt, is de standaard **sha256**. De uitvoer wordt naar de cmdlet gepiped `Format-List` om de uitvoer als een lijst op te maken.

```powershell
Get-FileHash /etc/apt/sources.list | Format-List
```

```Output
Algorithm : SHA256
Hash      : 3CBCFDDEC145E3382D592266BE193E5BE53443138EE6AB6CA09FF20DF609E268
Path      : /etc/apt/sources.list
```

### Voor beeld 2: de hash-waarde voor een ISO-bestand berekenen

In dit voor beeld worden de `Get-FileHash` cmdlet en de **SHA384** -algoritme gebruikt voor het berekenen van de hash-waarde voor een ISO-bestand dat een beheerder heeft gedownload van Internet. De uitvoer wordt naar de cmdlet gepiped `Format-List` om de uitvoer als een lijst op te maken.

```powershell
Get-FileHash C:\Users\user1\Downloads\Contoso8_1_ENT.iso -Algorithm SHA384 | Format-List
```

```Output
Algorithm : SHA384
Hash      : 20AB1C2EE19FC96A7C66E33917D191A24E3CE9DAC99DB7C786ACCE31E559144FEAFC695C58E508E2EBBC9D3C96F21FA3
Path      : C:\Users\user1\Downloads\Contoso8_1_ENT.iso
```

### Voor beeld 3: de hash-waarde van een stroom berekenen

In dit voor beeld gebruiken we **System .net. webclient** om een pakket te downloaden van de [pagina Power shell-release](https://github.com/PowerShell/PowerShell/releases/tag/v6.2.4). Op de release pagina wordt ook de SHA256-hash van elk pakket bestand gedocumenteerd. We kunnen de gepubliceerde hashwaarde vergelijken met de waarde die wordt berekend met `Get-FileHash` .

```powershell
$wc = [System.Net.WebClient]::new()
$pkgurl = 'https://github.com/PowerShell/PowerShell/releases/download/v6.2.4/powershell_6.2.4-1.debian.9_amd64.deb'
$publishedHash = '8E28E54D601F0751922DE24632C1E716B4684876255CF82304A9B19E89A9CCAC'
$FileHash = Get-FileHash -InputStream ($wc.OpenRead($pkgurl))
$FileHash.Hash -eq $publishedHash
```

```Output
True
```

### Voor beeld 4: de hash van een teken reeks berekenen

Power shell biedt geen cmdlet voor het berekenen van de hash van een teken reeks. U kunt echter een teken reeks naar een stroom schrijven en de para meter **InputStream** van gebruiken `Get-FileHash` om de hash-waarde op te halen.

```powershell
$stringAsStream = [System.IO.MemoryStream]::new()
$writer = [System.IO.StreamWriter]::new($stringAsStream)
$writer.write("Hello world")
$writer.Flush()
$stringAsStream.Position = 0
Get-FileHash -InputStream $stringAsStream | Select-Object Hash
```

```Output
Hash
----
64EC88CA00B268E5BA1A35678A1B5316D212F4F366B2477232534A8AECA37F3C
```

## PARAMETERS

### -Algoritme

Hiermee geeft u de cryptografische hash-functie op die moet worden gebruikt voor het berekenen van de hashwaarde van de inhoud van het opgegeven bestand of de gespecificeerde stroom. Een cryptografische hash-functie heeft de eigenschap die niet haalbaar is om twee verschillende bestanden met dezelfde hashwaarde te vinden. Hash-functies worden vaak gebruikt in combi natie met digitale hand tekeningen en gegevens integriteit. De aanvaardbare waarden voor deze parameter zijn:

- SHA1
- SHA256
- SHA384
- SHA512
- MD5

Als er geen waarde is opgegeven, of als de para meter wordt wegge laten, is de standaard waarde SHA256.

Om veiligheids redenen moet MD5 en SHA1, die niet meer worden beschouwd als veilig, alleen worden gebruikt voor eenvoudige wijzigings validatie, en mag niet worden gebruikt voor het genereren van hash-waarden voor bestanden die bescherming tegen aanvallen of knoeien vereisen.

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:
Accepted values: SHA1, SHA256, SHA384, SHA512, MD5

Required: False
Position: 1
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -InputStream

Hiermee geeft u de invoer stroom op.

```yaml
Type: System.IO.Stream
Parameter Sets: StreamParameterSet
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -LiteralPath

Hiermee geeft u het pad naar een bestand. In tegens telling tot de para meter **Path** wordt de waarde van de para meter **LiteralPath** exact gebruikt terwijl deze wordt getypt. Er worden geen tekens geïnterpreteerd als joker tekens. Als het pad escape tekens bevat, plaatst u het pad tussen enkele aanhalings tekens. Enkele aanhalings tekens geven Power shell opdracht instructies niet te interpreteren als escape reeksen.

```yaml
Type: System.String[]
Parameter Sets: LiteralPath
Aliases: PSPath, LP

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -Path

Hiermee geeft u het pad naar een of meer bestanden als een matrix. Joker tekens zijn toegestaan.

```yaml
Type: System.String[]
Parameter Sets: Path
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: True
```

### CommonParameters

Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable. Zie [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)voor meer informatie.

## INVOER

### System. String

U kunt een teken reeks door sluizen naar de `Get-FileHash` cmdlet die een pad naar een of meer bestanden bevat.

## UITVOER

### Micro soft. Power shell. Utility. FileHash

`Get-FileHash` retourneert een-object dat het pad naar het opgegeven bestand vertegenwoordigt, de waarde van de berekende hash en de algoritme die wordt gebruikt om de hash te berekenen.

## OPMERKINGEN

## GERELATEERDE KOPPELINGEN

[Format-List](Format-List.md)
