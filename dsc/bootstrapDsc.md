---
ms.date: 06/12/2017
keywords: DSC, powershell, configuratie, setup
title: Een virtuele machines op de eerste boot-up configureren met behulp van DSC
ms.openlocfilehash: d6dd997e607152d09d24b55370bb2f85810b333e
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 05/16/2018
ms.locfileid: "34190261"
---
>Van toepassing op: Windows PowerShell 5.0

>**Opmerking:** de **DSCAutomationHostEnabled** registersleutel beschreven in dit onderwerp is niet beschikbaar in PowerShell 4.0.
Zie voor meer informatie over het configureren van nieuwe virtuele machines op de eerste boot-up in PowerShell 4.0 [automatisch configureren van uw Machines met behulp van DSC op initiële Boot-up wilt?](https://blogs.msdn.microsoft.com/powershell/2014/02/28/want-to-automatically-configure-your-machines-using-dsc-at-initial-boot-up/)

# <a name="configure-a-virtual-machines-at-initial-boot-up-by-using-dsc"></a>Een virtuele machines op de eerste boot-up configureren met behulp van DSC

## <a name="requirements"></a>Vereisten

Voor het uitvoeren van deze voorbeelden, moet u het:

- Een opstartbare VHD werken met. U kunt geen ISO met een evaluatieversie van Windows Server 2016 op downloaden [TechNet Evaluation Center](https://www.microsoft.com/evalcenter/evaluate-windows-server-2016). U vindt instructies over het maken van een VHD van een ISO-installatiekopie op [opstartbare virtuele harde schijven maken](https://technet.microsoft.com/library/gg318049.aspx).
- Een hostcomputer waarop Hyper-V is ingeschakeld. Zie voor informatie [overzicht Hyper-V](https://technet.microsoft.com/library/hh831531.aspx).

U kunt software-installatie en configuratie van een computer op initiële boot-up automatiseren met behulp van DSC.
U doen dit door beide injecteren van een document van de MOF-configuratie of een metaconfiguratie in opstartbare media (zoals een VHD) zodat ze worden uitgevoerd wanneer de eerste keer opstarten-up.
Dit gedrag wordt opgegeven door de [DSCAutomationHostEnabled registersleutel](DSCAutomationHostEnabled.md) registersleutel onder **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion\Policies**.
Standaard is de waarde van deze sleutel 2, waardoor DSC om uit te voeren tijdens het opstarten.

Als u niet dat DSC om uit te voeren tijdens het opstarten wilt, stel de waarde van de [DSCAutomationHostEnabled registersleutel](DSCAutomationHostEnabled.md) registersleutel in op 0.

- Een configuratie MOF document invoeren in een VHD
- DSC-metaconfiguratie toe invoeren in een VHD
- DSC tijdens het opstarten uitschakelen

>**Opmerking:** kunt u beide injecteren `Pending.mof` en `MetaConfig.mof` in een computer op hetzelfde moment.
Als beide bestanden aanwezig zijn, worden de opgegeven instellingen `MetaConfig.mof` voorrang.

## <a name="inject-a-configuration-mof-document-into-a-vhd"></a>Een configuratie MOF document invoeren in een VHD

Om door te nemen in een configuratie op de eerste boot-up, kunt u een MOF-document gecompileerde configuratie invoeren in de VHD als de `Pending.mof` bestand.
Als de **DSCAutomationHostEnabled** registersleutel is ingesteld op 2 (de standaardwaarde), DSC geldt de configuratie die is gedefinieerd door `Pending.mof` wanneer de computer voor het eerst wordt opgestart.

We gebruiken de volgende configuratie waarop IIS wordt geïnstalleerd op de nieuwe computer voor dit voorbeeld:

```powershell
Configuration SampleIISInstall
{
    Import-DscResource -ModuleName 'PSDesiredStateConfiguration'

    node ('localhost')
    {
        WindowsFeature IIS
        {
            Ensure = 'Present'
            Name   = 'Web-Server'
        }
    }
}
```

### <a name="to-inject-the-configuration-mof-document-on-the-vhd"></a>Het MOF-document van de configuratie op de VHD invoeren

1. Koppelen van de VHD waaraan u invoeren van de configuratie wilt door het aanroepen van de [Mount-VHD](https://technet.microsoft.com/library/hh848551.aspx) cmdlet. Bijvoorbeeld:

    ```powershell
    Mount-VHD -Path C:\users\public\documents\vhd\Srv16.vhd
    ```
2. Op een computer waarop PowerShell 5.0 of hoger, sla de bovenstaande configuratie (**SampleIISInstall**) als een PowerShell-script (.ps1)-bestand.

3. Ga naar de map waar u de .ps1-bestand opgeslagen in een PowerShell-console.

4. Voer de volgende PowerShell-opdrachten voor het compileren van het MOF-document (Zie voor meer informatie over het compileren van DSC-configuraties [DSC-configuraties](configurations.md):

    ```powershell
    . .\SampleIISInstall.ps1
    SampleIISInstall
    ```

5. Hiermee maakt u een `localhost.mof` bestand in een nieuwe map met de naam `SampleIISInstall`.
Wijzig de naam en dat het bestand verplaatsen naar de juiste locatie op de VHD als `Pending.mof` met behulp van de [Item verplaatsen](https://technet.microsoft.comlibrary/hh849852.aspx) cmdlet. Bijvoorbeeld:

    ```powershell
        Move-Item -Path C:\DSCTest\SampleIISInstall\localhost.mof -Destination E:\Windows\System32\Configuration\Pending.mof
    ```
6. Ontkoppelen van de VHD door het aanroepen van de [Dismount-VHD](https://technet.microsoft.com/library/hh848562.aspx) cmdlet. Bijvoorbeeld:

    ```powershell
    Dismount-VHD -Path C:\users\public\documents\vhd\Srv16.vhd
    ```

7. Een virtuele machine maken met behulp van de VHD waar u het document DSC MOF hebt geïnstalleerd.
Na de eerste boot-up en besturingssysteeminstallatie wordt IIS geïnstalleerd.
U kunt dit controleren door het aanroepen van de [Get-WindowsFeature](https://technet.microsoft.com/library/jj205469.aspx) cmdlet.

## <a name="inject-a-dsc-metaconfiguration-into-a-vhd"></a>DSC-metaconfiguratie toe invoeren in een VHD

U kunt ook configureren met een computer om op te halen van een configuratie op de eerste boot-up door het injecteren van een metaconfiguratie (Zie [configureren van de lokale Configuration Manager (LCM)](metaConfig.md)) in de VHD als de `MetaConfig.mof` bestand.
Als de **DSCAutomationHostEnabled** registersleutel is ingesteld op 2 (de standaardwaarde), DSC gelden de metaconfiguratie gedefinieerd door `MetaConfig.mof` naar de LCM wanneer de computer voor het eerst wordt opgestart.
Als de metaconfiguratie wordt opgegeven dat de LCM moet pull-configuraties van een pull-server, probeert de computer voor het ophalen van een configuratie van die pull-server op de eerste boot-up.
Zie voor meer informatie over het instellen van een DSC-pull-server [instellen van een DSC-webserver pull](pullServer.md).

In dit voorbeeld gebruiken we beide de in de vorige sectie beschreven configuratie (**SampleIISInstall**), en de volgende metaconfiguratie toe:

```powershell
[DSCLocalConfigurationManager()]
configuration PullClientBootstrap
{
    Node localhost
    {
        Settings
        {
            RefreshMode = 'Pull'
            RefreshFrequencyMins = 30
            RebootNodeIfNeeded = $true
        }
        ConfigurationRepositoryWeb CONTOSO-PullSrv
        {
            ServerURL = 'https://CONTOSO-PullSrv:8080/PSDSCPullServer.svc'
            RegistrationKey = '140a952b-b9d6-406b-b416-e0f759c9c0e4'
            ConfigurationNames = @('SampleIISInstall')
        }
    }
}
```

### <a name="to-inject-the-metaconfiguration-mof-document-on-the-vhd"></a>Het document van de MOF metaconfiguratie toe op de VHD invoeren

1. Koppelen van de VHD waaraan u de metaconfiguratie invoeren wilt door het aanroepen van de [Mount-VHD](https://technet.microsoft.com/library/hh848551.aspx) cmdlet. Bijvoorbeeld:

    ```powershell
    Mount-VHD -Path C:\users\public\documents\vhd\Srv16.vhd
    ```

2. [Instellen van een DSC-webserver pull](pullServer.md), en sla de **SampleIISInistall** configuratie naar de juiste map.

3. Op een computer waarop PowerShell 5.0 of hoger, sla de bovenstaande metaconfiguratie (**PullClientBootstrap**) als een PowerShell-script (.ps1)-bestand.

4. Ga naar de map waar u de .ps1-bestand opgeslagen in een PowerShell-console.

5. Voer de volgende PowerShell-opdrachten voor het compileren van het MOF-metaconfiguratie document (Zie voor meer informatie over het compileren van DSC-configuraties [DSC-configuraties](configurations.md):

    ```powershell
    . .\PullClientBootstrap.ps1
    PullClientBootstrap
    ```

6. Hiermee maakt u een `localhost.meta.mof` bestand in een nieuwe map met de naam `PullClientBootstrap`.
Wijzig de naam en dat het bestand verplaatsen naar de juiste locatie op de VHD als `MetaConfig.mof` met behulp van de [Item verplaatsen](https://technet.microsoft.comlibrary/hh849852.aspx) cmdlet.

    ```powershell
    Move-Item -Path C:\DSCTest\PullClientBootstrap\localhost.meta.mof -Destination E:\Windows\Sytem32\Configuration\MetaConfig.mof
    ```

7. Ontkoppelen van de VHD door het aanroepen van de [Dismount-VHD](https://technet.microsoft.com/library/hh848562.aspx) cmdlet. Bijvoorbeeld:

    ```powershell
    Dismount-VHD -Path C:\users\public\documents\vhd\Srv16.vhd
    ```

8. Een virtuele machine maken met behulp van de VHD waar u het document DSC MOF hebt geïnstalleerd.
Na de eerste boot-up- en installatie van besturingssysteem DSC klikt, wordt de configuratie van de pull-server en IIS wordt geïnstalleerd.
U kunt dit controleren door het aanroepen van de [Get-WindowsFeature](https://technet.microsoft.com/library/jj205469.aspx) cmdlet.

## <a name="disable-dsc-at-boot-time"></a>DSC tijdens het opstarten uitschakelen

Standaard wordt de waarde van de **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion\Policies\DSCAutomationHostEnabled** sleutel is ingesteld op 2, waarmee een DSC-configuratie voor het uitvoeren als de computer in behandeling of huidige is status. Als u niet dat een configuratie op de eerste boot-up wordt uitgevoerd wilt, moet u de waarde van deze sleutel dus ingesteld op 0:

1. De VHD koppelen door het aanroepen van de [Mount-VHD](https://technet.microsoft.com/library/hh848551.aspx) cmdlet. Bijvoorbeeld:

    ```powershell
    Mount-VHD -Path C:\users\public\documents\vhd\Srv16.vhd
    ```

2. Laden van het register **HKLM\Software** subsleutels van de VHD door het aanroepen van `reg load`.

    ```
    reg load HKLM\Vhd E:\Windows\System32\Config\Software`
    ```

3. Navigeer naar de **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion\Policies\***  met behulp van de PowerShell-registerprovider.

    ```powershell
    Set-Location HKLM:\Software\Microsoft\Windows\CurrentVersion\Policies`
    ```

4. Wijzig de waarde van `DSCAutomationHostEnabled` op 0.

    ```powershell
    Set-ItemProperty -Path . -Name DSCAutomationHostEnabled -Value 0
    ```

5. Het register laden door het uitvoeren van de volgende opdrachten:

    ```powershell
    [gc]::Collect()
    reg unload HKLM\Vhd
    ```

## <a name="see-also"></a>Zie ook

- [DSC-configuraties](configurations.md)
- [De registersleutel DSCAutomationHostEnabled](DSCAutomationHostEnabled.md)
- [De Local Configuration Manager (LCM) configureren](metaConfig.md)
- [Een DSC web pull-server instellen](pullServer.md)