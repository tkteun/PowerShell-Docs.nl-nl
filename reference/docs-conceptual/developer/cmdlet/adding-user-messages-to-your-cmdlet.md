---
title: Gebruikers berichten toevoegen aan de cmdlet | Microsoft Docs
ms.date: 09/13/2016
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
ms.openlocfilehash: 9e324058401bc979d8ac8c23690ca86beaa67fd1
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 08/05/2020
ms.locfileid: "87782460"
---
# <a name="adding-user-messages-to-your-cmdlet"></a>Gebruikersberichten toevoegen aan uw cmdlet

Met cmdlets kunt u verschillende soorten berichten schrijven die kunnen worden weer gegeven aan de gebruiker door de Windows Power shell-runtime. Deze berichten bevatten de volgende typen:

- Uitgebreide berichten die algemene gebruikers informatie bevatten.

- Fouten opsporen in berichten die informatie over het oplossen van problemen bevatten.

- Waarschuwings berichten die een melding bevatten dat de cmdlet een bewerking moet uitvoeren die onverwachte resultaten kan hebben.

- Voortgangs rapport berichten die informatie bevatten over de hoeveelheid werk die de cmdlet heeft voltooid bij het uitvoeren van een bewerking die lange tijd in beslag neemt.

Er zijn geen beperkingen voor het aantal berichten dat door de cmdlet kan worden geschreven of het type berichten dat door de cmdlet wordt geschreven. Elk bericht wordt geschreven door een specifieke aanroep uit te voeren binnen de invoer verwerkings methode van uw cmdlet.

## <a name="defining-the-cmdlet"></a>De cmdlet definiëren

De eerste stap bij het maken van de cmdlet is altijd de naam van de cmdlet en het declareren van de .NET-klasse die de cmdlet implementeert. Elke sorteer-of cmdlet kan gebruikers meldingen schrijven van de invoer methoden. in het algemeen kunt u deze cmdlet een naam gegeven met een wille keurige term die aangeeft welke systeem wijzigingen de cmdlet uitvoert. Zie [cmdlet verb names](./approved-verbs-for-windows-powershell-commands.md)(Engelstalig) voor meer informatie over goedgekeurde cmdlet-termen.

De cmdlet stop-proc is ontworpen om het systeem te wijzigen. Daarom moet de declaratie [System. Management. Automation. CmdletAttribute](/dotnet/api/System.Management.Automation.CmdletAttribute) voor de .net-klasse het `SupportsShouldProcess` sleutel woord attribute bevatten en worden ingesteld op `true` .

De volgende code is de definitie voor deze klasse stop-proc-cmdlet. Zie voor meer informatie over deze definitie [een cmdlet maken die het systeem wijzigt](./creating-a-cmdlet-that-modifies-the-system.md).

```csharp
[Cmdlet(VerbsLifecycle.Stop, "proc",
        SupportsShouldProcess = true)]
public class StopProcCommand : Cmdlet
```

## <a name="defining-parameters-for-system-modification"></a>Para meters definiëren voor systeem wijziging

De cmdlet stop-proc definieert drie para meters: `Name` , `Force` en `PassThru` . Zie [een cmdlet maken die het systeem wijzigt](./creating-a-cmdlet-that-modifies-the-system.md)voor meer informatie over het definiëren van deze para meters.

Dit is de para meter declaratie voor de cmdlet stop-proc.

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

## <a name="overriding-an-input-processing-method"></a>Een invoer verwerkings methode overschrijven

De cmdlet moet een invoer verwerkings methode overschrijven, meestal is [System. Management. Automation. cmdlet. ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord). Deze Stop-proc-cmdlet overschrijft de verwerkings methode [System. Management. Automation. cmdlet. ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) . In deze implementatie van de cmdlet stop-proc worden er aanroepen gedaan om uitgebreide berichten, fout opsporingsgegevens en waarschuwings berichten te schrijven.

> [!NOTE]
> Zie [Creating a cmdlet waarmee het systeem wordt gewijzigd](./creating-a-cmdlet-that-modifies-the-system.md)voor meer informatie over hoe deze methode de methoden [System. Management. Automation. cmdlet. ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) en [System. Management. Automation. cmdlet. ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) aanroept.

## <a name="writing-a-verbose-message"></a>Een uitgebreid bericht schrijven

