---
title: Toevoegen van aliassen, jokertekens, en voor het tot Cmdlet-Parameters | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 931ccace-c565-4a98-8dcc-df00f86394b1
caps.latest.revision: 8
ms.openlocfilehash: bc921537062e35aa203fa3ee95d3b7211c89cb28
ms.sourcegitcommit: 46bebe692689ebedfe65ff2c828fe666b443198d
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/10/2019
ms.locfileid: "67733844"
---
# <a name="adding-aliases-wildcard-expansion-and-help-to-cmdlet-parameters"></a><span data-ttu-id="8d7e7-102">Aliassen, jokertekenuitbreiding en Help toevoegen aan cmdlet-parameters</span><span class="sxs-lookup"><span data-stu-id="8d7e7-102">Adding Aliases, Wildcard Expansion, and Help to Cmdlet Parameters</span></span>

<span data-ttu-id="8d7e7-103">In deze sectie wordt beschreven hoe u aliassen, jokertekens, toevoegen en Help berichten naar de parameters van de cmdlet Stop-Proc (beschreven in [maken van een Cmdlet die Hiermee wijzigt u het systeem](./creating-a-cmdlet-that-modifies-the-system.md)).</span><span class="sxs-lookup"><span data-stu-id="8d7e7-103">This section describes how to add aliases, wildcard expansion, and Help messages to the parameters of the Stop-Proc cmdlet (described in [Creating a Cmdlet that Modifies the System](./creating-a-cmdlet-that-modifies-the-system.md)).</span></span>

<span data-ttu-id="8d7e7-104">Deze cmdlet Stop-Proc probeert te beëindigen van processen die worden opgehaald met de cmdlet Get-Proc (beschreven in [het maken van uw eerste Cmdlet](./creating-a-cmdlet-without-parameters.md)).</span><span class="sxs-lookup"><span data-stu-id="8d7e7-104">This Stop-Proc cmdlet attempts to stop processes that are retrieved using the Get-Proc cmdlet (described in [Creating Your First Cmdlet](./creating-a-cmdlet-without-parameters.md)).</span></span>

## <a name="defining-the-cmdlet"></a><span data-ttu-id="8d7e7-105">De Cmdlet definiëren</span><span class="sxs-lookup"><span data-stu-id="8d7e7-105">Defining the Cmdlet</span></span>

<span data-ttu-id="8d7e7-106">De eerste stap bij het maken van de cmdlet is altijd naamgeving van de cmdlet en de .NET-klasse die de cmdlet declareren.</span><span class="sxs-lookup"><span data-stu-id="8d7e7-106">The first step in cmdlet creation is always naming the cmdlet and declaring the .NET class that implements the cmdlet.</span></span> <span data-ttu-id="8d7e7-107">Omdat u een cmdlet als u wilt wijzigen van het systeem schrijft, moet deze dienovereenkomstig worden genoemd.</span><span class="sxs-lookup"><span data-stu-id="8d7e7-107">Because you are writing a cmdlet to change the system, it should be named accordingly.</span></span> <span data-ttu-id="8d7e7-108">Omdat deze cmdlet systeemprocessen stopt, wordt de term 'Stop', die is gedefinieerd door de [System.Management.Automation.Verbslifecycle](/dotnet/api/System.Management.Automation.VerbsLifeCycle) klasse, met het zelfstandig naamwoord 'Proc' om aan te geven van proces.</span><span class="sxs-lookup"><span data-stu-id="8d7e7-108">Because this cmdlet stops system processes, it uses the verb "Stop", defined by the [System.Management.Automation.Verbslifecycle](/dotnet/api/System.Management.Automation.VerbsLifeCycle) class, with the noun "Proc" to indicate process.</span></span> <span data-ttu-id="8d7e7-109">Zie voor meer informatie over goedgekeurde werkwoorden [namen van de term cmdlets](./approved-verbs-for-windows-powershell-commands.md).</span><span class="sxs-lookup"><span data-stu-id="8d7e7-109">For more information about approved cmdlet verbs, see [Cmdlet Verb Names](./approved-verbs-for-windows-powershell-commands.md).</span></span>

