---
ms.date: 09/13/2016
ms.topic: reference
title: Voorbeeld Runspace04
description: Voorbeeld Runspace04
ms.openlocfilehash: 5a2e1137963e02def419bb924c63b0d651b0fdfa
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 12/10/2020
ms.locfileid: "92657739"
---
# <a name="runspace04-sample"></a><span data-ttu-id="2f103-103">Voorbeeld Runspace04</span><span class="sxs-lookup"><span data-stu-id="2f103-103">Runspace04 Sample</span></span>

<span data-ttu-id="2f103-104">In dit voor beeld ziet u hoe u de klasse [System. Management. Automation. Power shell](/dotnet/api/system.management.automation.powershell) gebruikt om opdrachten uit te voeren en hoe u afsluit fouten kunt opvangen die worden gegenereerd bij het uitvoeren van de opdrachten.</span><span class="sxs-lookup"><span data-stu-id="2f103-104">This sample shows how to use the [System.Management.Automation.Powershell](/dotnet/api/system.management.automation.powershell) class to run commands, and how to catch terminating errors that are thrown when running the commands.</span></span> <span data-ttu-id="2f103-105">Er worden twee opdrachten uitgevoerd en de laatste opdracht is een ongeldig parameter argument door gegeven.</span><span class="sxs-lookup"><span data-stu-id="2f103-105">Two commands are run, and the last command is passed a parameter argument that is not valid.</span></span> <span data-ttu-id="2f103-106">Als gevolg hiervan worden er geen objecten geretourneerd en wordt er een afsluit fout gegenereerd.</span><span class="sxs-lookup"><span data-stu-id="2f103-106">As a result, no objects are returned and a terminating error is thrown.</span></span>

## <a name="requirements"></a><span data-ttu-id="2f103-107">Vereisten</span><span class="sxs-lookup"><span data-stu-id="2f103-107">Requirements</span></span>

<span data-ttu-id="2f103-108">Voor dit voor beeld is Windows Power Shell 2,0 vereist.</span><span class="sxs-lookup"><span data-stu-id="2f103-108">This sample requires Windows PowerShell 2.0.</span></span>

## <a name="demonstrates"></a><span data-ttu-id="2f103-109">Demonstreert</span><span class="sxs-lookup"><span data-stu-id="2f103-109">Demonstrates</span></span>

<span data-ttu-id="2f103-110">In dit voor beeld ziet u het volgende.</span><span class="sxs-lookup"><span data-stu-id="2f103-110">This sample demonstrates the following.</span></span>

- <span data-ttu-id="2f103-111">Een [System. Management. Automation. Power shell](/dotnet/api/system.management.automation.powershell) -object maken.</span><span class="sxs-lookup"><span data-stu-id="2f103-111">Creating a [System.Management.Automation.Powershell](/dotnet/api/system.management.automation.powershell) object.</span></span>

- <span data-ttu-id="2f103-112">Opdrachten toevoegen aan de pijp lijn van het object [System. Management. Automation. Power shell](/dotnet/api/system.management.automation.powershell) .</span><span class="sxs-lookup"><span data-stu-id="2f103-112">Adding commands to the pipeline of the [System.Management.Automation.Powershell](/dotnet/api/system.management.automation.powershell) object.</span></span>

- <span data-ttu-id="2f103-113">Parameter argumenten toevoegen aan de pijp lijn.</span><span class="sxs-lookup"><span data-stu-id="2f103-113">Adding parameter arguments to the pipeline.</span></span>

- <span data-ttu-id="2f103-114">De opdrachten synchroon aan te roepen.</span><span class="sxs-lookup"><span data-stu-id="2f103-114">Invoking the commands synchronously.</span></span>

- <span data-ttu-id="2f103-115">Gebruik [System. Management. Automation. PSObject](/dotnet/api/System.Management.Automation.PSObject) -objecten om eigenschappen uit te pakken en weer te geven van de objecten die door de opdrachten worden geretourneerd.</span><span class="sxs-lookup"><span data-stu-id="2f103-115">Using [System.Management.Automation.PSObject](/dotnet/api/System.Management.Automation.PSObject) objects to extract and display properties from the objects returned by the commands.</span></span>

- <span data-ttu-id="2f103-116">Fout records ophalen en weer geven die zijn gegenereerd tijdens het uitvoeren van de opdrachten.</span><span class="sxs-lookup"><span data-stu-id="2f103-116">Retrieving and displaying error records that were generated during the running of the commands.</span></span>

