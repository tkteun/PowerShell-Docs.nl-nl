---
ms.date: 06/05/2017
keywords: powershell,cmdlet
title: Services beheren
description: Power shell biedt verschillende cmdlets waarmee u services op lokale en externe computers kunt beheren.
ms.openlocfilehash: 003803cdaa37e51b3788f3f897cbec7d6e243ca8
ms.sourcegitcommit: 9080316e3ca4f11d83067b41351531672b667b7a
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/24/2020
ms.locfileid: "92500348"
---
# <a name="managing-services"></a>Services beheren

Er zijn acht core service-cmdlets, ontworpen voor een breed scala aan service taken. We kijken alleen naar het aanbieden en wijzigen van de actieve status voor services, maar u kunt een lijst met Service-cmdlets krijgen met behulp van `Get-Help \*-Service` , en u kunt informatie over elke service-cmdlet vinden met `Get-Help <Cmdlet-Name>` , zoals `Get-Help New-Service` .

## <a name="getting-services"></a>Services ophalen

U kunt de services op een lokale of externe computer ophalen met behulp van de- `Get-Service` cmdlet. Net als bij `Get-Process` , met behulp van de `Get-Service` opdracht zonder para meters, worden alle services geretourneerd. U kunt filteren op naam, zelfs met een sterretje als Joker teken:

```powershell
PS> Get-Service -Name se*

Status   Name               DisplayName
------   ----               -----------
Running  seclogon           Secondary Logon
Running  SENS               System Event Notification
Stopped  ServiceLayer       ServiceLayer
```

Omdat het niet altijd duidelijk is wat de werkelijke naam voor de service is, kunt u de services op weergave naam zoeken. U kunt dit doen op basis van een specifieke naam, met behulp van joker tekens of met een lijst met weergave namen:

```powershell
PS> Get-Service -DisplayName se*

Status   Name               DisplayName
------   ----               -----------
Running  lanmanserver       Server
Running  SamSs              Security Accounts Manager
Running  seclogon           Secondary Logon
Stopped  ServiceLayer       ServiceLayer
Running  wscsvc             Security Center

PS> Get-Service -DisplayName ServiceLayer,Server

Status   Name               DisplayName
------   ----               -----------
Running  lanmanserver       Server
Stopped  ServiceLayer       ServiceLayer
```

U kunt de para meter ComputerName van de cmdlet Get-Service gebruiken om de services op externe computers op te halen. De para meter ComputerName accepteert meerdere waarden en Joker tekens, zodat u de services op meerdere computers met één opdracht kunt ophalen. Met de volgende opdracht worden bijvoorbeeld de services op de externe computer Server01 opgehaald.

```powershell
Get-Service -ComputerName Server01
```

## <a name="getting-required-and-dependent-services"></a>Vereiste en afhankelijke services ophalen

De cmdlet Get-Service heeft twee para meters die erg nuttig zijn in Service beheer. De para meter DependentServices haalt Services op die afhankelijk zijn van de service. De para meter RequiredServices haalt Services op waarvan deze service afhankelijk is.

Met deze para meters worden alleen de waarden weer gegeven van de eigenschappen DependentServices en ServicesDependedOn (alias = RequiredServices) van het object System. ServiceProcess. ServiceController dat Get-Service retourneert, maar de opdrachten worden vereenvoudigd en deze gegevens worden veel eenvoudiger gemaakt.

Met de volgende opdracht worden de services opgehaald die de LanmanWorkstation-service nodig heeft.

```powershell
PS> Get-Service -Name LanmanWorkstation -RequiredServices

Status   Name               DisplayName
------   ----               -----------
Running  MRxSmb20           SMB 2.0 MiniRedirector
Running  bowser             Bowser
Running  MRxSmb10           SMB 1.x MiniRedirector
Running  NSI                Network Store Interface Service
```

Met de volgende opdracht worden de services opgehaald waarvoor de LanmanWorkstation-service is vereist.

```powershell
PS> Get-Service -Name LanmanWorkstation -DependentServices

Status   Name               DisplayName
------   ----               -----------
Running  SessionEnv         Terminal Services Configuration
Running  Netlogon           Netlogon
Stopped  Browser            Computer Browser
Running  BITS               Background Intelligent Transfer Ser...
```

