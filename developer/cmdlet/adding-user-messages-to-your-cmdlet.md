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
ms.openlocfilehash: 138c6a43937e72fffaa2a09243e500e9822e6111
ms.sourcegitcommit: 01b81317029b28dd9b61d167045fd31f1ec7bc06
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 05/17/2019
ms.locfileid: "65854925"
---
# <a name="adding-user-messages-to-your-cmdlet"></a><span data-ttu-id="30a87-102">Gebruikersberichten toevoegen aan uw cmdlet</span><span class="sxs-lookup"><span data-stu-id="30a87-102">Adding User Messages to Your Cmdlet</span></span>

<span data-ttu-id="30a87-103">Cmdlets kunt schrijven die verschillende soorten berichten die door de Windows PowerShell-runtime voor de gebruiker kunnen worden weergegeven.</span><span class="sxs-lookup"><span data-stu-id="30a87-103">Cmdlets can write several kinds of messages that can be displayed to the user by the Windows PowerShell runtime.</span></span> <span data-ttu-id="30a87-104">Deze berichten zijn onder andere de volgende typen:</span><span class="sxs-lookup"><span data-stu-id="30a87-104">These messages include the following types:</span></span>

- <span data-ttu-id="30a87-105">Uitgebreide berichten waarin algemene informatie.</span><span class="sxs-lookup"><span data-stu-id="30a87-105">Verbose messages that contain general user information.</span></span>

- <span data-ttu-id="30a87-106">Fouten opsporen in berichten die informatie over probleemoplossing bevatten.</span><span class="sxs-lookup"><span data-stu-id="30a87-106">Debug messages that contain troubleshooting information.</span></span>

- <span data-ttu-id="30a87-107">Waarschuwingsberichten die bevatten een melding dat de cmdlet wordt een bewerking waarvoor kan onverwachte resultaten.</span><span class="sxs-lookup"><span data-stu-id="30a87-107">Warning messages that contain a notification that the cmdlet is about to perform an operation that can have unexpected results.</span></span>

- <span data-ttu-id="30a87-108">Voortgangsrapport berichten die informatie over hoeveel bevatten werken de cmdlet is voltooid bij het uitvoeren van een bewerking die lange tijd in beslag neemt.</span><span class="sxs-lookup"><span data-stu-id="30a87-108">Progress report messages that contain information about how much work the cmdlet has completed when performing an operation that takes a long time.</span></span>

<span data-ttu-id="30a87-109">Er zijn geen beperkingen op het aantal berichten dat uw cmdlet kan schrijven of het type berichten die uw cmdlet schrijft.</span><span class="sxs-lookup"><span data-stu-id="30a87-109">There are no limits to the number of messages that your cmdlet can write or the type of messages that your cmdlet writes.</span></span> <span data-ttu-id="30a87-110">Elk bericht is geschreven door een specifieke aanroep uit binnen de invoer-methode van de cmdlet verwerkt.</span><span class="sxs-lookup"><span data-stu-id="30a87-110">Each message is written by making a specific call from within the input processing method of your cmdlet.</span></span>

## <a name="defining-the-cmdlet"></a><span data-ttu-id="30a87-111">De Cmdlet definiëren</span><span class="sxs-lookup"><span data-stu-id="30a87-111">Defining the Cmdlet</span></span>

<span data-ttu-id="30a87-112">De eerste stap bij het maken van de cmdlet is altijd naamgeving van de cmdlet en de .NET-klasse die de cmdlet declareren.</span><span class="sxs-lookup"><span data-stu-id="30a87-112">The first step in cmdlet creation is always naming the cmdlet and declaring the .NET class that implements the cmdlet.</span></span> <span data-ttu-id="30a87-113">Een of andere vorm van cmdlet kunt meldingen voor gebruikers van de verwerking van methoden; invoer schrijven dus in het algemeen kunt u naam deze cmdlet met behulp van een bewerking die aangeeft welke system wijzigingen die de cmdlet uitvoert.</span><span class="sxs-lookup"><span data-stu-id="30a87-113">Any sort of cmdlet can write user notifications from its input processing methods; so, in general, you can name this cmdlet using any verb that indicates what system modifications the cmdlet performs.</span></span> <span data-ttu-id="30a87-114">Zie voor meer informatie over goedgekeurde werkwoorden [namen van de term cmdlets](./approved-verbs-for-windows-powershell-commands.md).</span><span class="sxs-lookup"><span data-stu-id="30a87-114">For more information about approved cmdlet verbs, see [Cmdlet Verb Names](./approved-verbs-for-windows-powershell-commands.md).</span></span>

