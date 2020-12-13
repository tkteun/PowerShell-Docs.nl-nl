---
ms.date: 09/13/2016
ms.topic: reference
title: Het element ExpressionBinding voor CustomItem voor Besturingselementen voor Configuratie (opmaak)
description: Het element ExpressionBinding voor CustomItem voor Besturingselementen voor Configuratie (opmaak)
ms.openlocfilehash: 1abcf2173e18d45839161b4c7e59f1ad238f81a1
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 12/10/2020
ms.locfileid: "92655335"
---
# <a name="expressionbinding-element-for-customitem-for-controls-for-configuration-format"></a><span data-ttu-id="cd136-103">Het element ExpressionBinding voor CustomItem voor Besturingselementen voor Configuratie (opmaak)</span><span class="sxs-lookup"><span data-stu-id="cd136-103">ExpressionBinding Element for CustomItem for Controls for Configuration (Format)</span></span>

<span data-ttu-id="cd136-104">Hiermee worden de gegevens gedefinieerd die door het besturings element worden weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="cd136-104">Defines the data that is displayed by the control.</span></span> <span data-ttu-id="cd136-105">Dit element wordt gebruikt bij het definiëren van een algemeen besturings element dat kan worden gebruikt door alle weer gaven in het opmaak bestand.</span><span class="sxs-lookup"><span data-stu-id="cd136-105">This element is used when defining a common control that can be used by all the views in the formatting file.</span></span>

