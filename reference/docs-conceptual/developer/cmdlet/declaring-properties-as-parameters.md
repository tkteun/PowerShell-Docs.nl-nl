---
ms.date: 09/13/2016
ms.topic: reference
title: Eigenschappen declareren als parameters
description: Eigenschappen declareren als parameters
ms.openlocfilehash: ade7928e2ca277da8bbd1a5e04997bd1d05f1e5d
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/27/2020
ms.locfileid: "92653155"
---
# <a name="declaring-properties-as-parameters"></a><span data-ttu-id="24415-103">Eigenschappen declareren als parameters</span><span class="sxs-lookup"><span data-stu-id="24415-103">Declaring Properties as Parameters</span></span>

<span data-ttu-id="24415-104">In dit onderwerp vindt u basis informatie die u moet begrijpen voordat u de para meters van een cmdlet declareert.</span><span class="sxs-lookup"><span data-stu-id="24415-104">This topic provides basic information you must understand before you declare the parameters of a cmdlet.</span></span>

<span data-ttu-id="24415-105">Als u de para meters van een cmdlet binnen de cmdlet-klasse wilt declareren, definieert u de open bare eigenschappen die voor elke para meter vertegenwoordigen en voegt u vervolgens een of meer parameter kenmerken toe aan elke eigenschap.</span><span class="sxs-lookup"><span data-stu-id="24415-105">To declare the parameters of a cmdlet within your cmdlet class, define the public properties that represent each parameter, and then add one or more Parameter attributes to each property.</span></span> <span data-ttu-id="24415-106">De Windows Power shell-runtime maakt gebruik van de parameter kenmerken om de eigenschap te identificeren als een cmdlet-para meter.</span><span class="sxs-lookup"><span data-stu-id="24415-106">The Windows PowerShell runtime uses the Parameter attributes to identify the property as a cmdlet parameter.</span></span> <span data-ttu-id="24415-107">De basis syntaxis voor het declareren van het parameter kenmerk is `[Parameter()]` .</span><span class="sxs-lookup"><span data-stu-id="24415-107">The basic syntax for declaring the Parameter attribute is `[Parameter()]`.</span></span>

<span data-ttu-id="24415-108">Hier volgt een voor beeld van een eigenschap die is gedefinieerd als een vereiste para meter.</span><span class="sxs-lookup"><span data-stu-id="24415-108">Here is an example of a property defined as a required parameter.</span></span>

```csharp
[Parameter(Position = 0, Mandatory = true)]
public string UserName
{
  get { return userName; }
  set { userName = value; }
}
private string userName;
```

<span data-ttu-id="24415-109">Hier volgen enkele dingen die u moet weten over para meters.</span><span class="sxs-lookup"><span data-stu-id="24415-109">Here are some things to remember about parameters.</span></span>

- <span data-ttu-id="24415-110">Een para meter moet expliciet als openbaar worden gemarkeerd.</span><span class="sxs-lookup"><span data-stu-id="24415-110">A parameter must be explicitly marked as public.</span></span> <span data-ttu-id="24415-111">Para meters die niet zijn gemarkeerd als open bare standaard waarde voor intern en niet worden gevonden door de Windows Power shell-runtime.</span><span class="sxs-lookup"><span data-stu-id="24415-111">Parameters that are not marked as public default to internal and will not be found by the Windows PowerShell runtime.</span></span>

- <span data-ttu-id="24415-112">Para meters moeten worden gedefinieerd als Microsoft .NET Framework-typen voor een betere validatie van de para meters.</span><span class="sxs-lookup"><span data-stu-id="24415-112">Parameters should be defined as Microsoft .NET Framework types to provide better parameter validation.</span></span> <span data-ttu-id="24415-113">Para meters die zijn beperkt tot één waarde uit een set waarden, moeten bijvoorbeeld worden gedefinieerd als een opsommings type.</span><span class="sxs-lookup"><span data-stu-id="24415-113">For example, parameters that are restricted to one value out of a set of values should be defined as an enumeration type.</span></span> <span data-ttu-id="24415-114">Para meters die een URI-waarde (Uniform Resource Identifier) volgen, moeten van het type [System. URI](/dotnet/api/System.Uri)zijn.</span><span class="sxs-lookup"><span data-stu-id="24415-114">Parameters that take a Uniform Resource Identifier (URI) value should be of type [System.Uri](/dotnet/api/System.Uri).</span></span>

- <span data-ttu-id="24415-115">Vermijd Basic string-para meters voor alle eigenschappen van een vrije-vorm tekst.</span><span class="sxs-lookup"><span data-stu-id="24415-115">Avoid basic string parameters for all but free-form text properties.</span></span>

- <span data-ttu-id="24415-116">U kunt een para meter toevoegen aan een wille keurig aantal parameter sets.</span><span class="sxs-lookup"><span data-stu-id="24415-116">You can add a parameter to any number of parameter sets.</span></span> <span data-ttu-id="24415-117">Zie [cmdlet-parameter sets](./cmdlet-parameter-sets.md)voor meer informatie over parameter sets.</span><span class="sxs-lookup"><span data-stu-id="24415-117">For more information about parameter sets, see [Cmdlet Parameter Sets](./cmdlet-parameter-sets.md).</span></span>

<span data-ttu-id="24415-118">Windows Power shell biedt ook een aantal algemene para meters die automatisch beschikbaar zijn voor elke cmdlet.</span><span class="sxs-lookup"><span data-stu-id="24415-118">Windows PowerShell also provides a set of common parameters that are automatically available to every cmdlet.</span></span> <span data-ttu-id="24415-119">Zie [algemene cmdlet-para meters](./common-parameter-names.md)voor meer informatie over deze para meters en de bijbehorende aliassen.</span><span class="sxs-lookup"><span data-stu-id="24415-119">For more information about these parameters and their aliases, see [Cmdlet Common Parameters](./common-parameter-names.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="24415-120">Zie ook</span><span class="sxs-lookup"><span data-stu-id="24415-120">See Also</span></span>

[<span data-ttu-id="24415-121">Algemene cmdlet-para meters</span><span class="sxs-lookup"><span data-stu-id="24415-121">Cmdlet Common Parameters</span></span>](./common-parameter-names.md)

[<span data-ttu-id="24415-122">Typen cmdlet-para meter</span><span class="sxs-lookup"><span data-stu-id="24415-122">Types of Cmdlet Parameter</span></span>](./types-of-cmdlet-parameters.md)

[<span data-ttu-id="24415-123">Een Windows PowerShell-cmdlet schrijven</span><span class="sxs-lookup"><span data-stu-id="24415-123">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
