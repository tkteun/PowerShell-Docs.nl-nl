---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 12/18/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/get-item?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-Item
ms.openlocfilehash: d034baf42f064149696f54a198dc97d7ee4e8fe7
ms.sourcegitcommit: bf07cffb2a66dec94bf3576e197090f958701f18
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 12/19/2020
ms.locfileid: "97693084"
---
# Get-Item

## SAMENVATTING
Hiermee wordt het item op de opgegeven locatie opgehaald.

## SYNTAXIS

### Pad (standaard)

```
Get-Item [-Path] <String[]> [-Filter <String>] [-Include <String[]>] [-Exclude <String[]>] [-Force]
 [-Credential <PSCredential>] [-Stream <String[]>] [<CommonParameters>]
```

### LiteralPath

```
Get-Item -LiteralPath <String[]> [-Filter <String>] [-Include <String[]>] [-Exclude <String[]>]
 [-Force] [-Credential <PSCredential>] [-Stream <String[]>] [<CommonParameters>]
```

## BESCHRIJVING

`Get-Item`Met de cmdlet wordt het item op de opgegeven locatie opgehaald. De inhoud van het item op de locatie wordt niet opgehaald, tenzij u een Joker teken ( `*` ) gebruikt om alle inhoud van het item aan te vragen.

Deze cmdlet wordt gebruikt door Power shell-providers om door verschillende typen gegevens archieven te navigeren.

## VOORBEELDEN

### Voor beeld 1: de huidige map ophalen

In dit voor beeld wordt de huidige map opgehaald. De punt ('. ') staat voor het item op de huidige locatie (niet de inhoud).

```powershell
Get-Item .
```

```output
Directory: C:\

Mode                LastWriteTime     Length Name
----                -------------     ------ ----
d----         7/26/2006  10:01 AM            ps-test
```

### Voor beeld 2: alle items in de huidige map ophalen

In dit voor beeld worden alle items in de huidige map opgehaald. Het Joker teken ( `*` ) vertegenwoordigt alle inhoud van het huidige item.

```powershell
Get-Item *
```

```output
Directory: C:\ps-test

Mode                LastWriteTime     Length Name
----                -------------     ------ ----
d----         7/26/2006   9:29 AM            Logs
d----         7/26/2006   9:26 AM            Recs
-a---         7/26/2006   9:28 AM         80 date.csv
-a---         7/26/2006  10:01 AM         30 filenoext
-a---         7/26/2006   9:30 AM      11472 process.doc
-a---         7/14/2006  10:47 AM         30 test.txt
```

### Voor beeld 3: de huidige map van een station ophalen

In dit voor beeld wordt de huidige map van het `C:` station opgehaald. Het opgehaalde object staat alleen voor de map en niet de inhoud ervan.

```powershell
Get-Item C:\
```

### Voor beeld 4: items in het opgegeven station ophalen

In dit voor beeld worden de items in het `C:` station opgehaald. Het Joker teken ( `*` ) vertegenwoordigt alle items in de container, niet alleen de container.

```powershell
Get-Item C:\*
```

Gebruik in Power shell één asterisk ( `*` ) om inhoud op te halen in plaats van de traditionele `*.*` . De indeling wordt letterlijk geïnterpreteerd, waardoor `*.*` er geen mappen of bestands namen worden opgehaald zonder een punt.

### Voor beeld 5: een eigenschap ophalen in de opgegeven map

In dit voor beeld wordt de eigenschap **LastAccessTime** van de `C:\Windows` Directory opgehaald. **LastAccessTime** is slechts één eigenschap van File System directory's. Als u alle eigenschappen van een map wilt weer geven, typt u `(Get-Item <directory-name>) | Get-Member` .

```powershell
(Get-Item C:\Windows).LastAccessTime
```

### Voor beeld 6: de inhoud van een register sleutel weer geven

