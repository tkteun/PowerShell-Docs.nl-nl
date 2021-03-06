---
ms.date: 01/07/2021
keywords: DSC, Power shell, configuratie, installatie
title: Aan de slag met de desired state Configuration (DSC) voor Linux
description: In dit onderwerp wordt uitgelegd hoe u aan de slag kunt gaan met behulp van Power shell desired state Configuration (DSC) voor Linux.
ms.openlocfilehash: 6f0dea956b16c0828964a10b43abbbc65879ea33
ms.sourcegitcommit: b9826dcf402db8a2b6d3eab37edb82c6af113343
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 01/08/2021
ms.locfileid: "98040919"
---
# <a name="get-started-with-desired-state-configuration-dsc-for-linux"></a>Aan de slag met de desired state Configuration (DSC) voor Linux

In dit onderwerp wordt uitgelegd hoe u aan de slag kunt gaan met behulp van Power shell desired state Configuration (DSC) voor Linux.
Zie [aan de slag met Windows Power shell desired state Configuration](../overview/overview.md)(Engelstalig) voor algemene informatie over DSC.

## <a name="supported-linux-operation-system-versions"></a>Ondersteunde versies van Linux-besturings systeem

De volgende versies van Linux-besturings systemen worden ondersteund door DSC voor Linux.

- CentOS 5, 6 en 7 (x86/x64)
- Debian GNU/Linux 6, 7 en 8 (x86/x64)
- Oracle Linux 5, 6 en 7 (x86/x64)
- Red Hat Enterprise Linux Server 5, 6 en 7 (x86/x64)
- SUSE Linux Enterprise Server 10, 11 en 12 (x86/x64)
- Ubuntu Server 12,04 LTS, 14,04 LTS, 16,04 LTS, 18,04 (x86/x64)

## <a name="installing-dsc-for-linux"></a>DSC voor Linux installeren

