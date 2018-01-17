---
ms.date: 2017-06-12
ms.topic: conceptual
keywords: DSC, powershell, configuratie, setup
title: Met Desired State Configuration (DSC) aan de slag voor Linux
ms.openlocfilehash: 4fd8460bc5d2564cab291904b60a1a0c26c3e5a7
ms.sourcegitcommit: a444406120e5af4e746cbbc0558fe89a7e78aef6
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 01/17/2018
---
# <a name="get-started-with-desired-state-configuration-dsc-for-linux"></a>Met Desired State Configuration (DSC) aan de slag voor Linux

In dit onderwerp wordt uitgelegd hoe u aan de slag met behulp van PowerShell Desired State Configuration (DSC) voor Linux. Raadpleeg voor algemene informatie over DSC [aan de slag met Windows PowerShell Desired State Configuration](overview.md).

## <a name="supported-linux-operation-system-versions"></a>Ondersteunde versies van Linux bewerking systeem

De volgende versies van Linux-besturingssystemen worden ondersteund voor DSC voor Linux.
- CentOS 5, 6 en 7 (x86/x64)
- Debian GNU/Linux 6, 7 en 8 (x86/x64)
- Oracle Linux 5, 6 en 7 (x86/x64)
- Red Hat Enterprise Linux Server 5, 6 en 7 (x86/x64)
- SUSE Linux Enterprise Server 10, 11 en 12 (x86/x64)
- Ubuntu Server 12.04 TNS, 14.04 TNS en 16.04 LTS (x86/x64)

De volgende tabel beschrijft de afhankelijkheden vereist pakket voor DSC voor Linux.

|  Vereist pakket |  Beschrijving |  Minimale versie | 
|---|---|---|
| glibc| GNU-bibliotheek| 2…4 – 31.30| 
| python| Python| 2.4 – 3.4| 
| omiserver| Open Management Infrastructure| 1.0.8.1| 
| Openssl| OpenSSL-bibliotheken| 0.9.8 of 1.0| 
| ctypes| CTypes Python-bibliotheek| Moet overeenkomen met de versie van Python| 
| libcurl| http-clientbibliotheek cURL| 7.15.1| 

## <a name="installing-dsc-for-linux"></a>DSC voor Linux installeren

