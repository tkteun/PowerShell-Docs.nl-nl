---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 3/26/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/get-eventlog?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-EventLog
ms.openlocfilehash: ab1a97dc3c78bbfdcc239fd573ef3b1f839e2b21
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/07/2020
ms.locfileid: "93250808"
---
# Get-EventLog

## SAMENVATTING
Hiermee haalt u de gebeurtenissen in een gebeurtenis logboek of een lijst met de gebeurtenis logboeken op de lokale computer of externe computers op.

## SYNTAXIS

### LogName (standaard)

```
Get-EventLog [-LogName] <String> [-ComputerName <String[]>] [-Newest <Int32>] [-After <DateTime>]
 [-Before <DateTime>] [-UserName <String[]>] [[-InstanceId] <Int64[]>] [-Index <Int32[]>]
 [-EntryType <String[]>] [-Source <String[]>] [-Message <String>] [-AsBaseObject]
 [<CommonParameters>]
```

### Lijst

```
Get-EventLog [-ComputerName <String[]>] [-List] [-AsString] [<CommonParameters>]
```

## BESCHRIJVING

De `Get-EventLog` cmdlet haalt gebeurtenissen en gebeurtenis logboeken op van lokale en externe computers. Standaard `Get-EventLog` haalt logboeken van de lokale computer op. Als u logboeken van externe computers wilt ontvangen, gebruikt u de para meter **ComputerName** .

U kunt de `Get-EventLog` para meters en eigenschaps waarden gebruiken om te zoeken naar gebeurtenissen. De cmdlet haalt gebeurtenissen op die overeenkomen met de opgegeven eigenschaps waarden.

Power shell-cmdlets die het `EventLog` zelfstandig naam woord bevatten, werken alleen in klassieke Windows-gebeurtenis logboeken, zoals toepassing, systeem of beveiliging. Als u logboeken wilt ophalen die gebruikmaken van de Windows-gebeurtenis logboek technologie in Windows Vista en latere versies van Windows, gebruikt u `Get-WinEvent` .

> [!NOTE]
> `Get-EventLog` maakt gebruik van een Win32 API die is afgeschaft. De resultaten zijn mogelijk niet nauw keurig. Gebruik `Get-WinEvent` in plaats daarvan de cmdlet.

## VOORBEELDEN

### Voor beeld 1: gebeurtenis logboeken op de lokale computer ophalen

In dit voor beeld wordt de lijst weer gegeven met gebeurtenis logboeken die beschikbaar zijn op de lokale computer. De namen in de logboek kolom worden gebruikt in combi natie met de para meter **LogName** om op te geven welk logboek moet worden doorzocht op gebeurtenissen.

```powershell
Get-EventLog -List
```

```Output
Max(K)   Retain   OverflowAction      Entries  Log
------   ------   --------------      -------  ---
15,168        0   OverwriteAsNeeded   20,792   Application
15,168        0   OverwriteAsNeeded   12,559   System
15,360        0   OverwriteAsNeeded   11,173   Windows PowerShell
```

De `Get-EventLog` cmdlet gebruikt de **List** -para meter om de beschik bare logboeken weer te geven.

### Voor beeld 2: recente vermeldingen ophalen uit een gebeurtenis logboek op de lokale computer

In dit voor beeld worden recente vermeldingen opgehaald uit het logboek voor systeem gebeurtenissen.

```powershell
Get-EventLog -LogName System -Newest 5
```

```Output
Index   Time          EntryType    Source              InstanceID   Message
-----   ----          ---------    ------              ----------   -------
13820   Jan 17 19:16  Error        DCOM                     10016   The description for Event...
13819   Jan 17 19:08  Error        DCOM                     10016   The description for Event...
13818   Jan 17 19:06  Information  Service Control...  1073748864   The start type of the Back...
13817   Jan 17 19:05  Error        DCOM                     10016   The description for Event...
13815   Jan 17 19:03  Information  Microsoft-Windows...        35   The time service is now sync...
```

De `Get-EventLog` cmdlet gebruikt de para meter **LogName** om het systeem gebeurtenis logboek op te geven. De **nieuwste** para meter retourneert de vijf meest recente gebeurtenissen.

### Voor beeld 3: alle bronnen zoeken voor een specifiek aantal vermeldingen in een gebeurtenis logboek

