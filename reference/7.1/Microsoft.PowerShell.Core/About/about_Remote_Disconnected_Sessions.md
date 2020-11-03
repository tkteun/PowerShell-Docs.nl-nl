---
description: Hierin wordt uitgelegd hoe u de verbinding verbreekt en opnieuw maakt met een Power shell-sessie (PSSession).
keywords: powershell,cmdlet
Locale: en-US
ms.date: 12/01/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_remote_disconnected_sessions?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Remote_Disconnected_Sessions
ms.openlocfilehash: 68903485ce92a692453bfba4aa5097dd062437f9
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/13/2020
ms.locfileid: "93252655"
---
# <a name="about-remote-disconnected-sessions"></a>Over externe verbroken sessies

## <a name="short-description"></a>Korte beschrijving

Hierin wordt uitgelegd hoe u de verbinding verbreekt en opnieuw maakt met een Power shell-sessie (PSSession).

## <a name="long-description"></a>Lange beschrijving

Vanaf Power Shell 3,0 kunt u de verbinding met een PSSession verbreken en opnieuw verbinding maken met de PSSession op dezelfde computer of een andere computer. De sessie status wordt gehandhaafd en opdrachten in de PSSession blijven actief wanneer de sessie wordt verbroken.

De functie voor verbroken sessies is alleen beschikbaar als op de externe computer Power Shell 3,0 of een latere versie wordt uitgevoerd.

Met de functie voor verbroken sessies kunt u de sessie sluiten waarin een PSSession is gemaakt, en zelfs Power shell sluiten en de computer afsluiten, zonder dat de opdrachten die in de PSSession worden uitgevoerd, worden onderbroken. Verbroken sessies zijn handig voor het uitvoeren van opdrachten die lange tijd in beslag nemen en biedt de tijd en de flexibiliteit van apparaten die IT-professionals nodig hebben.

U kunt de verbinding met een interactieve sessie die is gestart met behulp van de cmdlet, niet verbreken `Enter-PSSession` .

U kunt niet-verbonden sessies gebruiken om PSSessions te beheren die onbedoeld zijn losgekoppeld als gevolg van een computer of netwerk storing.

In Real-World-gebruik kunt u met de functie voor verbroken sessies beginnen met het oplossen van een probleem, een probleem met een hogere prioriteit maken en vervolgens het werk aan de oplossing hervatten, zelfs op een andere computer op een andere locatie.

## <a name="disconnected-session-cmdlets"></a>Verbroken sessie-cmdlets

De volgende cmdlets bieden ondersteuning voor de functie voor verbroken sessies:

- `Connect-PSSession`: Maakt verbinding met een niet-verbonden PSSession.
- `Disconnect-PSSession`: Verbreekt de verbinding met een PSSession.
- `Get-PSSession`: Hiermee wordt PSSessions opgehaald op de lokale computer of op externe computers.
- `Receive-PSSession`: Hiermee worden de resultaten opgehaald van opdrachten die zijn uitgevoerd in sessies zonder verbinding.
- `Invoke-Command`: Met de para meter **InDisconnectedSession** wordt direct een PSSession gemaakt en wordt de verbinding verbroken.

## <a name="how-the-disconnected-sessions-feature-works"></a>De werking van de functie voor verbroken sessies

Vanaf Power Shell 3,0 zijn PSSessions onafhankelijk van de sessies waarin ze zijn gemaakt. Actieve PSSessions worden onderhouden op de externe computer of aan de **server zijde** van de verbinding, zelfs als de sessie waarin de PSSession is gemaakt gesloten is en de oorspronkelijke computer wordt afgesloten of de verbinding met het netwerk is verbroken.

In Power Shell 2,0 wordt de PSSession verwijderd van de externe computer wanneer deze wordt losgekoppeld van de oorspronkelijke sessie of de sessie waarin deze is gemaakt.

Wanneer u een PSSession verbreekt, blijft de PSSession actief en wordt deze op de externe computer onderhouden. De sessie status wordt gewijzigd van **actief** in **losgekoppeld**. U kunt opnieuw verbinding maken met een niet-verbonden PSSession van de huidige sessie of van een andere sessie op dezelfde computer of vanaf een andere computer. De externe computer die de sessie onderhoudt, moet actief zijn en verbonden zijn met het netwerk.

