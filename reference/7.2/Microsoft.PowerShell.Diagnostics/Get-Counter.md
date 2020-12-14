---
external help file: Microsoft.PowerShell.Commands.Diagnostics.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Diagnostics
ms.date: 11/06/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.diagnostics/get-counter?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-Counter
ms.openlocfilehash: 4aed8db557b2d623aba4cd7218524af9957674c9
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 11/17/2020
ms.locfileid: "94705488"
---
# Get-Counter

## SAMENVATTING
Hiermee worden gegevens van het prestatie meter item opgehaald van lokale en externe computers.

## SYNTAXIS

### GetCounterSet (standaard)

```
Get-Counter [[-Counter] <String[]>] [-SampleInterval <Int32>] [-MaxSamples <Int64>] [-Continuous]
 [-ComputerName <String[]>] [<CommonParameters>]
```

### ListSetSet

```
Get-Counter [-ListSet] <String[]> [-ComputerName <String[]>] [<CommonParameters>]
```

## BESCHRIJVING

Met de `Get-Counter` cmdlet worden gegevens van prestatie meter items rechtstreeks opgehaald uit de instrumentatie voor prestatie bewaking in de Windows-besturings systemen. `Get-Counter` Hiermee worden prestatie gegevens opgehaald van een lokale computer of externe computers.

U kunt de `Get-Counter` para meters gebruiken voor het opgeven van een of meer computers, het weer geven van de prestatie meter sets en de instanties die ze bevatten, de controle-intervallen instellen en het maximum aantal steek proeven opgeven. Zonder para meters worden `Get-Counter` prestatie meter gegevens voor een set systeem tellers opgehaald.

Veel item sets worden beveiligd door Access Control Lists (ACL). Als u alle item sets wilt zien, opent u Power shell met de optie **als administrator uitvoeren** .

Deze cmdlet is opnieuw geïntroduceerd in Power shell 7.

## VOORBEELDEN

### Voor beeld 1: de lijst met item sets ophalen

In dit voor beeld wordt de lijst met item sets van de lokale computer opgehaald.

```powershell
Get-Counter -ListSet *
```

```Output
CounterSetName     : Processor
MachineName        : .
CounterSetType     : MultiInstance
Description        : The Processor performance object consists of counters that measure aspects ...
                     computer that performs arithmetic and logical computations, initiates ...
                     computer can have multiple processors.  The processor object represents ...
Paths              : {\Processor(*)\% Processor Time, \Processor(*)\% User Time, ...
PathsWithInstances : {\Processor(0)\% Processor Time, \Processor(1)\% Processor Time, ...
Counter            : {\Processor(*)\% Processor Time, \Processor(*)\% User Time, ...
```

`Get-Counter` maakt gebruik van de **listset** -para meter met een asterisk ( `*` ) om de lijst met item sets op te halen.
De punt ( `.` ) in de kolom **MachineName** vertegenwoordigt de lokale computer.

### Voor beeld 2: Geef de SampleInterval en MaxSamples op

In deze voor beelden worden de item gegevens voor alle processors op de lokale computer opgehaald. Gegevens worden op twee seconden verzameld, totdat er drie voor beelden zijn.

```powershell
Get-Counter -Counter "\Processor(_Total)\% Processor Time" -SampleInterval 2 -MaxSamples 3
```

```Output
Timestamp                 CounterSamples
---------                 --------------
6/18/2019 14:39:56        \\Computer01\processor(_total)\% processor time :
                          20.7144271584086

6/18/2019 14:39:58        \\Computer01\processor(_total)\% processor time :
                          10.4391790575511

6/18/2019 14:40:01        \\Computer01\processor(_total)\% processor time :
                          37.5968799396998
```

`Get-Counter` maakt gebruik van de para meter **Counter** om het itempad op te geven `\Processor(_Total)\% Processor Time` . De para meter **SampleInterval** stelt een interval van twee seconden in om de teller te controleren. **MaxSamples** bepaalt dat drie het maximum aantal keer dat de teller moet worden gecontroleerd.

