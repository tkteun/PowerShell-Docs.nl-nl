---
ms.date: 06/12/2017
ms.topic: conceptual
keywords: wmf,powershell,installeren
title: Oplossingen voor bugs in WMF 5.1
ms.openlocfilehash: 8edf295eb6304dc04de2fa5d3792b1c2fc4b01f3
ms.sourcegitcommit: 0a6b562a497860caadba754c75a83215315d37a1
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 09/19/2019
ms.locfileid: "71145206"
---
# <a name="bug-fixes-in-wmf-51"></a><span data-ttu-id="5a7aa-103">Oplossingen voor bugs in WMF 5.1</span><span class="sxs-lookup"><span data-stu-id="5a7aa-103">Bug Fixes in WMF 5.1</span></span>

## <a name="bug-fixes"></a><span data-ttu-id="5a7aa-104">Opgeloste fouten</span><span class="sxs-lookup"><span data-stu-id="5a7aa-104">Bug fixes</span></span>

<span data-ttu-id="5a7aa-105">De volgende belang rijke fouten zijn opgelost in WMF 5,1:</span><span class="sxs-lookup"><span data-stu-id="5a7aa-105">The following notable bugs are fixed in WMF 5.1:</span></span>

### <a name="module-auto-discovery-fully-honors-psmodulepath"></a><span data-ttu-id="5a7aa-106">Automatische detectie van module honoreert PSModulePath volledig</span><span class="sxs-lookup"><span data-stu-id="5a7aa-106">Module auto-discovery fully honors PSModulePath</span></span>

<span data-ttu-id="5a7aa-107">Module-automatische detectie (modules automatisch laden zonder expliciete import-module bij het aanroepen van een opdracht) werd geïntroduceerd in WMF 3.</span><span class="sxs-lookup"><span data-stu-id="5a7aa-107">Module auto-discovery (loading modules automatically without an explicit Import-Module when calling a command) was introduced in WMF 3.</span></span> <span data-ttu-id="5a7aa-108">Power shell is ingecheckt voor opdrachten `$PSHome\Modules` in voordat `$env:PSModulePath`u gaat gebruiken.</span><span class="sxs-lookup"><span data-stu-id="5a7aa-108">When introduced, PowerShell checked for commands in `$PSHome\Modules` before using `$env:PSModulePath`.</span></span>

<span data-ttu-id="5a7aa-109">WMF 5,1 wijzigt dit gedrag `$env:PSModulePath` volledig.</span><span class="sxs-lookup"><span data-stu-id="5a7aa-109">WMF 5.1 changes this behavior to honor `$env:PSModulePath` completely.</span></span> <span data-ttu-id="5a7aa-110">Dit maakt het mogelijk voor een door de gebruiker gemaakte module waarmee opdrachten worden gedefinieerd die worden verschaft `Get-ChildItem`door Power shell (bijvoorbeeld) om automatisch te worden geladen en de ingebouwde opdracht correct te vervangen.</span><span class="sxs-lookup"><span data-stu-id="5a7aa-110">This allows for a user-authored module that defines commands provided by PowerShell (e.g. `Get-ChildItem`) to be auto-loaded and correctly overriding the built-in command.</span></span>

### <a name="file-redirection-no-longer-hard-codes--encoding-unicode"></a><span data-ttu-id="5a7aa-111">Bestands omleiding heeft geen vaste codes meer-Unicode-code ring</span><span class="sxs-lookup"><span data-stu-id="5a7aa-111">File redirection no longer hard-codes -Encoding Unicode</span></span>

<span data-ttu-id="5a7aa-112">In alle eerdere versies van Power shell was het onmogelijk om de bestands codering te beheren die wordt gebruikt door de omleidings operator voor bestanden.</span><span class="sxs-lookup"><span data-stu-id="5a7aa-112">In all previous versions of PowerShell, it was impossible to control the file encoding used by the file redirection operator.</span></span>

