---
title: Levenscyclus voor ondersteuning van PowerShell Core
description: Beleid met betrekking tot ondersteuning voor PowerShell Core
ms.date: 08/06/2018
ms.openlocfilehash: 2e0ca1b9c133e6f316a40aff13365d0489059165
ms.sourcegitcommit: 00ff76d7d9414fe585c04740b739b9cf14d711e1
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 12/14/2018
ms.locfileid: "53404620"
---
# <a name="powershell-core-support-lifecycle"></a>Levenscyclus voor ondersteuning van PowerShell Core

PowerShell Core is een afzonderlijke set hulpprogramma's en onderdelen die is verzonden, geïnstalleerd en geconfigureerd afzonderlijk van Windows PowerShell.
PowerShell Core is daarom niet opgenomen in de licentieovereenkomsten voor Windows 7/8.1/10 of Windows Server.

PowerShell Core wordt echter ondersteund onder traditionele Microsoft support-overeenkomsten, met inbegrip van [Premier][], [Microsoft Enterprise-overeenkomsten][enterprise-agreement], en [Microsoft Software Assurance][assurance].
U kunt ook betalen voor [ondersteuning][] voor PowerShell Core via een ondersteuningsaanvraag voor uw probleem.

We bieden ook [communityondersteuning][] op GitHub, waar u een probleem, een fout of een functie-aanvraag kan indienen.
U kunt ook u Help-informatie van andere leden van de community kan vinden op de algemene [Microsoft Community][] of de Microsoft [PowerShell-Tech-Community][].
We bieden geen garantie er dat uw probleem wordt opgelost of tijdig worden opgelost.
Als er een probleem dat onmiddellijke aandacht vereist, moet u de traditionele betaalde ondersteuningsopties.

## <a name="lifecycle-of-powershell-core"></a>Levenscyclus van PowerShell Core

PowerShell Core is vast te stellen de [moderne Lifecycle-beleid van Microsoft][modern].
De ondersteuningslevenscyclus van deze is bedoeld om klanten up-to-date houden met de meest recente versies.

De versie 6.x-vertakking van PowerShell Core ongeveer om de zes maanden worden bijgewerkt (bijvoorbeeld 6.0, 6.1, 6.2, enz.)

> [!IMPORTANT]
> U moet binnen zes maanden na elke nieuwe secundaire versie vrij om door te gaan met het ontvangen van ondersteuning voor bijwerken.

Bijvoorbeeld, als PowerShell Core 6.1 wordt gepubliceerd op 1 juli 2018, zou u worden verwacht om bij te werken naar PowerShell Core 6.1 1 januari 2019 voor verdere ondersteuning.

![PowerShell Core vertakking levenscyclus][lifecycle-chart]

De moderne Lifecycle-beleid is ook vereist dat Microsoft biedt klanten 12 maanden kennisgeving voordat beëindigde ondersteuning voor een product (dat wil zeggen PowerShell Core).

We verwachten uiteindelijk PowerShell Core gaat hanteren de 'op de lange termijn onderhoud' benadering waarbij we alleen onderhoud en beveiliging vereist om te blijven in de ondersteuning op een specifieke vertakking/versie van 6.x bijgewerkt.

## <a name="supported-platforms"></a>Ondersteunde platformen

Raadpleeg de volgende tabel om te zien wat de versie van PowerShell Core die u gebruikt is officieel ondersteund platform.

Pakketten voor sommige platforms ook bijdrage aan onze community heeft geleverd, maar ze zijn niet officieel ondersteund.
Deze pakketten zijn gemarkeerd als `Community` in de tabel.

Platforms die worden weergegeven als `Experimental` zijn niet officieel ondersteund, maar zijn beschikbaar om te experimenteren en feedback.

