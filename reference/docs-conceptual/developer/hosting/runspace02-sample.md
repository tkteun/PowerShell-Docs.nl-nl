---
ms.date: 09/13/2016
ms.topic: reference
title: Voorbeeld Runspace02
description: Voorbeeld Runspace02
ms.openlocfilehash: 0206e1a80f3e5488fd2dd5628985756a5ca343c8
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 12/10/2020
ms.locfileid: "92657902"
---
# <a name="runspace02-sample"></a><span data-ttu-id="2199b-103">Voorbeeld Runspace02</span><span class="sxs-lookup"><span data-stu-id="2199b-103">Runspace02 Sample</span></span>

<span data-ttu-id="2199b-104">In dit voor beeld ziet u hoe u de klasse [System. Management. Automation. Power shell](/dotnet/api/system.management.automation.powershell) gebruikt om de cmdlets voor [Get-process](/powershell/module/Microsoft.PowerShell.Management/Get-Process) en [Sort-object](/powershell/module/Microsoft.PowerShell.Utility/Sort-Object) synchroon uit te voeren.</span><span class="sxs-lookup"><span data-stu-id="2199b-104">This sample shows how to use the [System.Management.Automation.Powershell](/dotnet/api/system.management.automation.powershell) class to run the [Get-Process](/powershell/module/Microsoft.PowerShell.Management/Get-Process) and [Sort-Object](/powershell/module/Microsoft.PowerShell.Utility/Sort-Object) cmdlets synchronously.</span></span> <span data-ttu-id="2199b-105">De cmdlet [Get-process](/powershell/module/Microsoft.PowerShell.Management/Get-Process) retourneert [System. Diagnostics. process](/dotnet/api/System.Diagnostics.Process) -objecten voor elk proces dat wordt uitgevoerd op de lokale computer en de `Sort-Object` objecten worden gesorteerd op basis van hun [System.Diagnostics.process.id \*](/dotnet/api/System.Diagnostics.Process.Id) -eigenschap.</span><span class="sxs-lookup"><span data-stu-id="2199b-105">The [Get-Process](/powershell/module/Microsoft.PowerShell.Management/Get-Process) cmdlet returns [System.Diagnostics.Process](/dotnet/api/System.Diagnostics.Process) objects for each process running on the local computer, and the `Sort-Object` sorts the objects based on their [System.Diagnostics.Process.Id\*](/dotnet/api/System.Diagnostics.Process.Id) property.</span></span> <span data-ttu-id="2199b-106">De resultaten van deze opdrachten worden weer gegeven met behulp van een [System. Windows. Forms. DataGridView](/dotnet/api/System.Windows.Forms.DataGridView) -besturings element.</span><span class="sxs-lookup"><span data-stu-id="2199b-106">The results of these commands is displayed by using a [System.Windows.Forms.Datagridview](/dotnet/api/System.Windows.Forms.DataGridView) control.</span></span>

## <a name="requirements"></a><span data-ttu-id="2199b-107">Vereisten</span><span class="sxs-lookup"><span data-stu-id="2199b-107">Requirements</span></span>

<span data-ttu-id="2199b-108">Voor dit voor beeld is Windows Power Shell 2,0 vereist.</span><span class="sxs-lookup"><span data-stu-id="2199b-108">This sample requires Windows PowerShell 2.0.</span></span>

## <a name="demonstrates"></a><span data-ttu-id="2199b-109">Demonstreert</span><span class="sxs-lookup"><span data-stu-id="2199b-109">Demonstrates</span></span>

<span data-ttu-id="2199b-110">In dit voor beeld ziet u het volgende.</span><span class="sxs-lookup"><span data-stu-id="2199b-110">This sample demonstrates the following.</span></span>

- <span data-ttu-id="2199b-111">Een [System. Management. Automation. Power shell](/dotnet/api/system.management.automation.powershell) -object maken om opdrachten uit te voeren.</span><span class="sxs-lookup"><span data-stu-id="2199b-111">Creating a [System.Management.Automation.Powershell](/dotnet/api/system.management.automation.powershell) object to run commands.</span></span>

- <span data-ttu-id="2199b-112">Opdrachten toevoegen aan de pijp lijn van [System. Management. Automation. Power shell](/dotnet/api/system.management.automation.powershell) -object.</span><span class="sxs-lookup"><span data-stu-id="2199b-112">Adding commands to the pipeline of [System.Management.Automation.Powershell](/dotnet/api/system.management.automation.powershell) object.</span></span>

- <span data-ttu-id="2199b-113">De opdrachten synchroon uit te voeren.</span><span class="sxs-lookup"><span data-stu-id="2199b-113">Running the commands synchronously.</span></span>

- <span data-ttu-id="2199b-114">Het besturings element [System. Windows. Forms. DataGridView](/dotnet/api/System.Windows.Forms.DataGridView) gebruiken om de uitvoer van de opdrachten in een Windows Forms-toepassing weer te geven.</span><span class="sxs-lookup"><span data-stu-id="2199b-114">Using a [System.Windows.Forms.Datagridview](/dotnet/api/System.Windows.Forms.DataGridView) control to display the output of the commands in a Windows Forms application.</span></span>

## <a name="example"></a><span data-ttu-id="2199b-115">Voorbeeld</span><span class="sxs-lookup"><span data-stu-id="2199b-115">Example</span></span>

<span data-ttu-id="2199b-116">In dit voor beeld worden de cmdlets [Get-process](/powershell/module/Microsoft.PowerShell.Management/Get-Process) en [Sort-object](/powershell/module/Microsoft.PowerShell.Utility/Sort-Object) synchroon uitgevoerd in de standaard runs Pace van Windows Power shell.</span><span class="sxs-lookup"><span data-stu-id="2199b-116">This sample runs the [Get-Process](/powershell/module/Microsoft.PowerShell.Management/Get-Process) and [Sort-Object](/powershell/module/Microsoft.PowerShell.Utility/Sort-Object) cmdlets synchronously in the default runspace provided by Windows PowerShell.</span></span> <span data-ttu-id="2199b-117">De uitvoer wordt weer gegeven in een formulier met behulp van een [System. Windows. Forms. DataGridView](/dotnet/api/System.Windows.Forms.DataGridView) -besturings element.</span><span class="sxs-lookup"><span data-stu-id="2199b-117">The output is displayed in a form using a [System.Windows.Forms.Datagridview](/dotnet/api/System.Windows.Forms.DataGridView) control.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="2199b-118">Zie ook</span><span class="sxs-lookup"><span data-stu-id="2199b-118">See Also</span></span>

[<span data-ttu-id="2199b-119">Een Windows PowerShell-hosttoepassing schrijven</span><span class="sxs-lookup"><span data-stu-id="2199b-119">Writing a Windows PowerShell Host Application</span></span>](./writing-a-windows-powershell-host-application.md)
