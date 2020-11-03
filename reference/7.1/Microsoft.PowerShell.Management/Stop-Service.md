---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/stop-service?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Stop-Service
ms.openlocfilehash: b3420a36d81d4e74ea74ecaf7e7a6f782250465e
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/07/2020
ms.locfileid: "93249999"
---
# Stop-Service

## SAMENVATTING
Hiermee worden een of meer actieve services gestopt.

## SYNTAXIS

### Input object (standaard)

```
Stop-Service [-Force] [-NoWait] [-InputObject] <ServiceController[]> [-PassThru] [-Include <String[]>]
 [-Exclude <String[]>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### Standaard

```
Stop-Service [-Force] [-NoWait] [-Name] <String[]> [-PassThru] [-Include <String[]>] [-Exclude <String[]>]
 [-WhatIf] [-Confirm] [<CommonParameters>]
```

### DisplayName

```
Stop-Service [-Force] [-NoWait] [-PassThru] -DisplayName <String[]> [-Include <String[]>] [-Exclude <String[]>]
 [-WhatIf] [-Confirm] [<CommonParameters>]
```

## BESCHRIJVING

De **Stop-Service-** cmdlet verzendt een Stop bericht naar de Windows-service controller voor elk van de opgegeven services.
U kunt de services opgeven met hun service namen of weergave namen, of u kunt de para meter **input object** gebruiken om een service object door te geven dat de service vertegenwoordigt die u wilt stoppen.

## VOORBEELDEN

### Voor beeld 1: een service op de lokale computer stoppen

```
PS C:\> Stop-Service -Name "sysmonlog"
```

Met deze opdracht wordt de Performance Logs and Alerts-service (SysmonLog) op de lokale computer gestopt.

### Voor beeld 2: een service stoppen met de weergave naam

```
PS C:\> Get-Service -DisplayName "telnet" | Stop-Service
```

Met deze opdracht wordt de Telnet-service op de lokale computer gestopt.
De opdracht gebruikt **Get-service** om een object op te halen dat de Telnet-service vertegenwoordigt.
De pijplijn operator (|) sluizen het object om te **stoppen-service** , waardoor de service wordt gestopt.

### Voor beeld 3: een service met afhankelijke services stoppen

```
PS C:\> Get-Service -Name "iisadmin" | Format-List -Property Name, DependentServices
PS C:\> Stop-Service -Name "iisadmin" -Force -Confirm
```

In dit voor beeld wordt de IISAdmin-service op de lokale computer gestopt.
Omdat het stoppen van deze service ook de services stopt die afhankelijk zijn van de IISAdmin-service, is het raadzaam om de service te **stoppen** met een opdracht met een lijst met de services die afhankelijk zijn van de IISADMIN-service.

De eerste opdracht geeft de services weer die afhankelijk zijn van IISAdmin.
Er wordt **Get-service** gebruikt om een object op te halen dat de IISADMIN-service vertegenwoordigt.
De pijplijn operator (|) geeft het resultaat door aan de cmdlet Format-List.
De opdracht gebruikt de *eigenschaps* parameter van de **notatie lijst** om alleen de eigenschappen **name** en **DependentServices** van de service weer te geven.

Met de tweede opdracht wordt de IISAdmin-service gestopt.
De para meter *Force* is vereist voor het stoppen van een service met afhankelijke services.
De opdracht gebruikt de *confirm* -para meter om een bevestiging van de gebruiker aan te vragen voordat de service wordt gestopt.

## PARAMETERS

### -DisplayName

Hiermee geeft u de weergave namen op van de services die moeten worden gestopt.
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

### -Force

Hiermee wordt de cmdlet gedwongen een service te stoppen, zelfs als die service afhankelijke services heeft.

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

### -Include

Hiermee geeft u de services op die met deze cmdlet worden gestopt.
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

### -Input object

Hiermee geeft u de **ServiceController** -objecten op die de services vertegenwoordigen die moeten worden gestopt.
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

Hiermee geeft u de service namen op van de services die moeten worden gestopt.
Joker tekens zijn toegestaan.

```yaml
Type: System.String[]
Parameter Sets: Default
Aliases: ServiceName

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: True
```

### -Wait

Geeft aan dat deze cmdlet de optie geen wait gebruikt.

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

U kunt een service object of een teken reeks die de naam van een service bevat, door sluizen naar deze cmdlet.

## UITVOER

### Geen, System. ServiceProcess. ServiceController

Met deze cmdlet wordt een **System. ServiceProcess. ServiceController** -object gegenereerd dat de service vertegenwoordigt, als u de para meter *PassThru* gebruikt.
Anders wordt met deze cmdlet geen uitvoer gegenereerd.

## OPMERKINGEN

* U kunt ook verwijzen naar **Stop-Service** door de ingebouwde alias, **spsv**. Zie about_Aliases voor meer informatie.

  **Stop-Service** kan alleen services bepalen wanneer de huidige gebruiker gemachtigd is om dit te doen.
Als een opdracht niet correct werkt, beschikt u mogelijk niet over de vereiste machtigingen.

  Als u de service namen wilt zoeken en de namen van de services op uw systeem wilt weer geven, typt u `Get-Service` .
De service namen worden weer gegeven in de kolom **naam** en de weergave namen worden weer gegeven in de kolom **DisplayName** .

*

## GERELATEERDE KOPPELINGEN

[Get-Service](Get-Service.md)

[New-Service](New-Service.md)

[Restart-Service](Restart-Service.md)

[Resume-Service](Resume-Service.md)

[Set-Service](Set-Service.md)

[Start-Service](Start-Service.md)

[Suspend-Service](Suspend-Service.md)

[Verwijderen-service](Remove-Service.md)

