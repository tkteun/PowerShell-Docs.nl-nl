---
ms.date: 2017-06-05
keywords: PowerShell-cmdlet
title: Uitvoeren van taken voor netwerken
ms.assetid: a43cc55f-70c1-45c8-9467-eaad0d57e3b5
ms.openlocfilehash: 4d7a91595b9d9d637ce915be2c2be9c20879dd8b
ms.sourcegitcommit: 74255f0b5f386a072458af058a15240140acb294
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 08/03/2017
---
# <a name="performing-networking-tasks"></a><span data-ttu-id="fcb8c-103">Uitvoeren van taken voor netwerken</span><span class="sxs-lookup"><span data-stu-id="fcb8c-103">Performing Networking Tasks</span></span>
<span data-ttu-id="fcb8c-104">Omdat TCP/IP het meest gebruikte netwerkprotocol is, omvatten de meeste beheertaken voor op laag niveau netwerk protocol TCP/IP.</span><span class="sxs-lookup"><span data-stu-id="fcb8c-104">Because TCP/IP is the most commonly used network protocol, most low-level network protocol administration tasks involve TCP/IP.</span></span> <span data-ttu-id="fcb8c-105">In deze sectie gebruiken we de Windows PowerShell en WMI voor deze taken.</span><span class="sxs-lookup"><span data-stu-id="fcb8c-105">In this section, we use Windows PowerShell and WMI to do these tasks.</span></span>

### <a name="listing-ip-addresses-for-a-computer"></a><span data-ttu-id="fcb8c-106">IP-adressen weergeven voor een Computer</span><span class="sxs-lookup"><span data-stu-id="fcb8c-106">Listing IP Addresses for a Computer</span></span>
<span data-ttu-id="fcb8c-107">Als u alle IP-adressen in gebruik is op de lokale computer, gebruikt u de volgende opdracht:</span><span class="sxs-lookup"><span data-stu-id="fcb8c-107">To get all IP addresses in use on the local computer, use the following command:</span></span>

```
Get-WmiObject -Class Win32_NetworkAdapterConfiguration -Filter IPEnabled=TRUE -ComputerName . | Format-Table -Property IPAddress
```

<span data-ttu-id="fcb8c-108">De uitvoer van deze opdracht verschilt van de meeste lijsten met zoekeigenschappen omdat waarden tussen accolades worden geplaatst:</span><span class="sxs-lookup"><span data-stu-id="fcb8c-108">The output of this command differs from most property lists, because values are enclosed in braces:</span></span>

<a name="preipaddress"></a><pre>IPAddress
---------
<span data-ttu-id="fcb8c-109">{192.168.1.80} {192.168.148.1} {192.168.171.1} {0.0.0.0}</span><span class="sxs-lookup"><span data-stu-id="fcb8c-109">{192.168.1.80} {192.168.148.1} {192.168.171.1} {0.0.0.0}</span></span></pre>

<span data-ttu-id="fcb8c-110">Om te begrijpen waarom de accolades worden weergegeven, gebruikt u de cmdlet Get-lid te onderzoeken de **IPAddress** eigenschap:</span><span class="sxs-lookup"><span data-stu-id="fcb8c-110">To understand why the braces appear, use the Get-Member cmdlet to examine the **IPAddress** property:</span></span>

<pre>PS> Get-WmiObject -Class Win32_NetworkAdapterConfiguration -Filter IPEnabled=TRUE -ComputerName . | Get-Member -Name IPAddress
TypeName: System.Management.ManagementObject#root\cimv2\Win32_NetworkAdapter
Configuration
Name      MemberType Definition
----      ---------- ----------
IPAddress Property   System.String[] IPAddress {get;}</pre>

<span data-ttu-id="fcb8c-111">De eigenschap IP-adres voor elke netwerkadapter is daadwerkelijk een matrix.</span><span class="sxs-lookup"><span data-stu-id="fcb8c-111">The IPAddress property for each network adapter is actually an array.</span></span> <span data-ttu-id="fcb8c-112">De accolades in de definitie is gebleken dat **IPAddress** is niet een **System.String** waarde, maar een matrix van **System.String** waarden.</span><span class="sxs-lookup"><span data-stu-id="fcb8c-112">The braces in the definition indicate that **IPAddress** is not a **System.String** value, but an array of **System.String** values.</span></span>

