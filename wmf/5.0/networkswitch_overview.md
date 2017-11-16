---
ms.date: 2017-06-12
author: JKeithB
ms.topic: reference
keywords: WMF, powershell, setup
ms.openlocfilehash: 80852bf750700d549de24e150ffd89ac55b7bf88
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 06/12/2017
---
# <a name="network-switch-management-with-powershell"></a><span data-ttu-id="66621-102">Switch-netwerkbeheer met PowerShell</span><span class="sxs-lookup"><span data-stu-id="66621-102">Network Switch Management with PowerShell</span></span>

<span data-ttu-id="66621-103">De **Get-NetworkSwitchEthernetPort** cmdlet retourneert nu de volgende aanvullende informatie met exemplaren:</span><span class="sxs-lookup"><span data-stu-id="66621-103">The **Get-NetworkSwitchEthernetPort** cmdlet now returns the following additional information with instances:</span></span>

- <span data-ttu-id="66621-104">IP-adres – het IP-adres die zijn gekoppeld aan de poort</span><span class="sxs-lookup"><span data-stu-id="66621-104">IPAddress – the IP address associated with the port</span></span>
- <span data-ttu-id="66621-105">PortMode: de poortmodus: toegang, route of trunk</span><span class="sxs-lookup"><span data-stu-id="66621-105">PortMode – the port mode: access, route, or trunk</span></span>
- <span data-ttu-id="66621-106">AccessVLAN – de de VLAN-ID die is gekoppeld aan deze poort in de toegangsmodus</span><span class="sxs-lookup"><span data-stu-id="66621-106">AccessVLAN – the ID of the VLAN associated with this port in access mode</span></span>
- <span data-ttu-id="66621-107">TrunkedVLANList – een lijst met de id van VLAN's die zijn gekoppeld aan deze poort in de trunkmodus</span><span class="sxs-lookup"><span data-stu-id="66621-107">TrunkedVLANList – a list of IDs of VLANs associated with this port in trunk mode</span></span>

## <a name="fundamental-network-switch-management-with-windows-powershell"></a><span data-ttu-id="66621-108">Fundamentele netwerkbeheer switch met Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="66621-108">Fundamental network switch management with Windows PowerShell</span></span>

