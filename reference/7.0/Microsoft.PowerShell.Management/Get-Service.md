---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 10/30/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/get-service?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-Service
ms.openlocfilehash: ce91313d1b581e3d666c131caaa1cf7ecad0c04f
ms.sourcegitcommit: de63e9481cf8024883060aae61fb02c59c2de662
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/03/2020
ms.locfileid: "93249597"
---
# Get-Service

## SAMENVATTING
Hiermee worden de services op de computer opgehaald.

## SYNTAXIS

### Standaard (standaard instelling)

```
Get-Service [[-Name] <String[]>] [-DependentServices] [-RequiredServices] [-Include <String[]>]
 [-Exclude <String[]>] [<CommonParameters>]
```

### DisplayName

```
Get-Service [-DependentServices] [-RequiredServices] -DisplayName <String[]> [-Include <String[]>]
 [-Exclude <String[]>] [<CommonParameters>]
```

### Input object

```
Get-Service [-DependentServices] [-RequiredServices] [-Include <String[]>] [-Exclude <String[]>]
 [-InputObject <ServiceController[]>] [<CommonParameters>]
```

## BESCHRIJVING

De `Get-Service` cmdlet haalt objecten op die de services op een computer vertegenwoordigen, waaronder het uitvoeren en stoppen van services. Wanneer `Get-Service` wordt uitgevoerd zonder para meters, worden standaard alle services van de lokale computer geretourneerd.

U kunt deze cmdlet gebruiken om alleen bepaalde services op te halen door de service naam of de weergave naam van de services op te geven, of u kunt Service objecten door sluizen naar deze cmdlet.

## VOORBEELDEN

### Voor beeld 1: alle services op de computer ophalen

In dit voor beeld worden alle services op de computer opgehaald. Het gedraagt zich alsof u hebt getypt `Get-Service *` . In de standaard weergave worden de status, de service naam en de weergave naam van elke service weer gegeven.

```powershell
Get-Service
```

### Voor beeld 2: services ophalen die beginnen met een zoek reeks

In dit voor beeld worden services opgehaald met service namen die beginnen met WMI (Windows Management Instrumentation).

```powershell
Get-Service "wmi*"
```

### Voor beeld 3: services weer geven die een zoek reeks bevatten

In dit voor beeld worden de services weer gegeven met een weergave naam die het woord netwerk bevat. Als u zoekt in de weergave naam, worden er netwerkgerelateerde services gevonden, zelfs wanneer de service naam geen netwerk bevat, zoals xmlprov, de Network Provisioning Service.

```powershell
Get-Service -Displayname "*network*"
```

### Voor beeld 4: services ophalen die beginnen met een zoek reeks en een uitsluiting

In dit voor beeld worden alleen de services met service namen opgehaald die beginnen met **Win** , met uitzonde ring van de WinRM-service.

```powershell
Get-Service -Name "win*" -Exclude "WinRM"
```

### Voor beeld 5: services weer geven die momenteel actief zijn

In dit voor beeld worden alleen de services weer gegeven met de status wordt uitgevoerd.

```powershell
Get-Service | Where-Object {$_.Status -eq "Running"}
```

`Get-Service` Hiermee worden alle services op de computer opgehaald en worden de objecten van de pijp lijn omlaag verzonden. De `Where-Object` cmdlet selecteert alleen de services met een **status** eigenschap die gelijk is aan die wordt uitgevoerd.

De status is slechts één eigenschap van service objecten. Als u alle eigenschappen wilt weer geven, typt u `Get-Service | Get-Member` .

### Voor beeld 6: de services op de computer weer geven die afhankelijke services hebben

In dit voor beeld worden services met afhankelijke services opgehaald.

```powershell
Get-Service |
  Where-Object {$_.DependentServices} |
    Format-List -Property Name, DependentServices, @{
      Label="NoOfDependentServices"; Expression={$_.dependentservices.count}
    }
```

```Output
Name                  : AudioEndpointBuilder
DependentServices     : {AudioSrv}
NoOfDependentServices : 1

Name                  : Dhcp
DependentServices     : {WinHttpAutoProxySvc}
NoOfDependentServices : 1
...
```

De `Get-Service` cmdlet haalt alle services op de computer op en verzendt de objecten naar de pijp lijn. De `Where-Object` cmdlet selecteert de services waarvan de eigenschap **DependentServices** niet null is.

De resultaten worden vanuit de pijp lijn naar de `Format-List` cmdlet verzonden. De **eigenschap** para meter geeft de naam van de service, de naam van de afhankelijke services en een berekende eigenschap weer die het aantal afhankelijke services voor elke service weergeeft.

### Voor beeld 7: Services sorteren op eigenschaps waarde

Dit voor beeld laat zien dat wanneer u services in oplopende volg orde sorteert op de waarde van de eigenschap **status** , gestopt services worden weer gegeven voordat Services worden uitgevoerd. De reden hiervoor is dat de waarde van **status** een opsomming is, waarbij gestopt de waarde 1 heeft en de waarde 4 heeft. Zie [ServiceControllerStatus](/dotnet/api/system.serviceprocess.servicecontrollerstatus)voor meer informatie.

Als u eerst actieve services wilt weer geven, gebruikt u de para meter **Aflopend** van de `Sort-Object` cmdlet.

```powershell
Get-Service "s*" | Sort-Object status
```

