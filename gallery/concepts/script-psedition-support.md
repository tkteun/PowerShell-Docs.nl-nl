---
ms.date: 06/12/2017
contributor: manikb
keywords: Galerie, powershell, cmdlet, psget
title: Script met compatibele PowerShell-edities
ms.openlocfilehash: e364879f611429a8583e550fb7704431e456fbb1
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62084688"
---
# <a name="script-with-compatible-powershell-editions"></a>Script met compatibele PowerShell-edities

Vanaf versie 5.1 is PowerShell beschikbaar in verschillende edities die staan voor verschillende functies en platformcompatibiliteit.

- **Desktop-editie:** Gebaseerd op .NET Framework en biedt compatibiliteit met scripts en modules die zijn gericht op versies van PowerShell die worden uitgevoerd op edities van Windows, zoals Server Core- en Windows Desktop volledige footprint.

- **Core-editie:** Gebaseerd op .NET Core en biedt compatibiliteit met scripts en modules die zijn gericht op versies van PowerShell die worden uitgevoerd op edities van Windows, zoals Nano Server en Windows IoT verminderde footprint.

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

Auteurs van scripts kunnen voorkomen dat er een script uitgevoerd, tenzij deze wordt uitgevoerd op een compatibele versie van PowerShell met de parameter PSEdition in een `#requires` instructie.

```powershell
Set-Content C:\script.ps1 -Value "#requires -PSEdition Core
Get-Process -Name PowerShell"
Get-Content C:\script.ps1
#requires -PSEdition Core
Get-Process -Name PowerShell

C:\script.ps1
C:\script.ps1 : The script 'script.ps1' cannot be run because it contained a "#requires" statement for PowerShell editions 'Core'. The edition of PowerShell that is required by the script does not match the currently running PowerShell Desktop edition.
At line:1 char:1
+ C:\script.ps1
+ ~~~~~~~~~~~~~
    + CategoryInfo          : NotSpecified: (script.ps1:String) [], RuntimeException
    + FullyQualifiedErrorId : ScriptRequiresUnmatchedPSEdition
```

Gebruikers van de PowerShell Gallery vindt de lijst met scripts die worden ondersteund op een specifieke editie van PowerShell.
Scripts zonder PSEdition_Desktop en PSEdition_Core tags worden beschouwd als goed werken in PowerShell-Desktop-editie.

```powershell
# Find scripts supported on PowerShell Desktop edition
Find-Script -Tag PSEdition_Desktop

# Find scripts supported on PowerShell Core edition
Find-Script -Tag PSEdition_Core
```

## <a name="more-details"></a>Meer informatie

- [Modules met PSEditions](module-psedition-support.md)
- [Ondersteuning op PowerShellGallery PSEditions](../how-to/finding-packages/searching-by-compatibility.md)
