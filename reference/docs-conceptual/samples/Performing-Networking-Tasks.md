---
ms.date: 06/05/2017
keywords: PowerShell-cmdlet
title: Netwerktaken uitvoeren
ms.assetid: a43cc55f-70c1-45c8-9467-eaad0d57e3b5
ms.openlocfilehash: 64c57c95a70bc4cad4b695a59d96673ed18afdf4
ms.sourcegitcommit: 00ff76d7d9414fe585c04740b739b9cf14d711e1
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 12/14/2018
ms.locfileid: "53404585"
---
# <a name="performing-networking-tasks"></a><span data-ttu-id="e2ed5-103">Netwerktaken uitvoeren</span><span class="sxs-lookup"><span data-stu-id="e2ed5-103">Performing Networking Tasks</span></span>

<span data-ttu-id="e2ed5-104">Omdat TCP/IP het meest gebruikte protocol is, worden de meeste beheertaken van laag niveau netwerk-protocol TCP/IP.</span><span class="sxs-lookup"><span data-stu-id="e2ed5-104">Because TCP/IP is the most commonly used network protocol, most low-level network protocol administration tasks involve TCP/IP.</span></span> <span data-ttu-id="e2ed5-105">In deze sectie gebruiken we Windows PowerShell en WMI voor deze taken.</span><span class="sxs-lookup"><span data-stu-id="e2ed5-105">In this section, we use Windows PowerShell and WMI to do these tasks.</span></span>

### <a name="listing-ip-addresses-for-a-computer"></a><span data-ttu-id="e2ed5-106">IP-adressen weergeven voor een Computer</span><span class="sxs-lookup"><span data-stu-id="e2ed5-106">Listing IP Addresses for a Computer</span></span>

<span data-ttu-id="e2ed5-107">Als u alle IP-adressen in gebruik is op de lokale computer, gebruikt u de volgende opdracht uit:</span><span class="sxs-lookup"><span data-stu-id="e2ed5-107">To get all IP addresses in use on the local computer, use the following command:</span></span>

```powershell
Get-WmiObject -Class Win32_NetworkAdapterConfiguration -Filter IPEnabled=$true -ComputerName . | Format-Table -Property IPAddress
```

<span data-ttu-id="e2ed5-108">De uitvoer van deze opdracht wijkt af van de meeste lijsten met zoekeigenschappen omdat waarden zijn tussen accolades:</span><span class="sxs-lookup"><span data-stu-id="e2ed5-108">The output of this command differs from most property lists, because values are enclosed in braces:</span></span>

```output
IPAddress
---------
{192.168.1.80}
{192.168.148.1}
{192.168.171.1}
{0.0.0.0}
```

<span data-ttu-id="e2ed5-109">Om te begrijpen waarom de accolades worden weergegeven, gebruikt u de cmdlet Get-Member het onderzoeken van de **IPAddress** eigenschap:</span><span class="sxs-lookup"><span data-stu-id="e2ed5-109">To understand why the braces appear, use the Get-Member cmdlet to examine the **IPAddress** property:</span></span>

```
PS> Get-WmiObject -Class Win32_NetworkAdapterConfiguration -Filter IPEnabled=$true -ComputerName . | Get-Member -Name IPAddress


TypeName: System.Management.ManagementObject#root\cimv2\Win32_NetworkAdapterConfiguration

Name      MemberType Definition
----      ---------- ----------
IPAddress Property   System.String[] IPAddress {get;}
```

<span data-ttu-id="e2ed5-110">De eigenschap IP-adres voor elke netwerkadapter is eigenlijk een matrix.</span><span class="sxs-lookup"><span data-stu-id="e2ed5-110">The IPAddress property for each network adapter is actually an array.</span></span> <span data-ttu-id="e2ed5-111">De accolades in het definitie geven aan dat **IPAddress** is niet een **System.String** waarde, maar een matrix met **System.String** waarden.</span><span class="sxs-lookup"><span data-stu-id="e2ed5-111">The braces in the definition indicate that **IPAddress** is not a **System.String** value, but an array of **System.String** values.</span></span>

