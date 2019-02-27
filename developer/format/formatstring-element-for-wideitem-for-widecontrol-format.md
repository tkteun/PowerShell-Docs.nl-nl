---
title: FormatString-Element voor WideItem voor WideControl (indeling) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 5bc6ea26-3ca6-4bab-8a13-29189821ba15
caps.latest.revision: 7
ms.openlocfilehash: a1dc145864a6904fd4af6c3b9187819c49e224b0
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 02/03/2019
ms.locfileid: "56850265"
---
# <a name="formatstring-element-for-wideitem-for-widecontrol-format"></a><span data-ttu-id="1b4b7-102">Het element FormatString voor WideItem voor WideControl (opmaak)</span><span class="sxs-lookup"><span data-stu-id="1b4b7-102">FormatString Element for WideItem for WideControl (Format)</span></span>

<span data-ttu-id="1b4b7-103">Hiermee geeft u een indeling patroon waarmee wordt gedefinieerd hoe de waarde voor eigenschap of het script wordt weergegeven in de weergave.</span><span class="sxs-lookup"><span data-stu-id="1b4b7-103">Specifies a format pattern that defines how the property or script value is displayed in the view.</span></span>

<span data-ttu-id="1b4b7-104">Configuratie Element (indeling) ViewDefinitions-Element (indeling) weergave Element (indeling) WideControl-Element (indeling) WideEntries-Element (indeling) WideEntry Element voor WideControl (indeling) WideItem-Element voor WideControl (indeling) FormatString-Element voor WideItem voor WideControl (indeling)</span><span class="sxs-lookup"><span data-stu-id="1b4b7-104">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) WideControl Element (Format) WideEntries Element (Format) WideEntry Element for WideControl (Format) WideItem Element for WideControl (Format) FormatString Element for WideItem for WideControl (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="1b4b7-105">Syntaxis</span><span class="sxs-lookup"><span data-stu-id="1b4b7-105">Syntax</span></span>

```xml
<FormatString>PropertyPattern</FormatString>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="1b4b7-106">Kenmerken en elementen</span><span class="sxs-lookup"><span data-stu-id="1b4b7-106">Attributes and Elements</span></span>

<span data-ttu-id="1b4b7-107">De volgende secties worden de kenmerken, onderliggende elementen en het bovenliggende element van de `FormatString` element.</span><span class="sxs-lookup"><span data-stu-id="1b4b7-107">The following sections describe the attributes, child elements, and the parent element of the `FormatString` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="1b4b7-108">Kenmerken</span><span class="sxs-lookup"><span data-stu-id="1b4b7-108">Attributes</span></span>

<span data-ttu-id="1b4b7-109">Geen.</span><span class="sxs-lookup"><span data-stu-id="1b4b7-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="1b4b7-110">Onderliggende elementen</span><span class="sxs-lookup"><span data-stu-id="1b4b7-110">Child Elements</span></span>

<span data-ttu-id="1b4b7-111">Geen.</span><span class="sxs-lookup"><span data-stu-id="1b4b7-111">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="1b4b7-112">Bovenliggende elementen</span><span class="sxs-lookup"><span data-stu-id="1b4b7-112">Parent Elements</span></span>

|<span data-ttu-id="1b4b7-113">Element</span><span class="sxs-lookup"><span data-stu-id="1b4b7-113">Element</span></span>|<span data-ttu-id="1b4b7-114">Description</span><span class="sxs-lookup"><span data-stu-id="1b4b7-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="1b4b7-115">WideItem-Element voor WideControl (indeling)</span><span class="sxs-lookup"><span data-stu-id="1b4b7-115">WideItem Element for WideControl (Format)</span></span>](./wideitem-element-for-widecontrol-format.md)|<span data-ttu-id="1b4b7-116">Hiermee definieert de eigenschap of het script waarvan de waarde wordt weergegeven in een rij in de lijstweergave.</span><span class="sxs-lookup"><span data-stu-id="1b4b7-116">Defines the property or script whose value is displayed in a row of the list view.</span></span>|

## <a name="text-value"></a><span data-ttu-id="1b4b7-117">Tekstwaarde</span><span class="sxs-lookup"><span data-stu-id="1b4b7-117">Text Value</span></span>

<span data-ttu-id="1b4b7-118">Geef het patroon dat wordt gebruikt om de opmaak van de gegevens.</span><span class="sxs-lookup"><span data-stu-id="1b4b7-118">Specify the pattern that is used to format the data.</span></span> <span data-ttu-id="1b4b7-119">Bijvoorbeeld, kunt u dit patroon om de waarde van elke eigenschap die is van het type [System.DateTime](/dotnet/api/System.TimeSpan): {0: MMM} {0:dd} {0:HH}: {0:mm}.</span><span class="sxs-lookup"><span data-stu-id="1b4b7-119">For example, you can use this pattern to format the value of any property that is of type [System.Timespan](/dotnet/api/System.TimeSpan): {0:MMM}{0:dd}{0:HH}:{0:mm}.</span></span>

## <a name="remarks"></a><span data-ttu-id="1b4b7-120">Opmerkingen</span><span class="sxs-lookup"><span data-stu-id="1b4b7-120">Remarks</span></span>

<span data-ttu-id="1b4b7-121">Opmaaktekenreeksen kunnen worden gebruikt bij het maken van tabelweergaven, lijst met weergaven, breed weergaven of aangepaste weergaven.</span><span class="sxs-lookup"><span data-stu-id="1b4b7-121">Format strings can be used when creating table views, list views, wide views, or custom views.</span></span> <span data-ttu-id="1b4b7-122">Zie voor meer informatie over het opmaken van een waarde die wordt weergegeven in een weergave [weergegeven gegevens opmaak](./formatting-displayed-data.md).</span><span class="sxs-lookup"><span data-stu-id="1b4b7-122">For more information about formatting a value displayed in a view, see [Formatting Displayed Data](./formatting-displayed-data.md).</span></span>

<span data-ttu-id="1b4b7-123">Zie voor meer informatie over het gebruik van opmaaktekenreeksen in breed weergaven [het maken van een brede weergave](./creating-a-wide-view.md).</span><span class="sxs-lookup"><span data-stu-id="1b4b7-123">For more information about using format strings in wide views, see [Creating a Wide View](./creating-a-wide-view.md).</span></span>

## <a name="example"></a><span data-ttu-id="1b4b7-124">Voorbeeld</span><span class="sxs-lookup"><span data-stu-id="1b4b7-124">Example</span></span>

<span data-ttu-id="1b4b7-125">Het volgende voorbeeld ziet u hoe u een opmaaktekenreeks voor de waarde van de `StartTime` eigenschap.</span><span class="sxs-lookup"><span data-stu-id="1b4b7-125">The following example shows how to define a formatting string for the value of the `StartTime` property.</span></span>

```xml
<WideItem>
  <PropertyName>StartTime</PropertyName>
  <FormatString>{0:MMM} (0:DD) (0:HH):(0:MM)</FormatString>
</WideItem>
```

## <a name="see-also"></a><span data-ttu-id="1b4b7-126">Zie ook</span><span class="sxs-lookup"><span data-stu-id="1b4b7-126">See Also</span></span>

[<span data-ttu-id="1b4b7-127">Het maken van een brede weergave</span><span class="sxs-lookup"><span data-stu-id="1b4b7-127">Creating a Wide View</span></span>](./creating-a-wide-view.md)

[<span data-ttu-id="1b4b7-128">WideItem-Element voor WideControl (indeling)</span><span class="sxs-lookup"><span data-stu-id="1b4b7-128">WideItem Element for WideControl (Format)</span></span>](./wideitem-element-for-widecontrol-format.md)

[<span data-ttu-id="1b4b7-129">Schrijven van een Windows PowerShell opmaak en het bestand van het type</span><span class="sxs-lookup"><span data-stu-id="1b4b7-129">Writing a Windows PowerShell Formatting and Types File</span></span>](./writing-a-powershell-formatting-file.md)
