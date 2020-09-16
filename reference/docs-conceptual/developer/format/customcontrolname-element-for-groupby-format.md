---
title: CustomControlName-element voor GroupBy (indeling) | Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: 4e3102f12cd37fa72a2de1bf1db5d1f82db31222
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 08/05/2020
ms.locfileid: "87783735"
---
# <a name="customcontrolname-element-for-groupby-format"></a><span data-ttu-id="dbf5a-102">Het element CustomControlName voor GroupBy (opmaak)</span><span class="sxs-lookup"><span data-stu-id="dbf5a-102">CustomControlName Element for GroupBy (Format)</span></span>

<span data-ttu-id="dbf5a-103">Hiermee geeft u de naam op van een aangepast besturings element dat wordt gebruikt om de nieuwe groep weer te geven.</span><span class="sxs-lookup"><span data-stu-id="dbf5a-103">Specifies the name of a custom control that is used to display the new group.</span></span> <span data-ttu-id="dbf5a-104">Dit element wordt gebruikt bij het definiëren van een tabel, lijst, brede of aangepaste beheer weergave.</span><span class="sxs-lookup"><span data-stu-id="dbf5a-104">This element is used when defining a table, list, wide or custom control view.</span></span>

<span data-ttu-id="dbf5a-105">Configuratie-element (indeling) ViewDefinitions element (indeling) element weer geven (indeling) GroupBy-element voor weer gave (indeling) CustomControlName element van GroupBy (indeling)</span><span class="sxs-lookup"><span data-stu-id="dbf5a-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) GroupBy Element for View (Format) CustomControlName Element of GroupBy (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="dbf5a-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="dbf5a-106">Syntax</span></span>

```xml
<CustomControlName>ControlName</CustomControlName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="dbf5a-107">Kenmerken en elementen</span><span class="sxs-lookup"><span data-stu-id="dbf5a-107">Attributes and Elements</span></span>

<span data-ttu-id="dbf5a-108">In de volgende secties worden de kenmerken, onderliggende elementen en bovenliggende elementen van het `CustomControlName` element beschreven.</span><span class="sxs-lookup"><span data-stu-id="dbf5a-108">The following sections describe the attributes, child elements, and parent elements of the `CustomControlName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="dbf5a-109">Kenmerken</span><span class="sxs-lookup"><span data-stu-id="dbf5a-109">Attributes</span></span>

<span data-ttu-id="dbf5a-110">Geen.</span><span class="sxs-lookup"><span data-stu-id="dbf5a-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="dbf5a-111">Onderliggende elementen</span><span class="sxs-lookup"><span data-stu-id="dbf5a-111">Child Elements</span></span>

<span data-ttu-id="dbf5a-112">Geen.</span><span class="sxs-lookup"><span data-stu-id="dbf5a-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="dbf5a-113">Bovenliggende elementen</span><span class="sxs-lookup"><span data-stu-id="dbf5a-113">Parent Elements</span></span>

|<span data-ttu-id="dbf5a-114">Element</span><span class="sxs-lookup"><span data-stu-id="dbf5a-114">Element</span></span>|<span data-ttu-id="dbf5a-115">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="dbf5a-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="dbf5a-116">Het element GroupBy voor Weergave (opmaak)</span><span class="sxs-lookup"><span data-stu-id="dbf5a-116">GroupBy Element for View (Format)</span></span>](./groupby-element-for-view-format.md)|<span data-ttu-id="dbf5a-117">Definieert hoe een nieuwe groep objecten wordt weer gegeven in Windows Power shell.</span><span class="sxs-lookup"><span data-stu-id="dbf5a-117">Defines how Windows PowerShell displays a new group of objects.</span></span>|

## <a name="text-value"></a><span data-ttu-id="dbf5a-118">Tekstwaarde</span><span class="sxs-lookup"><span data-stu-id="dbf5a-118">Text Value</span></span>

<span data-ttu-id="dbf5a-119">Geef de naam op van het aangepaste besturings element dat wordt gebruikt om een nieuwe groep weer te geven.</span><span class="sxs-lookup"><span data-stu-id="dbf5a-119">Specify the name of the custom control that is used to display a new group.</span></span>

## <a name="remarks"></a><span data-ttu-id="dbf5a-120">Opmerkingen</span><span class="sxs-lookup"><span data-stu-id="dbf5a-120">Remarks</span></span>

<span data-ttu-id="dbf5a-121">U kunt algemene besturings elementen maken die kunnen worden gebruikt door alle weer gaven van een opmaak bestand, en u kunt weergave besturings elementen maken die kunnen worden gebruikt door een specifieke weer gave.</span><span class="sxs-lookup"><span data-stu-id="dbf5a-121">You can create common controls that can be used by all the views of a formatting file, and you can create view controls that can be used by a specific view.</span></span> <span data-ttu-id="dbf5a-122">In de volgende elementen worden de namen van deze aangepaste besturings elementen opgegeven:</span><span class="sxs-lookup"><span data-stu-id="dbf5a-122">The following elements specify the names of these custom controls:</span></span>

- [<span data-ttu-id="dbf5a-123">Het element Naam voor Besturingselement voor Besturingselementen voor Configuratie (opmaak)</span><span class="sxs-lookup"><span data-stu-id="dbf5a-123">Name Element for Control for Controls for Configuration (Format)</span></span>](./name-element-for-control-for-controls-for-configuration-format.md)

- [<span data-ttu-id="dbf5a-124">Het element Naam voor Besturingselement voor Besturingselementen voor Weergave (opmaak)</span><span class="sxs-lookup"><span data-stu-id="dbf5a-124">Name Element for Control for Controls for View (Format)</span></span>](./name-element-for-control-for-controls-for-view-format.md)

## <a name="see-also"></a><span data-ttu-id="dbf5a-125">Zie ook</span><span class="sxs-lookup"><span data-stu-id="dbf5a-125">See Also</span></span>

[<span data-ttu-id="dbf5a-126">Het element GroupBy voor Weergave (opmaak)</span><span class="sxs-lookup"><span data-stu-id="dbf5a-126">GroupBy Element for View (Format)</span></span>](./groupby-element-for-view-format.md)

[<span data-ttu-id="dbf5a-127">Het element Naam voor Besturingselement voor Besturingselementen voor Configuratie (opmaak)</span><span class="sxs-lookup"><span data-stu-id="dbf5a-127">Name Element for Control for Controls for Configuration (Format)</span></span>](./name-element-for-control-for-controls-for-configuration-format.md)

[<span data-ttu-id="dbf5a-128">Het element Naam voor Besturingselement voor Besturingselementen voor Weergave (opmaak)</span><span class="sxs-lookup"><span data-stu-id="dbf5a-128">Name Element for Control for Controls for View (Format)</span></span>](./name-element-for-control-for-controls-for-view-format.md)

[<span data-ttu-id="dbf5a-129">Een PowerShell-opmaakbestand schrijven</span><span class="sxs-lookup"><span data-stu-id="dbf5a-129">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
