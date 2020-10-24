---
ms.date: 12/23/2019
keywords: powershell,cmdlet
title: Netwerktaken uitvoeren
description: In dit artikel wordt beschreven hoe u WMI-klassen in Power shell gebruikt voor het beheren van de netwerk configuratie-instelling in Windows.
ms.openlocfilehash: 95b05c193f4168cdcdf8414399c4f8c569bff754
ms.sourcegitcommit: 9080316e3ca4f11d83067b41351531672b667b7a
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/24/2020
ms.locfileid: "92500246"
---
# <a name="performing-networking-tasks"></a>Netwerktaken uitvoeren

Omdat TCP/IP het meest gebruikte netwerk protocol is, zijn voor de meeste netwerk protocol beheer taken op laag niveau TCP/IP vereist. In deze sectie gebruiken we Power shell en WMI om deze taken uit te voeren.

## <a name="listing-ip-addresses-for-a-computer"></a>IP-adressen voor een computer weer geven

Als u alle IP-adressen die in gebruik zijn op de lokale computer wilt ophalen, gebruikt u de volgende opdracht:

```powershell
 Get-CimInstance -Class Win32_NetworkAdapterConfiguration -Filter IPEnabled=$true |
  Select-Object -ExpandProperty IPAddress
```

De uitvoer van deze opdracht wijkt af van de meeste eigenschappen lijsten, omdat waarden tussen accolades worden geplaatst:

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

Als u wilt weten waarom de accolades worden weer gegeven, gebruikt u de `Get-Member` cmdlet om de eigenschap **IPAddress** te controleren:

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

De eigenschap IPAddress voor elke netwerk adapter is in feite een matrix. De accolades in de definitie geven aan dat **IPAddress** geen **System. String** -waarde, maar een matrix van **System. String** -waarden is.

## <a name="listing-ip-configuration-data"></a>IP-configuratie gegevens weer geven

Als u gedetailleerde IP-configuratie gegevens voor elke netwerk adapter wilt weer geven, gebruikt u de volgende opdracht:

```powershell
Get-CimInstance -Class Win32_NetworkAdapterConfiguration -Filter IPEnabled=$true
```

De standaard weergave voor het configuratie object voor de netwerk adapter is een zeer kleinere set beschik bare informatie. Gebruik `Select-Object` of een opmaak-cmdlet, zoals `Format-List` , om de eigenschappen op te geven die moeten worden weer gegeven voor uitgebreide inspectie en probleem oplossing.

In moderne TCP/IP-netwerken bent u waarschijnlijk niet geïnteresseerd in IPX-of WINS-eigenschappen. U kunt de para meter **ExcludeProperty** van gebruiken `Select-Object` om eigenschappen te verbergen met namen die beginnen met "WINS" of "IPX".

```powershell
Get-CimInstance -Class Win32_NetworkAdapterConfiguration -Filter IPEnabled=$true |
  Select-Object -ExcludeProperty IPX*,WINS*
```

Met deze opdracht wordt gedetailleerde informatie geretourneerd over DHCP, DNS, route ring en andere eigenschappen van een secundaire IP-configuratie.

## <a name="pinging-computers"></a>Computers pingen

U kunt een eenvoudige ping uitvoeren op een computer met behulp van **Win32_PingStatus**. De volgende opdracht voert de ping uit, maar retourneert een langdurige uitvoer:

```powershell
Get-CimInstance -Class Win32_PingStatus -Filter "Address='127.0.0.1'"
```

Een handiger formulier voor samen vattingen geeft een weer gave van de eigenschappen Address, respons tijd en status code, zoals wordt gegenereerd door de volgende opdracht. De para meter **AutoSize** van `Format-Table` het formaat van de tabel kolommen wijzigen zodat deze correct worden weer gegeven in Power shell.

```powershell
Get-CimInstance -Class Win32_PingStatus -Filter "Address='127.0.0.1'" |
  Format-Table -Property Address,ResponseTime,StatusCode -Autosize
```