<span data-ttu-id="30a87-115">De cmdlet Stop-Proc is ontworpen om te wijzigen van het systeem. daarom de [System.Management.Automation.CmdletAttribute](/dotnet/api/System.Management.Automation.CmdletAttribute) -declaratie voor de .NET-klasse moet bevatten de `SupportsShouldProcess` sleutelwoord kenmerk hebben en worden ingesteld op `true`.</span><span class="sxs-lookup"><span data-stu-id="30a87-115">The Stop-Proc cmdlet is designed to modify the system; therefore, the [System.Management.Automation.CmdletAttribute](/dotnet/api/System.Management.Automation.CmdletAttribute) declaration for the .NET class must include the `SupportsShouldProcess` attribute keyword and be set to `true`.</span></span>

<span data-ttu-id="30a87-116">De volgende code is de definitie voor deze cmdlet Stop-Proc klasse.</span><span class="sxs-lookup"><span data-stu-id="30a87-116">The following code is the definition for this Stop-Proc cmdlet class.</span></span> <span data-ttu-id="30a87-117">Zie voor meer informatie over deze definitie [maken van een Cmdlet die Hiermee wijzigt u het systeem](./creating-a-cmdlet-that-modifies-the-system.md).</span><span class="sxs-lookup"><span data-stu-id="30a87-117">For more information about this definition, see [Creating a Cmdlet that Modifies the System](./creating-a-cmdlet-that-modifies-the-system.md).</span></span>

```csharp
[Cmdlet(VerbsLifecycle.Stop, "proc",
        SupportsShouldProcess = true)]
public class StopProcCommand : Cmdlet
```

## <a name="defining-parameters-for-system-modification"></a><span data-ttu-id="30a87-118">Parameters voor aanpassing van het systeem definiëren</span><span class="sxs-lookup"><span data-stu-id="30a87-118">Defining Parameters for System Modification</span></span>

<span data-ttu-id="30a87-119">De cmdlet Stop-Proc definieert drie parameters: `Name`, `Force`, en `PassThru`.</span><span class="sxs-lookup"><span data-stu-id="30a87-119">The Stop-Proc cmdlet defines three parameters: `Name`, `Force`, and `PassThru`.</span></span> <span data-ttu-id="30a87-120">Zie voor meer informatie over het definiëren van deze parameters [maken van een Cmdlet die Hiermee wijzigt u het systeem](./creating-a-cmdlet-that-modifies-the-system.md).</span><span class="sxs-lookup"><span data-stu-id="30a87-120">For more information about defining these parameters, see [Creating a Cmdlet that Modifies the System](./creating-a-cmdlet-that-modifies-the-system.md).</span></span>

<span data-ttu-id="30a87-121">Hier is de parameterdeclaratie voor de cmdlet Stop-Proc.</span><span class="sxs-lookup"><span data-stu-id="30a87-121">Here is the parameter declaration for the Stop-Proc cmdlet.</span></span>

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

## <a name="overriding-an-input-processing-method"></a><span data-ttu-id="30a87-122">Invoer verwerken methode te overschrijven</span><span class="sxs-lookup"><span data-stu-id="30a87-122">Overriding an Input Processing Method</span></span>

