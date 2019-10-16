---
title: Scripts aanroepen binnen een cmdlet | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: cc0bc6ce-48a5-4d9c-927e-636bca743e9f
caps.latest.revision: 9
ms.openlocfilehash: 7dcb8bc20ab56225764854f9dc6fdfd858ed7451
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/15/2019
ms.locfileid: "72355508"
---
# <a name="how-to-invoke-scripts-within-a-cmdlet"></a><span data-ttu-id="caf5a-102">Scripts in een cmdlet aanroepen</span><span class="sxs-lookup"><span data-stu-id="caf5a-102">How to Invoke Scripts Within a Cmdlet</span></span>

<span data-ttu-id="caf5a-103">In dit voor beeld ziet u hoe u een script aanroept dat wordt geleverd aan een cmdlet.</span><span class="sxs-lookup"><span data-stu-id="caf5a-103">This example shows how to invoke a script that is supplied to a cmdlet.</span></span> <span data-ttu-id="caf5a-104">Het script wordt uitgevoerd door de cmdlet en de resultaten worden geretourneerd naar de cmdlet als een verzameling [System. Management. Automation. PSObject](/dotnet/api/System.Management.Automation.PSObject) -objecten.</span><span class="sxs-lookup"><span data-stu-id="caf5a-104">The script is executed by the cmdlet, and its results are returned to the cmdlet as a collection of [System.Management.Automation.PSObject](/dotnet/api/System.Management.Automation.PSObject) objects.</span></span>

## <a name="to-invoke-a-script-block"></a><span data-ttu-id="caf5a-105">Een script blok aanroepen</span><span class="sxs-lookup"><span data-stu-id="caf5a-105">To invoke a script block</span></span>

1. <span data-ttu-id="caf5a-106">Met deze opdracht wordt gecontroleerd of een script blok is opgegeven bij de cmdlet.</span><span class="sxs-lookup"><span data-stu-id="caf5a-106">The command verifies that a script block was supplied to the cmdlet.</span></span> <span data-ttu-id="caf5a-107">Als een script blok is opgegeven, roept de opdracht het script blok aan met de vereiste para meters.</span><span class="sxs-lookup"><span data-stu-id="caf5a-107">If a script block was supplied, the command invokes the script block with its required parameters.</span></span>

    ```csharp
    if (script != null)
    {
      WriteDebug("Executing script block.");

      // Invoke the script block with the required arguments.
      Collection<PSObject> PSObjects =
                     script.Invoke(
                                   line,
                                   simpleMatch,
                                   caseSensitive
                                  );
    ```

2. <span data-ttu-id="caf5a-108">Vervolgens doorloopt het script de geretourneerde verzameling [System. Management. Automation. PSObject](/dotnet/api/System.Management.Automation.PSObject) -objecten en voert u de benodigde bewerkingen uit.</span><span class="sxs-lookup"><span data-stu-id="caf5a-108">Then, the script iterates through the returned collection of [System.Management.Automation.PSObject](/dotnet/api/System.Management.Automation.PSObject) objects and perform the necessary operations.</span></span>

    ```c
    foreach (PSObject psObject in psObjects)
    {
      if (LanguagePrimitives.IsTrue(psObject))
      {
        result = new MatchInfo();
        result.Line = line;
        result.IgnoreCase = !caseSensitive;

        break;
      }
    }

    ```

## <a name="see-also"></a><span data-ttu-id="caf5a-109">Zie ook</span><span class="sxs-lookup"><span data-stu-id="caf5a-109">See Also</span></span>

[<span data-ttu-id="caf5a-110">Een Windows Power shell-cmdlet schrijven</span><span class="sxs-lookup"><span data-stu-id="caf5a-110">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
