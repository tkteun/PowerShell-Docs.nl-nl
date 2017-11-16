---
ms.date: 2017-06-12
author: JKeithB
ms.topic: reference
keywords: WMF, powershell, setup
title: Oplossingen voor problemen in WMF 5.1
ms.openlocfilehash: 137095f50f9f926d3488ff9c1ce8270ddbda63eb
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 06/12/2017
---
# <a name="bug-fixes-in-wmf-51"></a><span data-ttu-id="33e61-103">Oplossingen voor problemen in WMF 5.1#</span><span class="sxs-lookup"><span data-stu-id="33e61-103">Bug Fixes in WMF 5.1#</span></span>

## <a name="bug-fixes"></a><span data-ttu-id="33e61-104">Oplossingen voor problemen</span><span class="sxs-lookup"><span data-stu-id="33e61-104">Bug fixes</span></span> ##

<span data-ttu-id="33e61-105">De volgende opmerkelijke fouten zijn verholpen in WMF 5.1:</span><span class="sxs-lookup"><span data-stu-id="33e61-105">The following notable bugs are fixed in WMF 5.1:</span></span>

### <a name="module-auto-discovery-fully-honors-envpsmodulepath"></a><span data-ttu-id="33e61-106">Automatische detectie van module respecteert volledig`$env:PSModulePath`</span><span class="sxs-lookup"><span data-stu-id="33e61-106">Module auto-discovery fully honors `$env:PSModulePath`</span></span> ###

<span data-ttu-id="33e61-107">Module auto-discovery (modules laden zonder een expliciete Import-Module bij het aanroepen van een opdracht automatisch) is geïntroduceerd in WMF 3.</span><span class="sxs-lookup"><span data-stu-id="33e61-107">Module auto-discovery (loading modules automatically without an explicit Import-Module when calling a command) was introduced in WMF 3.</span></span> <span data-ttu-id="33e61-108">Wanneer geïntroduceerd, PowerShell gecontroleerd voor opdrachten in `$PSHome\Modules` voordat u `$env:PSModulePath`.</span><span class="sxs-lookup"><span data-stu-id="33e61-108">When introduced, PowerShell checked for commands in `$PSHome\Modules` before using `$env:PSModulePath`.</span></span>

<span data-ttu-id="33e61-109">Dit gedrag te houden van WMF 5.1 gewijzigd `$env:PSModulePath` volledig.</span><span class="sxs-lookup"><span data-stu-id="33e61-109">WMF 5.1 changes this behavior to honor `$env:PSModulePath` completely.</span></span> <span data-ttu-id="33e61-110">Hiermee kunt u een door de gebruiker opgestelde module die wordt gedefinieerd door PowerShell-opdrachten (bijvoorbeeld `Get-ChildItem`) automatisch geladen en de ingebouwde opdracht correct te overschrijven.</span><span class="sxs-lookup"><span data-stu-id="33e61-110">This allows for a user-authored module that defines commands provided by PowerShell (e.g. `Get-ChildItem`) to be auto-loaded and correctly overriding the built-in command.</span></span>

### <a name="file-redirection-no-longer-hard-codes--encoding-unicode"></a><span data-ttu-id="33e61-111">Omleiding van bestand geen langer harde-codes`-Encoding Unicode`</span><span class="sxs-lookup"><span data-stu-id="33e61-111">File redirection no longer hard-codes `-Encoding Unicode`</span></span> ###

<span data-ttu-id="33e61-112">In alle eerdere versies van PowerShell is het onmogelijk om te bepalen de bestandscodering gebruikt door de omleidingsoperator van bestand bijvoorbeeld `Get-ChildItem > out.txt` omdat PowerShell toegevoegd `-Encoding Unicode`.</span><span class="sxs-lookup"><span data-stu-id="33e61-112">In all previous versions of PowerShell, it was impossible to control the file encoding used by the file redirection operator, e.g. `Get-ChildItem > out.txt` because PowerShell added `-Encoding Unicode`.</span></span>

