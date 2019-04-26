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
# <a name="how-to-invoke-a-cmdlet-from-within-a-cmdlet"></a>Een cmdlet aanroepen vanuit een cmdlet

In dit voorbeeld laat zien hoe aanroepen van een cmdlet uit binnen een andere cmdlet, zodat u kunt de functionaliteit van de cmdlet aangeroepen toevoegen aan de cmdlet die u ontwikkelt. In dit voorbeeld wordt de `Get-Process` cmdlet wordt aangeroepen om de processen die worden uitgevoerd op de lokale computer. De aanroep van de `Get-Process` cmdlet komt overeen met de volgende opdracht. Deze opdracht worden alle processen waarvan de namen met de tekens beginnen "a" tot "t" opgehaald.

```powershell
Get-Process -name [a-t]
```

> [!IMPORTANT]
> U kunt aanroepen alleen die cmdlets die zijn afgeleid rechtstreeks vanuit de [System.Management.Automation.Cmdlet](/dotnet/api/System.Management.Automation.Cmdlet) klasse. U kunt geen aanroepen een cmdlet die is afgeleid van de [System.Management.Automation.PSCmdlet](/dotnet/api/System.Management.Automation.PSCmdlet) klasse.

## <a name="to-invoke-a-cmdlet-from-within-a-cmdlet"></a>Een cmdlet uit binnen een cmdlet aanroepen

1. Zorg ervoor dat er wordt verwezen naar de assembly waarin de cmdlet worden aangeroepen en dat de juiste `using` instructie wordt toegevoegd. In dit voorbeeld worden de volgende naamruimten toegevoegd.

    ```csharp
    using System.Diagnostics;
    using System.Management.Automation;   // Windows PowerShell assembly.
    using Microsoft.PowerShell.Commands;  // Windows PowerShell assembly.
    ```

2. In de invoer-methode van de cmdlet verwerkt, maak een nieuw exemplaar van de cmdlet worden aangeroepen. In dit voorbeeld wordt een object van het type [Microsoft.PowerShell.Commands.Getprocesscommand](/dotnet/api/Microsoft.PowerShell.Commands.GetProcessCommand) wordt gemaakt, samen met de tekenreeks zijn met de argumenten die worden gebruikt wanneer de cmdlet wordt aangeroepen.

    ```csharp
    GetProcessCommand gp = new GetProcessCommand();
    gp.Name = new string[] { "[a-t]*" };
    ```

3. Roep de [System.Management.Automation.Cmdlet.Invoke*](/dotnet/api/System.Management.Automation.Cmdlet.Invoke) aan te roepen methode de `Get-Process` cmdlet.

    ```csharp
      foreach (Process p in gp.Invoke<Process>())
      {
        Console.WriteLine(p.ToString());
      }
    }
    ```

## <a name="example"></a>Voorbeeld

In dit voorbeeld wordt de `Get-Process` cmdlet wordt aangeroepen vanuit de [System.Management.Automation.Cmdlet.BeginProcessing](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing) methode van een cmdlet.

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

[Schrijven van een Windows PowerShell-Cmdlet](./writing-a-windows-powershell-cmdlet.md)