```Output
Address   ResponseTime StatusCode
-------   ------------ ----------
127.0.0.1            0          0
```

Een status code van 0 geeft aan dat de ping is geslaagd.

U kunt een matrix gebruiken om meerdere computers te pingen met één opdracht. Omdat er meer dan één adres is, gebruikt `ForEach-Object` u de om elk adres afzonderlijk te pingen:

```powershell
'127.0.0.1','localhost','research.microsoft.com' |
  ForEach-Object -Process {
    Get-CimInstance -Class Win32_PingStatus -Filter ("Address='$_'") |
      Select-Object -Property Address,ResponseTime,StatusCode
  }
```

U kunt dezelfde opdracht indeling gebruiken voor het pingen van alle computers in een subnet, zoals een particulier netwerk dat gebruikmaakt van netwerk nummer 192.168.1.0 en een standaard klasse C-subnetmasker (255.255.255.0). alleen adressen in het bereik van 192.168.1.1 tot en met 192.168.1.254 zijn legitieme lokale adressen (0 is altijd gereserveerd voor het netwerk nummer en 255 is een subnet-broadcast adres).

Als u een matrix van de getallen 1 tot en met 254 in Power shell wilt weer geven, gebruikt u de instructie **1.. 254.**
Een volledige ping van het subnet kan worden uitgevoerd door de matrix te genereren en vervolgens de waarden toe te voegen aan een gedeeltelijk adres in de instructie ping:

```powershell
1..254| ForEach-Object -Process {
  Get-CimInstance -Class Win32_PingStatus -Filter ("Address='192.168.1.$_ '") } |
    Select-Object -Property Address,ResponseTime,StatusCode
```

Houd er rekening mee dat deze techniek voor het genereren van een bereik van adressen ook elders kan worden gebruikt. Op deze manier kunt u een volledige set adressen genereren:

```powershell
$ips = 1..254 | ForEach-Object -Process {'192.168.1.' + $_}
```

## <a name="retrieving-network-adapter-properties"></a>Eigenschappen van de netwerk adapter ophalen

Eerder werd geadviseerd dat u de algemene configuratie-eigenschappen kunt ophalen met behulp van de **Win32_NetworkAdapterConfiguration** -klasse. Hoewel dit geen strikte TCP/IP-informatie is, kunnen gegevens van netwerk adapters, zoals MAC-adressen en adapter typen, handig zijn om te zien wat er gebeurt met een computer. Gebruik de volgende opdracht om een overzicht van deze informatie te krijgen:

```powershell
Get-CimInstance -Class Win32_NetworkAdapter -ComputerName .
```

## <a name="assigning-the-dns-domain-for-a-network-adapter"></a>Toewijzing van het DNS-domein voor een netwerk adapter

Als u het DNS-domein voor automatische naam omzetting wilt toewijzen, gebruikt u de methode **SetDNSDomain** van de **Win32_NetworkAdapterConfiguration**. Omdat u het DNS-domein voor elke configuratie van de netwerk adapter afzonderlijk toewijst, moet u een `ForEach-Object` instructie gebruiken om het domein toe te wijzen aan elke adapter:

```powershell
Get-CimInstance -Class Win32_NetworkAdapterConfiguration -Filter IPEnabled=$true |
  ForEach-Object -Process { $_.SetDNSDomain('fabrikam.com') }
```

De filter `IPEnabled=$true` -instructie is nodig, omdat zelfs in een netwerk dat alleen TCP/IP gebruikt, geen gebruik wordt gemaakt van TCP/IP-adapters op een computer. Dit zijn algemene software-elementen die RAS-, PPTP-, QoS-en andere services ondersteunen voor alle adapters, en hebben dus geen eigen adres.

U kunt de opdracht filteren met behulp `Where-Object` van de-cmdlet, in plaats van het filter te gebruiken `Get-CimInstance` .

```powershell
Get-CimInstance -Class Win32_NetworkAdapterConfiguration |
  Where-Object {$_.IPEnabled} |
    ForEach-Object -Process {$_.SetDNSDomain('fabrikam.com')}
```

