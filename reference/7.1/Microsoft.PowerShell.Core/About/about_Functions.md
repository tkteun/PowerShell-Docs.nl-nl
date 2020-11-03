---
description: Hierin wordt beschreven hoe u functies maakt en gebruikt in Power shell.
keywords: powershell,cmdlet
Locale: en-US
ms.date: 2/27/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_functions?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Functions
ms.openlocfilehash: bef1f9f0b672f45c30626a1bbe4f2c6a7dfa540b
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/13/2020
ms.locfileid: "93252951"
---
# <a name="about-functions"></a>Over Functions

## <a name="short-description"></a>Korte beschrijving

Hierin wordt beschreven hoe u functies maakt en gebruikt in Power shell.

## <a name="long-description"></a>Lange beschrijving

Een functie is een lijst met Power shell-instructies die een naam hebben die u toewijst. Wanneer u een functie uitvoert, typt u de naam van de functie. De instructies in de lijst worden uitgevoerd alsof u deze hebt getypt bij de opdracht prompt.

Functions kunnen zo eenvoudig zijn als:

```powershell
function Get-PowerShellProcess { Get-Process PowerShell }
```

Een functie kan ook net zo complex zijn als een cmdlet of een toepassings programma.

Net als-cmdlets kunnen functies para meters hebben. De para meters kunnen de naam, positioneel, switch of dynamische para meters zijn. Functie parameters kunnen worden gelezen vanaf de opdracht regel of vanuit de pijp lijn.

Functies kunnen waarden retour neren die kunnen worden weer gegeven, toegewezen aan variabelen of worden door gegeven aan andere functies of cmdlets. U kunt ook een retour waarde opgeven met behulp van het `return` sleutel woord. Het `return` tref woord heeft geen invloed op of onderdrukt andere uitvoer die is geretourneerd door de functie. Het `return` sleutel woord verlaat echter de functie op die regel. Zie [about_Return](about_Return.md)voor meer informatie.

De instructie lijst van de functie kan verschillende typen instructie lijsten bevatten met de tref woorden `Begin` , `Process` en `End` . Deze instructie geeft een andere ingangs invoer van de pijp lijn.

Een filter is een speciaal soort functie die gebruikmaakt van het `Filter` sleutel woord.

Functies kunnen ook fungeren als-cmdlets. U kunt een functie maken die werkt op dezelfde manier als een cmdlet zonder `C#` Program meren te gebruiken. Zie [about_Functions_Advanced](about_Functions_Advanced.md)voor meer informatie.

## <a name="syntax"></a>Syntax

Hier volgt de syntaxis voor een functie:

```
function [<scope:>]<name> [([type]$parameter1[,[type]$parameter2])]
{
  param([type]$parameter1 [,[type]$parameter2])
  dynamicparam {<statement list>}
  begin {<statement list>}
  process {<statement list>}
  end {<statement list>}
}
```

Een functie omvat de volgende items:

- Een `Function` tref woord
- Een bereik (optioneel)
- Een naam die u selecteert
- Een wille keurig aantal benoemde para meters (optioneel)
- Een of meer Power shell-opdrachten tussen accolades `{}`

Zie about_Functions_Advanced_Parameters voor meer informatie over het `Dynamicparam` tref woord en dynamische para meters in functies. [about_Functions_Advanced_Parameters](about_Functions_Advanced_Parameters.md)

## <a name="simple-functions"></a>Eenvoudige functies

Functies hoeven niet ingewikkeld te zijn om nuttig te zijn. De eenvoudigste functies hebben de volgende indeling:

```
function <function-name> {statements}
```

Met de volgende functie wordt Power shell bijvoorbeeld gestart met de optie als administrator uitvoeren.

```powershell
function Start-PSAdmin {Start-Process PowerShell -Verb RunAs}
```

Als u de functie wilt gebruiken, typt u: `Start-PSAdmin`

Als u instructies wilt toevoegen aan de functie, typt u elke instructie op een aparte regel of gebruikt u een punt komma `;` om de instructies van elkaar te scheiden.

Met de volgende functie vindt u bijvoorbeeld alle `.jpg` bestanden in de mappen van de huidige gebruiker die na de begin datum zijn gewijzigd.

```powershell
function Get-NewPix
{
  $start = Get-Date -Month 1 -Day 1 -Year 2010
  $allpix = Get-ChildItem -Path $env:UserProfile\*.jpg -Recurse
  $allpix | Where-Object {$_.LastWriteTime -gt $Start}
}
```

U kunt een werkset met handige kleine functies maken. Voeg deze functies toe aan uw Power shell-profiel, zoals beschreven in [about_Profiles](about_Profiles.md) en verderop in dit onderwerp.

