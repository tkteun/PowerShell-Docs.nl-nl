---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 10/25/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/set-service?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Set-Service
ms.openlocfilehash: df4fda68508e21700235d2b772c6dd43c8e1fe1e
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/07/2020
ms.locfileid: "93250547"
---
# Set-Service

## SAMENVATTING
Hiermee wordt een service gestart, gestopt en onderbroken, en worden de eigenschappen ervan gewijzigd.

## SYNTAXIS

### Naam (standaard)

```
Set-Service [-ComputerName <String[]>] [-Name] <String> [-DisplayName <String>]
 [-Description <String>] [-StartupType <ServiceStartMode>] [-Status <String>] [-PassThru] [-WhatIf]
 [-Confirm] [<CommonParameters>]
```

### Input object

```
Set-Service [-ComputerName <String[]>] [-DisplayName <String>] [-Description <String>]
 [-StartupType <ServiceStartMode>] [-Status <String>] [-InputObject <ServiceController>] [-PassThru]
 [-WhatIf] [-Confirm] [<CommonParameters>]
```

## BESCHRIJVING

`Set-Service`Met de cmdlet worden de eigenschappen van een service gewijzigd, zoals de **status** , **Beschrijving** , **DisplayName** en **opstart type**. `Set-Service` kan een service starten, stoppen, onderbreken of onderbreken. Als u een service wilt identificeren, voert u de service naam in of verzendt u een service object. Of verzend een service naam of Service object omlaag in de pijp lijn `Set-Service` .

## VOORBEELDEN

### Voor beeld 1: een weergave naam wijzigen

In dit voor beeld wordt de weergave naam van een service gewijzigd. Als u de oorspronkelijke weergave naam wilt weer geven, gebruikt u `Get-Service` .

```powershell
Set-Service -Name LanmanWorkstation -DisplayName "LanMan Workstation"
```

`Set-Service` maakt gebruik van de para meter **name** om de naam van de service op te geven, **lanmanworkstation**. Met de para meter **DisplayName** geeft u de nieuwe weergave naam op: **LANMAN-werk station**.

### Voor beeld 2: het opstart type van Services wijzigen

In dit voor beeld ziet u hoe u het opstart type van een service wijzigt.

```powershell
Set-Service -Name BITS -StartupType Automatic
Get-Service BITS | Select-Object -Property Name, StartType, Status
```

```Output
Name  StartType   Status
----  ---------   ------
BITS  Automatic  Running
```

`Set-Service`maakt gebruik van de para meter **name** om de naam van de service **op te geven.** Met de para meter **opstart type** wordt de service ingesteld op **automatisch**.

`Get-Service` maakt gebruik van de para meter **name** om de **bits** -service op te geven en verzendt het object omlaag in de pijp lijn. `Select-Object` gebruikt de para meter **Property** om de status van de **bits** -service weer te geven.

### Voor beeld 3: de beschrijving van een service wijzigen

In dit voor beeld wordt de beschrijving van de BITS-service gewijzigd en wordt het resultaat weer gegeven.

De `Get-CimInstance` cmdlet wordt gebruikt omdat deze een **Win32_Service** -object retourneert dat de **Beschrijving** van de service bevat.

```powershell
Get-CimInstance Win32_Service -Filter 'Name = "BITS"'  | Format-List  Name, Description
```

```Output
Name        : BITS
Description : Transfers files in the background using idle network bandwidth. If the service is
              disabled, then any applications that depend on BITS, such as Windows Update or MSN
              Explorer, will be unable to automatically download programs and other information.
```

```powershell
Set-Service -Name BITS -Description "Transfers files in the background using idle network bandwidth."
Get-CimInstance Win32_Service -Filter 'Name = "BITS"' | Format-List  Name, Description
```

```Output
Name        : BITS
Description : Transfers files in the background using idle network bandwidth.
```

`Get-CimInstance` Hiermee wordt het object naar beneden verzonden naar de pijp lijn `Format-List` en worden de naam en beschrijving van de service weer gegeven. Voor vergelijkings doeleinden wordt de opdracht uitgevoerd v????r en na het bijwerken van de beschrijving.

`Set-Service` maakt gebruik van de para meter **name** om de **bits** -service op te geven. De **beschrijvings** parameter bevat de bijgewerkte tekst voor de beschrijving van de service.

### Voor beeld 4: een service starten

In dit voor beeld wordt een service gestart.

```powershell
Set-Service -Name WinRM -Status Running -PassThru
```

```Output
Status   Name               DisplayName
------   ----               -----------
Running  WinRM              Windows Remote Management (WS-Manag...
```

`Set-Service` maakt gebruik van de para meter **name** om de service, **WinRM** op te geven. De para meter **status** gebruikt de waarde **die wordt gebruikt** om de service te starten. De para meter **PassThru** voert een **ServiceController** -object uit dat de resultaten weergeeft.

### Voor beeld 5: een service opschorten

In dit voor beeld wordt de pijp lijn gebruikt om de service te onderbreken.

```powershell
Get-Service -Name Schedule | Set-Service -Status Paused
```

`Get-Service` maakt gebruik van de para meter **name** om de **Schedule** -service op te geven en verzendt het object omlaag in de pijp lijn. `Set-Service` maakt gebruik van de para meter **status** om de service in te stellen op **onderbroken**.

### Voor beeld 6: een service stoppen

In dit voor beeld wordt een variabele gebruikt om een service te stoppen.

```powershell
$S = Get-Service -Name Schedule
Set-Service -InputObject $S -Status Stopped
```

