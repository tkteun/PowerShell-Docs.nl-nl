---
ms.date: 09/13/2016
ms.topic: reference
title: Het element FormatString voor ListItem voor ListControl (opmaak)
description: Het element FormatString voor ListItem voor ListControl (opmaak)
ms.openlocfilehash: 1c16da92928ea632241942f4f2c63390c4fea706
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/27/2020
ms.locfileid: "92667909"
---
# <a name="formatstring-element-for-listitem-for-listcontrol--format"></a><span data-ttu-id="1d84e-103">Het element FormatString voor ListItem voor ListControl (opmaak)</span><span class="sxs-lookup"><span data-stu-id="1d84e-103">FormatString Element for ListItem for ListControl  (Format)</span></span>

<span data-ttu-id="1d84e-104">Geeft een opmaak patroon aan dat definieert hoe de eigenschap of script waarde wordt weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="1d84e-104">Specifies a format pattern that defines how the property or script value is displayed.</span></span>

<span data-ttu-id="1d84e-105">Configuratie-element (indeling) ViewDefinitions element (indeling) element weer geven (indeling) bestand van ListControl element (indeling). element (Format) List item voor ListControl (Format) element Entry List voor ListControl (Format) List items element voor ListControl (Format) lijst item element voor ListControl (Format) formats-element voor ListControl (Format)</span><span class="sxs-lookup"><span data-stu-id="1d84e-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) ListControl Element (Format) ListEntries Element for ListControl (Format) ListEntry Element for ListControl (Format) ListItems Element for ListControl (Format) ListItem Element for ListControl (Format) FormatString Element for ListItem for ListControl (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="1d84e-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="1d84e-106">Syntax</span></span>

```xml
<FormatString>PropertyPattern</FormatString>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="1d84e-107">Kenmerken en elementen</span><span class="sxs-lookup"><span data-stu-id="1d84e-107">Attributes and Elements</span></span>

<span data-ttu-id="1d84e-108">In de volgende secties worden de kenmerken, onderliggende elementen en het bovenliggende element van het `FormatString` element beschreven.</span><span class="sxs-lookup"><span data-stu-id="1d84e-108">The following sections describe the attributes, child elements, and the parent element of the `FormatString` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="1d84e-109">Kenmerken</span><span class="sxs-lookup"><span data-stu-id="1d84e-109">Attributes</span></span>

<span data-ttu-id="1d84e-110">Geen.</span><span class="sxs-lookup"><span data-stu-id="1d84e-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="1d84e-111">Onderliggende elementen</span><span class="sxs-lookup"><span data-stu-id="1d84e-111">Child Elements</span></span>

<span data-ttu-id="1d84e-112">Geen.</span><span class="sxs-lookup"><span data-stu-id="1d84e-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="1d84e-113">Bovenliggende elementen</span><span class="sxs-lookup"><span data-stu-id="1d84e-113">Parent Elements</span></span>

|<span data-ttu-id="1d84e-114">Element</span><span class="sxs-lookup"><span data-stu-id="1d84e-114">Element</span></span>|<span data-ttu-id="1d84e-115">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="1d84e-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="1d84e-116">Lijst item-element (indeling)</span><span class="sxs-lookup"><span data-stu-id="1d84e-116">ListItem Element (Format)</span></span>](./listitem-element-for-listitems-for-listcontrol-format.md)|<span data-ttu-id="1d84e-117">Hiermee wordt de eigenschap of het script gedefinieerd waarvan de waarde wordt weer gegeven in een rij van de lijst weergave.</span><span class="sxs-lookup"><span data-stu-id="1d84e-117">Defines the property or script whose value is displayed in a row of the list view.</span></span>|

## <a name="text-value"></a><span data-ttu-id="1d84e-118">Tekstwaarde</span><span class="sxs-lookup"><span data-stu-id="1d84e-118">Text Value</span></span>

<span data-ttu-id="1d84e-119">Geef het patroon op dat wordt gebruikt om de gegevens op te maken.</span><span class="sxs-lookup"><span data-stu-id="1d84e-119">Specify the pattern that is used to format the data.</span></span> <span data-ttu-id="1d84e-120">U kunt dit patroon bijvoorbeeld gebruiken om de waarde van een eigenschap van het type [System. time span](/dotnet/api/System.TimeSpan): {0: mmm} {0: dd} {0: uu}: {0: mm} in te delen.</span><span class="sxs-lookup"><span data-stu-id="1d84e-120">For example, you can use this pattern to format the value of any property that is of type [System.Timespan](/dotnet/api/System.TimeSpan): {0:MMM}{0:dd}{0:HH}:{0:mm}.</span></span>

## <a name="remarks"></a><span data-ttu-id="1d84e-121">Opmerkingen</span><span class="sxs-lookup"><span data-stu-id="1d84e-121">Remarks</span></span>

<span data-ttu-id="1d84e-122">Opmaak teken reeksen kunnen worden gebruikt bij het maken van tabel weergaven, lijst weergaven, brede weer gaven of aangepaste weer gaven.</span><span class="sxs-lookup"><span data-stu-id="1d84e-122">Format strings can be used when creating table views, list views, wide views, or custom views.</span></span> <span data-ttu-id="1d84e-123">Zie voor meer informatie over het opmaken van een waarde die wordt weer gegeven in een weer gave, [weer gegeven gegevens opmaken](./formatting-displayed-data.md).</span><span class="sxs-lookup"><span data-stu-id="1d84e-123">For more information about formatting a value displayed in a view, see [Formatting Displayed Data](./formatting-displayed-data.md).</span></span>

<span data-ttu-id="1d84e-124">Zie [lijst weergave maken](./creating-a-list-view.md)voor meer informatie over het gebruik van opmaak teken reeksen in lijst weergaven.</span><span class="sxs-lookup"><span data-stu-id="1d84e-124">For more information about using format strings in list views, see [Creating List View](./creating-a-list-view.md).</span></span>

## <a name="example"></a><span data-ttu-id="1d84e-125">Voorbeeld</span><span class="sxs-lookup"><span data-stu-id="1d84e-125">Example</span></span>

<span data-ttu-id="1d84e-126">In het volgende voor beeld ziet u hoe u een opmaak teken reeks definieert voor de waarde van de `StartTime` eigenschap.</span><span class="sxs-lookup"><span data-stu-id="1d84e-126">The following example shows how to define a formatting string for the value of the `StartTime` property.</span></span>

```xml
<ListItem>
  <PropertyName>StartTime</PropertyName>
  <FormatString>{0:MMM} (0:DD) (0:HH):(0:MM)</FormatString>
</ListItem>
```

## <a name="see-also"></a><span data-ttu-id="1d84e-127">Zie ook</span><span class="sxs-lookup"><span data-stu-id="1d84e-127">See Also</span></span>

[<span data-ttu-id="1d84e-128">Een lijstweergave maken</span><span class="sxs-lookup"><span data-stu-id="1d84e-128">Creating a List View</span></span>](./creating-a-list-view.md)

[<span data-ttu-id="1d84e-129">Lijst item-element (indeling)</span><span class="sxs-lookup"><span data-stu-id="1d84e-129">ListItem Element (Format)</span></span>](./listitem-element-for-listitems-for-listcontrol-format.md)

[<span data-ttu-id="1d84e-130">Een Windows Power shell-indeling en-type bestand schrijven</span><span class="sxs-lookup"><span data-stu-id="1d84e-130">Writing a Windows PowerShell Formatting and Types File</span></span>](./writing-a-powershell-formatting-file.md)
