---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 08/19/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/import-csv?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Import-Csv
ms.openlocfilehash: e33da9b461086e85e1fa074b0bed60ac275894b4
ms.sourcegitcommit: 9a8bb1b459b5939c95e1f6d9499fcb13d01a58c4
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 08/25/2020
ms.locfileid: "93251841"
---
# Import-Csv

## SAMENVATTING
Maakt tabel achtige aangepaste objecten van de items in een bestand met door komma's gescheiden waarden (CSV).

## SYNTAXIS

### DelimiterPath (standaard)

```
Import-Csv [[-Delimiter] <Char>] [-Path] <String[]> [-Header <String[]>] [-Encoding <Encoding>]
 [<CommonParameters>]
```

### DelimiterLiteralPath

```
Import-Csv [[-Delimiter] <Char>] -LiteralPath <String[]> [-Header <String[]>] [-Encoding <Encoding>]
 [<CommonParameters>]
```

### CulturePath

```
Import-Csv [-Path] <String[]> -UseCulture [-Header <String[]>] [-Encoding <Encoding>]
 [<CommonParameters>]
```

### CultureLiteralPath

```
Import-Csv -LiteralPath <String[]> -UseCulture [-Header <String[]>] [-Encoding <Encoding>]
 [<CommonParameters>]
```

## BESCHRIJVING

`Import-Csv`Met de cmdlet worden tabel achtige aangepaste objecten gemaakt op basis van de items in CSV-bestanden. Elke kolom in het CSV-bestand wordt een eigenschap van het aangepaste object en de items in rijen worden de eigenschaps waarden. `Import-Csv` werkt in elk CSV-bestand, inclusief bestanden die door de cmdlet worden gegenereerd `Export-Csv` .

U kunt de para meters van de `Import-Csv` cmdlet gebruiken om de rij met kolom koppen en het scheidings teken voor het item op te geven, of rechtstreeks `Import-Csv` om het lijst scheidings teken voor de huidige cultuur als item scheidings teken te gebruiken.

U kunt ook de `ConvertTo-Csv` `ConvertFrom-Csv` cmdlets en gebruiken om objecten te converteren naar CSV-teken reeksen (en terug). Deze cmdlets zijn hetzelfde als de `Export-CSV` `Import-Csv` cmdlets en, behalve dat ze niet omgaan met bestanden.

Als een vermelding in een veldnamenrij in een CSV-bestand een lege of null-waarde bevat, voegt Power shell een standaard naam voor de koprij in en wordt er een waarschuwings bericht weer gegeven.

Vanaf Power shell 6,0 `Import-Csv` ondersteunt nu de uitgebreide W3C-indeling van logboek bestand.

## VOORBEELDEN

### Voor beeld 1: proces objecten importeren

In dit voor beeld ziet u hoe u een CSV-bestand met proces objecten exporteert en importeert.

```powershell
Get-Process | Export-Csv -Path .\Processes.csv
$P = Import-Csv -Path .\Processes.csv
$P | Get-Member
```

```Output
   TypeName: System.Management.Automation.PSCustomObject

Name                       MemberType   Definition
----                       ----------   ----------
Equals                     Method       bool Equals(System.Object obj)
GetHashCode                Method       int GetHashCode()
GetType                    Method       type GetType()
ToString                   Method       string ToString()
BasePriority               NoteProperty string BasePriority=8
Company                    NoteProperty string Company=Microsoft Corporation
...
```

```powershell
$P | Format-Table
```

```Output
Name                   SI Handles VM            WS        PM        NPM    Path
----                   -- ------- --            --        --        ---    ----
ApplicationFrameHost   4  407     2199293489152 15884288  15151104  23792  C:\WINDOWS\system32\ApplicationFrameHost.exe
...
wininit                0  157     2199112204288 4591616   1630208   10376
winlogon               4  233     2199125549056 7659520   2826240   10992  C:\WINDOWS\System32\WinLogon.exe
WinStore.App           4  846     873435136     33652736  26607616  55432  C:\Program Files\WindowsApps\Microsoft.WindowsStore_11712.1001.13.0_x64__8weky...
WmiPrvSE               0  201     2199100219392 8830976   3297280   10632  C:\WINDOWS\system32\wbem\wmiprvse.exe
WmiPrvSE               0  407     2199157727232 18509824  12922880  16624  C:\WINDOWS\system32\wbem\wmiprvse.exe
WUDFHost               0  834     2199310204928 51945472  87441408  24984  C:\Windows\System32\WUDFHost.exe
```

