---
title: Script block-element voor ItemSeclectionCondition voor besturings elementen voor configuratie (indeling) | Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: f44b1a7f059fa5f41c19eed93762b61eda5110e8
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 08/05/2020
ms.locfileid: "87772889"
---
# <a name="scriptblock-element-for-itemseclectioncondition-for-controls-for-configuration-format"></a><span data-ttu-id="84ff1-102">Het element ScriptBlock voor ItemSelectionCondition voor Besturingselementen voor Configuratie (opmaak)</span><span class="sxs-lookup"><span data-stu-id="84ff1-102">ScriptBlock Element for ItemSeclectionCondition for Controls for Configuration (Format)</span></span>

<span data-ttu-id="84ff1-103">Hiermee geeft u het script op waarmee de voor waarde wordt geactiveerd.</span><span class="sxs-lookup"><span data-stu-id="84ff1-103">Specifies the script that triggers the condition.</span></span> <span data-ttu-id="84ff1-104">Wanneer dit script wordt geëvalueerd `true` , wordt voldaan aan de voor waarde en wordt het besturings element gebruikt.</span><span class="sxs-lookup"><span data-stu-id="84ff1-104">When this script is evaluated to `true`, the condition is met, and the control is used.</span></span> <span data-ttu-id="84ff1-105">Dit element wordt gebruikt bij het definiëren van een algemeen besturings element dat kan worden gebruikt door alle weer gaven in het opmaak bestand.</span><span class="sxs-lookup"><span data-stu-id="84ff1-105">This element is used when defining a common control that can be used by all the views in the formatting file.</span></span>

<span data-ttu-id="84ff1-106">Configuratie-element (Format) Controls element van configuratie (indeling) Control element voor besturings elementen voor configuratie (indeling) CustomControl-element voor besturings element voor configuratie (indeling) CustomEntries element voor het object CustomControl voor configuratie (indeling) CustomEntry configuratie (Format) CustomItem-element voor CustomEntry voor besturings elementen voor configuratie ExpressionBinding-element voor CustomItem voor besturings elementen voor configuratie (indeling) ItemSelectionCondition element voor ExpressionBinding voor besturings elementen voor configuratie (indeling) script block element voor ItemSelectionCondition voor besturings elementen voor configuratie (indeling)</span><span class="sxs-lookup"><span data-stu-id="84ff1-106">Configuration Element (Format) Controls Element of Configuration (Format) Control Element for Controls for Configuration (Format) CustomControl Element for Control for Configuration (Format) CustomEntries Element for CustomControl for Configuration (Format) CustomEntry Element for CustomControl for Controls for Configuration (Format) CustomItem Element for CustomEntry for Controls for Configuration ExpressionBinding Element for CustomItem for Controls for Configuration (Format) ItemSelectionCondition Element for ExpressionBinding for Controls for Configuration (Format) ScriptBlock Element for ItemSelectionCondition for Controls for Configuration (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="84ff1-107">Syntax</span><span class="sxs-lookup"><span data-stu-id="84ff1-107">Syntax</span></span>

```xml
<ScriptBlock>ScriptToEvaluate</ScriptBlock>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="84ff1-108">Kenmerken en elementen</span><span class="sxs-lookup"><span data-stu-id="84ff1-108">Attributes and Elements</span></span>

<span data-ttu-id="84ff1-109">In de volgende secties worden kenmerken, onderliggende elementen en het bovenliggende element van het `ScriptBlock` element beschreven.</span><span class="sxs-lookup"><span data-stu-id="84ff1-109">The following sections describe attributes, child elements, and the parent element of the `ScriptBlock` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="84ff1-110">Kenmerken</span><span class="sxs-lookup"><span data-stu-id="84ff1-110">Attributes</span></span>

<span data-ttu-id="84ff1-111">Geen.</span><span class="sxs-lookup"><span data-stu-id="84ff1-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="84ff1-112">Onderliggende elementen</span><span class="sxs-lookup"><span data-stu-id="84ff1-112">Child Elements</span></span>

<span data-ttu-id="84ff1-113">Geen.</span><span class="sxs-lookup"><span data-stu-id="84ff1-113">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="84ff1-114">Bovenliggende elementen</span><span class="sxs-lookup"><span data-stu-id="84ff1-114">Parent Elements</span></span>

|<span data-ttu-id="84ff1-115">Element</span><span class="sxs-lookup"><span data-stu-id="84ff1-115">Element</span></span>|<span data-ttu-id="84ff1-116">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="84ff1-116">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="84ff1-117">Het element ItemSelectionCondition voor ExpressionBinding voor Besturingselementen voor Configuratie (opmaak)</span><span class="sxs-lookup"><span data-stu-id="84ff1-117">ItemSelectionCondition Element for ExpressionBinding for Controls for Configuration (Format)</span></span>](./itemselectioncondition-element-for-expressionbinding-for-controls-for-configuration-format.md)|<span data-ttu-id="84ff1-118">Hiermee definieert u de voor waarde die moet bestaan voor het gebruik van dit besturings element.</span><span class="sxs-lookup"><span data-stu-id="84ff1-118">Defines the condition that must exist for this control to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="84ff1-119">Tekstwaarde</span><span class="sxs-lookup"><span data-stu-id="84ff1-119">Text Value</span></span>

<span data-ttu-id="84ff1-120">Geef het script op dat wordt geëvalueerd.</span><span class="sxs-lookup"><span data-stu-id="84ff1-120">Specify the script that is evaluated.</span></span>

## <a name="remarks"></a><span data-ttu-id="84ff1-121">Opmerkingen</span><span class="sxs-lookup"><span data-stu-id="84ff1-121">Remarks</span></span>

<span data-ttu-id="84ff1-122">Als dit element wordt gebruikt, kunt u het kenmerk [PropertyName](./propertyname-element-for-itemseclectioncondition-for-controls-for-configuration-format.md) niet opgeven bij het definiëren van de selectie voorwaarde.</span><span class="sxs-lookup"><span data-stu-id="84ff1-122">If this element is used, you cannot specify the [PropertyName](./propertyname-element-for-itemseclectioncondition-for-controls-for-configuration-format.md) element when defining the selection condition.</span></span>

## <a name="see-also"></a><span data-ttu-id="84ff1-123">Zie ook</span><span class="sxs-lookup"><span data-stu-id="84ff1-123">See Also</span></span>

[<span data-ttu-id="84ff1-124">Het element PropertyName voor ItemSelectionCondition voor Besturingselementen voor Configuratie (opmaak)</span><span class="sxs-lookup"><span data-stu-id="84ff1-124">PropertyName Element for ItemSeclectionCondition for Controls for Configuration (Format)</span></span>](./propertyname-element-for-itemseclectioncondition-for-controls-for-configuration-format.md)

[<span data-ttu-id="84ff1-125">Het element ItemSelectionCondition voor ExpressionBinding voor Besturingselementen voor Configuratie (opmaak)</span><span class="sxs-lookup"><span data-stu-id="84ff1-125">ItemSelectionCondition Element for ExpressionBinding for Controls for Configuration (Format)</span></span>](./itemselectioncondition-element-for-expressionbinding-for-controls-for-configuration-format.md)

[<span data-ttu-id="84ff1-126">Een PowerShell-opmaakbestand schrijven</span><span class="sxs-lookup"><span data-stu-id="84ff1-126">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
