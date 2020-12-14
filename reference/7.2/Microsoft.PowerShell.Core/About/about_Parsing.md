---
description: Hierin wordt beschreven hoe Power shell opdrachten parseert.
Locale: en-US
ms.date: 09/14/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_parsing?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Parsing
ms.openlocfilehash: a5ce30b2ad9aff7dd8b54e7a62937013a61cd278
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 11/17/2020
ms.locfileid: "94706228"
---
# <a name="about-parsing"></a>Over het parseren

## <a name="short-description"></a>KORTE BESCHRIJVING
Hierin wordt beschreven hoe Power shell opdrachten parseert.

## <a name="long-description"></a>LANGE BESCHRIJVING

Wanneer u een opdracht bij de opdracht prompt invoert, wordt de opdracht tekst door Power shell in een reeks segmenten met de naam _tokens_ genoemd en wordt vervolgens bepaald hoe elk token moet worden geïnterpreteerd.

Als u bijvoorbeeld het volgende typt:

```powershell
Write-Host book
```

Power shell verbreekt de opdracht in twee tokens `Write-Host` en `book` interpreteert elk token onafhankelijk van een van de twee primaire parserings modi: expressie modus en argument modus.

> [!NOTE]
> Tijdens het parseren van de opdracht invoer in Power shell wordt geprobeerd de opdracht namen om te zetten in cmdlets of native uitvoer bare bestanden. Als een opdracht naam niet exact overeenkomt, voegt Power shell `Get-` toe aan de opdracht als een standaard term. Power shell wordt bijvoorbeeld geparseerd `Process` als `Get-Process` . Het wordt niet aanbevolen om deze functie te gebruiken om de volgende redenen:
>
> - Het is inefficiënt. Dit leidt ertoe dat Power shell meerdere keren zoekt.
> - Externe Program ma's met dezelfde naam worden eerst opgelost, dus u kunt de beoogde cmdlet niet uitvoeren.
> - `Get-Help` en `Get-Command` herkennen niet-korte namen van woorden.

### <a name="expression-mode"></a>Expressie modus

De expressie modus is bedoeld voor het combi neren van expressies, die vereist zijn voor het bewerken van waarden in een script taal. Expressies zijn representaties van waarden in de Power shell-syntaxis en kunnen eenvoudig of samengesteld zijn, bijvoorbeeld:

Letterlijke expressies zijn directe representaties van hun waarden: 

```powershell
'hello', 32
```

Variabelen expressies bevatten de waarde van de variabele waarnaar wordt verwezen: 

```powershell
$x, $script:path
```
Opera tors combi neren andere expressies voor evaluatie: 

```powershell
- 12, -not $Quiet, 3 + 7, $input.Length -gt 1
```

- _Letterlijke teken reeks_ moet tussen aanhalings tekens staan.
- _Getallen_ worden beschouwd als numerieke waarden in plaats van als een reeks tekens (tenzij escaped).
- _Opera tors_, waaronder unaire Opera tors als `-` en `-not` binaire Opera tors zoals en `+` `-gt` , worden geïnterpreteerd als Opera tors en voeren hun respectieve bewerkingen uit op hun argumenten (operands).
- _Kenmerk-en conversie-expressies_ worden geparseerd als expressies en toegepast op onderliggende expressies, bijvoorbeeld `[int] '7'` .
- _Verwijzingen naar variabelen_ worden geëvalueerd op hun waarden, maar _splatting_ (d.w.z. het plakken van vooraf gevulde parameter sets) is verboden en veroorzaakt een parserfout.
- Alle andere worden behandeld als een opdracht die moet worden aangeroepen.

### <a name="argument-mode"></a>Argument modus

Bij het parseren van Power shell lijkt het om invoer te interpreteren als een expressie. Maar wanneer een opdracht aanroep wordt aangetroffen, wordt het parseren voortgezet in de argument modus.

De argument modus is ontworpen voor het parseren van argumenten en para meters voor opdrachten in een shell-omgeving. Alle invoer wordt beschouwd als een uitbreid bare teken reeks, tenzij deze gebruikmaakt van een van de volgende syntaxis:

- Dollar teken ( `$` ) begint een verwijzing naar een variabele (alleen als deze wordt gevolgd door een geldige variabelenaam, anders wordt de waarde geïnterpreteerd als onderdeel van de uitbreid bare teken reeks).
- Aanhalings tekens ( `'` en `"` ) begin teken reeks waarden
- Tussen haakjes ( `(` en `)` ) worden nieuwe expressies afgebakend.
- De operator voor subexpressie ( `$(` ... `)` ) afbakent Inge sloten expressies.
- Accolades ( `{` en `}` ) afbakenen nieuwe script blokken.
- Bij het eerste at `@` -teken () begint de syntaxis van de expressie, zoals splatting ( `@args` ), arrays ( `@(1,2,3)` ) en Hash Tables ( `@{a=1;b=2}` ).
- Komma's ( `,` ) introduceren lijsten die worden door gegeven als matrices, behalve wanneer de opdracht die moet worden aangeroepen, een systeem eigen toepassing is, in dat geval worden ze geïnterpreteerd als onderdeel van de uitbreid bare teken reeks. Initiële, opeenvolgende of afsluitende komma's worden niet ondersteund.