De `Get-Process` cmdlet verzendt proces objecten van de pijp lijn naar de `Export-Csv` . Met de `Export-Csv` cmdlet worden de proces objecten geconverteerd naar CSV-teken reeksen en worden de teken reeksen opgeslagen in het Processes.csv bestand. `Import-Csv`Met de cmdlet worden de CSV-teken reeksen uit het Processes.csv bestand geïmporteerd.
De teken reeksen worden opgeslagen in de `$P` variabele. De `$P` variabele wordt via de pijp lijn naar de `Get-Member` cmdlet verzonden die de eigenschappen van de geïmporteerde CSV-teken reeksen weergeeft. De `$P` variabele wordt vanuit de pijp lijn naar de `Format-Table` cmdlet verzonden en de objecten worden weer gegeven.

### Voor beeld 2: het scheidings teken opgeven

In dit voor beeld ziet u hoe u de para meter **scheidings teken** van de `Import-Csv` cmdlet gebruikt.

```powershell
Get-Process | Export-Csv -Path .\Processes.csv -Delimiter :
$P = Import-Csv -Path .\Processes.csv -Delimiter :
$P | Format-Table
```

`Get-Process`Met de cmdlet worden proces objecten naar beneden verzonden in de pijp lijn `Export-Csv` . Met de `Export-Csv` cmdlet worden de proces objecten geconverteerd naar CSV-teken reeksen en worden de teken reeksen opgeslagen in het Processes.csv bestand.
De para meter **scheidings teken** wordt gebruikt om een scheidings teken voor dubbele punten op te geven. `Import-Csv`Met de cmdlet worden de CSV-teken reeksen uit het Processes.csv bestand geïmporteerd. De teken reeksen worden opgeslagen in de `$P` variabele. `$P`De variabele wordt naar de-cmdlet verzonden via de pijp lijn `Format-Table` .

### Voor beeld 3: de huidige cultuur voor het scheidings teken opgeven

In dit voor beeld ziet u hoe u de `Import-Csv` cmdlet gebruikt met de para meter **UseCulture** .

```powershell
(Get-Culture).TextInfo.ListSeparator
Get-Process | Export-Csv -Path .\Processes.csv -UseCulture
Import-Csv -Path .\Processes.csv -UseCulture
```

De `Get-Culture` cmdlet gebruikt de geneste eigenschappen **Eigenschappen** en **ListSeparator** om het standaard lijst scheidings teken van de huidige cultuur op te halen. `Get-Process`Met de cmdlet worden proces objecten naar beneden verzonden in de pijp lijn `Export-Csv` . Met de `Export-Csv` cmdlet worden de proces objecten geconverteerd naar CSV-teken reeksen en worden de teken reeksen opgeslagen in het Processes.csv bestand. De para meter **UseCulture** maakt gebruik van het standaard lijst scheidings teken van de huidige cultuur. `Import-Csv`Met de cmdlet worden de CSV-teken reeksen uit het Processes.csv bestand geïmporteerd.

### Voor beeld 4: eigenschapnamen van eigenschappen in een geïmporteerd object wijzigen

In dit voor beeld ziet u hoe u de para meter **header** van kunt gebruiken `Import-Csv` om de namen van eigenschappen in het resulterende geïmporteerde object te wijzigen.

```powershell
Start-Job -ScriptBlock { Get-Process } | Export-Csv -Path .\Jobs.csv -NoTypeInformation
$Header = 'State', 'MoreData', 'StatusMessage', 'Location', 'Command', 'StateInfo', 'Finished', 'InstanceId', 'Id', 'Name', 'ChildJobs', 'BeginTime', 'EndTime', 'JobType', 'Output', 'Error', 'Progress', 'Verbose', 'Debug', 'Warning', 'Information'
# Delete the default header from file
$A = Get-Content -Path .\Jobs.csv
$A = $A[1..($A.Count - 1)]
$A | Out-File -FilePath .\Jobs.csv
$J = Import-Csv -Path .\Jobs.csv -Header $Header
$J
```

```Output
State         : Running
MoreData      : True
StatusMessage :
Location      : localhost
Command       : Get-Process
StateInfo     : Running
Finished      : System.Threading.ManualResetEvent
InstanceId    : a259eb63-6824-4b97-a033-305108ae1c2e
Id            : 1
Name          : Job1
ChildJobs     : System.Collections.Generic.List`1[System.Management.Automation.Job]
BeginTime     : 12/20/2018 18:59:57
EndTime       :
JobType       : BackgroundJob
Output        : System.Management.Automation.PSDataCollection`1[System.Management.Automation.PSObject]
Error         : System.Management.Automation.PSDataCollection`1[System.Management.Automation.ErrorRecord]
Progress      : System.Management.Automation.PSDataCollection`1[System.Management.Automation.ProgressRecord]
Verbose       : System.Management.Automation.PSDataCollection`1[System.Management.Automation.VerboseRecord]
Debug         : System.Management.Automation.PSDataCollection`1[System.Management.Automation.DebugRecord]
Warning       : System.Management.Automation.PSDataCollection`1[System.Management.Automation.WarningRecord]
Information   : System.Management.Automation.PSDataCollection`1[System.Management.Automation.InformationRecord]
```