<span data-ttu-id="30a87-123">De cmdlet moet verwerken van methode invoer overschrijven, meestal worden [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord).</span><span class="sxs-lookup"><span data-stu-id="30a87-123">Your cmdlet must override an input processing method, most often it will be [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord).</span></span> <span data-ttu-id="30a87-124">Deze cmdlet Stop-Proc overschrijft de [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) invoermethode voor verwerking.</span><span class="sxs-lookup"><span data-stu-id="30a87-124">This Stop-Proc cmdlet overrides the [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) input processing method.</span></span> <span data-ttu-id="30a87-125">In deze implementatie van de cmdlet Stop-Proc worden aangeroepen om uitgebreide berichten, Foutopsporingsberichten en waarschuwingen te schrijven.</span><span class="sxs-lookup"><span data-stu-id="30a87-125">In this implementation of the Stop-Proc cmdlet, calls are made to write verbose messages, debug messages, and warning messages.</span></span>

> [!NOTE]
> <span data-ttu-id="30a87-126">Voor meer informatie over hoe deze methode roept de [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) en [System.Management.Automation.Cmdlet.ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) methoden, Zie [Maken van een Cmdlet die Hiermee wijzigt u het systeem](./creating-a-cmdlet-that-modifies-the-system.md).</span><span class="sxs-lookup"><span data-stu-id="30a87-126">For more information about how this method calls the [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) and [System.Management.Automation.Cmdlet.ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) methods, see [Creating a Cmdlet that Modifies the System](./creating-a-cmdlet-that-modifies-the-system.md).</span></span>

## <a name="writing-a-verbose-message"></a><span data-ttu-id="30a87-127">Een uitgebreid bericht schrijven</span><span class="sxs-lookup"><span data-stu-id="30a87-127">Writing a Verbose Message</span></span>

<span data-ttu-id="30a87-128">De [System.Management.Automation.Cmdlet.WriteVerbose](/dotnet/api/System.Management.Automation.Cmdlet.WriteVerbose) methode wordt gebruikt om algemene op gebruikersniveau informatie die is gerelateerd aan bepaalde voorwaarden te schrijven.</span><span class="sxs-lookup"><span data-stu-id="30a87-128">The [System.Management.Automation.Cmdlet.WriteVerbose](/dotnet/api/System.Management.Automation.Cmdlet.WriteVerbose) method is used to write general user-level information that is unrelated to specific error conditions.</span></span> <span data-ttu-id="30a87-129">De systeembeheerder kunt die informatie vervolgens gebruiken om door te gaan met het verwerken van andere opdrachten.</span><span class="sxs-lookup"><span data-stu-id="30a87-129">The system administrator can then use that information to continue processing other commands.</span></span> <span data-ttu-id="30a87-130">Alle gegevens die zijn geschreven met deze methode moet bovendien zo nodig worden gelokaliseerd.</span><span class="sxs-lookup"><span data-stu-id="30a87-130">In addition, any information written using this method should be localized as needed.</span></span>

<span data-ttu-id="30a87-131">De volgende code uit deze cmdlet Stop-Proc toont twee verzoeken aan de [System.Management.Automation.Cmdlet.WriteVerbose](/dotnet/api/System.Management.Automation.Cmdlet.WriteVerbose) methode van de onderdrukking van de [System.Management.Automation.Cmdlet.ProcessRecord ](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) methode.</span><span class="sxs-lookup"><span data-stu-id="30a87-131">The following code from this Stop-Proc cmdlet shows two calls to the [System.Management.Automation.Cmdlet.WriteVerbose](/dotnet/api/System.Management.Automation.Cmdlet.WriteVerbose) method from the override of the [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) method.</span></span>

```csharp
message = String.Format("Attempting to stop process \"{0}\".", name);
WriteVerbose(message);
```

```csharp
message = String.Format("Stopped process \"{0}\", pid {1}.",
                        processName, process.Id);

WriteVerbose(message);
```

## <a name="writing-a-debug-message"></a><span data-ttu-id="30a87-132">Geen foutopsporingsbericht schrijven</span><span class="sxs-lookup"><span data-stu-id="30a87-132">Writing a Debug Message</span></span>

