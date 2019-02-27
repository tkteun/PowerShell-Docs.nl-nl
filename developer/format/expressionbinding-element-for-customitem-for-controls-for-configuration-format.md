---
title: ExpressionBinding-Element voor CustomItem voor besturingselementen voor de configuratie (-indeling) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: c6649d07-4762-4602-9b4b-d9e2e9e63312
caps.latest.revision: 13
ms.openlocfilehash: 531ff447f8407a737131a38351d7e4c6e7da90fb
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 02/03/2019
ms.locfileid: "56846205"
---
# <a name="expressionbinding-element-for-customitem-for-controls-for-configuration-format"></a><span data-ttu-id="bae29-102">Het element ExpressionBinding voor CustomItem voor Besturingselementen voor Configuratie (opmaak)</span><span class="sxs-lookup"><span data-stu-id="bae29-102">ExpressionBinding Element for CustomItem for Controls for Configuration (Format)</span></span>

<span data-ttu-id="bae29-103">Definieert de gegevens die door het besturingselement wordt weergegeven.</span><span class="sxs-lookup"><span data-stu-id="bae29-103">Defines the data that is displayed by the control.</span></span> <span data-ttu-id="bae29-104">Dit element wordt gebruikt bij het definiëren van een algemene besturingselement dat kan worden gebruikt door alle weergaven in de opmaak-bestand.</span><span class="sxs-lookup"><span data-stu-id="bae29-104">This element is used when defining a common control that can be used by all the views in the formatting file.</span></span>

