---
title: TypeName-Element voor SelectionCondition voor GroupBy (indeling) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 290d38e3-b9bd-4382-9671-2e28b32b7260
caps.latest.revision: 6
ms.openlocfilehash: a4036b1e9de85da7e0029e02cca9e0eaed462f70
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62083770"
---
# <a name="typename-element-for-selectioncondition-for-groupby-format"></a><span data-ttu-id="bf80a-102">Het element TypeName voor SelectionCondition voor GroupBy (opmaak)</span><span class="sxs-lookup"><span data-stu-id="bf80a-102">TypeName Element for SelectionCondition for GroupBy (Format)</span></span>

<span data-ttu-id="bf80a-103">Hiermee geeft u een .NET-type dat de voorwaarde wordt geactiveerd.</span><span class="sxs-lookup"><span data-stu-id="bf80a-103">Specifies a .NET type that triggers the condition.</span></span> <span data-ttu-id="bf80a-104">Dit element wordt gebruikt bij het definiëren van hoe een nieuwe groep objecten worden weergegeven.</span><span class="sxs-lookup"><span data-stu-id="bf80a-104">This element is used when defining how a new group of objects is displayed.</span></span>

<span data-ttu-id="bf80a-105">Configuratie van Element (indeling) ViewDefinitions-Element (indeling) weergave Element (indeling) GroupBy Element voor weergave (indeling) CustomControl Element voor GroupBy (indeling) CustomEntries Element voor CustomControl voor GroupBy (indeling) CustomEntry Element voor CustomControl voor GroupBy (indeling) EntrySelectedBy Element voor CustomEntry voor GroupBy (indeling) SelectionCondition Element voor EntrySelectedBy voor GroupBy (indeling) TypeName Element voor SelectionCondition voor GroupBy (indeling)</span><span class="sxs-lookup"><span data-stu-id="bf80a-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) GroupBy Element for View (Format) CustomControl Element for GroupBy (Format) CustomEntries Element for CustomControl for GroupBy (Format) CustomEntry Element for CustomControl for GroupBy (Format) EntrySelectedBy Element for CustomEntry for GroupBy (Format) SelectionCondition Element for EntrySelectedBy for GroupBy (Format) TypeName Element for SelectionCondition for GroupBy  (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="bf80a-106">Syntaxis</span><span class="sxs-lookup"><span data-stu-id="bf80a-106">Syntax</span></span>

```xml
<TypeName>Nameof.NetType</TypeName>

```

## <a name="attributes-and-elements"></a><span data-ttu-id="bf80a-107">Kenmerken en elementen</span><span class="sxs-lookup"><span data-stu-id="bf80a-107">Attributes and Elements</span></span>

<span data-ttu-id="bf80a-108">De volgende secties beschrijven kenmerken, onderliggende elementen en het bovenliggende element van de `TypeName` Element.</span><span class="sxs-lookup"><span data-stu-id="bf80a-108">The following sections describe attributes, child elements, and the parent element of the `TypeName` Element.</span></span>

### <a name="attributes"></a><span data-ttu-id="bf80a-109">Kenmerken</span><span class="sxs-lookup"><span data-stu-id="bf80a-109">Attributes</span></span>

<span data-ttu-id="bf80a-110">Geen.</span><span class="sxs-lookup"><span data-stu-id="bf80a-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="bf80a-111">Onderliggende elementen</span><span class="sxs-lookup"><span data-stu-id="bf80a-111">Child Elements</span></span>

<span data-ttu-id="bf80a-112">Geen.</span><span class="sxs-lookup"><span data-stu-id="bf80a-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="bf80a-113">Bovenliggende elementen</span><span class="sxs-lookup"><span data-stu-id="bf80a-113">Parent Elements</span></span>

|<span data-ttu-id="bf80a-114">Element</span><span class="sxs-lookup"><span data-stu-id="bf80a-114">Element</span></span>|<span data-ttu-id="bf80a-115">Description</span><span class="sxs-lookup"><span data-stu-id="bf80a-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="bf80a-116">SelectionCondition-Element voor EntrySelectedBy voor GroupBy (indeling)</span><span class="sxs-lookup"><span data-stu-id="bf80a-116">SelectionCondition Element for EntrySelectedBy for GroupBy (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-groupby-format.md)|<span data-ttu-id="bf80a-117">Hiermee definieert u een voorwaarde die moet aanwezig zijn voor de besturingselementdefinitie van het moet worden gebruikt.</span><span class="sxs-lookup"><span data-stu-id="bf80a-117">Defines a condition that must exist for the control definition to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="bf80a-118">Tekstwaarde</span><span class="sxs-lookup"><span data-stu-id="bf80a-118">Text Value</span></span>

<span data-ttu-id="bf80a-119">Geef de volledig gekwalificeerde naam van het .NET-type, bijvoorbeeld `System.IO.DirectoryInfo`.</span><span class="sxs-lookup"><span data-stu-id="bf80a-119">Specify the fully qualified name of the .NET type, such as `System.IO.DirectoryInfo`.</span></span>

## <a name="remarks"></a><span data-ttu-id="bf80a-120">Opmerkingen</span><span class="sxs-lookup"><span data-stu-id="bf80a-120">Remarks</span></span>

<span data-ttu-id="bf80a-121">Wanneer dit element is opgegeven, wordt u niet opgeven de `SelectionSetName` element.</span><span class="sxs-lookup"><span data-stu-id="bf80a-121">When this element is specified, you cannot specify the `SelectionSetName` element.</span></span> <span data-ttu-id="bf80a-122">Zie voor meer informatie over het definiëren van de voorwaarden van de selectie [voorwaarden definiëren voor het weergeven van gegevens](./defining-conditions-for-displaying-data.md).</span><span class="sxs-lookup"><span data-stu-id="bf80a-122">For more information about defining selection conditions, see [Defining Conditions for Displaying Data](./defining-conditions-for-displaying-data.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="bf80a-123">Zie ook</span><span class="sxs-lookup"><span data-stu-id="bf80a-123">See Also</span></span>

[<span data-ttu-id="bf80a-124">SelectionCondition-Element voor EntrySelectedBy voor GroupBy (indeling)</span><span class="sxs-lookup"><span data-stu-id="bf80a-124">SelectionCondition Element for EntrySelectedBy for GroupBy (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-groupby-format.md)

[<span data-ttu-id="bf80a-125">Schrijven van een bestand opmaak PowerShell</span><span class="sxs-lookup"><span data-stu-id="bf80a-125">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
