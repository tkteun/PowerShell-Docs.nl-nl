---
ms.date: 06/12/2017
keywords: wmf,powershell,installeren
ms.openlocfilehash: a0b1573611c5d4232082c19ca19b4cca79d0699e
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 02/03/2019
ms.locfileid: "55685254"
---
# <a name="powershell-module-discovery-install-and-inventory-with-powershellget"></a>PowerShell-Module detecteren, installeren en inventariseren van scripts met PowerShellGet

PowerShellGet is opgenomen in deze versie van WMF:
-   Find-Module kunt filteren op de metagegevens van de module met de - parameter Tag
-   Find-Module kunt filteren op zoektaal van de opslagplaats-specifieke met de parameter - Filter
-   Find-Module kan filteren op basis van de module met de opdracht-, - sleutelwoorden dscresource bieden, inhoud en - parameters bevat
-   Zoeken naar sleutelwoorden-dscresource bieden kunt detectie van afzonderlijke DSC-resources in opslagplaatsen
-   Ondersteuning voor het installeren van en publiceren naar bestandsshares met NuGet

## <a name="example-commands"></a>Van de voorbeeldopdrachten
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
-   Ondersteuning voor de side-by-side-versie van Windows PowerShell 5.0 of hoger
-   Ondersteuning voor de installatie van module afhankelijkheid
-   Drie nieuwe cmdlets
    -   Get-InstalledModule
    -   Verwijderen-Module
    -   Save-Module