<span data-ttu-id="cd136-106">Configuratie-element (Format) Controls element van configuratie (indeling) Control element voor besturings elementen voor configuratie (Format) CustomControl-element voor besturings element voor configuratie (indeling) CustomEntries element voor CustomControl voor configuratie (indeling) CustomEntry element voor CustomControl voor besturings elementen voor configuratie-ExpressionBinding element voor CustomItem voor besturings elementen voor configuratie (indeling)</span><span class="sxs-lookup"><span data-stu-id="cd136-106">Configuration Element (Format) Controls Element of Configuration (Format) Control Element for Controls for Configuration (Format) CustomControl Element for Control for Configuration (Format) CustomEntries Element for CustomControl for Configuration (Format) CustomEntry Element for CustomControl for Controls for Configuration (Format) CustomItem Element for CustomEntry for Controls for Configuration ExpressionBinding Element for CustomItem for Controls for Configuration (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="cd136-107">Syntax</span><span class="sxs-lookup"><span data-stu-id="cd136-107">Syntax</span></span>

```xml
<ExpressionBinding>
  <CustomControl>...</CustomControl>
  <CustomControlName>NameofCommonCustomControl</CustomControlName>
  <EnumerateCollection/>
  <ItemSelectionCondition>...</ItemSelectionCondition>
  <PropertyName>Nameof.NetTypeProperty</PropertyName>
  <ScriptBlock>ScriptToEvaluate></ScriptBlock>
</ExpressionBinding>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="cd136-108">Kenmerken en elementen</span><span class="sxs-lookup"><span data-stu-id="cd136-108">Attributes and Elements</span></span>

<span data-ttu-id="cd136-109">In de volgende secties worden kenmerken, onderliggende elementen en het bovenliggende element van het `ExpressionBinding` element beschreven.</span><span class="sxs-lookup"><span data-stu-id="cd136-109">The following sections describe attributes, child elements, and the parent element of the `ExpressionBinding` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="cd136-110">Kenmerken</span><span class="sxs-lookup"><span data-stu-id="cd136-110">Attributes</span></span>

<span data-ttu-id="cd136-111">Geen.</span><span class="sxs-lookup"><span data-stu-id="cd136-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="cd136-112">Onderliggende elementen</span><span class="sxs-lookup"><span data-stu-id="cd136-112">Child Elements</span></span>

|<span data-ttu-id="cd136-113">Element</span><span class="sxs-lookup"><span data-stu-id="cd136-113">Element</span></span>|<span data-ttu-id="cd136-114">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="cd136-114">Description</span></span>|
|-------------|-----------------|
|`CustomControl Element`|<span data-ttu-id="cd136-115">Optioneel element.</span><span class="sxs-lookup"><span data-stu-id="cd136-115">Optional element.</span></span><br /><br /> <span data-ttu-id="cd136-116">Hiermee wordt een besturings element gedefinieerd dat door dit besturings element wordt gebruikt.</span><span class="sxs-lookup"><span data-stu-id="cd136-116">Defines a control that is used by this control.</span></span>|
|[<span data-ttu-id="cd136-117">Het element CustomControlName voor ExpressionBinding voor Besturingselementen voor Configuratie (opmaak)</span><span class="sxs-lookup"><span data-stu-id="cd136-117">CustomControlName Element for ExpressionBinding for Controls for Configuration (Format)</span></span>](./customcontrolname-element-for-expressionbinding-for-controls-for-configuration-format.md)|<span data-ttu-id="cd136-118">Optioneel element.</span><span class="sxs-lookup"><span data-stu-id="cd136-118">Optional element.</span></span><br /><br /> <span data-ttu-id="cd136-119">Hiermee geeft u de naam op van een algemeen besturings element of een weergave besturings element.</span><span class="sxs-lookup"><span data-stu-id="cd136-119">Specifies the name of a common control or a view control.</span></span>|
|[<span data-ttu-id="cd136-120">Het element EnumerateCollection voor ExpressionBinding voor Besturingselementen voor Configuratie (opmaak)</span><span class="sxs-lookup"><span data-stu-id="cd136-120">EnumerateCollection Element for ExpressionBinding for Controls for Configuration (Format)</span></span>](./enumeratecollection-element-for-expressionbinding-for-controls-for-configuration-format.md)|<span data-ttu-id="cd136-121">Optioneel element.</span><span class="sxs-lookup"><span data-stu-id="cd136-121">Optional element.</span></span><br /><br /> <span data-ttu-id="cd136-122">Opgegeven dat de elementen van verzamelingen worden weer gegeven door het besturings element.</span><span class="sxs-lookup"><span data-stu-id="cd136-122">Specified that the elements of collections are displayed by the control.</span></span>|
|[<span data-ttu-id="cd136-123">Het element ItemSelectionCondition voor ExpressionBinding voor Besturingselementen voor Configuratie (opmaak)</span><span class="sxs-lookup"><span data-stu-id="cd136-123">ItemSelectionCondition Element for ExpressionBinding for Controls for Configuration (Format)</span></span>](./itemselectioncondition-element-for-expressionbinding-for-controls-for-configuration-format.md)|<span data-ttu-id="cd136-124">Optioneel element.</span><span class="sxs-lookup"><span data-stu-id="cd136-124">Optional element.</span></span><br /><br /> <span data-ttu-id="cd136-125">Hiermee definieert u de voor waarde die moet bestaan voor het gebruik van dit algemene besturings element.</span><span class="sxs-lookup"><span data-stu-id="cd136-125">Defines the condition that must exist for this common control to be used.</span></span>|
|[<span data-ttu-id="cd136-126">Het element PropertyName voor ExpressionBinding voor Besturingselementen voor Configuratie (opmaak)</span><span class="sxs-lookup"><span data-stu-id="cd136-126">PropertyName Element for ExpressionBinding for Controls for Configuration (Format)</span></span>](./propertyname-element-for-expressionbinding-for-controls-for-configuration-format.md)|<span data-ttu-id="cd136-127">Optioneel element.</span><span class="sxs-lookup"><span data-stu-id="cd136-127">Optional element.</span></span><br /><br /> <span data-ttu-id="cd136-128">Hiermee geeft u de .NET-eigenschap op waarvan de waarde wordt weer gegeven door het algemene besturings element.</span><span class="sxs-lookup"><span data-stu-id="cd136-128">Specifies the .NET property whose value is displayed by the common control.</span></span>|
|[<span data-ttu-id="cd136-129">Het element ScriptBlock voor ExpressionBinding voor Besturingselementen voor Configuratie (opmaak)</span><span class="sxs-lookup"><span data-stu-id="cd136-129">ScriptBlock Element for ExpressionBinding for Controls for Configuration (Format)</span></span>](./scriptblock-element-for-expressionbinding-for-controls-for-configuration-format.md)|<span data-ttu-id="cd136-130">Optioneel element.</span><span class="sxs-lookup"><span data-stu-id="cd136-130">Optional element.</span></span><br /><br /> <span data-ttu-id="cd136-131">Hiermee geeft u het script op waarvan de waarde wordt weer gegeven door het algemene besturings element.</span><span class="sxs-lookup"><span data-stu-id="cd136-131">Specifies the script whose value is displayed by the common control.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="cd136-132">Bovenliggende elementen</span><span class="sxs-lookup"><span data-stu-id="cd136-132">Parent Elements</span></span>

|<span data-ttu-id="cd136-133">Element</span><span class="sxs-lookup"><span data-stu-id="cd136-133">Element</span></span>|<span data-ttu-id="cd136-134">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="cd136-134">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="cd136-135">CustomItem-element voor CustomEntry voor besturings elementen voor configuratie</span><span class="sxs-lookup"><span data-stu-id="cd136-135">CustomItem Element for CustomEntry for Controls for Configuration</span></span>](./customitem-element-for-customentry-for-controls-for-configuration-format.md)|<span data-ttu-id="cd136-136">Hiermee definieert u welke gegevens worden weer gegeven in de weer gave van het aangepaste besturings element en hoe deze worden weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="cd136-136">Defines what data is displayed by the custom control view and how it is displayed.</span></span>|

## <a name="remarks"></a><span data-ttu-id="cd136-137">Opmerkingen</span><span class="sxs-lookup"><span data-stu-id="cd136-137">Remarks</span></span>

## <a name="see-also"></a><span data-ttu-id="cd136-138">Zie ook</span><span class="sxs-lookup"><span data-stu-id="cd136-138">See Also</span></span>

[<span data-ttu-id="cd136-139">CustomItem-element voor CustomEntry voor besturings elementen voor configuratie</span><span class="sxs-lookup"><span data-stu-id="cd136-139">CustomItem Element for CustomEntry for Controls for Configuration</span></span>](./customitem-element-for-customentry-for-controls-for-configuration-format.md)

[<span data-ttu-id="cd136-140">Een PowerShell-opmaakbestand schrijven</span><span class="sxs-lookup"><span data-stu-id="cd136-140">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
