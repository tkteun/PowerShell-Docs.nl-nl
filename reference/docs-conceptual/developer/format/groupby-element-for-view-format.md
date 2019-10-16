---
title: Element GroupBy voor weer gave (indeling) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 67a2b061-2a4a-4ad1-84f9-cdbefb64aaab
caps.latest.revision: 8
ms.openlocfilehash: abb8b91626128b3deaa2db24a9fd8b34a6563410
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/15/2019
ms.locfileid: "72354962"
---
# <a name="groupby-element-for-view-format"></a><span data-ttu-id="7862e-102">Het element GroupBy voor Weergave (opmaak)</span><span class="sxs-lookup"><span data-stu-id="7862e-102">GroupBy Element for View (Format)</span></span>

<span data-ttu-id="7862e-103">Hiermee wordt gedefinieerd hoe een nieuwe groep objecten wordt weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="7862e-103">Defines how a new group of objects is displayed.</span></span> <span data-ttu-id="7862e-104">Dit element wordt gebruikt bij het definiëren van een tabel, lijst, breed of aangepaste beheer weergave.</span><span class="sxs-lookup"><span data-stu-id="7862e-104">This element is used when defining a table, list, wide, or custom control view.</span></span>

<span data-ttu-id="7862e-105">Configuratie-element (indeling) ViewDefinitions element (indeling) element voor weer gave (indeling) GroupBy-element (indeling)</span><span class="sxs-lookup"><span data-stu-id="7862e-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) GroupBy Element for View (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="7862e-106">Syntaxis</span><span class="sxs-lookup"><span data-stu-id="7862e-106">Syntax</span></span>

