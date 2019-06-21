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
ms.openlocfilehash: 8a65915b88a04e36e773853b903528a65fe11e99
ms.sourcegitcommit: f60fa420bdc81db174e6168d3aeb11371e483162
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 06/20/2019
ms.locfileid: "67301390"
---
# <a name="creating-a-cmdlet-that-modifies-the-system"></a><span data-ttu-id="d638e-102">Een cmdlet maken waarmee het systeem wordt gewijzigd</span><span class="sxs-lookup"><span data-stu-id="d638e-102">Creating a Cmdlet that Modifies the System</span></span>

<span data-ttu-id="d638e-103">Een cmdlet moet soms de uitvoeringsstatus van het systeem, niet alleen de status van de Windows PowerShell-runtime wijzigen.</span><span class="sxs-lookup"><span data-stu-id="d638e-103">Sometimes a cmdlet must modify the running state of the system, not just the state of the Windows PowerShell runtime.</span></span> <span data-ttu-id="d638e-104">In dergelijke gevallen kan de cmdlet de gebruiker met een kans om te bevestigen of om de wijziging te maken of niet.</span><span class="sxs-lookup"><span data-stu-id="d638e-104">In these cases, the cmdlet should allow the user a chance to confirm whether or not to make the change.</span></span>

<span data-ttu-id="d638e-105">Ter ondersteuning van bevestiging moet een cmdlet twee dingen doen.</span><span class="sxs-lookup"><span data-stu-id="d638e-105">To support confirmation a cmdlet must do two things.</span></span>

- <span data-ttu-id="d638e-106">Declareert dat de cmdlet biedt ondersteuning voor bevestiging wanneer u opgeeft de [System.Management.Automation.CmdletAttribute](/dotnet/api/System.Management.Automation.CmdletAttribute) kenmerk door het sleutelwoord SupportsShouldProcess in te stellen `true`.</span><span class="sxs-lookup"><span data-stu-id="d638e-106">Declare that the cmdlet supports confirmation when you specify the [System.Management.Automation.CmdletAttribute](/dotnet/api/System.Management.Automation.CmdletAttribute) attribute by setting the SupportsShouldProcess keyword to `true`.</span></span>

- <span data-ttu-id="d638e-107">Bel [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) tijdens het uitvoeren van de cmdlet (zoals weergegeven in het volgende voorbeeld).</span><span class="sxs-lookup"><span data-stu-id="d638e-107">Call [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) during the execution of the cmdlet (as shown in the following example).</span></span>

<span data-ttu-id="d638e-108">Door de ondersteuning van bevestiging van een cmdlet wordt aangegeven dat de `Confirm` en `WhatIf` parameters die worden geleverd door Windows PowerShell, en ook voldoet aan de ontwikkeling van richtlijnen voor cmdlets (Zie voor meer informatie over de cmdlet ontwikkeling richtlijnen, [ Richtlijnen voor het ontwikkelen van cmdlet](./cmdlet-development-guidelines.md).).</span><span class="sxs-lookup"><span data-stu-id="d638e-108">By supporting confirmation, a cmdlet exposes the `Confirm` and `WhatIf` parameters that are provided by Windows PowerShell, and also meets the development guidelines for cmdlets (For more information about cmdlet development guidelines, see [Cmdlet Development Guidelines](./cmdlet-development-guidelines.md).).</span></span>

## <a name="changing-the-system"></a><span data-ttu-id="d638e-109">Wijzigen van het systeem</span><span class="sxs-lookup"><span data-stu-id="d638e-109">Changing the System</span></span>

<span data-ttu-id="d638e-110">De handeling van het "wijzigen van het systeem" verwijst naar een cmdlet die mogelijk de status van het systeem buiten Windows PowerShell gewijzigd.</span><span class="sxs-lookup"><span data-stu-id="d638e-110">The act of "changing the system" refers to any cmdlet that potentially changes the state of the system outside Windows PowerShell.</span></span> <span data-ttu-id="d638e-111">Bijvoorbeeld, het stoppen van een proces, inschakelen of uitschakelen van een gebruikersaccount of toevoegen van een rij in een databasetabel zijn alle wijzigingen in het systeem dat moet worden bevestigd.</span><span class="sxs-lookup"><span data-stu-id="d638e-111">For example, stopping a process, enabling or disabling a user account, or adding a row to a database table are all changes to the system that should be confirmed.</span></span> <span data-ttu-id="d638e-112">Daarentegen bewerkingen die gegevens lezen of tijdelijke verbindingen tot stand brengen het systeem niet te wijzigen en over het algemeen geen bevestiging vereist.</span><span class="sxs-lookup"><span data-stu-id="d638e-112">In contrast, operations that read data or establish transient connections do not change the system and generally do not require confirmation.</span></span> <span data-ttu-id="d638e-113">Bevestiging is ook niet nodig voor acties waarvan u het effect is beperkt in de Windows PowerShell-runtime, zoals `set-variable`.</span><span class="sxs-lookup"><span data-stu-id="d638e-113">Confirmation is also not needed for actions whose effect is limited to inside the Windows PowerShell runtime, such as `set-variable`.</span></span> <span data-ttu-id="d638e-114">Cmdlets die kan of kunnen niet maken voor een permanente wijziging moet declareren `SupportsShouldProcess` en roep [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) alleen als ze worden uitgevoerd over op een permanente wijziging aanbrengt.</span><span class="sxs-lookup"><span data-stu-id="d638e-114">Cmdlets that might or might not make a persistent change should declare `SupportsShouldProcess` and call [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) only if they are about to make a persistent change.</span></span>

