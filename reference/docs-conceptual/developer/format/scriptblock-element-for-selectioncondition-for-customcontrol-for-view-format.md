---
title: Script block-element voor SelectionCondition voor CustomControl voor weer gave (indeling) | Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: d3506188d32ce85ad6345dc0d0866dd789a1f293
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 08/05/2020
ms.locfileid: "87785401"
---
# <a name="scriptblock-element-for-selectioncondition-for-customcontrol-for-view-format"></a><span data-ttu-id="75841-102">Het element ScriptBlock voor SelectionCondition voor CustomControl voor Weergave (opmaak)</span><span class="sxs-lookup"><span data-stu-id="75841-102">ScriptBlock Element for SelectionCondition for CustomControl for View (Format)</span></span>

<span data-ttu-id="75841-103">Hiermee geeft u het script op waarmee de voor waarde wordt geactiveerd.</span><span class="sxs-lookup"><span data-stu-id="75841-103">Specifies the script that triggers the condition.</span></span> <span data-ttu-id="75841-104">Wanneer dit script wordt geëvalueerd `true` , wordt voldaan aan de voor waarde en wordt de definitie gebruikt.</span><span class="sxs-lookup"><span data-stu-id="75841-104">When this script is evaluated to `true`, the condition is met, and the definition is used.</span></span> <span data-ttu-id="75841-105">Dit element wordt gebruikt bij het definiëren van een aangepaste beheer weergave.</span><span class="sxs-lookup"><span data-stu-id="75841-105">This element is used when defining a custom control view.</span></span>

<span data-ttu-id="75841-106">Configuratie-element (indeling) ViewDefinitions element (indeling) element van weer gave (Format) CustomControl element voor weer gave (Format) CustomEntries element voor CustomControl voor weer gave (Format) CustomEntry-element voor CustomEntries voor CustomControl voor weer gave (Format) CustomItem-element voor CustomEntry voor het object CustomControl voor weer gave (Format) SelectionCondition voor EntrySelectedBy</span><span class="sxs-lookup"><span data-stu-id="75841-106">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) CustomControl Element for View (Format) CustomEntries Element for CustomControl for View (Format) CustomEntry Element for CustomEntries for CustomControl for View (Format) CustomItem Element for CustomEntry for CustomControl for View (Format) SelectionCondition Element for EntrySelectedBy for CustomControl for View (Format) ScriptBlock Element for SelectionCondition for CustomControl for View (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="75841-107">Syntax</span><span class="sxs-lookup"><span data-stu-id="75841-107">Syntax</span></span>

```xml
<ScriptBlock>ScriptToEvaluate</ScriptBlock>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="75841-108">Kenmerken en elementen</span><span class="sxs-lookup"><span data-stu-id="75841-108">Attributes and Elements</span></span>

<span data-ttu-id="75841-109">In de volgende secties worden kenmerken, onderliggende elementen en het bovenliggende element van het `ScriptBlock` element beschreven.</span><span class="sxs-lookup"><span data-stu-id="75841-109">The following sections describe attributes, child elements, and the parent element of the `ScriptBlock` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="75841-110">Kenmerken</span><span class="sxs-lookup"><span data-stu-id="75841-110">Attributes</span></span>

<span data-ttu-id="75841-111">Geen.</span><span class="sxs-lookup"><span data-stu-id="75841-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="75841-112">Onderliggende elementen</span><span class="sxs-lookup"><span data-stu-id="75841-112">Child Elements</span></span>

<span data-ttu-id="75841-113">Geen.</span><span class="sxs-lookup"><span data-stu-id="75841-113">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="75841-114">Bovenliggende elementen</span><span class="sxs-lookup"><span data-stu-id="75841-114">Parent Elements</span></span>

|<span data-ttu-id="75841-115">Element</span><span class="sxs-lookup"><span data-stu-id="75841-115">Element</span></span>|<span data-ttu-id="75841-116">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="75841-116">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="75841-117">SelectionCondition-element voor EntrySelectedBy voor CustomControl voor weer gave (indeling)</span><span class="sxs-lookup"><span data-stu-id="75841-117">SelectionCondition Element for EntrySelectedBy for CustomControl for View (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-customcontrol-format.md)|<span data-ttu-id="75841-118">Hiermee definieert u een voor waarde die moet bestaan voor het gebruik van de controle definitie.</span><span class="sxs-lookup"><span data-stu-id="75841-118">Defines a condition that must exist for the control definition to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="75841-119">Tekstwaarde</span><span class="sxs-lookup"><span data-stu-id="75841-119">Text Value</span></span>

<span data-ttu-id="75841-120">Geef het script op dat wordt geëvalueerd.</span><span class="sxs-lookup"><span data-stu-id="75841-120">Specify the script that is evaluated.</span></span>

## <a name="remarks"></a><span data-ttu-id="75841-121">Opmerkingen</span><span class="sxs-lookup"><span data-stu-id="75841-121">Remarks</span></span>

<span data-ttu-id="75841-122">Voor de selectie voorwaarde moet ten minste één script of eigenschaps naam worden opgegeven die moet worden geëvalueerd, maar kan niet beide worden opgegeven.</span><span class="sxs-lookup"><span data-stu-id="75841-122">The selection condition must specify a least one script or property name to evaluate, but cannot specify both.</span></span> <span data-ttu-id="75841-123">Zie voor [waarden definiëren voor het weer geven van gegevens](./defining-conditions-for-displaying-data.md)voor meer informatie over hoe selectie omstandigheden kunnen worden gebruikt.</span><span class="sxs-lookup"><span data-stu-id="75841-123">For more information about how selection conditions can be used, see [Defining Conditions for Displaying Data](./defining-conditions-for-displaying-data.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="75841-124">Zie ook</span><span class="sxs-lookup"><span data-stu-id="75841-124">See Also</span></span>

[<span data-ttu-id="75841-125">SelectionCondition-element voor EntrySelectedBy voor CustomControl voor weer gave (indeling)</span><span class="sxs-lookup"><span data-stu-id="75841-125">SelectionCondition Element for EntrySelectedBy for CustomControl for View (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-customcontrol-format.md)

[<span data-ttu-id="75841-126">Een PowerShell-opmaakbestand schrijven</span><span class="sxs-lookup"><span data-stu-id="75841-126">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
