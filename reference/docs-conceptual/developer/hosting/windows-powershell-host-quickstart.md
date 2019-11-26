---
title: Snelstartgids voor Windows Power shell-host | Microsoft Docs
ms.custom: ''
ms.date: 09/12/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 5a134b81-bd0c-4e1c-a2f0-9acbe852745a
caps.latest.revision: 9
ms.openlocfilehash: 390eb2d0153c65967d8c0711c852aa6e13fe4660
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/15/2019
ms.locfileid: "72352988"
---
# <a name="windows-powershell-host-quickstart"></a>Snelstartgids voor Windows PowerShell-hosts

Als u Windows Power shell in uw toepassing wilt hosten, gebruikt u de klasse [System. Management. Automation. Power shell](/dotnet/api/System.Management.Automation.PowerShell) .
Deze klasse biedt methoden die een pijp lijn van opdrachten maken en die opdrachten vervolgens uitvoeren in een runs Pace.
De eenvoudigste manier om een hosttoepassing te maken, is door de standaard runs Pace te gebruiken.
De standaard runs Pace bevat alle kern opdrachten van Windows Power shell.
Als u wilt dat uw toepassing slechts een subset van de Windows Power shell-opdrachten weergeeft, moet u een aangepaste runs Pace maken.

## <a name="using-the-default-runspace"></a>De standaard runs Pace gebruiken

We gebruiken de standaard runs Pace en gebruiken de methoden van de klasse [System. Management. Automation. Power shell](/dotnet/api/System.Management.Automation.PowerShell) om opdrachten, para meters, instructies en scripts toe te voegen aan een pijp lijn.

### <a name="addcommand"></a>AddCommand

U gebruikt de methode [System. Management. Automation. Power shell. AddCommand](/dotnet/api/System.Management.Automation.PowerShell.AddCommand) om opdrachten toe te voegen aan de pijp lijn.
Stel bijvoorbeeld dat u de lijst met actieve processen op de computer wilt ophalen.
De manier om deze opdracht uit te voeren, is als volgt.

1. Maak een [System. Management. Automation. Power shell](/dotnet/api/System.Management.Automation.PowerShell) -object.

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

Als u de AddCommand-methode meer dan één keer aanroept voordat u de methode [System. Management. Automation. Power shell. Invoke](/dotnet/api/System.Management.Automation.PowerShell.Invoke) aanroept, wordt het resultaat van de eerste opdracht naar het tweede gepiped, enzovoort.
Als u niet wilt dat het resultaat van een vorige opdracht naar een opdracht wordt geleid, voegt u dit toe door het aanroepen van [System. Management. Automation. Power shell. AddStatement](/dotnet/api/System.Management.Automation.PowerShell.AddStatement) in plaats daarvan.

### <a name="addparameter"></a>AddParameter

In het vorige voor beeld wordt één opdracht zonder para meters uitgevoerd.
U kunt para meters toevoegen aan de opdracht met behulp van de methode [System. Management. Automation. PSCommand. AddParameter](/dotnet/api/System.Management.Automation.PSCommand.AddParameter) .
Met de volgende code wordt bijvoorbeeld een lijst opgehaald van alle processen met de naam `PowerShell` die op de computer wordt uitgevoerd.

```csharp
PowerShell.Create().AddCommand("Get-Process")
                   .AddParameter("Name", "PowerShell")
                   .Invoke();
```

U kunt aanvullende para meters toevoegen door de methode AddParameter herhaaldelijk aan te roepen.

```csharp                   
PowerShell.Create().AddCommand("Get-ChildItem")
                   .AddParameter("Path", @"c:\Windows")
                   .AddParameter("Filter", "*.exe")
                   .Invoke();
```

U kunt ook een woorden lijst met parameter namen en-waarden toevoegen door de methode [System. Management. Automation. Power shell. AddParameters](/dotnet/api/System.Management.Automation.PowerShell.AddParameters) aan te roepen.

```csharp
IDictionary parameters = new Dictionary<String, String>();
parameters.Add("Path", @"c:\Windows");
parameters.Add("Filter", "*.exe");

PowerShell.Create().AddCommand("Get-Process")
   .AddParameters(parameters)
      .Invoke()

```

### <a name="addstatement"></a>AddStatement

U kunt batching simuleren met behulp van de methode [System. Management. Automation. Power shell. AddStatement](/dotnet/api/System.Management.Automation.PowerShell.AddStatement) , waarmee een extra instructie wordt toegevoegd aan het einde van de pijp lijn.
Met de volgende code wordt een lijst met actieve processen met de naam `PowerShell` opgehaald en wordt vervolgens de lijst met actieve services opgehaald.

```csharp
PowerShell ps = PowerShell.Create();
ps.AddCommand("Get-Process").AddParameter("Name", "PowerShell");
ps.AddStatement().AddCommand("Get-Service");
ps.Invoke();
```

### <a name="addscript"></a>AddScript

U kunt een bestaand script uitvoeren door de methode [System. Management. Automation. Power shell. AddScript](/dotnet/api/System.Management.Automation.PowerShell.AddScript) aan te roepen.
In het volgende voor beeld wordt een script aan de pijp lijn toegevoegd en uitgevoerd.
In dit voor beeld wordt ervan uitgegaan dat er al een script met de naam `MyScript.ps1` is in een map met de naam `D:\PSScripts`.