## <a name="performing-dhcp-configuration-tasks"></a>DHCP-configuratie taken uitvoeren

Bij het wijzigen van DHCP-details moet u werken met een set netwerk adapters, net zoals de DNS-configuratie. Er zijn verschillende acties die u kunt uitvoeren met behulp van WMI, en we gaan door een aantal van de gemeen schappelijke stappen.

### <a name="determining-dhcp-enabled-adapters"></a>DHCP-Enabled adapters bepalen

Als u de DHCP-adapters op een computer wilt zoeken, gebruikt u de volgende opdracht:

```powershell
Get-CimInstance -Class Win32_NetworkAdapterConfiguration -Filter "DHCPEnabled=$true"
```

Als u adapters wilt uitsluiten met IP-configuratie problemen, kunt u alleen adapters met IP-functionaliteit ophalen:

```powershell
Get-CimInstance -Class Win32_NetworkAdapterConfiguration -Filter "IPEnabled=$true and DHCPEnabled=$true"
```

### <a name="retrieving-dhcp-properties"></a>DHCP-eigenschappen ophalen

Omdat aan DHCP gerelateerde eigenschappen voor een adapter doorgaans beginnen met `DHCP` , kunt u de eigenschaps parameter van gebruiken `Format-Table` om alleen die eigenschappen weer te geven:

```powershell
Get-CimInstance -Class Win32_NetworkAdapterConfiguration -Filter "DHCPEnabled=$true" |
  Format-Table -Property DHCP*
```

### <a name="enabling-dhcp-on-each-adapter"></a>DHCP inschakelen op elke adapter

Als u DHCP op alle adapters wilt inschakelen, gebruikt u de volgende opdracht:

```powershell
Get-CimInstance -Class Win32_NetworkAdapterConfiguration -Filter IPEnabled=$true |
  ForEach-Object -Process {$_.EnableDHCP()}
```

U kunt de **filter** -instructie gebruiken `IPEnabled=$true and DHCPEnabled=$false` om te voor komen dat DHCP wordt ingeschakeld, maar als deze stap wordt wegge laten, worden er geen fouten veroorzaakt.

### <a name="releasing-and-renewing-dhcp-leases-on-specific-adapters"></a>DHCP-leases op specifieke adapters vrijgeven en vernieuwen

De klasse **Win32_NetworkAdapterConfiguration** heeft **ReleaseDHCPLease** -en **RenewDHCPLease** -methoden. Beide worden op dezelfde manier gebruikt. In het algemeen gebruikt u deze methoden als u alleen adressen voor een adapter op een specifiek subnet hoeft vrij te geven of te vernieuwen. De eenvoudigste manier om adapters op een subnet te filteren, is door alleen de adapter configuraties te kiezen die gebruikmaken van de gateway voor dat subnet. Met de volgende opdracht worden bijvoorbeeld alle DHCP-leases vrijgegeven op adapters op de lokale computer die DHCP-leases verkrijgen van 192.168.1.254:

```powershell
Get-CimInstance -Class Win32_NetworkAdapterConfiguration -Filter "IPEnabled=$true and DHCPEnabled=$true" |
  Where-Object {$_.DHCPServer -contains '192.168.1.254'} |
    ForEach-Object -Process {$_.ReleaseDHCPLease()}
```

De enige wijziging voor het vernieuwen van een DHCP-lease is het gebruik van de methode **RenewDHCPLease** in plaats van de methode **ReleaseDHCPLease** :

```powershell
Get-CimInstance -Class Win32_NetworkAdapterConfiguration -Filter "IPEnabled=$true and DHCPEnabled=$true" |
  Where-Object {$_.DHCPServer -contains '192.168.1.254'} |
    ForEach-Object -Process {$_.ReleaseDHCPLease()}
```

> [!NOTE]
> Wanneer u deze methoden op een externe computer gebruikt, moet u er rekening mee houden dat u de toegang tot het externe systeem kunt verliezen als u er met de adapter met de uitgebrachte of verlengde lease mee verbonden bent.

