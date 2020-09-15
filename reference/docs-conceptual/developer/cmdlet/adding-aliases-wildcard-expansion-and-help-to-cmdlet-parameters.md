---
title: Aliassen, uitbrei ding van joker tekens en Help voor cmdlet-para meters toevoegen | Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: 244c50c73972c2760e0029c7fa4f4b5764b066da
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 08/05/2020
ms.locfileid: "87774963"
---
# <a name="adding-aliases-wildcard-expansion-and-help-to-cmdlet-parameters"></a><span data-ttu-id="f05ce-102">Aliassen, jokertekenuitbreiding en Help toevoegen aan cmdlet-parameters</span><span class="sxs-lookup"><span data-stu-id="f05ce-102">Adding Aliases, Wildcard Expansion, and Help to Cmdlet Parameters</span></span>

<span data-ttu-id="f05ce-103">In deze sectie wordt beschreven hoe u aliassen, uitbrei ding van joker tekens en Help-berichten toevoegt aan de para meters van de cmdlet stop-proc (beschreven in [een cmdlet maken die het systeem wijzigt](./creating-a-cmdlet-that-modifies-the-system.md)).</span><span class="sxs-lookup"><span data-stu-id="f05ce-103">This section describes how to add aliases, wildcard expansion, and Help messages to the parameters of the Stop-Proc cmdlet (described in [Creating a Cmdlet that Modifies the System](./creating-a-cmdlet-that-modifies-the-system.md)).</span></span>

<span data-ttu-id="f05ce-104">Deze Stop-proc-cmdlet probeert processen te stoppen die worden opgehaald met de cmdlet Get-proc (beschreven in [uw eerste cmdlet maken](./creating-a-cmdlet-without-parameters.md)).</span><span class="sxs-lookup"><span data-stu-id="f05ce-104">This Stop-Proc cmdlet attempts to stop processes that are retrieved using the Get-Proc cmdlet (described in [Creating Your First Cmdlet](./creating-a-cmdlet-without-parameters.md)).</span></span>

## <a name="defining-the-cmdlet"></a><span data-ttu-id="f05ce-105">De cmdlet definiëren</span><span class="sxs-lookup"><span data-stu-id="f05ce-105">Defining the Cmdlet</span></span>

<span data-ttu-id="f05ce-106">De eerste stap bij het maken van de cmdlet is altijd de naam van de cmdlet en het declareren van de .NET-klasse die de cmdlet implementeert.</span><span class="sxs-lookup"><span data-stu-id="f05ce-106">The first step in cmdlet creation is always naming the cmdlet and declaring the .NET class that implements the cmdlet.</span></span> <span data-ttu-id="f05ce-107">Omdat u een cmdlet schrijft om het systeem te wijzigen, moet dit dienovereenkomstig een naam hebben.</span><span class="sxs-lookup"><span data-stu-id="f05ce-107">Because you are writing a cmdlet to change the system, it should be named accordingly.</span></span> <span data-ttu-id="f05ce-108">Omdat met deze cmdlet systeem processen worden gestopt, wordt de term ' Stop ' gebruikt, die door de [System. Management. Automation. Verbslifecycle](/dotnet/api/System.Management.Automation.VerbsLifeCycle) -klasse is gedefinieerd, met het zelfstandig naam woord ' proc ' om het proces aan te geven.</span><span class="sxs-lookup"><span data-stu-id="f05ce-108">Because this cmdlet stops system processes, it uses the verb "Stop", defined by the [System.Management.Automation.Verbslifecycle](/dotnet/api/System.Management.Automation.VerbsLifeCycle) class, with the noun "Proc" to indicate process.</span></span> <span data-ttu-id="f05ce-109">Zie [cmdlet verb names](./approved-verbs-for-windows-powershell-commands.md)(Engelstalig) voor meer informatie over goedgekeurde cmdlet-termen.</span><span class="sxs-lookup"><span data-stu-id="f05ce-109">For more information about approved cmdlet verbs, see [Cmdlet Verb Names](./approved-verbs-for-windows-powershell-commands.md).</span></span>

