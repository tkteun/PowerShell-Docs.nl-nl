---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 04/09/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/trace-command?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Trace-Command
ms.openlocfilehash: afc08b263d75f8a728ce6d64cc7ede0a639df196
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 11/17/2020
ms.locfileid: "94705800"
---
# Trace-Command

## SAMENVATTING
Hiermee wordt een tracering van de opgegeven expressie of opdracht geconfigureerd en gestart.

## SYNTAXIS

### expressieset (standaard)

```
Trace-Command [-InputObject <PSObject>] [-Name] <String[]> [[-Option] <PSTraceSourceOptions>]
 [-Expression] <ScriptBlock> [-ListenerOption <TraceOptions>] [-FilePath <String>] [-Force] [-Debugger]
 [-PSHost] [<CommonParameters>]
```

### opdrachtset

```
Trace-Command [-InputObject <PSObject>] [-Name] <String[]> [[-Option] <PSTraceSourceOptions>]
 [-Command] <String> [-ArgumentList <Object[]>] [-ListenerOption <TraceOptions>] [-FilePath <String>] [-Force]
 [-Debugger] [-PSHost] [<CommonParameters>]
```

## BESCHRIJVING
De `Trace-Command` cmdlet configureert en start een tracering van de opgegeven expressie of opdracht.
Het werkt zoals set-TraceSource, behalve dat deze alleen van toepassing is op de opgegeven opdracht.

## VOORBEELDEN

### Voor beeld 1: verwerking van meta gegevens volgen, parameter binding en een expressie

In dit voor beeld wordt een tracering gestart van meta gegevens verwerking, parameter binding en het maken van de cmdlet en vernietiging van de `Get-Process Notepad` expressie.

```powershell
Trace-Command -Name metadata,parameterbinding,cmdlet -Expression {Get-Process Notepad} -PSHost
```

Hierbij wordt de para meter **name** gebruikt voor het opgeven van de tracerings bronnen, de **expressie** parameter voor het opgeven van de opdracht en de para meter **PSHost** voor het verzenden van de uitvoer naar de-console. Omdat er geen tracerings opties of listener-opties worden opgegeven, gebruikt de opdracht de standaard waarden:

- Alle voor de tracerings opties
- Geen voor de opties voor de listener

### Voor beeld 2: de acties van ParameterBinding-bewerkingen traceren

In dit voor beeld worden de acties van de **ParameterBinding** -bewerkingen van Power shell getraceerd tijdens het verwerken van een `Get-Alias` expressie die invoer van de pijp lijn afneemt.

```powershell
$A = "i*"
Trace-Command ParameterBinding {Get-Alias $Input} -PSHost -InputObject $A
```

In `Trace-Command` geeft de para meter **input object** een object door aan de expressie die tijdens de tracering wordt verwerkt.

Met de eerste opdracht wordt de teken reeks `i*` in de `$A` variabele opgeslagen. De tweede opdracht maakt gebruik `Trace-Command` van de cmdlet met de tracerings bron ParameterBinding. De **PSHost** para meter verzendt de uitvoer naar de-console.

De expressie die wordt verwerkt `Get-Alias $Input` , is, waarbij de `$Input` variabele is gekoppeld aan de para meter **input object** . De **input object** para meter geeft de variabele door `$A` aan de expressie. In feite is de opdracht die wordt verwerkt tijdens de tracering `Get-Alias -InputObject $A" or "$A | Get-Alias` .

## PARAMETERS

### -Argument List

Hiermee geeft u de para meters en parameter waarden voor de opdracht die wordt getraceerd. De alias voor **argument List** is **args**. Deze functie is vooral nuttig voor het opsporen van fouten in dynamische para meters.

