---
external help file: Microsoft.PowerShell.Commands.Diagnostics.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Diagnostics
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.diagnostics/new-winevent?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: New-WinEvent
ms.openlocfilehash: 202d1792769dcdcda7a156621bfc50c89a1a92ac
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/07/2020
ms.locfileid: "93249938"
---
# New-WinEvent

## SAMENVATTING

Hiermee maakt u een nieuwe Windows-gebeurtenis voor de opgegeven gebeurtenis provider.

## SYNTAXIS

```
New-WinEvent [-ProviderName] <String> [-Id] <Int32> [-Version <Byte>] [[-Payload] <Object[]>]
 [<CommonParameters>]
```

## BESCHRIJVING

Met de cmdlet **New-Wine vent** maakt u een gebeurtenis Event Tracing for Windows (etw) voor een gebeurtenis provider.
U kunt deze cmdlet gebruiken om gebeurtenissen toe te voegen aan ETW-kanalen vanuit Windows Power shell.

## VOORBEELDEN

### Voorbeeld 1

```powershell
PS C:\> New-WinEvent -ProviderName Microsoft-Windows-PowerShell -Id 45090 -Payload @("Workflow", "Running")
```

Met deze opdracht wordt de cmdlet **New-Wine vent** gebruikt voor het maken van gebeurtenis 45090 voor de micro soft-Windows-Power shell-provider.

## PARAMETERS

### -Id

Hiermee geeft u een gebeurtenis-id op die is geregistreerd via een instrumentatie manifest.

```yaml
Type: System.Int32
Parameter Sets: (All)
Aliases:

Required: True
Position: 2
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Payload

Hiermee geeft u het bericht voor de gebeurtenis op. Wanneer de gebeurtenis naar een gebeurtenis logboek wordt geschreven, wordt de payload opgeslagen in de **bericht** eigenschap van het gebeurtenis object.

Wanneer de opgegeven Payload niet overeenkomt met de payload in de gebeurtenis definitie, wordt er door Windows Power shell een waarschuwing gegenereerd, maar de opdracht wordt nog steeds uitgevoerd.

```yaml
Type: System.Object[]
Parameter Sets: (All)
Aliases:

Required: False
Position: 3
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -ProviderName

Hiermee geeft u de gebeurtenis provider die de gebeurtenis naar een gebeurtenis logboek schrijft, zoals "micro soft-Windows-Power shell". Een ETW-gebeurtenis provider is een logische entiteit die gebeurtenissen naar ETW-sessies schrijft.

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: True
Position: 1
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Versie

Hiermee geeft u het versie nummer van de gebeurtenis. Typ het nummer van de gebeurtenis. Windows Power shell converteert het getal naar het vereiste byte type.

Met deze para meter kunt u een gebeurtenis opgeven wanneer verschillende versies van dezelfde gebeurtenis worden gedefinieerd.

```yaml
Type: System.Byte
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### CommonParameters

Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable. Zie [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)voor meer informatie.

## INVOER

### Geen

Deze cmdlet neemt geen invoer van de pijp lijn.

## UITVOER

### Geen

Met deze cmdlet wordt een uitvoer gegenereerd.

## OPMERKINGEN

* Nadat de provider de gebeurtenis naar een gebeurtenis logboek heeft geschreven, kunt u de Get-WinEvent-cmdlet gebruiken om het evenement op te halen uit het logboek.

## GERELATEERDE KOPPELINGEN

[Get-WinEvent](Get-WinEvent.md)
