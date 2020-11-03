---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 10/14/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/write-verbose?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Write-Verbose
ms.openlocfilehash: fab0d14d8f22227b37d0dabd2287a5cdff13cce7
ms.sourcegitcommit: 16883bb67e34b3915798070f60f974bf85160bd3
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/16/2020
ms.locfileid: "93253053"
---
# Write-Verbose

## SAMENVATTING
Schrijft tekst naar de uitgebreide berichten stroom.

## SYNTAXIS

```
Write-Verbose [-Message] <String> [<CommonParameters>]
```

## BESCHRIJVING

De `Write-Verbose` cmdlet schrijft tekst naar de uitgebreide berichten stroom in Power shell. Normaal gesp roken wordt de uitgebreide berichten stroom gebruikt om meer gedetailleerde informatie over de verwerking van opdrachten te bieden.

De uitgebreide berichten stroom wordt standaard niet weer gegeven, maar u kunt deze weer geven door de waarde van de variabele te wijzigen `$VerbosePreference` of door de **uitgebreide** para meter in een wille keurige opdracht te gebruiken.

## VOORBEELDEN

### Voor beeld 1: een status bericht schrijven

```powershell
Write-Verbose -Message "Searching the Application Event Log."
Write-Verbose -Message "Searching the Application Event Log." -Verbose
```

Deze opdrachten gebruiken de `Write-Verbose` cmdlet om een status bericht weer te geven. Het bericht wordt standaard niet weer gegeven.

De tweede opdracht maakt gebruik van de **uitgebreide** algemene para meter, waarmee alle uitgebreide berichten worden weer gegeven, ongeacht de waarde van de `$VerbosePreference` variabele.

### Voor beeld 2: $VerbosePreference instellen en een status bericht schrijven

```powershell
$VerbosePreference = "Continue"
Write-Verbose "Copying file $filename"
```

Deze opdrachten gebruiken de `Write-Verbose` cmdlet om een status bericht weer te geven. Het bericht wordt standaard niet weer gegeven.

Met de eerste opdracht wordt een waarde van door gaan naar de `$VerbosePreference` Voorkeurs variabele toegewezen. De standaard waarde, `SilentlyContinue` , onderdrukt uitgebreide berichten. Met de tweede opdracht wordt een uitgebreid bericht geschreven.

## PARAMETERS

### -Bericht

Hiermee geeft u het bericht op dat moet worden weer gegeven. Deze parameter is vereist. U kunt ook een bericht teken reeks door sluizen naar `Write-Verbose` .

```yaml
Type: System.String
Parameter Sets: (All)
Aliases: Msg

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### CommonParameters

Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable. Zie [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md)voor meer informatie.

## INVOER

### System. String

U kunt een teken reeks die het bericht bevat door sluizen naar `Write-Verbose` .

## UITVOER

### Geen

`Write-Verbose` schrijft alleen naar de uitgebreide berichten stroom.

## OPMERKINGEN

- Uitgebreide berichten worden alleen geretourneerd als de opdracht de **uitgebreide** para meter common gebruikt. Zie [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)voor meer informatie.
- In Windows Power shell-achtergrond taken en externe opdrachten `$VerbosePreference` wordt met de variabele in de taak sessie en externe sessie bepaald of het uitgebreide bericht standaard wordt weer gegeven.
  Zie about_Preference_Variables voor meer informatie over de `$VerbosePreference` variabele [about_Preference_Variables](../Microsoft.PowerShell.Core/About/about_Preference_Variables.md).

## GERELATEERDE KOPPELINGEN

[about_Output_Streams](../Microsoft.PowerShell.Core/About/about_Output_Streams.md)

[about_Redirection](../Microsoft.PowerShell.Core/About/about_Redirection.md)

[Schrijf fouten opsporen](Write-Debug.md)

[Schrijf fout](Write-Error.md)

[Write-host](Write-Host.md)

[Write-Information](Write-Information.md)

[Write-output](Write-Output.md)

[Schrijf voortgang](Write-Progress.md)

[Waarschuwing voor schrijven](Write-Warning.md)