In dit voor beeld ziet u hoe u alle bronnen vindt die zijn opgenomen in de 1000 meest recente vermeldingen in het systeem gebeurtenis logboek.

```powershell
$Events = Get-EventLog -LogName System -Newest 1000
$Events | Group-Object -Property Source -NoElement | Sort-Object -Property Count -Descending
```

```Output
Count   Name
-----   ----
  110   DCOM
   65   Service Control Manager
   51   Microsoft-Windows-Kern...
   14   EventLog
   14   BTHUSB
   13   Win32k
```

De `Get-EventLog` cmdlet gebruikt de para meter **LogName** om het systeem logboek op te geven. De **nieuwste** para meter selecteert de meest recente gebeurtenissen van 1000. De gebeurtenis objecten worden opgeslagen in de `$Events` variabele. De `$Events` objecten worden naar de-cmdlet verzonden via de pijp lijn `Group-Object` .
`Group-Object` gebruikt de **eigenschaps** parameter om de objecten op bron te groeperen en telt het aantal objecten voor elke bron. De para meter **microelement** verwijdert de groeps leden uit de uitvoer.
De `Sort-Object` cmdlet gebruikt de para meter **Property** om te sorteren op het aantal van elke bron naam.
De **aflopende** para meter sorteert de lijst in order by aantal van hoogste naar laagste.

### Voor beeld 4: fout gebeurtenissen van een specifiek gebeurtenis logboek ophalen

In dit voor beeld worden fout gebeurtenissen van het systeem gebeurtenis logboek opgehaald.

```powershell
Get-EventLog -LogName System -EntryType Error
```

```Output
Index Time          EntryType   Source  InstanceID Message
----- ----          ---------   ------  ---------- -------
13296 Jan 16 13:53  Error       DCOM    10016 The description for Event ID '10016' in Source...
13291 Jan 16 13:51  Error       DCOM    10016 The description for Event ID '10016' in Source...
13245 Jan 16 11:45  Error       DCOM    10016 The description for Event ID '10016' in Source...
13230 Jan 16 11:07  Error       DCOM    10016 The description for Event ID '10016' in Source...
```

De `Get-EventLog` cmdlet gebruikt de para meter **LogName** om het systeem logboek op te geven. Met de para meter **entry type is** worden de gebeurtenissen gefilterd om alleen fout gebeurtenissen weer te geven.

### Voor beeld 5: gebeurtenissen ophalen uit een gebeurtenis logboek met een InstanceId en een bron waarde

In dit voor beeld worden gebeurtenissen uit het systeem logboek voor een specifieke InstanceId en bron opgehaald.

```powershell
Get-EventLog -LogName System -InstanceId 10016 -Source DCOM
```

```Output
Index Time          EntryType  Source  InstanceID  Message
----- ----          ---------  ------  ----------  -------
13245 Jan 16 11:45  Error      DCOM         10016  The description for Event ID '10016' in Source...
13230 Jan 16 11:07  Error      DCOM         10016  The description for Event ID '10016' in Source...
13219 Jan 16 10:00  Error      DCOM         10016  The description for Event ID '10016' in Source...
```

De `Get-EventLog` cmdlet gebruikt de para meter **LogName** om het systeem logboek op te geven. De para meter **InstanceId** selecteert de gebeurtenissen met de opgegeven exemplaar-id. De para meter **Source** geeft u de gebeurtenis eigenschap op.

### Voor beeld 6: gebeurtenissen van meerdere computers ophalen

Met deze opdracht worden de gebeurtenissen uit het systeem gebeurtenis logboek op drie computers opgehaald: Server01, Server02 en Server03.

```powershell
Get-EventLog -LogName System -ComputerName Server01, Server02, Server03
```

De `Get-EventLog` cmdlet gebruikt de para meter **LogName** om het systeem logboek op te geven. De para meter **ComputerName** maakt gebruik van een door komma's gescheiden teken reeks voor het weer geven van de computers waarvan u de gebeurtenis logboeken wilt ophalen.

### Voor beeld 7: alle gebeurtenissen ophalen die een specifiek woord in het bericht bevatten

Met deze opdracht worden alle gebeurtenissen in het systeem gebeurtenis logboek opgehaald die een specifiek woord in het bericht van de gebeurtenis bevatten. Het is mogelijk dat de waarde van uw opgegeven **bericht** parameter is opgenomen in de inhoud van het bericht, maar niet wordt weer gegeven in de Power shell-console.

