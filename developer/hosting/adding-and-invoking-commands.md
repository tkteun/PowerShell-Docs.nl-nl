---
title: Opdrachten toevoegen en aanroepen | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 62be8432-28c1-4ca2-bcdb-d0350163fa8c
caps.latest.revision: 5
ms.openlocfilehash: f776f13fe743a3f5f67de0d94883e3f754040ffc
ms.sourcegitcommit: 4a2cf30351620a58ba95ff5d76b247e601907589
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 09/27/2019
ms.locfileid: "71323486"
---
# <a name="adding-and-invoking-commands"></a>Opdrachten toevoegen en aanroepen

Nadat u een runs Pace hebt gemaakt, kunt u Windows-PowerShellcommands en-scripts toevoegen aan een pijp lijn en vervolgens de pijp lijn synchroon of asynchroon aanroepen.

## <a name="creating-a-pipeline"></a>Een pijp lijn maken

 De klasse [System. Management. Automation. Power shell](/dotnet/api/system.management.automation.powershell) biedt verschillende methoden om opdrachten, para meters en scripts toe te voegen aan de pijp lijn. U kunt de pijp lijn synchroon aanroepen door het aanroepen van een overbelasting van de methode [System. Management. Automation. Power shell. Invoke *](/dotnet/api/System.Management.Automation.PowerShell.Invoke) of asynchroon door het aanroepen van een overbelasting van [System. Management. Automation. Power shell. BeginInvoke *](/dotnet/api/System.Management.Automation.PowerShell.BeginInvoke) en vervolgens de methode [System. Management. Automation. Power shell. Endinvoke *](/dotnet/api/System.Management.Automation.PowerShell.EndInvoke) .

### <a name="addcommand"></a>AddCommand

1. Maak een [System. Management. Automation. Power shell](/dotnet/api/system.management.automation.powershell) -object.

   ```csharp
   PowerShell ps = PowerShell.Create();
   ```

2. Voeg de opdracht toe die u wilt uitvoeren.

   ```csharp
   ps.AddCommand("Get-Process");
   ```

3. Roep de opdracht aan.

   ```csharp
   ps.Invoke();
   ```

 Als u de methode [System. Management. Automation. Power shell. Addcommand *](/dotnet/api/System.Management.Automation.PowerShell.AddCommand) meer dan eens aanroept voordat u de methode [System. Management. Automation. Power shell. Invoke *](/dotnet/api/System.Management.Automation.PowerShell.Invoke) aanroept, wordt het resultaat van de eerste opdracht naar de tweede, enzovoort. Als u het resultaat van een vorige opdracht niet wilt door geven aan een opdracht, voegt u dit toe door het aanroepen van [System. Management. Automation. Power shell. Addstatement *](/dotnet/api/System.Management.Automation.PowerShell.AddStatement) in plaats daarvan.

### <a name="addparameter"></a>AddParameter

 In het vorige voor beeld wordt één opdracht zonder para meters uitgevoerd. U kunt para meters toevoegen aan de opdracht met behulp van de methode [System. Management. Automation. Pscommand. Addparameter *](/dotnet/api/System.Management.Automation.PSCommand.AddParameter) . de volgende code haalt een lijst op met alle processen die `PowerShell` worden uitgevoerd op de computer.

```csharp
PowerShell.Create().AddCommand("Get-Process")
                   .AddParameter("Name", "PowerShell")
                   .Invoke();
```

 U kunt aanvullende para meters toevoegen door [System. Management. Automation. Pscommand. Addparameter *](/dotnet/api/System.Management.Automation.PSCommand.AddParameter) herhaaldelijk aan te roepen.

```csharp
PowerShell.Create().AddCommand("Get-Process")
                   .AddParameter("Name", "PowerShell")
                   .AddParameter("Id", "12768")
                   .Invoke();
```

 U kunt ook een woorden lijst met parameter namen en-waarden toevoegen door de methode [System. Management. Automation. Power shell. AddParameters *](/dotnet/api/System.Management.Automation.PowerShell.AddParameters) aan te roepen.

```csharp
IDictionary parameters = new Dictionary<String, String>();
parameters.Add("Name", "PowerShell");

parameters.Add("Id", "12768");
PowerShell.Create().AddCommand("Get-Process")
   .AddParameters(parameters)
      .Invoke()

```

### <a name="addstatement"></a>AddStatement

 U kunt batching simuleren met behulp van de methode [System. Management. Automation. Power shell. Addstatement *](/dotnet/api/System.Management.Automation.PowerShell.AddStatement) , waarmee een extra instructie aan het einde van de pijp lijn wordt toegevoegd met de volgende code wordt een lijst `PowerShell`met actieve processen met de naam opgehaald en vervolgens wordt de lijst met actieve services opgehaald.

