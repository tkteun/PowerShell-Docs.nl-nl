---
ms.date: 12/23/2019
keywords: Power shell, cmdlet
title: Netwerktaken uitvoeren
ms.openlocfilehash: e0aa3b8ef3d911ab0fe851f6621d70e1265c5bd4
ms.sourcegitcommit: 6545c60578f7745be015111052fd7769f8289296
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 04/22/2020
ms.locfileid: "75737199"
---
# <a name="performing-networking-tasks"></a><span data-ttu-id="55cf1-103">Netwerktaken uitvoeren</span><span class="sxs-lookup"><span data-stu-id="55cf1-103">Performing Networking Tasks</span></span>

<span data-ttu-id="55cf1-104">Omdat TCP/IP het meest gebruikte netwerk protocol is, zijn voor de meeste netwerk protocol beheer taken op laag niveau TCP/IP vereist.</span><span class="sxs-lookup"><span data-stu-id="55cf1-104">Because TCP/IP is the most commonly used network protocol, most low-level network protocol administration tasks involve TCP/IP.</span></span> <span data-ttu-id="55cf1-105">In deze sectie gebruiken we Power shell en WMI om deze taken uit te voeren.</span><span class="sxs-lookup"><span data-stu-id="55cf1-105">In this section, we use PowerShell and WMI to do these tasks.</span></span>

## <a name="listing-ip-addresses-for-a-computer"></a><span data-ttu-id="55cf1-106">IP-adressen voor een computer weer geven</span><span class="sxs-lookup"><span data-stu-id="55cf1-106">Listing IP Addresses for a Computer</span></span>

<span data-ttu-id="55cf1-107">Als u alle IP-adressen die in gebruik zijn op de lokale computer wilt ophalen, gebruikt u de volgende opdracht:</span><span class="sxs-lookup"><span data-stu-id="55cf1-107">To get all IP addresses in use on the local computer, use the following command:</span></span>

```powershell
 Get-CimInstance -Class Win32_NetworkAdapterConfiguration -Filter IPEnabled=$true |
  Select-Object -ExpandProperty IPAddress
```

<span data-ttu-id="55cf1-108">De uitvoer van deze opdracht wijkt af van de meeste eigenschappen lijsten, omdat waarden tussen accolades worden geplaatst:</span><span class="sxs-lookup"><span data-stu-id="55cf1-108">The output of this command differs from most property lists, because values are enclosed in braces:</span></span>

```Output
10.0.0.1
fe80::60ea:29a7:a233:7cb7
2601:600:a27f:a470:f532:6451:5630:ec8b
2601:600:a27f:a470:e167:477d:6c5c:342d
2601:600:a27f:a470:b021:7f0d:eab9:6299
2601:600:a27f:a470:a40e:ebce:1a8c:a2f3
2601:600:a27f:a470:613c:12a2:e0e0:bd89
2601:600:a27f:a470:444f:17ec:b463:7edd
2601:600:a27f:a470:10fd:7063:28e9:c9f3
2601:600:a27f:a470:60ea:29a7:a233:7cb7
2601:600:a27f:a470::2ec1
```

<span data-ttu-id="55cf1-109">Als u wilt weten waarom de accolades worden weer `Get-Member` gegeven, gebruikt u de cmdlet om de eigenschap **IPAddress** te controleren:</span><span class="sxs-lookup"><span data-stu-id="55cf1-109">To understand why the braces appear, use the `Get-Member` cmdlet to examine the **IPAddress** property:</span></span>

```powershell
 Get-CimInstance -Class Win32_NetworkAdapterConfiguration -Filter IPEnabled=$true |
  Get-Member -Name IPAddress
```

```Output
   TypeName: Microsoft.Management.Infrastructure.CimInstance#root/cimv2/Win32_NetworkAdapterConfiguration
Name      MemberType Definition
----      ---------- ----------
IPAddress Property   string[] IPAddress {get;}
```