U moet de [Open Management Infrastructure (Omi)](https://github.com/Microsoft/omi) installeren voordat u DSC voor Linux installeert.

### <a name="installing-omi"></a>OMI installeren

De desired state Configuration voor Linux vereist de open Management Infrastructure (OMI) CIM-Server versie 1.0.8.1 of hoger. OMI kan worden gedownload uit de geopende groep: [Open Management Infrastructure (Omi)](https://github.com/Microsoft/omi).

Als u OMI wilt installeren, installeert u het pakket dat geschikt is voor uw Linux-systeem (. rpm of. deb) en OpenSSL-versie (ssl_098 of ssl_100) en architectuur (x64/x86). RPM-pakketten zijn geschikt voor CentOS, Red Hat Enterprise Linux, SUSE Linux Enterprise Server en Oracle Linux. DEB-pakketten zijn geschikt voor Debian GNU/Linux en Ubuntu Server. De ssl_098-pakketten zijn geschikt voor computers waarop OpenSSL 0.9.8 is ge??nstalleerd terwijl de ssl_100 pakketten geschikt zijn voor computers waarop OpenSSL 1,0 is ge??nstalleerd.

> [!NOTE]
> Voer de opdracht uit om de ge??nstalleerde versie van OpenSSL te bepalen `openssl version` .

Voer de volgende opdracht uit om OMI te installeren op een CentOS 7 x64-systeem.

`# sudo rpm -Uvh omiserver-1.0.8.ssl_100.rpm`

### <a name="installing-dsc"></a>DSC installeren

DSC voor Linux kan worden gedownload via de [Power shell-DSC-for-Linux](https://github.com/Microsoft/PowerShell-DSC-for-Linux/releases/tag/v1.1.1-926) -opslag plaats in de opslag plaats.

Als u DSC wilt installeren, installeert u het pakket dat geschikt is voor uw Linux-systeem (. rpm of. deb) en OpenSSL-versie (ssl_098 of ssl_100) en architectuur (x64/x86). RPM-pakketten zijn geschikt voor CentOS, Red Hat Enterprise Linux, SUSE Linux Enterprise Server en Oracle Linux. DEB-pakketten zijn geschikt voor Debian GNU/Linux en Ubuntu Server. De ssl_098-pakketten zijn geschikt voor computers waarop OpenSSL 0.9.8 is ge??nstalleerd terwijl de ssl_100 pakketten geschikt zijn voor computers waarop OpenSSL 1,0 is ge??nstalleerd.

> [!NOTE]
> Voer de opdracht openssl versie uit om de ge??nstalleerde versie van OpenSSL te bepalen.

Voer de volgende opdracht uit om DSC te installeren op een CentOS 7 x64-systeem.

`# sudo rpm -Uvh dsc-1.0.0-254.ssl_100.x64.rpm`

## <a name="using-dsc-for-linux"></a>DSC voor Linux gebruiken

In de volgende secties wordt uitgelegd hoe u DSC-configuraties op Linux-computers maakt en uitvoert.

### <a name="creating-a-configuration-mof-document"></a>Een configuratie-MOF-document maken

Het sleutel woord Windows Power shell-configuratie wordt gebruikt voor het maken van een configuratie voor Linux-computers, net als bij Windows-computers. De volgende stappen beschrijven het maken van een configuratie document voor een Linux-computer met behulp van Windows Power shell.

1. Importeer de NX-module. De NX Windows Power shell-module bevat het schema voor Built-In resources voor DSC voor Linux, en moet op uw lokale computer zijn ge??nstalleerd en in de configuratie worden ge??mporteerd.

   - Als u de NX-module wilt installeren, kopieert u de map van de NX-module naar ofwel `$env:USERPROFILE\Documents\WindowsPowerShell\Modules\` of `$PSHOME\Modules` . De NX-module is opgenomen in het installatie pakket voor DSC voor Linux. Als u de NX-module in uw configuratie wilt importeren, gebruikt u de `Import-DSCResource` opdracht:

   ```powershell
   Configuration ExampleConfiguration{

    Import-DSCResource -Module nx

   }
   ```

2. Definieer een configuratie en Genereer het configuratie document:

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

### <a name="push-the-configuration-to-the-linux-computer"></a>De configuratie naar de Linux-computer pushen

Configuratie documenten (MOF-bestanden) kunnen worden gepusht naar de Linux-computer met behulp van de cmdlet [Start-DscConfiguration](/powershell/module/psdesiredstateconfiguration/start-dscconfiguration) . Als u deze cmdlet wilt gebruiken, samen met de cmdlets [Get-DscConfiguration](/powershell/module/PSDesiredStateConfiguration/Get-DscConfiguration)of [test-DscConfiguration](/powershell/module/psdesiredstateconfiguration/Test-DSCConfiguration) , op afstand naar een Linux-computer, moet u een CIMSession gebruiken. De cmdlet [New-CimSession](/powershell/module/CimCmdlets/New-CimSession) wordt gebruikt om een **CimSession** te maken op de Linux-computer.

De volgende code laat zien hoe u een CIMSession maakt voor DSC voor Linux.

```powershell
$Node = "ostc-dsc-01"
$Credential = Get-Credential -UserName "root" -Message "Enter Password:"

#Ignore SSL certificate validation
# $opt = New-CimSessionOption -UseSsl -SkipCACheck -SkipCNCheck -SkipRevocationCheck

#Options for a trusted SSL certificate
$opt = New-CimSessionOption -UseSsl

$sessParams = @{
    Credential = $credential
    ComputerName = $Node
    Port = 5986
    Authentication = 'basic'
    SessionOption = $opt
    OperationTimeoutSec = 90
}

$Sess = New-CimSession @sessParams
```

> [!NOTE]
> De gebruikers referenties voor de push-modus moeten de hoofd gebruiker zijn op de Linux-computer. Alleen SSL/TLS-verbindingen worden ondersteund voor DSC voor Linux, de `New-CimSession` moet worden gebruikt met de para meter ??? UseSSL die is ingesteld op $True. Het SSL-certificaat dat wordt gebruikt door OMI (voor DSC) is opgegeven in het bestand: `/etc/opt/omi/conf/omiserver.conf` met de eigenschappen: pemfile en keyfile. Als dit certificaat niet wordt vertrouwd door de Windows-computer waarop u de cmdlet [New-CimSession](/powershell/module/CimCmdlets/New-CimSession) uitvoert, kunt u certificaat validatie negeren met de CimSession-opties: `-SkipCACheck -SkipCNCheck -SkipRevocationCheck`

Voer de volgende opdracht uit om de DSC-configuratie naar het Linux-knoop punt te pushen.

`Start-DscConfiguration -Path:"C:\temp" -CimSession $Sess -Wait -Verbose`

### <a name="distribute-the-configuration-with-a-pull-server"></a>De configuratie distribueren met een pull-server

Configuraties kunnen worden gedistribueerd naar een Linux-computer met een pull-server, net zoals voor Windows-computers. Zie [Windows Power shell desired state Configuration pull servers](../pull-server/pullServer.md)(Engelstalig) voor hulp bij het gebruik van een pull-server. Voor aanvullende informatie en beperkingen met betrekking tot het gebruik van Linux-computers met een pull-Server raadpleegt u de release opmerkingen voor de gewenste status configuratie voor Linux.

### <a name="working-with-configurations-locally"></a>Lokaal met configuraties werken

DSC voor Linux bevat scripts voor het werken met de configuratie van de lokale Linux-computer. Deze scripts zijn te vinden in `/opt/microsoft/dsc/Scripts` en bevatten het volgende:

- GetDscConfiguration.py

  Retourneert de huidige configuratie die op de computer is toegepast. Vergelijkbaar met de cmdlet Windows Power shell cmdlet `Get-DscConfiguration` .

  `# sudo ./GetDscConfiguration.py`

- GetDscLocalConfigurationManager.py

  Retourneert de huidige meta-configuratie die op de computer is toegepast. Vergelijkbaar met de cmdlet [Get-DSCLocalConfigurationManager](/powershell/module/PSDesiredStateConfiguration/Get-DscLocalConfigurationManager) cmdlet.

  `# sudo ./GetDscLocalConfigurationManager.py`

- InstallModule.py

  Hiermee wordt een aangepaste DSC-resource module ge??nstalleerd. Vereist het pad naar een zip-bestand met de module gedeelde object bibliotheek en schema-MOF-bestanden.

  `# sudo ./InstallModule.py /tmp/cnx_Resource.zip`

- RemoveModule.py

  Hiermee verwijdert u een aangepaste DSC-resource module. Vereist de naam van de module die u wilt verwijderen.

  `# sudo ./RemoveModule.py cnx_Resource`

- StartDscLocalConfigurationManager.py

  Past een MOF-configuratie bestand op de computer toe. Vergelijkbaar met de cmdlet [Start-DscConfiguration](/powershell/module/psdesiredstateconfiguration/start-dscconfiguration) . Vereist het pad naar de configuratie-MOF die moet worden toegepast.

  `# sudo ./StartDscLocalConfigurationManager.py ???configurationmof /tmp/localhost.mof`

- SetDscLocalConfigurationManager.py

  Past een MOF-bestand van de meta configuratie toe op de computer. Vergelijkbaar met de cmdlet [set-DSCLocalConfigurationManager](/powershell/module/PSDesiredStateConfiguration/Set-DscLocalConfigurationManager) . Vereist het pad naar de meta configuratie-MOF die moet worden toegepast.

  `# sudo ./SetDscLocalConfigurationManager.py ???configurationmof /tmp/localhost.meta.mof`

## <a name="powershell-desired-state-configuration-for-linux-log-files"></a>Power shell desired state Configuration voor Linux-logboek bestanden

De volgende logboek bestanden worden gegenereerd voor DSC voor Linux-berichten.

|     Logboekbestand      |     Directory      |                                               Description                                                |
| ----------------- | ------------------ | -------------------------------------------------------------------------------------------------------- |
| **omiserver. log** | `/var/opt/omi/log` | Berichten met betrekking tot de werking van de OMI CIM-server.                                                |
| **DSC. log**       | `/var/opt/omi/log` | Berichten met betrekking tot de werking van de lokale Configuration Manager (LCM) en DSC-bron bewerkingen. |
