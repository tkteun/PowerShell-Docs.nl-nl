---
title: Een cmdlet maken die het systeem wijzigt | Microsoft Docs
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
ms.openlocfilehash: f0ce30c3fa76141908680934bcac41a989622c42
ms.sourcegitcommit: 173556307d45d88de31086ce776770547eece64c
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 05/19/2020
ms.locfileid: "83560063"
---
# <a name="creating-a-cmdlet-that-modifies-the-system"></a><span data-ttu-id="43a01-102">Een cmdlet maken waarmee het systeem wordt gewijzigd</span><span class="sxs-lookup"><span data-stu-id="43a01-102">Creating a Cmdlet that Modifies the System</span></span>

<span data-ttu-id="43a01-103">Soms moet een cmdlet de uitvoerings status van het systeem wijzigen, niet alleen de status van de Windows Power shell-runtime.</span><span class="sxs-lookup"><span data-stu-id="43a01-103">Sometimes a cmdlet must modify the running state of the system, not just the state of the Windows PowerShell runtime.</span></span> <span data-ttu-id="43a01-104">In deze gevallen moet de-cmdlet de gebruiker toestaan om te bevestigen of de wijziging moet worden aangebracht.</span><span class="sxs-lookup"><span data-stu-id="43a01-104">In these cases, the cmdlet should allow the user a chance to confirm whether or not to make the change.</span></span>

<span data-ttu-id="43a01-105">Ter ondersteuning van de bevestiging moet een cmdlet twee dingen doen.</span><span class="sxs-lookup"><span data-stu-id="43a01-105">To support confirmation a cmdlet must do two things.</span></span>

- <span data-ttu-id="43a01-106">Declareer dat de cmdlet bevestiging ondersteunt wanneer u het kenmerk [System. Management. Automation. CmdletAttribute](/dotnet/api/System.Management.Automation.CmdletAttribute) opgeeft door het sleutel woord SupportsShouldProcess in te stellen op `true` .</span><span class="sxs-lookup"><span data-stu-id="43a01-106">Declare that the cmdlet supports confirmation when you specify the [System.Management.Automation.CmdletAttribute](/dotnet/api/System.Management.Automation.CmdletAttribute) attribute by setting the SupportsShouldProcess keyword to `true`.</span></span>

- <span data-ttu-id="43a01-107">Roep [System. Management. Automation. cmdlet. ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) aan tijdens het uitvoeren van de cmdlet (zoals weer gegeven in het volgende voor beeld).</span><span class="sxs-lookup"><span data-stu-id="43a01-107">Call [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) during the execution of the cmdlet (as shown in the following example).</span></span>

<span data-ttu-id="43a01-108">Door de ondersteuning te bevestigen, `Confirm` `WhatIf` worden de para meters en door gegeven die worden verstrekt door Windows Power shell en voldoen aan de ontwikkel richtlijnen voor cmdlets (Zie [richt lijnen](./cmdlet-development-guidelines.md)voor de ontwikkeling van de cmdlet voor meer informatie over richt lijnen voor de ontwikkeling van de cmdlet).</span><span class="sxs-lookup"><span data-stu-id="43a01-108">By supporting confirmation, a cmdlet exposes the `Confirm` and `WhatIf` parameters that are provided by Windows PowerShell, and also meets the development guidelines for cmdlets (For more information about cmdlet development guidelines, see [Cmdlet Development Guidelines](./cmdlet-development-guidelines.md).).</span></span>

## <a name="changing-the-system"></a><span data-ttu-id="43a01-109">Het systeem wijzigen</span><span class="sxs-lookup"><span data-stu-id="43a01-109">Changing the System</span></span>

