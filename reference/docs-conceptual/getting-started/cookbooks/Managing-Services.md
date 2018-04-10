---
ms.date: 06/05/2017
keywords: PowerShell-cmdlet
title: Services beheren
ms.assetid: 7a410e4d-514b-4813-ba0c-0d8cef88df31
ms.openlocfilehash: f3231d1922568e552534f3d3face3864d1610d65
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 04/09/2018
---
# <a name="managing-services"></a>Services beheren

Er zijn acht core Service-cmdlets, die zijn bestemd voor een breed scala aan servicetaken. Kijken we alleen weergeven en wijzigen van de status voor services actief, maar u kunt een lijst Service cmdlets ophalen met behulp van **Get-Help \&#42;-Service**, en vindt u informatie over elke cmdlet Service met behulp van **Get-Help < naam Cmdlet >**, zoals **Get-Help nieuwe Service**.

## <a name="getting-services"></a>Ophalen van Services

U kunt de services op een lokale of externe computer verkrijgen door middel van de **Get-Service** cmdlet. Net als bij **Get-Process**, waarbij de **Get-Service** opdracht zonder parameters retourneert alle services. U kunt filteren op naam, zelfs met een sterretje als jokerteken:

```
PS> Get-Service -Name se*

Status   Name               DisplayName
------   ----               -----------
Running  seclogon           Secondary Logon
Running  SENS               System Event Notification
Stopped  ServiceLayer       ServiceLayer
```

Omdat het is niet altijd duidelijk wat de echte naam voor de service is, kunt u wellicht moet u services zoeken op weergavenaam. U kunt dit doen door een specifieke naam jokertekens gebruikt of als een lijst met weergavenamen:

```
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

U kunt de parameter ComputerName van de cmdlet Get-Service gebruiken om op te halen van de services op externe computers. De parameter ComputerName accepteert meerdere waarden en jokertekens, zodat u de services op meerdere computers met één opdracht krijgt. De volgende opdracht worden bijvoorbeeld de services op de externe computer Server01 opgehaald.

```powershell
Get-Service -ComputerName Server01
```

## <a name="getting-required-and-dependent-services"></a>Ophalen van vereist en afhankelijke Services

De cmdlet Get-Service heeft twee parameters die zeer nuttig zijn in Servicebeheer zijn. De parameter DependentServices opgehaald services die afhankelijk van de service zijn. De parameter RequiredServices opgehaald services waarvan deze service afhankelijk is.

Deze parameters worden alleen de waarden van de DependentServices en ServicesDependedOn weergeven (alias = RequiredServices) eigenschappen van het object System.ServiceProcess.ServiceController die Get-Service retourneert, maar ze vereenvoudigen opdrachten en ophalen Deze informatie is veel eenvoudiger.

De volgende opdracht haalt de services die de service LanmanWorkstation vereist.

```
PS> Get-Service -Name LanmanWorkstation -RequiredServices

Status   Name               DisplayName
------   ----               -----------
Running  MRxSmb20           SMB 2.0 MiniRedirector
Running  bowser             Bowser
Running  MRxSmb10           SMB 1.x MiniRedirector
Running  NSI                Network Store Interface Service
```

De volgende opdracht haalt de services waarvoor de LanmanWorkstation-service.

```
PS> Get-Service -Name LanmanWorkstation -DependentServices

Status   Name               DisplayName
------   ----               -----------
Running  SessionEnv         Terminal Services Configuration
Running  Netlogon           Netlogon
Stopped  Browser            Computer Browser
Running  BITS               Background Intelligent Transfer Ser...
```

U kunt zelfs krijgen alle services die afhankelijk zijn. De volgende opdracht wordt geregeld en vervolgens de cmdlet Format-Table wordt gebruikt om de Status, naam, RequiredServices en DependentServices eigenschappen van de services op de computer weer te geven.

```powershell
Get-Service -Name * | Where-Object {$_.RequiredServices -or $_.DependentServices} | Format-Table -Property Status, Name, RequiredServices, DependentServices -auto
```

## <a name="stopping-starting-suspending-and-restarting-services"></a>Stoppen, starten, onderbreken en opnieuw starten van Services
De Service van alle cmdlets hebben dezelfde algemene vorm. Services kunnen worden opgegeven met common name of display name en lijsten en jokertekens als waarden. Als u wilt stoppen met de afdrukspooler, gebruiken:

```powershell
Stop-Service -Name spooler
```

Als u wilt de afdrukspooler starten nadat deze is gestopt, gebruikt u:

```powershell
Start-Service -Name spooler
```

Als u wilt de afdrukspooler onderbreken, gebruikt u:

```powershell
Suspend-Service -Name spooler
```

De **herstarten-Service** cmdlet werkt op dezelfde manier als de Service-cmdlets, maar we enkele complexere voorbeelden voor tonen. Geef in het eenvoudigste gebruik, de naam van de service:

```
PS> Restart-Service -Name spooler

WARNING: Waiting for service 'Print Spooler (Spooler)' to finish starting...
WARNING: Waiting for service 'Print Spooler (Spooler)' to finish starting...
PS>
```

U ziet dat u krijgt een herhaalde waarschuwing over de afdrukspooler wordt opgestart. Wanneer u een servicebewerking die enige tijd duren uitvoert, waarschuwt Windows PowerShell u nog steeds wordt geprobeerd de taak uit te voeren.

Als u wilt meerdere services opnieuw starten, kunt u een lijst met services, ze filteren en voert u het opnieuw opstarten:

```
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

Deze cmdlets Service hoeft niet een parameter ComputerName, maar op een externe computer uitvoeren met behulp van de cmdlet Invoke-Command. Bijvoorbeeld, in de volgende opdracht de Spooler-service op de externe computer Server01 opnieuw opgestart.

```powershell
Invoke-Command -ComputerName Server01 {Restart-Service Spooler}
```

## <a name="setting-service-properties"></a>Service-Instellingseigenschappen

De cmdlet Set-Service wijzigt de eigenschappen van een service op een lokale of externe computer. Omdat de status van de eigenschap is, kunt u deze cmdlet te starten, stoppen en onderbreken van een service. De cmdlet Set-Service heeft ook een parameter StartupType waarmee u het opstarttype kunt wijzigen.

Voor het gebruik Set-Service in Windows Vista en latere versies van Windows, opent u Windows PowerShell met de optie 'Als administrator uitvoeren'.

Zie voor meer informatie [Service instellen [m2]](https://technet.microsoft.com/library/b71e29ed-372b-4e32-a4b7-5eb6216e56c3)

## <a name="see-also"></a>Zie ook

- [Get-Service [m2]](https://technet.microsoft.com/en-us/library/0a09cb22-0a1c-4a79-9851-4e53075f9cf6)
- [Set-Service [m2]](https://technet.microsoft.com/library/b71e29ed-372b-4e32-a4b7-5eb6216e56c3)
- [Restart-Service [m2]](https://technet.microsoft.com/en-us/library/45acf50d-2277-4523-baf7-ce7ced977d0f)
- [[M2] Suspend-Service](https://technet.microsoft.com/en-us/library/c8492b87-0e21-4faf-8054-3c83c2ec2826)