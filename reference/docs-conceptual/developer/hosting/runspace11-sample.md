---
ms.date: 09/13/2016
ms.topic: reference
title: Voorbeeld Runspace11
description: Voorbeeld Runspace11
ms.openlocfilehash: bb2fac179d6d3b939ed145fe98c208c202a97623
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 12/10/2020
ms.locfileid: "92657563"
---
# <a name="runspace11-sample"></a><span data-ttu-id="14faf-103">Voorbeeld Runspace11</span><span class="sxs-lookup"><span data-stu-id="14faf-103">Runspace11 Sample</span></span>

<span data-ttu-id="14faf-104">In dit voor beeld ziet u hoe u de klasse [System. Management. Automation. ProxyCommand](/dotnet/api/System.Management.Automation.ProxyCommand) gebruikt voor het maken van een proxy opdracht die een bestaande cmdlet aanroept, maar de set beschik bare para meters beperkt.</span><span class="sxs-lookup"><span data-stu-id="14faf-104">This sample shows how to use the [System.Management.Automation.Proxycommand](/dotnet/api/System.Management.Automation.ProxyCommand) class to create a proxy command that calls an existing cmdlet, but restricts the set of available parameters.</span></span> <span data-ttu-id="14faf-105">De proxy opdracht wordt vervolgens toegevoegd aan een initiële sessie status die wordt gebruikt om een beperkte runs Pace te maken.</span><span class="sxs-lookup"><span data-stu-id="14faf-105">The proxy command is then added to an initial session state that is used to create a constrained runspace.</span></span> <span data-ttu-id="14faf-106">Dit betekent dat de gebruiker alleen via de proxy opdracht toegang kan krijgen tot de functionaliteit van de cmdlet.</span><span class="sxs-lookup"><span data-stu-id="14faf-106">This means that the user can access the functionality of the cmdlet only through the proxy command.</span></span>

## <a name="requirements"></a><span data-ttu-id="14faf-107">Vereisten</span><span class="sxs-lookup"><span data-stu-id="14faf-107">Requirements</span></span>

<span data-ttu-id="14faf-108">Voor dit voor beeld is Windows Power Shell 2,0 vereist.</span><span class="sxs-lookup"><span data-stu-id="14faf-108">This sample requires Windows PowerShell 2.0.</span></span>

## <a name="demonstrates"></a><span data-ttu-id="14faf-109">Demonstreert</span><span class="sxs-lookup"><span data-stu-id="14faf-109">Demonstrates</span></span>

<span data-ttu-id="14faf-110">In dit voor beeld ziet u het volgende.</span><span class="sxs-lookup"><span data-stu-id="14faf-110">This sample demonstrates the following.</span></span>

- <span data-ttu-id="14faf-111">Een [System. Management. Automation. Commandmetadata](/dotnet/api/System.Management.Automation.CommandMetadata) -object maken waarmee de meta gegevens van een bestaande cmdlet worden beschreven.</span><span class="sxs-lookup"><span data-stu-id="14faf-111">Creating a [System.Management.Automation.Commandmetadata](/dotnet/api/System.Management.Automation.CommandMetadata) object that describes the metadata of an existing cmdlet.</span></span>

- <span data-ttu-id="14faf-112">Een [System.Management.Automation.Runspaces.Initialsessionstate](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState) -object maken.</span><span class="sxs-lookup"><span data-stu-id="14faf-112">Creating an [System.Management.Automation.Runspaces.Initialsessionstate](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState) object.</span></span>

- <span data-ttu-id="14faf-113">De cmdlet-meta gegevens wijzigen om een para meter van de cmdlet te verwijderen.</span><span class="sxs-lookup"><span data-stu-id="14faf-113">Modifying the cmdlet metadata to remove a parameter of the cmdlet.</span></span>

- <span data-ttu-id="14faf-114">De cmdlet wordt toegevoegd aan het tialsessionstate-object van [System.Management.Automation.Runspaces.Ini](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState) en de cmdlet is persoonlijk.</span><span class="sxs-lookup"><span data-stu-id="14faf-114">Adding the cmdlet to the [System.Management.Automation.Runspaces.Initialsessionstate](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState) object and making the cmdlet private.</span></span>

- <span data-ttu-id="14faf-115">Het maken van een proxy functie die de bestaande cmdlet aanroept, maar alleen een beperkt aantal para meters beschikbaar stelt.</span><span class="sxs-lookup"><span data-stu-id="14faf-115">Creating a proxy function that calls the existing cmdlet, but exposes only a restricted set of parameters.</span></span>

