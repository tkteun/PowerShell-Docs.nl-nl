---
title: Informatie over bestandscodering in VSCode en PowerShell
description: Bestandscodering in VSCode en PowerShell configureren
ms.date: 02/28/2019
ms.openlocfilehash: 73e766832d56a08bd5ef16df11899a0aab0badae
ms.sourcegitcommit: 5990f04b8042ef2d8e571bec6d5b051e64c9921c
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 03/12/2019
ms.locfileid: "57795111"
---
# <a name="understanding-file-encoding-in-vscode-and-powershell"></a>Informatie over bestandscodering in VSCode en PowerShell

Wanneer u VS Code gebruikt om te maken en PowerShell-scripts bewerken, is het belangrijk dat uw bestanden worden opgeslagen met behulp van de juiste tekencodering.

## <a name="what-is-file-encoding-and-why-is-it-important"></a>Wat is bestandscodering en waarom is het belangrijk?

VSCode beheert de interface tussen een menselijke invoeren tekenreeksen in een buffer en lezen/schrijven-blokken van bytes voor het bestandssysteem. Wanneer VSCode een bestand slaat, gebruikt een tekstcodering om dit te doen.

Wanneer u een script wordt uitgevoerd in PowerShell moet deze ook de bytes in een bestand converteren naar tekens te reconstrueren van het bestand in een PowerShell-programma. Aangezien VSCode schrijft u het bestand en PowerShell het bestand leest, moeten ze het systeem met dezelfde codering gebruiken. Deze zijn van dit proces van het parseren van een PowerShell-script: *bytes* -> *tekens* -> *tokens*  ->   *abstracte syntaxisstructuur* -> *uitvoering*.

Zowel VSCode en PowerShell zijn geïnstalleerd met een functionele codering standaardconfiguratie. Echter, de standaardversleuteling gebruikt PowerShell is gewijzigd met de versie van PowerShell Core (v6.x). Om ervoor te zorgen er zich geen problemen met PowerShell of de PowerShell-extensie vscode, moet u uw VSCode en PowerShell-instellingen configureren naar behoren.

## <a name="common-causes-of-encoding-issues"></a>Veelvoorkomende oorzaken van problemen met codering

Codering problemen optreden wanneer de codering van VSCode of het scriptbestand komt niet overeen met de verwachte codering van PowerShell. Er is geen manier voor PowerShell om automatisch te bepalen de bestandscodering.

