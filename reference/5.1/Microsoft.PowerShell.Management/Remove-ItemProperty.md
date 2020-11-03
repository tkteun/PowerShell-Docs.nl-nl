---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 10/18/2018
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/remove-itemproperty?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Remove-ItemProperty
ms.openlocfilehash: 9ae9c0e7c17a6a63da5487cce138ddce129b975b
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/07/2020
ms.locfileid: "93250580"
---
# Remove-ItemProperty

## SAMENVATTING
Hiermee verwijdert u de eigenschap en de waarde ervan uit een item.

## SYNTAXIS

### Pad (standaard)

```
Remove-ItemProperty [-Path] <String[]> [-Name] <String[]> [-Force] [-Filter <String>] [-Include <String[]>]
 [-Exclude <String[]>] [-Credential <PSCredential>] [-WhatIf] [-Confirm] [-UseTransaction] [<CommonParameters>]
```

### LiteralPath

```
Remove-ItemProperty -LiteralPath <String[]> [-Name] <String[]> [-Force] [-Filter <String>]
 [-Include <String[]>] [-Exclude <String[]>] [-Credential <PSCredential>] [-WhatIf] [-Confirm]
 [-UseTransaction] [<CommonParameters>]
```

## BESCHRIJVING

`Remove-ItemProperty`Met de cmdlet wordt een eigenschap en de waarde ervan uit een item verwijderd.
U kunt deze gebruiken om register waarden en de opgeslagen gegevens te verwijderen.

## VOORBEELDEN

### Voor beeld 1: een register waarde verwijderen

Met deze opdracht worden de register waarde ' SmpProperty ' en de bijbehorende gegevens verwijderd uit de subsleutel ' SmpApplication ' van de register sleutel ' HKEY_LOCAL_MACHINE\Software '.

Omdat de opdracht wordt verleend vanuit een bestandssysteem station ( `PS C:\>` ), bevat deze het volledig gekwalificeerde pad van de subsleutel "SmpApplication", met inbegrip van het station, `HKLM:` en de sleutel "software".

De para meter **name** wordt gebruikt om de register waarde te identificeren die wordt verwijderd.

```powershell
Remove-ItemProperty -Path "HKLM:\Software\SmpApplication" -Name "SmpProperty"
```

### Voor beeld 2: een register waarde verwijderen van de HKCU-locatie

Met deze opdrachten worden de register waarde ' Options ' en de bijbehorende gegevens uit de ' Mijntoep '-subsleutel van HKEY_CURRENT_USER\Software\MyCompany verwijderd.

De eerste opdracht gebruikt de `Set-Location` cmdlet om de huidige locatie te wijzigen naar de **HKEY_CURRENT_USER** station ( `HKCU:` ) en de subsleutel ' Software\MyCompany\MyApp '.

De tweede opdracht wordt gebruikt `Remove-ItemProperty` om de register waarde ' Options ' en de bijbehorende gegevens te verwijderen uit de ' Mijntoep '-subsleutel.
Omdat **pad** vereist is, gebruikt de opdracht een punt ('. ') om de huidige locatie aan te geven.
De **naam** wordt gebruikt om op te geven welke register waarde moet worden verwijderd.
De para meter **confirm** wordt gebruikt voor het aanvragen van een gebruikers prompt voordat de waarde wordt verwijderd.

```
PS C:\> Set-Location HKCU:\Software\MyCompany\MyApp
PS HKCU:\Software\MyCompany\MyApp> Remove-ItemProperty -Path . -Name "Options" -Confirm
```

### Voor beeld 3: een register waarde verwijderen met behulp van de pijp lijn

Met deze opdracht worden de register waarde ' NoOfEmployees ' en de bijbehorende gegevens verwijderd uit de register sleutel ' HKLM\Software\MyCompany '.

De opdracht gebruikt de `Get-Item` cmdlet om een item op te halen dat de register sleutel vertegenwoordigt.
Er wordt een pijplijn operator ( `|` ) gebruikt om het object naar te verzenden `Remove-ItemProperty` .
Vervolgens wordt de para meter **name** van gebruikt `Remove-ItemProperty` om de naam van de register waarde op te geven.

```powershell
Get-Item -Path HKLM:\Software\MyCompany | Remove-ItemProperty -Name NoOfEmployees
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

Hiermee geeft u de items die met deze cmdlet worden wegge laten.
De waarde van deze para meter komt in aanmerking voor de para meter **Path** .
Voer een element of patroon van een pad in, zoals *. txt.
Joker tekens zijn toegestaan.

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

Hiermee geeft u een filter op in de indeling of taal van de provider.
De waarde van deze para meter komt in aanmerking voor de para meter **Path** .

De syntaxis van het filter, inclusief het gebruik van joker tekens, is afhankelijk van de provider.
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

Hiermee wordt een teken reeks matrix opgegeven, een item of items die met deze cmdlet in de bewerking zijn opgenomen.
De waarde van deze para meter komt in aanmerking voor de para meter **Path** .
Voer een element of patroon van een pad in, zoals *. txt.
Joker tekens zijn toegestaan.

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

Hiermee geeft u het pad op naar de huidige locatie van de eigenschap.
In tegens telling tot de para meter **Path** wordt de waarde van **LiteralPath** precies zo gebruikt als deze wordt getypt.
Geen tekens worden geïnterpreteerd als joker tekens.
Als het pad escape tekens bevat, plaatst u het tussen enkele aanhalings tekens.
Enkele aanhalings tekens geven aan dat Power shell geen karakters interpreteert als escape reeksen.

```yaml
Type: System.String[]
Parameter Sets: LiteralPath
Aliases: PSPath

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

### -UseTransaction

Hiermee wordt de opdracht opgenomen in de actieve transactie.
Deze parameter is alleen geldig wanneer een transactie wordt uitgevoerd.
Zie about_Transactions voor meer informatie.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: usetx

Required: False
Position: Named
Default value: False
Accept pipeline input: False
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

### System. String

U kunt een teken reeks die een pad bevat, maar geen letterlijk pad, naar deze cmdlet pipet.

## UITVOER

### Geen

Met deze cmdlet wordt geen uitvoer geretourneerd.

## OPMERKINGEN

In de register provider van Power shell worden register waarden beschouwd als eigenschappen van een register sleutel of-subsleutel. U kunt de **item Property** -cmdlets gebruiken om deze waarden te beheren.

`Remove-ItemProperty` is ontworpen om te werken met de gegevens die door elke provider worden weer gegeven. Als u een lijst wilt weer geven van de providers die beschikbaar zijn in uw sessie, typt u `Get-PSProvider` . Zie about_Providers voor meer informatie.

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

[about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md)
