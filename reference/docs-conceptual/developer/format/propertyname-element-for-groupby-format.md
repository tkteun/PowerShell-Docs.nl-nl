---
title: PropertyName-element voor GroupBy (indeling) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: ddcecc46-ac75-43fa-b03a-802a68524ec3
caps.latest.revision: 10
ms.openlocfilehash: da6ac5abe7acbbee8f57b3e81529664f81800b86
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 12/05/2019
ms.locfileid: "72354185"
---
# <a name="propertyname-element-for-groupby-format"></a><span data-ttu-id="037d6-102">Het element PropertyName voor GroupBy (opmaak)</span><span class="sxs-lookup"><span data-stu-id="037d6-102">PropertyName Element for GroupBy (Format)</span></span>

<span data-ttu-id="037d6-103">Hiermee geeft u de .NET-eigenschap op waarmee een nieuwe groep wordt gestart wanneer de waarde ervan wordt gewijzigd.</span><span class="sxs-lookup"><span data-stu-id="037d6-103">Specifies the .NET property that starts a new group whenever its value changes.</span></span>

<span data-ttu-id="037d6-104">Configuratie-element (indeling) ViewDefinitions element (indeling) element voor weer gave (indeling) GroupBy-element (Format) voor de eigenschap element van de weer gave (indeling) voor GroupBy (indeling)</span><span class="sxs-lookup"><span data-stu-id="037d6-104">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) GroupBy Element for View (Format) PropertyName Element for GroupBy (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="037d6-105">Syntaxis</span><span class="sxs-lookup"><span data-stu-id="037d6-105">Syntax</span></span>

```xml
<PropertyName>.NetTypeProperty</PropertyName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="037d6-106">Kenmerken en elementen</span><span class="sxs-lookup"><span data-stu-id="037d6-106">Attributes and Elements</span></span>

<span data-ttu-id="037d6-107">In de volgende secties worden kenmerken, onderliggende elementen en het bovenliggende element van het element `PropertyName` beschreven.</span><span class="sxs-lookup"><span data-stu-id="037d6-107">The following sections describe attributes, child elements, and the parent element of the `PropertyName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="037d6-108">Kenmerken</span><span class="sxs-lookup"><span data-stu-id="037d6-108">Attributes</span></span>

<span data-ttu-id="037d6-109">Geen.</span><span class="sxs-lookup"><span data-stu-id="037d6-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="037d6-110">Onderliggende elementen</span><span class="sxs-lookup"><span data-stu-id="037d6-110">Child Elements</span></span>

<span data-ttu-id="037d6-111">Geen.</span><span class="sxs-lookup"><span data-stu-id="037d6-111">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="037d6-112">Bovenliggende elementen</span><span class="sxs-lookup"><span data-stu-id="037d6-112">Parent Elements</span></span>

|<span data-ttu-id="037d6-113">Element</span><span class="sxs-lookup"><span data-stu-id="037d6-113">Element</span></span>|<span data-ttu-id="037d6-114">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="037d6-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="037d6-115">Element GroupBy voor weer gave (indeling)</span><span class="sxs-lookup"><span data-stu-id="037d6-115">GroupBy Element for View (Format)</span></span>](./groupby-element-for-view-format.md)|<span data-ttu-id="037d6-116">Hiermee definieert u hoe een groep .NET-objecten wordt weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="037d6-116">Defines how a group of .NET objects is displayed.</span></span>|

## <a name="text-value"></a><span data-ttu-id="037d6-117">Tekstwaarde</span><span class="sxs-lookup"><span data-stu-id="037d6-117">Text Value</span></span>

<span data-ttu-id="037d6-118">Geef de .NET-eigenschaps naam op.</span><span class="sxs-lookup"><span data-stu-id="037d6-118">Specify the .NET property name.</span></span>

## <a name="remarks"></a><span data-ttu-id="037d6-119">Opmerkingen</span><span class="sxs-lookup"><span data-stu-id="037d6-119">Remarks</span></span>

<span data-ttu-id="037d6-120">Windows Power shell start een nieuwe groep wanneer de waarde van deze eigenschap wordt gewijzigd.</span><span class="sxs-lookup"><span data-stu-id="037d6-120">Windows PowerShell starts a new group whenever the value of this property changes.</span></span>

<span data-ttu-id="037d6-121">Als dit element is opgegeven, kunt u het [script Block](./scriptblock-element-for-groupby-format.md) -element niet opgeven om een nieuwe groep te starten.</span><span class="sxs-lookup"><span data-stu-id="037d6-121">When this element is specified, you cannot specify the [ScriptBlock](./scriptblock-element-for-groupby-format.md) element to start a new group.</span></span>

## <a name="example"></a><span data-ttu-id="037d6-122">Voorbeeld</span><span class="sxs-lookup"><span data-stu-id="037d6-122">Example</span></span>

<span data-ttu-id="037d6-123">In het volgende voor beeld ziet u hoe u een nieuwe groep kunt starten wanneer de waarde van een eigenschap wordt gewijzigd.</span><span class="sxs-lookup"><span data-stu-id="037d6-123">The following example shows how to start a new group when the value of a property changes.</span></span>

```xml
<GroupBy>
  <Label>Service Type</Label>
  <PropertyName>ServiceType</PropertyName>
</GroupBy>

```

<span data-ttu-id="037d6-124">Zie [Wide View (GroupBy)](./wide-view-groupby.md)voor een voor beeld van een volledig indelings bestand dat dit element bevat.</span><span class="sxs-lookup"><span data-stu-id="037d6-124">For an example of a complete formatting file that includes this element, see [Wide View (GroupBy)](./wide-view-groupby.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="037d6-125">Zie ook</span><span class="sxs-lookup"><span data-stu-id="037d6-125">See Also</span></span>

[<span data-ttu-id="037d6-126">Element GroupBy voor weer gave (indeling)</span><span class="sxs-lookup"><span data-stu-id="037d6-126">GroupBy Element for View (Format)</span></span>](./groupby-element-for-view-format.md)

[<span data-ttu-id="037d6-127">Script block-element voor GroupBy (indeling)</span><span class="sxs-lookup"><span data-stu-id="037d6-127">ScriptBlock Element for GroupBy (Format)</span></span>](./scriptblock-element-for-groupby-format.md)

[<span data-ttu-id="037d6-128">Een Power shell-indelings bestand schrijven</span><span class="sxs-lookup"><span data-stu-id="037d6-128">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