```csharp
PowerShell ps = PowerShell.Create();
ps.AddScript("D:\PSScripts\MyScript.ps1").Invoke();
```

Er is ook een versie van de methode AddScript die een Boole-para meter met de naam `useLocalScope` gebruikt.
Als deze para meter is ingesteld op `true`, wordt het script uitgevoerd in het lokale bereik.
Met de volgende code wordt het script uitgevoerd in het lokale bereik.

```csharp
PowerShell ps = PowerShell.Create();
ps.AddScript(@"D:\PSScripts\MyScript.ps1", true).Invoke();
```

## <a name="creating-a-custom-runspace"></a>Een aangepaste runs Pace maken

Hoewel de standaard runs Pace die in de vorige voor beelden wordt gebruikt, alle kern opdrachten van Windows Power shell laden, kunt u een aangepaste runs Pace maken waarmee alleen een opgegeven subset van alle opdrachten wordt geladen.
U kunt dit doen om de prestaties te verbeteren (het laden van een groter aantal opdrachten is een prestatie treffer), of om de functionaliteit van de gebruiker te beperken om bewerkingen uit te voeren.
Een runs Pace waarmee slechts een beperkt aantal opdrachten wordt weer gegeven, wordt een beperkte runs Pace genoemd.
Als u een beperkte runs Pace wilt maken, gebruikt u de klassen [System. Management. Automation. Runspaces. runs Pace](/dotnet/api/System.Management.Automation.Runspaces.Runspace) en [System. Management. Automation. Runspaces. InitialSessionState](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState) .

### <a name="creating-an-initialsessionstate-object"></a>Een InitialSessionState-object maken

Als u een aangepaste runs Pace wilt maken, moet u eerst een [System. Management. Automation. Runspaces. InitialSessionState](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState) -object maken.
In het volgende voor beeld gebruiken we [System. Management. Automation. Runspaces. RunspaceFactory](/dotnet/api/System.Management.Automation.Runspaces.RunspaceFactory) om een runs Pace te maken na het maken van een standaard InitialSessionState-object.

```csharp
InitialSessionState iss = InitialSessionState.CreateDefault();
Runspace rs = RunspaceFactory.CreateRunspace(iss);
rs.Open();
PowerShell ps = PowerShell.Create();
ps.Runspace = rs;
ps.AddCommand("Get-Command");
ps.Invoke();
```

### <a name="constraining-the-runspace"></a>De runs Pace beperken

In het vorige voor beeld is een standaard [System. Management. Automation. Runspaces. InitialSessionState](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState) -object gemaakt dat alle ingebouwde kernen van Windows Power shell laadt.
We hebben ook de methode [System. Management. Automation. Runspaces. InitialSessionState. CreateDefault2](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState.CreateDefault2) aangeroepen om een InitialSessionState-object te maken dat alleen de opdrachten in de module micro soft. Power shell. Core zou laden.
Als u een meer beperkte runs Pace wilt maken, moet u een leeg InitialSessionState-object maken door de methode [System. Management. Automation. Runspaces. InitialSessionState. Create](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState.Create) aan te roepen en vervolgens opdrachten toe te voegen aan de InitialSessionState.

Het gebruik van een runs Pace waarmee alleen de door u opgegeven opdrachten worden geladen, levert aanzienlijk betere prestaties.

U gebruikt de methoden van de klasse [System. Management. Automation. Runspaces. SessionStateCmdletEntry](/dotnet/api/System.Management.Automation.Runspaces.SessionStateCmdletEntry) om cmdlets te definiëren voor de oorspronkelijke sessie status.
In het volgende voor beeld wordt een lege begin sessie status gemaakt. vervolgens worden de opdrachten `Get-Command` en `Import-Module` gedefinieerd en toegevoegd aan de eerste sessie status.
Vervolgens maken we een runs Pace die is beperkt door de eerste sessie status en voert u de opdrachten in die runs Pace uit.

Maak de eerste sessie status.

```csharp
InitialSessionState iss = InitialSessionState.Create();
```

Definieer en voeg opdrachten toe aan de eerste sessie status.

```csharp
SessionStateCmdletEntry getCommand = new SessionStateCmdletEntry(
        "Get-Command", typeof(Microsoft.PowerShell.Commands.GetCommandCommand), "");
SessionStateCmdletEntry importModule = new SessionStateCmdletEntry(
        "Import-Module", typeof(Microsoft.PowerShell.Commands.ImportModuleCommand), "");
iss.Commands.Add(getCommand);
iss.Commands.Add(importModule);
```

Maak de runs Pace en open deze.

```csharp
Runspace rs = RunspaceFactory.CreateRunspace(iss);
rs.Open();
```

Een opdracht uitvoeren en het resultaat weer geven.

```csharp
PowerShell ps = PowerShell.Create();
ps.Runspace = rs;
ps.AddCommand("Get-Command");
Collection<CommandInfo> result = ps.Invoke<CommandInfo>();
foreach (var entry in result)
{
       Console.WriteLine(entry.Name);
}
```

Wanneer u deze uitvoert, ziet de uitvoer van deze code er als volgt uit.

```powershell
Get-Command
Import-Module
```