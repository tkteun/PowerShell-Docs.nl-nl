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
ms.openlocfilehash: db664e589f625855b5a33a02c522d6b238ad2810
ms.sourcegitcommit: caac7d098a448232304c9d6728e7340ec7517a71
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 03/16/2019
ms.locfileid: "58054868"
---
# <a name="adding-aliases-wildcard-expansion-and-help-to-cmdlet-parameters"></a><span data-ttu-id="78522-102">Aliassen, jokertekenuitbreiding en Help toevoegen aan cmdlet-parameters</span><span class="sxs-lookup"><span data-stu-id="78522-102">Adding Aliases, Wildcard Expansion, and Help to Cmdlet Parameters</span></span>

<span data-ttu-id="78522-103">In deze sectie wordt beschreven hoe u aliassen, jokertekens, toevoegen en Help berichten naar de parameters van de cmdlet Stop-Proc (beschreven in [maken van een Cmdlet die Hiermee wijzigt u het systeem](./creating-a-cmdlet-that-modifies-the-system.md)).</span><span class="sxs-lookup"><span data-stu-id="78522-103">This section describes how to add aliases, wildcard expansion, and Help messages to the parameters of the Stop-Proc cmdlet (described in [Creating a Cmdlet that Modifies the System](./creating-a-cmdlet-that-modifies-the-system.md)).</span></span>

<span data-ttu-id="78522-104">Deze cmdlet Stop-Proc probeert te beëindigen van processen die worden opgehaald met de cmdlet Get-Proc (beschreven in [het maken van uw eerste Cmdlet](./creating-a-cmdlet-without-parameters.md)).</span><span class="sxs-lookup"><span data-stu-id="78522-104">This Stop-Proc cmdlet attempts to stop processes that are retrieved using the Get-Proc cmdlet (described in [Creating Your First Cmdlet](./creating-a-cmdlet-without-parameters.md)).</span></span>

<span data-ttu-id="78522-105">Onderwerpen in deze sectie bevatten het volgende:</span><span class="sxs-lookup"><span data-stu-id="78522-105">Topics in this section include the following:</span></span>