### <a name="listing-ip-configuration-data"></a><span data-ttu-id="fcb8c-113">IP-configuratiegegevens van aanbieding</span><span class="sxs-lookup"><span data-stu-id="fcb8c-113">Listing IP Configuration Data</span></span>
<span data-ttu-id="fcb8c-114">Als u wilt weergeven van gedetailleerde IP-configuratiegegevens voor elke netwerkadapter, moet u de volgende opdracht gebruiken:</span><span class="sxs-lookup"><span data-stu-id="fcb8c-114">To display detailed IP configuration data for each network adapter, use the following command:</span></span>

```
Get-WmiObject -Class Win32_NetworkAdapterConfiguration -Filter IPEnabled=TRUE -ComputerName .
```

<span data-ttu-id="fcb8c-115">De standaardweergave voor de configuratie voor de netwerkadapter is een zeer beperkte set van de beschikbare informatie.</span><span class="sxs-lookup"><span data-stu-id="fcb8c-115">The default display for the network adapter configuration object is a very reduced set of the available information.</span></span> <span data-ttu-id="fcb8c-116">Gebruik voor uitgebreide controle en probleemoplossing, Select-Object of een opmaak cmdlet, zoals indeling-lijst om op te geven van de eigenschappen die moeten worden weergegeven.</span><span class="sxs-lookup"><span data-stu-id="fcb8c-116">For in-depth inspection and troubleshooting, use Select-Object or a formatting cmdlet, such as Format-List, to specify the properties to be displayed.</span></span>

<span data-ttu-id="fcb8c-117">Als u niet geïnteresseerd in de eigenschappen van IPX of WINS bent, waarschijnlijk het geval in een moderne TCP/IP-netwerk, kunt u de parameter ExcludeProperty van Select-Object voor het verbergen van eigenschappen met namen die met 'WINS beginnen' of ' IPX: "</span><span class="sxs-lookup"><span data-stu-id="fcb8c-117">If you are not interested in IPX or WINS properties—probably the case in a modern TCP/IP network—you can use the ExcludeProperty parameter of Select-Object to hide properties with names that begin with "WINS" or "IPX:"</span></span>

```
Get-WmiObject -Class Win32_NetworkAdapterConfiguration -Filter IPEnabled=TRUE -ComputerName . | Select-Object -Property [a-z]* -ExcludeProperty IPX*,WINS*
```

<span data-ttu-id="fcb8c-118">Deze opdracht retourneert gedetailleerde informatie over DHCP, DNS, Routering en andere secundaire IP-configuratie-eigenschappen.</span><span class="sxs-lookup"><span data-stu-id="fcb8c-118">This command returns detailed information about DHCP, DNS, routing, and other minor IP configuration properties.</span></span>

### <a name="pinging-computers"></a><span data-ttu-id="fcb8c-119">Pingen naar Computers</span><span class="sxs-lookup"><span data-stu-id="fcb8c-119">Pinging Computers</span></span>
<span data-ttu-id="fcb8c-120">U kunt een eenvoudige ping uit voor een computer met door uitvoeren **Win32_PingStatus**.</span><span class="sxs-lookup"><span data-stu-id="fcb8c-120">You can perform a simple ping against a computer using by **Win32_PingStatus**.</span></span> <span data-ttu-id="fcb8c-121">De volgende opdracht de opdracht ping wordt uitgevoerd, maar retourneert uitgebreide uitvoer:</span><span class="sxs-lookup"><span data-stu-id="fcb8c-121">The following command performs the ping, but returns lengthy output:</span></span>

```
Get-WmiObject -Class Win32_PingStatus -Filter "Address='127.0.0.1'" -ComputerName .
```

