---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 05/14/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/move-item?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Move-Item
ms.openlocfilehash: a47c017371fe5fe87618c11551cd1ecba76d5c60
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 11/17/2020
ms.locfileid: "94706041"
---
# Move-Item

## SAMENVATTING
Hiermee verplaatst u een item van de ene locatie naar een andere.

## SYNTAXIS

### Pad (standaard)

```
Move-Item [-Path] <String[]> [[-Destination] <String>] [-Force] [-Filter <String>] [-Include <String[]>]
 [-Exclude <String[]>] [-PassThru] [-Credential <PSCredential>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### LiteralPath

```
Move-Item -LiteralPath <String[]> [[-Destination] <String>] [-Force] [-Filter <String>] [-Include <String[]>]
 [-Exclude <String[]>] [-PassThru] [-Credential <PSCredential>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

## BESCHRIJVING

`Move-Item`Met de cmdlet wordt een item, inclusief eigenschappen, inhoud en onderliggende items, verplaatst van de ene locatie naar een andere locatie. De locaties moeten door dezelfde provider worden ondersteund.
Zo kunt u een bestand of submap van de ene map naar de andere verplaatsen of een registersubsleutel van de ene naar de andere sleutel verplaatsen.
Wanneer u een item verplaatst, wordt het toegevoegd aan de nieuwe locatie en verwijderd uit de oorspronkelijke locatie.

## VOORBEELDEN

### Voor beeld 1: een bestand verplaatsen naar een andere map en de naam wijzigen

Met deze opdracht `Test.txt` wordt het bestand van het `C:` station verplaatst naar de `E:\Temp` map en wordt de naam gewijzigd van `test.txt` in `tst.txt` .

```powershell
Move-Item -Path C:\test.txt -Destination E:\Temp\tst.txt
```

### Voor beeld 2: een map en de inhoud naar een andere map verplaatsen

Met deze opdracht verplaatst `C:\Temp` u de map en de inhoud ervan naar de `C:\Logs` map.
De map Temp en alle bijbehorende submappen en bestanden, worden weer gegeven in de map logs.

```powershell
Move-Item -Path C:\Temp -Destination C:\Logs
```

### Voor beeld 3: alle bestanden van een opgegeven extensie verplaatsen van de huidige map naar een andere map

Met deze opdracht worden alle tekst bestanden ( `*.txt` ) in de huidige map (aangeduid door een punt ( `.` )) naar de `C:\Logs` map verplaatst.

```powershell
Move-Item -Path .\*.txt -Destination C:\Logs
```

### Voor beeld 4: alle bestanden van een opgegeven extensie recursief verplaatsen vanuit de huidige map naar een andere map

Met deze opdracht worden alle tekst bestanden van de huidige map en alle submappen, recursief, naar de map C:\TextFiles verplaatst.

```powershell
Get-ChildItem -Path ".\*.txt" -Recurse | Move-Item -Destination "C:\TextFiles"
```

De opdracht gebruikt de `Get-ChildItem` cmdlet om alle onderliggende items in de huidige map op te halen (vertegenwoordigd door de punt \[ \] ) en de bijbehorende submappen met de *bestandsnaam extensie. txt. Hierbij wordt gebruikgemaakt van de para meter **recursieve** om het ophalen van recursie en de para meter include te beperken tot het ophalen van '*. txt ' bestanden.

De pijplijn operator ( `|` ) verzendt de resultaten van deze opdracht naar `Move-Item` , die de tekst bestanden verplaatst naar de map ' TextFiles '.

Als bestanden die worden verplaatst naar ' C:\Textfiles ' dezelfde naam hebben, `Move-Item` wordt er een fout weer gegeven en wordt de functie voortgezet, maar wordt slechts één bestand met elke naam verplaatst naar ' C:\Textfiles '.
De andere bestanden blijven in de oorspronkelijke mappen staan.

Als de map ' textfiles ' (of een ander element van het doelpad) niet bestaat, mislukt de opdracht.
De ontbrekende map wordt niet voor u gemaakt, zelfs niet als u de para meter **Forces** gebruikt.
`Move-Item` Hiermee wordt het eerste item verplaatst naar een bestand met de naam ' textfiles ' en wordt er een fout weer gegeven waarin wordt uitgelegd dat het bestand al bestaat.

Ook worden `Get-ChildItem` verborgen bestanden standaard niet verplaatst.
Als u verborgen bestanden wilt verplaatsen, gebruikt u de para meter **Force** with `Get-ChildItem` .

> [!NOTE]
> Bij het gebruik van de **recursieve** para meter van de cmdlet in Windows power Shell 2,0 `Get-ChildItem` moet de waarde van de para meter **Path** een container zijn.
> Gebruik de para meter **include** om het txt-bestand met de extensie filter () op te geven `Get-ChildItem -Path .\* -Include *.txt -Recurse | Move-Item -Destination C:\TextFiles` .

### Voor beeld 5: register sleutels en-waarden naar een andere sleutel verplaatsen

Met deze opdracht verplaatst u de register sleutels en-waarden in de register sleutel ' mijn bedrijf ' in `HKLM\Software` naar de sleutel ' MyNewCompany '.
Het Joker teken ( `*` ) geeft aan dat de inhoud van de sleutel ' mijn bedrijf ' moet worden verplaatst, niet de sleutel zelf.
In deze opdracht worden de namen van de optionele **paden** en **doel** parameters wegge laten.

```powershell
Move-Item "HKLM:\software\mycompany\*" "HKLM:\software\mynewcompany"
```

### Voor beeld 6: een map en de inhoud ervan verplaatsen naar een submap van de opgegeven map

Met deze opdracht wordt de map ' logs \[ Sept \` 06 \] ' (en de inhoud ervan) verplaatst naar de map ' logs \[ 2006 \] '.

```powershell
Move-Item -LiteralPath 'Logs[Sept`06]' -Destination 'Logs[2006]'
```

De para meter **LiteralPath** wordt gebruikt in plaats van het **pad**, omdat de naam van de oorspronkelijke map links van het haakje en rechter vier Kante tekens (" \[ " en " \] ") bevat.
Het pad bevindt zich ook tussen enkele aanhalings tekens (' '), zodat het apostroffen-symbool ( \` ) niet wordt geïnterpreteerd.

Voor de para meter **Destination** is geen letterlijk pad vereist, omdat de doel variabele ook tussen enkele aanhalings tekens moet worden geplaatst, omdat deze haakjes bevat die kunnen worden geïnterpreteerd.

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
Default value: Current user
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -Bestemming

Hiermee geeft u het pad op naar de locatie waar de items worden verplaatst.
De standaardwaarde is de huidige map.
Joker tekens zijn toegestaan, maar in het resultaat moet één locatie worden opgegeven.

Als u de naam van het item dat wordt verplaatst, wilt wijzigen, geeft u een nieuwe naam op in de waarde van de para meter **Destination** .

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: 1
Default value: Current directory
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: True
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

Hiermee wordt de opdracht uitgevoerd zonder dat de gebruiker om bevestiging wordt gevraagd.
De implementatie varieert van provider tot provider.
Zie [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md)voor meer informatie.

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

Retourneert een object dat het item vertegenwoordigt waarmee u werkt.
Deze cmdlet genereert standaard geen uitvoer.

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

Hiermee geeft u het pad op naar de huidige locatie van de items.
De standaardwaarde is de huidige map.
Joker tekens zijn toegestaan.

```yaml
Type: System.String[]
Parameter Sets: Path
Aliases:

