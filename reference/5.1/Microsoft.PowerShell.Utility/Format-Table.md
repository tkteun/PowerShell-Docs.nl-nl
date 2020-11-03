---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 08/10/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/format-table?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Format-Table
ms.openlocfilehash: 4880e4adc9b4ebc339eb44a114e8e6d8bea398a6
ms.sourcegitcommit: 9a6b6714ded4edb5119f1b82a253608018ea6b98
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 08/10/2020
ms.locfileid: "93251739"
---
# Format-Table

## SAMENVATTING
Hiermee wordt de uitvoer als een tabel opgemaakt.

## SYNTAXIS

### Alles

```
Format-Table [-AutoSize] [-RepeatHeader] [-HideTableHeaders] [-Wrap] [[-Property] <Object[]>]
 [-GroupBy <Object>] [-View <String>] [-ShowError] [-DisplayError] [-Force] [-Expand <String>]
 [-InputObject <PSObject>] [<CommonParameters>]
```

## BESCHRIJVING

`Format-Table`Met de cmdlet wordt de uitvoer van een opdracht opgemaakt als een tabel met de geselecteerde eigenschappen van het object in elke kolom. Het object type bepaalt de standaard indeling en eigenschappen die in elke kolom worden weer gegeven. U kunt de **eigenschap** para meter gebruiken om de eigenschappen te selecteren die u wilt weer geven.

Power shell gebruikt standaard formatteringen om te definiëren hoe object typen worden weer gegeven. U kunt `.ps1xml` bestanden gebruiken om aangepaste weer gaven te maken waarin een uitvoer tabel met opgegeven eigenschappen wordt weer gegeven. Nadat een aangepaste weer gave is gemaakt, gebruikt u de para meter **weer geven** om de tabel weer te geven met uw aangepaste weer gave. Zie voor meer informatie over weer gaven [about_Format.ps1XML](../Microsoft.PowerShell.Core/About/about_Format.ps1xml.md).

U kunt een hash-tabel gebruiken om berekende eigenschappen toe te voegen aan een object voordat dit wordt weer gegeven en om de kolom koppen in de tabel op te geven. Als u een berekende eigenschap wilt toevoegen, gebruikt u de **eigenschap** of **GroupBy** -para meter. Zie [about_Hash_Tables](../Microsoft.PowerShell.Core/About/about_Hash_Tables.md)voor meer informatie over hash-tabellen.

## VOORBEELDEN

### Voor beeld 1: Power shell-host Format teren

In dit voor beeld wordt informatie weer gegeven over het hostprogramma voor Power shell in een tabel.

```powershell
Get-Host | Format-Table -AutoSize
```

De `Get-Host` cmdlet krijgt **System. Management. Automation. internal. host. InternalHost** -objecten die de host vertegenwoordigen. De objecten worden naar de pijp lijn verzonden naar `Format-Table` en weer gegeven in een tabel. Met de para meter **AutoSize** worden de kolom breedten aangepast om de afkap ping te minimaliseren.

### Voor beeld 2: processen opmaken op BasePriority

In dit voor beeld worden processen weer gegeven in groepen met dezelfde **BasePriority** -eigenschap.

```powershell
Get-Process | Sort-Object -Property BasePriority | Format-Table -GroupBy BasePriority -Wrap
```

De `Get-Process` cmdlet haalt objecten op die elk proces op de computer vertegenwoordigen en verzendt deze naar de pijp lijn naar beneden `Sort-Object` . De objecten worden gesorteerd in de volg orde van hun **BasePriority** eigenschap.

De gesorteerde objecten worden naar de pijp lijn verzonden `Format-Table` . De para meter **GroupBy** rangschikt de proces gegevens in groepen op basis van de waarde van de eigenschap **BasePriority** . De **Terugloop** parameter zorgt ervoor dat de gegevens niet worden afgekapt.

### Voor beeld 3: processen opmaken op begin datum

