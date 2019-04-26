---
title: Het aanroepen van een Cmdlet uit binnen een Cmdlet | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: efa4dc9c-ddee-46a3-978a-9dbb61e9bb6f
caps.latest.revision: 12
ms.openlocfilehash: 57543a88d04eb66c9d109249a99ddd272b02ef9d
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62067821"
---
# <a name="how-to-invoke-a-cmdlet-from-within-a-cmdlet"></a><span data-ttu-id="618d5-102">Een cmdlet aanroepen vanuit een cmdlet</span><span class="sxs-lookup"><span data-stu-id="618d5-102">How to Invoke a Cmdlet from Within a Cmdlet</span></span>

<span data-ttu-id="618d5-103">In dit voorbeeld laat zien hoe aanroepen van een cmdlet uit binnen een andere cmdlet, zodat u kunt de functionaliteit van de cmdlet aangeroepen toevoegen aan de cmdlet die u ontwikkelt.</span><span class="sxs-lookup"><span data-stu-id="618d5-103">This example shows how to invoke a cmdlet from within another cmdlet, which allows you to add the functionality of the invoked cmdlet to the cmdlet you are developing.</span></span> <span data-ttu-id="618d5-104">In dit voorbeeld wordt de `Get-Process` cmdlet wordt aangeroepen om de processen die worden uitgevoerd op de lokale computer.</span><span class="sxs-lookup"><span data-stu-id="618d5-104">In this example, the `Get-Process` cmdlet is invoked to get the processes that are running on the local computer.</span></span> <span data-ttu-id="618d5-105">De aanroep van de `Get-Process` cmdlet komt overeen met de volgende opdracht.</span><span class="sxs-lookup"><span data-stu-id="618d5-105">The call to the `Get-Process` cmdlet is equivalent to the following command.</span></span> <span data-ttu-id="618d5-106">Deze opdracht worden alle processen waarvan de namen met de tekens beginnen "a" tot "t" opgehaald.</span><span class="sxs-lookup"><span data-stu-id="618d5-106">This command retrieves all the processes whose names start with the characters "a" through "t".</span></span>

```powershell
Get-Process -name [a-t]
```

> [!IMPORTANT]
> <span data-ttu-id="618d5-107">U kunt aanroepen alleen die cmdlets die zijn afgeleid rechtstreeks vanuit de [System.Management.Automation.Cmdlet](/dotnet/api/System.Management.Automation.Cmdlet) klasse.</span><span class="sxs-lookup"><span data-stu-id="618d5-107">You can invoke only those cmdlets that derive directly from the [System.Management.Automation.Cmdlet](/dotnet/api/System.Management.Automation.Cmdlet) class.</span></span> <span data-ttu-id="618d5-108">U kunt geen aanroepen een cmdlet die is afgeleid van de [System.Management.Automation.PSCmdlet](/dotnet/api/System.Management.Automation.PSCmdlet) klasse.</span><span class="sxs-lookup"><span data-stu-id="618d5-108">You cannot invoke a cmdlet that derives from the [System.Management.Automation.PSCmdlet](/dotnet/api/System.Management.Automation.PSCmdlet) class.</span></span>

## <a name="to-invoke-a-cmdlet-from-within-a-cmdlet"></a><span data-ttu-id="618d5-109">Een cmdlet uit binnen een cmdlet aanroepen</span><span class="sxs-lookup"><span data-stu-id="618d5-109">To invoke a cmdlet from within a cmdlet</span></span>

1. <span data-ttu-id="618d5-110">Zorg ervoor dat er wordt verwezen naar de assembly waarin de cmdlet worden aangeroepen en dat de juiste `using` instructie wordt toegevoegd.</span><span class="sxs-lookup"><span data-stu-id="618d5-110">Ensure that the assembly that defines the cmdlet to be invoked is referenced and that the appropriate `using` statement is added.</span></span> <span data-ttu-id="618d5-111">In dit voorbeeld worden de volgende naamruimten toegevoegd.</span><span class="sxs-lookup"><span data-stu-id="618d5-111">In this example, the following namespaces are added.</span></span>

    ```csharp
    using System.Diagnostics;
    using System.Management.Automation;   // Windows PowerShell assembly.
    using Microsoft.PowerShell.Commands;  // Windows PowerShell assembly.
    ```

