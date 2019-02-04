---
ms.date: 06/12/2017
keywords: DSC, powershell, configuratie en installatie
title: Een specifieke versie van een geïnstalleerde resource importeren
ms.openlocfilehash: 5ed81e11aa67eb6590d958647f48a33b1b5f1c0e
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 02/03/2019
ms.locfileid: "55683882"
---
# <a name="import-a-specific-version-of-an-installed-resource"></a><span data-ttu-id="fac33-103">Een specifieke versie van een geïnstalleerde resource importeren</span><span class="sxs-lookup"><span data-stu-id="fac33-103">Import a specific version of an installed resource</span></span>

> <span data-ttu-id="fac33-104">Van toepassing op: Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="fac33-104">Applies To: Windows PowerShell 5.0</span></span>

<span data-ttu-id="fac33-105">In PowerShell 5.0, kunnen verschillende versies van DSC-resources worden geïnstalleerd op een computer naast elkaar.</span><span class="sxs-lookup"><span data-stu-id="fac33-105">In PowerShell 5.0, separate versions of DSC resources can be installed on a computer side by side.</span></span> <span data-ttu-id="fac33-106">Een resource-module kunt u verschillende versies van een resource opslaan in versie met de naam van mappen.</span><span class="sxs-lookup"><span data-stu-id="fac33-106">A resource module can store separate versions of a resource in version named folders.</span></span>

## <a name="installing-separate-resource-versions-side-by-side"></a><span data-ttu-id="fac33-107">Afzonderlijke resource versies naast elkaar installeren</span><span class="sxs-lookup"><span data-stu-id="fac33-107">Installing separate resource versions side by side</span></span>

<span data-ttu-id="fac33-108">U kunt de **MinimumVersion**, **MaximumVersion**, en **RequiredVersion** parameters van de [Install-Module](/powershell/module/PowershellGet/Install-Module) cmdlet om op te geven welke versie van een module te installeren.</span><span class="sxs-lookup"><span data-stu-id="fac33-108">You can use the **MinimumVersion**, **MaximumVersion**, and **RequiredVersion** parameters of the [Install-Module](/powershell/module/PowershellGet/Install-Module) cmdlet to specify which version of a module to install.</span></span> <span data-ttu-id="fac33-109">Aanroepen van **Install-Module** zonder op te geven een versie installeert de meest recente versie.</span><span class="sxs-lookup"><span data-stu-id="fac33-109">Calling **Install-Module** without specifying a version installs the most recent version.</span></span>

<span data-ttu-id="fac33-110">Bijvoorbeeld, er zijn meerdere versies van de **xFailOverCluster** -module, die elk bevat een **xCluster** resource.</span><span class="sxs-lookup"><span data-stu-id="fac33-110">For example, there are multiple versions of the **xFailOverCluster** module, each of which contains an **xCluster** resource.</span></span> <span data-ttu-id="fac33-111">Aanroepen van **Install-Module** zonder de versie op te geven aantal installeert de meest recente versie van de module.</span><span class="sxs-lookup"><span data-stu-id="fac33-111">Calling **Install-Module** without specifying the version number installs the most recent version of the module.</span></span>

```powershell
PS> Install-Module xFailOverCluster
PS> Get-DscResource xCluster
```

```output
ImplementedAs   Name                      ModuleName                     Version    Properties
-------------   ----                      ----------                     -------    ----------
PowerShell      xCluster                  xFailOverCluster               1.2.0.0    {DomainAdministratorCredential, ...
```

<span data-ttu-id="fac33-112">Geef voor het installeren van een specifieke versie van een module, een **RequiredVersion** van 1.1.0.0.</span><span class="sxs-lookup"><span data-stu-id="fac33-112">To install a specific version of a module, specify a **RequiredVersion** of 1.1.0.0.</span></span> <span data-ttu-id="fac33-113">Hiermee installeert u de opgegeven versie naast de geïnstalleerde versie.</span><span class="sxs-lookup"><span data-stu-id="fac33-113">This installs the specified version side by side with the installed version.</span></span>

```powershell
PS> Install-Module xFailOverCluster -RequiredVersion 1.1
```

<span data-ttu-id="fac33-114">U ziet nu zowel versie van de module weergegeven wanneer u `Get-DSCResource`.</span><span class="sxs-lookup"><span data-stu-id="fac33-114">Now, you see both version of the module listed when you use `Get-DSCResource`.</span></span>

```powershell
PS> Get-DscResource xCluster
```

```output
ImplementedAs   Name                      ModuleName                     Version    Properties
-------------   ----                      ----------                     -------    ----------
PowerShell      xCluster                  xFailOverCluster               1.1        {DomainAdministratorCredential, Name, ...
PowerShell      xCluster                  xFailOverCluster               1.2.0.0    {DomainAdministratorCredential, Name, ...
```

