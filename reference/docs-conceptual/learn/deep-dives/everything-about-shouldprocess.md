---
title: Alles wat u wilde weten over ShouldProcess
description: ShouldProcess is een belangrijke functie die vaak over het hoofd wordt gezien. Met de parameters WhatIf en Confirm kunt u eenvoudig toevoegen aan uw functies.
ms.date: 05/23/2020
ms.custom: contributor-KevinMarquette
ms.openlocfilehash: 8d0d7dfe15f1ced2343212cddea7ae84a11eed62
ms.sourcegitcommit: 2ad76cd528338f8c2cc10a84c5c56c0e25b93436
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 04/19/2021
ms.locfileid: "107729969"
---
# <a name="everything-you-wanted-to-know-about-shouldprocess"></a>Alles wat u wilde weten over ShouldProcess

PowerShell-functies hebben verschillende functies die de manier waarop gebruikers erop reageren sterk verbeteren.
Een belangrijke functie die vaak over het hoofd wordt gezien, is ondersteuning en het is eenvoudig `-WhatIf` om aan uw functies toe te `-Confirm` voegen. In dit artikel gaan we dieper in op het implementeren van deze functie.

> [!NOTE]
> De [oorspronkelijke versie][] van dit artikel is te vinden in de blog geschreven door [@KevinMarquette][] . Het PowerShell-team bedankt Voor het delen van deze inhoud met ons. Bekijk zijn blog op [PowerShellExplained.com][].

Dit is een eenvoudige functie die u in uw functies kunt inschakelen om een veiligheidsnet te bieden voor de gebruikers die deze nodig hebben. Er is niets ergs dan het uitvoeren van een opdracht die voor de eerste keer gevaarlijk kan zijn. De optie om het uit te voeren `-WhatIf` met kan een groot verschil maken.

## <a name="commonparameters"></a>CommonParameters

Voordat we kijken naar het implementeren van deze [algemene parameters,][]wil ik even kijken hoe ze worden gebruikt.

## <a name="using--whatif"></a>-WhatIf gebruiken

Wanneer een opdracht de parameter ondersteunt, kunt u zien wat de opdracht zou hebben gedaan in plaats `-WhatIf` van wijzigingen aan te brengen. Het is een goede manier om de impact van een opdracht te testen, vooral voordat u iets destructiefs doet.

```powershell
PS C:\temp> Get-ChildItem
    Directory: C:\temp
Mode                 LastWriteTime         Length Name
----                 -------------         ------ ----
-a----         4/19/2021   8:59 AM              0 importantfile.txt
-a----         4/19/2021   8:58 AM              0 myfile1.txt
-a----         4/19/2021   8:59 AM              0 myfile2.txt

PS C:\temp> Remove-Item -Path .\myfile1.txt -WhatIf
What if: Performing the operation "Remove File" on target "C:\Temp\myfile1.txt".
```

Als de opdracht correct wordt geïmplementeerd, ziet u alle wijzigingen die `ShouldProcess` deze zou hebben aangebracht. Hier is een voorbeeld van het gebruik van een jokerteken om meerdere bestanden te verwijderen.

```powershell
PS C:\temp> Remove-Item -Path * -WhatIf
What if: Performing the operation "Remove File" on target "C:\Temp\myfile1.txt".
What if: Performing the operation "Remove File" on target "C:\Temp\myfile2.txt".
What if: Performing the operation "Remove File" on target "C:\Temp\importantfile.txt".
```

## <a name="using--confirm"></a>-Confirm gebruiken

Opdrachten die ondersteuning bieden `-WhatIf` voor ondersteunen ook `-Confirm` . Dit geeft u een kans om een actie te bevestigen voordat u deze gaat uitvoeren.

```powershell
PS C:\temp> Remove-Item .\myfile1.txt -Confirm

Confirm
Are you sure you want to perform this action?
Performing the operation "Remove File" on target "C:\Temp\myfile1.txt".
[Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "Y"):
```

In dit geval hebt u meerdere opties waarmee u kunt doorgaan, een wijziging kunt overslaan of het script kunt stoppen. In de Help-prompt worden al deze opties als deze beschreven.

```Output
Y - Continue with only the next step of the operation.
A - Continue with all the steps of the operation.
N - Skip this operation and proceed with the next operation.
L - Skip this operation and all subsequent operations.
S - Pause the current pipeline and return to the command prompt. Type "exit" to resume the pipeline.
[Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "Y"):
```

### <a name="localization"></a>Lokalisatie

