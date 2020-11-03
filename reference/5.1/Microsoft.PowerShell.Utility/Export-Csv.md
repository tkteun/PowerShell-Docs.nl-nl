---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 04/23/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/export-csv?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Export-Csv
ms.openlocfilehash: 5a76f8ec454ad8144f193d8927f913b89a429fec
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/07/2020
ms.locfileid: "93250453"
---
# Export-Csv

## SAMENVATTING
Hiermee worden objecten geconverteerd naar een reeks teken reeksen met door komma's gescheiden waarden (CSV) en worden de teken reeksen opgeslagen in een bestand.

## SYNTAXIS

### Scheidings teken (standaard)

```
Export-Csv [[-Path] <string>] [[-Delimiter] <char>] -InputObject <psobject> [-LiteralPath <string>]
 [-Force] [-NoClobber] [-Encoding <string>] [-Append] [-NoTypeInformation] [-WhatIf] [-Confirm]
 [<CommonParameters>]
```

### UseCulture

```
Export-Csv [[-Path] <string>] -InputObject <psobject> [-LiteralPath <string>] [-Force] [-NoClobber]
 [-Encoding <string>] [-Append] [-UseCulture] [-NoTypeInformation] [-WhatIf] [-Confirm]
 [<CommonParameters>]
```

## BESCHRIJVING

De `Export-CSV` cmdlet maakt een CSV-bestand van de objecten die u verzendt. Elk object is een rij met een door komma's gescheiden lijst van de eigenschaps waarden van het object. U kunt de `Export-CSV` cmdlet gebruiken om werk bladen te maken en gegevens te delen met Program ma's die CSV-bestanden accepteren als invoer.

Maak objecten niet op voordat u ze naar de `Export-CSV` cmdlet verzendt. Als u `Export-CSV` opgemaakte objecten ontvangt, bevat het CSV-bestand de indelings eigenschappen in plaats van de object eigenschappen. Als u alleen geselecteerde eigenschappen van een object wilt exporteren, gebruikt u de `Select-Object` cmdlet.

## VOORBEELDEN

### Voor beeld 1: proces eigenschappen exporteren naar een CSV-bestand

In dit voor beeld worden **proces** objecten met specifieke eigenschappen geselecteerd, worden de objecten geëxporteerd naar een CSV-bestand.

```powershell
Get-Process -Name WmiPrvSE | Select-Object -Property BasePriority,Id,SessionId,WorkingSet |
  Export-Csv -Path .\WmiData.csv -NoTypeInformation
Import-Csv -Path .\WmiData.csv
```

```Output
BasePriority Id    SessionId WorkingSet
------------ --    --------- ----------
8            976   0         20267008
8            2292  0         36786176
8            3816  0         30351360
8            8604  0         15011840
8            10008 0         8830976
8            11764 0         14237696
8            54632 0         9502720
```

`Get-Process`Met de cmdlet worden de **proces** objecten opgehaald. De para meter **name** filtert de uitvoer zo dat alleen de WmiPrvSE-proces objecten worden meegenomen. De proces objecten worden in de pijp lijn naar de `Select-Object` cmdlet verzonden. `Select-Object` gebruikt de para meter **Property** om een subset van eigenschappen van proces objecten te selecteren. De proces objecten worden in de pijp lijn naar de `Export-Csv` cmdlet verzonden. `Export-Csv` Hiermee worden de proces objecten geconverteerd naar een reeks CSV-teken reeksen. De para meter **Path** geeft aan dat het WmiData.csv bestand wordt opgeslagen in de huidige map. De para meter **NoTypeInformation** verwijdert de **#TYPE** informatie uit de CSV-uitvoer en is niet vereist in Power shell 6. De `Import-Csv` cmdlet gebruikt de para meter **Path** om het bestand weer te geven dat zich in de huidige map bevindt.

### Voor beeld 2: processen exporteren naar een bestand met door komma's gescheiden waarden

In dit voor beeld worden **proces** objecten opgehaald en worden de objecten geëxporteerd naar een CSV-bestand.

