---
external help file: Microsoft.Management.Infrastructure.CimCmdlets.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: CimCmdlets
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/cimcmdlets/remove-cimsession?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Remove-CimSession
ms.openlocfilehash: 729b0d1c860d29190ab4b87b818dd7b89018bfd7
ms.sourcegitcommit: de63e9481cf8024883060aae61fb02c59c2de662
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/03/2020
ms.locfileid: "93249476"
---
# Remove-CimSession

## SAMENVATTING
Hiermee verwijdert u een of meer CIM-sessies.

## SYNTAXIS

### CimSessionSet (standaard)

```
Remove-CimSession [-CimSession] <CimSession[]> [-WhatIf] [-Confirm] [<CommonParameters>]
```

### ComputerNameSet

```
Remove-CimSession [-ComputerName] <String[]> [-WhatIf] [-Confirm] [<CommonParameters>]
```

### SessionIdSet

```
Remove-CimSession [-Id] <UInt32[]> [-WhatIf] [-Confirm] [<CommonParameters>]
```

### InstanceIdSet

```
Remove-CimSession -InstanceId <Guid[]> [-WhatIf] [-Confirm] [<CommonParameters>]
```

### Naamset

```
Remove-CimSession -Name <String[]> [-WhatIf] [-Confirm] [<CommonParameters>]
```

## BESCHRIJVING

`Remove-CimSession`Met de cmdlet worden een of meer CIM-sessie objecten uit de lokale Power shell-sessie verwijderd.

## VOORBEELDEN

### Voor beeld 1: alle CIM-sessies verwijderen

In dit voor beeld worden alle beschik bare CIM-sessies op de lokale computer opgehaald met behulp van de cmdlet [Get-CimSession](Get-CimSession.md) en worden deze vervolgens verwijderd met behulp van `Remove-CimSession` .

```powershell
Get-CimSession | Remove-CimSession
```

### Voor beeld 2: een specifieke CIM-sessie verwijderen

In dit voor beeld wordt de CIM-sessie met de **id-** waarde 5 verwijderd.

```powershell
Remove-CimSession -Id 5
```

### Voor beeld 3: de lijst met te verwijderen CIM-sessies weer geven met behulp van de para meter WhatIf

In dit voor beeld wordt gebruikgemaakt van de algemene para meter **WhatIf** om op te geven dat de verwijdering niet moet worden uitgevoerd, maar alleen output wat er zou gebeuren als deze is uitgevoerd.

```powershell
Remove-CimSession -Name a* -WhatIf
```

## PARAMETERS

### -CimSession

Hiermee geeft u de sessie objecten op van de CIM-sessies die moeten worden gesloten.

Voer een variabele in die de CIM-sessie bevat of een opdracht die de CIM-sessie, zoals de [`New-CimSession`](New-CimSession.md) of cmdlets, maakt of ontvangt [`Get-CimSession`](Get-CimSession.md) .
Zie [about_CimSessions](../Microsoft.PowerShell.Core/About/about_CimSession.md)voor meer informatie.

```yaml
Type: Microsoft.Management.Infrastructure.CimSession[]
Parameter Sets: CimSessionSet
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### -ComputerName

Hiermee geeft u een matrix met namen van computers op. Hiermee verwijdert u de sessies die verbinding maken met de opgegeven computers. U kunt een Fully Qualified Domain Name (FQDN) of een NetBIOS-naam opgeven.

```yaml
Type: System.String[]
Parameter Sets: ComputerNameSet
Aliases: CN, ServerName

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: True
```

### -Id

Hiermee geeft u de ID op van de CIM-sessie die u wilt verwijderen. Geef een of meer Id's op, gescheiden door komma's, of gebruik de operator Range ( `..` ) om een reeks id's op te geven. Een **id** is een geheel getal dat de CIM-sessie in de huidige Power shell-sessie uniek identificeert.

Zie [about_Operators](../Microsoft.PowerShell.Core/About/about_Operators.md)voor meer informatie over de operator Range.

```yaml
Type: System.UInt32[]
Parameter Sets: SessionIdSet
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -InstanceId

Hiermee geeft u de exemplaar-ID op van de CIM-sessie die u wilt verwijderen. **InstanceId** is een GUID (Globally Unique Identifier) waarmee een CIM-sessie uniek wordt geïdentificeerd. De **InstanceId** is uniek, zelfs wanneer er meerdere sessies in Power shell worden uitgevoerd.

De **InstanceId** wordt opgeslagen in de eigenschap **InstanceId** van het object dat een CIM-sessie vertegenwoordigt.

```yaml
Type: System.Guid[]
Parameter Sets: InstanceIdSet
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -Name

Hiermee geeft u de beschrijvende naam op van de CIM-sessie die u wilt verwijderen. U kunt joker tekens gebruiken met deze para meter.

```yaml
Type: System.String[]
Parameter Sets: NameSet
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
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

## INVOER

### Geen

Deze cmdlet accepteert geen invoer objecten.

## UITVOER

### System. object

Met deze cmdlet wordt een object geretourneerd dat informatie over CIM-sessies bevat.

## OPMERKINGEN

## GERELATEERDE KOPPELINGEN

[Get-CimSession](Get-CimSession.md)

[New-CimSession](New-CimSession.md)

[about_CimSession](../Microsoft.PowerShell.Core/About/about_CimSession.md)