### <a name="listing-ip-configuration-data"></a><span data-ttu-id="e2ed5-112">IP-configuratiegegevens van aanbieding</span><span class="sxs-lookup"><span data-stu-id="e2ed5-112">Listing IP Configuration Data</span></span>

<span data-ttu-id="e2ed5-113">Als gedetailleerde IP-configuratiegegevens voor elke netwerkadapter weergeven, gebruikt u de volgende opdracht uit:</span><span class="sxs-lookup"><span data-stu-id="e2ed5-113">To display detailed IP configuration data for each network adapter, use the following command:</span></span>

```powershell
Get-WmiObject -Class Win32_NetworkAdapterConfiguration -Filter IPEnabled=$true -ComputerName .
```

<span data-ttu-id="e2ed5-114">De standaardweergave voor het object network adapter configuratie is een zeer beperkte set van de beschikbare informatie.</span><span class="sxs-lookup"><span data-stu-id="e2ed5-114">The default display for the network adapter configuration object is a very reduced set of the available information.</span></span> <span data-ttu-id="e2ed5-115">Gebruik voor uitgebreide controle en probleemoplossing, Select-Object of een opmaak cmdlet, zoals indeling-lijst om op te geven van de eigenschappen die moeten worden weergegeven.</span><span class="sxs-lookup"><span data-stu-id="e2ed5-115">For in-depth inspection and troubleshooting, use Select-Object or a formatting cmdlet, such as Format-List, to specify the properties to be displayed.</span></span>

<span data-ttu-id="e2ed5-116">Als u niet geïnteresseerd in de eigenschappen van IPX- of WINS bent, waarschijnlijk het geval in een moderne TCP/IP-netwerk, kunt u de parameter ExcludeProperty van Select-Object te verbergen eigenschappen met namen die met "WINS beginnen" of "IPX:"</span><span class="sxs-lookup"><span data-stu-id="e2ed5-116">If you are not interested in IPX or WINS properties—probably the case in a modern TCP/IP network—you can use the ExcludeProperty parameter of Select-Object to hide properties with names that begin with "WINS" or "IPX:"</span></span>

```powershell
Get-WmiObject -Class Win32_NetworkAdapterConfiguration -Filter IPEnabled=$true -ComputerName . | Select-Object -Property [a-z]* -ExcludeProperty IPX*,WINS*
```

<span data-ttu-id="e2ed5-117">Met deze opdracht retourneert gedetailleerde informatie over DHCP, DNS, Routering en andere secundaire IP-configuratie-eigenschappen.</span><span class="sxs-lookup"><span data-stu-id="e2ed5-117">This command returns detailed information about DHCP, DNS, routing, and other minor IP configuration properties.</span></span>

### <a name="pinging-computers"></a><span data-ttu-id="e2ed5-118">Pingen naar Computers</span><span class="sxs-lookup"><span data-stu-id="e2ed5-118">Pinging Computers</span></span>

<span data-ttu-id="e2ed5-119">U kunt een eenvoudige ping uit voor een computer met behulp van uitvoeren **Win32_PingStatus**.</span><span class="sxs-lookup"><span data-stu-id="e2ed5-119">You can perform a simple ping against a computer using by **Win32_PingStatus**.</span></span> <span data-ttu-id="e2ed5-120">De volgende opdracht de opdracht ping wordt uitgevoerd, maar retourneert uitgebreide uitvoer:</span><span class="sxs-lookup"><span data-stu-id="e2ed5-120">The following command performs the ping, but returns lengthy output:</span></span>

```powershell
Get-WmiObject -Class Win32_PingStatus -Filter "Address='127.0.0.1'" -ComputerName .
```

<span data-ttu-id="e2ed5-121">Nog meer nuttige formulier samenvattende informatie weergegeven in een van de eigenschappen van het adres, de responstijd en de StatusCode, zoals die worden gegenereerd door de volgende opdracht uit.</span><span class="sxs-lookup"><span data-stu-id="e2ed5-121">A more useful form for summary information a display of the Address, ResponseTime, and StatusCode properties, as generated by the following command.</span></span> <span data-ttu-id="e2ed5-122">De parameter Autosize van Format-Table vergroot/verkleint de kolommen in de tabel zodat ze goed worden weergegeven in Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="e2ed5-122">The Autosize parameter of Format-Table resizes the table columns so that they display properly in Windows PowerShell.</span></span>