<span data-ttu-id="fcb8c-122">Nuttiger formulier samenvattende informatie weergegeven in een van de eigenschappen van-adres, reactietijd en StatusCode, zoals worden gegenereerd door de volgende opdracht.</span><span class="sxs-lookup"><span data-stu-id="fcb8c-122">A more useful form for summary information a display of the Address, ResponseTime, and StatusCode properties, as generated by the following command.</span></span> <span data-ttu-id="fcb8c-123">De parameter Autosize van Format-Table aangepast kolommen in de tabel zodat ze correct wordt weergegeven in de Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="fcb8c-123">The Autosize parameter of Format-Table resizes the table columns so that they display properly in Windows PowerShell.</span></span>

```
PS> Get-WmiObject -Class Win32_PingStatus -Filter "Address='127.0.0.1'" -ComputerName . | Format-Table -Property Address,ResponseTime,StatusCode -Autosize

Address   ResponseTime StatusCode
-------   ------------ ----------
127.0.0.1            0          0
A status code of 0 indicates a successful ping.
```

<span data-ttu-id="fcb8c-124">U kunt een matrix gebruiken op meerdere computers met één opdracht ping.</span><span class="sxs-lookup"><span data-stu-id="fcb8c-124">You can use an array to ping multiple computers with a single command.</span></span> <span data-ttu-id="fcb8c-125">Omdat er meer dan één adres, gebruik de **ForEach-Object** te pingen elk adres afzonderlijk:</span><span class="sxs-lookup"><span data-stu-id="fcb8c-125">Because there is more than one address, use the **ForEach-Object** to ping each address separately:</span></span>

```
"127.0.0.1","localhost","research.microsoft.com" | ForEach-Object -Process {Get-WmiObject -Class Win32_PingStatus -Filter ("Address='" + $_ + "'") -ComputerName .} | Select-Object -Property Address,ResponseTime,StatusCode
```

<span data-ttu-id="fcb8c-126">U kunt dezelfde opdrachtindeling alle computers in een subnet, zoals een particulier netwerk dat gebruikmaakt van netwerknummer 192.168.1.0 en een standaard klasse C-subnetmasker (255.255.255.0) te pingen., worden alleen de adressen in het bereik van 192.168.1.1 via 192.168.1.254 rechtmatige lokale adressen (0 is altijd gereserveerd voor het netwerknummer en 255 is een subnet broadcast-adres).</span><span class="sxs-lookup"><span data-stu-id="fcb8c-126">You can use the same command format to ping all of the computers on a subnet, such as a private network that uses network number 192.168.1.0 and a standard Class C subnet mask (255.255.255.0)., Only addresses in the range of 192.168.1.1 through 192.168.1.254 are legitimate local addresses (0 is always reserved for the network number and 255 is a subnet broadcast address).</span></span>

<span data-ttu-id="fcb8c-127">Ter vertegenwoordiging van een matrix van de getallen tussen 1 en 254 in Windows PowerShell, gebruikt u de instructie **1..254.**</span><span class="sxs-lookup"><span data-stu-id="fcb8c-127">To represent an array of the numbers from 1 through 254 in Windows PowerShell, use the statement **1..254.**</span></span> <span data-ttu-id="fcb8c-128">Een ping voltooid subnet kan worden uitgevoerd door het genereren van de matrix en vervolgens de waarden op een gedeeltelijke adres toe te voegen in de ping-instructie:</span><span class="sxs-lookup"><span data-stu-id="fcb8c-128">A complete subnet ping can be performed by generating the array and then adding the values onto a partial address in the ping statement:</span></span>

```
1..254| ForEach-Object -Process {Get-WmiObject -Class Win32_PingStatus -Filter ("Address='192.168.1." + $_ + "'") -ComputerName .} | Select-Object -Property Address,ResponseTime,StatusCode
```

<span data-ttu-id="fcb8c-129">Houd er rekening mee dat deze techniek voor het genereren van een bereik aan adressen elders ook kan worden gebruikt.</span><span class="sxs-lookup"><span data-stu-id="fcb8c-129">Note that this technique for generating a range of addresses can be used elsewhere as well.</span></span> <span data-ttu-id="fcb8c-130">Op deze manier kunt u een volledige reeks adressen genereren:</span><span class="sxs-lookup"><span data-stu-id="fcb8c-130">You can generate a complete set of addresses in this way:</span></span>

