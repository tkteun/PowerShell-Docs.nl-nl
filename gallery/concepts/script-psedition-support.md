---
ms.date: 06/12/2017
contributor: manikb
keywords: Galerie, powershell, cmdlet, psget
title: Script met compatibele PowerShell-edities
ms.openlocfilehash: 386e65295641fb6932c13047246742531aeaec64
ms.sourcegitcommit: 77f62a55cac8c13d69d51eef5fade18f71d66955
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/17/2018
ms.locfileid: "39093657"
---
# <a name="script-with-compatible-powershell-editions"></a>Script met compatibele PowerShell-edities

Vanaf versie 5.1 is PowerShell beschikbaar in verschillende edities die staan voor verschillende functies en platformcompatibiliteit.

- **Desktop-editie:** deze editie is gebaseerd op .NET Framework en biedt compatibiliteit met scripts en modules die zijn gericht op versies van PowerShell die worden uitgevoerd op edities van Windows met een volledige footprint zoals Server Core en Windows Desktop.
- **Core-editie:** deze editie is gebaseerd op .NET Framework en biedt compatibiliteit met scripts en modules die zijn gericht op versies van PowerShell die worden uitgevoerd op edities van Windows met een verminderde footprint zoals Nano Server en Windows IoT.

De actieve editie van PowerShell wordt weergegeven in de eigenschap PSEdition van $PSVersionTable.

```powershell
$PSVersionTable

Name                           Value
----                           -----
PSVersion                      5.1.14300.1000
PSEdition                      Desktop
PSCompatibleVersions           {1.0, 2.0, 3.0, 4.0...}
CLRVersion                     4.0.30319.42000
BuildVersion                   10.0.14300.1000
WSManStackVersion              3.0
PSRemotingProtocolVersion      2.3
SerializationVersion           1.1.0.1
```

Auteurs van scripts kunnen met de parameter PSEdition in een #requires-instructie verhinderen dat een script wordt uitgevoerd, tenzij het wordt uitgevoerd op een compatibele versie van PowerShell.

```powershell
Set-Content C:\script.ps1 -Value "#requires -PSEdition Core
Get-Process -Name PowerShell"
Get-Content C:\script.ps1
#requires -PSEdition Core
Get-Process -Name PowerShell

C:\script.ps1
C:\script.ps1 : The script 'script.ps1' cannot be run because it contained a "#requires" statement for PowerShell Core edition. The edition of PowerShell that is required by the script does not match the currently running PowerShell Desktop edition.
At line:1 char:1
+ C:\script.ps1
+ ~~~~~~~~~~~~~
    + CategoryInfo          : NotSpecified: (script.ps1:String) [], RuntimeException
    + FullyQualifiedErrorId : ScriptRequiresUnmatchedPSEdition
```

Gebruikers van de PowerShell Gallery vindt de lijst met scripts die worden ondersteund op een specifieke editie van PowerShell.
Scripts zonder PSEdition_Desktop en PSEditon_Core worden beschouwd als goed werken op het bureaublad van de PowerShell-edities.

```powershell
# Find scripts supported on PowerShell Desktop edition
Find-Script -Tag PSEditon_Desktop

# Find scripts supported on PowerShell Core editions
Find-Script -Tag PSEditon_Core
```

## <a name="more-details"></a>Meer informatie

- [Modules met PSEditions](module-psedition-support.md)
- [Ondersteuning op PowerShellGallery PSEditions](../how-to/finding-items/searching-by-psedition.md)