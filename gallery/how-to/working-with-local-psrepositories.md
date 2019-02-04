---
ms.date: 11/06/2018
contributor: JKeithB
keywords: Galerie, powershell, cmdlet, psgallery, psget
title: Werken met lokale PSRepositories
ms.openlocfilehash: 94824ea584c097838b24c6f2cd02407b6147a781
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 02/03/2019
ms.locfileid: "55688390"
---
# <a name="working-with-local-powershellget-repositories"></a>Werken met lokale PowerShellGet-opslagplaatsen

De PowerShellGet-module-ondersteuning-opslagplaatsen dan de PowerShell Gallery.
Deze cmdlets kunt de volgende scenario's:

- Ondersteuning voor een vertrouwd en vooraf gevalideerde set PowerShell-modules voor gebruik in uw omgeving
- Een CI/CD-pijplijn die PowerShell-modules of scripts voortbouwt testen
- PowerShell-scripts en modules leveren voor systemen die geen toegang internet tot

Dit artikel wordt beschreven hoe u een lokale PowerShell-opslagplaats kunt instellen. Het artikel ook aandacht besteed aan het [OfflinePowerShellGetDeploy][] module die beschikbaar zijn vanuit de PowerShell Gallery. Deze module bevat cmdlets voor het installeren van de meest recente versie van PowerShellGet in uw lokale opslagplaats.

## <a name="local-repository-types"></a>Typen van de lokale opslagplaats

Er zijn twee manieren om te maken van een lokale PSRepository: NuGet-server of bestandsshare. Elk type heeft voor- en nadelen:

NuGet-Server

| Voordelen| Nadelen |
| --- | --- |
| Komt sterk overeen PowerShellGallery-functionaliteit | App met meerdere lagen vereist planning bewerkingen en ondersteuning |
| NuGet kan worden geïntegreerd met Visual Studio, andere hulpprogramma 's | Verificatiemodel en NuGet-accounts beheren die nodig zijn |
| NuGet biedt ondersteuning voor metagegevens in `.Nupkg` pakketten | Publicatie moet de API-sleutel en -onderhoud |
| Biedt zoeken, Pakketbeheer, enzovoort. | |

Bestandsshare

| Voordelen| Nadelen |
| --- | --- |
| Eenvoudig instellen, back-up maken en onderhouden | Metagegevens die worden gebruikt door de PowerShellGet is niet beschikbaar |
| Eenvoudige beveiligingsmodel - gebruikersmachtigingen voor de share | Er is geen gebruikersinterface naast basisopdrachten voor bestandsbeheer delen |
| Er zijn geen beperkingen, zoals bestaande artikelen vervangen | Beperkte beveiliging en geen de opname van wie wat bijgewerkt |

PowerShellGet werkt met het type en ondersteunt versies en de installatie van afhankelijkheid te zoeken.
Sommige functies die voor de PowerShell Gallery werken zijn echter niet beschikbaar voor basis NuGet-servers of -bestandsshares.

- Alles wat is een pakket - niet differentiatie van scripts, modules, DSC-resources of rolmogelijkheden.
- Share bestandsservers kunnen pakketmetagegevens, met inbegrip van tags niet zien.

## <a name="creating-a-local-repository"></a>Het maken van een lokale opslagplaats

Het volgende artikel vindt u de stappen voor het instellen van uw eigen NuGet-Server.

- [NuGet.Server][]

