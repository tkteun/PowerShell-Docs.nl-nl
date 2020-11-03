---
external help file: Microsoft.Powershell.LocalAccounts.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.LocalAccounts
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.localaccounts/remove-localuser?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Remove-LocalUser
ms.openlocfilehash: de1054971dab19f8cfae654208488ca9ce5e17e4
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/07/2020
ms.locfileid: "93250850"
---
# Remove-LocalUser

## SAMENVATTING
Lokale gebruikers accounts worden verwijderd.

## SYNTAXIS

### Input object

```
Remove-LocalUser [-InputObject] <LocalUser[]> [-WhatIf] [-Confirm] [<CommonParameters>]
```

### Standaard

```
Remove-LocalUser [-Name] <String[]> [-WhatIf] [-Confirm] [<CommonParameters>]
```

### Behoren

```
Remove-LocalUser [-SID] <SecurityIdentifier[]> [-WhatIf] [-Confirm] [<CommonParameters>]
```

## BESCHRIJVING
Met de cmdlet **Remove-lokalegebruiker** worden lokale gebruikers accounts verwijderd.

## VOORBEELDEN

### Voor beeld 1: een gebruikers account verwijderen

```
PS C:\> Remove-LocalUser -Name "AdminContoso02"
```

Met deze opdracht wordt het gebruikers account met de naam AdminContoso02 verwijderd.

> [!NOTE]
> De module micro soft. Power shell. LocalAccounts is niet beschikbaar in 32-bits Power shell op een 64-bits systeem.

## PARAMETERS

### -Input object
Hiermee geeft u een matrix op met gebruikers accounts die met deze cmdlet worden verwijderd.
Gebruik de cmdlet Get-LocalUser om een gebruikers account te verkrijgen.

```yaml
Type: Microsoft.PowerShell.Commands.LocalUser[]
Parameter Sets: InputObject
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### -Name
Hiermee geeft u een matrix met namen op van de gebruikers accounts die met deze cmdlet worden verwijderd.

```yaml
Type: System.String[]
Parameter Sets: Default
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### -SID
Hiermee geeft u een matrix met beveiligings-Id's (Sid's) op van gebruikers accounts die met deze cmdlet worden verwijderd.

```yaml
Type: System.Security.Principal.SecurityIdentifier[]
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

### System. Management. Automation. SecurityAccountsManager. Lokalegebruiker, System. String, System. Security. Principal. SecurityIdentifier
U kunt een lokale gebruiker, een teken reeks of een SID door geven aan deze cmdlet.

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

[Disable-Lokalegebruiker](Disable-LocalUser.md)

[Enable-Lokalegebruiker](Enable-LocalUser.md)

[Get-Lokalegebruiker](Get-LocalUser.md)

[New-Lokalegebruiker](New-LocalUser.md)

[Naam wijzigen-Lokalegebruiker](Rename-LocalUser.md)

[Set-Lokalegebruiker](Set-LocalUser.md)