- <span data-ttu-id="14faf-116">De proxy functie wordt toegevoegd aan de oorspronkelijke sessie status.</span><span class="sxs-lookup"><span data-stu-id="14faf-116">Adding the proxy function to the initial session state.</span></span>

- <span data-ttu-id="14faf-117">Maken van een [System. Management. Automation. Power shell](/dotnet/api/system.management.automation.powershell) -object dat gebruikmaakt van het object [System. Management. Automation. Runspaces. runs Pace](/dotnet/api/System.Management.Automation.Runspaces.Runspace) .</span><span class="sxs-lookup"><span data-stu-id="14faf-117">Creating a [System.Management.Automation.Powershell](/dotnet/api/system.management.automation.powershell) object that uses the [System.Management.Automation.Runspaces.Runspace](/dotnet/api/System.Management.Automation.Runspaces.Runspace) object.</span></span>

- <span data-ttu-id="14faf-118">Het aanroepen van de persoonlijke cmdlet en de proxy functie met behulp van een [System. Management. Automation. Power shell](/dotnet/api/system.management.automation.powershell) -object om de beperkte runs Pace te demonstreren.</span><span class="sxs-lookup"><span data-stu-id="14faf-118">Calling the private cmdlet and the proxy function using a [System.Management.Automation.Powershell](/dotnet/api/system.management.automation.powershell) object to demonstrate the constrained runspace.</span></span>

## <a name="example"></a><span data-ttu-id="14faf-119">Voorbeeld</span><span class="sxs-lookup"><span data-stu-id="14faf-119">Example</span></span>

<span data-ttu-id="14faf-120">Hiermee maakt u een proxy opdracht voor een persoonlijke cmdlet om een beperkte runs Pace te demonstreren.</span><span class="sxs-lookup"><span data-stu-id="14faf-120">This creates a proxy command for a private cmdlet to demonstrate a constrained runspace.</span></span>