<span data-ttu-id="8d7e7-110">De volgende code wordt de klassedefinitie van deze cmdlet Stop-Proc.</span><span class="sxs-lookup"><span data-stu-id="8d7e7-110">The following code is the class definition for this Stop-Proc cmdlet.</span></span>

```csharp
[Cmdlet(VerbsLifecycle.Stop, "proc",
        SupportsShouldProcess = true)]
public class StopProcCommand : Cmdlet
```

## <a name="defining-parameters-for-system-modification"></a><span data-ttu-id="8d7e7-111">Parameters voor aanpassing van het systeem definiëren</span><span class="sxs-lookup"><span data-stu-id="8d7e7-111">Defining Parameters for System Modification</span></span>

<span data-ttu-id="8d7e7-112">De cmdlet moet parameters definiëren die ondersteuningssysteem wijzigingen en feedback van gebruikers.</span><span class="sxs-lookup"><span data-stu-id="8d7e7-112">Your cmdlet needs to define parameters that support system modifications and user feedback.</span></span> <span data-ttu-id="8d7e7-113">De cmdlet moet definiëren een `Name` parameter of een vergelijkbare zodat de cmdlet kunnen wijzigen van het systeem door een soort id.</span><span class="sxs-lookup"><span data-stu-id="8d7e7-113">The cmdlet should define a `Name` parameter or equivalent so that the cmdlet will be able to modify the system by some sort of identifier.</span></span> <span data-ttu-id="8d7e7-114">Bovendien de cmdlet moet definiëren de `Force` en `PassThru` parameters.</span><span class="sxs-lookup"><span data-stu-id="8d7e7-114">In addition, the cmdlet should define the `Force` and `PassThru` parameters.</span></span> <span data-ttu-id="8d7e7-115">Zie voor meer informatie over deze parameters [maken van een Cmdlet die Hiermee wijzigt u het systeem](./creating-a-cmdlet-that-modifies-the-system.md).</span><span class="sxs-lookup"><span data-stu-id="8d7e7-115">For more information about these parameters, see [Creating a Cmdlet that Modifies the System](./creating-a-cmdlet-that-modifies-the-system.md).</span></span>

## <a name="defining-a-parameter-alias"></a><span data-ttu-id="8d7e7-116">Een Parameteralias definiëren</span><span class="sxs-lookup"><span data-stu-id="8d7e7-116">Defining a Parameter Alias</span></span>

<span data-ttu-id="8d7e7-117">Een parameteralias is een alternatieve naam of een goed gedefinieerde 1- of 2 letter korte naam voor een cmdlet-parameter.</span><span class="sxs-lookup"><span data-stu-id="8d7e7-117">A parameter alias can be an alternate name or a well-defined 1-letter or 2-letter short name for a cmdlet parameter.</span></span> <span data-ttu-id="8d7e7-118">In beide gevallen is het doel van het gebruik van aliassen voor het vereenvoudigen van de vermelding van de gebruiker vanaf de opdrachtregel.</span><span class="sxs-lookup"><span data-stu-id="8d7e7-118">In both cases, the goal of using aliases is to simplify user entry from the command line.</span></span> <span data-ttu-id="8d7e7-119">Windows PowerShell ondersteunt aliassen via de [System.Management.Automation.Aliasattribute](/dotnet/api/System.Management.Automation.AliasAttribute) kenmerk, die gebruikmaakt van de syntaxis van de declaratie [Alias()].</span><span class="sxs-lookup"><span data-stu-id="8d7e7-119">Windows PowerShell supports parameter aliases through the [System.Management.Automation.Aliasattribute](/dotnet/api/System.Management.Automation.AliasAttribute) attribute, which uses the declaration syntax [Alias()].</span></span>

<span data-ttu-id="8d7e7-120">De volgende code toont hoe een alias is toegevoegd aan de `Name` parameter.</span><span class="sxs-lookup"><span data-stu-id="8d7e7-120">The following code shows how an alias is added to the `Name` parameter.</span></span>

