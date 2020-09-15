---
title: Alles wat u wilt weten over ShouldProcess
description: ShouldProcess is een belang rijke functie die vaak wordt weer geven. Met de para meters WhatIf en confirm kunt u eenvoudig toevoegen aan uw functies.
ms.date: 05/23/2020
ms.custom: contributor-KevinMarquette
ms.openlocfilehash: 6bd4dbd5255203f2daf804163aa2a84d992d6697
ms.sourcegitcommit: 0afff6edbe560e88372dd5f1cdf51d77f9349972
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/20/2020
ms.locfileid: "86469732"
---
# <a name="everything-you-wanted-to-know-about-shouldprocess"></a>Alles wat u wilt weten over ShouldProcess

Power shell-functies hebben verschillende functies waarmee de manier waarop gebruikers ermee kunnen communiceren, aanzienlijk wordt verbeterd.
Een belang rijke functie die vaak wordt overzien, is `-WhatIf` en wordt `-Confirm` ondersteund en is gemakkelijk aan uw functies toe te voegen. In dit artikel wordt uitgelegd hoe u deze functie implementeert.

> [!NOTE]
> De [oorspronkelijke versie][] van dit artikel is gepubliceerd op de blog geschreven door [@KevinMarquette][] . Het Power shell-team hartelijk dank voor het delen van deze inhoud met ons. Raadpleeg zijn blog op [PowerShellExplained.com][].

Dit is een eenvoudige functie die u in uw functies kunt inschakelen om een veiligheids netwerk te bieden voor de gebruikers die er behoefte aan hebben. Er is niets scarier dan het uitvoeren van een opdracht waarvan u weet dat deze voor de eerste keer gevaarlijk kan zijn. De optie om het uit te voeren met `-WhatIf` kan een groot verschil maken.

## <a name="commonparameters"></a>CommonParameters

Voordat we kijken hoe u deze [algemene para meters][]implementeert, wil ik snel kijken hoe ze worden gebruikt.

## <a name="using--whatif"></a>Using-WhatIf

Wanneer een opdracht de `-WhatIf` para meter ondersteunt, kunt u zien wat de opdracht zou hebben gedaan in plaats van wijzigingen aan te brengen. het is een goede manier om de impact van een opdracht te testen, met name voordat u een destructieve handeling doet.

```powershell
PS C:\temp> Remove-Item -Path .\myfile1.txt -WhatIf
What if: Performing the operation "Remove File" on target "C:\Temp\myfile1.txt".
```

Als de opdracht op de juiste wijze `ShouldProcess` wordt geïmplementeerd, worden alle wijzigingen weer gegeven die zijn aangebracht. Hier volgt een voor beeld van het gebruik van een Joker teken om meerdere bestanden te verwijderen.

```powershell
PS C:\temp> Remove-Item -Path * -WhatIf
What if: Performing the operation "Remove File" on target "C:\Temp\myfile1.txt".
What if: Performing the operation "Remove File" on target "C:\Temp\myfile2.txt".
What if: Performing the operation "Remove File" on target "C:\Temp\importantfile.txt".
```

## <a name="using--confirm"></a>Gebruiken-bevestigen

Opdrachten die ondersteunen `-WhatIf` ook ondersteuning `-Confirm` . Dit geeft u de mogelijkheid om een actie te bevestigen voordat u deze uitvoert.

```powershell
PS C:\temp> Remove-Item .\myfile1.txt -Confirm

Confirm
Are you sure you want to perform this action?
Performing the operation "Remove File" on target "C:\Temp\myfile1.txt".
[Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "Y"):
```

In dit geval hebt u meerdere opties waarmee u kunt door gaan, een wijziging overs Laan of het script stoppen. De Help-prompt bevat een beschrijving van elk van deze opties.

```Output
Y - Continue with only the next step of the operation.
A - Continue with all the steps of the operation.
N - Skip this operation and proceed with the next operation.
L - Skip this operation and all subsequent operations.
S - Pause the current pipeline and return to the command prompt. Type "exit" to resume the pipeline.
[Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "Y"):
```

