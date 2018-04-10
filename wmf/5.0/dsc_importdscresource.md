---
ms.date: 06/12/2017
author: JKeithB
ms.topic: reference
keywords: wmf,powershell,installeren
ms.openlocfilehash: a3b176101bebf7081febd8629bddcfa0ae1e7540
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 04/09/2018
---
# <a name="import-dscresource-keyword-supports--moduleversion-parameter"></a><span data-ttu-id="32bb9-102">Importeren DscResource sleutelwoord ondersteunt ModuleVersion - parameter</span><span class="sxs-lookup"><span data-stu-id="32bb9-102">Import-DscResource keyword supports -ModuleVersion parameter</span></span>

<span data-ttu-id="32bb9-103">We hebben een nieuwe parameter voor toegevoegd de `Import-DscResource` dynamische sleutelwoord beschikbaar bij het ontwerpen van DSC-configuraties.</span><span class="sxs-lookup"><span data-stu-id="32bb9-103">We have added a new parameter to the `Import-DscResource` dynamic keyword available when authoring DSC configurations.</span></span> <span data-ttu-id="32bb9-104">Configuratie auteurs kunnen nu precies welke moduleversie om te laden van de DSC-resources van opgeven.</span><span class="sxs-lookup"><span data-stu-id="32bb9-104">Configuration authors can now specify exactly which module version to load the DSC resources from.</span></span> <span data-ttu-id="32bb9-105">De nieuwe syntaxis van het trefwoord is:</span><span class="sxs-lookup"><span data-stu-id="32bb9-105">The new syntax of the keyword is:</span></span>

```powershell
Import-DscResource [-Name <ResourceName(s)>] [-ModuleName <ModuleName(s)>] [-ModuleVersion <ModuleVersion>]
```

* <span data-ttu-id="32bb9-106">**Naam**: namen van een of meer resources om te importeren.</span><span class="sxs-lookup"><span data-stu-id="32bb9-106">**Name**: Names of one or more resources to import.</span></span>
* <span data-ttu-id="32bb9-107">**Modulenaam**: modulenamen of ModuleSpecification objecten van een of meer modules voor het importeren.</span><span class="sxs-lookup"><span data-stu-id="32bb9-107">**ModuleName**: Module names or ModuleSpecification objects of one or more modules to import.</span></span>
* <span data-ttu-id="32bb9-108">**ModuleVersion**: versie van de module iet importeren.</span><span class="sxs-lookup"><span data-stu-id="32bb9-108">**ModuleVersion**: Version of module ot import.</span></span> <span data-ttu-id="32bb9-109">Als u gebruikt, moet de modulenaam slechts één module met de naam vertegenwoordigen.</span><span class="sxs-lookup"><span data-stu-id="32bb9-109">If used, ModuleName must represent only one module by name.</span></span>

<span data-ttu-id="32bb9-110">In de Windows PowerShell ISE, wordt deze weergegeven met IntelliSense:</span><span class="sxs-lookup"><span data-stu-id="32bb9-110">In the Windows PowerShell ISE, it shows up with IntelliSense:</span></span>

![](../images/Import-DscResource-Modversion.jpg)

<span data-ttu-id="32bb9-111">**Opmerking**: de `–ModuleVersion` parameter kan alleen worden gebruikt in combinatie met de `–ModuleName` parameter.</span><span class="sxs-lookup"><span data-stu-id="32bb9-111">**Note**: the `–ModuleVersion` parameter can only be used in combination with the `–ModuleName` parameter.</span></span> <span data-ttu-id="32bb9-112">Deze kan niet worden gebruikt met resourcenamen met alleen de `–Name` parameter.</span><span class="sxs-lookup"><span data-stu-id="32bb9-112">It cannot be used with resource names using only the `–Name` parameter.</span></span>

<span data-ttu-id="32bb9-113">Voordat dit is de enige manier om de moduleversie opgeven bij het laden van DSC-resources met behulp van de specificatie moduleobject bijvoorbeeld: `–ModuleName @{ModuleName="UserConfigProvider";ModuleVersion="3.0"}`</span><span class="sxs-lookup"><span data-stu-id="32bb9-113">Before this, the only way to specify the module version when loading DSC resources was by using the Module specification object e.g.: `–ModuleName @{ModuleName="UserConfigProvider";ModuleVersion="3.0"}`</span></span>