```powershell
Get-Process | Export-Csv -Path .\Processes.csv -NoTypeInformation
Get-Content -Path .\Processes.csv
```

```Output
"Name","SI","Handles","VM","WS","PM","NPM","Path","Parent","Company","CPU","FileVersion", ...
"ApplicationFrameHost","4","511","2203597099008","35364864","21979136","30048", ...
```

`Get-Process`Met de cmdlet worden **proces** objecten opgehaald. De proces objecten worden in de pijp lijn naar de `Export-Csv` cmdlet verzonden. `Export-Csv` Hiermee worden de proces objecten geconverteerd naar een reeks CSV-teken reeksen.
De para meter **Path** geeft aan dat het Processes.csv bestand wordt opgeslagen in de huidige map. De para meter **NoTypeInformation** verwijdert de **#TYPE** informatie uit de CSV-uitvoer en is niet vereist in Power shell 6. De `Get-Content` cmdlet gebruikt de para meter **Path** om het bestand weer te geven dat zich in de huidige map bevindt.

### Voor beeld 3: processen exporteren naar een door punt komma's gescheiden bestand

In dit voor beeld worden **proces** objecten opgehaald en worden de objecten geëxporteerd naar een bestand met een punt komma als scheidings teken.

```powershell
Get-Process | Export-Csv -Path .\Processes.csv -Delimiter ';' -NoTypeInformation
Get-Content -Path .\Processes.csv
```

```Output
"Name";"SI";"Handles";"VM";"WS";"PM";"NPM";"Path";"Parent";"Company";"CPU";"FileVersion"; ...
"ApplicationFrameHost";"4";"509";"2203595321344";"34807808";"21770240";"29504"; ...
```

`Get-Process`Met de cmdlet worden **proces** objecten opgehaald. De proces objecten worden in de pijp lijn naar de `Export-Csv` cmdlet verzonden. `Export-Csv` Hiermee worden de proces objecten geconverteerd naar een reeks CSV-teken reeksen.
De para meter **Path** geeft aan dat het Processes.csv bestand wordt opgeslagen in de huidige map. De **scheidings** parameter geeft een punt komma om de teken reeks waarden te scheiden. De para meter **NoTypeInformation** verwijdert de **#TYPE** informatie uit de CSV-uitvoer en is niet vereist in Power shell 6. De `Get-Content` cmdlet gebruikt de para meter **Path** om het bestand weer te geven dat zich in de huidige map bevindt.

### Voor beeld 4: processen exporteren met behulp van het lijst scheidings teken van de huidige cultuur

In dit voor beeld worden **proces** objecten opgehaald en worden de objecten geëxporteerd naar een bestand. Het scheidings teken is het lijst scheidings teken van de huidige cultuur.

```powershell
(Get-Culture).TextInfo.ListSeparator
Get-Process | Export-Csv -Path .\Processes.csv -UseCulture -NoTypeInformation
Get-Content -Path .\Processes.csv
```

```Output
"Name","SI","Handles","VM","WS","PM","NPM","Path","Parent","Company","CPU","FileVersion", ...
"ApplicationFrameHost","4","511","2203597099008","35364864","21979136","30048", ...
```

De `Get-Culture` cmdlet maakt gebruik van de geneste eigenschappen **Eigenschappen** en **ListSeparator** en geeft het standaard lijst scheidings teken van de huidige cultuur weer. `Get-Process`Met de cmdlet worden **proces** objecten opgehaald.
De proces objecten worden in de pijp lijn naar de `Export-Csv` cmdlet verzonden. `Export-Csv` Hiermee worden de proces objecten geconverteerd naar een reeks CSV-teken reeksen. De para meter **Path** geeft aan dat het Processes.csv bestand wordt opgeslagen in de huidige map. De para meter **UseCulture** gebruikt het standaard lijst scheidings teken van de huidige cultuur als scheidings teken. De para meter **NoTypeInformation** verwijdert de **#TYPE** informatie uit de CSV-uitvoer en is niet vereist in Power shell 6. De `Get-Content` cmdlet gebruikt de para meter **Path** om het bestand weer te geven dat zich in de huidige map bevindt.

