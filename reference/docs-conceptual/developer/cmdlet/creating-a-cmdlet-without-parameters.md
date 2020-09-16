---
title: Een cmdlet zonder para meters maken | Microsoft Docs
ms.date: 09/13/2016
helpviewer_keywords:
- cmdlets [PowerShell Programmers Guide], creating
- cmdlets [PowerShell Programmers Guide], basic cmdlet
ms.openlocfilehash: a14d25660d596ebd12cd7d74b607eab6ac9fd1be
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 08/05/2020
ms.locfileid: "87784381"
---
# <a name="creating-a-cmdlet-without-parameters"></a><span data-ttu-id="c715a-102">Een cmdlet maken zonder parameters</span><span class="sxs-lookup"><span data-stu-id="c715a-102">Creating a Cmdlet without Parameters</span></span>

<span data-ttu-id="c715a-103">In deze sectie wordt beschreven hoe u een cmdlet maakt waarmee informatie wordt opgehaald van de lokale computer zonder het gebruik van para meters, en vervolgens de informatie naar de pijp lijn schrijft.</span><span class="sxs-lookup"><span data-stu-id="c715a-103">This section describes how to create a cmdlet that retrieves information from the local computer without the use of parameters, and then writes the information to the pipeline.</span></span> <span data-ttu-id="c715a-104">De cmdlet die hier wordt beschreven, is een Get-proc-cmdlet waarmee informatie wordt opgehaald over de processen van de lokale computer en die informatie vervolgens wordt weer gegeven op de opdracht regel.</span><span class="sxs-lookup"><span data-stu-id="c715a-104">The cmdlet described here is a Get-Proc cmdlet that retrieves information about the processes of the local computer, and then displays that information at the command line.</span></span>

> [!NOTE]
> <span data-ttu-id="c715a-105">Houd er rekening mee dat bij het schrijven van cmdlets de referentie-assembly's van Windows Power shell® worden gedownload naar schijf (standaard in C:\Program Files\Reference Assemblies\Microsoft\WindowsPowerShell\v1.0).</span><span class="sxs-lookup"><span data-stu-id="c715a-105">Be aware that when writing cmdlets, the Windows PowerShell® reference assemblies are downloaded onto disk (by default at C:\Program Files\Reference Assemblies\Microsoft\WindowsPowerShell\v1.0).</span></span> <span data-ttu-id="c715a-106">Ze zijn niet geïnstalleerd in de GAC (Global assembly cache).</span><span class="sxs-lookup"><span data-stu-id="c715a-106">They are not installed in the Global Assembly Cache (GAC).</span></span>

## <a name="naming-the-cmdlet"></a><span data-ttu-id="c715a-107">De cmdlet een naam geven</span><span class="sxs-lookup"><span data-stu-id="c715a-107">Naming the Cmdlet</span></span>

<span data-ttu-id="c715a-108">De naam van een cmdlet bestaat uit een werk woord waarmee de actie wordt aangegeven die de cmdlet uitvoert en een zelfstandig naam woord dat de items aangeeft waarop de cmdlet op betrekking heeft.</span><span class="sxs-lookup"><span data-stu-id="c715a-108">A cmdlet name consists of a verb that indicates the action the cmdlet takes and a noun that indicates the items that the cmdlet acts upon.</span></span> <span data-ttu-id="c715a-109">Omdat in deze voor beeld-cmdlet Get-proc proces objecten worden opgehaald, wordt de term Get gebruikt, die is gedefinieerd door [System. Management. Automation. Verbscommon](/dotnet/api/System.Management.Automation.VerbsCommon) -inventarisatie en het zelfstandig naam woord ' proc ' om aan te geven dat de cmdlet werkt voor het verwerken van items.</span><span class="sxs-lookup"><span data-stu-id="c715a-109">Because this sample Get-Proc cmdlet retrieves process objects, it uses the verb "Get", defined by the [System.Management.Automation.Verbscommon](/dotnet/api/System.Management.Automation.VerbsCommon) enumeration, and the noun "Proc" to indicate that the cmdlet works on process items.</span></span>

<span data-ttu-id="c715a-110">Gebruik bij het benoemen van cmdlets geen van de volgende tekens: #, () {} [] &-/\ $;: ' ' <> &#124; ?</span><span class="sxs-lookup"><span data-stu-id="c715a-110">When naming cmdlets, do not use any of the following characters: # , () {} [] & - /\ $ ; : " '<> &#124; ?</span></span> <span data-ttu-id="c715a-111">@ \` .</span><span class="sxs-lookup"><span data-stu-id="c715a-111">@ \` .</span></span>

