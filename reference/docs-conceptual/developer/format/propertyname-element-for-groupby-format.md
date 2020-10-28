---
ms.date: 09/13/2016
ms.topic: reference
title: Het element PropertyName voor GroupBy (opmaak)
description: Het element PropertyName voor GroupBy (opmaak)
ms.openlocfilehash: 44351c46ff2386f967644fef4f423b3858dc1619
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/27/2020
ms.locfileid: "92666141"
---
# <a name="propertyname-element-for-groupby-format"></a><span data-ttu-id="b1397-103">Het element PropertyName voor GroupBy (opmaak)</span><span class="sxs-lookup"><span data-stu-id="b1397-103">PropertyName Element for GroupBy (Format)</span></span>

<span data-ttu-id="b1397-104">Hiermee geeft u de .NET-eigenschap op waarmee een nieuwe groep wordt gestart wanneer de waarde ervan wordt gewijzigd.</span><span class="sxs-lookup"><span data-stu-id="b1397-104">Specifies the .NET property that starts a new group whenever its value changes.</span></span>

<span data-ttu-id="b1397-105">Configuratie-element (indeling) ViewDefinitions element (indeling) element voor weer gave (indeling) GroupBy-element (Format) voor de eigenschap element van de weer gave (indeling) voor GroupBy (indeling)</span><span class="sxs-lookup"><span data-stu-id="b1397-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) GroupBy Element for View (Format) PropertyName Element for GroupBy (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="b1397-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="b1397-106">Syntax</span></span>

```xml
<PropertyName>.NetTypeProperty</PropertyName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="b1397-107">Kenmerken en elementen</span><span class="sxs-lookup"><span data-stu-id="b1397-107">Attributes and Elements</span></span>

<span data-ttu-id="b1397-108">In de volgende secties worden kenmerken, onderliggende elementen en het bovenliggende element van het `PropertyName` element beschreven.</span><span class="sxs-lookup"><span data-stu-id="b1397-108">The following sections describe attributes, child elements, and the parent element of the `PropertyName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="b1397-109">Kenmerken</span><span class="sxs-lookup"><span data-stu-id="b1397-109">Attributes</span></span>

<span data-ttu-id="b1397-110">Geen.</span><span class="sxs-lookup"><span data-stu-id="b1397-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="b1397-111">Onderliggende elementen</span><span class="sxs-lookup"><span data-stu-id="b1397-111">Child Elements</span></span>

<span data-ttu-id="b1397-112">Geen.</span><span class="sxs-lookup"><span data-stu-id="b1397-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="b1397-113">Bovenliggende elementen</span><span class="sxs-lookup"><span data-stu-id="b1397-113">Parent Elements</span></span>

|<span data-ttu-id="b1397-114">Element</span><span class="sxs-lookup"><span data-stu-id="b1397-114">Element</span></span>|<span data-ttu-id="b1397-115">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="b1397-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="b1397-116">Het element GroupBy voor Weergave (opmaak)</span><span class="sxs-lookup"><span data-stu-id="b1397-116">GroupBy Element for View (Format)</span></span>](./groupby-element-for-view-format.md)|<span data-ttu-id="b1397-117">Hiermee definieert u hoe een groep .NET-objecten wordt weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="b1397-117">Defines how a group of .NET objects is displayed.</span></span>|

## <a name="text-value"></a><span data-ttu-id="b1397-118">Tekstwaarde</span><span class="sxs-lookup"><span data-stu-id="b1397-118">Text Value</span></span>

<span data-ttu-id="b1397-119">Geef de .NET-eigenschaps naam op.</span><span class="sxs-lookup"><span data-stu-id="b1397-119">Specify the .NET property name.</span></span>

## <a name="remarks"></a><span data-ttu-id="b1397-120">Opmerkingen</span><span class="sxs-lookup"><span data-stu-id="b1397-120">Remarks</span></span>

<span data-ttu-id="b1397-121">Windows Power shell start een nieuwe groep wanneer de waarde van deze eigenschap wordt gewijzigd.</span><span class="sxs-lookup"><span data-stu-id="b1397-121">Windows PowerShell starts a new group whenever the value of this property changes.</span></span>

<span data-ttu-id="b1397-122">Als dit element is opgegeven, kunt u het [script Block](./scriptblock-element-for-groupby-format.md) -element niet opgeven om een nieuwe groep te starten.</span><span class="sxs-lookup"><span data-stu-id="b1397-122">When this element is specified, you cannot specify the [ScriptBlock](./scriptblock-element-for-groupby-format.md) element to start a new group.</span></span>

## <a name="example"></a><span data-ttu-id="b1397-123">Voorbeeld</span><span class="sxs-lookup"><span data-stu-id="b1397-123">Example</span></span>

<span data-ttu-id="b1397-124">In het volgende voor beeld ziet u hoe u een nieuwe groep kunt starten wanneer de waarde van een eigenschap wordt gewijzigd.</span><span class="sxs-lookup"><span data-stu-id="b1397-124">The following example shows how to start a new group when the value of a property changes.</span></span>

```xml
<GroupBy>
  <Label>Service Type</Label>
  <PropertyName>ServiceType</PropertyName>
</GroupBy>

```

<span data-ttu-id="b1397-125">Zie [Wide View (GroupBy)](./wide-view-groupby.md)voor een voor beeld van een volledig indelings bestand dat dit element bevat.</span><span class="sxs-lookup"><span data-stu-id="b1397-125">For an example of a complete formatting file that includes this element, see [Wide View (GroupBy)](./wide-view-groupby.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="b1397-126">Zie ook</span><span class="sxs-lookup"><span data-stu-id="b1397-126">See Also</span></span>

[<span data-ttu-id="b1397-127">Het element GroupBy voor Weergave (opmaak)</span><span class="sxs-lookup"><span data-stu-id="b1397-127">GroupBy Element for View (Format)</span></span>](./groupby-element-for-view-format.md)

[<span data-ttu-id="b1397-128">Het element ScriptBlock voor GroupBy (opmaak)</span><span class="sxs-lookup"><span data-stu-id="b1397-128">ScriptBlock Element for GroupBy (Format)</span></span>](./scriptblock-element-for-groupby-format.md)

[<span data-ttu-id="b1397-129">Een PowerShell-opmaakbestand schrijven</span><span class="sxs-lookup"><span data-stu-id="b1397-129">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
