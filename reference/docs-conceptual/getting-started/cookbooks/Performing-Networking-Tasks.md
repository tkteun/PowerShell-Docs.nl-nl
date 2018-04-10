---
ms.date: 06/05/2017
keywords: PowerShell-cmdlet
title: Netwerktaken uitvoeren
ms.assetid: a43cc55f-70c1-45c8-9467-eaad0d57e3b5
ms.openlocfilehash: 64c57c95a70bc4cad4b695a59d96673ed18afdf4
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 04/09/2018
---
# <a name="performing-networking-tasks"></a>Netwerktaken uitvoeren

Omdat TCP/IP het meest gebruikte netwerkprotocol is, omvatten de meeste beheertaken voor op laag niveau netwerk protocol TCP/IP. In deze sectie gebruiken we de Windows PowerShell en WMI voor deze taken.

### <a name="listing-ip-addresses-for-a-computer"></a>IP-adressen weergeven voor een Computer

Als u alle IP-adressen in gebruik is op de lokale computer, gebruikt u de volgende opdracht:

```powershell
Get-WmiObject -Class Win32_NetworkAdapterConfiguration -Filter IPEnabled=$true -ComputerName . | Format-Table -Property IPAddress
```

De uitvoer van deze opdracht verschilt van de meeste lijsten met zoekeigenschappen omdat waarden tussen accolades worden geplaatst:

```output
IPAddress
---------
{192.168.1.80}
{192.168.148.1}
{192.168.171.1}
{0.0.0.0}
```

Om te begrijpen waarom de accolades worden weergegeven, gebruikt u de cmdlet Get-lid te onderzoeken de **IPAddress** eigenschap:

```
PS> Get-WmiObject -Class Win32_NetworkAdapterConfiguration -Filter IPEnabled=$true -ComputerName . | Get-Member -Name IPAddress


TypeName: System.Management.ManagementObject#root\cimv2\Win32_NetworkAdapterConfiguration

Name      MemberType Definition
----      ---------- ----------
IPAddress Property   System.String[] IPAddress {get;}
```

De eigenschap IP-adres voor elke netwerkadapter is daadwerkelijk een matrix. De accolades in de definitie is gebleken dat **IPAddress** is niet een **System.String** waarde, maar een matrix van **System.String** waarden.

### <a name="listing-ip-configuration-data"></a>IP-configuratiegegevens van aanbieding

Als u wilt weergeven van gedetailleerde IP-configuratiegegevens voor elke netwerkadapter, moet u de volgende opdracht gebruiken:

```powershell
Get-WmiObject -Class Win32_NetworkAdapterConfiguration -Filter IPEnabled=$true -ComputerName .
```

De standaardweergave voor de configuratie voor de netwerkadapter is een zeer beperkte set van de beschikbare informatie. Gebruik voor uitgebreide controle en probleemoplossing, Select-Object of een opmaak cmdlet, zoals indeling-lijst om op te geven van de eigenschappen die moeten worden weergegeven.

Als u niet geïnteresseerd in de eigenschappen van IPX of WINS bent, waarschijnlijk het geval in een moderne TCP/IP-netwerk, kunt u de parameter ExcludeProperty van Select-Object voor het verbergen van eigenschappen met namen die met 'WINS beginnen' of ' IPX: "

```powershell
Get-WmiObject -Class Win32_NetworkAdapterConfiguration -Filter IPEnabled=$true -ComputerName . | Select-Object -Property [a-z]* -ExcludeProperty IPX*,WINS*
```

Deze opdracht retourneert gedetailleerde informatie over DHCP, DNS, Routering en andere secundaire IP-configuratie-eigenschappen.

### <a name="pinging-computers"></a>Pingen naar Computers

U kunt een eenvoudige ping uit voor een computer met door uitvoeren **Win32_PingStatus**. De volgende opdracht de opdracht ping wordt uitgevoerd, maar retourneert uitgebreide uitvoer:

```powershell
Get-WmiObject -Class Win32_PingStatus -Filter "Address='127.0.0.1'" -ComputerName .
```

