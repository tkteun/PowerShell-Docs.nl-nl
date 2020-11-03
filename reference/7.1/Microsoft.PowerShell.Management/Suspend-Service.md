---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/suspend-service?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Suspend-Service
ms.openlocfilehash: 8455592f6b919da04603470262c134593f74877c
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/07/2020
ms.locfileid: "93249997"
---
# Suspend-Service

## SAMENVATTING
Hiermee worden een of meer actieve services onderbroken (onderbroken).

## SYNTAXIS

### Input object (standaard)

```
Suspend-Service [-InputObject] <ServiceController[]> [-PassThru] [-Include <String[]>] [-Exclude <String[]>]
 [-WhatIf] [-Confirm] [<CommonParameters>]
```

### Standaard

```
Suspend-Service [-Name] <String[]> [-PassThru] [-Include <String[]>] [-Exclude <String[]>] [-WhatIf] [-Confirm]
 [<CommonParameters>]
```

### DisplayName

```
Suspend-Service [-PassThru] -DisplayName <String[]> [-Include <String[]>] [-Exclude <String[]>] [-WhatIf]
 [-Confirm] [<CommonParameters>]
```

## BESCHRIJVING

De cmdlet **suspend-service** stuurt een suspend-bericht naar de Windows-service controller voor elk van de opgegeven services.
Tijdens de onderbreking wordt de service nog steeds uitgevoerd, maar de actie wordt gestopt totdat deze wordt hervat, bijvoorbeeld door de usingthe Resume-Service-cmdlet.
U kunt de services opgeven met hun service namen of weergave namen, of u kunt de para meter *input object* gebruiken om een service object door te geven dat staat voor de services die u wilt onderbreken.

## VOORBEELDEN

### Voor beeld 1: een service opschorten

```
PS C:\> Suspend-Service -DisplayName "Telnet"
```

Met deze opdracht wordt de service Telnet-service (TlntSvr) op de lokale computer onderbroken.

### Voor beeld 2: weer geven wat er gebeurt als u services uitbreekt

```
PS C:\> Suspend-Service -Name lanman* -WhatIf
```

Met deze opdracht wordt aangegeven wat er gebeurt als u de services met een service naam die begint met LANMAN hebt onderbroken.
Als u de services wilt onderbreken, voert u de opdracht opnieuw uit zonder de para meter *WhatIf* .

### Voor beeld 3: een service ophalen en opschorten

```
PS C:\> Get-Service schedule | Suspend-Service
```

Met deze opdracht wordt de cmdlet **Get-service** gebruikt om een object op te halen dat de taak planner-service (Schedule) op de computer vertegenwoordigt.
De pijplijn operator (|) geeft het resultaat door aan **suspend-service** , waardoor de service wordt onderbroken.

### Voor beeld 4: alle services onderbreken die kunnen worden onderbroken

```
PS C:\> Get-Service | Where-Object {$_.CanPauseAndContinue -eq "True"} | Suspend-Service -Confirm
```

Met deze opdracht worden alle services op de computer opgeschort die kunnen worden onderbroken.
Er wordt **Get-service** gebruikt om objecten op te halen die de services op de computer vertegenwoordigen.
De pijplijn operator geeft de resultaten door aan de cmdlet Where-Object, waarmee alleen de services worden geselecteerd met de waarde $True voor de eigenschap **CanPauseAndContinue** .
Een andere pijplijn operator geeft de resultaten door aan **suspend-service**.
De *bevestigings* parameter vraagt u om bevestiging voordat alle services worden onderbroken.

## PARAMETERS

### -DisplayName

Hiermee geeft u de weergave namen op van de services die moeten worden onderbroken.
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

Hiermee geeft u services op die van de opgegeven services worden wegge laten.
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

Hiermee worden de services opgegeven die moeten worden onderbroken.
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

Hiermee geeft u **ServiceController** -objecten op die de services vertegenwoordigen die moeten worden onderbroken.
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

Hiermee geeft u de service namen op van de services die moeten worden onderbroken.
Joker tekens zijn toegestaan.

De parameter naam is optioneel.
U kunt de *naam* of de alias ervan *gebruiken, of* u kunt de parameter naam weglaten.

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

Retourneert een object dat het item vertegenwoordigt waarmee u werkt.
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

Met deze cmdlet wordt een **System. ServiceProcess. ServiceController** -object gegenereerd dat de service vertegenwoordigt, als u de para meter *PassThru* opgeeft.
Anders wordt met deze cmdlet geen uitvoer gegenereerd.

## OPMERKINGEN

* **Suspend-service** kan alleen services bepalen wanneer de huidige gebruiker gemachtigd is om dit uit te voeren. Als een opdracht niet correct werkt, beschikt u mogelijk niet over de vereiste machtigingen.
* **Suspend-service** kan alleen services opschorten die ondersteuning bieden voor onderbroken en hervat. Als u wilt bepalen of een bepaalde service kan worden onderbroken, gebruikt u de Get-Service cmdlet samen met de eigenschap **CanPauseAndContinue** . Bijvoorbeeld `Get-Service wmi | Format-List Name, CanPauseAndContinue`. Als u wilt zoeken naar alle services op de computer die kunnen worden onderbroken, typt u `Get-Service | Where-Object {$_.CanPauseAndContinue -eq $true}` .
* Typ **Get-service** om de service namen te vinden en de namen van de services op uw systeem weer te geven. De service namen worden weer gegeven in de kolom **naam** en de weergave namen worden weer gegeven in de kolom **DisplayName** .

## GERELATEERDE KOPPELINGEN

[Get-Service](Get-Service.md)

[New-Service](New-Service.md)

[Restart-Service](Restart-Service.md)

[Resume-Service](Resume-Service.md)

[Set-Service](Set-Service.md)

[Start-Service](Start-Service.md)

[Stop-Service](Stop-Service.md)

[Verwijderen-service](Remove-Service.md)

