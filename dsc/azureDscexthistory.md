---
description: Meer informatie over de geschiedenis voor de uitbreiding Desired State Configuration (DSC) in Azure.
ms.date: 05/09/2018
keywords: DSC, azure, powershell-uitbreiding
title: Versiegeschiedenis van Azure DSC-extensie
ms.openlocfilehash: 81dfcf81bd8f8685a0c8c81cd07bc5447e1abf94
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 05/16/2018
ms.locfileid: "34189938"
---
# <a name="azure-desired-state-configuration-extension-version-history"></a>Versiegeschiedenis van Azure gewenst status configuratie-uitbreiding

De VM-extensie voor Azure Desired State Configuration (DSC) wordt bijgewerkt wanneer nodig voor de ondersteuning van verbeteringen en nieuwe mogelijkheden die worden geleverd door Azure, Windows Server en de Windows Management Framework (WMF) met Windows PowerShell.

In dit artikel wordt bevatten informatie over elke versie van de Azure DSC VM-extensie welke omgevingen ondersteunt, en opmerkingen toe te voegen en opmerkingen van nieuwe functies of wijzigingen.

## <a name="latest-versions"></a>Meest recente versies

### <a name="version-276"></a>Versie 2.76

- **Releasedatum:**
  - 9 mei 2018
- **Ondersteuning van het besturingssysteem:**
  - Windows Server 2016
  - Windows Server 2012 R2
  - Windows Server 2012
  - Windows Server 2008 R2 SP1
  - Client voor Windows 7/8.1/10
  - Nano Server
- **WMF ondersteuning:**
  - WMF 5.1
  - WMF 5.0 RTM
  - WMF 4.0 bijwerken
  - WMF 4.0
- **Omgeving:**
  - Azure
