---
title: Runspace01 (VB.NET)-code voorbeeld | Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: d40424283057b389d8a4aafeb8ddfa44284f3ba1
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 08/05/2020
ms.locfileid: "87778660"
---
# <a name="runspace01-vbnet-code-sample"></a>Runspace01-codevoorbeeld (VB.NET)

Hier volgen de code voorbeelden voor de runs Pace die wordt beschreven in [een console toepassing maken die een opgegeven opdracht uitvoert](/dotnet/csharp/programming-guide/inside-a-program/hello-world-your-first-program). Hiervoor roept de toepassing een runs Pace aan en roept hij een opdracht aan. (Houd er rekening mee dat met deze toepassing geen runs Pace-configuratie gegevens worden opgegeven, en dat er geen pijp lijn expliciet wordt gemaakt.) De opdracht die wordt aangeroepen, is de `Get-Process` cmdlet.

## <a name="code-sample"></a>Code voorbeeld

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

## <a name="see-also"></a>Zie ook

[Windows PowerShell SDK](../windows-powershell-reference.md)