### <a name="localization"></a>Lokalisatie

Deze prompt is gelokaliseerd in Power shell, zodat de taal wordt gewijzigd op basis van de taal van uw besturings systeem. Dit is nog een ding die Power shell voor u beheert.

### <a name="switch-parameters"></a>Switch parameters

U kunt snel even kijken hoe u een waarde kunt door geven aan een switch parameter. De belangrijkste reden hiervoor is dat u de parameter waarden vaak wilt door geven aan de functies die u aanroept.

De eerste benadering is een specifieke parameter syntaxis die kan worden gebruikt voor alle para meters, maar u kunt deze ook gebruiken voor switch-para meters. U geeft een dubbele punt op om een waarde aan de para meter toe te voegen.

```powershell
Remove-Item -Path:* -WhatIf:$true
```

U kunt hetzelfde doen met een variabele.

```powershell
$DoWhatIf = $true
Remove-Item -Path * -WhatIf:$DoWhatIf
```

De tweede aanpak is het gebruik van een hashtabel om de waarde te splat.

```powershell
$RemoveSplat = @{
    Path = '*'
    WhatIf = $true
}
Remove-Item @RemoveSplat
```

Als u nog niet bekend bent met hashtabellen of splatting, hebt u nog een artikel op dat betrekking heeft op [Alles wat u wilde weten over hashtabellen][].

## <a name="supportsshouldprocess"></a>SupportsShouldProcess

De eerste stap om in te scha kelen `-WhatIf` en `-Confirm` te ondersteunen is het opgeven `SupportsShouldProcess` `CmdletBinding` van uw functie.

```powershell
function Test-ShouldProcess {
    [CmdletBinding(SupportsShouldProcess)]
    param()
    Remove-Item .\myfile1.txt
}
```

Als u `SupportsShouldProcess` op deze manier opgeeft, kunnen we onze functie nu aanroepen met `-WhatIf` (of `-Confirm` ).

```powershell
PS> Test-ShouldProcess -WhatIf
What if: Performing the operation "Remove File" on target "C:\Temp\myfile1.txt".
```

U ziet dat ik geen para meter met de naam heb gemaakt `-WhatIf` . Als `SupportsShouldProcess` u deze opgeeft, worden deze automatisch gemaakt voor ons. Wanneer we de `-WhatIf` para meter op hebben opgegeven `Test-ShouldProcess` , kunnen we de verwerking ook uitvoeren `-WhatIf` .

### <a name="trust-but-verify"></a>Vertrouwen, maar controleren

Er is een risico dat hier wordt vertrouwd dat alles dat u aanroept waarden overneemt `-WhatIf` . In de rest van de voor beelden gaan we ervan uit dat deze niet werkt en zeer expliciet zijn bij het aanroepen van andere opdrachten. U wordt aangeraden hetzelfde te doen.

```powershell
function Test-ShouldProcess {
    [CmdletBinding(SupportsShouldProcess)]
    param()
    Remove-Item .\myfile1.txt -WhatIf:$WhatIf
}
```

Ik ga de nuances veel later opnieuw bezoeken wanneer u een beter inzicht hebt in alle onderdelen die worden afgespeeld.

## <a name="pscmdletshouldprocess"></a>$PSCmdlet. ShouldProcess

De methode waarmee u kunt implementeren `SupportsShouldProcess` is `$PSCmdlet.ShouldProcess` . U wordt gebeld `$PSCmdlet.ShouldProcess(...)` om te zien of u een deel van de logica moet verwerken en Power shell zorgt voor de rest. Laten we beginnen met een voor beeld:

```powershell
function Test-ShouldProcess {
    [CmdletBinding(SupportsShouldProcess)]
    param()

    $file = Get-ChildItem './myfile1.txt'
    if($PSCmdlet.ShouldProcess($file.Name)){
        $file.Delete()
    }
}
```

De aanroep `$PSCmdlet.ShouldProcess($file.name)` van controles voor de `-WhatIf` `-Confirm` para meter (en) wordt vervolgens dienovereenkomstig afgehandeld. De `-WhatIf` oorzaken `ShouldProcess` van het uitvoeren van een beschrijving van de wijziging en het resultaat `$false` :

