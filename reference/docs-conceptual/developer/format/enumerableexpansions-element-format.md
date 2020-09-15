---
title: EnumerableExpansions-element (indeling) | Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: 2b536b1ab9b34b0089d0a38d3c5dc7a937176443
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 08/05/2020
ms.locfileid: "87774011"
---
# <a name="enumerableexpansions-element-format"></a><span data-ttu-id="f6590-102">Het element EnumerableExpansions (opmaak)</span><span class="sxs-lookup"><span data-stu-id="f6590-102">EnumerableExpansions Element (Format)</span></span>

<span data-ttu-id="f6590-103">Hiermee definieert u hoe .NET-verzamelings objecten worden uitgevouwen wanneer ze worden weer gegeven in een weer gave.</span><span class="sxs-lookup"><span data-stu-id="f6590-103">Defines how .NET collection objects are expanded when they are displayed in a view.</span></span>

<span data-ttu-id="f6590-104">Configuratie-element (indeling) DefaultSettings element (indeling) EnumerableExpansions element (indeling)</span><span class="sxs-lookup"><span data-stu-id="f6590-104">Configuration Element (Format) DefaultSettings Element (Format) EnumerableExpansions Element (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="f6590-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="f6590-105">Syntax</span></span>

```xml
<EnumerableExpansions>
  <EnumerableExpansion>...</EnumerableExpansion>
</EnumerableExpansions>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="f6590-106">Kenmerken en elementen</span><span class="sxs-lookup"><span data-stu-id="f6590-106">Attributes and Elements</span></span>

<span data-ttu-id="f6590-107">In de volgende secties worden kenmerken, onderliggende elementen en het bovenliggende element van het `EnumerableExpansions` element beschreven.</span><span class="sxs-lookup"><span data-stu-id="f6590-107">The following sections describe attributes, child elements, and the parent element of the `EnumerableExpansions` element.</span></span> <span data-ttu-id="f6590-108">Er is geen limiet voor het aantal onderliggende elementen dat u kunt gebruiken.</span><span class="sxs-lookup"><span data-stu-id="f6590-108">There is no limit to the number of child elements that you can use.</span></span>

### <a name="attributes"></a><span data-ttu-id="f6590-109">Kenmerken</span><span class="sxs-lookup"><span data-stu-id="f6590-109">Attributes</span></span>

<span data-ttu-id="f6590-110">Geen.</span><span class="sxs-lookup"><span data-stu-id="f6590-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="f6590-111">Onderliggende elementen</span><span class="sxs-lookup"><span data-stu-id="f6590-111">Child Elements</span></span>

|<span data-ttu-id="f6590-112">Element</span><span class="sxs-lookup"><span data-stu-id="f6590-112">Element</span></span>|<span data-ttu-id="f6590-113">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="f6590-113">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="f6590-114">Het element EnumerableExpansion (opmaak)</span><span class="sxs-lookup"><span data-stu-id="f6590-114">EnumerableExpansion Element (Format)</span></span>](./enumerableexpansion-element-format.md)|<span data-ttu-id="f6590-115">Optioneel element.</span><span class="sxs-lookup"><span data-stu-id="f6590-115">Optional element.</span></span><br /><br /> <span data-ttu-id="f6590-116">Hiermee worden de specifieke .NET-verzamelings objecten gedefinieerd die worden uitgevouwen wanneer ze worden weer gegeven in een weer gave.</span><span class="sxs-lookup"><span data-stu-id="f6590-116">Defines the specific .NET collection objects that are expanded when they are displayed in a view.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="f6590-117">Bovenliggende elementen</span><span class="sxs-lookup"><span data-stu-id="f6590-117">Parent Elements</span></span>

|<span data-ttu-id="f6590-118">Element</span><span class="sxs-lookup"><span data-stu-id="f6590-118">Element</span></span>|<span data-ttu-id="f6590-119">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="f6590-119">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="f6590-120">Het element DefaultSettings (opmaak)</span><span class="sxs-lookup"><span data-stu-id="f6590-120">DefaultSettings Element (Format)</span></span>](./defaultsettings-element-format.md)|<span data-ttu-id="f6590-121">Hiermee definieert u algemene instellingen die van toepassing zijn op alle weer gaven van het opmaak bestand.</span><span class="sxs-lookup"><span data-stu-id="f6590-121">Defines common settings that apply to all the views of the formatting file.</span></span>|

## <a name="remarks"></a><span data-ttu-id="f6590-122">Opmerkingen</span><span class="sxs-lookup"><span data-stu-id="f6590-122">Remarks</span></span>

<span data-ttu-id="f6590-123">Dit element wordt gebruikt om te definiëren hoe verzamelings objecten en de objecten in de verzameling worden weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="f6590-123">This element is used to define how collection objects and the objects in the collection are displayed.</span></span> <span data-ttu-id="f6590-124">In dit geval verwijst een verzamelings object naar een object dat de interface  **System. Collections. ICollection** ondersteunt.</span><span class="sxs-lookup"><span data-stu-id="f6590-124">In this case, a collection object refers to any object that supports the  **System.Collections.ICollection** interface.</span></span>

## <a name="see-also"></a><span data-ttu-id="f6590-125">Zie ook</span><span class="sxs-lookup"><span data-stu-id="f6590-125">See Also</span></span>

[<span data-ttu-id="f6590-126">Een PowerShell-opmaakbestand schrijven</span><span class="sxs-lookup"><span data-stu-id="f6590-126">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
