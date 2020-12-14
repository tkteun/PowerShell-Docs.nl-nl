---
description: PSReadLine biedt een verbeterde opdracht regel bewerkings ervaring in de Power shell-console.
keywords: powershell
Locale: en-US
ms.date: 11/16/2020
online version: https://docs.microsoft.com/powershell/module/psreadline/about/about_psreadline?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Over PSReadLine
ms.openlocfilehash: 6d52bb04118914a9ccca5d3442a9d1915c1c2818
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 11/17/2020
ms.locfileid: "94692272"
---
# <a name="psreadline"></a>PSReadLine

## <a name="about_psreadline"></a>about_PSReadLine

## <a name="short-description"></a>Korte beschrijving

PSReadLine biedt een verbeterde opdracht regel bewerkings ervaring in de Power shell-console.

## <a name="long-description"></a>Lange beschrijving

PSReadLine 2,1 biedt een krachtige opdracht regel voor het bewerken van de Power shell-console. De oplossing biedt het volgende:

- Syntaxis kleur van de opdracht regel
- Een visuele indicatie van syntaxis fouten
- Een betere ervaring met meerdere regels (zowel bewerkingen als geschiedenis)
- Aanpas bare sleutel bindingen
- Cmd-en emacs-modi
- Veel configuratie opties
- Bash-stijl voltooiing (optioneel in CMD-modus, standaard in Emacs-modus)
- Emacs Yank/Kill-ring
- "Woord" verplaatsing en afsluiten op basis van Power shell-tokens
- Voorspellende IntelliSense

PSReadLine vereist Power Shell 3,0, of nieuwer, en de console-host. Het werkt niet in Power shell ISE. Het werkt in de console van Visual Studio code.

PSReadLine 2.1.0 wordt geleverd met Power shell 7,1 en wordt ondersteund in alle ondersteunde versies van Power shell. Het is beschikbaar om te installeren via de PowerShell Gallery.
Voer de volgende opdracht uit om PSReadLine 2.1.0 in een ondersteunde versie van Power shell te installeren.

```powershell
Install-Module -Name PSReadLine -RequiredVersion 2.1.0
```

> [!NOTE]
> Vanaf Power shell 7,0 wordt het automatisch laden van PSReadLine in Windows overs Laan als er een scherm lezer wordt gedetecteerd. Op dit moment werkt PSReadLine niet goed met scherm lezers. De standaard weergave en opmaak van Power shell 7,0 in Windows werkt op de juiste manier. U kunt de module hand matig laden, indien nodig.

## <a name="predictive-intellisense"></a>Voorspellende IntelliSense

Voorspellende IntelliSense is een aanvulling op het concept van tabblad voltooiing waarmee de gebruiker wordt geholpen bij het volt ooien van opdrachten. Hiermee kunnen gebruikers volledige opdrachten detecteren, bewerken en uitvoeren op basis van overeenkomende voor spellingen van de geschiedenis van de gebruiker en aanvullende toepassingsspecifieke invoeg toepassingen.

### <a name="enable-predictive-intellisense"></a>Voorspellende IntelliSense inschakelen

Voorspellende IntelliSense is standaard uitgeschakeld. Als u voor spellingen wilt inschakelen, voert u gewoon de volgende opdracht uit:

```powershell
Set-PSReadLineOption -PredictionSource History
```

De para meter **PredictionSource** kan ook invoeg toepassingen accepteren voor specifieke en aangepaste vereisten voor het domein.

Als u voorspellende IntelliSense wilt uitschakelen, voert u de volgende handelingen uit:

```powershell
Set-PSReadLineOption -PredictionSource None
```

De volgende functies zijn beschikbaar in de klasse **[micro soft. Power shell. PSConsoleReadLine]**.

## <a name="basic-editing-functions"></a>Basis bewerkings functies

### <a name="abort"></a>Afbreken

De huidige actie afbreken, bijvoorbeeld een incrementele geschiedenis zoekopdracht.

- Emacs: `<Ctrl+g>`

### <a name="acceptandgetnext"></a>AcceptAndGetNext

Poging tot het uitvoeren van de huidige invoer. Als deze kan worden uitgevoerd (zoals AcceptLine), kunt u het volgende item uit de geschiedenis intrekken de volgende keer dat ReadLine wordt aangeroepen.

- Emacs: `<Ctrl+o>`

### <a name="acceptline"></a>AcceptLine

Poging tot het uitvoeren van de huidige invoer. Als de huidige invoer onvolledig is (bijvoorbeeld omdat er een ontbrekend haakje sluiten, een accolade of een aanhalings teken ontbreekt), wordt de voortzettings prompt op de volgende regel weer gegeven en PSReadLine wacht op sleutels om de huidige invoer te bewerken.

- Cmd `<Enter>`
- Emacs: `<Enter>`
- VI Invoeg modus: `<Enter>`

### <a name="addline"></a>AddLine

De vervolg prompt wordt weer gegeven op de volgende regel en PSReadLine wacht op sleutels om de huidige invoer te bewerken. Dit is handig om invoer in meerdere regels als één opdracht in te voeren, zelfs wanneer één regel volledig wordt ingevoerd.

- Cmd `<Shift+Enter>`
- Emacs: `<Shift+Enter>`
- VI Invoeg modus: `<Shift+Enter>`
- VI-opdracht modus: `<Shift+Enter>`

### <a name="backwarddeletechar"></a>BackwardDeleteChar

Verwijder het teken voor de cursor.

- Cmd: `<Backspace>` , `<Ctrl+h>`
- Emacs: `<Backspace>` , `<Ctrl+Backspace>` , `<Ctrl+h>`
- VI Invoeg modus: `<Backspace>`
- VI-opdracht modus: `<X>` , `<d,h>`

### <a name="backwarddeleteline"></a>BackwardDeleteLine

Net als BackwardKillLine: verwijdert tekst van het punt naar het begin van de regel, maar plaatst de verwijderde tekst niet in de Kill-ring.

- Cmd `<Ctrl+Home>`
- VI Invoeg modus: `<Ctrl+u>` , `<Ctrl+Home>`
- VI-opdracht modus: `<Ctrl+u>` , `<Ctrl+Home>` , `<d,0>`

### <a name="backwarddeleteword"></a>BackwardDeleteWord

Hiermee verwijdert u het vorige woord.

- VI-opdracht modus: `<Ctrl+w>` , `<d,b>`

### <a name="backwardkillline"></a>BackwardKillLine

De invoer van het begin van de invoer wissen tot de cursor. De gewiste tekst wordt in de Kill-ring geplaatst.

- Emacs: `<Ctrl+u>` , `<Ctrl+x,Backspace>`

### <a name="backwardkillword"></a>BackwardKillWord

De invoer van het begin van het huidige woord wissen tot de cursor. Als de cursor zich tussen woorden bevindt, wordt de invoer uit het begin van het vorige woord naar de cursor gewist. De gewiste tekst wordt in de Kill-ring geplaatst.

- Cmd: `<Ctrl+Backspace>` , `<Ctrl+w>`
- Emacs: `<Alt+Backspace>` , `<Escape,Backspace>`
- VI Invoeg modus: `<Ctrl+Backspace>`
- VI-opdracht modus: `<Ctrl+Backspace>`

