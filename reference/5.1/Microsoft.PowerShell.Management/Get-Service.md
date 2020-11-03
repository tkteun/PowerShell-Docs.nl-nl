---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/get-service?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-Service
ms.openlocfilehash: 0c007f1becd7364806cfd47e18cf05995b81e0f7
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/07/2020
ms.locfileid: "93250792"
---
# Get-Service

## SAMENVATTING
Hiermee worden de services op een lokale of externe computer opgehaald.

## SYNTAXIS

### Standaard (standaard instelling)

```
Get-Service [[-Name] <String[]>] [-ComputerName <String[]>] [-DependentServices] [-RequiredServices]
 [-Include <String[]>] [-Exclude <String[]>] [<CommonParameters>]
```

### DisplayName

```
Get-Service [-ComputerName <String[]>] [-DependentServices] [-RequiredServices] -DisplayName <String[]>
 [-Include <String[]>] [-Exclude <String[]>] [<CommonParameters>]
```

### Input object

```
Get-Service [-ComputerName <String[]>] [-DependentServices] [-RequiredServices] [-Include <String[]>]
 [-Exclude <String[]>] [-InputObject <ServiceController[]>] [<CommonParameters>]
```

## BESCHRIJVING

Met de cmdlet **Get-service** worden objecten opgehaald die de services op een lokale computer of op een externe computer vertegenwoordigen, waaronder het uitvoeren en stoppen van services.

U kunt deze cmdlet gebruiken om alleen bepaalde services op te halen door de service naam of de weergave naam van de services op te geven, of u kunt Service objecten door sluizen naar deze cmdlet.

## VOORBEELDEN

### Voor beeld 1: alle services op de computer ophalen

```powershell
Get-Service
```

Met deze opdracht worden alle services op de computer opgehaald.
Het gedraagt zich alsof u hebt getypt `Get-Service *` .
In de standaard weergave worden de status, de service naam en de weergave naam van elke service weer gegeven.

### Voor beeld 2: services ophalen die beginnen met een zoek reeks

```powershell
Get-Service "wmi*"
```

Met deze opdracht worden services opgehaald met service namen die beginnen met WMI (de acroniem voor Windows Management Instrumentation).

### Voor beeld 3: services weer geven die een zoek reeks bevatten

```powershell
Get-Service -Displayname "*network*"
```

Met deze opdracht worden de services weer gegeven met een weergave naam die het woord netwerk bevat.
Als u zoekt in de weergave naam, worden er netwerkgerelateerde services gevonden, zelfs wanneer de service naam geen ' net ' bevat, zoals xmlprov, de Network Provisioning Service.

### Voor beeld 4: services ophalen die beginnen met een zoek reeks en een uitsluiting

```powershell
Get-Service -Name "win*" -Exclude "WinRM"
```

Deze opdrachten krijgen alleen de services met service namen die beginnen met Win, met uitzonde ring van de WinRM-service.

### Voor beeld 5: services weer geven die momenteel actief zijn

```powershell
Get-Service | Where-Object {$_.Status -eq "Running"}
```

Met deze opdracht worden alleen de services weer gegeven die momenteel actief zijn.
Er wordt gebruikgemaakt van de cmdlet **Get-service** om alle services op de computer op te halen.
De pijplijn operator (|) geeft de resultaten door aan de cmdlet Where-Object, waarmee alleen de services worden geselecteerd met een status eigenschap die gelijk is aan die wordt uitgevoerd.

De status is slechts één eigenschap van service objecten.
Als u alle eigenschappen wilt weer geven, typt u `Get-Service | Get-Member` .

### Voor beeld 6: de services op een externe computer ophalen

```powershell
Get-Service -ComputerName "Server02"
```

Met deze opdracht worden de services op de externe computer Server02 opgehaald.

Omdat de para meter *ComputerName* van **Get-service** geen gebruik maakt van Windows Power shell Remoting, kunt u deze para meter ook gebruiken als de computer niet is geconfigureerd voor externe toegang in Windows Power shell.

### Voor beeld 7: de services op de lokale computer weer geven die afhankelijke services hebben

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

Met de eerste opdracht wordt de cmdlet **Get-service** gebruikt om de services op de computer op te halen.
Een pijplijn operator (|) verzendt de services naar de **where-object-** cmdlet, waarmee de services worden geselecteerd waarvan de eigenschap **DependentServices** niet null is.

Een andere pijplijn operator verzendt de resultaten naar de Format-List-cmdlet.
De opdracht gebruikt de *eigenschaps* parameter voor het weer geven van de naam van de service, de naam van de afhankelijke services en een berekende eigenschap waarmee het aantal afhankelijke services wordt weer gegeven dat elke service heeft.

### Voor beeld 8: Services sorteren op eigenschaps waarde

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

Met deze opdracht wordt aangegeven dat wanneer u services in oplopende volg orde sorteert op de waarde van de eigenschap **status** , gestopt services worden weer gegeven voordat Services worden uitgevoerd.
Dit gebeurt omdat de waarde van status een opsomming is, waarbij gestopt de waarde 1 heeft en de waarde 4 heeft.

Als u eerst actieve services wilt weer geven, gebruikt u de para meter *Aflopend* van de cmdlet Sort-Object.

### Voor beeld 9: Services op meerdere computers ophalen

```powershell
Get-Service -Name "WinRM" -ComputerName "localhost", "Server01", "Server02" |
 Format-Table -Property MachineName, Status, Name, DisplayName -auto
```

