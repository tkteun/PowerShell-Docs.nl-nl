---
external help file: Microsoft.PowerShell.PSReadLine2.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: PSReadline
ms.date: 06/30/2020
online version: https://docs.microsoft.com/powershell/module/psreadline/set-psreadlineoption?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Set-PSReadLineOption
ms.openlocfilehash: 15295ffaac320d24a3c9c24c0419118ef2644f90
ms.sourcegitcommit: ae8b89e12c6fa2108075888dd6da92788d6c2888
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/21/2020
ms.locfileid: "93253153"
---
# Set-PSReadLineOption

## Samen vatting
Het gedrag van het bewerken van opdracht regels in **PSReadLine** aanpassen.

## Syntax

```
Set-PSReadLineOption [-EditMode <EditMode>] [-ContinuationPrompt <String>] [-HistoryNoDuplicates]
 [-AddToHistoryHandler <System.Func[System.String,System.Object]>]
 [-CommandValidationHandler <System.Action[System.Management.Automation.Language.CommandAst]>]
 [-HistorySearchCursorMovesToEnd] [-MaximumHistoryCount <Int32>] [-MaximumKillRingCount <Int32>]
 [-ShowToolTips] [-ExtraPromptLineCount <Int32>] [-DingTone <Int32>] [-DingDuration <Int32>]
 [-BellStyle <BellStyle>] [-CompletionQueryItems <Int32>] [-WordDelimiters <String>]
 [-HistorySearchCaseSensitive] [-HistorySaveStyle <HistorySaveStyle>] [-HistorySavePath <String>]
 [-AnsiEscapeTimeout <Int32>] [-PromptText <String[]>] [-ViModeIndicator <ViModeStyle>]
 [-ViModeChangeHandler <ScriptBlock>] [-Colors <Hashtable>] [<CommonParameters>]
```

## Beschrijving

`Set-PSReadLineOption`Met de cmdlet wordt het gedrag van de **PSReadLine** -module aangepast wanneer u de opdracht regel bewerkt. Als u de **PSReadLine** -instellingen wilt weer geven, gebruikt u `Get-PSReadLineOption` .

## Voorbeelden

### Voor beeld 1: voorgrond-en achtergrond kleuren instellen

In dit voor beeld wordt **PSReadLine** ingesteld om het **opmerkings** token met groene voorgrond tekst op een grijze achtergrond weer te geven. In de escape-reeks die in het voor beeld wordt gebruikt, vertegenwoordigt **32** de voorgrond kleur en **47** de achtergrond kleur.

```powershell
Set-PSReadLineOption -Colors @{ "Comment"="$([char]0x1b)[32;47m" }
```

U kunt ervoor kiezen om alleen een voorgrond tekst kleur in te stellen. Bijvoorbeeld een heldere, groene voorgrond tekst kleur voor het **opmerkings** token: `"Comment"="$([char]0x1b)[92m"` .

### Voor beeld 2: de stijl van de Bel instellen

In dit voor beeld reageert **PSReadLine** op fouten of voor waarden waarvoor aandacht van de gebruiker is vereist.
De **BellStyle** is ingesteld voor het verzenden van een hoorbaar pieptoon bij 1221 Hz voor 60 MS.

```powershell
Set-PSReadLineOption -BellStyle Audible -DingTone 1221 -DingDuration 60
```

> [!NOTE]
> Deze functie werkt mogelijk niet op alle hosts op platforms.

### Voor beeld 3: meerdere opties instellen

`Set-PSReadLineOption` kan meerdere opties instellen met een hash-tabel.

```powershell
$PSReadLineOptions = @{
    EditMode = "Emacs"
    HistoryNoDuplicates = $true
    HistorySearchCursorMovesToEnd = $true
    Colors = @{
        "Command" = "#8181f7"
    }
}
Set-PSReadLineOption @PSReadLineOptions
```

In de `$PSReadLineOptions` tabel hash worden de sleutels en waarden ingesteld. `Set-PSReadLineOption` gebruikt de sleutels en waarden met `@PSReadLineOptions` om de **PSReadLine** -opties bij te werken.

U kunt de sleutels en waarden voor het invoeren van de naam van de hash-tabel weer geven `$PSReadLineOptions` op de Power shell-opdracht regel.

### Voor beeld 4: meerdere kleur opties instellen

In dit voor beeld ziet u hoe u in één opdracht meer dan één kleur waarde kunt instellen.

