---
description: Hierin worden reguliere expressies in Power shell beschreven.
keywords: powershell,cmdlet
Locale: en-US
ms.date: 03/10/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_regular_expressions?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Regular_Expressions
ms.openlocfilehash: fe3f668265101f8c0aa07967f235a1092d76e299
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/13/2020
ms.locfileid: "93252920"
---
# <a name="about-regular-expressions"></a>Over reguliere expressies

## <a name="short-description"></a>Korte beschrijving
Hierin worden reguliere expressies in Power shell beschreven.

## <a name="long-description"></a>Lange beschrijving

> [!NOTE]
> In dit artikel ziet u de syntaxis en methoden voor het gebruik van reguliere expressies in Power shell. niet alle syntaxis wordt besproken. Zie voor een uitgebreidere referentie de [reguliere expressie taal-Quick Reference](/dotnet/standard/base-types/regular-expression-language-quick-reference).

Een reguliere expressie is een patroon dat wordt gebruikt voor het afstemmen van tekst. Het kan bestaan uit letterlijke tekens, Opera tors en andere constructies.

In dit artikel ziet u de syntaxis van een reguliere expressie in Power shell. Power Shell heeft verschillende Opera tors en cmdlets die gebruikmaken van reguliere expressies. U vindt meer informatie over de syntaxis en het gebruik van de onderstaande koppelingen.

- [Selecteer teken reeks](xref:Microsoft.PowerShell.Utility.Select-String)
- [-overeenkomsten en vervangen Opera tors](about_Comparison_Operators.md)
- [-splitsen](about_Split.md)
- [switch-instructie met de optie-regex](about_Switch.md)

Reguliere Power shell-expressies zijn standaard niet hoofdletter gevoelig. Elke hierboven weer gegeven methode heeft een andere manier om hoofdletter gevoeligheid af te dwingen.

|       Methode       |                      Hoofdletter gevoeligheid                      |
| ------------------ | ---------------------------------------------------------- |
| `Select-String`    | `-CaseSensitive`switch gebruiken                                |
| `switch` rekeningen | Gebruik de `-casesensitive` optie                            |
| operatoren          | voor voegsel met **' c '** ( `-cmatch` , `-csplit` of `-creplace` ) |

### <a name="character-literals"></a>Letterlijke tekens

Een reguliere expressie kan een letterlijke teken of een teken reeks zijn. De expressie zorgt ervoor dat de engine overeenkomt met de tekst die precies is opgegeven.

```powershell
# This statement returns true because book contains the string "oo"
'book' -match 'oo'
```

### <a name="character-classes"></a>Teken klassen

Hoewel letterlijke tekens werken als u het exacte patroon kent, kunt u met teken klassen minder specifiek zijn.

#### <a name="character-groups"></a>Teken groepen

`[character group]` Hiermee kunt u een wille keurig aantal tekens één keer vergelijken, terwijl `[^character group]` alleen de tekens in de groep overeenkomen.

```powershell
# This expression returns true if the pattern matches big, bog, or bug.
'big' -match 'b[iou]g'
```

Als uw lijst met tekens die moeten worden vergeleken, het afbreek streepje ( `-` ) bevat, moet deze aan het begin of einde van de lijst staan om deze te onderscheiden van een teken bereik expressie.

#### <a name="character-ranges"></a>Teken reeksen

Een patroon kan ook een teken reeks zijn. De tekens kunnen alfabetisch `[A-Z]` , numeriek `[0-9]` of zelfs op ASCII gebaseerd zijn `[ -~]` (alle afdruk bare tekens).

```powershell
# This expression returns true if the pattern matches any 2 digit number.
42 -match '[0-9][0-9]'
```

#### <a name="numbers"></a>Getallen

De `\d` teken klasse komt overeen met een decimaal getal. Wordt omgekeerd, komt `\D` overeen met een niet-decimaal getal.

```powershell
# This expression returns true if it matches a server name.
# (Server-01 - Server-99).
'Server-01' -match 'Server-\d\d'
```

#### <a name="word-characters"></a>Woord tekens

De `\w` teken klasse komt overeen met een wille keurig woord `[a-zA-Z_0-9]` . Als u wilt zoeken naar een wille keurig teken dat geen woord is, gebruikt u `\W` .

