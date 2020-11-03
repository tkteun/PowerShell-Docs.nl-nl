---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 10/28/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/out-gridview?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Out-GridView
ms.openlocfilehash: 22e6a8de2b52039e0a23cab135f81ff74bdf929a
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/07/2020
ms.locfileid: "93251278"
---
# Out-GridView

## SAMENVATTING
Hiermee wordt de uitvoer naar een interactieve tabel in een afzonderlijk venster verzonden.

## SYNTAXIS

### PassThru (standaard)

```
Out-GridView [-InputObject <PSObject>] [-Title <String>] [-PassThru] [<CommonParameters>]
```

### Wait

```
Out-GridView [-InputObject <PSObject>] [-Title <String>] [-Wait] [<CommonParameters>]
```

### OutputMode

```
Out-GridView [-InputObject <PSObject>] [-Title <String>] [-OutputMode <OutputModeOption>]
 [<CommonParameters>]
```

## BESCHRIJVING

De `Out-GridView` cmdlet verzendt de uitvoer van een opdracht naar een raster weergave venster waarin de uitvoer in een interactieve tabel wordt weer gegeven.

Omdat deze cmdlet een gebruikers interface vereist, werkt deze niet op Windows Server Core of Windows nano server.

U kunt de volgende functies van de tabel gebruiken om uw gegevens te controleren:

- Kolommen verbergen, weer geven en opnieuw ordenen
- Rijen sorteren
- Snelfilter
- Criteria filter toevoegen
- Kopiëren en plakken

