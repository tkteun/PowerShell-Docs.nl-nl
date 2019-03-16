---
title: Het maken van een Cmdlet die Hiermee wijzigt u het systeem | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- should process [PowerShell Programmer's Guide]
- should continue [PowerShell Programmer's Guide]
- user feedback [PowerShell Programmer's Guide]
- confirm impact [PowerShell Programmer's Guide]
ms.assetid: 59be4120-1700-4d92-a308-ef4a32ccf11a
caps.latest.revision: 8
ms.openlocfilehash: bbe9f0213754d1cc47e0fd9a7a898bde916c0636
ms.sourcegitcommit: caac7d098a448232304c9d6728e7340ec7517a71
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 03/16/2019
ms.locfileid: "58055135"
---
# <a name="creating-a-cmdlet-that-modifies-the-system"></a>Een cmdlet maken waarmee het systeem wordt gewijzigd

Een cmdlet moet soms de uitvoeringsstatus van het systeem, niet alleen de status van de Windows PowerShell-runtime wijzigen. In dergelijke gevallen kan de cmdlet de gebruiker met een kans om te bevestigen of om de wijziging te maken of niet.

Ter ondersteuning van bevestiging moet een cmdlet twee dingen doen.

- Declareert dat de cmdlet biedt ondersteuning voor bevestiging wanneer u opgeeft de [System.Management.Automation.CmdletAttribute](/dotnet/api/System.Management.Automation.CmdletAttribute) kenmerk door het sleutelwoord SupportsShouldProcess in te stellen `true`.

- Bel [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) tijdens het uitvoeren van de cmdlet (zoals weergegeven in het volgende voorbeeld).

Door de ondersteuning van bevestiging van een cmdlet wordt aangegeven dat de `Confirm` en `WhatIf` parameters die worden geleverd door Windows PowerShell, en ook voldoet aan de ontwikkeling van richtlijnen voor cmdlets (Zie voor meer informatie over de cmdlet ontwikkeling richtlijnen, [ Richtlijnen voor het ontwikkelen van cmdlet](./cmdlet-development-guidelines.md).).

## <a name="changing-the-system"></a>Wijzigen van het systeem

De handeling van het "wijzigen van het systeem" verwijst naar een cmdlet die mogelijk de status van het systeem buiten Windows PowerShell gewijzigd. Bijvoorbeeld, het stoppen van een proces, inschakelen of uitschakelen van een gebruikersaccount of toevoegen van een rij in een databasetabel zijn alle wijzigingen in het systeem dat moet worden bevestigd. Daarentegen bewerkingen die gegevens lezen of tijdelijke verbindingen tot stand brengen het systeem niet te wijzigen en over het algemeen geen bevestiging vereist. Bevestiging is ook niet nodig voor acties waarvan u het effect is beperkt in de Windows PowerShell-runtime, zoals `set-variable`. Cmdlets die kan of kunnen niet maken voor een permanente wijziging moet declareren `SupportsShouldProcess` en roep [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) alleen als ze worden uitgevoerd over op een permanente wijziging aanbrengt.

> [!NOTE]
> Bevestiging van shouldprocess wordt overgeslagen geldt alleen voor de cmdlets. Als een opdracht of script wijzigt de actieve status van een systeem door het .NET-methoden, eigenschappen of direct aan te roepen, of door de aanroepende toepassingen buiten Windows PowerShell, kan deze vorm van bevestiging niet meer beschikbaar.

## <a name="the-stopproc-cmdlet"></a>De StopProc Cmdlet

In dit onderwerp wordt beschreven hoe een cmdlet Stop-Proc waarmee wordt geprobeerd te beëindigen van processen die worden opgehaald met de cmdlet Get-Proc (beschreven in [het maken van uw eerste Cmdlet](./creating-a-cmdlet-without-parameters.md)).

Onderwerpen in deze sectie bevatten het volgende:

- [De Cmdlet definiëren](#Defining-the-Cmdlet)

- [Parameters voor aanpassing van het systeem definiëren](#Defining-Parameters-for-System-Modification)

- [Invoer verwerken methode te overschrijven](#Overriding-an-Input-Processing-Method)

- [Aanroepen van de methode shouldprocess wordt overgeslagen](#Calling-the-ShouldProcess-Method)

- [Aanroepen van de methode ShouldContinue](#Calling-the-ShouldContinue-Method)

- [Stoppen verwerking van invoer](#Stopping-Input-Processing)

- [Voorbeeld van code](#Code-Sample)

- [Objecttype definiëren en opmaak](#Defining-Object-Types-and-Formatting)

- [Het bouwen van de Cmdlet](#Building-the-Cmdlet)

- [Testen van de Cmdlet](#Testing-the-Cmdlet)

## <a name="defining-the-cmdlet"></a>De Cmdlet definiëren

De eerste stap bij het maken van de cmdlet is altijd naamgeving van de cmdlet en de .NET-klasse die de cmdlet declareren. Omdat u een cmdlet als u wilt wijzigen van het systeem schrijft, moet deze dienovereenkomstig worden genoemd. Deze cmdlet stopt systeemprocessen, dus de hier gekozen naam van de term "Stop", gedefinieerd door de [System.Management.Automation.Verbslifecycle](/dotnet/api/System.Management.Automation.VerbsLifeCycle) klasse, met het zelfstandig naamwoord 'Proc' om aan te geven dat de cmdlet worden processen gestopt. Zie voor meer informatie over goedgekeurde werkwoorden [namen van de term cmdlets](./approved-verbs-for-windows-powershell-commands.md).

Hier volgt de definitie van de klasse voor deze cmdlet Stop-Proc.

```csharp
[Cmdlet(VerbsLifecycle.Stop, "Proc",
        SupportsShouldProcess = true)]
public class StopProcCommand : Cmdlet
```

Houd er rekening mee dat in de [System.Management.Automation.CmdletAttribute](/dotnet/api/System.Management.Automation.CmdletAttribute) declaratie, de `SupportsShouldProcess` trefwoord kenmerk is ingesteld op `true` om in te schakelen van de cmdlet aanroepen [ System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) en [System.Management.Automation.Cmdlet.ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue). Zonder deze sleutelwoord is ingesteld, de `Confirm` en `WhatIf` parameters is niet beschikbaar voor de gebruiker.

### <a name="extremely-destructive-actions"></a>Zeer destructieve acties

Sommige bewerkingen zijn zeer destructieve, zoals het formatteren van de partitie van een actieve vaste schijf. In dergelijke gevallen de cmdlet moet worden ingesteld `ConfirmImpact`  =  `ConfirmImpact.High` bij het melden van de [System.Management.Automation.CmdletAttribute](/dotnet/api/System.Management.Automation.CmdletAttribute) kenmerk. Deze instelling zorgt ervoor dat de cmdlet op bevestiging van de gebruiker aanvraag, zelfs wanneer de gebruiker niet opgegeven is. de `Confirm` parameter. Echter cmdlet ontwikkelaars moeten spaarzaam `ConfirmImpact` voor bewerkingen die alleen mogelijk schadelijke zijn, zoals het verwijderen van een gebruikersaccount. Houd er rekening mee dat als `ConfirmImpact` is ingesteld op [System.Management.Automation.Confirmimpact.High](/dotnet/api/System.Management.Automation.ConfirmImpact.High).

Sommige bewerkingen zijn op dezelfde manier waarschijnlijk niet destructieve, hoewel ze in theorie Wijzig de actieve status van een systeem buiten Windows PowerShell. Deze cmdlets kunt instellen `ConfirmImpact` naar [System.Management.Automation.Confirmimpact.Low](/dotnet/api/system.management.automation.confirmimpact?view=powershellsdk-1.1.0). Dit wordt bevestiging aanvragen waarbij de gebruiker heeft gevraagd om te bevestigen bewerkingen alleen gemiddeld impact en hoge impact overslaan.

## <a name="defining-parameters-for-system-modification"></a>Parameters voor aanpassing van het systeem definiëren

Deze sectie wordt beschreven hoe u voor het definiëren van de cmdlet-parameters, waaronder degene die nodig zijn om te wijzigen van de ondersteuning van system. Zie [Parameters die invoer van de opdrachtregel proces toe te voegen](./adding-parameters-that-process-command-line-input.md) als u algemene informatie over het definiëren van parameters.

De cmdlet Stop-Proc definieert drie parameters: `Name`, `Force`, en `PassThru`.

De `Name` parameter komt overeen met de `Name` eigenschap van het procesobject voor invoer. Houd er rekening mee dat de `Name` parameter in dit voorbeeld is verplicht, zoals de cmdlet mislukt als er geen een benoemde proces om te stoppen.

De `Force` parameter zorgt ervoor dat de gebruiker voor de onderdrukking van aanroepen naar [System.Management.Automation.Cmdlet.ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue). In feite een cmdlet waarmee wordt aangeroepen [System.Management.Automation.Cmdlet.ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) moet een `Force` parameter zodat wanneer `Force` is opgegeven, wordt de cmdlet slaat de aanroep van [ System.Management.Automation.Cmdlet.ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) en wordt doorgegaan met de bewerking. Houd er rekening mee dat dit heeft geen invloed op aanroepen naar [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess).

De `PassThru` parameter zorgt ervoor dat de gebruiker om aan te geven of de cmdlet een uitvoerobject via de pijplijn in dit geval geeft nadat een proces is gestopt. Let erop dat deze parameter is gebonden aan de cmdlet zelf in plaats van aan een eigenschap van het invoerobject.

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

De cmdlet moet invoer verwerken methode overschrijven. De volgende code toont de [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) overschrijven in de voorbeeld-cmdlet Stop-Proc gebruikt. Voor elk procesnaam aangevraagd, deze methode zorgt ervoor dat het proces niet een speciaal proces is, probeert het proces te stoppen en vervolgens een uitvoerobject verzendt als de `PassThru` parameter is opgegeven.

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

## <a name="calling-the-shouldprocess-method"></a>Aanroepen van de methode shouldprocess wordt overgeslagen

De invoer verwerken van de methode van de cmdlet moet aanroepen de [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) methode voor het uitvoeren van een bewerking te bevestigen voordat de (bijvoorbeeld: verwijderen van bestanden) van een wijziging wordt aangebracht in de actieve status van het systeem. Hiermee wordt de Windows PowerShell-runtime op te geven van de juiste "WhatIf" en "Confirm" gedrag in de shell.

> [!NOTE]
> Als een cmdlet aangegeven dat het ondersteunt moeten worden verwerkt en niet de [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) aanroepen, de gebruiker kan het systeem onverwacht wijzigen.

De aanroep van [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) verzendt de naam van de resource moet worden gewijzigd voor de gebruiker met de Windows PowerShell-runtime rekening houdend met de opdrachtregel instellingen of voorkeursvariabelen bij het bepalen van wat de gebruiker moet worden weergegeven.

Het volgende voorbeeld ziet u de aanroep van [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) uit de onderdrukking van de [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) methode in het voorbeeld De cmdlet Stop-Proc.

```csharp
if (!ShouldProcess(string.Format("{0} ({1})", processName,
                   process.Id)))
{
  continue;
}
```

## <a name="calling-the-shouldcontinue-method"></a>Aanroepen van de methode ShouldContinue

De aanroep van de [System.Management.Automation.Cmdlet.ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) methode verzendt een secundaire bericht naar de gebruiker. Deze aanroep is uitgevoerd na de aanroep van [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) retourneert `true` en als de `Force` parameter niet is ingesteld op `true`. De gebruiker kan vervolgens feedback geven bijvoorbeeld of de bewerking moet worden voortgezet. Het aanroepen van cmdlet [System.Management.Automation.Cmdlet.ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) als een aanvullende controle voor wijzigingen van mogelijk schadelijke system of als u wilt dat voor Ja-naar-alles en Nee voor alle opties voor de gebruiker.

Het volgende voorbeeld ziet u de aanroep van [System.Management.Automation.Cmdlet.ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) uit de onderdrukking van de [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) methode in het voorbeeld De cmdlet Stop-Proc.

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

## <a name="stopping-input-processing"></a>Stoppen verwerking van invoer

De verwerking van de methode van een cmdlet die er wijzigingen zijn system invoer moet een manier om stoppen van de verwerking van invoer opgeven. In het geval van deze cmdlet Stop-Proc wordt een aanroep uitgevoerd vanaf de [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) methode de [System.Diagnostics.Process.Kill*](/dotnet/api/System.Diagnostics.Process.Kill) methode. Omdat de `PassThru` parameter is ingesteld op `true`, [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) ook aanroepen [System.Management.Automation.Cmdlet.WriteObject](/dotnet/api/System.Management.Automation.Cmdlet.WriteObject) te verzenden het procesobject aan de pijplijn.

## <a name="code-sample"></a>Voorbeeld van code

Voor de volledige C# voorbeeldcode, Zie [StopProcessSample01 voorbeeld](./stopprocesssample01-sample.md).

## <a name="defining-object-types-and-formatting"></a>Objecttype definiëren en opmaak

Windows PowerShell wordt informatie doorgegeven tussen cmdlets met behulp van .net-objecten. Als gevolg daarvan kan een cmdlet mogelijk nodig hebt voor het definiëren van een eigen type, of de cmdlet moet om uit te breiden van een bestaand type geleverd door een andere cmdlet. Zie voor meer informatie over het definiëren van nieuwe typen of uitbreiden van bestaande typen [objecttypen uitbreiden en opmaak](https://msdn.microsoft.com/en-us/da976d91-a3d6-44e8-affa-466b1e2bd351).

## <a name="building-the-cmdlet"></a>Het bouwen van de Cmdlet

Na de implementatie van een cmdlet, moet deze met Windows PowerShell worden geregistreerd via een Windows PowerShell-module. Zie voor meer informatie over het registreren van cmdlets [hoe u Cmdlets registreren, Providers en hosting van toepassingen](https://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c).

## <a name="testing-the-cmdlet"></a>Testen van de Cmdlet

Wanneer de cmdlet is geregistreerd met Windows PowerShell, kunt u deze testen door te voeren op de opdrachtregel. Hier volgen enkele tests die de cmdlet Stop-Proc testen. Zie voor meer informatie over het gebruik van cmdlets vanaf de opdrachtregel de [aan de slag met Windows PowerShell](/powershell/scripting/getting-started/getting-started-with-windows-powershell).

- Start Windows PowerShell en gebruik de cmdlet Stop-Proc te stoppen met het verwerken, zoals hieronder weergegeven. Omdat de cmdlet geeft de `Name` parameter verplicht is, de cmdlet-query's voor de parameter.

    ```powershell
    PS> stop-proc
    ```

De volgende uitvoer wordt weergegeven.

    ```
    Cmdlet stop-proc at command pipeline position 1
    Supply values for the following parameters:
    Name[0]:
    ```

- Nu we de cmdlet gebruiken om het proces met de naam "KLADBLOK" te stoppen. De cmdlet vraagt u de actie te bevestigen.

    ```powershell
    PS> stop-proc -Name notepad
    ```

De volgende uitvoer wordt weergegeven.

    ```
    Confirm
    Are you sure you want to perform this action?
    Performing operation "stop-proc" on Target "notepad (4996)".
    [Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "Y"): Y
    ```

- Stop-Proc zoals wordt weergegeven gebruiken om de kritieke proces met de naam "WINLOGON" te stoppen. U wordt gevraagd en gewaarschuwd over het uitvoeren van deze actie omdat hierdoor het besturingssysteem opnieuw op te starten.

    ```powershell
    PS> stop-proc -Name Winlogon
    ```

De volgende uitvoer wordt weergegeven.

    ```output
    Confirm
    Are you sure you want to perform this action?
    Performing operation "stop-proc" on Target "winlogon (656)".
    [Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "Y"): Y
    Warning!
    The process " winlogon " is a critical process and should not be stopped. Are you sure you wish to stop the process?
    [Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "Y"): N
    ```

- Laten we nu proberen de WINLOGON-proces stoppen zonder dat er een waarschuwing ontvangen. Houd er rekening mee dat deze vermelding opdracht gebruikt de `Force` parameter voor de onderdrukking van de waarschuwing.

    ```powershell
    PS> stop-proc -Name winlogon -Force
    ```

De volgende uitvoer wordt weergegeven.

    ```output
    Confirm
    Are you sure you want to perform this action?
    Performing operation "stop-proc" on Target "winlogon (656)".
    [Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "Y"): N
    ```

## <a name="see-also"></a>Zie ook

[Parameters die opdrachtregel verwerken toe te voegen](./adding-parameters-that-process-command-line-input.md)

[Objecttypen uitbreiden en opmaak](https://msdn.microsoft.com/en-us/da976d91-a3d6-44e8-affa-466b1e2bd351)

[Over het registreren van Providers,-Cmdlets en -toepassingen hosten](https://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c)

[Windows PowerShell SDK](../windows-powershell-reference.md)

[Cmdlet-voorbeelden](./cmdlet-samples.md)