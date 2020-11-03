---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/start-service?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Start-Service
ms.openlocfilehash: a7436e1b32beb968f37944021d7f702bd1f1918c
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/07/2020
ms.locfileid: "93250542"
---
# Start-Service

## SAMENVATTING
Start een of meer gestopt Services.

## SYNTAXIS

### Input object (standaard)

```
Start-Service [-InputObject] <ServiceController[]> [-PassThru] [-Include <String[]>] [-Exclude <String[]>]
 [-WhatIf] [-Confirm] [<CommonParameters>]
```

### Standaard

```
Start-Service [-Name] <String[]> [-PassThru] [-Include <String[]>] [-Exclude <String[]>] [-WhatIf] [-Confirm]
 [<CommonParameters>]
```

### DisplayName

```
Start-Service [-PassThru] -DisplayName <String[]> [-Include <String[]>] [-Exclude <String[]>] [-WhatIf]
 [-Confirm] [<CommonParameters>]
```

## BESCHRIJVING

De `Start-Service` cmdlet verzendt een start bericht naar de Windows-service controller voor elk van de opgegeven services. Als er al een service wordt uitgevoerd, wordt het bericht genegeerd zonder dat er een fout is opgetreden. U kunt de services opgeven met hun service namen of weergave namen, of u kunt de para meter **input object** gebruiken om een service object op te geven dat staat voor de services die u wilt starten.

## VOORBEELDEN

### Voor beeld 1: een service starten met behulp van de naam

In dit voor beeld wordt de EventLog-service op de lokale computer gestart. De **naam** parameter identificeert de service op basis van de service naam.

```powershell
Start-Service -Name "eventlog"
```

### Voor beeld 2: gegevens weer geven zonder een service te starten

In dit voor beeld ziet u wat er zou gebeuren als u de services hebt gestart met een weergave naam die ' Extern ' bevat.

```powershell
Start-Service -DisplayName *remote* -WhatIf
```

Met de para meter **DisplayName** worden de services geïdentificeerd op basis van de weergave naam in plaats van de service naam. De para meter **WhatIf** zorgt ervoor dat de cmdlet weergeeft wat er zou gebeuren wanneer u de opdracht uitvoert, maar geen wijzigingen aanbrengt.

### Voor beeld 3: een service starten en de actie vastleggen in een tekst bestand

In dit voor beeld wordt de Windows Management Instrumentation (WMI)-service op de computer gestart en wordt een record van de actie toegevoegd aan het services.txt bestand.

```powershell
$s = Get-Service wmi
Start-Service -InputObject $s -PassThru | Format-List >> services.txt
```

Eerst wordt gebruikt `Get-Service` om een object op te halen dat de WMI-service vertegenwoordigt en op te slaan in de `$s` variabele. Vervolgens wordt de service gestart. Zonder de **PassThru** para meter PassThru `Start-Service` wordt geen uitvoer gemaakt. De pijplijn operator (|) geeft de object uitvoer door `Start-Service` aan de `Format-List` cmdlet om het object op te maken als een lijst met eigenschappen. Met de operator voor het omleiden van toevoeg bewerkingen ( \> \> ) wordt de uitvoer omgeleid naar het services.txt-bestand. De uitvoer wordt toegevoegd aan het einde van het bestaande bestand.

### Voor beeld 4: een uitgeschakelde service starten

In dit voor beeld ziet u hoe u een service start wanneer het opstart type van de service wordt **uitgeschakeld**.

```
PS> Start-Service tlntsvr
Start-Service : Service 'Telnet (TlntSvr)' cannot be started due to the following error: Cannot start service TlntSvr on computer '.'.
At line:1 char:14
+ Start-Service  <<<< tlntsvr

PS> Get-CimInstance win32_service | Where-Object Name -eq "tlntsvr"
ExitCode  : 0
Name      : TlntSvr
ProcessId : 0
StartMode : Disabled
State     : Stopped
Status    : OK

PS> Set-Service tlntsvr -StartupType manual
PS> Start-Service tlntsvr
```