### <a name="releasing-and-renewing-dhcp-leases-on-all-adapters"></a>DHCP-leases op alle adapters vrijgeven en vernieuwen

U kunt algemene DHCP-adres releases of-vernieuwingen uitvoeren op alle adapters met behulp van de **Win32_NetworkAdapterConfiguration** methoden **ReleaseDHCPLeaseAll** en **RenewDHCPLeaseAll**.
De opdracht moet echter wel van toepassing zijn op de WMI-klasse in plaats van een bepaalde adapter, omdat leases die wereld wijd worden vrijgegeven en vernieuwen, worden uitgevoerd op de klasse, niet op een specifieke adapter.

U kunt een verwijzing naar een WMI-klasse verkrijgen in plaats van klasse-instanties door alle WMI-klassen weer te geven en vervolgens alleen de gewenste klasse op naam te selecteren. Met de volgende opdracht wordt bijvoorbeeld de **Win32_NetworkAdapterConfiguration** -klasse geretourneerd:

```powershell
Get-CimInstance -List | Where-Object {$_.Name -eq 'Win32_NetworkAdapterConfiguration'}
```

U kunt de volledige opdracht beschouwen als de klasse en vervolgens de **ReleaseDHCPAdapterLease** -methode aanroepen. In de volgende opdracht worden de haakjes rondom de `Get-CimInstance` en `Where-Object` pijplijn elementen direct Power shell uitgevoerd om ze eerst te evalueren:

```powershell
(Get-CimInstance -List |
  Where-Object {$_.Name -eq 'Win32_NetworkAdapterConfiguration'}).ReleaseDHCPLeaseAll()
```

U kunt dezelfde opdracht indeling gebruiken om de **RenewDHCPLeaseAll** -methode aan te roepen:

```powershell
(Get-CimInstance -List |
  Where-Object {$_.Name -eq 'Win32_NetworkAdapterConfiguration'}).RenewDHCPLeaseAll()
```

## <a name="creating-a-network-share"></a>Een netwerk share maken

Als u een netwerk share wilt maken, gebruikt u de methode **Create** van **Win32_Share**:

```powershell
(Get-CimInstance -List |
  Where-Object {$_.Name -eq 'Win32_Share'}).Create(
    'C:\temp','TempShare',0,25,'test share of the temp folder'
  )
```

U kunt de share ook maken met behulp van `net share` in Power shell in Windows:

```powershell
net share tempshare=c:\temp /users:25 /remark:"test share of the temp folder"
```

## <a name="removing-a-network-share"></a>Een netwerk share verwijderen

U kunt een netwerk share met **Win32_Share**verwijderen, maar het proces wijkt enigszins af van het maken van een share, omdat u de specifieke share moet ophalen die moet worden verwijderd, in plaats van de **Win32_Share** klasse. Met de volgende instructie wordt de share **TempShare**verwijderd:

```powershell
(Get-CimInstance -Class Win32_Share -Filter "Name='TempShare'").Delete()
```

In Windows `net share` werkt ook het volgende:

```powershell
net share tempshare /delete
```

```Output
tempshare was deleted successfully.
```

## <a name="connecting-a-windows-accessible-network-drive"></a>Verbinding maken met een met Windows toegankelijk netwerk station

De `New-PSDrive` cmdlets maken een Power Shell-station, maar stations die op deze manier zijn gemaakt, zijn alleen beschikbaar voor Power shell. Als u een nieuw netwerk station wilt maken, kunt u het object **WScript. Network** com gebruiken. Met de volgende opdracht wordt de share toegewezen `\\FPS01\users` aan een lokaal station `B:` ,

```powershell
(New-Object -ComObject WScript.Network).MapNetworkDrive('B:', '\\FPS01\users')
```

In Windows werkt de `net use` opdracht ook als volgt:

```powershell
net use B: \\FPS01\users
```

Stations die zijn toegewezen met **WScript. Network** of `net use` die onmiddellijk beschikbaar zijn voor Power shell.
