---
external help file: System.Management.Automation.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 05/13/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/clear-history?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Clear-History
ms.openlocfilehash: 859738998de9d2a61a5fb7d9f39ff6ef8b74ad4d
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/07/2020
ms.locfileid: "93250719"
---
# Clear-History

## SAMENVATTING
Hiermee verwijdert u vermeldingen uit de geschiedenis van de Power shell-sessie opdracht.

## SYNTAXIS

### IDParameter (standaard)

```
Clear-History [[-Id] <int[]>] [[-Count] <int>] [-Newest] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### CommandLineParameter

```
Clear-History [[-Count] <int>] [-CommandLine <string[]>] [-Newest] [-WhatIf] [-Confirm]
[<CommonParameters>]
```

## BESCHRIJVING

`Clear-History` Hiermee verwijdert u de opdracht geschiedenis uit een Power shell-sessie. Elke Power shell-sessie heeft een eigen opdracht geschiedenis. Als u de opdracht geschiedenis wilt weer geven, gebruikt u de- `Get-History` cmdlet.

`Clear-History`Verwijdert standaard de volledige opdracht geschiedenis uit een Power shell-sessie. U kunt para meters gebruiken `Clear-History` om geselecteerde opdrachten te verwijderen.

`Clear-History` Hiermee wordt het `PSReadLine` opdracht geschiedenis bestand niet gewist. `PSReadLine`In de module wordt een geschiedenis bestand opgeslagen dat elke Power shell-opdracht uit elke Power shell-sessie bevat. Gebruik vanuit een Power shell-prompt de pijl omhoog en omlaag op het toetsen bord om door de opdracht geschiedenis te bladeren. Als u de `PSReadLine` configuratie voor de opdracht geschiedenis wilt weer geven, gebruikt u `Get-PSReadLineOption` .
`PSReadLine` geleverd met Power shell 5,0 en hoger. Zie [about_PSReadLine](../PSReadLine/About/about_PSReadLine.md)voor meer informatie.

## VOORBEELDEN

### Voor beeld 1: de opdracht geschiedenis uit een Power shell-sessie verwijderen

Met deze opdracht worden alle opdrachten verwijderd uit de geschiedenis van een Power shell-sessie.

```powershell
Get-History
```

```Output
  Id CommandLine
  -- -----------
   1 Set-Location .\Test
   2 Update-Help
   3 Set-Location C:\Test\Logs
   4 Get-Location
```

```powershell
Clear-History
Get-History
```

```Output
  Id CommandLine
  -- -----------
   5 Clear-History
```

Met de `Get-History` cmdlet wordt de geschiedenis van de Power shell-sessie weer gegeven. `Clear-History` Hiermee verwijdert u de volledige opdracht geschiedenis. `Get-History` Hiermee wordt de bijgewerkte opdracht geschiedenis weer gegeven en wordt bevestigd dat de eerdere geschiedenis is verwijderd.

### Voor beeld 2: de nieuwste opdrachten verwijderen

Met deze opdracht worden de laatste en **laatste** para meters **uit de geschiedenis** van een Power shell-sessie verwijderd.

```powershell
Get-History
```

```Output
  Id CommandLine
  -- -----------
   1 Set-Location C:\Test\
   2 Get-Command Clear-History
   3 Get-Command Clear-History -Syntax
   4 Get-Command Clear-History -ShowCommandInfo
   5 Get-Help Get-Alias
   6 Get-Command Get-ChildItem -Syntax
   7 Get-Help Clear-History
   8 Set-Location C:\Test\Logs
   9 Get-Help Get-Variable
  10 Get-Help Get-ChildItem
```

```powershell
Clear-History -Count 5 -Newest
Get-History
```

```Output
  Id CommandLine
  -- -----------
   1 Set-Location C:\Test\
   2 Get-Command Clear-History
   3 Get-Command Clear-History -Syntax
   4 Get-Command Clear-History -ShowCommandInfo
   5 Get-Help Get-Alias
  11 Clear-History -Count 5 -Newest
```

Met de `Get-History` cmdlet wordt de geschiedenis van de Power shell-sessie weer gegeven. `Clear-History` wordt gebruikt voor het verwijderen van de opdracht geschiedenis. De para meter **aantal** bepaalt het aantal opdrachten dat moet worden verwijderd, inclusief de opgegeven **id**. De **nieuwste** para meter geeft aan dat de nieuwste opdrachten uit de geschiedenis worden verwijderd. `Get-History`de bijgewerkte opdracht geschiedenis wordt weer gegeven en er wordt bevestigd dat de vijf nieuwste opdrachten zijn verwijderd, **id 6**  -  **id 10**.

### Voor beeld 3: opdrachten verwijderen die aan bepaalde criteria voldoen

Met deze opdracht worden opdrachten verwijderd die overeenkomen met specifieke criteria die zijn gedefinieerd door de para meter **commandline** .

```powershell
Get-History
```

```Output
  Id CommandLine
  -- -----------
   1 Set-Location C:\Test\
   2 Get-Command Clear-History
   3 Get-Command Clear-History -Syntax
   4 Get-Command Clear-History -ShowCommandInfo
   5 Get-Help Get-Alias
   6 Get-Command Get-ChildItem -Syntax
   7 Get-Help Clear-History
