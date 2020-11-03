---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 10/03/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/rename-item?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Rename-Item
ms.openlocfilehash: f05101f06e4911a797d3342b2b535780badeaefd
ms.sourcegitcommit: de63e9481cf8024883060aae61fb02c59c2de662
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/03/2020
ms.locfileid: "93249724"
---
# Rename-Item

## SAMENVATTING
De naam van een item in een Power shell-provider naam ruimte wordt gewijzigd.

## SYNTAXIS

### ByPath (standaard)

```
Rename-Item [-Path] <String> [-NewName] <String> [-Force] [-PassThru] [-Credential <PSCredential>]
 [-WhatIf] [-Confirm]  [<CommonParameters>]
```

### ByLiteralPath

```
Rename-Item -LiteralPath <String> [-NewName] <String> [-Force] [-PassThru]
 [-Credential <PSCredential>] [-WhatIf] [-Confirm]  [<CommonParameters>]
```

## BESCHRIJVING

`Rename-Item`Met de cmdlet wordt de naam van een opgegeven item gewijzigd. Deze cmdlet heeft geen invloed op de inhoud van het item waarvan de naam wordt gewijzigd.

U kunt niet gebruiken `Rename-Item` om een item te verplaatsen, bijvoorbeeld door een pad op te geven in combi natie met de nieuwe naam. Als u een item wilt verplaatsen en de naam ervan wilt wijzigen, gebruikt u de `Move-Item` cmdlet.

## VOORBEELDEN

### Voor beeld 1: de naam van een bestand wijzigen

Met deze opdracht wordt de naam van het bestand gewijzigd `daily_file.txt` in `monday_file.txt` .

```powershell
Rename-Item -Path "c:\logfiles\daily_file.txt" -NewName "monday_file.txt"
```

### Voor beeld 2: een item een andere naam geven en verplaatsen

U kunt niet gebruiken `Rename-Item` om een item een andere naam te geven en te verplaatsen. U kunt met name geen pad opgeven voor de waarde van de para meter **newname** , tenzij het pad identiek is aan het pad dat is opgegeven in de para meter **Path** . Anders is alleen een nieuwe naam toegestaan.

In dit voor beeld wordt geprobeerd om de naam van het `project.txt` bestand in de huidige map in `old-project.txt` de map te wijzigen `D:\Archive` . Het resultaat is de fout die wordt weer gegeven in de uitvoer.

```powershell
Rename-Item -Path "project.txt" -NewName "d:\archive\old-project.txt"
```

```Output
Rename-Item : can't rename because the target specified represents a path or device name.
At line:1 char:12
+ Rename-Item <<<<  -path project.txt -NewName d:\archive\old-project.txt
+ CategoryInfo          : InvalidArgument: (:) [Rename-Item], PS>  Move-Item -Path "project.txt" -De
stination "d:\archive\old-project.txt"
```

### Voor beeld 3: de naam van een register sleutel wijzigen

In dit voor beeld wordt de naam van een register sleutel gewijzigd van **adverteren** in **marketing**. Wanneer de opdracht is voltooid, wordt de naam van de sleutel gewijzigd, maar de Register vermeldingen in de sleutel blijven onveranderd.

```powershell
Rename-Item -Path "HKLM:\Software\MyCompany\Advertising" -NewName "Marketing"
```

### Voor beeld 4: de naam van meerdere bestanden wijzigen

In dit voor beeld worden de namen `*.txt` van alle bestanden in de huidige map gewijzigd in `*.log` .

```powershell
Get-ChildItem *.txt
```

```Output
    Directory: C:\temp\files

Mode                LastWriteTime         Length Name
----                -------------         ------ ----
-a----        10/3/2019   7:47 AM           2918 Friday.TXT
-a----        10/3/2019   7:46 AM           2918 Monday.Txt
-a----        10/3/2019   7:47 AM           2918 Wednesday.txt
```

```powershell
Get-ChildItem *.txt | Rename-Item -NewName { $_.Name -replace '.txt','.log' }
Get-ChildItem *.log
```

```Output
    Directory: C:\temp\files

Mode                LastWriteTime         Length Name
----                -------------         ------ ----
-a----        10/3/2019   7:47 AM           2918 Friday.log
-a----        10/3/2019   7:46 AM           2918 Monday.log
-a----        10/3/2019   7:47 AM           2918 Wednesday.log
```

