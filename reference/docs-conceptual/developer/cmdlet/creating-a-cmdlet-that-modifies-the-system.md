---
ms.date: 09/13/2016
ms.topic: reference
title: Een cmdlet maken waarmee het systeem wordt gewijzigd
description: Een cmdlet maken waarmee het systeem wordt gewijzigd
ms.openlocfilehash: 757f2c97bb4b5dcf2fb633cd35fe52bc5f6c5cf9
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 12/10/2020
ms.locfileid: "93355541"
---
# <a name="creating-a-cmdlet-that-modifies-the-system"></a>Een cmdlet maken waarmee het systeem wordt gewijzigd

Soms moet een cmdlet de uitvoerings status van het systeem wijzigen, niet alleen de status van de Windows Power shell-runtime. In deze gevallen moet de-cmdlet de gebruiker toestaan om te bevestigen of de wijziging moet worden aangebracht.

Ter ondersteuning van de bevestiging moet een cmdlet twee dingen doen.

- Declareer dat de cmdlet bevestiging ondersteunt wanneer u het kenmerk [System. Management. Automation. CmdletAttribute](/dotnet/api/System.Management.Automation.CmdletAttribute) opgeeft door het sleutel woord SupportsShouldProcess in te stellen op `true` .

- Roep [System. Management. Automation. cmdlet. ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) aan tijdens het uitvoeren van de cmdlet (zoals weer gegeven in het volgende voor beeld).

Door de ondersteuning te bevestigen, `Confirm` `WhatIf` worden de para meters en door gegeven die worden verstrekt door Windows Power shell en voldoen aan de ontwikkel richtlijnen voor cmdlets (Zie [richt lijnen](./cmdlet-development-guidelines.md)voor de ontwikkeling van de cmdlet voor meer informatie over richt lijnen voor de ontwikkeling van de cmdlet).

## <a name="changing-the-system"></a>Het systeem wijzigen

De handeling ' wijzigen van het systeem ' verwijst naar een cmdlet die mogelijk de status van het systeem buiten Windows Power shell wijzigt. Als u bijvoorbeeld een proces stopt, een gebruikers account in-of uitschakelt of een rij toevoegt aan een database tabel, zijn alle wijzigingen in het systeem die moeten worden bevestigd.
Daarentegen wordt het systeem niet gewijzigd door bewerkingen waarmee gegevens worden gelezen of ingesteld tijdelijke verbindingen. Er is ook geen bevestiging nodig voor acties waarvan het effect is beperkt tot binnen de Windows Power shell-runtime, zoals `set-variable` . Cmdlets die een permanente wijziging mogelijk niet aanbrengen `SupportsShouldProcess` , moeten [System. Management. Automation. cmdlet. ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) alleen declareren en aanroepen als ze een permanente wijziging aanbrengen.

> [!NOTE]
> ShouldProcess-bevestiging geldt alleen voor cmdlets. Als een opdracht of script de uitvoerings status van een systeem wijzigt door rechtstreeks .NET-methoden of-eigenschappen aan te roepen of door toepassingen buiten Windows Power shell aan te roepen, is deze vorm van bevestiging niet beschikbaar.

## <a name="the-stopproc-cmdlet"></a>De StopProc-cmdlet

In dit onderwerp wordt een Stop-Proc-cmdlet beschreven die wordt gebruikt voor het stoppen van processen die worden opgehaald met behulp van de Get-Proc-cmdlet (beschreven in [uw eerste cmdlet maken](./creating-a-cmdlet-without-parameters.md)).

## <a name="defining-the-cmdlet"></a>De cmdlet defini??ren

