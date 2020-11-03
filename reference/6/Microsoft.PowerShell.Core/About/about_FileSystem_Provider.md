---
description: Bestandssysteem
keywords: powershell,cmdlet
Locale: en-US
ms.date: 10/18/2018
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_filesystem_provider?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Bestandssysteem provider
ms.openlocfilehash: 24c30e311ba43842e759e884424ce3abfb92aae7
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/13/2020
ms.locfileid: "93252345"
---
# <a name="filesystem-provider"></a>Bestandssysteem provider

## <a name="provider-name"></a>Provider naam
Bestandssysteem

## <a name="drives"></a>Aandrijfeenheden

`C:`, `D:` ...

## <a name="capabilities"></a>Functies

**Filteren** , **ShouldProcess**

## <a name="short-description"></a>Korte beschrijving

Biedt toegang tot bestanden en mappen.

## <a name="detailed-description"></a>Gedetailleerde beschrijving

Met de Power shell- **bestandssysteem** provider kunt u bestanden en mappen in Power shell ophalen, toevoegen, wijzigen, wissen en verwijderen.

De **bestandssysteem** stations zijn een hiërarchische naam ruimte die de mappen en bestanden op uw computer bevat. Een **bestandssysteem** station kan een logisch of phsyical station, een directory of een toegewezen netwerk share zijn.

De **bestandssysteem** provider ondersteunt de volgende cmdlets, die in dit artikel worden besproken.

- [Get-locatie](xref:Microsoft.PowerShell.Management.Get-Location)
- [Set-Location](xref:Microsoft.PowerShell.Management.Set-Location)
- [Get-item](xref:Microsoft.PowerShell.Management.Get-Item)
- [Get-Child item](xref:Microsoft.PowerShell.Management.Get-ChildItem)
- [Invoke-item](xref:Microsoft.PowerShell.Management.Invoke-Item)
- [Item verplaatsen](xref:Microsoft.PowerShell.Management.Move-Item)
- [Nieuw-item](xref:Microsoft.PowerShell.Management.New-Item)
- [Verwijderen-item](xref:Microsoft.PowerShell.Management.Remove-Item)
- [Get-item Property](xref:Microsoft.PowerShell.Management.Get-ItemProperty)
- [Set-item Property](xref:Microsoft.PowerShell.Management.Set-ItemProperty)
- [Wissen-item](xref:Microsoft.PowerShell.Management.Clear-Item)
- [Wissen-item Property](xref:Microsoft.PowerShell.Management.Clear-ItemProperty)
- [Verwijderen-item](xref:Microsoft.PowerShell.Management.Remove-Item)
- [Verwijderen-item Property](xref:Microsoft.PowerShell.Management.Remove-ItemProperty)
- [Get-ACL](xref:Microsoft.PowerShell.Security.Get-Acl)
- [Set-ACL](xref:Microsoft.PowerShell.Security.Set-Acl)
- [Get-AuthenticodeSignature](xref:Microsoft.PowerShell.Security.Get-AuthenticodeSignature)
- [Set-AuthenticodeSignature](xref:Microsoft.PowerShell.Security.Set-AuthenticodeSignature)

## <a name="types-exposed-by-this-provider"></a>Typen die door deze provider worden weer gegeven

De bestanden zijn exemplaren van de klasse [System. io. file info](/dotnet/api/system.io.fileinfo) .  Directory's zijn exemplaren van de klasse [System. io. DirectoryInfo](/dotnet/api/system.io.directoryinfo) .

## <a name="navigating-the-filesystem-drives"></a>Navigeren door de bestandssysteem stations

De gegevens archieven van het **Bestands systeem** worden weer gegeven door logische stations op de computer toe te wijzen als Power Shell-stations. Als u wilt werken met een **bestandssysteem** station, kunt u uw locatie wijzigen in een station gifte de naam van het station gevolgd door een dubbele punt ( `:` ).

```powershell
Set-Location C:
```

