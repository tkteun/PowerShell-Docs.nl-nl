---
ms.date: 11/09/2020
keywords: DSC, Power shell, configuratie, installatie
title: Een virtuele machine configureren bij de eerste keer opstarten met behulp van DSC
description: In dit artikel wordt uitgelegd hoe u een virtuele machine bij de eerste keer opstarten configureert met behulp van DSC
ms.openlocfilehash: 09449053ff085209dec6ccbfa800e5d112d1c769
ms.sourcegitcommit: 2c311274ce721cd1072dcf2dc077226789e21868
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 11/10/2020
ms.locfileid: "94389994"
---
# <a name="configure-a-virtual-machines-at-initial-boot-up-by-using-dsc"></a>Een virtuele machine configureren bij de eerste keer opstarten met behulp van DSC

> [!IMPORTANT]
> Van toepassing op: Windows Power shell 5,0

## <a name="requirements"></a>Vereisten

> [!NOTE]
> De register sleutel **DSCAutomationHostEnabled** die in dit onderwerp wordt beschreven, is niet beschikbaar in power Shell 4,0. Voor informatie over het configureren van nieuwe virtuele machines bij de eerste keer opstarten in Power Shell 4,0, raadpleegt [u uw machines automatisch configureren met DSC bij de eerste keer opstarten?](https://devblogs.microsoft.com/powershell/want-to-automatically-configure-your-machines-using-dsc-at-initial-boot-up/)

Als u deze voor beelden wilt uitvoeren, hebt u het volgende nodig:

- Een opstart bare VHD om mee te werken. U kunt een ISO downloaden met een evaluatie versie van Windows Server 2016 op [Evaluation Center](https://www.microsoft.com/evalcenter/evaluate-windows-server-2016).
  U vindt instructies over het maken van een VHD op basis van een ISO-installatie kopie bij [het maken van opstart bare virtuele harde schijven](/previous-versions/windows/it-pro/windows-7/gg318049(v=ws.10)).
- Een hostcomputer waarop Hyper-V is ingeschakeld. Zie [Hyper-V Overview](/previous-versions/windows/it-pro/windows-server-2012-R2-and-2012/hh831531(v=ws.11))(Engelstalig) voor meer informatie.

  Met behulp van DSC kunt u software-installatie en-configuratie automatiseren voor een computer bij de eerste keer dat deze wordt opgestart. U doet dit door een configuratie-MOF-document of een-configuratie in te voegen in opstart bare media (zoals een VHD), zodat ze tijdens het eerste opstart proces worden uitgevoerd. Dit gedrag wordt opgegeven door de register sleutel [DSCAutomationHostEnabled register sleutel](DSCAutomationHostEnabled.md) onder `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion\Policies\System` .
  De waarde van deze sleutel is standaard 2, zodat DSC tijdens het opstarten kan worden uitgevoerd.

  Als u niet wilt dat DSC tijdens de opstart tijd wordt uitgevoerd, stelt u de waarde van de register sleutel [DSCAutomationHostEnabled register sleutel](DSCAutomationHostEnabled.md) in op 0.

- Een configuratie-MOF-document in een VHD injecteren
- Een DSC-mailconfiguratie in een VHD injecteren
- DSC op het moment van opstarten uitschakelen

> [!NOTE]
> U kunt zowel `Pending.mof` als `MetaConfig.mof` op een computer tegelijk injecteren.
> Als beide bestanden aanwezig zijn, hebben de instellingen die zijn opgegeven in `MetaConfig.mof` prioriteit.

## <a name="inject-a-configuration-mof-document-into-a-vhd"></a>Een configuratie-MOF-document in een VHD injecteren

Als u een configuratie bij de eerste keer opstarten wilt instellen, kunt u een gecompileerd configuratie-MOF-document als bestand in de VHD injecteren `Pending.mof` . Als de register sleutel **DSCAutomationHostEnabled** is ingesteld op 2 (de standaard waarde), past DSC de configuratie toe die is gedefinieerd door `Pending.mof` wanneer de computer voor de eerste keer wordt opgestart.

In dit voor beeld gebruiken we de volgende configuratie, waarmee IIS wordt ge??nstalleerd op de nieuwe computer:

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

### <a name="to-inject-the-configuration-mof-document-on-the-vhd"></a>Het MOF-document voor de configuratie op de VHD injecteren

1. Koppel de VHD waarin u de configuratie wilt injecteren door de cmdlet [Mount-VHD](/powershell/module/hyper-v/mount-vhd) aan te roepen. Bijvoorbeeld:

   ```powershell
   Mount-VHD -Path C:\users\public\documents\vhd\Srv16.vhd
   ```

1. Op een computer waarop Power shell 5,0 of hoger wordt uitgevoerd, slaat u de bovenstaande configuratie ( **SampleIISInstall** ) op als een Power shell-script bestand (. ps1).

1. Navigeer in een Power shell-console naar de map waar u het. ps1-bestand hebt opgeslagen.

1. Voer de volgende Power shell-opdrachten uit om het MOF-document te compileren (Zie DSC- [configuraties](../configurations/configurations.md)voor informatie over het compileren van DSC-configuraties:

   ```powershell
   . .\SampleIISInstall.ps1
   SampleIISInstall
   ```

1. Hiermee maakt u een `localhost.mof` bestand in een nieuwe map met de naam `SampleIISInstall` . Wijzig de naam en verplaats dat bestand naar de juiste locatie op de VHD als met `Pending.mof` behulp van de cmdlet [Move-item](/powershell/module/microsoft.powershell.management/move-item) . Bijvoorbeeld:

   ```powershell
   Move-Item -Path C:\DSCTest\SampleIISInstall\localhost.mof -Destination E:\Windows\System32\Configuration\Pending.mof
   ```

1. Ontkoppel de VHD door de cmdlet [dismount-VHD](/powershell/module/hyper-v/dismount-vhd) aan te roepen.
   Bijvoorbeeld:

   ```powershell
   Dismount-VHD -Path C:\users\public\documents\vhd\Srv16.vhd
   ```

1. Maak een virtuele machine met behulp van de VHD waar u het DSC MOF-document hebt ge??nstalleerd.

Na de eerste opstart-en installatie van het besturings systeem wordt IIS ge??nstalleerd. U kunt dit controleren door de cmdlet [Get-WindowsFeature aan](/powershell/module/servermanager/get-windowsfeature) te roepen.

## <a name="inject-a-dsc-metaconfiguration-into-a-vhd"></a>Een DSC-mailconfiguratie in een VHD injecteren

U kunt ook een computer configureren voor het ophalen van een configuratie bij de eerste keer opstarten door een meta configuratie in te voeren (Zie [de lokale Configuration Manager (LCM) configureren](../managing-nodes/metaConfig.md)in de VHD als `MetaConfig.mof` bestand. Als de register sleutel **DSCAutomationHostEnabled** is ingesteld op 2 (de standaard waarde), wordt de door DSC gedefinieerde configuratie toegepast op `MetaConfig.mof` de LCM wanneer de computer voor de eerste keer wordt opgestart. Als de-configuratie opgeeft dat de LCM configuraties moet ophalen van een pull-server, probeert de computer tijdens het opstarten een configuratie te halen van die pull-server. Zie [een DSC Web-pull-server instellen](../pull-server/pullServer.md)voor meer informatie over het instellen van een DSC-pull-server.

Voor dit voor beeld gebruiken we zowel de configuratie die wordt beschreven in de vorige sectie ( **SampleIISInstall** ) als de volgende-configuratie:

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

### <a name="to-inject-the-metaconfiguration-mof-document-on-the-vhd"></a>Het MOF-document van de configuratie voor de virtuele harde schijf injecteren

1. Koppel de VHD waarin u de-configuratie wilt injecteren door de cmdlet [Mount-VHD](/powershell/module/hyper-v/mount-vhd) aan te roepen. Bijvoorbeeld:

   ```powershell
   Mount-VHD -Path C:\users\public\documents\vhd\Srv16.vhd
   ```

1. [Stel een DSC Web-pull-server](../pull-server/pullServer.md)in en sla de **SampleIISInstall** -configuratie op in de juiste map.

1. Op een computer waarop Power shell 5,0 of hoger wordt uitgevoerd, slaat u de bovenstaande meta configuratie ( **PullClientBootstrap** ) op als een Power shell-script bestand (. ps1).

1. Navigeer in een Power shell-console naar de map waar u het. ps1-bestand hebt opgeslagen.

1. Voer de volgende Power shell-opdrachten uit voor het compileren van het MOF-document met de eigen configuratie (Zie [DSC-configuraties](../configurations/configurations.md)voor meer informatie over het compileren van DSC-configuraties:

   ```powershell
   . .\PullClientBootstrap.ps1
   PullClientBootstrap
   ```

1. Hiermee maakt u een `localhost.meta.mof` bestand in een nieuwe map met de naam `PullClientBootstrap` . Wijzig de naam en verplaats dat bestand naar de juiste locatie op de VHD als met `MetaConfig.mof` behulp van de cmdlet [Move-item](/powershell/module/microsoft.powershell.management/move-item) .

   ```powershell
   Move-Item -Path C:\DSCTest\PullClientBootstrap\localhost.meta.mof -Destination E:\Windows\System32\Configuration\MetaConfig.mof
   ```

1. Ontkoppel de VHD door de cmdlet [dismount-VHD](/powershell/module/hyper-v/dismount-vhd) aan te roepen.
   Bijvoorbeeld:

   ```powershell
   Dismount-VHD -Path C:\users\public\documents\vhd\Srv16.vhd
   ```

1. Maak een virtuele machine met behulp van de VHD waar u het DSC MOF-document hebt ge??nstalleerd.

Na de eerste opstart-en installatie van het besturings systeem haalt DSC de configuratie van de pull-server en wordt IIS ge??nstalleerd. U kunt dit controleren door de cmdlet [Get-WindowsFeature aan](/powershell/module/servermanager/get-windowsfeature) te roepen.

## <a name="disable-dsc-at-boot-time"></a>DSC op het moment van opstarten uitschakelen

Standaard is dit de waarde van de `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion\Policies\System\DSCAutomationHostEnabled`
de sleutel is ingesteld op 2, waardoor een DSC-configuratie kan worden uitgevoerd als de computer de status in behandeling of actief heeft. Als u niet wilt dat een configuratie wordt uitgevoerd bij de eerste keer opstarten, moet u de waarde van deze sleutel instellen op 0:

1. Koppel de VHD door de cmdlet [Mount-VHD](/powershell/module/hyper-v/mount-vhd) aan te roepen. Bijvoorbeeld:

   ```powershell
   Mount-VHD -Path C:\users\public\documents\vhd\Srv16.vhd
   ```

1. Laad de `HKLM\Software` registersubsleutel van de VHD door aan te roepen `reg load` .

   ```powershell
   reg load HKLM\Vhd E:\Windows\System32\Config\Software
   ```

1. Wijzig de waarde van in `DSCAutomationHostEnabled` 0 in de geladen component.

   ```powershell
   reg add "HKLM\Vhd\Software\Microsoft\Windows\CurrentVersion\Policies\System" /v DSCAutomationHostEnabled /t REG_DWORD /d 0 /f
   ```

1. Verwijder het REGI ster door de volgende opdrachten uit te voeren:

   ```powershell
   reg unload HKLM\Vhd
   ```

## <a name="see-also"></a>Zie ook

[DSC-configuraties](../configurations/configurations.md)

[De registersleutel DSCAutomationHostEnabled](DSCAutomationHostEnabled.md)

[De Local Configuration Manager (LCM) configureren](../managing-nodes/metaConfig.md)

[Een DSC Web-pull-server instellen](../pull-server/pullServer.md)