```powershell
PS> Test-ShouldProcess -WhatIf
What if: Performing the operation "Test-ShouldProcess" on target "myfile1.txt".
```

Als u een aanroep gebruikt `-Confirm` , wordt het script onderbroken en wordt de gebruiker gevraagd om door te gaan. Als de gebruiker is geselecteerd, wordt deze geretourneerd `$true` `Y` .

```powershell
PS> Test-ShouldProcess -Confirm
Confirm
Are you sure you want to perform this action?
Performing the operation "Test-ShouldProcess" on target "myfile1.txt".
[Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "Y"):
```

Een meester functie van `$PSCmdlet.ShouldProcess` is dat deze wordt verdubbeld als uitgebreide uitvoer. Dit is vaak afhankelijk van het implementeren van `ShouldProcess` .

```powershell
PS> Test-ShouldProcess -Verbose
VERBOSE: Performing the operation "Test-ShouldProcess" on target "myfile1.txt".
```

### <a name="overloads"></a>Overloads

Er zijn een aantal verschillende overbelastingen voor `$PSCmdlet.ShouldProcess` met verschillende para meters voor het aanpassen van de berichten. In het bovenstaande voor beeld is de eerste versie al gezien. Laten we dit eens nader bekijken.

```powershell
function Test-ShouldProcess {
    [CmdletBinding(SupportsShouldProcess)]
    param()

    if($PSCmdlet.ShouldProcess('TARGET')){
        # ...
    }
}
```

Dit produceert uitvoer die zowel de naam van de functie als het doel (waarde van de para meter) bevat.

```powershell
What if: Performing the operation "Test-ShouldProcess" on target "TARGET".
```

Het opgeven van een tweede para meter als de bewerking de bewerkings waarde gebruikt in plaats van de functie naam in het bericht.

```powershell
## $PSCmdlet.ShouldProcess('TARGET','OPERATION')
What if: Performing the operation "OPERATION" on target "TARGET".
```

De volgende optie is om drie para meters op te geven voor het volledig aanpassen van het bericht. Als er drie para meters worden gebruikt, is de eerste een het hele bericht. De tweede twee para meters worden nog steeds gebruikt in de `-Confirm` bericht uitvoer.

```powershell
## $PSCmdlet.ShouldProcess('MESSAGE','TARGET','OPERATION')
What if: MESSAGE
```

### <a name="quick-parameter-reference"></a>Naslag informatie voor snelle para meters

U hoeft alleen maar te weten welke para meters u moet gebruiken. Hier volgt een kort overzicht van hoe de para meters het bericht in de verschillende `-WhatIf` scenario's wijzigen.

```powershell
## $PSCmdlet.ShouldProcess('TARGET')
What if: Performing the operation "FUNCTION_NAME" on target "TARGET".

## $PSCmdlet.ShouldProcess('TARGET','OPERATION')
What if: Performing the operation "OPERATION" on target "TARGET".

## $PSCmdlet.ShouldProcess('MESSAGE','TARGET','OPERATION')
What if: MESSAGE
```

Ik gebruik een van de twee para meters.

### <a name="shouldprocessreason"></a>ShouldProcessReason

We hebben een vierde overbelasting die geavanceerder is dan de andere. U kunt de reden hiervoor `ShouldProcess` uitvoeren. Ik voeg dit hier alleen toe voor de volledige taak omdat we `$WhatIf` `$true` in plaats daarvan alleen kunnen controleren.

```powershell
$reason = ''
if($PSCmdlet.ShouldProcess('MESSAGE','TARGET','OPERATION',[ref]$reason)){
    Write-Output "Some Action"
}
$reason
```

De variabele moet worden door gegeven aan `$reason` de vierde para meter als referentie variabele met `[ref]` . `ShouldProcess` vult `$reason` met de waarde `None` of `WhatIf` . Ik heb dit niet gedaan, maar ik heb geen reden gehad om deze ooit te gebruiken.

