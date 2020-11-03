---
description: Hierin worden de speciale teken reeksen beschreven die bepalen hoe Power shell de volgende tekens in de reeks interpreteert.
keywords: powershell,cmdlet
Locale: en-US
ms.date: 04/04/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_special_characters?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Special_Characters
ms.openlocfilehash: 5da2cf411519f2bd51296cd4311a607198a5ca6d
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/13/2020
ms.locfileid: "93252074"
---
# <a name="about-special-characters"></a>Speciale tekens

## <a name="short-description"></a>Korte beschrijving

Hierin worden de speciale teken reeksen beschreven die bepalen hoe Power shell de volgende tekens in de reeks interpreteert.

## <a name="long-description"></a>Lange beschrijving

Power shell ondersteunt een set speciale teken reeksen die worden gebruikt om tekens weer te geven die geen deel uitmaken van de standaard tekenset. De reeksen worden meestal _escape-reeksen_ genoemd.

Escape reeksen beginnen met het apostroffen-teken, ook wel het accent grave (ASCII 96), en zijn hoofdletter gevoelig. Het apostroffen-teken kan ook worden aangeduid als het _escape-teken_.

Escape-reeksen worden alleen geïnterpreteerd als ze zijn opgenomen in teken reeksen met dubbele aanhalings tekens ( `"` ).

Power shell herkent deze escape reeksen:

|  Reeks   |       Beschrijving       |
| ----------- | ----------------------- |
| `` `0 ``    | Null                    |
| `` `a ``    | Waarschuwing                   |
| `` `b ``    | Backspace               |
| `` `e ``    | Escape                  |
| `` `f ``    | Formulier feed               |
| `` `n ``    | Nieuwe regel                |
| `` `r ``    | Regel terugloop         |
| `` `t ``    | Tabblad horizon taal          |
| `` `u{x} `` | Unicode-escape reeks |
| `` `v ``    | Verticaal tabblad            |

Power Shell heeft ook een speciaal token om te markeren waar u wilt parseren om te stoppen. Alle tekens die deze token volgen, worden gebruikt als letterlijke waarden die niet worden geïnterpreteerd.

Speciaal parserings token:

| Reeks |            Beschrijving             |
| -------- | ---------------------------------- |
| `--%`    | Stoppen met het parseren van alles dat volgt |

## <a name="null-0"></a>Null (' 0)

Het null- `` `0 `` teken () wordt weer gegeven als een lege ruimte in Power shell-uitvoer.
Met deze functie kunt u Power shell gebruiken om tekst bestanden te lezen en verwerken die null-tekens gebruiken, zoals teken reeks beëindiging of Indica tors voor het beëindigen van een record. Het speciale teken voor een null-waarde is niet gelijk aan de `$null` variabele, die een **Null** -waarden opslaat.

## <a name="alert-a"></a>Waarschuwing (' a ')

Met het teken alert ( `` `a `` ) wordt een piep Toon signaal verzonden naar de spreker van de computer.
U kunt dit teken gebruiken om een gebruiker te waarschuwen over een bedreigende actie. In het volgende voor beeld worden twee piep signalen verzonden naar de spreker van de lokale computer.

```powershell
for ($i = 0; $i -le 1; $i++){"`a"}
```

## <a name="backspace-b"></a>Backspace (' b ')

Het Backspace `` `b `` teken () verplaatst de cursor één teken naar achter, maar verwijdert geen tekens.

In het voor beeld wordt de **back-up** van Word geschreven en vervolgens de cursor twee keer verplaatst.
Op de nieuwe positie schrijft vervolgens een spatie, gevolgd door het woord **uit**.

```powershell
"backup`b`b out"
```

```Output
back out
```

## <a name="escape-e"></a>Escape (' e)

Het escape- `` `e `` teken () wordt meestal gebruikt voor het opgeven van een virtuele terminal reeks (ANSI Escape Sequence) waarmee de kleur van tekst en andere tekst kenmerken, zoals vet en onderstrepen, worden gewijzigd. Deze reeksen kunnen ook worden gebruikt voor het positioneren en schuiven van de cursor. De Power shell-host moet virtuele terminal reeksen ondersteunen. U kunt de Booleaanse waarde van controleren `$Host.UI.SupportsVirtualTerminal` om te bepalen of deze ANSI-reeksen worden ondersteund.

Zie [ANSI_escape_code](https://en.wikipedia.org/wiki/ANSI_escape_code)voor meer informatie over ANSI escape-reeksen.

In het volgende voor beeld wordt tekst met een groene voorgrond kleur uitgevoerd.

```powershell
$fgColor = 32 # green
"`e[${fgColor}mGreen text`e[0m"
```

```Output
Green text
```

## <a name="form-feed-f"></a>Formulier feed (f)

Het teken voor formulier invoer ( `` `f `` ) is een afdruk instructie waarmee de huidige pagina wordt uitgeworpen en wordt verder afgedrukt op de volgende pagina. Het teken voor de formulier invoer is alleen van invloed op afgedrukte documenten. Dit heeft geen invloed op de scherm uitvoer.