```
PS> Get-WmiObject -Class Win32_PingStatus -Filter "Address='127.0.0.1'" -ComputerName . | Format-Table -Property Address,ResponseTime,StatusCode -Autosize

Address   ResponseTime StatusCode
-------   ------------ ----------
127.0.0.1            0          0
```

<span data-ttu-id="e2ed5-123">Een StatusCode van 0 geeft aan dat een geslaagde ping.</span><span class="sxs-lookup"><span data-stu-id="e2ed5-123">A StatusCode of 0 indicates a successful ping.</span></span>

<span data-ttu-id="e2ed5-124">Een matrix kunt u meerdere computers met slechts één opdracht ping.</span><span class="sxs-lookup"><span data-stu-id="e2ed5-124">You can use an array to ping multiple computers with a single command.</span></span> <span data-ttu-id="e2ed5-125">Omdat er meer dan één adres, gebruiken de **ForEach-Object** afzonderlijk pingt u elk adres:</span><span class="sxs-lookup"><span data-stu-id="e2ed5-125">Because there is more than one address, use the **ForEach-Object** to ping each address separately:</span></span>

```powershell
'127.0.0.1','localhost','research.microsoft.com' | ForEach-Object -Process {Get-WmiObject -Class Win32_PingStatus -Filter ("Address='" + $_ + "'") -ComputerName .} | Select-Object -Property Address,ResponseTime,StatusCode
```

<span data-ttu-id="e2ed5-126">U kunt de opdrachtindeling van dezelfde gebruiken om te pingen alle computers in een subnet, zoals een particulier netwerk die gebruikmaakt van nummer 192.168.1.0 van het netwerk en een standaard-klasse C-subnetmasker (255.255.255.0)., worden alleen de adressen binnen het bereik van 192.168.1.1 via 192.168.1.254 goedaardige lokale adressen (0 is altijd gereserveerd voor het nummer van het netwerk en 255 is een subnet broadcast-adres).</span><span class="sxs-lookup"><span data-stu-id="e2ed5-126">You can use the same command format to ping all of the computers on a subnet, such as a private network that uses network number 192.168.1.0 and a standard Class C subnet mask (255.255.255.0)., Only addresses in the range of 192.168.1.1 through 192.168.1.254 are legitimate local addresses (0 is always reserved for the network number and 255 is a subnet broadcast address).</span></span>

<span data-ttu-id="e2ed5-127">Om weer te geven een matrix van de getallen van 1 tot 254 in Windows PowerShell, gebruikt u de instructie **1..254.**</span><span class="sxs-lookup"><span data-stu-id="e2ed5-127">To represent an array of the numbers from 1 through 254 in Windows PowerShell, use the statement **1..254.**</span></span> <span data-ttu-id="e2ed5-128">Een ping voltooid subnet kan worden uitgevoerd door het genereren van de matrix en vervolgens de waarden naar een gedeeltelijke adres toe te voegen in de ping-instructie:</span><span class="sxs-lookup"><span data-stu-id="e2ed5-128">A complete subnet ping can be performed by generating the array and then adding the values onto a partial address in the ping statement:</span></span>

```powershell
1..254| ForEach-Object -Process {Get-WmiObject -Class Win32_PingStatus -Filter ("Address='192.168.1." + $_ + "'") -ComputerName .} | Select-Object -Property Address,ResponseTime,StatusCode
```

<span data-ttu-id="e2ed5-129">Houd er rekening mee dat deze techniek voor het genereren van een bereik van adressen elders kan worden gebruikt.</span><span class="sxs-lookup"><span data-stu-id="e2ed5-129">Note that this technique for generating a range of addresses can be used elsewhere as well.</span></span> <span data-ttu-id="e2ed5-130">Op deze manier kunt u een volledige set adressen genereren:</span><span class="sxs-lookup"><span data-stu-id="e2ed5-130">You can generate a complete set of addresses in this way:</span></span>

```powershell
$ips = 1..254 | ForEach-Object -Process {'192.168.1.' + $_}
```

