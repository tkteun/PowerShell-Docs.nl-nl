---
ms.date: 09/13/2016
ms.topic: reference
title: Voorbeeld Runspace08
description: Voorbeeld Runspace08
ms.openlocfilehash: ce60e85919a78143f26ff695a9c9104c86cd4f6a
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 12/10/2020
ms.locfileid: "92657645"
---
# <a name="runspace08-sample"></a><span data-ttu-id="bd52d-103">Voorbeeld Runspace08</span><span class="sxs-lookup"><span data-stu-id="bd52d-103">Runspace08 Sample</span></span>

<span data-ttu-id="bd52d-104">Dit voor beeld laat zien hoe u opdrachten en argumenten kunt toevoegen aan de pijp lijn van een [System. Management. Automation. Power shell](/dotnet/api/system.management.automation.powershell) -object en hoe de opdrachten synchroon moeten worden uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="bd52d-104">This sample shows how to add commands and arguments to the pipeline of a [System.Management.Automation.Powershell](/dotnet/api/system.management.automation.powershell) object and how to run the commands synchronously.</span></span>

## <a name="requirements"></a><span data-ttu-id="bd52d-105">Vereisten</span><span class="sxs-lookup"><span data-stu-id="bd52d-105">Requirements</span></span>

<span data-ttu-id="bd52d-106">Voor dit voor beeld is Windows Power Shell 2,0 vereist.</span><span class="sxs-lookup"><span data-stu-id="bd52d-106">This sample requires Windows PowerShell 2.0.</span></span>

## <a name="demonstrates"></a><span data-ttu-id="bd52d-107">Demonstreert</span><span class="sxs-lookup"><span data-stu-id="bd52d-107">Demonstrates</span></span>

<span data-ttu-id="bd52d-108">In dit voor beeld ziet u het volgende.</span><span class="sxs-lookup"><span data-stu-id="bd52d-108">This sample demonstrates the following.</span></span>

- <span data-ttu-id="bd52d-109">Een object [System. Management. Automation. Runspaces. runs Pace](/dotnet/api/System.Management.Automation.Runspaces.Runspace) maken met behulp van de klasse [System. Management. Automation. Runspaces. Runspacefactory](/dotnet/api/System.Management.Automation.Runspaces.RunspaceFactory) .</span><span class="sxs-lookup"><span data-stu-id="bd52d-109">Creating a [System.Management.Automation.Runspaces.Runspace](/dotnet/api/System.Management.Automation.Runspaces.Runspace) object by using the [System.Management.Automation.Runspaces.Runspacefactory](/dotnet/api/System.Management.Automation.Runspaces.RunspaceFactory) class.</span></span>

- <span data-ttu-id="bd52d-110">Een [System. Management. Automation. Power shell](/dotnet/api/system.management.automation.powershell) -object maken dat gebruikmaakt van de runs Pace.</span><span class="sxs-lookup"><span data-stu-id="bd52d-110">Creating a [System.Management.Automation.Powershell](/dotnet/api/system.management.automation.powershell) object that uses the runspace.</span></span>

- <span data-ttu-id="bd52d-111">Cmdlets worden toegevoegd aan de pijp lijn van het object [System. Management. Automation. Power shell](/dotnet/api/system.management.automation.powershell) .</span><span class="sxs-lookup"><span data-stu-id="bd52d-111">Adding cmdlets to the pipeline of the [System.Management.Automation.Powershell](/dotnet/api/system.management.automation.powershell) object.</span></span>

- <span data-ttu-id="bd52d-112">De cmdlets synchroon uit te voeren.</span><span class="sxs-lookup"><span data-stu-id="bd52d-112">Running the cmdlets synchronously.</span></span>

- <span data-ttu-id="bd52d-113">Eigenschappen uit de objecten [System. Management. Automation. PSObject](/dotnet/api/System.Management.Automation.PSObject) worden opgehaald die door de opdracht zijn geretourneerd.</span><span class="sxs-lookup"><span data-stu-id="bd52d-113">Extracting properties from the [System.Management.Automation.PSObject](/dotnet/api/System.Management.Automation.PSObject) objects returned by the command.</span></span>