U kunt ook met de **File System** provider werken vanuit elk ander Power Shell-station. Als u wilt verwijzen naar een bestand of map vanaf een andere locatie, gebruikt u de naam van het station ( `C:` , `D:` ,...) in het pad.

> [!NOTE]
> In Power shell worden aliassen gebruikt om u een vertrouwde manier te bieden om met provider paden te werken. Opdrachten zoals `dir` en `ls` zijn nu aliassen voor [Get-Child item](xref:Microsoft.PowerShell.Management.Get-ChildItem), `cd` is een alias voor [Set-Location](xref:Microsoft.PowerShell.Management.Set-Location). en `pwd` is een alias voor [Get-location](xref:Microsoft.PowerShell.Management.Get-Location).

## <a name="getting-files-and-directories"></a>Bestanden en mappen ophalen

De `Get-ChildItem` cmdlet retourneert alle bestanden en mappen op de huidige locatie. U kunt een ander pad opgeven om te zoeken en ingebouwde para meters te gebruiken voor het filteren en beheren van de diepte van recursie.

```powershell
Get-ChildItem
```

Zie [Get-Child item](xref:Microsoft.PowerShell.Management.Get-ChildItem)voor meer informatie over het gebruik van de cmdlet.

## <a name="copying-files-and-directories"></a>Kopiëren van bestanden en mappen

De `Copy-Item` cmdlet kopieert bestanden en mappen naar een locatie die u opgeeft.
Para meters zijn beschikbaar voor filteren en recursief, vergelijkbaar met `Get-ChildItem` .

Met de volgende opdracht worden alle bestanden en mappen onder het pad ' C:\Temp \" naar de map ' C:\Windows\Temp gekopieerd.

```powershell
Copy-Item -Path C:\temp\* -Destination C:\Windows\Temp -Recurse -File
```

`Copy-Item` overschrijft bestanden in de doelmap zonder dat om bevestiging wordt gevraagd.

Met deze opdracht kopieert `a.txt` u het bestand vanuit de `C:\a` map naar de `C:\a\bb` map.

```powershell
Copy-Item -Path C:\a\a.txt -Destination C:\a\bb\a.txt
```

Kopieert alle mappen en bestanden in de `C:\a` map naar de `C:\c` map. Als een van de mappen die u wilt kopiëren al aanwezig is in de doelmap, mislukt de opdracht tenzij u de para meter Force opgeeft.

```powershell
Copy-Item -Path C:\a\* -Destination C:\c -Recurse
```

Zie [kopiëren-item](xref:Microsoft.PowerShell.Management.Copy-Item)voor meer informatie.

## <a name="moving-files-and-directories"></a>Bestanden en mappen verplaatsen

Met deze opdracht wordt het `c.txt` bestand in de `C:\a` map verplaatst naar de `C:\a\aa` map:

```powershell
Move-Item -Path C:\a\c.txt -Destination C:\a\aa
```

Met de opdracht wordt een bestaand bestand met dezelfde naam niet automatisch overschreven. Als u wilt forceren dat de cmdlet een bestaand bestand overschrijft, geeft u de para meter Force op.

U kunt een map niet verplaatsen als die map de huidige locatie is. Wanneer u gebruikt `Move-Item` om de map op de huidige locatie te verplaatsen, ziet u deze fout.

```
C:\temp> Move-Item -Path C:\temp\ -Destination C:\Windows\Temp

Move-Item : Cannot move item because the item at 'C:\temp\' is in use.
At line:1 char:1
+ Move-Item C:\temp\ C:\temp2\
+ ~~~~~~~~~~~~~~~~~~~~~~~~~~~~
    + CategoryInfo          : InvalidOperation: (:) [Move-Item], PSInvalidOperationException
    + FullyQualifiedErrorId : InvalidOperation,Microsoft.PowerShell.Commands.MoveItemCommand
```

## <a name="managing-file-content"></a>Bestands inhoud beheren

### <a name="get-the-content-of-a-file"></a>De inhoud van een bestand ophalen