<span data-ttu-id="43a01-110">De handeling ' wijzigen van het systeem ' verwijst naar een cmdlet die mogelijk de status van het systeem buiten Windows Power shell wijzigt.</span><span class="sxs-lookup"><span data-stu-id="43a01-110">The act of "changing the system" refers to any cmdlet that potentially changes the state of the system outside Windows PowerShell.</span></span> <span data-ttu-id="43a01-111">Als u bijvoorbeeld een proces stopt, een gebruikers account in-of uitschakelt of een rij toevoegt aan een database tabel, zijn alle wijzigingen in het systeem die moeten worden bevestigd.</span><span class="sxs-lookup"><span data-stu-id="43a01-111">For example, stopping a process, enabling or disabling a user account, or adding a row to a database table are all changes to the system that should be confirmed.</span></span> <span data-ttu-id="43a01-112">Daarentegen wordt het systeem niet gewijzigd door bewerkingen waarmee gegevens worden gelezen of ingesteld tijdelijke verbindingen.</span><span class="sxs-lookup"><span data-stu-id="43a01-112">In contrast, operations that read data or establish transient connections do not change the system and generally do not require confirmation.</span></span> <span data-ttu-id="43a01-113">Er is ook geen bevestiging nodig voor acties waarvan het effect is beperkt tot binnen de Windows Power shell-runtime, zoals `set-variable` .</span><span class="sxs-lookup"><span data-stu-id="43a01-113">Confirmation is also not needed for actions whose effect is limited to inside the Windows PowerShell runtime, such as `set-variable`.</span></span> <span data-ttu-id="43a01-114">Cmdlets die een permanente wijziging mogelijk niet aanbrengen `SupportsShouldProcess` , moeten [System. Management. Automation. cmdlet. ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) alleen declareren en aanroepen als ze een permanente wijziging aanbrengen.</span><span class="sxs-lookup"><span data-stu-id="43a01-114">Cmdlets that might or might not make a persistent change should declare `SupportsShouldProcess` and call [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) only if they are about to make a persistent change.</span></span>

> [!NOTE]
> <span data-ttu-id="43a01-115">ShouldProcess-bevestiging geldt alleen voor cmdlets.</span><span class="sxs-lookup"><span data-stu-id="43a01-115">ShouldProcess confirmation applies only to cmdlets.</span></span> <span data-ttu-id="43a01-116">Als een opdracht of script de uitvoerings status van een systeem wijzigt door rechtstreeks .NET-methoden of-eigenschappen aan te roepen of door toepassingen buiten Windows Power shell aan te roepen, is deze vorm van bevestiging niet beschikbaar.</span><span class="sxs-lookup"><span data-stu-id="43a01-116">If a command or script modifies the running state of a system by directly calling .NET methods or properties, or by calling applications outside of Windows PowerShell, this form of confirmation will not be available.</span></span>

## <a name="the-stopproc-cmdlet"></a><span data-ttu-id="43a01-117">De StopProc-cmdlet</span><span class="sxs-lookup"><span data-stu-id="43a01-117">The StopProc Cmdlet</span></span>

<span data-ttu-id="43a01-118">In dit onderwerp wordt een stop-proc-cmdlet beschreven die probeert processen te stoppen die worden opgehaald met de cmdlet Get-proc (beschreven in [uw eerste cmdlet maken](./creating-a-cmdlet-without-parameters.md)).</span><span class="sxs-lookup"><span data-stu-id="43a01-118">This topic describes a Stop-Proc cmdlet that attempts to stop processes that are retrieved using the Get-Proc cmdlet (described in [Creating Your First Cmdlet](./creating-a-cmdlet-without-parameters.md)).</span></span>

## <a name="defining-the-cmdlet"></a><span data-ttu-id="43a01-119">De cmdlet definiëren</span><span class="sxs-lookup"><span data-stu-id="43a01-119">Defining the Cmdlet</span></span>

<span data-ttu-id="43a01-120">De eerste stap bij het maken van de cmdlet is altijd de naam van de cmdlet en het declareren van de .NET-klasse die de cmdlet implementeert.</span><span class="sxs-lookup"><span data-stu-id="43a01-120">The first step in cmdlet creation is always naming the cmdlet and declaring the .NET class that implements the cmdlet.</span></span> <span data-ttu-id="43a01-121">Omdat u een cmdlet schrijft om het systeem te wijzigen, moet dit dienovereenkomstig een naam hebben.</span><span class="sxs-lookup"><span data-stu-id="43a01-121">Because you are writing a cmdlet to change the system, it should be named accordingly.</span></span> <span data-ttu-id="43a01-122">Met deze cmdlet worden systeem processen gestopt, dus de naam van de bewerking die u hier kiest, is ' Stop ', zoals gedefinieerd door de klasse [System. Management. Automation. Verbslifecycle](/dotnet/api/System.Management.Automation.VerbsLifeCycle) , met het zelfstandig naam woord ' proc ' om aan te geven dat de cmdlet processen stopt.</span><span class="sxs-lookup"><span data-stu-id="43a01-122">This cmdlet stops system processes, so the verb name chosen here is "Stop", defined by the [System.Management.Automation.Verbslifecycle](/dotnet/api/System.Management.Automation.VerbsLifeCycle) class, with the noun "Proc" to indicate that the cmdlet stops processes.</span></span> <span data-ttu-id="43a01-123">Zie [cmdlet verb names](./approved-verbs-for-windows-powershell-commands.md)(Engelstalig) voor meer informatie over goedgekeurde cmdlet-termen.</span><span class="sxs-lookup"><span data-stu-id="43a01-123">For more information about approved cmdlet verbs, see [Cmdlet Verb Names](./approved-verbs-for-windows-powershell-commands.md).</span></span>

