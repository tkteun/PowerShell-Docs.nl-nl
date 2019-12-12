---
ms.date: 06/05/2017
keywords: Power shell, cmdlet
title: Services beheren
ms.openlocfilehash: d9e17b2d91ae01d7d4d6d573348289fa68dc9c56
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 12/05/2019
ms.locfileid: "67030163"
---
# <a name="managing-services"></a><span data-ttu-id="9be83-103">Services beheren</span><span class="sxs-lookup"><span data-stu-id="9be83-103">Managing Services</span></span>

<span data-ttu-id="9be83-104">Er zijn acht core service-cmdlets, ontworpen voor een breed scala aan service taken.</span><span class="sxs-lookup"><span data-stu-id="9be83-104">There are eight core Service cmdlets, designed for a wide range of service tasks .</span></span> <span data-ttu-id="9be83-105">We kijken alleen naar het aanbieden en wijzigen van de actieve status voor services, maar u kunt een lijst met Service-cmdlets ophalen met behulp van `Get-Help \*-Service`en u kunt informatie over elke service-cmdlet vinden met behulp van `Get-Help <Cmdlet-Name>`, zoals `Get-Help New-Service`.</span><span class="sxs-lookup"><span data-stu-id="9be83-105">We will look only at listing and changing running state for services, but you can get a list of Service cmdlets by using `Get-Help \*-Service`, and you can find information about each Service cmdlet by using `Get-Help <Cmdlet-Name>`, such as `Get-Help New-Service`.</span></span>

## <a name="getting-services"></a><span data-ttu-id="9be83-106">Services ophalen</span><span class="sxs-lookup"><span data-stu-id="9be83-106">Getting Services</span></span>

<span data-ttu-id="9be83-107">U kunt de services op een lokale of externe computer ophalen met behulp van de cmdlet `Get-Service`.</span><span class="sxs-lookup"><span data-stu-id="9be83-107">You can get the services on a local or remote computer by using the `Get-Service` cmdlet.</span></span> <span data-ttu-id="9be83-108">Net als bij `Get-Process`, met behulp van de `Get-Service` opdracht zonder para meters worden alle services geretourneerd.</span><span class="sxs-lookup"><span data-stu-id="9be83-108">As with `Get-Process`, using the `Get-Service` command without parameters returns all services.</span></span> <span data-ttu-id="9be83-109">U kunt filteren op naam, zelfs met een sterretje als Joker teken:</span><span class="sxs-lookup"><span data-stu-id="9be83-109">You can filter by name, even using an asterisk as a wildcard:</span></span>

```powershell
PS> Get-Service -Name se*

Status   Name               DisplayName
------   ----               -----------
Running  seclogon           Secondary Logon
Running  SENS               System Event Notification
Stopped  ServiceLayer       ServiceLayer
```

<span data-ttu-id="9be83-110">Omdat het niet altijd duidelijk is wat de werkelijke naam voor de service is, kunt u de services op weergave naam zoeken.</span><span class="sxs-lookup"><span data-stu-id="9be83-110">Because it is not always obvious what the real name for the service is, you may find you need to find services by display name.</span></span> <span data-ttu-id="9be83-111">U kunt dit doen op basis van een specifieke naam, met behulp van joker tekens of met een lijst met weergave namen:</span><span class="sxs-lookup"><span data-stu-id="9be83-111">You can do this by specific name, using wildcards, or using a list of display names:</span></span>

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

<span data-ttu-id="9be83-112">U kunt de para meter ComputerName van de cmdlet Get-service gebruiken om de services op externe computers op te halen.</span><span class="sxs-lookup"><span data-stu-id="9be83-112">You can use the ComputerName parameter of the Get-Service cmdlet to get the services on remote computers.</span></span> <span data-ttu-id="9be83-113">De para meter ComputerName accepteert meerdere waarden en Joker tekens, zodat u de services op meerdere computers met één opdracht kunt ophalen.</span><span class="sxs-lookup"><span data-stu-id="9be83-113">The ComputerName parameter accepts multiple values and wildcard characters, so you can get the services on multiple computers with a single command.</span></span> <span data-ttu-id="9be83-114">Met de volgende opdracht worden bijvoorbeeld de services op de externe computer Server01 opgehaald.</span><span class="sxs-lookup"><span data-stu-id="9be83-114">For example, the following command gets the services on the Server01 remote computer.</span></span>