Met deze opdracht wordt de inhoud van het bestand ' Test.txt ' opgehaald en weer gegeven in de-console.

```powershell
Get-Content -Path Test.txt
```

U kunt de inhoud van het bestand door sluizen naar een andere cmdlet. Met de volgende opdracht wordt bijvoorbeeld de inhoud van het `Test.txt` bestand gelezen en vervolgens als invoer voor de [ConvertTo-HTML-](xref:Microsoft.PowerShell.Utility.ConvertTo-Html) cmdlet geleverd:

```powershell
Get-Content -Path Test.txt | ConvertTo-Html
```

U kunt ook de inhoud van een bestand ophalen door een voor voegsel van het pad naar de provider te krijgen met het dollar teken ( `$` ). Het pad moet tussen accolades worden geplaatst als gevolg van beperkingen voor de naamgeving van variabelen. Zie [about_Variables](about_Variables.md)voor meer informatie.

```powershell
${C:\Windows\System32\Drivers\etc\hosts}
```

### <a name="add-content-to-a-file"></a>Inhoud toevoegen aan een bestand

Met deze opdracht wordt de teken reeks test inhoud toegevoegd aan het `Test.txt` bestand:

```powershell
Add-Content -Path test.txt -Value "test content"
```

De bestaande inhoud in het `Test.txt` bestand wordt niet verwijderd.

### <a name="replace-the-content-of-a-file"></a>De inhoud van een bestand vervangen

Met deze opdracht wordt de inhoud van het `Test.txt` bestand vervangen door de teken reeks "inhoud testen":

```powershell
Set-Content -Path test.txt -Value "test content"
```

De inhoud van wordt overschreven `Test.txt` . U kunt de para meter **Value** van de cmdlet [New-item](xref:Microsoft.PowerShell.Management.New-Item) gebruiken om inhoud toe te voegen aan een bestand wanneer u het maakt.

### <a name="loop-through-the-contents-of-a-file"></a>De inhoud van een bestand door lopen

De `Get-Content` cmdlet maakt standaard gebruik van het einde van de regel als scheidings teken, zodat er een bestand wordt opgehaald als een verzameling teken reeksen, waarbij elke regel als één teken reeks in het bestand wordt gebruikt.

U kunt de `-Delimiter` para meter gebruiken om een alternatief scheidings teken op te geven. Als u deze instelt op de tekens waarin het einde van een sectie of het begin van de volgende sectie wordt aangegeven, kunt u het bestand in logische delen splitsen.

Met de eerste opdracht wordt het `Employees.txt` bestand opgehaald en gesplitst in secties, die allemaal eindigen met de woorden ' einde van werknemers record ', en deze worden opgeslagen in de `$e` variabele.

De tweede opdracht maakt gebruik van de matrix notatie voor het ophalen van het eerste item in de verzameling in `$e` . Er wordt gebruikgemaakt van een index van 0, omdat Power shell-matrices op nul zijn gebaseerd.

`Get-Content`Zie het Help-onderwerp voor de [Get-content](xref:Microsoft.PowerShell.Management.Get-Content)voor meer informatie over de cmdlet.

Zie [about_Arrays](../About/about_Arrays.md)voor meer informatie over matrices.

```powershell
$e = Get-Content c:\test\employees.txt -Delimited "End Of Employee Record"
$e[0]
```

## <a name="managing-security-descriptors"></a>Security descriptors beheren

### <a name="view-the-acl-for-a-file"></a>De ACL voor een bestand weer geven

Met deze opdracht wordt een [System. Security. accesscontrol. FileSecurity](/dotnet/api/system.security.accesscontrol.filesecurity) -object geretourneerd:

```powershell
Get-Acl -Path test.txt | Format-List -Property *
```

Voor meer informatie over dit object pipet u de opdracht naar de cmdlet [Get-member](xref:Microsoft.PowerShell.Utility.Get-Member) . Of Zie '[FileSecurity](/dotnet/api/system.security.accesscontrol.filesecurity) class ' in de MSDN-bibliotheek (micro soft Developer Network).

