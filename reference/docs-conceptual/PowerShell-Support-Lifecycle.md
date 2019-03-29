---
title: Levenscyclus voor ondersteuning van PowerShell Core
description: Beleid met betrekking tot ondersteuning voor PowerShell Core
ms.date: 08/06/2018
ms.openlocfilehash: 178e5c43520f9a392ca219b9f785eb18b1ec5436
ms.sourcegitcommit: f268dce5b5e72be669be0c6634b8db11369bbae2
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 03/29/2019
ms.locfileid: "58623855"
---
# <a name="powershell-core-support-lifecycle"></a>Levenscyclus voor ondersteuning van PowerShell Core

PowerShell Core is een afzonderlijke set hulpprogramma's en onderdelen die is verzonden, geïnstalleerd en geconfigureerd afzonderlijk van Windows PowerShell.
PowerShell Core is dus niet opgenomen in de licentieovereenkomsten voor Windows 7/8.1/10 of Windows Server.

PowerShell Core wordt echter ondersteund onder traditionele Microsoft support-overeenkomsten, met inbegrip van [Premier][], [Microsoft Enterprise-overeenkomsten][enterprise-agreement], en [Microsoft Software Assurance][assurance].
U kunt ook betalen voor [ondersteuning][] voor PowerShell Core via een ondersteuningsaanvraag voor uw probleem.

## <a name="community-support"></a>Ondersteuning van de community

We bieden ook [Ondersteuning van de community][] op GitHub, waar u een probleem, een fout of een functie-aanvraag kan indienen.
Bovendien kan u hulp van andere leden van de community vinden op de algemene [Microsoft Community][] of de Microsoft [PowerShell Tech Community][].
We bieden geen garantie er dat de community wordt adres of het probleem tijdig oplossen.
Als er een probleem dat onmiddellijke aandacht vereist, moet u de traditionele betaalde ondersteuningsopties.

## <a name="lifecycle-of-powershell-core"></a>Levenscyclus van PowerShell Core

PowerShell Core is vast te stellen de [moderne Lifecycle-beleid van Microsoft][modern].
De ondersteuningslevenscyclus van deze is bedoeld om klanten up-to-date houden met de meest recente versies.

De versie 6.x-vertakking van PowerShell Core ongeveer om de zes maanden worden bijgewerkt (voorbeelden: 6.0, 6.1, 6.2, enz.)

> [!IMPORTANT]
> U moet binnen zes maanden na elke nieuwe secundaire versie vrij om door te gaan met het ontvangen van ondersteuning voor bijwerken.

Bijvoorbeeld, als PowerShell Core 6.1 wordt gepubliceerd op 1 juli 2018, zou u worden verwacht om bij te werken naar PowerShell Core 6.1 1 januari 2019 voor verdere ondersteuning.

> [!IMPORTANT]
> U moet binnen 30 dagen na elke nieuwe patchversie vrij om door te gaan met het ontvangen van ondersteuning voor bijwerken.

Bijvoorbeeld, als u PowerShell Core 6.1 en 6.1.3 is uitgebracht op 19 februari 2019, zou u worden verwacht bij te werken naar PowerShell Core 6.1.3 door 21 maart 2019, die 30 dagen na de release is voor verdere ondersteuning.
Als er problemen worden gevonden op vereist, worden de oplossingen in de volgende cumulatieve update uitgebracht.

![PowerShell Core vertakking levenscyclus][lifecycle-chart]

De moderne Lifecycle-beleid is ook vereist dat Microsoft biedt klanten 12 maanden kennisgeving voordat beëindigde ondersteuning voor een product (dat wil zeggen, PowerShell Core).

We verwachten uiteindelijk PowerShell Core gaat hanteren de 'op de lange termijn onderhoud"benadering.
In deze benadering onderhoud, zouden we alleen onderhoud en beveiliging updates om te blijven in de ondersteuning op een specifieke vertakking/versie van 6.x vereisen.

