---
title: Het Help-systeem
description: Het model leren van het Help-systeem is de sleutel om met Power shell te kunnen slagen.
ms.date: 06/02/2020
ms.topic: guide
ms.custom: Contributor-mikefrobbins
ms.reviewer: mirobb
ms.openlocfilehash: 8325a32ad8ec137781300e9d46cab52705f0805a
ms.sourcegitcommit: eaac7af89171379df2e20464ebee9fc7e7d7674a
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 09/05/2020
ms.locfileid: "89493654"
---
# <a name="chapter-2---the-help-system"></a>Hoofd stuk 2: het Help-systeem

Er zijn twee groepen IT-professionals die een geschreven test hebben ontvangen zonder toegang tot een computer om het niveau van hun vaardig heden te bepalen met Power shell. Beginners van Power shell zijn in één groep en experts in een ander opgenomen.
Op basis van de resultaten van de test lijkt het niet veel verschil in het vaardigheids niveau tussen de twee groepen. Beide groepen hebben een tweede test gegeven die vergelijkbaar is met die van de eerste. Deze keer werd toegang verleend tot een computer met Power shell die geen toegang tot internet heeft. De resultaten van de tweede test hebben een enorme verschillen in het vaardigheids niveau tussen de twee groepen. Experts kennen niet altijd de antwoorden, maar ze weten hoe ze de antwoorden kunnen achterhalen.

Wat is het verschil in de resultaten van de eerste en tweede test tussen deze twee groepen?

De verschillen die in deze twee tests worden waargenomen, waren omdat experts niet weten hoe duizenden opdrachten in Power shell moeten worden gebruikt. Ze leren hoe het Help-systeem in Power shell extreem goed kan worden gebruikt.
Op die manier kunnen ze de benodigde opdrachten vinden wanneer dat nodig is en hoe deze opdrachten kunnen worden gebruikt wanneer ze ze hebben gevonden.

Ik heb Jeffrey Snover, de voor Raad van Power shell, een aantal keren een vergelijkbaar verhaal.

Het model leren van het Help-systeem is de sleutel om met Power shell te kunnen slagen.

## <a name="discoverability"></a>Detectie

Gecompileerde opdrachten in Power shell worden cmdlets genoemd. De cmdlet is uitgesp roken met opdracht-Let (niet CMD-Let). Namen van cmdlets hebben de vorm van enkelvoudige ' verb-'-opdrachten om ze gemakkelijk te kunnen detecteren. De cmdlet voor het bepalen van de uitvoering van de processen is bijvoorbeeld `Get-Process` en de cmdlet voor het ophalen van een lijst met Services en hun status `Get-Service` . Er zijn andere soorten opdrachten in Power shell, zoals aliassen en functies die verderop in dit boek worden behandeld. De term Power shell-opdracht is een algemene term die vaak wordt gebruikt om te verwijzen naar een wille keurig type opdracht in Power shell, ongeacht of het een cmdlet, functie of alias is.

## <a name="the-three-core-cmdlets-in-powershell"></a>De drie kern-cmdlets in Power shell

- `Get-Command`
- `Get-Help`
- `Get-Member` (bedoeld in hoofd stuk 3)

Hoe weet ik vaak hoe snel u weet wat de opdrachten zijn in Power shell? Beide `Get-Command` en `Get-Help` kunnen worden gebruikt om de opdrachten te bepalen.

## <a name="get-help"></a>Get-Help

`Get-Help` is een opdracht voor meerdere doel einden. `Get-Help` helpt u bij het gebruik van opdrachten nadat u ze hebt gevonden. `Get-Help` kan ook worden gebruikt om opdrachten te vinden, maar op een andere en meer indirecte wijze in vergelijking tot `Get-Command` .

Wanneer `Get-Help` wordt gebruikt om opdrachten te vinden, zoekt het eerst naar Joker tekens die overeenkomen met de opdracht namen op basis van de opgegeven invoer. Als er geen overeenkomst wordt gevonden, wordt gezocht in de Help-onderwerpen zelf. als er geen overeenkomst wordt gevonden, wordt er een fout geretourneerd. In tegens telling tot populaire geloofs `Get-Help` kan worden gebruikt om opdrachten te vinden die geen Help-onderwerpen bevatten.

Het eerste wat u moet weten over het Help-systeem in Power shell is het gebruik van de `Get-Help` cmdlet. De volgende opdracht wordt gebruikt om het Help-onderwerp voor weer te geven `Get-Help` .

```powershell
Get-Help -Name Get-Help
```