### Voor beeld 3: doorlopende voor beelden van een item ophalen

In deze voor beelden worden voor elke seconde doorlopende voor beelden voor een item opgehaald. Als u de opdracht wilt stoppen, drukt u op <kbd>CTRL</kbd> + <kbd>C</kbd>. Als u een langere interval tussen steek proeven wilt opgeven, gebruikt u de para meter **SampleInterval** .

```powershell
Get-Counter -Counter "\Processor(_Total)\% Processor Time" -Continuous
```

```Output
Timestamp                 CounterSamples
---------                 --------------
6/19/2019 15:35:03        \\Computer01\processor(_total)\% processor time :
                          43.8522842937022

6/19/2019 15:35:04        \\Computer01\processor(_total)\% processor time :
                          29.7896844697383

6/19/2019 15:35:05        \\Computer01\processor(_total)\% processor time :
                          29.4962645638135

6/19/2019 15:35:06        \\Computer01\processor(_total)\% processor time :
                          25.5901500127408
```

`Get-Counter` Hiermee wordt **de teller-para meter** gebruikt om de teller op te geven `\Processor\% Processor Time` .
De **doorlopende** para meter geeft aan dat voor beelden elke seconde worden ontvangen totdat de opdracht wordt gestopt met <kbd>CTRL</kbd> + <kbd>C</kbd>.

### Voor beeld 4: alfabetische lijst met item sets

In dit voor beeld wordt de pijp lijn gebruikt om de lijst met tellers in te stellen en de lijst vervolgens in alfabetische volg orde te sorteren.

```powershell
Get-Counter -ListSet * |
  Sort-Object -Property CounterSetName |
    Format-Table CounterSetName, CounterSetType -AutoSize
```

```Output
CounterSetName                        CounterSetType
--------------                        --------------
.NET CLR Data                         SingleInstance
.NET Data Provider for SqlServer      SingleInstance
AppV Client Streamed Data Percentage  SingleInstance
Authorization Manager Applications    SingleInstance
BitLocker                             MultiInstance
Bluetooth Device                      SingleInstance
Cache                                 SingleInstance
Client Side Caching                   SingleInstance
```

`Get-Counter` maakt gebruik van de **listset** -para meter met een asterisk ( `*` ) om een volledige lijst met item sets op te halen. De **counterset** -objecten worden omlaag verzonden via de pijp lijn. `Sort-Object` Hiermee wordt de para meter **Property** gebruikt om op te geven dat de objecten zijn gesorteerd op **CounterSetName**. De objecten worden naar beneden verzonden in de pijp lijn `Format-Table` . Met de para meter **AutoSize** worden de kolom breedten aangepast om de afkap ping te minimaliseren.

De punt ( `.` ) in de kolom **MachineName** vertegenwoordigt de lokale computer.

### Voor beeld 5: een achtergrond taak uitvoeren om item gegevens op te halen

In dit voor beeld `Start-Job` wordt een `Get-Counter` opdracht uitgevoerd als achtergrond taak op de lokale computer.
Als u de uitvoer van het prestatie meter item van de taak wilt weer geven, gebruikt u de `Receive-Job` cmdlet.

```powershell
Start-Job -ScriptBlock {Get-Counter -Counter "\LogicalDisk(_Total)\% Free Space" -MaxSamples 1000}
```

```Output
Id     Name  PSJobTypeName   State    HasMoreData  Location   Command
--     ----  -------------   -----    -----------  --------   -------
1      Job1  BackgroundJob   Running  True         localhost  Get-Counter -Counter
```

`Start-Job` maakt gebruik van de para meter **script Block** om een opdracht uit te voeren `Get-Counter` . `Get-Counter` maakt gebruik van de para meter **Counter** om het itempad op te geven `\LogicalDisk(_Total)\% Free Space` . De para meter **MaxSamples** geeft aan dat er 1000 voor beelden van de teller worden ontvangen.

### Voor beeld 6: item gegevens van meerdere computers ophalen

