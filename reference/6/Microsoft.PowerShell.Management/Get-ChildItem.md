---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 03/27/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/get-childitem?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-ChildItem
ms.openlocfilehash: 14b1c5d0f37301a5312f37a115f0abc1c7b5990e
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/07/2020
ms.locfileid: "93251026"
---
# Get-ChildItem

## SAMENVATTING

Hiermee worden de items en onderliggende items in een of meer opgegeven locaties opgehaald.

## SYNTAXIS

### Items (standaard)

```
Get-ChildItem [[-Path] <string[]>] [[-Filter] <string>] [-Include <string[]>] [-Exclude <string[]>]
 [-Recurse] [-Depth <uint32>] [-Force] [-Name] [-Attributes <FlagsExpression[FileAttributes]>]
 [-FollowSymlink] [-Directory] [-File] [-Hidden] [-ReadOnly] [-System] [<CommonParameters>]
```

### LiteralItems

```
Get-ChildItem [[-Filter] <string>] -LiteralPath <string[]> [-Include <string[]>]
 [-Exclude <string[]>] [-Recurse] [-Depth <uint32>] [-Force] [-Name]
 [-Attributes <FlagsExpression[FileAttributes]>] [-FollowSymlink] [-Directory] [-File] [-Hidden]
 [-ReadOnly] [-System] [<CommonParameters>]
```

## BESCHRIJVING

De `Get-ChildItem` cmdlet haalt de items op een of meer opgegeven locaties op. Als het item een container is, worden de items in de container opgehaald, ook wel onderliggende items genoemd. U kunt de para meter **recursieve** gebruiken om items in alle onderliggende containers op te halen en de para meter **Depth** gebruiken om het aantal niveaus te beperken dat moet worden herhaald.

`Get-ChildItem` lege mappen worden niet weer gegeven. Wanneer een `Get-ChildItem` opdracht de **diepte** -of **recursieve** para meters bevat, worden lege mappen niet opgenomen in de uitvoer.

Locaties worden blootgesteld aan `Get-ChildItem` door Power shell-providers. Een locatie kan een map van een bestands systeem, een register component of een certificaat archief zijn. Zie [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md)voor meer informatie.

## VOORBEELDEN

### Voor beeld 1: onderliggende items uit een bestandssysteem Directory ophalen

In dit voor beeld worden de onderliggende items uit een map van het bestands systeem opgehaald. De namen van de bestanden en mappen worden weer gegeven. Voor lege locaties retourneert de opdracht geen uitvoer en keert deze terug naar de Power shell-prompt.

De `Get-ChildItem` cmdlet gebruikt de para meter **Path** om de map op te geven `C:\Test` .
`Get-ChildItem` Hiermee worden de bestanden en mappen in de Power shell-console weer gegeven.

```powershell
Get-ChildItem -Path C:\Test
```

```Output
   Directory: C:\Test

Mode                LastWriteTime         Length Name
----                -------------         ------ ----
d-----        2/15/2019     08:29                Logs
-a----        2/13/2019     08:55             26 anotherfile.txt
-a----        2/12/2019     15:40         118014 Command.txt
-a----         2/1/2019     08:43            183 CreateTestFile.ps1
-ar---        2/12/2019     14:31             27 ReadOnlyFile.txt
```

Standaard `Get-ChildItem` worden de modus ( **kenmerken** ), **LastWriteTime** , bestands grootte ( **lengte** ) en de **naam** van het item weer gegeven. De letters in de **modus** eigenschap kunnen als volgt worden geïnterpreteerd:

- `l` gekoppeld
- `d` uitvoermap
- `a` faxberichten
- `r` (alleen-lezen)
- `h` zit
- `s` (systeem).

