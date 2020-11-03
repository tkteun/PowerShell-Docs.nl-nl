---
external help file: System.Management.Automation.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/remove-pssession?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Remove-PSSession
ms.openlocfilehash: a6b980b022672fbc84549987e1cb5673f51e3dc4
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/07/2020
ms.locfileid: "93251229"
---
# Remove-PSSession

## SAMENVATTING
Hiermee sluit u een of meer Power shell-sessies (PSSessions).

## SYNTAXIS

### Id (standaard)

```
Remove-PSSession [-Id] <Int32[]> [-WhatIf] [-Confirm] [<CommonParameters>]
```

### Sessie

```
Remove-PSSession [-Session] <PSSession[]> [-WhatIf] [-Confirm] [<CommonParameters>]
```

### ContainerId

```
Remove-PSSession -ContainerId <String[]> [-WhatIf] [-Confirm] [<CommonParameters>]
```

### VMId

```
Remove-PSSession -VMId <Guid[]> [-WhatIf] [-Confirm] [<CommonParameters>]
```

### VMName

```
Remove-PSSession -VMName <String[]> [-WhatIf] [-Confirm] [<CommonParameters>]
```

### InstanceId

```
Remove-PSSession -InstanceId <Guid[]> [-WhatIf] [-Confirm] [<CommonParameters>]
```

### Naam

```
Remove-PSSession -Name <String[]> [-WhatIf] [-Confirm] [<CommonParameters>]
```

### ComputerName

```
Remove-PSSession [-ComputerName] <String[]> [-WhatIf] [-Confirm] [<CommonParameters>]
```

## BESCHRIJVING

De cmdlet **Remove-PSSession** sluit Power shell-sessies ( **PSSessions** ) in de huidige sessie.
Hiermee worden opdrachten gestopt die worden uitgevoerd in de **PSSessions** , wordt de **PSSession** beëindigd en worden de resources vrijgegeven die de **PSSession** gebruikt.
Als de **PSSession** is verbonden met een externe computer, sluit deze cmdlet ook de verbinding tussen de lokale en externe computers.

Als u een **PSSession** wilt verwijderen, voert u de *naam* , *ComputerName* , *id* of *InstanceId* van de sessie in.

Als u de *PSSession* hebt opgeslagen in een variabele, blijft het object Session in de variabele, maar wordt de status van de *PSSession* gesloten.

## VOORBEELDEN

### Voor beeld 1: sessies verwijderen met behulp van-Id's

```powershell
Remove-PSSession -Id 1, 2
```

Met deze opdracht verwijdert u de **PSSessions** met de id's 1 en 2.

### Voor beeld 2: alle sessies in de huidige sessie verwijderen

```powershell
Get-PSSession | Remove-PSSession
Remove-PSSession -Session (Get-PSSession)
$s = Get-PSSession
Remove-PSSession -Session $s
```

Met deze opdrachten worden alle **PSSessions** in de huidige sessie verwijderd.
Hoewel de drie opdracht indelingen er anders uitzien, hebben ze hetzelfde effect.

### Voor beeld 3: sessies sluiten met behulp van namen

```powershell
$r = Get-PSSession -ComputerName Serv*
$r | Remove-PSSession
```

Met deze opdrachten sluit u de **PSSessions** die zijn verbonden met computers die namen hebben die met Serviceart beginnen.

### Voor beeld 4: sessies sluiten die zijn verbonden met een poort

```powershell
Get-PSSession | where {$_.port -eq 90} | Remove-PSSession
```

Met deze opdracht sluit u de **PSSessions** die zijn verbonden met poort 90.
U kunt deze opdracht indeling gebruiken om **PSSessions** te identificeren op basis van andere eigenschappen dan *ComputerName* , *name* , *InstanceId* en *id*.

### Voor beeld 5: een sessie sluiten op basis van exemplaar-ID

```powershell
Get-PSSession | Format-Table ComputerName, InstanceID  -AutoSize
```

