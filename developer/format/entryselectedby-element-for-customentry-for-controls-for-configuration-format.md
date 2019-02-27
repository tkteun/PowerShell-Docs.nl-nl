---
title: EntrySelectedBy-Element voor CustomEntry voor besturingselementen voor de configuratie (-indeling) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 30abae8f-c7f7-479d-ad85-19e07ddef204
caps.latest.revision: 10
ms.openlocfilehash: e930e4422afd203feda6a389655ff8a355e3bec0
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 02/03/2019
ms.locfileid: "56848676"
---
# <a name="entryselectedby-element-for-customentry-for-controls-for-configuration-format"></a><span data-ttu-id="0edef-102">Het element EntrySelectedBy voor CustomEntry voor Besturingselementen voor Configuratie (opmaak)</span><span class="sxs-lookup"><span data-stu-id="0edef-102">EntrySelectedBy Element for CustomEntry for Controls for Configuration (Format)</span></span>

<span data-ttu-id="0edef-103">Hiermee definieert u de .NET-typen die gebruikmaken van de definitie van de algemene controle of de voorwaarde die moet bestaan voor dit besturingselement moet worden gebruikt.</span><span class="sxs-lookup"><span data-stu-id="0edef-103">Defines the .NET types that use the definition of the common control or the condition that must exist for this control to be used.</span></span> <span data-ttu-id="0edef-104">Dit element wordt gebruikt bij het definiëren van een algemene besturingselement dat kan worden gebruikt door alle weergaven in de opmaak-bestand.</span><span class="sxs-lookup"><span data-stu-id="0edef-104">This element is used when defining a common control that can be used by all the views in the formatting file.</span></span>

