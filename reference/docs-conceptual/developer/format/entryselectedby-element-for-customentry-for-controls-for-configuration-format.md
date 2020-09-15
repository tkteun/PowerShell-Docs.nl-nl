---
title: EntrySelectedBy-element voor CustomEntry voor besturings elementen voor configuratie (indeling) | Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: e9467c8c2d80e46c0a47c31569efbddbabe25bb1
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 08/05/2020
ms.locfileid: "87774266"
---
# <a name="entryselectedby-element-for-customentry-for-controls-for-configuration-format"></a><span data-ttu-id="535dc-102">Het element EntrySelectedBy voor CustomEntry voor Besturingselementen voor Configuratie (opmaak)</span><span class="sxs-lookup"><span data-stu-id="535dc-102">EntrySelectedBy Element for CustomEntry for Controls for Configuration (Format)</span></span>

<span data-ttu-id="535dc-103">Definieert de .NET-typen die gebruikmaken van de definitie van het algemene besturings element of de voor waarde die moet bestaan voor het gebruik van dit besturings element.</span><span class="sxs-lookup"><span data-stu-id="535dc-103">Defines the .NET types that use the definition of the common control or the condition that must exist for this control to be used.</span></span> <span data-ttu-id="535dc-104">Dit element wordt gebruikt bij het definiëren van een algemeen besturings element dat kan worden gebruikt door alle weer gaven in het opmaak bestand.</span><span class="sxs-lookup"><span data-stu-id="535dc-104">This element is used when defining a common control that can be used by all the views in the formatting file.</span></span>

