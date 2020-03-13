---
title: Power shell-stijl gids voor docs
description: Dit artikel bevat de regels van de stijl voor het schrijven van Power shell-documentatie.
ms.date: 03/05/2020
ms.topic: conceptual
ms.openlocfilehash: 964536c5195c3bb8abd98b5996a96fc7b9362489
ms.sourcegitcommit: 18d832858a7b8ea094763afa753e0f48f01372e7
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 03/10/2020
ms.locfileid: "79078645"
---
# <a name="powershell-docs-style-guide"></a>Power shell-stijl gids voor docs

Dit artikel bevat richt lijnen die specifiek zijn voor de Power shell-docs-inhoud. Dit is gebaseerd op de informatie die wordt beschreven in het [overzicht](overview.md#get-started-writing-docs).

## <a name="product-terminology"></a>Product terminologie

Er zijn verschillende varianten van Power shell.
In deze tabel worden enkele van de verschillende termen gedefinieerd die worden gebruikt voor het bespreken van Power shell.

- **Power shell** : dit is de standaard instelling. We overwegen Power shell 7 en nog eens te zijn. de echte Power shell gaat verder.

- **Power shell core** -Power shell gebouwd op .net core. Het gebruik van de term **core** moet worden beperkt tot gevallen waarin het nodig is om het te onderscheiden van Windows Power shell.

- **Windows Power shell** -Power shell is gebouwd op .NET Framework. Windows Power shell wordt alleen in Windows geleverd en vereist het volledige Framework.

In het algemeen kunnen verwijzingen naar ' Windows Power shell ' in de documentatie worden gewijzigd in Power shell.
' Windows Power shell ' mag **niet** worden gewijzigd wanneer de Windows-specifieke technologie wordt besproken.

## <a name="markdown-specifics"></a>Details van prijs verlaging

Het micro soft open publishing-systeem (OPS) dat onze documentatie bouwt, maakt gebruik van [markdig][] voor het verwerken van de verkortings documenten. Markdig parseert de documenten op basis van de regels van de meest recente [CommonMark][] -specificatie.

De nieuwe CommonMark-specificatie is veel strikter dan de constructie van sommige prijs verlagings elementen. Let op de details die in dit document worden gegeven.

### <a name="blank-lines-spaces-and-tabs"></a>Lege regels, spaties en tabbladen

Verwijder dubbele lege regels. Meerdere lege regels worden weer gegeven als één lege regel in HTML, zodat er geen meerdere lege regels zijn.

Lege regels geven ook aan dat het einde van een blok in de prijs opgave wordt gesignaleerd. Er mag slechts één lege waarde zijn tussen blokken van verschillende typen (bijvoorbeeld tussen een alinea en een lijst of koptekst).

> [!NOTE]
> De afstand is significant in de prijs verlaging. Maakt altijd gebruik van spaties in plaats van harde tabbladen. Verwijder extra spaties aan het einde van regels.

### <a name="titles-and-headings"></a>Titels en koppen

Gebruik alleen [ATX-koppen][atx] (# Style, in plaats van `=`-of `-` stijl headers).

- Gebruik alleen zinnen: alleen de juiste naam woorden en de eerste letter van een titel of koptekst moeten worden gekapitaliseerd
- Er mag slechts één spatie tussen de `#` en de eerste letter van de kop staan
- Koppen moeten worden omgeven door één lege regel
- Slechts één H1 per document
- Koptekst niveaus moeten met één worden verhoogd. Geen niveaus overs Laan
- Geen vette of andere opmaak gebruiken in kopteksten

### <a name="limit-line-length-to-100-characters"></a>Regel lengte beperken tot 100 tekens

Dit geldt voor conceptuele artikelen en cmdlet-verwijzingen. About_topics is beperkt tot 80 tekens.
Als u de regel lengte beperkt, worden de Lees baarheid van Git en geschiedenis verbeterd. Het maakt het ook gemakkelijker voor andere schrijvers om bijdragen te maken.

Gebruik de [uitprijs][reflow] uitbreiding opnieuw plaatsen in Visual Studio code om alinea's eenvoudig opnieuw te plaatsen zodat deze overeenkomen met de voorgeschreven regel lengte.

### <a name="lists"></a>Lijsten

Als uw lijst meerdere zinnen of alinea's bevat, kunt u overwegen om een koptekst op subniveau te gebruiken in plaats van een lijst.

De lijst moet tussen één lege regel worden geplaatst.

#### <a name="unordered-lists"></a>Niet-geordende lijsten

Beëindig geen lijst items met een punt, tenzij deze meerdere zinnen bevatten. Gebruik het afbreek streepje (`-`) voor opsommings tekens in lijst items. Dit voor komt Verwar ring met vette of cursieve markeringen die gebruikmaken van het sterretje [`*`]. Als u een alinea of andere elementen onder een item met opsommings tekens wilt opnemen, voegt u een regel-en inspringing in met het eerste teken achter het bullet.

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

Dit is een lijst met subelementen onder een item met opsommings tekens.

- Eerste item in opsommings teken

  Zin waarin het eerste opsommings teken wordt uitgelegd.

  - Item in subopsommingsteken

    Zin waarin het subopsommingsteken wordt uitgelegd.

- Tweede item voor opsommings teken
- Derde item voor opsommings teken

#### <a name="ordered-lists"></a>Geordende lijsten

Als u een alinea of andere elementen onder een genummerd item wilt toevoegen, moet u de inspringing uitlijnen met het eerste teken na het item nummer. Alle items in een genummerde lijst moeten het getal `1.` gebruiken in plaats van elk item te verhogen. Bij het weer geven van de prijs verlaging wordt de waarde automatisch verhoogd. Dit maakt het gemakkelijker om items opnieuw in te delen en de inspringing van onderliggende inhoud te standaardiseren.

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

1. Voeg voor het eerste element één spatie toe na de 1. Lange zinnen moeten worden verpakt naar de volgende regel en moeten worden uitgelijnd met het eerste teken na de markering van de genummerde lijst.

   Als u een tweede element (zoals deze) wilt opnemen, voegt u een regel afbreek na de eerste en inspringing in. De inspringing van het tweede element moet worden uitgelijnd met het eerste teken na de markering van de genummerde lijst. Voor items met één cijfer, zoals deze, inspringen naar kolom 4. Voor items met dubbele cijfers, bijvoorbeeld item nummer 10, inspringen naar kolom 5.

1. Het volgende genummerde item wordt hier gestart.

### <a name="formatting-command-syntax-elements"></a>Opmaak van opdracht syntaxis elementen

- Gebruik altijd de volledige naam voor cmdlets en para meters. Vermijd het gebruik van aliassen tenzij u de alias expliciet demonstreert.

- In een alinea moeten tref woorden, namen van cmdlets, variabelen en bestands paden worden verpakt in apostroffen-tekens (`` ` ``). Eigenschaps-, para meter-en klassen namen moeten **vet**zijn.

  Bijvoorbeeld:

  ~~~markdown
  The following code uses `Get-ChildItem` to list the contents of `C:\Windows` and assigns
  the output to the `$files` variable.

  ```powershell
  $files = Get-ChildItem C:\Windows
  ```
  ~~~

- Wanneer u verwijst naar een para meter op naam, moet de naam **vet**zijn. Bij het illustreren van het gebruik van een para meter met het voor voegsel hyphen moet de para meter worden ingepakt in accents graves. Bijvoorbeeld:

  ```markdown
  The parameter's name is **Name**, but it is typed as `-Name` when used on the command
  line as a parameter.
  ```

- Bij het verwijzen naar externe opdrachten (exe, scripts, enzovoort) moet de naam van de opdracht vet, alle kleine letters (of een hoofd letter als aan het begin van een zin) worden weer gegeven en de juiste bestands extensie bevatten. Bijvoorbeeld:

  ```markdown
  For example, on Windows systems, you can use the `net start` and `net stop` commands
  to start and stop a service. **Sc.exe** is another service control tool for Windows.
  That name does not fit into the naming pattern for the **net.exe** service commands.
  ```

- Wanneer het voor beeld-gebruik van een externe opdracht wordt weer gegeven, moet het voor beeld worden verpakt in accents graves.
  Wanneer er een naam conflict is met een alias, moet u de bestands extensie in het opdracht voorbeeld toevoegen. Bijvoorbeeld:

  ```markdown
  To start the spooler service on a remote computer named DC01, you type `sc.exe \\DC01 start spooler`.
  ```

- Bij het schrijven van een conceptueel artikel (in plaats van referentie-inhoud) moet het eerste exemplaar van een naam van een cmdlet worden gelinkt naar de cmdlet-documentatie. Gebruik geen accents graves, vet of andere opmaak binnen de haakjes van een Hyper link.

  Bijvoorbeeld:

  ```markdown
  This [Write-Host](/powershell/module/Microsoft.PowerShell.Utility/Write-Host) cmdlet
  uses the **Object** parameter to ...
  ```

  Zie de sectie [hyper links](#hyperlinks) in dit artikel voor meer informatie.

### <a name="images"></a>Installatiekopieën

De syntaxis voor het insluiten van een afbeelding is:

```markdown
![[alt text]](<folderPath>)

Example:
![Introduction](./media/overview/Introduction.png)
```

Waarbij `alt text` een korte beschrijving van de installatie kopie is en `<folder path>` een relatief pad naar de afbeelding is. Alternatieve tekst is vereist voor scherm lezers voor visueel gehandicapten. Het is ook handig als er een site fout is waar de installatie kopie niet kan worden gerenderd.

Afbeeldingen moeten worden opgeslagen in een `media/<article-name>` map in de map waarin het artikel zich bevindt.
Afbeeldingen mogen niet tussen artikelen worden gedeeld. Maak een map die overeenkomt met de bestands naam van uw artikel in de map `media`. Kopieer de installatie kopieën voor dat artikel naar de nieuwe map. Als een installatie kopie wordt gebruikt door meerdere artikelen, moet elke map met de installatie kopie een kopie van het afbeeldings bestand bevatten. In deze praktijk wordt voor komen dat een afbeelding wordt gewijzigd in een ander artikel.

De volgende afbeeldings bestands typen worden ondersteund: `*.png`, `*.gif`, `*.jpeg`, `*.jpg`, `*.svg`

### <a name="markdown-extensions-supported-by-open-publishing"></a>Uitprijs uitbreidingen ondersteund door open Publishing

Het [Microsoft docs authoring Pack](/contribute/how-to-write-docs-auth-pack) bevat hulpprogram ma's die ondersteuning bieden voor functies die uniek zijn voor het publicatie systeem. Waarschuwingen zijn een uitstel extensie voor het maken van blok citaten die op docs.microsoft.com worden weer gegeven met kleuren en pictogrammen die de betekenis van de inhoud aangeven. De volgende waarschuwings typen worden ondersteund:

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

Deze waarschuwingen zien er als volgt uit op docs.microsoft.com:

> [!NOTE]
> De informatie die de gebruiker moet opmerken, zelfs bij het onderhouden.

> [!TIP]
> Optionele informatie voor een succes volle gebruiker.

> [!IMPORTANT]
> Essentiële informatie die nodig is voor het slagen van een gebruiker.

> [!CAUTION]
> Negatieve mogelijke gevolgen van een actie.

> [!WARNING]
> Gevaarlijke bepaalde gevolgen van een actie.

## <a name="hyperlinks"></a>Link

- Vermijd het gebruik van bare Url's. Links moeten de syntaxis van de prijs verlaging gebruiken `[friendlyname](url-or-path)`
- Bare Url's kunnen worden gebruikt wanneer dit nodig is, maar moeten worden inge sloten in accents graves. Bijvoorbeeld:

  ```markdown
  By default, if you do not specify this parameter, the DMTF standard resource URI
  `http://schemas.dmtf.org/wbem/wscim/1/cim-schema/2/` is used and the class name is appended to it.
  ```

- URL-koppelingen moeten indien mogelijk HTTPS zijn.
- Koppelingen moeten een beschrijvende naam hebben, meestal de titel van het gekoppelde onderwerp
- Voor alle items in de sectie ' Verwante koppelingen ' aan de onderkant moet een Hyper link worden weer.
- Gebruik geen accents graves, vet of andere opmaak binnen de haakjes van een Hyper link.

### <a name="linking-to-other-content"></a>Koppeling naar andere inhoud

Er zijn twee typen hyper links die worden ondersteund door het publicatie systeem: Url's en bestands koppelingen.

Een URL-koppeling kan een URL-pad zijn dat relatief is ten opzichte van de hoofdmap van docs.microsoft.com. Of een absolute URL die de syntaxis van de volledige URL bevat. (Bijvoorbeeld: `https:/github.com/MicrosoftDocs/PowerShell-Docs`)

- Gebruik URL-koppelingen wanneer u een koppeling maakt naar inhoud buiten Power shell-docs of tussen Naslag informatie over de cmdlet en conceptuele artikelen in Power shell-docs.
- De eenvoudigste manier om een relatieve koppeling te maken, is door de URL te kopiëren vanuit uw browser en vervolgens `https://docs.microsoft.com/en-us` te verwijderen van de waarde die u in de prijs van de geplakte hebt geplakt.
   - Land instellingen niet opnemen in Url's op Eigenschappen van micro soft (bijv. /en-US verwijderen uit de URL).
- Alle Url's naar externe websites moeten HTTPS gebruiken, tenzij dat niet geldig is voor de doel site.

Een koppeling naar een bestand wordt gebruikt om te koppelen van het ene referentie artikel naar het andere of van het ene conceptuele artikel naar het andere. Als u een koppeling moet maken naar een referentie artikel voor een specifieke versie van Power shell, moet u een URL-koppeling gebruiken.

- Bestands koppelingen bevatten een relatief bestandspad (bijvoorbeeld: `../folder/file.md`)
- Alle bestands paden gebruiken tekens voor voorwaartse slash (`/`)

## <a name="formatting-code-samples"></a>Code voorbeelden opmaken

Prijs verlaging ondersteunt twee verschillende code stijlen:

- Code reeksen (inline): gemarkeerd met een enkel apostroffen-teken (`` ` ``). Wordt gebruikt in een alinea in plaats van als een zelfstandig blok.
- Code blokken: een blok met meerdere regels dat is omgeven door Triple-apostroffen (`` ``` ``) teken reeksen. Code blokken kunnen ook een taal label volgen volgens het accents graves. Het taal label schakelt syntaxis markering in voor de inhoud van het code blok.

### <a name="using-code-blocks"></a>Code blokken gebruiken

Met prijs verlaging kunt u inspringen om een code blok aan te duiden, maar dit patroon kan problematisch zijn en moet worden vermeden. Alle code blokken moeten zich in een code Fence bevinden. Een code Fence is een code blok dat is omgeven door Triple-apostroffen (`` ``` ``) teken reeksen. De markeringen voor de code omheining moeten zich op hun eigen regel vóór en na het code voorbeeld bevindt. De markering aan het begin van het code blok heeft mogelijk een optioneel taal label. Het open Publishing System (OPS) van micro soft gebruikt het taal label voor de ondersteuning van de functie voor het markeren van syntaxis.

Met OPS wordt ook een **Kopieer** knop toegevoegd waarmee de inhoud van het code blok naar het klem bord wordt gekopieerd. Zo kunt u de code snel in een script plakken om het code voorbeeld te testen. Niet alle voor beelden in onze documentatie zijn echter bedoeld om te worden uitgevoerd. Sommige code blokken zijn eenvoudige illustraties van een Power shell-concept.

Er zijn twee typen code blokken die in onze documentatie worden gebruikt:

1. Voor beelden van illustreren
2. Uitvoer bare voor beelden

### <a name="syntax-code-blocks"></a>Syntaxis code blokken

In dit voor beeld ziet u alle mogelijke para meters van de cmdlet `Get-Command`.

~~~markdown
```
Get-Command [-Verb <String[]>] [-Noun <String[]>] [-Module <String[]>]
  [-FullyQualifiedModule <ModuleSpecification[]>] [-TotalCount <Int32>] [-Syntax] [-ShowCommandInfo]
  [[-ArgumentList] <Object[]>] [-All] [-ListImported] [-ParameterName <String[]>]
  [-ParameterType <PSTypeName[]>] [<CommonParameters>]
```
~~~

In dit voor beeld wordt de `for` instructie in algemene termen beschreven:

~~~markdown
```
for (<init>; <condition>; <repeat>)
{<statement list>}
```
~~~

### <a name="illustrative-examples"></a>Voor beelden van illustreren

Voor beelden van illustreren een Power shell-concept. Ze zijn niet bedoeld om te worden gekopieerd naar het klem bord voor uitvoering. Deze worden meestal gebruikt voor eenvoudige voor beelden die eenvoudig kunnen worden getypt.
Ze worden ook gebruikt voor syntaxis voorbeelden waarbij u de syntaxis van een opdracht illustreert. Het code blok bevat mogelijk voorbeeld uitvoer van de opdracht die wordt geïllustreerd.

Hier volgt een eenvoudig voor beeld van het illustreren van een Power shell-vergelijkings operator:

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

Houd er rekening mee dat in dit voor beeld de vereenvoudigde Power shell-prompt wordt weer gegeven en de resulterende uitvoer. In dit geval is de lezer niet van plan om dit voor beeld te kopiëren en uit te voeren.

### <a name="executable-examples"></a>Uitvoer bare voor beelden

Complexere voor beelden of voor beelden die bedoeld zijn om te kopiëren en uit te voeren, moeten de volgende opmaak voor blok stijl gebruiken:

~~~markdown
```powershell
<PowerShell code goes here>
```
~~~

De uitvoer die door Power shell-opdrachten wordt weer gegeven, moet worden inge sloten in een **uitvoer** code blok om te voor komen dat de syntaxis wordt gemarkeerd. Bijvoorbeeld:

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

Het code label van de **uitvoer** is geen officiële taal die wordt ondersteund door het markerings systeem van de syntaxis.
Dit label is echter nuttig omdat OPS het label "uitvoer" toevoegt aan het frame van de code op de webpagina. Het vak uitvoer code heeft geen syntaxis markering.

## <a name="coding-style-rules"></a>Coderings stijl regels

### <a name="avoid-line-continuation-in-code-samples"></a>Regel voortzetting in code voorbeelden voor komen

Vermijd het gebruik van regel voortzettings tekens (`` ` ``) in voor beelden van Power shell-code. Deze zijn moeilijk te zien en kunnen problemen veroorzaken als er extra spaties aan het einde van de regel staan.

- Gebruik Power shell splatting om de regel lengte te verminderen voor cmdlets die veel para meters hebben.
- Profiteer van de natuurlijke lijn grens mogelijkheden van Power shell, zoals na het sluis teken (`|`), accolades, haakjes en haakjes.

### <a name="avoid-using-powershell-prompts-in-examples"></a>Vermijd het gebruik van Power shell-prompts in voor beelden

Het gebruik van de prompt teken reeks wordt afgeraden en moet worden beperkt tot scenario's die bedoeld zijn om het gebruik van de opdracht regel te illustreren. Voor de meeste van deze voor beelden moet de prompt teken reeks `PS>`zijn. Deze vraag is onafhankelijk van specifieke indica toren voor het besturings systeem.

Prompts zijn vereist voor voor beelden van opdrachten voor het wijzigen van de prompt of wanneer het weer gegeven pad belang rijk is voor het scenario dat wordt geïllustreerd. In het volgende voor beeld ziet u hoe de prompt verandert wanneer u de register provider gebruikt.

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

### <a name="do-not-use-aliases-in-examples"></a>Gebruik geen aliassen in voor beelden

U moet altijd de volledige naam van alle cmdlets en para meters gebruiken, tenzij u specifiek op de alias spreekt. De namen van cmdlets en para meters moeten de juiste spelling gebruiken die in de code is gedefinieerd.

### <a name="using-parameters-in-examples"></a>Para meters in voor beelden gebruiken

Vermijd het gebruik van positionele para meters. In het algemeen moet u altijd de parameter naam in een voor beeld gebruiken, zelfs als de para meter positioneel is. Dit verkleint de kans op Verwar ring in uw voor beelden.

## <a name="next-steps"></a>Volgende stappen

[Naslag informatie voor het bewerken van cmdlets](editing-cmdlet-ref.md)

<!-- External URLs -->
[platyPS]: https://github.com/PowerShell/platyPS
[markdig]: https://github.com/lunet-io/markdig
[CommonMark]: https://spec.commonmark.org/
[atx]: https://github.github.com/gfm/#atx-headings
[pascal-case]: https://en.wikipedia.org/wiki/PascalCase
[reflow]: https://marketplace.visualstudio.com/items?itemName=marvhen.reflow-markdown