In dit voor beeld wordt een variabele gebruikt om prestatie meter items van twee computers op te halen.

```powershell
$DiskReads = "\LogicalDisk(C:)\Disk Reads/sec"
$DiskReads | Get-Counter -ComputerName Server01, Server02 -MaxSamples 10
```

```Output
Timestamp                 CounterSamples
---------                 --------------
6/21/2019 10:51:04        \\Server01\logicaldisk(c:)\disk reads/sec :
                          0

                          \\Server02\logicaldisk(c:)\disk reads/sec :
                          0.983050344269146
```

De `$DiskReads` variabele slaat het `\LogicalDisk(C:)\Disk Reads/sec` itempad op. De `$DiskReads` variabele wordt naar beneden verzonden in de pijp lijn `Get-Counter` . **Teller** is de eerste positie parameter en accepteert het pad dat is opgeslagen in `$DiskReads` . **ComputerName** specificeert de twee computers en **MaxSamples** geeft aan dat er tien steek proeven van elke computer worden opgehaald.

### Voor beeld 7: de exemplaar waarden van een teller ophalen van meerdere wille keurige computers

In dit voor beeld wordt de waarde van een prestatie meter item op 50 wille keurige externe computers in de onderneming opgehaald. De para meter **ComputerName** gebruikt wille keurige computer namen die zijn opgeslagen in een variabele. Als u de computer namen in de variabele wilt bijwerken, maakt u de variabele opnieuw.

Een alternatief voor de server namen in de para meter **ComputerName** is het gebruik van een tekst bestand. Bijvoorbeeld:

`-ComputerName (Get-Random (Get-Content -Path C:\Servers.txt) -Count 50)`

Het itempad bevat een asterisk ( `*` ) in de naam van het exemplaar om de gegevens op te halen voor elk van de processors van de externe computer.

```powershell
$Servers = Get-Random (Get-Content -Path C:\Servers.txt) -Count 50
$Counter = "\Processor(*)\% Processor Time"
Get-Counter -Counter $Counter -ComputerName $Servers
```

```Output
Timestamp                 CounterSamples
---------                 --------------
6/20/2019 12:20:35        \\Server01\processor(0)\% processor time :
                          6.52610319637854

                          \\Server01\processor(1)\% processor time :
                          3.41030663625782

                          \\Server01\processor(2)\% processor time :
                          9.64189975649925

                          \\Server01\processor(3)\% processor time :
                          1.85240835619747

                          \\Server01\processor(_total)\% processor time :
                          5.35768447160776
```

De `Get-Random` cmdlet gebruikt `Get-Content` om 50 wille keurige computer namen uit het bestand te selecteren `Servers.txt` . De namen van de externe computers worden opgeslagen in de `$Servers` variabele. Het `\Processor(*)\% Processor Time` pad van het item wordt opgeslagen in de `$Counter` variabele. `Get-Counter` gebruikt de **teller** -para meter om de items in de variabele op te geven `$Counter` . Met de para meter **ComputerName** worden de computer namen in de `$Servers` variabele opgegeven.

### Voor beeld 8: gebruik de eigenschap Path om opgemaakte padnamen op te halen

In dit voor beeld wordt de eigenschap **Path** van een counterset gebruikt om de opgemaakte padnamen voor de prestatie meter items te vinden.

De pijp lijn wordt met de `Where-Object` cmdlet gebruikt om een subset van de namen van de paden te vinden. Als u wilt zoeken naar een item sets met een volledige lijst met item paden, verwijdert u de pijp lijn ( `|` ) en de `Where-Object` opdracht.

De `$_` is een automatische variabele voor het huidige object in de pijp lijn.
Zie [about_Automatic_Variables](../Microsoft.PowerShell.Core/About/about_Automatic_Variables.md)voor meer informatie.

```powershell
(Get-Counter -ListSet Memory).Paths | Where-Object { $_ -like "*Cache*" }
```

