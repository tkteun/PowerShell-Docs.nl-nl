---
ms.date: 09/13/2016
ms.topic: reference
title: Declaratie van het kenmerk ValidatePattern
description: Declaratie van het kenmerk ValidatePattern
ms.openlocfilehash: 364f63d2c52563eaefe64bcbb2bbae511bccb074
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/27/2020
ms.locfileid: "92646163"
---
# <a name="validatepattern-attribute-declaration"></a><span data-ttu-id="8faf2-103">Declaratie van het kenmerk ValidatePattern</span><span class="sxs-lookup"><span data-stu-id="8faf2-103">ValidatePattern Attribute Declaration</span></span>

<span data-ttu-id="8faf2-104">Het kenmerk ValidatePattern geeft een patroon van een reguliere expressie op waarmee het argument van een cmdlet-para meter wordt gevalideerd.</span><span class="sxs-lookup"><span data-stu-id="8faf2-104">The ValidatePattern attribute specifies a regular expression pattern that validates the argument of a cmdlet parameter.</span></span> <span data-ttu-id="8faf2-105">Dit kenmerk kan ook worden gebruikt door Windows Power shell-functies.</span><span class="sxs-lookup"><span data-stu-id="8faf2-105">This attribute can also be used by Windows PowerShell functions.</span></span>

<span data-ttu-id="8faf2-106">Wanneer ValidatePattern wordt aangeroepen binnen een cmdlet, converteert de Windows Power shell-runtime het argument van de cmdlet-para meter naar een teken reeks en vergelijkt die teken reeks met het patroon dat is opgegeven door het kenmerk ValidatePattern.</span><span class="sxs-lookup"><span data-stu-id="8faf2-106">When ValidatePattern is invoked within a cmdlet, the Windows PowerShell runtime converts the argument of the cmdlet parameter to a string and then compares that string to the pattern supplied by the ValidatePattern attribute.</span></span> <span data-ttu-id="8faf2-107">De cmdlet wordt alleen uitgevoerd als de geconverteerde teken reeks weergave van het argument en het opgegeven patroon overeenkomen.</span><span class="sxs-lookup"><span data-stu-id="8faf2-107">The cmdlet is run only if the converted string representation of the argument and the supplied pattern match.</span></span> <span data-ttu-id="8faf2-108">Als ze niet overeenkomen, wordt er een fout gegenereerd door de Windows Power shell-runtime.</span><span class="sxs-lookup"><span data-stu-id="8faf2-108">If they do not match, an error is thrown by the Windows PowerShell runtime.</span></span>

## <a name="syntax"></a><span data-ttu-id="8faf2-109">Syntaxis</span><span class="sxs-lookup"><span data-stu-id="8faf2-109">Syntax</span></span>

```csharp
[ValidatePattern(string regexString)]
[ValidatePattern(string regexString, Named Parameters)]
```

#### <a name="parameters"></a><span data-ttu-id="8faf2-110">Parameters</span><span class="sxs-lookup"><span data-stu-id="8faf2-110">Parameters</span></span>

<span data-ttu-id="8faf2-111">`RegexString` ([System. String](/dotnet/api/System.String)) vereist.</span><span class="sxs-lookup"><span data-stu-id="8faf2-111">`RegexString` ([System.String](/dotnet/api/System.String)) Required.</span></span> <span data-ttu-id="8faf2-112">Hiermee geeft u een reguliere expressie op waarmee het parameter argument wordt gevalideerd.</span><span class="sxs-lookup"><span data-stu-id="8faf2-112">Specifies a regular expression that validates the parameter argument.</span></span>

<span data-ttu-id="8faf2-113">Opties ([System. Text. RegularExpressions. Regexoptions](/dotnet/api/System.Text.RegularExpressions.RegexOptions)) een optionele benoemde para meter.</span><span class="sxs-lookup"><span data-stu-id="8faf2-113">Options ([System.Text.Regularexpressions.Regexoptions](/dotnet/api/System.Text.RegularExpressions.RegexOptions)) Optional named parameter.</span></span> <span data-ttu-id="8faf2-114">Hiermee geeft u een bitsgewijze combi natie van [System. Text. RegularExpressions. Regexoptions](/dotnet/api/System.Text.RegularExpressions.RegexOptions) -vlaggen op waarmee opties voor reguliere expressies worden opgegeven.</span><span class="sxs-lookup"><span data-stu-id="8faf2-114">Specifies a bitwise combination of [System.Text.Regularexpressions.Regexoptions](/dotnet/api/System.Text.RegularExpressions.RegexOptions) flags that specify regular expression options.</span></span>

## <a name="remarks"></a><span data-ttu-id="8faf2-115">Opmerkingen</span><span class="sxs-lookup"><span data-stu-id="8faf2-115">Remarks</span></span>

- <span data-ttu-id="8faf2-116">Dit kenmerk kan slechts eenmaal per para meter worden gebruikt.</span><span class="sxs-lookup"><span data-stu-id="8faf2-116">This attribute can be used only once per parameter.</span></span>

- <span data-ttu-id="8faf2-117">U kunt de `Option` para meter van het kenmerk gebruiken om het patroon verder te definiëren.</span><span class="sxs-lookup"><span data-stu-id="8faf2-117">You can use the `Option` parameter of the attribute to further define the pattern.</span></span> <span data-ttu-id="8faf2-118">U kunt bijvoorbeeld het patroon hoofdletter gevoelig maken.</span><span class="sxs-lookup"><span data-stu-id="8faf2-118">For example, you can make the pattern case sensitive.</span></span>

- <span data-ttu-id="8faf2-119">Als dit kenmerk wordt toegepast op een verzameling, moet elk element in de verzameling overeenkomen met het patroon.</span><span class="sxs-lookup"><span data-stu-id="8faf2-119">If this attribute is applied to a collection, each element in the collection must match the pattern.</span></span>

- <span data-ttu-id="8faf2-120">Het kenmerk ValidatePattern wordt gedefinieerd door de klasse [System. Management. Automation. Validatepatternattribute](/dotnet/api/System.Management.Automation.ValidatePatternAttribute) .</span><span class="sxs-lookup"><span data-stu-id="8faf2-120">The ValidatePattern attribute is defined by the [System.Management.Automation.Validatepatternattribute](/dotnet/api/System.Management.Automation.ValidatePatternAttribute) class.</span></span>

## <a name="see-also"></a><span data-ttu-id="8faf2-121">Zie ook</span><span class="sxs-lookup"><span data-stu-id="8faf2-121">See Also</span></span>

[<span data-ttu-id="8faf2-122">System. Management. Automation. Validatepatternattribute</span><span class="sxs-lookup"><span data-stu-id="8faf2-122">System.Management.Automation.Validatepatternattribute</span></span>](/dotnet/api/System.Management.Automation.ValidatePatternAttribute)

[<span data-ttu-id="8faf2-123">Een Windows PowerShell-cmdlet schrijven</span><span class="sxs-lookup"><span data-stu-id="8faf2-123">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