<span data-ttu-id="43a01-124">Hier volgt de klassedefinitie voor deze stop-proc-cmdlet.</span><span class="sxs-lookup"><span data-stu-id="43a01-124">The following is the class definition for this Stop-Proc cmdlet.</span></span>

```csharp
[Cmdlet(VerbsLifecycle.Stop, "Proc",
        SupportsShouldProcess = true)]
public class StopProcCommand : Cmdlet
```

<span data-ttu-id="43a01-125">Houd er rekening mee dat het sleutel woord ' [System. Management. Automation. CmdletAttribute](/dotnet/api/System.Management.Automation.CmdletAttribute) ' `SupportsShouldProcess` is ingesteld op `true` om de cmdlet in te scha kelen voor het aanroepen van [System. Management. Automation. cmdlet. ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) en [System. Management. Automation. cmdlet. ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue).</span><span class="sxs-lookup"><span data-stu-id="43a01-125">Be aware that in the [System.Management.Automation.CmdletAttribute](/dotnet/api/System.Management.Automation.CmdletAttribute) declaration, the `SupportsShouldProcess` attribute keyword is set to `true` to enable the cmdlet to make calls to [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) and [System.Management.Automation.Cmdlet.ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue).</span></span> <span data-ttu-id="43a01-126">Zonder dit tref woord is ingesteld `Confirm` , `WhatIf` zijn de para meters en niet beschikbaar voor de gebruiker.</span><span class="sxs-lookup"><span data-stu-id="43a01-126">Without this keyword set, the `Confirm` and `WhatIf` parameters will not be available to the user.</span></span>

### <a name="extremely-destructive-actions"></a><span data-ttu-id="43a01-127">Extreem destructieve acties</span><span class="sxs-lookup"><span data-stu-id="43a01-127">Extremely Destructive Actions</span></span>

<span data-ttu-id="43a01-128">Sommige bewerkingen zijn zeer destructief, zoals het opnieuw Format teren van een actieve vasteschijfpartitie.</span><span class="sxs-lookup"><span data-stu-id="43a01-128">Some operations are extremely destructive, such as reformatting an active hard disk partition.</span></span> <span data-ttu-id="43a01-129">In deze gevallen moet de cmdlet worden ingesteld `ConfirmImpact`  =  `ConfirmImpact.High` bij het declareren van het kenmerk [System. Management. Automation. CmdletAttribute](/dotnet/api/System.Management.Automation.CmdletAttribute) .</span><span class="sxs-lookup"><span data-stu-id="43a01-129">In these cases, the cmdlet should set `ConfirmImpact` = `ConfirmImpact.High` when declaring the [System.Management.Automation.CmdletAttribute](/dotnet/api/System.Management.Automation.CmdletAttribute) attribute.</span></span> <span data-ttu-id="43a01-130">Met deze instelling wordt de cmdlet gedwongen om een gebruikers bevestiging te vragen, zelfs wanneer de gebruiker de para meter niet heeft opgegeven `Confirm` .</span><span class="sxs-lookup"><span data-stu-id="43a01-130">This setting forces the cmdlet to request user confirmation even when the user has not specified the `Confirm` parameter.</span></span> <span data-ttu-id="43a01-131">Cmdlet-ontwikkel aars mogen echter niet `ConfirmImpact` overgaan op het gebruik van bewerkingen die alleen mogelijk destructief zijn, zoals het verwijderen van een gebruikers account.</span><span class="sxs-lookup"><span data-stu-id="43a01-131">However, cmdlet developers should avoid overusing `ConfirmImpact` for operations that are just potentially destructive, such as deleting a user account.</span></span> <span data-ttu-id="43a01-132">Houd er rekening mee dat als `ConfirmImpact` is ingesteld op [System. Management. Automation. ConfirmImpact](/dotnet/api/System.Management.Automation.ConfirmImpact) **High**.</span><span class="sxs-lookup"><span data-stu-id="43a01-132">Remember that if `ConfirmImpact` is set to [System.Management.Automation.ConfirmImpact](/dotnet/api/System.Management.Automation.ConfirmImpact) **High**.</span></span>

