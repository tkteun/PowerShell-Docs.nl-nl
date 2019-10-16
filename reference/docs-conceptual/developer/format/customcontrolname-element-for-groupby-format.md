---
title: CustomControlName-element voor GroupBy (indeling) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 473d9b56-521b-479a-8010-67fe9f040063
caps.latest.revision: 8
ms.openlocfilehash: 3a386eff95044eae573c255a451c5c8b8f16714d
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/15/2019
ms.locfileid: "72359034"
---
# <a name="customcontrolname-element-for-groupby-format"></a><span data-ttu-id="fdb97-102">Het element CustomControlName voor GroupBy (opmaak)</span><span class="sxs-lookup"><span data-stu-id="fdb97-102">CustomControlName Element for GroupBy (Format)</span></span>

<span data-ttu-id="fdb97-103">Hiermee geeft u de naam op van een aangepast besturings element dat wordt gebruikt om de nieuwe groep weer te geven.</span><span class="sxs-lookup"><span data-stu-id="fdb97-103">Specifies the name of a custom control that is used to display the new group.</span></span> <span data-ttu-id="fdb97-104">Dit element wordt gebruikt bij het definiëren van een tabel, lijst, brede of aangepaste beheer weergave.</span><span class="sxs-lookup"><span data-stu-id="fdb97-104">This element is used when defining a table, list, wide or custom control view.</span></span>

<span data-ttu-id="fdb97-105">Configuratie-element (indeling) ViewDefinitions element (indeling) element weer geven (indeling) GroupBy-element voor weer gave (indeling) CustomControlName element van GroupBy (indeling)</span><span class="sxs-lookup"><span data-stu-id="fdb97-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) GroupBy Element for View (Format) CustomControlName Element of GroupBy (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="fdb97-106">Syntaxis</span><span class="sxs-lookup"><span data-stu-id="fdb97-106">Syntax</span></span>

```xml
<CustomControlName>ControlName</CustomControlName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="fdb97-107">Kenmerken en elementen</span><span class="sxs-lookup"><span data-stu-id="fdb97-107">Attributes and Elements</span></span>

<span data-ttu-id="fdb97-108">In de volgende secties worden de kenmerken, onderliggende elementen en bovenliggende elementen van het element `CustomControlName` beschreven.</span><span class="sxs-lookup"><span data-stu-id="fdb97-108">The following sections describe the attributes, child elements, and parent elements of the `CustomControlName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="fdb97-109">Kenmerken</span><span class="sxs-lookup"><span data-stu-id="fdb97-109">Attributes</span></span>

<span data-ttu-id="fdb97-110">Geen.</span><span class="sxs-lookup"><span data-stu-id="fdb97-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="fdb97-111">Onderliggende elementen</span><span class="sxs-lookup"><span data-stu-id="fdb97-111">Child Elements</span></span>

<span data-ttu-id="fdb97-112">Geen.</span><span class="sxs-lookup"><span data-stu-id="fdb97-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="fdb97-113">Bovenliggende elementen</span><span class="sxs-lookup"><span data-stu-id="fdb97-113">Parent Elements</span></span>

|<span data-ttu-id="fdb97-114">Element</span><span class="sxs-lookup"><span data-stu-id="fdb97-114">Element</span></span>|<span data-ttu-id="fdb97-115">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="fdb97-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="fdb97-116">Element GroupBy voor weer gave (indeling)</span><span class="sxs-lookup"><span data-stu-id="fdb97-116">GroupBy Element for View (Format)</span></span>](./groupby-element-for-view-format.md)|<span data-ttu-id="fdb97-117">Definieert hoe een nieuwe groep objecten wordt weer gegeven in Windows Power shell.</span><span class="sxs-lookup"><span data-stu-id="fdb97-117">Defines how Windows PowerShell displays a new group of objects.</span></span>|

## <a name="text-value"></a><span data-ttu-id="fdb97-118">Tekst waarde</span><span class="sxs-lookup"><span data-stu-id="fdb97-118">Text Value</span></span>

<span data-ttu-id="fdb97-119">Geef de naam op van het aangepaste besturings element dat wordt gebruikt om een nieuwe groep weer te geven.</span><span class="sxs-lookup"><span data-stu-id="fdb97-119">Specify the name of the custom control that is used to display a new group.</span></span>

## <a name="remarks"></a><span data-ttu-id="fdb97-120">Opmerkingen</span><span class="sxs-lookup"><span data-stu-id="fdb97-120">Remarks</span></span>

<span data-ttu-id="fdb97-121">U kunt algemene besturings elementen maken die kunnen worden gebruikt door alle weer gaven van een opmaak bestand, en u kunt weergave besturings elementen maken die kunnen worden gebruikt door een specifieke weer gave.</span><span class="sxs-lookup"><span data-stu-id="fdb97-121">You can create common controls that can be used by all the views of a formatting file, and you can create view controls that can be used by a specific view.</span></span> <span data-ttu-id="fdb97-122">In de volgende elementen worden de namen van deze aangepaste besturings elementen opgegeven:</span><span class="sxs-lookup"><span data-stu-id="fdb97-122">The following elements specify the names of these custom controls:</span></span>

- [<span data-ttu-id="fdb97-123">Element naam voor besturings elementen voor configuratie (indeling)</span><span class="sxs-lookup"><span data-stu-id="fdb97-123">Name Element for Control for Controls for Configuration (Format)</span></span>](./name-element-for-control-for-controls-for-configuration-format.md)

- [<span data-ttu-id="fdb97-124">Element naam voor besturings elementen voor weer gave (indeling)</span><span class="sxs-lookup"><span data-stu-id="fdb97-124">Name Element for Control for Controls for View (Format)</span></span>](./name-element-for-control-for-controls-for-view-format.md)

## <a name="see-also"></a><span data-ttu-id="fdb97-125">Zie ook</span><span class="sxs-lookup"><span data-stu-id="fdb97-125">See Also</span></span>

[<span data-ttu-id="fdb97-126">Element GroupBy voor weer gave (indeling)</span><span class="sxs-lookup"><span data-stu-id="fdb97-126">GroupBy Element for View (Format)</span></span>](./groupby-element-for-view-format.md)

[<span data-ttu-id="fdb97-127">Element naam voor besturings elementen voor configuratie (indeling)</span><span class="sxs-lookup"><span data-stu-id="fdb97-127">Name Element for Control for Controls for Configuration (Format)</span></span>](./name-element-for-control-for-controls-for-configuration-format.md)

[<span data-ttu-id="fdb97-128">Element naam voor besturings elementen voor weer gave (indeling)</span><span class="sxs-lookup"><span data-stu-id="fdb97-128">Name Element for Control for Controls for View (Format)</span></span>](./name-element-for-control-for-controls-for-view-format.md)

[<span data-ttu-id="fdb97-129">Een Power shell-indelings bestand schrijven</span><span class="sxs-lookup"><span data-stu-id="fdb97-129">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