2. <span data-ttu-id="618d5-112">In de invoer-methode van de cmdlet verwerkt, maak een nieuw exemplaar van de cmdlet worden aangeroepen.</span><span class="sxs-lookup"><span data-stu-id="618d5-112">In the input processing method of the cmdlet, create a new instance of the cmdlet to be invoked.</span></span> <span data-ttu-id="618d5-113">In dit voorbeeld wordt een object van het type [Microsoft.PowerShell.Commands.Getprocesscommand](/dotnet/api/Microsoft.PowerShell.Commands.GetProcessCommand) wordt gemaakt, samen met de tekenreeks zijn met de argumenten die worden gebruikt wanneer de cmdlet wordt aangeroepen.</span><span class="sxs-lookup"><span data-stu-id="618d5-113">In this example, an object of type [Microsoft.PowerShell.Commands.Getprocesscommand](/dotnet/api/Microsoft.PowerShell.Commands.GetProcessCommand) is created along with the string that contains the arguments that are used when the cmdlet is invoked.</span></span>

    ```csharp
    GetProcessCommand gp = new GetProcessCommand();
    gp.Name = new string[] { "[a-t]*" };
    ```

3. <span data-ttu-id="618d5-114">Roep de [System.Management.Automation.Cmdlet.Invoke\*](/dotnet/api/System.Management.Automation.Cmdlet.Invoke) aan te roepen methode de `Get-Process` cmdlet.</span><span class="sxs-lookup"><span data-stu-id="618d5-114">Call the [System.Management.Automation.Cmdlet.Invoke\*](/dotnet/api/System.Management.Automation.Cmdlet.Invoke) method to invoke the `Get-Process` cmdlet.</span></span>

    ```csharp
      foreach (Process p in gp.Invoke<Process>())
      {
        Console.WriteLine(p.ToString());
      }
    }
    ```

## <a name="example"></a><span data-ttu-id="618d5-115">Voorbeeld</span><span class="sxs-lookup"><span data-stu-id="618d5-115">Example</span></span>

<span data-ttu-id="618d5-116">In dit voorbeeld wordt de `Get-Process` cmdlet wordt aangeroepen vanuit de [System.Management.Automation.Cmdlet.BeginProcessing](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing) methode van een cmdlet.</span><span class="sxs-lookup"><span data-stu-id="618d5-116">In this example, the `Get-Process` cmdlet is invoked from within the [System.Management.Automation.Cmdlet.BeginProcessing](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing) method of a cmdlet.</span></span>

```csharp
using System;
using System.Diagnostics;
using System.Management.Automation;   // Windows PowerShell assembly.
using Microsoft.PowerShell.Commands;  // Windows PowerShell assembly.

namespace SendGreeting
{
  // Declare the class as a cmdlet and specify an
  // appropriate verb and noun for the cmdlet name.
  [Cmdlet(VerbsCommunications.Send, "GreetingInvoke")]
  public class SendGreetingInvokeCommand : Cmdlet
  {
    // Declare the parameters for the cmdlet.
    [Parameter(Mandatory = true)]
    public string Name
    {
      get { return name; }
      set { name = value; }
    }
    private string name;

    // Override the BeginProcessing method to invoke
    // the Get-Process cmdlet.
    protected override void BeginProcessing()
    {
      GetProcessCommand gp = new GetProcessCommand();
      gp.Name = new string[] { "[a-t]*" };
      foreach (Process p in gp.Invoke<Process>())
      {
        Console.WriteLine(p.ToString());
      }
    }

    // Override the ProcessRecord method to process
    // the supplied user name and write out a
    // greeting to the user by calling the WriteObject
    // method.
    protected override void ProcessRecord()
    {
      WriteObject("Hello " + name + "!");
    }
  }
}
```

## <a name="see-also"></a><span data-ttu-id="618d5-117">Zie ook</span><span class="sxs-lookup"><span data-stu-id="618d5-117">See Also</span></span>

[<span data-ttu-id="618d5-118">Schrijven van een Windows PowerShell-Cmdlet</span><span class="sxs-lookup"><span data-stu-id="618d5-118">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