<span data-ttu-id="43a01-133">Op dezelfde manier zijn sommige bewerkingen waarschijnlijk niet destructief, hoewel ze in theorie de uitvoerings status van een systeem buiten Windows Power shell wijzigen.</span><span class="sxs-lookup"><span data-stu-id="43a01-133">Similarly, some operations are unlikely to be destructive, although they do in theory modify the running state of a system outside Windows PowerShell.</span></span> <span data-ttu-id="43a01-134">Dergelijke cmdlets kunnen `ConfirmImpact` worden ingesteld op [System. Management. Automation. Confirmimpact. low](/dotnet/api/system.management.automation.confirmimpact?view=powershellsdk-1.1.0).</span><span class="sxs-lookup"><span data-stu-id="43a01-134">Such cmdlets can set `ConfirmImpact` to [System.Management.Automation.Confirmimpact.Low](/dotnet/api/system.management.automation.confirmimpact?view=powershellsdk-1.1.0).</span></span> <span data-ttu-id="43a01-135">Hiermee worden bevestigings aanvragen overs Laan waarbij de gebruiker heeft gevraagd om alleen bewerkingen met een gemiddelde impact en hoge impact te bevestigen.</span><span class="sxs-lookup"><span data-stu-id="43a01-135">This will bypass confirmation requests where the user has asked to confirm only medium-impact and high-impact operations.</span></span>

## <a name="defining-parameters-for-system-modification"></a><span data-ttu-id="43a01-136">Para meters definiëren voor systeem wijziging</span><span class="sxs-lookup"><span data-stu-id="43a01-136">Defining Parameters for System Modification</span></span>

<span data-ttu-id="43a01-137">In deze sectie wordt beschreven hoe u de cmdlet-para meters definieert, inclusief die die nodig zijn om systeem wijzigingen te ondersteunen.</span><span class="sxs-lookup"><span data-stu-id="43a01-137">This section describes how to define the cmdlet parameters, including those that are needed to support system modification.</span></span> <span data-ttu-id="43a01-138">Zie [para meters toevoegen waarmee de commandline-invoer wordt verwerkt](./adding-parameters-that-process-command-line-input.md) als u algemene informatie nodig hebt over het definiëren van para meters.</span><span class="sxs-lookup"><span data-stu-id="43a01-138">See [Adding Parameters that Process CommandLine Input](./adding-parameters-that-process-command-line-input.md) if you need general information about defining parameters.</span></span>

<span data-ttu-id="43a01-139">De cmdlet stop-proc definieert drie para meters: `Name` , `Force` en `PassThru` .</span><span class="sxs-lookup"><span data-stu-id="43a01-139">The Stop-Proc cmdlet defines three parameters: `Name`, `Force`, and `PassThru`.</span></span>

<span data-ttu-id="43a01-140">De `Name` para meter komt overeen met de `Name` eigenschap van het invoer object voor het proces.</span><span class="sxs-lookup"><span data-stu-id="43a01-140">The `Name` parameter corresponds to the `Name` property of the process input object.</span></span> <span data-ttu-id="43a01-141">Houd er rekening mee dat de `Name` para meter in dit voor beeld verplicht is, omdat de cmdlet mislukt als deze geen benoemd proces heeft om te stoppen.</span><span class="sxs-lookup"><span data-stu-id="43a01-141">Be aware that the `Name` parameter in this sample is mandatory, as the cmdlet will fail if it does not have a named process to stop.</span></span>

<span data-ttu-id="43a01-142">Met de `Force` para meter kan de gebruiker aanroepen van [System. Management. Automation. cmdlet. ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue)negeren.</span><span class="sxs-lookup"><span data-stu-id="43a01-142">The `Force` parameter allows the user to override calls to [System.Management.Automation.Cmdlet.ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue).</span></span> <span data-ttu-id="43a01-143">Elke cmdlet die [System. Management. Automation. cmdlet. ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) aanroept, moet een `Force` para meter hebben zodat wanneer `Force` is opgegeven, de cmdlet de aanroep naar [System. Management. Automation. cmdlet. ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) overneemt en verdergaat met de bewerking.</span><span class="sxs-lookup"><span data-stu-id="43a01-143">In fact, any cmdlet that calls [System.Management.Automation.Cmdlet.ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) should have a `Force` parameter so that when `Force` is specified, the cmdlet skips the call to [System.Management.Automation.Cmdlet.ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) and proceeds with the operation.</span></span> <span data-ttu-id="43a01-144">Houd er rekening mee dat dit geen invloed heeft op de aanroepen van [System. Management. Automation. cmdlet. ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess).</span><span class="sxs-lookup"><span data-stu-id="43a01-144">Be aware that this does not affect calls to [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess).</span></span>