`$ips = 1..254 | ForEach-Object -Process {"192.168.1." + $_}`

### <a name="retrieving-network-adapter-properties"></a><span data-ttu-id="fcb8c-131">Bij het ophalen van eigenschappen van netwerkadapter</span><span class="sxs-lookup"><span data-stu-id="fcb8c-131">Retrieving Network Adapter Properties</span></span>
<span data-ttu-id="fcb8c-132">Eerder in deze handleiding wordt vermeld dat u algemene configuratie-eigenschappen ophalen met behulp van kan **Win32_NetworkAdapterConfiguration**.</span><span class="sxs-lookup"><span data-stu-id="fcb8c-132">Earlier in this user's guide, we mentioned that you could retrieve general configuration properties by using **Win32_NetworkAdapterConfiguration**.</span></span> <span data-ttu-id="fcb8c-133">Hoewel niet strikt TCP/IP-informatie, netwerkadapterinformatie zoals MAC-adressen en typen netwerkadapters kunnen nuttig zijn voor inzicht in wat er gebeurt met een computer.</span><span class="sxs-lookup"><span data-stu-id="fcb8c-133">Although not strictly TCP/IP information, network adapter information such as MAC addresses and adapter types can be useful for understanding what is going on with a computer.</span></span> <span data-ttu-id="fcb8c-134">Als u een overzicht van deze informatie, gebruikt u de volgende opdracht:</span><span class="sxs-lookup"><span data-stu-id="fcb8c-134">To get a summary of this information, use the following command:</span></span>

```
Get-WmiObject -Class Win32_NetworkAdapter -ComputerName .
```

### <a name="assigning-the-dns-domain-for-a-network-adapter"></a><span data-ttu-id="fcb8c-135">Het DNS-domein toe te wijzen voor een netwerkadapter</span><span class="sxs-lookup"><span data-stu-id="fcb8c-135">Assigning the DNS Domain for a Network Adapter</span></span>
<span data-ttu-id="fcb8c-136">Als het DNS-domein voor automatische naamomzetting wilt toewijzen, gebruikt u de **Win32_NetworkAdapterConfiguration SetDNSDomain** methode.</span><span class="sxs-lookup"><span data-stu-id="fcb8c-136">To assign the DNS domain for automatic name resolution, use the **Win32_NetworkAdapterConfiguration SetDNSDomain** method.</span></span> <span data-ttu-id="fcb8c-137">Omdat u de DNS-domein voor de configuratie van elke netwerkadapter afzonderlijk toewijst, moet u een **ForEach-Object** instructie het domein toewijzen aan elke adapter:</span><span class="sxs-lookup"><span data-stu-id="fcb8c-137">Because you assign the DNS domain for each network adapter configuration independently, you need to use a **ForEach-Object** statement to assign the domain to each adapter:</span></span>

```
Get-WmiObject -Class Win32_NetworkAdapterConfiguration -Filter IPEnabled=true -ComputerName . | ForEach-Object -Process { $_. SetDNSDomain("fabrikam.com") }
```

<span data-ttu-id="fcb8c-138">De instructie voor filteren ' IPEnabled = true ' is nodig omdat zelfs op een netwerk dat gebruikmaakt van alleen TCP/IP, verschillende configuraties van de netwerkadapters op een computer niet true TCP/IP-adapters; Deze algemene software-elementen ter ondersteuning van de RAS-, PPTP, QoS en andere services voor alle adapters zijn en dus niet een adres van hun eigen hebben.</span><span class="sxs-lookup"><span data-stu-id="fcb8c-138">The filtering statement "IPEnabled=true" is necessary, because even on a network that uses only TCP/IP, several of the network adapter configurations on a computer are not true TCP/IP adapters; they are general software elements supporting RAS, PPTP, QoS, and other services for all adapters and thus do not have an address of their own.</span></span>

<span data-ttu-id="fcb8c-139">U kunt de opdracht filteren met behulp van de **Where-Object** cmdlet, in plaats van de **Get-WmiObject** filter.</span><span class="sxs-lookup"><span data-stu-id="fcb8c-139">You can filter the command by using the **Where-Object** cmdlet, instead of using the **Get-WmiObject** filter.</span></span>

