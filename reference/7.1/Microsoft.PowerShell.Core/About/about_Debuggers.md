---
description: Hierin wordt het Power Shell-fout opsporingsprogramma beschreven.
keywords: powershell,cmdlet
Locale: en-US
ms.date: 08/06/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_debuggers?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Debuggers
ms.openlocfilehash: 6765c33e4508e19dfca7f291f8452f1bb4730747
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/13/2020
ms.locfileid: "93252458"
---
# <a name="about-debuggers"></a>Over fout opsporing

## <a name="short-description"></a>KORTE BESCHRIJVING
Hierin wordt het Power Shell-fout opsporingsprogramma beschreven.

## <a name="long-description"></a>LANGE BESCHRIJVING

Fout opsporing is het proces van het onderzoeken van een script terwijl het wordt uitgevoerd om fouten in de script instructies te identificeren en te corrigeren. De Power Shell-fout opsporing kan u helpen bij het onderzoeken en identificeren van fouten en inefficiëntie in uw scripts, functies, opdrachten, Power shell desired state Configuration (DSC)-configuraties of-expressies.

Vanaf Power shell 5,0 is het Power Shell-fout opsporingsprogramma bijgewerkt voor het opsporen van fouten in scripts, functies, opdrachten, configuraties of expressies die worden uitgevoerd in de-console of Windows PowerShell ISE op externe computers. U kunt uitvoeren `Enter-PSSession` om een interactieve externe Power shell-sessie te starten waarin u onderbrekings punten en script bestanden en opdrachten voor fout opsporing op de externe computer kunt instellen. `Enter-PSSession` de functionaliteit is bijgewerkt, waarmee u opnieuw verbinding kunt maken en een niet-verbonden sessie kunt invoeren waarop een script of opdracht op een externe computer wordt uitgevoerd. Als het script dat wordt uitgevoerd een onderbrekings punt bereikt, wordt het fout opsporingsprogramma automatisch gestart door uw client sessie. Als de niet-verbonden sessie met een script al een onderbrekings punt heeft bereikt en op het onderbrekings punt wordt gestopt, `Enter-PSSession` wordt het opdracht regel programma voor fout opsporing automatisch gestart nadat u opnieuw verbinding hebt gemaakt met de sessie.

U kunt de functies van de Power Shell-fout opsporing gebruiken om een Power shell-script,-functie,-opdracht of-expressie te onderzoeken terwijl deze wordt uitgevoerd. Het Power Shell-fout opsporingsprogramma bevat een set cmdlets waarmee u onderbrekings punten kunt instellen, onderbrekings punten kunt beheren en de aanroep stack weer geven.

## <a name="debugger-cmdlets"></a>Cmdlets voor fout opsporing

Het Power Shell-fout opsporingsprogramma bevat de volgende set cmdlets:

- `Set-PSBreakpoint`: Hiermee stelt u onderbrekings punten in voor lijnen, variabelen en opdrachten.
- `Get-PSBreakpoint`: Hiermee worden onderbrekings punten in de huidige sessie opgehaald.
- `Disable-PSBreakpoint`: Schakelt onderbrekings punten in de huidige sessie uit.
- `Enable-PSBreakpoint`: Hiermee schakelt u onderbrekings punten in de huidige sessie opnieuw in.
- `Remove-PSBreakpoint`: Verwijdert onderbrekings punten uit de huidige sessie.
- `Get-PSCallStack`: Hiermee wordt de huidige aanroep stack weer gegeven.

## <a name="starting-and-stopping-the-debugger"></a>Fout opsporing starten en stoppen

Stel een of meer onderbrekings punten in om de fout opsporing te starten. Voer vervolgens het script, de opdracht of de functie uit die u wilt fouten opsporen.

Wanneer u een onderbrekings punt bereikt, wordt de uitvoering gestopt en wordt het besturings element overgezet naar het fout opsporingsprogramma.

Als u het fout opsporingsprogramma wilt stoppen, voert u het script, de opdracht of de functie uit totdat dit is voltooid. Of typ `stop` of `t` .

### <a name="debugger-commands"></a>Opdrachten voor fout opsporing

Wanneer u het fout opsporingsprogramma gebruikt in de Power shell-console, gebruikt u de volgende opdrachten om de uitvoering te beheren. In Windows PowerShell ISE gebruikt u opdrachten in het menu fout opsporing.