### <a name="cancelline"></a>CancelLine

De huidige invoer annuleren, waardoor de invoer op het scherm wordt weer gegeven, maar terugkeert naar de host, zodat de prompt opnieuw wordt geëvalueerd.

- VI Invoeg modus: `<Ctrl+c>`
- VI-opdracht modus: `<Ctrl+c>`

### <a name="copy"></a>Kopiëren

Kopieer de geselecteerde regio naar het klem bord van het systeem. Als er geen regio is geselecteerd, kopieert u de hele regel.

- Cmd `<Ctrl+C>`

### <a name="copyorcancelline"></a>CopyOrCancelLine

Als tekst is geselecteerd, kopieert u deze naar het klem bord. anders annuleert u de regel.

- Cmd `<Ctrl+c>`
- Emacs: `<Ctrl+c>`

### <a name="cut"></a>Knippen

Geselecteerde regio verwijderen Verwijderde tekst in het systeem Klembord plaatsen.

- Cmd `<Ctrl+x>`

### <a name="deletechar"></a>DeleteChar

Verwijder het teken onder de cursor.

- Cmd `<Delete>`
- Emacs: `<Delete>`
- VI Invoeg modus: `<Delete>`
- VI-opdracht modus: `<Delete>` , `<x>` , `<d,l>` , `<d,Spacebar>`

### <a name="deletecharorexit"></a>DeleteCharOrExit

Verwijder het teken onder de cursor of als de regel leeg is, sluit u het proces.

- Emacs: `<Ctrl+d>`

### <a name="deleteendofbuffer"></a>DeleteEndOfBuffer

Hiermee verwijdert u aan het einde van de buffer voor meerdere regels.

- VI-opdracht modus: `<d,G>`

### <a name="deleteendofword"></a>DeleteEndOfWord

Verwijder aan het einde van het woord.

- VI-opdracht modus: `<d,e>`

### <a name="deleteline"></a>DeleteLine

Hiermee verwijdert u de huidige logische lijn van een buffer voor meerdere regels, waarbij u ongedaan maken inschakelt.

- VI-opdracht modus: `<d,d>` , `<d,_>`

### <a name="deletepreviouslines"></a>DeletePreviousLines

Hiermee verwijdert u de vorige aangevraagde logische regels en de huidige logische lijn in een buffer voor meerdere regels.

- VI-opdracht modus: `<d,k>`

### <a name="deleterelativelines"></a>DeleteRelativeLines

Verwijdert uit het begin van de buffer naar de huidige logische lijn in een buffer voor meerdere regels.

De meeste MS-DOS-opdrachten `<d,g,g>` kunnen worden voorafgegaan door een numeriek argument waarmee een absoluut regel nummer wordt opgegeven, samen met het huidige regel nummer, een bereik aan regels maken dat moet worden verwijderd.
Als u niets opgeeft, wordt het numerieke argument standaard ingesteld op 1, dat verwijst naar de eerste logische lijn in een buffer met meerdere regels.

Het werkelijke aantal regels dat uit de meerregelige moet worden verwijderd, wordt berekend als het verschil tussen het huidige logische regel nummer en het opgegeven numerieke argument. Dit kan dus negatief zijn. Daarom is het _relatieve_ deel van de methode naam.

- VI-opdracht modus: `<d,g,g>`

### <a name="deletenextlines"></a>DeleteNextLines

Hiermee verwijdert u de huidige logische lijn en de volgende aangevraagde logische regels in een buffer voor meerdere regels.

- VI-opdracht modus: `<d,j>`

### <a name="deletelinetofirstchar"></a>DeleteLineToFirstChar

Hiermee wordt tekst van de cursor verwijderd naar het eerste niet-lege teken van de regel.

- VI-opdracht modus: `<d,^>`

### <a name="deletetoend"></a>DeleteToEnd

Verwijderen tot aan het einde van de regel.

- VI-opdracht modus: `<D>` , `<d,$>`

### <a name="deleteword"></a>DeleteWord

Verwijder het volgende woord.

- VI-opdracht modus: `<d,w>`

### <a name="forwarddeleteline"></a>ForwardDeleteLine

Net als ForwardKillLine: verwijdert tekst van het punt naar het einde van de regel, maar plaatst de verwijderde tekst niet in de Kill-ring.

- Cmd `<Ctrl+End>`
- VI Invoeg modus: `<Ctrl+End>`
- VI-opdracht modus: `<Ctrl+End>`

### <a name="insertlineabove"></a>InsertLineAbove

Er wordt een nieuwe lege regel gemaakt op de huidige regel, ongeacht waar de cursor zich op de huidige regel bevindt. De cursor wordt verplaatst naar het begin van de nieuwe regel.

- Cmd `<Ctrl+Enter>`

### <a name="insertlinebelow"></a>InsertLineBelow

Er wordt een nieuwe lege regel gemaakt onder de huidige regel, ongeacht waar de cursor zich op de huidige regel bevindt. De cursor wordt verplaatst naar het begin van de nieuwe regel.

- Cmd `<Shift+Ctrl+Enter>`

### <a name="invertcase"></a>InvertCase

Het hoofdletter gebruik van het huidige teken omkeren en verplaatsen naar het volgende.

- VI-opdracht modus: `<~>`

### <a name="killline"></a>KillLine

De invoer wissen van de cursor tot het einde van de invoer. De gewiste tekst wordt in de Kill-ring geplaatst.

- Emacs: `<Ctrl+k>`

### <a name="killregion"></a>KillRegion

Beëindig de tekst tussen de cursor en de markering.

- De functie is niet-afhankelijk.

### <a name="killword"></a>KillWord

De invoer wissen van de cursor tot het einde van het huidige woord. Als de cursor zich tussen woorden bevindt, wordt de invoer uit de cursor verwijderd naar het einde van het volgende woord. De gewiste tekst wordt in de Kill-ring geplaatst.

- Cmd: `<Alt+d>` , `<Ctrl+Delete>`
- Emacs: `<Alt+d>` , `<Escape,d>`
- VI Invoeg modus: `<Ctrl+Delete>`
- VI-opdracht modus: `<Ctrl+Delete>`

### <a name="paste"></a>Plakken

Tekst van het klem bord van het systeem plakken.

- Cmd: `<Ctrl+v>` , `<Shift+Insert>`
- VI Invoeg modus: `<Ctrl+v>`
- VI-opdracht modus: `<Ctrl+v>`

> [!IMPORTANT]
> Wanneer u de functie **Paste** gebruikt, wordt de volledige inhoud van de Klembord buffer geplakt in de invoer buffer van PSReadLine. De invoer buffer wordt vervolgens door gegeven aan de Power shell-parser. Invoer die met de **rechter muisknop op** de plak methode van de console toepassing wordt geplakt, wordt met één teken per keer naar de invoer buffer gekopieerd. De invoer buffer wordt door gegeven aan de parser wanneer een teken voor een nieuwe regel wordt gekopieerd. Daarom wordt de invoer één regel tegelijk geparseerd. Het verschil tussen plak methoden resulteert in een ander uitvoerings gedrag.

### <a name="pasteafter"></a>PasteAfter

Plak het klem bord na de cursor door de cursor naar het einde van de geplakte tekst te verplaatsen.