<span data-ttu-id="66621-109">De netwerkswitch-cmdlets die zijn geïntroduceerd in WMF 5.0, kunt u switch, virtuele LAN (VLAN) en basic Layer 2-switch-poort netwerkconfiguratie van toepassing op Windows Server 2012 R2-logo gecertificeerde netwerkswitches.</span><span class="sxs-lookup"><span data-stu-id="66621-109">The Network Switch cmdlets, introduced in WMF 5.0, enable you to apply switch, virtual LAN (VLAN), and basic Layer 2 network switch port configuration to Windows Server 2012 R2 logo-certified network switches.</span></span> <span data-ttu-id="66621-110">Microsoft blijft doorgevoerd in de ondersteuning van de [Datacenter Abstraction](http://technet.microsoft.com/en-us/cloud/dal.aspx) visie Layer (DAL), en waarde voor onze klanten en partners in deze ruimte weergeven.</span><span class="sxs-lookup"><span data-stu-id="66621-110">Microsoft remains committed to supporting the [Datacenter Abstraction](http://technet.microsoft.com/en-us/cloud/dal.aspx) Layer (DAL) vision, and to show value for our customers and partners in this space.</span></span> <span data-ttu-id="66621-111">Met deze cmdlets kunt u uitvoeren:</span><span class="sxs-lookup"><span data-stu-id="66621-111">Using these cmdlets you can perform:</span></span>

- <span data-ttu-id="66621-112">Global switch configuratie, zoals:</span><span class="sxs-lookup"><span data-stu-id="66621-112">Global switch configuration, such as:</span></span>
    - <span data-ttu-id="66621-113">Naam van de host</span><span class="sxs-lookup"><span data-stu-id="66621-113">Set host name</span></span>
    - <span data-ttu-id="66621-114">Set switch banner</span><span class="sxs-lookup"><span data-stu-id="66621-114">Set switch banner</span></span>
    - <span data-ttu-id="66621-115">Configuratie blijven behouden</span><span class="sxs-lookup"><span data-stu-id="66621-115">Persist configuration</span></span>
    - <span data-ttu-id="66621-116">Functie- of uitschakelen</span><span class="sxs-lookup"><span data-stu-id="66621-116">Enable or disable feature</span></span>

- <span data-ttu-id="66621-117">VLAN-configuratie:</span><span class="sxs-lookup"><span data-stu-id="66621-117">VLAN configuration:</span></span>
    - <span data-ttu-id="66621-118">Maken of verwijderen van VLAN</span><span class="sxs-lookup"><span data-stu-id="66621-118">Create or remove VLAN</span></span>
    - <span data-ttu-id="66621-119">In- of uitschakelen van VLAN</span><span class="sxs-lookup"><span data-stu-id="66621-119">Enable or disable VLAN</span></span>
    - <span data-ttu-id="66621-120">VLAN opsommen</span><span class="sxs-lookup"><span data-stu-id="66621-120">Enumerate VLAN</span></span>
    - <span data-ttu-id="66621-121">Beschrijvende naam van de set met een VLAN</span><span class="sxs-lookup"><span data-stu-id="66621-121">Set friendly name to a VLAN</span></span>

- <span data-ttu-id="66621-122">Configuratie van laag 2-poort:</span><span class="sxs-lookup"><span data-stu-id="66621-122">Layer 2 port configuration:</span></span>
    - <span data-ttu-id="66621-123">Poorten opsommen</span><span class="sxs-lookup"><span data-stu-id="66621-123">Enumerate ports</span></span>
    - <span data-ttu-id="66621-124">In- of uitschakelen van poorten</span><span class="sxs-lookup"><span data-stu-id="66621-124">Enable or disable ports</span></span>
    - <span data-ttu-id="66621-125">Set-poort modi en eigenschappen</span><span class="sxs-lookup"><span data-stu-id="66621-125">Set port modes and properties</span></span>
    - <span data-ttu-id="66621-126">Toevoegen of koppelen van de VLAN Trunk of toegang op de poort</span><span class="sxs-lookup"><span data-stu-id="66621-126">Add or associate VLAN to Trunk or Access on the port</span></span>

<span data-ttu-id="66621-127">Te verkennen door te zoeken naar alle van de cmdlets NetworkSwitch!</span><span class="sxs-lookup"><span data-stu-id="66621-127">Start exploring by looking for all of the NetworkSwitch cmdlets!</span></span>

```powershell
PS> Get-Command *-NetworkSwitch*

| CommandType | Name                                      | Source        |
|-------------|-------------------------------------------|---------------|
|             |                                           |               |
| Function    | Disable-NetworkSwitchEthernetPort         | NetworkSwitch |
| Function    | Disable-NetworkSwitchFeature              | NetworkSwitch |
| Function    | Disable-NetworkSwitchVlan                 | NetworkSwitch |
| Function    | Enable-NetworkSwitchEthernetPort          | NetworkSwitch |
| Function    | Enable-NetworkSwitchFeature               | NetworkSwitch |
| Function    | Enable-NetworkSwitchVlan                  | NetworkSwitch |
| Function    | Get-NetworkSwitchEthernetPort             | NetworkSwitch |
| Function    | Get-NetworkSwitchFeature                  | NetworkSwitch |
| Function    | Get-NetworkSwitchGlobalData               | NetworkSwitch |
| Function    | Get-NetworkSwitchVlan                     | NetworkSwitch |
| Function    | New-NetworkSwitchVlan                     | NetworkSwitch |
| Function    | Remove-NetworkSwitchEthernetPortIPAddress | NetworkSwitch |
| Function    | Remove-NetworkSwitchVlan                  | NetworkSwitch |
| Function    | Restore-NetworkSwitchConfiguration        | NetworkSwitch |
| Function    | Save-NetworkSwitchConfiguration           | NetworkSwitch |
| Function    | Set-NetworkSwitchEthernetPortIPAddress    | NetworkSwitch |
| Function    | Set-NetworkSwitchPortMode                 | NetworkSwitch |
| Function    | Set-NetworkSwitchPortProperty             | NetworkSwitch |
| Function    | Set-NetworkSwitchVlanProperty             | NetworkSwitch |
```

<span data-ttu-id="66621-128">Meer informatie vindt u in de Jeffrey Snover WMF 5.0 Preview aankondiging blogbericht: <http://blogs.technet.com/b/windowsserver/archive/2014/04/03/windows-management-framework-v5-preview.aspx></span><span class="sxs-lookup"><span data-stu-id="66621-128">More information is available in Jeffrey Snover’s WMF 5.0 Preview announcement blog post: <http://blogs.technet.com/b/windowsserver/archive/2014/04/03/windows-management-framework-v5-preview.aspx></span></span>