Opdrachten in een PSSession zonder verbinding blijven worden uitgevoerd op de externe computer totdat de opdracht is voltooid of de uitvoer buffer vol is. Als u wilt voor komen dat een volledige uitvoer buffer een opdracht onderbreekt, gebruikt u de para meter **OutputBufferingMode** van de `Disconnect-PSSession` -, `New-PSSessionOption` -of- `New-PSTransportOption` cmdlets.

Verbroken sessies worden onderhouden met de status niet verbonden op de externe computer. Ze zijn beschikbaar zodat u opnieuw verbinding kunt maken, totdat u de PSSession verwijdert, zoals met de `Remove-PSSession` cmdlet of totdat de time-out voor inactiviteit van de PSSession verloopt. U kunt de time-out voor inactiviteit van een PSSession aanpassen met behulp van de **IdleTimeoutSec** -of **IdleTimeout** -para meters van de `Disconnect-PSSession` -, `New-PSSessionOption` -of- `New-PSTransportOption` cmdlets.

Een andere gebruiker kan verbinding maken met PSSessions die u hebt gemaakt, maar alleen als ze de referenties kunnen opgeven die zijn gebruikt voor het maken van de sessie, of de `RunAs` referenties van de sessie configuratie gebruiken.

## <a name="how-to-get-pssessions"></a>PSSessions ophalen

Vanaf Power Shell 3,0 krijgt de `Get-PSSession` cmdlet PSSessions op de lokale computer en externe computers. Er kunnen ook PSSessions worden opgehaald die in de huidige sessie zijn gemaakt.

Als u PSSessions op de lokale computer of externe computers wilt ophalen, gebruikt u de para meter **ComputerName** of **ConnectionUri** . Zonder para meters worden `Get-PSSession` PSSession opgehaald die zijn gemaakt in de lokale sessie, ongeacht waar ze worden beëindigd.

Vergeet niet om PSSessions te zoeken naar de computer waarop deze worden onderhouden, dat wil zeggen, de externe computer of de **Server** .

Als u bijvoorbeeld een PSSession maakt op de Server01-computer, kunt u de sessie ophalen van de Server01-computer. Als u een PSSession van een andere computer op de lokale computer maakt, haalt u de sessie vanaf de lokale computer op.

In de volgende opdracht volgorde ziet u hoe `Get-PSSession` werkt.

Met de eerste opdracht maakt u een sessie op de Server01-computer. De sessie bevindt zich op de Server01-computer.

```powershell
New-PSSession -ComputerName Server01
```

```Output
Id Name      ComputerName  State    ConfigurationName     Availability
-- ----      ------------  -----    -----------------     ------------
 2 Session2  Server01      Opened   Microsoft.PowerShell     Available
```

Als u de sessie wilt downloaden, gebruikt u de para meter **ComputerName** van `Get-PSSession` met de waarde Server01.

```powershell
Get-PSSession -ComputerName Server01
```

```Output
Id Name      ComputerName  State    ConfigurationName     Availability
-- ----      ------------  -----    -----------------     ------------
 2 Session2  Server01      Opened   Microsoft.PowerShell     Available
```

Als de waarde van de para meter **ComputerName** van `Get-PSSession` is localhost, `Get-PSSession` worden er PSSessions opgehaald die eindigen op en worden onderhouden op de lokale computer. Er wordt geen PSSessions op de Server01-computer opgehaald, zelfs als deze zijn gestart op de lokale computer.

```powershell
Get-PSSession -ComputerName localhost
```

Als u sessies wilt ophalen die in de huidige sessie zijn gemaakt, gebruikt u de `Get-PSSession` cmdlet zonder para meters. In dit voor beeld `Get-PSSession` wordt de PSSession opgehaald die in de huidige sessie is gemaakt en wordt er verbinding gemaakt met de Server01-computer.

```powershell
Get-PSSession
```

```Output
Id Name      ComputerName  State    ConfigurationName     Availability
-- ----      ------------  -----    -----------------     ------------
 2 Session2  Server01      Opened   Microsoft.PowerShell     Available
```

## <a name="how-to-disconnect-sessions"></a>Sessies verbreken

