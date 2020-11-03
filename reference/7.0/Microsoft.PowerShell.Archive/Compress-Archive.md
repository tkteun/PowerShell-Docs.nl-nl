---
external help file: Microsoft.PowerShell.Archive-help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Archive
ms.date: 02/20/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.archive/compress-archive?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Compress-Archive
ms.openlocfilehash: 1d5379b22cbc9f501d8fdf50da76d82f1122897b
ms.sourcegitcommit: de63e9481cf8024883060aae61fb02c59c2de662
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/03/2020
ms.locfileid: "93249712"
---
# Compress-Archive

## SAMENVATTING
Hiermee maakt u een gecomprimeerd archief of zip-bestand van opgegeven bestanden en mappen.

## SYNTAXIS

### Pad (standaard)

```
Compress-Archive [-Path] <String[]> [-DestinationPath] <String> [-CompressionLevel <String>]
 [-PassThru] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### PathWithUpdate

```
Compress-Archive [-Path] <String[]> [-DestinationPath] <String> [-CompressionLevel <String>] -Update
 [-PassThru] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### PathWithForce

```
Compress-Archive [-Path] <String[]> [-DestinationPath] <String> [-CompressionLevel <String>] -Force
 [-PassThru] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### LiteralPathWithUpdate

```
Compress-Archive -LiteralPath <String[]> [-DestinationPath] <String> [-CompressionLevel <String>]
 -Update [-PassThru] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### LiteralPathWithForce

```
Compress-Archive -LiteralPath <String[]> [-DestinationPath] <String> [-CompressionLevel <String>]
 -Force [-PassThru] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### LiteralPath

```
Compress-Archive -LiteralPath <String[]> [-DestinationPath] <String> [-CompressionLevel <String>]
 [-PassThru] [-WhatIf] [-Confirm] [<CommonParameters>]