Deze prompt is gelokaliseerd in PowerShell, zodat de taal wordt gewijzigd op basis van de taal van uw besturingssysteem. Dit is nog één ding dat PowerShell voor u beheert.

### <a name="switch-parameters"></a>Schakelen tussen parameters

Laten we even kijken naar manieren om een waarde door te geven aan een switchparameter. De belangrijkste reden waarom ik dit aanroep, is dat u vaak parameterwaarden wilt doorgeven aan functies die u aanroept.

De eerste benadering is een specifieke parametersyntaxis die kan worden gebruikt voor alle parameters, maar u ziet dat deze meestal wordt gebruikt voor switchparameters. U geeft een dubbele punt op om een waarde aan de parameter te koppelen.

```powershell
Remove-Item -Path:* -WhatIf:$true
```

U kunt hetzelfde doen met een variabele.

```powershell
$DoWhatIf = $true
Remove-Item -Path * -WhatIf:$DoWhatIf
```

De tweede benadering is het gebruik van een hashtabel om de waarde te splatten.

```powershell
$RemoveSplat = @{
    Path = '*'
    WhatIf = $true
}
Remove-Item @RemoveSplat
```

Als u geen bekend bent met hashtabels of splatting, heb ik nog een artikel over alles wat u wilde [weten over hashtables.][]

## <a name="supportsshouldprocess"></a>SupportsShouldProcess

De eerste stap voor het `-WhatIf` inschakelen `-Confirm` en ondersteunen van is het opgeven in de van uw `SupportsShouldProcess` `CmdletBinding` functie.

```powershell
function Test-ShouldProcess {
    [CmdletBinding(SupportsShouldProcess)]
    param()
    Remove-Item .\myfile1.txt
}
```

Door op deze manier op te geven, kunnen we nu `SupportsShouldProcess` onze functie aanroepen met `-WhatIf` (of `-Confirm` ).

```powershell
PS> Test-ShouldProcess -WhatIf
What if: Performing the operation "Remove File" on target "C:\Temp\myfile1.txt".
```

U ziet dat ik geen parameter met de naam heb `-WhatIf` gemaakt. Als u `SupportsShouldProcess` opgeeft, wordt deze automatisch voor ons gemaakt. Wanneer we de `-WhatIf` parameter voor `Test-ShouldProcess` opgeven, voeren sommige dingen die we aanroepen ook verwerking `-WhatIf` uit.

### <a name="trust-but-verify"></a>Vertrouwen, maar verifiëren

Er bestaat hier een risico wanneer u vertrouwt dat alles wat u aanroept waarden `-WhatIf` overgenomen. Voor de rest van de voorbeelden ga ik ervan uit dat het niet werkt en zeer expliciet is bij het aanroepen van andere opdrachten. U wordt aangeraden hetzelfde te doen.

```powershell
function Test-ShouldProcess {
    [CmdletBinding(SupportsShouldProcess)]
    param()
    Remove-Item .\myfile1.txt -WhatIf:$WhatIfPreference
}
```

Ik ga veel later terug naar de nuances als u een beter beeld hebt van alle onderdelen.

## <a name="pscmdletshouldprocess"></a>$PSCmdlet.ShouldProcess

De methode waarmee u kunt implementeren `SupportsShouldProcess` is `$PSCmdlet.ShouldProcess` . U roept `$PSCmdlet.ShouldProcess(...)` aan om te zien of u logica moet verwerken en PowerShell zorgt voor de rest. Laten we beginnen met een voorbeeld:

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

De aanroep `$PSCmdlet.ShouldProcess($file.name)` van controleert op `-WhatIf` de parameter (en ) en verwerkt deze `-Confirm` vervolgens dienovereenkomstig. De `-WhatIf` oorzaken zijn de uitvoer van een beschrijving van de wijziging en `ShouldProcess` retourneren `$false` :

```powershell
PS> Test-ShouldProcess -WhatIf
What if: Performing the operation "Test-ShouldProcess" on target "myfile1.txt".
```

Een aanroep `-Confirm` met pauzeert het script en vraagt de gebruiker met de optie om door te gaan. Deze retourneert `$true` als de gebruiker heeft `Y` geselecteerd.

```powershell
PS> Test-ShouldProcess -Confirm
Confirm
Are you sure you want to perform this action?
Performing the operation "Test-ShouldProcess" on target "myfile1.txt".
[Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "Y"):
```

