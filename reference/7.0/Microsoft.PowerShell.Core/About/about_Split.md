---
description: Hierin wordt uitgelegd hoe u de operator split gebruikt om een of meer teken reeksen te splitsen in subtekenreeksen.
Locale: en-US
ms.date: 03/30/2021
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_split?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Split
ms.openlocfilehash: fcf7568cfc2055331cc6025622352eee9711f4ec
ms.sourcegitcommit: 4d6ed6f7d747a9bbb3fcfcf6c981c5aa8a973a08
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 03/31/2021
ms.locfileid: "106072437"
---
# <a name="about-split"></a>Over splitsen

## <a name="short-description"></a>KORTE BESCHRIJVING
Hierin wordt uitgelegd hoe u de operator split gebruikt om een of meer teken reeksen te splitsen in subtekenreeksen.

## <a name="long-description"></a>LANGE BESCHRIJVING

Met de operator Split worden een of meer teken reeksen gesplitst in subtekenreeksen. U kunt de volgende elementen van de gesplitste bewerking wijzigen:

- Vorm. De standaard waarde is witruimte, maar u kunt tekens, teken reeksen, patronen of script blokken opgeven waarmee het scheidings teken wordt opgegeven. De Splits operator in Power Shell maakt gebruik van een reguliere expressie in het scheidings teken, in plaats van een eenvoudig personage.
- Het maximum aantal subtekenreeksen. Standaard worden alle subtekenreeksen geretourneerd. Als u een getal opgeeft dat kleiner is dan het aantal subtekenreeksen, worden de resterende subtekenreeksen samengevoegd in de laatste subtekenreeks.
- Opties die de voor waarden opgeven waaronder het scheidings teken wordt vergeleken, zoals SimpleMatch en meerregelige.

## <a name="syntax"></a>SYNTAXIS

In het volgende diagram ziet u de syntaxis voor de operator-Split.

De parameter namen worden niet weer gegeven in de opdracht. Alleen de parameter waarden bevatten. De waarden moeten worden weer gegeven in de volg orde die is opgegeven in het syntaxis diagram.

```
-Split <String>
-Split (<String[]>)
<String> -Split <Delimiter>[,<Max-substrings>[,"<Options>"]]
<String> -Split {<ScriptBlock>} [,<Max-substrings>]
```

U kunt vervangen `-iSplit` of `-cSplit` voor `-split` een binaire Splits instructie (een split-instructie met een scheidings teken of script blok). De `-iSplit` `-split` Opera tors en zijn niet hoofdletter gevoelig. De `-cSplit` operator is hoofdletter gevoelig, wat betekent dat er sprake is van het Toep assen van de scheidings regels.

## <a name="parameters"></a>PARAMETERS

### <a name="string-or-string"></a>\<String\> of \<String[]\>

Hiermee geeft u een of meer teken reeksen moet worden gesplitst. Als u meerdere teken reeksen verzendt, worden alle teken reeksen gesplitst met dezelfde scheidings regels.

Voorbeeld:

```
-split "red yellow blue green"
red
yellow
blue
green
```

### \<Delimiter\>

