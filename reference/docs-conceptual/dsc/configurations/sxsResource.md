---
ms.date: 06/12/2017
keywords: DSC, Power shell, configuratie, installatie
title: Een specifieke versie van een geïnstalleerde resource importeren
description: In dit artikel wordt beschreven hoe u specifieke versies van resource modules kunt installeren en importeren in uw configuraties.
ms.openlocfilehash: bb7b3273a5a3fed94fecd90dd3ea1e623fbc332b
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/27/2020
ms.locfileid: "92645051"
---
# <a name="import-a-specific-version-of-an-installed-resource"></a><span data-ttu-id="9056a-104">Een specifieke versie van een geïnstalleerde resource importeren</span><span class="sxs-lookup"><span data-stu-id="9056a-104">Import a specific version of an installed resource</span></span>

> <span data-ttu-id="9056a-105">Van toepassing op: Windows Power shell 5,0</span><span class="sxs-lookup"><span data-stu-id="9056a-105">Applies To: Windows PowerShell 5.0</span></span>

<span data-ttu-id="9056a-106">In Power shell 5,0 kunnen afzonderlijke versies van DSC-resources worden geïnstalleerd op een computer naast elkaar.</span><span class="sxs-lookup"><span data-stu-id="9056a-106">In PowerShell 5.0, separate versions of DSC resources can be installed on a computer side by side.</span></span> <span data-ttu-id="9056a-107">Een resource module kan afzonderlijke versies van een bron opslaan in versie mappen met de naam.</span><span class="sxs-lookup"><span data-stu-id="9056a-107">A resource module can store separate versions of a resource in version named folders.</span></span>

## <a name="installing-separate-resource-versions-side-by-side"></a><span data-ttu-id="9056a-108">Afzonderlijke resource versies naast elkaar installeren</span><span class="sxs-lookup"><span data-stu-id="9056a-108">Installing separate resource versions side by side</span></span>

<span data-ttu-id="9056a-109">U kunt de para meters **MinimumVersion** , **MaximumVersion** en **RequiredVersion** van de cmdlet [install-module](/powershell/module/PowershellGet/Install-Module) gebruiken om op te geven welke versie van een module moet worden geïnstalleerd.</span><span class="sxs-lookup"><span data-stu-id="9056a-109">You can use the **MinimumVersion** , **MaximumVersion** , and **RequiredVersion** parameters of the [Install-Module](/powershell/module/PowershellGet/Install-Module) cmdlet to specify which version of a module to install.</span></span> <span data-ttu-id="9056a-110">Als u **install-module** aanroept zonder een versie op te geven, wordt de meest recente versie geïnstalleerd.</span><span class="sxs-lookup"><span data-stu-id="9056a-110">Calling **Install-Module** without specifying a version installs the most recent version.</span></span>

<span data-ttu-id="9056a-111">Er zijn bijvoorbeeld meerdere versies van de **xFailOverCluster** -module, die elk een **xCluster** -resource bevatten.</span><span class="sxs-lookup"><span data-stu-id="9056a-111">For example, there are multiple versions of the **xFailOverCluster** module, each of which contains an **xCluster** resource.</span></span> <span data-ttu-id="9056a-112">Als u **install-module** aanroept zonder het versie nummer op te geven, wordt de meest recente versie van de module geïnstalleerd.</span><span class="sxs-lookup"><span data-stu-id="9056a-112">Calling **Install-Module** without specifying the version number installs the most recent version of the module.</span></span>

```powershell
PS> Install-Module xFailOverCluster
PS> Get-DscResource xCluster
```

```Output
ImplementedAs   Name          ModuleName           Version    Properties
-------------   ----          ----------           -------    ----------
PowerShell      xCluster      xFailOverCluster     1.2.0.0    {DomainAdministratorCredential, ...
```

<span data-ttu-id="9056a-113">Als u een specifieke versie van een module wilt installeren, geeft u een **RequiredVersion** van 1.1.0.0 op.</span><span class="sxs-lookup"><span data-stu-id="9056a-113">To install a specific version of a module, specify a **RequiredVersion** of 1.1.0.0.</span></span> <span data-ttu-id="9056a-114">Hiermee wordt de opgegeven versie naast de geïnstalleerde versie geïnstalleerd.</span><span class="sxs-lookup"><span data-stu-id="9056a-114">This installs the specified version side by side with the installed version.</span></span>