```

```powershell
Clear-History -CommandLine *Help*, *Syntax
Get-History
```

```Output
  Id CommandLine
  -- -----------
   1 Set-Location C:\Test\
   2 Get-Command Clear-History
   4 Get-Command Clear-History -ShowCommandInfo
   8 Clear-History -CommandLine *Help*, *Syntax
```

Met de `Get-History` cmdlet wordt de geschiedenis van de Power shell-sessie weer gegeven. `Clear-History` Hiermee verwijdert u de opdracht geschiedenis. De para meter **commandline** bevat opdrachten die **Help** of end met **syntaxis** bevatten. `Get-History` de bijgewerkte opdracht geschiedenis wordt weer gegeven en er wordt bevestigd dat de opdrachten **id 3** , **id 5** , **id 6** en **id 7** zijn verwijderd.

### Voor beeld 4: opdrachten op id-nummer verwijderen

Met deze opdracht worden specifieke geschiedenis items verwijderd met behulp van de **id**. Als u meerdere opdrachten wilt verwijderen, dient u een door komma's gescheiden lijst met **id-** nummers in te dienen.

```powershell
Get-History
```

```Output
  Id CommandLine
  -- -----------
   1 Set-Location C:\Test\
   2 Get-History
   3 Get-Help Get-Alias
   4 Get-Command Clear-History
   5 Get-Command Clear-History -Syntax
   6 Get-Command Clear-History -ShowCommandInfo
```

```powershell
Clear-History -Id 3, 5
Get-History
```

```Output
  Id CommandLine
  -- -----------
   1 Set-Location C:\Test\
   2 Get-History
   4 Get-Command Clear-History
   6 Get-Command Clear-History -ShowCommandInfo
   7 Get-History
   8 Clear-History -Id 3, 5
```

Met de `Get-History` cmdlet wordt de geschiedenis van de Power shell-sessie weer gegeven. `Clear-History` Hiermee verwijdert u de opdracht geschiedenis. De **id-** para meter geeft aan welke opdrachten moeten worden verwijderd. `Get-History` Hiermee wordt de bijgewerkte opdracht geschiedenis weer gegeven en wordt bevestigd dat **id 3** en **id 5** zijn verwijderd.

### Voor beeld 5: opdrachten op id-nummer en aantal verwijderen

Met deze opdracht worden de para meters **id** en **aantal** gebruikt voor het verwijderen van de opdracht geschiedenis. Opdrachten worden verwijderd uit de opgegeven **id** in omgekeerde volg orde, van nieuw naar oud.

```powershell
Get-History
```

```Output
  Id CommandLine
  -- -----------
   1 Set-Location C:\Test\
   2 Get-Command Clear-History
   3 Get-Command Clear-History -Syntax
   4 Get-Command Clear-History -ShowCommandInfo
   5 Get-Help Get-Alias
   6 Get-Command Get-ChildItem -Syntax
   7 Get-Help Clear-History
   8 Set-Location C:\Test\Logs
   9 Get-Help Get-Variable
  10 Get-Help Get-ChildItem
```

```powershell
Clear-History -Id 7 -Count 5
Get-History
```

```Output
  Id CommandLine
  -- -----------
   1 Set-Location C:\Test\
   2 Get-Command Clear-History
   8 Set-Location C:\Test\Logs
   9 Get-Help Get-Variable
  10 Get-Help Get-ChildItem
  11 Clear-History -Id 7 -Count 5
