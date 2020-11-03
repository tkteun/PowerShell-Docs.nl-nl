---
external help file: Microsoft.PowerShell.Commands.Diagnostics.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Diagnostics
ms.date: 11/20/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.diagnostics/get-winevent?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-WinEvent
ms.openlocfilehash: ba68ded5afe19a98555e7224692ab8dbe09e3486
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/07/2020
ms.locfileid: "93250120"
---
# Get-WinEvent

## SAMENVATTING
Hiermee worden gebeurtenissen opgehaald uit gebeurtenis logboeken en logboek bestanden voor gebeurtenis tracering op lokale en externe computers.

## SYNTAXIS

### GetLogSet (standaard)

```
Get-WinEvent [[-LogName] <String[]>] [-MaxEvents <Int64>] [-ComputerName <String>]
 [-Credential <PSCredential>] [-FilterXPath <String>] [-Force] [-Oldest] [<CommonParameters>]
```

### ListLogSet

```
Get-WinEvent [-ListLog] <String[]> [-ComputerName <String>] [-Credential <PSCredential>] [-Force]
 [<CommonParameters>]
```

### ListProviderSet

```
Get-WinEvent [-ListProvider] <String[]> [-ComputerName <String>] [-Credential <PSCredential>]
 [<CommonParameters>]
```

### GetProviderSet

```
Get-WinEvent [-ProviderName] <String[]> [-MaxEvents <Int64>] [-ComputerName <String>]
 [-Credential <PSCredential>] [-FilterXPath <String>] [-Force] [-Oldest] [<CommonParameters>]
```

### Bestandenset

```
Get-WinEvent [-Path] <String[]> [-MaxEvents <Int64>] [-Credential <PSCredential>]
 [-FilterXPath <String>] [-Oldest] [<CommonParameters>]
```

### HashQuerySet

```
Get-WinEvent [-MaxEvents <Int64>] [-ComputerName <String>] [-Credential <PSCredential>]
 [-FilterHashtable] <Hashtable[]> [-Force] [-Oldest] [<CommonParameters>]
```

### XmlQuerySet

```
Get-WinEvent [-MaxEvents <Int64>] [-ComputerName <String>] [-Credential <PSCredential>]
 [-FilterXml] <XmlDocument> [-Oldest] [<CommonParameters>]
```

## BESCHRIJVING

De `Get-WinEvent` cmdlet haalt gebeurtenissen op uit gebeurtenis logboeken, waaronder klassieke logboeken, zoals de **systeem** -en **toepassings** Logboeken. De cmdlet haalt gegevens op uit gebeurtenis logboeken die worden gegenereerd door de Windows-gebeurtenis logboek technologie die is geïntroduceerd in Windows Vista. En gebeurtenissen in logboek bestanden die worden gegenereerd door **Event Tracing for Windows (etw)**. `Get-WinEvent`Retourneert standaard gebeurtenis gegevens in de volg orde van nieuwste naar oudste.

`Get-WinEvent` een lijst met gebeurtenis logboeken en providers van gebeurtenis Logboeken. U kunt de opdracht onderbreken door op <kbd>CTRL</kbd> + <kbd>C</kbd>te drukken. U kunt gebeurtenissen uit geselecteerde logboeken ophalen of van logboeken die zijn gegenereerd door geselecteerde gebeurtenis providers. En u kunt gebeurtenissen uit meerdere bronnen combi neren in één opdracht.
`Get-WinEvent` Hiermee kunt u gebeurtenissen filteren met XPath-query's, gestructureerde XML-query's en hash-tabel query's.

Als u Power shell niet als beheerder uitvoert, worden er mogelijk fout berichten weer geven waarin u geen informatie over een logboek kunt ophalen.

## VOORBEELDEN

### Voor beeld 1: alle logboeken ophalen van een lokale computer

Met deze opdracht worden alle gebeurtenis logboeken op de lokale computer opgehaald. De logboeken worden weer gegeven in de volg orde waarin `Get-WinEvent` ze worden opgehaald. Klassieke logboeken worden eerst opgehaald, gevolgd door de nieuwe Windows-gebeurtenis Logboeken.
Het is mogelijk dat de **RecordCount** van een logboek null is, leeg of nul.

```powershell
Get-WinEvent -ListLog *
```

```Output
LogMode   MaximumSizeInBytes RecordCount LogName
-------   ------------------ ----------- -------
Circular            15532032       14500 Application
Circular             1052672         117 Azure Information Protection
Circular             1052672        3015 CxAudioSvcLog
Circular            20971520             ForwardedEvents
Circular            20971520           0 HardwareEvents
```

De `Get-WinEvent` cmdlet haalt logboek gegevens op van de computer. De para meter **ListLog** maakt gebruik `*` van het Joker teken sterretje () om informatie over elk logboek weer te geven.

### Voor beeld 2: het klassieke installatie logboek ophalen

Met deze opdracht wordt een **EventLogConfiguration** -object opgehaald dat het klassieke **installatie** logboek vertegenwoordigt. Het object bevat informatie over het logboek, zoals de bestands grootte, de provider, het bestandspad en of het logboek is ingeschakeld.

```powershell
Get-WinEvent -ListLog Setup | Format-List -Property *
```

