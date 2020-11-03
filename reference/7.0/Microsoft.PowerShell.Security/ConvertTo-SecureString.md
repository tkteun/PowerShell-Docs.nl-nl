---
external help file: Microsoft.PowerShell.Security.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Security
ms.date: 10/22/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.security/convertto-securestring?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: ConvertTo-SecureString
ms.openlocfilehash: c98f140a40046d1ba3e48e7063096394e358bea5
ms.sourcegitcommit: df80c558e9a4b89c9798f084bd04012ece15155c
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/23/2020
ms.locfileid: "93253209"
---
# ConvertTo-SecureString

## SAMENVATTING
Converteert tekst zonder opmaak of versleutelde teken reeksen naar beveiligde teken reeksen.

## SYNTAXIS

### Beveiligd (standaard)

```
ConvertTo-SecureString [-String] <String> [[-SecureKey] <SecureString>] [<CommonParameters>]
```

### PlainText

```
ConvertTo-SecureString [-String] <String> [-AsPlainText] [-Force] [<CommonParameters>]
```

### Openen

```
ConvertTo-SecureString [-String] <String> [-Key <Byte[]>] [<CommonParameters>]
```

## BESCHRIJVING

Met de `ConvertTo-SecureString` cmdlet worden versleutelde standaard teken reeksen omgezet in beveiligde teken reeksen. Het kan ook tekst zonder opmaak converteren naar beveiligde teken reeksen. Deze wordt gebruikt met `ConvertFrom-SecureString` en `Read-Host` . De beveiligde teken reeks die door de cmdlet wordt gemaakt, kan worden gebruikt met cmdlets of functies die een para meter van het type **SecureString** vereisen. De beveiligde teken reeks kan worden omgezet naar een versleutelde, standaard teken reeks met behulp van de `ConvertFrom-SecureString` cmdlet. Hierdoor kan het worden opgeslagen in een bestand voor later gebruik.

Als de standaard teken reeks die wordt geconverteerd, is versleuteld met `ConvertFrom-SecureString` behulp van een opgegeven sleutel, moet diezelfde sleutel worden opgegeven als de waarde van de **sleutel** -of **SecureKey** -para meter van de `ConvertTo-SecureString` cmdlet.