```

## BESCHRIJVING

`Compress-Archive`Met de cmdlet maakt u een gecomprimeerd of zip-archief bestand van een of meer opgegeven bestanden of mappen. Een archief verpakt meerdere bestanden, met optionele compressie, in één ZIP-bestand voor eenvoudigere distributie en opslag. Een archief bestand kan worden gecomprimeerd met behulp van het compressie algoritme dat is opgegeven door de para meter **CompressionLevel** .

De `Compress-Archive` cmdlet gebruikt de Microsoft .net-API [System.IO.Compression.ZipArchive](/dotnet/api/system.io.compression.ziparchive) om bestanden te comprimeren.
De maximale bestands grootte is 2 GB omdat de onderliggende API wordt beperkt.

Enkele voor beelden gebruiken splatting om de regel lengte van de code voorbeelden te reduceren. Zie [about_Splatting](../Microsoft.PowerShell.Core/About/about_Splatting.md)voor meer informatie.

## VOORBEELDEN

### Voor beeld 1: bestanden comprimeren om een archief bestand te maken

In dit voor beeld worden bestanden uit verschillende mappen gecomprimeerd en wordt een archief bestand gemaakt. Er wordt een Joker teken gebruikt om alle bestanden met een bepaalde bestands extensie op te halen. Er is geen mapstructuur in het archief bestand, omdat alleen bestands namen worden opgegeven in het **pad** .

```powershell
$compress = @{
  Path = "C:\Reference\Draftdoc.docx", "C:\Reference\Images\*.vsd"
  CompressionLevel = "Fastest"
  DestinationPath = "C:\Archives\Draft.Zip"
}
Compress-Archive @compress
```

De para meter **Path** accepteert specifieke bestands namen en bestands namen met Joker tekens, `*.vsd` . Het **pad** gebruikt een door komma's gescheiden lijst om bestanden uit verschillende mappen op te halen. Het compressie niveau is het **snelst** om de verwerkings tijd te verminderen. De **doelpad** para meter geeft u de locatie voor het `Draft.zip` bestand op. Het `Draft.zip` bestand bevat `Draftdoc.docx` en alle bestanden met een `.vsd` extensie.

### Voor beeld 2: bestanden comprimeren met een LiteralPath

In dit voor beeld worden specifieke benoemde bestanden gecomprimeerd en een nieuw archief bestand gemaakt. Er is geen mapstructuur in het archief bestand, omdat alleen bestands namen worden opgegeven in het **pad** .

```powershell
$compress = @{
LiteralPath= "C:\Reference\Draft Doc.docx", "C:\Reference\Images\diagram2.vsd"
CompressionLevel = "Fastest"
DestinationPath = "C:\Archives\Draft.Zip"
}
Compress-Archive @compress
```

Absolute paden en bestands namen worden gebruikt omdat de para meter **LiteralPath** geen joker tekens accepteert. Het **pad** gebruikt een door komma's gescheiden lijst om bestanden uit verschillende mappen op te halen. Het compressie niveau is het **snelst** om de verwerkings tijd te verminderen. De **doelpad** para meter geeft u de locatie voor het `Draft.zip` bestand op. Het `Draft.zip` bestand bevat alleen `Draftdoc.docx` en `diagram2.vsd` .

### Voor beeld 3: een map comprimeren die de hoofdmap bevat

In dit voor beeld wordt een map gecomprimeerd en wordt een archief bestand gemaakt dat de hoofdmap **bevat** en alle bijbehorende bestanden en submappen. Het archief bestand heeft een mapstructuur, omdat het **pad** een hoofdmap specificeert.

```powershell
Compress-Archive -Path C:\Reference -DestinationPath C:\Archives\Draft.zip
```

`Compress-Archive` gebruikt de para meter **Path** om de hoofdmap op te geven `C:\Reference` . De **doelpad** para meter geeft u de locatie voor het archief bestand op. Het `Draft.zip` archief bevat de `Reference` hoofdmap en alle bijbehorende bestanden en submappen.

### Voor beeld 4: een map comprimeren die de hoofdmap uitsluit

In dit voor beeld wordt een map gecomprimeerd en wordt een archief bestand gemaakt dat de hoofdmap **uitsluit** , omdat het **pad** een asterisk () gebruikt als `*` Joker teken. Het archief bevat een mapstructuur die de bestanden en submappen van de hoofdmap bevat.

```powershell
Compress-Archive -Path C:\Reference\* -DestinationPath C:\Archives\Draft.zip
```

`Compress-Archive` gebruikt de para meter **Path** om de hoofdmap op te geven `C:\Reference` met een asterisk ( `*` ) als Joker teken. De **doelpad** para meter geeft u de locatie voor het archief bestand op. Het `Draft.zip` archief bevat de bestanden en submappen van de hoofdmap. De `Reference` hoofdmap wordt uitgesloten van het archief.

### Voor beeld 5: alleen de bestanden in een hoofdmap comprimeren

In dit voor beeld worden alleen de bestanden in een hoofdmap gecomprimeerd en wordt een archief bestand gemaakt. Er is geen mapstructuur in het archief, omdat alleen bestanden zijn gecomprimeerd.

```powershell
Compress-Archive -Path C:\Reference\*.* -DestinationPath C:\Archives\Draft.zip
```

`Compress-Archive` maakt gebruik van de para meter **Path** om de hoofdmap op te geven, `C:\Reference` met een **sterretje** ( `*.*` ) als Joker teken (). De **doelpad** para meter geeft u de locatie voor het archief bestand op. Het `Draft.zip` archief bevat alleen de `Reference` bestanden van de hoofdmap en de hoofdmap wordt uitgesloten.

### Voor beeld 6: de pijp lijn gebruiken om bestanden te archiveren

In dit voor beeld worden bestanden via de pijp lijn verzonden om een archief te maken. Er is geen mapstructuur in het archief bestand, omdat alleen bestands namen worden opgegeven in het **pad** .

```powershell
Get-ChildItem -Path C:\Reference\Afile.txt, C:\Reference\Images\Bfile.txt |
  Compress-Archive -DestinationPath C:\Archives\PipelineFiles.zip
```

`Get-ChildItem` gebruikt de para meter **Path** om twee bestanden uit verschillende directory's op te geven. Elk bestand wordt vertegenwoordigd door een **file info** -object en de pijp lijn wordt naar beneden verzonden `Compress-Archive` .
De twee opgegeven bestanden worden gearchiveerd in `PipelineFiles.zip` .

### Voor beeld 7: de pijp lijn gebruiken om een map te archiveren

In dit voor beeld wordt een directory door de pijp lijn verzonden om een archief te maken. Bestanden worden als **DirectoryInfo** -objecten verzonden als **file info** -objecten en-mappen. De directory structuur van het archief bevat niet de hoofdmap, maar de bijbehorende bestanden en submappen zijn opgenomen in het archief.

```powershell
Get-ChildItem -Path C:\LogFiles | Compress-Archive -DestinationPath C:\Archives\PipelineDir.zip
```

`Get-ChildItem` maakt gebruik van de para meter **Path** om de hoofdmap op te geven `C:\LogFiles` . Elk **file info** -en **DirectoryInfo** -object wordt via de pijp lijn verzonden.

`Compress-Archive` elk object wordt toegevoegd aan het `PipelineDir.zip` Archief. De para meter **Path** is niet opgegeven omdat de pijplijn objecten worden ontvangen in de parameter positie 0.

### Voor beeld 8: hoe recursie kan invloed hebben op Archief

In dit voor beeld ziet u hoe herhalingen bestanden in uw archief kunnen dupliceren. Als u bijvoorbeeld gebruikt `Get-ChildItem` met de **recursieve** para meter. Als recursieproces worden elk **file info** -en **DirectoryInfo** -object verzonden naar de pijp lijn en toegevoegd aan het archief.

```powershell
Get-ChildItem -Path C:\TestLog -Recurse |
  Compress-Archive -DestinationPath C:\Archives\PipelineRecurse.zip