```csharp
/// <summary>
/// Specify the mandatory Name parameter used to identify the
/// processes to be stopped.
/// </summary>
[Parameter(
           Position = 0,
           Mandatory = true,
           ValueFromPipeline = true,
           ValueFromPipelineByPropertyName = true,
           HelpMessage = "The name of one or more processes to stop. Wildcards are permitted."
)]
[Alias("ProcessName")]
public string[] Name
{
  get { return processNames; }
  set { processNames = value; }
}
private string[] processNames;
```

<span data-ttu-id="8d7e7-121">Naast het gebruik van de [System.Management.Automation.Aliasattribute](/dotnet/api/System.Management.Automation.AliasAttribute) kenmerk, de Windows PowerShell-runtime voert gedeeltelijke namen matchen, zelfs als er geen aliassen zijn opgegeven.</span><span class="sxs-lookup"><span data-stu-id="8d7e7-121">In addition to using the [System.Management.Automation.Aliasattribute](/dotnet/api/System.Management.Automation.AliasAttribute) attribute, the Windows PowerShell runtime performs partial name matching, even if no aliases are specified.</span></span> <span data-ttu-id="8d7e7-122">Bijvoorbeeld, als de cmdlet heeft een `FileName` parameter en dat is de enige parameter die met begint `F`, de gebruiker kan invoeren `Filename`, `Filenam`, `File`, `Fi`, of `F` en nog steeds herkent de vermelding als de `FileName` parameter.</span><span class="sxs-lookup"><span data-stu-id="8d7e7-122">For example, if your cmdlet has a `FileName` parameter and that is the only parameter that starts with `F`, the user could enter `Filename`, `Filenam`, `File`, `Fi`, or `F` and still recognize the entry as the `FileName` parameter.</span></span>

## <a name="creating-help-for-parameters"></a><span data-ttu-id="8d7e7-123">Help voor Parameters maken</span><span class="sxs-lookup"><span data-stu-id="8d7e7-123">Creating Help for Parameters</span></span>

<span data-ttu-id="8d7e7-124">Windows PowerShell kunt u Help-informatie voor cmdlet-parameters maken.</span><span class="sxs-lookup"><span data-stu-id="8d7e7-124">Windows PowerShell allows you to create Help for cmdlet parameters.</span></span> <span data-ttu-id="8d7e7-125">Doe dit voor elke parameter die wordt gebruikt voor feedback op systeem wijzigen en de gebruiker.</span><span class="sxs-lookup"><span data-stu-id="8d7e7-125">Do this for any parameter used for system modification and user feedback.</span></span> <span data-ttu-id="8d7e7-126">Voor elke parameter voor de ondersteuning van Help-informatie, kunt u instellen de `HelpMessage` kenmerken van het sleutelwoord in de [System.Management.Automation.Parameterattribute](/dotnet/api/System.Management.Automation.ParameterAttribute) declaratie van het kenmerk.</span><span class="sxs-lookup"><span data-stu-id="8d7e7-126">For each parameter to support Help, you can set the `HelpMessage` attribute keyword in the [System.Management.Automation.Parameterattribute](/dotnet/api/System.Management.Automation.ParameterAttribute) attribute declaration.</span></span> <span data-ttu-id="8d7e7-127">Dit trefwoord definieert de tekst die moet worden weergegeven voor de gebruiker voor hulp bij het gebruik van de parameter.</span><span class="sxs-lookup"><span data-stu-id="8d7e7-127">This keyword defines the text to display to the user for assistance in using the parameter.</span></span> <span data-ttu-id="8d7e7-128">U kunt ook instellen de `HelpMessageBaseName` sleutelwoord voor het identificeren van de naam op van een resource moet worden gebruikt voor het bericht.</span><span class="sxs-lookup"><span data-stu-id="8d7e7-128">You can also set the `HelpMessageBaseName` keyword to identify the base name of a resource to use for the message.</span></span> <span data-ttu-id="8d7e7-129">Als u dit sleutelwoord instelt, moet u ook instellen de `HelpMessageResourceId` trefwoord om op te geven van de resource-id.</span><span class="sxs-lookup"><span data-stu-id="8d7e7-129">If you set this keyword, you must also set the `HelpMessageResourceId` keyword to specify the resource identifier.</span></span>

