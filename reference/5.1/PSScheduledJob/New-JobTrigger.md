---
external help file: Microsoft.PowerShell.ScheduledJob.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: PSScheduledJob
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/psscheduledjob/new-jobtrigger?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: New-JobTrigger
ms.openlocfilehash: de49ab937c6f3a8187f5aecd6aafc81425b8cd00
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/07/2020
ms.locfileid: "93250303"
---
# New-JobTrigger

## SAMENVATTING
Hiermee maakt u een taak trigger voor een geplande taak.

## SYNTAXIS

### Eenmaal (standaard)

```
New-JobTrigger [-RandomDelay <TimeSpan>] -At <DateTime> [-Once] [-RepetitionInterval <TimeSpan>]
 [-RepetitionDuration <TimeSpan>] [-RepeatIndefinitely] [<CommonParameters>]
```

### Dagelijks

```
New-JobTrigger [-DaysInterval <Int32>] [-RandomDelay <TimeSpan>] -At <DateTime> [-Daily] [<CommonParameters>]
```

### Wekelijks

```
New-JobTrigger [-WeeksInterval <Int32>] [-RandomDelay <TimeSpan>] -At <DateTime> -DaysOfWeek <DayOfWeek[]>
 [-Weekly] [<CommonParameters>]
```

### AtStartup

```
New-JobTrigger [-RandomDelay <TimeSpan>] [-AtStartup] [<CommonParameters>]
```

### AtLogon

```
New-JobTrigger [-RandomDelay <TimeSpan>] [-User <String>] [-AtLogOn] [<CommonParameters>]
```

## BESCHRIJVING
Met de cmdlet **New-JobTrigger** wordt een taak trigger gemaakt waarmee een geplande taak wordt gestart in een eenmalige of terugkerende planning, of wanneer er een gebeurtenis optreedt.

U kunt het **ScheduledJobTrigger** -object gebruiken dat **New-JobTrigger** retourneert om een taak trigger in te stellen voor een nieuwe of bestaande geplande taak.
U kunt ook een taak trigger maken met behulp van de cmdlet Get-JobTrigger om de taak trigger van een bestaande geplande taak te verkrijgen of door een hash-tabel waarde te gebruiken om een taak trigger weer te geven.

Wanneer u een taak trigger maakt, controleert u de standaard waarden van de opties die zijn opgegeven door de New-ScheduledJobOption-cmdlet.
Deze opties, die dezelfde geldige en standaard waarden hebben als de overeenkomstige opties in **taak planner** , beïnvloeden de planning en timing van geplande taken.

**New-JobTrigger** is een van een verzameling taak planning-cmdlets in de PSScheduledJob-module die is opgenomen in Windows Power shell.

Zie de onderwerpen in de PSScheduledJob-module voor meer informatie over geplande taken.
Importeer de PSScheduledJob-module en typ vervolgens: `Get-Help about_Scheduled*` of zie about_Scheduled_Jobs.

Deze cmdlet is geïntroduceerd in Windows Power Shell 3,0.

## VOORBEELDEN

### Voor beeld 1: eenmaal plannen

```
PS C:\> New-JobTrigger -Once -At "1/20/2012 3:00 AM"
```

Met deze opdracht wordt de cmdlet **New-JobTrigger** gebruikt om een taak trigger te maken waarmee slechts één keer een geplande taak wordt gestart.
De waarde van de *at* -para meter is een teken reeks die door Windows Power shell wordt geconverteerd naar een **DateTime** -object.
De waarde *van de at* -para meter bevat een expliciete datum, niet alleen een tijd.
Als de datum is wegge laten, wordt de trigger gemaakt met de huidige datum en 3:00 AM-tijd, die waarschijnlijk een tijd in het verleden aangeeft.

### Voor beeld 2: dagelijks plannen

```
PS C:\> New-JobTrigger -Daily -At "4:15 AM" -DaysInterval 3
Id         Frequency       Time                   DaysOfWeek              Enabled
--         ---------       ----                   ----------              -------
0          Daily           9/21/2012 4:15:00 AM                           True
```