Required: True
Position: 0
Default value: Current directory
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: True
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

Hiermee wordt weergegeven wat er zou gebeuren als u de cmdlet uitvoert.
De cmdlet wordt niet uitgevoerd.

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

Deze cmdlet biedt ondersteuning voor de algemene para meters: `-Debug` , `-ErrorAction` , `-ErrorVariable` , `-InformationAction` , `-InformationVariable` , `-OutVariable` , `-OutBuffer` , `-PipelineVariable` , `-Verbose` , `-WarningAction` en `-WarningVariable` . Zie [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md)voor meer informatie.

## INVOER

### System. String

U kunt een teken reeks met een pad naar deze cmdlet door sluizen.

## UITVOER

### Geen of een object dat het verplaatste item vertegenwoordigt

Wanneer u de para meter *PassThru* gebruikt, genereert deze cmdlet een object dat het verplaatste item vertegenwoordigt.
Anders wordt met deze cmdlet geen uitvoer gegenereerd.

## OPMERKINGEN

- Met deze cmdlet worden bestanden verplaatst tussen de stations die worden ondersteund door dezelfde provider, maar worden mappen alleen verplaatst binnen hetzelfde station.
- Omdat een `Move-Item` opdracht de eigenschappen, inhoud en onderliggende items van een item verplaatst, zijn alle verplaatsingen standaard recursief.
- Deze cmdlet is ontworpen om te werken met de gegevens die door elke provider worden weer gegeven.
  Als u een lijst wilt weer geven van de providers die beschikbaar zijn in uw sessie, typt u `Get-PSProvider` .
  Zie [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md)voor meer informatie.

## GERELATEERDE KOPPELINGEN

[Wissen-item](Clear-Item.md)

[Kopie-item](Copy-Item.md)

[Get-item](Get-Item.md)

[Invoke-item](Invoke-Item.md)

[Nieuw-item](New-Item.md)

[Verwijderen-item](Remove-Item.md)

[Naam wijzigen-item](Rename-Item.md)

[Set-item](Set-Item.md)

[about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md)

