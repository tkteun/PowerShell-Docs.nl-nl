---
title: TypeName-Element voor SelectionCondition voor besturingselementen voor weergave (indeling) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 7141aefc-6656-4c52-8a9c-c2bfc9c87be9
caps.latest.revision: 6
ms.openlocfilehash: 7a697c286ec9efe750930739cdfa2580003365dd
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62083897"
---
# <a name="typename-element-for-selectioncondition-for-controls-for-view-format"></a><span data-ttu-id="e04a6-102">Het element TypeName voor SelectionCondition voor Besturingselementen voor Weergave (opmaak)</span><span class="sxs-lookup"><span data-stu-id="e04a6-102">TypeName Element for SelectionCondition for Controls for View (Format)</span></span>

<span data-ttu-id="e04a6-103">Hiermee geeft u een .NET-type dat de voorwaarde wordt geactiveerd.</span><span class="sxs-lookup"><span data-stu-id="e04a6-103">Specifies a .NET type that triggers the condition.</span></span> <span data-ttu-id="e04a6-104">Dit element wordt gebruikt bij het definiëren van besturingselementen die kunnen worden gebruikt door een weergave.</span><span class="sxs-lookup"><span data-stu-id="e04a6-104">This element is used when defining controls that can be used by a view.</span></span>

<span data-ttu-id="e04a6-105">Configuratie-Element (indeling) ViewDefinitions-Element (indeling) weergave-Element (indeling) besturingselementen Element (indeling) controle-Element voor besturingselementen voor weergave (indeling) CustomControl Element voor de controle voor besturingselementen voor weergave (indeling) CustomEntries Element voor CustomControl voor besturingselementen voor weergave (indeling) CustomEntry Element voor CustomEntries voor besturingselementen voor weergave (indeling) EntrySelectedBy Element voor CustomEntry voor besturingselementen voor weergave (indeling) SelectionCondition Element voor EntrySelectedBy voor besturingselementen voor weergave ( TypeName-Element voor SelectionCondition voor besturingselementen voor weergave (indeling)-indeling)</span><span class="sxs-lookup"><span data-stu-id="e04a6-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) Controls Element (Format) Control Element for Controls for View (Format) CustomControl Element for Control for Controls for View (Format) CustomEntries Element for CustomControl for Controls for View (Format) CustomEntry Element for CustomEntries for Controls for View (Format) EntrySelectedBy Element for CustomEntry for Controls for View (Format) SelectionCondition Element for EntrySelectedBy for Controls for View (Format) TypeName Element for SelectionCondition for Controls for View (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="e04a6-106">Syntaxis</span><span class="sxs-lookup"><span data-stu-id="e04a6-106">Syntax</span></span>

```xml
<TypeName>Nameof.NetType</TypeName>

```

## <a name="attributes-and-elements"></a><span data-ttu-id="e04a6-107">Kenmerken en elementen</span><span class="sxs-lookup"><span data-stu-id="e04a6-107">Attributes and Elements</span></span>

<span data-ttu-id="e04a6-108">De volgende secties beschrijven kenmerken, onderliggende elementen en het bovenliggende element van de `TypeName` Element.</span><span class="sxs-lookup"><span data-stu-id="e04a6-108">The following sections describe attributes, child elements, and the parent element of the `TypeName` Element.</span></span>

### <a name="attributes"></a><span data-ttu-id="e04a6-109">Kenmerken</span><span class="sxs-lookup"><span data-stu-id="e04a6-109">Attributes</span></span>

<span data-ttu-id="e04a6-110">Geen.</span><span class="sxs-lookup"><span data-stu-id="e04a6-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="e04a6-111">Onderliggende elementen</span><span class="sxs-lookup"><span data-stu-id="e04a6-111">Child Elements</span></span>

<span data-ttu-id="e04a6-112">Geen.</span><span class="sxs-lookup"><span data-stu-id="e04a6-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="e04a6-113">Bovenliggende elementen</span><span class="sxs-lookup"><span data-stu-id="e04a6-113">Parent Elements</span></span>

|<span data-ttu-id="e04a6-114">Element</span><span class="sxs-lookup"><span data-stu-id="e04a6-114">Element</span></span>|<span data-ttu-id="e04a6-115">Description</span><span class="sxs-lookup"><span data-stu-id="e04a6-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="e04a6-116">SelectionCondition-Element voor EntrySelectedBy voor besturingselementen voor weergave (indeling)</span><span class="sxs-lookup"><span data-stu-id="e04a6-116">SelectionCondition Element for EntrySelectedBy for Controls for View (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-controls-for-view-format.md)|<span data-ttu-id="e04a6-117">Hiermee definieert u een voorwaarde die moet aanwezig zijn voor de besturingselementdefinitie van het moet worden gebruikt.</span><span class="sxs-lookup"><span data-stu-id="e04a6-117">Defines a condition that must exist for the control definition to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="e04a6-118">Tekstwaarde</span><span class="sxs-lookup"><span data-stu-id="e04a6-118">Text Value</span></span>

<span data-ttu-id="e04a6-119">Geef de volledig gekwalificeerde naam van het .NET-type, bijvoorbeeld `System.IO.DirectoryInfo`.</span><span class="sxs-lookup"><span data-stu-id="e04a6-119">Specify the fully qualified name of the .NET type, such as `System.IO.DirectoryInfo`.</span></span>

## <a name="remarks"></a><span data-ttu-id="e04a6-120">Opmerkingen</span><span class="sxs-lookup"><span data-stu-id="e04a6-120">Remarks</span></span>

## <a name="see-also"></a><span data-ttu-id="e04a6-121">Zie ook</span><span class="sxs-lookup"><span data-stu-id="e04a6-121">See Also</span></span>

[<span data-ttu-id="e04a6-122">SelectionCondition-Element voor EntrySelectedBy voor besturingselementen voor weergave (indeling)</span><span class="sxs-lookup"><span data-stu-id="e04a6-122">SelectionCondition Element for EntrySelectedBy for Controls for View (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-controls-for-view-format.md)

[<span data-ttu-id="e04a6-123">Schrijven van een bestand opmaak PowerShell</span><span class="sxs-lookup"><span data-stu-id="e04a6-123">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