```Output
FileSize                       : 69632
IsLogFull                      : False
LastAccessTime                 : 3/13/2019 09:41:46
LastWriteTime                  : 3/13/2019 09:41:46
OldestRecordNumber             : 1
RecordCount                    : 23
LogName                        : Setup
LogType                        : Operational
LogIsolation                   : Application
IsEnabled                      : True
IsClassicLog                   : False
SecurityDescriptor             : O:BAG:SYD: ...
LogFilePath                    : %SystemRoot%\System32\Winevt\Logs\Setup.evtx
MaximumSizeInBytes             : 1052672
LogMode                        : Circular
OwningProviderName             : Microsoft-Windows-Eventlog
ProviderNames                  : {Microsoft-Windows-WUSA, Microsoft-Windows-ActionQueue...
ProviderLevel                  :
ProviderKeywords               :
ProviderBufferSize             : 64
ProviderMinimumNumberOfBuffers : 0
ProviderMaximumNumberOfBuffers : 64
ProviderLatency                : 1000
ProviderControlGuid            :
```

De `Get-WinEvent` cmdlet gebruikt de para meter **ListLog** om het **installatie** logboek op te geven. Het object wordt vanuit de pijp lijn naar de `Format-List` cmdlet verzonden. `Format-List` gebruikt de **eigenschaps** parameter met het `*` Joker teken sterretje () om elke eigenschap weer te geven.

### Voor beeld 3: gebeurtenis logboeken ophalen van een server

Met deze opdracht worden alleen gebeurtenis logboeken op de lokale computer die gebeurtenissen bevatten. Het is mogelijk dat de **RecordCount** van een logboek null of nul is. In het voor beeld wordt de `$_` variabele gebruikt. Zie [about_Automatic_Variables](../Microsoft.PowerShell.Core/about/about_automatic_variables.md)voor meer informatie.

```powershell
Get-WinEvent -ListLog * -ComputerName localhost | Where-Object { $_.RecordCount }
```

```Output
LogMode   MaximumSizeInBytes RecordCount LogName
-------   ------------------ ----------- -------
Circular            15532032       14546 Application
Circular             1052672         117 Azure Information Protection
Circular             1052672        2990 CxAudioSvcLog
Circular             1052672           9 MSFTVPN Setup
Circular             1052672         282 OAlerts
```

De `Get-WinEvent` cmdlet haalt logboek gegevens op van de computer. De para meter **ListLog** maakt gebruik `*` van het Joker teken sterretje () om informatie over elk logboek weer te geven. Met de para meter **ComputerName** geeft u de logboeken op van de lokale computer, **localhost**. De objecten worden naar de-cmdlet verzonden via de pijp lijn `Where-Object` . `Where-Object` gebruikt `$_.RecordCount` om alleen logboeken te retour neren die gegevens bevatten. `$_` is een variabele die staat voor het huidige object in de pijp lijn. **RecordCount** is een eigenschap van het object met een waarde die niet null is.

### Voor beeld 4: gebeurtenis logboeken van meerdere servers ophalen

In dit voor beeld worden objecten opgehaald die de gebeurtenis logboeken van de **toepassing** op drie computers vertegenwoordigen: Server01, Server02 en Server03. Het sleutel woord **foreach** wordt gebruikt omdat de para meter **ComputerName** slechts één waarde accepteert. Zie [about_Foreach](../Microsoft.PowerShell.Core/about/about_Foreach.md)voor meer informatie.

```powershell
$S = 'Server01', 'Server02', 'Server03'
ForEach ($Server in $S) {
  Get-WinEvent -ListLog Application -ComputerName $Server |
    Select-Object LogMode, MaximumSizeInBytes, RecordCount, LogName,
      @{name='ComputerName'; expression={$Server}} |
    Format-Table -AutoSize
}
```

```Output
 LogMode MaximumSizeInBytes RecordCount LogName     ComputerName
 ------- ------------------ ----------- -------     ------------
Circular           15532032       14577 Application Server01
Circular           15532032        9689 Application Server02
Circular           15532032        5309 Application Server03
```

De variabele `$S` bevat de namen drie servers: **Server01** , **Server02** en **Server03**. De instructie **foreach** maakt gebruik van een lus voor het verwerken van elke server `($Server in $S)` . Het script blok in de accolades ( `{ }` ) voert de `Get-WinEvent` opdracht uit. De **ListLog** para meter geeft u het **toepassings** logboek op. De para meter **ComputerName** gebruikt de variabele `$Server` om logboek gegevens van elke server op te halen.

De objecten worden naar de-cmdlet verzonden via de pijp lijn `Select-Object` . `Select-Object` Hiermee worden de eigenschappen **LogMode** , **MaximumSizeInBytes** , **RecordCount** en **LogName** opgehaald en wordt een berekende expressie gebruikt om de **computer naam** weer te geven met behulp van de `$Server` variabele. De objecten worden in de pijp lijn naar de `Format-Table` cmdlet verzonden om de uitvoer in de Power shell-console weer te geven. Met de para meter **AutoSize** wordt de uitvoer op het scherm weer gegeven.

### Voor beeld 5: gebeurtenis logboek providers en logboek namen ophalen

