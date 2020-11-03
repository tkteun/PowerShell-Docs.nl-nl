---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 04/23/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/add-content?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Add-Content
ms.openlocfilehash: 903c4eb784c1bb86b66766c7dfb563f586545dc1
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/07/2020
ms.locfileid: "93250844"
---
# Add-Content

## SAMENVATTING
Voegt inhoud toe aan de opgegeven items, zoals het toevoegen van woorden aan een bestand.

## SYNTAXIS

### Pad (standaard)

```
Add-Content [-Path] <string[]> [-Value] <Object[]> [-PassThru] [-Filter <string>]
 [-Include <string[]>] [-Exclude <string[]>] [-Force] [-Credential <pscredential>] [-WhatIf]
 [-Confirm] [-UseTransaction] [-NoNewline] [-Encoding <FileSystemCmdletProviderEncoding>]
 [-Stream <string>] [<CommonParameters>]
```

### LiteralPath

```
Add-Content [-Value] <Object[]> -LiteralPath <string[]> [-PassThru] [-Filter <string>]
 [-Include <string[]>] [-Exclude <string[]>] [-Force] [-Credential <pscredential>] [-WhatIf]
 [-Confirm] [-UseTransaction] [-NoNewline] [-Encoding <FileSystemCmdletProviderEncoding>]
 [-Stream <string>] [<CommonParameters>]
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

De `Add-Content` cmdlet gebruikt de para meter **Path** om alle txt-bestanden in de huidige map op te geven. De **exclude** -para meter negeert bestands namen die overeenkomen met het opgegeven patroon. De **waarde** para meter geeft u de teken reeks op die naar de bestanden wordt geschreven.

Gebruik [Get-content](Get-Content.md) om de inhoud van deze bestanden weer te geven.

### Voor beeld 2: een datum toevoegen aan het einde van de opgegeven bestanden

In dit voor beeld wordt de datum toegevoegd aan bestanden in de huidige map en wordt de datum weer gegeven in de Power shell-console.

```powershell
Add-Content -Path .\DateTimeFile1.log, .\DateTimeFile2.log -Value (Get-Date) -PassThru
Get-Content -Path .\DateTimeFile1.log
```

De `Add-Content` cmdlet gebruikt de para meters **pad** en **waarde** om twee nieuwe bestanden in de huidige map te maken. Met de para meter **Value** wordt de `Get-Date` cmdlet opgegeven om de datum op te halen en wordt de datum door gegeven aan `Add-Content` . De `Add-Content` cmdlet schrijft de datum naar elk bestand. De para meter **PassThru** geeft een object door dat het object Date vertegenwoordigt. Omdat er geen andere cmdlet is om het door gegeven object te ontvangen, wordt het weer gegeven in de Power shell-console. Met de `Get-Content` cmdlet wordt het bijgewerkte bestand, DateTimeFile1. log, weer gegeven.

### Voor beeld 3: de inhoud van een opgegeven bestand toevoegen aan een ander bestand

In dit voor beeld wordt de inhoud van een bestand opgehaald en wordt die inhoud toegevoegd aan een ander bestand.

```powershell
Add-Content -Path .\CopyToFile.txt -Value (Get-Content -Path .\CopyFromFile.txt)
Get-Content -Path .\CopyToFile.txt
```

De `Add-Content` cmdlet gebruikt de para meter **Path** om het nieuwe bestand in de huidige map op te geven CopyToFile.txt. De **waarde** para meter gebruikt de `Get-Content` cmdlet om de inhoud van het bestand CopyFromFile.txt te verkrijgen. De haakjes rond de `Get-Content` cmdlet zorgen ervoor dat de opdracht is voltooid voordat de `Add-Content` opdracht wordt gestart. De **waarde** -para meter wordt door gegeven aan `Add-Content` . `Add-Content`Met de cmdlet worden de gegevens toegevoegd aan het CopyToFile.txt-bestand. De `Get-Content` cmdlet geeft het bijgewerkte bestand weer CopyToFile.txt.

### Voor beeld 4: een variabele gebruiken om de inhoud van een opgegeven bestand toe te voegen aan een ander bestand

In dit voor beeld wordt de inhoud van een bestand opgehaald en wordt de inhoud in een variabele opgeslagen. De variabele wordt gebruikt om de inhoud toe te voegen aan een ander bestand.

```powershell
$From = Get-Content -Path .\CopyFromFile.txt
Add-Content -Path .\CopyToFile.txt -Value $From
Get-Content -Path .\CopyToFile.txt
```

`Get-Content`Met de cmdlet wordt de inhoud van CopyFromFile.txt opgehaald en wordt de inhoud in de `$From` variabele opgeslagen. De `Add-Content` cmdlet gebruikt de para meter **Path** om het CopyToFile.txt bestand in de huidige map op te geven. De **waarde** para meter gebruikt de `$From` variabele en geeft de inhoud door aan `Add-Content` . De `Add-Content` cmdlet werkt het CopyToFile.txt-bestand bij. De `Get-Content` cmdlet geeft CopyToFile.txt weer.

### Voor beeld 5: een nieuw bestand maken en inhoud kopiëren

In dit voor beeld wordt een nieuw bestand gemaakt en wordt de inhoud van een bestaand bestand gekopieerd naar het nieuwe bestand.

```powershell
Add-Content -Path .\NewFile.txt -Value (Get-Content -Path .\CopyFromFile.txt)
Get-Content -Path .\NewFile.txt
```

De `Add-Content` cmdlet maakt gebruik van de para meters **pad** en **waarde** voor het maken van een nieuw bestand in de huidige map. De **waarde** para meter gebruikt de `Get-Content` cmdlet om de inhoud van een bestaand bestand te verkrijgen CopyFromFile.txt. De haakjes rond de `Get-Content` cmdlet zorgen ervoor dat de opdracht is voltooid voordat de `Add-Content` opdracht wordt gestart. De **waarde** para meter geeft de inhoud door `Add-Content` waarmee het NewFile.txt bestand wordt bijgewerkt. `Get-Content`Met de cmdlet wordt de inhoud van het nieuwe bestand NewFile.txt weer gegeven.

### Voor beeld 6: inhoud toevoegen aan een alleen-lezen bestand

Met deze opdracht wordt de waarde aan het bestand toegevoegd, zelfs als het kenmerk bestand **IsReadOnly** is ingesteld op True.
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
-ar---        1/28/2019     13:35              0 IsReadOnlyTextFile.txt
```

