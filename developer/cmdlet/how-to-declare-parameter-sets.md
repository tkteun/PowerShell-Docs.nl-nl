---
title: Hoe om te declareren parametersets | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 46905eb9-64d7-4c55-9c2a-7bc7bf04e14b
caps.latest.revision: 10
ms.openlocfilehash: 6c2e5891a8e3f24969c12a2e57dc5ae8caa68e41
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 02/03/2019
ms.locfileid: "56849397"
---
# <a name="how-to-declare-parameter-sets"></a><span data-ttu-id="a99fd-102">Parametersets declareren</span><span class="sxs-lookup"><span data-stu-id="a99fd-102">How to Declare Parameter Sets</span></span>

<span data-ttu-id="a99fd-103">In dit voorbeeld ziet u hoe u twee parametersets wanneer u de parameters voor een cmdlet declareren.</span><span class="sxs-lookup"><span data-stu-id="a99fd-103">This example shows how to define two parameter sets when you declare the parameters for a cmdlet.</span></span> <span data-ttu-id="a99fd-104">Elke parameterset is zowel een unieke parameter als een gedeelde parameter die wordt gebruikt door beide parametersets.</span><span class="sxs-lookup"><span data-stu-id="a99fd-104">Each parameter set has both a unique parameter and a shared parameter that is used by both parameter sets.</span></span> <span data-ttu-id="a99fd-105">Zie voor meer informatie over parameters sets, met inbegrip van het opgeven van de parameter standaardset [Cmdlet-Parameter stelt](./cmdlet-parameter-sets.md).</span><span class="sxs-lookup"><span data-stu-id="a99fd-105">For more information about parameters sets, including how to specify the default parameter set, see [Cmdlet Parameter Sets](./cmdlet-parameter-sets.md).</span></span>

> [!IMPORTANT]
> <span data-ttu-id="a99fd-106">Indien mogelijk, definieert u de unieke parameter van een parameter is ingesteld als een vereiste parameter.</span><span class="sxs-lookup"><span data-stu-id="a99fd-106">Whenever possible, define the unique parameter of a parameter set as a required parameter.</span></span> <span data-ttu-id="a99fd-107">Als u wilt dat de cmdlet uit te voeren zonder parameters op te geven, kan de unieke parameter echter een optionele parameter zijn.</span><span class="sxs-lookup"><span data-stu-id="a99fd-107">However, if you want your cmdlet to run without specifying any parameters, the unique parameter can be an optional parameter.</span></span> <span data-ttu-id="a99fd-108">Bijvoorbeeld, de unieke parameter van de `Get-Command` cmdlet is optioneel.</span><span class="sxs-lookup"><span data-stu-id="a99fd-108">For example, the unique parameter of the `Get-Command` cmdlet is optional.</span></span>

## <a name="how-to-define-two-parameter-sets"></a><span data-ttu-id="a99fd-109">Over het definiëren van twee parametersets</span><span class="sxs-lookup"><span data-stu-id="a99fd-109">How to Define Two Parameter Sets</span></span>

1. <span data-ttu-id="a99fd-110">Voeg de `ParameterSet` sleutelwoord met de Parameter-kenmerk voor de unieke parameter van de eerste parameter is ingesteld.</span><span class="sxs-lookup"><span data-stu-id="a99fd-110">Add the `ParameterSet` keyword to the Parameter attribute for the unique parameter of the first parameter set.</span></span>

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

2. <span data-ttu-id="a99fd-111">Voeg de `ParameterSet` sleutelwoord met de Parameter-kenmerk voor de unieke parameter van de tweede parameter is ingesteld.</span><span class="sxs-lookup"><span data-stu-id="a99fd-111">Add the `ParameterSet` keyword to the Parameter attribute for the unique parameter of the second parameter set.</span></span>

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

3. <span data-ttu-id="a99fd-112">Voor de parameter die deel uitmaakt van beide parametersets, Voeg een parameterkenmerk voor elke parameter is ingesteld en voeg vervolgens de `ParameterSet` sleutelwoord voor elke set.</span><span class="sxs-lookup"><span data-stu-id="a99fd-112">For the parameter that belongs to both parameter sets, add a Parameter attribute for each parameter set and then add the `ParameterSet` keyword to each set.</span></span> <span data-ttu-id="a99fd-113">In elk kenmerk Parameter kunt u opgeven hoe deze parameter wordt gedefinieerd.</span><span class="sxs-lookup"><span data-stu-id="a99fd-113">In each Parameter attribute, you can specify how that parameter is defined.</span></span> <span data-ttu-id="a99fd-114">Een parameter kan worden in één set optioneel en verplichte in een andere.</span><span class="sxs-lookup"><span data-stu-id="a99fd-114">A parameter can be optional in one set and mandatory in another.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="a99fd-115">Zie ook</span><span class="sxs-lookup"><span data-stu-id="a99fd-115">See Also</span></span>

[<span data-ttu-id="a99fd-116">Hiermee stelt u cmdlet-Parameter</span><span class="sxs-lookup"><span data-stu-id="a99fd-116">Cmdlet Parameter Sets</span></span>](./cmdlet-parameter-sets.md)

[<span data-ttu-id="a99fd-117">Schrijven van een Windows PowerShell-Cmdlet</span><span class="sxs-lookup"><span data-stu-id="a99fd-117">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