### <a name="where-to-place-it"></a>Locatie van de locatie

U gebruikt `ShouldProcess` om uw scripts veiliger te maken. Daarom gebruikt u dit wanneer uw scripts wijzigingen aanbrengen. Ik wil de oproep zo `$PSCmdlet.ShouldProcess` dicht mogelijk bij de wijziging plaatsen.

```powershell
## general logic and variable work
if ($PSCmdlet.ShouldProcess('TARGET','OPERATION')){
    # Change goes here
}
```

Als ik een verzameling items Verwerk, roep ik deze voor elk item aan. De aanroep wordt dus in de foreach-lus geplaatst.

```powershell
foreach ($node in $collection){
    # general logic and variable work
    if ($PSCmdlet.ShouldProcess($node,'OPERATION')){
        # Change goes here
    }
}
```

De reden waarom ik `ShouldProcess` nauw keurig rond de wijziging bevindt, is dat ik zo veel mogelijk code wil uitvoeren wanneer deze `-WhatIf` is opgegeven. Ik wil dat de installatie en validatie zo mogelijk worden uitgevoerd, zodat de gebruiker deze fouten kan zien.

Ik wil dit ook gebruiken in mijn ziekte tests die mijn projecten valideren. Als er sprake is van een stukje logica dat moeilijk in de ziekte kan worden gesimuleerd, kunt u deze regel matig inpakken `ShouldProcess` en aanroepen `-WhatIf` in mijn tests. Het is beter om een deel van uw code te testen dan geen van deze.

### <a name="whatifpreference"></a>$WhatIfPreference

De eerste voorkeurs variabele is `$WhatIfPreference` . Dit is `$false` standaard. Als u deze instelt op `$true` , wordt de functie uitgevoerd alsof u deze hebt opgegeven `-WhatIf` . Als u dit instelt in uw sessie, worden alle opdrachten `-WhatIf` uitgevoerd.

Wanneer u een functie aanroept met `-WhatIf` , wordt de waarde van `$WhatIfPreference` ingesteld op `$true` binnen het bereik van uw functie.

## <a name="confirmimpact"></a>ConfirmImpact

De meeste van de voor beelden zijn voor `-WhatIf` , maar alles werkt ook met `-Confirm` om de gebruiker te vragen. U kunt de `ConfirmImpact` functie instellen op hoog en de gebruiker wordt gevraagd alsof deze is aangeroepen met `-Confirm` .

```powershell
function Test-ShouldProcess {
    [CmdletBinding(
        SupportsShouldProcess,
        ConfirmImpact = 'High'
    )]
    param()

    if ($PSCmdlet.ShouldProcess('TARGET')){
        Write-Output "Some Action"
    }
}
```

Met deze aanroep `Test-ShouldProcess` wordt de `-Confirm` actie uitgevoerd wegens de `High` impact.

```powershell
PS> Test-ShouldProcess

Confirm
Are you sure you want to perform this action?
Performing the operation "Test-ShouldProcess" on target "TARGET".
[Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "Y"): y
Some Action
```

Het probleem is nu moeilijker te gebruiken in andere scripts zonder dat de gebruiker om toestemming wordt gevraagd. In dit geval kunnen we een ' aan ' door geven `$false` `-Confirm` om de prompt te onderdrukken.

```powershell
PS> Test-ShouldProcess -Confirm:$false
Some Action
```

Ik wil `-Force` de ondersteuning voor een latere sectie toevoegen.

### <a name="confirmpreference"></a>$ConfirmPreference

`$ConfirmPreference` is een automatische variabele die bepaalt wanneer `ConfirmImpact` u wordt gevraagd om de uitvoering te bevestigen. Dit zijn de mogelijke waarden voor zowel `$ConfirmPreference` als `ConfirmImpact` .

- `High`
- `Medium`
- `Low`
- `None`

Met deze waarden kunt u verschillende niveaus van invloed op elke functie opgeven. Als u `$ConfirmPreference` een waarde hebt ingesteld die hoger `ConfirmImpact` is dan, wordt u niet gevraagd om de uitvoering te bevestigen.

