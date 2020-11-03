---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 10/18/2018
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/set-itemproperty?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Set-ItemProperty
ms.openlocfilehash: 969cb181758dc1ac40b9d8fca2c22fa97f87c693
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/07/2020
ms.locfileid: "93250557"
---
# Set-ItemProperty

## SAMENVATTING
Hiermee wordt de waarde van een eigenschap van een item gemaakt of gewijzigd.

## SYNTAXIS

### propertyValuePathSet (standaard)

```
Set-ItemProperty [-Path] <String[]> [-Name] <String> [-Value] <Object> [-PassThru] [-Force] [-Filter <String>]
 [-Include <String[]>] [-Exclude <String[]>] [-Credential <PSCredential>] [-WhatIf] [-Confirm]
 [-UseTransaction] [<CommonParameters>]
```

### propertyPSObjectPathSet

```
Set-ItemProperty [-Path] <String[]> -InputObject <PSObject> [-PassThru] [-Force] [-Filter <String>]
 [-Include <String[]>] [-Exclude <String[]>] [-Credential <PSCredential>] [-WhatIf] [-Confirm]
 [-UseTransaction] [<CommonParameters>]
```

### propertyValueLiteralPathSet

```
Set-ItemProperty -LiteralPath <String[]> [-Name] <String> [-Value] <Object> [-PassThru] [-Force]
 [-Filter <String>] [-Include <String[]>] [-Exclude <String[]>] [-Credential <PSCredential>] [-WhatIf]
 [-Confirm] [-UseTransaction] [<CommonParameters>]
```

### propertyPSObjectLiteralPathSet

```
Set-ItemProperty -LiteralPath <String[]> -InputObject <PSObject> [-PassThru] [-Force] [-Filter <String>]
 [-Include <String[]>] [-Exclude <String[]>] [-Credential <PSCredential>] [-WhatIf] [-Confirm]
 [-UseTransaction] [<CommonParameters>]
```

## BESCHRIJVING

Met de `Set-ItemProperty` cmdlet wordt de waarde van de eigenschap van het opgegeven item gewijzigd. U kunt de-cmdlet gebruiken om de eigenschappen van items te bepalen of te wijzigen. U kunt bijvoorbeeld gebruiken `Set-ItemProperty` om de waarde van de eigenschap **IsReadOnly** van een File-object in te stellen op `$True` .

U kunt ook gebruiken `Set-ItemProperty` om register waarden en-gegevens te maken en te wijzigen.
U kunt bijvoorbeeld een nieuwe register vermelding toevoegen aan een sleutel en de waarde ervan instellen of wijzigen.

## VOORBEELDEN

### Voor beeld 1: een eigenschap van een bestand instellen

Met deze opdracht wordt de waarde van de eigenschap **IsReadOnly** van het bestand ' final.doc ' ingesteld op ' True '. Het **pad** wordt gebruikt om het bestand op te geven, de **naam** op te geven van de naam van de eigenschap en de **waarde** pazrameter om de nieuwe waarde op te geven.

Het bestand is een **System. io. file info** -object en **IsReadOnly** is slechts een van de eigenschappen ervan.
Als u alle eigenschappen wilt weer geven, typt u `Get-Item C:\GroupFiles\final.doc | Get-Member -MemberType Property` .

De `$true` Automatische variabele vertegenwoordigt de waarde ' True '.
Zie [about_Automatic_Variables](../Microsoft.PowerShell.Core/About/about_Automatic_Variables.md)voor meer informatie.

```powershell
Set-ItemProperty -Path C:\GroupFiles\final.doc -Name IsReadOnly -Value $true
```

### Voor beeld 2: een register vermelding en-waarde maken

In dit voor beeld ziet u hoe u kunt gebruiken `Set-ItemProperty` om een nieuwe register vermelding te maken en een waarde aan de vermelding toe te wijzen. Hiermee wordt de vermelding ' NoOfEmployees ' gemaakt in de sleutel ' ContosoCompany ' in de sleutel ' HKLM\Software ' en wordt de waarde ervan ingesteld op 823.