```powershell
Get-Service -ComputerName Server01
```

## <a name="getting-required-and-dependent-services"></a><span data-ttu-id="9be83-115">Vereiste en afhankelijke services ophalen</span><span class="sxs-lookup"><span data-stu-id="9be83-115">Getting Required and Dependent Services</span></span>

<span data-ttu-id="9be83-116">De cmdlet Get-service heeft twee para meters die erg nuttig zijn in Service beheer.</span><span class="sxs-lookup"><span data-stu-id="9be83-116">The Get-Service cmdlet has two parameters that are very useful in service administration.</span></span> <span data-ttu-id="9be83-117">De para meter DependentServices haalt Services op die afhankelijk zijn van de service.</span><span class="sxs-lookup"><span data-stu-id="9be83-117">The DependentServices parameter gets services that depend on the service.</span></span> <span data-ttu-id="9be83-118">De para meter RequiredServices haalt Services op waarvan deze service afhankelijk is.</span><span class="sxs-lookup"><span data-stu-id="9be83-118">The RequiredServices parameter gets services upon which this service depends.</span></span>

<span data-ttu-id="9be83-119">Met deze para meters worden alleen de waarden van de eigenschappen DependentServices en ServicesDependedOn (alias = RequiredServices) van het object System. ServiceProcess. ServiceController weer gegeven dat de Get-service retourneert, maar de opdrachten worden vereenvoudigd en krijgen deze gegevens zijn veel eenvoudiger.</span><span class="sxs-lookup"><span data-stu-id="9be83-119">These parameters just display the values of the DependentServices and ServicesDependedOn (alias=RequiredServices) properties of the System.ServiceProcess.ServiceController object that Get-Service returns, but they simplify commands and make getting this information much simpler.</span></span>

<span data-ttu-id="9be83-120">Met de volgende opdracht worden de services opgehaald die de LanmanWorkstation-service nodig heeft.</span><span class="sxs-lookup"><span data-stu-id="9be83-120">The following command gets the services that the LanmanWorkstation service requires.</span></span>

```powershell
PS> Get-Service -Name LanmanWorkstation -RequiredServices

Status   Name               DisplayName
------   ----               -----------
Running  MRxSmb20           SMB 2.0 MiniRedirector
Running  bowser             Bowser
Running  MRxSmb10           SMB 1.x MiniRedirector
Running  NSI                Network Store Interface Service
```

<span data-ttu-id="9be83-121">Met de volgende opdracht worden de services opgehaald waarvoor de LanmanWorkstation-service is vereist.</span><span class="sxs-lookup"><span data-stu-id="9be83-121">The following command gets the services that require the LanmanWorkstation service.</span></span>

```powershell
PS> Get-Service -Name LanmanWorkstation -DependentServices

Status   Name               DisplayName
------   ----               -----------
Running  SessionEnv         Terminal Services Configuration
Running  Netlogon           Netlogon
Stopped  Browser            Computer Browser
Running  BITS               Background Intelligent Transfer Ser...
```

<span data-ttu-id="9be83-122">U kunt zelfs alle services ophalen die afhankelijkheden hebben.</span><span class="sxs-lookup"><span data-stu-id="9be83-122">You can even get all services that have dependencies.</span></span> <span data-ttu-id="9be83-123">De volgende opdracht is alleen dat, en vervolgens wordt de cmdlet Format-Table gebruikt om de eigenschappen status, naam, RequiredServices en DependentServices van de services op de computer weer te geven.</span><span class="sxs-lookup"><span data-stu-id="9be83-123">The following command does just that, and then it uses the Format-Table cmdlet to display the Status, Name, RequiredServices and DependentServices properties of the services on the computer.</span></span>

```powershell
Get-Service -Name * | Where-Object {$_.RequiredServices -or $_.DependentServices} | Format-Table -Property Status, Name, RequiredServices, DependentServices -auto
```