## <a name="example"></a><span data-ttu-id="bd52d-114">Voorbeeld</span><span class="sxs-lookup"><span data-stu-id="bd52d-114">Example</span></span>

<span data-ttu-id="bd52d-115">In dit voor beeld worden de cmdlets [Get-process](/powershell/module/Microsoft.PowerShell.Management/Get-Process) en [Sort-object](/powershell/module/Microsoft.PowerShell.Utility/Sort-Object) uitgevoerd met behulp van een [System. Management. Automation. Power shell](/dotnet/api/system.management.automation.powershell) -object.</span><span class="sxs-lookup"><span data-stu-id="bd52d-115">This sample runs the [Get-Process](/powershell/module/Microsoft.PowerShell.Management/Get-Process) and [Sort-Object](/powershell/module/Microsoft.PowerShell.Utility/Sort-Object) cmdlets by using a [System.Management.Automation.Powershell](/dotnet/api/system.management.automation.powershell) object.</span></span>

```csharp
namespace Microsoft.Samples.PowerShell.Runspaces
{
  using System;
  using System.Collections.Generic;
  using System.Collections.ObjectModel;
  using System.Management.Automation;
  using System.Management.Automation.Runspaces;
  using PowerShell = System.Management.Automation.PowerShell;

  /// <summary>
  /// This class contains the Main entry point for this host application.
  /// </summary>
  internal class Runspace08
  {
    /// <summary>
    /// This sample shows how to use a PowerShell object to run commands. The
    /// PowerShell object builds a pipeline that include the get-process cmdlet,
    /// which is then piped to the sort-object cmdlet. Parameters are added to the
    /// sort-object cmdlet to sort the HandleCount property in descending order.
    /// </summary>
    /// <param name="args">Parameter is not used.</param>
    /// <remarks>
    /// This sample demonstrates:
    /// 1. Creating a PowerShell object
    /// 2. Adding individual commands to the PowerShell object.
    /// 3. Adding parameters to the commands.
    /// 4. Running the pipeline of the PowerShell object synchronously.
    /// 5. Working with PSObject objects to extract properties
    ///    from the objects returned by the commands.
    /// </remarks>
    private static void Main(string[] args)
    {
      Collection<PSObject> results; // Holds the result of the pipeline execution.

      // Create the PowerShell object. Notice that no runspace is specified so a
      // new default runspace is used.
      PowerShell powershell = PowerShell.Create();

      // Use the using statement so that we can dispose of the PowerShell object
      // when we are done.
      using (powershell)
      {
        // Add the get-process cmdlet to the pipeline of the PowerShell object.
        powershell.AddCommand("get-process");

        // Add the sort-object cmdlet and its parameters to the pipeline of
        // the PowerShell object so that we can sort the HandleCount property
        //  in descending order.
        powershell.AddCommand("sort-object").AddParameter("descending").AddParameter("property", "handlecount");

        // Run the commands of the pipeline synchronously.
        results = powershell.Invoke();
      }

      // Even after disposing of the PowerShell object, we still
      // need to set the powershell variable to null so that the
      // garbage collector can clean it up.
      powershell = null;

      Console.WriteLine("Process              HandleCount");
      Console.WriteLine("--------------------------------");

      // Display the results returned by the commands.
      foreach (PSObject result in results)
      {
        Console.WriteLine(
                          "{0,-20} {1}",
                          result.Members["ProcessName"].Value,
                          result.Members["HandleCount"].Value);
      }

      System.Console.WriteLine("Hit any key to exit...");
      System.Console.ReadKey();
    }
  }
}
```

## <a name="see-also"></a><span data-ttu-id="bd52d-116">Zie ook</span><span class="sxs-lookup"><span data-stu-id="bd52d-116">See Also</span></span>

[<span data-ttu-id="bd52d-117">Een Windows PowerShell-hosttoepassing schrijven</span><span class="sxs-lookup"><span data-stu-id="bd52d-117">Writing a Windows PowerShell Host Application</span></span>](./writing-a-windows-powershell-host-application.md)
