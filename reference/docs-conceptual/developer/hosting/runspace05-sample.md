---
title: Runspace05-voor beeld | Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: 2d274028d2357a26cd75cf70a033abbf907f5c4d
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 08/05/2020
ms.locfileid: "87772158"
---
# <a name="runspace05-sample"></a><span data-ttu-id="0defc-102">Voorbeeld Runspace05</span><span class="sxs-lookup"><span data-stu-id="0defc-102">Runspace05 Sample</span></span>

<span data-ttu-id="0defc-103">In dit voor beeld ziet u hoe u een module kunt toevoegen aan een [System.Management.Automation.Runspaces.Initialsessionstate](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState) -object, zodat de cmdlet van de module beschikbaar is wanneer de runs Pace wordt geopend.</span><span class="sxs-lookup"><span data-stu-id="0defc-103">This sample shows how to add a snap-in to an [System.Management.Automation.Runspaces.Initialsessionstate](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState) object so that the cmdlet of the snap-in is available when the runspace is opened.</span></span> <span data-ttu-id="0defc-104">De module biedt een Get-proc-cmdlet (gedefinieerd door het GetProcessSample01-voor [beeld](../cmdlet/getprocesssample01-sample.md)) die synchroon wordt uitgevoerd met behulp van een [System. Management. Automation. Power shell](/dotnet/api/system.management.automation.powershell) -object.</span><span class="sxs-lookup"><span data-stu-id="0defc-104">The snap-in provides a Get-Proc cmdlet (defined by the [GetProcessSample01 Sample](../cmdlet/getprocesssample01-sample.md)) that is run synchronously by using a [System.Management.Automation.Powershell](/dotnet/api/system.management.automation.powershell) object.</span></span>

## <a name="requirements"></a><span data-ttu-id="0defc-105">Vereisten</span><span class="sxs-lookup"><span data-stu-id="0defc-105">Requirements</span></span>

<span data-ttu-id="0defc-106">Voor dit voor beeld is Windows Power Shell 2,0 vereist.</span><span class="sxs-lookup"><span data-stu-id="0defc-106">This sample requires Windows PowerShell 2.0.</span></span>

## <a name="demonstrates"></a><span data-ttu-id="0defc-107">Demonstreert</span><span class="sxs-lookup"><span data-stu-id="0defc-107">Demonstrates</span></span>

<span data-ttu-id="0defc-108">In dit voor beeld ziet u het volgende.</span><span class="sxs-lookup"><span data-stu-id="0defc-108">This sample demonstrates the following.</span></span>

- <span data-ttu-id="0defc-109">Een [System.Management.Automation.Runspaces.Initialsessionstate](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState) -object maken.</span><span class="sxs-lookup"><span data-stu-id="0defc-109">Creating an [System.Management.Automation.Runspaces.Initialsessionstate](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState) object.</span></span>

- <span data-ttu-id="0defc-110">De module wordt toegevoegd aan het tialsessionstate-object [System.Management.Automation.Runspaces.Ini](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState) .</span><span class="sxs-lookup"><span data-stu-id="0defc-110">Adding the snap-in to the [System.Management.Automation.Runspaces.Initialsessionstate](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState) object.</span></span>

- <span data-ttu-id="0defc-111">Een object [System. Management. Automation. Runspaces. runs Pace](/dotnet/api/System.Management.Automation.Runspaces.Runspace) maken dat gebruikmaakt van het [System.Management.Automation.Runspaces.Initialsessionstate](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState) -object.</span><span class="sxs-lookup"><span data-stu-id="0defc-111">Creating a [System.Management.Automation.Runspaces.Runspace](/dotnet/api/System.Management.Automation.Runspaces.Runspace) object that uses the [System.Management.Automation.Runspaces.Initialsessionstate](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState) object.</span></span>

- <span data-ttu-id="0defc-112">Een [System. Management. Automation. Power shell](/dotnet/api/system.management.automation.powershell) -object maken dat gebruikmaakt van de runs Pace.</span><span class="sxs-lookup"><span data-stu-id="0defc-112">Creating a [System.Management.Automation.Powershell](/dotnet/api/system.management.automation.powershell) object that uses the runspace.</span></span>

- <span data-ttu-id="0defc-113">De cmdlet Get-proc van de module toevoegen aan de pijp lijn van het object [System. Management. Automation. Power shell](/dotnet/api/system.management.automation.powershell) .</span><span class="sxs-lookup"><span data-stu-id="0defc-113">Adding the snap-in's get-proc cmdlet to the pipeline of the [System.Management.Automation.Powershell](/dotnet/api/system.management.automation.powershell) object.</span></span>

- <span data-ttu-id="0defc-114">De opdracht synchroon uitvoeren.</span><span class="sxs-lookup"><span data-stu-id="0defc-114">Running the command synchronously.</span></span>

