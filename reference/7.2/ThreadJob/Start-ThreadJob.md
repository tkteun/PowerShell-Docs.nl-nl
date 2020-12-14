---
external help file: Microsoft.PowerShell.ThreadJob.dll-Help.xml
Locale: en-US
Module Name: ThreadJob
ms.date: 12/05/2020
online version: https://docs.microsoft.com/powershell/module/threadjob/start-threadjob?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Start-ThreadJob
ms.openlocfilehash: d08f883b232abadeacb445e5ba542b4b1fae023b
ms.sourcegitcommit: f9d855dd73b916559a22e337672dea3fbb11c634
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 12/07/2020
ms.locfileid: "96777701"
---
# Start-ThreadJob

## SAMENVATTING
Maakt achtergrond taken die vergelijkbaar zijn met de `Start-Job` cmdlet.

## SYNTAXIS

### Script Block

```
Start-ThreadJob [-ScriptBlock] <ScriptBlock> [-Name <String>] [-InitializationScript <ScriptBlock>]
 [-InputObject <PSObject>] [-ArgumentList <Object[]>] [-ThrottleLimit <Int32>]
 [-StreamingHost <PSHost>] [<CommonParameters>]
```

### Bestandspad

```
Start-ThreadJob [-FilePath] <String> [-Name <String>] [-InitializationScript <ScriptBlock>]
 [-InputObject <PSObject>] [-ArgumentList <Object[]>] [-ThrottleLimit <Int32>]
 [-StreamingHost <PSHost>] [<CommonParameters>]
```

## BESCHRIJVING

`Start-ThreadJob` maakt achtergrond taken die vergelijkbaar zijn met de `Start-Job` cmdlet. Het belangrijkste verschil is dat de taken die worden gemaakt in afzonderlijke threads binnen het lokale proces worden uitgevoerd. De taken gebruiken standaard de huidige werkmap van de aanroeper die de taak heeft gestart.

De cmdlet biedt ook ondersteuning voor de para meter **ThrottleLimit** om het aantal taken dat tegelijk wordt uitgevoerd, te beperken. Naarmate er meer taken worden gestart, worden deze in de wachtrij geplaatst en gewacht totdat het huidige aantal taken onder de vertragings limiet valt.

## VOORBEELDEN

### Voor beeld 1: Maak achtergrond taken met een thread limiet van 2

```powershell
Start-ThreadJob -ScriptBlock { 1..100 | % { sleep 1; "Output $_" } } -ThrottleLimit 2
Start-ThreadJob -ScriptBlock { 1..100 | % { sleep 1; "Output $_" } }
Start-ThreadJob -ScriptBlock { 1..100 | % { sleep 1; "Output $_" } }
Get-Job
```

```Output
Id   Name   PSJobTypeName   State        HasMoreData   Location     Command
--   ----   -------------   -----        -----------   --------     -------
1    Job1   ThreadJob       Running      True          PowerShell   1..100 | % { sleep 1;...
2    Job2   ThreadJob       Running      True          PowerShell   1..100 | % { sleep 1;...
3    Job3   ThreadJob       NotStarted   False         PowerShell   1..100 | % { sleep 1;...
```

### Voor beeld 2: de prestaties van Start-Job en Start-ThreadJob vergelijken

In dit voor beeld ziet u het verschil tussen `Start-Job` en `Start-ThreadJob` . De taken voeren de `Start-Sleep` cmdlet uit voor 1 seconde. Omdat de taken parallel worden uitgevoerd, is de totale uitvoerings tijd ongeveer 1 seconde, plus de tijd die nodig is om de taken te maken.

```powershell
# start five background jobs each running 1 second
Measure-Command {1..5 | % {Start-Job {Start-Sleep 1}} | Wait-Job} | Select-Object TotalSeconds
Measure-Command {1..5 | % {Start-ThreadJob {Start-Sleep 1}} | Wait-Job} | Select-Object TotalSeconds
```

```Output
TotalSeconds
------------
   5.7665849
   1.5735008
```

Nadat 1 seconde voor uitvoerings tijd is afgetrokken, ziet u dat `Start-Job` ongeveer 4,8 seconden duren om vijf taken te maken. `Start-ThreadJob` is 8 keer sneller, met ongeveer 0,6 seconden om vijf taken te maken. De resultaten kunnen variëren in uw omgeving, maar de relatieve verbetering moet hetzelfde zijn.

### Voor beeld 3: taken maken met input object

In dit voor beeld gebruikt het script blok de `$input` variabele om invoer te ontvangen van de para meter **input object** . Dit kan ook worden gedaan door pijpleiding objecten naar `Start-ThreadJob` .

```powershell
$j = Start-ThreadJob -InputObject (Get-Process pwsh) -ScriptBlock { $input | Out-String }
$j | Wait-Job | Receive-Job
```

```Output
 NPM(K)    PM(M)      WS(M)     CPU(s)      Id  SI ProcessName
 ------    -----      -----     ------      --  -- -----------
     94   145.80     159.02      18.31   18276   1 pwsh
    101   163.30     222.05      29.00   35928   1 pwsh
```

```powershell
$j = Get-Process pwsh | Start-ThreadJob -ScriptBlock { $input | Out-String }
$j | Wait-Job | Receive-Job
```

```Output
 NPM(K)    PM(M)      WS(M)     CPU(s)      Id  SI ProcessName
 ------    -----      -----     ------      --  -- -----------
     94   145.80     159.02      18.31   18276   1 pwsh
    101   163.30     222.05      29.00   35928   1 pwsh
```

