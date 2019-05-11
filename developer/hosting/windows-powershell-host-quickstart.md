---
title: Quick Start van Windows PowerShell-Host | Microsoft Docs
ms.custom: ''
ms.date: 09/12/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 5a134b81-bd0c-4e1c-a2f0-9acbe852745a
caps.latest.revision: 9
ms.openlocfilehash: 9a080b6db7416ae6bf65a1b0353e9f17a56cc6c5
ms.sourcegitcommit: 00cf9a99972ce40db7c25b9a3fc6152dec6bddb6
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 04/28/2019
ms.locfileid: "64530618"
---
# <a name="windows-powershell-host-quickstart"></a>Snelstartgids voor Windows PowerShell-hosts

Voor het hosten van Windows PowerShell in uw toepassing, gebruikt u de [System.Management.Automation.PowerShell](/dotnet/api/System.Management.Automation.PowerShell) klasse.
Deze klasse biedt methoden voor het maken van een pijplijn van opdrachten en vervolgens deze opdrachten uitvoeren in een runspace.
De eenvoudigste manier om een hosttoepassing te maken is met de standaard-runspace.
De standaard-runspace bevat alle van de belangrijkste Windows PowerShell-opdrachten.
Als u wilt dat uw toepassing om slechts een subset van de Windows PowerShell-opdrachten zichtbaar te maken, moet u een aangepaste runspace maken.

## <a name="using-the-default-runspace"></a>Met behulp van de standaard-runspace

Als u wilt starten, we gebruiken de standaard-runspace en gebruikt u de methoden van de [System.Management.Automation.PowerShell](/dotnet/api/System.Management.Automation.PowerShell) klasse opdrachten, parameters, instructies en -scripts toevoegen aan een pijplijn.

### <a name="addcommand"></a>AddCommand

U gebruikt de [System.Management.Automation.Powershell.AddCommand](/dotnet/api/System.Management.Automation.PowerShell.AddCommand) methode opdrachten toe te voegen aan de pijplijn.
Stel bijvoorbeeld dat u wilt ophalen van de lijst met actieve processen op de machine.
De manier om uit te voeren met deze opdracht is als volgt.

1. Maak een [System.Management.Automation.PowerShell](/dotnet/api/System.Management.Automation.PowerShell) object.

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

Als u de methode AddCommand meer dan één keer aanroepen voordat u contact opneemt met de [System.Management.Automation.Powershell.Invoke](/dotnet/api/System.Management.Automation.PowerShell.Invoke) methode, het resultaat van de eerste opdracht wordt doorgegeven naar de tweede, enzovoort.
Als u niet doorgeven van het resultaat van een vorige opdracht op een opdracht wilt, toevoegen door het aanroepen van de [System.Management.Automation.Powershell.AddStatement](/dotnet/api/System.Management.Automation.PowerShell.AddStatement) in plaats daarvan.

### <a name="addparameter"></a>AddParameter

Het vorige voorbeeld wordt een enkele opdracht zonder parameters uitgevoerd.
U kunt parameters toevoegen aan de opdracht met behulp van de [System.Management.Automation.PSCommand.AddParameter](/dotnet/api/System.Management.Automation.PSCommand.AddParameter) methode.
Bijvoorbeeld de volgende code verkrijgt u een lijst met alle van de processen die zijn benoemde `PowerShell` uitgevoerd op de machine.

```csharp
PowerShell.Create().AddCommand("Get-Process")
                   .AddParameter("Name", "PowerShell")
                   .Invoke();
```

U kunt extra parameters toevoegen door de methode AddParameter herhaaldelijk aan te roepen.

```csharp
PowerShell.Create().AddCommand("Get-Process")
                   .AddParameter("Name", "PowerShell")
                   .AddParameter("Id", "12768")
                   .Invoke();
```

U kunt ook een woordenlijst met de namen van parameters en waarden toevoegen door het aanroepen van de [System.Management.Automation.PowerShell.AddParameters](/dotnet/api/System.Management.Automation.PowerShell.AddParameters) methode.

```csharp
IDictionary parameters = new Dictionary<String, String>();
parameters.Add("Name", "PowerShell");

parameters.Add("Id", "12768");
PowerShell.Create().AddCommand("Get-Process")
   .AddParameters(parameters)
      .Invoke()

```

### <a name="addstatement"></a>AddStatement

U kunt simuleren via batchverwerking uitvoeren met behulp van de [System.Management.Automation.PowerShell.AddStatement](/dotnet/api/System.Management.Automation.PowerShell.AddStatement) methode, die een aanvullende instructie toegevoegd aan het einde van de pijplijn.
De volgende code verkrijgt u een lijst met actieve processen met de naam van de `PowerShell`, en vervolgens wordt de lijst met services.

```csharp
PowerShell ps = PowerShell.Create();
ps.AddCommand("Get-Process").AddParameter("Name", "PowerShell");
ps.AddStatement().AddCommand("Get-Service");
ps.Invoke();
```

### <a name="addscript"></a>AddScript

