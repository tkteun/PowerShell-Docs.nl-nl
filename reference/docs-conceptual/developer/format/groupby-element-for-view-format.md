---
ms.date: 09/13/2016
ms.topic: reference
title: Het element GroupBy voor Weergave (opmaak)
description: Het element GroupBy voor Weergave (opmaak)
ms.openlocfilehash: d8ca93a3b2c1490928885579919c07f5eb274cd8
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/27/2020
ms.locfileid: "92652101"
---
# <a name="groupby-element-for-view-format"></a><span data-ttu-id="c1c4d-103">Het element GroupBy voor Weergave (opmaak)</span><span class="sxs-lookup"><span data-stu-id="c1c4d-103">GroupBy Element for View (Format)</span></span>

<span data-ttu-id="c1c4d-104">Hiermee wordt gedefinieerd hoe een nieuwe groep objecten wordt weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="c1c4d-104">Defines how a new group of objects is displayed.</span></span> <span data-ttu-id="c1c4d-105">Dit element wordt gebruikt bij het definiëren van een tabel, lijst, breed of aangepaste beheer weergave.</span><span class="sxs-lookup"><span data-stu-id="c1c4d-105">This element is used when defining a table, list, wide, or custom control view.</span></span>

<span data-ttu-id="c1c4d-106">Configuratie-element (indeling) ViewDefinitions element (indeling) element voor weer gave (indeling) GroupBy-element (indeling)</span><span class="sxs-lookup"><span data-stu-id="c1c4d-106">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) GroupBy Element for View (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="c1c4d-107">Syntax</span><span class="sxs-lookup"><span data-stu-id="c1c4d-107">Syntax</span></span>

```xml
<GroupBy>
  <PropertyName>.NetTypeProperty</PropertyName>
  <ScriptBlock>ScriptToEvaluate</ScriptBlock>
  <Label>TextToDisplay</Label>
  <CustomControl>...</CustomControl>
  <CustomControlName>NameOfControl</CustomControlName>
</GroupBy>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="c1c4d-108">Kenmerken en elementen</span><span class="sxs-lookup"><span data-stu-id="c1c4d-108">Attributes and Elements</span></span>

<span data-ttu-id="c1c4d-109">In de volgende secties worden kenmerken, onderliggende elementen en bovenliggende elementen beschreven.</span><span class="sxs-lookup"><span data-stu-id="c1c4d-109">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="c1c4d-110">Kenmerken</span><span class="sxs-lookup"><span data-stu-id="c1c4d-110">Attributes</span></span>

<span data-ttu-id="c1c4d-111">Geen.</span><span class="sxs-lookup"><span data-stu-id="c1c4d-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="c1c4d-112">Onderliggende elementen</span><span class="sxs-lookup"><span data-stu-id="c1c4d-112">Child Elements</span></span>

|<span data-ttu-id="c1c4d-113">Element</span><span class="sxs-lookup"><span data-stu-id="c1c4d-113">Element</span></span>|<span data-ttu-id="c1c4d-114">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="c1c4d-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="c1c4d-115">Het element CustomControl voor GroupBy (opmaak)</span><span class="sxs-lookup"><span data-stu-id="c1c4d-115">CustomControl Element for GroupBy (Format)</span></span>](./customcontrol-element-for-groupby-format.md)|<span data-ttu-id="c1c4d-116">Optioneel element.</span><span class="sxs-lookup"><span data-stu-id="c1c4d-116">Optional element.</span></span><br /><br /> <span data-ttu-id="c1c4d-117">Hiermee definieert u het aangepaste besturings element waarmee nieuwe groepen worden weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="c1c4d-117">Defines the custom control that display new groups.</span></span>|
|[<span data-ttu-id="c1c4d-118">Het element CustomControlName voor GroupBy (opmaak)</span><span class="sxs-lookup"><span data-stu-id="c1c4d-118">CustomControlName Element for GroupBy (Format)</span></span>](./customcontrolname-element-for-groupby-format.md)|<span data-ttu-id="c1c4d-119">Optioneel element.</span><span class="sxs-lookup"><span data-stu-id="c1c4d-119">Optional element.</span></span><br /><br /> <span data-ttu-id="c1c4d-120">Hiermee geeft u de naam op van een besturings element dat wordt gebruikt om de nieuwe groep weer te geven.</span><span class="sxs-lookup"><span data-stu-id="c1c4d-120">Specifies the name of a control that is used to display the new group.</span></span>|
|[<span data-ttu-id="c1c4d-121">Het element Label voor GroupBy (opmaak)</span><span class="sxs-lookup"><span data-stu-id="c1c4d-121">Label Element for GroupBy (Format)</span></span>](./label-element-for-groupby-format.md)|<span data-ttu-id="c1c4d-122">Optioneel element.</span><span class="sxs-lookup"><span data-stu-id="c1c4d-122">Optional element.</span></span><br /><br /> <span data-ttu-id="c1c4d-123">Hiermee geeft u een label op dat wordt weer gegeven wanneer een nieuwe groep wordt aangetroffen.</span><span class="sxs-lookup"><span data-stu-id="c1c4d-123">Specifies a label that is displayed when a new group is encountered.</span></span>|
|[<span data-ttu-id="c1c4d-124">Het element PropertyName voor GroupBy (opmaak)</span><span class="sxs-lookup"><span data-stu-id="c1c4d-124">PropertyName Element for GroupBy (Format)</span></span>](./propertyname-element-for-groupby-format.md)|<span data-ttu-id="c1c4d-125">Optioneel element.</span><span class="sxs-lookup"><span data-stu-id="c1c4d-125">Optional element.</span></span><br /><br /> <span data-ttu-id="c1c4d-126">Hiermee geeft u de .NET-eigenschap op waarmee een nieuwe groep wordt gestart wanneer de waarde wordt gewijzigd.</span><span class="sxs-lookup"><span data-stu-id="c1c4d-126">Specifies the .NET property the starts a new group whenever its value changes.</span></span>|
|[<span data-ttu-id="c1c4d-127">Het element ScriptBlock voor GroupBy (opmaak)</span><span class="sxs-lookup"><span data-stu-id="c1c4d-127">ScriptBlock Element for GroupBy (Format)</span></span>](./scriptblock-element-for-groupby-format.md)|<span data-ttu-id="c1c4d-128">Optioneel element.</span><span class="sxs-lookup"><span data-stu-id="c1c4d-128">Optional element.</span></span><br /><br /> <span data-ttu-id="c1c4d-129">Hiermee geeft u het script op waarmee een nieuwe groep wordt gestart wanneer de waarde ervan wordt gewijzigd.</span><span class="sxs-lookup"><span data-stu-id="c1c4d-129">Specifies the script that starts a new group whenever its value changes.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="c1c4d-130">Bovenliggende elementen</span><span class="sxs-lookup"><span data-stu-id="c1c4d-130">Parent Elements</span></span>

|<span data-ttu-id="c1c4d-131">Element</span><span class="sxs-lookup"><span data-stu-id="c1c4d-131">Element</span></span>|<span data-ttu-id="c1c4d-132">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="c1c4d-132">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="c1c4d-133">Het element Weergave (opmaak)</span><span class="sxs-lookup"><span data-stu-id="c1c4d-133">View Element (Format)</span></span>](./view-element-format.md)|<span data-ttu-id="c1c4d-134">Hiermee wordt een weer gave gedefinieerd waarin een of meer .NET-objecten worden weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="c1c4d-134">Defines a view that displays one or more .NET objects.</span></span>|

## <a name="remarks"></a><span data-ttu-id="c1c4d-135">Opmerkingen</span><span class="sxs-lookup"><span data-stu-id="c1c4d-135">Remarks</span></span>

<span data-ttu-id="c1c4d-136">Wanneer u definieert hoe een nieuwe groep objecten wordt weer gegeven, moet u de eigenschap of het script opgeven waarmee de nieuwe groep wordt gestart. u kunt echter niet beide opgeven.</span><span class="sxs-lookup"><span data-stu-id="c1c4d-136">When defining how a new group of objects is displayed, you must specify the property or script that will start the new group; however, you cannot specify both.</span></span>

## <a name="see-also"></a><span data-ttu-id="c1c4d-137">Zie ook</span><span class="sxs-lookup"><span data-stu-id="c1c4d-137">See Also</span></span>

[<span data-ttu-id="c1c4d-138">Het element CustomControlName voor GroupBy (opmaak)</span><span class="sxs-lookup"><span data-stu-id="c1c4d-138">CustomControlName Element for GroupBy (Format)</span></span>](./customcontrolname-element-for-groupby-format.md)

[<span data-ttu-id="c1c4d-139">Het element Label voor GroupBy (opmaak)</span><span class="sxs-lookup"><span data-stu-id="c1c4d-139">Label Element for GroupBy (Format)</span></span>](./label-element-for-groupby-format.md)

[<span data-ttu-id="c1c4d-140">Het element PropertyName voor GroupBy (opmaak)</span><span class="sxs-lookup"><span data-stu-id="c1c4d-140">PropertyName Element for GroupBy (Format)</span></span>](./propertyname-element-for-groupby-format.md)

[<span data-ttu-id="c1c4d-141">Het element ScriptBlock voor GroupBy (opmaak)</span><span class="sxs-lookup"><span data-stu-id="c1c4d-141">ScriptBlock Element for GroupBy (Format)</span></span>](./scriptblock-element-for-groupby-format.md)

[<span data-ttu-id="c1c4d-142">Het element Weergave (opmaak)</span><span class="sxs-lookup"><span data-stu-id="c1c4d-142">View Element (Format)</span></span>](./view-element-format.md)

[<span data-ttu-id="c1c4d-143">Een PowerShell-opmaakbestand schrijven</span><span class="sxs-lookup"><span data-stu-id="c1c4d-143">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
