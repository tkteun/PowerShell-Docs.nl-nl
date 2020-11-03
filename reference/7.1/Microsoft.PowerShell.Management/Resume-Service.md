---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/resume-service?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Resume-Service
ms.openlocfilehash: f5bf1eab12b65b6e6ffeeb92c983777a576c503b
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/07/2020
ms.locfileid: "93249918"
---
# Resume-Service

## SAMENVATTING
Hiermee worden een of meer onderbroken (onderbroken) Services hervat.

## SYNTAXIS

### Input object (standaard)

```
Resume-Service [-InputObject] <ServiceController[]> [-PassThru] [-Include <String[]>] [-Exclude <String[]>]
 [-WhatIf] [-Confirm] [<CommonParameters>]
```

### Standaard

```
Resume-Service [-Name] <String[]> [-PassThru] [-Include <String[]>] [-Exclude <String[]>] [-WhatIf] [-Confirm]
 [<CommonParameters>]
```

### DisplayName

```
Resume-Service [-PassThru] -DisplayName <String[]> [-Include <String[]>] [-Exclude <String[]>] [-WhatIf]
 [-Confirm] [<CommonParameters>]
```

## BESCHRIJVING

De cmdlet **Resume-service** stuurt een resume-bericht naar de Windows-service controller voor elk van de opgegeven services.
Als een service wordt onderbroken, wordt deze hervat.
Als deze momenteel wordt uitgevoerd, wordt het bericht genegeerd.
U kunt de services opgeven met hun service namen of weergave namen, of u kunt de para meter *input object* gebruiken om een service object door te geven dat staat voor de services die u wilt hervatten.

## VOORBEELDEN

### Voor beeld 1: een service op de lokale computer hervatten

```
PS C:\> Resume-Service "sens"
```

Met deze opdracht wordt de systeem gebeurtenis meldings service op de lokale computer hervat.
De service naam wordt weer gegeven in de opdracht door Sens.
De opdracht gebruikt de para meter *name* om de service naam van de service op te geven, maar de opdracht laat de parameter naam achterwege omdat de parameter naam optioneel is.

### Voor beeld 2: alle onderbroken services hervatten

```
PS C:\> Get-Service | Where-Object {$_.Status -eq "Paused"} | Resume-Service
```

Met deze opdracht worden alle onderbroken services op de computer hervat.
Met de opdracht cmdlet Get-Service worden alle services op de computer opgehaald.
De pijplijn operator (|) geeft de resultaten door aan de cmdlet Where-Object, die de Services selecteert waarvan de eigenschap **status** is onderbroken.
De volgende pijplijn operator verzendt de resultaten naar **hervatten-service** , waardoor de onderbroken services worden hervat.

In de praktijk gebruikt u de para meter *WhatIf* om het effect van de opdracht te bepalen voordat u deze uitvoert.

## PARAMETERS

### -DisplayName

Hiermee geeft u de weergave namen op van de services die moeten worden hervat.
Joker tekens zijn toegestaan.

```yaml
Type: System.String[]
Parameter Sets: DisplayName
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: True
```

### -Uitsluiten

Hiermee geeft u de services die door deze cmdlet worden wegge laten.
De waarde van deze para meter komt in aanmerking voor de para meter *name* .
Voer een naam element of patroon in, zoals s *.
Joker tekens zijn toegestaan.

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: True
```

### -Include

Hiermee geeft u de services op die u wilt hervatten.
Met de waarde van deze para meter wordt de para meter *name* gekwalificeerd.
Voer een naam element of patroon in, zoals s *.
Joker tekens zijn toegestaan.

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: True
```

### -Input object

Hiermee geeft u de **ServiceController** -objecten op die de services vertegenwoordigen om te hervatten.
Voer een variabele in die de objecten bevat, of typ een opdracht of expressie waarmee de objecten worden opgehaald.

```yaml
Type: System.ServiceProcess.ServiceController[]
Parameter Sets: InputObject
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### -Name

Hiermee geeft u de service namen op van de services die moeten worden hervat.

```yaml
Type: System.String[]
Parameter Sets: Default
Aliases: ServiceName

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### -PassThru

Retourneert een object dat de service vertegenwoordigt.
Deze cmdlet genereert standaard geen uitvoer.

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

### System. ServiceProcess. ServiceController, System. String

U kunt een service object of een teken reeks die een service naam bevat door sluizen naar deze cmdlet.

## UITVOER

### Geen, System. ServiceProcess. ServiceController

Met deze cmdlet wordt een **System. ServiceProcess. ServiceController** -object gegenereerd dat de hervatde service vertegenwoordigt, als u de para meter *PassThru* opgeeft.
Anders wordt met deze cmdlet geen uitvoer gegenereerd.

## OPMERKINGEN

* De status van de services die zijn onderbroken, wordt onderbroken. Wanneer Services worden hervat, wordt de status ervan uitgevoerd.
* **Resume-service** kan alleen services bepalen wanneer de huidige gebruiker gemachtigd is om dit uit te voeren. Als een opdracht niet correct werkt, beschikt u mogelijk niet over de vereiste machtigingen.
* Als u de service namen wilt zoeken en de namen van de services op uw systeem wilt weer geven, typt u `Get-Service` . De service namen worden weer gegeven in de kolom **naam** en de weergave namen worden weer gegeven in de kolom **DisplayName** .

## GERELATEERDE KOPPELINGEN

[Get-Service](Get-Service.md)

[New-Service](New-Service.md)

[Restart-Service](Restart-Service.md)

[Set-Service](Set-Service.md)

[Start-Service](Start-Service.md)

[Stop-Service](Stop-Service.md)

[Suspend-Service](Suspend-Service.md)

[Verwijderen-service](Remove-Service.md)

