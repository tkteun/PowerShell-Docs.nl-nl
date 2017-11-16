---
ms.date: 2017-06-12
author: eslesar
ms.topic: conceptual
keywords: DSC, powershell, configuratie, setup
title: Met behulp van resources met meerdere versies
ms.openlocfilehash: c3397775a6767d74c182e15d07371e830f98e9a9
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 06/12/2017
---
# <a name="using-resources-with-multiple-versions"></a><span data-ttu-id="da461-103">Met behulp van resources met meerdere versies</span><span class="sxs-lookup"><span data-stu-id="da461-103">Using resources with multiple versions</span></span>

> <span data-ttu-id="da461-104">Van toepassing op: Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="da461-104">Applies To: Windows PowerShell 5.0</span></span>

<span data-ttu-id="da461-105">In PowerShell 5.0 DSC-resources mogelijk meerdere versies en versies kunnen worden geïnstalleerd op een computer naast elkaar.</span><span class="sxs-lookup"><span data-stu-id="da461-105">In PowerShell 5.0, DSC resources can have multiple versions, and versions can be installed on a computer side-by-side.</span></span> <span data-ttu-id="da461-106">Dit wordt geïmplementeerd door meerdere versies van een resource-module die zijn opgenomen in dezelfde modulemap.</span><span class="sxs-lookup"><span data-stu-id="da461-106">This is implemented by having multiple versions of a resource module that are contained in the same module folder.</span></span>

## <a name="installing-multiple-resource-versions-side-by-side"></a><span data-ttu-id="da461-107">Installeren van meerdere resources versies side-by-side</span><span class="sxs-lookup"><span data-stu-id="da461-107">Installing multiple resource versions side-by-side</span></span>

