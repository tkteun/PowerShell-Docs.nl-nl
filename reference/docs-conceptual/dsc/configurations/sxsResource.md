---
ms.date: 06/12/2017
keywords: DSC, Power shell, configuratie, installatie
title: Een specifieke versie van een geïnstalleerde resource importeren
ms.openlocfilehash: 5ed81e11aa67eb6590d958647f48a33b1b5f1c0e
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 12/05/2019
ms.locfileid: "71941969"
---
# <a name="import-a-specific-version-of-an-installed-resource"></a><span data-ttu-id="11c48-103">Een specifieke versie van een geïnstalleerde resource importeren</span><span class="sxs-lookup"><span data-stu-id="11c48-103">Import a specific version of an installed resource</span></span>

> <span data-ttu-id="11c48-104">Van toepassing op: Windows Power shell 5,0</span><span class="sxs-lookup"><span data-stu-id="11c48-104">Applies To: Windows PowerShell 5.0</span></span>

<span data-ttu-id="11c48-105">In Power shell 5,0 kunnen afzonderlijke versies van DSC-resources worden geïnstalleerd op een computer naast elkaar.</span><span class="sxs-lookup"><span data-stu-id="11c48-105">In PowerShell 5.0, separate versions of DSC resources can be installed on a computer side by side.</span></span> <span data-ttu-id="11c48-106">Een resource module kan afzonderlijke versies van een bron opslaan in versie mappen met de naam.</span><span class="sxs-lookup"><span data-stu-id="11c48-106">A resource module can store separate versions of a resource in version named folders.</span></span>

## <a name="installing-separate-resource-versions-side-by-side"></a><span data-ttu-id="11c48-107">Afzonderlijke resource versies naast elkaar installeren</span><span class="sxs-lookup"><span data-stu-id="11c48-107">Installing separate resource versions side by side</span></span>

<span data-ttu-id="11c48-108">U kunt de para meters **MinimumVersion**, **MaximumVersion**en **RequiredVersion** van de cmdlet [install-module](/powershell/module/PowershellGet/Install-Module) gebruiken om op te geven welke versie van een module moet worden geïnstalleerd.</span><span class="sxs-lookup"><span data-stu-id="11c48-108">You can use the **MinimumVersion**, **MaximumVersion**, and **RequiredVersion** parameters of the [Install-Module](/powershell/module/PowershellGet/Install-Module) cmdlet to specify which version of a module to install.</span></span> <span data-ttu-id="11c48-109">Als u **install-module** aanroept zonder een versie op te geven, wordt de meest recente versie geïnstalleerd.</span><span class="sxs-lookup"><span data-stu-id="11c48-109">Calling **Install-Module** without specifying a version installs the most recent version.</span></span>

<span data-ttu-id="11c48-110">Er zijn bijvoorbeeld meerdere versies van de **xFailOverCluster** -module, die elk een **xCluster** -resource bevatten.</span><span class="sxs-lookup"><span data-stu-id="11c48-110">For example, there are multiple versions of the **xFailOverCluster** module, each of which contains an **xCluster** resource.</span></span> <span data-ttu-id="11c48-111">Als u **install-module** aanroept zonder het versie nummer op te geven, wordt de meest recente versie van de module geïnstalleerd.</span><span class="sxs-lookup"><span data-stu-id="11c48-111">Calling **Install-Module** without specifying the version number installs the most recent version of the module.</span></span>

```powershell
PS> Install-Module xFailOverCluster
PS> Get-DscResource xCluster
```

```output
ImplementedAs   Name                      ModuleName                     Version    Properties
-------------   ----                      ----------                     -------    ----------
PowerShell      xCluster                  xFailOverCluster               1.2.0.0    {DomainAdministratorCredential, ...
```

<span data-ttu-id="11c48-112">Als u een specifieke versie van een module wilt installeren, geeft u een **RequiredVersion** van 1.1.0.0 op.</span><span class="sxs-lookup"><span data-stu-id="11c48-112">To install a specific version of a module, specify a **RequiredVersion** of 1.1.0.0.</span></span> <span data-ttu-id="11c48-113">Hiermee wordt de opgegeven versie naast de geïnstalleerde versie geïnstalleerd.</span><span class="sxs-lookup"><span data-stu-id="11c48-113">This installs the specified version side by side with the installed version.</span></span>

```powershell
PS> Install-Module xFailOverCluster -RequiredVersion 1.1
```

