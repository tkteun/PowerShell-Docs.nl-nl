---
external help file: System.Management.Automation.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 04/08/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/invoke-command?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Invoke-opdracht
ms.openlocfilehash: da098438e349a338443522816c8dee97fc15f216
ms.sourcegitcommit: 37abf054ad9eda8813be8ff4487803b10e1842ef
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/23/2020
ms.locfileid: "93251630"
---
# Invoke-opdracht

## SAMENVATTING
Voert opdrachten uit op lokale en externe computers.

## SYNTAXIS

### Inproces (standaard)

```
Invoke-Command [-ScriptBlock] <ScriptBlock> [-NoNewScope] [-InputObject <PSObject>]
 [-ArgumentList <Object[]>] [<CommonParameters>]
```

### FilePathRunspace

```
Invoke-Command [[-Session] <PSSession[]>] [-ThrottleLimit <Int32>] [-AsJob] [-HideComputerName]
 [-JobName <String>] [-FilePath] <String> [-RemoteDebug] [-InputObject <PSObject>]
 [-ArgumentList <Object[]>] [<CommonParameters>]
```

### Sessie

```
Invoke-Command [[-Session] <PSSession[]>] [-ThrottleLimit <Int32>] [-AsJob] [-HideComputerName]
 [-JobName <String>] [-ScriptBlock] <ScriptBlock> [-RemoteDebug] [-InputObject <PSObject>]
 [-ArgumentList <Object[]>] [<CommonParameters>]
```

### FilePathComputerName

```
Invoke-Command [[-ComputerName] <String[]>] [-Credential <PSCredential>] [-Port <Int32>] [-UseSSL]
 [-ConfigurationName <String>] [-ApplicationName <String>] [-ThrottleLimit <Int32>] [-AsJob]
 [-InDisconnectedSession] [-SessionName <String[]>] [-HideComputerName] [-JobName <String>]
 [-FilePath] <String> [-SessionOption <PSSessionOption>] [-Authentication <AuthenticationMechanism>]
 [-EnableNetworkAccess] [-RemoteDebug] [-InputObject <PSObject>] [-ArgumentList <Object[]>]
 [<CommonParameters>]
```

### ComputerName

```
Invoke-Command [[-ComputerName] <String[]>] [-Credential <PSCredential>] [-Port <Int32>] [-UseSSL]
 [-ConfigurationName <String>] [-ApplicationName <String>] [-ThrottleLimit <Int32>] [-AsJob]
 [-InDisconnectedSession] [-SessionName <String[]>] [-HideComputerName] [-JobName <String>]
 [-ScriptBlock] <ScriptBlock> [-SessionOption <PSSessionOption>]
 [-Authentication <AuthenticationMechanism>] [-EnableNetworkAccess] [-RemoteDebug]
 [-InputObject <PSObject>] [-ArgumentList <Object[]>] [-CertificateThumbprint <String>]
 [<CommonParameters>]
```

### URI

```
Invoke-Command [-Credential <PSCredential>] [-ConfigurationName <String>] [-ThrottleLimit <Int32>]
 [[-ConnectionUri] <Uri[]>] [-AsJob] [-InDisconnectedSession] [-HideComputerName]
 [-JobName <String>] [-ScriptBlock] <ScriptBlock> [-AllowRedirection]
 [-SessionOption <PSSessionOption>] [-Authentication <AuthenticationMechanism>]
 [-EnableNetworkAccess] [-RemoteDebug] [-InputObject <PSObject>] [-ArgumentList <Object[]>]
 [-CertificateThumbprint <String>] [<CommonParameters>]
```

### FilePathUri

```
Invoke-Command [-Credential <PSCredential>] [-ConfigurationName <String>] [-ThrottleLimit <Int32>]
 [[-ConnectionUri] <Uri[]>] [-AsJob] [-InDisconnectedSession] [-HideComputerName]
 [-JobName <String>] [-FilePath] <String> [-AllowRedirection] [-SessionOption <PSSessionOption>]
 [-Authentication <AuthenticationMechanism>] [-EnableNetworkAccess] [-RemoteDebug]
 [-InputObject <PSObject>] [-ArgumentList <Object[]>] [<CommonParameters>]
```

### VMId

```
Invoke-Command -Credential <PSCredential> [-ConfigurationName <String>] [-ThrottleLimit <Int32>]
 [-AsJob] [-HideComputerName] [-ScriptBlock] <ScriptBlock> [-RemoteDebug] [-InputObject <PSObject>]
 [-ArgumentList <Object[]>] [-VMId] <Guid[]> [<CommonParameters>]
```

### VMName

```
Invoke-Command -Credential <PSCredential> [-ConfigurationName <String>] [-ThrottleLimit <Int32>]
 [-AsJob] [-HideComputerName] [-ScriptBlock] <ScriptBlock> [-RemoteDebug] [-InputObject <PSObject>]
 [-ArgumentList <Object[]>] -VMName <String[]> [<CommonParameters>]
```

### FilePathVMId

```
Invoke-Command -Credential <PSCredential> [-ConfigurationName <String>] [-ThrottleLimit <Int32>]
 [-AsJob] [-HideComputerName] [-FilePath] <String> [-RemoteDebug] [-InputObject <PSObject>]
 [-ArgumentList <Object[]>] [-VMId] <Guid[]> [<CommonParameters>]
```

### FilePathVMName

```
Invoke-Command -Credential <PSCredential> [-ConfigurationName <String>] [-ThrottleLimit <Int32>]
 [-AsJob] [-HideComputerName] [-FilePath] <String> [-RemoteDebug] [-InputObject <PSObject>]
 [-ArgumentList <Object[]>] -VMName <String[]> [<CommonParameters>]
```

### SSHHost

```
Invoke-Command [-Port <Int32>] [-AsJob] [-HideComputerName] [-JobName <String>]
 [-ScriptBlock] <ScriptBlock> -HostName <String[]> [-UserName <String>] [-KeyFilePath <String>]
 [-SSHTransport] [-RemoteDebug] [-InputObject <PSObject>] [-ArgumentList <Object[]>]
 [-Subsystem <String>] [<CommonParameters>]
```

### ContainerId

```
Invoke-Command [-ConfigurationName <String>] [-ThrottleLimit <Int32>] [-AsJob] [-HideComputerName]
 [-JobName <String>] [-ScriptBlock] <ScriptBlock> [-RunAsAdministrator] [-RemoteDebug]
 [-InputObject <PSObject>] [-ArgumentList <Object[]>] -ContainerId <String[]> [<CommonParameters>]
```

### FilePathContainerId

```
Invoke-Command [-ConfigurationName <String>] [-ThrottleLimit <Int32>] [-AsJob] [-HideComputerName]
 [-JobName <String>] [-FilePath] <String> [-RunAsAdministrator] [-RemoteDebug]
 [-InputObject <PSObject>] [-ArgumentList <Object[]>] -ContainerId <String[]> [<CommonParameters>]
```

### SSHHostHashParam

```
Invoke-Command [-AsJob] [-HideComputerName] [-JobName <String>] [-ScriptBlock] <ScriptBlock>
 -SSHConnection <Hashtable[]> [-RemoteDebug] [-InputObject <PSObject>] [-ArgumentList <Object[]>]
 [<CommonParameters>]
```

### FilePathSSHHost

```
Invoke-Command [-AsJob] [-HideComputerName] -FilePath <String> -HostName <String[]>
 [-UserName <String>] [-KeyFilePath <String>] [-SSHTransport] [-RemoteDebug]
 [-InputObject <PSObject>] [-ArgumentList <Object[]>] [<CommonParameters>]
```

### FilePathSSHHostHash

```
Invoke-Command [-AsJob] [-HideComputerName] -FilePath <String> -SSHConnection <Hashtable[]>
 [-RemoteDebug] [-InputObject <PSObject>] [-ArgumentList <Object[]>] [<CommonParameters>]
```

## BESCHRIJVING

De `Invoke-Command` cmdlet voert opdrachten uit op een lokale of externe computer en retourneert alle uitvoer van de opdrachten, met inbegrip van fouten. Met één `Invoke-Command` opdracht kunt u opdrachten uitvoeren op meerdere computers.

Als u één opdracht wilt uitvoeren op een externe computer, gebruikt u de para meter **ComputerName** . Als u een reeks gerelateerde opdrachten wilt uitvoeren die gegevens delen, gebruikt u de `New-PSSession` cmdlet om een **PSSession** (een permanente verbinding) te maken op de externe computer en gebruikt u vervolgens de **sessie** parameter van `Invoke-Command` om de opdracht uit te voeren in de **PSSession**. Als u een opdracht wilt uitvoeren in een sessie zonder verbinding, gebruikt u de para meter **InDisconnectedSession** . Als u een opdracht in een achtergrond taak wilt uitvoeren, gebruikt u de para meter **AsJob** .

U kunt ook `Invoke-Command` op een lokale computer met een script blok als een opdracht. Power Shell voert het script blok onmiddellijk uit in een onderliggend bereik van de huidige scope.

`Invoke-Command`Lees [about_Remote](./About/about_Remote.md)voordat u opdrachten uitvoert op een externe computer.

