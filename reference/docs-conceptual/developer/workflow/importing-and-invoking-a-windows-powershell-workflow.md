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
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 12/05/2019
ms.locfileid: "72356649"
---
# <a name="importing-and-invoking-a-windows-powershell-workflow"></a><span data-ttu-id="c01b0-102">Een Windows PowerShell-werkstroom importeren en aanroepen</span><span class="sxs-lookup"><span data-stu-id="c01b0-102">Importing and Invoking a Windows PowerShell Workflow</span></span>

<span data-ttu-id="c01b0-103">Met Windows Power Shell 3 kunt u een werk stroom importeren en aanroepen die is verpakt als een Windows Power shell-module.</span><span class="sxs-lookup"><span data-stu-id="c01b0-103">Windows PowerShell 3, allows you to import and invoke a workflow that is packaged as a Windows PowerShell module.</span></span> <span data-ttu-id="c01b0-104">Zie [een Windows Power shell-module schrijven](../module/writing-a-windows-powershell-module.md)voor meer informatie over Windows Power shell-modules.</span><span class="sxs-lookup"><span data-stu-id="c01b0-104">For information about Windows PowerShell modules, see [Writing a Windows PowerShell Module](../module/writing-a-windows-powershell-module.md).</span></span>

<span data-ttu-id="c01b0-105">De klasse [System. Management. Automation. Psjobproxy](/dotnet/api/System.Management.Automation.PSJobProxy)wordt gebruikt als proxy aan de client zijde voor werk stroom objecten op de server.</span><span class="sxs-lookup"><span data-stu-id="c01b0-105">The [System.Management.Automation.Psjobproxy](/dotnet/api/System.Management.Automation.PSJobProxy)class is used as a client side proxy for workflow objects on the server.</span></span> <span data-ttu-id="c01b0-106">In de volgende procedure wordt uitgelegd hoe u een [System. Management. Automation. Psjobproxy](/dotnet/api/System.Management.Automation.PSJobProxy)-object gebruikt om een werk stroom aan te roepen.</span><span class="sxs-lookup"><span data-stu-id="c01b0-106">The following procedure explains how to use a [System.Management.Automation.Psjobproxy](/dotnet/api/System.Management.Automation.PSJobProxy)object to invoke a workflow.</span></span>

### <a name="creating-a-psjobproxy-object-to-execute-workflow-commands-on-a-remote-server"></a><span data-ttu-id="c01b0-107">Er wordt een PSJobProxy-object gemaakt om werk stroom opdrachten op een externe server uit te voeren.</span><span class="sxs-lookup"><span data-stu-id="c01b0-107">Creating a PSJobProxy object to execute workflow commands on a remote server.</span></span>

1. <span data-ttu-id="c01b0-108">Maak een [System. Management. Automation. Runspaces. Wsmanconnectioninfo](/dotnet/api/System.Management.Automation.Runspaces.WSManConnectionInfo)-object om een verbinding met een externe runs Pace te maken.</span><span class="sxs-lookup"><span data-stu-id="c01b0-108">Create an [System.Management.Automation.Runspaces.Wsmanconnectioninfo](/dotnet/api/System.Management.Automation.Runspaces.WSManConnectionInfo)object to create a connection to a remote runspace.</span></span>

2. <span data-ttu-id="c01b0-109">Stel de eigenschap [System. Management. Automation. Runspaces. Wsmanconnectioninfo. Shelluri \*](/dotnet/api/System.Management.Automation.Runspaces.WSManConnectionInfo.ShellUri) van het object [System. Management. Automation. Runspaces. Wsmanconnectioninfo](/dotnet/api/System.Management.Automation.Runspaces.WSManConnectionInfo)in op `Microsoft.PowerShell.Workflow` om een Windows Power shell-eind punt op te geven.</span><span class="sxs-lookup"><span data-stu-id="c01b0-109">Set the [System.Management.Automation.Runspaces.Wsmanconnectioninfo.Shelluri\*](/dotnet/api/System.Management.Automation.Runspaces.WSManConnectionInfo.ShellUri) property of the [System.Management.Automation.Runspaces.Wsmanconnectioninfo](/dotnet/api/System.Management.Automation.Runspaces.WSManConnectionInfo)object to `Microsoft.PowerShell.Workflow` to specify a Windows PowerShell endpoint.</span></span>

3. <span data-ttu-id="c01b0-110">Maak een runs Pace die gebruikmaakt van de verbinding die is gemaakt door de vorige stappen te volt ooien.</span><span class="sxs-lookup"><span data-stu-id="c01b0-110">Create a runspace that uses the connection created by completing the previous steps.</span></span>

4. <span data-ttu-id="c01b0-111">Maak een [System. Management. Automation. Power shell](/dotnet/api/System.Management.Automation.PowerShell)-object en stel de eigenschap [System. Management. Automation. Power shell. runs Pace \*](/dotnet/api/System.Management.Automation.PowerShell.Runspace) in op de runs Pace die in de vorige stap is gemaakt.</span><span class="sxs-lookup"><span data-stu-id="c01b0-111">Create a [System.Management.Automation.Powershell](/dotnet/api/System.Management.Automation.PowerShell)object and set its [System.Management.Automation.Powershell.Runspace\*](/dotnet/api/System.Management.Automation.PowerShell.Runspace) property to the runspace created in the previous step.</span></span>

5. <span data-ttu-id="c01b0-112">Importeer de werk stroom module en de bijbehorende opdrachten in het [System. Management. Automation. Power shell](/dotnet/api/System.Management.Automation.PowerShell).</span><span class="sxs-lookup"><span data-stu-id="c01b0-112">Import the workflow module and its commands into the [System.Management.Automation.Powershell](/dotnet/api/System.Management.Automation.PowerShell).</span></span>

6. <span data-ttu-id="c01b0-113">Maak een [System. Management. Automation. Psjobproxy](/dotnet/api/System.Management.Automation.PSJobProxy) -object en gebruik dit om werk stroom opdrachten op de externe server uit te voeren.</span><span class="sxs-lookup"><span data-stu-id="c01b0-113">Create a [System.Management.Automation.Psjobproxy](/dotnet/api/System.Management.Automation.PSJobProxy) object and use it to execute workflow commands on the remote server.</span></span>

## <a name="example"></a><span data-ttu-id="c01b0-114">Voorbeeld</span><span class="sxs-lookup"><span data-stu-id="c01b0-114">Example</span></span>

<span data-ttu-id="c01b0-115">In het volgende code voorbeeld ziet u hoe u een werk stroom aanroept met behulp van Windows Power shell.</span><span class="sxs-lookup"><span data-stu-id="c01b0-115">The following code example demonstrates how to invoke a workflow by using Windows PowerShell.</span></span>

<span data-ttu-id="c01b0-116">In dit voor beeld is Windows Power Shell 3 vereist.</span><span class="sxs-lookup"><span data-stu-id="c01b0-116">This example requires Windows PowerShell 3.</span></span>

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