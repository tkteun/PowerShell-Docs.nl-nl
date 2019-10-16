---
title: Element formats Tring voor WideItem voor WideControl (indeling) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 5bc6ea26-3ca6-4bab-8a13-29189821ba15
caps.latest.revision: 7
ms.openlocfilehash: a1dc145864a6904fd4af6c3b9187819c49e224b0
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/15/2019
ms.locfileid: "72354542"
---
# <a name="formatstring-element-for-wideitem-for-widecontrol-format"></a><span data-ttu-id="d7c60-102">Het element FormatString voor WideItem voor WideControl (opmaak)</span><span class="sxs-lookup"><span data-stu-id="d7c60-102">FormatString Element for WideItem for WideControl (Format)</span></span>

<span data-ttu-id="d7c60-103">Geeft een indelings patroon aan dat definieert hoe de eigenschap of script waarde wordt weer gegeven in de weer gave.</span><span class="sxs-lookup"><span data-stu-id="d7c60-103">Specifies a format pattern that defines how the property or script value is displayed in the view.</span></span>

<span data-ttu-id="d7c60-104">Configuratie-element (indeling) ViewDefinitions element (indeling) element weer geven (indeling) WideControl element (indeling) WideEntries element (indeling) WideEntry element voor WideControl (Format) WideItem element voor WideControl (indeling) formats Tring element voor WideItem voor WideControl (indeling)</span><span class="sxs-lookup"><span data-stu-id="d7c60-104">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) WideControl Element (Format) WideEntries Element (Format) WideEntry Element for WideControl (Format) WideItem Element for WideControl (Format) FormatString Element for WideItem for WideControl (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="d7c60-105">Syntaxis</span><span class="sxs-lookup"><span data-stu-id="d7c60-105">Syntax</span></span>

```xml
<FormatString>PropertyPattern</FormatString>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="d7c60-106">Kenmerken en elementen</span><span class="sxs-lookup"><span data-stu-id="d7c60-106">Attributes and Elements</span></span>

<span data-ttu-id="d7c60-107">In de volgende secties worden de kenmerken, onderliggende elementen en het bovenliggende element van het element `FormatString` beschreven.</span><span class="sxs-lookup"><span data-stu-id="d7c60-107">The following sections describe the attributes, child elements, and the parent element of the `FormatString` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="d7c60-108">Kenmerken</span><span class="sxs-lookup"><span data-stu-id="d7c60-108">Attributes</span></span>

<span data-ttu-id="d7c60-109">Geen.</span><span class="sxs-lookup"><span data-stu-id="d7c60-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="d7c60-110">Onderliggende elementen</span><span class="sxs-lookup"><span data-stu-id="d7c60-110">Child Elements</span></span>

<span data-ttu-id="d7c60-111">Geen.</span><span class="sxs-lookup"><span data-stu-id="d7c60-111">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="d7c60-112">Bovenliggende elementen</span><span class="sxs-lookup"><span data-stu-id="d7c60-112">Parent Elements</span></span>

|<span data-ttu-id="d7c60-113">Element</span><span class="sxs-lookup"><span data-stu-id="d7c60-113">Element</span></span>|<span data-ttu-id="d7c60-114">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="d7c60-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="d7c60-115">WideItem-element voor WideControl (indeling)</span><span class="sxs-lookup"><span data-stu-id="d7c60-115">WideItem Element for WideControl (Format)</span></span>](./wideitem-element-for-widecontrol-format.md)|<span data-ttu-id="d7c60-116">Hiermee wordt de eigenschap of het script gedefinieerd waarvan de waarde wordt weer gegeven in een rij van de lijst weergave.</span><span class="sxs-lookup"><span data-stu-id="d7c60-116">Defines the property or script whose value is displayed in a row of the list view.</span></span>|

## <a name="text-value"></a><span data-ttu-id="d7c60-117">Tekst waarde</span><span class="sxs-lookup"><span data-stu-id="d7c60-117">Text Value</span></span>

<span data-ttu-id="d7c60-118">Geef het patroon op dat wordt gebruikt om de gegevens op te maken.</span><span class="sxs-lookup"><span data-stu-id="d7c60-118">Specify the pattern that is used to format the data.</span></span> <span data-ttu-id="d7c60-119">U kunt dit patroon bijvoorbeeld gebruiken om de waarde van een eigenschap van het type [System. time span](/dotnet/api/System.TimeSpan): {0: mmm} {0: dd} {0: uu}: {0: mm} in te delen.</span><span class="sxs-lookup"><span data-stu-id="d7c60-119">For example, you can use this pattern to format the value of any property that is of type [System.Timespan](/dotnet/api/System.TimeSpan): {0:MMM}{0:dd}{0:HH}:{0:mm}.</span></span>

## <a name="remarks"></a><span data-ttu-id="d7c60-120">Opmerkingen</span><span class="sxs-lookup"><span data-stu-id="d7c60-120">Remarks</span></span>

<span data-ttu-id="d7c60-121">Opmaak teken reeksen kunnen worden gebruikt bij het maken van tabel weergaven, lijst weergaven, brede weer gaven of aangepaste weer gaven.</span><span class="sxs-lookup"><span data-stu-id="d7c60-121">Format strings can be used when creating table views, list views, wide views, or custom views.</span></span> <span data-ttu-id="d7c60-122">Zie voor meer informatie over het opmaken van een waarde die wordt weer gegeven in een weer gave, [weer gegeven gegevens opmaken](./formatting-displayed-data.md).</span><span class="sxs-lookup"><span data-stu-id="d7c60-122">For more information about formatting a value displayed in a view, see [Formatting Displayed Data](./formatting-displayed-data.md).</span></span>

<span data-ttu-id="d7c60-123">Zie [een brede weer gave maken](./creating-a-wide-view.md)voor meer informatie over het gebruik van opmaak reeksen in brede weer gaven.</span><span class="sxs-lookup"><span data-stu-id="d7c60-123">For more information about using format strings in wide views, see [Creating a Wide View](./creating-a-wide-view.md).</span></span>

## <a name="example"></a><span data-ttu-id="d7c60-124">Voorbeeld</span><span class="sxs-lookup"><span data-stu-id="d7c60-124">Example</span></span>

<span data-ttu-id="d7c60-125">In het volgende voor beeld ziet u hoe u een opmaak teken reeks definieert voor de waarde van de eigenschap `StartTime`.</span><span class="sxs-lookup"><span data-stu-id="d7c60-125">The following example shows how to define a formatting string for the value of the `StartTime` property.</span></span>

```xml
<WideItem>
  <PropertyName>StartTime</PropertyName>
  <FormatString>{0:MMM} (0:DD) (0:HH):(0:MM)</FormatString>
</WideItem>
```

## <a name="see-also"></a><span data-ttu-id="d7c60-126">Zie ook</span><span class="sxs-lookup"><span data-stu-id="d7c60-126">See Also</span></span>

[<span data-ttu-id="d7c60-127">Een brede weer gave maken</span><span class="sxs-lookup"><span data-stu-id="d7c60-127">Creating a Wide View</span></span>](./creating-a-wide-view.md)

[<span data-ttu-id="d7c60-128">WideItem-element voor WideControl (indeling)</span><span class="sxs-lookup"><span data-stu-id="d7c60-128">WideItem Element for WideControl (Format)</span></span>](./wideitem-element-for-widecontrol-format.md)

[<span data-ttu-id="d7c60-129">Een Windows Power shell-indeling en-type bestand schrijven</span><span class="sxs-lookup"><span data-stu-id="d7c60-129">Writing a Windows PowerShell Formatting and Types File</span></span>](./writing-a-powershell-formatting-file.md)
