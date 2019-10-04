---
ms.date: 06/12/2017
keywords: DSC, Power shell, configuratie, installatie
title: DSC gebruiken op Nano Server
ms.openlocfilehash: fb826455c21833ae4c8dc2ecd731ffce6bf7eaba
ms.sourcegitcommit: 18985d07ef024378c8590dc7a983099ff9225672
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/04/2019
ms.locfileid: "71941878"
---
# <a name="using-dsc-on-nano-server"></a>DSC gebruiken op Nano Server

> Van toepassing op: Windows Power shell 5,0

**DSC op nano server** is een optioneel pakket in de map `NanoServer\Packages` van de Windows Server 2016-media. Het pakket kan worden geïnstalleerd wanneer u een VHD maakt voor een nano server door het opgeven van **micro soft-nano server-DSC-package** als de waarde van de para meter **packages** van de functie **New-nano Server image** . Als u bijvoorbeeld een VHD voor een virtuele machine maakt, ziet de opdracht er als volgt uit:

```powershell
New-NanoServerImage -Edition Standard -DeploymentType Guest -MediaPath f:\ -BasePath .\Base -TargetPath .\Nano1\Nano.vhd -ComputerName Nano1 -Packages Microsoft-NanoServer-DSC-Package
```

Zie aan de slag [met nano server](/windows-server/get-started/getting-started-with-nano-server)voor meer informatie over het installeren en gebruiken van nano server, en het beheren van nano server met externe communicatie met Power shell.

## <a name="dsc-features-available-on-nano-server"></a>DSC-functies die beschikbaar zijn op nano server

Omdat nano server alleen ondersteuning biedt voor een beperkt aantal Api's in vergelijking met een volledige versie van Windows Server, heeft DSC op nano server niet de volledige functionele pariteit met DSC die op volledige Sku's wordt uitgevoerd voor de tijd. DSC op nano server is actief en is nog niet voltooid.

De volgende DSC-functies zijn momenteel beschikbaar op nano server:

Zowel push-als pull-modi

- Alle DSC-cmdlets die voor komen in een volledige versie van Windows Server, met inbegrip van het volgende:
- [Get-DscLocalConfigurationManager](/powershell/module/PSDesiredStateConfiguration/Get-DscLocalConfigurationManager)
- [Set-DscLocalConfigurationManager](/powershell/module/PSDesiredStateConfiguration/Set-DscLocalConfigurationManager)
- [Enable-DscDebug](/powershell/module/PSDesiredStateConfiguration/Enable-DscDebug)
- [Disable-DscDebug](/powershell/module/PSDesiredStateConfiguration/Disable-DscDebug)
- [Start-DscConfiguration](/powershell/module/psdesiredstateconfiguration/start-dscconfiguration)
- [Stop-DscConfiguration](/powershell/module/PSDesiredStateConfiguration/Stop-DscConfiguration)
- [Get-DscConfiguration](/powershell/module/PSDesiredStateConfiguration/Get-DscConfiguration)
- [Test-DscConfiguration](/powershell/module/psdesiredstateconfiguration/Test-DSCConfiguration)
- [Publish-DscConfiguration](/powershell/module/PSDesiredStateConfiguration/Publish-DscConfiguration)
- [Update-DscConfiguration](/powershell/module/PSDesiredStateConfiguration/Update-DscConfiguration)
- [Restore-DscConfiguration](/powershell/module/PSDesiredStateConfiguration/Restore-DscConfiguration)
- [Remove-DscConfigurationDocument](/powershell/module/PSDesiredStateConfiguration/Remove-DscConfigurationDocument)
- [Get-DscConfigurationStatus](/powershell/module/PSDesiredStateConfiguration/Get-DscConfigurationStatus)
- [Invoke-Dscresource bieden](/powershell/module/PSDesiredStateConfiguration/Invoke-DscResource)
- [Zoeken-Dscresource bieden](/powershell/module/powershellget/find-dscresource?view=powershell-6)
- [Get-Dscresource bieden](/powershell/module/PSDesiredStateConfiguration/Get-DscResource)
- [New-DscChecksum](/powershell/module/PSDesiredStateConfiguration/New-DSCCheckSum)