Gebruik de cmdlet om de verbinding met een PSSession te verbreken `Disconnect-PSSession` . Als u de PSSession wilt identificeren, gebruikt u de para meter **Session** of pijplijnt u een PSSession van de `New-PSSession` `Get-PSSession` cmdlets `Disconnect-PSSession` .

Met de volgende opdracht wordt de verbinding tussen de PSSession en de Server01-computer verbroken.
U ziet dat de waarde van de eigenschap **State** is **losgekoppeld** en dat de **Beschik baarheid** **geen** is.

```powershell
Get-PSSession -ComputerName Server01 | Disconnect-PSSession
```

```Output
Id Name      ComputerName  State         ConfigurationName     Availability
-- ----      ------------  -----         -----------------     ------------
 2 Session2  Server01      Disconnected  Microsoft.PowerShell          None
```

Als u een verbroken sessie wilt maken, gebruikt u de para meter **InDisconnectedSession** van de `Invoke-Command` cmdlet. Er wordt een sessie gemaakt, de opdracht wordt gestart en onmiddellijk wordt de verbinding verbroken, voordat de opdracht uitvoer kan retour neren.

Met de volgende opdracht wordt een `Get-WinEvent` opdracht uitgevoerd in een verbroken sessie op de externe computer Server02.

```powershell
Invoke-Command -ComputerName Server02 -InDisconnectedSession -ScriptBlock {
   Get-WinEvent -LogName "*PowerShell*" }
```

```Output
Id Name      ComputerName  State         ConfigurationName     Availability
-- ----      ------------  -----         -----------------     ------------
 4 Session3  Server02      Disconnected  Microsoft.PowerShell          None
```

## <a name="how-to-connect-to-disconnected-sessions"></a>Verbinding maken met sessies zonder verbinding

U kunt verbinding maken met elke beschik bare losgekoppelde PSSession van de sessie waarin u de PSSession hebt gemaakt of van andere sessies op de lokale computer of andere computers.

U kunt een PSSession maken, opdrachten uitvoeren in de PSSession, de verbinding verbreken met de PSSession, de Power shell sluiten en de computer afsluiten. Uur later kunt u een andere computer openen, de PSSession ophalen, er verbinding mee maken en de resultaten ophalen van opdrachten die in de PSSession werden uitgevoerd terwijl de verbinding werd verbroken. Vervolgens kunt u meer opdrachten in de sessie uitvoeren.

Gebruik de cmdlet om verbinding te maken met een PSSession waarvan de verbinding is verbroken `Connect-PSSession` . Gebruik de para meters **ComputerName** of **ConnectionUri** om de PSSession te identificeren of om een PSSession van `Get-PSSession` aan te geven `Connect-PSSession` .

Met de volgende opdracht worden de sessies op de Server02-computer opgehaald. De uitvoer bevat twee niet-verbonden sessies, beide beschikbaar.

```powershell
Get-PSSession -ComputerName Server02
```

```Output
Id Name      ComputerName   State         ConfigurationName     Availability
-- ----      ------------   -----         -----------------     ------------
 2 Session2  juneb-srv8320  Disconnected  Microsoft.PowerShell          None
 4 Session3  juneb-srv8320  Disconnected  Microsoft.PowerShell          None
```

Met de volgende opdracht maakt u verbinding met Session2. De PSSession is nu geopend en beschikbaar.

```powershell
Connect-PSSession -ComputerName Server02 -Name Session2
```

```Output
Id Name      ComputerName    State    ConfigurationName     Availability
-- ----      ------------    -----    -----------------     ------------
 2 Session2  juneb-srv8320   Opened   Microsoft.PowerShell     Available
```

## <a name="how-to-get-the-results"></a>De resultaten ophalen

Gebruik de cmdlet om de resultaten op te halen van opdrachten die zijn uitgevoerd in een PSSession zonder verbinding `Receive-PSSession` .

U kunt gebruiken `Receive-PSSession` in plaats van de `Connect-PSSession` cmdlet te gebruiken. Als de sessie al opnieuw is verbonden, worden `Receive-PSSession` de resultaten opgehaald van opdrachten die zijn uitgevoerd toen de verbinding van de sessie werd verbroken. Als de PSSession nog steeds is verbroken, wordt `Receive-PSSession` er verbinding mee gemaakt en worden de resultaten weer gegeven van opdrachten die zijn uitgevoerd toen de verbinding werd verbroken.

