---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 04/19/2021
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/get-item?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-Item
ms.openlocfilehash: 8949f4fed84272b8748f11e312d01134ad630489
ms.sourcegitcommit: 2ad76cd528338f8c2cc10a84c5c56c0e25b93436
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 04/19/2021
ms.locfileid: "107729846"
---
# Get-Item

## SAMENVATTING
Hiermee haalt u het item op de opgegeven locatie.

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

De `Get-Item` cmdlet haalt het item op de opgegeven locatie op. De inhoud van het item wordt niet op de locatie opgevraagd, tenzij u een jokerteken ( ) gebruikt om alle inhoud van het `*` item aan te vragen.

Deze cmdlet wordt gebruikt door PowerShell-providers om door verschillende typen gegevensopslag te navigeren.

## VOORBEELDEN

### Voorbeeld 1: de huidige map op te halen

In dit voorbeeld wordt de huidige map. De punt ('.') vertegenwoordigt het item op de huidige locatie (niet de inhoud ervan).

```powershell
Get-Item .
```

```output
Directory: C:\

Mode                LastWriteTime     Length Name
----                -------------     ------ ----
d----         7/26/2006  10:01 AM            ps-test
```

### Voorbeeld 2: alle items in de huidige map op te halen

In dit voorbeeld worden alle items in de huidige map. Het jokerteken ( `*` ) vertegenwoordigt alle inhoud van het huidige item.

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

### Voorbeeld 3: De huidige map van een station op te halen

In dit voorbeeld wordt de huidige map van het `C:` station. Het object dat wordt opgehaald vertegenwoordigt alleen de map, niet de inhoud ervan.

```powershell
Get-Item C:
```

### Voorbeeld 4: Items in het opgegeven station op halen

In dit voorbeeld worden de items in het `C:` station. Het jokerteken ( `*` ) vertegenwoordigt alle items in de container, niet alleen de container.

```powershell
Get-Item C:\*
```

Gebruik in PowerShell één sterretje () om inhoud op te halen in plaats `*` van de traditionele `*.*` . De indeling wordt letterlijk geïnterpreteerd, zodat er geen map of bestandsnaam zonder `*.*` een punt wordt opgehaald.

### Voorbeeld 5: Een eigenschap in de opgegeven map op te halen

In dit voorbeeld wordt de **eigenschap LastAccessTime** van de `C:\Windows` map . **LastAccessTime** is slechts één eigenschap van bestandssysteemdirecties. Als u alle eigenschappen van een map wilt zien, typt u `(Get-Item <directory-name>) | Get-Member` .

```powershell
(Get-Item C:\Windows).LastAccessTime
```

### Voorbeeld 6: De inhoud van een registersleutel weergeven

In dit voorbeeld ziet u de inhoud van de **Microsoft.PowerShell-registersleutel.** U kunt deze cmdlet gebruiken met de PowerShell-registerprovider om registersleutels en subsleutels op te halen, maar u moet de cmdlet gebruiken om de registerwaarden en -gegevens `Get-ItemProperty` op te halen.

```powershell
Get-Item HKLM:\Software\Microsoft\Powershell\1\Shellids\Microsoft.Powershell\
```

### Voorbeeld 7: Items in een directory met een uitsluiting op halen

In dit voorbeeld worden items in de Windows-map met namen met een punt ( ) , maar `.` niet met . `w*` Dit voorbeeld werkt alleen als het pad een jokerteken ( ) bevat om de inhoud van het `*` item op te geven.

```powershell
Get-Item C:\Windows\*.* -Exclude "w*"
```

### Voorbeeld 8: Hardlink-informatie verkrijgen

In PowerShell 6.2 is een alternatieve weergave toegevoegd om hardlinkgegevens op te halen. Als u de hardlink-informatie wilt op halen, slinkt u de uitvoer door naar `Format-Table -View childrenWithHardlink`

```powershell
Get-Item -Path C:\PathWhichIsAHardLink | Format-Table -View childrenWithHardlink
```

### Voorbeeld 9: Uitvoer voor niet-Windows-besturingssystemen

In PowerShell 7.1 op Unix-systemen biedt de `Get-Item` cmdlet Unix-achtige uitvoer:

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

- **UnixMode** is de bestandsmachtigingen zoals weergegeven in een Unix-systeem
- **Gebruiker** is de bestandseigenaar
- **Groep** is de groepseigenaar
- **Grootte** is de grootte van het bestand of de map zoals weergegeven op een Unix-systeem

> [!NOTE]
> Deze functie is verplaatst van experimenteel naar standaard in PowerShell 7.1.

## PARAMETERS

### -Stream

> [!NOTE]
> Deze parameter is alleen beschikbaar in Windows.

Hiermee haalt u de opgegeven alternatieve gegevensstroom van het bestand. Voer de naam van de stream in. Jokertekens worden ondersteund. Als u alle streams wilt op halen, gebruikt u een sterretje ( `*` ). Deze parameter is geldig voor -directories, maar houd er rekening mee dat er standaard geen gegevensstromen in de directories staan.

