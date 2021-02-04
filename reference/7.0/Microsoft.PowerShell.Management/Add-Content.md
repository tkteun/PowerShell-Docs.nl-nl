---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 12/18/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/add-content?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Add-Content
ms.openlocfilehash: e31e792a60cd09d35ecc67263f107584857efe7d
ms.sourcegitcommit: bf07cffb2a66dec94bf3576e197090f958701f18
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 12/19/2020
ms.locfileid: "97693030"
---
# Add-Content

## SAMENVATTING
Voegt inhoud toe aan de opgegeven items, zoals het toevoegen van woorden aan een bestand.

## SYNTAXIS

### Pad (standaard)

```
Add-Content [-Path] <string[]> [-Value] <Object[]> [-PassThru] [-Filter <string>]
 [-Include <string[]>] [-Exclude <string[]>] [-Force] [-Credential <pscredential>] [-WhatIf]
 [-Confirm] [-NoNewline] [-Encoding <Encoding>] [-AsByteStream] [-Stream <string>]
 [<CommonParameters>]
```

### LiteralPath

```
Add-Content [-Value] <Object[]> -LiteralPath <string[]> [-PassThru] [-Filter <string>]
 [-Include <string[]>] [-Exclude <string[]>] [-Force] [-Credential <pscredential>] [-WhatIf]
 [-Confirm] [-NoNewline] [-Encoding <Encoding>] [-AsByteStream] [-Stream <string>]
 [<CommonParameters>]
```

## BESCHRIJVING

De `Add-Content` cmdlet voegt inhoud toe aan een opgegeven item of bestand. U kunt de inhoud opgeven door de inhoud in de opdracht te typen of door een object op te geven dat de inhoud bevat.

Zie [Nieuw-item](New-Item.md)als u bestanden of mappen wilt maken voor de volgende voor beelden.

## VOORBEELDEN

### Voor beeld 1: een teken reeks toevoegen aan alle tekst bestanden met een uitzonde ring

In dit voor beeld wordt een waarde aan tekst bestanden in de huidige map toegevoegd, maar worden bestanden uitgesloten op basis van de bestands naam.

```powershell
Add-Content -Path .\*.txt -Exclude help* -Value 'End of file'
```

De para meter **Path** geeft alle `.txt` bestanden in de huidige map op, maar de **exclude** -para meter negeert bestands namen die overeenkomen met het opgegeven patroon. De **waarde** para meter geeft u de teken reeks op die naar de bestanden wordt geschreven.

### Voor beeld 2: een datum toevoegen aan het einde van de opgegeven bestanden

In dit voor beeld wordt de datum toegevoegd aan bestanden in de huidige map en wordt de datum weer gegeven in de Power shell-console.

```powershell
Add-Content -Path .\DateTimeFile1.log, .\DateTimeFile2.log -Value (Get-Date) -PassThru
Get-Content -Path .\DateTimeFile1.log
```

```Output
Tuesday, May 14, 2019 8:24:27 AM
Tuesday, May 14, 2019 8:24:27 AM
5/14/2019 8:24:27 AM
```

De `Add-Content` cmdlet maakt twee nieuwe bestanden in de huidige map. De **waarde** -para meter bevat de uitvoer van de `Get-Date` cmdlet. De para meter **PassThru** voert de toegevoegde inhoud uit naar de pijp lijn.
Omdat er geen andere cmdlet is om de uitvoer te ontvangen, wordt deze weer gegeven in de Power shell-console.
Met de `Get-Content` cmdlet wordt het bijgewerkte bestand weer gegeven, `DateTimeFile1.log` .

### Voor beeld 3: de inhoud van een opgegeven bestand toevoegen aan een ander bestand

In dit voor beeld wordt de inhoud van een bestand opgehaald en wordt de inhoud in een variabele opgeslagen. De variabele wordt gebruikt om de inhoud toe te voegen aan een ander bestand.

