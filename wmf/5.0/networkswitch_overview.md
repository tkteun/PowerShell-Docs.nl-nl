---
ms.date: 06/12/2017
keywords: wmf,powershell,installeren
ms.openlocfilehash: 61c5df1b64cb9c54f9c7372a56e77abf319658dd
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62085118"
---
# <a name="network-switch-management-with-powershell"></a><span data-ttu-id="a6b6e-102">Beheer van netwerkswitch met PowerShell</span><span class="sxs-lookup"><span data-stu-id="a6b6e-102">Network Switch Management with PowerShell</span></span>

<span data-ttu-id="a6b6e-103">De **Get-NetworkSwitchEthernetPort** cmdlet retourneert nu de volgende aanvullende informatie met exemplaren:</span><span class="sxs-lookup"><span data-stu-id="a6b6e-103">The **Get-NetworkSwitchEthernetPort** cmdlet now returns the following additional information with instances:</span></span>

- <span data-ttu-id="a6b6e-104">IP-adres – het IP-adres dat is gekoppeld aan de poort</span><span class="sxs-lookup"><span data-stu-id="a6b6e-104">IPAddress – the IP address associated with the port</span></span>
- <span data-ttu-id="a6b6e-105">PortMode: de poortmodus: toegang, route of trunk</span><span class="sxs-lookup"><span data-stu-id="a6b6e-105">PortMode – the port mode: access, route, or trunk</span></span>
- <span data-ttu-id="a6b6e-106">AccessVLAN – de de VLAN-ID die is gekoppeld aan deze poort in de toegangsmodus</span><span class="sxs-lookup"><span data-stu-id="a6b6e-106">AccessVLAN – the ID of the VLAN associated with this port in access mode</span></span>
- <span data-ttu-id="a6b6e-107">TrunkedVLANList: een lijst met id's van VLAN's die zijn gekoppeld aan deze poort in de trunkmodus</span><span class="sxs-lookup"><span data-stu-id="a6b6e-107">TrunkedVLANList – a list of IDs of VLANs associated with this port in trunk mode</span></span>

## <a name="fundamental-network-switch-management-with-windows-powershell"></a><span data-ttu-id="a6b6e-108">Fundamentele beheer van netwerkswitch met Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="a6b6e-108">Fundamental network switch management with Windows PowerShell</span></span>

<span data-ttu-id="a6b6e-109">De netwerkswitch-cmdlets die zijn geïntroduceerd in WMF 5.0, kunt u switch, virtuele LAN (VLAN) en basic Layer 2-switch-poort netwerkconfiguratie toepassen op Windows Server 2012 R2-logo gecertificeerde netwerkswitches.</span><span class="sxs-lookup"><span data-stu-id="a6b6e-109">The Network Switch cmdlets, introduced in WMF 5.0, enable you to apply switch, virtual LAN (VLAN), and basic Layer 2 network switch port configuration to Windows Server 2012 R2 logo-certified network switches.</span></span> <span data-ttu-id="a6b6e-110">Microsoft blijft doorgevoerd op de ondersteuning van de [Datacenter Abstraction](http://technet.microsoft.com/cloud/dal.aspx) visie Layer (DAL), en om weer te geven waarde voor onze klanten en partners in deze ruimte.</span><span class="sxs-lookup"><span data-stu-id="a6b6e-110">Microsoft remains committed to supporting the [Datacenter Abstraction](http://technet.microsoft.com/cloud/dal.aspx) Layer (DAL) vision, and to show value for our customers and partners in this space.</span></span> <span data-ttu-id="a6b6e-111">Met deze cmdlets die u kunt uitvoeren:</span><span class="sxs-lookup"><span data-stu-id="a6b6e-111">Using these cmdlets you can perform:</span></span>

- <span data-ttu-id="a6b6e-112">Globale switch configuratie, zoals:</span><span class="sxs-lookup"><span data-stu-id="a6b6e-112">Global switch configuration, such as:</span></span>
    - <span data-ttu-id="a6b6e-113">Set-hostnaam</span><span class="sxs-lookup"><span data-stu-id="a6b6e-113">Set host name</span></span>
    - <span data-ttu-id="a6b6e-114">Set-switch banner</span><span class="sxs-lookup"><span data-stu-id="a6b6e-114">Set switch banner</span></span>
    - <span data-ttu-id="a6b6e-115">Configuratie blijven behouden</span><span class="sxs-lookup"><span data-stu-id="a6b6e-115">Persist configuration</span></span>
    - <span data-ttu-id="a6b6e-116">Functie- of uitschakelen</span><span class="sxs-lookup"><span data-stu-id="a6b6e-116">Enable or disable feature</span></span>

- <span data-ttu-id="a6b6e-117">VLAN-configuratie:</span><span class="sxs-lookup"><span data-stu-id="a6b6e-117">VLAN configuration:</span></span>
    - <span data-ttu-id="a6b6e-118">Maken of verwijderen van VLAN</span><span class="sxs-lookup"><span data-stu-id="a6b6e-118">Create or remove VLAN</span></span>
    - <span data-ttu-id="a6b6e-119">In- of uitschakelen van VLAN</span><span class="sxs-lookup"><span data-stu-id="a6b6e-119">Enable or disable VLAN</span></span>
    - <span data-ttu-id="a6b6e-120">VLAN opsommen</span><span class="sxs-lookup"><span data-stu-id="a6b6e-120">Enumerate VLAN</span></span>
    - <span data-ttu-id="a6b6e-121">Beschrijvende naam van de set met een VLAN</span><span class="sxs-lookup"><span data-stu-id="a6b6e-121">Set friendly name to a VLAN</span></span>

- <span data-ttu-id="a6b6e-122">Configuratie van de laag-2-poort:</span><span class="sxs-lookup"><span data-stu-id="a6b6e-122">Layer 2 port configuration:</span></span>
    - <span data-ttu-id="a6b6e-123">Poorten inventariseren</span><span class="sxs-lookup"><span data-stu-id="a6b6e-123">Enumerate ports</span></span>
    - <span data-ttu-id="a6b6e-124">In- of uitschakelen van poorten</span><span class="sxs-lookup"><span data-stu-id="a6b6e-124">Enable or disable ports</span></span>
    - <span data-ttu-id="a6b6e-125">Set-poort-modi en eigenschappen</span><span class="sxs-lookup"><span data-stu-id="a6b6e-125">Set port modes and properties</span></span>
    - <span data-ttu-id="a6b6e-126">Toevoegen of koppelen van de VLAN Trunk of toegang op de poort</span><span class="sxs-lookup"><span data-stu-id="a6b6e-126">Add or associate VLAN to Trunk or Access on the port</span></span>

<span data-ttu-id="a6b6e-127">Beginnen met het verkennen door te zoeken naar alle van de cmdlets systeemtaak!</span><span class="sxs-lookup"><span data-stu-id="a6b6e-127">Start exploring by looking for all of the NetworkSwitch cmdlets!</span></span>

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

<span data-ttu-id="a6b6e-128">Meer informatie is beschikbaar in Jeffrey Snover van WMF 5.0 Preview aankondiging blogpost: <http://blogs.technet.com/b/windowsserver/archive/2014/04/03/windows-management-framework-v5-preview.aspx></span><span class="sxs-lookup"><span data-stu-id="a6b6e-128">More information is available in Jeffrey Snover’s WMF 5.0 Preview announcement blog post: <http://blogs.technet.com/b/windowsserver/archive/2014/04/03/windows-management-framework-v5-preview.aspx></span></span>