De eerste stap bij het maken van de cmdlet is altijd de naam van de cmdlet en het declareren van de .NET-klasse die de cmdlet implementeert. Omdat u een cmdlet schrijft om het systeem te wijzigen, moet dit dienovereenkomstig een naam hebben. Met deze cmdlet worden systeem processen gestopt, dus de naam van de bewerking die u hier kiest, is ' Stop ', zoals gedefinieerd door de klasse [System. Management. Automation. Verbslifecycle](/dotnet/api/System.Management.Automation.VerbsLifeCycle) , met het zelfstandig naam woord ' proc ' om aan te geven dat de cmdlet processen stopt. Zie [cmdlet verb names](./approved-verbs-for-windows-powershell-commands.md)(Engelstalig) voor meer informatie over goedgekeurde cmdlet-termen.

Hier volgt de klassedefinitie voor deze Stop-Proc-cmdlet.

```csharp
[Cmdlet(VerbsLifecycle.Stop, "Proc",
        SupportsShouldProcess = true)]
public class StopProcCommand : Cmdlet
```

Houd er rekening mee dat het sleutel woord ' [System. Management. Automation. CmdletAttribute](/dotnet/api/System.Management.Automation.CmdletAttribute) ' `SupportsShouldProcess` is ingesteld op `true` om de cmdlet in te scha kelen voor het aanroepen van [System. Management. Automation. cmdlet. ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) en [System. Management. Automation. cmdlet. ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue).
Zonder dit tref woord is ingesteld `Confirm` , `WhatIf` zijn de para meters en niet beschikbaar voor de gebruiker.

### <a name="extremely-destructive-actions"></a>Extreem destructieve acties

Sommige bewerkingen zijn zeer destructief, zoals het opnieuw Format teren van een actieve vasteschijfpartitie. In deze gevallen moet de cmdlet worden ingesteld `ConfirmImpact`  =  `ConfirmImpact.High` bij het declareren van het kenmerk [System. Management. Automation. CmdletAttribute](/dotnet/api/System.Management.Automation.CmdletAttribute) . Met deze instelling wordt de cmdlet gedwongen om een gebruikers bevestiging te vragen, zelfs wanneer de gebruiker de para meter niet heeft opgegeven `Confirm` . Cmdlet-ontwikkel aars mogen echter niet `ConfirmImpact` overgaan op het gebruik van bewerkingen die alleen mogelijk destructief zijn, zoals het verwijderen van een gebruikers account. Houd er rekening mee dat als `ConfirmImpact` is ingesteld op [System. Management. Automation. ConfirmImpact](/dotnet/api/System.Management.Automation.ConfirmImpact) 
 **High**.

Op dezelfde manier zijn sommige bewerkingen waarschijnlijk niet destructief, hoewel ze in theorie de uitvoerings status van een systeem buiten Windows Power shell wijzigen. Dergelijke cmdlets kunnen `ConfirmImpact` worden ingesteld op [System. Management. Automation. Confirmimpact. low](/dotnet/api/system.management.automation.confirmimpact).
Hiermee worden bevestigings aanvragen overs Laan waarbij de gebruiker heeft gevraagd om alleen bewerkingen met een gemiddelde impact en hoge impact te bevestigen.

## <a name="defining-parameters-for-system-modification"></a>Para meters defini??ren voor systeem wijziging

In deze sectie wordt beschreven hoe u de cmdlet-para meters definieert, inclusief die die nodig zijn om systeem wijzigingen te ondersteunen. Zie [para meters toevoegen waarmee de commandline-invoer wordt verwerkt](./adding-parameters-that-process-command-line-input.md) als u algemene informatie nodig hebt over het defini??ren van para meters.

De cmdlet Stop-Proc definieert drie para meters: `Name` , `Force` en `PassThru` .

De `Name` para meter komt overeen met de `Name` eigenschap van het invoer object voor het proces. Houd er rekening mee dat de `Name` para meter in dit voor beeld verplicht is, omdat de cmdlet mislukt als deze geen benoemd proces heeft om te stoppen.

Met de `Force` para meter kan de gebruiker aanroepen van [System. Management. Automation. cmdlet. ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue)negeren.
Elke cmdlet die [System. Management. Automation. cmdlet. ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) aanroept, moet een `Force` para meter hebben zodat wanneer `Force` is opgegeven, de cmdlet de aanroep naar [System. Management. Automation. cmdlet. ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) overneemt en verdergaat met de bewerking. Houd er rekening mee dat dit geen invloed heeft op de aanroepen van [System. Management. Automation. cmdlet. ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess).