```
Get-WmiObject -Class Win32_NetworkAdapterConfiguration -ComputerName . | Where-Object -FilterScript {$_.IPEnabled} | ForEach-Object -Process {$_.SetDNSDomain("fabrikam.com")}
```

### <a name="performing-dhcp-configuration-tasks"></a><span data-ttu-id="fcb8c-140">DHCP-uitvoeren configuratietaken</span><span class="sxs-lookup"><span data-stu-id="fcb8c-140">Performing DHCP Configuration Tasks</span></span>
<span data-ttu-id="fcb8c-141">Wijzigen van de DHCP-informatie omvat het werken met een set netwerkadapters, net als de DNS-configuratie.</span><span class="sxs-lookup"><span data-stu-id="fcb8c-141">Modifying DHCP details involves working with a set of network adapters, just as the DNS configuration does.</span></span> <span data-ttu-id="fcb8c-142">Er zijn verschillende afzonderlijke acties die u uitvoeren kunt met behulp van WMI en wordt er slechts enkele van de meest gangbare doorlopen.</span><span class="sxs-lookup"><span data-stu-id="fcb8c-142">There are several distinct actions you can perform by using WMI, and we will step through a few of the common ones.</span></span>

#### <a name="determining-dhcp-enabled-adapters"></a><span data-ttu-id="fcb8c-143">DCHP-Adapters bepalen</span><span class="sxs-lookup"><span data-stu-id="fcb8c-143">Determining DHCP-Enabled Adapters</span></span>
<span data-ttu-id="fcb8c-144">Ga voor de adapters DHCP ingeschakeld op een computer, moet u de volgende opdracht gebruiken:</span><span class="sxs-lookup"><span data-stu-id="fcb8c-144">To find the DHCP-enabled adapters on a computer, use the following command:</span></span>

```
Get-WmiObject -Class Win32_NetworkAdapterConfiguration -Filter "DHCPEnabled=true" -ComputerName .
```

<span data-ttu-id="fcb8c-145">Als u wilt uitsluiten van netwerkadapters met IP-configuratieproblemen, kunt u alleen IP ingeschakeld adapters ophalen:</span><span class="sxs-lookup"><span data-stu-id="fcb8c-145">To exclude adapters with IP configuration problems, you can retrieve only IP-enabled adapters:</span></span>

```
Get-WmiObject -Class Win32_NetworkAdapterConfiguration -Filter "IPEnabled=true and DHCPEnabled=true" -ComputerName .
```

#### <a name="retrieving-dhcp-properties"></a><span data-ttu-id="fcb8c-146">Bij het ophalen van eigenschappen voor DHCP</span><span class="sxs-lookup"><span data-stu-id="fcb8c-146">Retrieving DHCP Properties</span></span>
<span data-ttu-id="fcb8c-147">Omdat DHCP-gerelateerde eigenschappen voor een adapter wordt doorgaans begint met 'DHCP', kunt u de parameter Property van Format-Table gebruiken om alleen die eigenschappen weer te geven:</span><span class="sxs-lookup"><span data-stu-id="fcb8c-147">Because DHCP-related properties for an adapter generally begin with "DHCP," you can use the Property parameter of Format-Table to display only those properties:</span></span>

```
Get-WmiObject -Class Win32_NetworkAdapterConfiguration -Filter "DHCPEnabled=true" -ComputerName . | Format-Table -Property DHCP*
```

#### <a name="enabling-dhcp-on-each-adapter"></a><span data-ttu-id="fcb8c-148">DHCP op elke Adapter inschakelen</span><span class="sxs-lookup"><span data-stu-id="fcb8c-148">Enabling DHCP on Each Adapter</span></span>
<span data-ttu-id="fcb8c-149">Activeren van DHCP op alle netwerkadapters moet u de volgende opdracht gebruiken:</span><span class="sxs-lookup"><span data-stu-id="fcb8c-149">To enable DHCP on all adapters, use the following command:</span></span>

```
Get-WmiObject -Class Win32_NetworkAdapterConfiguration -Filter IPEnabled=true -ComputerName . | ForEach-Object -Process {$_.EnableDHCP()}
```