Met deze opdracht worden de gebeurtenis logboek providers en de Logboeken beschreven waarnaar ze schrijven.

```powershell
Get-WinEvent -ListProvider *
```

```Output
Name     : .NET Runtime
LogLinks : {Application}
Opcodes  : {}
Tasks    : {}

Name     : .NET Runtime Optimization Service
LogLinks : {Application}
Opcodes  : {}
Tasks    : {}
```

De `Get-WinEvent` cmdlet haalt logboek gegevens op van de computer. De para meter **ListProvider** maakt gebruik `*` van het Joker teken sterretje () om informatie over elke provider weer te geven. In de uitvoer is de **naam** de provider en **LogLinks** is het logboek dat door de provider wordt geschreven.

### Voor beeld 6: alle gebeurtenis logboek providers ophalen die naar een specifiek logboek schrijven

Met deze opdracht worden alle providers opgehaald die naar het **toepassings** logboek schrijven.

```powershell
(Get-WinEvent -ListLog Application).ProviderNames
```

```Output
.NET Runtime
.NET Runtime Optimization Service
Application
Application Error
Application Hang
Application Management
```

De `Get-WinEvent` cmdlet haalt logboek gegevens op van de computer. De para meter **ListLog** maakt gebruik van **toepassing** om objecten voor dat logboek op te halen. **ProviderNames** is een eigenschap van het object en geeft de providers weer die naar het **toepassings** logboek schrijven.

### Voor beeld 7: de provider namen van gebeurtenis logboeken ophalen die een specifieke teken reeks bevatten

Met deze opdracht worden de gebeurtenis logboek providers opgehaald met namen die een specifieke teken reeks bevatten in de naam van de provider.

```powershell
Get-WinEvent -ListProvider *Policy*
```

```Output
Name     : Group Policy Applications
LogLinks : {Application}
Opcodes  : {}
Tasks    : {}

Name     : Group Policy Client
LogLinks : {Application}
Opcodes  : {}
Tasks    : {}

Name     : Group Policy Data Sources
LogLinks : {Application}
Opcodes  : {}
Tasks    : {}
```

De `Get-WinEvent` cmdlet haalt logboek gegevens op van de computer. De para meter **ListProvider** maakt gebruik `*` van het Joker teken asterisk () om het **beleid** overal binnen de naam van de provider te vinden.

### Voor beeld 8: gebeurtenis-Id's ophalen die de gebeurtenis provider genereert

Met deze opdracht wordt een lijst weer gegeven met de gebeurtenis-Id's die de gebeurtenis provider **micro soft-Windows-architectuur** genereert samen met de beschrijving van de gebeurtenis.

```powershell
(Get-WinEvent -ListProvider Microsoft-Windows-GroupPolicy).Events | Format-Table Id, Description
```

```Output
  Id  Description
  --  -----------
1500  The Group Policy settings for the computer were processed successfully...
1501  The Group Policy settings for the user were processed successfully...
4115  Group Policy Service started.
4116  Started the Group Policy service initialization phase.
4117  Group Policy Session started.
```

De `Get-WinEvent` cmdlet haalt logboek gegevens op van de computer. De **ListProvider** para meter geeft u de provider, **micro soft-Windows-architectuur**. De expressie wordt tussen haakjes geplaatst en maakt gebruik van de eigenschap **Events** om objecten op te halen. De objecten worden naar de-cmdlet verzonden via de pijp lijn `Format-Table` . `Format-Table` Hiermee worden de **id** en de **Beschrijving** van de gebeurtenis objecten weer gegeven.

### Voor beeld 9: logboek gegevens ophalen uit gebeurtenis object eigenschappen

In dit voor beeld ziet u hoe u informatie over de inhoud van een logboek kunt ophalen met behulp van eigenschappen van het gebeurtenis object.
Gebeurtenis objecten worden opgeslagen in een variabele en vervolgens gegroepeerd en geteld op **gebeurtenis-id** en **niveau**.

```powershell
$Event = Get-WinEvent -LogName 'Windows PowerShell'
$Event.Count
$Event | Group-Object -Property Id -NoElement | Sort-Object -Property Count -Descending
$Event | Group-Object -Property LevelDisplayName -NoElement
```

```Output
195

Count  Name
-----  ----
  147  600
   22  400
   21  601
    3  403
    2  103

Count  Name
-----  ----
    2  Warning
  193  Information
```

De `Get-WinEvent` cmdlet gebruikt de para meter **LogName** om het gebeurtenis logboek van **Windows Power shell** op te geven. De gebeurtenis objecten worden opgeslagen in de `$Event` variabele. De eigenschap **Count** van `$Event` toont het totale aantal geregistreerde gebeurtenissen.

De `$Event` variabele wordt via de pijp lijn naar de `Group-Object` cmdlet verzonden. `Group-Object` gebruikt de para meter **Property** om de **id-** eigenschap op te geven en telt de objecten op de waarde van de gebeurtenis-id. De para meter **microelement** verwijdert andere eigenschappen van de uitvoer van objecten. De gegroepeerde objecten worden in de pijp lijn naar de `Sort-Object` cmdlet verzonden. `Sort-Object` gebruikt de para meter **Property** om de objecten te sorteren op **aantal**. Met de para meter **Aflopend** wordt de uitvoer weer gegeven per aantal, van hoog naar laag. In de uitvoer bevat de kolom **aantal** het totale aantal gebeurtenissen. De **naam** kolom bevat de gegroepeerde gebeurtenis-id-nummers.