- VI-opdracht modus: `<p>`

### <a name="pastebefore"></a>PasteBefore

Plak het klem bord vóór de cursor door de cursor naar het einde van de geplakte tekst te verplaatsen.

- VI-opdracht modus: `<P>`

### <a name="prependandaccept"></a>PrependAndAccept

Laten voorafgaan door een ' # ' en accepteer de regel.

- VI-opdracht modus: `<#>`

### <a name="redo"></a>Opnieuw uitvoeren

Undo ongedaan maken.

- Cmd `<Ctrl+y>`
- VI Invoeg modus: `<Ctrl+y>`
- VI-opdracht modus: `<Ctrl+y>`

### <a name="repeatlastcommand"></a>RepeatLastCommand

Herhaal de laatste tekst wijziging.

- VI-opdracht modus: `<.>`

### <a name="revertline"></a>RevertLine

Hiermee wordt alle invoer teruggezet naar de huidige invoer.

- Cmd `<Escape>`
- Emacs: `<Alt+r>` , `<Escape,r>`

### <a name="shellbackwardkillword"></a>ShellBackwardKillWord

De invoer van het begin van het huidige woord wissen tot de cursor. Als de cursor zich tussen woorden bevindt, wordt de invoer uit het begin van het vorige woord naar de cursor gewist. De gewiste tekst wordt in de Kill-ring geplaatst.

De functie is niet-afhankelijk.

### <a name="shellkillword"></a>ShellKillWord

De invoer wissen van de cursor tot het einde van het huidige woord. Als de cursor zich tussen woorden bevindt, wordt de invoer uit de cursor verwijderd naar het einde van het volgende woord. De gewiste tekst wordt in de Kill-ring geplaatst.

De functie is niet-afhankelijk.

### <a name="swapcharacters"></a>SwapCharacters

Het huidige teken en de eerste vervangen door wisselen.

- Emacs: `<Ctrl+t>`
- VI Invoeg modus: `<Ctrl+t>`
- VI-opdracht modus: `<Ctrl+t>`

### <a name="undo"></a>Ongedaan maken

Een vorige bewerking ongedaan maken.

- Cmd `<Ctrl+z>`
- Emacs: `<Ctrl+_>` , `<Ctrl+x,Ctrl+u>`
- VI Invoeg modus: `<Ctrl+z>`
- VI-opdracht modus: `<Ctrl+z>` , `<u>`

### <a name="undoall"></a>UndoAll

Alle vorige bewerkingen voor de regel ongedaan maken.

- VI-opdracht modus: `<U>`

### <a name="unixwordrubout"></a>UnixWordRubout

De invoer van het begin van het huidige woord wissen tot de cursor. Als de cursor zich tussen woorden bevindt, wordt de invoer uit het begin van het vorige woord naar de cursor gewist. De gewiste tekst wordt in de Kill-ring geplaatst.

- Emacs: `<Ctrl+w>`

### <a name="validateandacceptline"></a>ValidateAndAcceptLine

Poging tot het uitvoeren van de huidige invoer. Als de huidige invoer onvolledig is (bijvoorbeeld omdat er een ontbrekend haakje sluiten, een accolade of een aanhalings teken ontbreekt), wordt de voortzettings prompt op de volgende regel weer gegeven en PSReadLine wacht op sleutels om de huidige invoer te bewerken.

- Emacs: `<Ctrl+m>`

### <a name="viacceptline"></a>ViAcceptLine

Accepteer de regel en schakel over naar de modus invoegen.

- VI-opdracht modus: `<Enter>`

### <a name="viacceptlineorexit"></a>ViAcceptLineOrExit

Als DeleteCharOrExit in de Emacs-modus, maar wel in plaats van een teken te verwijderen, accepteert u de regel.

- VI Invoeg modus: `<Ctrl+d>`
- VI-opdracht modus: `<Ctrl+d>`

### <a name="viappendline"></a>ViAppendLine

Er wordt een nieuwe regel ingevoegd onder de huidige regel.

- VI-opdracht modus: `<o>`

### <a name="vibackwarddeleteglob"></a>ViBackwardDeleteGlob

Hiermee verwijdert u het vorige woord, waarbij alleen witruimte wordt gebruikt als woord scheidings teken.

- VI-opdracht modus: `<d,B>`

### <a name="vibackwardglob"></a>ViBackwardGlob

Verplaatst de cursor terug naar het begin van het vorige woord, waarbij alleen spaties als scheidings teken worden gebruikt.

- VI-opdracht modus: `<B>`

### <a name="videletebrace"></a>ViDeleteBrace

Zoek de accolade, het haakje sluiten of de vier Kante haken en verwijder alle inhoud binnen, inclusief de accolade.

- VI-opdracht modus: `<d,%>`

### <a name="videleteendofglob"></a>ViDeleteEndOfGlob

Verwijder aan het einde van het woord.

- VI-opdracht modus: `<d,E>`

### <a name="videleteglob"></a>ViDeleteGlob

De volgende Globs verwijderen (door witruimte gescheiden woord).

- VI-opdracht modus: `<d,W>`

### <a name="videletetobeforechar"></a>ViDeleteToBeforeChar

Hiermee verwijdert u tot het opgegeven teken.

- VI-opdracht modus: `<d,t>`

### <a name="videletetobeforecharbackward"></a>ViDeleteToBeforeCharBackward

Hiermee verwijdert u tot het opgegeven teken.

- VI-opdracht modus: `<d,T>`

### <a name="videletetochar"></a>ViDeleteToChar

Hiermee verwijdert u tot het opgegeven teken.

- VI-opdracht modus: `<d,f>`

### <a name="videletetocharbackward"></a>ViDeleteToCharBackward

Hiermee verwijdert u achterwaartse tekens tot aan het opgegeven teken.

- VI-opdracht modus: `<d,F>`

### <a name="viinsertatbegining"></a>ViInsertAtBegining

Schakel over naar de Invoeg modus en plaats de cursor aan het begin van de regel.

- VI-opdracht modus: `<I>`

### <a name="viinsertatend"></a>ViInsertAtEnd

Schakel over naar de Invoeg modus en plaats de cursor aan het einde van de regel.

- VI-opdracht modus: `<A>`

### <a name="viinsertline"></a>ViInsertLine

Boven de huidige regel wordt een nieuwe regel ingevoegd.

- VI-opdracht modus: `<O>`

### <a name="viinsertwithappend"></a>ViInsertWithAppend

Toevoegen vanaf de huidige regel positie.

- VI-opdracht modus: `<a>`

### <a name="viinsertwithdelete"></a>ViInsertWithDelete

Verwijder het huidige teken en schakel over naar de modus invoegen.

- VI-opdracht modus: `<s>`

### <a name="vijoinlines"></a>ViJoinLines

De huidige regel en de volgende regel worden samengevoegd.

- VI-opdracht modus: `<J>`

### <a name="vireplaceline"></a>ViReplaceLine

De volledige opdracht regel wissen.

- VI-opdracht modus: `<S>` , `<c,c>`

### <a name="vireplacetobeforechar"></a>ViReplaceToBeforeChar

Vervangt tot het opgegeven teken.

- VI-opdracht modus: `<c,t>`

