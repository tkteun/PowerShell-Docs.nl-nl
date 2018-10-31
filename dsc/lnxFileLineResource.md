---
ms.date: 06/12/2017
keywords: DSC, powershell, configuratie en installatie
title: DSC voor Linux nxFileLine-Resource
ms.openlocfilehash: 6a91db25638b09659adfabcec78f91bcb2e69dd9
ms.sourcegitcommit: e76665315fd928bf85210778f1fea2be15264fea
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/30/2018
ms.locfileid: "50225587"
---
# <a name="dsc-for-linux-nxfileline-resource"></a><span data-ttu-id="20778-103">DSC voor Linux nxFileLine-Resource</span><span class="sxs-lookup"><span data-stu-id="20778-103">DSC for Linux nxFileLine Resource</span></span>

<span data-ttu-id="20778-104">De **nxFileLine** resource in PowerShell Desired State Configuration (DSC) biedt een mechanisme voor het beheren van de regels in een configuratiebestand op een Linux-knooppunt.</span><span class="sxs-lookup"><span data-stu-id="20778-104">The **nxFileLine** resource in PowerShell Desired State Configuration (DSC) provides a mechanism to manage lines within a configuration file on a Linux node.</span></span>

## <a name="syntax"></a><span data-ttu-id="20778-105">Syntaxis</span><span class="sxs-lookup"><span data-stu-id="20778-105">Syntax</span></span>

```
nxFileLine <string> #ResourceName
{
    FilePath = <string>
    ContainsLine = <string>
    [ DoesNotContainPattern = <string> ]
    [ DependsOn = <string[]> ]

}
```

## <a name="properties"></a><span data-ttu-id="20778-106">Eigenschappen</span><span class="sxs-lookup"><span data-stu-id="20778-106">Properties</span></span>

|  <span data-ttu-id="20778-107">Eigenschap</span><span class="sxs-lookup"><span data-stu-id="20778-107">Property</span></span> |  <span data-ttu-id="20778-108">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="20778-108">Description</span></span> |
|---|---|
| <span data-ttu-id="20778-109">FilePath</span><span class="sxs-lookup"><span data-stu-id="20778-109">FilePath</span></span>| <span data-ttu-id="20778-110">Het volledige pad naar het bestand om regels in op het doelknooppunt te beheren.</span><span class="sxs-lookup"><span data-stu-id="20778-110">The full path to the file to manage lines in on the target node.</span></span>|
| <span data-ttu-id="20778-111">ContainsLine</span><span class="sxs-lookup"><span data-stu-id="20778-111">ContainsLine</span></span>| <span data-ttu-id="20778-112">Een regel om ervoor te zorgen bestaat in het bestand.</span><span class="sxs-lookup"><span data-stu-id="20778-112">A line to ensure exists in the file.</span></span> <span data-ttu-id="20778-113">Deze regel wordt toegevoegd aan het bestand als deze niet in het bestand bestaat.</span><span class="sxs-lookup"><span data-stu-id="20778-113">This line will be appended to the file if it does not exist in the file.</span></span> <span data-ttu-id="20778-114">**ContainsLine** is verplicht, maar kan worden ingesteld op een lege tekenreeks (`ContainsLine = ""`) als deze niet nodig is.</span><span class="sxs-lookup"><span data-stu-id="20778-114">**ContainsLine** is mandatory, but can be set to an empty string (`ContainsLine = ""`) if it is not needed.</span></span>|
| <span data-ttu-id="20778-115">DoesNotContainPattern</span><span class="sxs-lookup"><span data-stu-id="20778-115">DoesNotContainPattern</span></span>| <span data-ttu-id="20778-116">Een reguliere-expressiepatroon voor regels die niet in het bestand moet bestaan.</span><span class="sxs-lookup"><span data-stu-id="20778-116">A regular expression pattern for lines that should not exist in the file.</span></span> <span data-ttu-id="20778-117">Voor alle regels die zijn opgenomen in het bestand die overeenkomen met deze reguliere expressie, wordt de regel wordt verwijderd uit het bestand.</span><span class="sxs-lookup"><span data-stu-id="20778-117">For any lines that exist in the file that match this regular expression, the line will be removed from the file.</span></span>|
| <span data-ttu-id="20778-118">DependsOn</span><span class="sxs-lookup"><span data-stu-id="20778-118">DependsOn</span></span> | <span data-ttu-id="20778-119">Geeft aan dat de configuratie van een andere resource uitvoeren moet voordat deze resource is geconfigureerd.</span><span class="sxs-lookup"><span data-stu-id="20778-119">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="20778-120">Bijvoorbeeld, als de **ID** van de resource is scriptblok configuratie die u wilt uitvoeren eerst **ResourceName** en het type **ResourceType**, de syntaxis voor het gebruik van dit de eigenschap is `DependsOn = "[ResourceType]ResourceName"`.</span><span class="sxs-lookup"><span data-stu-id="20778-120">For example, if the **ID** of the resource configuration script block that you want to run first is **ResourceName** and its type is **ResourceType**, the syntax for using this property is `DependsOn = "[ResourceType]ResourceName"`.</span></span>|

## <a name="example"></a><span data-ttu-id="20778-121">Voorbeeld</span><span class="sxs-lookup"><span data-stu-id="20778-121">Example</span></span>

<span data-ttu-id="20778-122">In dit voorbeeld wordt met behulp van de **nxFileLine** resource die u wilt configureren van de `/etc/sudoers` -bestand, ervoor zorgen dat de gebruiker: monuser is geconfigureerd voor het niet requiretty.</span><span class="sxs-lookup"><span data-stu-id="20778-122">This example demonstrates using the **nxFileLine** resource to configure the `/etc/sudoers` file, ensuring that the user: monuser is configured to not requiretty.</span></span>

```powershell
Import-DscResource -Module nx

nxFileLine DoNotRequireTTY
{
   FilePath = “/etc/sudoers”
   ContainsLine = 'Defaults:monuser !requiretty'
   DoesNotContainPattern = "Defaults:monuser[ ]+requiretty"
}
```