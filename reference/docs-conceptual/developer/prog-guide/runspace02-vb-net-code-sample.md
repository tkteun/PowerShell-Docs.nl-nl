---
ms.date: 09/13/2016
ms.topic: reference
title: Runspace02-codevoorbeeld (VB.NET)
description: Runspace02-codevoorbeeld (VB.NET)
ms.openlocfilehash: 07197886a062881128655379e4a4b28aaec17163
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 12/10/2020
ms.locfileid: "92657042"
---
# <a name="runspace02-vbnet-code-sample"></a><span data-ttu-id="fda6c-103">Runspace02-codevoorbeeld (VB.NET)</span><span class="sxs-lookup"><span data-stu-id="fda6c-103">Runspace02 (VB.NET) Code Sample</span></span>

<span data-ttu-id="fda6c-104">Dit is de VB.NET-bron code voor het Runspace02-voor beeld.</span><span class="sxs-lookup"><span data-stu-id="fda6c-104">Here is the VB.NET source code for the Runspace02 sample.</span></span> <span data-ttu-id="fda6c-105">In dit voor beeld wordt de klasse [System. Management. Automation. Runspaceinvoke](/dotnet/api/System.Management.Automation.RunspaceInvoke) gebruikt om de cmdlet synchroon uit te voeren `Get-Process` .</span><span class="sxs-lookup"><span data-stu-id="fda6c-105">This sample uses the [System.Management.Automation.Runspaceinvoke](/dotnet/api/System.Management.Automation.RunspaceInvoke) class to execute the `Get-Process` cmdlet synchronously.</span></span> <span data-ttu-id="fda6c-106">Windows Forms en gegevens binding worden vervolgens gebruikt om de resultaten in een DataGridView-besturings element weer te geven.</span><span class="sxs-lookup"><span data-stu-id="fda6c-106">Windows Forms and data binding are then used to display the results in a DataGridView control.</span></span>

## <a name="code-sample"></a><span data-ttu-id="fda6c-107">Code voorbeeld</span><span class="sxs-lookup"><span data-stu-id="fda6c-107">Code Sample</span></span>

```vb
Imports System
Imports System.Collections
Imports System.Collections.ObjectModel
Imports System.Windows.Forms
Imports System.Management.Automation.Runspaces
Imports System.Management.Automation

Namespace Microsoft.Samples.PowerShell.Runspaces

    Class Runspace02

        Shared Sub CreateForm()
            Dim form As New Form()
            Dim grid As New DataGridView()
            form.Controls.Add(grid)
            grid.Dock = DockStyle.Fill

            ' Create an instance of the RunspaceInvoke class.
            ' This takes care of all building all of the other
            ' data structures needed...
            Dim invoker As New RunspaceInvoke()

            Dim results As Collection(Of PSObject) = _
                invoker.Invoke("get-process | sort-object ID")

            ' The generic collection needs to be re-wrapped in an ArrayList
            ' for data-binding to work...
            Dim objects As New ArrayList()
            objects.AddRange(results)

            ' The DataGridView will use the PSObjectTypeDescriptor type
            ' to retrieve the properties.
            grid.DataSource = objects

            form.ShowDialog()

        End Sub 'CreateForm


        ''' <summary>
        ''' This sample uses the RunspaceInvoke class to execute
        ''' the get-process cmdlet synchronously. Windows Forms and data
        ''' binding are then used to display the results in a
        ''' DataGridView control.
        ''' </summary>
        ''' <param name="args">Unused</param>
        ''' <remarks>
        ''' This sample demonstrates the following:
        ''' 1. Creating an instance of the RunspaceInvoke class.
        ''' 2. Using this instance to invoke a PowerShell command.
        ''' 3. Using the output of RunspaceInvoke in a DataGridView
        '''    in a Windows Forms application
        ''' </remarks
        Shared Sub Main(ByVal args() As String)
            Runspace02.CreateForm()
        End Sub 'Main

    End Class 'Runspace02

End Namespace
```

<!-- TODO!!!: [!code-csharp[Runspace02.vb](../../powershell-sdk-samples/SDK-2.0/vb/Runspace02/Runspace02.vb#L09-L68 "Runspace02.vb")] -->

## <a name="see-also"></a><span data-ttu-id="fda6c-108">Zie ook</span><span class="sxs-lookup"><span data-stu-id="fda6c-108">See Also</span></span>

[<span data-ttu-id="fda6c-109">Windows PowerShell SDK</span><span class="sxs-lookup"><span data-stu-id="fda6c-109">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)