In dit voor beeld wordt informatie weer gegeven over de processen die op de computer worden uitgevoerd. De objecten worden gesorteerd en `Format-Table` Er wordt een weer gave gebruikt om de objecten te groeperen op basis van de begin datum.

```powershell
Get-Process | Sort-Object StartTime | Format-Table -View StartTime
```

`Get-Process` Hiermee worden de **System. Diagnostics. process** -objecten opgehaald die de processen vertegenwoordigen die worden uitgevoerd op de computer. De objecten worden naar de pijp lijn verzonden naar `Sort-Object` en worden gesorteerd op basis van de eigenschap **StartTime** .

De gesorteerde objecten worden naar de pijp lijn verzonden `Format-Table` . De **weer gave** -para meter geeft u de weer gave van de **StartTime** op die is gedefinieerd in het Power shell- `DotNetTypes.format.ps1xml` bestand voor **System. Diagnostics. process** -objecten. In de weer gave **StartTime** worden de begin tijd van elke processen geconverteerd naar een korte datum en worden vervolgens de processen gegroepeerd op basis van de begin datum.

Het `DotNetTypes.format.ps1xml` bestand bevat een **prioriteits** weergave voor processen. U kunt uw eigen `format.ps1xml` bestanden maken met aangepaste weer gaven.

### Voor beeld 4: een aangepaste weer gave voor tabel uitvoer gebruiken

In dit voor beeld wordt de inhoud van een map weer gegeven in een aangepaste weer gave. De aangepaste weer gave voegt de kolom **CreationTime** toe aan de tabel uitvoer voor **System. io. DirectoryInfo** -en **System. io. file info** -objecten die zijn gemaakt door `Get-ChildItem` .