```Output
\Memory\Cache Faults/sec
\Memory\Cache Bytes
\Memory\Cache Bytes Peak
\Memory\System Cache Resident Bytes
\Memory\Standby Cache Reserve Bytes
\Memory\Standby Cache Normal Priority Bytes
\Memory\Standby Cache Core Bytes
\Memory\Long-Term Average Standby Cache Lifetime (s)
```

`Get-Counter` maakt gebruik van de **listset** -para meter om de set **geheugen** teller op te geven. De opdracht bevindt zich tussen haakjes zodat de eigenschap **paden** elk pad retourneert als een teken reeks. De objecten worden naar beneden verzonden in de pijp lijn `Where-Object` . `Where-Object` gebruikt de variabele `$_` voor het verwerken van elk object en gebruikt de `-like` operator om overeenkomsten te vinden voor de teken reeks `*Cache*` . De sterretjes ( `*` ) zijn joker tekens voor wille keurige tekens.

### Voor beeld 9: gebruik de eigenschap PathsWithInstances om opgemaakte padnamen op te halen

In dit voor beeld worden de opgemaakte padnamen opgehaald die de instanties voor de **fysieke schijf** prestatie meter items bevatten.

```powershell
(Get-Counter -ListSet PhysicalDisk).PathsWithInstances
```

```Output
\PhysicalDisk(0 C:)\Current Disk Queue Length
\PhysicalDisk(_Total)\Current Disk Queue Length
\PhysicalDisk(0 C:)\% Disk Time
\PhysicalDisk(_Total)\% Disk Time
\PhysicalDisk(0 C:)\Avg. Disk Queue Length
\PhysicalDisk(_Total)\Avg. Disk Queue Length
\PhysicalDisk(0 C:)\% Disk Read Time
\PhysicalDisk(_Total)\% Disk Read Time
```

`Get-Counter` maakt gebruik van de **listset** -para meter om de tellerset van het **fysieke** volume op te geven. De opdracht bevindt zich tussen haakjes zodat de eigenschap **PathsWithInstances** elke apparaatinstantie als een teken reeks retourneert.

### Voor beeld 10: een enkele waarde ophalen voor elk item in een tellerset

In dit voor beeld wordt één waarde geretourneerd voor elk prestatie meter item in de set **geheugen** tellers van de lokale computer.

```powershell
$MemCounters = (Get-Counter -ListSet Memory).Paths
Get-Counter -Counter $MemCounters
```

```Output
Timestamp                 CounterSamples
---------                 --------------
6/19/2019 12:05:00        \\Computer01\memory\page faults/sec :
                          868.772077545597

                          \\Computer01\memory\available bytes :
                          9031176192

                          \\Computer01\memory\committed bytes :
                          8242982912

                          \\Computer01\memory\commit limit :
                          19603333120
```

`Get-Counter` maakt gebruik van de **listset** -para meter om de set **geheugen** teller op te geven. De opdracht bevindt zich tussen haakjes zodat de eigenschap **paden** elk pad retourneert als een teken reeks. De paden worden opgeslagen in de `$MemCounters` variabele. `Get-Counter` gebruikt de **teller** -para meter om de item paden in de variabele op te geven `$MemCounters` .

### Voor beeld 11: de eigenschaps waarden van een object weer geven

De eigenschaps waarden in het object **PerformanceCounterSample** vertegenwoordigen elk gegevens voorbeeld. In dit voor beeld gebruiken we de eigenschappen van het object **CounterSamples** om de gegevens te bekijken, te selecteren, te sorteren en te groeperen.

```powershell
$Counter = "\\Server01\Process(Idle)\% Processor Time"
$Data = Get-Counter $Counter
$Data.CounterSamples | Format-List -Property *
```

```Output
Path             : \\Server01\process(idle)\% processor time
InstanceName     : idle
CookedValue      : 198.467899571389
RawValue         : 14329160321003
SecondValue      : 128606459528326201
MultipleCount    : 1
CounterType      : Timer100Ns
Timestamp        : 6/19/2019 12:20:49
Timestamp100NSec : 128606207528320000
Status           : 0
DefaultScale     : 0
TimeBase         : 10000000
```