Opmerking: voor meer informatie over het gebruik van het fout opsporingsprogramma in andere hosttoepassingen, raadpleegt u de documentatie van de hosttoepassing.

- `s`, `StepInto` : Voert de volgende instructie uit en stopt vervolgens.

- `v`, `StepOver` : Voert de volgende instructie uit, maar slaat functies en aanroepen over. De overgeslagen instructies worden uitgevoerd, maar niet getrapt via.

- `Ctrl+Break`: (Alles onderbreken in ISE) is in een actief script in de Power shell-console of Windows PowerShell ISE. Houd er rekening mee dat <kbd>CTRL</kbd> + -<kbd>afbreek</kbd> in Windows Power Shell 2,0, 3,0 en 4,0 het programma sluit. Alles onderbreken werkt op zowel lokale als externe interactief uitgevoerde scripts.

- `o`, `StepOut` : Stappen van de huidige functie; Eén niveau omhoog als genest. In de hoofd tekst wordt het einde of het volgende onderbrekings punt voortgezet. De overgeslagen instructies worden uitgevoerd, maar niet getrapt via.

- `c`, `Continue` : Blijft actief totdat het script is voltooid of totdat het volgende onderbrekings punt is bereikt. De overgeslagen instructies worden uitgevoerd, maar niet getrapt via.

- `l`, `List` : Geeft het deel van het script weer dat wordt uitgevoerd. Standaard worden de huidige regel, vijf vorige regels en tien volgende regels weer gegeven.
  Als u het script wilt blijven aanbieden, drukt u op ENTER.

- `l <m>`, `List` : Hiermee worden 16 regels van het script weer gegeven, te beginnen met het regel nummer dat is opgegeven door `<m>` .

- `l <m> <n>`, `List` : Hiermee worden de `<n>` regels van het script weer gegeven, te beginnen met het regel nummer dat is opgegeven door `<m>` .

- `q`, `Stop` , `Exit` : Stopt met het uitvoeren van het script en sluit het fout opsporingsprogramma af. Als u fouten opspoort in een taak door de cmdlet uit te voeren `Debug-Job` , wordt `Exit` het fout opsporingsprogramma door de opdracht losgekoppeld en kan de taak blijven worden uitgevoerd.

- `k`, `Get-PsCallStack` : Hiermee wordt de huidige aanroep stack weer gegeven.

- `<Enter>`: Herhaalt de laatste opdracht als de stap (s), StepOver (v) of lijst (l). Anders vertegenwoordigt een indienings actie.

- `?`, `h` : Geeft de Help voor de opdracht fout opsporing weer.

Als u het fout opsporingsprogramma wilt afsluiten, kunt u stoppen (q) gebruiken.

Vanaf Power shell 5,0 kunt u de opdracht exit uitvoeren om een geneste foutopsporingssessie te afsluiten die u hebt gestart door ofwel of uit te voeren `Debug-Job` `Debug-Runspace` .

Met behulp van deze opdrachten voor fout opsporing kunt u een script uitvoeren, stoppen op een bepaald punt, de waarden van variabelen en de status van het systeem controleren en door gaan met het uitvoeren van het script totdat u een probleem hebt vastgesteld.

Opmerking: als u een instructie Step Into met een omleidings operator, zoals ' > ', worden de Power Shell-fout opsporings stappen voor alle resterende instructies in het script.

De waarden van script variabelen weer geven

Terwijl u zich in het fout opsporingsprogramma bevindt, kunt u ook opdrachten invoeren, de waarde van variabelen weer geven, cmdlets gebruiken en scripts uitvoeren op de opdracht regel.

U kunt de huidige waarde van alle variabelen weer geven in het script waarvoor fout opsporing wordt uitgevoerd, met uitzonde ring van de volgende automatische variabelen:

```powershell
$_
$Args
$Input
$MyInvocation
$PSBoundParameters
```

Als u probeert de waarde van een van deze variabelen weer te geven, krijgt u de waarde van die variabele voor in een interne pijp lijn die wordt gebruikt door het fout opsporingsprogramma, niet de waarde van de variabele in het script.

Als u de waarde van deze variabelen wilt weer geven voor het script dat wordt opgespoord, wijst u in het script de waarde van de automatische variabele toe aan een nieuwe variabele. Vervolgens kunt u de waarde van de nieuwe variabele weer geven.

Bijvoorbeeld:

```powershell
$scriptArgs = $Args
$scriptArgs
```