## <a name="stopping-starting-suspending-and-restarting-services"></a><span data-ttu-id="9be83-124">Services stoppen, starten, onderbreken en opnieuw starten</span><span class="sxs-lookup"><span data-stu-id="9be83-124">Stopping, Starting, Suspending, and Restarting Services</span></span>

<span data-ttu-id="9be83-125">De service-cmdlets hebben allemaal hetzelfde algemene formulier.</span><span class="sxs-lookup"><span data-stu-id="9be83-125">The Service cmdlets all have the same general form.</span></span> <span data-ttu-id="9be83-126">Services kunnen worden opgegeven met een algemene naam of weergave naam en lijsten en Joker tekens worden als waarden.</span><span class="sxs-lookup"><span data-stu-id="9be83-126">Services can be specified by common name or display name, and take lists and wildcards as values.</span></span> <span data-ttu-id="9be83-127">Als u de afdrukspooler wilt stoppen, gebruikt u:</span><span class="sxs-lookup"><span data-stu-id="9be83-127">To stop the print spooler, use:</span></span>

```powershell
Stop-Service -Name spooler
```

<span data-ttu-id="9be83-128">Als u de afdrukspooler wilt starten nadat deze is gestopt, gebruikt u:</span><span class="sxs-lookup"><span data-stu-id="9be83-128">To start the print spooler after it is stopped, use:</span></span>

```powershell
Start-Service -Name spooler
```

<span data-ttu-id="9be83-129">Als u de afdrukspooler wilt onderbreken, gebruikt u:</span><span class="sxs-lookup"><span data-stu-id="9be83-129">To suspend the print spooler, use:</span></span>

```powershell
Suspend-Service -Name spooler
```

<span data-ttu-id="9be83-130">De cmdlet `Restart-Service` werkt op dezelfde manier als de andere service-cmdlets, maar er worden een aantal complexere voor beelden weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="9be83-130">The `Restart-Service` cmdlet works in the same manner as the other Service cmdlets, but we will show some more complex examples for it.</span></span> <span data-ttu-id="9be83-131">In het eenvoudigste gebruik geeft u de naam van de service op:</span><span class="sxs-lookup"><span data-stu-id="9be83-131">In the simplest use, you specify the name of the service:</span></span>

```powershell
PS> Restart-Service -Name spooler

WARNING: Waiting for service 'Print Spooler (Spooler)' to finish starting...
WARNING: Waiting for service 'Print Spooler (Spooler)' to finish starting...
PS>
```

<span data-ttu-id="9be83-132">U ziet dat er een herhaalde waarschuwing wordt weer gegeven over het starten van de afdrukspooler.</span><span class="sxs-lookup"><span data-stu-id="9be83-132">You will notice that you get a repeated warning message about the Print Spooler starting up.</span></span> <span data-ttu-id="9be83-133">Wanneer u een service bewerking uitvoert die enige tijd in beslag neemt, wordt u door Windows Power shell op de hoogte gesteld dat er nog steeds wordt geprobeerd om de taak uit te voeren.</span><span class="sxs-lookup"><span data-stu-id="9be83-133">When you perform a service operation that takes some time, Windows PowerShell will notify you that it is still attempting to perform the task.</span></span>

<span data-ttu-id="9be83-134">Als u meerdere services opnieuw wilt starten, kunt u een lijst met services ophalen, deze filteren en vervolgens het opnieuw opstarten uitvoeren:</span><span class="sxs-lookup"><span data-stu-id="9be83-134">If you want to restart multiple services, you can get a list of services, filter them, and then perform the restart:</span></span>

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

<span data-ttu-id="9be83-135">Deze service-cmdlets hebben geen ComputerName-para meter, maar u kunt ze uitvoeren op een externe computer met behulp van de cmdlet invoke-opdracht.</span><span class="sxs-lookup"><span data-stu-id="9be83-135">These Service cmdlets do not have a ComputerName parameter, but you can run them on a remote computer by using the Invoke-Command cmdlet.</span></span> <span data-ttu-id="9be83-136">Met de volgende opdracht wordt bijvoorbeeld de Spooler-service opnieuw gestart op de externe computer Server01.</span><span class="sxs-lookup"><span data-stu-id="9be83-136">For example, the following command restarts the Spooler service on the Server01 remote computer.</span></span>

