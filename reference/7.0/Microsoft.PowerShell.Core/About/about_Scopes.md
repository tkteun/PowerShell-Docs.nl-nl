---
description: Hierin wordt het concept van de scope in Power shell beschreven en wordt getoond hoe u het bereik van elementen kunt instellen en wijzigen.
keywords: powershell,cmdlet
Locale: en-US
ms.date: 03/13/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_scopes?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_scopes
ms.openlocfilehash: 2149a1dec14e4de9c6ff1021e98689ca93307cb8
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/13/2020
ms.locfileid: "93252083"
---
# <a name="about-scopes"></a>Over bereiken

## <a name="short-description"></a>Korte beschrijving
Hierin wordt het concept van de scope in Power shell beschreven en wordt getoond hoe u het bereik van elementen kunt instellen en wijzigen.

## <a name="long-description"></a>Lange beschrijving

Power shell beveiligt de toegang tot variabelen, aliassen, functies en Power Shell-stations (PSDrives) door te beperken waar ze kunnen worden gelezen en gewijzigd. In Power shell worden scope regels gebruikt om ervoor te zorgen dat u niet per ongeluk een item wijzigt dat niet mag worden gewijzigd.

Hier volgen de basis regels voor het bereik:

- Bereiken kunnen worden genest. Een buitenste bereik wordt een bovenliggend bereik genoemd. Alle geneste bereiken zijn onderliggende bereiken van het bovenliggende bereik.

- Een item is zichtbaar in het bereik waarin het is gemaakt en in een onderliggend bereik, tenzij u het expliciet persoonlijk maakt. U kunt variabelen, aliassen, functies of Power Shell-stations in een of meer scopes plaatsen.

- Een item dat u in een bereik hebt gemaakt, kan alleen worden gewijzigd in het bereik waarin het is gemaakt, tenzij u expliciet een ander bereik opgeeft.

Als u een item in een bereik maakt en de naam van het item is gedeeld met een item in een ander bereik, wordt het oorspronkelijke item mogelijk verborgen onder het nieuwe item, maar wordt het niet overschreven of gewijzigd.

## <a name="powershell-scopes"></a>Power shell-bereiken

Power shell ondersteunt de volgende bereiken:

- Global: de scope die van toepassing is wanneer Power shell wordt gestart. Variabelen en functies die aanwezig zijn wanneer Power shell wordt gestart, zijn gemaakt in het globale bereik, zoals automatische variabelen en voorkeurs variabelen. De variabelen, aliassen en functies in uw Power shell-profielen worden ook in het globale bereik gemaakt.

- Lokaal: het huidige bereik. Het lokale bereik kan het globale bereik of een ander bereik zijn.

- Script: het bereik dat is gemaakt tijdens het uitvoeren van een script bestand. Alleen de opdrachten in het script worden uitgevoerd in het bereik van het script. Met de opdrachten in een script is het bereik van het script het lokale bereik.

