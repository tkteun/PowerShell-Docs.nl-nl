---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/reset-computermachinepassword?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Reset-ComputerMachinePassword
ms.openlocfilehash: 1484bc83b9503ce43420b833a1b78b3c4215d98a
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/07/2020
ms.locfileid: "93250565"
---
# Reset-ComputerMachinePassword

## SAMENVATTING
Hiermee stelt u het wacht woord van het computer account voor de computer opnieuw in.

## SYNTAXIS

```
Reset-ComputerMachinePassword [-Server <String>] [-Credential <PSCredential>] [-WhatIf] [-Confirm]
 [<CommonParameters>]
```

## BESCHRIJVING
De cmdlet **Reset-ComputerMachinePassword** wijzigt het wacht woord voor het computer account dat de computers gebruiken om te verifiëren bij de domein controllers in het domein.
U kunt deze gebruiken om het wacht woord van de lokale computer opnieuw in te stellen.

## VOORBEELDEN

### Voor beeld 1: het wacht woord voor de lokale computer opnieuw instellen

```
PS C:\> Reset-ComputerMachinePassword
```

Met deze opdracht wordt het computer wachtwoord voor de lokale computer opnieuw ingesteld.
De opdracht wordt uitgevoerd met de referenties van de huidige gebruiker.

### Voor beeld 2: het wacht woord voor de lokale computer opnieuw instellen met behulp van een opgegeven domein controller

```
PS C:\> Reset-ComputerMachinePassword -Server "DC01" -Credential Domain01\Admin01
```

Met deze opdracht wordt het computer wachtwoord van de lokale computer opnieuw ingesteld met behulp van de DC01-domein controller.
De para meter *Credential* wordt gebruikt om een gebruikers account op te geven dat gemachtigd is om een computer wachtwoord opnieuw in te stellen in het domein.

### Voor beeld 3: het wacht woord opnieuw instellen op een externe computer

```
$cred = Get-Credential
PS C:\> Invoke-Command -ComputerName "Server01" -ScriptBlock {Reset-ComputerMachinePassword -Credential $using:cred}
```

Met deze opdracht wordt de cmdlet Invoke-Command uitgevoerd om de opdracht **Reset-ComputerMachinePassword** uit te voeren op de externe computer met Server01.

Zie about_Remote en **invoke-Command** voor meer informatie over externe opdrachten in Windows Power shell.

## PARAMETERS

### -Credential
Hiermee geeft u een gebruikers account op dat is gemachtigd om deze actie uit te voeren.
Standaard is dit de huidige gebruiker.

Typ een gebruikers naam, zoals gebruiker01 of Domain01\User01, of voer een **PSCredential** -object in, zoals het account dat is gegenereerd door de cmdlet Get-Credential.
Als u een gebruikers naam typt, vraagt deze cmdlet u om een wacht woord.

Deze para meter is geïntroduceerd in Windows Power Shell 3,0.

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

### -Server
Hiermee geeft u de naam op van een domein controller die moet worden gebruikt wanneer deze cmdlet het wacht woord van het computer account instelt.

Deze parameter is optioneel.
Als u deze para meter weglaat, wordt er een domein controller gekozen voor het onderhouden van de opdracht.

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

### Geen
Met deze cmdlet wordt geen uitvoer gegenereerd.

## OPMERKINGEN

## GERELATEERDE KOPPELINGEN

## GERELATEERDE KOPPELINGEN
