---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 08/22/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/select-string?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Select-String
ms.openlocfilehash: 339afab9c817b54a79e2f1b33b7021ecb4fe6a6e
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 11/17/2020
ms.locfileid: "94704739"
---
# Select-String

## SAMENVATTING
Zoeken naar tekst in teken reeksen en bestanden.

## SYNTAXIS

### Bestand (standaard)

```
Select-String [-Culture <String>] [-Pattern] <String[]> [-Path] <String[]> [-SimpleMatch]
 [-CaseSensitive] [-Quiet] [-List] [-NoEmphasis] [-Include <String[]>] [-Exclude <String[]>]
 [-NotMatch] [-AllMatches] [-Encoding <Encoding>] [-Context <Int32[]>] [<CommonParameters>]
```

### ObjectRaw

```
Select-String [-Culture <String>] -InputObject <PSObject> [-Pattern] <String[]> -Raw [-SimpleMatch]
 [-CaseSensitive] [-List] [-NoEmphasis] [-Include <String[]>] [-Exclude <String[]>] [-NotMatch]
 [-AllMatches] [-Encoding <Encoding>] [-Context <Int32[]>] [<CommonParameters>]
```

### Object

```
Select-String [-Culture <String>] -InputObject <PSObject> [-Pattern] <String[]> [-SimpleMatch]
 [-CaseSensitive] [-Quiet] [-List] [-NoEmphasis] [-Include <String[]>] [-Exclude <String[]>]
 [-NotMatch] [-AllMatches] [-Encoding <Encoding>] [-Context <Int32[]>] [<CommonParameters>]
```

### FileRaw

```
Select-String [-Culture <String>] [-Pattern] <String[]> [-Path] <String[]> -Raw [-SimpleMatch]
 [-CaseSensitive] [-List] [-NoEmphasis] [-Include <String[]>] [-Exclude <String[]>] [-NotMatch]
 [-AllMatches] [-Encoding <Encoding>] [-Context <Int32[]>] [<CommonParameters>]
```

### LiteralFileRaw

```
Select-String [-Culture <String>] [-Pattern] <String[]> -LiteralPath <String[]> -Raw [-SimpleMatch]
 [-CaseSensitive] [-List] [-NoEmphasis] [-Include <String[]>] [-Exclude <String[]>] [-NotMatch]
 [-AllMatches] [-Encoding <Encoding>] [-Context <Int32[]>] [<CommonParameters>]
```

### LiteralFile

```
Select-String [-Culture <String>] [-Pattern] <String[]> -LiteralPath <String[]> [-SimpleMatch]
 [-CaseSensitive] [-Quiet] [-List] [-NoEmphasis] [-Include <String[]>] [-Exclude <String[]>]
 [-NotMatch] [-AllMatches] [-Encoding <Encoding>] [-Context <Int32[]>] [<CommonParameters>]
```

## BESCHRIJVING

De `Select-String` cmdlet zoekt naar tekst-en tekst patronen in invoer teken reeksen en bestanden. U kunt `Select-String` vergelijkbaar met **grep** gebruiken in UNIX of **findstr.exe** in Windows.

`Select-String` is gebaseerd op regels tekst. Standaard `Select-String` zoekt de eerste overeenkomst op elke regel en, voor elke overeenkomst, worden de bestands naam, het regel nummer en alle tekst in de regel met de overeenkomst weer gegeven. U kunt direct `Select-String` zoeken naar meerdere overeenkomsten per regel, tekst weer geven voor en na de overeenkomst of een Booleaanse waarde (waar of onwaar) weer geven die aangeeft of er een overeenkomst is gevonden.

`Select-String` maakt gebruik van reguliere expressie matching, maar kan ook een overeenkomst uitvoeren die de invoer doorzoekt voor de tekst die u opgeeft.

`Select-String` kan alle tekst overeenkomsten weer geven of stoppen na de eerste overeenkomst in elk invoer bestand.
`Select-String` kan worden gebruikt om alle tekst weer te geven die niet overeenkomt met het opgegeven patroon.

U kunt ook opgeven dat `Select-String` een bepaalde teken codering moet worden verwacht, bijvoorbeeld wanneer u bestanden van Unicode-tekst zoekt. `Select-String` maakt gebruik van de byte-order-Mark (BOM) om de coderings indeling van het bestand te detecteren. Als het bestand geen stuk lijst heeft, wordt ervan uitgegaan dat de code ring UTF8 is.