- <span data-ttu-id="2f103-117">Het opvangen en weer geven van afsluit uitzonderingen die door de opdrachten worden gegenereerd.</span><span class="sxs-lookup"><span data-stu-id="2f103-117">Catching and displaying terminating exceptions thrown by the commands.</span></span>

## <a name="example"></a><span data-ttu-id="2f103-118">Voorbeeld</span><span class="sxs-lookup"><span data-stu-id="2f103-118">Example</span></span>

<span data-ttu-id="2f103-119">In dit voor beeld worden opdrachten synchroon uitgevoerd in de standaard runs Pace van Windows Power shell.</span><span class="sxs-lookup"><span data-stu-id="2f103-119">This sample runs commands synchronously in the default runspace provided by Windows PowerShell.</span></span> <span data-ttu-id="2f103-120">Met de laatste opdracht wordt een afsluit fout gegenereerd omdat een ongeldig parameter argument wordt door gegeven aan de opdracht.</span><span class="sxs-lookup"><span data-stu-id="2f103-120">The last command throws a terminating error because a parameter argument that is not valid is passed to the command.</span></span> <span data-ttu-id="2f103-121">De afsluit fout wordt overgevuld en weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="2f103-121">The terminating error is trapped and displayed.</span></span>

```csharp
namespace Microsoft.Samples.PowerShell.Runspaces
{
  using System;
  using System.Management.Automation;
  using System.Management.Automation.Runspaces;
  using PowerShell = System.Management.Automation.PowerShell;

  /// <summary>
  /// This class contains the Main entry point for this host application.
  /// </summary>
  internal class Runspace04
  {
    /// <summary>
    /// This sample shows how to use a PowerShell object to run commands.
    /// The commands generate a terminating exception that the caller
    /// should catch and process.
    /// </summary>
    /// <param name="args">The parameter is not used.</param>
    /// <remarks>
    /// This sample demonstrates the following:
    /// 1. Creating a PowerShell object to run commands.
    /// 2. Adding commands to the pipeline of  the PowerShell object.
    /// 3. Passing input objects to the commands from the calling program.
    /// 4. Using PSObject objects to extract and display properties from the
    ///    objects returned by the commands.
    /// 5. Retrieving and displaying error records that were generated
    ///    while running the commands.
    /// 6. Catching and displaying terminating exceptions generated
    ///    while running the commands.
    /// </remarks>
    private static void Main(string[] args)
    {
      // Create a PowerShell object.
      using (PowerShell powershell = PowerShell.Create())
      {
        // Add the commands to the PowerShell object.
        powershell.AddCommand("Get-ChildItem").AddCommand("Select-String").AddArgument("*");

        // Run the commands synchronously. Because of the bad regular expression,
        // no objects will be returned. Instead, an exception will be thrown.
        try
        {
          foreach (PSObject result in powershell.Invoke())
          {
            Console.WriteLine("'{0}'", result.ToString());
          }

          // Process any error records that were generated while running the commands.
          Console.WriteLine("\nThe following non-terminating errors occurred:\n");
          PSDataCollection<ErrorRecord> errors = powershell.Streams.Error;
          if (errors != null && errors.Count > 0)
          {
            foreach (ErrorRecord err in errors)
            {
              System.Console.WriteLine("    error: {0}", err.ToString());
            }
          }
        }
        catch (RuntimeException runtimeException)
        {
          // Trap any exception generated by the commands. These exceptions
          // will all be derived from the RuntimeException exception.
          System.Console.WriteLine(
                        "Runtime exception: {0}: {1}\n{2}",
                        runtimeException.ErrorRecord.InvocationInfo.InvocationName,
                        runtimeException.Message,
                        runtimeException.ErrorRecord.InvocationInfo.PositionMessage);
        }
      }

      System.Console.WriteLine("\nHit any key to exit...");
      System.Console.ReadKey();
    }
  }
}
```

## <a name="see-also"></a><span data-ttu-id="2f103-122">Zie ook</span><span class="sxs-lookup"><span data-stu-id="2f103-122">See Also</span></span>

[<span data-ttu-id="2f103-123">Een Windows PowerShell-hosttoepassing schrijven</span><span class="sxs-lookup"><span data-stu-id="2f103-123">Writing a Windows PowerShell Host Application</span></span>](./writing-a-windows-powershell-host-application.md)
