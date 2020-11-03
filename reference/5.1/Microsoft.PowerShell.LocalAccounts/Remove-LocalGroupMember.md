---
external help file: Microsoft.Powershell.LocalAccounts.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.LocalAccounts
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.localaccounts/remove-localgroupmember?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Remove-LocalGroupMember
ms.openlocfilehash: 6e6264a65c343657c2f2f87384d76cc3f1554d3d
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/07/2020
ms.locfileid: "93250613"
---
# Remove-LocalGroupMember

## SAMENVATTING
Hiermee verwijdert u leden uit een lokale groep.

## SYNTAXIS

### Groep

```
Remove-LocalGroupMember [-Group] <LocalGroup> [-Member] <LocalPrincipal[]> [-WhatIf] [-Confirm]
 [<CommonParameters>]
```

### Standaard

```
Remove-LocalGroupMember [-Member] <LocalPrincipal[]> [-Name] <String> [-WhatIf] [-Confirm] [<CommonParameters>]
```

### Behoren

```
Remove-LocalGroupMember [-Member] <LocalPrincipal[]> [-SID] <SecurityIdentifier> [-WhatIf] [-Confirm]
 [<CommonParameters>]
```

## BESCHRIJVING
De cmdlet **Remove-LocalGroupMember** verwijdert gebruikers of groepen uit een lokale groep.

> [!NOTE]
> De module micro soft. Power shell. LocalAccounts is niet beschikbaar in 32-bits Power shell op een 64-bits systeem.

## VOORBEELDEN

### Voor beeld 1: leden verwijderen uit de groep Administrators

```
PS C:\> Remove-LocalGroupMember -Group "Administrators" -Member "Admin02", "MicrosoftAccount\username@Outlook.com", "AzureAD\DavidChew@contoso.com", "CONTOSO\Domain Admins"
```

Met deze opdracht worden verschillende leden uit de lokale groep Administrators verwijderd.
De leden die met deze cmdlet worden verwijderd, zijn onder andere een lokale gebruikers account, een Microsoft-account, een Azure Active Directory account en een domein groep.
In dit voor beeld wordt een tijdelijke aanduiding gebruikt voor de gebruikers naam van een account op Outlook.com.

## PARAMETERS

### -Group
Hiermee geeft u de beveiligings groep op waarvan deze cmdlet leden verwijdert.

```yaml
Type: Microsoft.PowerShell.Commands.LocalGroup
Parameter Sets: Group
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Lid
Hiermee geeft u een matrix van gebruikers of groepen die met deze cmdlet worden verwijderd uit een beveiligings groep.
U kunt gebruikers of groepen opgeven op naam, beveiligings-ID (SID) of **LocalPrincipal** -objecten.
Geef SID-teken reeksen op in S-R-I-S-S.
. .
als indeling.

```yaml
Type: Microsoft.PowerShell.Commands.LocalPrincipal[]
Parameter Sets: (All)
Aliases:

Required: True
Position: 1
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### -Name
Hiermee geeft u de naam van de beveiligings groep waaruit deze cmdlet leden verwijdert.

```yaml
Type: System.String
Parameter Sets: Default
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -SID
Hiermee geeft u de beveiligings-ID op van de beveiligings groep waaruit deze cmdlet leden verwijdert.

```yaml
Type: System.Security.Principal.SecurityIdentifier
Parameter Sets: SecurityIdentifier
Aliases:

Required: True
Position: 0
Default value: None
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
Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable. Zie [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)voor meer informatie.

## INVOER

### System. Management. Automation. SecurityAccountsManager. LocalPrincipal, System. String, System. Security. Principal. SecurityIdentifier
U kunt een lokale Principal, een teken reeks of een SID door geven aan deze cmdlet.

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

[Add-LocalGroupMember](Add-LocalGroupMember.md)

[Get-LocalGroupMember](Get-LocalGroupMember.md)

[Nieuw-LocalGroup](New-LocalGroup.md)
