---
ms.date: 06/12/2017
keywords: wmf,powershell,installeren
ms.openlocfilehash: 61c5df1b64cb9c54f9c7372a56e77abf319658dd
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 02/03/2019
ms.locfileid: "55683763"
---
# <a name="network-switch-management-with-powershell"></a>Beheer van netwerkswitch met PowerShell

De **Get-NetworkSwitchEthernetPort** cmdlet retourneert nu de volgende aanvullende informatie met exemplaren:

- IP-adres – het IP-adres dat is gekoppeld aan de poort
- PortMode: de poortmodus: toegang, route of trunk
- AccessVLAN – de de VLAN-ID die is gekoppeld aan deze poort in de toegangsmodus
- TrunkedVLANList: een lijst met id's van VLAN's die zijn gekoppeld aan deze poort in de trunkmodus

## <a name="fundamental-network-switch-management-with-windows-powershell"></a>Fundamentele beheer van netwerkswitch met Windows PowerShell

De netwerkswitch-cmdlets die zijn geïntroduceerd in WMF 5.0, kunt u switch, virtuele LAN (VLAN) en basic Layer 2-switch-poort netwerkconfiguratie toepassen op Windows Server 2012 R2-logo gecertificeerde netwerkswitches. Microsoft blijft doorgevoerd op de ondersteuning van de [Datacenter Abstraction](http://technet.microsoft.com/cloud/dal.aspx) visie Layer (DAL), en om weer te geven waarde voor onze klanten en partners in deze ruimte. Met deze cmdlets die u kunt uitvoeren:

- Globale switch configuratie, zoals:
    - Set-hostnaam
    - Set-switch banner
    - Configuratie blijven behouden
    - Functie- of uitschakelen

- VLAN-configuratie:
    - Maken of verwijderen van VLAN
    - In- of uitschakelen van VLAN
    - VLAN opsommen
    - Beschrijvende naam van de set met een VLAN

- Configuratie van de laag-2-poort:
    - Poorten inventariseren
    - In- of uitschakelen van poorten
    - Set-poort-modi en eigenschappen
    - Toevoegen of koppelen van de VLAN Trunk of toegang op de poort

Beginnen met het verkennen door te zoeken naar alle van de cmdlets systeemtaak!

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

Meer informatie is beschikbaar in Jeffrey Snover van WMF 5.0 Preview aankondiging blogpost: <http://blogs.technet.com/b/windowsserver/archive/2014/04/03/windows-management-framework-v5-preview.aspx>
