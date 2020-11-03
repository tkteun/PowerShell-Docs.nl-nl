---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 5/14/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/remove-itemproperty?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Remove-ItemProperty
ms.openlocfilehash: 2daf4d9dacc0f15ab5347fff4bec831be25d97a6
ms.sourcegitcommit: de63e9481cf8024883060aae61fb02c59c2de662
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/03/2020
ms.locfileid: "93249409"
---
# Remove-ItemProperty

## SAMENVATTING
Hiermee verwijdert u de eigenschap en de waarde ervan uit een item.

## SYNTAXIS

### Pad (standaard)

```
Remove-ItemProperty [-Path] <String[]> [-Name] <String[]> [-Force] [-Filter <String>] [-Include <String[]>]
 [-Exclude <String[]>] [-Credential <PSCredential>] [-InformationAction <ActionPreference>]
 [-InformationVariable <String>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### LiteralPath

```
Remove-ItemProperty -LiteralPath <String[]> [-Name] <String[]> [-Force] [-Filter <String>]
 [-Include <String[]>] [-Exclude <String[]>] [-Credential <PSCredential>]
 [-WhatIf] [-Confirm] [<CommonParameters>]
```

## BESCHRIJVING

`Remove-ItemProperty`Met de cmdlet wordt een eigenschap en de waarde ervan uit een item verwijderd.
U kunt deze gebruiken om register waarden en de opgeslagen gegevens te verwijderen.

## VOORBEELDEN

### Voor beeld 1: een register waarde verwijderen

Met deze opdracht worden de register waarde ' SmpProperty ' en de bijbehorende gegevens verwijderd uit de subsleutel ' SmpApplication ' van de `HKEY_LOCAL_MACHINE\Software` register sleutel.

```powershell
Remove-ItemProperty -Path "HKLM:\Software\SmpApplication" -Name "SmpProperty"
```

Omdat de opdracht wordt verleend vanuit een bestandssysteem station ( `PS C:\>` ), bevat deze het volledig gekwalificeerde pad van de subsleutel "SmpApplication", met inbegrip van het station, `HKLM:` en de sleutel "software".

### Voor beeld 2: een register waarde verwijderen van de HKCU-locatie

Met deze opdrachten worden de register waarde ' Options ' en de bijbehorende gegevens uit de ' Mijntoep '-subsleutel van HKEY_CURRENT_USER\Software\MyCompany verwijderd.

```
PS C:\> Set-Location HKCU:\Software\MyCompany\MyApp
PS HKCU:\Software\MyCompany\MyApp> Remove-ItemProperty -Path . -Name "Options" -Confirm
```

Met de eerste opdracht wordt de `Set-Location` cmdlet gebruikt om de huidige locatie te wijzigen in de **HKEY_CURRENT_USER** station ( `HKCU:` ) en de `Software\MyCompany\MyApp` subsleutel.

De tweede opdracht wordt gebruikt `Remove-ItemProperty` om de register waarde ' Options ' en de bijbehorende gegevens te verwijderen uit de ' Mijntoep '-subsleutel. Omdat **pad** vereist is, gebruikt de opdracht een punt ( `.` ) om de huidige locatie aan te geven. De **confirm** -para meter vraagt een gebruikers prompt aan voordat de waarde wordt verwijderd.

### Voor beeld 3: een register waarde verwijderen met behulp van de pijp lijn

Met deze opdracht worden de register waarde ' NoOfEmployees ' en de bijbehorende gegevens uit de `HKLM\Software\MyCompany` register sleutel verwijderd.

```powershell
Get-Item -Path HKLM:\Software\MyCompany | Remove-ItemProperty -Name NoOfEmployees
```

De opdracht gebruikt de `Get-Item` cmdlet om een item op te halen dat de register sleutel vertegenwoordigt.
Er wordt een pijplijn operator ( `|` ) gebruikt om het object naar te verzenden `Remove-ItemProperty` .
Vervolgens wordt de para meter **name** van gebruikt `Remove-ItemProperty` om de naam van de register waarde op te geven.

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

Hiermee wordt de cmdlet gedwongen een eigenschap van een object te verwijderen dat niet kan worden gebruikt door de gebruiker.
De implementatie varieert van provider tot provider.
Zie [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md)voor meer informatie.

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

### -Name

Hiermee geeft u de namen van de eigenschappen die moeten worden verwijderd.
Joker tekens zijn toegestaan.

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases: PSProperty

Required: True
Position: 1
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: True
```

### -Path

Hiermee geeft u het pad op van het item waarvan de eigenschappen worden verwijderd.
Joker tekens zijn toegestaan.

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

U kunt een teken reeks die een pad bevat, maar geen letterlijk pad, naar deze cmdlet pipet.

## UITVOER

### Geen

Met deze cmdlet wordt geen uitvoer geretourneerd.

## OPMERKINGEN

- In de register provider van Power shell worden register waarden beschouwd als eigenschappen van een register sleutel of-subsleutel. U kunt de **item Property** -cmdlets gebruiken om deze waarden te beheren.
- `Remove-ItemProperty` is ontworpen om te werken met de gegevens die door elke provider worden weer gegeven. Als u een lijst wilt weer geven van de providers die beschikbaar zijn in uw sessie, typt u `Get-PSProvider` . Zie [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md)voor meer informatie.

## GERELATEERDE KOPPELINGEN

[Get-item](Get-Item.md)

[Wissen-item Property](Clear-ItemProperty.md)

[Kopiëren-item Property](Copy-ItemProperty.md)

[Get-item Property](Get-ItemProperty.md)

[Verplaatsen-item Property](Move-ItemProperty.md)

[Nieuw-item Property](New-ItemProperty.md)

[Verwijderen-item](Remove-Item.md)

[Naam wijzigen-item Property](Rename-ItemProperty.md)

[Set-item Property](Set-ItemProperty.md)

[Set-Location](Set-Location.md)

[about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md)