```

De `C:\TestLog` map bevat geen bestanden. Het bevat een submap met de naam `testsub` die het `testlog.txt` bestand bevat.

`Get-ChildItem` gebruikt de para meter **Path** om de hoofdmap op te geven `C:\TestLog` . Met de **recursieve** para meter worden de bestanden en mappen verwerkt. Er wordt een **DirectoryInfo** -object gemaakt voor `testsub` en een **file info** -object `testlog.txt` .

Elk object wordt naar beneden verzonden in de pijp lijn `Compress-Archive` . De **doelpad** geeft de locatie voor het archief bestand. De para meter **Path** is niet opgegeven omdat de pijplijn objecten worden ontvangen in de parameter positie 0.

In het volgende overzicht wordt de `PipelineRecurse.zip` inhoud van het archief beschreven die een dubbel bestand bevat:

- Het **DirectoryInfo** -object maakt de `testsub` map en bevat het `testlog.txt` bestand dat de oorspronkelijke mapstructuur weerspiegelt.
- Het **file info** -object maakt een duplicaat `testlog.txt` in de hoofdmap van het archief. Het duplicaat bestand is gemaakt, omdat de recursie een bestands object naar heeft verzonden `Compress-Archive` . Dit gedrag wordt verwacht omdat elk object dat via de pijp lijn wordt verzonden, wordt toegevoegd aan het archief.

### Voor beeld 9: een bestaand archief bestand bijwerken

In dit voor beeld wordt een bestaand archief bestand `Draft.Zip` in de `C:\Archives` map bijgewerkt. In dit voor beeld bevat het bestaande archief bestand de hoofdmap en de bijbehorende bestanden en submappen.

```powershell
Compress-Archive -Path C:\Reference -Update -DestinationPath C:\Archives\Draft.Zip
```

De opdracht wordt bijgewerkt `Draft.Zip` met nieuwere versies van bestaande bestanden in de `C:\Reference` map en de bijbehorende submappen. Nieuwe bestanden die zijn toegevoegd aan `C:\Reference` of de submappen daarvan, worden opgenomen in het bijgewerkte `Draft.Zip` Archief.

## PARAMETERS

### -CompressionLevel

Hiermee geeft u op hoeveel compressie moet worden toegepast bij het maken van het archief bestand. Snellere compressie vereist minder tijd om het bestand te maken, maar kan leiden tot grotere bestands grootten.

Als deze para meter niet is opgegeven, gebruikt de opdracht de standaard waarde, **optimaal**.

Hier volgen de geldige waarden voor deze para meter:

- **Snelst**. Gebruik de snelste compressie methode die beschikbaar is om de verwerkings tijd te verminderen. Snellere compressie kan leiden tot grotere bestands grootten.
- Geen **compressie**. De bron bestanden worden niet gecomprimeerd.
- **Optimaal**. De verwerkings tijd is afhankelijk van de bestands grootte.

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:
Accepted values: Optimal, NoCompression, Fastest

Required: False
Position: Named
Default value: Optimal
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

### -Doelpad

Deze para meter is vereist en geeft het pad op naar het uitvoer bestand voor het archief. De **doelpad** moet de naam van het zip-bestand bevatten en ofwel het absolute of relatieve pad naar het zip-bestand.

Als de bestands naam in **doelpad** geen `.zip` bestandsnaam extensie heeft, voegt de cmdlet de `.zip` bestandsnaam extensie toe.

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: True
Position: 1
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Force

Hiermee wordt de opdracht uitgevoerd zonder dat de gebruiker om bevestiging wordt gevraagd.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: PathWithForce, LiteralPathWithForce
Aliases:

Required: True
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### -LiteralPath

Hiermee geeft u het pad of de paden naar de bestanden die u wilt toevoegen aan het gecomprimeerde bestand van het archief. In tegens telling tot de para meter **Path** wordt de waarde van **LiteralPath** precies zo gebruikt als deze wordt getypt. Geen tekens worden geïnterpreteerd als joker tekens. Als het pad escape tekens bevat, moet u elk escape teken tussen enkele aanhalings tekens plaatsen om Power shell te instrueren dat tekens niet worden geïnterpreteerd als escape reeksen.
Als u meerdere paden wilt opgeven en bestanden wilt toevoegen op meerdere locaties in uw uitvoer zip-bestand, gebruikt u komma's om de paden van elkaar te scheiden.

```yaml
Type: System.String[]
Parameter Sets: LiteralPathWithUpdate, LiteralPathWithForce, LiteralPath
Aliases: PSPath

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -PassThru

