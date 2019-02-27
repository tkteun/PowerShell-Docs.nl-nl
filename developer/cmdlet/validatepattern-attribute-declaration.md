---
title: ValidatePattern kenmerk declaratie | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- attributes, ValidatePattern
- ValidatePattern attribute, described
- ValidatePattern attribute
ms.assetid: 87b811be-6d93-4e7d-b9d0-c567a19bb0ef
caps.latest.revision: 13
ms.openlocfilehash: 5edcb65a6fbe1cb2fe2d0efe3f763fb84628b049
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 02/03/2019
ms.locfileid: "56848823"
---
# <a name="validatepattern-attribute-declaration"></a><span data-ttu-id="ede0d-102">Declaratie van het kenmerk ValidatePattern</span><span class="sxs-lookup"><span data-stu-id="ede0d-102">ValidatePattern Attribute Declaration</span></span>

<span data-ttu-id="ede0d-103">Het kenmerk ValidatePattern Hiermee geeft u een reguliere-expressiepatroon dat het argument van een cmdlet-parameter worden gevalideerd.</span><span class="sxs-lookup"><span data-stu-id="ede0d-103">The ValidatePattern attribute specifies a regular expression pattern that validates the argument of a cmdlet parameter.</span></span> <span data-ttu-id="ede0d-104">Dit kenmerk kan ook worden gebruikt door Windows PowerShell-functies.</span><span class="sxs-lookup"><span data-stu-id="ede0d-104">This attribute can also be used by Windows PowerShell functions.</span></span>

<span data-ttu-id="ede0d-105">Wanneer ValidatePattern wordt opgeroepen binnen een cmdlet, wordt de Windows PowerShell-runtime wordt het argument van de cmdlet-parameter geconverteerd naar een tekenreeks en vergelijkt vervolgens die tekenreeks met het patroon dat is opgegeven door het kenmerk ValidatePattern.</span><span class="sxs-lookup"><span data-stu-id="ede0d-105">When ValidatePattern is invoked within a cmdlet, the Windows PowerShell runtime converts the argument of the cmdlet parameter to a string and then compares that string to the pattern supplied by the ValidatePattern attribute.</span></span> <span data-ttu-id="ede0d-106">De cmdlet wordt uitgevoerd alleen als de geconverteerde tekenreeksweergave van het argument en het opgegeven patroon voldoen aan.</span><span class="sxs-lookup"><span data-stu-id="ede0d-106">The cmdlet is run only if the converted string representation of the argument and the supplied pattern match.</span></span> <span data-ttu-id="ede0d-107">Als ze niet overeenkomen, wordt er door de Windows PowerShell-runtime een fout gegenereerd.</span><span class="sxs-lookup"><span data-stu-id="ede0d-107">If they do not match, an error is thrown by the Windows PowerShell runtime.</span></span>

## <a name="syntax"></a><span data-ttu-id="ede0d-108">Syntaxis</span><span class="sxs-lookup"><span data-stu-id="ede0d-108">Syntax</span></span>

```csharp
[ValidatePattern(string regexString)]
[ValidatePattern(string regexString, Named Parameters)]
```

#### <a name="parameters"></a><span data-ttu-id="ede0d-109">Parameters</span><span class="sxs-lookup"><span data-stu-id="ede0d-109">Parameters</span></span>

<span data-ttu-id="ede0d-110">`RegexString` ([System.String](/dotnet/api/System.String)) vereist.</span><span class="sxs-lookup"><span data-stu-id="ede0d-110">`RegexString` ([System.String](/dotnet/api/System.String)) Required.</span></span> <span data-ttu-id="ede0d-111">Hiermee geeft u een reguliere expressie die het parameterargument valideert.</span><span class="sxs-lookup"><span data-stu-id="ede0d-111">Specifies a regular expression that validates the parameter argument.</span></span>

<span data-ttu-id="ede0d-112">Opties ([System.Text.Regularexpressions.Regexoptions](/dotnet/api/System.Text.RegularExpressions.RegexOptions)) met de naam van parameter optioneel.</span><span class="sxs-lookup"><span data-stu-id="ede0d-112">Options ([System.Text.Regularexpressions.Regexoptions](/dotnet/api/System.Text.RegularExpressions.RegexOptions)) Optional named parameter.</span></span> <span data-ttu-id="ede0d-113">Hiermee geeft u een bitsgewijze combinatie van [System.Text.Regularexpressions.Regexoptions](/dotnet/api/System.Text.RegularExpressions.RegexOptions) vlaggen die reguliere expressie opgeven.</span><span class="sxs-lookup"><span data-stu-id="ede0d-113">Specifies a bitwise combination of [System.Text.Regularexpressions.Regexoptions](/dotnet/api/System.Text.RegularExpressions.RegexOptions) flags that specify regular expression options.</span></span>

## <a name="remarks"></a><span data-ttu-id="ede0d-114">Opmerkingen</span><span class="sxs-lookup"><span data-stu-id="ede0d-114">Remarks</span></span>

- <span data-ttu-id="ede0d-115">Dit kenmerk kan slechts één keer per parameter worden gebruikt.</span><span class="sxs-lookup"><span data-stu-id="ede0d-115">This attribute can be used only once per parameter.</span></span>

- <span data-ttu-id="ede0d-116">U kunt de `Option` parameter van het kenmerk om verder te definiëren het patroon.</span><span class="sxs-lookup"><span data-stu-id="ede0d-116">You can use the `Option` parameter of the attribute to further define the pattern.</span></span> <span data-ttu-id="ede0d-117">Bijvoorbeeld, kunt u het patroon hoofdlettergevoelig.</span><span class="sxs-lookup"><span data-stu-id="ede0d-117">For example, you can make the pattern case sensitive.</span></span>

- <span data-ttu-id="ede0d-118">Als dit kenmerk wordt toegepast op een verzameling, heeft elk element in de verzameling moet overeenkomen met het patroon.</span><span class="sxs-lookup"><span data-stu-id="ede0d-118">If this attribute is applied to a collection, each element in the collection must match the pattern.</span></span>

- <span data-ttu-id="ede0d-119">Het kenmerk ValidatePattern wordt gedefinieerd door de [System.Management.Automation.Validatepatternattribute](/dotnet/api/System.Management.Automation.ValidatePatternAttribute) klasse.</span><span class="sxs-lookup"><span data-stu-id="ede0d-119">The ValidatePattern attribute is defined by the [System.Management.Automation.Validatepatternattribute](/dotnet/api/System.Management.Automation.ValidatePatternAttribute) class.</span></span>

## <a name="see-also"></a><span data-ttu-id="ede0d-120">Zie ook</span><span class="sxs-lookup"><span data-stu-id="ede0d-120">See Also</span></span>

[<span data-ttu-id="ede0d-121">System.Management.Automation.Validatepatternattribute</span><span class="sxs-lookup"><span data-stu-id="ede0d-121">System.Management.Automation.Validatepatternattribute</span></span>](/dotnet/api/System.Management.Automation.ValidatePatternAttribute)

[<span data-ttu-id="ede0d-122">Schrijven van een Windows PowerShell-Cmdlet</span><span class="sxs-lookup"><span data-stu-id="ede0d-122">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