`Start-Job`Met de cmdlet wordt een achtergrond taak gestart die wordt uitgevoerd `Get-Process` . Een taak object wordt vanuit de pijp lijn naar de `Export-Csv` cmdlet verzonden en geconverteerd naar een CSV-teken reeks. Met de para meter **NoTypeInformation** wordt de type-informatie header uit de CSV-uitvoer verwijderd en is deze optioneel in Power shell core.
De `$Header` variabele bevat een aangepaste koptekst waarmee de volgende standaard waarden worden vervangen: **HasMoreData** , **JobStateInfo** , **PSBeginTime** , **PSEndTime** en **PSJobTypeName**. De `$A` variabele gebruikt de `Get-Content` cmdlet om de CSV-teken reeks uit het Jobs.csv-bestand op te halen. De `$A` variabele wordt gebruikt om de standaard header uit het bestand te verwijderen. Met de `Out-File` cmdlet wordt de nieuwe versie van het Jobs.csv bestand in de `$A` variabele opgeslagen. De `Import-Csv` cmdlet importeert het Jobs.csv-bestand en gebruikt de para meter **header** om de variabele toe te passen `$Header` . De `$J` variabele bevat de geïmporteerde **PSCustomObject** en het object wordt weer gegeven in de Power shell-console.

### Voor beeld 5: een aangepast object maken met behulp van een CSV-bestand

In dit voor beeld ziet u hoe u een aangepast object in Power Shell maakt met behulp van een CSV-bestand.

```powershell
Get-Content -Path .\Links.csv
```

```Output
113207,about_Aliases
113208,about_Arithmetic_Operators
113209,about_Arrays
113210,about_Assignment_Operators
113212,about_Automatic_Variables
113213,about_Break
113214,about_Command_Precedence
113215,about_Command_Syntax
144309,about_Comment_Based_Help
113216,about_CommonParameters
113217,about_Comparison_Operators
113218,about_Continue
113219,about_Core_Commands
113220,about_Data_Section
```

```powershell
$A = Import-Csv -Path .\Links.csv -Header 'LinkID', 'TopicTitle'
$A | Get-Member
```

```Output
   TypeName: System.Management.Automation.PSCustomObject

Name        MemberType   Definition
----        ----------   ----------
Equals      Method       bool Equals(System.Object obj)
GetHashCode Method       int GetHashCode()
GetType     Method       type GetType()
ToString    Method       string ToString()
LinkID      NoteProperty string LinkID=113207
TopicTitle  NoteProperty string TopicTitle=about_Aliases
```

```powershell
$A | Where-Object -Property TopicTitle -Like '*alias*'
```

```Output
LinkID TopicTitle
------ ----------
113207 about_Aliases
```

Als u uw Links.csv-bestand wilt maken, gebruikt u de waarden die worden weer gegeven in de `Get-Content` uitvoer.

Met de `Get-Content` cmdlet wordt het Links.csv-bestand weer gegeven. Met de `Import-Csv` cmdlet wordt het Links.csv bestand geïmporteerd. De para meter **header** geeft de eigenschaps namen **LinkId** en **TopicTitle**. De objecten worden opgeslagen in de `$A` variabele. `Get-Member`Met de cmdlet worden de eigenschapnamen van de para meter **header** weer gegeven. De `Where-Object` cmdlet selecteert objecten met de eigenschap **TopicTitle** die **alias** bevat.

### Voor beeld 6: een CSV importeren waarvoor een waarde ontbreekt

In dit voor beeld ziet u hoe de `Import-Csv` cmdlet in Power shell reageert wanneer de koprij in een CSV-bestand een null-waarde of lege waarden bevat. `Import-Csv` vervangt een standaard naam voor de ontbrekende veldnamenrij die de eigenschaps naam wordt van het object dat `Import-Csv` retourneert.

```powershell
Get-Content -Path .\Projects.csv
```

```Output
ProjectID,ProjectName,,Completed
13,Inventory,Redmond,True
440,,FarEast,True
469,Marketing,Europe,False
```

```powershell
Import-Csv -Path .\Projects.csv
```

