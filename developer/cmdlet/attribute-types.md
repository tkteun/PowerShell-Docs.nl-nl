---
title: Kenmerken van het type | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 9b1026ad-f072-4fca-8052-a2d8eb491c2a
caps.latest.revision: 6
ms.openlocfilehash: 52c75b3ca73706da39029d5b3ead52ff7197a5f1
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62068654"
---
# <a name="attribute-types"></a><span data-ttu-id="c323e-102">Typen kenmerken</span><span class="sxs-lookup"><span data-stu-id="c323e-102">Attribute Types</span></span>

<span data-ttu-id="c323e-103">Cmdlet kenmerken kunnen worden gegroepeerd op functionaliteit.</span><span class="sxs-lookup"><span data-stu-id="c323e-103">Cmdlet attributes can be grouped by functionality.</span></span>
<span data-ttu-id="c323e-104">De volgende secties beschrijven de beschikbare kenmerken en wordt beschreven wat de runtime doet wanneer het kenmerk wordt aangeroepen.</span><span class="sxs-lookup"><span data-stu-id="c323e-104">The following sections describe the available attributes and describe what the runtime does when the attribute is invoked.</span></span>

## <a name="cmdlet-attributes"></a><span data-ttu-id="c323e-105">Cmdlet-kenmerken</span><span class="sxs-lookup"><span data-stu-id="c323e-105">Cmdlet Attributes</span></span>

### <a name="cmdlet"></a><span data-ttu-id="c323e-106">Cmdlet</span><span class="sxs-lookup"><span data-stu-id="c323e-106">Cmdlet</span></span>

<span data-ttu-id="c323e-107">Een .NET Framework-klasse identificeert als een cmdlet.</span><span class="sxs-lookup"><span data-stu-id="c323e-107">Identifies a .NET Framework class as a cmdlet.</span></span>
<span data-ttu-id="c323e-108">Dit is de vereiste base-kenmerk.</span><span class="sxs-lookup"><span data-stu-id="c323e-108">This is the required base attribute.</span></span>
<span data-ttu-id="c323e-109">Zie voor meer informatie, [Cmdlet kenmerkdeclaratie](./cmdlet-attribute-declaration.md).</span><span class="sxs-lookup"><span data-stu-id="c323e-109">For more information, see [Cmdlet Attribute Declaration](./cmdlet-attribute-declaration.md).</span></span>

## <a name="parameter-attributes"></a><span data-ttu-id="c323e-110">Parameterkenmerken</span><span class="sxs-lookup"><span data-stu-id="c323e-110">Parameter Attributes</span></span>

### <a name="parameter"></a><span data-ttu-id="c323e-111">Parameter</span><span class="sxs-lookup"><span data-stu-id="c323e-111">Parameter</span></span>

<span data-ttu-id="c323e-112">Een openbare eigenschap in de cmdlet-klasse wordt aangeduid als cmdlet-parameter.</span><span class="sxs-lookup"><span data-stu-id="c323e-112">Identifies a public property in the cmdlet class as a cmdlet parameter.</span></span>
<span data-ttu-id="c323e-113">Zie voor meer informatie, [kenmerk parameterdeclaratie](./parameter-attribute-declaration.md).</span><span class="sxs-lookup"><span data-stu-id="c323e-113">For more information, see [Parameter Attribute Declaration](./parameter-attribute-declaration.md).</span></span>

### <a name="alias"></a><span data-ttu-id="c323e-114">Alias</span><span class="sxs-lookup"><span data-stu-id="c323e-114">Alias</span></span>

<span data-ttu-id="c323e-115">Hiermee geeft u een of meer aliassen voor een parameter.</span><span class="sxs-lookup"><span data-stu-id="c323e-115">Specifies one or more aliases for a parameter.</span></span>
<span data-ttu-id="c323e-116">Zie voor meer informatie, [Alias kenmerkdeclaratie](./alias-attribute-declaration.md).</span><span class="sxs-lookup"><span data-stu-id="c323e-116">For more information, see [Alias Attribute Declaration](./alias-attribute-declaration.md).</span></span>

## <a name="argument-validation-attributes"></a><span data-ttu-id="c323e-117">Argument validatie kenmerken</span><span class="sxs-lookup"><span data-stu-id="c323e-117">Argument Validation Attributes</span></span>

