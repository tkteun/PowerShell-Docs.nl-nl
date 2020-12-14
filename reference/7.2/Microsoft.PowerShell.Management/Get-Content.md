---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 08/19/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/get-content?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-Content
ms.openlocfilehash: 8ad7df860533b9f394fd81199dd7213175cce213
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 11/17/2020
ms.locfileid: "94706177"
---
# Get-Content

## SAMENVATTING
Hiermee wordt de inhoud van het item op de opgegeven locatie opgehaald.

## SYNTAXIS

### Pad (standaard)

```
Get-Content [-ReadCount <Int64>] [-TotalCount <Int64>] [-Tail <Int32>] [-Path] <String[]>
 [-Filter <String>] [-Include <String[]>] [-Exclude <String[]>] [-Force] [-Credential <PSCredential>]
 [-Delimiter <String>] [-Wait] [-Raw] [-Encoding <Encoding>] [-AsByteStream] [-Stream <String>]
 [<CommonParameters>]
```

### LiteralPath

```
Get-Content [-ReadCount <Int64>] [-TotalCount <Int64>] [-Tail <Int32>] -LiteralPath <String[]>
 [-Filter <String>] [-Include <String[]>] [-Exclude <String[]>] [-Force] [-Credential <PSCredential>]
 [-Delimiter <String>] [-Wait] [-Raw] [-Encoding <Encoding>] [-AsByteStream] [-Stream <String>]
 [<CommonParameters>]
```

## BESCHRIJVING

`Get-Content`Met de cmdlet wordt de inhoud van het item opgehaald op de locatie die is opgegeven door het pad, zoals de tekst in een bestand of de inhoud van een functie. Voor bestanden wordt de inhoud één regel tegelijk gelezen en wordt een verzameling objecten geretourneerd, die elk een regel met inhoud vertegenwoordigt.

Vanaf Power Shell 3,0 `Get-Content` kan ook een opgegeven aantal regels worden opgehaald vanaf het begin of einde van een item.

## VOORBEELDEN

### Voor beeld 1: de inhoud van een tekst bestand ophalen

In dit voor beeld wordt de inhoud van een bestand in de huidige map opgehaald. Het `LineNumbers.txt` bestand bevat 100 regels in de indeling. **Dit is regel X** en wordt in verschillende voor beelden gebruikt.

```powershell
1..100 | ForEach-Object { Add-Content -Path .\LineNumbers.txt -Value "This is line $_." }
Get-Content -Path .\LineNumbers.txt
```

```Output
This is Line 1
This is Line 2
...
This is line 99.
This is line 100.
```

De matrix waarden 1-100 worden in de pijp lijn naar de `ForEach-Object` cmdlet verzonden. `ForEach-Object` maakt gebruik van een script blok met de `Add-Content` cmdlet om het bestand te maken `LineNumbers.txt` . De variabele `$_` vertegenwoordigt de matrix waarden wanneer elk object wordt verzonden naar de pijp lijn. De `Get-Content` cmdlet gebruikt de para meter **Path** om het bestand op te geven `LineNumbers.txt` en geeft de inhoud weer in de Power shell-console.

### Voor beeld 2: het aantal regels dat Get-Content retourneert, beperken

Met deze opdracht worden de eerste vijf regels van een bestand opgehaald. De para meter **totalCount** wordt gebruikt voor het ophalen van de eerste vijf regels met inhoud. In dit voor beeld wordt het `LineNumbers.txt` bestand gebruikt dat in voor beeld 1 is gemaakt.

```powershell
Get-Content -Path .\LineNumbers.txt -TotalCount 5
```

```Output
This is Line 1
This is Line 2
This is Line 3
This is Line 4
This is Line 5
```

### Voor beeld 3: een specifieke regel met inhoud ophalen uit een tekst bestand

Met deze opdracht wordt een specifiek aantal regels van een bestand opgehaald en wordt vervolgens alleen de laatste regel van die inhoud weer gegeven. De para meter **totalCount** haalt de eerste 25 regels inhoud op. In dit voor beeld wordt het `LineNumbers.txt` bestand gebruikt dat in voor beeld 1 is gemaakt.

