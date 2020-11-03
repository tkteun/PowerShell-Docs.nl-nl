---
external help file: Microsoft.Powershell.LocalAccounts.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.LocalAccounts
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.localaccounts/get-localgroupmember?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-LocalGroupMember
ms.openlocfilehash: 200368c5d13bd027302ad824533e6c187906ed0f
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/07/2020
ms.locfileid: "93249924"
---
# Get-LocalGroupMember

## SAMENVATTING
Hiermee worden leden opgehaald uit een lokale groep.

## SYNTAXIS

### Standaard (standaard instelling)

```
Get-LocalGroupMember [[-Member] <String>] [-Name] <String> [<CommonParameters>]
```

### Groep

```
Get-LocalGroupMember [-Group] <LocalGroup> [[-Member] <String>] [<CommonParameters>]
```

### Behoren

```
Get-LocalGroupMember [[-Member] <String>] [-SID] <SecurityIdentifier> [<CommonParameters>]
```

## BESCHRIJVING
De cmdlet **Get-LocalGroupMember** krijgt leden van een lokale groep.

> [!NOTE]
> De module micro soft. Power shell. LocalAccounts is niet beschikbaar in 32-bits Power shell op een 64-bits systeem.

## VOORBEELDEN

### Voor beeld 1: alle leden van de groep Administrators ophalen

```
PS C:\> Get-LocalGroupMember -Group "Administrators"
ObjectClass Name                    PrincipalSource
----------- ----                    ---------------
User        CONTOSOPC\Administrator Local
User        CONTOSOPC\LocalAdmin    Local
```

Met deze opdracht worden alle leden van de lokale groep Administrators opgehaald.

## PARAMETERS

### -Group
Hiermee geeft u de beveiligings groep op waarvan deze cmdlet leden ophaalt.

```yaml
Type: Microsoft.PowerShell.Commands.LocalGroup
Parameter Sets: Group
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### -Lid
Hiermee geeft u een gebruiker of groep op die met deze cmdlet wordt opgehaald van een beveiligings groep.
U kunt gebruikers of groepen opgeven op naam of beveiligings-ID (SID).
Geef SID-teken reeksen op in S-R-I-S-S.
. .
als indeling.
U kunt joker tekens gebruiken.
Als u deze para meter niet opgeeft, haalt de cmdlet alle leden van de groep op.

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: 1
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Name
Hiermee geeft u de naam van de beveiligings groep op waarvan deze cmdlet leden ophaalt.

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

### -SID
Hiermee geeft u de beveiligings-ID op van de beveiligings groep waarvan de cmdlet leden ophaalt.

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

### CommonParameters
Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable. Zie [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)voor meer informatie.

## INVOER

### System. Management. Automation. SecurityAccountsManager. LocalGroup, System. String, System. Security. Principal. SecurityIdentifier
U kunt een lokale groep, een teken reeks of een SID door geven aan deze cmdlet.

## UITVOER

### Micro soft. SecurityAccountsManager. LocalPrincipal
Met deze cmdlet worden lokale principals geretourneerd.

## OPMERKINGEN

* De eigenschap **PrincipalSource** is een eigenschap van de objecten **lokalegebruiker** , **LocalGroup** en **LocalPrincipal** waarmee de bron van het object wordt beschreven. De mogelijke bronnen zijn als volgt:

- Lokaal
- Active Directory
- Azure Active Directory-groep
- Microsoft-account

**PrincipalSource** wordt alleen ondersteund door Windows 10, windows server 2016 en latere versies van het Windows-besturings systeem. De eigenschap is leeg voor eerdere versies.

## GERELATEERDE KOPPELINGEN

[Add-LocalGroupMember](Add-LocalGroupMember.md)

[Nieuw-LocalGroup](New-LocalGroup.md)

[Remove-LocalGroupMember](Remove-LocalGroupMember.md)