Een geweldige functie van `$PSCmdlet.ShouldProcess` is dat deze wordt verdubbeld als uitgebreide uitvoer. Ik ben hier vaak van afhankelijk bij het implementeren `ShouldProcess` van .

```powershell
PS> Test-ShouldProcess -Verbose
VERBOSE: Performing the operation "Test-ShouldProcess" on target "myfile1.txt".
```

### <a name="overloads"></a>Overloads

Er zijn enkele verschillende overloads voor `$PSCmdlet.ShouldProcess` met verschillende parameters voor het aanpassen van de berichten. In het bovenstaande voorbeeld hebben we het eerste al gezien. Laten we dit eens nader bekijken.

```powershell
function Test-ShouldProcess {
    [CmdletBinding(SupportsShouldProcess)]
    param()

    if($PSCmdlet.ShouldProcess('TARGET')){
        # ...
    }
}
```

Dit produceert uitvoer die zowel de functienaam als het doel (waarde van de parameter) bevat.

```powershell
What if: Performing the operation "Test-ShouldProcess" on target "TARGET".
```

Als u een tweede parameter opgeeft als de bewerking, wordt de bewerkingswaarde gebruikt in plaats van de functienaam in het bericht.

```powershell
## $PSCmdlet.ShouldProcess('TARGET','OPERATION')
What if: Performing the operation "OPERATION" on target "TARGET".
```

De volgende optie is om drie parameters op te geven om het bericht volledig aan te passen. Wanneer er drie parameters worden gebruikt, is de eerste het hele bericht. De tweede twee parameters worden nog steeds gebruikt in de `-Confirm` berichtuitvoer.

```powershell
## $PSCmdlet.ShouldProcess('MESSAGE','TARGET','OPERATION')
What if: MESSAGE
```

### <a name="quick-parameter-reference"></a>Snel naslagmateriaal voor parameters

Voor het geval u hier alleen bent om erachter te komen welke parameters u moet gebruiken, vindt u hier een snelle referentie die laat zien hoe de parameters het bericht in de verschillende scenario's `-WhatIf` wijzigen.

```powershell
## $PSCmdlet.ShouldProcess('TARGET')
What if: Performing the operation "FUNCTION_NAME" on target "TARGET".

## $PSCmdlet.ShouldProcess('TARGET','OPERATION')
What if: Performing the operation "OPERATION" on target "TARGET".

## $PSCmdlet.ShouldProcess('MESSAGE','TARGET','OPERATION')
What if: MESSAGE
```

Ik gebruik meestal de ene met twee parameters.

### <a name="shouldprocessreason"></a>ShouldProcessReason

We hebben een vierde overbelasting die geavanceerder is dan de andere. Hiermee kunt u de reden van de `ShouldProcess` uitvoering zien. Ik voeg dit hier alleen toe voor de volledigheid, omdat we in plaats daarvan gewoon kunnen controleren of `$WhatIfPreference` dat `$true` zo is.

```powershell
$reason = ''
if($PSCmdlet.ShouldProcess('MESSAGE','TARGET','OPERATION',[ref]$reason)){
    Write-Output "Some Action"
}
$reason
```

We moeten de variabele doorgeven `$reason` aan de vierde parameter als referentievariabele met `[ref]` . `ShouldProcess` wordt gevuld `$reason` met de waarde of `None` `WhatIf` . Ik heb niet gezegd dat dit nuttig is en ik heb geen reden gehad om het ooit te gebruiken.

### <a name="where-to-place-it"></a>Waar u het kunt plaatsen

U gebruikt om `ShouldProcess` uw scripts veiliger te maken. U gebruikt deze dus wanneer uw scripts wijzigingen aanbrengen. Ik wil de `$PSCmdlet.ShouldProcess` aanroep zo dicht mogelijk bij de wijziging plaatsen.

```powershell
## general logic and variable work
if ($PSCmdlet.ShouldProcess('TARGET','OPERATION')){
    # Change goes here
}
```

Als ik een verzameling items verwerkt, noem ik deze voor elk item. De aanroep wordt dus in de foreach-lus geplaatst.

```powershell
foreach ($node in $collection){
    # general logic and variable work
    if ($PSCmdlet.ShouldProcess($node,'OPERATION')){
        # Change goes here
    }
}
```

De reden waarom ik de wijziging nauw om de wijziging heen plaats, is dat ik zoveel mogelijk code wil uitvoeren `ShouldProcess` wanneer `-WhatIf` wordt opgegeven. Ik wil dat de installatie en validatie zo mogelijk worden uitgevoerd, zodat de gebruiker deze fouten kan zien.