<span data-ttu-id="fcb8c-150">U kunt de **Filter** instructie ' IPEnabled = true en DHCPEnabled = false ' om te voorkomen dat het inschakelen van DHCP waar deze al is ingeschakeld, maar als deze stap wordt weggelaten wordt geen fouten veroorzaken.</span><span class="sxs-lookup"><span data-stu-id="fcb8c-150">You can use the **Filter** statement "IPEnabled=true and DHCPEnabled=false" to avoid enabling DHCP where it is already enabled, but omitting this step will not cause errors.</span></span>

#### <a name="releasing-and-renewing-dhcp-leases-on-specific-adapters"></a><span data-ttu-id="fcb8c-151">Vrijgeven en DHCP-Leases op specifieke Adapters vernieuwen</span><span class="sxs-lookup"><span data-stu-id="fcb8c-151">Releasing and Renewing DHCP Leases on Specific Adapters</span></span>
<span data-ttu-id="fcb8c-152">De **Win32_NetworkAdapterConfiguration** klasse heeft **ReleaseDHCPLease** en **RenewDCHPLease** methoden.</span><span class="sxs-lookup"><span data-stu-id="fcb8c-152">The **Win32_NetworkAdapterConfiguration** class has **ReleaseDHCPLease** and **RenewDHCPLease** methods.</span></span> <span data-ttu-id="fcb8c-153">Beide worden op dezelfde manier gebruikt.</span><span class="sxs-lookup"><span data-stu-id="fcb8c-153">Both are used in the same way.</span></span> <span data-ttu-id="fcb8c-154">Deze methoden in het algemeen gebruiken als u alleen wilt vrijgeven of vernieuwen van adressen voor een adapter op een specifiek subnet.</span><span class="sxs-lookup"><span data-stu-id="fcb8c-154">In general, use these methods if you only need to release or renew addresses for an adapter on a specific subnet.</span></span> <span data-ttu-id="fcb8c-155">De eenvoudigste manier om filter-adapters in een subnet is de adapterconfiguraties die gebruikmaken van de gateway voor dat subnet kiezen.</span><span class="sxs-lookup"><span data-stu-id="fcb8c-155">The easiest way to filter adapters on a subnet is to choose only the adapter configurations that use the gateway for that subnet.</span></span> <span data-ttu-id="fcb8c-156">De volgende opdracht worden bijvoorbeeld alle DHCP-leases op adapters op de lokale computer die u DHCP-leases van 192.168.1.254 verkrijgt vrijgegeven:</span><span class="sxs-lookup"><span data-stu-id="fcb8c-156">For example, the following command releases all DHCP leases on adapters on the local computer that are obtaining DHCP leases from 192.168.1.254:</span></span>

```
Get-WmiObject -Class Win32_NetworkAdapterConfiguration -Filter "IPEnabled=true and DHCPEnabled=true" -ComputerName . | Where-Object -FilterScript {$_.DHCPServer -contains "192.168.1.254"} | ForEach-Object -Process {$_.ReleaseDHCPLease()}
```

<span data-ttu-id="fcb8c-157">De enige wijziging voor het vernieuwen van een DHCP-lease is met de **RenewDCHPLease** methode in plaats van de **ReleaseDHCPLease** methode:</span><span class="sxs-lookup"><span data-stu-id="fcb8c-157">The only change for renewing a DHCP lease is to use the **RenewDHCPLease** method instead of the **ReleaseDHCPLease** method:</span></span>

```
Get-WmiObject -Class Win32_NetworkAdapterConfiguration -Filter "IPEnabled=true and DHCPEnabled=true" -ComputerName . | Where-Object -FilterScript {$_.DHCPServer -contains "192.168.1.254"} | ForEach-Object -Process {$_.ReleaseDHCPLease()}
```

> [!NOTE]
> <span data-ttu-id="fcb8c-158">Wanneer u deze methoden op een externe computer, Let erop dat u toegang met het externe systeem verliezen kunt als u met het via de adapter met de lease vrijgegeven of vernieuwd verbonden bent.</span><span class="sxs-lookup"><span data-stu-id="fcb8c-158">When using these methods on a remote computer, be aware that you can lose access to the remote system if you are connected to it through the adapter with the released or renewed lease.</span></span>

