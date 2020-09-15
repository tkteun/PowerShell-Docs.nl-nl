---
title: Eigenschappen declareren als para meters | Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: 63113f541df534b1f720ceb06e14b5031f2311b2
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 08/05/2020
ms.locfileid: "87774640"
---
# <a name="declaring-properties-as-parameters"></a><span data-ttu-id="b7583-102">Eigenschappen declareren als parameters</span><span class="sxs-lookup"><span data-stu-id="b7583-102">Declaring Properties as Parameters</span></span>

<span data-ttu-id="b7583-103">In dit onderwerp vindt u basis informatie die u moet begrijpen voordat u de para meters van een cmdlet declareert.</span><span class="sxs-lookup"><span data-stu-id="b7583-103">This topic provides basic information you must understand before you declare the parameters of a cmdlet.</span></span>

<span data-ttu-id="b7583-104">Als u de para meters van een cmdlet binnen de cmdlet-klasse wilt declareren, definieert u de open bare eigenschappen die voor elke para meter vertegenwoordigen en voegt u vervolgens een of meer parameter kenmerken toe aan elke eigenschap.</span><span class="sxs-lookup"><span data-stu-id="b7583-104">To declare the parameters of a cmdlet within your cmdlet class, define the public properties that represent each parameter, and then add one or more Parameter attributes to each property.</span></span> <span data-ttu-id="b7583-105">De Windows Power shell-runtime maakt gebruik van de parameter kenmerken om de eigenschap te identificeren als een cmdlet-para meter.</span><span class="sxs-lookup"><span data-stu-id="b7583-105">The Windows PowerShell runtime uses the Parameter attributes to identify the property as a cmdlet parameter.</span></span> <span data-ttu-id="b7583-106">De basis syntaxis voor het declareren van het parameter kenmerk is `[Parameter()]` .</span><span class="sxs-lookup"><span data-stu-id="b7583-106">The basic syntax for declaring the Parameter attribute is `[Parameter()]`.</span></span>

<span data-ttu-id="b7583-107">Hier volgt een voor beeld van een eigenschap die is gedefinieerd als een vereiste para meter.</span><span class="sxs-lookup"><span data-stu-id="b7583-107">Here is an example of a property defined as a required parameter.</span></span>

```csharp
[Parameter(Position = 0, Mandatory = true)]
public string UserName
{
  get { return userName; }
  set { userName = value; }
}
private string userName;
```

<span data-ttu-id="b7583-108">Hier volgen enkele dingen die u moet weten over para meters.</span><span class="sxs-lookup"><span data-stu-id="b7583-108">Here are some things to remember about parameters.</span></span>

- <span data-ttu-id="b7583-109">Een para meter moet expliciet als openbaar worden gemarkeerd.</span><span class="sxs-lookup"><span data-stu-id="b7583-109">A parameter must be explicitly marked as public.</span></span> <span data-ttu-id="b7583-110">Para meters die niet zijn gemarkeerd als open bare standaard waarde voor intern en niet worden gevonden door de Windows Power shell-runtime.</span><span class="sxs-lookup"><span data-stu-id="b7583-110">Parameters that are not marked as public default to internal and will not be found by the Windows PowerShell runtime.</span></span>

- <span data-ttu-id="b7583-111">Para meters moeten worden gedefinieerd als Microsoft .NET Framework-typen voor een betere validatie van de para meters.</span><span class="sxs-lookup"><span data-stu-id="b7583-111">Parameters should be defined as Microsoft .NET Framework types to provide better parameter validation.</span></span> <span data-ttu-id="b7583-112">Para meters die zijn beperkt tot één waarde uit een set waarden, moeten bijvoorbeeld worden gedefinieerd als een opsommings type.</span><span class="sxs-lookup"><span data-stu-id="b7583-112">For example, parameters that are restricted to one value out of a set of values should be defined as an enumeration type.</span></span> <span data-ttu-id="b7583-113">Para meters die een URI-waarde (Uniform Resource Identifier) volgen, moeten van het type [System. URI](/dotnet/api/System.Uri)zijn.</span><span class="sxs-lookup"><span data-stu-id="b7583-113">Parameters that take a Uniform Resource Identifier (URI) value should be of type [System.Uri](/dotnet/api/System.Uri).</span></span>

- <span data-ttu-id="b7583-114">Vermijd Basic string-para meters voor alle eigenschappen van een vrije-vorm tekst.</span><span class="sxs-lookup"><span data-stu-id="b7583-114">Avoid basic string parameters for all but free-form text properties.</span></span>

- <span data-ttu-id="b7583-115">U kunt een para meter toevoegen aan een wille keurig aantal parameter sets.</span><span class="sxs-lookup"><span data-stu-id="b7583-115">You can add a parameter to any number of parameter sets.</span></span> <span data-ttu-id="b7583-116">Zie [cmdlet-parameter sets](./cmdlet-parameter-sets.md)voor meer informatie over parameter sets.</span><span class="sxs-lookup"><span data-stu-id="b7583-116">For more information about parameter sets, see [Cmdlet Parameter Sets](./cmdlet-parameter-sets.md).</span></span>

<span data-ttu-id="b7583-117">Windows Power shell biedt ook een aantal algemene para meters die automatisch beschikbaar zijn voor elke cmdlet.</span><span class="sxs-lookup"><span data-stu-id="b7583-117">Windows PowerShell also provides a set of common parameters that are automatically available to every cmdlet.</span></span> <span data-ttu-id="b7583-118">Zie [algemene cmdlet-para meters](./common-parameter-names.md)voor meer informatie over deze para meters en de bijbehorende aliassen.</span><span class="sxs-lookup"><span data-stu-id="b7583-118">For more information about these parameters and their aliases, see [Cmdlet Common Parameters](./common-parameter-names.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="b7583-119">Zie ook</span><span class="sxs-lookup"><span data-stu-id="b7583-119">See Also</span></span>

[<span data-ttu-id="b7583-120">Algemene cmdlet-para meters</span><span class="sxs-lookup"><span data-stu-id="b7583-120">Cmdlet Common Parameters</span></span>](./common-parameter-names.md)

[<span data-ttu-id="b7583-121">Typen cmdlet-para meter</span><span class="sxs-lookup"><span data-stu-id="b7583-121">Types of Cmdlet Parameter</span></span>](./types-of-cmdlet-parameters.md)

[<span data-ttu-id="b7583-122">Een Windows PowerShell-cmdlet schrijven</span><span class="sxs-lookup"><span data-stu-id="b7583-122">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
