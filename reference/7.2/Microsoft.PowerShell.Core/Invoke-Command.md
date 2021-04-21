---
external help file: System.Management.Automation.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 04/08/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/invoke-command?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Invoke-opdracht
ms.openlocfilehash: bd34c20843720b5900e3a6d594939934624d1b13
ms.sourcegitcommit: b10731301412afd4111743b85da95e8c25583533
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 04/20/2021
ms.locfileid: "107756321"
---
# Invoke-opdracht

## Synopsis
Opdrachten worden uitgevoerd op lokale en externe computers.

## Syntax

### InProcess (standaard)

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

### Uri

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
 [-Subsystem <String>] [-ConnectingTimeout <int>] [<CommonParameters>]
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

## Description

De cmdlet voert opdrachten uit op een lokale of externe computer en retourneert alle uitvoer van de `Invoke-Command` opdrachten, inclusief fouten. Met één opdracht `Invoke-Command` kunt u opdrachten uitvoeren op meerdere computers.

Als u één opdracht wilt uitvoeren op een externe computer, gebruikt u de parameter **ComputerName.** Als u een reeks gerelateerde opdrachten wilt uitvoeren die gegevens delen, gebruikt u de cmdlet om een `New-PSSession` **PSSession** (een permanente verbinding) te maken op de externe computer en gebruikt u vervolgens de parameter **Session** van om de opdracht uit te voeren `Invoke-Command` in de **PSSession**. Als u een opdracht wilt uitvoeren in een sessie zonder verbinding, gebruikt u de parameter **InDisconnectedSession.** Als u een opdracht wilt uitvoeren in een achtergrondjob, gebruikt u de parameter **AsJob.**

U kunt ook op `Invoke-Command` een lokale computer gebruiken om een blok script als een opdracht. PowerShell voert het scriptblok onmiddellijk uit in een onderliggend bereik van het huidige bereik.

Lees voordat u gebruikt om opdrachten uit te voeren op een `Invoke-Command` externe computer [about_Remote.](./About/about_Remote.md)

Vanaf PowerShell 6.0 kunt u Secure Shell (SSH) gebruiken om verbinding te maken met en opdrachten aan te roepen op externe computers. SSH moet worden geïnstalleerd op de lokale computer en de externe computer moet worden geconfigureerd met een PowerShell SSH-eindpunt. Het voordeel van een externe PowerShell-sessie op basis van SSH is dat deze op meerdere platforms werkt (Windows, Linux, macOS). Voor een SSH-sessie gebruikt u de parameters **HostName** of **SSHConnection** om de externe computer en relevante verbindingsgegevens op te geven. Zie Voor meer informatie over het instellen van remoting via PowerShell SSH [Via SSH.](/powershell/scripting/learn/remoting/ssh-remoting-in-powershell-core)

Sommige codevoorbeelden gebruiken splatting om de regellengte te verminderen. Zie voor meer informatie [about_Splatting](./About/about_Splatting.md).

## Voorbeelden

### Voorbeeld 1: een script uitvoeren op een server

In dit voorbeeld wordt het `Test.ps1` script uitgevoerd op de computer Server01.

```powershell
Invoke-Command -FilePath c:\scripts\test.ps1 -ComputerName Server01
```

De **FilePath** parameter geeft u een script dat zich op de lokale computer bevindt. Het script wordt uitgevoerd op de externe computer en de resultaten worden geretourneerd naar de lokale computer.

### Voorbeeld 2: een opdracht uitvoeren op een externe server

In dit voorbeeld wordt een `Get-Culture` opdracht uitgevoerd op de externe computer Server01.

```powershell
Invoke-Command -ComputerName Server01 -Credential Domain01\User01 -ScriptBlock { Get-Culture }
```

De **ComputerName** parameter geeft u de naam van de externe computer. De **referentie** parameter wordt gebruikt voor het uitvoeren van de opdracht in de beveiligingscontext van Domain01\User01, een gebruiker die is machtigingen voor het uitvoeren van opdrachten. De **ScriptBlock** parameter geeft u de opdracht moet worden uitgevoerd op de externe computer.

Als antwoord vraagt PowerShell het wachtwoord en een verificatiemethode voor het account User01 aan.
Vervolgens wordt de opdracht uitgevoerd op de computer Server01 en wordt het resultaat retourneert.

### Voorbeeld 3: Een opdracht uitvoeren in een permanente verbinding

In dit voorbeeld wordt dezelfde opdracht uitgevoerd in een sessie, met behulp van `Get-Culture` een permanente verbinding, op de externe computer met de naam Server02.

```powershell
$s = New-PSSession -ComputerName Server02 -Credential Domain01\User01
Invoke-Command -Session $s -ScriptBlock {Get-Culture}
```

De `New-PSSession` cmdlet maakt een sessie op de externe computer Server02 en slaat deze op in de `$s` variabele . Normaal gesproken maakt u een sessie alleen wanneer u een reeks opdrachten op de externe computer uitvoeren.

De `Invoke-Command` cmdlet voert de `Get-Culture` opdracht uit op Server02. De **sessie** parameter geeft u de sessie opgeslagen in de `$s` variabele.

Als antwoord voert PowerShell de opdracht uit in de sessie op de server02-computer.

### Voorbeeld 4: Een sessie gebruiken om een reeks opdrachten uit te voeren die gegevens delen

In dit voorbeeld worden de effecten van het gebruik van **de parameters ComputerName** en **Session** van `Invoke-Command` vergeleken. U ziet hoe u een sessie gebruikt om een reeks opdrachten uit te voeren die dezelfde gegevens delen.

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

De eerste twee opdrachten gebruiken de **ComputerName** parameter van `Invoke-Command` om opdrachten uit te voeren op de externe computer Server02. De eerste opdracht gebruikt de `Get-Process` cmdlet om het PowerShell-proces op de externe computer op te halen en op te slaan in de `$p` variabele . Met de tweede opdracht wordt de waarde van de eigenschap **VirtualMemorySize van** het PowerShell-proces opgeslagen.

Wanneer u de **parameter ComputerName gebruikt,** maakt PowerShell een nieuwe sessie om de opdracht uit te voeren.
De sessie wordt gesloten wanneer de opdracht is voltooid. De variabele is gemaakt in één verbinding, maar deze bestaat niet in de verbinding die is gemaakt `$p` voor de tweede opdracht.

Het probleem wordt opgelost door een permanente sessie te maken op de externe computer en vervolgens beide opdrachten in dezelfde sessie uit te voeren.

De `New-PSSession` cmdlet maakt een permanente sessie op de computer Server02 en slaat de sessie op in de `$s` variabele . De `Invoke-Command` volgende regels gebruiken de **sessieparameter** om beide opdrachten in dezelfde sessie uit te voeren. Omdat beide opdrachten in dezelfde sessie worden uitgevoerd, blijft `$p` de waarde actief.

### Voorbeeld 5: Voer een opdracht in die is opgeslagen in een lokale variabele

In dit voorbeeld ziet u hoe u een opdracht maakt die is opgeslagen als een scriptblok in een lokale variabele.
Wanneer het scriptblok wordt opgeslagen in een lokale variabele, kunt u de variabele opgeven als de waarde van de parameter **ScriptBlock.**