`Receive-PSSession` kan de resultaten in een taak (asynchroon) of aan het host-programma (synchroon) retour neren. Gebruik de para meter **outtarget** om **taak** of **host** te selecteren. De standaard waarde is **host**. Als de opdracht die wordt ontvangen, echter is gestart in de huidige sessie als een **taak** , wordt deze standaard als een **taak** geretourneerd.

Met de volgende opdracht wordt de `Receive-PSSession` cmdlet gebruikt om verbinding te maken met de PSSession op de Server02-computer en worden de resultaten opgehaald van de `Get-WinEvent` opdracht die in de Session3-sessie is uitgevoerd. De opdracht maakt gebruik van de **Outtarget** -para meter om de resultaten in een **taak** op te halen.

```powershell
Receive-PSSession -ComputerName Server02 -Name Session3 -OutTarget Job
```

```Output
Id   Name   PSJobTypeName   State         HasMoreData     Location
--   ----   -------------   -----         -----------     --------
 3   Job3   RemoteJob       Running       True            Server02
```

Gebruik de cmdlet om de resultaten van de taak te verkrijgen `Receive-Job` .

```powershell
Get-Job | Receive-Job -Keep
```

```Output
ProviderName: PowerShell

TimeCreated             Id LevelDisplayName Message     PSComputerName
-----------             -- ---------------- -------     --------------
5/14/2012 7:26:04 PM   400 Information      Engine stat Server02
5/14/2012 7:26:03 PM   600 Information      Provider "W Server02
5/14/2012 7:26:03 PM   600 Information      Provider "C Server02
5/14/2012 7:26:03 PM   600 Information      Provider "V Server02
```

## <a name="state-and-availability-properties"></a>Eigenschappen van status en beschik baarheid

Met de eigenschappen **status** en **Beschik baarheid** van een niet-verbonden PSSession weet u of de sessie voor u beschikbaar is om opnieuw verbinding te maken.

Wanneer een PSSession is verbonden met de huidige sessie, wordt de status ervan **geopend** en is de beschik baarheid **beschikbaar**. Wanneer u de verbinding met de PSSession verbreekt, wordt de status van de PSSession- **verbinding verbroken** en is de beschik baarheid **geen**.

De waarde van de eigenschap **State** is relatief ten opzichte van de huidige sessie. Als de waarde voor de **verbinding is verbroken** , betekent dit dat de PSSession niet is verbonden met de huidige sessie. Maar dit betekent niet dat de PSSession-verbinding met alle sessies is verbroken. Deze is mogelijk verbonden met een andere sessie.

Gebruik de eigenschap **Beschik baarheid** om te bepalen of u verbinding kunt maken of opnieuw verbinding wilt maken met de PSSession. De waarde **geen** geeft aan dat u verbinding kunt maken met de sessie. De waarde **bezet** geeft aan dat u geen verbinding kunt maken met de PSSession, omdat deze is verbonden met een andere sessie.

Het volgende voor beeld wordt uitgevoerd in twee Power shell-sessies op dezelfde computer.
Let op de wijzigings waarden van de **status** -en **beschikbaarheids** eigenschappen in elke sessie, omdat de PSSession is losgekoppeld en opnieuw verbinding maakt.

```powershell
# Session 1
New-PSSession -ComputerName Server30 -Name Test
```

```Output
Id Name   ComputerName    State         ConfigurationName     Availability
-- ----   ------------    -----         -----------------     ------------
1  Test   Server30        Opened        Microsoft.PowerShell     Available
```

```powershell
# Session 2
Get-PSSession -ComputerName Server30 -Name Test
```

```Output
Id Name   ComputerName    State         ConfigurationName     Availability
-- ----   ------------    -----         -----------------     ------------
1 Test    Server30        Disconnected  Microsoft.PowerShell          Busy
```

```powershell
# Session 1
Get-PSSession -ComputerName Server30 -Name Test | Disconnect-PSSession
```

```Output
Id Name   ComputerName    State         ConfigurationName     Availability
-- ----   ------------    -----         -----------------     ------------
1 Test    Server30        Disconnected  Microsoft.PowerShell          None
```