<span data-ttu-id="55cf1-110">De eigenschap IPAddress voor elke netwerk adapter is in feite een matrix.</span><span class="sxs-lookup"><span data-stu-id="55cf1-110">The IPAddress property for each network adapter is actually an array.</span></span> <span data-ttu-id="55cf1-111">De accolades in de definitie geven aan dat **IPAddress** geen **System. String** -waarde, maar een matrix van **System. String** -waarden is.</span><span class="sxs-lookup"><span data-stu-id="55cf1-111">The braces in the definition indicate that **IPAddress** is not a **System.String** value, but an array of **System.String** values.</span></span>

## <a name="listing-ip-configuration-data"></a><span data-ttu-id="55cf1-112">IP-configuratie gegevens weer geven</span><span class="sxs-lookup"><span data-stu-id="55cf1-112">Listing IP Configuration Data</span></span>

<span data-ttu-id="55cf1-113">Als u gedetailleerde IP-configuratie gegevens voor elke netwerk adapter wilt weer geven, gebruikt u de volgende opdracht:</span><span class="sxs-lookup"><span data-stu-id="55cf1-113">To display detailed IP configuration data for each network adapter, use the following command:</span></span>

```powershell
Get-CimInstance -Class Win32_NetworkAdapterConfiguration -Filter IPEnabled=$true
```

<span data-ttu-id="55cf1-114">De standaard weergave voor het configuratie object voor de netwerk adapter is een zeer kleinere set beschik bare informatie.</span><span class="sxs-lookup"><span data-stu-id="55cf1-114">The default display for the network adapter configuration object is a very reduced set of the available information.</span></span> <span data-ttu-id="55cf1-115">Gebruik `Select-Object` of een opmaak-cmdlet, zoals `Format-List`, om de eigenschappen op te geven die moeten worden weer gegeven voor uitgebreide inspectie en probleem oplossing.</span><span class="sxs-lookup"><span data-stu-id="55cf1-115">For in-depth inspection and troubleshooting, use `Select-Object` or a formatting cmdlet, such as `Format-List`, to specify the properties to be displayed.</span></span>

<span data-ttu-id="55cf1-116">In moderne TCP/IP-netwerken bent u waarschijnlijk niet geïnteresseerd in IPX-of WINS-eigenschappen.</span><span class="sxs-lookup"><span data-stu-id="55cf1-116">In modern TCP/IP networks you are probably not interested in IPX or WINS properties.</span></span> <span data-ttu-id="55cf1-117">U kunt de para meter **ExcludeProperty** van `Select-Object` gebruiken om eigenschappen te verbergen met namen die beginnen met "WINS" of "IPX".</span><span class="sxs-lookup"><span data-stu-id="55cf1-117">You can use the **ExcludeProperty** parameter of `Select-Object` to hide properties with names that begin with "WINS" or "IPX".</span></span>

```powershell
Get-CimInstance -Class Win32_NetworkAdapterConfiguration -Filter IPEnabled=$true |
  Select-Object -ExcludeProperty IPX*,WINS*
```

<span data-ttu-id="55cf1-118">Met deze opdracht wordt gedetailleerde informatie geretourneerd over DHCP, DNS, route ring en andere eigenschappen van een secundaire IP-configuratie.</span><span class="sxs-lookup"><span data-stu-id="55cf1-118">This command returns detailed information about DHCP, DNS, routing, and other minor IP configuration properties.</span></span>

## <a name="pinging-computers"></a><span data-ttu-id="55cf1-119">Computers pingen</span><span class="sxs-lookup"><span data-stu-id="55cf1-119">Pinging Computers</span></span>

<span data-ttu-id="55cf1-120">U kunt een eenvoudige ping uitvoeren op een computer met behulp van **Win32_PingStatus**.</span><span class="sxs-lookup"><span data-stu-id="55cf1-120">You can perform a simple ping against a computer using by **Win32_PingStatus**.</span></span> <span data-ttu-id="55cf1-121">De volgende opdracht voert de ping uit, maar retourneert een langdurige uitvoer:</span><span class="sxs-lookup"><span data-stu-id="55cf1-121">The following command performs the ping, but returns lengthy output:</span></span>

```powershell
Get-CimInstance -Class Win32_PingStatus -Filter "Address='127.0.0.1'"
```

