---
ms.date: 09/13/2016
ms.topic: reference
title: Parameters toevoegen die opdrachtregelinvoer verwerken
description: Parameters toevoegen die opdrachtregelinvoer verwerken
ms.openlocfilehash: f20469d366330aa787fbc16e4f0a76e67fc7c6db
ms.sourcegitcommit: 39c2a697228276d5dae39e540995fa479c2b5f39
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 11/05/2020
ms.locfileid: "93354606"
---
# <a name="adding-parameters-that-process-command-line-input"></a><span data-ttu-id="678da-103">Parameters toevoegen die opdrachtregelinvoer verwerken</span><span class="sxs-lookup"><span data-stu-id="678da-103">Adding Parameters That Process Command-Line Input</span></span>

<span data-ttu-id="678da-104">De eerste invoer bron voor een cmdlet is de opdracht regel.</span><span class="sxs-lookup"><span data-stu-id="678da-104">One source of input for a cmdlet is the command line.</span></span> <span data-ttu-id="678da-105">In dit onderwerp wordt beschreven hoe u een para meter kunt toevoegen aan de `Get-Proc` cmdlet (die wordt beschreven in [uw eerste cmdlet maken](./creating-a-cmdlet-without-parameters.md)), zodat de cmdlet invoer van de lokale computer kan verwerken op basis van expliciete objecten die aan de cmdlet worden door gegeven.</span><span class="sxs-lookup"><span data-stu-id="678da-105">This topic describes how to add a parameter to the `Get-Proc` cmdlet (which is described in [Creating Your First Cmdlet](./creating-a-cmdlet-without-parameters.md)) so that the cmdlet can process input from the local computer based on explicit objects passed to the cmdlet.</span></span> <span data-ttu-id="678da-106">`Get-Proc`Met de cmdlet die hier wordt beschreven, worden processen opgehaald op basis van hun namen en wordt vervolgens informatie weer gegeven over de processen bij een opdracht prompt.</span><span class="sxs-lookup"><span data-stu-id="678da-106">The `Get-Proc` cmdlet described here retrieves processes based on their names, and then displays information about the processes at a command prompt.</span></span>

## <a name="defining-the-cmdlet-class"></a><span data-ttu-id="678da-107">De cmdlet-klasse definiëren</span><span class="sxs-lookup"><span data-stu-id="678da-107">Defining the Cmdlet Class</span></span>

<span data-ttu-id="678da-108">De eerste stap bij het maken van de cmdlet is de naam van de cmdlet en de declaratie van de .NET Framework klasse die de cmdlet implementeert.</span><span class="sxs-lookup"><span data-stu-id="678da-108">The first step in cmdlet creation is cmdlet naming and the declaration of the .NET Framework class that implements the cmdlet.</span></span> <span data-ttu-id="678da-109">Met deze cmdlet worden proces gegevens opgehaald, zodat de naam van de term ' Get ' is.</span><span class="sxs-lookup"><span data-stu-id="678da-109">This cmdlet retrieves process information, so the verb name chosen here is "Get."</span></span> <span data-ttu-id="678da-110">(Bijna elk soort cmdlet waarmee informatie kan worden opgehaald, kan opdracht regel invoer verwerken.) Zie [cmdlet verb names](./approved-verbs-for-windows-powershell-commands.md)(Engelstalig) voor meer informatie over goedgekeurde cmdlet-termen.</span><span class="sxs-lookup"><span data-stu-id="678da-110">(Almost any sort of cmdlet that is capable of retrieving information can process command-line input.) For more information about approved cmdlet verbs, see [Cmdlet Verb Names](./approved-verbs-for-windows-powershell-commands.md).</span></span>

<span data-ttu-id="678da-111">Hier is de klassen declaratie voor de `Get-Proc` cmdlet.</span><span class="sxs-lookup"><span data-stu-id="678da-111">Here's the class declaration for the `Get-Proc` cmdlet.</span></span> <span data-ttu-id="678da-112">Meer informatie over deze definitie vindt u in [het maken van uw eerste cmdlet](./creating-a-cmdlet-without-parameters.md).</span><span class="sxs-lookup"><span data-stu-id="678da-112">Details about this definition are provided in [Creating Your First Cmdlet](./creating-a-cmdlet-without-parameters.md).</span></span>

