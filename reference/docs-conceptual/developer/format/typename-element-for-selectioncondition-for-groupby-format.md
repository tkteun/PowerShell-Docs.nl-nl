---
title: TypeName-element voor SelectionCondition voor GroupBy (indeling) | Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: ea1e0cb50c3a749f6c26d13fff4b001240ce6b95
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 08/05/2020
ms.locfileid: "87772549"
---
# <a name="typename-element-for-selectioncondition-for-groupby-format"></a><span data-ttu-id="c7a87-102">Het element TypeName voor SelectionCondition voor GroupBy (opmaak)</span><span class="sxs-lookup"><span data-stu-id="c7a87-102">TypeName Element for SelectionCondition for GroupBy (Format)</span></span>

<span data-ttu-id="c7a87-103">Hiermee geeft u een .NET-type op waarmee de voor waarde wordt geactiveerd.</span><span class="sxs-lookup"><span data-stu-id="c7a87-103">Specifies a .NET type that triggers the condition.</span></span> <span data-ttu-id="c7a87-104">Dit element wordt gebruikt bij het definiëren van de manier waarop een nieuwe groep objecten wordt weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="c7a87-104">This element is used when defining how a new group of objects is displayed.</span></span>

<span data-ttu-id="c7a87-105">Configuratie-element (indeling) ViewDefinitions element (indeling) element van het type GroupBy-element (Format) voor weer gave (indeling) CustomControl-element voor het CustomEntries-element van GroupBy (Format) voor CustomControl voor het element GroupBy (Format) CustomEntry element voor CustomControl voor het object GroupBy (Format) voor CustomEntry voor het element GroupBy (Format) voor SelectionCondition voor GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="c7a87-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) GroupBy Element for View (Format) CustomControl Element for GroupBy (Format) CustomEntries Element for CustomControl for GroupBy (Format) CustomEntry Element for CustomControl for GroupBy (Format) EntrySelectedBy Element for CustomEntry for GroupBy (Format) SelectionCondition Element for EntrySelectedBy for GroupBy (Format) TypeName Element for SelectionCondition for GroupBy  (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="c7a87-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="c7a87-106">Syntax</span></span>

```xml
<TypeName>Nameof.NetType</TypeName>

```

## <a name="attributes-and-elements"></a><span data-ttu-id="c7a87-107">Kenmerken en elementen</span><span class="sxs-lookup"><span data-stu-id="c7a87-107">Attributes and Elements</span></span>

<span data-ttu-id="c7a87-108">In de volgende secties worden kenmerken, onderliggende elementen en het bovenliggende element van het `TypeName` element beschreven.</span><span class="sxs-lookup"><span data-stu-id="c7a87-108">The following sections describe attributes, child elements, and the parent element of the `TypeName` Element.</span></span>

### <a name="attributes"></a><span data-ttu-id="c7a87-109">Kenmerken</span><span class="sxs-lookup"><span data-stu-id="c7a87-109">Attributes</span></span>

<span data-ttu-id="c7a87-110">Geen.</span><span class="sxs-lookup"><span data-stu-id="c7a87-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="c7a87-111">Onderliggende elementen</span><span class="sxs-lookup"><span data-stu-id="c7a87-111">Child Elements</span></span>

<span data-ttu-id="c7a87-112">Geen.</span><span class="sxs-lookup"><span data-stu-id="c7a87-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="c7a87-113">Bovenliggende elementen</span><span class="sxs-lookup"><span data-stu-id="c7a87-113">Parent Elements</span></span>

|<span data-ttu-id="c7a87-114">Element</span><span class="sxs-lookup"><span data-stu-id="c7a87-114">Element</span></span>|<span data-ttu-id="c7a87-115">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="c7a87-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="c7a87-116">Het element SelectionCondition voor EntrySelectedBy voor GroupBy (opmaak)</span><span class="sxs-lookup"><span data-stu-id="c7a87-116">SelectionCondition Element for EntrySelectedBy for GroupBy (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-groupby-format.md)|<span data-ttu-id="c7a87-117">Hiermee definieert u een voor waarde die moet bestaan voor het gebruik van de controle definitie.</span><span class="sxs-lookup"><span data-stu-id="c7a87-117">Defines a condition that must exist for the control definition to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="c7a87-118">Tekstwaarde</span><span class="sxs-lookup"><span data-stu-id="c7a87-118">Text Value</span></span>

<span data-ttu-id="c7a87-119">Geef de volledig gekwalificeerde naam van het .NET-type op, zoals `System.IO.DirectoryInfo` .</span><span class="sxs-lookup"><span data-stu-id="c7a87-119">Specify the fully qualified name of the .NET type, such as `System.IO.DirectoryInfo`.</span></span>

## <a name="remarks"></a><span data-ttu-id="c7a87-120">Opmerkingen</span><span class="sxs-lookup"><span data-stu-id="c7a87-120">Remarks</span></span>

<span data-ttu-id="c7a87-121">Als dit element is opgegeven, kunt u het element niet opgeven `SelectionSetName` .</span><span class="sxs-lookup"><span data-stu-id="c7a87-121">When this element is specified, you cannot specify the `SelectionSetName` element.</span></span> <span data-ttu-id="c7a87-122">Zie voor [waarden definiëren voor het weer geven van gegevens](./defining-conditions-for-displaying-data.md)voor meer informatie over het definiëren van selectie voorwaarden.</span><span class="sxs-lookup"><span data-stu-id="c7a87-122">For more information about defining selection conditions, see [Defining Conditions for Displaying Data](./defining-conditions-for-displaying-data.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="c7a87-123">Zie ook</span><span class="sxs-lookup"><span data-stu-id="c7a87-123">See Also</span></span>

[<span data-ttu-id="c7a87-124">Het element SelectionCondition voor EntrySelectedBy voor GroupBy (opmaak)</span><span class="sxs-lookup"><span data-stu-id="c7a87-124">SelectionCondition Element for EntrySelectedBy for GroupBy (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-groupby-format.md)

[<span data-ttu-id="c7a87-125">Een PowerShell-opmaakbestand schrijven</span><span class="sxs-lookup"><span data-stu-id="c7a87-125">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