De methode [System. Management. Automation. cmdlet. WriteVerbose](/dotnet/api/System.Management.Automation.Cmdlet.WriteVerbose) wordt gebruikt om algemene informatie op gebruikers niveau te schrijven die niet gerelateerd is aan specifieke fout voorwaarden. De systeem beheerder kan deze gegevens vervolgens gebruiken om de verwerking van andere opdrachten voort te zetten. Daarnaast moeten alle informatie die met deze methode wordt geschreven, naar behoefte worden gelokaliseerd.

De volgende code uit deze stop-proc-cmdlet bevat twee aanroepen naar de methode [System. Management. Automation. cmdlet. WriteVerbose](/dotnet/api/System.Management.Automation.Cmdlet.WriteVerbose) van de onderdrukking van de methode [System. Management. Automation. cmdlet. ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) .

```csharp
message = String.Format("Attempting to stop process \"{0}\".", name);
WriteVerbose(message);
```

```csharp
message = String.Format("Stopped process \"{0}\", pid {1}.",
                        processName, process.Id);

WriteVerbose(message);
```

## <a name="writing-a-debug-message"></a>Een debug-bericht schrijven

De methode [System. Management. Automation. cmdlet. WriteDebug](/dotnet/api/System.Management.Automation.Cmdlet.WriteDebug) wordt gebruikt voor het schrijven van fout opsporingsgegevens die kunnen worden gebruikt om de werking van de cmdlet op te lossen. De aanroep wordt uitgevoerd vanuit een invoer verwerkings methode.

> [!NOTE]
> Windows Power shell definieert ook een `Debug` para meter die zowel uitgebreide als fout opsporingsgegevens bevat. Als uw cmdlet deze para meter ondersteunt, hoeft [System. Management. Automation. cmdlet. WriteDebug](/dotnet/api/System.Management.Automation.Cmdlet.WriteDebug) niet te worden aangeroepen in dezelfde code die [System. Management. Automation. cmdlet. WriteVerbose](/dotnet/api/System.Management.Automation.Cmdlet.WriteVerbose)aanroept.

In de volgende twee secties van code uit de cmdlet stop-proc worden aanroepen naar de methode [System. Management. Automation. cmdlet. WriteDebug](/dotnet/api/System.Management.Automation.Cmdlet.WriteDebug) van de onderdrukking van de methode [System. Management. Automation. cmdlet. ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) weer gegeven.

Dit fout bericht wordt onmiddellijk beschreven voordat [System. Management. Automation. cmdlet. ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) wordt aangeroepen.

```csharp
message =
          String.Format("Acquired name for pid {0} : \"{1}\"",
                       process.Id, processName);
WriteDebug(message);
```

Dit fout bericht wordt onmiddellijk beschreven voordat [System. Management. Automation. cmdlet. WriteObject](/dotnet/api/System.Management.Automation.Cmdlet.WriteObject) wordt aangeroepen.

```csharp
message =
         String.Format("Writing process \"{0}\" to pipeline",
         processName);
WriteDebug(message);
WriteObject(process);
```

Windows Power shell stuurt automatisch alle [System. Management. Automation. cmdlet. WriteDebug](/dotnet/api/System.Management.Automation.Cmdlet.WriteDebug) -aanroepen naar de tracerings infrastructuur en-cmdlets. Hierdoor kan de methode aanroepen naar de hosttoepassing, een bestand of een fout opsporingsprogramma worden getraceerd zonder dat u in de cmdlet extra ontwikkel werkzaamheden hoeft te doen. Het volgende opdracht regel item implementeert een tracerings bewerking.

**PS> Trace-Expression stop-proc-File proc. log-opdracht stop-proc Notepad**

## <a name="writing-a-warning-message"></a>Een waarschuwings bericht schrijven

De methode [System. Management. Automation. cmdlet. WriteWarning](/dotnet/api/System.Management.Automation.Cmdlet.WriteWarning) wordt gebruikt om een waarschuwing te schrijven wanneer de cmdlet een bewerking uitvoert die een onverwacht resultaat kan hebben, bijvoorbeeld het overschrijven van een alleen-lezen bestand.

