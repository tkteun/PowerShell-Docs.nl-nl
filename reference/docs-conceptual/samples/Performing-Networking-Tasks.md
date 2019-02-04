---
ms.date: 06/05/2017
keywords: PowerShell-cmdlet
title: Netwerktaken uitvoeren
ms.assetid: a43cc55f-70c1-45c8-9467-eaad0d57e3b5
ms.openlocfilehash: 64c57c95a70bc4cad4b695a59d96673ed18afdf4
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 02/03/2019
ms.locfileid: "55688243"
---
# <a name="performing-networking-tasks"></a>Netwerktaken uitvoeren

Omdat TCP/IP het meest gebruikte protocol is, worden de meeste beheertaken van laag niveau netwerk-protocol TCP/IP. In deze sectie gebruiken we Windows PowerShell en WMI voor deze taken.

### <a name="listing-ip-addresses-for-a-computer"></a>IP-adressen weergeven voor een Computer

Als u alle IP-adressen in gebruik is op de lokale computer, gebruikt u de volgende opdracht uit:

```powershell
Get-WmiObject -Class Win32_NetworkAdapterConfiguration -Filter IPEnabled=$true -ComputerName . | Format-Table -Property IPAddress
```

De uitvoer van deze opdracht wijkt af van de meeste lijsten met zoekeigenschappen omdat waarden zijn tussen accolades:

```output
IPAddress
---------
{192.168.1.80}
{192.168.148.1}
{192.168.171.1}
{0.0.0.0}
```

Om te begrijpen waarom de accolades worden weergegeven, gebruikt u de cmdlet Get-Member het onderzoeken van de **IPAddress** eigenschap:

```
PS> Get-WmiObject -Class Win32_NetworkAdapterConfiguration -Filter IPEnabled=$true -ComputerName . | Get-Member -Name IPAddress


TypeName: System.Management.ManagementObject#root\cimv2\Win32_NetworkAdapterConfiguration

Name      MemberType Definition
----      ---------- ----------
IPAddress Property   System.String[] IPAddress {get;}
```

De eigenschap IP-adres voor elke netwerkadapter is eigenlijk een matrix. De accolades in het definitie geven aan dat **IPAddress** is niet een **System.String** waarde, maar een matrix met **System.String** waarden.

### <a name="listing-ip-configuration-data"></a>IP-configuratiegegevens van aanbieding

Als gedetailleerde IP-configuratiegegevens voor elke netwerkadapter weergeven, gebruikt u de volgende opdracht uit:

```powershell
Get-WmiObject -Class Win32_NetworkAdapterConfiguration -Filter IPEnabled=$true -ComputerName .
```

De standaardweergave voor het object network adapter configuratie is een zeer beperkte set van de beschikbare informatie. Gebruik voor uitgebreide controle en probleemoplossing, Select-Object of een opmaak cmdlet, zoals indeling-lijst om op te geven van de eigenschappen die moeten worden weergegeven.

Als u niet geïnteresseerd in de eigenschappen van IPX- of WINS bent, waarschijnlijk het geval in een moderne TCP/IP-netwerk, kunt u de parameter ExcludeProperty van Select-Object te verbergen eigenschappen met namen die met "WINS beginnen" of "IPX:"

```powershell
Get-WmiObject -Class Win32_NetworkAdapterConfiguration -Filter IPEnabled=$true -ComputerName . | Select-Object -Property [a-z]* -ExcludeProperty IPX*,WINS*
```

Met deze opdracht retourneert gedetailleerde informatie over DHCP, DNS, Routering en andere secundaire IP-configuratie-eigenschappen.

### <a name="pinging-computers"></a>Pingen naar Computers

U kunt een eenvoudige ping uit voor een computer met behulp van uitvoeren **Win32_PingStatus**. De volgende opdracht de opdracht ping wordt uitgevoerd, maar retourneert uitgebreide uitvoer:

```powershell
Get-WmiObject -Class Win32_PingStatus -Filter "Address='127.0.0.1'" -ComputerName .
```

Nog meer nuttige formulier samenvattende informatie weergegeven in een van de eigenschappen van het adres, de responstijd en de StatusCode, zoals die worden gegenereerd door de volgende opdracht uit. De parameter Autosize van Format-Table vergroot/verkleint de kolommen in de tabel zodat ze goed worden weergegeven in Windows PowerShell.

