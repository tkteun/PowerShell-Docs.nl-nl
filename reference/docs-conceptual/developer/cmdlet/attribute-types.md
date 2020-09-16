---
title: Kenmerk typen | Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: 96fdd38ba10eb748ab0762f0c910463dd472494d
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 08/05/2020
ms.locfileid: "87782375"
---
# <a name="attribute-types"></a><span data-ttu-id="d1afa-102">Typen kenmerken</span><span class="sxs-lookup"><span data-stu-id="d1afa-102">Attribute Types</span></span>

<span data-ttu-id="d1afa-103">Cmdlet-kenmerken kunnen worden gegroepeerd op functionaliteit.</span><span class="sxs-lookup"><span data-stu-id="d1afa-103">Cmdlet attributes can be grouped by functionality.</span></span>
<span data-ttu-id="d1afa-104">In de volgende secties worden de beschik bare kenmerken beschreven en wordt beschreven wat de runtime doet wanneer het kenmerk wordt aangeroepen.</span><span class="sxs-lookup"><span data-stu-id="d1afa-104">The following sections describe the available attributes and describe what the runtime does when the attribute is invoked.</span></span>

## <a name="cmdlet-attributes"></a><span data-ttu-id="d1afa-105">Cmdlet-kenmerken</span><span class="sxs-lookup"><span data-stu-id="d1afa-105">Cmdlet Attributes</span></span>

### <a name="cmdlet"></a><span data-ttu-id="d1afa-106">Cmdlet</span><span class="sxs-lookup"><span data-stu-id="d1afa-106">Cmdlet</span></span>

<span data-ttu-id="d1afa-107">Identificeert een .NET Framework klasse als een cmdlet.</span><span class="sxs-lookup"><span data-stu-id="d1afa-107">Identifies a .NET Framework class as a cmdlet.</span></span>
<span data-ttu-id="d1afa-108">Dit is het vereiste basis kenmerk.</span><span class="sxs-lookup"><span data-stu-id="d1afa-108">This is the required base attribute.</span></span>
<span data-ttu-id="d1afa-109">Zie voor meer informatie de [cmdlet-kenmerk declaratie](./cmdlet-attribute-declaration.md).</span><span class="sxs-lookup"><span data-stu-id="d1afa-109">For more information, see [Cmdlet Attribute Declaration](./cmdlet-attribute-declaration.md).</span></span>

## <a name="parameter-attributes"></a><span data-ttu-id="d1afa-110">Parameter kenmerken</span><span class="sxs-lookup"><span data-stu-id="d1afa-110">Parameter Attributes</span></span>

### <a name="parameter"></a><span data-ttu-id="d1afa-111">Parameter</span><span class="sxs-lookup"><span data-stu-id="d1afa-111">Parameter</span></span>

<span data-ttu-id="d1afa-112">Identificeert een open bare eigenschap in de cmdlet-klasse als een cmdlet-para meter.</span><span class="sxs-lookup"><span data-stu-id="d1afa-112">Identifies a public property in the cmdlet class as a cmdlet parameter.</span></span>
<span data-ttu-id="d1afa-113">Zie [para meter kenmerk declaratie](./parameter-attribute-declaration.md)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="d1afa-113">For more information, see [Parameter Attribute Declaration](./parameter-attribute-declaration.md).</span></span>

### <a name="alias"></a><span data-ttu-id="d1afa-114">Alias</span><span class="sxs-lookup"><span data-stu-id="d1afa-114">Alias</span></span>

<span data-ttu-id="d1afa-115">Hiermee geeft u een of meer aliassen voor een para meter.</span><span class="sxs-lookup"><span data-stu-id="d1afa-115">Specifies one or more aliases for a parameter.</span></span>
<span data-ttu-id="d1afa-116">Zie [alias kenmerk declaratie](./alias-attribute-declaration.md)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="d1afa-116">For more information, see [Alias Attribute Declaration](./alias-attribute-declaration.md).</span></span>

## <a name="argument-validation-attributes"></a><span data-ttu-id="d1afa-117">Argument validatie kenmerken</span><span class="sxs-lookup"><span data-stu-id="d1afa-117">Argument Validation Attributes</span></span>

