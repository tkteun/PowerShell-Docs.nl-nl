---
ms.date: 09/06/2019
keywords: Power shell, cmdlet
title: Wat is er nieuw in de Power shell 5,0 ISE
ms.openlocfilehash: 8f15e99c5a6ae33aeae9bd33eb0cf58fb27e3b90
ms.sourcegitcommit: d43f66071f1f33b350d34fa1f46f3a35910c5d24
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 11/23/2019
ms.locfileid: "74416645"
---
# <a name="whats-new-in-the-windows-powershell-50-ise"></a>Wat is er nieuw in de Windows Power shell 5,0 ISE

In dit onderwerp worden de nieuwe en bijgewerkte functies beschreven die zijn geïntroduceerd in versie 5,0 van de Windows Power shell Integrated Scripting Environment (ISE).

> [!NOTE]
> De Power shell-ISE is niet langer beschikbaar voor het ontwikkelen van actieve functies. Als onderdeel van Windows-verzen ding wordt het officieel ondersteund voor beveiligings updates en onderhoud met hoge prioriteit.
> Er zijn momenteel geen abonnementen om de ISE van Windows te verwijderen.
>
> Er is geen ondersteuning voor de ISE in Power shell V6 en verder. Gebruikers die op zoek zijn naar vervanging voor ISE, moeten [Visual Studio code](https://code.visualstudio.com/) gebruiken met de [Power shell-extensie](https://marketplace.visualstudio.com/items?itemName=ms-vscode.PowerShell).

## <a name="feature-description"></a>Functiebeschrijving

De Windows PowerShell ISE is een hosttoepassing waarmee u scripts en modules in een grafische en intuïtieve omgeving kunt schrijven, uitvoeren en testen. Belang rijke functies zoals syntaxis kleuren, tabblad aanvulling, visuele fout opsporing, Unicode-compatibiliteit en context gevoelige Help bieden een rijke script ervaring.

Zie [Inleiding tot de Windows PowerShell ISE](../components/ise/Introducing-the-Windows-PowerShell-ISE.md)voor meer informatie.

De volgende tabel bevat de nieuwe en gewijzigde functies voor deze versie van Windows PowerShell ISE in Windows Power shell.

## <a name="intellisense"></a>IntelliSense

> Toegevoegd in ISE 3,0

IntelliSense is een functie voor het automatisch volt ooien van hulp die deel uitmaakt van Windows PowerShell ISE.
IntelliSense bevat een klikable menu met mogelijk overeenkomende cmdlets, para meters, parameter waarden, bestanden of mappen die u typt.

**Welke waarde voegt deze wijziging toe?**

Met het toevoegen van IntelliSense, is het eenvoudiger om cmdlets en syntaxis te ontdekken wanneer u Windows PowerShell ISE gebruikt om scripts te maken. U kunt ook Windows PowerShell ISE gebruiken om Windows Power shell te leren wanneer u nieuwe scripts maakt.

**Wat werkt er anders?**

Wanneer u cmdlets in de Windows PowerShell ISE typt, wordt een schuif bare menu venster weer gegeven, zodat u de juiste opdrachten kunt door bladeren en selecteren.

## <a name="snippets"></a>fragmenten

> Toegevoegd in ISE 3,0

*Fragmenten* zijn korte secties van Windows Power shell-code die u kunt invoegen in de scripts die u maakt in Windows PowerShell ISE. Windows PowerShell ISE wordt geleverd met een standaardset fragmenten. U kunt fragmenten toevoegen met behulp van de cmdlet `New-Snippet` terwijl u aan het werk bent in Windows PowerShell ISE.

**Welke waarde voegt deze wijziging toe?**

U kunt met behulp van fragmenten snel scripts verzamelen en maken om uw omgeving te automatiseren.

**Wat werkt er anders?**

Als u fragmenten wilt gebruiken in Windows Power Shell 3,0 of hoger, klikt u in het menu **bewerken** op **fragmenten starten**of drukt u op <kbd>CTRL</kbd>+<kbd>J</kbd>.

## <a name="add-on-tools"></a>Invoeg toepassingen

> Toegevoegd in Power Shell 3,0

Windows PowerShell ISE ondersteunt nu invoeg toepassingen met het object model. Deze invoeg toepassingen zijn Windows Presentation Foundation (WPF)-besturings elementen die worden weer gegeven als een verticaal of horizon taal deel venster in de-console. Meerdere invoeg toepassingen in een deel venster worden weer gegeven als besturings element met tabbladen. U kunt ook invoeg toepassingen toevoegen of verwijderen die door niet-micro soft-partijen worden geproduceerd. Zie [het doel van het Windows PowerShell ISE scripting object model](../components/ise/object-model/Purpose-of-the-Windows-PowerShell-ISE-Scripting-Object-Model.md)voor meer informatie.

**Welke waarde voegt deze wijziging toe?**

Invoeg toepassingen bieden u de mogelijkheid om Windows PowerShell ISE uit te breiden en aan te passen met hulpprogram ma's waarmee functionaliteit wordt toegevoegd en uw script ervaring wordt verbeterd.

**Wat werkt er anders?**

Windows PowerShell ISE 3,0 en hoger wordt geleverd met de invoeg toepassing- **opdrachten** . Met de invoeg toepassing **opdrachten** kunt u door cmdlets bladeren en toegang krijgen tot de cmdlets naast de **script** -en **console** venster.

Aanvullende invoeg toepassingen kunt u vinden met behulp van de opdracht **invoeg toepassing openen** in het menu **invoeg toepassingen** .

## <a name="restart-manager-and-auto-save"></a>Beheer opnieuw starten en automatisch opslaan

> Toegevoegd in Power Shell 3,0

Windows PowerShell ISE worden nu automatisch elke twee minuten uw geopende scripts opgeslagen op een andere locatie. Wanneer Windows PowerShell ISE opnieuw wordt opgestart na een onverwachte crash of opnieuw opstarten, worden scripts hersteld die in de laatste sessie zijn geopend, zelfs als de scripts niet zijn opgeslagen.

Als u het interval voor automatisch opslaan wilt wijzigen, voert u de volgende opdracht uit in het console venster: `$psise.Options.AutoSaveMinuteInterval`.

**Welke waarde voegt deze wijziging toe?**

U kunt nu binnen Windows PowerShell ISE weten dat uw geopende scripts automatisch worden opgeslagen.

**Wat werkt er anders?**

De scripts worden niet automatisch door Windows PowerShell ISE 2,0 opgeslagen.

## <a name="most-recently-used-list"></a>Meest recent gebruikte lijst

> Toegevoegd in Power Shell 3,0

Windows PowerShell ISE hebt nu een meest recent gebruikte lijst voor bestanden. Wanneer u een bestand opent in Windows PowerShell ISE, wordt het bestand toegevoegd aan de lijst met meest recent gebruikte bestanden in het menu **bestand** .

Als u het standaard aantal bestanden in de meest recent gebruikte lijst wilt wijzigen, voert u de volgende opdracht uit in het console venster: `$psise.Options.MruCount`.

**Welke waarde voegt deze wijziging toe?**

U kunt nu de meest recent gebruikte lijst gebruiken om eenvoudig toegang te krijgen tot uw veelgebruikte bestanden.

**Wat werkt er anders?**

Windows PowerShell ISE 2,0 heeft geen meest recent gebruikte lijst.

## <a name="console-pane"></a>Console venster

> Toegevoegd in Power Shell 3,0

De afzonderlijke opdracht-en uitvoer deel Vensters die beschikbaar waren in de eerste versie van Windows PowerShell ISE, zijn gecombineerd in één console venster. Het console venster is vergelijkbaar met de functie en het uiterlijk van een typische Windows Power shell-console, maar bevat de volgende verbeteringen:

- Syntaxis kleuren voor invoer tekst (niet uitvoer tekst), met inbegrip van XML-syntaxis
- IntelliSense
- Accolades vergelijken
- Fout melding
- Volledige Unicode-ondersteuning
- Context afhankelijke Help van <kbd>F1</kbd>
- <kbd>Ctrl</kbd>+<kbd>F1</kbd> context gevoelige weer gave-opdracht
- Ondersteuning voor complex schrift en van rechts naar links
- Lettertype ondersteuning
- Zoom
- Lijn-selecteren en blok keren-selectie modi
- Behoud van getypte inhoud op de opdracht regel wanneer u op de <kbd>pijl-omlaag</kbd> drukt om de geschiedenis in de-console weer te geven

**Welke waarde voegt deze wijziging toe?**

De toevoeging van deze wijzigingen in het console venster biedt een script ervaring die consistent is met de interface van de console.

**Wat werkt er anders?**

Windows PowerShell ISE 2,0 heeft afzonderlijke opdracht-en uitvoer deel Vensters.

## <a name="command-line-switches"></a>Opdracht regel opties

> Toegevoegd in Power Shell 3,0

Als u Windows PowerShell ISE start vanaf de opdracht regel (door **powershell_ise. exe**te typen), kunt u de volgende nieuwe opdracht regel opties toevoegen.

- `-NoProfile`: er wordt Windows PowerShell ISE gestart zonder dat `$profile` wordt uitgevoerd
- `-Help`: Hiermee wordt een Help-venster weer gegeven
- `-mta`: de Windows PowerShell ISE wordt gestart in de modus voor meerdere threads. De standaard bewerkings modus voor Windows PowerShell ISE is modus met één thread of `-sta`.

**Welke waarde voegt deze wijziging toe?**

Met deze opdracht regel opties kunt u de omgeving bepalen waarin de Windows PowerShell ISE wordt uitgevoerd.

**Wat werkt er anders?**

Windows PowerShell ISE 2,0 herkent deze opdracht regel opties niet.

## <a name="new-editor-features"></a>Nieuwe editor functies

> Toegevoegd in Power Shell 3,0

Andere functies voor het bewerken van Windows PowerShell ISE zijn onder andere:

- **XML-syntaxis kleuren** -Windows PowerShell ISE nu kleuren XML-syntaxis op dezelfde manier als de Windows Power shell-syntaxis.
- **Vergeleken met accolades** : Windows PowerShell ISE omvatten accolades en markeringen en kunnen op de volgende manieren worden gebruikt: (als u bijvoorbeeld de opdracht **Go to Match** of <kbd>CTRL</kbd>+<kbd>]</kbd> zoekt, wordt de accolade gesloten als u een openings accolade hebt geselecteerd).
- **Overzichts weergave** Het deel venster script ondersteunt overzichten, waarmee u gedeelten van code kunt samen vouwen of uitvouwen door te klikken op een plus teken of minteken in de linkermarge. U kunt accolades of de `#region`-en `#endregion`-Tags gebruiken om het begin of einde van een inklap bare sectie te markeren. Als u alle regio's wilt uitvouwen of samen vouwen, drukt u op <kbd>Ctrl</kbd>+<kbd>M</kbd>.
- **Slepen en neerzetten van tekst** -Windows PowerShell ISE ondersteunt nu slepen en neerzetten van tekst. U kunt elk wille keurig blok tekst selecteren en deze tekst naar een andere locatie in de editor of de-console slepen om de tekst te verplaatsen. Als u de <kbd>CTRL</kbd> -toets ingedrukt houdt terwijl u de geselecteerde tekst sleept, wordt de tekst gekopieerd naar de nieuwe locatie wanneer u de muis knop loslaat. In deze versie van Windows PowerShell ISE, wanneer u bestanden naar Windows PowerShell ISE sleept en neerzet, Windows PowerShell ISE het bestand wordt geopend.
- **Fout weer geven bij parseren** -parseren van fouten worden aangeduid met rode onderstrepingen. Wanneer u de muis aanwijzer over een aangegeven fout beweegt, wordt in de tekst van de knop Info het probleem weer gegeven dat in de code is gevonden.
- **Zoom** -het zoom percentage van de inhoud van de console kan worden ingesteld met behulp van de schuif regelaar in-en uitzoomen (in de rechter benedenhoek van Windows PowerShell ISE venster) of door de opdracht `$psise.options.Zoom` in het console venster in te voeren.
- **RTF kopiëren en plakken** kopiëren naar het klem bord in Windows PowerShell ISE behoudt het letter type, de grootte en de kleur gegevens van de oorspronkelijke selectie.
- **Selectie blok keren** : u kunt een blok tekst selecteren door de <kbd>Alt</kbd> -toets ingedrukt te houden terwijl u tekst in het Script venster met de muis selecteert, of door op <kbd>Alt</kbd>+<kbd>SHIFT</kbd>+<kbd>pijl</kbd>te drukken.