### Voor beeld 5: processen exporteren met type-informatie

In dit voor beeld wordt uitgelegd hoe u de **#TYPE** header gegevens opneemt in een CSV-bestand. De **#TYPE** header is de standaard waarde in versies voorafgaand aan power shell 6,0.

```powershell
Get-Process | Export-Csv -Path .\Processes.csv
Get-Content -Path .\Processes.csv
```

```Output
#TYPE System.Diagnostics.Process
"Name","SI","Handles","VM","WS","PM","NPM","Path","Company","CPU","FileVersion", ...
"ApplicationFrameHost","4","507","2203595001856","35139584","20934656","29504", ...
```

`Get-Process`Met de cmdlet worden **proces** objecten opgehaald. De proces objecten worden in de pijp lijn naar de `Export-Csv` cmdlet verzonden. `Export-Csv` Hiermee worden de proces objecten geconverteerd naar een reeks CSV-teken reeksen.
De para meter **Path** geeft aan dat het Processes.csv bestand wordt opgeslagen in de huidige map. De `Get-Content` cmdlet gebruikt de para meter **Path** om het bestand weer te geven dat zich in de huidige map bevindt.

### Voor beeld 6: objecten exporteren en toevoegen aan een CSV-bestand

In dit voor beeld wordt beschreven hoe u objecten exporteert naar een CSV-bestand en hoe u de para meter **Append** gebruikt om objecten toe te voegen aan een bestaand bestand.

```powershell
$AppService = (Get-Service -DisplayName *Application* | Select-Object -Property DisplayName, Status)
$AppService | Export-Csv -Path .\Services.Csv -NoTypeInformation
Get-Content -Path .\Services.Csv
$WinService = (Get-Service -DisplayName *Windows* | Select-Object -Property DisplayName, Status)
$WinService | Export-Csv -Path ./Services.csv -NoTypeInformation -Append
Get-Content -Path .\Services.Csv
```

```Output
"DisplayName","Status"
"Application Layer Gateway Service","Stopped"
"Application Identity","Running"
"Windows Audio Endpoint Builder","Running"
"Windows Audio","Running"
"Windows Event Log","Running"
```

`Get-Service`Met de cmdlet worden service objecten opgehaald. De para meter **DisplayName** retourneert services die de Word-toepassing bevatten. De service objecten worden naar de-cmdlet verzonden via de pijp lijn `Select-Object` . `Select-Object` maakt gebruik van de para meter **Property** om de eigenschappen **DisplayName** en **status** op te geven. De `$AppService` variabele slaat de objecten op.

De `$AppService` objecten worden naar de-cmdlet verzonden via de pijp lijn `Export-Csv` . `Export-Csv` Hiermee worden de service objecten geconverteerd naar een reeks CSV-teken reeksen. De para meter **Path** geeft aan dat het Services.csv bestand wordt opgeslagen in de huidige map. De para meter **NoTypeInformation** verwijdert de **#TYPE** informatie uit de CSV-uitvoer en is niet vereist in Power shell 6. De `Get-Content` cmdlet gebruikt de para meter **Path** om het bestand weer te geven dat zich in de huidige map bevindt.

De `Get-Service` `Select-Object` cmdlets en worden herhaald voor services die het woord Windows bevatten. De `$WinService` variabele slaat de service objecten op. De `Export-Csv` cmdlet gebruikt de para meter **Append** om op te geven dat de `$WinService` objecten worden toegevoegd aan het bestaande Services.csv-bestand. De `Get-Content` cmdlet wordt herhaald om het bijgewerkte bestand weer te geven dat de toegevoegde gegevens bevat.

### Voor beeld 7: met de cmdlet Format in een pijp lijn worden onverwachte resultaten gemaakt

In dit voor beeld ziet u waarom het belang rijk is dat u geen indelings-cmdlet kunt gebruiken in een pijp lijn. Als onverwachte uitvoer wordt ontvangen, moet u de pijplijn syntaxis oplossen.

