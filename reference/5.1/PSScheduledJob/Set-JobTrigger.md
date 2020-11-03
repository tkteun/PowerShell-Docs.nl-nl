---
external help file: Microsoft.PowerShell.ScheduledJob.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: PSScheduledJob
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/psscheduledjob/set-jobtrigger?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Set-JobTrigger
ms.openlocfilehash: 8d1b12b67ccf695e1c4b948e6eeecf292c588af4
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/07/2020
ms.locfileid: "93250297"
---
# Set-JobTrigger

## SAMENVATTING
Hiermee wijzigt u de taak trigger van een geplande taak.

## SYNTAXIS

```
Set-JobTrigger [-InputObject] <ScheduledJobTrigger[]> [-DaysInterval <Int32>] [-WeeksInterval <Int32>]
 [-RandomDelay <TimeSpan>] [-At <DateTime>] [-User <String>] [-DaysOfWeek <DayOfWeek[]>] [-AtStartup]
 [-AtLogOn] [-Once] [-RepetitionInterval <TimeSpan>] [-RepetitionDuration <TimeSpan>] [-RepeatIndefinitely]
 [-Daily] [-Weekly] [-PassThru] [<CommonParameters>]
```

## BESCHRIJVING
Met de cmdlet **set-JobTrigger** worden de eigenschappen van de taak triggers van geplande taken gewijzigd.
U kunt deze gebruiken om de tijd of frequentie te wijzigen waarmee de taken worden gestart of om te wijzigen van een op tijd gebaseerde planningen in schema's die worden geactiveerd door een aanmelding of het opstarten.

Een taak trigger definieert een terugkerende planning of voor waarden voor het starten van een geplande taak.
Hoewel taak triggers niet op schijf worden opgeslagen, kunt u de taak triggers van geplande taken wijzigen, die op schijf worden opgeslagen.

Als u een taak trigger van een geplande taak wilt wijzigen, moet u beginnen met behulp van de cmdlet Get-JobTrigger om de taak trigger van een geplande taak op te halen.
Vervolgens pipet u de trigger in op **set JobTrigger** of slaat u de trigger op in een variabele en gebruikt u de para meter *input object* van de cmdlet **set-JobTrigger** om de trigger te identificeren.
Gebruik de resterende para meters van **set-JobTrigger** om de taak trigger te wijzigen.

Wanneer u het type van een taak trigger wijzigt, zoals het wijzigen van een taak trigger van een dagelijkse of wekelijkse trigger naar een *AtLogon* trigger, worden de oorspronkelijke trigger eigenschappen verwijderd.
Als u echter de waarden van de trigger wijzigt, maar niet het type ervan, zoals het wijzigen van de dagen in een wekelijkse trigger, worden alleen de eigenschappen die u opgeeft, gewijzigd.
Alle andere eigenschappen van de oorspronkelijke taak trigger blijven behouden.

**Set-JobTrigger** is een van een verzameling taak planning-cmdlets in de PSScheduledJob-module die is opgenomen in Windows Power shell.

Zie de onderwerpen in de PSScheduledJob-module voor meer informatie over geplande taken.
Importeer de PSScheduledJob-module en typ vervolgens: `Get-Help about_Scheduled*`  of zie about_Scheduled_Jobs.

Deze cmdlet is geïntroduceerd in Windows Power Shell 3,0.

## VOORBEELDEN

### Voor beeld 1: de dagen in een taak trigger wijzigen

