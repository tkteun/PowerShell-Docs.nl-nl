---
description: Meer informatie over de versiegeschiedenis van de extensie Desired State Configuration (DSC) in Azure.
ms.date: 06/21/2018
keywords: DSC, powershell, azure,-extensie
title: Versiegeschiedenis van Azure DSC-extensie
ms.openlocfilehash: 2c076e3beccc15e99af2327820916d7a4d28da68
ms.sourcegitcommit: 00ff76d7d9414fe585c04740b739b9cf14d711e1
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 12/14/2018
ms.locfileid: "53404366"
---
# <a name="azure-desired-state-configuration-extension-version-history"></a>Versiegeschiedenis van Azure Desired State Configuration-extensie

De VM-extensie voor Azure Desired State Configuration (DSC) wordt bijgewerkt zo nodig voor de ondersteuning van verbeteringen en nieuwe mogelijkheden die door Azure, Windows Server en de Windows Management Framework (WMF) met Windows PowerShell.

In dit artikel bevat informatie over elke versie van de Azure DSC VM-extensie welke omgevingen ondersteunt, en opmerkingen en opmerkingen over nieuwe functies of wijzigingen.

## <a name="latest-version"></a>Meest recente versie

### <a name="version-276"></a>Versie 2.76

- **Uitgebracht op:**
  - 9 mei 2018 (Azure) | Juni 21 2018 (Azure China, Azure Government)
- **Ondersteuning voor het besturingssysteem:**
  - Windows Server 2016
  - Windows Server 2012 R2
  - Windows Server 2012
  - Windows Server 2008 R2 SP1
  - Client voor Windows 7/8.1/10
  - Nano Server
- **WMF-ondersteuning:**
  - WMF 5.1
  - WMF 5.0 RTM
  - WMF 4.0 bijwerken
  - WMF 4.0
- **Omgeving:**
  - Azure
  - Azure China
  - Azure Government
