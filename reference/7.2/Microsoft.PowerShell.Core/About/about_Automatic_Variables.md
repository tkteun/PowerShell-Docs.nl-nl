---
description: Beschrijft variabelen waarin status informatie voor Power shell wordt opgeslagen. Deze variabelen worden gemaakt en onderhouden door Power shell.
Locale: en-US
ms.date: 03/29/2021
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_automatic_variables?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Automatic_Variables
ms.openlocfilehash: 49c1a311c13078b4e625fbcb450817f1d5039e0d
ms.sourcegitcommit: bdd0fedaf9ba534645b2f7eb1fe1241481f58715
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 03/30/2021
ms.locfileid: "105936647"
---
# <a name="about-automatic-variables"></a>Over automatische variabelen

## <a name="short-description"></a>Korte beschrijving

Beschrijft variabelen waarin status informatie voor Power shell wordt opgeslagen. Deze variabelen worden gemaakt en onderhouden door Power shell.

## <a name="long-description"></a>Lange beschrijving

Deze variabelen worden conceptueel gezien als alleen-lezen. Hoewel ze **kunnen** worden geschreven naar, voor achterwaartse compatibiliteit, **moeten** ze daar niet naar worden geschreven.

Hier volgt een lijst met de automatische variabelen in Power shell:

### <a name=""></a>$$

Bevat het laatste token in de laatste door de sessie ontvangen regel.

### <a name=""></a>$?

Bevat de uitvoerings status van de laatste opdracht. Het bevat **waar** als de laatste opdracht is geslaagd en **Onwaar** als deze is mislukt.

Voor cmdlets en geavanceerde functies die in meerdere fasen in een pijp lijn worden uitgevoerd, bijvoorbeeld in zowel `process` -als `end` -blokken, `this.WriteError()` wordt het aanroepen van of `$PSCmdlet.WriteError()` respectievelijk op elk punt ingesteld `$?` op **False**, zoals `this.ThrowTerminatingError()` en `$PSCmdlet.ThrowTerminatingError()` .

De `Write-Error` cmdlet wordt altijd ingesteld `$?` op **False** direct nadat deze is uitgevoerd, maar is niet ingesteld `$?` op **False** voor een functie die deze aanroept:

```powershell
function Test-WriteError
{
    Write-Error "Bad"
    $? # $false
}

Test-WriteError
$? # $true
```

Voor dit laatste doel `$PSCmdlet.WriteError()` moet in plaats daarvan worden gebruikt.

Voor systeem eigen opdrachten (uitvoer bare bestanden) `$?` is ingesteld op **True** wanneer `$LASTEXITCODE` 0 is en is ingesteld op **False** wanneer `$LASTEXITCODE` een andere waarde is.

> [!NOTE]
> Tot Power shell 7, met een instructie tussen haakjes, wordt de syntaxis van de `(...)` subexpressie `$(...)` of matrix expressie `@(...)` altijd opnieuw ingesteld `$?` op **True**, zodat deze `(Write-Error)` wordt weer gegeven `$?` als **waar**.
> Dit is gewijzigd in Power shell 7, zodat `$?` altijd het werkelijke succes van de laatste opdracht wordt uitgevoerd in deze expressies.

### <a name=""></a>$^

Bevat het eerste token in de laatste regel die door de sessie is ontvangen.

### <a name="_"></a>$_

Hetzelfde als `$PSItem` . Bevat het huidige object in het pijplijn object. U kunt deze variabele gebruiken in opdrachten voor het uitvoeren van een actie op elk object of op geselecteerde objecten in een pijp lijn.

### <a name="args"></a>$args

Bevat een matrix met waarden voor niet-gedeclareerde para meters die worden door gegeven aan een functie, script of script blok. Wanneer u een functie maakt, kunt u de para meters declareren met behulp van het `param` sleutel woord of door een door komma's gescheiden lijst met para meters toe te voegen tussen haakjes achter de functie naam.

In een gebeurtenis actie bevat de `$Args` variabele objecten die de gebeurtenis argumenten vertegenwoordigen van de gebeurtenis die wordt verwerkt. Deze variabele wordt alleen ingevuld in de `Action` blok kering van een gebeurtenis registratie opdracht.
De waarde van deze variabele kan ook worden gevonden in de eigenschap **SourceArgs** van het **PSEventArgs** -object dat `Get-Event` retourneert.

### <a name="consolefilename"></a>$ConsoleFileName

Bevat het pad naar het console bestand ( `.psc1` ) dat het meest recent is gebruikt in de sessie. Deze variabele wordt ingevuld wanneer u Power shell start met de para meter **PSConsoleFile** of wanneer u de `Export-Console` cmdlet gebruikt om module namen te exporteren naar een-console bestand.

Wanneer u de `Export-Console` cmdlet zonder para meters gebruikt, wordt automatisch het console bestand bijgewerkt dat het meest recent is gebruikt in de sessie. U kunt deze automatische variabele gebruiken om te bepalen welk bestand moet worden bijgewerkt.

### <a name="error"></a>$Error

Bevat een matrix met fout objecten die de meest recente fouten vertegenwoordigen.
De meest recente fout is het eerste fout object in de matrix `$Error[0]` .

