---
title: Het maken van een Cmdlet zonder Parameters | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- cmdlets [PowerShell Programmers Guide], creating
- cmdlets [PowerShell Programmers Guide], basic cmdlet
ms.assetid: 54236ef3-82db-45f8-9114-1ecb7ff65d3e
caps.latest.revision: 8
ms.openlocfilehash: c380b28570c955de6f41152fd617f5c1b0f9e4bd
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62068331"
---
# <a name="creating-a-cmdlet-without-parameters"></a><span data-ttu-id="c9f0e-102">Een cmdlet maken zonder parameters</span><span class="sxs-lookup"><span data-stu-id="c9f0e-102">Creating a Cmdlet without Parameters</span></span>

<span data-ttu-id="c9f0e-103">In deze sectie wordt beschreven hoe u een cmdlet die wordt informatie opgehaald uit de lokale computer zonder het gebruik van parameters en vervolgens schrijft de informatie in de pijplijn te maken.</span><span class="sxs-lookup"><span data-stu-id="c9f0e-103">This section describes how to create a cmdlet that retrieves information from the local computer without the use of parameters, and then writes the information to the pipeline.</span></span> <span data-ttu-id="c9f0e-104">De cmdlet die hier worden beschreven, is een cmdlet Get-Proc die haalt informatie op over de processen van de lokale computer en vervolgens informatie wordt weergegeven op de opdrachtregel.</span><span class="sxs-lookup"><span data-stu-id="c9f0e-104">The cmdlet described here is a Get-Proc cmdlet that retrieves information about the processes of the local computer, and then displays that information at the command line.</span></span>

<span data-ttu-id="c9f0e-105">Onderwerpen in deze sectie bevatten het volgende:</span><span class="sxs-lookup"><span data-stu-id="c9f0e-105">Topics in this section include the following:</span></span>

