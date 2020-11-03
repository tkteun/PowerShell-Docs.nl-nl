---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 07/30/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/register-wmievent?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Register-WmiEvent
ms.openlocfilehash: be29ce6376dea7686c0c063cc5528fbc7d840a9d
ms.sourcegitcommit: 41b072f0b6046d619b0e7f758982783fb648a3d5
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/31/2020
ms.locfileid: "93251695"
---
# Register-WmiEvent

## SAMENVATTING
Abonneer u op een Windows Management Instrumentation-gebeurtenis (WMI).

## SYNTAXIS

### klasse (standaard)

```
Register-WmiEvent [-Namespace <String>] [-Credential <PSCredential>] [-ComputerName <String>] [-Class] <String>
 [-Timeout <Int64>] [[-SourceIdentifier] <String>] [[-Action] <ScriptBlock>] [-MessageData <PSObject>]
 [-SupportEvent] [-Forward] [-MaxTriggerCount <Int32>] [<CommonParameters>]
```

### query

```
Register-WmiEvent [-Namespace <String>] [-Credential <PSCredential>] [-ComputerName <String>] [-Query] <String>
 [-Timeout <Int64>] [[-SourceIdentifier] <String>] [[-Action] <ScriptBlock>] [-MessageData <PSObject>]
 [-SupportEvent] [-Forward] [-MaxTriggerCount <Int32>] [<CommonParameters>]
```

## BESCHRIJVING

De cmdlet meldt zich `Register-WmiEvent` aan Windows Management Instrumentation-gebeurtenissen (WMI) op de lokale computer of op een externe computer.

Wanneer de WMI-gebeurtenis is gegenereerd, wordt deze toegevoegd aan de gebeurtenis wachtrij in uw lokale sessie, zelfs als de gebeurtenis zich voordoet op een externe computer. Gebruik de cmdlet om gebeurtenissen in de gebeurtenis wachtrij op te halen `Get-Event` .

U kunt de para meters van gebruiken om u te `Register-WmiEvent` Abonneren op gebeurtenissen op externe computers en om de eigenschapwaarden op te geven van de gebeurtenissen die u kunnen helpen bij het identificeren van de gebeurtenis in de wachtrij. U kunt ook de **actie** parameter gebruiken om op te geven welke acties moeten worden uitgevoerd wanneer een gebeurtenis waarop een abonnement is gegeven, wordt gegenereerd.

Wanneer u zich abonneert op een gebeurtenis, wordt een gebeurtenis abonnee toegevoegd aan uw sessie. Als u de gebeurtenis abonnees in de sessie wilt ophalen, gebruikt u de `Get-EventSubscriber` cmdlet. Als u het abonnement wilt annuleren, gebruikt u de `Unregister-Event` cmdlet waarmee de gebeurtenis abonnee uit de sessie wordt verwijderd.

Nieuwe Common Information Model (CIM)-cmdlets, geïntroduceerd in Windows Power Shell 3,0, voert dezelfde taken uit als de WMI-cmdlets. De CIM-cmdlets voldoen aan de WS-Management (WSMan)-standaarden en met de CIM-standaard, waardoor de-cmdlets dezelfde technieken kunnen gebruiken voor het beheren van computers waarop het Windows-besturings systeem wordt uitgevoerd en die die andere besturings systemen uitvoeren. In plaats van met kunt `Register-WmiEvent` u overwegen de cmdlet [REGI ster-CimIndicationEvent](../cimcmdlets/register-cimindicationevent.md) te gebruiken.

## VOORBEELDEN

### Voor beeld 1: abonneren op gebeurtenissen die door een klasse zijn gegenereerd

Met deze opdracht wordt een abonnement genomen op de gebeurtenissen die worden gegenereerd door de **Win32_ProcessStartTrace** klasse. Deze klasse genereert een gebeurtenis wanneer een proces wordt gestart.

```powershell
Register-WmiEvent -Class 'Win32_ProcessStartTrace' -SourceIdentifier "ProcessStarted"
```