```powershell
Set-PSReadLineOption -Colors @{
  Command            = 'Magenta'
  Number             = 'DarkGray'
  Member             = 'DarkGray'
  Operator           = 'DarkGray'
  Type               = 'DarkGray'
  Variable           = 'DarkGreen'
  Parameter          = 'DarkGreen'
  ContinuationPrompt = 'DarkGray'
  Default            = 'DarkGray'
}
```

### Voor beeld 5: kleur waarden instellen voor meerdere typen

Dit voor beeld toont drie verschillende methoden voor het instellen van de kleur van tokens die worden weer gegeven in **PSReadLine**.

```powershell
Set-PSReadLineOption -Colors @{
 # Use a ConsoleColor enum
 "Error" = [ConsoleColor]::DarkRed

 # 24 bit color escape sequence
 "String" = "$([char]0x1b)[38;5;100m"

 # RGB value
 "Command" = "#8181f7"
}
```

### Voor beeld 6: ViModeChangeHandler gebruiken om wijzigingen in de modus in de VI weer te geven

In dit voor beeld wordt een cursor wijziging een VT-Escape verzonden in reactie op een wijziging in de **VI** -modus.

```powershell
function OnViModeChange {
    if ($args[0] -eq 'Command') {
        # Set the cursor to a blinking block.
        Write-Host -NoNewLine "$([char]0x1b)[1 q"
    } else {
        # Set the cursor to a blinking line.
        Write-Host -NoNewLine "$([char]0x1b)[5 q"
    }
}
Set-PSReadLineOption -ViModeIndicator Script -ViModeChangeHandler $Function:OnViModeChange
```

De functie **OnViModeChange** stelt de cursor opties in voor de **VI** -modi: insert en Command.
**ViModeChangeHandler** maakt gebruik van de `Function:` provider om te verwijzen naar **OnViModeChange** als een script blok-object.

Zie [about_Providers](/powershell/module/microsoft.powershell.core/about/about_providers)voor meer informatie.

## Parameters

### -AddToHistoryHandler

Hiermee geeft u een **script Block** op die bepaalt welke opdrachten aan de **PSReadLine** -geschiedenis worden toegevoegd.

De **script Block** ontvangt de opdracht regel als invoer. Als de **script Block** wordt geretourneerd `$True` , wordt de opdracht regel aan de geschiedenis toegevoegd.

```yaml
Type: System.Func`2[System.String,System.Object]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -AnsiEscapeTimeout

Deze optie is specifiek voor Windows wanneer invoer wordt omgeleid, bijvoorbeeld wanneer deze wordt uitgevoerd onder `tmux` of `screen` .

Met omgeleide invoer in Windows worden veel sleutels verzonden als een reeks tekens die beginnen met het escape-teken. Het is niet mogelijk om onderscheid te maken tussen één escape teken, gevolgd door meer tekens en een geldige escape reeks.

De veronderstelling is dat de Terminal de tekens sneller kan verzenden dan een gebruiker typt. **PSReadLine** wacht op deze time-out voordat wordt geconcludeerd dat er een volledige escape reeks is ontvangen.

Als u wille keurige of onverwachte tekens ziet wanneer u typt, kunt u deze time-out aanpassen.

```yaml
Type: System.Int32
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: 100
Accept pipeline input: False
Accept wildcard characters: False
```

### -BellStyle

Hiermee geeft u op hoe **PSReadLine** reageert op verschillende fout-en ambigue voor waarden.

De geldige waarden zijn als volgt:

- **Hoorbaar** : een korte piep Toon.
- **Visueel** : tekst knippert even.
- **Geen: geen** feedback.

```yaml
Type: Microsoft.PowerShell.BellStyle
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: Audible
Accept pipeline input: False
Accept wildcard characters: False
```

### -Kleuren

De para meter **kleuren** bevat verschillende kleuren die worden gebruikt door **PSReadLine**.

Het argument is een hash-tabel waarin de sleutels opgeven welk element en welke waarden de kleur opgeven.
Zie [about_Hash_Tables](/powershell/module/microsoft.powershell.core/about/about_hash_tables)voor meer informatie.