<span data-ttu-id="55cf1-122">Een handiger formulier voor samen vattingen geeft een weer gave van de eigenschappen Address, respons tijd en status code, zoals wordt gegenereerd door de volgende opdracht.</span><span class="sxs-lookup"><span data-stu-id="55cf1-122">A more useful form for summary information a display of the Address, ResponseTime, and StatusCode properties, as generated by the following command.</span></span> <span data-ttu-id="55cf1-123">De **Autosize** para meter AutoSize `Format-Table` van het formaat van de tabel kolommen wijzigen zodat deze correct worden weer gegeven in Power shell.</span><span class="sxs-lookup"><span data-stu-id="55cf1-123">The **Autosize** parameter of `Format-Table` resizes the table columns so that they display properly in PowerShell.</span></span>

```powershell
Get-CimInstance -Class Win32_PingStatus -Filter "Address='127.0.0.1'" |
  Format-Table -Property Address,ResponseTime,StatusCode -Autosize
```

```Output
Address   ResponseTime StatusCode
-------   ------------ ----------
127.0.0.1            0          0
```

<span data-ttu-id="55cf1-124">Een status code van 0 geeft aan dat de ping is geslaagd.</span><span class="sxs-lookup"><span data-stu-id="55cf1-124">A StatusCode of 0 indicates a successful ping.</span></span>

<span data-ttu-id="55cf1-125">U kunt een matrix gebruiken om meerdere computers te pingen met één opdracht.</span><span class="sxs-lookup"><span data-stu-id="55cf1-125">You can use an array to ping multiple computers with a single command.</span></span> <span data-ttu-id="55cf1-126">Omdat er meer dan één adres is, gebruikt u `ForEach-Object` de om elk adres afzonderlijk te pingen:</span><span class="sxs-lookup"><span data-stu-id="55cf1-126">Because there is more than one address, use the `ForEach-Object` to ping each address separately:</span></span>

```powershell
'127.0.0.1','localhost','research.microsoft.com' |
  ForEach-Object -Process {
    Get-CimInstance -Class Win32_PingStatus -Filter ("Address='$_'") |
      Select-Object -Property Address,ResponseTime,StatusCode
  }
```

<span data-ttu-id="55cf1-127">U kunt dezelfde opdracht indeling gebruiken voor het pingen van alle computers in een subnet, zoals een particulier netwerk dat gebruikmaakt van netwerk nummer 192.168.1.0 en een standaard klasse C-subnetmasker (255.255.255.0). alleen adressen in het bereik van 192.168.1.1 tot en met 192.168.1.254 zijn legitieme lokale adressen (0 is altijd gereserveerd voor het netwerk nummer en 255 is een subnet-broadcast adres).</span><span class="sxs-lookup"><span data-stu-id="55cf1-127">You can use the same command format to ping all of the computers on a subnet, such as a private network that uses network number 192.168.1.0 and a standard Class C subnet mask (255.255.255.0)., Only addresses in the range of 192.168.1.1 through 192.168.1.254 are legitimate local addresses (0 is always reserved for the network number and 255 is a subnet broadcast address).</span></span>

<span data-ttu-id="55cf1-128">Als u een matrix van de getallen 1 tot en met 254 in Power shell wilt weer geven, gebruikt u de instructie **1.. 254.**</span><span class="sxs-lookup"><span data-stu-id="55cf1-128">To represent an array of the numbers from 1 through 254 in PowerShell, use the statement **1..254.**</span></span>
<span data-ttu-id="55cf1-129">Een volledige ping van het subnet kan worden uitgevoerd door de matrix te genereren en vervolgens de waarden toe te voegen aan een gedeeltelijk adres in de instructie ping:</span><span class="sxs-lookup"><span data-stu-id="55cf1-129">A complete subnet ping can be performed by generating the array and then adding the values onto a partial address in the ping statement:</span></span>

```powershell
1..254| ForEach-Object -Process {
  Get-CimInstance -Class Win32_PingStatus -Filter ("Address='192.168.1.$_ '") } |
    Select-Object -Property Address,ResponseTime,StatusCode
```

<span data-ttu-id="55cf1-130">Houd er rekening mee dat deze techniek voor het genereren van een bereik van adressen ook elders kan worden gebruikt.</span><span class="sxs-lookup"><span data-stu-id="55cf1-130">Note that this technique for generating a range of addresses can be used elsewhere as well.</span></span> <span data-ttu-id="55cf1-131">Op deze manier kunt u een volledige set adressen genereren:</span><span class="sxs-lookup"><span data-stu-id="55cf1-131">You can generate a complete set of addresses in this way:</span></span>

