---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 5/14/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/new-itemproperty?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: New-ItemProperty
ms.openlocfilehash: b1ee17e09a85c7f8afd3b41e7f9fb8b8dd5f019e
ms.sourcegitcommit: de63e9481cf8024883060aae61fb02c59c2de662
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/03/2020
ms.locfileid: "93249701"
---
# New-ItemProperty

## SAMENVATTING
Hiermee maakt u een nieuwe eigenschap voor een item en stelt u de waarde ervan in.

## SYNTAXIS

### Pad (standaard)

```
New-ItemProperty [-Path] <String[]> [-Name] <String> [-PropertyType <String>] [-Value <Object>] [-Force]
 [-Filter <String>] [-Include <String[]>] [-Exclude <String[]>] [-Credential <PSCredential>] [-WhatIf]
 [-Confirm] [<CommonParameters>]
```

### LiteralPath

```
New-ItemProperty -LiteralPath <String[]> [-Name] <String> [-PropertyType <String>] [-Value <Object>] [-Force]
 [-Filter <String>] [-Include <String[]>] [-Exclude <String[]>] [-Credential <PSCredential>] [-WhatIf]
 [-Confirm] [<CommonParameters>]
```

## BESCHRIJVING

De `New-ItemProperty` cmdlet maakt een nieuwe eigenschap voor een opgegeven item en stelt de waarde ervan in.
Deze cmdlet wordt doorgaans gebruikt om nieuwe register waarden te maken, omdat register waarden eigenschappen van een register sleutel item zijn.

Met deze cmdlet worden geen eigenschappen aan een object toegevoegd.

- Gebruik de cmdlet om een eigenschap toe te voegen aan een exemplaar van een object `Add-Member` .
- Als u een eigenschap wilt toevoegen aan alle objecten van een bepaald type, wijzigt u het Types.ps1XML-bestand.

## VOORBEELDEN

### Voor beeld 1: een register vermelding toevoegen

Met deze opdracht wordt een nieuwe register vermelding ' NoOfEmployees ' toegevoegd aan de sleutel ' mijn bedrijf ' van de component ' HKLM: \ software '.

Met de eerste opdracht wordt de para meter **Path** gebruikt om het pad van de register sleutel ' mijn bedrijf ' op te geven.
Hierbij wordt de para meter **name** gebruikt om een naam op te geven voor de vermelding en de para meter **waarde** om de waarde op te geven.

Met de tweede opdracht wordt de `Get-ItemProperty` cmdlet gebruikt om de nieuwe register vermelding te bekijken.

```powershell
New-ItemProperty -Path "HKLM:\Software\MyCompany" -Name "NoOfEmployees" -Value 822
Get-ItemProperty "HKLM:\Software\MyCompany"
```

```output
PSPath        : Microsoft.PowerShell.Core\Registry::HKEY_LOCAL_MACHINE\software\mycompany
PSParentPath  : Microsoft.PowerShell.Core\Registry::HKEY_LOCAL_MACHINE\software
PSChildName   : mycompany
PSDrive       : HKLM
PSProvider    : Microsoft.PowerShell.Core\Registry
NoOfLocations : 2
NoOfEmployees : 822
```

### Voor beeld 2: een register vermelding toevoegen aan een sleutel

Met deze opdracht wordt een nieuwe register vermelding toegevoegd aan een register sleutel.
Als u de sleutel wilt opgeven, wordt een pijplijn operator ( `|` ) gebruikt om een object te verzenden dat de sleutel naar vertegenwoordigt `New-ItemProperty` .

Het eerste deel van de opdracht gebruikt de `Get-Item` cmdlet om de register sleutel ' mijn bedrijf ' op te halen.
De pijplijn operator verzendt de resultaten van de opdracht naar `New-ItemProperty` , waarmee de nieuwe register vermelding ("NoOfLocations") en de waarde (3) wordt toegevoegd aan de sleutel "mijn bedrijf".

```powershell
Get-Item -Path "HKLM:\Software\MyCompany" | New-ItemProperty -Name NoOfLocations -Value 3
```

Deze opdracht werkt omdat de functie voor het binden van para meters van Power shell het pad van het object koppelt `RegistryKey` dat `Get-Item` retourneert met de para meter **LiteralPath** van `New-ItemProperty` . Zie [about_Pipelines](../Microsoft.PowerShell.Core/About/about_pipelines.md)voor meer informatie.

