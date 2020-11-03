---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/set-tracesource?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Set-TraceSource
ms.openlocfilehash: cef166404af546c35ccc3b0ffed4174515f74c15
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/07/2020
ms.locfileid: "93250369"
---
# Set-TraceSource

## SAMENVATTING
Hiermee configureert, start en stopt u het traceren van Power shell-onderdelen.

## SYNTAXIS

### optieset (standaard)

```
Set-TraceSource [-Name] <String[]> [[-Option] <PSTraceSourceOptions>] [-ListenerOption <TraceOptions>]
 [-FilePath <String>] [-Force] [-Debugger] [-PSHost] [-PassThru] [<CommonParameters>]
```

### removeAllListenersSet

```
Set-TraceSource [-Name] <String[]> [-RemoveListener <String[]>] [<CommonParameters>]
```

### removeFileListenersSet

```
Set-TraceSource [-Name] <String[]> [-RemoveFileListener <String[]>] [<CommonParameters>]
```

## BESCHRIJVING

De cmdlet **set-TraceSource** configureert, start en stopt een tracering van een Power Shell-onderdeel.
U kunt deze gebruiken om op te geven welke onderdelen moeten worden getraceerd en waar de tracerings uitvoer wordt verzonden.

## VOORBEELDEN

### Voor beeld 1: het ParameterBinding-onderdeel traceren

```
PS C:\> Set-TraceSource -Name "ParameterBinding" -Option ExecutionFlow -PSHost -ListenerOption "ProcessId,TimeStamp"
```

Met deze opdracht start u het traceren van het onderdeel ParameterBinding van Power shell.
Hierbij wordt de para meter *name* gebruikt voor het opgeven van de tracerings bron, de *optie* parameter voor het selecteren van de ExecutionFlow tracerings gebeurtenissen en de para meter *PSHost* om de Power shell-host-listener te selecteren, die de uitvoer naar de-console verzendt.
Met de para meter *ListenerOption* worden de ProcessID-en time stamp-waarden toegevoegd aan het voor voegsel van het tracerings bericht.

### Voor beeld 2: een tracering stoppen

```
PS C:\> Set-TraceSource -Name "ParameterBinding" -RemoveListener "Host"
```

Met deze opdracht stopt u de tracering van het ParameterBinding-onderdeel van Power shell.
Hierbij wordt de para meter *name* gebruikt voor het identificeren van het onderdeel dat wordt getraceerd en de para meter *RemoveListener* voor het identificeren van de traceer-listener.

## PARAMETERS

### -Fout opsporingsprogramma

Geeft aan dat de cmdlet de tracerings uitvoer naar het fout opsporingsprogramma verzendt.
U kunt de uitvoer bekijken in een fout opsporingsprogramma voor gebruikers modus of kernelmodus of in micro soft Visual Studio.
Met deze para meter selecteert u ook de standaard traceer-listener.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: optionsSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -FilePath

Hiermee geeft u een bestand op waarnaar met deze cmdlet de tracerings uitvoer wordt verzonden.
Met deze para meter wordt ook de listener voor bestands tracering geselecteerd.
Als u deze para meter gebruikt om de tracering te starten, gebruikt u de para meter *RemoveFileListener* om de tracering te stoppen.

```yaml
Type: System.String
Parameter Sets: optionsSet
Aliases: PSPath

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Force

Geeft aan dat de cmdlet een alleen-lezen bestand overschrijft.
Gebruiken met de *filepath* -para meter.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: optionsSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -ListenerOption

Hiermee geeft u optionele gegevens op voor het voor voegsel van elk tracerings bericht in de uitvoer.
De aanvaardbare waarden voor deze parameter zijn:

- Geen
- LogicalOperationStack
- DateTime
- Tijdstempel
- Process
- Thread
- Procedures

Geen is de standaard instelling.

Als u meerdere opties wilt opgeven, scheidt u deze met komma's, maar zonder spaties, en plaatst u ze tussen dubbele aanhalings tekens, zoals ' ProcessID ', thread '.

```yaml
Type: System.Diagnostics.TraceOptions
Parameter Sets: optionsSet
Aliases:
Accepted values: None, LogicalOperationStack, DateTime, Timestamp, ProcessId, ThreadId, Callstack

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Name

Hiermee geeft u op welke onderdelen worden getraceerd.
Voer de naam van de tracerings bron van elk onderdeel in.
Joker tekens zijn toegestaan.

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: True
```

### -Optie

Hiermee geeft u het type gebeurtenissen op dat wordt getraceerd.
De aanvaardbare waarden voor deze parameter zijn:

- Geen
- Constructor
- Gooien
- Volt ooien
- Methode
- Eigenschap
- Gedelegeerden
- Gebeurtenissen
- Uitzondering
- Vergrendelen
- Fout
- Fouten
- Waarschuwing
- Uitgebreid
- WriteLine
- Gegevens
- Bereik
- ExecutionFlow
- Assert
- Alles

Dit is de standaard instelling.

De volgende waarden zijn combi Naties van andere waarden:

- ExecutionFlow: (constructor, Dispose, FINALIZE, methode, gemachtigden, gebeurtenissen en bereik)
- Gegevens: (constructor, Dispose, FINALIZE, eigenschap, verbose en WriteLine)
- Fouten: (fout en uitzonde ring).

Als u meerdere opties wilt opgeven, scheidt u deze met komma's, maar zonder spaties, en plaatst u ze tussen dubbele aanhalings tekens, zoals ' constructor, Dispose '.

```yaml
Type: System.Management.Automation.PSTraceSourceOptions
Parameter Sets: optionsSet
Aliases:
Accepted values: None, Constructor, Dispose, Finalizer, Method, Property, Delegates, Events, Exception, Lock, Error, Errors, Warning, Verbose, WriteLine, Data, Scope, ExecutionFlow, Assert, All