#### <a name="releasing-and-renewing-dhcp-leases-on-all-adapters"></a><span data-ttu-id="fcb8c-159">Vrijgeven en DHCP-Leases op alle Adapters vernieuwen</span><span class="sxs-lookup"><span data-stu-id="fcb8c-159">Releasing and Renewing DHCP Leases on All Adapters</span></span>
<span data-ttu-id="fcb8c-160">U kunt globale releases van DHCP-adres of vernieuwingen op alle adapters uitvoeren met behulp van de **Win32_NetworkAdapterConfiguration** methoden, **ReleaseDHCPLeaseAll** en **RenewDCHPLeaseAll** .</span><span class="sxs-lookup"><span data-stu-id="fcb8c-160">You can perform global DHCP address releases or renewals on all adapters by using the **Win32_NetworkAdapterConfiguration** methods, **ReleaseDHCPLeaseAll** and **RenewDHCPLeaseAll**.</span></span> <span data-ttu-id="fcb8c-161">Echter de opdracht moet toepassen op de WMI-klasse, in plaats van een bepaalde adapter omdat vrijgeven en leases globaal vernieuwen op de klasse, niet op een bepaalde adapter wordt uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="fcb8c-161">However, the command must apply to the WMI class, rather than a particular adapter, because releasing and renewing leases globally is performed on the class, not on a specific adapter.</span></span>

<span data-ttu-id="fcb8c-162">U krijgt een verwijzing naar een WMI-klasse, in plaats van de klasse-instanties weergeven van alle WMI-klassen en selecteert u alleen de gewenste klasse met de naam.</span><span class="sxs-lookup"><span data-stu-id="fcb8c-162">You can get a reference to a WMI class, instead of class instances, by listing all WMI classes and then selecting only the desired class by name.</span></span> <span data-ttu-id="fcb8c-163">De volgende opdracht geeft bijvoorbeeld de Win32_NetworkAdapterConfiguration-klasse:</span><span class="sxs-lookup"><span data-stu-id="fcb8c-163">For example, the following command returns the Win32_NetworkAdapterConfiguration class:</span></span>

```
Get-WmiObject -List | Where-Object -FilterScript {$_.Name -eq "Win32_NetworkAdapterConfiguration"}
```

<span data-ttu-id="fcb8c-164">U kunt de volledige opdracht behandelen als de klasse en roep daarna de **ReleaseDHCPAdapterLease** methode erop.</span><span class="sxs-lookup"><span data-stu-id="fcb8c-164">You can treat the entire command as the class and then invoke the **ReleaseDHCPAdapterLease** method on it.</span></span> <span data-ttu-id="fcb8c-165">In de volgende opdracht, de haakjes de **Get-WmiObject** en **Where-Object** Pijplijnelementen direct Windows PowerShell om te evalueren ze eerst:</span><span class="sxs-lookup"><span data-stu-id="fcb8c-165">In the following command, the parentheses surrounding the **Get-WmiObject** and **Where-Object** pipeline elements direct Windows PowerShell to evaluate them first:</span></span>

```
( Get-WmiObject -List | Where-Object -FilterScript {$_.Name -eq "Win32_NetworkAdapterConfiguration"} ).ReleaseDHCPLeaseAll()
```

<span data-ttu-id="fcb8c-166">U kunt dezelfde opdrachtindeling gebruiken om aan te roepen de **RenewDCHPLeaseAll** methode:</span><span class="sxs-lookup"><span data-stu-id="fcb8c-166">You can use the same command format to invoke the **RenewDHCPLeaseAll** method:</span></span>

```
( Get-WmiObject -List | Where-Object -FilterScript {$_.Name -eq "Win32_NetworkAdapterConfiguration"} ).RenewDHCPLeaseAll()
```

