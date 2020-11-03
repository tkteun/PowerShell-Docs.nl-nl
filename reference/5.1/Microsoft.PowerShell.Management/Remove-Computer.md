---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 04/04/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/remove-computer?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Remove-Computer
ms.openlocfilehash: 89e43220a8d5ac675ea232db09cf3edec2ca2b97
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/07/2020
ms.locfileid: "93250583"
---
# Remove-Computer

## SAMENVATTING
Hiermee verwijdert u de lokale computer uit het domein.

## SYNTAXIS

### Lokaal (standaard)

```
Remove-Computer [[-UnjoinDomainCredential] <PSCredential>] [-Restart] [-Force] [-PassThru]
 [-WorkgroupName <String>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### Extern

```
Remove-Computer -UnjoinDomainCredential <PSCredential> [-LocalCredential <PSCredential>] [-Restart]
 [-ComputerName <String[]>] [-Force] [-PassThru] [-WorkgroupName <String>] [-WhatIf] [-Confirm]
 [<CommonParameters>]
```

## BESCHRIJVING

De `Remove-Computer` cmdlet verwijdert de lokale computer en de externe computers uit hun huidige domeinen.

Wanneer u een computer uit een domein verwijdert, `Remove-Computer` schakelt u ook het domein account van de computer uit. U moet expliciete referenties opgeven om de computer uit het domein te ontkoppelen, zelfs wanneer de referenties van de huidige gebruiker zijn. U moet de computer opnieuw opstarten om de wijziging van kracht te laten worden. Wanneer u een computer uit een domein verwijdert, moet u ook deze naar een werk groep verplaatsen. Gebruik de para meter **werkgroepsjablonen** om de werk groep op te geven.

Als u een computer wilt verplaatsen van een werk groep naar een domein, van de ene werk groep naar een andere of van het ene naar het andere domein, gebruikt u de `Add-Computer` cmdlet.

Als u de resultaten van de opdracht wilt weer geven, gebruikt u de para meters **uitgebreid** en **PassThru** . Gebruik de para meter **Force** om de gebruikers prompt te onderdrukken.

`Remove-Computer` Hiermee verwijdert u de lokale computer en de externe computers uit domeinen. Het bevat referentie parameters waarmee alternatieve referenties worden opgegeven voor het maken van verbinding met externe computers en het ontkoppelen van een domein, een **restart** -para meter voor het opnieuw opstarten van de betrokken computers en een **werkgroeps** parameter voor het opgeven van de naam van de werk groep waaraan computers worden toegevoegd.

## VOORBEELDEN

### Voor beeld 1: de lokale computer uit het domein verwijderen

In dit voor beeld wordt de lokale computer verwijderd van het domein waaraan deze is gekoppeld.

```powershell
Remove-Computer -UnjoinDomaincredential Domain01\Admin01 -PassThru -Verbose -Restart
```

De para meter **UnjoinDomainCredential** geeft de referenties van een domein beheerder. De **PassThru** -en de **uitgebreide** para meters geven informatie weer over het slagen of mislukken van de opdracht. Met de para meter **restart** wordt de computer opnieuw opgestart om de Verwijder bewerking te volt ooien.

Als er geen werkgroepnaam is opgegeven, wordt de computer verplaatst naar de werk groep met de naam nadat deze is verwijderd uit het domein.

### Voor beeld 2: meerdere computers verplaatsen naar een verouderde werk groep

In dit voor beeld worden alle computers die worden vermeld in het `OldServers.txt` bestand uit hun domeinen verwijderd en verplaatst naar de **verouderde** werk groep.

```powershell
Remove-Computer -ComputerName (Get-Content OldServers.txt) -LocalCredential Domain01\Admin01 -UnJoinDomainCredential Domain01\Admin01 -WorkgroupName "Legacy" -Force -Restart
```

De para meter **LocalCredential** geeft de referenties van een gebruiker die gemachtigd is om verbinding te maken met externe computers. De para meter **UnjoinDomainCredential** biedt de referenties van een gebruiker die gemachtigd is om de computers uit hun domeinen te verwijderen. De **Force** -para meter onderdrukt de bevestigings prompts voor elke computer. De para meter **restart** start elke computer opnieuw op nadat deze is verwijderd uit het domein.

### Voor beeld 3: computers verwijderen uit een werk groep zonder bevestiging

In dit voor beeld worden de externe computer, Server01 en de lokale computer uit hun domeinen verwijderd en toegevoegd aan de **lokale** werk groep.

```powershell
Remove-Computer -ComputerName "Server01", "localhost" -UnjoinDomainCredential Domain01\Admin01 -WorkgroupName "Local" -Restart -Force
```

De **Force** -para meter onderdrukt de bevestigings prompt voor elke computer. De para meter **restart** start de computers opnieuw op om de wijziging van kracht te laten worden.

## PARAMETERS

### -ComputerName

Hiermee geeft u de computers op die uit hun domeinen moeten worden verwijderd. Standaard is dit de lokale computer.

Typ de NetBIOS-naam, een IP-adres of een Fully Qualified Domain Name (FQDN) van de externe computers. Als u de lokale computer wilt opgeven, typt u de naam van de computer, een punt (.) of localhost.

Deze para meter is niet afhankelijk van externe communicatie met Power shell. U kunt de para meter **ComputerName** gebruiken `Remove-Computer` , zelfs als uw computer niet is geconfigureerd om externe opdrachten uit te voeren.

Deze para meter is geïntroduceerd in Power Shell 3,0.

```yaml
Type: System.String[]
Parameter Sets: Remote
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### -Force