```
PS C:\> Get-JobTrigger -Name "DeployPackage"
Id         Frequency       Time                   DaysOfWeek              Enabled
--         ---------       ----                   ----------              -------
1          Weekly          9/29/2011 12:00:00 AM  {Wednesday, Saturday}   True

The second command uses the Get-JobTrigger cmdlet to get the job trigger of the DeployPackage scheduled job. A pipeline operator (|) sends the trigger to the **Set-JobTrigger** cmdlet, which changes the job trigger so that it starts the DeployPackage job on Wednesdays and Sundays. The command uses the *Passthru* parameter to return the trigger after the change.
PS C:\> Get-JobTrigger -Name "DeployPackage" | Set-JobTrigger -DaysOfWeek "Wednesday", "Sunday" -Passthru
Id         Frequency       Time                   DaysOfWeek              Enabled
--         ---------       ----                   ----------              -------
1          Weekly          9/29/2011 12:00:00 AM  {Wednesday, Sunday}     True
```

In dit voor beeld ziet u hoe u de dagen in een wekelijkse taak trigger wijzigt.

De eerste opdracht gebruikt de cmdlet Get-JobTrigger om de taak trigger van de geplande taak DeployPackage te verkrijgen.
De uitvoer laat zien dat de trigger de taak wordt gestart om middernacht op Wednesdays en zaterdag.

Deze opdracht is niet vereist. het is alleen opgenomen om het effect van de wijziging van de trigger weer te geven.

### Voor beeld 2: het taak trigger type wijzigen

```
PS C:\> Get-JobTrigger -Name "Inventory"
Id         Frequency       Time                   DaysOfWeek              Enabled
--         ---------       ----                   ----------              -------
1          Daily           9/27/2011 11:00:00 PM                          True
2          AtStartup                                                      True

The second command uses the **Get-JobTrigger** cmdlet to get the *AtStartup* job trigger of the Inventory job. The command uses the *TriggerID* parameter to identify the job trigger. A pipeline operator (|) sends the job trigger to the **Set-JobTrigger** cmdlet, which changes it to a weekly job trigger that runs every four weeks on Monday at midnight. The command uses the *Passthru* parameter to return the trigger after the change.
PS C:\> Get-JobTrigger -Name "Inventory" -TriggerID 2 | Set-JobTrigger -Weekly -WeeksInterval 4 -DaysOfWeek Monday -At "12:00 AM"
Id         Frequency       Time                   DaysOfWeek              Enabled
--         ---------       ----                   ----------              -------
1          Daily           9/27/2011 11:00:00 PM                          True
2          Weekly          10/31/2011 12:00:00 AM {Monday}                True
```

In dit voor beeld ziet u hoe u het type taak trigger kunt wijzigen waarmee een taak wordt gestart.
Met de opdrachten in dit voor beeld wordt een trigger voor een AtStartup-taak vervangen door een wekelijkse trigger.

De eerste opdracht maakt gebruik van de cmdlet Get-JobTrigger om de taak trigger van de geplande voorraad taak op te halen.
In de uitvoer ziet u dat de taak twee keer een dagelijkse trigger en een *AtStartup* -trigger heeft geactiveerd.

Deze opdracht is niet vereist. het is alleen opgenomen om het effect van de wijziging van de trigger weer te geven.

### Voor beeld 3: de gebruiker wijzigen op een externe taak trigger

```
PS C:\> Invoke-Command -ComputerName "Server01" -ScriptBlock {Get-ScheduledJob | Get-JobTrigger | Where-Object {$_.User} | Set-JobTrigger -User "Domain01/Admin02"}
```

Met deze opdracht wordt de gebruiker gewijzigd in alle *AtLogon* -taak triggers van geplande taken op de Server01-computer.

De opdracht gebruikt de cmdlet Invoke-Command om een opdracht uit te voeren op de computer Server01.

De externe opdracht begint met een Get-ScheduledJob opdracht waarmee alle geplande taken op de computer worden opgehaald.
De geplande taken worden door gegeven aan de cmdlet Get-JobTrigger, waarmee de taak triggers van de geplande taken worden opgehaald.
Elke taak trigger bevat een taak definitie-eigenschap die de geplande taak bevat. de trigger blijft dus gekoppeld aan de geplande taak, zelfs wanneer deze wordt gewijzigd.