```csharp
[Cmdlet(VerbsCommon.Get, "proc")]
public class GetProcCommand: Cmdlet
```

```vb
<Cmdlet(VerbsCommon.Get, "Proc")> _
Public Class GetProcCommand
    Inherits Cmdlet
```

## <a name="declaring-parameters"></a><span data-ttu-id="678da-113">Para meters declareren</span><span class="sxs-lookup"><span data-stu-id="678da-113">Declaring Parameters</span></span>

<span data-ttu-id="678da-114">Met een cmdlet-para meter kan de gebruiker invoer opgeven voor de cmdlet.</span><span class="sxs-lookup"><span data-stu-id="678da-114">A cmdlet parameter enables the user to provide input to the cmdlet.</span></span> <span data-ttu-id="678da-115">In het volgende voor beeld `Get-Proc` `Get-Member` zijn de namen van pijplijn-cmdlets en `MemberType` is een para meter voor de `Get-Member` cmdlet.</span><span class="sxs-lookup"><span data-stu-id="678da-115">In the following example, `Get-Proc` and `Get-Member` are the names of pipelined cmdlets, and `MemberType` is a parameter for the `Get-Member` cmdlet.</span></span> <span data-ttu-id="678da-116">De para meter heeft het argument ' Property '.</span><span class="sxs-lookup"><span data-stu-id="678da-116">The parameter has the argument "property."</span></span>

<span data-ttu-id="678da-117">**PS> Get-proc; `get-member` -member type-eigenschap**</span><span class="sxs-lookup"><span data-stu-id="678da-117">**PS> get-proc ; `get-member` -membertype property**</span></span>

<span data-ttu-id="678da-118">Als u para meters voor een cmdlet wilt declareren, moet u eerst de eigenschappen definiëren die de para meters vertegenwoordigen.</span><span class="sxs-lookup"><span data-stu-id="678da-118">To declare parameters for a cmdlet, you must first define the properties that represent the parameters.</span></span> <span data-ttu-id="678da-119">In de `Get-Proc` cmdlet is de enige para meter `Name` , die in dit geval de naam vertegenwoordigt van het .NET Framework proces object dat moet worden opgehaald.</span><span class="sxs-lookup"><span data-stu-id="678da-119">In the `Get-Proc` cmdlet, the only parameter is `Name`, which in this case represents the name of the .NET Framework process object to retrieve.</span></span> <span data-ttu-id="678da-120">Daarom definieert de klasse cmdlet een eigenschap van het type teken reeks om een matrix met namen te accepteren.</span><span class="sxs-lookup"><span data-stu-id="678da-120">Therefore, the cmdlet class defines a property of type string to accept an array of names.</span></span>

<span data-ttu-id="678da-121">Hier ziet u de parameter declaratie voor de `Name` para meter van de `Get-Proc` cmdlet.</span><span class="sxs-lookup"><span data-stu-id="678da-121">Here's the parameter declaration for the `Name` parameter of the `Get-Proc` cmdlet.</span></span>

```csharp
/// <summary>
/// Specify the cmdlet Name parameter.
/// </summary>
  [Parameter(Position = 0)]
  [ValidateNotNullOrEmpty]
  public string[] Name
  {
    get { return processNames; }
    set { processNames = value; }
  }
  private string[] processNames;

  #endregion Parameters
```

```vb
<Parameter(Position:=0), ValidateNotNullOrEmpty()> _
Public Property Name() As String()
    Get
        Return processNames
    End Get

    Set(ByVal value As String())
        processNames = value
    End Set

End Property
```

<span data-ttu-id="678da-122">Als u de Windows Power shell-runtime wilt laten weten dat deze eigenschap de `Name` para meter is, wordt het kenmerk [System. Management. Automation. Parameterattribute](/dotnet/api/System.Management.Automation.ParameterAttribute) toegevoegd aan de eigenschaps definitie.</span><span class="sxs-lookup"><span data-stu-id="678da-122">To inform the Windows PowerShell runtime that this property is the `Name` parameter, a [System.Management.Automation.Parameterattribute](/dotnet/api/System.Management.Automation.ParameterAttribute) attribute is added to the property definition.</span></span> <span data-ttu-id="678da-123">De basis syntaxis voor het declareren van dit kenmerk is `[Parameter()]` .</span><span class="sxs-lookup"><span data-stu-id="678da-123">The basic syntax for declaring this attribute is `[Parameter()]`.</span></span>

