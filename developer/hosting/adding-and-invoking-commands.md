---
title: Toe te voegen en aan te roepen opdrachten | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 62be8432-28c1-4ca2-bcdb-d0350163fa8c
caps.latest.revision: 5
ms.openlocfilehash: 9a01f948c5b474b4f9068030907601543e13cc7e
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62083022"
---
# <a name="adding-and-invoking-commands"></a>Opdrachten toevoegen en aanroepen

Na het maken van een runspace, kunt u Windows PowerShellcommands en scripts toevoegen aan een pijplijn en vervolgens de pijplijn aanroepen synchroon of asynchroon.

## <a name="creating-a-pipeline"></a>Het maken van een pijplijn

 De [System.Management.Automation.Powershell](/dotnet/api/system.management.automation.powershell) klasse biedt verschillende methoden voor het toevoegen van opdrachten, parameters en scripts aan de pijplijn. U kunt de pijplijn synchroon aanroepen door het aanroepen van een overbelasting van de [System.Management.Automation.Powershell.Invoke*](/dotnet/api/System.Management.Automation.PowerShell.Invoke) methode, of asynchroon door het aanroepen van een overbelasting van de [ System.Management.Automation.Powershell.Begininvoke*](/dotnet/api/System.Management.Automation.PowerShell.BeginInvoke) en vervolgens de [System.Management.Automation.Powershell.Endinvoke*](/dotnet/api/System.Management.Automation.PowerShell.EndInvoke) methode.

### <a name="addcommand"></a>AddCommand

1. Maak een [System.Management.Automation.Powershell](/dotnet/api/system.management.automation.powershell) object.

   ```csharp
   PowerShell ps = PowerShell.Create();
   ```

2. Voeg de opdracht die u wilt uitvoeren.

   ```csharp
   ps.AddCommand("Get-Process");
   ```

3. De opdracht aanroepen.

   ```csharp
   ps.Invoke();
   ```

 Als u de [System.Management.Automation.Powershell.Addcommand*](/dotnet/api/System.Management.Automation.PowerShell.AddCommand) methode meer dan één keer voordat u contact opneemt met de [System.Management.Automation.Powershell.Invoke*](/dotnet/api/System.Management.Automation.PowerShell.Invoke) methode, het resultaat van de eerste opdracht wordt doorgegeven naar de tweede, enzovoort. Als u niet doorgeven van het resultaat van een vorige opdracht op een opdracht wilt, toevoegen door het aanroepen van de [System.Management.Automation.Powershell.Addstatement*](/dotnet/api/System.Management.Automation.PowerShell.AddStatement) in plaats daarvan.

### <a name="addparameter"></a>AddParameter

 Het vorige voorbeeld wordt een enkele opdracht zonder parameters uitgevoerd. U kunt parameters toevoegen aan de opdracht met behulp van de [System.Management.Automation.Pscommand.Addparameter*](/dotnet/api/System.Management.Automation.PSCommand.AddParameter) methode bijvoorbeeld de volgende code verkrijgt u een lijst met alle van de processen die zijn met de naam `PowerShell` die worden uitgevoerd op de machine.

```csharp
PowerShell.Create().AddCommand("Get-Process")
                   .AddParameter("Name", "PowerShell")
                   .Invoke();
```

 U kunt extra parameters toevoegen door het aanroepen van [System.Management.Automation.Pscommand.Addparameter*](/dotnet/api/System.Management.Automation.PSCommand.AddParameter) herhaaldelijk.

```csharp
PowerShell.Create().AddCommand("Get-Process")
                   .AddParameter("Name", "PowerShell")
                   .AddParameter("Id", "12768")
                   .Invoke();
```

 U kunt ook een woordenlijst met de namen van parameters en waarden toevoegen door het aanroepen van de [System.Management.Automation.Powershell.Addparameters*](/dotnet/api/System.Management.Automation.PowerShell.AddParameters) methode.

```csharp
IDictionary parameters = new Dictionary<String, String>();
parameters.Add("Name", "PowerShell");

parameters.Add("Id", "12768");
PowerShell.Create().AddCommand("Get-Process")
   .AddParameters(parameters)
      .Invoke()

```

### <a name="addstatement"></a>AddStatement

 U kunt simuleren via batchverwerking uitvoeren met behulp van de [System.Management.Automation.Powershell.Addstatement*](/dotnet/api/System.Management.Automation.PowerShell.AddStatement) methode, die een aanvullende instructie toegevoegd aan het einde van de pijplijn die de volgende code verkrijgt u een lijst met actieve processen met de naam `PowerShell`, en vervolgens wordt de lijst met services.

```csharp
PowerShell ps = PowerShell.Create();
ps.AddCommand("Get-Process").AddParameter("Name", "PowerShell");
ps.AddStatement().AddCommand("Get-Service");
ps.Invoke();
```

### <a name="addscript"></a>AddScript

 U kunt een bestaand script uitvoeren door het aanroepen van de [System.Management.Automation.Powershell.Addscript*](/dotnet/api/System.Management.Automation.PowerShell.AddScript) methode. Het volgende voorbeeld wordt een script toegevoegd aan de pijplijn en wordt uitgevoerd. In dit voorbeeld wordt ervan uitgegaan dat er is al een script met de naam `MyScript.ps1` in een map met de naam `D:\PSScripts`.

```csharp
PowerShell ps = PowerShell.Create();
ps.AddScript("D:\PSScripts\MyScript.ps1").Invoke();
```

 Er is ook een versie van de [System.Management.Automation.Powershell.Addscript*](/dotnet/api/System.Management.Automation.PowerShell.AddScript) methode die een Boole-parameter met de naam `useLocalScope`. Als deze parameter is ingesteld op `true`, en vervolgens het script wordt uitgevoerd in de lokale scope. De volgende code wordt het script uitgevoerd in de lokale scope.

```csharp
PowerShell ps = PowerShell.Create();
ps.AddScript(@"D:\PSScripts\MyScript.ps1", true).Invoke();
```

### <a name="invoking-a-pipeline-synchronously"></a>Een pijplijn aanroepen synchroon

 Nadat u elementen aan de pijplijn toevoegen, Roep deze. Voor het aanroepen van de pijplijn synchroon, die u aanroept een overbelasting van de [System.Management.Automation.Powershell.Invoke*](/dotnet/api/System.Management.Automation.PowerShell.Invoke) methode. Het volgende voorbeeld ziet hoe u een pijplijn synchroon kunt aanroepen.

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

### <a name="invoking-a-pipeline-asynchronously"></a>Een pijplijn aanroepen asynchroon

 U asynchroon een pijplijn aanroepen door het aanroepen van een overbelasting van de [System.Management.Automation.Powershell.Begininvoke*](/dotnet/api/System.Management.Automation.PowerShell.BeginInvoke) maken een [IAsyncResult](http://msdn.microsoft.com/library/system.iasyncresult\(v=vs.110\).aspx) -object en klikt u vervolgens aanroepen van de [ System.Management.Automation.Powershell.Endinvoke*](/dotnet/api/System.Management.Automation.PowerShell.EndInvoke) methode.

 Het volgende voorbeeld ziet hoe u een pijplijn asynchroon aanroepen.

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

 [Het maken van een InitialSessionState](./creating-an-initialsessionstate.md)

 [Het maken van een beperkte runspace](./creating-a-constrained-runspace.md)