Ik wil dit ook gebruiken in mijn Tests voor het valideren van mijn projecten. Als ik een stukje logica heb dat moeilijk te na te denken is in een hoer, kan ik deze vaak inpakken en aanroepen `ShouldProcess` `-WhatIf` met in mijn tests. Het is beter om een deel van uw code te testen dan geen code.

### <a name="whatifpreference"></a>$WhatIfPreference

De eerste voorkeursvariabele die we hebben, is `$WhatIfPreference` . Dit is `$false` standaard. Als u deze in stelt `$true` op , wordt uw functie uitgevoerd alsof u hebt `-WhatIf` opgegeven. Als u dit in uw sessie in stelt, worden alle opdrachten `-WhatIf` uitgevoerd.

Wanneer u een functie aanroept met , wordt de waarde `-WhatIf` van ingesteld op binnen het bereik van uw `$WhatIfPreference` `$true` functie.

## <a name="confirmimpact"></a>ConfirmImpact

De meeste van mijn voorbeelden zijn `-WhatIf` voor, maar alles tot nu toe werkt ook met `-Confirm` om de gebruiker te vragen. U kunt de van de functie instellen op Hoog en de gebruiker wordt gevraagd of `ConfirmImpact` deze is aangeroepen met `-Confirm` .

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

Deze aanroep `Test-ShouldProcess` van voert de actie uit vanwege de `-Confirm` `High` impact.

```powershell
PS> Test-ShouldProcess

Confirm
Are you sure you want to perform this action?
Performing the operation "Test-ShouldProcess" on target "TARGET".
[Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "Y"): y
Some Action
```

Het voor de hand liggende probleem is dat het nu moeilijker is om in andere scripts te gebruiken zonder de gebruiker te vragen. In dit geval kunnen we een doorgeven aan `$false` om de prompt te `-Confirm` onderdrukken.

```powershell
PS> Test-ShouldProcess -Confirm:$false
Some Action
```

In een latere sectie wordt be lezen hoe `-Force` u ondersteuning toevoegt.

### <a name="confirmpreference"></a>$ConfirmPreference

`$ConfirmPreference` is een automatische variabele die bepaalt wanneer `ConfirmImpact` u wordt gevraagd om de uitvoering te bevestigen. Hier zijn de mogelijke waarden voor zowel `$ConfirmPreference` als `ConfirmImpact` .

- `High`
- `Medium`
- `Low`
- `None`

Met deze waarden kunt u verschillende niveaus van impact voor elke functie opgeven. Als u hebt ingesteld op een waarde die hoger is dan , wordt u niet gevraagd `$ConfirmPreference` om de uitvoering te `ConfirmImpact` bevestigen.

Is standaard `$ConfirmPreference` ingesteld op en is `High` `ConfirmImpact` `Medium` . Als u wilt dat de functie de gebruiker automatisch vraagt, stelt u uw `ConfirmImpact` in op `High` . Anders instellen op als `Medium` de destructieve en gebruiken `Low` als de opdracht altijd veilig in productie wordt uitgevoerd. Als u deze in stelt op , wordt er niet om gevraagd, zelfs niet als is opgegeven (maar u wordt `none` `-Confirm` wel `-WhatIf` ondersteund).

Wanneer u een functie aanroept met , wordt de waarde `-Confirm` van ingesteld op binnen het bereik van uw `$ConfirmPreference` `Low` functie.

### <a name="suppressing-nested-confirm-prompts"></a>Geneste bevestigingsprompts onderdrukken

De `$ConfirmPreference` kan worden opgehaald door functies die u aanroept. Dit kan scenario's maken waarbij u een bevestigingsprompt toevoegt en de functie die u aanroept ook de gebruiker vraagt.

Wat ik meestal doe, is opgeven in de opdrachten die ik aanroep wanneer ik de prompt `-Confirm:$false` al heb afgehandeld.

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

Dit brengt ons terug naar een eerdere waarschuwing: Er zijn nuances voor wanneer niet wordt doorgegeven aan een functie en wanneer wordt doorgegeven `-WhatIf` `-Confirm` aan een functie. Ik ga dit later nog eens doen.

## <a name="pscmdletshouldcontinue"></a>$PSCmdlet.ShouldContinue

Als u meer controle nodig hebt dan `ShouldProcess` u hebt, kunt u de prompt rechtstreeks activeren met `ShouldContinue` . `ShouldContinue` negeert `$ConfirmPreference` `ConfirmImpact` , , , , en omdat `-Confirm` deze telkens wordt gevraagd als deze wordt `$WhatIfPreference` `-WhatIf` uitgevoerd.

