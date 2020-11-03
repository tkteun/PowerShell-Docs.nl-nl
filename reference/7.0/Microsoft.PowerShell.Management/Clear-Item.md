---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 5/14/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/clear-item?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Clear-Item
ms.openlocfilehash: 9b7ba6637574f769b1a2c55739c9989736a08c05
ms.sourcegitcommit: de63e9481cf8024883060aae61fb02c59c2de662
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/03/2020
ms.locfileid: "93249743"
---
# Clear-Item

## SAMENVATTING
Hiermee wist u de inhoud van een item, maar verwijdert u het item niet.

## SYNTAXIS

### Pad (standaard)

```
Clear-Item [-Path] <String[]> [-Force] [-Filter <String>] [-Include <String[]>] [-Exclude <String[]>]
 [-Credential <PSCredential>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### LiteralPath

```
Clear-Item -LiteralPath <String[]> [-Force] [-Filter <String>] [-Include <String[]>] [-Exclude <String[]>]
 [-Credential <PSCredential>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

## BESCHRIJVING

Met de cmdlet wordt de `Clear-Item` inhoud van een item gewist, maar wordt het item niet verwijderd.
`Clear-Item`Met de cmdlet kan bijvoorbeeld de waarde van een variabele worden verwijderd, maar wordt de variabele niet verwijderd. De waarde die wordt gebruikt om een verrekend item weer te geven, wordt gedefinieerd door elke Power shell-provider.
Deze cmdlet is vergelijkbaar met `Clear-Content` , maar werkt op aliassen en variabelen, in plaats van bestanden.

## VOORBEELDEN

### Voor beeld 1: de waarde van een variabele wissen

Met deze opdracht wordt de waarde van de variabele met de naam gewist `TestVar1` .
De variabele blijft en is geldig, maar de waarde is ingesteld op `$null` .
De naam van de variabele wordt voorafgegaan door `Variable:` om de Power shell-variabele provider aan te geven.

De alternatieve opdrachten laten zien dat, om hetzelfde resultaat te krijgen, u kunt overschakelen naar het Power shell- `Variable:` station en vervolgens de `Clear-Item` opdracht uitvoeren.

```powershell
Clear-Item Variable:TestVar1
```

```
Set-Location Variable:
PS Variable:\> Clear-Item TestVar1
```

### Voor beeld 2: alle Register vermeldingen wissen

Met deze opdracht worden alle Register vermeldingen in de subsleutel "MyKey" gewist, maar pas u gevraagd om uw intentie te bevestigen.
De subsleutel "MyKey" wordt niet verwijderd of heeft geen invloed op andere register sleutels of-vermeldingen.
U kunt de para meters **include** en **exclude** gebruiken om bepaalde register sleutels te identificeren, maar u kunt ze niet gebruiken om Register vermeldingen te identificeren.

- Als u bepaalde register vermeldingen wilt verwijderen, gebruikt u de `Remove-ItemProperty` cmdlet.
- Als u de waarde van een register vermelding wilt verwijderen, gebruikt u de `Clear-ItemProperty cmdlet` .

```powershell
Clear-Item HKLM:\Software\MyCompany\MyKey -Confirm
```

## PARAMETERS

### -Credential

> [!NOTE]
> Deze para meter wordt niet ondersteund door providers die zijn geïnstalleerd met Power shell.
> Gebruik [invoke-Command](../Microsoft.PowerShell.Core/Invoke-Command.md)om een andere gebruiker te imiteren of uw referenties te verhogen wanneer u deze cmdlet uitvoert.

```yaml
Type: System.Management.Automation.PSCredential
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: Current user
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -Uitsluiten

Hiermee geeft u als een teken reeks matrix een item of items die met deze cmdlet worden uitgesloten in de bewerking. De waarde van deze para meter komt in aanmerking voor de para meter **Path** . Voer een element of patroon van een pad in, zoals `*.txt` . Joker tekens zijn toegestaan. De **exclude** -para meter is alleen effectief wanneer de inhoud van een item wordt opgenomen, zoals `C:\Windows\*` , waarbij het Joker teken de inhoud van de `C:\Windows` map bevat.

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: True
```

### -Filter

Hiermee geeft u een filter op om de para meter **Path** te kwalificeren. De [File System](../Microsoft.PowerShell.Core/About/about_FileSystem_Provider.md) -provider is de enige geïnstalleerde Power shell-provider die het gebruik van filters ondersteunt. U kunt de syntaxis voor de filter taal van het **Bestands systeem** in [about_Wildcards](../Microsoft.PowerShell.Core/About/about_Wildcards.md)vinden.
Filters zijn efficiënter dan andere para meters, omdat deze door de provider worden toegepast wanneer de cmdlet de objecten ophaalt in plaats van dat Power shell de objecten heeft gefilterd nadat ze zijn opgehaald.

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: True
```

### -Force

Geeft aan dat de cmdlet items wist die anders niet kunnen worden gewijzigd, zoals alleen-lezen aliassen.
De cmdlet kan constanten niet wissen.
De implementatie varieert van provider tot provider.
Zie [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md)voor meer informatie.
De cmdlet kan geen beveiligings beperkingen overschrijven, zelfs niet wanneer de para meter **Forces** wordt gebruikt.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### -Include

Hiermee wordt een teken reeks matrix opgegeven, een item of items die met deze cmdlet in de bewerking zijn opgenomen. De waarde van deze para meter komt in aanmerking voor de para meter **Path** . Voer een element of patroon van een pad in, zoals `"*.txt"` . Joker tekens zijn toegestaan. De para meter **include** is alleen effectief wanneer de inhoud van een item wordt opgenomen, zoals `C:\Windows\*` , waarbij het Joker teken de inhoud van de `C:\Windows` map bevat.

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: True
```

### -LiteralPath

Hiermee geeft u een pad naar een of meer locaties. De waarde van **LiteralPath** wordt precies zo gebruikt als deze wordt getypt. Geen tekens worden geïnterpreteerd als joker tekens. Als het pad escape tekens bevat, plaatst u het tussen enkele aanhalings tekens. Enkele aanhalings tekens geven aan dat Power shell geen karakters interpreteert als escape reeksen.

Zie [about_Quoting_Rules](../Microsoft.Powershell.Core/About/about_Quoting_Rules.md)voor meer informatie.

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

Hiermee geeft u het pad op naar de items die worden gewist.
Joker tekens zijn toegestaan.
Deze para meter is vereist, maar het **pad naar** de parameter naam is optioneel.

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

Deze cmdlet biedt ondersteuning voor de algemene para meters: `-Debug` , `-ErrorAction` , `-ErrorVariable` , `-InformationAction` , `-InformationVariable` , `-OutVariable` , `-OutBuffer` , `-PipelineVariable` , `-Verbose` , `-WarningAction` en `-WarningVariable` . Zie [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md)voor meer informatie.

## INVOER

### System. String

U kunt een padtekenreeks door sluizen naar deze cmdlet.

## UITVOER

### Geen

Met deze cmdlet wordt geen uitvoer gegenereerd.

## OPMERKINGEN

- De `Clear-Item` cmdlet wordt alleen ondersteund door verschillende Power shell-providers, met inbegrip van de **alias** -, **omgevings** -, **functie** -, **register** -en **variabelen** providers. Zo kunt u gebruiken `Clear-Item` om de inhoud van items in de naam ruimten van de provider te verwijderen. Als u een lijst wilt weer geven van de providers die beschikbaar zijn in uw sessie, typt u `Get-PsProvider` . Zie [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md)voor meer informatie.
- U kunt niet gebruiken `Clear-Item` om de inhoud van een bestand te verwijderen, omdat de Power shell-bestands provider deze cmdlet niet ondersteunt. Gebruik de om bestanden te wissen `Clear-Content` .

## GERELATEERDE KOPPELINGEN

[Kopie-item](Copy-Item.md)

[Get-item](Get-Item.md)

[Invoke-item](Invoke-Item.md)

[Item verplaatsen](Move-Item.md)

[Nieuw-item](New-Item.md)

[Verwijderen-item](Remove-Item.md)

[Naam wijzigen-item](Rename-Item.md)

[Set-item](Set-Item.md)

[about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md)
