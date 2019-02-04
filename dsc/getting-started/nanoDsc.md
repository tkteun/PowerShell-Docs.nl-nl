---
ms.date: 06/12/2017
keywords: DSC, powershell, configuratie en installatie
title: DSC gebruiken op Nano Server
ms.openlocfilehash: fd81fe56d16100f45d9ee2dfd8fdc303c2a6c17a
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 02/03/2019
ms.locfileid: "55686584"
---
# <a name="using-dsc-on-nano-server"></a>DSC gebruiken op Nano Server

> Van toepassing op: Windows PowerShell 5.0

**DSC op Nano Server** is een optioneel pakket in de `NanoServer\Packages` map van de Windows Server 2016-media. Het pakket kan worden geïnstalleerd wanneer u een VHD voor een Nano-Server door op te geven maken **Microsoft-NanoServer-DSC-Package** als de waarde van de **pakketten** parameter van de **New-NanoServerImage**  functie. Als u een VHD voor een virtuele machine maakt, wordt door de opdracht er als volgt uit:

```powershell
New-NanoServerImage -Edition Standard -DeploymentType Guest -MediaPath f:\ -BasePath .\Base -TargetPath .\Nano1\Nano.vhd -ComputerName Nano1 -Packages Microsoft-NanoServer-DSC-Package
```

Zie voor meer informatie over het installeren en gebruiken van Nano Server, evenals over het beheren van Nano Server met externe communicatie van PowerShell [aan de slag met Nano Server](/windows-server/get-started/getting-started-with-nano-server).

## <a name="dsc-features-available-on-nano-server"></a>DSC-functies die beschikbaar zijn op Nano Server

Omdat Nano Server alleen een beperkte set API's in vergelijking met een volledige versie van Windows Server ondersteunt, heeft DSC op Nano Server geen volledig functionele pariteit met DSC op volledige SKU's voor de tijd die wordt uitgevoerd. DSC op Nano Server is in ontwikkeling en is nog niet de functie is voltooid.

De volgende DSC-functies zijn momenteel beschikbaar in Nano Server:

Zowel push als pull-modi

