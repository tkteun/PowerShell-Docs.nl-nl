---
title: Parameters die opdrachtregel verwerken toe te voegen | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- cmdlets [PowerShell Programmer's Guide], parameters
- Get-Proc cmdlet [PowerShell Programmer's Guide]
- cmdlets [PowerShell Programmer's Guide], command line input
- command line input [PowerShell Programmer's Guide]
- parameters [PowerShell Programmer's Guide]
- cmdlets [PowerShell Programmer's Guide], creating
ms.assetid: da0b32f8-7b51-440e-a061-3177b5759e0e
caps.latest.revision: 9
ms.openlocfilehash: fb113086ce89e4becff9bcaf3232905fde2bf610
ms.sourcegitcommit: caac7d098a448232304c9d6728e7340ec7517a71
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 03/16/2019
ms.locfileid: "58055917"
---
# <a name="adding-parameters-that-process-command-line-input"></a><span data-ttu-id="5fd94-102">Parameters toevoegen die opdrachtregelinvoer verwerken</span><span class="sxs-lookup"><span data-stu-id="5fd94-102">Adding Parameters That Process Command-Line Input</span></span>

<span data-ttu-id="5fd94-103">Een bron van de invoer voor een cmdlet is vanaf de opdrachtregel.</span><span class="sxs-lookup"><span data-stu-id="5fd94-103">One source of input for a cmdlet is the command line.</span></span> <span data-ttu-id="5fd94-104">In dit onderwerp wordt beschreven hoe u om toe te voegen een parameter voor de **Get-Proc** cmdlet (die wordt beschreven [het maken van uw eerste Cmdlet](./creating-a-cmdlet-without-parameters.md)) zodat de cmdlet kan de invoer van de lokale computer op basis van expliciete verwerken objecten die is doorgegeven aan de cmdlet.</span><span class="sxs-lookup"><span data-stu-id="5fd94-104">This topic describes how to add a parameter to the **Get-Proc** cmdlet (which is described in [Creating Your First Cmdlet](./creating-a-cmdlet-without-parameters.md)) so that the cmdlet can process input from the local computer based on explicit objects passed to the cmdlet.</span></span> <span data-ttu-id="5fd94-105">De **Get-Proc** cmdlet beschreven hier haalt processen op basis van hun namen en vervolgens geeft informatie weer over de processen achter de opdrachtprompt.</span><span class="sxs-lookup"><span data-stu-id="5fd94-105">The **Get-Proc** cmdlet described here retrieves processes based on their names, and then displays information about the processes at a command prompt.</span></span>

<span data-ttu-id="5fd94-106">De volgende secties zijn in dit onderwerp:</span><span class="sxs-lookup"><span data-stu-id="5fd94-106">The following sections are in this topic:</span></span>

- [<span data-ttu-id="5fd94-107">De Cmdlet-klasse definiëren</span><span class="sxs-lookup"><span data-stu-id="5fd94-107">Defining the Cmdlet Class</span></span>](#Defining-the-Cmdlet-Class)

- [<span data-ttu-id="5fd94-108">Parameters declareren</span><span class="sxs-lookup"><span data-stu-id="5fd94-108">Declaring Parameters</span></span>](#Declaring-Parameters)

- [<span data-ttu-id="5fd94-109">Validatie van de Parameter ondersteunen</span><span class="sxs-lookup"><span data-stu-id="5fd94-109">Supporting Parameter Validation</span></span>](#Supporting-Parameter-Validation)

- [<span data-ttu-id="5fd94-110">Invoer verwerken methode te overschrijven</span><span class="sxs-lookup"><span data-stu-id="5fd94-110">Overriding an Input Processing Method</span></span>](#Overriding-an-Input-Processing-Method)

- [<span data-ttu-id="5fd94-111">Voorbeeld van code</span><span class="sxs-lookup"><span data-stu-id="5fd94-111">Code Sample</span></span>](#Code-Sample)

- [<span data-ttu-id="5fd94-112">Objecttype definiëren en opmaak</span><span class="sxs-lookup"><span data-stu-id="5fd94-112">Defining Object Types and Formatting</span></span>](#Defining-Object-Types-and-Formatting)

- [<span data-ttu-id="5fd94-113">Het bouwen van de Cmdlet</span><span class="sxs-lookup"><span data-stu-id="5fd94-113">Building the Cmdlet</span></span>](#Building-the-Cmdlet)

- [<span data-ttu-id="5fd94-114">Testen van de Cmdlet</span><span class="sxs-lookup"><span data-stu-id="5fd94-114">Testing the Cmdlet</span></span>](#Testing-the-Cmdlet)

## <a name="defining-the-cmdlet-class"></a><span data-ttu-id="5fd94-115">De Cmdlet-klasse definiëren</span><span class="sxs-lookup"><span data-stu-id="5fd94-115">Defining the Cmdlet Class</span></span>

<span data-ttu-id="5fd94-116">De eerste stap bij het maken van de cmdlet is cmdlet naamgeving en de declaratie van het .NET Framework-klasse die de cmdlet.</span><span class="sxs-lookup"><span data-stu-id="5fd94-116">The first step in cmdlet creation is cmdlet naming and the declaration of the .NET Framework class that implements the cmdlet.</span></span> <span data-ttu-id="5fd94-117">Dit smdlet haalt procesinformatie, dus de hier gekozen naam van de term 'Ophalen'.</span><span class="sxs-lookup"><span data-stu-id="5fd94-117">This cmdlet retrieves process information, so the verb name chosen here is "Get."</span></span> <span data-ttu-id="5fd94-118">(Bijna elk soort cmdlet waarmee het ophalen van gegevens kan opdrachtregel invoer verwerken). Zie voor meer informatie over goedgekeurde werkwoorden [namen van de term cmdlets](./approved-verbs-for-windows-powershell-commands.md).</span><span class="sxs-lookup"><span data-stu-id="5fd94-118">(Almost any sort of cmdlet that is capable of retrieving information can process command-line input.) For more information about approved cmdlet verbs, see [Cmdlet Verb Names](./approved-verbs-for-windows-powershell-commands.md).</span></span>

<span data-ttu-id="5fd94-119">Hier is de klassendeclaratie voor de **Get-Proc** cmdlet.</span><span class="sxs-lookup"><span data-stu-id="5fd94-119">Here's the class declaration for the **Get-Proc** cmdlet.</span></span> <span data-ttu-id="5fd94-120">Meer informatie over deze definitie vindt u in [het maken van uw eerste Cmdlet](./creating-a-cmdlet-without-parameters.md).</span><span class="sxs-lookup"><span data-stu-id="5fd94-120">Details about this definition are provided in [Creating Your First Cmdlet](./creating-a-cmdlet-without-parameters.md).</span></span>

```csharp
[Cmdlet(VerbsCommon.Get, "proc")]
public class GetProcCommand: Cmdlet
```

```vb
<Cmdlet(VerbsCommon.Get, "Proc")> _
Public Class GetProcCommand
    Inherits Cmdlet
```

## <a name="declaring-parameters"></a><span data-ttu-id="5fd94-121">Parameters declareren</span><span class="sxs-lookup"><span data-stu-id="5fd94-121">Declaring Parameters</span></span>

<span data-ttu-id="5fd94-122">Cmdlet-parameter kan de gebruiker voor invoer naar de cmdlet.</span><span class="sxs-lookup"><span data-stu-id="5fd94-122">A cmdlet parameter enables the user to provide input to the cmdlet.</span></span> <span data-ttu-id="5fd94-123">In het volgende voorbeeld **Get-Proc** en `Get-Member` zijn de namen van de pipeline-cmdlets en `MemberType` is een parameter voor de `Get-Member` cmdlet.</span><span class="sxs-lookup"><span data-stu-id="5fd94-123">In the following example, **Get-Proc** and `Get-Member` are the names of pipelined cmdlets, and `MemberType` is a parameter for the `Get-Member` cmdlet.</span></span> <span data-ttu-id="5fd94-124">De parameter is het argument 'eigenschap'.</span><span class="sxs-lookup"><span data-stu-id="5fd94-124">The parameter has the argument "property."</span></span>

<span data-ttu-id="5fd94-125">**PS > get-proc; `get-member` membertype - eigenschap**</span><span class="sxs-lookup"><span data-stu-id="5fd94-125">**PS> get-proc ; `get-member` -membertype property**</span></span>

<span data-ttu-id="5fd94-126">Voor het declareren van parameters voor een cmdlet, moet u eerst de eigenschappen die staan voor de parameters definiëren.</span><span class="sxs-lookup"><span data-stu-id="5fd94-126">To declare parameters for a cmdlet, you must first define the properties that represent the parameters.</span></span> <span data-ttu-id="5fd94-127">In de **Get-Proc** cmdlet, de enige parameter is `Name`, die in dit geval vertegenwoordigt de naam van de .NET Framework-proces dat moet worden opgehaald.</span><span class="sxs-lookup"><span data-stu-id="5fd94-127">In the **Get-Proc** cmdlet, the only parameter is `Name`, which in this case represents the name of the .NET Framework process object to retrieve.</span></span> <span data-ttu-id="5fd94-128">Daarom definieert de cmdlet-klasse een eigenschap van het typetekenreeks om te accepteren van een matrix van namen.</span><span class="sxs-lookup"><span data-stu-id="5fd94-128">Therefore, the cmdlet class defines a property of type string to accept an array of names.</span></span>

<span data-ttu-id="5fd94-129">Hier is de parameterdeclaratie voor de `Name` parameter van de **Get-Proc** cmdlet.</span><span class="sxs-lookup"><span data-stu-id="5fd94-129">Here's the parameter declaration for the `Name` parameter of the **Get-Proc** cmdlet.</span></span>

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

<span data-ttu-id="5fd94-130">Om te informeren over de Windows PowerShell-runtime die deze eigenschap is de `Name` parameter, een [System.Management.Automation.Parameterattribute](/dotnet/api/System.Management.Automation.ParameterAttribute) kenmerk wordt toegevoegd aan de eigenschapsdefinitie van de.</span><span class="sxs-lookup"><span data-stu-id="5fd94-130">To inform the Windows PowerShell runtime that this property is the `Name` parameter, a [System.Management.Automation.Parameterattribute](/dotnet/api/System.Management.Automation.ParameterAttribute) attribute is added to the property definition.</span></span> <span data-ttu-id="5fd94-131">De eenvoudige syntaxis voor het declareren van dit kenmerk is `[Parameter()]`.</span><span class="sxs-lookup"><span data-stu-id="5fd94-131">The basic syntax for declaring this attribute is `[Parameter()]`.</span></span>

> [!NOTE]
> <span data-ttu-id="5fd94-132">Een parameter moet expliciet gemarkeerd als openbaar.</span><span class="sxs-lookup"><span data-stu-id="5fd94-132">A parameter must be explicitly marked as public.</span></span> <span data-ttu-id="5fd94-133">De parameters die niet zijn gemarkeerd als openbare standaard naar interne en niet worden gevonden door de Windows PowerShell-runtime.</span><span class="sxs-lookup"><span data-stu-id="5fd94-133">Parameters that are not marked as public default to internal and are not found by the Windows PowerShell runtime.</span></span>

<span data-ttu-id="5fd94-134">Deze cmdlet wordt een matrix van tekenreeksen voor de `Name` parameter.</span><span class="sxs-lookup"><span data-stu-id="5fd94-134">This cmdlet uses an array of strings for the `Name` parameter.</span></span> <span data-ttu-id="5fd94-135">Indien mogelijk moet de cmdlet ook een parameter definiëren als een matrix, omdat Hiermee wordt de cmdlet om te accepteren van meer dan één item.</span><span class="sxs-lookup"><span data-stu-id="5fd94-135">If possible, your cmdlet should also define a parameter as an array, because this allows the cmdlet to accept more than one item.</span></span>

#### <a name="things-to-remember-about-parameter-definitions"></a><span data-ttu-id="5fd94-136">Om te onthouden over parameterdefinities</span><span class="sxs-lookup"><span data-stu-id="5fd94-136">Things to Remember About Parameter Definitions</span></span>

- <span data-ttu-id="5fd94-137">Vooraf gedefinieerde Windows PowerShell parameter kolomnamen en gegevenstypen moeten opnieuw worden gebruikt zo veel mogelijk om ervoor te zorgen dat uw cmdlet compatibel met Windows PowerShell-cmdlets is.</span><span class="sxs-lookup"><span data-stu-id="5fd94-137">Predefined Windows PowerShell parameter names and data types should be reused as much as possible to ensure that your cmdlet is compatible with Windows PowerShell cmdlets.</span></span> <span data-ttu-id="5fd94-138">Bijvoorbeeld, als alle cmdlets gebruiken de vooraf gedefinieerde `Id` unieke parameternaam in voor een resource, de gebruiker wordt eenvoudig te begrijpen van de betekenis van de parameter, ongeacht welke cmdlet die ze gebruiken.</span><span class="sxs-lookup"><span data-stu-id="5fd94-138">For example, if all cmdlets use the predefined `Id` parameter name to identify a resource, user will easily understand the meaning of the parameter, regardless of what cmdlet they are using.</span></span> <span data-ttu-id="5fd94-139">Parameternamen worden in feite, als volgt dezelfde regels als die worden gebruikt voor de namen van variabelen in de common language runtime (CLR).</span><span class="sxs-lookup"><span data-stu-id="5fd94-139">Basically, parameter names follow the same rules as those used for variable names in the common language runtime (CLR).</span></span> <span data-ttu-id="5fd94-140">Zie voor meer informatie over de naamgeving van parameter [namen van de Cmdlet-parameters](https://msdn.microsoft.com/en-us/c4500737-0a05-4d01-911b-394424c65bfb).</span><span class="sxs-lookup"><span data-stu-id="5fd94-140">For more information about parameter naming, see [Cmdlet Parameter Names](https://msdn.microsoft.com/en-us/c4500737-0a05-4d01-911b-394424c65bfb).</span></span>

- <span data-ttu-id="5fd94-141">Windows PowerShell behoudt een aantal namen van parameters om een consistente gebruikerservaring te bieden.</span><span class="sxs-lookup"><span data-stu-id="5fd94-141">Windows PowerShell reserves a few parameter names to provide a consistent user experience.</span></span> <span data-ttu-id="5fd94-142">Gebruik niet de namen van deze parameters: `WhatIf`, `Confirm`, `Verbose`, `Debug`, `Warn`, `ErrorAction`, `ErrorVariable`, `OutVariable`, en `OutBuffer`.</span><span class="sxs-lookup"><span data-stu-id="5fd94-142">Do not use these parameter names: `WhatIf`, `Confirm`, `Verbose`, `Debug`, `Warn`, `ErrorAction`, `ErrorVariable`, `OutVariable`, and `OutBuffer`.</span></span> <span data-ttu-id="5fd94-143">Bovendien de volgende aliassen voor de namen van deze parameters zijn gereserveerd: `vb`, `db`, `ea`, `ev`, `ov`, en `ob`.</span><span class="sxs-lookup"><span data-stu-id="5fd94-143">Additionally, the following aliases for these parameter names are reserved: `vb`, `db`, `ea`, `ev`, `ov`, and `ob`.</span></span>

- <span data-ttu-id="5fd94-144">`Name` is een eenvoudige en algemene parameternamen, aanbevolen voor gebruik in uw cmdlets.</span><span class="sxs-lookup"><span data-stu-id="5fd94-144">`Name` is a simple and common parameter name, recommended for use in your cmdlets.</span></span> <span data-ttu-id="5fd94-145">Is het beter om te kiezen van een parameternaam als volgt dan de naam van een complexe die uniek is voor een bepaalde cmdlet en moeilijk te onthouden.</span><span class="sxs-lookup"><span data-stu-id="5fd94-145">It is better to choose a parameter name like this than a complex name that is unique to a specific cmdlet and hard to remember.</span></span>

- <span data-ttu-id="5fd94-146">Parameters zijn niet hoofdlettergevoelig in Windows PowerShell, hoewel standaard de shell hoofdlettergebruik behoudt.</span><span class="sxs-lookup"><span data-stu-id="5fd94-146">Parameters are case-insensitive in Windows PowerShell, although by default the shell preserves case.</span></span> <span data-ttu-id="5fd94-147">Hoofdlettergevoeligheid van de argumenten is afhankelijk van de werking van de cmdlet.</span><span class="sxs-lookup"><span data-stu-id="5fd94-147">Case-sensitivity of the arguments depends on the operation of the cmdlet.</span></span> <span data-ttu-id="5fd94-148">Argumenten worden doorgegeven aan een parameter zoals opgegeven op de opdrachtregel.</span><span class="sxs-lookup"><span data-stu-id="5fd94-148">Arguments are passed to a parameter as specified at the command line.</span></span>

- <span data-ttu-id="5fd94-149">Zie voor meer voorbeelden van andere parameterdeclaraties [Cmdlet-Parameters](./cmdlet-parameters.md).</span><span class="sxs-lookup"><span data-stu-id="5fd94-149">For examples of other parameter declarations, see [Cmdlet Parameters](./cmdlet-parameters.md).</span></span>

## <a name="declaring-parameters-as-positional-or-named"></a><span data-ttu-id="5fd94-150">Parameters declareren als positionele of benoemde</span><span class="sxs-lookup"><span data-stu-id="5fd94-150">Declaring Parameters as Positional or Named</span></span>

<span data-ttu-id="5fd94-151">Een cmdlet moet elke parameter worden ingesteld als een parameter positionele of met de naam.</span><span class="sxs-lookup"><span data-stu-id="5fd94-151">A cmdlet must set each parameter as either a positional or named parameter.</span></span> <span data-ttu-id="5fd94-152">Beide soorten parameters accepteren één argumenten, meerdere argumenten gescheiden door komma's en instellingen voor Booleaanse.</span><span class="sxs-lookup"><span data-stu-id="5fd94-152">Both kinds of parameters accept single arguments, multiple arguments separated by commas, and Boolean settings.</span></span> <span data-ttu-id="5fd94-153">Een Boole-parameter, ook wel een *overschakelen*, alleen Booleaanse instellingen worden verwerkt.</span><span class="sxs-lookup"><span data-stu-id="5fd94-153">A Boolean parameter, also called a *switch*, handles only Boolean settings.</span></span> <span data-ttu-id="5fd94-154">De switch wordt gebruikt om de aanwezigheid van de parameter.</span><span class="sxs-lookup"><span data-stu-id="5fd94-154">The switch is used to determine the presence of the parameter.</span></span> <span data-ttu-id="5fd94-155">De aanbevolen standaardwaarde is `false`.</span><span class="sxs-lookup"><span data-stu-id="5fd94-155">The recommended default is `false`.</span></span>

<span data-ttu-id="5fd94-156">Het voorbeeld **Get-Proc** cmdlet definieert de `Name` parameter als een positionele parameter met de positie 0.</span><span class="sxs-lookup"><span data-stu-id="5fd94-156">The sample **Get-Proc** cmdlet defines the `Name` parameter as a positional parameter with position 0.</span></span> <span data-ttu-id="5fd94-157">Dit betekent dat het eerste argument dat de gebruiker op de opdrachtregel invoert automatisch voor deze parameter is geplaatst.</span><span class="sxs-lookup"><span data-stu-id="5fd94-157">This means that the first argument the user enters on the command line is automatically inserted for this parameter.</span></span> <span data-ttu-id="5fd94-158">Als u wilt voor het definiëren van een benoemde parameter, voor de gebruiker moet opgeven de parameternaam vanaf de opdrachtregel, laat u de `Position` sleutelwoord buiten de kenmerkdeclaratie.</span><span class="sxs-lookup"><span data-stu-id="5fd94-158">If you want to define a named parameter, for which the user must specify the parameter name from the command line, leave the `Position` keyword out of the attribute declaration.</span></span>

> [!NOTE]
> <span data-ttu-id="5fd94-159">Als parameters moeten de naam, wordt u aangeraden dat u de meest gebruikte parameters positionele zodat gebruikers niet hebben de naam van de parameter.</span><span class="sxs-lookup"><span data-stu-id="5fd94-159">Unless parameters must be named, we recommend that you make the most-used parameters positional so that users will not have to type the parameter name.</span></span>

## <a name="declaring-parameters-as-mandatory-or-optional"></a><span data-ttu-id="5fd94-160">Parameters declareren als verplicht of optioneel</span><span class="sxs-lookup"><span data-stu-id="5fd94-160">Declaring Parameters as Mandatory or Optional</span></span>

<span data-ttu-id="5fd94-161">Een cmdlet, moet elke parameter ingesteld als een optionele of een verplichte parameter.</span><span class="sxs-lookup"><span data-stu-id="5fd94-161">A cmdlet must set each parameter as either an optional or a mandatory parameter.</span></span> <span data-ttu-id="5fd94-162">In het voorbeeld **Get-Proc** cmdlet, de `Name` parameter wordt gedefinieerd als optioneel, omdat de `Mandatory` sleutelwoord is niet ingesteld in de kenmerkdeclaratie.</span><span class="sxs-lookup"><span data-stu-id="5fd94-162">In the sample **Get-Proc** cmdlet, the `Name` parameter is defined as optional because the `Mandatory` keyword is not set in the attribute declaration.</span></span>

## <a name="supporting-parameter-validation"></a><span data-ttu-id="5fd94-163">Validatie van de Parameter ondersteunen</span><span class="sxs-lookup"><span data-stu-id="5fd94-163">Supporting Parameter Validation</span></span>

<span data-ttu-id="5fd94-164">Het voorbeeld **Get-Proc** cmdlet wordt toegevoegd een kenmerk Invoervalidatie [System.Management.Automation.Validatenotnulloremptyattribute](/dotnet/api/System.Management.Automation.ValidateNotNullOrEmptyAttribute), naar de `Name` parameter validatie inschakelen die de de invoer is geen van beide `null` of leeg zijn.</span><span class="sxs-lookup"><span data-stu-id="5fd94-164">The sample **Get-Proc** cmdlet adds an input validation attribute, [System.Management.Automation.Validatenotnulloremptyattribute](/dotnet/api/System.Management.Automation.ValidateNotNullOrEmptyAttribute), to the `Name` parameter to enable validation that the input is neither `null` nor empty.</span></span> <span data-ttu-id="5fd94-165">Dit kenmerk is een van verschillende validatie kenmerken die worden geleverd door Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="5fd94-165">This attribute is one of several validation attributes provided by Windows PowerShell.</span></span> <span data-ttu-id="5fd94-166">Zie voor meer voorbeelden van andere kenmerken validatie [Parameter invoer valideren](./validating-parameter-input.md).</span><span class="sxs-lookup"><span data-stu-id="5fd94-166">For examples of other validation attributes, see [Validating Parameter Input](./validating-parameter-input.md).</span></span>

```
[Parameter(Position = 0)]
[ValidateNotNullOrEmpty]
public string[] Name
```

## <a name="overriding-an-input-processing-method"></a><span data-ttu-id="5fd94-167">Invoer verwerken methode te overschrijven</span><span class="sxs-lookup"><span data-stu-id="5fd94-167">Overriding an Input Processing Method</span></span>

<span data-ttu-id="5fd94-168">Als de cmdlet voor het afhandelen van de invoer van de opdrachtregel, moet deze de juiste invoer verwerkingsmethoden overschrijven.</span><span class="sxs-lookup"><span data-stu-id="5fd94-168">If your cmdlet is to handle command-line input, it must override the appropriate input processing methods.</span></span> <span data-ttu-id="5fd94-169">De van basic input-verwerkingsmethoden zijn geïntroduceerd in [het maken van uw eerste Cmdlet](./creating-a-cmdlet-without-parameters.md).</span><span class="sxs-lookup"><span data-stu-id="5fd94-169">The basic input processing methods are introduced in [Creating Your First Cmdlet](./creating-a-cmdlet-without-parameters.md).</span></span>

<span data-ttu-id="5fd94-170">De **Get-Proc** cmdlet vervangt de [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) methode voor het afhandelen van de `Name` parameter is niets opgegeven door de gebruiker of een script.</span><span class="sxs-lookup"><span data-stu-id="5fd94-170">The **Get-Proc** cmdlet overrides the [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) method to handle the `Name` parameter input provided by the user or a script.</span></span> <span data-ttu-id="5fd94-171">Deze methode haalt de processen voor elke gewenste procesnaam of alle processen als er geen naam is opgegeven.</span><span class="sxs-lookup"><span data-stu-id="5fd94-171">This method gets the processes for each requested process name, or all for processes if no name is provided.</span></span> <span data-ttu-id="5fd94-172">U ziet dat in [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord), de aanroep van [System.Management.Automation.Cmdlet.WriteObject%28System.Object%2CSystem.Boolean%29](/dotnet/api/system.management.automation.cmdlet.writeobject?view=powershellsdk-1.1.0#System_Management_Automation_Cmdlet_WriteObject_System_Object_System_Boolean_) is de uitvoer mechanisme voor het verzenden van uitvoer objecten aan de pijplijn.</span><span class="sxs-lookup"><span data-stu-id="5fd94-172">Notice that in [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord), the call to [System.Management.Automation.Cmdlet.WriteObject%28System.Object%2CSystem.Boolean%29](/dotnet/api/system.management.automation.cmdlet.writeobject?view=powershellsdk-1.1.0#System_Management_Automation_Cmdlet_WriteObject_System_Object_System_Boolean_) is the output mechanism for sending output objects to the pipeline.</span></span> <span data-ttu-id="5fd94-173">De tweede parameter van deze aanroep `enumerateCollection`, is ingesteld op `true` om te informeren over de Windows PowerShell-runtime voor het inventariseren van de uitvoermatrix met proces-objecten en een proces op een tijdstip schrijven naar de opdrachtregel.</span><span class="sxs-lookup"><span data-stu-id="5fd94-173">The second parameter of this call, `enumerateCollection`, is set to `true` to inform the Windows PowerShell runtime to enumerate the output array of process objects and write one process at a time to the command line.</span></span>

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

## <a name="code-sample"></a><span data-ttu-id="5fd94-174">Voorbeeld van code</span><span class="sxs-lookup"><span data-stu-id="5fd94-174">Code Sample</span></span>

<span data-ttu-id="5fd94-175">Voor de volledige C# voorbeeldcode, Zie [GetProcessSample02 voorbeeld](./getprocesssample02-sample.md).</span><span class="sxs-lookup"><span data-stu-id="5fd94-175">For the complete C# sample code, see [GetProcessSample02 Sample](./getprocesssample02-sample.md).</span></span>

## <a name="defining-object-types-and-formatting"></a><span data-ttu-id="5fd94-176">Objecttype definiëren en opmaak</span><span class="sxs-lookup"><span data-stu-id="5fd94-176">Defining Object Types and Formatting</span></span>

<span data-ttu-id="5fd94-177">Windows PowerShell wordt informatie doorgegeven tussen cmdlets met behulp van .NET Framework-objecten.</span><span class="sxs-lookup"><span data-stu-id="5fd94-177">Windows PowerShell passes information between cmdlets by using .NET Framework objects.</span></span> <span data-ttu-id="5fd94-178">Als gevolg daarvan kan een cmdlet mogelijk voor het definiëren van een eigen type of een cmdlet uit te breiden van een bestaand type geleverd door een andere cmdlet moet mogelijk.</span><span class="sxs-lookup"><span data-stu-id="5fd94-178">Consequently, a cmdlet might need to define its own type, or a cmdlet might need to extend an existing type provided by another cmdlet.</span></span> <span data-ttu-id="5fd94-179">Zie voor meer informatie over het definiëren van nieuwe typen of uitbreiden van bestaande typen [objecttypen uitbreiden en opmaak](http://msdn.microsoft.com/en-us/da976d91-a3d6-44e8-affa-466b1e2bd351).</span><span class="sxs-lookup"><span data-stu-id="5fd94-179">For more information about defining new types or extending existing types, see [Extending Object Types and Formatting](http://msdn.microsoft.com/en-us/da976d91-a3d6-44e8-affa-466b1e2bd351).</span></span>

## <a name="building-the-cmdlet"></a><span data-ttu-id="5fd94-180">Het bouwen van de Cmdlet</span><span class="sxs-lookup"><span data-stu-id="5fd94-180">Building the Cmdlet</span></span>

<span data-ttu-id="5fd94-181">Nadat u een cmdlet kunt implementeren, moet u het registreren met Windows PowerShell met behulp van een Windows PowerShell-module.</span><span class="sxs-lookup"><span data-stu-id="5fd94-181">After you implement a cmdlet, you must register it with Windows PowerShell by using a Windows PowerShell snap-in.</span></span> <span data-ttu-id="5fd94-182">Zie voor meer informatie over het registreren van cmdlets [hoe u Cmdlets registreren, Providers en hosting van toepassingen](http://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c).</span><span class="sxs-lookup"><span data-stu-id="5fd94-182">For more information about registering cmdlets, see [How to Register Cmdlets, Providers, and Host Applications](http://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c).</span></span>

## <a name="testing-the-cmdlet"></a><span data-ttu-id="5fd94-183">Testen van de Cmdlet</span><span class="sxs-lookup"><span data-stu-id="5fd94-183">Testing the Cmdlet</span></span>

<span data-ttu-id="5fd94-184">Als de cmdlet is geregistreerd met Windows PowerShell, kunt u deze testen door te voeren op de opdrachtregel.</span><span class="sxs-lookup"><span data-stu-id="5fd94-184">When your cmdlet is registered with Windows PowerShell, you can test it by running it on the command line.</span></span> <span data-ttu-id="5fd94-185">Hier volgen twee manieren om te testen hoe de code voor de voorbeeld-cmdlet.</span><span class="sxs-lookup"><span data-stu-id="5fd94-185">Here are two ways to test the code for the sample cmdlet.</span></span> <span data-ttu-id="5fd94-186">Zie voor meer informatie over het gebruik van cmdlets vanaf de opdrachtregel [aan de slag met Windows PowerShell](/powershell/scripting/getting-started/getting-started-with-windows-powershell).</span><span class="sxs-lookup"><span data-stu-id="5fd94-186">For more information about using cmdlets from the command line, see [Getting Started with Windows PowerShell](/powershell/scripting/getting-started/getting-started-with-windows-powershell).</span></span>

- <span data-ttu-id="5fd94-187">Gebruik bij de Windows PowerShell-prompt de volgende opdracht om het proces van Internet Explorer, met de naam "IEXPLORE."</span><span class="sxs-lookup"><span data-stu-id="5fd94-187">At the Windows PowerShell prompt, use the following command to list the Internet Explorer process, which is named "IEXPLORE."</span></span>

    ```powershell
    PS> get-proc -name iexplore
    ```

<span data-ttu-id="5fd94-188">De volgende uitvoer wordt weergegeven.</span><span class="sxs-lookup"><span data-stu-id="5fd94-188">The following output appears.</span></span>

    ```
    Handles  NPM(K)  PM(K)   WS(K)  VS(M)  CPU(s)   Id   ProcessName
    -------  ------  -----   -----  -----   ------ --   -----------
        354      11  10036   18992    85   0.67   3284   iexplore
    ```

- <span data-ttu-id="5fd94-189">Gebruik de volgende opdracht als de Internet Explorer, Outlook en Kladblok processen met de naam 'IEXPLORE', 'OUTLOOK' en 'KLADBLOK,'.</span><span class="sxs-lookup"><span data-stu-id="5fd94-189">To list the Internet Explorer, Outlook, and Notepad processes named "IEXPLORE," "OUTLOOK," and "NOTEPAD," use the following command.</span></span> <span data-ttu-id="5fd94-190">Als er meerdere processen, die allemaal worden weergegeven.</span><span class="sxs-lookup"><span data-stu-id="5fd94-190">If there are multiple processes, all of them are displayed.</span></span>

    ```powershell
    PS> get-proc -name iexplore, outlook, notepad
    ```

<span data-ttu-id="5fd94-191">De volgende uitvoer wordt weergegeven.</span><span class="sxs-lookup"><span data-stu-id="5fd94-191">The following output appears.</span></span>

    ```
    Handles  NPM(K)  PM(K)   WS(K)  VS(M)  CPU(s)   Id   ProcessName
    -------  ------  -----   -----  -----  ------   --    -----------
        732      21  24696    5000    138   2.25  2288   iexplore
        715      19  20556   14116    136   1.78  3860   iexplore
       3917      62  74096   58112    468 191.56  1848   OUTLOOK
         39       2   1024    3280     30   0.09  1444   notepad
         39       2   1024     356     30   0.08  3396   notepad
    ```

## <a name="see-also"></a><span data-ttu-id="5fd94-192">Zie ook</span><span class="sxs-lookup"><span data-stu-id="5fd94-192">See Also</span></span>

[<span data-ttu-id="5fd94-193">Parameters die proces Pipeline ingevoerd toe te voegen</span><span class="sxs-lookup"><span data-stu-id="5fd94-193">Adding Parameters that Process Pipeline Input</span></span>](./adding-parameters-that-process-pipeline-input.md)

[<span data-ttu-id="5fd94-194">Het maken van uw eerste Cmdlet</span><span class="sxs-lookup"><span data-stu-id="5fd94-194">Creating Your First Cmdlet</span></span>](./creating-a-cmdlet-without-parameters.md)

[<span data-ttu-id="5fd94-195">Objecttypen uitbreiden en opmaak</span><span class="sxs-lookup"><span data-stu-id="5fd94-195">Extending Object Types and Formatting</span></span>](http://msdn.microsoft.com/en-us/da976d91-a3d6-44e8-affa-466b1e2bd351)

[<span data-ttu-id="5fd94-196">Over het registreren van Providers,-Cmdlets en -toepassingen hosten</span><span class="sxs-lookup"><span data-stu-id="5fd94-196">How to Register Cmdlets, Providers, and Host Applications</span></span>](http://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c)

[<span data-ttu-id="5fd94-197">Windows PowerShell-referentie</span><span class="sxs-lookup"><span data-stu-id="5fd94-197">Windows PowerShell Reference</span></span>](../windows-powershell-reference.md)

[<span data-ttu-id="5fd94-198">Cmdlet-voorbeelden</span><span class="sxs-lookup"><span data-stu-id="5fd94-198">Cmdlet Samples</span></span>](./cmdlet-samples.md)