|                                                   | 6.0         | 6.1         |
|---------------------------------------------------|:-----------:|:-----------:|
| Windows 7, 8.1 en 10                            | Ondersteund   | Ondersteund   |
| Windows Server 2008 R2, 2012 R2, 2016             | Ondersteund   | Ondersteund   |
| [Windows Server semi-Annual-kanaal][semi-annual] | Ondersteund   | Ondersteund   |
| Ubuntu 14.04 en 16.04                           | Ondersteund   | Ondersteund   |
| Ubuntu 18.04                                      |             | Ondersteund   |
| Ubuntu 18.10 (via Snap-pakket)                   |             | Community   |
| Debian 8,7 + en 9                                | Ondersteund   | Ondersteund   |
| CentOS 7                                          | Ondersteund   | Ondersteund   |
| Red Hat Enterprise Linux 7                        | Ondersteund   | Ondersteund   |
| OpenSUSE 42,3                                     | Ondersteund   | Ondersteund   |
| Fedora 27                                         | Ondersteund   | Ondersteund   |
| Fedora 28                                         |             | Ondersteund   |
| macOS 10.12+                                      | Ondersteund   | Ondersteund   |
| Arch                                              | Community   | Community   |
| Raspbian                                          | Experimentele| Community   |
| Kali                                              | Community   | Community   |
| AppImage (werkt op meerdere platforms voor Linux)     | Community   | Community   |
| [Snap-pakket](https://snapcraft.io/powershell)   | Zie de opmerking    | Zie de opmerking    |

> [!NOTE]
> Snap-pakketten worden experimentele gedurende een periode.  Nadat er we zeker van bent dat module komt niet leiden tot nieuwe voor ondersteuningsproblemen, de ondersteuning voor de distributie die u kunt het pakket worden uitgevoerd op volgen.

## <a name="platform-which-are-out-of-support"></a>Platforms die niet worden ondersteund

Wanneer een versie van het platform einde van de levenscyclus zoals gedefinieerd door de eigenaar van het platform is bereikt, wordt ook PowerShell Core factureringscodes bieden ondersteuning voor die versie van het platform. Eerder uitgebrachte pakketten blijven beschikbaar voor klanten die toegang tot, maar formele ondersteuning en de updates van welke aard dan ook niet meer worden geleverd.

Daarom de ondersteuning voor de volgende versies is beëindigd door de eigenaren van de distributie en worden niet ondersteund.

| Besturingssysteem       | Versie | Einde van hun levensduur                                                                                 |
|----------|---------|---------------------------------------------------------------------------------------------|
| Fedora   | 24      | [Augustus 2017](https://fedoramagazine.org/fedora-24-eol/)                                    |
| Fedora   | 25      | [December 2017](https://fedoramagazine.org/fedora-25-end-life/)                             |
| Fedora   | 26      | [Mei 2018](https://fedoramagazine.org/fedora-26-end-life/)                                  |
| OpenSUSE | 42,1    | [Mei 2017](https://lists.opensuse.org/opensuse-security-announce/2017-05/msg00053.html)     |
| OpenSUSE | 42.2    | [Januari 2018](https://lists.opensuse.org/opensuse-security-announce/2017-11/msg00066.html) |
| Ubuntu   | 16,10   | [Juli 2017](https://lists.ubuntu.com/archives/ubuntu-announce/2017-July/000223.html)        |
| Ubuntu   | 17.04   | [Januari 2018](https://lists.ubuntu.com/archives/ubuntu-announce/2018-January.txt)          |
| Ubuntu   | 17.10   | [Juli 2018](https://lists.ubuntu.com/archives/ubuntu-announce/2018-July/000232.html)        |

## <a name="notes-on-licensing"></a>Opmerkingen bij de licentieverlening

PowerShell Core is uitgebracht onder de [MIT-licentie][].
Onder deze licentie, en in de afwezigheid van een betaalde ondersteuningsovereenkomst, gebruikers zijn beperkt tot [communityondersteuning][].
Met de ondersteuning van de community kan Microsoft niet garanderen van de reactiesnelheid of oplossingen.

## <a name="windows-powershell-module"></a>Windows PowerShell-Module

Ondersteuning voor PowerShell Core niet van toepassing op andere modules product, tenzij deze modules expliciet ondersteuning voor PowerShell Core.
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

[Premier]: https://www.microsoft.com/en-us/microsoftservices/support.aspx
[enterprise-agreement]: https://www.microsoft.com/en-us/licensing/licensing-programs/enterprise.aspx
[assurance]: https://www.microsoft.com/en-us/licensing/licensing-programs/software-assurance-default.aspx
[communityondersteuning]: https://github.com/powershell/powershell/issues
[Microsoft Community]: https://answers.microsoft.com/
[PowerShell-Tech-Community]: https://techcommunity.microsoft.com/t5/PowerShell/ct-p/WindowsPowerShell
[ondersteuning]: https://support.microsoft.com/assistedsupportproducts
[modern]: https://support.microsoft.com/help/30881/modern-lifecycle-policy
[lifecycle-chart]: ./images/modern-lifecycle.png
[semi-annual]: https://docs.microsoft.com/windows-server/get-started/semi-annual-channel-overview
[MIT-licentie]: https://github.com/PowerShell/PowerShell/blob/master/LICENSE.txt
['WindowsPSModulePath']: https://www.powershellgallery.com/packages/WindowsPSModulePath/
