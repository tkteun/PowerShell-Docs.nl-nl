---
ms.date: 08/25/2017
keywords: PowerShell-cmdlet
title: Het ObjectModelRoot-object
ms.openlocfilehash: 2670321ebac1eac4ecc8457afb796f9f260da471
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 04/09/2018
ms.locfileid: "30954599"
---
# <a name="the-objectmodelroot-object"></a><span data-ttu-id="65a54-103">Het ObjectModelRoot-object</span><span class="sxs-lookup"><span data-stu-id="65a54-103">The ObjectModelRoot Object</span></span>

<span data-ttu-id="65a54-104">De **$psISE** object, dat de principal hoofdobject in Windows PowerShell® Integrated Scripting Environment (ISE) is een exemplaar van de klasse Microsoft.PowerShell.Host.ISE.ObjectModelRoot.</span><span class="sxs-lookup"><span data-stu-id="65a54-104">The **$psISE** object, which is the principal root object in Windows PowerShell® Integrated Scripting Environment (ISE) is an instance of the Microsoft.PowerShell.Host.ISE.ObjectModelRoot class.</span></span>
<span data-ttu-id="65a54-105">In dit onderwerp beschrijft de eigenschappen van de **ObjectModelRoot** object.</span><span class="sxs-lookup"><span data-stu-id="65a54-105">This topic describes the properties of the **ObjectModelRoot** object.</span></span>

## <a name="properties"></a><span data-ttu-id="65a54-106">Eigenschappen</span><span class="sxs-lookup"><span data-stu-id="65a54-106">Properties</span></span>

### <a name="currentfile"></a><span data-ttu-id="65a54-107">CurrentFile</span><span class="sxs-lookup"><span data-stu-id="65a54-107">CurrentFile</span></span>

> <span data-ttu-id="65a54-108">In Windows PowerShell ISE 2.0 en hoger ondersteund.</span><span class="sxs-lookup"><span data-stu-id="65a54-108">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="65a54-109">De alleen-lezen eigenschap die opgehaald van het bestand, dat is gekoppeld aan deze hostobject dat momenteel de focus heeft.</span><span class="sxs-lookup"><span data-stu-id="65a54-109">The read-only property that gets the file, which is associated with this host object that currently has the focus.</span></span>

### <a name="currentpowershelltab"></a><span data-ttu-id="65a54-110">CurrentPowerShellTab</span><span class="sxs-lookup"><span data-stu-id="65a54-110">CurrentPowerShellTab</span></span>

> <span data-ttu-id="65a54-111">In Windows PowerShell ISE 2.0 en hoger ondersteund.</span><span class="sxs-lookup"><span data-stu-id="65a54-111">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="65a54-112">De alleen-lezen eigenschap die het PowerShell-tabblad opgehaald die heeft de focus.</span><span class="sxs-lookup"><span data-stu-id="65a54-112">The read-only property that gets the PowerShell tab that has the focus.</span></span>

### <a name="currentvisiblehorizontaltool"></a><span data-ttu-id="65a54-113">CurrentVisibleHorizontalTool</span><span class="sxs-lookup"><span data-stu-id="65a54-113">CurrentVisibleHorizontalTool</span></span>

> <span data-ttu-id="65a54-114">In Windows PowerShell ISE 2.0 en hoger ondersteund.</span><span class="sxs-lookup"><span data-stu-id="65a54-114">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="65a54-115">De alleen-lezen eigenschap die het momenteel zichtbaar zijn Windows PowerShell ISE-invoegtoepassing hulpprogramma opgehaald die bevindt zich in het deelvenster horizontale hulpprogramma aan de onderkant van de editor.</span><span class="sxs-lookup"><span data-stu-id="65a54-115">The read-only property that gets the currently visible Windows PowerShell ISE add-on tool that is located in the horizontal tool pane at the bottom of the editor.</span></span>

### <a name="currentvisibleverticaltool"></a><span data-ttu-id="65a54-116">CurrentVisibleVerticalTool</span><span class="sxs-lookup"><span data-stu-id="65a54-116">CurrentVisibleVerticalTool</span></span>

> <span data-ttu-id="65a54-117">In Windows PowerShell ISE 2.0 en hoger ondersteund.</span><span class="sxs-lookup"><span data-stu-id="65a54-117">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="65a54-118">De alleen-lezen eigenschap die het momenteel zichtbaar zijn Windows PowerShell ISE-invoegtoepassing hulpprogramma opgehaald die bevindt zich in de verticale werkvenster aan de rechterkant van de editor.</span><span class="sxs-lookup"><span data-stu-id="65a54-118">The read-only property that gets the currently visible Windows PowerShell ISE add-on tool that is located in the vertical tool pane on the right side of the editor.</span></span>

### <a name="options"></a><span data-ttu-id="65a54-119">Opties</span><span class="sxs-lookup"><span data-stu-id="65a54-119">Options</span></span>

> <span data-ttu-id="65a54-120">In Windows PowerShell ISE 2.0 en hoger ondersteund.</span><span class="sxs-lookup"><span data-stu-id="65a54-120">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="65a54-121">De alleen-lezen eigenschap die opgehaald van de verschillende opties die kunt in Windows PowerShell ISE wijzigen.</span><span class="sxs-lookup"><span data-stu-id="65a54-121">The read-only property that gets the various options that can change settings in Windows PowerShell ISE.</span></span>

### <a name="powershelltabs"></a><span data-ttu-id="65a54-122">PowerShellTabs</span><span class="sxs-lookup"><span data-stu-id="65a54-122">PowerShellTabs</span></span>

> <span data-ttu-id="65a54-123">In Windows PowerShell ISE 2.0 en hoger ondersteund.</span><span class="sxs-lookup"><span data-stu-id="65a54-123">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="65a54-124">De alleen-lezen eigenschap die de verzameling van de PowerShell-tabbladen die geopend in Windows PowerShell ISE zijn opgehaald.</span><span class="sxs-lookup"><span data-stu-id="65a54-124">The read-only property that gets the collection of the PowerShell tabs, which are open in Windows PowerShell ISE.</span></span> <span data-ttu-id="65a54-125">Dit object bevat standaard een PowerShell-tabblad. U kunt echter meer PowerShell tabbladen toevoegen aan dit object met behulp van scripts of door de menu's in Windows PowerShell ISE.</span><span class="sxs-lookup"><span data-stu-id="65a54-125">By default, this object contains one PowerShell tab. However, you can add more PowerShell tabs to this object by using scripts or by using the menus in Windows PowerShell ISE.</span></span>

## <a name="see-also"></a><span data-ttu-id="65a54-126">Zie ook</span><span class="sxs-lookup"><span data-stu-id="65a54-126">See Also</span></span>

- [<span data-ttu-id="65a54-127">Doel van de Windows PowerShell ISE-objectmodel Scripting</span><span class="sxs-lookup"><span data-stu-id="65a54-127">Purpose of the Windows PowerShell ISE Scripting Object Model</span></span>](Purpose-of-the-Windows-PowerShell-ISE-Scripting-Object-Model.md)
- [<span data-ttu-id="65a54-128">De objectmodelhiërarchie van ISE</span><span class="sxs-lookup"><span data-stu-id="65a54-128">The ISE Object Model Hierarchy</span></span>](The-ISE-Object-Model-Hierarchy.md)