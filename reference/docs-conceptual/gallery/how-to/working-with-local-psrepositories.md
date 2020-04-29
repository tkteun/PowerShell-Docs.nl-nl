---
ms.date: 11/06/2018
contributor: JKeithB
keywords: Galerie, Power shell, cmdlet, psgallery, psget
title: Werken met lokale PSRepositories
ms.openlocfilehash: c1bd905674ae76a3badd3eff50780f0e1bb5fc64
ms.sourcegitcommit: 6545c60578f7745be015111052fd7769f8289296
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 04/22/2020
ms.locfileid: "75415822"
---
# <a name="working-with-private-powershellget-repositories"></a>Werken met PowerShellGet-privé-opslagplaatsen

De PowerShellGet-module ondersteunt andere opslag plaatsen dan de PowerShell Gallery.
Met deze cmdlets kunnen de volgende scenario's worden ingeschakeld:

- Ondersteuning voor een vertrouwde, vooraf gevalideerde set Power shell-modules voor gebruik in uw omgeving
- Een CI/CD-pijp lijn testen die Power shell-modules of-scripts bouwt
- Power shell-scripts en-modules leveren aan systemen die geen toegang tot internet hebben
- Power shell-scripts en-modules bieden die alleen beschikbaar zijn voor uw organisatie

In dit artikel wordt beschreven hoe u een lokale Power shell-opslag plaats instelt. Het artikel heeft ook betrekking op de [OfflinePowerShellGetDeploy][] -module die beschikbaar is via de PowerShell Gallery. Deze module bevat cmdlets voor het installeren van de meest recente versie van PowerShellGet in uw lokale opslag plaats.

## <a name="local-repository-types"></a>Typen lokale opslag plaats

Er zijn twee manieren om een lokale PSRepository: NuGet-server of-bestands share te maken. Elk type heeft voor-en nadelen:

### <a name="nuget-server"></a>NuGet-server

| Voordelen| Nadelen |
| --- | --- |
| PowerShellGallery-functionaliteit nauw keurig nabootsen | Voor een app met meerdere lagen is ondersteuning van operations-planning & |
| NuGet kan worden geïntegreerd met Visual Studio, andere hulpprogram ma's | Het verificatie model en het NuGet-account beheer zijn vereist |
| NuGet biedt ondersteuning voor `.Nupkg` meta gegevens in pakketten | Voor publiceren is API-sleutel beheer & onderhoud vereist |
| Biedt zoeken, pakket beheer, enzovoort. | |

### <a name="file-share"></a>Bestandsshare

| Voordelen| Nadelen |
| --- | --- |
| Eenvoudig in te stellen, back-ups te maken en te onderhouden | Meta gegevens die door PowerShellGet worden gebruikt, zijn niet beschikbaar |
| Eenvoudig beveiligings model: gebruikers machtigingen voor de share | Geen gebruikers interface buiten de basis bestands share |
| Geen beperkingen, zoals het vervangen van bestaande items | Beperkte beveiliging en geen opname van wie kan bijwerken wat er gebeurt |

PowerShellGet werkt met beide typen en biedt ondersteuning voor het zoeken van versies en afhankelijkheids installatie.
Sommige functies die werken voor de PowerShell Gallery zijn echter niet beschikbaar voor basis NuGet-servers of-bestands shares.

- Alles is een pakket-geen differentiatie van scripts, modules, DSC-resources of functie mogelijkheden.
- Bestands share servers kunnen geen meta gegevens van pakketten zien, met inbegrip van tags.

## <a name="creating-a-local-repository"></a>Een lokale opslag plaats maken

In het volgende artikel worden de stappen beschreven voor het instellen van uw eigen NuGet-server.

- [NuGet. server][]