### <a name="retrieving-network-adapter-properties"></a><span data-ttu-id="e2ed5-131">Bij het ophalen van eigenschappen van netwerkadapter</span><span class="sxs-lookup"><span data-stu-id="e2ed5-131">Retrieving Network Adapter Properties</span></span>

<span data-ttu-id="e2ed5-132">Eerder in deze handleiding, hebben we al gemeld dat u algemene configuratie-eigenschappen ophalen met behulp van kan **Win32_NetworkAdapterConfiguration**.</span><span class="sxs-lookup"><span data-stu-id="e2ed5-132">Earlier in this user's guide, we mentioned that you could retrieve general configuration properties by using **Win32_NetworkAdapterConfiguration**.</span></span> <span data-ttu-id="e2ed5-133">Hoewel dit strikt genomen TCP/IP-informatie, netwerkadapterinformatie, zoals MAC-adressen en typen netwerkadapters kunnen nuttig zijn om te begrijpen wat er gebeurt met een computer zijn.</span><span class="sxs-lookup"><span data-stu-id="e2ed5-133">Although not strictly TCP/IP information, network adapter information such as MAC addresses and adapter types can be useful for understanding what is going on with a computer.</span></span> <span data-ttu-id="e2ed5-134">Als u een overzicht van deze informatie, gebruikt u de volgende opdracht uit:</span><span class="sxs-lookup"><span data-stu-id="e2ed5-134">To get a summary of this information, use the following command:</span></span>

```powershell
Get-WmiObject -Class Win32_NetworkAdapter -ComputerName .
```

### <a name="assigning-the-dns-domain-for-a-network-adapter"></a><span data-ttu-id="e2ed5-135">De DNS-domein toewijzen voor een netwerkadapter</span><span class="sxs-lookup"><span data-stu-id="e2ed5-135">Assigning the DNS Domain for a Network Adapter</span></span>

<span data-ttu-id="e2ed5-136">Als u wilt toewijzen van de DNS-domein voor het omzetten van automatische, gebruikt u de **Win32_NetworkAdapterConfiguration SetDNSDomain** methode.</span><span class="sxs-lookup"><span data-stu-id="e2ed5-136">To assign the DNS domain for automatic name resolution, use the **Win32_NetworkAdapterConfiguration SetDNSDomain** method.</span></span> <span data-ttu-id="e2ed5-137">Omdat u de DNS-domein voor de configuratie van elke netwerkadapter afzonderlijk toewijst, moet u een **ForEach-Object** instructie het domein toewijzen aan elke adapter:</span><span class="sxs-lookup"><span data-stu-id="e2ed5-137">Because you assign the DNS domain for each network adapter configuration independently, you need to use a **ForEach-Object** statement to assign the domain to each adapter:</span></span>

```powershell
Get-WmiObject -Class Win32_NetworkAdapterConfiguration -Filter IPEnabled=$true -ComputerName . | ForEach-Object -Process { $_. SetDNSDomain('fabrikam.com') }
```

<span data-ttu-id="e2ed5-138">De instructie filteren ' IPEnabled $true = "is nodig omdat zelfs op een netwerk dat gebruikmaakt van alleen TCP/IP, verschillende configuraties van de netwerkadapters op een computer niet TCP/IP-adapters, ' True '; Deze algemene software-elementen ter ondersteuning van RAS, PPTP, QoS en andere services voor alle adapters zijn en dus niet een adres van hun eigen over.</span><span class="sxs-lookup"><span data-stu-id="e2ed5-138">The filtering statement "IPEnabled=$true" is necessary, because even on a network that uses only TCP/IP, several of the network adapter configurations on a computer are not true TCP/IP adapters; they are general software elements supporting RAS, PPTP, QoS, and other services for all adapters and thus do not have an address of their own.</span></span>

<span data-ttu-id="e2ed5-139">U kunt de opdracht filteren met behulp van de **Where-Object** cmdlet, in plaats van de **Get-WmiObject** filter.</span><span class="sxs-lookup"><span data-stu-id="e2ed5-139">You can filter the command by using the **Where-Object** cmdlet, instead of using the **Get-WmiObject** filter.</span></span>