```Output
Do you want to run Update-Help?
The Update-Help cmdlet downloads the most current Help files for Windows PowerShell
modules, and installs them on your computer. For more information about the Update-Help
cmdlet, see http://go.microsoft.com/fwlink/?LinkId=210614.
[Y] Yes  [N] No  [S] Suspend  [?] Help (default is "Y"):
```

Vanaf Power shell versie 3 wordt de Power shell-Help niet geleverd bij het besturings systeem. De eerste keer dat `Get-Help` voor een opdracht wordt uitgevoerd, wordt het vorige bericht weer gegeven. Als de `help` functie of `man` alias wordt gebruikt in plaats van de `Get-Help` cmdlet, wordt dit bericht niet weer gegeven.

Als u Ja antwoordt door op <kbd>Y</kbd> wordt de `Update-Help` cmdlet uit te voeren. hiervoor is standaard Internet toegang vereist. `Y` kan worden opgegeven in een hoofd-of kleine letter.

Zodra de Help is gedownload en de update is voltooid, wordt het Help-onderwerp geretourneerd voor de opgegeven opdracht:

```powershell
Get-Help -Name Get-Help
```

Neem even de tijd om dit voor beeld uit te voeren op uw computer, Bekijk de uitvoer en Let op hoe de gegevens worden gegroepeerd:

- NAAM
- SAMENVATTING
- SYNTAXIS
- BESCHRIJVING
- GERELATEERDE KOPPELINGEN
- OPMERKINGEN

Zoals u kunt zien, kunnen Help-onderwerpen een enorme hoeveelheid informatie bevatten, maar dit is niet het volledige Help-onderwerp.

Hoewel het niet specifiek is voor Power shell, is een para meter een manier om invoer te leveren aan een opdracht. `Get-Help` heeft veel para meters die kunnen worden opgegeven om het volledige Help-onderwerp of een subset ervan te retour neren.

De sectie syntaxis van het Help-onderwerp dat wordt weer gegeven in de vorige set met resultaten bevat een lijst met alle para meters voor `Get-Help` . Op het eerste gezicht ziet u dezelfde para meters die zes verschillende tijdstippen worden weer gegeven. Elk van deze verschillende blokken in de syntaxis sectie is een parameterset. Dit betekent dat de `Get-Help` cmdlet zes verschillende parameter sets heeft. Als u een kijkje neemt, ziet u dat ten minste één para meter in elk van de parameter sets anders is.

Parameter sets sluiten elkaar wederzijds uit. Wanneer een unieke para meter die alleen in een van de parameter sets voor komt, wordt gebruikt, kunnen alleen para meters in die set para meters worden gebruikt. Zo kunnen zowel de **volledige** als de **gedetailleerde** para meters op hetzelfde moment niet worden opgegeven omdat ze zich in verschillende parameter sets bevinden.

Elk van de volgende para meters bevinden zich in verschillende parameter sets:

- Volledig
- Gedetailleerd
- Voorbeelden
- Online
- Parameter
- ShowWindow

Alle cryptische syntaxis, zoals vier Kante en punt haken in de syntaxis sectie, betekent iets, maar wordt wel behandeld in bijlage A van dit boek. Het is belang rijk dat u leert hoe de cryptische syntaxis vaak moeilijk te bewaren is voor iemand die geen ervaring heeft met Power shell en deze mogelijk niet dagelijks gebruikt.

Zie [bijlage A][]voor meer informatie over het beter begrijpen van de cryptische syntaxis.

Voor beginners is er een eenvoudige manier om dezelfde informatie te achterhalen, behalve in de taal normaal.

Wanneer de **volledige** para meter van `Get-Help` is opgegeven, wordt het volledige Help-onderwerp geretourneerd.

```powershell
Get-Help -Name Get-Help -Full
```

Neem even de tijd om dit voor beeld uit te voeren op uw computer, Bekijk de uitvoer en Let op hoe de gegevens worden gegroepeerd:

- NAAM
- SAMENVATTING
- SYNTAXIS
- BESCHRIJVING
- PARAMETERS
- INVOER
- UITVOER
- OPMERKINGEN
- VOORBEELDEN
- GERELATEERDE KOPPELINGEN

U ziet dat met behulp van de **volledige** para meter verschillende extra secties zijn geretourneerd, een van de para meters die meer informatie bevat dan de sectie cryptische syntaxis.

De **volledige** para meter is een switch parameter. Een para meter waarvoor geen waarde is vereist, wordt een switch parameter genoemd. Wanneer een switch parameter wordt opgegeven, is de waarde True en wanneer dit niet het geval is, is de waarde false.