### Voor beeld 2: abonneren op het maken van gebeurtenissen voor een proces

Met deze opdracht wordt een query gebruikt om u te abonneren op gebeurtenissen voor het maken van Win32_process instanties.

```powershell
$wmiParameters = @{
  Query = "select * from __instancecreationevent within 5 where targetinstance isa 'win32_process'"
  SourceIdentifier = "WMIProcess"
  MessageData = "Test 01"
  TimeOut = 500
}
Register-WmiEvent @wmiParameters
```

### Voor beeld 3: een actie gebruiken om te reageren op een gebeurtenis

In dit voor beeld ziet u hoe u een actie kunt gebruiken om te reageren op een gebeurtenis. In dit geval `Start-Process` worden alle opdrachten in de huidige sessie naar een XML-bestand geschreven wanneer een proces wordt gestart.

```powershell
$action = { Get-History | where { $_.commandline -like "*start-process*" } | export-cliXml "commandHistory.clixml" }
Register-WmiEvent -Class 'Win32_ProcessStartTrace' -SourceIdentifier "ProcessStarted" -Action $action
```

```Output
Id    Name            State      HasMoreData   Location  Command
--    ----            -----      -----------   --------  -------
1     ProcessStarted  NotStarted False                   get-history | where {...
```

Wanneer u de **actie** parameter gebruikt, `Register-WmiEvent` retourneert een achtergrond taak die de gebeurtenis actie vertegenwoordigt. U kunt de **taak** -cmdlets, zoals `Get-Job` en, gebruiken `Receive-Job` om de gebeurtenis taak te beheren.

Zie About Jobs (Taken) voor meer informatie.

### Voor beeld 4: registreren voor gebeurtenissen op een externe computer

Dit voor beeld registreert voor gebeurtenissen op de externe computer Server01.

```powershell
Register-WmiEvent -Class 'Win32_ProcessStartTrace' -SourceIdentifier "Start" -Computername Server01
Get-Event -SourceIdentifier "Start"
```

WMI retourneert de gebeurtenissen naar de lokale computer en slaat deze op in de gebeurtenis wachtrij in de huidige sessie. Voer een lokale opdracht uit om de gebeurtenissen op te halen `Get-Event` .

## PARAMETERS

### -Actie

Geeft opdrachten voor het verwerken van gebeurtenissen. De opdrachten in de **actie** parameter worden uitgevoerd wanneer een gebeurtenis wordt gestart in plaats van de gebeurtenis naar de gebeurtenis wachtrij te verzenden. Plaats de opdrachten tussen accolades ( `{}` ) om een script blok te maken.

De waarde van de **actie** kan de `$Event` `$EventSubscriber` variabelen,,, `$Sender` `$EventArgs` en `$Args` automatisch bevatten. deze bevatten informatie over de gebeurtenis in het blok **actie** script. Zie about_Automatic_Variables voor meer informatie.

Wanneer u een actie opgeeft, `Register-WmiEvent` retourneert een gebeurtenis taak object dat die actie vertegenwoordigt. U kunt de-cmdlets gebruiken die het zelfstandige **taak** onderdeel (de **taak** -cmdlets) bevatten om de gebeurtenis taak te beheren.

```yaml
Type: System.Management.Automation.ScriptBlock
Parameter Sets: (All)
Aliases:

Required: False
Position: 101
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Klasse

Hiermee geeft u de gebeurtenis op waarop u bent geabonneerd. Geef de WMI-klasse op waarmee de gebeurtenissen worden gegenereerd. Een **klasse** -of **query** parameter is vereist in elke opdracht.

```yaml
Type: System.String
Parameter Sets: class
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -ComputerName

Hiermee geeft u de naam op van de computer waarop de opdracht wordt uitgevoerd. Standaard is dit de lokale computer.

Typ de NetBIOS-naam, een IP-adres of een Fully Qualified Domain Name van de computer. Als u de lokale computer wilt opgeven, typt u de naam van de computer, een punt ( `.` ) of localhost.