Kleuren kunnen bestaan uit een waarde van **ConsoleColor** , bijvoorbeeld `[ConsoleColor]::Red` of een geldige ANSI-escape reeks. Geldige escape reeksen zijn afhankelijk van uw Terminal. In Power shell 5,0 is een voor beeld van een escape reeks voor rode tekst `$([char]0x1b)[91m` . In Power shell 6 en hoger is dezelfde escape reeks `` `e[91m`` . U kunt andere escape reeksen opgeven, met inbegrip van de volgende typen:

- 256-kleur
- 24-bits kleur
- Voor grond, achtergrond of beide
- Inverse, vet

Zie [ANSI escape-code](https://wikipedia.org/wiki/ANSI_escape_code#Colors_) in Wikipedia voor meer informatie over ANSI-kleur codes.

De geldige sleutels zijn onder andere:

- **ContinuationPrompt** : de kleur van de voortzettings prompt.
- **Nadruk** : de kleur van de nadruk. Bijvoorbeeld, de overeenkomende tekst bij het zoeken van de geschiedenis.
- **Fout** : de fout kleur. Bijvoorbeeld in de prompt.
- **Selectie** : de kleur voor het markeren van de menu selectie of de geselecteerde tekst.
- **Standaard** : de kleur van het standaard token.
- **Opmerking** : de kleur van het opmerkings token.
- **Sleutel woord** : de kleur van het trefwoord token.
- **Teken reeks** : de kleur van het teken reeks token.
- **Operator** : de kleur van de operator token.
- **Variabele** : de kleur van het variabele token.
- **Opdracht** : de kleur van het opdracht token.
- **Para meter** : de kleur van het parameter token.
- **Type** : het type token kleur.
- **Getal** : de kleur van het cijfer token.
- **Lid** : de kleur van het token van de leden naam.

```yaml
Type: System.Collections.Hashtable
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -CommandValidationHandler

Hiermee geeft u een **script Block** die wordt aangeroepen vanuit **ValidateAndAcceptLine**. Als er een uitzonde ring wordt gegenereerd, mislukt de validatie en wordt de fout gerapporteerd.

Voordat u een uitzonde ring uitvoerde, kan de validatie-handler de cursor op het punt van de fout plaatsen, zodat deze eenvoudiger te verhelpen is. Een validatie-handler kan ook de opdracht regel wijzigen, zoals om veelvoorkomende typografische fouten te corrigeren.

**ValidateAndAcceptLine** wordt gebruikt om te voor komen dat uw geschiedenis wordt opgeruimd met opdrachten die niet werken.

```yaml
Type: System.Action`1[System.Management.Automation.Language.CommandAst]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -CompletionQueryItems

Hiermee geeft u het maximum aantal voltooiings items op dat wordt weer gegeven zonder te vragen.

Als het aantal items dat moet worden weer gegeven groter is dan deze waarde, vraagt **PSReadLine** **Ja/Nee** voordat de voltooiings items worden weer gegeven.

```yaml
Type: System.Int32
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: 100
Accept pipeline input: False
Accept wildcard characters: False
```

### -ContinuationPrompt