De taak triggers worden door gegeven aan de cmdlet Where-Object, waarmee taak triggers worden opgehaald die de eigenschap gebruiker hebben.
De geselecteerde taak triggers worden gepiped naar de cmdlet **set-JobTrigger** , waarmee de gebruiker wordt gewijzigd in Domain01\Admin02.

### Voor beeld 4: een van de vele taak triggers wijzigen

```
PS C:\> Get-JobTrigger -Name "SecurityCheck"
Id         Frequency       Time                   DaysOfWeek              Enabled
--         ---------       ----                   ----------              -------
1          Daily           4/24/2013 3:00:00 AM                           True
2          Weekly          4/24/2013 4:00:00 PM   {Sunday}                True
3          Once            4/24/2013 4:00:00 PM                           True

The second command uses the **TriggerID** parameter of the **Get-JobTrigger** cmdlet to get the *Once* trigger of the SecurityCheck scheduled job. The command pipes the trigger to the Format-List cmdlet, which displays all of the properties of the *Once* job trigger.The output shows that the trigger starts the job once every hour (RepetitionInterval = 1 hour) for one day (RepetitionDuration = 1 day).
PS C:\> Get-JobTrigger -Name "SecurityCheck" -TriggerID 3 | Format-List -Property *
At                 : 4/24/2012 4:00:00 PM
DaysOfWeek         :
Interval           : 1
Frequency          : Once
RandomDelay        : 00:00:00
RepetitionInterval : 01:00:00
RepetitionDuration : 1.00:00:00
User               :
Id                 : 3
Enabled            : True
JobDefinition      : Microsoft.PowerShell.ScheduledJob.ScheduledJobDefinition

The third command changes the repetition interval of the job trigger from one hour to 90 minutes. The command does not return any output.
PS C:\> Get-JobTrigger -Name "SecurityCheck" -TriggerId 3 | Set-JobTrigger -RepetitionInterval (New-TimeSpan -Minutes 90)

The fourth command displays the effect of the change.The output shows that the trigger starts the job once every 90 minutes (RepetitionInterval = 1 hour, 30 minutes) for one day (RepetitionDuration = 1 day).
PS C:\> Get-JobTrigger -Name "SecurityCheck" -TriggerID 3 | Format-List -Property *
At                 : 4/24/2012 4:00:00 PM
DaysOfWeek         :
Interval           : 1
Frequency          : Once
RandomDelay        : 00:00:00
RepetitionInterval : 01:30:00
RepetitionDuration : 1.00:00:00
User               :
Id                 : 3
Enabled            : True
JobDefinition      : Microsoft.PowerShell.ScheduledJob.ScheduledJobDefinition
```

Met de opdrachten in dit voor beeld wordt het herhalings interval van de taak trigger *Once* van de geplande taak SecurityCheck van elke 60 minuten tot elke 90 minuten gewijzigd.
De geplande SecurityCheck-taak heeft drie taak triggers, waardoor de opdrachten de para meter *TriggerId* van de cmdlet Get-JobTrigger gebruiken om de taak trigger te identificeren die wordt gewijzigd.

Met de eerste opdracht wordt de cmdlet **Get-JobTrigger** gebruikt om alle taak triggers van de geplande SecurityCheck-taak op te halen.
De uitvoer, waarin de Id's van de taak triggers worden weer gegeven, laat zien dat de trigger voor de taak *eenmaal* de id 3 heeft.

## PARAMETERS

### -At
De taak wordt gestart op de opgegeven datum en tijd.
Voer een **DateTime** -object in, zoals een teken reeks die wordt geretourneerd door de cmdlet Get-Date, of een String die kan worden geconverteerd naar een tijd, zoals ' 19 April 2012 15:00 ', ' 12/31/2013 9:00 pm ' of ' 3am '.

Als u geen element van het **DateTime** -object opgeeft, zoals seconden, wordt dat element van de taak trigger niet gewijzigd.
Als de oorspronkelijke taak trigger geen **DateTime** -object bevat en u een element weglaat, wordt de taak trigger gemaakt met het bijbehorende element van de huidige datum en tijd.