De `New-Item` cmdlet maakt gebruik van de para meters **Path** en **item** type voor het maken van het bestand IsReadOnlyTextFile.txt in de huidige map. De `Set-ItemProperty` cmdlet gebruikt de para meters **name** en **Value** om de eigenschap **IsReadOnly** van het bestand te wijzigen in True. De `Get-ChildItem` cmdlet geeft aan dat het bestand leeg is (0) en het kenmerk alleen-lezen ( `r` ) heeft. De `Add-Content` cmdlet gebruikt de para meter **Path** om het bestand op te geven. De **waarde** para meter bevat de teken reeks die moet worden toegevoegd aan het bestand. De para meter **Force** schrijft de tekst naar het bestand met het kenmerk alleen-lezen. De `Get-Content` cmdlet gebruikt de para meter **Path** om de inhoud van het bestand weer te geven.

Als u het kenmerk alleen-lezen wilt verwijderen, gebruikt u de `Set-ItemProperty` opdracht met de para meter **Value** ingesteld op `False` .

## PARAMETERS

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

### -Credential

Hiermee geeft u een gebruikers account op dat is gemachtigd om deze actie uit te voeren. Standaard is dit de huidige gebruiker.

Typ een gebruikers naam, zoals **gebruiker01** of **Domain01\User01** , of voer een **PSCredential** -object in, zoals het account dat is gegenereerd door de `Get-Credential` cmdlet. Als u een gebruikers naam typt, wordt u gevraagd een wacht woord op te vragen.

> [!WARNING]
> Deze para meter wordt niet ondersteund door providers die zijn geïnstalleerd met Power shell.

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

De acceptabele waarden voor deze para meter zijn als volgt:

- `Ascii` Maakt gebruik van ASCII-tekenset (7-bits).
- `BigEndianUnicode` Maakt gebruik van UTF-16 met de byte volgorde big endian.
- `BigEndianUTF32` Maakt gebruik van UTF-32 met de byte volgorde big endian.
- `Byte` Codeert een reeks tekens in een reeks bytes.
- `Default` Gebruikt de code ring die overeenkomt met de actieve code tabel van het systeem (meestal ANSI).
- `Oem` Gebruikt de code ring die overeenkomt met de huidige OEM-code tabel van het systeem.
- `String` Hetzelfde als **Unicode**.
- `Unicode` Maakt gebruik van UTF-16 met de byte volgorde little endian.
- `Unknown` Hetzelfde als **Unicode**.
- `UTF7` Maakt gebruik van UTF-7.
- `UTF8` Maakt gebruik van UTF-8.
- `UTF32` Maakt gebruik van UTF-32 met de byte volgorde little endian.

Encoding is een dynamische para meter die de File System Provider toevoegt aan de `Add-Content` cmdlet. Deze para meter werkt alleen op stations met een bestands systeem.

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

