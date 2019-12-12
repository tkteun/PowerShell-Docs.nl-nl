---
title: TypeName-element voor EntrySelectedBy voor GroupBy (indeling) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: b8b6739b-770c-432a-95ab-551c7507c51f
caps.latest.revision: 6
ms.openlocfilehash: 3b5ce60d3a0d76988af48f49445a5478a415d498
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 12/05/2019
ms.locfileid: "72353590"
---
# <a name="typename-element-for-entryselectedby-for-groupby-format"></a><span data-ttu-id="8cd80-102">Het element TypeName voor EntrySelectedBy voor GroupBy (opmaak)</span><span class="sxs-lookup"><span data-stu-id="8cd80-102">TypeName Element for EntrySelectedBy for GroupBy (Format)</span></span>

<span data-ttu-id="8cd80-103">Hiermee geeft u een .NET-type op dat gebruikmaakt van deze definitie van het aangepaste besturings element.</span><span class="sxs-lookup"><span data-stu-id="8cd80-103">Specifies a .NET type that uses this definition of the custom control.</span></span> <span data-ttu-id="8cd80-104">Dit element wordt gebruikt bij het definiëren van de manier waarop een nieuwe groep objecten wordt weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="8cd80-104">This element is used when defining how a new group of objects is displayed.</span></span>

<span data-ttu-id="8cd80-105">Configuratie-element (indeling) ViewDefinitions element (indeling) element voor weer gave (indeling) GroupBy-element (Format) voor weer gave (indeling) CustomControl-element voor het element GroupBy (indeling) CustomEntries voor CustomControl voor het element GroupBy (Format) CustomEntry voor CustomControl voor het element GroupBy (indeling) EntrySelectedBy voor CustomEntry voor het element GroupBy (Format) voor EntrySelectedBy voor GroupBy (indeling)</span><span class="sxs-lookup"><span data-stu-id="8cd80-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) GroupBy Element for View (Format) CustomControl Element for GroupBy (Format) CustomEntries Element for CustomControl for GroupBy (Format) CustomEntry Element for CustomControl for GroupBy (Format) EntrySelectedBy Element for CustomEntry for GroupBy (Format) TypeName Element for EntrySelectedBy for GroupBy (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="8cd80-106">Syntaxis</span><span class="sxs-lookup"><span data-stu-id="8cd80-106">Syntax</span></span>

```xml
<TypeName>Nameof.NetType</TypeName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="8cd80-107">Kenmerken en elementen</span><span class="sxs-lookup"><span data-stu-id="8cd80-107">Attributes and Elements</span></span>

<span data-ttu-id="8cd80-108">In de volgende secties worden kenmerken, onderliggende elementen en het bovenliggende element van het element `TypeName` beschreven.</span><span class="sxs-lookup"><span data-stu-id="8cd80-108">The following sections describe attributes, child elements, and the parent element of the `TypeName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="8cd80-109">Kenmerken</span><span class="sxs-lookup"><span data-stu-id="8cd80-109">Attributes</span></span>

<span data-ttu-id="8cd80-110">Geen.</span><span class="sxs-lookup"><span data-stu-id="8cd80-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="8cd80-111">Onderliggende elementen</span><span class="sxs-lookup"><span data-stu-id="8cd80-111">Child Elements</span></span>

<span data-ttu-id="8cd80-112">Geen.</span><span class="sxs-lookup"><span data-stu-id="8cd80-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="8cd80-113">Bovenliggende elementen</span><span class="sxs-lookup"><span data-stu-id="8cd80-113">Parent Elements</span></span>

|<span data-ttu-id="8cd80-114">Element</span><span class="sxs-lookup"><span data-stu-id="8cd80-114">Element</span></span>|<span data-ttu-id="8cd80-115">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="8cd80-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="8cd80-116">EntrySelectedBy-element voor CustomEntry voor GroupBy (indeling)</span><span class="sxs-lookup"><span data-stu-id="8cd80-116">EntrySelectedBy Element for CustomEntry for GroupBy (Format)</span></span>](./entryselectedby-element-for-customentry-for-groupby-format.md)|<span data-ttu-id="8cd80-117">Hiermee definieert u de .NET-typen die gebruikmaken van deze controle definitie of de voor waarde die voor deze definitie moet worden gebruikt.</span><span class="sxs-lookup"><span data-stu-id="8cd80-117">Defines the .NET types that use this control definition or the condition that must exist for this definition to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="8cd80-118">Tekstwaarde</span><span class="sxs-lookup"><span data-stu-id="8cd80-118">Text Value</span></span>

<span data-ttu-id="8cd80-119">Geef de volledig gekwalificeerde naam van het .NET-type op, zoals `System.IO.DirectoryInfo`.</span><span class="sxs-lookup"><span data-stu-id="8cd80-119">Specify the fully qualified name of the .NET type, such as `System.IO.DirectoryInfo`.</span></span>

## <a name="remarks"></a><span data-ttu-id="8cd80-120">Opmerkingen</span><span class="sxs-lookup"><span data-stu-id="8cd80-120">Remarks</span></span>

<span data-ttu-id="8cd80-121">Voor elke controle definitie moet ten minste één type naam, selectieset of selectie voorwaarde zijn gedefinieerd.</span><span class="sxs-lookup"><span data-stu-id="8cd80-121">Each control definition must have at least one type name, selection set, or selection condition defined.</span></span>

<span data-ttu-id="8cd80-122">Zie [aangepaste besturings elementen maken](./creating-custom-controls.md)voor meer informatie over de onderdelen van een aangepaste beheer weergave.</span><span class="sxs-lookup"><span data-stu-id="8cd80-122">For more information about the components of a custom control view, see [Creating Custom Controls](./creating-custom-controls.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="8cd80-123">Zie ook</span><span class="sxs-lookup"><span data-stu-id="8cd80-123">See Also</span></span>

[<span data-ttu-id="8cd80-124">Aangepaste besturings elementen maken</span><span class="sxs-lookup"><span data-stu-id="8cd80-124">Creating Custom Controls</span></span>](./creating-custom-controls.md)

[<span data-ttu-id="8cd80-125">EntrySelectedBy-element voor CustomEntry voor GroupBy (indeling)</span><span class="sxs-lookup"><span data-stu-id="8cd80-125">EntrySelectedBy Element for CustomEntry for GroupBy (Format)</span></span>](./entryselectedby-element-for-customentry-for-groupby-format.md)

[<span data-ttu-id="8cd80-126">Een Power shell-indelings bestand schrijven</span><span class="sxs-lookup"><span data-stu-id="8cd80-126">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