Zorgt ervoor dat de cmdlet een File-object uitvoert dat het gemaakte archief bestand vertegenwoordigt.

Deze para meter is geïntroduceerd in Power shell 6,0.

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

### -Path

Hiermee geeft u het pad of de paden naar de bestanden die u wilt toevoegen aan het gecomprimeerde bestand van het archief. Als u meerdere paden wilt opgeven en bestanden op meerdere locaties wilt toevoegen, gebruikt u komma's om de paden van elkaar te scheiden.

Deze para meter accepteert joker tekens. Met Joker tekens kunt u alle bestanden in een map toevoegen aan het archief bestand.

Het gebruik van joker tekens met een root directory is van invloed op de inhoud van het archief:

- Als u een archief wilt maken dat de hoofdmap **bevat** en alle bijbehorende bestanden en submappen, geeft u de hoofdmap op in het **pad** zonder joker tekens. Bijvoorbeeld: `-Path C:\Reference`
- Gebruik het Joker teken asterisk () om een archief te maken dat de hoofdmap **uitsluit** , maar zips alle bestanden en submappen `*` . Bijvoorbeeld: `-Path C:\Reference\*`
- Als u een archief wilt maken dat alleen de bestanden in de hoofdmap zips, gebruikt u het Joker teken **Star-punt** ( `*.*` ). Submappen van de hoofdmap worden niet opgenomen in het archief. Bijvoorbeeld: `-Path C:\Reference\*.*`

```yaml
Type: System.String[]
Parameter Sets: Path, PathWithUpdate, PathWithForce
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: True
```

### -Update

Hiermee wordt het opgegeven archief bijgewerkt door oudere versies van bestanden in het archief te vervangen door nieuwere bestands versies die dezelfde naam hebben. U kunt deze para meter ook toevoegen om bestanden toe te voegen aan een bestaand archief.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: PathWithUpdate, LiteralPathWithUpdate
Aliases:

Required: True
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### -WhatIf

Hiermee wordt weergegeven wat er zou gebeuren als u de cmdlet uitvoert. De cmdlet wordt niet uitgevoerd.

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

### System. String

U kunt een teken reeks met een pad naar een of meer bestanden door sluizen.

## UITVOER

### System. IO. file info

De cmdlet retourneert alleen een **file info** -object wanneer u de para meter **PassThru** gebruikt.

## OPMERKINGEN

Door recursie te gebruiken en objecten naar beneden te verzenden, kunnen de bestanden in uw archief worden gedupliceerd. Als u bijvoorbeeld gebruikt `Get-ChildItem` met de **recursieve** para meter, worden elk **file info** -en **DirectoryInfo** -object dat wordt verzonden naar de pijp lijn toegevoegd aan het archief.

De [specificatie zip-bestand](https://pkware.cachefly.net/webdocs/casestudies/APPNOTE.TXT) geeft geen standaard wijze op voor het coderen van bestands namen die niet-ASCII-tekens bevatten. De `Compress-Archive` cmdlet maakt gebruik van UTF-8-code ring. Andere ZIP-archief hulpprogramma's kunnen gebruikmaken van een ander coderings schema. Bij het uitpakken van bestanden met bestands namen die niet met UTF-8-code ring zijn opgeslagen, `Expand-Archive` wordt de onbewerkte waarde gebruikt die in het archief is gevonden. Dit kan resulteren in een bestands naam die verschilt van de bron bestandsnaam die is opgeslagen in het archief.

## GERELATEERDE KOPPELINGEN

[Uitvouwen-archief](Expand-Archive.md)

[Get-Child item](../Microsoft.PowerShell.Management/Get-ChildItem.md)
