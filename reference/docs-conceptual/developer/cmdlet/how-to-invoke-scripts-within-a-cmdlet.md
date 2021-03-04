---
ms.date: 09/13/2016
ms.topic: reference
title: Scripts in een cmdlet aanroepen
description: Scripts in een cmdlet aanroepen
ms.openlocfilehash: 503ecb8913fe61ef3f5ec6fe969c22c2319a4f12
ms.sourcegitcommit: 1dfd5554b70c7e8f4e3df19e29c384a9c0a4b227
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 03/03/2021
ms.locfileid: "101685342"
---
# <a name="how-to-invoke-scripts-within-a-cmdlet"></a><span data-ttu-id="48066-103">Scripts in een cmdlet aanroepen</span><span class="sxs-lookup"><span data-stu-id="48066-103">How to Invoke Scripts Within a Cmdlet</span></span>

<span data-ttu-id="48066-104">In dit voor beeld ziet u hoe u een script aanroept dat wordt geleverd aan een cmdlet.</span><span class="sxs-lookup"><span data-stu-id="48066-104">This example shows how to invoke a script that is supplied to a cmdlet.</span></span> <span data-ttu-id="48066-105">Het script wordt uitgevoerd door de cmdlet en de resultaten worden geretourneerd naar de cmdlet als een verzameling [System. Management. Automation. PSObject](/dotnet/api/System.Management.Automation.PSObject) -objecten.</span><span class="sxs-lookup"><span data-stu-id="48066-105">The script is executed by the cmdlet, and its results are returned to the cmdlet as a collection of [System.Management.Automation.PSObject](/dotnet/api/System.Management.Automation.PSObject) objects.</span></span>

## <a name="to-invoke-a-script-block"></a><span data-ttu-id="48066-106">Een script blok aanroepen</span><span class="sxs-lookup"><span data-stu-id="48066-106">To invoke a script block</span></span>

1. <span data-ttu-id="48066-107">Met deze opdracht wordt gecontroleerd of een script blok is opgegeven bij de cmdlet.</span><span class="sxs-lookup"><span data-stu-id="48066-107">The command verifies that a script block was supplied to the cmdlet.</span></span> <span data-ttu-id="48066-108">Als een script blok is opgegeven, roept de opdracht het script blok aan met de vereiste para meters.</span><span class="sxs-lookup"><span data-stu-id="48066-108">If a script block was supplied, the command invokes the script block with its required parameters.</span></span>

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

2. <span data-ttu-id="48066-109">Vervolgens doorloopt het script de geretourneerde verzameling [System. Management. Automation. PSObject](/dotnet/api/System.Management.Automation.PSObject) -objecten en voert u de benodigde bewerkingen uit.</span><span class="sxs-lookup"><span data-stu-id="48066-109">Then, the script iterates through the returned collection of [System.Management.Automation.PSObject](/dotnet/api/System.Management.Automation.PSObject) objects and perform the necessary operations.</span></span>

    ```csharp
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

## <a name="see-also"></a><span data-ttu-id="48066-110">Zie ook</span><span class="sxs-lookup"><span data-stu-id="48066-110">See Also</span></span>

[<span data-ttu-id="48066-111">Een Windows PowerShell-cmdlet schrijven</span><span class="sxs-lookup"><span data-stu-id="48066-111">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