Als u dit hoofd stuk in de Power shell-console hebt door lopen, hebt u opgemerkt dat de vorige opdracht om het volledige Help-onderwerp voor vloog weer te geven `Get-Help` op het scherm, zonder dat u de kans krijgt om het te lezen. Er is een betere manier.

`Help` is een functie die pipet `Get-Help` naar een functie met `more` de naam, een wrapper voor het `more.com` uitvoer bare bestand in Windows. In de Power shell-console `help` biedt één pagina met Help per keer. In de ISE werkt het op dezelfde manier als `Get-Help` . Mijn aanbeveling is de functie te gebruiken `help` in plaats van de `Get-Help` cmdlet, omdat het een betere ervaring biedt en het minder is om te typen.

Minder typen zijn echter niet altijd goed. Als u uw opdrachten wilt opslaan als een script of ze wilt delen met iemand anders, moet u volledige cmdlet-en parameter namen gebruiken. De volledige namen zijn zelf gedocumenteerd, waardoor ze gemakkelijker te begrijpen zijn. Denk aan de volgende persoon die uw opdrachten moet lezen en begrijpen. U kunt dit ook doen. Uw collega's en de toekomst zullen u bedanken.

Voer de volgende opdrachten uit in de Power shell-console op de computer met de Windows 10-test omgeving.

```powershell
Get-Help -Name Get-Help -Full
help -Name Get-Help -Full
help Get-Help -Full
```

Hebt u de verschillen in de uitvoer van de eerder vermelde opdrachten genoteerd toen u ze op de computer met Windows 10 lab-omgeving werd uitgevoerd?

Er zijn geen verschillen tussen de laatste twee opties en retour neren de resultaten één pagina per keer.
De <kbd>spatie balk</kbd> wordt gebruikt om de volgende pagina met inhoud weer te geven wanneer u de `Help` functie gebruikt en <kbd>CTRL</kbd> + <kbd>C</kbd> opdrachten die in de Power shell-console worden uitgevoerd, worden geannuleerd.

In het eerste voor beeld wordt de `Get-Help` cmdlet gebruikt, de tweede gebruikt de `Help` functie en de derde para meter voor de **naam** weglaat wanneer u de `Help` functie gebruikt. **Name** is een positionele para meter en wordt positioneel in dit voor beeld gebruikt. Dit betekent dat de waarde kan worden opgegeven zonder de parameter naam op te geven, zolang de waarde zelf is opgegeven op de juiste positie. Hoe weet ik op welke positie de waarde moet worden opgegeven? Lees de Help, zoals wordt weer gegeven in het volgende voor beeld.

```powershell
help Get-Help -Parameter Name
```

```Output
-Name <String>
    Gets help about the specified command or concept. Enter the name of a cmdlet, function,
    provider, script, or workflow, such as Get-Member, a conceptual article name, such as
    about_Objects, or an alias, such as ls. Wildcard characters are permitted in cmdlet and
    provider names, but you can't use wildcard characters to find the names of function help and
    script help articles.

    To get help for a script that isn't located in a path that's listed in the $env:Path
    environment variable, type the script's path and file name.

    If you enter the exact name of a help article, Get-Help displays the article contents.

    If you enter a word or word pattern that appears in several help article titles, Get-Help
    displays a list of the matching titles.

    If you enter a word that doesn't match any help article titles, Get-Help displays a list of
    articles that include that word in their contents.

    The names of conceptual articles, such as about_Objects, must be entered in English, even in
    non-English versions of PowerShell.

    Required?                    false
    Position?                    0
    Default value                None
    Accept pipeline input?       True (ByPropertyName)
    Accept wildcard characters?  true
```

In het vorige voor beeld is de **parameter** parameter met de Help-functie gebruikt om alleen informatie uit het Help-onderwerp voor de para meter **name** te retour neren. Dit is veel beknopter dan het hand matig gebruiken van een honderd pagina Help-onderwerp.

Op basis van deze resultaten kunt u zien dat de para meter **name** positioneel is en moet u deze opgeven in positie nul (de eerste positie) wanneer u positioneel gebruikt. De volg orde waarin para meters worden opgegeven, is niet van belang als de parameter naam is opgegeven.

Een andere belang rijke informatie is dat de para meter **name** verwacht dat het gegevens type voor de waarde een enkele teken reeks is, die wordt aangeduid door `<String>` . Als er meerdere teken reeksen zijn geaccepteerd, wordt het gegevens type weer gegeven als `<String[]>` .

