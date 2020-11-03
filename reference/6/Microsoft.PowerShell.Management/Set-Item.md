---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 5/14/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/set-item?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Set-Item
ms.openlocfilehash: 6a6bffbdbf0b619b4ac07391a4b4be368c932777
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/07/2020
ms.locfileid: "93250025"
---
# Set-Item

## SAMENVATTING
Wijzigt de waarde van een item in de waarde die is opgegeven in de opdracht.

## SYNTAXIS

### Pad (standaard)

```
Set-Item [-Path] <String[]> [[-Value] <Object>] [-Force] [-PassThru] [-Filter <String>] [-Include <String[]>]
 [-Exclude <String[]>] [-Credential <PSCredential>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### LiteralPath

```
Set-Item -LiteralPath <String[]> [[-Value] <Object>] [-Force] [-PassThru] [-Filter <String>]
 [-Include <String[]>] [-Exclude <String[]>] [-Credential <PSCredential>]
 [-WhatIf] [-Confirm] [<CommonParameters>]
```

## BESCHRIJVING

`Set-Item`Met de cmdlet wordt de waarde van een item, zoals een variabele of register sleutel, gewijzigd in de waarde die is opgegeven in de opdracht.

## VOORBEELDEN

### Voor beeld 1: een alias maken

Met deze opdracht maakt u een alias van NP voor Klad blok.

```powershell
Set-Item -Path alias:np -Value "c:\windows\notepad.exe"
```

### Voor beeld 2: de waarde van een omgevings variabele wijzigen

Met deze opdracht wordt de waarde van de omgevings variabele UserRole gewijzigd in Administrator.

```powershell
Set-Item -Path env:UserRole -Value "Administrator"
```

### Voor beeld 3: uw prompt functie wijzigen

Met deze opdracht wordt de functie prompt zodanig gewijzigd dat de tijd voor het pad wordt weer gegeven.

```powershell
Set-Item -Path function:prompt -Value {'PS '+ (Get-Date -Format t) + " " + (Get-Location) + '> '}
```

### Voor beeld 4: opties instellen voor de functie vragen

Met deze opdracht worden de opties **AllScope** en **ReadOnly** ingesteld voor de functie prompt.
Met deze opdracht wordt de dynamische para meter **Options** van gebruikt `Set-Item` .
De para meter **Options** is `Set-Item` alleen beschikbaar wanneer u deze met de **alias** of **functie** provider gebruikt.

```powershell
Set-Item -Path function:prompt -Options "AllScope,ReadOnly"
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

Hiermee wordt de cmdlet gedwongen om items in te stellen die anders niet kunnen worden gewijzigd, zoals een alleen-lezen alias of variabelen. De cmdlet kan geen constante aliassen of variabelen wijzigen.
De implementatie varieert van provider tot provider.
Zie [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md)voor meer informatie.
Zelfs met behulp van de para meter *forceren* , kan de cmdlet geen beveiligings beperkingen opheffen.

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

### -PassThru

Geeft een object dat het item vertegenwoordigt in de pijp lijn.
Deze cmdlet genereert standaard geen uitvoer.

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

### -Path

Hiermee geeft u een pad op naar de locatie van de items.
Joker tekens zijn toegestaan.

```yaml
Type: System.String[]
Parameter Sets: Path
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: True
```

### -Waarde

Hiermee geeft u een nieuwe waarde op voor het item.

```yaml
Type: System.Object
Parameter Sets: (All)
Aliases:

Required: False
Position: 1
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
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

Deze cmdlet biedt ondersteuning voor de algemene para meters: `-Debug` , `-ErrorAction` , `-ErrorVariable` , `-InformationAction` , `-InformationVariable` , `-OutVariable` , `-OutBuffer` , `-PipelineVariable` , `-Verbose` , `-WarningAction` en `-WarningVariable` . Zie [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md)voor meer informatie.

## INVOER

### System. object

U kunt een object dat de nieuwe waarde van het item vertegenwoordigt door sluizen naar deze cmdlet.

## UITVOER

### Geen of een object dat het nieuwe of gewijzigde item voor stelt.

Met deze cmdlet wordt een object dat het item vertegenwoordigt, gegenereerd als u de para meter *PassThru* opgeeft.
Anders wordt met deze cmdlet geen uitvoer gegenereerd.

## OPMERKINGEN

- `Set-Item` wordt niet ondersteund door de Power shell-bestandssysteem provider. Als u de waarden van items in het bestands systeem wilt wijzigen, gebruikt u de `Set-Content` cmdlet.
- In de register stations, `HKLM:` en `HKCU:` worden `Set-Item` de gegevens in de (standaard) waarde van een register sleutel gewijzigd.
  - Gebruik de cmdlet en om de namen van register sleutels te maken en te wijzigen `New-Item` `Rename-Item` .
  - Als u de namen en gegevens in register waarden wilt wijzigen, gebruikt u de `New-ItemProperty` `Set-ItemProperty` `Rename-ItemProperty` cmdlets, en.
- `Set-Item` is ontworpen om te werken met de gegevens die door elke provider worden weer gegeven.
  Als u een lijst wilt weer geven van de providers die beschikbaar zijn in uw sessie, typt u `Get-PsProvider` .
  Zie [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md)voor meer informatie.

## GERELATEERDE KOPPELINGEN

[Wissen-item](Clear-Item.md)

[Kopie-item](Copy-Item.md)

[Get-item](Get-Item.md)

[Invoke-item](Invoke-Item.md)

[Item verplaatsen](Move-Item.md)

[Nieuw-item](New-Item.md)

[Verwijderen-item](Remove-Item.md)

[Naam wijzigen-item](Rename-Item.md)

[about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md)