```powershell
Get-EventLog -LogName System -Message *description*
```

```Output
Index Time          EntryType   Source       InstanceID   Message
----- ----          ---------   ------       ----------   -------
13821 Jan 17 19:17  Error       DCOM              10016   The description for Event ID '10016'...
13820 Jan 17 19:16  Error       DCOM              10016   The description for Event ID '10016'...
13819 Jan 17 19:08  Error       DCOM              10016   The description for Event ID '10016'...
```

De `Get-EventLog` cmdlet gebruikt de para meter **LogName** om het systeem gebeurtenis logboek op te geven. De para meter **bericht** geeft een woord op waarnaar moet worden gezocht in het veld bericht van elke gebeurtenis.

### Voor beeld 8: de eigenschaps waarden van een gebeurtenis weer geven

In dit voor beeld ziet u hoe alle eigenschappen en waarden van een gebeurtenis worden weer gegeven.

```powershell
$A = Get-EventLog -LogName System -Newest 1
$A | Select-Object -Property *
```

```Output
EventID            : 10016
MachineName        : localhost
Data               : {}
Index              : 13821
Category           : (0)
CategoryNumber     : 0
EntryType          : Error
Message            : The description for Event ID '10016' in Source 'DCOM'...
Source             : DCOM
ReplacementStrings : {Local,...}
InstanceId         : 10016
TimeGenerated      : 1/17/2019 19:17:23
TimeWritten        : 1/17/2019 19:17:23
UserName           : username
Site               :
Container          :
```

De `Get-EventLog` cmdlet gebruikt de para meter **LogName** om het systeem gebeurtenis logboek op te geven. Met de **nieuwste** para meter selecteert u het meest recente gebeurtenis object. Het object wordt opgeslagen in de `$A` variabele. Het object in de `$A` variabele wordt via de pijp lijn naar de `Select-Object` cmdlet verzonden.
`Select-Object` gebruikt de **eigenschaps** parameter met een asterisk ( `*` ) om alle eigenschappen van het object te selecteren.

### Voor beeld 9: gebeurtenissen uit een gebeurtenis logboek ophalen met behulp van een bron-en gebeurtenis-ID

In dit voor beeld worden gebeurtenissen voor een opgegeven bron en gebeurtenis-ID opgehaald.

```powershell
Get-EventLog -LogName Application -Source Outlook | Where-Object {$_.EventID -eq 63} |
              Select-Object -Property Source, EventID, InstanceId, Message
```

```Output
Source   EventID   InstanceId   Message
------   -------   ----------   -------
Outlook       63   1073741887   The Exchange web service request succeeded.
Outlook       63   1073741887   Outlook detected a change notification.
Outlook       63   1073741887   The Exchange web service request succeeded.
```

De `Get-EventLog` cmdlet gebruikt de para meter **LogName** om het gebeurtenis logboek van de toepassing op te geven. De para meter **Source** specificeert de naam van de toepassing, Outlook. De objecten worden naar de-cmdlet verzonden via de pijp lijn `Where-Object` . Voor elk object in de pijp lijn gebruikt de- `Where-Object` cmdlet de variabele `$_.EventID` om de eigenschap gebeurtenis-id te vergelijken met de opgegeven waarde. De objecten worden naar de-cmdlet verzonden via de pijp lijn `Select-Object` . `Select-Object` gebruikt de para meter **Property** om de eigenschappen te selecteren die u wilt weer geven in de Power shell-console.

### Voor beeld 10: gebeurtenissen en groepen op basis van een eigenschap ophalen

```powershell
Get-EventLog -LogName System -UserName NT* | Group-Object -Property UserName -NoElement |
              Select-Object -Property Count, Name
```

```Output
Count  Name
-----  ----
6031   NT AUTHORITY\SYSTEM
  42   NT AUTHORITY\LOCAL SERVICE
   4   NT AUTHORITY\NETWORK SERVICE
```

