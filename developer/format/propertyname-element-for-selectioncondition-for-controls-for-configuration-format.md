---
title: PropertyName-Element voor SelectionCondition voor besturingselementen voor de configuratie (-indeling) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: ec048408-e1c6-41ef-b39b-72f4c2dcf2ac
caps.latest.revision: 6
ms.openlocfilehash: b4b2440fdb7171d09fdc16ac7cc4f25ed1a4bb78
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 02/03/2019
ms.locfileid: "56850328"
---
# <a name="propertyname-element-for-selectioncondition-for-controls-for-configuration-format"></a><span data-ttu-id="1e787-102">Het element PropertyName voor SelectionCondition voor Besturingselementen voor Configuratie (opmaak)</span><span class="sxs-lookup"><span data-stu-id="1e787-102">PropertyName Element for SelectionCondition for Controls for Configuration (Format)</span></span>

<span data-ttu-id="1e787-103">Hiermee geeft u de .NET-eigenschap die de voorwaarde wordt geactiveerd.</span><span class="sxs-lookup"><span data-stu-id="1e787-103">Specifies the .NET property that triggers the condition.</span></span> <span data-ttu-id="1e787-104">Als deze eigenschap is aanwezig, of wanneer deze wordt geëvalueerd naar `true`, de voorwaarde wordt voldaan en de vermelding wordt gebruikt.</span><span class="sxs-lookup"><span data-stu-id="1e787-104">When this property is present or when it evaluates to `true`, the condition is met, and the entry is used.</span></span> <span data-ttu-id="1e787-105">Dit element wordt gebruikt bij het definiëren van een algemene besturingselement dat kan worden gebruikt door alle weergaven in de opmaak-bestand.</span><span class="sxs-lookup"><span data-stu-id="1e787-105">This element is used when defining a common control that can be used by all the views in the formatting file.</span></span>

<span data-ttu-id="1e787-106">Configuratie-Element (indeling) besturingselementen Element van configuratie (-indeling) besturingselement Element controles voor configuratie (-indeling) CustomControl-Element voor het besturingselement voor configuratie (-indeling) CustomEntries-Element voor CustomControl voor configuratie ( CustomEntry-Element voor CustomControl controles voor configuratie (-indeling) EntrySelectedBy-Element voor CustomEntry controles voor configuratie (-indeling) SelectionCondition-Element voor EntrySelectedBy voor CustomEntry voor configuratie (-indeling) -Indeling) PropertyName-Element voor SelectionCondition voor EntrySelectedBy voor ListEntry (indeling)</span><span class="sxs-lookup"><span data-stu-id="1e787-106">Configuration Element (Format) Controls Element of Configuration (Format) Control Element for Controls for Configuration (Format) CustomControl Element for Control for Configuration (Format) CustomEntries Element for CustomControl for Configuration (Format) CustomEntry Element for CustomControl for Controls for Configuration (Format) EntrySelectedBy Element for CustomEntry for Controls for Configuration (Format) SelectionCondition Element for EntrySelectedBy for CustomEntry for Configuration (Format) PropertyName Element for SelectionCondition for EntrySelectedBy for ListEntry (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="1e787-107">Syntaxis</span><span class="sxs-lookup"><span data-stu-id="1e787-107">Syntax</span></span>

```xml
<PropertyName>.NetTypeProperty</PropertyName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="1e787-108">Kenmerken en elementen</span><span class="sxs-lookup"><span data-stu-id="1e787-108">Attributes and Elements</span></span>

<span data-ttu-id="1e787-109">De volgende secties beschrijven kenmerken, onderliggende elementen en het bovenliggende element van de `PropertyName` element.</span><span class="sxs-lookup"><span data-stu-id="1e787-109">The following sections describe attributes, child elements, and the parent element of the `PropertyName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="1e787-110">Kenmerken</span><span class="sxs-lookup"><span data-stu-id="1e787-110">Attributes</span></span>

<span data-ttu-id="1e787-111">Geen.</span><span class="sxs-lookup"><span data-stu-id="1e787-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="1e787-112">Onderliggende elementen</span><span class="sxs-lookup"><span data-stu-id="1e787-112">Child Elements</span></span>

<span data-ttu-id="1e787-113">Geen.</span><span class="sxs-lookup"><span data-stu-id="1e787-113">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="1e787-114">Bovenliggende elementen</span><span class="sxs-lookup"><span data-stu-id="1e787-114">Parent Elements</span></span>

|<span data-ttu-id="1e787-115">Element</span><span class="sxs-lookup"><span data-stu-id="1e787-115">Element</span></span>|<span data-ttu-id="1e787-116">Description</span><span class="sxs-lookup"><span data-stu-id="1e787-116">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="1e787-117">SelectionCondition-Element voor EntrySelectedBy voor besturingselementen voor de configuratie (-indeling)</span><span class="sxs-lookup"><span data-stu-id="1e787-117">SelectionCondition Element for EntrySelectedBy for Controls for Configuration (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-controls-for-configuration-format.md)|<span data-ttu-id="1e787-118">Hiermee definieert u een voorwaarde die moet aanwezig zijn voor de besturingselementdefinitie van een algemene moet worden gebruikt.</span><span class="sxs-lookup"><span data-stu-id="1e787-118">Defines a condition that must exist for a common control definition to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="1e787-119">Tekstwaarde</span><span class="sxs-lookup"><span data-stu-id="1e787-119">Text Value</span></span>

<span data-ttu-id="1e787-120">Geef de naam van de .NET-eigenschap.</span><span class="sxs-lookup"><span data-stu-id="1e787-120">Specify the .NET property name.</span></span>

## <a name="remarks"></a><span data-ttu-id="1e787-121">Opmerkingen</span><span class="sxs-lookup"><span data-stu-id="1e787-121">Remarks</span></span>

<span data-ttu-id="1e787-122">De selectievoorwaarde moet de naam van een minimaal één eigenschap of een script opgeven, maar u kunt niet beide opgeven.</span><span class="sxs-lookup"><span data-stu-id="1e787-122">The selection condition must specify a least one property name or a script, but cannot specify both.</span></span> <span data-ttu-id="1e787-123">Zie voor meer informatie over hoe voorwaarden van de selectie kunnen worden gebruikt, [voorwaarden definiëren voor het weergeven van gegevens](./defining-conditions-for-displaying-data.md).</span><span class="sxs-lookup"><span data-stu-id="1e787-123">For more information about how selection conditions can be used, see [Defining Conditions for Displaying Data](./defining-conditions-for-displaying-data.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="1e787-124">Zie ook</span><span class="sxs-lookup"><span data-stu-id="1e787-124">See Also</span></span>

[<span data-ttu-id="1e787-125">SelectionCondition-Element voor EntrySelectedBy voor besturingselementen voor de configuratie (-indeling)</span><span class="sxs-lookup"><span data-stu-id="1e787-125">SelectionCondition Element for EntrySelectedBy for Controls for Configuration (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-controls-for-configuration-format.md)

[<span data-ttu-id="1e787-126">Schrijven van een bestand opmaak PowerShell</span><span class="sxs-lookup"><span data-stu-id="1e787-126">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