## VOORBEELDEN

### Voor beeld 1: een hoofdletter gevoelige overeenkomst zoeken

In dit voor beeld is een hoofdletter gevoelige overeenkomst van de tekst die de pijp lijn naar de cmdlet heeft verzonden `Select-String` .

```powershell
'Hello', 'HELLO' | Select-String -Pattern 'HELLO' -CaseSensitive -SimpleMatch
```

De tekst teken reeksen **Hello** en **Hello** worden in de pijp lijn naar de `Select-String` cmdlet verzonden.
`Select-String` maakt gebruik van de para meter **pattern** om **Hello** op te geven. De para meter **CaseSensitive** geeft aan dat de case alleen moet overeenkomen met het hoofd-hoofdletter patroon. **SimpleMatch** is een optionele para meter en geeft aan dat de teken reeks in het patroon niet wordt ge??nterpreteerd als een reguliere expressie.
`Select-String` Hiermee wordt **Hello** weer gegeven in de Power shell-console.

### Voor beeld 2: overeenkomsten zoeken in tekst bestanden

Met deze opdracht worden alle bestanden `.txt` in de huidige map doorzocht met de bestandsnaam extensie. In de uitvoer worden de regels in die bestanden weer gegeven die de opgegeven teken reeks bevatten.

```powershell
Get-Alias | Out-File -FilePath .\Alias.txt
Get-Command | Out-File -FilePath .\Command.txt
Select-String -Path .\*.txt -Pattern 'Get-'
```

```Output
Alias.txt:8:Alias            cat -> Get-Content
Alias.txt:28:Alias           dir -> Get-ChildItem
Alias.txt:43:Alias           gal -> Get-Alias
Command.txt:966:Cmdlet       Get-Acl
Command.txt:967:Cmdlet       Get-Alias
```

In dit voor beeld `Get-Alias` wordt `Get-Command` met de `Out-File` cmdlet twee tekst bestanden gemaakt in de huidige map **Alias.txt** en **Command.txt**.

`Select-String` gebruikt de para meter **Path** met het `*` Joker teken sterretje () om alle bestanden in de huidige map te doorzoeken met de bestandsnaam extensie `.txt` . De **pattern** -para meter geeft de tekst op die moet overeenkomen met **Get-**. `Select-String` Hiermee wordt de uitvoer in de Power shell-console weer gegeven. De bestands naam en het regel nummer v????r elke regel met inhoud die overeenkomt met de **patroon** parameter.

### Voor beeld 3: zoeken naar een patroon overeenkomst

In dit voor beeld worden meerdere bestanden doorzocht om overeenkomsten te vinden voor het opgegeven patroon. Het patroon gebruikt een reguliere expressie-kwantor. Zie [about_Regular_Expressions](../Microsoft.PowerShell.Core/About/About_Regular_Expressions.md)voor meer informatie.

```powershell
Select-String -Path "$PSHOME\en-US\*.txt" -Pattern '\?'
```

```Output
C:\Program Files\PowerShell\6\en-US\default.help.txt:27:    beginning at https://go.microsoft.com/fwlink/?LinkID=108518.
C:\Program Files\PowerShell\6\en-US\default.help.txt:50:    or go to: https://go.microsoft.com/fwlink/?LinkID=210614
```