U kunt zelfs alle services ophalen die afhankelijkheden hebben. De volgende opdracht is alleen dat en vervolgens wordt de cmdlet Format-Table gebruikt om de eigenschappen status, naam, RequiredServices en DependentServices van de services op de computer weer te geven.

```powershell
Get-Service -Name * | Where-Object {$_.RequiredServices -or $_.DependentServices} |
  Format-Table -Property Status, Name, RequiredServices, DependentServices -auto
```

## <a name="stopping-starting-suspending-and-restarting-services"></a>Services stoppen, starten, onderbreken en opnieuw starten

De service-cmdlets hebben allemaal hetzelfde algemene formulier. Services kunnen worden opgegeven met een algemene naam of weergave naam en lijsten en Joker tekens worden als waarden. Als u de afdrukspooler wilt stoppen, gebruikt u:

```powershell
Stop-Service -Name spooler
```

Als u de afdrukspooler wilt starten nadat deze is gestopt, gebruikt u:

```powershell
Start-Service -Name spooler
```

Als u de afdrukspooler wilt onderbreken, gebruikt u:

```powershell
Suspend-Service -Name spooler
```

De `Restart-Service` cmdlet werkt op dezelfde manier als de andere service-cmdlets, maar er worden een aantal complexere voor beelden weer gegeven. In het eenvoudigste gebruik geeft u de naam van de service op:

```powershell
PS> Restart-Service -Name spooler

WARNING: Waiting for service 'Print Spooler (Spooler)' to finish starting...
WARNING: Waiting for service 'Print Spooler (Spooler)' to finish starting...
PS>
```

U ziet dat er een herhaalde waarschuwing wordt weer gegeven over het starten van de afdrukspooler. Wanneer u een service bewerking uitvoert die enige tijd in beslag neemt, wordt u door Windows Power shell op de hoogte gesteld dat er nog steeds wordt geprobeerd om de taak uit te voeren.

Als u meerdere services opnieuw wilt starten, kunt u een lijst met services ophalen, deze filteren en vervolgens het opnieuw opstarten uitvoeren:

```powershell
PS> Get-Service | Where-Object -FilterScript {$_.CanStop} | Restart-Service

WARNING: Waiting for service 'Computer Browser (Browser)' to finish stopping...
WARNING: Waiting for service 'Computer Browser (Browser)' to finish stopping...
Restart-Service : Cannot stop service 'Logical Disk Manager (dmserver)' because
 it has dependent services. It can only be stopped if the Force flag is set.
At line:1 char:57
+ Get-Service | Where-Object -FilterScript {$_.CanStop} | Restart-Service <<<<
WARNING: Waiting for service 'Print Spooler (Spooler)' to finish starting...
WARNING: Waiting for service 'Print Spooler (Spooler)' to finish starting...
```

Deze service-cmdlets hebben geen ComputerName-para meter, maar u kunt ze uitvoeren op een externe computer met behulp van de cmdlet Invoke-Command. Met de volgende opdracht wordt bijvoorbeeld de Spooler-service opnieuw gestart op de externe computer Server01.

```powershell
Invoke-Command -ComputerName Server01 {Restart-Service Spooler}
```

## <a name="setting-service-properties"></a>Service-eigenschappen instellen

De `Set-Service` cmdlet wijzigt de eigenschappen van een service op een lokale of externe computer. Omdat de status van de service een eigenschap is, kunt u deze cmdlet gebruiken om een service te starten, te stoppen en te onderbreken.
De cmdlet Set-Service heeft ook een opstart type-para meter waarmee u het opstart type voor de service kunt wijzigen.

Als u wilt gebruiken `Set-Service` voor Windows Vista en latere versies van Windows, opent u Windows Power shell met de optie als administrator uitvoeren.

Zie [set-service](/powershell/module/Microsoft.PowerShell.Management/set-service) voor meer informatie.

## <a name="see-also"></a>Zie ook

- [Get-Service](/powershell/module/Microsoft.PowerShell.Management/get-service)
- [Set-Service](/powershell/module/Microsoft.PowerShell.Management/set-service)
- [Restart-Service](/powershell/module/Microsoft.PowerShell.Management/restart-service)
- [Suspend-Service](/powershell/module/Microsoft.PowerShell.Management/suspend-service)