Vanaf Power shell 6,0 kunt u Secure Shell (SSH) gebruiken om een verbinding te maken met en opdrachten op externe computers aan te roepen. SSH moet worden geïnstalleerd op de lokale computer en de externe computer moet worden geconfigureerd met een Power shell-SSH-eind punt. Het voor deel van een op SSH gebaseerde Power shell-externe sessie is dat deze werkt op meerdere platformen (Windows, Linux, macOS). Voor SSH-sessie gebruikt u de para meter **hostname** of **SSHConnection** om de externe computer en de relevante verbindings gegevens op te geven. Zie voor meer informatie over het instellen van externe toegang tot Power shell [via SSH Power shell](/powershell/scripting/learn/remoting/ssh-remoting-in-powershell-core).

Sommige code voorbeelden gebruiken splatting om de lengte van de lijn te verkleinen. Zie [about_Splatting](./About/about_Splatting.md)voor meer informatie.

## VOORBEELDEN

### Voor beeld 1: een script uitvoeren op een server

In dit voor beeld wordt het `Test.ps1` script op de Server01-computer uitgevoerd.

```powershell
Invoke-Command -FilePath c:\scripts\test.ps1 -ComputerName Server01
```

De **filepath** para meter geeft u een script op dat zich op de lokale computer bevindt. Het script wordt uitgevoerd op de externe computer en de resultaten worden geretourneerd naar de lokale computer.

### Voor beeld 2: een opdracht uitvoeren op een externe server

In dit voor beeld wordt een `Get-Culture` opdracht uitgevoerd op de externe computer Server01.

```powershell
Invoke-Command -ComputerName Server01 -Credential Domain01\User01 -ScriptBlock { Get-Culture }
```

De **ComputerName** para meter geeft de naam van de externe computer. De para meter **Credential** wordt gebruikt om de opdracht uit te voeren in de beveiligings context van Domain01\User01, een gebruiker die gemachtigd is om opdrachten uit te voeren. De **script Block** para meter geeft u de opdracht op die moet worden uitgevoerd op de externe computer.

Als antwoord Power shell vraagt het wacht woord en een verificatie methode voor het gebruiker01-account.
Vervolgens wordt de opdracht op de computer Server01 uitgevoerd en wordt het resultaat geretourneerd.

### Voor beeld 3: een opdracht uitvoeren in een permanente verbinding

In dit voor beeld wordt dezelfde `Get-Culture` opdracht uitgevoerd in een sessie, met behulp van een permanente verbinding op de externe computer met de naam Server02.

```powershell
$s = New-PSSession -ComputerName Server02 -Credential Domain01\User01
Invoke-Command -Session $s -ScriptBlock {Get-Culture}
```

`New-PSSession`Met de cmdlet wordt een sessie gemaakt op de externe computer Server02 en opgeslagen in de `$s` variabele. Normaal gesp roken maakt u alleen een sessie wanneer u een reeks opdrachten op de externe computer uitvoert.

`Invoke-Command`Met de cmdlet wordt de `Get-Culture` opdracht uitgevoerd op Server02. Met de **sessie** parameter wordt de sessie opgegeven die is opgeslagen in de `$s` variabele.

Als antwoord Power Shell voert de opdracht uit in de sessie op de Server02-computer.

### Voor beeld 4: een sessie gebruiken om een reeks opdrachten uit te voeren die gegevens delen

In dit voor beeld worden de gevolgen van **computer naam** en **sessie** parameters van gebruikt `Invoke-Command` . U ziet hoe u een sessie gebruikt om een reeks opdrachten uit te voeren die dezelfde gegevens delen.

```powershell
Invoke-Command -ComputerName Server02 -ScriptBlock {$p = Get-Process PowerShell}
Invoke-Command -ComputerName Server02 -ScriptBlock {$p.VirtualMemorySize}
$s = New-PSSession -ComputerName Server02
Invoke-Command -Session $s -ScriptBlock {$p = Get-Process PowerShell}
Invoke-Command -Session $s -ScriptBlock {$p.VirtualMemorySize}
```

```Output
17930240
```

De eerste twee opdrachten gebruiken de para meter **ComputerName** van `Invoke-Command` om opdrachten uit te voeren op de externe computer Server02. De eerste opdracht gebruikt de `Get-Process` cmdlet om het Power Shell-proces op de externe computer op te halen en om het in de variabele op te slaan `$p` . Met de tweede opdracht wordt de waarde van de eigenschap **VirtualMemorySize** van het Power Shell-proces opgehaald.

Wanneer u de para meter **ComputerName** gebruikt, maakt Power shell een nieuwe sessie om de opdracht uit te voeren.
De sessie wordt gesloten wanneer de opdracht is voltooid. De `$p` variabele is gemaakt in één verbinding, maar bestaat niet in de verbinding die is gemaakt voor de tweede opdracht.

Het probleem wordt opgelost door een permanente sessie te maken op de externe computer en vervolgens beide opdrachten in dezelfde sessie uit te voeren.

Met de `New-PSSession` cmdlet wordt een permanente sessie gemaakt op de computer Server02 en wordt de sessie opgeslagen in de `$s` variabele. `Invoke-Command`Op de regels die volgen, wordt de para meter **Session** gebruikt om beide opdrachten in dezelfde sessie uit te voeren. Omdat beide opdrachten in dezelfde sessie worden uitgevoerd, `$p` blijft de waarde actief.

### Voor beeld 5: Voer een opdracht in die is opgeslagen in een lokale variabele

In dit voor beeld ziet u hoe u een opdracht maakt die is opgeslagen als een script blok in een lokale variabele.
Wanneer het script blok wordt opgeslagen in een lokale variabele, kunt u de variabele opgeven als de waarde van de para meter **script Block** .

```powershell
$command = { Get-WinEvent -LogName PowerShellCore/Operational |
  Where-Object {$_.Message -like "*certificate*"} }
Invoke-Command -ComputerName S1, S2 -ScriptBlock $command
```

De `$command` variabele slaat de `Get-WinEvent` opdracht op die is opgemaakt als een script blok. Hiermee `Invoke-Command` wordt de opdracht uitgevoerd die is opgeslagen in `$command` op de externe computers S1 en S2.

### Voor beeld 6: één opdracht op meerdere computers uitvoeren

In dit voor beeld ziet u hoe u kunt gebruiken `Invoke-Command` om één opdracht op meerdere computers uit te voeren.

```powershell
$parameters = @{
  ComputerName = "Server01", "Server02", "TST-0143", "localhost"
  ConfigurationName = 'MySession.PowerShell'
  ScriptBlock = { Get-WinEvent -LogName PowerShellCore/Operational }
}
Invoke-Command @parameters
```

De para meter **ComputerName** bevat een door komma's gescheiden lijst met computer namen. De lijst met computers bevat de localhost-waarde, die de lokale computer vertegenwoordigt. Met de para meter **configuratiepad** wordt een alternatieve sessie configuratie opgegeven. De para meter **script Block** wordt uitgevoerd `Get-WinEvent` om de PowerShellCore/operationele gebeurtenis logboeken van elke computer op te halen.

### Voor beeld 7: de versie van het hostprogramma op meerdere computers ophalen

In dit voor beeld wordt de versie van het Power shell-host-programma uitgevoerd op 200 externe computers.

```powershell
$version = Invoke-Command -ComputerName (Get-Content Machines.txt) -ScriptBlock {(Get-Host).Version}
```

Omdat er slechts één opdracht wordt uitgevoerd, hoeft u geen permanente verbindingen te maken met elk van de computers. In plaats daarvan gebruikt de opdracht de para meter **ComputerName** om de computers aan te geven. Als u de computers wilt opgeven, wordt de `Get-Content` cmdlet gebruikt om de inhoud van het Machine.txt bestand, een bestand met computer namen, op te halen.

`Invoke-Command`Met de cmdlet wordt een `Get-Host` opdracht op de externe computers uitgevoerd. De teken punt notatie wordt gebruikt om de eigenschap **Version** van de Power shell-host op te halen.

Deze opdrachten worden een voor een uitgevoerd. Wanneer de opdrachten zijn voltooid, wordt de uitvoer van de opdrachten van alle computers in de variabele opgeslagen `$version` . De uitvoer bevat de naam van de computer waarvan de gegevens afkomstig zijn.

### Voor beeld 8: een achtergrond taak op meerdere externe computers uitvoeren

In dit voor beeld wordt een opdracht op twee externe computers uitgevoerd. De `Invoke-Command` opdracht maakt gebruik van de para meter **AsJob** , zodat de opdracht als achtergrond taak wordt uitgevoerd. De opdrachten worden uitgevoerd op de externe computers, maar de taak bestaat op de lokale computer. De resultaten worden verzonden naar de lokale computer.

```powershell
$s = New-PSSession -ComputerName Server01, Server02
Invoke-Command -Session $s -ScriptBlock {Get-EventLog system} -AsJob
```

```Output
Id   Name    State      HasMoreData   Location           Command
---  ----    -----      -----         -----------        ---------------
1    Job1    Running    True          Server01,Server02  Get-EventLog system
```

```powershell
$j = Get-Job
$j | Format-List -Property *
```

```Output
HasMoreData   : True
StatusMessage :
Location      : Server01,Server02
Command       : Get-EventLog system
JobStateInfo  : Running
Finished      : System.Threading.ManualResetEvent
InstanceId    : e124bb59-8cb2-498b-a0d2-2e07d4e030ca
Id            : 1
Name          : Job1
ChildJobs     : {Job2, Job3}
Output        : {}
Error         : {}
Progress      : {}
Verbose       : {}
Debug         : {}
Warning       : {}
StateChanged  :
```

