---
external help file: Microsoft.PowerShell.Security.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Security
ms.date: 07/27/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.security/convertfrom-securestring?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: ConvertFrom-SecureString
ms.openlocfilehash: ba360e133800ae0e569643c12b1254a53aaac6ff
ms.sourcegitcommit: 366304d096c1caf52f0e17962f6ed23d20f86e7b
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 04/16/2021
ms.locfileid: "107543741"
---
# ConvertFrom-SecureString

## SAMENVATTING
Converteert een beveiligde tekenreeks naar een versleutelde standaardreeks.

## SYNTAXIS

### Veilig (standaard)

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

De **cmdlet ConvertFrom-SecureString** converteert een beveiligde tekenreeks (**System.Security.SecureString**) naar een versleutelde standaardtekenreeks (**System.String**). In tegenstelling tot een beveiligde tekenreeks kan een versleutelde standaardreeks worden opgeslagen in een bestand voor later gebruik. De versleutelde standaardreeks kan met behulp van de cmdlet worden geconverteerd naar de beveiligde `ConvertTo-SecureString` tekenreeksindeling.

Als een versleutelingssleutel wordt opgegeven met behulp van de parameters **Sleutel** of **SecureKey,** wordt het AES Advanced Encryption Standard-versleutelingsalgoritme gebruikt. De opgegeven sleutel moet een lengte van 128, 192 of 256 bits hebben, omdat dit de sleutellengten zijn die worden ondersteund door het AES-versleutelingsalgoritme. Als er geen sleutel is opgegeven, wordt de Windows Data Protection API (DPAPI) gebruikt om de standaardreeksweergave te versleutelen.

> [!NOTE]
> Houd er rekening mee dat de inhoud van een SecureString per [DotNet](/dotnet/api/system.security.securestring?view=netcore-2.1#remarks)niet is versleuteld op niet-Windows-systemen.

## VOORBEELDEN

### Voorbeeld 1: Een beveiligde tekenreeks maken

```powershell
$SecureString = Read-Host -AsSecureString
```

Met deze opdracht maakt u een beveiligde tekenreeks van tekens die u typt bij de opdrachtprompt. Nadat u de opdracht hebt invoeren, typt u de tekenreeks die u wilt opslaan als een beveiligde tekenreeks. Er wordt een sterretje () weergegeven om elk teken dat u typt `*` weer te geven.

### Voorbeeld 2: Een beveiligde tekenreeks converteren naar een versleutelde standaardreeks

```powershell
$StandardString = ConvertFrom-SecureString $SecureString
```

Met deze opdracht wordt de beveiligde tekenreeks in de `$SecureString` variabele ge converteerd naar een versleutelde standaardreeks. De resulterende versleutelde standaardreeks wordt opgeslagen in de `$StandardString` variabele .

### Voorbeeld 3: Een beveiligde tekenreeks converteren naar een versleutelde standaardreeks met een 192-bits sleutel

```powershell
$Key = (3,4,2,3,56,34,254,222,1,1,2,23,42,54,33,233,1,34,2,7,6,5,35,43)
$StandardString = ConvertFrom-SecureString $SecureString -Key $Key
```

Deze opdrachten gebruiken het AES-algoritme (Advanced Encryption Standard) om de beveiligde tekenreeks die is opgeslagen in de variabele te converteren naar een versleutelde standaardreeks met een `$SecureString` 192-bits sleutel. De resulterende versleutelde standaardreeks wordt opgeslagen in de `$StandardString` variabele .

De eerste opdracht slaat een sleutel op in de `$Key` variabele . De sleutel is een matrix van 24 decimale cijfers, die elk minder dan 256 moeten zijn om binnen één niet-ondertekende byte te passen.

Omdat elk decimaal getal één byte (8 bits) vertegenwoordigt, heeft de sleutel 24 cijfers voor een totaal van 192 bits (8 x 24). Dit is een geldige sleutellengte voor het AES-algoritme.

De tweede opdracht maakt gebruik van de sleutel in de `$Key` variabele om de beveiligde tekenreeks te converteren naar een versleutelde standaardreeks.

### Voorbeeld 4: Een beveiligde tekenreeks rechtstreeks converteren naar een tekst zonder tekst

```powershell
$secureString = ConvertTo-SecureString -String 'Example' -AsPlainText
$secureString # 'System.Security.SecureString'
ConvertFrom-SecureString -SecureString $secureString -AsPlainText # 'Example'
```

## PARAMETERS

### -AsPlainText

Wanneer deze is ingesteld, `ConvertFrom-SecureString` converteert beveiligde tekenreeksen naar de ontsleutelde tekst zonder tekst als uitvoer.

Deze parameter is toegevoegd in PowerShell 7.0.

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

### -Key

Hiermee geeft u de versleutelingssleutel op als een bytematrix.

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

Hiermee geeft u de versleutelingssleutel als een beveiligde tekenreeks. De waarde van de beveiligde tekenreeks wordt geconverteerd naar een bytematrice voordat deze als sleutel wordt gebruikt.

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

Hiermee geeft u de beveiligde tekenreeks om te converteren naar een versleutelde standaardreeks.

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

Deze cmdlet ondersteunt de algemene parameters: `-Debug` , , , , , , , , `-ErrorAction` , , en `-ErrorVariable` `-InformationAction` `-InformationVariable` `-OutVariable` `-OutBuffer` `-PipelineVariable` `-Verbose` `-WarningAction` `-WarningVariable` .
Zie voor meer informatie [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).

## INVOER

### System.Security.SecureString

U kunt een **SecureString-object** doorspijpen naar ConvertFrom-SecureString.

## UITVOER

### System.String

ConvertFrom-SecureString retourneert een standaard-tekenreeksobject.

## OPMERKINGEN

- Als u een beveiligde tekenreeks wilt maken van tekens die zijn getypt bij de opdrachtprompt, gebruikt u de parameter **AsSecureString** van de `Read-Host` cmdlet .
- Wanneer u de parameters **Sleutel** of **SecureKey gebruikt om** een sleutel op te geven, moet de sleutellengte juist zijn. Een sleutel van 128 bits kan bijvoorbeeld worden opgegeven als een bytematrix van 16 decimale cijfers.
  Op dezelfde manier komen 192-bits en 256-bits sleutels overeen met bytematrixen van respectievelijk 24 en 32 decimalen.
- Sommige tekens, zoals emoticons, komen overeen met verschillende codepunten in de tekenreeks die ze bevat. Vermijd het gebruik van deze tekens omdat deze problemen en misvattingen kunnen veroorzaken bij gebruik in een wachtwoord.

## GERELATEERDE KOPPELINGEN

[ConvertTo-SecureString](ConvertTo-SecureString.md)

[Read-Host](../Microsoft.PowerShell.Utility/Read-Host.md)
