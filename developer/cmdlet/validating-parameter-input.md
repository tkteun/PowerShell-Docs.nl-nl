---
title: Valideren van de invoer van de Parameter | Microsoft Docs
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
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62067141"
---
# <a name="validating-parameter-input"></a><span data-ttu-id="eb3ac-102">Parameter-invoer valideren</span><span class="sxs-lookup"><span data-stu-id="eb3ac-102">Validating Parameter Input</span></span>

<span data-ttu-id="eb3ac-103">PowerShell kan de argumenten doorgegeven aan de cmdlet-parameters in verschillende manieren worden gevalideerd.</span><span class="sxs-lookup"><span data-stu-id="eb3ac-103">PowerShell can validate the arguments passed to cmdlet parameters in several ways.</span></span>
<span data-ttu-id="eb3ac-104">PowerShell kunt valideren de lengte van het bereik en het patroon van de tekens van het argument.</span><span class="sxs-lookup"><span data-stu-id="eb3ac-104">PowerShell can validate the length, the range, and the pattern of the characters of the argument.</span></span>
<span data-ttu-id="eb3ac-105">Dit kan het aantal argumenten beschikbaar (aantal) valideren.</span><span class="sxs-lookup"><span data-stu-id="eb3ac-105">It can validate the number of arguments available (the count).</span></span>
<span data-ttu-id="eb3ac-106">Deze validatieregels zijn gedefinieerd door validatie kenmerken die zijn gedeclareerd met de Parameter-kenmerk op openbare eigenschappen van de cmdlet-klasse.</span><span class="sxs-lookup"><span data-stu-id="eb3ac-106">These validation rules are defined by validation attributes that are declared with the Parameter attribute on public properties of the cmdlet class.</span></span>

<span data-ttu-id="eb3ac-107">Voor het valideren van een parameterargument gebruikt de PowerShell-runtime de informatie die is geleverd door de kenmerken van de validatie te bevestigen van de waarde van de parameter voordat de cmdlet wordt uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="eb3ac-107">To validate a parameter argument, the PowerShell runtime uses the information provided by the validation attributes to confirm the value of the parameter before the cmdlet is run.</span></span>
<span data-ttu-id="eb3ac-108">Als de parameter-invoer niet geldig is, ontvangt de gebruiker een foutbericht weergegeven.</span><span class="sxs-lookup"><span data-stu-id="eb3ac-108">If the parameter input is not valid, the user receives an error message.</span></span>
<span data-ttu-id="eb3ac-109">Elke parameter validatie definieert een regel voor het valideren die wordt afgedwongen door PowerShell.</span><span class="sxs-lookup"><span data-stu-id="eb3ac-109">Each validation parameter defines a validation rule that is enforced by PowerShell.</span></span>

<span data-ttu-id="eb3ac-110">PowerShell de validatieregels op basis van de volgende kenmerken afgedwongen.</span><span class="sxs-lookup"><span data-stu-id="eb3ac-110">PowerShell enforces the validation rules based on the following attributes.</span></span>

### <a name="validatecount"></a><span data-ttu-id="eb3ac-111">ValidateCount</span><span class="sxs-lookup"><span data-stu-id="eb3ac-111">ValidateCount</span></span>

<span data-ttu-id="eb3ac-112">Hiermee geeft u het minimum en maximum aantal argumenten dat een parameter kunt accepteren.</span><span class="sxs-lookup"><span data-stu-id="eb3ac-112">Specifies the minimum and maximum number of arguments that a parameter can accept.</span></span>
<span data-ttu-id="eb3ac-113">Zie voor meer informatie, [ValidateCount kenmerkdeclaratie](./validatecount-attribute-declaration.md).</span><span class="sxs-lookup"><span data-stu-id="eb3ac-113">For more information, see [ValidateCount Attribute Declaration](./validatecount-attribute-declaration.md).</span></span>

### <a name="validatelength"></a><span data-ttu-id="eb3ac-114">ValidateLength</span><span class="sxs-lookup"><span data-stu-id="eb3ac-114">ValidateLength</span></span>

<span data-ttu-id="eb3ac-115">Hiermee geeft u het minimum en maximum aantal tekens in de parameterargument.</span><span class="sxs-lookup"><span data-stu-id="eb3ac-115">Specifies the minimum and maximum number of characters in the parameter argument.</span></span>
<span data-ttu-id="eb3ac-116">Zie voor meer informatie, [ValidateLength kenmerkdeclaratie](./validatelength-attribute-declaration.md).</span><span class="sxs-lookup"><span data-stu-id="eb3ac-116">For more information, see [ValidateLength Attribute Declaration](./validatelength-attribute-declaration.md).</span></span>

### <a name="validatepattern"></a><span data-ttu-id="eb3ac-117">ValidatePattern</span><span class="sxs-lookup"><span data-stu-id="eb3ac-117">ValidatePattern</span></span>

<span data-ttu-id="eb3ac-118">Hiermee geeft u een reguliere expressie die het parameterargument valideert.</span><span class="sxs-lookup"><span data-stu-id="eb3ac-118">Specifies a regular expression that validates the parameter argument.</span></span>
<span data-ttu-id="eb3ac-119">Zie voor meer informatie, [ValidatePattern kenmerkdeclaratie](./validatepattern-attribute-declaration.md).</span><span class="sxs-lookup"><span data-stu-id="eb3ac-119">For more information, see [ValidatePattern Attribute Declaration](./validatepattern-attribute-declaration.md).</span></span>

### <a name="validaterange"></a><span data-ttu-id="eb3ac-120">ValidateRange</span><span class="sxs-lookup"><span data-stu-id="eb3ac-120">ValidateRange</span></span>

<span data-ttu-id="eb3ac-121">Hiermee geeft u de minimale en maximale waarden van de parameterargument.</span><span class="sxs-lookup"><span data-stu-id="eb3ac-121">Specifies the minimum and maximum values of the parameter argument.</span></span>
<span data-ttu-id="eb3ac-122">Zie voor meer informatie, [ValidateRange kenmerkdeclaratie](./validaterange-attribute-declaration.md).</span><span class="sxs-lookup"><span data-stu-id="eb3ac-122">For more information, see [ValidateRange Attribute Declaration](./validaterange-attribute-declaration.md).</span></span>

### <a name="validateset"></a><span data-ttu-id="eb3ac-123">ValidateSet</span><span class="sxs-lookup"><span data-stu-id="eb3ac-123">ValidateSet</span></span>

<span data-ttu-id="eb3ac-124">Hiermee geeft u de geldige waarden voor de parameterargument.</span><span class="sxs-lookup"><span data-stu-id="eb3ac-124">Specifies the valid values for the parameter argument.</span></span>
<span data-ttu-id="eb3ac-125">Zie voor meer informatie, [ValidateSet kenmerkdeclaratie](./validateset-attribute-declaration.md).</span><span class="sxs-lookup"><span data-stu-id="eb3ac-125">For more information, see [ValidateSet Attribute Declaration](./validateset-attribute-declaration.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="eb3ac-126">Zie ook</span><span class="sxs-lookup"><span data-stu-id="eb3ac-126">See Also</span></span>

[<span data-ttu-id="eb3ac-127">Het valideren van de Parameter-invoer</span><span class="sxs-lookup"><span data-stu-id="eb3ac-127">How to Validate Parameter Input</span></span>](./how-to-validate-parameter-input.md)

[<span data-ttu-id="eb3ac-128">Schrijven van een Windows PowerShell-Cmdlet</span><span class="sxs-lookup"><span data-stu-id="eb3ac-128">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