De `Select-String` cmdlet gebruikt twee para meters, **pad** en **patroon**. De para meter **Path** maakt gebruik van de variabele `$PSHOME` die de Power shell-map opgeeft. De rest van het pad bevat de submap en **-US** en geeft elk `*.txt` bestand in de map op. De **patroon** parameter geeft aan dat deze overeenkomt met een vraag teken ( `?` ) in elk bestand. Een back slash ( `\` ) wordt gebruikt als escape-teken en is nodig omdat het vraag teken ( `?` ) een reguliere expressie-kwantor is. `Select-String` Hiermee wordt de uitvoer in de Power shell-console weer gegeven. De bestands naam en het regel nummer v????r elke regel met inhoud die overeenkomt met de **patroon** parameter.

### Voor beeld 4: Select-String gebruiken in een functie

In dit voor beeld wordt een functie gemaakt om te zoeken naar een patroon in de Help-bestanden van Power shell. Voor dit voor beeld is de functie alleen aanwezig in de Power shell-sessie. Wanneer de Power shell-sessie is gesloten, wordt de functie verwijderd. Zie [about_Functions](../Microsoft.PowerShell.Core/About/about_Functions.md)voor meer informatie.

```
PS> Function Search-Help
>> {
>> $PSHelp = "$PSHOME\en-US\*.txt"
>> Select-String -Path $PSHelp -Pattern 'About_'
>> }
PS>

PS> Search-Help

C:\Program Files\PowerShell\6\en-US\default.help.txt:67:    The titles of conceptual topics begin with "About_".
C:\Program Files\PowerShell\6\en-US\default.help.txt:70:    Get-Help About_<topic-name>
C:\Program Files\PowerShell\6\en-US\default.help.txt:93:    Get-Help About_Modules : Displays help about PowerShell modules.
C:\Program Files\PowerShell\6\en-US\default.help.txt:97:    about_Updatable_Help
```

De functie wordt gemaakt op de Power shell-opdracht regel. De `Function` opdracht maakt gebruik van de naam **zoeken-Help**. Druk op **Enter** om instructies toe te voegen aan de functie. Voeg bij de `>>` prompt elke instructie toe en druk op **Enter** , zoals wordt weer gegeven in het voor beeld. Nadat het haakje is toegevoegd, keert u terug naar een Power shell-prompt.

De functie bevat twee opdrachten. De `$PSHelp` variabele slaat het pad op naar de Help-bestanden van Power shell. `$PSHOME` is de Power shell-installatiemap met de submap **en-US** waarmee elk `*.txt` bestand in de Directory wordt opgegeven.

De `Select-String` opdracht in de functie maakt gebruik van het **pad** en de **patroon** parameters. De para meter **Path** gebruikt de `$PSHelp` variabele om het pad op te halen. De **patroon** parameter maakt gebruik van de teken reeks **About_** als Zoek criterium.

Als u de functie wilt uitvoeren, typt u `Search-Help` . De opdracht van de functie `Select-String` geeft de uitvoer in de Power shell-console.

### Voor beeld 5: zoeken naar een teken reeks in een Windows-gebeurtenis logboek

In dit voor beeld wordt gezocht naar een teken reeks in een Windows-gebeurtenis logboek. De variabele `$_` vertegenwoordigt het huidige object in de pijp lijn. Zie [about_Automatic_Variables](../Microsoft.PowerShell.Core/About/about_Automatic_Variables.md)voor meer informatie.

```powershell
$Events = Get-WinEvent -LogName Application -MaxEvents 50
$Events | Select-String -InputObject {$_.message} -Pattern 'Failed'
```

De `Get-WinEvent` cmdlet gebruikt de para meter **LogName** om het toepassings logboek op te geven. De para meter **MaxEvents** haalt de 50 meest recente gebeurtenissen uit het logboek op. De logboek inhoud wordt opgeslagen in de variabele met de naam `$Events` .

De `$Events` variabele wordt via de pijp lijn naar de `Select-String` cmdlet verzonden. `Select-String` maakt gebruik van de para meter **input object** . De `$_` variabele vertegenwoordigt het huidige object en `message` is een eigenschap van de gebeurtenis. De **patroon** parameter vissoort de teken reeks **is mislukt** en zoekt naar overeenkomsten in `$_.message` . `Select-String` Hiermee wordt de uitvoer in de Power shell-console weer gegeven.

### Voor beeld 6: een teken reeks zoeken in submappen

In dit voor beeld wordt gezocht naar een map en alle submappen voor een specifieke teken reeks.

```powershell
Get-ChildItem -Path C:\Windows\System32\*.txt -Recurse | Select-String -Pattern 'Microsoft' -CaseSensitive
```

`Get-ChildItem` maakt gebruik van de para meter **Path** om **C:\Windows\System32 \* . txt** op te geven. De **recursie** -para meter bevat de submappen. De objecten worden naar beneden verzonden in de pijp lijn `Select-String` .

`Select-String` maakt gebruik van de **patroon** parameter en specificeert de teken reeks **micro soft**. De para meter **CaseSensitive** wordt gebruikt om de exacte case van de teken reeks overeen te laten komen. `Select-String` Hiermee wordt de uitvoer in de Power shell-console weer gegeven.

> [!NOTE]
> Afhankelijk van uw machtigingen ziet u mogelijk de **toegang geweigerde** berichten in de uitvoer.

### Voor beeld 7: teken reeksen zoeken die niet overeenkomen met een patroon

In dit voor beeld ziet u hoe u gegevens regels uitsluit die niet overeenkomen met een patroon.

```powershell
Get-Command | Out-File -FilePath .\Command.txt
Select-String -Path .\Command.txt -Pattern 'Get', 'Set'  -NotMatch
```

De `Get-Command` cmdlet verzendt objecten van de pijp lijn naar de `Out-File` om het **Command.txt** -bestand in de huidige map te maken. `Select-String` maakt gebruik van de para meter **Path** om het **Command.txt** -bestand op te geven. De para meter **pattern** geeft **Get** en **set** op als zoek patroon. De para meter **NotMatch** uitgesloten **Get** en **set** van de resultaten.
`Select-String` Hiermee wordt de uitvoer weer gegeven in de Power shell-console die geen **Get** of **set** bevat.

### Voor beeld 8: regels voor en na een overeenkomst zoeken

In dit voor beeld ziet u hoe u de lijnen voor en na het overeenkomende patroon kunt ophalen.

```powershell
Get-Command | Out-File -FilePath .\Command.txt
Select-String -Path .\Command.txt -Pattern 'Get-Computer' -Context 2, 3
```

```Output
  Command.txt:986:Cmdlet          Get-CmsMessage           6.1.0.0    Microsoft.PowerShell.Security
  Command.txt:987:Cmdlet          Get-Command              6.1.2.0    Microsoft.PowerShell.Core
> Command.txt:988:Cmdlet          Get-ComputerInfo         6.1.0.0    Microsoft.PowerShell.Management
  Command.txt:990:Cmdlet          Get-Content              6.1.0.0    Microsoft.PowerShell.Management
  Command.txt:991:Cmdlet          Get-ControlPanelItem     3.1.0.0    Microsoft.PowerShell.Management
  Command.txt:992:Cmdlet          Get-Credential           6.1.0.0    Microsoft.PowerShell.Security
```

De `Get-Command` cmdlet verzendt objecten van de pijp lijn naar de `Out-File` om het **Command.txt** -bestand in de huidige map te maken. `Select-String` maakt gebruik van de para meter **Path** om het **Command.txt** -bestand op te geven. De para meter **pattern** geeft **Get-computer** op als zoek patroon. De para meter **context** gebruikt twee waarden, v????r en na, en markeert patroon overeenkomsten in de uitvoer met een punt haak ( `>` ). Met de **context** parameter worden de twee regels v????r het eerste patroon uitgevoerd en worden er drie regels na het laatste patroon overeenkomen.

### Voor beeld 9: alle patroon overeenkomsten zoeken

In dit voor beeld ziet u hoe de para meter **AllMatches** elke overeenkomende patroon in een tekst regel vindt. Standaard `Select-String` zoekt alleen het eerste exemplaar van een patroon in een tekst regel. In dit voor beeld worden object eigenschappen gebruikt die met de cmdlet worden gevonden `Get-Member` .

```
PS> $A = Get-ChildItem -Path "$PSHOME\en-US\*.txt" | Select-String -Pattern 'PowerShell'

PS> $A

C:\Program Files\PowerShell\6\en-US\default.help.txt:3:    PowerShell Help System
C:\Program Files\PowerShell\6\en-US\default.help.txt:6:    Displays help about PowerShell cmdlets and concepts.
C:\Program Files\PowerShell\6\en-US\default.help.txt:9:    PowerShell Help describes PowerShell cmdlets

PS> $A.Matches

Groups   : {0}
Success  : True
Name     : 0
Captures : {0}
Index    : 4
Length   : 10
Value    : PowerShell

PS> $A.Matches.Length

8

PS> $B = Get-ChildItem -Path "$PSHOME\en-US\*.txt" | Select-String -Pattern 'PowerShell' -AllMatches

PS> $B.Matches.Length

9
```

De `Get-ChildItem` cmdlet gebruikt de para meter **Path** . De para meter **Path** maakt gebruik van de variabele `$PSHOME` die de Power shell-map opgeeft. De rest van het pad bevat de submap en **-US** en geeft elk `*.txt` bestand in de map op. De `Get-ChildItem` objecten worden opgeslagen in de `$A` variabele. De `$A` variabele wordt via de pijp lijn naar de `Select-String` cmdlet verzonden. `Select-String` maakt gebruik van de **patroon** parameter om te zoeken in elk bestand naar de teken reeks- **Power shell**.

Van de Power shell-opdracht regel wordt de `$A` variabele-inhoud weer gegeven. Er is een regel die twee exemplaren van de teken reeks **Power shell** bevat.

De `$A.Matches` eigenschap geeft het eerste exemplaar van het patroon **Power shell** op elke regel.

De `$A.Matches.Length` eigenschap telt het eerste exemplaar van het patroon **Power shell** op elke regel.

De `$B` variabele maakt gebruik van dezelfde `Get-ChildItem` en `Select-String` cmdlets, maar voegt de para meter **AllMatches** toe. **AllMatches** vindt elk exemplaar van het patroon **Power shell** op elke regel. De objecten die zijn opgeslagen in de `$A` `$B` variabelen en zijn identiek.

De `$B.Matches.Length` eigenschap neemt toe vanwege elke regel, waarbij elk exemplaar van het patroon **Power shell** wordt geteld.

## PARAMETERS

### -AllMatches

Geeft aan dat de cmdlet zoekt naar meer dan ????n overeenkomst in elke regel tekst. Zonder deze para meter wordt `Select-String` alleen gezocht naar de eerste overeenkomst in elke regel tekst.

Wanneer er `Select-String` meer dan ????n overeenkomst in een tekst regel wordt gevonden, wordt er nog steeds slechts ????n **MatchInfo** -object voor de regel geleverd, maar de eigenschap **matchs** van het object bevat alle overeenkomsten.

> [!NOTE]
> Deze para meter wordt genegeerd als deze wordt gebruikt in combi natie met de para meter **SimpleMatch** . Als u alle overeenkomsten wilt retour neren en het patroon waarnaar u zoekt reguliere expressie tekens bevat, moet u deze tekens weglaten in plaats van **SimpleMatch** te gebruiken. Zie [about_Regular_Expressions](../Microsoft.PowerShell.Core/About/about_Regular_Expressions.md) voor meer informatie over reguliere expressies voor Escapes.

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

### -CaseSensitive

Geeft aan dat de cmdlets overeenkomen met hoofdletter gevoelig. Standaard zijn niet hoofdletter gevoelig.

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

### -Context

Hiermee wordt het opgegeven aantal regels v????r en na de lijn die overeenkomt met het patroon vastgelegd.

Als u ????n getal als waarde voor deze para meter opgeeft, wordt het aantal regels bepaald dat voor en na de overeenkomst is vastgelegd. Als u twee getallen opgeeft als waarde, bepaalt het eerste getal het aantal regels v????r de overeenkomst en het tweede getal bepaalt het aantal regels na de overeenkomst. Bijvoorbeeld `-Context 2,3`.

In de standaard weergave worden regels met een overeenkomst aangeduid met een rechter punt haak ( `>` ) (ASCII 62) in de eerste kolom van de weer gave. Niet-gemarkeerde regels zijn de context.

De para meter **context** wijzigt niet het aantal objecten dat door is gegenereerd `Select-String` .
`Select-String` genereert ????n [MatchInfo](/dotnet/api/microsoft.powershell.commands.matchinfo) -object voor elke overeenkomst. De context wordt opgeslagen als een matrix met teken reeksen in de **context** eigenschap van het object.

Wanneer de uitvoer van een `Select-String` opdracht door de pijp lijn naar een andere opdracht wordt verzonden `Select-String` , doorzoekt de ontvangende opdracht alleen de tekst in de overeenkomende lijn. De overeenkomende lijn is de waarde van de **regel** eigenschap van het object **MatchInfo** , niet de tekst in de context regels. Als gevolg hiervan is de **context** parameter niet geldig voor de ontvangende `Select-String` opdracht.

Wanneer de context een overeenkomst bevat, bevat het **MatchInfo** -object voor elke overeenkomst alle context regels, maar worden de overlappende lijnen slechts eenmaal in de weer gave weer gegeven.

```yaml
Type: System.Int32[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Cultuur

Hiermee geeft u een cultuur naam op die overeenkomt met het opgegeven patroon. De para meter **Culture** moet worden gebruikt in combi natie met de para meter **SimpleMatch** . Bij het standaard gedrag wordt gebruikgemaakt van de cultuur van de huidige Power shell-runs Pace (sessie).

Gebruik de opdracht om een lijst met alle ondersteunde cult uren weer te geven `Get-Culture -ListAvailable` .

Daarnaast accepteert deze para meter de volgende argumenten:

- CurrentCulture, dat is standaard;
- Rang telwoord, dat wil zeggen een binaire vergelijking zonder taal;
- Invariantie, een cultuur onafhankelijke vergelijking.

Met de `Select-String -Culture Ordinal -CaseSensitive -SimpleMatch` opdracht kunt u een snelste binaire vergelijking.

De para meter **Culture** gebruikt Tab-aanvulling om door de lijst met argumenten te bladeren waarmee de beschik bare cult uren worden opgegeven. Als u alle beschik bare argumenten wilt weer geven, gebruikt u de volgende opdracht:

`(Get-Command Select-String).Parameters.Culture.Attributes.ValidValues`

Zie [CultureInfo.name](/dotnet/api//system.globalization.cultureinfo.name)voor meer informatie over de eigenschap .net CultureInfo.name.

De para meter **Culture** is ge??ntroduceerd in Power shell 7.

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: Culture of the current PowerShell session
Accept pipeline input: False
Accept wildcard characters: False
```

### -Encoding

Hiermee geeft u het type code ring voor het doel bestand op. De standaardwaarde is `utf8NoBOM`.

De acceptabele waarden voor deze para meter zijn als volgt:

- `ascii`: Gebruikt de code ring voor de ASCII-tekenset (7-bits).
- `bigendianunicode`: Wordt gecodeerd in UTF-16-indeling met behulp van de byte volgorde big endian.
- `bigendianutf32`: Codeert in UTF-32-indeling met behulp van de byte volgorde big endian.
- `oem`: Maakt gebruik van de standaard codering voor MS-DOS-en console Programma's.
- `unicode`: Wordt gecodeerd in UTF-16-indeling met behulp van de byte volgorde little endian.
- `utf7`: Wordt gecodeerd in de indeling UTF-7.
- `utf8`: Wordt gecodeerd in UTF-8-indeling.
- `utf8BOM`: Code ring in UTF-8-indeling met byte order Mark (BOM)
- `utf8NoBOM`: Code ring in UTF-8-indeling zonder byte order Mark (BOM)
- `utf32`: Gecodeerd in UTF-32-indeling.

Vanaf Power shell 6,2 kunnen met de para meter **Encoding** ook numerieke id's van geregistreerde code pagina's (zoals `-Encoding 1251` ) of teken reeks namen van geregistreerde code pagina's (zoals) worden toegestaan `-Encoding "windows-1251"` . Zie de .NET-documentatie voor [code ring. code tabel](/dotnet/api/system.text.encoding.codepage?view=netcore-2.2)voor meer informatie.

> [!NOTE]
> **UTF-7** _ wordt niet meer aanbevolen om te gebruiken. In Power shell 7,1 wordt een waarschuwing geschreven als u `utf7` de para meter _ *Encoding** opgeeft.

```yaml
Type: System.Text.Encoding
Parameter Sets: (All)
Aliases:
Accepted values: ASCII, BigEndianUnicode, BigEndianUTF32, OEM, Unicode, UTF7, UTF8, UTF8BOM, UTF8NoBOM, UTF32

Required: False
Position: Named
Default value: UTF8NoBOM
Accept pipeline input: False
Accept wildcard characters: False
```

### -Uitsluiten

Sluit de opgegeven items uit. De waarde van deze para meter komt in aanmerking voor de para meter **Path** . Voer een element of patroon van een pad in, zoals `*.txt` . Joker tekens zijn toegestaan.

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

### -Include

Bevat de opgegeven items. De waarde van deze para meter komt in aanmerking voor de para meter **Path** . Voer een element of patroon van een pad in, zoals `*.txt` . Joker tekens zijn toegestaan.

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

### -Input object

Geeft de tekst aan waarnaar moet worden gezocht. Voer een variabele in die de tekst bevat of typ een opdracht of expressie waarmee de tekst wordt opgehaald.

Het gebruik van de para meter **input object** is niet hetzelfde als het verzenden van teken reeksen naar de pijp lijn `Select-String` .

Wanneer u meer dan een teken reeks naar de `Select-String` cmdlet Pipet, zoekt het naar de opgegeven tekst in elke teken reeks en retourneert elke teken reeks die de Zoek tekst bevat.

Wanneer u de para meter **input object** gebruikt voor het verzenden van een verzameling teken reeksen, `Select-String` behandelt de verzameling als ????n gecombineerde teken reeks. `Select-String` retourneert de teken reeksen als eenheid als de Zoek tekst in een wille keurige teken reeks wordt gevonden.

```yaml
Type: System.Management.Automation.PSObject
Parameter Sets: Object, ObjectRaw
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### -Lijst

Alleen het eerste exemplaar van de overeenkomende tekst wordt geretourneerd vanuit elk invoer bestand. Dit is de meest effici??nte manier om een lijst met bestanden op te halen met inhoud die overeenkomt met de reguliere expressie.

`Select-String`Retourneert standaard een **MatchInfo** -object voor elke gevonden overeenkomst.

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

### -LiteralPath

Hiermee geeft u het pad op naar de bestanden die moeten worden doorzocht. De waarde van de para meter **LiteralPath** wordt precies zo gebruikt als deze wordt getypt. Geen tekens worden ge??nterpreteerd als joker tekens. Als het pad escape tekens bevat, plaatst u het tussen enkele aanhalings tekens. Enkele aanhalings tekens geven aan dat Power shell geen karakters interpreteert als escape reeksen. Zie [about_Quoting_Rules](../Microsoft.Powershell.Core/About/about_Quoting_Rules.md)voor meer informatie.

```yaml
Type: System.String[]
Parameter Sets: LiteralFileRaw, LiteralFile
Aliases: PSPath, LP

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -De nadruk

`Select-String`Markeert standaard de teken reeks die overeenkomt met het patroon dat u hebt gezocht met de **patroon** parameter. Met de para meter voor de **nadruk** wordt de markering uitgeschakeld.

De nadruk gebruikt negatieve kleuren op basis van uw Power shell-achtergrond en tekst kleuren. Als uw Power shell-kleuren bijvoorbeeld een zwarte achtergrond met witte tekst zijn. De nadruk is een witte achtergrond met zwarte tekst.

Deze para meter is ge??ntroduceerd in Power shell 7.

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

### -NotMatch

De para meter **NotMatch** vindt tekst die niet overeenkomt met het opgegeven patroon.

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

Hiermee geeft u het pad op naar de bestanden waarnaar moet worden gezocht. Joker tekens zijn toegestaan. De standaard locatie is de lokale map.

Bestanden opgeven in de Directory, zoals `log1.txt` , `*.doc` of `*.*` . Als u alleen een map opgeeft, mislukt de opdracht.

```yaml
Type: System.String[]
Parameter Sets: File, FileRaw
Aliases:

Required: True
Position: 1
Default value: Local directory
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: True
```

### -Patroon

Hiermee geeft u de tekst op elke regel moet worden gevonden. De patroon waarde wordt beschouwd als een reguliere expressie.

Zie [about_Regular_Expressions](../Microsoft.PowerShell.Core/About/about_Regular_Expressions.md)voor meer informatie over reguliere expressies.

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Quiet

Geeft aan dat de cmdlet een Booleaanse waarde retourneert (True of false) in plaats van een **MatchInfo** -object. De waarde is True als het patroon is gevonden; anders is de waarde false.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: File, Object, LiteralFile
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### -RAW

Zorgt ervoor dat de cmdlet alleen de overeenkomende teken reeksen uitvoer in plaats van **MatchInfo** -objecten. Dit is de resultaten die het meest overeenkomen met **de UNIX-** of Windows **findstr.exe** -opdrachten.

Deze para meter is ge??ntroduceerd in Power shell 7.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: ObjectRaw, FileRaw, LiteralFileRaw
Aliases:

Required: True
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### -SimpleMatch

Geeft aan dat de cmdlet een eenvoudige overeenkomst gebruikt in plaats van een reguliere expressie. In een eenvoudige overeenkomst `Select-String` zoekt de invoer voor de tekst in de para meter **pattern** . De waarde van de **patroon** parameter wordt niet ge??nterpreteerd als een reguliere expressie-instructie.

Wanneer **SimpleMatch** wordt gebruikt, is de eigenschap **matchers** van het geretourneerde **MatchInfo** -object ook leeg.

> [!NOTE]
> Als deze para meter wordt gebruikt met de para meter **AllMatches** , wordt de **AllMatches** genegeerd.

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

### CommonParameters

Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable. Zie [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)voor meer informatie.

## INVOER

### System. Management. Automation. PSObject

U kunt elk object dat een **toString** -methode heeft, aan het sluis teken toe `Select-String` .

## UITVOER

### Micro soft. Power shell. commands. MatchInfo, System. Boolean, System. String

Standaard is de uitvoer een set **MatchInfo** -objecten met ????n voor elke gevonden overeenkomst. Als u de **stille** para meter gebruikt, is de uitvoer een **Booleaanse** waarde die aangeeft of het patroon is gevonden.
Als u de **onbewerkte** para meter gebruikt, is de uitvoer een set **teken reeks** objecten die overeenkomen met het patroon.

## OPMERKINGEN

`Select-String` is vergelijkbaar met **grep** in UNIX of **findstr.exe** in Windows.

De **SLS** -alias voor de `Select-String` cmdlet is ge??ntroduceerd in Power Shell 3,0.

> [!NOTE]
> Volgens de [goedgekeurde werk woorden voor Power shell-opdrachten](/powershell/scripting/developer/cmdlet/approved-verbs-for-windows-powershell-commands)is het offici??le alias voorvoegsel voor `Select-*` cmdlets `sc` `sl` . Daarom moet de juiste alias voor `Select-String` zijn `scs` , niet `sls` . Dit is een uitzonde ring op deze regel.

Als u wilt gebruiken `Select-String` , typt u de tekst die u wilt zoeken als waarde voor de **patroon** parameter. Gebruik de volgende criteria om de tekst op te geven die moet worden doorzocht:

- Typ de tekst in een teken reeks tussen aanhalings tekens en sleep deze naar `Select-String` .
- Sla een teken reeks op in een variabele en geef de variabele op als de waarde van de para meter **input object** .
- Als de tekst wordt opgeslagen in bestanden, gebruikt u de para meter **Path** om het pad naar de bestanden op te geven.

`Select-String`De waarde van de **pattern** -para meter wordt standaard ge??nterpreteerd als een reguliere expressie. Zie [about_Regular_Expressions](../Microsoft.PowerShell.Core/About/about_Regular_Expressions.md)voor meer informatie. U kunt de para meter **SimpleMatch** gebruiken om de reguliere expressie overeenkomst te overschrijven. De para meter **SimpleMatch** vindt instanties van de waarde van de para meter **pattern** in de invoer.

De standaard uitvoer van `Select-String` is een **MatchInfo** -object, dat gedetailleerde informatie over de overeenkomsten bevat. De informatie in het object is handig wanneer u zoekt naar tekst in bestanden, omdat **MatchInfo** -objecten eigenschappen hebben zoals **filename** en **Line**. Wanneer de invoer niet van het bestand is, is de waarde van deze para meters **InputStream**.

Als u de gegevens in het **MatchInfo** -object niet nodig hebt, gebruikt u de **stille** para meter. De **stille** para meter retourneert een Booleaanse waarde (waar of onwaar) om aan te geven of deze een overeenkomst heeft gevonden in plaats van een **MatchInfo** -object.

Bij overeenkomende woord groepen `Select-String` gebruikt de huidige cultuur die is ingesteld voor het systeem. Als u de huidige cultuur wilt zoeken, gebruikt u de `Get-Culture` cmdlet.

Als u de eigenschappen van een **MatchInfo** -object wilt zoeken, typt u de volgende opdracht:

`Select-String -Path test.txt -Pattern 'test' | Get-Member | Format-List -Property *`

## GERELATEERDE KOPPELINGEN

[about_Automatic_Variables](../Microsoft.PowerShell.Core/About/about_Automatic_Variables.md)

[about_Comparison_Operators](../Microsoft.PowerShell.Core/About/about_Comparison_Operators.md)

[about_Functions](../Microsoft.PowerShell.Core/About/about_Functions.md)

[about_Quoting_Rules](../Microsoft.Powershell.Core/About/about_Quoting_Rules.md)

[about_Regular_Expressions](../Microsoft.PowerShell.Core/About/about_Regular_Expressions.md)

[Get-alias](Get-Alias.md)

[Get-Child item](../Microsoft.PowerShell.Management/Get-ChildItem.md)

[Get-Command](../Microsoft.PowerShell.Core/Get-Command.md)

[Get-member](Get-Member.md)

[Get-WinEvent](../Microsoft.PowerShell.Diagnostics/Get-WinEvent.md)

[Out-file](Out-File.md)