### <a name="modify-the-acl-for-a-file"></a>De ACL voor een bestand wijzigen

### <a name="create-and-set-an-acl-for-a-file"></a>Een ACL maken en instellen voor een bestand

## <a name="creating-files-and-directories"></a>Bestanden en mappen maken

### <a name="create-a-directory"></a>Een map maken

Met deze opdracht maakt u de `logfiles` map op het `C` station:

```powershell
New-Item -Path c:\ -Name logfiles -Type directory
```

Power shell bevat ook een `mkdir` functie (alias `md` ) die gebruikmaakt van de cmdlet [New-item](xref:Microsoft.PowerShell.Management.New-Item) om een nieuwe map te maken.

### <a name="create-a-file"></a>Een bestand maken

Met deze opdracht maakt `log2.txt` u het bestand in de `C:\logfiles` map en voegt u vervolgens de teken reeks "test logboek" toe aan het bestand:

```powershell
New-Item -Path c:\logfiles -Name log2.txt -Type file
```

### <a name="create-a-file-with-content"></a>Een bestand met inhoud maken

Hiermee maakt u een bestand `log2.txt` met de naam in de `C:\logfiles` map en voegt u de teken reeks ' test logboek ' toe aan het bestand.

```powershell
New-Item -Path c:\logfiles -Name log2.txt -Type file -Value "test log"
```

## <a name="renaming-files-and-directories"></a>Naam wijzigen van bestanden en mappen

### <a name="rename-a-file"></a>De naam van een bestand wijzigen

Met deze opdracht wordt de naam `a.txt` van het bestand in de map gewijzigd in `C:\a` `b.txt` :

```powershell
Rename-Item -Path c:\a\a.txt -NewName b.txt
```

### <a name="rename-a-directory"></a>De naam van een map wijzigen

Met deze opdracht wordt de naam van de `C:\a\cc` map gewijzigd in `C:\a\dd` :

```powershell
Rename-Item -Path c:\a\cc -NewName dd
```

## <a name="deleting-files-and-directories"></a>Bestanden en mappen verwijderen

### <a name="delete-a-file"></a>Een bestand verwijderen

Met deze opdracht wordt het `Test.txt` bestand in de huidige map verwijderd:

```powershell
Remove-Item -Path test.txt
```

### <a name="delete-files-using-wildcards"></a>Bestanden verwijderen met Joker tekens

Met deze opdracht worden alle bestanden in de huidige map met de `.xml` bestandsnaam extensie verwijderd:

```powershell
Remove-Item -Path *.xml
```

## <a name="starting-a-program-by-invoking-an-associated-file"></a>Een programma starten door een gekoppeld bestand aan te roepen

### <a name="invoke-a-file"></a>Een bestand aanroepen

Met de eerste opdracht wordt de cmdlet [Get-service](xref:Microsoft.PowerShell.Management.Get-Service) gebruikt om informatie over lokale services op te halen.

Het pipet de gegevens naar de cmdlet [export-csv](xref:Microsoft.PowerShell.Utility.Export-Csv) en slaat die informatie vervolgens op in het `Services.csv` bestand.

Met de tweede opdracht wordt [invoke-item](xref:Microsoft.PowerShell.Management.Invoke-Item) gebruikt om het bestand te openen `services.csv` in het programma dat is gekoppeld aan de `.csv` extensie:

```powershell
Get-Service | Export-Csv -Path services.csv
Invoke-Item -Path services.csv
```

## <a name="getting-files-and-folders-with-specified-attributes"></a>Bestanden en mappen met opgegeven kenmerken ophalen

### <a name="get-system-files"></a>Systeem bestanden ophalen

Met deze opdracht worden systeem bestanden in de huidige map en de submappen ervan opgehaald.