<span data-ttu-id="5a7aa-113">Vanaf de WMF 5,1 kunt u nu de bestands codering van de omleiding wijzigen door de instelling `$PSDefaultParameterValues`:</span><span class="sxs-lookup"><span data-stu-id="5a7aa-113">Starting with WMF 5.1, you can now change the file encoding of redirection by setting `$PSDefaultParameterValues`:</span></span>

```powershell
$PSDefaultParameterValues["Out-File:Encoding"] = "Ascii"
```

### <a name="fixed-a-regression-in-accessing-members-of-systemreflectiontypeinfo"></a><span data-ttu-id="5a7aa-114">Er is een regressie voor het openen van leden van System. reflectie. type info opgelost</span><span class="sxs-lookup"><span data-stu-id="5a7aa-114">Fixed a regression in accessing members of System.Reflection.TypeInfo</span></span>

<span data-ttu-id="5a7aa-115">Een regressie geïntroduceerd in WMF 5,0 om toegang te krijgen tot `System.Reflection.RuntimeType`leden van, `[int].ImplementedInterfaces`bijvoorbeeld.</span><span class="sxs-lookup"><span data-stu-id="5a7aa-115">A regression introduced in WMF 5.0 broke accessing members of `System.Reflection.RuntimeType`, for example, `[int].ImplementedInterfaces`.</span></span> <span data-ttu-id="5a7aa-116">Deze fout is opgelost in WMF 5,1.</span><span class="sxs-lookup"><span data-stu-id="5a7aa-116">This bug has been fixed in WMF 5.1.</span></span>

### <a name="fixed-some-issues-with-com-objects"></a><span data-ttu-id="5a7aa-117">Er zijn problemen opgelost met COM-objecten</span><span class="sxs-lookup"><span data-stu-id="5a7aa-117">Fixed some issues with COM objects</span></span>

<span data-ttu-id="5a7aa-118">WMF 5,0 heeft een nieuwe COM-Binder geïntroduceerd voor het aanroepen van methoden voor COM-objecten en het openen van eigenschappen van COM-objecten.</span><span class="sxs-lookup"><span data-stu-id="5a7aa-118">WMF 5.0 introduced a new COM binder for invoking methods on COM objects and accessing properties of COM objects.</span></span> <span data-ttu-id="5a7aa-119">Deze nieuwe Binder verbetert de prestaties aanzienlijk, maar heeft ook een aantal bugs geïntroduceerd die zijn verholpen in WMF 5,1.</span><span class="sxs-lookup"><span data-stu-id="5a7aa-119">This new binder improved performance significantly but also introduced some bugs which have been fixed in WMF 5.1.</span></span>

#### <a name="argument-conversions-were-not-always-performed-correctly"></a><span data-ttu-id="5a7aa-120">Argument conversies zijn niet altijd correct uitgevoerd</span><span class="sxs-lookup"><span data-stu-id="5a7aa-120">Argument conversions were not always performed correctly</span></span>

<span data-ttu-id="5a7aa-121">In het volgende voor beeld:</span><span class="sxs-lookup"><span data-stu-id="5a7aa-121">In the following example:</span></span>

```powershell
$obj = New-Object -ComObject WScript.Shell
$obj.SendKeys([char]173)
```

<span data-ttu-id="5a7aa-122">De methode **SendKeys** verwacht een teken reeks, maar Power Shell heeft het teken niet omgezet naar een teken reeks, waardoor de conversie naar **IDispatch:: Invoke**wordt uitgesteld, waarbij **VariantChangeType** wordt gebruikt om de conversie uit te voeren.</span><span class="sxs-lookup"><span data-stu-id="5a7aa-122">The **SendKeys** method expects a string, but PowerShell did not convert the char to a string, deferring the conversion to **IDispatch::Invoke**, which uses **VariantChangeType** to do the conversion.</span></span> <span data-ttu-id="5a7aa-123">In dit voor beeld heeft dit ertoe geleid dat de sleutels ' 1 ', ' 7 ' en ' 3 ' worden verzonden in plaats van het verwachte **volume. Mute** -sleutel.</span><span class="sxs-lookup"><span data-stu-id="5a7aa-123">In this example, this resulted in sending the keys '1', '7', and '3' instead of the expected **Volume.Mute** key.</span></span>