### <a name="validatecount"></a><span data-ttu-id="d1afa-118">ValidateCount</span><span class="sxs-lookup"><span data-stu-id="d1afa-118">ValidateCount</span></span>

<span data-ttu-id="d1afa-119">Hiermee geeft u het minimum en maximum aantal argumenten op dat is toegestaan voor een cmdlet-para meter.</span><span class="sxs-lookup"><span data-stu-id="d1afa-119">Specifies the minimum and maximum number of arguments that are allowed for a cmdlet parameter.</span></span>
<span data-ttu-id="d1afa-120">Zie [ValidateCount kenmerk declaratie](./validatecount-attribute-declaration.md)(Engelstalig) voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="d1afa-120">For more information, see [ValidateCount Attribute Declaration](./validatecount-attribute-declaration.md).</span></span>

### <a name="validatelength"></a><span data-ttu-id="d1afa-121">ValidateLength</span><span class="sxs-lookup"><span data-stu-id="d1afa-121">ValidateLength</span></span>

<span data-ttu-id="d1afa-122">Hiermee geeft u een minimum en maximum aantal tekens op voor een argument van een cmdlet-para meter.</span><span class="sxs-lookup"><span data-stu-id="d1afa-122">Specifies a minimum and maximum number of characters for a cmdlet parameter argument.</span></span>
<span data-ttu-id="d1afa-123">Zie [ValidateLength kenmerk declaratie](./validatelength-attribute-declaration.md)(Engelstalig) voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="d1afa-123">For more information, see [ValidateLength Attribute Declaration](./validatelength-attribute-declaration.md).</span></span>

### <a name="validatepattern"></a><span data-ttu-id="d1afa-124">ValidatePattern</span><span class="sxs-lookup"><span data-stu-id="d1afa-124">ValidatePattern</span></span>

<span data-ttu-id="d1afa-125">Hiermee geeft u een patroon van een reguliere expressie op dat het argument van de cmdlet-para meter moet overeenkomen.</span><span class="sxs-lookup"><span data-stu-id="d1afa-125">Specifies a regular expression pattern that the cmdlet parameter argument must match.</span></span>
<span data-ttu-id="d1afa-126">Zie [ValidatePattern kenmerk declaratie](./validatepattern-attribute-declaration.md)(Engelstalig) voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="d1afa-126">For more information, see [ValidatePattern Attribute Declaration](./validatepattern-attribute-declaration.md).</span></span>

### <a name="validaterange"></a><span data-ttu-id="d1afa-127">ValidateRange</span><span class="sxs-lookup"><span data-stu-id="d1afa-127">ValidateRange</span></span>

<span data-ttu-id="d1afa-128">Hiermee geeft u de minimum-en maximum waarde op voor een argument van een cmdlet-para meter.</span><span class="sxs-lookup"><span data-stu-id="d1afa-128">Specifies the minimum and maximum values for a cmdlet parameter argument.</span></span>
<span data-ttu-id="d1afa-129">Zie [ValidateRange kenmerk declaratie](./validaterange-attribute-declaration.md)(Engelstalig) voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="d1afa-129">For more information, see [ValidateRange Attribute Declaration](./validaterange-attribute-declaration.md).</span></span>

### <a name="validateset"></a><span data-ttu-id="d1afa-130">Validatieset</span><span class="sxs-lookup"><span data-stu-id="d1afa-130">ValidateSet</span></span>

<span data-ttu-id="d1afa-131">Hiermee geeft u een set geldige waarden op voor het argument van de cmdlet-para meter.</span><span class="sxs-lookup"><span data-stu-id="d1afa-131">Specifies a set of valid values for the cmdlet parameter argument.</span></span>
<span data-ttu-id="d1afa-132">Zie [Validate kenmerk Declaration](./validateset-attribute-declaration.md)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="d1afa-132">For more information, see [ValidateSet Attribute Declaration](./validateset-attribute-declaration.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="d1afa-133">Zie ook</span><span class="sxs-lookup"><span data-stu-id="d1afa-133">See Also</span></span>

[<span data-ttu-id="d1afa-134">Windows PowerShell SDK</span><span class="sxs-lookup"><span data-stu-id="d1afa-134">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)