<span data-ttu-id="11c48-114">Nu ziet u beide versies van de module die wordt weer gegeven wanneer u `Get-DSCResource`gebruikt.</span><span class="sxs-lookup"><span data-stu-id="11c48-114">Now, you see both version of the module listed when you use `Get-DSCResource`.</span></span>

```powershell
PS> Get-DscResource xCluster
```

```output
ImplementedAs   Name                      ModuleName                     Version    Properties
-------------   ----                      ----------                     -------    ----------
PowerShell      xCluster                  xFailOverCluster               1.1        {DomainAdministratorCredential, Name, ...
PowerShell      xCluster                  xFailOverCluster               1.2.0.0    {DomainAdministratorCredential, Name, ...
```

## <a name="specifying-a-resource-version-in-a-configuration"></a><span data-ttu-id="11c48-115">Een bron versie opgeven in een configuratie</span><span class="sxs-lookup"><span data-stu-id="11c48-115">Specifying a resource version in a configuration</span></span>

<span data-ttu-id="11c48-116">Als er afzonderlijke resource versies op een computer zijn geïnstalleerd, moet u de versie van die bron opgeven wanneer u deze in een configuratie gebruikt.</span><span class="sxs-lookup"><span data-stu-id="11c48-116">If you have separate resource versions installed on a computer, you must specify the version of that resource when you use it in a configuration.</span></span> <span data-ttu-id="11c48-117">U doet dit door de para meter **ModuleVersion** van het sleutel woord **import-dscresource bieden** op te geven.</span><span class="sxs-lookup"><span data-stu-id="11c48-117">You do this by specifying the **ModuleVersion** parameter of the **Import-DscResource** keyword.</span></span> <span data-ttu-id="11c48-118">Als u de versie van een resource module niet opgeeft van een resource waarvan u meer dan één versie hebt geïnstalleerd, genereert de configuratie een fout.</span><span class="sxs-lookup"><span data-stu-id="11c48-118">If you fail to specify the version of a resource module of a resource of which you have more than one version installed, the configuration generates an error.</span></span>

<span data-ttu-id="11c48-119">In de volgende configuratie ziet u hoe u de versie van de te kiezen resource opgeeft:</span><span class="sxs-lookup"><span data-stu-id="11c48-119">The following configuration shows how to specify the version of the resource to call:</span></span>

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

><span data-ttu-id="11c48-120">Opmerking: de para meter ModuleVersion van import-Dscresource bieden is niet beschikbaar in Power Shell 4,0.</span><span class="sxs-lookup"><span data-stu-id="11c48-120">Note: The ModuleVersion parameter of Import-DscResource is not available in PowerShell 4.0.</span></span> <span data-ttu-id="11c48-121">In Power Shell 4,0 kunt u een module versie opgeven door een module specificatie object door te geven aan de para meter module van import-Dscresource bieden.</span><span class="sxs-lookup"><span data-stu-id="11c48-121">In PowerShell 4.0, you can specify a module version by passing a module specification object to the ModuleName parameter of Import-DscResource.</span></span> <span data-ttu-id="11c48-122">Een module-specificatie object is een hash-tabel die module-en RequiredVersion-sleutels bevat.</span><span class="sxs-lookup"><span data-stu-id="11c48-122">A module specification object is a hash table that contains ModuleName and RequiredVersion  keys.</span></span> <span data-ttu-id="11c48-123">Bijvoorbeeld:</span><span class="sxs-lookup"><span data-stu-id="11c48-123">For example:</span></span>

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

<span data-ttu-id="11c48-124">Dit werkt ook in Power shell 5,0, maar u wordt aangeraden de para meter **ModuleVersion** te gebruiken.</span><span class="sxs-lookup"><span data-stu-id="11c48-124">This will also work in PowerShell 5.0, but it is recommended that you use the **ModuleVersion** parameter.</span></span>

## <a name="see-also"></a><span data-ttu-id="11c48-125">Zie ook</span><span class="sxs-lookup"><span data-stu-id="11c48-125">See also</span></span>

- [<span data-ttu-id="11c48-126">DSC-configuraties</span><span class="sxs-lookup"><span data-stu-id="11c48-126">DSC Configurations</span></span>](configurations.md)
- [<span data-ttu-id="11c48-127">DSC-resources</span><span class="sxs-lookup"><span data-stu-id="11c48-127">DSC Resources</span></span>](../resources/resources.md)
