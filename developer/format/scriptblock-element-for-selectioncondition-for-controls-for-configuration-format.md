---
title: ScriptBlock-Element voor SelectionCondition voor besturingselementen voor de configuratie (-indeling) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: bb032dfc-9ef6-403c-b557-5858617e3483
caps.latest.revision: 6
ms.openlocfilehash: 102987970152420896a0c986f0973280ae209623
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 02/03/2019
ms.locfileid: "56844861"
---
# <a name="scriptblock-element-for-selectioncondition-for-controls-for-configuration-format"></a><span data-ttu-id="84825-102">Het element ScriptBlock voor SelectionCondition voor Besturingselementen voor Configuratie (opmaak)</span><span class="sxs-lookup"><span data-stu-id="84825-102">ScriptBlock Element for SelectionCondition for Controls for Configuration (Format)</span></span>

<span data-ttu-id="84825-103">Hiermee geeft u het script dat de voorwaarde wordt geactiveerd.</span><span class="sxs-lookup"><span data-stu-id="84825-103">Specifies the script that triggers the condition.</span></span> <span data-ttu-id="84825-104">Wanneer dit script wordt geëvalueerd naar `true`, de voorwaarde wordt voldaan en de definitie wordt gebruikt.</span><span class="sxs-lookup"><span data-stu-id="84825-104">When this script is evaluated to `true`, the condition is met, and the definition is used.</span></span> <span data-ttu-id="84825-105">Dit element wordt gebruikt bij het definiëren van een algemene besturingselement dat kan worden gebruikt door alle weergaven in de opmaak-bestand.</span><span class="sxs-lookup"><span data-stu-id="84825-105">This element is used when defining a common control that can be used by all the views in the formatting file.</span></span>

<span data-ttu-id="84825-106">Configuratie-Element (indeling) besturingselementen Element van configuratie (-indeling) besturingselement Element controles voor configuratie (-indeling) CustomControl-Element voor het besturingselement voor configuratie (-indeling) CustomEntries-Element voor CustomControl voor configuratie ( -Indeling) CustomEntry Element voor CustomControl controles voor configuratie (-indeling) EntrySelectedBy-Element voor CustomEntry controles voor configuratie (-indeling) SelectionCondition-Element voor EntrySelectedBy voor besturingselementen voor de configuratie (-indeling) ScriptBlock-Element voor SelectionCondition voor besturingselementen voor de configuratie (-indeling)</span><span class="sxs-lookup"><span data-stu-id="84825-106">Configuration Element (Format) Controls Element of Configuration (Format) Control Element for Controls for Configuration (Format) CustomControl Element for Control for Configuration (Format) CustomEntries Element for CustomControl for Configuration (Format) CustomEntry Element for CustomControl for Controls for Configuration (Format) EntrySelectedBy Element for CustomEntry for Controls for Configuration (Format) SelectionCondition Element for EntrySelectedBy for Controls for Configuration (Format) ScriptBlock Element for SelectionCondition for Controls for Configuration (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="84825-107">Syntaxis</span><span class="sxs-lookup"><span data-stu-id="84825-107">Syntax</span></span>

```xml
<ScriptBlock>ScriptToEvaluate</ScriptBlock>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="84825-108">Kenmerken en elementen</span><span class="sxs-lookup"><span data-stu-id="84825-108">Attributes and Elements</span></span>

<span data-ttu-id="84825-109">De volgende secties beschrijven kenmerken, onderliggende elementen en het bovenliggende element van de `ScriptBlock` element.</span><span class="sxs-lookup"><span data-stu-id="84825-109">The following sections describe attributes, child elements, and the parent element of the `ScriptBlock` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="84825-110">Kenmerken</span><span class="sxs-lookup"><span data-stu-id="84825-110">Attributes</span></span>

<span data-ttu-id="84825-111">Geen.</span><span class="sxs-lookup"><span data-stu-id="84825-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="84825-112">Onderliggende elementen</span><span class="sxs-lookup"><span data-stu-id="84825-112">Child Elements</span></span>

<span data-ttu-id="84825-113">Geen.</span><span class="sxs-lookup"><span data-stu-id="84825-113">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="84825-114">Bovenliggende elementen</span><span class="sxs-lookup"><span data-stu-id="84825-114">Parent Elements</span></span>

|<span data-ttu-id="84825-115">Element</span><span class="sxs-lookup"><span data-stu-id="84825-115">Element</span></span>|<span data-ttu-id="84825-116">Description</span><span class="sxs-lookup"><span data-stu-id="84825-116">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="84825-117">SelectionCondition-Element voor EntrySelectedBy voor besturingselementen voor de configuratie (-indeling)</span><span class="sxs-lookup"><span data-stu-id="84825-117">SelectionCondition Element for EntrySelectedBy for Controls for Configuration (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-controls-for-configuration-format.md)|<span data-ttu-id="84825-118">Hiermee definieert u een voorwaarde die moet aanwezig zijn voor de definitie van de algemene controle moet worden gebruikt.</span><span class="sxs-lookup"><span data-stu-id="84825-118">Defines a condition that must exist for the common control definition to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="84825-119">Tekstwaarde</span><span class="sxs-lookup"><span data-stu-id="84825-119">Text Value</span></span>

<span data-ttu-id="84825-120">Geef het script dat wordt geëvalueerd.</span><span class="sxs-lookup"><span data-stu-id="84825-120">Specify the script that is evaluated.</span></span>

## <a name="remarks"></a><span data-ttu-id="84825-121">Opmerkingen</span><span class="sxs-lookup"><span data-stu-id="84825-121">Remarks</span></span>

<span data-ttu-id="84825-122">De selectievoorwaarde moet een minimaal één script of de eigenschap naam opgeven om te evalueren, maar u kunt niet beide opgeven.</span><span class="sxs-lookup"><span data-stu-id="84825-122">The selection condition must specify a least one script or property name to evaluate, but cannot specify both.</span></span> <span data-ttu-id="84825-123">Zie voor meer informatie over hoe voorwaarden van de selectie kunnen worden gebruikt, [voorwaarden definiëren voor het weergeven van gegevens](./defining-conditions-for-displaying-data.md).</span><span class="sxs-lookup"><span data-stu-id="84825-123">For more information about how selection conditions can be used, see [Defining Conditions for Displaying Data](./defining-conditions-for-displaying-data.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="84825-124">Zie ook</span><span class="sxs-lookup"><span data-stu-id="84825-124">See Also</span></span>

[<span data-ttu-id="84825-125">SelectionCondition-Element voor EntrySelectedBy voor besturingselementen voor de configuratie (-indeling)</span><span class="sxs-lookup"><span data-stu-id="84825-125">SelectionCondition Element for EntrySelectedBy for Controls for Configuration (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-controls-for-configuration-format.md)

[<span data-ttu-id="84825-126">Schrijven van een bestand opmaak PowerShell</span><span class="sxs-lookup"><span data-stu-id="84825-126">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
