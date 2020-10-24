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
# <a name="managing-services"></a><span data-ttu-id="35959-104">Services beheren</span><span class="sxs-lookup"><span data-stu-id="35959-104">Managing Services</span></span>

<span data-ttu-id="35959-105">Er zijn acht core service-cmdlets, ontworpen voor een breed scala aan service taken.</span><span class="sxs-lookup"><span data-stu-id="35959-105">There are eight core Service cmdlets, designed for a wide range of service tasks .</span></span> <span data-ttu-id="35959-106">We kijken alleen naar het aanbieden en wijzigen van de actieve status voor services, maar u kunt een lijst met Service-cmdlets krijgen met behulp van `Get-Help \*-Service` , en u kunt informatie over elke service-cmdlet vinden met `Get-Help <Cmdlet-Name>` , zoals `Get-Help New-Service` .</span><span class="sxs-lookup"><span data-stu-id="35959-106">We will look only at listing and changing running state for services, but you can get a list of Service cmdlets by using `Get-Help \*-Service`, and you can find information about each Service cmdlet by using `Get-Help <Cmdlet-Name>`, such as `Get-Help New-Service`.</span></span>

## <a name="getting-services"></a><span data-ttu-id="35959-107">Services ophalen</span><span class="sxs-lookup"><span data-stu-id="35959-107">Getting Services</span></span>

<span data-ttu-id="35959-108">U kunt de services op een lokale of externe computer ophalen met behulp van de- `Get-Service` cmdlet.</span><span class="sxs-lookup"><span data-stu-id="35959-108">You can get the services on a local or remote computer by using the `Get-Service` cmdlet.</span></span> <span data-ttu-id="35959-109">Net als bij `Get-Process` , met behulp van de `Get-Service` opdracht zonder para meters, worden alle services geretourneerd.</span><span class="sxs-lookup"><span data-stu-id="35959-109">As with `Get-Process`, using the `Get-Service` command without parameters returns all services.</span></span> <span data-ttu-id="35959-110">U kunt filteren op naam, zelfs met een sterretje als Joker teken:</span><span class="sxs-lookup"><span data-stu-id="35959-110">You can filter by name, even using an asterisk as a wildcard:</span></span>

```powershell
PS> Get-Service -Name se*

Status   Name               DisplayName
------   ----               -----------
Running  seclogon           Secondary Logon
Running  SENS               System Event Notification
Stopped  ServiceLayer       ServiceLayer
```

<span data-ttu-id="35959-111">Omdat het niet altijd duidelijk is wat de werkelijke naam voor de service is, kunt u de services op weergave naam zoeken.</span><span class="sxs-lookup"><span data-stu-id="35959-111">Because it is not always obvious what the real name for the service is, you may find you need to find services by display name.</span></span> <span data-ttu-id="35959-112">U kunt dit doen op basis van een specifieke naam, met behulp van joker tekens of met een lijst met weergave namen:</span><span class="sxs-lookup"><span data-stu-id="35959-112">You can do this by specific name, using wildcards, or using a list of display names:</span></span>

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

<span data-ttu-id="35959-113">U kunt de para meter ComputerName van de cmdlet Get-Service gebruiken om de services op externe computers op te halen.</span><span class="sxs-lookup"><span data-stu-id="35959-113">You can use the ComputerName parameter of the Get-Service cmdlet to get the services on remote computers.</span></span> <span data-ttu-id="35959-114">De para meter ComputerName accepteert meerdere waarden en Joker tekens, zodat u de services op meerdere computers met één opdracht kunt ophalen.</span><span class="sxs-lookup"><span data-stu-id="35959-114">The ComputerName parameter accepts multiple values and wildcard characters, so you can get the services on multiple computers with a single command.</span></span> <span data-ttu-id="35959-115">Met de volgende opdracht worden bijvoorbeeld de services op de externe computer Server01 opgehaald.</span><span class="sxs-lookup"><span data-stu-id="35959-115">For example, the following command gets the services on the Server01 remote computer.</span></span>

```powershell
Get-Service -ComputerName Server01
```

## <a name="getting-required-and-dependent-services"></a><span data-ttu-id="35959-116">Vereiste en afhankelijke services ophalen</span><span class="sxs-lookup"><span data-stu-id="35959-116">Getting Required and Dependent Services</span></span>

<span data-ttu-id="35959-117">De cmdlet Get-Service heeft twee para meters die erg nuttig zijn in Service beheer.</span><span class="sxs-lookup"><span data-stu-id="35959-117">The Get-Service cmdlet has two parameters that are very useful in service administration.</span></span> <span data-ttu-id="35959-118">De para meter DependentServices haalt Services op die afhankelijk zijn van de service.</span><span class="sxs-lookup"><span data-stu-id="35959-118">The DependentServices parameter gets services that depend on the service.</span></span> <span data-ttu-id="35959-119">De para meter RequiredServices haalt Services op waarvan deze service afhankelijk is.</span><span class="sxs-lookup"><span data-stu-id="35959-119">The RequiredServices parameter gets services upon which this service depends.</span></span>