### <a name="vireplacetobeforecharbackward"></a>ViReplaceToBeforeCharBackward

Vervangt tot het opgegeven teken.

- VI-opdracht modus: `<c,T>`

### <a name="vireplacetochar"></a>ViReplaceToChar

Hiermee verwijdert u tot het opgegeven teken.

- VI-opdracht modus: `<c,f>`

### <a name="vireplacetocharbackward"></a>ViReplaceToCharBackward

Vervangt tot het opgegeven teken.

- VI-opdracht modus: `<c,F>`

### <a name="viyankbeginningofline"></a>ViYankBeginningOfLine

Yank vanaf het begin van de buffer naar de cursor.

- VI-opdracht modus: `<y,0>`

### <a name="viyankendofglob"></a>ViYankEndOfGlob

Yank van de cursor tot het einde van het (de) woord (en).

- VI-opdracht modus: `<y,E>`

### <a name="viyankendofword"></a>ViYankEndOfWord

Yank van de cursor tot het einde van het (de) woord (en).

- VI-opdracht modus: `<y,e>`

### <a name="viyankleft"></a>ViYankLeft

Yank teken (s) links van de cursor.

- VI-opdracht modus: `<y,h>`

### <a name="viyankline"></a>ViYankLine

Yank de volledige buffer.

- VI-opdracht modus: `<y,y>`

### <a name="viyanknextglob"></a>ViYankNextGlob

Yank van de cursor naar het begin van de volgende woord (en).

- VI-opdracht modus: `<y,W>`

### <a name="viyanknextword"></a>ViYankNextWord

Yank het woord (en) na de cursor.

- VI-opdracht modus: `<y,w>`

### <a name="viyankpercent"></a>ViYankPercent

Yank naar/van overeenkomende accolade.

- VI-opdracht modus: `<y,%>`

### <a name="viyankpreviousglob"></a>ViYankPreviousGlob

Yank vanaf het begin van het (de) woord (en) tot de cursor.

- VI-opdracht modus: `<y,B>`

### <a name="viyankpreviousword"></a>ViYankPreviousWord

Yank de woorden vóór de cursor.

- VI-opdracht modus: `<y,b>`

### <a name="viyankright"></a>ViYankRight

Yank teken (s) onder en rechts van de cursor.

- VI-opdracht modus: `<y,l>` , `<y,Spacebar>`

### <a name="viyanktoendofline"></a>ViYankToEndOfLine

Yank van de cursor tot het einde van de buffer.

- VI-opdracht modus: `<y,$>`

### <a name="viyanktofirstchar"></a>ViYankToFirstChar

Yank van het eerste niet-spatie teken tot de cursor.

- VI-opdracht modus: `<y,^>`

### <a name="yank"></a>Yank

Voeg de meest recent afgebroken tekst toe aan de invoer.

- Emacs: `<Ctrl+y>`

### <a name="yanklastarg"></a>YankLastArg

Yank het laatste argument van de vorige geschiedenis regel. Met een argument, de eerste keer dat deze wordt aangeroepen, gedraagt zich op dezelfde manier als YankNthArg. Als meerdere keren worden aangeroepen, wordt door de geschiedenis en ARG de richting ingesteld (negatief de richting omkeren.)

- Cmd `<Alt+.>`
- Emacs: `<Alt+.>` , `<Alt+_>` , `<Escape,.>` , `<Escape,_>`

### <a name="yankntharg"></a>YankNthArg

Yank het eerste argument (na de opdracht) van de vorige geschiedenis regel.
Met een argument, Yank het ne argument (vanaf 0), als het argument negatief is, begint vanaf het laatste argument.

- Emacs: `<Ctrl+Alt+y>` , `<Escape,Ctrl+y>`

### <a name="yankpop"></a>YankPop

Als de vorige bewerking Yank of YankPop is, vervangt u de eerder yanked tekst door de volgende afgebroken tekst van de Kill-ring.

- Emacs: `<Alt+y>` , `<Escape,y>`

## <a name="cursor-movement-functions"></a>Functies voor cursor verplaatsing

### <a name="backwardchar"></a>BackwardChar

De cursor één teken naar links verplaatsen. Hierdoor kan de cursor worden verplaatst naar de vorige regel van de invoer op meerdere regels.

- Cmd `<LeftArrow>`
- Emacs: `<LeftArrow>` , `<Ctrl+b>`

### <a name="backwardword"></a>BackwardWord

De cursor weer naar het begin van het huidige woord verplaatsen of tussen woorden, het begin van het vorige woord. Grenzen van woorden worden gedefinieerd door een Configureer bare set tekens.

- Cmd `<Ctrl+LeftArrow>`
- Emacs: `<Alt+b>` , `<Escape,b>`
- VI Invoeg modus: `<Ctrl+LeftArrow>`
- VI-opdracht modus: `<Ctrl+LeftArrow>`

### <a name="beginningofline"></a>BeginningOfLine

Als de invoer meerdere regels heeft, gaat u naar het begin van de huidige regel of gaat u naar het begin van de invoer als deze al aan het begin van de regel staat. Als de invoer één regel heeft, gaat u naar het begin van de invoer.

- Cmd `<Home>`
- Emacs: `<Home>` , `<Ctrl+a>`
- VI Invoeg modus: `<Home>`
- VI-opdracht modus: `<Home>`

### <a name="endofline"></a>EndOfLine

Als de invoer meerdere regels heeft, gaat u naar het einde van de huidige regel of gaat u naar het einde van de invoer als u aan het einde van de regel bent. Als de invoer één regel heeft, gaat u naar het einde van de invoer.

- Cmd `<End>`
- Emacs: `<End>` , `<Ctrl+e>`
- VI Invoeg modus: `<End>`

### <a name="forwardchar"></a>ForwardChar

De cursor één teken naar rechts verplaatsen. Hierdoor kan de cursor worden verplaatst naar de volgende regel van de invoer op meerdere regels.

- Cmd `<RightArrow>`
- Emacs: `<RightArrow>` , `<Ctrl+f>`

### <a name="forwardword"></a>ForwardWord

De cursor naar het einde van het huidige woord verplaatsen, of tussen woorden, naar het einde van het volgende woord. Grenzen van woorden worden gedefinieerd door een Configureer bare set tekens.

- Emacs: `<Alt+f>` , `<Escape,f>`

### <a name="gotobrace"></a>GotoBrace

Ga naar de accolade, haakjes of vier Kante haakjes.

- Cmd `<Ctrl+]>`
- VI Invoeg modus: `<Ctrl+]>`
- VI-opdracht modus: `<Ctrl+]>`

### <a name="gotocolumn"></a>GotoColumn

Ga naar de kolom die wordt aangegeven door arg.

- VI-opdracht modus: `<|>`

### <a name="gotofirstnonblankofline"></a>GotoFirstNonBlankOfLine

De cursor verplaatsen naar het eerste niet-lege teken in de regel.

- VI-opdracht modus: `<^>` , `<_>`

### <a name="movetoendofline"></a>MoveToEndOfLine

De cursor verplaatsen naar het einde van de invoer.

- VI-opdracht modus: `<End>` , `<$>`

### <a name="nextline"></a>NextLine

De cursor verplaatsen naar de volgende regel.