```powershell
$ips = 1..254 | ForEach-Object -Process {'192.168.1.' + $_}
```

## <a name="retrieving-network-adapter-properties"></a><span data-ttu-id="55cf1-132">Eigenschappen van de netwerk adapter ophalen</span><span class="sxs-lookup"><span data-stu-id="55cf1-132">Retrieving Network Adapter Properties</span></span>

<span data-ttu-id="55cf1-133">Eerder werd geadviseerd dat u de algemene configuratie-eigenschappen kunt ophalen met behulp van de **Win32_NetworkAdapterConfiguration** -klasse.</span><span class="sxs-lookup"><span data-stu-id="55cf1-133">Earlier, we mentioned that you could retrieve general configuration properties using the **Win32_NetworkAdapterConfiguration** class.</span></span> <span data-ttu-id="55cf1-134">Hoewel dit geen strikte TCP/IP-informatie is, kunnen gegevens van netwerk adapters, zoals MAC-adressen en adapter typen, handig zijn om te zien wat er gebeurt met een computer.</span><span class="sxs-lookup"><span data-stu-id="55cf1-134">Although not strictly TCP/IP information, network adapter information such as MAC addresses and adapter types can be useful for understanding what is going on with a computer.</span></span> <span data-ttu-id="55cf1-135">Gebruik de volgende opdracht om een overzicht van deze informatie te krijgen:</span><span class="sxs-lookup"><span data-stu-id="55cf1-135">To get a summary of this information, use the following command:</span></span>

```powershell
Get-CimInstance -Class Win32_NetworkAdapter -ComputerName .
```

## <a name="assigning-the-dns-domain-for-a-network-adapter"></a><span data-ttu-id="55cf1-136">Toewijzing van het DNS-domein voor een netwerk adapter</span><span class="sxs-lookup"><span data-stu-id="55cf1-136">Assigning the DNS Domain for a Network Adapter</span></span>

<span data-ttu-id="55cf1-137">Als u het DNS-domein voor automatische naam omzetting wilt toewijzen, gebruikt u de methode **SetDNSDomain** van de **Win32_NetworkAdapterConfiguration**.</span><span class="sxs-lookup"><span data-stu-id="55cf1-137">To assign the DNS domain for automatic name resolution, use the **SetDNSDomain** method of the **Win32_NetworkAdapterConfiguration**.</span></span> <span data-ttu-id="55cf1-138">Omdat u het DNS-domein voor elke configuratie van de netwerk adapter afzonderlijk toewijst, `ForEach-Object` moet u een instructie gebruiken om het domein toe te wijzen aan elke adapter:</span><span class="sxs-lookup"><span data-stu-id="55cf1-138">Because you assign the DNS domain for each network adapter configuration independently, you need to use a `ForEach-Object` statement to assign the domain to each adapter:</span></span>

```powershell
Get-CimInstance -Class Win32_NetworkAdapterConfiguration -Filter IPEnabled=$true |
  ForEach-Object -Process { $_.SetDNSDomain('fabrikam.com') }
```

<span data-ttu-id="55cf1-139">De filter instructie `IPEnabled=$true` is nodig, omdat zelfs in een netwerk dat alleen TCP/IP gebruikt, een aantal netwerk adapter configuraties op een computer niet waar TCP/IP-adapters zijn. Dit zijn algemene software-elementen die RAS-, PPTP-, QoS-en andere services ondersteunen voor alle adapters, en dus geen eigen adres hebben.</span><span class="sxs-lookup"><span data-stu-id="55cf1-139">The filtering statement `IPEnabled=$true` is necessary, because even on a network that uses only TCP/IP, several of the network adapter configurations on a computer are not true TCP/IP adapters; they are general software elements supporting RAS, PPTP, QoS, and other services for all adapters and thus do not have an address of their own.</span></span>

<span data-ttu-id="55cf1-140">U kunt de opdracht filteren met behulp `Where-Object` van de-cmdlet, in `Get-CimInstance` plaats van het filter te gebruiken.</span><span class="sxs-lookup"><span data-stu-id="55cf1-140">You can filter the command by using the `Where-Object` cmdlet, instead of using the `Get-CimInstance` filter.</span></span>