Nuttiger formulier samenvattende informatie weergegeven in een van de eigenschappen van-adres, reactietijd en StatusCode, zoals worden gegenereerd door de volgende opdracht. De parameter Autosize van Format-Table aangepast kolommen in de tabel zodat ze correct wordt weergegeven in de Windows PowerShell.

```
PS> Get-WmiObject -Class Win32_PingStatus -Filter "Address='127.0.0.1'" -ComputerName . | Format-Table -Property Address,ResponseTime,StatusCode -Autosize

Address   ResponseTime StatusCode
-------   ------------ ----------
127.0.0.1            0          0
```

Een StatusCode 0 geeft aan dat een geslaagde ping.

U kunt een matrix gebruiken op meerdere computers met één opdracht ping. Omdat er meer dan één adres, gebruik de **ForEach-Object** te pingen elk adres afzonderlijk:

```powershell
'127.0.0.1','localhost','research.microsoft.com' | ForEach-Object -Process {Get-WmiObject -Class Win32_PingStatus -Filter ("Address='" + $_ + "'") -ComputerName .} | Select-Object -Property Address,ResponseTime,StatusCode
```

U kunt dezelfde opdrachtindeling alle computers in een subnet, zoals een particulier netwerk dat gebruikmaakt van netwerknummer 192.168.1.0 en een standaard klasse C-subnetmasker (255.255.255.0) te pingen., worden alleen de adressen in het bereik van 192.168.1.1 via 192.168.1.254 rechtmatige lokale adressen (0 is altijd gereserveerd voor het netwerknummer en 255 is een subnet broadcast-adres).

Ter vertegenwoordiging van een matrix van de getallen tussen 1 en 254 in Windows PowerShell, gebruikt u de instructie **1..254.** Een ping voltooid subnet kan worden uitgevoerd door het genereren van de matrix en vervolgens de waarden op een gedeeltelijke adres toe te voegen in de ping-instructie:

```powershell
1..254| ForEach-Object -Process {Get-WmiObject -Class Win32_PingStatus -Filter ("Address='192.168.1." + $_ + "'") -ComputerName .} | Select-Object -Property Address,ResponseTime,StatusCode
```

Houd er rekening mee dat deze techniek voor het genereren van een bereik aan adressen elders ook kan worden gebruikt. Op deze manier kunt u een volledige reeks adressen genereren:

```powershell
$ips = 1..254 | ForEach-Object -Process {'192.168.1.' + $_}
```

### <a name="retrieving-network-adapter-properties"></a>Bij het ophalen van eigenschappen van netwerkadapter

Eerder in deze handleiding wordt vermeld dat u algemene configuratie-eigenschappen ophalen met behulp van kan **Win32_NetworkAdapterConfiguration**. Hoewel niet strikt TCP/IP-informatie, netwerkadapterinformatie zoals MAC-adressen en typen netwerkadapters kunnen nuttig zijn voor inzicht in wat er gebeurt met een computer. Als u een overzicht van deze informatie, gebruikt u de volgende opdracht:

```powershell
Get-WmiObject -Class Win32_NetworkAdapter -ComputerName .
```

### <a name="assigning-the-dns-domain-for-a-network-adapter"></a>Het DNS-domein toe te wijzen voor een netwerkadapter

Als het DNS-domein voor automatische naamomzetting wilt toewijzen, gebruikt u de **Win32_NetworkAdapterConfiguration SetDNSDomain** methode. Omdat u de DNS-domein voor de configuratie van elke netwerkadapter afzonderlijk toewijst, moet u een **ForEach-Object** instructie het domein toewijzen aan elke adapter:

```powershell
Get-WmiObject -Class Win32_NetworkAdapterConfiguration -Filter IPEnabled=$true -ComputerName . | ForEach-Object -Process { $_. SetDNSDomain('fabrikam.com') }
```

De instructie voor filteren ' IPEnabled $true = ' is nodig omdat zelfs op een netwerk dat gebruikmaakt van alleen TCP/IP, verschillende configuraties van de netwerkadapters op een computer niet true TCP/IP-adapters; Deze algemene software-elementen ter ondersteuning van de RAS-, PPTP, QoS en andere services voor alle adapters zijn en dus niet een adres van hun eigen hebben.