> [!NOTE]
> <span data-ttu-id="678da-124">Een para meter moet expliciet als openbaar worden gemarkeerd.</span><span class="sxs-lookup"><span data-stu-id="678da-124">A parameter must be explicitly marked as public.</span></span> <span data-ttu-id="678da-125">Para meters die niet zijn gemarkeerd als open bare standaard waarde voor intern en niet worden gevonden door de Windows Power shell-runtime.</span><span class="sxs-lookup"><span data-stu-id="678da-125">Parameters that are not marked as public default to internal and are not found by the Windows PowerShell runtime.</span></span>

<span data-ttu-id="678da-126">Deze cmdlet gebruikt een matrix met teken reeksen voor de `Name` para meter.</span><span class="sxs-lookup"><span data-stu-id="678da-126">This cmdlet uses an array of strings for the `Name` parameter.</span></span> <span data-ttu-id="678da-127">Als dat mogelijk is, moet uw cmdlet ook een para meter definiëren als een matrix, omdat hierdoor meer dan één item kan worden geaccepteerd met de cmdlet.</span><span class="sxs-lookup"><span data-stu-id="678da-127">If possible, your cmdlet should also define a parameter as an array, because this allows the cmdlet to accept more than one item.</span></span>

#### <a name="things-to-remember-about-parameter-definitions"></a><span data-ttu-id="678da-128">Wat u moet weten over parameter definities</span><span class="sxs-lookup"><span data-stu-id="678da-128">Things to Remember About Parameter Definitions</span></span>

- <span data-ttu-id="678da-129">Vooraf gedefinieerde namen van Windows Power shell-para meters en gegevens typen moeten zo veel mogelijk worden hergebruikt om ervoor te zorgen dat uw cmdlet compatibel is met Windows Power shell-cmdlets.</span><span class="sxs-lookup"><span data-stu-id="678da-129">Predefined Windows PowerShell parameter names and data types should be reused as much as possible to ensure that your cmdlet is compatible with Windows PowerShell cmdlets.</span></span> <span data-ttu-id="678da-130">Als alle cmdlets bijvoorbeeld de naam van de vooraf gedefinieerde `Id` para meter gebruiken om een resource te identificeren, is de gebruiker eenvoudig inzicht in de betekenis van de para meter, ongeacht welke cmdlet ze gebruiken.</span><span class="sxs-lookup"><span data-stu-id="678da-130">For example, if all cmdlets use the predefined `Id` parameter name to identify a resource, user will easily understand the meaning of the parameter, regardless of what cmdlet they are using.</span></span> <span data-ttu-id="678da-131">In principe volgen de namen van para meters dezelfde regels als die worden gebruikt voor variabelenamen in de Common Language Runtime (CLR).</span><span class="sxs-lookup"><span data-stu-id="678da-131">Basically, parameter names follow the same rules as those used for variable names in the common language runtime (CLR).</span></span> <span data-ttu-id="678da-132">Zie [cmdlet para meter names](/previous-versions/ms714468(v=vs.85))(Engelstalig) voor meer informatie over de naamgeving van para meters.</span><span class="sxs-lookup"><span data-stu-id="678da-132">For more information about parameter naming, see [Cmdlet Parameter Names](/previous-versions/ms714468(v=vs.85)).</span></span>