<span data-ttu-id="35959-120">Met deze para meters worden alleen de waarden weer gegeven van de eigenschappen DependentServices en ServicesDependedOn (alias = RequiredServices) van het object System. ServiceProcess. ServiceController dat Get-Service retourneert, maar de opdrachten worden vereenvoudigd en deze gegevens worden veel eenvoudiger gemaakt.</span><span class="sxs-lookup"><span data-stu-id="35959-120">These parameters just display the values of the DependentServices and ServicesDependedOn (alias=RequiredServices) properties of the System.ServiceProcess.ServiceController object that Get-Service returns, but they simplify commands and make getting this information much simpler.</span></span>

<span data-ttu-id="35959-121">Met de volgende opdracht worden de services opgehaald die de LanmanWorkstation-service nodig heeft.</span><span class="sxs-lookup"><span data-stu-id="35959-121">The following command gets the services that the LanmanWorkstation service requires.</span></span>

```powershell
PS> Get-Service -Name LanmanWorkstation -RequiredServices

Status   Name               DisplayName
------   ----               -----------
Running  MRxSmb20           SMB 2.0 MiniRedirector
Running  bowser             Bowser
Running  MRxSmb10           SMB 1.x MiniRedirector
Running  NSI                Network Store Interface Service
```

<span data-ttu-id="35959-122">Met de volgende opdracht worden de services opgehaald waarvoor de LanmanWorkstation-service is vereist.</span><span class="sxs-lookup"><span data-stu-id="35959-122">The following command gets the services that require the LanmanWorkstation service.</span></span>

```powershell
PS> Get-Service -Name LanmanWorkstation -DependentServices

Status   Name               DisplayName
------   ----               -----------
Running  SessionEnv         Terminal Services Configuration
Running  Netlogon           Netlogon
Stopped  Browser            Computer Browser
Running  BITS               Background Intelligent Transfer Ser...
```

<span data-ttu-id="35959-123">U kunt zelfs alle services ophalen die afhankelijkheden hebben.</span><span class="sxs-lookup"><span data-stu-id="35959-123">You can even get all services that have dependencies.</span></span> <span data-ttu-id="35959-124">De volgende opdracht is alleen dat en vervolgens wordt de cmdlet Format-Table gebruikt om de eigenschappen status, naam, RequiredServices en DependentServices van de services op de computer weer te geven.</span><span class="sxs-lookup"><span data-stu-id="35959-124">The following command does just that, and then it uses the Format-Table cmdlet to display the Status, Name, RequiredServices and DependentServices properties of the services on the computer.</span></span>

```powershell
Get-Service -Name * | Where-Object {$_.RequiredServices -or $_.DependentServices} |
  Format-Table -Property Status, Name, RequiredServices, DependentServices -auto
```

## <a name="stopping-starting-suspending-and-restarting-services"></a><span data-ttu-id="35959-125">Services stoppen, starten, onderbreken en opnieuw starten</span><span class="sxs-lookup"><span data-stu-id="35959-125">Stopping, Starting, Suspending, and Restarting Services</span></span>

<span data-ttu-id="35959-126">De service-cmdlets hebben allemaal hetzelfde algemene formulier.</span><span class="sxs-lookup"><span data-stu-id="35959-126">The Service cmdlets all have the same general form.</span></span> <span data-ttu-id="35959-127">Services kunnen worden opgegeven met een algemene naam of weergave naam en lijsten en Joker tekens worden als waarden.</span><span class="sxs-lookup"><span data-stu-id="35959-127">Services can be specified by common name or display name, and take lists and wildcards as values.</span></span> <span data-ttu-id="35959-128">Als u de afdrukspooler wilt stoppen, gebruikt u:</span><span class="sxs-lookup"><span data-stu-id="35959-128">To stop the print spooler, use:</span></span>

```powershell
Stop-Service -Name spooler
```

<span data-ttu-id="35959-129">Als u de afdrukspooler wilt starten nadat deze is gestopt, gebruikt u:</span><span class="sxs-lookup"><span data-stu-id="35959-129">To start the print spooler after it is stopped, use:</span></span>

```powershell
Start-Service -Name spooler
```

<span data-ttu-id="35959-130">Als u de afdrukspooler wilt onderbreken, gebruikt u:</span><span class="sxs-lookup"><span data-stu-id="35959-130">To suspend the print spooler, use:</span></span>

```powershell
Suspend-Service -Name spooler
```

<span data-ttu-id="35959-131">De `Restart-Service` cmdlet werkt op dezelfde manier als de andere service-cmdlets, maar er worden een aantal complexere voor beelden weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="35959-131">The `Restart-Service` cmdlet works in the same manner as the other Service cmdlets, but we will show some more complex examples for it.</span></span> <span data-ttu-id="35959-132">In het eenvoudigste gebruik geeft u de naam van de service op:</span><span class="sxs-lookup"><span data-stu-id="35959-132">In the simplest use, you specify the name of the service:</span></span>