Zie [about_Splatting](../Microsoft.PowerShell.Core/About/about_Splatting.md#splatting-with-arrays)voor meer informatie over het gedrag van **argument List**.

```yaml
Type: System.Object[]
Parameter Sets: commandSet
Aliases: Args

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Opdracht

Hiermee geeft u een opdracht die tijdens de tracering wordt verwerkt.

```yaml
Type: System.String
Parameter Sets: commandSet
Aliases:

Required: True
Position: 1
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Fout opsporingsprogramma

Geeft aan dat de cmdlet de tracerings uitvoer naar het fout opsporingsprogramma verzendt. U kunt de uitvoer bekijken in een fout opsporingsprogramma voor gebruikers modus of kernelmodus of in Visual Studio. Met deze para meter selecteert u ook de standaard traceer-listener.

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

### -Expressie

Hiermee geeft u de expressie op die tijdens de tracering wordt verwerkt. Plaats de expressie tussen accolades ( `{}` ).

```yaml
Type: System.Management.Automation.ScriptBlock
Parameter Sets: expressionSet
Aliases:

Required: True
Position: 1
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -FilePath

Hiermee geeft u een bestand op waarnaar de-cmdlet de tracerings uitvoer verzendt. Met deze para meter wordt ook de listener voor bestands tracering geselecteerd.

```yaml
Type: System.String
Parameter Sets: (All)
Aliases: PSPath, Path

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Force

Hiermee wordt de opdracht uitgevoerd zonder dat de gebruiker om bevestiging wordt gevraagd. Wordt gebruikt met de **filepath** -para meter. Zelfs met behulp van de para meter **forceren** , kan de cmdlet geen beveiligings beperkingen opheffen.

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

### -Input object

Hiermee wordt de invoer opgegeven van de expressie die tijdens de tracering wordt verwerkt. U kunt een variabele opgeven die de invoer vertegenwoordigt die de expressie accepteert, of een object door geven via de pijp lijn.

```yaml
Type: System.Management.Automation.PSObject
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### -ListenerOption

Hiermee geeft u optionele gegevens op voor het voor voegsel van elk tracerings bericht in de uitvoer. De aanvaardbare waarden voor deze parameter zijn:

- Geen
- LogicalOperationStack
- DateTime
- Timestamp
- Process
- Thread
- Procedures

**Geen** is de standaard instelling.

Als u meerdere opties wilt opgeven, scheidt u deze met komma's, maar zonder spaties, en plaatst u ze tussen dubbele aanhalings tekens, zoals ' ProcessID ', thread '.

```yaml
Type: System.Diagnostics.TraceOptions
Parameter Sets: (All)
Aliases:
Accepted values: None, LogicalOperationStack, DateTime, Timestamp, ProcessId, ThreadId, Callstack

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Name

Hiermee geeft u een matrix van Power shell-onderdelen die worden getraceerd. Voer de naam van de tracerings bron van elk onderdeel in. Joker tekens zijn toegestaan. Als u de tracerings bronnen op uw computer wilt zoeken, typt u `Get-TraceSource` .

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Optie

Bepaalt het type gebeurtenissen dat wordt getraceerd. De aanvaardbare waarden voor deze parameter zijn:

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
Parameter Sets: (All)
Aliases:
Accepted values: None, Constructor, Dispose, Finalizer, Method, Property, Delegates, Events, Exception, Lock, Error, Errors, Warning, Verbose, WriteLine, Data, Scope, ExecutionFlow, Assert, All

Required: False
Position: 2
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -PSHost

Geeft aan dat de cmdlet de tracerings uitvoer naar de Power shell-host verzendt. Met deze para meter wordt ook de PSHost Trace listener geselecteerd.

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

### CommonParameters

Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable. Zie [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)voor meer informatie.

## INVOER

### System. Management. Automation. PSObject

U kunt objecten pipeen die de invoer voor de expressie vertegenwoordigen `Trace-Command` .

## UITVOER

### System. Management. Automation. PSObject

Retourneert de opdracht tracering in de stroom voor fout opsporing.

## OPMERKINGEN

- Tracering is een methode die ontwikkel aars gebruiken voor het opsporen van fouten en het verfijnen van Program ma's. Bij het traceren worden gedetailleerde berichten over elke stap in de interne verwerking gegenereerd.

- De Power shell-cmdlets voor tracering zijn ontworpen om Power shell-ontwikkel aars te helpen, maar ze zijn beschikbaar voor alle gebruikers. U kunt vrijwel elk aspect van de functionaliteit van de shell bewaken.

- Als u de Power shell-onderdelen wilt vinden die zijn ingeschakeld voor tracering, typt u `Get-Help Get-TraceSource` .

  Een tracerings bron is het deel van elk Power Shell-onderdeel dat tracering beheert en tracerings berichten genereert voor het onderdeel. Als u een onderdeel wilt traceren, identificeert u de traceer bron.

  Een traceer-listener ontvangt de uitvoer van de tracering en geeft deze weer voor de gebruiker. U kunt ervoor kiezen om de tracerings gegevens naar een gebruikers modus of kernel-modus debugger te verzenden naar de host of console, naar een bestand of naar een aangepaste listener die is afgeleid van de **System. Diagnostics. TraceListener** -klasse.

- Wanneer u de opdrachtset para meter set gebruikt, verwerkt Power shell de opdracht net zoals deze in een pijp lijn zou worden verwerkt. Bijvoorbeeld: opdracht detectie wordt niet herhaald voor elk binnenkomend object.

- De namen van de para meters **name**, **expressie**, **Option** en **Command** zijn optioneel. Als u de parameter namen weglaat, moeten de niet-genaamde parameter waarden in deze volg orde worden weer gegeven: **naam**, **expressie**, **optie** of **naam**, **opdracht**, **optie**. Als u de parameter namen toevoegt, kunnen de para meters in een wille keurige volg orde worden weer gegeven.

## GERELATEERDE KOPPELINGEN

[Get-TraceSource](Get-TraceSource.md)

[Measure-Command](Measure-Command.md)

[Set-TraceSource](Set-TraceSource.md)