## <a name="specifying-a-resource-version-in-a-configuration"></a><span data-ttu-id="fac33-115">Een resourceversie opgeven in een configuratie</span><span class="sxs-lookup"><span data-stu-id="fac33-115">Specifying a resource version in a configuration</span></span>

<span data-ttu-id="fac33-116">Als u afzonderlijke resource-versies die zijn geïnstalleerd op een computer hebt, moet u de versie van die resource opgeven wanneer u deze in een configuratie gebruikt.</span><span class="sxs-lookup"><span data-stu-id="fac33-116">If you have separate resource versions installed on a computer, you must specify the version of that resource when you use it in a configuration.</span></span> <span data-ttu-id="fac33-117">U dit doen door op te geven de **ModuleVersion** parameter van de **sleutelwoorden Import-dscresource bieden** trefwoord.</span><span class="sxs-lookup"><span data-stu-id="fac33-117">You do this by specifying the **ModuleVersion** parameter of the **Import-DscResource** keyword.</span></span> <span data-ttu-id="fac33-118">Als u niet om op te geven van de versie van een resource-module van een resource die u meer dan één versie geïnstalleerd hebt, wordt er een fout gegenereerd in de configuratie.</span><span class="sxs-lookup"><span data-stu-id="fac33-118">If you fail to specify the version of a resource module of a resource of which you have more than one version installed, the configuration generates an error.</span></span>

<span data-ttu-id="fac33-119">De volgende configuratie laat zien hoe om op te geven van de versie van de resource om aan te roepen:</span><span class="sxs-lookup"><span data-stu-id="fac33-119">The following configuration shows how to specify the version of the resource to call:</span></span>

```powershell
configuration VersionTest
{
    Import-DscResource -ModuleName xFailOverCluster -ModuleVersion 1.1

    Node 'localhost'
    {
       xCluster ClusterTest
       {
            Name                          = 'TestCluster'
            StaticIPAddress               = '10.0.0.3'
            DomainAdministratorCredential = Get-Credential
        }
     }
}
```

><span data-ttu-id="fac33-120">Opmerking: De parameter ModuleVersion van sleutelwoorden Import-dscresource bieden is niet beschikbaar in PowerShell 4.0.</span><span class="sxs-lookup"><span data-stu-id="fac33-120">Note: The ModuleVersion parameter of Import-DscResource is not available in PowerShell 4.0.</span></span> <span data-ttu-id="fac33-121">In PowerShell 4.0, kunt u de versie van een module door een module-specificatie-object doorgeven aan de parameter ModuleName van sleutelwoorden Import-dscresource bieden.</span><span class="sxs-lookup"><span data-stu-id="fac33-121">In PowerShell 4.0, you can specify a module version by passing a module specification object to the ModuleName parameter of Import-DscResource.</span></span> <span data-ttu-id="fac33-122">Een module-specificatie-object is een hashtabel met sleutels ModuleName en requiredversion aan.</span><span class="sxs-lookup"><span data-stu-id="fac33-122">A module specification object is a hash table that contains ModuleName and RequiredVersion  keys.</span></span> <span data-ttu-id="fac33-123">Bijvoorbeeld:</span><span class="sxs-lookup"><span data-stu-id="fac33-123">For example:</span></span>

```powershell
configuration VersionTest
{
    Import-DscResource -ModuleName (@{ModuleName='xFailOverCluster'; RequiredVersion='1.1'} )

    Node 'localhost'
    {
       xCluster ClusterTest
       {
            Name                          = 'TestCluster'
            StaticIPAddress               = '10.0.0.3'
            DomainAdministratorCredential = Get-Credential
        }
     }
}
```

<span data-ttu-id="fac33-124">Dit werkt ook in PowerShell 5.0, maar het is raadzaam dat u de **ModuleVersion** parameter.</span><span class="sxs-lookup"><span data-stu-id="fac33-124">This will also work in PowerShell 5.0, but it is recommended that you use the **ModuleVersion** parameter.</span></span>

## <a name="see-also"></a><span data-ttu-id="fac33-125">Zie ook</span><span class="sxs-lookup"><span data-stu-id="fac33-125">See also</span></span>

- [<span data-ttu-id="fac33-126">DSC-configuraties</span><span class="sxs-lookup"><span data-stu-id="fac33-126">DSC Configurations</span></span>](configurations.md)
- [<span data-ttu-id="fac33-127">DSC-Resources</span><span class="sxs-lookup"><span data-stu-id="fac33-127">DSC Resources</span></span>](../resources/resources.md)