### <a name="validatecount"></a><span data-ttu-id="c323e-118">ValidateCount</span><span class="sxs-lookup"><span data-stu-id="c323e-118">ValidateCount</span></span>

<span data-ttu-id="c323e-119">Hiermee geeft u het minimum en maximum aantal argumenten die zijn toegestaan voor een cmdlet-parameter.</span><span class="sxs-lookup"><span data-stu-id="c323e-119">Specifies the minimum and maximum number of arguments that are allowed for a cmdlet parameter.</span></span>
<span data-ttu-id="c323e-120">Zie voor meer informatie, [ValidateCount kenmerkdeclaratie](./validatecount-attribute-declaration.md).</span><span class="sxs-lookup"><span data-stu-id="c323e-120">For more information, see [ValidateCount Attribute Declaration](./validatecount-attribute-declaration.md).</span></span>

### <a name="validatelength"></a><span data-ttu-id="c323e-121">ValidateLength</span><span class="sxs-lookup"><span data-stu-id="c323e-121">ValidateLength</span></span>

<span data-ttu-id="c323e-122">Hiermee geeft u een minimum en maximum aantal tekens in voor een argument van de cmdlet-parameter.</span><span class="sxs-lookup"><span data-stu-id="c323e-122">Specifies a minimum and maximum number of characters for a cmdlet parameter argument.</span></span>
<span data-ttu-id="c323e-123">Zie voor meer informatie, [ValidateLength kenmerkdeclaratie](./validatelength-attribute-declaration.md).</span><span class="sxs-lookup"><span data-stu-id="c323e-123">For more information, see [ValidateLength Attribute Declaration](./validatelength-attribute-declaration.md).</span></span>

### <a name="validatepattern"></a><span data-ttu-id="c323e-124">ValidatePattern</span><span class="sxs-lookup"><span data-stu-id="c323e-124">ValidatePattern</span></span>

<span data-ttu-id="c323e-125">Hiermee geeft u een reguliere-expressiepatroon dat moet overeenkomen met het argument van de cmdlet-parameter.</span><span class="sxs-lookup"><span data-stu-id="c323e-125">Specifies a regular expression pattern that the cmdlet parameter argument must match.</span></span>
<span data-ttu-id="c323e-126">Zie voor meer informatie, [ValidatePattern kenmerkdeclaratie](./validatepattern-attribute-declaration.md).</span><span class="sxs-lookup"><span data-stu-id="c323e-126">For more information, see [ValidatePattern Attribute Declaration](./validatepattern-attribute-declaration.md).</span></span>

### <a name="validaterange"></a><span data-ttu-id="c323e-127">ValidateRange</span><span class="sxs-lookup"><span data-stu-id="c323e-127">ValidateRange</span></span>

<span data-ttu-id="c323e-128">Hiermee geeft u de minimale en maximale waarden voor een argument van de cmdlet-parameter.</span><span class="sxs-lookup"><span data-stu-id="c323e-128">Specifies the minimum and maximum values for a cmdlet parameter argument.</span></span>
<span data-ttu-id="c323e-129">Zie voor meer informatie, [ValidateRange kenmerkdeclaratie](./validaterange-attribute-declaration.md).</span><span class="sxs-lookup"><span data-stu-id="c323e-129">For more information, see [ValidateRange Attribute Declaration](./validaterange-attribute-declaration.md).</span></span>

### <a name="validateset"></a><span data-ttu-id="c323e-130">ValidateSet</span><span class="sxs-lookup"><span data-stu-id="c323e-130">ValidateSet</span></span>

<span data-ttu-id="c323e-131">Hiermee geeft u een set met geldige waarden voor het argument van de cmdlet-parameter.</span><span class="sxs-lookup"><span data-stu-id="c323e-131">Specifies a set of valid values for the cmdlet parameter argument.</span></span>
<span data-ttu-id="c323e-132">Zie voor meer informatie, [ValidateSet kenmerkdeclaratie](./validateset-attribute-declaration.md).</span><span class="sxs-lookup"><span data-stu-id="c323e-132">For more information, see [ValidateSet Attribute Declaration](./validateset-attribute-declaration.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="c323e-133">Zie ook</span><span class="sxs-lookup"><span data-stu-id="c323e-133">See Also</span></span>

[<span data-ttu-id="c323e-134">Windows PowerShell SDK</span><span class="sxs-lookup"><span data-stu-id="c323e-134">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)
