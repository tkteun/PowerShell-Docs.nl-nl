---
ms.date: 09/13/2016
ms.topic: reference
title: Het element Besturingselementen voor Configuratie (opmaak)
description: Het element Besturingselementen voor Configuratie (opmaak)
ms.openlocfilehash: 53f874ddccf3b4f1f0a23aad608e786524bde830
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/27/2020
ms.locfileid: "92668096"
---
# <a name="controls-element-for-configuration-format"></a><span data-ttu-id="09780-103">Het element Besturingselementen voor Configuratie (opmaak)</span><span class="sxs-lookup"><span data-stu-id="09780-103">Controls Element for Configuration (Format)</span></span>

<span data-ttu-id="09780-104">Hiermee definieert u de algemene besturings elementen die kunnen worden gebruikt door alle weer gaven van het opmaak bestand.</span><span class="sxs-lookup"><span data-stu-id="09780-104">Defines the common controls that can be used by all views of the formatting file.</span></span>

<span data-ttu-id="09780-105">Configuratie-element (Format) bepaalt element van de configuratie (indeling)</span><span class="sxs-lookup"><span data-stu-id="09780-105">Configuration Element (Format) Controls Element of Configuration (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="09780-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="09780-106">Syntax</span></span>

```xml
<Controls>
  <Control>...</Control>
</Controls>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="09780-107">Kenmerken en elementen</span><span class="sxs-lookup"><span data-stu-id="09780-107">Attributes and Elements</span></span>

<span data-ttu-id="09780-108">In de volgende secties worden de kenmerken, onderliggende elementen en het bovenliggende element van het `Controls` element beschreven.</span><span class="sxs-lookup"><span data-stu-id="09780-108">The following sections describe the attributes, child elements, and the parent element of the `Controls` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="09780-109">Kenmerken</span><span class="sxs-lookup"><span data-stu-id="09780-109">Attributes</span></span>

<span data-ttu-id="09780-110">Geen.</span><span class="sxs-lookup"><span data-stu-id="09780-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="09780-111">Onderliggende elementen</span><span class="sxs-lookup"><span data-stu-id="09780-111">Child Elements</span></span>

|<span data-ttu-id="09780-112">Element</span><span class="sxs-lookup"><span data-stu-id="09780-112">Element</span></span>|<span data-ttu-id="09780-113">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="09780-113">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="09780-114">Het element Besturingselement voor Besturingselementen voor Configuratie (opmaak)</span><span class="sxs-lookup"><span data-stu-id="09780-114">Control Element for Controls for Configuration (Format)</span></span>](./control-element-for-controls-for-configuration-format.md)|<span data-ttu-id="09780-115">Vereist element.</span><span class="sxs-lookup"><span data-stu-id="09780-115">Required element.</span></span><br /><br /> <span data-ttu-id="09780-116">Hiermee wordt een algemeen besturings element gedefinieerd dat kan worden gebruikt door alle weer gaven van het opmaak bestand.</span><span class="sxs-lookup"><span data-stu-id="09780-116">Defines a common control that can be used by all views of the formatting file.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="09780-117">Bovenliggende elementen</span><span class="sxs-lookup"><span data-stu-id="09780-117">Parent Elements</span></span>

|<span data-ttu-id="09780-118">Element</span><span class="sxs-lookup"><span data-stu-id="09780-118">Element</span></span>|<span data-ttu-id="09780-119">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="09780-119">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="09780-120">Het element Configuratie (opmaak)</span><span class="sxs-lookup"><span data-stu-id="09780-120">Configuration Element (Format)</span></span>](./configuration-element-format.md)|<span data-ttu-id="09780-121">Vertegenwoordigt het element op het hoogste niveau van een opmaak bestand.</span><span class="sxs-lookup"><span data-stu-id="09780-121">Represents the top-level element of a formatting file.</span></span>|

## <a name="remarks"></a><span data-ttu-id="09780-122">Opmerkingen</span><span class="sxs-lookup"><span data-stu-id="09780-122">Remarks</span></span>

<span data-ttu-id="09780-123">U kunt een wille keurig aantal algemene besturings elementen maken.</span><span class="sxs-lookup"><span data-stu-id="09780-123">You can create any number of common controls.</span></span> <span data-ttu-id="09780-124">Voor elk besturings element moet u de naam opgeven die wordt gebruikt om te verwijzen naar het besturings element en de onderdelen van het besturings element.</span><span class="sxs-lookup"><span data-stu-id="09780-124">For each control, you must specify the name that is used to reference the control and the components of the control.</span></span>

## <a name="see-also"></a><span data-ttu-id="09780-125">Zie ook</span><span class="sxs-lookup"><span data-stu-id="09780-125">See Also</span></span>

[<span data-ttu-id="09780-126">Het element Configuratie (opmaak)</span><span class="sxs-lookup"><span data-stu-id="09780-126">Configuration Element (Format)</span></span>](./configuration-element-format.md)

[<span data-ttu-id="09780-127">Het element Besturingselement voor Besturingselementen voor Configuratie (opmaak)</span><span class="sxs-lookup"><span data-stu-id="09780-127">Control Element for Controls for Configuration (Format)</span></span>](./control-element-for-controls-for-configuration-format.md)

[<span data-ttu-id="09780-128">Een PowerShell-opmaakbestand schrijven</span><span class="sxs-lookup"><span data-stu-id="09780-128">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