- De functie is niet-afhankelijk.

### <a name="nextword"></a>NextWord

De cursor voorwaarts verplaatsen naar het begin van het volgende woord. Grenzen van woorden worden gedefinieerd door een Configureer bare set tekens.

- Cmd `<Ctrl+RightArrow>`
- VI Invoeg modus: `<Ctrl+RightArrow>`
- VI-opdracht modus: `<Ctrl+RightArrow>`

### <a name="nextwordend"></a>NextWordEnd

De cursor naar het einde van het huidige woord verplaatsen, of tussen woorden, naar het einde van het volgende woord. Grenzen van woorden worden gedefinieerd door een Configureer bare set tekens.

- VI-opdracht modus: `<e>`

### <a name="previousline"></a>PreviousLine

Verplaats de cursor naar de vorige regel.

- De functie is niet-afhankelijk.

### <a name="shellbackwardword"></a>ShellBackwardWord

De cursor weer naar het begin van het huidige woord verplaatsen of tussen woorden, het begin van het vorige woord. Grenzen van woorden worden gedefinieerd door Power shell-tokens.

- De functie is niet-afhankelijk.

### <a name="shellforwardword"></a>ShellForwardWord

De cursor voorwaarts verplaatsen naar het begin van het volgende woord. Grenzen van woorden worden gedefinieerd door Power shell-tokens.

- De functie is niet-afhankelijk.

### <a name="shellnextword"></a>ShellNextWord

De cursor naar het einde van het huidige woord verplaatsen, of tussen woorden, naar het einde van het volgende woord. Grenzen van woorden worden gedefinieerd door Power shell-tokens.

- De functie is niet-afhankelijk.

### <a name="vibackwardchar"></a>ViBackwardChar

De cursor één teken naar links verplaatsen in de bewerkings modus VI. Hierdoor kan de cursor worden verplaatst naar de vorige regel van de invoer op meerdere regels.

- VI Invoeg modus: `<LeftArrow>`
- VI-opdracht modus: `<LeftArrow>` , `<Backspace>` , `<h>`

### <a name="vibackwardword"></a>ViBackwardWord

De cursor weer naar het begin van het huidige woord verplaatsen of tussen woorden, het begin van het vorige woord. Grenzen van woorden worden gedefinieerd door een Configureer bare set tekens.

- VI-opdracht modus: `<b>`

### <a name="viforwardchar"></a>ViForwardChar

De cursor één teken naar rechts verplaatsen in de bewerkings modus VI. Hierdoor kan de cursor worden verplaatst naar de volgende regel van de invoer op meerdere regels.

- VI Invoeg modus: `<RightArrow>`
- VI-opdracht modus: `<RightArrow>` , `<Spacebar>` , `<l>`

### <a name="viendofglob"></a>ViEndOfGlob

Verplaatst de cursor naar het einde van het woord, waarbij alleen spaties als scheidings teken worden gebruikt.

- VI-opdracht modus: `<E>`

### <a name="viendofpreviousglob"></a>ViEndOfPreviousGlob

Wordt verplaatst naar het einde van het vorige woord, waarbij alleen witruimte wordt gebruikt als woord als scheidings teken.

- De functie is niet-afhankelijk.

### <a name="vigotobrace"></a>ViGotoBrace

Vergelijkbaar met GotoBrace, maar is in plaats van op tokens gebaseerd.

- VI-opdracht modus: `<%>`

### <a name="vinextglob"></a>ViNextGlob

Verplaatst naar het volgende woord, waarbij alleen witruimte wordt gebruikt als woord scheidings teken.

- VI-opdracht modus: `<W>`

### <a name="vinextword"></a>ViNextWord

De cursor voorwaarts verplaatsen naar het begin van het volgende woord. Grenzen van woorden worden gedefinieerd door een Configureer bare set tekens.

- VI-opdracht modus: `<w>`

## <a name="history-functions"></a>Geschiedenis functies

### <a name="beginningofhistory"></a>BeginningOfHistory

Hiermee gaat u naar het eerste item in de geschiedenis.

- Emacs: `<Alt+<>`

### <a name="clearhistory"></a>ClearHistory

Hiermee wist u de geschiedenis in PSReadLine. Dit heeft geen invloed op de Power shell-geschiedenis.

- Cmd `<Alt+F7>`

### <a name="endofhistory"></a>EndOfHistory

Hiermee gaat u naar het laatste item (de huidige invoer) in de geschiedenis.

- Emacs: `<Alt+>>`

### <a name="forwardsearchhistory"></a>ForwardSearchHistory

Voer een incrementele zoek opdracht uit met de geschiedenis.

- Cmd `<Ctrl+s>`
- Emacs: `<Ctrl+s>`

### <a name="historysearchbackward"></a>HistorySearchBackward

Vervang de huidige invoer door het item ' Previous ' uit de PSReadLine-geschiedenis dat overeenkomt met de tekens tussen de start en de invoer en de cursor.

- Cmd `<F8>`

### <a name="historysearchforward"></a>HistorySearchForward

Vervang de huidige invoer door het ' volgende ' item uit de PSReadLine-geschiedenis dat overeenkomt met de tekens tussen de start en de invoer en de cursor.

- Cmd `<Shift+F8>`

### <a name="nexthistory"></a>NextHistory

Vervang de huidige invoer door het ' volgende ' item uit de PSReadLine-geschiedenis.

- Cmd `<DownArrow>`
- Emacs: `<DownArrow>` , `<Ctrl+n>`
- VI Invoeg modus: `<DownArrow>`
- VI-opdracht modus: `<DownArrow>` , `<j>` , `<+>`

### <a name="previoushistory"></a>PreviousHistory

Vervang de huidige invoer door het item ' Previous ' uit de PSReadLine-geschiedenis.

- Cmd `<UpArrow>`
- Emacs: `<UpArrow>` , `<Ctrl+p>`
- VI Invoeg modus: `<UpArrow>`
- VI-opdracht modus: `<UpArrow>` , `<k>` , `<->`

### <a name="reversesearchhistory"></a>ReverseSearchHistory

Voer een incrementele zoek opdracht uit met de geschiedenis.

- Cmd `<Ctrl+r>`
- Emacs: `<Ctrl+r>`

### <a name="visearchhistorybackward"></a>ViSearchHistoryBackward

Vraagt om een zoek reeks en start de zoek opdracht op AcceptLine.

- VI Invoeg modus: `<Ctrl+r>`
- VI-opdracht modus: `</>` , `<Ctrl+r>`

## <a name="completion-functions"></a>Voltooiings functies

### <a name="complete"></a>Voltooid

Poging tot het volt ooien van de tekst rondom de cursor. Als er meerdere mogelijke afrondingen zijn, wordt het langste ondubbelzinnige voor voegsel gebruikt voor het volt ooien. Als u probeert de langste ondubbelzinnige voltooiing te volt ooien, wordt een lijst met mogelijke voltooiingen weer gegeven.

- Emacs: `<Tab>`

### <a name="menucomplete"></a>MenuComplete

Poging tot het volt ooien van de tekst rondom de cursor. Als er meerdere mogelijke afrondingen zijn, wordt het langste ondubbelzinnige voor voegsel gebruikt voor het volt ooien. Als u probeert de langste ondubbelzinnige voltooiing te volt ooien, wordt een lijst met mogelijke voltooiingen weer gegeven.

