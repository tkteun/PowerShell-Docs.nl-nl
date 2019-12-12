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
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 12/05/2019
ms.locfileid: "72359143"
---
# <a name="validatepattern-attribute-declaration"></a><span data-ttu-id="b395d-102">Declaratie van het kenmerk ValidatePattern</span><span class="sxs-lookup"><span data-stu-id="b395d-102">ValidatePattern Attribute Declaration</span></span>

<span data-ttu-id="b395d-103">Het kenmerk ValidatePattern geeft een patroon van een reguliere expressie op waarmee het argument van een cmdlet-para meter wordt gevalideerd.</span><span class="sxs-lookup"><span data-stu-id="b395d-103">The ValidatePattern attribute specifies a regular expression pattern that validates the argument of a cmdlet parameter.</span></span> <span data-ttu-id="b395d-104">Dit kenmerk kan ook worden gebruikt door Windows Power shell-functies.</span><span class="sxs-lookup"><span data-stu-id="b395d-104">This attribute can also be used by Windows PowerShell functions.</span></span>

<span data-ttu-id="b395d-105">Wanneer ValidatePattern wordt aangeroepen binnen een cmdlet, converteert de Windows Power shell-runtime het argument van de cmdlet-para meter naar een teken reeks en vergelijkt die teken reeks met het patroon dat is opgegeven door het kenmerk ValidatePattern.</span><span class="sxs-lookup"><span data-stu-id="b395d-105">When ValidatePattern is invoked within a cmdlet, the Windows PowerShell runtime converts the argument of the cmdlet parameter to a string and then compares that string to the pattern supplied by the ValidatePattern attribute.</span></span> <span data-ttu-id="b395d-106">De cmdlet wordt alleen uitgevoerd als de geconverteerde teken reeks weergave van het argument en het opgegeven patroon overeenkomen.</span><span class="sxs-lookup"><span data-stu-id="b395d-106">The cmdlet is run only if the converted string representation of the argument and the supplied pattern match.</span></span> <span data-ttu-id="b395d-107">Als ze niet overeenkomen, wordt er een fout gegenereerd door de Windows Power shell-runtime.</span><span class="sxs-lookup"><span data-stu-id="b395d-107">If they do not match, an error is thrown by the Windows PowerShell runtime.</span></span>

## <a name="syntax"></a><span data-ttu-id="b395d-108">Syntaxis</span><span class="sxs-lookup"><span data-stu-id="b395d-108">Syntax</span></span>

```csharp
[ValidatePattern(string regexString)]
[ValidatePattern(string regexString, Named Parameters)]
```

#### <a name="parameters"></a><span data-ttu-id="b395d-109">Parameters</span><span class="sxs-lookup"><span data-stu-id="b395d-109">Parameters</span></span>

<span data-ttu-id="b395d-110">`RegexString` ([System. String](/dotnet/api/System.String)) vereist.</span><span class="sxs-lookup"><span data-stu-id="b395d-110">`RegexString` ([System.String](/dotnet/api/System.String)) Required.</span></span> <span data-ttu-id="b395d-111">Hiermee geeft u een reguliere expressie op waarmee het parameter argument wordt gevalideerd.</span><span class="sxs-lookup"><span data-stu-id="b395d-111">Specifies a regular expression that validates the parameter argument.</span></span>

<span data-ttu-id="b395d-112">Opties ([System. Text. RegularExpressions. Regexoptions](/dotnet/api/System.Text.RegularExpressions.RegexOptions)) een optionele benoemde para meter.</span><span class="sxs-lookup"><span data-stu-id="b395d-112">Options ([System.Text.Regularexpressions.Regexoptions](/dotnet/api/System.Text.RegularExpressions.RegexOptions)) Optional named parameter.</span></span> <span data-ttu-id="b395d-113">Hiermee geeft u een bitsgewijze combi natie van [System. Text. RegularExpressions. Regexoptions](/dotnet/api/System.Text.RegularExpressions.RegexOptions) -vlaggen op waarmee opties voor reguliere expressies worden opgegeven.</span><span class="sxs-lookup"><span data-stu-id="b395d-113">Specifies a bitwise combination of [System.Text.Regularexpressions.Regexoptions](/dotnet/api/System.Text.RegularExpressions.RegexOptions) flags that specify regular expression options.</span></span>

## <a name="remarks"></a><span data-ttu-id="b395d-114">Opmerkingen</span><span class="sxs-lookup"><span data-stu-id="b395d-114">Remarks</span></span>

- <span data-ttu-id="b395d-115">Dit kenmerk kan slechts eenmaal per para meter worden gebruikt.</span><span class="sxs-lookup"><span data-stu-id="b395d-115">This attribute can be used only once per parameter.</span></span>

- <span data-ttu-id="b395d-116">U kunt de para meter `Option` van het kenmerk gebruiken om het patroon verder te definiëren.</span><span class="sxs-lookup"><span data-stu-id="b395d-116">You can use the `Option` parameter of the attribute to further define the pattern.</span></span> <span data-ttu-id="b395d-117">U kunt bijvoorbeeld het patroon hoofdletter gevoelig maken.</span><span class="sxs-lookup"><span data-stu-id="b395d-117">For example, you can make the pattern case sensitive.</span></span>

- <span data-ttu-id="b395d-118">Als dit kenmerk wordt toegepast op een verzameling, moet elk element in de verzameling overeenkomen met het patroon.</span><span class="sxs-lookup"><span data-stu-id="b395d-118">If this attribute is applied to a collection, each element in the collection must match the pattern.</span></span>

- <span data-ttu-id="b395d-119">Het kenmerk ValidatePattern wordt gedefinieerd door de klasse [System. Management. Automation. Validatepatternattribute](/dotnet/api/System.Management.Automation.ValidatePatternAttribute) .</span><span class="sxs-lookup"><span data-stu-id="b395d-119">The ValidatePattern attribute is defined by the [System.Management.Automation.Validatepatternattribute](/dotnet/api/System.Management.Automation.ValidatePatternAttribute) class.</span></span>

## <a name="see-also"></a><span data-ttu-id="b395d-120">Zie ook</span><span class="sxs-lookup"><span data-stu-id="b395d-120">See Also</span></span>

[<span data-ttu-id="b395d-121">System. Management. Automation. Validatepatternattribute</span><span class="sxs-lookup"><span data-stu-id="b395d-121">System.Management.Automation.Validatepatternattribute</span></span>](/dotnet/api/System.Management.Automation.ValidatePatternAttribute)

[<span data-ttu-id="b395d-122">Een Windows Power shell-cmdlet schrijven</span><span class="sxs-lookup"><span data-stu-id="b395d-122">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