> [!NOTE]
> <span data-ttu-id="d638e-115">Bevestiging van shouldprocess wordt overgeslagen geldt alleen voor de cmdlets.</span><span class="sxs-lookup"><span data-stu-id="d638e-115">ShouldProcess confirmation applies only to cmdlets.</span></span> <span data-ttu-id="d638e-116">Als een opdracht of script wijzigt de actieve status van een systeem door het .NET-methoden, eigenschappen of direct aan te roepen, of door de aanroepende toepassingen buiten Windows PowerShell, kan deze vorm van bevestiging niet meer beschikbaar.</span><span class="sxs-lookup"><span data-stu-id="d638e-116">If a command or script modifies the running state of a system by directly calling .NET methods or properties, or by calling applications outside of Windows PowerShell, this form of confirmation will not be available.</span></span>

## <a name="the-stopproc-cmdlet"></a><span data-ttu-id="d638e-117">De StopProc Cmdlet</span><span class="sxs-lookup"><span data-stu-id="d638e-117">The StopProc Cmdlet</span></span>

<span data-ttu-id="d638e-118">In dit onderwerp wordt beschreven hoe een cmdlet Stop-Proc waarmee wordt geprobeerd te beëindigen van processen die worden opgehaald met de cmdlet Get-Proc (beschreven in [het maken van uw eerste Cmdlet](./creating-a-cmdlet-without-parameters.md)).</span><span class="sxs-lookup"><span data-stu-id="d638e-118">This topic describes a Stop-Proc cmdlet that attempts to stop processes that are retrieved using the Get-Proc cmdlet (described in [Creating Your First Cmdlet](./creating-a-cmdlet-without-parameters.md)).</span></span>

## <a name="defining-the-cmdlet"></a><span data-ttu-id="d638e-119">De Cmdlet definiëren</span><span class="sxs-lookup"><span data-stu-id="d638e-119">Defining the Cmdlet</span></span>

<span data-ttu-id="d638e-120">De eerste stap bij het maken van de cmdlet is altijd naamgeving van de cmdlet en de .NET-klasse die de cmdlet declareren.</span><span class="sxs-lookup"><span data-stu-id="d638e-120">The first step in cmdlet creation is always naming the cmdlet and declaring the .NET class that implements the cmdlet.</span></span> <span data-ttu-id="d638e-121">Omdat u een cmdlet als u wilt wijzigen van het systeem schrijft, moet deze dienovereenkomstig worden genoemd.</span><span class="sxs-lookup"><span data-stu-id="d638e-121">Because you are writing a cmdlet to change the system, it should be named accordingly.</span></span> <span data-ttu-id="d638e-122">Deze cmdlet stopt systeemprocessen, dus de hier gekozen naam van de term "Stop", gedefinieerd door de [System.Management.Automation.Verbslifecycle](/dotnet/api/System.Management.Automation.VerbsLifeCycle) klasse, met het zelfstandig naamwoord 'Proc' om aan te geven dat de cmdlet worden processen gestopt.</span><span class="sxs-lookup"><span data-stu-id="d638e-122">This cmdlet stops system processes, so the verb name chosen here is "Stop", defined by the [System.Management.Automation.Verbslifecycle](/dotnet/api/System.Management.Automation.VerbsLifeCycle) class, with the noun "Proc" to indicate that the cmdlet stops processes.</span></span> <span data-ttu-id="d638e-123">Zie voor meer informatie over goedgekeurde werkwoorden [namen van de term cmdlets](./approved-verbs-for-windows-powershell-commands.md).</span><span class="sxs-lookup"><span data-stu-id="d638e-123">For more information about approved cmdlet verbs, see [Cmdlet Verb Names](./approved-verbs-for-windows-powershell-commands.md).</span></span>