> [!NOTE]
> **Privé** is geen bereik. Het is een [optie](#private-option) waarmee de zicht baarheid van een item buiten het bereik waarin het item is gedefinieerd, wordt gewijzigd.

## <a name="parent-and-child-scopes"></a>Bovenliggende en onderliggende bereiken

U kunt een nieuwe scope maken door een script of functie uit te voeren door een sessie te maken of door een nieuw exemplaar van Power shell te starten. Wanneer u een nieuwe scope maakt, is het resultaat een bovenliggend bereik (het oorspronkelijke bereik) en een onderliggend bereik (het bereik dat u hebt gemaakt).

In Power shell zijn alle bereiken onderliggende bereiken van het globale bereik, maar u kunt een groot aantal bereiken maken en veel recursieve bereiken.

Tenzij u de items expliciet aanmaakt, zijn de items in het bovenliggende bereik beschikbaar voor het onderliggende bereik. Items die u in het onderliggende bereik maakt en wijzigt, hebben echter geen invloed op het bovenliggende bereik, tenzij u expliciet het bereik opgeeft wanneer u de items maakt.

## <a name="inheritance"></a>Overname

Een onderliggend bereik neemt de variabelen, aliassen en functies niet over van het bovenliggende bereik. Tenzij een item privé is, kan het onderliggende bereik de items in het bovenliggende bereik weer geven. En de items kunnen worden gewijzigd door expliciet het bovenliggende bereik op te geven, maar de items maken geen deel uit van het onderliggende bereik.

Een onderliggend bereik wordt echter gemaakt met een set items. Normaal gesp roken bevat het alle aliassen met de optie **AllScope** . Deze optie wordt verderop in dit artikel besproken. Het bevat alle variabelen met de optie **AllScope** , plus enkele automatische variabelen.

Als u de items in een bepaald bereik wilt zoeken, gebruikt u de para meter bereik van `Get-Variable` of `Get-Alias` .

Als u bijvoorbeeld alle variabelen in het lokale bereik wilt ophalen, typt u:

```powershell
Get-Variable -Scope local
```

Als u alle variabelen in het globale bereik wilt ophalen, typt u:

```powershell
Get-Variable -Scope global
```

## <a name="scope-modifiers"></a>Bereik aanpassingen

Een variabele-, alias-of functie naam kan een van de volgende optionele Scope-para meters bevatten:

- `global:` -Geeft aan dat de naam bestaat in het **globale** bereik.
- `local:` -Geeft aan dat de naam bestaat in het **lokale** bereik. Het huidige bereik is altijd het **lokale** bereik.
- `private:` -Geeft aan dat de naam **privé** is en alleen zichtbaar is voor de huidige scope.
- `script:` -Geeft aan dat de naam in het **script** bereik bestaat.
  Het bereik van het **script** is het bereik van het dichtstbijzijnde bovenliggende script bestand of **globaal** als er zich geen dichtstbijgelegen bovenliggend script bestand bevindt.
- `using:` : Wordt gebruikt voor toegang tot variabelen die in een ander bereik zijn gedefinieerd tijdens het uitvoeren van scripts via cmdlets zoals `Start-Job` en `Invoke-Command` .
- `workflow:` -Geeft aan dat de naam bestaat in een werk stroom. Opmerking: werk stromen worden niet ondersteund in Power shell core.
- `<variable-namespace>` -Een wijzigings functie die is gemaakt door een Power shell PSDrive-provider.
  Bijvoorbeeld:

  |  Naamruimte  |                    Beschrijving                     |
  | ----------- | -------------------------------------------------- |
  | `Alias:`    | Aliassen die in het huidige bereik zijn gedefinieerd               |
  | `Env:`      | Omgevings variabelen die zijn gedefinieerd in het huidige bereik |
  | `Function:` | Functies die zijn gedefinieerd in het huidige bereik             |
  | `Variable:` | Variabelen die zijn gedefinieerd in het huidige bereik             |

Het standaard bereik voor scripts is het script bereik. Het standaard bereik voor functies en aliassen is het lokale bereik, zelfs als ze in een script zijn gedefinieerd.

### <a name="using-scope-modifiers"></a>Bereik aanpassingen gebruiken

Als u het bereik van een nieuwe variabele, alias of functie wilt opgeven, gebruikt u een bereik aanpassing.

De syntaxis voor een bereik wijzigings functie in een variabele is:

```
$[<scope-modifier>:]<name> = <value>
```

De syntaxis voor een bereik aanpassing in een functie is:

```
function [<scope-modifier>:]<name> {<function-body>}
```

Met de volgende opdracht, waarbij geen bereik wijziging wordt gebruikt, maakt een variabele in het huidige of **lokale** bereik:

```powershell
$a = "one"
```

Als u dezelfde variabele wilt maken in het **globale** bereik, gebruikt u de `global:` aanpassings functie voor het bereik:

```powershell
$global:a = "one"
```

Als u dezelfde variabele in het **script** bereik wilt maken, gebruikt u de `script:` aanpassings functie voor het bereik:

```powershell
$script:a = "one"
```

U kunt ook een bereik wijzigings functie met functies gebruiken. Met de volgende functie definitie maakt u een functie in het **globale** bereik:

```powershell
function global:Hello {
  Write-Host "Hello, World"
}
```

U kunt ook bereik aanpassingen gebruiken om te verwijzen naar een variabele in een ander bereik.
De volgende opdracht verwijst naar de `$test` variabele, eerst in het lokale bereik en vervolgens in het globale bereik:

```powershell
$test
$global:test
```

### <a name="the-using-scope-modifier"></a>De `Using:` aanpassing van het bereik

Met is een speciale Scope wijzigings functie waarmee een lokale variabele wordt aangeduid in een externe opdracht. Zonder een wijzigings programma verwacht Power shell variabelen in externe opdrachten die in de externe sessie moeten worden gedefinieerd.

De `Using` aanpassing van het bereik is geïntroduceerd in Power shell 3,0.

Voor elk script of elke opdracht die uit de sessie wordt uitgevoerd, hebt u de `Using` bereik wijzigings functie nodig om variabele waarden van het aanroepende sessie bereik in te sluiten, zodat out of Session-code er toegang toe heeft. De `Using` aanpassing van het bereik wordt ondersteund in de volgende contexten:

- Extern uitgevoerde opdrachten, begonnen met `Invoke-Command` het gebruik van **ComputerName** , **hostname** , **SSHConnection** of **Session** para meters (externe sessie)
- Achtergrond taken, begonnen met `Start-Job` (out-of-process-sessie)
- Thread taken, gestart via `Start-ThreadJob` of `ForEach-Object -Parallel` (afzonderlijke thread sessie)

Afhankelijk van de context, zijn Inge sloten variabelen waarden ofwel onafhankelijke kopieën van de gegevens in het bereik of verwijzingen naar de aanroeper. In externe en out-of-process-sessies zijn ze altijd onafhankelijke kopieën.

Zie [about_Remote_Variables](about_Remote_Variables.md)voor meer informatie.

In thread sessies worden ze door gegeven door verwijzing. Dit betekent dat het mogelijk is om de variabelen voor het aanroep bereik te wijzigen in een andere thread. Voor het veilig wijzigen van variabelen is thread synchronisatie vereist.

Zie voor meer informatie:

- [Start-ThreadJob](xref:ThreadJob.Start-ThreadJob)
- [ForEach-object](xref:Microsoft.PowerShell.Core.ForEach-Object)

#### <a name="serialization-of-variable-values"></a>Serialisatie van variabele waarden

Extern uitgevoerde opdrachten en achtergrond taken worden out-of-process uitgevoerd.
Out-of-process-sessies gebruiken op XML gebaseerde serialisatie en deserialisatie om de waarden van variabelen beschikbaar te maken voor de grenzen van het proces. Het serialization-proces converteert objecten naar een **PSObject** die de eigenschappen van de oorspronkelijke objecten bevat, maar niet de methoden ervan.

Voor een beperkte set typen worden objecten door deserialisatie opnieuw naar het oorspronkelijke type gehydrateerd. Het opnieuw gehydrateerde object is een kopie van het oorspronkelijke object exemplaar.
Deze bevat de type-eigenschappen en-methoden. Voor eenvoudige typen, zoals **System. versie** , is de kopie gelijk. Voor complexe typen is de kopie niet perfect. Bijvoorbeeld: opnieuw gehydrateerde certificaat objecten bevatten niet de persoonlijke sleutel.

Exemplaren van alle andere typen zijn **PSObject** -exemplaren. De eigenschap **PSTypeNames** bevat de oorspronkelijke type naam, voorafgegaan door een **gedeserialiseerd** , bijvoorbeeld **Deserialized.System. Data. DataTable**

### <a name="the-allscope-option"></a>De optie AllScope

Variabelen en aliassen hebben een **optie** -eigenschap die een waarde van **AllScope** kan hebben. Items met de eigenschap **AllScope** worden deel van alle onderliggende bereiken die u maakt, hoewel ze niet met terugwerkende kracht worden overgenomen door bovenliggende bereiken.

Een item met de eigenschap **AllScope** is zichtbaar in het onderliggende bereik en maakt deel uit van dat bereik. Wijzigingen in het item in elk bereik zijn van invloed op alle bereiken waarin de variabele is gedefinieerd.

### <a name="managing-scope"></a>Bereik beheren

Verschillende cmdlets hebben een **bereik** parameter waarmee u items in een bepaald bereik kunt ophalen of instellen (maken en wijzigen). Gebruik de volgende opdracht om te zoeken naar alle cmdlets in uw sessie met een **bereik** parameter:

```powershell
Get-Help * -Parameter scope
```

Als u de variabelen wilt vinden die zichtbaar zijn in een bepaald bereik, gebruikt u de `Scope` para meter van `Get-Variable` . De zicht bare variabelen bevatten globale variabelen, variabelen in het bovenliggende bereik en variabelen in het huidige bereik.

Met de volgende opdracht worden bijvoorbeeld de variabelen opgehaald die zichtbaar zijn in het lokale bereik:

```powershell
Get-Variable -Scope local
```

Als u een variabele in een bepaald bereik wilt maken, gebruikt u een bereik wijzigings functie of de **bereik** parameter van `Set-Variable` . Met de volgende opdracht maakt u een variabele in het globale bereik:

```powershell
New-Variable -Scope global -Name a -Value "One"
```

U kunt ook de bereik parameter van de `New-Alias` -, `Set-Alias` -of- `Get-Alias` cmdlets gebruiken om het bereik op te geven. Met de volgende opdracht maakt u een alias in het globale bereik:

```powershell
New-Alias -Scope global -Name np -Value Notepad.exe
```

Als u de functies in een bepaald bereik wilt ophalen, gebruikt `Get-Item` u de cmdlet als u zich in het bereik bevindt. De `Get-Item` cmdlet heeft geen **bereik** parameter.

> [!NOTE]
> Voor de cmdlets die gebruikmaken van de **bereik** parameter, kunt u ook bereiken op aantal. Met het nummer wordt de relatieve positie van het ene bereik naar het andere bepaald. Scope 0 staat voor het huidige of lokale bereik. Scope 1 geeft het directe bovenliggende bereik aan. Scope 2 geeft het bovenliggende bereik aan, enzovoort. Genummerde bereiken zijn handig als u veel recursieve bereiken hebt gemaakt.

### <a name="using-dot-source-notation-with-scope"></a>Punt bron notatie met bereik gebruiken

Scripts en functies volgen alle regels van het bereik. U maakt ze in een bepaald bereik en zijn alleen van invloed op dat bereik, tenzij u een cmdlet-para meter of een bereik aanpassings functie gebruikt om dat bereik te wijzigen.

Maar u kunt een script of functie aan het huidige bereik toevoegen met behulp van de punt-bron notatie. Wanneer een script wordt uitgevoerd in het huidige bereik, worden alle functies, aliassen en variabelen die het script maakt, beschikbaar in het huidige bereik.

Als u een functie wilt toevoegen aan het huidige bereik, typt u een punt (.) en een spatie vóór het pad en de naam van de functie in de functie aanroep.

Als u bijvoorbeeld het Sample.ps1 script uit de directory C:\Scripts in het script bereik (de standaard waarde voor scripts) wilt uitvoeren, gebruikt u de volgende opdracht:

```powershell
c:\scripts\sample.ps1
```

Als u het Sample.ps1 script in het lokale bereik wilt uitvoeren, gebruikt u de volgende opdracht:

```powershell
. c:\scripts.sample.ps1
```

Wanneer u de aanroep operator (&) gebruikt om een functie of script uit te voeren, wordt deze niet toegevoegd aan het huidige bereik. In het volgende voor beeld wordt de aanroep operator gebruikt:

```powershell
& c:\scripts.sample.ps1
```

Meer informatie over de aanroep operator vindt u in [about_operators](about_operators.md).

Aliassen, functies of variabelen die het Sample.ps1 script maakt, zijn niet beschikbaar in het huidige bereik.

## <a name="restricting-without-scope"></a>Beperken zonder bereik

Enkele Power shell-concepten zijn vergelijkbaar met de reik wijdte of interactie met het bereik. Deze concepten kunnen worden verward met het bereik of het gedrag van het bereik.

Sessies, modules en geneste prompts zijn op zichzelf staande omgevingen, maar ze zijn geen onderliggende bereiken van het globale bereik in de sessie.

### <a name="sessions"></a>Sessies

Een sessie is een omgeving waarin Power shell wordt uitgevoerd. Wanneer u een sessie op een externe computer maakt, brengt Power shell een permanente verbinding met de externe computer tot stand. Met de permanente verbinding kunt u de sessie voor meerdere gerelateerde opdrachten gebruiken.

Omdat een sessie een opgenomen omgeving is, heeft deze een eigen bereik, maar een sessie is geen onderliggend bereik van de sessie waarin deze is gemaakt. De sessie begint met een eigen globaal bereik. Deze scope is onafhankelijk van het globale bereik van de sessie. U kunt onderliggende bereiken maken in de sessie. U kunt bijvoorbeeld een script uitvoeren om een onderliggend bereik in een sessie te maken.

### <a name="modules"></a>Modules

U kunt een Power shell-module gebruiken om Power shell-hulpprogram ma's te delen en te leveren. Een module is een eenheid die cmdlets, scripts, functies, variabelen, aliassen en andere nuttige items kan bevatten. Tenzij expliciet gedefinieerd, zijn de items in een module niet toegankelijk buiten de module. Daarom kunt u de module toevoegen aan uw sessie en de open bare items gebruiken zonder dat u zich zorgen hoeft te maken dat de andere items de cmdlets, scripts, functies en andere items in uw sessie kunnen overschrijven.

Standaard worden modules geladen in het hoogste niveau van de huidige _sessie status_ niet van de huidige _Scope_. De huidige sessie status kan een module sessie status of de status van de globale sessie zijn. Wanneer een module aan een sessie wordt toegevoegd, wordt het bereik niet gewijzigd. Als u zich in het globale bereik bevindt, worden modules geladen in de globale sessie status. Eventuele exports worden in de globale tabellen geplaatst.
Als u Module2 laadt _vanuit Module1,_ wordt Module2 in de sessie status van Module1 geladen en niet de globale sessie status. Exports van Module2 worden boven aan de Module1-sessie status geplaatst. Als u gebruikt `Import-Module -Scope local` , worden de exports in het huidige bereik object geplaatst in plaats van op het hoogste niveau. Als u zich _in een module_ bevindt en gebruikt `Import-Module -Scope global` (of `Import-Module -Global` ) om een andere module te laden, worden die module en de export bewerkingen geladen in de status van de globale sessie in plaats van de lokale sessie status van de module. Deze functie is ontworpen voor het schrijven van module voor het bewerken van modules. In de **WindowsCompatibility** -module worden proxy modules in de globale sessie status geïmporteerd.

Binnen de sessie status hebben modules hun eigen bereik. Bekijk de volgende module `C:\temp\mod1.psm1` :

```powershell
$a = "Hello"

function foo {
    "`$a = $a"
    "`$global:a = $global:a"
}
```

Nu maakt u een globale variabele `$a` , geeft u deze een waarde en roept u de functie **Foo** aan.

```powershell
$a = "Goodbye"
foo
```

De module declareert de variabele `$a` in het module bereik en de functie **Foo** voert de waarde van de variabele in beide bereiken uit.

```Output
$a = Hello
$global:a = Goodbye
```

### <a name="nested-prompts"></a>Geneste prompts

Geneste prompts hebben geen eigen bereik. Wanneer u een geneste prompt invoert, is de geneste prompt een subset van de omgeving. Maar u blijft binnen het lokale bereik.

Scripts hebben hun eigen bereik. Als u fouten opspoort in een script en u een onderbrekings punt in het script bereikt, voert u het script bereik in.

### <a name="private-option"></a>Privé-optie

Aliassen en variabelen hebben een **optie** -eigenschap die de waarde **privé** kan uitvoeren. Items met de optie **privé** kunnen worden weer gegeven en gewijzigd in het bereik waarin ze zijn gemaakt, maar ze kunnen niet worden weer gegeven of gewijzigd buiten dat bereik.

Als u bijvoorbeeld een variabele maakt met de optie privé in het globale bereik en vervolgens een script uitvoert, wordt `Get-Variable` de persoonlijke variabele niet weer gegeven in opdrachten in het script. Als u de para meter voor globaal bereik in dit exemplaar gebruikt, wordt de persoonlijke variabele niet weer gegeven.

U kunt de optie para meter van de `New-Variable` `Set-Variable` `New-Alias` cmdlets,, en gebruiken `Set-Alias` om de waarde van de eigenschap Option in te stellen op persoonlijk.

### <a name="visibility"></a>Zicht

De **zichtbaarheids** eigenschap van een variabele of alias bepaalt of u het item buiten de container kunt zien waarin het is gemaakt. Een container kan een module, script of module zijn. Zicht baarheid is ontworpen voor containers op dezelfde manier als de **privé** waarde van de eigenschap **Option** is ontworpen voor scopes.

De **zichtbaarheids** eigenschap heeft de **open bare** en **persoonlijke** waarden. Items met een persoonlijke zicht baarheid kunnen alleen worden weer gegeven en gewijzigd in de container waarin ze zijn gemaakt. Als de container wordt toegevoegd of geïmporteerd, kunnen de items met een persoonlijke zicht baarheid niet worden weer gegeven of gewijzigd.

Omdat de zicht baarheid is ontworpen voor containers, werkt deze anders in een bereik.

- Als u een item maakt dat een persoonlijke zicht baarheid heeft in het globale bereik, kunt u het item in geen enkel bereik weer geven of wijzigen.
- Als u de waarde van een variabele met persoonlijke zicht baarheid probeert weer te geven of te wijzigen, retourneert Power shell een fout bericht.

U kunt de `New-Variable` `Set-Variable` cmdlets en gebruiken om een variabele met persoonlijke zicht baarheid te maken.

## <a name="examples"></a>Voorbeelden

### <a name="example-1-change-a-variable-value-only-in-a-script"></a>Voor beeld 1: een variabele waarde alleen in een script wijzigen

Met de volgende opdracht wordt de waarde van de `$ConfirmPreference` variabele in een script gewijzigd. De wijziging heeft geen invloed op het globale bereik.

Gebruik eerst de volgende opdracht om de waarde van de `$ConfirmPreference` variabele in het lokale bereik weer te geven:

```
PS>  $ConfirmPreference
High
```

Maak een Scope.ps1-script dat de volgende opdrachten bevat:

```powershell
$ConfirmPreference = "Low"
"The value of `$ConfirmPreference is $ConfirmPreference."
```

Voer het script uit. Het script wijzigt de waarde van de `$ConfirmPreference` variabele en rapporteert vervolgens de waarde in het script bereik. De uitvoer moet er ongeveer uitzien als in de volgende uitvoer:

```output
The value of $ConfirmPreference is Low.
```

Test vervolgens de huidige waarde van de `$ConfirmPreference` variabele in het huidige bereik.

```
PS>  $ConfirmPreference
High
```

Dit voor beeld laat zien dat wijzigingen in de waarde van een variabele in het script bereik geen invloed hebben op de waarde van de variabele in het bovenliggende bereik.

### <a name="example-2-view-a-variable-value-in-different-scopes"></a>Voor beeld 2: een variabele waarde in verschillende bereiken weer geven

U kunt Scope-para meters gebruiken om de waarde van een variabele in het lokale bereik en in een bovenliggend bereik weer te geven.

Definieer eerst een `$test` variabele in het globale bereik.

```powershell
$test = "Global"
```

Maak vervolgens een Sample.ps1 script waarmee de variabele wordt gedefinieerd `$test` . Gebruik in het script een bereik aanpassings functie om te verwijzen naar de globale of lokale versies van de `$test` variabele.

In Sample.ps1:

```powershell
$test = "Local"
"The local value of `$test is $test."
"The global value of `$test is $global:test."
```

Wanneer u Sample.ps1 uitvoert, moet de uitvoer eruitzien als in de volgende uitvoer:

```output
The local value of $test is Local.
The global value of $test is Global.
```

Wanneer het script is voltooid, wordt alleen de globale waarde van `$test` in de sessie gedefinieerd.

```
PS>  $test
Global
```

### <a name="example-3-change-the-value-of-a-variable-in-a-parent-scope"></a>Voor beeld 3: de waarde van een variabele in een bovenliggend bereik wijzigen

Tenzij u een item beveiligt met behulp van de optie privé of een andere methode, kunt u de waarde van een variabele in een bovenliggend bereik weer geven en wijzigen.

Definieer eerst een `$test` variabele in het globale bereik.

```powershell
$test = "Global"
```

Maak vervolgens een Sample.ps1 script waarmee de variabele wordt gedefinieerd `$test` . Gebruik in het script een bereik aanpassings functie om te verwijzen naar de globale of lokale versies van de `$test` variabele.

In Sample.ps1:

```powershell
$global:test = "Local"
"The global value of `$test is $global:test."
```

Wanneer het script is voltooid, wordt de algemene waarde van `$test` gewijzigd.

```
PS>  $test
Local
```

### <a name="example-4-creating-a-private-variable"></a>Voor beeld 4: een persoonlijke variabele maken

Een persoonlijke variabele is een variabele met een **optie** -eigenschap die de waarde *privé* heeft. *Persoonlijke* variabelen worden overgenomen door het onderliggende bereik, maar ze kunnen alleen worden weer gegeven of gewijzigd in het bereik waarin ze zijn gemaakt.

Met de volgende opdracht maakt u een persoonlijke variabele `$ptest` met de naam in het lokale bereik.

```powershell
New-Variable -Name ptest -Value 1 -Option private
```

U kunt de waarde van `$ptest` in het lokale bereik weer geven en wijzigen.

```
PS>  $ptest
1