De tekens die het einde van een subtekenreeks identificeren. Het standaard scheidings teken is witruimte, inclusief spaties en niet-afdruk bare tekens, zoals nieuwe regel ( \` n) en tab ( \` t). Wanneer de teken reeksen zijn gesplitst, wordt het scheidings teken uit alle subtekenreeksen wegge laten. Voorbeeld:

```powershell
"Lastname:FirstName:Address" -split ":"
Lastname
FirstName
Address
```

Standaard wordt het scheidings teken uit de resultaten wegge laten. Als u het scheidings teken geheel of gedeeltelijk wilt behouden, plaatst u tussen haakjes het onderdeel dat u wilt behouden.
Als de `<Max-substrings>` para meter wordt toegevoegd, heeft dit prioriteit wanneer uw opdracht de verzameling opsplitst. Als u ervoor kiest om een scheidings teken op te nemen als onderdeel van de uitvoer, retourneert de opdracht het scheidings teken als onderdeel van de uitvoer; het splitsen van de teken reeks om het scheidings teken als onderdeel van de uitvoer te retour neren, telt echter niet als een splitsing.

Voorbeelden:

```powershell
"Lastname:FirstName:Address" -split "(:)"
Lastname
:
FirstName
:
Address

"Lastname/:/FirstName/:/Address" -split "/(:)/"
Lastname
:
FirstName
:
Address
```

### `<Max-substrings>`

Hiermee geeft u het maximum aantal subtekenreeksen op dat door de Splits bewerking wordt geretourneerd. De standaard waarde is alle subtekenreeksen die worden gesplitst door het scheidings teken. Als er meer subtekenreeksen zijn, worden deze samengevoegd met de uiteindelijke subtekenreeks. Als er minder subtekenreeksen zijn, worden alle subtekenreeksen geretourneerd. De waarde 0 retourneert alle subtekenreeksen.

Voorbeeld:

```powershell
$c = "Mercury,Venus,Earth,Mars,Jupiter,Saturn,Uranus,Neptune"
$c -split ",", 5
```

```Output
Mercury
Venus
Earth
Mars
Jupiter,Saturn,Uranus,Neptune
```

Als u meer dan één teken reeks (een matrix met teken reeksen) naar de `-split` operator verzendt, `Max-substrings` wordt de limiet voor elke teken reeks afzonderlijk toegepast.

```powershell
$c = 'a,b,c','1,2,3,4,5'
$c -split ',', 3

a
b
c
1
2
3,4,5
```

`<Max-substrings>` geeft niet het maximum aantal objecten op dat wordt geretourneerd. In het volgende voor beeld `<Max-substrings>` is ingesteld op 3.
Dit resulteert in drie subtekenreekswaarde waarden, maar in totaal vijf teken reeksen in de resulterende uitvoer. Het scheidings teken wordt opgenomen na de splitsing totdat het maximum van de drie subtekenreeksen is bereikt. Extra scheidings tekens in de uiteindelijke subtekenreeks worden deel van de subtekenreeks.

```powershell
'Chocolate-Vanilla-Strawberry-Blueberry' -split '(-)', 3
```

```Output
Chocolate
-
Vanilla
-
Strawberry-Blueberry
```

Negatieve waarden geven de hoeveelheid subtekenreeksen aan die is aangevraagd vanaf het einde van de invoer teken reeks.

> [!NOTE]
> Er is ondersteuning voor negatieve waarden toegevoegd aan Power shell 7.

```powershell
$c = "Mercury,Venus,Earth,Mars,Jupiter,Saturn,Uranus,Neptune"
$c -split ",", -5
```

```Output
Mercury,Venus,Earth,Mars
Jupiter
Saturn
Uranus
Neptune
```

### \<ScriptBlock\>

Een expressie waarmee de regels voor het Toep assen van het scheidings teken worden opgegeven. De expressie moet $true of $false evalueren. Plaats het script blok tussen accolades.

Voorbeeld:

```powershell
$c = "Mercury,Venus,Earth,Mars,Jupiter,Saturn,Uranus,Neptune"
$c -split {$_ -eq "e" -or $_ -eq "p"}
```

```Output
M
rcury,V
nus,
arth,Mars,Ju
it
r,Saturn,Uranus,N

tun
```

### \<Options\>

Plaats de naam van de optie tussen aanhalings tekens. Opties zijn alleen geldig wanneer de \<Max-substrings\> para meter wordt gebruikt in de instructie.

De syntaxis voor de para meter Options is:

```
"SimpleMatch [,IgnoreCase]"

"[RegexMatch] [,IgnoreCase] [,CultureInvariant]
[,IgnorePatternWhitespace] [,ExplicitCapture]
[,Singleline | ,Multiline]"
```

De SimpleMatch-opties zijn:

- **SimpleMatch**: gebruik eenvoudige teken reeks vergelijking bij het evalueren van het scheidings teken. Kan niet worden gebruikt met RegexMatch.
- **IgnoreCase**: dwingt niet-hoofdletter gevoelige overeenkomst af, zelfs als de operator-cSplit is opgegeven.

De RegexMatch-opties zijn:

- **RegexMatch**: gebruik reguliere expressie matching om het scheidings teken te evalueren. Dit is de standaardinstelling. Kan niet worden gebruikt met SimpleMatch.
- **IgnoreCase**: dwingt niet-hoofdletter gevoelige overeenkomst af, zelfs als de operator-cSplit is opgegeven.
- **CultureInvariant**: negeert culturele verschillen in taal wanneer het scheidings teken wordt evaluting. Alleen geldig voor RegexMatch.
- **IgnorePatternWhitespace**: negeert witruimte zonder escape-teken en opmerkingen met het hekje (#). Alleen geldig voor RegexMatch.
- **Meerdere** regels: de modus `^` voor meerdere regels en `$` het begin einde van elke regel wordt vergeleken in plaats van het begin en het einde van de invoer teken reeks.
- **Modus singleline**: de modus singleline-modus behandelt de invoer teken reeks als een *modus singleline*.
  Hiermee wordt het `.` teken afgedwongen dat overeenkomt met elk teken (inclusief nieuwe regels), in plaats van elk teken te vergelijken met de nieuwe regel `\n` .
- **ExplicitCapture**: negeert niet-benoemde overeenkomende groepen, zodat alleen expliciete opname groepen worden geretourneerd in de lijst met resultaten. Alleen geldig voor RegexMatch.

## <a name="unary-and-binary-split-operators"></a>Unaire en binaire SPLITs Opera tors

De unaire Splits operator ( `-split <string>` ) heeft een hogere prioriteit dan een komma. Als u dus een door komma's gescheiden lijst met teken reeksen verzendt naar de operator unsplit, wordt alleen de eerste teken reeks (vóór de eerste komma) gesplitst.

Gebruik een van de volgende patronen om meer dan één teken reeks te splitsen:

- De binaire Splits operator ( \<string[]\> -Split \<delimiter\> ) gebruiken
- Alle teken reeksen tussen haakjes plaatsen
- De teken reeksen in een variabele opslaan en vervolgens de variabele naar de Splits operator verzenden

Kijk eens naar het volgende voorbeeld:

```
PS> -split "1 2", "a b"
1
2
a b
```

```
PS> "1 2", "a b" -split " "
1
2
a
b
```

```
PS> -split ("1 2", "a b")
1
2
a
b
```

```
PS> $a = "1 2", "a b"
PS> -split $a
1
2
a
b
```

## <a name="examples"></a>VOORBEELDEN

De volgende instructie splitst de teken reeks op een spatie.

```powershell
-split "Windows PowerShell 2.0`nWindows PowerShell with remoting"
```

```Output

Windows
PowerShell
2.0
Windows
PowerShell
with
remoting
```

De volgende instructie splitst de teken reeks op een wille keurige komma.

```powershell
"Mercury,Venus,Earth,Mars,Jupiter,Saturn,Uranus,Neptune" -split ','
```

```Output
Mercury
Venus
Earth
Mars
Jupiter
Saturn
Uranus
Neptune
```

Met de volgende instructie wordt de teken reeks in het patroon ' er ' gesplitst.

```powershell
"Mercury,Venus,Earth,Mars,Jupiter,Saturn,Uranus,Neptune" -split 'er'
```

```Output
M
cury,Venus,Earth,Mars,Jupit
,Saturn,Uranus,Neptune
```

De volgende instructie voert een hoofdletter gevoelige splitsing uit op de letter "N".

```powershell
"Mercury,Venus,Earth,Mars,Jupiter,Saturn,Uranus,Neptune" -cSplit 'N'
```

```Output
Mercury,Venus,Earth,Mars,Jupiter,Saturn,Uranus,
eptune
```

Met de volgende instructie wordt de teken reeks op ' e ' en ' t ' gesplitst.

```powershell
"Mercury,Venus,Earth,Mars,Jupiter,Saturn,Uranus,Neptune" -split '[et]'
```

```Output
M
rcury,V
nus,
ar
h,Mars,Jupi

r,Sa
urn,Uranus,N
p
un
```

Met de volgende instructie wordt de teken reeks op ' e ' en ' r ' gesplitst, maar worden de resulterende subtekenreeksen beperkt tot zes subtekenreeksen.

```powershell
"Mercury,Venus,Earth,Mars,Jupiter,Saturn,Uranus,Neptune" -split '[er]', 6
```

```Output
M

cu
y,V
nus,
arth,Mars,Jupiter,Saturn,Uranus,Neptune
```

Met de volgende instructie wordt een teken reeks gesplitst in drie subtekenreeksen.

```powershell
"a,b,c,d,e,f,g,h" -split ",", 3
```

```Output
a
b
c,d,e,f,g,h
```

Met de volgende instructie wordt een teken reeks gesplitst in drie subtekenreeksen vanaf het einde van de teken reeks.

```powershell
"a,b,c,d,e,f,g,h" -split ",", -3
```

```Output
a,b,c,d,e,f
g
h
```

Met de volgende instructie splitst u twee teken reeksen in drie subtekenreeksen.
(De limiet wordt afzonderlijk toegepast op elke teken reeks.)

```powershell
"a,b,c,d", "e,f,g,h" -split ",", 3
```

```Output
a
b
c,d
e
f
g,h
```

Met de volgende instructie wordt elke regel in de teken reeks in het eerste cijfer gesplitst. De optie voor meerdere regels wordt gebruikt om het begin van elke regel en teken reeks te herkennen.

De 0 vertegenwoordigt de waarde ' return all ' van de para meter Max-subtekenreeksen. U kunt opties, zoals meerregelige, alleen gebruiken wanneer de waarde voor de Max-subtekenreeksen is opgegeven.

```powershell
$a = @'
1The first line.
2The second line.
3The third of three lines.
'@
$a -split "^\d", 0, "multiline"
```

```Output

The first line.

The second line.

The third of three lines.
```

In de volgende instructie wordt de back slash gebruikt om het punt scheidings teken (.) te escapen.

Met de standaard waarde RegexMatch, de punt tussen aanhalings tekens (".") wordt geïnterpreteerd zodat deze overeenkomt met een wille keurig teken behalve een nieuwe regel. Als gevolg hiervan retourneert de gesplitste instructie een lege regel voor elk teken behalve een nieuwe voor waarde.

```powershell
"This.is.a.test" -split "\."
```

```Output
This
is
a
test
```

De volgende instructie maakt gebruik van de SimpleMatch-optie om de operator-split te sturen om het punt scheidings teken letterlijk te interpreteren.

De 0 vertegenwoordigt de waarde ' return all ' van de para meter Max-subtekenreeksen. U kunt opties, zoals SimpleMatch, alleen gebruiken wanneer de waarde voor de Max-subtekenreeksen is opgegeven.

```powershell
"This.is.a.test" -split ".", 0, "simplematch"
```

```Output
This
is
a
test
```

Met de volgende instructie wordt de teken reeks in een van de twee scheidings tekens gesplitst, afhankelijk van de waarde van een variabele.

```powershell
$i = 1
$c = "LastName, FirstName; Address, City, State, Zip"
$c -split $(if ($i -lt 1) {","} else {";"})
```

```Output
LastName, FirstName
 Address, City, State, Zip
```

## <a name="see-also"></a>ZIE OOK

[Split-pad](xref:Microsoft.PowerShell.Management.Split-Path)

[about_Operators](about_Operators.md)

[about_Comparison_Operators](about_Comparison_Operators.md)

[about_Join](about_Join.md)