```powershell
Get-CimInstance -Class Win32_NetworkAdapterConfiguration |
  Where-Object {$_.IPEnabled} |
    ForEach-Object -Process {$_.SetDNSDomain('fabrikam.com')}
```

## <a name="performing-dhcp-configuration-tasks"></a><span data-ttu-id="55cf1-141">DHCP-configuratie taken uitvoeren</span><span class="sxs-lookup"><span data-stu-id="55cf1-141">Performing DHCP Configuration Tasks</span></span>

<span data-ttu-id="55cf1-142">Bij het wijzigen van DHCP-details moet u werken met een set netwerk adapters, net zoals de DNS-configuratie.</span><span class="sxs-lookup"><span data-stu-id="55cf1-142">Modifying DHCP details involves working with a set of network adapters, just as the DNS configuration does.</span></span> <span data-ttu-id="55cf1-143">Er zijn verschillende acties die u kunt uitvoeren met behulp van WMI, en we gaan door een aantal van de gemeen schappelijke stappen.</span><span class="sxs-lookup"><span data-stu-id="55cf1-143">There are several distinct actions you can perform by using WMI, and we will step through a few of the common ones.</span></span>

### <a name="determining-dhcp-enabled-adapters"></a><span data-ttu-id="55cf1-144">Adapters voor DHCP-ondersteuning bepalen</span><span class="sxs-lookup"><span data-stu-id="55cf1-144">Determining DHCP-Enabled Adapters</span></span>

<span data-ttu-id="55cf1-145">Als u de DHCP-adapters op een computer wilt zoeken, gebruikt u de volgende opdracht:</span><span class="sxs-lookup"><span data-stu-id="55cf1-145">To find the DHCP-enabled adapters on a computer, use the following command:</span></span>

```powershell
Get-CimInstance -Class Win32_NetworkAdapterConfiguration -Filter "DHCPEnabled=$true"
```

<span data-ttu-id="55cf1-146">Als u adapters wilt uitsluiten met IP-configuratie problemen, kunt u alleen adapters met IP-functionaliteit ophalen:</span><span class="sxs-lookup"><span data-stu-id="55cf1-146">To exclude adapters with IP configuration problems, you can retrieve only IP-enabled adapters:</span></span>

```powershell
Get-CimInstance -Class Win32_NetworkAdapterConfiguration -Filter "IPEnabled=$true and DHCPEnabled=$true"
```

### <a name="retrieving-dhcp-properties"></a><span data-ttu-id="55cf1-147">DHCP-eigenschappen ophalen</span><span class="sxs-lookup"><span data-stu-id="55cf1-147">Retrieving DHCP Properties</span></span>

<span data-ttu-id="55cf1-148">Omdat aan DHCP gerelateerde eigenschappen voor een adapter doorgaans beginnen met `DHCP`, kunt u de eigenschaps parameter van `Format-Table` gebruiken om alleen die eigenschappen weer te geven:</span><span class="sxs-lookup"><span data-stu-id="55cf1-148">Because DHCP-related properties for an adapter generally begin with `DHCP`, you can use the Property parameter of `Format-Table` to display only those properties:</span></span>

```powershell
Get-CimInstance -Class Win32_NetworkAdapterConfiguration -Filter "DHCPEnabled=$true" |
  Format-Table -Property DHCP*
```

### <a name="enabling-dhcp-on-each-adapter"></a><span data-ttu-id="55cf1-149">DHCP inschakelen op elke adapter</span><span class="sxs-lookup"><span data-stu-id="55cf1-149">Enabling DHCP on Each Adapter</span></span>

<span data-ttu-id="55cf1-150">Als u DHCP op alle adapters wilt inschakelen, gebruikt u de volgende opdracht:</span><span class="sxs-lookup"><span data-stu-id="55cf1-150">To enable DHCP on all adapters, use the following command:</span></span>

```powershell
Get-CimInstance -Class Win32_NetworkAdapterConfiguration -Filter IPEnabled=$true |
  ForEach-Object -Process {$_.EnableDHCP()}
```