```powershell
Get-Date | Select-Object -Property DateTime, Day, DayOfWeek, DayOfYear |
 Export-Csv -Path .\DateTime.csv -NoTypeInformation
Get-Content -Path .\DateTime.csv
```

```Output
"DateTime","Day","DayOfWeek","DayOfYear"
"Wednesday, January 2, 2019 14:59:34","2","Wednesday","2"
```

```powershell
Get-Date | Format-Table -Property DateTime, Day, DayOfWeek, DayOfYear |
 Export-Csv -Path .\FTDateTime.csv -NoTypeInformation
Get-Content -Path .\FTDateTime.csv
```

```Output
"ClassId2e4f51ef21dd47e99d3c952918aff9cd","pageHeaderEntry","pageFooterEntry","autosizeInfo", ...
"033ecb2bc07a4d43b5ef94ed5a35d280",,,,"Microsoft.PowerShell.Commands.Internal.Format. ...
"9e210fe47d09416682b841769c78b8a3",,,,,
"27c87ef9bbda4f709f6b4002fa4af63c",,,,,
"4ec4f0187cb04f4cb6973460dfe252df",,,,,
"cf522b78d86c486691226b40aa69e95c",,,,,
```

De `Get-Date` cmdlet haalt het **DateTime** -object op. Het object wordt vanuit de pijp lijn naar de `Select-Object` cmdlet verzonden. `Select-Object` gebruikt de para meter **Property** om een subset van object eigenschappen te selecteren. Het object wordt vanuit de pijp lijn naar de `Export-Csv` cmdlet verzonden. `Export-Csv` converteert het object naar een CSV-indeling. De para meter **Path** geeft aan dat het DateTime.csv bestand wordt opgeslagen in de huidige map. De para meter **NoTypeInformation** verwijdert de **#TYPE** informatie uit de CSV-uitvoer en is niet vereist in Power shell 6. De `Get-Content` cmdlet gebruikt de para meter **Path** om het CSV-bestand weer te geven dat zich in de huidige map bevindt.

Wanneer de `Format-Table` cmdlet wordt gebruikt in de pijp lijn om eigenschappen te selecteren, worden er onverwachte resultaten ontvangen. `Format-Table` Hiermee worden de objecten van de tabel indeling naar de-cmdlet van de pijp lijn in `Export-Csv` plaats van het **DateTime** -object verzonden. `Export-Csv` de tabel indelings objecten worden geconverteerd naar een reeks CSV-teken reeksen. `Get-Content`Met de cmdlet wordt het CSV-bestand weer gegeven dat de tabel indelings objecten bevat.

### Voor beeld 8: de para meter Force gebruiken om alleen-lezen bestanden te overschrijven

In dit voor beeld maakt u een leeg bestand met het kenmerk alleen-lezen en gebruikt u de para meter **Force** om het bestand bij te werken.

```powershell
New-Item -Path .\ReadOnly.csv -ItemType File
Set-ItemProperty -Path .\ReadOnly.csv -Name IsReadOnly -Value $true
Get-Process | Export-Csv -Path .\ReadOnly.csv -NoTypeInformation
```

```Output
Export-Csv : Access to the path 'C:\ReadOnly.csv' is denied.
At line:1 char:15
+ Get-Process | Export-Csv -Path .\ReadOnly.csv -NoTypeInformation
+               ~~~~~~~~~~~~~~~~~~~~~~~~
+ CategoryInfo          : OpenError: (:) [Export-Csv], UnauthorizedAccessException
+ FullyQualifiedErrorId : FileOpenFailure,Microsoft.PowerShell.Commands.ExportCsvCommand
```

```powershell
Get-Process | Export-Csv -Path .\ReadOnly.csv -NoTypeInformation -Force
Get-Content -Path .\ReadOnly.csv
```

```Output
"Name";"SI";"Handles";"VM";"WS";"PM";"NPM";"Path";"Parent";"Company";"CPU";"FileVersion"; ...
"ApplicationFrameHost";"4";"509";"2203595321344";"34807808";"21770240";"29504"; ...
```

