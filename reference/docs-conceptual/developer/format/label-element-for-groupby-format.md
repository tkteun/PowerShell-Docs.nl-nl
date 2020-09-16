---
title: Label element voor GroupBy (indeling) | Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: 07b4d037472a9dd2329e94576ec10f5b82f46b34
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 08/05/2020
ms.locfileid: "87785775"
---
# <a name="label-element-for-groupby-format"></a><span data-ttu-id="70024-102">Het element Label voor GroupBy (opmaak)</span><span class="sxs-lookup"><span data-stu-id="70024-102">Label Element for GroupBy (Format)</span></span>

<span data-ttu-id="70024-103">Hiermee geeft u een label op dat wordt weer gegeven wanneer een nieuwe groep wordt aangetroffen.</span><span class="sxs-lookup"><span data-stu-id="70024-103">Specifies a label that is displayed when a new group is encountered.</span></span>

<span data-ttu-id="70024-104">Configuratie-element (indeling) ViewDefinitions element (indeling) element weer geven (indeling) GroupBy-element voor weer gave (indeling) label element voor GroupBy (indeling)</span><span class="sxs-lookup"><span data-stu-id="70024-104">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) GroupBy Element for View (Format) Label Element for GroupBy (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="70024-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="70024-105">Syntax</span></span>

```xml
<Label>DisplayedLabel</Label>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="70024-106">Kenmerken en elementen</span><span class="sxs-lookup"><span data-stu-id="70024-106">Attributes and Elements</span></span>

<span data-ttu-id="70024-107">In de volgende secties worden de kenmerken, onderliggende elementen en het bovenliggende element van het `Label` element beschreven.</span><span class="sxs-lookup"><span data-stu-id="70024-107">The following sections describe the attributes, child elements, and parent element of the `Label` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="70024-108">Kenmerken</span><span class="sxs-lookup"><span data-stu-id="70024-108">Attributes</span></span>

<span data-ttu-id="70024-109">Geen.</span><span class="sxs-lookup"><span data-stu-id="70024-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="70024-110">Onderliggende elementen</span><span class="sxs-lookup"><span data-stu-id="70024-110">Child Elements</span></span>

<span data-ttu-id="70024-111">Geen.</span><span class="sxs-lookup"><span data-stu-id="70024-111">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="70024-112">Bovenliggende elementen</span><span class="sxs-lookup"><span data-stu-id="70024-112">Parent Elements</span></span>

|<span data-ttu-id="70024-113">Element</span><span class="sxs-lookup"><span data-stu-id="70024-113">Element</span></span>|<span data-ttu-id="70024-114">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="70024-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="70024-115">Het element GroupBy voor Weergave (opmaak)</span><span class="sxs-lookup"><span data-stu-id="70024-115">GroupBy Element for View (Format)</span></span>](./groupby-element-for-view-format.md)|<span data-ttu-id="70024-116">Hiermee wordt gedefinieerd hoe een nieuwe groep objecten wordt weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="70024-116">Defines how a new group of objects is displayed.</span></span>|

## <a name="text-value"></a><span data-ttu-id="70024-117">Tekstwaarde</span><span class="sxs-lookup"><span data-stu-id="70024-117">Text Value</span></span>

<span data-ttu-id="70024-118">Geef de tekst op die wordt weer gegeven wanneer in Windows Power shell een nieuwe eigenschap of script waarde wordt aangetroffen.</span><span class="sxs-lookup"><span data-stu-id="70024-118">Specify the text that is displayed whenever Windows PowerShell encounters a new property or script value.</span></span>

## <a name="remarks"></a><span data-ttu-id="70024-119">Opmerkingen</span><span class="sxs-lookup"><span data-stu-id="70024-119">Remarks</span></span>

<span data-ttu-id="70024-120">Naast de tekst die door dit element is opgegeven, wordt in Windows Power shell de nieuwe waarde weer gegeven waarmee de groep wordt gestart en wordt een lege regel voor en na de groep toegevoegd.</span><span class="sxs-lookup"><span data-stu-id="70024-120">In addition to the text specified by this element, Windows PowerShell displays the new value that starts the group, and adds a blank line before and after the group.</span></span>

## <a name="example"></a><span data-ttu-id="70024-121">Voorbeeld</span><span class="sxs-lookup"><span data-stu-id="70024-121">Example</span></span>

<span data-ttu-id="70024-122">In het volgende voor beeld ziet u het label voor een nieuwe groep.</span><span class="sxs-lookup"><span data-stu-id="70024-122">The following example shows the label for a new group.</span></span> <span data-ttu-id="70024-123">Het weer gegeven label ziet er ongeveer als volgt uit: `Service Type: NewValueofProperty`</span><span class="sxs-lookup"><span data-stu-id="70024-123">The displayed label would look similar to this: `Service Type: NewValueofProperty`</span></span>

```xml
<GroupBy>
  <Label>Service Type</Label>
  <PropertyName>ServiceType</PropertyName>
</GroupBy>

```

<span data-ttu-id="70024-124">Zie [Wide View (GroupBy)](./wide-view-groupby.md)voor een voor beeld van een volledig indelings bestand dat dit element bevat.</span><span class="sxs-lookup"><span data-stu-id="70024-124">For an example of a complete formatting file that includes this element, see [Wide View (GroupBy)](./wide-view-groupby.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="70024-125">Zie ook</span><span class="sxs-lookup"><span data-stu-id="70024-125">See Also</span></span>

[<span data-ttu-id="70024-126">Het element GroupBy voor Weergave (opmaak)</span><span class="sxs-lookup"><span data-stu-id="70024-126">GroupBy Element for View (Format)</span></span>](./groupby-element-for-view-format.md)

[<span data-ttu-id="70024-127">Een PowerShell-opmaakbestand schrijven</span><span class="sxs-lookup"><span data-stu-id="70024-127">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
