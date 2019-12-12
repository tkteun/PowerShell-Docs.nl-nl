---
title: FirstLineHanging-element voor frame voor besturings elementen voor weer gave (indeling) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 53694f08-57f7-4185-b443-1636a0918afc
caps.latest.revision: 8
ms.openlocfilehash: 387340cd9b0aae2ad0419b187d96ab4fee183d5a
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 12/05/2019
ms.locfileid: "72355074"
---
# <a name="firstlinehanging-element-for-frame-for-controls-for-view-format"></a><span data-ttu-id="e00b2-102">Het element FirstLineHanging voor Frame voor Besturingselementen voor Weergave (opmaak)</span><span class="sxs-lookup"><span data-stu-id="e00b2-102">FirstLineHanging Element for Frame for Controls for View (Format)</span></span>

<span data-ttu-id="e00b2-103">Geeft aan hoeveel tekens de eerste regel van de gegevens naar links verschuift.</span><span class="sxs-lookup"><span data-stu-id="e00b2-103">Specifies how many characters the first line of data is shifted to the left.</span></span> <span data-ttu-id="e00b2-104">Dit element wordt gebruikt bij het definiëren van besturings elementen die kunnen worden gebruikt door een weer gave.</span><span class="sxs-lookup"><span data-stu-id="e00b2-104">This element is used when defining controls that can be used by a view.</span></span>

<span data-ttu-id="e00b2-105">Configuratie-element (indeling) ViewDefinitions element (indeling) element weer geven (indeling) Controls-element (Format) Control element (opmaak) voor besturings elementen voor de weer gave (indeling) CustomControl-element voor besturings elementen voor Controls (Format) CustomEntries element voor CustomControl voor View (Format) CustomEntry-element voor CustomEntries voor besturings elementen voor weer gave (Format) CustomItem-element voor CustomEntry voor besturings elementen voor de weer gave (Format)-frame-element voor CustomItem voor besturings elementen voor de weer gave (Format) FirstLineHanging-element van Frame van de besturings elementen van de weer gave (indeling)</span><span class="sxs-lookup"><span data-stu-id="e00b2-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) Controls Element (Format) Control Element for Controls for View (Format) CustomControl Element for Control for Controls for View (Format) CustomEntries Element for CustomControl for View (Format) CustomEntry Element for CustomEntries for Controls for View (Format) CustomItem Element for CustomEntry for Controls for View (Format) Frame Element for CustomItem for Controls for View (Format) FirstLineHanging Element of Frame of Controls of View (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="e00b2-106">Syntaxis</span><span class="sxs-lookup"><span data-stu-id="e00b2-106">Syntax</span></span>

```xml
<FirstLineHanging>NumberOfCharactersToShift</FirstLineHanging>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="e00b2-107">Kenmerken en elementen</span><span class="sxs-lookup"><span data-stu-id="e00b2-107">Attributes and Elements</span></span>

<span data-ttu-id="e00b2-108">In de volgende secties worden de kenmerken, onderliggende elementen en het bovenliggende element van het element `FirstLineHanging` beschreven.</span><span class="sxs-lookup"><span data-stu-id="e00b2-108">The following sections describe attributes, child elements, and parent element of the `FirstLineHanging` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="e00b2-109">Kenmerken</span><span class="sxs-lookup"><span data-stu-id="e00b2-109">Attributes</span></span>

<span data-ttu-id="e00b2-110">Geen.</span><span class="sxs-lookup"><span data-stu-id="e00b2-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="e00b2-111">Onderliggende elementen</span><span class="sxs-lookup"><span data-stu-id="e00b2-111">Child Elements</span></span>

<span data-ttu-id="e00b2-112">Geen.</span><span class="sxs-lookup"><span data-stu-id="e00b2-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="e00b2-113">Bovenliggende elementen</span><span class="sxs-lookup"><span data-stu-id="e00b2-113">Parent Elements</span></span>

|<span data-ttu-id="e00b2-114">Element</span><span class="sxs-lookup"><span data-stu-id="e00b2-114">Element</span></span>|<span data-ttu-id="e00b2-115">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="e00b2-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="e00b2-116">Frame-element voor CustomItem voor besturings elementen voor weer gave (indeling)</span><span class="sxs-lookup"><span data-stu-id="e00b2-116">Frame Element for CustomItem for Controls for View (Format)</span></span>](./frame-element-for-customitem-for-controls-for-view-format.md)|<span data-ttu-id="e00b2-117">Hiermee definieert u hoe de gegevens worden weer gegeven, zoals de gegevens naar links of rechts verplaatsen.</span><span class="sxs-lookup"><span data-stu-id="e00b2-117">Defines how the data is displayed, such as shifting the data to the left or right.</span></span>|

## <a name="text-value"></a><span data-ttu-id="e00b2-118">Tekstwaarde</span><span class="sxs-lookup"><span data-stu-id="e00b2-118">Text Value</span></span>

<span data-ttu-id="e00b2-119">Geef het aantal tekens op waarmee u de eerste regel van de gegevens wilt verschuiven.</span><span class="sxs-lookup"><span data-stu-id="e00b2-119">Specify the number of characters that you want to shift the first line of the data.</span></span>

## <a name="remarks"></a><span data-ttu-id="e00b2-120">Opmerkingen</span><span class="sxs-lookup"><span data-stu-id="e00b2-120">Remarks</span></span>

<span data-ttu-id="e00b2-121">Als dit element is opgegeven, kunt u het [FirstLineIndent](./firstlineindent-element-for-frame-for-controls-for-view-format.md) -element niet opgeven.</span><span class="sxs-lookup"><span data-stu-id="e00b2-121">If this element is specified, you cannot specify the [FirstLineIndent](./firstlineindent-element-for-frame-for-controls-for-view-format.md) element.</span></span>

## <a name="see-also"></a><span data-ttu-id="e00b2-122">Zie ook</span><span class="sxs-lookup"><span data-stu-id="e00b2-122">See Also</span></span>

[<span data-ttu-id="e00b2-123">FirstLineIndent-element voor frame voor besturings elementen voor weer gave (indeling)</span><span class="sxs-lookup"><span data-stu-id="e00b2-123">FirstLineIndent Element for Frame for Controls for View (Format)</span></span>](./firstlineindent-element-for-frame-for-controls-for-view-format.md)

[<span data-ttu-id="e00b2-124">Frame-element voor CustomItem voor besturings elementen voor weer gave (indeling)</span><span class="sxs-lookup"><span data-stu-id="e00b2-124">Frame Element for CustomItem for Controls for View (Format)</span></span>](./frame-element-for-customitem-for-controls-for-view-format.md)

[<span data-ttu-id="e00b2-125">Een Power shell-indelings bestand schrijven</span><span class="sxs-lookup"><span data-stu-id="e00b2-125">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
