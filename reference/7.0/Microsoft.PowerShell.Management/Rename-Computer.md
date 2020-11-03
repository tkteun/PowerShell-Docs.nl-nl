---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 5/1/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/rename-computer?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Rename-Computer
ms.openlocfilehash: aeffc496e78a447af828737980429a91a74b5a6b
ms.sourcegitcommit: de63e9481cf8024883060aae61fb02c59c2de662
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/03/2020
ms.locfileid: "93249401"
---
# Rename-Computer

## SAMENVATTING
De naam van een computer wijzigen.

## SYNTAXIS

```
Rename-Computer [-ComputerName <String>] [-PassThru] [-DomainCredential <PSCredential>]
 [-LocalCredential <PSCredential>] [-NewName] <String> [-Force] [-Restart] [-WsmanAuthentication <String>]
 [-WhatIf] [-Confirm] [<CommonParameters>]
```

## BESCHRIJVING

De `Rename-Computer` cmdlet hernoemt de naam van de lokale computer of een externe computer.
De naam van een computer in elke opdracht wordt gewijzigd.

Deze cmdlet is geïntroduceerd in Windows Power Shell 3,0.

## VOORBEELDEN

### Voor beeld 1: de naam van de lokale computer wijzigen

Met deze opdracht wordt de naam van de lokale computer gewijzigd in `Server044` en wordt deze opnieuw opgestart om de wijziging van kracht te laten worden.

```powershell
Rename-Computer -NewName "Server044" -DomainCredential Domain01\Admin01 -Restart
```

### Voor beeld 2: de naam van een externe computer wijzigen

Met deze opdracht wordt de naam van de `Srv01` computer gewijzigd in `Server001` . De computer is niet opnieuw opgestart.

De **DomainCredential** para meter geeft u de referenties op van een gebruiker die gemachtigd is om de naam van computers in het domein te wijzigen.

De **Force** -para meter onderdrukt de bevestigings prompt.

```powershell
Rename-Computer -ComputerName "Srv01" -NewName "Server001" -DomainCredential Domain01\Admin01 -Force
```

## PARAMETERS

### -ComputerName

De naam van de opgegeven externe computer.
Standaard is dit de lokale computer.

Typ de NetBIOS-naam, een IP-adres of een Fully Qualified Domain Name van een externe computer.
Als u de lokale computer wilt opgeven, typt u de naam van de computer, een punt ( `.` ) of `localhost` .

Deze para meter is niet afhankelijk van externe communicatie met Power shell.
U kunt de para meter **ComputerName** gebruiken `Rename-Computer` , zelfs als uw computer niet is geconfigureerd om externe opdrachten uit te voeren.

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: Local Computer
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -DomainCredential

Hiermee geeft u een gebruikers account op dat is gemachtigd om verbinding te maken met het domein.
Er zijn expliciete referenties vereist voor het wijzigen van de naam van een computer die lid is van een domein.

Typ een gebruikers naam, zoals `User01` of `Domain01\User01` , of voer een **PSCredential** -object in, zoals het certificaat dat is gegenereerd door de `Get-Credential` cmdlet.

Als u een gebruikers naam typt, vraagt deze cmdlet u om een wacht woord.

Als u een gebruikers account wilt opgeven dat is gemachtigd om verbinding te maken met de computer die is opgegeven door de para meter **ComputerName** , gebruikt u de para meter **LocalCredential** .

```yaml
Type: System.Management.Automation.PSCredential
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Force

Hiermee wordt de opdracht uitgevoerd zonder dat de gebruiker om bevestiging wordt gevraagd.

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

### -LocalCredential

Hiermee geeft u een gebruikers account op dat is gemachtigd om verbinding te maken met de computer die is opgegeven door de para meter **ComputerName** . Standaard is dit de huidige gebruiker.

Typ een gebruikers naam, zoals `User01` of `Domain01\User01` , of voer een **PSCredential** -object in, zoals het certificaat dat is gegenereerd door de `Get-Credential` cmdlet.

Als u een gebruikers naam typt, vraagt deze cmdlet u om een wacht woord.

Als u een gebruikers account wilt opgeven dat is gemachtigd om verbinding te maken met het domein, gebruikt u de para meter **DomainCredential** .

```yaml
Type: System.Management.Automation.PSCredential
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: Current User
Accept pipeline input: False
Accept wildcard characters: False
```

### -NewName

Hiermee geeft u een nieuwe naam voor de computer op.
Deze parameter is vereist.

Standaard namen mogen letters ( `a-z` ), ( `A-Z` ), cijfers ( `0-9` ) en afbreek streepjes ( `-` ), maar geen spaties of punten () bevatten `.` . De naam mag niet volledig uit cijfers bestaan en mag niet langer zijn dan 63 tekens

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -PassThru

Retourneert de resultaten van de opdracht.
Anders wordt met deze cmdlet geen uitvoer gegenereerd.

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

### -Restart

Geeft aan dat deze cmdlet de computer opnieuw opstart waarvan de naam is gewijzigd.
Het is vaak nood zakelijk om opnieuw op te starten om de wijziging van kracht te laten worden.

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

### -WsmanAuthentication

Hiermee geeft u het mechanisme op dat wordt gebruikt voor het verifiëren van de gebruikers referenties wanneer deze cmdlet gebruikmaakt van het WSMan-protocol. De aanvaardbare waarden voor deze parameter zijn:

- **Basic**
- **CredSSP**
- **Prijs**
- **Samenvatting**
- **Kerberos**
- **Afspraken**

De standaard waarde is **standaard**.

Zie [AuthenticationMechanism Enumeration (Engelstalig)](/dotnet/api/system.management.automation.runspaces.authenticationmechanism)voor meer informatie over de waarden van deze para meter.

> [!WARNING]
> CredSSP-verificatie (Credential Security service provider), waarbij de gebruikers referenties worden door gegeven aan een externe computer die moet worden geverifieerd, is ontworpen voor opdrachten waarvoor verificatie is vereist voor meer dan één bron, zoals het openen van een externe netwerk share.
> Dit mechanisme verhoogt het beveiligings risico van de externe bewerking.
> Als er is geknoeid met de externe computer, kunnen de referenties die aan worden door gegeven, worden gebruikt om > de netwerk sessie te beheren.

Deze para meter is geïntroduceerd in Windows Power Shell 3,0.

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:
Accepted values: Default, Basic, Negotiate, CredSSP, Digest, Kerberos

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

Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable. Zie [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md)voor meer informatie.

## INVOER

### Geen

Deze cmdlet heeft geen para meters die invoer door waarde krijgen.
U kunt de waarden van de eigenschappen **ComputerName** en **newname** van objecten echter door sluizen naar deze cmdlet.

## UITVOER

### Micro soft. Power shell. commands. ComputerChangeInfo

Met deze cmdlet wordt een **ComputerChangeInfo** -object geretourneerd als u de para meter **PassThru** opgeeft.
Anders wordt er geen uitvoer geretourneerd.

## OPMERKINGEN

## GERELATEERDE KOPPELINGEN

[Restart-Computer](Restart-Computer.md)

[Stop-computer](Stop-Computer.md)
