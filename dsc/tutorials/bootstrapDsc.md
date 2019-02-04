---
ms.date: 06/12/2017
keywords: DSC, powershell, configuratie en installatie
title: Een virtuele machine configureren bij de eerste keer opstarten met behulp van DSC
ms.openlocfilehash: 2ae6f7a85af3d08bad9e97b90efaefb2ff8410ca
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 02/03/2019
ms.locfileid: "55686906"
---
# <a name="configure-a-virtual-machines-at-initial-boot-up-by-using-dsc"></a>Een virtuele machine configureren bij de eerste keer opstarten met behulp van DSC

> [!IMPORTANT]
> Van toepassing op: Windows PowerShell 5.0

## <a name="requirements"></a>Vereisten

> [!NOTE]
> De **DSCAutomationHostEnabled** registersleutel die worden beschreven in dit onderwerp is niet beschikbaar in PowerShell 4.0.
> Zie voor meer informatie over het configureren van nieuwe virtuele machines bij de eerste keer opstarten in PowerShell 4.0 [wilt automatisch configureren van uw Machines met behulp van DSC bij de eerste keer opstarten?](https://blogs.msdn.microsoft.com/powershell/2014/02/28/want-to-automatically-configure-your-machines-using-dsc-at-initial-boot-up/)

Om uit te voeren van deze voorbeelden, hebt u het volgende nodig:

- Een opstartbare virtuele harde schijf om te werken met. U kunt een ISO met een evaluatieversie van Windows Server 2016 op downloaden [TechNet Evaluation Center](https://www.microsoft.com/en-us/evalcenter/evaluate-windows-server-2016).
  U vindt instructies over het maken van een VHD van een ISO-installatiekopie op [opstartbare virtuele Hardeschijven maken](/previous-versions/windows/it-pro/windows-7/gg318049(v=ws.10)).
- Een hostcomputer waarop Hyper-V is ingeschakeld. Zie voor meer informatie, [overzicht van Hyper-V](/previous-versions/windows/it-pro/windows-server-2012-R2-and-2012/hh831531(v=ws.11)).

  U kunt software-installatie en configuratie voor een computer bij de eerste keer opstarten automatiseren met behulp van DSC.
  U doen dit door een van beide injecteren van een MOF-configuratiebestand of een metaconfiguration in opstartbare media (zoals een VHD) zodat ze worden uitgevoerd tijdens de eerste keer opstarten.
  Dit gedrag is opgegeven door de [de registersleutel dscautomationhostenabled](DSCAutomationHostEnabled.md) registersleutel onder `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion\Policies\System`.
  Standaard is de waarde van deze sleutel 2, waarmee DSC om uit te voeren bij het opstarten.

  Als u niet dat DSC om uit te voeren bij het opstarten wilt, stel de waarde van de [de registersleutel dscautomationhostenabled](DSCAutomationHostEnabled.md) registersleutel in op 0.

- Een MOF-configuratiebestand invoeren in een VHD
- Een DSC-metaconfiguration invoeren in een VHD
- DSC bij het opstarten uitschakelen

> [!NOTE]
> U kunt beide invoeren `Pending.mof` en `MetaConfig.mof` bij een computer op hetzelfde moment.
> Als beide bestanden aanwezig zijn, de instellingen zijn opgegeven in `MetaConfig.mof` voorrang.

## <a name="inject-a-configuration-mof-document-into-a-vhd"></a>Een MOF-configuratiebestand invoeren in een VHD

Als u wilt een configuratie bij de eerste keer opstarten gerapporteerd, kunt u een gecompileerde configuratie MOF-document invoeren in de VHD als de `Pending.mof` bestand.
Als de **DSCAutomationHostEnabled** registersleutel is ingesteld op 2 (standaardwaarde), DSC geldt de configuratie die is gedefinieerd door `Pending.mof` wanneer de computer voor de eerste keer wordt opgestart.

Voor dit voorbeeld gebruiken we de volgende configuratie, waarop IIS wordt geïnstalleerd op de nieuwe computer:

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

### <a name="to-inject-the-configuration-mof-document-on-the-vhd"></a>Naar het MOF-configuratiebestand op de VHD invoeren

1. Koppel de VHD waarnaar u invoeren van de configuratie wilt door het aanroepen van de [VHD koppelen](/powershell/module/hyper-v/mount-vhd) cmdlet. Bijvoorbeeld:

   ```powershell
   Mount-VHD -Path C:\users\public\documents\vhd\Srv16.vhd
   ```

2. Op een computer waarop PowerShell 5.0 of hoger, sla de bovenstaande configuratie (**SampleIISInstall**) als een PowerShell-script (.ps1)-bestand.

3. Navigeer naar de map waar u de .ps1-bestand hebt opgeslagen in een PowerShell-console.

4. Voer de volgende PowerShell-opdrachten voor het compileren van het MOF-document (Zie voor meer informatie over DSC-configuraties compileren [DSC-configuraties](../configurations/configurations.md):

   ```powershell
   . .\SampleIISInstall.ps1
   SampleIISInstall
   ```

5. Hiermee maakt u een `localhost.mof` bestand in een nieuwe map met de naam `SampleIISInstall`.
   Wijzig de naam en dat bestand verplaatsen naar de juiste locatie op de VHD als `Pending.mof` met behulp van de [Item verplaatsen](/powershell/module/microsoft.powershell.management/move-item) cmdlet. Bijvoorbeeld:

   ```powershell
       Move-Item -Path C:\DSCTest\SampleIISInstall\localhost.mof -Destination E:\Windows\System32\Configuration\Pending.mof
   ```

6. Ontkoppelen van de VHD door het aanroepen van de [Dismount-VHD](/powershell/module/hyper-v/dismount-vhd) cmdlet. Bijvoorbeeld:

   ```powershell
   Dismount-VHD -Path C:\users\public\documents\vhd\Srv16.vhd
   ```

7. Een virtuele machine maken met behulp van de installatie van de DSC MOF-document VHD.

Na het eerste boot-up en installatie van besturingssysteem, wordt IIS geïnstalleerd.
U kunt dit controleren door het aanroepen van de [Get-WindowsFeature](/powershell/module/servermanager/get-windowsfeature) cmdlet.

## <a name="inject-a-dsc-metaconfiguration-into-a-vhd"></a>Een DSC-metaconfiguration invoeren in een VHD

U kunt ook een computer om op te halen van een configuratie bij de eerste keer opstarten door het injecteren van een metaconfiguration configureren (Zie [de lokale Configuration Manager (LCM) configureren](../managing-nodes/metaConfig.md)) in de VHD als de `MetaConfig.mof` bestand.
Als de **DSCAutomationHostEnabled** registersleutel is ingesteld op 2 (standaardwaarde), DSC geldt de metaconfiguration gedefinieerd door `MetaConfig.mof` naar de LCM wanneer de computer voor de eerste keer wordt opgestart.
Als de metaconfiguration geeft aan dat de LCM-configuraties van een pull-server moet halen, probeert de computer voor het ophalen van een configuratie van die pull-server bij de eerste keer opstarten.
Zie voor meer informatie over het instellen van een DSC-pull-server [instellen van een DSC-pull-endwebserver](../pull-server/pullServer.md).

Voor dit voorbeeld gebruiken we zowel de configuratie wordt beschreven in de vorige sectie (**SampleIISInstall**), en de volgende metaconfiguration:

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

### <a name="to-inject-the-metaconfiguration-mof-document-on-the-vhd"></a>Aan de metaconfiguration MOF-document op de VHD invoeren

1. Koppel de VHD waarnaar u de metaconfiguration invoeren wilt door het aanroepen van de [VHD koppelen](/powershell/module/hyper-v/mount-vhd) cmdlet. Bijvoorbeeld:

   ```powershell
   Mount-VHD -Path C:\users\public\documents\vhd\Srv16.vhd
   ```

2. [Instellen van een DSC-pull-endwebserver](../pull-server/pullServer.md), en sla de **SampleIISInistall** configuratie naar de juiste map.

3. Op een computer waarop PowerShell 5.0 of hoger, sla de bovenstaande metaconfiguration (**PullClientBootstrap**) als een PowerShell-script (.ps1)-bestand.

4. Navigeer naar de map waar u de .ps1-bestand hebt opgeslagen in een PowerShell-console.

5. Voer de volgende PowerShell-opdrachten voor het compileren van het metaconfiguration MOF-document (Zie voor meer informatie over DSC-configuraties compileren [DSC-configuraties](../configurations/configurations.md):

   ```powershell
   . .\PullClientBootstrap.ps1
   PullClientBootstrap
   ```

6. Hiermee maakt u een `localhost.meta.mof` bestand in een nieuwe map met de naam `PullClientBootstrap`.
   Wijzig de naam en dat bestand verplaatsen naar de juiste locatie op de VHD als `MetaConfig.mof` met behulp van de [Item verplaatsen](/powershell/module/microsoft.powershell.management/move-item) cmdlet.

   ```powershell
   Move-Item -Path C:\DSCTest\PullClientBootstrap\localhost.meta.mof -Destination E:\Windows\System32\Configuration\MetaConfig.mof
   ```

7. Ontkoppelen van de VHD door het aanroepen van de [Dismount-VHD](/powershell/module/hyper-v/dismount-vhd) cmdlet. Bijvoorbeeld:

   ```powershell
   Dismount-VHD -Path C:\users\public\documents\vhd\Srv16.vhd
   ```

8. Een virtuele machine maken met behulp van de installatie van de DSC MOF-document VHD.

Na het eerste boot-up en installatie van besturingssysteem, DSC klikt, wordt de configuratie van de pull-server en IIS wordt geïnstalleerd.
U kunt dit controleren door het aanroepen van de [Get-WindowsFeature](/powershell/module/servermanager/get-windowsfeature) cmdlet.

## <a name="disable-dsc-at-boot-time"></a>DSC bij het opstarten uitschakelen

Standaard is de waarde van de `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion\Policies\System\DSCAutomationHostEnabled` sleutel is ingesteld op 2, waarmee een DSC-configuratie voor het uitvoeren als de computer is in behandeling of de huidige status. Als u niet dat een configuratie om uit te voeren bij de eerste keer opstarten wilt, moet u dus de waarde van deze sleutel instellen op 0:

1. De VHD koppelen door het aanroepen van de [VHD koppelen](/powershell/module/hyper-v/mount-vhd) cmdlet. Bijvoorbeeld:

   ```powershell
   Mount-VHD -Path C:\users\public\documents\vhd\Srv16.vhd
   ```

2. Laden van het register `HKLM\Software` subsleutel van de VHD door het aanroepen van `reg load`.

   ```powershell
   reg load HKLM\Vhd E:\Windows\System32\Config\Software`
   ```

3. Navigeer naar de `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion\Policies\System` met behulp van de PowerShell-registerprovider.

   ```powershell
   Set-Location HKLM:\Software\Microsoft\Windows\CurrentVersion\Policies\System`
   ```

4. Wijzig de waarde van `DSCAutomationHostEnabled` op 0.

   ```powershell
   Set-ItemProperty -Path . -Name DSCAutomationHostEnabled -Value 0
   ```

5. Het register verwijderen door het uitvoeren van de volgende opdrachten:

   ```powershell
   [gc]::Collect()
   reg unload HKLM\Vhd
   ```

## <a name="see-also"></a>Zie ook

[DSC-configuraties](../configurations/configurations.md)

[De registersleutel DSCAutomationHostEnabled](DSCAutomationHostEnabled.md)

[De Local Configuration Manager (LCM) configureren](../managing-nodes/metaConfig.md)

[Instellen van een DSC-pull-endwebserver](../pull-server/pullServer.md)