```Output
MachineName    Status  Name  DisplayName
------------   ------  ----  -----------
localhost      Running WinRM Windows Remote Management (WS-Management)
Server01       Running WinRM Windows Remote Management (WS-Management)
Server02       Running WinRM Windows Remote Management (WS-Management)
```

Met deze opdracht wordt de cmdlet **Get-service** gebruikt om een Get-Service WinRM-opdracht uit te voeren op twee externe computers en op de lokale computer (' localhost ').

De opdracht wordt uitgevoerd op de externe computers en de resultaten worden geretourneerd naar de lokale computer.
Een pijplijn operator (|) verzendt de resultaten naar de **indeling-tabel-** cmdlet, waarmee de services als tabel worden opgemaakt.
De **notatie tabel** opdracht gebruikt de para meter *Property* om de eigenschappen op te geven die in de tabel worden weer gegeven, met inbegrip van de **MachineName** -eigenschap.

### Voor beeld 10: de afhankelijke services van een service ophalen

```powershell
Get-Service "WinRM" -RequiredServices
```

Met deze opdracht worden de services opgehaald die nodig zijn voor de WinRM-service.

De opdracht retourneert de waarde van de eigenschap **ServicesDependedOn** van de service.

### Voor beeld 11: een service ophalen via de pijplijn operator

```powershell
"WinRM" | Get-Service
```

Met deze opdracht wordt de WinRM-service op de lokale computer opgehaald.
Dit voor beeld laat zien dat u een teken reeks met een service naam (tussen aanhalings tekens) kunt plaatsen om **service te verkrijgen**.

## PARAMETERS

### -ComputerName

Hiermee worden de services opgehaald die worden uitgevoerd op de opgegeven computers.
Standaard is dit de lokale computer.

Typ de NetBIOS-naam, een IP-adres of een Fully Qualified Domain Name (FQDN) van een externe computer.
Als u de lokale computer wilt opgeven, typt u de naam van de computer, een punt (.) of localhost.

Deze para meter is niet gebaseerd op externe communicatie met Windows Power shell.
U kunt de para meter *ComputerName* van **Get-service gebruiken,** zelfs als uw computer niet is geconfigureerd om externe opdrachten uit te voeren.

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases: Cn

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -DependentServices

Geeft aan dat met deze cmdlet alleen de services worden opgehaald die afhankelijk zijn van de opgegeven service.

Deze cmdlet haalt standaard alle services op.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: DS

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -DisplayName

Hiermee geeft u als een teken reeks matrix de weergave namen op van de services die moeten worden opgehaald.
Joker tekens zijn toegestaan.
Met deze cmdlet worden standaard alle services op de computer opgehaald.

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
De waarde van deze para meter komt in aanmerking voor de para meter *name* .
Voer een naam element of patroon in, zoals ' s * '.
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

Hiermee wordt een teken reeks matrix opgegeven, een service of services die met deze cmdlet in de bewerking zijn opgenomen.
De waarde van deze para meter komt in aanmerking voor de para meter *name* .
Voer een naam element of patroon in, zoals ' s * '.
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

Hiermee geeft u de **ServiceController** -objecten op die de services vertegenwoordigen die moeten worden opgehaald.
Voer een variabele in die de objecten bevat, of typ een opdracht of expressie waarmee de objecten worden opgehaald.
U kunt ook een service object door sluizen naar deze cmdlet.

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

Hiermee geeft u de service namen op van de services die moeten worden opgehaald.
Joker tekens zijn toegestaan.
Met deze cmdlet worden standaard alle services op de computer opgehaald.

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

Geeft aan dat met deze cmdlet alleen de services worden opgehaald die door deze service zijn vereist.

Met deze para meter wordt de waarde van de eigenschap **ServicesDependedOn** van de service opgehaald.
Deze cmdlet haalt standaard alle services op.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: SDO, ServicesDependedOn

Required: False
Position: Named
Default value: None
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

U kunt ook verwijzen naar **Get-service** door de ingebouwde alias, ' GSV '. Zie about_Aliases voor meer informatie.

Met deze cmdlet kunnen alleen services worden weer gegeven wanneer de huidige gebruiker gemachtigd is om deze te bekijken.
Als met deze cmdlet geen services worden weer gegeven, bent u mogelijk niet gemachtigd om deze weer te geven.

Als u de service naam en de weergave naam van elke service op uw systeem wilt zoeken, typt u `Get-Service` .
De service namen worden weer gegeven in de kolom naam en de weergave namen worden weer gegeven in de kolom DisplayName.

Wanneer u in oplopende volg orde sorteren op status waarde, worden de Services ' gestopt ' weer gegeven voor services die worden uitgevoerd.
De eigenschap status van een service is een opsommings waarde waarin de namen van de status waarden gehele getallen vertegenwoordigen.
De sorteer bewerking is gebaseerd op de gehele waarde, niet de naam.
' Running ' wordt weer gegeven vóór ' Stopped ' omdat ' Stopped ' de waarde ' 1 ' heeft en ' running ' de waarde ' 4 ' heeft.

## GERELATEERDE KOPPELINGEN

[New-Service](New-Service.md)

[Restart-Service](Restart-Service.md)

[Resume-Service](Resume-Service.md)

[Set-Service](Set-Service.md)

[Start-Service](Start-Service.md)

[Stop-Service](Stop-Service.md)

[Suspend-Service](Suspend-Service.md)
