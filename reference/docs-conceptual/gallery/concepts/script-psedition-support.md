---
ms.date: 06/12/2017
contributor: manikb
keywords: Galerie, Power shell, cmdlet, psget
title: Script met compatibele Power shell-edities
ms.openlocfilehash: e364879f611429a8583e550fb7704431e456fbb1
ms.sourcegitcommit: 6545c60578f7745be015111052fd7769f8289296
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 04/22/2020
ms.locfileid: "71328880"
---
# <a name="script-with-compatible-powershell-editions"></a><span data-ttu-id="28006-103">Script met compatibele Power shell-edities</span><span class="sxs-lookup"><span data-stu-id="28006-103">Script with compatible PowerShell editions</span></span>

<span data-ttu-id="28006-104">Vanaf versie 5.1 is PowerShell beschikbaar in verschillende edities die staan voor verschillende functies en platformcompatibiliteit.</span><span class="sxs-lookup"><span data-stu-id="28006-104">Starting with version 5.1, PowerShell is available in different editions which denote varying feature sets and platform compatibility.</span></span>

- <span data-ttu-id="28006-105">**Desktop-editie:** deze editie is gebaseerd op .NET Framework en biedt compatibiliteit met scripts en modules die zijn gericht op versies van PowerShell die worden uitgevoerd op edities van Windows met een volledige footprint zoals Server Core en Windows Desktop.</span><span class="sxs-lookup"><span data-stu-id="28006-105">**Desktop Edition:** Built on .NET Framework and provides compatibility with scripts and modules targeting versions of PowerShell running on full footprint editions of Windows such as Server Core and Windows Desktop.</span></span>

- <span data-ttu-id="28006-106">**Core-editie:** deze editie is gebaseerd op .NET Framework en biedt compatibiliteit met scripts en modules die zijn gericht op versies van PowerShell die worden uitgevoerd op edities van Windows met een verminderde footprint zoals Nano Server en Windows IoT.</span><span class="sxs-lookup"><span data-stu-id="28006-106">**Core Edition:** Built on .NET Core and provides compatibility with scripts and modules targeting versions of PowerShell running on reduced footprint editions of Windows such as Nano Server and Windows IoT.</span></span>

<span data-ttu-id="28006-107">De actieve editie van PowerShell wordt weergegeven in de eigenschap PSEdition van $PSVersionTable.</span><span class="sxs-lookup"><span data-stu-id="28006-107">The running edition of PowerShell is shown in the PSEdition property of $PSVersionTable.</span></span>

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

<span data-ttu-id="28006-108">Auteurs van het script kunnen voor komen dat een script wordt uitgevoerd, tenzij dit wordt uitgevoerd op een compatibele editie van Power shell met `#requires` behulp van de para meter PSEdition in een-instructie.</span><span class="sxs-lookup"><span data-stu-id="28006-108">Script authors can prevent a script from executing unless it is run on a compatible edition of PowerShell using the PSEdition parameter on a `#requires` statement.</span></span>

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

<span data-ttu-id="28006-109">PowerShell Gallery kunnen gebruikers de lijst met scripts vinden die worden ondersteund op een specifieke Power shell-editie.</span><span class="sxs-lookup"><span data-stu-id="28006-109">PowerShell Gallery users can find the list of scripts supported on a specific PowerShell Edition.</span></span>
<span data-ttu-id="28006-110">Scripts zonder PSEdition_Desktop-en PSEdition_Core-Tags worden beschouwd als goed op Power shell Desktop Edition.</span><span class="sxs-lookup"><span data-stu-id="28006-110">Scripts without PSEdition_Desktop and PSEdition_Core tags are considered to work fine on PowerShell Desktop edition.</span></span>

```powershell
# Find scripts supported on PowerShell Desktop edition
Find-Script -Tag PSEdition_Desktop

# Find scripts supported on PowerShell Core edition
Find-Script -Tag PSEdition_Core
```

## <a name="more-details"></a><span data-ttu-id="28006-111">Meer informatie</span><span class="sxs-lookup"><span data-stu-id="28006-111">More details</span></span>

- [<span data-ttu-id="28006-112">Modules met PSEditions</span><span class="sxs-lookup"><span data-stu-id="28006-112">Modules with PSEditions</span></span>](module-psedition-support.md)
- [<span data-ttu-id="28006-113">PSEditions-ondersteuning op PowerShellGallery</span><span class="sxs-lookup"><span data-stu-id="28006-113">PSEditions support on PowerShellGallery</span></span>](../how-to/finding-packages/searching-by-compatibility.md)