U kunt de opdracht filteren met behulp van de **Where-Object** cmdlet, in plaats van de **Get-WmiObject** filter.

```powershell
Get-WmiObject -Class Win32_NetworkAdapterConfiguration -ComputerName . | Where-Object -FilterScript {$_.IPEnabled} | ForEach-Object -Process {$_.SetDNSDomain('fabrikam.com')}
```

### <a name="performing-dhcp-configuration-tasks"></a>DHCP-uitvoeren configuratietaken

Wijzigen van de DHCP-informatie omvat het werken met een set netwerkadapters, net als de DNS-configuratie. Er zijn verschillende afzonderlijke acties die u uitvoeren kunt met behulp van WMI en wordt er slechts enkele van de meest gangbare doorlopen.

#### <a name="determining-dhcp-enabled-adapters"></a>DCHP-Adapters bepalen

Ga voor de adapters DHCP ingeschakeld op een computer, moet u de volgende opdracht gebruiken:

```powershell
Get-WmiObject -Class Win32_NetworkAdapterConfiguration -Filter "DHCPEnabled=$true" -ComputerName .
```

Als u wilt uitsluiten van netwerkadapters met IP-configuratieproblemen, kunt u alleen IP ingeschakeld adapters ophalen:

```powershell
Get-WmiObject -Class Win32_NetworkAdapterConfiguration -Filter "IPEnabled=$true and DHCPEnabled=$true" -ComputerName .
```

#### <a name="retrieving-dhcp-properties"></a>Bij het ophalen van eigenschappen voor DHCP

Omdat DHCP-gerelateerde eigenschappen voor een adapter wordt doorgaans begint met 'DHCP', kunt u de parameter Property van Format-Table gebruiken om alleen die eigenschappen weer te geven:

```powershell
Get-WmiObject -Class Win32_NetworkAdapterConfiguration -Filter "DHCPEnabled=$true" -ComputerName . | Format-Table -Property DHCP*
```

#### <a name="enabling-dhcp-on-each-adapter"></a>DHCP op elke Adapter inschakelen

Activeren van DHCP op alle netwerkadapters moet u de volgende opdracht gebruiken:

```powershell
Get-WmiObject -Class Win32_NetworkAdapterConfiguration -Filter IPEnabled=$true -ComputerName . | ForEach-Object -Process {$_.EnableDHCP()}
```

U kunt de **Filter** instructie ' IPEnabled = $true en DHCPEnabled $false = "om te voorkomen dat het inschakelen van DHCP waar deze al is ingeschakeld, maar als deze stap wordt weggelaten wordt geen fouten veroorzaken.

#### <a name="releasing-and-renewing-dhcp-leases-on-specific-adapters"></a>Vrijgeven en DHCP-Leases op specifieke Adapters vernieuwen

De **Win32_NetworkAdapterConfiguration** klasse heeft **ReleaseDHCPLease** en **RenewDCHPLease** methoden. Beide worden op dezelfde manier gebruikt. Deze methoden in het algemeen gebruiken als u alleen wilt vrijgeven of vernieuwen van adressen voor een adapter op een specifiek subnet. De eenvoudigste manier om filter-adapters in een subnet is de adapterconfiguraties die gebruikmaken van de gateway voor dat subnet kiezen. De volgende opdracht worden bijvoorbeeld alle DHCP-leases op adapters op de lokale computer die u DHCP-leases van 192.168.1.254 verkrijgt vrijgegeven:

```powershell
Get-WmiObject -Class Win32_NetworkAdapterConfiguration -Filter "IPEnabled=$true and DHCPEnabled=$true" -ComputerName . | Where-Object -FilterScript {$_.DHCPServer -contains '192.168.1.254'} | ForEach-Object -Process {$_.ReleaseDHCPLease()}
```

De enige wijziging voor het vernieuwen van een DHCP-lease is met de **RenewDCHPLease** methode in plaats van de **ReleaseDHCPLease** methode:

```powershell
Get-WmiObject -Class Win32_NetworkAdapterConfiguration -Filter "IPEnabled=$true and DHCPEnabled=$true" -ComputerName . | Where-Object -FilterScript {$_.DHCPServer -contains '192.168.1.254'} | ForEach-Object -Process {$_.ReleaseDHCPLease()}
```

