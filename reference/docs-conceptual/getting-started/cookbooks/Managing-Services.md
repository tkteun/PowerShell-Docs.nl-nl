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
# <a name="managing-services"></a><span data-ttu-id="2ac83-103">Services beheren</span><span class="sxs-lookup"><span data-stu-id="2ac83-103">Managing Services</span></span>

<span data-ttu-id="2ac83-104">Er zijn acht core Service-cmdlets, die zijn bestemd voor een breed scala aan servicetaken.</span><span class="sxs-lookup"><span data-stu-id="2ac83-104">There are eight core Service cmdlets, designed for a wide range of service tasks .</span></span> <span data-ttu-id="2ac83-105">Kijken we alleen weergeven en wijzigen van de status voor services actief, maar u kunt een lijst Service cmdlets ophalen met behulp van **Get-Help \&#42;-Service**, en vindt u informatie over elke cmdlet Service met behulp van **Get-Help < naam Cmdlet >**, zoals **Get-Help nieuwe Service**.</span><span class="sxs-lookup"><span data-stu-id="2ac83-105">We will look only at listing and changing running state for services, but you can get a list Service cmdlets by using **Get-Help \&#42;-Service**, and you can find information about each Service cmdlet by using **Get-Help<Cmdlet-Name>**, such as **Get-Help New-Service**.</span></span>

## <a name="getting-services"></a><span data-ttu-id="2ac83-106">Ophalen van Services</span><span class="sxs-lookup"><span data-stu-id="2ac83-106">Getting Services</span></span>

<span data-ttu-id="2ac83-107">U kunt de services op een lokale of externe computer verkrijgen door middel van de **Get-Service** cmdlet.</span><span class="sxs-lookup"><span data-stu-id="2ac83-107">You can get the services on a local or remote computer by using the **Get-Service** cmdlet.</span></span> <span data-ttu-id="2ac83-108">Net als bij **Get-Process**, waarbij de **Get-Service** opdracht zonder parameters retourneert alle services.</span><span class="sxs-lookup"><span data-stu-id="2ac83-108">As with **Get-Process**, using the **Get-Service** command without parameters returns all services.</span></span> <span data-ttu-id="2ac83-109">U kunt filteren op naam, zelfs met een sterretje als jokerteken:</span><span class="sxs-lookup"><span data-stu-id="2ac83-109">You can filter by name, even using an asterisk as a wildcard:</span></span>

```
PS> Get-Service -Name se*

Status   Name               DisplayName
------   ----               -----------
Running  seclogon           Secondary Logon
Running  SENS               System Event Notification
Stopped  ServiceLayer       ServiceLayer
```

<span data-ttu-id="2ac83-110">Omdat het is niet altijd duidelijk wat de echte naam voor de service is, kunt u wellicht moet u services zoeken op weergavenaam.</span><span class="sxs-lookup"><span data-stu-id="2ac83-110">Because it is not always obvious what the real name for the service is, you may find you need to find services by display name.</span></span> <span data-ttu-id="2ac83-111">U kunt dit doen door een specifieke naam jokertekens gebruikt of als een lijst met weergavenamen:</span><span class="sxs-lookup"><span data-stu-id="2ac83-111">You can do this by specific name, using wildcards, or using a list of display names:</span></span>

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

<span data-ttu-id="2ac83-112">U kunt de parameter ComputerName van de cmdlet Get-Service gebruiken om op te halen van de services op externe computers.</span><span class="sxs-lookup"><span data-stu-id="2ac83-112">You can use the ComputerName parameter of the Get-Service cmdlet to get the services on remote computers.</span></span> <span data-ttu-id="2ac83-113">De parameter ComputerName accepteert meerdere waarden en jokertekens, zodat u de services op meerdere computers met één opdracht krijgt.</span><span class="sxs-lookup"><span data-stu-id="2ac83-113">The ComputerName parameter accepts multiple values and wildcard characters, so you can get the services on multiple computers with a single command.</span></span> <span data-ttu-id="2ac83-114">De volgende opdracht worden bijvoorbeeld de services op de externe computer Server01 opgehaald.</span><span class="sxs-lookup"><span data-stu-id="2ac83-114">For example, the following command gets the services on the Server01 remote computer.</span></span>

