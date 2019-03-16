---
title: Voorbeeld van Runspace06 | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 471c85f3-9287-45c2-b4bc-833caa1b7634
caps.latest.revision: 8
ms.openlocfilehash: 3850aec88bc800718a82f51c91fbd0cb3c705089
ms.sourcegitcommit: caac7d098a448232304c9d6728e7340ec7517a71
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 03/16/2019
ms.locfileid: "58059623"
---
# <a name="runspace06-sample"></a><span data-ttu-id="574eb-102">Voorbeeld Runspace06</span><span class="sxs-lookup"><span data-stu-id="574eb-102">Runspace06 Sample</span></span>

<span data-ttu-id="574eb-103">In dit voorbeeld laat zien hoe u een module om in te voegen een [System.Management.Automation.Runspaces.Initialsessionstate](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState) object zodat de module wordt geladen wanneer de runspace wordt geopend.</span><span class="sxs-lookup"><span data-stu-id="574eb-103">This sample shows how to add a module to an [System.Management.Automation.Runspaces.Initialsessionstate](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState) object so that the module is loaded when the runspace is opened.</span></span> <span data-ttu-id="574eb-104">De module biedt een cmdlet Get-Proc (gedefinieerd door de [GetProcessSample02 voorbeeld](../cmdlet/getprocesssample02-sample.md)) die synchroon wordt uitgevoerd met behulp van een [System.Management.Automation.Powershell](/dotnet/api/system.management.automation.powershell) object.</span><span class="sxs-lookup"><span data-stu-id="574eb-104">The module provides a Get-Proc cmdlet (defined by the [GetProcessSample02 Sample](../cmdlet/getprocesssample02-sample.md)) that is run synchronously by using a [System.Management.Automation.Powershell](/dotnet/api/system.management.automation.powershell) object.</span></span>

## <a name="requirements"></a><span data-ttu-id="574eb-105">Vereisten</span><span class="sxs-lookup"><span data-stu-id="574eb-105">Requirements</span></span>

<span data-ttu-id="574eb-106">In dit voorbeeld is Windows PowerShell 2.0 vereist.</span><span class="sxs-lookup"><span data-stu-id="574eb-106">This sample requires Windows PowerShell 2.0.</span></span>

## <a name="demonstrates"></a><span data-ttu-id="574eb-107">Hier ziet u</span><span class="sxs-lookup"><span data-stu-id="574eb-107">Demonstrates</span></span>

<span data-ttu-id="574eb-108">In dit voorbeeld ziet u het volgende.</span><span class="sxs-lookup"><span data-stu-id="574eb-108">This sample demonstrates the following.</span></span>

- <span data-ttu-id="574eb-109">Het maken van een [System.Management.Automation.Runspaces.Initialsessionstate](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState) object.</span><span class="sxs-lookup"><span data-stu-id="574eb-109">Creating an [System.Management.Automation.Runspaces.Initialsessionstate](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState) object.</span></span>

- <span data-ttu-id="574eb-110">Toevoegen van de module aan de [System.Management.Automation.Runspaces.Initialsessionstate](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState) object.</span><span class="sxs-lookup"><span data-stu-id="574eb-110">Adding the module to the [System.Management.Automation.Runspaces.Initialsessionstate](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState) object.</span></span>

- <span data-ttu-id="574eb-111">Het maken van een [System.Management.Automation.Runspaces.Runspace](/dotnet/api/System.Management.Automation.Runspaces.Runspace) object die gebruikmaakt van de [System.Management.Automation.Runspaces.Initialsessionstate](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState) object.</span><span class="sxs-lookup"><span data-stu-id="574eb-111">Creating a [System.Management.Automation.Runspaces.Runspace](/dotnet/api/System.Management.Automation.Runspaces.Runspace) object that uses the [System.Management.Automation.Runspaces.Initialsessionstate](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState) object.</span></span>

- <span data-ttu-id="574eb-112">Het maken van een [System.Management.Automation.Powershell](/dotnet/api/system.management.automation.powershell) object dat de runspace gebruikt.</span><span class="sxs-lookup"><span data-stu-id="574eb-112">Creating a [System.Management.Automation.Powershell](/dotnet/api/system.management.automation.powershell) object that uses the runspace.</span></span>