`$ConfirmPreference`Is standaard ingesteld op `High` en `ConfirmImpact` `Medium` . Als u wilt dat uw functie de gebruiker automatisch vraagt, stelt u uw `ConfirmImpact` in op `High` . Stel deze optie in op `Medium` als het destructieve en gebruik `Low` als de opdracht altijd veilig moet worden uitgevoerd in de productie omgeving. Als u deze instelt op `none` , wordt u niet gevraagd, zelfs als deze `-Confirm` is opgegeven (maar nog wel ondersteuning biedt voor u `-WhatIf` ).

Bij het aanroepen van een functie met `-Confirm` wordt de waarde van `$ConfirmPreference` ingesteld op `Low` binnen het bereik van uw functie.

### <a name="suppressing-nested-confirm-prompts"></a>Geneste bevestigings prompts onderdrukken

De `$ConfirmPreference` kan worden opgehaald op basis van functies die u aanroept. Dit kan scenario's maken waarbij u een bevestigings prompt toevoegt en de functie die u aanroept ook vraagt de gebruiker.

Wat ik vaak wil doen, is `-Confirm:$false` het opgeven van de opdrachten die ik roep wanneer ik de vragen al heb afgehandeld.

```powershell
function Test-ShouldProcess {
    [CmdletBinding(SupportsShouldProcess)]
    param()

    $file = Get-ChildItem './myfile1.txt'
    if($PSCmdlet.ShouldProcess($file.Name)){
        Remove-Item -Path $file.FullName -Confirm:$false
    }
}
```

Hiermee gaat u terug naar een eerdere waarschuwing: er zijn nuances die niet worden `-WhatIf` door gegeven aan een functie en wanneer `-Confirm` een functie wordt door gegeven. Ik ga nu later terug.

## <a name="pscmdletshouldcontinue"></a>$PSCmdlet. ShouldContinue

Als u meer controle nodig hebt dan `ShouldProcess` biedt, kunt u de prompt direct activeren met `ShouldContinue` . `ShouldContinue` negeert `$ConfirmPreference` ,,, `ConfirmImpact` `-Confirm` `$WhatIfPreference` en `-WhatIf` wordt gevraagd elke keer dat deze wordt uitgevoerd.

In een kort overzicht kunt u gemakkelijk verwarren `ShouldProcess` en `ShouldContinue` . Ik wil het vaak niet gebruiken `ShouldProcess` omdat de para meter wordt aangeroepen `SupportsShouldProcess` in de `CmdletBinding` .
U moet `ShouldProcess` in vrijwel elk scenario gebruiken. Daarom heb ik die methode eerst gedekt.

Laten we eens kijken `ShouldContinue` in actie.

```powershell
function Test-ShouldContinue {
    [CmdletBinding()]
    param()

    if($PSCmdlet.ShouldContinue('TARGET','OPERATION')){
        Write-Output "Some Action"
    }
}
```

Dit biedt ons een eenvoudigere prompt met minder opties.

```powershell
Test-ShouldContinue

Second
TARGET
[Y] Yes  [N] No  [S] Suspend  [?] Help (default is "Y"):
```

Het grootste probleem met `ShouldContinue` is dat de gebruiker het interactief moet uitvoeren omdat de gebruiker altijd om toestemming wordt gevraagd. U moet altijd hulp middelen bouwen die door andere scripts kunnen worden gebruikt. Hoe u dit doet, is door de implementatie uit te voeren `-Force` . Ik ga dit idee later opnieuw.

### <a name="yes-to-all"></a>Ja op alles

Dit wordt automatisch afgehandeld, `ShouldProcess` maar we moeten nog wat werk voor doen `ShouldContinue` . Er is een tweede methode overbelasting waar we een paar waarden moeten door lopen door te verwijzen naar de logica te beheren.