<span data-ttu-id="43a01-145">Met de `PassThru` para meter kan de gebruiker aangeven of de cmdlet een uitvoer object via de pijp lijn doorgeeft, in dit geval nadat een proces is gestopt.</span><span class="sxs-lookup"><span data-stu-id="43a01-145">The `PassThru` parameter allows the user to indicate whether the cmdlet passes an output object through the pipeline, in this case, after a process is stopped.</span></span> <span data-ttu-id="43a01-146">Houd er rekening mee dat deze para meter is gekoppeld aan de cmdlet zelf in plaats van op een eigenschap van het invoer object.</span><span class="sxs-lookup"><span data-stu-id="43a01-146">Be aware that this parameter is tied to the cmdlet itself instead of to a property of the input object.</span></span>

<span data-ttu-id="43a01-147">Dit is de para meter declaratie voor de cmdlet stop-proc.</span><span class="sxs-lookup"><span data-stu-id="43a01-147">Here is the parameter declaration for the Stop-Proc cmdlet.</span></span>

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

## <a name="overriding-an-input-processing-method"></a><span data-ttu-id="43a01-148">Een invoer verwerkings methode overschrijven</span><span class="sxs-lookup"><span data-stu-id="43a01-148">Overriding an Input Processing Method</span></span>

<span data-ttu-id="43a01-149">De cmdlet moet een invoer verwerkings methode overschrijven.</span><span class="sxs-lookup"><span data-stu-id="43a01-149">The cmdlet must override an input processing method.</span></span> <span data-ttu-id="43a01-150">In de volgende code ziet u de onderdrukking [System. Management. Automation. cmdlet. ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) die wordt gebruikt in de voor beeld van de cmdlet stop-proc.</span><span class="sxs-lookup"><span data-stu-id="43a01-150">The following code illustrates the [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) override used in the sample Stop-Proc cmdlet.</span></span> <span data-ttu-id="43a01-151">Voor elke aangevraagde proces naam zorgt deze methode ervoor dat het proces geen speciaal proces is, probeert het proces te stoppen en vervolgens een uitvoer object te verzenden als de `PassThru` para meter is opgegeven.</span><span class="sxs-lookup"><span data-stu-id="43a01-151">For each requested process name, this method ensures that the process is not a special process, tries to stop the process, and then sends an output object if the `PassThru` parameter is specified.</span></span>

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

## <a name="calling-the-shouldprocess-method"></a><span data-ttu-id="43a01-152">De ShouldProcess-methode aanroepen</span><span class="sxs-lookup"><span data-stu-id="43a01-152">Calling the ShouldProcess Method</span></span>

<span data-ttu-id="43a01-153">De invoer verwerkings methode van uw cmdlet moet de methode [System. Management. Automation. cmdlet. ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) aanroepen om de uitvoering van een bewerking te bevestigen voordat een wijziging (bijvoorbeeld het verwijderen van bestanden) wordt doorgevoerd in de uitvoerings status van het systeem.</span><span class="sxs-lookup"><span data-stu-id="43a01-153">The input processing method of your cmdlet should call the [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) method to confirm execution of an operation before a change (for example, deleting files) is made to the running state of the system.</span></span> <span data-ttu-id="43a01-154">Hierdoor kan de Windows Power shell-runtime het juiste gedrag ' WhatIf ' en ' Confirm ' in de shell opgeven.</span><span class="sxs-lookup"><span data-stu-id="43a01-154">This allows the Windows PowerShell runtime to supply the correct "WhatIf" and "Confirm" behavior within the shell.</span></span>

> [!NOTE]
> <span data-ttu-id="43a01-155">Als een door het systeem ondersteunde cmdlet moet worden verwerkt en niet kan worden uitgevoerd, wordt de aanroep van [System. Management. Automation. cmdlet. ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) mogelijk onverwacht gewijzigd.</span><span class="sxs-lookup"><span data-stu-id="43a01-155">If a cmdlet states that it supports should process and fails to make the [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) call, the user might modify the system unexpectedly.</span></span>

<span data-ttu-id="43a01-156">De aanroep van [System. Management. Automation. cmdlet. ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) verzendt de naam van de resource die moet worden gewijzigd naar de gebruiker, met de Windows Power shell-runtime, waarbij rekening wordt gehouden met opdracht regel instellingen of voorkeurs variabelen bij het bepalen van wat er moet worden weer gegeven voor de gebruiker.</span><span class="sxs-lookup"><span data-stu-id="43a01-156">The call to [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) sends the name of the resource to be changed to the user, with the Windows PowerShell runtime taking into account any command-line settings or preference variables in determining what should be displayed to the user.</span></span>

<span data-ttu-id="43a01-157">In het volgende voor beeld ziet u de aanroep van [System. Management. Automation. cmdlet. ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) uit de onderdrukking van de methode [System. Management. Automation. cmdlet. ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) in de voor beeld van de cmdlet stop-proc.</span><span class="sxs-lookup"><span data-stu-id="43a01-157">The following example shows the call to [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) from the override of the [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) method in the sample Stop-Proc cmdlet.</span></span>

