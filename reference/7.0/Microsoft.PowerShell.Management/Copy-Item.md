---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 08/25/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/copy-item?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Copy-Item
ms.openlocfilehash: 6ddcada506e5bc1ed70615ce32b1481b7d4e9d8b
ms.sourcegitcommit: 33ac34789e86ffb4e7e69453ae38fc0bd24933dd
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 08/26/2020
ms.locfileid: "93251873"
---
# Copy-Item

## SAMENVATTING
Hiermee wordt een item gekopieerd van de ene locatie naar een andere.

## SYNTAXIS

### Pad (standaard)

```
Copy-Item [-Path] <String[]> [[-Destination] <String>] [-Container] [-Force] [-Filter <String>]
 [-Include <String[]>] [-Exclude <String[]>] [-Recurse] [-PassThru] [-Credential <PSCredential>]
 [-WhatIf] [-Confirm] [-FromSession <PSSession>] [-ToSession <PSSession>] [<CommonParameters>]
```

### LiteralPath

```
Copy-Item -LiteralPath <String[]> [[-Destination] <String>] [-Container] [-Force] [-Filter <String>]
 [-Include <String[]>] [-Exclude <String[]>] [-Recurse] [-PassThru] [-Credential <PSCredential>]
 [-WhatIf] [-Confirm] [-FromSession <PSSession>] [-ToSession <PSSession>] [<CommonParameters>]
```

## BESCHRIJVING

Met de `Copy-Item` cmdlet wordt een item gekopieerd van de ene locatie naar een andere locatie in dezelfde naam ruimte.
Het kan bijvoorbeeld een bestand kopiëren naar een map, maar het bestand kan niet worden gekopieerd naar een certificaat station.

Met deze cmdlet worden de gekopieerde items niet geknipt of verwijderd. De specifieke items die de cmdlet kan kopiëren, zijn afhankelijk van de Power shell-provider die het item beschikbaar maakt. Zo kunnen ze bestanden en mappen in een bestandssysteem station en register sleutels en vermeldingen in het register station kopiëren.

Met deze cmdlet kunt u items in dezelfde opdracht kopiëren en een andere naam geven. Als u de naam van een item wilt wijzigen, voert u de nieuwe naam in de waarde van de para meter **doel** . Als u de naam van een item wilt wijzigen en dit niet wilt kopiëren, gebruikt u de `Rename-Item` cmdlet.

## VOORBEELDEN

### Voor beeld 1: een bestand kopiëren naar de opgegeven map

In dit voor beeld wordt het `mar1604.log.txt` bestand naar de `C:\Presentation` map gekopieerd. Het oorspronkelijke bestand wordt niet verwijderd.

```powershell
Copy-Item "C:\Wabash\Logfiles\mar1604.log.txt" -Destination "C:\Presentation"
```

### Voor beeld 2: Mapinhoud kopiëren naar een bestaande map

In dit voor beeld wordt de inhoud van de `C:\Logfiles` map gekopieerd naar de bestaande `C:\Drawings` map. De `Logfiles` map wordt niet gekopieerd.

Als de `Logfiles` map bestanden bevat in submappen, worden deze submappen met hun bestands structuren intact gekopieerd. Standaard is de **container** parameter ingesteld op **True** , waarmee de mapstructuur wordt behouden.

```powershell
Copy-Item -Path "C:\Logfiles\*" -Destination "C:\Drawings" -Recurse
```

> [!NOTE]
> Als u de map wilt toevoegen aan `Logfiles` de kopie, verwijdert u de `\*` uit het **pad**.
> Bijvoorbeeld:
>
> `Copy-Item -Path "C:\Logfiles" -Destination "C:\Drawings" -Recurse`

### Voor beeld 3: Directory en inhoud kopiëren naar een nieuwe map

In dit voor beeld wordt de inhoud van de `C:\Logfiles` Bron Directory gekopieerd en wordt een nieuwe doelmap gemaakt. De nieuwe doelmap `\Logs` wordt gemaakt in `C:\Drawings` .

Als u de naam van de bron directory wilt toevoegen, kopieert u deze naar een bestaande doelmap, zoals wordt weer gegeven in **voor beeld 2**. U kunt ook de nieuwe doelmap een naam hebben die overeenkomt met die van de bron directory.