```powershell
Get-Service -ComputerName Server01
```

## <a name="getting-required-and-dependent-services"></a><span data-ttu-id="2ac83-115">Ophalen van vereist en afhankelijke Services</span><span class="sxs-lookup"><span data-stu-id="2ac83-115">Getting Required and Dependent Services</span></span>

<span data-ttu-id="2ac83-116">De cmdlet Get-Service heeft twee parameters die zeer nuttig zijn in Servicebeheer zijn.</span><span class="sxs-lookup"><span data-stu-id="2ac83-116">The Get-Service cmdlet has two parameters that are very useful in service administration.</span></span> <span data-ttu-id="2ac83-117">De parameter DependentServices opgehaald services die afhankelijk van de service zijn.</span><span class="sxs-lookup"><span data-stu-id="2ac83-117">The DependentServices parameter gets services that depend on the service.</span></span> <span data-ttu-id="2ac83-118">De parameter RequiredServices opgehaald services waarvan deze service afhankelijk is.</span><span class="sxs-lookup"><span data-stu-id="2ac83-118">The RequiredServices parameter gets services upon which this service depends.</span></span>

<span data-ttu-id="2ac83-119">Deze parameters worden alleen de waarden van de DependentServices en ServicesDependedOn weergeven (alias = RequiredServices) eigenschappen van het object System.ServiceProcess.ServiceController die Get-Service retourneert, maar ze vereenvoudigen opdrachten en ophalen Deze informatie is veel eenvoudiger.</span><span class="sxs-lookup"><span data-stu-id="2ac83-119">These parameters just display the values of the DependentServices and ServicesDependedOn (alias=RequiredServices) properties of the System.ServiceProcess.ServiceController object that Get-Service returns, but they simplify commands and make getting this information much simpler.</span></span>

<span data-ttu-id="2ac83-120">De volgende opdracht haalt de services die de service LanmanWorkstation vereist.</span><span class="sxs-lookup"><span data-stu-id="2ac83-120">The following command gets the services that the LanmanWorkstation service requires.</span></span>

```
PS> Get-Service -Name LanmanWorkstation -RequiredServices

Status   Name               DisplayName
------   ----               -----------
Running  MRxSmb20           SMB 2.0 MiniRedirector
Running  bowser             Bowser
Running  MRxSmb10           SMB 1.x MiniRedirector
Running  NSI                Network Store Interface Service
```

<span data-ttu-id="2ac83-121">De volgende opdracht haalt de services waarvoor de LanmanWorkstation-service.</span><span class="sxs-lookup"><span data-stu-id="2ac83-121">The following command gets the services that require the LanmanWorkstation service.</span></span>

```
PS> Get-Service -Name LanmanWorkstation -DependentServices

Status   Name               DisplayName
------   ----               -----------
Running  SessionEnv         Terminal Services Configuration
Running  Netlogon           Netlogon
Stopped  Browser            Computer Browser
Running  BITS               Background Intelligent Transfer Ser...
```

<span data-ttu-id="2ac83-122">U kunt zelfs krijgen alle services die afhankelijk zijn.</span><span class="sxs-lookup"><span data-stu-id="2ac83-122">You can even get all services that have dependencies.</span></span> <span data-ttu-id="2ac83-123">De volgende opdracht wordt geregeld en vervolgens de cmdlet Format-Table wordt gebruikt om de Status, naam, RequiredServices en DependentServices eigenschappen van de services op de computer weer te geven.</span><span class="sxs-lookup"><span data-stu-id="2ac83-123">The following command does just that, and then it uses the Format-Table cmdlet to display the Status, Name, RequiredServices and DependentServices properties of the services on the computer.</span></span>

```powershell
Get-Service -Name * | Where-Object {$_.RequiredServices -or $_.DependentServices} | Format-Table -Property Status, Name, RequiredServices, DependentServices -auto
```