De eerste poging om de Telnet-service (TlntSvr) te starten, mislukt. De `Get-CimInstance` opdracht geeft aan dat de eigenschap **Start** modus van de TlntSvr-service is **uitgeschakeld**. `Set-Service`Met de cmdlet wordt het type start gewijzigd in **hand matig**. Nu kunnen we de opdracht opnieuw verzenden `Start-Service` . Deze keer is de opdracht geslaagd. Voer uit om te controleren of de opdracht is geslaagd `Get-Service` .

## PARAMETERS

### -DisplayName

Hiermee geeft u de weergave namen op van de services die moeten worden gestart. Joker tekens zijn toegestaan.

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

Hiermee geeft u de services die door deze cmdlet worden wegge laten. De waarde van deze para meter komt in aanmerking voor de para meter **name** . Voer een naam element of patroon in, bijvoorbeeld `s*` . Joker tekens zijn toegestaan.

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

Hiermee geeft u de services op die met deze cmdlet worden gestart. De waarde van deze para meter komt in aanmerking voor de para meter **name** . Voer een naam element of patroon in, bijvoorbeeld `s*` . Joker tekens zijn toegestaan.

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

Hiermee geeft u **ServiceController** -objecten op die de services vertegenwoordigen die moeten worden gestart. Voer een variabele in die de objecten bevat, of typ een opdracht of expressie waarmee de objecten worden opgehaald.

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

Hiermee geeft u de service namen voor de service moet worden gestart.

De parameter naam is optioneel. U kunt de **naam** of de alias ervan **gebruiken, of** u kunt de parameter naam weglaten.

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

U kunt objecten pipeen die de services of teken reeksen vertegenwoordigen die de service namen bevatten voor deze cmdlet.

## UITVOER

### Geen, System. ServiceProcess. ServiceController

Met deze cmdlet wordt een **System. ServiceProcess. ServiceController** -object gegenereerd dat de service vertegenwoordigt, als u **PassThru** opgeeft. Anders wordt met deze cmdlet geen uitvoer gegenereerd.

## OPMERKINGEN

* U kunt ook verwijzen naar `Start-Service` de ingebouwde alias `sasv` . Zie [about_Aliases](../Microsoft.PowerShell.Core/About/about_Aliases.md)voor meer informatie.
* `Start-Service` Hiermee kunnen alleen services worden beheerd als de huidige gebruiker gemachtigd is om dit te doen. Als een opdracht niet correct werkt, beschikt u mogelijk niet over de vereiste machtigingen.
* Als u de service namen wilt zoeken en de namen van de services op uw systeem wilt weer geven, typt u `Get-Service` .
  De service namen worden weer gegeven in de kolom **naam** en de weergave namen worden weer gegeven in de kolom **DisplayName** .
* U kunt alleen de services starten die het begin type hand matig, automatisch of automatisch hebben (vertraagd starten). U kunt de services die het begin type uitgeschakeld hebben niet starten. Als een `Start-Service` opdracht mislukt met het bericht `Cannot start service \<service-name\> on computer` , gebruikt `Get-CimInstance` u om het start type van de service te vinden. Als u dat wilt, gebruikt u de `Set-Service` cmdlet om het start type van de service te wijzigen.
* Sommige services, zoals Performance Logs and Alerts (SysmonLog), worden automatisch gestopt als ze geen werk hebben. Wanneer Power shell een service start die zichzelf bijna onmiddellijk stopt, wordt het volgende bericht weer gegeven: `Service \<display-name\> start failed.`

## GERELATEERDE KOPPELINGEN

[Get-Service](Get-Service.md)

[New-Service](New-Service.md)

[Restart-Service](Restart-Service.md)

[Resume-Service](Resume-Service.md)

[Set-Service](Set-Service.md)

[Stop-Service](Stop-Service.md)

[Suspend-Service](Suspend-Service.md)