- [<span data-ttu-id="78522-106">De Cmdlet definiëren</span><span class="sxs-lookup"><span data-stu-id="78522-106">Defining the Cmdlet</span></span>](#Defining-the-Cmdlet)

- [<span data-ttu-id="78522-107">Parameters voor aanpassing van het systeem definiëren</span><span class="sxs-lookup"><span data-stu-id="78522-107">Defining Parameters for System Modification</span></span>](#Defining-Parameters-for-System-Modification)

- [<span data-ttu-id="78522-108">Een Parameteralias definiëren</span><span class="sxs-lookup"><span data-stu-id="78522-108">Defining a Parameter Alias</span></span>](#Defining-a-Parameter-Alias)

- [<span data-ttu-id="78522-109">Help voor Parameters maken</span><span class="sxs-lookup"><span data-stu-id="78522-109">Creating Help for Parameters</span></span>](#Creating-Help-for-Parameters)

- [<span data-ttu-id="78522-110">Invoer verwerken methode te overschrijven</span><span class="sxs-lookup"><span data-stu-id="78522-110">Overriding an Input Processing Method</span></span>](#Overriding-an-Input-Processing-Method)

- [<span data-ttu-id="78522-111">Ondersteunende jokertekens</span><span class="sxs-lookup"><span data-stu-id="78522-111">Supporting Wildcard Expansion</span></span>](#Supporting-Wildcard-Expansion)

- [<span data-ttu-id="78522-112">Voorbeeld van code</span><span class="sxs-lookup"><span data-stu-id="78522-112">Code Sample</span></span>](#Defining-a-Parameter-Alias)

- [<span data-ttu-id="78522-113">Objecttype definiëren en opmaak</span><span class="sxs-lookup"><span data-stu-id="78522-113">Defining Object Types and Formatting</span></span>](#Define-Object-Types-and-Formatting)

- [<span data-ttu-id="78522-114">Het bouwen van de Cmdlet</span><span class="sxs-lookup"><span data-stu-id="78522-114">Building the Cmdlet</span></span>](#Building-the-Cmdlet)

- [<span data-ttu-id="78522-115">Testen van de Cmdlet</span><span class="sxs-lookup"><span data-stu-id="78522-115">Testing the Cmdlet</span></span>](#Testing-the-Cmdlet)

## <a name="defining-the-cmdlet"></a><span data-ttu-id="78522-116">De Cmdlet definiëren</span><span class="sxs-lookup"><span data-stu-id="78522-116">Defining the Cmdlet</span></span>

<span data-ttu-id="78522-117">De eerste stap bij het maken van de cmdlet is altijd naamgeving van de cmdlet en de .NET-klasse die de cmdlet declareren.</span><span class="sxs-lookup"><span data-stu-id="78522-117">The first step in cmdlet creation is always naming the cmdlet and declaring the .NET class that implements the cmdlet.</span></span> <span data-ttu-id="78522-118">Omdat u een cmdlet als u wilt wijzigen van het systeem schrijft, moet deze dienovereenkomstig worden genoemd.</span><span class="sxs-lookup"><span data-stu-id="78522-118">Because you are writing a cmdlet to change the system, it should be named accordingly.</span></span> <span data-ttu-id="78522-119">Omdat deze cmdlet systeemprocessen stopt, wordt de term 'Stop', die is gedefinieerd door de [System.Management.Automation.Verbslifecycle](/dotnet/api/System.Management.Automation.VerbsLifeCycle) klasse, met het zelfstandig naamwoord 'Proc' om aan te geven van proces.</span><span class="sxs-lookup"><span data-stu-id="78522-119">Because this cmdlet stops system processes, it uses the verb "Stop", defined by the [System.Management.Automation.Verbslifecycle](/dotnet/api/System.Management.Automation.VerbsLifeCycle) class, with the noun "Proc" to indicate process.</span></span> <span data-ttu-id="78522-120">Zie voor meer informatie over goedgekeurde werkwoorden [namen van de term cmdlets](./approved-verbs-for-windows-powershell-commands.md).</span><span class="sxs-lookup"><span data-stu-id="78522-120">For more information about approved cmdlet verbs, see [Cmdlet Verb Names](./approved-verbs-for-windows-powershell-commands.md).</span></span>

<span data-ttu-id="78522-121">De volgende code wordt de klassedefinitie van deze cmdlet Stop-Proc.</span><span class="sxs-lookup"><span data-stu-id="78522-121">The following code is the class definition for this Stop-Proc cmdlet.</span></span>

```csharp
[Cmdlet(VerbsLifecycle.Stop, "proc",
        SupportsShouldProcess = true)]
public class StopProcCommand : Cmdlet
```

## <a name="defining-parameters-for-system-modification"></a><span data-ttu-id="78522-122">Parameters voor aanpassing van het systeem definiëren</span><span class="sxs-lookup"><span data-stu-id="78522-122">Defining Parameters for System Modification</span></span>

<span data-ttu-id="78522-123">De cmdlet moet parameters definiëren die ondersteuningssysteem wijzigingen en feedback van gebruikers.</span><span class="sxs-lookup"><span data-stu-id="78522-123">Your cmdlet needs to define parameters that support system modifications and user feedback.</span></span> <span data-ttu-id="78522-124">De cmdlet moet definiëren een `Name` parameter of een vergelijkbare zodat de cmdlet kunnen wijzigen van het systeem door een soort id.</span><span class="sxs-lookup"><span data-stu-id="78522-124">The cmdlet should define a `Name` parameter or equivalent so that the cmdlet will be able to modify the system by some sort of identifier.</span></span> <span data-ttu-id="78522-125">Bovendien de cmdlet moet definiëren de `Force` en `PassThru` parameters.</span><span class="sxs-lookup"><span data-stu-id="78522-125">In addition, the cmdlet should define the `Force` and `PassThru` parameters.</span></span> <span data-ttu-id="78522-126">Zie voor meer informatie over deze parameters [maken van een Cmdlet die Hiermee wijzigt u het systeem](./creating-a-cmdlet-that-modifies-the-system.md).</span><span class="sxs-lookup"><span data-stu-id="78522-126">For more information about these parameters, see [Creating a Cmdlet that Modifies the System](./creating-a-cmdlet-that-modifies-the-system.md).</span></span>

## <a name="defining-a-parameter-alias"></a><span data-ttu-id="78522-127">Een Parameteralias definiëren</span><span class="sxs-lookup"><span data-stu-id="78522-127">Defining a Parameter Alias</span></span>

<span data-ttu-id="78522-128">Een parameteralias is een alternatieve naam of een goed gedefinieerde 1- of 2 letter korte naam voor een cmdlet-parameter.</span><span class="sxs-lookup"><span data-stu-id="78522-128">A parameter alias can be an alternate name or a well-defined 1-letter or 2-letter short name for a cmdlet parameter.</span></span> <span data-ttu-id="78522-129">In beide gevallen is het doel van het gebruik van aliassen voor het vereenvoudigen van de vermelding van de gebruiker vanaf de opdrachtregel.</span><span class="sxs-lookup"><span data-stu-id="78522-129">In both cases, the goal of using aliases is to simplify user entry from the command line.</span></span> <span data-ttu-id="78522-130">Windows PowerShell ondersteunt aliassen via de [System.Management.Automation.Aliasattribute](/dotnet/api/System.Management.Automation.AliasAttribute) kenmerk, die gebruikmaakt van de syntaxis van de declaratie [Alias()].</span><span class="sxs-lookup"><span data-stu-id="78522-130">Windows PowerShell supports parameter aliases through the [System.Management.Automation.Aliasattribute](/dotnet/api/System.Management.Automation.AliasAttribute) attribute, which uses the declaration syntax [Alias()].</span></span>

<span data-ttu-id="78522-131">De volgende code toont hoe een alias is toegevoegd aan de `Name` parameter.</span><span class="sxs-lookup"><span data-stu-id="78522-131">The following code shows how an alias is added to the `Name` parameter.</span></span>

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

<span data-ttu-id="78522-132">Naast het gebruik van de [System.Management.Automation.Aliasattribute](/dotnet/api/System.Management.Automation.AliasAttribute) kenmerk, de Windows PowerShell-runtime voert gedeeltelijke namen matchen, zelfs als er geen aliassen zijn opgegeven.</span><span class="sxs-lookup"><span data-stu-id="78522-132">In addition to using the [System.Management.Automation.Aliasattribute](/dotnet/api/System.Management.Automation.AliasAttribute) attribute, the Windows PowerShell runtime performs partial name matching, even if no aliases are specified.</span></span> <span data-ttu-id="78522-133">Bijvoorbeeld, als de cmdlet heeft een `FileName` parameter en dat is de enige parameter die met begint `F`, de gebruiker kan invoeren `Filename`, `Filenam`, `File`, `Fi`, of `F` en nog steeds herkent de vermelding als de `FileName` parameter.</span><span class="sxs-lookup"><span data-stu-id="78522-133">For example, if your cmdlet has a `FileName` parameter and that is the only parameter that starts with `F`, the user could enter `Filename`, `Filenam`, `File`, `Fi`, or `F` and still recognize the entry as the `FileName` parameter.</span></span>

## <a name="creating-help-for-parameters"></a><span data-ttu-id="78522-134">Help voor Parameters maken</span><span class="sxs-lookup"><span data-stu-id="78522-134">Creating Help for Parameters</span></span>

<span data-ttu-id="78522-135">Windows PowerShell kunt u Help-informatie voor cmdlet-parameters maken.</span><span class="sxs-lookup"><span data-stu-id="78522-135">Windows PowerShell allows you to create Help for cmdlet parameters.</span></span> <span data-ttu-id="78522-136">Doe dit voor elke parameter die wordt gebruikt voor feedback op systeem wijzigen en de gebruiker.</span><span class="sxs-lookup"><span data-stu-id="78522-136">Do this for any parameter used for system modification and user feedback.</span></span> <span data-ttu-id="78522-137">Voor elke parameter voor de ondersteuning van Help-informatie, kunt u instellen de `HelpMessage` kenmerken van het sleutelwoord in de [System.Management.Automation.Parameterattribute](/dotnet/api/System.Management.Automation.ParameterAttribute) declaratie van het kenmerk.</span><span class="sxs-lookup"><span data-stu-id="78522-137">For each parameter to support Help, you can set the `HelpMessage` attribute keyword in the [System.Management.Automation.Parameterattribute](/dotnet/api/System.Management.Automation.ParameterAttribute) attribute declaration.</span></span> <span data-ttu-id="78522-138">Dit trefwoord definieert de tekst die moet worden weergegeven voor de gebruiker voor hulp bij het gebruik van de parameter.</span><span class="sxs-lookup"><span data-stu-id="78522-138">This keyword defines the text to display to the user for assistance in using the parameter.</span></span> <span data-ttu-id="78522-139">U kunt ook instellen de `HelpMessageBaseName` sleutelwoord voor het identificeren van de naam op van een resource moet worden gebruikt voor het bericht.</span><span class="sxs-lookup"><span data-stu-id="78522-139">You can also set the `HelpMessageBaseName` keyword to identify the base name of a resource to use for the message.</span></span> <span data-ttu-id="78522-140">Als u dit sleutelwoord instelt, moet u ook instellen de `HelpMessageResourceId` trefwoord om op te geven van de resource-id.</span><span class="sxs-lookup"><span data-stu-id="78522-140">If you set this keyword, you must also set the `HelpMessageResourceId` keyword to specify the resource identifier.</span></span>

<span data-ttu-id="78522-141">De volgende code uit deze cmdlet Stop-Proc definieert de `HelpMessage` kenmerk trefwoord voor de `Name` parameter.</span><span class="sxs-lookup"><span data-stu-id="78522-141">The following code from this Stop-Proc cmdlet defines the `HelpMessage` attribute keyword for the `Name` parameter.</span></span>

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

## <a name="overriding-an-input-processing-method"></a><span data-ttu-id="78522-142">Invoer verwerken methode te overschrijven</span><span class="sxs-lookup"><span data-stu-id="78522-142">Overriding an Input Processing Method</span></span>

<span data-ttu-id="78522-143">De cmdlet moet verwerken van methode invoer overschrijven, dit is meestal [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord).</span><span class="sxs-lookup"><span data-stu-id="78522-143">Your cmdlet must override an input processing method, most often this will be [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord).</span></span> <span data-ttu-id="78522-144">Bij het wijzigen van het systeem, de cmdlet moet aanroepen de [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) en [System.Management.Automation.Cmdlet.ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) methoden waarmee de gebruiker om feedback te geven voordat er een wijziging is aangebracht.</span><span class="sxs-lookup"><span data-stu-id="78522-144">When modifying the system, the cmdlet should call the [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) and [System.Management.Automation.Cmdlet.ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) methods to allow the user to provide feedback before a change is made.</span></span> <span data-ttu-id="78522-145">Zie voor meer informatie over deze methoden, [maken van een Cmdlet die Hiermee wijzigt u het systeem](./creating-a-cmdlet-that-modifies-the-system.md).</span><span class="sxs-lookup"><span data-stu-id="78522-145">For more information about these methods, see [Creating a Cmdlet that Modifies the System](./creating-a-cmdlet-that-modifies-the-system.md).</span></span>

## <a name="supporting-wildcard-expansion"></a><span data-ttu-id="78522-146">Ondersteunende jokertekens</span><span class="sxs-lookup"><span data-stu-id="78522-146">Supporting Wildcard Expansion</span></span>

<span data-ttu-id="78522-147">Als u wilt toestaan dat de selectie van meerdere objecten, uw cmdlet kunt gebruiken de [System.Management.Automation.Wildcardpattern](/dotnet/api/System.Management.Automation.WildcardPattern) en [System.Management.Automation.Wildcardoptions](/dotnet/api/System.Management.Automation.WildcardOptions) klassen voor jokertekens worden uitbreiding voor de parameter invoeren.</span><span class="sxs-lookup"><span data-stu-id="78522-147">To allow the selection of multiple objects, your cmdlet can use the [System.Management.Automation.Wildcardpattern](/dotnet/api/System.Management.Automation.WildcardPattern) and [System.Management.Automation.Wildcardoptions](/dotnet/api/System.Management.Automation.WildcardOptions) classes to provide wildcard expansion support for parameter input.</span></span> <span data-ttu-id="78522-148">Er zijn voorbeelden van jokertekenpatronen lsa \* \*.txt en [a-c]\*.</span><span class="sxs-lookup"><span data-stu-id="78522-148">Examples of wildcard patterns are lsa\*, \*.txt, and [a-c]\*.</span></span> <span data-ttu-id="78522-149">Gebruik de back-aanhalingsteken (') als een escape-teken als het patroon bevat een teken letterlijk moet worden gebruikt.</span><span class="sxs-lookup"><span data-stu-id="78522-149">Use the back-quote character (\`) as an escape character when the pattern contains a character that should be used literally.</span></span>

<span data-ttu-id="78522-150">Wildcard-uitbreidingen van bestands- en padnamen zijn voorbeelden van veelvoorkomende scenario's waarin de cmdlet ondersteuning voor het pad invoer toestaan kunt wanneer de selectie van meerdere objecten vereist is.</span><span class="sxs-lookup"><span data-stu-id="78522-150">Wildcard expansions of file and path names are examples of common scenarios where the cmdlet may want to allow support for path inputs when the selection of multiple objects is required.</span></span> <span data-ttu-id="78522-151">Gebruikelijk is in het bestandssysteem, waarbij een gebruiker wil zien van alle bestanden die zich bevinden in de huidige map.</span><span class="sxs-lookup"><span data-stu-id="78522-151">A common case is in the file system, where a user wants to see all files residing in the current folder.</span></span>

<span data-ttu-id="78522-152">U hoeft slechts zelden een aangepaste jokertekens patroon overeenkomende implementatie.</span><span class="sxs-lookup"><span data-stu-id="78522-152">You should need a customized wildcard pattern matching implementation only rarely.</span></span> <span data-ttu-id="78522-153">In dit geval moet de cmdlet ondersteuning voor de volledige POSIX-1003.2, 3,13 specificatie voor jokertekens of de volgende vereenvoudigde subset:</span><span class="sxs-lookup"><span data-stu-id="78522-153">In this case, your cmdlet should support either the full POSIX 1003.2, 3.13 specification for wildcard expansion or the following simplified subset:</span></span>

- <span data-ttu-id="78522-154">**Vraagteken (?).**</span><span class="sxs-lookup"><span data-stu-id="78522-154">**Question mark (?).**</span></span> <span data-ttu-id="78522-155">Komt overeen met een willekeurig teken op de opgegeven locatie.</span><span class="sxs-lookup"><span data-stu-id="78522-155">Matches any character at the specified location.</span></span>

- <span data-ttu-id="78522-156">**Sterretje (\*).**</span><span class="sxs-lookup"><span data-stu-id="78522-156">**Asterisk (\*).**</span></span> <span data-ttu-id="78522-157">Komt overeen met nul of meer tekens vanaf de opgegeven locatie.</span><span class="sxs-lookup"><span data-stu-id="78522-157">Matches zero or more characters starting at the specified location.</span></span>

- <span data-ttu-id="78522-158">**Open haakje sluiten ([]).**</span><span class="sxs-lookup"><span data-stu-id="78522-158">**Open bracket ([).**</span></span> <span data-ttu-id="78522-159">Introduceert een haakje-expressie voor het patroon die tekens of een bereik met tekens kan bevatten.</span><span class="sxs-lookup"><span data-stu-id="78522-159">Introduces a pattern bracket expression that can contain characters or a range of characters.</span></span> <span data-ttu-id="78522-160">Als een bereik is vereist, wordt een koppelteken (-) gebruikt om aan te geven van het bereik.</span><span class="sxs-lookup"><span data-stu-id="78522-160">If a range is required, a hyphen (-) is used to indicate the range.</span></span>

- <span data-ttu-id="78522-161">**Sluiten haak sluiten (]).**</span><span class="sxs-lookup"><span data-stu-id="78522-161">**Close bracket (]).**</span></span> <span data-ttu-id="78522-162">Een patroon haakje-expressie wordt beëindigd.</span><span class="sxs-lookup"><span data-stu-id="78522-162">Ends a pattern bracket expression.</span></span>

- <span data-ttu-id="78522-163">**Back-aanhalingsteken (') als escape-teken.**</span><span class="sxs-lookup"><span data-stu-id="78522-163">**Back-quote escape character (\`).**</span></span> <span data-ttu-id="78522-164">Geeft aan dat het volgende teken letterlijk moet worden genomen.</span><span class="sxs-lookup"><span data-stu-id="78522-164">Indicates that the next character should be taken literally.</span></span> <span data-ttu-id="78522-165">Let erop dat bij het opgeven van de back-aanhalingsteken vanaf de opdrachtregel (in plaats van via een programma opgeven), het back-offerte escape-teken moet worden twee keer opgegeven.</span><span class="sxs-lookup"><span data-stu-id="78522-165">Be aware that when specifying the back-quote character from the command line (as opposed to specifying it programmatically), the back-quote escape character must be specified twice.</span></span>

> [!NOTE]
> <span data-ttu-id="78522-166">Zie voor meer informatie over de jokertekenpatronen [ondersteunt jokertekens in de Cmdlet-Parameters](./supporting-wildcard-characters-in-cmdlet-parameters.md).</span><span class="sxs-lookup"><span data-stu-id="78522-166">For more information about wildcard patterns, see [Supporting Wildcards in Cmdlet Parameters](./supporting-wildcard-characters-in-cmdlet-parameters.md).</span></span>

<span data-ttu-id="78522-167">De volgende code laat zien hoe u jokertekens opties instellen en definiëren van het jokerteken-patroon gebruikt voor het oplossen van de `Name` parameter voor deze cmdlet.</span><span class="sxs-lookup"><span data-stu-id="78522-167">The following code shows how to set wildcard options and define the wildcard pattern used for resolving the `Name` parameter for this cmdlet.</span></span>

```csharp
WildcardOptions options = WildcardOptions.IgnoreCase |
                          WildcardOptions.Compiled;
WildcardPattern wildcard = new WildcardPattern(name,options);
```

<span data-ttu-id="78522-168">De volgende code toont hoe u kunt testen of de procesnaam overeenkomt met het patroon gedefinieerde jokertekens.</span><span class="sxs-lookup"><span data-stu-id="78522-168">The following code shows how to test whether the process name matches the defined wildcard pattern.</span></span> <span data-ttu-id="78522-169">U ziet dat in dit geval als de procesnaam komt niet overeen met het patroon, de cmdlet blijft op de naam van de volgende procedure.</span><span class="sxs-lookup"><span data-stu-id="78522-169">Notice that, in this case, if the process name does not match the pattern, the cmdlet continues on to get the next process name.</span></span>

```csharp
if (!wildcard.IsMatch(processName))
{
  continue;
}
```

## <a name="code-sample"></a><span data-ttu-id="78522-170">Voorbeeld van code</span><span class="sxs-lookup"><span data-stu-id="78522-170">Code Sample</span></span>

<span data-ttu-id="78522-171">Voor de volledige C# voorbeeldcode, Zie [StopProcessSample03 voorbeeld](./stopprocesssample03-sample.md).</span><span class="sxs-lookup"><span data-stu-id="78522-171">For the complete C# sample code, see [StopProcessSample03 Sample](./stopprocesssample03-sample.md).</span></span>

## <a name="define-object-types-and-formatting"></a><span data-ttu-id="78522-172">Definieer objecttypen en opmaak</span><span class="sxs-lookup"><span data-stu-id="78522-172">Define Object Types and Formatting</span></span>

<span data-ttu-id="78522-173">Windows PowerShell wordt informatie doorgegeven tussen cmdlets met behulp van .net-objecten.</span><span class="sxs-lookup"><span data-stu-id="78522-173">Windows PowerShell passes information between cmdlets using .Net objects.</span></span> <span data-ttu-id="78522-174">Als gevolg daarvan kan een cmdlet mogelijk nodig hebt voor het definiëren van een eigen type, of de cmdlet moet om uit te breiden van een bestaand type geleverd door een andere cmdlet.</span><span class="sxs-lookup"><span data-stu-id="78522-174">Consequently, a cmdlet may need to define its own type, or the cmdlet may need to extend an existing type provided by another cmdlet.</span></span> <span data-ttu-id="78522-175">Zie voor meer informatie over het definiëren van nieuwe typen of uitbreiden van bestaande typen [objecttypen uitbreiden en opmaak](https://msdn.microsoft.com/en-us/da976d91-a3d6-44e8-affa-466b1e2bd351).</span><span class="sxs-lookup"><span data-stu-id="78522-175">For more information about defining new types or extending existing types, see [Extending Object Types and Formatting](https://msdn.microsoft.com/en-us/da976d91-a3d6-44e8-affa-466b1e2bd351).</span></span>

## <a name="building-the-cmdlet"></a><span data-ttu-id="78522-176">Het bouwen van de Cmdlet</span><span class="sxs-lookup"><span data-stu-id="78522-176">Building the Cmdlet</span></span>

<span data-ttu-id="78522-177">Na de implementatie van een cmdlet, moet deze met Windows PowerShell worden geregistreerd via een Windows PowerShell-module.</span><span class="sxs-lookup"><span data-stu-id="78522-177">After implementing a cmdlet, it must be registered with Windows PowerShell through a Windows PowerShell snap-in.</span></span> <span data-ttu-id="78522-178">Zie voor meer informatie over het registreren van cmdlets [hoe u Cmdlets registreren, Providers en hosting van toepassingen](https://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c).</span><span class="sxs-lookup"><span data-stu-id="78522-178">For more information about registering cmdlets, see [How to Register Cmdlets, Providers, and Host Applications](https://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c).</span></span>

## <a name="testing-the-cmdlet"></a><span data-ttu-id="78522-179">Testen van de Cmdlet</span><span class="sxs-lookup"><span data-stu-id="78522-179">Testing the Cmdlet</span></span>

<span data-ttu-id="78522-180">Wanneer de cmdlet is geregistreerd met Windows PowerShell, kunt u deze testen door te voeren op de opdrachtregel.</span><span class="sxs-lookup"><span data-stu-id="78522-180">When your cmdlet has been registered with Windows PowerShell, you can test it by running it on the command line.</span></span> <span data-ttu-id="78522-181">We gaan de voorbeeld-cmdlet Stop-Proc testen.</span><span class="sxs-lookup"><span data-stu-id="78522-181">Let's test the sample Stop-Proc cmdlet.</span></span> <span data-ttu-id="78522-182">Zie voor meer informatie over het gebruik van cmdlets vanaf de opdrachtregel de [aan de slag met Windows PowerShell](/powershell/scripting/getting-started/getting-started-with-windows-powershell).</span><span class="sxs-lookup"><span data-stu-id="78522-182">For more information about using cmdlets from the command line, see the [Getting Started with Windows PowerShell](/powershell/scripting/getting-started/getting-started-with-windows-powershell).</span></span>

- <span data-ttu-id="78522-183">Start Windows PowerShell en Stop-procedure gebruiken om te stoppen van een proces met behulp van de procesnaam-alias voor de `Name` parameter.</span><span class="sxs-lookup"><span data-stu-id="78522-183">Start Windows PowerShell and use Stop-Proc to stop a process using the ProcessName alias for the `Name` parameter.</span></span>

    ```powershell
    PS> stop-proc -ProcessName notepad
    ```

<span data-ttu-id="78522-184">De volgende uitvoer wordt weergegeven.</span><span class="sxs-lookup"><span data-stu-id="78522-184">The following output appears.</span></span>

    ```
    Confirm
    Are you sure you want to perform this action?
    Performing operation "stop-proc" on Target "notepad (3496)".
    [Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "Y"): Y
    ```

- <span data-ttu-id="78522-185">Controleer de volgende vermelding op de opdrachtregel.</span><span class="sxs-lookup"><span data-stu-id="78522-185">Make the following entry on the command line.</span></span> <span data-ttu-id="78522-186">Omdat de parameter Name verplicht is, wordt u gevraagd voor het.</span><span class="sxs-lookup"><span data-stu-id="78522-186">Because the Name parameter is mandatory, you are prompted for it.</span></span> <span data-ttu-id="78522-187">Invoeren '!? "</span><span class="sxs-lookup"><span data-stu-id="78522-187">Entering "!?"</span></span> <span data-ttu-id="78522-188">Hiermee geeft u de help-tekst die is gekoppeld aan de parameter.</span><span class="sxs-lookup"><span data-stu-id="78522-188">brings up the help text associated with the parameter.</span></span>

    ```powershell
    PS> stop-proc
    ```

<span data-ttu-id="78522-189">De volgende uitvoer wordt weergegeven.</span><span class="sxs-lookup"><span data-stu-id="78522-189">The following output appears.</span></span>

    ```
    Cmdlet stop-proc at command pipeline position 1
    Supply values for the following parameters:
    (Type !? for Help.)
    Name[0]: !?
    The name of one or more processes to stop. Wildcards are permitted.
    Name[0]: notepad
    ```

- <span data-ttu-id="78522-190">Maak nu de volgende vermelding te beëindigen alle processen die overeenkomen met het patroon jokerteken ' \* Opmerking\*'.</span><span class="sxs-lookup"><span data-stu-id="78522-190">Now make the following entry to stop all processes that match the wildcard pattern "\*note\*".</span></span> <span data-ttu-id="78522-191">U wordt gevraagd voordat elk proces dat overeenkomt met het patroon wordt gestopt.</span><span class="sxs-lookup"><span data-stu-id="78522-191">You are prompted before stopping each process that matches the pattern.</span></span>

    ```powershell
    PS> stop-proc -Name *note*
    ```

<span data-ttu-id="78522-192">De volgende uitvoer wordt weergegeven.</span><span class="sxs-lookup"><span data-stu-id="78522-192">The following output appears.</span></span>

    ```
    Confirm
    Are you sure you want to perform this action?
    Performing operation "stop-proc" on Target "notepad (1112)".
    [Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "Y"): Y
    ```

<span data-ttu-id="78522-193">De volgende uitvoer wordt weergegeven.</span><span class="sxs-lookup"><span data-stu-id="78522-193">The following output appears.</span></span>

    ```
    Confirm
    Are you sure you want to perform this action?
    Performing operation "stop-proc" on Target "ONENOTEM (3712)".
    [Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "Y"): N
    ```

<span data-ttu-id="78522-194">De volgende uitvoer wordt weergegeven.</span><span class="sxs-lookup"><span data-stu-id="78522-194">The following output appears.</span></span>

    ```
    Confirm
    Are you sure you want to perform this action?
    Performing operation "stop-proc" on Target "ONENOTE (3592)".
    [Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "Y"): N
    ```

## <a name="see-also"></a><span data-ttu-id="78522-195">Zie ook</span><span class="sxs-lookup"><span data-stu-id="78522-195">See Also</span></span>

[<span data-ttu-id="78522-196">Maken van een Cmdlet die Hiermee wijzigt u het systeem</span><span class="sxs-lookup"><span data-stu-id="78522-196">Create a Cmdlet that Modifies the System</span></span>](./creating-a-cmdlet-that-modifies-the-system.md)

[<span data-ttu-id="78522-197">Over het maken van een Windows PowerShell-Cmdlet</span><span class="sxs-lookup"><span data-stu-id="78522-197">How to Create a Windows PowerShell Cmdlet</span></span>](https://msdn.microsoft.com/en-us/0d721742-c849-4d0d-964f-78ddd9cd258c)

[<span data-ttu-id="78522-198">Objecttypen uitbreiden en opmaak</span><span class="sxs-lookup"><span data-stu-id="78522-198">Extending Object Types and Formatting</span></span>](https://msdn.microsoft.com/en-us/da976d91-a3d6-44e8-affa-466b1e2bd351)

[<span data-ttu-id="78522-199">Over het registreren van Providers,-Cmdlets en -toepassingen hosten</span><span class="sxs-lookup"><span data-stu-id="78522-199">How to Register Cmdlets, Providers, and Host Applications</span></span>](https://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c)

[<span data-ttu-id="78522-200">Ondersteuning van jokertekens in de Cmdlet-Parameters</span><span class="sxs-lookup"><span data-stu-id="78522-200">Supporting Wildcards in Cmdlet Parameters</span></span>](./supporting-wildcard-characters-in-cmdlet-parameters.md)

[<span data-ttu-id="78522-201">Windows PowerShell SDK</span><span class="sxs-lookup"><span data-stu-id="78522-201">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)