```powershell
# Session 2
Get-PSSession -ComputerName Server30
```

```Output
Id Name   ComputerName    State         ConfigurationName     Availability
-- ----   ------------    -----         -----------------     ------------
1 Test    Server30        Disconnected  Microsoft.PowerShell          None
```

```powershell
# Session 2
Connect-PSSession -ComputerName Server30 -Name Test
```

```Output
Id Name   ComputerName    State         ConfigurationName     Availability
-- ----   ------------    -----         -----------------     ------------
3 Test    Server30        Opened        Microsoft.PowerShell     Available
```

```powershell
# Session 1
Get-PSSession -ComputerName Server30
```

```Output
Id Name   ComputerName    State         ConfigurationName     Availability
-- ----   ------------    -----         -----------------     ------------
1 Test    Server30        Disconnected  Microsoft.PowerShell          Busy
```

```Output
# Idle Timeout
```

Verbroken sessies worden op de externe computer gehandhaafd totdat u ze verwijdert, bijvoorbeeld door de cmdlet te gebruiken `Remove-PSSession` of als er een time-out optreedt. De eigenschap **IdleTimeout** van een PSSession bepaalt hoe lang een verbroken sessie wordt behouden voordat deze wordt verwijderd.

PSSessions zijn niet actief wanneer de **heartbeat-thread** geen antwoord ontvangt.
Als u een sessie verbreekt, wordt deze niet-actief en wordt de **IdleTimeout** -klok gestart, zelfs als opdrachten nog steeds worden uitgevoerd in de verbroken sessie. Power shell beschouwt beëindigde sessies als actief, maar niet-actief.

Wanneer u sessies maakt en verbreekt, controleert u of de time-out voor inactiviteit in de PSSession lang genoeg is om de sessie voor uw behoeften te onderhouden, maar niet zo lang dat er overbodige resources op de externe computer worden verbruikt.

De eigenschap **IdleTimeoutMs** van de sessie configuratie bepaalt de standaard time-out voor inactiviteit van sessies die gebruikmaken van de sessie configuratie. U kunt de standaard waarde overschrijven, maar de waarde die u gebruikt, kan niet groter zijn dan de eigenschap **MaxIdleTimeoutMs** van de sessie configuratie.

Als u de waarde van de waarden **IdleTimeoutMs** en **MaxIdleTimeoutMs** van een sessie configuratie wilt zoeken, gebruikt u de volgende opdracht indeling.

```powershell
Get-PSSessionConfiguration |
  Format-Table Name, IdleTimeoutMs, MaxIdleTimeoutMs
```

U kunt de standaard waarde in de sessie configuratie overschrijven en de time-out voor inactiviteit van een PSSession instellen wanneer u een PSSession maakt en wanneer u de verbinding verbreekt.

Als u lid bent van de groep Administrators op de externe computer, kunt u de eigenschappen **IdleTimeoutMs** en **MaxIdleTimeoutMs** van sessie configuraties maken en wijzigen.

## <a name="idle-timeout-values"></a>Time-outwaarden

De waarde voor time-out voor inactiviteit van sessie configuraties en sessie opties is in milliseconden. De waarde voor time-out voor inactiviteit van sessies en sessie configuratie opties is in enkele seconden.

U kunt de time-out voor inactiviteit van een PSSession instellen wanneer u de PSSession ( `New-PSSession` , `Invoke-Command` ) maakt en wanneer u de verbinding met deze server verbreekt ( `Disconnect-PSSession` ). U kunt de waarde voor **IdleTimeout** echter niet wijzigen wanneer u verbinding maakt met de PSSession ( `Connect-PSSession` ) of resultaten ophalen ( `Receive-PSSession` ).

De `Connect-PSSession` `Receive-PSSession` cmdlets en hebben een **SessionOption** -para meter die een **SessionOption** -object gebruikt, zoals het resultaat dat door de cmdlet wordt geretourneerd `New-PSSessionOption` . De waarde voor **IdleTimeout** in **SessionOption** -object en de waarde voor **IdleTimeout** in de `$PSSessionOption` Voorkeurs variabele wijzigen niet de **IdleTimeout** waarde van de PSSession in een `Connect-PSSession` of- `Receive-PSSession` opdracht.