<span data-ttu-id="bae29-105">Configuratie-Element (indeling) besturingselementen Element van configuratie (-indeling) besturingselement Element controles voor configuratie (-indeling) CustomControl-Element voor het besturingselement voor configuratie (-indeling) CustomEntries-Element voor CustomControl voor configuratie ( -Indeling) CustomEntry Element voor CustomControl controles voor configuratie (-indeling) CustomItem-Element voor CustomEntry voor besturingselementen voor ExpressionBinding, configuratie-Element voor CustomItem voor besturingselementen voor de configuratie (-indeling)</span><span class="sxs-lookup"><span data-stu-id="bae29-105">Configuration Element (Format) Controls Element of Configuration (Format) Control Element for Controls for Configuration (Format) CustomControl Element for Control for Configuration (Format) CustomEntries Element for CustomControl for Configuration (Format) CustomEntry Element for CustomControl for Controls for Configuration (Format) CustomItem Element for CustomEntry for Controls for Configuration ExpressionBinding Element for CustomItem for Controls for Configuration (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="bae29-106">Syntaxis</span><span class="sxs-lookup"><span data-stu-id="bae29-106">Syntax</span></span>

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

## <a name="attributes-and-elements"></a><span data-ttu-id="bae29-107">Kenmerken en elementen</span><span class="sxs-lookup"><span data-stu-id="bae29-107">Attributes and Elements</span></span>

<span data-ttu-id="bae29-108">De volgende secties beschrijven kenmerken, onderliggende elementen en het bovenliggende element van de `ExpressionBinding` element.</span><span class="sxs-lookup"><span data-stu-id="bae29-108">The following sections describe attributes, child elements, and the parent element of the `ExpressionBinding` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="bae29-109">Kenmerken</span><span class="sxs-lookup"><span data-stu-id="bae29-109">Attributes</span></span>

<span data-ttu-id="bae29-110">Geen.</span><span class="sxs-lookup"><span data-stu-id="bae29-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="bae29-111">Onderliggende elementen</span><span class="sxs-lookup"><span data-stu-id="bae29-111">Child Elements</span></span>

|<span data-ttu-id="bae29-112">Element</span><span class="sxs-lookup"><span data-stu-id="bae29-112">Element</span></span>|<span data-ttu-id="bae29-113">Description</span><span class="sxs-lookup"><span data-stu-id="bae29-113">Description</span></span>|
|-------------|-----------------|
|`CustomControl Element`|<span data-ttu-id="bae29-114">Optioneel element.</span><span class="sxs-lookup"><span data-stu-id="bae29-114">Optional element.</span></span><br /><br /> <span data-ttu-id="bae29-115">Hiermee definieert u een besturingselement dat wordt gebruikt door dit besturingselement.</span><span class="sxs-lookup"><span data-stu-id="bae29-115">Defines a control that is used by this control.</span></span>|
|[<span data-ttu-id="bae29-116">CustomControlName-Element voor ExpressionBinding voor besturingselementen voor de configuratie (-indeling)</span><span class="sxs-lookup"><span data-stu-id="bae29-116">CustomControlName Element for ExpressionBinding for Controls for Configuration (Format)</span></span>](./customcontrolname-element-for-expressionbinding-for-controls-for-configuration-format.md)|<span data-ttu-id="bae29-117">Optioneel element.</span><span class="sxs-lookup"><span data-stu-id="bae29-117">Optional element.</span></span><br /><br /> <span data-ttu-id="bae29-118">Hiermee geeft u de naam van een algemene besturingselement of een besturingselement voor lijstweergave.</span><span class="sxs-lookup"><span data-stu-id="bae29-118">Specifies the name of a common control or a view control.</span></span>|
|[<span data-ttu-id="bae29-119">EnumerateCollection-Element voor ExpressionBinding voor besturingselementen voor de configuratie (-indeling)</span><span class="sxs-lookup"><span data-stu-id="bae29-119">EnumerateCollection Element for ExpressionBinding for Controls for Configuration (Format)</span></span>](./enumeratecollection-element-for-expressionbinding-for-controls-for-configuration-format.md)|<span data-ttu-id="bae29-120">Optioneel element.</span><span class="sxs-lookup"><span data-stu-id="bae29-120">Optional element.</span></span><br /><br /> <span data-ttu-id="bae29-121">Opgegeven dat de elementen van verzamelingen worden weergegeven door het besturingselement.</span><span class="sxs-lookup"><span data-stu-id="bae29-121">Specified that the elements of collections are displayed by the control.</span></span>|
|[<span data-ttu-id="bae29-122">ItemSelectionCondition-Element voor ExpressionBinding voor besturingselementen voor de configuratie (-indeling)</span><span class="sxs-lookup"><span data-stu-id="bae29-122">ItemSelectionCondition Element for ExpressionBinding for Controls for Configuration (Format)</span></span>](./itemselectioncondition-element-for-expressionbinding-for-controls-for-configuration-format.md)|<span data-ttu-id="bae29-123">Optioneel element.</span><span class="sxs-lookup"><span data-stu-id="bae29-123">Optional element.</span></span><br /><br /> <span data-ttu-id="bae29-124">Hiermee definieert u de voorwaarde die moet bestaan voor dit algemene besturingselement moet worden gebruikt.</span><span class="sxs-lookup"><span data-stu-id="bae29-124">Defines the condition that must exist for this common control to be used.</span></span>|
|[<span data-ttu-id="bae29-125">PropertyName-Element voor ExpressionBinding voor besturingselementen voor de configuratie (-indeling)</span><span class="sxs-lookup"><span data-stu-id="bae29-125">PropertyName Element for ExpressionBinding for Controls for Configuration (Format)</span></span>](./propertyname-element-for-expressionbinding-for-controls-for-configuration-format.md)|<span data-ttu-id="bae29-126">Optioneel element.</span><span class="sxs-lookup"><span data-stu-id="bae29-126">Optional element.</span></span><br /><br /> <span data-ttu-id="bae29-127">Hiermee geeft u de .NET-eigenschap waarvan de waarde van het algemene besturingselement wordt weergegeven.</span><span class="sxs-lookup"><span data-stu-id="bae29-127">Specifies the .NET property whose value is displayed by the common control.</span></span>|
|[<span data-ttu-id="bae29-128">ScriptBlock-Element voor ExpressionBinding voor besturingselementen voor de configuratie (-indeling)</span><span class="sxs-lookup"><span data-stu-id="bae29-128">ScriptBlock Element for ExpressionBinding for Controls for Configuration (Format)</span></span>](./scriptblock-element-for-expressionbinding-for-controls-for-configuration-format.md)|<span data-ttu-id="bae29-129">Optioneel element.</span><span class="sxs-lookup"><span data-stu-id="bae29-129">Optional element.</span></span><br /><br /> <span data-ttu-id="bae29-130">Hiermee geeft u het script waarvan de waarde van het algemene besturingselement wordt weergegeven.</span><span class="sxs-lookup"><span data-stu-id="bae29-130">Specifies the script whose value is displayed by the common control.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="bae29-131">Bovenliggende elementen</span><span class="sxs-lookup"><span data-stu-id="bae29-131">Parent Elements</span></span>

|<span data-ttu-id="bae29-132">Element</span><span class="sxs-lookup"><span data-stu-id="bae29-132">Element</span></span>|<span data-ttu-id="bae29-133">Description</span><span class="sxs-lookup"><span data-stu-id="bae29-133">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="bae29-134">CustomItem-Element voor CustomEntry voor besturingselementen voor configuratie</span><span class="sxs-lookup"><span data-stu-id="bae29-134">CustomItem Element for CustomEntry for Controls for Configuration</span></span>](./customitem-element-for-customentry-for-controls-for-configuration-format.md)|<span data-ttu-id="bae29-135">Bepaalt welke gegevens worden weergegeven in de weergave van het aangepaste besturingselement en hoe deze wordt weergegeven.</span><span class="sxs-lookup"><span data-stu-id="bae29-135">Defines what data is displayed by the custom control view and how it is displayed.</span></span>|

## <a name="remarks"></a><span data-ttu-id="bae29-136">Opmerkingen</span><span class="sxs-lookup"><span data-stu-id="bae29-136">Remarks</span></span>

## <a name="see-also"></a><span data-ttu-id="bae29-137">Zie ook</span><span class="sxs-lookup"><span data-stu-id="bae29-137">See Also</span></span>

[<span data-ttu-id="bae29-138">CustomItem-Element voor CustomEntry voor besturingselementen voor configuratie</span><span class="sxs-lookup"><span data-stu-id="bae29-138">CustomItem Element for CustomEntry for Controls for Configuration</span></span>](./customitem-element-for-customentry-for-controls-for-configuration-format.md)

[<span data-ttu-id="bae29-139">Schrijven van een bestand opmaak PowerShell</span><span class="sxs-lookup"><span data-stu-id="bae29-139">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