<span data-ttu-id="d638e-124">Hier volgt de definitie van de klasse voor deze cmdlet Stop-Proc.</span><span class="sxs-lookup"><span data-stu-id="d638e-124">The following is the class definition for this Stop-Proc cmdlet.</span></span>

```csharp
[Cmdlet(VerbsLifecycle.Stop, "Proc",
        SupportsShouldProcess = true)]
public class StopProcCommand : Cmdlet
```

<span data-ttu-id="d638e-125">Houd er rekening mee dat in de [System.Management.Automation.CmdletAttribute](/dotnet/api/System.Management.Automation.CmdletAttribute) declaratie, de `SupportsShouldProcess` trefwoord kenmerk is ingesteld op `true` om in te schakelen van de cmdlet aanroepen [ System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) en [System.Management.Automation.Cmdlet.ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue).</span><span class="sxs-lookup"><span data-stu-id="d638e-125">Be aware that in the [System.Management.Automation.CmdletAttribute](/dotnet/api/System.Management.Automation.CmdletAttribute) declaration, the `SupportsShouldProcess` attribute keyword is set to `true` to enable the cmdlet to make calls to [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) and [System.Management.Automation.Cmdlet.ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue).</span></span> <span data-ttu-id="d638e-126">Zonder deze sleutelwoord is ingesteld, de `Confirm` en `WhatIf` parameters is niet beschikbaar voor de gebruiker.</span><span class="sxs-lookup"><span data-stu-id="d638e-126">Without this keyword set, the `Confirm` and `WhatIf` parameters will not be available to the user.</span></span>

### <a name="extremely-destructive-actions"></a><span data-ttu-id="d638e-127">Zeer destructieve acties</span><span class="sxs-lookup"><span data-stu-id="d638e-127">Extremely Destructive Actions</span></span>

<span data-ttu-id="d638e-128">Sommige bewerkingen zijn zeer destructieve, zoals het formatteren van de partitie van een actieve vaste schijf.</span><span class="sxs-lookup"><span data-stu-id="d638e-128">Some operations are extremely destructive, such as reformatting an active hard disk partition.</span></span> <span data-ttu-id="d638e-129">In dergelijke gevallen de cmdlet moet worden ingesteld `ConfirmImpact`  =  `ConfirmImpact.High` bij het melden van de [System.Management.Automation.CmdletAttribute](/dotnet/api/System.Management.Automation.CmdletAttribute) kenmerk.</span><span class="sxs-lookup"><span data-stu-id="d638e-129">In these cases, the cmdlet should set `ConfirmImpact` = `ConfirmImpact.High` when declaring the [System.Management.Automation.CmdletAttribute](/dotnet/api/System.Management.Automation.CmdletAttribute) attribute.</span></span> <span data-ttu-id="d638e-130">Deze instelling zorgt ervoor dat de cmdlet op bevestiging van de gebruiker aanvraag, zelfs wanneer de gebruiker niet opgegeven is. de `Confirm` parameter.</span><span class="sxs-lookup"><span data-stu-id="d638e-130">This setting forces the cmdlet to request user confirmation even when the user has not specified the `Confirm` parameter.</span></span> <span data-ttu-id="d638e-131">Echter cmdlet ontwikkelaars moeten spaarzaam `ConfirmImpact` voor bewerkingen die alleen mogelijk schadelijke zijn, zoals het verwijderen van een gebruikersaccount.</span><span class="sxs-lookup"><span data-stu-id="d638e-131">However, cmdlet developers should avoid overusing `ConfirmImpact` for operations that are just potentially destructive, such as deleting a user account.</span></span> <span data-ttu-id="d638e-132">Houd er rekening mee dat als `ConfirmImpact` is ingesteld op [System.Management.Automation.ConfirmImpact](/dotnet/api/System.Management.Automation.ConfirmImpact) **hoge**.</span><span class="sxs-lookup"><span data-stu-id="d638e-132">Remember that if `ConfirmImpact` is set to [System.Management.Automation.ConfirmImpact](/dotnet/api/System.Management.Automation.ConfirmImpact) **High**.</span></span>