- <span data-ttu-id="0defc-115">Eigenschappen uit de objecten [System. Management. Automation. PSObject](/dotnet/api/System.Management.Automation.PSObject) worden opgehaald die door de opdracht zijn geretourneerd.</span><span class="sxs-lookup"><span data-stu-id="0defc-115">Extracting properties from the [System.Management.Automation.PSObject](/dotnet/api/System.Management.Automation.PSObject) objects returned by the command.</span></span>

## <a name="example"></a><span data-ttu-id="0defc-116">Voorbeeld</span><span class="sxs-lookup"><span data-stu-id="0defc-116">Example</span></span>

<span data-ttu-id="0defc-117">In dit voor beeld wordt een runs Pace gemaakt die gebruikmaakt van een [System.Management.Automation.Runspaces.Initialsessionstate](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState) -object om de elementen te definiëren die beschikbaar zijn wanneer de runs Pace wordt geopend.</span><span class="sxs-lookup"><span data-stu-id="0defc-117">This sample creates a runspace that uses an [System.Management.Automation.Runspaces.Initialsessionstate](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState) object to define the elements that are available when the runspace is opened.</span></span> <span data-ttu-id="0defc-118">In dit voor beeld wordt een module die een Get-proc-cmdlet definieert, toegevoegd aan de eerste sessie status.</span><span class="sxs-lookup"><span data-stu-id="0defc-118">In this sample, a snap-in that defines a Get-Proc cmdlet is added to the initial session state.</span></span>

```csharp
namespace Microsoft.Samples.PowerShell.Runspaces
{
  using System;
  using System.Collections.ObjectModel;
  using System.Management.Automation;
  using System.Management.Automation.Runspaces;
  using PowerShell = System.Management.Automation.PowerShell;

  /// <summary>
  /// This class contains the Main entry point for this host application.
  /// </summary>
  internal class Runspace05
  {
    /// <summary>
    /// This sample shows how to define an initial session state that is
    /// used when creating a runspace. The sample invokes a command from
    /// a Windows PowerShell snap-in that is present in the console file.
    /// </summary>
    /// <param name="args">The parameter is not used.</param>
    /// <remarks>
    /// This sample assumes that user has coppied the GetProcessSample01.dll
    /// that is produced by the GetProcessSample01 sample to the current
    /// directory.
    /// This sample demonstrates the following:
    /// 1. Creating a default initial session state.
    /// 2. Adding a snap-in to the initial session state.
    /// 3. Creating a runspace that uses the initial session state.
    /// 4. Creating a PowerShell object that uses the runspace.
    /// 5. Adding the snap-in's get-proc cmdlet to the PowerShell object.
    /// 6. Using PSObject objects to extract and display properties from
    ///    the objects returned by the cmdlet.
    /// </remarks>
    private static void Main(string[] args)
    {
      // Create the default initial session state. The default initial
      // session state contains all the elements provided by Windows
      // PowerShell.
      InitialSessionState iss = InitialSessionState.CreateDefault();
      PSSnapInException warning;
      iss.ImportPSSnapIn("GetProcPSSnapIn01", out warning);

      // Create a runspace. Notice that no PSHost object is supplied to the
      // CreateRunspace method so the default host is used. See the Host
      // samples for more information on creating your own custom host.
      using (Runspace myRunSpace = RunspaceFactory.CreateRunspace(iss))
      {
        myRunSpace.Open();

        // Create a PowerShell object.
        using (PowerShell powershell = PowerShell.Create())
        {
          // Add the snap-in cmdlet and specify the runspace.
          powershell.AddCommand("GetProcPSSnapIn01\\get-proc");
          powershell.Runspace = myRunSpace;

          // Run the cmdlet synchronously.
          Collection<PSObject> results = powershell.Invoke();

          Console.WriteLine("Process              HandleCount");
          Console.WriteLine("--------------------------------");

          // Display the results.
          foreach (PSObject result in results)
          {
            Console.WriteLine(
                              "{0,-20} {1}",
                              result.Members["ProcessName"].Value,
                              result.Members["HandleCount"].Value);
          }
        }

        // Close the runspace to release any resources.
        myRunSpace.Close();
      }
      System.Console.WriteLine("Hit any key to exit...");
      System.Console.ReadKey();
    }
  }
}
```

## <a name="see-also"></a><span data-ttu-id="0defc-119">Zie ook</span><span class="sxs-lookup"><span data-stu-id="0defc-119">See Also</span></span>

[<span data-ttu-id="0defc-120">Een Windows PowerShell-hosttoepassing schrijven</span><span class="sxs-lookup"><span data-stu-id="0defc-120">Writing a Windows PowerShell Host Application</span></span>](./writing-a-windows-powershell-host-application.md)