De `Get-EventLog` cmdlet gebruikt de para meter **LogName** om het systeem logboek op te geven. De para meter **username** bevat het `*` Joker teken sterretje () om een deel van de gebruikers naam op te geven. De gebeurtenis objecten worden in de pijp lijn naar de `Group-Object` cmdlet verzonden. `Group-Object` maakt gebruik van de **eigenschap** para meter om op te geven dat de eigenschap **username** wordt gebruikt om de objecten te groeperen en het aantal objecten voor elke gebruikers naam te tellen. De para meter **microelement** verwijdert de groeps leden uit de uitvoer. De objecten worden naar de-cmdlet verzonden via de pijp lijn `Select-Object` .
`Select-Object` gebruikt de para meter **Property** om de eigenschappen te selecteren die u wilt weer geven in de Power shell-console.

### Voor beeld 11: gebeurtenissen ophalen die zijn opgetreden tijdens een bepaald datum-en tijds bereik

In dit voor beeld worden fout gebeurtenissen van het logboek voor systeem gebeurtenissen opgehaald voor een opgegeven datum-en tijds bereik. De para meters **before** en **After** hebben de datum en het tijds bereik ingesteld, maar worden uitgesloten van de uitvoer.

```powershell
$Begin = Get-Date -Date '1/17/2019 08:00:00'
$End = Get-Date -Date '1/17/2019 17:00:00'
Get-EventLog -LogName System -EntryType Error -After $Begin -Before $End
```

```Output
Index Time          EntryType   Source   InstanceID  Message
----- ----          ---------   ------   ----------  -------
13821 Jan 17 13:40  Error       DCOM          10016  The description for Event ID...
13820 Jan 17 13:11  Error       DCOM          10016  The description for Event ID...
...
12372 Jan 17 10:08  Error       DCOM          10016  The description for Event ID...
12371 Jan 17 09:04  Error       DCOM          10016  The description for Event ID...
```

De `Get-Date` cmdlet gebruikt de para meter **date** om een datum en tijd op te geven. De **DateTime** -objecten worden opgeslagen in `$Begin` de `$End` variabelen en. De `Get-EventLog` cmdlet gebruikt de para meter **LogName** om het systeem logboek op te geven. De **entry type is** para meter geeft u het type fout gebeurtenis op. Het datum-en tijds bereik wordt ingesteld met de para meter en de variabele **After** `$Begin` en de **before** -para meter en de `$End` variabele.

## PARAMETERS

### -Na

Hiermee worden gebeurtenissen opgehaald die zijn opgetreden na een opgegeven datum en tijd. De datum en tijd van de para meter **After** worden uitgesloten van de uitvoer. Voer een **DateTime** -object in, zoals de waarde die door de cmdlet wordt geretourneerd `Get-Date` .

```yaml
Type: System.DateTime
Parameter Sets: LogName
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -AsBaseObject

Geeft aan dat met deze cmdlet een standaard **System. Diagnostics. EventLogEntry** -object wordt geretourneerd voor elke gebeurtenis. Zonder deze para meter `Get-EventLog` retourneert een Extended **PSObject** -object met aanvullende eigenschappen voor **Eventlog** , **Source** en **InstanceId** .

Als u het effect van deze para meter wilt zien, pipet u de gebeurtenissen naar de `Get-Member` cmdlet en bekijkt u de waarde **TypeName** in het resultaat.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: LogName
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -AsString

Geeft aan dat deze cmdlet de uitvoer als teken reeksen retourneert in plaats van objecten.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: List
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Vóór

Hiermee worden gebeurtenissen opgehaald die zijn opgetreden vóór een opgegeven datum en tijd. De datum en tijd van de para meter **before** worden uitgesloten van de uitvoer. Voer een **DateTime** -object in, zoals de waarde die door de cmdlet wordt geretourneerd `Get-Date` .

```yaml
Type: System.DateTime
Parameter Sets: LogName
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -ComputerName

Met deze para meter wordt de NetBIOS-naam, het Internet Protocol (IP)-adres of een Fully Qualified Domain Name (FQDN) van de externe computer opgegeven.

Als de para meter **ComputerName** niet is opgegeven, wordt `Get-EventLog` standaard de lokale computer gebruikt. De para meter accepteert ook een punt ( `.` ) om de lokale computer op te geven.

De para meter **ComputerName** is niet gebaseerd op externe communicatie met Windows Power shell. U kunt `Get-EventLog` met de para meter **ComputerName** ook gebruiken als uw computer niet is geconfigureerd om externe opdrachten uit te voeren.

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

### -Entry type is