#### <a name="enumerable-com-objects-not-always-handled-correctly"></a><span data-ttu-id="5a7aa-124">Het inventariseren van COM-objecten wordt niet altijd correct verwerkt</span><span class="sxs-lookup"><span data-stu-id="5a7aa-124">Enumerable COM objects not always handled correctly</span></span>

<span data-ttu-id="5a7aa-125">Power shell inventariseert normaal gesp roken de meeste overzichts objecten, maar een regressie geïntroduceerd in WMF 5,0 heeft de inventarisatie van COM-objecten die IEnumerable implementeren, voor komen.</span><span class="sxs-lookup"><span data-stu-id="5a7aa-125">PowerShell normally enumerates most enumerable objects, but a regression introduced in WMF 5.0 prevented the enumeration of COM objects that implement IEnumerable.</span></span> <span data-ttu-id="5a7aa-126">Bijvoorbeeld:</span><span class="sxs-lookup"><span data-stu-id="5a7aa-126">For example:</span></span>

```powershell
function Get-COMDictionary
{
    $d = New-Object -ComObject Scripting.Dictionary
    $d.Add('a', 2)
    $d.Add('b', 2)
    return $d
}

$x = Get-COMDictionary
```

<span data-ttu-id="5a7aa-127">In het bovenstaande voor beeld heeft WMF 5,0 de **Scripting. Dictionary** onjuist geschreven in de pijp lijn in plaats van de sleutel-waardeparen te inventariseren.</span><span class="sxs-lookup"><span data-stu-id="5a7aa-127">In the above example, WMF 5.0 incorrectly wrote the **Scripting.Dictionary** to the pipeline instead of enumerating the key/value pairs.</span></span>

### <a name="ordered-was-not-allowed-inside-classes"></a><span data-ttu-id="5a7aa-128">[gelast] is niet toegestaan binnen klassen</span><span class="sxs-lookup"><span data-stu-id="5a7aa-128">[ordered] was not allowed inside classes</span></span>

<span data-ttu-id="5a7aa-129">WMF 5,0 heeft klassen met validatie van type letterlijke waarden in klassen geïntroduceerd.</span><span class="sxs-lookup"><span data-stu-id="5a7aa-129">WMF 5.0 introduced classes with validation of type literals used in classes.</span></span> <span data-ttu-id="5a7aa-130">`[ordered]`het lijkt op een letterlijke type, maar is geen echt .NET-type.</span><span class="sxs-lookup"><span data-stu-id="5a7aa-130">`[ordered]` looks like a type literal but is not a true .NET type.</span></span> <span data-ttu-id="5a7aa-131">WMF 5,0 heeft foutief een fout `[ordered]` gerapporteerd binnen een klasse:</span><span class="sxs-lookup"><span data-stu-id="5a7aa-131">WMF 5.0 incorrectly reported an error on `[ordered]` inside a class:</span></span>

```powershell
class CThing
{
    [object] foo($i)
    {
        [ordered]@{ Thing = $i }
    }
}
```

### <a name="help-on-about-topics-with-multiple-versions-does-not-work"></a><span data-ttu-id="5a7aa-132">Help-informatie over onderwerpen met meerdere versies werkt niet</span><span class="sxs-lookup"><span data-stu-id="5a7aa-132">Help on About topics with multiple versions does not work</span></span>

<span data-ttu-id="5a7aa-133">Als er meerdere versies van een module zijn geïnstalleerd, moet u vóór WMF 5,1 meerdere onderwerpen retour neren zonder een duidelijke manier om de werkelijke `help about_PSReadline` Help te bekijken, als u meer dan een Help-onderwerp, bijvoorbeeld about_PSReadline, gebruikt.</span><span class="sxs-lookup"><span data-stu-id="5a7aa-133">Before WMF 5.1, if you had multiple versions of a module installed and they all shared a help topic, for example, about_PSReadline, `help about_PSReadline` would return multiple topics with no obvious way to view the real help.</span></span>