```powershell
function Test-ShouldContinue {
    [CmdletBinding()]
    param()

    $collection = 1..5
    $yesToAll = $false
    $noToAll = $false

    foreach($target in $collection) {

        $continue = $PSCmdlet.ShouldContinue(
                "TARGET_$target",
                'OPERATION',
                [ref]$yesToAll,
                [ref]$noToAll
            )

        if ($continue){
            Write-Output "Some Action [$target]"
        }
    }
}
```

Ik heb een `foreach` lus en een verzameling toegevoegd om deze in actie weer te geven. Ik heb de `ShouldContinue` aanroep uit de `if` verklaring gehaald, zodat deze eenvoudiger te lezen is. Het aanroepen van een methode met vier para meters begint met het verkrijgen van een beetje rommelige, maar ik heb geprobeerd het uiterlijk zo schoon te maken.

## <a name="implementing--force"></a>Implementatie-forceren

`ShouldProcess` en `ShouldContinue` moet `-Force` op verschillende manieren worden geïmplementeerd. De truc van deze implementaties is dat `ShouldProcess` altijd moet worden uitgevoerd, maar `ShouldContinue` niet moet worden uitgevoerd als `-Force` is opgegeven.

### <a name="shouldprocess--force"></a>ShouldProcess-forceren

Als u uw instelt `ConfirmImpact` op `high` , is het eerste wat uw gebruikers gaan proberen te onderdrukken `-Force` . Dat is de eerste ding die ik toch kan doen.

```powershell
Test-ShouldProcess -Force
Error: Test-ShouldProcess: A parameter cannot be found that matches parameter name 'force'.
```

Als u de sectie intrekt, moeten deze als volgt `ConfirmImpact` worden opgeroepen:

```powershell
Test-ShouldProcess -Confirm:$false
```

Niet iedereen realiseert dat ze dit moeten doen en `-Confirm:$false` niet worden onderdrukt `ShouldContinue` .
Daarom moeten we `-Force` de Sanity van onze gebruikers implementeren. Bekijk hier dit volledige voor beeld:

```powershell
function Test-ShouldProcess {
    [CmdletBinding(
        SupportsShouldProcess,
        ConfirmImpact = 'High'
    )]
    param(
        [Switch]$Force
    )

    if ($Force -and -not $Confirm){
        $ConfirmPreference = 'None'
    }

    if ($PSCmdlet.ShouldProcess('TARGET')){
        Write-Output "Some Action"
    }
}
```

We voegen onze eigen `-Force` switch toe als een para meter en gebruiken de `$Confirm` automatische para meter die beschikbaar is bij `SupportsShouldProcess` het toevoegen in `CmdletBinding` .

```powershell
[CmdletBinding(
    SupportsShouldProcess,
    ConfirmImpact = 'High'
)]
param(
    [Switch]$Force
)
```

Hier kunt u zich richten op de `-Force` logica:

```powershell
if ($Force -and -not $Confirm){
    $ConfirmPreference = 'None'
}
```

Als de gebruiker opgeeft `-Force` , willen we de bevestigings prompt onderdrukken, tenzij ze ook opgeven `-Confirm` . Hiermee kan een gebruiker een wijziging afdwingen, maar wordt de wijziging toch bevestigd. Vervolgens stellen we `$ConfirmPreference` in het lokale bereik op de aanroep naar `ShouldProcess` detecties.

```powershell
if ($PSCmdlet.ShouldProcess('TARGET')){
        Write-Output "Some Action"
    }
```

Als iemand beide opgeeft `-Force` en `-WhatIf` , moet de prioriteit worden ingesteld `-WhatIf` . Deze aanpak behoudt de `-WhatIf` verwerking omdat deze `ShouldProcess` altijd wordt uitgevoerd.

Voeg geen controle toe voor de `$Force` waarde in de `if` instructie met de `ShouldProcess` . Dit is een anti patroon voor dit specifieke scenario, zelfs als dat zo is, in de volgende sectie voor `ShouldContinue` .

### <a name="shouldcontinue--force"></a>ShouldContinue-forceren

Dit is de juiste manier om met te implementeren `-Force` `ShouldContinue` .

