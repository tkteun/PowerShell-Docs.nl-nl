---
title: TypeName-element voor SelectionCondition voor GroupBy (indeling) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 290d38e3-b9bd-4382-9671-2e28b32b7260
caps.latest.revision: 6
ms.openlocfilehash: a4036b1e9de85da7e0029e02cca9e0eaed462f70
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 12/05/2019
ms.locfileid: "72353457"
---
# <a name="typename-element-for-selectioncondition-for-groupby-format"></a><span data-ttu-id="acf0d-102">Het element TypeName voor SelectionCondition voor GroupBy (opmaak)</span><span class="sxs-lookup"><span data-stu-id="acf0d-102">TypeName Element for SelectionCondition for GroupBy (Format)</span></span>

<span data-ttu-id="acf0d-103">Hiermee geeft u een .NET-type op waarmee de voor waarde wordt geactiveerd.</span><span class="sxs-lookup"><span data-stu-id="acf0d-103">Specifies a .NET type that triggers the condition.</span></span> <span data-ttu-id="acf0d-104">Dit element wordt gebruikt bij het definiëren van de manier waarop een nieuwe groep objecten wordt weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="acf0d-104">This element is used when defining how a new group of objects is displayed.</span></span>

<span data-ttu-id="acf0d-105">Configuratie-element (indeling) ViewDefinitions element (indeling) element voor weer gave (indeling) GroupBy-element (Format) voor weer gave (indeling) CustomControl-element voor het element GroupBy (indeling) CustomEntries voor CustomControl voor het element GroupBy (Format) CustomEntry voor CustomControl voor het element GroupBy (Format) EntrySelectedBy voor CustomEntry voor het element GroupBy (Format) SelectionCondition voor EntrySelectedBy voor het element GroupBy (Format) voor SelectionCondition voor GroupBy (indeling)</span><span class="sxs-lookup"><span data-stu-id="acf0d-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) GroupBy Element for View (Format) CustomControl Element for GroupBy (Format) CustomEntries Element for CustomControl for GroupBy (Format) CustomEntry Element for CustomControl for GroupBy (Format) EntrySelectedBy Element for CustomEntry for GroupBy (Format) SelectionCondition Element for EntrySelectedBy for GroupBy (Format) TypeName Element for SelectionCondition for GroupBy  (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="acf0d-106">Syntaxis</span><span class="sxs-lookup"><span data-stu-id="acf0d-106">Syntax</span></span>

```xml
<TypeName>Nameof.NetType</TypeName>

```

## <a name="attributes-and-elements"></a><span data-ttu-id="acf0d-107">Kenmerken en elementen</span><span class="sxs-lookup"><span data-stu-id="acf0d-107">Attributes and Elements</span></span>

<span data-ttu-id="acf0d-108">In de volgende secties worden kenmerken, onderliggende elementen en het bovenliggende element van het element `TypeName` beschreven.</span><span class="sxs-lookup"><span data-stu-id="acf0d-108">The following sections describe attributes, child elements, and the parent element of the `TypeName` Element.</span></span>

### <a name="attributes"></a><span data-ttu-id="acf0d-109">Kenmerken</span><span class="sxs-lookup"><span data-stu-id="acf0d-109">Attributes</span></span>

<span data-ttu-id="acf0d-110">Geen.</span><span class="sxs-lookup"><span data-stu-id="acf0d-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="acf0d-111">Onderliggende elementen</span><span class="sxs-lookup"><span data-stu-id="acf0d-111">Child Elements</span></span>

<span data-ttu-id="acf0d-112">Geen.</span><span class="sxs-lookup"><span data-stu-id="acf0d-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="acf0d-113">Bovenliggende elementen</span><span class="sxs-lookup"><span data-stu-id="acf0d-113">Parent Elements</span></span>

|<span data-ttu-id="acf0d-114">Element</span><span class="sxs-lookup"><span data-stu-id="acf0d-114">Element</span></span>|<span data-ttu-id="acf0d-115">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="acf0d-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="acf0d-116">SelectionCondition-element voor EntrySelectedBy voor GroupBy (indeling)</span><span class="sxs-lookup"><span data-stu-id="acf0d-116">SelectionCondition Element for EntrySelectedBy for GroupBy (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-groupby-format.md)|<span data-ttu-id="acf0d-117">Hiermee definieert u een voor waarde die moet bestaan voor het gebruik van de controle definitie.</span><span class="sxs-lookup"><span data-stu-id="acf0d-117">Defines a condition that must exist for the control definition to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="acf0d-118">Tekstwaarde</span><span class="sxs-lookup"><span data-stu-id="acf0d-118">Text Value</span></span>

<span data-ttu-id="acf0d-119">Geef de volledig gekwalificeerde naam van het .NET-type op, zoals `System.IO.DirectoryInfo`.</span><span class="sxs-lookup"><span data-stu-id="acf0d-119">Specify the fully qualified name of the .NET type, such as `System.IO.DirectoryInfo`.</span></span>

## <a name="remarks"></a><span data-ttu-id="acf0d-120">Opmerkingen</span><span class="sxs-lookup"><span data-stu-id="acf0d-120">Remarks</span></span>

<span data-ttu-id="acf0d-121">Als dit element is opgegeven, kunt u het `SelectionSetName`-element niet opgeven.</span><span class="sxs-lookup"><span data-stu-id="acf0d-121">When this element is specified, you cannot specify the `SelectionSetName` element.</span></span> <span data-ttu-id="acf0d-122">Zie voor [waarden definiëren voor het weer geven van gegevens](./defining-conditions-for-displaying-data.md)voor meer informatie over het definiëren van selectie voorwaarden.</span><span class="sxs-lookup"><span data-stu-id="acf0d-122">For more information about defining selection conditions, see [Defining Conditions for Displaying Data](./defining-conditions-for-displaying-data.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="acf0d-123">Zie ook</span><span class="sxs-lookup"><span data-stu-id="acf0d-123">See Also</span></span>

[<span data-ttu-id="acf0d-124">SelectionCondition-element voor EntrySelectedBy voor GroupBy (indeling)</span><span class="sxs-lookup"><span data-stu-id="acf0d-124">SelectionCondition Element for EntrySelectedBy for GroupBy (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-groupby-format.md)

[<span data-ttu-id="acf0d-125">Een Power shell-indelings bestand schrijven</span><span class="sxs-lookup"><span data-stu-id="acf0d-125">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
