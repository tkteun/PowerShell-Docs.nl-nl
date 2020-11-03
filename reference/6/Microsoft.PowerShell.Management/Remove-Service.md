---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/remove-service?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Remove-Service
ms.openlocfilehash: c55a7ef01171e63e8c64ee03446ca1bdcd838e2a
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/07/2020
ms.locfileid: "93251170"
---
# Remove-Service

## SAMENVATTING
Hiermee verwijdert u een Windows-service.

## SYNTAXIS

### Naam (standaard)

```
Remove-Service [-Name] <String> [-WhatIf] [-Confirm] [<CommonParameters>]
```

### Input object

```
Remove-Service [-InputObject <ServiceController>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

## BESCHRIJVING

Met de `Remove-Service` cmdlet wordt een Windows-service in het REGI ster en in de service database verwijderd.

De `Remove-Service` cmdlet is geïntroduceerd in Power shell 6,0.

## VOORBEELDEN

### Voor beeld 1: een service verwijderen

Hiermee verwijdert u een service met de naam TestService.

```powershell
Remove-Service -Name "TestService"
```

### Voor beeld 2: een service verwijderen met de weergave naam

In dit voor beeld wordt een service met de naam TestService verwijderd. De opdracht wordt gebruikt `Get-Service` om een object op te halen dat de TestService-service vertegenwoordigt met behulp van de weergave naam. De pijplijn operator ( `|` ) sluizen het object naar `Remove-Service` , waardoor de service wordt verwijderd.

```powershell
Get-Service -DisplayName "Test Service" | Remove-Service
```

## PARAMETERS

### -Input object

Hiermee geeft u de **ServiceController** -objecten op die de services vertegenwoordigen die moeten worden verwijderd. Voer een variabele in die de objecten bevat, of typ een opdracht of expressie waarmee de objecten worden opgehaald.

```yaml
Type: System.ServiceProcess.ServiceController
Parameter Sets: InputObject
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### -Name

Hiermee geeft u de service namen op van de services die u wilt verwijderen. Joker tekens zijn toegestaan.

```yaml
Type: System.String
Parameter Sets: Name
Aliases: ServiceName, SN

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: True
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

### System. ServiceProcess. ServiceController, System. String

U kunt een service object of een teken reeks die de naam van een service bevat, door sluizen naar deze cmdlet.

## UITVOER

### Geen

Met deze cmdlet wordt geen uitvoer geretourneerd.

## OPMERKINGEN

Als u deze cmdlet wilt uitvoeren, start u Power shell met de optie **als administrator uitvoeren** .

## GERELATEERDE KOPPELINGEN

[Get-Service](Get-Service.md)

[Restart-Service](Restart-Service.md)

[Resume-Service](Resume-Service.md)

[Set-Service](Set-Service.md)

[Start-Service](Start-Service.md)

[Stop-Service](Stop-Service.md)

[Suspend-Service](Suspend-Service.md)
