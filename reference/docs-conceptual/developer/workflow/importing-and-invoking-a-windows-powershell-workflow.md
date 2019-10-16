---
title: Een Windows Power shell-werk stroom importeren en aanroepen | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 50e6f9b1-2678-4f53-9250-7c48843a9549
caps.latest.revision: 5
ms.openlocfilehash: 1113c0d1cd68bb97d2f96b529f755b62137d1f40
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/15/2019
ms.locfileid: "72356649"
---
# <a name="importing-and-invoking-a-windows-powershell-workflow"></a>Een Windows PowerShell-werkstroom importeren en aanroepen

Met Windows Power Shell 3 kunt u een werk stroom importeren en aanroepen die is verpakt als een Windows Power shell-module. Zie [een Windows Power shell-module schrijven](../module/writing-a-windows-powershell-module.md)voor meer informatie over Windows Power shell-modules.

De klasse [System. Management. Automation. Psjobproxy](/dotnet/api/System.Management.Automation.PSJobProxy)wordt gebruikt als proxy aan de client zijde voor werk stroom objecten op de server. In de volgende procedure wordt uitgelegd hoe u een [System. Management. Automation. Psjobproxy](/dotnet/api/System.Management.Automation.PSJobProxy)-object gebruikt om een werk stroom aan te roepen.

### <a name="creating-a-psjobproxy-object-to-execute-workflow-commands-on-a-remote-server"></a>Er wordt een PSJobProxy-object gemaakt om werk stroom opdrachten op een externe server uit te voeren.

1. Maak een [System. Management. Automation. Runspaces. Wsmanconnectioninfo](/dotnet/api/System.Management.Automation.Runspaces.WSManConnectionInfo)-object om een verbinding met een externe runs Pace te maken.

2. Stel de eigenschap [System. Management. Automation. Runspaces. Wsmanconnectioninfo. Shelluri *](/dotnet/api/System.Management.Automation.Runspaces.WSManConnectionInfo.ShellUri) van het object [System. Management. Automation. Runspaces. Wsmanconnectioninfo](/dotnet/api/System.Management.Automation.Runspaces.WSManConnectionInfo)in op `Microsoft.PowerShell.Workflow` om een Windows Power shell-eind punt op te geven.

3. Maak een runs Pace die gebruikmaakt van de verbinding die is gemaakt door de vorige stappen te volt ooien.

4. Maak een [System. Management. Automation. Power shell](/dotnet/api/System.Management.Automation.PowerShell)-object en stel de eigenschap [System. Management. Automation. Power shell. runs Pace *](/dotnet/api/System.Management.Automation.PowerShell.Runspace) in op de runs Pace die in de vorige stap is gemaakt.

5. Importeer de werk stroom module en de bijbehorende opdrachten in het [System. Management. Automation. Power shell](/dotnet/api/System.Management.Automation.PowerShell).

6. Maak een [System. Management. Automation. Psjobproxy](/dotnet/api/System.Management.Automation.PSJobProxy) -object en gebruik dit om werk stroom opdrachten op de externe server uit te voeren.

## <a name="example"></a>Voorbeeld

In het volgende code voorbeeld ziet u hoe u een werk stroom aanroept met behulp van Windows Power shell.

In dit voor beeld is Windows Power Shell 3 vereist.

```csharp
using System;
using System.Collections.Generic;
using System.Linq;
using System.Text;
using System.Management.Automation;
using System.Management.Automation.Runspaces;

namespace WorkflowHostTest
{

class Program
    {
        static void Main(string[] args)
        {
            if (args.Length == 0)
            {
                Console.WriteLine("Specify path to Workflow module");
                return;
            }

            string moduleFile = args[0];

            Console.Write("Creating Remote runspace connection...");
            WSManConnectionInfo connectionInfo = new WSManConnectionInfo();

            //Set the shellURI to workflow endpoint Microsoft.PowerShell.Workflow
            connectionInfo.ShellUri = "Microsoft.PowerShell.Workflow";

            //Create and open a runspace.
            Runspace runspace = RunspaceFactory.CreateRunspace(connectionInfo);
            runspace.Open();
            Console.WriteLine("done");

            PowerShell powershell = PowerShell.Create();
            powershell.Runspace = runspace;
            Console.Write("Setting $VerbosePreference=\"Continue\"...");
            powershell.AddScript("$VerbosePreference=\"Continue\"");
            powershell.Invoke();
            Console.WriteLine("done");

            Console.Write("Importing Workflow module...");
            powershell.Commands.Clear();

            //Import the module in to the PowerShell runspace. A XAML file could also be imported directly by using Import-Module.
            powershell.AddCommand("Import-Module").AddArgument(moduleFile);
            powershell.Invoke();
            Console.WriteLine("done");

            Console.Write("Creating job proxy...");
            powershell.Commands.Clear();
            powershell.AddCommand("Get-Proc").AddArgument("*");
            PSJobProxy job = powershell.AsJobProxy();
            Console.WriteLine("done");

                Console.WriteLine();
                Console.WriteLine("Using job proxy and performing operations...");
                Console.WriteLine("State of Job :" + job.JobStateInfo.State.ToString());
                Console.WriteLine("Starting job...");
                job.StartJob();
                Console.WriteLine("State of Job :" + job.JobStateInfo.State.ToString());

                // use blocking enumerator to wait for objects until job finishes
                job.Output.BlockingEnumerator = true;
                foreach (PSObject o in job.Output)
                {
                    Console.WriteLine(o.Properties["ProcessName"].Value.ToString());
                }

                // wait for a random time before attempting to stop job
                Random random = new Random();
                int time = random.Next(1, 10);
                Console.Write("Sleeping for {0} seconds when job is running on another thread...", time);
                System.Threading.Thread.Sleep(time * 1000);
                Console.WriteLine("done");
                Console.WriteLine("Stopping job...");
                job.StopJob();
                Console.WriteLine("State of Job :" + job.JobStateInfo.State.ToString());
                Console.WriteLine();
                job.Finished.WaitOne();
                Console.WriteLine("Output from job");
                Console.WriteLine("---------------");

                foreach (PSObject o in job.Output)
                {
                    Console.WriteLine(o.Properties["ProcessName"].Value.ToString());
                }

                Console.WriteLine();
                Console.WriteLine("Verbose messages from job");
                Console.WriteLine("-------------------------");
                foreach (VerboseRecord v in job.Verbose)
                {
                    Console.WriteLine(v.Message);
                }

            runspace.Close();
        }
    }
}

```