U moet installeren de [Open Management Infrastructure (OMI)](https://github.com/Microsoft/omi) voordat DSC voor Linux installeren.

### <a name="installing-omi"></a>OMI installeren

Desired State Configuration voor Linux de Open Management Infrastructure (OMI) CIM-server, versie 1.0.8.1 vereist of hoger. OMI kan worden gedownload uit de Open groep: [Open Management Infrastructure (OMI)](https://github.com/Microsoft/omi).

Installeer het pakket dat geschikt is voor uw Linux-systeem (.rpm of .deb) en de versie van OpenSSL (ssl_098 of ssl_100) en de architectuur (x64/x86) voor het installeren van OMI. RPM pakketten zijn geschikt voor CentOS, Red Hat Enterprise Linux, SUSE Linux Enterprise Server en Oracle Linux. DEB pakketten zijn geschikt voor Debian GNU/Linux en Ubuntu Server. De ssl_098-pakketten zijn geschikt voor computers met OpenSSL 0.9.8 hebt geïnstalleerd terwijl de ssl_100-pakketten geschikt voor computers met OpenSSL 1.0 is geïnstalleerd zijn.

> **Opmerking**: Voer de opdracht uit om te bepalen van de geïnstalleerde versie van OpenSSL, `openssl version`.

Voer de volgende opdracht voor het installeren van OMI op een systeem CentOS 7 x64.

`# sudo rpm -Uvh omiserver-1.0.8.ssl_100.rpm`

### <a name="installing-dsc"></a>DSC installeren

DSC voor Linux is beschikbaar als download [hier](https://github.com/Microsoft/PowerShell-DSC-for-Linux/releases/latest). 

Installeer het pakket dat geschikt is voor uw Linux-systeem (.rpm of .deb) en de versie van OpenSSL (ssl_098 of ssl_100) en de architectuur (x64/x86) voor het installeren van DSC. RPM pakketten zijn geschikt voor CentOS, Red Hat Enterprise Linux, SUSE Linux Enterprise Server en Oracle Linux. DEB pakketten zijn geschikt voor Debian GNU/Linux en Ubuntu Server. De ssl_098-pakketten zijn geschikt voor computers met OpenSSL 0.9.8 hebt geïnstalleerd terwijl de ssl_100-pakketten geschikt voor computers met OpenSSL 1.0 is geïnstalleerd zijn.

> **Opmerking**: om te bepalen van de geïnstalleerde versie van OpenSSL, voert u de opdracht openssl-versie.
 
Voer de volgende opdracht DSC installeren op een systeem CentOS 7 x64.

`# sudo rpm -Uvh dsc-1.0.0-254.ssl_100.x64.rpm`


## <a name="using-dsc-for-linux"></a>Gebruik van DSC voor Linux

De volgende secties wordt uitgelegd hoe maken en uitvoeren van DSC-configuraties op Linux-computers.

### <a name="creating-a-configuration-mof-document"></a>Maken van een document van de MOF-configuratie

De configuratie van Windows PowerShell-sleutelwoord gebruikt voor het maken van een configuratie voor Linux-computers, net als voor Windows-computers. De volgende stappen beschrijven het maken van een document van de configuratie voor een Linux-computer met Windows PowerShell.

1. Importeer de module NX inschakelen. De nx Windows PowerShell-module moet bevat het schema voor ingebouwde bronnen voor DSC voor Linux en worden geïnstalleerd op uw lokale computer en geïmporteerd in de configuratie.

    -Voor het installeren van de module nx, kopieert u de modulemap nx naar elk `$env:USERPROFILE\Documents\WindowsPowerShell\Modules\` of `$PSHOME\Modules`. De module nx is opgenomen in de DSC voor Linux-installatiepakket (MSI). Gebruik de module nx in uw configuratie importeren de __importeren DSCResource__ opdracht:
    
```powershell
Configuration ExampleConfiguration{
   
    Import-DSCResource -Module nx

}
```
2. Definieer een configuratie en genereren van het configuratiebestand:

```powershell
Configuration ExampleConfiguration{
   
    Import-DscResource -Module nx
 
    Node  "linuxhost.contoso.com"{
    nxFile ExampleFile {

        DestinationPath = "/tmp/example"
        Contents = "hello world `n"
        Ensure = "Present"
        Type = "File"
    }

    }
}
ExampleConfiguration -OutputPath:"C:\temp" 
```

### <a name="push-the-configuration-to-the-linux-computer"></a>De configuratie van de push naar de Linux-computer

Van configuratiedocumenten (MOF-bestanden) kunnen worden geactiveerd met het Linux-computer via de [Start DscConfiguration](https://technet.microsoft.com/en-us/library/dn521623.aspx) cmdlet. Als u wilt gebruiken van deze cmdlet, samen met de [Get-DscConfiguration](https://technet.microsoft.com/en-us/library/dn407379.aspx), of [Test DscConfiguration](https://technet.microsoft.com/en-us/library/dn407382.aspx) cmdlets, naar een Linux-computer, moet u op afstand een CIMSession gebruiken. De [New-CimSession](http://go.microsoft.com/fwlink/?LinkId=227967) cmdlet gebruikt voor het maken van een CIMSession naar de Linux-computer.

De volgende code laat zien hoe een CIMSession voor DSC voor Linux maken.

```powershell
$Node = "ostc-dsc-01"
$Credential = Get-Credential -UserName:"root" -Message:"Enter Password:"

#Ignore SSL certificate validation
#$opt = New-CimSessionOption -UseSsl:$true -SkipCACheck:$true -SkipCNCheck:$true -SkipRevocationCheck:$true

#Options for a trusted SSL certificate
$opt = New-CimSessionOption -UseSsl:$true 
$Sess=New-CimSession -Credential:$credential -ComputerName:$Node -Port:5986 -Authentication:basic -SessionOption:$opt -OperationTimeoutSec:90 
```

> **Opmerking**:
* Voor de modus 'Push' moet de gebruikersreferentie de hoofdgebruiker op de Linux-computer.
* Alleen SSL/TLS-verbindingen worden ondersteund voor DSC voor Linux, de New-CimSession moet worden gebruikt met de parameter – UseSSL is ingesteld op $true.
* Het SSL-certificaat gebruikt door OMI (DSC) is opgegeven in het bestand: `/opt/omi/etc/omiserver.conf` met de eigenschappen: pemfile en keyfile.
Als dit certificaat niet wordt vertrouwd door de Windows-computer die u gebruikt de [New-CimSession](http://go.microsoft.com/fwlink/?LinkId=227967) cmdlet op, kunt u voor het negeren van validatie van het servercertificaat met de opties CIMSession:`-SkipCACheck:$true -SkipCNCheck:$true -SkipRevocationCheck:$true`

Voer de volgende opdracht om de DSC-configuratie naar de Linux-knooppunt.

`Start-DscConfiguration -Path:"C:\temp" -CimSession:$Sess -Wait -Verbose`

### <a name="distribute-the-configuration-with-a-pull-server"></a>De configuratie met een pull-server distribueren

Configuraties kunnen worden gedistribueerd naar een Linux-computer met een pull-server, net als voor Windows-computers. Zie voor instructies over het gebruik van een pull-server, [Windows PowerShell Desired status Pull configuratieservers](pullServer.md). Zie voor meer informatie en beperkingen bij het gebruik van Linux-computers met een pull-server, de Release-opmerkingen voor Desired State Configuration voor Linux.

### <a name="working-with-configurations-locally"></a>Werken met lokaal configuraties

DSC voor Linux bevat scripts werken met de configuratie van de lokale Linux-computer. Deze scripts zijn niet vinden in `/opt/microsoft/dsc/Scripts` en neem het volgende:
* GetDscConfiguration.py

 Retourneert de huidige configuratie toegepast op de computer. Vergelijkbaar met de cmdlet Get-DscConfiguration Windows PowerShell-cmdlet.

`# sudo ./GetDscConfiguration.py`

* GetDscLocalConfigurationManager.py

 Retourneert de huidige meta-configuratie toegepast op de computer. Vergelijkbaar met de cmdlet [Get-DSCLocalConfigurationManager](https://technet.microsoft.com/en-us/library/dn407378.aspx) cmdlet.

`# sudo ./GetDscLocalConfigurationManager.py`

* InstallModule.py

 Hiermee installeert een aangepaste module van de DSC-resource. Het pad naar een ZIP-bestand met de module Gedeelde objectbibliotheek en schema MOF-bestanden vereist.

`# sudo ./InstallModule.py /tmp/cnx_Resource.zip`

* RemoveModule.py

 Hiermee verwijdert u een aangepaste module van de DSC-resource. Vereist de naam van de module te verwijderen.

`# sudo ./RemoveModule.py cnx_Resource`

* StartDscLocalConfigurationManager.py 

 Geldt een MOF-bestand voor configuratie voor de computer. Net als bij de [Start DscConfiguration](https://technet.microsoft.com/en-us/library/dn521623.aspx) cmdlet. Het pad naar MOF toepassen van de configuratie vereist.

`# sudo ./StartDscLocalConfigurationManager.py –configurationmof /tmp/localhost.mof`

* SetDscLocalConfigurationManager.py

 Geldt een Meta configuratie MOF-bestand voor de computer. Net als bij de [Set DSCLocalConfigurationManager](https://technet.microsoft.com/en-us/library/dn521621.aspx) cmdlet. Vereist het pad naar het MOF Meta configuratie toe te passen.

`# sudo ./SetDscLocalConfigurationManager.py –configurationmof /tmp/localhost.meta.mof`

## <a name="powershell-desired-state-configuration-for-linux-log-files"></a>PowerShell Desired State Configuration voor Linux-logboekbestanden

De volgende logboekbestanden worden gegenereerd voor DSC voor Linux-berichten.

|Logboekbestand|Adreslijst|Beschrijving|
|---|---|---|
|omiserver.log|/var/opt/OMI/log|Berichten met betrekking tot de werking van de OMI-CIM-server.|
|dsc.log|/var/opt/OMI/log|Berichten met betrekking tot de werking van de bewerkingen van de lokale Configuration Manager (LCM) en DSC-resources.|