Soms wilt u alleen het volledige Help-onderwerp voor een opdracht weer geven. Er zijn een aantal andere para meters behalve de **volledige** waarde die kan worden opgegeven met `Get-Help` of `Help` . Voer de volgende opdrachten uit op de computer met de Windows 10-test omgeving:

```powershell
Get-Help -Name Get-Command -Full
Get-Help -Name Get-Command -Detailed
Get-Help -Name Get-Command -Examples
Get-Help -Name Get-Command -Online
Get-Help -Name Get-Command -Parameter Noun
Get-Help -Name Get-Command -ShowWindow
```

Ik gebruik normaal gesp roken `help <command name>` met de **volledige** of **online** -para meter. Als ik alleen geïnteresseerd in de voor beelden, gebruik ik de **voor beelden** van de para meter en als ik alleen in een specifieke para meter geïnteresseerd ben, gebruik **ik de para meter parameter.** De **ShowWindow** -para meter opent u het Help-onderwerp in een afzonderlijk Zoek venster dat kan worden geplaatst op een andere monitor als u meerdere monitors hebt. Ik heb de **ShowWindow** -para meter vermeden, omdat er een bekende fout is waarbij het volledige Help-onderwerp niet wordt weer gegeven.

Als u hulp nodig hebt in een afzonderlijk venster, is het raadzaam om de para meter **online** te gebruiken of de **volledige** para meter te gebruiken en de resultaten door te sluizen naar `Out-GridView` , zoals in het volgende voor beeld wordt weer gegeven.

```powershell
help Get-Command -Full | Out-GridView
```

Zowel de `Out-GridView` cmdlet als de **ShowWindow** -para meter van de `Get-Help` cmdlet vereisen een besturings systeem met een GUI (grafische gebruikers interface). Er wordt een fout bericht gegenereerd als u probeert een van beide te gebruiken op een Windows-Server die is geïnstalleerd met behulp van de Server Core-installatie optie (no-GUI).

Als u `Get-Help` wilt gebruiken om opdrachten te vinden, gebruikt u het `*` Joker teken asterisk () met de **naam** parameter. Geef een term op die u zoekt naar opdrachten als de waarde voor de para meter **name** , zoals wordt weer gegeven in het volgende voor beeld.

```powershell
help *process*
```

```Output
Name                              Category  Module                    Synopsis
----                              --------  ------                    --------
Enter-PSHostProcess               Cmdlet    Microsoft.PowerShell.Core Connects to and ...
Exit-PSHostProcess                Cmdlet    Microsoft.PowerShell.Core Closes an intera...
Get-PSHostProcessInfo             Cmdlet    Microsoft.PowerShell.Core
Debug-Process                     Cmdlet    Microsoft.PowerShell.M... Debugs one or mo...
Get-Process                       Cmdlet    Microsoft.PowerShell.M... Gets the process...
Start-Process                     Cmdlet    Microsoft.PowerShell.M... Starts one or mo...
Stop-Process                      Cmdlet    Microsoft.PowerShell.M... Stops one or mor...
Wait-Process                      Cmdlet    Microsoft.PowerShell.M... Waits for the pr...
Get-AppvVirtualProcess            Function  AppvClient                ...
Start-AppvVirtualProcess          Function  AppvClient                ...
```

In het vorige voor beeld `*` zijn de joker tekens niet vereist en wordt het weglaten van hetzelfde resultaat. `Get-Help` voegt automatisch de joker tekens achter de schermen toe.

```powershell
help process
```

Met de vorige opdracht worden dezelfde resultaten gegenereerd als het `*` Joker teken opgeven aan elk einde van het proces.

Ik wil ze liever toevoegen omdat dit de optie is die altijd consistent werkt. Anders zijn ze vereist in bepaalde scenario's en niet op andere. Zodra u een Joker teken aan het midden van de waarde toevoegt, worden deze niet meer automatisch achter de schermen toegevoegd aan de waarde die u hebt opgegeven.

```powershell
help pr*cess
```

Met deze opdracht worden geen resultaten geretourneerd, tenzij het `*` Joker teken wordt toegevoegd aan het begin, het einde of aan het begin en het einde van `pr*cess` .

Als de waarde die u hebt opgegeven begint met een streepje, wordt er een fout gegenereerd omdat Power shell deze als parameter naam interpreteert en er geen parameter naam bestaat voor de `Get-Help` cmdlet.

```powershell
help -process
```

Als u wilt zoeken naar opdrachten die eindigen op `-process` , hoeft u alleen het `*` Joker teken aan het begin van de waarde toe te voegen.

```powershell
help *-process
```

Wanneer u Power shell-opdrachten zoekt met `Get-Help` , wilt u nog iets meer vague in plaats van te specifiek voor wat u zoekt.