Volg de stappen tot en met het punt om pakketten toe te voegen. De stappen voor het [publiceren van een pakket](#publishing-to-a-local-repository) worden verderop in dit artikel besproken.

Zorg ervoor dat uw gebruikers machtigingen hebben voor toegang tot de bestands share voor een opslag plaats op basis van een bestands share.

## <a name="registering-a-local-repository"></a>Een lokale opslag plaats registreren

Voordat een opslag plaats kan worden gebruikt, moet deze worden geregistreerd met `Register-PSRepository` behulp van de opdracht.
In de onderstaande voor beelden wordt de **InstallationPolicy** ingesteld op *vertrouwd*, op de veronderstelling dat u uw eigen opslag plaats vertrouwt.

```powershell
# Register a NuGet-based server
Register-PSRepository -Name LocalPSRepo -SourceLocation http://MyLocalNuget/Api/V2/ -ScriptSourceLocation http://MyLocalNuget/Api/V2 -InstallationPolicy Trusted

# Register a file share on my local machine
Register-PSRepository -Name LocalPSRepo -SourceLocation '\\localhost\PSRepoLocal\' -ScriptSourceLocation '\\localhost\PSRepoLocal\' -InstallationPolicy Trusted
```

Let op het verschil tussen hoe de twee opdrachten **ScriptSourceLocation**verwerken. Voor opslag plaatsen op basis van een bestands share moeten de **SourceLocation** en **ScriptSourceLocation** overeenkomen. Voor een op het web gebaseerde opslag plaatsen moeten ze verschillend zijn, dus in dit voor beeld wordt een navolgende toegevoegd aan de **SourceLocation**.

Als u de zojuist gemaakte PSRepository de standaard opslagplaats wilt maken, moet u de registratie van alle andere PSRepositories ongedaan maken. Bijvoorbeeld:

```powershell
Unregister-PSRepository -Name PSGallery
```

> [!NOTE]
> De naam van de opslag plaats ' PSGallery ' is gereserveerd voor gebruik door de PowerShell Gallery. U kunt de registratie van PSGallery ongedaan maken, maar u kunt de naam PSGallery niet opnieuw gebruiken voor een andere opslag plaats.

Als u de PSGallery wilt herstellen, voert u de volgende opdracht uit:

```powershell
Register-PSRepository -Default
```

## <a name="publishing-to-a-local-repository"></a>Publiceren naar een lokale opslag plaats

Zodra u de lokale PSRepository hebt geregistreerd, kunt u publiceren naar uw lokale PSRepository. Er zijn twee belang rijke scenario's: uw eigen module publiceren en een module publiceren vanuit de PSGallery.

### <a name="publishing-a-module-you-authored"></a>Een module publiceren die u hebt gemaakt

Gebruik `Publish-Module` en `Publish-Script` om uw module te publiceren op uw lokale PSRepository op dezelfde manier als voor de PowerShell Gallery.

- De locatie voor de code opgeven
- Een API-sleutel opgeven
- Geef de naam van de opslag plaats op. Bijvoorbeeld: `-PSRepository LocalPSRepo`

> [!NOTE]
> U moet een account maken op de NuGet-server en u vervolgens aanmelden om de API-sleutel te genereren en op te slaan.
> Voor een bestands share gebruikt u een niet-lege teken reeks voor de waarde NuGetApiKey.

Voorbeelden:

```powershell
# Publish to a NuGet Server repository using my NuGetAPI key
Publish-Module -Path 'c:\projects\MyModule' -Repository LocalPsRepo -NuGetApiKey 'oy2bi4avlkjolp6bme6azdyssn6ps3iu7ib2qpiudrtbji'
```

```powershell
# Publish to a file share repo - the NuGet API key must be a non-blank string
Publish-Module -Path 'c:\projects\MyModule' -Repository LocalPsRepo -NuGetApiKey 'AnyStringWillDo'
```

> [!IMPORTANT]
> Om de beveiliging te waarborgen, moeten API-sleutels niet in scripts worden vastgelegd. Gebruik een systeem voor beveiligd sleutel beheer.

### <a name="publishing-a-module-from-the-psgallery"></a>Een module publiceren vanuit de PSGallery

Als u een module van de PSGallery naar uw lokale PSRepository wilt publiceren, kunt u de cmdlet Save-package gebruiken.

- De naam van het pakket opgeven
- Geef ' NuGet ' op als provider
- Geef de locatie van de PSGallery op als de bron (https://www.powershellgallery.com/api/v2)
- Het pad naar uw lokale opslag plaats opgeven

Voorbeeld:

```powershell
# Publish from the PSGallery to your local Repository
Save-Package -Name 'PackageName' -Provider NuGet -Source https://www.powershellgallery.com/api/v2 -Path '\\localhost\PSRepoLocal\'
```

Als uw lokale PSRepository is gebaseerd op het web, is er een extra stap nodig die gebruikmaakt van nuget. exe om te publiceren.

Raadpleeg de documentatie voor het gebruik van [nuget. exe][].

## <a name="installing-powershellget-on-a-disconnected-system"></a>PowerShellGet installeren op een systeem zonder verbinding

Het implementeren van PowerShellGet is moeilijk in omgevingen waarin de verbinding van systemen met internet is vereist. PowerShellGet heeft een Boots trap proces waarmee de nieuwste versie wordt geïnstalleerd wanneer deze voor de eerste keer wordt gebruikt. De OfflinePowerShellGetDeploy-module in de PowerShell Gallery biedt cmdlets die dit Boots trap proces ondersteunen.

Als u een offline-implementatie wilt Boots trappen, moet u het volgende doen:

- Down load en installeer de OfflinePowerShellGetDeploy uw systeem met Internet verbinding en uw niet-verbonden systemen
- PowerShellGet en de bijbehorende afhankelijkheden downloaden op het met internet verbonden systeem `Save-PowerShellGetForOffline` met behulp van de cmdlet
- PowerShellGet en de bijbehorende afhankelijkheden kopiëren van het systeem dat is verbonden met internet naar het niet-verbonden systeem
- Gebruik de `Install-PowerShellGetOffline` op het niet-verbonden systeem om PowerShellGet en de bijbehorende afhankelijkheden in de juiste mappen te plaatsen

De volgende opdrachten gebruiken `Save-PowerShellGetForOffline` om alle onderdelen in een map te plaatsen`f:\OfflinePowerShellGet`

```powershell
# Requires -RunAsAdministrator
#Download the OfflinePowerShellGetDeploy to a location that can be accessed
# by both the connected and disconnected systems.
Save-Module -Name OfflinePowerShellGetDeploy -Path 'F:\' -Repository PSGallery
Import-Module F:\OfflinePowerShellGetDeploy

# Put PowerShellGet somewhere locally
Save-PowerShellGetForOffline -LocalFolder 'F:\OfflinePowerShellGet'
```

Op dit moment moet u de inhoud van `F:\OfflinePowerShellGet` beschikbaar maken voor uw niet-verbonden systemen. Voer de `Install-PowerShellGetOffline` cmdlet uit om PowerShellGet op het niet-verbonden systeem te installeren.

> [!NOTE]
> Het is belang rijk dat u PowerShellGet in de Power shell-sessie niet uitvoert voordat u deze opdrachten uitvoert. Zodra PowerShellGet in de sessie is geladen, kunnen de onderdelen niet worden bijgewerkt. Als u PowerShellGet per ongeluk start, sluit u Power shell af en start u het opnieuw.

```powershell
Import-Module F:\OfflinePowerShellGetDeploy

Install-PowerShellGetOffline -LocalFolder 'F:\OfflinePowerShellGet'
```

Nadat u deze opdrachten hebt uitgevoerd, kunt u PowerShellGet publiceren naar uw lokale opslag plaats.

```powershell
# Publish to a NuGet Server repository using my NuGetAPI key
Publish-Module -Path 'F:\OfflinePowershellGet' -Repository LocalPsRepo -NuGetApiKey 'oy2bi4avlkjolp6bme6azdyssn6ps3iu7ib2qpiudrtbji'

# Publish to a file share repo - the NuGet API key must be a non-blank string
Publish-Module -Path 'F:\OfflinePowerShellGet' -Repository LocalPsRepo -NuGetApiKey 'AnyStringWillDo'
```

## <a name="use-packaging-solutions-to-host-powershellget-repositories"></a>Verpakkings oplossingen gebruiken voor het hosten van PowerShellGet-opslag plaatsen

U kunt ook verpakkings oplossingen zoals Azure-artefacten gebruiken om een persoonlijke of open bare PowerShellGet-opslag plaats te hosten. Zie de [documentatie van Azure artefacten](https://docs.microsoft.com/azure/devops/artifacts/tutorials/private-powershell-library)voor meer informatie en instructies.

> [!IMPORTANT]
> Om de beveiliging te waarborgen, moeten API-sleutels niet in scripts worden vastgelegd. Gebruik een systeem voor beveiligd sleutel beheer.

<!-- external links -->
[OfflinePowerShellGetDeploy]: https://www.powershellgallery.com/packages/OfflinePowerShellGetDeploy/0.1.1
[Nuget. server]: /nuget/hosting-packages/nuget-server
[nuget. exe]: /nuget/tools/nuget-exe-cli-reference
