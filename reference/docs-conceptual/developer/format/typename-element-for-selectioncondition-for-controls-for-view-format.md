---
title: TypeName-element voor SelectionCondition voor besturings elementen voor weer gave (indeling) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 7141aefc-6656-4c52-8a9c-c2bfc9c87be9
caps.latest.revision: 6
ms.openlocfilehash: 7a697c286ec9efe750930739cdfa2580003365dd
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/15/2019
ms.locfileid: "72353541"
---
# <a name="typename-element-for-selectioncondition-for-controls-for-view-format"></a><span data-ttu-id="1f8de-102">Het element TypeName voor SelectionCondition voor Besturingselementen voor Weergave (opmaak)</span><span class="sxs-lookup"><span data-stu-id="1f8de-102">TypeName Element for SelectionCondition for Controls for View (Format)</span></span>

<span data-ttu-id="1f8de-103">Hiermee geeft u een .NET-type op waarmee de voor waarde wordt geactiveerd.</span><span class="sxs-lookup"><span data-stu-id="1f8de-103">Specifies a .NET type that triggers the condition.</span></span> <span data-ttu-id="1f8de-104">Dit element wordt gebruikt bij het definiëren van besturings elementen die kunnen worden gebruikt door een weer gave.</span><span class="sxs-lookup"><span data-stu-id="1f8de-104">This element is used when defining controls that can be used by a view.</span></span>

<span data-ttu-id="1f8de-105">Configuratie-element (indeling) ViewDefinitions element (indeling) element weer geven (indeling) Controls-element (Format) Control element (opmaak) voor besturings elementen voor de weer gave (indeling) CustomControl-element voor besturings elementen voor Controls (Format) CustomEntries element voor CustomControl voor besturings elementen voor weer gave (indeling) CustomEntry element voor CustomEntries voor besturings elementen voor de weer gave (Format) EntrySelectedBy-element voor CustomEntry voor besturings elementen voor de weer gave (Format) SelectionCondition-element voor EntrySelectedBy for Controls ( Format) TypeName-element voor SelectionCondition voor besturings elementen voor weer gave (indeling)</span><span class="sxs-lookup"><span data-stu-id="1f8de-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) Controls Element (Format) Control Element for Controls for View (Format) CustomControl Element for Control for Controls for View (Format) CustomEntries Element for CustomControl for Controls for View (Format) CustomEntry Element for CustomEntries for Controls for View (Format) EntrySelectedBy Element for CustomEntry for Controls for View (Format) SelectionCondition Element for EntrySelectedBy for Controls for View (Format) TypeName Element for SelectionCondition for Controls for View (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="1f8de-106">Syntaxis</span><span class="sxs-lookup"><span data-stu-id="1f8de-106">Syntax</span></span>

```xml
<TypeName>Nameof.NetType</TypeName>

```

## <a name="attributes-and-elements"></a><span data-ttu-id="1f8de-107">Kenmerken en elementen</span><span class="sxs-lookup"><span data-stu-id="1f8de-107">Attributes and Elements</span></span>

<span data-ttu-id="1f8de-108">In de volgende secties worden kenmerken, onderliggende elementen en het bovenliggende element van het element `TypeName` beschreven.</span><span class="sxs-lookup"><span data-stu-id="1f8de-108">The following sections describe attributes, child elements, and the parent element of the `TypeName` Element.</span></span>

### <a name="attributes"></a><span data-ttu-id="1f8de-109">Kenmerken</span><span class="sxs-lookup"><span data-stu-id="1f8de-109">Attributes</span></span>

<span data-ttu-id="1f8de-110">Geen.</span><span class="sxs-lookup"><span data-stu-id="1f8de-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="1f8de-111">Onderliggende elementen</span><span class="sxs-lookup"><span data-stu-id="1f8de-111">Child Elements</span></span>

<span data-ttu-id="1f8de-112">Geen.</span><span class="sxs-lookup"><span data-stu-id="1f8de-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="1f8de-113">Bovenliggende elementen</span><span class="sxs-lookup"><span data-stu-id="1f8de-113">Parent Elements</span></span>

|<span data-ttu-id="1f8de-114">Element</span><span class="sxs-lookup"><span data-stu-id="1f8de-114">Element</span></span>|<span data-ttu-id="1f8de-115">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="1f8de-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="1f8de-116">SelectionCondition-element voor EntrySelectedBy voor besturings elementen voor weer gave (indeling)</span><span class="sxs-lookup"><span data-stu-id="1f8de-116">SelectionCondition Element for EntrySelectedBy for Controls for View (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-controls-for-view-format.md)|<span data-ttu-id="1f8de-117">Hiermee definieert u een voor waarde die moet bestaan voor het gebruik van de controle definitie.</span><span class="sxs-lookup"><span data-stu-id="1f8de-117">Defines a condition that must exist for the control definition to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="1f8de-118">Tekst waarde</span><span class="sxs-lookup"><span data-stu-id="1f8de-118">Text Value</span></span>

<span data-ttu-id="1f8de-119">Geef de volledig gekwalificeerde naam van het .NET-type op, bijvoorbeeld `System.IO.DirectoryInfo`.</span><span class="sxs-lookup"><span data-stu-id="1f8de-119">Specify the fully qualified name of the .NET type, such as `System.IO.DirectoryInfo`.</span></span>

## <a name="remarks"></a><span data-ttu-id="1f8de-120">Opmerkingen</span><span class="sxs-lookup"><span data-stu-id="1f8de-120">Remarks</span></span>

## <a name="see-also"></a><span data-ttu-id="1f8de-121">Zie ook</span><span class="sxs-lookup"><span data-stu-id="1f8de-121">See Also</span></span>

[<span data-ttu-id="1f8de-122">SelectionCondition-element voor EntrySelectedBy voor besturings elementen voor weer gave (indeling)</span><span class="sxs-lookup"><span data-stu-id="1f8de-122">SelectionCondition Element for EntrySelectedBy for Controls for View (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-controls-for-view-format.md)

[<span data-ttu-id="1f8de-123">Een Power shell-indelings bestand schrijven</span><span class="sxs-lookup"><span data-stu-id="1f8de-123">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
