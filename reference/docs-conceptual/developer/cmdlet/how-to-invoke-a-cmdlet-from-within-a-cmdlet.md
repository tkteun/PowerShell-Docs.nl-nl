---
title: Een cmdlet aanroepen vanuit een cmdlet | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: efa4dc9c-ddee-46a3-978a-9dbb61e9bb6f
caps.latest.revision: 12
ms.openlocfilehash: 57543a88d04eb66c9d109249a99ddd272b02ef9d
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/15/2019
ms.locfileid: "72356306"
---
# <a name="how-to-invoke-a-cmdlet-from-within-a-cmdlet"></a><span data-ttu-id="45861-102">Een cmdlet aanroepen vanuit een cmdlet</span><span class="sxs-lookup"><span data-stu-id="45861-102">How to Invoke a Cmdlet from Within a Cmdlet</span></span>

<span data-ttu-id="45861-103">In dit voor beeld ziet u hoe u een cmdlet aanroept vanuit een andere cmdlet, waarmee u de functionaliteit van de aangeroepen cmdlet kunt toevoegen aan de cmdlet die u ontwikkelt.</span><span class="sxs-lookup"><span data-stu-id="45861-103">This example shows how to invoke a cmdlet from within another cmdlet, which allows you to add the functionality of the invoked cmdlet to the cmdlet you are developing.</span></span> <span data-ttu-id="45861-104">In dit voor beeld wordt de cmdlet `Get-Process` aangeroepen om de processen op te halen die worden uitgevoerd op de lokale computer.</span><span class="sxs-lookup"><span data-stu-id="45861-104">In this example, the `Get-Process` cmdlet is invoked to get the processes that are running on the local computer.</span></span> <span data-ttu-id="45861-105">De aanroep van de cmdlet `Get-Process` is gelijk aan de volgende opdracht.</span><span class="sxs-lookup"><span data-stu-id="45861-105">The call to the `Get-Process` cmdlet is equivalent to the following command.</span></span> <span data-ttu-id="45861-106">Met deze opdracht worden alle processen opgehaald waarvan de namen beginnen met de tekens a tot en met t.</span><span class="sxs-lookup"><span data-stu-id="45861-106">This command retrieves all the processes whose names start with the characters "a" through "t".</span></span>

```powershell
Get-Process -name [a-t]
```

> [!IMPORTANT]
> <span data-ttu-id="45861-107">U kunt alleen de cmdlets aanroepen die rechtstreeks zijn afgeleid van de klasse [System. Management. Automation. cmdlet](/dotnet/api/System.Management.Automation.Cmdlet) .</span><span class="sxs-lookup"><span data-stu-id="45861-107">You can invoke only those cmdlets that derive directly from the [System.Management.Automation.Cmdlet](/dotnet/api/System.Management.Automation.Cmdlet) class.</span></span> <span data-ttu-id="45861-108">U kunt geen cmdlet aanroepen die is afgeleid van de klasse [System. Management. Automation. PSCmdlet](/dotnet/api/System.Management.Automation.PSCmdlet) .</span><span class="sxs-lookup"><span data-stu-id="45861-108">You cannot invoke a cmdlet that derives from the [System.Management.Automation.PSCmdlet](/dotnet/api/System.Management.Automation.PSCmdlet) class.</span></span>

## <a name="to-invoke-a-cmdlet-from-within-a-cmdlet"></a><span data-ttu-id="45861-109">Een cmdlet aanroepen vanuit een cmdlet</span><span class="sxs-lookup"><span data-stu-id="45861-109">To invoke a cmdlet from within a cmdlet</span></span>

1. <span data-ttu-id="45861-110">Controleer of er wordt verwezen naar de assembly die de cmdlet definieert die moet worden aangeroepen en dat de juiste `using`-instructie is toegevoegd.</span><span class="sxs-lookup"><span data-stu-id="45861-110">Ensure that the assembly that defines the cmdlet to be invoked is referenced and that the appropriate `using` statement is added.</span></span> <span data-ttu-id="45861-111">In dit voor beeld worden de volgende naam ruimten toegevoegd.</span><span class="sxs-lookup"><span data-stu-id="45861-111">In this example, the following namespaces are added.</span></span>

    ```csharp
    using System.Diagnostics;
    using System.Management.Automation;   // Windows PowerShell assembly.
    using Microsoft.PowerShell.Commands;  // Windows PowerShell assembly.
    ```

2. <span data-ttu-id="45861-112">Maak in de invoer verwerkings methode van de cmdlet een nieuw exemplaar van de cmdlet die moet worden aangeroepen.</span><span class="sxs-lookup"><span data-stu-id="45861-112">In the input processing method of the cmdlet, create a new instance of the cmdlet to be invoked.</span></span> <span data-ttu-id="45861-113">In dit voor beeld wordt een object van het type [micro soft. Power shell. commands. Getprocesscommand](/dotnet/api/Microsoft.PowerShell.Commands.GetProcessCommand) gemaakt samen met de teken reeks die de argumenten bevat die worden gebruikt wanneer de cmdlet wordt aangeroepen.</span><span class="sxs-lookup"><span data-stu-id="45861-113">In this example, an object of type [Microsoft.PowerShell.Commands.Getprocesscommand](/dotnet/api/Microsoft.PowerShell.Commands.GetProcessCommand) is created along with the string that contains the arguments that are used when the cmdlet is invoked.</span></span>

    ```csharp
    GetProcessCommand gp = new GetProcessCommand();
    gp.Name = new string[] { "[a-t]*" };
    ```

3. <span data-ttu-id="45861-114">Roep de methode [System. Management. Automation. cmdlet. Invoke \*](/dotnet/api/System.Management.Automation.Cmdlet.Invoke) aan om de `Get-Process`-cmdlet aan te roepen.</span><span class="sxs-lookup"><span data-stu-id="45861-114">Call the [System.Management.Automation.Cmdlet.Invoke\*](/dotnet/api/System.Management.Automation.Cmdlet.Invoke) method to invoke the `Get-Process` cmdlet.</span></span>

    ```csharp
      foreach (Process p in gp.Invoke<Process>())
      {
        Console.WriteLine(p.ToString());
      }
    }
    ```

## <a name="example"></a><span data-ttu-id="45861-115">Voorbeeld</span><span class="sxs-lookup"><span data-stu-id="45861-115">Example</span></span>

<span data-ttu-id="45861-116">In dit voor beeld wordt de cmdlet `Get-Process` aangeroepen vanuit de methode [System. Management. Automation. cmdlet. BeginProcessing](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing) van een cmdlet.</span><span class="sxs-lookup"><span data-stu-id="45861-116">In this example, the `Get-Process` cmdlet is invoked from within the [System.Management.Automation.Cmdlet.BeginProcessing](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing) method of a cmdlet.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="45861-117">Zie ook</span><span class="sxs-lookup"><span data-stu-id="45861-117">See Also</span></span>

[<span data-ttu-id="45861-118">Een Windows Power shell-cmdlet schrijven</span><span class="sxs-lookup"><span data-stu-id="45861-118">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
