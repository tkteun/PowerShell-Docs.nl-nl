---
title: Parameter invoer valideren | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- parameters, validation rules
- validation, examples
- validation
ms.assetid: 3f15bf20-a068-4a7d-a170-bc43f755d1fe
caps.latest.revision: 14
ms.openlocfilehash: 171e3e974619e197a0bcc9dfc759297005e34568
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/15/2019
ms.locfileid: "72354878"
---
# <a name="validating-parameter-input"></a><span data-ttu-id="30ed5-102">Parameter-invoer valideren</span><span class="sxs-lookup"><span data-stu-id="30ed5-102">Validating Parameter Input</span></span>

<span data-ttu-id="30ed5-103">Power shell kan de argumenten die zijn door gegeven aan cmdlet-para meters op verschillende manieren valideren.</span><span class="sxs-lookup"><span data-stu-id="30ed5-103">PowerShell can validate the arguments passed to cmdlet parameters in several ways.</span></span>
<span data-ttu-id="30ed5-104">In Power shell kunnen de lengte, het bereik en het patroon van de tekens van het argument worden gevalideerd.</span><span class="sxs-lookup"><span data-stu-id="30ed5-104">PowerShell can validate the length, the range, and the pattern of the characters of the argument.</span></span>
<span data-ttu-id="30ed5-105">Hiermee kan het aantal beschik bare argumenten (de telling) worden gevalideerd.</span><span class="sxs-lookup"><span data-stu-id="30ed5-105">It can validate the number of arguments available (the count).</span></span>
<span data-ttu-id="30ed5-106">Deze validatie regels worden gedefinieerd door validatie kenmerken die zijn gedeclareerd met het parameter kenmerk voor open bare eigenschappen van de cmdlet-klasse.</span><span class="sxs-lookup"><span data-stu-id="30ed5-106">These validation rules are defined by validation attributes that are declared with the Parameter attribute on public properties of the cmdlet class.</span></span>

<span data-ttu-id="30ed5-107">Voor het valideren van een parameter argument gebruikt Power shell runtime de informatie die door de validatie kenmerken wordt verstrekt om de waarde van de para meter te bevestigen voordat de cmdlet wordt uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="30ed5-107">To validate a parameter argument, the PowerShell runtime uses the information provided by the validation attributes to confirm the value of the parameter before the cmdlet is run.</span></span>
<span data-ttu-id="30ed5-108">Als de invoer van de para meter niet geldig is, ontvangt de gebruiker een fout bericht.</span><span class="sxs-lookup"><span data-stu-id="30ed5-108">If the parameter input is not valid, the user receives an error message.</span></span>
<span data-ttu-id="30ed5-109">Elke validatie parameter definieert een validatie regel die door Power shell wordt afgedwongen.</span><span class="sxs-lookup"><span data-stu-id="30ed5-109">Each validation parameter defines a validation rule that is enforced by PowerShell.</span></span>

<span data-ttu-id="30ed5-110">Power shell dwingt de validatie regels af op basis van de volgende kenmerken.</span><span class="sxs-lookup"><span data-stu-id="30ed5-110">PowerShell enforces the validation rules based on the following attributes.</span></span>

### <a name="validatecount"></a><span data-ttu-id="30ed5-111">ValidateCount</span><span class="sxs-lookup"><span data-stu-id="30ed5-111">ValidateCount</span></span>

<span data-ttu-id="30ed5-112">Hiermee geeft u het minimum en maximum aantal argumenten op dat door een para meter kan worden geaccepteerd.</span><span class="sxs-lookup"><span data-stu-id="30ed5-112">Specifies the minimum and maximum number of arguments that a parameter can accept.</span></span>
<span data-ttu-id="30ed5-113">Zie [ValidateCount kenmerk declaratie](./validatecount-attribute-declaration.md)(Engelstalig) voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="30ed5-113">For more information, see [ValidateCount Attribute Declaration](./validatecount-attribute-declaration.md).</span></span>

### <a name="validatelength"></a><span data-ttu-id="30ed5-114">ValidateLength</span><span class="sxs-lookup"><span data-stu-id="30ed5-114">ValidateLength</span></span>

<span data-ttu-id="30ed5-115">Hiermee geeft u het minimum en maximum aantal tekens in het parameter argument op.</span><span class="sxs-lookup"><span data-stu-id="30ed5-115">Specifies the minimum and maximum number of characters in the parameter argument.</span></span>
<span data-ttu-id="30ed5-116">Zie [ValidateLength kenmerk declaratie](./validatelength-attribute-declaration.md)(Engelstalig) voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="30ed5-116">For more information, see [ValidateLength Attribute Declaration](./validatelength-attribute-declaration.md).</span></span>

### <a name="validatepattern"></a><span data-ttu-id="30ed5-117">ValidatePattern</span><span class="sxs-lookup"><span data-stu-id="30ed5-117">ValidatePattern</span></span>

<span data-ttu-id="30ed5-118">Hiermee geeft u een reguliere expressie op waarmee het parameter argument wordt gevalideerd.</span><span class="sxs-lookup"><span data-stu-id="30ed5-118">Specifies a regular expression that validates the parameter argument.</span></span>
<span data-ttu-id="30ed5-119">Zie [ValidatePattern kenmerk declaratie](./validatepattern-attribute-declaration.md)(Engelstalig) voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="30ed5-119">For more information, see [ValidatePattern Attribute Declaration](./validatepattern-attribute-declaration.md).</span></span>

### <a name="validaterange"></a><span data-ttu-id="30ed5-120">ValidateRange</span><span class="sxs-lookup"><span data-stu-id="30ed5-120">ValidateRange</span></span>

<span data-ttu-id="30ed5-121">Hiermee geeft u de minimum-en maximum waarden van het parameter argument op.</span><span class="sxs-lookup"><span data-stu-id="30ed5-121">Specifies the minimum and maximum values of the parameter argument.</span></span>
<span data-ttu-id="30ed5-122">Zie [ValidateRange kenmerk declaratie](./validaterange-attribute-declaration.md)(Engelstalig) voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="30ed5-122">For more information, see [ValidateRange Attribute Declaration](./validaterange-attribute-declaration.md).</span></span>

### <a name="validateset"></a><span data-ttu-id="30ed5-123">Validatieset</span><span class="sxs-lookup"><span data-stu-id="30ed5-123">ValidateSet</span></span>

<span data-ttu-id="30ed5-124">Hiermee geeft u de geldige waarden voor het parameter argument op.</span><span class="sxs-lookup"><span data-stu-id="30ed5-124">Specifies the valid values for the parameter argument.</span></span>
<span data-ttu-id="30ed5-125">Zie [Validate kenmerk Declaration](./validateset-attribute-declaration.md)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="30ed5-125">For more information, see [ValidateSet Attribute Declaration](./validateset-attribute-declaration.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="30ed5-126">Zie ook</span><span class="sxs-lookup"><span data-stu-id="30ed5-126">See Also</span></span>

[<span data-ttu-id="30ed5-127">Parameter invoer valideren</span><span class="sxs-lookup"><span data-stu-id="30ed5-127">How to Validate Parameter Input</span></span>](./how-to-validate-parameter-input.md)

[<span data-ttu-id="30ed5-128">Een Windows Power shell-cmdlet schrijven</span><span class="sxs-lookup"><span data-stu-id="30ed5-128">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