### Voor beeld 4: taak uitvoer naar bovenliggende host streamen

Met de para meter **StreamingHost** kunt u een taak vertelt om alle host uitvoer naar een specifieke host te sturen. Zonder deze para meter wordt de uitvoer naar de gegevensstroom verzameling taak verplaatst en wordt deze niet weer gegeven in een host-console totdat u de uitvoer van de taak ontvangt.

Voor dit voor beeld wordt de huidige host door gegeven aan `Start-ThreadJob` het gebruik van de `$Host` Automatische variabele.

```powershell
PS> Start-ThreadJob -ScriptBlock { Read-Host 'Say hello'; Write-Warning 'Warning output' } -StreamingHost $Host

Id   Name   PSJobTypeName   State         HasMoreData     Location      Command
--   ----   -------------   -----         -----------     --------      -------
7    Job7   ThreadJob       NotStarted    False           PowerShell    Read-Host 'Say hello'; �

PS> Say hello: Hello
WARNING: Warning output
PS> Receive-Job -Id 7
Hello
WARNING: Warning output
PS>
```

U ziet dat de prompt van `Read-Host` wordt weer gegeven en u kunt invoer typen. Vervolgens wordt het bericht van `Write-Warning` weer gegeven. De `Receive-Job` cmdlet retourneert alle uitvoer van de taak.

## PARAMETERS

### -Argument List

Hiermee geeft u een matrix met argumenten, of parameter waarden, op voor het script dat is opgegeven door de para meters **filepath** of **script Block** .

**Argument List** moet de laatste para meter zijn op de opdracht regel. Alle waarden die de parameter naam volgen, worden geïnterpreteerd als waarden in de argumenten lijst.

```yaml
Type: System.Object[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -FilePath

Hiermee geeft u een script bestand moet worden uitgevoerd als een achtergrond taak. Voer het pad en de bestands naam van het script in. Het script moet zich op de lokale computer of in een map bevindt waartoe de lokale computer toegang heeft.

Wanneer u deze para meter gebruikt, wordt de inhoud van het opgegeven script bestand door Power shell naar een script blok geconverteerd en wordt het script blok als achtergrond taak uitgevoerd.

```yaml
Type: System.String
Parameter Sets: FilePath
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -InitializationScript

Geeft opdrachten die worden uitgevoerd voordat de taak wordt gestart. Plaats de opdrachten tussen accolades ( `{}` ) om een script blok te maken.

Gebruik deze para meter om de sessie voor te bereiden waarin de taak wordt uitgevoerd. U kunt dit bijvoorbeeld gebruiken om functies en modules toe te voegen aan de sessie.

```yaml
Type: System.Management.Automation.ScriptBlock
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Input object

Hiermee geeft u de objecten die worden gebruikt als invoer voor het-script blok. Het biedt ook ondersteuning voor pijplijn invoer. Gebruik de `$input` Automatische variabele in het script blok om toegang te krijgen tot de invoer objecten.

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

### -Name

Hiermee geeft u een beschrijvende naam op voor de nieuwe taak. U kunt de naam gebruiken om de taak te identificeren in andere taak-cmdlets, zoals de- `Stop-Job` cmdlet.

De standaard beschrijvende naam is ' job # ', waarbij ' # ' een rang nummer is dat voor elke taak wordt verhoogd.

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

### -Script Block

Hiermee geeft u de opdrachten op die in de achtergrond taak moeten worden uitgevoerd. Plaats de opdrachten tussen accolades ( `{}` ) om een script blok te maken. Gebruik de `$Input` Automatische variabele om toegang te krijgen tot de waarde van de para meter **input object** . Deze parameter is vereist.

```yaml
Type: System.Management.Automation.ScriptBlock
Parameter Sets: ScriptBlock
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -StreamingHost

Deze para meter biedt een veilige manier om `Write-Host` de uitvoer van een thread direct naar het door gegeven **PSHost** -object te laten gaan. Zonder IT `Write-Host` gaat uitvoer naar de gegevensstroom verzameling taak gegevens en pas weer in een host-console nadat de uitvoering van de taken is voltooid.

```yaml
Type: System.Management.Automation.Host.PSHost
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -ThrottleLimit

Deze para meter beperkt het aantal taken dat tegelijk wordt uitgevoerd. Wanneer taken worden gestart, worden deze in de wachtrij geplaatst en gewacht totdat een thread beschikbaar is in de thread groep om de taak uit te voeren. De standaard limiet is 5 threads.

De grootte van de thread groep is globaal voor de Power shell-sessie. Als u een **ThrottleLimit** in één aanroep opgeeft, wordt de limiet voor de volgende aanroepen in dezelfde sessie ingesteld.

```yaml
Type: System.Int32
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: 5
Accept pipeline input: False
Accept wildcard characters: False
```

### CommonParameters

Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable. Zie [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)voor meer informatie.

## INVOER

### System. Management. Automation. PSObject

## UITVOER

### ThreadJob.ThreadJob

## OPMERKINGEN

## GERELATEERDE KOPPELINGEN

[Begin taak](../Microsoft.PowerShell.Core/Start-Job.md)

[Stoppen-taak](../Microsoft.PowerShell.Core/Stop-Job.md)

[Receive-job](../Microsoft.PowerShell.Core/Receive-Job.md)