### <a name="choosing-a-noun"></a><span data-ttu-id="c715a-112">Een zelfstandig naam woord kiezen</span><span class="sxs-lookup"><span data-stu-id="c715a-112">Choosing a Noun</span></span>

<span data-ttu-id="c715a-113">Kies een specifiek zelfstandig naam woord.</span><span class="sxs-lookup"><span data-stu-id="c715a-113">You should choose a noun that is specific.</span></span> <span data-ttu-id="c715a-114">U kunt het beste een enkelvoudig zelfstandig naam woord gebruiken, met een kortere versie van de product naam.</span><span class="sxs-lookup"><span data-stu-id="c715a-114">It is best to use a singular noun prefixed with a shortened version of the product name.</span></span> <span data-ttu-id="c715a-115">Een voor beeld van een cmdlet-naam van dit type is ' `Get-SQLServer` '.</span><span class="sxs-lookup"><span data-stu-id="c715a-115">An example cmdlet name of this type is "`Get-SQLServer`".</span></span>

### <a name="choosing-a-verb"></a><span data-ttu-id="c715a-116">Een werk woord kiezen</span><span class="sxs-lookup"><span data-stu-id="c715a-116">Choosing a Verb</span></span>

<span data-ttu-id="c715a-117">U moet een verb gebruiken uit de set met goedgekeurde opdracht namen voor cmdlets.</span><span class="sxs-lookup"><span data-stu-id="c715a-117">You should use a verb from the set of approved cmdlet verb names.</span></span> <span data-ttu-id="c715a-118">Zie [cmdlet verb names](./approved-verbs-for-windows-powershell-commands.md)(Engelstalig) voor meer informatie over de goedgekeurde cmdlet-termen.</span><span class="sxs-lookup"><span data-stu-id="c715a-118">For more information about the approved cmdlet verbs, see [Cmdlet Verb Names](./approved-verbs-for-windows-powershell-commands.md).</span></span>

## <a name="defining-the-cmdlet-class"></a><span data-ttu-id="c715a-119">De cmdlet-klasse definiëren</span><span class="sxs-lookup"><span data-stu-id="c715a-119">Defining the Cmdlet Class</span></span>

<span data-ttu-id="c715a-120">Nadat u de naam van een cmdlet hebt gekozen, definieert u een .NET-klasse voor het implementeren van de cmdlet.</span><span class="sxs-lookup"><span data-stu-id="c715a-120">Once you have chosen a cmdlet name, define a .NET class to implement the cmdlet.</span></span> <span data-ttu-id="c715a-121">Dit is de klassedefinitie voor deze voor beeld van de cmdlet Get-proc:</span><span class="sxs-lookup"><span data-stu-id="c715a-121">Here is the class definition for this sample Get-Proc cmdlet:</span></span>

```csharp
[Cmdlet(VerbsCommon.Get, "Proc")]
  public class GetProcCommand : Cmdlet
```

```vb
<Cmdlet(VerbsCommon.Get, "Proc")> _
Public Class GetProcCommand
    Inherits Cmdlet
```

<span data-ttu-id="c715a-122">U ziet dat er eerder aan de klassedefinitie, het kenmerk [System. Management. Automation. CmdletAttribute](/dotnet/api/System.Management.Automation.CmdletAttribute) , met de syntaxis `[Cmdlet(verb, noun, ...)]` , wordt gebruikt om deze klasse te identificeren als een cmdlet.</span><span class="sxs-lookup"><span data-stu-id="c715a-122">Notice that previous to the class definition, the [System.Management.Automation.CmdletAttribute](/dotnet/api/System.Management.Automation.CmdletAttribute) attribute, with the syntax `[Cmdlet(verb, noun, ...)]`, is used to identify this class as a cmdlet.</span></span> <span data-ttu-id="c715a-123">Dit is het enige vereiste kenmerk voor alle cmdlets en de Windows Power shell-runtime kan ze op de juiste wijze aanroepen.</span><span class="sxs-lookup"><span data-stu-id="c715a-123">This is the only required attribute for all cmdlets, and it allows the Windows PowerShell runtime to call them correctly.</span></span> <span data-ttu-id="c715a-124">U kunt kenmerk trefwoorden instellen om de klasse zo nodig verder te declareren.</span><span class="sxs-lookup"><span data-stu-id="c715a-124">You can set attribute keywords to further declare the class if necessary.</span></span> <span data-ttu-id="c715a-125">Houd er rekening mee dat de kenmerk declaratie voor onze voor beeld-GetProcCommand-klasse alleen de namen van de zelfstandig naam woord en de verb declareert voor de cmdlet Get-proc.</span><span class="sxs-lookup"><span data-stu-id="c715a-125">Be aware that the attribute declaration for our sample GetProcCommand class declares only the noun and verb names for the Get-Proc cmdlet.</span></span>