Geeft de teken reeks aan die wordt weer gegeven aan het begin van de volgende regels wanneer de invoer van meerdere regels wordt ingevoerd. De standaard waarde is Double groter dan tekens ( `>>` ). Een lege teken reeks is geldig.

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: >>
Accept pipeline input: False
Accept wildcard characters: False
```

### -DingDuration

Hiermee geeft u de duur van de piep Toon op wanneer **BellStyle** is ingesteld op **hoorbaar**.

```yaml
Type: System.Int32
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: 50ms
Accept pipeline input: False
Accept wildcard characters: False
```

### -DingTone

Geeft de Toon in Hertz (Hz) van de piep Toon wanneer **BellStyle** is ingesteld op **hoorbaar**.

```yaml
Type: System.Int32
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: 1221
Accept pipeline input: False
Accept wildcard characters: False
```

### -EditMode

Hiermee geeft u de bewerkings modus van de opdracht regel op. Als u deze para meter gebruikt, worden de sleutel bindingen die zijn ingesteld door hersteld `Set-PSReadLineKeyHandler` .

De geldige waarden zijn als volgt:

- **Windows** : sleutel bindingen emuleren Power shell, cmd en Visual Studio.
- **Emacs** : sleutel bindingen bash of emacs emuleren.
- **VI** : sleutel bindingen emuleren VI.

Gebruik `Get-PSReadLineKeyHandler` om de sleutel bindingen voor de momenteel geconfigureerde **EditMode** weer te geven.

```yaml
Type: Microsoft.PowerShell.EditMode
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: Windows
Accept pipeline input: False
Accept wildcard characters: False
```

### -ExtraPromptLineCount

Hiermee geeft u het aantal extra regels op.

Als uw prompt meer dan één regel omvat, geeft u een waarde op voor deze para meter. Gebruik deze optie als u wilt dat extra lijnen beschikbaar zijn wanneer **PSReadLine** de vraag geeft nadat een bepaalde uitvoer wordt weer gegeven. **PSReadLine** retourneert bijvoorbeeld een lijst met voltooiingen.

Deze optie is minder nodig dan in eerdere versies van **PSReadLine** , maar is handig wanneer de `InvokePrompt` functie wordt gebruikt.

```yaml
Type: System.Int32
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: 0
Accept pipeline input: False
Accept wildcard characters: False
```

### -HistoryNoDuplicates

Met deze optie bepaalt u het intrekkings gedrag. Er worden nog dubbele opdrachten toegevoegd aan het geschiedenis bestand.
Als deze optie is ingesteld, wordt alleen de meest recente aanroep weer gegeven wanneer opdrachten worden ingetrokken. Herhaalde opdrachten worden toegevoegd aan de geschiedenis om de volg orde te behouden tijdens het intrekken. Normaal gesp roken wilt u de opdracht echter niet meerdere keren zien wanneer u de geschiedenis aanroept of doorzoekt.

De eigenschap **HistoryNoDuplicates** van het object Global **PSConsoleReadLineOptions** is standaard ingesteld op `True` . Met deze **SwitchParameter** stelt u de waarde van de eigenschap in op `True` . Als u de waarde van de eigenschap wilt wijzigen, moet u de waarde van de **SwitchParameter** als volgt opgeven: `-HistoryNoDuplicates:$False` .

Met de volgende opdracht kunt u de waarde van de eigenschap rechtstreeks instellen:

`(Get-PSReadLineOption).HistoryNoDuplicates = $False`

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

### -HistorySavePath

Hiermee geeft u het pad op naar het bestand waarin de geschiedenis wordt opgeslagen. Op computers met Windows-of niet-Windows-platforms wordt het bestand op verschillende locaties opgeslagen. De bestands naam wordt bijvoorbeeld opgeslagen in een variabele `$($host.Name)_history.txt` `ConsoleHost_history.txt` .

Als u deze para meter niet gebruikt, is het standaardpad als volgt:

**Windows**

`$env:APPDATA\Microsoft\Windows\PowerShell\PSReadLine\$($host.Name)_history.txt`

**niet-Windows**

`$env:XDG_DATA_HOME/powershell/PSReadLine\$($host.Name)_history.txt`

`$env:HOME/.local/share/powershell/PSReadLine\$($host.Name)_history.txt`

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: A file named $($host.Name)_history.txt in $env:APPDATA\Microsoft\Windows\PowerShell\PSReadLine on Windows and $env:XDG_DATA_HOME/powershell/PSReadLine or $env:HOME/.local/share/powershell/PSReadLine on non-Windows platforms
Accept pipeline input: False
Accept wildcard characters: False
```

### -HistorySaveStyle

Hiermee geeft u op hoe **PSReadLine** de geschiedenis opslaat.

Geldige waarden zijn als volgt:

- **SaveIncrementally** : Sla de geschiedenis op nadat elke opdracht is uitgevoerd en delen over meerdere instanties van Power shell.
- **SaveAtExit** : het geschiedenis bestand toevoegen wanneer Power shell wordt afgesloten.
- **SaveNothing** : gebruik geen geschiedenis bestand.

```yaml
Type: Microsoft.PowerShell.HistorySaveStyle
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: SaveIncrementally
Accept pipeline input: False
Accept wildcard characters: False
```

### -HistorySearchCaseSensitive

Hiermee geeft u op dat zoeken in de geschiedenis hoofdletter gevoelig is in functions zoals **ReverseSearchHistory** of **HistorySearchBackward**.

De eigenschap **HistorySearchCaseSensitive** van het object Global **PSConsoleReadLineOptions** is standaard ingesteld op `False` . Met deze **SwitchParameter** stelt u de waarde van de eigenschap in op `True` . Als u de waarde van de eigenschap terug wilt wijzigen, moet u de waarde van de **SwitchParameter** als volgt opgeven: `-HistorySearchCaseSensitive:$False` .

Met de volgende opdracht kunt u de waarde van de eigenschap rechtstreeks instellen:

`(Get-PSReadLineOption).HistorySearchCaseSensitive = $False`

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

### -HistorySearchCursorMovesToEnd

Hiermee wordt aangegeven dat de cursor wordt verplaatst naar het einde van opdrachten die u uit de geschiedenis laadt met behulp van een zoek opdracht.
Als deze para meter is ingesteld op `$False` , blijft de cursor op de positie waar deze zich bevond toen u op de pijl omhoog of omlaag was geklikt.