De aangepaste weer gave in dit voor beeld is gemaakt op basis van de weer gave die in Power shell-bron code is gedefinieerd. Zie [about_Format.ps1XML](../Microsoft.PowerShell.Core/About/about_Format.ps1xml.md#sample-xml-for-a-format-table-custom-view)voor meer informatie over weer gaven en de code die wordt gebruikt om de weer gave van dit voor beeld te maken.

```powershell
Get-ChildItem  -Path C:\Test | Format-Table -View mygciview
```

```Output
    Directory: C:\Test

Mode                LastWriteTime              CreationTime         Length Name
----                -------------              ------------         ------ ----
d-----        11/4/2019     15:54       9/24/2019     15:54                Archives
d-----        8/27/2019     14:22       8/27/2019     14:22                Drawings
d-----       10/23/2019     09:38       2/25/2019     09:38                Files
-a----        11/7/2019     11:07       11/7/2019     11:07          11345 Alias.txt
-a----        2/27/2019     15:15       2/27/2019     15:15            258 alias_out.txt
-a----        2/27/2019     15:16       2/27/2019     15:16            258 alias_out2.txt
```

`Get-ChildItem` Hiermee wordt de inhoud van de huidige map opgehaald `C:\Test` . De objecten **System. io. DirectoryInfo** en **System. io. file info** worden via de pijp lijn verzonden.
`Format-Table` gebruikt de **weer gave** -para meter om de aangepaste weergave **mygciview** op te geven die de kolom **CreationTime** bevat.

De standaard `Format-Table` uitvoer voor bevat `Get-ChildItem` niet de kolom **CreationTime** .

### Voor beeld 5: eigenschappen voor tabel uitvoer gebruiken

In dit voor beeld wordt de para meter **Property** gebruikt om alle services van de computer weer te geven in een tabel met twee kolommen waarin de eigenschappen **name** en **DependentServices** worden weer gegeven.

```powershell
Get-Service | Format-Table -Property Name, DependentServices
```

`Get-Service` haalt alle services op de computer op en verzendt de objecten **System. ServiceProcess. ServiceController** omlaag in de pijp lijn. `Format-Table` Hiermee wordt de **eigenschap** para meter gebruikt om op te geven dat de eigenschappen **name** en **DependentServices** in de tabel worden weer gegeven.

**Name** en **DependentServices** zijn twee eigenschappen van het object type. Alle eigenschappen weer geven: `Get-Service | Get-Member -MemberType Properties` .

### Voor beeld 6: een proces opmaken en de uitvoerings tijd berekenen

In dit voor beeld wordt een tabel weer gegeven met de proces naam en de totale uitvoerings tijd voor de **Klad blok** -processen van de lokale computer. De totale uitvoerings tijd wordt berekend door de begin tijd van elk proces van de huidige tijd af te trekken.

```powershell
Get-Process notepad |
  Format-Table ProcessName, @{Label="TotalRunningTime"; Expression={(Get-Date) - $_.StartTime}}
```

```Output
ProcessName TotalRunningTime
----------- ----------------
notepad     03:20:00.2751767
notepad     00:00:16.7710520
```

`Get-Process` Hiermee worden alle **Notepad** -processen van de lokale computer opgehaald en worden de objecten van de pijp lijn omlaag verzonden. `Format-Table` geeft een tabel weer met twee kolommen: **Verwerknaam** , een `Get-Process` eigenschap en **TotalRunningTime** , een berekende eigenschap.

De eigenschap **TotalRunningTime** wordt opgegeven met een hash-tabel met twee sleutels, **Label** en **expressie**. De **Label** sleutel geeft u de naam van de eigenschap op. De **expressie** sleutel geeft de berekening aan. Met de expressie wordt de eigenschap **StartTime** van elk proces object opgehaald en afgetrokken van het resultaat van een `Get-Date` opdracht, waardoor de huidige datum en tijd worden opgehaald.

### Voor beeld 7: Klad blok-processen opmaken

In dit voor beeld wordt gebruikt `Get-CimInstance` om de uitvoerings tijd voor alle **Notepad** -processen op de lokale computer op te halen. U kunt `Get-CimInstance` met de para meter **ComputerName** gebruiken om informatie op te halen van externe computers.

```powershell
$Processes = Get-CimInstance -Class win32_process -Filter "name='notepad.exe'"
$Processes | Format-Table ProcessName, @{ Label = "Total Running Time"; Expression={(Get-Date) - $_.CreationDate}}
```

```Output
ProcessName Total Running Time
----------- ------------------
notepad.exe 03:39:39.6260693
notepad.exe 00:19:56.1376922
```

`Get-CimInstance` Hiermee haalt u exemplaren van de WMI- **Win32_Process** klasse op waarmee alle processen van de lokale computer met de naam **notepad.exe** worden beschreven. De proces objecten worden opgeslagen in de `$Processes` variabele.

De proces objecten in de `$Processes` variabele worden naar beneden verzonden in de pijp lijn naar `Format-Table` , waarin de eigenschap **proces** naam en een nieuwe berekende eigenschap worden weer gegeven, waarbij de **totale uitvoerings tijd** wordt berekend.

De opdracht wijst de naam van de nieuwe berekende eigenschap, de **totale uitvoerings tijd** , toe aan de **Label** sleutel. Het script blok van de **expressie** sleutel berekent hoe lang het proces actief is door de aanmaak datum van de processen af te trekken van de huidige datum. De `Get-Date` cmdlet krijgt de huidige datum. De aanmaak datum wordt afgetrokken van de huidige datum. Het resultaat is de waarde van de **totale uitvoerings tijd**.

### Voor beeld 8: problemen met indelings fouten oplossen

In de volgende voor beelden ziet u de resultaten van het toevoegen van de para meters **Display error** of **show error** met een expressie.

```powershell
Get-Date | Format-Table DayOfWeek,{ $_ / $null } -DisplayError
```

```Output
DayOfWeek  $_ / $null
--------- ------------
Wednesday #ERR
```

```powershell
Get-Date | Format-Table DayOfWeek,{ $_ / $null } -ShowError
```

```Output
DayOfWeek  $_ / $null
--------- ------------
Wednesday
Failed to evaluate expression " $_ / $null ".
    + CategoryInfo          : InvalidArgument: (11/27/2019 12:53:41:PSObject) [], RuntimeException
    + FullyQualifiedErrorId : mshExpressionError
```

## PARAMETERS

### -AutoSize

Geeft aan dat de cmdlet de kolom grootte en het aantal kolommen aanpast op basis van de breedte van de gegevens. De grootte en het aantal van de kolom worden standaard bepaald door de weer gave.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### -Display error

Geeft aan dat de cmdlet fouten weergeeft op de opdracht regel. Deze para meter kan worden gebruikt als hulp bij het opsporen van fout opsporing wanneer u expressies opmaakt in een `Format-Table` opdracht en de expressies moet oplossen.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### -Uitbreiden

Hiermee geeft u de indeling van het verzamelings object en de objecten in de verzameling op. Deze para meter is ontworpen om objecten op te maken die ondersteuning bieden voor de [ICollection](/dotnet/api/system.collections.icollection) -interface ([System. Collections](/dotnet/api/system.collections)). De standaard waarde is **EnumOnly**.
De acceptabele waarden voor deze para meter zijn als volgt:

- **EnumOnly** : Hiermee worden de eigenschappen van de objecten in de verzameling weer gegeven.
- **CoreOnly** : Hiermee worden de eigenschappen van het verzamelings object weer gegeven.
- **Beide** : Hiermee worden de eigenschappen van het verzamelings object en de eigenschappen van objecten in de verzameling weer gegeven.

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:
Accepted values: CoreOnly, EnumOnly, Both

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Force

Geeft aan dat de cmdlet de cmdlet omleidt om alle fout gegevens weer te geven. Gebruik met de para meter **Display error** of **show error** . Wanneer een fout object naar de fout wordt geschreven of stromen weer geven, wordt standaard slechts een deel van de fout informatie weer gegeven.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### -GroupBy

Hiermee geeft u de gesorteerde uitvoer in afzonderlijke tabellen op op basis van een eigenschaps waarde. U kunt bijvoorbeeld **GroupBy** gebruiken om services in afzonderlijke tabellen weer te geven op basis van hun status.

Voer een expressie of een eigenschap in. De para meter **GroupBy** verwacht dat de objecten zijn gesorteerd.
Gebruik de `Sort-Object` cmdlet voor `Format-Table` het groeperen van de objecten.

De waarde van de para meter **GroupBy** kan een nieuwe berekende eigenschap zijn. De berekende eigenschap kan een script blok of een hash-tabel zijn. Geldige sleutel-waardeparen zijn:

- Naam (of label)- `<string>`
- Expressie- `<string>` of `<script block>`
- Tring `<string>`

Zie [about_Calculated_Properties](../Microsoft.PowerShell.Core/About/about_Calculated_Properties.md)voor meer informatie.

```yaml
Type: System.Object
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -HideTableHeaders

De kolom koppen in de tabel worden wegge laten.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### -Input object

Hiermee geeft u de objecten op die moeten worden opgemaakt. Voer een variabele in die de objecten bevat, of typ een opdracht of expressie waarmee de objecten worden opgehaald.

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

Hiermee geeft u de object eigenschappen op die in de weer gave worden weer gegeven en de volg orde waarin ze worden weer gegeven. Typ een of meer eigenschapnamen, gescheiden door komma's, of gebruik een hash-tabel om een berekende eigenschap weer te geven. Joker tekens zijn toegestaan.

Als u deze para meter weglaat, zijn de eigenschappen die worden weer gegeven in de weer gave afhankelijk van de eigenschappen van het eerste object. Als het eerste object bijvoorbeeld **eigenschapa** en **PropertyB** heeft, maar volgende objecten **eigenschapa** , **PropertyB** en **PropertyC** hebben, worden alleen de **eigenschapa** en **PropertyB** teksten weer gegeven.

De **eigenschaps** parameter is optioneel. U kunt de **Eigenschappen** en **weer gave** -para meters niet gebruiken in dezelfde opdracht.

De waarde van de **eigenschaps** parameter kan een nieuwe berekende eigenschap zijn. De berekende eigenschap kan een script blok of een hash-tabel zijn. Geldige sleutel-waardeparen zijn:

- Naam (of label) `<string>`
- Expressie- `<string>` of `<script block>`
- Tring `<string>`
- Breedte: `<int32>` moet groter zijn dan `0`
- Uitlijning-waarde kan `Left` , `Center` of `Right`

Zie [about_Calculated_Properties](../Microsoft.PowerShell.Core/About/about_Calculated_Properties.md)voor meer informatie.

```yaml
Type: System.Object[]
Parameter Sets: (All)
Aliases:

Required: False
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: True
```

### -RepeatHeader

Herhaalt de weer gave van de koptekst van een tabel na elk scherm vol. De herhaalde koptekst is nuttig wanneer de uitvoer wordt gepiped naar een paginerings functie zoals `less` of `more` of paging met een scherm lezer.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### -Show error

Met deze para meter worden fouten verzonden via de pijp lijn. Deze para meter kan worden gebruikt als hulp bij het opsporen van fout opsporing wanneer u expressies opmaakt in een `Format-Table` opdracht en de expressies moet oplossen.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### -Weer geven

In Power shell 5,1 en eerdere versies worden de standaard weergaven gedefinieerd in `*.format.ps1xml` bestanden die zijn opgeslagen in `$PSHOME` .

Met de para meter **weer geven** kunt u een alternatieve notatie of aangepaste weer gave voor de tabel opgeven. U kunt de standaard Power shell-weer gaven gebruiken of aangepaste weer gaven maken. Zie [about_Format.ps1XML](../Microsoft.PowerShell.Core/About/about_Format.ps1xml.md)voor meer informatie over het maken van een aangepaste weer gave.

De alternatieve en aangepaste weer gaven voor de **weergave** parameter moeten de tabel indeling gebruiken, anders `Format-Table` mislukt. Als de weer gave alternatieve een lijst is, gebruikt u de `Format-List` cmdlet. Als de alternatieve weer gave geen lijst of tabel is, gebruikt u de `Format-Custom` cmdlet.

U kunt de **Eigenschappen** en **weer gave** -para meters niet gebruiken in dezelfde opdracht.

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

### -Terugloop

Hiermee wordt tekst weer gegeven die de kolom breedte op de volgende regel overschrijdt. Standaard wordt tekst die de kolom breedte overschrijdt, afgekapt.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

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

U kunt elk object omlaag naar de pijp lijn verzenden `Format-Table` .

## UITVOER

### Micro soft. Power shell. commands. internal. Format

`Format-Table` retourneert de indelings objecten die de tabel vertegenwoordigen.

## OPMERKINGEN

## GERELATEERDE KOPPELINGEN

[about_Calculated_Properties](../Microsoft.PowerShell.Core/About/about_Calculated_Properties.md)

[about_Format.ps1XML](../Microsoft.PowerShell.Core/About/about_Format.ps1xml.md)

[about_Hash_Tables](../Microsoft.PowerShell.Core/About/about_Hash_Tables.md)

[Exporteren-FormatData](Export-FormatData.md)

[Format-Custom](Format-Custom.md)

[Format-Hex](Format-Hex.md)

[Format-List](Format-List.md)

[Format-Wide](Format-Wide.md)

[Get-FormatData](Get-FormatData.md)

[Get-member](Get-Member.md)

[Get-CimInstance](../CimCmdlets/Get-CimInstance.md)

[Update-FormatData](Update-FormatData.md)