- <span data-ttu-id="678da-133">Windows Power Shell heeft enkele parameter namen gereserveerd om een consistente gebruikers ervaring te bieden.</span><span class="sxs-lookup"><span data-stu-id="678da-133">Windows PowerShell reserves a few parameter names to provide a consistent user experience.</span></span> <span data-ttu-id="678da-134">Gebruik deze parameter namen niet: `WhatIf` ,, `Confirm` `Verbose` ,, `Debug` , `Warn` `ErrorAction` , `ErrorVariable` , `OutVariable` en `OutBuffer` .</span><span class="sxs-lookup"><span data-stu-id="678da-134">Do not use these parameter names: `WhatIf`, `Confirm`, `Verbose`, `Debug`, `Warn`, `ErrorAction`, `ErrorVariable`, `OutVariable`, and `OutBuffer`.</span></span> <span data-ttu-id="678da-135">Daarnaast zijn de volgende aliassen voor deze parameter namen gereserveerd: `vb` ,, `db` , `ea` , `ev` `ov` en `ob` .</span><span class="sxs-lookup"><span data-stu-id="678da-135">Additionally, the following aliases for these parameter names are reserved: `vb`, `db`, `ea`, `ev`, `ov`, and `ob`.</span></span>

- <span data-ttu-id="678da-136">`Name` is een eenvoudige en algemene parameter naam, aanbevolen voor gebruik in de-cmdlets.</span><span class="sxs-lookup"><span data-stu-id="678da-136">`Name` is a simple and common parameter name, recommended for use in your cmdlets.</span></span> <span data-ttu-id="678da-137">Het is beter om een parameter naam te kiezen, zoals deze, een complexe naam die uniek is voor een specifieke cmdlet en moeilijk te onthouden is.</span><span class="sxs-lookup"><span data-stu-id="678da-137">It is better to choose a parameter name like this than a complex name that is unique to a specific cmdlet and hard to remember.</span></span>

- <span data-ttu-id="678da-138">Para meters zijn hoofdletter gevoelig in Windows Power shell, hoewel de shell standaard niet wordt bewaard.</span><span class="sxs-lookup"><span data-stu-id="678da-138">Parameters are case-insensitive in Windows PowerShell, although by default the shell preserves case.</span></span> <span data-ttu-id="678da-139">Hoofdletter gevoeligheid van de argumenten is afhankelijk van de werking van de cmdlet.</span><span class="sxs-lookup"><span data-stu-id="678da-139">Case-sensitivity of the arguments depends on the operation of the cmdlet.</span></span> <span data-ttu-id="678da-140">Argumenten worden door gegeven aan een para meter zoals opgegeven op de opdracht regel.</span><span class="sxs-lookup"><span data-stu-id="678da-140">Arguments are passed to a parameter as specified at the command line.</span></span>

- <span data-ttu-id="678da-141">Zie [cmdlet-para meters](./cmdlet-parameters.md)voor voor beelden van andere parameter declaraties.</span><span class="sxs-lookup"><span data-stu-id="678da-141">For examples of other parameter declarations, see [Cmdlet Parameters](./cmdlet-parameters.md).</span></span>

## <a name="declaring-parameters-as-positional-or-named"></a><span data-ttu-id="678da-142">Para meters declareren als positioneel of benoemd</span><span class="sxs-lookup"><span data-stu-id="678da-142">Declaring Parameters as Positional or Named</span></span>

<span data-ttu-id="678da-143">Voor een cmdlet moet elke para meter worden ingesteld als een positie of para meter met de naam.</span><span class="sxs-lookup"><span data-stu-id="678da-143">A cmdlet must set each parameter as either a positional or named parameter.</span></span> <span data-ttu-id="678da-144">Beide soorten para meters accepteren enkele argumenten, meerdere argumenten gescheiden door komma's en Booleaanse instellingen.</span><span class="sxs-lookup"><span data-stu-id="678da-144">Both kinds of parameters accept single arguments, multiple arguments separated by commas, and Boolean settings.</span></span> <span data-ttu-id="678da-145">Een Booleaanse para meter, ook wel een *Switch* genoemd, verwerkt alleen Boole-instellingen.</span><span class="sxs-lookup"><span data-stu-id="678da-145">A Boolean parameter, also called a *switch* , handles only Boolean settings.</span></span> <span data-ttu-id="678da-146">De switch wordt gebruikt om de aanwezigheid van de para meter te bepalen.</span><span class="sxs-lookup"><span data-stu-id="678da-146">The switch is used to determine the presence of the parameter.</span></span> <span data-ttu-id="678da-147">De aanbevolen standaard waarde is `false` .</span><span class="sxs-lookup"><span data-stu-id="678da-147">The recommended default is `false`.</span></span>