<span data-ttu-id="30a87-133">De [System.Management.Automation.Cmdlet.WriteDebug](/dotnet/api/System.Management.Automation.Cmdlet.WriteDebug) methode wordt gebruikt om te schrijven foutopsporingsberichten die kunnen worden gebruikt om op te lossen van de werking van de cmdlet.</span><span class="sxs-lookup"><span data-stu-id="30a87-133">The [System.Management.Automation.Cmdlet.WriteDebug](/dotnet/api/System.Management.Automation.Cmdlet.WriteDebug) method is used to write debug messages that can be used to troubleshoot the operation of the cmdlet.</span></span> <span data-ttu-id="30a87-134">De aanroep wordt uitgevoerd vanaf een invoer verwerken van methode.</span><span class="sxs-lookup"><span data-stu-id="30a87-134">The call is made from an input processing method.</span></span>

> [!NOTE]
> <span data-ttu-id="30a87-135">Windows PowerShell ook definieert een `Debug` parameter geeft beide uitgebreide en informatie voor foutopsporing.</span><span class="sxs-lookup"><span data-stu-id="30a87-135">Windows PowerShell also defines a `Debug` parameter that presents both verbose and debug information.</span></span> <span data-ttu-id="30a87-136">Als uw cmdlet biedt ondersteuning voor deze parameter, hoeft deze niet aan te roepen [System.Management.Automation.Cmdlet.WriteDebug](/dotnet/api/System.Management.Automation.Cmdlet.WriteDebug) in dezelfde code die worden aangeroepen [System.Management.Automation.Cmdlet.WriteVerbose](/dotnet/api/System.Management.Automation.Cmdlet.WriteVerbose) .</span><span class="sxs-lookup"><span data-stu-id="30a87-136">If your cmdlet supports this parameter, it does not need to call [System.Management.Automation.Cmdlet.WriteDebug](/dotnet/api/System.Management.Automation.Cmdlet.WriteDebug) in the same code that calls [System.Management.Automation.Cmdlet.WriteVerbose](/dotnet/api/System.Management.Automation.Cmdlet.WriteVerbose).</span></span>

<span data-ttu-id="30a87-137">De volgende twee secties van de code van de voorbeeld-cmdlet Stop-Proc weergeven aanroepen naar de [System.Management.Automation.Cmdlet.WriteDebug](/dotnet/api/System.Management.Automation.Cmdlet.WriteDebug) methode van de onderdrukking van de [ System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) methode.</span><span class="sxs-lookup"><span data-stu-id="30a87-137">The following two sections of code from the sample Stop-Proc cmdlet show calls to the [System.Management.Automation.Cmdlet.WriteDebug](/dotnet/api/System.Management.Automation.Cmdlet.WriteDebug) method from the override of the [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) method.</span></span>

<span data-ttu-id="30a87-138">Dit foutopsporingsbericht wordt geschreven direct vóór de [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) wordt genoemd.</span><span class="sxs-lookup"><span data-stu-id="30a87-138">This debug message is written immediately before [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) is called.</span></span>

```csharp
message =
          String.Format("Acquired name for pid {0} : \"{1}\"",
                       process.Id, processName);
WriteDebug(message);
```

<span data-ttu-id="30a87-139">Dit foutopsporingsbericht wordt geschreven direct vóór de [System.Management.Automation.Cmdlet.WriteObject](/dotnet/api/System.Management.Automation.Cmdlet.WriteObject) wordt genoemd.</span><span class="sxs-lookup"><span data-stu-id="30a87-139">This debug message is written immediately before [System.Management.Automation.Cmdlet.WriteObject](/dotnet/api/System.Management.Automation.Cmdlet.WriteObject) is called.</span></span>

```csharp
message =
         String.Format("Writing process \"{0}\" to pipeline",
         processName);
WriteDebug(message);
WriteObject(process);
```