> [!NOTE]
> Houd er rekening mee dat de inhoud van een SecureString per [DotNet](/dotnet/api/system.security.securestring#remarks)niet wordt versleuteld op niet-Windows-systemen.

## VOORBEELDEN

### Voor beeld 1: een beveiligde teken reeks converteren naar een versleutelde teken reeks

In dit voor beeld ziet u hoe u een veilige teken reeks maakt op basis van gebruikers invoer, de beveiligde teken reeks converteert naar een versleutelde standaard teken reeks en de versleutelde standaard teken reeks vervolgens weer converteert naar een veilige teken reeks.

```powershell
PS C:\> $Secure = Read-Host -AsSecureString
PS C:\> $Secure
System.Security.SecureString
PS C:\> $Encrypted = ConvertFrom-SecureString -SecureString $Secure
PS C:\> $Encrypted
01000000d08c9ddf0115d1118c7a00c04fc297eb010000001a114d45b8dd3f4aa11ad7c0abdae98000000000
02000000000003660000a8000000100000005df63cea84bfb7d70bd6842e7efa79820000000004800000a000
000010000000f10cd0f4a99a8d5814d94e0687d7430b100000008bf11f1960158405b2779613e9352c6d1400
0000e6b7bf46a9d485ff211b9b2a2df3bd6eb67aae41
PS C:\> $Secure2 = ConvertTo-SecureString -String $Encrypted
PS C:\> $Secure2
System.Security.SecureString
```

De eerste opdracht maakt gebruik van de para meter **AsSecureString** van de `Read-Host` cmdlet om een beveiligde teken reeks te maken. Nadat u de opdracht hebt ingevoerd, worden de door u getypte tekens omgezet in een beveiligde teken reeks en vervolgens opgeslagen in de `$Secure` variabele.

Met de tweede opdracht wordt de inhoud van de variabele weer gegeven `$Secure` . Omdat de `$Secure` variabele een beveiligde teken reeks bevat, wordt in Power shell alleen het type **System. Security. SecureString** weer gegeven.

De derde opdracht gebruikt de `ConvertFrom-SecureString` cmdlet om de beveiligde teken reeks in de `$Secure` variabele te converteren naar een versleutelde standaard teken reeks. Het resultaat wordt opgeslagen in de `$Encrypted` variabele.

Met de vierde opdracht wordt de versleutelde teken reeks weer gegeven in de waarde van de `$Encrypted` variabele.

De vijfde opdracht gebruikt de `ConvertTo-SecureString` cmdlet om de versleutelde standaard teken reeks in de `$Encrypted` variabele terug te converteren naar een veilige teken reeks. Het resultaat wordt opgeslagen in de `$Secure2` variabele.
Met de zesde opdracht wordt de waarde van de variabele weer gegeven `$Secure2` . Het type SecureString geeft aan dat de opdracht is geslaagd.

### Voor beeld 2: een veilige teken reeks maken op basis van een versleutelde teken reeks in een bestand

In dit voor beeld ziet u hoe u een veilige teken reeks maakt van een versleutelde standaard teken reeks die in een bestand wordt opgeslagen.

```powershell
$Secure = Read-Host -AsSecureString
$Encrypted = ConvertFrom-SecureString -SecureString $Secure -Key (1..16)
$Encrypted | Set-Content Encrypted.txt
$Secure2 = Get-Content Encrypted.txt | ConvertTo-SecureString -Key (1..16)
```

De eerste opdracht maakt gebruik van de para meter **AsSecureString** van de `Read-Host` cmdlet om een beveiligde teken reeks te maken. Nadat u de opdracht hebt ingevoerd, worden de door u getypte tekens omgezet in een beveiligde teken reeks en vervolgens opgeslagen in de `$Secure` variabele.

Met de tweede opdracht wordt de- `ConvertFrom-SecureString` cmdlet gebruikt om de beveiligde teken reeks in de variabele te converteren `$Secure` naar een versleutelde standaard teken reeks met behulp van de opgegeven sleutel. De inhoud wordt opgeslagen in de `$Encrypted` variabele.

De derde opdracht maakt gebruik van een pijplijn operator ( `|` ) om de waarde van de `$Encrypted` variabele naar de `Set-Content` cmdlet te verzenden, waarmee de waarde in het Encrypted.txt-bestand wordt opgeslagen.

De vierde opdracht gebruikt de `Get-Content` cmdlet om de versleutelde standaard teken reeks in het Encrypted.txt-bestand op te halen. De opdracht maakt gebruik van een pijplijn operator voor het verzenden van de versleutelde teken reeks naar de `ConvertTo-SecureString` cmdlet, die deze converteert naar een beveiligde teken reeks met behulp van de opgegeven sleutel.
De resultaten worden opgeslagen in de `$Secure2` variabele.

### Voor beeld 3: een teken reeks met tekst zonder opmaak converteren naar een veilige teken reeks

Met deze opdracht wordt de teken reeks met tekst zonder opmaak geconverteerd `P@ssW0rD!` naar een beveiligde teken reeks en wordt het resultaat opgeslagen in de `$Secure_String_Pwd` variabele. Als u de para meter **AsPlainText** wilt gebruiken, moet de para meter **Forces** ook worden opgenomen in de opdracht.

```powershell
$Secure_String_Pwd = ConvertTo-SecureString "P@ssW0rD!" -AsPlainText -Force
```

> [!CAUTION]
> Vermijd het gebruik van teken reeksen met tekst zonder opmaak in een script of vanaf de opdracht regel. De tekst zonder opmaak kan worden weer gegeven in gebeurtenis logboeken en logboeken van de opdracht geschiedenis.

## PARAMETERS

### -AsPlainText

Geeft een teken reeks voor onbewerkte tekst aan die moet worden geconverteerd naar een beveiligde teken reeks. Met de beveiligde teken reeks-cmdlets kunt u vertrouwelijke tekst beveiligen. De tekst wordt versleuteld voor privacy en wordt verwijderd uit het computer geheugen nadat deze is gebruikt. Als u deze para meter gebruikt om onbewerkte tekst als invoer op te geven, kan het systeem die invoer niet op deze manier beveiligen. Als u deze para meter wilt gebruiken, moet u ook de para meter **Force** opgeven.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: PlainText
Aliases:

Required: False
Position: 1
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Force

Hiermee wordt bevestigd dat u de implicaties van het gebruik van de para meter **AsPlainText** begrijpt en deze nog steeds wilt gebruiken.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: PlainText
Aliases:

Required: False
Position: 2
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Sleutel

Hiermee geeft u de versleutelings sleutel die wordt gebruikt om de oorspronkelijke beveiligde teken reeks te converteren naar de versleutelde standaard teken reeks. Geldige sleutel lengten zijn 16, 24 en 32 bytes.

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

Hiermee geeft u de versleutelings sleutel die wordt gebruikt om de oorspronkelijke beveiligde teken reeks te converteren naar de versleutelde standaard teken reeks. De sleutel moet worden vermeld in de indeling van een beveiligde teken reeks. De beveiligde teken reeks wordt geconverteerd naar een byte matrix die als sleutel moet worden gebruikt. Geldige veilige sleutel lengten zijn 8, 12 en 16 code punten.

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

### -Teken reeks

Hiermee geeft u de teken reeks die moet worden geconverteerd naar een beveiligde teken reeks.

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### CommonParameters

Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable. Zie [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)voor meer informatie.

## INVOER

### System. String

U kunt een standaard versleutelde teken reeks door sluizen naar `ConvertTo-SecureString` .

## UITVOER

### System. Security. SecureString

`ConvertTo-SecureString` retourneert een **SecureString** -object.

## OPMERKINGEN

Sommige tekens, zoals emoticons, komen overeen met verschillende code punten in de teken reeks die ze bevatten. Vermijd het gebruik van deze tekens omdat deze problemen kunnen veroorzaken en de oorzaak is van het gebruik van een wacht woord.

## GERELATEERDE KOPPELINGEN

[ConvertFrom-SecureString](ConvertFrom-SecureString.md)

[Read-host](../Microsoft.PowerShell.Utility/Read-Host.md)