Zie [about_Filesystem_Provider](../microsoft.powershell.core/about/about_filesystem_provider.md#attributes-flagsexpression)voor meer informatie over de modus vlaggen.

### Voor beeld 2: namen van onderliggende items in een directory ophalen

In dit voor beeld worden alleen de namen van items in een map weer gegeven.

De `Get-ChildItem` cmdlet gebruikt de para meter **Path** om de map op te geven `C:\Test` . De para meter **name** retourneert alleen de namen van bestanden of mappen uit het opgegeven pad.

```powershell
Get-ChildItem -Path C:\Test -Name
```

```Output
Logs
anotherfile.txt
Command.txt
CreateTestFile.ps1
ReadOnlyFile.txt
```

### Voor beeld 3: onderliggende items in de huidige map en submappen ophalen

In dit voor beeld worden **. txt** -bestanden weer gegeven die zich in de huidige map en de submappen ervan bevinden.

```powershell
Get-ChildItem -Path C:\Test\*.txt -Recurse -Force
```

```Output
    Directory: C:\Test\Logs\Adirectory

Mode                LastWriteTime         Length Name
----                -------------         ------ ----
-a----        2/12/2019     16:16             20 Afile4.txt
-a-h--        2/12/2019     15:52             22 hiddenfile.txt
-a----        2/13/2019     13:26             20 LogFile4.txt

    Directory: C:\Test\Logs\Backup

Mode                LastWriteTime         Length Name
----                -------------         ------ ----
-a----        2/12/2019     16:16             20 ATextFile.txt
-a----        2/12/2019     15:50             20 LogFile3.txt

    Directory: C:\Test\Logs

Mode                LastWriteTime         Length Name
----                -------------         ------ ----
-a----        2/12/2019     16:16             20 Afile.txt
-a-h--        2/12/2019     15:52             22 hiddenfile.txt
-a----        2/13/2019     13:26             20 LogFile1.txt

    Directory: C:\Test

Mode                LastWriteTime         Length Name
----                -------------         ------ ----
-a----        2/13/2019     08:55             26 anotherfile.txt
-a----        2/12/2019     15:40         118014 Command.txt
-a-h--        2/12/2019     15:52             22 hiddenfile.txt
-ar---        2/12/2019     14:31             27 ReadOnlyFile.txt
```

De `Get-ChildItem` cmdlet gebruikt de para meter **Path** om op te geven `C:\Test\*.txt` . **Pad** gebruikt het sterretje ( `*` )-Joker teken om alle bestanden met de bestandsnaam extensie op te geven `.txt` . De **recursieve** para meter zoekt in de map **pad** de submappen, zoals wordt weer gegeven in de **map:** koppen. Met de para meter **Force** worden verborgen bestanden weer gegeven, zoals `hiddenfile.txt` een modus van **h**.

### Voor beeld 4: onderliggende items ophalen met behulp van de para meter include

In dit voor beeld `Get-ChildItem` wordt de para meter **include** gebruikt om specifieke items te zoeken in de map die is opgegeven door de para meter **Path** .

```powershell
# When using the -Include parameter, if you don't include an asterisk in the path
# the command returns no output.
Get-ChildItem -Path C:\Test\ -Include *.txt
```

```Output

```

```powershell
Get-ChildItem -Path C:\Test\* -Include *.txt
```

```Output
    Directory: C:\Test

Mode                LastWriteTime         Length Name
----                -------------         ------ ----
-a----        2/13/2019     08:55             26 anotherfile.txt
-a----        2/12/2019     15:40         118014 Command.txt
-ar---        2/12/2019     14:31             27 ReadOnlyFile.txt
```

De `Get-ChildItem` cmdlet gebruikt de para meter **Path** om de map **C:\Test** op te geven. De para meter **Path** bevat een asterisk ( `*` ) met het Joker teken () om de inhoud van de map op te geven.
De para meter **include** maakt gebruik van een asterisk ( `*` ) als Joker teken om alle bestanden met de bestandsnaam extensie **. txt** op te geven.

Wanneer de para meter **include** wordt gebruikt, moet de para meter **Path** een asterisk () met een sterretje ( `*` ) gebruiken om de inhoud van de map op te geven. Bijvoorbeeld `-Path C:\Test\*`.

- Als de **recursie** -para meter wordt toegevoegd aan de opdracht, is de afsluitende asterisk ( `*` ) in de para meter **Path** optioneel. De **recursie** -para meter haalt items op uit de map **pad** en de bijbehorende submappen. bijvoorbeeld `-Path C:\Test\ -Recurse -Include *.txt`
- Als een eindigend sterretje ( `*` ) niet is opgenomen in de para meter **Path** , retourneert de opdracht geen uitvoer en keert deze terug naar de Power shell-prompt. Bijvoorbeeld `-Path C:\Test\`.

### Voor beeld 5: onderliggende items ophalen met de para meter exclude

In de uitvoer van het voor beeld ziet u de inhoud van de map **C:\Test\Logs**. De uitvoer is een verwijzing naar de andere opdrachten die gebruikmaken van de para meters **exclude** en **recursief** .

```powershell
Get-ChildItem -Path C:\Test\Logs
```

```Output
    Directory: C:\Test\Logs

Mode                LastWriteTime         Length Name
----                -------------         ------ ----
d-----        2/15/2019     13:21                Adirectory
d-----        2/15/2019     08:28                AnEmptyDirectory
d-----        2/15/2019     13:21                Backup
-a----        2/12/2019     16:16             20 Afile.txt
-a----        2/13/2019     13:26             20 LogFile1.txt
-a----        2/12/2019     16:24             23 systemlog1.log
```

```powershell
Get-ChildItem -Path C:\Test\Logs\* -Exclude A*
```

```Output
    Directory: C:\Test\Logs

Mode                LastWriteTime         Length Name
----                -------------         ------ ----
d-----        2/15/2019     13:21                Backup
-a----        2/13/2019     13:26             20 LogFile1.txt
-a----        2/12/2019     16:24             23 systemlog1.log
```

De `Get-ChildItem` cmdlet gebruikt de para meter **Path** om de map op te geven `C:\Test\Logs` .
De para meter **exclude** maakt gebruik `*` van het Joker teken sterretje () om op te geven welke bestanden of mappen die met **een** of **een** beginnen, worden uitgesloten van de uitvoer.

Wanneer de **exclude** -para meter wordt gebruikt, is een sterretje ( `*` ) in de para meter **Path** optioneel. Bijvoorbeeld `-Path C:\Test\Logs` of `-Path C:\Test\Logs\*`.

- Als een eindigend sterretje ( `*` ) niet is opgenomen in de para meter **Path** , wordt de inhoud van de para meter **Path** weer gegeven. De uitzonde ringen zijn bestands namen of mapnamen die overeenkomen met de waarde van de para meter **exclude** .
- Als een eindigend sterretje ( `*` ) wordt opgenomen in de para meter **Path** , wordt de opdracht herhaald in de para meters van het **pad** . De uitzonde ringen zijn bestands namen of mapnamen die overeenkomen met de waarde van de para meter **exclude** .
- Als de **recursie** -para meter wordt toegevoegd aan de opdracht, is de uitvoer van de recursie hetzelfde, ongeacht of de para meter **Path** een afsluitend sterretje ( `*` ) bevat.

### Voor beeld 6: de register sleutels ophalen uit een register component

In dit voor beeld worden alle register sleutels opgehaald uit `HKEY_LOCAL_MACHINE\HARDWARE` .

`Get-ChildItem` maakt gebruik van de para meter **Path** om de register sleutel op te geven `HKLM:\HARDWARE` . Het pad en het hoogste niveau van register sleutels van de Hive worden weer gegeven in de Power shell-console.

Zie [about_Registry_Provider](../Microsoft.PowerShell.Core/About/about_Registry_Provider.md)voor meer informatie.

```powershell
Get-ChildItem -Path HKLM:\HARDWARE
```

```Output
    Hive: HKEY_LOCAL_MACHINE\HARDWARE

Name             Property
----             --------
ACPI
DESCRIPTION
DEVICEMAP
RESOURCEMAP
UEFI
```

```powershell
Get-ChildItem -Path HKLM:\HARDWARE -Exclude D*
```

```Output
   Hive: HKEY_LOCAL_MACHINE\HARDWARE

Name                           Property
----                           --------
ACPI
RESOURCEMAP
```

Met de eerste opdracht wordt de inhoud van de `HKLM:\HARDWARE` register sleutel weer gegeven. De **exclude** -para meter geeft `Get-ChildItem` aan dat er geen subsleutels worden geretourneerd die beginnen met `D*` . Op dit moment werkt de **exclude** -para meter alleen voor subsleutels, niet voor item eigenschappen.

### Voor beeld 7: alle certificaten ophalen met de instantie voor ondertekening van programma code

In dit voor beeld wordt elk certificaat opgehaald uit het Power shell- **certificaat:** station met instantie voor ondertekening van programma code.

De `Get-ChildItem` cmdlet gebruikt de para meter **Path** om het **certificaat:** provider op te geven. De **recursieve** para meter doorzoekt de map die is opgegeven door het **pad** en de bijbehorende submappen. Met de para meter **CodeSigningCert** worden alleen certificaten opgehaald die instantie voor ondertekening van programma code hebben.

```powershell
Get-ChildItem -Path Cert:\* -Recurse -CodeSigningCert
```

Zie [about_Certificate_Provider](../Microsoft.PowerShell.Security/About/about_Certificate_Provider.md)voor meer informatie over de certificaat provider en het certificaat: station.

### Voor beeld 8: items ophalen met de para meter Depth

In dit voor beeld worden de items in een map en de bijbehorende submappen weer gegeven. De **Depth** -para meter bepaalt het aantal niveaus van de submap dat moet worden meegenomen in de recursie. Lege mappen worden uitgesloten van de uitvoer.

```powershell
Get-ChildItem -Path C:\Parent -Depth 2
```

```Output
    Directory: C:\Parent

Mode                LastWriteTime         Length Name
----                -------------         ------ ----
d-----        2/14/2019     10:24                SubDir_Level1
-a----        2/13/2019     08:55             26 file.txt

    Directory: C:\Parent\SubDir_Level1

Mode                LastWriteTime         Length Name
----                -------------         ------ ----
d-----        2/14/2019     10:24                SubDir_Level2
-a----        2/13/2019     08:55             26 file.txt

    Directory: C:\Parent\SubDir_Level1\SubDir_Level2

Mode                LastWriteTime         Length Name
----                -------------         ------ ----
d-----        2/14/2019     10:22                SubDir_Level3
-a----        2/13/2019     08:55             26 file.txt
```

De `Get-ChildItem` cmdlet gebruikt de para meter **Path** om **C:\Parent** op te geven. Met de **diepte** parameter worden twee niveaus van recursie opgegeven. `Get-ChildItem` geeft de inhoud weer van de map die is opgegeven door de para meter **Path** en de twee niveaus van submappen.

### Voor beeld 9: informatie over vaste koppeling ophalen

In Power shell 6,2 is een alternatieve weer gave toegevoegd voor het ophalen van harde koppelings informatie.

```powershell
Get-ChildItem -Path C:\PathContainingHardLink | Format-Table -View childrenWithHardLink
```

## Parameters

### -Kenmerken

Hiermee worden bestanden en mappen opgehaald met de opgegeven kenmerken. Deze para meter ondersteunt alle kenmerken en geeft u de mogelijkheid om complexe combi Naties van kenmerken op te geven.

Als u bijvoorbeeld niet-systeem bestanden (niet directory's) wilt ophalen die zijn versleuteld of gecomprimeerd, typt u:

`Get-ChildItem -Attributes !Directory+!System+Encrypted, !Directory+!System+Compressed`

Als u bestanden en mappen met veelgebruikte kenmerken wilt zoeken, gebruikt u de para meter **Attributes** . Of de para meters **map** , **bestand** , **verborgen** , **alleen-lezen** en **systeem**.

De para meter **Attributes** ondersteunt de volgende eigenschappen:

- **Archiveren**
- **Gecomprimeerd**
- **Apparaat**
- **Directory**
- **Versleuteld**
- **Verborgen**
- **IntegrityStream**
- **Normaal**
- **NoScrubData**
- **NotContentIndexed**
- **Offline**
- **Kenmerk**
- **ReparsePoint**
- **SparseFile**
- **Systeem**
- **Tijdelijk**

Zie de [FileAttributes-inventarisatie](/dotnet/api/system.io.fileattributes)voor een beschrijving van deze kenmerken.

Als u kenmerken wilt combi neren, gebruikt u de volgende Opera tors:

- `!` TEN
- `+` MAAR
- `,` OF

Gebruik geen spaties tussen een operator en het bijbehorende kenmerk. Spaties worden geaccepteerd na komma's.

Voor algemene kenmerken gebruikt u de volgende afkortingen:

- `D` Uitvoermap
- `H` Zit
- `R` (Alleen-lezen)
- `S` Opgehaald

```yaml
Type: System.Management.Automation.FlagsExpression`1[System.IO.FileAttributes]
Parameter Sets: (All)
Aliases:
Accepted values: Archive, Compressed, Device, Directory, Encrypted, Hidden, IntegrityStream, Normal, NoScrubData, NotContentIndexed, Offline, ReadOnly, ReparsePoint, SparseFile, System, Temporary

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Diepte

Deze para meter is toegevoegd in Power shell 5,0 en stelt u in staat om de diepte van recursie te bepalen. `Get-ChildItem`De inhoud van de bovenliggende map wordt standaard weer gegeven. De **Depth** para meter bepaalt het aantal niveaus van de submap die zijn opgenomen in de recursie en geeft de inhoud weer.

U kunt bijvoorbeeld `Depth 2` de para meter **Path** , het eerste niveau van submappen en het tweede niveau van submappen bevatten. Standaard worden mapnamen en bestands namen in de uitvoer opgenomen.

> [!NOTE]
> Op een Windows-computer in Power shell of **cmd.exe** , kunt u een grafische weer gave van een mapstructuur weer geven met de opdracht **tree.com** .

```yaml
Type: System.UInt32
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Directory

Als u een lijst met mappen wilt ophalen, gebruikt u de para meter **Directory** of de para meter **Attributes** met de **Directory** -eigenschap. U kunt de para meter **recursief** gebruiken met **Directory**.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: ad, d

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Uitsluiten

Hiermee geeft u als een teken reeks matrix een eigenschap of eigenschap op die met deze cmdlet wordt uitgesloten van de bewerking.
De waarde van deze para meter komt in aanmerking voor de para meter **Path** . Voer een element of patroon van een pad in, zoals `*.txt` of `A*` . Joker tekens worden geaccepteerd.

Een eindigend sterretje ( `*` ) in de para meter **Path** is optioneel. Bijvoorbeeld `-Path C:\Test\Logs` of `-Path C:\Test\Logs\*`. Als er een sterretje ( `*` ) wordt opgenomen, wordt de opdracht herhaald in de para meters van het **pad** . Zonder sterretje ( `*` ) wordt de inhoud van de para meter **Path** weer gegeven. Meer informatie is opgenomen in voor beeld 5 en de sectie opmerkingen.

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: True
```

### -Bestand

Als u een lijst met bestanden wilt ophalen, gebruikt u de para meter **File** . U kunt de **recursieve** para meter gebruiken met **bestand**.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: af

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Filter

Hiermee geeft u een filter op om de para meter **Path** te kwalificeren. De [File System](../Microsoft.PowerShell.Core/About/about_FileSystem_Provider.md) -provider is de enige geïnstalleerde Power shell-provider die filters ondersteunt. Filters zijn efficiënter dan andere para meters. De provider past filter toe wanneer de cmdlet de objecten ophaalt in plaats van dat Power shell de objecten heeft gefilterd nadat ze zijn opgehaald. De filter teken reeks wordt door gegeven aan de .NET API om bestanden te inventariseren. De API ondersteunt alleen `*` en `?` joker tekens.

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: 1
Default value: None
Accept pipeline input: False
Accept wildcard characters: True
```

### -FollowSymlink

Standaard worden in de `Get-ChildItem` cmdlet symbolische koppelingen weer gegeven naar directory's die zijn gevonden tijdens de recursie, maar worden ze niet meer in deze mappen opgenomen. Gebruik de para meter **FollowSymlink** om te zoeken in de mappen waarin deze symbolische koppelingen zijn gericht. De **FollowSymlink** is een dynamische para meter en wordt alleen ondersteund in de **File System** provider.

Deze para meter is geïntroduceerd in Power shell 6,0.

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

### -Force

Hiermee kan de cmdlet items ophalen die anders niet toegankelijk zijn voor de gebruiker, zoals verborgen of systeem bestanden. De para meter **Force** overschrijft geen beveiligings beperkingen. Implementatie is afhankelijk van providers. Zie [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md)voor meer informatie.

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

### -Verborgen

Als u alleen verborgen items wilt ophalen, gebruikt u de para meter **Hidden** of de para meter **Attributes** met de eigenschap **Hidden** . Standaard worden `Get-ChildItem` verborgen items niet weer gegeven. Gebruik de para meter **Force** om verborgen items te verkrijgen.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: ah, h

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Include

Hiermee wordt een teken reeks matrix opgegeven, een item of items die met deze cmdlet in de bewerking zijn opgenomen. De waarde van deze para meter komt in aanmerking voor de para meter **Path** . Voer een element of patroon van een pad in, zoals `"*.txt"` . Joker tekens zijn toegestaan. De para meter **include** is alleen effectief wanneer de inhoud van een item wordt opgenomen, zoals `C:\Windows\*` , waarbij het Joker teken de inhoud van de `C:\Windows` map bevat.

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: True
```

### -LiteralPath

Hiermee geeft u een pad naar een of meer locaties. De waarde van **LiteralPath** wordt precies zo gebruikt als deze wordt getypt. Geen tekens worden geïnterpreteerd als joker tekens. Als het pad escape tekens bevat, plaatst u het tussen enkele aanhalings tekens. Enkele aanhalings tekens geven aan dat Power shell geen karakters interpreteert als escape reeksen.

Zie [about_Quoting_Rules](../Microsoft.Powershell.Core/About/about_Quoting_Rules.md)voor meer informatie.

```yaml
Type: System.String[]
Parameter Sets: LiteralItems
Aliases: PSPath, LP

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -Name

Hiermee worden alleen de namen van de items in de locatie opgehaald. De uitvoer is een teken reeks object dat via de pijp lijn naar andere opdrachten kan worden verzonden. Joker tekens zijn toegestaan.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: True
```

### -Path

Hiermee geeft u een pad naar een of meer locaties. Joker tekens worden geaccepteerd. De standaard locatie is de huidige map ( `.` ).

```yaml
Type: System.String[]
Parameter Sets: Items
Aliases:

Required: False
Position: 0
Default value: Current directory
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: True
```

### -ReadOnly

Als u alleen-lezen items wilt ophalen, gebruikt u de para meter **ReadOnly** of de **eigenschap para meter kenmerk** **ReadOnly** .

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: ar

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Recursief

Hiermee worden de items in de opgegeven locaties en alle onderliggende items van de locaties opgehaald.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: s

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### -Systeem

Hiermee worden alleen systeem bestanden en mappen opgehaald. Als u alleen systeem bestanden en-mappen wilt ophalen, gebruikt u de para meter **systeem** -of **kenmerk** parameter **systeem** eigenschap.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: as

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### CommonParameters

Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable. Zie [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)voor meer informatie.

## INVOER

### System. String

U kunt een teken reeks met een pad naar door sluizen `Get-ChildItem` .

## UITVOER

### System. object

Het type van het object dat `Get-ChildItem` retourneert, wordt bepaald door de objecten in het pad van de provider-schijf.

### System. String

Als u de para meter **name** gebruikt, `Get-ChildItem` retourneert de object namen als teken reeksen.

## OPMERKINGEN

- `Get-ChildItem` kan worden uitgevoerd met een van de ingebouwde aliassen, `ls` , `dir` en `gci` . Zie [about_Aliases](../Microsoft.PowerShell.Core/About/about_Aliases.md)voor meer informatie.
- `Get-ChildItem` Standaard worden verborgen items niet weer gegeven. Als u verborgen items wilt ophalen, gebruikt u de para meter **Forces** .
- De `Get-ChildItem` cmdlet is ontworpen om te werken met de gegevens die door elke provider worden weer gegeven. Als u een lijst wilt weer geven van de providers die beschikbaar zijn in uw sessie, typt u `Get-PSProvider` .
  Zie [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md)voor meer informatie.

## GERELATEERDE KOPPELINGEN

[about_Certificate_Provider](../Microsoft.PowerShell.Security/About/about_Certificate_Provider.md)

[about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md)

[about_Quoting_Rules](../Microsoft.Powershell.Core/About/about_Quoting_Rules.md)

[about_Registry_Provider](../Microsoft.PowerShell.Core/About/about_Registry_Provider.md)

[ForEach-object](../Microsoft.PowerShell.Core/ForEach-Object.md)

[Get-alias](../Microsoft.PowerShell.Utility/Get-Alias.md)

[Get-item](Get-Item.md)

[Get-locatie](Get-Location.md)

[Get-Process](Get-Process.md)

[Get-PSProvider](Get-PSProvider.md)

[Split-pad](Split-Path.md)
