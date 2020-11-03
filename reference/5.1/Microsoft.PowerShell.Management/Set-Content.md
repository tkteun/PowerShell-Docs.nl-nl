---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 5/14/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/set-content?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Set-Content
ms.openlocfilehash: 897029cab790487f6834d021bfc447060fd39812
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/07/2020
ms.locfileid: "93250561"
---
# Set-Content

## SAMENVATTING
Schrijft nieuwe inhoud of vervangt bestaande inhoud in een bestand.

## SYNTAXIS

### Pad (standaard)

```
Set-Content [-Path] <string[]> [-Value] <Object[]> [-PassThru] [-Filter <string>]
 [-Include <string[]>] [-Exclude <string[]>] [-Force] [-Credential <pscredential>] [-WhatIf]
 [-Confirm] [-UseTransaction] [-NoNewline] [-Encoding <FileSystemCmdletProviderEncoding>]
 [-Stream <string>] [<CommonParameters>]
```

### LiteralPath

```
Set-Content [-Value] <Object[]> -LiteralPath <string[]> [-PassThru] [-Filter <string>]
 [-Include <string[]>] [-Exclude <string[]>] [-Force] [-Credential <pscredential>] [-WhatIf]
 [-Confirm] [-UseTransaction] [-NoNewline] [-Encoding <FileSystemCmdletProviderEncoding>]
 [-Stream <string>] [<CommonParameters>]
```

## BESCHRIJVING

`Set-Content` is een cmdlet voor het verwerken van teken reeksen waarmee nieuwe inhoud wordt geschreven of de inhoud in een bestand wordt vervangen. `Set-Content` vervangt de bestaande inhoud en wijkt af van de `Add-Content` cmdlet waarmee inhoud wordt toegevoegd aan een bestand. Als u inhoud wilt verzenden naar, `Set-Content` kunt u de para meter **Value** gebruiken op de opdracht regel of inhoud verzenden via de pijp lijn.

Zie [Nieuw-item](New-Item.md)als u bestanden of mappen wilt maken voor de volgende voor beelden.

## VOORBEELDEN

### Voor beeld 1: de inhoud van meerdere bestanden in een map vervangen

In dit voor beeld wordt de inhoud voor meerdere bestanden in de huidige map vervangen.

```powershell
Get-ChildItem -Path .\Test*.txt
```

```Output
Test1.txt
Test2.txt
Test3.txt
```

```powershell
Set-Content -Path .\Test*.txt -Value 'Hello, World'
Get-Content -Path .\Test*.txt
```

```Output
Hello, World
Hello, World
Hello, World
```

De `Get-ChildItem` cmdlet gebruikt de para meter **Path** om de **txt** -bestanden weer te geven die beginnen met `Test*` in de huidige map. De `Set-Content` cmdlet gebruikt de para meter **Path** om de bestanden op te geven `Test*.txt` . De **waarde** para meter geeft de teken reeks **Hello, World** waarmee de bestaande inhoud in elk bestand wordt vervangen. Met de `Get-Content` cmdlet wordt de para meter **Path** gebruikt om de bestanden op te geven `Test*.txt` en wordt de inhoud van elk bestand in de Power shell-console weer gegeven.

### Voor beeld 2: een nieuw bestand maken en inhoud schrijven

In dit voor beeld wordt een nieuw bestand gemaakt en worden de huidige datum en tijd naar het bestand geschreven.

```powershell
Set-Content -Path .\DateTime.txt -Value (Get-Date)
Get-Content -Path .\DateTime.txt
```

```Output
1/30/2019 09:55:08
```

`Set-Content` maakt gebruik van de para meters **pad** en **waarde** voor het maken van een nieuw bestand met de naam **DateTime.txt** in de huidige map. De **waarde** para meter wordt gebruikt `Get-Date` om de huidige datum en tijd op te halen.
`Set-Content` schrijft het **DateTime** -object naar het bestand als een teken reeks. De `Get-Content` cmdlet gebruikt de para meter **Path** om de inhoud van **DateTime.txt** in de Power shell-console weer te geven.