Zoeken naar `process` eerder gevonden alleen opdrachten die zijn opgenomen `process` in de naam van de opdracht en alleen die resultaten retour neren. Wanneer `Get-Help` wordt gebruikt om te zoeken, worden er geen `processes` overeenkomsten voor opdracht namen gevonden, zodat er een zoek opdracht wordt uitgevoerd in elk Help-onderwerp in Power shell op uw systeem en er gevonden overeenkomsten worden weer gegeven. Dit leidt ertoe dat er een enorm aantal resultaten wordt geretourneerd.

```powershell
Get-Help processes
```

```Output
Name                              Category  Module                    Synopsis
----                              --------  ------                    --------
Disconnect-PSSession              Cmdlet    Microsoft.PowerShell.Core Disconnects from...
Enter-PSHostProcess               Cmdlet    Microsoft.PowerShell.Core Connects to and ...
ForEach-Object                    Cmdlet    Microsoft.PowerShell.Core Performs an oper...
Get-PSSessionConfiguration        Cmdlet    Microsoft.PowerShell.Core Gets the registe...
New-PSTransportOption             Cmdlet    Microsoft.PowerShell.Core Creates an objec...
Out-Host                          Cmdlet    Microsoft.PowerShell.Core Sends output to ...
Where-Object                      Cmdlet    Microsoft.PowerShell.Core Selects objects ...
Clear-Variable                    Cmdlet    Microsoft.PowerShell.U... Deletes the valu...
Compare-Object                    Cmdlet    Microsoft.PowerShell.U... Compares two set...
Convert-String                    Cmdlet    Microsoft.PowerShell.U... Formats a string...
ConvertFrom-Csv                   Cmdlet    Microsoft.PowerShell.U... Converts object ...
ConvertTo-Html                    Cmdlet    Microsoft.PowerShell.U... Converts Microso...
ConvertTo-Xml                     Cmdlet    Microsoft.PowerShell.U... Creates an XML-b...
Debug-Runspace                    Cmdlet    Microsoft.PowerShell.U... Starts an intera...
Export-Csv                        Cmdlet    Microsoft.PowerShell.U... Converts objects...
Export-FormatData                 Cmdlet    Microsoft.PowerShell.U... Saves formatting...
Format-List                       Cmdlet    Microsoft.PowerShell.U... Formats the outp...
Format-Table                      Cmdlet    Microsoft.PowerShell.U... Formats the outp...
Get-Random                        Cmdlet    Microsoft.PowerShell.U... Gets a random nu...
Get-Unique                        Cmdlet    Microsoft.PowerShell.U... Returns unique i...
Group-Object                      Cmdlet    Microsoft.PowerShell.U... Groups objects t...
Import-Clixml                     Cmdlet    Microsoft.PowerShell.U... Imports a CLIXML...
Import-Csv                        Cmdlet    Microsoft.PowerShell.U... Creates table-li...
Measure-Object                    Cmdlet    Microsoft.PowerShell.U... Calculates the n...
Out-File                          Cmdlet    Microsoft.PowerShell.U... Sends output to ...
Out-GridView                      Cmdlet    Microsoft.PowerShell.U... Sends output to ...
Select-Object                     Cmdlet    Microsoft.PowerShell.U... Selects objects ...
Set-Variable                      Cmdlet    Microsoft.PowerShell.U... Sets the value o...
Sort-Object                       Cmdlet    Microsoft.PowerShell.U... Sorts objects by...
Tee-Object                        Cmdlet    Microsoft.PowerShell.U... Saves command ou...
Trace-Command                     Cmdlet    Microsoft.PowerShell.U... Configures and s...
Write-Output                      Cmdlet    Microsoft.PowerShell.U... Sends the specif...
Debug-Process                     Cmdlet    Microsoft.PowerShell.M... Debugs one or mo...
Get-Process                       Cmdlet    Microsoft.PowerShell.M... Gets the process...
Get-WmiObject                     Cmdlet    Microsoft.PowerShell.M... Gets instances o...
Start-Process                     Cmdlet    Microsoft.PowerShell.M... Starts one or mo...
Stop-Process                      Cmdlet    Microsoft.PowerShell.M... Stops one or mor...
Wait-Process                      Cmdlet    Microsoft.PowerShell.M... Waits for the pr...
Get-Counter                       Cmdlet    Microsoft.PowerShell.D... Gets performance...
Invoke-WSManAction                Cmdlet    Microsoft.WSMan.Manage... Invokes an actio...
Remove-WSManInstance              Cmdlet    Microsoft.WSMan.Manage... Deletes a manage...
Get-WSManInstance                 Cmdlet    Microsoft.WSMan.Manage... Displays managem...
New-WSManInstance                 Cmdlet    Microsoft.WSMan.Manage... Creates a new in...
Set-WSManInstance                 Cmdlet    Microsoft.WSMan.Manage... Modifies the man...
about_Arithmetic_Operators        HelpFile                            Describes the op...
about_Arrays                      HelpFile                            Describes arrays...
about_Debuggers                   HelpFile                            Describes the Wi...
about_Execution_Policies          HelpFile                            Describes the Wi...
about_ForEach-Parallel            HelpFile                            Describes the Fo...
about_Foreach                     HelpFile                            Describes a lang...
about_Functions                   HelpFile                            Describes how to...
about_Language_Keywords           HelpFile                            Describes the ke...
about_Methods                     HelpFile                            Describes how to...
about_Objects                     HelpFile                            Provides essenti...
about_Parallel                    HelpFile                            Describes the Pa...
about_Pipelines                   HelpFile                            Combining comman...
about_Preference_Variables        HelpFile                            Variables that c...
about_Remote                      HelpFile                            Describes how to...
about_Remote_Output               HelpFile                            Describes how to...
about_Sequence                    HelpFile                            Describes the Se...
about_Session_Configuration_Files HelpFile                            Describes sessio...
about_Variables                   HelpFile                            Describes how va...
about_Windows_PowerShell_5.0      HelpFile                            Describes new fe...
about_WQL                         HelpFile                            Describes WMI Qu...
about_WS-Management_Cmdlets       HelpFile                            Provides an over...
about_ForEach-Parallel            HelpFile                            Describes the Fo...
about_Parallel                    HelpFile                            Describes the Pa...
about_Sequence                    HelpFile                            Describes the Se...
```