<span data-ttu-id="f05ce-110">De volgende code is de klassedefinitie voor deze stop-proc-cmdlet.</span><span class="sxs-lookup"><span data-stu-id="f05ce-110">The following code is the class definition for this Stop-Proc cmdlet.</span></span>

```csharp
[Cmdlet(VerbsLifecycle.Stop, "proc",
        SupportsShouldProcess = true)]
public class StopProcCommand : Cmdlet
```

## <a name="defining-parameters-for-system-modification"></a><span data-ttu-id="f05ce-111">Para meters definiëren voor systeem wijziging</span><span class="sxs-lookup"><span data-stu-id="f05ce-111">Defining Parameters for System Modification</span></span>

<span data-ttu-id="f05ce-112">Uw cmdlet moet para meters definiëren die systeem wijzigingen en gebruikers feedback ondersteunen.</span><span class="sxs-lookup"><span data-stu-id="f05ce-112">Your cmdlet needs to define parameters that support system modifications and user feedback.</span></span> <span data-ttu-id="f05ce-113">Met de cmdlet wordt een `Name` para meter of gelijkwaardige waarde gedefinieerd, zodat de cmdlet het systeem kan wijzigen met een bepaalde sorteer-id.</span><span class="sxs-lookup"><span data-stu-id="f05ce-113">The cmdlet should define a `Name` parameter or equivalent so that the cmdlet will be able to modify the system by some sort of identifier.</span></span> <span data-ttu-id="f05ce-114">Daarnaast moet de cmdlet de `Force` `PassThru` para meters en opgeven.</span><span class="sxs-lookup"><span data-stu-id="f05ce-114">In addition, the cmdlet should define the `Force` and `PassThru` parameters.</span></span> <span data-ttu-id="f05ce-115">Zie [een cmdlet maken die het systeem wijzigt](./creating-a-cmdlet-that-modifies-the-system.md)voor meer informatie over deze para meters.</span><span class="sxs-lookup"><span data-stu-id="f05ce-115">For more information about these parameters, see [Creating a Cmdlet that Modifies the System](./creating-a-cmdlet-that-modifies-the-system.md).</span></span>

## <a name="defining-a-parameter-alias"></a><span data-ttu-id="f05ce-116">Een parameter alias definiëren</span><span class="sxs-lookup"><span data-stu-id="f05ce-116">Defining a Parameter Alias</span></span>

<span data-ttu-id="f05ce-117">Een parameter alias kan een alternatieve naam of een goed gedefinieerde korte naam van één of twee letters zijn voor een cmdlet-para meter.</span><span class="sxs-lookup"><span data-stu-id="f05ce-117">A parameter alias can be an alternate name or a well-defined 1-letter or 2-letter short name for a cmdlet parameter.</span></span> <span data-ttu-id="f05ce-118">In beide gevallen is het doel van het gebruik van aliassen om de gebruikers vermelding te vereenvoudigen vanaf de opdracht regel.</span><span class="sxs-lookup"><span data-stu-id="f05ce-118">In both cases, the goal of using aliases is to simplify user entry from the command line.</span></span> <span data-ttu-id="f05ce-119">Windows Power shell ondersteunt parameter aliassen via het kenmerk [System. Management. Automation. Aliasattribute](/dotnet/api/System.Management.Automation.AliasAttribute) , dat gebruikmaakt van de declaratie syntaxis [alias ()].</span><span class="sxs-lookup"><span data-stu-id="f05ce-119">Windows PowerShell supports parameter aliases through the [System.Management.Automation.Aliasattribute](/dotnet/api/System.Management.Automation.AliasAttribute) attribute, which uses the declaration syntax [Alias()].</span></span>

<span data-ttu-id="f05ce-120">De volgende code laat zien hoe een alias wordt toegevoegd aan de `Name` para meter.</span><span class="sxs-lookup"><span data-stu-id="f05ce-120">The following code shows how an alias is added to the `Name` parameter.</span></span>

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

