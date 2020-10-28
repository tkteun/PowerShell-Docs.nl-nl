---
ms.date: 09/13/2016
ms.topic: reference
title: Het element EntrySelectedBy voor CustomEntry voor Besturingselementen voor Configuratie (opmaak)
description: Het element EntrySelectedBy voor CustomEntry voor Besturingselementen voor Configuratie (opmaak)
ms.openlocfilehash: fadcdb69ac71269ba2f2f80baf139bb363d4acba
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/27/2020
ms.locfileid: "92666668"
---
# <a name="entryselectedby-element-for-customentry-for-controls-for-configuration-format"></a><span data-ttu-id="7cf6a-103">Het element EntrySelectedBy voor CustomEntry voor Besturingselementen voor Configuratie (opmaak)</span><span class="sxs-lookup"><span data-stu-id="7cf6a-103">EntrySelectedBy Element for CustomEntry for Controls for Configuration (Format)</span></span>

<span data-ttu-id="7cf6a-104">Definieert de .NET-typen die gebruikmaken van de definitie van het algemene besturings element of de voor waarde die moet bestaan voor het gebruik van dit besturings element.</span><span class="sxs-lookup"><span data-stu-id="7cf6a-104">Defines the .NET types that use the definition of the common control or the condition that must exist for this control to be used.</span></span> <span data-ttu-id="7cf6a-105">Dit element wordt gebruikt bij het definiëren van een algemeen besturings element dat kan worden gebruikt door alle weer gaven in het opmaak bestand.</span><span class="sxs-lookup"><span data-stu-id="7cf6a-105">This element is used when defining a common control that can be used by all the views in the formatting file.</span></span>

