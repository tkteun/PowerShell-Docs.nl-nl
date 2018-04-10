---
ms.date: 06/12/2017
contributor: manikb
ms.topic: reference
keywords: Galerie, powershell, cmdlet, psget
title: Get-InstalledScript
ms.openlocfilehash: 668327905b0dab40119940a3134b674c452f538d
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 04/09/2018
---
# <a name="get-installedscript"></a>Get-InstalledScript

Haalt geïnstalleerde scripts op een computer.

## <a name="description"></a>Beschrijving

De cmdlet Get-InstalledScript haalt geïnstalleerde PowerShell-scripts op een computer.

Voor elke geïnstalleerde script retourneert Get-InstalledScript een PSRepositoryItemInfo-object dat kan eventueel worden doorgesluisd naar Uninstall-Script voor het verwijderen van de geïnstalleerde scripts.

- Get-InstalledScript kunt geïnstalleerde scripts op basis van naam, Versieparameters filteren.
- Get-InstalledScript kunt filteren met Versieparameters: MinimumVersion, MaximumVersion, RequiredVersion, AllVersions.
  - Deze parameters zijn, met uitzondering van MinmimumVersion en MaximumVersion, sluiten elkaar wederzijds uit.
  - Deze Versieparameters zijn alleen met de naam van één script zonder eventuele jokertekens toegestaan.
  - Als de parameter RequiredVersion niet is opgegeven, retourneert Get-InstalledScript de meest recente versie van het geïnstalleerde script dat gelijk is aan of groter is dan de opgegeven minimumversie of de nieuwste versie van het script als er geen minimum versie is opgegeven.
  - Als de parameter RequiredVersion is opgegeven, wordt met Get-InstalledScript alleen de versie van geïnstalleerde script die exact overeenkomt met de opgegeven versie retourneert.

## <a name="cmdlet-syntax"></a>De syntaxis van cmdlet

```powershell
Get-Command -Name Get-InstalledScript -Module PowerShellGet -Syntax
```

## <a name="cmdlet-online-help-reference"></a>Verwijzing naar het online help van cmdlet

[Get-InstalledScript](http://go.microsoft.com/fwlink/?LinkId=619790)

## <a name="example-commands"></a>Voorbeeldopdrachten

```powershell

# Get all scripts installed using PowerShellGet cmdlets
Get-InstalledScript

# Get a specific installed script
Get-InstalledScript Show-Tree

Version    Name                                Repository           Description
-------    ----                                ----------           -----------
1.0.0      Show-Tree                           PSGallery            Script to show the layout of PowerShell namespaces (Tr...

# Get installed script with wildcards
Get-InstalledScript -Name *Azure*

# Get all versions of an installed script
Get-InstalledScript -Name Connect-O365 -AllVersions

# Get installed script with MinimumVersion
Get-InstalledScript -Name Connect-O365 -MinimumVersion 1.1

# Get installed script with MaximumVersion
Get-InstalledScript -Name Connect-O365 -MaximumVersion 1.6.3

# Get installed script with version range
Get-InstalledScript -Name Connect-O365 -MinimumVersion 1.1 -MaximumVersion 1.6.3

# Get installed script with RequiredVersion
Get-InstalledScript -Name Connect-O365 -RequiredVersion 1.4

# Properties of Get-InstalledScript returned object
Get-InstalledScript Show-Tree | Format-List * -Force

Name                       : Show-Tree
Version                    : 1.0.0
Type                       : Script
Description                : Script to show the layout of PowerShell namespaces (Trees) using ASCII
Author                     : Jeffrey Snover
CompanyName                : jsnover
Copyright                  : (C) Microsoft Corporation. All rights reserved.
PublishedDate              : 2/15/2016 10:15:35 PM
InstalledDate              : 5/4/2016 11:44:13 PM
UpdatedDate                :
LicenseUri                 :
ProjectUri                 :
IconUri                    :
Tags                       : {Nano, PSScript}
Includes                   : {Function, RoleCapability, Command, DscResource...}
PowerShellGetFormatVersion :
ReleaseNotes               :
Dependencies               : {}
RepositorySourceLocation   : https://www.powershellgallery.com/api/v2/
Repository                 : PSGallery
PackageManagementProvider  : NuGet
AdditionalMetadata         : {description, installeddate, tags, PackageManagementProvider...}
InstalledLocation          : C:\Program Files\WindowsPowerShell\Scripts


```