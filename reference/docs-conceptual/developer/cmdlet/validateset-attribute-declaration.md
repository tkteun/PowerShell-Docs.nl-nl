---
ms.date: 09/13/2016
ms.topic: reference
title: Declaratie van het kenmerk ValidateSet
description: Declaratie van het kenmerk ValidateSet
ms.openlocfilehash: 7894d00561366ada492911e8147acbd8d3454a55
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/27/2020
ms.locfileid: "92660470"
---
# <a name="validateset-attribute-declaration"></a><span data-ttu-id="f6665-103">Declaratie van het kenmerk ValidateSet</span><span class="sxs-lookup"><span data-stu-id="f6665-103">ValidateSet Attribute Declaration</span></span>

<span data-ttu-id="f6665-104">Het kenmerk ValidateSetAttribute bevat een reeks mogelijke waarden voor een argument van een cmdlet-para meter.</span><span class="sxs-lookup"><span data-stu-id="f6665-104">The ValidateSetAttribute attribute specifies a set of possible values for a cmdlet parameter argument.</span></span> <span data-ttu-id="f6665-105">Dit kenmerk kan ook worden gebruikt door Windows Power shell-functies.</span><span class="sxs-lookup"><span data-stu-id="f6665-105">This attribute can also be used by Windows PowerShell functions.</span></span>

<span data-ttu-id="f6665-106">Als dit kenmerk is opgegeven, bepaalt de Windows Power shell-runtime of het opgegeven argument voor de cmdlet-para meter overeenkomt met een element in de opgegeven verzameling van elementen.</span><span class="sxs-lookup"><span data-stu-id="f6665-106">When this attribute is specified, the Windows PowerShell runtime determines whether the supplied argument for the cmdlet parameter matches an element in the supplied element set.</span></span> <span data-ttu-id="f6665-107">De cmdlet wordt alleen uitgevoerd als het parameter argument overeenkomt met een element in de set.</span><span class="sxs-lookup"><span data-stu-id="f6665-107">The cmdlet is run only if the parameter argument matches an element in the set.</span></span> <span data-ttu-id="f6665-108">Als er geen overeenkomst wordt gevonden, wordt er een fout gegenereerd door de Windows Power shell-runtime.</span><span class="sxs-lookup"><span data-stu-id="f6665-108">If no match is found, an error is thrown by the Windows PowerShell runtime.</span></span>

## <a name="syntax"></a><span data-ttu-id="f6665-109">Syntaxis</span><span class="sxs-lookup"><span data-stu-id="f6665-109">Syntax</span></span>

```csharp
[ValidateSetAttribute(params string[] validValues)]
[ValidateSetAttribute(params string[] validValues, Named Parameters)]
```

#### <a name="parameters"></a><span data-ttu-id="f6665-110">Parameters</span><span class="sxs-lookup"><span data-stu-id="f6665-110">Parameters</span></span>

<span data-ttu-id="f6665-111">`ValidValues` ([System. String](/dotnet/api/System.String)) vereist.</span><span class="sxs-lookup"><span data-stu-id="f6665-111">`ValidValues` ([System.String](/dotnet/api/System.String)) Required.</span></span> <span data-ttu-id="f6665-112">Hiermee geeft u de geldige parameter element waarden op.</span><span class="sxs-lookup"><span data-stu-id="f6665-112">Specifies the valid parameter element values.</span></span> <span data-ttu-id="f6665-113">Het volgende voor beeld laat zien hoe u één element of meerdere elementen kunt opgeven.</span><span class="sxs-lookup"><span data-stu-id="f6665-113">The following sample shows how to specify one element or multiple elements.</span></span>

```csharp
[ValidateSetAttribute("Steve")]
[ValidateSetAttribute("Steve","Mary")]
```

<span data-ttu-id="f6665-114">`IgnoreCase` ([System. Boolean](/dotnet/api/System.Boolean)) een optionele benoemde para meter.</span><span class="sxs-lookup"><span data-stu-id="f6665-114">`IgnoreCase` ([System.Boolean](/dotnet/api/System.Boolean)) Optional named parameter.</span></span> <span data-ttu-id="f6665-115">De standaard waarde van `true` geeft aan dat de aanvraag wordt genegeerd.</span><span class="sxs-lookup"><span data-stu-id="f6665-115">The default value of `true` indicates that case is ignored.</span></span> <span data-ttu-id="f6665-116">De waarde van `false` de cmdlet is hoofdletter gevoelig.</span><span class="sxs-lookup"><span data-stu-id="f6665-116">A value of `false` makes the cmdlet case-sensitive.</span></span>

## <a name="remarks"></a><span data-ttu-id="f6665-117">Opmerkingen</span><span class="sxs-lookup"><span data-stu-id="f6665-117">Remarks</span></span>

- <span data-ttu-id="f6665-118">Dit kenmerk kan slechts eenmaal per para meter worden gebruikt.</span><span class="sxs-lookup"><span data-stu-id="f6665-118">This attribute can be used only once per parameter.</span></span>

- <span data-ttu-id="f6665-119">Als de parameter waarde een matrix is, moet elk element van de matrix overeenkomen met een element van de kenmerkset.</span><span class="sxs-lookup"><span data-stu-id="f6665-119">If the parameter value is an array, every element of the array must match an element of the attribute set.</span></span>

- <span data-ttu-id="f6665-120">Het kenmerk ValidateSetAttribute wordt gedefinieerd door de klasse [System. Management. Automation. ValidateSetAttribute](/dotnet/api/System.Management.Automation.ValidateSetAttribute) .</span><span class="sxs-lookup"><span data-stu-id="f6665-120">The ValidateSetAttribute attribute is defined by the [System.Management.Automation.Validatesetattribute](/dotnet/api/System.Management.Automation.ValidateSetAttribute) class.</span></span>

## <a name="see-also"></a><span data-ttu-id="f6665-121">Zie ook</span><span class="sxs-lookup"><span data-stu-id="f6665-121">See Also</span></span>

[<span data-ttu-id="f6665-122">System. Management. Automation. Validatesetattribute</span><span class="sxs-lookup"><span data-stu-id="f6665-122">System.Management.Automation.Validatesetattribute</span></span>](/dotnet/api/System.Management.Automation.ValidateSetAttribute)

[<span data-ttu-id="f6665-123">Een Windows PowerShell-cmdlet schrijven</span><span class="sxs-lookup"><span data-stu-id="f6665-123">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
