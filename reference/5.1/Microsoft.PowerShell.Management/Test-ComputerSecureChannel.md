---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/test-computersecurechannel?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Test-ComputerSecureChannel
ms.openlocfilehash: 20ea76e725a8ab53d7090078dc819a6297a639ff
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/07/2020
ms.locfileid: "93250529"
---
# Test-ComputerSecureChannel

## SAMENVATTING
Test en herstelt het beveiligde kanaal tussen de lokale computer en het bijbehorende domein.

## SYNTAXIS

```
Test-ComputerSecureChannel [-Repair] [-Server <String>] [-Credential <PSCredential>] [-WhatIf] [-Confirm]
 [<CommonParameters>]
```

## BESCHRIJVING
Met de cmdlet **test-ComputerSecureChannel** wordt gecontroleerd of het kanaal tussen de lokale computer en het domein correct werkt door de status van de vertrouwens relaties te controleren.
Als een verbinding mislukt, kunt u de *herstel* parameter gebruiken om te proberen deze te herstellen.

**Test-ComputerSecureChannel** retourneert $True als het kanaal correct werkt en $False als dat niet het geval is.
Dit leidt ertoe dat u de cmdlet kunt gebruiken in voorwaardelijke instructies in functies en scripts.
Gebruik de para meter *uitgebreid* om meer gedetailleerde test resultaten te krijgen.

Deze cmdlet werkt op ongeveer dezelfde manier als NetDom.exe.
Zowel NetDom als **test-ComputerSecureChannel** gebruiken de **Netlogon** -service om de acties uit te voeren.

## VOORBEELDEN

### Voor beeld 1: een kanaal testen tussen de lokale computer en het bijbehorende domein

```
PS C:\> Test-ComputerSecureChannel
True
```

Met deze opdracht wordt het kanaal getest tussen de lokale computer en het domein waarvan deze deel uitmaakt.

### Voor beeld 2: een kanaal testen tussen de lokale computer en een domein controller

```
PS C:\> Test-ComputerSecureChannel -Server "DCName.fabrikam.com"
True
```

Met deze opdracht geeft u een voorkeurs domein controller voor de test op.

### Voor beeld 3: het kanaal tussen de lokale computer en het domein opnieuw instellen

```
PS C:\> Test-ComputerSecureChannel -Repair
True
```

Met deze opdracht wordt het kanaal tussen de lokale computer en het domein opnieuw ingesteld.

### Voor beeld 4: gedetailleerde informatie over de test weer geven

```
PS C:\> Test-ComputerSecureChannel -verbose
VERBOSE: Performing operation "Test-ComputerSecureChannel" on Target "SERVER01".
True
VERBOSE: "The secure channel between 'SERVER01' and 'net.fabrikam.com' is alive and working correctly."
```

Met deze opdracht wordt de *uitgebreide* algemene para meter gebruikt om gedetailleerde berichten over de bewerking aan te vragen.
Zie about_CommonParameters voor meer informatie over *uitgebreid*.

### Voor beeld 5: een verbinding testen voordat u een script uitvoert

```
PS C:\> Set-Alias tcsc Test-ComputerSecureChannel
if (!(tcsc))
{Write-Host "Connection failed. Reconnect and retry."}
else { &(.\Get-Servers.ps1) }
```

In dit voor beeld ziet u hoe u **test-ComputerSecureChannel** gebruikt om een verbinding te testen voordat u een script uitvoert dat de verbinding vereist.

De eerste opdracht gebruikt de cmdlet Set-Alias om een alias te maken voor de naam van de cmdlet.
Dit bespaart ruimte en voor komt het typen van fouten.

De **if** -instructie controleert de waarde die door **test-ComputerSecureChannel** wordt geretourneerd voordat een script wordt uitgevoerd.

## PARAMETERS

### -Credential
Hiermee geeft u een gebruikers account op dat is gemachtigd om deze actie uit te voeren.
Typ een gebruikers naam, zoals gebruiker01 of Domain01\User01, of voer een **PSCredential** -object in, bijvoorbeeld een account dat door de Get-Credential cmdlet wordt geretourneerd.
De cmdlet maakt standaard gebruik van de referenties van de huidige gebruiker.

De *referentie* parameter is ontworpen voor gebruik in opdrachten die gebruikmaken van de *herstel* parameter voor het herstellen van het kanaal tussen de computer en het domein.

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

### -Herstellen
Hiermee wordt aangegeven dat met deze cmdlet het kanaal dat door de NetLogon-service is ingesteld, wordt verwijderd en opnieuw gemaakt.
Gebruik deze para meter om een verbinding te herstellen waarvan de test is mislukt.

Als u deze para meter wilt gebruiken, moet de huidige gebruiker lid zijn van de groep Administrators op de lokale computer.

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

### -Server
Hiermee geeft u de domein controller waarop de opdracht moet worden uitgevoerd.
Als deze para meter niet wordt opgegeven, wordt met deze cmdlet een standaard domein controller voor de bewerking geselecteerd.

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

### Geen
U kunt geen invoer van een pipe naar deze cmdlet.

## UITVOER

### System. Boolean
Deze cmdlet retourneert $True als de verbinding goed werkt en $False als dat niet het geval is.

## OPMERKINGEN

* Als u een **test-ComputerSecureChannel** opdracht wilt uitvoeren in Windows Vista en latere versies van het Windows-besturings systeem, opent u Windows Power shell met de optie als administrator uitvoeren.
* **Test-ComputerSecureChannel** wordt geïmplementeerd met behulp van de functie **I_NetLogonControl2** , waarmee verschillende aspecten van de Netlogon-service worden beheerd.

## GERELATEERDE KOPPELINGEN

[Checkpoint-Computer](Checkpoint-Computer.md)

[Reset-ComputerMachinePassword](Reset-ComputerMachinePassword.md)

[Restart-Computer](Restart-Computer.md)

[Stop-computer](Stop-Computer.md)
