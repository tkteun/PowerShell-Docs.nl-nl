---
ms.date: 09/13/2016
ms.topic: reference
title: Typen kenmerken
description: Typen kenmerken
ms.openlocfilehash: 65640f2f8449887dedb9fae137eb16b6252f1d57
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/27/2020
ms.locfileid: "92667110"
---
# <a name="attribute-types"></a><span data-ttu-id="79f43-103">Typen kenmerken</span><span class="sxs-lookup"><span data-stu-id="79f43-103">Attribute Types</span></span>

<span data-ttu-id="79f43-104">Cmdlet-kenmerken kunnen worden gegroepeerd op functionaliteit.</span><span class="sxs-lookup"><span data-stu-id="79f43-104">Cmdlet attributes can be grouped by functionality.</span></span>
<span data-ttu-id="79f43-105">In de volgende secties worden de beschik bare kenmerken beschreven en wordt beschreven wat de runtime doet wanneer het kenmerk wordt aangeroepen.</span><span class="sxs-lookup"><span data-stu-id="79f43-105">The following sections describe the available attributes and describe what the runtime does when the attribute is invoked.</span></span>

## <a name="cmdlet-attributes"></a><span data-ttu-id="79f43-106">Cmdlet-kenmerken</span><span class="sxs-lookup"><span data-stu-id="79f43-106">Cmdlet Attributes</span></span>

### <a name="cmdlet"></a><span data-ttu-id="79f43-107">Cmdlet</span><span class="sxs-lookup"><span data-stu-id="79f43-107">Cmdlet</span></span>

<span data-ttu-id="79f43-108">Identificeert een .NET Framework klasse als een cmdlet.</span><span class="sxs-lookup"><span data-stu-id="79f43-108">Identifies a .NET Framework class as a cmdlet.</span></span>
<span data-ttu-id="79f43-109">Dit is het vereiste basis kenmerk.</span><span class="sxs-lookup"><span data-stu-id="79f43-109">This is the required base attribute.</span></span>
<span data-ttu-id="79f43-110">Zie voor meer informatie de [cmdlet-kenmerk declaratie](./cmdlet-attribute-declaration.md).</span><span class="sxs-lookup"><span data-stu-id="79f43-110">For more information, see [Cmdlet Attribute Declaration](./cmdlet-attribute-declaration.md).</span></span>

## <a name="parameter-attributes"></a><span data-ttu-id="79f43-111">Parameter kenmerken</span><span class="sxs-lookup"><span data-stu-id="79f43-111">Parameter Attributes</span></span>

### <a name="parameter"></a><span data-ttu-id="79f43-112">Parameter</span><span class="sxs-lookup"><span data-stu-id="79f43-112">Parameter</span></span>

<span data-ttu-id="79f43-113">Identificeert een open bare eigenschap in de cmdlet-klasse als een cmdlet-para meter.</span><span class="sxs-lookup"><span data-stu-id="79f43-113">Identifies a public property in the cmdlet class as a cmdlet parameter.</span></span>
<span data-ttu-id="79f43-114">Zie [para meter kenmerk declaratie](./parameter-attribute-declaration.md)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="79f43-114">For more information, see [Parameter Attribute Declaration](./parameter-attribute-declaration.md).</span></span>

### <a name="alias"></a><span data-ttu-id="79f43-115">Alias</span><span class="sxs-lookup"><span data-stu-id="79f43-115">Alias</span></span>

<span data-ttu-id="79f43-116">Hiermee geeft u een of meer aliassen voor een para meter.</span><span class="sxs-lookup"><span data-stu-id="79f43-116">Specifies one or more aliases for a parameter.</span></span>
<span data-ttu-id="79f43-117">Zie [alias kenmerk declaratie](./alias-attribute-declaration.md)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="79f43-117">For more information, see [Alias Attribute Declaration](./alias-attribute-declaration.md).</span></span>

## <a name="argument-validation-attributes"></a><span data-ttu-id="79f43-118">Argument validatie kenmerken</span><span class="sxs-lookup"><span data-stu-id="79f43-118">Argument Validation Attributes</span></span>