```powershell
PS> Restart-Service -Name spooler

WARNING: Waiting for service 'Print Spooler (Spooler)' to finish starting...
WARNING: Waiting for service 'Print Spooler (Spooler)' to finish starting...
PS>
```

<span data-ttu-id="35959-133">U ziet dat er een herhaalde waarschuwing wordt weer gegeven over het starten van de afdrukspooler.</span><span class="sxs-lookup"><span data-stu-id="35959-133">You will notice that you get a repeated warning message about the Print Spooler starting up.</span></span> <span data-ttu-id="35959-134">Wanneer u een service bewerking uitvoert die enige tijd in beslag neemt, wordt u door Windows Power shell op de hoogte gesteld dat er nog steeds wordt geprobeerd om de taak uit te voeren.</span><span class="sxs-lookup"><span data-stu-id="35959-134">When you perform a service operation that takes some time, Windows PowerShell will notify you that it is still attempting to perform the task.</span></span>

<span data-ttu-id="35959-135">Als u meerdere services opnieuw wilt starten, kunt u een lijst met services ophalen, deze filteren en vervolgens het opnieuw opstarten uitvoeren:</span><span class="sxs-lookup"><span data-stu-id="35959-135">If you want to restart multiple services, you can get a list of services, filter them, and then perform the restart:</span></span>

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

<span data-ttu-id="35959-136">Deze service-cmdlets hebben geen ComputerName-para meter, maar u kunt ze uitvoeren op een externe computer met behulp van de cmdlet Invoke-Command.</span><span class="sxs-lookup"><span data-stu-id="35959-136">These Service cmdlets do not have a ComputerName parameter, but you can run them on a remote computer by using the Invoke-Command cmdlet.</span></span> <span data-ttu-id="35959-137">Met de volgende opdracht wordt bijvoorbeeld de Spooler-service opnieuw gestart op de externe computer Server01.</span><span class="sxs-lookup"><span data-stu-id="35959-137">For example, the following command restarts the Spooler service on the Server01 remote computer.</span></span>

```powershell
Invoke-Command -ComputerName Server01 {Restart-Service Spooler}
```

## <a name="setting-service-properties"></a><span data-ttu-id="35959-138">Service-eigenschappen instellen</span><span class="sxs-lookup"><span data-stu-id="35959-138">Setting Service Properties</span></span>

<span data-ttu-id="35959-139">De `Set-Service` cmdlet wijzigt de eigenschappen van een service op een lokale of externe computer.</span><span class="sxs-lookup"><span data-stu-id="35959-139">The `Set-Service` cmdlet changes the properties of a service on a local or remote computer.</span></span> <span data-ttu-id="35959-140">Omdat de status van de service een eigenschap is, kunt u deze cmdlet gebruiken om een service te starten, te stoppen en te onderbreken.</span><span class="sxs-lookup"><span data-stu-id="35959-140">Because the service status is a property, you can use this cmdlet to start, stop, and suspend a service.</span></span>
<span data-ttu-id="35959-141">De cmdlet Set-Service heeft ook een opstart type-para meter waarmee u het opstart type voor de service kunt wijzigen.</span><span class="sxs-lookup"><span data-stu-id="35959-141">The Set-Service cmdlet also has a StartupType parameter that lets you change the service startup type.</span></span>

<span data-ttu-id="35959-142">Als u wilt gebruiken `Set-Service` voor Windows Vista en latere versies van Windows, opent u Windows Power shell met de optie als administrator uitvoeren.</span><span class="sxs-lookup"><span data-stu-id="35959-142">To use `Set-Service` on Windows Vista and later versions of Windows, open Windows PowerShell with the "Run as administrator" option.</span></span>

<span data-ttu-id="35959-143">Zie [set-service](/powershell/module/Microsoft.PowerShell.Management/set-service) voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="35959-143">For more information, see [Set-Service](/powershell/module/Microsoft.PowerShell.Management/set-service)</span></span>

## <a name="see-also"></a><span data-ttu-id="35959-144">Zie ook</span><span class="sxs-lookup"><span data-stu-id="35959-144">See Also</span></span>

- [<span data-ttu-id="35959-145">Get-Service</span><span class="sxs-lookup"><span data-stu-id="35959-145">Get-Service</span></span>](/powershell/module/Microsoft.PowerShell.Management/get-service)
- [<span data-ttu-id="35959-146">Set-Service</span><span class="sxs-lookup"><span data-stu-id="35959-146">Set-Service</span></span>](/powershell/module/Microsoft.PowerShell.Management/set-service)
- [<span data-ttu-id="35959-147">Restart-Service</span><span class="sxs-lookup"><span data-stu-id="35959-147">Restart-Service</span></span>](/powershell/module/Microsoft.PowerShell.Management/restart-service)
- [<span data-ttu-id="35959-148">Suspend-Service</span><span class="sxs-lookup"><span data-stu-id="35959-148">Suspend-Service</span></span>](/powershell/module/Microsoft.PowerShell.Management/suspend-service)
