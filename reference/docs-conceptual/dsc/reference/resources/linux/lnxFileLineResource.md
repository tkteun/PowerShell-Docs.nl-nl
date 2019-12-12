---
ms.date: 09/20/2019
keywords: DSC, Power shell, configuratie, installatie
title: DSC voor Linux nxFileLine-resource
ms.openlocfilehash: 2e94bab318b5db65df88d268a88585079bab89bf
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 12/05/2019
ms.locfileid: "71941430"
---
# <a name="dsc-for-linux-nxfileline-resource"></a><span data-ttu-id="5f8e3-103">DSC voor Linux nxFileLine-resource</span><span class="sxs-lookup"><span data-stu-id="5f8e3-103">DSC for Linux nxFileLine Resource</span></span>

<span data-ttu-id="5f8e3-104">De **nxFileLine** -resource in Power shell desired state Configuration (DSC) biedt een mechanisme voor het beheren van regels in een configuratie bestand op een Linux-knoop punt.</span><span class="sxs-lookup"><span data-stu-id="5f8e3-104">The **nxFileLine** resource in PowerShell Desired State Configuration (DSC) provides a mechanism to manage lines within a configuration file on a Linux node.</span></span>

## <a name="syntax"></a><span data-ttu-id="5f8e3-105">Syntaxis</span><span class="sxs-lookup"><span data-stu-id="5f8e3-105">Syntax</span></span>

```Syntax
nxFileLine <string> #ResourceName
{
    FilePath = <string>
    ContainsLine = <string>
    [ DoesNotContainPattern = <string> ]
    [ DependsOn = <string[]> ]
}
```

## <a name="properties"></a><span data-ttu-id="5f8e3-106">Eigenschappen</span><span class="sxs-lookup"><span data-stu-id="5f8e3-106">Properties</span></span>

|<span data-ttu-id="5f8e3-107">Eigenschap</span><span class="sxs-lookup"><span data-stu-id="5f8e3-107">Property</span></span> |<span data-ttu-id="5f8e3-108">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="5f8e3-108">Description</span></span> |
|---|---|
|<span data-ttu-id="5f8e3-109">Bestandspad</span><span class="sxs-lookup"><span data-stu-id="5f8e3-109">FilePath</span></span> |<span data-ttu-id="5f8e3-110">Het volledige pad naar het bestand voor het beheren van de regels in het doel knooppunt.</span><span class="sxs-lookup"><span data-stu-id="5f8e3-110">The full path to the file to manage lines in on the target node.</span></span> |
|<span data-ttu-id="5f8e3-111">ContainsLine</span><span class="sxs-lookup"><span data-stu-id="5f8e3-111">ContainsLine</span></span> |<span data-ttu-id="5f8e3-112">Een regel om ervoor te zorgen dat het bestand bestaat.</span><span class="sxs-lookup"><span data-stu-id="5f8e3-112">A line to ensure exists in the file.</span></span> <span data-ttu-id="5f8e3-113">Deze regel wordt toegevoegd aan het bestand als het niet in het bestand voor komt.</span><span class="sxs-lookup"><span data-stu-id="5f8e3-113">This line will be appended to the file if it does not exist in the file.</span></span> <span data-ttu-id="5f8e3-114">**ContainsLine** is verplicht, maar kan worden ingesteld op een lege teken reeks (`ContainsLine = ""`) als dit niet nodig is.</span><span class="sxs-lookup"><span data-stu-id="5f8e3-114">**ContainsLine** is mandatory, but can be set to an empty string (`ContainsLine = ""`) if it is not needed.</span></span> |
|<span data-ttu-id="5f8e3-115">DoesNotContainPattern</span><span class="sxs-lookup"><span data-stu-id="5f8e3-115">DoesNotContainPattern</span></span> |<span data-ttu-id="5f8e3-116">Een reguliere-expressie patroon voor lijnen die niet in het bestand moeten voor komen.</span><span class="sxs-lookup"><span data-stu-id="5f8e3-116">A regular expression pattern for lines that should not exist in the file.</span></span> <span data-ttu-id="5f8e3-117">Voor alle regels die voor komen in het bestand die overeenkomen met deze reguliere expressie, wordt de regel uit het bestand verwijderd.</span><span class="sxs-lookup"><span data-stu-id="5f8e3-117">For any lines that exist in the file that match this regular expression, the line will be removed from the file.</span></span> |

## <a name="common-properties"></a><span data-ttu-id="5f8e3-118">Algemene eigenschappen</span><span class="sxs-lookup"><span data-stu-id="5f8e3-118">Common properties</span></span>

|<span data-ttu-id="5f8e3-119">Eigenschap</span><span class="sxs-lookup"><span data-stu-id="5f8e3-119">Property</span></span> |<span data-ttu-id="5f8e3-120">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="5f8e3-120">Description</span></span> |
|---|---|
|<span data-ttu-id="5f8e3-121">DependsOn</span><span class="sxs-lookup"><span data-stu-id="5f8e3-121">DependsOn</span></span> |<span data-ttu-id="5f8e3-122">Geeft aan dat de configuratie van een andere bron moet worden uitgevoerd voordat deze resource wordt geconfigureerd.</span><span class="sxs-lookup"><span data-stu-id="5f8e3-122">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="5f8e3-123">Als de ID van het resource-configuratie script blok dat u eerst wilt uitvoeren bijvoorbeeld de naam ResourceName is, en het type van de bron resource is, is de syntaxis voor het gebruik van deze eigenschap `DependsOn = "[ResourceType]ResourceName"`.</span><span class="sxs-lookup"><span data-stu-id="5f8e3-123">For example, if the ID of the resource configuration script block that you want to run first is ResourceName and its type is ResourceType, the syntax for using this property is `DependsOn = "[ResourceType]ResourceName"`.</span></span> |

## <a name="example"></a><span data-ttu-id="5f8e3-124">Voorbeeld</span><span class="sxs-lookup"><span data-stu-id="5f8e3-124">Example</span></span>

<span data-ttu-id="5f8e3-125">In dit voor beeld wordt gedemonstreerd met behulp van de **nxFileLine** -resource voor het configureren van het `/etc/sudoers` bestand, zodat de gebruiker: monuser is geconfigureerd om niet requiretty.</span><span class="sxs-lookup"><span data-stu-id="5f8e3-125">This example demonstrates using the **nxFileLine** resource to configure the `/etc/sudoers` file, ensuring that the user: monuser is configured to not requiretty.</span></span>

```powershell
Import-DscResource -Module nx

nxFileLine DoNotRequireTTY
{
   FilePath = "/etc/sudoers"
   ContainsLine = 'Defaults:monuser !requiretty'
   DoesNotContainPattern = "Defaults:monuser[ ]+requiretty"
}
```