Omdat Register vermeldingen worden beschouwd als eigenschappen van de register sleutels, die items zijn, kunt u gebruiken `Set-ItemProperty` om Register vermeldingen te maken en om hun waarden te bepalen en te wijzigen.

Met de eerste opdracht wordt de register vermelding gemaakt.
Het **pad** wordt gebruikt om het pad van het `HKLM:` station en de sleutel ' Software\MyCompany ' op te geven.
De opdracht gebruikt de **naam** om de naam en **waarde** van het item op te geven om een waarde op te geven.

Met de tweede opdracht wordt de `Get-ItemProperty` cmdlet gebruikt om de nieuwe register vermelding te bekijken. Als u de `Get-Item` `Get-ChildItem` cmdlets of gebruikt, worden de vermeldingen niet weer gegeven omdat ze eigenschappen van een sleutel, geen items of onderliggende items zijn.

Met de derde opdracht wordt de waarde van de vermelding **NoOfEmployees** gewijzigd in 824.

U kunt ook de- `New-ItemProperty` cmdlet gebruiken om de register vermelding en de waarde ervan te maken en vervolgens `Set-ItemProperty` de waarde te wijzigen.

Typ voor meer informatie over het `HKLM:` station `Get-Help Get-PSDrive` .
Als u meer informatie wilt over het gebruik van Power shell voor het beheren van het REGI ster, typt u `Get-Help Registry` .

```powershell
Set-ItemProperty -Path "HKLM:\Software\ContosoCompany" -Name "NoOfEmployees" -Value 823
Get-ItemProperty -Path "HKLM:\Software\ContosoCompany"
```

```output
PSPath        : Microsoft.PowerShell.Core\Registry::HKEY_LOCAL_MACHINE\software\contosocompany
PSParentPath  : Microsoft.PowerShell.Core\Registry::HKEY_LOCAL_MACHINE\software
PSChildName   : contosocompany
PSDrive       : HKLM
PSProvider    : Microsoft.PowerShell.Core\Registry
NoOfLocations : 2
NoOfEmployees : 823

```

```powershell
Set-ItemProperty -Path "HKLM:\Software\ContosoCompany" -Name "NoOfEmployees" -Value 824
Get-ItemProperty -Path "HKLM:\Software\ContosoCompany"
```

```output
PSPath        : Microsoft.PowerShell.Core\Registry::HKEY_LOCAL_MACHINE\software\contosocompany
PSParentPath  : Microsoft.PowerShell.Core\Registry::HKEY_LOCAL_MACHINE\software
PSChildName   : contosocompany
PSDrive       : HKLM
PSProvider    : Microsoft.PowerShell.Core\Registry
NoOfLocations : 2
NoOfEmployees : 824
```

### Voor beeld 3: een item wijzigen met behulp van de pijp lijn

Deze opdrachten laten zien hoe u een pijplijn operator () kunt gebruiken `|` voor het verzenden van een item naar `Set-ItemProperty` .

Het eerste deel van de opdracht wordt gebruikt `Get-ChildItem` om een object op te halen dat het bestand ' Weekly.txt ' vertegenwoordigt.
De opdracht maakt gebruik van een pijplijn operator om het bestands object naar te verzenden `Set-ItemProperty` .
De `Set-ItemProperty` opdracht maakt gebruik van de para meters **name** en **Value** om de eigenschap en de nieuwe waarde op te geven.

Deze opdracht is gelijk aan het gebruik van de para meter **input object** om het object op te geven dat `Get-ChildItem` wordt opgehaald.

```powershell
Get-ChildItem weekly.txt | Set-ItemProperty -Name IsReadOnly -Value $True
```

## PARAMETERS

### -Credential

Hiermee geeft u een gebruikers account op dat is gemachtigd om deze actie uit te voeren.
Standaard is dit de huidige gebruiker.

Typ een gebruikers naam, zoals "gebruiker01" of "Domain01\User01", of voer een **PSCredential** -object in, zoals het account dat is gegenereerd door de `Get-Credential` cmdlet.
Als u een gebruikers naam typt, wordt u gevraagd een wacht woord op te vragen.

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

Hiermee geeft u de items op waarop de cmdlet niet van toepassing is en die alle andere bevat.
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
Accept wildcard characters: False
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