In een oogopslag is het eenvoudig om en te `ShouldProcess` `ShouldContinue` verwarrend. Ik vergeet niet om te `ShouldProcess` gebruiken, omdat de parameter wordt `SupportsShouldProcess` aangeroepen in de `CmdletBinding` .
U moet in `ShouldProcess` bijna elk scenario gebruiken. Daarom heb ik die methode eerst behandeld.

Laten we eens kijken `ShouldContinue` naar in actie.

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

Het grootste probleem met is dat de gebruiker deze interactief moet uitvoeren, omdat de gebruiker hier altijd `ShouldContinue` om wordt gevraagd. U moet altijd hulpprogramma's bouwen die door andere scripts kunnen worden gebruikt. De manier waarop u dit doet, is door te `-Force` implementeren. Ik kom later terug op dit idee.

### <a name="yes-to-all"></a>Ja op alles

Dit wordt automatisch afgehandeld met , maar we moeten iets meer `ShouldProcess` doen voor `ShouldContinue` . Er is een tweede methode-overload waarbij we een paar waarden moeten doorgeven om de logica te kunnen bepalen.

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

Ik heb een `foreach` lus en een verzameling toegevoegd om deze in actie te zien. Ik heb de `ShouldContinue` aanroep uit de `if` -instructie gehaald om het gemakkelijker te lezen. Het aanroepen van een methode met vier parameters begint een beetje vervelend te worden, maar ik heb geprobeerd om deze er zo schoon mogelijk uit te laten zien.

## <a name="implementing--force"></a>-Force implementeren

`ShouldProcess` en `ShouldContinue` moeten op verschillende manieren worden `-Force` geïmplementeerd. De trick voor deze implementaties is dat `ShouldProcess` altijd moet worden uitgevoerd, maar niet moet `ShouldContinue` worden uitgevoerd als is `-Force` opgegeven.

### <a name="shouldprocess--force"></a>ShouldProcess - Force

Als u uw in stelt op , is het eerste wat uw gebruikers proberen te onderdrukken `ConfirmImpact` `high` met `-Force` . Dat is het eerste wat ik toch doe.

```powershell
Test-ShouldProcess -Force
Error: Test-ShouldProcess: A parameter cannot be found that matches parameter name 'force'.
```

Zoals u zich nog herinnert `ConfirmImpact` uit de sectie, moeten ze deze als de volgende aanroepen:

```powershell
Test-ShouldProcess -Confirm:$false
```

Niet iedereen realiseert zich dat ze dat moeten doen `-Force` en onderdrukt `ShouldContinue` niet.
Daarom moeten we implementeren `-Force` voor de gezondheid van onze gebruikers. Bekijk dit volledige voorbeeld hier:

```powershell
function Test-ShouldProcess {
    [CmdletBinding(
        SupportsShouldProcess,
        ConfirmImpact = 'High'
    )]
    param(
        [Switch]$Force
    )

    if ($Force){
        $ConfirmPreference = 'None'
    }

    if ($PSCmdlet.ShouldProcess('TARGET')){
        Write-Output "Some Action"
    }
}
```

We voegen onze eigen `-Force` switch toe als parameter. De `-Confirm` parameter wordt automatisch toegevoegd wanneer wordt gebruikt in de `SupportsShouldProcess` `CmdletBinding` .

```powershell
[CmdletBinding(
    SupportsShouldProcess,
    ConfirmImpact = 'High'
)]
param(
    [Switch]$Force
)
```

Richt u hier op `-Force` de logica:

```powershell
if ($Force){
    $ConfirmPreference = 'None'
}
```

Als de gebruiker `-Force` opgeeft, willen we de bevestigingsprompt onderdrukken, tenzij ze ook `-Confirm` opgeven. Hierdoor kan een gebruiker een wijziging forcen, maar toch de wijziging bevestigen. Vervolgens stellen we `$ConfirmPreference` in het lokale bereik in. Nu stelt u met de parameter tijdelijk de in op geen, en wordt `-Force` de prompt om bevestiging uit te `$ConfirmPreference` stellen.

```powershell
if ($Force -or $PSCmdlet.ShouldProcess('TARGET')){
        Write-Output "Some Action"
    }
```

