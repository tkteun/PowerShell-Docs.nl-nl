---
ms.date: 06/12/2017
keywords: wmf,powershell,installeren
ms.openlocfilehash: 46a278b83edb9d8e3d75b0874603710d416be3b5
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 02/03/2019
ms.locfileid: "55684652"
---
# <a name="import-dscresource-keyword-supports--moduleversion-parameter"></a><span data-ttu-id="07c13-102">Sleutelwoord sleutelwoorden import-dscresource bieden ondersteuning biedt voor de parameter - ModuleVersion</span><span class="sxs-lookup"><span data-stu-id="07c13-102">Import-DscResource keyword supports -ModuleVersion parameter</span></span>

<span data-ttu-id="07c13-103">We hebben een nieuwe parameter toegevoegd de `Import-DscResource` dynamische sleutelwoord beschikbaar bij het ontwerpen van DSC-configuraties.</span><span class="sxs-lookup"><span data-stu-id="07c13-103">We have added a new parameter to the `Import-DscResource` dynamic keyword available when authoring DSC configurations.</span></span> <span data-ttu-id="07c13-104">Configuratie auteurs kunnen nu precies welke moduleversie voor het laden van de DSC-resources uit opgeven.</span><span class="sxs-lookup"><span data-stu-id="07c13-104">Configuration authors can now specify exactly which module version to load the DSC resources from.</span></span> <span data-ttu-id="07c13-105">De nieuwe syntaxis van het sleutelwoord is:</span><span class="sxs-lookup"><span data-stu-id="07c13-105">The new syntax of the keyword is:</span></span>

```powershell
Import-DscResource [-Name <ResourceName(s)>] [-ModuleName <ModuleName(s)>] [-ModuleVersion <ModuleVersion>]
```

* <span data-ttu-id="07c13-106">**Naam**: Namen van een of meer resources te importeren.</span><span class="sxs-lookup"><span data-stu-id="07c13-106">**Name**: Names of one or more resources to import.</span></span>
* <span data-ttu-id="07c13-107">**ModuleName**: Modulenamen of ModuleSpecification objecten van een of meer modules te importeren.</span><span class="sxs-lookup"><span data-stu-id="07c13-107">**ModuleName**: Module names or ModuleSpecification objects of one or more modules to import.</span></span>
* <span data-ttu-id="07c13-108">**ModuleVersion**: De versie van de module te importeren.</span><span class="sxs-lookup"><span data-stu-id="07c13-108">**ModuleVersion**: Version of module to import.</span></span> <span data-ttu-id="07c13-109">Als u gebruikt, moet ModuleName slechts één module met de naam vertegenwoordigen.</span><span class="sxs-lookup"><span data-stu-id="07c13-109">If used, ModuleName must represent only one module by name.</span></span>

<span data-ttu-id="07c13-110">In de Windows PowerShell ISE, wordt deze weergegeven met IntelliSense:</span><span class="sxs-lookup"><span data-stu-id="07c13-110">In the Windows PowerShell ISE, it shows up with IntelliSense:</span></span>

![](../images/Import-DscResource-Modversion.jpg)

<span data-ttu-id="07c13-111">**Houd er rekening mee**: de `–ModuleVersion` parameter kan alleen worden gebruikt in combinatie met de `–ModuleName` parameter.</span><span class="sxs-lookup"><span data-stu-id="07c13-111">**Note**: the `–ModuleVersion` parameter can only be used in combination with the `–ModuleName` parameter.</span></span> <span data-ttu-id="07c13-112">Deze kan niet worden gebruikt met namen van voorbeeldresources met alleen de `–Name` parameter.</span><span class="sxs-lookup"><span data-stu-id="07c13-112">It cannot be used with resource names using only the `–Name` parameter.</span></span>

<span data-ttu-id="07c13-113">Voordat dit is de enige manier om op te geven van de versie van de module bij het laden van DSC-resources met behulp van de Module-specificatie-object, bijvoorbeeld: `–ModuleName @{ModuleName="UserConfigProvider";ModuleVersion="3.0"}`</span><span class="sxs-lookup"><span data-stu-id="07c13-113">Before this, the only way to specify the module version when loading DSC resources was by using the Module specification object e.g.: `–ModuleName @{ModuleName="UserConfigProvider";ModuleVersion="3.0"}`</span></span>