> [!NOTE]
> <span data-ttu-id="c715a-126">Voor alle Windows Power shell-kenmerk klassen moeten de tref woorden die u kunt instellen overeenkomen met de eigenschappen van de kenmerk klasse.</span><span class="sxs-lookup"><span data-stu-id="c715a-126">For all Windows PowerShell attribute classes, the keywords that you can set correspond to properties of the attribute class.</span></span>

<span data-ttu-id="c715a-127">Wanneer u de klasse van de cmdlet een naam geeft, is het een goed idee om de naam van de cmdlet in de naam van de klasse weer te geven.</span><span class="sxs-lookup"><span data-stu-id="c715a-127">When naming the class of the cmdlet, it is a good practice to reflect the cmdlet name in the class name.</span></span> <span data-ttu-id="c715a-128">U doet dit door het formulier "VerbNounCommand" te gebruiken en "verb" en "zelfstandig naam" te vervangen door het werk woord en het zelfstandig naam woord dat wordt gebruikt in de cmdletnaam.</span><span class="sxs-lookup"><span data-stu-id="c715a-128">To do this, use the form "VerbNounCommand" and replace "Verb" and "Noun" with the verb and noun used in the cmdlet name.</span></span> <span data-ttu-id="c715a-129">Zoals wordt weer gegeven in de vorige klassedefinitie, definieert de voor beeld-cmdlet Get-proc een klasse met de naam GetProcCommand, die is afgeleid van de basis klasse [System. Management. Automation. cmdlet](/dotnet/api/System.Management.Automation.Cmdlet) .</span><span class="sxs-lookup"><span data-stu-id="c715a-129">As is shown in the previous class definition, the sample Get-Proc cmdlet defines a class called GetProcCommand, which derives from the [System.Management.Automation.Cmdlet](/dotnet/api/System.Management.Automation.Cmdlet) base class.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="c715a-130">Als u een cmdlet wilt definiëren die rechtstreeks toegang heeft tot de Windows Power shell-runtime, moet uw .NET-klasse worden afgeleid van de basis klasse [System. Management. Automation. PSCmdlet](/dotnet/api/System.Management.Automation.PSCmdlet) .</span><span class="sxs-lookup"><span data-stu-id="c715a-130">If you want to define a cmdlet that accesses the Windows PowerShell runtime directly, your .NET class should derive from the [System.Management.Automation.PSCmdlet](/dotnet/api/System.Management.Automation.PSCmdlet) base class.</span></span> <span data-ttu-id="c715a-131">Zie [een cmdlet maken die parameter sets definieert](./adding-parameter-sets-to-a-cmdlet.md)voor meer informatie over deze klasse.</span><span class="sxs-lookup"><span data-stu-id="c715a-131">For more information about this class, see [Creating a Cmdlet that Defines Parameter Sets](./adding-parameter-sets-to-a-cmdlet.md).</span></span>

> [!NOTE]
> <span data-ttu-id="c715a-132">De klasse voor een cmdlet moet expliciet als openbaar worden gemarkeerd.</span><span class="sxs-lookup"><span data-stu-id="c715a-132">The class for a cmdlet must be explicitly marked as public.</span></span> <span data-ttu-id="c715a-133">Klassen die niet zijn gemarkeerd als openbaar, worden standaard intern en worden niet gevonden door de Windows Power shell-runtime.</span><span class="sxs-lookup"><span data-stu-id="c715a-133">Classes that are not marked as public will default to internal and will not be found by the Windows PowerShell runtime.</span></span>

<span data-ttu-id="c715a-134">Windows Power Shell maakt gebruik van de naam ruimte [micro soft. Power shell. commands](/dotnet/api/Microsoft.PowerShell.Commands) voor de bijbehorende cmdlet-klassen.</span><span class="sxs-lookup"><span data-stu-id="c715a-134">Windows PowerShell uses the [Microsoft.PowerShell.Commands](/dotnet/api/Microsoft.PowerShell.Commands) namespace for its cmdlet classes.</span></span> <span data-ttu-id="c715a-135">Het is raadzaam om uw cmdlet-klassen in een opdrachten naam ruimte van uw API-naam ruimte te plaatsen, bijvoorbeeld xxx. PS. commands.</span><span class="sxs-lookup"><span data-stu-id="c715a-135">It is recommended to place your cmdlet classes in a Commands namespace of your API namespace, for example, xxx.PS.Commands.</span></span>

