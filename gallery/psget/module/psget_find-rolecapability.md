---
ms.date: 2017-06-12
contributor: manikb
ms.topic: reference
keywords: Galerie, powershell, cmdlet, psget
title: Zoeken naar RoleCapability
ms.openlocfilehash: 77c5b492d9681fa05315401fba410c508af1d13b
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 06/12/2017
---
# <a name="find-rolecapability"></a>Zoeken naar RoleCapability

Hiermee zoekt rol mogelijkheden in modules.

## <a name="description"></a>Beschrijving
De cmdlet zoeken RoleCapability zoekt PowerShell rol mogelijkheden in modules. Modules zoekt zoeken RoleCapability in geregistreerde opslagplaatsen. Voor de capaciteit van elke rol die deze cmdlet vindt, wordt een PSGetRoleCapabilityInfo-object. U kunt een PSGetRoleCapabilityInfo-object doorgeven aan de cmdlet Install-Module voor het installeren van de module met de mogelijkheid van de rol.
PowerShell rol mogelijkheden definiëren die opdrachten, toepassingen, enzovoort beschikbaar zijn voor een gebruiker op een eindpunt net genoeg Administration (JEA). Rol mogelijkheden worden gedefinieerd door de bestanden met de extensie .psrc.

- Zoeken naar RoleCapability kunt filteren met Versieparameters: MinimumVersion, RequiredVersion, AllVersions.
  - Deze parameters elkaar wederzijds uit.
  - Deze Versieparameters zijn alleen met de naam van de één module zonder eventuele jokertekens toegestaan.
  - Als de parameter RequiredVersion niet is opgegeven, retourneert zoeken RoleCapability de nieuwste versie van de module die gelijk is aan of groter is dan de opgegeven minimumversie of de nieuwste versie van de module als er geen minimum versie is opgegeven.
  - Als de parameter RequiredVersion is opgegeven, retourneert zoeken RoleCapability alleen de versie van de module die exact overeenkomt met de opgegeven versie.
- Zoeken naar RoleCapability kunt filteren op de metagegevens van de module met de - parameter van label
- Zoeken naar RoleCapability kunt filteren op zoektaal opslagplaats-specifieke met de - parameter Filter.
- Zoeken naar RoleCapability kunt filteren op modules van alle of enkele van de geregistreerde opslagplaatsen.

## <a name="cmdlet-syntax"></a>De syntaxis van cmdlet
```powershell
Get-Command -Name Find-RoleCapability -Module PowerShellGet -Syntax
```

## <a name="cmdlet-online-help-reference"></a>Verwijzing naar het online help van cmdlet

[Zoeken naar RoleCapability](http://go.microsoft.com/fwlink/?LinkId=718029)

## <a name="example-commands"></a>Voorbeeldopdrachten
```powershell

# Find a specific role capability
Find-RoleCapability -Name Maintenance

Name                                Version    ModuleName                          Repository
----                                -------    ----------                          ----------
Maintenance                         1.5.0      RoleCapModule                       PrivatePSGallery

# Find multiple role capabilities
Find-RoleCapability -Name MyJeaRole, Maintenance

# Find all available role capabilities from all registered repositories
Find-RoleCapability

# Find available role capabilities from few registered repositories
Find-RoleCapability -Repository PSGallery,PrivatePSGallery

# Find all role capabilities in a specified repository
Find-RoleCapability -Repository PSGallery

# Find a role capability defined in a specific module
Find-RoleCapability -Name Maintenance -ModuleName RoleCapModule

# Find role capabilities from all versions of a module
Find-RoleCapability -ModuleName RoleCapModule -AllVersions

# Find role capabilities with module name and MinimumVersion.
Find-RoleCapability -ModuleName RoleCapModule -MinimumVersion 1.1

# Find role capabilities with module name and exact version
Find-RoleCapability -ModuleName RoleCapModule -RequiredVersion 1.4.0

# Find role capabilities defined modules with -Filter based search. -Filter searches in description and module names
Find-RoleCapability -Filter Cookbook
Find-RoleCapability -Filter RBAC

# Find all role capabilities with tags Azure or DSC in module metadata
Find-RoleCapability -Tag Azure, DSC

```