```Output
ComputerName InstanceId
------------ ----------------
Server01     875d231b-2788-4f36-9f67-2e50d63bb82a
localhost    c065ffa0-02c4-406e-84a3-dacb0d677868
Server02     4699cdbc-61d5-4e0d-b916-84f82ebede1f
Server03     4e5a3245-4c63-43e4-88d0-a7798bfc2414
TX-TEST-01   fc4e9dfa-f246-452d-9fa3-1adbdd64ae85 PS C:\> Remove-PSSession -InstanceID fc4e9dfa-f246-452d-9fa3-1adbdd64ae85
```

Deze opdrachten laten zien hoe u een **PSSession** kunt sluiten op basis van de instantie-id of **RemoteRunspaceID**.

De eerste opdracht maakt gebruik van de cmdlet **Get-PSSession** om de **PSSessions** in de huidige sessie op te halen.
Er wordt gebruikgemaakt van een pijplijn operator (|) om de **PSSessions** te verzenden naar de cmdlet Format-Table, waarmee de eigenschappen **ComputerName** en **InstanceId** worden opgemaakt in een tabel.
De *AutoSize* -para meter comprimeert de kolommen voor weer gave.

Vanuit de resulterende weer gave kunt u de **PSSession** die moeten worden gesloten identificeren en de *InstanceId* van die **PSSession** kopiëren en plakken in de tweede opdracht.

De tweede opdracht maakt gebruik van de cmdlet **Remove-PSSession** om de *PSSession* te verwijderen met de opgegeven exemplaar-id.

### Voor beeld 6: een functie maken waarmee alle sessies in de huidige sessie worden verwijderd

```powershell
Function EndPSS { Get-PSSession | Remove-PSSession }
```

Deze functie verwijdert alle **PSSessions** in de huidige sessie.
Nadat u deze functie aan uw Power shell-profiel hebt toegevoegd, kunt u alle sessies verwijderen `EndPSS` .

## PARAMETERS

### -ComputerName

Hiermee geeft u een matrix met namen van computers op.
Met deze cmdlet worden de **PSSessions** die zijn verbonden met de opgegeven computers gesloten.
Joker tekens zijn toegestaan.

Typ de NetBIOS-naam, een IP-adres of een Fully Qualified Domain Name van een of meer externe computers.
Typ de computer naam, localhost of een punt (.) om de lokale computer op te geven.

```yaml
Type: System.String[]
Parameter Sets: ComputerName
Aliases: Cn

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: True
```

### -ContainerId