Wanneer u de para meter *Once* gebruikt, stelt u de waarde van de para meter *in* op een bepaalde datum en tijd.
Omdat de standaard datum in een **DateTime** -object de huidige datum is, is het instellen van een tijd vóór de huidige tijd zonder een expliciete datum resulteert in een taak trigger voor een tijd in het verleden.

**DateTime** -objecten en teken reeksen die worden geconverteerd naar **DateTime** -objecten, worden automatisch aangepast zodat ze compatibel zijn met de datum-en tijd notaties die zijn geselecteerd voor de lokale computer in de regio en taal in het configuratie scherm.

```yaml
Type: System.DateTime
Parameter Sets: (All)
Aliases:

Required: False
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
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -AtStartup
De geplande taak wordt gestart wanneer Windows wordt gestart.

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

### -Dagelijks
Geeft een terugkerende dagelijkse taak planning op.
Gebruik de andere para meters in de para meter *dagelijks* instellen om de details van de planning op te geven.

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

### -DaysInterval
Hiermee geeft u het aantal dagen op dat in een dagelijks schema voor komt.
Een waarde van 3 begint bijvoorbeeld met de geplande taak op dagen 1, 4, 7, enzovoort.
De standaardwaarde is 1.

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

### -DaysOfWeek
Hiermee geeft u de dagen van de week op waarop een wekelijkse geplande taak wordt uitgevoerd.
Voer de namen van dagen in, zoals maandag, donderdag, gehele getallen van 0-6, waarbij 0 staat voor zondag, of een asterisk ( \* ) die elke dag voor stelt.
Deze para meter is vereist in de set met wekelijkse para meters.

De namen van dagen worden geconverteerd naar hun gehele waarden in de taak trigger.
Wanneer u namen van dagen tussen aanhalings tekens in een opdracht plaatst, plaatst u de naam van elke dag in afzonderlijke aanhalings tekens, zoals "maandag", "dinsdag".
Als u meerdere namen van dagen in een enkel aanhalings teken plaatst, worden de bijbehorende waarden voor gehele getallen opgeteld.
Bijvoorbeeld: ' maandag, dinsdag ' (1, 2) resulteert in een waarde van ' woensdag ' (3).

```yaml
Type: System.DayOfWeek[]
Parameter Sets: (All)
Aliases:
Accepted values: Sunday, Monday, Tuesday, Wednesday, Thursday, Friday, Saturday

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Input object
Hiermee geeft u de taak triggers.
Voer een variabele in die **ScheduledJobTrigger** -objecten bevat of typ een opdracht of expressie waarmee **ScheduledJobTrigger** -objecten worden opgehaald, zoals een Get-JobTrigger opdracht.
U kunt ook een **ScheduledJobTrigger** -object pipeen naar **set-JobTrigger**.

Als u meerdere taak triggers opgeeft, worden met **set-JobTrigger** dezelfde wijzigingen aangebracht aan alle taak triggers.