<!--
01234567890123456789012345678901234567890123456789012345678901234567890123456789
-->
Waarden van Inge sloten expressies worden geconverteerd naar teken reeksen.

De volgende tabel bevat een aantal voor beelden van waarden die worden verwerkt in de expressie modus en de argument modus en de evaluatie van die waarden. We gaan ervan uit dat de waarde van de variabele `a` is `4` .

|       Voorbeeld        |    Modus    |      Resultaat       |
| -------------------- | ---------- | ----------------- |
| `2`                  | Expression | 2 (geheel getal)       |
| `` `2``              | Expression | "2" (opdracht)     |
| `echo 2`             | Expression | 2 (geheel getal)       |
| `2+2`                | Expression | 4 (geheel getal)       |
| `echo 2+2`           | Argument   | "2 + 2" (teken reeks)    |
| `echo(2+2)`          | Expression | 4 (geheel getal)       |
| `$a`                 | Expression | 4 (geheel getal)       |
| `echo $a`            | Expression | 4 (geheel getal)       |
| `$a+2`               | Expression | 6 (geheel getal)       |
| `echo $a+2`          | Argument   | 4 + 2 (teken reeks)      |
| `$-`                 | Argument   | "$-" (opdracht)    |
| `echo $-`            | Argument   | "$-" (teken reeks)     |
| `a$a`                | Expression | "a $ a" (opdracht)   |
| `echo a$a`           | Argument   | "A4" (teken reeks)     |
| `a'$a'`              | Expression | "a $ a" (opdracht)   |
| `echo a'$a'`         | Argument   | "a $ a" (teken reeks)    |
| `a"$a"`              | Expression | "a $ a" (opdracht)   |
| `echo a"$a"`         | Argument   | "A4" (teken reeks)     |
| `a$(2)`              | Expression | "a $ (2)" (opdracht) |
| `echo a$(2)`         | Argument   | "a2" (teken reeks)     |

Elk token kan worden geïnterpreteerd als een soort object type, zoals Boole of teken reeks. Power shell probeert het object type te bepalen op basis van de expressie.
Het object type is afhankelijk van het type para meter dat een opdracht verwacht en of Power shell weet hoe het argument moet worden geconverteerd naar het juiste type. In de volgende tabel ziet u een aantal voor beelden van de typen die zijn toegewezen aan waarden die door de expressies worden geretourneerd.

|       Voorbeeld          |    Modus    |     Resultaat      |
| ---------------------- | ---------- | --------------- |
| `Write-Output !1`      | Argument voor    | "! 1" (teken reeks)   |
| `Write-Output (!1)`    | expression | False (Boole-waarde) |
| `Write-Output (2)`     | expression | 2 (geheel getal)     |
| `Set-Variable AB A,B`  | Argument voor    | ' A ', ' B ' (matrix) |
| `CMD /CECHO A,B`       | Argument voor    | A, B (teken reeks)  |
| `CMD /CECHO $AB`       | expression | ' A ', ' B ' (matrix) |
| `CMD /CECHO :$AB`      | Argument voor    | ': A B ' (teken reeks) |

Het symbool voor het stoppen van parseren ( `--%` ), geïntroduceerd in Power shell 3,0, stuurt Power shell uit om te voor komen dat invoer als Power shell-opdrachten of-expressies wordt geïnterpreteerd.

Wanneer u een uitvoerbaar programma aanroept in Power shell, plaatst u het symbool voor het stoppen van parseren voor de programma argumenten. Deze techniek is veel eenvoudiger dan het gebruik van escape tekens om te voor komen dat er geen misinterpretatie is.

Wanneer er een symbool voor het stoppen van het parseren wordt aangetroffen, behandelt Power shell de resterende tekens in de regel als een letterlijke waarde. De enige interpretatie die wordt uitgevoerd, is het vervangen van waarden voor omgevings variabelen die gebruikmaken van de standaard Windows-notatie, zoals `%USERPROFILE%` .

Het stop-parserings symbool is alleen geldig tot de volgende nieuwe regel of een volgend pijp lijn teken. U kunt geen voortzettings teken ( `` ` `` ) gebruiken om het effect ervan uit te breiden of een opdracht scheidings teken ( `;` ) te gebruiken om het effect te beëindigen.

Met de volgende opdracht wordt bijvoorbeeld het programma **icacls** aangeroepen.

```powershell
icacls X:\VMS /grant Dom\HVAdmin:(CI)(OI)F
```

Als u deze opdracht wilt uitvoeren in Power Shell 2,0, moet u escape tekens gebruiken om te voor komen dat Power shell de haakjes interpreteert.

```powershell
icacls X:\VMS /grant Dom\HVAdmin:`(CI`)`(OI`)F
```

Vanaf Power Shell 3,0 kunt u het symbool voor stoppen en parseren gebruiken.

```powershell
icacls X:\VMS --% /grant Dom\HVAdmin:(CI)(OI)F
```

Power shell verzendt de volgende opdracht reeks naar het **icacls** -programma:

`X:\VMS /grant Dom\HVAdmin:(CI)(OI)F`

> [!NOTE]
> Het symbool voor stoppen-parseren is alleen bedoeld voor gebruik op Windows-platforms.

## <a name="see-also"></a>ZIE OOK

[about_Command_Syntax](about_Command_Syntax.md)
