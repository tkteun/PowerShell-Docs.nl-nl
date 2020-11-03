---
external help file: Microsoft.Powershell.LocalAccounts.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.LocalAccounts
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.localaccounts/new-localuser?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: New-LocalUser
ms.openlocfilehash: d83f3ad12481df0849ff2fe3f61d553a9ffdcdde
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/07/2020
ms.locfileid: "93250611"
---
# New-LocalUser

## SAMENVATTING

Hiermee maakt u een lokaal gebruikers account.

## SYNTAXIS

### Wacht woord (standaard)

```
New-LocalUser [-AccountExpires <DateTime>] [-AccountNeverExpires] [-Description <String>] [-Disabled]
 [-FullName <String>] [-Name] <String> -Password <SecureString> [-PasswordNeverExpires]
 [-UserMayNotChangePassword] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### Geen wacht woord

```
New-LocalUser [-AccountExpires <DateTime>] [-AccountNeverExpires] [-Description <String>] [-Disabled]
 [-FullName <String>] [-Name] <String> [-NoPassword] [-UserMayNotChangePassword] [-WhatIf] [-Confirm]
 [<CommonParameters>]
```

## BESCHRIJVING

Met de `New-LocalUser` cmdlet maakt u een lokaal gebruikers account. Met deze cmdlet maakt u een lokaal gebruikers account of een lokaal gebruikers account dat is verbonden met een Microsoft-account.

> [!NOTE]
> De module micro soft. Power shell. LocalAccounts is niet beschikbaar in 32-bits Power shell op een 64-bits systeem.

## VOORBEELDEN

### Voor beeld 1: een gebruikers account maken

```
PS C:\> New-LocalUser -Name "User02" -Description "Description of this account." -NoPassword
Name    Enabled  Description
----    -------  -----------
User02  True     Description of this account.
```

Met deze opdracht maakt u een lokaal gebruikers account en geeft u de para meters **AccountExpires** of **Password** niet op. Daarom verloopt het account niet standaard of heeft het een wacht woord.

### Voor beeld 2: een gebruikers account met een wacht woord maken

```
PS C:\> $Password = Read-Host -AsSecureString
PS C:\> New-LocalUser "User03" -Password $Password -FullName "Third User" -Description "Description of this account."
Name    Enabled  Description
----    -------  -----------
User03  True     Description of this account.
```

Met de eerste opdracht wordt u gevraagd om een wacht woord met behulp van de- `Read-Host` cmdlet. De opdracht slaat het wacht woord op als een beveiligde teken reeks in de `$Password` variabele.

Met de tweede opdracht maakt u een lokaal gebruikers account met behulp van het wacht woord dat is opgeslagen in `$Password` . De opdracht geeft een gebruikers naam, volledige naam en beschrijving voor het gebruikers account op.

## PARAMETERS

### -AccountExpires

Hiermee geeft u op wanneer het gebruikers account verloopt. Gebruik de cmdlet om een **DateTime** -object te verkrijgen `Get-Date` .
Als u deze para meter niet opgeeft, verloopt het account niet.

```yaml
Type: System.DateTime
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
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
Accept pipeline input: True (ByPropertyName)
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
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -Uitgeschakeld

Hiermee wordt aangegeven dat de gebruikers account is uitgeschakeld met deze cmdlet.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -FullName

Hiermee geeft u de volledige naam voor het gebruikers account. De volledige naam wijkt af van de gebruikers naam van het gebruikers account.

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -Name

Hiermee geeft u de gebruikers naam voor het gebruikers account.

Als u een lokaal gebruikers account voor het lokale systeem maakt, mag de gebruikers naam Maxi maal 20 tekens of kleine letters bevatten. Een gebruikers naam mag niet de volgende tekens bevatten:

`"`, `/`, `\`, `[`, `]`, `:`, `;`, `|`, `=`, `,`, `+`, `*`, `?`, `<`, `>`, `@`

Een gebruikers naam mag niet alleen uit punten `.` of spaties bestaan.

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### -Geen wacht woord

Geeft aan dat het gebruikers account geen wacht woord heeft.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: NoPassword
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -Password

Hiermee geeft u een wacht woord voor het gebruikers account. U kunt `Read-Host -GetCredential` , `Get-Credential` , of `ConvertTo-SecureString` een **SecureString** -object maken voor het wacht woord.

Als u de para meters **wacht woord** **en wacht woord** weglaat, wordt `New-LocalUser` u gevraagd om het wacht woord van de nieuwe gebruiker.

```yaml
Type: System.Security.SecureString
Parameter Sets: Password
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -PasswordNeverExpires

Hiermee wordt aangegeven of het wacht woord is verlopen.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: Password
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -UserMayNotChangePassword

Geeft aan dat de gebruiker het wacht woord voor het gebruikers account niet kan wijzigen.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
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

Deze cmdlet biedt ondersteuning voor de algemene para meters: `-Debug` , `-ErrorAction` , `-ErrorVariable` , `-InformationAction` , `-InformationVariable` , `-OutVariable` , `-OutBuffer` , `-PipelineVariable` , `-Verbose` , `-WarningAction` en `-WarningVariable` . Zie [about_CommonParameters](/reference/6/Microsoft.PowerShell.Core/About/about_CommonParameters.md)voor meer informatie.

## INVOER

### System. String, System. DateTime, System. Boole, System. Security. SecureString

U kunt een teken reeks, een **DateTime** -object, een Booleaanse waarde of een beveiligde teken reeks door geven aan deze cmdlet.

## UITVOER

### System. Management. Automation. SecurityAccountsManager. Lokalegebruiker

Met deze cmdlet wordt een **lokalegebruiker** -object geretourneerd.
Dit object bevat informatie over het gebruikers account.

## OPMERKINGEN

- Een gebruikers naam mag niet identiek zijn aan een andere gebruikers naam of groeps naam op de computer. Een gebruikers naam mag niet alleen uit punten `.` of spaties bestaan. Een gebruikers naam mag Maxi maal 20 tekens of kleine letters bevatten. Een gebruikers naam mag niet de volgende tekens bevatten:

`"`, `/`, `\`, `[`, `]`, `:`, `;`, `|`, `=`, `,`, `+`, `*`, `?`, `<`, `>`, `@`

- Een wacht woord mag Maxi maal 127 tekens bevatten.
- De eigenschap **PrincipalSource** is een eigenschap van de objecten **lokalegebruiker** , **LocalGroup** en **LocalPrincipal** waarmee de bron van het object wordt beschreven. De mogelijke bronnen zijn als volgt:

  - Lokaal
  - Active Directory
  - Azure Active Directory-groep
  - Microsoft-account

> [!NOTE]
> **PrincipalSource** wordt alleen ondersteund door Windows 10, windows server 2016 en latere versies van het Windows-besturings systeem. De eigenschap is leeg voor eerdere versies.

## GERELATEERDE KOPPELINGEN

[Disable-Lokalegebruiker](Disable-LocalUser.md)

[Enable-Lokalegebruiker](Enable-LocalUser.md)

[Get-Lokalegebruiker](Get-LocalUser.md)

[Remove-Lokalegebruiker](Remove-LocalUser.md)

[Naam wijzigen-Lokalegebruiker](Rename-LocalUser.md)

[Set-Lokalegebruiker](Set-LocalUser.md)