- **Opmerking:** Deze versie wordt DSC opgenomen in Windows Server 2016; voor andere Windows-besturingssystemen, installeert het de [Windows Management Framework 5.1](https://blogs.msdn.microsoft.com/powershell/2016/12/06/wmf-5-1-releasing-january-2017/) (installeren van WMF opnieuw opstarten vereist). DSC-rol is voor Nano-Server geïnstalleerd op de virtuele machine.
- **Nieuwe functies**
  - Verbetering van de extensiemetagegevens voor substatus en overige kleine correcties.

## <a name="supported-versions"></a>Ondersteunde versies

> [!WARNING]
> Versies 2.4 via 2,13 maken gebruik van WMF 5.0 Public Preview waarvan handtekeningcertificaten in augustus 2016 verlopen.  Zie voor meer informatie over dit probleem [blogbericht](https://blogs.msdn.microsoft.com/powershell/2016/05/24/azure-dsc-extension-versions-2-4-up-to-2-13-will-retire-in-august/).

### <a name="version-275"></a>Versie 2,75

- **Uitgebracht op:** 5 maart 2018
- **Ondersteuning voor het besturingssysteem:** Windows Server 2016, Windows Server 2012 R2, Windows Server 2012, Windows Server 2008 R2 SP1, Windows Client 7/8.1/10, Nano Server
- **WMF-ondersteuning:** WMF 5.1, WMF 5.0 RTM, WMF 4.0 Update, WMF 4.0
- **Omgeving:** Azure
- **Opmerking:** Deze versie wordt DSC opgenomen in Windows Server 2016; voor andere Windows-besturingssystemen, installeert het de [Windows Management Framework 5.1](https://blogs.msdn.microsoft.com/powershell/2016/12/06/wmf-5-1-releasing-january-2017/) (installeren van WMF opnieuw opstarten vereist). DSC-rol is voor Nano-Server geïnstalleerd op de virtuele machine.
- **Nieuwe functies**
  - Na van GitHub recente overstappen op TLS 1.2, kan onboarding niet een virtuele machine naar Azure Automation DSC en ZELFGEMAAKT Resource Manager-sjablonen die beschikbaar zijn met op Azure Marketplace of DSC-extensie gebruiken om op te halen van een configuratie die wordt gehost op GitHub. Hier ziet u een fout die vergelijkbaar is met het volgende bij het implementeren van de extensie:

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

  - TLS 1.2 wordt nu afgedwongen in de nieuwe versie van de extensie. Tijdens het implementeren van de extensie als u al werkt met de AutoUpgradeMinorVersion = true in het Resource Manager-sjabloon en vervolgens de extensie autoupgraded naar 2,75 krijgt. Geef voor handmatige updates `TypeHandlerVersion = 2.75` in de Resource Manager-sjabloon.

### <a name="version-270---272"></a>Versie 2.70 2.72

- **Uitgebracht op:** 13 november 2017
- **Ondersteuning voor het besturingssysteem:** Windows Server 2016, Windows Server 2012 R2, Windows Server 2012, Windows Server 2008 R2 SP1, Windows Client 7/8.1/10, Nano Server
- **WMF-ondersteuning:** WMF 5.1, WMF 5.0 RTM, WMF 4.0 Update, WMF 4.0
- **Omgeving:** Azure
- **Opmerking:** Deze versie wordt DSC opgenomen in Windows Server 2016; voor andere Windows-besturingssystemen, installeert het de [Windows Management Framework 5.1](https://blogs.msdn.microsoft.com/powershell/2016/12/06/wmf-5-1-releasing-january-2017/) (installeren van WMF opnieuw opstarten vereist). DSC-rol is voor Nano-Server geïnstalleerd op de virtuele machine.
- **Nieuwe functies**
  - Bug opgelost en verbeteringen vereenvoudigen met behulp van Azure Automation DSC via de gebruikersinterface van de portal, evenals de Resource Manager-sjabloon.  Zie voor meer informatie, [configuratiescript standaard](/azure/virtual-machines/extensions/dsc-overview) in de documentatie van DSC-extensie.

### <a name="version-226"></a>Versie 2, 26 g

- **Uitgebracht op:** 9 juni 2017
- **Ondersteuning voor het besturingssysteem:** Windows Server 2016, Windows Server 2012 R2, Windows Server 2012, Windows Server 2008 R2 SP1, Windows Client 7/8.1/10, Nano Server
- **WMF-ondersteuning:** WMF 5.1, WMF 5.0 RTM, WMF 4.0 Update, WMF 4.0
- **Omgeving:** Azure
- **Opmerking:** Deze versie wordt DSC opgenomen in Windows Server 2016; voor andere Windows-besturingssystemen, installeert het de [Windows Management Framework 5.1](https://blogs.msdn.microsoft.com/powershell/2016/12/06/wmf-5-1-releasing-january-2017/) (installeren van WMF opnieuw opstarten vereist). DSC-rol is voor Nano-Server geïnstalleerd op de virtuele machine.
- **Nieuwe functies**
  - Verbeteringen van telemetrie.

### <a name="version-225"></a>Versie 2,25

- **Uitgebracht op:** 2 juni 2017
- **Ondersteuning voor het besturingssysteem:** Windows Server 2016, Windows Server 2012 R2, Windows Server 2012, Windows Server 2008 R2 SP1, Windows Client 7/8.1/10, Nano Server
- **WMF-ondersteuning:** WMF 5.1, WMF 5.0 RTM, WMF 4.0 Update, WMF 4.0
- **Omgeving:** Azure
- **Opmerking:** Deze versie wordt DSC opgenomen in Windows Server 2016; voor andere Windows-besturingssystemen, installeert het de [Windows Management Framework 5.1](https://blogs.msdn.microsoft.com/powershell/2016/12/06/wmf-5-1-releasing-january-2017/) (installeren van WMF opnieuw opstarten vereist). DSC-rol is voor Nano-Server geïnstalleerd op de virtuele machine.
- **Nieuwe functies**
  - Er zijn verschillende oplossingen voor problemen en andere kleine verbeteringen toegevoegd.

### <a name="version-224"></a>Versie 2,24

- **Uitgebracht op:** Vanaf 13 april 2017
- **Ondersteuning voor het besturingssysteem:** Windows Server 2016, Windows Server 2012 R2, Windows Server 2012, Windows Server 2008 R2 SP1, Nano Server
- **WMF-ondersteuning:** WMF 5.1, WMF 5.0 RTM, WMF 4.0 Update, WMF 4.0
- **Omgeving:** Azure
- **Opmerking:** Deze versie wordt DSC opgenomen in Windows Server 2016; voor andere Windows-besturingssystemen, installeert het de [Windows Management Framework 5.1](https://blogs.msdn.microsoft.com/powershell/2016/12/06/wmf-5-1-releasing-january-2017/) (installeren van WMF opnieuw opstarten vereist). DSC-rol is voor Nano-Server geïnstalleerd op de virtuele machine.
- **Nieuwe functies**
  - Wordt als extensiemetagegevens aangegeven VM UUID & ID van de DSC-Agent. Andere kleine verbeteringen zijn toegevoegd.

### <a name="version-223"></a>Versie 2.23

- **Uitgebracht op:** 15 maart 2017
- **Ondersteuning voor het besturingssysteem:** Windows Server 2016, Windows Server 2012 R2, Windows Server 2012, Windows Server 2008 R2 SP1, Nano Server
- **WMF-ondersteuning:** WMF 5.1, WMF 5.0 RTM, WMF 4.0 Update, WMF 4.0
- **Omgeving:** Azure
- **Opmerking:** Deze versie wordt DSC opgenomen in Windows Server 2016; voor andere Windows-besturingssystemen, installeert het de [Windows Management Framework 5.1](https://blogs.msdn.microsoft.com/powershell/2016/12/06/wmf-5-1-releasing-january-2017/) (installeren van WMF opnieuw opstarten vereist). DSC-rol is voor Nano-Server geïnstalleerd op de virtuele machine.
- **Nieuwe functies**
  - Veel oplossingen voor problemen en andere verbeteringen zijn toegevoegd.

### <a name="version-222"></a>Versie 2,22

- **Uitgebracht op:** 8 februari 2017
- **Ondersteuning voor het besturingssysteem:** Windows Server 2016, Windows Server 2012 R2, Windows Server 2012, Windows Server 2008 R2 SP1, Nano Server
- **WMF-ondersteuning:** WMF 5.1, WMF 5.0 RTM, WMF 4.0 Update, WMF 4.0
- **Omgeving:** Azure
- **Opmerking:** Deze versie wordt DSC opgenomen in Windows Server 2016; voor andere Windows-besturingssystemen, installeert het de [Windows Management Framework 5.1](https://blogs.msdn.microsoft.com/powershell/2016/12/06/wmf-5-1-releasing-january-2017/) (installeren van WMF opnieuw opstarten vereist). DSC-rol is voor Nano-Server geïnstalleerd op de virtuele machine.
- **Nieuwe functies**
  - De DSC-extensie biedt nu ondersteuning voor WMF 5.1.
  - Secundaire dat andere verbeteringen zijn toegevoegd.

### <a name="version-221"></a>Versie 2.21

- **Uitgebracht op:** 2 december 2016
- **Ondersteuning voor het besturingssysteem:** Windows Server 2016, Windows Server 2012 R2, Windows Server 2012, Windows Server 2008 R2 SP1, Nano Server
- **WMF-ondersteuning:** WMF 5.1 Preview, WMF 5.0 RTM, WMF 4.0 Update, WMF 4.0
- **Omgeving:** Azure
- **Opmerking:** Deze versie wordt DSC opgenomen in Windows Server 2016; voor andere Windows-besturingssystemen, installeert het de [Windows Management Framework 5.0 RTM](https://blogs.msdn.microsoft.com/powershell/2015/12/16/windows-management-framework-wmf-5-0-rtm-is-now-available/) (installeren van WMF opnieuw opstarten vereist). DSC-rol is voor Nano-Server geïnstalleerd op de virtuele machine.
- **Nieuwe functies**
  - De DSC-extensie is nu beschikbaar in Nano Server. Deze versie bevat voornamelijk code hoeft te wijzigen voor het uitvoeren van de extensie op Nano Server.
  - Secundaire dat andere verbeteringen zijn toegevoegd.

### <a name="version-220"></a>Versie 2,20

- **Uitgebracht op:** 2 augustus 2016
- **Ondersteuning voor het besturingssysteem:** Windows Server 2016 Technical Preview, Windows Server 2012 R2, WindowsServer 2012, Windows Server 2008 R2 SP1
- **WMF-ondersteuning:** WMF 5.1 Preview, WMF 5.0 RTM, WMF 4.0 Update, WMF 4.0
- **Omgeving:** Azure
- **Opmerking:** Deze versie wordt DSC opgenomen in Windows Server 2016 Technical Preview; voor andere Windows-besturingssystemen, installeert het de [Windows Management Framework 5.0 RTM](https://blogs.msdn.microsoft.com/powershell/2015/12/16/windows-management-framework-wmf-5-0-rtm-is-now-available/) (installeren van WMF opnieuw opstarten vereist).
- **Nieuwe functies**
  - Ondersteuning voor WMF 5.1 Preview. Eerst wordt gepubliceerd, deze versie is een optionele upgrade en moest u om op te geven Wmfversion = ' 5.1PP' in Resource Manager-sjablonen voor het installeren van WMF 5.1 preview. Wmfversion = 'latest' nog steeds installeert de [WMF 5.0 RTM](https://blogs.msdn.microsoft.com/powershell/2015/12/16/windows-management-framework-wmf-5-0-rtm-is-now-available/). Zie voor meer informatie over WMF 5.1 preview [deze blog]( https://blogs.msdn.microsoft.com/powershell/2016/07/16/announcing-windows-management-framework-wmf-5-1-preview/).
  - Secundaire van andere oplossingen en verbeteringen zijn toegevoegd.

### <a name="version--219"></a>Versie 2.19

- **Uitgebracht op:** 3 juni 2016
- **Ondersteuning voor het besturingssysteem:** Windows Server 2016 Technical Preview, Windows Server 2012 R2, WindowsServer 2012, Windows Server 2008 R2 SP1
- **WMF-ondersteuning:** WMF 5.0 RTM, WMF 4.0 Update, WMF 4.0
- **Omgeving:** Azure, Azure China, Azure Government
- **Opmerking:** Deze versie wordt DSC opgenomen in Windows Server 2016 Technical Preview; voor andere Windows-besturingssystemen, installeert het de [Windows Management Framework 5.0 RTM](https://blogs.msdn.microsoft.com/powershell/2015/12/16/windows-management-framework-wmf-5-0-rtm-is-now-available/) (installeren van WMF opnieuw opstarten vereist).
- **Nieuwe functies**
  - De DSC-extensie is nu vrijgegeven aan Azure China. Deze versie bevat voornamelijk oplossingen voor het uitvoeren van de uitbreiding op Azure China.

### <a name="version-218"></a>Versie 2.18

- **Uitgebracht op:** 3 juni 2016
- **Ondersteuning voor het besturingssysteem:** Windows Server 2016 Technical Preview, Windows Server 2012 R2, WindowsServer 2012, Windows Server 2008 R2 SP1
- **WMF-ondersteuning:** WMF 5.0 RTM, WMF 4.0 Update, WMF 4.0
- **Omgeving:** Azure
- **Opmerking:** Deze versie wordt DSC opgenomen in Windows Server 2016 Technical Preview; voor andere Windows-besturingssystemen, installeert het de [Windows Management Framework 5.0 RTM](https://blogs.msdn.microsoft.com/powershell/2015/12/16/windows-management-framework-wmf-5-0-rtm-is-now-available/) (installeren van WMF opnieuw opstarten vereist).
- **Nieuwe functies**
  - Moet telemetrie niet-blokkerende wanneer er een fout optreedt tijdens het downloaden van de hotfix telemetrie (bekend probleem met het Azure DNS) of tijdens de installatie.
  - Oplossing voor het tijdelijk probleem waarbij extensie verwerking configuratie na het opnieuw opstarten niet. Dit is veroorzaakt door de DSC-extensie om te blijven bij het overstappen staat.
  - Secundaire van andere oplossingen en verbeteringen zijn toegevoegd.

### <a name="version-217"></a>Versie 2.17

- **Uitgebracht op:** 26 april 2016
- **Ondersteuning voor het besturingssysteem:** Windows Server 2016 Technical Preview, Windows Server 2012 R2, WindowsServer 2012, Windows Server 2008 R2 SP1
- **WMF-ondersteuning:** WMF 5.0 RTM, WMF 4.0 Update, WMF 4.0
- **Omgeving:** Azure
- **Opmerking:** Deze versie wordt DSC opgenomen in Windows Server 2016 Technical Preview; voor andere Windows-besturingssystemen, installeert het de [Windows Management Framework 5.0 RTM](https://blogs.msdn.microsoft.com/powershell/2015/12/16/windows-management-framework-wmf-5-0-rtm-is-now-available/) (installeren van WMF opnieuw opstarten vereist).
- **Nieuwe functies**
  - Ondersteuning voor WMF 4.0-Update. Zie voor meer informatie over WMF 4.0-Update [deze blog](https://blogs.msdn.microsoft.com/powershell/2016/01/19/windows-management-framework-wmf-4-0-update-now-available-for-windows-server-2012-windows-server-2008-r2-sp1-and-windows-7-sp1/).
  - Logica voor opnieuw proberen op fouten die optreden tijdens de installatie van de DSC-extensie of tijdens het toepassen van een DSC-configuratie plaatsen extensie installeren. De extensie wordt als onderdeel van deze wijziging wordt de installatie opnieuw uitvoeren als een eerdere installatie is mislukt of opnieuw een DSC-configuratie die eerder is mislukt, maximaal drie keer totdat de voltooiingsstatus (geslaagd/fout) is bereikt of als een nieuwe aanvraag afkomstig is gerapporteerd. Als de extensie is mislukt vanwege een ongeldige gebruiker instellingen/gebruikersinvoer, probeert het niet opnieuw. In dit geval moet de extensie opnieuw worden aangeroepen met een nieuwe aanvraag en gebruikersinstellingen te corrigeren. Opmerking: De DSC-extensie is afhankelijk van de Azure VM-agent voor de nieuwe pogingen. Azure VM-agent roept de uitbreiding met de laatste mislukte aanvraag totdat een status voltooid of fout wordt bereikt.

### <a name="version-216"></a>Versie 2,16

- **Uitgebracht op:** 21 april 2016
- **Ondersteuning voor het besturingssysteem:** Windows Server 2016 Technical Preview, Windows Server 2012 R2, WindowsServer 2012, Windows Server 2008 R2 SP1
- **WMF-ondersteuning:** WMF 5.0 RTM, WMF 4.0
- **Omgeving:** Azure
- **Opmerking:** Deze versie wordt DSC opgenomen in Windows Server 2016 Technical Preview; voor andere Windows-besturingssystemen, installeert het de [Windows Management Framework 5.0 RTM](https://blogs.msdn.microsoft.com/powershell/2015/12/16/windows-management-framework-wmf-5-0-rtm-is-now-available/) (installeren van WMF opnieuw opstarten vereist).
- **Nieuwe functies**
  - Verbetering van de foutafhandeling en overige kleine correcties.
  - Nieuwe eigenschap in de instellingen van de DSC-extensie. 'ForcePullAndApply' in AdvancedOptions wordt toegevoegd aan de DSC-extensie inschakelen DSC-configuraties gerapporteerd als de vernieuwingsmodus voor het Pull (in plaats van de standaard-Push-modus is). Raadpleeg voor meer informatie, [deze blog](https://blogs.msdn.microsoft.com/powershell/2016/02/26/arm-dsc-extension-settings/) voor meer informatie over de DSC-extensie-instellingen.

### <a name="version-215"></a>Versie 2.15

- **Uitgebracht op:** 14 maart 2016
- **Ondersteuning voor het besturingssysteem:** Windows Server 2016 Technical Preview, Windows Server 2012 R2, WindowsServer 2012, Windows Server 2008 R2 SP1
- **WMF-ondersteuning:** WMF 5.0 RTM, WMF 4.0
- **Omgeving:** Azure
- **Opmerking:** Deze versie wordt DSC opgenomen in Windows Server 2016 Technical Preview; voor andere Windows-besturingssystemen, installeert het de [Windows Management Framework 5.0 RTM](https://blogs.msdn.microsoft.com/powershell/2015/12/16/windows-management-framework-wmf-5-0-rtm-is-now-available/) (installeren van WMF opnieuw opstarten vereist).
- **Nieuwe functies**
  - In de versie van de extensie 2.14 zijn gewijzigd voor het installeren van WMF RTM opgenomen. Tijdens de upgrade van versie van de extensie 2.13.2.0-2.14.0.0, merkt u dat sommige cmdlets DSC mislukken of uw configuratie is mislukt met fout: 'Geen exemplaar met de opgegeven eigenschapswaarden gevonden'. Zie voor meer informatie de [opmerkingen bij de release van DSC](https://msdn.microsoft.com/en-us/powershell/wmf/limitation_dsc). De tijdelijke oplossingen voor deze problemen zijn toegevoegd in 2.15 versie.
  - Helaas, als u versie 2.14 hebt geïnstalleerd en worden uitgevoerd in een van de bovenstaande twee problemen, u moet deze stappen handmatig uitvoeren.  In een PowerShell-sessie met verhoogde bevoegdheden:
    - `Remove-Item -Path $env:SystemRoot\system32\Configuration\DSCEngineCache.mof`
    - `mofcomp $env:windir\system32\wbem\DscCoreConfProv.mof`

### <a name="version-214"></a>Versie 2.14

- **Uitgebracht op:** 25 februari 2016
- **Ondersteuning voor het besturingssysteem:** Windows Server 2016 Technical Preview, Windows Server 2012 R2, WindowsServer 2012, Windows Server 2008 R2 SP1
- **WMF-ondersteuning:** WMF 5.0 RTM, WMF 4.0
- **Omgeving:** Azure
- **Opmerking:** Deze versie wordt DSC opgenomen in Windows Server 2016 Technical Preview; voor andere Windows-besturingssystemen, installeert het de [Windows Management Framework 5.0 RTM](https://blogs.msdn.microsoft.com/powershell/2015/12/16/windows-management-framework-wmf-5-0-rtm-is-now-available/) (installeren van WMF opnieuw opstarten vereist).
- **Nieuwe functies**
  - Maakt gebruik van WMF RTM.
  - Schakelt de gegevensverzameling om te verbeteren van de kwaliteit van de DSC-extensie. Zie voor meer informatie, [de blog](https://blogs.msdn.microsoft.com/powershell/2016/02/02/azure-dsc-extension-data-collection-2/).
  - Biedt een indeling van de bijgewerkte instellingen voor de extensie in Resource Manager-sjabloon. Zie voor meer informatie, [de blog](https://blogs.msdn.microsoft.com/powershell/2016/02/26/arm-dsc-extension-settings/).
  - Oplossingen voor problemen en andere verbeteringen.

## <a name="next-steps"></a>Volgende stappen

- Voor meer informatie over PowerShell DSC, gaat u naar de [PowerShell-documentatiecentrum](../overview/overview.md).
- Bekijk de [Resource Manager-sjabloon voor de DSC-extensie](/azure/virtual-machines/extensions/dsc-template).
- Ga voor meer functionaliteit die u beheren kunt met behulp van PowerShell DSC, evenals meer DSC-resources, het [PowerShell gallery](https://www.powershellgallery.com/packages?q=DscResource&x=0&y=0).
- Zie voor meer informatie over gevoelige parameters doorgeven in configuraties [beheren van referenties veilig met de DSC-extensie-handler](/azure/virtual-machines/extensions/dsc-credentials).