---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 04/27/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/remove-typedata?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Remove-TypeData
ms.openlocfilehash: 23a5241aa2f4b18fc02c3ea1c1a5bb8fb467b430
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/07/2020
ms.locfileid: "93251011"
---
# Remove-TypeData

## Samen vatting
Hiermee verwijdert u uitgebreide typen van de huidige sessie.

## Syntax

### RemoveTypeDataSet (standaard)

```
Remove-TypeData -TypeData <TypeData> [-WhatIf] [-Confirm] [<CommonParameters>]
```

### RemoveTypeSet

```
Remove-TypeData [-TypeName] <String> [-WhatIf] [-Confirm] [<CommonParameters>]
```

### RemoveFileSet

```
Remove-TypeData -Path <String[]> [-WhatIf] [-Confirm] [<CommonParameters>]
```

## BESCHRIJVING

`Remove-TypeData`Met de cmdlet worden uitgebreide type gegevens uit de huidige sessie verwijderd. Deze cmdlet is alleen van invloed op de huidige sessie en sessies die zijn gemaakt in de huidige sessie.

U kunt eigenschappen en methoden toevoegen aan objecten in Power shell door ze te definiëren in `Update-TypeData` opdrachten en `Types.ps1xml` bestanden. `Remove-TypeData` Hiermee verwijdert u de uitgebreide eigenschappen en methoden van de huidige sessie. `Remove-TypeData` verwijdert de bestanden niet `Types.ps1xml` of verwijdert uitgebreide type definities van de `Types.ps1xml` bestanden. `Types.ps1xml`Zie [about_Types.ps1XML](../Microsoft.PowerShell.Core/about/about_Types.ps1xml.md)voor meer informatie over bestanden.

Deze cmdlet is geïntroduceerd in Windows Power Shell 3,0.

## Voorbeelden

### Voor beeld 1: type gegevens verwijderen voor een opgegeven type

In dit voor beeld worden alle type gegevens voor het type **System. matrix** verwijderd uit de sessie, inclusief type gegevens die zijn toegevoegd door een `Types.ps1xml` bestand en dynamische type gegevens die zijn toegevoegd aan de-sessie met behulp van de- `Update-TypeData` cmdlet.

```powershell
Remove-TypeData -TypeName System.Array
```

### Voor beeld 2: een uitgebreide-gegevens type uit een sessie verwijderen

Dit voor beeld toont het effect van het verwijderen van uitgebreide type gegevens uit een sessie. Met de eerste worden `Get-TypeData` uitgebreide type gegevens voor het type **System. datetime** opgehaald. In de uitvoer ziet u dat een **datum/tijd** -eigenschap is toegevoegd aan alle **System. datetime** -objecten in Power shell. De `Get-Date` cmdlet retourneert een **System. datetime** -object. De opdracht gebruikt punt notatie om de waarde van de eigenschap **DateTime** van het object **System. datetime** op te halen dat `Get-Date` retourneert.

```powershell
Get-TypeData System.DateTime
(Get-Date).DateTime
Get-TypeData System.DateTime | Remove-TypeData
(Get-Date).DateTime
```

```Output
TypeName        Members
--------        -------
System.DateTime {[DateTime, System.Management.Automation.Runspaces.ScriptPropertyData]}

Friday, January 20, 2012 9:01:00 PM
```

De volgende `Get-TypeData` cmdlet voor het ophalen van alle uitgebreide type gegevens voor het type **System. datetime** en pijpen die de cmdlet voor het `Remove-TypeData` verwijderen van de gegevens van het uitgebreide type hebben. De laatste `Get-Date` cmdlet toont het effect van het verwijderen van de uitgebreide type gegevens voor het type **System. datetime** . Omdat de eigenschap **System. datetime** niet meer bestaat, retourneert een opdracht om de waarde ervan op te halen niets.

### Voor beeld 3: uitgebreide typen voor modules verwijderen

In dit voor beeld worden alle uitgebreide type gegevens voor module objecten verwijderd. Wanneer u een object pipet op `Remove-TypeData` , `Remove-TypeData` haalt de naam van het object type op en verwijdert alle type gegevens voor alle objecten van dat type.

```powershell
Get-Module | Remove-TypeData
```

### Voor beeld 4: uitgebreide typen verwijderen uit opgegeven modules