In het voor beeld in dit onderwerp wordt de waarde van de `$MyInvocation` variabele als volgt opnieuw toegewezen:

```powershell
$scriptname = $MyInvocation.MyCommand.Path
```

## <a name="the-debugger-environment"></a>De debugger omgeving

Wanneer u een onderbrekings punt bereikt, voert u de omgeving voor fout opsporing in. De opdracht prompt wordt gewijzigd zodat deze begint met "[DBG]:".

Zie [about_Prompts](about_prompts.md)voor meer informatie over het aanpassen van de prompt.

Daarnaast wordt in sommige hosttoepassingen, zoals de Power shell-console, (maar niet in Windows Power shell Integrated Scripting Environment [ISE]), een geneste prompt geopend voor fout opsporing. U kunt de geneste prompt detecteren door de herhaalde tekens die groter zijn dan (ASCII 62) die worden weer gegeven bij de opdracht prompt.

Het volgende is bijvoorbeeld de standaard prompt voor fout opsporing in de Power shell-console:

```
[DBG]: PS (get-location)>>>
```

U kunt het nest niveau vinden met behulp van de `$NestedPromptLevel` Automatische variabele.

Daarnaast wordt een automatische variabele `$PSDebugContext` gedefinieerd in het lokale bereik. U kunt de aanwezigheid van de `$PsDebugContext` variabele gebruiken om te bepalen of u zich in het fout opsporingsprogramma bevindt.

Bijvoorbeeld:

```powershell
if ($PSDebugContext) {"Debugging"} else {"Not Debugging"}
```

U kunt de waarde van de `$PSDebugContext` variabele in de fout opsporing gebruiken.

```
[DBG]: PS>>> $PSDebugContext.InvocationInfo

Name   CommandLineParameters  UnboundArguments  Location
----   ---------------------  ----------------  --------
=      {}                     {}                C:\ps-test\vote.ps1 (1)
```

## <a name="debugging-and-scope"></a>Fout opsporing en bereik

Breuk in het fout opsporingsprogramma wijzigt niet het bereik waarin u werkt, maar wanneer u een onderbrekings punt in een script bereikt, gaat u naar het script bereik. Het script bereik is een onderliggend item van het bereik waarin u het fout opsporingsprogramma hebt uitgevoerd.

Als u de variabelen en aliassen wilt vinden die in het script bereik zijn gedefinieerd, gebruikt u de para meter bereik van de `Get-Alias` `Get-Variable` cmdlets.

Met de volgende opdracht worden bijvoorbeeld de variabelen in het lokale (script) bereik opgehaald:

```powershell
Get-Variable -scope 0
```

U kunt de opdracht als volgt afkorten:

```powershell
gv -s 0
```

Dit is een handige manier om alleen de variabelen weer te geven die u in het script hebt gedefinieerd en die u tijdens het opsporen van fouten hebt gedefinieerd.

Fout opsporing op de opdracht regel

Wanneer u een onderbrekings punt voor een variabele of een opdracht onderbrekings punt instelt, kunt u het onderbrekings punt alleen instellen in een script bestand. Het onderbrekings punt wordt echter standaard ingesteld op alles dat wordt uitgevoerd in de huidige sessie.

Als u bijvoorbeeld een onderbrekings punt instelt voor de `$name` variabele, wordt het fout opsporingsprogramma afgebroken op een wille keurige `$name` variabele in een script, opdracht, functie, script-cmdlet of expressie die u uitvoert totdat u het onderbrekings punt uitschakelt of verwijdert.

Zo kunt u fouten opsporen in uw scripts in een realistischere context waarin ze mogelijk worden beïnvloed door functies, variabelen en andere scripts in de sessie en in het profiel van de gebruiker.

Regel onderbrekingen zijn specifiek voor script bestanden, zodat ze alleen worden ingesteld in script bestanden.

## <a name="debugging-functions"></a>Functies voor fout opsporing

Wanneer u een onderbrekings punt instelt voor een functie die de volgende secties bevat, `Begin` `Process` wordt `End` het fout opsporingsprogramma afgebroken op de eerste regel van elke sectie.

Bijvoorbeeld:

