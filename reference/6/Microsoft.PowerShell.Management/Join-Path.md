---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/join-path?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Join-Path
ms.openlocfilehash: 7752688a04057861fffdbc7b30c293239acb132e
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/07/2020
ms.locfileid: "93250245"
---
# Join-Path

## SAMENVATTING
Hiermee wordt een pad en een onderliggend pad gecombineerd tot één pad.

## SYNTAXIS

```
Join-Path [-Path] <String[]> [-ChildPath] <String> [[-AdditionalChildPath] <String[]>] [-Resolve]
 [-Credential <PSCredential>] [<CommonParameters>]
```

## BESCHRIJVING

De `Join-Path` cmdlet combineert een pad en een onderliggend pad naar één pad.
De provider levert de pad-scheidings tekens.

## VOORBEELDEN

### Voor beeld 1: een pad met een onderliggend pad combi neren

```powershell
PS C:\> Join-Path -Path "path" -ChildPath "childpath"
```

```output
path\childpath
```

Met deze opdracht wordt gebruikt `Join-Path` om een pad te combi neren met een childpath.

Omdat de opdracht wordt uitgevoerd vanuit de `FileSystem` provider, wordt het `\` scheidings teken geleverd om lid te worden van de paden.

### Voor beeld 2: paden combi neren die al Directory scheidings tekens bevatten

```powershell
PS C:\> Join-Path -Path "path\" -ChildPath "\childpath"
```

```output
path\childpath
```

Bestaande mappen gescheiden `\` en afgehandeld, zodat er slechts één schei ding is tussen `Path` en `ChildPath`

### Voor beeld 3: bestanden en mappen weer geven door een pad met een onderliggend pad samen te voegen

```powershell
Join-Path "C:\win*" "System*" -Resolve
```

Met deze opdracht worden de bestanden en mappen waarnaar wordt verwezen, weer gegeven door de C:\Win- \* pad en het onderliggende pad van het systeem samen te voegen \* .
De bestanden en mappen worden weer gegeven als `Get-ChildItem` , maar het volledig gekwalificeerde pad naar elk item wordt weer gegeven.
In deze opdracht worden de `Path` namen van de en `ChildPath` optionele para meters wegge laten.

### Voor beeld 4: Join-Path gebruiken met de register provider van Power shell

```powershell
PS HKLM:\> Join-Path -Path System -ChildPath *ControlSet* -Resolve
```

```output
HKLM:\System\ControlSet001
HKLM:\System\CurrentControlSet
```

Met deze opdracht worden de register sleutels in de `HKLM\System` register sleutel met de volgende inhoud weer gegeven `ControlSet` .

De `Resolve` para meter, probeert het gekoppelde pad op te lossen, inclusief joker tekens van het huidige pad naar de provider `HKLM:\`

### Voor beeld 5: meerdere paden met een onderliggend pad combi neren

```powershell
Join-Path -Path C:, D:, E:, F: -ChildPath New
```

```output
C:\New
D:\New
E:\New
F:\New
```

Met deze opdracht wordt gebruikt `Join-Path` om meerdere paden te combi neren met een onderliggend pad.

> [!NOTE]
> De stations die door `Path` moeten worden opgegeven, bestaan of de samen voeging van dat item mislukt.

### Voor beeld 6: de hoofd mappen van een bestandssysteem station met een onderliggend pad combi neren

```powershell
Get-PSDrive -PSProvider filesystem | ForEach-Object {$_.root} | Join-Path -ChildPath "Subdir"
```

```output
C:\Subdir
D:\Subdir
```

Met deze opdracht worden de hoofd mappen van elk systeem station van het Power shell-bestand in de-console gecombineerd met het onderliggende subdir-pad.

De opdracht gebruikt de `Get-PSDrive` cmdlet om de Power Shell-stations op te halen die worden ondersteund door de File System-Provider.
De `ForEach-Object` instructie selecteert alleen de hoofd eigenschap van de `PSDriveInfo` objecten en combineert deze met het opgegeven onderliggende pad.

In de uitvoer ziet u dat de Power Shell-stations op de computer een station bevatten dat is toegewezen aan de map C:\Program Files.

### Voor beeld 7: een onbeperkt aantal paden combi neren

```powershell
Join-Path a b c d e f g
```

```Output
a\b\c\d\e\f\g
```

`AdditionalChildPath`Met de para meter kan een onbeperkt aantal paden worden samengevoegd.

In dit voor beeld worden geen parameter namen gebruikt, waardoor "a" bindt naar `Path` , "b" naar `ChildPath` en "c-g" om `AdditionalChildPath`

## PARAMETERS

### -AdditionalChildPath

Hiermee geeft u extra elementen op die moeten worden toegevoegd aan de waarde van de para meter *Path* . De `ChildPath` para meter is nog steeds verplicht en moet ook worden opgegeven.

Deze para meter wordt opgegeven met de `ValueFromRemainingArguments` eigenschap waarmee een onbeperkt aantal paden kan worden toegevoegd.

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: 2
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -ChildPath

Hiermee geeft u de elementen die moeten worden toegevoegd aan de waarde van de `Path` para meter.
Joker tekens zijn toegestaan.
De `ChildPath` para meter is vereist, hoewel de parameter naam ("ChildPath") optioneel is.

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: True
Position: 1
Default value: None
Accept pipeline input: True (ByPropertyName)
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
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -Path

Hiermee geeft u de hoofd paden (of paden) waaraan het onderliggende pad wordt toegevoegd.
Joker tekens zijn toegestaan.

De waarde van `Path` bepaalt welke provider wordt gekoppeld aan de paden en voegt de scheidings tekens voor het pad toe.
De `Path` para meter is vereist, hoewel de parameter naam ("pad") optioneel is.

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases: PSPath

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: True
```

