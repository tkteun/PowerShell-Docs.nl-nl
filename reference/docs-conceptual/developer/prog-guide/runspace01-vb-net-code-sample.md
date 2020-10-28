---
ms.date: 09/13/2016
ms.topic: reference
title: Runspace01-codevoorbeeld (VB.NET)
description: Runspace01-codevoorbeeld (VB.NET)
ms.openlocfilehash: 69211662c166c40e6e99e287083f7bd53f9f536f
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/27/2020
ms.locfileid: "92653859"
---
# <a name="runspace01-vbnet-code-sample"></a><span data-ttu-id="ea4de-103">Runspace01-codevoorbeeld (VB.NET)</span><span class="sxs-lookup"><span data-stu-id="ea4de-103">Runspace01 (VB.NET) Code Sample</span></span>

<span data-ttu-id="ea4de-104">Hier volgen de code voorbeelden voor de runs Pace die wordt beschreven in [een console toepassing maken die een opgegeven opdracht uitvoert](/dotnet/csharp/programming-guide/inside-a-program/hello-world-your-first-program).</span><span class="sxs-lookup"><span data-stu-id="ea4de-104">Here are the code samples for the runspace described in [Creating a Console Application That Runs a Specified Command](/dotnet/csharp/programming-guide/inside-a-program/hello-world-your-first-program).</span></span> <span data-ttu-id="ea4de-105">Hiervoor roept de toepassing een runs Pace aan en roept hij een opdracht aan.</span><span class="sxs-lookup"><span data-stu-id="ea4de-105">To do this, the application invokes a runspace, and then invokes a command.</span></span> <span data-ttu-id="ea4de-106">(Houd er rekening mee dat met deze toepassing geen runs Pace-configuratie gegevens worden opgegeven, en dat er geen pijp lijn expliciet wordt gemaakt.) De opdracht die wordt aangeroepen, is de `Get-Process` cmdlet.</span><span class="sxs-lookup"><span data-stu-id="ea4de-106">(Note that this application does not specify runspace configuration information, nor does it explicitly create a pipeline.) The command that is invoked is the `Get-Process` cmdlet.</span></span>

## <a name="code-sample"></a><span data-ttu-id="ea4de-107">Code voorbeeld</span><span class="sxs-lookup"><span data-stu-id="ea4de-107">Code Sample</span></span>

```vb
Imports System
Imports System.Collections.Generic
Imports System.Text
Imports System.Management.Automation
Imports System.Management.Automation.Host
Imports System.Management.Automation.Runspaces

Namespace Microsoft.Samples.PowerShell.Runspaces

    Module Runspace01
        ' <summary>
        ' This sample uses the RunspaceInvoke class to execute
        ' the get-process cmdlet synchronously. The name and
        ' handlecount are then extracted from  the PSObjects
        ' returned and displayed.
        ' </summary>
        ' <param name="args">Unused</param>
        ' <remarks>
        ' This sample demonstrates the following:
        ' 1. Creating an instance of the RunspaceInvoke class.
        ' 2. Using this instance to invoke a PowerShell command.
        ' 3. Using PSObject to extract properties from the objects
        '    returned by this command.
        ' </remarks>
        Sub Main()
            ' Create an instance of the RunspaceInvoke class.
            ' This takes care of all building all of the other
            ' data structures needed...
            Dim invoker As RunspaceInvoke = New RunspaceInvoke()

            Console.WriteLine("Process              HandleCount")
            Console.WriteLine("--------------------------------")

            ' Now invoke the runspace and display the objects that are
            ' returned...
            For Each result As PSObject In invoker.Invoke("get-process")
                Console.WriteLine("{0,-20} {1}", _
                    result.Members("ProcessName").Value, _
                    result.Members("HandleCount").Value)
            Next
            System.Console.WriteLine("Hit any key to exit...")
            System.Console.ReadKey()
        End Sub
    End Module
End Namespace
```

<!-- TODO!!!: [!code-csharp[Runspace01.vb](../../powershell-sdk-samples/SDK-2.0/vb/Runspace01/Runspace01.vb#L09-L53 "Runspace01.vb")] -->

## <a name="see-also"></a><span data-ttu-id="ea4de-108">Zie ook</span><span class="sxs-lookup"><span data-stu-id="ea4de-108">See Also</span></span>

[<span data-ttu-id="ea4de-109">Windows PowerShell SDK</span><span class="sxs-lookup"><span data-stu-id="ea4de-109">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)