```xml
<GroupBy>
  <PropertyName>.NetTypeProperty</PropertyName>
  <ScriptBlock>ScriptToEvaluate</ScriptBlock>
  <Label>TextToDisplay</Label>
  <CustomControl>...</CustomControl>
  <CustomControlName>NameOfControl</CustomControlName>
</GroupBy>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="7862e-107">Kenmerken en elementen</span><span class="sxs-lookup"><span data-stu-id="7862e-107">Attributes and Elements</span></span>

<span data-ttu-id="7862e-108">In de volgende secties worden kenmerken, onderliggende elementen en bovenliggende elementen beschreven.</span><span class="sxs-lookup"><span data-stu-id="7862e-108">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="7862e-109">Kenmerken</span><span class="sxs-lookup"><span data-stu-id="7862e-109">Attributes</span></span>

<span data-ttu-id="7862e-110">Geen.</span><span class="sxs-lookup"><span data-stu-id="7862e-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="7862e-111">Onderliggende elementen</span><span class="sxs-lookup"><span data-stu-id="7862e-111">Child Elements</span></span>

|<span data-ttu-id="7862e-112">Element</span><span class="sxs-lookup"><span data-stu-id="7862e-112">Element</span></span>|<span data-ttu-id="7862e-113">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="7862e-113">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="7862e-114">CustomControl-element voor GroupBy (indeling)</span><span class="sxs-lookup"><span data-stu-id="7862e-114">CustomControl Element for GroupBy (Format)</span></span>](./customcontrol-element-for-groupby-format.md)|<span data-ttu-id="7862e-115">Optioneel element.</span><span class="sxs-lookup"><span data-stu-id="7862e-115">Optional element.</span></span><br /><br /> <span data-ttu-id="7862e-116">Hiermee definieert u het aangepaste besturings element waarmee nieuwe groepen worden weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="7862e-116">Defines the custom control that display new groups.</span></span>|
|[<span data-ttu-id="7862e-117">CustomControlName-element voor GroupBy (indeling)</span><span class="sxs-lookup"><span data-stu-id="7862e-117">CustomControlName Element for GroupBy (Format)</span></span>](./customcontrolname-element-for-groupby-format.md)|<span data-ttu-id="7862e-118">Optioneel element.</span><span class="sxs-lookup"><span data-stu-id="7862e-118">Optional element.</span></span><br /><br /> <span data-ttu-id="7862e-119">Hiermee geeft u de naam op van een besturings element dat wordt gebruikt om de nieuwe groep weer te geven.</span><span class="sxs-lookup"><span data-stu-id="7862e-119">Specifies the name of a control that is used to display the new group.</span></span>|
|[<span data-ttu-id="7862e-120">Label element voor GroupBy (indeling)</span><span class="sxs-lookup"><span data-stu-id="7862e-120">Label Element for GroupBy (Format)</span></span>](./label-element-for-groupby-format.md)|<span data-ttu-id="7862e-121">Optioneel element.</span><span class="sxs-lookup"><span data-stu-id="7862e-121">Optional element.</span></span><br /><br /> <span data-ttu-id="7862e-122">Hiermee geeft u een label op dat wordt weer gegeven wanneer een nieuwe groep wordt aangetroffen.</span><span class="sxs-lookup"><span data-stu-id="7862e-122">Specifies a label that is displayed when a new group is encountered.</span></span>|
|[<span data-ttu-id="7862e-123">PropertyName-element voor GroupBy (indeling)</span><span class="sxs-lookup"><span data-stu-id="7862e-123">PropertyName Element for GroupBy (Format)</span></span>](./propertyname-element-for-groupby-format.md)|<span data-ttu-id="7862e-124">Optioneel element.</span><span class="sxs-lookup"><span data-stu-id="7862e-124">Optional element.</span></span><br /><br /> <span data-ttu-id="7862e-125">Hiermee geeft u de .NET-eigenschap op waarmee een nieuwe groep wordt gestart wanneer de waarde wordt gewijzigd.</span><span class="sxs-lookup"><span data-stu-id="7862e-125">Specifies the .NET property the starts a new group whenever its value changes.</span></span>|
|[<span data-ttu-id="7862e-126">Script block-element voor GroupBy (indeling)</span><span class="sxs-lookup"><span data-stu-id="7862e-126">ScriptBlock Element for GroupBy (Format)</span></span>](./scriptblock-element-for-groupby-format.md)|<span data-ttu-id="7862e-127">Optioneel element.</span><span class="sxs-lookup"><span data-stu-id="7862e-127">Optional element.</span></span><br /><br /> <span data-ttu-id="7862e-128">Hiermee geeft u het script op waarmee een nieuwe groep wordt gestart wanneer de waarde ervan wordt gewijzigd.</span><span class="sxs-lookup"><span data-stu-id="7862e-128">Specifies the script that starts a new group whenever its value changes.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="7862e-129">Bovenliggende elementen</span><span class="sxs-lookup"><span data-stu-id="7862e-129">Parent Elements</span></span>

|<span data-ttu-id="7862e-130">Element</span><span class="sxs-lookup"><span data-stu-id="7862e-130">Element</span></span>|<span data-ttu-id="7862e-131">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="7862e-131">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="7862e-132">Element weer geven (indeling)</span><span class="sxs-lookup"><span data-stu-id="7862e-132">View Element (Format)</span></span>](./view-element-format.md)|<span data-ttu-id="7862e-133">Hiermee wordt een weer gave gedefinieerd waarin een of meer .NET-objecten worden weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="7862e-133">Defines a view that displays one or more .NET objects.</span></span>|

## <a name="remarks"></a><span data-ttu-id="7862e-134">Opmerkingen</span><span class="sxs-lookup"><span data-stu-id="7862e-134">Remarks</span></span>

<span data-ttu-id="7862e-135">Wanneer u definieert hoe een nieuwe groep objecten wordt weer gegeven, moet u de eigenschap of het script opgeven waarmee de nieuwe groep wordt gestart. u kunt echter niet beide opgeven.</span><span class="sxs-lookup"><span data-stu-id="7862e-135">When defining how a new group of objects is displayed, you must specify the property or script that will start the new group; however, you cannot specify both.</span></span>

## <a name="see-also"></a><span data-ttu-id="7862e-136">Zie ook</span><span class="sxs-lookup"><span data-stu-id="7862e-136">See Also</span></span>

[<span data-ttu-id="7862e-137">CustomControlName-element voor GroupBy (indeling)</span><span class="sxs-lookup"><span data-stu-id="7862e-137">CustomControlName Element for GroupBy (Format)</span></span>](./customcontrolname-element-for-groupby-format.md)

[<span data-ttu-id="7862e-138">Label element voor GroupBy (indeling)</span><span class="sxs-lookup"><span data-stu-id="7862e-138">Label Element for GroupBy (Format)</span></span>](./label-element-for-groupby-format.md)

[<span data-ttu-id="7862e-139">PropertyName-element voor GroupBy (indeling)</span><span class="sxs-lookup"><span data-stu-id="7862e-139">PropertyName Element for GroupBy (Format)</span></span>](./propertyname-element-for-groupby-format.md)

[<span data-ttu-id="7862e-140">Script block-element voor GroupBy (indeling)</span><span class="sxs-lookup"><span data-stu-id="7862e-140">ScriptBlock Element for GroupBy (Format)</span></span>](./scriptblock-element-for-groupby-format.md)

[<span data-ttu-id="7862e-141">Element weer geven (indeling)</span><span class="sxs-lookup"><span data-stu-id="7862e-141">View Element (Format)</span></span>](./view-element-format.md)

[<span data-ttu-id="7862e-142">Een Power shell-indelings bestand schrijven</span><span class="sxs-lookup"><span data-stu-id="7862e-142">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