Het itempad wordt opgeslagen in de `$Counter` variabele. `Get-Counter` Hiermee wordt een voor beeld van de item waarden opgehaald en worden de resultaten opgeslagen in de `$Data` variabele. De `$Data` variabele gebruikt de eigenschap **CounterSamples** om de eigenschappen van het object op te halen. Het object wordt naar de pijp lijn verzonden `Format-List` . De **eigenschaps** parameter maakt gebruik van een asterisk ( `*` ) als Joker teken om alle eigenschappen te selecteren.

### Voor beeld 12: matrix waarden voor prestatie meter items

In dit voor beeld wordt elk prestatie meter item opgeslagen in een variabele. De eigenschap **CounterSamples** is een matrix waarin specifieke item waarden kunnen worden weer gegeven.

Als u elk item voorbeeld wilt weer geven, gebruikt u `$Counter.CounterSamples` .

```powershell
$Counter = Get-Counter -Counter "\Processor(*)\% Processor Time"
$Counter.CounterSamples[0]
```

```Output
Path                                         InstanceName        CookedValue
----                                         ------------        -----------
\\Computer01\processor(0)\% processor time   0              1.33997091699662
```

`Get-Counter` Hiermee wordt **de teller-para meter** gebruikt om de teller op te geven `\Processor(*)\% Processor Time` . De waarden worden opgeslagen in de `$Counter` variabele.
`$Counter.CounterSamples[0]` Hiermee wordt de matrix waarde voor de waarde van het eerste item weer gegeven.

### Voor beeld 13: waarden van prestatie meter items vergelijken

In dit voor beeld wordt gezocht naar de hoeveelheid processor tijd die door elke processor op de lokale computer wordt gebruikt. De eigenschap **CounterSamples** wordt gebruikt om de item gegevens te vergelijken met een opgegeven waarde.

Als u elk item voorbeeld wilt weer geven, gebruikt u `$Counter.CounterSamples` .

```powershell
$Counter = Get-Counter -Counter "\Processor(*)\% Processor Time"
$Counter.CounterSamples | Where-Object { $_.CookedValue -lt "20" }
```

```Output
Path                                         InstanceName        CookedValue
----                                         ------------        -----------
\\Computer01\processor(0)\% processor time   0              12.6398025240208
\\Computer01\processor(1)\% processor time   1              15.7598095767344
```

`Get-Counter` Hiermee wordt **de teller-para meter** gebruikt om de teller op te geven `\Processor(*)\% Processor Time` . De waarden worden opgeslagen in de `$Counter` variabele. De objecten `$Counter.CounterSamples` die zijn opgeslagen in, worden naar de pijp lijn verzonden. `Where-Object` maakt gebruik van een script blok om de waarde van elk object te vergelijken met een opgegeven waarde van 20. De `$_.CookedValue` is een variabele voor het huidige object in de pijp lijn. Tellers met een **CookedValue** die kleiner is dan 20 worden weer gegeven.

### Voor beeld 14: gegevens van prestatie meter items sorteren

In dit voor beeld ziet u hoe gegevens van prestatie meter items worden gesorteerd. In het voor beeld worden de processen gevonden op de computer die de meeste processor tijd gebruiken tijdens het voor beeld.

```powershell
$Procs = Get-Counter -Counter "\Process(*)\% Processor Time"
$Procs.CounterSamples | Sort-Object -Property CookedValue -Descending |
   Format-Table -Property Path, InstanceName, CookedValue -AutoSize
```

