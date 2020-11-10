---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/get-process?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-Process
ms.openlocfilehash: d1a576ce9c718561718bac5fee065983a057d458
ms.sourcegitcommit: 2c311274ce721cd1072dcf2dc077226789e21868
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 11/10/2020
ms.locfileid: "94388294"
---
# Get-Process

## SAMENVATTING
Hiermee worden de processen opgehaald die worden uitgevoerd op de lokale computer of op een externe computer.

## SYNTAXIS

### Naam (standaard)

```
Get-Process [[-Name] <String[]>] [-ComputerName <String[]>] [-Module] [-FileVersionInfo] [<CommonParameters>]
```

### NameWithUserName

```
Get-Process [[-Name] <String[]>] [-IncludeUserName] [<CommonParameters>]
```

### IdWithUserName

```
Get-Process -Id <Int32[]> [-IncludeUserName] [<CommonParameters>]
```

### Id

```
Get-Process -Id <Int32[]> [-ComputerName <String[]>] [-Module] [-FileVersionInfo] [<CommonParameters>]
```

### InputObjectWithUserName

```
Get-Process -InputObject <Process[]> [-IncludeUserName] [<CommonParameters>]
```

### Input object

```
Get-Process -InputObject <Process[]> [-ComputerName <String[]>] [-Module] [-FileVersionInfo]
 [<CommonParameters>]
```

## BESCHRIJVING

De `Get-Process` cmdlet haalt de processen op een lokale of externe computer op.

Zonder para meters haalt deze cmdlet alle processen op de lokale computer op. U kunt ook een bepaald proces opgeven op basis van de proces naam of proces-ID (PID) of een proces object door de pijp lijn door geven aan deze cmdlet.

Met deze cmdlet wordt standaard een proces object geretourneerd dat gedetailleerde informatie over het proces bevat en methoden ondersteunt waarmee u het proces kunt starten en stoppen. U kunt ook de para meters van de `Get-Process` cmdlet gebruiken om informatie over de bestands versie op te halen voor het programma dat wordt uitgevoerd in het proces en om de modules op te halen die het proces heeft geladen.

## VOORBEELDEN

### Voor beeld 1: een lijst met alle actieve processen op de lokale computer ophalen

```powershell
Get-Process
```

