---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/restart-service?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Restart-Service
ms.openlocfilehash: fee113e20b178c2b86b8f95cd3147f991aed8efe
ms.sourcegitcommit: 177ae45034b58ead716853096b2e72e4864e6df6
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 11/07/2020
ms.locfileid: "94346629"
---
# Restart-Service

## SAMENVATTING
Stopt en start een of meer services.

## SYNTAXIS

### Input object (standaard)

```
Restart-Service [-Force] [-InputObject] <ServiceController[]> [-PassThru] [-Include <String[]>]
 [-Exclude <String[]>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### Standaard

```
Restart-Service [-Force] [-Name] <String[]> [-PassThru] [-Include <String[]>] [-Exclude <String[]>] [-WhatIf]
 [-Confirm] [<CommonParameters>]
```

### DisplayName

```
Restart-Service [-Force] [-PassThru] -DisplayName <String[]> [-Include <String[]>] [-Exclude <String[]>]
 [-WhatIf] [-Confirm] [<CommonParameters>]
```

## BESCHRIJVING

De `Restart-Service` cmdlet verzendt een Stop bericht en vervolgens een start bericht naar de Windows-service controller voor een opgegeven service. Als een service al is gestopt, wordt deze gestart zonder dat u wordt gewaarschuwd als er een fout optreedt. U kunt de services opgeven met hun service namen of weergave namen, of u kunt de para meter **input object** gebruiken om een object door te geven dat elke service vertegenwoordigt die u opnieuw wilt opstarten.

## VOORBEELDEN

### Voor beeld 1: een service opnieuw starten op de lokale computer

```powershell
PS C:\> Restart-Service -Name winmgmt
```

Met deze opdracht wordt de Windows Management Instrumentation service (WinMgmt) opnieuw gestart op de lokale computer.

### Voor beeld 2: een service uitsluiten

```powershell
PS C:\> Restart-Service -DisplayName "net*" -Exclude "net logon"
```

Met deze opdracht worden de services die een weergave naam hebben die begint met net, met uitzonde ring van de Net Logon-service opnieuw gestart.

### Voor beeld 3: alle gestopt netwerk services starten

```powershell
PS C:\> Get-Service -Name "net*" | Where-Object {$_.Status -eq "Stopped"} | Restart-Service
```

Met deze opdracht worden alle gestopte netwerk services op de computer gestart.

Met deze opdracht wordt de `Get-Service` cmdlet gebruikt om objecten op te halen die de services vertegenwoordigen waarvan de service naam begint met net. De pijplijn operator ( `|` ) verzendt het object Services naar de `Where-Object` cmdlet, waarmee alleen de services worden geselecteerd die de status gestopt hebben. Een andere pijplijn operator verzendt de geselecteerde services naar `Restart-Service` .

In de praktijk gebruikt u de para meter **WhatIf** om het effect van de opdracht te bepalen voordat u deze uitvoert.

## PARAMETERS

### -DisplayName

Hiermee geeft u de weergave namen op van de services die opnieuw moeten worden gestart. Joker tekens zijn toegestaan.

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

Hiermee geeft u de services die door deze cmdlet worden wegge laten. De waarde van deze para meter komt in aanmerking voor de para meter **name** . Voer een naam element of patroon in, zoals s *. Joker tekens zijn toegestaan.

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

Hiermee wordt de opdracht uitgevoerd zonder dat de gebruiker om bevestiging wordt gevraagd.

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

Hiermee geeft u de services op die met deze cmdlet opnieuw worden gestart. De waarde van deze para meter komt in aanmerking voor de para meter **name** . Voer een naam element of patroon in, zoals s *. Joker tekens zijn toegestaan.

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

Hiermee geeft u **ServiceController** -objecten op die de services vertegenwoordigen die opnieuw moeten worden gestart. Voer een variabele in die de objecten bevat, of typ een opdracht of expressie waarmee de objecten worden opgehaald.

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

Hiermee geeft u de service namen op van de services die opnieuw moeten worden gestart.

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

### -PassThru

Retourneert een object dat de service vertegenwoordigt. Deze cmdlet genereert standaard geen uitvoer.

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

U kunt een service object of een teken reeks die een service naam bevat door sluizen naar deze cmdlet.

## UITVOER

### Geen, System. ServiceProcess. ServiceController

Met deze cmdlet wordt een **System. ServiceProcess. ServiceController** -object gegenereerd dat de opnieuw gestarte service vertegenwoordigt als u de para meter **PassThru** opgeeft. Anders wordt met deze cmdlet geen uitvoer gegenereerd.

## OPMERKINGEN

Deze cmdlet is alleen beschikbaar op Windows-platforms.

- `Restart-Service` kan alleen services bepalen wanneer de huidige gebruiker gemachtigd is om dit te doen. Als een opdracht niet correct werkt, beschikt u mogelijk niet over de vereiste machtigingen.
- Als u de service namen wilt zoeken en de namen van de services op uw systeem wilt weer geven, typt u `Get-Service` '.
  De service namen worden weer gegeven in de kolom **naam** en de weergave namen worden weer gegeven in de kolom **DisplayName** .

## GERELATEERDE KOPPELINGEN

[Get-Service](Get-Service.md)

[New-Service](New-Service.md)

[Resume-Service](Resume-Service.md)

[Set-Service](Set-Service.md)

[Start-Service](Start-Service.md)

[Stop-Service](Stop-Service.md)

[Suspend-Service](Suspend-Service.md)

[Verwijderen-service](Remove-Service.md)