- **Opmerking:** DSC door deze versie wordt gebruikt om te worden opgenomen in Windows Server 2016; voor andere Windows-besturingssystemen installeert de [Windows Management Framework 5.1](https://blogs.msdn.microsoft.com/powershell/2016/12/06/wmf-5-1-releasing-january-2017/) (installeren van WMF opnieuw opstarten vereist). DSC-rol is voor de Nano-Server geïnstalleerd op de virtuele machine.
- **Nieuwe functies**
  - Verbetering van de metagegevens van de uitbreiding voor substatus en andere kleine oplossingen voor problemen.

### <a name="version-219"></a>Versie 2.19

- **Releasedatum:**
  - 3 juni 2016
- **Ondersteuning van het besturingssysteem:**
  - Windows Server 2016 Technical Preview
  - Windows Server 2012 R2
  - Windows Server 2012
  - Windows Server 2008 R2 SP1
- **WMF ondersteuning:**
  - WMF 5.0 RTM
  - WMF 4.0 bijwerken
  - WMF 4.0
- **Omgeving:**
  - Azure
  - Azure China
  - Azure Government
- **Opmerking:** DSC door deze versie wordt gebruikt om te worden opgenomen in Windows Server 2016 Technical Preview; voor andere besturingssystemen, installeert de [Windows Management Framework 5.0 RTM](https://blogs.msdn.microsoft.com/powershell/2015/12/16/windows-management-framework-wmf-5-0-rtm-is-now-available/) (installeren van WMF opnieuw opstarten vereist).
- **Nieuwe functies**
  - De DSC-uitbreiding is nu op aangehouden Azure China. Deze versie bevat voornamelijk oplossingen voor het uitvoeren van de extensie op Azure China.

## <a name="supported-versions"></a>Ondersteunde versies

> [!WARNING]
> Versie 2.4 via 2,13 gebruik WMF 5.0 Public Preview waarvan handtekeningcertificaten in augustus 2016 verlopen.  Zie voor meer informatie over dit probleem [blogbericht](https://blogs.msdn.microsoft.com/powershell/2016/05/24/azure-dsc-extension-versions-2-4-up-to-2-13-will-retire-in-august/).

### <a name="version-275"></a>Versie 2,75

- **Releasedatum:** 5 maart 2018
- **Ondersteuning van het besturingssysteem:** Windows Server 2016, Windows Server 2012 R2, Windows Server 2012, Windows Server 2008 R2 SP1, Windows Client 7/8.1/10, Nano Server
- **Ondersteuning van WMF:** WMF 5.1, WMF 5.0 RTM, WMF 4.0-Update, WMF 4.0
- **Omgeving:** Azure
- **Opmerking:** DSC door deze versie wordt gebruikt om te worden opgenomen in Windows Server 2016; voor andere Windows-besturingssystemen installeert de [Windows Management Framework 5.1](https://blogs.msdn.microsoft.com/powershell/2016/12/06/wmf-5-1-releasing-january-2017/) (installeren van WMF opnieuw opstarten vereist). DSC-rol is voor de Nano-Server geïnstalleerd op de virtuele machine.
- **Nieuwe functies**
  - Na de GitHub recente verplaatsen naar TLS 1.2, kan niet vrijgeven van een virtuele machine aan Azure Automation DSC met ZELFOPLOSSING Resource Manager-sjablonen die beschikbaar zijn op Azure Marketplace of gebruik van DSC-extensie om een configuratie die wordt gehost op GitHub. Hier ziet u een foutbericht weergegeven dat vergelijkbaar is met de volgende tijdens de implementatie van de extensie:

    ```json
    {
        "code": "DeploymentFailed",
        "message": "At least one resource deployment operation failed. Please list deployment operations for details. Please see https://aka.ms/arm-debug for usage details.",
        "details": [{
            "code": "Conflict",
            "message": "{
                \"status\": \"Failed\",
                \"error\": {
                    \"code\": \"ResourceDeploymentFailure\",
                    \"message\": \"The resource operation completed with terminal provisioning state 'Failed'.\",
                    \"details\": [ {
                        \"code\": \"VMExtensionProvisioningError\",
                        \"message\": \"VM has reported a failure when processing extension 'Microsoft.Powershell.DSC'.
                        Error message: \\\"The DSC Extension failed to execute: Error downloading
                        https://github.com/Azure/azure-quickstart-templates/raw/master/dsc-extension-azure-automation-pullserver/UpdateLCMforAAPull.zip
                        after 29 attempts: The request was aborted: Could not create SSL/TLS secure channel..\\nMore information about the failure can
                        be found in the logs located under 'C:\\\\WindowsAzure\\\\Logs\\\\Plugins\\\\Microsoft.Powershell.DSC\\\\2.74.0.0' on the VM.\\\".\"
                    } ]
                }
            }"
        }]
    }
    ```

  - TLS 1.2 wordt nu afgedwongen in de nieuwe versie van de extensie. Tijdens de implementatie van de extensie als u al de AutoUpgradeMinorVersion = true in het Resource Manager-sjabloon en de uitbreiding wordt autoupgraded naar 2,75 get. Geef voor handmatige updates `TypeHandlerVersion = 2.75` in de Resource Manager-sjabloon.

### <a name="version-270---272"></a>Versie 2,70 2.72

- **Releasedatum:** 13 November 2017
- **Ondersteuning van het besturingssysteem:** Windows Server 2016, Windows Server 2012 R2, Windows Server 2012, Windows Server 2008 R2 SP1, Windows Client 7/8.1/10, Nano Server
- **Ondersteuning van WMF:** WMF 5.1, WMF 5.0 RTM, WMF 4.0-Update, WMF 4.0
- **Omgeving:** Azure
- **Opmerking:** DSC door deze versie wordt gebruikt om te worden opgenomen in Windows Server 2016; voor andere Windows-besturingssystemen installeert de [Windows Management Framework 5.1](https://blogs.msdn.microsoft.com/powershell/2016/12/06/wmf-5-1-releasing-january-2017/) (installeren van WMF opnieuw opstarten vereist). DSC-rol is voor de Nano-Server geïnstalleerd op de virtuele machine.
- **Nieuwe functies**
  - Bug oplossingen & verbeteringen die eenvoudiger met Azure Automation DSC via de UI-portal als Resource Manager-sjabloon.  Zie voor meer informatie [configuratiescript standaard](https://docs.microsoft.com/en-us/azure/virtual-machines/windows/extensions-dsc-overview#default-configuration-script) in de documentatie van de DSC-extensie.

### <a name="version-226"></a>Versie 2, 26 g

- **Releasedatum:** 9 juni 2017
- **Ondersteuning van het besturingssysteem:** Windows Server 2016, Windows Server 2012 R2, Windows Server 2012, Windows Server 2008 R2 SP1, Windows Client 7/8.1/10, Nano Server
- **Ondersteuning van WMF:** WMF 5.1, WMF 5.0 RTM, WMF 4.0-Update, WMF 4.0
- **Omgeving:** Azure
- **Opmerking:** DSC door deze versie wordt gebruikt om te worden opgenomen in Windows Server 2016; voor andere Windows-besturingssystemen installeert de [Windows Management Framework 5.1](https://blogs.msdn.microsoft.com/powershell/2016/12/06/wmf-5-1-releasing-january-2017/) (installeren van WMF opnieuw opstarten vereist). DSC-rol is voor de Nano-Server geïnstalleerd op de virtuele machine.
- **Nieuwe functies**
  - Telemetrie is verbeterd.

### <a name="version-225"></a>Versie 2,25

- **Releasedatum:** 2 juni 2017
- **Ondersteuning van het besturingssysteem:** Windows Server 2016, Windows Server 2012 R2, Windows Server 2012, Windows Server 2008 R2 SP1, Windows Client 7/8.1/10, Nano Server
- **Ondersteuning van WMF:** WMF 5.1, WMF 5.0 RTM, WMF 4.0-Update, WMF 4.0
- **Omgeving:** Azure
- **Opmerking:** DSC door deze versie wordt gebruikt om te worden opgenomen in Windows Server 2016; voor andere Windows-besturingssystemen installeert de [Windows Management Framework 5.1](https://blogs.msdn.microsoft.com/powershell/2016/12/06/wmf-5-1-releasing-january-2017/) (installeren van WMF opnieuw opstarten vereist). DSC-rol is voor de Nano-Server geïnstalleerd op de virtuele machine.
- **Nieuwe functies**
  - Er zijn verschillende oplossingen voor problemen en andere kleine verbeteringen toegevoegd.

### <a name="version-224"></a>Versie 2,24

- **Releasedatum:** 13 April 2017
- **Ondersteuning van het besturingssysteem:** Windows Server 2016, Windows Server 2012 R2, WindowsServer 2012, Windows Server 2008 R2 SP1 Nano Server
- **Ondersteuning van WMF:** WMF 5.1, WMF 5.0 RTM, WMF 4.0-Update, WMF 4.0
- **Omgeving:** Azure
- **Opmerking:** DSC door deze versie wordt gebruikt om te worden opgenomen in Windows Server 2016; voor andere Windows-besturingssystemen installeert de [Windows Management Framework 5.1](https://blogs.msdn.microsoft.com/powershell/2016/12/06/wmf-5-1-releasing-january-2017/) (installeren van WMF opnieuw opstarten vereist). DSC-rol is voor de Nano-Server geïnstalleerd op de virtuele machine.
- **Nieuwe functies**
  - VM UUID & DSC Agent-ID wordt als uitbreiding metagegevens. Er zijn andere kleine verbeteringen toegevoegd.

### <a name="version-223"></a>Versie 2.23

- **Releasedatum:** 15 maart 2017
- **Ondersteuning van het besturingssysteem:** Windows Server 2016, Windows Server 2012 R2, WindowsServer 2012, Windows Server 2008 R2 SP1 Nano Server
- **Ondersteuning van WMF:** WMF 5.1, WMF 5.0 RTM, WMF 4.0-Update, WMF 4.0
- **Omgeving:** Azure
- **Opmerking:** DSC door deze versie wordt gebruikt om te worden opgenomen in Windows Server 2016; voor andere Windows-besturingssystemen installeert de [Windows Management Framework 5.1](https://blogs.msdn.microsoft.com/powershell/2016/12/06/wmf-5-1-releasing-january-2017/) (installeren van WMF opnieuw opstarten vereist). DSC-rol is voor de Nano-Server geïnstalleerd op de virtuele machine.
- **Nieuwe functies**
  - Er zijn veel oplossingen voor problemen en andere verbeteringen toegevoegd.

### <a name="version-222"></a>Versie 2,22

- **Releasedatum:** 8 februari 2017
- **Ondersteuning van het besturingssysteem:** Windows Server 2016, Windows Server 2012 R2, WindowsServer 2012, Windows Server 2008 R2 SP1 Nano Server
- **Ondersteuning van WMF:** WMF 5.1, WMF 5.0 RTM, WMF 4.0-Update, WMF 4.0
- **Omgeving:** Azure
- **Opmerking:** DSC door deze versie wordt gebruikt om te worden opgenomen in Windows Server 2016; voor andere Windows-besturingssystemen installeert de [Windows Management Framework 5.1](https://blogs.msdn.microsoft.com/powershell/2016/12/06/wmf-5-1-releasing-january-2017/) (installeren van WMF opnieuw opstarten vereist). DSC-rol is voor de Nano-Server geïnstalleerd op de virtuele machine.
- **Nieuwe functies**
  - De DSC-uitbreiding biedt nu ondersteuning voor WMF 5.1.
  - Secundaire dat andere verbeteringen zijn toegevoegd.

### <a name="version-221"></a>Versie 2.21

- **Releasedatum:** 2 December 2016
- **Ondersteuning van het besturingssysteem:** Windows Server 2016, Windows Server 2012 R2, WindowsServer 2012, Windows Server 2008 R2 SP1 Nano Server
- **Ondersteuning van WMF:** WMF 5.1 Preview, WMF 5.0 RTM, WMF 4.0-Update, WMF 4.0
- **Omgeving:** Azure
- **Opmerking:** DSC door deze versie wordt gebruikt om te worden opgenomen in Windows Server 2016; voor andere Windows-besturingssystemen installeert de [Windows Management Framework 5.0 RTM](https://blogs.msdn.microsoft.com/powershell/2015/12/16/windows-management-framework-wmf-5-0-rtm-is-now-available/) (installeren van WMF opnieuw opstarten vereist). DSC-rol is voor de Nano-Server geïnstalleerd op de virtuele machine.
- **Nieuwe functies**
  - De DSC-extensie is nu beschikbaar op Nano Server. Deze versie bevat voornamelijk codewijzigingen voor het uitvoeren van de extensie op Nano Server.
  - Secundaire dat andere verbeteringen zijn toegevoegd.

### <a name="version-220"></a>Versie 2,20

- **Releasedatum:** 2 augustus 2016
- **Ondersteuning van het besturingssysteem:** Windows Server 2016 Technical Preview, Windows Server 2012 R2, Windows Server 2012, Windows Server 2008 R2 SP1
- **Ondersteuning van WMF:** WMF 5.1 Preview, WMF 5.0 RTM, WMF 4.0-Update, WMF 4.0
- **Omgeving:** Azure
- **Opmerking:** DSC door deze versie wordt gebruikt om te worden opgenomen in Windows Server 2016 Technical Preview; voor andere Windows-besturingssystemen installeert de [Windows Management Framework 5.0 RTM](https://blogs.msdn.microsoft.com/powershell/2015/12/16/windows-management-framework-wmf-5-0-rtm-is-now-available/) (installeren van WMF opnieuw opstarten vereist).
- **Nieuwe functies**
  - Ondersteuning voor WMF 5.1 Preview. Als eerste wordt gepubliceerd, deze versie is een optionele upgrade en moest u Geef Wmfversion = ' 5.1PP' in het Resource Manager-sjablonen voor het installeren van WMF 5.1 preview. Wmfversion = 'nieuwste' nog steeds installeert de [WMF 5.0 RTM](https://blogs.msdn.microsoft.com/powershell/2015/12/16/windows-management-framework-wmf-5-0-rtm-is-now-available/). Zie voor meer informatie over WMF 5.1 preview [deze blog]( https://blogs.msdn.microsoft.com/powershell/2016/07/16/announcing-windows-management-framework-wmf-5-1-preview/).
  - Andere correcties voor secundaire en verbeteringen zijn toegevoegd.

### <a name="version--219"></a>Versie 2.19

- **Releasedatum:** 3 juni 2016
- **Ondersteuning van het besturingssysteem:** Windows Server 2016 Technical Preview, Windows Server 2012 R2, Windows Server 2012, Windows Server 2008 R2 SP1
- **Ondersteuning van WMF:** WMF 5.0 RTM, WMF 4.0-Update, WMF 4.0
- **Omgeving:** Azure, Azure China Azure Government
- **Opmerking:** DSC door deze versie wordt gebruikt om te worden opgenomen in Windows Server 2016 Technical Preview; voor andere Windows-besturingssystemen installeert de [Windows Management Framework 5.0 RTM](https://blogs.msdn.microsoft.com/powershell/2015/12/16/windows-management-framework-wmf-5-0-rtm-is-now-available/) (installeren van WMF opnieuw opstarten vereist).
- **Nieuwe functies**
  - De DSC-extensie is nu vrijgegeven voor Azure China. Deze versie bevat voornamelijk oplossingen voor het uitvoeren van de extensie op Azure China.

### <a name="version-218"></a>Versie 2.18

- **Releasedatum:** 3 juni 2016
- **Ondersteuning van het besturingssysteem:** Windows Server 2016 Technical Preview, Windows Server 2012 R2, Windows Server 2012, Windows Server 2008 R2 SP1
- **Ondersteuning van WMF:** WMF 5.0 RTM, WMF 4.0-Update, WMF 4.0
- **Omgeving:** Azure
- **Opmerking:** DSC door deze versie wordt gebruikt om te worden opgenomen in Windows Server 2016 Technical Preview; voor andere Windows-besturingssystemen installeert de [Windows Management Framework 5.0 RTM](https://blogs.msdn.microsoft.com/powershell/2015/12/16/windows-management-framework-wmf-5-0-rtm-is-now-available/) (installeren van WMF opnieuw opstarten vereist).
- **Nieuwe functies**
  - Controleer de telemetrie niet-blokkerende als een fout tijdens de telemetrie hotfix-download (bekend probleem met het Azure DNS) of installeren optreedt.
  - Voor de onregelmatig probleem vaststellen waar extensie stopt configuration verwerking na opnieuw opstarten. Dit is veroorzaakt door de DSC-uitbreiding moet worden bewaard in de status overgang.
  - Andere correcties voor secundaire en verbeteringen zijn toegevoegd.

### <a name="version-217"></a>Versie 2.17

- **Releasedatum:** 26 April 2016
- **Ondersteuning van het besturingssysteem:** Windows Server 2016 Technical Preview, Windows Server 2012 R2, Windows Server 2012, Windows Server 2008 R2 SP1
- **Ondersteuning van WMF:** WMF 5.0 RTM, WMF 4.0-Update, WMF 4.0
- **Omgeving:** Azure
- **Opmerking:** DSC door deze versie wordt gebruikt om te worden opgenomen in Windows Server 2016 Technical Preview; voor andere Windows-besturingssystemen installeert de [Windows Management Framework 5.0 RTM](https://blogs.msdn.microsoft.com/powershell/2015/12/16/windows-management-framework-wmf-5-0-rtm-is-now-available/) (installeren van WMF opnieuw opstarten vereist).
- **Nieuwe functies**
  - Ondersteuning voor WMF 4.0-Update. Zie voor meer informatie over WMF 4.0-Update [deze blog](https://blogs.msdn.microsoft.com/powershell/2016/01/19/windows-management-framework-wmf-4-0-update-now-available-for-windows-server-2012-windows-server-2008-r2-sp1-and-windows-7-sp1/).
  - Pogingslogica op fouten die optreden tijdens de installatie van de DSC-extensie of boeken extensie tijdens het toepassen van een DSC-configuratie installeren. Als onderdeel van deze wijziging, wordt de uitbreiding voor de installatie opnieuw uitvoeren als een vorige installatie is mislukt of opnieuw vast een DSC-configuratie die was eerder is mislukt, maximaal drie keer totdat het de voltooiingsstatus (geslaagde of mislukte) bereikt of als een nieuwe aanvraag afkomstig is. Als de extensie is mislukt vanwege ongeldige gebruiker instellingen/gebruikersinvoer, probeert het niet opnieuw. In dit geval moet de extensie opnieuw worden aangeroepen met een nieuwe aanvraag en gebruikersinstellingen te corrigeren. Opmerking: De DSC-uitbreiding is afhankelijk van de Azure VM-agent voor de nieuwe pogingen. Azure VM-agent roept de uitbreiding met de laatste mislukte aanvraag totdat het slagen of fout status bereikt.

### <a name="version-216"></a>Versie 2,16

- **Releasedatum:** 21 April 2016
- **Ondersteuning van het besturingssysteem:** Windows Server 2016 Technical Preview, Windows Server 2012 R2, Windows Server 2012, Windows Server 2008 R2 SP1
- **Ondersteuning van WMF:** WMF 5.0 RTM, WMF 4.0
- **Omgeving:** Azure
- **Opmerking:** DSC door deze versie wordt gebruikt om te worden opgenomen in Windows Server 2016 Technical Preview; voor andere Windows-besturingssystemen installeert de [Windows Management Framework 5.0 RTM](https://blogs.msdn.microsoft.com/powershell/2015/12/16/windows-management-framework-wmf-5-0-rtm-is-now-available/) (installeren van WMF opnieuw opstarten vereist).
- **Nieuwe functies**
  - Verbetering van de foutafhandeling en andere kleine oplossingen voor problemen.
  - Nieuwe eigenschap in de instellingen van de DSC-extensie. 'ForcePullAndApply' in AdvancedOptions wordt toegevoegd aan de DSC-extensie inschakelen DSC-configuraties vast wanneer de vernieuwingsmodus Pull (in plaats van de Push-standaardmodus). Raadpleeg voor meer informatie [deze blog](https://blogs.msdn.microsoft.com/powershell/2016/02/26/arm-dsc-extension-settings/) voor meer informatie over de instellingen van de DSC-extensie.

### <a name="version-215"></a>Versie 2.15

- **Releasedatum:** 14 maart 2016
- **Ondersteuning van het besturingssysteem:** Windows Server 2016 Technical Preview, Windows Server 2012 R2, Windows Server 2012, Windows Server 2008 R2 SP1
- **Ondersteuning van WMF:** WMF 5.0 RTM, WMF 4.0
- **Omgeving:** Azure
- **Opmerking:** DSC door deze versie wordt gebruikt om te worden opgenomen in Windows Server 2016 Technical Preview; voor andere Windows-besturingssystemen installeert de [Windows Management Framework 5.0 RTM](https://blogs.msdn.microsoft.com/powershell/2015/12/16/windows-management-framework-wmf-5-0-rtm-is-now-available/) (installeren van WMF opnieuw opstarten vereist).
- **Nieuwe functies**
  - In de versie van de uitbreiding 2.14 zijn wijzigingen voor het installeren van WMF RTM opgenomen. Tijdens een upgrade van versie van de uitbreiding 2.13.2.0-2.14.0.0, merkt u dat enkele DSC-cmdlets mislukken of uw configuratie is mislukt met een fout: 'Er is geen exemplaar met de gegeven eigenschapswaarden gevonden'. Zie voor meer informatie de [DSC-releaseopmerkingen](https://msdn.microsoft.com/en-us/powershell/wmf/limitation_dsc). De tijdelijke oplossingen voor deze problemen zijn toegevoegd in 2.15 versie.
  - Helaas als u versie 2.14 al hebt geïnstalleerd en worden uitgevoerd in een van de bovenstaande twee problemen, moet u deze stappen handmatig uitvoeren.  In een PowerShell-sessie met verhoogde bevoegdheid:
    - `Remove-Item -Path $env:SystemRoot\system32\Configuration\DSCEngineCache.mof`
    - `mofcomp $env:windir\system32\wbem\DscCoreConfProv.mof`

### <a name="version-214"></a>Versie 2.14

- **Releasedatum:** 25 februari 2016
- **Ondersteuning van het besturingssysteem:** Windows Server 2016 Technical Preview, Windows Server 2012 R2, Windows Server 2012, Windows Server 2008 R2 SP1
- **Ondersteuning van WMF:** WMF 5.0 RTM, WMF 4.0
- **Omgeving:** Azure
- **Opmerking:** DSC door deze versie wordt gebruikt om te worden opgenomen in Windows Server 2016 Technical Preview; voor andere Windows-besturingssystemen installeert de [Windows Management Framework 5.0 RTM](https://blogs.msdn.microsoft.com/powershell/2015/12/16/windows-management-framework-wmf-5-0-rtm-is-now-available/) (installeren van WMF opnieuw opstarten vereist).
- **Nieuwe functies**
  - Maakt gebruik van WMF RTM.
  - Hiermee schakelt u gegevensverzameling om te verbeteren van de kwaliteit van de DSC-uitbreiding. Zie voor meer informatie [de blog](https://blogs.msdn.microsoft.com/powershell/2016/02/02/azure-dsc-extension-data-collection-2/).
  - Biedt een indeling met bijgewerkte instellingen voor de extensie in de Resource Manager-sjabloon. Zie voor meer informatie [de blog](https://blogs.msdn.microsoft.com/powershell/2016/02/26/arm-dsc-extension-settings/).
  - Oplossingen voor problemen en andere verbeteringen.

## <a name="next-steps"></a>Volgende stappen

- Voor meer informatie over PowerShell DSC, gaat u naar de [PowerShell-documentatiecentrum](overview.md).
- Bekijk de [Resource Manager-sjabloon voor de uitbreiding van DSC](/azure/virtual-machines/windows/extensions-dsc-template).
- Ga voor meer functionaliteit die u beheren kunt met behulp van PowerShell DSC, en voor meer DSC-resources, het [PowerShell gallery](https://www.powershellgallery.com/packages?q=DscResource&x=0&y=0).
- Zie voor meer informatie over gevoelige parameters doorgeven in configuraties [beheren van referenties veilig met de DSC-uitbreiding handler](/azure/virtual-machines/windows/extensions-dsc-credentials).