```powershell
(Get-Content -Path .\LineNumbers.txt -TotalCount 25)[-1]
```

```Output
This is Line 25
```

De `Get-Content` opdracht wordt tussen haakjes geplaatst, zodat de opdracht is voltooid voordat u naar de volgende stap gaat. `Get-Content`retourneert een matrix met lijnen, Hiermee kunt u de index notatie toevoegen na het haakje om een specifiek regel nummer op te halen. In dit geval geeft de `[-1]` index de laatste index in de geretourneerde matrix van 25 opgehaalde regels.

### Voor beeld 4: de laatste regel van een tekst bestand ophalen

Met deze opdracht wordt de eerste regel en de laatste regel van de inhoud van een bestand opgehaald. In dit voor beeld wordt het `LineNumbers.txt` bestand gebruikt dat in voor beeld 1 is gemaakt.

```powershell
Get-Item -Path .\LineNumbers.txt | Get-Content -Tail 1
```

```Output
This is Line 100
```

In dit voor beeld wordt de `Get-Item` cmdlet gebruikt om te demonstreren dat u bestanden in de `Get-Content` para meter kunt sluizen. De para meter **staart** haalt de laatste regel van het bestand op. Deze methode is sneller dan alle regels op te halen en de `[-1]` index notatie te gebruiken.

### Voor beeld 5: de inhoud van een alternatieve gegevens stroom ophalen

In dit voor beeld wordt beschreven hoe u de para meter **Stream** kunt gebruiken om de inhoud van een alternatieve gegevens stroom op te halen voor bestanden die zijn opgeslagen op een Windows NTFS volume. In dit voor beeld `Set-Content` wordt de cmdlet gebruikt voor het maken van voorbeeld inhoud in een bestand met de naam `Stream.txt` .

```powershell
Set-Content -Path .\Stream.txt -Value 'This is the content of the Stream.txt file'
# Specify a wildcard to the Stream parameter to display all streams of the recently created file.
Get-Item -Path .\Stream.txt -Stream *
```

```Output
PSPath        : Microsoft.PowerShell.Core\FileSystem::C:\Test\Stream.txt::$DATA
PSParentPath  : Microsoft.PowerShell.Core\FileSystem::C:\Test
PSChildName   : Stream.txt::$DATA
PSDrive       : C
PSProvider    : Microsoft.PowerShell.Core\FileSystem
PSIsContainer : False
FileName      : C:\Test\Stream.txt
Stream        : :$DATA
Length        : 44
```

```powershell
# Retrieve the content of the primary, or $DATA stream.
Get-Content -Path .\Stream.txt -Stream $DATA
```

```Output
This is the content of the Stream.txt file
```

```powershell
# Use the Stream parameter of Add-Content to create a new Stream containing sample content.
Add-Content -Path .\Stream.txt -Stream NewStream -Value 'Added a stream named NewStream to Stream.txt'
# Use Get-Item to verify the stream was created.
Get-Item -Path .\Stream.txt -Stream *
```

```Output
PSPath        : Microsoft.PowerShell.Core\FileSystem::C:\Test\Stream.txt::$DATA
PSParentPath  : Microsoft.PowerShell.Core\FileSystem::C:\Test
PSChildName   : Stream.txt::$DATA
PSDrive       : C
PSProvider    : Microsoft.PowerShell.Core\FileSystem
PSIsContainer : False
FileName      : C:\Test\Stream.txt
Stream        : :$DATA
Length        : 44

PSPath        : Microsoft.PowerShell.Core\FileSystem::C:\Test\Stream.txt:NewStream
PSParentPath  : Microsoft.PowerShell.Core\FileSystem::C:\Test
PSChildName   : Stream.txt:NewStream
PSDrive       : C
PSProvider    : Microsoft.PowerShell.Core\FileSystem
PSIsContainer : False
FileName      : C:\Test\Stream.txt
Stream        : NewStream
Length        : 46
```

```powershell
# Retrieve the content of your newly created Stream.
Get-Content -Path .\Stream.txt -Stream NewStream
```

```Output
Added a stream named NewStream to Stream.txt
```