`Get-Service` maakt gebruik van de para meter **name** om de service, de **planning** op te geven. Het object wordt opgeslagen in de variabele `$S` . `Set-Service` maakt gebruik van de para meter **input object** en geeft het object op dat is opgeslagen `$S` . Met de para meter **status** wordt de service ingesteld op **gestopt**.

## PARAMETERS

### -ComputerName

Hiermee geeft u een of meer computers op. Voor externe computers typt u de NetBIOS-naam, een IP-adres of een Fully Qualified Domain Name. Als de para meter **ComputerName** niet is opgegeven, wordt de opdracht uitgevoerd op de lokale computer.

Deze para meter is niet afhankelijk van externe communicatie met Power shell. U kunt de para meter **ComputerName** ook gebruiken als uw computer niet is geconfigureerd om externe opdrachten uit te voeren.

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases: cn

Required: False
Position: Named
Default value: Local computer
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -Confirm

Vraagt u om bevestiging voordat deze wordt uitgevoerd `Set-Service` .

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

### -Beschrijving

Hiermee geeft u een nieuwe beschrijving op voor de service.

De beschrijving van de service wordt weer gegeven in **computer beheer, services**. De **Beschrijving** is geen eigenschap van het `Get-Service` **ServiceController** -object. Als u de beschrijving van de service wilt zien, gebruikt u `Get-CimInstance` die een **Win32_Service** -object retourneert dat de service vertegenwoordigt.

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -DisplayName

Hiermee geeft u een nieuwe weergave naam voor de service op.

```yaml
Type: System.String
Parameter Sets: (All)
Aliases: DN

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Input object

Hiermee geeft u een **ServiceController** -object op dat de service vertegenwoordigt die moet worden gewijzigd. Voer een variabele in die het object bevat of typ een opdracht of expressie waarmee het object wordt opgehaald, zoals een `Get-Service` opdracht. U kunt de pijp lijn gebruiken om een service object naar te verzenden `Set-Service` .

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

Hiermee geeft u de service naam op van de service die moet worden gewijzigd. Joker tekens zijn niet toegestaan. U kunt de pijp lijn gebruiken om een service naam naar te verzenden `Set-Service` .

```yaml
Type: System.String
Parameter Sets: Name
Aliases: ServiceName, SN

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### -PassThru

Retourneert een **ServiceController** -object dat staat voor de services die zijn gewijzigd. Standaard genereert geen `Set-Service` uitvoer.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### -Opstart type

Hiermee stelt u het opstart type van de service in. De aanvaardbare waarden voor deze parameter zijn:

- **Automatisch** : de service wordt gestart of is door het besturings systeem gestart tijdens het opstarten van het systeem.
  Als een service die automatisch wordt gestart, afhankelijk is van een hand matig gestarte service, wordt de hand matig gestarte service ook automatisch gestart bij het opstarten van het systeem.
- **Uitgeschakeld** : de service is uitgeschakeld en kan niet worden gestart door een gebruiker of toepassing.
- **Hand matig** : de service wordt alleen hand matig gestart door een gebruiker, met behulp van service besturings beheer of door een toepassing.
- **Boot** : geeft aan dat de service een apparaatstuurprogramma is dat door de System loader wordt gestart. Deze waarde is alleen geldig voor apparaatstuurprogramma's.
- **Systeem** : geeft aan dat de service een apparaatstuurprogramma is dat is gestart door de functie IOInitSystem (). Deze waarde is alleen geldig voor apparaatstuurprogramma's.

 De standaard waarde is **automatisch**.

```yaml
Type: System.ServiceProcess.ServiceStartMode
Parameter Sets: (All)
Aliases: StartMode, SM, ST
Accepted values: Boot, System, Automatic, Manual, Disabled

Required: False
Position: Named
Default value: Automatic
Accept pipeline input: False
Accept wildcard characters: False
```

### -Status

Hiermee geeft u de status van de service op.

De acceptabele waarden voor deze para meter zijn als volgt:

- **Onderbroken**. Hiermee wordt de service onderbroken.
- **Wordt uitgevoerd**. De service wordt gestart.
- **Gestopt**. Hiermee stopt u de service.

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:
Accepted values: Paused, Running, Stopped

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -WhatIf

Hier wordt weer gegeven wat er gebeurt als er `Set-Service` wordt uitgevoerd. De cmdlet wordt niet uitgevoerd.

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

U kunt de pijp lijn gebruiken om een service object of een teken reeks die een service naam bevat te verzenden naar `Set-Service` .

## UITVOER

### System. ServiceProcess. ServiceController

Er worden standaard `Set-Service` geen objecten geretourneerd. Gebruik de para meter **PassThru** voor het uitvoeren van een **ServiceController** -object.

## OPMERKINGEN

`Set-Service` vereist verhoogde machtigingen. Gebruik de optie **als administrator uitvoeren** .

`Set-Service` kan alleen services beheren wanneer de huidige gebruiker machtigingen heeft om services te beheren. Als een opdracht niet correct werkt, beschikt u mogelijk niet over de vereiste machtigingen.

Als u de service naam of weergave naam van een service wilt zoeken, gebruikt u `Get-Service` . De service namen bevinden zich in de kolom **naam** en de weergave namen bevinden zich in de kolom **DisplayName** .

## GERELATEERDE KOPPELINGEN

[Get-Service](Get-Service.md)

[New-Service](New-Service.md)

[Restart-Service](Restart-Service.md)

[Resume-Service](Resume-Service.md)

[Start-Service](Start-Service.md)

[Stop-Service](Stop-Service.md)

[Suspend-Service](Suspend-Service.md)