```Output
Path                                                         InstanceName             CookedValue
----                                                         ------------             -----------
\\Computer01\process(_total)\% processor time                _total              395.464129650573
\\Computer01\process(idle)\% processor time                  idle                389.356575524695
\\Computer01\process(mssense)\% processor time               mssense             3.05377706293879
\\Computer01\process(csrss#1)\% processor time               csrss               1.52688853146939
\\Computer01\process(microsoftedgecp#10)\% processor time    microsoftedgecp     1.52688853146939
\\Computer01\process(runtimebroker#5)\% processor time       runtimebroker                      0
\\Computer01\process(settingsynchost)\% processor time       settingsynchost                    0
\\Computer01\process(microsoftedgecp#16)\% processor time    microsoftedgecp                    0
```

`Get-Counter` gebruikt de **teller** -para meter om de `\Process(*)\% Processor Time` teller op te geven voor alle processen op de lokale computer. Het resultaat wordt opgeslagen in de `$Procs` variabele. De `$Procs` variabele met de eigenschap **CounterSamples** verzendt de **PerformanceCounterSample** -objecten omlaag in de pijp lijn. `Sort-Object` gebruikt de para meter **Property** om de objecten te sorteren op **CookedValue** in **aflopende** volg orde. `Format-Table` gebruikt de para meter **Property** om de kolommen voor de uitvoer te selecteren. Met de para meter **AutoSize** worden de kolom breedten aangepast om de afkap ping te minimaliseren.

## PARAMETERS

### -ComputerName

Hiermee geeft u een computer naam of een door komma's gescheiden matrix met **externe** computer namen op. Gebruik de NetBIOS-naam, een IP-adres of de Fully Qualified Domain Name van de computer.

Als u prestatie meter gegevens wilt ophalen van de **lokale** computer, sluit u de para meter **ComputerName** .
Voor uitvoer, zoals een **lijstset** die de kolom **MachineName** bevat, geeft een punt ( `.` ) de lokale computer aan.

`Get-Counter` vertrouwt niet op externe communicatie met Power shell. U kunt de para meter **ComputerName** ook gebruiken als uw computer niet is geconfigureerd om externe opdrachten uit te voeren.

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases: Cn

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Doorlopend

Wanneer de **doorlopende** is opgegeven, worden `Get-Counter` er voor beelden opgehaald totdat u op <kbd>CTRL</kbd> + <kbd>C</kbd>drukt. Voor elk opgegeven prestatie meter item worden voor beelden elke seconde opgehaald. Gebruik de para meter **SampleInterval** om het interval tussen opeenvolgende steek proeven te verhogen.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: GetCounterSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Teller

Hiermee geeft u het pad naar een of meer teller paden. Paden worden ingevoerd als een door komma's gescheiden matrix, een variabele of waarden uit een tekst bestand. U kunt tellers voor itempad naar beneden verplaatsen in de pijp lijn `Get-Counter` .

Teller paden gebruiken de volgende syntaxis:

`\\ComputerName\CounterSet(Instance)\CounterName`

`\CounterSet(Instance)\CounterName`

Bijvoorbeeld:

`\\Server01\Processor(*)\% User Time`

`\Processor(*)\% User Time`

De `\\ComputerName` is optioneel in een pad voor prestatie meter items. Als het itempad geen computer naam bevat, `Get-Counter` wordt de lokale computer gebruikt.

Een asterisk ( `*` ) in het exemplaar is een Joker teken om alle exemplaren van de teller op te halen.

```yaml
Type: System.String[]
Parameter Sets: GetCounterSet
Aliases:

Required: False
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: True
```

### -Lijstset

Geeft een lijst van de prestatie meter sets op de computers. Gebruik een asterisk ( `*` ) om alle item sets op te geven. Voer één naam of een door komma's gescheiden teken reeks in voor de namen van de Counter sets. U kunt namen van tellers sets omlaag verzenden via de pijp lijn.

Voor het ophalen van teller-paden die zijn opgemaakt met Counter sets, gebruikt u de **listset** -para meter. De **paden** en **PathsWithInstances** -eigenschappen van elke verzameling tellers bevatten de afzonderlijke item paden die zijn opgemaakt als een teken reeks.

U kunt de itempad teken reeksen in een variabele opslaan of de pijp lijn gebruiken om de teken reeks naar een andere opdracht te verzenden `Get-Counter` .