<span data-ttu-id="5a7aa-134">WMF 5,1 corrigeert dit door de Help voor de meest recente versie van het onderwerp te retour neren.</span><span class="sxs-lookup"><span data-stu-id="5a7aa-134">WMF 5.1 fixes this by returning the help for the latest version of the topic.</span></span>

<span data-ttu-id="5a7aa-135">`Get-Help`biedt geen manier om de versie op te geven waarvoor u hulp nodig hebt.</span><span class="sxs-lookup"><span data-stu-id="5a7aa-135">`Get-Help` does not provide a way to specify which version you want help for.</span></span> <span data-ttu-id="5a7aa-136">Om dit te omzeilen, gaat u naar de map modules en bekijkt u de Help rechtstreeks met een hulp programma zoals uw favoriete editor.</span><span class="sxs-lookup"><span data-stu-id="5a7aa-136">To work around this, navigate to the modules directory and view the help directly with a tool like your favorite editor.</span></span>

### <a name="powershellexe-reading-from-stdin-stopped-working"></a><span data-ttu-id="5a7aa-137">het lezen van Power shell. exe van STDIN werkt niet meer</span><span class="sxs-lookup"><span data-stu-id="5a7aa-137">powershell.exe reading from STDIN stopped working</span></span>

<span data-ttu-id="5a7aa-138">Klanten gebruiken `powershell -command -` systeem eigen apps om Power shell uit te voeren in het script via stdin. Dit is helaas verbroken door andere wijzigingen in de console-host.</span><span class="sxs-lookup"><span data-stu-id="5a7aa-138">Customers use `powershell -command -` from native apps to execute PowerShell passing in the script via STDIN unfortunately this was broken by other changes in the console host.</span></span>

<span data-ttu-id="5a7aa-139">Dit probleem is opgelost in versie 5,1 van de jubileum update van Windows 10.</span><span class="sxs-lookup"><span data-stu-id="5a7aa-139">This is fixed for version 5.1 in the Windows 10 Anniversary Update.</span></span>

### <a name="powershellexe-creates-spike-in-cpu-usage-on-startup"></a><span data-ttu-id="5a7aa-140">Power shell. exe maakt pieken in het CPU-gebruik bij het opstarten</span><span class="sxs-lookup"><span data-stu-id="5a7aa-140">powershell.exe creates spike in CPU usage on startup</span></span>

<span data-ttu-id="5a7aa-141">Power shell gebruikt een WMI-query om te controleren of deze is gestart via groepsbeleid om te voor komen dat de aanmelding vertraging veroorzaakt.</span><span class="sxs-lookup"><span data-stu-id="5a7aa-141">PowerShell uses a WMI query to check if it was started via Group Policy to avoid causing delay in login.</span></span> <span data-ttu-id="5a7aa-142">De WMI-query beëindigt het injecteren van tzres. MUI. dll in elk proces op het systeem, omdat de WMI **Win32_Process** -klasse de lokale tijdzone gegevens probeert op te halen.</span><span class="sxs-lookup"><span data-stu-id="5a7aa-142">The WMI query ends up injecting tzres.mui.dll into every process on the system since the WMI **Win32_Process** class attempts to retrieve local timezone information.</span></span> <span data-ttu-id="5a7aa-143">Dit resulteert in een grote CPU-piek in **WMIPRVSE** (de host van de WMI-provider).</span><span class="sxs-lookup"><span data-stu-id="5a7aa-143">This results in a large CPU spike in **wmiprvse** (the WMI provider host).</span></span> <span data-ttu-id="5a7aa-144">Correctie is het gebruik van Win32 API-aanroepen om dezelfde informatie te verkrijgen in plaats van WMI te gebruiken.</span><span class="sxs-lookup"><span data-stu-id="5a7aa-144">Fix is to use Win32 API calls to get the same information instead of using WMI.</span></span>