```Output
WARNING: One or more headers were not specified. Default names starting with "H" have been used in place of any missing headers.

ProjectID ProjectName H1      Completed
--------- ----------- --      ---------
13        Inventory   Redmond True
440                   FarEast True
469       Marketing   Europe  False
```

```powershell
(Import-Csv -Path .\Projects.csv).H1
```

```Output
WARNING: One or more headers were not specified. Default names starting with "H" have been used in place of any missing headers.
Redmond
FarEast
Europe
```

Als u uw Projects.csv-bestand wilt maken, gebruikt u de waarden die worden weer gegeven in de uitvoer van het voor beeld `Get-Content` .

Met de `Get-Content` cmdlet wordt het Projects.csv-bestand weer gegeven. Er ontbreekt een waarde tussen **ProjectName** en **voltooid** voor de rij met koppen. `Import-Csv`Met de cmdlet wordt het Projects.csv bestand geïmporteerd en er wordt een waarschuwings bericht weer gegeven, omdat **H1** een standaard naam voor de header is. `(Import-Csv -Path
.\Projects.csv).H1`Met de opdracht worden de waarden van de eigenschap **H1** opgehaald en wordt een waarschuwing weer gegeven.

## PARAMETERS

### -Scheidings teken

Hiermee geeft u het scheidings teken op waarmee de eigenschaps waarden in het CSV-bestand worden gescheiden.
De standaard waarde is een komma (,).

Voer een teken in, bijvoorbeeld een dubbele punt (:).
Een punt komma (;)) opgeven plaats de invoeg toepassing tussen enkele aanhalings tekens.

Als u in het bestand een ander teken dan het teken voor de werkelijke waarde opgeeft, `Import-Csv` kan de objecten niet maken op basis van de CSV-teken reeksen en worden de CSV-teken reeksen geretourneerd.

```yaml
Type: System.Char
Parameter Sets: DelimiterPath, DelimiterLiteralPath
Aliases:

Required: False
Position: 1
Default value: comma (,)
Accept pipeline input: False
Accept wildcard characters: False
```

### -Encoding

Hiermee geeft u de code ring voor het geïmporteerde CSV-bestand op. De standaardwaarde is `utf8NoBOM`.

De acceptabele waarden voor deze para meter zijn als volgt:

- `ascii`: Gebruikt de code ring voor de ASCII-tekenset (7-bits).
- `bigendianunicode`: Wordt gecodeerd in UTF-16-indeling met behulp van de byte volgorde big endian.
- `bigendianutf32`: Codeert in UTF-32-indeling met behulp van de byte volgorde big endian.
- `oem`: Maakt gebruik van de standaard codering voor MS-DOS-en console Programma's.
- `unicode`: Wordt gecodeerd in UTF-16-indeling met behulp van de byte volgorde little endian.
- `utf7`: Wordt gecodeerd in de indeling UTF-7.
- `utf8`: Wordt gecodeerd in UTF-8-indeling.
- `utf8BOM`: Code ring in UTF-8-indeling met byte order Mark (BOM)
- `utf8NoBOM`: Code ring in UTF-8-indeling zonder byte order Mark (BOM)
- `utf32`: Gecodeerd in UTF-32-indeling.

Vanaf Power shell 6,2 kunnen met de para meter **Encoding** ook numerieke id's van geregistreerde code pagina's (zoals `-Encoding 1251` ) of teken reeks namen van geregistreerde code pagina's (zoals) worden toegestaan `-Encoding "windows-1251"` . Zie de .NET-documentatie voor [code ring. code tabel](/dotnet/api/system.text.encoding.codepage?view=netcore-2.2)voor meer informatie.

> [!NOTE]
> **UTF-7** * wordt niet meer aanbevolen voor gebruik. In Power shell 7,1 wordt een waarschuwing geschreven als u `utf7` voor de para meter **Encoding** opgeeft.

```yaml
Type: System.Text.Encoding
Parameter Sets: (All)
Aliases:
Accepted values: ASCII, BigEndianUnicode, BigEndianUTF32, OEM, Unicode, UTF7, UTF8, UTF8BOM, UTF8NoBOM, UTF32

Required: False
Position: Named
Default value: UTF8NoBOM
Accept pipeline input: False
Accept wildcard characters: False
```

### -Header

Hiermee wordt een rij met een alternatieve kolom koppen opgegeven voor het geïmporteerde bestand. De kolomkop bepaalt de eigenschapnamen van de objecten die zijn gemaakt door `Import-Csv` .

Voer kolom koppen in als een door komma's gescheiden lijst. Plaats de teken reeks van de header niet tussen aanhalings tekens. Plaats elke kolomkop tussen enkele aanhalings tekens.