In de volgende code van de voor beeld van de cmdlet stop-proc wordt de aanroep van de methode [System. Management. Automation. cmdlet. WriteWarning](/dotnet/api/System.Management.Automation.Cmdlet.WriteWarning) van de onderdrukking van de methode [System. Management. Automation. cmdlet. ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) weer gegeven.

```csharp
 if (criticalProcess)
 {
   message =
             String.Format("Stopping the critical process \"{0}\".",
                           processName);
   WriteWarning(message);
} // if (criticalProcess...
```

## <a name="writing-a-progress-message"></a>Een voortgangs bericht schrijven

[System. Management. Automation. cmdlet. WriteProgress](/dotnet/api/System.Management.Automation.Cmdlet.WriteProgress) wordt gebruikt om voortgangs berichten te schrijven wanneer cmdlet-bewerkingen een lange tijd lang duren om te volt ooien. Een aanroep van [System. Management. Automation. cmdlet. WriteProgress](/dotnet/api/System.Management.Automation.Cmdlet.WriteProgress) geeft een [System. Management. Automation. Progressrecord](/dotnet/api/System.Management.Automation.ProgressRecord) -object door dat naar de hosting toepassing wordt verzonden voor rendering naar de gebruiker.

> [!NOTE]
> De cmdlet stop-proc bevat geen aanroep van de methode [System. Management. Automation. cmdlet. WriteProgress](/dotnet/api/System.Management.Automation.Cmdlet.WriteProgress) .

De volgende code is een voor beeld van een voortgangs bericht dat is geschreven door een cmdlet die probeert een item te kopiëren.

```csharp
int myId = 0;
string myActivity = "Copy-item: Copying *.* to c:\abc";
string myStatus = "Copying file bar.txt";
ProgressRecord pr = new ProgressRecord(myId, myActivity, myStatus);
WriteProgress(pr);

pr.RecordType = ProgressRecordType.Completed;
WriteProgress(pr);
```

## <a name="code-sample"></a>Code voorbeeld

Zie StopProcessSample02-voor [beeld](./stopprocesssample02-sample.md)voor de volledige C#-voorbeeld code.

## <a name="define-object-types-and-formatting"></a>Object typen en-opmaak definiëren

Windows Power shell geeft informatie door over cmdlets met behulp van .NET-objecten. Daarom moet een cmdlet een eigen type kunnen definiëren, of moet de cmdlet een bestaand type uitbreiden dat door een andere cmdlet wordt verschaft. Zie [object typen en-opmaak uitbreiden](/previous-versions//ms714665(v=vs.85))voor meer informatie over het definiëren van nieuwe typen of het uitbreiden van bestaande typen.

## <a name="building-the-cmdlet"></a>De cmdlet bouwen

Na de implementatie van een cmdlet moet deze met Windows Power shell zijn geregistreerd via een Windows Power shell-module. Zie [cmdlets, providers en hosttoepassingen registreren](/previous-versions//ms714644(v=vs.85))voor meer informatie over het registreren van cmdlets.

## <a name="testing-the-cmdlet"></a>De cmdlet testen

Als uw cmdlet is geregistreerd bij Windows Power shell, kunt u deze testen door deze uit te voeren op de opdracht regel. We gaan de voor beeld van de cmdlet stop-proc testen. Zie aan de slag [met Windows Power shell](/powershell/scripting/getting-started/getting-started-with-windows-powershell)voor meer informatie over het gebruik van cmdlets vanaf de opdracht regel.

- De volgende opdracht regel vermelding maakt gebruik van stop-proc om het proces ' NOTEPAD ' te stoppen, uitgebreide meldingen op te geven en fout opsporingsgegevens op te lossen.

    ```powershell
    PS> stop-proc -Name notepad -Verbose -Debug
    ```

    De volgende uitvoer wordt weer gegeven.

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

[Een cmdlet maken die het systeem wijzigt](./creating-a-cmdlet-that-modifies-the-system.md)

[Een Windows Power shell-cmdlet maken](/powershell/scripting/developer/cmdlet/writing-a-windows-powershell-cmdlet)

[Object typen en-opmaak uitbreiden](/previous-versions//ms714665(v=vs.85))

[Cmdlets, providers en hosttoepassingen registreren](/previous-versions//ms714644(v=vs.85))

[Windows PowerShell SDK](../windows-powershell-reference.md)