- Cmd: `<Ctrl+@>` , `<Ctrl+Spacebar>`
- Emacs: `<Ctrl+Spacebar>`

### <a name="possiblecompletions"></a>PossibleCompletions

De lijst met mogelijke aanvullingen weer geven.

- Emacs: `<Alt+=>`
- VI Invoeg modus: `<Ctrl+Spacebar>`
- VI-opdracht modus: `<Ctrl+Spacebar>`

### <a name="tabcompletenext"></a>TabCompleteNext

Poging om de tekst rond de cursor te volt ooien met de volgende beschik bare voltooiing.

- Cmd `<Tab>`
- VI-opdracht modus: `<Tab>`

### <a name="tabcompleteprevious"></a>TabCompletePrevious

Poging om de tekst rond de cursor te volt ooien met de vorige beschik bare voltooiing.

- Cmd `<Shift+Tab>`
- VI-opdracht modus: `<Shift+Tab>`

### <a name="vitabcompletenext"></a>ViTabCompleteNext

Beëindigt de huidige bewerkings groep, indien nodig, en roept TabCompleteNext aan.

- VI Invoeg modus: `<Tab>`

### <a name="vitabcompleteprevious"></a>ViTabCompletePrevious

Beëindigt de huidige bewerkings groep, indien nodig, en roept TabCompletePrevious aan.

- VI Invoeg modus: `<Shift+Tab>`

## <a name="miscellaneous-functions"></a>Diverse functies

### <a name="acceptnextsuggestionword"></a>AcceptNextSuggestionWord

Het volgende woord van de inline of geselecteerde suggestie accepteren.

- De functie is niet-afhankelijk.

### <a name="acceptsuggestion"></a>AcceptSuggestion

De huidige inline of geselecteerde suggestie accepteren.

- De functie is niet-afhankelijk.

### <a name="capturescreen"></a>CaptureScreen

Interactieve scherm opname starten-pijl-omhoog/omlaag Selecteer regels en voer de geselecteerde tekst als tekst en HTML naar het klem bord kopiëren.

- De functie is niet-afhankelijk.

### <a name="clearscreen"></a>ClearScreen

Schakel het scherm uit en teken de huidige regel boven aan het scherm.

- Cmd `<Ctrl+l>`
- Emacs: `<Ctrl+l>`
- VI Invoeg modus: `<Ctrl+l>`
- VI-opdracht modus: `<Ctrl+l>`

### <a name="digitargument"></a>DigitArgument

Start een nieuw cijfer argument om door te geven aan andere functies.

- Cmd: `<Alt+0>` , `<Alt+1>` , `<Alt+2>` , `<Alt+3>` , `<Alt+4>` , `<Alt+5>` , `<Alt+6>` , `<Alt+7>` , `<Alt+8>` , `<Alt+9>` , `<Alt+->`
- Emacs: `<Alt+0>` , `<Alt+1>` , `<Alt+2>` , `<Alt+3>` , `<Alt+4>` , `<Alt+5>` , `<Alt+6>` , `<Alt+7>` , `<Alt+8>` , `<Alt+9>` , `<Alt+->`
- VI-opdracht modus: `<0>` , `<1>` , `<2>` , `<3>` , `<4>` , `<5>` , `<6>` , `<7>` , `<8>` , `<9>`

### <a name="invokeprompt"></a>InvokePrompt

Hiermee wordt de huidige prompt gewist en wordt de functie Prompt aangeroepen om de prompt opnieuw weer te geven. Dit is handig voor aangepaste sleutel afhandelingen die de status wijzigen, bijvoorbeeld de huidige map wijzigen.

- De functie is niet-afhankelijk.

### <a name="scrolldisplaydown"></a>ScrollDisplayDown

De weer gave één scherm omlaag schuiven.

- Cmd `<PageDown>`
- Emacs: `<PageDown>`

### <a name="scrolldisplaydownline"></a>ScrollDisplayDownLine

De weer gave één regel omlaag schuiven.

- Cmd `<Ctrl+PageDown>`
- Emacs: `<Ctrl+PageDown>`

### <a name="scrolldisplaytocursor"></a>ScrollDisplayToCursor

Schuif de weer gave naar de cursor.

- Emacs: `<Ctrl+End>`

### <a name="scrolldisplaytop"></a>ScrollDisplayTop

Schuif de weer gave naar boven.

- Emacs: `<Ctrl+Home>`

### <a name="scrolldisplayup"></a>ScrollDisplayUp

Schuif de weer gave één scherm omhoog.

- Cmd `<PageUp>`
- Emacs: `<PageUp>`

### <a name="scrolldisplayupline"></a>ScrollDisplayUpLine

De weer gave één regel omhoog schuiven.

- Cmd `<Ctrl+PageUp>`
- Emacs: `<Ctrl+PageUp>`

### <a name="selfinsert"></a>SelfInsert

Voeg de sleutel in.

- De functie is niet-afhankelijk.

### <a name="showkeybindings"></a>ShowKeyBindings

Alle gebonden sleutels weer geven.

- Cmd `<Ctrl+Alt+?>`
- Emacs: `<Ctrl+Alt+?>`
- VI Invoeg modus: `<Ctrl+Alt+?>`

### <a name="vicommandmode"></a>ViCommandMode

Schakel de huidige bedrijfs modus uit van Vi-Insert naar de VI-opdracht.

- VI Invoeg modus: `<Escape>`

### <a name="vidigitargumentinchord"></a>ViDigitArgumentInChord

Start een nieuw cijfer argument om door te geven aan andere functies in een van de koorden van VI.

- De functie is niet-afhankelijk.

### <a name="vieditvisually"></a>ViEditVisually

Bewerk de opdracht regel in een tekst editor die is opgegeven door $env: EDITOR of $env: VISUAL.

- Emacs: `<Ctrl+x,Ctrl+e>`
- VI-opdracht modus: `<v>`

### <a name="viexit"></a>ViExit

Hiermee wordt de shell afgesloten.

- De functie is niet-afhankelijk.

### <a name="viinsertmode"></a>ViInsertMode

Schakel over naar de modus invoegen.

- VI-opdracht modus: `<i>`

### <a name="whatiskey"></a>WhatIsKey

Lees een sleutel en vertel me wat de sleutel is gebonden.

- Cmd `<Alt+?>`
- Emacs: `<Alt+?>`

## <a name="selection-functions"></a>Selectie functies

### <a name="exchangepointandmark"></a>ExchangePointAndMark

De cursor wordt op de locatie van het merk geplaatst en het vinkje wordt verplaatst naar de locatie van de cursor.

- Emacs: `<Ctrl+x,Ctrl+x>`

### <a name="selectall"></a>SelectAll aanroepen

Selecteer de volledige regel.

- Cmd `<Ctrl+a>`

### <a name="selectbackwardchar"></a>SelectBackwardChar

Pas de huidige selectie aan om het vorige teken op te laten staan.

- Cmd `<Shift+LeftArrow>`
- Emacs: `<Shift+LeftArrow>`

### <a name="selectbackwardsline"></a>SelectBackwardsLine