Met deze opdracht wordt een taak trigger gemaakt waarmee elke 3 dagen om 4:15 uur een geplande taak wordt gestart.

Omdat de waarde van de para meter *at* geen datum bevat, wordt de huidige datum gebruikt als datum waarde in het **DateTime** -object.
Als de datum en tijd zich in het verleden bevindt, wordt de geplande taak gestart bij de volgende instantie, die 3 dagen later van de waarde *bij* para meter is.

### Voor beeld 3: wekelijks schema

```
PS C:\> New-JobTrigger -Weekly -DaysOfWeek Monday, Wednesday, Friday -At "23:00" -WeeksInterval 4
Id Frequency Time                  DaysOfWeek                  Enabled
-- --------- ----                  ----------                  -------
0  Weekly    9/21/2012 11:00:00 PM {Monday, Wednesday, Friday} True
```

Met deze opdracht wordt een taak trigger gemaakt waarmee elke 4 weken op maandag, woensdag en vrijdag om 2300 uur (11:00 PM) een geplande taak wordt gestart.

U kunt ook de waarde van de para meter *DaysOfWeek* invoeren in gehele getallen, zoals `-DaysOfWeek 1, 5` .

### Voor beeld 4: aanmeldings schema

```
PS C:\> New-JobTrigger -AtLogOn -User Domain01\Admin01
```

Met deze opdracht wordt een taak trigger gemaakt waarmee een geplande taak wordt gestart wanneer de domein beheerder zich bij de computer aanmeldt.

### Voor beeld 5: een wille keurige vertraging gebruiken

```
PS C:\> New-JobTrigger -Daily -At 1:00 -RandomDelay 00:20:00
```

Met deze opdracht wordt een taak trigger gemaakt waarmee elke dag om 1:00 's morgen een geplande taak wordt gestart.
De opdracht gebruikt de para meter *RandomDelay* om de maximale vertraging in te stellen op 20 minuten.
Als gevolg hiervan wordt de taak elke dag uitgevoerd tussen 1:00 uur en 1:20 uur, met het interval waarbij pseudo-wille keurig wordt gevarieerd.

U kunt een wille keurige vertraging gebruiken voor steek proeven, taak verdeling en andere beheer taken.
Wanneer u de vertragings waarde instelt, controleert u de ingangs-en standaard waarden van de cmdlet New-ScheduledJobOption en coördineert u de vertraging met de optie-instellingen.

### Voor beeld 6: een taak trigger maken voor een nieuwe geplande taak

```
The first command uses the **New-JobTrigger** cmdlet to create a job trigger that starts a job every Monday, Wednesday, and Friday at 12:01 AM. The command saves the job trigger in the $T variable.
PS C:\> $T = New-JobTrigger -Weekly -DaysOfWeek 1,3,5 -At 12:01AM


The second command uses the Register-ScheduledJob cmdlet to create a scheduled job that starts a job every Monday, Wednesday, and Friday at 12:01 AM. The value of the *Trigger* parameter is the trigger that is stored in the $T variable.
PS C:\> Register-ScheduledJob -Name Test-HelpFiles -FilePath C:\Scripts\Test-HelpFiles.ps1 -Trigger $T
```

Deze opdrachten gebruiken een taak trigger om een nieuwe geplande taak te maken.

### Voor beeld 7: een taak trigger toevoegen aan een geplande taak

```
PS C:\> Add-JobTrigger -Name SynchronizeApps -Trigger (New-JobTrigger -Daily -At 3:10AM)
```

In dit voor beeld ziet u hoe u een taak trigger toevoegt aan een bestaande geplande taak.
U kunt meerdere taak triggers toevoegen aan een geplande taak.