In dit voor beeld wordt de inhoud van de register sleutel **micro soft. Power shell** weer gegeven. U kunt deze cmdlet gebruiken met de Power shell-register provider om register sleutels en subsleutels op te halen, maar u moet de `Get-ItemProperty` cmdlet gebruiken om de register waarden en-gegevens op te halen.

```powershell
Get-Item HKLM:\Software\Microsoft\Powershell\1\Shellids\Microsoft.Powershell\
```

### Voor beeld 7: items in een directory met een uitsluiting ophalen

In dit voor beeld worden items in de Windows-map met namen die een punt ( `.` ) bevatten, maar niet beginnen met `w*` . Dit voor beeld werkt alleen wanneer het pad een Joker teken ( `*` ) bevat om de inhoud van het item op te geven.

```powershell
Get-Item C:\Windows\*.* -Exclude "w*"
```

### Voor beeld 8: koppelings gegevens ophalen

In Power shell 6,2 is een alternatieve weer gave toegevoegd om koppelings gegevens op te halen. Als u de vaste gegevens wilt ophalen, pipet u de uitvoer naar `Format-Table -View childrenWithHardlink`

```powershell
Get-Item -Path C:\PathWhichIsAHardLink | Format-Table -View childrenWithHardlink
```

### Voor beeld 9: uitvoer voor niet-Windows-besturings systemen

In Power shell 7,1 op UNIX-systemen `Get-Item` biedt de cmdlet UNIX-achtige uitvoer:

```powershell
PS> Get-Item /Users
```

```Output
    Directory: /

UnixMode    User  Group   LastWriteTime      Size  Name
--------    ----  -----   -------------      ----  ----
drwxr-xr-x  root  admin   12/20/2019 11:46   192   Users
```

De nieuwe eigenschappen die nu deel uitmaken van de uitvoer zijn:

- **UnixMode** is de bestands machtigingen die worden weer gegeven op een UNIX-systeem
- De **gebruiker** is de bestands eigenaar
- **Groep** is de eigenaar van de groep
- **Grootte** is de grootte van het bestand of de map zoals deze wordt weer gegeven op een UNIX-systeem

> [!NOTE]
> Deze functie is verplaatst van experimentele naar mainstream in Power shell 7,1.

## PARAMETERS

### -Stream

> [!NOTE]
> Deze para meter is alleen beschikbaar in Windows.

Hiermee wordt de opgegeven alternatieve NTFS-bestands stroom opgehaald uit het bestand. Voer de naam van de stream in. Joker tekens worden ondersteund. Als u alle streams wilt ophalen, gebruikt u een asterisk ( `*` ). Deze para meter is niet geldig voor mappen.

**Stream** is een dynamische para meter die de **File System** provider toevoegt aan de `Get-Item` cmdlet.
Deze para meter werkt alleen op stations met een bestands systeem.

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: No alternate file streams
Accept pipeline input: False
Accept wildcard characters: True
```

### -Credential

> [!NOTE]
> Deze para meter wordt niet ondersteund door providers die zijn geïnstalleerd met Power shell.
> Gebruik [invoke-Command](../Microsoft.PowerShell.Core/Invoke-Command.md)om een andere gebruiker te imiteren of uw referenties te verhogen wanneer u deze cmdlet uitvoert.

```yaml
Type: System.Management.Automation.PSCredential
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: Current user
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -Uitsluiten

Hiermee geeft u als een teken reeks matrix een item of items die met deze cmdlet worden uitgesloten in de bewerking. De waarde van deze para meter komt in aanmerking voor de para meter **Path** . Voer een element of patroon van een pad in, zoals `*.txt` . Joker tekens zijn toegestaan. De **exclude** -para meter is alleen effectief wanneer de inhoud van een item wordt opgenomen, zoals `C:\Windows\*` , waarbij het Joker teken de inhoud van de `C:\Windows` map bevat.

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

### -Filter

