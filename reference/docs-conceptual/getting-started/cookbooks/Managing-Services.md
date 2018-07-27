---
ms.date: 06/05/2017
keywords: PowerShell-cmdlet
title: Services beheren
ms.assetid: 7a410e4d-514b-4813-ba0c-0d8cef88df31
ms.openlocfilehash: 81fd8802215da80ce22fa3fd4750b1df6efe8206
ms.sourcegitcommit: c3f1a83b59484651119630f3089aa51b6e7d4c3c
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/26/2018
ms.locfileid: "39268072"
---
# <a name="managing-services"></a>Services beheren

Er zijn acht core-Service-cmdlets, ontworpen voor een breed scala aan service-taken. We kijken alleen weergeven en wijzigen van de status voor services actief, maar krijgt u een lijst van Service-cmdlets met behulp van `Get-Help \*-Service`, en vindt u informatie over elke cmdlet Service met behulp van `Get-Help <Cmdlet-Name>`, zoals `Get-Help New-Service`.

## <a name="getting-services"></a>Ophalen van Services

U kunt de services krijgen bij een lokale of externe computer met behulp van de `Get-Service` cmdlet. Net als bij `Get-Process`, met de `Get-Service` opdracht zonder parameters, retourneert alle services. U kunt filteren op naam, zelfs met een sterretje als jokerteken:

```powershell
PS> Get-Service -Name se*

Status   Name               DisplayName
------   ----               -----------
Running  seclogon           Secondary Logon
Running  SENS               System Event Notification
Stopped  ServiceLayer       ServiceLayer
```

Omdat het is niet altijd duidelijk wat de echte naam van de service is, merkt u misschien moet u services vinden op weergavenaam. U kunt dit doen met de specifieke naam, gebruik van jokertekens of met behulp van een lijst met weergavenamen:

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

U kunt de parameter ComputerName van de cmdlet Get-Service gebruiken om op te halen van de services op externe computers. De parameter ComputerName accepteert meerdere waarden en jokertekens bevatten, zodat u kunt de services op meerdere computers met slechts één opdracht. De volgende opdracht wordt bijvoorbeeld de services op de externe computer Server01.

```powershell
Get-Service -ComputerName Server01
```

## <a name="getting-required-and-dependent-services"></a>Ophalen van vereist en afhankelijke Services

De cmdlet Get-Service heeft twee parameters die zeer nuttig zijn in Servicebeheer zijn. De parameter DependentServices services die afhankelijk van de service zijn opgehaald. De parameter RequiredServices haalt services waarvan deze service afhankelijk is.

Deze parameters worden alleen de waarden van de DependentServices en ServicesDependedOn weergeven (alias = RequiredServices) eigenschappen van het object System.ServiceProcess.ServiceController Get-Service retourneert, maar deze eenvoudige opdrachten en breng ophalen Deze informatie is veel eenvoudiger.

De volgende opdracht wordt de services die de LanmanWorkstation-service is vereist.

```powershell
PS> Get-Service -Name LanmanWorkstation -RequiredServices

Status   Name               DisplayName
------   ----               -----------
Running  MRxSmb20           SMB 2.0 MiniRedirector
Running  bowser             Bowser
Running  MRxSmb10           SMB 1.x MiniRedirector
Running  NSI                Network Store Interface Service
```

De volgende opdracht wordt de services waarvoor de LanmanWorkstation-service.

```powershell
PS> Get-Service -Name LanmanWorkstation -DependentServices

Status   Name               DisplayName
------   ----               -----------
Running  SessionEnv         Terminal Services Configuration
Running  Netlogon           Netlogon
Stopped  Browser            Computer Browser
Running  BITS               Background Intelligent Transfer Ser...
```

Ook krijgt u alle services die afhankelijkheden hebben. De volgende opdracht precies dat doet en vervolgens de cmdlet Format-Table wordt gebruikt om de Status, de naam, RequiredServices en DependentServices eigenschappen van de services op de computer weer te geven.

```powershell
Get-Service -Name * | Where-Object {$_.RequiredServices -or $_.DependentServices} | Format-Table -Property Status, Name, RequiredServices, DependentServices -auto
```

## <a name="stopping-starting-suspending-and-restarting-services"></a>Stoppen, starten, onderbreken en opnieuw starten van Services

Het alle Service-cmdlets hebben de dezelfde algemene vorm. Services kunnen worden opgegeven met common name of display name en lijsten en jokertekens als waarden. Als u wilt de afdruk-spooler stoppen, gebruikt u:

```powershell
Stop-Service -Name spooler
```

Als u wilt de afdruk-spooler starten nadat deze is gestopt, gebruikt u:

```powershell
Start-Service -Name spooler
```

Als u wilt onderbreken de afdruk-spooler, gebruikt u:

```powershell
Suspend-Service -Name spooler
```

De `Restart-Service` cmdlet werkt op dezelfde manier als de andere Service-cmdlets, maar we enkele complexere voorbeelden tonen voor deze. Geef de naam van de service in het eenvoudigste gebruik:

```powershell
PS> Restart-Service -Name spooler

WARNING: Waiting for service 'Print Spooler (Spooler)' to finish starting...
WARNING: Waiting for service 'Print Spooler (Spooler)' to finish starting...
PS>
```

U zult merken dat u krijgt een herhaalde waarschuwing over de afdrukspooler gestart. Als u de bewerking van een service die het duurt enige tijd uitvoert, ontvangt Windows PowerShell u dat deze nog steeds probeert de taak uit te voeren.

Als u wilt dat meerdere services opnieuw starten, kunt u een lijst met services, filteren en voert u het opnieuw opstarten:

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

Deze cmdlets Service nog geen een ComputerName-parameter, maar u kunt ze op een externe computer uitvoeren met behulp van de cmdlet Invoke-Command. Bijvoorbeeld, dat de volgende opdracht de Spooler-service op de externe computer Server01 wordt opnieuw opgestart.

```powershell
Invoke-Command -ComputerName Server01 {Restart-Service Spooler}
```

## <a name="setting-service-properties"></a>Service-Instellingseigenschappen

De `Set-Service` cmdlet worden de eigenschappen van een service op een lokale of externe computer gewijzigd. Omdat de status van de service is een eigenschap, kunt u deze cmdlet te starten, stoppen en onderbreken van een service.
De cmdlet Set-Service heeft ook een opstarttype van parameter waarmee u het opstarttype service wijzigen.

Gebruik `Set-Service` in Windows Vista en latere versies van Windows, opent u Windows PowerShell met de optie 'Als administrator uitvoeren'.

Zie voor meer informatie, [-Service instellen [m2]](https://technet.microsoft.com/library/b71e29ed-372b-4e32-a4b7-5eb6216e56c3)

## <a name="see-also"></a>Zie ook

- [Get-Service [m2]](https://technet.microsoft.com/en-us/library/0a09cb22-0a1c-4a79-9851-4e53075f9cf6)
- [Set-Service [m2]](https://technet.microsoft.com/library/b71e29ed-372b-4e32-a4b7-5eb6216e56c3)
- [[M2] restart-Service](https://technet.microsoft.com/en-us/library/45acf50d-2277-4523-baf7-ce7ced977d0f)
- [[M2] onderbreken-Service](https://technet.microsoft.com/en-us/library/c8492b87-0e21-4faf-8054-3c83c2ec2826)