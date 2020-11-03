---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 03/20/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/sort-object?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Sort-Object
ms.openlocfilehash: 3eef18677c8f81b560354303c2d685abfc44601c
ms.sourcegitcommit: 9a6b6714ded4edb5119f1b82a253608018ea6b98
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 08/10/2020
ms.locfileid: "93251779"
---
# Sort-Object

## SAMENVATTING
Objecten sorteren op eigenschaps waarden.

## SYNTAXIS

### Standaard (standaard instelling)

```
Sort-Object [-Stable] [-Descending] [-Unique] [-InputObject <PSObject>] [[-Property] <Object[]>]
 [-Culture <String>] [-CaseSensitive] [<CommonParameters>]
```

### Boven

```
Sort-Object [-Descending] [-Unique] -Top <Int32> [-InputObject <PSObject>] [[-Property] <Object[]>]
 [-Culture <String>] [-CaseSensitive] [<CommonParameters>]
```

### Onderste

```
Sort-Object [-Descending] [-Unique] -Bottom <Int32> [-InputObject <PSObject>] [[-Property] <Object[]>]
 [-Culture <String>] [-CaseSensitive] [<CommonParameters>]
```

## BESCHRIJVING

`Sort-Object`Met de cmdlet worden objecten in oplopende of aflopende volg orde gesorteerd op basis van de object eigenschaps waarden. Als Sorteer eigenschappen niet zijn opgenomen in een opdracht, gebruikt Power Shell standaard sorteer eigenschappen van het eerste invoer object. Als het type van het invoer object geen standaard sorteer eigenschappen heeft, probeert Power shell de objecten zelf te vergelijken. Zie de sectie [opmerkingen](#notes) voor meer informatie.

U kunt objecten sorteren op één eigenschap of meerdere eigenschappen. Meerdere eigenschappen gebruiken hash-tabellen om in oplopende volg orde, aflopende volg orde of een combi natie van sorteer volgorden te sorteren. Eigenschappen worden gesorteerd als hoofdletter gevoelig of niet hoofdletter gevoelig. Gebruik de **unieke** para meter voor het verwijderen van dubbele waarden uit de uitvoer.

## VOORBEELDEN

### Voor beeld 1: de huidige map sorteren op naam

In dit voor beeld worden de bestanden en submappen in een map gesorteerd.

```
PS> Get-ChildItem -Path C:\Test | Sort-Object

    Directory: C:\Test

Mode                LastWriteTime         Length Name
----                -------------         ------ ----
-a----        2/13/2019     08:55             26 anotherfile.txt
-a----        2/13/2019     13:26             20 Bfile.txt
-a----        2/12/2019     15:40         118014 Command.txt
-a----         2/1/2019     08:43            183 CreateTestFile.ps1
d-----        2/25/2019     18:25                Files
d-----        2/25/2019     18:24                Logs
-ar---        2/12/2019     14:31             27 ReadOnlyFile.txt
-a----        2/12/2019     16:24             23 Zsystemlog.log
```

`Get-ChildItem`Met de cmdlet worden de bestanden en submappen opgehaald uit de map die is opgegeven door de para meter **Path** , **C:\Test**. De objecten worden naar de-cmdlet verzonden via de pijp lijn `Sort-Object` .
`Sort-Object` geeft geen eigenschap op waardoor de uitvoer wordt gesorteerd op basis van de standaard sorteer eigenschap, **naam**.

### Voor beeld 2: de huidige map sorteren op bestands lengte

Met deze opdracht worden de bestanden in de huidige map op basis van de lengte in oplopende volg orde weer gegeven.

```
PS> Get-ChildItem -Path C:\Test -File | Sort-Object -Property Length

    Directory: C:\Test

Mode                LastWriteTime         Length Name
----                -------------         ------ ----
-a----        2/13/2019     13:26             20 Bfile.txt
-a----        2/12/2019     16:24             23 Zsystemlog.log
-a----        2/13/2019     08:55             26 anotherfile.txt
-ar---        2/12/2019     14:31             27 ReadOnlyFile.txt
-a----         2/1/2019     08:43            183 CreateTestFile.ps1
-a----        2/12/2019     15:40         118014 Command.txt
```

De `Get-ChildItem` cmdlet haalt de bestanden op uit de map die is opgegeven door de para meter **Path** .
De **File** -para meter geeft aan dat `Get-ChildItem` alleen bestands objecten worden opgehaald. De objecten worden naar de-cmdlet verzonden via de pijp lijn `Sort-Object` . `Sort-Object` gebruikt de **lengte** parameter om de bestanden te sorteren op lengte in oplopende volg orde.

### Voor beeld 3: processen sorteren op geheugen gebruik

In dit voor beeld worden processen met het hoogste geheugen gebruik weer gegeven op basis van de grootte van de werkset (WS).

```
PS> Get-Process | Sort-Object -Property WS | Select-Object -Last 5

 NPM(K)    PM(M)      WS(M)     CPU(s)      Id  SI ProcessName
 ------    -----      -----     ------      --  -- -----------
    136   193.92     217.11     889.16   87492   8 OUTLOOK
    112   347.73     297.02      95.19  106908   8 Teams
    206   266.54     323.71      37.17   60620   8 MicrosoftEdgeCP
     35   552.19     549.94     131.66    6552   8 Code
      0     1.43     595.12       0.00    2780   0 Memory Compression
```

De `Get-Process` cmdlet haalt de lijst op met processen die op de computer worden uitgevoerd. De proces objecten worden in de pijp lijn naar de `Sort-Object` cmdlet verzonden. `Sort-Object` gebruikt de para meter **Property** om de objecten te sorteren op **WS**. De objecten worden naar de-cmdlet verzonden via de pijp lijn `Select-Object` .
`Select-Object` gebruikt de **laatste** para meter om de laatste vijf objecten op te geven. Dit zijn de objecten met het hoogste **WS** -gebruik.

In Power shell 6 `Sort-Object` is de para meter **onder** een alternatief voor `Select-Object` . Bijvoorbeeld `Get-Process | Sort-Object -Property WS -Bottom 5`.

### Voor beeld 4: HistoryInfo-objecten sorteren op id

Met deze opdracht worden de **HistoryInfo** -objecten van de Power shell **-** sessie gesorteerd met de eigenschap ID. Elke Power shell-sessie heeft een eigen opdracht geschiedenis.

```
PS> Get-History | Sort-Object -Property Id -Descending

  Id CommandLine
  -- -----------
  10 Get-Command Sort-Object -Syntax
   9 $PSVersionTable
   8 Get-Command Sort-Object -Syntax
   7 Get-Command Sort-Object -ShowCommandInfo
   6 Get-ChildItem -Path C:\Test | Sort-Object -Property Length
   5 Get-Help Clear-History -online
   4 Get-Help Clear-History -full
   3 Get-ChildItem | Get-Member
   2 Get-Command Sort-Object -Syntax
   1 Set-Location C:\Test\
```

De `Get-History` cmdlet haalt de geschiedenis objecten op uit de huidige Power shell-sessie. De objecten worden naar de-cmdlet verzonden via de pijp lijn `Sort-Object` . `Sort-Object` gebruikt de para meter **Property** om de objecten op **id** te sorteren. De **aflopende** para meter sorteert de opdracht geschiedenis van nieuwste naar oudste.

### Voor beeld 5: een hash-tabel gebruiken om eigenschappen in oplopende en aflopende volg orde te sorteren

In dit voor beeld worden twee eigenschappen gebruikt om de objecten, **status** en **DisplayName** te sorteren. De **status** wordt gesorteerd in aflopende volg orde en **DisplayName** wordt in oplopende volg orde gesorteerd.

Een hash-tabel wordt gebruikt om de waarde van de **eigenschap** para meter op te geven. De hash-tabel gebruikt een expressie om de namen van eigenschappen en sorteer volgorden op te geven. Zie [about_Hash_Tables](../Microsoft.PowerShell.Core/About/about_Hash_Tables.md)voor meer informatie over hash-tabellen.

De eigenschap **status** die in de hash-tabel wordt gebruikt, is een opgesomde eigenschap.
Zie [ServiceControllerStatus](/dotnet/api/system.serviceprocess.servicecontrollerstatus)voor meer informatie.

```
PS C:\> Get-Service | Sort-Object -Property @{Expression = "Status"; Descending = $True}, @{Expression = "DisplayName"; Descending = $False}

Status   Name               DisplayName
------   ----               -----------
Running  Appinfo            Application Information
Running  BthAvctpSvc        AVCTP service
Running  BrokerInfrastru... Background Tasks Infrastructure Ser...
Running  BDESVC             BitLocker Drive Encryption Service
Running  CoreMessagingRe... CoreMessaging
Running  VaultSvc           Credential Manager
Running  DsSvc              Data Sharing Service
Running  Dhcp               DHCP Client
...
Stopped  ALG                Application Layer Gateway Service
Stopped  AppMgmt            Application Management
Stopped  BITS               Background Intelligent Transfer Ser...
Stopped  wbengine           Block Level Backup Engine Service
Stopped  BluetoothUserSe... Bluetooth User Support Service_14fb...
Stopped  COMSysApp          COM+ System Application
Stopped  smstsmgr           ConfigMgr Task Sequence Agent
Stopped  DeviceInstall      Device Install Service
Stopped  MSDTC              Distributed Transaction Coordinator
```

De `Get-Service` cmdlet haalt de lijst met Services op de computer op. De service objecten worden naar de-cmdlet verzonden via de pijp lijn `Sort-Object` . `Sort-Object` gebruikt de **eigenschaps** parameter met een hash-tabel om de namen van eigenschappen en sorteer volgorden op te geven. De **eigenschaps** parameter is gesorteerd op twee eigenschappen, **status** in aflopende volg orde en **DisplayName** in oplopende volg orde.

**Status** is een opgesomde eigenschap. **Gestopt** heeft de waarde **1** en **wordt uitgevoerd** met de waarde **4**. De **aflopende** para meter is ingesteld op `$True` zodat **actieve** processen worden weer gegeven voordat processen worden **gestopt** . **DisplayName** stelt de **aflopende** para meter in om `$False` de weergave namen in alfabetische volg orde te sorteren.

### Voor beeld 6: tekst bestanden sorteren op tijds Panne

Met deze opdracht worden tekst bestanden in aflopende volg orde gesorteerd op basis van de tijds duur tussen **CreationTime** en **LastWriteTime**.

```
PS> Get-ChildItem -Path C:\Test\*.txt | Sort-Object -Property @{Expression = {$_.CreationTime - $_.LastWriteTime}; Descending = $False} | Format-Table CreationTime, LastWriteTime, FullName

CreationTime          LastWriteTime        FullName
------------          -------------        --------
11/21/2018 12:39:01   2/26/2019 08:59:36   C:\Test\test2.txt
12/4/2018 08:29:41    2/26/2019 08:57:05   C:\Test\powershell_list.txt
2/20/2019 08:15:59    2/26/2019 12:09:43   C:\Test\CreateTestFile.txt
2/20/2019 08:15:59    2/26/2019 12:07:41   C:\Test\Command.txt
2/20/2019 08:15:59    2/26/2019 08:57:52   C:\Test\ReadOnlyFile.txt
11/29/2018 15:16:50   12/4/2018 16:16:24   C:\Test\LogData.txt
2/25/2019 18:25:11    2/26/2019 12:08:47   C:\Test\Zsystemlog.txt
2/25/2019 18:25:11    2/26/2019 08:55:33   C:\Test\Bfile.txt
2/26/2019 08:46:59    2/26/2019 12:12:19   C:\Test\LogFile3.txt
```

De `Get-ChildItem` cmdlet gebruikt de para meter **Path** om de map **C:\Test** en alle bestanden op te geven `*.txt` . De objecten worden naar de-cmdlet verzonden via de pijp lijn `Sort-Object` .
`Sort-Object` gebruikt de **eigenschaps** parameter met een hash-tabel om te bepalen hoeveel bestanden de tijd tussen **CreationTime** en **LastWriteTime**. De **aflopende** para meter is ingesteld op `$False` om te sorteren in de volg orde van voor de kortste periode.

### Voor beeld 7: namen in een tekst bestand sorteren

In dit voor beeld ziet u hoe u een lijst kunt sorteren op basis van een tekst bestand. Het oorspronkelijke bestand wordt weer gegeven als een niet-gesorteerde lijst. `Sort-Object` Hiermee wordt de inhoud gesorteerd en wordt de inhoud gesorteerd met de **unieke** para meter waarmee dubbele waarden worden verwijderd.

```
PS> Get-Content -Path C:\Test\ServerNames.txt
localhost
server01
server25
LOCALHOST
Server19
server3
localhost

PS> Get-Content -Path C:\Test\ServerNames.txt | Sort-Object
localhost
LOCALHOST
localhost
server01
Server19
server25
server3

PS> Get-Content -Path C:\Test\ServerNames.txt | Sort-Object -Unique
localhost
server01
Server19
server25
server3
```

De `Get-Content` cmdlet gebruikt de para meter **Path** om de map en de bestands naam op te geven. Het bestand **ServerNames.txt** bevat een niet-gesorteerde lijst met computer namen.

De `Get-Content` cmdlet gebruikt de para meter **Path** om de map en de bestands naam op te geven. Het bestand **ServerNames.txt** bevat een niet-gesorteerde lijst met computer namen. De objecten worden naar de-cmdlet verzonden via de pijp lijn `Sort-Object` . `Sort-Object` sorteert de lijst in de standaard volgorde, oplopend.

De `Get-Content` cmdlet gebruikt de para meter **Path** om de map en de bestands naam op te geven. Het bestand **ServerNames.txt** bevat een niet-gesorteerde lijst met computer namen. De objecten worden naar de-cmdlet verzonden via de pijp lijn `Sort-Object` . `Sort-Object` gebruikt de **unieke** para meter voor het verwijderen van dubbele computer namen. De lijst wordt gesorteerd in de standaard volgorde, oplopend.

### Voor beeld 8: een teken reeks sorteren als een geheel getal

In dit voor beeld ziet u hoe u een tekst bestand met teken reeks objecten kunt sorteren als gehele getallen. U kunt elke opdracht naar de pijp lijn verzenden om te `Get-Member` controleren of de objecten teken reeksen zijn in plaats van gehele getallen. In deze voor beelden `ProductId.txt` bevat het bestand een niet-gesorteerde lijst met product nummers.

In het eerste voor beeld `Get-Content` wordt de inhoud van het bestand en pijp lijnen naar de `Sort-Object` cmdlet opgehaald. `Sort-Object` Hiermee worden de teken reeks objecten in oplopende volg orde gesorteerd.

```
PS> Get-Content -Path C:\Test\ProductId.txt | Sort-Object
0
1
12345
1500
2
2800
3500
4100
500
6200
77
88
99999

PS> Get-Content -Path C:\Test\ProductId.txt | Sort-Object {[int]$_}
0
1
2
77
88
500
1500
2800
3500
4100
6200
12345
99999
```

In het tweede voor beeld `Get-Content` wordt de inhoud van het bestand en pijp lijnen naar de `Sort-Object` cmdlet opgehaald. `Sort-Object` maakt gebruik van een script blok om de teken reeksen te converteren naar gehele getallen. In de voorbeeld code wordt `[int]` de teken reeks geconverteerd naar een geheel getal en `$_` wordt elke teken reeks aangeduid als de pijp lijn. De objecten met gehele getallen worden via de pijp lijn naar de `Sort-Object` cmdlet verzonden.
`Sort-Object` de objecten van het gehele getal worden in numerieke volg orde gesorteerd.

### Voor beeld 9: stabiele sorteringen gebruiken

Wanneer u de para meters **Top** , **bottom** of **stabiele** gebruikt, worden de gesorteerde objecten bezorgd in de volg orde waarin ze zijn ontvangen, `Sort-Object` wanneer de sorteer criteria gelijk zijn. In dit voor beeld sorteren we de getallen één tot en met 20 door de bijbehorende waarde modulo 3. De modulo-waarde ligt tussen nul en twee.

```powershell
PS> 1..20 |Sort-Object {$_ % 3}
18
3
15
6
12
9
1
16
13
10
7
4
19
11
8
14
5
17
2
20

PS> 1..20 |Sort-Object {$_ % 3} -Stable
3
6
9
12
15
18
1
4
7
10
13
16
19
2
5
8
11
14
17
20
```

De uitvoer van de eerste Sorteer bewerking is correct gegroepeerd op basis van de modulus waarde, maar de afzonderlijke items worden niet binnen het bereik van de modulus gesorteerd. Bij de tweede sortering wordt de **stabiele** optie gebruikt om een stabiele sortering te retour neren.

## PARAMETERS

### -Onder

Hiermee geeft u het aantal objecten op dat moet worden opgehaald vanaf het einde van een gesorteerde object matrix. Dit resulteert in een stabiele Sorteer bewerking.

Deze para meter is geïntroduceerd in Power shell 6,0.

```yaml
Type: System.Int32
Parameter Sets: Bottom
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -CaseSensitive

Hiermee wordt aangegeven dat de sortering hoofdletter gevoelig is. Sorteren is standaard niet hoofdletter gevoelig.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: Case-insensitive
Accept pipeline input: False
Accept wildcard characters: False
```

### -Cultuur

Hiermee geeft u de cultuur configuratie op die moet worden gebruikt voor het sorteren. Gebruiken `Get-Culture` om de configuratie van de systeem cultuur weer te geven.

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

### -Aflopend

Hiermee wordt aangegeven dat `Sort-Object` de objecten in aflopende volg orde worden gesorteerd. De standaard instelling is oplopende volg orde.

Als u meerdere eigenschappen met verschillende sorteer volgorden wilt sorteren, gebruikt u een hash-tabel. Met een hash-tabel kunt u bijvoorbeeld één eigenschap in oplopende volg orde sorteren en een andere eigenschap in aflopende volg orde.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: Ascending
Accept pipeline input: False
Accept wildcard characters: False
```

### -Input object

Als u objecten wilt sorteren, stuurt u ze omlaag in de pijp lijn `Sort-Object` . Als u de para meter **input object** gebruikt voor het verzenden van een verzameling items, `Sort-Object` ontvangt u één object dat de verzameling vertegenwoordigt. Omdat één object niet kan worden gesorteerd, `Sort-Object` retourneert de hele verzameling ongewijzigd.

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

### -Eigenschap

Hiermee geeft u de eigenschapnamen `Sort-Object` op waarmee de objecten worden gesorteerd. Joker tekens zijn toegestaan.
Objecten worden gesorteerd op basis van de eigenschaps waarden. Als u geen eigenschap opgeeft, `Sort-Object` sorteert u op basis van de standaard eigenschappen voor het object type of de objecten zelf.

Meerdere eigenschappen kunnen in oplopende volg orde, aflopende volg orde of een combi natie van sorteer volgorden worden gesorteerd. Wanneer u meerdere eigenschappen opgeeft, worden de objecten gesorteerd op de eerste eigenschap. Als meerdere objecten dezelfde waarde hebben voor de eerste eigenschap, worden deze objecten gesorteerd op de tweede eigenschap. Dit proces wordt voortgezet totdat er geen specifieke eigenschappen of groepen van objecten zijn.

De waarde van de **eigenschaps** parameter kan een berekende eigenschap zijn. Als u een berekende eigenschap wilt maken, gebruikt u een hash-tabel.

Geldige sleutels voor een hash-tabel zijn als volgt:

- `expression` - `<string>` of `<script block>`
- `ascending` of `descending` - `<boolean>`

Zie [about_Calculated_Properties](../Microsoft.PowerShell.Core/About/about_Calculated_Properties.md)voor meer informatie.

```yaml
Type: System.Object[]
Parameter Sets: (All)
Aliases:

Required: False
Position: 0
Default value: Default properties
Accept pipeline input: False
Accept wildcard characters: True
```

### -Boven

Hiermee geeft u het aantal objecten op dat moet worden opgehaald uit het begin van een gesorteerde object matrix. Dit resulteert in een stabiele Sorteer bewerking.

Deze para meter is geïntroduceerd in Power shell 6,0.

```yaml
Type: System.Int32
Parameter Sets: Top
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Uniek

Hiermee wordt aangegeven dat `Sort-Object` dubbele waarden worden geëlimineerd en alleen de unieke leden van de verzameling worden geretourneerd. Het eerste exemplaar van een unieke waarde is opgenomen in de gesorteerde uitvoer.

**Uniek** is hoofdletter gevoelig. Teken reeksen die alleen verschillen per teken, worden als hetzelfde beschouwd.
Bijvoorbeeld teken en teken.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: All
Accept pipeline input: False
Accept wildcard characters: False
```

### -Stabiel

De gesorteerde objecten worden afgeleverd in de volg orde waarin ze zijn ontvangen toen de sorteer criteria gelijk zijn.

Deze para meter is toegevoegd aan Power shell v-6.2.0.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: Default
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

U kunt de objecten waarop moet worden gesorteerd, door sluizen `Sort-Object` .

## UITVOER

### System. Management. Automation. PSObject

`Sort-Object` Hiermee worden de gesorteerde objecten geretourneerd.

## OPMERKINGEN

`Sort-Object`Met de cmdlet worden objecten gesorteerd op basis van eigenschappen die zijn opgegeven in de opdracht of de standaard sorteer eigenschappen voor het object type. Standaard sorteer eigenschappen worden gedefinieerd met behulp `PropertySet` van de naam `DefaultKeyPropertySet` in een `types.ps1xml` bestand. Zie [about_Types.ps1XML](/powershell/module/Microsoft.PowerShell.Core/About/about_Types.ps1xml)voor meer informatie.

Als een object niet over een van de opgegeven eigenschappen beschikt, wordt de eigenschaps waarde voor dat object geïnterpreteerd `Sort-Object` als **Null** en aan het einde van de sorteer volgorde geplaatst.

Als er geen sorteer eigenschappen beschikbaar zijn, probeert Power shell de objecten zelf te vergelijken.
`Sort-Object` maakt gebruik van de **vergelijkings** methode voor elke eigenschap. Als een eigenschap niet wordt geïmplementeerd **IComparable** , wordt de waarde van de eigenschap door de cmdlet geconverteerd naar een teken reeks en wordt de **vergelijkings** methode voor **System. String** gebruikt. Zie de [methode PSObject. CompareTo (object)](/dotnet/api/system.management.automation.psobject.compareto)voor meer informatie.

Als u sorteert op een opgesomde eigenschap zoals **status** , wordt `Sort-Object` gesorteerd op de opsommings waarden. Voor Windows-Services is **gestopt** met de waarde **1** en **wordt uitgevoerd** met de waarde **4**.
**Gestopt** wordt gesorteerd voordat deze **wordt uitgevoerd** vanwege de opgesomde waarden. Zie [ServiceControllerStatus](/dotnet/api/system.serviceprocess.servicecontrollerstatus)voor meer informatie.

De prestaties van het sorteer algoritme zijn langzamer wanneer u een stabiele Sorteer bewerking uitvoert.

## GERELATEERDE KOPPELINGEN

[about_Calculated_Properties](../Microsoft.PowerShell.Core/About/about_Calculated_Properties.md)

[about_Hash_Tables](../Microsoft.PowerShell.Core/About/about_Hash_Tables.md)

[about_Types.ps1XML](../Microsoft.PowerShell.Core/About/about_Types.ps1xml.md)

[Compare-object](Compare-Object.md)

[ForEach-object](../Microsoft.PowerShell.Core/ForEach-Object.md)

[Groep-object](Group-Object.md)

[Meting object](Measure-Object.md)

[New-Object](New-Object.md)

[Select-Object](Select-Object.md)

[T-object](Tee-Object.md)