<span data-ttu-id="d638e-133">Sommige bewerkingen zijn op dezelfde manier waarschijnlijk niet destructieve, hoewel ze in theorie Wijzig de actieve status van een systeem buiten Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="d638e-133">Similarly, some operations are unlikely to be destructive, although they do in theory modify the running state of a system outside Windows PowerShell.</span></span> <span data-ttu-id="d638e-134">Deze cmdlets kunt instellen `ConfirmImpact` naar [System.Management.Automation.Confirmimpact.Low](/dotnet/api/system.management.automation.confirmimpact?view=powershellsdk-1.1.0).</span><span class="sxs-lookup"><span data-stu-id="d638e-134">Such cmdlets can set `ConfirmImpact` to [System.Management.Automation.Confirmimpact.Low](/dotnet/api/system.management.automation.confirmimpact?view=powershellsdk-1.1.0).</span></span> <span data-ttu-id="d638e-135">Dit wordt bevestiging aanvragen waarbij de gebruiker heeft gevraagd om te bevestigen bewerkingen alleen gemiddeld impact en hoge impact overslaan.</span><span class="sxs-lookup"><span data-stu-id="d638e-135">This will bypass confirmation requests where the user has asked to confirm only medium-impact and high-impact operations.</span></span>

## <a name="defining-parameters-for-system-modification"></a><span data-ttu-id="d638e-136">Parameters voor aanpassing van het systeem definiëren</span><span class="sxs-lookup"><span data-stu-id="d638e-136">Defining Parameters for System Modification</span></span>

<span data-ttu-id="d638e-137">Deze sectie wordt beschreven hoe u voor het definiëren van de cmdlet-parameters, waaronder degene die nodig zijn om te wijzigen van de ondersteuning van system.</span><span class="sxs-lookup"><span data-stu-id="d638e-137">This section describes how to define the cmdlet parameters, including those that are needed to support system modification.</span></span> <span data-ttu-id="d638e-138">Zie [Parameters die invoer van de opdrachtregel proces toe te voegen](./adding-parameters-that-process-command-line-input.md) als u algemene informatie over het definiëren van parameters.</span><span class="sxs-lookup"><span data-stu-id="d638e-138">See [Adding Parameters that Process CommandLine Input](./adding-parameters-that-process-command-line-input.md) if you need general information about defining parameters.</span></span>

<span data-ttu-id="d638e-139">De cmdlet Stop-Proc definieert drie parameters: `Name`, `Force`, en `PassThru`.</span><span class="sxs-lookup"><span data-stu-id="d638e-139">The Stop-Proc cmdlet defines three parameters: `Name`, `Force`, and `PassThru`.</span></span>

<span data-ttu-id="d638e-140">De `Name` parameter komt overeen met de `Name` eigenschap van het procesobject voor invoer.</span><span class="sxs-lookup"><span data-stu-id="d638e-140">The `Name` parameter corresponds to the `Name` property of the process input object.</span></span> <span data-ttu-id="d638e-141">Houd er rekening mee dat de `Name` parameter in dit voorbeeld is verplicht, zoals de cmdlet mislukt als er geen een benoemde proces om te stoppen.</span><span class="sxs-lookup"><span data-stu-id="d638e-141">Be aware that the `Name` parameter in this sample is mandatory, as the cmdlet will fail if it does not have a named process to stop.</span></span>

<span data-ttu-id="d638e-142">De `Force` parameter zorgt ervoor dat de gebruiker voor de onderdrukking van aanroepen naar [System.Management.Automation.Cmdlet.ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue).</span><span class="sxs-lookup"><span data-stu-id="d638e-142">The `Force` parameter allows the user to override calls to [System.Management.Automation.Cmdlet.ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue).</span></span> <span data-ttu-id="d638e-143">In feite een cmdlet waarmee wordt aangeroepen [System.Management.Automation.Cmdlet.ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) moet een `Force` parameter zodat wanneer `Force` is opgegeven, wordt de cmdlet slaat de aanroep van [ System.Management.Automation.Cmdlet.ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) en wordt doorgegaan met de bewerking.</span><span class="sxs-lookup"><span data-stu-id="d638e-143">In fact, any cmdlet that calls [System.Management.Automation.Cmdlet.ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) should have a `Force` parameter so that when `Force` is specified, the cmdlet skips the call to [System.Management.Automation.Cmdlet.ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) and proceeds with the operation.</span></span> <span data-ttu-id="d638e-144">Houd er rekening mee dat dit heeft geen invloed op aanroepen naar [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess).</span><span class="sxs-lookup"><span data-stu-id="d638e-144">Be aware that this does not affect calls to [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess).</span></span>

<span data-ttu-id="d638e-145">De `PassThru` parameter zorgt ervoor dat de gebruiker om aan te geven of de cmdlet een uitvoerobject via de pijplijn in dit geval geeft nadat een proces is gestopt.</span><span class="sxs-lookup"><span data-stu-id="d638e-145">The `PassThru` parameter allows the user to indicate whether the cmdlet passes an output object through the pipeline, in this case, after a process is stopped.</span></span> <span data-ttu-id="d638e-146">Let erop dat deze parameter is gebonden aan de cmdlet zelf in plaats van aan een eigenschap van het invoerobject.</span><span class="sxs-lookup"><span data-stu-id="d638e-146">Be aware that this parameter is tied to the cmdlet itself instead of to a property of the input object.</span></span>