Deze parameter is geïntroduceerd in PowerShell 3.0.  Vanaf PowerShell 7.2 kunt u alternatieve gegevensstromen van `Get-Item` mappen en bestanden krijgen.

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
> Deze parameter wordt niet ondersteund door providers die zijn geïnstalleerd met PowerShell.
> Als u een andere gebruiker wilt imiteren of uw referenties wilt verhogen bij het uitvoeren van deze cmdlet, gebruikt [u Invoke-Command](../Microsoft.PowerShell.Core/Invoke-Command.md).

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

Hiermee geeft u als tekenreeksmatrix een item of items op die deze cmdlet uitsluit in de bewerking. De waarde van deze parameter komt in aanmerking voor de **parameter Path.** Voer een padelement of -patroon in, zoals `*.txt` . Jokertekens zijn toegestaan. De **uitsluiten** parameter is alleen van kracht wanneer de opdracht bevat de inhoud van een item, zoals , waarbij het jokerteken geeft de inhoud `C:\Windows\*` van de `C:\Windows` map.

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

Hiermee geeft u een filter op om de **padparameter te kwalificeren.** De [FileSystem-provider](../Microsoft.PowerShell.Core/About/about_FileSystem_Provider.md) is de enige geïnstalleerde PowerShell-provider die filters ondersteunt. Filters zijn efficiënter dan andere parameters. De provider past een filter toe wanneer de cmdlet de objecten op haalt in plaats van de objecten te laten filteren door PowerShell nadat deze zijn opgehaald. De filterreeks wordt doorgegeven aan de .NET API om bestanden op te semuleren. De API ondersteunt alleen `*` `?` jokertekens en .

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

Geeft aan dat met deze cmdlet items worden opgeslagen die anders niet toegankelijk zijn, zoals verborgen items.
Implementatie varieert per provider. Zie voor meer informatie [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md). Zelfs met **de** parameter Force kan de cmdlet geen beveiligingsbeperkingen overschrijven.

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

Hiermee geeft u als tekenreeksmatrix een item of items op die deze cmdlet in de bewerking op bevat. De waarde van deze parameter komt in aanmerking voor de **parameter Path.** Voer een padelement of -patroon in, zoals `*.txt` . Jokertekens zijn toegestaan. De **parameter Include** is alleen van kracht wanneer de opdracht de inhoud van een item bevat, zoals , waarbij het jokerteken de inhoud van de map `C:\Windows\*` `C:\Windows` specificeert.

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

Hiermee geeft u een pad naar een of meer locaties. De waarde van **LiteralPath** wordt exact gebruikt zoals deze wordt getypt. Er worden geen tekens geïnterpreteerd als jokertekens. Als het pad escape-tekens bevat, sluit u het tussen enkele aanhalingstekens. Enkele aanhalingstekens geven aan PowerShell door dat er geen tekens als escapereeksen moeten worden geïnterpreteerd.

Zie voor meer informatie [about_Quoting_Rules](../Microsoft.Powershell.Core/About/about_Quoting_Rules.md).

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

Hiermee geeft u het pad naar een item. Met deze cmdlet wordt het item op de opgegeven locatie opgeslagen. Jokertekens zijn toegestaan. Deze parameter is vereist, maar de parameternaam **Pad** is optioneel.

Gebruik een punt ( `.` ) om de huidige locatie op te geven. Gebruik het jokerteken ( `*` ) om alle items op de huidige locatie op te geven.

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

Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable. Zie voor meer informatie [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).

## INVOER

### System.String

U kunt een tekenreeks die een pad naar deze cmdlet bevat doorseen.

## UITVOER

### System.Object

Deze cmdlet retourneert de objecten die deze krijgt. Het type wordt bepaald door het type objecten in het pad.

## OPMERKINGEN

Deze cmdlet heeft geen **Recurse-parameter,** omdat deze alleen een item krijgt, niet de inhoud ervan.
Gebruik om de inhoud van een item recursief op te `Get-ChildItem` halen.

Als u door het register wilt navigeren, gebruikt u deze cmdlet om registersleutels op te halen en de om `Get-ItemProperty` registerwaarden en -gegevens op te halen. De registerwaarden worden beschouwd als eigenschappen van de registersleutel.

Deze cmdlet is ontworpen om te werken met de gegevens die beschikbaar worden gemaakt door elke provider. Typ om de providers weer te geven die beschikbaar zijn in uw `Get-PsProvider` sessie. Zie voor meer informatie [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md).

## GERELATEERDE KOPPELINGEN

[Clear-Item](Clear-Item.md)

[Copy-Item](Copy-Item.md)

[Invoke-Item](Invoke-Item.md)

[Item verplaatsen](Move-Item.md)

[Nieuw item](New-Item.md)

[Item verwijderen](Remove-Item.md)

[Rename-Item](Rename-Item.md)

[Set-Item](Set-Item.md)

[Get-ChildItem](Get-ChildItem.md)

[Get-ItemProperty](Get-ItemProperty.md)

[Get-PSProvider](Get-PSProvider.md)

[about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md)