De `New-Item` cmdlet maakt gebruik van de para meters **Path** en **item** type voor het maken van het ReadOnly.csv-bestand in de huidige map. De `Set-ItemProperty` cmdlet gebruikt de para meters **name** en **Value** om de eigenschap **IsReadOnly** van het bestand te wijzigen in True. `Get-Process`Met de cmdlet worden **proces** objecten opgehaald. De proces objecten worden in de pijp lijn naar de `Export-Csv` cmdlet verzonden. `Export-Csv` Hiermee worden de proces objecten geconverteerd naar een reeks CSV-teken reeksen. De para meter **Path** geeft aan dat het ReadOnly.csv bestand wordt opgeslagen in de huidige map. De para meter **NoTypeInformation** verwijdert de **#TYPE** informatie uit de CSV-uitvoer en is niet vereist in Power shell 6. In de uitvoer ziet u dat het bestand niet is geschreven, omdat de toegang wordt geweigerd.

De para meter **Force** wordt toegevoegd aan de `Export-Csv` cmdlet om de export af te dwingen om naar het bestand te schrijven. De `Get-Content` cmdlet gebruikt de para meter **Path** om het bestand weer te geven dat zich in de huidige map bevindt.

### Voor beeld 9: de para meter Force gebruiken met Append

In dit voor beeld ziet u hoe u de para meters **Force** en **Append** gebruikt. Als deze para meters worden gecombineerd, kunnen niet-overeenkomende object eigenschappen naar een CSV-bestand worden geschreven.

```powershell
$Content = [PSCustomObject]@{Name = 'PowerShell Core'; Version = '6.0'}
$Content | Export-Csv -Path .\ParmFile.csv -NoTypeInformation
$AdditionalContent = [PSCustomObject]@{Name = 'Windows PowerShell'; Edition = 'Desktop'}
$AdditionalContent | Export-Csv -Path .\ParmFile.csv -NoTypeInformation -Append
```

```Output
Export-Csv : Cannot append CSV content to the following file: ParmFile.csv.
The appended object does not have a property that corresponds to the following column:
Version. To continue with mismatched properties, add the -Force parameter, and then retry
 the command.
At line:1 char:22
+ $AdditionalContent | Export-Csv -Path .\ParmFile.csv -NoTypeInformation -Append
+                      ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
+ CategoryInfo          : InvalidData: (Version:String) [Export-Csv], InvalidOperationException
+ FullyQualifiedErrorId : CannotAppendCsvWithMismatchedPropertyNames,Microsoft.PowerShell. ...
```

```powershell
$AdditionalContent | Export-Csv -Path .\ParmFile.csv -NoTypeInformation -Append -Force
Import-Csv -Path .\ParmFile.csv
```

```Output
Name               Version
----               -------
PowerShell Core    6.0
Windows PowerShell
```

Een expressie maakt de **PSCustomObject** met de **naam** en **versie** -eigenschappen. De waarden worden opgeslagen in de `$Content` variabele. De `$Content` variabele wordt via de pijp lijn naar de `Export-Csv` cmdlet verzonden. `Export-Csv` maakt gebruik van de para meter **Path** en slaat het ParmFile.csv-bestand op in de huidige map. De para meter **NoTypeInformation** verwijdert de **#TYPE** informatie uit de CSV-uitvoer en is niet vereist in Power shell 6.

Met een andere expressie maakt u een **PSCustomObject** met de **naam** en **editie** -eigenschappen. De waarden worden opgeslagen in de `$AdditionalContent` variabele. De `$AdditionalContent` variabele wordt via de pijp lijn naar de `Export-Csv` cmdlet verzonden. De **toevoeg** parameter wordt gebruikt om de gegevens aan het bestand toe te voegen. De toevoeg bewerking mislukt omdat de naam van een eigenschap niet overeenkomt met de **versie** en **editie**.