```csharp
if (!ShouldProcess(string.Format("{0} ({1})", processName,
                   process.Id)))
{
  continue;
}
```

## <a name="calling-the-shouldcontinue-method"></a><span data-ttu-id="43a01-158">De ShouldContinue-methode aanroepen</span><span class="sxs-lookup"><span data-stu-id="43a01-158">Calling the ShouldContinue Method</span></span>

<span data-ttu-id="43a01-159">De aanroep van de methode [System. Management. Automation. cmdlet. ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) verzendt een secundair bericht naar de gebruiker.</span><span class="sxs-lookup"><span data-stu-id="43a01-159">The call to the [System.Management.Automation.Cmdlet.ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) method sends a secondary message to the user.</span></span> <span data-ttu-id="43a01-160">Deze aanroep wordt uitgevoerd nadat de aanroep van [System. Management. Automation. cmdlet. ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) wordt geretourneerd `true` en als de `Force` para meter niet is ingesteld op `true` .</span><span class="sxs-lookup"><span data-stu-id="43a01-160">This call is made after the call to [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) returns `true` and if the `Force` parameter was not set to `true`.</span></span> <span data-ttu-id="43a01-161">De gebruiker kan vervolgens feedback geven om te zeggen of de bewerking moet worden voortgezet.</span><span class="sxs-lookup"><span data-stu-id="43a01-161">The user can then provide feedback to say whether the operation should be continued.</span></span> <span data-ttu-id="43a01-162">De cmdlet roept [System. Management. Automation. cmdlet. ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) aan als een extra controle op mogelijk schadelijke systeem wijzigingen of wanneer u Ja-naar-alle-en geen-alle opties voor de gebruiker wilt bieden.</span><span class="sxs-lookup"><span data-stu-id="43a01-162">Your cmdlet calls [System.Management.Automation.Cmdlet.ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) as an additional check for potentially dangerous system modifications or when you want to provide yes-to-all and no-to-all options to the user.</span></span>

<span data-ttu-id="43a01-163">In het volgende voor beeld ziet u de aanroep van [System. Management. Automation. cmdlet. ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) uit de onderdrukking van de methode [System. Management. Automation. cmdlet. ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) in de voor beeld van de cmdlet stop-proc.</span><span class="sxs-lookup"><span data-stu-id="43a01-163">The following example shows the call to [System.Management.Automation.Cmdlet.ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) from the override of the [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) method in the sample Stop-Proc cmdlet.</span></span>

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

## <a name="stopping-input-processing"></a><span data-ttu-id="43a01-164">Invoer verwerking stoppen</span><span class="sxs-lookup"><span data-stu-id="43a01-164">Stopping Input Processing</span></span>

<span data-ttu-id="43a01-165">De invoer verwerkings methode van een cmdlet die systeem wijzigingen aanbrengt, moet een manier bieden om de verwerking van de invoer te stoppen.</span><span class="sxs-lookup"><span data-stu-id="43a01-165">The input processing method of a cmdlet that makes system modifications must provide a way of stopping the processing of input.</span></span> <span data-ttu-id="43a01-166">In het geval van deze stop-proc cmdlet wordt een aanroep uitgevoerd vanuit de methode [System. Management. Automation. cmdlet. ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) aan de methode [System. Diagnostics. process. Kill \*](/dotnet/api/System.Diagnostics.Process.Kill) .</span><span class="sxs-lookup"><span data-stu-id="43a01-166">In the case of this Stop-Proc cmdlet, a call is made from the [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) method to the [System.Diagnostics.Process.Kill\*](/dotnet/api/System.Diagnostics.Process.Kill) method.</span></span> <span data-ttu-id="43a01-167">Omdat de `PassThru` para meter is ingesteld op `true` , [System. Management. Automation. cmdlet. ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) , wordt [System. Management. Automation. cmdlet. WriteObject](/dotnet/api/System.Management.Automation.Cmdlet.WriteObject) ook aangeroepen om het proces object naar de pijp lijn te verzenden.</span><span class="sxs-lookup"><span data-stu-id="43a01-167">Because the `PassThru` parameter is set to `true`, [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) also calls [System.Management.Automation.Cmdlet.WriteObject](/dotnet/api/System.Management.Automation.Cmdlet.WriteObject) to send the process object to the pipeline.</span></span>

## <a name="code-sample"></a><span data-ttu-id="43a01-168">Code voorbeeld</span><span class="sxs-lookup"><span data-stu-id="43a01-168">Code Sample</span></span>