```

Met de `Get-History` cmdlet wordt de geschiedenis van de Power shell-sessie weer gegeven. `Clear-History` Hiermee verwijdert u de opdracht geschiedenis. De **id-** para meter geeft aan dat begint met **id 7**. De para meter **aantal** geeft aan dat vijf opdrachten moeten worden verwijderd, inclusief de opgegeven **id**. `Get-History`Hiermee wordt de bijgewerkte opdracht geschiedenis weer gegeven en wordt bevestigd dat er vijf opdrachten zijn verwijderd, **id 3**  -  **-id 7**.

## PARAMETERS

### -CommandLine

Hiermee verwijdert u de opdracht geschiedenis uit een Power shell-sessie. De teken reeks moet exact overeenkomen of joker tekens gebruiken om opdrachten in de Power shell-sessie geschiedenis weer gegeven door te vergelijken `Get-History` . Als u meer dan één teken reeks opgeeft, `Clear-History` worden opdrachten verwijderd die overeenkomen met een van de teken reeksen. De para meter **commandline** kan worden gebruikt met **Count**.

Gebruik voor teken reeksen met een spatie enkele aanhalings tekens. Zie [about_Quoting_Rules](About/about_Quoting_Rules.md)voor meer informatie.

```yaml
Type: System.String[]
Parameter Sets: CommandLineParameter
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: True
```

### -Aantal

Hiermee geeft u het aantal geschiedenis vermeldingen op dat wordt `Clear-History` verwijderd. Opdrachten worden in volg orde verwijderd, te beginnen met de oudste vermelding in de geschiedenis.

De para meters **Count** en **id** kunnen samen worden gebruikt. De para meter **aantal** bepaalt het aantal opdrachten dat moet worden verwijderd, inclusief de opgegeven **id**. Vanaf de opgegeven **id** worden opdrachten in omgekeerde sequentiële volg orde verwijderd. Als de **id** bijvoorbeeld 30 is en de **telling** 10, `Clear-History` worden de items 21 tot en met 30 verwijderd.

De para meters **Count** en **commandline** kunnen samen worden gebruikt. **Count** Hiermee geeft u het aantal opdrachten dat moet worden verwijderd dat overeenkomt met de waarde van de **commandline** -para meter. De opdrachten worden in sequentiële volg orde verwijderd.

```yaml
Type: System.Int32
Parameter Sets: (All)
Aliases:

Required: False
Position: 1
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Id

Hiermee geeft u de opdracht geschiedenis **-id** die wordt `Clear-History` verwijderd. Als u **id-** nummers wilt weer geven, gebruikt u de `Get-History` cmdlet. De **id-** nummers zijn opeenvolgend en opdrachten blijven hun **id-** nummer in een Power shell-sessie. De **id-** para meter kan worden gebruikt met **aantal** en **Nieuw**.

```yaml
Type: System.Int32[]
Parameter Sets: IDParameter
Aliases:

Required: False
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Nieuwste

Wanneer de **nieuwste** para meter wordt gebruikt, `Clear-History` worden de meest recente vermeldingen in de geschiedenis verwijderd. Standaard `Clear-History` verwijdert de oudste vermeldingen in de geschiedenis.

De **nieuwste** para meter kan worden gebruikt met **id** en **aantal**. De para meter **aantal** bepaalt het aantal opdrachten dat moet worden verwijderd, inclusief de opgegeven **id**. Vanaf de opgegeven **id** worden opdrachten in sequentiële volg orde verwijderd. Als de **id** bijvoorbeeld 30 is en de **telling** 10, verwijdert u de `Clear-History` items 30 tot en met 39.

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

### -Confirm

Vraagt u om bevestiging voordat de cmdlet wordt uitgevoerd `Clear-History` .

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

Laat zien wat er zou gebeuren als de `Clear-History` cmdlet wordt uitgevoerd. De cmdlet wordt niet uitgevoerd.

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

Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable. Zie [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md)voor meer informatie.

## INVOER

### Geen

U kunt geen objecten pipeen naar `Clear-History` .

## UITVOER

### Geen

`Clear-History` Er wordt geen uitvoer gegenereerd.

## OPMERKINGEN

De Power shell-sessie geschiedenis is een lijst met opdrachten die tijdens een Power shell-sessie zijn ingevoerd. U kunt de geschiedenis bekijken, opdrachten toevoegen en verwijderen en opdrachten uit de geschiedenis uitvoeren. Zie [about_History](About/about_History.md)voor meer informatie.

De sessie geschiedenis wordt afzonderlijk beheerd vanaf de geschiedenis die wordt onderhouden door de **PSReadLine** -module.
Beide geschiedenissen zijn beschikbaar in sessies waarin **PSReadLine** wordt geladen. Deze cmdlet werkt alleen met de sessie geschiedenis. Zie [about_PSReadLine](../PSReadLine/About/about_PSReadLine.md)voor meer informatie.

## GERELATEERDE KOPPELINGEN

[about_History](About/about_History.md)

[about_PSReadLine](../PSReadLine/About/about_PSReadLine.md)

[about_Quoting_Rules](About/about_Quoting_Rules.md)

[Toevoegen-geschiedenis](Add-History.md)

[Get-geschiedenis](Get-History.md)

[Invoke-geschiedenis](Invoke-History.md)

[Get-PSReadLineOption](/powershell/module/psreadline/get-psreadlineoption)

[Set-PSReadLineOption](/powershell/module/psreadline/set-psreadlineoption)