- Configuraties compileren (Zie [DSC-configuraties](../configurations/configurations.md))

  **Name** Wachtwoord versleuteling (Zie [het MOF-bestand beveiligen](../pull-server/secureMOF.md)) tijdens de compilatie van de configuratie werkt niet.

- Bezig met het compileren van de-configuratie (Zie [de lokale Configuration Manager configureren](../managing-nodes/metaConfig.md))

- Een resource uitvoeren onder gebruikers context (Zie [DSC uitvoeren met gebruikers referenties (runas)](../configurations/runAsUser.md))

- Op klassen gebaseerde resources (Zie [een aangepaste DSC-resource schrijven met Power shell-klassen](/previous-versions//dn948461(v=technet.10)))

- Fout opsporing voor DSC-resources (Zie [fout opsporing voor DSC-resources](../troubleshooting/debugResource.md))

  **Name** Werkt niet als een resource gebruikmaakt van PsDscRunAsCredential (Zie [DSC uitvoeren met gebruikers referenties](../configurations/runAsUser.md))

- [Afhankelijkheden van meerdere knooppunten opgeven](../configurations/crossNodeDependencies.md)

- [Resource versie beheer](../configurations/sxsResource.md)

- Pull-client (configuraties & bronnen) (Zie [een pull-client instellen met behulp van configuratie namen](../pull-server/pullClientConfigNames.md))

- [Gedeeltelijke configuraties (pull & push)](../pull-server/partialConfigs.md)

- [Rapportage aan pull-server](../pull-server/reportServer.md)

- MOF-versleuteling

- Gebeurtenis registratie

- Azure Automation DSC-rapportage

- Volledig functionele bronnen

- **Archief**
- **Variabelen**
- **File**
- **Log**
- **ProcessSet**
- **Registersubsleutel**
- **Schriften**
- **WindowsPackageCab**
- **WindowsProcess**
- **WaitForAll** (Zie [afhankelijkheden van meerdere knoop punten opgeven](../configurations/crossNodeDependencies.md))
- **WaitForAny** (Zie [afhankelijkheden van meerdere knoop punten opgeven](../configurations/crossNodeDependencies.md))
- **WaitForSome** (Zie [afhankelijkheden van meerdere knoop punten opgeven](../configurations/crossNodeDependencies.md))

- Resources die gedeeltelijk functioneel zijn
- **Groep**
- **GroupSet**

  **Name** De bovenstaande bronnen mislukken als een specifiek exemplaar twee maal wordt aangeroepen (twee keer dezelfde configuratie uitvoeren)

- **Service**
- **ServiceSet**

  **Name** Werkt alleen voor starten/stoppen (status)-service. Mislukt als er wordt geprobeerd andere service kenmerken te wijzigen, zoals opstart type, referenties, Description, enzovoort. De fout die wordt gegenereerd, is vergelijkbaar met:

  *Kan type [management. managementobject] niet vinden: Controleer of de assembly met dit type is geladen.*

- Resources die niet functioneel zijn
- **Gebruiker**

## <a name="dsc-features-not-available-on-nano-server"></a>DSC-functies zijn niet beschikbaar op nano server

De volgende DSC-functies zijn momenteel niet beschikbaar op nano server:

- MOF-document met versleuteld wacht woord (en) ontsleutelen
- Pull-server: u kunt momenteel geen pull-server op nano server instellen
- Alles wat niet voor komt in de lijst met functies werkt

## <a name="using-custom-dsc-resources-on-nano-server"></a>Aangepaste DSC-resources gebruiken op nano server

Vanwege een beperkt aantal Windows-Api's en CLR-bibliotheken die beschikbaar zijn op nano server, werken DSC-resources die werken met de volledige CLR-versie van Windows, niet noodzakelijkerwijs op nano server.
Voltooi end-to-end tests voordat u eventuele DSC-aangepaste resources implementeert in een productie omgeving.

## <a name="see-also"></a>Zie ook

- [Aan de slag met nano server](/windows-server/get-started/getting-started-with-nano-server)