<span data-ttu-id="43a01-169">Zie StopProcessSample01-voor [beeld](./stopprocesssample01-sample.md)voor de volledige C#-voorbeeld code.</span><span class="sxs-lookup"><span data-stu-id="43a01-169">For the complete C# sample code, see [StopProcessSample01 Sample](./stopprocesssample01-sample.md).</span></span>

## <a name="defining-object-types-and-formatting"></a><span data-ttu-id="43a01-170">Object typen en-opmaak definiëren</span><span class="sxs-lookup"><span data-stu-id="43a01-170">Defining Object Types and Formatting</span></span>

<span data-ttu-id="43a01-171">Windows Power shell geeft informatie door over cmdlets met behulp van .net-objecten.</span><span class="sxs-lookup"><span data-stu-id="43a01-171">Windows PowerShell passes information between cmdlets using .Net objects.</span></span> <span data-ttu-id="43a01-172">Daarom moet een cmdlet een eigen type kunnen definiëren, of moet de cmdlet een bestaand type uitbreiden dat door een andere cmdlet wordt verschaft.</span><span class="sxs-lookup"><span data-stu-id="43a01-172">Consequently, a cmdlet may need to define its own type, or the cmdlet may need to extend an existing type provided by another cmdlet.</span></span> <span data-ttu-id="43a01-173">Zie [object typen en-opmaak uitbreiden](/previous-versions//ms714665(v=vs.85))voor meer informatie over het definiëren van nieuwe typen of het uitbreiden van bestaande typen.</span><span class="sxs-lookup"><span data-stu-id="43a01-173">For more information about defining new types or extending existing types, see [Extending Object Types and Formatting](/previous-versions//ms714665(v=vs.85)).</span></span>

## <a name="building-the-cmdlet"></a><span data-ttu-id="43a01-174">De cmdlet bouwen</span><span class="sxs-lookup"><span data-stu-id="43a01-174">Building the Cmdlet</span></span>

<span data-ttu-id="43a01-175">Na de implementatie van een cmdlet moet deze met Windows Power shell zijn geregistreerd via een Windows Power shell-module.</span><span class="sxs-lookup"><span data-stu-id="43a01-175">After implementing a cmdlet, it must be registered with Windows PowerShell through a Windows PowerShell snap-in.</span></span> <span data-ttu-id="43a01-176">Zie [cmdlets, providers en hosttoepassingen registreren](/previous-versions//ms714644(v=vs.85))voor meer informatie over het registreren van cmdlets.</span><span class="sxs-lookup"><span data-stu-id="43a01-176">For more information about registering cmdlets, see [How to Register Cmdlets, Providers, and Host Applications](/previous-versions//ms714644(v=vs.85)).</span></span>

## <a name="testing-the-cmdlet"></a><span data-ttu-id="43a01-177">De cmdlet testen</span><span class="sxs-lookup"><span data-stu-id="43a01-177">Testing the Cmdlet</span></span>

<span data-ttu-id="43a01-178">Als uw cmdlet is geregistreerd bij Windows Power shell, kunt u deze testen door deze uit te voeren op de opdracht regel.</span><span class="sxs-lookup"><span data-stu-id="43a01-178">When your cmdlet has been registered with Windows PowerShell, you can test it by running it on the command line.</span></span> <span data-ttu-id="43a01-179">Hier volgen enkele tests die de cmdlet stop-proc testen.</span><span class="sxs-lookup"><span data-stu-id="43a01-179">Here are several tests that test the Stop-Proc cmdlet.</span></span> <span data-ttu-id="43a01-180">Zie aan de slag [met Windows Power shell](/powershell/scripting/getting-started/getting-started-with-windows-powershell)voor meer informatie over het gebruik van cmdlets vanaf de opdracht regel.</span><span class="sxs-lookup"><span data-stu-id="43a01-180">For more information about using cmdlets from the command line, see the [Getting Started with Windows PowerShell](/powershell/scripting/getting-started/getting-started-with-windows-powershell).</span></span>

- <span data-ttu-id="43a01-181">Start Windows Power shell en gebruik de cmdlet stop-proc om de verwerking te stoppen, zoals hieronder wordt weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="43a01-181">Start Windows PowerShell and use the Stop-Proc cmdlet to stop processing as shown below.</span></span> <span data-ttu-id="43a01-182">Omdat de cmdlet de `Name` para meter als verplicht opgeeft, vraagt de cmdlet naar de para meter.</span><span class="sxs-lookup"><span data-stu-id="43a01-182">Because the cmdlet specifies the `Name` parameter as mandatory, the cmdlet queries for the parameter.</span></span>

    ```powershell
    PS> stop-proc
    ```

    <span data-ttu-id="43a01-183">De volgende uitvoer wordt weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="43a01-183">The following output appears.</span></span>

    ```
    Cmdlet stop-proc at command pipeline position 1
    Supply values for the following parameters:
    Name[0]:
    ```

- <span data-ttu-id="43a01-184">We gaan nu de cmdlet gebruiken om het proces met de naam ' NOTEPAD ' te stoppen.</span><span class="sxs-lookup"><span data-stu-id="43a01-184">Now let's use the cmdlet to stop the process named "NOTEPAD".</span></span> <span data-ttu-id="43a01-185">De cmdlet vraagt u om de actie te bevestigen.</span><span class="sxs-lookup"><span data-stu-id="43a01-185">The cmdlet asks you to confirm the action.</span></span>

    ```powershell
    PS> stop-proc -Name notepad
    ```

    <span data-ttu-id="43a01-186">De volgende uitvoer wordt weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="43a01-186">The following output appears.</span></span>

    ```
    Confirm
    Are you sure you want to perform this action?
    Performing operation "stop-proc" on Target "notepad (4996)".
    [Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "Y"): Y
    ```

- <span data-ttu-id="43a01-187">Stop-proc gebruiken zoals wordt weer gegeven om het kritieke proces met de naam ' WINLOGON ' te stoppen.</span><span class="sxs-lookup"><span data-stu-id="43a01-187">Use Stop-Proc as shown to stop the critical process named "WINLOGON".</span></span> <span data-ttu-id="43a01-188">U wordt gevraagd om deze actie uit te voeren, omdat het besturings systeem hierdoor opnieuw wordt opgestart.</span><span class="sxs-lookup"><span data-stu-id="43a01-188">You are prompted and warned about performing this action because it will cause the operating system to reboot.</span></span>

    ```powershell
    PS> stop-proc -Name Winlogon
    ```

    <span data-ttu-id="43a01-189">De volgende uitvoer wordt weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="43a01-189">The following output appears.</span></span>

    ```output
    Confirm
    Are you sure you want to perform this action?
    Performing operation "stop-proc" on Target "winlogon (656)".
    [Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "Y"): Y
    Warning!
    The process " winlogon " is a critical process and should not be stopped. Are you sure you wish to stop the process?
    [Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "Y"): N
    ```

- <span data-ttu-id="43a01-190">We gaan nu proberen het WINLOGON-proces te stoppen zonder een waarschuwing te ontvangen.</span><span class="sxs-lookup"><span data-stu-id="43a01-190">Let's now try to stop the WINLOGON process without receiving a warning.</span></span> <span data-ttu-id="43a01-191">Houd er rekening mee dat deze opdracht invoer de `Force` para meter gebruikt om de waarschuwing te onderdrukken.</span><span class="sxs-lookup"><span data-stu-id="43a01-191">Be aware that this command entry uses the `Force` parameter to override the warning.</span></span>

    ```powershell
    PS> stop-proc -Name winlogon -Force
    ```

    <span data-ttu-id="43a01-192">De volgende uitvoer wordt weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="43a01-192">The following output appears.</span></span>

    ```output
    Confirm
    Are you sure you want to perform this action?
    Performing operation "stop-proc" on Target "winlogon (656)".
    [Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "Y"): N
    ```

## <a name="see-also"></a><span data-ttu-id="43a01-193">Zie ook</span><span class="sxs-lookup"><span data-stu-id="43a01-193">See Also</span></span>

[<span data-ttu-id="43a01-194">Para meters toevoegen die opdracht regel invoer verwerken</span><span class="sxs-lookup"><span data-stu-id="43a01-194">Adding Parameters that Process Command-Line Input</span></span>](./adding-parameters-that-process-command-line-input.md)

<span data-ttu-id="43a01-195">[Object typen en-opmaak uitbreiden](/previous-versions//ms714665(v=vs.85))</span><span class="sxs-lookup"><span data-stu-id="43a01-195">[Extending Object Types and Formatting](/previous-versions//ms714665(v=vs.85))</span></span>

<span data-ttu-id="43a01-196">[Cmdlets, providers en hosttoepassingen registreren](/previous-versions//ms714644(v=vs.85))</span><span class="sxs-lookup"><span data-stu-id="43a01-196">[How to Register Cmdlets, Providers, and Host Applications](/previous-versions//ms714644(v=vs.85))</span></span>

[<span data-ttu-id="43a01-197">Windows PowerShell SDK</span><span class="sxs-lookup"><span data-stu-id="43a01-197">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)

[<span data-ttu-id="43a01-198">Cmdlet-voorbeelden</span><span class="sxs-lookup"><span data-stu-id="43a01-198">Cmdlet Samples</span></span>](./cmdlet-samples.md)