De eigenschap **HistorySearchCursorMovesToEnd** van het object Global **PSConsoleReadLineOptions** is standaard ingesteld op `False` . Met deze **SwitchParameter** stelt u de waarde van de eigenschap in op `True` . Als u de waarde van de eigenschap terug wilt wijzigen, moet u de waarde van de **SwitchParameter** als volgt opgeven: `-HistorySearchCursorMovesToEnd:$False` .

Met de volgende opdracht kunt u de waarde van de eigenschap rechtstreeks instellen:

`(Get-PSReadLineOption).HistorySearchCursorMovesToEnd = $False`

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

### -MaximumHistoryCount

Hiermee geeft u het maximum aantal opdrachten op dat moet worden opgeslagen in de **PSReadLine** geschiedenis.

De geschiedenis van de **PSReadLine** is gescheiden van de Power shell-geschiedenis.

```yaml
Type: System.Int32
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -MaximumKillRingCount

Hiermee geeft u het maximum aantal items op dat is opgeslagen in de Kill-ring.

```yaml
Type: System.Int32
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: 10
Accept pipeline input: False
Accept wildcard characters: False
```

### -PromptText

Wanneer er een parseringsfout optreedt, wordt in **PSReadLine** een deel van de prompt rood gewijzigd. **PSReadLine** analyseert uw prompt functie om te bepalen hoe u alleen de kleur van een deel van uw prompt kunt wijzigen. Deze analyse is niet 100% betrouwbaar.

Gebruik deze optie als **PSReadLine** uw prompt op onverwachte manieren wijzigt. Geef een wille keurige spatie op.

Bijvoorbeeld, als uw prompt functie lijkt op het volgende voor beeld:

`function prompt { Write-Host -NoNewLine -ForegroundColor Yellow "$pwd"; return "# " }`

Vervolgens ingesteld:

`Set-PSReadLineOption -PromptText "# "`

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: >
Accept pipeline input: False
Accept wildcard characters: False
```

### -ShowToolTips

Wanneer mogelijke voltooiingen worden weer gegeven, worden knop Info weer gegeven in de lijst met voltooiingen.

Deze optie is standaard ingeschakeld. Deze optie is niet standaard ingeschakeld in eerdere versies van **PSReadLine**. Als u wilt uitschakelen, stelt u deze optie in op `$False` .

De eigenschap **ShowToolTips** van het object Global **PSConsoleReadLineOptions** is standaard ingesteld op `True` . Met deze **SwitchParameter** stelt u de waarde van de eigenschap in op `True` . Als u de waarde van de eigenschap wilt wijzigen, moet u de waarde van de **SwitchParameter** als volgt opgeven: `-ShowToolTips:$False` .

Met de volgende opdracht kunt u de waarde van de eigenschap rechtstreeks instellen:

`(Get-PSReadLineOption).ShowToolTips = $False`

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

### -ViModeChangeHandler

Wanneer de **ViModeIndicator** is ingesteld op `Script` , wordt het opgegeven script blok elke keer dat de modus verandert, aangeroepen. Het script blok biedt één argument van het type `ViMode` .

Deze para meter is geïntroduceerd in Power shell 7.

```yaml
Type: System.Management.Automation.ScriptBlock
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -ViModeIndicator

Met deze optie stelt u de visuele indicatie in voor de huidige **VI** -modus. De Invoeg modus of de opdracht modus.

De geldige waarden zijn als volgt:

- **Geen** : er is geen indicatie.
- **Prompt** : de prompt verandert in kleur.
- **Cursor** : de grootte van de cursor verandert.
- **Script** : door de gebruiker opgegeven tekst wordt afgedrukt.

```yaml
Type: Microsoft.PowerShell.ViModeStyle
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -WordDelimiters

Hiermee geeft u de tekens op waarmee woorden worden beperkt voor functies zoals **ForwardWord** of **KillWord**.

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: ;:,.[]{}()/\|^&*-=+'"---
Accept pipeline input: False
Accept wildcard characters: False
```

### CommonParameters

Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable. Zie [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)voor meer informatie.

## Invoerwaarden

### Geen

U kunt objecten niet naar `Set-PSReadLineOption.`

## Uitvoer

### Geen

Met deze cmdlet wordt geen uitvoer gegenereerd.

## Opmerkingen

## Verwante koppelingen

[about_PSReadLine](./About/about_PSReadLine.md)

[Get-PSReadLineKeyHandler](Get-PSReadLineKeyHandler.md)

[Get-PSReadLineOption](Get-PSReadLineOption.md)

[Remove-PSReadLineKeyHandler](Remove-PSReadLineKeyHandler.md)

[Set-PSReadLineKeyHandler](Set-PSReadLineKeyHandler.md)