De `Export-Csv` cmdlet **Force** -para meter wordt gebruikt om het exporteren af te dwingen om naar het bestand te schrijven. De **editie** -eigenschap wordt verwijderd. De `Import-Csv` cmdlet gebruikt de para meter **Path** om het bestand weer te geven dat zich in de huidige map bevindt.

## PARAMETERS

### -Toevoegen

Gebruik deze para meter zodat `Export-CSV` CSV-uitvoer aan het einde van het opgegeven bestand wordt toegevoegd. Zonder deze para meter `Export-CSV` vervangt de bestands inhoud zonder waarschuwing.

Deze para meter is geïntroduceerd in Windows Power Shell 3,0.

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

### -Scheidings teken

Hiermee wordt een scheidings teken opgegeven om de eigenschaps waarden van elkaar te scheiden. De standaard waarde is een komma ( `,` ). Voer een teken in, bijvoorbeeld een dubbele punt ( `:` ). Als u een punt komma () wilt opgeven `;` , plaatst u deze tussen aanhalings tekens.

```yaml
Type: System.Char
Parameter Sets: Delimiter
Aliases:

Required: False
Position: 1
Default value: comma (,)
Accept pipeline input: False
Accept wildcard characters: False
```

### -Encoding

Hiermee geeft u het type code ring voor het doel bestand op. De standaardwaarde is `ASCII`.

De acceptabele waarden voor deze para meter zijn als volgt:

- `ASCII` Maakt gebruik van ASCII-tekenset (7-bits).
- `BigEndianUnicode` Maakt gebruik van UTF-16 met de byte volgorde big endian.
- `Default` Gebruikt de code ring die overeenkomt met de actieve code tabel van het systeem (meestal ANSI).
- `OEM` Gebruikt de code ring die overeenkomt met de huidige OEM-code tabel van het systeem.
- `Unicode` Maakt gebruik van UTF-16 met de byte volgorde little endian.
- `UTF7` Maakt gebruik van UTF-7.
- `UTF8` Maakt gebruik van UTF-8.
- `UTF32` Maakt gebruik van UTF-32 met de byte volgorde little endian.

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:
Accepted values: ASCII, BigEndianUnicode, Default, OEM, Unicode, UTF7, UTF8, UTF32

Required: False
Position: Named
Default value: ASCII
Accept pipeline input: False
Accept wildcard characters: False
```

### -Force

Met deze para meter kunt `Export-Csv` u bestanden overschrijven met het kenmerk **alleen-lezen** .

Wanneer **Force** -en **Append** -para meters worden gecombineerd, kunnen objecten die niet-overeenkomende eigenschappen bevatten, naar een CSV-bestand worden geschreven. Alleen de eigenschappen die overeenkomen, worden naar het bestand geschreven. De eigenschappen die niet overeenkomen, worden verwijderd.

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

Geeft aan welke objecten als CSV-teken reeksen moeten worden geëxporteerd. Voer een variabele in die de objecten bevat of typ een opdracht of expressie waarmee de objecten worden opgehaald. U kunt ook objecten pipeen naar `Export-CSV` .

```yaml
Type: System.Management.Automation.PSObject
Parameter Sets: (All)
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### -LiteralPath

Hiermee geeft u het pad naar het CSV-uitvoer bestand. In tegens telling tot **Path** wordt de waarde van de para meter **LiteralPath** exact gebruikt wanneer deze wordt getypt. Geen tekens worden geïnterpreteerd als joker tekens. Als het pad escape-tekens bevat, gebruikt u enkele aanhalings tekens. Enkele aanhalings tekens geven aan dat Power shell geen karakters interpreteert als escape reeksen.