```powershell
# This expression returns true.
# The pattern matches the first word character 'B'.
'Book' -match '\w'
```

#### <a name="wildcards"></a>Jokertekens

De punt ( `.` ) is een Joker teken in reguliere expressies. Dit komt overeen met een wille keurig teken behalve een nieuwe regel ( `\n` ).

```powershell
# This expression returns true.
# The pattern matches any 4 characters except the newline.
'a1\ ' -match '....'
```

#### <a name="whitespace"></a>Witruimte

Spatie komt overeen met de `\s` teken klasse. Een teken dat niet uit witruimte bestaat, wordt met behulp van gebruikt `\S` . Er kunnen ook letterlijke spatie tekens `' '` worden gebruikt.

```powershell
# This expression returns true.
# The pattern uses both methods to match the space.
' - ' -match '\s- '
```

### <a name="quantifiers"></a>Kwantiteits meters

Kwant oren bepalen hoeveel exemplaren van elk element aanwezig moeten zijn in de invoer teken reeks.

Hier volgen enkele van de Kwant oren die beschikbaar zijn in Power shell:

| Kwantiteits meter |                Beschrijving                |
| ---------- | ----------------------------------------- |
| `*`        | Nul of meer keer.                       |
| `+`        | Een of meer keren.                        |
| `?`        | Nul of één keer.                         |
| `{n,m}`    | Minstens `n` , maar niet meer dan een `m` keer. |

Het sterretje ( `*` ) komt niet overeen met het vorige element of is meer dan nul. Het resultaat is dat zelfs een invoer teken reeks zonder het element een overeenkomst zou zijn.

```powershell
# This returns true for all account name strings even if the name is absent.
'ACCOUNT NAME:    Administrator' -match 'ACCOUNT NAME:\s*\w*'
```

Het plus teken ( `+` ) komt een of meer keer overeen met het vorige element.

```powershell
# This returns true if it matches any server name.
'DC-01' -match '[A-Z]+-\d\d'
```

Het vraag teken `?` komt overeen met het vorige element nul of één keer. Net als bij een sterretje komt `*` het overeen met teken reeksen waar het element niet aanwezig is.

```powershell
# This returns true for any server name, even server names without dashes.
'SERVER01' -match '[A-Z]+-?\d\d'
```

De `{n, m}` kwantor kan verschillende manieren gebruiken om nauw keurige controle over de kwantor toe te staan. Het tweede element `m` en de komma `,` zijn optioneel.

| Kwantiteits meter |                Beschrijving                 |
| ---------- | ------------------------------------------ |
| `{n}`      | EXACT overeenkomen met het `n` aantal keren.         |
| `{n,}`     | Ten minste één `n` keer overeenkomen.        |
| `{n,m}`    | Komt overeen met `n` en `m` aantal keren. |

```powershell
# This returns true if it matches any phone number.
'111-222-3333' -match '\d{3}-\d{3}-\d{4}'
```

### <a name="anchors"></a>Ankers

Met ankers kunt u ervoor zorgen dat een overeenkomst slaagt of mislukt op basis van de overeenkomst positie binnen de invoer teken reeks.

De twee veelgebruikte ankers zijn `^` en `$` . Het caret `^` komt overeen met het begin van een teken reeks en `$` , die overeenkomt met het einde van een teken reeks. Met de ankers kunt u uw tekst op een specifieke positie afstemmen en ook ongewenste tekens verwijderen.

```powershell
# The pattern expects the string 'fish' to be the only thing on the line.
# This returns FALSE.
'fishing' -match '^fish$'
```

> [!NOTE]
> Wanneer u een regex met een `$` anker definieert, moet u de regex insluiten met enkele aanhalings tekens ( `'` ) in plaats van dubbele aanhalings tekens ( `"` ) of de expressie wordt in Power shell uitgebreid als een variabele.

Wanneer u ankers in Power shell gebruikt, moet u weten wat het verschil is tussen de opties van de **modus singleline** en de reguliere expressie van **meerdere regels** .

- **Meerdere** regels: de modus `^` voor meerdere regels en `$` het begin einde van elke regel wordt vergeleken in plaats van het begin en het einde van de invoer teken reeks.
- **Modus singleline** : de modus singleline-modus behandelt de invoer teken reeks als een **modus singleline**.
  Hiermee wordt het `.` teken afgedwongen dat overeenkomt met elk teken (inclusief nieuwe regels), in plaats van elk teken te vergelijken met de nieuwe regel `\n` .