## <a name="new-line-n"></a>Nieuwe regel (' n ')

Met het nieuwe regel `` `n `` teken () wordt direct na het teken een regel afbreek punt ingevoegd.

In dit voor beeld ziet u hoe u het nieuwe regel teken kunt gebruiken om regel einden in een opdracht te maken `Write-Host` .

```powershell
"There are two line breaks to create a blank line`n`nbetween the words."
```

```Output
There are two line breaks to create a blank line

between the words.
```

## <a name="carriage-return-r"></a>Regel terugloop (r)

Met het teken Enter Return ( `` `r `` ) verplaatst u de uitvoer cursor naar het begin van de huidige regel en gaat u verder met schrijven. Alle tekens op de huidige regel worden overschreven.

In dit voor beeld wordt de tekst vóór de regel terugloop overschreven.

```powershell
Write-Host "These characters are overwritten.`rI want this text instead "
```

U ziet dat de tekst voordat het `` `r `` teken wordt verwijderd, wordt overschreven.

```Output
I want this text instead written.
```

## <a name="horizontal-tab-t"></a>Horizon taal tabblad (niet)

Het horizontale tabblad ( `` `t `` ) teken gaat naar de volgende tabpositie en blijft op dat punt schrijven. De Power shell-console heeft standaard een tabpositie op elke achtste spatie.

In dit voor beeld worden twee tabbladen tussen elke kolom ingevoegd.

```powershell
"Column1`t`tColumn2`t`tColumn3"
```

```Output
Column1         Column2         Column3
```

## <a name="unicode-character-ux"></a>Unicode-teken (' u {x})

Met de Unicode-escape reeks ( `` `u{x} `` ) kunt u een Unicode-teken opgeven door de hexadecimale weer gave van het code punt. Dit geldt ook voor Unicode-tekens boven het basis vlak (meertalig) (> `0xFFFF` ), dat Emoji-tekens bevat, zoals het teken **duim omhoog** ( `` `u{1F44D} `` ). De Unicode-escape reeks vereist ten minste één hexadecimaal cijfer en ondersteunt Maxi maal zes hexadecimale cijfers. De maximale hexadecimale waarde voor de reeks is `10FFFF` .

In dit voor beeld wordt het symbool **pijl-omhoog** (&#x2195;) uitgevoerd.

```powershell
"`u{2195}"
```

## <a name="vertical-tab-v"></a>Verticaal tabblad (' v)

Het horizontale tabblad ( `` `v `` ) teken gaat naar het volgende verticale tabblad en schrijft de resterende uitvoer op dat punt. Dit heeft geen invloed op de standaard Windows-console.

```powershell
Write-Host "There is a vertical tab`vbetween the words."
```

In het volgende voor beeld ziet u de uitvoer die u op een printer of op een andere console host zou krijgen.

```Output
There is a vertical tab
                       between the words.
```

## <a name="stop-parsing-token---"></a>Token voor stoppen en parseren (--%)

Het token voor het stoppen van parseren ( `--%` ) voor komt dat Power shell teken reeksen interpreteert als Power shell-opdrachten en-expressies. Hierdoor kunnen die teken reeksen worden door gegeven aan andere Program ma's voor interpretatie.

Plaats het token voor het stoppen van het parseren na de programma naam en vóór programma argumenten die fouten kunnen veroorzaken.

In dit voor beeld `Icacls` maakt de opdracht gebruik van het token voor stoppen-parseren.

```powershell
icacls X:\VMS --% /grant Dom\HVAdmin:(CI)(OI)F
```

Power shell verzendt de volgende teken reeks naar `Icacls` .

```
X:\VMS /grant Dom\HVAdmin:(CI)(OI)F
```

Hier volgt nog een voorbeeld. De functie **showArgs** voert de waarden uit die zijn door gegeven. In dit voor beeld geven we de variabele `$HOME` met de naam naar de functie twee keer door.

```powershell
function showArgs {
  "`$args = " + ($args -join '|')
}

showArgs $HOME --% $HOME
```

U kunt in de uitvoer zien dat de variabele voor de eerste para meter `$HOME` wordt geïnterpreteerd door Power shell, zodat de waarde van de variabele wordt door gegeven aan de functie. Het tweede gebruik van `$HOME` is na het token voor het stoppen van parseren, zodat de teken reeks "$Home" wordt door gegeven aan de functie zonder interpretatie.

```Output
$args = C:\Users\username|--%|$HOME
```

Zie [about_Parsing](about_Parsing.md)voor meer informatie over het stop-parseren token.

## <a name="see-also"></a>Zie ook

[about_Quoting_Rules](about_Quoting_Rules.md)
