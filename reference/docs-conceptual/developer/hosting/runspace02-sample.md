---
title: Runspace02-voor beeld | Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: 7a2dce436aceb1d8744377c37671a66398614851
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 08/05/2020
ms.locfileid: "87784959"
---
# <a name="runspace02-sample"></a><span data-ttu-id="35876-102">Voorbeeld Runspace02</span><span class="sxs-lookup"><span data-stu-id="35876-102">Runspace02 Sample</span></span>

<span data-ttu-id="35876-103">In dit voor beeld ziet u hoe u de klasse [System. Management. Automation. Power shell](/dotnet/api/system.management.automation.powershell) gebruikt om de cmdlets voor [Get-process](/powershell/module/Microsoft.PowerShell.Management/Get-Process) en [Sort-object](/powershell/module/Microsoft.PowerShell.Utility/Sort-Object) synchroon uit te voeren.</span><span class="sxs-lookup"><span data-stu-id="35876-103">This sample shows how to use the [System.Management.Automation.Powershell](/dotnet/api/system.management.automation.powershell) class to run the [Get-Process](/powershell/module/Microsoft.PowerShell.Management/Get-Process) and [Sort-Object](/powershell/module/Microsoft.PowerShell.Utility/Sort-Object) cmdlets synchronously.</span></span> <span data-ttu-id="35876-104">De cmdlet [Get-process](/powershell/module/Microsoft.PowerShell.Management/Get-Process) retourneert [System. Diagnostics. process](/dotnet/api/System.Diagnostics.Process) -objecten voor elk proces dat wordt uitgevoerd op de lokale computer en de `Sort-Object` objecten worden gesorteerd op basis van hun [System.Diagnostics.process.id \*](/dotnet/api/System.Diagnostics.Process.Id) -eigenschap.</span><span class="sxs-lookup"><span data-stu-id="35876-104">The [Get-Process](/powershell/module/Microsoft.PowerShell.Management/Get-Process) cmdlet returns [System.Diagnostics.Process](/dotnet/api/System.Diagnostics.Process) objects for each process running on the local computer, and the `Sort-Object` sorts the objects based on their [System.Diagnostics.Process.Id\*](/dotnet/api/System.Diagnostics.Process.Id) property.</span></span> <span data-ttu-id="35876-105">De resultaten van deze opdrachten worden weer gegeven met behulp van een [System. Windows. Forms. DataGridView](/dotnet/api/System.Windows.Forms.DataGridView) -besturings element.</span><span class="sxs-lookup"><span data-stu-id="35876-105">The results of these commands is displayed by using a [System.Windows.Forms.Datagridview](/dotnet/api/System.Windows.Forms.DataGridView) control.</span></span>

## <a name="requirements"></a><span data-ttu-id="35876-106">Vereisten</span><span class="sxs-lookup"><span data-stu-id="35876-106">Requirements</span></span>

<span data-ttu-id="35876-107">Voor dit voor beeld is Windows Power Shell 2,0 vereist.</span><span class="sxs-lookup"><span data-stu-id="35876-107">This sample requires Windows PowerShell 2.0.</span></span>

## <a name="demonstrates"></a><span data-ttu-id="35876-108">Demonstreert</span><span class="sxs-lookup"><span data-stu-id="35876-108">Demonstrates</span></span>

<span data-ttu-id="35876-109">In dit voor beeld ziet u het volgende.</span><span class="sxs-lookup"><span data-stu-id="35876-109">This sample demonstrates the following.</span></span>

- <span data-ttu-id="35876-110">Een [System. Management. Automation. Power shell](/dotnet/api/system.management.automation.powershell) -object maken om opdrachten uit te voeren.</span><span class="sxs-lookup"><span data-stu-id="35876-110">Creating a [System.Management.Automation.Powershell](/dotnet/api/system.management.automation.powershell) object to run commands.</span></span>

- <span data-ttu-id="35876-111">Opdrachten toevoegen aan de pijp lijn van [System. Management. Automation. Power shell](/dotnet/api/system.management.automation.powershell) -object.</span><span class="sxs-lookup"><span data-stu-id="35876-111">Adding commands to the pipeline of [System.Management.Automation.Powershell](/dotnet/api/system.management.automation.powershell) object.</span></span>

- <span data-ttu-id="35876-112">De opdrachten synchroon uit te voeren.</span><span class="sxs-lookup"><span data-stu-id="35876-112">Running the commands synchronously.</span></span>

- <span data-ttu-id="35876-113">Het besturings element [System. Windows. Forms. DataGridView](/dotnet/api/System.Windows.Forms.DataGridView) gebruiken om de uitvoer van de opdrachten in een Windows Forms-toepassing weer te geven.</span><span class="sxs-lookup"><span data-stu-id="35876-113">Using a [System.Windows.Forms.Datagridview](/dotnet/api/System.Windows.Forms.DataGridView) control to display the output of the commands in a Windows Forms application.</span></span>

## <a name="example"></a><span data-ttu-id="35876-114">Voorbeeld</span><span class="sxs-lookup"><span data-stu-id="35876-114">Example</span></span>

<span data-ttu-id="35876-115">In dit voor beeld worden de cmdlets [Get-process](/powershell/module/Microsoft.PowerShell.Management/Get-Process) en [Sort-object](/powershell/module/Microsoft.PowerShell.Utility/Sort-Object) synchroon uitgevoerd in de standaard runs Pace van Windows Power shell.</span><span class="sxs-lookup"><span data-stu-id="35876-115">This sample runs the [Get-Process](/powershell/module/Microsoft.PowerShell.Management/Get-Process) and [Sort-Object](/powershell/module/Microsoft.PowerShell.Utility/Sort-Object) cmdlets synchronously in the default runspace provided by Windows PowerShell.</span></span> <span data-ttu-id="35876-116">De uitvoer wordt weer gegeven in een formulier met behulp van een [System. Windows. Forms. DataGridView](/dotnet/api/System.Windows.Forms.DataGridView) -besturings element.</span><span class="sxs-lookup"><span data-stu-id="35876-116">The output is displayed in a form using a [System.Windows.Forms.Datagridview](/dotnet/api/System.Windows.Forms.DataGridView) control.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="35876-117">Zie ook</span><span class="sxs-lookup"><span data-stu-id="35876-117">See Also</span></span>

[<span data-ttu-id="35876-118">Een Windows PowerShell-hosttoepassing schrijven</span><span class="sxs-lookup"><span data-stu-id="35876-118">Writing a Windows PowerShell Host Application</span></span>](./writing-a-windows-powershell-host-application.md)