Gebruiken `Help` om te zoeken naar `process` geretourneerde 10 resultaten en om te zoeken naar `processes` geretourneerde 68-resultaten. Als er slechts één resultaat wordt gevonden, wordt het Help-onderwerp zelf weer gegeven in plaats van een lijst met opdrachten.

```powershell
get-help *hotfix*
```

```Output
NAME
    Get-HotFix

SYNOPSIS
    Gets the hotfixes that have been applied to the local and remote computers.


SYNTAX
    Get-HotFix [-ComputerName <String[]>] [-Credential <PSCredential>] [-Description
    <String[]>] [<CommonParameters>]

    Get-HotFix [[-Id] <String[]>] [-ComputerName <String[]>] [-Credential
    <PSCredential>] [<CommonParameters>]


DESCRIPTION
    The Get-Hotfix cmdlet gets hotfixes (also called updates) that have been installed
    on either the local computer (or on specified remote computers) by Windows Update,
    Microsoft Update, or Windows Server Update Services; the cmdlet also gets hotfixes
    or updates that have been installed manually by users.


RELATED LINKS
    Online Version: http://go.microsoft.com/fwlink/?LinkId=821586
    Win32_QuickFixEngineering http://go.microsoft.com/fwlink/?LinkID=145071
    Get-ComputerRestorePoint
    Add-Content

REMARKS
    To see the examples, type: "get-help Get-HotFix -examples".
    For more information, type: "get-help Get-HotFix -detailed".
    For technical information, type: "get-help Get-HotFix -full".
    For online help, type: "get-help Get-HotFix -online"
```

Nu debunk u de mythe die `Help` in Power shell alleen opdrachten kan vinden die Help-onderwerpen bevatten.

```powershell
help *more*
```

```Output
NAME
    more

SYNTAX
    more [[-paths] <string[]>]


ALIASES
    None


REMARKS
    None
```

U ziet in het vorige voor beeld dat `more` geen Help-onderwerp is, maar het `Help` systeem in Power shell kon het niet vinden. Er is slechts één overeenkomst gevonden die overeenkomt met de basis informatie over de syntaxis die wordt weer gegeven wanneer een opdracht geen Help-onderwerp heeft.

Power shell bevat talloze conceptuele Help-onderwerpen. De volgende opdracht kan worden gebruikt om een lijst met alle Help-onderwerpen op uw **systeem te retour** neren.

```powershell
help About_*
```

Als u de resultaten beperkt tot één Help-onderwerp, wordt het werkelijke Help-onderwerp weer gegeven in plaats van een lijst te retour neren.

```powershell
help about_Updatable_Help
```