<span data-ttu-id="8d7e7-130">De volgende code uit deze cmdlet Stop-Proc definieert de `HelpMessage` kenmerk trefwoord voor de `Name` parameter.</span><span class="sxs-lookup"><span data-stu-id="8d7e7-130">The following code from this Stop-Proc cmdlet defines the `HelpMessage` attribute keyword for the `Name` parameter.</span></span>

```csharp
/// <summary>
/// Specify the mandatory Name parameter used to identify the
/// processes to be stopped.
/// </summary>
[Parameter(
           Position = 0,
           Mandatory = true,
           ValueFromPipeline = true,
           ValueFromPipelineByPropertyName = true,
           HelpMessage = "The name of one or more processes to stop. Wildcards are permitted."
)]
```

## <a name="overriding-an-input-processing-method"></a><span data-ttu-id="8d7e7-131">Invoer verwerken methode te overschrijven</span><span class="sxs-lookup"><span data-stu-id="8d7e7-131">Overriding an Input Processing Method</span></span>

<span data-ttu-id="8d7e7-132">De cmdlet moet verwerken van methode invoer overschrijven, dit is meestal [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord).</span><span class="sxs-lookup"><span data-stu-id="8d7e7-132">Your cmdlet must override an input processing method, most often this will be [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord).</span></span> <span data-ttu-id="8d7e7-133">Bij het wijzigen van het systeem, de cmdlet moet aanroepen de [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) en [System.Management.Automation.Cmdlet.ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) methoden waarmee de gebruiker om feedback te geven voordat er een wijziging is aangebracht.</span><span class="sxs-lookup"><span data-stu-id="8d7e7-133">When modifying the system, the cmdlet should call the [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) and [System.Management.Automation.Cmdlet.ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) methods to allow the user to provide feedback before a change is made.</span></span> <span data-ttu-id="8d7e7-134">Zie voor meer informatie over deze methoden, [maken van een Cmdlet die Hiermee wijzigt u het systeem](./creating-a-cmdlet-that-modifies-the-system.md).</span><span class="sxs-lookup"><span data-stu-id="8d7e7-134">For more information about these methods, see [Creating a Cmdlet that Modifies the System](./creating-a-cmdlet-that-modifies-the-system.md).</span></span>

## <a name="supporting-wildcard-expansion"></a><span data-ttu-id="8d7e7-135">Ondersteunende jokertekens</span><span class="sxs-lookup"><span data-stu-id="8d7e7-135">Supporting Wildcard Expansion</span></span>