<span data-ttu-id="d638e-147">Hier is de parameterdeclaratie voor de cmdlet Stop-Proc.</span><span class="sxs-lookup"><span data-stu-id="d638e-147">Here is the parameter declaration for the Stop-Proc cmdlet.</span></span>

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

## <a name="overriding-an-input-processing-method"></a><span data-ttu-id="d638e-148">Invoer verwerken methode te overschrijven</span><span class="sxs-lookup"><span data-stu-id="d638e-148">Overriding an Input Processing Method</span></span>

<span data-ttu-id="d638e-149">De cmdlet moet invoer verwerken methode overschrijven.</span><span class="sxs-lookup"><span data-stu-id="d638e-149">The cmdlet must override an input processing method.</span></span> <span data-ttu-id="d638e-150">De volgende code toont de [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) overschrijven in de voorbeeld-cmdlet Stop-Proc gebruikt.</span><span class="sxs-lookup"><span data-stu-id="d638e-150">The following code illustrates the [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) override used in the sample Stop-Proc cmdlet.</span></span> <span data-ttu-id="d638e-151">Voor elk procesnaam aangevraagd, deze methode zorgt ervoor dat het proces niet een speciaal proces is, probeert het proces te stoppen en vervolgens een uitvoerobject verzendt als de `PassThru` parameter is opgegeven.</span><span class="sxs-lookup"><span data-stu-id="d638e-151">For each requested process name, this method ensures that the process is not a special process, tries to stop the process, and then sends an output object if the `PassThru` parameter is specified.</span></span>

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

## <a name="calling-the-shouldprocess-method"></a><span data-ttu-id="d638e-152">Aanroepen van de methode shouldprocess wordt overgeslagen</span><span class="sxs-lookup"><span data-stu-id="d638e-152">Calling the ShouldProcess Method</span></span>

<span data-ttu-id="d638e-153">De invoer verwerken van de methode van de cmdlet moet aanroepen de [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) methode voor het uitvoeren van een bewerking te bevestigen voordat de (bijvoorbeeld: verwijderen van bestanden) van een wijziging wordt aangebracht in de actieve status van het systeem.</span><span class="sxs-lookup"><span data-stu-id="d638e-153">The input processing method of your cmdlet should call the [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) method to confirm execution of an operation before a change (for example, deleting files) is made to the running state of the system.</span></span> <span data-ttu-id="d638e-154">Hiermee wordt de Windows PowerShell-runtime op te geven van de juiste "WhatIf" en "Confirm" gedrag in de shell.</span><span class="sxs-lookup"><span data-stu-id="d638e-154">This allows the Windows PowerShell runtime to supply the correct "WhatIf" and "Confirm" behavior within the shell.</span></span>

> [!NOTE]
> <span data-ttu-id="d638e-155">Als een cmdlet aangegeven dat het ondersteunt moeten worden verwerkt en niet de [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) aanroepen, de gebruiker kan het systeem onverwacht wijzigen.</span><span class="sxs-lookup"><span data-stu-id="d638e-155">If a cmdlet states that it supports should process and fails to make the [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) call, the user might modify the system unexpectedly.</span></span>

<span data-ttu-id="d638e-156">De aanroep van [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) verzendt de naam van de resource moet worden gewijzigd voor de gebruiker met de Windows PowerShell-runtime rekening houdend met de opdrachtregel instellingen of voorkeursvariabelen bij het bepalen van wat de gebruiker moet worden weergegeven.</span><span class="sxs-lookup"><span data-stu-id="d638e-156">The call to [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) sends the name of the resource to be changed to the user, with the Windows PowerShell runtime taking into account any command-line settings or preference variables in determining what should be displayed to the user.</span></span>

<span data-ttu-id="d638e-157">Het volgende voorbeeld ziet u de aanroep van [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) uit de onderdrukking van de [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) methode in het voorbeeld De cmdlet Stop-Proc.</span><span class="sxs-lookup"><span data-stu-id="d638e-157">The following example shows the call to [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) from the override of the [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) method in the sample Stop-Proc cmdlet.</span></span>

```csharp
if (!ShouldProcess(string.Format("{0} ({1})", processName,
                   process.Id)))
{
  continue;
}
```

