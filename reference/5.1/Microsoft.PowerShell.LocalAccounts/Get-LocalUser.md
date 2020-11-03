---
external help file: Microsoft.Powershell.LocalAccounts.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.LocalAccounts
ms.date: 02/10/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.localaccounts/get-localuser?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-LocalUser
ms.openlocfilehash: 34210145bcddc8d9420552d637a6cd6e5f8e61cc
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/07/2020
ms.locfileid: "93249923"
---
# Get-LocalUser

## SAMENVATTING
Hiermee haalt u lokale gebruikers accounts op.

## SYNTAXIS

### Standaard (standaard instelling)

```
Get-LocalUser [[-Name] <String[]>] [<CommonParameters>]
```

### Behoren

```
Get-LocalUser [[-SID] <SecurityIdentifier[]>] [<CommonParameters>]
```

## BESCHRIJVING

De `Get-LocalUser` cmdlet haalt lokale gebruikers accounts op. Deze cmdlet krijgt standaard ingebouwde gebruikers accounts, lokale gebruikers accounts die u hebt gemaakt en lokale accounts die u hebt verbonden met micro soft-accounts.

> [!NOTE]
> De module micro soft. Power shell. LocalAccounts is niet beschikbaar in 32-bits Power shell op een 64-bits systeem.

## VOORBEELDEN

### Voor beeld 1: een account ophalen met behulp van de naam

In dit voor beeld wordt een gebruikers account met de naam AdminContoso02 opgehaald.

```powershell
Get-LocalUser -Name "AdminContoso02"
```

```Output
Name             Enabled Description
----             ------- -----------
AdminContoso02   True    Description of this account.
```

### Voor beeld 2: een account ophalen dat is verbonden met een Microsoft-account

In dit voor beeld wordt een gebruikers account opgehaald dat is verbonden met een Microsoft-account. In dit voor beeld wordt een tijdelijke aanduiding voor de gebruikers naam van een account op Outlook.com.

```powershell
Get-LocalUser -Name "MicrosoftAccount\username@Outlook.com"
```

```Output
Name                                    Enabled  Description
----                                    -------  -----------
MicrosoftAccount\username@outlook.com  True     Description of this account.
```

### Voor beeld 3: een account ophalen dat is verbonden met een Microsoft-account

In dit voor beeld wordt een lokale gebruikers account met de opgegeven SID opgehaald.

```powershell
Get-LocalUser -SID S-1-5-21-9526073513-1762370368-3942940353-500
```

```Output
Name          Enabled Description
----          ------- -----------
Administrator True    Built-in account for administering the computer/domain
```

## PARAMETERS

### -Name

Hiermee geeft u een matrix met namen van gebruikers accounts op die met deze cmdlet worden opgehaald. U kunt het Joker teken gebruiken.

```yaml
Type: System.String[]
Parameter Sets: Default
Aliases:

Required: False
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: True
```

### -SID

Hiermee geeft u een matrix met beveiligings-Id's (Sid's) op van gebruikers accounts die met deze cmdlet worden opgehaald.

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

U kunt een teken reeks of SID door sluizen naar deze cmdlet.

## UITVOER

### System. Management. Automation. SecurityAccountsManager. Lokalegebruiker []

Met deze cmdlet worden lokale gebruikers accounts geretourneerd.

## OPMERKINGEN

De eigenschap **PrincipalSource** in de objecten **lokalegebruiker** , **LocalGroup** en **LocalPrincipal** beschrijft de bron van het object. De mogelijke bronnen zijn als volgt:

- Lokaal
- Active Directory
- Azure Active Directory-groep
- Microsoft-account

**PrincipalSource** wordt alleen ondersteund door Windows 10, windows server 2016 en latere versies van het Windows-besturings systeem. De eigenschap is leeg voor eerdere versies.

## GERELATEERDE KOPPELINGEN

[Disable-Lokalegebruiker](Disable-LocalUser.md)

[Enable-Lokalegebruiker](Enable-LocalUser.md)

[New-Lokalegebruiker](New-LocalUser.md)

[Remove-Lokalegebruiker](Remove-LocalUser.md)

[Naam wijzigen-Lokalegebruiker](Rename-LocalUser.md)

[Set-Lokalegebruiker](Set-LocalUser.md)
