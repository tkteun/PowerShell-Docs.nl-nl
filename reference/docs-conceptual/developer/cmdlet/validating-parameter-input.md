---
ms.date: 09/13/2016
ms.topic: reference
title: Parameter-invoer valideren
description: Parameter-invoer valideren
ms.openlocfilehash: a97b5c670e8c36463a85bbef1506f6311bdd5ec3
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 12/10/2020
ms.locfileid: "92660394"
---
# <a name="validating-parameter-input"></a><span data-ttu-id="02c75-103">Parameter-invoer valideren</span><span class="sxs-lookup"><span data-stu-id="02c75-103">Validating Parameter Input</span></span>

<span data-ttu-id="02c75-104">Power shell kan de argumenten die zijn door gegeven aan cmdlet-para meters op verschillende manieren valideren.</span><span class="sxs-lookup"><span data-stu-id="02c75-104">PowerShell can validate the arguments passed to cmdlet parameters in several ways.</span></span>
<span data-ttu-id="02c75-105">In Power shell kunnen de lengte, het bereik en het patroon van de tekens van het argument worden gevalideerd.</span><span class="sxs-lookup"><span data-stu-id="02c75-105">PowerShell can validate the length, the range, and the pattern of the characters of the argument.</span></span>
<span data-ttu-id="02c75-106">Hiermee kan het aantal beschik bare argumenten (de telling) worden gevalideerd.</span><span class="sxs-lookup"><span data-stu-id="02c75-106">It can validate the number of arguments available (the count).</span></span>
<span data-ttu-id="02c75-107">Deze validatie regels worden gedefinieerd door validatie kenmerken die zijn gedeclareerd met het parameter kenmerk voor open bare eigenschappen van de cmdlet-klasse.</span><span class="sxs-lookup"><span data-stu-id="02c75-107">These validation rules are defined by validation attributes that are declared with the Parameter attribute on public properties of the cmdlet class.</span></span>

<span data-ttu-id="02c75-108">Voor het valideren van een parameter argument gebruikt Power shell runtime de informatie die door de validatie kenmerken wordt verstrekt om de waarde van de para meter te bevestigen voordat de cmdlet wordt uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="02c75-108">To validate a parameter argument, the PowerShell runtime uses the information provided by the validation attributes to confirm the value of the parameter before the cmdlet is run.</span></span>
<span data-ttu-id="02c75-109">Als de invoer van de para meter niet geldig is, ontvangt de gebruiker een fout bericht.</span><span class="sxs-lookup"><span data-stu-id="02c75-109">If the parameter input is not valid, the user receives an error message.</span></span>
<span data-ttu-id="02c75-110">Elke validatie parameter definieert een validatie regel die door Power shell wordt afgedwongen.</span><span class="sxs-lookup"><span data-stu-id="02c75-110">Each validation parameter defines a validation rule that is enforced by PowerShell.</span></span>

<span data-ttu-id="02c75-111">Power shell dwingt de validatie regels af op basis van de volgende kenmerken.</span><span class="sxs-lookup"><span data-stu-id="02c75-111">PowerShell enforces the validation rules based on the following attributes.</span></span>

### <a name="validatecount"></a><span data-ttu-id="02c75-112">ValidateCount</span><span class="sxs-lookup"><span data-stu-id="02c75-112">ValidateCount</span></span>

<span data-ttu-id="02c75-113">Hiermee geeft u het minimum en maximum aantal argumenten op dat door een para meter kan worden geaccepteerd.</span><span class="sxs-lookup"><span data-stu-id="02c75-113">Specifies the minimum and maximum number of arguments that a parameter can accept.</span></span>
<span data-ttu-id="02c75-114">Zie [ValidateCount kenmerk declaratie](./validatecount-attribute-declaration.md)(Engelstalig) voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="02c75-114">For more information, see [ValidateCount Attribute Declaration](./validatecount-attribute-declaration.md).</span></span>

### <a name="validatelength"></a><span data-ttu-id="02c75-115">ValidateLength</span><span class="sxs-lookup"><span data-stu-id="02c75-115">ValidateLength</span></span>

<span data-ttu-id="02c75-116">Hiermee geeft u het minimum en maximum aantal tekens in het parameter argument op.</span><span class="sxs-lookup"><span data-stu-id="02c75-116">Specifies the minimum and maximum number of characters in the parameter argument.</span></span>
<span data-ttu-id="02c75-117">Zie [ValidateLength kenmerk declaratie](./validatelength-attribute-declaration.md)(Engelstalig) voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="02c75-117">For more information, see [ValidateLength Attribute Declaration](./validatelength-attribute-declaration.md).</span></span>

### <a name="validatepattern"></a><span data-ttu-id="02c75-118">ValidatePattern</span><span class="sxs-lookup"><span data-stu-id="02c75-118">ValidatePattern</span></span>

<span data-ttu-id="02c75-119">Hiermee geeft u een reguliere expressie op waarmee het parameter argument wordt gevalideerd.</span><span class="sxs-lookup"><span data-stu-id="02c75-119">Specifies a regular expression that validates the parameter argument.</span></span>
<span data-ttu-id="02c75-120">Zie [ValidatePattern kenmerk declaratie](./validatepattern-attribute-declaration.md)(Engelstalig) voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="02c75-120">For more information, see [ValidatePattern Attribute Declaration](./validatepattern-attribute-declaration.md).</span></span>

### <a name="validaterange"></a><span data-ttu-id="02c75-121">ValidateRange</span><span class="sxs-lookup"><span data-stu-id="02c75-121">ValidateRange</span></span>

<span data-ttu-id="02c75-122">Hiermee geeft u de minimum-en maximum waarden van het parameter argument op.</span><span class="sxs-lookup"><span data-stu-id="02c75-122">Specifies the minimum and maximum values of the parameter argument.</span></span>
<span data-ttu-id="02c75-123">Zie [ValidateRange kenmerk declaratie](./validaterange-attribute-declaration.md)(Engelstalig) voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="02c75-123">For more information, see [ValidateRange Attribute Declaration](./validaterange-attribute-declaration.md).</span></span>

### <a name="validateset"></a><span data-ttu-id="02c75-124">Validatieset</span><span class="sxs-lookup"><span data-stu-id="02c75-124">ValidateSet</span></span>

<span data-ttu-id="02c75-125">Hiermee geeft u de geldige waarden voor het parameter argument op.</span><span class="sxs-lookup"><span data-stu-id="02c75-125">Specifies the valid values for the parameter argument.</span></span>
<span data-ttu-id="02c75-126">Zie [Validate kenmerk Declaration](./validateset-attribute-declaration.md)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="02c75-126">For more information, see [ValidateSet Attribute Declaration](./validateset-attribute-declaration.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="02c75-127">Zie ook</span><span class="sxs-lookup"><span data-stu-id="02c75-127">See Also</span></span>

[<span data-ttu-id="02c75-128">Parameterinvoer valideren</span><span class="sxs-lookup"><span data-stu-id="02c75-128">How to Validate Parameter Input</span></span>](./how-to-validate-parameter-input.md)

[<span data-ttu-id="02c75-129">Een Windows PowerShell-cmdlet schrijven</span><span class="sxs-lookup"><span data-stu-id="02c75-129">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
