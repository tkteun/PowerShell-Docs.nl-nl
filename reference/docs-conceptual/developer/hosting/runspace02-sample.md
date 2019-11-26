---
title: Runspace02-voor beeld | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 7630bb63-ef39-4abd-b795-8000f984c1e5
caps.latest.revision: 9
ms.openlocfilehash: 6352169cffbb8a8bf59a42f79979f5003c150fa4
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/15/2019
ms.locfileid: "72353100"
---
# <a name="runspace02-sample"></a>Voorbeeld Runspace02

In dit voor beeld ziet u hoe u de klasse [System. Management. Automation. Power shell](/dotnet/api/system.management.automation.powershell) gebruikt om de cmdlets voor [Get-process](/powershell/module/Microsoft.PowerShell.Management/Get-Process) en [Sort-object](/powershell/module/Microsoft.PowerShell.Utility/Sort-Object) synchroon uit te voeren. De cmdlet [Get-process](/powershell/module/Microsoft.PowerShell.Management/Get-Process) retourneert [System. Diagnostics. process](/dotnet/api/System.Diagnostics.Process) -objecten voor elk proces dat wordt uitgevoerd op de lokale computer en de `Sort-Object` sorteert de objecten op basis van hun [System.Diagnostics.process.id *](/dotnet/api/System.Diagnostics.Process.Id) -eigenschap. De resultaten van deze opdrachten worden weer gegeven met behulp van een [System. Windows. Forms. DataGridView](/dotnet/api/System.Windows.Forms.DataGridView) -besturings element.

## <a name="requirements"></a>Vereisten

Voor dit voor beeld is Windows Power Shell 2,0 vereist.

## <a name="demonstrates"></a>Laat zien

In dit voor beeld ziet u het volgende.

- Een [System. Management. Automation. Power shell](/dotnet/api/system.management.automation.powershell) -object maken om opdrachten uit te voeren.

- Opdrachten toevoegen aan de pijp lijn van [System. Management. Automation. Power shell](/dotnet/api/system.management.automation.powershell) -object.

- De opdrachten synchroon uit te voeren.

- Het besturings element [System. Windows. Forms. DataGridView](/dotnet/api/System.Windows.Forms.DataGridView) gebruiken om de uitvoer van de opdrachten in een Windows Forms-toepassing weer te geven.

## <a name="example"></a>Voorbeeld

In dit voor beeld worden de cmdlets [Get-process](/powershell/module/Microsoft.PowerShell.Management/Get-Process) en [Sort-object](/powershell/module/Microsoft.PowerShell.Utility/Sort-Object) synchroon uitgevoerd in de standaard runs Pace van Windows Power shell. De uitvoer wordt weer gegeven in een formulier met behulp van een [System. Windows. Forms. DataGridView](/dotnet/api/System.Windows.Forms.DataGridView) -besturings element.

```csharp
namespace Microsoft.Samples.PowerShell.Runspaces
{
  using System;
  using System.Collections;
  using System.Collections.ObjectModel;
  using System.Management.Automation;
  using System.Management.Automation.Runspaces;
  using System.Windows.Forms;
  using PowerShell = System.Management.Automation.PowerShell;

  /// <summary>
  /// This class contains the Main entry point for this host application.
  /// </summary>
  internal class Runspace02
  {
    /// <summary>
    /// This method creates the form where the output is displayed.
    /// </summary>
    private static void CreateForm()
    {
      Form form = new Form();
      DataGridView grid = new DataGridView();
      form.Controls.Add(grid);
      grid.Dock = DockStyle.Fill;

      // Create a PowerShell object. Creating this object takes care of
      // building all of the other data structures needed to run the command.
      using (PowerShell powershell = PowerShell.Create())
      {
        powershell.AddCommand("get-process").AddCommand("sort-object").AddArgument("ID");
        if (Runspace.DefaultRunspace == null)
        {
          Runspace.DefaultRunspace = powershell.Runspace;
        }

        Collection<PSObject> results = powershell.Invoke();

        // The generic collection needs to be re-wrapped in an ArrayList
        // for data-binding to work.
        ArrayList objects = new ArrayList();
        objects.AddRange(results);

        // The DataGridView will use the PSObjectTypeDescriptor type
        // to retrieve the properties.
        grid.DataSource = objects;
      }

      form.ShowDialog();
    }

    /// <summary>
    /// This sample uses a PowerShell object to run the Get-Process
    /// and Sort-Object cmdlets synchronously. Windows Forms and
    /// data binding are then used to display the results in a
    /// DataGridView control.
    /// </summary>
    /// <param name="args">The parameter is not used.</param>
    /// <remarks>
    /// This sample demonstrates the following:
    /// 1. Creating a PowerShell object.
    /// 2. Adding commands and arguments to the pipeline of
    ///    the PowerShell object.
    /// 3. Running the commands synchronously.
    /// 4. Using a DataGridView control to display the output
    ///    of the commands in a Windows Forms application.
    /// </remarks>
    private static void Main(string[] args)
    {
      Runspace02.CreateForm();
    }
  }
}
```

## <a name="see-also"></a>Zie ook

[Een Windows Power shell-hosttoepassing schrijven](./writing-a-windows-powershell-host-application.md)