### Voor beeld 3: tekst in een bestand vervangen

Met deze opdracht worden alle exemplaren van Word in een bestaand bestand vervangen.

```powershell
Get-Content -Path .\Notice.txt
```

```Output
Warning
Replace Warning with a new word.
The word Warning was replaced.
```

```powershell
(Get-Content -Path .\Notice.txt) |
    ForEach-Object {$_ -Replace 'Warning', 'Caution'} |
        Set-Content -Path .\Notice.txt
Get-Content -Path .\Notice.txt
```

```Output
Caution
Replace Caution with a new word.
The word Caution was replaced.
```

De `Get-Content` cmdlet gebruikt de para meter **Path** om het **Notice.txt** bestand in de huidige map op te geven. De `Get-Content` opdracht wordt verpakt met haakjes zodat de opdracht is voltooid voordat de pijp lijn wordt verzonden.

De inhoud van het **Notice.txt** -bestand wordt naar de-cmdlet verzonden via de pijp lijn `ForEach-Object` .
`ForEach-Object`maakt gebruik van de automatische variabele `$_` en vervangt elke **waarschuwing** telkens **Caution** als dat zo is. De objecten worden naar de-cmdlet verzonden via de pijp lijn `Set-Content` . `Set-Content` gebruikt de para meter **Path** om het **Notice.txt** -bestand op te geven en de bijgewerkte inhoud naar het bestand te schrijven.

Met de laatste `Get-Content` cmdlet wordt de bijgewerkte bestands inhoud weer gegeven in de Power shell-console.

### Voor beeld 4: filters gebruiken met Set-Content

U kunt een filter opgeven voor de `Set-Content` cmdlet. Wanneer u filters gebruikt om de para meter **Path** te kwalificeren, moet u een asterisk ( `*` ) toevoegen om de inhoud van het pad aan te geven.

Met de volgende opdracht stelt u de inhoud alle `*.txt` bestanden in de `C:\Temp` map in op de **waarde** empty.

```powershell
Set-Content -Path C:\Temp\* -Filter *.txt -Value "Empty"
```

## PARAMETERS

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

Hiermee geeft u het type code ring voor het doel bestand op. De standaardwaarde is `Default`.

Encoding is een dynamische para meter waaraan de File System Provider toevoegt `Set-Content` . Deze para meter werkt alleen op stations met een bestands systeem.

De acceptabele waarden voor deze para meter zijn als volgt:

- `Ascii` Maakt gebruik van ASCII-tekenset (7-bits).
- `BigEndianUnicode` Maakt gebruik van UTF-16 met de byte volgorde big endian.
- `BigEndianUTF32` Maakt gebruik van UTF-32 met de byte volgorde big endian.
- `Byte` Codeert een reeks tekens in een reeks bytes.
- `Default` Gebruikt de code ring die overeenkomt met de actieve code tabel van het systeem (meestal ANSI).
- `Oem` Gebruikt de code ring die overeenkomt met de huidige OEM-code tabel van het systeem.
- `String` Hetzelfde als `Unicode` .
- `Unicode` Maakt gebruik van UTF-16 met de byte volgorde little endian.
- `Unknown` Hetzelfde als `Unicode` .
- `UTF7` Maakt gebruik van UTF-7.
- `UTF8` Maakt gebruik van UTF-8.
- `UTF32` Maakt gebruik van UTF-32 met de byte volgorde little endian.

Encoding is een dynamische para meter waaraan de File System Provider toevoegt `Set-Content` . Deze para meter werkt alleen op stations met een bestands systeem.

