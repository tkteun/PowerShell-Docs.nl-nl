---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 01/22/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/new-eventlog?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: New-EventLog
ms.openlocfilehash: 61fafc0670a24fd6ca057e4cf0c7179d90446b07
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/07/2020
ms.locfileid: "93250598"
---
# New-EventLog

## SAMENVATTING
Hiermee maakt u een nieuw gebeurtenis logboek en een nieuwe gebeurtenis bron op een lokale of externe computer.

## SYNTAXIS

```
New-EventLog [-LogName] <string> [-Source] <string[]> [[-ComputerName] <string[]>]
  [-CategoryResourceFile <string>] [-MessageResourceFile <string>] [-ParameterResourceFile <string>]
  [<CommonParameters>]
```

## BESCHRIJVING

Met deze cmdlet maakt u een nieuw klassiek gebeurtenis logboek op een lokale of externe computer. Het kan ook een gebeurtenis bron registreren die naar het nieuwe logboek of naar een bestaand logboek schrijft.

De cmdlets die het zelfstandig naam woord van het gebeurtenissen logboek bevatten (de gebeurtenis logboek-cmdlets) werken alleen in klassieke gebeurtenis Logboeken.
Als u gebeurtenissen wilt ophalen uit logboeken die gebruikmaken van de Windows-gebeurtenis logboek technologie in Windows Vista en latere versies van Windows, gebruikt u `Get-WinEvent` .

## VOORBEELDEN

### Voor beeld 1: een nieuw gebeurtenis logboek maken

Met deze opdracht wordt het TestLog-gebeurtenis logboek op de lokale computer gemaakt en wordt er een nieuwe bron voor geregistreerd.

```powershell
New-EventLog -source TestApp -LogName TestLog -MessageResourceFile C:\Test\TestApp.dll
```

### Voor beeld 2: een nieuwe gebeurtenis bron aan een bestaand logboek toevoegen

Met deze opdracht wordt een nieuwe gebeurtenis bron, NewTestApp, toegevoegd aan het toepassings logboek op de externe computer met Server01.

```powershell
$file = "C:\Program Files\TestApps\NewTestApp.dll"
New-EventLog -ComputerName Server01 -Source NewTestApp -LogName Application -MessageResourceFile $file -CategoryResourceFile $file
```

Voor de opdracht is vereist dat het NewTestApp.dll-bestand zich op de Server01-computer bevindt.

## PARAMETERS

### -CategoryResourceFile

Hiermee geeft u het pad naar het bestand met categorie teken reeksen voor de bron gebeurtenissen. Dit bestand wordt ook wel het categorie bericht bestand genoemd.

Het bestand moet aanwezig zijn op de computer waarop het gebeurtenis logboek wordt gemaakt. Met deze para meter worden geen bestanden gemaakt of verplaatst.

```yaml
Type: System.String
Parameter Sets: (All)
Aliases: CRF

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -ComputerName

Maakt de nieuwe gebeurtenis logboeken op de opgegeven computers. Standaard is dit de lokale computer.

De NetBIOS-naam, het IP-adres of de Fully Qualified Domain Name van een externe computer.
Typ de computer naam, een punt (.) of ' localhost ' om de lokale computer op te geven.

Deze para meter is niet afhankelijk van externe communicatie met Power shell. U kunt de para meter **ComputerName** gebruiken `Get-EventLog` , zelfs als uw computer niet is geconfigureerd om externe opdrachten uit te voeren.

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases: CN

Required: False
Position: 3
Default value: Local computer
Accept pipeline input: False
Accept wildcard characters: False
```

### -LogName

Hiermee geeft u de naam van het gebeurtenis logboek op.

Als het logboek niet bestaat, `New-EventLog` wordt het logboek gemaakt en wordt deze waarde gebruikt voor de eigenschappen **log** en **LogDisplayName** van het nieuwe gebeurtenis logboek. Als het logboek bestaat, `New-EventLog` registreert een nieuwe bron voor het gebeurtenis logboek.

```yaml
Type: System.String
Parameter Sets: (All)
Aliases: LN

Required: True
Position: 1
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -MessageResourceFile

Hiermee geeft u het pad naar het bestand met teken reeksen voor bericht opmaak voor de bron gebeurtenissen.
Dit bestand wordt ook wel het gebeurtenis bericht bestand genoemd.

Het bestand moet aanwezig zijn op de computer waarop het gebeurtenis logboek wordt gemaakt.
Met deze para meter worden geen bestanden gemaakt of verplaatst.

```yaml
Type: System.String
Parameter Sets: (All)
Aliases: MRF

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -ParameterResourceFile

Hiermee geeft u het pad op naar het bestand met teken reeksen die worden gebruikt voor het vervangen van para meters in gebeurtenis beschrijvingen. Dit bestand wordt ook wel het parameter bericht bestand genoemd.

Het bestand moet aanwezig zijn op de computer waarop het gebeurtenis logboek wordt gemaakt.
Met deze para meter worden geen bestanden gemaakt of verplaatst.

```yaml
Type: System.String
Parameter Sets: (All)
Aliases: PRF

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Source

Hiermee geeft u de namen van de gebeurtenis logboek bronnen, zoals toepassings Programma's die naar het gebeurtenis logboek schrijven. Deze parameter is vereist.

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases: SRC

Required: True
Position: 2
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### CommonParameters

Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable. Zie [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)voor meer informatie.

## INVOER

### Geen

U kunt geen invoer van een pipe naar deze cmdlet.

## UITVOER

### System. Diagnostics. EventLogEntry

## OPMERKINGEN

Als u wilt gebruiken `New-EventLog` voor Windows Vista en latere versies van Windows, opent u Power shell met de optie als administrator uitvoeren.

Als u een gebeurtenis bron wilt maken in Windows Vista, Windows XP Professional of Windows Server 2003, moet u lid zijn van de groep Administrators op de computer.

Wanneer u een nieuw gebeurtenis logboek en een nieuwe gebeurtenis bron maakt, registreert het systeem de nieuwe bron voor het nieuwe logboek, maar wordt het logboek niet gemaakt totdat de eerste vermelding naar het bestand wordt geschreven.

Het besturings systeem slaat gebeurtenis logboeken op als bestanden.

Wanneer u een nieuw gebeurtenis logboek maakt, wordt het bijbehorende bestand opgeslagen in de `$env:SystemRoot\System32\Config` map op de opgegeven computer.

De bestands naam is de eerste acht tekens van de **logboek** eigenschap met de bestandsnaam extensie. evt.

## GERELATEERDE KOPPELINGEN

[Clear-EventLog](Clear-EventLog.md)

[Get-EventLog](Get-EventLog.md)

[Get-WinEvent](../Microsoft.PowerShell.Diagnostics/Get-WinEvent.md)

[Limit-EventLog](Limit-EventLog.md)

[Nieuw-gebeurtenis logboek](New-EventLog.md)

[Remove-EventLog](Remove-EventLog.md)

[Weer geven-EventLog](Show-EventLog.md)

[Write-EventLog](Write-EventLog.md)