### <a name="validatecount"></a><span data-ttu-id="79f43-119">ValidateCount</span><span class="sxs-lookup"><span data-stu-id="79f43-119">ValidateCount</span></span>

<span data-ttu-id="79f43-120">Hiermee geeft u het minimum en maximum aantal argumenten op dat is toegestaan voor een cmdlet-para meter.</span><span class="sxs-lookup"><span data-stu-id="79f43-120">Specifies the minimum and maximum number of arguments that are allowed for a cmdlet parameter.</span></span>
<span data-ttu-id="79f43-121">Zie [ValidateCount kenmerk declaratie](./validatecount-attribute-declaration.md)(Engelstalig) voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="79f43-121">For more information, see [ValidateCount Attribute Declaration](./validatecount-attribute-declaration.md).</span></span>

### <a name="validatelength"></a><span data-ttu-id="79f43-122">ValidateLength</span><span class="sxs-lookup"><span data-stu-id="79f43-122">ValidateLength</span></span>

<span data-ttu-id="79f43-123">Hiermee geeft u een minimum en maximum aantal tekens op voor een argument van een cmdlet-para meter.</span><span class="sxs-lookup"><span data-stu-id="79f43-123">Specifies a minimum and maximum number of characters for a cmdlet parameter argument.</span></span>
<span data-ttu-id="79f43-124">Zie [ValidateLength kenmerk declaratie](./validatelength-attribute-declaration.md)(Engelstalig) voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="79f43-124">For more information, see [ValidateLength Attribute Declaration](./validatelength-attribute-declaration.md).</span></span>

### <a name="validatepattern"></a><span data-ttu-id="79f43-125">ValidatePattern</span><span class="sxs-lookup"><span data-stu-id="79f43-125">ValidatePattern</span></span>

<span data-ttu-id="79f43-126">Hiermee geeft u een patroon van een reguliere expressie op dat het argument van de cmdlet-para meter moet overeenkomen.</span><span class="sxs-lookup"><span data-stu-id="79f43-126">Specifies a regular expression pattern that the cmdlet parameter argument must match.</span></span>
<span data-ttu-id="79f43-127">Zie [ValidatePattern kenmerk declaratie](./validatepattern-attribute-declaration.md)(Engelstalig) voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="79f43-127">For more information, see [ValidatePattern Attribute Declaration](./validatepattern-attribute-declaration.md).</span></span>

### <a name="validaterange"></a><span data-ttu-id="79f43-128">ValidateRange</span><span class="sxs-lookup"><span data-stu-id="79f43-128">ValidateRange</span></span>

<span data-ttu-id="79f43-129">Hiermee geeft u de minimum-en maximum waarde op voor een argument van een cmdlet-para meter.</span><span class="sxs-lookup"><span data-stu-id="79f43-129">Specifies the minimum and maximum values for a cmdlet parameter argument.</span></span>
<span data-ttu-id="79f43-130">Zie [ValidateRange kenmerk declaratie](./validaterange-attribute-declaration.md)(Engelstalig) voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="79f43-130">For more information, see [ValidateRange Attribute Declaration](./validaterange-attribute-declaration.md).</span></span>

### <a name="validateset"></a><span data-ttu-id="79f43-131">Validatieset</span><span class="sxs-lookup"><span data-stu-id="79f43-131">ValidateSet</span></span>

<span data-ttu-id="79f43-132">Hiermee geeft u een set geldige waarden op voor het argument van de cmdlet-para meter.</span><span class="sxs-lookup"><span data-stu-id="79f43-132">Specifies a set of valid values for the cmdlet parameter argument.</span></span>
<span data-ttu-id="79f43-133">Zie [Validate kenmerk Declaration](./validateset-attribute-declaration.md)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="79f43-133">For more information, see [ValidateSet Attribute Declaration](./validateset-attribute-declaration.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="79f43-134">Zie ook</span><span class="sxs-lookup"><span data-stu-id="79f43-134">See Also</span></span>

[<span data-ttu-id="79f43-135">Windows PowerShell SDK</span><span class="sxs-lookup"><span data-stu-id="79f43-135">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)
