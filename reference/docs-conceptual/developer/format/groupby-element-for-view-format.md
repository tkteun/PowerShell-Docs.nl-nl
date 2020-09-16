---
title: Element GroupBy voor weer gave (indeling) | Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: 2f9071a3ebbc7cc2ccb7721dd518e82723e9cc4e
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 08/05/2020
ms.locfileid: "87781423"
---
# <a name="groupby-element-for-view-format"></a><span data-ttu-id="2042f-102">Het element GroupBy voor Weergave (opmaak)</span><span class="sxs-lookup"><span data-stu-id="2042f-102">GroupBy Element for View (Format)</span></span>

<span data-ttu-id="2042f-103">Hiermee wordt gedefinieerd hoe een nieuwe groep objecten wordt weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="2042f-103">Defines how a new group of objects is displayed.</span></span> <span data-ttu-id="2042f-104">Dit element wordt gebruikt bij het definiëren van een tabel, lijst, breed of aangepaste beheer weergave.</span><span class="sxs-lookup"><span data-stu-id="2042f-104">This element is used when defining a table, list, wide, or custom control view.</span></span>

<span data-ttu-id="2042f-105">Configuratie-element (indeling) ViewDefinitions element (indeling) element voor weer gave (indeling) GroupBy-element (indeling)</span><span class="sxs-lookup"><span data-stu-id="2042f-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) GroupBy Element for View (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="2042f-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="2042f-106">Syntax</span></span>