> [!NOTE]
> Wanneer u deze methoden op een externe computer, Let erop dat u toegang met het externe systeem verliezen kunt als u met het via de adapter met de lease vrijgegeven of vernieuwd verbonden bent.

#### <a name="releasing-and-renewing-dhcp-leases-on-all-adapters"></a>Vrijgeven en DHCP-Leases op alle Adapters vernieuwen

U kunt globale releases van DHCP-adres of vernieuwingen op alle adapters uitvoeren met behulp van de **Win32_NetworkAdapterConfiguration** methoden, **ReleaseDHCPLeaseAll** en **RenewDCHPLeaseAll** . Echter de opdracht moet toepassen op de WMI-klasse, in plaats van een bepaalde adapter omdat vrijgeven en leases globaal vernieuwen op de klasse, niet op een bepaalde adapter wordt uitgevoerd.

U krijgt een verwijzing naar een WMI-klasse, in plaats van de klasse-instanties weergeven van alle WMI-klassen en selecteert u alleen de gewenste klasse met de naam. De volgende opdracht geeft bijvoorbeeld de Win32_NetworkAdapterConfiguration-klasse:

```powershell
Get-WmiObject -List | Where-Object -FilterScript {$_.Name -eq 'Win32_NetworkAdapterConfiguration'}
```

U kunt de volledige opdracht behandelen als de klasse en roep daarna de **ReleaseDHCPAdapterLease** methode erop. In de volgende opdracht, de haakjes de **Get-WmiObject** en **Where-Object** Pijplijnelementen direct Windows PowerShell om te evalueren ze eerst:

```powershell
( Get-WmiObject -List | Where-Object -FilterScript {$_.Name -eq 'Win32_NetworkAdapterConfiguration'} ).ReleaseDHCPLeaseAll()
```

U kunt dezelfde opdrachtindeling gebruiken om aan te roepen de **RenewDCHPLeaseAll** methode:

```powershell
( Get-WmiObject -List | Where-Object -FilterScript {$_.Name -eq 'Win32_NetworkAdapterConfiguration'} ).RenewDHCPLeaseAll()
```

### <a name="creating-a-network-share"></a>Een netwerkshare maken

Voor het maken van een netwerkshare gebruikt de **Win32_Share maken** methode:

```powershell
(Get-WmiObject -List -ComputerName . | Where-Object -FilterScript {$_.Name -eq 'Win32_Share'}).Create('C:\temp','TempShare',0,25,'test share of the temp folder')
```

U kunt ook de share maken met behulp van **net share** in Windows PowerShell:

```powershell
net share tempshare=c:\temp /users:25 /remark:"test share of the temp folder"
```

### <a name="removing-a-network-share"></a>Een netwerkshare verwijderen

U kunt een netwerkshare in verwijderen **Win32_Share**, maar het proces is enigszins afwijken van het maken van een share, omdat u nodig hebt voor het ophalen van de specifieke share moet worden verwijderd, in plaats van de **Win32_Share** de klasse. De volgende instructie verwijdert de share 'TempShare':

```powershell
(Get-WmiObject -Class Win32_Share -ComputerName . -Filter "Name='TempShare'").Delete()
```

**Net share** werkt ook:

```
PS> net share tempshare /delete

tempshare was deleted successfully.
```

### <a name="connecting-a-windows-accessible-network-drive"></a>Verbinding maken met een toegankelijke netwerkstation van Windows

De **nieuw PSDrive** cmdlets maakt een Windows PowerShell-station, maar de stations die zijn gemaakt op deze manier zijn alleen beschikbaar voor Windows PowerShell. Een nieuwe netwerk station wilt maken, kunt u de **WScript.Network** COM-object. De volgende opdracht wordt de share toegewezen \\ \\FPS01\\gebruikers naar de lokale schijf B:

```powershell
(New-Object -ComObject WScript.Network).MapNetworkDrive('B:', '\\FPS01\users')
```

De **gebruik net** opdracht werkt ook:

```powershell
net use B: \\FPS01\users
```

Schijven met een toegewezen **WScript.Network** of net gebruik onmiddellijk beschikbaar zijn voor Windows PowerShell.