### <a name="creating-a-network-share"></a><span data-ttu-id="fcb8c-167">Een netwerkshare maken</span><span class="sxs-lookup"><span data-stu-id="fcb8c-167">Creating a Network Share</span></span>
<span data-ttu-id="fcb8c-168">Voor het maken van een netwerkshare gebruikt de **Win32_Share maken** methode:</span><span class="sxs-lookup"><span data-stu-id="fcb8c-168">To create a network share, use the **Win32_Share Create** method:</span></span>

```
(Get-WmiObject -List -ComputerName . | Where-Object -FilterScript {$_.Name -eq "Win32_Share"}).Create("C:\temp","TempShare",0,25,"test share of the temp folder")
```

<span data-ttu-id="fcb8c-169">U kunt ook de share maken met behulp van **net share** in Windows PowerShell:</span><span class="sxs-lookup"><span data-stu-id="fcb8c-169">You can also create the share by using **net share** in Windows PowerShell:</span></span>

```
net share tempshare=c:\temp /users:25 /remark:"test share of the temp folder"
```

### <a name="removing-a-network-share"></a><span data-ttu-id="fcb8c-170">Een netwerkshare verwijderen</span><span class="sxs-lookup"><span data-stu-id="fcb8c-170">Removing a Network Share</span></span>
<span data-ttu-id="fcb8c-171">U kunt een netwerkshare in verwijderen **Win32_Share**, maar het proces is enigszins afwijken van het maken van een share, omdat u nodig hebt voor het ophalen van de specifieke share moet worden verwijderd, in plaats van de **Win32_Share** de klasse.</span><span class="sxs-lookup"><span data-stu-id="fcb8c-171">You can remove a network share with **Win32_Share**, but the process is slightly different from creating a share, because you need to retrieve the specific share to be removed, rather than the **Win32_Share** class.</span></span> <span data-ttu-id="fcb8c-172">De volgende instructie verwijdert de share 'TempShare':</span><span class="sxs-lookup"><span data-stu-id="fcb8c-172">The following statement deletes the share "TempShare":</span></span>

```
(Get-WmiObject -Class Win32_Share -ComputerName . -Filter "Name='TempShare'").Delete()
```

<span data-ttu-id="fcb8c-173">**Net share** werkt ook:</span><span class="sxs-lookup"><span data-stu-id="fcb8c-173">**Net share** works as well:</span></span>

```
PS> net share tempshare /delete
tempshare was deleted successfully.
```

### <a name="connecting-a-windows-accessible-network-drive"></a><span data-ttu-id="fcb8c-174">Verbinding maken met een toegankelijke netwerkstation van Windows</span><span class="sxs-lookup"><span data-stu-id="fcb8c-174">Connecting a Windows Accessible Network Drive</span></span>
<span data-ttu-id="fcb8c-175">De **nieuw PSDrive** cmdlets maakt een Windows PowerShell-station, maar de stations die zijn gemaakt op deze manier zijn alleen beschikbaar voor Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="fcb8c-175">The **New-PSDrive** cmdlets creates a Windows PowerShell drive, but drives created this way are available only to Windows PowerShell.</span></span> <span data-ttu-id="fcb8c-176">Een nieuwe netwerk station wilt maken, kunt u de **WScript.Network** COM-object.</span><span class="sxs-lookup"><span data-stu-id="fcb8c-176">To create a new networked drive, you can use the **WScript.Network** COM object.</span></span> <span data-ttu-id="fcb8c-177">De volgende opdracht wordt de share toegewezen \\ \\FPS01\\gebruikers naar de lokale schijf B:</span><span class="sxs-lookup"><span data-stu-id="fcb8c-177">The following command maps the share \\\\FPS01\\users to local drive B:</span></span>

```
(New-Object -ComObject WScript.Network).MapNetworkDrive("B:", "\\FPS01\users")
```

<span data-ttu-id="fcb8c-178">De **gebruik net** opdracht werkt ook:</span><span class="sxs-lookup"><span data-stu-id="fcb8c-178">The **net use** command works as well:</span></span>

```
net use B: \\FPS01\users
```

<span data-ttu-id="fcb8c-179">Schijven met een toegewezen **WScript.Network** of net gebruik onmiddellijk beschikbaar zijn voor Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="fcb8c-179">Drives mapped with either **WScript.Network** or net use are immediately available to Windows PowerShell.</span></span>