```Output
Status   Name               DisplayName
------   ----               -----------
Stopped  stisvc             Windows Image Acquisition (WIA)
Stopped  SwPrv              MS Software Shadow Copy Provider
Stopped  SysmonLog          Performance Logs and Alerts
Running  Spooler            Print Spooler
Running  srservice          System Restore Service
Running  SSDPSRV            SSDP Discovery Service
Running  ShellHWDetection   Shell Hardware Detection
Running  Schedule           Task Scheduler
Running  SCardSvr           Smart Card
Running  SamSs              Security Accounts Manager
Running  SharedAccess       Windows Firewall/Internet Connectio...
Running  SENS               System Event Notification
Running  seclogon           Secondary Logon
```

### Voor beeld 8: de afhankelijke services van een service ophalen

In dit voor beeld worden de services opgehaald die voor de WinRM-service zijn vereist. De waarde van de eigenschap **ServicesDependedOn** van de service wordt geretourneerd.

```powershell
Get-Service "WinRM" -RequiredServices
```

### Voor beeld 9: een service ophalen via de pijplijn operator

In dit voor beeld wordt de WinRM-service op de lokale computer opgehaald. De service naam teken reeks tussen aanhalings tekens, wordt naar beneden verzonden naar de pijp lijn `Get-Service` .

```powershell
"WinRM" | Get-Service
```

## PARAMETERS

### -DependentServices

Geeft aan dat met deze cmdlet alleen de services worden opgehaald die afhankelijk zijn van de opgegeven service.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: DS

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### -DisplayName

Hiermee geeft u als een teken reeks matrix de weergave namen op van de services die moeten worden opgehaald. Joker tekens zijn toegestaan.

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

Hiermee wordt een teken reeks matrix opgegeven, een service of services die met deze cmdlet worden uitgesloten van de bewerking.
De waarde van deze para meter komt in aanmerking voor de para meter **name** . Voer een naam element of patroon in, bijvoorbeeld `s*` . Joker tekens zijn toegestaan.

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

Hiermee wordt een teken reeks matrix opgegeven, een service of services die met deze cmdlet in de bewerking zijn opgenomen. De waarde van deze para meter komt in aanmerking voor de para meter **name** . Voer een naam element of patroon in, bijvoorbeeld `s*` . Joker tekens zijn toegestaan.

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

Hiermee geeft u de **ServiceController** -objecten op die de services vertegenwoordigen die moeten worden opgehaald. Voer een variabele in die de objecten bevat, of typ een opdracht of expressie waarmee de objecten worden opgehaald. U kunt een service object door sluizen naar deze cmdlet.

```yaml
Type: System.ServiceProcess.ServiceController[]
Parameter Sets: InputObject
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### -Name

Hiermee geeft u de service namen op van de services die moeten worden opgehaald. Joker tekens zijn toegestaan.

```yaml
Type: System.String[]
Parameter Sets: Default
Aliases: ServiceName

Required: False
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: True
```

### -RequiredServices

Geeft aan dat met deze cmdlet alleen de services worden opgehaald die door deze service zijn vereist. Met deze para meter wordt de waarde van de eigenschap **ServicesDependedOn** van de service opgehaald.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: SDO, ServicesDependedOn

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: True
```

### CommonParameters

Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable. Zie [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)voor meer informatie.

## INVOER

### System. ServiceProcess. ServiceController, System. String

U kunt een service object of een service naam door sluizen naar deze cmdlet.

## UITVOER

### System. ServiceProcess. ServiceController

Deze cmdlet retourneert objecten die de services op de computer vertegenwoordigen.

## OPMERKINGEN

Vanaf Power shell 6,0 worden de volgende eigenschappen toegevoegd aan de **ServiceController** -objecten: **username** , **Description** , **DelayedAutoStart** , **BinaryPathName** en **opstart type** .

U kunt ook verwijzen naar `Get-Service` de ingebouwde alias `gsv` . Zie [about_Aliases](../Microsoft.PowerShell.Core/About/about_Aliases.md)voor meer informatie.

Met deze cmdlet kunnen alleen services worden weer gegeven wanneer de huidige gebruiker gemachtigd is om deze te bekijken. Als met deze cmdlet geen services worden weer gegeven, bent u mogelijk niet gemachtigd om deze weer te geven.

Als u de service naam en de weergave naam van elke service op uw systeem wilt zoeken, typt u `Get-Service` . De service namen worden weer gegeven in de kolom naam en de weergave namen worden weer gegeven in de kolom **DisplayName** .

Wanneer u in oplopende volg orde sorteert op de waarde van de eigenschap **status** , worden de gestopte services weer gegeven voordat u Services uitvoert. De eigenschap **status** van de service is een opsommings waarde en de status namen vertegenwoordigen gehele waarden. De sorteer volgorde is gebaseerd op de gehele waarde, niet de naam. Gestopt wordt weer gegeven voordat de actie wordt uitgevoerd, omdat de waarde is gestopt, en het uitvoeren van de waarde 4. Zie [ServiceControllerStatus](/dotnet/api/system.serviceprocess.servicecontrollerstatus)voor meer informatie.

## GERELATEERDE KOPPELINGEN

[New-Service](New-Service.md)

[Restart-Service](Restart-Service.md)

[Resume-Service](Resume-Service.md)

[Set-Service](Set-Service.md)

[Start-Service](Start-Service.md)

[Stop-Service](Stop-Service.md)

[Suspend-Service](Suspend-Service.md)

[Verwijderen-service](Remove-Service.md)