<span data-ttu-id="535dc-105">Configuratie-element (Format) Controls element van configuratie (indeling) Control element voor besturings elementen voor configuratie (Format) CustomControl-element voor besturings element voor configuratie (indeling) CustomEntries element voor CustomControl voor configuratie (indeling) CustomEntry element voor CustomControl voor besturings elementen voor configuratie (indeling) EntrySelectedBy</span><span class="sxs-lookup"><span data-stu-id="535dc-105">Configuration Element (Format) Controls Element of Configuration (Format) Control Element for Controls for Configuration (Format) CustomControl Element for Control for Configuration (Format) CustomEntries Element for CustomControl for Configuration (Format) CustomEntry Element for CustomControl for Controls for Configuration (Format) EntrySelectedBy Element for CustomEntry for Controls for Configuration (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="535dc-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="535dc-106">Syntax</span></span>

```xml
<EntrySelectedBy>
  <TypeName>Nameof.NetType</TypeName>
  <SelectionSetName>SelectionSet</SelectionSetName>
  <SelectionCondition>...</SelectionCondition>
</EntrySelectedBy>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="535dc-107">Kenmerken en elementen</span><span class="sxs-lookup"><span data-stu-id="535dc-107">Attributes and Elements</span></span>

<span data-ttu-id="535dc-108">In de volgende secties worden kenmerken, onderliggende elementen en het bovenliggende element van het `EntrySelectedBy` element beschreven.</span><span class="sxs-lookup"><span data-stu-id="535dc-108">The following sections describe attributes, child elements, and the parent element of the `EntrySelectedBy` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="535dc-109">Kenmerken</span><span class="sxs-lookup"><span data-stu-id="535dc-109">Attributes</span></span>

<span data-ttu-id="535dc-110">Geen.</span><span class="sxs-lookup"><span data-stu-id="535dc-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="535dc-111">Onderliggende elementen</span><span class="sxs-lookup"><span data-stu-id="535dc-111">Child Elements</span></span>

|<span data-ttu-id="535dc-112">Element</span><span class="sxs-lookup"><span data-stu-id="535dc-112">Element</span></span>|<span data-ttu-id="535dc-113">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="535dc-113">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="535dc-114">Het element SelectionCondition voor EntrySelectedBy voor Besturingselementen voor Configuratie (opmaak)</span><span class="sxs-lookup"><span data-stu-id="535dc-114">SelectionCondition Element for EntrySelectedBy for Controls for Configuration (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-controls-for-configuration-format.md)|<span data-ttu-id="535dc-115">Optioneel element.</span><span class="sxs-lookup"><span data-stu-id="535dc-115">Optional element.</span></span><br /><br /> <span data-ttu-id="535dc-116">Hiermee definieert u de voor waarde die moet bestaan voor het gebruik van de algemene controle definitie.</span><span class="sxs-lookup"><span data-stu-id="535dc-116">Defines the condition that must exist for the common control definition to be used.</span></span>|
|[<span data-ttu-id="535dc-117">Het element SelectionSetName voor EntrySelectedBy voor Besturingselementen voor Configuratie (opmaak)</span><span class="sxs-lookup"><span data-stu-id="535dc-117">SelectionSetName Element for EntrySelectedBy for Controls for Configuration (Format)</span></span>](./selectionsetname-element-for-selectioncondition-for-controls-for-configuration-format.md)|<span data-ttu-id="535dc-118">Optioneel element.</span><span class="sxs-lookup"><span data-stu-id="535dc-118">Optional element.</span></span><br /><br /> <span data-ttu-id="535dc-119">Hiermee geeft u een set .NET-typen op die gebruikmaken van deze definitie van het gemeen schappelijke besturings element.</span><span class="sxs-lookup"><span data-stu-id="535dc-119">Specifies a set of .NET types that use this definition of the common control.</span></span>|
|[<span data-ttu-id="535dc-120">Het element TypeName voor EntrySelectedBy voor Besturingselementen voor Configuratie (opmaak)</span><span class="sxs-lookup"><span data-stu-id="535dc-120">TypeName Element for EntrySelectedBy for Controls for Configuration (Format)</span></span>](./typename-element-for-entryselectedby-for-controls-for-configuration-format.md)|<span data-ttu-id="535dc-121">Optioneel element.</span><span class="sxs-lookup"><span data-stu-id="535dc-121">Optional element.</span></span><br /><br /> <span data-ttu-id="535dc-122">Hiermee geeft u een .NET-type op dat gebruikmaakt van deze definitie van het algemene besturings element.</span><span class="sxs-lookup"><span data-stu-id="535dc-122">Specifies a .NET type that uses this definition of the common control.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="535dc-123">Bovenliggende elementen</span><span class="sxs-lookup"><span data-stu-id="535dc-123">Parent Elements</span></span>

|<span data-ttu-id="535dc-124">Element</span><span class="sxs-lookup"><span data-stu-id="535dc-124">Element</span></span>|<span data-ttu-id="535dc-125">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="535dc-125">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="535dc-126">Het element CustomEntry voor CustomControl voor Besturingselementen voor Configuratie (opmaak)</span><span class="sxs-lookup"><span data-stu-id="535dc-126">CustomEntry Element for CustomControl for Controls for Configuration (Format)</span></span>](./customentry-element-for-customcontrol-for-controls-for-configuration-format.md)|<span data-ttu-id="535dc-127">Biedt een definitie van het algemene besturings element.</span><span class="sxs-lookup"><span data-stu-id="535dc-127">Provides a definition of the common control.</span></span>|

## <a name="remarks"></a><span data-ttu-id="535dc-128">Opmerkingen</span><span class="sxs-lookup"><span data-stu-id="535dc-128">Remarks</span></span>

<span data-ttu-id="535dc-129">Elke definitie moet mini maal één .NET-type,-selectieset of-selectie voorwaarde hebben opgegeven.</span><span class="sxs-lookup"><span data-stu-id="535dc-129">At a minimum, each definition must have at least one .NET type, selection set, or selection condition specified.</span></span> <span data-ttu-id="535dc-130">Er is geen maximum limiet voor het aantal typen, de selectie sets of de selectie voorwaarden die u kunt opgeven.</span><span class="sxs-lookup"><span data-stu-id="535dc-130">There is no maximum limit to the number of types, selection sets, or selection conditions that you can specify.</span></span>

## <a name="see-also"></a><span data-ttu-id="535dc-131">Zie ook</span><span class="sxs-lookup"><span data-stu-id="535dc-131">See Also</span></span>

[<span data-ttu-id="535dc-132">Het element SelectionCondition voor EntrySelectedBy voor Besturingselementen voor Configuratie (opmaak)</span><span class="sxs-lookup"><span data-stu-id="535dc-132">SelectionCondition Element for EntrySelectedBy for Controls for Configuration (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-controls-for-configuration-format.md)

[<span data-ttu-id="535dc-133">Het element SelectionSetName voor EntrySelectedBy voor Besturingselementen voor Configuratie (opmaak)</span><span class="sxs-lookup"><span data-stu-id="535dc-133">SelectionSetName Element for EntrySelectedBy for Controls for Configuration (Format)</span></span>](./selectionsetname-element-for-selectioncondition-for-controls-for-configuration-format.md)

[<span data-ttu-id="535dc-134">Het element CustomEntry voor CustomControl voor Besturingselementen voor Configuratie (opmaak)</span><span class="sxs-lookup"><span data-stu-id="535dc-134">CustomEntry Element for CustomControl for Controls for Configuration (Format)</span></span>](./customentry-element-for-customcontrol-for-controls-for-configuration-format.md)

[<span data-ttu-id="535dc-135">Het element TypeName voor EntrySelectedBy voor Besturingselementen voor Configuratie (opmaak)</span><span class="sxs-lookup"><span data-stu-id="535dc-135">TypeName Element for EntrySelectedBy for Controls for Configuration (Format)</span></span>](./typename-element-for-selectioncondition-for-controls-for-configuration-format.md)

[<span data-ttu-id="535dc-136">Een PowerShell-opmaakbestand schrijven</span><span class="sxs-lookup"><span data-stu-id="535dc-136">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
