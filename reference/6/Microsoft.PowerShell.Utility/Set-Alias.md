---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 2/28/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/set-alias?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Set-Alias
ms.openlocfilehash: 791b500660ed536eb1bd7ba4d6f37e8211078a0c
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/07/2020
ms.locfileid: "93251009"
---
# Set-Alias

## SAMENVATTING
Hiermee maakt of wijzigt u een alias voor een cmdlet of een andere opdracht in de huidige Power shell-sessie.

## SYNTAXIS

### Standaard (standaard instelling)

```
Set-Alias [-Name] <string> [-Value] <string> [-Description <string>] [-Option <ScopedItemOptions>]
 [-PassThru] [-Scope <string>] [-Force] [-WhatIf] [-Confirm] [<CommonParameters>]
```

## BESCHRIJVING

De `Set-Alias` cmdlet maakt of wijzigt een alias voor een cmdlet of een opdracht, zoals een functie, script, bestand of ander uitvoerbaar bestand. Een alias is een alternatieve naam die verwijst naar een cmdlet of opdracht.
`sal`Is bijvoorbeeld de alias voor de `Set-Alias` cmdlet. Zie [about_Aliases](../Microsoft.PowerShell.Core/About/about_Aliases.md)voor meer informatie.

Een cmdlet kan meerdere aliassen hebben, maar een alias kan slechts aan één cmdlet worden gekoppeld. U kunt gebruiken `Set-Alias` om een bestaande alias opnieuw toe te wijzen aan een andere cmdlet of de eigenschappen van een alias te wijzigen, zoals de beschrijving.

Een alias die is gemaakt of gewijzigd door `Set-Alias` is niet permanent en is alleen beschikbaar tijdens de huidige Power shell-sessie. Wanneer de Power shell-sessie is gesloten, wordt de alias verwijderd.

## VOORBEELDEN

### Voor beeld 1: een alias maken voor een cmdlet

Met deze opdracht maakt u een alias voor een cmdlet in de huidige Power shell-sessie.

```
PS> Set-Alias -Name list -Value Get-ChildItem

PS> Get-Alias -Name list

CommandType     Name
-----------     ----
Alias           list -> Get-ChildItem
```

`Set-Alias`Met de cmdlet maakt u een alias in de huidige Power shell-sessie. Met de para meter **name** wordt de naam van de alias opgegeven, `list` . De **waarde** para meter geeft u de cmdlet op die de alias uitvoert.

Als u de alias wilt uitvoeren, typt u `list` op de Power shell-opdracht regel.

### Voor beeld 2: een bestaande alias opnieuw toewijzen aan een andere cmdlet

Met deze opdracht wordt een bestaande alias opnieuw toegewezen om een andere cmdlet uit te voeren.

```
PS> Get-Alias -Name list

CommandType     Name
-----------     ----
Alias           list -> Get-ChildItem

PS> Set-Alias -Name list -Value Get-Location

PS> Get-Alias -Name list

CommandType     Name
-----------     ----
Alias           list -> Get-Location
```

De `Get-Alias` cmdlet gebruikt de para meter **name** om de alias weer te geven `list` . De `list` alias is gekoppeld aan de `Get-ChildItem` cmdlet. Wanneer de `list` alias wordt uitgevoerd, worden de items in de huidige map weer gegeven.

De `Set-Alias` cmdlet gebruikt de para meter **name** om de alias op te geven `list` . De **waarde** para meter koppelt de alias aan de `Get-Location` cmdlet.

De `Get-Alias` cmdlet gebruikt de para meter **name** om de alias weer te geven `list` . De `list` alias is gekoppeld aan de `Get-Location` cmdlet. Wanneer de `list` alias wordt uitgevoerd, wordt de locatie van de huidige map weer gegeven.

### Voor beeld 3: een alleen-lezen-alias maken en wijzigen

Met deze opdracht maakt u een alias met het kenmerk alleen-lezen. De alleen-lezen optie voor komt onbedoelde wijzigingen aan een alias. Als u een alleen-lezen alias wilt wijzigen of verwijderen, gebruikt u de para meter **Force** .

```
PS> Set-Alias -Name loc -Value Get-Location -Option ReadOnly -PassThru | Format-List -Property *

DisplayName         : loc -> Get-Location
Definition          : Get-Location
Options             : ReadOnly
Description         :
Name                : loc
CommandType         : Alias

PS> Set-Alias -Name loc -Value Get-Location -Option ReadOnly -Description 'Displays the current directory' -Force -PassThru | Format-List -Property *

DisplayName         : loc -> Get-Location
Definition          : Get-Location
Options             : ReadOnly
Description         : Displays the current directory
Name                : loc
CommandType         : Alias
```