```powershell
$results = $j | Receive-Job
```

De `New-PSSession` cmdlet maakt sessies op de externe computers Server01 en Server02. De `Invoke-Command` cmdlet voert een achtergrond taak in elk van de sessies uit. De opdracht gebruikt de para meter **AsJob** om de opdracht als achtergrond taak uit te voeren. Met deze opdracht wordt een taak object geretourneerd dat twee onderliggende taak objecten bevat, één voor elk van de taken die op de twee externe computers worden uitgevoerd.

De `Get-Job` opdracht slaat het taak object op in de `$j` variabele. De `$j` variabele wordt vervolgens naar de cmdlet geleid `Format-List` om alle eigenschappen van het taak object in een lijst weer te geven. Met de laatste opdracht worden de resultaten van de taken opgehaald. Hiermee wordt het taak object in `$j` naar de `Receive-Job` cmdlet sluizen en worden de resultaten opgeslagen in de `$results` variabele.

### Voor beeld 9: lokale variabelen insluiten in een opdracht die wordt uitgevoerd op een externe computer

In dit voor beeld ziet u hoe u de waarden van lokale variabelen opneemt in een opdracht die wordt uitgevoerd op een externe computer. De opdracht gebruikt de `Using` aanpassings functie van het bereik om een lokale variabele in een externe opdracht te identificeren. Standaard worden alle variabelen geacht te zijn gedefinieerd in de externe sessie. De `Using` aanpassing van het bereik is geïntroduceerd in Power shell 3,0. `Using`Zie [about_Remote_Variables](./About/about_Remote_Variables.md) en [about_Scopes](./about/about_scopes.md)voor meer informatie over de aanpassing van het bereik.

```powershell
$Log = "PowerShellCore/Operational"
Invoke-Command -ComputerName Server01 -ScriptBlock {Get-WinEvent -LogName $Using:Log -MaxEvents 10}
```

De `$Log` variabele bevat de naam van het gebeurtenis logboek, PowerShellCore/Operation. De `Invoke-Command` cmdlet wordt uitgevoerd `Get-WinEvent` op Server01 om de tien nieuwste gebeurtenissen uit het gebeurtenis logboek op te halen. De waarde van de para meter **LogName** is de `$Log` variabele die wordt voorafgegaan door de `Using` wijzigings functie van het bereik om aan te geven dat deze is gemaakt in de lokale sessie, niet in de externe sessie.

### Voor beeld 10: de computer naam verbergen

In dit voor beeld ziet u het effect van het gebruik van de para meter **HideComputerName** van `Invoke-Command` .
**HideComputerName** heeft geen invloed op het object dat met deze cmdlet wordt geretourneerd. Alleen de weer gave wordt gewijzigd. U kunt nog steeds de **Format** -cmdlets gebruiken om de eigenschap **PsComputerName** van de betrokken objecten weer te geven.

```powershell
Invoke-Command -ComputerName S1, S2 -ScriptBlock {Get-Process PowerShell}
```

```Output
PSComputerName    Handles  NPM(K)    PM(K)      WS(K) VM(M)   CPU(s)     Id   ProcessName
--------------    -------  ------    -----      ----- -----   ------     --   -----------
S1                575      15        45100      40988   200     4.68     1392 PowerShell
S2                777      14        35100      30988   150     3.68     67   PowerShell
```

```powershell
Invoke-Command -ComputerName S1, S2 -ScriptBlock {Get-Process PowerShell} -HideComputerName
```

```Output
Handles  NPM(K)    PM(K)      WS(K) VM(M)   CPU(s)     Id   ProcessName
-------  ------    -----      ----- -----   ------     --   -----------
575      15        45100      40988   200     4.68     1392 PowerShell
777      14        35100      30988   150     3.68     67   PowerShell
```

De eerste twee opdrachten gebruiken `Invoke-Command` om een `Get-Process` opdracht voor het Power Shell-proces uit te voeren. De uitvoer van de eerste opdracht bevat de eigenschap **PsComputerName** , die de naam bevat van de computer waarop de opdracht is uitgevoerd. De uitvoer van de tweede opdracht, die gebruikmaakt van **HideComputerName** , bevat niet de kolom **PsComputerName** .

### Voor beeld 11: het sleutel woord param in een script blok gebruiken

Het `Param` sleutel woord en de para meter **argument List** worden gebruikt om variabele waarden door te geven aan benoemde para meters in een-script blok. In dit voor beeld worden bestands namen weer gegeven die beginnen met de letter `a` en de `.pdf` uitbrei ding hebben.

