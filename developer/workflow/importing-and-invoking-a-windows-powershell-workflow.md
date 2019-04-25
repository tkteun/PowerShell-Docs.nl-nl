---
title: Importeren en het aanroepen van een Windows PowerShell-werkstroom | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 50e6f9b1-2678-4f53-9250-7c48843a9549
caps.latest.revision: 5
ms.openlocfilehash: 1113c0d1cd68bb97d2f96b529f755b62137d1f40
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62080336"
---
# <a name="importing-and-invoking-a-windows-powershell-workflow"></a>Een Windows PowerShell-werkstroom importeren en aanroepen

Windows PowerShell 3, kunt u voor het importeren en aanroepen van een werkstroom die wordt geleverd als een Windows PowerShell-module. Zie voor meer informatie over Windows PowerShell-modules [schrijven van een Windows PowerShell-Module](../module/writing-a-windows-powershell-module.md).

De [System.Management.Automation.Psjobproxy](/dotnet/api/System.Management.Automation.PSJobProxy)klasse wordt gebruikt als een client-side-proxy voor werkstroomobjecten op de server. De volgende procedure wordt uitgelegd hoe u een [System.Management.Automation.Psjobproxy](/dotnet/api/System.Management.Automation.PSJobProxy)object om aan te roepen een werkstroom.

### <a name="creating-a-psjobproxy-object-to-execute-workflow-commands-on-a-remote-server"></a>Het maken van een object PSJobProxy werkstroomopdrachten worden uitgevoerd op een externe server.

1. Maak een [System.Management.Automation.Runspaces.Wsmanconnectioninfo](/dotnet/api/System.Management.Automation.Runspaces.WSManConnectionInfo)object dat wordt gemaakt van een verbinding met een externe runspace.

2. Stel de [System.Management.Automation.Runspaces.Wsmanconnectioninfo.Shelluri*](/dotnet/api/System.Management.Automation.Runspaces.WSManConnectionInfo.ShellUri) eigenschap van de [System.Management.Automation.Runspaces.Wsmanconnectioninfo](/dotnet/api/System.Management.Automation.Runspaces.WSManConnectionInfo)object toe aan `Microsoft.PowerShell.Workflow` te een Windows PowerShell-eindpunt opgeven.

3. Maak een runspace die gebruikmaakt van de verbinding is gemaakt door de vorige stappen te voltooien.

4. Maak een [System.Management.Automation.Powershell](/dotnet/api/System.Management.Automation.PowerShell)object en stel de [System.Management.Automation.Powershell.Runspace*](/dotnet/api/System.Management.Automation.PowerShell.Runspace) eigenschap in op de runspace in de vorige stap hebt gemaakt.

5. Importeren van de werkstroommodule en de bijbehorende opdrachten in de [System.Management.Automation.Powershell](/dotnet/api/System.Management.Automation.PowerShell).

6. Maak een [System.Management.Automation.Psjobproxy](/dotnet/api/System.Management.Automation.PSJobProxy) object en gebruiken om de werkstroomopdrachten uitvoeren op de externe server.

## <a name="example"></a>Voorbeeld

Het volgende codevoorbeeld ziet u hoe u een werkstroom aanroepen met behulp van Windows PowerShell.

In dit voorbeeld vereist Windows PowerShell 3.

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