<span data-ttu-id="30a87-140">Windows PowerShell automatisch stuurt een [System.Management.Automation.Cmdlet.WriteDebug](/dotnet/api/System.Management.Automation.Cmdlet.WriteDebug) aanroepen naar de van traceringsinfrastructuur en -cmdlets.</span><span class="sxs-lookup"><span data-stu-id="30a87-140">Windows PowerShell automatically routes any [System.Management.Automation.Cmdlet.WriteDebug](/dotnet/api/System.Management.Automation.Cmdlet.WriteDebug) calls to the tracing infrastructure and cmdlets.</span></span> <span data-ttu-id="30a87-141">Hiermee wordt de methodeaanroepen zonder deze aan de ontwikkeling van extra werk binnen de cmdlet, worden herleid tot de hosttoepassing, een bestand of een foutopsporingsprogramma.</span><span class="sxs-lookup"><span data-stu-id="30a87-141">This allows the method calls to be traced to the hosting application, a file, or a debugger without your having to do any extra development work within the cmdlet.</span></span> <span data-ttu-id="30a87-142">De volgende opdrachtregel vermelding implementeert een tracering-bewerking.</span><span class="sxs-lookup"><span data-stu-id="30a87-142">The following command-line entry implements a tracing operation.</span></span>

<span data-ttu-id="30a87-143">**PS > trace-expressie stop-proc-bestand proc.log-opdracht stop-proc Kladblok**</span><span class="sxs-lookup"><span data-stu-id="30a87-143">**PS> trace-expression stop-proc -file proc.log -command stop-proc notepad**</span></span>

## <a name="writing-a-warning-message"></a><span data-ttu-id="30a87-144">Schrijven van een waarschuwingsbericht wordt weergegeven</span><span class="sxs-lookup"><span data-stu-id="30a87-144">Writing a Warning Message</span></span>

<span data-ttu-id="30a87-145">De [System.Management.Automation.Cmdlet.WriteWarning](/dotnet/api/System.Management.Automation.Cmdlet.WriteWarning) methode wordt gebruikt voor het schrijven van een waarschuwing wanneer de cmdlet wordt een bewerking die mogelijk een onverwacht resultaat, bijvoorbeeld een alleen-lezen-bestand te overschrijven.</span><span class="sxs-lookup"><span data-stu-id="30a87-145">The [System.Management.Automation.Cmdlet.WriteWarning](/dotnet/api/System.Management.Automation.Cmdlet.WriteWarning) method is used to write a warning when the cmdlet is about to perform an operation that might have an unexpected result, for example, overwriting a read-only file.</span></span>

<span data-ttu-id="30a87-146">De volgende code uit de voorbeeld-cmdlet Stop-Proc toont het aanroepen van de [System.Management.Automation.Cmdlet.WriteWarning](/dotnet/api/System.Management.Automation.Cmdlet.WriteWarning) methode van de onderdrukking van de [ System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) methode.</span><span class="sxs-lookup"><span data-stu-id="30a87-146">The following code from the sample Stop-Proc cmdlet shows the call to the [System.Management.Automation.Cmdlet.WriteWarning](/dotnet/api/System.Management.Automation.Cmdlet.WriteWarning) method from the override of the [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) method.</span></span>

```csharp
 if (criticalProcess)
 {
   message =
             String.Format("Stopping the critical process \"{0}\".",
                           processName);
   WriteWarning(message);
} // if (criticalProcess...
```

## <a name="writing-a-progress-message"></a><span data-ttu-id="30a87-147">Schrijven van een bericht wordt uitgevoerd</span><span class="sxs-lookup"><span data-stu-id="30a87-147">Writing a Progress Message</span></span>

<span data-ttu-id="30a87-148">De [System.Management.Automation.Cmdlet.WriteProgress](/dotnet/api/System.Management.Automation.Cmdlet.WriteProgress) wordt gebruikt voor het schrijven van berichten over de voortgang bij bewerkingen van de cmdlet een uitgebreide hoeveelheid tijd in beslag nemen.</span><span class="sxs-lookup"><span data-stu-id="30a87-148">The [System.Management.Automation.Cmdlet.WriteProgress](/dotnet/api/System.Management.Automation.Cmdlet.WriteProgress) is used to write progress messages when cmdlet operations take an extended amount of time to complete.</span></span> <span data-ttu-id="30a87-149">Een aanroep van [System.Management.Automation.Cmdlet.WriteProgress](/dotnet/api/System.Management.Automation.Cmdlet.WriteProgress) geeft een [System.Management.Automation.Progressrecord](/dotnet/api/System.Management.Automation.ProgressRecord) -object dat wordt verzonden naar de hosttoepassing voor rendering aan de gebruiker.</span><span class="sxs-lookup"><span data-stu-id="30a87-149">A call to [System.Management.Automation.Cmdlet.WriteProgress](/dotnet/api/System.Management.Automation.Cmdlet.WriteProgress) passes a [System.Management.Automation.Progressrecord](/dotnet/api/System.Management.Automation.ProgressRecord) object that is sent to the hosting application for rendering to the user.</span></span>