<span data-ttu-id="8d7e7-136">Als u wilt toestaan dat de selectie van meerdere objecten, uw cmdlet kunt gebruiken de [System.Management.Automation.Wildcardpattern](/dotnet/api/System.Management.Automation.WildcardPattern) en [System.Management.Automation.Wildcardoptions](/dotnet/api/System.Management.Automation.WildcardOptions) klassen voor jokertekens worden uitbreiding voor de parameter invoeren.</span><span class="sxs-lookup"><span data-stu-id="8d7e7-136">To allow the selection of multiple objects, your cmdlet can use the [System.Management.Automation.Wildcardpattern](/dotnet/api/System.Management.Automation.WildcardPattern) and [System.Management.Automation.Wildcardoptions](/dotnet/api/System.Management.Automation.WildcardOptions) classes to provide wildcard expansion support for parameter input.</span></span> <span data-ttu-id="8d7e7-137">Er zijn voorbeelden van jokertekenpatronen lsa \* \*.txt en [a-c]\*.</span><span class="sxs-lookup"><span data-stu-id="8d7e7-137">Examples of wildcard patterns are lsa\*, \*.txt, and [a-c]\*.</span></span> <span data-ttu-id="8d7e7-138">Gebruik de back-aanhalingsteken (') als een escape-teken als het patroon bevat een teken letterlijk moet worden gebruikt.</span><span class="sxs-lookup"><span data-stu-id="8d7e7-138">Use the back-quote character (\`) as an escape character when the pattern contains a character that should be used literally.</span></span>

<span data-ttu-id="8d7e7-139">Wildcard-uitbreidingen van bestands- en padnamen zijn voorbeelden van veelvoorkomende scenario's waarin de cmdlet ondersteuning voor het pad invoer toestaan kunt wanneer de selectie van meerdere objecten vereist is.</span><span class="sxs-lookup"><span data-stu-id="8d7e7-139">Wildcard expansions of file and path names are examples of common scenarios where the cmdlet may want to allow support for path inputs when the selection of multiple objects is required.</span></span> <span data-ttu-id="8d7e7-140">Gebruikelijk is in het bestandssysteem, waarbij een gebruiker wil zien van alle bestanden die zich bevinden in de huidige map.</span><span class="sxs-lookup"><span data-stu-id="8d7e7-140">A common case is in the file system, where a user wants to see all files residing in the current folder.</span></span>

<span data-ttu-id="8d7e7-141">U hoeft slechts zelden een aangepaste jokertekens patroon overeenkomende implementatie.</span><span class="sxs-lookup"><span data-stu-id="8d7e7-141">You should need a customized wildcard pattern matching implementation only rarely.</span></span> <span data-ttu-id="8d7e7-142">In dit geval moet de cmdlet ondersteuning voor de volledige POSIX-1003.2, 3,13 specificatie voor jokertekens of de volgende vereenvoudigde subset:</span><span class="sxs-lookup"><span data-stu-id="8d7e7-142">In this case, your cmdlet should support either the full POSIX 1003.2, 3.13 specification for wildcard expansion or the following simplified subset:</span></span>

- <span data-ttu-id="8d7e7-143">**Vraagteken (?).**</span><span class="sxs-lookup"><span data-stu-id="8d7e7-143">**Question mark (?).**</span></span> <span data-ttu-id="8d7e7-144">Komt overeen met een willekeurig teken op de opgegeven locatie.</span><span class="sxs-lookup"><span data-stu-id="8d7e7-144">Matches any character at the specified location.</span></span>

- <span data-ttu-id="8d7e7-145">**Sterretje (\*).**</span><span class="sxs-lookup"><span data-stu-id="8d7e7-145">**Asterisk (\*).**</span></span> <span data-ttu-id="8d7e7-146">Komt overeen met nul of meer tekens vanaf de opgegeven locatie.</span><span class="sxs-lookup"><span data-stu-id="8d7e7-146">Matches zero or more characters starting at the specified location.</span></span>

- <span data-ttu-id="8d7e7-147">**Open haakje sluiten ([]).**</span><span class="sxs-lookup"><span data-stu-id="8d7e7-147">**Open bracket ([).**</span></span> <span data-ttu-id="8d7e7-148">Introduceert een haakje-expressie voor het patroon die tekens of een bereik met tekens kan bevatten.</span><span class="sxs-lookup"><span data-stu-id="8d7e7-148">Introduces a pattern bracket expression that can contain characters or a range of characters.</span></span> <span data-ttu-id="8d7e7-149">Als een bereik is vereist, wordt een koppelteken (-) gebruikt om aan te geven van het bereik.</span><span class="sxs-lookup"><span data-stu-id="8d7e7-149">If a range is required, a hyphen (-) is used to indicate the range.</span></span>

- <span data-ttu-id="8d7e7-150">**Sluiten haak sluiten (]).**</span><span class="sxs-lookup"><span data-stu-id="8d7e7-150">**Close bracket (]).**</span></span> <span data-ttu-id="8d7e7-151">Een patroon haakje-expressie wordt beëindigd.</span><span class="sxs-lookup"><span data-stu-id="8d7e7-151">Ends a pattern bracket expression.</span></span>