Required: False
Position: 1
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -PassThru

Retourneert een object dat het item vertegenwoordigt waarmee u werkt.
Deze cmdlet genereert standaard geen uitvoer.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: optionsSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -PSHost

ndicates dat deze cmdlet de tracerings uitvoer naar de Power shell-host verzendt.
Met deze para meter wordt ook de PSHost Trace listener geselecteerd.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: optionsSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -RemoveFileListener

Hiermee stopt u de tracering door de listener voor bestands tracering die is gekoppeld aan het opgegeven bestand te verwijderen.
Voer het pad en de bestands naam van het uitvoer bestand voor tracering in.

```yaml
Type: System.String[]
Parameter Sets: removeFileListenersSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -RemoveListener

Stopt de tracering door de traceer-listener te verwijderen.

Gebruik de volgende waarden met *RemoveListener* :

- Als u PSHost (console) wilt verwijderen, typt u `Host` .
- Om het fout opsporingsprogramma te verwijderen, typt u `Debug` .
- Als u alle traceer-listeners wilt verwijderen, typt u `*` .

Als u de listener voor bestands tracering wilt verwijderen, gebruikt u de para meter *RemoveFileListener* .

```yaml
Type: System.String[]
Parameter Sets: removeAllListenersSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### CommonParameters

Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable. Zie [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)voor meer informatie.

## INVOER

### System. String

U kunt een teken reeks die een naam bevat, door sluizen naar **set-TraceSource**.

## UITVOER

### Geen of System. Management. Automation. PSTraceSource

Wanneer u de para meter *PassThru* gebruikt, genereert **set-TraceSource** een **System. Management. Automation. PSTraceSource** -object dat de traceer sessie vertegenwoordigt.
Anders wordt met deze cmdlet geen uitvoer gegenereerd.

## OPMERKINGEN

* Tracering is een methode die ontwikkel aars gebruiken voor het opsporen van fouten en het verfijnen van Program ma's. Bij het traceren worden gedetailleerde berichten over elke stap in de interne verwerking gegenereerd.

  De Power shell-cmdlets voor tracering zijn ontworpen om Power shell-ontwikkel aars te helpen, maar ze zijn beschikbaar voor alle gebruikers.
U kunt vrijwel elk aspect van de functionaliteit van Power shell bewaken.

  Een tracerings bron is het deel van elk Power Shell-onderdeel dat tracering beheert en tracerings berichten genereert voor het onderdeel.
Als u een onderdeel wilt traceren, identificeert u de traceer bron.

  Een traceer-listener ontvangt de uitvoer van de tracering en geeft deze weer voor de gebruiker.
U kunt ervoor kiezen om de tracerings gegevens te verzenden naar een fout opsporingsprogramma voor gebruikers modus of kernel-modus, naar de-console, naar een bestand of naar een aangepaste listener die is afgeleid van de **System. Diagnostics. TraceListener** -klasse.

* Als u een tracering wilt starten, gebruikt u de para meter *name* om een tracerings bron op te geven en de para meters *filepath* , *debugger* of *PSHost* om een listener op te geven (een bestemming voor de uitvoer). Gebruik de para meter *Options* om te bepalen welke typen gebeurtenissen worden getraceerd en de para meter *ListenerOption* om de uitvoer van de tracering te configureren.
* Als u de configuratie van een tracering wilt wijzigen, voert u de opdracht **set-TraceSource** in, zoals u een tracering wilt starten. Power Shell heeft gedetecteerd dat de tracerings bron al wordt getraceerd. De tracering wordt gestopt, de nieuwe configuratie wordt toegevoegd en de tracering wordt gestart of opnieuw gestart.
* Als u een tracering wilt stoppen, gebruikt u de para meter *RemoveListener* . Als u een tracering wilt stoppen die gebruikmaakt van de file listener (een tracering die is gestart met de para meter *filepath* ), gebruikt u de para meter *RemoveFileListener* . Wanneer u de listener verwijdert, wordt de tracering gestopt.
* Gebruik Get-TraceSource om te bepalen welke onderdelen kunnen worden getraceerd. De tracerings bronnen voor elke module worden automatisch geladen wanneer het onderdeel wordt gebruikt en ze worden weer gegeven in de uitvoer van **Get-TraceSource**.

## GERELATEERDE KOPPELINGEN

[Get-TraceSource](Get-TraceSource.md)

[Tracering-opdracht](Trace-Command.md)