### -Oplossen

Geeft aan dat deze cmdlet het gekoppelde pad van de huidige provider moet proberen op te lossen.

- Als joker tekens worden gebruikt, retourneert de cmdlet alle paden die overeenkomen met het gekoppelde pad.
- Als **er geen** joker tekens worden gebruikt, treedt er een fout op in de cmdlet als het pad niet bestaat.

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

Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable. Zie [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)voor meer informatie.

## INVOER

### System. String

U kunt een teken reeks met een pad naar deze cmdlet door sluizen.

## UITVOER

### System. String

Deze cmdlet retourneert een teken reeks die het resulterende pad bevat.

## OPMERKINGEN

De-cmdlets die het pad zelfstandig naam woord (de pad-cmdlets) bevatten, kunnen namen van paden wijzigen en de namen retour neren in een beknopte notatie die alle Power shell-providers kan interpreteren. Ze zijn ontworpen voor gebruik in Program ma's en scripts waarvoor u de volledige of gedeeltelijke naam van een pad wilt weer geven in een bepaalde indeling. Gebruik deze zoals u mapnaam, Normpath, realpath, Join's of andere pad-werkers zou gebruiken.

U kunt de pad-cmdlets gebruiken met verschillende providers, waaronder de `FileSystem` -, `Registry` -en- `Certificate` providers.

Deze cmdlet is ontworpen om te werken met de gegevens die door elke provider worden weer gegeven.
Als u een lijst wilt weer geven van de providers die beschikbaar zijn in uw sessie, typt u `Get-PSProvider` .
Zie [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md)voor meer informatie.

## GERELATEERDE KOPPELINGEN

[Convert-pad](Convert-Path.md)

[Oplossen-pad](Resolve-Path.md)

[Split-pad](Split-Path.md)

[Test-pad](Test-Path.md)

[Get-PSProvider](Get-PSProvider.md)

[Get-Child item](Get-ChildItem.md)

[Get-PSDrive](Get-PSDrive.md)