- <span data-ttu-id="574eb-113">Van de module get-proc cmdlet toe te voegen aan de pijplijn met de [System.Management.Automation.Powershell](/dotnet/api/system.management.automation.powershell) object.</span><span class="sxs-lookup"><span data-stu-id="574eb-113">Adding the module's get-proc cmdlet to the pipeline of the [System.Management.Automation.Powershell](/dotnet/api/system.management.automation.powershell) object.</span></span>

- <span data-ttu-id="574eb-114">De opdracht synchroon wordt uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="574eb-114">Running the command synchronously.</span></span>

- <span data-ttu-id="574eb-115">Uitpakken van de eigenschappen van de [System.Management.Automation.PSObject](/dotnet/api/System.Management.Automation.PSObject) objecten geretourneerd door de opdracht.</span><span class="sxs-lookup"><span data-stu-id="574eb-115">Extracting properties from the [System.Management.Automation.PSObject](/dotnet/api/System.Management.Automation.PSObject) objects returned by the command.</span></span>

## <a name="example"></a><span data-ttu-id="574eb-116">Voorbeeld</span><span class="sxs-lookup"><span data-stu-id="574eb-116">Example</span></span>

<span data-ttu-id="574eb-117">Hiermee maakt u een runspace die gebruikmaakt van een [System.Management.Automation.Runspaces.Initialsessionstate](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState) object voor het definiëren van de elementen die beschikbaar zijn wanneer de runspace wordt geopend.</span><span class="sxs-lookup"><span data-stu-id="574eb-117">This sample creates a runspace that uses an [System.Management.Automation.Runspaces.Initialsessionstate](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState) object to define the elements that are available when the runspace is opened.</span></span> <span data-ttu-id="574eb-118">In dit voorbeeld wordt een module die u een cmdlet Get-Proc definieert toegevoegd aan de status van de eerste sessie.</span><span class="sxs-lookup"><span data-stu-id="574eb-118">In this sample, a module that defines a Get-Proc cmdlet is added to the initial session state.</span></span>

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
  internal class Runspace06
  {
    /// <summary>
    /// This sample shows how to define an initial session state that is
    /// used when creating a runspace. The sample invokes a command from
    /// a binary module that is loaded by the initial session state.
    /// </summary>
    /// <param name="args">Parameter not used.</param>
    /// <remarks>
    /// This sample assumes that user has coppied the GetProcessSample02.dll
    /// that is produced by the GetProcessSample02 sample to the current
    /// directory.
    /// This sample demonstrates the following:
    /// 1. Creating a default initial session state.
    /// 2. Adding a module to the initial session state.
    /// 3. Creating a runspace that uses the initial session state.
    /// 4. Creating a PowerShell object that uses the runspace.
    /// 5. Adding the module's get-proc cmdlet to the PowerShell object.
    /// 6. Running the command synchronously.
    /// 7. Using PSObject objects to extract and display properties from
    ///    the objects returned by the cmdlet.
    /// </remarks>
    private static void Main(string[] args)
    {
        // Create the default initial session state and add the module.
      InitialSessionState iss = InitialSessionState.CreateDefault();
      iss.ImportPSModule(new string[] { @".\GetProcessSample02.dll" });

      // Create a runspace. Notice that no PSHost object is supplied to the
      // CreateRunspace method so the default host is used. See the Host
      // samples for more information on creating your own custom host.
      using (Runspace myRunSpace = RunspaceFactory.CreateRunspace(iss))
      {
        myRunSpace.Open();

        // Create a PowerShell object.
        using (PowerShell powershell = PowerShell.Create())
        {
          // Add the cmdlet and specify the runspace.
          powershell.AddCommand(@"GetProcessSample02\get-proc");
          powershell.Runspace = myRunSpace;

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

## <a name="see-also"></a><span data-ttu-id="574eb-119">Zie ook</span><span class="sxs-lookup"><span data-stu-id="574eb-119">See Also</span></span>

[<span data-ttu-id="574eb-120">Een Windows PowerShell-hosttoepassing schrijven</span><span class="sxs-lookup"><span data-stu-id="574eb-120">Writing a Windows PowerShell Host Application</span></span>](./writing-a-windows-powershell-host-application.md)