`$Error`Gebruik de para meter **Error Action** common met de waarde **Ignore** om te voor komen dat er een fout wordt toegevoegd aan de matrix. Zie [about_CommonParameters](about_CommonParameters.md)voor meer informatie.

### <a name="event"></a>$Event

Bevat een **PSEventArgs** -object dat de gebeurtenis vertegenwoordigt die wordt verwerkt. Deze variabele wordt alleen ingevuld binnen het `Action` blok van een gebeurtenis registratie opdracht, zoals `Register-ObjectEvent` . De waarde van deze variabele is hetzelfde object dat door de `Get-Event` cmdlet wordt geretourneerd. Daarom kunt u de eigenschappen van de variabele gebruiken `Event` , zoals `$Event.TimeGenerated` in een- `Action` script blok.

### <a name="eventargs"></a>$EventArgs

Bevat een object dat het eerste gebeurtenis argument vertegenwoordigt dat is afgeleid van **EventArgs** van de gebeurtenis die wordt verwerkt. Deze variabele wordt alleen ingevuld in de `Action` blok kering van een gebeurtenis registratie opdracht.
De waarde van deze variabele kan ook worden gevonden in de eigenschap **SourceEventArgs** van het **PSEventArgs** -object dat `Get-Event` retourneert.

### <a name="eventsubscriber"></a>$EventSubscriber

Bevat een **PSEventSubscriber** -object dat de gebeurtenis abonnee vertegenwoordigt van de gebeurtenis die wordt verwerkt. Deze variabele wordt alleen ingevuld in de `Action` blok kering van een gebeurtenis registratie opdracht. De waarde van deze variabele is hetzelfde object dat door de `Get-EventSubscriber` cmdlet wordt geretourneerd.

### <a name="executioncontext"></a>$ExecutionContext

Bevat een **EngineIntrinsics** -object dat de uitvoerings context van de Power shell-host vertegenwoordigt. U kunt deze variabele gebruiken om de uitvoerings objecten te vinden die beschikbaar zijn voor cmdlets.

### <a name="false"></a>$false

Bevat **Onwaar**. U kunt deze variabele gebruiken om **Onwaar** in opdrachten en scripts weer te geven in plaats van de teken reeks "false" te gebruiken. De teken reeks kan worden geïnterpreteerd als **True** als deze is geconverteerd naar een niet-lege teken reeks of een niet-nul-geheel getal.

### <a name="foreach"></a>$foreach

Bevat de enumerator (niet de resulterende waarden) van een [foreach](about_ForEach.md) -lus. De `$ForEach` variabele bestaat alleen wanneer de `ForEach` lus wordt uitgevoerd; deze wordt verwijderd nadat de lus is voltooid.