U kunt een bestaand script uitvoeren door het aanroepen van de [System.Management.Automation.PowerShell.AddScript](/dotnet/api/System.Management.Automation.PowerShell.AddScript) methode.
Het volgende voorbeeld wordt een script toegevoegd aan de pijplijn en wordt uitgevoerd.
In dit voorbeeld wordt ervan uitgegaan dat er is al een script met de naam `MyScript.ps1` in een map met de naam `D:\PSScripts`.

```csharp
PowerShell ps = PowerShell.Create();
ps.AddScript("D:\PSScripts\MyScript.ps1").Invoke();
```

Er is ook een versie van de methode voor toevoegen script waarmee een Boole-parameter met de naam `useLocalScope`.
Als deze parameter is ingesteld op `true`, en vervolgens het script wordt uitgevoerd in de lokale scope.
De volgende code wordt het script uitgevoerd in de lokale scope.

```csharp
PowerShell ps = PowerShell.Create();
ps.AddScript(@"D:\PSScripts\MyScript.ps1", true).Invoke();
```

## <a name="creating-a-custom-runspace"></a>Het maken van een aangepaste runspace

Terwijl de standaard-runspace gebruikt in de vorige voorbeelden wordt geladen van de belangrijkste Windows PowerShell-opdrachten, kunt u een aangepaste runspace die alleen een subverzameling van alle opdrachten laadt.
U kunt dit wilt doen voor betere prestaties (het laden van een groter aantal opdrachten is een treffer prestaties), of om te beperken van de mogelijkheid van de gebruiker bewerkingen uit te voeren.
Een runspace dat slechts een beperkt aantal opdrachten wordt een beperkte runspace genoemd.
Voor het maken van een beperkte runspace die u gebruikt de [System.Management.Automation.Runspaces.Runspace](/dotnet/api/System.Management.Automation.Runspaces.Runspace) en [System.Management.Automation.Runspaces.InitialSessionState](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState) klassen.

### <a name="creating-an-initialsessionstate-object"></a>Het maken van een object InitialSessionState

Voor het maken van een aangepaste runspace, moet u eerst maken een [System.Management.Automation.Runspaces.InitialSessionState](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState) object.
In het volgende voorbeeld gebruiken we de [System.Management.Automation.Runspaces.RunspaceFactory](/dotnet/api/System.Management.Automation.Runspaces.RunspaceFactory) te maken van een runspace na het maken van een standaard InitialSessionState-object.

```csharp
InitialSessionState iss = InitialSessionState.CreateDefault();
Runspace rs = RunspaceFactory.CreateRunspace(iss);
rs.Open();
PowerShell ps = PowerShell.Create();
ps.Runspace = rs;
ps.AddCommand("Get-Command");
ps.Invoke();
```

### <a name="constraining-the-runspace"></a>Beperken van de runspace

In het vorige voorbeeld, er een standaard gemaakt [System.Management.Automation.Runspaces.InitialSessionState](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState) -object dat alle van de ingebouwde Windows PowerShell-kern geladen.
Er kan ook zijn met de naam de [System.Management.Automation.Runspaces.InitialSessionState.CreateDefault2](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState.CreateDefault2) methode voor het maken van een InitialSessionState-object dat alleen de opdrachten in de Microsoft.PowerShell.Core zou laden de module.
Voor het maken van een meer beperkte runspace, moet u een lege InitialSessionState-object maken door het aanroepen van de [System.Management.Automation.Runspaces.InitialSessionState.Create](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState.Create) methode, en voeg deze opdrachten de InitialSessionState.

Met behulp van een runspace dat alleen de opdrachten die u opgeeft wordt geladen biedt aanzienlijk betere prestaties.

U gebruikt de methoden van de [System.Management.Automation.Runspaces.SessionStateCmdletEntry](/dotnet/api/System.Management.Automation.Runspaces.SessionStateCmdletEntry) klasse voor het definiëren van de cmdlets voor de eerste sessiestatus.
In het volgende voorbeeld maakt u een lege initiële sessiestatus, vervolgens definieert en voegt de `Get-Command` en `Import-Module` opdrachten naar de sessiestatus van de eerste.
We maken een runspace beperkt door die staat voor de eerste sessie, en voert u de opdrachten in deze runspace.

Status van de eerste sessie maken.

```csharp
InitialSessionState iss = InitialSessionState.Create();
```

Definieer en opdrachten toegevoegd voor de eerste sessiestatus.

```csharp
SessionStateCmdletEntry getCommand = new SessionStateCmdletEntry(
        "Get-Command", typeof(Microsoft.PowerShell.Commands.GetCommandCommand), "");
SessionStateCmdletEntry importModule = new SessionStateCmdletEntry(
        "Import-Module", typeof(Microsoft.PowerShell.Commands.ImportModuleCommand), "");
iss.Commands.Add(getCommand);
iss.Commands.Add(importModule);
```

Maak en open de runspace.

```csharp
Runspace rs = RunspaceFactory.CreateRunspace(iss);
rs.Open();
```

Een opdracht uitvoeren en het resultaat weergegeven.

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

Wanneer uitvoert, ziet de uitvoer van deze code als volgt.

```powershell
Get-Command
Import-Module
```