```powershell
Get-WmiObject -Class Win32_NetworkAdapterConfiguration -ComputerName . | Where-Object -FilterScript {$_.IPEnabled} | ForEach-Object -Process {$_.SetDNSDomain('fabrikam.com')}
```

### <a name="performing-dhcp-configuration-tasks"></a><span data-ttu-id="e2ed5-140">DHCP-uitvoeren configuratietaken</span><span class="sxs-lookup"><span data-stu-id="e2ed5-140">Performing DHCP Configuration Tasks</span></span>

<span data-ttu-id="e2ed5-141">Wijzigen van de DHCP-informatie omvat het werken met een set netwerkadapters, net als de DNS-configuratie.</span><span class="sxs-lookup"><span data-stu-id="e2ed5-141">Modifying DHCP details involves working with a set of network adapters, just as the DNS configuration does.</span></span> <span data-ttu-id="e2ed5-142">Er zijn verschillende afzonderlijke acties die u uitvoeren kunt met behulp van WMI en we enkele van de algemene die gegevensbronnen wordt doorlopen.</span><span class="sxs-lookup"><span data-stu-id="e2ed5-142">There are several distinct actions you can perform by using WMI, and we will step through a few of the common ones.</span></span>

#### <a name="determining-dhcp-enabled-adapters"></a><span data-ttu-id="e2ed5-143">DHCP ingeschakeld Adapters bepalen</span><span class="sxs-lookup"><span data-stu-id="e2ed5-143">Determining DHCP-Enabled Adapters</span></span>

<span data-ttu-id="e2ed5-144">Als u zoekt de adapters DHCP-functionaliteit op een computer, gebruik de volgende opdracht:</span><span class="sxs-lookup"><span data-stu-id="e2ed5-144">To find the DHCP-enabled adapters on a computer, use the following command:</span></span>

```powershell
Get-WmiObject -Class Win32_NetworkAdapterConfiguration -Filter "DHCPEnabled=$true" -ComputerName .
```

<span data-ttu-id="e2ed5-145">Als u wilt uitsluiten van netwerkadapters met IP-configuratie oplossen, kunt u alleen IP-functionaliteit adapters ophalen:</span><span class="sxs-lookup"><span data-stu-id="e2ed5-145">To exclude adapters with IP configuration problems, you can retrieve only IP-enabled adapters:</span></span>

```powershell
Get-WmiObject -Class Win32_NetworkAdapterConfiguration -Filter "IPEnabled=$true and DHCPEnabled=$true" -ComputerName .
```

#### <a name="retrieving-dhcp-properties"></a><span data-ttu-id="e2ed5-146">Bij het ophalen van DHCP-eigenschappen</span><span class="sxs-lookup"><span data-stu-id="e2ed5-146">Retrieving DHCP Properties</span></span>

<span data-ttu-id="e2ed5-147">Omdat DHCP-eigenschappen voor een adapter met algemeen begint met 'DHCP', kunt u de parameter eigenschap van Format-Table kunt gebruiken om alleen de eigenschappen weer te geven:</span><span class="sxs-lookup"><span data-stu-id="e2ed5-147">Because DHCP-related properties for an adapter generally begin with "DHCP," you can use the Property parameter of Format-Table to display only those properties:</span></span>

```powershell
Get-WmiObject -Class Win32_NetworkAdapterConfiguration -Filter "DHCPEnabled=$true" -ComputerName . | Format-Table -Property DHCP*
```

#### <a name="enabling-dhcp-on-each-adapter"></a><span data-ttu-id="e2ed5-148">DHCP op elke Adapter inschakelen</span><span class="sxs-lookup"><span data-stu-id="e2ed5-148">Enabling DHCP on Each Adapter</span></span>

<span data-ttu-id="e2ed5-149">Om in te schakelen DHCP op alle netwerkadapters, gebruik de volgende opdracht:</span><span class="sxs-lookup"><span data-stu-id="e2ed5-149">To enable DHCP on all adapters, use the following command:</span></span>

```powershell
Get-WmiObject -Class Win32_NetworkAdapterConfiguration -Filter IPEnabled=$true -ComputerName . | ForEach-Object -Process {$_.EnableDHCP()}
```