Het Help-systeem in Power shell moet worden bijgewerkt zodat **de Help-** onderwerpen aanwezig zijn. Als de eerste update van het Help-systeem op uw computer is mislukt, zijn de bestanden niet beschikbaar totdat de cmdlet is `Update-Help` uitgevoerd.

## <a name="get-command"></a>Get-Command

`Get-Command` is ontworpen om u te helpen bij het vinden van opdrachten. `Get-Command`Als u zonder para meters uitvoert, wordt een lijst met alle opdrachten op het systeem geretourneerd. In het volgende voor beeld ziet u hoe u de `Get-Command` cmdlet gebruikt om te bepalen welke opdrachten bestaan voor het werken met processen:

```powershell
Get-Command -Noun Process
```

```Output
CommandType     Name                                               Version    Source
-----------     ----                                               -------    ------
Cmdlet          Debug-Process                                      3.1.0.0    Microsof...
Cmdlet          Get-Process                                        3.1.0.0    Microsof...
Cmdlet          Start-Process                                      3.1.0.0    Microsof...
Cmdlet          Stop-Process                                       3.1.0.0    Microsof...
Cmdlet          Wait-Process                                       3.1.0.0    Microsof...
```

In het vorige voor beeld waar `Get-Command` is uitgevoerd, wordt de para meter **zelfstandig** gebruikt en `Process` wordt deze opgegeven als de waarde voor de para meter **zelfstandig** . Wat als u niet weet hoe u de cmdlet moet gebruiken `Get-Command` ? U kunt gebruiken `Get-Help` om het Help-onderwerp voor weer te geven `Get-Command` .

De para meters **name**, zelfstandig naam **woord**en **Verb** accepteren joker tekens. In het volgende voor beeld ziet u Joker tekens die worden gebruikt met de para meter **name** :

```Output
Get-Command -Name *service*
```

```powershell
CommandType     Name                                               Version    Source
-----------     ----                                               -------    ------
Function        Get-NetFirewallServiceFilter                       2.0.0.0    NetSecurity
Function        Set-NetFirewallServiceFilter                       2.0.0.0    NetSecurity
Cmdlet          Get-Service                                        3.1.0.0    Microsof...
Cmdlet          New-Service                                        3.1.0.0    Microsof...
Cmdlet          New-WebServiceProxy                                3.1.0.0    Microsof...
Cmdlet          Restart-Service                                    3.1.0.0    Microsof...
Cmdlet          Resume-Service                                     3.1.0.0    Microsof...
Cmdlet          Set-Service                                        3.1.0.0    Microsof...
Cmdlet          Start-Service                                      3.1.0.0    Microsof...
Cmdlet          Stop-Service                                       3.1.0.0    Microsof...
Cmdlet          Suspend-Service                                    3.1.0.0    Microsof...
Application     AgentService.exe                                   10.0.14... C:\Windo...
Application     SensorDataService.exe                              10.0.14... C:\Windo...
Application     services.exe                                       10.0.14... C:\Windo...
Application     services.msc                                       0.0.0.0    C:\Windo...
Application     TieringEngineService.exe                           10.0.14... C:\Windo...
```

Ik ben geen ventilator van het gebruik van joker tekens met de para meter **name** van `Get-Command` , omdat deze ook uitvoer bare bestanden retourneert die geen systeem eigen Power shell-opdrachten zijn.

Als u Joker tekens wilt gebruiken met de para meter **name** , raden we u aan de resultaten te beperken met de para meter **CommandType** .

```powershell
Get-Command -Name *service* -CommandType Cmdlet, Function, Alias
```

Een betere optie is het gebruik van ofwel het **woord** of de **zelfstandig** para meter, omdat alleen Power shell-opdrachten beide werk woorden en zelfstandige naam woorden hebben.

Is er iets mis met een Help-onderwerp? Het goede nieuws is de Help-onderwerpen voor Power shell zijn geopend en beschikbaar in de [Power shell-docs-][] opslag plaats op github. Betaal het voorwaarts door niet alleen de onjuiste informatie voor uzelf te corrigeren, maar ook voor alle andere gebruikers. U hoeft alleen de Power shell-documentatie opslagplaats op GitHub te splitsen, het Help-onderwerp bij te werken en een pull-aanvraag in te dienen.
Zodra de pull-aanvraag is geaccepteerd, is de gecorrigeerde documentatie voor iedereen beschikbaar.

## <a name="updating-help"></a>Help bijwerken