## <a name="overriding-an-input-processing-method"></a><span data-ttu-id="c715a-136">Een invoer verwerkings methode overschrijven</span><span class="sxs-lookup"><span data-stu-id="c715a-136">Overriding an Input Processing Method</span></span>

<span data-ttu-id="c715a-137">De klasse [System. Management. Automation. cmdlet](/dotnet/api/System.Management.Automation.Cmdlet) biedt drie belang rijke invoer methoden, ten minste één van de cmdlets die moeten worden overschreven.</span><span class="sxs-lookup"><span data-stu-id="c715a-137">The [System.Management.Automation.Cmdlet](/dotnet/api/System.Management.Automation.Cmdlet) class provides three main input processing methods, at least one of which your cmdlet must override.</span></span> <span data-ttu-id="c715a-138">Zie [How Windows Power shell](/previous-versions//ms714658(v=vs.85))(Engelstalig) voor meer informatie over het verwerken van records in Windows Power shell.</span><span class="sxs-lookup"><span data-stu-id="c715a-138">For more information about how Windows PowerShell processes records, see [How Windows PowerShell Works](/previous-versions//ms714658(v=vs.85)).</span></span>

<span data-ttu-id="c715a-139">Voor alle typen invoer roept Windows Power shell runtime [System. Management. Automation. cmdlet. BeginProcessing](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing) aan om de verwerking in te scha kelen.</span><span class="sxs-lookup"><span data-stu-id="c715a-139">For all types of input, the Windows PowerShell runtime calls [System.Management.Automation.Cmdlet.BeginProcessing](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing) to enable processing.</span></span> <span data-ttu-id="c715a-140">Als uw cmdlet een aantal voor verwerkingen of Setup moet uitvoeren, kan dit door deze methode te overschrijven.</span><span class="sxs-lookup"><span data-stu-id="c715a-140">If your cmdlet must perform some preprocessing or setup, it can do this by overriding this method.</span></span>

> [!NOTE]
> <span data-ttu-id="c715a-141">Windows Power shell gebruikt de term ' record ' om de set parameter waarden te beschrijven die worden opgegeven wanneer een cmdlet wordt aangeroepen.</span><span class="sxs-lookup"><span data-stu-id="c715a-141">Windows PowerShell uses the term "record" to describe the set of parameter values supplied when a cmdlet is called.</span></span>

<span data-ttu-id="c715a-142">Als uw cmdlet pijplijn invoer accepteert, moet deze de methode [System. Management. Automation. cmdlet. ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) negeren en optioneel de methode [System. Management. Automation. cmdlet. EndProcessing](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing) .</span><span class="sxs-lookup"><span data-stu-id="c715a-142">If your cmdlet accepts pipeline input, it must override the [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) method, and optionally the [System.Management.Automation.Cmdlet.EndProcessing](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing) method.</span></span> <span data-ttu-id="c715a-143">Zo kan een cmdlet beide methoden overschrijven als alle invoer wordt verzameld met [System. Management. Automation. cmdlet. ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) en vervolgens als de cmdlet wordt uitgevoerd op de invoer als geheel in plaats van één element tegelijk `Sort-Object` .</span><span class="sxs-lookup"><span data-stu-id="c715a-143">For example, a cmdlet might override both methods if it gathers all input using [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) and then operates on the input as a whole rather than one element at a time, as the `Sort-Object` cmdlet does.</span></span>

<span data-ttu-id="c715a-144">Als uw cmdlet geen pijplijn invoer heeft, moet deze de methode [System. Management. Automation. cmdlet. EndProcessing](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing) overschrijven.</span><span class="sxs-lookup"><span data-stu-id="c715a-144">If your cmdlet does not take pipeline input, it should override the [System.Management.Automation.Cmdlet.EndProcessing](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing) method.</span></span> <span data-ttu-id="c715a-145">Houd er rekening mee dat deze methode veelvuldig wordt gebruikt in plaats van [System. Management. Automation. cmdlet. BeginProcessing](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing) wanneer de cmdlet op één element per keer niet kan worden uitgevoerd, zoals in het geval van een sorteer-cmdlet.</span><span class="sxs-lookup"><span data-stu-id="c715a-145">Be aware that this method is frequently used in place of [System.Management.Automation.Cmdlet.BeginProcessing](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing) when the cmdlet cannot operate on one element at a time, as is the case for a sorting cmdlet.</span></span>

<span data-ttu-id="c715a-146">Omdat deze voor beeld-cmdlet Get-proc de pijplijn invoer moet ontvangen, wordt de methode [System. Management. Automation. cmdlet. ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) genegeerd en worden de standaard implementaties voor [System.](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing) management. Automation. cmdlet. BeginProcessing en [System. Management. Automation. cmdlet. EndProcessing](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing)gebruikt.</span><span class="sxs-lookup"><span data-stu-id="c715a-146">Because this sample Get-Proc cmdlet must receive pipeline input, it overrides the [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) method and uses the default implementations for [System.Management.Automation.Cmdlet.BeginProcessing](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing) and [System.Management.Automation.Cmdlet.EndProcessing](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing).</span></span> <span data-ttu-id="c715a-147">Met [System. Management. Automation. cmdlet. ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) override worden processen opgehaald en naar de opdracht regel geschreven met behulp van de methode [System. Management. Automation. cmdlet. WriteObject](/dotnet/api/System.Management.Automation.Cmdlet.WriteObject) .</span><span class="sxs-lookup"><span data-stu-id="c715a-147">The [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) override retrieves processes and writes them to the command line using the [System.Management.Automation.Cmdlet.WriteObject](/dotnet/api/System.Management.Automation.Cmdlet.WriteObject) method.</span></span>

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

#### <a name="things-to-remember-about-input-processing"></a><span data-ttu-id="c715a-148">Wat u moet weten over invoer verwerking</span><span class="sxs-lookup"><span data-stu-id="c715a-148">Things to Remember About Input Processing</span></span>

- <span data-ttu-id="c715a-149">De standaard bron voor invoer is een expliciet object (bijvoorbeeld een teken reeks) dat door de gebruiker is opgegeven op de opdracht regel.</span><span class="sxs-lookup"><span data-stu-id="c715a-149">The default source for input is an explicit object (for example, a string) provided by the user on the command line.</span></span> <span data-ttu-id="c715a-150">Zie [een cmdlet maken voor het verwerken van opdracht regel invoer](./adding-parameters-that-process-command-line-input.md)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="c715a-150">For more information, see [Creating a Cmdlet to Process Command Line Input](./adding-parameters-that-process-command-line-input.md).</span></span>

- <span data-ttu-id="c715a-151">Een invoer verwerkings methode kan ook invoer ontvangen van het uitvoer object van een upstream-cmdlet in de pijp lijn.</span><span class="sxs-lookup"><span data-stu-id="c715a-151">An input processing method can also receive input from the output object of an upstream cmdlet on the pipeline.</span></span> <span data-ttu-id="c715a-152">Zie [een cmdlet maken voor het verwerken van pijplijn invoer](./adding-parameters-that-process-pipeline-input.md)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="c715a-152">For more information, see [Creating a Cmdlet to Process Pipeline Input](./adding-parameters-that-process-pipeline-input.md).</span></span> <span data-ttu-id="c715a-153">Houd er rekening mee dat uw cmdlet invoer kan ontvangen van een combi natie van opdracht regel-en pijplijn bronnen.</span><span class="sxs-lookup"><span data-stu-id="c715a-153">Be aware that your cmdlet can receive input from a combination of command-line and pipeline sources.</span></span>

- <span data-ttu-id="c715a-154">De downstream-cmdlet kan niet lang worden geretourneerd of helemaal niet.</span><span class="sxs-lookup"><span data-stu-id="c715a-154">The downstream cmdlet might not return for a long time, or not at all.</span></span> <span data-ttu-id="c715a-155">Om die reden mag de invoer verwerkings methode in uw cmdlet geen vergren delingen bevatten tijdens aanroepen naar [System. Management. Automation. cmdlet. WriteObject](/dotnet/api/System.Management.Automation.Cmdlet.WriteObject), met name de vergren delingen waarvoor de scope zich buiten het cmdlet-exemplaar bevindt.</span><span class="sxs-lookup"><span data-stu-id="c715a-155">For that reason, the input processing method in your cmdlet should not hold locks during calls to [System.Management.Automation.Cmdlet.WriteObject](/dotnet/api/System.Management.Automation.Cmdlet.WriteObject), especially locks for which the scope extends beyond the cmdlet instance.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="c715a-156">Cmdlets moeten nooit [System. console. WriteLine \*](/dotnet/api/System.Console.WriteLine) of gelijkwaardige aanroepen.</span><span class="sxs-lookup"><span data-stu-id="c715a-156">Cmdlets should never call [System.Console.Writeline\*](/dotnet/api/System.Console.WriteLine) or its equivalent.</span></span>

- <span data-ttu-id="c715a-157">Uw cmdlet kan object variabelen bevatten om op te schonen wanneer de verwerking is voltooid (bijvoorbeeld als er een bestands ingang in de methode [System. Management. Automation. cmdlet. BeginProcessing](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing) wordt geopend en de ingang geopend is voor gebruik door [System. Management. Automation. cmdlet. ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord)).</span><span class="sxs-lookup"><span data-stu-id="c715a-157">Your cmdlet might have object variables to clean up when it is finished processing (for example, if it opens a file handle in the [System.Management.Automation.Cmdlet.BeginProcessing](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing) method and keeps the handle open for use by [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord)).</span></span> <span data-ttu-id="c715a-158">Het is belang rijk te weten dat de Windows Power shell-runtime de methode [System. Management. Automation. cmdlet. EndProcessing](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing) niet altijd aanroept, waardoor het opschonen van objecten moet worden uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="c715a-158">It is important to remember that the Windows PowerShell runtime does not always call the [System.Management.Automation.Cmdlet.EndProcessing](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing) method, which should perform object cleanup.</span></span>

<span data-ttu-id="c715a-159">[System. Management. Automation. cmdlet. EndProcessing](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing) kan bijvoorbeeld niet worden aangeroepen als de cmdlet halverwege is geannuleerd of als er een afsluit fout optreedt in een deel van de cmdlet.</span><span class="sxs-lookup"><span data-stu-id="c715a-159">For example, [System.Management.Automation.Cmdlet.EndProcessing](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing) might not be called if the cmdlet is canceled midway or if a terminating error occurs in any part of the cmdlet.</span></span> <span data-ttu-id="c715a-160">Daarom moet een cmdlet die het opschonen van objecten vereist, het volledige [System. IDisposable](/dotnet/api/System.IDisposable) -patroon implementeren, met inbegrip van de FINALIZE, zodat de runtime zowel [System. Management. Automation. cmdlet. EndProcessing](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing) als [System. IDisposable. Dispose \*](/dotnet/api/System.IDisposable.Dispose) aan het einde van de verwerking kan aanroepen.</span><span class="sxs-lookup"><span data-stu-id="c715a-160">Therefore, a cmdlet that requires object cleanup should implement the complete [System.IDisposable](/dotnet/api/System.IDisposable) pattern, including the finalizer, so that the runtime can call both [System.Management.Automation.Cmdlet.EndProcessing](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing) and [System.IDisposable.Dispose\*](/dotnet/api/System.IDisposable.Dispose) at the end of processing.</span></span>

## <a name="code-sample"></a><span data-ttu-id="c715a-161">Code voorbeeld</span><span class="sxs-lookup"><span data-stu-id="c715a-161">Code Sample</span></span>

<span data-ttu-id="c715a-162">Zie GetProcessSample01-voor [beeld](./getprocesssample01-sample.md)voor de volledige C#-voorbeeld code.</span><span class="sxs-lookup"><span data-stu-id="c715a-162">For the complete C# sample code, see [GetProcessSample01 Sample](./getprocesssample01-sample.md).</span></span>

## <a name="defining-object-types-and-formatting"></a><span data-ttu-id="c715a-163">Object typen en-opmaak definiëren</span><span class="sxs-lookup"><span data-stu-id="c715a-163">Defining Object Types and Formatting</span></span>

<span data-ttu-id="c715a-164">Windows Power shell geeft informatie door over cmdlets met behulp van .NET-objecten.</span><span class="sxs-lookup"><span data-stu-id="c715a-164">Windows PowerShell passes information between cmdlets using .NET objects.</span></span> <span data-ttu-id="c715a-165">Daarom moet een cmdlet een eigen type kunnen definiëren, of moet de cmdlet een bestaand type uitbreiden dat door een andere cmdlet wordt verschaft.</span><span class="sxs-lookup"><span data-stu-id="c715a-165">Consequently, a cmdlet might need to define its own type, or the cmdlet might need to extend an existing type provided by another cmdlet.</span></span> <span data-ttu-id="c715a-166">Zie [object typen en-opmaak uitbreiden](/previous-versions//ms714665(v=vs.85))voor meer informatie over het definiëren van nieuwe typen of het uitbreiden van bestaande typen.</span><span class="sxs-lookup"><span data-stu-id="c715a-166">For more information about defining new types or extending existing types, see [Extending Object Types and Formatting](/previous-versions//ms714665(v=vs.85)).</span></span>

## <a name="building-the-cmdlet"></a><span data-ttu-id="c715a-167">De cmdlet bouwen</span><span class="sxs-lookup"><span data-stu-id="c715a-167">Building the Cmdlet</span></span>

<span data-ttu-id="c715a-168">Nadat u een cmdlet hebt geïmplementeerd, moet u deze met Windows Power shell registreren via een Windows Power shell-module.</span><span class="sxs-lookup"><span data-stu-id="c715a-168">After implementing a cmdlet, you must register it with Windows PowerShell through a Windows PowerShell snap-in.</span></span> <span data-ttu-id="c715a-169">Zie [cmdlets, providers en hosttoepassingen registreren](/previous-versions//ms714644(v=vs.85))voor meer informatie over het registreren van cmdlets.</span><span class="sxs-lookup"><span data-stu-id="c715a-169">For more information about registering cmdlets, see [How to Register Cmdlets, Providers, and Host Applications](/previous-versions//ms714644(v=vs.85)).</span></span>

## <a name="testing-the-cmdlet"></a><span data-ttu-id="c715a-170">De cmdlet testen</span><span class="sxs-lookup"><span data-stu-id="c715a-170">Testing the Cmdlet</span></span>

<span data-ttu-id="c715a-171">Als uw cmdlet is geregistreerd bij Windows Power shell, kunt u deze testen door deze uit te voeren op de opdracht regel.</span><span class="sxs-lookup"><span data-stu-id="c715a-171">When your cmdlet has been registered with Windows PowerShell, you can test it by running it on the command line.</span></span> <span data-ttu-id="c715a-172">De code voor de voor beeld-cmdlet Get-proc is klein, maar maakt nog steeds gebruik van de Windows Power shell-runtime en een bestaand .NET-object. Dit is voldoende om het handig te maken.</span><span class="sxs-lookup"><span data-stu-id="c715a-172">The code for our sample Get-Proc cmdlet is small, but it still uses the Windows PowerShell runtime and an existing .NET object, which is enough to make it useful.</span></span> <span data-ttu-id="c715a-173">Laten we dit testen om beter te begrijpen wat Get-proc kan doen en hoe de uitvoer ervan kan worden gebruikt.</span><span class="sxs-lookup"><span data-stu-id="c715a-173">Let's test it to better understand what Get-Proc can do and how its output can be used.</span></span> <span data-ttu-id="c715a-174">Zie aan de slag [met Windows Power shell](/powershell/scripting/getting-started/getting-started-with-windows-powershell)voor meer informatie over het gebruik van cmdlets vanaf de opdracht regel.</span><span class="sxs-lookup"><span data-stu-id="c715a-174">For more information about using cmdlets from the command line, see the [Getting Started with Windows PowerShell](/powershell/scripting/getting-started/getting-started-with-windows-powershell).</span></span>

1. <span data-ttu-id="c715a-175">Start Windows Power shell en ontvang de huidige processen die op de computer worden uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="c715a-175">Start Windows PowerShell, and get the current processes running on the computer.</span></span>

    ```powershell
    get-proc
    ```

    <span data-ttu-id="c715a-176">De volgende uitvoer wordt weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="c715a-176">The following output appears.</span></span>

    ```output
    Handles  NPM(K)  PM(K)  WS(K)  VS(M)  CPU(s)  Id   ProcessName
    -------  ------  -----  -----  -----  ------  --   ----------
    254      7       7664   12048  66     173.75  1200  QCTRAY
    32       2       1372   2628   31       0.04  1860  DLG
    271      6       1216   3688   33       0.03  3816  lg
    27       2       560    1920   24       0.01  1768  TpScrex
    ...
    ```

2. <span data-ttu-id="c715a-177">Wijs een variabele toe aan de cmdlet-resultaten voor eenvoudiger manipulatie.</span><span class="sxs-lookup"><span data-stu-id="c715a-177">Assign a variable to the cmdlet results for easier manipulation.</span></span>

    ```powershell
    $p=get-proc
    ```

3. <span data-ttu-id="c715a-178">Het aantal processen ophalen.</span><span class="sxs-lookup"><span data-stu-id="c715a-178">Get the number of processes.</span></span>

    ```powershell
    $p.length
    ```

    <span data-ttu-id="c715a-179">De volgende uitvoer wordt weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="c715a-179">The following output appears.</span></span>

    ```output
    63
    ```

4. <span data-ttu-id="c715a-180">Haal een specifiek proces op.</span><span class="sxs-lookup"><span data-stu-id="c715a-180">Retrieve a specific process.</span></span>

    ```powershell
    $p[6]
    ```

    <span data-ttu-id="c715a-181">De volgende uitvoer wordt weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="c715a-181">The following output appears.</span></span>

    ```output
    Handles  NPM(K)  PM(K)  WS(K)  VS(M)  CPU(s)  Id    ProcessName
    -------  ------  -----  -----  -----  ------  --    -----------
    1033     3       2400   3336   35     0.53    1588  rundll32
    ```

5. <span data-ttu-id="c715a-182">De begin tijd van dit proces ophalen.</span><span class="sxs-lookup"><span data-stu-id="c715a-182">Get the start time of this process.</span></span>

    ```powershell
    $p[6].starttime
    ```

    <span data-ttu-id="c715a-183">De volgende uitvoer wordt weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="c715a-183">The following output appears.</span></span>

    ```output
    Tuesday, July 26, 2005 9:34:15 AM
    ```

    ```powershell
    $p[6].starttime.dayofyear
    ```

    ```output
    207
    ```

6. <span data-ttu-id="c715a-184">Haal de processen op waarvoor het aantal ingangen groter is dan 500 en sorteer het resultaat.</span><span class="sxs-lookup"><span data-stu-id="c715a-184">Get the processes for which the handle count is greater than 500, and sort the result.</span></span>

    ```powershell
    $p | Where-Object {$_.HandleCount -gt 500 } | Sort-Object HandleCount
    ```

    <span data-ttu-id="c715a-185">De volgende uitvoer wordt weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="c715a-185">The following output appears.</span></span>

    ```output
    Handles  NPM(K)  PM(K)  WS(K)  VS(M)  CPU(s)  Id   ProcessName
    -------  ------  -----  -----  -----  ------  --   ----------
    568      14      2164   4972   39     5.55    824  svchost
    716       7      2080   5332   28    25.38    468  csrss
    761      21      33060  56608  440  393.56    3300 WINWORD
    791      71      7412   4540   59     3.31    492  winlogon
    ...
    ```

7. <span data-ttu-id="c715a-186">Gebruik de `Get-Member` cmdlet om de eigenschappen weer te geven die beschikbaar zijn voor elk proces.</span><span class="sxs-lookup"><span data-stu-id="c715a-186">Use the `Get-Member` cmdlet to list the properties available for each process.</span></span>

    ```powershell
    $p | Get-Member -MemberType property
    ```

    ```output
        TypeName: System.Diagnostics.Process
    ```

    <span data-ttu-id="c715a-187">De volgende uitvoer wordt weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="c715a-187">The following output appears.</span></span>

    ```output
    Name                     MemberType Definition
    ----                     ---------- ----------
    BasePriority             Property   System.Int32 BasePriority {get;}
    Container                Property   System.ComponentModel.IContainer Conta...
    EnableRaisingEvents      Property   System.Boolean EnableRaisingEvents {ge...
    ...
    ```

## <a name="see-also"></a><span data-ttu-id="c715a-188">Zie ook</span><span class="sxs-lookup"><span data-stu-id="c715a-188">See Also</span></span>

[<span data-ttu-id="c715a-189">Een cmdlet maken voor het verwerken van de invoer van de opdracht regel</span><span class="sxs-lookup"><span data-stu-id="c715a-189">Creating a Cmdlet to Process Command Line Input</span></span>](./adding-parameters-that-process-command-line-input.md)

[<span data-ttu-id="c715a-190">Een cmdlet maken om de invoer van de pijp lijn te verwerken</span><span class="sxs-lookup"><span data-stu-id="c715a-190">Creating a Cmdlet to Process Pipeline Input</span></span>](./adding-parameters-that-process-pipeline-input.md)

[<span data-ttu-id="c715a-191">Een Windows Power shell-cmdlet maken</span><span class="sxs-lookup"><span data-stu-id="c715a-191">How to Create a Windows PowerShell Cmdlet</span></span>](/powershell/scripting/developer/cmdlet/writing-a-windows-powershell-cmdlet)

<span data-ttu-id="c715a-192">[Object typen en-opmaak uitbreiden](/previous-versions//ms714665(v=vs.85))</span><span class="sxs-lookup"><span data-stu-id="c715a-192">[Extending Object Types and Formatting](/previous-versions//ms714665(v=vs.85))</span></span>

<span data-ttu-id="c715a-193">[Hoe Windows Power shell werkt](/previous-versions//ms714658(v=vs.85))</span><span class="sxs-lookup"><span data-stu-id="c715a-193">[How Windows PowerShell Works](/previous-versions//ms714658(v=vs.85))</span></span>

<span data-ttu-id="c715a-194">[Cmdlets, providers en hosttoepassingen registreren](/previous-versions//ms714644(v=vs.85))</span><span class="sxs-lookup"><span data-stu-id="c715a-194">[How to Register Cmdlets, Providers, and Host Applications](/previous-versions//ms714644(v=vs.85))</span></span>

[<span data-ttu-id="c715a-195">Naslaginformatie over Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="c715a-195">Windows PowerShell Reference</span></span>](../windows-powershell-reference.md)

[<span data-ttu-id="c715a-196">Cmdlet-voorbeelden</span><span class="sxs-lookup"><span data-stu-id="c715a-196">Cmdlet Samples</span></span>](./cmdlet-samples.md)