```powershell
Invoke-Command -ComputerName Server01 {Restart-Service Spooler}
```

## <a name="setting-service-properties"></a><span data-ttu-id="9be83-137">Service-eigenschappen instellen</span><span class="sxs-lookup"><span data-stu-id="9be83-137">Setting Service Properties</span></span>

<span data-ttu-id="9be83-138">Met de cmdlet `Set-Service` worden de eigenschappen van een service op een lokale of externe computer gewijzigd.</span><span class="sxs-lookup"><span data-stu-id="9be83-138">The `Set-Service` cmdlet changes the properties of a service on a local or remote computer.</span></span> <span data-ttu-id="9be83-139">Omdat de status van de service een eigenschap is, kunt u deze cmdlet gebruiken om een service te starten, te stoppen en te onderbreken.</span><span class="sxs-lookup"><span data-stu-id="9be83-139">Because the service status is a property, you can use this cmdlet to start, stop, and suspend a service.</span></span>
<span data-ttu-id="9be83-140">De cmdlet Set-service heeft ook een opstart type-para meter waarmee u het opstart type voor de service kunt wijzigen.</span><span class="sxs-lookup"><span data-stu-id="9be83-140">The Set-Service cmdlet also has a StartupType parameter that lets you change the service startup type.</span></span>

<span data-ttu-id="9be83-141">Als u `Set-Service` wilt gebruiken in Windows Vista en latere versies van Windows, opent u Windows Power shell met de optie als administrator uitvoeren.</span><span class="sxs-lookup"><span data-stu-id="9be83-141">To use `Set-Service` on Windows Vista and later versions of Windows, open Windows PowerShell with the "Run as administrator" option.</span></span>

<span data-ttu-id="9be83-142">Zie [set-service [m2]](https://technet.microsoft.com/library/b71e29ed-372b-4e32-a4b7-5eb6216e56c3) voor meer informatie</span><span class="sxs-lookup"><span data-stu-id="9be83-142">For more information, see [Set-Service [m2]](https://technet.microsoft.com/library/b71e29ed-372b-4e32-a4b7-5eb6216e56c3)</span></span>

## <a name="see-also"></a><span data-ttu-id="9be83-143">Zie ook</span><span class="sxs-lookup"><span data-stu-id="9be83-143">See Also</span></span>

- <span data-ttu-id="9be83-144">[Get-service [m2]](https://technet.microsoft.com/en-us/library/0a09cb22-0a1c-4a79-9851-4e53075f9cf6)</span><span class="sxs-lookup"><span data-stu-id="9be83-144">[Get-Service [m2]](https://technet.microsoft.com/en-us/library/0a09cb22-0a1c-4a79-9851-4e53075f9cf6)</span></span>
- <span data-ttu-id="9be83-145">[Set-service [m2]](https://technet.microsoft.com/library/b71e29ed-372b-4e32-a4b7-5eb6216e56c3)</span><span class="sxs-lookup"><span data-stu-id="9be83-145">[Set-Service [m2]](https://technet.microsoft.com/library/b71e29ed-372b-4e32-a4b7-5eb6216e56c3)</span></span>
- <span data-ttu-id="9be83-146">[Restart-service [m2]](https://technet.microsoft.com/en-us/library/45acf50d-2277-4523-baf7-ce7ced977d0f)</span><span class="sxs-lookup"><span data-stu-id="9be83-146">[Restart-Service [m2]](https://technet.microsoft.com/en-us/library/45acf50d-2277-4523-baf7-ce7ced977d0f)</span></span>
- <span data-ttu-id="9be83-147">[Suspend-service [m2]](https://technet.microsoft.com/en-us/library/c8492b87-0e21-4faf-8054-3c83c2ec2826)</span><span class="sxs-lookup"><span data-stu-id="9be83-147">[Suspend-Service [m2]](https://technet.microsoft.com/en-us/library/c8492b87-0e21-4faf-8054-3c83c2ec2826)</span></span>
