---
ms.date: 2017-06-12
contributor: manikb
ms.topic: reference
keywords: Galerie, powershell, cmdlet, psget
title: Opdracht Zoeken
ms.openlocfilehash: f867f12b1c6efad30a04581c6f36c5a77a2fb2ae
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 06/12/2017
---
# <a name="find-command"></a>Opdracht Zoeken

Hiermee zoekt PowerShell-opdrachten in modules.

## <a name="description"></a>Beschrijving
De opdracht Zoeken cmdlet vindt een PowerShell-opdrachten zoals cmdlets, aliassen, functies en werkstromen. Opdracht Zoeken zoekt modules in geregistreerde opslagplaatsen.
Voor elke opdracht die door deze cmdlet worden gevonden, retourneert deze een PSGetCommandInfo-object. U kunt een PSGetCommandInfo-object doorgeven aan de cmdlet Install-Module voor het installeren van de module waarin de opdracht.

- Opdracht Zoeken kunt filteren met Versieparameters: MinimumVersion, RequiredVersion, AllVersions.
  - Deze parameters elkaar wederzijds uit.
  - Deze Versieparameters zijn alleen met de naam van de één module zonder eventuele jokertekens toegestaan.
  - Als de parameter RequiredVersion niet is opgegeven, retourneert opdracht Zoeken de nieuwste versie van de module die gelijk is aan of groter is dan de opgegeven minimumversie of de nieuwste versie van de module als er geen minimum versie is opgegeven.
  - Als de parameter RequiredVersion is opgegeven, zijn zoeken opdracht retourneert alleen de versie van de module die exact overeenkomt met de opgegeven versie.
- Opdracht Zoeken kunt filteren op de metagegevens van de module met de - parameter van label
- Opdracht Zoeken kunt filteren op zoektaal opslagplaats-specifieke met de - parameter Filter.
- Opdracht Zoeken kunt filteren op modules van alle of enkele van de geregistreerde opslagplaatsen.

## <a name="cmdlet-syntax"></a>De syntaxis van cmdlet
```powershell
Get-Command -Name Find-Command -Module PowerShellGet -Syntax
```

## <a name="cmdlet-online-help-reference"></a>Verwijzing naar het online help van cmdlet

[Opdracht Zoeken](http://go.microsoft.com/fwlink/?LinkId=733636)

## <a name="example-commands"></a>Voorbeeldopdrachten
```powershell

# Find a specific command
Find-Command -Name Get-ScriptAnalyzerRule

Name                                Version    ModuleName                          Repository
----                                -------    ----------                          ----------
Get-ScriptAnalyzerRule              1.5.0      PSScriptAnalyzer                    PSGallery

# Find multiple commands
Find-Command -Name Get-ScriptAnalyzerRule, Invoke-ScriptAnalyzer

# Find all available commands from all registered repositories
Find-Command

# Find available commands from few registered repositories
Find-Command -Repository PSGallery,PrivatePSGallery

# Find all commands in a specified repository
Find-Command -Repository PSGallery

# Find a command defined in a specific module
Find-Command -Name Get-ScriptAnalyzerRule -Module PSScriptAnalyzer

# Find commands from all versions of a module
Find-Command -ModuleName PSReadline -AllVersions

# Find commands with module name and MinimumVersion.
Find-Command -ModuleName PSReadline -MinimumVersion 1.1

# Find commands with module name and exact version
Find-Command -ModuleName AzureRM -RequiredVersion 1.4.0

# Find commands defined modules with -Filter based search. -Filter searches in description and module names
Find-Command -Filter Cookbook
Find-Command -Filter RBAC

# Find all commands with tags Azure or DSC in module metadata
Find-Command -Tag Azure, DSC

```