```xml
<GroupBy>
  <PropertyName>.NetTypeProperty</PropertyName>
  <ScriptBlock>ScriptToEvaluate</ScriptBlock>
  <Label>TextToDisplay</Label>
  <CustomControl>...</CustomControl>
  <CustomControlName>NameOfControl</CustomControlName>
</GroupBy>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="2042f-107">Kenmerken en elementen</span><span class="sxs-lookup"><span data-stu-id="2042f-107">Attributes and Elements</span></span>

<span data-ttu-id="2042f-108">In de volgende secties worden kenmerken, onderliggende elementen en bovenliggende elementen beschreven.</span><span class="sxs-lookup"><span data-stu-id="2042f-108">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="2042f-109">Kenmerken</span><span class="sxs-lookup"><span data-stu-id="2042f-109">Attributes</span></span>

<span data-ttu-id="2042f-110">Geen.</span><span class="sxs-lookup"><span data-stu-id="2042f-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="2042f-111">Onderliggende elementen</span><span class="sxs-lookup"><span data-stu-id="2042f-111">Child Elements</span></span>

|<span data-ttu-id="2042f-112">Element</span><span class="sxs-lookup"><span data-stu-id="2042f-112">Element</span></span>|<span data-ttu-id="2042f-113">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="2042f-113">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="2042f-114">Het element CustomControl voor GroupBy (opmaak)</span><span class="sxs-lookup"><span data-stu-id="2042f-114">CustomControl Element for GroupBy (Format)</span></span>](./customcontrol-element-for-groupby-format.md)|<span data-ttu-id="2042f-115">Optioneel element.</span><span class="sxs-lookup"><span data-stu-id="2042f-115">Optional element.</span></span><br /><br /> <span data-ttu-id="2042f-116">Hiermee definieert u het aangepaste besturings element waarmee nieuwe groepen worden weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="2042f-116">Defines the custom control that display new groups.</span></span>|
|[<span data-ttu-id="2042f-117">Het element CustomControlName voor GroupBy (opmaak)</span><span class="sxs-lookup"><span data-stu-id="2042f-117">CustomControlName Element for GroupBy (Format)</span></span>](./customcontrolname-element-for-groupby-format.md)|<span data-ttu-id="2042f-118">Optioneel element.</span><span class="sxs-lookup"><span data-stu-id="2042f-118">Optional element.</span></span><br /><br /> <span data-ttu-id="2042f-119">Hiermee geeft u de naam op van een besturings element dat wordt gebruikt om de nieuwe groep weer te geven.</span><span class="sxs-lookup"><span data-stu-id="2042f-119">Specifies the name of a control that is used to display the new group.</span></span>|
|[<span data-ttu-id="2042f-120">Het element Label voor GroupBy (opmaak)</span><span class="sxs-lookup"><span data-stu-id="2042f-120">Label Element for GroupBy (Format)</span></span>](./label-element-for-groupby-format.md)|<span data-ttu-id="2042f-121">Optioneel element.</span><span class="sxs-lookup"><span data-stu-id="2042f-121">Optional element.</span></span><br /><br /> <span data-ttu-id="2042f-122">Hiermee geeft u een label op dat wordt weer gegeven wanneer een nieuwe groep wordt aangetroffen.</span><span class="sxs-lookup"><span data-stu-id="2042f-122">Specifies a label that is displayed when a new group is encountered.</span></span>|
|[<span data-ttu-id="2042f-123">Het element PropertyName voor GroupBy (opmaak)</span><span class="sxs-lookup"><span data-stu-id="2042f-123">PropertyName Element for GroupBy (Format)</span></span>](./propertyname-element-for-groupby-format.md)|<span data-ttu-id="2042f-124">Optioneel element.</span><span class="sxs-lookup"><span data-stu-id="2042f-124">Optional element.</span></span><br /><br /> <span data-ttu-id="2042f-125">Hiermee geeft u de .NET-eigenschap op waarmee een nieuwe groep wordt gestart wanneer de waarde wordt gewijzigd.</span><span class="sxs-lookup"><span data-stu-id="2042f-125">Specifies the .NET property the starts a new group whenever its value changes.</span></span>|
|[<span data-ttu-id="2042f-126">Het element ScriptBlock voor GroupBy (opmaak)</span><span class="sxs-lookup"><span data-stu-id="2042f-126">ScriptBlock Element for GroupBy (Format)</span></span>](./scriptblock-element-for-groupby-format.md)|<span data-ttu-id="2042f-127">Optioneel element.</span><span class="sxs-lookup"><span data-stu-id="2042f-127">Optional element.</span></span><br /><br /> <span data-ttu-id="2042f-128">Hiermee geeft u het script op waarmee een nieuwe groep wordt gestart wanneer de waarde ervan wordt gewijzigd.</span><span class="sxs-lookup"><span data-stu-id="2042f-128">Specifies the script that starts a new group whenever its value changes.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="2042f-129">Bovenliggende elementen</span><span class="sxs-lookup"><span data-stu-id="2042f-129">Parent Elements</span></span>

|<span data-ttu-id="2042f-130">Element</span><span class="sxs-lookup"><span data-stu-id="2042f-130">Element</span></span>|<span data-ttu-id="2042f-131">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="2042f-131">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="2042f-132">Het element Weergave (opmaak)</span><span class="sxs-lookup"><span data-stu-id="2042f-132">View Element (Format)</span></span>](./view-element-format.md)|<span data-ttu-id="2042f-133">Hiermee wordt een weer gave gedefinieerd waarin een of meer .NET-objecten worden weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="2042f-133">Defines a view that displays one or more .NET objects.</span></span>|

## <a name="remarks"></a><span data-ttu-id="2042f-134">Opmerkingen</span><span class="sxs-lookup"><span data-stu-id="2042f-134">Remarks</span></span>

<span data-ttu-id="2042f-135">Wanneer u definieert hoe een nieuwe groep objecten wordt weer gegeven, moet u de eigenschap of het script opgeven waarmee de nieuwe groep wordt gestart. u kunt echter niet beide opgeven.</span><span class="sxs-lookup"><span data-stu-id="2042f-135">When defining how a new group of objects is displayed, you must specify the property or script that will start the new group; however, you cannot specify both.</span></span>

## <a name="see-also"></a><span data-ttu-id="2042f-136">Zie ook</span><span class="sxs-lookup"><span data-stu-id="2042f-136">See Also</span></span>

[<span data-ttu-id="2042f-137">Het element CustomControlName voor GroupBy (opmaak)</span><span class="sxs-lookup"><span data-stu-id="2042f-137">CustomControlName Element for GroupBy (Format)</span></span>](./customcontrolname-element-for-groupby-format.md)

[<span data-ttu-id="2042f-138">Het element Label voor GroupBy (opmaak)</span><span class="sxs-lookup"><span data-stu-id="2042f-138">Label Element for GroupBy (Format)</span></span>](./label-element-for-groupby-format.md)

[<span data-ttu-id="2042f-139">Het element PropertyName voor GroupBy (opmaak)</span><span class="sxs-lookup"><span data-stu-id="2042f-139">PropertyName Element for GroupBy (Format)</span></span>](./propertyname-element-for-groupby-format.md)

[<span data-ttu-id="2042f-140">Het element ScriptBlock voor GroupBy (opmaak)</span><span class="sxs-lookup"><span data-stu-id="2042f-140">ScriptBlock Element for GroupBy (Format)</span></span>](./scriptblock-element-for-groupby-format.md)

[<span data-ttu-id="2042f-141">Het element Weergave (opmaak)</span><span class="sxs-lookup"><span data-stu-id="2042f-141">View Element (Format)</span></span>](./view-element-format.md)

[<span data-ttu-id="2042f-142">Een PowerShell-opmaakbestand schrijven</span><span class="sxs-lookup"><span data-stu-id="2042f-142">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