De `$Event` variabele wordt via de pijp lijn naar de `Group-Object` cmdlet verzonden. `Group-Object` gebruikt de para meter **Property** om de eigenschap **LevelDisplayName** op te geven en telt de objecten op **LevelDisplayName**. De objecten worden gegroepeerd op basis van de niveaus, zoals **waarschuwing** en **informatie**.
De para meter **microelement** verwijdert andere eigenschappen uit de uitvoer. In de uitvoer bevat de kolom **aantal** het totale aantal gebeurtenissen. De **naam** kolom bevat de gegroepeerde **LevelDisplayName**.

### Voor beeld 10: fout gebeurtenissen met een opgegeven teken reeks in hun naam ophalen

In dit voor beeld wordt een door komma's gescheiden teken reeks met logboek namen gebruikt. De uitvoer wordt gegroepeerd op het niveau van de fout of waarschuwing en de naam van het logboek.

```powershell
Get-WinEvent -LogName *PowerShell*, Microsoft-Windows-Kernel-WHEA* |
  Group-Object -Property LevelDisplayName, LogName -NoElement |
    Format-Table -AutoSize
```

```Output
Count  Name
-----  ----
    1  Error, PowerShellCore/Operational
   26  Information, Microsoft-Windows-Kernel-WHEA/Operational
  488  Information, Microsoft-Windows-PowerShell/Operational
   77  Information, PowerShellCore/Operational
 9835  Information, Windows PowerShell
   19  Verbose, PowerShellCore/Operational
  444  Warning, Microsoft-Windows-PowerShell/Operational
  512  Warning, PowerShellCore/Operational
```

De `Get-WinEvent` cmdlet haalt logboek gegevens op van de computer. De para meter **LogName** maakt gebruik van een door komma's gescheiden teken reeks met het `*` Joker teken sterretje () om de logboek namen op te geven. De objecten worden naar de-cmdlet verzonden via de pijp lijn `Group-Object` . `Group-Object` gebruikt de **eigenschaps** parameter voor het groeperen van de objecten op **LevelDisplayName** en **LogName**. De para meter **microelement** verwijdert andere eigenschappen uit de uitvoer. De gegroepeerde objecten worden in de pijp lijn naar de `Format-Table` cmdlet verzonden. `Format-Table` maakt gebruik van de para meter **AutoSize** om de kolommen op te maken. De kolom **aantal** bevat het totale aantal gebeurtenissen. De kolom **naam** bevat de gegroepeerde **LevelDisplayName** en **LogName**.

### Voor beeld 11: gebeurtenissen ophalen uit een gearchiveerd gebeurtenis logboek

`Get-WinEvent` kan gebeurtenis gegevens ophalen uit opgeslagen logboek bestanden. In dit voor beeld wordt gebruikgemaakt van een gearchiveerd Power shell-logboek dat is opgeslagen op de lokale computer.

```powershell
Get-WinEvent -Path 'C:\Test\Windows PowerShell.evtx'
```

```Output
   ProviderName: PowerShell

TimeCreated              Id LevelDisplayName  Message
-----------              -- ----------------  -------
3/15/2019 13:54:13      403 Information       Engine state is changed from Available to Stopped...
3/15/2019 13:54:13      400 Information       Engine state is changed from None to Available...
3/15/2019 13:54:13      600 Information       Provider "Variable" is Started...
3/15/2019 13:54:13      600 Information       Provider "Function" is Started...
3/15/2019 13:54:13      600 Information       Provider "FileSystem" is Started...
```

De `Get-WinEvent` cmdlet haalt logboek gegevens op van de computer. De para meter **Path** geeft de naam van de map en het bestand aan.

### Voor beeld 12: een specifiek aantal gebeurtenissen uit een gearchiveerd gebeurtenis logboek ophalen

Met deze opdrachten wordt een specifiek aantal gebeurtenissen uit een gearchiveerd gebeurtenis logboek opgehaald. `Get-WinEvent` heeft para meters die een maximum aantal gebeurtenissen of de oudste gebeurtenissen kunnen verkrijgen. In dit voor beeld wordt gebruikgemaakt van een gearchiveerd Power shell-logboek dat is opgeslagen in **C:\Test\PowerShellCore Operational. evtx**.

```powershell
Get-WinEvent -Path 'C:\Test\PowerShellCore Operational.evtx' -MaxEvents 100
```

```Output
   ProviderName: PowerShellCore

TimeCreated                 Id   LevelDisplayName  Message
-----------                 --   ----------------  -------
3/15/2019 09:54:54        4104   Warning           Creating Scriptblock text (1 of 1):...
3/15/2019 09:37:13       40962   Information       PowerShell console is ready for user input
3/15/2019 07:56:24        4104   Warning           Creating Scriptblock text (1 of 1):...
...
3/7/2019 10:53:22        40961   Information       PowerShell console is starting up
3/7/2019 10:53:22         8197   Verbose           Runspace state changed to Opening
3/7/2019 10:53:22         8195   Verbose           Opening RunspacePool
```