`Set-Alias`Met de cmdlet maakt u een alias in de huidige Power shell-sessie. Met de para meter **name** wordt de naam van de alias opgegeven, `loc` . De **waarde** para meter geeft u de `Get-Location` cmdlet op die de alias uitvoert. Met de para meter **Option** wordt de waarde **ReadOnly** opgegeven. De para meter **PassThru** vertegenwoordigt het alias object en stuurt het object omlaag in de pijp lijn naar de `Format-List` cmdlet. `Format-List` gebruikt de **eigenschaps** parameter met een asterisk ( `*` ), zodat alle eigenschappen worden weer gegeven. In de voorbeeld uitvoer ziet u een gedeeltelijke lijst met die eigenschappen.

De `loc` alias wordt gewijzigd met de toevoeging van twee para meters. **Beschrijving** voegt tekst toe om het doel van de alias te verklaren. De para meter **Force** is vereist omdat de `loc` alias alleen-lezen is. Als de para meter **Forces** niet wordt gebruikt, mislukt de wijziging.

### Voor beeld 4: een alias maken voor een uitvoerbaar bestand

In dit voor beeld wordt een alias gemaakt voor een uitvoerbaar bestand op de lokale computer.

```
PS> Set-Alias -Name np -Value C:\Windows\notepad.exe

PS> Get-Alias -Name np

CommandType     Name
-----------     ----
Alias           np -> notepad.exe
```

`Set-Alias`Met de cmdlet maakt u een alias in de huidige Power shell-sessie. Met de para meter **name** wordt de naam van de alias opgegeven, `np` . De **waarde** para meter geeft u het pad en de naam van de toepassing op **C:\Windows\notepad.exe**. De `Get-Alias` cmdlet gebruikt de para meter **name** om aan te geven dat de `np` alias is gekoppeld aan **notepad.exe**.

Als u de alias wilt uitvoeren, typt `np` u op de Power shell-opdracht regel om **notepad.exe** te openen.

### Voor beeld 5: een alias maken voor een opdracht met para meters

In dit voor beeld ziet u hoe u een alias toewijst aan een opdracht met para meters.

U kunt een alias voor een cmdlet maken, zoals `Set-Location` . U kunt geen alias maken voor een opdracht met para meters en waarden, zoals `Set-Location -Path C:\Windows\System32` . Als u een alias voor een opdracht wilt maken, maakt u een functie die de opdracht bevat en maakt u vervolgens een alias voor de functie. Zie [about_Functions](../Microsoft.PowerShell.Core/about/about_Functions.md)voor meer informatie.

```
PS> Function CD32 {Set-Location -Path C:\Windows\System32}

PS> Set-Alias -Name Go -Value CD32
```

Er wordt een functie gemaakt met de naam `CD32` . De functie gebruikt de- `Set-Location` cmdlet met de para meter **Path** om de map, **C:\Windows\System32** op te geven.

De `Set-Alias` cmdlet maakt een alias voor de functie in de huidige Power shell-sessie. Met de para meter **name** wordt de naam van de alias opgegeven, `Go` . De **waarde** para meter geeft u de naam van de functie op `CD32` .

Als u de alias wilt uitvoeren, typt u `Go` op de Power shell-opdracht regel. De `CD32` functie wordt uitgevoerd en wijzigingen worden aangebracht in de Directory **C:\Windows\System32**.

## PARAMETERS

### -Beschrijving

Hiermee geeft u een beschrijving van de alias. U kunt een wille keurige teken reeks typen. Als de beschrijving spaties bevat, plaatst u deze enkele aanhalings tekens.

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

### -Force

Gebruik de para meter **Force** om een alias te wijzigen of te verwijderen waarvoor de **optie** parameter is ingesteld op **ReadOnly**.

De para meter **Force** kan geen alias wijzigen of verwijderen met de para meter **Option** ingesteld op **constant**.

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

### -Name

Hiermee geeft u de naam van een nieuwe alias. Een alias naam mag alfanumerieke tekens en afbreek streepjes bevatten. Alias namen mogen niet numeriek zijn, zoals 123.

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -Optie