Zie about_Language_Keywords voor meer informatie over het `Param` tref [about_Language_Keywords](./about/about_language_keywords.md#param)woord.

```powershell
$parameters = @{
    ComputerName = "Server01"
    ScriptBlock = { Param ($param1,$param2) Get-ChildItem -Name $param1 -Include $param2 }
    ArgumentList = "a*", "*.pdf"
}
Invoke-Command @parameters
```

```Output
aa.pdf
ab.pdf
ac.pdf
az.pdf
```

`Invoke-Command` maakt gebruik van de para meter **script Block** die twee variabelen definieert, `$param1` en `$param2` . `Get-ChildItem` maakt gebruik van de benoemde para meters, **naam** en **bevatten** met de namen van variabelen. De **argument List** geeft de waarden door aan de variabelen.

### Voor beeld 12: de $args automatische variabele in een script blok gebruiken

De `$args` Automatische variabele en de para meter **argument List** worden gebruikt om matrix waarden door te geven aan parameter posities in een-script blok. In dit voor beeld wordt de mapinhoud van de server weer gegeven `.txt` . De `Get-ChildItem` para meter **Path** is positie 0 en de **filter** parameter is positie
1.

Zie about_Automatic_Variables voor meer informatie over de `$args` variabele [about_Automatic_Variables](./about/about_automatic_variables.md#args)

```powershell
$parameters = @{
    ComputerName = "Server01"
    ScriptBlock = { Get-ChildItem $args[0] $args[1] }
    ArgumentList = "C:\Test", "*.txt*"
}
Invoke-Command @parameters
```

```Output
    Directory: C:\Test

Mode                 LastWriteTime         Length Name
----                 -------------         ------ ----
-a---           6/12/2019    15:15            128 alog.txt
-a---           7/27/2019    15:16            256 blog.txt
-a---           9/28/2019    17:10             64 zlog.txt
```

`Invoke-Command` Hiermee wordt een **script Block** -para meter gebruikt en worden `Get-ChildItem` de-en- `$args[0]` `$args[1]` matrix waarden opgegeven. De **argument List** geeft de `$args` matrix waarden door aan de `Get-ChildItem` parameter posities voor **Path** en **filter**.

### Voor beeld 13: een script uitvoeren op alle computers die worden vermeld in een tekst bestand

In dit voor beeld wordt de `Invoke-Command` cmdlet gebruikt om het script uit te voeren `Sample.ps1` op alle computers die worden vermeld in het `Servers.txt` bestand. De opdracht gebruikt de **filepath** -para meter om het script bestand op te geven. Met deze opdracht kunt u het script uitvoeren op de externe computers, zelfs als het script bestand niet toegankelijk is voor de externe computers.

```powershell
Invoke-Command -ComputerName (Get-Content Servers.txt) -FilePath C:\Scripts\Sample.ps1 -ArgumentList Process, Service
```

Wanneer u de opdracht verzendt, wordt de inhoud van het `Sample.ps1` bestand gekopieerd naar een script blok en wordt het script blok op elke externe computer uitgevoerd. Deze procedure is gelijk aan het gebruik van de para meter **script Block** om de inhoud van het script te verzenden.

### Voor beeld 14: een opdracht uitvoeren op een externe computer met behulp van een URI

In dit voor beeld ziet u hoe u een opdracht uitvoert op een externe computer die wordt geïdentificeerd door een URI (Uniform Resource Identifier). In dit voor beeld wordt een `Set-Mailbox` opdracht uitgevoerd op een externe Exchange-Server.

```powershell
$LiveCred = Get-Credential
$parameters = @{
  ConfigurationName = 'Microsoft.Exchange'
  ConnectionUri = 'https://ps.exchangelabs.com/PowerShell'
  Credential = $LiveCred
  Authentication = 'Basic'
  ScriptBlock = {Set-Mailbox Dan -DisplayName "Dan Park"}
}
Invoke-Command @parameters
```

De eerste regel gebruikt de `Get-Credential` cmdlet voor het opslaan van Windows Live ID-referenties in de `$LiveCred` variabele. Power shell vraagt de gebruiker om Windows Live ID-referenties in te voeren.

De `$parameters` variabele is een hash-tabel met de para meters die moeten worden door gegeven aan de `Invoke-Command` cmdlet. `Invoke-Command`Met de cmdlet wordt een `Set-Mailbox` opdracht uitgevoerd met behulp van de **micro soft. Exchange** -sessie configuratie. De **ConnectionURI** para meter geeft u de URL van het Exchange Server-eind punt. De **referentie** parameter bevat de referenties die zijn opgeslagen in de `$LiveCred` variabele. De para meter **AuthenticationMechanism** bepaalt het gebruik van basis verificatie. De para meter **script Block** geeft een script blok dat de opdracht bevat.

### Voor beeld 15: een sessie optie gebruiken

In dit voor beeld ziet u hoe u een **SessionOption** -para meter maakt en gebruikt.

```powershell
$so = New-PSSessionOption -SkipCACheck -SkipCNCheck -SkipRevocationCheck
Invoke-Command -ComputerName server01 -UseSSL -ScriptBlock { Get-HotFix } -SessionOption $so -Credential server01\user01
```

De `New-PSSessionOption` cmdlet maakt een sessie optie object dat ervoor zorgt dat het externe einde de certificerings instantie, canonieke naam en intrekkings lijsten niet verifieert tijdens het evalueren van de binnenkomende https-verbinding. Het **SessionOption** -object wordt opgeslagen in de `$so` variabele.

> [!NOTE]
> Het uitschakelen van deze controles is handig voor het oplossen van problemen, maar is uiteraard niet veilig.

Met de `Invoke-Command` cmdlet wordt `Get-HotFix` op afstand een opdracht uitgevoerd. De **SessionOption** -para meter krijgt de `$so` variabele.

### Voor beeld 16: URI-omleiding beheren in een externe opdracht

In dit voor beeld ziet u hoe u de para meters **AllowRedirection** en **SessionOption** gebruikt voor het beheren van URI-omleiding in een externe opdracht.

```powershell
$max = New-PSSessionOption -MaximumRedirection 1
$parameters = @{
  ConnectionUri = "https://ps.exchangelabs.com/PowerShell"
  ScriptBlock = { Get-Mailbox dan }
  AllowRedirection = $true
  SessionOption = $max
}
Invoke-Command @parameters
```

`New-PSSessionOption`Met de cmdlet maakt u een **PSSessionOption** -object dat is opgeslagen in de `$max` variabele. De opdracht gebruikt de para meter **MaximumRedirection** om de eigenschap **MaximumConnectionRedirectionCount** van het object **PSSessionOption** in te stellen op 1.

`Invoke-Command`Met de cmdlet wordt een `Get-Mailbox` opdracht uitgevoerd op een externe micro soft Exchange-Server. De para meter **AllowRedirection** biedt expliciete machtigingen voor het omleiden van de verbinding met een ander eind punt. De para meter **SessionOption** maakt gebruik van het sessie object dat is opgeslagen in de `$max` variabele.

Als de externe computer die wordt opgegeven door **ConnectionURI** een omleidings bericht retourneert, wordt de verbinding door Power shell omgeleid, maar als de nieuwe bestemming een andere omleidings bericht retourneert, wordt de waarde van het aantal omleidingen van 1 overschreden en `Invoke-Command` wordt een niet-afsluit fout geretourneerd.

### Voor beeld 17: toegang tot een netwerk share in een externe sessie

In dit voor beeld ziet u hoe u een netwerk share opent vanuit een externe sessie. Er worden drie computers gebruikt om het voor beeld te demonstreren. Server01 is de lokale computer, Server02 is de externe computer en Net03 bevat de netwerk share. Server01 maakt verbinding met Server02 en vervolgens wordt Server02 een tweede hop naar Net03 om toegang te krijgen tot de netwerk share. Zie [de tweede hop in Power shell Remoting maken](/powershell/scripting/learn/remoting/ps-remoting-second-hop)voor meer informatie over de manier waarop externe communicatie tussen computers door Power shell wordt ondersteund.

De vereiste CredSSP-overdracht (Credential Security Support Provider) is ingeschakeld in de client instellingen op de lokale computer en in de service-instellingen op de externe computer. Als u de opdrachten in dit voor beeld wilt uitvoeren, moet u lid zijn van de groep **Administrators** op de lokale computer en de externe computer.

```powershell
Enable-WSManCredSSP -Role Client -DelegateComputer Server02
$s = New-PSSession Server02
Invoke-Command -Session $s -ScriptBlock {Enable-WSManCredSSP -Role Server -Force}
$parameters = @{
  Session = $s
  ScriptBlock = { Get-Item \\Net03\Scripts\LogFiles.ps1 }
  Authentication = "CredSSP"
  Credential = "Domain01\Admin01"
}
Invoke-Command @parameters
```

`Enable-WSManCredSSP`Met de cmdlet wordt CredSSP delegering van de lokale Server01-computer naar de externe computer van Server02 ingeschakeld. De para meter **Role** specificeert de **client** voor het configureren van de CredSSP client-instelling op de lokale computer.

`New-PSSession` Hiermee maakt u een **PSSession** -object voor Server02 en slaat u het object op in de `$s` variabele.

De `Invoke-Command` cmdlet gebruikt de `$s` variabele om verbinding te maken met de externe computer, Server02. De para meter **script Block** wordt uitgevoerd `Enable-WSManCredSSP` op de externe computer. De para meter **Role** specificeert de **Server** voor het configureren van de CredSSP-server instelling op de externe computer.

De `$parameters` variabele bevat de parameter waarden om verbinding te maken met de netwerk share. De `Invoke-Command` cmdlet voert een `Get-Item` opdracht in de sessie in uit `$s` . Met deze opdracht wordt een script opgehaald van de `\\Net03\Scripts` netwerk share. De opdracht gebruikt de **verificatie** parameter met de waarde **CredSSP** en de para meter **Credential** met de waarde **Domain01\Admin01**.

### Voor beeld 18: scripts op veel externe computers starten

In dit voor beeld wordt een script uitgevoerd op meer dan honderd computers. Om de impact op de lokale computer tot een minimum te beperken, wordt er verbinding gemaakt met elke computer, wordt het script gestart en wordt de verbinding met elke computer verbroken.
Het script wordt nog steeds uitgevoerd in de verbroken sessies.

```powershell
$parameters = @{
  ComputerName = (Get-Content -Path C:\Test\Servers.txt)
  InDisconnectedSession = $true
  FilePath = "\\Scripts\Public\ConfigInventory.ps1"
  SessionOption = @{OutputBufferingMode="Drop";IdleTimeout=43200000}
}
Invoke-Command @parameters
```

De opdracht wordt gebruikt `Invoke-Command` om het script uit te voeren. De waarde van de para meter **ComputerName** is een `Get-Content` opdracht waarmee de namen van de externe computers uit een tekst bestand worden opgehaald. De **InDisconnectedSession** para meter verbreekt de verbinding van de sessies zodra de opdracht wordt gestart. De waarde van de **filepath** para meter is het script dat `Invoke-Command` op elke computer wordt uitgevoerd.

De waarde van **SessionOption** is een hash-tabel. De **OutputBufferingMode** -waarde is ingesteld op **Drop** en de waarde **IdleTimeout** is ingesteld op **43200000** milliseconden (12 uur).

Gebruik de cmdlet om de resultaten op te halen van opdrachten en scripts die worden uitgevoerd in verbroken sessies `Receive-PSSession` .

### Voor beeld 19: een opdracht uitvoeren op een externe computer via SSH

In dit voor beeld ziet u hoe u een opdracht op een externe computer uitvoert met behulp van Secure Shell (SSH). Als SSH op de externe computer is geconfigureerd om te vragen om wacht woorden, wordt u gevraagd een wacht woord op te geven.
Anders moet u op SSH-sleutel gebaseerde gebruikers verificatie gebruiken.

```powershell
Invoke-Command -HostName UserA@LinuxServer01 -ScriptBlock { Get-MailBox * }
```

### Voor beeld 20: een opdracht uitvoeren op een externe computer met SSH en een gebruikers verificatie sleutel opgeven

In dit voor beeld ziet u hoe u een opdracht op een externe computer uitvoert met SSH en een sleutel bestand opgeeft voor gebruikers verificatie. U wordt niet gevraagd om een wacht woord tenzij de sleutel verificatie mislukt en de externe computer zo is geconfigureerd dat basis wachtwoord verificatie is toegestaan.

```powershell
Invoke-Command -HostName UserA@LinuxServer01 -ScriptBlock { Get-MailBox * } -KeyFilePath /UserA/UserAKey_rsa
```

### Voor beeld 21: een script bestand op meerdere externe computers uitvoeren met SSH als een taak

In dit voor beeld ziet u hoe u een script bestand op meerdere externe computers kunt uitvoeren met behulp van SSH en de para meter **SSHConnection** . De para meter **SSHConnection** gebruikt een matrix van hash-tabellen die verbindings gegevens voor elke computer bevatten. Dit voor beeld vereist dat de doel-externe computers SSH hebben geconfigureerd ter ondersteuning van de verificatie op basis van sleutel-gebruikers.

```powershell
$sshConnections =
@{ HostName="WinServer1"; UserName="Domain\UserA"; KeyFilePath="C:\Users\UserA\id_rsa" },
@{ HostName="UserB@LinuxServer5"; KeyFilePath="/Users/UserB/id_rsa" }
$results = Invoke-Command -FilePath c:\Scripts\CollectEvents.ps1 -SSHConnection $sshConnections
```

## PARAMETERS

### -AllowRedirection

Hiermee kan de verbinding worden omgeleid naar een alternatieve URI (Uniform Resource Identifier).

Wanneer u de para meter **ConnectionURI** gebruikt, kan de externe bestemming een instructie retour neren die wordt omgeleid naar een andere URI. Standaard worden verbindingen niet door Power shell omgeleid, maar u kunt deze para meter gebruiken om de verbinding door te sturen.

U kunt ook het aantal keren beperken dat de verbinding wordt omgeleid door de waarde van de **MaximumConnectionRedirectionCount** -sessie optie te wijzigen. Gebruik de para meter **MaximumRedirection** van de `New-PSSessionOption` cmdlet of stel de eigenschap **MaximumConnectionRedirectionCount** van de `$PSSessionOption` Voorkeurs variabele in. De standaard waarde is 5.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: Uri, FilePathUri
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### -ApplicationName

Hiermee geeft u het segment van de toepassings naam van de verbindings-URI op. Gebruik deze para meter om de naam van de toepassing op te geven wanneer u de para meter **ConnectionURI** niet in de opdracht gebruikt.

De standaard waarde is de waarde van de `$PSSessionApplicationName` Voorkeurs variabele op de lokale computer. Als deze voorkeurs variabele niet is gedefinieerd, is de standaard waarde WSMAN. Deze waarde is geschikt voor de meeste toepassingen. Zie [about_Preference_Variables](./About/about_Preference_Variables.md)voor meer informatie.

De WinRM-service gebruikt de naam van de toepassing om een listener te selecteren om de verbindings aanvraag te onderhouden.
De waarde van deze para meter moet overeenkomen met de waarde van de eigenschap **URLPrefix** van een listener op de externe computer.

```yaml
Type: System.String
Parameter Sets: ComputerName, FilePathComputerName
Aliases:

Required: False
Position: Named
Default value: $PSSessionApplicationName if set on the local computer, otherwise WSMAN
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -Argument List

Levert de waarden van lokale variabelen in de opdracht. De variabelen in de opdracht worden vervangen door deze waarden voordat de opdracht wordt uitgevoerd op de externe computer. Voer de waarden in een door komma's gescheiden lijst in. Waarden worden aan variabelen gekoppeld in de volg orde waarin ze worden weer gegeven. De alias voor **argument List** is args.

De waarden in de para meter **argument List** kunnen werkelijke waarden zijn, zoals 1024, of ze kunnen verwijzingen zijn naar lokale variabelen, zoals `$max` .

Als u lokale variabelen wilt gebruiken in een opdracht, gebruikt u de volgende opdracht indeling:

`{param($<name1>[, $<name2>]...) <command-with-local-variables>} -ArgumentList <value>` of `<local-variable>`

Het sleutel woord **param** bevat de lokale variabelen die worden gebruikt in de opdracht. **Argument List** levert de waarden van de variabelen in de volg orde waarin ze worden weer gegeven. Zie [about_Splatting](about/about_Splatting.md#splatting-with-arrays)voor meer informatie over het gedrag van **argument List**.

```yaml
Type: System.Object[]
Parameter Sets: (All)
Aliases: Args

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -AsJob

Geeft aan dat met deze cmdlet de opdracht wordt uitgevoerd als een achtergrond taak op een externe computer. Gebruik deze para meter om opdrachten uit te voeren die veel tijd in beslag nemen.

Wanneer u de para meter **AsJob** gebruikt, retourneert de opdracht een object dat de taak vertegenwoordigt, waarna de opdracht prompt wordt weer gegeven. U kunt in de sessie blijven werken terwijl de taak is voltooid. Als u de taak wilt beheren, gebruikt u de- `*-Job` cmdlets. Gebruik de cmdlet om de taak resultaten te verkrijgen `Receive-Job` .

De para meter **AsJob** lijkt op het gebruik van de `Invoke-Command` cmdlet om een `Start-Job` cmdlet op afstand uit te voeren. Met **AsJob** wordt de taak echter gemaakt op de lokale computer, zelfs als de taak wordt uitgevoerd op een externe computer. De resultaten van de externe taak worden automatisch geretourneerd naar de lokale computer.

Zie [about_Jobs](About/about_Jobs.md) en [about_Remote_Jobs](About/about_Remote_Jobs.md)voor meer informatie over Power shell-achtergrond taken.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: FilePathRunspace, Session, ComputerName, FilePathComputerName, Uri, FilePathUri, VMId, VMName, FilePathVMId, FilePathVMName, SSHHost, ContainerId, FilePathContainerId, SSHHostHashParam, FilePathSSHHost, FilePathSSHHostHash
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### -Verificatie

Hiermee geeft u het mechanisme op dat wordt gebruikt om de referenties van de gebruiker te verifiëren. CredSSP-verificatie is alleen beschikbaar in Windows Vista, Windows Server 2008 en latere versies van het Windows-besturings systeem.

De acceptabele waarden voor deze para meter zijn als volgt:

- Standaard
- Basic
- CredSSP
- Samenvatting
- Kerberos
- Negotiate
- NegotiateWithImplicitCredential

De standaard waarde is standaard.

Zie [AuthenticationMechanism Enumeration (Engelstalig)](/dotnet/api/system.management.automation.runspaces.authenticationmechanism)voor meer informatie over de waarden van deze para meter.

> [!CAUTION]
> De verificatie van de referentie provider (CredSSP), waarbij de referenties van de gebruiker worden door gegeven aan een externe computer die moet worden geverifieerd, is ontworpen voor opdrachten waarvoor verificatie is vereist voor meer dan één bron, zoals het openen van een externe netwerk share. Dit mechanisme verhoogt het beveiligings risico van de externe bewerking. Als er is geknoeid met de externe computer, kunnen de referenties die aan worden door gegeven, worden gebruikt om de netwerk sessie te beheren. Zie [Credential Security Support Provider](/windows/win32/secauthn/credential-security-support-provider)(Engelstalig) voor meer informatie.

```yaml
Type: System.Management.Automation.Runspaces.AuthenticationMechanism
Parameter Sets: ComputerName, FilePathComputerName, Uri, FilePathUri
Aliases:
Accepted values: Basic, Default, Credssp, Digest, Kerberos, Negotiate, NegotiateWithImplicitCredential

Required: False
Position: Named
Default value: Default
Accept pipeline input: False
Accept wildcard characters: False
```

### -CertificateThumbprint

Hiermee geeft u het digitale open bare-sleutel certificaat (x509) op van een gebruikers account dat is gemachtigd om verbinding te maken met de verbroken sessie. Voer de vinger afdruk van het certificaat in.

Certificaten worden gebruikt in authenticatie op basis van client certificaten. Ze kunnen alleen worden toegewezen aan lokale gebruikers accounts en ze werken niet met domein accounts.

Als u een certificaat vingerafdruk wilt ophalen, gebruikt u een `Get-Item` of- `Get-ChildItem` opdracht in het Power shell-certificaat: station.

```yaml
Type: System.String
Parameter Sets: ComputerName, Uri
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -ComputerName

Hiermee geeft u de computers waarop de opdracht wordt uitgevoerd. Standaard is dit de lokale computer.

Wanneer u de para meter **ComputerName** gebruikt, maakt Power shell een tijdelijke verbinding die alleen wordt gebruikt om de opgegeven opdracht uit te voeren en vervolgens gesloten. Als u een permanente verbinding nodig hebt, gebruikt u de para meter **Session** .

Typ de NETBIOS-naam, het IP-adres of de Fully Qualified Domain Name van een of meer computers in een lijst met door komma's gescheiden waarden. Typ de computer naam, localhost of een punt () om de lokale computer op te geven `.` .

Als u een IP-adres in de waarde **computer naam** wilt gebruiken, moet de opdracht de para meter **Credential** bevatten. De computer moet zijn geconfigureerd voor het HTTPS-Trans Port of het IP-adres van de externe computer moet zijn opgenomen in de lijst met WinRM **TrustedHosts** van de lokale computer. Zie [een computer toevoegen aan de lijst met vertrouwde hosts](./about/about_remote_troubleshooting.md#how-to-add-a-computer-to-the-trusted-hosts-list)voor instructies om een computer naam toe te voegen aan de lijst met **TrustedHosts** .

In Windows Vista en latere versies van het Windows-besturings systeem moet u Power shell uitvoeren met de optie **als administrator uitvoeren** om de lokale computer op te vragen met de waarde **computer naam**.

```yaml
Type: System.String[]
Parameter Sets: ComputerName, FilePathComputerName
Aliases: Cn

Required: False
Position: 0
Default value: Local computer
Accept pipeline input: False
Accept wildcard characters: False
```

### -Configuratiepad

Hiermee geeft u de sessie configuratie op die wordt gebruikt voor de nieuwe **PSSession**.

Voer een configuratie naam of de volledig gekwalificeerde resource-URI in voor een sessie configuratie. Als u alleen de configuratie naam opgeeft, wordt de volgende schema-URI voor voegsel: `http://schemas.microsoft.com/PowerShell` .

Als deze para meter wordt gebruikt in combi natie met SSH, geeft u het subsysteem op dat moet worden gebruikt voor het doel zoals gedefinieerd in `sshd_config` . De standaard waarde voor SSH is het `powershell` subsysteem.

De sessie configuratie voor een sessie bevindt zich op de externe computer. Als de opgegeven sessie configuratie niet bestaat op de externe computer, mislukt de opdracht.

De standaard waarde is de waarde van de `$PSSessionConfigurationName` Voorkeurs variabele op de lokale computer. Als deze voorkeurs variabele niet is ingesteld, is de standaard instelling **micro soft. Power shell**. Zie [about_Preference_Variables](about/about_Preference_Variables.md)voor meer informatie.

```yaml
Type: System.String
Parameter Sets: ComputerName, FilePathComputerName, Uri, FilePathUri, VMId, VMName, FilePathVMId, FilePathVMName, ContainerId, FilePathContainerId
Aliases:

Required: False
Position: Named
Default value: $PSSessionConfigurationName if set on the local computer, otherwise Microsoft.PowerShell
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -ConnectionUri

Hiermee geeft u een URI (Uniform Resource Identifier) op die het verbindings eindpunt van de sessie definieert.
De URI moet volledig gekwalificeerd zijn.

De indeling van deze teken reeks is als volgt:

`<Transport>://<ComputerName>:<Port>/<ApplicationName>`

De standaard waarde is als volgt:

`http://localhost:5985/WSMAN`

Als u geen verbindings-URI opgeeft, kunt u de para meters **UseSSL** en **Port** gebruiken om de verbindings-URI-waarden op te geven.

Geldige waarden voor het **transport** segment van de URI zijn http en HTTPS. Als u een verbindings-URI met een transport segment opgeeft, maar geen poort opgeeft, wordt de sessie gemaakt met de standaard poorten: 80 voor HTTP en 443 voor HTTPS. Als u de standaard poorten voor externe communicatie van Power shell wilt gebruiken, geeft u poort 5985 voor HTTP of 5986 op voor HTTPS.

Als de doel computer de verbinding omleidt naar een andere URI, wordt de omleiding door Power shell voor komen, tenzij u de para meter **AllowRedirection** in de opdracht gebruikt.

```yaml
Type: System.Uri[]
Parameter Sets: Uri, FilePathUri
Aliases: URI, CU

Required: False
Position: 0
Default value: http://localhost:5985/WSMAN
Accept pipeline input: False
Accept wildcard characters: False
```

### -ContainerId

Hiermee geeft u een matrix met container-Id's op.

```yaml
Type: System.String[]
Parameter Sets: ContainerId, FilePathContainerId
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -Credential

Hiermee geeft u een gebruikers account op dat is gemachtigd om deze actie uit te voeren. Standaard is dit de huidige gebruiker.

Typ een gebruikers naam, zoals **gebruiker01** of **Domain01\User01** , of voer een **PSCredential** -object in dat door de cmdlet wordt gegenereerd `Get-Credential` . Als u een gebruikers naam typt, wordt u gevraagd het wacht woord in te voeren.

Referenties worden opgeslagen in een [PSCredential](/dotnet/api/system.management.automation.pscredential) -object en het wacht woord wordt opgeslagen als [SecureString](/dotnet/api/system.security.securestring).

> [!NOTE]
> Zie [Hoe veilig is securestring?](/dotnet/api/system.security.securestring#how-secure-is-securestring)voor meer informatie over **securestring** Data Protection.

```yaml
Type: System.Management.Automation.PSCredential
Parameter Sets: ComputerName, FilePathComputerName, Uri, FilePathUri, VMId, VMName, FilePathVMId, FilePathVMName
Aliases:

Required: True (VMId, VMName, FilePathVMId, FilePathVMName), False (ComputerName, FilePathComputerName, Uri, FilePathUri)
Position: Named
Default value: Current user
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -EnableNetworkAccess

Geeft aan dat met deze cmdlet een interactief beveiligings token wordt toegevoegd aan loop Back-sessies. Met het interactieve token kunt u opdrachten uitvoeren in de loop back-sessie die gegevens van andere computers ophalen. U kunt bijvoorbeeld een opdracht uitvoeren in de sessie waarmee XML-bestanden van een externe computer naar de lokale computer worden gekopieerd.

Een loop back-sessie is een **PSSession** die afkomstig is van en eindigt op dezelfde computer. Als u een loop back-sessie wilt maken, laat u de para meter **ComputerName** weg of stelt u de waarde in op punt ( `.` ), localhost of de naam van de lokale computer.

Loop Back-sessies worden standaard gemaakt met behulp van een netwerk token, wat mogelijk niet voldoende machtigingen biedt om te verifiëren bij externe computers.

De para meter **EnableNetworkAccess** is alleen effectief in loop Back-sessies. Als u **EnableNetworkAccess** gebruikt wanneer u een sessie op een externe computer maakt, mislukt de opdracht, maar wordt de para meter genegeerd.

U kunt externe toegang toestaan in een loop back-sessie met behulp van de **CredSSP** -waarde van de **verificatie** parameter, waarmee de sessie referenties worden gedelegeerd aan andere computers.

Om de computer te beschermen tegen kwaadwillende toegang, kunnen niet-verbonden loop Back-sessies met interactieve tokens, die zijn gemaakt met behulp van **EnableNetworkAccess** , alleen opnieuw verbinding maken vanaf de computer waarop de sessie is gemaakt. Verbroken sessies die gebruikmaken van CredSSP-verificatie, kunnen opnieuw worden aangesloten op andere computers. Voor meer informatie raadpleegt u `Disconnect-PSSession`.

Deze para meter is geïntroduceerd in Power Shell 3,0.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: ComputerName, FilePathComputerName, Uri, FilePathUri
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### -FilePath

Hiermee geeft u een lokaal script op dat met deze cmdlet wordt uitgevoerd op een of meer externe computers. Voer het pad en de bestands naam van het script in of pipet een scriptpad naar `Invoke-Command` . Het script moet bestaan op de lokale computer of in een map waartoe de lokale computer toegang heeft. Gebruik **argument List** om de waarden van para meters in het script op te geven.

Wanneer u deze para meter gebruikt, wordt de inhoud van het opgegeven script bestand door Power shell naar een script blok geconverteerd, wordt het script blok verzonden naar de externe computer en uitgevoerd op de externe computer.

```yaml
Type: System.String
Parameter Sets: FilePathRunspace, FilePathComputerName, FilePathUri, FilePathVMId, FilePathVMName, FilePathContainerId, FilePathSSHHost, FilePathSSHHostHash
Aliases: PSPath

Required: True
Position: 1
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -HideComputerName

Geeft aan dat met deze cmdlet de computer naam van elk object uit de uitvoer weergave wordt wegge laten. De naam van de computer die het object heeft gegenereerd, wordt standaard weer gegeven in de weer gave.

Deze para meter is alleen van invloed op de uitvoer weergave. Het object wordt niet gewijzigd.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: FilePathRunspace, Session, ComputerName, FilePathComputerName, Uri, FilePathUri, VMId, VMName, FilePathVMId, FilePathVMName, SSHHost, ContainerId, FilePathContainerId, SSHHostHashParam, FilePathSSHHost, FilePathSSHHostHash
Aliases: HCN

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### -Hostnaam

Hiermee geeft u een matrix van computer namen voor een verbinding op basis van SSH (Secure Shell). Dit is vergelijkbaar met de para meter **ComputerName** , behalve dat de verbinding met de externe computer wordt gemaakt met behulp van SSH in plaats van Windows WinRM.

Deze para meter is geïntroduceerd in Power shell 6,0.

```yaml
Type: System.String[]
Parameter Sets: SSHHost, FilePathSSHHost
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -InDisconnectedSession

Geeft aan dat met deze cmdlet een opdracht of script wordt uitgevoerd in een sessie waarbij de verbinding is verbroken.

Wanneer u de para meter **InDisconnectedSession** gebruikt, `Invoke-Command` wordt op elke externe computer een permanente sessie gemaakt, wordt de opdracht gestart die is opgegeven door de para meter **script Block** of **filepath** en wordt de verbinding met de sessie verbroken. De opdrachten blijven worden uitgevoerd in de verbroken sessies. Met **InDisconnectedSession** kunt u opdrachten uitvoeren zonder een verbinding met de externe sessies te onderhouden. En omdat de verbinding van de sessie wordt verbroken voordat er resultaten worden geretourneerd, zorgt **InDisconnectedSession** ervoor dat alle opdracht resultaten worden geretourneerd naar de opnieuw verbonden sessie, in plaats van te worden gesplitst tussen sessies.

U kunt **InDisconnectedSession** niet gebruiken met de para meter **Session** of de para meter **AsJob** .

Opdrachten die gebruikmaken van **InDisconnectedSession** retour neren een **PSSession** -object dat de niet-verbonden sessie vertegenwoordigt. Ze retour neren niet de uitvoer van de opdracht. Gebruik de cmdlets of om verbinding te maken met de verbroken sessie `Connect-PSSession` `Receive-PSSession` . Gebruik de cmdlet om de resultaten op te halen van de opdrachten die in de sessie worden uitgevoerd `Receive-PSSession` . Om opdrachten uit te voeren die uitvoer genereren in een verbroken sessie, stelt u de waarde van de **OutputBufferingMode** -sessie optie in op **Drop**. Als u van plan bent om verbinding te maken met de verbroken sessie, stelt u de time-out voor inactiviteit in de sessie zo in dat u voldoende tijd hebt om verbinding te maken voordat u de sessie verwijdert.

U kunt de uitvoer buffer modus en time-out voor inactiviteit instellen in de para meter **SessionOption** of in de `$PSSessionOption` Voorkeurs variabele. Zie en about_Preference_Variables voor meer informatie over sessie `New-PSSessionOption` opties [about_Preference_Variables](./about/about_preference_variables.md).

Zie [about_Remote_Disconnected_Sessions](about/about_Remote_Disconnected_Sessions.md)voor meer informatie over de functie voor verbroken sessies.

Deze para meter is geïntroduceerd in Power Shell 3,0.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: ComputerName, FilePathComputerName, Uri, FilePathUri
Aliases: Disconnected

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### -Input object

Hiermee geeft u de invoer aan de opdracht. Voer een variabele in die de objecten bevat of typ een opdracht of expressie waarmee de objecten worden opgehaald.

Gebruik bij het gebruik van de para meter **input object** de `$Input` Automatische variabele in de waarde van de para meter **script Block** om de invoer objecten weer te geven.

```yaml
Type: System.Management.Automation.PSObject
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### -JobName

Hiermee geeft u een beschrijvende naam op voor de achtergrond taak. Taken worden standaard benoemd `Job<n>` , waarbij `<n>` een rang nummer is.

Als u de para meter **JobName** in een opdracht gebruikt, wordt de opdracht uitgevoerd als een taak en `Invoke-Command` wordt een taak object geretourneerd, zelfs als u geen **AsJob** in de opdracht opneemt.

Zie [about_Jobs](./About/about_Jobs.md)voor meer informatie over Power shell-achtergrond taken.

```yaml
Type: System.String
Parameter Sets: FilePathRunspace, Session, ComputerName, FilePathComputerName, Uri, FilePathUri, SSHHost, ContainerId, FilePathContainerId, SSHHostHashParam
Aliases:

Required: False
Position: Named
Default value: Job<n>
Accept pipeline input: False
Accept wildcard characters: False
```

### -Bestandspad

Hiermee geeft u een pad naar een sleutel bestand dat door een Secure Shell (SSH) wordt gebruikt om een gebruiker op een externe computer te verifiëren.

Met SSH kan gebruikers verificatie worden uitgevoerd via persoonlijke en open bare sleutels als alternatief voor de basis wachtwoord verificatie. Als de externe computer is geconfigureerd voor sleutel verificatie, kan deze para meter worden gebruikt om de sleutel op te geven waarmee de gebruiker wordt geïdentificeerd.

Deze para meter is geïntroduceerd in Power shell 6,0.

```yaml
Type: System.String
Parameter Sets: SSHHost, FilePathSSHHost
Aliases: IdentityFilePath

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -NoNewScope

Geeft aan dat met deze cmdlet de opgegeven opdracht wordt uitgevoerd in het huidige bereik. `Invoke-Command`Voert standaard opdrachten uit in hun eigen bereik.

Deze para meter is alleen geldig in opdrachten die worden uitgevoerd in de huidige sessie, dat wil zeggen opdrachten die de **computer naam** en de **sessie** parameters weglaten.

Deze para meter is geïntroduceerd in Power Shell 3,0.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: InProcess
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### -Port

Hiermee geeft u de netwerk poort op de externe computer die wordt gebruikt voor deze opdracht. Als u verbinding wilt maken met een externe computer, moet op de externe computer worden geluisterd op de poort die door de verbinding wordt gebruikt. De standaard poorten zijn 5985 (WinRM-poort voor HTTP) en 5986 (WinRM-poort voor HTTPS).

Voordat u een andere poort gebruikt, configureert u de WinRM-listener op de externe computer om op die poort te Luis teren. Als u de listener wilt configureren, typt u de volgende twee opdrachten bij de Power shell-prompt:

`Remove-Item -Path WSMan:\Localhost\listener\listener* -Recurse`

`New-Item -Path WSMan:\Localhost\listener -Transport http -Address * -Port \<port-number\>`

Gebruik de para meter **poort** alleen als dat nodig is. De poort die in de opdracht is ingesteld, is van toepassing op alle computers of sessies waarop de opdracht wordt uitgevoerd. Een alternatieve poort instelling kan verhinderen dat de opdracht wordt uitgevoerd op alle computers.

```yaml
Type: System.Int32
Parameter Sets: ComputerName, FilePathComputerName, SSHHost
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -RemoteDebug

Wordt gebruikt om de aangeroepen opdracht in de foutopsporingsmodus in de externe Power shell-sessie uit te voeren.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: FilePathRunspace, Session, ComputerName, FilePathComputerName, Uri, FilePathUri, VMId, VMName, FilePathVMId, FilePathVMName, SSHHost, ContainerId, FilePathContainerId, SSHHostHashParam, FilePathSSHHost, FilePathSSHHostHash
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### -RunAsAdministrator

Geeft aan dat deze cmdlet een opdracht aanroept als beheerder.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: ContainerId, FilePathContainerId
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### -Script Block

Hiermee geeft u de opdrachten op die moeten worden uitgevoerd. Plaats de opdrachten tussen accolades `{ }` om een script blok te maken.
Deze parameter is vereist.

Standaard worden alle variabelen in de opdracht geëvalueerd op de externe computer. Als u lokale variabelen wilt toevoegen aan de opdracht, gebruikt u **argument List**.

```yaml
Type: System.Management.Automation.ScriptBlock
Parameter Sets: InProcess, Session, ComputerName, Uri, VMId, VMName, SSHHost, ContainerId, SSHHostHashParam
Aliases: Command

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Sessie

Hiermee geeft u een matrix met sessies waarin met deze cmdlet de opdracht wordt uitgevoerd. Voer een variabele in die **PSSession** -objecten bevat of een opdracht waarmee de **PSSession** -objecten, zoals een of-opdracht, worden gemaakt of opgehaald `New-PSSession` `Get-PSSession` .

Wanneer u een **PSSession** maakt, brengt Power shell een permanente verbinding met de externe computer tot stand. Gebruik een **PSSession** om een reeks gerelateerde opdrachten uit te voeren die gegevens delen. Als u één opdracht of een reeks niet-gerelateerde opdrachten wilt uitvoeren, gebruikt u de para meter **ComputerName** . Zie [about_PSSessions](./About/about_PSSessions.md)voor meer informatie.

```yaml
Type: System.Management.Automation.Runspaces.PSSession[]
Parameter Sets: FilePathRunspace, Session
Aliases:

Required: False
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Sessie naam

Hiermee geeft u een beschrijvende naam op voor een niet-verbonden sessie. U kunt de naam gebruiken om te verwijzen naar de sessie in volgende opdrachten, zoals een `Get-PSSession` opdracht. Deze para meter is alleen geldig voor de para meter **InDisconnectedSession** .

Deze para meter is geïntroduceerd in Power Shell 3,0.

```yaml
Type: System.String[]
Parameter Sets: ComputerName, FilePathComputerName
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -SessionOption

Hiermee geeft u geavanceerde opties voor de sessie op. Voer een **SessionOption** -object in, zoals het account dat u maakt met behulp van de `New-PSSessionOption` cmdlet of een hash-tabel waarin de sleutels de namen van sessie opties zijn en de waarden zijn waarden voor de sessie.

De standaard waarden voor de opties worden bepaald door de waarde van de `$PSSessionOption` Voorkeurs variabele, als deze is ingesteld. Anders worden de standaard waarden bepaald door opties die zijn ingesteld in de sessie configuratie.

De waarden van de sessie optie hebben voor rang op de standaard waarden voor sessies die zijn ingesteld in de `$PSSessionOption` Voorkeurs variabele en in de sessie configuratie. Ze hebben echter geen voor rang op de maximum waarden, quota's of limieten die zijn ingesteld in de sessie configuratie.

Zie voor een beschrijving van de sessie opties die de standaard waarden bevatten `New-PSSessionOption` . Zie about_Preference_Variables voor meer informatie over de `$PSSessionOption` voorkeurs [about_Preference_Variables](About/about_Preference_Variables.md)variabele.
Zie [about_Session_Configurations](About/about_Session_Configurations.md) (Engelstalig) voor meer informatie over sessieconfiguraties.

```yaml
Type: System.Management.Automation.Remoting.PSSessionOption
Parameter Sets: ComputerName, FilePathComputerName, Uri, FilePathUri
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -SSHConnection

Deze para meter gebruikt een matrix van hash-tabellen waarbij elke hash-tabel een of meer verbindings parameters bevat die nodig zijn om een SSH-verbinding (Secure Shell) tot stand te brengen. De **SSHConnection** -para meter is handig voor het maken van meerdere sessies waarbij voor elke sessie verschillende verbindings gegevens zijn vereist.

De hashtabel bevat de volgende leden:

- **ComputerName** (of **hostnaam** )
- **Poort**
- **Gebruikers**
- Het **bestandspad** (of **IdentityFilePath** )

**ComputerName** (of **hostnaam** ) is het enige sleutel-waardepaar dat vereist is.

Deze para meter is geïntroduceerd in Power shell 6,0.

```yaml
Type: System.Collections.Hashtable[]
Parameter Sets: SSHHostHashParam, FilePathSSHHostHash
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -SSHTransport

Geeft aan dat de externe verbinding tot stand is gebracht met behulp van Secure Shell (SSH).

Power Shell maakt standaard gebruik van Windows WinRM om verbinding te maken met een externe computer. Met deze switch wordt Power shell gedwongen de para meter **hostname** te gebruiken om een externe verbinding op basis van SSH tot stand te brengen.

Deze para meter is geïntroduceerd in Power shell 6,0.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: SSHHost, FilePathSSHHost
Aliases:
Accepted values: true

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### -ThrottleLimit

Hiermee geeft u het maximum aantal gelijktijdige verbindingen op dat tot stand kan worden gebracht om deze opdracht uit te voeren.
Als u deze para meter weglaat of een waarde van 0 invoert, wordt de standaard waarde 32 gebruikt.

De beperkings limiet geldt alleen voor de huidige opdracht, niet voor de sessie of voor de computer.

```yaml
Type: System.Int32
Parameter Sets: FilePathRunspace, Session, ComputerName, FilePathComputerName, Uri, FilePathUri, VMId, VMName, FilePathVMId, FilePathVMName, ContainerId, FilePathContainerId
Aliases:

Required: False
Position: Named
Default value: 32
Accept pipeline input: False
Accept wildcard characters: False
```

### -GebruikersNaam

Hiermee geeft u de gebruikers naam op voor het account dat wordt gebruikt om een opdracht uit te voeren op de externe computer. De verificatie methode voor de gebruiker is afhankelijk van hoe Secure Shell (SSH) is geconfigureerd op de externe computer.

Als SSH is geconfigureerd voor basis wachtwoord verificatie, wordt u gevraagd om het wacht woord van de gebruiker.

Als SSH is geconfigureerd voor gebruikers authenticatie op basis van sleutels, kan een pad naar een sleutel bestand worden opgegeven **via de para** meter voor het sleutelpad en wordt er geen wachtwoord prompt weer gegeven. Als het sleutel bestand van de client gebruiker zich in een bekende SSH-locatie bevindt, is de para meter voor het sleutelpad niet nodig voor verificatie op basis van een sleutel en **wordt de gebruikers** verificatie automatisch uitgevoerd op basis van de gebruikers naam. Zie de SSH-documentatie van uw platform over gebruikers verificatie op basis van een sleutel voor meer informatie.

Dit is geen vereiste para meter. Als de para meter **username** niet is opgegeven, wordt de huidige aangemelde gebruikers naam gebruikt voor de verbinding.

Deze para meter is geïntroduceerd in Power shell 6,0.

```yaml
Type: System.String
Parameter Sets: SSHHost, FilePathSSHHost
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -UseSSL

Geeft aan dat deze cmdlet het Secure Sockets Layer-Protocol (SSL) gebruikt om verbinding te maken met de externe computer. SSL wordt standaard niet gebruikt.

WS-Management versleutelt alle Power shell-inhoud die via het netwerk wordt verzonden. De para meter **UseSSL** is een extra beveiliging waarbij de gegevens worden verzonden via een HTTPS, in plaats van via http.

Als u deze para meter gebruikt, maar SSL niet beschikbaar is op de poort die wordt gebruikt voor de opdracht, mislukt de opdracht.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: ComputerName, FilePathComputerName
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### -VMId

Hiermee geeft u een matrix met Id's van virtuele machines op.

```yaml
Type: System.Guid[]
Parameter Sets: VMId, FilePathVMId
Aliases: VMGuid

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -VMName

Hiermee geeft u een matrix met namen van virtuele machines op.

```yaml
Type: System.String[]
Parameter Sets: VMName, FilePathVMName
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -Subsysteem

Hiermee geeft u het SSH-subsysteem op dat wordt gebruikt voor de nieuwe **PSSession**.

Hiermee geeft u het subsysteem op dat moet worden gebruikt op het doel zoals gedefinieerd in sshd_config.
Het subsysteem start een specifieke versie van Power shell met vooraf gedefinieerde para meters.
Als het opgegeven subsysteem niet bestaat op de externe computer, mislukt de opdracht.

Als deze para meter niet wordt gebruikt, is de standaard het subsysteem Power shell.

```yaml
Type: System.String
Parameter Sets: SSHHost
Aliases:

Required: False
Position: Named
Default value: powershell
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### CommonParameters

Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable. Zie [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)voor meer informatie.

## INVOER

### System. Management. Automation. script Block

U kunt een opdracht in een script blok door sluizen naar `Invoke-Command` . Gebruik de `$Input` Automatische variabele om de invoer objecten in de opdracht weer te geven.

## UITVOER

### System. Management. Automation. PSRemotingJob, System. Management. Automation. Runspaces. PSSession, of de uitvoer van de aangeroepen opdracht

Met deze cmdlet wordt een taak object geretourneerd als u de para meter **AsJob** gebruikt. Als u de para meter **InDisconnectedSession** opgeeft, `Invoke-Command` wordt een **PSSession** -object geretourneerd. Anders wordt de uitvoer van de aangeroepen opdracht geretourneerd. Dit is de waarde van de para meter **script Block** .

## OPMERKINGEN

In Windows Vista en latere versies van het Windows-besturings systeem **ComputerName** `Invoke-Command` moet u Power shell uitvoeren met de optie **als administrator uitvoeren** om de para meter ComputerName van te gebruiken voor het uitvoeren van een opdracht op de lokale computer.

Wanneer u opdrachten op meerdere computers uitvoert, maakt Power shell verbinding met de computers in de volg orde waarin ze worden weer gegeven in de lijst. De uitvoer van de opdracht wordt echter weer gegeven in de volg orde waarin deze worden ontvangen van de externe computers. Dit kan anders zijn.

Fouten die het resultaat zijn van de opdracht die `Invoke-Command` wordt uitgevoerd, worden opgenomen in de opdracht resultaten.
Fouten waarvoor fouten in een lokale opdracht zouden worden beëindigd, worden beschouwd als niet-afsluit fouten in een externe opdracht. Deze strategie zorgt ervoor dat het beëindigen van fouten op één computer de opdracht niet sluit op alle computers waarop deze wordt uitgevoerd. Deze procedure wordt ook gebruikt wanneer een externe opdracht wordt uitgevoerd op één computer.

Als de externe computer zich niet in een domein bevindt dat de lokale computer vertrouwt, is de computer mogelijk niet in staat om de referenties van de gebruiker te verifiëren. Als u de externe computer wilt toevoegen aan de lijst met vertrouwde hosts in WS-Management, gebruikt u de volgende opdracht in de `WSMAN` provider, waarbij `<Remote-Computer-Name>` de naam is van de externe computer:

`Set-Item -Path WSMan:\Localhost\Client\TrustedHosts -Value \<Remote-Computer-Name\>`

Wanneer u een **PSSession** verbreekt met de para meter **InDisconnectedSession** , wordt de sessie status **losgekoppeld** en is de beschik baarheid **geen**. De waarde van de eigenschap **State** is relatief ten opzichte van de huidige sessie. Als de waarde voor de **verbinding is verbroken** , betekent dit dat de **PSSession** niet is verbonden met de huidige sessie. Dit betekent echter niet dat de **PSSession** van de verbinding met alle sessies is verbroken. Deze is mogelijk verbonden met een andere sessie. Gebruik de eigenschap **Beschik baarheid** om te bepalen of u verbinding kunt maken met de sessie of er opnieuw verbinding mee wilt maken.

Een **beschikbaarheids** waarde van **geen** geeft aan dat u verbinding kunt maken met de sessie. De waarde **bezet** geeft aan dat u geen verbinding kunt maken met de **PSSession** , omdat deze is verbonden met een andere sessie. Zie [RunspaceState](/dotnet/api/system.management.automation.runspaces.runspacestate)voor meer informatie over de waarden van de eigenschap **State** van sessies. Zie [RunspaceAvailability](/dotnet/api/system.management.automation.runspaces.runspaceavailability)voor meer informatie over de waarden van de eigenschap **Beschik baarheid** van sessies.

De para meters **hostname** en **SSHConnection** zijn opgenomen vanaf Power shell 6,0. Ze zijn toegevoegd om Power shell Remoting te bieden op basis van de Secure Shell (SSH). Power shell en SSH worden ondersteund op meerdere platformen (Windows, Linux, macOS) en externe communicatie van Power shell werkt op deze platforms waarin Power shell en SSH zijn geïnstalleerd en geconfigureerd. Dit is gescheiden van de vorige Windows-functie voor externe toegang die is gebaseerd op WinRM en veel van de specifieke WinRM-functies en-beperkingen zijn niet van toepassing. Bijvoorbeeld: op WinRM gebaseerde quota's, sessie opties, aangepaste eindpunt configuratie en functies voor ontkoppelen/opnieuw verbinden worden op dit moment niet ondersteund. Zie voor meer informatie over het instellen van externe toegang tot Power shell [via SSH Power shell](/powershell/scripting/learn/remoting/ssh-remoting-in-powershell-core).

## GERELATEERDE KOPPELINGEN

[about_PSSessions](./About/about_PSSessions.md)

[about_Remote](./About/about_Remote.md)

[about_Remote_Disconnected_Sessions](./About/about_Remote_Disconnected_Sessions.md)

[about_Remote_Troubleshooting](./About/about_remote_troubleshooting.md)

[about_Remote_Variables](./About/about_Remote_Variables.md)

[about_Scopes](./About/about_scopes.md)

[Enter-PSSession](Enter-PSSession.md)

[Afsluiten-PSSession](Exit-PSSession.md)

[Get-PSSession](Get-PSSession.md)

[Invoke-item](../Microsoft.PowerShell.Management/Invoke-Item.md)

[New-PSSession](New-PSSession.md)

[Remove-PSSession](Remove-PSSession.md)

[WSMan Provider](../Microsoft.WsMan.Management/About/about_WSMan_Provider.md)

