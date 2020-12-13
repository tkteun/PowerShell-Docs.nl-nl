---
ms.date: 09/13/2016
ms.topic: reference
title: Het element TypeName voor SelectionCondition voor Besturingselementen voor Configuratie (opmaak)
description: Het element TypeName voor SelectionCondition voor Besturingselementen voor Configuratie (opmaak)
ms.openlocfilehash: fddb8ddbac7c9292a05cadfa31f98db6439a557d
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 12/10/2020
ms.locfileid: "92659664"
---
# <a name="typename-element-for-selectioncondition-for-controls-for-configuration-format"></a><span data-ttu-id="fd165-103">Het element TypeName voor SelectionCondition voor Besturingselementen voor Configuratie (opmaak)</span><span class="sxs-lookup"><span data-stu-id="fd165-103">TypeName Element for SelectionCondition for Controls for Configuration (Format)</span></span>

<span data-ttu-id="fd165-104">Hiermee geeft u een .NET-type op waarmee de voor waarde wordt geactiveerd.</span><span class="sxs-lookup"><span data-stu-id="fd165-104">Specifies a .NET type that triggers the condition.</span></span> <span data-ttu-id="fd165-105">Dit element wordt gebruikt bij het definiëren van een algemeen besturings element dat kan worden gebruikt door alle weer gaven in het opmaak bestand.</span><span class="sxs-lookup"><span data-stu-id="fd165-105">This element is used when defining a common control that can be used by all the views in the formatting file.</span></span>

<span data-ttu-id="fd165-106">Configuratie-element (Format) Controls element van configuratie (Format) Control-element voor besturings elementen voor configuratie (Format) CustomControl-element voor Control for Configuration (Format) CustomEntries element voor het beheer van de configuratie (Format) CustomEntry-element voor het EntrySelectedBy-element voor het configureren van de configuratie (indeling) voor CustomEntry voor besturings elementen voor de configuratie (Format) SelectionCondition-element voor EntrySelectedBy voor CustomEntry voor de configuratie (indeling) TypeName-element voor SelectionCondition voor besturings elementen voor configuratie (indeling)</span><span class="sxs-lookup"><span data-stu-id="fd165-106">Configuration Element (Format) Controls Element of Configuration (Format) Control Element for Controls for Configuration (Format) CustomControl Element for Control for Configuration (Format) CustomEntries Element for CustomControl for Controls for Configuration (Format) CustomEntry Element for CustomControl for Controls for Configuration (Format) EntrySelectedBy Element for CustomEntry for Controls for Configuration (Format) SelectionCondition Element for EntrySelectedBy for CustomEntry for Configuration (Format) TypeName Element for SelectionCondition for Controls for Configuration (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="fd165-107">Syntax</span><span class="sxs-lookup"><span data-stu-id="fd165-107">Syntax</span></span>

```xml
<TypeName>Nameof.NetType</TypeName>

```

## <a name="attributes-and-elements"></a><span data-ttu-id="fd165-108">Kenmerken en elementen</span><span class="sxs-lookup"><span data-stu-id="fd165-108">Attributes and Elements</span></span>

<span data-ttu-id="fd165-109">In de volgende secties worden kenmerken, onderliggende elementen en het bovenliggende element van het `TypeName` element beschreven.</span><span class="sxs-lookup"><span data-stu-id="fd165-109">The following sections describe attributes, child elements, and the parent element of the `TypeName` Element.</span></span>

### <a name="attributes"></a><span data-ttu-id="fd165-110">Kenmerken</span><span class="sxs-lookup"><span data-stu-id="fd165-110">Attributes</span></span>

<span data-ttu-id="fd165-111">Geen.</span><span class="sxs-lookup"><span data-stu-id="fd165-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="fd165-112">Onderliggende elementen</span><span class="sxs-lookup"><span data-stu-id="fd165-112">Child Elements</span></span>

<span data-ttu-id="fd165-113">Geen.</span><span class="sxs-lookup"><span data-stu-id="fd165-113">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="fd165-114">Bovenliggende elementen</span><span class="sxs-lookup"><span data-stu-id="fd165-114">Parent Elements</span></span>

|<span data-ttu-id="fd165-115">Element</span><span class="sxs-lookup"><span data-stu-id="fd165-115">Element</span></span>|<span data-ttu-id="fd165-116">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="fd165-116">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="fd165-117">SelectionCondition-element voor EntrySelectedBy voor CustomEntry voor configuratie (indeling)</span><span class="sxs-lookup"><span data-stu-id="fd165-117">SelectionCondition Element for EntrySelectedBy for CustomEntry for Configuration (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-controls-for-configuration-format.md)|<span data-ttu-id="fd165-118">Hiermee definieert u een voor waarde die moet bestaan voor het gebruik van de controle definitie.</span><span class="sxs-lookup"><span data-stu-id="fd165-118">Defines a condition that must exist for the control definition to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="fd165-119">Tekstwaarde</span><span class="sxs-lookup"><span data-stu-id="fd165-119">Text Value</span></span>

<span data-ttu-id="fd165-120">Geef de volledig gekwalificeerde naam van het .NET-type op, zoals `System.IO.DirectoryInfo` .</span><span class="sxs-lookup"><span data-stu-id="fd165-120">Specify the fully qualified name of the .NET type, such as `System.IO.DirectoryInfo`.</span></span>

## <a name="remarks"></a><span data-ttu-id="fd165-121">Opmerkingen</span><span class="sxs-lookup"><span data-stu-id="fd165-121">Remarks</span></span>

## <a name="see-also"></a><span data-ttu-id="fd165-122">Zie ook</span><span class="sxs-lookup"><span data-stu-id="fd165-122">See Also</span></span>

[<span data-ttu-id="fd165-123">SelectionCondition-element voor EntrySelectedBy voor CustomEntry voor configuratie (indeling)</span><span class="sxs-lookup"><span data-stu-id="fd165-123">SelectionCondition Element for EntrySelectedBy for CustomEntry for Configuration (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-controls-for-configuration-format.md)

[<span data-ttu-id="fd165-124">Een PowerShell-opmaakbestand schrijven</span><span class="sxs-lookup"><span data-stu-id="fd165-124">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
