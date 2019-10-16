---
title: Levenscyclus voor ondersteuning van PowerShell Core
description: Beleids regels die ondersteuning bieden voor Power shell core
ms.date: 08/06/2018
ms.openlocfilehash: fbbda0a5f8460e5625625adcc50c631729df53f1
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/15/2019
ms.locfileid: "72351798"
---
# <a name="powershell-core-support-lifecycle"></a>Levenscyclus voor ondersteuning van PowerShell Core

Power shell Core is een afzonderlijke set hulpprogram ma's en onderdelen die los van Windows Power shell worden geleverd, geïnstalleerd en geconfigureerd. Power shell Core is dus niet opgenomen in de licentie overeenkomsten voor Windows 7/8.1/10 of Windows Server.

Power shell core wordt echter ondersteund onder traditionele micro soft-ondersteunings overeenkomsten, waaronder [Premium][], [micro soft Enter prise agreements][enterprise-agreement]en [micro soft Software Assurance][assurance].
U kunt ook betalen voor [ondersteuning][] voor Power shell core door een ondersteunings aanvraag voor uw probleem te archiveren.

## <a name="community-support"></a>Community-ondersteuning

We bieden ook [Community-ondersteuning][] op github waar u een probleem, een fout of een functie aanvraag kunt indienen.
U kunt ook hulp van andere leden van de Community vinden op de algemene [micro soft-Community][] of de [Technische community van Power shell][]van micro soft power shell. We bieden geen garantie dat de Community tijdig het probleem zal verhelpen of oplossen. Als u een probleem ondervindt dat onmiddellijke aandacht vereist, moet u de traditionele, betaalde ondersteunings opties gebruiken.

## <a name="lifecycle-of-powershell-core"></a>Levens cyclus van Power shell core

Power shell core stelt het [micro soft moderne levenscyclus beleid][modern]vast. Deze ondersteunings levenscyclus is bedoeld om klanten up-to-date te houden met de meest recente versies.

De vertakking versie 6. x van Power shell core wordt ongeveer eenmaal per zes maanden bijgewerkt (bijvoorbeeld: 6,0, 6,1, 6,2, etc.)

> [!IMPORTANT]
> U moet binnen zes maanden na de release van elke nieuwe secundaire versie een update voor het ontvangen van ondersteuning door lopen.

Als Power shell Core 6,1 bijvoorbeeld is uitgebracht op 1 juli 2018, wordt u naar verwachting naar Power shell Core 6,1 bijgewerkt op 1 januari 2019 om ondersteuning te onderhouden.

> [!IMPORTANT]
> U moet binnen 30 dagen na elke nieuwe versie van de patch een update uitvoeren om ondersteuning te blijven ontvangen.

Als u bijvoorbeeld Power shell Core 6,1 uitvoert en 6.1.3 is uitgebracht op 19 februari 2019, zou u op 21 maart 2019 naar verwachting moeten bijwerken naar Power shell Core 6.1.3. Dit is 30 dagen na de release voor het onderhouden van de ondersteuning. Als er oplossingen worden gevonden die vereist zijn, worden de oplossingen vrijgegeven in de volgende cumulatieve update.

Voor het beleid voor moderne levens cyclus moet micro soft klanten 12 maanden vertellen voordat de ondersteuning voor een product (dat wil zeggen Power shell core) wordt beëindigd.

Uiteindelijk wordt verwacht dat Power shell Core de aanpak van de lange termijn voor onderhoud aanneemt. In deze onderhouds benadering moeten alleen onderhouds-en beveiligings updates worden ondersteund voor een specifieke vertakking/versie van 6. x.

## <a name="supported-platforms"></a>Ondersteunde platformen

Raadpleeg de volgende tabel om te controleren of uw platform en versie van Power shell core officieel worden ondersteund.

Onze community heeft ook pakketten bijgedragen voor sommige platforms, maar ze worden niet officieel ondersteund. Deze pakketten zijn gemarkeerd als `Community` in de tabel.