```
PS> Get-WmiObject -Class Win32_PingStatus -Filter "Address='127.0.0.1'" -ComputerName . | Format-Table -Property Address,ResponseTime,StatusCode -Autosize

Address   ResponseTime StatusCode
-------   ------------ ----------
127.0.0.1            0          0
```

Een StatusCode van 0 geeft aan dat een geslaagde ping.

Een matrix kunt u meerdere computers met slechts één opdracht ping. Omdat er meer dan één adres, gebruiken de **ForEach-Object** afzonderlijk pingt u elk adres:

```powershell
'127.0.0.1','localhost','research.microsoft.com' | ForEach-Object -Process {Get-WmiObject -Class Win32_PingStatus -Filter ("Address='" + $_ + "'") -ComputerName .} | Select-Object -Property Address,ResponseTime,StatusCode
```

U kunt de opdrachtindeling van dezelfde gebruiken om te pingen alle computers in een subnet, zoals een particulier netwerk die gebruikmaakt van nummer 192.168.1.0 van het netwerk en een standaard-klasse C-subnetmasker (255.255.255.0)., worden alleen de adressen binnen het bereik van 192.168.1.1 via 192.168.1.254 goedaardige lokale adressen (0 is altijd gereserveerd voor het nummer van het netwerk en 255 is een subnet broadcast-adres).

Om weer te geven een matrix van de getallen van 1 tot 254 in Windows PowerShell, gebruikt u de instructie **1..254.** Een ping voltooid subnet kan worden uitgevoerd door het genereren van de matrix en vervolgens de waarden naar een gedeeltelijke adres toe te voegen in de ping-instructie:

```powershell
1..254| ForEach-Object -Process {Get-WmiObject -Class Win32_PingStatus -Filter ("Address='192.168.1." + $_ + "'") -ComputerName .} | Select-Object -Property Address,ResponseTime,StatusCode
```

Houd er rekening mee dat deze techniek voor het genereren van een bereik van adressen elders kan worden gebruikt. Op deze manier kunt u een volledige set adressen genereren:

```powershell
$ips = 1..254 | ForEach-Object -Process {'192.168.1.' + $_}
```

### <a name="retrieving-network-adapter-properties"></a>Bij het ophalen van eigenschappen van netwerkadapter

Eerder in deze handleiding, hebben we al gemeld dat u algemene configuratie-eigenschappen ophalen met behulp van kan **Win32_NetworkAdapterConfiguration**. Hoewel dit strikt genomen TCP/IP-informatie, netwerkadapterinformatie, zoals MAC-adressen en typen netwerkadapters kunnen nuttig zijn om te begrijpen wat er gebeurt met een computer zijn. Als u een overzicht van deze informatie, gebruikt u de volgende opdracht uit:

```powershell
Get-WmiObject -Class Win32_NetworkAdapter -ComputerName .
```

### <a name="assigning-the-dns-domain-for-a-network-adapter"></a>De DNS-domein toewijzen voor een netwerkadapter

Als u wilt toewijzen van de DNS-domein voor het omzetten van automatische, gebruikt u de **Win32_NetworkAdapterConfiguration SetDNSDomain** methode. Omdat u de DNS-domein voor de configuratie van elke netwerkadapter afzonderlijk toewijst, moet u een **ForEach-Object** instructie het domein toewijzen aan elke adapter:

```powershell
Get-WmiObject -Class Win32_NetworkAdapterConfiguration -Filter IPEnabled=$true -ComputerName . | ForEach-Object -Process { $_. SetDNSDomain('fabrikam.com') }
```

De instructie filteren ' IPEnabled $true = "is nodig omdat zelfs op een netwerk dat gebruikmaakt van alleen TCP/IP, verschillende configuraties van de netwerkadapters op een computer niet TCP/IP-adapters, ' True '; Deze algemene software-elementen ter ondersteuning van RAS, PPTP, QoS en andere services voor alle adapters zijn en dus niet een adres van hun eigen over.

U kunt de opdracht filteren met behulp van de **Where-Object** cmdlet, in plaats van de **Get-WmiObject** filter.