Als u een PSSession met een bepaalde time-outwaarde wilt maken, maakt u een `$PSSessionOption` Voorkeurs variabele. Stel de waarde van de eigenschap **IdleTimeout** in op de gewenste waarde (in milliseconden).

Wanneer u PSSessions maakt, hebben de waarden in `$PSSessionOption` de variabele voor rang op de waarden in de sessie configuratie.

Met de volgende opdracht wordt bijvoorbeeld een time-out voor inactiviteit van 48 uur ingesteld:

```powershell
$PSSessionOption = New-PSSessionOption -IdleTimeoutMSec 172800000
```

Als u een PSSession met een bepaalde time-outwaarde wilt maken, gebruikt u de para meter **IdleTimeoutMSec** van de `New-PSSessionOption` cmdlet. Gebruik vervolgens de optie sessie in de waarde van de para meter **SessionOption** van de- `New-PSSession` of- `Invoke-Command` cmdlets.

De waarden die zijn ingesteld bij het maken van de sessie, hebben voor rang op de waarden die zijn ingesteld in de `$PSSessionOption` Voorkeurs variabele en de sessie configuratie.

Bijvoorbeeld:

```powershell
$o = New-PSSessionOption -IdleTimeoutMSec 172800000
New-PSSession -SessionOption $o
```

Als u de time-out voor inactiviteit van een PSSession wilt wijzigen tijdens het verbreken van de verbinding, gebruikt u de para meter **IdleTimeoutSec** van de `Disconnect-PSSession` cmdlet.

Bijvoorbeeld:

```powershell
Disconnect-PSSession -IdleTimeoutSec 172800
```

Gebruik de para meters **IdleTimeoutSec** en **MaxIdleTimeoutSec** van de cmdlet om een sessie configuratie te maken met een bepaalde time-out voor inactiviteit en een maximale inactieve time-out `New-PSTransportOption` . Gebruik vervolgens de transport optie in de waarde van de para meter **TransportOption** van `Register-PSSessionConfiguration` .

Bijvoorbeeld:

```powershell
$o = New-PSTransportOption -IdleTimeoutSec 172800 -MaxIdleTimeoutSec 259200
Register-PSSessionConfiguration -Name Test -TransportOption $o
```

Als u de standaard time-out voor inactiviteit en de maximale time-out voor inactiviteit van een sessie configuratie wilt wijzigen, gebruikt u de para meters **IdleTimeoutSec** en **MaxIdleTimeoutSec** van de `New-PSTransportOption` cmdlet. Gebruik vervolgens de transport optie in de waarde van de para meter **TransportOption** van `Set-PSSessionConfiguration` .

Bijvoorbeeld:

```powershell
$o = New-PSTransportOption -IdleTimeoutSec 172800 -MaxIdleTimeoutSec 259200
Set-PSSessionConfiguration -Name Test -TransportOption $o
```

## <a name="output-buffering-mode"></a>Modus voor uitvoer buffer

De uitvoer buffer modus van een PSSession bepaalt hoe de uitvoer van de opdracht wordt beheerd wanneer de uitvoer buffer van de PSSession vol is.

In een verbroken sessie bepaalt de uitvoer buffer modus effectief of de opdracht wordt uitgevoerd terwijl de sessie wordt verbroken.

De geldige waarden zijn als volgt:

- **Blok keren**. Wanneer de uitvoer buffer vol is, wordt de uitvoering onderbroken totdat de buffer leeg is. De standaard waarde.
- **Neerzetten**. Wanneer de uitvoer buffer vol is, wordt de uitvoering voortgezet. Wanneer er een nieuwe uitvoer wordt gegenereerd, wordt de oudste uitvoer verwijderd.

Met **blok keren** worden gegevens bewaard, maar kan de opdracht worden onderbroken. Met de waarde **Drop** kan de opdracht worden voltooid, hoewel gegevens verloren kunnen gaan. Wanneer u de waarde voor **neerzetten** gebruikt, moet u de uitvoer van de opdracht omleiden naar een bestand op schijf. Deze waarde wordt aanbevolen voor verbroken sessies.