<span data-ttu-id="678da-148">De voor beeld- `Get-Proc` cmdlet definieert de `Name` para meter als een positionele para meter met positie</span><span class="sxs-lookup"><span data-stu-id="678da-148">The sample `Get-Proc` cmdlet defines the `Name` parameter as a positional parameter with position</span></span>
0. <span data-ttu-id="678da-149">Dit betekent dat het eerste argument dat de gebruiker invoert op de opdracht regel automatisch wordt ingevoegd voor deze para meter.</span><span class="sxs-lookup"><span data-stu-id="678da-149">This means that the first argument the user enters on the command line is automatically inserted for this parameter.</span></span> <span data-ttu-id="678da-150">Als u een benoemde para meter wilt definiëren waarvoor de gebruiker de parameter naam moet opgeven vanaf de opdracht regel, blijft u het `Position` sleutel woord uit de kenmerk declaratie.</span><span class="sxs-lookup"><span data-stu-id="678da-150">If you want to define a named parameter, for which the user must specify the parameter name from the command line, leave the `Position` keyword out of the attribute declaration.</span></span>

> [!NOTE]
> <span data-ttu-id="678da-151">Tenzij para meters moeten worden benoemd, wordt u aangeraden de meest gebruikte para meters positioneel te maken zodat gebruikers de parameter naam niet hoeven in te voeren.</span><span class="sxs-lookup"><span data-stu-id="678da-151">Unless parameters must be named, we recommend that you make the most-used parameters positional so that users will not have to type the parameter name.</span></span>

## <a name="declaring-parameters-as-mandatory-or-optional"></a><span data-ttu-id="678da-152">Para meters declareren als verplicht of optioneel</span><span class="sxs-lookup"><span data-stu-id="678da-152">Declaring Parameters as Mandatory or Optional</span></span>

<span data-ttu-id="678da-153">Een cmdlet moet elke para meter instellen als een optionele of een verplichte para meter.</span><span class="sxs-lookup"><span data-stu-id="678da-153">A cmdlet must set each parameter as either an optional or a mandatory parameter.</span></span> <span data-ttu-id="678da-154">In de voor beeld `Get-Proc` -cmdlet `Name` wordt de para meter gedefinieerd als optioneel omdat het `Mandatory` sleutel woord niet is ingesteld in de kenmerk declaratie.</span><span class="sxs-lookup"><span data-stu-id="678da-154">In the sample `Get-Proc` cmdlet, the `Name` parameter is defined as optional because the `Mandatory` keyword is not set in the attribute declaration.</span></span>

## <a name="supporting-parameter-validation"></a><span data-ttu-id="678da-155">Ondersteuning voor parameter validatie</span><span class="sxs-lookup"><span data-stu-id="678da-155">Supporting Parameter Validation</span></span>

<span data-ttu-id="678da-156">De voor beeld `Get-Proc` -cmdlet voegt een invoer validatie kenmerk, [System. Management. Automation. Validatenotnulloremptyattribute](/dotnet/api/System.Management.Automation.ValidateNotNullOrEmptyAttribute), toe aan de `Name` para meter om validatie mogelijk te maken dat de invoer niet `null` of leeg is.</span><span class="sxs-lookup"><span data-stu-id="678da-156">The sample `Get-Proc` cmdlet adds an input validation attribute, [System.Management.Automation.Validatenotnulloremptyattribute](/dotnet/api/System.Management.Automation.ValidateNotNullOrEmptyAttribute), to the `Name` parameter to enable validation that the input is neither `null` nor empty.</span></span> <span data-ttu-id="678da-157">Dit kenmerk is een van de beschik bare validatie kenmerken van Windows Power shell.</span><span class="sxs-lookup"><span data-stu-id="678da-157">This attribute is one of several validation attributes provided by Windows PowerShell.</span></span> <span data-ttu-id="678da-158">Zie [para meter invoer valideren](./validating-parameter-input.md)voor voor beelden van andere validatie kenmerken.</span><span class="sxs-lookup"><span data-stu-id="678da-158">For examples of other validation attributes, see [Validating Parameter Input](./validating-parameter-input.md).</span></span>

