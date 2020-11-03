---
external help file: Microsoft.Powershell.LocalAccounts.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.LocalAccounts
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.localaccounts/get-localgroup?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-LocalGroup
ms.openlocfilehash: 2cd77c2766840527825b0ccf68abaac3c2ea6c16
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/07/2020
ms.locfileid: "93249927"
---
# Get-LocalGroup

## SAMENVATTING
Hiermee haalt u de lokale beveiligings groepen op.

## SYNTAXIS

### Standaard (standaard instelling)

```
Get-LocalGroup [[-Name] <String[]>] [<CommonParameters>]
```

### Behoren

```
Get-LocalGroup [[-SID] <SecurityIdentifier[]>] [<CommonParameters>]
```

## BESCHRIJVING
Met de cmdlet **Get-LocalGroup** worden lokale beveiligings groepen in de SAM-account opgehaald.
Met deze cmdlet worden standaard ingebouwde groepen en lokale beveiligings groepen opgehaald die u maakt.

> [!NOTE]
> De module micro soft. Power shell. LocalAccounts is niet beschikbaar in 32-bits Power shell op een 64-bits systeem.

## VOORBEELDEN

### Voor beeld 1: de groep Administrators ophalen

```
PS C:\> Get-LocalGroup -Name "Administrators"
Name           Description
----           -----------
Administrators Administrators have complete and unrestricted access to the computer/domain
```

Met deze opdracht wordt de lokale groep Administrators opgehaald.
Met de opdracht worden de eigenschappen van de groep in de-console weer gegeven.

## PARAMETERS

### -Name
Hiermee geeft u een matrix met namen van beveiligings groepen op die met deze cmdlet worden opgehaald.
U kunt het Joker teken gebruiken.

```yaml
Type: System.String[]
Parameter Sets: Default
Aliases:

Required: False
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### -SID
Hiermee geeft u een matrix met beveiligings-Id's (Sid's) op van beveiligings groepen die met deze cmdlet worden opgehaald.

```yaml
Type: System.Security.Principal.SecurityIdentifier[]
Parameter Sets: SecurityIdentifier
Aliases:

Required: False
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### CommonParameters
Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable. Zie [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)voor meer informatie.

## INVOER

### System. String, System. Security. Principal. SecurityIdentifier
U kunt een teken reeks of SID door geven aan deze cmdlet.

## UITVOER

### System. Management. Automation. SecurityAccountsManager. LocalGroup
Met deze cmdlet wordt een lokale groep geretourneerd.

## OPMERKINGEN

* De eigenschap **PrincipalSource** is een eigenschap van de objecten **lokalegebruiker** , **LocalGroup** en **LocalPrincipal** waarmee de bron van het object wordt beschreven. De mogelijke bronnen zijn als volgt:

- Lokaal
- Active Directory
- Azure Active Directory-groep
- Microsoft-account

**PrincipalSource** wordt alleen ondersteund door Windows 10, windows server 2016 en latere versies van het Windows-besturings systeem. De eigenschap is leeg voor eerdere versies.

## GERELATEERDE KOPPELINGEN

[Nieuw-LocalGroup](New-LocalGroup.md)

[Remove-LocalGroup](Remove-LocalGroup.md)

[Rename-LocalGroup](Rename-LocalGroup.md)

[Set-LocalGroup](Set-LocalGroup.md)