```yaml
Type: Microsoft.PowerShell.Commands.FileSystemCmdletProviderEncoding
Parameter Sets: (All)
Aliases:
Accepted values: ASCII, BigEndianUnicode, BigEndianUTF32, Byte, Default, OEM, String, Unicode, Unknown, UTF7, UTF8, UTF32

Required: False
Position: Named
Default value: Default
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

Hiermee wordt de cmdlet gedwongen de inhoud van een bestand in te stellen, zelfs als het bestand alleen-lezen is. De implementatie varieert van provider tot provider. Zie [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md)voor meer informatie.
De para meter **Force** overschrijft geen beveiligings beperkingen.

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
Aliases: PSPath

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -Nieuwe regel

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

Retourneert een object dat de inhoud vertegenwoordigt. Deze cmdlet genereert standaard geen uitvoer.

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

Hiermee geeft u het pad op van het item dat de inhoud ontvangt.
Joker tekens zijn toegestaan.

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

Hiermee geeft u een alternatieve gegevens stroom voor inhoud. Als de stroom niet bestaat, wordt deze gemaakt met deze cmdlet. Joker tekens worden niet ondersteund.

**Stream** is een dynamische para meter waaraan de **File System** provider toevoegt `Set-Content` . Deze para meter werkt alleen op stations met een bestands systeem.

U kunt de- `Set-Content` cmdlet gebruiken om de inhoud van de **zone te wijzigen. id** alternatieve gegevens stroom. Dit wordt echter niet aangeraden als een manier om beveiligings controles te elimineren waarmee bestanden die worden gedownload van Internet, worden geblokkeerd. Als u controleert of een gedownload bestand veilig is, gebruikt u de `Unblock-File` cmdlet.

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

### -UseTransaction

Hiermee wordt de opdracht opgenomen in de actieve transactie. Deze parameter is alleen geldig wanneer een transactie wordt uitgevoerd. Zie [about_Transactions](../Microsoft.PowerShell.Core/About/about_Transactions.md)voor meer informatie.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: usetx

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### -Waarde

Hiermee geeft u de nieuwe inhoud voor het item.

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

Deze cmdlet biedt ondersteuning voor de algemene para meters: `-Debug` , `-ErrorAction` , `-ErrorVariable` , `-InformationAction` , `-InformationVariable` , `-OutVariable` , `-OutBuffer` , `-PipelineVariable` , `-Verbose` , `-WarningAction` en `-WarningVariable` .
Zie [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md)voor meer informatie.

## INVOER

### System. object

U kunt een object dat de nieuwe waarde voor het item bevat, door sluizen naar `Set-Content` .

## UITVOER

### Geen of System. String

Wanneer u de para meter **PassThru** gebruikt, `Set-Content` genereert een **System. String** -object dat de inhoud vertegenwoordigt. Anders wordt met deze cmdlet geen uitvoer gegenereerd.

## OPMERKINGEN

- U kunt ook verwijzen naar `Set-Content` de ingebouwde alias `sc` .
  Zie [about_Aliases](../Microsoft.PowerShell.Core/About/about_Aliases.md)voor meer informatie.
- `Set-Content` is ontworpen voor het verwerken van teken reeksen. Als u niet-teken reeks objecten naar `Set-Content` een teken reeks in het pipet zet, wordt het object geconverteerd naar een String voordat het wordt geschreven. Als u objecten naar bestanden wilt schrijven, gebruikt u `Out-File` .
- De `Set-Content` cmdlet is ontworpen om te werken met de gegevens die door elke provider worden weer gegeven. Als u een lijst wilt weer geven van de providers die beschikbaar zijn in uw sessie, typt u `Get-PsProvider` . Zie [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md)voor meer informatie.

## GERELATEERDE KOPPELINGEN

[about_Aliases](../Microsoft.PowerShell.Core/About/about_Aliases.md)

[about_Automatic_Variables. MD](../Microsoft.PowerShell.Core/About/about_Automatic_Variables.md)

[about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md)

[about_Transactions](../Microsoft.PowerShell.Core/About/about_Transactions.md)

[Add-content](Add-Content.md)

[Wissen-inhoud](Clear-Content.md)

[Get-Child item](Get-ChildItem.md)

[Get-Content](Get-Content.md)

[ForEach-object](../Microsoft.PowerShell.Core/ForEach-Object.md)

[Nieuw-item](New-Item.md)