<span data-ttu-id="55cf1-151">U kunt de **filter** -instructie `IPEnabled=$true and DHCPEnabled=$false` gebruiken om te voor komen dat DHCP wordt ingeschakeld, maar als deze stap wordt wegge laten, worden er geen fouten veroorzaakt.</span><span class="sxs-lookup"><span data-stu-id="55cf1-151">You can use the **Filter** statement `IPEnabled=$true and DHCPEnabled=$false` to avoid enabling DHCP where it is already enabled, but omitting this step will not cause errors.</span></span>

### <a name="releasing-and-renewing-dhcp-leases-on-specific-adapters"></a><span data-ttu-id="55cf1-152">DHCP-leases op specifieke adapters vrijgeven en vernieuwen</span><span class="sxs-lookup"><span data-stu-id="55cf1-152">Releasing and Renewing DHCP Leases on Specific Adapters</span></span>

<span data-ttu-id="55cf1-153">De klasse **Win32_NetworkAdapterConfiguration** heeft **ReleaseDHCPLease** -en **RenewDHCPLease** -methoden.</span><span class="sxs-lookup"><span data-stu-id="55cf1-153">The **Win32_NetworkAdapterConfiguration** class has **ReleaseDHCPLease** and **RenewDHCPLease** methods.</span></span> <span data-ttu-id="55cf1-154">Beide worden op dezelfde manier gebruikt.</span><span class="sxs-lookup"><span data-stu-id="55cf1-154">Both are used in the same way.</span></span> <span data-ttu-id="55cf1-155">In het algemeen gebruikt u deze methoden als u alleen adressen voor een adapter op een specifiek subnet hoeft vrij te geven of te vernieuwen.</span><span class="sxs-lookup"><span data-stu-id="55cf1-155">In general, use these methods if you only need to release or renew addresses for an adapter on a specific subnet.</span></span> <span data-ttu-id="55cf1-156">De eenvoudigste manier om adapters op een subnet te filteren, is door alleen de adapter configuraties te kiezen die gebruikmaken van de gateway voor dat subnet.</span><span class="sxs-lookup"><span data-stu-id="55cf1-156">The easiest way to filter adapters on a subnet is to choose only the adapter configurations that use the gateway for that subnet.</span></span> <span data-ttu-id="55cf1-157">Met de volgende opdracht worden bijvoorbeeld alle DHCP-leases vrijgegeven op adapters op de lokale computer die DHCP-leases verkrijgen van 192.168.1.254:</span><span class="sxs-lookup"><span data-stu-id="55cf1-157">For example, the following command releases all DHCP leases on adapters on the local computer that are obtaining DHCP leases from 192.168.1.254:</span></span>

```powershell
Get-CimInstance -Class Win32_NetworkAdapterConfiguration -Filter "IPEnabled=$true and DHCPEnabled=$true" |
  Where-Object {$_.DHCPServer -contains '192.168.1.254'} |
    ForEach-Object -Process {$_.ReleaseDHCPLease()}
```

<span data-ttu-id="55cf1-158">De enige wijziging voor het vernieuwen van een DHCP-lease is het gebruik van de methode **RenewDHCPLease** in plaats van de methode **ReleaseDHCPLease** :</span><span class="sxs-lookup"><span data-stu-id="55cf1-158">The only change for renewing a DHCP lease is to use the **RenewDHCPLease** method instead of the **ReleaseDHCPLease** method:</span></span>

```powershell
Get-CimInstance -Class Win32_NetworkAdapterConfiguration -Filter "IPEnabled=$true and DHCPEnabled=$true" |
  Where-Object {$_.DHCPServer -contains '192.168.1.254'} |
    ForEach-Object -Process {$_.ReleaseDHCPLease()}
```

> [!NOTE]
> <span data-ttu-id="55cf1-159">Wanneer u deze methoden op een externe computer gebruikt, moet u er rekening mee houden dat u de toegang tot het externe systeem kunt verliezen als u er met de adapter met de uitgebrachte of verlengde lease mee verbonden bent.</span><span class="sxs-lookup"><span data-stu-id="55cf1-159">When using these methods on a remote computer, be aware that you can lose access to the remote system if you are connected to it through the adapter with the released or renewed lease.</span></span>

