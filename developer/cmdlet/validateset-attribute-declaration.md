---
title: ValidateSet kenmerk declaratie | Microsoft Docs
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
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 02/03/2019
ms.locfileid: "56850454"
---
# <a name="validateset-attribute-declaration"></a><span data-ttu-id="29105-102">Declaratie van het kenmerk ValidateSet</span><span class="sxs-lookup"><span data-stu-id="29105-102">ValidateSet Attribute Declaration</span></span>

<span data-ttu-id="29105-103">Het kenmerk ValidateSetAttribute geeft een reeks van mogelijke waarden voor een argument van de cmdlet-parameter.</span><span class="sxs-lookup"><span data-stu-id="29105-103">The ValidateSetAttribute attribute specifies a set of possible values for a cmdlet parameter argument.</span></span> <span data-ttu-id="29105-104">Dit kenmerk kan ook worden gebruikt door Windows PowerShell-functies.</span><span class="sxs-lookup"><span data-stu-id="29105-104">This attribute can also be used by Windows PowerShell functions.</span></span>

<span data-ttu-id="29105-105">Wanneer dit kenmerk wordt opgegeven, wordt in de Windows PowerShell-runtime bepaalt of het opgegeven argument voor de cmdlet-parameter overeenkomt met een element in het opgegeven element instellen.</span><span class="sxs-lookup"><span data-stu-id="29105-105">When this attribute is specified, the Windows PowerShell runtime determines whether the supplied argument for the cmdlet parameter matches an element in the supplied element set.</span></span> <span data-ttu-id="29105-106">De cmdlet wordt uitgevoerd alleen als het parameterargument overeenkomt met een element in de set.</span><span class="sxs-lookup"><span data-stu-id="29105-106">The cmdlet is run only if the parameter argument matches an element in the set.</span></span> <span data-ttu-id="29105-107">Als er geen overeenkomst wordt gevonden, wordt er door de Windows PowerShell-runtime een fout gegenereerd.</span><span class="sxs-lookup"><span data-stu-id="29105-107">If no match is found, an error is thrown by the Windows PowerShell runtime.</span></span>

## <a name="syntax"></a><span data-ttu-id="29105-108">Syntaxis</span><span class="sxs-lookup"><span data-stu-id="29105-108">Syntax</span></span>

```csharp
[ValidateSetAttribute(params string[] validValues)]
[ValidateSetAttribute(params string[] validValues, Named Parameters)]
```

#### <a name="parameters"></a><span data-ttu-id="29105-109">Parameters</span><span class="sxs-lookup"><span data-stu-id="29105-109">Parameters</span></span>

<span data-ttu-id="29105-110">`ValidValues` ([System.String](/dotnet/api/System.String)) vereist.</span><span class="sxs-lookup"><span data-stu-id="29105-110">`ValidValues` ([System.String](/dotnet/api/System.String)) Required.</span></span> <span data-ttu-id="29105-111">Hiermee geeft u de waarden van het element geldige parameter.</span><span class="sxs-lookup"><span data-stu-id="29105-111">Specifies the valid parameter element values.</span></span> <span data-ttu-id="29105-112">Het volgende voorbeeld laat zien hoe een element of meerdere elementen op te geven.</span><span class="sxs-lookup"><span data-stu-id="29105-112">The following sample shows how to specify one element or multiple elements.</span></span>

```csharp
[ValidateSetAttribute("Steve")]
[ValidateSetAttribute("Steve","Mary")]
```

<span data-ttu-id="29105-113">`IgnoreCase` ([System.Boolean](/dotnet/api/System.Boolean)) met de naam van parameter optioneel.</span><span class="sxs-lookup"><span data-stu-id="29105-113">`IgnoreCase` ([System.Boolean](/dotnet/api/System.Boolean)) Optional named parameter.</span></span> <span data-ttu-id="29105-114">De standaardwaarde van `true` geeft aan dat de aanvraag wordt genegeerd.</span><span class="sxs-lookup"><span data-stu-id="29105-114">The default value of `true` indicates that case is ignored.</span></span> <span data-ttu-id="29105-115">Een waarde van `false` kunt u de cmdlet hoofdlettergevoelig.</span><span class="sxs-lookup"><span data-stu-id="29105-115">A value of `false` makes the cmdlet case-sensitive.</span></span>

## <a name="remarks"></a><span data-ttu-id="29105-116">Opmerkingen</span><span class="sxs-lookup"><span data-stu-id="29105-116">Remarks</span></span>

- <span data-ttu-id="29105-117">Dit kenmerk kan slechts één keer per parameter worden gebruikt.</span><span class="sxs-lookup"><span data-stu-id="29105-117">This attribute can be used only once per parameter.</span></span>

- <span data-ttu-id="29105-118">Als de waarde van parameter een matrix is, heeft elk element van de matrix moet overeenkomen met een element van het kenmerk is ingesteld.</span><span class="sxs-lookup"><span data-stu-id="29105-118">If the parameter value is an array, every element of the array must match an element of the attribute set.</span></span>

- <span data-ttu-id="29105-119">Het kenmerk ValidateSetAttribute wordt gedefinieerd door de [System.Management.Automation.Validatesetattribute](/dotnet/api/System.Management.Automation.ValidateSetAttribute) klasse.</span><span class="sxs-lookup"><span data-stu-id="29105-119">The ValidateSetAttribute attribute is defined by the [System.Management.Automation.Validatesetattribute](/dotnet/api/System.Management.Automation.ValidateSetAttribute) class.</span></span>

## <a name="see-also"></a><span data-ttu-id="29105-120">Zie ook</span><span class="sxs-lookup"><span data-stu-id="29105-120">See Also</span></span>

[<span data-ttu-id="29105-121">System.Management.Automation.Validatesetattribute</span><span class="sxs-lookup"><span data-stu-id="29105-121">System.Management.Automation.Validatesetattribute</span></span>](/dotnet/api/System.Management.Automation.ValidateSetAttribute)

[<span data-ttu-id="29105-122">Schrijven van een Windows PowerShell-Cmdlet</span><span class="sxs-lookup"><span data-stu-id="29105-122">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
