---
ms.date: 06/12/2017
author: JKeithB
ms.topic: reference
keywords: wmf,powershell,installeren
ms.openlocfilehash: 2b6b81d250c3d745f3ab21ebadb9a657583638b0
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 04/09/2018
---
# <a name="network-switch-management-with-powershell"></a><span data-ttu-id="3eb58-102">Beheer van netwerkswitch met PowerShell</span><span class="sxs-lookup"><span data-stu-id="3eb58-102">Network Switch Management with PowerShell</span></span>

<span data-ttu-id="3eb58-103">De **Get-NetworkSwitchEthernetPort** cmdlet retourneert nu de volgende aanvullende informatie met exemplaren:</span><span class="sxs-lookup"><span data-stu-id="3eb58-103">The **Get-NetworkSwitchEthernetPort** cmdlet now returns the following additional information with instances:</span></span>

- <span data-ttu-id="3eb58-104">IP-adres – het IP-adres die zijn gekoppeld aan de poort</span><span class="sxs-lookup"><span data-stu-id="3eb58-104">IPAddress – the IP address associated with the port</span></span>
- <span data-ttu-id="3eb58-105">PortMode: de poortmodus: toegang, route of trunk</span><span class="sxs-lookup"><span data-stu-id="3eb58-105">PortMode – the port mode: access, route, or trunk</span></span>
- <span data-ttu-id="3eb58-106">AccessVLAN – de de VLAN-ID die is gekoppeld aan deze poort in de toegangsmodus</span><span class="sxs-lookup"><span data-stu-id="3eb58-106">AccessVLAN – the ID of the VLAN associated with this port in access mode</span></span>
- <span data-ttu-id="3eb58-107">TrunkedVLANList – een lijst met de id van VLAN's die zijn gekoppeld aan deze poort in de trunkmodus</span><span class="sxs-lookup"><span data-stu-id="3eb58-107">TrunkedVLANList – a list of IDs of VLANs associated with this port in trunk mode</span></span>

## <a name="fundamental-network-switch-management-with-windows-powershell"></a><span data-ttu-id="3eb58-108">Fundamentele netwerkbeheer switch met Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="3eb58-108">Fundamental network switch management with Windows PowerShell</span></span>

<span data-ttu-id="3eb58-109">De netwerkswitch-cmdlets die zijn geïntroduceerd in WMF 5.0, kunt u switch, virtuele LAN (VLAN) en basic Layer 2-switch-poort netwerkconfiguratie van toepassing op Windows Server 2012 R2-logo gecertificeerde netwerkswitches.</span><span class="sxs-lookup"><span data-stu-id="3eb58-109">The Network Switch cmdlets, introduced in WMF 5.0, enable you to apply switch, virtual LAN (VLAN), and basic Layer 2 network switch port configuration to Windows Server 2012 R2 logo-certified network switches.</span></span> <span data-ttu-id="3eb58-110">Microsoft blijft doorgevoerd in de ondersteuning van de [Datacenter Abstraction](http://technet.microsoft.com/cloud/dal.aspx) visie Layer (DAL), en waarde voor onze klanten en partners in deze ruimte weergeven.</span><span class="sxs-lookup"><span data-stu-id="3eb58-110">Microsoft remains committed to supporting the [Datacenter Abstraction](http://technet.microsoft.com/cloud/dal.aspx) Layer (DAL) vision, and to show value for our customers and partners in this space.</span></span> <span data-ttu-id="3eb58-111">Met deze cmdlets kunt u uitvoeren:</span><span class="sxs-lookup"><span data-stu-id="3eb58-111">Using these cmdlets you can perform:</span></span>

- <span data-ttu-id="3eb58-112">Global switch configuratie, zoals:</span><span class="sxs-lookup"><span data-stu-id="3eb58-112">Global switch configuration, such as:</span></span>
    - <span data-ttu-id="3eb58-113">Naam van de host</span><span class="sxs-lookup"><span data-stu-id="3eb58-113">Set host name</span></span>
    - <span data-ttu-id="3eb58-114">Set switch banner</span><span class="sxs-lookup"><span data-stu-id="3eb58-114">Set switch banner</span></span>
    - <span data-ttu-id="3eb58-115">Configuratie blijven behouden</span><span class="sxs-lookup"><span data-stu-id="3eb58-115">Persist configuration</span></span>
    - <span data-ttu-id="3eb58-116">Functie- of uitschakelen</span><span class="sxs-lookup"><span data-stu-id="3eb58-116">Enable or disable feature</span></span>

- <span data-ttu-id="3eb58-117">VLAN-configuratie:</span><span class="sxs-lookup"><span data-stu-id="3eb58-117">VLAN configuration:</span></span>
    - <span data-ttu-id="3eb58-118">Maken of verwijderen van VLAN</span><span class="sxs-lookup"><span data-stu-id="3eb58-118">Create or remove VLAN</span></span>
    - <span data-ttu-id="3eb58-119">In- of uitschakelen van VLAN</span><span class="sxs-lookup"><span data-stu-id="3eb58-119">Enable or disable VLAN</span></span>
    - <span data-ttu-id="3eb58-120">VLAN opsommen</span><span class="sxs-lookup"><span data-stu-id="3eb58-120">Enumerate VLAN</span></span>
    - <span data-ttu-id="3eb58-121">Beschrijvende naam van de set met een VLAN</span><span class="sxs-lookup"><span data-stu-id="3eb58-121">Set friendly name to a VLAN</span></span>

- <span data-ttu-id="3eb58-122">Configuratie van laag 2-poort:</span><span class="sxs-lookup"><span data-stu-id="3eb58-122">Layer 2 port configuration:</span></span>
    - <span data-ttu-id="3eb58-123">Poorten opsommen</span><span class="sxs-lookup"><span data-stu-id="3eb58-123">Enumerate ports</span></span>
    - <span data-ttu-id="3eb58-124">In- of uitschakelen van poorten</span><span class="sxs-lookup"><span data-stu-id="3eb58-124">Enable or disable ports</span></span>
    - <span data-ttu-id="3eb58-125">Set-poort modi en eigenschappen</span><span class="sxs-lookup"><span data-stu-id="3eb58-125">Set port modes and properties</span></span>
    - <span data-ttu-id="3eb58-126">Toevoegen of koppelen van de VLAN Trunk of toegang op de poort</span><span class="sxs-lookup"><span data-stu-id="3eb58-126">Add or associate VLAN to Trunk or Access on the port</span></span>

<span data-ttu-id="3eb58-127">Te verkennen door te zoeken naar alle van de cmdlets NetworkSwitch!</span><span class="sxs-lookup"><span data-stu-id="3eb58-127">Start exploring by looking for all of the NetworkSwitch cmdlets!</span></span>

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

<span data-ttu-id="3eb58-128">Meer informatie is beschikbaar in de Jeffrey Snover WMF 5.0 Preview aankondiging blogbericht: <http://blogs.technet.com/b/windowsserver/archive/2014/04/03/windows-management-framework-v5-preview.aspx></span><span class="sxs-lookup"><span data-stu-id="3eb58-128">More information is available in Jeffrey Snover’s WMF 5.0 Preview announcement blog post: <http://blogs.technet.com/b/windowsserver/archive/2014/04/03/windows-management-framework-v5-preview.aspx></span></span>