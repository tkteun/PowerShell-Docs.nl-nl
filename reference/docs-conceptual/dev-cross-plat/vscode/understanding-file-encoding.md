---
title: Informatie over bestandscodering in VS Code en PowerShell
description: Bestands codering configureren in VS code en Power shell
ms.date: 02/28/2019
ms.openlocfilehash: a4b13bcfbe5cffc4e015a37a5fd64fbb8b91f949
ms.sourcegitcommit: 01a1c253f48b61c943f6d6aca4e603118014015f
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 08/06/2020
ms.locfileid: "87900004"
---
# <a name="understanding-file-encoding-in-vs-code-and-powershell"></a>Informatie over bestandscodering in VS Code en PowerShell

Wanneer u VS code gebruikt om Power shell-scripts te maken en te bewerken, is het belang rijk dat uw bestanden worden opgeslagen met de juiste indeling voor teken versleuteling.

## <a name="what-is-file-encoding-and-why-is-it-important"></a>Wat is bestands codering en waarom is het belang rijk?

VS code beheert de interface tussen een menselijk invoer van teken reeksen in een buffer en lees-en schrijf blokken van bytes naar het bestands systeem. Als VS code een bestand opslaat, wordt een tekst codering gebruikt om te bepalen welke bytes elk teken wordt.

Op dezelfde manier moet, wanneer Power shell een script uitvoert, de bytes in een bestand converteren naar tekens om het bestand opnieuw te maken in een Power shell-programma. Omdat VS code het bestand schrijft en Power shell het bestand leest, moeten ze hetzelfde coderings systeem gebruiken. Dit proces voor het parseren van een Power shell-script gaat over: _bytes_  ->  _tekens_  ->  _tokens_de  ->  _abstracte syntaxis_  ->  _van_de syntax structuur

Zowel VS code als Power shell worden geïnstalleerd met een verstandig standaard coderings configuratie. De standaard codering die door Power shell wordt gebruikt, is echter gewijzigd met de release van Power shell core (v6. x). Om ervoor te zorgen dat u geen problemen hebt met het gebruik van Power shell of de Power shell-extensie in VS code, moet u de VS code en Power shell-instellingen op de juiste wijze configureren.

## <a name="common-causes-of-encoding-issues"></a>Veelvoorkomende oorzaken van het coderen van problemen

Coderings problemen treden op wanneer de code ring van VS code of uw script bestand niet overeenkomt met de verwachte code ring van Power shell. Het is niet mogelijk om in Power shell automatisch de bestands codering te bepalen.