Onderdrukt de gebruikers prompt. Standaard wordt `Remove-Computer` u gevraagd om bevestiging voordat elke computer wordt verwijderd.

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

Hiermee geeft u een gebruikers account op dat is gemachtigd om verbinding te maken met de computers die door de para meter **ComputerName** worden opgegeven. Standaard is dit de huidige gebruiker.

Typ een gebruikers naam, zoals `User01` of `Domain01\User01` , of voer een **PSCredential** -object in, zoals het certificaat dat is gegenereerd door de `Get-Credential` cmdlet. Als u een gebruikers naam typt, wordt u door de cmdlet gevraagd om een wacht woord. Als u een gebruikers account wilt opgeven dat is gemachtigd om de computer uit het huidige domein te verwijderen, gebruikt u de para meter **UnjoinDomainCredential** .

Deze para meter is geïntroduceerd in Power Shell 3,0.

```yaml
Type: System.Management.Automation.PSCredential
Parameter Sets: Remote
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -PassThru

Retourneert de resultaten van de opdracht. Anders wordt met deze cmdlet geen uitvoer gegenereerd.

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

Geeft aan dat met deze cmdlet de computers worden gestart die worden verwijderd. Het is vaak nood zakelijk om opnieuw op te starten om de wijziging van kracht te laten worden.

Deze para meter is geïntroduceerd in Power Shell 3,0.

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

### -UnjoinDomainCredential

Hiermee geeft u een gebruikers account op dat gemachtigd is om de computers uit hun huidige domeinen te verwijderen.
Expliciete referenties, zoals opgegeven door deze para meter, zijn vereist voor het verwijderen van externe computers uit een domein, zelfs wanneer de waarde de referenties van de huidige gebruiker is.

Typ een gebruikers naam, zoals gebruiker01 of Domain01\User01, of voer een **PSCredential** -object in, bijvoorbeeld het account dat door wordt gegenereerd `Get-Credential` . Als u een gebruikers naam typt, vraagt deze cmdlet u om een wacht woord.

Als u een gebruikers account wilt opgeven dat is gemachtigd om verbinding te maken met de externe computers, gebruikt u de para meter **LocalCredential** .

Deze para meter is geïntroduceerd in Power Shell 3,0.

```yaml
Type: System.Management.Automation.PSCredential
Parameter Sets: Local, Remote
Aliases: Credential

Required: False (Local), True (Remote)
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Werkgroepnaam

Hiermee geeft u de naam van een werk groep waaraan de computers worden toegevoegd wanneer deze uit hun domeinen worden verwijderd. De standaard waarde is **werk groep**. Wanneer u een computer uit een domein verwijdert, moet u deze toevoegen aan een werk groep.

Deze para meter is geïntroduceerd in Power Shell 3,0.

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

### System. String

U kunt computer namen door sluizen naar thiscmdlet.

## UITVOER

### Micro soft. Power shell. commands. ComputerChangeInfo

Wanneer u de para meter **PassThru** gebruikt, `Remove-Computer` wordt een **ComputerChangeInfo** -object geretourneerd.
Anders wordt met deze cmdlet geen uitvoer gegenereerd.

## OPMERKINGEN

Met deze cmdlet worden geen computers uit werk groepen verwijderd.

## GERELATEERDE KOPPELINGEN

[Add-computer](Add-Computer.md)

[Checkpoint-Computer](Checkpoint-Computer.md)

[Verwijderen-computer](Remove-Computer.md)

[Naam wijzigen-computer](Rename-Computer.md)

[Restart-Computer](Restart-Computer.md)

[Herstellen-computer](Restore-Computer.md)

[Stop-computer](Stop-Computer.md)

[Test-Connection](Test-Connection.md)
