---
title: Een cmdlet aanroepen vanuit een cmdlet | Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: 2d5b0788d3310d0dd7b311f86c497afe8eec9d11
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 08/05/2020
ms.locfileid: "87784143"
---
# <a name="how-to-invoke-a-cmdlet-from-within-a-cmdlet"></a>Een cmdlet aanroepen vanuit een cmdlet

In dit voor beeld ziet u hoe u een cmdlet aanroept vanuit een andere cmdlet, waarmee u de functionaliteit van de aangeroepen cmdlet kunt toevoegen aan de cmdlet die u ontwikkelt. In dit voor beeld `Get-Process` wordt de cmdlet aangeroepen om de processen op te halen die worden uitgevoerd op de lokale computer. De aanroep van de `Get-Process` cmdlet is gelijk aan de volgende opdracht. Met deze opdracht worden alle processen opgehaald waarvan de namen beginnen met de tekens a tot en met t.

```powershell
Get-Process -name [a-t]
```

> [!IMPORTANT]
> U kunt alleen de cmdlets aanroepen die rechtstreeks zijn afgeleid van de klasse [System. Management. Automation. cmdlet](/dotnet/api/System.Management.Automation.Cmdlet) . U kunt geen cmdlet aanroepen die is afgeleid van de klasse [System. Management. Automation. PSCmdlet](/dotnet/api/System.Management.Automation.PSCmdlet) .

## <a name="to-invoke-a-cmdlet-from-within-a-cmdlet"></a>Een cmdlet aanroepen vanuit een cmdlet

1. Controleer of de assembly die de cmdlet definieert die moet worden aangeroepen, wordt verwezen en of de juiste `using` instructie is toegevoegd. In dit voor beeld worden de volgende naam ruimten toegevoegd.

    ```csharp
    using System.Diagnostics;
    using System.Management.Automation;   // Windows PowerShell assembly.
    using Microsoft.PowerShell.Commands;  // Windows PowerShell assembly.
    ```

2. Maak in de invoer verwerkings methode van de cmdlet een nieuw exemplaar van de cmdlet die moet worden aangeroepen. In dit voor beeld wordt een object van het type [micro soft. Power shell. commands. Getprocesscommand](/dotnet/api/Microsoft.PowerShell.Commands.GetProcessCommand) gemaakt samen met de teken reeks die de argumenten bevat die worden gebruikt wanneer de cmdlet wordt aangeroepen.

    ```csharp
    GetProcessCommand gp = new GetProcessCommand();
    gp.Name = new string[] { "[a-t]*" };
    ```

3. Roep de methode [System. Management. Automation. cmdlet. Invoke *](/dotnet/api/System.Management.Automation.Cmdlet.Invoke) aan om de cmdlet aan te roepen `Get-Process` .

    ```csharp
      foreach (Process p in gp.Invoke<Process>())
      {
        Console.WriteLine(p.ToString());
      }
    }
    ```

## <a name="example"></a>Voorbeeld

In dit voor beeld `Get-Process` wordt de cmdlet aangeroepen vanuit de methode [System. Management. Automation. cmdlet. BeginProcessing](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing) van een cmdlet.

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

## <a name="see-also"></a>Zie ook

[Een Windows PowerShell-cmdlet schrijven](./writing-a-windows-powershell-cmdlet.md)