<span data-ttu-id="33e61-113">Beginnen met WMF 5.1, kunt u nu wijzigen de bestandscodering van omleiding door in te stellen `$PSDefaultParameterValues`:</span><span class="sxs-lookup"><span data-stu-id="33e61-113">Starting with WMF 5.1, you can now change the file encoding of redirection by setting `$PSDefaultParameterValues`:</span></span>

```
$PSDefaultParameterValues["Out-File:Encoding"] = "Ascii"
```

### <a name="fixed-a-regression-in-accessing-members-of-systemreflectiontypeinfo"></a><span data-ttu-id="33e61-114">Een regressie bij het openen van de leden van vast`System.Reflection.TypeInfo`</span><span class="sxs-lookup"><span data-stu-id="33e61-114">Fixed a regression in accessing members of `System.Reflection.TypeInfo`</span></span> ###

<span data-ttu-id="33e61-115">Een regressie geïntroduceerd in WMF 5.0 heeft toegang tot leden van `System.Reflection.RuntimeType`, bijvoorbeeld `[int].ImplementedInterfaces`.</span><span class="sxs-lookup"><span data-stu-id="33e61-115">A regression introduced in WMF 5.0 broke accessing members of `System.Reflection.RuntimeType`, e.g. `[int].ImplementedInterfaces`.</span></span>
<span data-ttu-id="33e61-116">Deze fout is verholpen in WMF 5.1.</span><span class="sxs-lookup"><span data-stu-id="33e61-116">This bug has been fixed in WMF 5.1.</span></span>


### <a name="fixed-some-issues-with-com-objects"></a><span data-ttu-id="33e61-117">Sommige problemen opgelost met COM-objecten</span><span class="sxs-lookup"><span data-stu-id="33e61-117">Fixed some issues with COM objects</span></span> ###

<span data-ttu-id="33e61-118">WMF 5.0 geïntroduceerd om een nieuw COM-binder voor aanroepen methoden op COM-objecten en toegang tot eigenschappen van de COM-objecten.</span><span class="sxs-lookup"><span data-stu-id="33e61-118">WMF 5.0 introduced a new COM binder for invoking methods on COM objects and accessing properties of COM objects.</span></span> <span data-ttu-id="33e61-119">Deze nieuwe binder prestaties aanzienlijk verbeterd, maar ook een aantal fouten die zijn vastgesteld in WMF 5.1 geïntroduceerd.</span><span class="sxs-lookup"><span data-stu-id="33e61-119">This new binder improved performance significantly but also introduced some bugs which have been fixed in WMF 5.1.</span></span>

#### <a name="argument-conversions-were-not-always-performed-correctly"></a><span data-ttu-id="33e61-120">Argument conversies zijn niet altijd correct worden uitgevoerd</span><span class="sxs-lookup"><span data-stu-id="33e61-120">Argument conversions were not always performed correctly</span></span> ####

<span data-ttu-id="33e61-121">In het volgende voorbeeld:</span><span class="sxs-lookup"><span data-stu-id="33e61-121">In the following example:</span></span>

```
$obj = New-Object -ComObject WScript.Shell
$obj.SendKeys([char]173)
```

<span data-ttu-id="33e61-122">De methode SendKeys verwacht een tekenreeks, maar PowerShell is niet geconverteerd de char naar een tekenreeks uitstellende geconverteerd naar een IDispatch::Invoke die VariantChangeType worden gebruikt voor de conversie, wat in dit voorbeeld leidde tot de sleutels '1', '7' en '3' in plaats daarvan verzenden van de verwachte Volume.Mute-sleutel.</span><span class="sxs-lookup"><span data-stu-id="33e61-122">The SendKeys method expects a string, but PowerShell did not convert the char to a string, deferring the conversion to IDispatch::Invoke, which uses VariantChangeType to do the conversion, which in this example resulted in sending the keys '1', '7', and '3' instead of the expected Volume.Mute key.</span></span>