PS>  $ptest = 2
PS>  $ptest
2
```

Maak vervolgens een Sample.ps1 script dat de volgende opdrachten bevat. De opdracht probeert de waarde van weer te geven en te wijzigen `$ptest` .

In Sample.ps1:

```powershell
"The value of `$Ptest is $Ptest."
"The value of `$Ptest is $global:Ptest."
```

De `$ptest` variabele is niet zichtbaar in het script bereik. de uitvoer is leeg.

```powershell
"The value of $Ptest is ."
"The value of $Ptest is ."
```

### <a name="example-5-using-a-local-variable-in-a-remote-command"></a>Voor beeld 5: een lokale variabele gebruiken in een externe opdracht

Voor variabelen in een externe opdracht die in de lokale sessie wordt gemaakt, gebruikt u de `Using` bereik aanpassing. In Power shell wordt ervan uitgegaan dat de variabelen in externe opdrachten zijn gemaakt in de externe sessie.

De syntaxis is:

```
$Using:<VariableName>
```

Met de volgende opdrachten maakt u bijvoorbeeld een `$Cred` variabele in de lokale sessie en gebruikt u vervolgens de `$Cred` variabele in een externe opdracht:

```powershell
$Cred = Get-Credential
Invoke-Command $s {Remove-Item .\Test*.ps1 -Credential $Using:Cred}
```

Het gebruik van het bereik is geïntroduceerd in Power Shell 3,0. In Power Shell 2,0 om aan te geven dat een variabele is gemaakt in de lokale sessie, gebruikt u de volgende opdracht indeling.

```powershell
$Cred = Get-Credential
Invoke-Command $s {
  param($c)
  Remove-Item .\Test*.ps1 -Credential $c
} -ArgumentList $Cred
```

## <a name="see-also"></a>Zie ook

[about_Variables](about_Variables.md)

[about_Environment_Variables](about_Environment_Variables.md)

[about_Functions](about_Functions.md)

[about_Script_Blocks](about_Script_Blocks.md)

[Start-ThreadJob](/powershell/module/ThreadJob/Start-ThreadJob)
