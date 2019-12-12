---
title: Script block-element voor SelectionCondition voor besturings elementen voor configuratie (indeling) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: bb032dfc-9ef6-403c-b557-5858617e3483
caps.latest.revision: 6
ms.openlocfilehash: 102987970152420896a0c986f0973280ae209623
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 12/05/2019
ms.locfileid: "72358954"
---
# <a name="scriptblock-element-for-selectioncondition-for-controls-for-configuration-format"></a><span data-ttu-id="85a92-102">Het element ScriptBlock voor SelectionCondition voor Besturingselementen voor Configuratie (opmaak)</span><span class="sxs-lookup"><span data-stu-id="85a92-102">ScriptBlock Element for SelectionCondition for Controls for Configuration (Format)</span></span>

<span data-ttu-id="85a92-103">Hiermee geeft u het script op waarmee de voor waarde wordt geactiveerd.</span><span class="sxs-lookup"><span data-stu-id="85a92-103">Specifies the script that triggers the condition.</span></span> <span data-ttu-id="85a92-104">Wanneer dit script wordt geëvalueerd om `true`, wordt aan de voor waarde voldaan en wordt de definitie gebruikt.</span><span class="sxs-lookup"><span data-stu-id="85a92-104">When this script is evaluated to `true`, the condition is met, and the definition is used.</span></span> <span data-ttu-id="85a92-105">Dit element wordt gebruikt bij het definiëren van een algemeen besturings element dat kan worden gebruikt door alle weer gaven in het opmaak bestand.</span><span class="sxs-lookup"><span data-stu-id="85a92-105">This element is used when defining a common control that can be used by all the views in the formatting file.</span></span>

<span data-ttu-id="85a92-106">Configuratie-element (Format) Controls element van configuratie (Format) Control element voor besturings elementen voor configuratie (Format) CustomControl-element voor Control for Configuration (Format) CustomEntries element voor het configureren van een configuratie ( Format) CustomEntry element voor CustomControl voor besturings elementen voor configuratie (indeling) EntrySelectedBy-element voor CustomEntry voor besturings elementen voor de configuratie (indeling) SelectionCondition element voor EntrySelectedBy voor besturings elementen voor configuratie (indeling) Script block-element voor SelectionCondition voor besturings elementen voor configuratie (indeling)</span><span class="sxs-lookup"><span data-stu-id="85a92-106">Configuration Element (Format) Controls Element of Configuration (Format) Control Element for Controls for Configuration (Format) CustomControl Element for Control for Configuration (Format) CustomEntries Element for CustomControl for Configuration (Format) CustomEntry Element for CustomControl for Controls for Configuration (Format) EntrySelectedBy Element for CustomEntry for Controls for Configuration (Format) SelectionCondition Element for EntrySelectedBy for Controls for Configuration (Format) ScriptBlock Element for SelectionCondition for Controls for Configuration (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="85a92-107">Syntaxis</span><span class="sxs-lookup"><span data-stu-id="85a92-107">Syntax</span></span>

```xml
<ScriptBlock>ScriptToEvaluate</ScriptBlock>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="85a92-108">Kenmerken en elementen</span><span class="sxs-lookup"><span data-stu-id="85a92-108">Attributes and Elements</span></span>

<span data-ttu-id="85a92-109">In de volgende secties worden kenmerken, onderliggende elementen en het bovenliggende element van het element `ScriptBlock` beschreven.</span><span class="sxs-lookup"><span data-stu-id="85a92-109">The following sections describe attributes, child elements, and the parent element of the `ScriptBlock` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="85a92-110">Kenmerken</span><span class="sxs-lookup"><span data-stu-id="85a92-110">Attributes</span></span>

<span data-ttu-id="85a92-111">Geen.</span><span class="sxs-lookup"><span data-stu-id="85a92-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="85a92-112">Onderliggende elementen</span><span class="sxs-lookup"><span data-stu-id="85a92-112">Child Elements</span></span>

<span data-ttu-id="85a92-113">Geen.</span><span class="sxs-lookup"><span data-stu-id="85a92-113">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="85a92-114">Bovenliggende elementen</span><span class="sxs-lookup"><span data-stu-id="85a92-114">Parent Elements</span></span>

|<span data-ttu-id="85a92-115">Element</span><span class="sxs-lookup"><span data-stu-id="85a92-115">Element</span></span>|<span data-ttu-id="85a92-116">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="85a92-116">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="85a92-117">SelectionCondition-element voor EntrySelectedBy voor besturings elementen voor configuratie (indeling)</span><span class="sxs-lookup"><span data-stu-id="85a92-117">SelectionCondition Element for EntrySelectedBy for Controls for Configuration (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-controls-for-configuration-format.md)|<span data-ttu-id="85a92-118">Hiermee definieert u een voor waarde die moet bestaan voor het gebruik van de algemene definitie van het besturings element.</span><span class="sxs-lookup"><span data-stu-id="85a92-118">Defines a condition that must exist for the common control definition to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="85a92-119">Tekstwaarde</span><span class="sxs-lookup"><span data-stu-id="85a92-119">Text Value</span></span>

<span data-ttu-id="85a92-120">Geef het script op dat wordt geëvalueerd.</span><span class="sxs-lookup"><span data-stu-id="85a92-120">Specify the script that is evaluated.</span></span>

## <a name="remarks"></a><span data-ttu-id="85a92-121">Opmerkingen</span><span class="sxs-lookup"><span data-stu-id="85a92-121">Remarks</span></span>

<span data-ttu-id="85a92-122">Voor de selectie voorwaarde moet ten minste één script of eigenschaps naam worden opgegeven die moet worden geëvalueerd, maar kan niet beide worden opgegeven.</span><span class="sxs-lookup"><span data-stu-id="85a92-122">The selection condition must specify a least one script or property name to evaluate, but cannot specify both.</span></span> <span data-ttu-id="85a92-123">Zie voor [waarden definiëren voor het weer geven van gegevens](./defining-conditions-for-displaying-data.md)voor meer informatie over hoe selectie omstandigheden kunnen worden gebruikt.</span><span class="sxs-lookup"><span data-stu-id="85a92-123">For more information about how selection conditions can be used, see [Defining Conditions for Displaying Data](./defining-conditions-for-displaying-data.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="85a92-124">Zie ook</span><span class="sxs-lookup"><span data-stu-id="85a92-124">See Also</span></span>

[<span data-ttu-id="85a92-125">SelectionCondition-element voor EntrySelectedBy voor besturings elementen voor configuratie (indeling)</span><span class="sxs-lookup"><span data-stu-id="85a92-125">SelectionCondition Element for EntrySelectedBy for Controls for Configuration (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-controls-for-configuration-format.md)

[<span data-ttu-id="85a92-126">Een Power shell-indelings bestand schrijven</span><span class="sxs-lookup"><span data-stu-id="85a92-126">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