<span data-ttu-id="f05ce-121">Naast het gebruik van het kenmerk [System. Management. Automation. Aliasattribute](/dotnet/api/System.Management.Automation.AliasAttribute) voert de Windows Power shell-runtime gedeeltelijke naam aanpassing uit, zelfs als er geen aliassen zijn opgegeven.</span><span class="sxs-lookup"><span data-stu-id="f05ce-121">In addition to using the [System.Management.Automation.Aliasattribute](/dotnet/api/System.Management.Automation.AliasAttribute) attribute, the Windows PowerShell runtime performs partial name matching, even if no aliases are specified.</span></span> <span data-ttu-id="f05ce-122">Als uw cmdlet bijvoorbeeld een para meter heeft `FileName` en de enige para meter is die begint met `F` , kan de gebruiker `Filename` `Filenam` `File` `Fi` `F` de vermelding als de para meter opgeven,,, of en nog steeds herkennen `FileName` .</span><span class="sxs-lookup"><span data-stu-id="f05ce-122">For example, if your cmdlet has a `FileName` parameter and that is the only parameter that starts with `F`, the user could enter `Filename`, `Filenam`, `File`, `Fi`, or `F` and still recognize the entry as the `FileName` parameter.</span></span>

## <a name="creating-help-for-parameters"></a><span data-ttu-id="f05ce-123">Help voor para meters maken</span><span class="sxs-lookup"><span data-stu-id="f05ce-123">Creating Help for Parameters</span></span>

<span data-ttu-id="f05ce-124">Met Windows Power shell kunt u Help maken voor cmdlet-para meters.</span><span class="sxs-lookup"><span data-stu-id="f05ce-124">Windows PowerShell allows you to create Help for cmdlet parameters.</span></span> <span data-ttu-id="f05ce-125">Doe dit voor alle para meters die worden gebruikt voor systeem wijzigingen en gebruikers feedback.</span><span class="sxs-lookup"><span data-stu-id="f05ce-125">Do this for any parameter used for system modification and user feedback.</span></span> <span data-ttu-id="f05ce-126">Voor elke para meter om hulp te ondersteunen, kunt u het `HelpMessage` sleutel woord kenmerk instellen in de kenmerk declaratie [System. Management. Automation. Parameterattribute](/dotnet/api/System.Management.Automation.ParameterAttribute) .</span><span class="sxs-lookup"><span data-stu-id="f05ce-126">For each parameter to support Help, you can set the `HelpMessage` attribute keyword in the [System.Management.Automation.Parameterattribute](/dotnet/api/System.Management.Automation.ParameterAttribute) attribute declaration.</span></span> <span data-ttu-id="f05ce-127">Dit sleutel woord definieert de tekst die voor de gebruiker moet worden weer gegeven voor hulp bij het gebruik van de para meter.</span><span class="sxs-lookup"><span data-stu-id="f05ce-127">This keyword defines the text to display to the user for assistance in using the parameter.</span></span> <span data-ttu-id="f05ce-128">U kunt ook het `HelpMessageBaseName` tref woord instellen om de basis naam te identificeren van een resource die moet worden gebruikt voor het bericht.</span><span class="sxs-lookup"><span data-stu-id="f05ce-128">You can also set the `HelpMessageBaseName` keyword to identify the base name of a resource to use for the message.</span></span> <span data-ttu-id="f05ce-129">Als u dit tref woord hebt ingesteld, moet u ook het `HelpMessageResourceId` tref woord instellen om de resource-id op te geven.</span><span class="sxs-lookup"><span data-stu-id="f05ce-129">If you set this keyword, you must also set the `HelpMessageResourceId` keyword to specify the resource identifier.</span></span>

