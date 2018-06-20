---
ms.date: 06/12/2017
keywords: DSC, powershell, configuratie, setup
title: DSC voor Linux nxFileLine Resource
ms.openlocfilehash: 6b927839c23478aa9916a5d23836b31fccc58484
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 05/17/2018
ms.locfileid: "34219630"
---
# <a name="dsc-for-linux-nxfileline-resource"></a><span data-ttu-id="3b179-103">DSC voor Linux nxFileLine Resource</span><span class="sxs-lookup"><span data-stu-id="3b179-103">DSC for Linux nxFileLine Resource</span></span>

<span data-ttu-id="3b179-104">De **nxFileLine** in PowerShell Desired State Configuration (DSC)-bron biedt een mechanisme op voor het beheren van de regels in een configuratiebestand op een Linux-knooppunt.</span><span class="sxs-lookup"><span data-stu-id="3b179-104">The **nxFileLine** resource in PowerShell Desired State Configuration (DSC) provides a mechanism to to manage lines within a configuration file on a Linux node.</span></span>

## <a name="syntax"></a><span data-ttu-id="3b179-105">Syntaxis</span><span class="sxs-lookup"><span data-stu-id="3b179-105">Syntax</span></span>

```
nxFileLine <string> #ResourceName
{
    FilePath = <string>
    ContainsLine = <string>
    [ DoesNotContainPattern = <string> ]
    [ DependsOn = <string[]> ]

}
```

## <a name="properties"></a><span data-ttu-id="3b179-106">Eigenschappen</span><span class="sxs-lookup"><span data-stu-id="3b179-106">Properties</span></span>

|  <span data-ttu-id="3b179-107">Eigenschap</span><span class="sxs-lookup"><span data-stu-id="3b179-107">Property</span></span> |  <span data-ttu-id="3b179-108">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="3b179-108">Description</span></span> |
|---|---|
| <span data-ttu-id="3b179-109">filePath</span><span class="sxs-lookup"><span data-stu-id="3b179-109">FilePath</span></span>| <span data-ttu-id="3b179-110">Het volledige pad naar het bestand om regels in in het doelknooppunt te beheren.</span><span class="sxs-lookup"><span data-stu-id="3b179-110">The full path to the file to manage lines in on the target node.</span></span>|
| <span data-ttu-id="3b179-111">ContainsLine</span><span class="sxs-lookup"><span data-stu-id="3b179-111">ContainsLine</span></span>| <span data-ttu-id="3b179-112">Een regel om ervoor te zorgen bestaat in het bestand.</span><span class="sxs-lookup"><span data-stu-id="3b179-112">A line to ensure exists in the file.</span></span> <span data-ttu-id="3b179-113">Deze regel wordt toegevoegd aan het bestand als deze niet in het bestand bestaat nog.</span><span class="sxs-lookup"><span data-stu-id="3b179-113">This line will be appended to the file if it does not exist in the file.</span></span> <span data-ttu-id="3b179-114">**ContainsLine** is verplicht, maar kan worden ingesteld op een lege tekenreeks ('ContainsLine = ''') als deze niet nodig is.</span><span class="sxs-lookup"><span data-stu-id="3b179-114">**ContainsLine** is mandatory, but can be set to an empty string (\`ContainsLine = ‘’\`\`) if it is not needed.</span></span>|
| <span data-ttu-id="3b179-115">DoesNotContainPattern</span><span class="sxs-lookup"><span data-stu-id="3b179-115">DoesNotContainPattern</span></span>| <span data-ttu-id="3b179-116">Een reguliere-expressiepatroon voor regels die niet in het bestand moet bestaan.</span><span class="sxs-lookup"><span data-stu-id="3b179-116">A regular expression pattern for lines that should not exist in the file.</span></span> <span data-ttu-id="3b179-117">Voor alle regels die zijn opgenomen in het bestand die overeenkomen met de reguliere expressie, wordt de regel wordt verwijderd uit het bestand.</span><span class="sxs-lookup"><span data-stu-id="3b179-117">For any lines that exist in the file that match this regular expression, the line will be removed from the file.</span></span>|
| <span data-ttu-id="3b179-118">dependsOn</span><span class="sxs-lookup"><span data-stu-id="3b179-118">DependsOn</span></span> | <span data-ttu-id="3b179-119">Hiermee wordt aangegeven dat de configuratie van een andere resource uitvoeren moet voordat deze bron is geconfigureerd.</span><span class="sxs-lookup"><span data-stu-id="3b179-119">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="3b179-120">Bijvoorbeeld, als de **ID** van de resource is scriptblok configuratie die u wilt uitvoeren eerst **ResourceName** en het type **ResourceType**, de syntaxis voor het gebruik van deze de eigenschap is `DependsOn = "[ResourceType]ResourceName"`.</span><span class="sxs-lookup"><span data-stu-id="3b179-120">For example, if the **ID** of the resource configuration script block that you want to run first is **ResourceName** and its type is **ResourceType**, the syntax for using this property is `DependsOn = "[ResourceType]ResourceName"`.</span></span>|

## <a name="example"></a><span data-ttu-id="3b179-121">Voorbeeld</span><span class="sxs-lookup"><span data-stu-id="3b179-121">Example</span></span>

<span data-ttu-id="3b179-122">In dit voorbeeld wordt met behulp van de **nxFileLine** resource voor het configureren van de `/etc/sudoers` -bestand, zorgt u ervoor dat de gebruiker: monuser niet requiretty is geconfigureerd.</span><span class="sxs-lookup"><span data-stu-id="3b179-122">This example demonstrates using the **nxFileLine** resource to configure the `/etc/sudoers` file, ensuring that the user: monuser is configured to not requiretty.</span></span>

```
Import-DSCResource -Module nx

nxFileLine DoNotRequireTTY
{
   FilePath = “/etc/sudoers”
   ContainsLine = 'Defaults:monuser !requiretty'
   DoesNotContainPattern = "Defaults:monuser[ ]+requiretty"
}
```