```powershell
PS> Install-Module xFailOverCluster -RequiredVersion 1.1
```

<span data-ttu-id="9056a-115">Nu ziet u beide versies van de module die wordt weer gegeven wanneer u gebruikt `Get-DSCResource` .</span><span class="sxs-lookup"><span data-stu-id="9056a-115">Now, you see both version of the module listed when you use `Get-DSCResource`.</span></span>

```powershell
PS> Get-DscResource xCluster
```

```Output
ImplementedAs   Name          ModuleName            Version    Properties
-------------   ----          ----------            -------    ----------
PowerShell      xCluster      xFailOverCluster      1.1        {DomainAdministratorCredential, Name, ...
PowerShell      xCluster      xFailOverCluster      1.2.0.0    {DomainAdministratorCredential, Name, ...
```

## <a name="specifying-a-resource-version-in-a-configuration"></a><span data-ttu-id="9056a-116">Een bron versie opgeven in een configuratie</span><span class="sxs-lookup"><span data-stu-id="9056a-116">Specifying a resource version in a configuration</span></span>

<span data-ttu-id="9056a-117">Als er afzonderlijke resource versies op een computer zijn geïnstalleerd, moet u de versie van die bron opgeven wanneer u deze in een configuratie gebruikt.</span><span class="sxs-lookup"><span data-stu-id="9056a-117">If you have separate resource versions installed on a computer, you must specify the version of that resource when you use it in a configuration.</span></span> <span data-ttu-id="9056a-118">U doet dit door de para meter **ModuleVersion** van het sleutel woord **import-dscresource bieden** op te geven.</span><span class="sxs-lookup"><span data-stu-id="9056a-118">You do this by specifying the **ModuleVersion** parameter of the **Import-DscResource** keyword.</span></span> <span data-ttu-id="9056a-119">Als u de versie van een resource module niet opgeeft van een resource waarvan u meer dan één versie hebt geïnstalleerd, genereert de configuratie een fout.</span><span class="sxs-lookup"><span data-stu-id="9056a-119">If you fail to specify the version of a resource module of a resource of which you have more than one version installed, the configuration generates an error.</span></span>

<span data-ttu-id="9056a-120">In de volgende configuratie ziet u hoe u de versie van de te kiezen resource opgeeft:</span><span class="sxs-lookup"><span data-stu-id="9056a-120">The following configuration shows how to specify the version of the resource to call:</span></span>

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

<span data-ttu-id="9056a-121">De ModuleVersion-para meter van Import-DscResource is niet beschikbaar in Power Shell 4,0.</span><span class="sxs-lookup"><span data-stu-id="9056a-121">The ModuleVersion parameter of Import-DscResource is not available in PowerShell 4.0.</span></span> <span data-ttu-id="9056a-122">In Power Shell 4,0 kunt u een module versie opgeven door een module specificatie object door te geven aan de para meter module van import-Dscresource bieden.</span><span class="sxs-lookup"><span data-stu-id="9056a-122">In PowerShell 4.0, you can specify a module version by passing a module specification object to the ModuleName parameter of Import-DscResource.</span></span> <span data-ttu-id="9056a-123">Een module-specificatie object is een hash-tabel die module-en RequiredVersion-sleutels bevat.</span><span class="sxs-lookup"><span data-stu-id="9056a-123">A module specification object is a hash table that contains ModuleName and RequiredVersion keys.</span></span> <span data-ttu-id="9056a-124">Bijvoorbeeld:</span><span class="sxs-lookup"><span data-stu-id="9056a-124">For example:</span></span>

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

<span data-ttu-id="9056a-125">Dit werkt ook in Power shell 5,0, maar u wordt aangeraden de para meter **ModuleVersion** te gebruiken.</span><span class="sxs-lookup"><span data-stu-id="9056a-125">This will also work in PowerShell 5.0, but it is recommended that you use the **ModuleVersion** parameter.</span></span>

## <a name="see-also"></a><span data-ttu-id="9056a-126">Zie ook</span><span class="sxs-lookup"><span data-stu-id="9056a-126">See also</span></span>

- [<span data-ttu-id="9056a-127">DSC-configuraties</span><span class="sxs-lookup"><span data-stu-id="9056a-127">DSC Configurations</span></span>](configurations.md)
- [<span data-ttu-id="9056a-128">DSC-resources</span><span class="sxs-lookup"><span data-stu-id="9056a-128">DSC Resources</span></span>](../resources/resources.md)
