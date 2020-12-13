---
ms.date: 09/13/2016
ms.topic: reference
title: Het element Label voor GroupBy (opmaak)
description: Het element Label voor GroupBy (opmaak)
ms.openlocfilehash: ff4b0dec01bb5b472b1813540661791b91568eed
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 12/10/2020
ms.locfileid: "92649789"
---
# <a name="label-element-for-groupby-format"></a><span data-ttu-id="08566-103">Het element Label voor GroupBy (opmaak)</span><span class="sxs-lookup"><span data-stu-id="08566-103">Label Element for GroupBy (Format)</span></span>

<span data-ttu-id="08566-104">Hiermee geeft u een label op dat wordt weer gegeven wanneer een nieuwe groep wordt aangetroffen.</span><span class="sxs-lookup"><span data-stu-id="08566-104">Specifies a label that is displayed when a new group is encountered.</span></span>

<span data-ttu-id="08566-105">Configuratie-element (indeling) ViewDefinitions element (indeling) element weer geven (indeling) GroupBy-element voor weer gave (indeling) label element voor GroupBy (indeling)</span><span class="sxs-lookup"><span data-stu-id="08566-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) GroupBy Element for View (Format) Label Element for GroupBy (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="08566-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="08566-106">Syntax</span></span>

```xml
<Label>DisplayedLabel</Label>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="08566-107">Kenmerken en elementen</span><span class="sxs-lookup"><span data-stu-id="08566-107">Attributes and Elements</span></span>

<span data-ttu-id="08566-108">In de volgende secties worden de kenmerken, onderliggende elementen en het bovenliggende element van het `Label` element beschreven.</span><span class="sxs-lookup"><span data-stu-id="08566-108">The following sections describe the attributes, child elements, and parent element of the `Label` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="08566-109">Kenmerken</span><span class="sxs-lookup"><span data-stu-id="08566-109">Attributes</span></span>

<span data-ttu-id="08566-110">Geen.</span><span class="sxs-lookup"><span data-stu-id="08566-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="08566-111">Onderliggende elementen</span><span class="sxs-lookup"><span data-stu-id="08566-111">Child Elements</span></span>

<span data-ttu-id="08566-112">Geen.</span><span class="sxs-lookup"><span data-stu-id="08566-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="08566-113">Bovenliggende elementen</span><span class="sxs-lookup"><span data-stu-id="08566-113">Parent Elements</span></span>

|<span data-ttu-id="08566-114">Element</span><span class="sxs-lookup"><span data-stu-id="08566-114">Element</span></span>|<span data-ttu-id="08566-115">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="08566-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="08566-116">Het element GroupBy voor Weergave (opmaak)</span><span class="sxs-lookup"><span data-stu-id="08566-116">GroupBy Element for View (Format)</span></span>](./groupby-element-for-view-format.md)|<span data-ttu-id="08566-117">Hiermee wordt gedefinieerd hoe een nieuwe groep objecten wordt weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="08566-117">Defines how a new group of objects is displayed.</span></span>|

## <a name="text-value"></a><span data-ttu-id="08566-118">Tekstwaarde</span><span class="sxs-lookup"><span data-stu-id="08566-118">Text Value</span></span>

<span data-ttu-id="08566-119">Geef de tekst op die wordt weer gegeven wanneer in Windows Power shell een nieuwe eigenschap of script waarde wordt aangetroffen.</span><span class="sxs-lookup"><span data-stu-id="08566-119">Specify the text that is displayed whenever Windows PowerShell encounters a new property or script value.</span></span>

## <a name="remarks"></a><span data-ttu-id="08566-120">Opmerkingen</span><span class="sxs-lookup"><span data-stu-id="08566-120">Remarks</span></span>

<span data-ttu-id="08566-121">Naast de tekst die door dit element is opgegeven, wordt in Windows Power shell de nieuwe waarde weer gegeven waarmee de groep wordt gestart en wordt een lege regel voor en na de groep toegevoegd.</span><span class="sxs-lookup"><span data-stu-id="08566-121">In addition to the text specified by this element, Windows PowerShell displays the new value that starts the group, and adds a blank line before and after the group.</span></span>

## <a name="example"></a><span data-ttu-id="08566-122">Voorbeeld</span><span class="sxs-lookup"><span data-stu-id="08566-122">Example</span></span>

<span data-ttu-id="08566-123">In het volgende voor beeld ziet u het label voor een nieuwe groep.</span><span class="sxs-lookup"><span data-stu-id="08566-123">The following example shows the label for a new group.</span></span> <span data-ttu-id="08566-124">Het weer gegeven label ziet er ongeveer als volgt uit: `Service Type: NewValueofProperty`</span><span class="sxs-lookup"><span data-stu-id="08566-124">The displayed label would look similar to this: `Service Type: NewValueofProperty`</span></span>

```xml
<GroupBy>
  <Label>Service Type</Label>
  <PropertyName>ServiceType</PropertyName>
</GroupBy>

```

<span data-ttu-id="08566-125">Zie [Wide View (GroupBy)](./wide-view-groupby.md)voor een voor beeld van een volledig indelings bestand dat dit element bevat.</span><span class="sxs-lookup"><span data-stu-id="08566-125">For an example of a complete formatting file that includes this element, see [Wide View (GroupBy)](./wide-view-groupby.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="08566-126">Zie ook</span><span class="sxs-lookup"><span data-stu-id="08566-126">See Also</span></span>

[<span data-ttu-id="08566-127">Het element GroupBy voor Weergave (opmaak)</span><span class="sxs-lookup"><span data-stu-id="08566-127">GroupBy Element for View (Format)</span></span>](./groupby-element-for-view-format.md)

[<span data-ttu-id="08566-128">Een PowerShell-opmaakbestand schrijven</span><span class="sxs-lookup"><span data-stu-id="08566-128">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
