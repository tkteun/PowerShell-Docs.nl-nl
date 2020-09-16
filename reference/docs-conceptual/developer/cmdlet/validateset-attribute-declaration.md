---
title: Verklaring van de kenmerkset validate | Microsoft Docs
ms.date: 09/13/2016
helpviewer_keywords:
- attributes, ValidateSet
- ValidateSet attribute, described
- ValidateSet attribute
ms.openlocfilehash: 0b6833efb0ce8e9474e9d91049fd201fc845cbea
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 08/05/2020
ms.locfileid: "87787764"
---
# <a name="validateset-attribute-declaration"></a><span data-ttu-id="699e5-102">Declaratie van het kenmerk ValidateSet</span><span class="sxs-lookup"><span data-stu-id="699e5-102">ValidateSet Attribute Declaration</span></span>

<span data-ttu-id="699e5-103">Het kenmerk ValidateSetAttribute bevat een reeks mogelijke waarden voor een argument van een cmdlet-para meter.</span><span class="sxs-lookup"><span data-stu-id="699e5-103">The ValidateSetAttribute attribute specifies a set of possible values for a cmdlet parameter argument.</span></span> <span data-ttu-id="699e5-104">Dit kenmerk kan ook worden gebruikt door Windows Power shell-functies.</span><span class="sxs-lookup"><span data-stu-id="699e5-104">This attribute can also be used by Windows PowerShell functions.</span></span>

<span data-ttu-id="699e5-105">Als dit kenmerk is opgegeven, bepaalt de Windows Power shell-runtime of het opgegeven argument voor de cmdlet-para meter overeenkomt met een element in de opgegeven verzameling van elementen.</span><span class="sxs-lookup"><span data-stu-id="699e5-105">When this attribute is specified, the Windows PowerShell runtime determines whether the supplied argument for the cmdlet parameter matches an element in the supplied element set.</span></span> <span data-ttu-id="699e5-106">De cmdlet wordt alleen uitgevoerd als het parameter argument overeenkomt met een element in de set.</span><span class="sxs-lookup"><span data-stu-id="699e5-106">The cmdlet is run only if the parameter argument matches an element in the set.</span></span> <span data-ttu-id="699e5-107">Als er geen overeenkomst wordt gevonden, wordt er een fout gegenereerd door de Windows Power shell-runtime.</span><span class="sxs-lookup"><span data-stu-id="699e5-107">If no match is found, an error is thrown by the Windows PowerShell runtime.</span></span>

## <a name="syntax"></a><span data-ttu-id="699e5-108">Syntaxis</span><span class="sxs-lookup"><span data-stu-id="699e5-108">Syntax</span></span>

```csharp
[ValidateSetAttribute(params string[] validValues)]
[ValidateSetAttribute(params string[] validValues, Named Parameters)]
```

#### <a name="parameters"></a><span data-ttu-id="699e5-109">Parameters</span><span class="sxs-lookup"><span data-stu-id="699e5-109">Parameters</span></span>

<span data-ttu-id="699e5-110">`ValidValues` ([System. String](/dotnet/api/System.String)) vereist.</span><span class="sxs-lookup"><span data-stu-id="699e5-110">`ValidValues` ([System.String](/dotnet/api/System.String)) Required.</span></span> <span data-ttu-id="699e5-111">Hiermee geeft u de geldige parameter element waarden op.</span><span class="sxs-lookup"><span data-stu-id="699e5-111">Specifies the valid parameter element values.</span></span> <span data-ttu-id="699e5-112">Het volgende voor beeld laat zien hoe u één element of meerdere elementen kunt opgeven.</span><span class="sxs-lookup"><span data-stu-id="699e5-112">The following sample shows how to specify one element or multiple elements.</span></span>

```csharp
[ValidateSetAttribute("Steve")]
[ValidateSetAttribute("Steve","Mary")]
```

<span data-ttu-id="699e5-113">`IgnoreCase` ([System. Boolean](/dotnet/api/System.Boolean)) een optionele benoemde para meter.</span><span class="sxs-lookup"><span data-stu-id="699e5-113">`IgnoreCase` ([System.Boolean](/dotnet/api/System.Boolean)) Optional named parameter.</span></span> <span data-ttu-id="699e5-114">De standaard waarde van `true` geeft aan dat de aanvraag wordt genegeerd.</span><span class="sxs-lookup"><span data-stu-id="699e5-114">The default value of `true` indicates that case is ignored.</span></span> <span data-ttu-id="699e5-115">De waarde van `false` de cmdlet is hoofdletter gevoelig.</span><span class="sxs-lookup"><span data-stu-id="699e5-115">A value of `false` makes the cmdlet case-sensitive.</span></span>

## <a name="remarks"></a><span data-ttu-id="699e5-116">Opmerkingen</span><span class="sxs-lookup"><span data-stu-id="699e5-116">Remarks</span></span>

- <span data-ttu-id="699e5-117">Dit kenmerk kan slechts eenmaal per para meter worden gebruikt.</span><span class="sxs-lookup"><span data-stu-id="699e5-117">This attribute can be used only once per parameter.</span></span>

- <span data-ttu-id="699e5-118">Als de parameter waarde een matrix is, moet elk element van de matrix overeenkomen met een element van de kenmerkset.</span><span class="sxs-lookup"><span data-stu-id="699e5-118">If the parameter value is an array, every element of the array must match an element of the attribute set.</span></span>

- <span data-ttu-id="699e5-119">Het kenmerk ValidateSetAttribute wordt gedefinieerd door de klasse [System. Management. Automation. ValidateSetAttribute](/dotnet/api/System.Management.Automation.ValidateSetAttribute) .</span><span class="sxs-lookup"><span data-stu-id="699e5-119">The ValidateSetAttribute attribute is defined by the [System.Management.Automation.Validatesetattribute](/dotnet/api/System.Management.Automation.ValidateSetAttribute) class.</span></span>

## <a name="see-also"></a><span data-ttu-id="699e5-120">Zie ook</span><span class="sxs-lookup"><span data-stu-id="699e5-120">See Also</span></span>

[<span data-ttu-id="699e5-121">System. Management. Automation. Validatesetattribute</span><span class="sxs-lookup"><span data-stu-id="699e5-121">System.Management.Automation.Validatesetattribute</span></span>](/dotnet/api/System.Management.Automation.ValidateSetAttribute)

[<span data-ttu-id="699e5-122">Een Windows PowerShell-cmdlet schrijven</span><span class="sxs-lookup"><span data-stu-id="699e5-122">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