### <a name="releasing-and-renewing-dhcp-leases-on-all-adapters"></a><span data-ttu-id="55cf1-160">DHCP-leases op alle adapters vrijgeven en vernieuwen</span><span class="sxs-lookup"><span data-stu-id="55cf1-160">Releasing and Renewing DHCP Leases on All Adapters</span></span>

<span data-ttu-id="55cf1-161">U kunt algemene DHCP-adres releases of-vernieuwingen uitvoeren op alle adapters met behulp van de **Win32_NetworkAdapterConfiguration** methoden **ReleaseDHCPLeaseAll** en **RenewDHCPLeaseAll**.</span><span class="sxs-lookup"><span data-stu-id="55cf1-161">You can perform global DHCP address releases or renewals on all adapters by using the **Win32_NetworkAdapterConfiguration** methods, **ReleaseDHCPLeaseAll** and **RenewDHCPLeaseAll**.</span></span>
<span data-ttu-id="55cf1-162">De opdracht moet echter wel van toepassing zijn op de WMI-klasse in plaats van een bepaalde adapter, omdat leases die wereld wijd worden vrijgegeven en vernieuwen, worden uitgevoerd op de klasse, niet op een specifieke adapter.</span><span class="sxs-lookup"><span data-stu-id="55cf1-162">However, the command must apply to the WMI class, rather than a particular adapter, because releasing and renewing leases globally is performed on the class, not on a specific adapter.</span></span>

<span data-ttu-id="55cf1-163">U kunt een verwijzing naar een WMI-klasse verkrijgen in plaats van klasse-instanties door alle WMI-klassen weer te geven en vervolgens alleen de gewenste klasse op naam te selecteren.</span><span class="sxs-lookup"><span data-stu-id="55cf1-163">You can get a reference to a WMI class, instead of class instances, by listing all WMI classes and then selecting only the desired class by name.</span></span> <span data-ttu-id="55cf1-164">Met de volgende opdracht wordt bijvoorbeeld de **Win32_NetworkAdapterConfiguration** -klasse geretourneerd:</span><span class="sxs-lookup"><span data-stu-id="55cf1-164">For example, the following command returns the **Win32_NetworkAdapterConfiguration** class:</span></span>

```powershell
Get-CimInstance -List | Where-Object {$_.Name -eq 'Win32_NetworkAdapterConfiguration'}
```

<span data-ttu-id="55cf1-165">U kunt de volledige opdracht beschouwen als de klasse en vervolgens de **ReleaseDHCPAdapterLease** -methode aanroepen.</span><span class="sxs-lookup"><span data-stu-id="55cf1-165">You can treat the entire command as the class and then invoke the **ReleaseDHCPAdapterLease** method on it.</span></span> <span data-ttu-id="55cf1-166">In de volgende opdracht worden de haakjes rondom de `Get-CimInstance` en `Where-Object` pijplijn elementen direct Power shell uitgevoerd om ze eerst te evalueren:</span><span class="sxs-lookup"><span data-stu-id="55cf1-166">In the following command, the parentheses surrounding the `Get-CimInstance` and `Where-Object` pipeline elements direct PowerShell to evaluate them first:</span></span>

```powershell
(Get-CimInstance -List |
  Where-Object {$_.Name -eq 'Win32_NetworkAdapterConfiguration'}).ReleaseDHCPLeaseAll()
```

<span data-ttu-id="55cf1-167">U kunt dezelfde opdracht indeling gebruiken om de **RenewDHCPLeaseAll** -methode aan te roepen:</span><span class="sxs-lookup"><span data-stu-id="55cf1-167">You can use the same command format to invoke the **RenewDHCPLeaseAll** method:</span></span>

```powershell
(Get-CimInstance -List |
  Where-Object {$_.Name -eq 'Win32_NetworkAdapterConfiguration'}).RenewDHCPLeaseAll()
```

## <a name="creating-a-network-share"></a><span data-ttu-id="55cf1-168">Een netwerk share maken</span><span class="sxs-lookup"><span data-stu-id="55cf1-168">Creating a Network Share</span></span>