De `Get-WinEvent` cmdlet haalt logboek gegevens op van de computer. De para meter **Path** specificeert de map en de bestands naam. De para meter **MaxEvents** geeft aan dat 100 records worden weer gegeven, van nieuw naar oud.

### Voor beeld 13: Event Tracing for Windows

Event Tracing for Windows (ETW) gebeurtenissen naar het logboek schrijven als gebeurtenissen plaatsvinden. De gebeurtenissen worden opgeslagen in de volg orde van oudste naar nieuwste. Een gearchiveerd ETW-bestand wordt opgeslagen als een `.etl` **TraceLog. etl**.
De gebeurtenissen worden weer gegeven in de volg orde waarin ze naar het logboek worden geschreven, dus de *oudste* para meter is vereist.

```powershell
Get-WinEvent -Path 'C:\Tracing\TraceLog.etl' -Oldest |
  Sort-Object -Property TimeCreated -Descending |
    Select-Object -First 100
```

`Get-WinEvent`Met de cmdlet worden logboek gegevens opgehaald uit het gearchiveerde bestand. De para meter **Path** geeft de naam van de map en het bestand aan. De **oudste** para meter wordt gebruikt voor het uitvoeren van gebeurtenissen in de volg orde waarin ze zijn geschreven, oudste naar nieuwste. De objecten worden via de pijp lijn naar de cmdlet verzonden, waarbij de `Sort-Object` `Sort-Object` objecten in aflopende volg orde worden gesorteerd op basis van de waarde van de eigenschap **TimeCreated** . De objecten worden via de pijp lijn naar de `Select-Object` cmdlet verzonden die de nieuwste gebeurtenissen van 100 weergeeft.

### Voor beeld 14: gebeurtenissen ophalen uit een logboek voor gebeurtenis tracering

In dit voor beeld ziet u hoe u de gebeurtenissen van een logboek bestand voor gebeurtenis tracering ( `.etl` ) en een gearchiveerd Windows Power shell-logboek bestand () kunt ophalen `.evtx` . U kunt meerdere bestands typen combi neren in één opdracht.
Omdat de bestanden van hetzelfde type **.NET Framework** object **bevatten, kunt** u ze met dezelfde eigenschappen filteren. De opdracht vereist de **oudste** para meter omdat deze wordt gelezen vanuit een `.etl` bestand, maar de **oudste** para meter is van toepassing op elk bestand.

```powershell
Get-WinEvent -Path 'C:\Tracing\TraceLog.etl', 'C:\Test\Windows PowerShell.evtx' -Oldest |
  Where-Object { $_.Id -eq '403' }
```

`Get-WinEvent`Met de cmdlet worden logboek gegevens opgehaald uit de gearchiveerde bestanden. De para meter **Path** gebruikt een door komma's gescheiden lijst om elke map en de bestands naam op te geven. De **oudste** para meter wordt gebruikt voor het uitvoeren van gebeurtenissen in de volg orde waarin ze zijn geschreven, oudste naar nieuwste. De objecten worden naar de-cmdlet verzonden via de pijp lijn `Where-Object` . `Where-Object` maakt gebruik van een script blok voor het zoeken van gebeurtenissen met de **Id** **403**. De `$_` variabele vertegenwoordigt het huidige object in de pijp lijn en de **id** is de gebeurtenis-id-eigenschap.

### Voor beeld 15: resultaten van gebeurtenis logboeken filteren

In dit voor beeld ziet u een aantal methoden voor het filteren en selecteren van gebeurtenissen uit een gebeurtenis logboek. Met al deze opdrachten worden gebeurtenissen opgehaald die in de afgelopen 24 uur zijn opgetreden in het gebeurtenis logboek van **Windows Power shell** .
De filter methoden zijn efficiënter dan het gebruik van de `Where-Object` cmdlet. Filters worden toegepast wanneer de objecten worden opgehaald. `Where-Object` Hiermee worden alle objecten opgehaald en vervolgens filters toegepast op alle objecten.

```powershell
# Using the Where-Object cmdlet:
$Yesterday = (Get-Date) - (New-TimeSpan -Day 1)
Get-WinEvent -LogName 'Windows PowerShell' | Where-Object { $_.TimeCreated -ge $Yesterday }

# Using the FilterHashtable parameter:
$Yesterday = (Get-Date) - (New-TimeSpan -Day 1)
Get-WinEvent -FilterHashtable @{ LogName='Windows PowerShell'; Level=3; StartTime=$Yesterday }

# Using the FilterXML parameter:
$xmlQuery = @'
<QueryList>
  <Query Id="0" Path="Windows PowerShell">
    <Select Path="System">*[System[(Level=3) and
        TimeCreated[timediff(@SystemTime) &lt;= 86400000]]]</Select>
  </Query>
</QueryList>
'@
Get-WinEvent -FilterXML $xmlQuery

# Using the FilterXPath parameter:
$XPath = '*[System[Level=3 and TimeCreated[timediff(@SystemTime) &lt;= 86400000]]]'
Get-WinEvent -LogName 'Windows PowerShell' -FilterXPath $XPath
```