<span data-ttu-id="0edef-105">Configuratie-Element (indeling) besturingselementen Element van configuratie (-indeling) besturingselement Element controles voor configuratie (-indeling) CustomControl-Element voor het besturingselement voor configuratie (-indeling) CustomEntries-Element voor CustomControl voor configuratie ( -Indeling) CustomEntry Element voor CustomControl controles voor configuratie (-indeling) EntrySelectedBy-Element voor CustomEntry voor besturingselementen voor de configuratie (-indeling)</span><span class="sxs-lookup"><span data-stu-id="0edef-105">Configuration Element (Format) Controls Element of Configuration (Format) Control Element for Controls for Configuration (Format) CustomControl Element for Control for Configuration (Format) CustomEntries Element for CustomControl for Configuration (Format) CustomEntry Element for CustomControl for Controls for Configuration (Format) EntrySelectedBy Element for CustomEntry for Controls for Configuration (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="0edef-106">Syntaxis</span><span class="sxs-lookup"><span data-stu-id="0edef-106">Syntax</span></span>

```xml
<EntrySelectedBy>
  <TypeName>Nameof.NetType</TypeName>
  <SelectionSetName>SelectionSet</SelectionSetName>
  <SelectionCondition>...</SelectionCondition>
</EntrySelectedBy>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="0edef-107">Kenmerken en elementen</span><span class="sxs-lookup"><span data-stu-id="0edef-107">Attributes and Elements</span></span>

<span data-ttu-id="0edef-108">De volgende secties beschrijven kenmerken, onderliggende elementen en het bovenliggende element van de `EntrySelectedBy` element.</span><span class="sxs-lookup"><span data-stu-id="0edef-108">The following sections describe attributes, child elements, and the parent element of the `EntrySelectedBy` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="0edef-109">Kenmerken</span><span class="sxs-lookup"><span data-stu-id="0edef-109">Attributes</span></span>

<span data-ttu-id="0edef-110">Geen.</span><span class="sxs-lookup"><span data-stu-id="0edef-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="0edef-111">Onderliggende elementen</span><span class="sxs-lookup"><span data-stu-id="0edef-111">Child Elements</span></span>

|<span data-ttu-id="0edef-112">Element</span><span class="sxs-lookup"><span data-stu-id="0edef-112">Element</span></span>|<span data-ttu-id="0edef-113">Description</span><span class="sxs-lookup"><span data-stu-id="0edef-113">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="0edef-114">SelectionCondition-Element voor EntrySelectedBy voor besturingselementen voor de configuratie (-indeling)</span><span class="sxs-lookup"><span data-stu-id="0edef-114">SelectionCondition Element for EntrySelectedBy for Controls for Configuration (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-controls-for-configuration-format.md)|<span data-ttu-id="0edef-115">Optioneel element.</span><span class="sxs-lookup"><span data-stu-id="0edef-115">Optional element.</span></span><br /><br /> <span data-ttu-id="0edef-116">Hiermee definieert u de voorwaarde die moet aanwezig zijn voor de definitie van de algemene controle moet worden gebruikt.</span><span class="sxs-lookup"><span data-stu-id="0edef-116">Defines the condition that must exist for the common control definition to be used.</span></span>|
|[<span data-ttu-id="0edef-117">SelectionSetName-Element voor EntrySelectedBy voor besturingselementen voor de configuratie (-indeling)</span><span class="sxs-lookup"><span data-stu-id="0edef-117">SelectionSetName Element for EntrySelectedBy for Controls for Configuration (Format)</span></span>](./selectionsetname-element-for-selectioncondition-for-controls-for-configuration-format.md)|<span data-ttu-id="0edef-118">Optioneel element.</span><span class="sxs-lookup"><span data-stu-id="0edef-118">Optional element.</span></span><br /><br /> <span data-ttu-id="0edef-119">Hiermee geeft u een set van .NET-typen die gebruikmaken van deze definitie van de algemene besturingselementen.</span><span class="sxs-lookup"><span data-stu-id="0edef-119">Specifies a set of .NET types that use this definition of the common control.</span></span>|
|[<span data-ttu-id="0edef-120">TypeName-Element voor EntrySelectedBy voor besturingselementen voor de configuratie (-indeling)</span><span class="sxs-lookup"><span data-stu-id="0edef-120">TypeName Element for EntrySelectedBy for Controls for Configuration (Format)</span></span>](./typename-element-for-entryselectedby-for-controls-for-configuration-format.md)|<span data-ttu-id="0edef-121">Optioneel element.</span><span class="sxs-lookup"><span data-stu-id="0edef-121">Optional element.</span></span><br /><br /> <span data-ttu-id="0edef-122">Hiermee geeft u een .NET-type dat gebruikmaakt van deze definitie van de algemene besturingselementen.</span><span class="sxs-lookup"><span data-stu-id="0edef-122">Specifies a .NET type that uses this definition of the common control.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="0edef-123">Bovenliggende elementen</span><span class="sxs-lookup"><span data-stu-id="0edef-123">Parent Elements</span></span>

|<span data-ttu-id="0edef-124">Element</span><span class="sxs-lookup"><span data-stu-id="0edef-124">Element</span></span>|<span data-ttu-id="0edef-125">Description</span><span class="sxs-lookup"><span data-stu-id="0edef-125">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="0edef-126">CustomEntry-Element voor CustomControl voor besturingselementen voor de configuratie (-indeling)</span><span class="sxs-lookup"><span data-stu-id="0edef-126">CustomEntry Element for CustomControl for Controls for Configuration (Format)</span></span>](./customentry-element-for-customcontrol-for-controls-for-configuration-format.md)|<span data-ttu-id="0edef-127">Bevat een definitie van de algemene besturingselementen.</span><span class="sxs-lookup"><span data-stu-id="0edef-127">Provides a definition of the common control.</span></span>|

## <a name="remarks"></a><span data-ttu-id="0edef-128">Opmerkingen</span><span class="sxs-lookup"><span data-stu-id="0edef-128">Remarks</span></span>

<span data-ttu-id="0edef-129">Ten minste hebt elke definitie ten minste één .NET-type, selectie instellen of selectievoorwaarde die is opgegeven.</span><span class="sxs-lookup"><span data-stu-id="0edef-129">At a minimum, each definition must have at least one .NET type, selection set, or selection condition specified.</span></span> <span data-ttu-id="0edef-130">Er is geen maximale limiet voor het aantal typen, sets selecteren of selectie voorwaarden die u kunt opgeven.</span><span class="sxs-lookup"><span data-stu-id="0edef-130">There is no maximum limit to the number of types, selection sets, or selection conditions that you can specify.</span></span>

## <a name="see-also"></a><span data-ttu-id="0edef-131">Zie ook</span><span class="sxs-lookup"><span data-stu-id="0edef-131">See Also</span></span>

[<span data-ttu-id="0edef-132">SelectionCondition-Element voor EntrySelectedBy voor besturingselementen voor de configuratie (-indeling)</span><span class="sxs-lookup"><span data-stu-id="0edef-132">SelectionCondition Element for EntrySelectedBy for Controls for Configuration (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-controls-for-configuration-format.md)

[<span data-ttu-id="0edef-133">SelectionSetName-Element voor EntrySelectedBy voor besturingselementen voor de configuratie (-indeling)</span><span class="sxs-lookup"><span data-stu-id="0edef-133">SelectionSetName Element for EntrySelectedBy for Controls for Configuration (Format)</span></span>](./selectionsetname-element-for-selectioncondition-for-controls-for-configuration-format.md)

[<span data-ttu-id="0edef-134">CustomEntry-Element voor CustomControl voor besturingselementen voor de configuratie (-indeling)</span><span class="sxs-lookup"><span data-stu-id="0edef-134">CustomEntry Element for CustomControl for Controls for Configuration (Format)</span></span>](./customentry-element-for-customcontrol-for-controls-for-configuration-format.md)

[<span data-ttu-id="0edef-135">TypeName-Element voor EntrySelectdBy voor besturingselementen voor de configuratie (-indeling)</span><span class="sxs-lookup"><span data-stu-id="0edef-135">TypeName Element for EntrySelectdBy for Controls for Configuration (Format)</span></span>](./typename-element-for-selectioncondition-for-controls-for-configuration-format.md)

[<span data-ttu-id="0edef-136">Schrijven van een bestand opmaak PowerShell</span><span class="sxs-lookup"><span data-stu-id="0edef-136">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
