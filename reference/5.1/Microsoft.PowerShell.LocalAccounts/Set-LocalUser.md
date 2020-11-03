---
external help file: Microsoft.Powershell.LocalAccounts.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.LocalAccounts
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.localaccounts/set-localuser?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Set-LocalUser
ms.openlocfilehash: a6352611b757dae828a2efef07f9ce65abaa5e2e
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/07/2020
ms.locfileid: "93250845"
---
# Set-LocalUser

## SAMENVATTING
Hiermee wijzigt u een lokaal gebruikers account.

## SYNTAXIS

### Naam (standaard)

```
Set-LocalUser [-AccountExpires <DateTime>] [-AccountNeverExpires] [-Description <String>] [-FullName <String>]
 [-Name] <String> [-Password <SecureString>] [-PasswordNeverExpires <Boolean>]
 [-UserMayChangePassword <Boolean>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### Input object

```
Set-LocalUser [-AccountExpires <DateTime>] [-AccountNeverExpires] [-Description <String>] [-FullName <String>]
 [-InputObject] <LocalUser> [-Password <SecureString>] [-PasswordNeverExpires <Boolean>]
 [-UserMayChangePassword <Boolean>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### Behoren

```
Set-LocalUser [-AccountExpires <DateTime>] [-AccountNeverExpires] [-Description <String>] [-FullName <String>]
 [-Password <SecureString>] [-PasswordNeverExpires <Boolean>] [-SID] <SecurityIdentifier>
 [-UserMayChangePassword <Boolean>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

## BESCHRIJVING
De cmdlet **set-lokalegebruiker** wijzigt een lokale gebruikers account.
Met deze cmdlet kan het wacht woord van een lokaal gebruikers account opnieuw worden ingesteld.

> [!NOTE]
> De module micro soft. Power shell. LocalAccounts is niet beschikbaar in 32-bits Power shell op een 64-bits systeem.

## VOORBEELDEN

### Voor beeld 1: een beschrijving van een gebruikers account wijzigen

```
PS C:\> Set-LocalUser -Name "Admin07" -Description "Description of this account."
```

Met deze opdracht wordt de beschrijving van een gebruikers account met de naam Admin07 gewijzigd.

### Voor beeld 2: het wacht woord voor een account wijzigen

```
PS C:\> $Password = Read-Host -AsSecureString
PS C:\> $UserAccount = Get-LocalUser -Name "User02"
PS C:\> $UserAccount | Set-LocalUser -Password $Password
```

Met de eerste opdracht wordt u gevraagd om een wacht woord met behulp van de cmdlet Read-Host.
De opdracht slaat het wacht woord op als een beveiligde teken reeks in de variabele $Password.

Met de tweede opdracht wordt een gebruikers account met de naam User02 opgehaald door **Get-lokalegebruiker** te gebruiken.
De opdracht slaat het account op in de variabele $UserAccount.

Met de derde opdracht wordt het nieuwe wacht woord ingesteld voor het gebruikers account dat is opgeslagen in $UserAccount.

## PARAMETERS

### -AccountExpires
Hiermee geeft u op wanneer het gebruikers account verloopt.
Als u een **DateTime** -object wilt ophalen, gebruikt u de cmdlet Get-Date.

Als u het account niet wilt laten verlopen, geeft u de para meter *AccountNeverExpires* op.

```yaml
Type: System.DateTime
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -AccountNeverExpires
Geeft aan dat het account niet verloopt.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Beschrijving
Hiermee geeft u een opmerking op voor het gebruikers account.
De maximale lengte is 48 tekens.

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -FullName
Hiermee geeft u de volledige naam voor het gebruikers account.
De volledige naam wijkt af van de gebruikers naam van het gebruikers account.

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Input object
Hiermee geeft u het gebruikers account op dat met deze cmdlet wordt gewijzigd.
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
Hiermee geeft u de naam van het gebruikers account dat door deze cmdlet wordt gewijzigd.

```yaml
Type: System.String
Parameter Sets: Name
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### -Password
Hiermee geeft u een wacht woord voor het gebruikers account.
Als het gebruikers account is verbonden met een Microsoft-account, stelt u geen wacht woord in.

U kunt `Read-Host -GetCredential` , Get-Credential of ConvertTo-SecureString gebruiken om een **SecureString** -object voor het wacht woord te maken.

Als u de para meters *wacht woord* en niet- *wacht woord* weglaat, **stelt u-lokalegebruiker** in om het wacht woord van de gebruiker.

```yaml
Type: System.Security.SecureString
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -PasswordNeverExpires
Hiermee wordt aangegeven of het wacht woord is verlopen.

```yaml
Type: System.Boolean
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -SID
Hiermee geeft u de beveiligings-ID (SID) van het gebruikers account dat door deze cmdlet wordt gewijzigd.

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

### -UserMayChangePassword
Geeft aan dat de gebruiker het wacht woord voor het gebruikers account kan wijzigen.

```yaml
Type: System.Boolean
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
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

[Naam wijzigen-Lokalegebruiker](Rename-LocalUser.md)