### Voor beeld 3: een waarde met meerdere teken reeksen in het REGI ster maken met behulp van een Here-String

In dit voor beeld wordt een waarde met meerdere teken reeksen gemaakt met behulp van een hier-teken reeks.

```powershell
$newValue = New-ItemProperty -Path "HKLM:\SOFTWARE\ContosoCompany\" -Name 'HereString' -PropertyType MultiString -Value @"
This is text which contains newlines
It can also contain "quoted" strings
"@
$newValue.multistring
```

```output
This is text which contains newlines
It can also contain "quoted" strings
```

### Voor beeld 4: een waarde met meerdere teken reeksen in het REGI ster maken met een matrix

In het voor beeld ziet u hoe u een matrix met waarden gebruikt om de waarde te maken `MultiString` .

```powershell
$newValue = New-ItemProperty -Path "HKLM:\SOFTWARE\ContosoCompany\" -Name 'MultiString' -PropertyType MultiString -Value ('a','b','c')
$newValue.multistring[0]
```

```output
a
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

Hiermee wordt de cmdlet gedwongen een eigenschap te maken voor een object dat niet kan worden gebruikt door de gebruiker.
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

Hiermee geeft u een naam op voor de nieuwe eigenschap.
Als de eigenschap een register vermelding is, geeft deze para meter de naam van het item aan.

```yaml
Type: System.String
Parameter Sets: (All)
Aliases: PSProperty

Required: True
Position: 1
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -Path

Hiermee geeft u het pad van het item.
Joker tekens zijn toegestaan.
Met deze para meter wordt het item geïdentificeerd waaraan deze cmdlet de nieuwe eigenschap toevoegt.

```yaml
Type: System.String[]
Parameter Sets: Path
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: True
```

### -Property type

Hiermee geeft u het type eigenschap op dat met deze cmdlet wordt toegevoegd.
De aanvaardbare waarden voor deze parameter zijn:

- **Teken reeks** : Hiermee geeft u een teken reeks met een null-waarde op. Gelijk aan **REG_SZ**.
- **ExpandString** : Hiermee geeft u een teken reeks met een null-waarde eindigen die niet-uitgevouwen verwijzingen bevat naar omgevings variabelen die worden uitgebreid wanneer de waarde wordt opgehaald. Gelijk aan **REG_EXPAND_SZ**.
- **Binary** : Hiermee worden binaire gegevens in een wille keurig formulier opgegeven. Gelijk aan **REG_BINARY**.
- **DWORD** : Hiermee geeft u een 32-bits binair getal op. Gelijk aan **REG_DWORD**.
- Meerdere **teken reeksen** : Hiermee geeft u een matrix van teken reeksen met een null-waarde die is beëindigd door twee null-tekens.
  Gelijk aan **REG_MULTI_SZ**.
- **Qword** : Hiermee geeft u een 64-bits binair getal op. Gelijk aan **REG_QWORD**.
- **Onbekend** : Hiermee wordt een niet-ondersteund gegevens type van het REGI ster aangegeven, zoals **REG_RESOURCE_LIST**.

```yaml
Type: System.String
Parameter Sets: (All)
Aliases: Type

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -Waarde

Geeft de waarde van de eigenschap aan.
Als de eigenschap een register vermelding is, geeft deze para meter de waarde van het item aan.

```yaml
Type: System.Object
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
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

### Geen

U kunt geen invoer van een pipe naar deze cmdlet.

## UITVOER

### System. Management. Automation. PSCustomObject

`New-ItemProperty` retourneert een aangepast object dat de nieuwe eigenschap bevat.

## OPMERKINGEN

`New-ItemProperty` is ontworpen om te werken met de gegevens die door elke provider worden weer gegeven. Als u een lijst wilt weer geven van de providers die beschikbaar zijn in uw sessie, typt u `Get-PSProvider` . Zie [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md)voor meer informatie.

## GERELATEERDE KOPPELINGEN

[Wissen-item Property](Clear-ItemProperty.md)

[Kopiëren-item Property](Copy-ItemProperty.md)

[Get-item Property](Get-ItemProperty.md)

[Verplaatsen-item Property](Move-ItemProperty.md)

[Verwijderen-item Property](Remove-ItemProperty.md)

[Naam wijzigen-item Property](Rename-ItemProperty.md)

[Set-item Property](Set-ItemProperty.md)

[about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md)