## <a name="function-names"></a>Functie namen

U kunt een wille keurige naam toewijzen aan een functie, maar functies die u met anderen deelt, moeten voldoen aan de naamgevings regels die tot stand zijn gebracht voor alle Power shell-opdrachten.

De namen van functies moeten bestaan uit een combi natie van woorden en zelfstandig naam woord waarin de bewerking de actie identificeert die de functie uitvoert en het zelfstandig naam woord identificeert het item waarop de cmdlet de actie uitvoert.

Functies moeten de standaard woorden gebruiken die zijn goedgekeurd voor alle Power shell-opdrachten. Met deze termen kunnen we onze opdracht namen eenvoudig, consistent en eenvoudig voor gebruikers begrijpen.

Zie [goedgekeurde werk woorden](/powershell/scripting/developer/cmdlet/approved-verbs-for-windows-powershell-commands) in de Microsoft docs voor meer informatie over de standaard-Power shell-termen.

## <a name="functions-with-parameters"></a>Functies met para meters

U kunt para meters gebruiken met functies, zoals benoemde para meters, positionele para meters, Switch parameters en dynamische para meters. Zie [about_Functions_Advanced_Parameters](about_Functions_Advanced_Parameters.md)voor meer informatie over dynamische para meters in functies.

### <a name="named-parameters"></a>Benoemde para meters

U kunt een wille keurig aantal benoemde para meters definiëren. U kunt een standaard waarde voor benoemde para meters toevoegen, zoals verderop in dit onderwerp wordt beschreven.

U kunt para meters definiëren in de accolades met behulp `Param` van het tref woord, zoals wordt weer gegeven in de volgende voorbeeld syntaxis:

```
function <name> {
  param ([type]$parameter1[,[type]$parameter2])
  <statement list>
}
```

U kunt ook para meters definiëren buiten de accolades zonder het `Param` sleutel woord, zoals wordt weer gegeven in de volgende voorbeeld syntaxis:

```powershell
function <name> [([type]$parameter1[,[type]$parameter2])] {
  <statement list>
}
```

Hieronder ziet u een voor beeld van deze alternatieve syntaxis.

```powershell
Function Add-Numbers($one, $two) {
    $one + $two
}
```

Hoewel de eerste methode de voor keur heeft, is er geen verschil tussen deze twee methoden.

Wanneer u de functie uitvoert, wordt de waarde die u opgeeft voor een para meter toegewezen aan een variabele die de parameter naam bevat. De waarde van die variabele kan worden gebruikt in de functie.

Het volgende voor beeld is een functie met de naam `Get-SmallFiles` . Deze functie heeft een `$Size` para meter. De functie geeft alle bestanden weer die kleiner zijn dan de waarde van de `$Size` para meter en sluit mappen uit:

```powershell
function Get-SmallFiles {
  Param($Size)
  Get-ChildItem $HOME | Where-Object {
    $_.Length -lt $Size -and !$_.PSIsContainer
  }
}
```

In de functie kunt u de variabele gebruiken `$Size` . Dit is de naam die voor de para meter is gedefinieerd.

Als u deze functie wilt gebruiken, typt u de volgende opdracht:

```powershell
Get-SmallFiles -Size 50
```

U kunt ook een waarde opgeven voor een benoemde para meter zonder de parameter naam.
De volgende opdracht geeft bijvoorbeeld hetzelfde resultaat als een opdracht die de **grootte** parameter benoemt:

```powershell
Get-SmallFiles 50
```

Als u een standaard waarde voor een para meter wilt definiëren, typt u een gelijkteken en de waarde na de parameter naam, zoals wordt weer gegeven in de volgende variant van het `Get-SmallFiles` voor beeld:

```powershell
function Get-SmallFiles ($Size = 100) {
  Get-ChildItem $HOME | Where-Object {
    $_.Length -lt $Size -and !$_.PSIsContainer
  }
}
```

Als u `Get-SmallFiles` zonder waarde typt, wijst de functie 100 toe aan `$size` . Als u een waarde opgeeft, gebruikt de functie die waarde.

U kunt desgewenst een korte Help-teken reeks opgeven die de standaard waarde van uw para meter beschrijft door het kenmerk **PSDefaultValue** toe te voegen aan de beschrijving van de para meter en de eigenschap **Help** van **PSDefaultValue** op te geven. Als u een Help-teken reeks wilt opgeven die de standaard waarde (100) van de para meter **Size** in de `Get-SmallFiles` functie beschrijft, voegt u het kenmerk **PSDefaultValue** toe, zoals in het volgende voor beeld wordt weer gegeven.