Platforms die worden vermeld als `Experimental`, worden niet officieel ondersteund, maar zijn beschikbaar voor experimenten en feedback.

| Platform                                          |      6.2      |    7,0    |
|---------------------------------------------------|:-------------:|:---------:|
| Windows 7, 8,1 en 10                            |   Ondersteund   | Ondersteund |
| Windows Server 2008 R2, 2012 R2, 2016             |   Ondersteund   | Ondersteund |
| [Windows Server Semi-Annual-kanaal][semi-annual] |   Ondersteund   | Ondersteund |
| Ubuntu 16,04 en 18,04                            |   Ondersteund   | Ondersteund |
| Ubuntu 18,10 (via snap package)                   |   Community   | Community |
| Ubuntu 19,04 (via snap package)                   |   Community   | Community |
| Debian 9                                          |   Ondersteund   | Ondersteund |
| Debian 10                                         | Niet ondersteund | Ondersteund |
| CentOS 7                                          |   Ondersteund   | Ondersteund |
| Red Hat Enterprise Linux 7                        |   Ondersteund   | Ondersteund |
| openSUSE 42,3                                     |   Ondersteund   | Ondersteund |
| Fedora 28                                         |   Ondersteund   | Ondersteund |
| Fedora 29, 30                                     | Niet ondersteund | Ondersteund |
| Alpine 3,8                                        |   Zie opmerking    | Zie opmerking  |
| Alpine 3,9 en 3,10                               | Niet ondersteund | Zie opmerking  |
| macOS 10.12+                                      |   Ondersteund   | Ondersteund |
| Arch                                              |   Community   | Community |
| Raspbian                                          |   Community   | Community |
| Kali                                              |   Community   | Community |
| AppImage (werkt op meerdere Linux-platforms)      |   Community   | Community |
| [Snap-pakket](https://snapcraft.io/powershell)   |   Zie opmerking    | Zie opmerking  |

> [!NOTE]
> Snap-pakketten worden hetzelfde ondersteund als de distributie waarmee u het pakket uitvoert.

> [!NOTE]
> CIM, externe communicatie van Power shell en DSC worden niet ondersteund in Alpine.

## <a name="powershell-releases-end-of-life"></a>Levens duur van Power shell-releases

Op basis van de [levens cyclus van de Power shell-kern](#lifecycle-of-powershell-core), worden in de volgende tabel de datums weer gegeven wanneer verschillende releases niet meer worden ondersteund.

| Versie | Einde van de levens duur                   |
|---------|-------------------------------|
| 6.0     | 13 februari 2019             |
| 6.1     | 28 september 2019            |
| 6.2     | 6 maanden na 7 releases     |

## <a name="unsupported-platforms"></a>Niet-ondersteunde platforms

Wanneer een platform versie het einde van de levens duur bereikt zoals gedefinieerd door de platform eigenaar, zal Power shell core ook niet langer ondersteuning bieden voor die platform versie. Eerder vrijgegeven pakketten blijven beschikbaar voor klanten die toegang nodig hebben, maar formele ondersteuning en updates van welke aard dan ook niet meer.

De distributie-eigen aren hebben daarom de volgende versies gestopt en worden niet ondersteund.

| Platform | Versie | Einde van de levens duur                                                                                 |
|----------|---------|---------------------------------------------------------------------------------------------|
| Fedora   | 24      | [2017 augustus](https://fedoramagazine.org/fedora-24-eol/)                                    |
| Fedora   | 25      | [December 2017](https://fedoramagazine.org/fedora-25-end-life/)                             |
| Fedora   | 26      | [Mei 2018](https://fedoramagazine.org/fedora-26-end-life/)                                  |
| openSUSE | 42,1    | [Mei 2017](https://lists.opensuse.org/opensuse-security-announce/2017-05/msg00053.html)     |
| openSUSE | 42,2    | [Januari 2018](https://lists.opensuse.org/opensuse-security-announce/2017-11/msg00066.html) |
| Ubuntu   | 16,10   | [2017 juli](https://lists.ubuntu.com/archives/ubuntu-announce/2017-July/000223.html)        |
| Ubuntu   | 17,04   | [Januari 2018](https://lists.ubuntu.com/archives/ubuntu-announce/2018-January.txt)          |
| Ubuntu   | 17,10   | [2018 juli](https://lists.ubuntu.com/archives/ubuntu-announce/2018-July/000232.html)        |
| Debian   | 8       | [Juni 2018](https://lists.debian.org/debian-security-announce/2018/msg00132.html)           |
| Fedora   | 27      | [November 2018](https://fedoramagazine.org/fedora-27-end-of-life/)                          |
| Ubuntu   | 14,04   | [April 2019](https://wiki.ubuntu.com/Releases)                                              |

## <a name="notes-on-licensing"></a>Opmerkingen over licenties

Power shell core wordt uitgebracht onder de [MIT-licentie][]. Onder deze licentie en zonder een betaalde ondersteunings overeenkomst zijn gebruikers beperkt tot [Community-ondersteuning][]van de community. Met ondersteuning van de Community biedt micro soft geen garanties voor reactie tijd of oplossingen.

## <a name="windows-powershell-module"></a>Windows Power shell-module

Ondersteuning voor Power shell Core bevat geen product modules, tenzij deze modules expliciet Power shell core ondersteunen. Als u bijvoorbeeld de module `ActiveDirectory` gebruikt die wordt geleverd als onderdeel van Windows Server, is dit een niet-ondersteund scenario.

Modules die Power shell Core niet expliciet ondersteunen, kunnen in sommige gevallen ook compatibel zijn. Door de [`WindowsPSModulePath`-][] module te installeren, kunt u de Windows Power shell-`PSModulePath` toevoegen aan uw Power shell Core-`PSModulePath`.

Installeer eerst de module `WindowsPSModulePath` vanuit de PowerShell Gallery:

```powershell
# Add `-Scope CurrentUser` if you're installing as non-admin
Install-Module WindowsPSModulePath -Force
```

Na de installatie van deze module voert u de `Add-WindowsPSModulePath`-cmdlet uit om de Windows Power shell-`PSModulePath` toe te voegen aan Power shell core:

```powershell
# Add this line to your profile if you always want Windows PowerShell PSModulePath
Add-WindowsPSModulePath
```

## <a name="experimental-features"></a>Experimentele functies

[Experimentele functies][] zijn beperkt tot [ondersteuning](#community-support)van de community.

[Premium]: https://www.microsoft.com/en-us/microsoftservices/support.aspx
[enterprise-agreement]: https://www.microsoft.com/en-us/licensing/licensing-programs/enterprise.aspx
[assurance]: https://www.microsoft.com/en-us/licensing/licensing-programs/software-assurance-default.aspx
[Community-ondersteuning]: https://github.com/powershell/powershell/issues
[Micro soft-Community]: https://answers.microsoft.com/
[Technische community van Power shell]: https://techcommunity.microsoft.com/t5/PowerShell/ct-p/WindowsPowerShell
[ondersteuning]: https://support.microsoft.com/assistedsupportproducts
[modern]: https://support.microsoft.com/help/30881/modern-lifecycle-policy
[lifecycle-chart]: ./images/modern-lifecycle.png
[semi-annual]: https://docs.microsoft.com/windows-server/get-started/semi-annual-channel-overview
[MIT-licentie]: https://github.com/PowerShell/PowerShell/blob/master/LICENSE.txt
['WindowsPSModulePath']: https://www.powershellgallery.com/packages/WindowsPSModulePath/
[Experimentele functies]: /powershell/module/microsoft.powershell.core/about/about_powershell_config?view=powershell-6#experimentalfeatures
