---
ms.date: 06/12/2017
keywords: DSC, powershell, configuratie en installatie
title: Aan de slag met Desired State Configuration (DSC) voor Linux
ms.openlocfilehash: 69f087434455aae8e97ea07c79c52e493412d134
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 02/03/2019
ms.locfileid: "55686598"
---
# <a name="get-started-with-desired-state-configuration-dsc-for-linux"></a>Aan de slag met Desired State Configuration (DSC) voor Linux

In dit onderwerp wordt uitgelegd hoe u aan de slag met behulp van PowerShell Desired State Configuration (DSC) voor Linux. Raadpleeg voor algemene informatie over DSC [aan de slag met Windows PowerShell Desired State Configuration](../overview/overview.md).

## <a name="supported-linux-operation-system-versions"></a>Ondersteunde versies van Linux bewerking system

De volgende versies van de Linux-besturingssystemen worden ondersteund voor DSC voor Linux.

- CentOS 5, 6 en 7 (x86/x64)
- Debian GNU/Linux 6, 7 en 8 (x86/x64)
- Oracle Linux 5, 6 en 7 (x86/x64)
- Red Hat Enterprise Linux Server 5, 6 and 7 (x86/x64)
- SUSE Linux Enterprise Server 10, 11 en 12 (x86/x64)
- Server Ubuntu 12.04 LTS, 14.04 LTS en 16.04 LTS (x86/x64)

De volgende tabel beschrijft de vereiste pakketafhankelijkheden voor DSC voor Linux.

|  Vereist pakket |  Beschrijving |  Minimale versie |
|---|---|---|
| glibc| GNU-bibliotheek| 2…4 – 31.30|
| python| Python| 2.4 – 3.4|
| omiserver| Open Management Infrastructure| 1.0.8.1|
| openssl| OpenSSL-bibliotheken| versie 0.9.8 of 1.0|
| ctypes| CTypes Python-bibliotheek| Moet overeenkomen met de Python-versie|
| libcurl| cURL http-clientbibliotheek| 7.15.1|

## <a name="installing-dsc-for-linux"></a>DSC voor Linux installeren