```powershell
function Test-ShouldContinue {
    [CmdletBinding()]
    param(
        [Switch]$Force
    )

    if($Force -or $PSCmdlet.ShouldContinue('TARGET','OPERATION')){
        Write-Output "Some Action"
    }
}
```

Door de `$Force` aan de linkerkant van de operator te plaatsen, wordt het `-or` eerst geëvalueerd. Op deze manier schrijft u de uitvoering van de-instructie korte circuits `if` . Als `$force` dat `$true` het geval is, `ShouldContinue` wordt de niet uitgevoerd.

```powershell
PS> Test-ShouldContinue -Force
Some Action
```

U hoeft zich geen zorgen te maken over `-Confirm` of `-WhatIf` in dit scenario omdat deze niet worden ondersteund door `ShouldContinue` . Dit is de reden dat het anders moet worden afgehandeld dan `ShouldProcess` .

## <a name="scope-issues"></a>Scope problemen

Het gebruik van `-WhatIf` en `-Confirm` moet worden toegepast op alles binnen uw functies en alles wat ze aanroepen. Dit doet u door `$WhatIfPreference` in te stellen op `$true` of `$ConfirmPreference` `Low` in het lokale bereik van de functie. Wanneer u een andere functie aanroept, aanroepen om `ShouldProcess` deze waarden te gebruiken.

Dit werkt eigenlijk de meeste tijd goed. Telkens wanneer u ingebouwde cmdlet of een functie binnen hetzelfde bereik aanroept, werkt deze. Het werkt ook wanneer u een script of een functie in een script module aanroept vanuit de-console.

De ene specifieke locatie waar deze niet werkt, is wanneer een script of een script module een functie in een andere script module aanroept. Dit klinkt mogelijk niet zo goed als een groot probleem, maar de meeste modules die u maakt of ophaalt vanuit de PSGallery zijn script modules.

Het belangrijkste probleem is dat script modules de waarden voor `$WhatIfPreference` of `$ConfirmPreference` (en verschillende andere) niet overnemen bij het aanroepen van functies in andere script modules.

De beste manier om dit samen te vatten als een algemene regel is dat dit correct werkt voor binaire modules en de IT-afdeling nooit vertrouwt om te werken voor script modules. Als u dat niet zeker weet, kunt u het testen of alleen naar behoren werken.

Ik vind het persoonlijk dat dit zeer gevaarlijk is omdat er scenario's worden gemaakt waarin u `-WhatIf` ondersteuning toevoegt aan meerdere modules die correct werken, maar niet goed werken wanneer ze elkaar aanroepen.

Er is een GitHub-RFC actief om dit probleem te verhelpen. Zie [uitvoerings voorkeuren buiten het bereik van de script module door geven][RFC] voor meer informatie.

## <a name="in-closing"></a>In sluiten

Ik moet kijken hoe `ShouldProcess` ze elke keer moeten worden gebruikt om het te gebruiken. Het kan erg lang duren om onderscheid te `ShouldProcess` maken `ShouldContinue` . Ik moet bijna altijd zoeken welke para meters u moet gebruiken. Dit is geen probleem als u nog steeds van tijd tot tijd wordt geverwarrend. Dit artikel wordt weer gegeven wanneer u het nodig hebt. Ik weet dat ik het vaak zelf kan raadplegen.

Als u dit bericht leuk vindt, kunt u met behulp van de onderstaande koppeling uw gedachten delen met mij op Twitter. Ik vind het altijd leuk om te horen van mensen die de waarde van mijn inhoud ophalen.

<!-- link references -->
[oorspronkelijke versie]: https://powershellexplained.com/2020-03-15-Powershell-shouldprocess-whatif-confirm-shouldcontinue-everything/
[powershellexplained.com]: https://powershellexplained.com/
[@KevinMarquette]: https://twitter.com/KevinMarquette
[algemene para meters]: /powershell/module/microsoft.powershell.core/about/about_commonparameters
[alles wat u wilt weten over hashtabellen]: everything-about-hashtable.md
[RFC]: https://github.com/PowerShell/PowerShell-RFC/pull/221#issuecomment-592954839