```powershell
Get-WmiObject -Class Win32_NetworkAdapterConfiguration -ComputerName . | Where-Object -FilterScript {$_.IPEnabled} | ForEach-Object -Process {$_.SetDNSDomain('fabrikam.com')}
```

### <a name="performing-dhcp-configuration-tasks"></a>DHCP-uitvoeren configuratietaken

Wijzigen van de DHCP-informatie omvat het werken met een set netwerkadapters, net als de DNS-configuratie. Er zijn verschillende afzonderlijke acties die u uitvoeren kunt met behulp van WMI en we enkele van de algemene die gegevensbronnen wordt doorlopen.

#### <a name="determining-dhcp-enabled-adapters"></a>DHCP ingeschakeld Adapters bepalen

Als u zoekt de adapters DHCP-functionaliteit op een computer, gebruik de volgende opdracht:

```powershell
Get-WmiObject -Class Win32_NetworkAdapterConfiguration -Filter "DHCPEnabled=$true" -ComputerName .
```

Als u wilt uitsluiten van netwerkadapters met IP-configuratie oplossen, kunt u alleen IP-functionaliteit adapters ophalen:

```powershell
Get-WmiObject -Class Win32_NetworkAdapterConfiguration -Filter "IPEnabled=$true and DHCPEnabled=$true" -ComputerName .
```

#### <a name="retrieving-dhcp-properties"></a>Bij het ophalen van DHCP-eigenschappen

Omdat DHCP-eigenschappen voor een adapter met algemeen begint met 'DHCP', kunt u de parameter eigenschap van Format-Table kunt gebruiken om alleen de eigenschappen weer te geven:

```powershell
Get-WmiObject -Class Win32_NetworkAdapterConfiguration -Filter "DHCPEnabled=$true" -ComputerName . | Format-Table -Property DHCP*
```

#### <a name="enabling-dhcp-on-each-adapter"></a>DHCP op elke Adapter inschakelen

Om in te schakelen DHCP op alle netwerkadapters, gebruik de volgende opdracht:

```powershell
Get-WmiObject -Class Win32_NetworkAdapterConfiguration -Filter IPEnabled=$true -ComputerName . | ForEach-Object -Process {$_.EnableDHCP()}
```

U kunt de **Filter** instructie ' IPEnabled = $true en DHCPEnabled $false = "om te voorkomen dat het inschakelen van DHCP waar deze al is ingeschakeld, maar als deze stap niet leiden tot fouten.

#### <a name="releasing-and-renewing-dhcp-leases-on-specific-adapters"></a>Vrijgeven en DHCP-Leases op specifieke netwerkadapters te vernieuwen

De **Win32_NetworkAdapterConfiguration** klasse heeft **ReleaseDHCPLease** en **RenewDCHPLease** methoden. Beide worden op dezelfde manier gebruikt. In het algemeen deze methoden gebruiken als u alleen wilt vrijgeven of vernieuwen van adressen voor een adapter op een specifiek subnet. De eenvoudigste manier om filter-adapters in een subnet is de adapterconfiguraties die gebruikmaken van de gateway voor dat subnet kiezen. De volgende opdracht worden bijvoorbeeld alle DHCP-leases op netwerkadapters op de lokale computer die zijn het verkrijgen van DHCP-leases van 192.168.1.254 vrijgegeven:

```powershell
Get-WmiObject -Class Win32_NetworkAdapterConfiguration -Filter "IPEnabled=$true and DHCPEnabled=$true" -ComputerName . | Where-Object -FilterScript {$_.DHCPServer -contains '192.168.1.254'} | ForEach-Object -Process {$_.ReleaseDHCPLease()}
```

De enige wijziging voor het vernieuwen van een DHCP-lease is het gebruik van de **RenewDCHPLease** methode in plaats van de **ReleaseDHCPLease** methode:

```powershell
Get-WmiObject -Class Win32_NetworkAdapterConfiguration -Filter "IPEnabled=$true and DHCPEnabled=$true" -ComputerName . | Where-Object -FilterScript {$_.DHCPServer -contains '192.168.1.254'} | ForEach-Object -Process {$_.ReleaseDHCPLease()}
```

