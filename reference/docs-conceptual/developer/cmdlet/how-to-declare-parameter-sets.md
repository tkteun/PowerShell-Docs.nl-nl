---
ms.date: 09/13/2016
ms.topic: reference
title: Parametersets declareren
description: Parametersets declareren
ms.openlocfilehash: bd4d504a9fe6c7f7626901c49bc08851244f0995
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/27/2020
ms.locfileid: "92667059"
---
# <a name="how-to-declare-parameter-sets"></a><span data-ttu-id="9a72a-103">Parametersets declareren</span><span class="sxs-lookup"><span data-stu-id="9a72a-103">How to Declare Parameter Sets</span></span>

<span data-ttu-id="9a72a-104">In dit voor beeld ziet u hoe u twee parameter sets definieert wanneer u de para meters voor een cmdlet declareert.</span><span class="sxs-lookup"><span data-stu-id="9a72a-104">This example shows how to define two parameter sets when you declare the parameters for a cmdlet.</span></span> <span data-ttu-id="9a72a-105">Elke parameterset heeft zowel een unieke para meter als een gedeelde para meter die wordt gebruikt door beide parameter sets.</span><span class="sxs-lookup"><span data-stu-id="9a72a-105">Each parameter set has both a unique parameter and a shared parameter that is used by both parameter sets.</span></span> <span data-ttu-id="9a72a-106">Zie [para meters](./cmdlet-parameter-sets.md)voor de cmdlet voor meer informatie over parameters sets, zoals het opgeven van de standaard parameterset.</span><span class="sxs-lookup"><span data-stu-id="9a72a-106">For more information about parameters sets, including how to specify the default parameter set, see [Cmdlet Parameter Sets](./cmdlet-parameter-sets.md).</span></span>

> [!IMPORTANT]
> <span data-ttu-id="9a72a-107">Als dat mogelijk is, definieert u de unieke para meter van een para meter die is ingesteld als een vereiste para meter.</span><span class="sxs-lookup"><span data-stu-id="9a72a-107">Whenever possible, define the unique parameter of a parameter set as a required parameter.</span></span> <span data-ttu-id="9a72a-108">Als u de cmdlet echter wilt uitvoeren zonder para meters op te geven, kunt u een optionele para meter opgeven.</span><span class="sxs-lookup"><span data-stu-id="9a72a-108">However, if you want your cmdlet to run without specifying any parameters, the unique parameter can be an optional parameter.</span></span> <span data-ttu-id="9a72a-109">Zo is de unieke para meter van de `Get-Command` cmdlet optioneel.</span><span class="sxs-lookup"><span data-stu-id="9a72a-109">For example, the unique parameter of the `Get-Command` cmdlet is optional.</span></span>

## <a name="how-to-define-two-parameter-sets"></a><span data-ttu-id="9a72a-110">Twee parameter sets definiëren</span><span class="sxs-lookup"><span data-stu-id="9a72a-110">How to Define Two Parameter Sets</span></span>

1. <span data-ttu-id="9a72a-111">Voeg het `ParameterSet` tref woord toe aan het parameter kenmerk voor de unieke para meter van de eerste parameterset.</span><span class="sxs-lookup"><span data-stu-id="9a72a-111">Add the `ParameterSet` keyword to the Parameter attribute for the unique parameter of the first parameter set.</span></span>

   ```csharp
   [Parameter(Position = 0, Mandatory = true,
              ParameterSetName = "Test01")]
   public string UserName
   {
     get { return userName; }
     set { userName = value; }
   }
   private string userName;
   ```

2. <span data-ttu-id="9a72a-112">Voeg het `ParameterSet` tref woord toe aan het parameter kenmerk voor de unieke para meter van de tweede parameterset.</span><span class="sxs-lookup"><span data-stu-id="9a72a-112">Add the `ParameterSet` keyword to the Parameter attribute for the unique parameter of the second parameter set.</span></span>

   ```csharp
   [Parameter(Position = 0, Mandatory = true,
              ParameterSetName = "Test02")]
   public string ComputerName
   {
     get { return computerName; }
     set { computerName = value; }
   }
   private string computerName;
   ```

3. <span data-ttu-id="9a72a-113">Voor de para meter die deel uitmaakt van beide parameter sets, voegt u een parameter kenmerk toe voor elke parameterset en voegt u vervolgens het `ParameterSet` tref woord toe aan elke set.</span><span class="sxs-lookup"><span data-stu-id="9a72a-113">For the parameter that belongs to both parameter sets, add a Parameter attribute for each parameter set and then add the `ParameterSet` keyword to each set.</span></span> <span data-ttu-id="9a72a-114">In elk parameter kenmerk kunt u opgeven hoe die para meter wordt gedefinieerd.</span><span class="sxs-lookup"><span data-stu-id="9a72a-114">In each Parameter attribute, you can specify how that parameter is defined.</span></span> <span data-ttu-id="9a72a-115">Een para meter kan optioneel zijn in een set en verplicht in een andere.</span><span class="sxs-lookup"><span data-stu-id="9a72a-115">A parameter can be optional in one set and mandatory in another.</span></span>

   ```csharp
   [Parameter(Mandatory= true, ParameterSetName = "Test01")]
   [Parameter(ParameterSetName = "Test02")]
   public string SharedParam
   {
       get { return sharedParam; }
       set { sharedParam = value; }
   }
   private string sharedParam;
   ```

## <a name="see-also"></a><span data-ttu-id="9a72a-116">Zie ook</span><span class="sxs-lookup"><span data-stu-id="9a72a-116">See Also</span></span>

[<span data-ttu-id="9a72a-117">Parametersets voor cmdlets</span><span class="sxs-lookup"><span data-stu-id="9a72a-117">Cmdlet Parameter Sets</span></span>](./cmdlet-parameter-sets.md)

[<span data-ttu-id="9a72a-118">Een Windows PowerShell-cmdlet schrijven</span><span class="sxs-lookup"><span data-stu-id="9a72a-118">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
