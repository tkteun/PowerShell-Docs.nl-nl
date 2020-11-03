---
description: Beschrijft de tref woorden in de Power shell-script taal.
keywords: powershell,cmdlet
Locale: en-US
ms.date: 10/06/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_language_keywords?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Language_Keywords
ms.openlocfilehash: 6d59d0ac58eb5d2ddecc69be97b1ccebaca58195
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/13/2020
ms.locfileid: "93252609"
---
# <a name="about-language-keywords"></a>Over taal trefwoorden

## <a name="short-description"></a>KORTE BESCHRIJVING
Beschrijft de tref woorden in de Power shell-script taal.

## <a name="long-description"></a>LANGE BESCHRIJVING

Power Shell heeft de volgende taal trefwoorden. Zie het onderwerp over het tref woord en de informatie die volgt op de tabel voor meer informatie.

Zoek     | Naslaginformatie
---         | ---
Beginnen       | [about_Functions](about_Functions.md), [about_Functions_Advanced](about_Functions_Advanced.md)
Breken       | [about_Break](about_Break.md), [about_Trap](about_Trap.md)
Achterstand       | [about_Try_Catch_Finally](about_Try_Catch_Finally.md)
Klasse       | [about_Classes](about_Classes.md)
Doorgaan    | [about_Continue](about_Continue.md), [about_Trap](about_Trap.md)
Gegevens        | [about_Data_Sections](about_Data_Sections.md)
Bepaalt      | Gereserveerd voor toekomstig gebruik
Wel doen          | [about_Do](about_Do.md), [about_While](about_While.md)
DynamicParam| [about_Functions_Advanced_Parameters](about_Functions_Advanced_Parameters.md)
Hierin        | [about_If](about_If.md)
Elseif      | [about_If](about_If.md)
Beëindigen         | [about_Functions](about_Functions.md), [about_Functions_Advanced_Methods](about_Functions_Advanced_Methods.md)
Enum        | [about_Enum](about_Enum.md)
Afsluiten        | [Beschreven in dit onderwerp](#exit)
Filteren      | [about_Functions](about_Functions.md)
Werd     | [about_Try_Catch_Finally](about_Try_Catch_Finally.md)
Voor         | [about_For](about_For.md)
ForEach     | [about_ForEach](about_ForEach.md)
Van        | Gereserveerd voor toekomstig gebruik
Functie    | [about_Functions](about_Functions.md), [about_Functions_Advanced](about_Functions_Advanced.md)
Verborgen      | [about_Hidden](about_Hidden.md)
Als          | [about_If](about_If.md)
In          | [about_ForEach](about_ForEach.md)
InlineScript| [about_InlineScript](../../PSWorkflow/About/about_InlineScript.md)
Param       | [about_Functions](about_Functions.md)
Proces     | [about_Functions](about_Functions.md), [about_Functions_Advanced](about_Functions_Advanced.md)
Opvragen      | [about_Return](about_Return.md)
Statisch      | [about_Classes](about_Classes.md)
Switch      | [about_Switch](about_Switch.md)
Sprong       | [about_Throw](about_Throw.md), [about_Functions_Advanced_Methods](about_Functions_Advanced_Methods.md)
Overlapping        | [about_Trap](about_Trap.md), [about_Break](about_Break.md) [about_Try_Catch_Finally](about_Try_Catch_Finally.md)
Proberen         | [about_Try_Catch_Finally](about_Try_Catch_Finally.md)
Totdat       | [about_Do](about_Do.md)
Gebruiken       | [about_Using](about_Using.md), [about_Classes](about_Classes.md)
Gereserveerd         | Gereserveerd voor toekomstig gebruik
Het       | [about_While](about_While.md), [about_Do](about_Do.md)

Taal trefwoorden

### <a name="begin"></a>Beginnen

Hiermee wordt een deel van de hoofd tekst van een functie opgegeven, samen met de `DynamicParam` `Process` woorden, en `End` . De `Begin` lijst met instructies wordt één keer uitgevoerd voordat er objecten van de pijp lijn worden ontvangen.

Syntaxis:

```Syntax
function <name> {
    DynamicParam {<statement list>}
    begin {<statement list>}
    process {<statement list>}
    end {<statement list>}
}
```

### <a name="break"></a>Breken

Zorgt ervoor dat een script een lus verlaat.

Syntaxis:

```Syntax
while (<condition>) {
   <statements>
   ...

   break
   ...

   <statements>
}
```

### <a name="catch"></a>Achterstand

Hiermee geeft u een overzichts lijst moet worden uitgevoerd als er een fout optreedt in de lijst met bijbehorende instructie try. Een fout type vereist vier Kante haken. Het tweede paar haken geeft aan dat het fout type optioneel is.

Syntaxis:

```Syntax
try {<statement list>}
catch [[<error type>]] {<statement list>}
```

### <a name="class"></a>Klasse

Hiermee geeft u een nieuwe klasse op in Power shell.

Syntaxis:

```Syntax
class <class-name> {
    [[hidden] [static] <property-definition> ...]
    [<class-name>([argument-list>]) {<constructor-statement-list>} ...]
    [[hidden] [static] <method-definition> ...]
}
```

### <a name="continue"></a>Doorgaan

Zorgt ervoor dat een script stopt met het uitvoeren van een lus en om terug te gaan naar de voor waarde. Als aan de voor waarde wordt voldaan, wordt de lus opnieuw gestart door het script.

Syntaxis:

```Syntax
while (<condition>) {
   <statements>
   ...

   continue
   ...

   <statements>
}
```

### <a name="data"></a>Gegevens

In een script definieert een sectie die gegevens uit de script logica isoleert. Kan ook `If` instructies en enkele beperkte opdrachten bevatten.

Syntaxis:

```Syntax
data <variable> [-supportedCommand <cmdlet-name>] {<permitted content>}
```

### <a name="do"></a>Wel doen

Wordt gebruikt met `While` het `Until` sleutel woord or als een herhalings constructie. Power Shell voert de instructie lijst ten minste één keer uit, in tegens telling tot een lus die gebruikmaakt van `While` .

Syntaxis voor `While` :

```Syntax
do {<statement list>} while (<condition>)
```

Syntaxis voor `Until` :

```Syntax
do {<statement list>} until (<condition>)
```

### <a name="dynamicparam"></a>DynamicParam

Hiermee wordt een deel van de hoofd tekst van een functie opgegeven, samen met de `Begin` `Process` woorden, en `End` . Dynamische para meters worden toegevoegd tijdens runtime.

Syntaxis:

```Syntax
function <name> {
   DynamicParam {<statement list>}
   begin {<statement list>}
   process {<statement list>}
   end {<statement list>}
}
```

### <a name="else"></a>Hierin

Wordt gebruikt met het `If` sleutel woord om de standaard lijst met instructies op te geven.

Syntaxis:

```Syntax
if (<condition>) {<statement list>}
else {<statement list>}
```

### <a name="elseif"></a>Elseif

Wordt gebruikt met `If` de `Else` tref woorden en om aanvullende voor waarden op te geven. Het `Else` sleutel woord is optioneel.

Syntaxis:

```Syntax
if (<condition>) {<statement list>}
elseif (<condition>) {<statement list>}
else {<statement list>}
```

### <a name="end"></a>Beëindigen

Hiermee wordt een deel van de hoofd tekst van een functie opgegeven, samen met de `DynamicParam` `Begin` woorden, en `End` . De `End` lijst met instructies wordt één keer uitgevoerd nadat alle objecten zijn ontvangen van de pijp lijn.

Syntaxis:

```Syntax
function <name> {
   DynamicParam {<statement list>}
   begin {<statement list>}
   process {<statement list>}
   end {<statement list>}
}
```

### <a name="enum"></a>Enum

`enum` wordt gebruikt voor het declareren van een opsomming; een afzonderlijk type dat bestaat uit een set benoemde labels, de lijst enumerator genoemd.

Syntaxis:

```Syntax
enum <enum-name> {
    <label> [= <int-value>]
    ...
}
```

### <a name="exit"></a>Afsluiten

Hiermee wordt Power shell een script of een Power shell-exemplaar afgesloten.

Syntaxis:

```Syntax
exit
exit <exitcode>
```

Wanneer u gebruikt `powershell.exe` met de **File** -para meter, `.ps1` moet het (script) bestand zelf instructies bevatten voor het verwerken van eventuele fouten of uitzonde ringen die optreden tijdens het uitvoeren van het script. Gebruik de-instructie alleen `exit` om de status na uitvoering van het script aan te geven.

Een wille keurig getal tussen `[int]::MinValue` en `[int]::MaxValue` is toegestaan.

In Power shell `exit` stelt de instructie de waarde van de `$LASTEXITCODE` variabele in. In de Windows-opdracht shell (cmd.exe) wordt met de instructie Exit de waarde van de `%ERRORLEVEL%` omgevings variabele ingesteld.

Elk argument dat niet-numeriek of buiten het platformspecifieke bereik valt, wordt vertaald naar de waarde van `0` .

In het volgende voor beeld stelt de gebruiker de waarde van de variabele fout niveau in op 4 door toe te voegen `exit 4` aan het script bestand `test.ps1` .

```cmd
C:\scripts\test>type test.ps1
1
2
3
exit 4

C:\scripts\test>powershell -file ./test.ps1
1
2
3

C:\scripts\test>echo %ERRORLEVEL%
4
```

Wanneer u uitvoert `pwsh.exe -File <path to a script>` en het script bestand eindigt met een `exit` opdracht, wordt de afsluit code ingesteld op het numerieke argument dat met de opdracht wordt gebruikt `exit` . Als het script geen `exit` instructie heeft, is de afsluit code altijd `0` wanneer het script is voltooid zonder fouten of `1` wanneer het script wordt beëindigd van een onverwerkte uitzonde ring.

### <a name="filter"></a>Filteren

Hiermee geeft u een functie op waarin de overzichts lijst één keer wordt uitgevoerd voor elk invoer object. Dit heeft hetzelfde effect als een functie die alleen een proces blok bevat.

Syntaxis:

```Syntax
filter <name> {<statement list>}
```

### <a name="finally"></a>Werd

Hiermee wordt een lijst met overzichten gedefinieerd die worden uitgevoerd na-instructies die zijn gekoppeld aan try en catch. Een `Finally` overzichts lijst wordt uitgevoerd, zelfs als u op `CTRL+C` een script drukt of als u het sleutel woord exit in het script gebruikt.

Syntaxis:

```Syntax
try {<statement list>}
catch [<error type>] {<statement list>}
finally {<statement list>}
```

### <a name="for"></a>Voor

Definieert een lus met behulp van een voor waarde.

Syntaxis:

```Syntax
for (<initialize>; <condition>; <iterate>) { <statement list> }
```

### <a name="foreach"></a>ForEach

Definieert een lus door elk lid van een verzameling te gebruiken.

Syntaxis:

```Syntax
ForEach (<item> in <collection>) { <statement list> }
```

### <a name="from"></a>Van

Gereserveerd voor toekomstig gebruik.

### <a name="function"></a>Functie

Hiermee maakt u een lijst met benoemde instructies voor herbruikbare code. U kunt de naam van het bereik waarvan een functie deel uitmaakt. En u kunt een of meer benoemde para meters opgeven met behulp van het `Param` sleutel woord. In de lijst functie-instructie kunt u `DynamicParam` lijsten,, en `Begin` `Process` `End` afschriften opnemen.

Syntaxis:

```Syntax
function [<scope:>]<name> {
   param ([type]<$pname1> [, [type]<$pname2>])
   DynamicParam {<statement list>}
   begin {<statement list>}
   process {<statement list>}
   end {<statement list>}
}
```

U kunt ook een of meer para meters definiëren buiten de lijst met instructies na de functie naam.

Syntaxis:

```Syntax
function [<scope:>]<name> [([type]<$pname1>, [[type]<$pname2>])] {
   DynamicParam {<statement list>}
   begin {<statement list>}
   process {<statement list>}
   end {<statement list>}
}
```

### <a name="if"></a>Als

Hiermee definieert u een voorwaardelijke waarde.

Syntaxis:

```Syntax
if (<condition>) {<statement list>}
```

### <a name="hidden"></a>Verborgen

Hiermee worden klasse-leden verborgen in de standaard resultaten van de `Get-Member` cmdlet en uit IntelliSense en de resultaten van het volt ooien van tabbladen.

Syntaxis:

```Syntax
Hidden [data type] $member_name
```

### <a name="in"></a>In

Wordt gebruikt in een `ForEach` instructie om een lus te maken die gebruikmaakt van elk lid van een verzameling.

Syntaxis:

```Syntax
ForEach (<item> in <collection>){<statement list>}
```

### <a name="inlinescript"></a>InlineScript

Voert werk stroom opdrachten uit in een gedeelde Power shell-sessie. Dit sleutel woord is alleen geldig in een Power shell-werk stroom.

Syntaxis:

```Syntax
workflow <verb>-<noun>
{
   InlineScript
   {
      <Command/Expression>
      ...

   }
}
```

Het `InlineScript` sleutel woord geeft een `InlineScript` activiteit aan, waarmee opdrachten worden uitgevoerd in een gedeelde standaard sessie (een niet-werk stroom). U kunt het `InlineScript` sleutel woord gebruiken om opdrachten uit te voeren die niet op een andere manier geldig zijn in een werk stroom en om opdrachten uit te voeren die gegevens delen. Standaard worden de opdrachten in een InlineScript-script blok uitgevoerd in een afzonderlijk proces.

Zie [Power shell-opdrachten uitvoeren in een werk stroom](/previous-versions/windows/it-pro/windows-server-2012-R2-and-2012/jj574197(v=ws.11))voor meer informatie.

### <a name="param"></a>Param

Hiermee worden de para meters in een functie gedefinieerd.

Syntaxis:

```Syntax
function [<scope:>]<name> {
   param ([type]<$pname1>[, [[type]<$pname2>]])
   <statement list>
}
```

### <a name="process"></a>Proces

Hiermee wordt een deel van de hoofd tekst van een functie opgegeven, samen met de `DynamicParam` `Begin` woorden, en `End` . Wanneer een `Process` lijst met overzichten invoer van de pijp lijn ontvangt, `Process` wordt de lijst met overzichten één keer uitgevoerd voor elk element van de pijp lijn. Als de pijp lijn geen objecten bevat, `Process` wordt de lijst met overzichten niet uitgevoerd. Als de opdracht de eerste opdracht in de pijp lijn is, `Process` wordt de lijst met overzichten één keer uitgevoerd.

Syntaxis:

```Syntax
function <name> {
   DynamicParam {<statement list>}
   begin {<statement list>}
   process {<statement list>}
   end {<statement list>}
}
```

### <a name="return"></a>Opvragen

Zorgt ervoor dat Power shell het huidige bereik verlaat, zoals een script of functie en de optionele expressie naar de uitvoer schrijft.

Syntaxis:

```Syntax
return [<expression>]
```

### <a name="static"></a>Statisch

Hiermee geeft u de gedefinieerde eigenschap of methode op die wordt gebruikt voor alle exemplaren van de klasse waarin is gedefinieerd.

Zie `Class` voor voor beelden van gebruik.

### <a name="switch"></a>Switch

Als u meerdere voor waarden wilt controleren, gebruikt u een- `Switch` instructie. De `Switch` instructie is gelijk aan een reeks `If` instructies, maar is eenvoudiger.

De `Switch` instructie vermeldt elke voor waarde en een optionele actie. Als een voor waarde wordt opgehaald, wordt de actie uitgevoerd.

Syntaxis 1:

```Syntax
switch [-regex|-wildcard|-exact][-casesensitive] ( <value> )
{
   <string>|<number>|<variable>|{ <expression> } {<statement list>}
   <string>|<number>|<variable>|{ <expression> } {<statement list>}
   ...

   default {<statement list>}
}
```

Syntaxis 2:

```Syntax
switch [-regex|-wildcard|-exact][-casesensitive] -file <filename>
{
   <string>|<number>|<variable>|{ <expression> } {<statement list>}
   <string>|<number>|<variable>|{ <expression> } {<statement list>}
   ...

   default {<statement list>}
}
```

### <a name="throw"></a>Sprong

Genereert een object als een fout.

Syntaxis:

```Syntax
throw [<object>]
```

### <a name="trap"></a>Overlapping

Hiermee wordt een overzichts lijst gedefinieerd die moet worden uitgevoerd als er een fout optreedt. Een fout type vereist vier Kante haken. Het tweede paar haken geeft aan dat het fout type optioneel is.

Syntaxis:

```Syntax
trap [[<error type>]] {<statement list>}
```

### <a name="try"></a>Proberen

Hiermee wordt een lijst met overzichten gedefinieerd die op fouten moet worden gecontroleerd wanneer de instructies worden uitgevoerd. Als er een fout optreedt, wordt Power shell voortgezet in een- `Catch` of- `Finally` instructie. Een fout type vereist vier Kante haken. Het tweede paar haken geeft aan dat het fout type optioneel is.

Syntaxis:

```Syntax
try {<statement list>}
catch [[<error type>]] {<statement list>}
finally {<statement list>}
```

### <a name="until"></a>Totdat

Wordt gebruikt in een `Do` instructie als een herhalings constructie waarbij de instructie lijst ten minste één keer wordt uitgevoerd.

Syntaxis:

```Syntax
do {<statement list>} until (<condition>)
```

### <a name="using"></a>Gebruiken

Hiermee kunt u aangeven welke naam ruimten in de sessie worden gebruikt. Klassen en leden vereisen minder typen om ze te vermelden. U kunt ook klassen uit modules toevoegen.

Syntaxis #1:

```Syntax
using namespace <.Net-framework-namespace>
```

Syntaxis #2:

```Syntax
using module <module-name>
```

### <a name="while"></a>Het

De `while` instructie is een herhalings constructie waarbij de voor waarde wordt getest voordat de instructies worden uitgevoerd. Als de voor waarde ONWAAR is, worden de instructies niet uitgevoerd.

Instructie syntaxis:

```Syntax
while (<condition>) {
   <statements>
 }
```

Bij gebruik in een `Do` instructie maakt `while` deel uit van een construct constructie waarbij de instructie lijst ten minste één keer wordt uitgevoerd.

Syntaxis van de lus do:

```Syntax
do {<statement list>} while (<condition>)
```

## <a name="see-also"></a>ZIE OOK

- [about_Special_Characters](about_Special_Characters.md)
- [about_Wildcards](about_Wildcards.md)