Als iemand zowel als `-Force` opfeit, `-WhatIf` moet deze prioriteit `-WhatIf` krijgen. Deze aanpak behoudt `-WhatIf` de verwerking omdat altijd wordt `ShouldProcess` uitgevoerd.

Voeg geen controle toe voor de waarde `$Force` in de instructie met de `if` `ShouldProcess` . Dat is een antipatroon voor dit specifieke scenario, ook al laat ik u dat zien in de volgende sectie voor `ShouldContinue` .

### <a name="shouldcontinue--force"></a>ShouldContinue -Force

Dit is de juiste manier om te `-Force` implementeren met `ShouldContinue` .

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

Door de `$Force` links van de operator te `-or` plaatsen, wordt deze eerst geëvalueerd. Als u deze op deze manier schrijft, wordt de uitvoering van de `if` -instructie verkort. Als `$force` `$true` is, wordt `ShouldContinue` de niet uitgevoerd.

```powershell
PS> Test-ShouldContinue -Force
Some Action
```

We hoeven ons geen zorgen te maken over `-Confirm` of in dit scenario omdat ze niet worden ondersteund door `-WhatIf` `ShouldContinue` . Daarom moet dit anders worden verwerkt dan `ShouldProcess` .

## <a name="scope-issues"></a>Bereikproblemen

Het `-WhatIf` gebruik van en moet van toepassing zijn op alles in uw functies en alles wat ze `-Confirm` aanroepen. Ze doen dit door in te `$WhatIfPreference` stellen op of in te stellen op in het lokale bereik van de `$true` `$ConfirmPreference` `Low` functie. Wanneer u een andere functie aanroept, roept u aan `ShouldProcess` om deze waarden te gebruiken.

Dit werkt in de meeste tijd correct. Steeds wanneer u de ingebouwde cmdlet of een functie in hetzelfde bereik aanroept, werkt deze. Het werkt ook wanneer u een script of een functie in een scriptmodule aanroept vanuit de -console.

De ene specifieke plaats waar het niet werkt, is wanneer een script of scriptmodule een functie aanroept in een andere scriptmodule. Dit klinkt misschien niet als een groot probleem, maar de meeste modules die u maakt of pullt uit PSGallery zijn scriptmodules.

Het belangrijkste probleem is dat scriptmodules de waarden voor of (en verschillende andere) niet overnemen wanneer ze worden aangeroepen vanuit `$WhatIfPreference` `$ConfirmPreference` functies in andere scriptmodules.

De beste manier om dit samen te vatten als een algemene regel is dat dit correct werkt voor binaire modules en nooit vertrouwt dat het werkt voor scriptmodules. Als u het niet zeker weet, test u deze of gaat u ervan uit dat het niet correct werkt.

Persoonlijk vind ik dit erg gevaarlijk omdat er scenario's worden gemaakt waarin u ondersteuning toevoegt aan meerdere modules die op de juiste manier werken, maar niet goed werken wanneer ze elkaar `-WhatIf` aanroepen.

We hebben een GitHub RFC die werkt om dit probleem op te lossen. Zie [Uitvoeringsvoorkeuren doorgeven buiten het bereik van scriptmodule][RFC] voor meer informatie.

## <a name="in-closing"></a>Afsluitend

Ik moet elke keer dat ik het nodig heb, op zoek naar hoe `ShouldProcess` ik het moet gebruiken. Het duurde lang om te onderscheiden van `ShouldProcess` `ShouldContinue` . Ik moet bijna altijd op zoek naar de parameters die ik moet gebruiken. U hoeft zich dus geen zorgen te maken als u van tijd tot tijd nog steeds in de war raakt. Dit artikel vindt u hier wanneer u het nodig hebt. Ik weet zeker dat ik er zelf vaak naar verwijs.

Als u tevreden bent over dit bericht, kunt u uw mening met mij delen op Twitter via de onderstaande koppeling. Ik vind het altijd leuk om te horen van mensen die waarde krijgen uit mijn inhoud.

<!-- link references -->
[oorspronkelijke versie]: https://powershellexplained.com/2020-03-15-Powershell-shouldprocess-whatif-confirm-shouldcontinue-everything/
[powershellexplained.com]: https://powershellexplained.com/
[@KevinMarquette]: https://twitter.com/KevinMarquette
[algemene parameters]: /powershell/module/microsoft.powershell.core/about/about_commonparameters
[alles wat u wilde weten over hashtables]: everything-about-hashtable.md
[RFC]: https://github.com/PowerShell/PowerShell-RFC/pull/221#issuecomment-592954839
