---
external help file: System.Management.Automation.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/out-null?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Out-Null
ms.openlocfilehash: 5a949629cdf0f0822866863822e82e70fc38d8c2
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/07/2020
ms.locfileid: "93250162"
---
# Out-Null

## SAMENVATTING
Hiermee verbergt u de uitvoer in plaats van deze te verzenden naar de pijp lijn of weer te geven.

## SYNTAXIS

```
Out-Null [-InputObject <PSObject>] [<CommonParameters>]
```

## BESCHRIJVING
Met de cmdlet **out-null** wordt de uitvoer naar null verzonden, in feite verwijderd uit de pijp lijn en wordt voor komen dat de uitvoer op het scherm wordt weer gegeven. Dit is alleen van invloed op de standaard uitvoer stroom.
Andere uitvoer stromen, zoals de fout stroom, worden niet beïnvloed. Uitzonde ringen worden weer gegeven. Dit maakt het gemakkelijker om uw opdracht te testen op fouten.

## VOORBEELDEN

### Voor beeld 1: uitvoer verwijderen

```
PS C:\> Get-ChildItem | Out-Null
```

Met deze opdracht worden items in de huidige locatie/map opgehaald, maar de uitvoer wordt niet via de pijp lijn door gegeven en wordt niet weer gegeven op de opdracht regel.
Dit is handig voor het verbergen van de uitvoer die u niet nodig hebt.

## PARAMETERS

### -Input object
Hiermee geeft u het object op dat naar NULL moet worden verzonden (verwijderd uit de pijp lijn).
Voer een variabele in die de objecten bevat, of typ een opdracht of expressie waarmee de objecten worden opgehaald.

```yaml
Type: System.Management.Automation.PSObject
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### CommonParameters
Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable. Zie [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)voor meer informatie.

## INVOER

### System. Management. Automation. PSObject
U kunt elk object door sluizen naar deze cmdlet.

## UITVOER

### Geen
Met deze cmdlet wordt geen uitvoer gegenereerd.

## OPMERKINGEN

* De cmdlets die de **out** -bewerking (de **out** -cmdlets) bevatten, hebben geen para meters voor namen of bestands paden. Als u gegevens wilt verzenden naar een **out** -cmdlet, gebruikt u een pijplijn operator (|) om de uitvoer van een Windows Power shell-opdracht naar de cmdlet te verzenden. U kunt ook gegevens in een variabele opslaan en de para meter *input object* gebruiken om de gegevens door te geven aan de cmdlet. Zie de voor beelden voor meer informatie.
* **Out-null** retourneert geen output-objecten. Als u de uitvoer van **out-null** naar de cmdlet voor Get-Member haalt, rapporten **ophalen van leden** dat er geen objecten zijn opgegeven.

## GERELATEERDE KOPPELINGEN

[Out-standaard](Out-Default.md)

[Out-host](Out-Host.md)