In dit voor beeld wordt de para meter **Path** van de `Remove-TypeData` cmdlet gebruikt voor het verwijderen van de uitgebreide typen die zijn gedefinieerd in de `Types.ps1xml` bestanden die worden toegevoegd door de **PSScheduledJob** -en **PSWorkflow** -modules. Deze opdracht is niet van invloed op dynamische type gegevens die worden toegevoegd met behulp van de- `Update-TypeData` cmdlet. De opdracht wordt alleen uitgevoerd als de modules zijn geïmporteerd in de huidige sessie.

```powershell
Remove-TypeData -Path "$PSHOME\Modules\PSScheduledJob", "$PSHOME\Modules\PSWorkflow\PSWorkflow.types.ps1xml"
```

Zie [about_Modules](../Microsoft.PowerShell.Core/About/about_Modules.md)voor meer informatie over modules.

### Voor beeld 5: uitgebreide typen verwijderen uit een externe sessie

In dit voor beeld worden uitgebreide typen verwijderd uit een externe sessie. De opdracht gebruikt de `Invoke-Command` cmdlet voor het verwijderen van uitgebreide type gegevens voor alle CIM-typen in de sessies in de `$S` variabele.

```powershell
Invoke-Command -Session $S {Get-TypeData -TypeName *CIM* | Remove-TypeData}
```

## Parameters

### -Path

Hiermee geeft u een matrix met bestanden op die met deze cmdlet worden verwijderd uit de uitgebreide type gegevens van de sessie. Deze parameter is vereist.

Voer de paden en bestands namen van een of meer `Types.ps1xml` bestanden in. Jokertekens worden niet ondersteund. Als u het pad weglaat, is de standaard locatie de huidige map.

```yaml
Type: System.String[]
Parameter Sets: RemoveFileSet
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -TypeData

Hiermee geeft u de type gegevens op die met deze cmdlet uit de sessie worden verwijderd. Deze parameter is vereist. Voer een variabele in die **TypeData** -objecten ( **System. Management. Automation. Runspaces. TypeData** ) bevat of een opdracht waarmee **TypeData** -objecten, zoals een opdracht, worden opgehaald `Get-TypeData` . U kunt ook **TypeData** -objecten pipeen naar `Remove-TypeData` .

```yaml
Type: System.Management.Automation.Runspaces.TypeData
Parameter Sets: RemoveTypeDataSet
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### -TypeName

Hiermee geeft u de typen op waarvoor met deze cmdlet alle uitgebreide type gegevens worden verwijderd voor. Voor typen in de naam ruimte van het systeem voert u de korte naam in. Anders is de volledige type naam vereist. Jokertekens worden niet ondersteund.

U kunt typen van het type sluizen naar `Remove-TypeData` . Wanneer u een object pipet op `Remove-TypeData` , `Remove-TypeData` haalt de type naam van het object op en verwijdert alle type gegevens voor het object type.

```yaml
Type: System.String
Parameter Sets: RemoveTypeSet
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

Hiermee wordt weergegeven wat er zou gebeuren als u de cmdlet uitvoert. De cmdlet wordt niet uitgevoerd.

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

Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable. Zie [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)voor meer informatie.

## Invoerwaarden

### System. Management. Automation. Runspaces. TypeData

U kunt het **TypeData** -object, zoals de items die `Get-TypeData` door de cmdlet worden geretourneerd, aan `Remove-TypeData` .

### System. String

U kunt de type namen door sluizen naar `Remove-TypeData` . Wanneer u een object pipet op `Remove-TypeData` , `Remove-TypeData` haalt de type naam van het object op en verwijdert alle type gegevens voor het object type.

## Uitvoer

### Geen

Met deze cmdlet wordt geen uitvoer gegenereerd.

## Opmerkingen

`Remove-TypeData` kan alleen de uitgebreide-type gegevens in de huidige sessie verwijderen. Het is niet mogelijk om uitgebreide type gegevens op de computer te verwijderen, maar is niet toegevoegd aan de huidige sessie, zoals uitgebreide typen die zijn gedefinieerd in modules die niet in de huidige sessie zijn geïmporteerd.

## Verwante koppelingen

[Get-TypeData](Get-TypeData.md)

[Update-TypeData](Update-TypeData.md)