**Welke waarde voegt deze wijziging toe?**

De aanvullende bewerkings functies bieden een consistente en krachtige bewerkings omgeving.

**Wat werkt er anders?**

Deze bewerkings uitbreidingen zijn niet aanwezig in Windows PowerShell ISE 2,0.

## <a name="new-help-viewer-window"></a>Nieuw Help viewer-venster

> Toegevoegd in Power Shell 3,0

Als u op <kbd>F1</kbd> drukt wanneer uw cursor zich in een cmdlet bevindt of als u een deel van een cmdlet hebt gemarkeerd, opent de nieuwe Help-viewer context gevoelige Help-informatie over de gemarkeerde cmdlet. Als u de Help van Windows Power **Shell wilt weer** geven, typt u `operators` in het console venster en drukt u vervolgens op <kbd>F1</kbd>.

Voordat u deze functie gebruikt, downloadt u de meest recente versie van de Help-onderwerpen voor Windows Power shell op de website van micro soft. De eenvoudigste methode voor het downloaden van de Help-onderwerpen is het uitvoeren van de `Update-Help`-cmdlet in het console venster wanneer u Windows PowerShell ISE als beheerder uitvoert.

U kunt wijzigen waar de <kbd>F1</kbd> -toets naar Help zoekt. In het menu **extra**/**Opties** , op het tabblad **algemene instellingen** onder **andere instellingen**, kunt u het selectie vakje **lokale Help-inhoud gebruiken in plaats van online inhoud**in-of uitschakelen. Als u dit selectie vakje inschakelt, zoekt de client naar de Help van de cmdlet in de gedownloade Help die in de map modules is gevonden. Als het selectie vakje is uitgeschakeld, zoekt de client online naar Help.

**Welke waarde voegt deze wijziging toe?**

Context gevoelige Help zonder uw huidige cmdlet of script te verlaten biedt een geïntegreerde leer ervaring.

**Wat werkt er anders?**

Als u op <kbd>F1</kbd> drukt in vorige versies van Windows PowerShell ISE hebt u het Help-bestand op de lokale computer geopend. In Windows PowerShell ISE 3,0 en hoger wordt een venster geopend met de Help voor de cmdlet die kan worden doorzocht en geconfigureerd. Deze Help-ervaring is nieuw voor Windows PowerShell ISE 3,0 en de bijwerk bare Help is nieuw voor Windows Power Shell 3,0.

## <a name="show-command-cmdlet"></a>Show-opdracht-cmdlet

> Toegevoegd in Power Shell 3,0

Met de cmdlet `Show-Command` kunt u een cmdlet of functie samen stellen of uitvoeren door een grafisch formulier in te vullen. Met het formulier kunnen gebruikers werken met Windows Power shell in een grafische omgeving.
met `Show-Command` kunt u ook geavanceerde scripters een snelle, op Windows Power shell gebaseerde gebruikers interface maken.

**Welke waarde voegt deze wijziging toe?**

Met behulp van `Show-Command` in uw Windows Power shell-scripts kunt u uw gebruikers voorzien van de grafische omgeving waarmee ze bekend zijn. `Show-Command` kan de inleidende gebruikers ook helpen bij het leren van Windows Power shell.

**Wat werkt er anders?**

`Show-Command` is nieuw Windows PowerShell ISE 3,0.

## <a name="see-also"></a>Zie ook

Zie [de Windows Power shell Integrated Scripting Environment verkennen](../components/ise/exploring-the-windows-powershell-ise.md)voor meer informatie over het gebruik van Windows PowerShell ISE.