U kunt bijvoorbeeld elk pad naar de **processor** teller verzenden naar `Get-Counter` :

`Get-Counter -ListSet Processor | Get-Counter`

> [!NOTE]
> In Power shell 7 `Get-Counter` kan de eigenschap **Description** van de verzameling tellers niet worden opgehaald. De **Beschrijving** is ingesteld op `$null` .

```yaml
Type: System.String[]
Parameter Sets: ListSetSet
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: True
```

### -MaxSamples

Hiermee geeft u het aantal steek proeven op dat moet worden opgehaald van elk opgegeven prestatie meter item. Gebruik de **doorlopende** para meter om een constante stroom van voor beelden te verkrijgen.

Als de para meter **MaxSamples** niet is opgegeven, `Get-Counter` wordt er slechts één voor beeld voor elke opgegeven teller opgehaald.

Als u een grote gegevensset wilt verzamelen, voert u uit `Get-Counter` als een Power shell-achtergrond taak. Zie [About Jobs](../Microsoft.PowerShell.Core/About/about_Jobs.md) (Taken) voor meer informatie.

```yaml
Type: System.Int64
Parameter Sets: GetCounterSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -SampleInterval

Hiermee geeft u het aantal seconden tussen steek proeven op voor elk opgegeven prestatie meter item. Als de para meter **SampleInterval** niet wordt opgegeven, `Get-Counter` gebruikt een interval van één seconde.

```yaml
Type: System.Int32
Parameter Sets: GetCounterSet
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

### System.String[]

`Get-Counter` accepteert invoer van de pijp lijn voor item paden en namen van tellers.

## UITVOER

### Micro soft. Power shell. commands. GetCounter. Counterset, micro soft. Power shell. commands. GetCounter. PerformanceCounterSampleSet, micro soft. Power shell. commands. GetCounter. PerformanceCounterSample

Als u de eigenschappen van een object wilt weer geven, verzendt u de uitvoer naar de pijp lijn naar `Get-Member` . De object typen die worden uitgevoerd, zijn als volgt:

**Listset** -para meter: **micro soft. Power shell. commands. GetCounter. counterset**

**Teller** -para meter: **micro soft. Power shell. commands. GetCounter. PerformanceCounterSampleSet**

Eigenschap **CounterSamples** : **micro soft. Power shell. commands. GetCounter. PerformanceCounterSample**

## OPMERKINGEN

Als er geen para meters zijn opgegeven, `Get-Counter` wordt een voor beeld opgehaald voor elk opgegeven prestatie meter item. Gebruik de **MaxSamples** -en **doorlopende** para meters om meer voor beelden te verkrijgen.

`Get-Counter` maakt gebruik van een interval van één seconde tussen steek proeven. Gebruik de para meter **SampleInterval** om het interval te verhogen.

De waarden **MaxSamples** en **SampleInterval** zijn van toepassing op alle items op elke computer in de opdracht. Als u verschillende waarden voor verschillende items wilt instellen, voert u afzonderlijke `Get-Counter` opdrachten in.

Bij gebruik van de **listset** para meter kan in Power shell 7 `Get-Counter` de eigenschap **Description** van de verzameling tellers niet ophalen. De **Beschrijving** is ingesteld op `$null` .

## GERELATEERDE KOPPELINGEN

[about_Automatic_Variables](../Microsoft.PowerShell.Core/About/about_Automatic_Variables.md)

[about_Jobs](../Microsoft.PowerShell.Core/About/about_Jobs.md)

[Format-List](../Microsoft.PowerShell.Utility/Format-List.md)

[Format-Table](../Microsoft.PowerShell.Utility/Format-Table.md)

[Get-member](../Microsoft.PowerShell.Utility/Get-Member.md)

[Receive-job](../Microsoft.PowerShell.Core/Receive-Job.md)

[Begin taak](../Microsoft.PowerShell.Core/Start-Job.md)

[Where-object](..//Microsoft.PowerShell.Core/Where-Object.md)