```powershell
$From = Get-Content -Path .\CopyFromFile.txt
Add-Content -Path .\CopyToFile.txt -Value $From
Get-Content -Path .\CopyToFile.txt
```

- `Get-Content`Met de cmdlet wordt de inhoud van opgehaald `CopyFromFile.txt` en wordt de inhoud in de `$From` variabele opgeslagen.
- De `Add-Content` cmdlet werkt het `CopyToFile.txt` bestand bij met de inhoud van de `$From` variabele.
- De `Get-Content` cmdlet geeft CopyToFile.txt weer.

### Voor beeld 4: de inhoud van een opgegeven bestand toevoegen aan een ander bestand met behulp van de pijp lijn

In dit voor beeld wordt de inhoud van een bestand opgehaald en wordt deze naar de cmdlet gesluizen `Add-Content` .

```powershell
Get-Content -Path .\CopyFromFile.txt | Add-Content -Path .\CopyToFile.txt
Get-Content -Path .\CopyToFile.txt
```

`Get-Content`Met de cmdlet wordt de inhoud van opgehaald `CopyFromFile.txt` . De resultaten worden door gegeven aan de `Add-Content` cmdlet, waarmee de wordt bijgewerkt `CopyToFile.txt` .
De laatste `Get-Content` cmdlet wordt weer gegeven `CopyToFile.txt` .

### Voor beeld 5: een nieuw bestand maken en inhoud kopiëren

In dit voor beeld wordt een nieuw bestand gemaakt en wordt de inhoud van een bestaand bestand gekopieerd naar het nieuwe bestand.

```powershell
Add-Content -Path .\NewFile.txt -Value (Get-Content -Path .\CopyFromFile.txt)
Get-Content -Path .\NewFile.txt
```

- De `Add-Content` cmdlet maakt gebruik van de para meters **pad** en **waarde** voor het maken van een nieuw bestand in de huidige map.
- Met de `Get-Content` cmdlet wordt de inhoud van een bestaand bestand opgehaald `CopyFromFile.txt` en door gegeven aan de **waarde** -para meter. De haakjes rond de `Get-Content` cmdlet zorgen ervoor dat de opdracht is voltooid voordat de `Add-Content` opdracht wordt gestart.
- `Get-Content`Met de cmdlet wordt de inhoud van het nieuwe bestand weer gegeven `NewFile.txt` .

### Voor beeld 6: inhoud toevoegen aan een alleen-lezen bestand

Met deze opdracht wordt een waarde aan het bestand toegevoegd, zelfs als het kenmerk bestand **IsReadOnly** is ingesteld op **True**.
De stappen voor het maken van een alleen-lezen bestand zijn opgenomen in het voor beeld.

```powershell
New-Item -Path .\IsReadOnlyTextFile.txt -ItemType File
Set-ItemProperty -Path .\IsReadOnlyTextFile.txt -Name IsReadOnly -Value $True
Get-ChildItem -Path .\IsReadOnlyTextFile.txt
Add-Content -Path .\IsReadOnlyTextFile.txt -Value 'Add value to read-only text file' -Force
Get-Content -Path .\IsReadOnlyTextFile.txt
```

```Output
Mode                LastWriteTime         Length Name
----                -------------         ------ ----
-ar--         1/28/2019     13:35              0 IsReadOnlyTextFile.txt
```

- De `New-Item` cmdlet gebruikt de para meter **Path** en **item** type om het bestand `IsReadOnlyTextFile.txt` in de huidige map te maken.
- De `Set-ItemProperty` cmdlet gebruikt de para meters **name** en **Value** om de eigenschap **IsReadOnly** van het bestand te wijzigen in True.
- De `Get-ChildItem` cmdlet geeft aan dat het bestand leeg is (0) en het kenmerk alleen-lezen ( `r` ) heeft.
- De `Add-Content` cmdlet gebruikt de para meter **Path** om het bestand op te geven. De **waarde** para meter bevat de teken reeks die moet worden toegevoegd aan het bestand. De para meter **Force** schrijft de tekst naar het bestand met het kenmerk alleen-lezen.
- De `Get-Content` cmdlet gebruikt de para meter **Path** om de inhoud van het bestand weer te geven.

