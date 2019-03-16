---
title: Berichten van de gebruiker toe te voegen aan uw Cmdlet | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- WriteWarning
- notifications, writing
- progress notification
- WriteVerbose
- Stop-Proc
- WriteProgress
- WriteDebug
- notifications, debug
- ProgressRecord
- samples, Stop-Proc cmdlet
- notifications, progress
- notifications, warning
- WriteObject
- WriteError
- verbose notification
- ProcessRecord
- notifications, verbose
- debug notification
- cmdlet, writing notifications
- warning
- code sample, user notifications
- user notifications
ms.assetid: 14c13acb-f0b7-4613-bc7d-c361d14da1a2
caps.latest.revision: 8
ms.openlocfilehash: 5b3a5f5d5d02c7d5a3c1d622ec1a3740739c694f
ms.sourcegitcommit: caac7d098a448232304c9d6728e7340ec7517a71
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 03/16/2019
ms.locfileid: "58055033"
---
# <a name="adding-user-messages-to-your-cmdlet"></a>Gebruikersberichten toevoegen aan uw cmdlet

Cmdlets kunt schrijven die verschillende soorten berichten die door de Windows PowerShell-runtime voor de gebruiker kunnen worden weergegeven. Deze berichten zijn onder andere de volgende typen:

- Uitgebreide berichten waarin algemene informatie.

- Fouten opsporen in berichten die informatie over probleemoplossing bevatten.

- Waarschuwingsberichten die bevatten een melding dat de cmdlet wordt een bewerking waarvoor kan onverwachte resultaten.

- Voortgangsrapport berichten die informatie over hoeveel bevatten werken de cmdlet is voltooid bij het uitvoeren van een bewerking die lange tijd in beslag neemt.

Er zijn geen beperkingen op het aantal berichten dat uw cmdlet kan schrijven of het type berichten die uw cmdlet schrijft. Elk bericht is geschreven door een specifieke aanroep uit binnen de invoer-methode van de cmdlet verwerkt.

## <a name="the-stopproc-cmdlet"></a>De StopProc Cmdlet

Onderwerpen in deze sectie bevatten het volgende:

- [De Cmdlet definiëren](#Defining-the-Cmdlet)

- [Parameters voor aanpassing van het systeem definiëren](#Defining-Parameters-for-System-Modification)

- [Invoer verwerken methode te overschrijven](#Overriding-an-Input-Processing-Method)

- [Een uitgebreid bericht schrijven](#Writing-a-Verbose-Message)

- [Geen foutopsporingsbericht schrijven](#Writing-a-Debug-Message)

- [Schrijven van een waarschuwingsbericht wordt weergegeven](#Writing-a-Warning-Message)

- [Schrijven van een bericht wordt uitgevoerd](#Writing-a-Progress-Message)

- [Voorbeeld van code](#Code-Sample)

- [Definieer objecttypen en opmaak](#Define-Object-Types-and-Formatting)

- [Het bouwen van de Cmdlet](#Building-the-Cmdlet)

- [Testen van de Cmdlet](#Testing-the-Cmdlet)

## <a name="defining-the-cmdlet"></a>De Cmdlet definiëren

De eerste stap bij het maken van de cmdlet is altijd naamgeving van de cmdlet en de .NET-klasse die de cmdlet declareren. Een of andere vorm van cmdlet kunt meldingen voor gebruikers van de verwerking van methoden; invoer schrijven dus in het algemeen kunt u naam deze cmdlet met behulp van een bewerking die aangeeft welke system wijzigingen die de cmdlet uitvoert. Zie voor meer informatie over goedgekeurde werkwoorden [namen van de term cmdlets](./approved-verbs-for-windows-powershell-commands.md).

De cmdlet Stop-Proc is ontworpen om te wijzigen van het systeem. daarom de [System.Management.Automation.CmdletAttribute](/dotnet/api/System.Management.Automation.CmdletAttribute) -declaratie voor de .NET-klasse moet bevatten de `SupportsShouldProcess` sleutelwoord kenmerk hebben en worden ingesteld op `true`.

De volgende code is de definitie voor deze cmdlet Stop-Proc klasse. Zie voor meer informatie over deze definitie [maken van een Cmdlet die Hiermee wijzigt u het systeem](./creating-a-cmdlet-that-modifies-the-system.md).

```csharp
[Cmdlet(VerbsLifecycle.Stop, "proc",
        SupportsShouldProcess = true)]
public class StopProcCommand : Cmdlet
```

## <a name="defining-parameters-for-system-modification"></a>Parameters voor aanpassing van het systeem definiëren

De cmdlet Stop-Proc definieert drie parameters: `Name`, `Force`, en `PassThru`. Zie voor meer informatie over het definiëren van deze parameters [maken van een Cmdlet die Hiermee wijzigt u het systeem](./creating-a-cmdlet-that-modifies-the-system.md).

Hier is de parameterdeclaratie voor de cmdlet Stop-Proc.

```csharp
[Parameter(
           Position = 0,
           Mandatory = true,
           ValueFromPipeline = true,
           ValueFromPipelineByPropertyName = true
)]
public string[] Name
{
  get { return processNames; }
  set { processNames = value; }
}
private string[] processNames;

/// <summary>
/// Specify the Force parameter that allows the user to override
/// the ShouldContinue call to force the stop operation. This
/// parameter should always be used with caution.
/// </summary>
[Parameter]
public SwitchParameter Force
{
  get { return force; }
  set { force = value; }
}
private bool force;

/// <summary>
/// Specify the PassThru parameter that allows the user to specify
/// that the cmdlet should pass the process object down the pipeline
/// after the process has been stopped.
/// </summary>
[Parameter]
public SwitchParameter PassThru
{
  get { return passThru; }
  set { passThru = value; }
}
private bool passThru;
```

## <a name="overriding-an-input-processing-method"></a>Invoer verwerken methode te overschrijven

De cmdlet moet verwerken van methode invoer overschrijven, meestal worden [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord). Deze cmdlet Stop-Proc overschrijft de [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) invoermethode voor verwerking. In deze implementatie van de cmdlet Stop-Proc worden aangeroepen om uitgebreide berichten, Foutopsporingsberichten en waarschuwingen te schrijven.

> [!NOTE]
> Voor meer informatie over hoe deze methode roept de [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) en [System.Management.Automation.Cmdlet.ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) methoden, Zie [Maken van een Cmdlet die Hiermee wijzigt u het systeem](./creating-a-cmdlet-that-modifies-the-system.md).

## <a name="writing-a-verbose-message"></a>Een uitgebreid bericht schrijven

De [System.Management.Automation.Cmdlet.WriteVerbose](/dotnet/api/System.Management.Automation.Cmdlet.WriteVerbose) methode wordt gebruikt om algemene op gebruikersniveau informatie die is gerelateerd aan bepaalde voorwaarden te schrijven. De systeembeheerder kunt die informatie vervolgens gebruiken om door te gaan met het verwerken van andere opdrachten. Alle gegevens die zijn geschreven met deze methode moet bovendien zo nodig worden gelokaliseerd.

De volgende code uit deze cmdlet Stop-Proc toont twee verzoeken aan de [System.Management.Automation.Cmdlet.WriteVerbose](/dotnet/api/System.Management.Automation.Cmdlet.WriteVerbose) methode van de onderdrukking van de [System.Management.Automation.Cmdlet.ProcessRecord ](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) methode.

```csharp
message = String.Format("Attempting to stop process \"{0}\".", name);
WriteVerbose(message);
```

```csharp
message = String.Format("Stopped process \"{0}\", pid {1}.",
                        processName, process.Id);

WriteVerbose(message);
```

## <a name="writing-a-debug-message"></a>Geen foutopsporingsbericht schrijven

De [System.Management.Automation.Cmdlet.WriteDebug](/dotnet/api/System.Management.Automation.Cmdlet.WriteDebug) methode wordt gebruikt om te schrijven foutopsporingsberichten die kunnen worden gebruikt om op te lossen van de werking van de cmdlet. De aanroep wordt uitgevoerd vanaf een invoer verwerken van methode.

> [!NOTE]
> Windows PowerShell ook definieert een `Debug` parameter geeft beide uitgebreide en informatie voor foutopsporing. Als uw cmdlet biedt ondersteuning voor deze parameter, hoeft deze niet aan te roepen [System.Management.Automation.Cmdlet.WriteDebug](/dotnet/api/System.Management.Automation.Cmdlet.WriteDebug) in dezelfde code die worden aangeroepen [System.Management.Automation.Cmdlet.WriteVerbose](/dotnet/api/System.Management.Automation.Cmdlet.WriteVerbose) .

De volgende twee secties van de code van de voorbeeld-cmdlet Stop-Proc weergeven aanroepen naar de [System.Management.Automation.Cmdlet.WriteDebug](/dotnet/api/System.Management.Automation.Cmdlet.WriteDebug) methode van de onderdrukking van de [ System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) methode.

Dit foutopsporingsbericht wordt geschreven direct vóór de [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) wordt genoemd.

```csharp
message =
          String.Format("Acquired name for pid {0} : \"{1}\"",
                       process.Id, processName);
WriteDebug(message);
```

Dit foutopsporingsbericht wordt geschreven direct vóór de [System.Management.Automation.Cmdlet.WriteObject](/dotnet/api/System.Management.Automation.Cmdlet.WriteObject) wordt genoemd.

```csharp
message =
         String.Format("Writing process \"{0}\" to pipeline",
         processName);
WriteDebug(message);
WriteObject(process);
```

Windows PowerShell automatisch stuurt een [System.Management.Automation.Cmdlet.WriteDebug](/dotnet/api/System.Management.Automation.Cmdlet.WriteDebug) aanroepen naar de van traceringsinfrastructuur en -cmdlets. Hiermee wordt de methodeaanroepen zonder deze aan de ontwikkeling van extra werk binnen de cmdlet, worden herleid tot de hosttoepassing, een bestand of een foutopsporingsprogramma. De volgende opdrachtregel vermelding implementeert een tracering-bewerking.

**PS > trace-expressie stop-proc-bestand proc.log-opdracht stop-proc Kladblok**

## <a name="writing-a-warning-message"></a>Schrijven van een waarschuwingsbericht wordt weergegeven

De [System.Management.Automation.Cmdlet.WriteWarning](/dotnet/api/System.Management.Automation.Cmdlet.WriteWarning) methode wordt gebruikt voor het schrijven van een waarschuwing wanneer de cmdlet wordt een bewerking die mogelijk een onverwacht resultaat, bijvoorbeeld een alleen-lezen-bestand te overschrijven.

De volgende code uit de voorbeeld-cmdlet Stop-Proc toont het aanroepen van de [System.Management.Automation.Cmdlet.WriteWarning](/dotnet/api/System.Management.Automation.Cmdlet.WriteWarning) methode van de onderdrukking van de [ System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) methode.

```csharp
 if (criticalProcess)
 {
   message =
             String.Format("Stopping the critical process \"{0}\".",
                           processName);
   WriteWarning(message);
} // if (criticalProcess...
```

## <a name="writing-a-progress-message"></a>Schrijven van een bericht wordt uitgevoerd

De [System.Management.Automation.Cmdlet.WriteProgress](/dotnet/api/System.Management.Automation.Cmdlet.WriteProgress) wordt gebruikt voor het schrijven van berichten over de voortgang bij bewerkingen van de cmdlet een uitgebreide hoeveelheid tijd in beslag nemen. Een aanroep van [System.Management.Automation.Cmdlet.WriteProgress](/dotnet/api/System.Management.Automation.Cmdlet.WriteProgress) geeft een [System.Management.Automation.Progressrecord](/dotnet/api/System.Management.Automation.ProgressRecord) -object dat wordt verzonden naar de hosttoepassing voor rendering aan de gebruiker.

> [!NOTE]
> Deze cmdlet Stop-Proc bevat geen een aanroep naar de [System.Management.Automation.Cmdlet.WriteProgress](/dotnet/api/System.Management.Automation.Cmdlet.WriteProgress) methode.

De volgende code is een voorbeeld van een bericht Bezig is geschreven door een cmdlet die probeert een item te kopiëren.

```csharp
int myId = 0;
string myActivity = "Copy-item: Copying *.* to c:\abc";
string myStatus = "Copying file bar.txt";
ProgressRecord pr = new ProgressRecord(myId, myActivity, myStatus);
WriteProgress(pr);

pr.RecordType = ProgressRecordType.Completed;
WriteProgress(pr);
```

## <a name="code-sample"></a>Voorbeeld van code

Voor de volledige C# voorbeeldcode, Zie [StopProcessSample02 voorbeeld](./stopprocesssample02-sample.md).

## <a name="define-object-types-and-formatting"></a>Definieer objecttypen en opmaak

Windows PowerShell wordt informatie doorgegeven tussen cmdlets met behulp van .NET-objecten. Als gevolg daarvan kan een cmdlet mogelijk voor het definiëren van een eigen type of de cmdlet moet mogelijk om uit te breiden van een bestaand type geleverd door een andere cmdlet. Zie voor meer informatie over het definiëren van nieuwe typen of uitbreiden van bestaande typen [objecttypen uitbreiden en opmaak](http://msdn.microsoft.com/en-us/da976d91-a3d6-44e8-affa-466b1e2bd351).

## <a name="building-the-cmdlet"></a>Het bouwen van de Cmdlet

Na de implementatie van een cmdlet, moet deze met Windows PowerShell worden geregistreerd via een Windows PowerShell-module. Zie voor meer informatie over het registreren van cmdlets [hoe u Cmdlets registreren, Providers en hosting van toepassingen](http://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c).

## <a name="testing-the-cmdlet"></a>Testen van de Cmdlet

Wanneer de cmdlet is geregistreerd met Windows PowerShell, kunt u deze testen door te voeren op de opdrachtregel. We gaan de voorbeeld-cmdlet Stop-Proc testen. Zie voor meer informatie over het gebruik van cmdlets vanaf de opdrachtregel de [aan de slag met Windows PowerShell](/powershell/scripting/getting-started/getting-started-with-windows-powershell).

- De volgende vermelding in de opdrachtregel gebruikt Stop-Proc voor het stoppen van het proces met de naam "KLADBLOK", bieden uitgebreide meldingen en gegevens voor foutopsporing afdrukken.

    ```powershell
    PS> stop-proc -Name notepad -Verbose -Debug
    ```

De volgende uitvoer wordt weergegeven.

    ```
    VERBOSE: Attempting to stop process " notepad ".
    DEBUG: Acquired name for pid 5584 : "notepad"

    Confirm
    Continue with this operation?
    [Y] Yes  [A] Yes to All  [H] Halt Command  [S] Suspend  [?] Help (default is "Y"): Y

    Confirm
    Are you sure you want to perform this action?
    Performing operation "stop-proc" on Target "notepad (5584)".
    [Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "Y"): Y
    VERBOSE: Stopped process "notepad", pid 5584.
    ```

## <a name="see-also"></a>Zie ook

[Maken van een Cmdlet die Hiermee wijzigt u het systeem](./creating-a-cmdlet-that-modifies-the-system.md)

[Over het maken van een Windows PowerShell-Cmdlet](http://msdn.microsoft.com/en-us/0d721742-c849-4d0d-964f-78ddd9cd258c)

[Objecttypen uitbreiden en opmaak](http://msdn.microsoft.com/en-us/da976d91-a3d6-44e8-affa-466b1e2bd351)

[Over het registreren van Providers,-Cmdlets en -toepassingen hosten](http://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c)

[Windows PowerShell SDK](../windows-powershell-reference.md)