<span data-ttu-id="e2ed5-150">U kunt de **Filter** instructie ' IPEnabled = $true en DHCPEnabled $false = "om te voorkomen dat het inschakelen van DHCP waar deze al is ingeschakeld, maar als deze stap niet leiden tot fouten.</span><span class="sxs-lookup"><span data-stu-id="e2ed5-150">You can use the **Filter** statement "IPEnabled=$true and DHCPEnabled=$false" to avoid enabling DHCP where it is already enabled, but omitting this step will not cause errors.</span></span>

#### <a name="releasing-and-renewing-dhcp-leases-on-specific-adapters"></a><span data-ttu-id="e2ed5-151">Vrijgeven en DHCP-Leases op specifieke netwerkadapters te vernieuwen</span><span class="sxs-lookup"><span data-stu-id="e2ed5-151">Releasing and Renewing DHCP Leases on Specific Adapters</span></span>

<span data-ttu-id="e2ed5-152">De **Win32_NetworkAdapterConfiguration** klasse heeft **ReleaseDHCPLease** en **RenewDCHPLease** methoden.</span><span class="sxs-lookup"><span data-stu-id="e2ed5-152">The **Win32_NetworkAdapterConfiguration** class has **ReleaseDHCPLease** and **RenewDHCPLease** methods.</span></span> <span data-ttu-id="e2ed5-153">Beide worden op dezelfde manier gebruikt.</span><span class="sxs-lookup"><span data-stu-id="e2ed5-153">Both are used in the same way.</span></span> <span data-ttu-id="e2ed5-154">In het algemeen deze methoden gebruiken als u alleen wilt vrijgeven of vernieuwen van adressen voor een adapter op een specifiek subnet.</span><span class="sxs-lookup"><span data-stu-id="e2ed5-154">In general, use these methods if you only need to release or renew addresses for an adapter on a specific subnet.</span></span> <span data-ttu-id="e2ed5-155">De eenvoudigste manier om filter-adapters in een subnet is de adapterconfiguraties die gebruikmaken van de gateway voor dat subnet kiezen.</span><span class="sxs-lookup"><span data-stu-id="e2ed5-155">The easiest way to filter adapters on a subnet is to choose only the adapter configurations that use the gateway for that subnet.</span></span> <span data-ttu-id="e2ed5-156">De volgende opdracht worden bijvoorbeeld alle DHCP-leases op netwerkadapters op de lokale computer die zijn het verkrijgen van DHCP-leases van 192.168.1.254 vrijgegeven:</span><span class="sxs-lookup"><span data-stu-id="e2ed5-156">For example, the following command releases all DHCP leases on adapters on the local computer that are obtaining DHCP leases from 192.168.1.254:</span></span>

```powershell
Get-WmiObject -Class Win32_NetworkAdapterConfiguration -Filter "IPEnabled=$true and DHCPEnabled=$true" -ComputerName . | Where-Object -FilterScript {$_.DHCPServer -contains '192.168.1.254'} | ForEach-Object -Process {$_.ReleaseDHCPLease()}
```

<span data-ttu-id="e2ed5-157">De enige wijziging voor het vernieuwen van een DHCP-lease is het gebruik van de **RenewDCHPLease** methode in plaats van de **ReleaseDHCPLease** methode:</span><span class="sxs-lookup"><span data-stu-id="e2ed5-157">The only change for renewing a DHCP lease is to use the **RenewDHCPLease** method instead of the **ReleaseDHCPLease** method:</span></span>

```powershell
Get-WmiObject -Class Win32_NetworkAdapterConfiguration -Filter "IPEnabled=$true and DHCPEnabled=$true" -ComputerName . | Where-Object -FilterScript {$_.DHCPServer -contains '192.168.1.254'} | ForEach-Object -Process {$_.ReleaseDHCPLease()}
```

> [!NOTE]
> <span data-ttu-id="e2ed5-158">Wanneer u deze methoden op een externe computer, er rekening mee dat u kunt geen toegang meer tot het externe systeem als u met het via de adapter met de lease vrijgegeven of vernieuwd verbonden bent.</span><span class="sxs-lookup"><span data-stu-id="e2ed5-158">When using these methods on a remote computer, be aware that you can lose access to the remote system if you are connected to it through the adapter with the released or renewed lease.</span></span>