```csharp
PowerShell ps = PowerShell.Create();
ps.AddCommand("Get-Process").AddParameter("Name", "PowerShell");
ps.AddStatement().AddCommand("Get-Service");
ps.Invoke();
```

### <a name="addscript"></a>AddScript

 U kunt een bestaand script uitvoeren door de methode [System. Management. Automation. Power shell. addScript *](/dotnet/api/System.Management.Automation.PowerShell.AddScript) aan te roepen. In het volgende voor beeld wordt een script aan de pijp lijn toegevoegd en uitgevoerd. `MyScript.ps1` In dit voor beeld wordt ervan uitgegaan dat er al een script met `D:\PSScripts`de naam in een map wordt genoemd.

```csharp
PowerShell ps = PowerShell.Create();
ps.AddScript("D:\PSScripts\MyScript.ps1").Invoke();
```

 Er is ook een versie van de methode [System. Management. Automation. Power shell. addScript *](/dotnet/api/System.Management.Automation.PowerShell.AddScript) die een Boole- `useLocalScope`para meter met de naam heeft. Als deze para meter is ingesteld `true`op, wordt het script uitgevoerd in het lokale bereik. Met de volgende code wordt het script uitgevoerd in het lokale bereik.

```csharp
PowerShell ps = PowerShell.Create();
ps.AddScript(@"D:\PSScripts\MyScript.ps1", true).Invoke();
```

### <a name="invoking-a-pipeline-synchronously"></a>Een pijp lijn synchroon aanroepen

 Nadat u elementen aan de pijp lijn hebt toegevoegd, kunt u deze aanroepen. Als u de pijp lijn synchroon wilt aanroepen, roept u een overbelasting aan van de methode [System. Management. Automation. Power shell. Invoke *](/dotnet/api/System.Management.Automation.PowerShell.Invoke) . In het volgende voor beeld ziet u hoe u een pijp lijn synchroon kunt aanroepen.

```csharp
using System;
using System.Collections.Generic;
using System.Linq;
using System.Text;
using System.Management.Automation;

namespace HostPS1e
{
  class HostPS1e
  {
    static void Main(string[] args)
    {
      // Using the PowerShell.Create and AddCommand
      // methods, create a command pipeline.
      PowerShell ps = PowerShell.Create().AddCommand ("Sort-Object");

      // Using the PowerShell.Invoke method, run the command
      // pipeline using the supplied input.
      foreach (PSObject result in ps.Invoke(new int[] { 3, 1, 6, 2, 5, 4 }))
      {
          Console.WriteLine("{0}", result);
      } // End foreach.
    } // End Main.
  } // End HostPS1e.
}
```

### <a name="invoking-a-pipeline-asynchronously"></a>Een pijp lijn asynchroon aanroepen

 U roept een pijp lijn asynchroon aan door een overbelasting van [System. Management. Automation. Power shell. BeginInvoke *](/dotnet/api/System.Management.Automation.PowerShell.BeginInvoke) aan te roepen om een object [IAsyncResult](https://msdn.microsoft.com/library/system.iasyncresult\(v=vs.110\).aspx) te maken, en vervolgens de [System. Management. Automation. Power shell. Endinvoke aan te roepen. *](/dotnet/api/System.Management.Automation.PowerShell.EndInvoke) -methode.

 In het volgende voor beeld ziet u hoe u een pijp lijn asynchroon aanroept.

```csharp
using System;
using System.Collections.Generic;
using System.Linq;
using System.Text;
using System.Management.Automation;

namespace HostPS3
{
  class HostPS3
  {
    static void Main(string[] args)
    {
      // Use the PowerShell.Create and PowerShell.AddCommand
      // methods to create a command pipeline that includes
      // Get-Process cmdlet. Do not include spaces immediately
      // before or after the cmdlet name as that will cause
      // the command to fail.
      PowerShell ps = PowerShell.Create().AddCommand("Get-Process");

      // Create an IAsyncResult object and call the
      // BeginInvoke method to start running the
      // command pipeline asynchronously.
      IAsyncResult async = ps.BeginInvoke();

      // Using the PowerShell.Invoke method, run the command
      // pipeline using the default runspace.
      foreach (PSObject result in ps.EndInvoke(async))
      {
        Console.WriteLine("{0,-20}{1}",
                result.Members["ProcessName"].Value,
                result.Members["Id"].Value);
      } // End foreach.
      System.Console.WriteLine("Hit any key to exit.");
      System.Console.ReadKey();
    } // End Main.
  } // End HostPS3.
}
```

## <a name="see-also"></a>Zie ook

 [Een InitialSessionState maken](./creating-an-initialsessionstate.md)

 [Een beperkte runs Pace maken](./creating-a-constrained-runspace.md)
