---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 01/27/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/get-formatdata?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-FormatData
ms.openlocfilehash: afc6253e112bf44ba4f92b726002003cc8b594fc
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/07/2020
ms.locfileid: "93251102"
---
# Get-FormatData

## SAMENVATTING
Hiermee haalt u de opmaak gegevens op in de huidige sessie.

## SYNTAXIS

```
Get-FormatData [[-TypeName] <String[]>] [-PowerShellVersion <Version>] [<CommonParameters>]
```

## BESCHRIJVING

De `Get-FormatData` cmdlet haalt de indelings gegevens in de huidige sessie op.

De indelings gegevens in de sessie bevatten opmaak gegevens uit `Format.ps1xml` opmaak bestanden, zoals die in de `$PSHOME` map, het format teren van gegevens voor modules die u in de sessie importeert, en het opmaken van gegevens voor opdrachten die u importeert in uw-sessie met behulp van de- `Import-PSSession` cmdlet.

U kunt deze cmdlet gebruiken om de opmaak gegevens te controleren. Vervolgens kunt u de- `Export-FormatData` cmdlet gebruiken om de objecten te serialiseren, converteren naar XML en deze op te slaan in `Format.ps1xml` bestanden.

Zie [about_Format.ps1XML](../Microsoft.PowerShell.Core/About/about_Format.ps1xml.md)voor meer informatie over het format teren van bestanden in Power shell.

## VOORBEELDEN

### Voor beeld 1: alle opmaak gegevens ophalen

In dit voor beeld worden alle opmaak gegevens in de sessie opgehaald.

```powershell
Get-FormatData -PowerShellVersion 5.1
```

> [!IMPORTANT]
> Om ervoor te zorgen dat de volledige informatie over de indeling van het type wordt geretourneerd, moet u altijd de para meter **PowerShellVersion** met de waarde toevoegen `5.1` Wanneer u een lokale aanroep van gebruikt `Get-FormatData` . Als de para meter en waarde worden wegge laten, wordt mogelijk niet alle juiste type gegevens opgehaald.

### Voor beeld 2: opmaak gegevens ophalen op type naam

In dit voor beeld worden de opmaak gegevens items opgehaald waarvan de naam begint met `System.Management.Automation.Cmd` .

```powershell
Get-FormatData -TypeName 'System.Management.Automation.Cmd*' -PowerShellVersion 5.1
```

### Voor beeld 3: een opmaak gegevens object bekijken

In dit voor beeld ziet u hoe u een object met een opmaak gegevens ophaalt en de eigenschappen ervan bekijkt.

```powershell
$F = Get-FormatData -TypeName 'System.Management.Automation.Cmd*' -PowerShellVersion 5.1
$F
```

```Output
TypeName        FormatViewDefinition
--------        --------------------
HelpInfoShort   {help , TableControl}
```

```powershell
$F.FormatViewDefinition[0].control
```

```Output
Headers          : {System.Management.Automation.TableControlColumnHeader,
                   System.Management.Automation.TableControlColumnHeader,
                   System.Management.Automation.TableControlColumnHeader,
                   System.Management.Automation.TableControlColumnHeader}
Rows             : {System.Management.Automation.TableControlRow}
AutoSize         : False
HideTableHeaders : False
GroupBy          :
OutOfBand        : False
```

```powershell
$F.FormatViewDefinition[0].control.Headers
```

```Output
Label       Alignment Width
-----       --------- -----
CommandType Undefined    15
Name        Undefined    50
Version     Undefined    10
Source      Undefined     0
```

### Voor beeld 4: opmaak gegevens ophalen en deze exporteren

In dit voor beeld ziet u hoe u `Get-FormatData` `Export-FormatData` de opmaak gegevens die door een module worden toegevoegd, kunt gebruiken en exporteren.

```powershell
$A = Get-FormatData -PowerShellVersion 5.1
Import-Module bitstransfer
$B = Get-FormatData -PowerShellVersion 5.1
Compare-Object $A $B
```

```Output
InputObject                                                SideIndicator
-----------                                                -------------
Microsoft.BackgroundIntelligentTransfer.Management.BitsJob =>
```

```powershell
Get-FormatData *bits* | Export-FormatData -FilePath c:\test\bits.format.ps1xml
Get-Content c:\test\bits.format.ps1xml
```

```Output
<?xml version="1.0" encoding="utf-8"?><Configuration><ViewDefinitions>
<View><Name>Microsoft.BackgroundIntelligentTransfer.Management.BitsJob</Name>
...
```

De eerste vier opdrachten gebruiken de `Get-FormatData` -, `Import-Module` -en- `Compare-Object` cmdlets om het indelings type te identificeren dat door de **BitsTransfer** -module wordt toegevoegd aan de sessie.

De vijfde opdracht gebruikt de `Get-FormatData` cmdlet om het indelings type op te halen dat door de **BitsTransfer** -module wordt toegevoegd. Er wordt een pijplijn operator ( `|` ) gebruikt om het indelings type object te verzenden naar de `Export-FormatData` cmdlet, waarmee het weer wordt omgezet in XML en wordt opgeslagen in het opgegeven `format.ps1xml` bestand.

Met de laatste opdracht wordt een fragment van de `format.ps1xml` Bestands inhoud weer gegeven.

### Voor beeld 5: opmaak gegevens ophalen op basis van de opgegeven versie van Power shell

In dit voor beeld ziet u hoe u kunt gebruiken `Get-FormatData` om gegevens op te halen voor een opgegeven **TypeName** en Power shell-versie.

```powershell
Get-FormatData -TypeName 'Microsoft.Powershell.Utility.FileHash' -PowerShellVersion $PSVersionTable.PSVersion

TypeNames                               FormatViewDefinition
---------                               --------------------
{Microsoft.Powershell.Utility.FileHash} {Microsoft.Powershell.Utility.FileHash}
```

## PARAMETERS

### -PowerShellVersion

Geef de versie van Power shell op die met deze cmdlet wordt opgehaald voor de indelings gegevens. Voer een getal in van twee cijfers, gescheiden door een punt.

Deze para meter is toegevoegd aan Power shell 5,1 om de compatibiliteit te verbeteren wanneer externe computers met oudere versies van Power shell worden uitgevoerd.

```yaml
Type: System.Version
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -TypeName

Hiermee geeft u de type namen op die met deze cmdlet worden opgehaald voor de indelings gegevens.
Voer de type namen in.
Joker tekens zijn toegestaan.

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: True
```

### CommonParameters

Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable. Zie [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)voor meer informatie.

## INVOER

### Geen

U kunt geen invoer van een pipe naar deze cmdlet.

## UITVOER

### System. Management. Automation. ExtendedTypeDefinition

## OPMERKINGEN

## GERELATEERDE KOPPELINGEN

[Exporteren-FormatData](Export-FormatData.md)

[Update-FormatData](Update-FormatData.md)