```powershell
function Get-SmallFiles {
  param (
      [PSDefaultValue(Help = '100')]
      $Size = 100
  )
}
```

Zie [PSDefaultValue kenmerk members](/dotnet/api/system.management.automation.psdefaultvalueattribute)(Engelstalig) voor meer informatie over de kenmerk klasse **PSDefaultValue** .

### <a name="positional-parameters"></a>Positionele para meters

Een positionele para meter is een para meter zonder parameter naam. Power shell gebruikt de volg orde van de parameter waarde om elke parameter waarde te koppelen aan een para meter in de functie.

Wanneer u positionele para meters gebruikt, typt u een of meer waarden achter de functie naam. Positionele parameter waarden worden toegewezen aan de `$args` matrix variabele.
De waarde die volgt op de naam van de functie wordt toegewezen aan de eerste positie in de `$args` matrix `$args[0]` .

Met de volgende `Get-Extension` functie wordt de `.txt` bestandsnaam extensie toegevoegd aan een bestands naam die u opgeeft:

```powershell
function Get-Extension {
  $name = $args[0] + ".txt"
  $name
}
```

```powershell
Get-Extension myTextFile
```

```Output
myTextFile.txt
```

### <a name="switch-parameters"></a>Switch parameters

Een schakel optie is een para meter waarvoor geen waarde is vereist. In plaats daarvan typt u de naam van de functie, gevolgd door de naam van de para meter switch.

Als u een para meter switch wilt definiëren, geeft u het type `[switch]` voor de parameter naam op, zoals in het volgende voor beeld wordt weer gegeven:

```powershell
function Switch-Item {
  param ([switch]$on)
  if ($on) { "Switch on" }
  else { "Switch off" }
}
```

Wanneer u de `On` para meter switch na de functie naam typt, wordt de functie ' activeren op ' weer gegeven. Zonder de para meter switch wordt ' switch uitgeschakeld ' weer gegeven.

```powershell
Switch-Item -on
```

```Output
Switch on
```

```powershell
Switch-Item
```

```Output
Switch off
```

U kunt ook een **Booleaanse** waarde toewijzen aan een switch wanneer u de functie uitvoert, zoals wordt weer gegeven in het volgende voor beeld:

```powershell
Switch-Item -on:$true
```

```Output
Switch on
```

```powershell
Switch-Item -on:$false
```

```Output
Switch off
```

## <a name="using-splatting-to-represent-command-parameters"></a>Splatting gebruiken om opdracht parameters weer te geven

U kunt splatting gebruiken om de para meters van een opdracht weer te geven. Deze functie is geïntroduceerd in Windows Power Shell 3,0.

Gebruik deze techniek in functies die opdrachten in de sessie aanroepen. U hoeft de opdracht parameters niet te declareren of te inventariseren, of u kunt de functie wijzigen als de opdracht parameter wordt gewijzigd.

Met de volgende voorbeeld functie wordt de `Get-Command` cmdlet aangeroepen. De opdracht wordt gebruikt `@Args` om de para meters van te vertegenwoordigen `Get-Command` .

```powershell
function Get-MyCommand { Get-Command @Args }
```

U kunt alle para meters van gebruiken `Get-Command` Wanneer u de functie aanroept `Get-MyCommand` . De para meters en parameter waarden worden door gegeven aan de opdracht met `@Args` .

```powershell
Get-MyCommand -Name Get-ChildItem
```

```Output
CommandType     Name                ModuleName
-----------     ----                ----------
Cmdlet          Get-ChildItem       Microsoft.PowerShell.Management
```

De `@Args` functie maakt gebruik `$Args` van de automatische para meter, die niet-gedeclareerde cmdlet-para meters en waarden van de resterende argumenten vertegenwoordigt.

Zie [about_Splatting](about_Splatting.md)voor meer informatie over splatting.

## <a name="piping-objects-to-functions"></a>Pijpleiding objecten naar functions

Elke functie kan invoer uit de pijp lijn nemen. U kunt bepalen hoe een functie invoer van de pijp lijn verwerkt met `Begin` , `Process` en `End` sleutel woorden. Met de volgende voorbeeld syntaxis worden de drie tref woorden weer gegeven:

```
function <name> {
  begin {<statement list>}
  process {<statement list>}
  end {<statement list>}
}
```

De `Begin` lijst met overzichten wordt slechts één keer uitgevoerd, aan het begin van de functie.

> [!IMPORTANT]
> Als uw functie een `Begin` , `Process` of `End` blok, definieert, moet al uw code zich in die blokken bevinden. Als *een* van de blokken is gedefinieerd, wordt er geen code buiten de blokken herkend.