U moet installeren de [Open Management Infrastructure (OMI)](https://github.com/Microsoft/omi) voordat u DSC voor Linux installeert.

### <a name="installing-omi"></a>OMI installeren

Desired State Configuration voor Linux is vereist voor de Open Management Infrastructure (OMI) CIM-server, versie 1.0.8.1 of hoger. OMI kan worden gedownload uit de Open groep: [Open Management Infrastructure (OMI)](https://github.com/Microsoft/omi).

OMI, installeert u het pakket dat geschikt is voor uw Linux-systeem (.rpm of .deb) en de versie van OpenSSL (ssl_098 of ssl_100) en de architectuur (x64/x86). RPM-pakketten zijn geschikt voor CentOS, Red Hat Enterprise Linux, SUSE Linux Enterprise Server en Oracle Linux. DEB pakketten zijn geschikt voor Debian GNU/Linux- en Ubuntu Server. De ssl_098-pakketten zijn geschikt voor computers met OpenSSL 0.9.8 geïnstalleerd terwijl de ssl_100-pakketten geschikt voor computers met OpenSSL 1.0 is geïnstalleerd zijn.

> [!NOTE]
> Voer de opdracht uit om te bepalen van de geïnstalleerde versie van OpenSSL, `openssl version`.

Voer de volgende opdracht te OMI installeren op een CentOS 7 x64-systeem.

`# sudo rpm -Uvh omiserver-1.0.8.ssl_100.rpm`

### <a name="installing-dsc"></a>Installeren van DSC

DSC voor Linux is beschikbaar als download [hier](https://github.com/Microsoft/PowerShell-DSC-for-Linux/releases/tag/v1.1.1-294).

DSC, installeert u het pakket dat geschikt is voor uw Linux-systeem (.rpm of .deb) en de versie van OpenSSL (ssl_098 of ssl_100) en de architectuur (x64/x86). RPM-pakketten zijn geschikt voor CentOS, Red Hat Enterprise Linux, SUSE Linux Enterprise Server en Oracle Linux. DEB pakketten zijn geschikt voor Debian GNU/Linux- en Ubuntu Server. De ssl_098-pakketten zijn geschikt voor computers met OpenSSL 0.9.8 geïnstalleerd terwijl de ssl_100-pakketten geschikt voor computers met OpenSSL 1.0 is geïnstalleerd zijn.

> [!NOTE]
> Om te bepalen van de geïnstalleerde versie van OpenSSL, de opdracht openssl-versie wordt uitgevoerd.

Voer de volgende opdracht voor het installeren van DSC op een CentOS 7 x64-systeem.

`# sudo rpm -Uvh dsc-1.0.0-254.ssl_100.x64.rpm`

## <a name="using-dsc-for-linux"></a>Met behulp van DSC voor Linux

De volgende secties wordt uitgelegd hoe het maken en uitvoeren van DSC-configuraties op Linux-computers.

### <a name="creating-a-configuration-mof-document"></a>Het maken van een MOF-configuratiebestand

Het sleutelwoord Windows PowerShell-configuratie wordt gebruikt voor het maken van een configuratie voor Linux-computers, net als voor Windows-computers. De volgende stappen beschrijven het maken van een configuratiebestand voor een Linux-computer met Windows PowerShell.

1. Importeer de nx-module. De nx Windows PowerShell-module moet bevat het schema voor ingebouwde resources voor DSC voor Linux, en worden geïnstalleerd op uw lokale computer en geïmporteerd in de configuratie.

   - Als u wilt de nx-module installeert, kopieert u de modulemap nx naar een `$env:USERPROFILE\Documents\WindowsPowerShell\Modules\` of `$PSHOME\Modules`. De nx-module is opgenomen in de DSC voor Linux-installatiepakket. Als u wilt importeren in de configuratie van de nx-module, gebruikt de `Import-DSCResource` opdracht:

   ```powershell
   Configuration ExampleConfiguration{

    Import-DSCResource -Module nx

   }
   ```

2. Een configuratie definiëren en genereren van het configuratiebestand:

   ```powershell
   Configuration ExampleConfiguration
   {
        Import-DscResource -Module nx

        Node  "linuxhost.contoso.com"
        {
            nxFile ExampleFile 
            {
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

Van configuratiedocumenten (MOF-bestanden) kunnen worden geactiveerd met de Linux-computer via de [Start-DscConfiguration](/powershell/module/psdesiredstateconfiguration/start-dscconfiguration) cmdlet. Als u wilt gebruiken met deze cmdlet, samen met de [Get-DscConfiguration](/powershell/module/PSDesiredStateConfiguration/Get-DscConfiguration), of [Test-DscConfiguration](/powershell/module/psdesiredstateconfiguration/Test-DSCConfiguration) cmdlets, op afstand op een Linux-computer, moet u een CIMSession gebruiken. De [New-CimSession](/powershell/module/CimCmdlets/New-CimSession) cmdlet wordt gebruikt om u te maken van een CIMSession naar de Linux-computer.

De volgende code laat zien hoe een CIMSession maken voor DSC voor Linux.

```powershell
$Node = "ostc-dsc-01"
$Credential = Get-Credential -UserName:"root" -Message:"Enter Password:"

#Ignore SSL certificate validation
#$opt = New-CimSessionOption -UseSsl:$true -SkipCACheck:$true -SkipCNCheck:$true -SkipRevocationCheck:$true

#Options for a trusted SSL certificate
$opt = New-CimSessionOption -UseSsl:$true
$Sess=New-CimSession -Credential:$credential -ComputerName:$Node -Port:5986 -Authentication:basic -SessionOption:$opt -OperationTimeoutSec:90
```

> [!NOTE]
> Voor de modus 'Push' moet de referenties van de gebruiker de hoofdgebruiker zijn op de Linux-computer.
> Alleen SSL/TLS-verbindingen worden ondersteund voor DSC voor Linux, de `New-CimSession` moet worden gebruikt met de parameter – UseSSL is ingesteld op $true.
> Het SSL-certificaat gebruikt door OMI (DSC) is opgegeven in het bestand: `/opt/omi/etc/omiserver.conf` met de eigenschappen: pemfile en keyfile.
> Als dit certificaat niet wordt vertrouwd door de Windows-computer waarop u de [New-CimSession](/powershell/module/CimCmdlets/New-CimSession) cmdlet op die u kunt kiezen om de validatie van het servercertificaat met de opties CIMSession negeren: `-SkipCACheck:$true -SkipCNCheck:$true -SkipRevocationCheck:$true`

Voer de volgende opdracht om de DSC-configuratie tot de Linux-knooppunt.

`Start-DscConfiguration -Path:"C:\temp" -CimSession:$Sess -Wait -Verbose`

### <a name="distribute-the-configuration-with-a-pull-server"></a>Distribueren van de configuratie met een pull-server

Configuraties kunnen worden gedistribueerd naar een Linux-computer met een pull-server, net als voor Windows-computers. Zie voor instructies over het gebruik van een pull-server [Windows PowerShell Desired State Configuration Pull Servers](../pull-server/pullServer.md). Zie voor meer informatie en beperkingen met betrekking tot het gebruik van Linux-computers met een pull-server, de opmerkingen bij de Release voor Desired State Configuration voor Linux.

### <a name="working-with-configurations-locally"></a>Werken met configuraties lokaal

DSC voor Linux bevat scripts die worden gebruikt met de configuratie van de lokale Linux-computer. Deze scripts zijn niet vinden in `/opt/microsoft/dsc/Scripts` en neem het volgende:

- GetDscConfiguration.py

Retourneert de huidige configuratie is toegepast op de computer. Vergelijkbaar met de Windows PowerShell-cmdlet `Get-DscConfiguration` cmdlet.

`# sudo ./GetDscConfiguration.py`

- GetDscLocalConfigurationManager.py

Retourneert de huidige meta-configuratie op de computer toegepast. Vergelijkbaar met de cmdlet [Get-DSCLocalConfigurationManager](/powershell/module/PSDesiredStateConfiguration/Get-DscLocalConfigurationManager) cmdlet.

`# sudo ./GetDscLocalConfigurationManager.py`

- InstallModule.py

Hiermee installeert u een aangepaste module van de DSC-resource. Het pad naar een ZIP-bestand met de module Gedeelde objectbibliotheek en schema MOF-bestanden vereist.

`# sudo ./InstallModule.py /tmp/cnx_Resource.zip`

- RemoveModule.py

Hiermee verwijdert u een aangepaste module van de DSC-resource. Vereist de naam van de module te verwijderen.

`# sudo ./RemoveModule.py cnx_Resource`

- StartDscLocalConfigurationManager.py

Geldt een MOF-configuratiebestand voor de computer. Vergelijkbaar met de [Start-DscConfiguration](/powershell/module/psdesiredstateconfiguration/start-dscconfiguration) cmdlet. Het pad naar MOF om toe te passen van de configuratie vereist.

`# sudo ./StartDscLocalConfigurationManager.py –configurationmof /tmp/localhost.mof`

- SetDscLocalConfigurationManager.py

Geldt een Meta-configuratie MOF-bestand voor de computer. Vergelijkbaar met de [Set-DSCLocalConfigurationManager](/powershell/module/PSDesiredStateConfiguration/Set-DscLocalConfigurationManager) cmdlet. Moet het pad naar het MOF Meta-configuratie om toe te passen.

`# sudo ./SetDscLocalConfigurationManager.py –configurationmof /tmp/localhost.meta.mof`

## <a name="powershell-desired-state-configuration-for-linux-log-files"></a>PowerShell Desired State Configuration voor Linux-logboekbestanden

De volgende logboekbestanden worden gegenereerd voor DSC voor Linux-berichten.

|Logboekbestand|Adreslijst|Beschrijving|
|---|---|---|
|**omiserver.log**|`/var/opt/omi/log`|Berichten die betrekking hebben op de werking van de OMI-CIM-server.|
|**dsc.log**|`/var/opt/omi/log`|Berichten die betrekking hebben op de werking van de lokale Configuration Manager (LCM) en DSC-resource-bewerkingen.|