Als u minder kolom koppen opgeeft dan er gegevens kolommen zijn, worden de resterende gegevens kolommen verwijderd. Als u meer kolom koppen opgeeft dan er gegevens kolommen zijn, worden de aanvullende kolom koppen gemaakt met lege gegevens kolommen.

Wanneer u de para meter **header** gebruikt, verwijdert u de rij met de oorspronkelijke veldnamenrij uit het CSV-bestand. Anders `Import-Csv` wordt er een extra object gemaakt op basis van de items in de rij met koppen.

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -LiteralPath

Hiermee geeft u het pad op naar het CSV-bestand dat moet worden geïmporteerd. In tegens telling tot **Path** wordt de waarde van de para meter **LiteralPath** exact gebruikt wanneer deze wordt getypt. Geen tekens worden geïnterpreteerd als joker tekens. Als het pad escape tekens bevat, plaatst u het tussen enkele aanhalings tekens. Enkele aanhalings tekens geven aan dat Power shell geen karakters interpreteert als escape reeksen.

```yaml
Type: System.String[]
Parameter Sets: DelimiterLiteralPath, CultureLiteralPath
Aliases: PSPath, LP

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -Path

Hiermee geeft u het pad op naar het CSV-bestand dat moet worden geïmporteerd.
U kunt ook een pad naar beleiding van `Import-Csv` .

```yaml
Type: System.String[]
Parameter Sets: DelimiterPath, CulturePath
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### -UseCulture

Maakt gebruik van het lijst scheidings teken voor de huidige cultuur als item scheidings teken. Als u het lijst scheidings teken voor een cultuur wilt zoeken, gebruikt u de volgende opdracht: `(Get-Culture).TextInfo.ListSeparator` .

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: CulturePath, CultureLiteralPath
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### CommonParameters

Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable. Zie [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)voor meer informatie.

## INVOER

### System. String

U kunt een teken reeks met een pad naar door sluizen `Import-Csv` .

## UITVOER

### Object

Met deze cmdlet worden de objecten geretourneerd die worden beschreven door de inhoud in het CSV-bestand.

## OPMERKINGEN

Omdat de geïmporteerde objecten CSV-versies zijn van het object type, worden ze niet herkend en opgemaakt door de Power shell-type-indelings vermeldingen die de niet-CSV-versies van het object type Format teren.

Het resultaat van een `Import-Csv` opdracht is een verzameling teken reeksen die een tabel-achtige aangepast object vormen. Elke rij is een afzonderlijke teken reeks, dus u kunt de eigenschap **Count** van het object gebruiken om de tabel rijen te tellen. De kolommen zijn de eigenschappen van het object en de items in de rijen zijn de eigenschaps waarden.

De rij met kolom koppen bepaalt het aantal kolommen en de kolom namen. De kolom namen zijn ook de namen van de eigenschappen van de objecten. De eerste rij wordt geïnterpreteerd als kolom koppen, tenzij u de para meter **koptekst** gebruikt om kolom koppen op te geven. Als een rij meer waarden heeft dan de rij met koppen, worden de aanvullende waarden genegeerd.

Als er in de rij met kolom koppen een waarde ontbreekt of een null of lege waarde bevat, `Import-Csv` wordt **H** gevolgd door een getal voor de ontbrekende kolomkop en de naam van de eigenschap.

In het CSV-bestand wordt elk object vertegenwoordigd door een door komma's gescheiden lijst van de eigenschaps waarden van het object. De eigenschaps waarden worden geconverteerd naar teken reeksen met behulp van de methode **toString ()** van het object, zodat deze worden weer gegeven met de naam van de eigenschaps waarde. `Export-Csv` exporteert de methoden van het object niet.

`Import-Csv` biedt ook ondersteuning voor de uitgebreide W3C-logboek bestands indeling. Regels die beginnen met `#` worden beschouwd als opmerkingen en worden genegeerd, tenzij de opmerking begint met `#Fields:` en bevat een gescheiden lijst met kolom namen. In dat geval gebruikt de cmdlet die kolom namen. Dit is de standaard indeling voor Windows IIS en andere webserver logboeken. Zie [uitgebreide indeling van logboek bestand](https://www.w3.org/TR/WD-logfile.html)voor meer informatie.

## GERELATEERDE KOPPELINGEN

[ConvertFrom-CSV](ConvertFrom-Csv.md)

[ConvertTo-Csv](ConvertTo-Csv.md)

[Exporteren-CSV](Export-Csv.md)

[Get-cultuur](Get-Culture.md)