```powershell
function test-cmdlet {
    begin {
        write-output "Begin"
    }
    process {
        write-output "Process"
    }
    end {
        write-output "End"
    }
}

C:\PS> Set-PSBreakpoint -command test-cmdlet

C:\PS> test-cmdlet

Begin
Entering debug mode. Use h or ? for help.

Hit Command breakpoint on 'prompt:test-cmdlet'

test-cmdlet

[DBG]: C:\PS> c
Process
Entering debug mode. Use h or ? for help.

Hit Command breakpoint on 'prompt:test-cmdlet'

test-cmdlet

[DBG]: C:\PS> c
End
Entering debug mode. Use h or ? for help.

Hit Command breakpoint on 'prompt:test-cmdlet'

test-cmdlet

# [DBG]: C:\PS>
```

## <a name="debugging-remote-scripts"></a>Fout opsporing voor externe scripts

Vanaf Power shell 5,0 kunt u de Power Shell-fout opsporing uitvoeren in een externe sessie, in de-console of in Windows PowerShell ISE.
`Enter-PSSession` de functionaliteit is bijgewerkt, waarmee u opnieuw verbinding kunt maken en een niet-verbonden sessie kunt invoeren die wordt uitgevoerd op een externe computer en die op dit moment een script uitvoert. Als het script dat wordt uitgevoerd een onderbrekings punt bereikt, wordt het fout opsporingsprogramma automatisch gestart door uw client sessie.

Hier volgt een voor beeld van hoe dit werkt, waarbij onderbrekings punten in een script worden ingesteld op regels 6, 11, 22 en 25. In het voor beeld, wanneer het fout opsporingsprogramma wordt gestart, zijn er twee instructies: de naam van de computer waarop de sessie wordt uitgevoerd en de DBG-prompt waarin u kunt zien dat u zich in de foutopsporingsmodus bevindt.

```powershell
Enter-Pssession -Cn localhost
[localhost]: PS C:\psscripts> Set-PSBreakpoint .\ttest19.ps1 6,11,22,25

ID Script          Line     Command          Variable          Action
-- ------          ----     -------          --------          ------
0 ttest19.ps1          6
1 ttest19.ps1          11
2 ttest19.ps1          22
3 ttest19.ps1          25

[localhost]: PS C:\psscripts> .\ttest19.ps1
Hit Line breakpoint on 'C:\psscripts\ttest19.ps1:11'

At C:\psscripts\ttest19.ps1:11 char:1
+ $winRMName = "WinRM"
# + ~

[localhost]: [DBG]: PS C:\psscripts>> list

6:      1..5 | foreach { sleep 1; Write-Output "hello2day $_" }
7:  }
# 8:

9:  $count = 10
10:  $psName = "PowerShell"
11:* $winRMName = "WinRM"
12:  $myVar = 102
# 13:

14:  for ($i=0; $i -lt $count; $i++)
15:  {
16:      sleep 1
17:      Write-Output "Loop iteration is: $i"
18:      Write-Output "MyVar is $myVar"
# 19:

20:      hello2day
# 21:


[localhost]: [DBG]: PS C:\psscripts>> stepover
At C:\psscripts\ttest19.ps1:12 char:1
+ $myVar = 102
# + ~

[localhost]: [DBG]: PS C:\psscripts>> quit
[localhost]: PS C:\psscripts> Exit-PSSession
PS C:\psscripts>
```

## <a name="examples"></a>Voorbeelden

Met dit test script wordt de versie van het besturings systeem gedetecteerd en wordt er een systeem bericht weer gegeven. Het bevat een functie, een functie aanroep en een variabele.

De volgende opdracht wordt de inhoud van het test script bestand weer gegeven:

```powershell
PS C:\PS-test>  Get-Content test.ps1

function psversion {
  "PowerShell " + $PSVersionTable.PSVersion
  if ($PSVersionTable.PSVersion.Major -lt 6) {
    "Upgrade to PowerShell 6.0!"
  }
  else {
    "Have you run a background job today (start-job)?"
  }
}

$scriptName = $MyInvocation.MyCommand.Path
psversion
"Done $scriptName."
```

Als u wilt beginnen, stelt u een onderbrekings punt in dat interessant is in het script, zoals een regel, opdracht, variabele of functie.

Begin door een regel onderbreking te maken op de eerste regel van het Test.ps1 script in de huidige map.

```powershell
PS C:\ps-test> Set-PSBreakpoint -line 1 -script test.ps1
```

U kunt deze opdracht afkorten tot:

```powershell
PS C:\ps-test> spb 1 -s test.ps1
```

