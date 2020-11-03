---
external help file: Microsoft.Powershell.LocalAccounts.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.LocalAccounts
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.localaccounts/rename-localuser?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Rename-LocalUser
ms.openlocfilehash: fc5740e52e08ad2146981799a4e1659cd420b321
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/07/2020
ms.locfileid: "93250849"
---
# Rename-LocalUser

## SAMENVATTING
De naam van een lokale gebruikers account wordt gewijzigd.

## SYNTAXIS

### Input object

```
Rename-LocalUser [-InputObject] <LocalUser> [-NewName] <String> [-WhatIf] [-Confirm] [<CommonParameters>]
```

### Standaard

```
Rename-LocalUser [-Name] <String> [-NewName] <String> [-WhatIf] [-Confirm] [<CommonParameters>]
```

### Behoren

```
Rename-LocalUser [-NewName] <String> [-SID] <SecurityIdentifier> [-WhatIf] [-Confirm] [<CommonParameters>]
```

## BESCHRIJVING
De naam van de cmdlet **Rename-lokalegebruiker** wijzigt een lokale gebruikers account.

> [!NOTE]
> De module micro soft. Power shell. LocalAccounts is niet beschikbaar in 32-bits Power shell op een 64-bits systeem.

## VOORBEELDEN

### Voor beeld 1: de naam van een gebruikers account wijzigen

```
PS C:\> Rename-LocalUser -Name "Admin02" -NewName "AdminContoso02"
```

Met deze opdracht wordt de naam gewijzigd van het gebruikers account met de naam Admin02.

## PARAMETERS

### -Input object
Hiermee geeft u het gebruikers account op dat met deze cmdlet wordt hernoemd.
Gebruik de cmdlet Get-LocalUser om een gebruikers account te verkrijgen.

```yaml
Type: Microsoft.PowerShell.Commands.LocalUser
Parameter Sets: InputObject
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### -Name
Hiermee geeft u de naam van het gebruikers account dat door deze cmdlet wordt hernoemd.

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

### -NewName
Hiermee geeft u een nieuwe naam op voor het gebruikers account.

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: True
Position: 1
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -SID
Hiermee geeft u de beveiligings-ID (SID) van een gebruikers account op die door deze cmdlet wordt hernoemd.

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

[Remove-Lokalegebruiker](Remove-LocalUser.md)

[Set-Lokalegebruiker](Set-LocalUser.md)
