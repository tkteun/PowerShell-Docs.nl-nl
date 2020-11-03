---
description: Hierin wordt beschreven hoe variabelen waarden opslaan die kunnen worden gebruikt in Power shell.
keywords: powershell,cmdlet
Locale: en-US
ms.date: 03/19/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_variables?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Variables
ms.openlocfilehash: 0865afe69f5f1774e90d2d2dc5827d628cab0f6a
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/13/2020
ms.locfileid: "93252134"
---
# <a name="about-variables"></a>Over variabelen

## <a name="short-description"></a>Korte beschrijving

Hierin wordt beschreven hoe variabelen waarden opslaan die kunnen worden gebruikt in Power shell.

## <a name="long-description"></a>Lange beschrijving

U kunt alle typen waarden opslaan in Power shell-variabelen. U kunt bijvoorbeeld de resultaten van opdrachten opslaan en elementen opslaan die in opdrachten en expressies worden gebruikt, zoals namen, paden, instellingen en waarden.

Een variabele is een geheugen eenheid waarin waarden worden opgeslagen. In Power shell worden variabelen vertegenwoordigd door teken reeksen die beginnen met een dollar teken ( `$` ), zoals `$a` , `$process` of `$my_var` .

Namen van variabelen zijn niet hoofdletter gevoelig en kunnen spaties en speciale tekens bevatten. Namen van variabelen met speciale tekens en spaties zijn echter lastig te gebruiken en moeten worden vermeden. Zie [namen van variabelen die speciale tekens bevatten](#variable-names-that-include-special-characters)voor meer informatie.

Er zijn verschillende typen variabelen in Power shell.

- Door gebruiker gemaakte variabelen: door de gebruiker gemaakte variabelen worden gemaakt en onderhouden door de gebruiker. De variabelen die u in de Power shell-opdracht regel maakt, bestaan standaard alleen wanneer het Power shell-venster is geopend. Wanneer het Power shell-venster wordt gesloten, worden de variabelen verwijderd. Als u een variabele wilt opslaan, voegt u deze toe aan uw Power shell-profiel. U kunt ook variabelen maken in scripts met globaal, script of lokaal bereik.

- Automatische variabelen: automatische variabelen slaan de status van Power shell op. Deze variabelen worden gemaakt door Power shell en Power shell wijzigt hun waarden naar behoefte om hun nauw keurigheid te behouden. Gebruikers kunnen de waarde van deze variabelen niet wijzigen. De `$PSHOME` variabele slaat bijvoorbeeld het pad op naar de installatie directory van Power shell.

  Zie [about_Automatic_Variables](about_Automatic_Variables.md)voor meer informatie, een lijst en een beschrijving van de automatische variabelen.

- Voorkeurs variabelen: voorkeurs variabelen slaan gebruikers voorkeuren op voor Power shell. Deze variabelen worden gemaakt door Power shell en worden gevuld met standaard waarden. Gebruikers kunnen de waarden van deze variabelen wijzigen. De `$MaximumHistoryCount` variabele bepaalt bijvoorbeeld het maximum aantal vermeldingen in de sessie geschiedenis.

  Zie [about_Preference_Variables](about_Preference_Variables.md)voor meer informatie, een lijst en een beschrijving van de voorkeurs variabelen.

## <a name="working-with-variables"></a>Werken met variabelen

Als u een nieuwe variabele wilt maken, gebruikt u een toewijzings instructie om een waarde toe te wijzen aan de variabele. U hoeft de variabele niet te declareren voordat u deze gebruikt. De standaard waarde van alle variabelen is `$null` .

Als u een lijst wilt weer geven met alle variabelen in uw Power shell-sessie, typt u `Get-Variable` . De namen van variabelen worden weer gegeven zonder het voor gaande dollar `$` teken () dat wordt gebruikt om te verwijzen naar variabelen.

Bijvoorbeeld:

```powershell
$MyVariable = 1, 2, 3

$Path = "C:\Windows\System32"
```

Variabelen zijn handig om de resultaten van opdrachten op te slaan.

Bijvoorbeeld:

```powershell
$Processes = Get-Process

$Today = (Get-Date).DateTime
```

Als u de waarde van een variabele wilt weer geven, typt u de naam van de variabele, voorafgegaan door een dollar teken ( `$` ).

Bijvoorbeeld:

```powershell
$MyVariable
```

```Output
1
2
3
```

```powershell
$Today
```

```Output
Tuesday, September 3, 2019 09:46:46
```

Als u de waarde van een variabele wilt wijzigen, wijst u een nieuwe waarde toe aan de variabele.

In de volgende voor beelden wordt de waarde van de variabele weer gegeven `$MyVariable` , wordt de waarde van de variabele gewijzigd, waarna de nieuwe waarde wordt weer gegeven.

```powershell
$MyVariable = 1, 2, 3
$MyVariable
```

```Output
1
2
3
```

```powershell
$MyVariable = "The green cat."
$MyVariable
```

```Output
The green cat.
```

Als u de waarde van een variabele wilt verwijderen, gebruikt u de `Clear-Variable` cmdlet of wijzigt u de waarde in `$null` .

```powershell
Clear-Variable -Name MyVariable
```

```powershell
$MyVariable = $null
```

Als u de variabele wilt verwijderen, gebruikt u [Remove-variable](xref:Microsoft.PowerShell.Utility.Remove-Variable) of [Remove-item](xref:Microsoft.PowerShell.Management.Remove-Item).

```powershell
Remove-Variable -Name MyVariable
```

```powershell
Remove-Item -Path Variable:\MyVariable
```

## <a name="types-of-variables"></a>Typen variabelen

U kunt elk type object in een variabele opslaan, met inbegrip van gehele getallen, teken reeksen, matrices en hash-tabellen. En, objecten die processen, services, gebeurtenis logboeken en computers vertegenwoordigen.

Power shell-variabelen worden op een losse manier getypt, wat betekent dat ze niet zijn beperkt tot een bepaald type object. Eén variabele kan zelfs een verzameling, of matrix, van verschillende typen objecten tegelijk bevatten.

Het gegevens type van een variabele wordt bepaald door de .NET-typen van de waarden van de variabele. Als u het object type van een variabele wilt weer geven, gebruikt u [Get-member](xref:Microsoft.PowerShell.Utility.Get-Member).

Bijvoorbeeld:

```powershell
$a = 12                         # System.Int32
$a = "Word"                     # System.String
$a = 12, "Word"                 # array of System.Int32, System.String
$a = Get-ChildItem C:\Windows   # FileInfo and DirectoryInfo types
```

U kunt een type kenmerk en een cast-notatie gebruiken om ervoor te zorgen dat een variabele alleen specifieke object typen of objecten kan bevatten die kunnen worden geconverteerd naar dat type. Als u een waarde van een ander type wilt toewijzen, probeert Power shell de waarde naar het type te converteren. Als het type niet kan worden geconverteerd, mislukt de toewijzings instructie.

Als u de cast-notatie wilt gebruiken, voert u een type naam tussen vier Kante haken in, vóór de naam van de variabele (aan de linkerkant van de toewijzings instructie). In het volgende voor beeld wordt een `$number` variabele gemaakt die alleen gehele getallen kan bevatten, een `$words` variabele die alleen teken reeksen kan bevatten en een `$dates` variabele die alleen **DateTime** -objecten kan bevatten.

```powershell
[int]$number = 8
$number = "12345"  # The string is converted to an integer.
$number = "Hello"
```

```Output
Cannot convert value "Hello" to type "System.Int32". Error: "Input string was
 not in a correct format."
At line:1 char:1
+ $number = "Hello"
+ ~~~~~~~~~~~~~~~~~
+ CategoryInfo          : MetadataError: (:) [],
    ArgumentTransformationMetadataException
+ FullyQualifiedErrorId : RuntimeException
```

```powershell
[string]$words = "Hello"
$words = 2       # The integer is converted to a string.
$words += 10     # The plus (+) sign concatenates the strings.
$words
```

```Output
210
```

```powershell
[datetime] $dates = "09/12/91"  # The string is converted to a DateTime object.
$dates
```

```Output
Thursday, September 12, 1991 00:00:00
```

```powershell
$dates = 10    # The integer is converted to a DateTime object.
$dates
```

```Output
Monday, January 1, 0001 00:00:00
```

## <a name="using-variables-in-commands-and-expressions"></a>Variabelen gebruiken in opdrachten en expressies

Als u een variabele wilt gebruiken in een opdracht of expressie, typt u de naam van de variabele, voorafgegaan door het dollar `$` teken ().

Als de naam van de variabele en het dollar teken niet tussen aanhalings tekens staan, of als deze tussen dubbele aanhalings `"` tekens () zijn geplaatst, wordt de waarde van de variabele in de opdracht of expressie gebruikt.

Als de naam van de variabele en het dollar teken tussen enkele aanhalings `'` tekens () worden geplaatst, wordt de naam van de variabele in de expressie gebruikt.

Zie [about_Quoting_Rules](about_Quoting_Rules.md)voor meer informatie over het gebruik van aanhalings tekens in Power shell.

In dit voor beeld wordt de waarde van de `$PROFILE` variabele opgehaald, het pad naar het Power shell-gebruikers profiel bestand in de Power shell-console.

```powershell
$PROFILE
```

```Output
C:\Users\User01\Documents\PowerShell\Microsoft.PowerShell_profile.ps1
```

In dit voor beeld worden twee opdrachten weer gegeven waarmee het Power shell-profiel in **notepad.exe** kan worden geopend. Het voor beeld met dubbele aanhalings `"` tekens () maakt gebruik van de waarde van de variabele.

```powershell
notepad $PROFILE

notepad "$PROFILE"
```

In de volgende voor beelden worden enkele aanhalings `'` tekens () gebruikt die de variabele behandelen als letterlijke tekst.

```powershell
'$PROFILE'
```

```Output
$PROFILE
```

```powershell
'Use the $PROFILE variable.'
```

```Output
Use the $PROFILE variable.
```

## <a name="variable-names-that-include-special-characters"></a>Namen van variabelen die speciale tekens bevatten

Namen van variabelen beginnen met een dollar ( `$` ) teken en kunnen alfanumerieke tekens en speciale tekens bevatten. De lengte van de variabele naam wordt alleen beperkt door het beschik bare geheugen.

De best practice is dat namen van variabelen alleen alfanumerieke tekens en het onderstrepings `_` teken () bevatten. Namen van variabelen die spaties en andere speciale tekens bevatten, zijn lastig te gebruiken en moeten worden vermeden.

Alfanumerieke namen van variabelen kunnen de volgende tekens bevatten:

- Unicode-tekens uit deze categorieën: **Lu** , **ll** , **lt** , **LM** , **lo** of **ND**.
- Onderstrepings `_` teken ().
- Vraag teken ( `?` )-teken.

De volgende lijst bevat de beschrijvingen van de Unicode-categorie. Zie [UnicodeCategory](/dotnet/api/system.globalization.unicodecategory)voor meer informatie.

- **Lu** -UppercaseLetter
- **Ll** -LowercaseLetter
- **Lt** -TitlecaseLetter
- **LM** -ModifierLetter
- **Lo** -OtherLetter
- **ND** -DecimalDigitNumber

Als u een naam van een variabele wilt maken of weer geven die spaties of speciale tekens bevat, moet u de naam van de variabele tussen accolades ( `{}` ) plaatsen.
De accolades direct Power shell om de tekens van de naam van de variabele te interpreteren als letterlijke waarden.

Namen van speciale teken variabelen kunnen de volgende tekens bevatten:

- Elk Unicode-teken, met de volgende uitzonde ringen:
  - Het accolade `}` teken () sluiten (U + 007D).
  - Het apostroffen ( `` ` `` )-teken (U + 0060). De apostroffen wordt gebruikt om Unicode-tekens te escapen zodat ze als letterlijke waarden worden behandeld.

Power Shell heeft gereserveerde variabelen `$$` , zoals,, `$?` `$^` en `$_` die alfanumerieke en speciale tekens bevatten. Zie [about_Automatic_Variables](about_automatic_variables.md)voor meer informatie.

Met de volgende opdracht wordt bijvoorbeeld de variabele met de naam gemaakt `save-items` . De accolades ( `{}` ) zijn nodig omdat de naam van de variabele een afbreek streepje () met een `-` speciaal teken bevat.

```powershell
${save-items} = "a", "b", "c"
${save-items}
```

```Output
a
b
c
```

Met de volgende opdracht worden de onderliggende items in de map opgehaald die wordt vertegenwoordigd door de `ProgramFiles(x86)` omgevings variabele.

```powershell
Get-ChildItem ${env:ProgramFiles(x86)}
```

Als u wilt verwijzen naar een naam van een variabele die accolades bevat, plaatst u de naam van de variabele tussen accolades en gebruikt u het apostroffen-teken om de accolades te escapen. Als u bijvoorbeeld een variabele met de naam `this{value}is` type wilt maken:

```powershell
${this`{value`}is} = "This variable name uses braces and backticks."
${this`{value`}is}
```

```Output
This variable name uses braces and backticks.
```

## <a name="variables-and-scope"></a>Variabelen en bereik

Variabelen zijn standaard alleen beschikbaar in het bereik waarin ze zijn gemaakt.

Een variabele die u in een functie hebt gemaakt, is bijvoorbeeld alleen beschikbaar in de functie. Een variabele die u in een script maakt, is alleen beschikbaar in het script. Als u het script met de punt-bron, wordt de variabele toegevoegd aan het huidige bereik. Zie [about_Scopes](about_Scopes.md)voor meer informatie.

U kunt een bereik wijzigings functie gebruiken om het standaard bereik van de variabele te wijzigen. Met de volgende expressie maakt u een variabele met de naam `Computers` . De variabele heeft een globaal bereik, zelfs wanneer deze in een script of functie is gemaakt.

```powershell
$Global:Computers = "Server01"
```

Voor elk script of elke opdracht die uit de sessie wordt uitgevoerd, hebt u de `Using` bereik wijzigings functie nodig om variabele waarden van het aanroepende sessie bereik in te sluiten, zodat out of Session-code er toegang toe heeft.

Zie [about_Remote_Variables](about_Remote_Variables.md)voor meer informatie.

## <a name="saving-variables"></a>Variabelen opslaan

Variabelen die u maakt, zijn alleen beschikbaar in de sessie waarin u ze maakt. Ze gaan verloren wanneer u uw sessie sluit.

Als u de variabele wilt maken in elke Power shell-sessie die u start, voegt u de variabele toe aan uw Power shell-profiel.

Als u bijvoorbeeld de waarde van de `$VerbosePreference` variabele in elke Power shell-sessie wilt wijzigen, voegt u de volgende opdracht toe aan uw Power shell-profiel.

```powershell
$VerbosePreference = "Continue"
```

U kunt deze opdracht toevoegen aan uw Power shell-profiel door het bestand te openen `$PROFILE` in een tekst editor, zoals **notepad.exe**. Zie [about_Profiles](about_Profiles.md)voor meer informatie over Power shell-profielen.

## <a name="the-variable-drive"></a>De variabele: station

De provider van de Power shell-variabele maakt een `Variable:` station dat eruitziet en fungeert als een bestandssysteem station, maar bevat de variabelen in uw sessie en hun waarden.

Als u het station wilt wijzigen `Variable:` , gebruikt u de volgende opdracht:

```powershell
Set-Location Variable:
```

`Variable:`Gebruik de `Get-Item` cmdlets of om de items en variabelen in het station weer te geven `Get-ChildItem` .

```powershell
Get-ChildItem Variable:
```

Als u de waarde van een bepaalde variabele wilt ophalen, gebruikt u de notatie File System om de naam van het station en de naam van de variabele op te geven. `$PSCulture`Gebruik bijvoorbeeld de volgende opdracht om de automatische variabele op te halen.

```powershell
Get-Item Variable:\PSCulture
```

```Output
Name                           Value
----                           -----
PSCulture                      en-US
```

Als u meer informatie over het `Variable:` station en de Power shell-variabele provider wilt weer geven, typt u:

```powershell
Get-Help Variable
```

## <a name="variable-syntax-with-provider-paths"></a>Variabele syntaxis met provider paden

U kunt een pad naar een provider voor voegsel met het dollar ( `$` )-teken en toegang krijgen tot de inhoud van elke provider die de [IContentCmdletProvider](/dotnet/api/system.management.automation.provider.icontentcmdletprovider) -interface implementeert.

De volgende ingebouwde Power shell-providers ondersteunen deze notatie:

- [about_Environment_Provider](about_Environment_Provider.md)
- [about_Variable_Provider](about_Variable_Provider.md)
- [about_Function_Provider](about_Function_Provider.md)
- [about_Alias_Provider](about_Alias_Provider.md)

## <a name="the-variable-cmdlets"></a>De variabele-cmdlets

Power shell bevat een set cmdlets die zijn ontworpen voor het beheren van variabelen.

Als u de cmdlets wilt weer geven, typt u:

```powershell
Get-Command -Noun Variable
```

Als u hulp wilt krijgen voor een specifieke cmdlet, typt u:

```powershell
Get-Help <cmdlet-name>
```

| Naam van cmdlet       | Beschrijving                                |
| ---------------   | ------------------------------------------ |
| `Clear-Variable`  | Hiermee verwijdert u de waarde van een variabele.           |
| `Get-Variable`    | Hiermee worden de variabelen in de huidige console opgehaald. |
| `New-Variable`    | Hiermee maakt u een nieuwe variabele.                    |
| `Remove-Variable` | Hiermee verwijdert u een variabele en de bijbehorende waarde.          |
| `Set-Variable`    | Wijzigt de waarde van een variabele.           |

## <a name="see-also"></a>Zie ook

[about_Automatic_Variables](about_Automatic_Variables.md)

[about_Environment_Variables](about_Environment_Variables.md)

[about_Preference_Variables](about_Preference_Variables.md)

[about_Profiles](about_Profiles.md)

[about_Quoting_Rules](about_Quoting_Rules.md)

[about_Scopes](about_Scopes.md)

[about_Remote_Variables](about_Remote_Variables.md)