### Voor beeld 16: FilterHashtable gebruiken om gebeurtenissen op te halen uit het toepassings logboek

In dit voor beeld wordt de para meter **FilterHashtable** gebruikt om gebeurtenissen uit het **toepassings** logboek op te halen. De hash-tabel gebruikt **sleutel-** waardeparen. Zie [Get-WinEvent Query's maken met FilterHashtable](/powershell/scripting/samples/Creating-Get-WinEvent-queries-with-FilterHashtable)voor meer informatie over de para meter **FilterHashtable** .
Zie [about_Hash_Tables](../Microsoft.PowerShell.Core/about/about_hash_tables.md)voor meer informatie over hash-tabellen.

```powershell
$Date = (Get-Date).AddDays(-2)
Get-WinEvent -FilterHashtable @{ LogName='Application'; StartTime=$Date; Id='1003' }
```

De `Get-Date` cmdlet gebruikt de methode **addDays** om een datum op te halen die twee dagen vóór de huidige datum valt. Het object Date wordt opgeslagen in de `$Date` variabele.

De `Get-WinEvent` cmdlet haalt logboek gegevens op. De para meter **FilterHashtable** wordt gebruikt om de uitvoer te filteren. De sleutel **LogName** geeft de waarde aan als het **toepassings** logboek. De toets **StartTime** gebruikt de waarde die is opgeslagen in de `$Date` variabele. De **id-** sleutel maakt gebruik van een gebeurtenis-id-waarde van **1003**.

### Voor beeld 17: FilterHashtable gebruiken om toepassings fouten op te halen

In dit voor beeld wordt de para meter **FilterHashtable** gebruikt voor het vinden van toepassings fouten in Internet Explorer die in de afgelopen week zijn opgetreden.

```powershell
$StartTime = (Get-Date).AddDays(-7)
Get-WinEvent -FilterHashtable @{
  Logname='Application'
  ProviderName='Application Error'
  Data='iexplore.exe'
  StartTime=$StartTime
}
```

De `Get-Date` cmdlet gebruikt de methode **addDays** om een datum te verkrijgen die zeven dagen voor de huidige datum ligt. Het object Date wordt opgeslagen in de `$StartTime` variabele.

De `Get-WinEvent` cmdlet haalt logboek gegevens op. De para meter **FilterHashtable** wordt gebruikt om de uitvoer te filteren. De sleutel **LogName** geeft de waarde aan als het **toepassings** logboek. De sleutel **ProviderName** gebruikt de waarde, **toepassings fout** , die de **bron** van de gebeurtenis is. De **gegevens** sleutel gebruikt de waarde **iexplore.exe** de sleutel **StartTime** maakt gebruik van de waarde die is opgeslagen in de `$StartTime` variabele.

## PARAMETERS

### -ComputerName

Hiermee geeft u de naam op van de computer die met deze cmdlet gebeurtenissen uit de gebeurtenis logboeken ontvangt. Typ de NetBIOS-naam, een IP-adres of de Fully Qualified Domain Name (FQDN) van de computer. De standaard waarde is de lokale computer, **localhost**. Deze para meter accepteert slechts één computer naam per keer.

Als u gebeurtenis logboeken wilt ophalen van externe computers, configureert u de firewall poort voor de Event Log-service om externe toegang toe te staan.

Deze cmdlet is niet afhankelijk van externe communicatie met Power shell. U kunt de para meter **ComputerName** ook gebruiken als uw computer niet is geconfigureerd om externe opdrachten uit te voeren.

```yaml
Type: System.String
Parameter Sets: GetLogSet, ListLogSet, ListProviderSet, GetProviderSet, HashQuerySet, XmlQuerySet
Aliases: Cn

Required: False
Position: Named
Default value: Local computer
Accept pipeline input: False
Accept wildcard characters: False
```

### -Credential

Hiermee geeft u een gebruikers account op dat is gemachtigd om deze actie uit te voeren. De standaard waarde is de huidige gebruiker.

Typ een gebruikers naam, zoals **gebruiker01** of **Domain01\User01**. U kunt ook een **PSCredential** -object invoeren, zoals het dat is gegenereerd door de `Get-Credential` cmdlet. Als u een gebruikers naam typt, wordt u gevraagd een wacht woord op te vragen. Als u alleen de parameter naam typt, wordt u gevraagd om een gebruikers naam en wacht woord in te voeren.

```yaml
Type: System.Management.Automation.PSCredential
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: Current user
Accept pipeline input: False
Accept wildcard characters: False
```

### -FilterHashtable

Hiermee geeft u een query in hash-tabel indeling op om gebeurtenissen uit een of meer gebeurtenis logboeken te selecteren. De query bevat een hash-tabel met een of meer **sleutel-** waardeparen.

Hash-tabel query's hebben de volgende regels:

- Sleutels en waarden zijn niet hoofdletter gevoelig.
- Joker tekens zijn alleen geldig in de waarden die zijn gekoppeld aan de sleutels **LogName** en **ProviderName** .
- Elke sleutel kan slechts eenmaal in elke hash-tabel worden weer gegeven.
- De waarde voor het **pad** heeft paden naar `.etl` , `.evt` en `.evtx` logboek bestanden.
- De sleutels **LogName** , **Path** en **ProviderName** kunnen worden gebruikt in dezelfde query.
- De sleutel **GebruikersID** kan een geldige beveiligings-id (sid) of een domein accountnaam hebben die kan worden gebruikt om een geldig **System. Security. Principal. NTAccount-object** te maken.
- De **gegevens** waarde heeft gebeurtenis gegevens in een niet-gegroepeerde veld. Bijvoorbeeld gebeurtenissen in klassieke gebeurtenis Logboeken.

Wanneer `Get-WinEvent` een **sleutel/waarde** -paar niet kan interpreteren, wordt de sleutel geïnterpreteerd als een hoofdletter gevoelige naam voor de gebeurtenis gegevens in de gebeurtenis.

De geldige `Get-WinEvent` **sleutel/waarde-** paren zijn als volgt:

- **LogName**=`<String[]>`
- **ProviderName**=`<String[]>`
- **Programmapad**=`<String[]>`
- **Woord**=`<Long[]>`
- **ID**=`<Int32[]>`
- **Afvlakking**=`<Int32[]>`
- **StartTime**=`<DateTime>`
- **Tijd**=`<DateTime>`
- **Naam**=`<SID>`
- **Gegevens**=`<String[]>`

```yaml
Type: System.Collections.Hashtable[]
Parameter Sets: HashQuerySet
Aliases:

Required: True
Position: 1
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -FilterXPath

Hiermee geeft u een XPath-query op die met deze cmdlet gebeurtenissen uit een of meer logboeken selecteert.

Zie [XPath-verwijzing](/previous-versions/dotnet/netframework-4.0/ms256115(v=vs.100)) en het gedeelte selectie filters van de [gebeurtenis selectie](/previous-versions/aa385231(v=vs.85))voor meer informatie over de XPath-taal.

```yaml
Type: System.String
Parameter Sets: GetLogSet, GetProviderSet, FileSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -FilterXml

Hiermee geeft u een gestructureerde XML-query op die met deze cmdlet gebeurtenissen uit een of meer gebeurtenis logboeken selecteert.

Als u een geldige XML-query wilt genereren, gebruikt u de functies **aangepaste weer gave maken** en **huidige logboeken filteren** in Windows Logboeken. Gebruik de items in het dialoog venster om een query te maken en klik vervolgens op het tabblad XML om de query in XML-indeling weer te geven. U kunt de XML van het tabblad XML kopiëren naar de waarde van de para meter **FilterXml** . Zie Logboeken Help voor meer informatie over de functies van Logboeken.

Gebruik een XML-query om een complexe query met verschillende XPath-instructies te maken. Met de XML-indeling kunt u ook een **onderdrukking XML-** element gebruiken waarmee gebeurtenissen van de query worden uitgesloten. Zie [query schema](/windows/win32/wes/queryschema-schema) en het gedeelte XML-gebeurtenis query's van de [gebeurtenis selectie](/previous-versions/aa385231(v=vs.85))voor meer informatie over het XML-schema voor gebeurtenis logboek query's.

```yaml
Type: System.Xml.XmlDocument
Parameter Sets: XmlQuerySet
Aliases:

Required: True
Position: 1
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Force

Hiermee worden fout opsporing en analytische logboeken opgehaald, naast andere gebeurtenis Logboeken. De para meter **Force** is vereist om een debug-of analytische logboek op te halen wanneer de waarde van de para meter name joker tekens bevat.

De `Get-WinEvent` cmdlet sluit deze logboeken standaard uit tenzij u de volledige naam van een debug-of analytisch logboek opgeeft.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: GetLogSet, ListLogSet, GetProviderSet, HashQuerySet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -ListLog

Hiermee geeft u de gebeurtenis Logboeken. Geef de namen van de gebeurtenis logboeken op in een lijst met door komma's gescheiden waarden. Joker tekens zijn toegestaan. Als u alle logboeken wilt ophalen, gebruikt u het `*` Joker teken asterisk ().

```yaml
Type: System.String[]
Parameter Sets: ListLogSet
Aliases:

Required: True
Position: 1
Default value: None
Accept pipeline input: False
Accept wildcard characters: True
```

### -ListProvider

Hiermee geeft u de gebeurtenis logboek providers op die met deze cmdlet worden opgehaald. Een gebeurtenis logboek provider is een programma of service die gebeurtenissen naar het gebeurtenis logboek schrijft.

Geef de naam van de provider op in een lijst met door komma's gescheiden waarden. Joker tekens zijn toegestaan. Gebruik het Joker teken sterretje () om de providers van alle gebeurtenis logboeken op de computer op te halen `*` .

```yaml
Type: System.String[]
Parameter Sets: ListProviderSet
Aliases:

Required: True
Position: 1
Default value: None
Accept pipeline input: False
Accept wildcard characters: True
```

### -LogName

Hiermee geeft u de gebeurtenis logboeken waarvan deze cmdlet gebeurtenissen ophaalt. Geef de namen van de gebeurtenis logboeken op in een lijst met door komma's gescheiden waarden. Joker tekens zijn toegestaan. U kunt logboek namen ook door sluizen naar de `Get-WinEvent` cmdlet.

> [!NOTE]
> Power shell beperkt het aantal logboeken dat u kunt aanvragen niet. Met de cmdlet wordt echter `Get-WinEvent` een query uitgevoerd op de Windows-API met een limiet van 256. Hierdoor kan het lastig zijn om al uw logboeken in één keer te filteren. U kunt dit probleem omzeilen door een `foreach` lus te gebruiken om elk logboek als volgt te herhalen: `Get-WinEvent -ListLog * | ForEach-Object{ Get-WinEvent -LogName $_.Logname }`

```yaml
Type: System.String[]
Parameter Sets: GetLogSet
Aliases:

Required: False
Position: 1
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: True
```

### -MaxEvents

Hiermee geeft u het maximum aantal gebeurtenissen op dat wordt geretourneerd. Voer een geheel getal in, bijvoorbeeld 100. Standaard worden alle gebeurtenissen in de logboeken of bestanden geretourneerd.

```yaml
Type: System.Int64
Parameter Sets: GetLogSet, GetProviderSet, FileSet, HashQuerySet, XmlQuerySet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Oudste

Geef aan dat met deze cmdlet de gebeurtenissen in oudste eerste volg orde worden opgehaald. Standaard worden gebeurtenissen in de meest recente-eerste volg orde geretourneerd.

Deze para meter is vereist voor het ophalen van gebeurtenissen van `.etl` en `.evt` bestanden, en van fouten opsporen en analytische Logboeken. In deze bestanden worden gebeurtenissen in de oudste eerste volg orde vastgelegd en de gebeurtenissen kunnen alleen in de eerste volg orde worden geretourneerd.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: GetLogSet, GetProviderSet, FileSet, HashQuerySet, XmlQuerySet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Path

Hiermee geeft u het pad op naar de gebeurtenis logboek bestanden waarvan deze cmdlet gebeurtenissen ophaalt. Voer de paden naar de logboek bestanden in een lijst met door komma's gescheiden waarden in of gebruik joker tekens om patronen voor het bestandspad te maken.

`Get-WinEvent` ondersteunt bestanden met de `.evt` bestandsnaam `.evtx` extensies, en `.etl` . U kunt gebeurtenissen uit verschillende bestanden en bestands typen in dezelfde opdracht invoegen.

```yaml
Type: System.String[]
Parameter Sets: FileSet
Aliases: PSPath

Required: True
Position: 1
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: True
```

### -ProviderName

Hiermee geeft u als een teken reeks matrix de gebeurtenis logboek providers op waarvan deze cmdlet gebeurtenissen ophaalt. Geef de namen van providers op in een lijst met door komma's gescheiden waarden of gebruik joker tekens om naam patronen voor de provider te maken.

Een gebeurtenis logboek provider is een programma of service die gebeurtenissen naar het gebeurtenis logboek schrijft. Het is geen Power shell-provider.

```yaml
Type: System.String[]
Parameter Sets: GetProviderSet
Aliases:

Required: True
Position: 1
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: True
```

### CommonParameters

Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable. Zie [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)voor meer informatie.

## INVOER

### System. String, System.Xml.Xmldocument, System. Collections. hashtabel

U kunt een **LogName** (teken reeks), een **FilterXML** -query of een **FilterHashtable** -query door pijp lijnen `Get-WinEvent` .

## UITVOER

### System. Diagnostics. Evente. Reader. EventLogConfiguration, System. Diagnostics. Evente. Reader. EventLogRecord, System. Diagnostics. eventing. Reader. ProviderMetadata

Met de **ListLog** para meter ListLog `Get-WinEvent` retourneert **System. Diagnostics. eventing. Reader. EventLogConfiguration** -objecten.

Met de **ListProvider** para meter ListProvider `Get-WinEvent` retourneert **System. Diagnostics. eventing. Reader. ProviderMetadata** -objecten.

Met alle andere para meters `Get-WinEvent` retourneert **System. Diagnostics. eventing. Reader. EventLogRecord** -objecten.

## OPMERKINGEN

`Get-WinEvent` is ontworpen om de cmdlet te vervangen `Get-EventLog` op computers met Windows Vista en latere versies van Windows. `Get-EventLog` Hiermee worden alleen gebeurtenissen in klassieke gebeurtenis logboeken opgehaald. `Get-EventLog` wordt bewaard voor achterwaartse compatibiliteit.

De `Get-WinEvent` `Get-EventLog` cmdlets en worden niet ondersteund in de Pre-Installation Environment (Windows PE).

## GERELATEERDE KOPPELINGEN

[about_Automatic_Variables](../Microsoft.PowerShell.Core/about/about_automatic_variables.md)

[about_Foreach](../Microsoft.PowerShell.Core/about/about_Foreach.md)

[about_Hash_Tables](../Microsoft.PowerShell.Core/about/about_hash_tables.md)

[Get-WinEvent-query's maken met FilterHashtable](/powershell/scripting/samples/Creating-Get-WinEvent-queries-with-FilterHashtable)

[Format-Table](../Microsoft.PowerShell.Utility/Format-Table.md)

[Groep-object](../Microsoft.PowerShell.Utility/Group-Object.md)

[Sorteer object](../Microsoft.PowerShell.Utility/Sort-Object.md)

[Where-object](../Microsoft.PowerShell.Core/Where-Object.md)
