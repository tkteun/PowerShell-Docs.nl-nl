---
title: TypeName-Element voor SelectionCondition voor besturingselementen voor de configuratie (-indeling) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 477c8711-fffc-4f92-af45-6d4f80990474
caps.latest.revision: 7
ms.openlocfilehash: 60f02f3240c5574e1b1f9027b060bd9af89a11d2
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62083940"
---
# <a name="typename-element-for-selectioncondition-for-controls-for-configuration-format"></a><span data-ttu-id="83a90-102">Het element TypeName voor SelectionCondition voor Besturingselementen voor Configuratie (opmaak)</span><span class="sxs-lookup"><span data-stu-id="83a90-102">TypeName Element for SelectionCondition for Controls for Configuration (Format)</span></span>

<span data-ttu-id="83a90-103">Hiermee geeft u een .NET-type dat de voorwaarde wordt geactiveerd.</span><span class="sxs-lookup"><span data-stu-id="83a90-103">Specifies a .NET type that triggers the condition.</span></span> <span data-ttu-id="83a90-104">Dit element wordt gebruikt bij het definiëren van een algemene besturingselement dat kan worden gebruikt door alle weergaven in de opmaak-bestand.</span><span class="sxs-lookup"><span data-stu-id="83a90-104">This element is used when defining a common control that can be used by all the views in the formatting file.</span></span>

<span data-ttu-id="83a90-105">Configuratie-Element (indeling) besturingselementen Element van configuratie (-indeling) besturingselement Element controles voor configuratie (-indeling) CustomControl-Element voor configuratie (-indeling) CustomEntries-Element voor CustomControl voor besturingselementen voor het besturingselement Configuratie (-indeling) CustomEntry-Element voor CustomControl controles voor configuratie (-indeling) EntrySelectedBy-Element voor CustomEntry controles voor configuratie (-indeling) SelectionCondition-Element voor EntrySelectedBy voor CustomEntry voor Configuratie (-indeling) TypeName-Element voor SelectionCondition voor besturingselementen voor de configuratie (-indeling)</span><span class="sxs-lookup"><span data-stu-id="83a90-105">Configuration Element (Format) Controls Element of Configuration (Format) Control Element for Controls for Configuration (Format) CustomControl Element for Control for Configuration (Format) CustomEntries Element for CustomControl for Controls for Configuration (Format) CustomEntry Element for CustomControl for Controls for Configuration (Format) EntrySelectedBy Element for CustomEntry for Controls for Configuration (Format) SelectionCondition Element for EntrySelectedBy for CustomEntry for Configuration (Format) TypeName Element for SelectionCondition for Controls for Configuration (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="83a90-106">Syntaxis</span><span class="sxs-lookup"><span data-stu-id="83a90-106">Syntax</span></span>

```xml
<TypeName>Nameof.NetType</TypeName>

```

## <a name="attributes-and-elements"></a><span data-ttu-id="83a90-107">Kenmerken en elementen</span><span class="sxs-lookup"><span data-stu-id="83a90-107">Attributes and Elements</span></span>

<span data-ttu-id="83a90-108">De volgende secties beschrijven kenmerken, onderliggende elementen en het bovenliggende element van de `TypeName` Element.</span><span class="sxs-lookup"><span data-stu-id="83a90-108">The following sections describe attributes, child elements, and the parent element of the `TypeName` Element.</span></span>

### <a name="attributes"></a><span data-ttu-id="83a90-109">Kenmerken</span><span class="sxs-lookup"><span data-stu-id="83a90-109">Attributes</span></span>

<span data-ttu-id="83a90-110">Geen.</span><span class="sxs-lookup"><span data-stu-id="83a90-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="83a90-111">Onderliggende elementen</span><span class="sxs-lookup"><span data-stu-id="83a90-111">Child Elements</span></span>

<span data-ttu-id="83a90-112">Geen.</span><span class="sxs-lookup"><span data-stu-id="83a90-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="83a90-113">Bovenliggende elementen</span><span class="sxs-lookup"><span data-stu-id="83a90-113">Parent Elements</span></span>

|<span data-ttu-id="83a90-114">Element</span><span class="sxs-lookup"><span data-stu-id="83a90-114">Element</span></span>|<span data-ttu-id="83a90-115">Description</span><span class="sxs-lookup"><span data-stu-id="83a90-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="83a90-116">SelectionCondition-Element voor EntrySelectedBy voor CustomEntry voor configuratie (-indeling)</span><span class="sxs-lookup"><span data-stu-id="83a90-116">SelectionCondition Element for EntrySelectedBy for CustomEntry for Configuration (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-controls-for-configuration-format.md)|<span data-ttu-id="83a90-117">Hiermee definieert u een voorwaarde die moet aanwezig zijn voor de besturingselementdefinitie van het moet worden gebruikt.</span><span class="sxs-lookup"><span data-stu-id="83a90-117">Defines a condition that must exist for the control definition to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="83a90-118">Tekstwaarde</span><span class="sxs-lookup"><span data-stu-id="83a90-118">Text Value</span></span>

<span data-ttu-id="83a90-119">Geef de volledig gekwalificeerde naam van het .NET-type, bijvoorbeeld `System.IO.DirectoryInfo`.</span><span class="sxs-lookup"><span data-stu-id="83a90-119">Specify the fully qualified name of the .NET type, such as `System.IO.DirectoryInfo`.</span></span>

## <a name="remarks"></a><span data-ttu-id="83a90-120">Opmerkingen</span><span class="sxs-lookup"><span data-stu-id="83a90-120">Remarks</span></span>

## <a name="see-also"></a><span data-ttu-id="83a90-121">Zie ook</span><span class="sxs-lookup"><span data-stu-id="83a90-121">See Also</span></span>

[<span data-ttu-id="83a90-122">SelectionCondition-Element voor EntrySelectedBy voor CustomEntry voor configuratie (-indeling)</span><span class="sxs-lookup"><span data-stu-id="83a90-122">SelectionCondition Element for EntrySelectedBy for CustomEntry for Configuration (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-controls-for-configuration-format.md)

[<span data-ttu-id="83a90-123">Schrijven van een bestand opmaak PowerShell</span><span class="sxs-lookup"><span data-stu-id="83a90-123">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
