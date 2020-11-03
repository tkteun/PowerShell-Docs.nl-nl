---
external help file: Microsoft.Powershell.LocalAccounts.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.LocalAccounts
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.localaccounts/disable-localuser?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Disable-LocalUser
ms.openlocfilehash: a62242251da00688d3299c60e4cdae7aae6f581a
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/07/2020
ms.locfileid: "93249932"
---
# Disable-LocalUser

## SAMENVATTING
Hiermee schakelt u een lokaal gebruikers account uit.

## SYNTAXIS

### Input object

```
Disable-LocalUser [-InputObject] <LocalUser[]> [-WhatIf] [-Confirm] [<CommonParameters>]
```

### Standaard

```
Disable-LocalUser [-Name] <String[]> [-WhatIf] [-Confirm] [<CommonParameters>]
```

### Behoren

```
Disable-LocalUser [-SID] <SecurityIdentifier[]> [-WhatIf] [-Confirm] [<CommonParameters>]
```

## BESCHRIJVING
Met de cmdlet **Disable-lokalegebruiker** worden lokale gebruikers accounts uitgeschakeld.
Wanneer een gebruikers account is uitgeschakeld, kan de gebruiker zich niet aanmelden.
Wanneer een gebruikers account is ingeschakeld, kan de gebruiker zich aanmelden.

> [!NOTE]
> De module micro soft. Power shell. LocalAccounts is niet beschikbaar in 32-bits Power shell op een 64-bits systeem.

## VOORBEELDEN

### Voor beeld 1: een account uitschakelen door een naam op te geven

```
PS C:\> Disable-LocalUser -Name "Admin02"
```

Met deze opdracht wordt het gebruikers account met de naam Admin02 uitgeschakeld.

### Voor beeld 2: een account uitschakelen met behulp van de pijp lijn

```
PS C:\> Get-LocalUser Guest | Disable-LocalUser
```

Met deze opdracht wordt het ingebouwde gast account opgehaald met **Get-lokalegebruiker** en wordt het vervolgens door gegeven aan de huidige cmdlet met behulp van de pijplijn operator.
Met deze cmdlet wordt dat account uitgeschakeld.

## PARAMETERS

### -Input object
Hiermee geeft u een matrix met gebruikers accounts die met deze cmdlet wordt uitgeschakeld.
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
Hiermee geeft u een matrix met namen op van de gebruikers accounts die met deze cmdlet worden uitgeschakeld.

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
Hiermee geeft u een matrix met gebruikers accounts die met deze cmdlet wordt uitgeschakeld.

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

[Enable-Lokalegebruiker](Enable-LocalUser.md)

[Get-Lokalegebruiker](Get-LocalUser.md)

[New-Lokalegebruiker](New-LocalUser.md)

[Remove-Lokalegebruiker](Remove-LocalUser.md)

[Naam wijzigen-Lokalegebruiker](Rename-LocalUser.md)

[Set-Lokalegebruiker](Set-LocalUser.md)