De `Process` lijst met overzichten wordt één keer uitgevoerd voor elk object in de pijp lijn.
Terwijl het `Process` blok wordt uitgevoerd, wordt elk pijplijn object toegewezen aan de `$_` Automatische variabele, één pijplijn object tegelijk.

Nadat de functie alle objecten in de pijp lijn heeft ontvangen, `End` wordt de lijst met overzichten één keer uitgevoerd. Als Nee `Begin` , `Process` of als `End` tref woorden worden gebruikt, worden alle instructies behandeld, zoals een `End` lijst met overzichten.

De volgende functie maakt gebruik van het `Process` sleutel woord. De functie geeft voor beelden uit de pijp lijn weer:

```powershell
function Get-Pipeline
{
  process {"The value is: $_"}
}
```

Als u deze functie wilt demonstreren, geeft u een lijst met getallen op, gescheiden door komma's, zoals wordt weer gegeven in het volgende voor beeld:

```powershell
1,2,4 | Get-Pipeline
```

```Output
The value is: 1
The value is: 2
The value is: 4
```

Wanneer u een functie in een pijp lijn gebruikt, worden de objecten die naar de functie worden geleid, toegewezen aan de `$input` Automatische variabele. De functie voert instructies uit met het `Begin` sleutel woord voordat er objecten uit de pijp lijn worden opgehaald. De functie voert instructies uit met het `End` sleutel woord nadat alle objecten zijn ontvangen van de pijp lijn.

In het volgende voor beeld wordt de `$input` Automatische variabele met `Begin` en `End` tref woorden weer gegeven.

```powershell
function Get-PipelineBeginEnd
{
  begin {"Begin: The input is $input"}
  end {"End:   The input is $input" }
}
```

Als deze functie wordt uitgevoerd met behulp van de pijp lijn, worden de volgende resultaten weer gegeven:

```powershell
1,2,4 | Get-PipelineBeginEnd
```

```Output
Begin: The input is
End:   The input is 1 2 4
```

Wanneer de `Begin` instructie wordt uitgevoerd, heeft de functie niet de invoer van de pijp lijn. De `End` instructie wordt uitgevoerd nadat de functie de waarden heeft.

Als de functie een `Process` tref woord heeft, wordt elk object in `$input` verwijderd uit `$input` en toegewezen aan `$_` . In het volgende voor beeld wordt een `Process` instructie lijst weer geven:

```powershell
function Get-PipelineInput
{
  process {"Processing:  $_ " }
  end {"End:   The input is: $input" }
}
```

In dit voor beeld wordt elk object dat naar de functie is gesluisd, verzonden naar de `Process` lijst met instructies. De `Process` instructies worden op elk object uitgevoerd, één object per keer. De `$input` Automatische variabele is leeg wanneer de functie het `End` tref woord bereikt.

```powershell
1,2,4 | Get-PipelineInput
```

```Output
Processing:  1
Processing:  2
Processing:  4
End:   The input is:
```