Opsommingen bevatten eigenschappen en methoden die u kunt gebruiken om loop waarden op te halen en de huidige loop-iteratie te wijzigen. Zie [using enumeraties](#using-enumerators)voor meer informatie.

### <a name="home"></a>$HOME

Bevat het volledige pad naar de basismap van de gebruiker. Deze variabele is het equivalent van de `"$env:homedrive$env:homepath"` Windows-omgevings variabelen `C:\Users\<UserName>` .

### <a name="host"></a>$Host

Bevat een-object dat de huidige hosttoepassing voor Power shell vertegenwoordigt. U kunt deze variabele gebruiken om de huidige host in opdrachten aan te geven of om de eigenschappen van de host, zoals of of, weer te geven of te wijzigen `$Host.version` `$Host.CurrentCulture` `$host.ui.rawui.setbackgroundcolor("Red")` .

### <a name="input"></a>$input

Bevat een enumerator die alle invoer inventariseert die wordt door gegeven aan een functie. De `$input` variabele is alleen beschikbaar voor functies en script blokken (die functies zijn die geen naam zijn).

- In een functie zonder een `Begin` , `Process` , of `End` blok keert de `$input` variabele de verzameling van alle invoer naar de functie.

- In het `Begin` blok bevat de `$input` variabele geen gegevens.

- In het `Process` blok bevat de `$input` variabele het object dat zich momenteel in de pijp lijn bevindt.

- In het `End` blok wordt met de `$input` variabele de verzameling van alle invoer in de functie opgesomd.

  > [!NOTE]
  > U kunt de variabele niet in `$input` zowel het proces blok als het eind blok in dezelfde functie of hetzelfde script blok gebruiken.

Omdat `$input` een enumerator is, heeft toegang tot de eigenschappen van het bestand `$input` niet langer beschikbaar. U kunt `$input` in een andere variabele opslaan om de eigenschappen opnieuw te gebruiken `$input` .

Opsommingen bevatten eigenschappen en methoden die u kunt gebruiken om loop waarden op te halen en de huidige loop-iteratie te wijzigen. Zie [using enumeraties](#using-enumerators)voor meer informatie.

De `$input` variabele is ook beschikbaar voor de opdracht die is opgegeven door de `-Command` para meter van `pwsh` wanneer deze wordt aangeroepen vanaf de opdracht regel. Het volgende voor beeld wordt uitgevoerd vanuit de Windows-opdracht shell.

```CMD
echo Hello | pwsh -Command """$input World!"""
```

### <a name="iscoreclr"></a>$IsCoreCLR

Bevat `$True` als de huidige sessie wordt uitgevoerd op .net core runtime (CoreCLR). Anders bevat `$False` .

### <a name="islinux"></a>$IsLinux

Bevat `$True` als de huidige sessie wordt uitgevoerd op een Linux-besturings systeem.
Anders bevat `$False` .

### <a name="ismacos"></a>$IsMacOS

Bevat `$True` als de huidige sessie wordt uitgevoerd op een MacOS-besturings systeem.
Anders bevat `$False` .

### <a name="iswindows"></a>$IsWindows

Bevat `$TRUE` als de huidige sessie wordt uitgevoerd op een Windows-besturings systeem. Anders bevat `$FALSE` .

### <a name="lastexitcode"></a>$LastExitCode

Bevat de afsluit code van het laatste op Windows gebaseerde programma dat is uitgevoerd.

### <a name="matches"></a>$Matches

De `Matches` variabele werkt met de `-match` `-notmatch` Opera tors en.
Wanneer u scalaire invoer verzendt naar `-match` de `-notmatch` operator OR en één overeenkomst detecteert, wordt een Booleaanse waarde geretourneerd en wordt de `$Matches` Automatische variabele gevuld met een hash-tabel van de teken reeks waarden die overeenkomen. De `$Matches` hash-tabel kan ook worden gevuld met opnamen wanneer u reguliere expressies met de operator gebruikt `-match` .

Zie about_Comparison_Operators voor meer informatie over de `-match` - [](about_comparison_operators.md)operator. Zie [about_Regular_Expressions](about_Regular_Expressions.md)voor meer informatie over reguliere expressies.

De `$Matches` variabele werkt ook in een `switch` instructie met de `-Regex` para meter. Het is op dezelfde manier gevuld als de `-match` `-notmatch` Opera tors en.
Zie about_Switch voor meer informatie over de `switch` - [](about_Switch.md)instructie.

### <a name="myinvocation"></a>$MyInvocation

Bevat informatie over de huidige opdracht, zoals de naam, para meters, parameter waarden en informatie over de manier waarop de opdracht is gestart, aangeroepen of aangeroepen, zoals de naam van het script dat de huidige opdracht heet.

`$MyInvocation` wordt alleen ingevuld voor scripts, functies en script blokken. U kunt de informatie in het object **System. Management. Automation. InvocationInfo** gebruiken dat `$MyInvocation` in het huidige script retourneert, zoals het pad en de bestands naam van het script ( `$MyInvocation.MyCommand.Path` ) of de naam van een functie ( `$MyInvocation.MyCommand.Name` ) om de huidige opdracht te identificeren. Dit is vooral handig om de naam van het huidige script te vinden.

Vanaf Power Shell 3,0 `MyInvocation` heeft de volgende nieuwe eigenschappen.

- **PSScriptRoot** : bevat het volledige pad naar het script dat de huidige opdracht heeft aangeroepen. De waarde van deze eigenschap wordt alleen ingevuld wanneer de aanroeper een script is.
- **PSCommandPath** : bevat het volledige pad en de bestands naam van het script dat de huidige opdracht heeft aangeroepen. De waarde van deze eigenschap wordt alleen ingevuld wanneer de aanroeper een script is.

In tegens telling tot de `$PSScriptRoot` en `$PSCommandPath` automatische variabelen bevatten de eigenschappen **PSScriptRoot** en **PSCommandPath** van de `$MyInvocation` Automatische variabele informatie over de aanroeper of aanroepende script, niet het huidige script.

### <a name="nestedpromptlevel"></a>$NestedPromptLevel

Bevat het huidige prompt niveau. Een waarde van 0 geeft aan dat het oorspronkelijke prompt niveau is. De waarde wordt verhoogd wanneer u een genest niveau invoert en afneemt wanneer u het afsluit.

Power shell presenteert bijvoorbeeld een genest opdracht prompt wanneer u de- `$Host.EnterNestedPrompt` methode gebruikt. Power shell presenteert ook een geneste opdracht prompt wanneer u een onderbrekings punt in het Power Shell-fout opsporingsprogramma bereikt.

Wanneer u een geneste prompt invoert, wordt de huidige opdracht door Power shell onderbroken, wordt de uitvoerings context opgeslagen en wordt de waarde van de `$NestedPromptLevel` variabele verhoogd. Als u extra geneste opdracht prompts wilt maken (Maxi maal 128 niveaus) of als u wilt terugkeren naar de oorspronkelijke opdracht prompt, voltooit u de opdracht of typt u `exit` .

De `$NestedPromptLevel` variabele helpt u bij het volgen van het prompt niveau. U kunt een alternatieve Power shell-opdracht prompt met daarin deze waarde maken zodat deze altijd zichtbaar is.

### <a name="null"></a>$null

`$null` is een automatische variabele die een **Null** of lege waarde bevat. U kunt deze variabele gebruiken om een ontbrekende of niet-gedefinieerde waarde te vertegenwoordigen in opdrachten en scripts.

Power shell behandelt `$null` als een object met een waarde, dat wil zeggen, als een expliciete tijdelijke aanduiding, zodat u kunt gebruiken `$null` om een lege waarde in een reeks waarden weer te geven.

Als bijvoorbeeld `$null` is opgenomen in een verzameling, wordt deze geteld als een van de objecten.

```powershell
$a = "one", $null, "three"
$a.count
```

```Output
3
```

Als u de `$null` variabele naar de cmdlet pipet `ForEach-Object` , wordt er een waarde voor gegenereerd `$null` , net zoals voor de andere objecten

```powershell
"one", $null, "three" | ForEach-Object { "Hello " + $_}
```

```Output
Hello one
Hello
Hello three
```

Als gevolg hiervan kunt u `$null` **geen parameter waarde** gebruiken. Een parameter waarde van `$null` overschrijft de standaard parameter waarde.

Omdat Power shell de `$null` variabele echter als tijdelijke aanduiding beschouwt, kunt u deze gebruiken in scripts zoals de volgende, wat niet zou kunnen werken als ze worden `$null` genegeerd.

```powershell
$calendar = @($null, $null, "Meeting", $null, $null, "Team Lunch", $null)
$days = "Sunday","Monday","Tuesday","Wednesday","Thursday",
        "Friday","Saturday"
$currentDay = 0
foreach($day in $calendar)
{
    if($day -ne $null)
    {
        "Appointment on $($days[$currentDay]): $day"
    }

    $currentDay++
}
```

```Output
Appointment on Tuesday: Meeting
Appointment on Friday: Team lunch
```

### <a name="pid"></a>$PID

Bevat de proces-id (PID) van het proces dat als host fungeert voor de huidige Power shell-sessie.

### <a name="profile"></a>$PROFILE

Bevat het volledige pad van het Power shell-profiel voor de huidige gebruiker en de huidige host-toepassing. U kunt deze variabele gebruiken om het profiel in opdrachten weer te geven. U kunt deze bijvoorbeeld in een opdracht gebruiken om te bepalen of er een profiel is gemaakt:

```powershell
Test-Path $PROFILE
```

Of u kunt deze gebruiken in een opdracht voor het maken van een profiel:

```powershell
New-Item -ItemType file -Path $PROFILE -Force
```

U kunt dit in een opdracht gebruiken om het profiel in **notepad.exe** te openen:

```powershell
notepad.exe $PROFILE
```

### <a name="psboundparameters"></a>$PSBoundParameters

Bevat een woorden lijst van de para meters die worden door gegeven aan een script of functie en de huidige waarden. Deze variabele heeft alleen een waarde in een bereik waarvoor para meters zijn gedeclareerd, zoals een script of functie. U kunt deze gebruiken om de huidige waarden van para meters weer te geven of te wijzigen of om parameter waarden door te geven aan een ander script of een functie.

In dit voor beeld wordt de functie **Test2** door gegeven `$PSBoundParameters` aan de functie **test1** . De `$PSBoundParameters` worden weer gegeven in de indeling **sleutel** en **waarde**.

```powershell
function Test1 {
   param($a, $b)

   # Display the parameters in dictionary format.
   $PSBoundParameters
}

function Test2 {
   param($a, $b)

   # Run the Test1 function with $a and $b.
   Test1 @PSBoundParameters
}
```

```powershell
Test2 -a Power -b Shell
```

```Output
Key   Value
---   -----
a     Power
b     Shell
```

### <a name="pscmdlet"></a>$PSCmdlet

Bevat een-object dat de cmdlet of geavanceerde functie vertegenwoordigt die wordt uitgevoerd.

U kunt de eigenschappen en methoden van het object in uw cmdlet of functie code gebruiken om te reageren op de gebruiks voorwaarden. De eigenschap **ParameterSetName** bevat bijvoorbeeld de naam van de para meter die wordt gebruikt en de methode **ShouldProcess** voegt de **WhatIf** en **de para** meters voor de cmdlet dynamisch toe.

`$PSCmdlet`Zie [about_Functions_CmdletBindingAttribute](about_Functions_CmdletBindingAttribute.md) en [about_Functions_Advanced](about_Functions_Advanced.md)voor meer informatie over de automatische variabele.

### <a name="pscommandpath"></a>$PSCommandPath

Bevat het volledige pad en de bestands naam van het script dat wordt uitgevoerd. Deze variabele is in alle scripts geldig.

### <a name="psculture"></a>$PSCulture

Vanaf Power shell 7 `$PSCulture` weerspiegelt de cultuur van de huidige Power shell-runs Pace (sessie). Als de cultuur wordt gewijzigd in een Power shell-runs Pace, `$PSCulture` wordt de waarde voor die runs Pace bijgewerkt.

De cultuur bepaalt de weergave notatie van items, zoals getallen, valuta's en datums, en wordt opgeslagen in een object **System. Globalization. Culture info** . Gebruiken `Get-Culture` om de cultuur van de computer weer te geven. `$PSCulture` bevat de waarde van de eigenschap **naam** .

### <a name="psdebugcontext"></a>$PSDebugContext

Bij het opsporen van fouten bevat deze variabele informatie over de fout opsporing. Anders bevat het een **Null** -waarde. Als gevolg hiervan kunt u deze gebruiken om aan te geven of het fout opsporingsprogramma controle heeft. Bij het invullen bevat deze een **PsDebugContext** -object met **onderbrekings punten** en eigenschappen **InvocationInfo** . De eigenschap **InvocationInfo** heeft verschillende nuttige eigenschappen, waaronder de **locatie** -eigenschap. De eigenschap **Location** geeft het pad van het script aan waarvoor fouten worden opgespoord.

### <a name="pshome"></a>$PSHOME

Bevat het volledige pad van de installatie directory voor Power shell, meestal `$env:windir\System32\PowerShell\v1.0` in Windows-systemen. U kunt deze variabele gebruiken in de paden van Power Shell-bestanden. De volgende opdracht zoekt bijvoorbeeld naar de conceptuele Help-onderwerpen voor de **variabele** woord:

```powershell
Select-String -Pattern Variable -Path $pshome\*.txt
```

### <a name="psitem"></a>$PSItem

Hetzelfde als `$_` . Bevat het huidige object in het pijplijn object. U kunt deze variabele gebruiken in opdrachten voor het uitvoeren van een actie op elk object of op geselecteerde objecten in een pijp lijn.

### <a name="psscriptroot"></a>$PSScriptRoot

Bevat de map van waaruit een script wordt uitgevoerd.

In Power Shell 2,0 is deze variabele alleen geldig in script modules ( `.psm1` ).
Vanaf Power Shell 3,0 is het in alle scripts geldig.

### <a name="pssenderinfo"></a>$PSSenderInfo

Bevat informatie over de gebruiker die de PSSession heeft gestart, met inbegrip van de gebruikers-id en de tijd zone van de oorspronkelijke computer. Deze variabele is alleen beschikbaar in PSSessions.

De `$PSSenderInfo` variabele bevat een door de gebruiker Configureer bare eigenschap, **ApplicationArguments**, die standaard alleen de `$PSVersionTable` van de oorspronkelijke sessie bevat. Als u gegevens wilt toevoegen aan de eigenschap **ApplicationArguments** , gebruikt u de para meter **ApplicationArguments** van de `New-PSSessionOption` cmdlet.

### <a name="psstyle"></a>$PSStyle

> [!NOTE]
> Deze variabele is alleen beschikbaar wanneer de `PSAnsiRendering` experimentele functie IA is ingeschakeld. Zie [about_Experimental_Features](about_Experimental_Features.md) en het [gebruik van experimentele functies](/powershell/scripting/learn/experimental-features)voor meer informatie.

Vanaf Power shell 7,2 hebt u nu toegang tot de `$PSStyle` Automatische variabele om de weer gave van ANSI-teken reeks uitvoer weer te geven en te wijzigen. De variabele bevat de volgende eigenschappen:

- **Opnieuw instellen** : Hiermee worden alle decoratie uitgeschakeld
- **Achtergrond** : genest object voor achtergrond kleur beheer
- **Blinken** : knippert
- **BlinkOff** : Hiermee schakelt u het Knip peren uit
- **Vet** : wordt vet ingeschakeld
- **BoldOff** : Hiermee schakelt u vet uit
- Voor **grond** genest object om de voorgrond kleur te bepalen
- **Opmaak** : Hiermee bepaalt u de standaard opmaak voor uitvoer stromen
- **Verborgen** : wordt verborgen ingeschakeld
- **HiddenOff** -uitgeschakeld verbergen
- **OutputRendering** : bepalen wanneer de weer gave van uitvoer wordt gebruikt
- **Omgekeerde** : omkeren inschakelen
- **ReverseOff** -uitschakelen
- **Cursief** -wordt cursief ingeschakeld
- **ItalicOff** : Hiermee schakelt u cursief in
- **Onderstrepen** : Hiermee wordt de onderstreping op
- **UnderlineOff** -schakelt onderstrepen uit

De basis leden retour neren teken reeksen van ANSI-escape reeksen die zijn toegewezen aan hun namen.
De waarden kunnen worden ingesteld om aanpassing mogelijk te maken. U kunt bijvoorbeeld vet op onderstreept wijzigen. Met de namen van eigenschappen kunt u gemakkelijker gedecoreerde teken reeksen maken met behulp van het volt ooien van het tabblad:

```powershell
"$($PSStyle.Background.LightCyan)Power$($PSStyle.Underline)$($PSStyle.Bold)Shell$($PSStyle.Reset)"
```

De `$PSStyle.Background` `$PSStyle.Foreground` leden en zijn teken reeksen die de ANSI-escape reeksen voor de 16 standaard console kleuren bevatten en een `Rgb()` methode om 24-bits kleuren op te geven. De waarden zijn instelbaar en kunnen een wille keurig aantal ANSI-escape reeksen bevatten.

`$PSStyle.Formatting` is een genest object voor het beheren van de standaard opmaak van debug-, fout-, uitgebreide en waarschuwings berichten. U kunt ook kenmerken, zoals vet en onderstrepen, beheren. Het wordt vervangen `$Host.PrivateData` als de manier om kleuren voor het weer geven van opmaak te beheren. `$Host.PrivateData` blijft bestaan voor achterwaartse compatibiliteit, maar is niet verbonden met `$PSStyle.Formatting` .

`$PSStyle.OutputRendering` is een `System.Management.Automation.OutputRendering` Enum met de waarden:

- **Automatisch**: dit is de standaard instelling. Als de host VirtualTerminal ondersteunt, wordt ANSI altijd als-is door gegeven, anders wordt de Lees bare tekst
- **ANSI**: ANSI wordt altijd door gegeven als-is
- **Tekst** zonder opmaak: ANSI-escape reeksen worden altijd verwijderd, zodat deze alleen uit tekst bestaan
- **HostOnly**: dit is het macOS-gedrag waarbij de ANSI-escape reeksen worden verwijderd in omgeleide of gesluisde uitvoer.

### <a name="psuiculture"></a>$PSUICulture

Bevat de naam van de cultuur van de gebruikers interface die momenteel wordt gebruikt in het besturings systeem. De GEBRUIKERSINTERFACE cultuur bepaalt welke teken reeksen worden gebruikt voor elementen van de gebruikers interface, zoals menu's en berichten. Dit is de waarde van de eigenschap **System.Globalization.CultureInfo.CurrentUICulture.name** van het systeem. Gebruik de cmdlet om het object **System. Globalization. Culture info** voor het systeem op te halen `Get-UICulture` .

### <a name="psversiontable"></a>$PSVersionTable

Bevat een alleen-lezen hash-tabel waarin details worden weer gegeven over de versie van Power shell die in de huidige sessie wordt uitgevoerd. De tabel bevat de volgende items:

- **PSVersion** -het Power shell-versie nummer
- **PSEdition** : deze eigenschap heeft de waarde ' Desktop ' voor Power Shell 4 en lager, en power shell 5,1 op volledige Windows-edities. Deze eigenschap heeft de waarde ' core ' voor Power shell 6 en hoger, maar ook Power shell 5,1 voor de gereduceerde footprint, zoals Windows nano server of Windows IoT.
- **GitCommitId** : de door Voer-id van de bron bestanden in github,
- **OS** -beschrijving van het besturings systeem waarop Power shell wordt uitgevoerd.
- **Platform** platform waarop het besturings systeem wordt uitgevoerd. De waarde op Linux en macOS is **UNIX**. Zie `$IsMacOs` en `$IsLinux` .
- **PSCompatibleVersions** -versies van Power shell die compatibel zijn met de huidige versie
- **PSRemotingProtocolVersion** : de versie van het Power shell Remote Management-Protocol.
- **SerializationVersion** -de versie van de serialisatie-methode
- **WSManStackVersion** : het versie nummer van de WS-Management stack

### <a name="pwd"></a>$PWD

Bevat een Path-object dat het volledige pad vertegenwoordigt van de huidige maplocatie voor de huidige Power shell-runs Pace.

> [!NOTE]
> Power shell ondersteunt meerdere runspaces per proces. Elke runs Pace heeft zijn eigen _huidige map_. Dit is niet hetzelfde als de huidige map van het proces: `[System.Environment]::CurrentDirectory` .

### <a name="sender"></a>$Sender

Bevat het object dat deze gebeurtenis heeft gegenereerd. Deze variabele wordt alleen ingevuld binnen het actie blok van een gebeurtenis registratie opdracht. De waarde van deze variabele kan ook worden gevonden in de eigenschap Sender van het **PSEventArgs** -object dat `Get-Event` retourneert.

### <a name="shellid"></a>$ShellId

Bevat de id van de huidige shell.

### <a name="stacktrace"></a>$StackTrace

Bevat een stack tracering voor de meest recente fout.

### <a name="switch"></a>$switch

Bevat de enumerator niet de resulterende waarden van een `Switch` instructie. De `$switch` variabele bestaat alleen als de `Switch` instructie wordt uitgevoerd en wordt verwijderd wanneer de instructie wordt uitgevoerd `switch` . Zie [about_Switch](about_Switch.md)voor meer informatie.

Opsommingen bevatten eigenschappen en methoden die u kunt gebruiken om loop waarden op te halen en de huidige loop-iteratie te wijzigen. Zie [using enumeraties](#using-enumerators)voor meer informatie.

### <a name="this"></a>$this

In een script blok dat een script eigenschap of script methode definieert, `$this` verwijst de variabele naar het object dat wordt uitgebreid.

In een aangepaste klasse verwijst de `$this` variabele naar het klassen object zelf, waardoor toegang wordt toegestaan tot eigenschappen en methoden die zijn gedefinieerd in de klasse.

### <a name="true"></a>$true

Bevat **waar**. U kunt deze variabele gebruiken om **waar** in opdrachten en scripts weer te geven.

## <a name="using-enumerators"></a>Opsommingen gebruiken

De `$input` `$foreach` variabelen, en `$switch` zijn alle inventarisaties die worden gebruikt om de waarden te herhalen die worden verwerkt door hun insluitende code blok.

Een enumerator bevat eigenschappen en methoden die u kunt gebruiken om herhaling te herstellen of opnieuw in te stellen, of om iteratie waarden op te halen. Het rechtstreeks bewerken van opsommings wordt niet beschouwd als best practice.

- Binnen lussen moeten [de tref woorden](about_Break.md) voor stroom beheer en [door gaan](about_Continue.md) worden voor keur.
- Binnen functies die pijplijn invoer accepteren, is het best practice om para meters met de kenmerken **ValueFromPipeline** of **ValueFromPipelineByPropertyName** te gebruiken.

  Zie [about_Functions_Advanced_Parameters](about_Functions_Advanced_Parameters.md)voor meer informatie.

### <a name="movenext"></a>Aangeroepen

De methode [MoveNext](/dotnet/api/system.collections.ienumerator.movenext) gaat de enumerator door naar het volgende element van de verzameling. **MoveNext** retourneert **True** als de enumerator is uitgebreid, **False** als de enumerator het einde van de verzameling heeft door gegeven.

> [!NOTE]
> De **Booleaanse** waarde die mijn **MoveNext** retourneert, wordt verzonden naar de uitvoer stroom.
> U kunt de uitvoer onderdrukken door deze te typecasting `[void]` of deze uit te sluizen naar [out-null](xref:Microsoft.PowerShell.Core.Out-Null).
>
> ```powershell
> $input.MoveNext() | Out-Null
> ```
>
> ```powershell
> [void]$input.MoveNext()
> ```

### <a name="reset"></a>Opnieuw instellen

Met de methode [Reset](/dotnet/api/system.collections.ienumerator.reset) wordt de enumerator ingesteld op de oorspronkelijke positie, die **vóór** het eerste element in de verzameling ligt.

### <a name="current"></a>Huidig

Met de [huidige](/dotnet/api/system.collections.ienumerator.current) eigenschap wordt het element in de verzameling, of de pijp lijn, op de huidige positie van de enumerator opgehaald.

De **huidige** eigenschap blijft dezelfde eigenschap retour neren totdat **MoveNext** is aangeroepen.

## <a name="examples"></a>Voorbeelden

### <a name="example-1-using-the-input-variable"></a>Voor beeld 1: de variabele $input gebruiken

In het volgende voor beeld wordt met de `$input` variabele de variabele gewist tot de volgende keer dat het proces blok wordt uitgevoerd. Als u de methode **Reset** gebruikt, wordt de variabele opnieuw ingesteld `$input` op de huidige pijplijn waarde.

```powershell
function Test
{
    begin
    {
        $i = 0
    }

    process
    {
        "Iteration: $i"
        $i++
        "`tInput: $input"
        "`tAccess Again: $input"
        $input.Reset()
        "`tAfter Reset: $input"
    }
}

"one","two" | Test
```

```Output
Iteration: 0
    Input: one
    Access Again:
    After Reset: one
Iteration: 1
    Input: two
    Access Again:
    After Reset: two
```

De variabele wordt door het proces blok automatisch `$input` door berekend, zelfs als u geen toegang hebt.

```powershell
$skip = $true
function Skip
{
    begin
    {
        $i = 0
    }

    process
    {
        "Iteration: $i"
        $i++
        if ($skip)
        {
            "`tSkipping"
            $skip = $false
        }
        else
        {
            "`tInput: $input"
        }
    }
}

"one","two" | Skip
```

```Output
Iteration: 0
    Skipping
Iteration: 1
    Input: two
```

### <a name="example-2-using-input-outside-the-process-block"></a>Voor beeld 2: $input buiten het proces blok gebruiken

Buiten het proces blok bevindt de `$input` variabele alle waarden die in de functie zijn ondergebracht.

- Als u de variabele opent, worden `$input` alle waarden gewist.
- De methode **Reset** herstelt de volledige verzameling.
- De **huidige** eigenschap wordt nooit ingevuld.
- De methode **MoveNext** retourneert False omdat de verzameling niet kan worden uitgebreid.
  - Door **MoveNext** aan te roepen, wordt de `$input` variabele gewist.

```powershell
Function All
{
    "All Values: $input"
    "Access Again: $input"
    $input.Reset()
    "After Reset: $input"
    $input.MoveNext() | Out-Null
    "After MoveNext: $input"
}

"one","two","three" | All
```

```Output
All Values: one two three
Access Again:
After Reset: one two three
After MoveNext:
```

### <a name="example-3-using-the-inputcurrent-property"></a>Voor beeld 3: het $input gebruiken. Huidige eigenschap

Met de **huidige** eigenschap kan de huidige pijplijn waarde meerdere keren worden gebruikt zonder gebruik te maken van de methode **Reset** . De methode **MoveNext** wordt niet automatisch aangeroepen door het proces blok.

De **huidige** eigenschap wordt nooit gevuld tenzij u **MoveNext** expliciet aanroept. De **huidige** eigenschap kan meermaals worden gebruikt binnen het proces blok zonder dat de waarde ervan wordt gewist.

```powershell
function Current
{
    begin
    {
        $i = 0
    }

    process
    {
        "Iteration: $i"
        $i++
        "`tBefore MoveNext: $($input.Current)"
        $input.MoveNext() | Out-Null
        "`tAfter MoveNext: $($input.Current)"
        "`tAccess Again: $($input.Current)"
    }
}

"one","two" | Current
```

```Output
Iteration: 0
    Before MoveNext:
    After MoveNext: one
    Access Again: one
Iteration: 1
    Before MoveNext:
    After MoveNext: two
    Access Again: two
```

### <a name="example-4-using-the-foreach-variable"></a>Voor beeld 4: de variabele $foreach gebruiken

In tegens telling tot de `$input` variabele `$foreach` vertegenwoordigt de variabele altijd alle items in de verzameling wanneer deze rechtstreeks worden geopend. Gebruik de eigenschap **Current** om toegang te krijgen tot het huidige verzamelings element en de methoden **Reset** en **MoveNext** om de waarde ervan te wijzigen.

> [!NOTE]
> Bij elke herhaling van de `foreach` lus wordt de methode **MoveNext** automatisch aangeroepen.

De volgende lus wordt alleen twee keer uitgevoerd. In de tweede iteratie wordt de verzameling verplaatst naar het derde element voordat de herhaling is voltooid. Na de tweede iteratie zijn er nu geen waarden meer om te herhalen en wordt de lus afgebroken.

De eigenschap **MoveNext** heeft geen invloed op de variabele die is gekozen om de verzameling () door te lopen `$Num` .

```powershell
$i = 0
foreach ($num in ("one","two","three"))
{
    "Iteration: $i"
    $i++
    "`tNum: $num"
    "`tCurrent: $($foreach.Current)"

    if ($foreach.Current -eq "two")
    {
        "Before MoveNext (Current): $($foreach.Current)"
        $foreach.MoveNext() | Out-Null
        "After MoveNext (Current): $($foreach.Current)"
        "Num has not changed: $num"
    }
}
```

```Output
Iteration: 0
        Num: one
        Current: one
Iteration: 1
        Num: two
        Current: two
Before MoveNext (Current): two
After MoveNext (Current): three
Num has not changed: two
```

Als u de methode **Reset** gebruikt, wordt het huidige element in de verzameling opnieuw ingesteld. In het volgende voor beeld worden de eerste twee elementen **twee keer** door lopen, omdat de methode **Reset** is aangeroepen. Na de eerste twee lussen `if` mislukt de instructie en doorloopt de lus alle drie de elementen normaal.

> [!IMPORTANT]
> Dit kan leiden tot een oneindige lus.

```powershell
$stopLoop = 0
foreach ($num in ("one","two", "three"))
{
    ("`t" * $stopLoop) + "Current: $($foreach.Current)"

    if ($num -eq "two" -and $stopLoop -lt 2)
    {
        $foreach.Reset() | Out-Null
        ("`t" * $stopLoop) + "Reset Loop: $stopLoop"
        $stopLoop++
    }
}
```

```Output
Current: one
Current: two
Reset Loop: 0
        Current: one
        Current: two
        Reset Loop: 1
                Current: one
                Current: two
                Current: three
```

### <a name="example-5-using-the-switch-variable"></a>Voor beeld 5: de variabele $switch gebruiken

De `$switch` variabele heeft precies dezelfde regels als de `$foreach` variabele.
In het volgende voor beeld worden alle enumerator-concepten gedemonstreerd.

> [!NOTE]
> U ziet dat de **NotEvaluated** -Case nooit wordt uitgevoerd, ook al is er geen `break` instructie na de methode **MoveNext** .

```powershell
$values = "Start", "MoveNext", "NotEvaluated", "Reset", "End"
$stopInfinite = $false
switch ($values)
{
    "MoveNext" {
        "`tMoveNext"
        $switch.MoveNext() | Out-Null
        "`tAfter MoveNext: $($switch.Current)"
    }
    # This case is never evaluated.
    "NotEvaluated" {
        "`tAfterMoveNext: $($switch.Current)"
    }

    "Reset" {
        if (!$stopInfinite)
        {
            "`tReset"
            $switch.Reset()
            $stopInfinite = $true
        }
    }

    default {
        "Default (Current): $($switch.Current)"
    }
}
```

```Output
Default (Current): Start
    MoveNext
    After MoveNext: NotEvaluated
    Reset
Default (Current): Start
    MoveNext
    After MoveNext: NotEvaluated
Default (Current): End
```

## <a name="see-also"></a>Zie ook

[about_Functions](about_Functions.md)

[about_Functions_Advanced](about_Functions_Advanced.md)

[about_Functions_Advanced_Methods](about_Functions_Advanced_Methods.md)

[about_Functions_Advanced_Parameters](about_Functions_Advanced_Parameters.md)

[about_Functions_OutputTypeAttribute](about_Functions_OutputTypeAttribute.md)

[about_Functions_CmdletBindingAttribute](about_Functions_CmdletBindingAttribute.md)

[about_Hash_Tables](about_Hash_Tables.md)

[about_Preference_Variables](about_Preference_Variables.md)

[about_Splatting](about_Splatting.md)

[about_Variables](about_Variables.md)

