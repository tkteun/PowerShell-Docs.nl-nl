---
title: Controls-element voor configuratie (indeling) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 4d4ef63d-5866-4319-ba00-7ed96de26821
caps.latest.revision: 18
ms.openlocfilehash: ac9f7ff08f6e87ef83b5a2fe23fc58ee2651566d
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/15/2019
ms.locfileid: "72359096"
---
# <a name="controls-element-for-configuration-format"></a><span data-ttu-id="de415-102">Het element Besturingselementen voor Configuratie (opmaak)</span><span class="sxs-lookup"><span data-stu-id="de415-102">Controls Element for Configuration (Format)</span></span>

<span data-ttu-id="de415-103">Hiermee definieert u de algemene besturings elementen die kunnen worden gebruikt door alle weer gaven van het opmaak bestand.</span><span class="sxs-lookup"><span data-stu-id="de415-103">Defines the common controls that can be used by all views of the formatting file.</span></span>

<span data-ttu-id="de415-104">Configuratie-element (Format) bepaalt element van de configuratie (indeling)</span><span class="sxs-lookup"><span data-stu-id="de415-104">Configuration Element (Format) Controls Element of Configuration (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="de415-105">Syntaxis</span><span class="sxs-lookup"><span data-stu-id="de415-105">Syntax</span></span>

```xml
<Controls>
  <Control>...</Control>
</Controls>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="de415-106">Kenmerken en elementen</span><span class="sxs-lookup"><span data-stu-id="de415-106">Attributes and Elements</span></span>

<span data-ttu-id="de415-107">In de volgende secties worden de kenmerken, onderliggende elementen en het bovenliggende element van het element `Controls` beschreven.</span><span class="sxs-lookup"><span data-stu-id="de415-107">The following sections describe the attributes, child elements, and the parent element of the `Controls` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="de415-108">Kenmerken</span><span class="sxs-lookup"><span data-stu-id="de415-108">Attributes</span></span>

<span data-ttu-id="de415-109">Geen.</span><span class="sxs-lookup"><span data-stu-id="de415-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="de415-110">Onderliggende elementen</span><span class="sxs-lookup"><span data-stu-id="de415-110">Child Elements</span></span>

|<span data-ttu-id="de415-111">Element</span><span class="sxs-lookup"><span data-stu-id="de415-111">Element</span></span>|<span data-ttu-id="de415-112">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="de415-112">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="de415-113">Control-element voor besturings elementen voor configuratie (indeling)</span><span class="sxs-lookup"><span data-stu-id="de415-113">Control Element for Controls for Configuration (Format)</span></span>](./control-element-for-controls-for-configuration-format.md)|<span data-ttu-id="de415-114">Vereist element.</span><span class="sxs-lookup"><span data-stu-id="de415-114">Required element.</span></span><br /><br /> <span data-ttu-id="de415-115">Hiermee wordt een algemeen besturings element gedefinieerd dat kan worden gebruikt door alle weer gaven van het opmaak bestand.</span><span class="sxs-lookup"><span data-stu-id="de415-115">Defines a common control that can be used by all views of the formatting file.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="de415-116">Bovenliggende elementen</span><span class="sxs-lookup"><span data-stu-id="de415-116">Parent Elements</span></span>

|<span data-ttu-id="de415-117">Element</span><span class="sxs-lookup"><span data-stu-id="de415-117">Element</span></span>|<span data-ttu-id="de415-118">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="de415-118">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="de415-119">Configuratie-element (indeling)</span><span class="sxs-lookup"><span data-stu-id="de415-119">Configuration Element (Format)</span></span>](./configuration-element-format.md)|<span data-ttu-id="de415-120">Vertegenwoordigt het element op het hoogste niveau van een opmaak bestand.</span><span class="sxs-lookup"><span data-stu-id="de415-120">Represents the top-level element of a formatting file.</span></span>|

## <a name="remarks"></a><span data-ttu-id="de415-121">Opmerkingen</span><span class="sxs-lookup"><span data-stu-id="de415-121">Remarks</span></span>

<span data-ttu-id="de415-122">U kunt een wille keurig aantal algemene besturings elementen maken.</span><span class="sxs-lookup"><span data-stu-id="de415-122">You can create any number of common controls.</span></span> <span data-ttu-id="de415-123">Voor elk besturings element moet u de naam opgeven die wordt gebruikt om te verwijzen naar het besturings element en de onderdelen van het besturings element.</span><span class="sxs-lookup"><span data-stu-id="de415-123">For each control, you must specify the name that is used to reference the control and the components of the control.</span></span>

## <a name="see-also"></a><span data-ttu-id="de415-124">Zie ook</span><span class="sxs-lookup"><span data-stu-id="de415-124">See Also</span></span>

[<span data-ttu-id="de415-125">Configuratie-element (indeling)</span><span class="sxs-lookup"><span data-stu-id="de415-125">Configuration Element (Format)</span></span>](./configuration-element-format.md)

[<span data-ttu-id="de415-126">Control-element voor besturings elementen voor configuratie (indeling)</span><span class="sxs-lookup"><span data-stu-id="de415-126">Control Element for Controls for Configuration (Format)</span></span>](./control-element-for-controls-for-configuration-format.md)

[<span data-ttu-id="de415-127">Een Power shell-indelings bestand schrijven</span><span class="sxs-lookup"><span data-stu-id="de415-127">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
