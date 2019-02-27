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
ms.openlocfilehash: f7e5d4fb2f89bd6bc7036fdcff8f38e017d5d0e4
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 02/03/2019
ms.locfileid: "56848802"
---
# <a name="validating-parameter-input"></a><span data-ttu-id="956ba-102">Parameter-invoer valideren</span><span class="sxs-lookup"><span data-stu-id="956ba-102">Validating Parameter Input</span></span>

<span data-ttu-id="956ba-103">Windows PowerShell kunnen de argumenten doorgegeven aan de cmdlet-parameters in verschillende manieren worden gevalideerd.</span><span class="sxs-lookup"><span data-stu-id="956ba-103">Windows PowerShell can validate the arguments passed to cmdlet parameters in several ways.</span></span> <span data-ttu-id="956ba-104">Windows PowerShell kunt valideren de lengte van het bereik en het patroon van de tekens van het argument.</span><span class="sxs-lookup"><span data-stu-id="956ba-104">Windows PowerShell can validate the length, the range, and the pattern of the characters of the argument.</span></span> <span data-ttu-id="956ba-105">Dit kan het aantal argumenten beschikbaar (aantal) valideren.</span><span class="sxs-lookup"><span data-stu-id="956ba-105">It can validate the number of arguments available (the count).</span></span> <span data-ttu-id="956ba-106">Deze validatieregels zijn gedefinieerd door validatie kenmerken die zijn gedeclareerd met de Parameter-kenmerk op openbare eigenschappen van de cmdlet-klasse.</span><span class="sxs-lookup"><span data-stu-id="956ba-106">These validation rules are defined by validation attributes that are declared with the Parameter attribute on public properties of the cmdlet class.</span></span>

<span data-ttu-id="956ba-107">Voor het valideren van een parameterargument gebruikt de Windows PowerShell-runtime de informatie die is geleverd door de kenmerken van de validatie te bevestigen van de waarde van de parameter voordat de cmdlet wordt uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="956ba-107">To validate a parameter argument, the Windows PowerShell runtime uses the information provided by the validation attributes to confirm the value of the parameter before the cmdlet is run.</span></span> <span data-ttu-id="956ba-108">Als de parameter-invoer niet geldig is, ontvangt de gebruiker een foutbericht weergegeven.</span><span class="sxs-lookup"><span data-stu-id="956ba-108">If the parameter input is not valid, the user receives an error message.</span></span> <span data-ttu-id="956ba-109">Elke parameter validatie definieert een regel voor het valideren die door Windows PowerShell wordt afgedwongen.</span><span class="sxs-lookup"><span data-stu-id="956ba-109">Each validation parameter defines a validation rule that is enforced by Windows PowerShell.</span></span>

<span data-ttu-id="956ba-110">Windows PowerShell de validatieregels op basis van de volgende kenmerken afgedwongen.</span><span class="sxs-lookup"><span data-stu-id="956ba-110">Windows PowerShell enforces the validation rules based on the following attributes.</span></span>

<span data-ttu-id="956ba-111">ValidateCount Hiermee geeft u het minimum en maximum aantal argumenten dat een parameter kunt accepteren.</span><span class="sxs-lookup"><span data-stu-id="956ba-111">ValidateCount Specifies the minimum and maximum number of arguments that a parameter can accept.</span></span> <span data-ttu-id="956ba-112">Zie voor meer informatie over de syntaxis die is gebruikt om te declareren van dit kenmerk [ValidateCount kenmerkdeclaratie](./validatecount-attribute-declaration.md).</span><span class="sxs-lookup"><span data-stu-id="956ba-112">For more information about the syntax used to declare this attribute, see [ValidateCount Attribute Declaration](./validatecount-attribute-declaration.md).</span></span>

<span data-ttu-id="956ba-113">ValidateLength Hiermee geeft u het minimum en maximum aantal tekens in de parameterargument.</span><span class="sxs-lookup"><span data-stu-id="956ba-113">ValidateLength Specifies the minimum and maximum number of characters in the parameter argument.</span></span> <span data-ttu-id="956ba-114">Zie voor meer informatie over de syntaxis die is gebruikt om te declareren van dit kenmerk [ValidateLength kenmerkdeclaratie](./validatelength-attribute-declaration.md).</span><span class="sxs-lookup"><span data-stu-id="956ba-114">For more information about the syntax used to declare this attribute, see [ValidateLength Attribute Declaration](./validatelength-attribute-declaration.md).</span></span>

<span data-ttu-id="956ba-115">ValidatePattern Hiermee geeft u een reguliere expressie die het parameterargument valideert.</span><span class="sxs-lookup"><span data-stu-id="956ba-115">ValidatePattern Specifies a regular expression that validates the parameter argument.</span></span> <span data-ttu-id="956ba-116">Zie voor meer informatie over de syntaxis die is gebruikt om te declareren van dit kenmerk [ValidatePattern kenmerkdeclaratie](./validatepattern-attribute-declaration.md).</span><span class="sxs-lookup"><span data-stu-id="956ba-116">For more information about the syntax used to declare this attribute, see [ValidatePattern Attribute Declaration](./validatepattern-attribute-declaration.md).</span></span>

<span data-ttu-id="956ba-117">ValidateRange Hiermee geeft u de minimale en maximale waarden van de parameterargument.</span><span class="sxs-lookup"><span data-stu-id="956ba-117">ValidateRange Specifies the minimum and maximum values of the parameter argument.</span></span> <span data-ttu-id="956ba-118">Zie voor meer informatie over de syntaxis die is gebruikt om te declareren van dit kenmerk [ValidateRange kenmerkdeclaratie](./validaterange-attribute-declaration.md).</span><span class="sxs-lookup"><span data-stu-id="956ba-118">For more information about the syntax used to declare this attribute, see [ValidateRange Attribute Declaration](./validaterange-attribute-declaration.md).</span></span>

<span data-ttu-id="956ba-119">ValidateSet Hiermee geeft u de geldige waarden voor de parameterargument.</span><span class="sxs-lookup"><span data-stu-id="956ba-119">ValidateSet Specifies the valid values for the parameter argument.</span></span> <span data-ttu-id="956ba-120">Zie voor meer informatie over de syntaxis die is gebruikt om te declareren van dit kenmerk [ValidateSet kenmerkdeclaratie](./validateset-attribute-declaration.md).</span><span class="sxs-lookup"><span data-stu-id="956ba-120">For more information about the syntax used to declare this attribute, see [ValidateSet Attribute Declaration](./validateset-attribute-declaration.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="956ba-121">Zie ook</span><span class="sxs-lookup"><span data-stu-id="956ba-121">See Also</span></span>

[<span data-ttu-id="956ba-122">Het valideren van de Parameter-invoer</span><span class="sxs-lookup"><span data-stu-id="956ba-122">How to Validate Parameter Input</span></span>](./how-to-validate-parameter-input.md)

[<span data-ttu-id="956ba-123">Schrijven van een Windows PowerShell-Cmdlet</span><span class="sxs-lookup"><span data-stu-id="956ba-123">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