#### <a name="releasing-and-renewing-dhcp-leases-on-all-adapters"></a><span data-ttu-id="e2ed5-159">Vrijgeven en vernieuwen van DHCP-Leases op alle netwerkadapters</span><span class="sxs-lookup"><span data-stu-id="e2ed5-159">Releasing and Renewing DHCP Leases on All Adapters</span></span>

<span data-ttu-id="e2ed5-160">U kunt globale releases van DHCP-adres of vernieuwingen op alle netwerkadapters uitvoeren met behulp van de **Win32_NetworkAdapterConfiguration** methoden, **ReleaseDHCPLeaseAll** en **RenewDCHPLeaseAll** .</span><span class="sxs-lookup"><span data-stu-id="e2ed5-160">You can perform global DHCP address releases or renewals on all adapters by using the **Win32_NetworkAdapterConfiguration** methods, **ReleaseDHCPLeaseAll** and **RenewDHCPLeaseAll**.</span></span> <span data-ttu-id="e2ed5-161">Echter, de opdracht moet toepassen op de WMI-klasse, in plaats van een bepaalde adapter, omdat het vrijgeven en leases wereldwijd vernieuwen wordt uitgevoerd op de klasse, niet op een specifieke adapter.</span><span class="sxs-lookup"><span data-stu-id="e2ed5-161">However, the command must apply to the WMI class, rather than a particular adapter, because releasing and renewing leases globally is performed on the class, not on a specific adapter.</span></span>

<span data-ttu-id="e2ed5-162">Een verwijzing naar een WMI-klasse, in plaats van de klasse-instanties, krijgt u alle WMI-klassen weergeven en selecteert u alleen de gewenste klasse met de naam.</span><span class="sxs-lookup"><span data-stu-id="e2ed5-162">You can get a reference to a WMI class, instead of class instances, by listing all WMI classes and then selecting only the desired class by name.</span></span> <span data-ttu-id="e2ed5-163">De volgende opdracht geeft bijvoorbeeld de Win32_NetworkAdapterConfiguration-klasse:</span><span class="sxs-lookup"><span data-stu-id="e2ed5-163">For example, the following command returns the Win32_NetworkAdapterConfiguration class:</span></span>

```powershell
Get-WmiObject -List | Where-Object -FilterScript {$_.Name -eq 'Win32_NetworkAdapterConfiguration'}
```

<span data-ttu-id="e2ed5-164">U kunt de volledige opdracht behandelen als de klasse en vervolgens de **ReleaseDHCPAdapterLease** methode.</span><span class="sxs-lookup"><span data-stu-id="e2ed5-164">You can treat the entire command as the class and then invoke the **ReleaseDHCPAdapterLease** method on it.</span></span> <span data-ttu-id="e2ed5-165">In de volgende opdracht, de haakjes de **Get-WmiObject** en **Where-Object** Pijplijnelementen direct Windows PowerShell moeten worden eerst geëvalueerd:</span><span class="sxs-lookup"><span data-stu-id="e2ed5-165">In the following command, the parentheses surrounding the **Get-WmiObject** and **Where-Object** pipeline elements direct Windows PowerShell to evaluate them first:</span></span>

```powershell
( Get-WmiObject -List | Where-Object -FilterScript {$_.Name -eq 'Win32_NetworkAdapterConfiguration'} ).ReleaseDHCPLeaseAll()
```

<span data-ttu-id="e2ed5-166">U kunt dezelfde opdrachtindeling gebruiken om aan te roepen de **RenewDCHPLeaseAll** methode:</span><span class="sxs-lookup"><span data-stu-id="e2ed5-166">You can use the same command format to invoke the **RenewDHCPLeaseAll** method:</span></span>

```powershell
( Get-WmiObject -List | Where-Object -FilterScript {$_.Name -eq 'Win32_NetworkAdapterConfiguration'} ).RenewDHCPLeaseAll()
```

### <a name="creating-a-network-share"></a><span data-ttu-id="e2ed5-167">Het maken van een netwerkshare</span><span class="sxs-lookup"><span data-stu-id="e2ed5-167">Creating a Network Share</span></span>