```
[Parameter(Position = 0)]
[ValidateNotNullOrEmpty]
public string[] Name
```

## <a name="overriding-an-input-processing-method"></a><span data-ttu-id="678da-159">Een invoer verwerkings methode overschrijven</span><span class="sxs-lookup"><span data-stu-id="678da-159">Overriding an Input Processing Method</span></span>

<span data-ttu-id="678da-160">Als uw cmdlet opdracht regel invoer verwerkt, moet deze de juiste invoer methoden onderdrukken.</span><span class="sxs-lookup"><span data-stu-id="678da-160">If your cmdlet is to handle command-line input, it must override the appropriate input processing methods.</span></span> <span data-ttu-id="678da-161">De basis methoden voor invoer verwerking zijn geïntroduceerd bij het [maken van uw eerste cmdlet](./creating-a-cmdlet-without-parameters.md).</span><span class="sxs-lookup"><span data-stu-id="678da-161">The basic input processing methods are introduced in [Creating Your First Cmdlet](./creating-a-cmdlet-without-parameters.md).</span></span>

<span data-ttu-id="678da-162">De `Get-Proc` cmdlet overschrijft de methode [System. Management. Automation. cmdlet. ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) om de `Name` parameter invoer van de gebruiker of een script af te handelen.</span><span class="sxs-lookup"><span data-stu-id="678da-162">The `Get-Proc` cmdlet overrides the [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) method to handle the `Name` parameter input provided by the user or a script.</span></span> <span data-ttu-id="678da-163">Met deze methode worden de processen voor elke aangevraagde proces naam en alle voor processen opgehaald als er geen naam is opgegeven.</span><span class="sxs-lookup"><span data-stu-id="678da-163">This method gets the processes for each requested process name, or all for processes if no name is provided.</span></span> <span data-ttu-id="678da-164">U ziet dat in [System. Management. Automation. cmdlet. ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord)de aanroep van [System. Management. Automation. cmdlet. WriteObject% 28System. object% 2CSystem. Boolean %29](/dotnet/api/system.management.automation.cmdlet.writeobject#System_Management_Automation_Cmdlet_WriteObject_System_Object_System_Boolean_) het uitvoer mechanisme is voor het verzenden van uitvoer objecten naar de pijp lijn.</span><span class="sxs-lookup"><span data-stu-id="678da-164">Notice that in [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord), the call to [System.Management.Automation.Cmdlet.WriteObject%28System.Object%2CSystem.Boolean%29](/dotnet/api/system.management.automation.cmdlet.writeobject#System_Management_Automation_Cmdlet_WriteObject_System_Object_System_Boolean_) is the output mechanism for sending output objects to the pipeline.</span></span> <span data-ttu-id="678da-165">De tweede para meter van deze aanroep, `enumerateCollection` , wordt ingesteld op `true` om de Windows Power shell-runtime op de hoogte te stellen van de uitvoer matrix van proces objecten en het één proces per keer naar de opdracht regel te schrijven.</span><span class="sxs-lookup"><span data-stu-id="678da-165">The second parameter of this call, `enumerateCollection`, is set to `true` to inform the Windows PowerShell runtime to enumerate the output array of process objects and write one process at a time to the command line.</span></span>

```csharp
protected override void ProcessRecord()
{
  // If no process names are passed to the cmdlet, get all processes.
  if (processNames == null)
  {
    // Write the processes to the pipeline making them available
    // to the next cmdlet. The second argument of this call tells
    // PowerShell to enumerate the array, and send one process at a
    // time to the pipeline.
    WriteObject(Process.GetProcesses(), true);
  }
  else
  {
    // If process names are passed to the cmdlet, get and write
    // the associated processes.
    foreach (string name in processNames)
    {
      WriteObject(Process.GetProcessesByName(name), true);
    }
  }
}
```

```vb
Protected Overrides Sub ProcessRecord()

    '/ If no process names are passed to the cmdlet, get all processes.
    If processNames Is Nothing Then
        Dim processes As Process()
        processes = Process.GetProcesses()
    End If

    '/ If process names are specified, write the processes to the
    '/ pipeline to display them or make them available to the next cmdlet.

    For Each name As String In processNames
        '/ The second parameter of this call tells PowerShell to enumerate the
        '/ array, and send one process at a time to the pipeline.
        WriteObject(Process.GetProcessesByName(name), True)
    Next

End Sub 'ProcessRecord
```

## <a name="code-sample"></a><span data-ttu-id="678da-166">Code voorbeeld</span><span class="sxs-lookup"><span data-stu-id="678da-166">Code Sample</span></span>

<span data-ttu-id="678da-167">Zie GetProcessSample02-voor [beeld](./getprocesssample02-sample.md)voor de volledige C#-voorbeeld code.</span><span class="sxs-lookup"><span data-stu-id="678da-167">For the complete C# sample code, see [GetProcessSample02 Sample](./getprocesssample02-sample.md).</span></span>

## <a name="defining-object-types-and-formatting"></a><span data-ttu-id="678da-168">Object typen en-opmaak definiëren</span><span class="sxs-lookup"><span data-stu-id="678da-168">Defining Object Types and Formatting</span></span>

<span data-ttu-id="678da-169">Windows Power shell geeft informatie tussen cmdlets door .NET Framework-objecten te gebruiken.</span><span class="sxs-lookup"><span data-stu-id="678da-169">Windows PowerShell passes information between cmdlets by using .NET Framework objects.</span></span> <span data-ttu-id="678da-170">Daarom moet een cmdlet een eigen type kunnen definiëren, of moet een cmdlet een bestaand type uitbreiden dat door een andere cmdlet wordt verschaft.</span><span class="sxs-lookup"><span data-stu-id="678da-170">Consequently, a cmdlet might need to define its own type, or a cmdlet might need to extend an existing type provided by another cmdlet.</span></span> <span data-ttu-id="678da-171">Zie [object typen en-opmaak uitbreiden](/previous-versions/ms714665(v=vs.85))voor meer informatie over het definiëren van nieuwe typen of het uitbreiden van bestaande typen.</span><span class="sxs-lookup"><span data-stu-id="678da-171">For more information about defining new types or extending existing types, see [Extending Object Types and Formatting](/previous-versions/ms714665(v=vs.85)).</span></span>

## <a name="building-the-cmdlet"></a><span data-ttu-id="678da-172">De cmdlet bouwen</span><span class="sxs-lookup"><span data-stu-id="678da-172">Building the Cmdlet</span></span>

<span data-ttu-id="678da-173">Nadat u een cmdlet hebt geïmplementeerd, moet u deze met Windows Power shell registreren met behulp van een Windows Power shell-module.</span><span class="sxs-lookup"><span data-stu-id="678da-173">After you implement a cmdlet, you must register it with Windows PowerShell by using a Windows PowerShell snap-in.</span></span> <span data-ttu-id="678da-174">Zie [cmdlets, providers en hosttoepassingen registreren](/previous-versions/ms714644(v=vs.85))voor meer informatie over het registreren van cmdlets.</span><span class="sxs-lookup"><span data-stu-id="678da-174">For more information about registering cmdlets, see [How to Register Cmdlets, Providers, and Host Applications](/previous-versions/ms714644(v=vs.85)).</span></span>

## <a name="testing-the-cmdlet"></a><span data-ttu-id="678da-175">De cmdlet testen</span><span class="sxs-lookup"><span data-stu-id="678da-175">Testing the Cmdlet</span></span>

<span data-ttu-id="678da-176">Als uw cmdlet is geregistreerd bij Windows Power shell, kunt u deze testen door deze uit te voeren op de opdracht regel.</span><span class="sxs-lookup"><span data-stu-id="678da-176">When your cmdlet is registered with Windows PowerShell, you can test it by running it on the command line.</span></span> <span data-ttu-id="678da-177">Hier volgen twee manieren om de code voor de voor beeld-cmdlet te testen.</span><span class="sxs-lookup"><span data-stu-id="678da-177">Here are two ways to test the code for the sample cmdlet.</span></span> <span data-ttu-id="678da-178">Zie aan de slag [met Windows Power shell](/powershell/scripting/getting-started/getting-started-with-windows-powershell)voor meer informatie over het gebruik van cmdlets vanaf de opdracht regel.</span><span class="sxs-lookup"><span data-stu-id="678da-178">For more information about using cmdlets from the command line, see [Getting Started with Windows PowerShell](/powershell/scripting/getting-started/getting-started-with-windows-powershell).</span></span>

- <span data-ttu-id="678da-179">Gebruik de volgende opdracht bij de Windows Power shell-prompt om het Internet Explorer-proces met de naam ' IEXPLORE ' weer te geven.</span><span class="sxs-lookup"><span data-stu-id="678da-179">At the Windows PowerShell prompt, use the following command to list the Internet Explorer process, which is named "IEXPLORE."</span></span>

  ```powershell
  get-proc -name iexplore
  ```

  <span data-ttu-id="678da-180">De volgende uitvoer wordt weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="678da-180">The following output appears.</span></span>

  ```Output
  Handles  NPM(K)  PM(K)   WS(K)  VS(M)  CPU(s)   Id   ProcessName
  -------  ------  -----   -----  -----   ------ --   -----------
      354      11  10036   18992    85   0.67   3284   iexplore
  ```

- <span data-ttu-id="678da-181">Gebruik de volgende opdracht om de Internet Explorer-, Outlook-en Notepad-processen met de naam ' IEXPLORE, ' OUTLOOK ' en ' NOTEPAD ' te vermelden.</span><span class="sxs-lookup"><span data-stu-id="678da-181">To list the Internet Explorer, Outlook, and Notepad processes named "IEXPLORE," "OUTLOOK," and "NOTEPAD," use the following command.</span></span> <span data-ttu-id="678da-182">Als er meerdere processen zijn, worden deze weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="678da-182">If there are multiple processes, all of them are displayed.</span></span>

  ```powershell
  get-proc -name iexplore, outlook, notepad
  ```

  <span data-ttu-id="678da-183">De volgende uitvoer wordt weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="678da-183">The following output appears.</span></span>

  ```
  Handles  NPM(K)  PM(K)   WS(K)  VS(M)  CPU(s)   Id   ProcessName
  -------  ------  -----   -----  -----  ------   --   -----------
      732      21  24696    5000    138   2.25  2288   iexplore
      715      19  20556   14116    136   1.78  3860   iexplore
     3917      62  74096   58112    468 191.56  1848   OUTLOOK
       39       2   1024    3280     30   0.09  1444   notepad
       39       2   1024     356     30   0.08  3396   notepad
  ```

## <a name="see-also"></a><span data-ttu-id="678da-184">Zie ook</span><span class="sxs-lookup"><span data-stu-id="678da-184">See Also</span></span>

[<span data-ttu-id="678da-185">Parameters toevoegen die pijplijninvoer verwerken</span><span class="sxs-lookup"><span data-stu-id="678da-185">Adding Parameters that Process Pipeline Input</span></span>](./adding-parameters-that-process-pipeline-input.md)

[<span data-ttu-id="678da-186">Uw eerste cmdlet maken</span><span class="sxs-lookup"><span data-stu-id="678da-186">Creating Your First Cmdlet</span></span>](./creating-a-cmdlet-without-parameters.md)

<span data-ttu-id="678da-187">[Object typen en-opmaak uitbreiden](/previous-versions/ms714665(v=vs.85))</span><span class="sxs-lookup"><span data-stu-id="678da-187">[Extending Object Types and Formatting](/previous-versions/ms714665(v=vs.85))</span></span>

<span data-ttu-id="678da-188">[Cmdlets, providers en hosttoepassingen registreren](/previous-versions/ms714644(v=vs.85))</span><span class="sxs-lookup"><span data-stu-id="678da-188">[How to Register Cmdlets, Providers, and Host Applications](/previous-versions/ms714644(v=vs.85))</span></span>

[<span data-ttu-id="678da-189">Naslaginformatie over Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="678da-189">Windows PowerShell Reference</span></span>](../windows-powershell-reference.md)

[<span data-ttu-id="678da-190">Cmdlet-voorbeelden</span><span class="sxs-lookup"><span data-stu-id="678da-190">Cmdlet Samples</span></span>](./cmdlet-samples.md)