De opdracht retourneert een regel voor het onderbrekings object ( **System. Management. Automation. LineBreakpoint** ).

```
Column     : 0
Line       : 1
Action     :
Enabled    : True
HitCount   : 0
Id         : 0
Script     : C:\ps-test\test.ps1
ScriptName : C:\ps-test\test.ps1
```

Start nu het script.

```powershell
PS C:\ps-test> .\test.ps1
```

Wanneer het script het eerste onderbrekings punt bereikt, geeft het onderbrekings bericht aan dat het fout opsporingsprogramma actief is. Hierin wordt het onderbrekings punt beschreven en wordt een voor beeld weer gegeven van de eerste regel van het script. Dit is een functie declaratie. De opdracht prompt wordt ook gewijzigd om aan te geven dat het fout opsporingsprogramma het besturings element heeft.

De voorbeeld regel bevat de script naam en het regel nummer van de vooraf bekeken opdracht.

```powershell
Entering debug mode. Use h or ? for help.

Hit Line breakpoint on 'C:\ps-test\test.ps1:1'

test.ps1:1   function psversion {
# DBG>
```

Gebruik de stap opdracht (en) om de eerste instructie in het script uit te voeren en de volgende instructie te bekijken. In de volgende instructie wordt de `$MyInvocation` Automatische variabele gebruikt om de waarde van de `$scriptName` variabele in te stellen op het pad en de bestands naam van het script bestand.

```powershell
DBG> s
test.ps1:11  $scriptName = $MyInvocation.MyCommand.Path
```

De variabele wordt op dit moment `$scriptName` niet ingevuld, maar u kunt de waarde van de variabele controleren door de waarde ervan weer te geven. In dit geval is de waarde `$null` .

```powershell
DBG> $scriptname
# DBG>
```

Gebruik een andere stap opdracht (en) om de huidige instructie uit te voeren en de volgende instructie in het script te bekijken. Met de volgende instructie wordt de functie PsVersion aangeroepen.

```powershell
DBG> s
test.ps1:12  psversion
```

Op dit moment wordt de `$scriptName` variabele gevuld, maar u controleert de waarde van de variabele door de waarde ervan weer te geven. In dit geval wordt de waarde ingesteld op het pad naar het script.

```powershell
DBG> $scriptName
C:\ps-test\test.ps1
```

Gebruik een andere stap opdracht om de functie aanroep uit te voeren. Druk op ENTER of typ "s" voor stap.

```powershell
DBG> s
test.ps1:2       "PowerShell " + $PSVersionTable.PSVersion
```

Het debug-bericht bevat een voor beeld van de instructie in de functie. Als u deze instructie wilt uitvoeren en de volgende instructie in de functie wilt bekijken, kunt u een `Step` opdracht gebruiken. Maar in dit geval gebruikt u een StepOut-opdracht (o). De uitvoering van de functie is voltooid (tenzij deze een onderbrekings punt bereikt) en stappen voor de volgende instructie in het script.

```powershell
DBG> o
Windows PowerShell 2.0
Have you run a background job today (start-job)?
test.ps1:13  "Done $scriptName"
```

Omdat we de laatste instructie in het script hebben gedaan, hebben de opdrachten stap, StepOut en voortzetten hetzelfde effect. In dit geval gebruikt u StepOut (o).

```powershell
Done C:\ps-test\test.ps1
PS C:\ps-test>
```

De opdracht StepOut voert de laatste opdracht uit. De standaard opdracht prompt geeft aan dat het fout opsporingsprogramma is afgesloten en het besturings element heeft geretourneerd aan de opdracht processor.

Voer het fout opsporingsprogramma nu opnieuw uit. Gebruik eerst de cmdlets en om het huidige onderbrekings punt te verwijderen `Get-PsBreakpoint` `Remove-PsBreakpoint` . (Als u denkt dat u het onderbrekings punt zou kunnen hergebruiken, gebruikt u de `Disable-PsBreakpoint` cmdlet in plaats van `Remove-PsBreakpoint` .)

```powershell
PS C:\ps-test> Get-PSBreakpoint| Remove-PSBreakpoint
```

U kunt deze opdracht afkorten tot:

```powershell
PS C:\ps-test> gbp | rbp
```

Of voer de opdracht uit door een functie te schrijven, zoals de volgende functie:

```powershell
function delbr { gbp | rbp }
```