Geeft als een teken reeks matrix het type vermelding van de gebeurtenissen die met deze cmdlet worden opgehaald.

De aanvaardbare waarden voor deze parameter zijn:

- Fout
- Informatie
- FailureAudit
- SuccessAudit
- Waarschuwing

```yaml
Type: System.String[]
Parameter Sets: LogName
Aliases: ET
Accepted values: Error, Information, FailureAudit, SuccessAudit, Warning

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Index

Hiermee geeft u de index waarden op die moeten worden opgehaald uit het gebeurtenis logboek. De para meter accepteert een door komma's gescheiden teken reeks met waarden.

```yaml
Type: System.Int32[]
Parameter Sets: LogName
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -InstanceId

Hiermee geeft u de exemplaar-Id's op die moeten worden opgehaald uit het gebeurtenis logboek. De para meter accepteert een door komma's gescheiden teken reeks met waarden.

```yaml
Type: System.Int64[]
Parameter Sets: LogName
Aliases:

Required: False
Position: 1
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Lijst

Hiermee wordt de lijst met gebeurtenis logboeken op de computer weer gegeven.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: List
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -LogName

Hiermee geeft u de naam van één gebeurtenis logboek op. Als u de logboek namen wilt vinden `Get-EventLog -List` . Joker tekens zijn toegestaan. Deze parameter is vereist.

```yaml
Type: System.String
Parameter Sets: LogName
Aliases: LN

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: True
```

### -Bericht

Hiermee wordt een teken reeks in het gebeurtenis bericht opgegeven. U kunt deze para meter gebruiken om te zoeken naar berichten die bepaalde woorden of zinsdelen bevatten. Joker tekens zijn toegestaan.

```yaml
Type: System.String
Parameter Sets: LogName
Aliases: MSG

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: True
```

### -Nieuwste

Begint met de nieuwste gebeurtenissen en haalt het opgegeven aantal gebeurtenissen op. Het aantal gebeurtenissen is bijvoorbeeld vereist `-Newest 100` . Hiermee geeft u het maximum aantal gebeurtenissen op dat wordt geretourneerd.

```yaml
Type: System.Int32
Parameter Sets: LogName
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Source

Hiermee geeft u als een teken reeks matrix de bronnen op die zijn geschreven naar het logboek dat deze cmdlet krijgt. Joker tekens zijn toegestaan.

```yaml
Type: System.String[]
Parameter Sets: LogName
Aliases: ABO

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: True
```

### -GebruikersNaam

Hiermee geeft u als een teken reeks matrix de gebruikers namen op die aan gebeurtenissen zijn gekoppeld. Voer namen of naam patronen in, zoals `User01` , `User*` of `Domain01\User*` . Joker tekens zijn toegestaan.

```yaml
Type: System.String[]
Parameter Sets: LogName
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: True
```

### CommonParameters

Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable. Zie [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)voor meer informatie.

## INVOER

### Geen

U kunt geen pipe invoer naar `Get-EventLog` .

## UITVOER

### System. Diagnostics. EventLogEntry. System. Diagnostics. EventLog. System. String

Als de para meter **LogName** is opgegeven, is de uitvoer een verzameling **System. Diagnostics. EventLogEntry** -objecten.

Als alleen de **lijst** parameter is opgegeven, is de uitvoer een verzameling **System. Diagnostics. Eventlog** -objecten.

Als zowel de **lijst** -als de **AsString** -para meters zijn opgegeven, is de uitvoer een verzameling **System. String** -objecten.

## OPMERKINGEN

De cmdlets `Get-EventLog` en `Get-WinEvent` worden niet ondersteund in de Windows Preinstallation Environment (Windows PE).

## GERELATEERDE KOPPELINGEN

[Clear-EventLog](Clear-EventLog.md)

[Get-WinEvent](../Microsoft.PowerShell.Diagnostics/Get-WinEvent.md)

[Groep-object](../Microsoft.PowerShell.Utility/Group-Object.md)

[Limit-EventLog](Limit-EventLog.md)

[Nieuw-gebeurtenis logboek](New-EventLog.md)

[Remove-EventLog](Remove-EventLog.md)

[Select-Object](../Microsoft.PowerShell.Utility/Select-Object.md)

[Weer geven-EventLog](Show-EventLog.md)

[Write-EventLog](Write-EventLog.md)
