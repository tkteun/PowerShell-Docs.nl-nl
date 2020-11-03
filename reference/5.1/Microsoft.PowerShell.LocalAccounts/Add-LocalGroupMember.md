---
external help file: Microsoft.Powershell.LocalAccounts.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.LocalAccounts
ms.date: 04/09/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.localaccounts/add-localgroupmember?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Add-LocalGroupMember
ms.openlocfilehash: 06993c8f6618472f4809e37fbf83d298d13ae515
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/07/2020
ms.locfileid: "93249933"
---
# Add-LocalGroupMember

## SAMENVATTING
Hiermee voegt u leden toe aan een lokale groep.

## SYNTAXIS

### Groep

```
Add-LocalGroupMember [-Group] <LocalGroup> [-Member] <LocalPrincipal[]> [-WhatIf] [-Confirm]
 [<CommonParameters>]
```

### Standaard

```
Add-LocalGroupMember [-Member] <LocalPrincipal[]> [-Name] <String> [-WhatIf] [-Confirm] [<CommonParameters>]
```

### Behoren

```
Add-LocalGroupMember [-Member] <LocalPrincipal[]> [-SID] <SecurityIdentifier> [-WhatIf] [-Confirm]
 [<CommonParameters>]
```

## BESCHRIJVING

De `Add-LocalGroupMember` cmdlet voegt gebruikers of groepen toe aan een lokale beveiligings groep. Alle rechten en machtigingen die aan een groep zijn toegewezen, worden toegewezen aan alle leden van die groep.

Leden van de groep Administrators op een lokale computer hebben machtigingen voor volledig beheer op die computer. Beperk het aantal gebruikers in de groep Administrators.

Als de computer lid is van een domein, kunt u gebruikers accounts, computer accounts en groeps accounts uit dat domein en uit vertrouwde domeinen toevoegen aan een lokale groep.

> [!NOTE]
> Als de computer lid is van een domein en u probeert een lokale gebruiker toe te voegen die dezelfde naam heeft als een lid van het domein, voegt deze het domeinlid toe.

## VOORBEELDEN

### Voor beeld 1: leden toevoegen aan de groep Administrators

Met deze opdracht worden verschillende leden toegevoegd aan de lokale groep Administrators. De nieuwe leden bevatten een lokale gebruikers account, een Microsoft-account, een Azure Active Directory account en een domein groep. In dit voor beeld wordt een tijdelijke aanduiding gebruikt voor de gebruikers naam van een account op Outlook.com.

```powershell
Add-LocalGroupMember -Group "Administrators" -Member "Admin02", "MicrosoftAccount\username@Outlook.com", "AzureAD\DavidChew@contoso.com", "CONTOSO\Domain Admins"
```

## PARAMETERS

### -Group

Hiermee geeft u de beveiligings groep waaraan deze cmdlet leden toevoegt.

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

Hiermee geeft u een matrix van gebruikers of groepen die met deze cmdlet worden toegevoegd aan een beveiligings groep. U kunt gebruikers of groepen opgeven op naam, beveiligings-ID (SID) of **LocalPrincipal** -objecten.

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

Hiermee geeft u de naam van de beveiligings groep waaraan deze cmdlet leden toevoegt.

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

Hiermee geeft u de beveiligings-ID op van de beveiligings groep waaraan deze cmdlet leden toevoegt.

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

Hiermee wordt weergegeven wat er zou gebeuren als u de cmdlet uitvoert. De cmdlet wordt niet uitgevoerd.

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

U kunt een lokale Principal, een teken reeks of een SID door geven aan deze cmdlet.

## UITVOER

### Geen

Met deze cmdlet wordt geen uitvoer gegenereerd.

## OPMERKINGEN

De module micro soft. Power shell. LocalAccounts is niet beschikbaar in 32-bits Power shell op een 64-bits systeem.

De eigenschap **PrincipalSource** is een eigenschap van de objecten **lokalegebruiker** , **LocalGroup** en **LocalPrincipal** waarmee de bron van het object wordt beschreven. De mogelijke bronnen zijn als volgt:

- Lokaal
- Active Directory
- Azure Active Directory-groep
- Microsoft-account

**PrincipalSource** wordt alleen ondersteund door Windows 10, windows server 2016 en latere versies van het Windows-besturings systeem. De eigenschap is leeg voor eerdere versies.

## GERELATEERDE KOPPELINGEN

[Get-LocalGroupMember](Get-LocalGroupMember.md)

[Nieuw-LocalGroup](New-LocalGroup.md)

[Remove-LocalGroupMember](Remove-LocalGroupMember.md)