De lokale versie van de Help-onderwerpen voor Power shell is eerder bijgewerkt met de eerste keer dat er een opdracht is aangevraagd. Het is raadzaam om het Help-systeem regel matig bij te werken omdat er van tijd tot tijd updates kunnen zijn voor de Help-inhoud. De `Update-Help` cmdlet wordt gebruikt om de Help-onderwerpen bij te werken.
Hiervoor is Internet toegang vereist en u moet Power shell met verhoogde bevoegdheden uitvoeren als Administrator.

```powershell
Update-Help
```

```Output
Update-Help : Failed to update Help for the module(s) 'BitsTransfer' with UI culture(s)
{en-US} : The value of the HelpInfoUri key in the module manifest must resolve to a
container or root URL on a website where the help files are stored. The HelpInfoUri
'https://technet.microsoft.com/en-us/library/dd819413.aspx' does not resolve to a
container.
At line:1 char:1
+ Update-Help
+
    + CategoryInfo          : InvalidOperation: (:) [Update-Help], Exception
    + FullyQualifiedErrorId : InvalidHelpInfoUri,Microsoft.PowerShell.Commands.UpdateHel
   pCommand

Update-Help : Failed to update Help for the module(s) 'NetworkControllerDiagnostics,
StorageReplica' with UI culture(s) {en-US} : Unable to retrieve the HelpInfo XML file
for UI culture en-US. Make sure the HelpInfoUri property in the module manifest is valid
or check your network connection and then try the command again.
At line:1 char:1
+ Update-Help
+
    + CategoryInfo          : ResourceUnavailable: (:) [Update-Help], Exception
    + FullyQualifiedErrorId : UnableToRetrieveHelpInfoXml,Microsoft.PowerShell.Commands.
   UpdateHelpCommand
```

Enkele van de modules hebben fouten geretourneerd die niet ongebruikelijk zijn. Als de computer geen toegang heeft tot internet, kunt u de `Save-Help` cmdlet gebruiken op een andere computer die toegang heeft tot internet om eerst de bijgewerkte Help-informatie op te slaan in een bestands share op uw netwerk en vervolgens de para meter **SourcePath** van gebruiken `Update-Help` om deze netwerk locatie op te geven voor de Help-onderwerpen.

Overweeg een geplande taak in te stellen of een logica toe te voegen aan uw profiel script in Power shell om regel matig de Help-inhoud op uw computer bij te werken. Profiel scripts worden besproken in een gepland hoofd stuk.

## <a name="summary"></a>Samenvatting

In dit hoofd stuk hebt u geleerd hoe u opdrachten kunt vinden met zowel `Get-Help` als `Get-Command` . U hebt geleerd hoe u het Help-systeem kunt gebruiken om de opdrachten te gebruiken wanneer u ze hebt gevonden. U hebt ook geleerd hoe u de inhoud van de Help-onderwerpen bijwerkt wanneer er updates beschikbaar zijn.

Mijn uitdaging voor u is om een Power shell-opdracht per dag te leren.

```powershell
Get-Command | Get-Random | Get-Help -Full
```

## <a name="review"></a>Beoordelen

1. Is de para meter **DisplayName** van `Get-Service` positioneel?
1. Hoeveel parameter sets heeft de `Get-Process` cmdlet?
1. Welke Power shell-opdrachten bestaan er voor het werken met gebeurtenis logboeken?
1. Wat is de Power shell-opdracht voor het retour neren van een lijst met Power shell-processen die worden uitgevoerd op uw computer?
1. Hoe werkt u de Help-inhoud van Power shell bij die op uw computer is opgeslagen?

## <a name="recommended-reading"></a>Aanbevolen Lees bewerkingen

Als u meer informatie wilt over de onderwerpen die in dit hoofd stuk worden behandeld, raden we u aan de volgende Help-onderwerpen voor Power shell te lezen.

- [Get-Help][]
- [Get-Command][]
- [Update-Help][]
- [Opslaan-Help][]
- [about_Updatable_Help][]
- [about_Command_Syntax][]

In het volgende hoofd stuk vindt u informatie over de `Get-Member` cmdlet en objecten, eigenschappen en methoden.

<!-- link references -->
[Get-Help]: /powershell/module/microsoft.powershell.core/get-help
[Get-Command]: /powershell/module/microsoft.powershell.core/get-command
[Update-Help]: /powershell/module/microsoft.powershell.core/update-help
[Opslaan-Help]: /powershell/module/microsoft.powershell.core/save-help
[about_Updatable_Help]: /powershell/module/microsoft.powershell.core/about/about_updatable_help
[about_Command_Syntax]: /powershell/module/microsoft.powershell.core/about/about_command_syntax
[PowerShell-Docs]: https://github.com/powershell/powershell
[Bijlage A]: appendix-a.md