Met de `PassThru` para meter kan de gebruiker aangeven of de cmdlet een uitvoer object via de pijp lijn doorgeeft, in dit geval nadat een proces is gestopt. Houd er rekening mee dat deze para meter is gekoppeld aan de cmdlet zelf in plaats van op een eigenschap van het invoer object.

Dit is de parameter declaratie voor de Stop-Proc-cmdlet.

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

De cmdlet moet een invoer verwerkings methode overschrijven. De volgende code illustreert het [System. Management. Automation. cmdlet. ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) -onderdrukking dat wordt gebruikt in de voor beeld-cmdlet Stop-Proc. Voor elke aangevraagde proces naam zorgt deze methode ervoor dat het proces geen speciaal proces is, probeert het proces te stoppen en vervolgens een uitvoer object te verzenden als de `PassThru` para meter is opgegeven.

```csharp
protected override void ProcessRecord()
{
  foreach (string name in processNames)
  {
    // For every process name passed to the cmdlet, get the associated
    // process(es). For failures, write a non-terminating error
    Process[] processes;

    try
    {
      processes = Process.GetProcessesByName(name);
    }
    catch (InvalidOperationException ioe)
    {
      WriteError(new ErrorRecord(ioe,"Unable to access the target process by name",
                 ErrorCategory.InvalidOperation, name));
      continue;
    }

    // Try to stop the process(es) that have been retrieved for a name
    foreach (Process process in processes)
    {
      string processName;

      try
      {
        processName = process.ProcessName;
      }

      catch (Win32Exception e)
        {
          WriteError(new ErrorRecord(e, "ProcessNameNotFound",
                     ErrorCategory.ReadError, process));
          continue;
        }

        // Call Should Process to confirm the operation first.
        // This is always false if WhatIf is set.
        if (!ShouldProcess(string.Format("{0} ({1})", processName,
                           process.Id)))
        {
          continue;
        }
        // Call ShouldContinue to make sure the user really does want
        // to stop a critical process that could possibly stop the computer.
        bool criticalProcess =
             criticalProcessNames.Contains(processName.ToLower());

        if (criticalProcess &&!force)
        {
          string message = String.Format
                ("The process \"{0}\" is a critical process and should not be stopped. Are you sure you wish to stop the process?",
                processName);

          // It is possible that ProcessRecord is called multiple times
          // when the Name parameter receives objects as input from the
          // pipeline. So to retain YesToAll and NoToAll input that the
          // user may enter across multiple calls to ProcessRecord, this
          // information is stored as private members of the cmdlet.
          if (!ShouldContinue(message, "Warning!",
                              ref yesToAll,
                              ref noToAll))
          {
            continue;
          }
        } // if (criticalProcess...
        // Stop the named process.
        try
        {
          process.Kill();
        }
        catch (Exception e)
        {
          if ((e is Win32Exception) || (e is SystemException) ||
              (e is InvalidOperationException))
          {
            // This process could not be stopped so write
            // a non-terminating error.
            string message = String.Format("{0} {1} {2}",
                             "Could not stop process \"", processName,
                             "\".");
            WriteError(new ErrorRecord(e, message,
                       ErrorCategory.CloseError, process));
                       continue;
          } // if ((e is...
          else throw;
        } // catch

        // If the PassThru parameter argument is
        // True, pass the terminated process on.
        if (passThru)
        {
          WriteObject(process);
        }
    } // foreach (Process...
  } // foreach (string...
} // ProcessRecord
```

## <a name="calling-the-shouldprocess-method"></a>De ShouldProcess-methode aanroepen