```powershell
Copy-Item -Path "C:\Logfiles" -Destination "C:\Drawings\Logs" -Recurse
```

> [!NOTE]
> Als het **pad** bevat `\*` , wordt de bestands inhoud van de map, met inbegrip van de mapstructuur structuren, gekopieerd naar de nieuwe doelmap. Bijvoorbeeld:
>
> `Copy-Item -Path "C:\Logfiles\*" -Destination "C:\Drawings\Logs" -Recurse`

### Voor beeld 4: een bestand kopiëren naar de opgegeven map en de naam van het bestand wijzigen

In dit voor beeld wordt de `Copy-Item` cmdlet gebruikt om het `Get-Widget.ps1` script uit de `\\Server01\Share` Directory naar de map te kopiëren `\\Server12\ScriptArchive` . Als onderdeel van de Kopieer bewerking wijzigt de opdracht de item naam van `Get-Widget.ps1` in `Get-Widget.ps1.txt` , zodat deze kan worden toegevoegd aan e-mail berichten.

```powershell
Copy-Item "\\Server01\Share\Get-Widget.ps1" -Destination "\\Server12\ScriptArchive\Get-Widget.ps1.txt"
```

### Voor beeld 5: een bestand naar een externe computer kopiëren

Er wordt een sessie gemaakt met de externe computer met de naam **Server01** met de referentie van `Contoso\User01` en worden de resultaten opgeslagen in de variabele met de naam `$Session` .

De `Copy-Item` cmdlet kopieert `test.log` vanuit de `D:\Folder001` map naar de `C:\Folder001_Copy` map op de externe computer met behulp van de sessie-informatie die is opgeslagen in de `$Session` variabele. Het oorspronkelijke bestand wordt niet verwijderd.

```powershell
$Session = New-PSSession -ComputerName "Server01" -Credential "Contoso\User01"
Copy-Item "D:\Folder001\test.log" -Destination "C:\Folder001_Copy\" -ToSession $Session
```

### Voor beeld 6: een map naar een externe computer kopiëren

Er wordt een sessie gemaakt met de externe computer met de naam **Server01** met de referentie van `Contoso\User01` en worden de resultaten opgeslagen in de variabele met de naam `$Session` .

De `Copy-Item` cmdlet kopieert de `D:\Folder002` map naar de `C:\Folder002_Copy` map op de externe computer met behulp van de sessie-informatie die is opgeslagen in de `$Session` variabele. Submappen of bestanden worden niet gekopieerd zonder de **recursieve** switch te gebruiken.
Met deze bewerking wordt de `Folder002_Copy` map gemaakt als deze nog niet bestaat.

```powershell
$Session = New-PSSession -ComputerName "Server02" -Credential "Contoso\User01"
Copy-Item "D:\Folder002\" -Destination "C:\Folder002_Copy\" -ToSession $Session
```

### Voor beeld 7: de volledige inhoud van een map recursief kopiëren naar een externe computer

Er wordt een sessie gemaakt met de externe computer met de naam **Server01** met de referentie van `Contoso\User01` en worden de resultaten opgeslagen in de variabele met de naam `$Session` .

`Copy-Item`Met de cmdlet wordt de volledige inhoud van de `D:\Folder003` map gekopieerd naar de `C:\Folder003_Copy` map op de externe computer met behulp van de sessie-informatie die is opgeslagen in de `$Session` variabele. De submappen worden gekopieerd met hun bestands structuren. Met deze bewerking wordt de `Folder003_Copy` map gemaakt als deze nog niet bestaat.

```powershell
$Session = New-PSSession -ComputerName "Server04" -Credential "Contoso\User01"
Copy-Item "D:\Folder003\" -Destination "C:\Folder003_Copy\" -ToSession $Session -Recurse
```

### Voor beeld 8: een bestand kopiëren naar een externe computer en de naam van het bestand wijzigen

Er wordt een sessie gemaakt met de externe computer met de naam **Server01** met de referentie van `Contoso\User01` en worden de resultaten opgeslagen in de variabele met de naam `$Session` .