Maak nu een onderbrekings punt voor de `$scriptname` variabele.

```powershell
PS C:\ps-test> Set-PSBreakpoint -variable scriptname -script test.ps1
```

U kunt de opdracht als volgt afkorten:

```powershell
PS C:\ps-test> sbp -v scriptname -s test.ps1
```

Start nu het script. Het script bereikt het onderbrekings punt van de variabele. De standaard modus is schrijven, dus de uitvoering stopt net vóór de instructie die de waarde van de variabele wijzigt.

```powershell
PS C:\ps-test> .\test.ps1
Hit Variable breakpoint on 'C:\ps-test\test.ps1:$scriptName'
(Write access)

test.ps1:11  $scriptName = $MyInvocation.MyCommand.Path
# DBG>
```

De huidige waarde van de variabele weer geven `$scriptName` `$null` .

```powershell
DBG> $scriptName
# DBG>
```

Gebruik een stap opdracht (en) om de instructie uit te voeren waarmee de variabele wordt gevuld.
Vervolgens wordt de nieuwe waarde van de variabele weer gegeven `$scriptName` .

```powershell
DBG> $scriptName
C:\ps-test\test.ps1
```powershell

Use a Step command (s) to preview the next statement in the script.

```powershell
DBG> s
test.ps1:12  psversion
```

De volgende instructie is een aanroep van de functie PsVersion. Als u de functie wilt overs Laan, maar nog steeds wilt uitvoeren, gebruikt u een StepOver-opdracht (v). Als u zich al in de functie bevindt wanneer u StepOver gebruikt, is deze niet effectief. De functie aanroep wordt weer gegeven, maar wordt niet uitgevoerd.

```powershell
DBG> v
Windows PowerShell 2.0
Have you run a background job today (start-job)?
test.ps1:13  "Done $scriptName"
```

Met de opdracht StepOver wordt de functie uitgevoerd en wordt een voor beeld weer gegeven van de volgende instructie in het script, die de laatste regel afdrukt.

Gebruik een stop opdracht (t) om het fout opsporingsprogramma af te sluiten. De opdracht prompt wordt teruggezet naar de standaard opdracht prompt.

```powershell
C:\ps-test>
```

Gebruik de cmdlets en om de onderbrekings punten te verwijderen `Get-PsBreakpoint` `Remove-PsBreakpoint` .

```powershell
PS C:\ps-test> Get-PSBreakpoint| Remove-PSBreakpoint
```

Maak een nieuwe opdracht onderbrekings punt voor de functie PsVersion.

```powershell
PS C:\ps-test> Set-PSBreakpoint -command psversion -script test.ps1
```

U kunt deze opdracht afkorten tot:

```powershell
PS C:\ps-test> sbp -c psversion -s test.ps1
```

Voer nu het script uit.

```powershell
PS C:\ps-test> .\test.ps1
Hit Command breakpoint on 'C:\ps-test\test.ps1:psversion'

test.ps1:12  psversion
# DBG>
```

Het script bereikt het onderbrekings punt bij de functie aanroep. De functie is op dit moment nog niet aangeroepen. Dit biedt u de mogelijkheid om de actie parameter van te gebruiken om voor waarden in te `Set-PSBreakpoint` stellen voor de uitvoering van het onderbrekings punt of om voorbereidende-of diagnose taken uit te voeren, zoals het starten van een logboek of het aanroepen van een diagnose-of beveiligings script.

Als u een actie wilt instellen, gebruikt u de opdracht door gaan (c) om het script af te sluiten en een `Remove-PsBreakpoint` opdracht om het huidige onderbrekings punt te verwijderen. (Onderbrekings punten zijn alleen-lezen, dus u kunt geen actie aan het huidige onderbrekings punt toevoegen.)

```powershell
DBG> c
Windows PowerShell 2.0
Have you run a background job today (start-job)?
Done C:\ps-test\test.ps1

PS C:\ps-test> Get-PSBreakpoint| Remove-PSBreakpoint
PS C:\ps-test>
```