```yaml
Type: Microsoft.PowerShell.ScheduledJob.ScheduledJobTrigger[]
Parameter Sets: (All)
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### -Eenmaal
Hiermee geeft u een schema voor niet-terugkerende (eenmalige).

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

### -PassThru
Retourneert de taak triggers die zijn gewijzigd.
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

### -RandomDelay
Hiermee schakelt u een wille keurige vertraging in die begint op de geplande begin tijd en stelt de maximale vertragings waarde in.
De lengte van de vertraging is ingesteld op wille keurige pseudo voor elk begin en varieert van geen vertraging tot de tijd die is opgegeven door de waarde van deze para meter.
De standaard waarde, nul (00:00:00), schakelt de wille keurige vertraging uit.

Voer een time span-object in, zoals het resultaat van de cmdlet New-TimeSpan, of voer een waarde in \<hours\> : \<minutes\> : \<seconds\> Format, die automatisch wordt geconverteerd naar een time span-object.

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
Parameter Sets: (All)
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
Als de waarde van **RepetitionInterval** bijvoorbeeld 5 minuten is en de waarde van *RepetitionDuration* 2 uur is, wordt de taak gedurende twee uur elke vijf minuten geactiveerd.

Voer een time span-object in, zoals een voor het retour neren van de cmdlet New-TimeSpan, of een teken reeks die kan worden geconverteerd naar een time span-object, zoals ' 1:05:30 '.

Als u een taak voor onbepaalde tijd wilt uitvoeren, voegt u in plaats daarvan de para meter *RepeatIndefinitely* toe.

Als u een taak wilt stoppen voordat de herhalings duur van de taak trigger verloopt, stelt u de waarde voor **RepetitionDuration** in op nul (0).

Als u de herhalings duur of het herhalings interval van een *eenmalige* taak trigger wilt wijzigen, moet de opdracht zowel de para meters **RepetitionInterval** als **RepetitionDuration** bevatten.
Als u de herhalings duur of herhalings intervallen van andere typen taak triggers wilt wijzigen, moet de opdracht de para meters *Once* , *at* , *RepetitionInterval* en *RepetitionDuration* bevatten.

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

### -RepetitionInterval
Hiermee wordt de taak herhaald op het opgegeven tijds interval.
Als de waarde van deze para meter bijvoorbeeld 2 uur is, wordt de taak elke twee uur geactiveerd.
De standaard waarde, 0, herhaalt de taak niet.

Voer een time span-object in, zoals een voor het retour neren van de cmdlet New-TimeSpan, of een teken reeks die kan worden geconverteerd naar een time span-object, zoals ' 1:05:30 '.

Als u de herhalings duur of het herhalings interval van een **eenmalige** taak trigger wilt wijzigen, moet de opdracht zowel de para meters **RepetitionInterval** als **RepetitionDuration** bevatten.
Als u de herhalings duur of herhalings intervallen van andere typen taak triggers wilt wijzigen, moet de opdracht de para meters **Once** , **at** , **RepetitionInterval** en **RepetitionDuration** bevatten.

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

### -User
Hiermee geeft u de gebruikers die een geplande taak *AtLogon* starten.
Voer de naam van een gebruiker in \<UserName\> of in of \<Domain\Username\> Voer een asterisk ( \* ) in om alle gebruikers weer te geven.
De standaard waarde is alle gebruikers.

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

### -Wekelijks
Hiermee geeft u een terugkerende wekelijkse taak planning op.
Gebruik de andere para meters in de set met *wekelijkse* para meters om de details van de planning op te geven.

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

### -WeeksInterval
Hiermee geeft u het aantal weken tussen exemplaren op voor een wekelijks taak schema.
Een waarde van 3 begint bijvoorbeeld met de geplande taak op weken 1, 4, 7 enzovoort.
De standaardwaarde is 1.

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

### CommonParameters
Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable. Zie [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)voor meer informatie.

## INVOER

### Micro soft. Power shell. ScheduledJob. ScheduledJobTrigger
U kunt meerdere taak triggers door sluizen naar **set-JobTrigger**.

## UITVOER

### Geen of Microsoft. Power shell. ScheduledJob. ScheduledJobTrigger
Wanneer u de para meter *PassThru* gebruikt, retourneert **set-JobTrigger** de taak triggers die zijn gewijzigd.
Anders wordt met deze cmdlet geen uitvoer gegenereerd.

## OPMERKINGEN

* Taak triggers hebben een JobDefintion-eigenschap die deze koppelt aan de geplande taak. Wanneer u de taak trigger van een geplande taak wijzigt, wordt de taak gewijzigd. U hoeft geen Set-ScheduledJob opdracht te gebruiken om de gewijzigde trigger toe te passen op de geplande taak.

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