<span data-ttu-id="55cf1-169">Als u een netwerk share wilt maken, gebruikt u de methode **Create** van **Win32_Share**:</span><span class="sxs-lookup"><span data-stu-id="55cf1-169">To create a network share, use the **Create** method of **Win32_Share**:</span></span>

```powershell
(Get-CimInstance -List |
  Where-Object {$_.Name -eq 'Win32_Share'}).Create(
    'C:\temp','TempShare',0,25,'test share of the temp folder'
  )
```

<span data-ttu-id="55cf1-170">U kunt de share ook maken met behulp `net share` van in Power shell in Windows:</span><span class="sxs-lookup"><span data-stu-id="55cf1-170">You can also create the share by using `net share` in PowerShell on Windows:</span></span>

```powershell
net share tempshare=c:\temp /users:25 /remark:"test share of the temp folder"
```

## <a name="removing-a-network-share"></a><span data-ttu-id="55cf1-171">Een netwerk share verwijderen</span><span class="sxs-lookup"><span data-stu-id="55cf1-171">Removing a Network Share</span></span>

<span data-ttu-id="55cf1-172">U kunt een netwerk share met **Win32_Share**verwijderen, maar het proces wijkt enigszins af van het maken van een share, omdat u de specifieke share moet ophalen die moet worden verwijderd, in plaats van de **Win32_Share** klasse.</span><span class="sxs-lookup"><span data-stu-id="55cf1-172">You can remove a network share with **Win32_Share**, but the process is slightly different from creating a share, because you need to retrieve the specific share to be removed, rather than the **Win32_Share** class.</span></span> <span data-ttu-id="55cf1-173">Met de volgende instructie wordt de share **TempShare**verwijderd:</span><span class="sxs-lookup"><span data-stu-id="55cf1-173">The following statement deletes the share **TempShare**:</span></span>

```powershell
(Get-CimInstance -Class Win32_Share -Filter "Name='TempShare'").Delete()
```

<span data-ttu-id="55cf1-174">In Windows `net share` werkt ook het volgende:</span><span class="sxs-lookup"><span data-stu-id="55cf1-174">In Windows, `net share` works as well:</span></span>

```powershell
net share tempshare /delete
```

```Output
tempshare was deleted successfully.
```

## <a name="connecting-a-windows-accessible-network-drive"></a><span data-ttu-id="55cf1-175">Verbinding maken met een met Windows toegankelijk netwerk station</span><span class="sxs-lookup"><span data-stu-id="55cf1-175">Connecting a Windows Accessible Network Drive</span></span>

<span data-ttu-id="55cf1-176">De `New-PSDrive` cmdlets maken een Power Shell-station, maar stations die op deze manier zijn gemaakt, zijn alleen beschikbaar voor Power shell.</span><span class="sxs-lookup"><span data-stu-id="55cf1-176">The `New-PSDrive` cmdlets creates a PowerShell drive, but drives created this way are available only to PowerShell.</span></span> <span data-ttu-id="55cf1-177">Als u een nieuw netwerk station wilt maken, kunt u het object **WScript. Network** com gebruiken.</span><span class="sxs-lookup"><span data-stu-id="55cf1-177">To create a new networked drive, you can use the **WScript.Network** COM object.</span></span> <span data-ttu-id="55cf1-178">Met de volgende opdracht wordt de `\\FPS01\users` share toegewezen aan `B:`een lokaal station,</span><span class="sxs-lookup"><span data-stu-id="55cf1-178">The following command maps the share `\\FPS01\users` to local drive `B:`,</span></span>

```powershell
(New-Object -ComObject WScript.Network).MapNetworkDrive('B:', '\\FPS01\users')
```

<span data-ttu-id="55cf1-179">In Windows werkt de `net use` opdracht ook als volgt:</span><span class="sxs-lookup"><span data-stu-id="55cf1-179">On Windows, the `net use` command works as well:</span></span>

```powershell
net use B: \\FPS01\users
```

<span data-ttu-id="55cf1-180">Stations die zijn toegewezen met **WScript. Network** of `net use` die onmiddellijk beschikbaar zijn voor Power shell.</span><span class="sxs-lookup"><span data-stu-id="55cf1-180">Drives mapped with either **WScript.Network** or `net use` are immediately available to PowerShell.</span></span>