#### <a name="enumerable-com-objects-not-always-handled-correctly"></a><span data-ttu-id="33e61-123">Inventariseerbare COM-objecten die niet altijd correct wordt afgehandeld</span><span class="sxs-lookup"><span data-stu-id="33e61-123">Enumerable COM objects not always handled correctly</span></span> ####

<span data-ttu-id="33e61-124">Normaal gesproken inventariseren meeste inventariseerbare objecten PowerShell, maar een regressie geïntroduceerd in WMF 5.0 voorkomen dat de opsomming van COM-objecten die als IEnumerable is geïmplementeerd.</span><span class="sxs-lookup"><span data-stu-id="33e61-124">PowerShell normally enumerates most enumerable objects, but a regression introduced in WMF 5.0 prevented the enumeration of COM objects that implement IEnumerable.</span></span>  <span data-ttu-id="33e61-125">Bijvoorbeeld:</span><span class="sxs-lookup"><span data-stu-id="33e61-125">For example:</span></span>

```
function Get-COMDictionary
{
    $d = New-Object -ComObject Scripting.Dictionary
    $d.Add('a', 2)
    $d.Add('b', 2)
    return $d
}

$x = Get-COMDictionary
```

<span data-ttu-id="33e61-126">In het bovenstaande voorbeeld geschreven WMF 5.0 onjuist de Scripting.Dictionary aan de pijplijn in plaats van het inventariseren van de sleutel/waarde-paren.</span><span class="sxs-lookup"><span data-stu-id="33e61-126">In the above example, WMF 5.0 incorrectly wrote the Scripting.Dictionary to the pipeline instead of enumerating the key/value pairs.</span></span>