## <a name="supported-platforms"></a>Ondersteunde platformen

De volgende tabel om te zien welke platforms de versie van PowerShell Core die u gebruikt is officieel ondersteund.

Pakketten voor sommige platforms ook bijdrage aan onze community heeft geleverd, maar ze zijn niet officieel ondersteund.
Deze pakketten zijn gemarkeerd als `Community` in de tabel.

Platforms die worden weergegeven als `Experimental` zijn niet officieel ondersteund, maar zijn beschikbaar om te experimenteren en feedback.

|                                                   | 6.1         | 6.2         |
|---------------------------------------------------|:-----------:|:-----------:|
| Windows 7, 8.1 en 10                            | Ondersteund   | Ondersteund   |
| Windows Server 2008 R2, 2012 R2, 2016             | Ondersteund   | Ondersteund   |
| [Windows Server semi-Annual-kanaal][semi-annual] | Ondersteund   | Ondersteund   |
| Ubuntu 16.04 en 18.04                            | Ondersteund   | Ondersteund   |
| Ubuntu 18.10 (via Snap-pakket)                   | Community   | Community   |
| Debian 9                                          | Ondersteund   | Ondersteund   |
| CentOS 7                                          | Ondersteund   | Ondersteund   |
| Red Hat Enterprise Linux 7                        | Ondersteund   | Ondersteund   |
| openSUSE 42,3                                     | Ondersteund   | Ondersteund   |
| Fedora 28                                         | Ondersteund   | Ondersteund   |
| macOS 10.12+                                      | Ondersteund   | Ondersteund   |
| Arch                                              | Community   | Community   |
| Raspbian                                          | Community   | Community   |
| Kali                                              | Community   | Community   |
| AppImage (werkt op meerdere platforms voor Linux)     | Community   | Community   |
| [Snap-pakket](https://snapcraft.io/powershell)   | Zie de opmerking    | Zie de opmerking    |

> [!NOTE]
> Module-pakketten ondersteund gelijk zijn aan de distributie wordt uitgevoerd het pakket op.

## <a name="powershell-release-end-of-life"></a>Einde van de PowerShell-versie van de levensduur

Op basis van [levenscyclus van de PowerShell Core](#lifecycle-of-powershell-core), de volgende tabel bevat de datums waarop verschillende versie wordt niet meer ondersteund.

| Versie | Einde van hun levensduur                   |
|---------|-------------------------------|
| 6.0     | Op 13 februari 2019             |
| 6.1     | 28 september 2019            |
| 6.2     | zes maanden na 6.3-versies   |

## <a name="platforms-which-are-out-of-support"></a>Platforms die niet ondersteund worden

Wanneer een versie van het platform einde van de levenscyclus bereikt zoals gedefinieerd door de eigenaar van het platform, worden ook PowerShell Core gestaakt voor de ondersteuning van deze versie van het platform.
Eerder uitgebrachte pakketten blijven beschikbaar voor klanten die toegang tot, maar formele ondersteuning en de updates van welke aard dan ook niet meer worden geleverd.

Dus de eigenaren van de distributie van ondersteuning voor de volgende versies beëindigd en worden niet ondersteund.

| Besturingssysteem       | Versie | Einde van hun levensduur                                                                                 |
|----------|---------|---------------------------------------------------------------------------------------------|
| Fedora   | 24      | [Augustus 2017](https://fedoramagazine.org/fedora-24-eol/)                                    |
| Fedora   | 25      | [December 2017](https://fedoramagazine.org/fedora-25-end-life/)                             |
| Fedora   | 26      | [Mei 2018](https://fedoramagazine.org/fedora-26-end-life/)                                  |
| openSUSE | 42.1    | [Mei 2017](https://lists.opensuse.org/opensuse-security-announce/2017-05/msg00053.html)     |
| openSUSE | 42.2    | [Januari 2018](https://lists.opensuse.org/opensuse-security-announce/2017-11/msg00066.html) |
| Ubuntu   | 16.10   | [Juli 2017](https://lists.ubuntu.com/archives/ubuntu-announce/2017-July/000223.html)        |
| Ubuntu   | 17.04   | [Januari 2018](https://lists.ubuntu.com/archives/ubuntu-announce/2018-January.txt)          |
| Ubuntu   | 17.10   | [Juli 2018](https://lists.ubuntu.com/archives/ubuntu-announce/2018-July/000232.html)        |
| Debian   | 8       | [Juni 2018](https://lists.debian.org/debian-security-announce/2018/msg00132.html)           |
| Fedora   | 27      | [November 2018](https://fedoramagazine.org/fedora-27-end-of-life/)                          |
| Ubuntu   | 14.04   | [April 2019](https://wiki.ubuntu.com/Releases)                                              |

## <a name="notes-on-licensing"></a>Opmerkingen bij de licentieverlening

PowerShell Core is uitgebracht onder de [MIT-licentie][].
Onder deze licentie, en zonder een betaalde ondersteuningsovereenkomst, gebruikers zijn beperkt tot [Ondersteuning van de community][].
Met de ondersteuning van de community kan Microsoft niet garanderen van de reactiesnelheid of oplossingen.

## <a name="windows-powershell-module"></a>Windows PowerShell Module

Ondersteuning voor PowerShell Core bevat geen van product-modules, tenzij deze modules expliciet ondersteuning voor PowerShell Core.
Bijvoorbeeld, met behulp van de `ActiveDirectory` module die wordt geleverd als onderdeel van Windows Server een niet-ondersteund scenario is.

Modules die niet expliciet PowerShell Core ondersteunen kunnen zich echter compatibel zijn in sommige gevallen.
Door het installeren van de [ `WindowsPSModulePath` ][] -module, kunt u de Windows PowerShell toevoegen `PSModulePath` aan uw PowerShell Core `PSModulePath`.

Installeer eerst de `WindowsPSModulePath` module op basis van de PowerShell Gallery:

```powershell
# Add `-Scope CurrentUser` if you're installing as non-admin
Install-Module WindowsPSModulePath -Force
```

Na de installatie van deze module worden uitgevoerd de `Add-WindowsPSModulePath` cmdlet om toe te voegen van de Windows PowerShell `PSModulePath` PowerShell Core:

```powershell
# Add this line to your profile if you always want Windows PowerShell PSModulePath
Add-WindowsPSModulePath
```

## <a name="experimental-features"></a>Experimentele functies

[Experimentele functies][] zijn beperkt tot [communityondersteuning](#community-support).

[Premier]: https://www.microsoft.com/en-us/microsoftservices/support.aspx
[enterprise-agreement]: https://www.microsoft.com/en-us/licensing/licensing-programs/enterprise.aspx
[assurance]: https://www.microsoft.com/en-us/licensing/licensing-programs/software-assurance-default.aspx
[Ondersteuning van de community]: https://github.com/powershell/powershell/issues
[Microsoft Community]: https://answers.microsoft.com/
[PowerShell Tech Community]: https://techcommunity.microsoft.com/t5/PowerShell/ct-p/WindowsPowerShell
[ondersteuning]: https://support.microsoft.com/assistedsupportproducts
[modern]: https://support.microsoft.com/help/30881/modern-lifecycle-policy
[lifecycle-chart]: ./images/modern-lifecycle.png
[semi-annual]: https://docs.microsoft.com/windows-server/get-started/semi-annual-channel-overview
[MIT-licentie]: https://github.com/PowerShell/PowerShell/blob/master/LICENSE.txt
[`WindowsPSModulePath`]: https://www.powershellgallery.com/packages/WindowsPSModulePath/
[Experimentele functies]: /powershell/module/microsoft.powershell.core/about/about_powershell_config?view=powershell-6#experimentalfeatures