Hiermee wordt de cmdlet gedwongen een eigenschap in te stellen voor items die anders niet toegankelijk zijn voor de gebruiker.
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

Hiermee geeft u alleen de items op waarvoor de cmdlet reageert, waarbij alle andere worden uitgesloten.
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
Accept wildcard characters: False
```

### -Input object

Hiermee geeft u het object op dat de eigenschappen bevat die met deze cmdlet worden gewijzigd.
Voer een variabele in die het object of een opdracht bevat die het object ophaalt.

```yaml
Type: System.Management.Automation.PSObject
Parameter Sets: propertyPSObjectPathSet, propertyPSObjectLiteralPathSet
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### -LiteralPath

Hiermee geeft u een pad van de eigenschap item op.
In tegens telling tot de para meter **Path** wordt de waarde van **LiteralPath** precies zo gebruikt als deze wordt getypt.
Geen tekens worden geïnterpreteerd als joker tekens.
Als het pad escape tekens bevat, plaatst u het tussen enkele aanhalings tekens.
Enkele aanhalings tekens geven aan dat Power shell geen karakters interpreteert als escape reeksen.

```yaml
Type: System.String[]
Parameter Sets: propertyValueLiteralPathSet, propertyPSObjectLiteralPathSet
Aliases: PSPath

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -Name

Hiermee geeft u de naam van de eigenschap op.

```yaml
Type: System.String
Parameter Sets: propertyValuePathSet, propertyValueLiteralPathSet
Aliases: PSProperty

Required: True
Position: 1
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -PassThru

Retourneert een object dat de eigenschap item vertegenwoordigt.
Deze cmdlet genereert standaard geen uitvoer.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Path

Hiermee geeft u het pad op van de items waarvan de eigenschap moet worden gewijzigd.

```yaml
Type: System.String[]
Parameter Sets: propertyValuePathSet, propertyPSObjectPathSet
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -Type

**Type** is een dynamische para meter die de register provider aan de `Set-ItemProperty` cmdlet toevoegt.
Deze para meter werkt alleen in de register stations.

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
Type: RegistryValueKind
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -UseTransaction

Hiermee wordt de opdracht opgenomen in de actieve transactie.
Deze parameter is alleen geldig wanneer een transactie wordt uitgevoerd.
Zie [about_Transactions](../Microsoft.PowerShell.Core/About/about_Transactions.md)voor meer informatie.

```yaml
Type: SwitchParameter
Parameter Sets: (All)
Aliases: usetx

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### -Waarde

Hiermee geeft u de waarde van de eigenschap op.

```yaml
Type: Object
Parameter Sets: propertyValuePathSet, propertyValueLiteralPathSet
Aliases:

Required: True
Position: 2
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -Confirm

Hiermee wordt u gevraagd om bevestiging voordat u de cmdlet uitvoert.

```yaml
Type: SwitchParameter
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
Type: SwitchParameter
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

### System. Management. Automation. PSObject

U kunt objecten door sluizen naar deze cmdlet.

## UITVOER

### Geen, System. Management. Automation. PSCustomObject

Met deze cmdlet wordt een **PSCustomObject** -object gegenereerd dat het item vertegenwoordigt dat is gewijzigd en de nieuwe eigenschaps waarde als u de para meter **PassThru** opgeeft. Anders wordt met deze cmdlet geen uitvoer gegenereerd.

## OPMERKINGEN

`Set-ItemProperty` is ontworpen om te werken met de gegevens die door elke provider worden weer gegeven. Als u een lijst wilt weer geven van de providers die beschikbaar zijn in uw sessie, typt u `Get-PSProvider` . Zie [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md)voor meer informatie.

## GERELATEERDE KOPPELINGEN

[Wissen-item Property](Clear-ItemProperty.md)

[Kopiëren-item Property](Copy-ItemProperty.md)

[Get-item Property](Get-ItemProperty.md)

[Verplaatsen-item Property](Move-ItemProperty.md)

[Nieuw-item Property](New-ItemProperty.md)

[Verwijderen-item Property](Remove-ItemProperty.md)

[Naam wijzigen-item Property](Rename-ItemProperty.md)