Hiermee geeft u een matrix met Id's van containers op. Met deze cmdlet worden sessies voor elk van de opgegeven containers verwijderd. Gebruik de `docker ps` opdracht om een lijst met container-id's op te halen. Zie de Help voor de opdracht [docker PS](https://docs.docker.com/engine/reference/commandline/ps/) voor meer informatie.

```yaml
Type: System.String[]
Parameter Sets: ContainerId
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -Id

Hiermee geeft u een matrix met Id's van sessies.
Met deze cmdlet wordt de *PSSessions* met de opgegeven id's gesloten.
Typ een of meer Id's, gescheiden door komma's, of gebruik de operator Range (..) om een bereik van Id's op te geven.

Een ID is een geheel getal dat de **PSSession** in de huidige sessie uniek identificeert.
Het is gemakkelijker te onthouden en te typen dan de *InstanceId* , maar is alleen uniek in de huidige sessie.
Als u de ID van een **PSSession** wilt zoeken, voert u de cmdlet Get-PSSession zonder para meters uit.

```yaml
Type: System.Int32[]
Parameter Sets: Id
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -InstanceId

Hiermee geeft u een matrix met exemplaar-Id's op.
Met deze cmdlet wordt de **PSSessions** gesloten met de opgegeven exemplaar-id's.

De exemplaar-ID is een GUID waarmee een **PSSession** in de huidige sessie uniek wordt geïdentificeerd.
De exemplaar-ID is uniek, zelfs wanneer er meerdere sessies worden uitgevoerd op één computer.

De exemplaar-ID wordt opgeslagen in de eigenschap **InstanceId** van het object dat een **PSSession** vertegenwoordigt.
Als u wilt zoeken naar de **InstanceId** van de **PSSessions** in de huidige sessie, typt u `Get-PSSession | Format-Table Name, ComputerName, InstanceId` .

```yaml
Type: System.Guid[]
Parameter Sets: InstanceId
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -Name

Hiermee geeft u een matrix met beschrijvende namen van sessies.
Met deze cmdlet worden de **PSSessions** met de opgegeven beschrijvende namen gesloten.
Joker tekens zijn toegestaan.

Omdat de beschrijvende naam van een **PSSession** mogelijk niet uniek is, moet u, wanneer u de para meter *name* gebruikt, ook de *WhatIf* of de para meter *confirm* gebruiken in de opdracht **Remove-PSSession** .

```yaml
Type: System.String[]
Parameter Sets: Name
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: True
```

### -Sessie

Hiermee geeft u de sessie objecten van de **PSSessions** moeten worden gesloten.
Voer een variabele in die de **PSSessions** bevat of een opdracht die de **PSSessions** , zoals een New-PSSession of **Get-PSSession** opdracht, maakt of ontvangt.
U kunt ook een of meer sessie objecten pipeen om **-PSSession te verwijderen**.

```yaml
Type: System.Management.Automation.Runspaces.PSSession[]
Parameter Sets: Session
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### -VMId

Hiermee geeft u een ID-matrix van virtuele machines op.
Met deze cmdlet wordt een interactieve sessie gestart met elk van de opgegeven virtuele machines.
Als u de virtuele machines wilt zien die voor u beschikbaar zijn, gebruikt u de volgende opdracht:

`Get-VM | Select-Object -Property Name, ID`

```yaml
Type: System.Guid[]
Parameter Sets: VMId
Aliases: VMGuid

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -VMName

Hiermee geeft u een matrix met namen van virtuele machines op.
Met deze cmdlet wordt een interactieve sessie gestart met elk van de opgegeven virtuele machines.
Als u de virtuele machines wilt zien die voor u beschikbaar zijn, gebruikt u de cmdlet **Get-VM** .

```yaml
Type: System.String[]
Parameter Sets: VMName
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
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

### System. Management. Automation. Runspaces. PSSession

U kunt een sessie object door sluizen naar deze cmdlet.

## UITVOER

### Geen

Met deze cmdlet worden geen objecten geretourneerd.

## OPMERKINGEN

* De *id-* para meter is verplicht. Als u wilt verwijderen van alle **PSSessions** in de huidige sessie, typt u `Get-PSSession | Remove-PSSession` .
* Een **PSSession** maakt gebruik van een permanente verbinding met een externe computer. Een **PSSession** maken om een reeks opdrachten uit te voeren die gegevens delen. Typ `Get-Help about_PSSessions` voor meer informatie.
* **PSSessions** zijn specifiek voor de huidige sessie. Wanneer u een sessie beëindigt, wordt de **PSSessions** die u in die sessie hebt gemaakt, geforceerd gesloten.

## GERELATEERDE KOPPELINGEN

[Connect-PSSession](Connect-PSSession.md)

[Verbinding verbreken-PSSession](Disconnect-PSSession.md)

[Enter-PSSession](Enter-PSSession.md)

[Afsluiten-PSSession](Exit-PSSession.md)

[Get-PSSession](Get-PSSession.md)

[Invoke-opdracht](Invoke-Command.md)

[New-PSSession](New-PSSession.md)

[Receive-PSSession](Receive-PSSession.md)

[about_PSSessions](About/about_PSSessions.md)

[about_Remote](About/about_Remote.md)