Pas de huidige selectie aan de cursor toe aan het begin van de regel.

- Cmd `<Shift+Home>`
- Emacs: `<Shift+Home>`

### <a name="selectbackwardword"></a>SelectBackwardWord

Pas de huidige selectie aan om het vorige woord op te laten staan.

- Cmd `<Shift+Ctrl+LeftArrow>`
- Emacs: `<Alt+B>`

### <a name="selectforwardchar"></a>SelectForwardChar

Pas de huidige selectie aan om het volgende teken op te laten staan.

- Cmd `<Shift+RightArrow>`
- Emacs: `<Shift+RightArrow>`

### <a name="selectforwardword"></a>SelectForwardWord

Pas de huidige selectie aan om het volgende woord in te voegen met behulp van ForwardWord.

- Emacs: `<Alt+F>`

### <a name="selectline"></a>SelectLine

Pas de huidige selectie aan de cursor toe aan het einde van de regel.

- Cmd `<Shift+End>`
- Emacs: `<Shift+End>`

### <a name="selectnextword"></a>SelectNextWord

Pas de huidige selectie aan om het volgende woord op te laten staan.

- Cmd `<Shift+Ctrl+RightArrow>`

### <a name="selectshellbackwardword"></a>SelectShellBackwardWord

Pas de huidige selectie aan om het vorige woord op te maken met behulp van ShellBackwardWord.

- De functie is niet-afhankelijk.

### <a name="selectshellforwardword"></a>SelectShellForwardWord

Pas de huidige selectie aan om het volgende woord in te voegen met behulp van ShellForwardWord.

- De functie is niet-afhankelijk.

### <a name="selectshellnextword"></a>SelectShellNextWord

Pas de huidige selectie aan om het volgende woord in te voegen met behulp van ShellNextWord.

- De functie is niet-afhankelijk.

### <a name="setmark"></a>SetMark

De huidige locatie van de cursor markeren voor gebruik in een volgende bewerkings opdracht.

- Emacs: `<Ctrl+@>`

## <a name="predictive-intellisense-functions"></a>Voorspellende IntelliSense-functies

> [!NOTE]
> Voorspellende IntelliSense moet zijn ingeschakeld om deze functies te kunnen gebruiken.

### <a name="acceptnextwordsuggestion"></a>AcceptNextWordSuggestion

Hiermee wordt het volgende woord van de inline suggestie geaccepteerd van voorspellende IntelliSense.
Deze functie kan worden gebonden met <kbd>CTRL</kbd> + <kbd>F</kbd> door de volgende opdracht uit te voeren.

```powershell
Set-PSReadLineKeyHandler -Chord "Ctrl+f" -Function ForwardWord
```

### <a name="acceptsuggestion"></a>AcceptSuggestion

Hiermee wordt de huidige inline suggestie van voorspellende IntelliSense geaccepteerd door op <kbd>RightArrow</kbd> te drukken wanneer de cursor zich aan het einde van de huidige regel bevindt.

## <a name="search-functions"></a>Zoek functies

### <a name="charactersearch"></a>CharacterSearch

Lees een teken en zoek voorwaarts naar het volgende exemplaar van het teken.
Als er een argument is opgegeven, zoekt u voorwaarts (of achterwaarts als negatieve) voor het ne voorval.

- Cmd `<F3>`
- Emacs: `<Ctrl+]>`
- VI Invoeg modus: `<F3>`
- VI-opdracht modus: `<F3>`

### <a name="charactersearchbackward"></a>CharacterSearchBackward

Lees een teken en zoek terug naar het volgende exemplaar van het teken. Als er een argument is opgegeven, zoekt u terug (of als dit negatief is) voor het ne exemplaar.

- Cmd `<Shift+F3>`
- Emacs: `<Ctrl+Alt+]>`
- VI Invoeg modus: `<Shift+F3>`
- VI-opdracht modus: `<Shift+F3>`

### <a name="repeatlastcharsearch"></a>RepeatLastCharSearch

De laatst opgenomen zoek opdracht herhalen.

- VI-opdracht modus: `<;>`

### <a name="repeatlastcharsearchbackwards"></a>RepeatLastCharSearchBackwards

De laatst opgenomen zoek opdracht herhalen, maar in tegenovergestelde richting.

- VI-opdracht modus: `<,>`

### <a name="repeatsearch"></a>RepeatSearch

Herhaal de laatste zoek opdracht in dezelfde richting als voorheen.

- VI-opdracht modus: `<n>`

### <a name="repeatsearchbackward"></a>RepeatSearchBackward

Herhaal de laatste zoek opdracht in dezelfde richting als voorheen.

- VI-opdracht modus: `<N>`

### <a name="searchchar"></a>SearchChar

Lees het volgende teken, zoek het naar een later moment en maak een back-up van het teken. Dit is voor de ' on'-functionaliteit.

- VI-opdracht modus: `<f>`

### <a name="searchcharbackward"></a>SearchCharBackward

Lees het volgende teken en zoek het vervolgens naar achteren, en ga vervolgens terug naar een teken. Dit is voor de ' on'-functionaliteit.

- VI-opdracht modus: `<F>`

### <a name="searchcharbackwardwithbackoff"></a>SearchCharBackwardWithBackoff

Lees het volgende teken en zoek het vervolgens naar achteren, en ga vervolgens terug naar een teken. Dit is voor de ' on'-functionaliteit.

- VI-opdracht modus: `<T>`

### <a name="searchcharwithbackoff"></a>SearchCharWithBackoff

Lees het volgende teken, zoek het naar een later moment en maak een back-up van het teken. Dit is voor de ' on'-functionaliteit.

- VI-opdracht modus: `<t>`

### <a name="searchforward"></a>SearchForward

Vraagt om een zoek reeks en start de zoek opdracht op AcceptLine.

- VI Invoeg modus: `<Ctrl+s>`
- VI-opdracht modus: `<?>` , `<Ctrl+s>`

## <a name="custom-key-bindings"></a>Aangepaste sleutel bindingen

PSReadLine ondersteunt aangepaste sleutel bindingen met behulp van de-cmdlet `Set-PSReadLineKeyHandler` . De meeste aangepaste sleutel bindingen roepen een van de bovenstaande functies aan, bijvoorbeeld

```powershell
Set-PSReadLineKeyHandler -Key UpArrow -Function HistorySearchBackward
```

U kunt een script Block binden aan een sleutel. Het script Block kan veel wat u wilt. Enkele handige voor beelden zijn

- de opdracht regel bewerken
- een nieuw venster openen (bijvoorbeeld Help)
- mappen wijzigen zonder de opdracht regel te wijzigen

De script Block ontvangt twee argumenten:

- `$key` -Een **[ConsoleKeyInfo]** -object dat de sleutel is die de aangepaste binding heeft geactiveerd. Als u dezelfde script Block aan meerdere sleutels koppelt en verschillende acties moet uitvoeren, afhankelijk van de sleutel, kunt u $key controleren. Veel aangepaste bindingen negeren dit argument.

- `$arg` -Een wille keurig argument. Meestal is dit een geheel getal dat de gebruiker door gegeven van de sleutel bindingen DigitArgument. Als uw binding geen argumenten accepteert, is het redelijk om dit argument te negeren.