De opdracht gebruikt de cmdlet Add-JobTrigger om de taak trigger toe te voegen aan de geplande taak SynchronizeApps.
De waarde van de *trigger* parameter is een **nieuwe JobTrigger** opdracht waarmee de taak elke dag om 3:10 uur wordt uitgevoerd.

Wanneer de opdracht is voltooid, is SynchronizeApps een geplande taak die wordt uitgevoerd op het tijdstip dat is opgegeven door de taak trigger.

### Voor beeld 8: een herhalende taak trigger maken

```
PS C:\> New-JobTrigger -Once -At "09/12/2013 1:00:00" -RepetitionInterval (New-TimeSpan -Hours 1) -RepetitionDuration (New-Timespan -Hours 48)
```

Met deze opdracht wordt een taak trigger gemaakt waarmee elke 60 minuten voor 48 uur vanaf 12 september 2013 op 1:00 AM een taak wordt uitgevoerd.

### Voor beeld 9: een herhaalde taak trigger stoppen

```
PS C:\> Get-JobTrigger -Name SecurityCheck | Set-JobTrigger -RepetitionInterval 0:00 -RepetitionDuration 0:00
```

Met deze opdracht wordt de SecurityCheck-taak geforceerd gestopt, die wordt geactiveerd om elke 60 minuten uit te voeren totdat de taak trigger verloopt.

Om te voor komen dat de taak wordt herhaald, gebruikt de opdracht de Get-JobTrigger om de taak trigger van de SecurityCheck-taak te verkrijgen en de Set-JobTrigger-cmdlet om het herhalings interval en de duur van de herhaling van de taak trigger te wijzigen in nul (0).

### Voor beeld 10: een taak trigger per uur maken

```
PS C:\> New-JobTrigger -Once -At "9/21/2012 0am" -RepetitionInterval (New-TimeSpan -Hour 12) -RepetitionDuration ([TimeSpan]::MaxValue)
```

Met de volgende opdracht maakt u een taak trigger die elke 12 uur een geplande taak uitvoert voor een onbepaalde periode.
De planning begint morgen (9/21/2012) om middernacht (0:00 uur).

## PARAMETERS

### -At
De taak wordt gestart op de opgegeven datum en tijd.
Voer een **DateTime** -object in, zoals een teken reeks die wordt geretourneerd door de cmdlet Get-Date, of een String die kan worden geconverteerd naar een datum en tijd, zoals ' 19 April 2012 15:00 ', ' 12/31 ' of ' 3am '.
Als u geen element van de datum opgeeft, zoals het jaar, heeft de datum in de trigger het bijbehorende element van de huidige datum.

Wanneer u de para meter *Once* gebruikt, stelt u de waarde van de para meter *in* op een datum en tijd in de toekomst.
Omdat de standaard datum in een **DateTime** -object de huidige datum is, als u een tijd opgeeft vóór de huidige tijd zonder een expliciete datum, wordt de taak trigger voor een tijd in het verleden gemaakt.

**DateTime** -objecten en teken reeksen die worden geconverteerd naar **DateTime** -objecten, worden automatisch aangepast zodat ze compatibel zijn met de datum-en tijd notaties die zijn geselecteerd voor de lokale computer in de regio en taal in het configuratie scherm.

```yaml
Type: System.DateTime
Parameter Sets: Once, Daily, Weekly
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -AtLogOn
Hiermee wordt de geplande taak gestart wanneer de opgegeven gebruikers zich aanmelden bij de computer.
Als u een gebruiker wilt opgeven, gebruikt u de para meter *User* .

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: AtLogon
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -AtStartup
De geplande taak wordt gestart wanneer Windows wordt gestart.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: AtStartup
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Dagelijks
Geeft een terugkerende dagelijkse taak planning op.
Gebruik de andere para meters in de para meter *dagelijks* instellen om de details van de planning op te geven.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: Daily
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -DaysInterval
Hiermee geeft u het aantal dagen op dat in een dagelijks schema voor komt.
Een waarde van 3 begint bijvoorbeeld met de geplande taak op dagen 1, 4, 7, enzovoort.
De standaardwaarde is 1.

```yaml
Type: System.Int32
Parameter Sets: Daily
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -DaysOfWeek
Hiermee geeft u de dagen van de week op waarop een wekelijkse geplande taak wordt uitgevoerd.
Voer namen van dagen in, zoals "maandag" of gehele getallen van 0-6, waarbij 0 staat voor zondag.
Deze para meter is vereist in de set met wekelijkse para meters.

