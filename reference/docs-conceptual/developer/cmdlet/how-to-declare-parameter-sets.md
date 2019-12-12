---
title: Parameter sets declareren | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 46905eb9-64d7-4c55-9c2a-7bc7bf04e14b
caps.latest.revision: 10
ms.openlocfilehash: 6c2e5891a8e3f24969c12a2e57dc5ae8caa68e41
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 12/05/2019
ms.locfileid: "72356348"
---
# <a name="how-to-declare-parameter-sets"></a><span data-ttu-id="a5c54-102">Parametersets declareren</span><span class="sxs-lookup"><span data-stu-id="a5c54-102">How to Declare Parameter Sets</span></span>

<span data-ttu-id="a5c54-103">In dit voor beeld ziet u hoe u twee parameter sets definieert wanneer u de para meters voor een cmdlet declareert.</span><span class="sxs-lookup"><span data-stu-id="a5c54-103">This example shows how to define two parameter sets when you declare the parameters for a cmdlet.</span></span> <span data-ttu-id="a5c54-104">Elke parameterset heeft zowel een unieke para meter als een gedeelde para meter die wordt gebruikt door beide parameter sets.</span><span class="sxs-lookup"><span data-stu-id="a5c54-104">Each parameter set has both a unique parameter and a shared parameter that is used by both parameter sets.</span></span> <span data-ttu-id="a5c54-105">Zie [para meters](./cmdlet-parameter-sets.md)voor de cmdlet voor meer informatie over parameters sets, zoals het opgeven van de standaard parameterset.</span><span class="sxs-lookup"><span data-stu-id="a5c54-105">For more information about parameters sets, including how to specify the default parameter set, see [Cmdlet Parameter Sets](./cmdlet-parameter-sets.md).</span></span>

> [!IMPORTANT]
> <span data-ttu-id="a5c54-106">Als dat mogelijk is, definieert u de unieke para meter van een para meter die is ingesteld als een vereiste para meter.</span><span class="sxs-lookup"><span data-stu-id="a5c54-106">Whenever possible, define the unique parameter of a parameter set as a required parameter.</span></span> <span data-ttu-id="a5c54-107">Als u de cmdlet echter wilt uitvoeren zonder para meters op te geven, kunt u een optionele para meter opgeven.</span><span class="sxs-lookup"><span data-stu-id="a5c54-107">However, if you want your cmdlet to run without specifying any parameters, the unique parameter can be an optional parameter.</span></span> <span data-ttu-id="a5c54-108">Zo is de unieke para meter van de cmdlet `Get-Command` optioneel.</span><span class="sxs-lookup"><span data-stu-id="a5c54-108">For example, the unique parameter of the `Get-Command` cmdlet is optional.</span></span>

## <a name="how-to-define-two-parameter-sets"></a><span data-ttu-id="a5c54-109">Twee parameter sets definiëren</span><span class="sxs-lookup"><span data-stu-id="a5c54-109">How to Define Two Parameter Sets</span></span>

1. <span data-ttu-id="a5c54-110">Voeg het sleutel woord `ParameterSet` toe aan het parameter kenmerk voor de unieke para meter van de eerste parameterset.</span><span class="sxs-lookup"><span data-stu-id="a5c54-110">Add the `ParameterSet` keyword to the Parameter attribute for the unique parameter of the first parameter set.</span></span>

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

2. <span data-ttu-id="a5c54-111">Voeg het sleutel woord `ParameterSet` toe aan het parameter kenmerk voor de unieke para meter van de tweede parameterset.</span><span class="sxs-lookup"><span data-stu-id="a5c54-111">Add the `ParameterSet` keyword to the Parameter attribute for the unique parameter of the second parameter set.</span></span>

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

3. <span data-ttu-id="a5c54-112">Voor de para meter die deel uitmaakt van beide parameter sets, voegt u een parameter kenmerk toe voor elke parameterset en voegt u vervolgens het sleutel woord `ParameterSet` toe aan elke set.</span><span class="sxs-lookup"><span data-stu-id="a5c54-112">For the parameter that belongs to both parameter sets, add a Parameter attribute for each parameter set and then add the `ParameterSet` keyword to each set.</span></span> <span data-ttu-id="a5c54-113">In elk parameter kenmerk kunt u opgeven hoe die para meter wordt gedefinieerd.</span><span class="sxs-lookup"><span data-stu-id="a5c54-113">In each Parameter attribute, you can specify how that parameter is defined.</span></span> <span data-ttu-id="a5c54-114">Een para meter kan optioneel zijn in een set en verplicht in een andere.</span><span class="sxs-lookup"><span data-stu-id="a5c54-114">A parameter can be optional in one set and mandatory in another.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="a5c54-115">Zie ook</span><span class="sxs-lookup"><span data-stu-id="a5c54-115">See Also</span></span>

[<span data-ttu-id="a5c54-116">Cmdlet-parameter sets</span><span class="sxs-lookup"><span data-stu-id="a5c54-116">Cmdlet Parameter Sets</span></span>](./cmdlet-parameter-sets.md)

[<span data-ttu-id="a5c54-117">Een Windows Power shell-cmdlet schrijven</span><span class="sxs-lookup"><span data-stu-id="a5c54-117">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