> [!NOTE]
> <span data-ttu-id="30a87-150">Deze cmdlet Stop-Proc bevat geen een aanroep naar de [System.Management.Automation.Cmdlet.WriteProgress](/dotnet/api/System.Management.Automation.Cmdlet.WriteProgress) methode.</span><span class="sxs-lookup"><span data-stu-id="30a87-150">This Stop-Proc cmdlet does not include a call to the [System.Management.Automation.Cmdlet.WriteProgress](/dotnet/api/System.Management.Automation.Cmdlet.WriteProgress) method.</span></span>

<span data-ttu-id="30a87-151">De volgende code is een voorbeeld van een bericht Bezig is geschreven door een cmdlet die probeert een item te kopiëren.</span><span class="sxs-lookup"><span data-stu-id="30a87-151">The following code is an example of a progress message written by a cmdlet that is attempting to copy an item.</span></span>

```csharp
int myId = 0;
string myActivity = "Copy-item: Copying *.* to c:\abc";
string myStatus = "Copying file bar.txt";
ProgressRecord pr = new ProgressRecord(myId, myActivity, myStatus);
WriteProgress(pr);

pr.RecordType = ProgressRecordType.Completed;
WriteProgress(pr);
```

## <a name="code-sample"></a><span data-ttu-id="30a87-152">Voorbeeld van code</span><span class="sxs-lookup"><span data-stu-id="30a87-152">Code Sample</span></span>

<span data-ttu-id="30a87-153">Voor de volledige C# voorbeeldcode, Zie [StopProcessSample02 voorbeeld](./stopprocesssample02-sample.md).</span><span class="sxs-lookup"><span data-stu-id="30a87-153">For the complete C# sample code, see [StopProcessSample02 Sample](./stopprocesssample02-sample.md).</span></span>

## <a name="define-object-types-and-formatting"></a><span data-ttu-id="30a87-154">Definieer objecttypen en opmaak</span><span class="sxs-lookup"><span data-stu-id="30a87-154">Define Object Types and Formatting</span></span>

