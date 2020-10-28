---
ms.date: 09/13/2016
ms.topic: reference
title: Het element FormatString voor WideItem voor WideControl (opmaak)
description: Het element FormatString voor WideItem voor WideControl (opmaak)
ms.openlocfilehash: f67a18e3ec4f1323e7f9be8904db518c679d53e5
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/27/2020
ms.locfileid: "92667875"
---
# <a name="formatstring-element-for-wideitem-for-widecontrol-format"></a><span data-ttu-id="65ae9-103">Het element FormatString voor WideItem voor WideControl (opmaak)</span><span class="sxs-lookup"><span data-stu-id="65ae9-103">FormatString Element for WideItem for WideControl (Format)</span></span>

<span data-ttu-id="65ae9-104">Geeft een indelings patroon aan dat definieert hoe de eigenschap of script waarde wordt weer gegeven in de weer gave.</span><span class="sxs-lookup"><span data-stu-id="65ae9-104">Specifies a format pattern that defines how the property or script value is displayed in the view.</span></span>

<span data-ttu-id="65ae9-105">Configuratie-element (indeling) ViewDefinitions element (indeling) element weer geven (indeling) WideControl element (indeling) WideEntries element (indeling) WideEntry element voor WideControl (Format) WideItem-element voor WideControl (Format) voor WideItem-element voor WideControl (Format)</span><span class="sxs-lookup"><span data-stu-id="65ae9-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) WideControl Element (Format) WideEntries Element (Format) WideEntry Element for WideControl (Format) WideItem Element for WideControl (Format) FormatString Element for WideItem for WideControl (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="65ae9-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="65ae9-106">Syntax</span></span>

```xml
<FormatString>PropertyPattern</FormatString>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="65ae9-107">Kenmerken en elementen</span><span class="sxs-lookup"><span data-stu-id="65ae9-107">Attributes and Elements</span></span>

<span data-ttu-id="65ae9-108">In de volgende secties worden de kenmerken, onderliggende elementen en het bovenliggende element van het `FormatString` element beschreven.</span><span class="sxs-lookup"><span data-stu-id="65ae9-108">The following sections describe the attributes, child elements, and the parent element of the `FormatString` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="65ae9-109">Kenmerken</span><span class="sxs-lookup"><span data-stu-id="65ae9-109">Attributes</span></span>

<span data-ttu-id="65ae9-110">Geen.</span><span class="sxs-lookup"><span data-stu-id="65ae9-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="65ae9-111">Onderliggende elementen</span><span class="sxs-lookup"><span data-stu-id="65ae9-111">Child Elements</span></span>

<span data-ttu-id="65ae9-112">Geen.</span><span class="sxs-lookup"><span data-stu-id="65ae9-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="65ae9-113">Bovenliggende elementen</span><span class="sxs-lookup"><span data-stu-id="65ae9-113">Parent Elements</span></span>

|<span data-ttu-id="65ae9-114">Element</span><span class="sxs-lookup"><span data-stu-id="65ae9-114">Element</span></span>|<span data-ttu-id="65ae9-115">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="65ae9-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="65ae9-116">Het element WideItem voor WideControl (opmaak)</span><span class="sxs-lookup"><span data-stu-id="65ae9-116">WideItem Element for WideControl (Format)</span></span>](./wideitem-element-for-widecontrol-format.md)|<span data-ttu-id="65ae9-117">Hiermee wordt de eigenschap of het script gedefinieerd waarvan de waarde wordt weer gegeven in een rij van de lijst weergave.</span><span class="sxs-lookup"><span data-stu-id="65ae9-117">Defines the property or script whose value is displayed in a row of the list view.</span></span>|

## <a name="text-value"></a><span data-ttu-id="65ae9-118">Tekstwaarde</span><span class="sxs-lookup"><span data-stu-id="65ae9-118">Text Value</span></span>

<span data-ttu-id="65ae9-119">Geef het patroon op dat wordt gebruikt om de gegevens op te maken.</span><span class="sxs-lookup"><span data-stu-id="65ae9-119">Specify the pattern that is used to format the data.</span></span> <span data-ttu-id="65ae9-120">U kunt dit patroon bijvoorbeeld gebruiken om de waarde van een eigenschap van het type [System. time span](/dotnet/api/System.TimeSpan): {0: mmm} {0: dd} {0: uu}: {0: mm} in te delen.</span><span class="sxs-lookup"><span data-stu-id="65ae9-120">For example, you can use this pattern to format the value of any property that is of type [System.Timespan](/dotnet/api/System.TimeSpan): {0:MMM}{0:dd}{0:HH}:{0:mm}.</span></span>

## <a name="remarks"></a><span data-ttu-id="65ae9-121">Opmerkingen</span><span class="sxs-lookup"><span data-stu-id="65ae9-121">Remarks</span></span>

<span data-ttu-id="65ae9-122">Opmaak teken reeksen kunnen worden gebruikt bij het maken van tabel weergaven, lijst weergaven, brede weer gaven of aangepaste weer gaven.</span><span class="sxs-lookup"><span data-stu-id="65ae9-122">Format strings can be used when creating table views, list views, wide views, or custom views.</span></span> <span data-ttu-id="65ae9-123">Zie voor meer informatie over het opmaken van een waarde die wordt weer gegeven in een weer gave, [weer gegeven gegevens opmaken](./formatting-displayed-data.md).</span><span class="sxs-lookup"><span data-stu-id="65ae9-123">For more information about formatting a value displayed in a view, see [Formatting Displayed Data](./formatting-displayed-data.md).</span></span>

<span data-ttu-id="65ae9-124">Zie [een brede weer gave maken](./creating-a-wide-view.md)voor meer informatie over het gebruik van opmaak reeksen in brede weer gaven.</span><span class="sxs-lookup"><span data-stu-id="65ae9-124">For more information about using format strings in wide views, see [Creating a Wide View](./creating-a-wide-view.md).</span></span>

## <a name="example"></a><span data-ttu-id="65ae9-125">Voorbeeld</span><span class="sxs-lookup"><span data-stu-id="65ae9-125">Example</span></span>

<span data-ttu-id="65ae9-126">In het volgende voor beeld ziet u hoe u een opmaak teken reeks definieert voor de waarde van de `StartTime` eigenschap.</span><span class="sxs-lookup"><span data-stu-id="65ae9-126">The following example shows how to define a formatting string for the value of the `StartTime` property.</span></span>

```xml
<WideItem>
  <PropertyName>StartTime</PropertyName>
  <FormatString>{0:MMM} (0:DD) (0:HH):(0:MM)</FormatString>
</WideItem>
```

## <a name="see-also"></a><span data-ttu-id="65ae9-127">Zie ook</span><span class="sxs-lookup"><span data-stu-id="65ae9-127">See Also</span></span>

[<span data-ttu-id="65ae9-128">Een brede weergave maken</span><span class="sxs-lookup"><span data-stu-id="65ae9-128">Creating a Wide View</span></span>](./creating-a-wide-view.md)

[<span data-ttu-id="65ae9-129">Het element WideItem voor WideControl (opmaak)</span><span class="sxs-lookup"><span data-stu-id="65ae9-129">WideItem Element for WideControl (Format)</span></span>](./wideitem-element-for-widecontrol-format.md)

[<span data-ttu-id="65ae9-130">Een Windows Power shell-indeling en-type bestand schrijven</span><span class="sxs-lookup"><span data-stu-id="65ae9-130">Writing a Windows PowerShell Formatting and Types File</span></span>](./writing-a-powershell-formatting-file.md)