## <a name="calling-the-shouldcontinue-method"></a><span data-ttu-id="d638e-158">Aanroepen van de methode ShouldContinue</span><span class="sxs-lookup"><span data-stu-id="d638e-158">Calling the ShouldContinue Method</span></span>

<span data-ttu-id="d638e-159">De aanroep van de [System.Management.Automation.Cmdlet.ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) methode verzendt een secundaire bericht naar de gebruiker.</span><span class="sxs-lookup"><span data-stu-id="d638e-159">The call to the [System.Management.Automation.Cmdlet.ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) method sends a secondary message to the user.</span></span> <span data-ttu-id="d638e-160">Deze aanroep is uitgevoerd na de aanroep van [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) retourneert `true` en als de `Force` parameter niet is ingesteld op `true`.</span><span class="sxs-lookup"><span data-stu-id="d638e-160">This call is made after the call to [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) returns `true` and if the `Force` parameter was not set to `true`.</span></span> <span data-ttu-id="d638e-161">De gebruiker kan vervolgens feedback geven bijvoorbeeld of de bewerking moet worden voortgezet.</span><span class="sxs-lookup"><span data-stu-id="d638e-161">The user can then provide feedback to say whether the operation should be continued.</span></span> <span data-ttu-id="d638e-162">Het aanroepen van cmdlet [System.Management.Automation.Cmdlet.ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) als een aanvullende controle voor wijzigingen van mogelijk schadelijke system of als u wilt dat voor Ja-naar-alles en Nee voor alle opties voor de gebruiker.</span><span class="sxs-lookup"><span data-stu-id="d638e-162">Your cmdlet calls [System.Management.Automation.Cmdlet.ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) as an additional check for potentially dangerous system modifications or when you want to provide yes-to-all and no-to-all options to the user.</span></span>

<span data-ttu-id="d638e-163">Het volgende voorbeeld ziet u de aanroep van [System.Management.Automation.Cmdlet.ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) uit de onderdrukking van de [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) methode in het voorbeeld De cmdlet Stop-Proc.</span><span class="sxs-lookup"><span data-stu-id="d638e-163">The following example shows the call to [System.Management.Automation.Cmdlet.ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) from the override of the [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) method in the sample Stop-Proc cmdlet.</span></span>

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

## <a name="stopping-input-processing"></a><span data-ttu-id="d638e-164">Stoppen verwerking van invoer</span><span class="sxs-lookup"><span data-stu-id="d638e-164">Stopping Input Processing</span></span>

<span data-ttu-id="d638e-165">De verwerking van de methode van een cmdlet die er wijzigingen zijn system invoer moet een manier om stoppen van de verwerking van invoer opgeven.</span><span class="sxs-lookup"><span data-stu-id="d638e-165">The input processing method of a cmdlet that makes system modifications must provide a way of stopping the processing of input.</span></span> <span data-ttu-id="d638e-166">In het geval van deze cmdlet Stop-Proc wordt een aanroep uitgevoerd vanaf de [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) methode de [System.Diagnostics.Process.Kill\*](/dotnet/api/System.Diagnostics.Process.Kill) methode.</span><span class="sxs-lookup"><span data-stu-id="d638e-166">In the case of this Stop-Proc cmdlet, a call is made from the [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) method to the [System.Diagnostics.Process.Kill\*](/dotnet/api/System.Diagnostics.Process.Kill) method.</span></span> <span data-ttu-id="d638e-167">Omdat de `PassThru` parameter is ingesteld op `true`, [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) ook aanroepen [System.Management.Automation.Cmdlet.WriteObject](/dotnet/api/System.Management.Automation.Cmdlet.WriteObject) te verzenden het procesobject aan de pijplijn.</span><span class="sxs-lookup"><span data-stu-id="d638e-167">Because the `PassThru` parameter is set to `true`, [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) also calls [System.Management.Automation.Cmdlet.WriteObject](/dotnet/api/System.Management.Automation.Cmdlet.WriteObject) to send the process object to the pipeline.</span></span>

## <a name="code-sample"></a><span data-ttu-id="d638e-168">Voorbeeld van code</span><span class="sxs-lookup"><span data-stu-id="d638e-168">Code Sample</span></span>

<span data-ttu-id="d638e-169">Voor de volledige C# voorbeeldcode, Zie [StopProcessSample01 voorbeeld](./stopprocesssample01-sample.md).</span><span class="sxs-lookup"><span data-stu-id="d638e-169">For the complete C# sample code, see [StopProcessSample01 Sample](./stopprocesssample01-sample.md).</span></span>

## <a name="defining-object-types-and-formatting"></a><span data-ttu-id="d638e-170">Objecttype definiëren en opmaak</span><span class="sxs-lookup"><span data-stu-id="d638e-170">Defining Object Types and Formatting</span></span>

