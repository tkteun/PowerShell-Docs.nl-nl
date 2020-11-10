---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 4/30/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/set-date?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Set-Date
ms.openlocfilehash: 36e49d36ffe7e4000926cf821767dfb158efcf46
ms.sourcegitcommit: 2c311274ce721cd1072dcf2dc077226789e21868
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 11/10/2020
ms.locfileid: "94387971"
---
# Set-Date

## SAMENVATTING
Hiermee wijzigt u de systeem tijd op de computer naar een tijd die u opgeeft.

## SYNTAXIS

### Datum (standaard)

```
Set-Date [-Date] <DateTime> [-DisplayHint <DisplayHintType>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### Stel

```
Set-Date [-Adjust] <TimeSpan> [-DisplayHint <DisplayHintType>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

## BESCHRIJVING

`Set-Date`Met de cmdlet worden de systeem datum en-tijd op de computer gewijzigd in een datum en tijd die u opgeeft.
U kunt een nieuwe datum en/of tijd opgeven door een teken reeks te typen of door een **DateTime** -of **time span** -object door te geven aan `Set-Date` . Als u een nieuwe datum of tijd wilt opgeven, gebruikt u de para meter **date** .
Als u een wijzigings interval wilt opgeven, gebruikt u de para meter **aanpassen** .

## VOORBEELDEN

### Voor beeld 1: drie dagen aan de systeem datum toevoegen

Met deze opdracht worden drie dagen aan de huidige systeem datum toegevoegd.
Dit heeft geen invloed op de tijd.
De opdracht gebruikt de para meter **date** om de datum op te geven.

De `Get-Date` cmdlet retourneert de huidige datum als een **DateTime** -object. De methode **addDays** van het object **DateTime** voegt een opgegeven aantal dagen (3) toe aan het huidige **DateTime** -object.

```powershell
Set-Date -Date (Get-Date).AddDays(3)
```

### Voor beeld 2: de systeem klok is 10 minuten terug ingesteld

In dit voor beeld wordt de huidige systeem tijd 10 minuten teruggezet.

Met de para meter **aanpassen** kunt u een wijzigings interval (min tien minuten) opgeven in de standaardtijd notatie voor de land instelling.

De para meter **DisplayHint** vertelt Power shell om alleen de tijd weer te geven, maar dit heeft geen invloed op het **DateTime** -object dat `Set-Date` retourneert.

```powershell
Set-Date -Adjust -0:10:0 -DisplayHint Time
```

### Voor beeld 3: de datum en tijd instellen op een variabele waarde

Met deze opdrachten worden de systeem datum en-tijd op de lokale computer gewijzigd in de datum en tijd die zijn opgeslagen in de variabele `$T` . Met de eerste opdracht wordt de datum opgehaald en opgeslagen in `$T` .

De tweede opdracht gebruikt de para meter **date** om het **DateTime** -object door `$T` te geven aan de `Set-Date` cmdlet.

```powershell
$T = Get-Date
Set-Date -Date $T
```

### Voor beeld 4:90 minuten toevoegen aan de systeem klok

Met deze opdrachten wordt de systeem tijd op de lokale computer met 90 minuten voor bereid.

De eerste opdracht gebruikt de `New-TimeSpan` cmdlet om een **time span** -object met een interval van 90 minuten te maken en slaat het op in de `$90mins` variabele.

De tweede opdracht maakt gebruik van de para meter **aanpassen** van `Set-Date` om de datum aan te passen door de waarde van het object **time span** in de `$90mins` variabele.

```powershell
$90mins = New-TimeSpan -Minutes 90
Set-Date -Adjust $90mins
```

## PARAMETERS

### -Aanpassen

Hiermee geeft u de waarde op waarvoor deze cmdlet van de huidige datum en tijd wordt toegevoegd of afgetrokken.
kan een aanpassing in de standaard datum-en tijd notatie voor uw land instelling typen of de para meter **aanpassen** gebruiken om een **time span** -object door te geven van `New-TimeSpan` tot `Set-Date` .

```yaml
Type: System.TimeSpan
Parameter Sets: Adjust
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -Datum

Wijzigt de datum en tijd in de opgegeven waarden.
U kunt een nieuwe datum typen in de korte datum notatie en een tijd in de standaardtijd notatie voor uw land instelling. U kunt ook een **DateTime** -object door geven van `Get-Date` .

Als u een datum opgeeft, maar niet een tijd, `Set-Date` wijzigt de tijd in middernacht op de opgegeven datum. Als u alleen een tijd opgeeft, wordt de datum niet gewijzigd.

```yaml
Type: System.DateTime
Parameter Sets: Date
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### -DisplayHint

Hiermee geeft u op welke elementen van de datum en tijd worden weer gegeven. De acceptabele waarden voor deze para meter zijn:

- **Datum** : alleen de datum weer gegeven.
- **Tijd** : alleen de tijd weer gegeven.
- **DateTime** : geeft de datum en tijd weer.

Deze para meter is alleen van invloed op de weer gave.
Dit heeft geen invloed op het **DateTime** -object dat wordt `Get-Date` opgehaald.

```yaml
Type: Microsoft.PowerShell.Commands.DisplayHintType
Parameter Sets: (All)
Aliases:
Accepted values: Date, Time, DateTime

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

### System. DateTime

U kunt een datum door sluizen naar `Set-Date` .

## UITVOER

### System. DateTime

`Set-Date` retourneert een object dat staat voor de datum die is ingesteld.

## OPMERKINGEN

- Gebruik deze cmdlet voorzichtig bij het wijzigen van de datum en tijd op de computer. De wijziging kan ertoe leiden dat de computer geen systeem gebeurtenissen en updates ontvangt die worden geactiveerd door een datum of tijd. Gebruik de **WhatIf** en **Bevestig** de para meters om fouten te voor komen.
- U kunt standaard .NET-methoden gebruiken met de **DateTime** -en **time span** -objecten die worden gebruikt met `Set-Date` , zoals **addDays** , **AddMonths** en **FromFileTime**. Zie [DateTime-methoden](/dotnet/api/system.datetime) en voor meer informatie

  [Time span-methoden](/dotnet/api/system.timespan) in de .NET SDK.

## GERELATEERDE KOPPELINGEN

[Ophalen datum](Get-Date.md)

[Nieuw-time span](New-TimeSpan.md)
