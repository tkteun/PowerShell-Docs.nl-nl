---
title: Stijlgids voor PowerShell-documentatie
description: Dit artikel bevat de regels van de stijl voor het schrijven van Power shell-documentatie.
ms.date: 03/05/2020
ms.topic: conceptual
ms.openlocfilehash: 32df641f7cafa2a5bfcf1bcbf94be594aa77c7d0
ms.sourcegitcommit: 105c69ecedfe5180d8c12e8015d667c5f1a71579
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/02/2020
ms.locfileid: "85837440"
---
# <a name="powershell-docs-style-guide"></a>Stijlgids voor PowerShell-documentatie

Dit artikel bevat richt lijnen die specifiek zijn voor de Power shell-docs-inhoud. Dit is gebaseerd op de informatie die wordt beschreven in het [overzicht](overview.md#get-started-writing-docs).

## <a name="product-terminology"></a>Productterminologie

Er zijn verschillende varianten van PowerShell.

- **PowerShell**: Dit is de standaard. We overwegen Power shell 7 en nog eens te zijn. de echte Power shell gaat verder.
- **Power shell core** -Power shell gebouwd op .net core. Het gebruik van de term **core** moet worden beperkt tot gevallen waarin het nodig is om het te onderscheiden van Windows Power shell.
- **Windows Power shell** -Power shell is gebouwd op .NET Framework. Windows Power shell wordt alleen in Windows geleverd en vereist het volledige Framework.

  Over het algemeen kunnen verwijzingen naar ‘Windows PowerShell’ in documentatie worden vervangen door ‘PowerShell’.
  ' Windows Power shell ' moet worden gebruikt wanneer ' Windows Power Shell-specifiek gedrag wordt besproken.

Gerelateerde producten

- **Visual Studio code (VS code)** : dit is de gratis open source editor van micro soft. Bij de eerste vermelding moet de volledige naam worden gebruikt. Daarna kunt u **VS code**gebruiken. Gebruik niet ' VSCode '.
- **Power shell-extensie voor Visual Studio code** : de uitbrei ding schakelt versus code in voor de voor Keurs-IDE voor Power shell. Bij de eerste vermelding moet de volledige naam worden gebruikt. Daarna kunt u de **Power shell-extensie**gebruiken.
- **Azure PowerShell** : dit is de verzameling Power shell-modules die worden gebruikt voor het beheren van Azure-Services.
- **Azure stack Power shell** : dit is de verzameling Power shell-modules die worden gebruikt voor het beheren van de hybride Cloud oplossing van micro soft.

## <a name="markdown-specifics"></a>Details van prijs verlaging

Het micro soft open publishing-systeem (OPS) dat onze documentatie bouwt, maakt gebruik van [markdig][] voor het verwerken van de verkortings documenten. Markdig parseert de documenten op basis van de regels van de meest recente [CommonMark][] -specificatie.

De nieuwe CommonMark-specificatie is veel strikter dan de constructie van sommige prijs verlagings elementen. Let op de details die in dit document worden gegeven.

### <a name="blank-lines-spaces-and-tabs"></a>Witregels, spaties en tabs

Witregels geven ook het einde van een blok aan in Markdown. Er moet één witregel tussen verschillende typen Markdown-blokken zijn (zoals tussen een alinea en een lijst of koptekst).

Verwijder dubbele witregels. Meerdere lege regels worden weer gegeven als één lege regel in HTML, zodat er geen doel is voor meerdere lege regels. Er zijn meerdere lege regels in een code blok die het code blok opsplitsen.

Verwijder extra spaties aan het einde van regels.

> [!NOTE]
> Spatiegebruik is erg belangrijk in Markdown. Gebruik altijd spaties in plaats van harde tabs. Volg spaties kunnen veranderen hoe de weer gave van de prijs wordt gerenderd.

### <a name="titles-and-headings"></a>Titels en koppen

Gebruik alleen [ATX-kopteksten][atx] (kopteksten in #-stijl in plaats van `=`- of `-`-stijl).

- Gebruik alleen zinnen - alleen eigennamen en de eerste letter van een titel of koptekst moet een hoofdletter krijgen
- Er moet één spatie zijn tussen de `#` en de eerste letter van de koptekst
- Kopteksten moeten worden omgeven door één lege regel
- Slechts één H1 per document
- Koptekst niveaus moeten met één worden verhoogd. Geen niveaus overs Laan
- Geen vette of andere opmaak gebruiken in kopteksten

### <a name="limit-line-length-to-100-characters"></a>Beperk de lengte van regels tot 100 tekens

Dit geldt voor conceptuele artikelen en cmdlet-verwijzingen. Als u de lijn lengte beperkt, wordt de Lees baarheid van Git-verschillen en-geschiedenis verbeterd. Het maakt het ook gemakkelijker voor andere schrijvers om bijdragen te maken.

Gebruik de [uitprijs][reflow] uitbreiding opnieuw plaatsen in Visual Studio code om alinea's eenvoudig opnieuw te plaatsen zodat deze overeenkomen met de voorgeschreven regel lengte.

About_topics is beperkt tot 80 tekens. Zie [verwijzings artikelen bewerken](./editing-cmdlet-ref.md#formatting-about_-files)voor meer informatie.

### <a name="lists"></a>Lijsten

Als uw lijst meerdere zinnen of alinea’s bevat, kunt u overwegen een koptekst op subniveau te gebruiken in plaats van een lijst.

Lijsten moeten worden omgeven door één lege regel.

#### <a name="unordered-lists"></a>Niet-geordende lijsten

Beëindig lijstitems niet met een punt, tenzij ze meerdere zinnen bevatten. Gebruik het afbreekstreepje (`-`) als opsommingsteken voor een lijstitem. Dit voorkomt verwarring met vette of cursieve markeringen, waarbij het sterretje [`*`] wordt gebruikt. Voeg een regel toe en lijn de inspringing uit met het eerste teken achter het opsommingsteken om een alinea of andere elementen onder een opsomming op te nemen.

Bijvoorbeeld:

```markdown
This is a list that contain sub-elements under a bullet item.

- First bullet item

  Sentence explaining the first bullet.

  - Sub-bullet item

    Sentence explaining the sub-bullet.

- Second bullet item
- Third bullet item
```

Dit is een lijst met subelementen onder een opsommingsteken.

- Item van eerste opsomming

  Zin met uitleg voor de eerste opsomming.

  - Item van subopsommingsteken

    Zin met uitleg voor de subopsomming.

- Item van tweede opsomming
- Item van derde opsomming

#### <a name="ordered-lists"></a>Geordende lijsten

Lijn de inspringing uit met het eerste teken achter het itemnummer om een alinea of andere elementen onder een genummerd item op te nemen. Alle items in een genummerde lijst moeten het nummer gebruiken in `1.` plaats van elk item te verhogen. Bij het weergeven van de Markdown wordt de waarde automatisch verhoogd. Hierdoor kunnen items gemakkelijker in een andere volgorde worden geplaatst en wordt de inspringing van onderliggende inhoud gestandaardiseerd.

Bijvoorbeeld:

```markdown
1. For the first element, insert a single space after the 1. Long sentences should be
   wrapped to the next line and must line up with the first character after the numbered
   list marker.

   To include a second element (like this one), insert a line break after the first
   and align indentations. The indentation of the second element must line up with
   the first character after the numbered list marker. For single digit items, like
   this one, you indent to column 4. For double digits items, for example item number
   10, you indent to column 5.

1. The next numbered item starts here.
```

De resulterende prijs verlaging wordt als volgt weer gegeven:

1. Plaats bij het eerste element een spatie achter de 1. Lange zinnen moeten passend worden gemaakt op de volgende regel en worden uitgelijnd met het eerste teken na de markering van de genummerde lijst.

   U kunt een tweede element (zoals dit) opnemen door een nieuwe regel na de eerste in te voegen en de inspringing uit te lijnen. De inspringing van het tweede element moet worden uitgelijnd met het eerste teken na de markering van de genummerde lijst. Voor items met één cijfer, zoals dit, springt u in naar kolom 4. Voor items met dubbele cijfers, zoals nummer 10, springt u in naar kolom 5.

1. Het volgende genummerde item begint hier.

### <a name="images"></a>Installatiekopieën

De syntaxis voor het insluiten van een afbeelding is:

```markdown
![[alt text]](<folderPath>)

Example:
![Introduction](./media/overview/Introduction.png)
```

Hierbij is `alt text` een korte beschrijving van de afbeelding en `<folder path>` een relatief pad naar de afbeelding. Voor schermlezers voor visueel gehandicapten is alternatieve tekst nodig. Dit is ook handig wanneer de afbeelding niet kan worden weergegeven door een sitebug.

Afbeeldingen moeten worden opgeslagen in een `media/<article-name>` map in de map waarin het artikel zich bevindt.
Afbeeldingen moeten niet worden gedeeld tussen artikelen. Maak onder de map `media` een map die overeenkomt met de bestandsnaam van uw artikel. Kopieer de afbeeldingen voor dat artikel naar de nieuwe map. Als een afbeelding door meerdere artikelen wordt gebruikt, moet elke afbeeldingsmap een kopie van het afbeeldingsbestand bevatten. Dit voorkomt dat een wijziging voor een afbeelding in het ene artikel gevolgen heeft voor het andere artikelen.

De volgende afbeeldings bestands typen worden ondersteund: `*.png` , `*.gif` , `*.jpeg` , `*.jpg` , `*.svg`

### <a name="markdown-extensions-supported-by-open-publishing"></a>Markdown-extensies ondersteund door Open Publishing

Het [Microsoft docs authoring Pack](/contribute/how-to-write-docs-auth-pack) bevat hulpprogram ma's die ondersteuning bieden voor functies die uniek zijn voor het publicatie systeem. Waarschuwingen zijn een uitkortings extensie voor het maken van Block quotes die op docs.microsoft.com worden weer gegeven met kleuren en pictogrammen die de betekenis van de inhoud markeren. De volgende typen waarschuwingen worden ondersteund:

```markdown
> [!NOTE]
> Information the user should notice even if skimming.

> [!TIP]
> Optional information to help a user be more successful.

> [!IMPORTANT]
> Essential information required for user success.

> [!CAUTION]
> Negative potential consequences of an action.

> [!WARNING]
> Dangerous certain consequences of an action.
```

Deze waarschuwingen zien er op docs.microsoft.com als volgt uit:

Notitie blok

> [!NOTE]
> Information the user should notice even if skimming.

Info blok

> [!TIP]
> Optional information to help a user be more successful.

Belang rijk blok

> [!IMPORTANT]
> Essential information required for user success.

Waarschuwings blok

> [!CAUTION]
> Negative potential consequences of an action.

Waarschuwings blok

> [!WARNING]
> Bepaalde gevaarlijke gevolgen van een actie.

### <a name="hyperlinks"></a>Hyperlinks

- Hyper links moeten de syntaxis van de korting gebruiken `[friendlyname](url-or-path)`
- Koppelingen moeten indien mogelijk HTTPS zijn.
- Koppelingen moeten een beschrijvende naam hebben, meestal de titel van het onderwerp waarnaar wordt verwezen
- Met alle items in de sectie ' Verwante koppelingen ' aan de onderkant moet een Hyper link worden
- Gebruik geen accents graves, vetgedrukte tekst of andere opmaak binnen de haakjes van een hyperlink.
- Bare Url's kunnen worden gebruikt wanneer u aan het praten bent over een specifieke URI. De URI moet worden inge sloten in accents graves. Bijvoorbeeld:

  ```markdown
  By default, if you do not specify this parameter, the DMTF standard resource URI
  `http://schemas.dmtf.org/wbem/wscim/1/cim-schema/2/` is used and the class name is appended to it.
  ```

#### <a name="linking-to-other-content"></a>Koppeling naar andere inhoud

Er zijn twee typen hyper links die worden ondersteund door het publicatie systeem:

Een **URL-koppeling** kan een URL-pad zijn dat relatief is ten opzichte van de hoofdmap van docs.Microsoft.com. Of een absolute URL die de syntaxis van de volledige URL bevat. Bijvoorbeeld: `https:/github.com/MicrosoftDocs/PowerShell-Docs`

- Gebruik URL-koppelingen wanneer u een koppeling maakt naar inhoud buiten Power shell-docs of tussen Naslag informatie over de cmdlet en conceptuele artikelen in Power shell-docs. De eenvoudigste manier om een relatieve koppeling te maken, is door de URL te kopiëren uit uw browser en vervolgens te verwijderen `https://docs.microsoft.com/en-us` van de waarde die u in de prijs opsplitsen hebt geplakt.
- Land instellingen niet opnemen in Url's op Eigenschappen van micro soft (bijv. verwijderen `/en-us` van URL).
- Verwijder overbodige query parameters uit de URL, tenzij u een koppeling moet maken naar een specifieke versie van een artikel. Voorbeelden:
  - `?view=powershell-5.1` : dit wordt gebruikt om een koppeling te maken naar een specifieke versie van Power shell
  - `?redirectedfrom=MSDN` : deze wordt toegevoegd aan de URL wanneer u wordt omgeleid van een oud artikel naar de nieuwe locatie
- Alle Url's naar externe websites moeten HTTPS gebruiken, tenzij dat niet geldig is voor de doel site.

Een **koppeling** naar een bestand wordt gebruikt om te koppelen van het ene referentie artikel naar het andere of van het ene conceptuele artikel naar het andere. Als u een verwijzing naar een referentie artikel moet koppelen voor een specifieke versie van Power shell, moet u een URL-koppeling gebruiken.

- Bestands koppelingen bevatten een relatief bestandspad (bijvoorbeeld: `../folder/file.md` )
- Alle bestands paden gebruiken tekens voor voorwaartse slash ( `/` )

Uitgebreide koppeling is toegestaan voor URL-en bestands koppelingen. Voeg het anker toe aan het einde van het doelpad.
Bijvoorbeeld:

- `[about_Splatting](about_Splatting.md#splatting-with-arrays)`
- `[custom key bindings](https://code.visualstudio.com/docs/getstarted/keybindings#_custom-keybindings-for-refactorings)`

Zie [koppelingen in documentatie gebruiken](/contribute/how-to-write-links)voor meer informatie.

## <a name="formatting-command-syntax-elements"></a>Syntaxiselementen van opdrachten opmaken

- Gebruik altijd de volledige naam voor cmdlets en para meters. Vermijd het gebruik van aliassen tenzij u de alias expliciet demonstreert.

- Eigenschap, para meter, object, type namen, klassen namen en klassen methoden moeten **vet**zijn.
  - Eigenschaps-en parameter waarden moeten worden verpakt in accents graves ( `` ` `` ).
  - Wanneer u verwijst naar typen met behulp van de stijl met tussen haakjes, gebruikt u accents graves. Bijvoorbeeld: `[System.Io.FileInfo]`

- Taal trefwoorden, namen van cmdlets, functies, variabelen, systeem eigen exe, bestands paden en in-line syntaxis voorbeelden moeten worden verpakt in apostroffen- `` ` `` tekens ().

  Bijvoorbeeld:

  ~~~markdown
  The following code uses `Get-ChildItem` to list the contents of `C:\Windows` and assigns
  the output to the `$files` variable.

  ```powershell
  $files = Get-ChildItem C:\Windows
  ```
  ~~~

  - Wanneer naar een parameter wordt verwezen aan de hand van de naam, moet de naam **vet** zijn. Wanneer het gebruik van een parameter met een afbreekstreepje als voorvoegsel wordt gedemonstreerd, moet de parameter tussen accents graves worden geplaatst. Bijvoorbeeld:

    ```markdown
    The parameter's name is **Name**, but it is typed as `-Name` when used on the command
    line as a parameter.
    ```

  - Wanneer een voorbeeld van het gebruik van een externe opdracht wordt gebruikt, moet het voorbeeld tussen accents graves zijn geplaatst.
    Neem altijd de bestands extensie op in de systeem eigen opdracht. Bijvoorbeeld:

    ```markdown
    To start the spooler service on a remote computer named DC01, you type `sc.exe \\DC01 start spooler`.
    ```

    Met inbegrip van de bestands extensie zorgt ervoor dat de juiste opdracht wordt uitgevoerd volgens de opdracht prioriteit van Power shell.

- Als u een conceptueel artikel (in tegenstelling tot referentie-inhoud) schrijft, moet de eerste instantie van een cmdlet-naam een hyperlink naar de cmdlet-documentatie bevatten. Gebruik geen accents graves, vetgedrukte tekst of andere opmaak binnen de haakjes van een hyperlink.

  Bijvoorbeeld:

  ```markdown
  This [Write-Host](/powershell/module/Microsoft.PowerShell.Utility/Write-Host) cmdlet
  uses the **Object** parameter to ...
  ```

  Zie de sectie [hyper links](#hyperlinks) in dit artikel voor meer informatie.

## <a name="markdown-for-code-samples"></a>Prijs verlaging voor code voorbeelden

Markdown ondersteunt twee verschillende codestijlen:

- **Code reeksen (inline)** : gemarkeerd met één apostroffen ( `` ` `` )-teken. Wordt gebruikt in een alinea in plaats van als een zelfstandig blok.
- **Code blokken** : een blok met meerdere regels dat is omgeven door Triple-apostroffen ( `` ``` `` ) teken reeksen. Code blokken kunnen ook een taal label volgen volgens het accents graves. Het taal label schakelt syntaxis markering in voor de inhoud van het code blok.

Alle codeblokken moeten zich binnen een afscheiding bevinden. Gebruik nooit inspringing voor code blokken. Met prijs verlaging wordt dit patroon toegestaan, maar dit kan een probleem zijn en moet worden vermeden.

Een code blok bestaat uit een of meer regels code omgeven door een code Fence van Triple-apostroffen ( `` ``` `` ).
De markeringen voor de codeafscheiding moeten zich op een eigen regel voor en na het codevoorbeeld bevinden. De markering na het begin van het codeblok heeft mogelijk een optioneel taallabel. In het Open Publishing System (OPS) van Microsoft wordt het taallabel gebruikt om de functie voor markering van de syntaxis te ondersteunen.

Zie [Geomheiningde code blokken](/contribute/code-in-docs#fenced-code-blocks) in de hand leiding gecentraliseerde Inzender voor een volledige lijst met ondersteunde taal codes.

OPS voegt tevens een knop **Kopiëren** toe waarmee u de inhoud van het codeblok naar het klembord kopieert. Zo kunt u de code snel in een script plakken om het code voorbeeld te testen. Niet alle voor beelden in onze documentatie zijn echter bedoeld om te worden uitgevoerd als. Sommige code blokken zijn eenvoudige illustraties van een Power shell-concept.

Er zijn drie typen code blokken die in onze documentatie worden gebruikt:

1. Syntaxis blokken
1. Illustratieve voorbeelden
1. Uitvoerbare voorbeelden

### <a name="syntax-code-blocks"></a>Syntaxis code blokken

Syntaxis code blokken worden gebruikt voor het beschrijven van de syntaxis structuur van een opdracht. Gebruik geen taal code op de code Fence. Dit voorbeeld toont alle mogelijke parameters van de `Get-Command`-cmdlet.

~~~markdown
```
Get-Command [-Verb <String[]>] [-Noun <String[]>] [-Module <String[]>]
  [-FullyQualifiedModule <ModuleSpecification[]>] [-TotalCount <Int32>] [-Syntax]
  [-ShowCommandInfo] [[-ArgumentList] <Object[]>] [-All] [-ListImported]
  [-ParameterName <String[]>] [-ParameterType <PSTypeName[]>] [<CommonParameters>]
```
~~~

Dit voorbeeld bevat een beschrijving van de `for`-instructie in algemene termen:

~~~markdown
```
for (<init>; <condition>; <repeat>)
{<statement list>}
```
~~~

### <a name="illustrative-examples"></a>Illustratieve voorbeelden

Illustratieve voorbeelden worden gebruikt om een PowerShell-concept uit te leggen. Ze zijn niet bedoeld om naar het klembord te worden gekopieerd en te worden uitgevoerd. Deze worden meestal gebruikt voor eenvoudige voor beelden die eenvoudig te typen zijn en eenvoudig te begrijpen zijn. Het code blok kan de Power shell-prompt en voorbeeld uitvoer bevatten.

Hier volgt een eenvoudig voor beeld van de Power shell-vergelijkings operatoren. In dit geval is het niet de bedoeling dat de lezer dit voorbeeld kopieert en uitvoert.

~~~markdown
```powershell
PS> 2 -eq 2
True

PS> 2 -eq 3
False

PS>  1,2,3 -eq 2
2

PS> "abc" -eq "abc"
True

PS> "abc" -eq "abc", "def"
False

PS> "abc", "def" -eq "abc"
abc
```
~~~

### <a name="executable-examples"></a>Uitvoerbare voorbeelden

Complexe voor beelden of voor beelden die bedoeld zijn om te worden gekopieerd en uitgevoerd, moeten de volgende opmaak voor blok stijl gebruiken:

~~~markdown
```powershell
<Your PowerShell code goes here>
```
~~~

De uitvoer die door PowerShell-opdrachten wordt weergegeven, moet zich in een **Uitvoer**-codeblok bevinden om markering van de syntaxis te voorkomen. Bijvoorbeeld:

~~~markdown
```powershell
Get-Command -Module Microsoft.PowerShell.Security
```

```Output
CommandType  Name                        Version    Source
-----------  ----                        -------    ------
Cmdlet       ConvertFrom-SecureString    3.0.0.0    Microsoft.PowerShell.Security
Cmdlet       ConvertTo-SecureString      3.0.0.0    Microsoft.PowerShell.Security
Cmdlet       Get-Acl                     3.0.0.0    Microsoft.PowerShell.Security
Cmdlet       Get-AuthenticodeSignature   3.0.0.0    Microsoft.PowerShell.Security
Cmdlet       Get-CmsMessage              3.0.0.0    Microsoft.PowerShell.Security
Cmdlet       Get-Credential              3.0.0.0    Microsoft.PowerShell.Security
Cmdlet       Get-ExecutionPolicy         3.0.0.0    Microsoft.PowerShell.Security
Cmdlet       Get-PfxCertificate          3.0.0.0    Microsoft.PowerShell.Security
Cmdlet       New-FileCatalog             3.0.0.0    Microsoft.PowerShell.Security
Cmdlet       Protect-CmsMessage          3.0.0.0    Microsoft.PowerShell.Security
Cmdlet       Set-Acl                     3.0.0.0    Microsoft.PowerShell.Security
Cmdlet       Set-AuthenticodeSignature   3.0.0.0    Microsoft.PowerShell.Security
Cmdlet       Set-ExecutionPolicy         3.0.0.0    Microsoft.PowerShell.Security
Cmdlet       Test-FileCatalog            3.0.0.0    Microsoft.PowerShell.Security
Cmdlet       Unprotect-CmsMessage        3.0.0.0    Microsoft.PowerShell.Security
```
~~~

Het codelabel **Uitvoer** is geen officiële ‘taal’ die door het systeem voor het markeren van syntaxis wordt ondersteund.
Dit label is echter nuttig omdat OPS het label "uitvoer" toevoegt aan het frame van de code op de webpagina. Het vak uitvoer code heeft geen syntaxis markering.

## <a name="coding-style-rules"></a>Stijlregels voor code

### <a name="avoid-line-continuation-in-code-samples"></a>Voortzetting van regels in codevoorbeelden vermijden

Vermijd tekens voor voortzetting van de regel (`` ` ``) in PowerShell-codevoorbeelden. Deze zijn moeilijk te zien en kunnen problemen veroorzaken als er extra spaties aan het einde van de regel staan.

- Gebruik PowerShell-splatting om de regellengte in te korten voor cmdlets die veel parameters bevatten.
- Profiteer van de mogelijkheden voor natuurlijke regeleinden in PowerShell, zoals na het pijpteken (`|`), accolades en haakjes.

### <a name="avoid-using-powershell-prompts-in-examples"></a>PowerShell-prompts vermijden in voorbeelden

Het gebruik van de prompt-tekenreeks wordt afgeraden en moet worden beperkt tot scenario’s die zijn bedoeld om het gebruik van de opdrachtregel te illustreren. Voor de meeste van deze voor beelden moet de prompt teken reeks zijn `PS>` . Deze prompt is onafhankelijk van indicatoren voor specifieke besturingssystemen.

Prompts zijn vereist voor voorbeelden waarin opdrachten worden weergegeven waarmee de prompt wordt aangepast of als het getoonde pad van belang is voor het scenario dat wordt geïllustreerd. In het volgende voorbeeld wordt getoond hoe de prompt verandert als de registerprovider wordt gebruikt.

```powershell
PS C:\> cd HKCU:\System\
PS HKCU:\System\> dir

    Hive: HKEY_CURRENT_USER\System

Name                   Property
----                   --------
CurrentControlSet
GameConfigStore        GameDVR_Enabled                       : 1
                       GameDVR_FSEBehaviorMode               : 2
                       Win32_AutoGameModeDefaultProfile      : {2, 0, 1, 0...}
                       Win32_GameModeRelatedProcesses        : {1, 0, 1, 0...}
                       GameDVR_HonorUserFSEBehaviorMode      : 0
                       GameDVR_DXGIHonorFSEWindowsCompatible : 0
```

### <a name="do-not-use-aliases-in-examples"></a>Geen aliassen gebruiken in voorbeelden

Gebruik altijd de volledige naam van cmdlets en parameters, tenzij u het specifiek over de alias hebt. De namen van cmdlets en para meters moeten gebruikmaken van de juiste namen van Pascal-cases.

### <a name="using-parameters-in-examples"></a>Parameters gebruiken in voorbeelden

Vermijd het gebruik van positionele parameters. Over het algemeen moet u altijd de parameter naam in een voor beeld meenemen, zelfs als de para meter positioneel is. Dit verkleint de kans op verwarring in uw voorbeelden.

## <a name="next-steps"></a>Volgende stappen

[Naslaginformatie voor cmdlets bewerken](editing-cmdlet-ref.md)

<!-- External URLs -->
[platyPS]: https://github.com/PowerShell/platyPS
[markdig]: https://github.com/lunet-io/markdig
[CommonMark]: https://spec.commonmark.org/
[atx]: https://github.github.com/gfm/#atx-headings
[pascal-case]: https://en.wikipedia.org/wiki/PascalCase
[reflow]: https://marketplace.visualstudio.com/items?itemName=marvhen.reflow-markdown
