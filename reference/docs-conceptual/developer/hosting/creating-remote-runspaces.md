---
ms.date: 09/12/2016
ms.topic: reference
title: Externe runspaces maken
description: Externe runspaces maken
ms.openlocfilehash: 4a2af4094ff2503fc12ee460d49565f035f0e4fe
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 12/10/2020
ms.locfileid: "92649364"
---
# <a name="creating-remote-runspaces"></a>Externe runspaces maken

Power shell-opdrachten met de para meter **ComputerName** kunnen worden uitgevoerd op elke computer waarop Power shell wordt uitgevoerd. Om opdrachten uit te voeren die geen para meter **ComputerName** hebben, kunt u WS-Management gebruiken om een runs Pace te configureren die verbinding maakt met een opgegeven computer en om opdrachten uit te voeren op die computer.

## <a name="using-a-wsmanconnection-to-create-a-remote-runspace"></a>Een WSManConnection gebruiken om een externe runs Pace te maken

 Als u een runs Pace wilt maken die verbinding maakt met een externe computer, maakt u een [System. Management. Automation. Runspaces. WSManConnectionInfo](/dotnet/api/System.Management.Automation.Runspaces.WSManConnectionInfo) -object. U geeft het doel eindpunt voor de verbinding op door de eigenschap [System. Management. Automation. Runspaces. WSManConnectionInfo. ConnectionUri](/dotnet/api/System.Management.Automation.Runspaces.WSManConnectionInfo.ConnectionUri) van het object in te stellen. Vervolgens maakt u een runs Pace door de methode [System. Management. Automation. Runspaces. RunspaceFactory. CreateRunspace](/dotnet/api/System.Management.Automation.Runspaces.RunspaceFactory.CreateRunspace) aan te roepen, waarbij u het object [System. Management. Automation. Runspaces. WSManConnectionInfo](/dotnet/api/System.Management.Automation.Runspaces.WSManConnectionInfo) opgeeft als de `connectionInfo` para meter.

 In het volgende voor beeld ziet u hoe u een runs Pace maakt die verbinding maakt met een externe computer. In het voor beeld `RemoteComputerUri` wordt gebruikt als tijdelijke aanduiding voor de daad werkelijke URI van een externe computer.

```csharp
namespace Samples
{
  using System;
  using System.Collections.ObjectModel;
  using System.Management.Automation;            // PowerShell namespace.
  using System.Management.Automation.Runspaces;  // PowerShell namespace.

  /// <summary>
  /// This class contains the Main entry point for this host application.
  /// </summary>
  internal class RemoteRunspace02
  {
    /// <summary>
    /// This sample shows how to create a remote runspace that
    /// runs commands on the local computer.
    /// </summary>
    /// <param name="args">Parameter not used.</param>
    private static void Main(string[] args)
    {
      // Create a WSManConnectionInfo object using the default constructor
      // to connect to the "localHost". The WSManConnectionInfo object can
      // also be used to specify connections to remote computers.
      Uri RemoteComputerUri = new Uri("http://Server01:5985/WSMAN");
      WSManConnectionInfo connectionInfo = new WSManConnectionInfo(RemoteComputerUri);

      // Set the OperationTimeout property and OpenTimeout properties.
      // The OperationTimeout property is used to tell PowerShell
      // how long to wait (in milliseconds) before timing out for an
      // operation. The OpenTimeout property is used to tell Windows
      // PowerShell how long to wait (in milliseconds) before timing out
      // while establishing a remote connection.
      connectionInfo.OperationTimeout = 4 * 60 * 1000; // 4 minutes.
      connectionInfo.OpenTimeout = 1 * 60 * 1000; // 1 minute.

      // Create a remote runspace using the connection information.
      //using (Runspace remoteRunspace = RunspaceFactory.CreateRunspace())
      using (Runspace remoteRunspace = RunspaceFactory.CreateRunspace(connectionInfo))
      {
        // Establish the connection by calling the Open() method to open the runspace.
        // The OpenTimeout value set previously will be applied while establishing
        // the connection. Establishing a remote connection involves sending and
        // receiving some data, so the OperationTimeout will also play a role in this process.
          remoteRunspace.Open();

        // Create a PowerShell object to run commands in the remote runspace.
        using (PowerShell powershell = PowerShell.Create())
        {
          powershell.Runspace = remoteRunspace;
          powershell.AddCommand("get-process");
          powershell.Invoke();

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

        // Close the connection. Call the Close() method to close the remote
        // runspace. The Dispose() method (called by using primitive) will call
        // the Close() method if it is not already called.
        remoteRunspace.Close();
      }
    }
  }
}
```