```csharp
namespace Microsoft.Samples.PowerShell.Runspaces
{
  using System;
  using System.Collections.Generic;
  using System.Diagnostics;
  using System.Management.Automation;
  using System.Management.Automation.Runspaces;
  using PowerShell = System.Management.Automation.PowerShell;

  #region GetProcCommand

  /// <summary>
  /// This class implements the get-proc cmdlet. It has been copied
  /// verbatim from the GetProcessSample02.cs sample.
  /// </summary>
  [Cmdlet(VerbsCommon.Get, "Proc")]
  public class GetProcCommand : Cmdlet
  {
    #region Parameters

    /// <summary>
    /// The names of the processes to act on.
    /// </summary>
    private string[] processNames;

    /// <summary>
    /// Gets or sets the list of process names on which
    /// the Get-Proc cmdlet will work.
    /// </summary>
    [Parameter(Position = 0)]
    [ValidateNotNullOrEmpty]
    public string[] Name
    {
      get { return this.processNames; }
      set { this.processNames = value; }
    }

    #endregion Parameters

    #region Cmdlet Overrides

    /// <summary>
    /// The ProcessRecord method calls the Process.GetProcesses
    /// method to retrieve the processes specified by the Name
    /// parameter. Then, the WriteObject method writes the
    /// associated processes to the pipeline.
    /// </summary>
    protected override void ProcessRecord()
    {
      // If no process names are passed to the cmdlet, get all
      // processes.
      if (this.processNames == null)
      {
        WriteObject(Process.GetProcesses(), true);
      }
      else
      {
        // If process names are passed to cmdlet, get and write
        // the associated processes.
        foreach (string name in this.processNames)
        {
          WriteObject(Process.GetProcessesByName(name), true);
        }
      } // if (processNames...
    } // ProcessRecord

    #endregion Cmdlet Overrides
  } // GetProcCommand

  #endregion GetProcCommand

  /// <summary>
  /// This class contains the Main entry point for this host application.
  /// </summary>
  internal class Runspace11
  {
    /// <summary>
    /// This shows how to use the ProxyCommand class to create a proxy
    /// command that calls an existing cmdlet, but restricts the set of
    /// available parameters. The proxy command is then added to an initial
    /// session state that is used to create a constrained runspace. This
    /// means that the user can access the cmdlet only through the proxy
    /// command.
    /// </summary>
    /// <remarks>
    /// This sample demonstrates the following:
    /// 1. Creating a CommandMetadata object that describes the metadata of an
    ///    existing cmdlet.
    /// 2. Modifying the cmdlet metadata to remove a parameter of the cmdlet.
    /// 3. Adding the cmdlet to an initial session state and making it private.
    /// 4. Creating a proxy function that calls the existing cmdlet, but exposes
    ///    only a restricted set of parameters.
    /// 6. Adding the proxy function to the initial session state.
    /// 7. Calling the private cmdlet and the proxy function to demonstrate the
    ///    constrained runspace.
    /// </remarks>
    private static void Main()
    {
      // Create a default initial session state. The default initial session state
      // includes all the elements that are provided by Windows PowerShell.
      InitialSessionState iss = InitialSessionState.CreateDefault();

      // Add the get-proc cmdlet to the initial session state.
      SessionStateCmdletEntry cmdletEntry = new SessionStateCmdletEntry("get-proc", typeof(GetProcCommand), null);
      iss.Commands.Add(cmdletEntry);

      // Make the cmdlet private so that it is not accessible.
      cmdletEntry.Visibility = SessionStateEntryVisibility.Private;

      // Set the language mode of the initial session state to NoLanguage to
      //prevent users from using language features. Only the invocation of
      // public commands is allowed.
      iss.LanguageMode = PSLanguageMode.NoLanguage;

      // Create the proxy command using cmdlet metadata to expose the
      // get-proc cmdlet.
      CommandMetadata cmdletMetadata = new CommandMetadata(typeof(GetProcCommand));

      // Remove one of the parameters from the command metadata.
      cmdletMetadata.Parameters.Remove("Name");

      // Generate the body of a proxy function that calls the original cmdlet,
      // but does not have the removed parameter.
      string bodyOfProxyFunction = ProxyCommand.Create(cmdletMetadata);

      // Add the proxy function to the initial session state. The name of the proxy
      // function can be the same as the name of the cmdlet, but to clearly
      // demonstrate that the original cmdlet is not available a different name is
      // used for the proxy function.
      iss.Commands.Add(new SessionStateFunctionEntry("get-procProxy", bodyOfProxyFunction));

      // Create the constrained runspace using the initial session state.
      using (Runspace myRunspace = RunspaceFactory.CreateRunspace(iss))
      {
        myRunspace.Open();

        // Call the private cmdlet to demonstrate that it is not available.
        try
        {
          using (PowerShell powershell = PowerShell.Create())
          {
            powershell.Runspace = myRunspace;
            powershell.AddCommand("get-proc").AddParameter("Name", "*explore*");
            powershell.Invoke();
          }
        }
        catch (CommandNotFoundException e)
        {
          System.Console.WriteLine(
                        "Invoking 'get-proc' failed as expected: {0}: {1}",
                        e.GetType().FullName,
                        e.Message);
        }

        // Call the proxy function to demonstrate that the -Name parameter is
        // not available.
        try
        {
          using (PowerShell powershell = PowerShell.Create())
          {
            powershell.Runspace = myRunspace;
            powershell.AddCommand("get-procProxy").AddParameter("Name", "idle");
            powershell.Invoke();
          }
        }
        catch (ParameterBindingException e)
        {
          System.Console.WriteLine(
                        "\nInvoking 'get-procProxy -Name idle' failed as expected: {0}: {1}",
                        e.GetType().FullName,
                        e.Message);
        }

        // Call the proxy function to demonstrate that it calls into the
        // private cmdlet to retrieve the processes.
        using (PowerShell powershell = PowerShell.Create())
        {
          powershell.Runspace = myRunspace;
          powershell.AddCommand("get-procProxy");
          List<Process> processes = new List<Process>(powershell.Invoke<Process>());
          System.Console.WriteLine(
                        "\nInvoking the get-procProxy function called into the get-proc cmdlet and returned {0} processes",
                        processes.Count);
        }

        // Close the runspace to release resources.
        myRunspace.Close();
      }

      System.Console.WriteLine("Hit any key to exit...");
      System.Console.ReadKey();
    }
  }
}
```

## <a name="see-also"></a><span data-ttu-id="14faf-121">Zie ook</span><span class="sxs-lookup"><span data-stu-id="14faf-121">See Also</span></span>

[<span data-ttu-id="14faf-122">Een Windows PowerShell-hosttoepassing schrijven</span><span class="sxs-lookup"><span data-stu-id="14faf-122">Writing a Windows PowerShell Host Application</span></span>](./writing-a-windows-powershell-host-application.md)