## <a name="stopping-starting-suspending-and-restarting-services"></a><span data-ttu-id="2ac83-124">Stoppen, starten, onderbreken en opnieuw starten van Services</span><span class="sxs-lookup"><span data-stu-id="2ac83-124">Stopping, Starting, Suspending, and Restarting Services</span></span>
<span data-ttu-id="2ac83-125">De Service van alle cmdlets hebben dezelfde algemene vorm.</span><span class="sxs-lookup"><span data-stu-id="2ac83-125">The Service cmdlets all have the same general form.</span></span> <span data-ttu-id="2ac83-126">Services kunnen worden opgegeven met common name of display name en lijsten en jokertekens als waarden.</span><span class="sxs-lookup"><span data-stu-id="2ac83-126">Services can be specified by common name or display name, and take lists and wildcards as values.</span></span> <span data-ttu-id="2ac83-127">Als u wilt stoppen met de afdrukspooler, gebruiken:</span><span class="sxs-lookup"><span data-stu-id="2ac83-127">To stop the print spooler, use:</span></span>

```powershell
Stop-Service -Name spooler
```

<span data-ttu-id="2ac83-128">Als u wilt de afdrukspooler starten nadat deze is gestopt, gebruikt u:</span><span class="sxs-lookup"><span data-stu-id="2ac83-128">To start the print spooler after it is stopped, use:</span></span>

```powershell
Start-Service -Name spooler
```

<span data-ttu-id="2ac83-129">Als u wilt de afdrukspooler onderbreken, gebruikt u:</span><span class="sxs-lookup"><span data-stu-id="2ac83-129">To suspend the print spooler, use:</span></span>

```powershell
Suspend-Service -Name spooler
```

<span data-ttu-id="2ac83-130">De **herstarten-Service** cmdlet werkt op dezelfde manier als de Service-cmdlets, maar we enkele complexere voorbeelden voor tonen.</span><span class="sxs-lookup"><span data-stu-id="2ac83-130">The **Restart-Service** cmdlet works in the same manner as the other Service cmdlets, but we will show some more complex examples for it.</span></span> <span data-ttu-id="2ac83-131">Geef in het eenvoudigste gebruik, de naam van de service:</span><span class="sxs-lookup"><span data-stu-id="2ac83-131">In the simplest use, you specify the name of the service:</span></span>

```
PS> Restart-Service -Name spooler

WARNING: Waiting for service 'Print Spooler (Spooler)' to finish starting...
WARNING: Waiting for service 'Print Spooler (Spooler)' to finish starting...
PS>
```

<span data-ttu-id="2ac83-132">U ziet dat u krijgt een herhaalde waarschuwing over de afdrukspooler wordt opgestart.</span><span class="sxs-lookup"><span data-stu-id="2ac83-132">You will notice that you get a repeated warning message about the Print Spooler starting up.</span></span> <span data-ttu-id="2ac83-133">Wanneer u een servicebewerking die enige tijd duren uitvoert, waarschuwt Windows PowerShell u nog steeds wordt geprobeerd de taak uit te voeren.</span><span class="sxs-lookup"><span data-stu-id="2ac83-133">When you perform a service operation that takes some time, Windows PowerShell will notify you that it is still attempting to perform the task.</span></span>

<span data-ttu-id="2ac83-134">Als u wilt meerdere services opnieuw starten, kunt u een lijst met services, ze filteren en voert u het opnieuw opstarten:</span><span class="sxs-lookup"><span data-stu-id="2ac83-134">If you want to restart multiple services, you can get a list of services, filter them, and then perform the restart:</span></span>

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

<span data-ttu-id="2ac83-135">Deze cmdlets Service hoeft niet een parameter ComputerName, maar op een externe computer uitvoeren met behulp van de cmdlet Invoke-Command.</span><span class="sxs-lookup"><span data-stu-id="2ac83-135">These Service cmdlets do not have a ComputerName parameter, but you can run them on a remote computer by using the Invoke-Command cmdlet.</span></span> <span data-ttu-id="2ac83-136">Bijvoorbeeld, in de volgende opdracht de Spooler-service op de externe computer Server01 opnieuw opgestart.</span><span class="sxs-lookup"><span data-stu-id="2ac83-136">For example, the following command restarts the Spooler service on the Server01 remote computer.</span></span>