De eigenschap **OutputBufferingMode** van de sessie configuratie bepaalt de standaard modus voor uitvoer buffering van sessies die gebruikmaken van de sessie configuratie.

U kunt een van de volgende opdracht indelingen gebruiken om de waarde van de **OutputBufferingMode** van de sessie configuratie te vinden:

```powershell
(Get-PSSessionConfiguration <ConfigurationName>).OutputBufferingMode
```

```powershell
Get-PSSessionConfiguration | Format-Table Name, OutputBufferingMode
```

U kunt de standaard waarde in de sessie configuratie overschrijven en de uitvoer buffer modus van een PSSession instellen wanneer u een PSSession maakt, wanneer u de verbinding verbreekt en wanneer u opnieuw verbinding maakt.

Als u lid bent van de groep Administrators op de externe computer, kunt u de uitvoer buffer modus van sessie configuraties maken en wijzigen.

Als u een PSSession wilt maken met een uitvoer buffer methode **Drop** , maakt u een `$PSSessionOption` Voorkeurs variabele waarin de waarde van de eigenschap **OutputBufferingMode** wordt **Drop** verwijderd.

Wanneer u PSSessions maakt, hebben de waarden in `$PSSessionOption` de variabele voor rang op de waarden in de sessie configuratie.

Bijvoorbeeld:

```powershell
$PSSessionOption = New-PSSessionOption -OutputBufferingMode Drop
```

Als u een PSSession wilt maken met een uitvoer buffer methode **Drop** , gebruikt u de para meter **OutputBufferingMode** van de `New-PSSessionOption` cmdlet om een sessie optie met de waarde **Drop** te maken. Gebruik vervolgens de optie sessie in de waarde van de para meter **SessionOption** van de- `New-PSSession` of- `Invoke-Command` cmdlets.

De waarden die zijn ingesteld bij het maken van de sessie, hebben voor rang op de waarden die zijn ingesteld in de `$PSSessionOption` Voorkeurs variabele en de sessie configuratie.

Bijvoorbeeld:

```powershell
$o = New-PSSessionOption -OutputBufferingMode Drop
New-PSSession -SessionOption $o
```

Als u de modus voor uitvoer buffering van een PSSession wilt wijzigen wanneer de verbinding wordt verbroken, gebruikt u de para meter **OutputBufferingMode** van de `Disconnect-PSSession` cmdlet.

Bijvoorbeeld:

```powershell
Disconnect-PSSession -OutputBufferingMode Drop
```

Als u de modus voor uitvoer buffering van een PSSession wilt wijzigen wanneer u opnieuw verbinding maakt, gebruikt u de para meter **OutputBufferingMode** van de `New-PSSessionOption` cmdlet om een sessie optie met de waarde **Drop** te maken. Gebruik vervolgens de optie sessie in de waarde van de para meter **SessionOption** van `Connect-PSSession` of `Receive-PSSession` .

Bijvoorbeeld:

```powershell
$o = New-PSSessionOption -OutputBufferingMode Drop
Connect-PSSession -ComputerName Server01 -Name Test -SessionOption $o
```

Als u een sessie configuratie met een standaard uitvoer buffer modus wilt maken **, gebruikt** u de para meter **OutputBufferingMode** van de `New-PSTransportOption` cmdlet om een transport optie object te maken met de waarde **Drop**. Gebruik vervolgens de transport optie in de waarde van de para meter **TransportOption** van `Register-PSSessionConfiguration` .

Bijvoorbeeld:

```powershell
$o = New-PSTransportOption -OutputBufferingMode Drop
Register-PSSessionConfiguration -Name Test -TransportOption $o
```

Als u de standaard modus voor uitvoer buffering van een sessie configuratie wilt wijzigen, gebruikt u de para meter **OutputBufferingMode** van de `New-PSTransportOption` cmdlet om een transport optie te maken met de waarde **Drop**. Gebruik vervolgens de transport optie in de waarde van de para meter **SessionOption** van `Set-PSSessionConfiguration` .

Bijvoorbeeld:

```powershell
$o = New-PSTransportOption -OutputBufferingMode Drop
Set-PSSessionConfiguration -Name Test -TransportOption $o
```

## <a name="disconnecting-loopback-sessions"></a>Loop Back-sessies verbreken

