---
ms.date: 06/12/2017
contributor: manikb
ms.topic: reference
keywords: Galerie, powershell, cmdlet, psget
title: Find-DscResource
ms.openlocfilehash: 522a44e25c57a7dd75a098a1f34e53e74d96f4a6
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 04/09/2018
---
# <a name="find-dscresource"></a>Find-DscResource

Zoekt DSC-Resources in modules.

## <a name="description"></a>Beschrijving

De cmdlet zoeken DscResource vindt [Desired State Configuration (DSC)](https://msdn.microsoft.com/PowerShell/dsc/overview) bronnen die zich bevinden in de modules die overeenkomen met de opgegeven criteria uit geregistreerde opslagplaatsen.
Voor elke module die deze cmdlet wordt gevonden, retourneert zoeken DscResource een PSGetDscResourceInfo-object dat u kunt doorsluizen naar installatie-Module voor het installeren van de modules die met de resources die deze cmdlet retourneert.

DSC is een nieuw management-platform in Windows PowerShell waarmee implementeren en beheren van configuratiegegevens voor de, softwareservices en beheren van de omgeving waarin deze services worden uitgevoerd.

Desired dat State Configuration (DSC) bronnen vindt u de bouwstenen voor een DSC-configuratie. Een bron beschrijft eigenschappen die kunnen worden geconfigureerd (schema) en bevat de functies van de PowerShell-script die de lokale Configuration Manager (LCM) ' om deze te maken zodat' aanroept.

Een resource kan iets als algemene als een bestand of de instelling van een IIS-server zo specifiek model. Groepen van zoals bronnen worden gecombineerd in naar een DSC-Module, waarbij alle vereiste bestanden in een structuur die overdraagbaar en bevat metagegevens om te bepalen hoe de resources zijn bedoeld om te worden gebruikt.

- Zoeken naar DscResource kunt filteren met Versieparameters: MinimumVersion, RequiredVersion, AllVersions.
  - Deze parameters elkaar wederzijds uit.
  - Deze Versieparameters zijn alleen met de naam van de één module zonder eventuele jokertekens toegestaan.
  - Als de parameter RequiredVersion niet is opgegeven, retourneert zoeken DscResource de nieuwste versie van de module die gelijk is aan of groter is dan de opgegeven minimumversie of de nieuwste versie van de module als er geen minimum versie is opgegeven.
  - Als de parameter RequiredVersion is opgegeven, retourneert zoeken DscResource alleen de versie van de module die exact overeenkomt met de opgegeven versie.
- Zoeken naar DscResource kunt filteren op de metagegevens van de module met de - parameter van label
- Zoeken naar DscResource kunt filteren op zoektaal opslagplaats-specifieke met de - parameter Filter.
- Zoeken naar DscResource kunt filteren op modules van alle of enkele van de geregistreerde opslagplaatsen.

## <a name="cmdlet-syntax"></a>De syntaxis van cmdlet
```powershell
Get-Command -Name Find-DscResource -Module PowerShellGet -Syntax
```

## <a name="cmdlet-online-help-reference"></a>Verwijzing naar het online help van cmdlet

[Find-DscResource](http://go.microsoft.com/fwlink/?LinkId=517196)

## <a name="example-commands"></a>Voorbeeldopdrachten
```powershell

# Find a specific DSC Resource
Find-DscResource -Name xIisFeatureDelegation

Name                                Version    ModuleName                          Repository
----                                -------    ----------                          ----------
xIisFeatureDelegation               1.10.0.0   xWebAdministration                  PSGallery

# Find all available DSC Resources from all registered repositories
Find-DscResource

# Find a DSC resource by name
Find-DscResource -Name xWebsite

# Find multiple DSC Resources
Find-DscResource -Name xIisHandler, xFirewall

# Find all DSC resources contained within a specific module
Find-DscResource -ModuleName xNetworking
Find-DscResource -ModuleName xWebAdministration

# Find all DSC resources in modules with DSCResourceKit or DesiredStateConfiguration
Find-DscResource -Tag DesiredStateConfiguration, DSCResourceKit

# Find available DSC Resources from few registered repositories
Find-DscResource -Repository PSGallery,PrivatePSGallery

# Find all DSC Resources in a specified repository
Find-DscResource -Repository PSGallery

# Find DSC Resources from all versions of a module
Find-DscResource -ModuleName xNetworking -AllVersions

# Find DSC Resources with module name and MinimumVersion.
Find-DscResource -ModuleName xNetworking -MinimumVersion 1.1

# Find DSC Resources with module name and exact version
Find-DscResource -ModuleName xNetworking -RequiredVersion 2.1.1

# Find DSC Resources defined modules with -Filter based search. -Filter searches in description and module names
Find-DscResource -Filter Domain

# Find all DSC Resources with tags Azure or DSC in module metadata
Find-DscResource -Tag Azure, DSC

```