- [<span data-ttu-id="c9f0e-106">Naamgeving van de Cmdlet</span><span class="sxs-lookup"><span data-stu-id="c9f0e-106">Naming the Cmdlet</span></span>](#Naming-the-Cmdlet)

- [<span data-ttu-id="c9f0e-107">De Cmdlet-klasse definiëren</span><span class="sxs-lookup"><span data-stu-id="c9f0e-107">Defining the Cmdlet Class</span></span>](#Defining-the-Cmdlet-Class)

- [<span data-ttu-id="c9f0e-108">Invoer verwerken methode te overschrijven</span><span class="sxs-lookup"><span data-stu-id="c9f0e-108">Overriding an Input Processing Method</span></span>](#Overriding-an-Input-Processing-Method)

- [<span data-ttu-id="c9f0e-109">Voorbeeld van code</span><span class="sxs-lookup"><span data-stu-id="c9f0e-109">Code Sample</span></span>](#Code-Sample)

- [<span data-ttu-id="c9f0e-110">Objecttype definiëren en opmaak</span><span class="sxs-lookup"><span data-stu-id="c9f0e-110">Defining Object Types and Formatting</span></span>](#Defining-Object-Types-and-Formatting)

- [<span data-ttu-id="c9f0e-111">Het bouwen van de Cmdlet</span><span class="sxs-lookup"><span data-stu-id="c9f0e-111">Building the Cmdlet</span></span>](#Building-the-Cmdlet)

- [<span data-ttu-id="c9f0e-112">Testen van de Cmdlet</span><span class="sxs-lookup"><span data-stu-id="c9f0e-112">Testing the Cmdlet</span></span>](#Testing-the-Cmdlet)

> [!NOTE]
> <span data-ttu-id="c9f0e-113">Let erop dat bij het schrijven van cmdlets, de Windows PowerShell®-verwijzingsassembly's worden gedownload naar schijf (standaard op C:\Program Files\Reference Assemblies\Microsoft\WindowsPowerShell\v1.0). Ze zijn niet geïnstalleerd in de Global Assembly Cache (GAC).</span><span class="sxs-lookup"><span data-stu-id="c9f0e-113">Be aware that when writing cmdlets, the Windows PowerShell® reference assemblies are downloaded onto disk (by default at C:\Program Files\Reference Assemblies\Microsoft\WindowsPowerShell\v1.0).They are not installed in the Global Assembly Cache (GAC).</span></span>

## <a name="naming-the-cmdlet"></a><span data-ttu-id="c9f0e-114">Naamgeving van de Cmdlet</span><span class="sxs-lookup"><span data-stu-id="c9f0e-114">Naming the Cmdlet</span></span>

<span data-ttu-id="c9f0e-115">De naam van een cmdlet bestaat uit een term die geeft aan dat de actie van de cmdlet wordt en een zelfstandig naamwoord die aangeeft van de items die de cmdlet reageert.</span><span class="sxs-lookup"><span data-stu-id="c9f0e-115">A cmdlet name consists of a verb that indicates the action the cmdlet takes and a noun that indicates the items that the cmdlet acts upon.</span></span> <span data-ttu-id="c9f0e-116">Omdat deze voorbeeld-cmdlet Get-Proc proces objecten worden opgehaald, wordt de term 'Ophalen', gedefinieerd door de [System.Management.Automation.Verbscommon](/dotnet/api/System.Management.Automation.VerbsCommon) inventarisatie en het zelfstandig naamwoord 'Proc' om aan te geven dat de cmdlet op proces-items werkt.</span><span class="sxs-lookup"><span data-stu-id="c9f0e-116">Because this sample Get-Proc cmdlet retrieves process objects, it uses the verb "Get", defined by the [System.Management.Automation.Verbscommon](/dotnet/api/System.Management.Automation.VerbsCommon) enumeration, and the noun "Proc" to indicate that the cmdlet works on process items.</span></span>

<span data-ttu-id="c9f0e-117">Bij het benoemen van cmdlets gebruik niet een van de volgende tekens bevatten: #, () {} [] & - / \ $;: ' ' <> &#124; ?</span><span class="sxs-lookup"><span data-stu-id="c9f0e-117">When naming cmdlets, do not use any of the following characters: # , () {} [] & - /\ $ ; : " '<> &#124; ?</span></span> <span data-ttu-id="c9f0e-118">@ \` .</span><span class="sxs-lookup"><span data-stu-id="c9f0e-118">@ \` .</span></span>

### <a name="choosing-a-noun"></a><span data-ttu-id="c9f0e-119">Een zelfstandig naamwoord kiezen</span><span class="sxs-lookup"><span data-stu-id="c9f0e-119">Choosing a Noun</span></span>

<span data-ttu-id="c9f0e-120">Een zelfstandig naamwoord die specifiek is, moet u kiezen.</span><span class="sxs-lookup"><span data-stu-id="c9f0e-120">You should choose a noun that is specific.</span></span> <span data-ttu-id="c9f0e-121">Het is raadzaam om te gebruiken van een enkelvoudige zelfstandig naamwoord voorafgegaan door een verkorte versie van de naam van het product.</span><span class="sxs-lookup"><span data-stu-id="c9f0e-121">It is best to use a singular noun prefixed with a shortened version of the product name.</span></span> <span data-ttu-id="c9f0e-122">De cmdlet-naam van een voorbeeld van dit type is '`Get-SQLServer`'.</span><span class="sxs-lookup"><span data-stu-id="c9f0e-122">An example cmdlet name of this type is "`Get-SQLServer`".</span></span>

### <a name="choosing-a-verb"></a><span data-ttu-id="c9f0e-123">Een term kiezen</span><span class="sxs-lookup"><span data-stu-id="c9f0e-123">Choosing a Verb</span></span>

<span data-ttu-id="c9f0e-124">U moet een term uit de set van goedgekeurde cmdlet term namen gebruiken.</span><span class="sxs-lookup"><span data-stu-id="c9f0e-124">You should use a verb from the set of approved cmdlet verb names.</span></span> <span data-ttu-id="c9f0e-125">Zie voor meer informatie over de goedgekeurde werkwoorden [namen van de term cmdlets](./approved-verbs-for-windows-powershell-commands.md).</span><span class="sxs-lookup"><span data-stu-id="c9f0e-125">For more information about the approved cmdlet verbs, see [Cmdlet Verb Names](./approved-verbs-for-windows-powershell-commands.md).</span></span>

## <a name="defining-the-cmdlet-class"></a><span data-ttu-id="c9f0e-126">De Cmdlet-klasse definiëren</span><span class="sxs-lookup"><span data-stu-id="c9f0e-126">Defining the Cmdlet Class</span></span>

<span data-ttu-id="c9f0e-127">Nadat u de naam van een cmdlet hebt gekozen, definieert u een .NET-klasse voor het implementeren van de cmdlet.</span><span class="sxs-lookup"><span data-stu-id="c9f0e-127">Once you have chosen a cmdlet name, define a .NET class to implement the cmdlet.</span></span> <span data-ttu-id="c9f0e-128">Hier volgt de definitie van de klasse voor dit voorbeeld-cmdlet Get-Proc:</span><span class="sxs-lookup"><span data-stu-id="c9f0e-128">Here is the class definition for this sample Get-Proc cmdlet:</span></span>

```csharp
[Cmdlet(VerbsCommon.Get, "Proc")]
  public class GetProcCommand : Cmdlet
```

```vb
<Cmdlet(VerbsCommon.Get, "Proc")> _
Public Class GetProcCommand
    Inherits Cmdlet
```

<span data-ttu-id="c9f0e-129">U ziet dat voor de klassendefinitie van de de [System.Management.Automation.CmdletAttribute](/dotnet/api/System.Management.Automation.CmdletAttribute) kenmerk met de syntaxis van de `[Cmdlet(verb, noun, ...)]`, wordt gebruikt voor het identificeren van deze klasse als een cmdlet.</span><span class="sxs-lookup"><span data-stu-id="c9f0e-129">Notice that previous to the class definition, the [System.Management.Automation.CmdletAttribute](/dotnet/api/System.Management.Automation.CmdletAttribute) attribute, with the syntax `[Cmdlet(verb, noun, ...)]`, is used to identify this class as a cmdlet.</span></span> <span data-ttu-id="c9f0e-130">Dit is de enige vereiste kenmerk voor alle cmdlets en hierdoor kan de Windows PowerShell-runtime ze correct aanroept.</span><span class="sxs-lookup"><span data-stu-id="c9f0e-130">This is the only required attribute for all cmdlets, and it allows the Windows PowerShell runtime to call them correctly.</span></span> <span data-ttu-id="c9f0e-131">U kunt instellen dat kenmerk trefwoorden voor de klasse verder declareren indien nodig.</span><span class="sxs-lookup"><span data-stu-id="c9f0e-131">You can set attribute keywords to further declare the class if necessary.</span></span> <span data-ttu-id="c9f0e-132">Let erop dat de kenmerkdeclaratie voor onze GetProcCommand voorbeeldklasse alleen het zelfstandig naamwoord en werkwoord namen voor de cmdlet Get-Proc declareert.</span><span class="sxs-lookup"><span data-stu-id="c9f0e-132">Be aware that the attribute declaration for our sample GetProcCommand class declares only the noun and verb names for the Get-Proc cmdlet.</span></span>

> [!NOTE]
> <span data-ttu-id="c9f0e-133">Voor alle Windows PowerShell-klassen in kenmerk overeenkomen de trefwoorden die u kunt instellen met eigenschappen van de kenmerkklasse.</span><span class="sxs-lookup"><span data-stu-id="c9f0e-133">For all Windows PowerShell attribute classes, the keywords that you can set correspond to properties of the attribute class.</span></span>

<span data-ttu-id="c9f0e-134">Naam van de klasse van de cmdlet, is het raadzaam in overeenstemming met de cmdletnaam van de in de naam van de klasse.</span><span class="sxs-lookup"><span data-stu-id="c9f0e-134">When naming the class of the cmdlet, it is a good practice to reflect the cmdlet name in the class name.</span></span> <span data-ttu-id="c9f0e-135">Om dit te doen, gebruikt u de indeling "VerbNounCommand" en 'Bewerking' en "Zelfstandig naamwoord" vervangen door het werkwoord en een zelfstandig naamwoord gebruikt in de cmdletnaam.</span><span class="sxs-lookup"><span data-stu-id="c9f0e-135">To do this, use the form "VerbNounCommand" and replace "Verb" and "Noun" with the verb and noun used in the cmdlet name.</span></span> <span data-ttu-id="c9f0e-136">Zoals wordt weergegeven in de vorige klassedefinitie, de voorbeeld-cmdlet Get-Proc definieert een klasse genaamd GetProcCommand, die is afgeleid van de [System.Management.Automation.Cmdlet](/dotnet/api/System.Management.Automation.Cmdlet) basisklasse.</span><span class="sxs-lookup"><span data-stu-id="c9f0e-136">As is shown in the previous class definition, the sample Get-Proc cmdlet defines a class called GetProcCommand, which derives from the [System.Management.Automation.Cmdlet](/dotnet/api/System.Management.Automation.Cmdlet) base class.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="c9f0e-137">Als u wilt voor het definiëren van een cmdlet die rechtstreeks toegang heeft tot de Windows PowerShell-runtime, uw .NET-klasse moet zijn afgeleid van de [System.Management.Automation.PSCmdlet](/dotnet/api/System.Management.Automation.PSCmdlet) basisklasse.</span><span class="sxs-lookup"><span data-stu-id="c9f0e-137">If you want to define a cmdlet that accesses the Windows PowerShell runtime directly, your .NET class should derive from the [System.Management.Automation.PSCmdlet](/dotnet/api/System.Management.Automation.PSCmdlet) base class.</span></span> <span data-ttu-id="c9f0e-138">Zie voor meer informatie over deze klasse [het maken van een Cmdlet die parametersets definieert](./adding-parameter-sets-to-a-cmdlet.md).</span><span class="sxs-lookup"><span data-stu-id="c9f0e-138">For more information about this class, see [Creating a Cmdlet that Defines Parameter Sets](./adding-parameter-sets-to-a-cmdlet.md).</span></span>

> [!NOTE]
> <span data-ttu-id="c9f0e-139">De klasse voor een cmdlet moet expliciet gemarkeerd als openbaar.</span><span class="sxs-lookup"><span data-stu-id="c9f0e-139">The class for a cmdlet must be explicitly marked as public.</span></span> <span data-ttu-id="c9f0e-140">Klassen die niet zijn gemarkeerd als openbare standaard ingesteld op interne en zal niet worden gevonden door de Windows PowerShell-runtime.</span><span class="sxs-lookup"><span data-stu-id="c9f0e-140">Classes that are not marked as public will default to internal and will not be found by the Windows PowerShell runtime.</span></span>

<span data-ttu-id="c9f0e-141">Windows PowerShell gebruikt de [Microsoft.PowerShell.Commands](/dotnet/api/Microsoft.PowerShell.Commands) naamruimte voor de cmdlet-klassen.</span><span class="sxs-lookup"><span data-stu-id="c9f0e-141">Windows PowerShell uses the [Microsoft.PowerShell.Commands](/dotnet/api/Microsoft.PowerShell.Commands) namespace for its cmdlet classes.</span></span> <span data-ttu-id="c9f0e-142">Het verdient aanbeveling uw cmdlet-klassen in een naamruimte opdrachten van uw API-naamruimte, bijvoorbeeld xxx.PS.Commands plaatsen.</span><span class="sxs-lookup"><span data-stu-id="c9f0e-142">It is recommended to place your cmdlet classes in a Commands namespace of your API namespace, for example, xxx.PS.Commands.</span></span>

## <a name="overriding-an-input-processing-method"></a><span data-ttu-id="c9f0e-143">Invoer verwerken methode te overschrijven</span><span class="sxs-lookup"><span data-stu-id="c9f0e-143">Overriding an Input Processing Method</span></span>

<span data-ttu-id="c9f0e-144">De [System.Management.Automation.Cmdlet](/dotnet/api/System.Management.Automation.Cmdlet) klasse biedt drie verwerkingsmethoden van de belangrijkste invoer, ten minste een van die de cmdlet moet overschrijven.</span><span class="sxs-lookup"><span data-stu-id="c9f0e-144">The [System.Management.Automation.Cmdlet](/dotnet/api/System.Management.Automation.Cmdlet) class provides three main input processing methods, at least one of which your cmdlet must override.</span></span> <span data-ttu-id="c9f0e-145">Zie voor meer informatie over hoe Windows PowerShell records verwerkt [hoe Windows PowerShell werkt](https://msdn.microsoft.com/en-us/ced30e23-10af-4700-8933-49873bd84d58).</span><span class="sxs-lookup"><span data-stu-id="c9f0e-145">For more information about how Windows PowerShell processes records, see [How Windows PowerShell Works](https://msdn.microsoft.com/en-us/ced30e23-10af-4700-8933-49873bd84d58).</span></span>

<span data-ttu-id="c9f0e-146">Voor alle soorten invoer, de Windows PowerShell-runtime roept [System.Management.Automation.Cmdlet.BeginProcessing](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing) om in te schakelen van verwerking.</span><span class="sxs-lookup"><span data-stu-id="c9f0e-146">For all types of input, the Windows PowerShell runtime calls [System.Management.Automation.Cmdlet.BeginProcessing](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing) to enable processing.</span></span> <span data-ttu-id="c9f0e-147">Als de cmdlet sommige voorverwerking of setup uitvoert moet, kunt deze dit doen door deze methode te overschrijven.</span><span class="sxs-lookup"><span data-stu-id="c9f0e-147">If your cmdlet must perform some preprocessing or setup, it can do this by overriding this method.</span></span>

> [!NOTE]
> <span data-ttu-id="c9f0e-148">Windows PowerShell wordt de term 'record' gebruikt om te beschrijven van de set met parameterwaarden die zijn opgegeven als een cmdlet wordt aangeroepen.</span><span class="sxs-lookup"><span data-stu-id="c9f0e-148">Windows PowerShell uses the term "record" to describe the set of parameter values supplied when a cmdlet is called.</span></span>

<span data-ttu-id="c9f0e-149">Als de cmdlet pijpleidinginvoer accepteert, overschrijven deze de [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) methode, en (optioneel) de [System.Management.Automation.Cmdlet.EndProcessing](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing)methode.</span><span class="sxs-lookup"><span data-stu-id="c9f0e-149">If your cmdlet accepts pipeline input, it must override the [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) method, and optionally the [System.Management.Automation.Cmdlet.EndProcessing](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing) method.</span></span> <span data-ttu-id="c9f0e-150">Bijvoorbeeld, een cmdlet beide methoden kan overschrijven als het verzamelt alle invoer met behulp van [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) en wordt vervolgens toegepast op de invoer als geheel in plaats van één element tegelijk, als de `Sort-Object` cmdlet is.</span><span class="sxs-lookup"><span data-stu-id="c9f0e-150">For example, a cmdlet might override both methods if it gathers all input using [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) and then operates on the input as a whole rather than one element at a time, as the `Sort-Object` cmdlet does.</span></span>

<span data-ttu-id="c9f0e-151">Als uw cmdlet pijpleidinginvoer neemt, overschrijven deze de [System.Management.Automation.Cmdlet.EndProcessing](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing) methode.</span><span class="sxs-lookup"><span data-stu-id="c9f0e-151">If your cmdlet does not take pipeline input, it should override the [System.Management.Automation.Cmdlet.EndProcessing](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing) method.</span></span> <span data-ttu-id="c9f0e-152">Houd er rekening mee dat deze methode vaak in plaats van gebruikt wordt [System.Management.Automation.Cmdlet.BeginProcessing](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing) wanneer de cmdlet kan niet worden uitgevoerd op één element op een tijdstip, zoals het geval van een cmdlet sorteren.</span><span class="sxs-lookup"><span data-stu-id="c9f0e-152">Be aware that this method is frequently used in place of [System.Management.Automation.Cmdlet.BeginProcessing](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing) when the cmdlet cannot operate on one element at a time, as is the case for a sorting cmdlet.</span></span>

<span data-ttu-id="c9f0e-153">Omdat deze voorbeeld-cmdlet Get-Proc pijpleidinginvoer ontvangen moet, dit vervangt de [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) methode en maakt gebruik van de standaard-implementaties voor [ System.Management.Automation.Cmdlet.BeginProcessing](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing) en [System.Management.Automation.Cmdlet.EndProcessing](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing).</span><span class="sxs-lookup"><span data-stu-id="c9f0e-153">Because this sample Get-Proc cmdlet must receive pipeline input, it overrides the [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) method and uses the default implementations for [System.Management.Automation.Cmdlet.BeginProcessing](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing) and [System.Management.Automation.Cmdlet.EndProcessing](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing).</span></span> <span data-ttu-id="c9f0e-154">De [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) onderdrukking processen worden opgehaald en schrijft deze naar de opdrachtregel met behulp van de [System.Management.Automation.Cmdlet.WriteObject](/dotnet/api/System.Management.Automation.Cmdlet.WriteObject) methode.</span><span class="sxs-lookup"><span data-stu-id="c9f0e-154">The [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) override retrieves processes and writes them to the command line using the [System.Management.Automation.Cmdlet.WriteObject](/dotnet/api/System.Management.Automation.Cmdlet.WriteObject) method.</span></span>

```csharp
protected override void ProcessRecord()
{
  // Get the current processes
  Process[] processes = Process.GetProcesses();

  // Write the processes to the pipeline making them available
  // to the next cmdlet. The second parameter of this call tells
  // PowerShell to enumerate the array, and send one process at a
  // time to the pipeline.
  WriteObject(processes, true);
}
```

```vb
Protected Overrides Sub ProcessRecord()

    '/ Get the current processes.
    Dim processes As Process()
    processes = Process.GetProcesses()

    '/ Write the processes to the pipeline making them available
    '/ to the next cmdlet. The second parameter of this call tells
    '/ PowerShell to enumerate the array, and send one process at a
    '/ time to the pipeline.
    WriteObject(processes, True)

End Sub 'ProcessRecord
```

#### <a name="things-to-remember-about-input-processing"></a><span data-ttu-id="c9f0e-155">Om te onthouden over de verwerking van invoer</span><span class="sxs-lookup"><span data-stu-id="c9f0e-155">Things to Remember About Input Processing</span></span>

- <span data-ttu-id="c9f0e-156">De standaardbron voor invoer is een expliciete object (bijvoorbeeld een tekenreeks) opgegeven door de gebruiker op de opdrachtregel.</span><span class="sxs-lookup"><span data-stu-id="c9f0e-156">The default source for input is an explicit object (for example, a string) provided by the user on the command line.</span></span> <span data-ttu-id="c9f0e-157">Zie voor meer informatie, [het maken van een Cmdlet voor het proces vanaf de opdrachtregelinvoer](./adding-parameters-that-process-command-line-input.md).</span><span class="sxs-lookup"><span data-stu-id="c9f0e-157">For more information, see [Creating a Cmdlet to Process Command Line Input](./adding-parameters-that-process-command-line-input.md).</span></span>

- <span data-ttu-id="c9f0e-158">Invoer verwerken methode kan ook invoer ontvangen van het uitvoerobject van een upstream-cmdlet op de pijplijn.</span><span class="sxs-lookup"><span data-stu-id="c9f0e-158">An input processing method can also receive input from the output object of an upstream cmdlet on the pipeline.</span></span> <span data-ttu-id="c9f0e-159">Zie voor meer informatie, [het maken van een Cmdlet voor het proces Pijpleidinginvoer](./adding-parameters-that-process-pipeline-input.md).</span><span class="sxs-lookup"><span data-stu-id="c9f0e-159">For more information, see [Creating a Cmdlet to Process Pipeline Input](./adding-parameters-that-process-pipeline-input.md).</span></span> <span data-ttu-id="c9f0e-160">Houd er rekening mee dat de cmdlet kunt invoer van een combinatie van de opdrachtregel ontvangen en pipeline-gegevensbronnen.</span><span class="sxs-lookup"><span data-stu-id="c9f0e-160">Be aware that your cmdlet can receive input from a combination of command-line and pipeline sources.</span></span>

- <span data-ttu-id="c9f0e-161">De downstream-cmdlet kan niet worden geretourneerd gedurende een lange periode of helemaal niet.</span><span class="sxs-lookup"><span data-stu-id="c9f0e-161">The downstream cmdlet might not return for a long time, or not at all.</span></span> <span data-ttu-id="c9f0e-162">Om die reden, de verwerking van de methode in uw cmdlet invoer moet niet vergrendelingen hebben tijdens het aanroepen van [System.Management.Automation.Cmdlet.WriteObject](/dotnet/api/System.Management.Automation.Cmdlet.WriteObject), met name vergrendelingen waarvoor het bereik het cmdlet-exemplaar overschrijdt.</span><span class="sxs-lookup"><span data-stu-id="c9f0e-162">For that reason, the input processing method in your cmdlet should not hold locks during calls to [System.Management.Automation.Cmdlet.WriteObject](/dotnet/api/System.Management.Automation.Cmdlet.WriteObject), especially locks for which the scope extends beyond the cmdlet instance.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="c9f0e-163">Cmdlets moet nooit aanroepen [System.Console.Writeline\*](/dotnet/api/System.Console.WriteLine) of een equivalent daarvan.</span><span class="sxs-lookup"><span data-stu-id="c9f0e-163">Cmdlets should never call [System.Console.Writeline\*](/dotnet/api/System.Console.WriteLine) or its equivalent.</span></span>

- <span data-ttu-id="c9f0e-164">Uw cmdlet hebt objectvariabelen opschonen na afloop verwerken (bijvoorbeeld, als het openen van de schuifknop van een bestand van de [System.Management.Automation.Cmdlet.BeginProcessing](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing) methode en houdt de ingang voor gebruik door openen.[ System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord)).</span><span class="sxs-lookup"><span data-stu-id="c9f0e-164">Your cmdlet might have object variables to clean up when it is finished processing (for example, if it opens a file handle in the [System.Management.Automation.Cmdlet.BeginProcessing](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing) method and keeps the handle open for use by [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord)).</span></span> <span data-ttu-id="c9f0e-165">Het is belangrijk te onthouden dat de Windows PowerShell-runtime niet altijd aanroepen de [System.Management.Automation.Cmdlet.EndProcessing](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing) methode, waarmee de object-opschoning moet uitvoeren.</span><span class="sxs-lookup"><span data-stu-id="c9f0e-165">It is important to remember that the Windows PowerShell runtime does not always call the [System.Management.Automation.Cmdlet.EndProcessing](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing) method, which should perform object cleanup.</span></span>

<span data-ttu-id="c9f0e-166">Bijvoorbeeld, [System.Management.Automation.Cmdlet.EndProcessing](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing) kan niet worden aangeroepen als de cmdlet halverwege wordt geannuleerd of als een afsluitende fout in een deel van de cmdlet optreedt.</span><span class="sxs-lookup"><span data-stu-id="c9f0e-166">For example, [System.Management.Automation.Cmdlet.EndProcessing](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing) might not be called if the cmdlet is canceled midway or if a terminating error occurs in any part of the cmdlet.</span></span> <span data-ttu-id="c9f0e-167">Daarom een cmdlet waarvoor de object-opschoning moet implementeren de volledige [System.IDisposable](/dotnet/api/System.IDisposable) patroon, waaronder de finalizer, zodat de runtime beide aanroepen kan [ System.Management.Automation.Cmdlet.EndProcessing](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing) en [System.IDisposable.Dispose\*](/dotnet/api/System.IDisposable.Dispose) aan het einde van de verwerking.</span><span class="sxs-lookup"><span data-stu-id="c9f0e-167">Therefore, a cmdlet that requires object cleanup should implement the complete [System.IDisposable](/dotnet/api/System.IDisposable) pattern, including the finalizer, so that the runtime can call both [System.Management.Automation.Cmdlet.EndProcessing](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing) and [System.IDisposable.Dispose\*](/dotnet/api/System.IDisposable.Dispose) at the end of processing.</span></span>

## <a name="code-sample"></a><span data-ttu-id="c9f0e-168">Voorbeeld van code</span><span class="sxs-lookup"><span data-stu-id="c9f0e-168">Code Sample</span></span>

<span data-ttu-id="c9f0e-169">Voor de volledige C# voorbeeldcode, Zie [GetProcessSample01 voorbeeld](./getprocesssample01-sample.md).</span><span class="sxs-lookup"><span data-stu-id="c9f0e-169">For the complete C# sample code, see [GetProcessSample01 Sample](./getprocesssample01-sample.md).</span></span>

## <a name="defining-object-types-and-formatting"></a><span data-ttu-id="c9f0e-170">Objecttype definiëren en opmaak</span><span class="sxs-lookup"><span data-stu-id="c9f0e-170">Defining Object Types and Formatting</span></span>

<span data-ttu-id="c9f0e-171">Windows PowerShell wordt informatie doorgegeven tussen cmdlets met behulp van .NET-objecten.</span><span class="sxs-lookup"><span data-stu-id="c9f0e-171">Windows PowerShell passes information between cmdlets using .NET objects.</span></span> <span data-ttu-id="c9f0e-172">Als gevolg daarvan kan een cmdlet mogelijk voor het definiëren van een eigen type of de cmdlet moet mogelijk om uit te breiden van een bestaand type geleverd door een andere cmdlet.</span><span class="sxs-lookup"><span data-stu-id="c9f0e-172">Consequently, a cmdlet might need to define its own type, or the cmdlet might need to extend an existing type provided by another cmdlet.</span></span> <span data-ttu-id="c9f0e-173">Zie voor meer informatie over het definiëren van nieuwe typen of uitbreiden van bestaande typen [objecttypen uitbreiden en opmaak](https://msdn.microsoft.com/en-us/da976d91-a3d6-44e8-affa-466b1e2bd351).</span><span class="sxs-lookup"><span data-stu-id="c9f0e-173">For more information about defining new types or extending existing types, see [Extending Object Types and Formatting](https://msdn.microsoft.com/en-us/da976d91-a3d6-44e8-affa-466b1e2bd351).</span></span>

## <a name="building-the-cmdlet"></a><span data-ttu-id="c9f0e-174">Het bouwen van de Cmdlet</span><span class="sxs-lookup"><span data-stu-id="c9f0e-174">Building the Cmdlet</span></span>

<span data-ttu-id="c9f0e-175">Na de implementatie van een cmdlet, moet u deze registreren met Windows PowerShell via een Windows PowerShell-module.</span><span class="sxs-lookup"><span data-stu-id="c9f0e-175">After implementing a cmdlet, you must register it with Windows PowerShell through a Windows PowerShell snap-in.</span></span> <span data-ttu-id="c9f0e-176">Zie voor meer informatie over het registreren van cmdlets [hoe u Cmdlets registreren, Providers en hosting van toepassingen](https://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c).</span><span class="sxs-lookup"><span data-stu-id="c9f0e-176">For more information about registering cmdlets, see [How to Register Cmdlets, Providers, and Host Applications](https://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c).</span></span>

## <a name="testing-the-cmdlet"></a><span data-ttu-id="c9f0e-177">Testen van de Cmdlet</span><span class="sxs-lookup"><span data-stu-id="c9f0e-177">Testing the Cmdlet</span></span>

<span data-ttu-id="c9f0e-178">Wanneer de cmdlet is geregistreerd met Windows PowerShell, kunt u deze testen door te voeren op de opdrachtregel.</span><span class="sxs-lookup"><span data-stu-id="c9f0e-178">When your cmdlet has been registered with Windows PowerShell, you can test it by running it on the command line.</span></span> <span data-ttu-id="c9f0e-179">De code voor onze voorbeeld-cmdlet Get-Proc is klein, maar nog steeds maakt gebruik van de Windows PowerShell-runtime en een bestaande .NET-object, wat voldoende is om nuttig.</span><span class="sxs-lookup"><span data-stu-id="c9f0e-179">The code for our sample Get-Proc cmdlet is small, but it still uses the Windows PowerShell runtime and an existing .NET object, which is enough to make it useful.</span></span> <span data-ttu-id="c9f0e-180">Laten we het testen om beter te begrijpen wat Get-Proc kan doen en hoe de uitvoer kan worden gebruikt.</span><span class="sxs-lookup"><span data-stu-id="c9f0e-180">Let's test it to better understand what Get-Proc can do and how its output can be used.</span></span> <span data-ttu-id="c9f0e-181">Zie voor meer informatie over het gebruik van cmdlets vanaf de opdrachtregel de [aan de slag met Windows PowerShell](/powershell/scripting/getting-started/getting-started-with-windows-powershell).</span><span class="sxs-lookup"><span data-stu-id="c9f0e-181">For more information about using cmdlets from the command line, see the [Getting Started with Windows PowerShell](/powershell/scripting/getting-started/getting-started-with-windows-powershell).</span></span>

1. <span data-ttu-id="c9f0e-182">Start Windows PowerShell en ophalen van de huidige processen die worden uitgevoerd op de computer.</span><span class="sxs-lookup"><span data-stu-id="c9f0e-182">Start Windows PowerShell, and get the current processes running on the computer.</span></span>

    ```powershell
    get-proc
    ```

    <span data-ttu-id="c9f0e-183">De volgende uitvoer wordt weergegeven.</span><span class="sxs-lookup"><span data-stu-id="c9f0e-183">The following output appears.</span></span>

    ```output
    Handles  NPM(K)  PM(K)  WS(K)  VS(M)  CPU(s)  Id   ProcessName
    -------  ------  -----  -----  -----  ------  --   ----------
    254      7       7664   12048  66     173.75  1200  QCTRAY
    32       2       1372   2628   31       0.04  1860  DLG
    271      6       1216   3688   33       0.03  3816  lg
    27       2       560    1920   24       0.01  1768  TpScrex
    ...
    ```

2. <span data-ttu-id="c9f0e-184">Een variabele toewijzen aan de cmdlet-resultaten voor het eenvoudiger bewerken.</span><span class="sxs-lookup"><span data-stu-id="c9f0e-184">Assign a variable to the cmdlet results for easier manipulation.</span></span>

    ```powershell
    $p=get-proc
    ```

3. <span data-ttu-id="c9f0e-185">Het aantal processen ophalen.</span><span class="sxs-lookup"><span data-stu-id="c9f0e-185">Get the number of processes.</span></span>

    ```powershell
    $p.length
    ```

    <span data-ttu-id="c9f0e-186">De volgende uitvoer wordt weergegeven.</span><span class="sxs-lookup"><span data-stu-id="c9f0e-186">The following output appears.</span></span>

    ```output
    63
    ```

4. <span data-ttu-id="c9f0e-187">Een specifiek proces worden opgehaald.</span><span class="sxs-lookup"><span data-stu-id="c9f0e-187">Retrieve a specific process.</span></span>

    ```powershell
    $p[6]
    ```

    <span data-ttu-id="c9f0e-188">De volgende uitvoer wordt weergegeven.</span><span class="sxs-lookup"><span data-stu-id="c9f0e-188">The following output appears.</span></span>

    ```output
    Handles  NPM(K)  PM(K)  WS(K)  VS(M)  CPU(s)  Id    ProcessName
    -------  ------  -----  -----  -----  ------  --    -----------
    1033     3       2400   3336   35     0.53    1588  rundll32
    ```

5. <span data-ttu-id="c9f0e-189">Haal de begintijd van dit proces.</span><span class="sxs-lookup"><span data-stu-id="c9f0e-189">Get the start time of this process.</span></span>

    ```powershell
    $p[6].starttime
    ```

    <span data-ttu-id="c9f0e-190">De volgende uitvoer wordt weergegeven.</span><span class="sxs-lookup"><span data-stu-id="c9f0e-190">The following output appears.</span></span>

    ```output
    Tuesday, July 26, 2005 9:34:15 AM
    ```

    ```powershell
    $p[6].starttime.dayofyear
    ```

    ```output
    207
    ```

6. <span data-ttu-id="c9f0e-191">De processen die het aantal ingangen groter dan 500 is ophalen en het resultaat te sorteren.</span><span class="sxs-lookup"><span data-stu-id="c9f0e-191">Get the processes for which the handle count is greater than 500, and sort the result.</span></span>

    ```powershell
    $p | Where-Object {$_.HandleCount -gt 500 } | Sort-Object HandleCount
    ```

    <span data-ttu-id="c9f0e-192">De volgende uitvoer wordt weergegeven.</span><span class="sxs-lookup"><span data-stu-id="c9f0e-192">The following output appears.</span></span>

    ```output
    Handles  NPM(K)  PM(K)  WS(K)  VS(M)  CPU(s)  Id   ProcessName
    -------  ------  -----  -----  -----  ------  --   ----------
    568      14      2164   4972   39     5.55    824  svchost
    716       7      2080   5332   28    25.38    468  csrss
    761      21      33060  56608  440  393.56    3300 WINWORD
    791      71      7412   4540   59     3.31    492  winlogon
    ...
    ```

7. <span data-ttu-id="c9f0e-193">Gebruik de `Get-Member` cmdlet om de eigenschappen die beschikbaar zijn voor elk proces weer te geven.</span><span class="sxs-lookup"><span data-stu-id="c9f0e-193">Use the `Get-Member` cmdlet to list the properties available for each process.</span></span>

    ```powershell
    $p | Get-Member -MemberType property
    ```

    ```output
        TypeName: System.Diagnostics.Process
    ```

    <span data-ttu-id="c9f0e-194">De volgende uitvoer wordt weergegeven.</span><span class="sxs-lookup"><span data-stu-id="c9f0e-194">The following output appears.</span></span>

    ```output
    Name                     MemberType Definition
    ----                     ---------- ----------
    BasePriority             Property   System.Int32 BasePriority {get;}
    Container                Property   System.ComponentModel.IContainer Conta...
    EnableRaisingEvents      Property   System.Boolean EnableRaisingEvents {ge...
    ...
    ```

## <a name="see-also"></a><span data-ttu-id="c9f0e-195">Zie ook</span><span class="sxs-lookup"><span data-stu-id="c9f0e-195">See Also</span></span>

[<span data-ttu-id="c9f0e-196">Het maken van een Cmdlet voor het verwerken van invoer van de opdrachtregel</span><span class="sxs-lookup"><span data-stu-id="c9f0e-196">Creating a Cmdlet to Process Command Line Input</span></span>](./adding-parameters-that-process-command-line-input.md)

[<span data-ttu-id="c9f0e-197">Het maken van een Cmdlet voor het verwerken van invoer van de pijplijn</span><span class="sxs-lookup"><span data-stu-id="c9f0e-197">Creating a Cmdlet to Process Pipeline Input</span></span>](./adding-parameters-that-process-pipeline-input.md)

[<span data-ttu-id="c9f0e-198">Over het maken van een Windows PowerShell-Cmdlet</span><span class="sxs-lookup"><span data-stu-id="c9f0e-198">How to Create a Windows PowerShell Cmdlet</span></span>](https://msdn.microsoft.com/en-us/0d721742-c849-4d0d-964f-78ddd9cd258c)

[<span data-ttu-id="c9f0e-199">Objecttypen uitbreiden en opmaak</span><span class="sxs-lookup"><span data-stu-id="c9f0e-199">Extending Object Types and Formatting</span></span>](https://msdn.microsoft.com/en-us/da976d91-a3d6-44e8-affa-466b1e2bd351)

[<span data-ttu-id="c9f0e-200">How Windows PowerShell Works</span><span class="sxs-lookup"><span data-stu-id="c9f0e-200">How Windows PowerShell Works</span></span>](https://msdn.microsoft.com/en-us/ced30e23-10af-4700-8933-49873bd84d58)

[<span data-ttu-id="c9f0e-201">Over het registreren van Providers,-Cmdlets en -toepassingen hosten</span><span class="sxs-lookup"><span data-stu-id="c9f0e-201">How to Register Cmdlets, Providers, and Host Applications</span></span>](https://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c)

[<span data-ttu-id="c9f0e-202">Windows PowerShell-referentie</span><span class="sxs-lookup"><span data-stu-id="c9f0e-202">Windows PowerShell Reference</span></span>](../windows-powershell-reference.md)

[<span data-ttu-id="c9f0e-203">Cmdlet-voorbeelden</span><span class="sxs-lookup"><span data-stu-id="c9f0e-203">Cmdlet Samples</span></span>](./cmdlet-samples.md)