De invoer verwerkings methode van uw cmdlet moet de methode [System. Management. Automation. cmdlet. ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) aanroepen om de uitvoering van een bewerking te bevestigen voordat een wijziging (bijvoorbeeld het verwijderen van bestanden) wordt doorgevoerd in de uitvoerings status van het systeem. Hierdoor kan de Windows Power shell-runtime het juiste gedrag ' WhatIf ' en ' Confirm ' in de shell opgeven.

> [!NOTE]
> Als een door het systeem ondersteunde cmdlet moet worden verwerkt en niet kan worden uitgevoerd, wordt de aanroep van [System. Management. Automation. cmdlet. ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) mogelijk onverwacht gewijzigd.

De aanroep van [System. Management. Automation. cmdlet. ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) verzendt de naam van de resource die moet worden gewijzigd naar de gebruiker, met de Windows Power shell-runtime, waarbij rekening wordt gehouden met opdracht regel instellingen of voorkeurs variabelen bij het bepalen van wat er moet worden weer gegeven voor de gebruiker.

In het volgende voor beeld ziet u de aanroep van [System. Management. Automation. cmdlet. ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) uit de onderdrukking van de methode [System. Management. Automation. cmdlet. ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) in de voor beeld-cmdlet Stop-Proc.

```csharp
if (!ShouldProcess(string.Format("{0} ({1})", processName,
                   process.Id)))
{
  continue;
}
```

## <a name="calling-the-shouldcontinue-method"></a>De ShouldContinue-methode aanroepen

De aanroep van de methode [System. Management. Automation. cmdlet. ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) verzendt een secundair bericht naar de gebruiker. Deze aanroep wordt uitgevoerd nadat de aanroep van [System. Management. Automation. cmdlet. ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) wordt geretourneerd `true` en als de `Force` para meter niet is ingesteld op `true` . De gebruiker kan vervolgens feedback geven om te zeggen of de bewerking moet worden voortgezet. De cmdlet roept [System. Management. Automation. cmdlet. ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) aan als een extra controle op mogelijk schadelijke systeem wijzigingen of wanneer u Ja-naar-alle-en geen-alle opties voor de gebruiker wilt bieden.

In het volgende voor beeld ziet u de aanroep van [System. Management. Automation. cmdlet. ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) uit de onderdrukking van de methode [System. Management. Automation. cmdlet. ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) in de voor beeld-cmdlet Stop-Proc.

```csharp
if (criticalProcess &&!force)
{
  string message = String.Format
        ("The process \"{0}\" is a critical process and should not be stopped. Are you sure you wish to stop the process?",
        processName);

  // It is possible that ProcessRecord is called multiple times
  // when the Name parameter receives objects as input from the
  // pipeline. So to retain YesToAll and NoToAll input that the
  // user may enter across multiple calls to ProcessRecord, this
  // information is stored as private members of the cmdlet.
  if (!ShouldContinue(message, "Warning!",
                      ref yesToAll,
                      ref noToAll))
  {
    continue;
  }
} // if (criticalProcess...
```

## <a name="stopping-input-processing"></a>Invoer verwerking stoppen

De invoer verwerkings methode van een cmdlet die systeem wijzigingen aanbrengt, moet een manier bieden om de verwerking van de invoer te stoppen. In het geval van deze Stop-Proc cmdlet wordt een aanroep uitgevoerd vanuit de methode [System. Management. Automation. cmdlet. ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) naar de methode [System. Diagnostics. process. Kill *](/dotnet/api/System.Diagnostics.Process.Kill) . Omdat de `PassThru` para meter is ingesteld op `true` , [System. Management. Automation. cmdlet. ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) , wordt [System. Management. Automation. cmdlet. WriteObject](/dotnet/api/System.Management.Automation.Cmdlet.WriteObject) ook aangeroepen om het proces object naar de pijp lijn te verzenden.

## <a name="code-sample"></a>Code voorbeeld

Zie StopProcessSample01-voor [beeld](./stopprocesssample01-sample.md)voor de volledige C#-voorbeeld code.

## <a name="defining-object-types-and-formatting"></a>Object typen en-opmaak defini??ren

