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
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62064421"
---
# <a name="scriptblock-element-for-selectioncondition-for-controls-for-configuration-format"></a><span data-ttu-id="cfa3f-102">Het element ScriptBlock voor SelectionCondition voor Besturingselementen voor Configuratie (opmaak)</span><span class="sxs-lookup"><span data-stu-id="cfa3f-102">ScriptBlock Element for SelectionCondition for Controls for Configuration (Format)</span></span>

<span data-ttu-id="cfa3f-103">Hiermee geeft u het script dat de voorwaarde wordt geactiveerd.</span><span class="sxs-lookup"><span data-stu-id="cfa3f-103">Specifies the script that triggers the condition.</span></span> <span data-ttu-id="cfa3f-104">Wanneer dit script wordt geëvalueerd naar `true`, de voorwaarde wordt voldaan en de definitie wordt gebruikt.</span><span class="sxs-lookup"><span data-stu-id="cfa3f-104">When this script is evaluated to `true`, the condition is met, and the definition is used.</span></span> <span data-ttu-id="cfa3f-105">Dit element wordt gebruikt bij het definiëren van een algemene besturingselement dat kan worden gebruikt door alle weergaven in de opmaak-bestand.</span><span class="sxs-lookup"><span data-stu-id="cfa3f-105">This element is used when defining a common control that can be used by all the views in the formatting file.</span></span>

<span data-ttu-id="cfa3f-106">Configuratie-Element (indeling) besturingselementen Element van configuratie (-indeling) besturingselement Element controles voor configuratie (-indeling) CustomControl-Element voor het besturingselement voor configuratie (-indeling) CustomEntries-Element voor CustomControl voor configuratie ( -Indeling) CustomEntry Element voor CustomControl controles voor configuratie (-indeling) EntrySelectedBy-Element voor CustomEntry controles voor configuratie (-indeling) SelectionCondition-Element voor EntrySelectedBy voor besturingselementen voor de configuratie (-indeling) ScriptBlock-Element voor SelectionCondition voor besturingselementen voor de configuratie (-indeling)</span><span class="sxs-lookup"><span data-stu-id="cfa3f-106">Configuration Element (Format) Controls Element of Configuration (Format) Control Element for Controls for Configuration (Format) CustomControl Element for Control for Configuration (Format) CustomEntries Element for CustomControl for Configuration (Format) CustomEntry Element for CustomControl for Controls for Configuration (Format) EntrySelectedBy Element for CustomEntry for Controls for Configuration (Format) SelectionCondition Element for EntrySelectedBy for Controls for Configuration (Format) ScriptBlock Element for SelectionCondition for Controls for Configuration (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="cfa3f-107">Syntaxis</span><span class="sxs-lookup"><span data-stu-id="cfa3f-107">Syntax</span></span>

```xml
<ScriptBlock>ScriptToEvaluate</ScriptBlock>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="cfa3f-108">Kenmerken en elementen</span><span class="sxs-lookup"><span data-stu-id="cfa3f-108">Attributes and Elements</span></span>

<span data-ttu-id="cfa3f-109">De volgende secties beschrijven kenmerken, onderliggende elementen en het bovenliggende element van de `ScriptBlock` element.</span><span class="sxs-lookup"><span data-stu-id="cfa3f-109">The following sections describe attributes, child elements, and the parent element of the `ScriptBlock` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="cfa3f-110">Kenmerken</span><span class="sxs-lookup"><span data-stu-id="cfa3f-110">Attributes</span></span>

<span data-ttu-id="cfa3f-111">Geen.</span><span class="sxs-lookup"><span data-stu-id="cfa3f-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="cfa3f-112">Onderliggende elementen</span><span class="sxs-lookup"><span data-stu-id="cfa3f-112">Child Elements</span></span>

<span data-ttu-id="cfa3f-113">Geen.</span><span class="sxs-lookup"><span data-stu-id="cfa3f-113">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="cfa3f-114">Bovenliggende elementen</span><span class="sxs-lookup"><span data-stu-id="cfa3f-114">Parent Elements</span></span>

|<span data-ttu-id="cfa3f-115">Element</span><span class="sxs-lookup"><span data-stu-id="cfa3f-115">Element</span></span>|<span data-ttu-id="cfa3f-116">Description</span><span class="sxs-lookup"><span data-stu-id="cfa3f-116">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="cfa3f-117">SelectionCondition-Element voor EntrySelectedBy voor besturingselementen voor de configuratie (-indeling)</span><span class="sxs-lookup"><span data-stu-id="cfa3f-117">SelectionCondition Element for EntrySelectedBy for Controls for Configuration (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-controls-for-configuration-format.md)|<span data-ttu-id="cfa3f-118">Hiermee definieert u een voorwaarde die moet aanwezig zijn voor de definitie van de algemene controle moet worden gebruikt.</span><span class="sxs-lookup"><span data-stu-id="cfa3f-118">Defines a condition that must exist for the common control definition to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="cfa3f-119">Tekstwaarde</span><span class="sxs-lookup"><span data-stu-id="cfa3f-119">Text Value</span></span>

<span data-ttu-id="cfa3f-120">Geef het script dat wordt geëvalueerd.</span><span class="sxs-lookup"><span data-stu-id="cfa3f-120">Specify the script that is evaluated.</span></span>

## <a name="remarks"></a><span data-ttu-id="cfa3f-121">Opmerkingen</span><span class="sxs-lookup"><span data-stu-id="cfa3f-121">Remarks</span></span>

<span data-ttu-id="cfa3f-122">De selectievoorwaarde moet een minimaal één script of de eigenschap naam opgeven om te evalueren, maar u kunt niet beide opgeven.</span><span class="sxs-lookup"><span data-stu-id="cfa3f-122">The selection condition must specify a least one script or property name to evaluate, but cannot specify both.</span></span> <span data-ttu-id="cfa3f-123">Zie voor meer informatie over hoe voorwaarden van de selectie kunnen worden gebruikt, [voorwaarden definiëren voor het weergeven van gegevens](./defining-conditions-for-displaying-data.md).</span><span class="sxs-lookup"><span data-stu-id="cfa3f-123">For more information about how selection conditions can be used, see [Defining Conditions for Displaying Data](./defining-conditions-for-displaying-data.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="cfa3f-124">Zie ook</span><span class="sxs-lookup"><span data-stu-id="cfa3f-124">See Also</span></span>

[<span data-ttu-id="cfa3f-125">SelectionCondition-Element voor EntrySelectedBy voor besturingselementen voor de configuratie (-indeling)</span><span class="sxs-lookup"><span data-stu-id="cfa3f-125">SelectionCondition Element for EntrySelectedBy for Controls for Configuration (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-controls-for-configuration-format.md)

[<span data-ttu-id="cfa3f-126">Schrijven van een bestand opmaak PowerShell</span><span class="sxs-lookup"><span data-stu-id="cfa3f-126">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