Met de `Get-ChildItem` cmdlet worden alle bestanden in de huidige map met een `.txt` bestands extensie opgehaald `Rename-Item` . De waarde van **newname** is een script blok dat wordt uitgevoerd voordat de waarde wordt verzonden naar de para meter **newname** .

In het-script blok `$_` stelt de automatische variabele elk bestands object voor, zoals het via de pijp lijn naar de opdracht wordt geleverd. Het script blok gebruikt de `-replace` operator om de bestands extensie van elk bestand te vervangen door `.log` . U ziet dat het vergelijken met behulp van de `-replace` operator niet hoofdletter gevoelig is.

## PARAMETERS

### -Credential

> [!NOTE]
> Deze para meter wordt niet ondersteund door providers die zijn geïnstalleerd met Power shell. Gebruik [invoke-Command](../Microsoft.PowerShell.Core/Invoke-Command.md)om een andere gebruiker te imiteren of uw referenties te verhogen wanneer u deze cmdlet uitvoert.

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

### -Force

Hiermee wordt de naam van items die niet kunnen worden gewijzigd, zoals verborgen of alleen-lezen bestanden of alleen-lezen-aliassen of-variabelen, door de cmdlet geforceerd. De cmdlet kan geen constante aliassen of variabelen wijzigen.
De implementatie varieert van provider tot provider. Zie [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md)voor meer informatie.

Zelfs met behulp van de para meter **forceren** , kunnen de cmdlet geen beveiligings beperkingen opheffen.

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

### -LiteralPath

Hiermee geeft u een pad naar een of meer locaties. De waarde van **LiteralPath** wordt precies zo gebruikt als deze wordt getypt. Geen tekens worden geïnterpreteerd als joker tekens. Als het pad escape tekens bevat, plaatst u het tussen enkele aanhalings tekens. Enkele aanhalings tekens geven aan dat Power shell geen karakters interpreteert als escape reeksen.

Zie [about_Quoting_Rules](../Microsoft.Powershell.Core/About/about_Quoting_Rules.md)voor meer informatie.

```yaml
Type: System.String
Parameter Sets: ByLiteralPath
Aliases: PSPath, LP

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -NewName

Hiermee geeft u de nieuwe naam van het item. Voer alleen een naam in, geen pad en naam. Als u een pad opgeeft dat verschilt van het pad dat is opgegeven in de para meter **Path** , wordt `Rename-Item` een fout gegenereerd.
Gebruik om een item een andere naam te geven en te verplaatsen `Move-Item` .

U kunt geen joker tekens gebruiken in de waarde van de para meter **newname** . Als u een naam voor meerdere bestanden wilt opgeven, gebruikt u de operator **replace** in een reguliere expressie. Zie [about_Comparison_Operators](../Microsoft.PowerShell.Core/About/about_Comparison_Operators.md)voor meer informatie over de operator vervangen.

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: True
Position: 1
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -PassThru

Retourneert een object dat het item voor de pijp lijn vertegenwoordigt. Deze cmdlet genereert standaard geen uitvoer.

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

Hiermee geeft u het pad op van het item waarvan u de naam wilt wijzigen.

```yaml
Type: System.String
Parameter Sets: ByPath
Aliases:

Required: True
Position: 0
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

Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable. Zie [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md)voor meer informatie.

## INVOER

### System. String

U kunt een teken reeks met een pad naar deze cmdlet door sluizen.

## UITVOER

### Geen of een object dat het hernoemde item vertegenwoordigt.

Met deze cmdlet wordt een object gegenereerd dat het hernoemde item vertegenwoordigt, als u de para meter **PassThru** opgeeft. Anders wordt met deze cmdlet geen uitvoer gegenereerd.

## OPMERKINGEN

`Rename-Item` is ontworpen om te werken met de gegevens die door elke provider worden weer gegeven. Als u een lijst wilt weer geven van de providers die beschikbaar zijn in uw sessie, typt u `Get-PsProvider` . Zie [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md)voor meer informatie.

## GERELATEERDE KOPPELINGEN

[Wissen-item](Clear-Item.md)

[Kopie-item](Copy-Item.md)

[Get-Child item](Get-ChildItem.md)

[Get-item](Get-Item.md)

[Invoke-item](Invoke-Item.md)

[Item verplaatsen](Move-Item.md)

[Nieuw-item](New-Item.md)

[Verwijderen-item](Remove-Item.md)

[Naam wijzigen-item Property](Rename-ItemProperty.md)

[Set-item](Set-Item.md)

[about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md)