<span data-ttu-id="da461-108">U kunt de **MinimumVersion**, **MaximumVersion**, en **RequiredVersion** parameters van de [Install-Module](https://technet.microsoft.com/en-us/library/dn807162.aspx) cmdlet om op te geven welke versie van een module te installeren.</span><span class="sxs-lookup"><span data-stu-id="da461-108">You can use the **MinimumVersion**, **MaximumVersion**, and **RequiredVersion** parameters of the [Install-Module](https://technet.microsoft.com/en-us/library/dn807162.aspx) cmdlet to specify which version of a module to install.</span></span> <span data-ttu-id="da461-109">Het aanroepen van **Install-Module** zonder op te geven met een versie installeert de meest recente versie.</span><span class="sxs-lookup"><span data-stu-id="da461-109">Calling **Install-Module** without specifying a version installs the most recent version.</span></span>

<span data-ttu-id="da461-110">Bijvoorbeeld: Er zijn meerdere versies van de **xFailOverCluster** -module, die een **xCluster** bron.</span><span class="sxs-lookup"><span data-stu-id="da461-110">For example, there are multiple versions of the **xFailOverCluster** module, each of which contains an **xCluster** resouce.</span></span> <span data-ttu-id="da461-111">Het resultaat van aanroepen **Install-Module** zonder op te geven van de versie nummer ziet er als volgt:</span><span class="sxs-lookup"><span data-stu-id="da461-111">The result of calling **Install-Module** without specifying the version number is as follows:</span></span>

```powershell
C:\Program Files\WindowsPowerShell\Modules\xFailOverCluster> Install-Module xFailOverCluster
C:\Program Files\WindowsPowerShell\Modules\xFailOverCluster> Get-DscResource xCluster

ImplementedAs   Name                      ModuleName                     Version    Properties
-------------   ----                      ----------                     -------    ----------
PowerShell      xCluster                  xFailOverCluster               1.2.0.0    {DomainAdministratorCredential, ...
```

<span data-ttu-id="da461-112">Als u nu **Install-Module** opnieuw, maar Geef een **RequiredVersion** van 1.1.0.0, resulteert dit in de volgende:</span><span class="sxs-lookup"><span data-stu-id="da461-112">Now, if you call **Install-Module** again, but specify a **RequiredVersion** of 1.1.0.0, it results in the following:</span></span>

```powershell
C:\Program Files\WindowsPowerShell\Modules\xFailOverCluster> Install-Module xFailOverCluster -RequiredVersion 1.1
C:\Program Files\WindowsPowerShell\Modules\xFailOverCluster> Get-DscResource xCluster

ImplementedAs   Name                      ModuleName                     Version    Properties
-------------   ----                      ----------                     -------    ----------
PowerShell      xCluster                  xFailOverCluster               1.1        {DomainAdministratorCredential, Name, ...
PowerShell      xCluster                  xFailOverCluster               1.2.0.0    {DomainAdministratorCredential, Name, ...
```

## <a name="specifying-a-resource-version-in-a-configuration"></a><span data-ttu-id="da461-113">Een resourceversie opgeven in een configuratie</span><span class="sxs-lookup"><span data-stu-id="da461-113">Specifying a resource version in a configuration</span></span>

<span data-ttu-id="da461-114">Als u meerdere resources die zijn geïnstalleerd op een computer hebt, moet u de versie van de bron opgeven wanneer u deze in een configuratie gebruikt.</span><span class="sxs-lookup"><span data-stu-id="da461-114">If you have multiple resources installed on a computer, you must specify the version of that resource when you use it in a configuration.</span></span> <span data-ttu-id="da461-115">U doet dit door geven de **ModuleVersion** parameter van de **importeren DscResource** sleutelwoord.</span><span class="sxs-lookup"><span data-stu-id="da461-115">You do this by specifying the **ModuleVersion** parameter of the **Import-DscResource** keyword.</span></span> <span data-ttu-id="da461-116">Als u niet de versie van een resource-module van een resource die u meer dan één versie geïnstalleerd hebt, wordt er een fout gegenereerd in de configuratie.</span><span class="sxs-lookup"><span data-stu-id="da461-116">If you fail to specify the version of a resource module of a resource of which you have more than one version installed, the configuration generates an error.</span></span>

<span data-ttu-id="da461-117">De volgende configuratie ziet u hoe de versie van de bron aan te roepen:</span><span class="sxs-lookup"><span data-stu-id="da461-117">The following configuration shows how to specify the version of the resource to call:</span></span>

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

><span data-ttu-id="da461-118">Opmerking: De parameter ModuleVersion van importeren DscResource is niet beschikbaar in PowerShell 4.0.</span><span class="sxs-lookup"><span data-stu-id="da461-118">Note: The ModuleVersion parameter of Import-DscResource is not available in PowerShell 4.0.</span></span> <span data-ttu-id="da461-119">In PowerShell 4.0, kunt u een moduleversie door een module specificatie-object doorgegeven aan de parameter ModuleName van importeren DscResource opgeven.</span><span class="sxs-lookup"><span data-stu-id="da461-119">In PowerShell 4.0, you can specify a module version by passing a module specification object to the ModuleName parameter of Import-DscResource.</span></span> <span data-ttu-id="da461-120">Een module-specificatie van het object is een hashtabel met ModuleName en RequiredVersion sleutels.</span><span class="sxs-lookup"><span data-stu-id="da461-120">A module specification object is a hash table that contains ModuleName and RequiredVersion  keys.</span></span> <span data-ttu-id="da461-121">Bijvoorbeeld:</span><span class="sxs-lookup"><span data-stu-id="da461-121">For example:</span></span>

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

<span data-ttu-id="da461-122">Dit werkt ook in PowerShell 5.0, maar het is raadzaam dat u de **ModuleVersion** parameter.</span><span class="sxs-lookup"><span data-stu-id="da461-122">This will also work in PowerShell 5.0, but it is recommended that you use the **ModuleVersion** parameter.</span></span>

## <a name="see-also"></a><span data-ttu-id="da461-123">Zie ook</span><span class="sxs-lookup"><span data-stu-id="da461-123">See also</span></span>
* [<span data-ttu-id="da461-124">DSC-configuraties</span><span class="sxs-lookup"><span data-stu-id="da461-124">DSC Configurations</span></span>](configurations.md)
* [<span data-ttu-id="da461-125">DSC-Resources</span><span class="sxs-lookup"><span data-stu-id="da461-125">DSC Resources</span></span>](resources.md)