Hiermee geeft u een filter op om de para meter **Path** te kwalificeren. De [File System](../Microsoft.PowerShell.Core/About/about_FileSystem_Provider.md) -provider is de enige geïnstalleerde Power shell-provider die filters ondersteunt. Filters zijn efficiënter dan andere para meters. De provider past filter toe wanneer de cmdlet de objecten ophaalt in plaats van dat Power shell de objecten heeft gefilterd nadat ze zijn opgehaald. De filter teken reeks wordt door gegeven aan de .NET API om bestanden te inventariseren. De API ondersteunt alleen `*` en `?` joker tekens.

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: True
```

### -Force

Geeft aan dat met deze cmdlet items worden opgehaald die niet kunnen worden geopend, zoals verborgen items.
De implementatie varieert van provider tot provider. Zie [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md)voor meer informatie. Zelfs met behulp van de para meter **forceren** , kunnen de cmdlet geen beveiligings beperkingen opheffen.

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

### -Include

Hiermee wordt een teken reeks matrix opgegeven, een item of items die met deze cmdlet in de bewerking zijn opgenomen. De waarde van deze para meter komt in aanmerking voor de para meter **Path** . Voer een element of patroon van een pad in, zoals `*.txt` . Joker tekens zijn toegestaan. De para meter **include** is alleen effectief wanneer de inhoud van een item wordt opgenomen, zoals `C:\Windows\*` , waarbij het Joker teken de inhoud van de `C:\Windows` map bevat.

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
Parameter Sets: LiteralPath
Aliases: PSPath, LP

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -Path

Hiermee geeft u het pad naar een item. Met deze cmdlet wordt het item op de opgegeven locatie opgehaald. Joker tekens zijn toegestaan. Deze para meter is vereist, maar het **pad naar** de parameter naam is optioneel.

Gebruik een punt ( `.` ) om de huidige locatie op te geven. Gebruik het Joker teken ( `*` ) om alle items op de huidige locatie op te geven.

```yaml
Type: System.String[]
Parameter Sets: Path
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: True
```

### CommonParameters

Deze cmdlet biedt ondersteuning voor de algemene para meters: `-Debug` , `-ErrorAction` , `-ErrorVariable` , `-InformationAction` , `-InformationVariable` , `-OutVariable` , `-OutBuffer` , `-PipelineVariable` , `-Verbose` , `-WarningAction` en `-WarningVariable` . Zie [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md)voor meer informatie.

## INVOER

### System. String

U kunt een teken reeks met een pad naar deze cmdlet door sluizen.

## UITVOER

### System. object

Deze cmdlet retourneert de objecten die worden opgehaald. Het type wordt bepaald door het type objecten in het pad.

## OPMERKINGEN

Deze cmdlet heeft geen **recursieve** para meter, omdat alleen een item wordt opgehaald, niet de inhoud ervan.
Als u de inhoud van een item recursief wilt ophalen, gebruikt u `Get-ChildItem` .

Als u door het REGI ster wilt navigeren, gebruikt u deze cmdlet voor het ophalen van register sleutels en de `Get-ItemProperty` om register waarden en-gegevens op te halen. De register waarden worden beschouwd als eigenschappen van de register sleutel.

Deze cmdlet is ontworpen om te werken met de gegevens die door elke provider worden weer gegeven. Als u een lijst wilt weer geven van de providers die beschikbaar zijn in uw sessie, typt u `Get-PsProvider` . Zie [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md)voor meer informatie.

## GERELATEERDE KOPPELINGEN

[Wissen-item](Clear-Item.md)

[Kopie-item](Copy-Item.md)

[Invoke-item](Invoke-Item.md)

[Item verplaatsen](Move-Item.md)

[Nieuw-item](New-Item.md)

[Verwijderen-item](Remove-Item.md)

[Naam wijzigen-item](Rename-Item.md)

[Set-item](Set-Item.md)

[Get-Child item](Get-ChildItem.md)

[Get-item Property](Get-ItemProperty.md)

[Get-PSProvider](Get-PSProvider.md)

[about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md)