Volg de stappen tot het moment van het toevoegen van pakketten. De stappen voor het [publiceren van een pakket](#publishing-to-a-local-repository) verderop in dit artikel worden besproken.

Voor een bestand op basis van een share-opslagplaats, ervoor zorgen dat uw gebruikers machtigingen hebben voor toegang tot de bestandsshare.

## <a name="registering-a-local-repository"></a>Een lokale opslagplaats registreren

Voordat een opslagplaats kan worden gebruikt, moet deze worden geregistreerd met behulp van de `Register-PSRepository` opdracht.
In de onderstaande voorbeelden de **InstallationPolicy** is ingesteld op *vertrouwde*, op de veronderstelling dat u uw eigen opslagplaats vertrouwen.

```powershell
# Register a NuGet-based server
Register-PSRepository -Name LocalPSRepo -SourceLocation http://MyLocalNuget/Api/V2/ -ScriptSourceLocation http://MyLocalNuget/Api/V2 -InstallationPolicy Trusted

# Register a file share on my local machine
Register-PSRepository -Name LocalPSRepo -SourceLocation '\\localhost\PSRepoLocal\' -ScriptSourceLocation '\\localhost\PSRepoLocal\' -InstallationPolicy Trusted
```

Noteer het verschil tussen hoe de twee opdrachten verwerkt **ScriptSourceLocation**. Voor een bestand op basis van een share-opslagplaatsen, de **SourceLocation** en **ScriptSourceLocation** moeten overeenkomen. Een website op basis van-opslagplaats, moeten ze verschillend zijn, dus in dit voorbeeld een afsluitende '/' wordt toegevoegd aan de **SourceLocation**.

Als u wilt dat de zojuist gemaakte PSRepository moet de standaard-opslagplaats, moet u de registratie ongedaan maken voor alle andere PSRepositories. Bijvoorbeeld:

```powershell
Unregister-PSRepository -Name PSGallery
```

> [!NOTE]
> De naam van de opslagplaats 'PSGallery' is gereserveerd voor gebruik door de PowerShell Gallery. U kunt de registratie ongedaan maken PSGallery, maar u kunt de naam PSGallery voor een andere opslagplaats niet opnieuw gebruiken.

Als u herstellen van de PSGallery wilt, voert u de volgende opdracht uit:

```powershell
Register-PSRepository -Default
```

## <a name="publishing-to-a-local-repository"></a>Publiceren naar een lokale opslagplaats

Zodra u de lokale PSRepository hebt geregistreerd, kunt u publiceren op uw lokale PSRepository. Er zijn twee hoofdscenario publishing's: uw eigen module publiceren en publiceren van een module op basis van de PSGallery.

### <a name="publishing-a-module-you-authored"></a>Publiceren van een module die u gemaakt

Gebruik `Publish-Module` en `Publish-Script` uw module publiceren naar uw lokale PSRepository de dezelfde manier als voor de PowerShell Gallery.

- Geef de locatie voor uw code
- Een API-sleutel opgeven
- Geef de naam van de opslagplaats. bijvoorbeeld `-PSRepository LocalPSRepo`

> [!NOTE]
> U moet een account maken in de NuGet-server en meld u aan om te genereren en opslaan van de API-sleutel.
> Gebruik een niet-lege tekenreeks voor de NuGetApiKey-waarde voor een bestandsshare.

Voorbeelden:

```powershell
# Publish to a NuGet Server repository using my NuGetAPI key
Publish-Module -Path 'c:\projects\MyModule' -Repository LocalPsRepo -NuGetApiKey 'oy2bi4avlkjolp6bme6azdyssn6ps3iu7ib2qpiudrtbji'

# Publish to a file share repo - the NuGet API key must be a non-blank string
Publish-Module -Path 'c:\projects\MyModule' -Repository LocalPsRepo -NuGetApiKey 'AnyStringWillDo'
```

> [!IMPORTANT]
> Om beveiliging te waarborgen, mag API-sleutels niet zijn hardgecodeerd in scripts. Een systeem veilig Sleutelbeheer gebruiken.

### <a name="publishing-a-module-from-the-psgallery"></a>Een module op basis van de PSGallery publiceren

Voor het publiceren van een module op basis van de PSGallery naar uw lokale PSRepository, kunt u de cmdlet 'Opslaan-Package'.

- Geef de naam van het pakket
- 'NuGet' opgeven als de Provider
- De locatie PSGallery opgeven als de bron (https://www.powershellgallery.com/api/v2)
- Geef het pad op naar uw lokale opslagplaats

Voorbeeld:

```powershell
# Publish from the PSGallery to your local Repository
Save-Package -Name 'PackageName' -Provider Nuget -Source https://www.powershellgallery.com/api/v2 -Path '\\localhost\PSRepoLocal\'
```

Als uw lokale PSRepository webgebaseerde, hiervoor een extra stap die gebruikmaakt van nuget.exe om te publiceren.

Zie de documentatie voor het gebruik van [nuget.exe][].

## <a name="installing-powershellget-on-a-disconnected-system"></a>PowerShellGet installeren op een niet-verbonden systeem

PowerShellGet implementeren is het moeilijk in omgevingen waarvoor systemen worden losgekoppeld van het internet. PowerShellGet heeft een bootstrap proces dat de eerste keer dat deze wordt gebruikt voor de meest recente versie installeert. De module OfflinePowerShellGetDeploy in de PowerShell Gallery bevat cmdlets die ondersteuning bieden voor deze bootstrap-proces.

Als u wilt de implementatie van een offline bootstrap, moet u naar:

- Download en installeer het systeem OfflinePowerShellGetDeploy uw internetverbinding en uw niet-verbonden systemen
- Downloaden van PowerShellGet en de bijbehorende afhankelijkheden op het internet verbonden systeem gebruikt de `Save-PowerShellGetForOffline` cmdlet
- PowerShellGet en de bijbehorende afhankelijkheden van het internet verbonden systeem naar het niet-verbonden systeem kopiëren
- Gebruik de `Install-PowerShellGetOffline` op het niet-verbonden systeem PowerShellGet en de bijbehorende afhankelijkheden in de juiste mappen plaatsen

De volgende opdrachten gebruikt `Save-PowerShellGetForOffline` om alle onderdelen in een map `f:\OfflinePowerShellGet`

```powershell
# Requires -RunAsAdministrator
#Download the OfflinePowerShellGetDeploy to a location that can be accessed
# by both the connected and disconnected systems.
Save-Module -Name OfflinePowerShellGetDeploy -Path 'F:\' -Repository PSGallery
Import-Module F:\OfflinePowerShellGetDeploy

# Put PowerShellGet somewhere locally
Save-PowerShellGetForOffline -LocalFolder 'F:\OfflinePowerShellGet'
```

Op dit moment moet u de inhoud van `F:\OfflinePowerShellGet` beschikbaar zijn voor uw niet-verbonden systemen. Voer de `Install-PowerShellGetOffline` cmdlet PowerShellGet installeren op de niet-verbonden systeem.

> [!NOTE]
> Het is belangrijk dat u niet PowerShellGet in de PowerShell-sessie uitvoert voordat u deze opdrachten uitvoert. Zodra de PowerShellGet in de sessie is geladen, kunnen de onderdelen kunnen niet worden bijgewerkt. Als u PowerShellGet per ongeluk starten, afsluiten en opnieuw opstarten van PowerShell.

```powershell
Import-Module F:\OfflinePowerShellGetDeploy

Install-PowerShellGetOffline -LocalFolder 'F:\OfflinePowerShellGet'
```

Na het uitvoeren van deze opdrachten, bent u klaar om te publiceren PowerShellGet op uw lokale opslagplaats.

```powershell
# Publish to a NuGet Server repository using my NuGetAPI key
Publish-Module -Path 'F:\OfflinePowershellGet' -Repository LocalPsRepo -NuGetApiKey 'oy2bi4avlkjolp6bme6azdyssn6ps3iu7ib2qpiudrtbji'

# Publish to a file share repo - the NuGet API key must be a non-blank string
Publish-Module -Path 'F:\OfflinePowerShellGet' -Repository LocalPsRepo -NuGetApiKey 'AnyStringWillDo'
```

> [!IMPORTANT]
> Om beveiliging te waarborgen, mag API-sleutels niet zijn hardgecodeerd in scripts. Een systeem veilig Sleutelbeheer gebruiken.

<!-- external links -->
[OfflinePowerShellGetDeploy]: https://www.powershellgallery.com/packages/OfflinePowerShellGetDeploy/0.1.1
[Nuget.Server]: /nuget/hosting-packages/nuget-server
[nuget.exe]: /nuget/tools/nuget-exe-cli-reference