<span data-ttu-id="e2ed5-168">Voor het maken van een netwerkshare bevindt, gebruikt u de **Win32_Share maken** methode:</span><span class="sxs-lookup"><span data-stu-id="e2ed5-168">To create a network share, use the **Win32_Share Create** method:</span></span>

```powershell
(Get-WmiObject -List -ComputerName . | Where-Object -FilterScript {$_.Name -eq 'Win32_Share'}).Create('C:\temp','TempShare',0,25,'test share of the temp folder')
```

<span data-ttu-id="e2ed5-169">U kunt ook de share maken met behulp van **net share** in Windows PowerShell:</span><span class="sxs-lookup"><span data-stu-id="e2ed5-169">You can also create the share by using **net share** in Windows PowerShell:</span></span>

```powershell
net share tempshare=c:\temp /users:25 /remark:"test share of the temp folder"
```

### <a name="removing-a-network-share"></a><span data-ttu-id="e2ed5-170">Verwijderen van een netwerkshare</span><span class="sxs-lookup"><span data-stu-id="e2ed5-170">Removing a Network Share</span></span>

<span data-ttu-id="e2ed5-171">Kunt u een netwerkshare met **Win32_Share**, maar het proces is enigszins afwijken van het maken van een share, omdat u nodig hebt om op te halen van de specifieke share moet worden verwijderd, in plaats van de **Win32_Share** de klasse.</span><span class="sxs-lookup"><span data-stu-id="e2ed5-171">You can remove a network share with **Win32_Share**, but the process is slightly different from creating a share, because you need to retrieve the specific share to be removed, rather than the **Win32_Share** class.</span></span> <span data-ttu-id="e2ed5-172">De volgende instructie verwijdert u de share 'TempShare':</span><span class="sxs-lookup"><span data-stu-id="e2ed5-172">The following statement deletes the share "TempShare":</span></span>

```powershell
(Get-WmiObject -Class Win32_Share -ComputerName . -Filter "Name='TempShare'").Delete()
```

<span data-ttu-id="e2ed5-173">**Net share** zo goed werkt:</span><span class="sxs-lookup"><span data-stu-id="e2ed5-173">**Net share** works as well:</span></span>

```
PS> net share tempshare /delete

tempshare was deleted successfully.
```

### <a name="connecting-a-windows-accessible-network-drive"></a><span data-ttu-id="e2ed5-174">Verbinding maken van een netwerkstation toegankelijk is in Windows</span><span class="sxs-lookup"><span data-stu-id="e2ed5-174">Connecting a Windows Accessible Network Drive</span></span>

<span data-ttu-id="e2ed5-175">De **New-PSDrive** cmdlets maakt u een Windows PowerShell-station, maar de stations die zijn gemaakt op deze manier zijn alleen beschikbaar voor Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="e2ed5-175">The **New-PSDrive** cmdlets creates a Windows PowerShell drive, but drives created this way are available only to Windows PowerShell.</span></span> <span data-ttu-id="e2ed5-176">Een nieuwe netwerk station wilt maken, kunt u de **WScript.Network** COM-object.</span><span class="sxs-lookup"><span data-stu-id="e2ed5-176">To create a new networked drive, you can use the **WScript.Network** COM object.</span></span> <span data-ttu-id="e2ed5-177">De volgende opdracht wordt de share toegewezen \\ \\FPS01\\gebruikers naar de lokale schijf B:</span><span class="sxs-lookup"><span data-stu-id="e2ed5-177">The following command maps the share \\\\FPS01\\users to local drive B:</span></span>

```powershell
(New-Object -ComObject WScript.Network).MapNetworkDrive('B:', '\\FPS01\users')
```

<span data-ttu-id="e2ed5-178">De **netgebruik** opdracht werkt ook:</span><span class="sxs-lookup"><span data-stu-id="e2ed5-178">The **net use** command works as well:</span></span>

```powershell
net use B: \\FPS01\users
```

<span data-ttu-id="e2ed5-179">In beide gevallen toegewezen stations **WScript.Network** of netgebruik zijn onmiddellijk beschikbaar voor Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="e2ed5-179">Drives mapped with either **WScript.Network** or net use are immediately available to Windows PowerShell.</span></span>