Laten we een voor beeld bekijken waarmee een opdracht regel wordt toegevoegd aan de geschiedenis zonder deze uit te voeren. Dit is handig wanneer u ervoor hebt gekozen om iets te doen, maar niet opnieuw moet invoeren van de opdracht regel die u al hebt ingevoerd.

```powershell
$parameters = @{
    Key = 'Alt+w'
    BriefDescription = 'SaveInHistory'
    LongDescription = 'Save current line in history but do not execute'
    ScriptBlock = {
      param($key, $arg)   # The arguments are ignored in this example

      # GetBufferState gives us the command line (with the cursor position)
      $line = $null
      $cursor = $null
      [Microsoft.PowerShell.PSConsoleReadLine]::GetBufferState([ref]$line,
        [ref]$cursor)

      # AddToHistory saves the line in history, but does not execute it.
      [Microsoft.PowerShell.PSConsoleReadLine]::AddToHistory($line)

      # RevertLine is like pressing Escape.
      [Microsoft.PowerShell.PSConsoleReadLine]::RevertLine()
  }
}
Set-PSReadLineKeyHandler @parameters
```

U kunt veel meer voor beelden bekijken in het bestand `SamplePSReadLineProfile.ps1` dat is geïnstalleerd in de PSReadLine-module.

De meeste sleutel bindingen gebruiken enkele hulp functies voor het bewerken van de opdracht regel.
Deze Api's worden beschreven in de volgende sectie.

## <a name="custom-key-binding-support-apis"></a>Api's voor de ondersteuning van aangepaste sleutel bindingen

De volgende functies zijn openbaar in micro soft. Power shell. PSConsoleReadLine, maar kunnen niet rechtstreeks aan een sleutel worden gebonden. De meeste zijn handig in aangepaste sleutel bindingen.

```csharp
void AddToHistory(string command)
```

Een opdracht regel toevoegen aan de geschiedenis zonder deze uit te voeren.

```csharp
void ClearKillRing()
```

Wis de Kill-ring.  Dit wordt meestal gebruikt voor het testen.

```csharp
void Delete(int start, int length)
```

Verwijder de lengte tekens uit het begin.  Met deze bewerking wordt ongedaan maken/opnieuw uitvoeren ondersteund.

```csharp
void Ding()
```

Voer de actie opname uit op basis van de voor keuren van de gebruiker.

```csharp
void GetBufferState([ref] string input, [ref] int cursor)
void GetBufferState([ref] Ast ast, [ref] Token[] tokens,
  [ref] ParseError[] parseErrors, [ref] int cursor)
```

Deze twee functies halen nuttige informatie op over de huidige status van de invoer buffer.  De eerste wordt vaak gebruikt voor eenvoudige gevallen.  De tweede wordt gebruikt als uw binding iets geavanceerder gaat met de AST.

```csharp
IEnumerable[Microsoft.PowerShell.KeyHandler]
  GetKeyHandlers(bool includeBound, bool includeUnbound)

IEnumerable[Microsoft.PowerShell.KeyHandler]
  GetKeyHandlers(string[] Chord)
```

Deze twee functies worden gebruikt door `Get-PSReadLineKeyHandler` . De eerste wordt gebruikt om alle sleutel bindingen op te halen. De tweede wordt gebruikt voor het ophalen van specifieke sleutel bindingen.

```csharp
Microsoft.PowerShell.PSConsoleReadLineOptions GetOptions()
```

Deze functie wordt gebruikt door Get-PSReadLineOption en is waarschijnlijk niet nuttig in een aangepaste sleutel binding.

```csharp
void GetSelectionState([ref] int start, [ref] int length)
```

Als er niets is geselecteerd op de opdracht regel, wordt-1 geretourneerd in zowel start als length. Als er een selectie is op de opdracht regel, worden het begin en de lengte van de selectie geretourneerd.

```csharp
void Insert(char c)
void Insert(string s)
```

Voeg een teken of teken reeks toe aan de cursor.  Met deze bewerking wordt ongedaan maken/opnieuw uitvoeren ondersteund.

```csharp
string ReadLine(runspace remoteRunspace,
  System.Management.Automation.EngineIntrinsics engineIntrinsics)
```

Dit is het belangrijkste ingangs punt voor PSReadLine. Er wordt geen recursie ondersteund, dus is niet nuttig in een aangepaste sleutel binding.

```csharp
void RemoveKeyHandler(string[] key)
```

Deze functie wordt gebruikt door Remove-PSReadLineKeyHandler en is waarschijnlijk niet nuttig in een aangepaste sleutel binding.

```csharp
void Replace(int start, int length, string replacement)
```

Vervang een deel van de invoer. Met deze bewerking wordt ongedaan maken/opnieuw uitvoeren ondersteund. U kunt het beste verwijderen gevolgd door INSERT, omdat het wordt beschouwd als één actie voor ongedaan maken.

```csharp
void SetCursorPosition(int cursor)
```

De cursor verplaatsen naar de opgegeven verschuiving. Cursor verplaatsing wordt niet bijgehouden voor ongedaan maken.

```csharp
void SetOptions(Microsoft.PowerShell.SetPSReadLineOption options)
```

Deze functie is een helper-methode die wordt gebruikt door de cmdlet Set-PSReadLineOption, maar kan handig zijn voor een aangepaste sleutel binding die tijdelijk een instelling wil wijzigen.

```csharp
bool TryGetArgAsInt(System.Object arg, [ref] int numericArg,
  int defaultNumericArg)
```

Deze Help methode wordt gebruikt voor aangepaste bindingen die voldoen aan DigitArgument. Een typische aanroep ziet eruit als

```powershell
[int]$numericArg = 0
[Microsoft.PowerShell.PSConsoleReadLine]::TryGetArgAsInt($arg,
  [ref]$numericArg, 1)
```

## <a name="note"></a>Notitie

### <a name="command-history"></a>Opdracht geschiedenis

PSReadLine onderhoudt een geschiedenis bestand met alle opdrachten en gegevens die u hebt ingevoerd op de opdracht regel. Dit kan gevoelige gegevens bevatten, inclusief wacht woorden. Als u bijvoorbeeld de cmdlet gebruikt, `ConvertTo-SecureString` wordt het wacht woord in het geschiedenis bestand vastgelegd als tekst zonder opmaak. De geschiedenis bestanden zijn een bestand met de naam `$($host.Name)_history.txt` . Op Windows-systemen wordt het geschiedenis bestand opgeslagen op `$env:APPDATA\Microsoft\Windows\PowerShell\PSReadLine` . Op niet-Windows-systemen worden de geschiedenis bestanden opgeslagen in `$env:XDG_DATA_HOME/powershell/PSReadLine` of `$env:HOME/.local/share/powershell/PSReadLine` .

### <a name="feedback--contributing-to-psreadline"></a>Feedback & bijdragen aan PSReadLine

[PSReadLine op GitHub](https://github.com/PowerShell/PSReadLine)

U kunt een pull-aanvraag verzenden of feedback verzenden op de pagina GitHub.

## <a name="see-also"></a>Zie ook

PSReadLine wordt sterk beïnvloed door de GNU [readline](https://tiswww.case.edu/php/chet/readline/rltop.html) -bibliotheek.