De opgegeven items worden wegge laten. De waarde van deze para meter komt in aanmerking voor de para meter **Path** . Voer een element of patroon van een pad in, zoals **\* . txt**. Joker tekens zijn toegestaan.

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

Hiermee geeft u een filter op in de indeling of taal van de provider. De waarde van deze para meter komt in aanmerking voor de para meter **Path** . De syntaxis van het filter, inclusief het gebruik van joker tekens, is afhankelijk van de provider. **Filters** zijn efficiënter dan andere para meters omdat de provider filters toepast wanneer objecten worden opgehaald. Als dat niet het geval is, worden filters door Power shell verwerkt nadat de objecten zijn opgehaald.

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

Voegt alleen de opgegeven items toe. De waarde van deze para meter komt in aanmerking voor de para meter **Path** . Voer een element of patroon van een pad in, zoals **\* . txt**. Joker tekens zijn toegestaan.

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

Hiermee geeft u het pad op naar de items die de extra inhoud ontvangen. In tegens telling tot **Path** wordt de waarde van **LiteralPath** precies zo gebruikt als deze wordt getypt. Geen tekens worden geïnterpreteerd als joker tekens. Als het pad escape tekens bevat, plaatst u het tussen enkele aanhalings tekens. Enkele aanhalings tekens geven aan dat Power shell geen karakters interpreteert als escape reeksen.

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

Hiermee geeft u het pad op naar de items die de extra inhoud ontvangen. Joker tekens zijn toegestaan. Als u meerdere paden opgeeft, gebruikt u komma's om de paden van elkaar te scheiden.

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

**Stream** is een dynamische para meter waaraan de File System Provider toevoegt `Add-Content` . Deze para meter werkt alleen op stations met een bestands systeem.

U kunt de- `Add-Content` cmdlet gebruiken om de inhoud van de **zone te wijzigen. id** alternatieve gegevens stroom. Dit wordt echter niet aangeraden als een manier om beveiligings controles te elimineren waarmee bestanden die worden gedownload van Internet, worden geblokkeerd. Als u controleert of een gedownload bestand veilig is, gebruikt u de `Unblock-File` cmdlet.

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

Hiermee geeft u de inhoud moet worden toegevoegd. Typ een teken reeks tussen aanhalings tekens, zoals **deze gegevens zijn alleen voor intern gebruik** , of geef een object op dat inhoud bevat, zoals het **DateTime** -object dat `Get-Date` genereert.

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

Deze cmdlet biedt ondersteuning voor de algemene para meters: `-Debug` , `-ErrorAction` , `-ErrorVariable` , `-InformationAction` , `-InformationVariable` , `-OutVariable` , `-OutBuffer` , `-PipelineVariable` , `-Verbose` , `-WarningAction` en `-WarningVariable` . Zie [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)voor meer informatie.

## INVOER

### System. object, System. Management. Automation. PSCredential

U kunt waarden, paden of referenties door sluizen naar `Set-Content` .

## UITVOER

### Geen of System. String

Wanneer u de para meter **PassThru** gebruikt, `Add-Content` genereert een **System. String** -object dat de inhoud vertegenwoordigt. Anders wordt met deze cmdlet geen uitvoer gegenereerd.

## OPMERKINGEN

Wanneer u een object pipet naar `Add-Content` , wordt het object geconverteerd naar een teken reeks voordat het aan het item wordt toegevoegd. Het object type bepaalt de teken reeks notatie, maar de notatie kan afwijken van de standaard weergave van het object. Als u de teken reeks indeling wilt beheren, gebruikt u de opmaak parameters van de verzenden-cmdlet.

U kunt ook verwijzen naar `Add-Content` de ingebouwde alias `ac` . Zie [about_Aliases](../Microsoft.PowerShell.Core/About/about_Aliases.md)voor meer informatie.

De `Add-Content` cmdlet is ontworpen om te werken met de gegevens die door elke provider worden weer gegeven. Als u een lijst wilt weer geven van de providers die beschikbaar zijn in uw sessie, typt u `Get-PSProvider` . Zie [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md)voor meer informatie.

## GERELATEERDE KOPPELINGEN

[about_Aliases](../Microsoft.PowerShell.Core/About/about_Aliases.md)

[about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md)

[about_Transactions](../Microsoft.PowerShell.Core/About/about_Transactions.md)

[Wissen-inhoud](Clear-Content.md)

[Get-Content](Get-Content.md)

[Get-item](Get-Item.md)

[Nieuw-item](New-Item.md)

[Set-Content](Set-Content.md)