```yaml
Type: System.String
Parameter Sets: (All)
Aliases: PSPath

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -NoClobber

Gebruik deze para meter om `Export-CSV` een bestaand bestand niet te overschrijven. Als het bestand zich in het opgegeven pad bevindt, wordt `Export-CSV` het bestand standaard zonder waarschuwing overschreven.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: NoOverwrite

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -NoTypeInformation

Hiermee verwijdert u de **#TYPE** informatie uit de uitvoer. Deze para meter werd de standaard waarde in Power shell 6,0 en is opgenomen voor achterwaartse compatibiliteit.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: NTI

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Path

Een vereiste para meter waarmee de locatie wordt opgegeven waarop het CSV-uitvoer bestand moet worden opgeslagen.

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -UseCulture

Maakt gebruik van het lijst scheidings teken voor de huidige cultuur als item scheidings teken. Als u het lijst scheidings teken voor een cultuur wilt zoeken, gebruikt u de volgende opdracht: `(Get-Culture).TextInfo.ListSeparator` .

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: UseCulture
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Confirm

Hiermee wordt u gevraagd om bevestiging voordat u de cmdlet uitvoert.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: cf

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### -WhatIf

Hiermee voor komt u dat de cmdlet wordt verwerkt of dat er wijzigingen worden aangebracht. De uitvoer laat zien wat er zou gebeuren als de cmdlet werd uitgevoerd.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: wi

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### CommonParameters

Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable. Zie [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)voor meer informatie.

## INVOER

### System. Management. Automation. PSObject

U kunt elk object met een adapter voor een Extended-type systeem (ETS) aan `Export-CSV` .

## UITVOER

### System. String

De CSV-lijst wordt verzonden naar het bestand dat is opgegeven in de para meter Path.

## OPMERKINGEN

De `Export-CSV` cmdlet converteert de objecten die u verzendt naar een reeks CSV-teken reeksen en slaat deze op in het opgegeven tekst bestand. U kunt gebruiken `Export-CSV` om objecten op te slaan in een CSV-bestand en vervolgens de `Import-Csv` cmdlet te gebruiken om objecten te maken vanuit het CSV-bestand.

In het CSV-bestand wordt elk object vertegenwoordigd door een door komma's gescheiden lijst van de eigenschaps waarden van het object. De eigenschaps waarden worden geconverteerd naar teken reeksen met de methode **toString ()** . De teken reeksen worden vertegenwoordigd door de naam van de eigenschaps waarde. Export-CSV exporteert de methoden van het object niet.

De CSV-teken reeksen worden als volgt uitgevoerd:

- De eerste teken reeks bevat standaard de **#TYPE** informatie header, gevolgd door de volledig gekwalificeerde naam van het object type. Bijvoorbeeld **#TYPE System. Diagnostics. process**.
- Als **NoTypeInformation** wordt gebruikt, bevat de eerste teken reeks de kolom koppen. De headers bevatten de eigenschaps namen van het eerste object als een door komma's gescheiden lijst.
- De resterende teken reeksen bevatten door komma's gescheiden lijsten van de eigenschaps waarden van elk object.

Wanneer u meerdere objecten indient `Export-CSV` , `Export-CSV` organiseert het bestand op basis van de eigenschappen van het eerste object dat u verzendt. Als de resterende objecten niet beschikken over een van de opgegeven eigenschappen, is de eigenschaps waarde van dat object null, zoals wordt weer gegeven in twee opeenvolgende komma's. Als de resterende objecten extra eigenschappen hebben, worden deze eigenschaps waarden niet opgenomen in het bestand.

U kunt de `Import-Csv` cmdlet gebruiken om objecten opnieuw te maken op basis van de CSV-teken reeksen in de bestanden. De resulterende objecten zijn CSV-versies van de oorspronkelijke objecten die bestaan uit teken reeks representaties van de eigenschaps waarden en geen methoden.

Met `ConvertTo-Csv` de `ConvertFrom-Csv` cmdlets en worden objecten GECONVERTEERD naar CSV-teken reeksen en CSV-teken reeksen. `Export-CSV` is hetzelfde als `ConvertTo-CSV` , behalve dat de CSV-teken reeksen worden opgeslagen in een bestand.

## GERELATEERDE KOPPELINGEN

[ConvertFrom-CSV](ConvertFrom-Csv.md)

[ConvertTo-Csv](ConvertTo-Csv.md)

[Format-Table](Format-Table.md)

[Import-Csv](Import-Csv.md)

[Select-Object](Select-Object.md)