```powershell
Invoke-Command -ComputerName Server01 {Restart-Service Spooler}
```

## <a name="setting-service-properties"></a><span data-ttu-id="2ac83-137">Service-Instellingseigenschappen</span><span class="sxs-lookup"><span data-stu-id="2ac83-137">Setting Service Properties</span></span>

<span data-ttu-id="2ac83-138">De cmdlet Set-Service wijzigt de eigenschappen van een service op een lokale of externe computer.</span><span class="sxs-lookup"><span data-stu-id="2ac83-138">The Set-Service cmdlet changes the properties of a service on a local or remote computer.</span></span> <span data-ttu-id="2ac83-139">Omdat de status van de eigenschap is, kunt u deze cmdlet te starten, stoppen en onderbreken van een service.</span><span class="sxs-lookup"><span data-stu-id="2ac83-139">Because the service status is a property, you can use this cmdlet to start, stop, and suspend a service.</span></span> <span data-ttu-id="2ac83-140">De cmdlet Set-Service heeft ook een parameter StartupType waarmee u het opstarttype kunt wijzigen.</span><span class="sxs-lookup"><span data-stu-id="2ac83-140">The Set-Service cmdlet also has a StartupType parameter that lets you change the service startup type.</span></span>

<span data-ttu-id="2ac83-141">Voor het gebruik Set-Service in Windows Vista en latere versies van Windows, opent u Windows PowerShell met de optie 'Als administrator uitvoeren'.</span><span class="sxs-lookup"><span data-stu-id="2ac83-141">To use Set-Service on Windows Vista and later versions of Windows, open Windows PowerShell with the "Run as administrator" option.</span></span>

<span data-ttu-id="2ac83-142">Zie voor meer informatie [Service instellen [m2]](https://technet.microsoft.com/library/b71e29ed-372b-4e32-a4b7-5eb6216e56c3)</span><span class="sxs-lookup"><span data-stu-id="2ac83-142">For more information, see [Set-Service [m2]](https://technet.microsoft.com/library/b71e29ed-372b-4e32-a4b7-5eb6216e56c3)</span></span>

## <a name="see-also"></a><span data-ttu-id="2ac83-143">Zie ook</span><span class="sxs-lookup"><span data-stu-id="2ac83-143">See Also</span></span>

- <span data-ttu-id="2ac83-144">[Get-Service [m2]](https://technet.microsoft.com/en-us/library/0a09cb22-0a1c-4a79-9851-4e53075f9cf6)</span><span class="sxs-lookup"><span data-stu-id="2ac83-144">[Get-Service [m2]](https://technet.microsoft.com/en-us/library/0a09cb22-0a1c-4a79-9851-4e53075f9cf6)</span></span>
- <span data-ttu-id="2ac83-145">[Set-Service [m2]](https://technet.microsoft.com/library/b71e29ed-372b-4e32-a4b7-5eb6216e56c3)</span><span class="sxs-lookup"><span data-stu-id="2ac83-145">[Set-Service [m2]](https://technet.microsoft.com/library/b71e29ed-372b-4e32-a4b7-5eb6216e56c3)</span></span>
- <span data-ttu-id="2ac83-146">[Restart-Service [m2]](https://technet.microsoft.com/en-us/library/45acf50d-2277-4523-baf7-ce7ced977d0f)</span><span class="sxs-lookup"><span data-stu-id="2ac83-146">[Restart-Service [m2]](https://technet.microsoft.com/en-us/library/45acf50d-2277-4523-baf7-ce7ced977d0f)</span></span>
- <span data-ttu-id="2ac83-147">[[M2] Suspend-Service](https://technet.microsoft.com/en-us/library/c8492b87-0e21-4faf-8054-3c83c2ec2826)</span><span class="sxs-lookup"><span data-stu-id="2ac83-147">[Suspend-Service [m2]](https://technet.microsoft.com/en-us/library/c8492b87-0e21-4faf-8054-3c83c2ec2826)</span></span>