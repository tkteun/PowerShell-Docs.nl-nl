---
ms.date: 07/17/2020
keywords: DSC, Power shell, configuratie, installatie
title: DSC voor Linux nxFileLine-resource
ms.openlocfilehash: c87054ec7039923bcb5e7c5c5d58f9221a12c9ca
ms.sourcegitcommit: 41e1acbd9ce0f49a23c6eb99facd2c280d836836
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/18/2020
ms.locfileid: "86463666"
---
# <a name="dsc-for-linux-nxfileline-resource"></a><span data-ttu-id="b86db-103">DSC voor Linux nxFileLine-resource</span><span class="sxs-lookup"><span data-stu-id="b86db-103">DSC for Linux nxFileLine Resource</span></span>

<span data-ttu-id="b86db-104">De **nxFileLine** -resource in Power shell desired state Configuration (DSC) biedt een mechanisme voor het beheren van regels in een configuratie bestand op een Linux-knoop punt.</span><span class="sxs-lookup"><span data-stu-id="b86db-104">The **nxFileLine** resource in PowerShell Desired State Configuration (DSC) provides a mechanism to manage lines within a configuration file on a Linux node.</span></span>

## <a name="syntax"></a><span data-ttu-id="b86db-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="b86db-105">Syntax</span></span>

```Syntax
nxFileLine <string> #ResourceName
{
    FilePath = <string>
    ContainsLine = <string>
    [ DoesNotContainPattern = <string> ]
    [ DependsOn = <string[]> ]
}
```

## <a name="properties"></a><span data-ttu-id="b86db-106">Eigenschappen</span><span class="sxs-lookup"><span data-stu-id="b86db-106">Properties</span></span>

|<span data-ttu-id="b86db-107">Eigenschap</span><span class="sxs-lookup"><span data-stu-id="b86db-107">Property</span></span> |<span data-ttu-id="b86db-108">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="b86db-108">Description</span></span> |
|---|---|
|<span data-ttu-id="b86db-109">Bestandspad</span><span class="sxs-lookup"><span data-stu-id="b86db-109">FilePath</span></span> |<span data-ttu-id="b86db-110">Het volledige pad naar het bestand voor het beheren van de regels in het doel knooppunt.</span><span class="sxs-lookup"><span data-stu-id="b86db-110">The full path to the file to manage lines in on the target node.</span></span> |
|<span data-ttu-id="b86db-111">ContainsLine</span><span class="sxs-lookup"><span data-stu-id="b86db-111">ContainsLine</span></span> |<span data-ttu-id="b86db-112">Een regel om ervoor te zorgen dat het bestand bestaat.</span><span class="sxs-lookup"><span data-stu-id="b86db-112">A line to ensure exists in the file.</span></span> <span data-ttu-id="b86db-113">Deze regel wordt toegevoegd aan het bestand als het niet in het bestand voor komt.</span><span class="sxs-lookup"><span data-stu-id="b86db-113">This line will be appended to the file if it does not exist in the file.</span></span> <span data-ttu-id="b86db-114">**ContainsLine** is verplicht, maar kan worden ingesteld op een lege teken reeks ( `ContainsLine = ""` ) als dit niet nodig is.</span><span class="sxs-lookup"><span data-stu-id="b86db-114">**ContainsLine** is mandatory, but can be set to an empty string (`ContainsLine = ""`) if it is not needed.</span></span> |
|<span data-ttu-id="b86db-115">DoesNotContainPattern</span><span class="sxs-lookup"><span data-stu-id="b86db-115">DoesNotContainPattern</span></span> |<span data-ttu-id="b86db-116">Een reguliere-expressie patroon voor lijnen die niet in het bestand moeten voor komen.</span><span class="sxs-lookup"><span data-stu-id="b86db-116">A regular expression pattern for lines that should not exist in the file.</span></span> <span data-ttu-id="b86db-117">Voor alle regels die voor komen in het bestand die overeenkomen met deze reguliere expressie, wordt de regel uit het bestand verwijderd.</span><span class="sxs-lookup"><span data-stu-id="b86db-117">For any lines that exist in the file that match this regular expression, the line will be removed from the file.</span></span> |

## <a name="common-properties"></a><span data-ttu-id="b86db-118">Algemene eigenschappen</span><span class="sxs-lookup"><span data-stu-id="b86db-118">Common properties</span></span>

|<span data-ttu-id="b86db-119">Eigenschap</span><span class="sxs-lookup"><span data-stu-id="b86db-119">Property</span></span> |<span data-ttu-id="b86db-120">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="b86db-120">Description</span></span> |
|---|---|
|<span data-ttu-id="b86db-121">DependsOn</span><span class="sxs-lookup"><span data-stu-id="b86db-121">DependsOn</span></span> |<span data-ttu-id="b86db-122">Geeft aan dat de configuratie van een andere bron moet worden uitgevoerd voordat deze resource wordt geconfigureerd.</span><span class="sxs-lookup"><span data-stu-id="b86db-122">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="b86db-123">De syntaxis voor het gebruik van deze eigenschap is bijvoorbeeld als de ID van het resource-script blok dat u als eerste wilt uitvoeren, de naam ResourceName is en het type van de bron resource is `DependsOn = "[ResourceType]ResourceName"` .</span><span class="sxs-lookup"><span data-stu-id="b86db-123">For example, if the ID of the resource configuration script block that you want to run first is ResourceName and its type is ResourceType, the syntax for using this property is `DependsOn = "[ResourceType]ResourceName"`.</span></span> |

## <a name="example"></a><span data-ttu-id="b86db-124">Voorbeeld</span><span class="sxs-lookup"><span data-stu-id="b86db-124">Example</span></span>

<span data-ttu-id="b86db-125">In dit voor beeld ziet u hoe u de **nxFileLine** -resource gebruikt om het bestand te configureren `/etc/sudoers` , zodat de gebruiker: monuser is geconfigureerd om niet requiretty.</span><span class="sxs-lookup"><span data-stu-id="b86db-125">This example demonstrates using the **nxFileLine** resource to configure the `/etc/sudoers` file, ensuring that the user: monuser is configured to not requiretty.</span></span>

```powershell
Import-DscResource -Module nx

nxFileLine DoNotRequireTTY
{
   FilePath = "/etc/sudoers"
   ContainsLine = 'Defaults:monuser !requiretty'
   DoesNotContainPattern = "Defaults:monuser[ ]+requiretty"
}
```
