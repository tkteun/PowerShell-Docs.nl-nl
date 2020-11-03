---
external help file: Microsoft.Powershell.LocalAccounts.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.LocalAccounts
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.localaccounts/remove-localgroup?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Remove-LocalGroup
ms.openlocfilehash: 6a2f921972fef1794581b301df6e7439e56c7f47
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/07/2020
ms.locfileid: "93250612"
---
# Remove-LocalGroup

## SAMENVATTING
Hiermee verwijdert u lokale beveiligings groepen.

## SYNTAXIS

### Input object

```
Remove-LocalGroup [-InputObject] <LocalGroup[]> [-WhatIf] [-Confirm] [<CommonParameters>]
```

### Standaard

```
Remove-LocalGroup [-Name] <String[]> [-WhatIf] [-Confirm] [<CommonParameters>]
```

### Behoren

```
Remove-LocalGroup [-SID] <SecurityIdentifier[]> [-WhatIf] [-Confirm] [<CommonParameters>]
```

## BESCHRIJVING
Met de cmdlet **Remove-LocalGroup** worden lokale beveiligings groepen verwijderd.
Met deze cmdlet wordt alleen een lokale groep verwijderd.
De gebruikers accounts, computer accounts of groeps accounts die deel uitmaken van deze groep worden niet verwijderd.
U kunt een verwijderde groep niet herstellen.

Als u een groep verwijdert en vervolgens een andere groep met dezelfde groeps naam maakt, moet u nieuwe machtigingen voor de nieuwe groep instellen.
De nieuwe groep neemt niet de machtigingen over die aan de groep zijn toegewezen.

> [!NOTE]
> De module micro soft. Power shell. LocalAccounts is niet beschikbaar in 32-bits Power shell op een 64-bits systeem.

## VOORBEELDEN

### Voor beeld 1: een beveiligings groep verwijderen

```
PS C:\> Remove-LocalGroup -Name "SecurityGroup04"
```

Met deze opdracht wordt de groep met de naam SecurityGroup04 verwijderd.

## PARAMETERS

### -Input object
Hiermee geeft u een matrix van beveiligings groepen op die met deze cmdlet worden verwijderd.
Gebruik de cmdlet Get-LocalGroup om groepen te verkrijgen.

```yaml
Type: Microsoft.PowerShell.Commands.LocalGroup[]
Parameter Sets: InputObject
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### -Name
Hiermee geeft u een matrix met namen op van de beveiligings groepen die met deze cmdlet worden verwijderd.

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
Hiermee geeft u een matrix met beveiligings-Id's (Sid's) op van beveiligings groepen die met deze cmdlet worden verwijderd.

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

### System. Management. Automation. SecurityAccountsManager. LocalGroup, System. String, System. Security. Principal. SecurityIdentifier
U kunt een beveiligings groep, een teken reeks of een SID door sluizen naar deze cmdlet.

## UITVOER

### Geen
Met deze cmdlet wordt geen uitvoer gegenereerd.

## OPMERKINGEN

* Met deze cmdlet kunnen de volgende standaard groepen niet worden verwijderd:

- Beheerders
- Back-upoperators
- Cryptografische Operators
- Gedistribueerde COM-gebruikers
- Gebeurtenislogboek-lezers
- Gasten
- Hyper-V-beheerders
- IIS_IUSRS
- Network Configuration Operators
- Prestatielogboekgebruikers
- Prestatiemetergebruikers
- Hoofdgebruikers
- Extern bureaublad-gebruikers
- Gebruikers van extern beheer
- Replicator
- Gebruikers
- WinRMRemoteWMIUsers__

* De eigenschap **PrincipalSource** is een eigenschap van de objecten **lokalegebruiker** , **LocalGroup** en **LocalPrincipal** waarmee de bron van het object wordt beschreven. De mogelijke bronnen zijn als volgt:

- Lokaal
- Active Directory
- Azure Active Directory-groep
- Microsoft-account

**PrincipalSource** wordt alleen ondersteund door Windows 10, windows server 2016 en latere versies van het Windows-besturings systeem. De eigenschap is leeg voor eerdere versies.

## GERELATEERDE KOPPELINGEN

[Get-LocalGroup](Get-LocalGroup.md)

[Nieuw-LocalGroup](New-LocalGroup.md)

[Rename-LocalGroup](Rename-LocalGroup.md)

[Set-LocalGroup](Set-LocalGroup.md)