De `Copy-Item` cmdlet kopieert `scriptingexample.ps1` vanuit de `D:\Folder004` map naar de `C:\Folder004_Copy` map op de externe computer met behulp van de sessie-informatie die is opgeslagen in de `$Session` variabele. Als onderdeel van de Kopieer bewerking wijzigt de opdracht de item naam van `scriptingexample.ps1` in `scriptingexample_copy.ps1` , zodat deze kan worden toegevoegd aan e-mail berichten. Het oorspronkelijke bestand wordt niet verwijderd.

```powershell
$Session = New-PSSession -ComputerName "Server04" -Credential "Contoso\User01"
Copy-Item "D:\Folder004\scriptingexample.ps1" -Destination "C:\Folder004_Copy\scriptingexample_copy.ps1" -ToSession $Session
```

### Voor beeld 9: een extern bestand naar de lokale computer kopiëren

Er wordt een sessie gemaakt met de externe computer met de naam **Server01** met de referentie van `Contoso\User01` en worden de resultaten opgeslagen in de variabele met de naam `$Session` .

De `Copy-Item` cmdlet kopieert `test.log` van de externe `C:\MyRemoteData\` naar de lokale `D:\MyLocalData` map met behulp van de sessie-informatie die is opgeslagen in de `$Session` variabele. Het oorspronkelijke bestand wordt niet verwijderd.

```powershell
$Session = New-PSSession -ComputerName "Server01" -Credential "Contoso\User01"
Copy-Item "C:\MyRemoteData\test.log" -Destination "D:\MyLocalData\" -FromSession $Session
```

### Voor beeld 10: de volledige inhoud van een externe map kopiëren naar de lokale computer

Er wordt een sessie gemaakt met de externe computer met de naam **Server01** met de referentie van `Contoso\User01` en worden de resultaten opgeslagen in de variabele met de naam `$Session` .

`Copy-Item`Met de cmdlet wordt de volledige inhoud van de externe `C:\MyRemoteData\scripts` map gekopieerd naar de lokale `D:\MyLocalData` map met behulp van de sessie-informatie die is opgeslagen in de `$Session` variabele. Als de map scripts bestanden bevat in submappen, worden deze submappen gekopieerd met hun bestands structuren.

```powershell
$Session = New-PSSession -ComputerName "Server01" -Credential "Contoso\User01"
Copy-Item "C:\MyRemoteData\scripts" -Destination "D:\MyLocalData\" -FromSession $Session
```

### Voor beeld 11: de volledige inhoud van een externe map recursief kopiëren naar de lokale computer

Er wordt een sessie gemaakt met de externe computer met de naam **Server01** met de referentie van `Contoso\User01` en worden de resultaten opgeslagen in de variabele met de naam `$Session` .

`Copy-Item`Met de cmdlet wordt de volledige inhoud van de externe `C:\MyRemoteData\scripts` map gekopieerd naar de lokale `D:\MyLocalData\scripts` map met behulp van de sessie-informatie die is opgeslagen in de `$Session` variabele. Omdat de **recursie** -para meter wordt gebruikt, maakt de bewerking de map scripts als deze nog niet bestaat. Als de map scripts bestanden bevat in submappen, worden deze submappen gekopieerd met hun bestands structuren.

```powershell
$Session = New-PSSession -ComputerName "Server01" -Credential "Contoso\User01"
Copy-Item "C:\MyRemoteData\scripts" -Destination "D:\MyLocalData\scripts" -FromSession $Session -Recurse
```

### Voor beeld 12: recursief kopiëren van bestanden van een mapstructuur naar de huidige map

In dit voor beeld ziet u hoe u bestanden kopieert van een mapstructuur met meerdere niveaus naar één platte map.
De eerste drie opdrachten tonen de bestaande mappen structuur en de inhoud van twee bestanden, beide namen `file3.txt` .

```powershell
PS C:\temp\test> (Get-ChildItem C:\temp\tree -Recurse).FullName
C:\temp\tree\subfolder
C:\temp\tree\file1.txt
C:\temp\tree\file2.txt
C:\temp\tree\file3.txt
C:\temp\tree\subfolder\file3.txt
C:\temp\tree\subfolder\file4.txt
C:\temp\tree\subfolder\file5.txt

PS C:\temp\test> Get-Content C:\temp\tree\file3.txt
This is file3.txt in the root folder