<span data-ttu-id="30a87-155">Windows PowerShell wordt informatie doorgegeven tussen cmdlets met behulp van .NET-objecten.</span><span class="sxs-lookup"><span data-stu-id="30a87-155">Windows PowerShell passes information between cmdlets using .NET objects.</span></span> <span data-ttu-id="30a87-156">Als gevolg daarvan kan een cmdlet mogelijk voor het definiëren van een eigen type of de cmdlet moet mogelijk om uit te breiden van een bestaand type geleverd door een andere cmdlet.</span><span class="sxs-lookup"><span data-stu-id="30a87-156">Consequently, a cmdlet might need to define its own type, or the cmdlet might need to extend an existing type provided by another cmdlet.</span></span> <span data-ttu-id="30a87-157">Zie voor meer informatie over het definiëren van nieuwe typen of uitbreiden van bestaande typen [objecttypen uitbreiden en opmaak](http://msdn.microsoft.com/en-us/da976d91-a3d6-44e8-affa-466b1e2bd351).</span><span class="sxs-lookup"><span data-stu-id="30a87-157">For more information about defining new types or extending existing types, see [Extending Object Types and Formatting](http://msdn.microsoft.com/en-us/da976d91-a3d6-44e8-affa-466b1e2bd351).</span></span>

## <a name="building-the-cmdlet"></a><span data-ttu-id="30a87-158">Het bouwen van de Cmdlet</span><span class="sxs-lookup"><span data-stu-id="30a87-158">Building the Cmdlet</span></span>

<span data-ttu-id="30a87-159">Na de implementatie van een cmdlet, moet deze met Windows PowerShell worden geregistreerd via een Windows PowerShell-module.</span><span class="sxs-lookup"><span data-stu-id="30a87-159">After implementing a cmdlet, it must be registered with Windows PowerShell through a Windows PowerShell snap-in.</span></span> <span data-ttu-id="30a87-160">Zie voor meer informatie over het registreren van cmdlets [hoe u Cmdlets registreren, Providers en hosting van toepassingen](http://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c).</span><span class="sxs-lookup"><span data-stu-id="30a87-160">For more information about registering cmdlets, see [How to Register Cmdlets, Providers, and Host Applications](http://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c).</span></span>

## <a name="testing-the-cmdlet"></a><span data-ttu-id="30a87-161">Testen van de Cmdlet</span><span class="sxs-lookup"><span data-stu-id="30a87-161">Testing the Cmdlet</span></span>

<span data-ttu-id="30a87-162">Wanneer de cmdlet is geregistreerd met Windows PowerShell, kunt u deze testen door te voeren op de opdrachtregel.</span><span class="sxs-lookup"><span data-stu-id="30a87-162">When your cmdlet has been registered with Windows PowerShell, you can test it by running it on the command line.</span></span> <span data-ttu-id="30a87-163">We gaan de voorbeeld-cmdlet Stop-Proc testen.</span><span class="sxs-lookup"><span data-stu-id="30a87-163">Let's test the sample Stop-Proc cmdlet.</span></span> <span data-ttu-id="30a87-164">Zie voor meer informatie over het gebruik van cmdlets vanaf de opdrachtregel de [aan de slag met Windows PowerShell](/powershell/scripting/getting-started/getting-started-with-windows-powershell).</span><span class="sxs-lookup"><span data-stu-id="30a87-164">For more information about using cmdlets from the command line, see the [Getting Started with Windows PowerShell](/powershell/scripting/getting-started/getting-started-with-windows-powershell).</span></span>

- <span data-ttu-id="30a87-165">De volgende vermelding in de opdrachtregel gebruikt Stop-Proc voor het stoppen van het proces met de naam "KLADBLOK", bieden uitgebreide meldingen en gegevens voor foutopsporing afdrukken.</span><span class="sxs-lookup"><span data-stu-id="30a87-165">The following command-line entry uses Stop-Proc to stop the process named "NOTEPAD", provide verbose notifications, and print debug information.</span></span>

    ```powershell
    PS> stop-proc -Name notepad -Verbose -Debug
    ```

<span data-ttu-id="30a87-166">De volgende uitvoer wordt weergegeven.</span><span class="sxs-lookup"><span data-stu-id="30a87-166">The following output appears.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="30a87-167">Zie ook</span><span class="sxs-lookup"><span data-stu-id="30a87-167">See Also</span></span>

[<span data-ttu-id="30a87-168">Maken van een Cmdlet die Hiermee wijzigt u het systeem</span><span class="sxs-lookup"><span data-stu-id="30a87-168">Create a Cmdlet that Modifies the System</span></span>](./creating-a-cmdlet-that-modifies-the-system.md)

[<span data-ttu-id="30a87-169">Over het maken van een Windows PowerShell-Cmdlet</span><span class="sxs-lookup"><span data-stu-id="30a87-169">How to Create a Windows PowerShell Cmdlet</span></span>](http://msdn.microsoft.com/en-us/0d721742-c849-4d0d-964f-78ddd9cd258c)

[<span data-ttu-id="30a87-170">Objecttypen uitbreiden en opmaak</span><span class="sxs-lookup"><span data-stu-id="30a87-170">Extending Object Types and Formatting</span></span>](http://msdn.microsoft.com/en-us/da976d91-a3d6-44e8-affa-466b1e2bd351)

[<span data-ttu-id="30a87-171">Over het registreren van Providers,-Cmdlets en -toepassingen hosten</span><span class="sxs-lookup"><span data-stu-id="30a87-171">How to Register Cmdlets, Providers, and Host Applications</span></span>](http://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c)

[<span data-ttu-id="30a87-172">Windows PowerShell SDK</span><span class="sxs-lookup"><span data-stu-id="30a87-172">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)