<span data-ttu-id="7cf6a-106">Configuratie-element (Format) Controls element van configuratie (indeling) Control element voor besturings elementen voor configuratie (Format) CustomControl-element voor besturings element voor configuratie (indeling) CustomEntries element voor CustomControl voor configuratie (indeling) CustomEntry element voor CustomControl voor besturings elementen voor configuratie (indeling) EntrySelectedBy</span><span class="sxs-lookup"><span data-stu-id="7cf6a-106">Configuration Element (Format) Controls Element of Configuration (Format) Control Element for Controls for Configuration (Format) CustomControl Element for Control for Configuration (Format) CustomEntries Element for CustomControl for Configuration (Format) CustomEntry Element for CustomControl for Controls for Configuration (Format) EntrySelectedBy Element for CustomEntry for Controls for Configuration (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="7cf6a-107">Syntax</span><span class="sxs-lookup"><span data-stu-id="7cf6a-107">Syntax</span></span>

```xml
<EntrySelectedBy>
  <TypeName>Nameof.NetType</TypeName>
  <SelectionSetName>SelectionSet</SelectionSetName>
  <SelectionCondition>...</SelectionCondition>
</EntrySelectedBy>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="7cf6a-108">Kenmerken en elementen</span><span class="sxs-lookup"><span data-stu-id="7cf6a-108">Attributes and Elements</span></span>

<span data-ttu-id="7cf6a-109">In de volgende secties worden kenmerken, onderliggende elementen en het bovenliggende element van het `EntrySelectedBy` element beschreven.</span><span class="sxs-lookup"><span data-stu-id="7cf6a-109">The following sections describe attributes, child elements, and the parent element of the `EntrySelectedBy` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="7cf6a-110">Kenmerken</span><span class="sxs-lookup"><span data-stu-id="7cf6a-110">Attributes</span></span>

<span data-ttu-id="7cf6a-111">Geen.</span><span class="sxs-lookup"><span data-stu-id="7cf6a-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="7cf6a-112">Onderliggende elementen</span><span class="sxs-lookup"><span data-stu-id="7cf6a-112">Child Elements</span></span>

|<span data-ttu-id="7cf6a-113">Element</span><span class="sxs-lookup"><span data-stu-id="7cf6a-113">Element</span></span>|<span data-ttu-id="7cf6a-114">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="7cf6a-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="7cf6a-115">Het element SelectionCondition voor EntrySelectedBy voor Besturingselementen voor Configuratie (opmaak)</span><span class="sxs-lookup"><span data-stu-id="7cf6a-115">SelectionCondition Element for EntrySelectedBy for Controls for Configuration (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-controls-for-configuration-format.md)|<span data-ttu-id="7cf6a-116">Optioneel element.</span><span class="sxs-lookup"><span data-stu-id="7cf6a-116">Optional element.</span></span><br /><br /> <span data-ttu-id="7cf6a-117">Hiermee definieert u de voor waarde die moet bestaan voor het gebruik van de algemene controle definitie.</span><span class="sxs-lookup"><span data-stu-id="7cf6a-117">Defines the condition that must exist for the common control definition to be used.</span></span>|
|[<span data-ttu-id="7cf6a-118">Het element SelectionSetName voor EntrySelectedBy voor Besturingselementen voor Configuratie (opmaak)</span><span class="sxs-lookup"><span data-stu-id="7cf6a-118">SelectionSetName Element for EntrySelectedBy for Controls for Configuration (Format)</span></span>](./selectionsetname-element-for-selectioncondition-for-controls-for-configuration-format.md)|<span data-ttu-id="7cf6a-119">Optioneel element.</span><span class="sxs-lookup"><span data-stu-id="7cf6a-119">Optional element.</span></span><br /><br /> <span data-ttu-id="7cf6a-120">Hiermee geeft u een set .NET-typen op die gebruikmaken van deze definitie van het gemeen schappelijke besturings element.</span><span class="sxs-lookup"><span data-stu-id="7cf6a-120">Specifies a set of .NET types that use this definition of the common control.</span></span>|
|[<span data-ttu-id="7cf6a-121">Het element TypeName voor EntrySelectedBy voor Besturingselementen voor Configuratie (opmaak)</span><span class="sxs-lookup"><span data-stu-id="7cf6a-121">TypeName Element for EntrySelectedBy for Controls for Configuration (Format)</span></span>](./typename-element-for-entryselectedby-for-controls-for-configuration-format.md)|<span data-ttu-id="7cf6a-122">Optioneel element.</span><span class="sxs-lookup"><span data-stu-id="7cf6a-122">Optional element.</span></span><br /><br /> <span data-ttu-id="7cf6a-123">Hiermee geeft u een .NET-type op dat gebruikmaakt van deze definitie van het algemene besturings element.</span><span class="sxs-lookup"><span data-stu-id="7cf6a-123">Specifies a .NET type that uses this definition of the common control.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="7cf6a-124">Bovenliggende elementen</span><span class="sxs-lookup"><span data-stu-id="7cf6a-124">Parent Elements</span></span>

|<span data-ttu-id="7cf6a-125">Element</span><span class="sxs-lookup"><span data-stu-id="7cf6a-125">Element</span></span>|<span data-ttu-id="7cf6a-126">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="7cf6a-126">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="7cf6a-127">Het element CustomEntry voor CustomControl voor Besturingselementen voor Configuratie (opmaak)</span><span class="sxs-lookup"><span data-stu-id="7cf6a-127">CustomEntry Element for CustomControl for Controls for Configuration (Format)</span></span>](./customentry-element-for-customcontrol-for-controls-for-configuration-format.md)|<span data-ttu-id="7cf6a-128">Biedt een definitie van het algemene besturings element.</span><span class="sxs-lookup"><span data-stu-id="7cf6a-128">Provides a definition of the common control.</span></span>|

## <a name="remarks"></a><span data-ttu-id="7cf6a-129">Opmerkingen</span><span class="sxs-lookup"><span data-stu-id="7cf6a-129">Remarks</span></span>

<span data-ttu-id="7cf6a-130">Elke definitie moet mini maal één .NET-type,-selectieset of-selectie voorwaarde hebben opgegeven.</span><span class="sxs-lookup"><span data-stu-id="7cf6a-130">At a minimum, each definition must have at least one .NET type, selection set, or selection condition specified.</span></span> <span data-ttu-id="7cf6a-131">Er is geen maximum limiet voor het aantal typen, de selectie sets of de selectie voorwaarden die u kunt opgeven.</span><span class="sxs-lookup"><span data-stu-id="7cf6a-131">There is no maximum limit to the number of types, selection sets, or selection conditions that you can specify.</span></span>

## <a name="see-also"></a><span data-ttu-id="7cf6a-132">Zie ook</span><span class="sxs-lookup"><span data-stu-id="7cf6a-132">See Also</span></span>

[<span data-ttu-id="7cf6a-133">Het element SelectionCondition voor EntrySelectedBy voor Besturingselementen voor Configuratie (opmaak)</span><span class="sxs-lookup"><span data-stu-id="7cf6a-133">SelectionCondition Element for EntrySelectedBy for Controls for Configuration (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-controls-for-configuration-format.md)

[<span data-ttu-id="7cf6a-134">Het element SelectionSetName voor EntrySelectedBy voor Besturingselementen voor Configuratie (opmaak)</span><span class="sxs-lookup"><span data-stu-id="7cf6a-134">SelectionSetName Element for EntrySelectedBy for Controls for Configuration (Format)</span></span>](./selectionsetname-element-for-selectioncondition-for-controls-for-configuration-format.md)

[<span data-ttu-id="7cf6a-135">Het element CustomEntry voor CustomControl voor Besturingselementen voor Configuratie (opmaak)</span><span class="sxs-lookup"><span data-stu-id="7cf6a-135">CustomEntry Element for CustomControl for Controls for Configuration (Format)</span></span>](./customentry-element-for-customcontrol-for-controls-for-configuration-format.md)

[<span data-ttu-id="7cf6a-136">Het element TypeName voor EntrySelectedBy voor Besturingselementen voor Configuratie (opmaak)</span><span class="sxs-lookup"><span data-stu-id="7cf6a-136">TypeName Element for EntrySelectedBy for Controls for Configuration (Format)</span></span>](./typename-element-for-selectioncondition-for-controls-for-configuration-format.md)

[<span data-ttu-id="7cf6a-137">Een PowerShell-opmaakbestand schrijven</span><span class="sxs-lookup"><span data-stu-id="7cf6a-137">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