- Alle DSC-cmdlets die aanwezig zijn op een volledige versie van Windows Server, waaronder het volgende:
- [Get-DscLocalConfigurationManager](/powershell/module/PSDesiredStateConfiguration/Get-DscLocalConfigurationManager)
- [Set-DscLocalConfigurationManager](/powershell/module/PSDesiredStateConfiguration/Set-DscLocalConfigurationManager)
- [Enable-DscDebug](/powershell/module/PSDesiredStateConfiguration/Enable-DscDebug)
- [Disable-DscDebug](/powershell/module/PSDesiredStateConfiguration/Disable-DscDebug)
- [Start-DscConfiguration](/powershell/module/psdesiredstateconfiguration/start-dscconfiguration)
- [Stop-DscConfiguration](/powershell/module/PSDesiredStateConfiguration/Stop-DscConfiguration)
- [Get-DscConfiguration](/powershell/module/PSDesiredStateConfiguration/Get-DscConfiguration)
- [Test-DscConfiguration](/powershell/module/psdesiredstateconfiguration/Test-DSCConfiguration)
- [Publish-DscConfiguraiton](/powershell/module/PSDesiredStateConfiguration/Publish-DscConfiguration)
- [Update-DscConfiguration](/powershell/module/PSDesiredStateConfiguration/Update-DscConfiguration)
- [Restore-DscConfiguration](/powershell/module/PSDesiredStateConfiguration/Restore-DscConfiguration)
- [Remove-DscConfigurationDocument](/powershell/module/PSDesiredStateConfiguration/Remove-DscConfigurationDocument)
- [Get-DscConfigurationStatus](/powershell/module/PSDesiredStateConfiguration/Get-DscConfigurationStatus)
- [Invoke-DscResource](/powershell/module/PSDesiredStateConfiguration/Invoke-DscResource)
- [Find-DscResource](https://technet.microsoft.com/en-us/library/mt517874.aspx)
- [Get-DscResource](/powershell/module/PSDesiredStateConfiguration/Get-DscResource)
- [New-DscChecksum](/powershell/module/PSDesiredStateConfiguration/New-DSCCheckSum)

- -Configuraties compileren (Zie [DSC-configuraties](../configurations/configurations.md))

  **Probleem:** Wachtwoordversleuteling (Zie [beveiligen van het MOF-bestand](../pull-server/secureMOF.md)) tijdens het configureren van de compilatie niet werkt.

- Metaconfigurations compileren (Zie [de Local Configuration Manager configureren](../managing-nodes/metaConfig.md))

- Een resource onder gebruikerscontext uitgevoerd (Zie [DSC uitvoeren met gebruikersreferenties (RunAs)](../configurations/runAsUser.md))

- Op basis van een klasse resources (Zie [schrijven van een aangepaste DSC-resource met de PowerShell-klassen](../resources/authoringResourceClass.md))

- Foutopsporing van DSC-resources (Zie [foutopsporing DSC-resources](../troubleshooting/debugResource.md))

  **Probleem:** Werkt niet als een resource met behulp van PsDscRunAsCredential (Zie [DSC uitvoeren met gebruikersreferenties](../configurations/runAsUser.md))

- [Afhankelijkheden van meerdere knooppunten opgeven](../configurations/crossNodeDependencies.md)

- [Resource-versiebeheer](../configurations/sxsResource.md)

- Pull-client (configuraties en resources) (Zie [instellen van een pull-client met behulp van configuratienamen](../pull-server/pullClientConfigNames.md))

- [Gedeeltelijke configuraties (pull & push)](../pull-server/partialConfigs.md)

- [Rapporteren aan de pull-server](../pull-server/reportServer.md)

- MOF-versleuteling

- Gebeurtenisregistratie

- Azure Automation DSC-rapportage

- Resources die volledig functioneel zijn

- **Archiveren**
- **Omgeving**
- **File**
- **Log**
- **ProcessSet**
- **Registry**
- **Script**
- **WindowsPackageCab**
- **WindowsProcess**
- **WaitForAll** (Zie [afhankelijkheden van meerdere knooppunten opgeven](../configurations/crossNodeDependencies.md))
- **WaitForAny** (Zie [afhankelijkheden van meerdere knooppunten opgeven](../configurations/crossNodeDependencies.md))
- **WaitForSome** (Zie [afhankelijkheden van meerdere knooppunten opgeven](../configurations/crossNodeDependencies.md))

- Resources die, gedeeltelijk functionele zijn
- **Groep**
- **GroupSet**

  **Probleem:** Bovenstaande resources mislukken als specifieke exemplaar tweemaal wordt genoemd (met dezelfde configuratie twee keer)

- **Service**
- **ServiceSet**

  **Probleem:** Werkt alleen voor (status) van de service starten/stoppen. Mislukt, als een probeert te wijzigen van de kenmerken van andere service, zoals het opstarttype van, referenties, beschrijving, enzovoort... De opgetreden fout is vergelijkbaar met:

  *Kan type [management.managementobject] niet vinden: Controleer of de assembly met dit type is geladen.*

- Resources die geen functionele
- **User**

## <a name="dsc-features-not-available-on-nano-server"></a>DSC-functies niet beschikbaar in Nano Server

De volgende DSC-functies zijn momenteel niet beschikbaar in Nano Server:

- MOF-document met versleutelde wachtwoorden ontsleutelen
- Pull-Server kan niet op dit moment instellen van een pull-server op Nano Server
- Alles dat zich niet in de lijst met de functie werkt

## <a name="using-custom-dsc-resources-on-nano-server"></a>Aangepaste DSC-resources gebruiken in Nano Server

Vanwege een beperkte sets van Windows-API's en CLR-bibliotheken beschikbaar in Nano Server werken DSC-resources die aan de volledige CLR-versie van Windows werken mogelijk niet op Nano Server.
Volledige end-to-end testen voordat u een aangepaste DSC-resources in een productieomgeving implementeert.

## <a name="see-also"></a>Zie ook

- [Aan de slag met Nano Server](/windows-server/get-started/getting-started-with-nano-server)