Hebt u waarschijnlijk meer hebben problemen-codering als u tekens die niet in de [-7-bits ASCII-tekenset](https://ascii.cl/). Bijvoorbeeld:

- Accenten Latijnse tekens (`É`, `ü`)
- Niet-Latijnse tekens zoals Cyrillisch (`Д`, `Ц`)
- Han Chinees (`脚`, `本`)

Veelvoorkomende redenen voor het coderen van problemen zijn:

- De coderingen van VSCode en PowerShell zijn niet uit de standaardwaarden gewijzigd. Voor PowerShell 5.1 en onder de standaard wijkt codering af van de VSCode zijn.
- Een andere editor is geopend en het bestand in een nieuwe codering overschreven. Dit gebeurt vaak met de ISE.
- Het bestand is ingeschakeld in broncodebeheer in een codering die verschilt van welke VSCode of PowerShell verwacht. Dit kan gebeuren wanneer de medewerkers editors met verschillende codering configuraties.

### <a name="how-to-tell-when-you-have-encoding-issues"></a>Hoe kunt u zien wanneer u hebt coderingsproblemen

Vaak coderingsfouten zich presenteren als fouten in scripts parseren. Als u vreemd tekenreeksen in uw script kunt vinden, kan dit het probleem zijn. In het voorbeeld hieronder een en-streepje (`–`) wordt weergegeven als de tekens `â€“`:

```Output
Send-MailMessage : A positional parameter cannot be found that accepts argument 'Testing FuseMail SMTP...'.
At C:\Users\<User>\<OneDrive>\Development\PowerShell\Scripts\Send-EmailUsingSmtpRelay.ps1:6 char:1
+ Send-MailMessage â€“From $from â€“To $recipient1 â€“Subject $subject  ...
+ ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
    + CategoryInfo          : InvalidArgument: (:) [Send-MailMessage], ParameterBindingException
    + FullyQualifiedErrorId : PositionalParameterNotFound,Microsoft.PowerShell.Commands.SendMailMessage
```

Dit probleem treedt op omdat VSCode het teken codeert `–` in UTF-8 als het aantal bytes `0xE2 0x80 0x93`.
Wanneer deze bytes worden gedecodeerd als Windows-1252, worden geïnterpreteerd als de tekens `â€“`.

Sommige vreemd tekenreeksen die u kunt tegenkomen zijn onder andere:

<!-- markdownlint-disable MD038 -->
- `â€“` In plaats van `–`
- `â€”` In plaats van `—`
- `Ã„2` In plaats van `Ä`
- `Â` in plaats van ` ` (een vaste spatie)
- `Ã©` In plaats van `é`
<!-- markdownlint-enable MD038 -->

Binnen handbereik [verwijzing](https://www.i18nqa.com/debug/utf8-debug.html) geeft een lijst van de algemene patronen die wijzen op een probleem opgetreden bij codering UTF-8/Windows-1252.

## <a name="how-the-powershell-extension-in-vscode-interacts-with-encodings"></a>De interactie van de PowerShell-extensie in VSCode met coderingen

De extensie van PowerShell communiceert met behulp van scripts in een aantal manieren:

1. Als scripts worden bewerkt in VSCode, worden de inhoud door VSCode verzonden naar de extensie. De [Language Server Protocol][] mandaten dat deze inhoud wordt verzonden in UTF-8. Het is daarom niet mogelijk om de extensie te krijgen van de verkeerde codering.
2. Tijdens de uitvoering van scripts rechtstreeks in de geïntegreerde Console bent ze gelezen uit het bestand door PowerShell direct. Als de PowerShell-codering van de VSCode verschilt, kan iets fout gaan hier.
3. Wanneer u een script dat is geopend in VSCode verwijst naar een ander script dat niet is geopend in VSCode, valt de extensie terug op het laden van de inhoud van het script van het bestandssysteem. De standaardinstelling UTF-8-codering van de PowerShell-extensie, maar maakt gebruik van [byte-volgordemarkering][], of stuklijst, detectie selecteert u de juiste codering.

Het probleem treedt op wanneer ervan uitgaande dat de codering van stuklijst zonder indelingen (zoals [UTF-8][] met geen stuklijst en [Windows-1252][]).
De extensie van PowerShell standaardwaarde is UTF-8. De extensie wijzigen niet encoding van VSCode-instellingen.
Zie voor meer informatie, [uitgeven #824](https://github.com/Microsoft/vscode/issues/824).

## <a name="choosing-the-right-encoding"></a>Kies de juiste codering

Verschillende systemen en toepassingen kunnen verschillende coderingen gebruiken:

- In .NET Standard, op het web en in de wereld Linux is UTF-8 nu bij de dominante codering.
- Veel .NET Framework-toepassingen gebruiken [UTF-16][]. Voor historische doeleinden, dit wordt soms 'Unicode' genoemd, een term die nu verwijst naar een brede [standard](https://en.wikipedia.org/wiki/Unicode) die zowel UTF-8- en UTF-16 bevat.
- Op Windows, worden veel systeemeigen toepassingen die zijn gemaakt vóór publicatie Unicode nog maken standaard gebruik van Windows-1252.

Unicode-coderingen hebben ook het concept van een bytevolgorde markeren (BOM). Stuklijsten optreden aan het begin van de tekst een decoder zien waarvan de codering de tekst die wordt gebruikt. Voor meerdere byte coderingen, geeft de stuklijst ook [endianness](https://en.wikipedia.org/wiki/Endianness) van de codering. Stuklijsten zijn ontworpen om te worden van bytes die in niet-Unicode-tekst, zodat een redelijke schatting tekst is Unicode wanneer een stuklijst aanwezig is.

Stuklijsten zijn optioneel en hun goedkeuring is zo populair zijn in de wereld Linux niet omdat het een betrouwbare conventie UTF-8 overal wordt gebruikt. De meeste Linux-toepassingen wordt ervan uitgegaan dat de tekstinvoer in UTF-8 wordt gecodeerd. Hoewel veel Linux-toepassingen wordt herkend en verwerkt goed een stuklijst, een getal geldt dit niet, waardoor er artefacten in tekst met deze toepassingen zijn gemanipuleerd.

**Daarom**:

- Als u met toepassingen voor Windows en Windows PowerShell werkt, moet u liever een codering, zoals UTF-8 met stuklijst- of UTF-16.
- Als u verschillende platforms werkt, moet u UTF-8 met stuklijst liever.
- Als u voornamelijk in de context van Linux-die zijn gekoppeld werkt, moet u UTF-8 zonder stuklijst liever.
- Windows-1252 en Latijns-1 zijn in feite oudere coderingen die Vermijd indien mogelijk.
  Sommige oudere Windows-toepassingen kunnen echter afhankelijk is van deze.
- Het is ook het vermelden waard dat ondertekening van het script is [encoding-afhankelijke](https://github.com/PowerShell/PowerShell/issues/3466), wat betekent dat een wijziging van de codering op een ondertekende script moet opgeven.

## <a name="configuring-vscode"></a>VSCode configureren

VSCode de standaardcodering is UTF-8 zonder stuklijst.

Om in te stellen [Van VSCode-codering][], gaat u naar de VSCode-instellingen (<kbd>Ctrl<kbd>+</kbd>,</kbd>) en stel de `"files.encoding"` instelling:

```json
"files.encoding": "utf8bom"
```

Enkele mogelijke waarden zijn:

- `utf8`: [UTF-8] zonder stuklijst
- `utf8bom`: [UTF-8] met stuklijst
- `utf16le`: Weinig endian [UTF-16]
- `utf16be`: Big endian [UTF-16]
- `windows1252`: [Windows-1252]

U krijgt een vervolgkeuzelijst voor deze in de GUI-weergave of voltooiingen voor het in de JSON weergeven.

U kunt ook het volgende toevoegen aan autodetectie codering indien mogelijk:

```json
"files.autoGuessEncoding": true
```

Als u niet dat deze instellingen wilt beïnvloeden alle bestandstypen, kan VSCode per taal configuraties. Een instelling taalspecifieke maken door instellingen een `[<language-name>]` veld. Bijvoorbeeld:

```json
"[powershell]": {
    "files.encoding": "utf8bom",
    "files.autoGuessEncoding": true
}
```

## <a name="configuring-powershell"></a>PowerShell configureren

PowerShell de standaardcodering is afhankelijk van versie:

- In PowerShell 6 + is de standaardcodering UTF-8 zonder stuklijst op alle platforms.
- In Windows PowerShell, de standaardcodering is meestal Windows-1252, een uitbreiding van [latin 1][], ook wel aangeduid als ISO 8859-1.

In PowerShell 5 + vindt u de standaardversleuteling aan:

```powershell
[psobject].Assembly.GetTypes() | Where-Object { $_.Name -eq 'ClrFacade'} |
  ForEach-Object {
    $_.GetMethod('GetDefaultEncoding', [System.Reflection.BindingFlags]'nonpublic,static').Invoke($null, @())
  }
```

De volgende [script](https://gist.github.com/rjmholt/3d8dd4849f718c914132ce3c5b278e0e) kan worden gebruikt om te bepalen wat de PowerShell-sessie-codering afleidt voor een script zonder een stuklijst.

```powershell
$badBytes = [byte[]]@(0xC3, 0x80)
$utf8Str = [System.Text.Encoding]::UTF8.GetString($badBytes)
$bytes = [System.Text.Encoding]::ASCII.GetBytes('Write-Output "') + [byte[]]@(0xC3, 0x80) + [byte[]]@(0x22)
$path = Join-Path ([System.IO.Path]::GetTempPath()) 'encodingtest.ps1'

try
{
    [System.IO.File]::WriteAllBytes($path, $bytes)

    switch (& $path)
    {
        $utf8Str
        {
            return 'UTF-8'
            break
        }

        default
        {
            return 'Windows-1252'
            break
        }
    }
}
finally
{
    Remove-Item $path
}
```

Het is mogelijk PowerShell voor het gebruik van een bepaalde codering meer in het algemeen gebruik-profielinstellingen te configureren. Zie de volgende artikelen:

- [@mklement0]de [antwoord over PowerShell-codering op StackOverflow](https://stackoverflow.com/a/40098904).
- [@rkeithhill]de [blogbericht over het afhandelen van stuklijst zonder UTF-8-invoer in PowerShell](https://rkeithhill.wordpress.com/2010/05/26/handling-native-exe-output-encoding-in-utf8-with-no-bom/).

Het is niet mogelijk om af te dwingen PowerShell gebruik van een specifieke invoer codering. PowerShell 5.1 en onder de standaard Windows-1252-codering als er geen stuklijst is. Omwille van de interoperabiliteit is het raadzaam om op te slaan van scripts in een Unicode-indeling met een stuklijst.

> [!IMPORTANT]
> Andere hulpprogramma's hebt die touch PowerShell-scripts kunnen worden beïnvloed door uw keuzes codering of een andere codering van uw scripts opnieuw te coderen.

### <a name="existing-scripts"></a>Bestaande scripts

Scripts al op het bestandssysteem moet mogelijk opnieuw worden gecodeerd naar uw nieuw gekozen codering. In de onderste balk van VSCode ziet u het label UTF-8. Klik hierop om de actiebalk te openen en selecteer **opslaan met codering**. U kunt nu kiezen om een nieuwe codering voor dat bestand. Zie [Van VSCode-codering][] voor volledige instructies.

Als u wilt dat meerdere bestanden opnieuw te coderen, kunt u het volgende script gebruiken:

```powershell
Get-ChildItem *.ps1 -Recurse | ForEach-Object {
    $content = Get-Content -Path $_
    Set-Content -Path $_.Fullname -Value $content -Encoding UTF8 -PassThru -Force
}
```

### <a name="the-powershell-integrated-scripting-environment-ise"></a>De PowerShell Integrated Scripting Environment (ISE)

Als u ook scripts die met behulp van de PowerShell ISE hebt bewerkt, moet u uw encoding-instellingen er synchroniseren.

Het ISE moet voldoen aan een stuklijst, maar het is ook mogelijk om reflectie te te gebruiken [stelt de](https://bensonxion.wordpress.com/2012/04/25/powershell-ise-default-saveas-encoding/).
Houd er rekening mee dat dit worden gehandhaafd tussen startende ondernemingen blijft wouldn't.

### <a name="source-control-software"></a>Software voor bronbeheer

Sommige source control hulpprogramma's, zoals git, negeren coderingen; GIT traceert alleen de bytes.
Andere resources, zoals TFS of Mercurial, mogelijk niet. Zelfs enkele git-hulpprogramma's zijn, is afhankelijk van de tekst te decoderen.

Als dit het geval is, zorg ervoor dat u:

- Configureer de tekst die in uw broncodebeheer zodat deze overeenkomen met de configuratie van uw VSCode-codering.
- Zorg ervoor dat alle bestanden worden gecontroleerd in broncodebeheer in de relevante codering.
- Let van wijzigingen in de codering ontvangen via broncodebeheer. Een sleutel teken van dit is een diff die wijzen op wijzigingen, maar waar niets lijkt te zijn gewijzigd (omdat bytes hebben, maar niet hebt gedaan tekens).

### <a name="collaborators-environments"></a>De deelnemers omgevingen

Naast het configureren van broncodebeheer, ervoor te zorgen dat uw medewerkers op alle bestanden die u deelt geen instellingen de codering uitvoeren overschrijven door het PowerShell-bestanden opnieuw te coderen.

### <a name="other-programs"></a>Andere programma 's

Andere programma's die leest of schrijft een PowerShell-script kan deze opnieuw coderen.

Enkele voorbeelden zijn:

- Met behulp van het Klembord kopiëren en plakken van een script. Dit is gebruikelijk in scenario's zoals:
  - Een script kopieert naar een virtuele machine
  - Een script uit een e-mailadres of webpagina kopiëren
  - Een script kopiëren naar of uit een Microsoft Word- of PowerPoint-document
- Andere teksteditors, zoals:
  - Kladblok
  - vim
  - Een andere PowerShell-script-editor
- Tekst met hulpprogramma's, zoals:
  - `Get-Content`/`Set-Content`/`Out-File`
  - PowerShell-omleiding operators zoals `>` en `>>`
  - `sed`/`awk`
- File transfer-programma's, zoals:
  - Een webbrowser, bij het downloaden van scripts
  - Een bestandsshare

Sommige van deze hulpprogramma's bieden in bytes in plaats van tekst, maar andere codering configuraties bieden. In gevallen waarin u wilt configureren een codering, moet u zodat deze gelijk zijn aan de editor codering om problemen te voorkomen.

## <a name="other-resources-on-encoding-in-powershell"></a>Andere bronnen op codering in PowerShell

Er zijn een paar andere mooie berichten op codering en codering in PowerShell configureren die het noemen waard lezen zijn:

- [@mklement0]de [samenvatting van de PowerShell-codering op StackOverflow](https://stackoverflow.com/questions/40098771/changing-powershells-default-output-encoding-to-utf-8)
- Problemen met vorige geopend op vscode-PowerShell voor het coderen van problemen:
  - [#1308](https://github.com/PowerShell/vscode-powershell/issues/1308)
  - [#1628](https://github.com/PowerShell/vscode-powershell/issues/1628)
  - [#1680](https://github.com/PowerShell/vscode-powershell/issues/1680)
  - [#1744](https://github.com/PowerShell/vscode-powershell/issues/1744)
  - [#1751](https://github.com/PowerShell/vscode-powershell/issues/1751)
- [Het klassieke *Joel op Software* up over Unicode schrijven](https://www.joelonsoftware.com/2003/10/08/the-absolute-minimum-every-software-developer-absolutely-positively-must-know-about-unicode-and-character-sets-no-excuses/)
- [Encoding in .NET Standard](https://github.com/dotnet/standard/issues/260#issuecomment-289549508)


[@mklement0]: https://github.com/mklement0
[@rkeithhill]: https://github.com/rkeithhill
[Windows-1252]: https://wikipedia.org/wiki/Windows-1252
[latin 1]: https://wikipedia.org/wiki/ISO/IEC_8859-1
[UTF-8]: https://wikipedia.org/wiki/UTF-8
[byte-volgordemarkering]: https://wikipedia.org/wiki/Byte_order_mark
[UTF-16]: https://wikipedia.org/wiki/UTF-16
[Language Server Protocol]: https://microsoft.github.io/language-server-protocol/
[Van VSCode-codering]: https://code.visualstudio.com/docs/editor/codebasics#_file-encoding-support
