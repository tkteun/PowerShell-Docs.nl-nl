---
ms.date: 06/12/2017
keywords: wmf,powershell,installeren
ms.openlocfilehash: 9efc640dfda7e08e59d2c56746facd9658b1f9de
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 05/17/2018
ms.locfileid: "34222170"
---
# <a name="powershell-module-discovery-install-and-inventory-with-powershellget"></a>Detectie van de PowerShell-Module installeren en met PowerShellGet inventariseren

PowerShellGet is opgenomen in deze versie van WMF:
-   Zoek-Module kunt filteren op de metagegevens van de module met de - parameter van label
-   Zoek-Module kunt filteren op zoektaal opslagplaats-specifieke met de - parameter Filter
-   Zoek-Module kunt filteren op basis van de module met de opdracht-, - DscResource, inhoud en - parameters bevat
-   Zoeken naar DscResource kunt detectie van afzonderlijke DSC-resources in de opslagplaatsen
-   Ondersteuning voor het installeren van en publiceren naar de gedeelde bestanden met NuGet

## <a name="example-commands"></a>Voorbeeldopdrachten
```powershell
\# Find all modules with tags Azure or DSC
Find-Module -Tag Azure, DSC

\# Find modules with a specific DscResource
Find-Module -DscResource xFirewall

\#Find modules with specific commands
Find-Module -Command Get-ScriptAnalyzerRule, Invoke-ScriptAnalyzer

\# Find all modules with Dsc resources
Find-Module -Includes DscResource

\# Find all modules with cmdlets
Find-Module -Includes Cmdlet

\# Find all modules with functions
Find-Module -Includes Function

\# Find all DSC resources
Find-DscResource

\# Find all DSC resources contained within a specific module
Find-DscResource -ModuleName xNetworking

\# Find all DSC resources in modules with DSCResourceKit or DesiredStateConfiguration
Find-DscResource -Tag DesiredStateConfiguration, DSCResourceKit

\# Find modules using -Filter parameter
\# Specified filter value is searched in Name and Description properties
Find-Module -Filter Cookbook -Repository PSGallery
Find-Module -Filter RBAC -Repository PSGallery
```

## <a name="new-features-in-powershellget"></a>Nieuwe functies in PowerShellGet
-   Side-by-side-versie-ondersteuning in Windows PowerShell 5.0 of hoger
-   Ondersteuning voor de installatie van module afhankelijkheid
-   Drie nieuwe cmdlets
    -   Get-InstalledModule
    -   Verwijderen-Module
    -   Opslaan-Module