Voor meer informatie over deze opties en hoe u deze kunt gebruiken, gaat u naar de [reguliere expressie taal-Naslag informatie](/dotnet/standard/base-types/regular-expression-language-quick-reference).

### <a name="escaping-characters"></a>Escape tekens

De back slash ( `\` ) wordt gebruikt om tekens te escapen zodat ze niet worden geparseerd door de reguliere expressie-engine.

De volgende tekens zijn gereserveerd: `[]().\^$|?*+{}` .

U moet deze tekens in uw patronen opescapeen zodat deze overeenkomen met uw invoer teken reeksen.

```powershell
# This returns true and matches numbers with at least 2 digits of precision.
# The decimal point is escaped using the backslash.
'3.141' -match '3\.\d{2,}'
```

Er is een statische methode van de regex-klasse die tekst voor u kan escapef.

```powershell
[regex]::escape('3.\d{2,}')
```

```Output
3\.\\d\{2,}
```

> [!NOTE]
> Hiermee worden alle gereserveerde reguliere expressie tekens geescapet, inclusief de bestaande backslashes die in teken klassen worden gebruikt. Zorg ervoor dat u deze alleen gebruikt in het gedeelte van het patroon dat u wilt escapepen.

#### <a name="other-character-escapes"></a>Andere teken-Escapes

Er zijn ook gereserveerde teken-Escapes die u kunt gebruiken om speciale teken typen te koppelen.

Hier volgen enkele veelgebruikte escape-tekens:

|Escape teken  |Beschrijving  |
|---------|---------|
|`\t`|Komt overeen met een tabblad|
|`\n`|Komt overeen met een nieuwe regel|
|`\r`|Komt overeen met een Enter-retour|

### <a name="groups-captures-and-substitutions"></a>Groepen, vastleg ging en vervangingen

Met groeperings constructies wordt een invoer teken reeks gescheiden in subtekenreeksen die kunnen worden vastgelegd of genegeerd. Gegroepeerde subtekenreeksen worden subexpressies genoemd. Standaard worden subexpressies vastgelegd in genummerde groepen, maar u kunt ook namen toewijzen.

Een groeperings constructie is een reguliere expressie tussen haakjes. Alle tekst die overeenkomt met de Inge sloten reguliere expressie wordt vastgelegd. In het volgende voor beeld wordt de invoer tekst in twee opname groepen onderverdeeld.

```powershell
'The last logged on user was CONTOSO\jsmith' -match '(.+was )(.+)'
```

```Output
True
```

Gebruik de `$Matches` automatische **hashtabel** -variabele om vastgelegde tekst op te halen.
De tekst die de volledige overeenkomst vertegenwoordigt, wordt opgeslagen op de sleutel `0` .

```powershell
$Matches.0
```

```Output
The last logged on user was CONTOSO\jsmith
```

Vastleg ging worden opgeslagen in numerieke sleutels met **gehele getallen** die van links naar rechts worden verhoogd. Capture `1` bevat alle tekst totdat de gebruikers naam, Capture `2` bevat alleen de gebruikers naam.

```powershell
$Matches
```

```Output
Name                           Value
----                           -----
2                              CONTOSO\jsmith
1                              The last logged on user was
0                              The last logged on user was CONTOSO\jsmith
```

> [!IMPORTANT]
> De `0` sleutel is een **geheel getal**. U kunt elke **hash** -methode gebruiken om toegang te krijgen tot de opgeslagen waarde.
>
> ```
> PS> 'Good Dog' -match 'Dog'
> True
>
> PS> $Matches[0]
> Dog
>
> PS> $Matches.Item(0)
> Dog
>
> PS> $Matches.0
> Dog
> ```

#### <a name="named-captures"></a>Benoemde opnamen

Standaard worden opnamen opgeslagen in oplopende numerieke volg orde, van links naar rechts.
U kunt ook een **naam** toewijzen aan een opname groep. Deze **naam** wordt een sleutel voor de `$Matches` Automatische variabele **hashtabel** .

In een opname groep gebruikt `?<keyname>` u om opgenomen gegevens onder een benoemde sleutel op te slaan.

```
PS> $string = 'The last logged on user was CONTOSO\jsmith'
PS> $string -match 'was (?<domain>.+)\\(?<user>.+)'
True

PS> $Matches

Name                           Value
----                           -----
domain                         CONTOSO
user                           jsmith
0                              was CONTOSO\jsmith

PS> $Matches.domain
CONTOSO

PS> $Matches.user
jsmith
```

In het volgende voor beeld wordt de meest recente logboek vermelding opgeslagen in het Windows-beveiligings logboek.
Met de gevoorziete reguliere expressie worden de gebruikers naam en het domein uit het bericht geëxtraheerd en opgeslagen onder de sleutels: **N** voor naam en **D** voor domein.

```powershell
$log = (Get-WinEvent -LogName Security -MaxEvents 1).message
$r = '(?s).*Account Name:\s*(?<N>.*).*Account Domain:\s*(?<D>[A-Z,0-9]*)'
$log -match $r
```

```Output
True
```

```powershell
$Matches
```

```Output
Name                           Value
----                           -----
D                              CONTOSO
N                              jsmith
0                              A process has exited....
```

Zie [Construct groups in reguliere expressies](/dotnet/standard/base-types/grouping-constructs-in-regular-expressions)voor meer informatie.

#### <a name="substitutions-in-regular-expressions"></a>Vervangingen in reguliere expressies

Met de reguliere expressies met de `-replace` operator kunt u tekst dynamisch vervangen met behulp van vastgelegde tekst.

`<input> -replace <original>, <substitute>`

- `<input>`: De teken reeks die moet worden doorzocht
- `<original>`: Een reguliere expressie die wordt gebruikt om de invoer teken reeks te doorzoeken
- `<substitute>`: Een expressie voor vervanging van een reguliere expressie om overeenkomsten te vervangen die in de invoer teken reeks zijn gevonden.

> [!NOTE]
> De `<original>` `<substitute>` operanden en zijn onderworpen aan regels van de reguliere-expressie-engine, zoals teken-Escapes.

In de teken reeks kan naar de opname groepen worden verwezen `<substitute>` . De vervanging wordt uitgevoerd met behulp van het `$` teken voor de groeps-id.

U kunt op twee manieren verwijzen naar het vastleggen van groepen op **nummer** en **naam**.

- Op **nummer** : het vastleggen van groepen wordt van links naar rechts genummerd.

  ```powershell
  'John D. Smith' -replace '(\w+) (\w+)\. (\w+)', '$1.$2.$3@contoso.com'
  ```

  ```Output
  John.D.Smith@contoso.com
  ```

- Op **naam** : voor het vastleggen van groepen kan ook naar een naam worden verwezen.

  ```powershell
  'CONTOSO\Administrator' -replace '\w+\\(?<user>\w+)', 'FABRIKAM\${user}'
  ```

  ```Output
  FABRIKAM\Administrator
  ```

De `$&` expressie vertegenwoordigt alle overeenkomende tekst.

```powershell
'Gobble' -replace 'Gobble', '$& $&'
```

```Output
Gobble Gobble
```

> [!WARNING]
> Omdat het `$` teken wordt gebruikt in teken reeks uitbreiding, moet u letterlijke teken reeksen gebruiken met vervanging of het teken escapen `$` Wanneer u dubbele aanhalings tekens gebruikt.
>
> ```powershell
> 'Hello World' -replace '(\w+) \w+', '$1 Universe'
> "Hello World" -replace "(\w+) \w+", "`$1 Universe"
> ```
>
> ```Output
> Hello Universe
> Hello Universe
> ```
>
> Als u het `$` als letterlijk teken wilt gebruiken, gebruikt u dit `$$` in plaats van de normale escape-tekens. Wanneer u dubbele aanhalings tekens gebruikt, moet u nog steeds alle exemplaren van `$` vervangen om een onjuiste vervanging te voor komen.
>
> ```powershell
> '5.72' -replace '(.+)', '$$$1'
> "5.72" -replace "(.+)", "`$`$`$1"
> ```
>
> ```Output
> $5.72
> $5.72
> ```

Zie [vervangingen in reguliere expressies](/dotnet/standard/base-types/substitutions-in-regular-expressions)voor meer informatie.

## <a name="see-also"></a>Zie ook

[about_Comparison_Operators](about_Comparison_Operators.md)

[about_Operators](about_Operators.md)