Met deze opdracht wordt een lijst met alle actieve processen opgehaald die worden uitgevoerd op de lokale computer. Zie de sectie [opmerkingen](#notes) voor een definitie van elke kolom.

### Voor beeld 2: alle beschik bare gegevens over een of meer processen ophalen

```powershell
Get-Process winword, explorer | Format-List *
```

Met deze opdracht worden alle beschik bare gegevens over de processen Winword en Explorer op de computer opgehaald. Hierbij wordt de para meter **name** gebruikt voor het opgeven van de processen, maar de naam van de optionele para meter wordt wegge laten. De pijplijn operator `|` geeft de gegevens door aan de `Format-List` cmdlet, die alle beschik bare eigenschappen `*` van de objecten Winword en Explorer-proces weergeeft.

U kunt de processen ook identificeren aan de hand van hun proces-Id's. Bijvoorbeeld `Get-Process -Id 664, 2060`.

### Voor beeld 3: alle processen ophalen met een werkset die groter is dan een opgegeven grootte

```powershell
Get-Process | Where-Object {$_.WorkingSet -gt 20000000}
```

Met deze opdracht worden alle processen opgehaald die een werkset hebben die groter is dan 20 MB. De cmdlet wordt gebruikt `Get-Process` voor het ophalen van alle actieve processen. De pijplijn operator `|` geeft de proces objecten door aan de `Where-Object` cmdlet, waarmee alleen het object wordt geselecteerd met een waarde die groter is dan 20.000.000 bytes voor de eigenschap **workingset** .

**Workingset** is een van de vele eigenschappen van proces objecten. Als u alle eigenschappen wilt weer geven, typt u `Get-Process | Get-Member` . Standaard worden de waarden van alle eigenschappen van het bedrag in bytes weer gegeven, zelfs als de standaard weergave deze in kilo bytes en mega bytes vermeldt.

### Voor beeld 4: processen op de computer in groepen weer geven op basis van prioriteit

```powershell
$A = Get-Process
$A | Get-Process | Format-Table -View priority
```

Met deze opdrachten worden de processen op de computer in groepen weer geven op basis van hun prioriteits klasse. De eerste opdracht haalt alle processen op de computer op en slaat deze vervolgens op in de `$A` variabele.

Met de tweede opdracht pipet u het **proces** object dat in de `$A` variabele is opgeslagen, naar de `Get-Process` cmdlet en vervolgens naar de `Format-Table` cmdlet, waarmee de processen worden opgemaakt met behulp van de weer gave **prioriteit** .

De weer gave **prioriteit** en andere weer gaven worden gedefinieerd in de PS1XML-indelings bestanden in de Power shell-basis directory ( `$pshome` ).

### Voor beeld 5: een eigenschap toevoegen aan de standaard Get-Process uitvoer weergave

```powershell
Get-Process powershell -ComputerName S1, localhost | Format-Table `
    @{Label = "NPM(K)"; Expression = {[int]($_.NPM / 1024)}},
    @{Label = "PM(K)"; Expression = {[int]($_.PM / 1024)}},
    @{Label = "WS(K)"; Expression = {[int]($_.WS / 1024)}},
    @{Label = "VM(M)"; Expression = {[int]($_.VM / 1MB)}},
    @{Label = "CPU(s)"; Expression = {if ($_.CPU) {$_.CPU.ToString("N")}}},
    Id, MachineName, ProcessName -AutoSize
```

```Output
NPM(K) PM(K) WS(K) VM(M) CPU(s)   Id MachineName ProcessName
------ ----- ----- ----- ------   -- ----------- -----------
     6 23500 31340   142 1.70   1980 S1          powershell
     6 23500 31348   142 2.75   4016 S1          powershell
    27 54572 54520   576 5.52   4428 localhost   powershell
```

In dit voor beeld worden processen opgehaald van de lokale computer en een externe computer (S1). De opgehaalde processen worden door gegeven aan de `Format-Table` opdracht waarmee de eigenschap **MachineName** wordt toegevoegd aan de standaard `Get-Process` uitvoer weergave.

### Voor beeld 6: versie-informatie voor een proces ophalen

```powershell
Get-Process powershell -FileVersionInfo
```

```Output
ProductVersion   FileVersion      FileName
--------------   -----------      --------
6.1.6713.1       6.1.6713.1 (f... C:\WINDOWS\system32\WindowsPowerShell\v1.0\powershell.exe
```

Met deze opdracht wordt de **FileVersionInfo** -para meter gebruikt om de versie gegevens op te halen voor het powershell.exe-bestand dat de belangrijkste module voor het Power Shell-proces is.

Als u deze opdracht wilt uitvoeren met processen waarvan u geen eigenaar bent in Windows Vista en latere versies van Windows, moet u Power shell openen met de optie als administrator uitvoeren.

### Voor beeld 7: modules ophalen die met het opgegeven proces zijn geladen

```powershell
Get-Process SQL* -Module
```

Met deze opdracht wordt de **module** parameter gebruikt om de modules op te halen die door het proces zijn geladen.
Met deze opdracht worden de modules opgehaald voor de processen die namen hebben die met SQL beginnen.

Als u deze opdracht wilt uitvoeren in Windows Vista en latere versies van Windows met processen waarvan u geen eigenaar bent, moet u Power shell starten met de optie als administrator uitvoeren.

### Voor beeld 8: de eigenaar van een proces zoeken

```powershell
Get-Process pwsh -IncludeUserName
```

```Output
Handles      WS(K)   CPU(s)     Id UserName            ProcessName
-------      -----   ------     -- --------            -----------
    782     132080     2.08   2188 DOMAIN01\user01     powershell
```

```powershell
$p = Get-WmiObject Win32_Process -Filter "name='powershell.exe'"
$p.GetOwner()
```

```Output
__GENUS          : 2
__CLASS          : __PARAMETERS
__SUPERCLASS     :
__DYNASTY        : __PARAMETERS
__RELPATH        :
__PROPERTY_COUNT : 3
__DERIVATION     : {}
__SERVER         :
__NAMESPACE      :
__PATH           :
Domain           : DOMAIN01
ReturnValue      : 0
User             : user01
```

De eerste opdracht laat zien hoe u de eigenaar van een proces kunt vinden. De para meter **IncludeUserName** vereist verhoogde gebruikers rechten (als administrator uitvoeren). De uitvoer laat zien dat de eigenaar Domain01\user01. is

De tweede en derde opdracht zijn een andere manier om de eigenaar van een proces te vinden.

De tweede opdracht wordt gebruikt `Get-WmiObject` om het Power Shell-proces op te halen.
Het wordt opgeslagen in de `$p` variabele.

De derde opdracht maakt gebruik van de methode GetOwner om de eigenaar van het proces op te halen `$p` . De uitvoer laat zien dat de eigenaar Domain01\user01. is

### Voor beeld 9: een automatische variabele gebruiken om het proces te identificeren dat als host fungeert voor de huidige sessie

```powershell
Get-Process powershell
```

```Output
Handles  NPM(K)    PM(K)      WS(K) VM(M)   CPU(s)     Id ProcessName
-------  ------    -----      ----- -----   ------     -- -----------
308      26        52308      61780   567     3.18   5632 powershell
377      26        62676      63384   575     3.88   5888 powershell
```

```powershell
Get-Process -Id $PID
```

```Output
Handles  NPM(K)    PM(K)      WS(K) VM(M)   CPU(s)     Id ProcessName
-------  ------    -----      ----- -----   ------     -- -----------
396      26        56488      57236   575     3.90   5888 powershell
```

Deze opdrachten laten zien hoe u de `$PID` Automatische variabele gebruikt om het proces te identificeren dat als host fungeert voor de huidige Power shell-sessie. U kunt deze methode gebruiken om het hostproces te onderscheiden van andere Power shell-processen die u mogelijk wilt stoppen of sluiten.

Met de eerste opdracht worden alle Power shell-processen in de huidige sessie opgehaald.

Met de tweede opdracht wordt het Power Shell-proces opgehaald dat als host fungeert voor de huidige sessie.

### Voor beeld 10: alle processen met een hoofd venster titel ophalen en weer geven in een tabel

```powershell
Get-Process | Where-Object {$_.mainWindowTitle} | Format-Table Id, Name, mainWindowtitle -AutoSize
```

Met deze opdracht worden alle processen opgehaald die een hoofd venster titel hebben en worden deze weer gegeven in een tabel met de proces-ID en de proces naam.

De eigenschap **mainWindowTitle** is slechts een van de vele handige eigenschappen van het **proces** object dat `Get-Process` retourneert. Als u alle eigenschappen wilt weer geven, pipet u de resultaten van een `Get-Process` opdracht naar de `Get-Member` cmdlet `Get-Process | Get-Member` .

## PARAMETERS

### -ComputerName

Hiermee geeft u de computers op waarvoor deze cmdlet actieve processen ontvangt. Standaard is dit de lokale computer.

Typ de NetBIOS-naam, een IP-adres of een Fully Qualified Domain Name (FQDN) van een of meer computers. Als u de lokale computer wilt opgeven, typt u de naam van de computer, een punt (.) of localhost.

Deze para meter is niet gebaseerd op externe communicatie met Windows Power shell. U kunt de para meter **ComputerName** van deze cmdlet zelfs gebruiken als uw computer niet is geconfigureerd om externe opdrachten uit te voeren.

```yaml
Type: System.String[]
Parameter Sets: Name, Id, InputObject
Aliases: Cn

Required: False
Position: Named
Default value: Local computer
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -FileVersionInfo

Geeft aan dat met deze cmdlet de informatie over de bestands versie wordt opgehaald voor het programma dat in het proces wordt uitgevoerd.

In Windows Vista en latere versies van Windows moet u Power shell openen met de optie als administrator uitvoeren om deze para meter te gebruiken voor processen waarvan u geen eigenaar bent.

U kunt de para meters **FileVersionInfo** en **ComputerName** van de `Get-Process` cmdlet niet gebruiken in dezelfde opdracht.

Als u informatie over de bestands versie wilt ophalen voor een proces op een externe computer, gebruikt u de `Invoke-Command` cmdlet.

Het gebruik van deze para meter komt overeen met het ophalen van de eigenschap **MainModule. FileVersionInfo** van elk proces object. Wanneer u deze para meter gebruikt, `Get-Process` retourneert een **FileVersionInfo** -object **System. Diagnostics. FileVersionInfo** , geen process-object. U kunt de uitvoer van de opdracht dus niet door sluizen naar een cmdlet die een proces object verwacht, zoals `Stop-Process` .

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: Name, Id, InputObject
Aliases: FV, FVI

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### -Id

Hiermee geeft u een of meer processen op proces-ID (PID). Als u meerdere Id's wilt opgeven, gebruikt u komma's om de Id's van elkaar te scheiden. Als u de PID van een proces wilt vinden, typt u `Get-Process` .

```yaml
Type: System.Int32[]
Parameter Sets: IdWithUserName, Id
Aliases: PID

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -IncludeUserName

Geeft aan dat de waarde van de gebruikers naam van het **proces** object wordt geretourneerd met de resultaten van de opdracht.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: NameWithUserName, IdWithUserName, InputObjectWithUserName
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Input object

Hiermee geeft u een of meer proces objecten op. Voer een variabele in die de objecten bevat, of typ een opdracht of expressie waarmee de objecten worden opgehaald.

```yaml
Type: System.Diagnostics.Process[]
Parameter Sets: InputObjectWithUserName, InputObject
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### -Module

Geeft aan dat met deze cmdlet de modules worden opgehaald die zijn geladen door de processen.

In Windows Vista en latere versies van Windows moet u Power shell openen met de optie **als administrator uitvoeren** om deze para meter te gebruiken voor processen waarvan u geen eigenaar bent.

Gebruik de cmdlet om de modules op te halen die zijn geladen door een proces op een externe computer `Invoke-Command` .

Deze para meter is gelijk aan het ophalen van de eigenschap **modules** van elk proces object. Wanneer u deze para meter gebruikt, retourneert deze cmdlet een **ProcessModule** -object **System. Diagnostics. ProcessModule** , geen process-object. U kunt de uitvoer van de opdracht dus niet door sluizen naar een cmdlet die een proces object verwacht, zoals `Stop-Process` .

Wanneer u zowel de *module* -als de **FileVersionInfo** -para meters in dezelfde opdracht gebruikt, retourneert deze cmdlet een **FileVersionInfo** -object met informatie over de bestands versie van alle modules.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: Name, Id, InputObject
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### -Name

Hiermee geeft u een of meer processen op proces naam. U kunt meerdere proces namen typen (gescheiden door komma's) en Joker tekens gebruiken. De parameter naam ("naam") is optioneel.

```yaml
Type: System.String[]
Parameter Sets: Name, NameWithUserName
Aliases: ProcessName

Required: False
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: True
```

### CommonParameters

Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable. Zie [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md)voor meer informatie.

## INVOER

### System. Diagnostics. process

U kunt een proces object door sluizen naar deze cmdlet.

## UITVOER

### System. Diagnostics. proces, System. Diagnostics. FileVersionInfo, System. Diagnostics. ProcessModule

Met deze cmdlet wordt standaard een **System. Diagnostics. process** -object geretourneerd. Als u de para meter **FileVersionInfo** gebruikt, wordt een **System. Diagnostics. FileVersionInfo** -object geretourneerd. Als u de **module** parameter gebruikt zonder de para meter **FileVersionInfo** , wordt er een **System. Diagnostics. ProcessModule** -object geretourneerd.

## OPMERKINGEN

- U kunt ook naar deze cmdlet verwijzen door de ingebouwde aliassen ps en GPS te gebruiken. Zie [about_Aliases](../Microsoft.PowerShell.Core/About/about_Aliases.md)voor meer informatie.
- Op computers waarop een 64-bits versie van Windows wordt uitgevoerd, worden door de 64-bits versie van Power shell alleen de 64-bits proces modules en de 32-bits versie van Power shell alleen 32-bits proces modules opgehaald.
- U kunt de eigenschappen en methoden van het Windows Management Instrumentation (WMI) Win32_Process-object in Power shell gebruiken. Zie `Get-WmiObject` en de WMI-SDK voor meer informatie.
- De standaard weergave van een proces is een tabel die de volgende kolommen bevat. Zie [Eigenschappen](/dotnet/api/system.diagnostics.process)van het proces voor een beschrijving van alle eigenschappen van proces objecten.
  - Handgrepen: het aantal ingangen dat het proces heeft geopend.
  - NPM (K): de hoeveelheid niet-wisselbaar geheugen die door het proces wordt gebruikt, in kilo bytes.
  - PM (K): de hoeveelheid wisselbaar geheugen die door het proces wordt gebruikt, in kilo bytes.
  - WS (K): de grootte van de werkset van het proces, in kilo bytes.
    De werkset bestaat uit de geheugen pagina's waarnaar recent werd verwezen door het proces.
  - VM (M): de hoeveelheid virtueel geheugen die door het proces wordt gebruikt, in mega bytes.
    Virtueel geheugen bevat opslag in de Wissel bestanden op schijf.
  - CPU ('s): de hoeveelheid processor tijd die het proces heeft gebruikt op alle processors, in seconden.
  - ID: de proces-ID (PID) van het proces.
  - Verwerker: de naam van het proces. Zie de woorden lijst in Help en ondersteuning en de Help voor taak beheer voor uitleg van de concepten die betrekking hebben op processen.
- U kunt ook de ingebouwde alternatieve weer gaven van de beschik bare processen gebruiken `Format-Table` , zoals **StartTime** en **prioriteit** , en u kunt uw eigen weer gaven ontwerpen.

## GERELATEERDE KOPPELINGEN

[Debug-proces](Debug-Process.md)

[Get-Process](Get-Process.md)

[Start-process](Start-Process.md)

[Stoppen-proces](Stop-Process.md)

[Wacht proces](Wait-Process.md)
