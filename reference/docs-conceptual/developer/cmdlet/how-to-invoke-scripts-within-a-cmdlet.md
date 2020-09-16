---
title: Scripts aanroepen binnen een cmdlet | Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: 248ad7e2e35fe53682836d094a391023007fa0b7
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 08/05/2020
ms.locfileid: "87784126"
---
# <a name="how-to-invoke-scripts-within-a-cmdlet"></a><span data-ttu-id="8bc03-102">Scripts in een cmdlet aanroepen</span><span class="sxs-lookup"><span data-stu-id="8bc03-102">How to Invoke Scripts Within a Cmdlet</span></span>

<span data-ttu-id="8bc03-103">In dit voor beeld ziet u hoe u een script aanroept dat wordt geleverd aan een cmdlet.</span><span class="sxs-lookup"><span data-stu-id="8bc03-103">This example shows how to invoke a script that is supplied to a cmdlet.</span></span> <span data-ttu-id="8bc03-104">Het script wordt uitgevoerd door de cmdlet en de resultaten worden geretourneerd naar de cmdlet als een verzameling [System. Management. Automation. PSObject](/dotnet/api/System.Management.Automation.PSObject) -objecten.</span><span class="sxs-lookup"><span data-stu-id="8bc03-104">The script is executed by the cmdlet, and its results are returned to the cmdlet as a collection of [System.Management.Automation.PSObject](/dotnet/api/System.Management.Automation.PSObject) objects.</span></span>

## <a name="to-invoke-a-script-block"></a><span data-ttu-id="8bc03-105">Een script blok aanroepen</span><span class="sxs-lookup"><span data-stu-id="8bc03-105">To invoke a script block</span></span>

1. <span data-ttu-id="8bc03-106">Met deze opdracht wordt gecontroleerd of een script blok is opgegeven bij de cmdlet.</span><span class="sxs-lookup"><span data-stu-id="8bc03-106">The command verifies that a script block was supplied to the cmdlet.</span></span> <span data-ttu-id="8bc03-107">Als een script blok is opgegeven, roept de opdracht het script blok aan met de vereiste para meters.</span><span class="sxs-lookup"><span data-stu-id="8bc03-107">If a script block was supplied, the command invokes the script block with its required parameters.</span></span>

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

2. <span data-ttu-id="8bc03-108">Vervolgens doorloopt het script de geretourneerde verzameling [System. Management. Automation. PSObject](/dotnet/api/System.Management.Automation.PSObject) -objecten en voert u de benodigde bewerkingen uit.</span><span class="sxs-lookup"><span data-stu-id="8bc03-108">Then, the script iterates through the returned collection of [System.Management.Automation.PSObject](/dotnet/api/System.Management.Automation.PSObject) objects and perform the necessary operations.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="8bc03-109">Zie ook</span><span class="sxs-lookup"><span data-stu-id="8bc03-109">See Also</span></span>

[<span data-ttu-id="8bc03-110">Een Windows PowerShell-cmdlet schrijven</span><span class="sxs-lookup"><span data-stu-id="8bc03-110">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