De `-File` para meter wordt gebruikt voor het ophalen van alleen bestanden (niet directory's) en de `-System` para meter om alleen items met het kenmerk systeem op te halen.

De `-Recurse` para meter wordt gebruikt voor het ophalen van de items in de huidige map en alle submappen.

```powershell
Get-ChildItem -File -System -Recurse
```

### <a name="get-hidden-files"></a>Verborgen bestanden ophalen

Met deze opdracht worden alle bestanden met inbegrip van verborgen bestanden in de huidige map opgehaald.

Hierbij wordt gebruikgemaakt van de para meter **Attributes** met twee waarden, `!Directory+Hidden` , die verborgen bestanden ophalen en `!Directory` , waarmee alle andere bestanden worden opgehaald.

```powershell
Get-ChildItem -Attributes !Directory,!Directory+Hidden
```

`dir -att !d,!d+h` is het equivalent van deze opdracht.

### <a name="get-compressed-and-encrypted-files"></a>Gecomprimeerde en versleutelde bestanden ophalen

Met deze opdracht worden bestanden in de huidige map opgehaald die zijn gecomprimeerd of versleuteld zijn.

De `-Attributes` para meter wordt gebruikt met twee waarden `Compressed` en `Encrypted` . De waarden worden gescheiden door een komma `,` die de operator or vertegenwoordigt.

```powershell
Get-ChildItem -Attributes Compressed,Encrypted
```

## <a name="dynamic-parameters"></a>Dynamische parameters

Dynamische para meters zijn cmdlet-para meters die worden toegevoegd door een Power shell-provider en zijn alleen beschikbaar wanneer de cmdlet wordt gebruikt in het station waarvoor de provider is ingeschakeld.

### <a name="encoding-microsoftpowershellcommandsfilesystemcmdletproviderencoding"></a>Gecodeerd \<Microsoft.PowerShell.Commands.FileSystemCmdletProviderEncoding\>

Hiermee geeft u de bestands codering. De standaard waarde is ASCII.

- **ASCII** : gebruikt de code ring voor de ASCII-tekenset (7-bits).
- **BigEndianUnicode** : codeert in UTF-16-indeling met behulp van de byte volgorde big endian.
- **Teken reeks** : maakt gebruik van het coderings type voor een teken reeks.
- **Unicode** : wordt gecodeerd in UTF-16-indeling met behulp van de byte volgorde little endian.
- **UTF7** : wordt gecodeerd in de indeling UTF-7.
- **Utf8** : gecodeerd in UTF-8-indeling.
- **UTF8BOM** : coderen in UTF-8-indeling met byte order Mark (bom)
- **UF8NOBOM** : code ring in UTF-8-indeling zonder byte order Mark (bom)
- **UTF32** : code ring in UTF-32-indeling.
- **Standaard** : Codeer in de standaard pagina met geïnstalleerde codes.
- **OEM** : gebruikt de standaard codering voor MS-DOS-en console-Program ma's.
- **Onbekend** : het coderings type is onbekend of ongeldig. De gegevens kunnen worden behandeld als binair.

#### <a name="cmdlets-supported"></a>Ondersteunde cmdlets

- [Add-content](xref:Microsoft.PowerShell.Management.Add-Content)
- [Get-Content](xref:Microsoft.PowerShell.Management.Get-Content)
- [Set-Content](xref:Microsoft.PowerShell.Management.Set-Content)

### <a name="delimiter-systemstring"></a>Vorm \<System.String\>

Hiermee geeft u het scheidings teken op dat wordt gebruikt om het bestand in objecten te verdelen terwijl [het wordt gelezen](xref:Microsoft.PowerShell.Management.Get-Content) .

De standaard waarde is `\n` , het einde van de regel.

Bij het lezen van een tekst bestand wordt met [Get-content](xref:Microsoft.PowerShell.Management.Get-Content) een verzameling teken reeks objecten geretourneerd, die elk eindigen op het scheidings teken.

Als u een scheidings teken opgeeft dat niet in het bestand voor komt, [Get-content](xref:Microsoft.PowerShell.Management.Get-Content) retourneert het hele bestand als een enkel, niet-gescheiden object.

U kunt deze para meter gebruiken om een groot bestand te splitsen in kleinere bestanden door een bestands scheidings teken, zoals ' einde van het voor beeld ', op te geven als scheidings teken. Het scheidings teken wordt bewaard (niet verwijderd) en wordt het laatste item in elk bestands gedeelte.

> [!NOTE]
> Wanneer de waarde van de para meter op dit moment `-Delimiter` een lege teken reeks is, retourneert [Get-content](xref:Microsoft.PowerShell.Management.Get-Content) niets.
> Dit is een bekend probleem. Om [Get-content](xref:Microsoft.PowerShell.Management.Get-Content) af te dwingen om het hele bestand als één undelimited teken reeks te retour neren, voert u een waarde in die niet voor komt in het bestand.

#### <a name="cmdlets-supported"></a>Ondersteunde cmdlets

- [Get-Content](xref:Microsoft.PowerShell.Management.Get-Content)

### <a name="wait-systemmanagementautomationswitchparameter"></a>Bewerking \<System.Management.Automation.SwitchParameter\>

Er wordt gewacht tot de inhoud aan het bestand is toegevoegd. Als er inhoud wordt toegevoegd, wordt de toegevoegde inhoud geretourneerd. Als de inhoud is gewijzigd, wordt het hele bestand geretourneerd.

Als er wordt gewacht, controleert de [Get-content](xref:Microsoft.PowerShell.Management.Get-Content) het bestand eenmaal per seconde totdat u het onderbreekt, bijvoorbeeld door op CTRL + C te drukken.

#### <a name="cmdlets-supported"></a>Ondersteunde cmdlets

- [Get-Content](xref:Microsoft.PowerShell.Management.Get-Content)

### <a name="attributes-flagsexpression"></a>Eigenschappen \<FlagsExpression\>

Hiermee worden bestanden en mappen opgehaald met de opgegeven kenmerken. Deze para meter ondersteunt alle kenmerken en geeft u de mogelijkheid om complexe combi Naties van kenmerken op te geven.

De `-Attributes` para meter is geïntroduceerd in Windows Power shell 3,0.

De `-Attributes` para meter ondersteunt de volgende kenmerken:

- **Archiveren**
- **Gecomprimeerd**
- **Apparaat**
- **Directory**
- **Versleuteld**
- **Verborgen**
- **Normaal**
- **NotContentIndexed**
- **Offline**
- **Kenmerk**
- **ReparsePoint**
- **SparseFile**
- **Systeem**
- **Tijdelijk**

Zie de [FileAttributes](/dotnet/api/system.io.fileattributes) -inventarisatie voor een beschrijving van deze kenmerken.

Gebruik de volgende Opera tors om kenmerken te combi neren.

- `!` -NIET
- `+` -EN
- `,` -OF

Er zijn geen spaties toegestaan tussen een operator en het bijbehorende kenmerk. Spaties zijn echter toegestaan vóór komma's.

#### <a name="cmdlets-supported"></a>Ondersteunde cmdlets

- [Get-Child item](xref:Microsoft.PowerShell.Management.Get-ChildItem)

### <a name="directory-systemmanagementautomationswitchparameter"></a>Uitvoermap \<System.Management.Automation.SwitchParameter\>

Haalt mappen (mappen) op.

De `-Directory` para meter is geïntroduceerd in Windows Power shell 3,0.

Als u alleen mappen wilt ophalen, gebruikt u de `-Directory` para meter en laat u de `-File` para meter weg. Als u directory's wilt uitsluiten, gebruikt u de `-File` para meter en laat u de `-Directory` para meter weg of gebruikt u de `-Attributes` para meter.

#### <a name="cmdlets-supported"></a>Ondersteunde cmdlets

- [Get-Child item](xref:Microsoft.PowerShell.Management.Get-ChildItem)

### <a name="file-systemmanagementautomationswitchparameter"></a>Profiler \<System.Management.Automation.SwitchParameter\>

Haalt bestanden op.

De `-File` para meter is geïntroduceerd in Windows Power shell 3,0.

Als u alleen bestanden wilt ophalen, gebruikt u de `-File` para meter en laat u de `-Directory` para meter weg. Als u bestanden wilt uitsluiten, gebruikt u de `-Directory` para meter en laat u de `-File` para meter weg of gebruikt u de `-Attributes` para meter.

#### <a name="cmdlets-supported"></a>Ondersteunde cmdlets

- [Get-Child item](xref:Microsoft.PowerShell.Management.Get-ChildItem)

### <a name="hidden-systemmanagementautomationswitchparameter"></a>Zit \<System.Management.Automation.SwitchParameter\>

Hiermee worden alleen verborgen bestanden en mappen (mappen) opgehaald. [Get-Child item](xref:Microsoft.PowerShell.Management.Get-ChildItem) haalt standaard alleen niet-verborgen items op.

De `-Hidden` para meter is geïntroduceerd in Windows Power shell 3,0.

Als u alleen verborgen items wilt ophalen, gebruikt u de `-Hidden` para meter, de `h` `ah` aliassen of de **verborgen** waarde van de `-Attributes` para meter. Als u verborgen items wilt uitsluiten, laat u de `-Hidden` para meter weg of gebruikt u de `-Attributes` para meter.

#### <a name="cmdlets-supported"></a>Ondersteunde cmdlets

- [Get-Child item](xref:Microsoft.PowerShell.Management.Get-ChildItem)

### <a name="readonly-systemmanagementautomationswitchparameter"></a>Kenmerk \<System.Management.Automation.SwitchParameter\>

Hiermee worden alleen alleen-lezen bestanden en mappen (mappen) opgehaald.

De `-ReadOnly` para meter is geïntroduceerd in Windows Power shell 3,0.

Als u alleen-lezen items wilt ophalen, gebruikt u de `-ReadOnly` para meter, de `ar` alias of de **ReadOnly** -waarde van de `-Attributes` para meter. Als u alleen-lezen items wilt uitsluiten, gebruikt u de `-Attributes` para meter.

#### <a name="cmdlets-supported"></a>Ondersteunde cmdlets

- [Get-Child item](xref:Microsoft.PowerShell.Management.Get-ChildItem)

### <a name="system-systemmanagementautomationswitchparameter"></a>Opgehaald \<System.Management.Automation.SwitchParameter\>

Hiermee worden alleen systeem bestanden en mappen (mappen) opgehaald.

De `-System` para meter is geïntroduceerd in Windows Power shell 3,0.

Als u alleen systeem bestanden en-mappen wilt ophalen, gebruikt u de `-System` para meter, de `as` alias of de **systeem** waarde van de `-Attributes` para meter. Gebruik de para meter om systeem bestanden en-mappen uit te sluiten `-Attributes` .

#### <a name="cmdlets-supported"></a>Ondersteunde cmdlets

- [Get-Child item](xref:Microsoft.PowerShell.Management.Get-ChildItem)

### <a name="newerthan-systemdatetime"></a>NewerThan \<System.DateTime\>

Retourneert `$True` wanneer de `LastWriteTime` waarde van een bestand groter is dan de opgegeven datum. Als dat niet het geval is, wordt geretourneerd `$False` .

Voer een [DateTime](/dotnet/api/system.datetime) -object in, zoals een dat de cmdlet [Get-date](xref:Microsoft.PowerShell.Utility.Get-Date) retourneert, of een teken reeks die kan worden geconverteerd naar een [DateTime](/dotnet/api/system.datetime) -object, zoals `"August 10, 2011 2:00 PM"` .

#### <a name="cmdlets-supported"></a>Ondersteunde cmdlets

- [Test-pad](xref:Microsoft.PowerShell.Management.Test-Path)

### <a name="olderthan-systemdatetime"></a>OlderThan \<System.DateTime\>

Retourneert `$True` wanneer de `LastWriteTime` waarde van een bestand kleiner is dan de opgegeven datum. Als dat niet het geval is, wordt geretourneerd `$False` .

Voer een [DateTime](/dotnet/api/system.datetime) -object in, zoals een dat de cmdlet [Get-date](xref:Microsoft.PowerShell.Utility.Get-Date) retourneert, of een teken reeks die kan worden geconverteerd naar een [DateTime](/dotnet/api/system.datetime) -object, zoals `"August 10, 2011 2:00 PM"` .

#### <a name="cmdlets-supported"></a>Ondersteunde cmdlets

- [Test-pad](xref:Microsoft.PowerShell.Management.Test-Path)

### <a name="stream-systemstring"></a>Bitsnelheid \<System.String\>

Hiermee beheert u alternatieve gegevens stromen. Voer de naam van de stream in. Joker tekens zijn alleen toegestaan in opdrachten [Get-item](xref:Microsoft.PowerShell.Management.Get-Item) for en [Remove item](xref:Microsoft.PowerShell.Management.Remove-Item) in een bestandssysteem station.

#### <a name="cmdlets-supported"></a>Ondersteunde cmdlets

- [Add-content](xref:Microsoft.PowerShell.Management.Add-Content)
- [Wissen-inhoud](xref:Microsoft.PowerShell.Management.Clear-Content)
- [Get-item](xref:Microsoft.PowerShell.Management.Get-Item)
- [Get-Content](xref:Microsoft.PowerShell.Management.Get-Content)
- [Verwijderen-item](xref:Microsoft.PowerShell.Management.Remove-Item)
- [Set-Content](xref:Microsoft.PowerShell.Management.Set-Content)

### <a name="raw-switchparameter"></a>Uitgang \<SwitchParameter\>

Hiermee worden de tekens voor nieuwe regels genegeerd. Retourneert inhoud als één item.

#### <a name="cmdlets-supported"></a>Ondersteunde cmdlets

- [Get-Content](xref:Microsoft.PowerShell.Management.Get-Content)

### <a name="itemtype-string"></a>Item type \<String\>

Met deze para meter kunt u de Tye opgeven van het item dat moet worden gemaakt met `New-Item`

De beschik bare waarden van deze para meter zijn afhankelijk van de huidige provider die u gebruikt.

In een `FileSystem` station zijn de volgende waarden toegestaan:

- Bestand
- Directory
- SymbolicLink
- Verbinding
- Hard link

### <a name="cmdlets-supported"></a>Ondersteunde cmdlets

- [Nieuw-item](xref:Microsoft.PowerShell.Management.New-Item)

## <a name="using-the-pipeline"></a>De pijp lijn gebruiken

Provider-cmdlets accepteren de invoer van de pijp lijn. U kunt de pijp lijn gebruiken om de taak te vereenvoudigen door provider gegevens van de ene cmdlet naar een andere provider-cmdlet te verzenden.
Zie de cmdlet-verwijzingen die in dit artikel worden vermeld voor meer informatie over het gebruik van de pijp lijn met provider-cmdlets.

## <a name="getting-help"></a>Ondersteuning vragen

Vanaf Windows Power Shell 3,0 kunt u aangepaste Help-onderwerpen voor provider-cmdlets krijgen waarin wordt uitgelegd hoe deze cmdlets zich gedragen in een bestandssysteem station.

Als u de Help-onderwerpen wilt ophalen die zijn aangepast voor het bestandssysteem station, voert u de opdracht [Get-Help](xref:Microsoft.PowerShell.Core.Get-Help) uit in een bestandssysteem station of gebruikt `-Path` u de para meter [Get-Help](xref:Microsoft.PowerShell.Core.Get-Help) om een bestandssysteem station op te geven.

```powershell
Get-Help Get-ChildItem
```

```powershell
Get-Help Get-ChildItem -Path c:
```

## <a name="see-also"></a>Zie ook

[about_Providers](../About/about_Providers.md)