Als u het kenmerk alleen-lezen wilt verwijderen, gebruikt u de `Set-ItemProperty` opdracht met de para meter **Value** ingesteld op `False` .

### Voor beeld 7: filters gebruiken met Add-Content

U kunt een filter opgeven voor de `Add-Content` cmdlet. Wanneer u filters gebruikt om de para meter **Path** te kwalificeren, moet u een asterisk ( `*` ) toevoegen om de inhoud van het pad aan te geven.

Met de volgende opdracht wordt het woord ' gereed ' toegevoegd aan de inhoud van alle `*.txt` bestanden in de `C:\Temp` map.

```powershell
Add-Content -Path C:\Temp\* -Filter *.txt -Value "Done"
```

## PARAMETERS

### -AsByteStream

Hiermee geeft u op dat de inhoud moet worden gelezen als een byte stroom. Deze para meter is geïntroduceerd in Power shell 6,0.

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
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -Encoding

Hiermee geeft u het type code ring voor het doel bestand op. De standaardwaarde is `utf8BOM`.

Encoding is een dynamische para meter die de File System Provider toevoegt aan de `Add-Content` cmdlet. Deze para meter werkt alleen op stations met een bestands systeem.

De acceptabele waarden voor deze para meter zijn als volgt:

- `ascii`: Gebruikt de code ring voor de ASCII-tekenset (7-bits).
- `bigendianunicode`: Wordt gecodeerd in UTF-16-indeling met behulp van de byte volgorde big endian.
- `oem`: Maakt gebruik van de standaard codering voor MS-DOS-en console Programma's.
- `unicode`: Wordt gecodeerd in UTF-16-indeling met behulp van de byte volgorde little endian.
- `utf7`: Wordt gecodeerd in de indeling UTF-7.
- `utf8`: Wordt gecodeerd in UTF-8-indeling.
- `utf8BOM`: Code ring in UTF-8-indeling met byte order Mark (BOM)
- `utf8NoBOM`: Code ring in UTF-8-indeling zonder byte order Mark (BOM)
- `utf32`: Gecodeerd in UTF-32-indeling.

Vanaf Power shell 6,2 kunnen met de para meter **Encoding** ook numerieke id's van geregistreerde code pagina's (zoals `-Encoding 1251` ) of teken reeks namen van geregistreerde code pagina's (zoals) worden toegestaan `-Encoding "windows-1251"` . Zie de .NET-documentatie voor [code ring. code tabel](/dotnet/api/system.text.encoding.codepage?view=netcore-2.2)voor meer informatie.

