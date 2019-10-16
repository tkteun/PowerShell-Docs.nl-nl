---
title: Label element voor GroupBy (indeling) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 3351d237-e8c2-4ec5-9500-4eceadb407c2
caps.latest.revision: 11
ms.openlocfilehash: e7158711c60d13c745bbdfab9b1b9fc7d98b34e2
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/15/2019
ms.locfileid: "72356061"
---
# <a name="label-element-for-groupby-format"></a><span data-ttu-id="2663d-102">Het element Label voor GroupBy (opmaak)</span><span class="sxs-lookup"><span data-stu-id="2663d-102">Label Element for GroupBy (Format)</span></span>

<span data-ttu-id="2663d-103">Hiermee geeft u een label op dat wordt weer gegeven wanneer een nieuwe groep wordt aangetroffen.</span><span class="sxs-lookup"><span data-stu-id="2663d-103">Specifies a label that is displayed when a new group is encountered.</span></span>

<span data-ttu-id="2663d-104">Configuratie-element (indeling) ViewDefinitions element (indeling) element weer geven (indeling) GroupBy-element voor weer gave (indeling) label element voor GroupBy (indeling)</span><span class="sxs-lookup"><span data-stu-id="2663d-104">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) GroupBy Element for View (Format) Label Element for GroupBy (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="2663d-105">Syntaxis</span><span class="sxs-lookup"><span data-stu-id="2663d-105">Syntax</span></span>

```xml
<Label>DisplayedLabel</Label>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="2663d-106">Kenmerken en elementen</span><span class="sxs-lookup"><span data-stu-id="2663d-106">Attributes and Elements</span></span>

<span data-ttu-id="2663d-107">In de volgende secties worden de kenmerken, onderliggende elementen en het bovenliggende element van het element `Label` beschreven.</span><span class="sxs-lookup"><span data-stu-id="2663d-107">The following sections describe the attributes, child elements, and parent element of the `Label` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="2663d-108">Kenmerken</span><span class="sxs-lookup"><span data-stu-id="2663d-108">Attributes</span></span>

<span data-ttu-id="2663d-109">Geen.</span><span class="sxs-lookup"><span data-stu-id="2663d-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="2663d-110">Onderliggende elementen</span><span class="sxs-lookup"><span data-stu-id="2663d-110">Child Elements</span></span>

<span data-ttu-id="2663d-111">Geen.</span><span class="sxs-lookup"><span data-stu-id="2663d-111">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="2663d-112">Bovenliggende elementen</span><span class="sxs-lookup"><span data-stu-id="2663d-112">Parent Elements</span></span>

|<span data-ttu-id="2663d-113">Element</span><span class="sxs-lookup"><span data-stu-id="2663d-113">Element</span></span>|<span data-ttu-id="2663d-114">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="2663d-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="2663d-115">Element GroupBy voor weer gave (indeling)</span><span class="sxs-lookup"><span data-stu-id="2663d-115">GroupBy Element for View (Format)</span></span>](./groupby-element-for-view-format.md)|<span data-ttu-id="2663d-116">Hiermee wordt gedefinieerd hoe een nieuwe groep objecten wordt weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="2663d-116">Defines how a new group of objects is displayed.</span></span>|

## <a name="text-value"></a><span data-ttu-id="2663d-117">Tekst waarde</span><span class="sxs-lookup"><span data-stu-id="2663d-117">Text Value</span></span>

<span data-ttu-id="2663d-118">Geef de tekst op die wordt weer gegeven wanneer in Windows Power shell een nieuwe eigenschap of script waarde wordt aangetroffen.</span><span class="sxs-lookup"><span data-stu-id="2663d-118">Specify the text that is displayed whenever Windows PowerShell encounters a new property or script value.</span></span>

## <a name="remarks"></a><span data-ttu-id="2663d-119">Opmerkingen</span><span class="sxs-lookup"><span data-stu-id="2663d-119">Remarks</span></span>

<span data-ttu-id="2663d-120">Naast de tekst die door dit element is opgegeven, wordt in Windows Power shell de nieuwe waarde weer gegeven waarmee de groep wordt gestart en wordt een lege regel voor en na de groep toegevoegd.</span><span class="sxs-lookup"><span data-stu-id="2663d-120">In addition to the text specified by this element, Windows PowerShell displays the new value that starts the group, and adds a blank line before and after the group.</span></span>

## <a name="example"></a><span data-ttu-id="2663d-121">Voorbeeld</span><span class="sxs-lookup"><span data-stu-id="2663d-121">Example</span></span>

<span data-ttu-id="2663d-122">In het volgende voor beeld ziet u het label voor een nieuwe groep.</span><span class="sxs-lookup"><span data-stu-id="2663d-122">The following example shows the label for a new group.</span></span> <span data-ttu-id="2663d-123">Het weer gegeven label ziet er ongeveer als volgt uit: `Service Type: NewValueofProperty`</span><span class="sxs-lookup"><span data-stu-id="2663d-123">The displayed label would look similar to this: `Service Type: NewValueofProperty`</span></span>

```xml
<GroupBy>
  <Label>Service Type</Label>
  <PropertyName>ServiceType</PropertyName>
</GroupBy>

```

<span data-ttu-id="2663d-124">Zie [Wide View (GroupBy)](./wide-view-groupby.md)voor een voor beeld van een volledig indelings bestand dat dit element bevat.</span><span class="sxs-lookup"><span data-stu-id="2663d-124">For an example of a complete formatting file that includes this element, see [Wide View (GroupBy)](./wide-view-groupby.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="2663d-125">Zie ook</span><span class="sxs-lookup"><span data-stu-id="2663d-125">See Also</span></span>

[<span data-ttu-id="2663d-126">Element GroupBy voor weer gave (indeling)</span><span class="sxs-lookup"><span data-stu-id="2663d-126">GroupBy Element for View (Format)</span></span>](./groupby-element-for-view-format.md)

[<span data-ttu-id="2663d-127">Een Power shell-indelings bestand schrijven</span><span class="sxs-lookup"><span data-stu-id="2663d-127">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