De **Stream** -para meter is een dynamische para meter van de [File System Provider](../microsoft.powershell.core/about/about_filesystem_provider.md#stream-systemstring).
Standaard worden `Get-Content` alleen gegevens opgehaald uit de primaire of `$DATA` Stream. **Stromen** kunnen worden gebruikt voor het opslaan van verborgen gegevens zoals kenmerken, beveiligings instellingen of andere gegevens.

### Voor beeld 6: onbewerkte inhoud ophalen

Met de opdrachten in dit voor beeld wordt de inhoud van een bestand als één teken reeks opgehaald, in plaats van een matrix met teken reeksen. Standaard wordt, zonder de **onbewerkte** dynamische para meter, de inhoud geretourneerd als een matrix met teken reeksen die zijn gescheiden door een nieuwe regel. In dit voor beeld wordt het `LineNumbers.txt` bestand gebruikt dat in het voor beeld is gemaakt
1.

```powershell
$raw = Get-Content -Path .\LineNumbers.txt -Raw
$lines = Get-Content -Path .\LineNumbers.txt
Write-Host "Raw contains $($raw.Count) lines."
Write-Host "Lines contains $($lines.Count) lines."
```

```Output
Raw contains 1 lines.
Lines contains 100 lines.
```

### Voor beeld 7: filters gebruiken met Get-Content

U kunt een filter opgeven voor de `Get-Content` cmdlet. Wanneer u filters gebruikt om de para meter **Path** te kwalificeren, moet u een asterisk ( `*` ) toevoegen om de inhoud van het pad aan te geven.

Met de volgende opdracht wordt de inhoud van alle `*.log` bestanden in de `C:\Temp` map opgehaald.

```powershell
Get-Content -Path C:\Temp\* -Filter *.log
```

### Voor beeld 8: de bestands inhoud als een byte matrix ophalen

In dit voor beeld ziet u hoe u de inhoud van een bestand als `[byte[]]` één object kunt ophalen.

```powershell
$byteArray = Get-Content -Path C:\temp\test.txt -AsByteStream -Raw
Get-Member -InputObject $bytearray
```

```Output
   TypeName: System.Byte[]

Name           MemberType            Definition
----           ----------            ----------
Count          AliasProperty         Count = Length
Add            Method                int IList.Add(System.Object value)
```

De eerste opdracht gebruikt de para meter **AsByteStream** om de stroom van bytes uit het bestand op te halen.
De **onbewerkte** para meter zorgt ervoor dat de bytes worden geretourneerd als een `[System.Byte[]]` . Als de **onbewerkte** para meter ontbreekt, is de geretourneerde waarde een stroom van bytes, die wordt geïnterpreteerd door Power shell als `[System.Object[]]` .

## PARAMETERS

### -Path

Hiermee geeft u het pad op naar een item waarmee `Get-Content` de inhoud wordt opgehaald. Joker tekens zijn toegestaan. De paden moeten paden naar items zijn en niet naar containers. U moet bijvoorbeeld een pad naar een of meer bestanden opgeven, niet een pad naar een map.

```yaml
Type: System.String[]
Parameter Sets: Path
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
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

### -ReadCount

Hiermee geeft u op hoeveel regels met inhoud per keer via de pijp lijn worden verzonden. De standaardwaarde is 1.
Met de waarde 0 (nul) wordt alle inhoud in één keer verzonden.

Met deze para meter wordt de weer gegeven inhoud niet gewijzigd, maar dit is van invloed op de tijd die nodig is om de inhoud weer te geven. Als de waarde van **ReadCount** toeneemt, wordt de tijd die nodig is om de eerste regel te retour neren, maar wordt de totale tijd van de bewerking afgenomen. Dit kan een merkbaar verschil in grote items vormen.

```yaml
Type: System.Int64
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: 1
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -TotalCount

Hiermee geeft u het aantal regels vanaf het begin van een bestand of een ander item op. De standaard waarde is-1 (alle regels).

U kunt de naam van de **totalCount** of de aliassen van de para meter, **First** of **Head** gebruiken.

```yaml
Type: System.Int64
Parameter Sets: (All)
Aliases: First, Head

Required: False
Position: Named
Default value: -1
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -Staart

Hiermee wordt het aantal regels van het einde van een bestand of een ander item opgegeven. U kunt de naam van de para meter van de **staart** of de bijbehorende alias als **laatste** gebruiken. Deze para meter is geïntroduceerd in Power Shell 3,0.

```yaml
Type: System.Int32
Parameter Sets: (All)
Aliases: Last

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -Filter

Hiermee geeft u een filter op om de para meter **Path** te kwalificeren. De [File System](../Microsoft.PowerShell.Core/About/about_FileSystem_Provider.md) -provider is de enige geïnstalleerde Power shell-provider die het gebruik van filters ondersteunt. U kunt de syntaxis voor de filter taal van het **Bestands systeem** in [about_Wildcards](../Microsoft.PowerShell.Core/About/about_Wildcards.md)vinden.
Filters zijn efficiënter dan andere para meters, omdat deze door de provider worden toegepast wanneer de cmdlet de objecten ophaalt in plaats van dat Power shell de objecten heeft gefilterd nadat ze zijn opgehaald.

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

### -Uitsluiten

Hiermee geeft u als een teken reeks matrix een item of items die met deze cmdlet worden uitgesloten in de bewerking.
De waarde van deze para meter komt in aanmerking voor de para meter **Path** .

Voer een element of patroon van een pad in, zoals `*.txt` .
Joker tekens zijn toegestaan.

De **exclude** -para meter is alleen effectief wanneer de inhoud van een item wordt opgenomen, zoals `C:\Windows\*` , waarbij het Joker teken de inhoud van de `C:\Windows` map bevat.

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

### -Force

**Force** overschrijft een alleen-lezen kenmerk of maakt mappen om een bestandspad te volt ooien. De para meter **Forces** probeert geen bestands machtigingen te wijzigen of beveiligings beperkingen te negeren.

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

### -Scheidings teken

Hiermee geeft u het scheidings teken `Get-Content` op dat wordt gebruikt om het bestand in objecten te verdelen terwijl het wordt gelezen. De standaard waarde is `\n` , het einde van de regel. Bij het lezen van een tekst bestand `Get-Content` retourneert een verzameling teken reeks objecten, die allemaal eindigen met een einde van een regel. Wanneer u een scheidings teken opgeeft dat niet voor komt in het bestand, `Get-Content` retourneert het hele bestand als één undelimited-object.

U kunt deze para meter gebruiken om een groot bestand te splitsen in kleinere bestanden door een bestands scheidings teken op te geven als scheidings teken. Het scheidings teken wordt bewaard (niet verwijderd) en wordt het laatste item in elk bestands gedeelte.

**Scheidings teken** is een dynamische para meter die de **File System** provider toevoegt aan de `Get-Content` cmdlet. Deze para meter werkt alleen op stations met een bestands systeem.

> [!NOTE]
> Wanneer de waarde van de para meter voor het **scheidings** teken leeg is, wordt er op dit moment `Get-Content` niets geretourneerd. Dit is een bekend probleem. Als u `Get-Content` wilt forceren om het hele bestand als een enkele, undelimited teken reeks te retour neren. Voer een waarde in die niet voor komt in het bestand.

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: End-of-line character
Accept pipeline input: False
Accept wildcard characters: False
```

### -Wachten

Hiermee blijft het bestand geopend nadat alle bestaande regels zijn uitgevoerd. Tijdens het wachten wordt `Get-Content` het bestand na elke seconde gecontroleerd en worden er nieuwe regels uitgevoerd, indien aanwezig. U kunt de **wacht tijd** onderbreken door op **CTRL + C** te drukken. De wacht tijd eindigt ook als het bestand wordt verwijderd. in dat geval wordt een niet-afsluit fout gerapporteerd.

**Wait** is een dynamische para meter die de File System Provider toevoegt aan de `Get-Content` cmdlet. Deze para meter werkt alleen op stations met een bestands systeem. **Wait** kan niet worden gecombineerd met **RAW**.

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

### -RAW

Hiermee worden tekens voor nieuwe regels genegeerd en wordt de volledige inhoud van een bestand in één teken reeks geretourneerd, waarbij de nieuwe voors worden bewaard. Standaard worden nieuwe regels in een bestand gebruikt als scheidings tekens om de invoer te scheiden in een matrix met teken reeksen. Deze para meter is geïntroduceerd in Power Shell 3,0.

**RAW** is een dynamische para meter die de **File System** provider toevoegt aan de `Get-Content` cmdlet deze para meter werkt alleen in bestandssysteem stations.

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

### -Encoding

Hiermee geeft u het type code ring voor het doel bestand op. De standaardwaarde is `utf8NoBOM`.

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

Encoding is een dynamische para meter die de **File System** provider toevoegt aan de `Get-Content` cmdlet.
Deze para meter is alleen beschikbaar in bestandssysteem stations.

Bij het lezen van en schrijven naar binaire bestanden gebruikt u de para meter **AsByteStream** en de waarde 0 voor de para meter **ReadCount** . Met een **ReadCount** -waarde van 0 wordt het hele bestand in één Lees bewerking gelezen. De standaard waarde voor **ReadCount** , 1, leest één byte per Lees bewerking en converteert elke byte naar een afzonderlijk object, waardoor fouten optreden wanneer u de- `Set-Content` cmdlet gebruikt om de bytes naar een bestand te schrijven, tenzij u de para meter **AsByteStream** gebruikt.

Vanaf Power shell 6,2 kunnen met de para meter **Encoding** ook numerieke id's van geregistreerde code pagina's (zoals `-Encoding 1251` ) of teken reeks namen van geregistreerde code pagina's (zoals) worden toegestaan `-Encoding "windows-1251"` . Zie de .NET-documentatie voor [code ring. code tabel](/dotnet/api/system.text.encoding.codepage?view=netcore-2.2)voor meer informatie.

> [!NOTE]
> **UTF-7** _ wordt niet meer aanbevolen om te gebruiken. In Power shell 7,1 wordt een waarschuwing geschreven als u `utf7` de para meter _ *Encoding** opgeeft.

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

### -Stream

Hiermee wordt de inhoud van de opgegeven alternatieve NTFS-bestands stroom opgehaald uit het bestand. Voer de naam van de stream in.
Jokertekens worden niet ondersteund.

**Stream** is een dynamische para meter die de **File System** provider toevoegt aan de `Get-Content` cmdlet.
Deze para meter werkt alleen in bestandssysteem stations op Windows-systemen. Deze para meter is geïntroduceerd in Windows Power Shell 3,0.

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

### -AsByteStream

Hiermee geeft u op dat de inhoud moet worden gelezen als een byte stroom. De para meter **AsByteStream** is geïntroduceerd in Windows power shell 6,0.

Er treedt een waarschuwing op wanneer u de para meter **AsByteStream** gebruikt met de para meter **Encoding** . De para meter **AsByteStream** negeert elke code ring en de uitvoer wordt geretourneerd als een byte stroom.

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

### CommonParameters

Deze cmdlet biedt ondersteuning voor de algemene para meters: `-Debug` , `-ErrorAction` , `-ErrorVariable` , `-InformationAction` , `-InformationVariable` , `-OutVariable` , `-OutBuffer` , `-PipelineVariable` , `-Verbose` , `-WarningAction` en `-WarningVariable` . Zie [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md)voor meer informatie.

## INVOER

### Systeem. Int64, System. string [], System. Management. Automation. PSCredential

U kunt het lees aantal, het totale aantal, de paden of de referenties door sluizen naar `Get-Content` .

## UITVOER

### System. byte, System. String

`Get-Content` retourneert teken reeksen of bytes. Het uitvoer type is afhankelijk van het type inhoud dat u opgeeft als invoer.

## OPMERKINGEN

De `Get-Content` cmdlet is ontworpen om te werken met de gegevens die door elke provider worden weer gegeven. Gebruik de cmdlet om de providers in uw sessie op te halen `Get-PSProvider` . Zie [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md)voor meer informatie.

## GERELATEERDE KOPPELINGEN

[about_Automatic_Variables](../Microsoft.PowerShell.Core/About/about_Automatic_Variables.md)

[about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md)

[Add-content](Add-Content.md)

[Wissen-inhoud](Clear-Content.md)

[ForEach-object](../Microsoft.PowerShell.Core/ForEach-Object.md)

[Get-PSProvider](Get-PSProvider.md)

[Set-Content](Set-Content.md)