De namen van dagen worden geconverteerd naar hun gehele waarden in de taak trigger.
Wanneer u namen van dagen tussen aanhalings tekens in een opdracht plaatst, plaatst u de naam van elke dag in afzonderlijke aanhalings tekens, zoals "maandag", "dinsdag".
Als u meerdere namen van dagen in een enkel aanhalings teken plaatst, worden de bijbehorende waarden voor gehele getallen opgeteld.
Bijvoorbeeld: ' maandag, dinsdag ' (1, 2) resulteert in een waarde van ' woensdag ' (3).

```yaml
Type: System.DayOfWeek[]
Parameter Sets: Weekly
Aliases:
Accepted values: Sunday, Monday, Tuesday, Wednesday, Thursday, Friday, Saturday

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Eenmaal
Hiermee geeft u een niet-terugkerende (eenmalige) of aangepaste herhalende planning op.
Als u een herhalings schema wilt maken, gebruikt u de para meter *Once* met de para meters *RepetitionDuration* en *RepetitionInterval* .

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: Once
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -RandomDelay
Hiermee schakelt u een wille keurige vertraging in die begint op de geplande begin tijd en stelt de maximale vertragings waarde in.
De lengte van de vertraging is ingesteld op wille keurige pseudo voor elk begin en varieert van geen vertraging tot de tijd die is opgegeven door de waarde van deze para meter.
De standaard waarde, nul (00:00:00), schakelt de wille keurige vertraging uit.

Voer een time span-object in, zoals het resultaat van de cmdlet New-TimeSpan, of voer een waarde in \<hours\> : \<minutes\> : \<seconds\> Format, die automatisch wordt geconverteerd naar een **time span** -object.

```yaml
Type: System.TimeSpan
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -RepeatIndefinitely
Deze para meter, die beschikbaar is in Windows Power Shell 4,0, elimineert de nood zaak om een **time span. MaxValue** -waarde voor de para meter *RepetitionDuration* op te geven om een geplande taak herhaaldelijk uit te voeren voor een onbepaalde periode.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: Once
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -RepetitionDuration
Herhaalt de taak totdat de opgegeven tijd verloopt.
De frequentie van de herhaling wordt bepaald door de waarde van de para meter *RepetitionInterval* .
Als de waarde van **RepetitionInterval** bijvoorbeeld 5 minuten is en de waarde van **RepetitionDuration** 2 uur is, wordt de taak gedurende twee uur elke vijf minuten geactiveerd.

Voer een time span-object in, zoals een voor het retour neren van de cmdlet New-TimeSpan, of een teken reeks die kan worden geconverteerd naar een time span-object, zoals ' 1:05:30 '.

Als u een taak voor onbepaalde tijd wilt uitvoeren, voegt u in plaats daarvan de para meter *RepeatIndefinitely* toe.

Als u een taak wilt stoppen voordat de herhalings duur van de taak trigger verloopt, gebruikt u de Set-JobTrigger cmdlet om de waarde *RepetitionDuration* in te stellen op nul (0).

Deze para meter is alleen geldig wanneer de para meters *eenmaal* , *at* en *RepetitionInterval* worden gebruikt in de opdracht.