<span data-ttu-id="f05ce-130">Met de volgende code uit deze stop-proc-cmdlet wordt het `HelpMessage` sleutel woord attribute voor de `Name` para meter gedefinieerd.</span><span class="sxs-lookup"><span data-stu-id="f05ce-130">The following code from this Stop-Proc cmdlet defines the `HelpMessage` attribute keyword for the `Name` parameter.</span></span>

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

## <a name="overriding-an-input-processing-method"></a><span data-ttu-id="f05ce-131">Een invoer verwerkings methode overschrijven</span><span class="sxs-lookup"><span data-stu-id="f05ce-131">Overriding an Input Processing Method</span></span>

<span data-ttu-id="f05ce-132">De cmdlet moet een invoer verwerkings methode overschrijven. Dit is meestal [System. Management. Automation. cmdlet. ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord).</span><span class="sxs-lookup"><span data-stu-id="f05ce-132">Your cmdlet must override an input processing method, most often this will be [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord).</span></span> <span data-ttu-id="f05ce-133">Bij het wijzigen van het systeem moet de cmdlet de methoden [System. Management. Automation. cmdlet. ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) en [System. Management. Automation. cmdlet. ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) gebruiken om de gebruiker feedback te geven voordat een wijziging wordt aangebracht.</span><span class="sxs-lookup"><span data-stu-id="f05ce-133">When modifying the system, the cmdlet should call the [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) and [System.Management.Automation.Cmdlet.ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) methods to allow the user to provide feedback before a change is made.</span></span> <span data-ttu-id="f05ce-134">Zie [een cmdlet maken die het systeem wijzigt](./creating-a-cmdlet-that-modifies-the-system.md)voor meer informatie over deze methoden.</span><span class="sxs-lookup"><span data-stu-id="f05ce-134">For more information about these methods, see [Creating a Cmdlet that Modifies the System](./creating-a-cmdlet-that-modifies-the-system.md).</span></span>

## <a name="supporting-wildcard-expansion"></a><span data-ttu-id="f05ce-135">Ondersteuning voor het uitbreiden van joker tekens</span><span class="sxs-lookup"><span data-stu-id="f05ce-135">Supporting Wildcard Expansion</span></span>

