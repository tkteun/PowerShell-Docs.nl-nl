---
title: Verklaring van de kenmerkset validate | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- attributes, ValidateSet
- ValidateSet attribute, described
- ValidateSet attribute
ms.assetid: 4a6f97ab-45b2-4f3d-84d4-30acf8e074d0
caps.latest.revision: 12
ms.openlocfilehash: b036f39cd01ffe4b4ce7db9627cb6da0d5327190
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 12/05/2019
ms.locfileid: "72355417"
---
# <a name="validateset-attribute-declaration"></a><span data-ttu-id="b9a98-102">Declaratie van het kenmerk ValidateSet</span><span class="sxs-lookup"><span data-stu-id="b9a98-102">ValidateSet Attribute Declaration</span></span>

<span data-ttu-id="b9a98-103">Het kenmerk ValidateSetAttribute bevat een reeks mogelijke waarden voor een argument van een cmdlet-para meter.</span><span class="sxs-lookup"><span data-stu-id="b9a98-103">The ValidateSetAttribute attribute specifies a set of possible values for a cmdlet parameter argument.</span></span> <span data-ttu-id="b9a98-104">Dit kenmerk kan ook worden gebruikt door Windows Power shell-functies.</span><span class="sxs-lookup"><span data-stu-id="b9a98-104">This attribute can also be used by Windows PowerShell functions.</span></span>

<span data-ttu-id="b9a98-105">Als dit kenmerk is opgegeven, bepaalt de Windows Power shell-runtime of het opgegeven argument voor de cmdlet-para meter overeenkomt met een element in de opgegeven verzameling van elementen.</span><span class="sxs-lookup"><span data-stu-id="b9a98-105">When this attribute is specified, the Windows PowerShell runtime determines whether the supplied argument for the cmdlet parameter matches an element in the supplied element set.</span></span> <span data-ttu-id="b9a98-106">De cmdlet wordt alleen uitgevoerd als het parameter argument overeenkomt met een element in de set.</span><span class="sxs-lookup"><span data-stu-id="b9a98-106">The cmdlet is run only if the parameter argument matches an element in the set.</span></span> <span data-ttu-id="b9a98-107">Als er geen overeenkomst wordt gevonden, wordt er een fout gegenereerd door de Windows Power shell-runtime.</span><span class="sxs-lookup"><span data-stu-id="b9a98-107">If no match is found, an error is thrown by the Windows PowerShell runtime.</span></span>

## <a name="syntax"></a><span data-ttu-id="b9a98-108">Syntaxis</span><span class="sxs-lookup"><span data-stu-id="b9a98-108">Syntax</span></span>

```csharp
[ValidateSetAttribute(params string[] validValues)]
[ValidateSetAttribute(params string[] validValues, Named Parameters)]
```

#### <a name="parameters"></a><span data-ttu-id="b9a98-109">Parameters</span><span class="sxs-lookup"><span data-stu-id="b9a98-109">Parameters</span></span>

<span data-ttu-id="b9a98-110">`ValidValues` ([System. String](/dotnet/api/System.String)) vereist.</span><span class="sxs-lookup"><span data-stu-id="b9a98-110">`ValidValues` ([System.String](/dotnet/api/System.String)) Required.</span></span> <span data-ttu-id="b9a98-111">Hiermee geeft u de geldige parameter element waarden op.</span><span class="sxs-lookup"><span data-stu-id="b9a98-111">Specifies the valid parameter element values.</span></span> <span data-ttu-id="b9a98-112">Het volgende voor beeld laat zien hoe u één element of meerdere elementen kunt opgeven.</span><span class="sxs-lookup"><span data-stu-id="b9a98-112">The following sample shows how to specify one element or multiple elements.</span></span>

```csharp
[ValidateSetAttribute("Steve")]
[ValidateSetAttribute("Steve","Mary")]
```

<span data-ttu-id="b9a98-113">`IgnoreCase` ([System. Boolean](/dotnet/api/System.Boolean)) een optionele benoemde para meter.</span><span class="sxs-lookup"><span data-stu-id="b9a98-113">`IgnoreCase` ([System.Boolean](/dotnet/api/System.Boolean)) Optional named parameter.</span></span> <span data-ttu-id="b9a98-114">De standaard waarde van `true` geeft aan dat het geval wordt genegeerd.</span><span class="sxs-lookup"><span data-stu-id="b9a98-114">The default value of `true` indicates that case is ignored.</span></span> <span data-ttu-id="b9a98-115">Met een waarde van `false` wordt de cmdlet hoofdletter gevoelig gemaakt.</span><span class="sxs-lookup"><span data-stu-id="b9a98-115">A value of `false` makes the cmdlet case-sensitive.</span></span>

## <a name="remarks"></a><span data-ttu-id="b9a98-116">Opmerkingen</span><span class="sxs-lookup"><span data-stu-id="b9a98-116">Remarks</span></span>

- <span data-ttu-id="b9a98-117">Dit kenmerk kan slechts eenmaal per para meter worden gebruikt.</span><span class="sxs-lookup"><span data-stu-id="b9a98-117">This attribute can be used only once per parameter.</span></span>

- <span data-ttu-id="b9a98-118">Als de parameter waarde een matrix is, moet elk element van de matrix overeenkomen met een element van de kenmerkset.</span><span class="sxs-lookup"><span data-stu-id="b9a98-118">If the parameter value is an array, every element of the array must match an element of the attribute set.</span></span>

- <span data-ttu-id="b9a98-119">Het kenmerk ValidateSetAttribute wordt gedefinieerd door de klasse [System. Management. Automation. ValidateSetAttribute](/dotnet/api/System.Management.Automation.ValidateSetAttribute) .</span><span class="sxs-lookup"><span data-stu-id="b9a98-119">The ValidateSetAttribute attribute is defined by the [System.Management.Automation.Validatesetattribute](/dotnet/api/System.Management.Automation.ValidateSetAttribute) class.</span></span>

## <a name="see-also"></a><span data-ttu-id="b9a98-120">Zie ook</span><span class="sxs-lookup"><span data-stu-id="b9a98-120">See Also</span></span>

[<span data-ttu-id="b9a98-121">System. Management. Automation. Validatesetattribute</span><span class="sxs-lookup"><span data-stu-id="b9a98-121">System.Management.Automation.Validatesetattribute</span></span>](/dotnet/api/System.Management.Automation.ValidateSetAttribute)

[<span data-ttu-id="b9a98-122">Een Windows Power shell-cmdlet schrijven</span><span class="sxs-lookup"><span data-stu-id="b9a98-122">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