> [!NOTE]
> Wanneer u deze methoden op een externe computer, er rekening mee dat u kunt geen toegang meer tot het externe systeem als u met het via de adapter met de lease vrijgegeven of vernieuwd verbonden bent.

#### <a name="releasing-and-renewing-dhcp-leases-on-all-adapters"></a>Vrijgeven en vernieuwen van DHCP-Leases op alle netwerkadapters

U kunt globale releases van DHCP-adres of vernieuwingen op alle netwerkadapters uitvoeren met behulp van de **Win32_NetworkAdapterConfiguration** methoden, **ReleaseDHCPLeaseAll** en **RenewDCHPLeaseAll** . Echter, de opdracht moet toepassen op de WMI-klasse, in plaats van een bepaalde adapter, omdat het vrijgeven en leases wereldwijd vernieuwen wordt uitgevoerd op de klasse, niet op een specifieke adapter.

Een verwijzing naar een WMI-klasse, in plaats van de klasse-instanties, krijgt u alle WMI-klassen weergeven en selecteert u alleen de gewenste klasse met de naam. De volgende opdracht geeft bijvoorbeeld de Win32_NetworkAdapterConfiguration-klasse:

```powershell
Get-WmiObject -List | Where-Object -FilterScript {$_.Name -eq 'Win32_NetworkAdapterConfiguration'}
```

U kunt de volledige opdracht behandelen als de klasse en vervolgens de **ReleaseDHCPAdapterLease** methode. In de volgende opdracht, de haakjes de **Get-WmiObject** en **Where-Object** Pijplijnelementen direct Windows PowerShell moeten worden eerst geëvalueerd:

```powershell
( Get-WmiObject -List | Where-Object -FilterScript {$_.Name -eq 'Win32_NetworkAdapterConfiguration'} ).ReleaseDHCPLeaseAll()
```

U kunt dezelfde opdrachtindeling gebruiken om aan te roepen de **RenewDCHPLeaseAll** methode:

```powershell
( Get-WmiObject -List | Where-Object -FilterScript {$_.Name -eq 'Win32_NetworkAdapterConfiguration'} ).RenewDHCPLeaseAll()
```

### <a name="creating-a-network-share"></a>Het maken van een netwerkshare

Voor het maken van een netwerkshare bevindt, gebruikt u de **Win32_Share maken** methode:

```powershell
(Get-WmiObject -List -ComputerName . | Where-Object -FilterScript {$_.Name -eq 'Win32_Share'}).Create('C:\temp','TempShare',0,25,'test share of the temp folder')
```

U kunt ook de share maken met behulp van **net share** in Windows PowerShell:

```powershell
net share tempshare=c:\temp /users:25 /remark:"test share of the temp folder"
```

### <a name="removing-a-network-share"></a>Verwijderen van een netwerkshare

Kunt u een netwerkshare met **Win32_Share**, maar het proces is enigszins afwijken van het maken van een share, omdat u nodig hebt om op te halen van de specifieke share moet worden verwijderd, in plaats van de **Win32_Share** de klasse. De volgende instructie verwijdert u de share 'TempShare':

```powershell
(Get-WmiObject -Class Win32_Share -ComputerName . -Filter "Name='TempShare'").Delete()
```

**Net share** zo goed werkt:

```
PS> net share tempshare /delete

tempshare was deleted successfully.
```

### <a name="connecting-a-windows-accessible-network-drive"></a>Verbinding maken van een netwerkstation toegankelijk is in Windows

De **New-PSDrive** cmdlets maakt u een Windows PowerShell-station, maar de stations die zijn gemaakt op deze manier zijn alleen beschikbaar voor Windows PowerShell. Een nieuwe netwerk station wilt maken, kunt u de **WScript.Network** COM-object. De volgende opdracht wordt de share toegewezen \\ \\FPS01\\gebruikers naar de lokale schijf B:

```powershell
(New-Object -ComObject WScript.Network).MapNetworkDrive('B:', '\\FPS01\users')
```

De **netgebruik** opdracht werkt ook:

```powershell
net use B: \\FPS01\users
```

In beide gevallen toegewezen stations **WScript.Network** of netgebruik zijn onmiddellijk beschikbaar voor Windows PowerShell.