```yaml
Type: System.Text.Encoding
Parameter Sets: (All)
Aliases:
Accepted values: ASCII, BigEndianUnicode, OEM, Unicode, UTF7, UTF8, UTF8BOM, UTF8NoBOM, UTF32

Required: False
Position: Named
Default value: UTF8NoBOM
Accept pipeline input: False
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

### -Force

Onderdrukt het kenmerk alleen-lezen, zodat u inhoud kunt toevoegen aan een alleen-lezen bestand. **Forceert** bijvoorbeeld het kenmerk alleen-lezen of maakt mappen om een bestandspad te volt ooien, maar er wordt geen poging gedaan om bestands machtigingen te wijzigen.

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
Parameter Sets: LiteralPath
Aliases: PSPath, LP

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -Nieuwe regel

Geeft aan dat met deze cmdlet geen nieuwe regel wordt toegevoegd of het retour neren naar de inhoud.

De teken reeks representaties van de invoer objecten worden samengevoegd om de uitvoer te vormen. Er worden geen spaties of nieuwe regels tussen de uitvoer teken reeksen ingevoegd. Er wordt geen nieuwe regel toegevoegd na de laatste uitvoer teken reeks.

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

### -PassThru

Retourneert een object dat de toegevoegde inhoud vertegenwoordigt. Deze cmdlet genereert standaard geen uitvoer.

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

### -Path

Hiermee geeft u het pad op naar de items die de extra inhoud ontvangen.
Joker tekens zijn toegestaan.
De paden moeten paden naar items zijn en niet naar containers.
U moet bijvoorbeeld een pad naar een of meer bestanden opgeven, niet een pad naar een map.
Als u meerdere paden opgeeft, gebruikt u komma's om de paden van elkaar te scheiden.

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

### -Stream

> [!NOTE]
> Deze para meter is alleen beschikbaar in Windows.

Hiermee geeft u een alternatieve gegevens stroom voor inhoud. Als de stroom niet bestaat, wordt deze gemaakt met deze cmdlet. Joker tekens worden niet ondersteund.

**Stream** is een dynamische para meter waaraan de File System Provider toevoegt `Add-Content` . Deze para meter werkt alleen op stations met een bestands systeem.

U kunt de `Add-Content` cmdlet gebruiken om de inhoud van een andere gegevens stroom te wijzigen, zoals `Zone.Identifier` . Dit wordt echter niet aangeraden als een manier om beveiligings controles te elimineren waarmee bestanden die worden gedownload van Internet, worden geblokkeerd. Als u controleert of een gedownload bestand veilig is, gebruikt u de `Unblock-File` cmdlet.

Deze para meter is geïntroduceerd in Power Shell 3,0.

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

### -Waarde

Hiermee geeft u de inhoud moet worden toegevoegd. Typ een teken reeks tussen aanhalings tekens, zoals **deze gegevens zijn alleen voor intern gebruik**, of geef een object op dat inhoud bevat, zoals het **DateTime** -object dat `Get-Date` genereert.

U kunt de inhoud van een bestand niet opgeven door het bijbehorende pad te typen, omdat het pad alleen een teken reeks is.
U kunt een `Get-Content` opdracht gebruiken om de inhoud op te halen en door te geven aan de **waarde** -para meter.

```yaml
Type: System.Object[]
Parameter Sets: (All)
Aliases:

Required: True
Position: 1
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
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

### System. object, System. Management. Automation. PSCredential

U kunt waarden, paden of referenties door sluizen naar `Set-Content` .

## UITVOER

### Geen of System. String

Wanneer u de para meter **PassThru** gebruikt, `Add-Content` genereert een **System. String** -object dat de inhoud vertegenwoordigt. Anders wordt met deze cmdlet geen uitvoer gegenereerd.

## OPMERKINGEN

- Wanneer u een object pipet naar `Add-Content` , wordt het object geconverteerd naar een teken reeks voordat het aan het item wordt toegevoegd. Het object type bepaalt de teken reeks notatie, maar de notatie kan afwijken van de standaard weergave van het object. Als u de teken reeks indeling wilt beheren, gebruikt u de opmaak parameters van de verzenden-cmdlet.
- U kunt ook verwijzen naar `Add-Content` de ingebouwde alias `ac` . Zie [about_Aliases](../Microsoft.PowerShell.Core/About/about_Aliases.md)voor meer informatie.
- De `Add-Content` cmdlet is ontworpen om te werken met de gegevens die door elke provider worden weer gegeven. Als u een lijst wilt weer geven van de providers die beschikbaar zijn in uw sessie, typt u `Get-PSProvider` . Zie [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md)voor meer informatie.

## GERELATEERDE KOPPELINGEN

[about_Aliases](../Microsoft.PowerShell.Core/About/about_Aliases.md)

[about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md)

[Wissen-inhoud](Clear-Content.md)

[Get-Content](Get-Content.md)

[Get-item](Get-Item.md)

[Nieuw-item](New-Item.md)

[Set-Content](Set-Content.md)
