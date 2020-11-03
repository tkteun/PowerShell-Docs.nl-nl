---
external help file: Microsoft.Powershell.LocalAccounts.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.LocalAccounts
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.localaccounts/set-localgroup?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Set-LocalGroup
ms.openlocfilehash: 471c3c7bc01bf26dfe9d8eec26e4414464cae02e
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/07/2020
ms.locfileid: "93250848"
---
# Set-LocalGroup

## SAMENVATTING
Hiermee wijzigt u een lokale beveiligings groep.

## SYNTAXIS

### Input object

```
Set-LocalGroup -Description <String> [-InputObject] <LocalGroup> [-WhatIf] [-Confirm] [<CommonParameters>]
```

### Standaard

```
Set-LocalGroup -Description <String> [-Name] <String> [-WhatIf] [-Confirm] [<CommonParameters>]
```

### Behoren

```
Set-LocalGroup -Description <String> [-SID] <SecurityIdentifier> [-WhatIf] [-Confirm] [<CommonParameters>]
```

## BESCHRIJVING
De cmdlet **set-LocalGroup** wijzigt een lokale beveiligings groep.

## VOORBEELDEN

### Voor beeld 1: een groeps beschrijving wijzigen

```
PS C:\> Set-LocalGroup -Name "SecurityGroup04" -Description "This is a sample description."
```

Met deze opdracht wordt de beschrijving van een lokale groep gewijzigd.

> [!NOTE]
> De module micro soft. Power shell. LocalAccounts is niet beschikbaar in 32-bits Power shell op een 64-bits systeem.

## PARAMETERS

### -Beschrijving
Hiermee geeft u een opmerking voor de groep op.
De maximale lengte is 48 tekens.

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Input object
Hiermee geeft u de beveiligings groep op die met deze cmdlet wordt gewijzigd.
Gebruik de cmdlet Get-LocalGroup om een beveiligings groep te verkrijgen.

```yaml
Type: Microsoft.PowerShell.Commands.LocalGroup
Parameter Sets: InputObject
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### -Name
Hiermee geeft u de naam van de beveiligings groep die met deze cmdlet wordt gewijzigd.

```yaml
Type: System.String
Parameter Sets: Default
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### -SID
Hiermee geeft u de beveiligings-ID (SID) op van de beveiligings groep die met deze cmdlet wordt gewijzigd.

```yaml
Type: System.Security.Principal.SecurityIdentifier
Parameter Sets: SecurityIdentifier
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
Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable. Zie [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)voor meer informatie.

## INVOER

### System. Management. Automation. SecurityAccountsManager. LocalGroup, System. String, System. Security. Principal. SecurityIdentifier
U kunt een beveiligings groep, een teken reeks of een SID door sluizen naar deze cmdlet.

## UITVOER

### Geen
Met deze cmdlet wordt geen uitvoer gegenereerd.

## OPMERKINGEN

* De eigenschap **PrincipalSource** is een eigenschap van de objecten **lokalegebruiker** , **LocalGroup** en **LocalPrincipal** waarmee de bron van het object wordt beschreven. De mogelijke bronnen zijn als volgt:

- Lokaal
- Active Directory
- Azure Active Directory-groep
- Microsoft-account

**PrincipalSource** wordt alleen ondersteund door Windows 10, windows server 2016 en latere versies van het Windows-besturings systeem. De eigenschap is leeg voor eerdere versies.

## GERELATEERDE KOPPELINGEN

[Get-LocalGroup](Get-LocalGroup.md)

[Nieuw-LocalGroup](New-LocalGroup.md)

[Remove-LocalGroup](Remove-LocalGroup.md)

[Rename-LocalGroup](Rename-LocalGroup.md)