```powershell
$command = { Get-WinEvent -LogName PowerShellCore/Operational |
  Where-Object {$_.Message -like "*certificate*"} }
Invoke-Command -ComputerName S1, S2 -ScriptBlock $command
```

De `$command` variabele slaat de opdracht op die is opgemaakt als een `Get-WinEvent` scriptblok. De `Invoke-Command` voert de opdracht uit die is opgeslagen in op de externe computers `$command` S1 en S2.

### Voorbeeld 6: Een enkele opdracht uitvoeren op verschillende computers

In dit voorbeeld wordt gedemonstreerd hoe `Invoke-Command` u gebruikt om één opdracht uit te voeren op meerdere computers.

```powershell
$parameters = @{
  ComputerName = "Server01", "Server02", "TST-0143", "localhost"
  ConfigurationName = 'MySession.PowerShell'
  ScriptBlock = { Get-WinEvent -LogName PowerShellCore/Operational }
}
Invoke-Command @parameters
```

De **ComputerName** parameter geeft u een door komma's gescheiden lijst met computernamen. De lijst met computers bevat de localhost-waarde, die de lokale computer vertegenwoordigt. De **ConfigurationName** parameter geeft u een alternatieve sessieconfiguratie. De **parameter ScriptBlock** wordt uitgevoerd `Get-WinEvent` om de gebeurtenislogboeken van PowerShellCore/Operational op te halen van elke computer.

### Voorbeeld 7: de versie van het hostprogramma op meerdere computers op halen

In dit voorbeeld wordt de versie van het PowerShell-hostprogramma op 200 externe computers uitgevoerd.

```powershell
$version = Invoke-Command -ComputerName (Get-Content Machines.txt) -ScriptBlock {(Get-Host).Version}
```

Omdat er slechts één opdracht wordt uitgevoerd, hoeft u geen permanente verbindingen met elk van de computers te maken. In plaats daarvan gebruikt de opdracht de **Parameter ComputerName** om de computers aan te geven. Als u de computers wilt opgeven, wordt de cmdlet gebruikt om de inhoud van het Machine.txt op te halen, een bestand `Get-Content` met computernamen.

De `Invoke-Command` cmdlet voert een `Get-Host` opdracht uit op de externe computers. Er wordt een punt-notatie gebruikt om de **eigenschap Version van** de PowerShell-host op te halen.

Deze opdrachten worden één voor één uitgevoerd. Wanneer de opdrachten zijn voltooid, wordt de uitvoer van de opdrachten van alle computers opgeslagen in de `$version` variabele . De uitvoer bevat de naam van de computer van waaruit de gegevens afkomstig zijn.

### Voorbeeld 8: een achtergrond taak uitvoeren op verschillende externe computers

In dit voorbeeld wordt een opdracht uitgevoerd op twee externe computers. De `Invoke-Command` opdracht maakt gebruik van de Parameter **AsJob** zodat de opdracht wordt uitgevoerd als een achtergrond job. De opdrachten worden uitgevoerd op de externe computers, maar de taak bestaat op de lokale computer. De resultaten worden verzonden naar de lokale computer.

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

De `New-PSSession` cmdlet maakt sessies op de externe computers Server01 en Server02. De `Invoke-Command` cmdlet voert in elk van de sessies een achtergrond job uit. De opdracht gebruikt de **parameter AsJob** om de opdracht uit te voeren als achtergrondjob. Deze opdracht retourneert een taakobject dat twee onderliggende taakobjecten bevat, één voor elk van de taken die op de twee externe computers worden uitgevoerd.

De `Get-Job` opdracht slaat het taakobject op in de variabele `$j` . De `$j` variabele wordt vervolgens doorspijpt naar de cmdlet om alle eigenschappen van het `Format-List` taakobject in een lijst weer te geven. De laatste opdracht haalt de resultaten van de taken op. Het taakobject wordt naar de `$j` `Receive-Job` cmdlet doorgespijpt en de resultaten worden opgeslagen in de `$results` variabele .

### Voorbeeld 9: lokale variabelen opnemen in een opdracht die wordt uitgevoerd op een externe computer

In dit voorbeeld ziet u hoe u de waarden van lokale variabelen op te nemen in een opdracht die wordt uitgevoerd op een externe computer. De opdracht maakt gebruik van `Using` de scope-modifier om een lokale variabele in een externe opdracht te identificeren. Standaard wordt aangenomen dat alle variabelen worden gedefinieerd in de externe sessie. De `Using` scope-modifier is geïntroduceerd in PowerShell 3.0. Zie voor meer informatie over `Using` de scope-modifier [about_Remote_Variables](./About/about_Remote_Variables.md) en [about_Scopes.](./about/about_scopes.md)

```powershell
$Log = "PowerShellCore/Operational"
Invoke-Command -ComputerName Server01 -ScriptBlock {Get-WinEvent -LogName $Using:Log -MaxEvents 10}
```

De `$Log` variabele slaat de naam op van het gebeurtenislogboek, PowerShellCore/Operational. De `Invoke-Command` cmdlet wordt uitgevoerd op Server01 om de tien nieuwste gebeurtenissen uit `Get-WinEvent` het gebeurtenislogboek op te halen. De waarde van de **LogName** parameter is de variabele die wordt voorafgemaakt door de bereik modifier om aan te geven dat deze is gemaakt in de lokale sessie, niet in de `$Log` `Using` externe sessie.

### Voorbeeld 10: de computernaam verbergen

In dit voorbeeld ziet u het effect van het gebruik van de parameter **HideComputerName** van `Invoke-Command` .
**HideComputerName** wijzigt het object dat deze cmdlet retourneert niet. Alleen de weergave wordt gewijzigd. U kunt nog  steeds de Opmaak-cmdlets gebruiken om de eigenschap **PsComputerName** van een van de betrokken objecten weer te geven.

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

De eerste twee opdrachten gebruiken om `Invoke-Command` een opdracht uit te voeren voor het `Get-Process` PowerShell-proces. De uitvoer van de eerste opdracht bevat de eigenschap **PsComputerName,** die de naam bevat van de computer waarop de opdracht is uitgevoerd. De uitvoer van de tweede opdracht, die **gebruikmaakt van HideComputerName,** bevat niet de **kolom PsComputerName.**

### Voorbeeld 11: Het sleutelwoord Param gebruiken in een scriptblok

Het `Param` trefwoord en de **parameter ArgumentList** worden gebruikt om variabele waarden door te geven aan benoemde parameters in een scriptblok. In dit voorbeeld worden bestandsnamen weergegeven die beginnen met de letter `a` en de extensie `.pdf` hebben.