<span data-ttu-id="33e61-127">Dit wijzigen adressen [uitgeven 1752224 op verbinding maken](https://connect.microsoft.com/PowerShell/feedback/details/1752224)</span><span class="sxs-lookup"><span data-stu-id="33e61-127">This change also addresses [issue 1752224 on Connect](https://connect.microsoft.com/PowerShell/feedback/details/1752224)</span></span>

### <a name="ordered-was-not-allowed-inside-classes"></a><span data-ttu-id="33e61-128">`[ordered]`is niet toegestaan in klassen</span><span class="sxs-lookup"><span data-stu-id="33e61-128">`[ordered]` was not allowed inside classes</span></span> ###

<span data-ttu-id="33e61-129">WMF 5.0 geïntroduceerd klassen met de validatie van het type letterlijke waarden in klassen gebruikt.</span><span class="sxs-lookup"><span data-stu-id="33e61-129">WMF 5.0 introduced classes with validation of type literals used in classes.</span></span>  
<span data-ttu-id="33e61-130">`[ordered]`ziet eruit als een letterlijke waarde van het type, maar is niet een waar .NET-type.</span><span class="sxs-lookup"><span data-stu-id="33e61-130">`[ordered]` looks like a type literal but is not a true .NET type.</span></span> <span data-ttu-id="33e61-131">WMF 5.0 onjuist heeft een fout gerapporteerd op `[ordered]` binnen een klasse:</span><span class="sxs-lookup"><span data-stu-id="33e61-131">WMF 5.0 incorrectly reported an error on `[ordered]` inside a class:</span></span>

```
class CThing
{
    [object] foo($i)
    {
        [ordered]@{ Thing = $i }
    }
}
```


### <a name="help-on-about-topics-with-multiple-versions-does-not-work"></a><span data-ttu-id="33e61-132">Help-informatie op over onderwerpen met meerdere versies werkt niet</span><span class="sxs-lookup"><span data-stu-id="33e61-132">Help on About topics with multiple versions does not work</span></span> ###

<span data-ttu-id="33e61-133">Voordat u WMF 5.1, als u meerdere versies van een module geïnstalleerd had en ze allemaal een help-onderwerp bijvoorbeeld gedeeld about_PSReadline, `help about_PSReadline` meerdere onderwerpen met geen duidelijke manier waarmee u de echte help zou retourneren.</span><span class="sxs-lookup"><span data-stu-id="33e61-133">Before WMF 5.1, if you had multiple versions of a module installed and they all shared a help topic, for example, about_PSReadline, `help about_PSReadline` would return multiple topics with no obvious way to view the real help.</span></span>

<span data-ttu-id="33e61-134">WMF 5.1 corrigeert dit door te retourneren van de help voor de nieuwste versie van het onderwerp.</span><span class="sxs-lookup"><span data-stu-id="33e61-134">WMF 5.1 fixes this by returning the help for the latest version of the topic.</span></span>

<span data-ttu-id="33e61-135">`Get-Help`biedt geen manier om op te geven welke versie u hulp wilt.</span><span class="sxs-lookup"><span data-stu-id="33e61-135">`Get-Help` does not provide a way to specify which version you want help for.</span></span> <span data-ttu-id="33e61-136">Om dit te voorkomen, navigeer naar de map modules en de hulp rechtstreeks met een hulpprogramma zoals uw favoriete editor weergeven.</span><span class="sxs-lookup"><span data-stu-id="33e61-136">To work around this, navigate to the modules directory and view the help directly with a tool like your favorite editor.</span></span> 

### <a name="powershellexe-reading-from-stdin-stopped-working"></a><span data-ttu-id="33e61-137">lezen van STDIN PowerShell.exe werkt niet</span><span class="sxs-lookup"><span data-stu-id="33e61-137">powershell.exe reading from STDIN stopped working</span></span>

<span data-ttu-id="33e61-138">Klanten gebruiken `powershell -command -` van systeemeigen apps uit te voeren PowerShell doorgeeft in het script via STDIN helaas dit is verbroken vanwege een andere wijzigingen van de console-host.</span><span class="sxs-lookup"><span data-stu-id="33e61-138">Customers use `powershell -command -` from native apps to execute PowerShell passing in the script via STDIN unfortunately this was broken due to other changes it the console host.</span></span>

<span data-ttu-id="33e61-139">https://WindowsServer.uservoice.com/forums/301869-PowerShell/Suggestions/15854689-PowerShell-exe-Command-is-broken-on-Windows-10</span><span class="sxs-lookup"><span data-stu-id="33e61-139">https://windowsserver.uservoice.com/forums/301869-powershell/suggestions/15854689-powershell-exe-command-is-broken-on-windows-10</span></span>

### <a name="powershellexe-creates-spike-in-cpu-usage-on-startup"></a><span data-ttu-id="33e61-140">PowerShell.exe maakt piek in CPU-gebruik bij het opstarten</span><span class="sxs-lookup"><span data-stu-id="33e61-140">powershell.exe creates spike in CPU usage on startup</span></span>

<span data-ttu-id="33e61-141">PowerShell maakt gebruik van een WMI-query om te controleren of het via Groepsbeleid om te voorkomen dat de vertraging veroorzaakt in de aanmelding is gestart.</span><span class="sxs-lookup"><span data-stu-id="33e61-141">PowerShell uses a WMI query to check if it was started via Group Policy to avoid causing delay in login.</span></span>
<span data-ttu-id="33e61-142">De WMI-query belandt tzres.mui.dll injecteren in elk proces op het systeem omdat de Win32_Process WMI-klasse probeert op te halen van de lokale tijdzone-informatie.</span><span class="sxs-lookup"><span data-stu-id="33e61-142">The WMI query ends up injecting tzres.mui.dll into every process on the system since the WMI Win32_Process class attempts to retrieve local timezone information.</span></span>
<span data-ttu-id="33e61-143">Dit resulteert in een grote CPU piek in de wmiprvse (de WMI-provider host).</span><span class="sxs-lookup"><span data-stu-id="33e61-143">This results in a large CPU spike in wmiprvse (the WMI provider host).</span></span>
<span data-ttu-id="33e61-144">FIX is het gebruik van Win32-API-aanroepen dezelfde informatie in plaats van WMI ophalen.</span><span class="sxs-lookup"><span data-stu-id="33e61-144">Fix is to use Win32 API calls to get the same information instead of using WMI.</span></span>