Maak nu een nieuwe opdracht onderbrekings punt met een actie. Met de volgende opdracht wordt een opdracht onderbrekings punt ingesteld met een actie waarmee de waarde van de `$scriptName` variabele wordt geregistreerd wanneer de functie wordt aangeroepen. Omdat het sleutel woord einde niet wordt gebruikt in de actie, wordt de uitvoering niet gestopt. (De apostroffen (') is het regel vervolg teken.)

```powershell
PS C:\ps-test> Set-PSBreakpoint -command psversion -script test.ps1  `
-action { add-content "The value of `$scriptName is $scriptName." `
-path action.log}
```

U kunt ook acties toevoegen die voor waarden voor het onderbrekings punt instellen. In de volgende opdracht wordt het onderbrekings punt voor opdrachten alleen uitgevoerd als het uitvoerings beleid is ingesteld op RemoteSigned, het meest beperkende beleid dat nog steeds in staat is om scripts uit te voeren. (De apostroffen (') is het voortzettings teken.)

```powershell
PS C:\ps-test> Set-PSBreakpoint -script test.ps1 -command psversion `
-action { if ((Get-ExecutionPolicy) -eq "RemoteSigned") { break }}
```

Met het sleutel woord break in de actie wordt het fout opsporingsprogramma doorgestuurd om het onderbrekings punt uit te voeren.
U kunt ook het sleutel woord continue gebruiken om het fout opsporingsprogramma te laten uitvoeren zonder te verbreken. Omdat het sleutel woord default wordt voortgezet, moet u onderbreken opgeven om de uitvoering te stoppen.

Voer nu het script uit.

```powershell
PS C:\ps-test> .\test.ps1
Hit Command breakpoint on 'C:\ps-test\test.ps1:psversion'

test.ps1:12  psversion
```

Omdat het uitvoerings beleid is ingesteld op **RemoteSigned** , wordt de uitvoering gestopt bij de functie aanroep.

Op dit moment kunt u de aanroep stack controleren. Gebruik de `Get-PsCallStack` cmdlet of de `Get-PsCallStack` debugger opdracht (k). Met de volgende opdracht wordt de huidige aanroep stack opgehaald.

```powershell
DBG> k
2: prompt
1: .\test.ps1: $args=[]
0: prompt: $args=[]
```

In dit voor beeld ziet u slechts enkele van de vele manieren waarop u het Power Shell-fout opsporingsprogramma kunt gebruiken.

Voor meer informatie over de cmdlets voor fout opsporing typt u de volgende opdracht:

```powershell
help <cmdlet-name> -full
```

Typ bijvoorbeeld:

```powershell
help Set-PSBreakpoint -full
```

## <a name="other-debugging-features-in-powershell"></a>Andere functies voor fout opsporing in Power shell

Naast de Power Shell-fout opsporing bevat Power shell diverse andere functies die u kunt gebruiken om fouten in scripts en functies op te sporen.

- Windows PowerShell ISE bevat een interactief grafisch fout opsporingsprogramma. Start Windows PowerShell ISE en druk op F1 voor meer informatie.

- De `Set-PSDebug` cmdlet biedt zeer eenvoudige script functies voor fout opsporing, waaronder steping en tracering.

- Gebruik de `Set-StrictMode` cmdlet voor het detecteren van verwijzingen naar niet-geïnitialiseerde variabelen, verwijzingen naar niet-bestaande eigenschappen van een object en de syntaxis van de functie die ongeldig is.

- Voeg diagnostische instructies toe aan een script, zoals instructies voor het weer geven van de waarde van variabelen, instructies die invoer lezen van de opdracht regel of instructies die de huidige instructie rapporteren. Gebruik de cmdlets die de schrijf bewerking voor deze taak bevatten, zoals `Write-Host` ,, `Write-Debug` en `Write-Warning` `Write-Verbose` .

## <a name="see-also"></a>ZIE OOK

- [Disable-PsBreakpoint](xref:Microsoft.PowerShell.Utility.Disable-PSBreakpoint)
- [Enable-PsBreakpoint](xref:Microsoft.PowerShell.Utility.Enable-PSBreakpoint)
- [Get-PsBreakpoint](xref:Microsoft.PowerShell.Utility.Get-PSBreakpoint)
- [Get-PsCallStack](xref:Microsoft.PowerShell.Utility.Get-PSCallStack)
- [Remove-PsBreakpoint](xref:Microsoft.PowerShell.Utility.Remove-PSBreakpoint)
- [Set-PSBreakpoint](xref:Microsoft.PowerShell.Utility.Set-PSBreakpoint)
- [Schrijf fouten opsporen](xref:Microsoft.PowerShell.Utility.Write-Debug)
- [Write-verbose](xref:Microsoft.PowerShell.Utility.Write-Verbose)