Zie voor meer informatie over `Param` het [trefwoord about_Language_Keywords](./about/about_language_keywords.md#param).

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

`Invoke-Command` gebruikt de **parameter ScriptBlock** die twee variabelen definieert, `$param1` en `$param2` . `Get-ChildItem` maakt gebruik van de benoemde **parameters, Naam** **en Opnemen** met de namen van variabelen. De **ArgumentList** geeft de waarden door aan de variabelen.

### Voorbeeld 12: De automatische $args in een scriptblok gebruiken

De automatische variabele en de parameter ArgumentList worden gebruikt om matrixwaarden door te geven aan `$args` parameterposities  in een scriptblok. In dit voorbeeld wordt de mapinhoud van bestanden van een `.txt` server weergegeven. De `Get-ChildItem` **parameter Path** is positie 0 en de **filterparameter** is positie
1.

Zie voor meer informatie `$args` over de [variabele about_Automatic_Variables](./about/about_automatic_variables.md#args)

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

`Invoke-Command` gebruikt een **ScriptBlock-parameter** en `Get-ChildItem` geeft de `$args[0]` matrixwaarden en `$args[1]` op. De **ArgumentList geeft** de `$args` matrixwaarden door aan de `Get-ChildItem` parameterposities **voor Pad** en **Filter.**

### Voorbeeld 13: Een script uitvoeren op alle computers die worden vermeld in een tekstbestand

In dit voorbeeld wordt de `Invoke-Command` cmdlet gebruikt om het `Sample.ps1` script uit te voeren op alle computers die in het bestand worden `Servers.txt` vermeld. De opdracht gebruikt de **parameter FilePath** om het scriptbestand op te geven. Met deze opdracht kunt u het script uitvoeren op de externe computers, zelfs als het scriptbestand niet toegankelijk is voor de externe computers.

```powershell
Invoke-Command -ComputerName (Get-Content Servers.txt) -FilePath C:\Scripts\Sample.ps1 -ArgumentList Process, Service
```

Wanneer u de opdracht indient, wordt de inhoud van het bestand gekopieerd naar een scriptblok en wordt het `Sample.ps1` scriptblok uitgevoerd op elk van de externe computers. Deze procedure is gelijk aan het gebruik van de parameter **ScriptBlock** om de inhoud van het script in te dienen.

### Voorbeeld 14: Een opdracht uitvoeren op een externe computer met behulp van een URI

In dit voorbeeld ziet u hoe u een opdracht kunt uitvoeren op een externe computer die wordt geïdentificeerd door een Uniform Resource Identifier (URI). In dit specifieke voorbeeld wordt een `Set-Mailbox` opdracht uitgevoerd op een externe Exchange-server.

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

De eerste regel maakt gebruik van `Get-Credential` de cmdlet voor het opslaan van Windows Live ID-referenties in de `$LiveCred` variabele . PowerShell vraagt de gebruiker om Windows Live ID-referenties in te voeren.

De `$parameters` variabele is een hashtabel met de parameters die moeten worden doorgegeven aan de `Invoke-Command` cmdlet . De `Invoke-Command` cmdlet voert een opdracht `Set-Mailbox` uit met behulp van de **sessieconfiguratie Microsoft.Exchange.** Met **de parameter ConnectionURI** wordt de URL van het Exchange-server-eindpunt opgegeven. De **referentie** parameter geeft u de referenties die zijn opgeslagen in de `$LiveCred` variabele. De **AuthenticationMechanism** parameter geeft u het gebruik van basisverificatie. Met de parameter **ScriptBlock** geeft u een scriptblok op dat de opdracht bevat.

### Voorbeeld 15: Een sessieoptie gebruiken

In dit voorbeeld ziet u hoe u een **SessionOption-parameter maakt en** gebruikt.

```powershell
$so = New-PSSessionOption -SkipCACheck -SkipCNCheck -SkipRevocationCheck
Invoke-Command -ComputerName server01 -UseSSL -ScriptBlock { Get-HotFix } -SessionOption $so -Credential server01\user01
```

De cmdlet maakt een sessieoptieobject dat ervoor zorgt dat de externe end de certificeringsinstantie, canonieke naam en intrekkingslijsten niet verifieert tijdens het evalueren van de binnenkomende `New-PSSessionOption` HTTPS-verbinding. Het **object SessionOption** wordt opgeslagen in de `$so` variabele .

> [!NOTE]
> Het uitschakelen van deze controles is handig voor het oplossen van problemen, maar is natuurlijk niet veilig.

De `Invoke-Command` cmdlet voert een `Get-HotFix` opdracht op afstand uit. De **parameter SessionOption** krijgt de `$so` variabele .

### Voorbeeld 16: URI-omleiding beheren in een externe opdracht

In dit voorbeeld ziet u hoe u de **parameters AllowRedirection** en **SessionOption** gebruikt voor het beheren van URI-omleiding in een externe opdracht.

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

De `New-PSSessionOption` cmdlet maakt een **PSSessionOption-object** dat wordt opgeslagen in de `$max` variabele . De opdracht gebruikt de **parameter MaximumRedirection** om de eigenschap **MaximumConnectionRedirectionCount** van het **PSSessionOption-object** in te stellen op 1.

De `Invoke-Command` cmdlet voert een `Get-Mailbox` opdracht uit op een externe Microsoft Exchange-server. De **parameter AllowRedirection** biedt expliciete machtigingen om de verbinding om te leiden naar een alternatief eindpunt. De **parameter SessionOption** maakt gebruik van het sessieobject dat is opgeslagen in de `$max` variabele .

Als gevolg hiervan, als de externe computer die is opgegeven door **ConnectionURI** een omleidingsbericht retourneert, wordt de verbinding door PowerShell omgeleid, maar als de nieuwe bestemming een ander omleidingsbericht retourneert, wordt de waarde van het aantal omleidingen van 1 overschreden en wordt een `Invoke-Command` niet-beëindigingsfout retourneert.

### Voorbeeld 17: Toegang tot een netwerk share in een externe sessie

In dit voorbeeld ziet u hoe u toegang krijgt tot een netwerk share vanuit een externe sessie. Er worden drie computers gebruikt om het voorbeeld te demonstreren. Server01 is de lokale computer, Server02 is de externe computer en Net03 bevat de netwerk share. Server01 maakt verbinding met Server02 en server02 maakt vervolgens een tweede hop naar Net03 om toegang te krijgen tot de netwerk share. Zie Making the second hop in PowerShell Remoting (De tweede [hop maken in Remoting van PowerShell) voor meer](/powershell/scripting/learn/remoting/ps-remoting-second-hop)informatie over hoe remoting van PowerShell hops tussen computers ondersteunt.

De vereiste credSSP-delegering (Credential Security Support Provider) wordt ingeschakeld in de clientinstellingen op de lokale computer en in de service-instellingen op de externe computer. Als u de opdrachten in dit voorbeeld wilt uitvoeren, moet u lid zijn van de groep **Administrators** op de lokale computer en de externe computer.

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

De `Enable-WSManCredSSP` cmdlet schakelt CredSSP-overdracht van de lokale computer Server01 naar de externe computer Server02. De **rol** parameter geeft u **client voor** het configureren van de CredSSP-clientinstelling op de lokale computer.

`New-PSSession` maakt een **PSSession-object** voor Server02 en slaat het object op in de `$s` variabele .

De `Invoke-Command` cmdlet gebruikt de `$s` variabele om verbinding te maken met de externe computer Server02. De **ScriptBlock** parameter wordt `Enable-WSManCredSSP` uitgevoerd op de externe computer. De **rol** parameter geeft u **Server** voor het configureren van de CredSSP-serverinstelling op de externe computer.

De `$parameters` variabele bevat de parameterwaarden om verbinding te maken met de netwerk share. De `Invoke-Command` cmdlet voert een `Get-Item` opdracht uit in de sessie in `$s` . Met deze opdracht haalt u een script op uit de `\\Net03\Scripts` netwerk share. De opdracht gebruikt de **verificatie** parameter met de waarde van **CredSSP en** de **referentie** parameter met de waarde **van Domain01\Admin01.**

### Voorbeeld 18: Scripts starten op veel externe computers

In dit voorbeeld wordt een script uitgevoerd op meer dan honderd computers. Om de impact op de lokale computer te minimaliseren, maakt deze verbinding met elke computer, start het script en wordt vervolgens de verbinding met elke computer verbroken.
Het script blijft worden uitgevoerd in de niet-verbonden sessies.

```powershell
$parameters = @{
  ComputerName = (Get-Content -Path C:\Test\Servers.txt)
  InDisconnectedSession = $true
  FilePath = "\\Scripts\Public\ConfigInventory.ps1"
  SessionOption = @{OutputBufferingMode="Drop";IdleTimeout=43200000}
}
Invoke-Command @parameters
```

De opdracht gebruikt om `Invoke-Command` het script uit te voeren. De waarde van de **ComputerName** parameter is een opdracht die de namen van de externe `Get-Content` computers uit een tekstbestand. Met de parameter **InDisconnectedSession** worden de sessies verbroken zodra de opdracht wordt gestart. De waarde van de **FilePath** parameter is het script dat `Invoke-Command` wordt uitgevoerd op elke computer.

De waarde van **SessionOption** is een hash-tabel. De **waarde OutputBufferingMode** is ingesteld op **Drop** en de **waarde IdleTimeout** op **43200000** milliseconden (12 uur).

Gebruik de cmdlet om de resultaten op te halen van opdrachten en scripts die worden uitgevoerd in niet-verbonden `Receive-PSSession` sessies.

### Voorbeeld 19: een opdracht uitvoeren op een externe computer met behulp van SSH

In dit voorbeeld ziet u hoe u een opdracht kunt uitvoeren op een externe computer met behulp van Secure Shell (SSH). Als SSH is geconfigureerd op de externe computer om te vragen om wachtwoorden, krijgt u een wachtwoordprompt.
Anders moet u gebruikersverificatie op basis van een SSH-sleutel gebruiken.

```powershell
Invoke-Command -HostName UserA@LinuxServer01 -ScriptBlock { Get-MailBox * }
```

### Voorbeeld 20: een opdracht uitvoeren op een externe computer met behulp van SSH en een sleutel voor gebruikersverificatie opgeven

In dit voorbeeld ziet u hoe u een opdracht op een externe computer kunt uitvoeren met behulp van SSH en een sleutelbestand voor gebruikersverificatie kunt opgeven. U wordt niet om een wachtwoord gevraagd, tenzij de sleutelverificatie mislukt en de externe computer is geconfigureerd om eenvoudige wachtwoordverificatie toe te staan.

```powershell
Invoke-Command -HostName UserA@LinuxServer01 -ScriptBlock { Get-MailBox * } -KeyFilePath /UserA/UserAKey_rsa
```

### Voorbeeld 21: Een scriptbestand uitvoeren op meerdere externe computers met SSH als taak

In dit voorbeeld ziet u hoe u een scriptbestand op meerdere externe computers kunt uitvoeren met behulp van SSH en de **parameterset SSHConnection.** De **parameter SSHConnection** maakt gebruik van een matrix met hashtabellen die verbindingsgegevens voor elke computer bevatten. Voor dit voorbeeld is vereist dat op de externe doelcomputers SSH is geconfigureerd ter ondersteuning van op sleutels gebaseerde gebruikersverificatie.

```powershell
$sshConnections =
@{ HostName="WinServer1"; UserName="Domain\UserA"; KeyFilePath="C:\Users\UserA\id_rsa" },
@{ HostName="UserB@LinuxServer5"; KeyFilePath="/Users/UserB/id_rsa" }
$results = Invoke-Command -FilePath c:\Scripts\CollectEvents.ps1 -SSHConnection $sshConnections
```

## Parameters

### -AllowRedirection

Staat omleiding van deze verbinding naar een alternatieve Uniform Resource Identifier (URI) toe.

Wanneer u de **parameter ConnectionURI** gebruikt, kan de externe bestemming een instructie retourneren om om te leiden naar een andere URI. PowerShell leidt verbindingen standaard niet om, maar u kunt deze parameter gebruiken om de verbinding om te leiden.

U kunt ook het aantal keren beperken dat de verbinding wordt omgeleid door de **optiewaarde maximumConnectionRedirectionCount-sessie** te wijzigen. Gebruik de **parameter MaximumRedirection** van de cmdlet of stel de eigenschap `New-PSSessionOption` **MaximumConnectionRedirectionCount** van de `$PSSessionOption` voorkeursvariabele in. De standaardwaarde is 5.

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

Hiermee geeft u het toepassingsnaamsegment van de verbindings-URI op. Gebruik deze parameter om de naam van de toepassing op te geven wanneer u de **parameter ConnectionURI** niet gebruikt in de opdracht .

De standaardwaarde is de waarde van de `$PSSessionApplicationName` voorkeursvariabele op de lokale computer. Als deze voorkeursvariabele niet is gedefinieerd, is de standaardwaarde WSMAN. Deze waarde is geschikt voor de meeste toepassingen. Zie voor meer informatie [about_Preference_Variables](./About/about_Preference_Variables.md).

De WinRM-service gebruikt de toepassingsnaam om een listener te selecteren om de verbindingsaanvraag te verwerken.
De waarde van deze parameter moet overeenkomen met de waarde van de **eigenschap URLPrefix** van een listener op de externe computer.

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

### -ArgumentList

Levert de waarden van lokale variabelen in de opdracht. De variabelen in de opdracht worden vervangen door deze waarden voordat de opdracht wordt uitgevoerd op de externe computer. Voer de waarden in een door komma's gescheiden lijst in. Waarden zijn gekoppeld aan variabelen in de volgorde waarin ze worden weergegeven. De alias voor **ArgumentList** is Args.

De waarden in de parameter **ArgumentList** kunnen werkelijke waarden zijn, zoals 1024, of ze kunnen verwijzingen zijn naar lokale variabelen, zoals `$max` .

Als u lokale variabelen in een opdracht wilt gebruiken, gebruikt u de volgende opdrachtindeling:

`{param($<name1>[, $<name2>]...) <command-with-local-variables>} -ArgumentList <value>` -or- `<local-variable>`

Het **sleutelwoord param** bevat de lokale variabelen die worden gebruikt in de opdracht. **ArgumentList** levert de waarden van de variabelen in de volgorde waarin ze worden vermeld. Zie voor meer informatie over het gedrag van **ArgumentList** [about_Splatting](about/about_Splatting.md#splatting-with-arrays).

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

Geeft aan dat deze cmdlet wordt uitgevoerd de opdracht als achtergrond taak op een externe computer. Gebruik deze parameter om opdrachten uit te voeren die lang duren.

Wanneer u de **Parameter AsJob** gebruikt, retourneert de opdracht een -object dat de taak vertegenwoordigt en geeft vervolgens de opdrachtprompt weer. U kunt in de sessie blijven werken terwijl de taak is voltooien. Gebruik de cmdlets om de `*-Job` taak te beheren. Gebruik de cmdlet om de `Receive-Job` taakresultaten op te halen.

De **Parameter AsJob** lijkt op het gebruik van `Invoke-Command` de cmdlet om een `Start-Job` cmdlet op afstand uit te voeren. Met **AsJob wordt de** taak echter gemaakt op de lokale computer, ook al wordt de taak uitgevoerd op een externe computer. De resultaten van de externe taak worden automatisch geretourneerd naar de lokale computer.

Zie PowerShell-achtergrondtaken voor meer [informatie about_Jobs](About/about_Jobs.md) en [about_Remote_Jobs.](About/about_Remote_Jobs.md)

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

Hiermee geeft u het mechanisme op dat wordt gebruikt om de referenties van de gebruiker te verifiëren. CredSSP-verificatie is alleen beschikbaar in Windows Vista, Windows Server 2008 en latere versies van het Windows-besturingssysteem.

De acceptabele waarden voor deze parameter zijn als volgt:

- Standaard
- Basic
- Credssp
- Samenvatting
- Kerberos
- Negotiate
- NegotiateWithImplicitCredential

De standaardwaarde is Standaard.

Zie [AuthenticationMechanism Enumeration](/dotnet/api/system.management.automation.runspaces.authenticationmechanism)voor meer informatie over de waarden van deze parameter.

> [!CAUTION]
> CredSSP-verificatie (Credential Security Support Provider), waarbij de referenties van de gebruiker worden doorgegeven aan een externe computer die moet worden geverifieerd, is ontworpen voor opdrachten waarvoor verificatie op meer dan één resource is vereist, zoals toegang tot een externe netwerk share. Dit mechanisme verhoogt het beveiligingsrisico van de externe bewerking. Als de externe computer is aangetast, kunnen de referenties die worden doorgegeven aan deze worden gebruikt voor het beheer van de netwerksessie. Zie Credential [Security Support Provider (Referentiebeveiligingsondersteuningsprovider) voor meer informatie.](/windows/win32/secauthn/credential-security-support-provider)

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

Hiermee geeft u het digitale openbare-sleutelcertificaat (X509) op van een gebruikersaccount dat is machtigingen heeft om verbinding te maken met de niet-verbonden sessie. Voer de vingerafdruk van het certificaat in.

Certificaten worden gebruikt bij verificatie op basis van clientcertificaten. Ze kunnen alleen worden toe te staan aan lokale gebruikersaccounts en ze werken niet met domeinaccounts.

Gebruik een - of -opdracht in het PowerShell-certificaatstation om een vingerafdruk van het `Get-Item` `Get-ChildItem` certificaat op te halen.

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

Wanneer u de **parameter ComputerName** gebruikt, maakt PowerShell een tijdelijke verbinding die alleen wordt gebruikt om de opgegeven opdracht uit te voeren en vervolgens wordt gesloten. Als u een permanente verbinding nodig hebt, gebruikt u de parameter **Sessie.**

Typ de NETBIOS-naam, het IP-adres of de Fully Qualified Domain Name van een of meer computers in een door komma's gescheiden lijst. Als u de lokale computer wilt opgeven, typt u de computernaam, localhost of een punt ( `.` ).

Als u een IP-adres in de waarde **computernaam** wilt gebruiken, moet de opdracht de parameter **Credential** bevatten. De computer moet worden geconfigureerd voor het HTTPS-transport of het IP-adres van de externe computer moet worden opgenomen in de WinRM **TrustedHosts-lijst van de** lokale computer. Zie How to Add a Computer to the Trusted Host List (Een computer toevoegen aan de lijst met vertrouwde [host)](./about/about_remote_troubleshooting.md#how-to-add-a-computer-to-the-trusted-hosts-list)voor instructies voor het toevoegen van een computernaam aan de **lijst met TrustedHosts.**

In Windows Vista en latere versies van het Windows-besturingssysteem moet u PowerShell uitvoeren met  de optie Als administrator uitvoeren om de lokale computer op te nemen in de waarde **computernaam.**

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

### -ConfigurationName

Hiermee geeft u de sessieconfiguratie op die wordt gebruikt voor de nieuwe **PSSession**.

Voer een configuratienaam of de volledig gekwalificeerde resource-URI in voor een sessieconfiguratie. Als u alleen de configuratienaam opgeeft, wordt de volgende schema-URI toegevoegd: `http://schemas.microsoft.com/PowerShell` .

Wanneer u deze parameter gebruikt met SSH, geeft u het subsysteem op dat moet worden gebruikt op het doel, zoals gedefinieerd in `sshd_config` . De standaardwaarde voor SSH is het `powershell` subsysteem.

De sessieconfiguratie voor een sessie bevindt zich op de externe computer. Als de opgegeven sessieconfiguratie niet bestaat op de externe computer, mislukt de opdracht.

De standaardwaarde is de waarde van de `$PSSessionConfigurationName` voorkeursvariabele op de lokale computer. Als deze voorkeursvariabele niet is ingesteld, is de **standaardwaarde Microsoft.PowerShell.** Zie voor meer informatie [about_Preference_Variables.](about/about_Preference_Variables.md)

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

### -ConnectingTimeout

Hiermee geeft u de hoeveelheid tijd in milliseconden op die is toegestaan voor het voltooien van de eerste SSH-verbinding. Als de verbinding niet binnen de opgegeven tijd is voltooid, wordt er een fout geretourneerd.

Deze parameter is geïntroduceerd in PowerShell 7.2

```yaml
Type: System.Int32
Parameter Sets: SSHHost
Aliases:

Required: False
Position: Named
Default value: unlimited
Accept pipeline input: False
Accept wildcard characters: False
```

### -ConnectionUri

Hiermee geeft u een Uniform Resource Identifier (URI) op die het verbindings-eindpunt van de sessie definieert.
De URI moet volledig gekwalificeerd zijn.

De indeling van deze tekenreeks is als volgt:

`<Transport>://<ComputerName>:<Port>/<ApplicationName>`

De standaardwaarde is als volgt:

`http://localhost:5985/WSMAN`

Als u geen verbindings-URI opgeeft, kunt u de parameters **UseSSL** en **Port** gebruiken om de waarden voor de verbindings-URI op te geven.

Geldige waarden voor het **segment Transport** van de URI zijn HTTP en HTTPS. Als u een verbindings-URI opgeeft met een Transport-segment, maar geen poort opgeeft, wordt de sessie gemaakt met de standaardpoorten: 80 voor HTTP en 443 voor HTTPS. Geef poort 5985 voor HTTP of 5986 voor HTTPS op als u de standaardpoorten wilt gebruiken voor het op andere locatie gebruiken van PowerShell.

Als de doelcomputer de verbinding omleiden naar een andere URI, PowerShell voorkomt de omleiding, tenzij u de **allowRedirection** parameter in de opdracht.

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

Hiermee geeft u een matrix met container-ID's op.

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

Hiermee geeft u een gebruikersaccount op dat is machtigingen heeft om deze actie uit te voeren. Standaard is dit de huidige gebruiker.

Typ een gebruikersnaam, zoals **User01** of **Domain01\User01,** of voer een **PSCredential-object** in dat door de `Get-Credential` cmdlet is gegenereerd. Als u een gebruikersnaam typt, wordt u gevraagd het wachtwoord in te voeren.

Referenties worden opgeslagen in een [PSCredential-object](/dotnet/api/system.management.automation.pscredential) en het wachtwoord wordt opgeslagen als een [SecureString](/dotnet/api/system.security.securestring).

> [!NOTE]
> Zie How secure is **SecureString?** (Hoe veilig is SecureString?) voor meer informatie over [SecureString-gegevensbeveiliging.](/dotnet/api/system.security.securestring#how-secure-is-securestring)

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

Geeft aan dat deze cmdlet een interactief beveiliging token toevoegt aan loopback-sessies. Met het interactieve token kunt u opdrachten uitvoeren in de loopback-sessie die gegevens van andere computers op halen. U kunt bijvoorbeeld een opdracht uitvoeren in de sessie die XML-bestanden kopieert van een externe computer naar de lokale computer.

Een loopback-sessie is **een PSSession** die afkomstig is van en eindigt op dezelfde computer. Als u een loopback-sessie wilt maken, laat u de parameter **ComputerName** weg of stelt u de waarde ervan in op dot ( ), localhost of de `.` naam van de lokale computer.

Loopback-sessies worden standaard gemaakt met behulp van een netwerk-token, dat mogelijk onvoldoende machtigingen biedt voor verificatie bij externe computers.

De **parameter EnableNetworkAccess** is alleen van kracht in loopback-sessies. Als u **EnableNetworkAccess** gebruikt wanneer u een sessie op een externe computer maakt, slaagt de opdracht, maar de parameter wordt genegeerd.

U kunt externe toegang toestaan in een loopback-sessie  met behulp van de **CredSSP-waarde** van de verificatieparameter, die de sessiereferenties delegeert naar andere computers.

Om de computer te beschermen tegen schadelijke toegang, kunnen losgekoppelde loopback-sessies met interactieve tokens, die zijn gemaakt met **EnableNetworkAccess,** alleen opnieuw worden verbonden vanaf de computer waarop de sessie is gemaakt. Niet-verbonden sessies die gebruikmaken van CredSSP-verificatie kunnen opnieuw worden verbonden vanaf andere computers. Voor meer informatie raadpleegt u `Disconnect-PSSession`.

Deze parameter is geïntroduceerd in PowerShell 3.0.

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

Hiermee geeft u een lokaal script dat deze cmdlet wordt uitgevoerd op een of meer externe computers. Voer het pad en de bestandsnaam van het script in of geef een scriptpad door naar `Invoke-Command` . Het script moet bestaan op de lokale computer of in een map waar de lokale computer toegang toe heeft. Gebruik **ArgumentList om** de waarden van parameters in het script op te geven.

Wanneer u deze parameter gebruikt, converteert PowerShell de inhoud van het opgegeven scriptbestand naar een scriptblok, verzendt het scriptblok naar de externe computer en voert het uit op de externe computer.

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

Geeft aan dat deze cmdlet de computernaam van elk object weglaat uit de uitvoerweergave. De naam van de computer die het object heeft gegenereerd, wordt standaard weergegeven in de weergave.

Deze parameter is alleen van invloed op de uitvoerweergave. Het object wordt niet gewijzigd.

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

### -HostName

Hiermee geeft u een matrix met computernamen op voor een SSH-verbinding (Secure Shell). Dit is vergelijkbaar met de **ComputerName** parameter behalve dat de verbinding met de externe computer wordt gemaakt met behulp van SSH in plaats van Windows WinRM.

Deze parameter is geïntroduceerd in PowerShell 6.0.

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

Geeft aan dat deze cmdlet een opdracht of script in een niet-verbonden sessie wordt uitgevoerd.

Wanneer u de **parameter InDisconnectedSession** gebruikt, maakt een permanente sessie op elke externe computer, start u de opdracht die is opgegeven door de parameter ScriptBlock of FilePath en wordt de verbinding met de sessie `Invoke-Command` verbroken.   De opdrachten blijven worden uitgevoerd in de niet-verbonden sessies. **Met InDisconnectedSession kunt** u opdrachten uitvoeren zonder een verbinding met de externe sessies te onderhouden. En omdat de sessie wordt verbroken voordat er resultaten worden geretourneerd, zorgt **InDisconnectedSession** ervoor dat alle opdrachtresultaten worden geretourneerd naar de opnieuw verbonden sessie, in plaats van te worden gesplitst tussen sessies.

U kunt **InDisconnectedSession** niet gebruiken met de parameter **Session** of **de parameter AsJob.**

Opdrachten die **gebruikmaken van InDisconnectedSession retourneren** een **PSSession-object** dat de niet-verbonden sessie vertegenwoordigt. Ze retourneren de opdrachtuitvoer niet. Gebruik de cmdlets of om verbinding te maken met de sessie zonder `Connect-PSSession` `Receive-PSSession` verbinding. Gebruik de cmdlet om de resultaten op te halen van opdrachten die in de `Receive-PSSession` sessie zijn gemaakt. Als u opdrachten wilt uitvoeren die uitvoer genereren in een niet-verbonden sessie, stelt u de waarde van de **sessieoptie OutputBufferingMode** in op **Drop**. Als u verbinding wilt maken met de niet-verbonden sessie, stelt u de time-out voor inactiefheid in de sessie in, zodat u voldoende tijd hebt om verbinding te maken voordat u de sessie kunt verwijderen.

U kunt de uitvoerbuffermodus en niet-actieve time-out instellen in de parameter **SessionOption** of in de `$PSSessionOption` voorkeursvariabele. Zie en about_Preference_Variables voor `New-PSSessionOption` [meer informatie over sessieopties.](./about/about_preference_variables.md)

Zie voor meer informatie over de functie Niet-verbonden [sessies about_Remote_Disconnected_Sessions.](about/about_Remote_Disconnected_Sessions.md)

Deze parameter is geïntroduceerd in PowerShell 3.0.

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

### -InputObject

Hiermee geeft u invoer voor de opdracht. Voer een variabele in die de objecten bevat of typ een opdracht of expressie die de objecten op haalt.

Wanneer u de **parameter InputObject** gebruikt, gebruikt u de automatische variabele in de waarde van de `$Input` parameter **ScriptBlock** om de invoerobjecten weer te geven.

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

Hiermee geeft u een gebruiksvriendelijke naam voor de achtergrond taak. Taken hebben standaard de naam `Job<n>` , waarbij `<n>` een rangnummer is.

Als u de parameter **JobName** in een opdracht gebruikt, wordt de opdracht uitgevoerd als een taak en wordt een taakobject retourneert, zelfs als u AsJob niet in de opdracht `Invoke-Command` opgeeft. 

Zie voor meer informatie over PowerShell-achtergrondtaken [about_Jobs.](./About/about_Jobs.md)

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

### -KeyFilePath

Hiermee geeft u een sleutelbestandspad op dat door Secure Shell (SSH) wordt gebruikt om een gebruiker op een externe computer te verifiëren.

Met SSH kan gebruikersverificatie worden uitgevoerd via persoonlijke en openbare sleutels als alternatief voor basiswachtwoordverificatie. Als de externe computer is geconfigureerd voor sleutelverificatie, kan deze parameter worden gebruikt om de sleutel op te geven waarmee de gebruiker wordt geïdentificeerd.

Deze parameter is geïntroduceerd in PowerShell 6.0.

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

Geeft aan dat deze cmdlet de opgegeven opdracht in het huidige bereik wordt uitgevoerd. Opdrachten worden `Invoke-Command` standaard uitgevoerd in hun eigen bereik.

Deze parameter is alleen geldig in opdrachten die worden uitgevoerd in de huidige sessie, dat wil zeggen opdrachten die weglaten zowel de **ComputerName** en **sessie** parameters.

Deze parameter is geïntroduceerd in PowerShell 3.0.

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

Hiermee geeft u de netwerkpoort op de externe computer die wordt gebruikt voor deze opdracht. Als u verbinding wilt maken met een externe computer, moet de externe computer luisteren op de poort die de verbinding gebruikt. De standaardpoorten zijn 5985 (WinRM-poort voor HTTP) en 5986 (WinRM-poort voor HTTPS).

Voordat u een alternatieve poort gebruikt, configureert u de WinRM-listener op de externe computer om naar die poort te luisteren. Als u de listener wilt configureren, typt u de volgende twee opdrachten bij de PowerShell-prompt:

`Remove-Item -Path WSMan:\Localhost\listener\listener* -Recurse`

`New-Item -Path WSMan:\Localhost\listener -Transport http -Address * -Port \<port-number\>`

Gebruik de parameter **Port niet,** tenzij dat nodig is. De poort die is ingesteld in de opdracht is van toepassing op alle computers of sessies waarop de opdracht wordt uitgevoerd. Een alternatieve poortinstelling kan verhinderen dat de opdracht wordt uitgevoerd op alle computers.

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

Wordt gebruikt om de aangeroepen opdracht uit te voeren in de foutopsporingsmodus in de externe PowerShell-sessie.

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

### -ScriptBlock

Hiermee geeft u de opdrachten uit te voeren. Sluit de opdrachten tussen accolades om `{ }` een scriptblok te maken.
Deze parameter is vereist.

Standaard worden variabelen in de opdracht geëvalueerd op de externe computer. Gebruik **ArgumentList** om lokale variabelen op te nemen in de opdracht .

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

Hiermee geeft u een matrix van sessies waarin deze cmdlet de opdracht wordt uitgevoerd. Voer een variabele in die **PSSession-objecten** bevat of een opdracht die de **PSSession-objecten** maakt of op haalt, zoals een `New-PSSession` - of `Get-PSSession` -opdracht.

Wanneer u een **PSSession maakt,** maakt PowerShell een permanente verbinding met de externe computer. Gebruik een **PSSession om** een reeks gerelateerde opdrachten uit te voeren die gegevens delen. Als u één opdracht of een reeks niet-gerelateerde opdrachten wilt uitvoeren, gebruikt u de parameter **ComputerName.** Zie voor meer informatie [about_PSSessions](./About/about_PSSessions.md).

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

### -SessionName

Hiermee geeft u een gebruiksvriendelijke naam op voor een niet-verbonden sessie. U kunt de naam gebruiken om te verwijzen naar de sessie in volgende opdrachten, zoals een `Get-PSSession` opdracht. Deze parameter is alleen geldig met **de parameter InDisconnectedSession.**

Deze parameter is geïntroduceerd in PowerShell 3.0.

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

Hiermee geeft u geavanceerde opties voor de sessie. Voer een **SessionOption-object** in, zoals een object dat u maakt met behulp van de cmdlet of een hash-tabel waarin de sleutels sessieoptienamen zijn en de waarden `New-PSSessionOption` sessieoptiewaarden zijn.

De standaardwaarden voor de opties worden bepaald door de waarde van de `$PSSessionOption` voorkeursvariabele als deze is ingesteld. Anders worden de standaardwaarden ingesteld door opties die zijn ingesteld in de sessieconfiguratie.

De waarden van de sessieoptie hebben voorrang op standaardwaarden voor sessies die zijn ingesteld in de `$PSSessionOption` voorkeursvariabele en in de sessieconfiguratie. Ze hebben echter geen voorrang op maximumwaarden, quota of limieten die zijn ingesteld in de sessieconfiguratie.

Zie voor een beschrijving van de sessieopties die de standaardwaarden `New-PSSessionOption` bevatten. Zie voor meer informatie `$PSSessionOption` over de voorkeursvariabele [about_Preference_Variables.](About/about_Preference_Variables.md)
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

Deze parameter maakt gebruik van een matrix met hashtabellen waarbij elke hash-tabel een of meer verbindingsparameters bevat die nodig zijn om een SSH-verbinding (Secure Shell) tot stand te brengen. De **parameter SSHConnection** is handig voor het maken van meerdere sessies waarbij elke sessie andere verbindingsgegevens vereist.

De hashtabel heeft de volgende leden:

- **ComputerName** (of **HostName**)
- **Poort**
- **Gebruikersnaam**
- **KeyFilePath** (of **IdentityFilePath**)

**ComputerName** (of **HostName)** is het enige sleutel-waardepaar dat vereist is.

Deze parameter is geïntroduceerd in PowerShell 6.0.

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

PowerShell maakt standaard gebruik van Windows WinRM om verbinding te maken met een externe computer. Deze schakelknop dwingt PowerShell om de **parameter HostName** te gebruiken voor het tot stand brengen van een externe SSH-verbinding.

Deze parameter is geïntroduceerd in PowerShell 6.0.

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

Hiermee geeft u het maximum aantal gelijktijdige verbindingen die kunnen worden ingesteld voor het uitvoeren van deze opdracht.
Als u deze parameter weglaten of een waarde van 0, de standaardwaarde, 32, wordt gebruikt.

De beperkingslimiet geldt alleen voor de huidige opdracht, niet voor de sessie of voor de computer.

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

Hiermee geeft u de gebruikersnaam voor het account dat wordt gebruikt voor het uitvoeren van een opdracht op de externe computer. De gebruikersverificatiemethode is afhankelijk van hoe Secure Shell (SSH) is geconfigureerd op de externe computer.

Als SSH is geconfigureerd voor basiswachtwoordverificatie, wordt u gevraagd om het gebruikerswachtwoord.

Als SSH is geconfigureerd voor op sleutels gebaseerde gebruikersverificatie, kan een sleutelbestandspad worden opgegeven via de parameter **KeyFilePath** en wordt er geen wachtwoordprompt gegeven. Als het clientgebruikerssleutelbestand zich op een bekende SSH-locatie bevindt, is de parameter **KeyFilePath** niet nodig voor verificatie op basis van een sleutel en vindt gebruikersverificatie automatisch plaats op basis van de gebruikersnaam. Zie de SSH-documentatie van uw platform over op sleutels gebaseerde gebruikersverificatie voor meer informatie.

Dit is geen vereiste parameter. Als de **gebruikersnaam** parameter niet is opgegeven, wordt de huidige aangemelde gebruikersnaam gebruikt voor de verbinding.

Deze parameter is geïntroduceerd in PowerShell 6.0.

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

Geeft aan dat deze cmdlet het SSL-protocol (Secure Sockets Layer) gebruikt om een verbinding met de externe computer tot stand te brengen. Standaard wordt SSL niet gebruikt.

WS-Management versleutelt alle PowerShell-inhoud die via het netwerk wordt verzonden. De **parameter UseSSL** is een extra beveiliging die de gegevens via een HTTPS verzendt in plaats van HTTP.

Als u deze parameter gebruikt, maar SSL niet beschikbaar is op de poort die wordt gebruikt voor de opdracht, mislukt de opdracht.

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

Hiermee geeft u een matrix van de ID's van virtuele machines.

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

Hiermee geeft u een matrix met namen van virtuele machines.

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

Hiermee geeft u het subsysteem op dat moet worden gebruikt op het doel, zoals gedefinieerd in sshd_config.
Het subsysteem start een specifieke versie van PowerShell met vooraf gedefinieerde parameters.
Als het opgegeven subsysteem niet bestaat op de externe computer, mislukt de opdracht.

Als deze parameter niet wordt gebruikt, is de standaardwaarde het subsysteem 'powershell'.

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

Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable. Zie voor meer informatie [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).

## Invoerwaarden

### System.Management.Automation.ScriptBlock

U kunt een opdracht in een scriptblok doorseen naar `Invoke-Command` . Gebruik de `$Input` automatische variabele om de invoerobjecten in de opdracht weer te geven.

## Uitvoerwaarden

### System.Management.Automation.PSRemotingJob, System.Management.Automation.Runspaces.PSSession of de uitvoer van de aangeroepen opdracht

Deze cmdlet retourneert een taakobject als u de **parameter AsJob** gebruikt. Als u de **parameter InDisconnectedSession opgeeft,** `Invoke-Command` retourneert een **PSSession-object.** Anders wordt de uitvoer van de aangeroepen opdracht, de waarde van de **parameter ScriptBlock,** retourneert.

## Notities

Op Windows Vista, en latere versies van het Windows-besturingssysteem, moet u PowerShell uitvoeren met de optie Als administrator uitvoeren om de parameter **ComputerName** van te gebruiken om een opdracht uit te voeren op de lokale `Invoke-Command` computer. 

Wanneer u opdrachten op meerdere computers uitvoeren, maakt PowerShell verbinding met de computers in de volgorde waarin ze worden weergegeven in de lijst. De uitvoer van de opdracht wordt echter weergegeven in de volgorde waarin deze wordt ontvangen van de externe computers, wat mogelijk anders is.

Fouten die het resultaat zijn van de opdracht `Invoke-Command` die wordt uitgevoerd, zijn opgenomen in de opdrachtresultaten.
Fouten die fouten in een lokale opdracht zouden beëindigen, worden in een externe opdracht behandeld als niet-beëindigingsfouten. Deze strategie zorgt ervoor dat het beëindigen van fouten op één computer de opdracht niet sluit op alle computers waarop deze wordt uitgevoerd. Deze oefening wordt zelfs gebruikt wanneer een externe opdracht wordt uitgevoerd op één computer.

Als de externe computer zich niet in een domein dat de lokale computer vertrouwt, kan de computer mogelijk niet de referenties van de gebruiker verifiëren. Als u de externe computer wilt toevoegen aan de lijst met vertrouwde hosts in WS-Management, gebruikt u de volgende opdracht in de provider, waarbij de naam `WSMAN` van de externe computer `<Remote-Computer-Name>` is:

`Set-Item -Path WSMan:\Localhost\Client\TrustedHosts -Value \<Remote-Computer-Name\>`

Wanneer u de verbinding met **een PSSession** verbreekt met behulp van de parameter **InDisconnectedSession,** wordt de sessietoestand **Verbroken** en is de beschikbaarheid **Geen.** De waarde van de **eigenschap State** is relatief ten opzichte van de huidige sessie. De waarde **Verbroken** betekent dat **de PSSession** niet is verbonden met de huidige sessie. Dit betekent echter niet dat de **PSSession** is losgekoppeld van alle sessies. Deze kan zijn verbonden met een andere sessie. Gebruik de eigenschap Beschikbaarheid om te bepalen of u verbinding kunt maken of opnieuw verbinding kunt maken met **de** sessie.

De **waarde** Beschikbaarheid **van Geen** geeft aan dat u verbinding kunt maken met de sessie. De waarde **Bezet geeft** aan dat u geen verbinding kunt maken met de **PSSession** omdat deze is verbonden met een andere sessie. Zie [RunspaceState](/dotnet/api/system.management.automation.runspaces.runspacestate)voor meer informatie over de waarden van de **eigenschap Status** van sessies. Zie [RunspaceAvailability](/dotnet/api/system.management.automation.runspaces.runspaceavailability)voor meer informatie over de waarden van de **eigenschap Beschikbaarheid** van sessies.

De **parameters HostName** en **SSHConnection** zijn vanaf PowerShell 6.0 opgenomen. Ze zijn toegevoegd om powershell voor remoting te bieden op basis van Secure Shell (SSH). PowerShell en SSH worden ondersteund op meerdere platformen (Windows, Linux, macOS) en voor remoting van PowerShell werkt via deze platformen waarop PowerShell en SSH zijn geïnstalleerd en geconfigureerd. Dit staat los van de vorige windows-remoting die is gebaseerd op WinRM en veel specifieke WinRM-functies en -beperkingen zijn niet van toepassing. Bijvoorbeeld quota op basis van WinRM, sessieopties, aangepaste eindpuntconfiguratie en functies voor verbreken/opnieuw verbinden worden momenteel niet ondersteund. Zie Voor meer informatie over het instellen van SSH-remoting voor [PowerShell Via SSH.](/powershell/scripting/learn/remoting/ssh-remoting-in-powershell-core)

## Verwante koppelingen

[about_PSSessions](./About/about_PSSessions.md)

[about_Remote](./About/about_Remote.md)

[about_Remote_Disconnected_Sessions](./About/about_Remote_Disconnected_Sessions.md)

[about_Remote_Troubleshooting](./About/about_remote_troubleshooting.md)

[about_Remote_Variables](./About/about_Remote_Variables.md)

[about_Scopes](./About/about_scopes.md)

[Enter-PSSession](Enter-PSSession.md)

[Exit-PSSession](Exit-PSSession.md)

[Get-PSSession](Get-PSSession.md)

[Invoke-Item](../Microsoft.PowerShell.Management/Invoke-Item.md)

[New-PSSession](New-PSSession.md)

[Remove-PSSession](Remove-PSSession.md)

[WSMan Provider](../Microsoft.WsMan.Management/About/about_WSMan_Provider.md)