Het is waarschijnlijker dat u problemen hebt met het coderen wanneer u tekens gebruikt die niet voor komt in de [7-bits ASCII-tekenset](https://ascii.cl/). Bijvoorbeeld:

<!-- markdownlint-disable MD038 -->
- Uitgebreide niet-letter-tekens zoals em-streepje ( `—` ), non-Break Space ( ` ` ) of dubbele aanhalings teken `"` ()
- Latijnse tekens met accenten ( `É` , `ü` )
- Niet-Latijnse tekens zoals Cyrillisch ( `Д` , `Ц` )
- CJK-tekens ( `本` , `화` , `が` )

Veelvoorkomende redenen voor het coderen van problemen zijn:

- De code ringen van VS code en Power shell zijn niet gewijzigd ten opzichte van hun standaard waarden. Voor Power shell 5,1 en lager is de standaard codering verschillend van VS code.
- Een andere editor heeft het bestand geopend en overschreven in een nieuwe code ring. Dit gebeurt vaak met de ISE.
- Het bestand is in broncode beheer ingecheckt in een code ring die verschilt van wat VS code of Power shell verwacht. Dit kan gebeuren wanneer samen werkers editors gebruiken met verschillende coderings configuraties.

### <a name="how-to-tell-when-you-have-encoding-issues"></a>Hoe weet ik wanneer u problemen met het coderen hebt

Codeer fouten worden vaak als fouten in scripts geparseerd. Als u vreemde teken reeksen in uw script vindt, kan dit het probleem zijn. In het onderstaande voor beeld wordt een en-streepje ( `–` ) weer gegeven als de tekens `â€"` :

```Output
Send-MailMessage : A positional parameter cannot be found that accepts argument 'Testing FuseMail SMTP...'.
At C:\Users\<User>\<OneDrive>\Development\PowerShell\Scripts\Send-EmailUsingSmtpRelay.ps1:6 char:1
+ Send-MailMessage â€"From $from â€"To $recipient1 â€"Subject $subject  ...
+ ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
    + CategoryInfo          : InvalidArgument: (:) [Send-MailMessage], ParameterBindingException
    + FullyQualifiedErrorId : PositionalParameterNotFound,Microsoft.PowerShell.Commands.SendMailMessage
```

Dit probleem treedt op omdat VS code het teken `–` in UTF-8 als de bytes codeert `0xE2 0x80 0x93` . Wanneer deze bytes worden gedecodeerd als Windows-1252, worden ze geïnterpreteerd als de tekens `â€"` .

U kunt onder andere de volgende vreemde teken reeksen zien:

<!-- markdownlint-disable MD038 -->
- `â€"` In plaats van `–`
- `â€"` In plaats van `—`
- `Ã„2` In plaats van `Ä`
- `Â` in plaats van ` `  (een vaste spatie)
- `Ã©` In plaats van `é`
<!-- markdownlint-enable MD038 -->

Deze handige [Naslag informatie](https://www.i18nqa.com/debug/utf8-debug.html) bevat de algemene patronen die duiden op een UTF-8-of Windows-1252-coderings probleem.

## <a name="how-the-powershell-extension-in-vs-code-interacts-with-encodings"></a>Hoe de Power shell-uitbrei ding in VS code communiceert met code ringen

De Power shell-extensie communiceert op een aantal manieren met scripts:

1. Wanneer scripts worden bewerkt in VS code, wordt de inhoud door VS-code naar de uitbrei ding verzonden. Het [Language server-protocol][] verplichtt dat deze inhoud wordt overgedragen in UTF-8. Daarom is het niet mogelijk om de uitbrei ding de verkeerde code ring te verkrijgen.
1. Wanneer scripts rechtstreeks worden uitgevoerd in de geïntegreerde console, worden ze rechtstreeks door Power shell gelezen uit het bestand. Als de code ring van Power shell verschilt van VS code, kan er iets fout hier worden weer gegeven.
1. Wanneer een script dat is geopend in VS code verwijst naar een ander script dat niet is geopend in VS code, valt de uitbrei ding terug om de inhoud van dat script uit het bestands systeem te laden. De Power shell-extensie wordt standaard ingesteld op UTF-8-code ring, maar gebruikt een [byte-volgorde markering][]of stuk lijst, detectie om de juiste code ring te selecteren.

Het probleem treedt op bij het afnemen van de code ring van een stuk lijst-less-indeling (zoals [UTF-8][] zonder stuk lijst en [Windows-1252][]). De Power shell-extensie wordt standaard ingesteld op UTF-8. De uitbrei ding kan de coderings instellingen van VS code niet wijzigen. Zie [issue #824](https://github.com/Microsoft/VSCode/issues/824)(Engelstalig) voor meer informatie.

## <a name="choosing-the-right-encoding"></a>De juiste code ring kiezen

Verschillende systemen en toepassingen kunnen gebruikmaken van verschillende code ringen:

- In .NET Standard, op het web en in de Linux-wereld is UTF-8 nu de dominante code ring.
- Veel .NET Framework toepassingen gebruiken [UTF-16][]. Voor historische redenen wordt dit ook wel ' Unicode ' genoemd, een term die nu verwijst naar een brede [norm](https://en.wikipedia.org/wiki/Unicode) die zowel UTF-8 als UTF-16 bevat.
- In Windows zijn veel systeem eigen toepassingen die vooraf date Unicode blijven gebruiken standaard Windows-1252.

Unicode-code ringen hebben ook het concept van een byte-volgorde markering (stuk lijst). Stuk lijsten komen aan het begin van de tekst voor om een decoder te laten zien welke code wordt gebruikt voor het coderen van de tekst. Voor multi byte-code ringen geeft de stuk lijst ook de [endian](https://en.wikipedia.org/wiki/Endianness) van de code ring aan. Stuk lijsten zijn ontworpen om bytes te zijn die zelden voor komen in niet-Unicode-tekst, waardoor een redelijke schatting van de tekst Unicode wanneer een stuk lijst aanwezig is.

Stuk lijsten zijn optioneel en hun acceptatie is niet hetzelfde als populair in de Linux-wereld omdat een betrouw bare Conventie van UTF-8 overal wordt gebruikt. De meeste Linux-toepassingen gaan ervan uit dat tekst invoer is gecodeerd in UTF-8. Hoewel veel Linux-toepassingen een stuk lijst herkennen en op de juiste wijze afhandelen, wordt een getal niet in rekening gebracht voor artefacten in tekst die is gemanipuleerd met deze toepassingen.

**Daarom**:

- Als u voornamelijk met Windows-toepassingen en Windows Power shell werkt, moet u de voor keur geven aan een code ring zoals UTF-8 met stuk lijst of UTF-16.
- Als u op verschillende platforms werkt, moet u de voor keur geven aan UTF-8 met stuk lijst.
- Als u voornamelijk werkt in contexten die aan Linux zijn gekoppeld, moet u de voor keur geven aan UTF-8 zonder stuk lijst.
- Windows-1252 en Latijns-1 zijn in wezen oudere code ringen die u zo mogelijk moet vermijden.
  Sommige oudere Windows-toepassingen kunnen echter afhankelijk zijn.
- Het is ook belang rijk dat het ondertekenen van een script [coderings afhankelijke](https://github.com/PowerShell/PowerShell/issues/3466)is, wat betekent dat het wijzigen van de code ring van een ondertekend script opnieuw moet worden ondertekend.

## <a name="configuring-vs-code"></a>VS-code configureren

De standaard codering van VS code is UTF-8 zonder stuk lijst.

Als u de code [ring van VS code][]wilt instellen, gaat u naar de instellingen van VS code (<kbd>CTRL</kbd> + <kbd>,</kbd>) en stelt u de `"files.encoding"` instelling in:

```json
"files.encoding": "utf8bom"
```

Enkele mogelijke waarden zijn:

- `utf8`: [UTF-8] zonder stuk lijst
- `utf8bom`: [UTF-8] met stuk lijst
- `utf16le`: Little Endian [UTF-16]
- `utf16be`: Big endian [UTF-16]
- `windows1252`: [Windows-1252]

U krijgt hiervoor een vervolg keuzelijst te zien in de weer gave GUI of in de JSON-weer gave.

U kunt indien mogelijk ook het volgende toevoegen voor het automatisch detecteren van code ring:

```json
"files.autoGuessEncoding": true
```

Als u niet wilt dat deze instellingen van invloed zijn op alle bestands typen, kunt u in VS code configuraties per taal instellen. Maak een taalspecifieke instelling door instellingen in een veld in te voeren `[<language-name>]` . Bijvoorbeeld:

```json
"[powershell]": {
    "files.encoding": "utf8bom",
    "files.autoGuessEncoding": true
}
```

## <a name="configuring-powershell"></a>Power shell configureren

De standaard codering van Power shell varieert afhankelijk van de versie:

- In Power shell 6 + is de standaard codering UTF-8 zonder stuk lijst op alle platformen.
- In Windows Power shell is de standaard codering doorgaans Windows-1252, een uitbrei ding van [Latijn-1][], ook wel ISO 8859-1 genoemd.

In Power shell 5 + vindt u de standaard codering met de volgende opties:

```powershell
[psobject].Assembly.GetTypes() | Where-Object { $_.Name -eq 'ClrFacade'} |
  ForEach-Object {
    $_.GetMethod('GetDefaultEncoding', [System.Reflection.BindingFlags]'nonpublic,static').Invoke($null, @())
  }
```

Het volgende [script](https://gist.github.com/rjmholt/3d8dd4849f718c914132ce3c5b278e0e) kan worden gebruikt om te bepalen welke code ring uw Power shell-sessie afleidt voor een script zonder een stuk lijst.

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

Het is mogelijk om Power shell te configureren voor het gebruik van een bepaalde code ring, met behulp van profiel instellingen.
Zie de volgende artikelen:

- [@mklement0][antwoord over Power shell-code ring op stack overflow](https://stackoverflow.com/a/40098904).
- [@rkeithhill]het [blog bericht over het afhandelen van een stuk lijst zonder UTF-8-invoer in Power shell](https://rkeithhill.wordpress.com/2010/05/26/handling-native-exe-output-encoding-in-utf8-with-no-bom/).

Het is niet mogelijk om Power shell te dwingen een specifieke invoer codering te gebruiken. In Power shell 5,1 en lager, dat wordt uitgevoerd op Windows met de land instelling ingesteld op en-US, wordt standaard Windows-1252-code ring weer gegeven wanneer er geen stuk lijst is. Andere land instellingen kunnen gebruikmaken van een andere code ring. Om interoperabiliteit te garanderen, is het het beste om scripts in een Unicode-indeling met een stuk lijst op te slaan.

> [!IMPORTANT]
> Andere hulpprogram ma's waarmee u Power shell-scripts kunt aanraken, kunnen worden beïnvloed door uw coderings opties of uw scripts opnieuw versleutelen naar een andere code ring.

### <a name="existing-scripts"></a>Bestaande scripts

Scripts die zich al op het bestands systeem bevinden, moeten mogelijk opnieuw worden gecodeerd met de nieuwe gekozen code ring. In de onderste balk van VS code ziet u het label UTF-8. Klik hierop om de actie balk te openen en selecteer **opslaan met code ring**. U kunt nu een nieuwe code ring voor dat bestand kiezen. Bekijk [de code ring van VS codes][] voor volledige instructies.

Als u meerdere bestanden opnieuw moet versleutelen, kunt u het volgende script gebruiken:

```powershell
Get-ChildItem *.ps1 -Recurse | ForEach-Object {
    $content = Get-Content -Path $_
    Set-Content -Path $_.Fullname -Value $content -Encoding UTF8 -PassThru -Force
}
```

### <a name="the-powershell-integrated-scripting-environment-ise"></a>De Power shell Integrated Scripting Environment (ISE)

Als u ook scripts bewerkt met behulp van de Power shell-ISE, moet u de instellingen voor de code ring hier synchroniseren.

De ISE moet voldoen aan een stuk lijst, maar het is ook mogelijk om reflectie te gebruiken om [de code ring](https://bensonxion.wordpress.com/2012/04/25/powershell-ise-default-saveas-encoding/)in te stellen.
Houd er rekening mee dat dit niet kan worden gehandhaafd tussen opstart handelingen.

### <a name="source-control-software"></a>Broncode beheer software

Sommige hulpprogram ma's voor broncode beheer, zoals git, negeren code ringen. Git houdt alleen de bytes bij. Andere, zoals Azure DevOps of mercurial, is niet mogelijk. Zelfs sommige Git-hulpprogram ma's zijn afhankelijk van het decoderen van tekst.

Als dit het geval is, moet u het volgende doen:

- Configureer de tekst codering in het bron beheer zodat deze overeenkomt met de configuratie van de VS code.
- Zorg ervoor dat al uw bestanden in de juiste code ring zijn ingecheckt in broncode beheer.
- Wees op de hoede van wijzigingen in de code ring die via broncode beheer wordt ontvangen. Een sleutel teken van dit is een verschil waarmee de wijzigingen worden aangegeven, maar waarbij niets lijkt te zijn gewijzigd (omdat het aantal bytes maar tekens bevat).

### <a name="collaborators-environments"></a>Omgevingen van deel nemers

Zorg ervoor dat uw samen werkers op bestanden die u deelt geen instellingen hebben die uw code ring overschrijven door Power Shell-bestanden opnieuw te coderen, boven op het configureren van broncode beheer.

### <a name="other-programs"></a>Andere Program ma's

Elk ander programma dat een Power shell-script leest of schrijft, kan het opnieuw versleutelen.

Een aantal voorbeelden:

- Het klem bord gebruiken om een script te kopiëren en te plakken. Dit is gebruikelijk in scenario's zoals:
  - Een script naar een VM kopiëren
  - Een script uit een e-mail bericht of webpagina kopiëren
  - Een script kopiëren naar of van een micro soft Word-of Power Point-document
- Andere tekst editors, zoals:
  - Kladblok
  - vim
  - Een andere Power shell-script editor
- Hulpprogram ma's voor tekst bewerking, zoals:
  - `Get-Content`/`Set-Content`/`Out-File`
  - Power shell-omleidings operatoren zoals `>` en `>>`
  - `sed`/`awk`
- Program ma's voor bestands overdracht, zoals:
  - Een webbrowser bij het downloaden van scripts
  - Een bestands share

Sommige van deze hulpprogram ma's maken deel uit van bytes in plaats van tekst, maar andere bieden coderings configuraties. In die gevallen waarin u een code ring moet configureren, moet u deze op dezelfde locatie instellen als uw editor codering om problemen te voor komen.

## <a name="other-resources-on-encoding-in-powershell"></a>Andere bronnen voor code ring in Power shell

Er zijn enkele andere leuke berichten over code ring en het configureren van code ring in Power shell die een lees bewerking zijn:

- [@mklement0][overzicht van Power shell-code ring op stack overflow](https://stackoverflow.com/questions/40098771/changing-powershells-default-output-encoding-to-utf-8)
- Eerdere problemen die zijn geopend op VS code-Power shell voor het coderen van problemen:
  - [#1308](https://github.com/PowerShell/VSCode-powershell/issues/1308)
  - [#1628](https://github.com/PowerShell/VSCode-powershell/issues/1628)
  - [#1680](https://github.com/PowerShell/VSCode-powershell/issues/1680)
  - [#1744](https://github.com/PowerShell/VSCode-powershell/issues/1744)
  - [#1751](https://github.com/PowerShell/VSCode-powershell/issues/1751)
- [De klassieke _Joel op software_ schrijven over Unicode](https://www.joelonsoftware.com/2003/10/08/the-absolute-minimum-every-software-developer-absolutely-positively-must-know-about-unicode-and-character-sets-no-excuses/)
- [Coderen in .NET Standard](https://github.com/dotnet/standard/issues/260#issuecomment-289549508)

[@mklement0]: https://github.com/mklement0
[@rkeithhill]: https://github.com/rkeithhill
[Windows-1252]: https://wikipedia.org/wiki/Windows-1252
[Latijns-1]: https://wikipedia.org/wiki/ISO/IEC_8859-1
[UTF-8]: https://wikipedia.org/wiki/UTF-8
[byte-volgorde markering]: https://wikipedia.org/wiki/Byte_order_mark
[UTF-16]: https://wikipedia.org/wiki/UTF-16
[Protocol voor taal server]: https://microsoft.github.io/language-server-protocol/
[Versleuteling van VS code]: https://code.visualstudio.com/docs/editor/codebasics#_file-encoding-support