Windows Power shell geeft informatie door over cmdlets met behulp van .net-objecten. Daarom moet een cmdlet een eigen type kunnen defini??ren, of moet de cmdlet een bestaand type uitbreiden dat door een andere cmdlet wordt verschaft. Zie [object typen en-opmaak uitbreiden](/previous-versions//ms714665(v=vs.85))voor meer informatie over het defini??ren van nieuwe typen of het uitbreiden van bestaande typen.

## <a name="building-the-cmdlet"></a>De cmdlet bouwen

Na de implementatie van een cmdlet moet deze met Windows Power shell zijn geregistreerd via een Windows Power shell-module. Zie [cmdlets, providers en hosttoepassingen registreren](/previous-versions//ms714644(v=vs.85))voor meer informatie over het registreren van cmdlets.

## <a name="testing-the-cmdlet"></a>De cmdlet testen

Als uw cmdlet is geregistreerd bij Windows Power shell, kunt u deze testen door deze uit te voeren op de opdracht regel. Hier volgen enkele tests die de Stop-Proc-cmdlet testen. Zie aan de slag [met Windows Power shell](/powershell/scripting/getting-started/getting-started-with-windows-powershell)voor meer informatie over het gebruik van cmdlets vanaf de opdracht regel.

- Start Windows Power shell en gebruik de cmdlet Stop-Proc om de verwerking te stoppen, zoals hieronder wordt weer gegeven. Omdat de cmdlet de `Name` para meter als verplicht opgeeft, vraagt de cmdlet naar de para meter.

    ```powershell
    PS> stop-proc
    ```

    De volgende uitvoer wordt weer gegeven.

    ```
    Cmdlet stop-proc at command pipeline position 1
    Supply values for the following parameters:
    Name[0]:
    ```

- We gaan nu de cmdlet gebruiken om het proces met de naam ' NOTEPAD ' te stoppen. De cmdlet vraagt u om de actie te bevestigen.

    ```powershell
    PS> stop-proc -Name notepad
    ```

    De volgende uitvoer wordt weer gegeven.

    ```
    Confirm
    Are you sure you want to perform this action?
    Performing operation "stop-proc" on Target "notepad (4996)".
    [Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "Y"): Y
    ```

- Gebruik Stop-Proc zoals weer gegeven om het kritieke proces met de naam ' WINLOGON ' te stoppen. U wordt gevraagd om deze actie uit te voeren, omdat het besturings systeem hierdoor opnieuw wordt opgestart.

    ```powershell
    PS> stop-proc -Name Winlogon
    ```

    De volgende uitvoer wordt weer gegeven.

    ```Output
    Confirm
    Are you sure you want to perform this action?
    Performing operation "stop-proc" on Target "winlogon (656)".
    [Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "Y"): Y
    Warning!
    The process " winlogon " is a critical process and should not be stopped. Are you sure you wish to stop the process?
    [Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "Y"): N
    ```

- We gaan nu proberen het WINLOGON-proces te stoppen zonder een waarschuwing te ontvangen. Houd er rekening mee dat deze opdracht invoer de `Force` para meter gebruikt om de waarschuwing te onderdrukken.

    ```powershell
    PS> stop-proc -Name winlogon -Force
    ```

    De volgende uitvoer wordt weer gegeven.

    ```Output
    Confirm
    Are you sure you want to perform this action?
    Performing operation "stop-proc" on Target "winlogon (656)".
    [Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "Y"): N
    ```

## <a name="see-also"></a>Zie ook

[Para meters toevoegen die Command-Line invoer verwerken](./adding-parameters-that-process-command-line-input.md)

[Object typen en-opmaak uitbreiden](/previous-versions//ms714665(v=vs.85))

[Cmdlets, providers en hosttoepassingen registreren](/previous-versions//ms714644(v=vs.85))

[Windows PowerShell SDK](../windows-powershell-reference.md)

[Cmdlet-voorbeelden](./cmdlet-samples.md)
