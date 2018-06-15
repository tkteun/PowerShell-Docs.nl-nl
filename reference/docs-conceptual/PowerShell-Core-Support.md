# <a name="powershell-core-support-lifecycle"></a>Levenscyclus voor ondersteuning van PowerShell Core

PowerShell Core is een unieke set van hulpprogramma's en onderdelen die is verzonden, geïnstalleerd en geconfigureerd afzonderlijk vanuit Windows PowerShell.
PowerShell Core is daarom niet opgenomen in de licentieovereenkomsten voor Windows 7/8.1/10 of Windows Server.

PowerShell Core wordt echter ondersteund onder traditionele Microsoft support-overeenkomsten, met inbegrip van [Premier][], [Microsoft Enterprise Agreements][enterprise-agreement], en [Microsoft Software Assurance][assurance].
U kunt ook betalen voor [ondersteuning][] voor PowerShell Core door het indienen van een aanvraag voor de ondersteuning voor uw probleem.

We bieden ook [communityondersteuning][] op GitHub waarin u een probleem, een fout of een aanvraag van de functie kan opslaan.
U kunt ook u Help-informatie van andere leden van de community mogelijk vinden op de algemene [Microsoft-Community][] of Microsoft [PowerShell Tech-Community][].
We bieden geen garantie er dat het probleem worden aangepakt of tijdig opgelost.
Als er een probleem dat onmiddellijke aandacht vereist, moet u de traditionele betaald ondersteuningsopties.

## <a name="lifecycle-of-powershell-core"></a>Levenscyclus van PowerShell Core

Het gebruik nemen van PowerShell Core de [moderne Lifecycle-beleid van Microsoft][modern].
Deze ondersteuningslevenscyclus is bedoeld om klanten up-to-date houden met de meest recente versies.

De versie 6.x-vertakking van PowerShell Core ongeveer om de zes maanden worden bijgewerkt (zoals 6.0, 6.1, 6.2, enz.)

> [!IMPORTANT]
> U moet bijwerken in zes maanden na de release van elke nieuwe secundaire versie om te blijven ontvangen van ondersteuning.

Bijvoorbeeld, als PowerShell Core 6.1 is uitgebracht op 1e juli 2018, zou worden uitgegaan dat u voor het bijwerken naar PowerShell Core 6.1 door 1e januari 2019 voor verdere ondersteuning.

![Levenscyclus van de vertakking PowerShell Core][lifecycle-chart]

Het moderne Lifecycle-beleid vereist ook dat Microsoft geeft klanten 12 maanden kennisgeving voordat beëindigde ondersteuning voor een product (dat wil zeggen PowerShell Core).

Uiteindelijk we verwachten PowerShell Core invoert 'op lange termijn onderhoud' benadering waar we alleen onderhoud en beveiliging vereist updates moeten worden ondersteund op een specifieke vertakking of de versie van 6.x blijven.

## <a name="supported-platforms"></a>Ondersteunde platformen

PowerShell Core wordt officieel ondersteund op de volgende platforms:

* Windows 7, 8.1 en 10
* Windows Server 2008 R2, 2012 R2, 2016
* [Windows-serverkanaal puntkomma per jaar][semi-annual]
* Ubuntu 14.04 16.04 en 17.04
* Debian 8,7 + en 9
* CentOS 7
* Red Hat Enterprise Linux 7
* OpenSUSE 42,2
* Fedora 27, 28
* macOS 10.12+

Onze community heeft ook bijgedragen pakketten voor de volgende platforms, maar ze zijn niet officieel suppported:

* Boog Linux
* Kali Linux
* AppImage (werkt op meerdere platforms voor Linux)

## <a name="notes-on-licensing"></a>Opmerkingen over licentieverlening

PowerShell Core wordt uitgebracht onder de [MIT-licentie][].
Onder deze licentie, en in het ontbreken van een ondersteuningsovereenkomst betaalde, gebruikers zijn beperkt tot [communityondersteuning][].
Microsoft kan niet garanderen van reactiesnelheid of oplossingen met communityondersteuning.

## <a name="windows-powershell-module"></a>Windows PowerShell-Module

Ondersteuning voor PowerShell Core niet van toepassing op andere modules product tenzij expliciet ondersteuning voor die modules PowerShell Core.
Bijvoorbeeld, met behulp van de `ActiveDirectory` module die wordt geleverd als onderdeel van Windows Server een niet-ondersteund scenario is.

Modules die niet expliciet PowerShell Core ondersteunen mogelijk echter compatibel in sommige gevallen.
Door het installeren van de [ `WindowsPSModulePath` ][] -module, kunt u de Windows PowerShell toevoegen `PSModulePath` naar uw PowerShell-kern `PSModulePath`.

Installeer eerst de `WindowsPSModulePath` module op basis van de PowerShell-galerie:

```powershell
# Add `-Scope CurrentUser` if you're installing as non-admin
Install-Module WindowsPSModulePath -Force
```

Voer na het installeren van deze module de `Add-WindowsPSModulePath` cmdlet om toe te voegen van de Windows PowerShell `PSModulePath` naar PowerShell-kern:

```powershell
# Add this line to your profile if you always want Windows PowerShell PSModulePath
Add-WindowsPSModulePath
```

[Premier]: https://www.microsoft.com/en-us/microsoftservices/support.aspx
[enterprise-agreement]: https://www.microsoft.com/en-us/licensing/licensing-programs/enterprise.aspx
[assurance]: https://www.microsoft.com/en-us/licensing/licensing-programs/software-assurance-default.aspx
[communityondersteuning]: https://github.com/powershell/powershell/issues
[Microsoft-Community]: https://answers.microsoft.com/
[PowerShell Tech-Community]: https://techcommunity.microsoft.com/t5/PowerShell/ct-p/WindowsPowerShell
[ondersteuning]: https://support.microsoft.com/assistedsupportproducts
[modern]: https://support.microsoft.com/help/30881/modern-lifecycle-policy
[lifecycle-chart]: ./images/modern-lifecycle.png
[semi-annual]: https://docs.microsoft.com/windows-server/get-started/semi-annual-channel-overview
[MIT-licentie]: https://github.com/PowerShell/PowerShell/blob/master/LICENSE.txt
['WindowsPSModulePath']: https://www.powershellgallery.com/packages/WindowsPSModulePath/