```yaml
Type: System.TimeSpan
Parameter Sets: Once
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -RepetitionInterval
Hiermee wordt de taak herhaald op het opgegeven tijds interval.
Als de waarde van deze para meter bijvoorbeeld 2 uur is, wordt de taak elke twee uur geactiveerd.
De standaard waarde, 0, herhaalt de taak niet.

Voer een time span-object in, zoals een voor het retour neren van de cmdlet New-TimeSpan, of een teken reeks die kan worden geconverteerd naar een time span-object, zoals ' 1:05:30 '.

Deze para meter is alleen geldig wanneer de *eenmalige* , *at* -en *RepetitionDuration* -para meters worden gebruikt in de opdracht.

```yaml
Type: System.TimeSpan
Parameter Sets: Once
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -User
Hiermee geeft u de gebruikers die een geplande taak *AtLogon* starten.
Voer de naam van een gebruiker in \<UserName\> of in of \<Domain\Username\> Voer een asterisk ( \* ) in om alle gebruikers weer te geven.
De standaard waarde is alle gebruikers.

```yaml
Type: System.String
Parameter Sets: AtLogon
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Wekelijks
Hiermee geeft u een terugkerende wekelijkse taak planning op.
Gebruik de andere para meters in de set met wekelijkse para meters om de details van de planning op te geven.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: Weekly
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -WeeksInterval
Hiermee geeft u het aantal weken tussen exemplaren op voor een wekelijks taak schema.
Een waarde van 3 begint bijvoorbeeld met de geplande taak op weken 1, 4, 7 enzovoort.
De standaardwaarde is 1.

```yaml
Type: System.Int32
Parameter Sets: Weekly
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

### Geen
U kunt geen invoer van een pipe naar deze cmdlet.

## UITVOER

### Micro soft. Power shell. ScheduledJob. ScheduledJobTrigger

## OPMERKINGEN

* Taak triggers worden niet op schijf opgeslagen. Geplande taken worden echter op schijf opgeslagen en u kunt de Get-JobTrigger gebruiken om de taak trigger van een geplande taak op te halen.
* **New-JobTrigger** voor komt niet dat u een taak trigger maakt waarmee geen geplande taak wordt uitgevoerd, zoals eenmalige trigger voor een datum in het verleden.
* De Register-ScheduledJob-cmdlet accepteert een ScheduledJobTrigger-object, zoals het dat wordt geretourneerd door de cmdlets **New-JobTrigger** of Get-JobTrigger, of een hash-tabel met trigger waarden.

  Als u een hash-tabel wilt verzenden, gebruikt u de volgende sleutels.

  `@{Frequency="Once" (or Daily, Weekly, AtStartup, AtLogon);At="3am"` (of een wille keurige geldige tijd reeks); `DaysOfWeek="Monday", "Wednesday"` (of een combi natie van namen van dagen); `Interval=2` (of een geldig frequentie-interval); `RandomDelay="30minutes"` (of een wille keurige geldige time span-teken reeks); `User="Domain1\User01` (of een geldige gebruiker; wordt alleen gebruikt met de *AtLogon* -frequentie waarde)}

## GERELATEERDE KOPPELINGEN

[Add-JobTrigger](Add-JobTrigger.md)

[Disable-JobTrigger](Disable-JobTrigger.md)

[Disable-ScheduledJob](Disable-ScheduledJob.md)

[Enable-JobTrigger](Enable-JobTrigger.md)

[Enable-ScheduledJob](Enable-ScheduledJob.md)

[Get-JobTrigger](Get-JobTrigger.md)

[Get-ScheduledJob](Get-ScheduledJob.md)

[Get-ScheduledJobOption](Get-ScheduledJobOption.md)

[New-JobTrigger](New-JobTrigger.md)

[New-ScheduledJobOption](New-ScheduledJobOption.md)

[REGI ster-ScheduledJob](Register-ScheduledJob.md)

[Remove-JobTrigger](Remove-JobTrigger.md)

[Set-JobTrigger](Set-JobTrigger.md)

[Set-ScheduledJob](Set-ScheduledJob.md)

[Set-ScheduledJobOption](Set-ScheduledJobOption.md)

[Registratie ongedaan maken-ScheduledJob](Unregister-ScheduledJob.md)
