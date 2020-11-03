---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/read-host?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Read-Host
ms.openlocfilehash: 9017d2352f1d2735f21343f4c1194c5e97ce2848
ms.sourcegitcommit: 57df49488015e7ac17ff1df402a94441aa6d6064
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/08/2020
ms.locfileid: "93251415"
---
# Read-Host

## SAMENVATTING
Hiermee wordt een regel invoer uit de-console gelezen.

## SYNTAXIS

```
Read-Host [[-Prompt] <Object>] [-AsSecureString] [<CommonParameters>]
```

## BESCHRIJVING

De `Read-Host` cmdlet leest een regel invoer van de-console. U kunt deze gebruiken om een gebruiker te vragen om invoer. Omdat u de invoer kunt opslaan als een beveiligde teken reeks, kunt u deze cmdlet gebruiken om gebruikers te vragen voor beveiligde gegevens, zoals wacht woorden, en gedeelde gegevens.

## VOORBEELDEN

### Voor beeld 1: console-invoer opslaan in een variabele

In dit voor beeld wordt de teken reeks "Voer uw leeftijd:" als prompt weer gegeven. Wanneer een waarde wordt ingevoerd en de Enter-toets wordt ingedrukt, wordt de waarde opgeslagen in de `$Age` variabele.

```powershell
$Age = Read-Host "Please enter your age"
```

### Voor beeld 2: de console-invoer opslaan als een veilige teken reeks

In dit voor beeld wordt de teken reeks "Voer een wacht woord:" als prompt weer gegeven. Als er een waarde wordt ingevoerd, worden sterretjes ( `*` ) op de console weer gegeven in plaats van de invoer. Wanneer de Enter-toets wordt ingedrukt, wordt de waarde opgeslagen als een **SecureString** -object in de `$pwd_secure_string` variabele.

```powershell
$pwd_secure_string = Read-Host "Enter a Password" -AsSecureString
```

## PARAMETERS

### -AsSecureString

Geeft aan dat de cmdlet sterretjes ( `*` ) weergeeft in plaats van de tekens die de gebruiker typt als invoer. Wanneer u deze para meter gebruikt, is de uitvoer van de `Read-Host` cmdlet een **SecureString** -object ( **System. Security. SecureString** ).

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

### -Prompt

Hiermee geeft u de tekst van de prompt.
Typ een teken reeks.
Als de teken reeks spaties bevat, plaatst u deze tussen aanhalings tekens.
Power shell voegt een dubbele punt ( `:` ) toe aan de tekst die u invoert.

```yaml
Type: System.Object
Parameter Sets: (All)
Aliases:

Required: False
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### CommonParameters

Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable. Zie [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)voor meer informatie.

## INVOER

### Geen

U kunt geen invoer van een pipe naar deze cmdlet.

## UITVOER

### System. String of System. Security. SecureString

Als de para meter **AsSecureString** wordt gebruikt, `Read-Host` retourneert een **SecureString**. Anders wordt een teken reeks geretourneerd.

## OPMERKINGEN

## GERELATEERDE KOPPELINGEN

[Wissen-host](../microsoft.powershell.core/clear-host.md)

[Get-host](Get-Host.md)

[Write-host](Write-Host.md)

[ConvertFrom-SecureString](../Microsoft.PowerShell.Security/ConvertFrom-SecureString.md)