<span data-ttu-id="d638e-171">Windows PowerShell wordt informatie doorgegeven tussen cmdlets met behulp van .net-objecten.</span><span class="sxs-lookup"><span data-stu-id="d638e-171">Windows PowerShell passes information between cmdlets using .Net objects.</span></span> <span data-ttu-id="d638e-172">Als gevolg daarvan kan een cmdlet mogelijk nodig hebt voor het definiëren van een eigen type, of de cmdlet moet om uit te breiden van een bestaand type geleverd door een andere cmdlet.</span><span class="sxs-lookup"><span data-stu-id="d638e-172">Consequently, a cmdlet may need to define its own type, or the cmdlet may need to extend an existing type provided by another cmdlet.</span></span> <span data-ttu-id="d638e-173">Zie voor meer informatie over het definiëren van nieuwe typen of uitbreiden van bestaande typen [objecttypen uitbreiden en opmaak](/previous-versions//ms714665(v=vs.85)).</span><span class="sxs-lookup"><span data-stu-id="d638e-173">For more information about defining new types or extending existing types, see [Extending Object Types and Formatting](/previous-versions//ms714665(v=vs.85)).</span></span>

## <a name="building-the-cmdlet"></a><span data-ttu-id="d638e-174">Het bouwen van de Cmdlet</span><span class="sxs-lookup"><span data-stu-id="d638e-174">Building the Cmdlet</span></span>

<span data-ttu-id="d638e-175">Na de implementatie van een cmdlet, moet deze met Windows PowerShell worden geregistreerd via een Windows PowerShell-module.</span><span class="sxs-lookup"><span data-stu-id="d638e-175">After implementing a cmdlet, it must be registered with Windows PowerShell through a Windows PowerShell snap-in.</span></span> <span data-ttu-id="d638e-176">Zie voor meer informatie over het registreren van cmdlets [hoe u Cmdlets registreren, Providers en hosting van toepassingen](/previous-versions//ms714644(v=vs.85)).</span><span class="sxs-lookup"><span data-stu-id="d638e-176">For more information about registering cmdlets, see [How to Register Cmdlets, Providers, and Host Applications](/previous-versions//ms714644(v=vs.85)).</span></span>

## <a name="testing-the-cmdlet"></a><span data-ttu-id="d638e-177">Testen van de Cmdlet</span><span class="sxs-lookup"><span data-stu-id="d638e-177">Testing the Cmdlet</span></span>

<span data-ttu-id="d638e-178">Wanneer de cmdlet is geregistreerd met Windows PowerShell, kunt u deze testen door te voeren op de opdrachtregel.</span><span class="sxs-lookup"><span data-stu-id="d638e-178">When your cmdlet has been registered with Windows PowerShell, you can test it by running it on the command line.</span></span> <span data-ttu-id="d638e-179">Hier volgen enkele tests die de cmdlet Stop-Proc testen.</span><span class="sxs-lookup"><span data-stu-id="d638e-179">Here are several tests that test the Stop-Proc cmdlet.</span></span> <span data-ttu-id="d638e-180">Zie voor meer informatie over het gebruik van cmdlets vanaf de opdrachtregel de [aan de slag met Windows PowerShell](/powershell/scripting/getting-started/getting-started-with-windows-powershell).</span><span class="sxs-lookup"><span data-stu-id="d638e-180">For more information about using cmdlets from the command line, see the [Getting Started with Windows PowerShell](/powershell/scripting/getting-started/getting-started-with-windows-powershell).</span></span>

- <span data-ttu-id="d638e-181">Start Windows PowerShell en gebruik de cmdlet Stop-Proc te stoppen met het verwerken, zoals hieronder weergegeven.</span><span class="sxs-lookup"><span data-stu-id="d638e-181">Start Windows PowerShell and use the Stop-Proc cmdlet to stop processing as shown below.</span></span> <span data-ttu-id="d638e-182">Omdat de cmdlet geeft de `Name` parameter verplicht is, de cmdlet-query's voor de parameter.</span><span class="sxs-lookup"><span data-stu-id="d638e-182">Because the cmdlet specifies the `Name` parameter as mandatory, the cmdlet queries for the parameter.</span></span>

    ```powershell
    PS> stop-proc
    ```

<span data-ttu-id="d638e-183">De volgende uitvoer wordt weergegeven.</span><span class="sxs-lookup"><span data-stu-id="d638e-183">The following output appears.</span></span>

    ```
    Cmdlet stop-proc at command pipeline position 1
    Supply values for the following parameters:
    Name[0]:
    ```

- <span data-ttu-id="d638e-184">Nu we de cmdlet gebruiken om het proces met de naam "KLADBLOK" te stoppen.</span><span class="sxs-lookup"><span data-stu-id="d638e-184">Now let's use the cmdlet to stop the process named "NOTEPAD".</span></span> <span data-ttu-id="d638e-185">De cmdlet vraagt u de actie te bevestigen.</span><span class="sxs-lookup"><span data-stu-id="d638e-185">The cmdlet asks you to confirm the action.</span></span>

    ```powershell
    PS> stop-proc -Name notepad
    ```

<span data-ttu-id="d638e-186">De volgende uitvoer wordt weergegeven.</span><span class="sxs-lookup"><span data-stu-id="d638e-186">The following output appears.</span></span>

    ```
    Confirm
    Are you sure you want to perform this action?
    Performing operation "stop-proc" on Target "notepad (4996)".
    [Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "Y"): Y
    ```

- <span data-ttu-id="d638e-187">Stop-Proc zoals wordt weergegeven gebruiken om de kritieke proces met de naam "WINLOGON" te stoppen.</span><span class="sxs-lookup"><span data-stu-id="d638e-187">Use Stop-Proc as shown to stop the critical process named "WINLOGON".</span></span> <span data-ttu-id="d638e-188">U wordt gevraagd en gewaarschuwd over het uitvoeren van deze actie omdat hierdoor het besturingssysteem opnieuw op te starten.</span><span class="sxs-lookup"><span data-stu-id="d638e-188">You are prompted and warned about performing this action because it will cause the operating system to reboot.</span></span>

    ```powershell
    PS> stop-proc -Name Winlogon
    ```

<span data-ttu-id="d638e-189">De volgende uitvoer wordt weergegeven.</span><span class="sxs-lookup"><span data-stu-id="d638e-189">The following output appears.</span></span>

    ```output
    Confirm
    Are you sure you want to perform this action?
    Performing operation "stop-proc" on Target "winlogon (656)".
    [Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "Y"): Y
    Warning!
    The process " winlogon " is a critical process and should not be stopped. Are you sure you wish to stop the process?
    [Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "Y"): N
    ```

- <span data-ttu-id="d638e-190">Laten we nu proberen de WINLOGON-proces stoppen zonder dat er een waarschuwing ontvangen.</span><span class="sxs-lookup"><span data-stu-id="d638e-190">Let's now try to stop the WINLOGON process without receiving a warning.</span></span> <span data-ttu-id="d638e-191">Houd er rekening mee dat deze vermelding opdracht gebruikt de `Force` parameter voor de onderdrukking van de waarschuwing.</span><span class="sxs-lookup"><span data-stu-id="d638e-191">Be aware that this command entry uses the `Force` parameter to override the warning.</span></span>

    ```powershell
    PS> stop-proc -Name winlogon -Force
    ```

<span data-ttu-id="d638e-192">De volgende uitvoer wordt weergegeven.</span><span class="sxs-lookup"><span data-stu-id="d638e-192">The following output appears.</span></span>

    ```output
    Confirm
    Are you sure you want to perform this action?
    Performing operation "stop-proc" on Target "winlogon (656)".
    [Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "Y"): N
    ```

## <a name="see-also"></a><span data-ttu-id="d638e-193">Zie ook</span><span class="sxs-lookup"><span data-stu-id="d638e-193">See Also</span></span>

[<span data-ttu-id="d638e-194">Parameters die opdrachtregel verwerken toe te voegen</span><span class="sxs-lookup"><span data-stu-id="d638e-194">Adding Parameters that Process Command-Line Input</span></span>](./adding-parameters-that-process-command-line-input.md)

<span data-ttu-id="d638e-195">[Objecttypen uitbreiden en opmaak](/previous-versions//ms714665(v=vs.85))</span><span class="sxs-lookup"><span data-stu-id="d638e-195">[Extending Object Types and Formatting](/previous-versions//ms714665(v=vs.85))</span></span>

<span data-ttu-id="d638e-196">[Over het registreren van Providers,-Cmdlets en -toepassingen hosten](/previous-versions//ms714644(v=vs.85))</span><span class="sxs-lookup"><span data-stu-id="d638e-196">[How to Register Cmdlets, Providers, and Host Applications](/previous-versions//ms714644(v=vs.85))</span></span>

[<span data-ttu-id="d638e-197">Windows PowerShell SDK</span><span class="sxs-lookup"><span data-stu-id="d638e-197">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)

[<span data-ttu-id="d638e-198">Cmdlet-voorbeelden</span><span class="sxs-lookup"><span data-stu-id="d638e-198">Cmdlet Samples</span></span>](./cmdlet-samples.md)