PS C:\temp\test> Get-Content C:\temp\tree\subfolder\file3.txt
This is file3.txt in the subfolder

PS C:\temp\test> Copy-Item -Path C:\temp\tree -Filter *.txt -Recurse -Container:$false
PS C:\temp\test> (Get-ChildItem . -Recurse).FullName
C:\temp\test\subfolder
C:\temp\test\file1.txt
C:\temp\test\file2.txt
C:\temp\test\file3.txt
C:\temp\test\file4.txt
C:\temp\test\file5.txt

PS C:\temp\test> Get-Content .\file3.txt
This is file3.txt in the subfolder
```

`Copy-Item`Voor de cmdlet is de **container** parameter ingesteld op `$false` . Dit zorgt ervoor dat de inhoud van de bronmap wordt gekopieerd, maar behoudt de mappen structuur niet. U ziet dat bestanden met dezelfde naam worden overschreven in de doelmap.

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

### -Container

Geeft aan dat met deze cmdlet container objecten worden bewaard tijdens de Kopieer bewerking. Standaard is de **container** parameter ingesteld op **True**.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: True
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

### -Bestemming

Hiermee geeft u het pad naar de nieuwe locatie. De standaardwaarde is de huidige map.

Als u de naam van het item dat wordt gekopieerd, wilt wijzigen, geeft u een nieuwe naam op in de waarde van de para meter **Destination** .

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: 1
Default value: Current directory
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

Geeft aan dat deze cmdlet items kopieert die anders niet kunnen worden gewijzigd, zoals het kopiëren over een alleen-lezen bestand of alias.

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

### -FromSession

Hiermee geeft u het **PSSession** -object op waaruit een extern bestand wordt gekopieerd. Wanneer u deze para meter gebruikt, verwijzen de para meters **Path** en **LiteralPath** naar het lokale pad op de externe computer.

```yaml
Type: System.Management.Automation.Runspaces.PSSession
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

### -PassThru

Retourneert een object dat het item vertegenwoordigt waarmee u werkt. Deze cmdlet genereert standaard geen uitvoer.

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

Hiermee wordt een teken reeks matrix opgegeven, het pad naar de items die moeten worden gekopieerd. Joker tekens zijn toegestaan.

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

### -Recursief

Geeft aan dat deze cmdlet een recursieve kopie doet.

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

### -ToSession

Hiermee geeft u het **PSSession** -object op waarnaar een extern bestand wordt gekopieerd. Wanneer u deze para meter gebruikt, verwijst de para meter **Destination** naar het lokale pad op de externe computer.

```yaml
Type: System.Management.Automation.Runspaces.PSSession
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
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

Deze cmdlet biedt ondersteuning voor de algemene para meters: `-Debug` , `-ErrorAction` , `-ErrorVariable` , `-InformationAction` , `-InformationVariable` , `-OutVariable` , `-OutBuffer` , `-PipelineVariable` , `-Verbose` , `-WarningAction` en `-WarningVariable` . Zie [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)voor meer informatie.

## INVOER

### System. String

U kunt een teken reeks met een pad naar deze cmdlet door sluizen.

## UITVOER

### Geen of een object dat het gekopieerde item vertegenwoordigt

Wanneer u de para meter **PassThru** gebruikt, retourneert deze cmdlet een object dat staat voor het gekopieerde item. Anders wordt met deze cmdlet geen uitvoer gegenereerd.

## OPMERKINGEN

Deze cmdlet is ontworpen om te werken met de gegevens die door elke provider worden weer gegeven. Als u een lijst wilt weer geven van de providers die beschikbaar zijn in uw sessie, typt u `Get-PSProvider` . Zie [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md)voor meer informatie.

## GERELATEERDE KOPPELINGEN

[about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md)

[Wissen-item](Clear-Item.md)

[Get-item](Get-Item.md)

[Get-PSProvider](Get-PSProvider.md)

[Invoke-item](Invoke-Item.md)

[Item verplaatsen](Move-Item.md)

[Nieuw-item](New-Item.md)

[Verwijderen-item](Remove-Item.md)

[Naam wijzigen-item](Rename-Item.md)

[Set-item](Set-Item.md)