Zie de sectie [opmerkingen](#notes) van dit artikel voor volledige instructies.

> [!NOTE]
> Deze cmdlet is opnieuw geïntroduceerd in Power shell 7. Deze cmdlet is alleen beschikbaar op Windows-systemen die ondersteuning bieden voor het Windows-bureau blad. Voor een platform onafhankelijke versie van deze cmdlet raadpleegt u de module [grafische](https://www.powershellgallery.com/packages/Microsoft.PowerShell.GraphicalTools) weer gave in de PowerShell Gallery.

## VOORBEELDEN

### Voor beeld 1: uitvoer processen naar een raster weergave

In dit voor beeld worden de processen opgehaald die worden uitgevoerd op de lokale computer en verzonden naar een raster weergave venster.

```powershell
Get-Process | Out-GridView
```

### Voor beeld 2: een variabele gebruiken om processen uit te voeren naar een raster weergave

In dit voor beeld worden ook de processen opgehaald die worden uitgevoerd op de lokale computer en verzonden naar een raster weergave venster.

```powershell
$P = Get-Process
$P | Out-GridView
```

De uitvoer van de `Get-Process` cmdlet wordt opgeslagen in de `$P` variabele. Vervolgens `$P` wordt de pipet naar `Out-GridView` .

### Voor beeld 3: een geselecteerde eigenschap weer geven in een raster weergave

In dit voor beeld worden geselecteerde eigenschappen van de actieve processen weer gegeven in een raster weergave.

```powershell
Get-Process | Select-Object -Property Name, WorkingSet, PeakWorkingSet |
  Sort-Object -Property WorkingSet -Descending | Out-GridView
```

De uitvoer van `Get-Process` wordt piped om `Select-Object` de eigenschappen **name** , **workingset** en **PeakWorkingSet** te selecteren. Een andere pijplijn operator verzendt de gefilterde objecten naar de `Sort-Object` cmdlet om ze in aflopende volg orde te sorteren op basis van de waarde van de eigenschap **workingset** .
Vervolgens worden de gesorteerde resultaten gepiped naar `Out-GridView` . U kunt nu de functies van de raster weergave gebruiken om de gegevens te zoeken, te sorteren en te filteren.

### Voor beeld 4: uitvoer opslaan in een variabele en vervolgens een raster weergave uitvoeren

In dit voor beeld wordt de cmdlet-uitvoer in een variabele opgeslagen en vervolgens verzonden naar `Out-GridView` .

```powershell
($A = Get-ChildItem -Path $PSHOME -Recurse) | Out-GridView
```

`Get-ChildItem` Hiermee worden alle bestanden in de installatie directory van Power shell en de bijbehorende submappen met de `$PSHOME` Automatische variabele opgehaald. De volg orde van de bewerkingen wordt door de haakjes in de opdracht ingesteld. Als gevolg hiervan wordt de uitvoer van de `Get-ChildItem` opdracht opgeslagen in de `$A` variabele voordat deze wordt verzonden naar `Out-GridView` .

### Voor beeld 5: uitvoer processen voor een opgegeven computer naar een raster weergave

In dit voor beeld worden de processen weer gegeven die worden uitgevoerd op de Server01-computer in een raster weergave venster.

```powershell
Get-Process -ComputerName "Server01" | ogv -Title "Processes - Server01"
```

De examle gebruikt `ogv` , de alias voor de `Out-GridView` cmdlet. De **title** para meter geeft de venster titel aan.

### Voor beeld 6: uitvoer gegevens van externe computers naar een raster weergave

In dit voor beeld ziet u hoe gegevens worden verzonden die zijn verzameld van externe computers naar `Out-GridView` .

```powershell
Invoke-Command -ComputerName S1, S2, S3 -ScriptBlock {Get-Culture} | Out-GridView
```

`Invoke-Command` wordt uitgevoerd `Get-Culture` op drie externe computers. De resulterende gegevens worden gepiped naar `Out-GridView` . U ziet dat het script blok dat wordt uitgevoerd op de externe computer, de `Out-GridView` opdracht niet bevat. Als dat het geval is, mislukt de opdracht wanneer er is geprobeerd een raster weergave venster te openen op elke externe computer.

### Voor beeld 7: meerdere items door geven via `Out-GridView`

In dit voor beeld kunt u meerdere processen selecteren in het `Out-GridView` venster. De processen die u selecteert, worden door gegeven aan de `Export-Csv` opdracht en naar het `ProcessLog.csv` bestand geschreven.

```powershell
Get-Process | Out-GridView -PassThru | Export-Csv -Path .\ProcessLog.csv
```

Met de para meter **PassThru** van `Out-GridView` kunt u meerdere items naar beneden verplaatsen in de pijp lijn. De para meter **PassThru** is gelijk aan het gebruik van de **Meervoudige** waarde van de para meter **OutputMode** .

### Voor beeld 8: een Windows-snelkoppeling maken naar `Out-GridView`

In dit voor beeld ziet u hoe u de **wait** -para meter van gebruikt `Out-GridView` om een Windows-snelkoppeling naar het venster te maken `Out-GridView` .

```powershell
pwsh -Command "Get-Service | Out-GridView -Wait"
```

Deze opdracht regel kan worden gebruikt in een Windows-snelkoppeling. Zonder de **wait** -para meter wordt Power shell afgesloten zodra het `Out-GridView` venster is geopend, waardoor het `Out-GridView` venster bijna onmiddellijk wordt gesloten.

## PARAMETERS

### -Input object

Hiermee geeft u het object op dat door de cmdlet wordt geaccepteerd als invoer voor `Out-GridView` .

Wanneer u de para meter **input object** gebruikt voor het verzenden van een verzameling objecten naar `Out-GridView` , `Out-GridView` behandelt de verzameling als één verzamelings object en wordt één rij met de verzameling weer gegeven. Als u wilt dat elk object in de verzameling wordt weer gegeven, gebruikt u een pijplijn operator (|) om objecten te verzenden naar `Out-GridView` .

```yaml
Type: System.Management.Automation.PSObject
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### -OutputMode

Hiermee geeft u de items op die het interactieve venster de pijp lijn als invoer naar andere opdrachten verzendt.
Deze cmdlet genereert standaard geen uitvoer. Als u items vanuit het interactieve venster omlaag wilt verzenden, klikt u om de items te selecteren en klikt u vervolgens op OK.

De waarden van deze para meter bepalen hoeveel items u naar beneden kunt verzenden in de pijp lijn.

- Geen.  Geen items. Dit is de standaardwaarde.
- Afzonderlijke. Nul items of één item. Gebruik deze waarde wanneer de volgende opdracht slechts één invoer object kan aannemen.
- Vermenigvuldig. Nul, één of veel items. Gebruik deze waarde wanneer de volgende opdracht meerdere invoer objecten kan hebben. Deze waarde is gelijk aan de **PassThru** -para meter.

```yaml
Type: Microsoft.PowerShell.Commands.OutputModeOption
Parameter Sets: OutputMode
Aliases:
Accepted values: None, Single, Multiple

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -PassThru

Geeft aan dat de cmdlet items van het interactieve venster omlaag verzendt als invoer naar andere opdrachten. Deze cmdlet genereert standaard geen uitvoer. Deze para meter is gelijk aan het gebruik van de **Meervoudige** waarde van de para meter **OutputMode** .

Als u items vanuit het interactieve venster omlaag wilt verzenden, klikt u om de items te selecteren en klikt u vervolgens op OK. Shift-klikken en Ctrl-klikken worden ondersteund.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: PassThru
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### -Titel

Hiermee geeft u de tekst op die wordt weer gegeven in de titel balk van het `Out-GridView` venster. De titel balk geeft standaard de opdracht weer die aanroept `Out-GridView` .

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

### -Wachten

Geeft aan dat de cmdlet de opdracht prompt onderdrukt en voor komt dat Windows Power shell wordt afgesloten totdat het `Out-GridView` venster is gesloten. De opdracht prompt wordt standaard weer gegeven wanneer het `Out-GridView` venster wordt geopend.

Met deze functie kunt u de `Out-GridView` cmdlets in Windows-snelkoppelingen gebruiken. Wanneer `Out-GridView` wordt gebruikt in een snelkoppeling zonder de para meter **wait** , `Out-GridView` wordt het venster alleen weer gegeven voordat Power shell wordt gesloten.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: Wait
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

U kunt elk object verzenden naar deze cmdlet.

## UITVOER

### Geen

Normaal gesp roken worden `Out-GridView` er geen objecten geretourneerd. Wanneer u de para meter **PassThru** gebruikt, worden de objecten die de geselecteerde rijen vertegenwoordigen, geretourneerd naar de pijp lijn.

## OPMERKINGEN

U kunt een externe opdracht niet gebruiken om een raster weergave venster op een andere computer te openen.

De uitvoer van de opdracht die u verzendt `Out-GridView` , kan niet worden geformatteerd met de `Format` cmdlets, zoals `Format-Table` of `Format-Wide` cmdlets. Gebruik de cmdlet om eigenschappen te selecteren `Select-Object` .

Gedeserialiseerd uitvoer van externe opdrachten wordt mogelijk niet juist opgemaakt in het raster weergave venster.

**Sneltoetsen voor**`Out-GridView`

|              Gebruik deze sleutel:              |                                   Om deze actie uit te voeren:                                    |
| --------------------------------------- | -------------------------------------------------------------------------------------------- |
| <kbd>Tabbesturingselement</kbd>                          | Verplaatst de cursor van het vak **filter** naar het menu **criteria toevoegen** aan de tabel en terug. |
| <kbd>Pijl-omhoog</kbd>                      | Eén rij omhoog gaan. Verplaatst naar de kolom koppen van de eerste rij met gegevens.                             |
| <kbd>DownArrow</kbd>                    | Eén rij omlaag.                                                                           |
| <kbd>LeftArrow</kbd>                    | Ga in de rij met kolom koppen naar links en één kolom.                                                  |
| <kbd>RightArrow</kbd>                   | Ga in de rij met kolom koppen naar de rechter kolom.                                                 |
| <kbd>ContextMenuKey</kbd>               | In rij met kolom koppen wordt de optie kolommen selecteren weer gegeven.                                    |
| <kbd>Enter</kbd> of <kbd>spatie balk</kbd> | Sorteer kolom gegevens in rij met kolom koppen (wissel knop A-Z, Z-A).                                    |

**De functies van het grid-weergave venster gebruiken**

**Een kolom weer geven of verbergen:**

1. Klik met de rechter muisknop op een kolomkop en klik op **kolommen selecteren**.
2. Gebruik in het dialoog venster **kolommen selecteren** de pijl toetsen om de kolommen tussen de geselecteerde kolommen te verplaatsen naar de vakken beschik bare kolommen. Alleen kolommen in het vak **kolommen selecteren** worden weer gegeven in het raster weergave venster.

**Volg orde van kolommen wijzigen:**

U kunt kolommen naar de gewenste locatie slepen en neerzetten. U kunt ook de volgende stappen uitvoeren:

1. Klik met de rechter muisknop op een kolomkop en klik op **kolommen selecteren**.
2. Gebruik in het dialoog venster **kolommen selecteren** de knoppen **omhoog** en **omlaag** om de volg orde van de kolommen te wijzigen. De kolommen boven aan de lijst worden links van de kolommen aan de onderkant van de lijst weer gegeven in het raster weergave venster.

**Tabel gegevens sorteren**

- Als u de gegevens wilt sorteren, klikt u op een kolomkop.
- Als u de sorteer volgorde wilt wijzigen, klikt u nogmaals op de kolomkop. Telkens wanneer u op dezelfde koptekst klikt, wisselt de sorteer volgorde tussen oplopend naar aflopende volg orde. De huidige volg orde wordt aangegeven door een drie hoek in de kolomkop.

**Tabel gegevens selecteren**

- Als u een rij wilt selecteren, selecteert u de rij of gebruikt u de pijl-omhoog of omlaag om naar de rij te navigeren.
- Als u alle rijen wilt selecteren (met uitzonde ring van de veldnamenrij), drukt u op <kbd>CTRL</kbd> + <kbd>A</kbd>.
- Als u opeenvolgende rijen wilt selecteren, houdt u de <kbd>SHIFT</kbd> -toets ingedrukt en klikt u op de rijen of met de pijl toetsen.
- Als u niet-opeenvolgende rijen wilt selecteren, drukt u op de toets <kbd>CTRL</kbd> en klikt u op om een rij aan de selectie toe te voegen.
- U kunt geen kolommen selecteren en u kunt niet de gehele rij van de kolom kolomkop selecteren.

**Rijen kopiëren**

- Als u een of meer rijen uit de tabel wilt kopiëren, selecteert u de rijen en drukt u vervolgens op CTRL + C.

  U kunt de gegevens in elk tekst-of spreadsheet programma plakken. U kunt geen kolommen of delen van rijen kopiëren en u kunt de rij met kolom koppen niet kopiëren.

**Zoeken in de tabel (snel filter)**

In het vak filteren kunt u gegevens in de tabel zoeken. Wanneer u in het vak typt, worden alleen items die de getypte tekst bevatten, weer gegeven in de tabel.

- Zoeken naar tekst. Als u wilt zoeken naar tekst in de tabel, typt u in het vak Filter de tekst die u wilt zoeken.
- Zoek naar meerdere woorden. Als u wilt zoeken naar meerdere woorden in de tabel, typt u de woorden gescheiden door spaties. `Out-GridView` geeft rijen weer die alle woorden (logische en) bevatten.
- Zoeken naar letterlijke woord groepen. Als u wilt zoeken naar woord groepen die spaties of speciale tekens bevatten, plaatst u de tekst tussen aanhalings tekens. `Out-GridView` geeft rijen weer die een exacte overeenkomst voor de woord groep bevatten.
- Zoeken in kolommen. Als u tekst in een of meer kolommen wilt zoeken, gebruikt u de volgende indeling:

  `<column>:<text> [<column>:<text>] ...`

  Als u bijvoorbeeld ' net ' wilt vinden in de kolom **DisplayName** , typt u in het vak **filter** :

  `displayname:net`

  Als u rijen met ' net ' wilt zoeken in de kolommen **DisplayName** en **name** , typt u in het vak **filter** :

  `displayname:net name:net`

- Schakel de zoek opdracht uit. Als u de hele tabel opnieuw wilt weer geven, klikt u op de rode X knop in de rechter bovenhoek van het vak **filter** of verwijdert u de tekst uit het vak **filter** .

**Criteria gebruiken om de tabel te filteren**

U kunt regels of criteria gebruiken om te bepalen welke items in de tabel worden weer gegeven. Items worden alleen weer gegeven wanneer ze voldoen aan de criteria die u hebt ingesteld. De beschik bare criteria worden bepaald door de eigenschappen van de objecten die worden weer gegeven in het raster weergave venster en de .NET Framework typen van die eigenschappen.

Elk criterium heeft de volgende indeling:

`<column> <operator> <value>`

De criteria voor verschillende eigenschappen zijn verbonden door **en**. De criteria voor dezelfde eigenschap zijn verbonden door **of**. U kunt de logische connectors niet wijzigen.

De criteria zijn alleen van invloed op de weer gave. Er worden geen items uit de tabel verwijderd.

**Criteria toevoegen**

1. Als u de menu knop **criteria toevoegen** wilt weer geven, klikt u op de Uitvouw pijl in de rechter bovenhoek van het venster.
2. Klik op de menu knop **criteria toevoegen** .
3. Klik om kolommen (eigenschappen) te selecteren. U kunt een of meer eigenschappen selecteren.
4. Wanneer u klaar bent met het selecteren van eigenschappen, klikt u op de knop **toevoegen** .
5. Klik op **Annuleren** om de toevoegingen te annuleren.
6. Klik opnieuw op de knop **criteria toevoegen** om meer criteria toe te voegen.

**Een criterium bewerken**

- Als u een operator wilt wijzigen, klikt u op de waarde Blue operator en selecteert u vervolgens een andere operator in de vervolg keuzelijst.
- Typ een waarde in het vak waarde om een waarde in te voeren of te wijzigen. Als u een ongeldige waarde opgeeft, wordt er een rond X-pictogram weer gegeven. Als u deze wilt verwijderen, wijzigt u de waarde.
- Als u een **or** -instructie wilt maken, voegt u een criterium met dezelfde eigenschap toe.

**Criteria verwijderen**

- Als u geselecteerde criteria wilt verwijderen, klikt u op de rode X naast elk criterium.
- Als u alle criteria wilt verwijderen, klikt u op de knop **Alles wissen** .

## GERELATEERDE KOPPELINGEN

[Out-file](Out-File.md)

[Out-Printer](Out-Printer.md)

[Out-teken reeks](Out-String.md)