Hiermee stelt u de waarde van de **optie** eigenschap van de alias. Waarden zoals **alleen-lezen** en **constant** een alias beveiligen tegen onbedoelde wijzigingen. Als u de **optie** -eigenschap van alle aliassen in de sessie wilt weer geven, typt u `Get-Alias | Format-Table -Property Name, Options -Autosize` .

De acceptabele waarden voor deze para meter zijn als volgt:

- **AllScope** De alias wordt gekopieerd naar nieuwe bereiken die worden gemaakt.
- **Constante** Kan niet worden gewijzigd of verwijderd.
- **Geen** Stelt geen opties in en is de standaard waarde.
- **Privé** De alias is alleen beschikbaar in de huidige scope.
- **Alleen-lezen** Kan alleen worden gewijzigd of verwijderd als de para meter **Forces** wordt gebruikt.
- **Niet opgegeven**

```yaml
Type: System.Management.Automation.ScopedItemOptions
Parameter Sets: (All)
Aliases:
Accepted values: AllScope, Constant, None, Private, ReadOnly, Unspecified

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -PassThru

Retourneert een object dat de alias vertegenwoordigt. Gebruik een indelings-cmdlet, zoals `Format-List` om het object weer te geven. `Set-Alias`Er wordt standaard geen uitvoer gegenereerd.

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

### -Bereik

Hiermee geeft u het bereik op waarin deze alias geldig is. De standaard waarde is **lokaal**. Zie [about_Scopes](../Microsoft.PowerShell.Core/About/about_Scopes.md)voor meer informatie.

De acceptabele waarden zijn als volgt:

- Globaal
- Lokaal
- Privé
- Genummerde bereiken
- Script

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:
Accepted values: Global, Local, Private, Numbered scopes, Script

Required: False
Position: Named
Default value: Local
Accept pipeline input: False
Accept wildcard characters: False
```

### -Waarde

Hiermee geeft u de naam op van de cmdlet of opdracht die de alias uitvoert. De **waarde** para meter is de eigenschap **definitie** van de alias.

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: True
Position: 1
Default value: None
Accept pipeline input: True (ByPropertyName)
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

### Geen

`Set-Alias` accepteert geen invoer van de pijp lijn.

## UITVOER

### Geen of System. Management. Automation. AliasInfo

Wanneer u de para meter **PassThru** gebruikt, `Set-Alias` genereert een **System. Management. Automation. AliasInfo** -object dat de alias vertegenwoordigt. Anders `Set-Alias` wordt er geen uitvoer gegenereerd.

## OPMERKINGEN

Power shell bevat ingebouwde aliassen die beschikbaar zijn in elke Power shell-sessie. `Get-Alias`Met de cmdlet worden de aliassen weer gegeven die beschikbaar zijn in een Power shell-sessie.

Als u een alias wilt maken, gebruikt u de-cmdlets `Set-Alias` of `New-Alias` . In Power shell 6 kunt u een alias verwijderen met de `Remove-Alias` cmdlet. `Remove-Item` wordt geaccepteerd voor achterwaartse compatibiliteit, zoals voor scripts die zijn gemaakt met eerdere versies van Power shell. Gebruik een opdracht zoals `Remove-Item -Path Alias:aliasname` .

Als u een alias wilt maken die beschikbaar is in elke Power shell-sessie, voegt u deze toe aan uw Power shell-profiel.
Zie [about_Profiles](../Microsoft.PowerShell.Core/About/about_Profiles.md)voor meer informatie.

Een alias kan worden opgeslagen en opnieuw worden gebruikt in een andere Power shell-sessie door een export-en import bewerking uit te voeren. Als u een alias wilt opslaan in een bestand, gebruikt u `Export-Alias` . Gebruik om een opgeslagen alias toe te voegen aan een nieuwe Power shell-sessie `Import-Alias` .

## GERELATEERDE KOPPELINGEN

[about_Aliases](../Microsoft.PowerShell.Core/About/about_Aliases.md)

[about_Functions](../Microsoft.PowerShell.Core/about/about_Functions.md)

[about_Profiles](../Microsoft.PowerShell.Core/About/about_Profiles.md)

[about_Scopes](../Microsoft.PowerShell.Core/About/about_Scopes.md)

[Exporteren-alias](Export-Alias.md)

[Get-alias](Get-Alias.md)

[Import-alias](Import-Alias.md)

[Nieuwe alias](New-Alias.md)

[Alias verwijderen](Remove-Alias.md)

[Verwijderen-item](../Microsoft.PowerShell.Management/Remove-Item.md)