Zie [using enumeraties](about_Automatic_Variables.md#using-enumerators) voor meer informatie.

## <a name="filters"></a>Filters

Een filter is een type functie dat wordt uitgevoerd op elk object in de pijp lijn. Een filter lijkt op een functie met alle instructies in een `Process` blok.

De syntaxis van een filter is als volgt:

```
filter [<scope:>]<name> {<statement list>}
```

Het volgende filter neemt logboek vermeldingen van de pijp lijn en vervolgens wordt het hele item of alleen het bericht gedeelte van de vermelding weer gegeven:

```powershell
filter Get-ErrorLog ([switch]$message)
{
  if ($message) { Out-Host -InputObject $_.Message }
  else { $_ }
}
```

## <a name="function-scope"></a>Functie bereik

Een functie bestaat in het bereik waarin deze is gemaakt.

Als een functie deel uitmaakt van een script, is de functie beschikbaar voor instructies binnen dat script. Een functie in een script is standaard niet beschikbaar op de opdracht regel.

U kunt het bereik van een functie opgeven. De functie wordt bijvoorbeeld toegevoegd aan het globale bereik in het volgende voor beeld:

```powershell
function global:Get-DependentSvs {
  Get-Service | Where-Object {$_.DependentServices}
}
```

Wanneer een functie zich in het globale bereik bevindt, kunt u de functie gebruiken in scripts, in functies en op de opdracht regel.

Functions maken normaal een bereik. De items die zijn gemaakt in een functie, zoals variabelen, bestaan alleen in het functie bereik.

Zie [about_Scopes](about_Scopes.md)voor meer informatie over het bereik in Power shell.

## <a name="finding-and-managing-functions-using-the-function-drive"></a>Functies zoeken en beheren met behulp van de functie: station

Alle functies en filters in Power shell worden automatisch opgeslagen in het `Function:` station. Dit station wordt weer gegeven door de Power shell- **functie** provider.

Wanneer u verwijst naar het `Function:` station, typt u een dubbele punt na **functie** , net zoals u zou doen bij het verwijzen naar de `C` of het `D` station van een computer.

Met de volgende opdracht worden alle functies in de huidige sessie van Power shell weer gegeven:

```powershell
Get-ChildItem function:
```

De opdrachten in de functie worden opgeslagen als een script blok in de eigenschap definitie van de functie. Als u bijvoorbeeld de opdrachten wilt weer geven in de Help-functie die wordt geleverd met Power shell, typt u:

```powershell
(Get-ChildItem function:help).Definition
```

U kunt ook de volgende syntaxis gebruiken.

```powershell
$function:help
```

`Function:`Zie het Help-onderwerp voor de **functie** provider voor meer informatie over het station. Typ `Get-Help Function`.

## <a name="reusing-functions-in-new-sessions"></a>Functies opnieuw gebruiken in nieuwe sessies

Wanneer u een functie typt bij de Power shell-opdracht prompt, wordt de functie onderdeel van de huidige sessie. Het is beschikbaar totdat de sessie is beëindigd.

Als u de functie in alle Power shell-sessies wilt gebruiken, voegt u de functie toe aan uw Power shell-profiel. Zie [about_Profiles](about_Profiles.md)voor meer informatie over profielen.

U kunt de functie ook opslaan in een Power shell-script bestand. Typ uw functie in een tekst bestand en sla het bestand op met de `.ps1` bestandsnaam extensie.

## <a name="writing-help-for-functions"></a>Help-informatie over functies schrijven

De `Get-Help` cmdlet krijgt hulp bij functies, evenals voor cmdlets, providers en scripts. Als u hulp wilt krijgen voor een functie, typt u `Get-Help` gevolgd door de naam van de functie.

Als u bijvoorbeeld hulp voor de functie wilt weer geven `Get-MyDisks` , typt u:

```powershell
Get-Help Get-MyDisks
```

U kunt op een van de volgende twee manieren hulp voor een functie schrijven:

- Help voor functies Comment-Based

  Maak een Help-onderwerp met behulp van speciale tref woorden in de opmerkingen. Als u op opmerkingen gebaseerde hulp voor een functie wilt maken, moeten de opmerkingen aan het begin of einde van de hoofd tekst van de functie of op de regels vóór het gereserveerde woord function worden geplaatst. Zie [about_Comment_Based_Help](about_Comment_Based_Help.md)voor meer informatie over op opmerkingen gebaseerde Help.

- Help voor functies XML-Based

  Maak een Help-onderwerp op basis van XML, zoals het type dat doorgaans voor cmdlets wordt gemaakt. Help op basis van XML is vereist als u Help-onderwerpen in meerdere talen onderlokaliseert.

  Als u de functie wilt koppelen aan het Help-onderwerp met XML, gebruikt u het `.ExternalHelp` tref woord Help op basis van opmerkingen. Zonder dit sleutel woord `Get-Help` kan het Help-onderwerp van de functie niet worden gevonden en wordt aanroepen naar `Get-Help` voor de functie retourneert alleen automatisch gegenereerde Help.

  Zie about_Comment_Based_Help voor meer informatie over het `ExternalHelp` tref [about_Comment_Based_Help](about_Comment_Based_Help.md)woord. Zie [instructies voor het schrijven van cmdlets](https://go.microsoft.com/fwlink/?LinkID=123415) in de MSDN-bibliotheek voor meer informatie over Help op basis van XML.

## <a name="see-also"></a>Zie ook

[about_Automatic_Variables](about_Automatic_Variables.md)

[about_Comment_Based_Help](about_Comment_Based_Help.md)

[about_Functions_Advanced](about_Functions_Advanced.md)

[about_Functions_Advanced_Methods](about_Functions_Advanced_Methods.md)

[about_Functions_Advanced_Parameters](about_Functions_Advanced_Parameters.md)

[about_Functions_CmdletBindingAttribute](about_Functions_CmdletBindingAttribute.md)

[about_Functions_OutputTypeAttribute](about_Functions_OutputTypeAttribute.md)

[about_Parameters](about_Parameters.md)

[about_Profiles](about_Profiles.md)

[about_Scopes](about_Scopes.md)

[about_Script_Blocks](about_Script_Blocks.md)

[about_Function_provider](about_Function_provider.md)