Loop Back-sessies of lokale sessies zijn PSSessions die afkomstig zijn van en eindigen op dezelfde computer. Net als bij andere PSSessions worden actieve loop Back-sessies op de computer op het externe einde van de verbinding (de lokale computer) bewaard, zodat u de verbinding met loop Back-sessies kunt verbreken en opnieuw verbinding moet maken.

Loop Back-sessies worden standaard gemaakt met een netwerk beveiligings token dat geen opdrachten toestaat die in de sessie worden uitgevoerd om toegang te krijgen tot andere computers. U kunt opnieuw verbinding maken met loop Back-sessies met een netwerk beveiligings token van een wille keurige sessie op de lokale computer of een externe computer.

Als u echter de para meter **EnableNetworkAccess** van de `New-PSSession` cmdlet, `Enter-PSSession` of gebruikt `Invoke-Command` , wordt de loop back-sessie gemaakt met een interactief beveiligings token. Met het interactieve token kunnen opdrachten die worden uitgevoerd in de loop back-sessie gegevens van andere computers ophalen.

U kunt de loop Back-sessies met interactieve tokens verbreken en vervolgens opnieuw verbinding maken met de-sessie of een andere sessie op dezelfde computer.
Om bijvoorbeeld kwaad aardige toegang te voor komen, kunt u opnieuw verbinding maken met loop Back-sessies met interactieve tokens van de computer waarop deze zijn gemaakt.

## <a name="waiting-for-jobs-in-disconnected-sessions"></a>Wachten op taken in sessies zonder verbinding

De `Wait-Job` cmdlet wacht tot een taak is voltooid en keert vervolgens terug naar de opdracht prompt of de volgende opdracht. `Wait-Job`Retourneert standaard als de sessie waarin een taak wordt uitgevoerd, niet is verbonden. Als u de `Wait-Job` cmdlet wilt wachten totdat de sessie opnieuw is verbonden, gebruikt u de para meter **Forces** in de status **geopend** . Zie [wait-job](xref:Microsoft.PowerShell.Core.Wait-Job)voor meer informatie.

## <a name="robust-sessions-and-unintentional-disconnection"></a>Robuuste sessies en onbedoelde verbreken van de verbinding

Een PSSession kan per ongeluk worden verbroken vanwege een storing in de computer of netwerk storingen. Power shell probeert de PSSession te herstellen, maar het succes ervan is afhankelijk van de ernst en de duur van de oorzaak.

De status van een onbedoelde ontkoppelde PSSession kan worden **verbroken** of **gesloten** , maar kan ook worden **losgekoppeld**. Als de waarde van **status** is **verbroken** , kunt u dezelfde technieken gebruiken om de PSSession te beheren zoals u zou doen als de verbinding met de sessie opzettelijk is verbroken. U kunt bijvoorbeeld de-cmdlet gebruiken `Connect-PSSession` om opnieuw verbinding te maken met de sessie en de `Receive-PSSession` cmdlet om de resultaten op te halen van opdrachten die zijn uitgevoerd terwijl de verbinding met de sessie werd verbroken.

Als u sluit (afsluit) de sessie waarin een PSSession is gemaakt terwijl opdrachten worden uitgevoerd in de PSSession, onderhoudt Power shell de PSSession in de niet- **verbonden** status op de externe computer. Als u de sessie sluit waarin een PSSession is gemaakt, maar er geen opdrachten worden uitgevoerd in de PSSession, probeert Power shell de PSSession niet te onderhouden.

## <a name="see-also"></a>Zie ook

[about_Jobs](about_Jobs.md)

[about_Remote](about_Remote.md)

[about_Remote_Variables](about_Remote_Variables.md)

[about_PSSessions](about_PSSessions.md)

[about_Session_Configurations](about_Session_Configurations.md)

[Connect-PSSession](xref:Microsoft.PowerShell.Core.Connect-PSSession)

[Verbinding verbreken-PSSession](xref:Microsoft.PowerShell.Core.Disconnect-PSSession)

[Get-PSSession](xref:Microsoft.PowerShell.Core.Get-PSSession)

[Receive-PSSession](xref:Microsoft.PowerShell.Core.Receive-PSSession)

[Invoke-opdracht](xref:Microsoft.PowerShell.Core.Invoke-Command)