- <span data-ttu-id="8d7e7-152">**Back-aanhalingsteken (') als escape-teken.**</span><span class="sxs-lookup"><span data-stu-id="8d7e7-152">**Back-quote escape character (\`).**</span></span> <span data-ttu-id="8d7e7-153">Geeft aan dat het volgende teken letterlijk moet worden genomen.</span><span class="sxs-lookup"><span data-stu-id="8d7e7-153">Indicates that the next character should be taken literally.</span></span> <span data-ttu-id="8d7e7-154">Let erop dat bij het opgeven van de back-aanhalingsteken vanaf de opdrachtregel (in plaats van via een programma opgeven), het back-offerte escape-teken moet worden twee keer opgegeven.</span><span class="sxs-lookup"><span data-stu-id="8d7e7-154">Be aware that when specifying the back-quote character from the command line (as opposed to specifying it programmatically), the back-quote escape character must be specified twice.</span></span>

> [!NOTE]
> <span data-ttu-id="8d7e7-155">Zie voor meer informatie over de jokertekenpatronen [ondersteunt jokertekens in de Cmdlet-Parameters](./supporting-wildcard-characters-in-cmdlet-parameters.md).</span><span class="sxs-lookup"><span data-stu-id="8d7e7-155">For more information about wildcard patterns, see [Supporting Wildcards in Cmdlet Parameters](./supporting-wildcard-characters-in-cmdlet-parameters.md).</span></span>

<span data-ttu-id="8d7e7-156">De volgende code laat zien hoe u jokertekens opties instellen en definiëren van het jokerteken-patroon gebruikt voor het oplossen van de `Name` parameter voor deze cmdlet.</span><span class="sxs-lookup"><span data-stu-id="8d7e7-156">The following code shows how to set wildcard options and define the wildcard pattern used for resolving the `Name` parameter for this cmdlet.</span></span>

```csharp
WildcardOptions options = WildcardOptions.IgnoreCase |
                          WildcardOptions.Compiled;
WildcardPattern wildcard = new WildcardPattern(name,options);
```

<span data-ttu-id="8d7e7-157">De volgende code toont hoe u kunt testen of de procesnaam overeenkomt met het patroon gedefinieerde jokertekens.</span><span class="sxs-lookup"><span data-stu-id="8d7e7-157">The following code shows how to test whether the process name matches the defined wildcard pattern.</span></span> <span data-ttu-id="8d7e7-158">U ziet dat in dit geval als de procesnaam komt niet overeen met het patroon, de cmdlet blijft op de naam van de volgende procedure.</span><span class="sxs-lookup"><span data-stu-id="8d7e7-158">Notice that, in this case, if the process name does not match the pattern, the cmdlet continues on to get the next process name.</span></span>

```csharp
if (!wildcard.IsMatch(processName))
{
  continue;
}
```

## <a name="code-sample"></a><span data-ttu-id="8d7e7-159">Voorbeeld van code</span><span class="sxs-lookup"><span data-stu-id="8d7e7-159">Code Sample</span></span>

<span data-ttu-id="8d7e7-160">Voor de volledige C# voorbeeldcode, Zie [StopProcessSample03 voorbeeld](./stopprocesssample03-sample.md).</span><span class="sxs-lookup"><span data-stu-id="8d7e7-160">For the complete C# sample code, see [StopProcessSample03 Sample](./stopprocesssample03-sample.md).</span></span>

## <a name="define-object-types-and-formatting"></a><span data-ttu-id="8d7e7-161">Definieer objecttypen en opmaak</span><span class="sxs-lookup"><span data-stu-id="8d7e7-161">Define Object Types and Formatting</span></span>

<span data-ttu-id="8d7e7-162">Windows PowerShell wordt informatie doorgegeven tussen cmdlets met behulp van .net-objecten.</span><span class="sxs-lookup"><span data-stu-id="8d7e7-162">Windows PowerShell passes information between cmdlets using .Net objects.</span></span> <span data-ttu-id="8d7e7-163">Als gevolg daarvan kan een cmdlet mogelijk nodig hebt voor het definiëren van een eigen type, of de cmdlet moet om uit te breiden van een bestaand type geleverd door een andere cmdlet.</span><span class="sxs-lookup"><span data-stu-id="8d7e7-163">Consequently, a cmdlet may need to define its own type, or the cmdlet may need to extend an existing type provided by another cmdlet.</span></span> <span data-ttu-id="8d7e7-164">Zie voor meer informatie over het definiëren van nieuwe typen of uitbreiden van bestaande typen [objecttypen uitbreiden en opmaak](/previous-versions//ms714665(v=vs.85)).</span><span class="sxs-lookup"><span data-stu-id="8d7e7-164">For more information about defining new types or extending existing types, see [Extending Object Types and Formatting](/previous-versions//ms714665(v=vs.85)).</span></span>

## <a name="building-the-cmdlet"></a><span data-ttu-id="8d7e7-165">Het bouwen van de Cmdlet</span><span class="sxs-lookup"><span data-stu-id="8d7e7-165">Building the Cmdlet</span></span>

<span data-ttu-id="8d7e7-166">Na de implementatie van een cmdlet, moet deze met Windows PowerShell worden geregistreerd via een Windows PowerShell-module.</span><span class="sxs-lookup"><span data-stu-id="8d7e7-166">After implementing a cmdlet, it must be registered with Windows PowerShell through a Windows PowerShell snap-in.</span></span> <span data-ttu-id="8d7e7-167">Zie voor meer informatie over het registreren van cmdlets [hoe u Cmdlets registreren, Providers en hosting van toepassingen](/previous-versions//ms714644(v=vs.85)).</span><span class="sxs-lookup"><span data-stu-id="8d7e7-167">For more information about registering cmdlets, see [How to Register Cmdlets, Providers, and Host Applications](/previous-versions//ms714644(v=vs.85)).</span></span>

## <a name="testing-the-cmdlet"></a><span data-ttu-id="8d7e7-168">Testen van de Cmdlet</span><span class="sxs-lookup"><span data-stu-id="8d7e7-168">Testing the Cmdlet</span></span>

<span data-ttu-id="8d7e7-169">Wanneer de cmdlet is geregistreerd met Windows PowerShell, kunt u deze testen door te voeren op de opdrachtregel.</span><span class="sxs-lookup"><span data-stu-id="8d7e7-169">When your cmdlet has been registered with Windows PowerShell, you can test it by running it on the command line.</span></span> <span data-ttu-id="8d7e7-170">We gaan de voorbeeld-cmdlet Stop-Proc testen.</span><span class="sxs-lookup"><span data-stu-id="8d7e7-170">Let's test the sample Stop-Proc cmdlet.</span></span> <span data-ttu-id="8d7e7-171">Zie voor meer informatie over het gebruik van cmdlets vanaf de opdrachtregel de [aan de slag met Windows PowerShell](/powershell/scripting/getting-started/getting-started-with-windows-powershell).</span><span class="sxs-lookup"><span data-stu-id="8d7e7-171">For more information about using cmdlets from the command line, see the [Getting Started with Windows PowerShell](/powershell/scripting/getting-started/getting-started-with-windows-powershell).</span></span>

- <span data-ttu-id="8d7e7-172">Start Windows PowerShell en Stop-procedure gebruiken om te stoppen van een proces met behulp van de procesnaam-alias voor de `Name` parameter.</span><span class="sxs-lookup"><span data-stu-id="8d7e7-172">Start Windows PowerShell and use Stop-Proc to stop a process using the ProcessName alias for the `Name` parameter.</span></span>

    ```powershell
    PS> stop-proc -ProcessName notepad
    ```

<span data-ttu-id="8d7e7-173">De volgende uitvoer wordt weergegeven.</span><span class="sxs-lookup"><span data-stu-id="8d7e7-173">The following output appears.</span></span>

    ```
    Confirm
    Are you sure you want to perform this action?
    Performing operation "stop-proc" on Target "notepad (3496)".
    [Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "Y"): Y
    ```

- <span data-ttu-id="8d7e7-174">Controleer de volgende vermelding op de opdrachtregel.</span><span class="sxs-lookup"><span data-stu-id="8d7e7-174">Make the following entry on the command line.</span></span> <span data-ttu-id="8d7e7-175">Omdat de parameter Name verplicht is, wordt u gevraagd voor het.</span><span class="sxs-lookup"><span data-stu-id="8d7e7-175">Because the Name parameter is mandatory, you are prompted for it.</span></span> <span data-ttu-id="8d7e7-176">Invoeren '!? "</span><span class="sxs-lookup"><span data-stu-id="8d7e7-176">Entering "!?"</span></span> <span data-ttu-id="8d7e7-177">Hiermee geeft u de help-tekst die is gekoppeld aan de parameter.</span><span class="sxs-lookup"><span data-stu-id="8d7e7-177">brings up the help text associated with the parameter.</span></span>

    ```powershell
    PS> stop-proc
    ```

<span data-ttu-id="8d7e7-178">De volgende uitvoer wordt weergegeven.</span><span class="sxs-lookup"><span data-stu-id="8d7e7-178">The following output appears.</span></span>

    ```
    Cmdlet stop-proc at command pipeline position 1
    Supply values for the following parameters:
    (Type !? for Help.)
    Name[0]: !?
    The name of one or more processes to stop. Wildcards are permitted.
    Name[0]: notepad
    ```

- <span data-ttu-id="8d7e7-179">Maak nu de volgende vermelding te beëindigen alle processen die overeenkomen met het patroon jokerteken ' \* Opmerking\*'.</span><span class="sxs-lookup"><span data-stu-id="8d7e7-179">Now make the following entry to stop all processes that match the wildcard pattern "\*note\*".</span></span> <span data-ttu-id="8d7e7-180">U wordt gevraagd voordat elk proces dat overeenkomt met het patroon wordt gestopt.</span><span class="sxs-lookup"><span data-stu-id="8d7e7-180">You are prompted before stopping each process that matches the pattern.</span></span>

    ```powershell
    PS> stop-proc -Name *note*
    ```

<span data-ttu-id="8d7e7-181">De volgende uitvoer wordt weergegeven.</span><span class="sxs-lookup"><span data-stu-id="8d7e7-181">The following output appears.</span></span>

    ```
    Confirm
    Are you sure you want to perform this action?
    Performing operation "stop-proc" on Target "notepad (1112)".
    [Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "Y"): Y
    ```

<span data-ttu-id="8d7e7-182">De volgende uitvoer wordt weergegeven.</span><span class="sxs-lookup"><span data-stu-id="8d7e7-182">The following output appears.</span></span>

    ```
    Confirm
    Are you sure you want to perform this action?
    Performing operation "stop-proc" on Target "ONENOTEM (3712)".
    [Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "Y"): N
    ```

<span data-ttu-id="8d7e7-183">De volgende uitvoer wordt weergegeven.</span><span class="sxs-lookup"><span data-stu-id="8d7e7-183">The following output appears.</span></span>

    ```
    Confirm
    Are you sure you want to perform this action?
    Performing operation "stop-proc" on Target "ONENOTE (3592)".
    [Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "Y"): N
    ```

## <a name="see-also"></a><span data-ttu-id="8d7e7-184">Zie ook</span><span class="sxs-lookup"><span data-stu-id="8d7e7-184">See Also</span></span>

[<span data-ttu-id="8d7e7-185">Maken van een Cmdlet die Hiermee wijzigt u het systeem</span><span class="sxs-lookup"><span data-stu-id="8d7e7-185">Create a Cmdlet that Modifies the System</span></span>](./creating-a-cmdlet-that-modifies-the-system.md)

[<span data-ttu-id="8d7e7-186">Over het maken van een Windows PowerShell-Cmdlet</span><span class="sxs-lookup"><span data-stu-id="8d7e7-186">How to Create a Windows PowerShell Cmdlet</span></span>](/powershell/developer/cmdlet/writing-a-windows-powershell-cmdlet)

<span data-ttu-id="8d7e7-187">[Objecttypen uitbreiden en opmaak](/previous-versions//ms714665(v=vs.85))</span><span class="sxs-lookup"><span data-stu-id="8d7e7-187">[Extending Object Types and Formatting](/previous-versions//ms714665(v=vs.85))</span></span>

<span data-ttu-id="8d7e7-188">[Over het registreren van Providers,-Cmdlets en -toepassingen hosten](/previous-versions//ms714644(v=vs.85))</span><span class="sxs-lookup"><span data-stu-id="8d7e7-188">[How to Register Cmdlets, Providers, and Host Applications](/previous-versions//ms714644(v=vs.85))</span></span>

[<span data-ttu-id="8d7e7-189">Ondersteuning van jokertekens in de Cmdlet-Parameters</span><span class="sxs-lookup"><span data-stu-id="8d7e7-189">Supporting Wildcards in Cmdlet Parameters</span></span>](./supporting-wildcard-characters-in-cmdlet-parameters.md)

[<span data-ttu-id="8d7e7-190">Windows PowerShell SDK</span><span class="sxs-lookup"><span data-stu-id="8d7e7-190">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)