<span data-ttu-id="f05ce-136">Als u wilt toestaan dat meerdere objecten worden geselecteerd, kan uw cmdlet de klassen [System. Management. Automation. Wildcardpattern](/dotnet/api/System.Management.Automation.WildcardPattern) en [System. Management. Automation. Wildcardoptions](/dotnet/api/System.Management.Automation.WildcardOptions) gebruiken om ondersteuning voor joker tekens te bieden voor de invoer van para meters.</span><span class="sxs-lookup"><span data-stu-id="f05ce-136">To allow the selection of multiple objects, your cmdlet can use the [System.Management.Automation.Wildcardpattern](/dotnet/api/System.Management.Automation.WildcardPattern) and [System.Management.Automation.Wildcardoptions](/dotnet/api/System.Management.Automation.WildcardOptions) classes to provide wildcard expansion support for parameter input.</span></span> <span data-ttu-id="f05ce-137">Voor beelden van Joker teken patronen zijn LSA \*, \* . txt en [a-c] \* .</span><span class="sxs-lookup"><span data-stu-id="f05ce-137">Examples of wildcard patterns are lsa\*, \*.txt, and [a-c]\*.</span></span> <span data-ttu-id="f05ce-138">Gebruik het back-quote teken (') als escape-teken wanneer het patroon een teken bevat dat letterlijk moet worden gebruikt.</span><span class="sxs-lookup"><span data-stu-id="f05ce-138">Use the back-quote character (\`) as an escape character when the pattern contains a character that should be used literally.</span></span>

<span data-ttu-id="f05ce-139">Een Joker teken uitbreiding van bestands-en padnamen zijn voor beelden van veelvoorkomende scenario's waarbij de cmdlet mogelijk ondersteuning biedt voor invoer van paden wanneer de selectie van meerdere objecten is vereist.</span><span class="sxs-lookup"><span data-stu-id="f05ce-139">Wildcard expansions of file and path names are examples of common scenarios where the cmdlet may want to allow support for path inputs when the selection of multiple objects is required.</span></span> <span data-ttu-id="f05ce-140">Een veelvoorkomend geval is in het bestands systeem, waarbij een gebruiker alle bestanden in de huidige map wil weer geven.</span><span class="sxs-lookup"><span data-stu-id="f05ce-140">A common case is in the file system, where a user wants to see all files residing in the current folder.</span></span>

<span data-ttu-id="f05ce-141">U moet een aangepaste implementatie van Joker teken patronen die slechts zelden overeenkomen, hebben.</span><span class="sxs-lookup"><span data-stu-id="f05ce-141">You should need a customized wildcard pattern matching implementation only rarely.</span></span> <span data-ttu-id="f05ce-142">In dit geval moet uw cmdlet de volledige POSIX 1003,2, 3,13 specificatie voor de uitbrei ding van het Joker teken of de volgende vereenvoudigde subset ondersteunen:</span><span class="sxs-lookup"><span data-stu-id="f05ce-142">In this case, your cmdlet should support either the full POSIX 1003.2, 3.13 specification for wildcard expansion or the following simplified subset:</span></span>

- <span data-ttu-id="f05ce-143">**Vraag teken (?).**</span><span class="sxs-lookup"><span data-stu-id="f05ce-143">**Question mark (?).**</span></span> <span data-ttu-id="f05ce-144">Komt overeen met een teken op de opgegeven locatie.</span><span class="sxs-lookup"><span data-stu-id="f05ce-144">Matches any character at the specified location.</span></span>

- <span data-ttu-id="f05ce-145">**Asterisk ( \* ).**</span><span class="sxs-lookup"><span data-stu-id="f05ce-145">**Asterisk (\*).**</span></span> <span data-ttu-id="f05ce-146">Komt overeen met nul of meer tekens, te beginnen bij de opgegeven locatie.</span><span class="sxs-lookup"><span data-stu-id="f05ce-146">Matches zero or more characters starting at the specified location.</span></span>

- <span data-ttu-id="f05ce-147">**Haakje openen ([).**</span><span class="sxs-lookup"><span data-stu-id="f05ce-147">**Open bracket ([).**</span></span> <span data-ttu-id="f05ce-148">Introduceert een patroon rechte haak expressie die tekens of een reeks tekens kan bevatten.</span><span class="sxs-lookup"><span data-stu-id="f05ce-148">Introduces a pattern bracket expression that can contain characters or a range of characters.</span></span> <span data-ttu-id="f05ce-149">Als een bereik vereist is, wordt een koppel teken (-) gebruikt om het bereik aan te geven.</span><span class="sxs-lookup"><span data-stu-id="f05ce-149">If a range is required, a hyphen (-) is used to indicate the range.</span></span>

- <span data-ttu-id="f05ce-150">**Haakje sluiten (]).**</span><span class="sxs-lookup"><span data-stu-id="f05ce-150">**Close bracket (]).**</span></span> <span data-ttu-id="f05ce-151">Hiermee wordt een expressie voor een patroon haak afgesloten.</span><span class="sxs-lookup"><span data-stu-id="f05ce-151">Ends a pattern bracket expression.</span></span>

- <span data-ttu-id="f05ce-152">**Escape teken voor back-quote (').**</span><span class="sxs-lookup"><span data-stu-id="f05ce-152">**Back-quote escape character (\`).**</span></span> <span data-ttu-id="f05ce-153">Geeft aan dat het volgende teken letterlijk moet worden genomen.</span><span class="sxs-lookup"><span data-stu-id="f05ce-153">Indicates that the next character should be taken literally.</span></span> <span data-ttu-id="f05ce-154">Houd er rekening mee dat wanneer u het nummer van de back-quote opgeeft vanaf de opdracht regel (in plaats van het programma op te geven), het escape-teken voor de back-quote twee keer moet worden opgegeven.</span><span class="sxs-lookup"><span data-stu-id="f05ce-154">Be aware that when specifying the back-quote character from the command line (as opposed to specifying it programmatically), the back-quote escape character must be specified twice.</span></span>

> [!NOTE]
> <span data-ttu-id="f05ce-155">Zie [ondersteuning voor joker tekens in cmdlet-para meters](./supporting-wildcard-characters-in-cmdlet-parameters.md)voor meer informatie over Joker teken patronen.</span><span class="sxs-lookup"><span data-stu-id="f05ce-155">For more information about wildcard patterns, see [Supporting Wildcards in Cmdlet Parameters](./supporting-wildcard-characters-in-cmdlet-parameters.md).</span></span>

<span data-ttu-id="f05ce-156">De volgende code laat zien hoe u opties voor joker tekens instelt en het Joker teken definieert dat wordt gebruikt voor het omzetten van de `Name` para meter voor deze cmdlet.</span><span class="sxs-lookup"><span data-stu-id="f05ce-156">The following code shows how to set wildcard options and define the wildcard pattern used for resolving the `Name` parameter for this cmdlet.</span></span>

```csharp
WildcardOptions options = WildcardOptions.IgnoreCase |
                          WildcardOptions.Compiled;
WildcardPattern wildcard = new WildcardPattern(name,options);
```

<span data-ttu-id="f05ce-157">De volgende code laat zien hoe u kunt testen of de proces naam overeenkomt met het gedefinieerde Joker teken patroon.</span><span class="sxs-lookup"><span data-stu-id="f05ce-157">The following code shows how to test whether the process name matches the defined wildcard pattern.</span></span> <span data-ttu-id="f05ce-158">In dit geval, als de proces naam niet overeenkomt met het patroon, blijft de cmdlet de volgende proces naam ophalen.</span><span class="sxs-lookup"><span data-stu-id="f05ce-158">Notice that, in this case, if the process name does not match the pattern, the cmdlet continues on to get the next process name.</span></span>

```csharp
if (!wildcard.IsMatch(processName))
{
  continue;
}
```

## <a name="code-sample"></a><span data-ttu-id="f05ce-159">Code voorbeeld</span><span class="sxs-lookup"><span data-stu-id="f05ce-159">Code Sample</span></span>

<span data-ttu-id="f05ce-160">Zie StopProcessSample03-voor [beeld](./stopprocesssample03-sample.md)voor de volledige C#-voorbeeld code.</span><span class="sxs-lookup"><span data-stu-id="f05ce-160">For the complete C# sample code, see [StopProcessSample03 Sample](./stopprocesssample03-sample.md).</span></span>

## <a name="define-object-types-and-formatting"></a><span data-ttu-id="f05ce-161">Object typen en-opmaak definiëren</span><span class="sxs-lookup"><span data-stu-id="f05ce-161">Define Object Types and Formatting</span></span>

<span data-ttu-id="f05ce-162">Windows Power shell geeft informatie door over cmdlets met behulp van .net-objecten.</span><span class="sxs-lookup"><span data-stu-id="f05ce-162">Windows PowerShell passes information between cmdlets using .Net objects.</span></span> <span data-ttu-id="f05ce-163">Daarom moet een cmdlet een eigen type kunnen definiëren, of moet de cmdlet een bestaand type uitbreiden dat door een andere cmdlet wordt verschaft.</span><span class="sxs-lookup"><span data-stu-id="f05ce-163">Consequently, a cmdlet may need to define its own type, or the cmdlet may need to extend an existing type provided by another cmdlet.</span></span> <span data-ttu-id="f05ce-164">Zie [object typen en-opmaak uitbreiden](/previous-versions//ms714665(v=vs.85))voor meer informatie over het definiëren van nieuwe typen of het uitbreiden van bestaande typen.</span><span class="sxs-lookup"><span data-stu-id="f05ce-164">For more information about defining new types or extending existing types, see [Extending Object Types and Formatting](/previous-versions//ms714665(v=vs.85)).</span></span>

## <a name="building-the-cmdlet"></a><span data-ttu-id="f05ce-165">De cmdlet bouwen</span><span class="sxs-lookup"><span data-stu-id="f05ce-165">Building the Cmdlet</span></span>

<span data-ttu-id="f05ce-166">Na de implementatie van een cmdlet moet deze met Windows Power shell zijn geregistreerd via een Windows Power shell-module.</span><span class="sxs-lookup"><span data-stu-id="f05ce-166">After implementing a cmdlet, it must be registered with Windows PowerShell through a Windows PowerShell snap-in.</span></span> <span data-ttu-id="f05ce-167">Zie [cmdlets, providers en hosttoepassingen registreren](/previous-versions//ms714644(v=vs.85))voor meer informatie over het registreren van cmdlets.</span><span class="sxs-lookup"><span data-stu-id="f05ce-167">For more information about registering cmdlets, see [How to Register Cmdlets, Providers, and Host Applications](/previous-versions//ms714644(v=vs.85)).</span></span>

## <a name="testing-the-cmdlet"></a><span data-ttu-id="f05ce-168">De cmdlet testen</span><span class="sxs-lookup"><span data-stu-id="f05ce-168">Testing the Cmdlet</span></span>

<span data-ttu-id="f05ce-169">Als uw cmdlet is geregistreerd bij Windows Power shell, kunt u deze testen door deze uit te voeren op de opdracht regel.</span><span class="sxs-lookup"><span data-stu-id="f05ce-169">When your cmdlet has been registered with Windows PowerShell, you can test it by running it on the command line.</span></span> <span data-ttu-id="f05ce-170">We gaan de voor beeld van de cmdlet stop-proc testen.</span><span class="sxs-lookup"><span data-stu-id="f05ce-170">Let's test the sample Stop-Proc cmdlet.</span></span> <span data-ttu-id="f05ce-171">Zie aan de slag [met Windows Power shell](/powershell/scripting/getting-started/getting-started-with-windows-powershell)voor meer informatie over het gebruik van cmdlets vanaf de opdracht regel.</span><span class="sxs-lookup"><span data-stu-id="f05ce-171">For more information about using cmdlets from the command line, see the [Getting Started with Windows PowerShell](/powershell/scripting/getting-started/getting-started-with-windows-powershell).</span></span>

- <span data-ttu-id="f05ce-172">Start Windows Power shell en gebruik stop-proc om een proces te stoppen met de alias van de procesnaam voor de `Name` para meter.</span><span class="sxs-lookup"><span data-stu-id="f05ce-172">Start Windows PowerShell and use Stop-Proc to stop a process using the ProcessName alias for the `Name` parameter.</span></span>

    ```powershell
    PS> stop-proc -ProcessName notepad
    ```

    <span data-ttu-id="f05ce-173">De volgende uitvoer wordt weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="f05ce-173">The following output appears.</span></span>

    ```
    Confirm
    Are you sure you want to perform this action?
    Performing operation "stop-proc" on Target "notepad (3496)".
    [Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "Y"): Y
    ```

- <span data-ttu-id="f05ce-174">Maak de volgende vermelding op de opdracht regel.</span><span class="sxs-lookup"><span data-stu-id="f05ce-174">Make the following entry on the command line.</span></span> <span data-ttu-id="f05ce-175">Omdat de para meter name verplicht is, wordt u gevraagd.</span><span class="sxs-lookup"><span data-stu-id="f05ce-175">Because the Name parameter is mandatory, you are prompted for it.</span></span> <span data-ttu-id="f05ce-176">Invoeren van "!?"</span><span class="sxs-lookup"><span data-stu-id="f05ce-176">Entering "!?"</span></span> <span data-ttu-id="f05ce-177">Hiermee wordt de Help-tekst voor de para meter geopend.</span><span class="sxs-lookup"><span data-stu-id="f05ce-177">brings up the help text associated with the parameter.</span></span>

    ```powershell
    PS> stop-proc
    ```

    <span data-ttu-id="f05ce-178">De volgende uitvoer wordt weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="f05ce-178">The following output appears.</span></span>

    ```
    Cmdlet stop-proc at command pipeline position 1
    Supply values for the following parameters:
    (Type !? for Help.)
    Name[0]: !?
    The name of one or more processes to stop. Wildcards are permitted.
    Name[0]: notepad
    ```

- <span data-ttu-id="f05ce-179">Maak nu de volgende vermelding om alle processen te stoppen die overeenkomen met het Joker teken ' \* Note \* '.</span><span class="sxs-lookup"><span data-stu-id="f05ce-179">Now make the following entry to stop all processes that match the wildcard pattern "\*note\*".</span></span> <span data-ttu-id="f05ce-180">U wordt gevraagd om elk proces dat overeenkomt met het patroon te stoppen.</span><span class="sxs-lookup"><span data-stu-id="f05ce-180">You are prompted before stopping each process that matches the pattern.</span></span>

    ```powershell
    PS> stop-proc -Name *note*
    ```

    <span data-ttu-id="f05ce-181">De volgende uitvoer wordt weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="f05ce-181">The following output appears.</span></span>

    ```
    Confirm
    Are you sure you want to perform this action?
    Performing operation "stop-proc" on Target "notepad (1112)".
    [Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "Y"): Y
    ```

    <span data-ttu-id="f05ce-182">De volgende uitvoer wordt weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="f05ce-182">The following output appears.</span></span>

    ```
    Confirm
    Are you sure you want to perform this action?
    Performing operation "stop-proc" on Target "ONENOTEM (3712)".
    [Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "Y"): N
    ```

    <span data-ttu-id="f05ce-183">De volgende uitvoer wordt weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="f05ce-183">The following output appears.</span></span>

    ```
    Confirm
    Are you sure you want to perform this action?
    Performing operation "stop-proc" on Target "ONENOTE (3592)".
    [Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "Y"): N
    ```

## <a name="see-also"></a><span data-ttu-id="f05ce-184">Zie ook</span><span class="sxs-lookup"><span data-stu-id="f05ce-184">See Also</span></span>

[<span data-ttu-id="f05ce-185">Een cmdlet maken die het systeem wijzigt</span><span class="sxs-lookup"><span data-stu-id="f05ce-185">Create a Cmdlet that Modifies the System</span></span>](./creating-a-cmdlet-that-modifies-the-system.md)

[<span data-ttu-id="f05ce-186">Een Windows Power shell-cmdlet maken</span><span class="sxs-lookup"><span data-stu-id="f05ce-186">How to Create a Windows PowerShell Cmdlet</span></span>](/powershell/scripting/developer/cmdlet/writing-a-windows-powershell-cmdlet)

<span data-ttu-id="f05ce-187">[Object typen en-opmaak uitbreiden](/previous-versions//ms714665(v=vs.85))</span><span class="sxs-lookup"><span data-stu-id="f05ce-187">[Extending Object Types and Formatting](/previous-versions//ms714665(v=vs.85))</span></span>

<span data-ttu-id="f05ce-188">[Cmdlets, providers en hosttoepassingen registreren](/previous-versions//ms714644(v=vs.85))</span><span class="sxs-lookup"><span data-stu-id="f05ce-188">[How to Register Cmdlets, Providers, and Host Applications](/previous-versions//ms714644(v=vs.85))</span></span>

[<span data-ttu-id="f05ce-189">Ondersteuning voor joker tekens in cmdlet-para meters</span><span class="sxs-lookup"><span data-stu-id="f05ce-189">Supporting Wildcards in Cmdlet Parameters</span></span>](./supporting-wildcard-characters-in-cmdlet-parameters.md)

[<span data-ttu-id="f05ce-190">Windows PowerShell SDK</span><span class="sxs-lookup"><span data-stu-id="f05ce-190">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)
