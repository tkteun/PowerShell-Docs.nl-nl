---
title: Parameter sets declareren | Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: e6d06a9a78356693fe7a338dc5c9207044b23441
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 08/05/2020
ms.locfileid: "87784160"
---
# <a name="how-to-declare-parameter-sets"></a><span data-ttu-id="4f421-102">Parametersets declareren</span><span class="sxs-lookup"><span data-stu-id="4f421-102">How to Declare Parameter Sets</span></span>

<span data-ttu-id="4f421-103">In dit voor beeld ziet u hoe u twee parameter sets definieert wanneer u de para meters voor een cmdlet declareert.</span><span class="sxs-lookup"><span data-stu-id="4f421-103">This example shows how to define two parameter sets when you declare the parameters for a cmdlet.</span></span> <span data-ttu-id="4f421-104">Elke parameterset heeft zowel een unieke para meter als een gedeelde para meter die wordt gebruikt door beide parameter sets.</span><span class="sxs-lookup"><span data-stu-id="4f421-104">Each parameter set has both a unique parameter and a shared parameter that is used by both parameter sets.</span></span> <span data-ttu-id="4f421-105">Zie [para meters](./cmdlet-parameter-sets.md)voor de cmdlet voor meer informatie over parameters sets, zoals het opgeven van de standaard parameterset.</span><span class="sxs-lookup"><span data-stu-id="4f421-105">For more information about parameters sets, including how to specify the default parameter set, see [Cmdlet Parameter Sets](./cmdlet-parameter-sets.md).</span></span>

> [!IMPORTANT]
> <span data-ttu-id="4f421-106">Als dat mogelijk is, definieert u de unieke para meter van een para meter die is ingesteld als een vereiste para meter.</span><span class="sxs-lookup"><span data-stu-id="4f421-106">Whenever possible, define the unique parameter of a parameter set as a required parameter.</span></span> <span data-ttu-id="4f421-107">Als u de cmdlet echter wilt uitvoeren zonder para meters op te geven, kunt u een optionele para meter opgeven.</span><span class="sxs-lookup"><span data-stu-id="4f421-107">However, if you want your cmdlet to run without specifying any parameters, the unique parameter can be an optional parameter.</span></span> <span data-ttu-id="4f421-108">Zo is de unieke para meter van de `Get-Command` cmdlet optioneel.</span><span class="sxs-lookup"><span data-stu-id="4f421-108">For example, the unique parameter of the `Get-Command` cmdlet is optional.</span></span>

## <a name="how-to-define-two-parameter-sets"></a><span data-ttu-id="4f421-109">Twee parameter sets definiëren</span><span class="sxs-lookup"><span data-stu-id="4f421-109">How to Define Two Parameter Sets</span></span>

1. <span data-ttu-id="4f421-110">Voeg het `ParameterSet` tref woord toe aan het parameter kenmerk voor de unieke para meter van de eerste parameterset.</span><span class="sxs-lookup"><span data-stu-id="4f421-110">Add the `ParameterSet` keyword to the Parameter attribute for the unique parameter of the first parameter set.</span></span>

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

2. <span data-ttu-id="4f421-111">Voeg het `ParameterSet` tref woord toe aan het parameter kenmerk voor de unieke para meter van de tweede parameterset.</span><span class="sxs-lookup"><span data-stu-id="4f421-111">Add the `ParameterSet` keyword to the Parameter attribute for the unique parameter of the second parameter set.</span></span>

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

3. <span data-ttu-id="4f421-112">Voor de para meter die deel uitmaakt van beide parameter sets, voegt u een parameter kenmerk toe voor elke parameterset en voegt u vervolgens het `ParameterSet` tref woord toe aan elke set.</span><span class="sxs-lookup"><span data-stu-id="4f421-112">For the parameter that belongs to both parameter sets, add a Parameter attribute for each parameter set and then add the `ParameterSet` keyword to each set.</span></span> <span data-ttu-id="4f421-113">In elk parameter kenmerk kunt u opgeven hoe die para meter wordt gedefinieerd.</span><span class="sxs-lookup"><span data-stu-id="4f421-113">In each Parameter attribute, you can specify how that parameter is defined.</span></span> <span data-ttu-id="4f421-114">Een para meter kan optioneel zijn in een set en verplicht in een andere.</span><span class="sxs-lookup"><span data-stu-id="4f421-114">A parameter can be optional in one set and mandatory in another.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="4f421-115">Zie ook</span><span class="sxs-lookup"><span data-stu-id="4f421-115">See Also</span></span>

[<span data-ttu-id="4f421-116">Parametersets voor cmdlets</span><span class="sxs-lookup"><span data-stu-id="4f421-116">Cmdlet Parameter Sets</span></span>](./cmdlet-parameter-sets.md)

[<span data-ttu-id="4f421-117">Een Windows PowerShell-cmdlet schrijven</span><span class="sxs-lookup"><span data-stu-id="4f421-117">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