Deze para meter is niet gebaseerd op externe communicatie met Windows Power shell. U kunt de para meter **ComputerName** ook gebruiken als uw computer niet is geconfigureerd om externe opdrachten uit te voeren.

```yaml
Type: System.String
Parameter Sets: (All)
Aliases: Cn

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Credential

Hiermee geeft u een gebruikers account op dat is gemachtigd om deze actie uit te voeren. Standaard is dit de huidige gebruiker.

Typ een gebruikers naam, zoals gebruiker01 of Domain01\User01, of voer een **PSCredential** -object in, zoals het account dat is gegenereerd door de `Get-Credential` cmdlet. Als u een gebruikers naam typt, vraagt deze cmdlet u om een wacht woord.

```yaml
Type: System.Management.Automation.PSCredential
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Voorwaarts

Geeft aan dat deze cmdlet gebeurtenissen voor dit abonnement naar de sessie op de lokale computer verzendt.
Gebruik deze para meter als u zich registreert voor gebeurtenissen op een externe computer of in een externe sessie.

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

### -MaxTriggerCount

Hiermee geeft u het maximum aantal triggers op.

```yaml
Type: System.Int32
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -MessageData

Hiermee geeft u aanvullende gegevens op die moeten worden gekoppeld aan dit gebeurtenis abonnement. De waarde van deze para meter wordt weer gegeven in de eigenschap **MessageData** van alle gebeurtenissen die aan dit abonnement zijn gekoppeld.

```yaml
Type: System.Management.Automation.PSObject
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Naam ruimte

Hiermee geeft u de naam ruimte van de WMI-klasse op.

```yaml
Type: System.String
Parameter Sets: (All)
Aliases: NS

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Query uitvoeren

Hiermee geeft u een query in WMI Query Language (WQL) op waarmee de WMI-gebeurtenis klasse wordt geïdentificeerd, zoals: `select * from __InstanceDeletionEvent` .

```yaml
Type: System.String
Parameter Sets: query
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -SourceIdentifier

Hiermee geeft u een naam op die u voor het abonnement selecteert. De naam die u selecteert, moet uniek zijn in de huidige sessie. De standaard waarde is de GUID die Windows Power shell toewijst.

De waarde van deze para meter wordt weer gegeven in de waarde van de eigenschap **SourceIdentifier** van het object Subscriber en alle gebeurtenis objecten die zijn gekoppeld aan dit abonnement.

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: 100
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -SupportEvent

Geeft aan dat met deze cmdlet het gebeurtenis abonnement wordt verborgen. Gebruik deze para meter wanneer het huidige abonnement deel uitmaakt van een complexere gebeurtenis registratie mechanisme en niet onafhankelijk moet worden gedetecteerd.

Als u een abonnement wilt bekijken of annuleren dat is gemaakt met behulp van de para meter **SupportEvent** , geeft u de para meter **Force** van de `Get-EventSubscriber` `Unregister-Event` cmdlets op.

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

### -Time-out

Hiermee geeft u op hoelang Windows Power shell wacht tot deze opdracht is voltooid.

De standaard waarde, 0 (nul), houdt in dat er geen time-out is en zorgt ervoor dat Windows Power shell voor onbepaalde tijd wacht.

```yaml
Type: System.Int64
Parameter Sets: (All)
Aliases: TimeoutMSec

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### CommonParameters

Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable. Zie [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)voor meer informatie.

## INVOER

### Geen

U kunt geen objecten naar deze cmdlet pipeen.

## UITVOER

### Geen

Met deze cmdlet wordt geen uitvoer gegenereerd.

## OPMERKINGEN

Als u deze cmdlet wilt gebruiken in Windows Vista of een nieuwere versie van het Windows-besturings systeem, start u Windows Power shell met de optie als administrator uitvoeren.

Gebeurtenissen, gebeurtenis abonnementen en de gebeurtenis wachtrij bestaan alleen in de huidige sessie. Als u de huidige sessie sluit, wordt de gebeurtenis wachtrij verwijderd en wordt het gebeurtenis abonnement geannuleerd.

## GERELATEERDE KOPPELINGEN
