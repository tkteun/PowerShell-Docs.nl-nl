---
title: Conflicten met de assembly-afhankelijkheden van Power shell-modules oplossen
description: Bij het schrijven van een binaire Power shell-module in C# is het natuurlijk om afhankelijkheden te maken met andere pakketten of bibliotheken om functionaliteit te bieden.
ms.date: 06/25/2020
ms.custom: rjmholt
ms.openlocfilehash: 93bb39bdd440c7f97c27aa81e68f68331569b69e
ms.sourcegitcommit: 2fc6ee49a70bda4c59135136bd5cc7782836a124
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 11/18/2020
ms.locfileid: "94810399"
---
# <a name="resolving-powershell-module-assembly-dependency-conflicts"></a><span data-ttu-id="6ea33-103">Conflicten met de assembly-afhankelijkheden van Power shell-modules oplossen</span><span class="sxs-lookup"><span data-stu-id="6ea33-103">Resolving PowerShell module assembly dependency conflicts</span></span>

<span data-ttu-id="6ea33-104">Bij het schrijven van een binaire Power shell-module in C# is het natuurlijk om afhankelijkheden te maken met andere pakketten of bibliotheken om functionaliteit te bieden.</span><span class="sxs-lookup"><span data-stu-id="6ea33-104">When writing a binary PowerShell module in C#, it's natural to take dependencies on other packages or libraries to provide functionality.</span></span> <span data-ttu-id="6ea33-105">Het nemen van afhankelijkheden op andere bibliotheken is wenselijk voor het hergebruik van code.</span><span class="sxs-lookup"><span data-stu-id="6ea33-105">Taking dependencies on other libraries is desirable for code reuse.</span></span> <span data-ttu-id="6ea33-106">Power shell laadt altijd assembly's in dezelfde context.</span><span class="sxs-lookup"><span data-stu-id="6ea33-106">PowerShell always loads assemblies into the same context.</span></span> <span data-ttu-id="6ea33-107">Dit geeft problemen wanneer de afhankelijkheden van een module conflicteren met reeds geladen Dll's en kunnen verhinderen dat er twee anderszins niet-gerelateerde modules worden gebruikt in dezelfde Power shell-sessie.</span><span class="sxs-lookup"><span data-stu-id="6ea33-107">This presents issues when a module's dependencies conflict with already-loaded DLLs and may prevent using two otherwise unrelated modules in the same PowerShell session.</span></span>

<span data-ttu-id="6ea33-108">Als u dit probleem hebt gehad, ziet u een fout bericht als volgt:</span><span class="sxs-lookup"><span data-stu-id="6ea33-108">If you've had this problem, you've seen an error message like this:</span></span>

![Fout bericht bij conflict bij het laden van assembly](./media/resolving-dependency-conflicts/moduleconflict.png)

<span data-ttu-id="6ea33-110">In dit artikel vindt u een aantal manieren waarop afhankelijkheids conflicten optreden in Power shell en manieren om problemen met afhankelijkheids conflicten te verhelpen.</span><span class="sxs-lookup"><span data-stu-id="6ea33-110">This article looks at some of the ways dependency conflicts occur in PowerShell and ways to mitigate dependency conflict issues.</span></span> <span data-ttu-id="6ea33-111">Zelfs als u geen module auteur bent, zijn er hier enkele trucs die u kunnen helpen bij het oplossen van afhankelijkheids conflicten in modules die u gebruikt.</span><span class="sxs-lookup"><span data-stu-id="6ea33-111">Even if you're not a module author, there are some tricks in here that might help you with dependency conflicts occurring in modules that you use.</span></span>

## <a name="why-do-dependency-conflicts-occur"></a><span data-ttu-id="6ea33-112">Waarom vinden afhankelijkheids conflicten plaats?</span><span class="sxs-lookup"><span data-stu-id="6ea33-112">Why do dependency conflicts occur?</span></span>

<span data-ttu-id="6ea33-113">In .NET treden afhankelijkheids conflicten op wanneer twee versies van dezelfde assembly worden geladen in dezelfde _Assembly-laad context_.</span><span class="sxs-lookup"><span data-stu-id="6ea33-113">In .NET, dependency conflicts occur when two versions of the same assembly are loaded into the same _Assembly Load Context_.</span></span> <span data-ttu-id="6ea33-114">Deze term betekent iets anders op verschillende .NET-platformen, die [later](#powershell-and-net)worden besproken.</span><span class="sxs-lookup"><span data-stu-id="6ea33-114">This term means slightly different things on different .NET platforms, which is covered [later](#powershell-and-net).</span></span> <span data-ttu-id="6ea33-115">Dit conflict is een veelvoorkomend probleem dat zich voordoet in software waarvoor versie afhankelijke afhankelijkheden worden gebruikt.</span><span class="sxs-lookup"><span data-stu-id="6ea33-115">This conflict is a common problem that occurs in any software where versioned dependencies are used.</span></span> <span data-ttu-id="6ea33-116">Omdat er geen eenvoudige oplossingen zijn, en omdat veel afhankelijkheids modellen het probleem op verschillende manieren proberen op te lossen, wordt deze situatie vaak ' afhankelijkheids Hell ' genoemd.</span><span class="sxs-lookup"><span data-stu-id="6ea33-116">Because there are no simple solutions, and because many dependency-resolution frameworks try to solve the problem in different ways, this situation is often called "dependency hell".</span></span>

<span data-ttu-id="6ea33-117">Conflict problemen worden samengesteld op basis van het feit dat een project bijna nooit opzettelijk of rechtstreeks afhankelijk is van twee versies van dezelfde afhankelijkheid.</span><span class="sxs-lookup"><span data-stu-id="6ea33-117">Conflict issues are compounded by the fact that a project almost never deliberately or directly depends on two versions of the same dependency.</span></span> <span data-ttu-id="6ea33-118">In plaats daarvan heeft het project twee of meer afhankelijkheden waarvoor elk een andere versie van dezelfde afhankelijkheid nodig is.</span><span class="sxs-lookup"><span data-stu-id="6ea33-118">Instead, the project has two or more dependencies that each require a different version of the same dependency.</span></span>

<span data-ttu-id="6ea33-119">Stel bijvoorbeeld dat uw .NET-toepassing, `DuckBuilder` met twee afhankelijkheden, een deel van de functionaliteit kan uitvoeren en er als volgt uitziet:</span><span class="sxs-lookup"><span data-stu-id="6ea33-119">For example, say your .NET application, `DuckBuilder`, brings in two dependencies, to perform parts of its functionality and looks like this:</span></span>

![Twee afhankelijkheden van DuckBuilder zijn afhankelijk van verschillende versies van Newtonsoft.Jsop](./media/resolving-dependency-conflicts/dep-conflict.jpg)

<span data-ttu-id="6ea33-121">Omdat `Contoso.ZipTools` en `Fabrikam.FileHelpers` beide afhankelijk zijn van verschillende versies van `Newtonsoft.Json` , is er mogelijk een afhankelijkheids conflict afhankelijk van hoe elke afhankelijkheid wordt geladen.</span><span class="sxs-lookup"><span data-stu-id="6ea33-121">Because `Contoso.ZipTools` and `Fabrikam.FileHelpers` both depend on different versions of `Newtonsoft.Json`, there may be a dependency conflict depending on how each dependency is loaded.</span></span>

### <a name="conflicting-with-powershells-dependencies"></a><span data-ttu-id="6ea33-122">Conflicterende met de afhankelijkheden van Power shell</span><span class="sxs-lookup"><span data-stu-id="6ea33-122">Conflicting with PowerShell's dependencies</span></span>

<span data-ttu-id="6ea33-123">In Power shell wordt het conflict met afhankelijkheids conflicten verg root omdat Power shell-modules en eigen afhankelijkheden van Power shell in dezelfde gedeelde context worden geladen.</span><span class="sxs-lookup"><span data-stu-id="6ea33-123">In PowerShell, the dependency conflict issue is magnified because PowerShell modules and PowerShell's own dependencies are loaded into the same shared context.</span></span> <span data-ttu-id="6ea33-124">Dit betekent dat de Power shell-engine en alle geladen Power shell-modules geen conflicterende afhankelijkheden hebben.</span><span class="sxs-lookup"><span data-stu-id="6ea33-124">This means the PowerShell engine and all loaded PowerShell modules must not have conflicting dependencies.</span></span> <span data-ttu-id="6ea33-125">Een klassiek voor beeld hiervan is `Newtonsoft.Json` :</span><span class="sxs-lookup"><span data-stu-id="6ea33-125">A classic example of this is `Newtonsoft.Json`:</span></span>

![De FictionalTools-module is afhankelijk van de nieuwere versie van Newtonsoft.Jsvan Power shell](./media/resolving-dependency-conflicts/engine-conflict.jpg)

<span data-ttu-id="6ea33-127">In dit voor beeld is de module `FictionalTools` afhankelijk van `Newtonsoft.Json` versie `12.0.3` , een nieuwere versie van `Newtonsoft.Json` `11.0.2` die in het voor beeld Power shell wordt geleverd.</span><span class="sxs-lookup"><span data-stu-id="6ea33-127">In this example, the module `FictionalTools` depends on `Newtonsoft.Json` version `12.0.3`, which is a newer version of `Newtonsoft.Json` than `11.0.2` that ships in the example PowerShell.</span></span>

> [!NOTE]
> <span data-ttu-id="6ea33-128">Dit is een voor beeld en Power shell 7 wordt momenteel geleverd met `Newtonsoft.Json 12.0.3` .</span><span class="sxs-lookup"><span data-stu-id="6ea33-128">This is an example and PowerShell 7 currently ships with `Newtonsoft.Json 12.0.3`.</span></span>

<span data-ttu-id="6ea33-129">Omdat de module afhankelijk is van een nieuwere versie van de assembly, wordt de versie die Power shell al heeft geladen, niet geaccepteerd.</span><span class="sxs-lookup"><span data-stu-id="6ea33-129">Because the module depends on a newer version of the assembly, it won't accept the version that PowerShell already has loaded.</span></span> <span data-ttu-id="6ea33-130">Maar omdat Power shell al een versie van de assembly heeft geladen, kan de module geen eigen versie laden met behulp van het conventionele laad mechanisme.</span><span class="sxs-lookup"><span data-stu-id="6ea33-130">But because PowerShell has already loaded a version of the assembly, the module can't load its own version using the conventional load mechanism.</span></span>

### <a name="conflicting-with-another-modules-dependencies"></a><span data-ttu-id="6ea33-131">Conflicterende met de afhankelijkheden van een andere module</span><span class="sxs-lookup"><span data-stu-id="6ea33-131">Conflicting with another module's dependencies</span></span>

<span data-ttu-id="6ea33-132">Een ander algemeen scenario in Power shell is dat een module wordt geladen die afhankelijk is van één versie van een assembly. vervolgens wordt een andere module geladen die afhankelijk is van een andere versie van de assembly.</span><span class="sxs-lookup"><span data-stu-id="6ea33-132">Another common scenario in PowerShell is that a module is loaded that depends on one version of an assembly, and then another module is loaded later that depends on a different version of that assembly.</span></span>

<span data-ttu-id="6ea33-133">Dit ziet er ongeveer als volgt uit:</span><span class="sxs-lookup"><span data-stu-id="6ea33-133">This often looks like the following:</span></span>

![Twee Power shell-modules vereisen verschillende versies van de micro soft. Extensions. logboek registratie afhankelijkheid](./media/resolving-dependency-conflicts/mod-conflict.jpg)

<span data-ttu-id="6ea33-135">In dit geval vereist de `FictionalTools` module een nieuwere versie van `Microsoft.Extensions.Logging` de `FilesystemManager` module.</span><span class="sxs-lookup"><span data-stu-id="6ea33-135">In this case, the `FictionalTools` module requires a newer version of `Microsoft.Extensions.Logging` than the `FilesystemManager` module.</span></span>

<span data-ttu-id="6ea33-136">Stel dat deze modules hun afhankelijkheden laden door de afhankelijkheids-assembly's in dezelfde map als de assembly van de hoofd module te plaatsen.</span><span class="sxs-lookup"><span data-stu-id="6ea33-136">Imagine these modules load their dependencies by placing the dependency assemblies in the same directory as the root module assembly.</span></span> <span data-ttu-id="6ea33-137">Hierdoor kan .NET deze impliciet op naam laden.</span><span class="sxs-lookup"><span data-stu-id="6ea33-137">This allows .NET to implicitly load them by name.</span></span> <span data-ttu-id="6ea33-138">Als Power shell 7 wordt uitgevoerd (boven op .NET Core 3,1), kunnen we laden en uitvoeren `FictionalTools` , vervolgens laden en uitvoeren `FilesystemManager` zonder problemen.</span><span class="sxs-lookup"><span data-stu-id="6ea33-138">If we're running PowerShell 7 (on top of .NET Core 3.1), we can load and run `FictionalTools`, then load and run `FilesystemManager` without issue.</span></span> <span data-ttu-id="6ea33-139">Als we in een nieuwe sessie echter laden en uitvoeren en `FilesystemManager` vervolgens laden, `FictionalTools` krijgen we een `FileLoadException` van de `FictionalTools` opdracht omdat er een nieuwere versie van is vereist `Microsoft.Extensions.Logging` dan de geladen.</span><span class="sxs-lookup"><span data-stu-id="6ea33-139">However, in a new session, if we load and run `FilesystemManager`, then load `FictionalTools`, we get a `FileLoadException` from the `FictionalTools` command because it requires a newer version of `Microsoft.Extensions.Logging` than the one loaded.</span></span>
<span data-ttu-id="6ea33-140">`FictionalTools` de benodigde versie kan niet worden geladen omdat er al een assembly met dezelfde naam is geladen.</span><span class="sxs-lookup"><span data-stu-id="6ea33-140">`FictionalTools` can't load the version needed because an assembly of the same name has already been loaded.</span></span>

## <a name="powershell-and-net"></a><span data-ttu-id="6ea33-141">Power shell en .NET</span><span class="sxs-lookup"><span data-stu-id="6ea33-141">PowerShell and .NET</span></span>

<span data-ttu-id="6ea33-142">Power shell wordt uitgevoerd op het .NET-platform.</span><span class="sxs-lookup"><span data-stu-id="6ea33-142">PowerShell runs on the .NET platform.</span></span> <span data-ttu-id="6ea33-143">NET is uiteindelijk verantwoordelijk voor het oplossen en laden van assembly-afhankelijkheden. Daarom moeten we weten hoe .NET hier wordt beschreven om afhankelijkheids conflicten te begrijpen.</span><span class="sxs-lookup"><span data-stu-id="6ea33-143">NET is ultimately responsible for resolving and loading assembly dependencies, so we must understand how .NET operates here to understand dependency conflicts.</span></span>

<span data-ttu-id="6ea33-144">We moeten ook het feit confront dat verschillende versies van Power shell worden uitgevoerd op verschillende .NET-implementaties.</span><span class="sxs-lookup"><span data-stu-id="6ea33-144">We must also confront the fact that different versions of PowerShell run on different .NET implementations.</span></span> <span data-ttu-id="6ea33-145">In het algemeen worden Power shell 5,1 en lager uitgevoerd op .NET Framework, terwijl Power shell 6 en hoger op .NET core worden uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="6ea33-145">In general, PowerShell 5.1 and below run on .NET Framework, while PowerShell 6 and above run on .NET Core.</span></span> <span data-ttu-id="6ea33-146">Deze twee implementaties van .NET laden en verwerken assembly's verschillend.</span><span class="sxs-lookup"><span data-stu-id="6ea33-146">These two implementations of .NET load and handle assemblies differently.</span></span>
<span data-ttu-id="6ea33-147">Dit betekent dat het oplossen van afhankelijkheids conflicten kan variëren, afhankelijk van het onderliggende .NET-platform.</span><span class="sxs-lookup"><span data-stu-id="6ea33-147">This means that resolving dependency conflicts can vary depending on the underlying .NET platform.</span></span>

### <a name="assembly-load-contexts"></a><span data-ttu-id="6ea33-148">Contexten assembly laden</span><span class="sxs-lookup"><span data-stu-id="6ea33-148">Assembly Load Contexts</span></span>

<span data-ttu-id="6ea33-149">In .NET is dit een _Assembly-laad context_ (ALC) die een runtime-naam ruimte is waarin de assembly's worden geladen.</span><span class="sxs-lookup"><span data-stu-id="6ea33-149">In .NET, an _Assembly Load Context_ (ALC) that is a runtime namespace into which assemblies are loaded.</span></span> <span data-ttu-id="6ea33-150">De namen van de assembly's moeten uniek zijn.</span><span class="sxs-lookup"><span data-stu-id="6ea33-150">The assemblies' names must be unique.</span></span> <span data-ttu-id="6ea33-151">In dit concept kunnen assembly's uniek worden omgezet op naam in elke ALC.</span><span class="sxs-lookup"><span data-stu-id="6ea33-151">This concept allows assemblies to be uniquely resolved by name in each ALC.</span></span>

### <a name="assembly-reference-loading-in-net"></a><span data-ttu-id="6ea33-152">Assembly-referentie laden in .NET</span><span class="sxs-lookup"><span data-stu-id="6ea33-152">Assembly reference loading in .NET</span></span>

<span data-ttu-id="6ea33-153">De semantiek van het laden van de assembly is afhankelijk van de .NET-implementatie (.NET Core versus .NET Framework) en de .NET API die wordt gebruikt om een bepaalde assembly te laden.</span><span class="sxs-lookup"><span data-stu-id="6ea33-153">The semantics of assembly loading depend on both the .NET implementation (.NET Core vs .NET Framework) and the .NET API used to load a particular assembly.</span></span> <span data-ttu-id="6ea33-154">In plaats van hier meer informatie te geven, zijn er koppelingen in de [verdere Lees](#further-reading) sectie die in het bijzonder worden uitgebreid over hoe .NET-assembly laden in elke .net-implementatie werkt.</span><span class="sxs-lookup"><span data-stu-id="6ea33-154">Rather than go into detail here, there are links in the [Further reading](#further-reading) section that go into great detail on how .NET assembly loading works in each .NET implementation.</span></span>

<span data-ttu-id="6ea33-155">In dit artikel wordt verwezen naar de volgende mechanismen:</span><span class="sxs-lookup"><span data-stu-id="6ea33-155">In this article we'll refer to the following mechanisms:</span></span>

- <span data-ttu-id="6ea33-156">Impliciet assembly wordt geladen (effectief `Assembly.Load(AssemblyName)` ), wanneer .net impliciet probeert een assembly te laden op naam uit een statische assembly-verwijzing in .net-code.</span><span class="sxs-lookup"><span data-stu-id="6ea33-156">Implicit assembly loading (effectively `Assembly.Load(AssemblyName)`), when .NET implicitly tries to load an assembly by name from a static assembly reference in .NET code.</span></span>
- <span data-ttu-id="6ea33-157">`Assembly.LoadFrom()`, een door de invoeg toepassing georiënteerde laad-API die handlers toevoegt voor het oplossen van afhankelijkheden van het geladen DLL-bestand.</span><span class="sxs-lookup"><span data-stu-id="6ea33-157">`Assembly.LoadFrom()`, a plugin-oriented loading API that adds handlers to resolve dependencies of the loaded DLL.</span></span> <span data-ttu-id="6ea33-158">Deze methode kan mogelijk de afhankelijkheden niet op de gewenste manier oplossen.</span><span class="sxs-lookup"><span data-stu-id="6ea33-158">This method may not resolve dependencies the way we want.</span></span>
- <span data-ttu-id="6ea33-159">`Assembly.LoadFile()`, een Basic-laad-API die bedoeld is voor het laden van alleen de assembly die wordt gevraagd en geen afhankelijkheden afhandelt.</span><span class="sxs-lookup"><span data-stu-id="6ea33-159">`Assembly.LoadFile()`, a basic loading API intended to load only the assembly asked for and does not handle any dependencies.</span></span>

### <a name="differences-in-net-framework-vs-net-core"></a><span data-ttu-id="6ea33-160">Verschillen in .NET Framework vs .NET core</span><span class="sxs-lookup"><span data-stu-id="6ea33-160">Differences in .NET Framework vs .NET Core</span></span>

<span data-ttu-id="6ea33-161">De manier waarop deze Api's werken, is gewijzigd op subtiele manieren tussen .NET core en .NET Framework, zodat het voor deel is dat u de opgenomen [koppelingen](#further-reading)kunt lezen.</span><span class="sxs-lookup"><span data-stu-id="6ea33-161">The way these APIs work has changed in subtle ways between .NET Core and .NET Framework, so it's worth reading through the included [links](#further-reading).</span></span> <span data-ttu-id="6ea33-162">Het is belang rijk dat contexten voor assembly-belasting en andere mechanismen voor de oplossing van de assembly zijn gewijzigd tussen .NET Framework en .NET core.</span><span class="sxs-lookup"><span data-stu-id="6ea33-162">Importantly, Assembly Load Contexts and other assembly resolution mechanisms have changed between .NET Framework and .NET Core.</span></span>

<span data-ttu-id="6ea33-163">Met name .NET Framework heeft de volgende functies:</span><span class="sxs-lookup"><span data-stu-id="6ea33-163">In particular, .NET Framework has the following features:</span></span>

- <span data-ttu-id="6ea33-164">De globale assembly-cache, voor de oplossing van de assembly voor alle computers</span><span class="sxs-lookup"><span data-stu-id="6ea33-164">The Global Assembly Cache, for machine-wide assembly resolution</span></span>
- <span data-ttu-id="6ea33-165">Toepassings domeinen, die in sandboxes in het proces worden gebruikt voor de isolatie van de assembly, maar die ook een serializion-laag aan concurreren geven met</span><span class="sxs-lookup"><span data-stu-id="6ea33-165">Application Domains, which work like in-process sandboxes for assembly isolation, but also present a serialization layer to contend with</span></span>
- <span data-ttu-id="6ea33-166">Een beperkt context model voor het laden van de assembly, waarin [hier](/dotnet/framework/deployment/best-practices-for-assembly-loading)dieper wordt uitgelegd, met een vaste verzameling van assembly-laad contexten, elk met hun eigen gedrag:</span><span class="sxs-lookup"><span data-stu-id="6ea33-166">A limited assembly load context model, explained in depth [here](/dotnet/framework/deployment/best-practices-for-assembly-loading), that has a fixed set of assembly load contexts, each with their own behavior:</span></span>
  - <span data-ttu-id="6ea33-167">De standaard laad context, waar assembly's standaard worden geladen</span><span class="sxs-lookup"><span data-stu-id="6ea33-167">The default load context, where assemblies are loaded by default</span></span>
  - <span data-ttu-id="6ea33-168">De context van laden voor het hand matig laden van assembly's tijdens runtime</span><span class="sxs-lookup"><span data-stu-id="6ea33-168">The load-from context, for loading assemblies manually at runtime</span></span>
  - <span data-ttu-id="6ea33-169">De alleen-reflectie context, voor het veilig laden van assembly's om de meta gegevens te lezen zonder ze uit te voeren</span><span class="sxs-lookup"><span data-stu-id="6ea33-169">The reflection-only context, for safely loading assemblies to read their metadata without running them</span></span>
  - <span data-ttu-id="6ea33-170">De verwarrende void dat assembly's zijn geladen met `Assembly.LoadFile(string path)` en `Assembly.Load(byte[] asmBytes)` Live in</span><span class="sxs-lookup"><span data-stu-id="6ea33-170">The mysterious void that assemblies loaded with `Assembly.LoadFile(string path)` and `Assembly.Load(byte[] asmBytes)` live in</span></span>

<span data-ttu-id="6ea33-171">.NET core (en .NET 5 +) heeft deze complexiteit vervangen door een eenvoudiger model:</span><span class="sxs-lookup"><span data-stu-id="6ea33-171">.NET Core (and .NET 5+) has replaced this complexity with a simpler model:</span></span>

- <span data-ttu-id="6ea33-172">Geen globale assembly-cache.</span><span class="sxs-lookup"><span data-stu-id="6ea33-172">No Global Assembly Cache.</span></span> <span data-ttu-id="6ea33-173">Toepassingen nemen al hun eigen afhankelijkheden.</span><span class="sxs-lookup"><span data-stu-id="6ea33-173">Applications bring all their own dependencies.</span></span> <span data-ttu-id="6ea33-174">Hiermee verwijdert u een externe factor voor de oplossing van afhankelijkheden in toepassingen, waardoor het maken van afhankelijkheids oplossingen betrouwbaarder wordt.</span><span class="sxs-lookup"><span data-stu-id="6ea33-174">This removes an external factor for dependency resolution in applications, making dependency resolution more reproducible.</span></span>
  <span data-ttu-id="6ea33-175">Met Power shell, als de host voor de invoeg toepassing, wordt dit enigszins door ingewik kelder voor modules.</span><span class="sxs-lookup"><span data-stu-id="6ea33-175">PowerShell, as the plugin host, complicates this slightly for modules.</span></span> <span data-ttu-id="6ea33-176">De afhankelijkheden in `$PSHOME` worden gedeeld met alle modules.</span><span class="sxs-lookup"><span data-stu-id="6ea33-176">Its dependencies in `$PSHOME` are shared with all modules.</span></span>
- <span data-ttu-id="6ea33-177">Slechts één toepassings domein en geen mogelijkheid om nieuwe items te maken.</span><span class="sxs-lookup"><span data-stu-id="6ea33-177">Only one Application Domain, and no ability to create new ones.</span></span> <span data-ttu-id="6ea33-178">Het toepassings domein concept wordt in .NET core onderhouden, louter als de algemene status van het .NET-proces.</span><span class="sxs-lookup"><span data-stu-id="6ea33-178">The Application Domain concept is maintained in .NET Core purely to be the global state of the .NET process.</span></span>
- <span data-ttu-id="6ea33-179">Een nieuw, uitbreidbaar verzamelings context model voor het laden van de assembly.</span><span class="sxs-lookup"><span data-stu-id="6ea33-179">A new, extensible Assembly Load Context model.</span></span> <span data-ttu-id="6ea33-180">De oplossing van de assembly kan worden voorzien van een naam ruimte door deze in een nieuwe ALC te zetten.</span><span class="sxs-lookup"><span data-stu-id="6ea33-180">Assembly resolution can be namespaced by putting it in a new ALC.</span></span> <span data-ttu-id="6ea33-181">.NET core-processen beginnen met één standaard ALC waarin alle assembly's worden geladen.</span><span class="sxs-lookup"><span data-stu-id="6ea33-181">.NET Core processes begin with a single default ALC into which all assemblies are loaded.</span></span> <span data-ttu-id="6ea33-182">(met uitzonde ring van de geladen met `Assembly.LoadFile(string)` en `Assembly.Load(byte[])` ), maar het proces kan een eigen aangepaste ALCs maken en definiëren met een eigen geladen logica.</span><span class="sxs-lookup"><span data-stu-id="6ea33-182">(except for those loaded with `Assembly.LoadFile(string)` and `Assembly.Load(byte[])`) But the process can create and define its own custom ALCs with its own loading logic.</span></span> <span data-ttu-id="6ea33-183">Wanneer een assembly wordt geladen, wordt de eerste ALC die wordt geladen in, verantwoordelijk voor het oplossen van de bijbehorende afhankelijkheden.</span><span class="sxs-lookup"><span data-stu-id="6ea33-183">When an assembly is loaded, the first ALC it is loaded into is responsible for resolving its dependencies.</span></span> <span data-ttu-id="6ea33-184">Hiermee maakt u mogelijkheden voor het implementeren van krachtige .NET-invoeg toepassingen voor laden.</span><span class="sxs-lookup"><span data-stu-id="6ea33-184">This creates opportunities to implement powerful .NET plugin loading mechanisms.</span></span>

<span data-ttu-id="6ea33-185">In beide implementaties worden assembly's geladen vertraagd.</span><span class="sxs-lookup"><span data-stu-id="6ea33-185">In both implementations, assemblies are loaded lazily.</span></span> <span data-ttu-id="6ea33-186">Dit betekent dat ze worden geladen wanneer een methode voor de eerste keer wordt uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="6ea33-186">This means that they are loaded when a method requiring their type is run for the first time.</span></span>

<span data-ttu-id="6ea33-187">Dit zijn bijvoorbeeld twee versies van dezelfde code die een afhankelijkheid op verschillende tijdstippen laden.</span><span class="sxs-lookup"><span data-stu-id="6ea33-187">For example, here are two versions of the same code that load a dependency at different times.</span></span>

<span data-ttu-id="6ea33-188">Bij de eerste keer wordt de afhankelijkheid altijd geladen als `Program.GetRange()` deze wordt aangeroepen, omdat de afhankelijkheids verwijzing in de methode lexicalen is.</span><span class="sxs-lookup"><span data-stu-id="6ea33-188">The first always loads its dependency when `Program.GetRange()` is called, because the dependency reference is lexically present within the method:</span></span>

```csharp
using Dependency.Library;

public static class Program
{
    public static List<int> GetRange(int limit)
    {
        var list = new List<int>();
        for (int i = 0; i < limit; i++)
        {
            if (i >= 20)
            {
                // Dependency.Library will be loaded when GetRange is run
                // because the dependency call occurs directly within the method
                DependencyApi.Use();
            }

            list.Add(i);
        }
        return list;
    }
}
```

<span data-ttu-id="6ea33-189">De tweede laadt de afhankelijkheid alleen als de `limit` para meter 20 of meer is, vanwege de interne Inleiding via een methode:</span><span class="sxs-lookup"><span data-stu-id="6ea33-189">The second will load its dependency only if the `limit` parameter is 20 or more, because of the internal indirection through a method:</span></span>

```csharp
using Dependency.Library;

public static class Program
{
    public static List<int> GetNumbers(int limit)
    {
        var list = new List<int>();
        for (int i = 0; i < limit; i++)
        {
            if (i >= 20)
            {
                // Dependency.Library is only referenced within
                // the UseDependencyApi() method,
                // so will only be loaded when limit >= 20
                UseDependencyApi();
            }

            list.Add(i);
        }
        return list;
    }

    private static void UseDependencyApi()
    {
        // Once UseDependencyApi() is called, Dependency.Library is loaded
        DependencyApi.Use();
    }
}
```

<span data-ttu-id="6ea33-190">Dit is een goede gewoonte omdat het geheugen en bestandssysteem-I/O minimaliseert en de bronnen efficiënter worden gebruikt.</span><span class="sxs-lookup"><span data-stu-id="6ea33-190">This is a good practice since it minimizes the memory and filesystem I/O and uses the resources more efficiently.</span></span> <span data-ttu-id="6ea33-191">De vervelend een neven effect hiervan is dat we niet weten dat de assembly niet kan worden geladen totdat we het codepad hebben bereikt dat probeert de assembly te laden.</span><span class="sxs-lookup"><span data-stu-id="6ea33-191">The unfortunate a side effect of this is that we won't know that the assembly fails to load until we reach the code path that tries to load the assembly.</span></span>

<span data-ttu-id="6ea33-192">Er kan ook een timing voorwaarde worden gemaakt voor conflicten bij het laden van de assembly.</span><span class="sxs-lookup"><span data-stu-id="6ea33-192">It can also create a timing condition for assembly load conflicts.</span></span> <span data-ttu-id="6ea33-193">Als twee delen van hetzelfde programma proberen verschillende versies van dezelfde assembly te laden, is de versie die wordt geladen, afhankelijk van welk codepad het eerst wordt uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="6ea33-193">If two parts of the same program try to load different versions of the same assembly, the version loaded depends on which code path is run first.</span></span>

<span data-ttu-id="6ea33-194">Voor Power shell betekent dit dat de volgende factoren van invloed kunnen zijn op een assembly-belasting conflict:</span><span class="sxs-lookup"><span data-stu-id="6ea33-194">For PowerShell, this means that the following factors can affect an assembly load conflict:</span></span>

- <span data-ttu-id="6ea33-195">Welke module is het eerst geladen?</span><span class="sxs-lookup"><span data-stu-id="6ea33-195">Which module was loaded first?</span></span>
- <span data-ttu-id="6ea33-196">Is het codepad dat gebruikmaakt van de afhankelijkheids bibliotheek run?</span><span class="sxs-lookup"><span data-stu-id="6ea33-196">Was the code path that uses the dependency library run?</span></span>
- <span data-ttu-id="6ea33-197">Laadt Power shell een conflicterende afhankelijkheid bij het opstarten of alleen onder bepaalde code paden?</span><span class="sxs-lookup"><span data-stu-id="6ea33-197">Does PowerShell load a conflicting dependency at startup or only under certain code paths?</span></span>

## <a name="quick-fixes-and-their-limitations"></a><span data-ttu-id="6ea33-198">Snelle oplossingen en hun beperkingen</span><span class="sxs-lookup"><span data-stu-id="6ea33-198">Quick fixes and their limitations</span></span>

<span data-ttu-id="6ea33-199">In sommige gevallen is het mogelijk om kleine aanpassingen aan te brengen in uw module en om dingen te corrigeren met minimale inspanning.</span><span class="sxs-lookup"><span data-stu-id="6ea33-199">In some cases, it's possible to make small adjustments to your module and fix things with minimal effort.</span></span> <span data-ttu-id="6ea33-200">Maar deze oplossingen worden meestal geleverd met aanvullende opmerkingen.</span><span class="sxs-lookup"><span data-stu-id="6ea33-200">But these solutions tend to come with caveats.</span></span> <span data-ttu-id="6ea33-201">Hoewel ze kunnen worden toegepast op uw module, werken ze niet voor elke module.</span><span class="sxs-lookup"><span data-stu-id="6ea33-201">While they may apply to your module, they won't work for every module.</span></span>

### <a name="change-your-dependency-version"></a><span data-ttu-id="6ea33-202">De afhankelijkheids versie wijzigen</span><span class="sxs-lookup"><span data-stu-id="6ea33-202">Change your dependency version</span></span>

<span data-ttu-id="6ea33-203">De eenvoudigste manier om afhankelijkheids conflicten te voor komen, is door akkoord te gaan met een afhankelijkheid.</span><span class="sxs-lookup"><span data-stu-id="6ea33-203">The simplest way to avoid dependency conflicts is to agree on a dependency.</span></span> <span data-ttu-id="6ea33-204">Dit kan de volgende oorzaken hebben:</span><span class="sxs-lookup"><span data-stu-id="6ea33-204">This may be possible when:</span></span>

- <span data-ttu-id="6ea33-205">Uw conflict is met een directe afhankelijkheid van uw module en u beheert de versie.</span><span class="sxs-lookup"><span data-stu-id="6ea33-205">Your conflict is with a direct dependency of your module and you control the version.</span></span>
- <span data-ttu-id="6ea33-206">Uw conflict is met een indirecte afhankelijkheid, maar u kunt uw directe afhankelijkheden configureren voor het gebruik van een bemaalde, indirecte afhankelijkheids versie.</span><span class="sxs-lookup"><span data-stu-id="6ea33-206">Your conflict is with an indirect dependency, but you can configure your direct dependencies to use a workable indirect dependency version.</span></span>
- <span data-ttu-id="6ea33-207">U weet de conflicterende versie en kan erop vertrouwen dat deze niet verandert.</span><span class="sxs-lookup"><span data-stu-id="6ea33-207">You know the conflicting version and can rely on it not changing.</span></span>

<span data-ttu-id="6ea33-208">Het `Newtonsoft.Json` pakket is een goed voor beeld van dit laatste scenario.</span><span class="sxs-lookup"><span data-stu-id="6ea33-208">The `Newtonsoft.Json` package is a good example of this last scenario.</span></span> <span data-ttu-id="6ea33-209">Dit is een afhankelijkheid van Power shell 6 en hoger, en wordt niet gebruikt in Windows Power shell.</span><span class="sxs-lookup"><span data-stu-id="6ea33-209">This is a dependency of PowerShell 6 and above, and isn't used in Windows PowerShell.</span></span> <span data-ttu-id="6ea33-210">Een eenvoudige manier om versie conflicten op te lossen is het richten op de laagste versie van `Newtonsoft.Json` alle Power shell-versies die u wilt richten.</span><span class="sxs-lookup"><span data-stu-id="6ea33-210">Meaning a simple way to resolve versioning conflicts is to target the lowest version of `Newtonsoft.Json` across the PowerShell versions you wish to target.</span></span>

<span data-ttu-id="6ea33-211">Bijvoorbeeld, Power shell 6.2.6 en Power shell 7.0.2 gebruiken momenteel `Newtonsoft.Json` versie 12.0.3.</span><span class="sxs-lookup"><span data-stu-id="6ea33-211">For example, PowerShell 6.2.6 and PowerShell 7.0.2 both currently use `Newtonsoft.Json` version 12.0.3.</span></span> <span data-ttu-id="6ea33-212">Als u een module wilt maken die is gericht op Windows Power shell, Power shell 6 en Power shell 7, zou u dus `Newtonsoft.Json 12.0.3` als een afhankelijkheid als doel hebben en deze in uw ingebouwde module toevoegen.</span><span class="sxs-lookup"><span data-stu-id="6ea33-212">So, to create a module targeting Windows PowerShell, PowerShell 6, and PowerShell 7, you would target `Newtonsoft.Json 12.0.3` as a dependency and include it in your built module.</span></span> <span data-ttu-id="6ea33-213">Wanneer de module in Power shell 6 of 7 is geladen, is de eigen assembly van Power shell `Newtonsoft.Json` al geladen.</span><span class="sxs-lookup"><span data-stu-id="6ea33-213">When the module is loaded in PowerShell 6 or 7, PowerShell's own `Newtonsoft.Json` assembly is already loaded.</span></span> <span data-ttu-id="6ea33-214">Het is ook ten minste de versie die is vereist voor uw module, waardoor de oplossing slaagt.</span><span class="sxs-lookup"><span data-stu-id="6ea33-214">Also, it is at least the version required for your module, so resolution succeeds.</span></span> <span data-ttu-id="6ea33-215">In Windows Power shell is de assembly niet al aanwezig in Power shell.</span><span class="sxs-lookup"><span data-stu-id="6ea33-215">In Windows PowerShell, the assembly isn't already present in PowerShell.</span></span> <span data-ttu-id="6ea33-216">In plaats daarvan wordt het geladen vanuit de map module.</span><span class="sxs-lookup"><span data-stu-id="6ea33-216">So, it's loaded from your module folder instead.</span></span>

<span data-ttu-id="6ea33-217">Bij het richten op een concreet Power shell-pakket, zoals `Microsoft.PowerShell.Sdk` of `System.Management.Automation` , moet NuGet de juiste vereiste afhankelijkheids versies kunnen omzetten.</span><span class="sxs-lookup"><span data-stu-id="6ea33-217">Generally, when targeting a concrete PowerShell package, like `Microsoft.PowerShell.Sdk` or `System.Management.Automation`, NuGet should be able to resolve the right dependency versions required.</span></span> <span data-ttu-id="6ea33-218">Het doel van Windows Power shell en Power shell 6 + is moeilijker geworden omdat u moet kiezen tussen meerdere frameworks of het doel `PowerShellStandard.Library` .</span><span class="sxs-lookup"><span data-stu-id="6ea33-218">Targeting both Windows PowerShell and PowerShell 6+ becomes more difficult because you must choose between targeting multiple frameworks or `PowerShellStandard.Library`.</span></span>

<span data-ttu-id="6ea33-219">Omstandigheden waarbij het vastmaken aan een algemene afhankelijkheids versie niet werkt:</span><span class="sxs-lookup"><span data-stu-id="6ea33-219">Circumstances where pinning to a common dependency version won't work include:</span></span>

- <span data-ttu-id="6ea33-220">Het conflict is met een indirecte afhankelijkheid en geen van uw afhankelijkheden kunnen worden geconfigureerd voor het gebruik van een gemeen schappelijke versie.</span><span class="sxs-lookup"><span data-stu-id="6ea33-220">The conflict is with an indirect dependency, and none of your dependencies can be configured to use a common version.</span></span>
- <span data-ttu-id="6ea33-221">De andere versie van de afhankelijkheid is waarschijnlijk vaak gewijzigd, dus het afstellen van een algemene versie is alleen een oplossing op korte termijn.</span><span class="sxs-lookup"><span data-stu-id="6ea33-221">The other dependency version is likely to change often, so settling on a common version is only a short-term fix.</span></span>

### <a name="add-an-assemblyresolve-event-handler-to-create-a-dynamic-binding-redirect"></a><span data-ttu-id="6ea33-222">Een gebeurtenis-handler voor AssemblyResolve toevoegen om een omleiding van dynamische bindingen te maken</span><span class="sxs-lookup"><span data-stu-id="6ea33-222">Add an AssemblyResolve event handler to create a dynamic binding redirect</span></span>

<span data-ttu-id="6ea33-223">Soms is het wijzigen van uw eigen afhankelijkheids versie niet mogelijk of is het te moeilijk.</span><span class="sxs-lookup"><span data-stu-id="6ea33-223">Sometimes changing your own dependency version isn't possible or is too difficult.</span></span> <span data-ttu-id="6ea33-224">Een andere optie is om een dynamische bindings omleiding in te stellen door een gebeurtenis-handler voor de gebeurtenis te registreren `AssemblyResolve` .</span><span class="sxs-lookup"><span data-stu-id="6ea33-224">Another option is to set up a dynamic binding redirect by registering an event handler for the `AssemblyResolve` event.</span></span>

<span data-ttu-id="6ea33-225">Net als bij een statische bindings omleiding is het punt om alle consumenten van een afhankelijkheid af te dwingen om dezelfde werkelijke assembly te gebruiken.</span><span class="sxs-lookup"><span data-stu-id="6ea33-225">As with a static binding redirect, the point is to force all consumers of a dependency to use the same actual assembly.</span></span> <span data-ttu-id="6ea33-226">U kunt aanroepen voor het laden van de afhankelijkheid onderscheppen en deze altijd omleiden naar de gewenste versie.</span><span class="sxs-lookup"><span data-stu-id="6ea33-226">You intercept calls to load the dependency and always redirect them to the version you want.</span></span>

<span data-ttu-id="6ea33-227">Dit ziet er ongeveer als volgt uit:</span><span class="sxs-lookup"><span data-stu-id="6ea33-227">This looks something like this:</span></span>

```csharp
// Register the event handler as early as you can in your code.
// A good option is to use the IModuleAssemblyInitializer interface
// that PowerShell provides to run code early on when your module is loaded.

// This class will be instantiated on module import and the OnImport() method run.
// Make sure that:
//  - the class is public
//  - the class has a public, parameterless constructor
//  - the class implements IModuleAssemblyInitializer
public class MyModuleInitializer : IModuleAssemblyInitializer
{
    public void OnImport()
    {
        AppDomain.CurrentDomain.AssemblyResolve += DependencyResolution.ResolveNewtonsoftJson;
    }
}

// Clean up the event handler when the the module is removed
// to prevent memory leaks.
//
// Like IModuleAssemblyInitializer, IModuleAssemblyCleanup allows
// you to register code to run when a module is removed (with Remove-Module).
// Make sure it is also public with a public parameterless contructor
// and implements IModuleAssemblyCleanup.
public class MyModuleCleanup : IModuleAssemblyCleanup
{
    public void OnRemove()
    {
        AppDomain.CurrentDomain.AssemblyResolve -= DependencyResolution.ResolveNewtonsoftJson;
    }
}

internal static class DependencyResolution
{
    private static readonly string s_modulePath = Path.GetDirectoryName(
        Assembly.GetExecutingAssembly().Location);

    public static Assembly ResolveNewtonsoftJson(object sender, ResolveEventArgs args)
    {
        // Parse the assembly name
        var assemblyName = new AssemblyName(args.Name);

        // We only want to handle the dependency we care about.
        // In this example it's Newtonsoft.Json.
        if (!assemblyName.Name.Equals("Newtonsoft.Json"))
        {
            return null;
        }

        // Generally the version of the dependency you want to load is the higher one,
        // since it's the most likely to be compatible with all dependent assemblies.
        // The logic here assumes our module always has the version we want to load.
        // Also note the use of Assembly.LoadFrom() here rather than Assembly.LoadFile().
        return Assembly.LoadFrom(Path.Combine(s_modulePath, "Newtonsoft.Json.dll"));
    }
}
```

<span data-ttu-id="6ea33-228">U kunt een script Block in Power shell technisch registreren voor het afhandelen van een `AssemblyResolve` gebeurtenis, maar:</span><span class="sxs-lookup"><span data-stu-id="6ea33-228">You can technically register a scriptblock within PowerShell to handle an `AssemblyResolve` event, but:</span></span>

- <span data-ttu-id="6ea33-229">Een `AssemblyResolve` gebeurtenis kan worden geactiveerd voor elke thread, iets wat niet kan worden verwerkt met Power shell.</span><span class="sxs-lookup"><span data-stu-id="6ea33-229">An `AssemblyResolve` event may be triggered on any thread, something that PowerShell will be unable to handle.</span></span>
- <span data-ttu-id="6ea33-230">Zelfs wanneer gebeurtenissen worden verwerkt op de juiste thread, betekenen de scope-concepten van Power shell dat de gebeurtenis-handler script Block zorgvuldig moet worden geschreven zodat deze niet afhankelijk zijn van variabelen die buiten het bereik zijn gedefinieerd.</span><span class="sxs-lookup"><span data-stu-id="6ea33-230">Even when events are handled on the right thread, PowerShell's scoping concepts mean that the event handler scriptblock must be written carefully to not depend on variables defined outside it.</span></span>

<span data-ttu-id="6ea33-231">Er zijn situaties waarin het omleiden naar een algemene versie niet werkt:</span><span class="sxs-lookup"><span data-stu-id="6ea33-231">There are situations where redirecting to a common version won't work:</span></span>

- <span data-ttu-id="6ea33-232">Wanneer de afhankelijkheid wijzigingen heeft aangebracht tussen versies of wanneer afhankelijke code afhankelijk is van een functionaliteit die niet beschikbaar is in de versie waarnaar u omleidt.</span><span class="sxs-lookup"><span data-stu-id="6ea33-232">When the dependency has made breaking changes between versions, or when dependent code relies on a functionality otherwise not available in the version you redirect to.</span></span>
- <span data-ttu-id="6ea33-233">Als uw module niet is geladen vóór de conflicterende afhankelijkheid.</span><span class="sxs-lookup"><span data-stu-id="6ea33-233">When your module isn't loaded before the conflicting dependency.</span></span> <span data-ttu-id="6ea33-234">Als u een gebeurtenis-handler registreert `AssemblyResolve` nadat de afhankelijkheid is geladen, wordt deze nooit gestart.</span><span class="sxs-lookup"><span data-stu-id="6ea33-234">If you register an `AssemblyResolve` event handler after the dependency has been loaded, it will never be fired.</span></span> <span data-ttu-id="6ea33-235">Als u afhankelijkheids conflicten met een andere module wilt voor komen, is dit mogelijk een probleem omdat de andere module eerst kan worden geladen.</span><span class="sxs-lookup"><span data-stu-id="6ea33-235">If you're trying to prevent dependency conflicts with another module, this may be an issue, since the other module may be loaded first.</span></span>

### <a name="use-the-dependency-out-of-process"></a><span data-ttu-id="6ea33-236">De afhankelijkheid uit het proces gebruiken</span><span class="sxs-lookup"><span data-stu-id="6ea33-236">Use the dependency out of process</span></span>

<span data-ttu-id="6ea33-237">Deze oplossing is meer voor module gebruikers dan van module auteurs.</span><span class="sxs-lookup"><span data-stu-id="6ea33-237">This solution is more for module users than module authors.</span></span> <span data-ttu-id="6ea33-238">Dit is een oplossing voor het gebruik van een module die niet werkt vanwege een bestaand afhankelijkheids conflict.</span><span class="sxs-lookup"><span data-stu-id="6ea33-238">This is a solution to use when confronted with a module that won't work due to an existing dependency conflict.</span></span>

<span data-ttu-id="6ea33-239">Afhankelijkheids conflicten treden op omdat twee versies van dezelfde assembly in hetzelfde .NET-proces worden geladen.</span><span class="sxs-lookup"><span data-stu-id="6ea33-239">Dependency conflicts occur because two versions of the same assembly are loaded into the same .NET process.</span></span> <span data-ttu-id="6ea33-240">Een eenvoudige oplossing is het laden van deze in verschillende processen, zolang u de functionaliteit van beide kunt gebruiken.</span><span class="sxs-lookup"><span data-stu-id="6ea33-240">A simple solution is to load them into different processes, as long as you can still use the functionality from both together.</span></span>

<span data-ttu-id="6ea33-241">In Power shell zijn er verschillende manieren om dit te doen:</span><span class="sxs-lookup"><span data-stu-id="6ea33-241">In PowerShell, there are several ways to achieve this:</span></span>

- <span data-ttu-id="6ea33-242">Power shell als een subproces aanroepen</span><span class="sxs-lookup"><span data-stu-id="6ea33-242">Invoke PowerShell as a subprocess</span></span>

  <span data-ttu-id="6ea33-243">Een eenvoudige manier om een Power shell-opdracht uit te voeren vanuit het huidige proces is door alleen een nieuw Power Shell-proces rechtstreeks te starten met de opdracht aanroep:</span><span class="sxs-lookup"><span data-stu-id="6ea33-243">A simple way to run a PowerShell command out of the current process is to just start a new PowerShell process directly with the command call:</span></span>

  ```powershell
  pwsh -c 'Invoke-ConflictingCommand'
  ```

  <span data-ttu-id="6ea33-244">De belangrijkste beperking is dat de herstructurering het resultaat kan trickier of meer fout gevoelig is dan andere opties.</span><span class="sxs-lookup"><span data-stu-id="6ea33-244">The main limitation here is that restructuring the result can be trickier or more error prone than other options.</span></span>

- <span data-ttu-id="6ea33-245">Het Power shell-taak systeem</span><span class="sxs-lookup"><span data-stu-id="6ea33-245">The PowerShell job system</span></span>

  <span data-ttu-id="6ea33-246">Het Power shell-taak systeem voert ook opdrachten uit het proces uit, door opdrachten te verzenden naar een nieuw Power Shell-proces en de resultaten te retour neren:</span><span class="sxs-lookup"><span data-stu-id="6ea33-246">The PowerShell job system also runs commands out of process, by sending commands to a new PowerShell process and returning the results:</span></span>

  ```powershell
  $result = Start-Job { Invoke-ConflictingCommand } | Receive-Job -Wait
  ```

  <span data-ttu-id="6ea33-247">In dit geval moet u er alleen voor zorgen dat alle variabelen en status correct worden door gegeven.</span><span class="sxs-lookup"><span data-stu-id="6ea33-247">In this case, you just need to be sure that any variables and state are passed in correctly.</span></span>

  <span data-ttu-id="6ea33-248">Het taak systeem kan ook iets omslachtig zijn wanneer u kleine opdrachten uitvoert.</span><span class="sxs-lookup"><span data-stu-id="6ea33-248">The job system can also be slightly cumbersome when running small commands.</span></span>

- <span data-ttu-id="6ea33-249">Externe communicatie van powershell</span><span class="sxs-lookup"><span data-stu-id="6ea33-249">PowerShell remoting</span></span>

  <span data-ttu-id="6ea33-250">Wanneer het beschikbaar is, kan externe communicatie van Power shell op een handige manier worden uitgevoerd om opdrachten uit te voeren.</span><span class="sxs-lookup"><span data-stu-id="6ea33-250">When it's available, PowerShell remoting can be a useful way to run commands out of process.</span></span> <span data-ttu-id="6ea33-251">Met externe toegang kunt u een nieuwe **PSSession** maken in een nieuw proces, de opdrachten aanroepen via Power shell remoting en vervolgens de resultaten lokaal gebruiken met de andere modules met de conflicterende afhankelijkheden.</span><span class="sxs-lookup"><span data-stu-id="6ea33-251">With remoting, you can create a fresh **PSSession** in a new process, call its commands over PowerShell remoting, then use the results locally with the other modules containing the conflicting dependencies.</span></span>

  <span data-ttu-id="6ea33-252">Een voor beeld kan er als volgt uitzien:</span><span class="sxs-lookup"><span data-stu-id="6ea33-252">An example might look like this:</span></span>

  ```powershell
  # Create a local PowerShell session
  # where the module with conflicting assemblies will be loaded
  $s = New-PSSession

  # Import the module with the conflicting dependency via remoting,
  # exposing the commands locally
  Import-Module -PSSession $s -Name ConflictingModule

  # Run a command from the module with the conflicting dependencies
  Invoke-ConflictingCommand
  ```

- <span data-ttu-id="6ea33-253">Impliciete externe toegang tot Windows Power shell</span><span class="sxs-lookup"><span data-stu-id="6ea33-253">Implicit remoting to Windows PowerShell</span></span>

  <span data-ttu-id="6ea33-254">Een andere optie in Power shell 7 is het gebruik `-UseWindowsPowerShell` van de vlag on `Import-Module` .</span><span class="sxs-lookup"><span data-stu-id="6ea33-254">Another option in PowerShell 7 is to use the `-UseWindowsPowerShell` flag on `Import-Module`.</span></span> <span data-ttu-id="6ea33-255">Hiermee wordt de module via een lokale externe sessie in Windows Power shell geïmporteerd:</span><span class="sxs-lookup"><span data-stu-id="6ea33-255">This will import the module through a local remoting session into Windows PowerShell:</span></span>

  ```powershell
  Import-Module -Name ConflictingModule -UseWindowsPowerShell
  ```

  <span data-ttu-id="6ea33-256">Houd er rekening mee dat modules mogelijk niet werken met of anders werken met Windows Power shell.</span><span class="sxs-lookup"><span data-stu-id="6ea33-256">Be aware that modules may not work with, or work differently with Windows PowerShell.</span></span>

#### <a name="when-out-of-process-invocation-should-not-be-used"></a><span data-ttu-id="6ea33-257">Als out-of-process-aanroep niet kan worden gebruikt</span><span class="sxs-lookup"><span data-stu-id="6ea33-257">When out-of-process invocation should not be used</span></span>

<span data-ttu-id="6ea33-258">Als module-auteur is het intrekken van de out-of-process-opdracht moeilijk te maken in een module en kunnen er ook rand cases zijn die problemen veroorzaken.</span><span class="sxs-lookup"><span data-stu-id="6ea33-258">As a module author, out-of-process command invocation is difficult to bake into a module and may have edge cases that cause issues.</span></span> <span data-ttu-id="6ea33-259">Met name externe communicatie en taken zijn mogelijk niet beschikbaar in alle omgevingen waar de module moet worden gebruikt.</span><span class="sxs-lookup"><span data-stu-id="6ea33-259">In particular, remoting and jobs may not be available in all environments where your module needs to work.</span></span> <span data-ttu-id="6ea33-260">Het algemene principe van het verplaatsen van de implementatie uit het proces en het toestaan van de Power shell-module als een smallere client, kan echter nog steeds van toepassing zijn.</span><span class="sxs-lookup"><span data-stu-id="6ea33-260">However, the general principle of moving the implementation out of process and allowing the PowerShell module to be a thinner client, may still be applicable.</span></span>

<span data-ttu-id="6ea33-261">Als module gebruiker zijn er gevallen waarin out-of-process-aanroep niet werkt:</span><span class="sxs-lookup"><span data-stu-id="6ea33-261">As a module user, there are cases where out-of-process invocation won't work:</span></span>

- <span data-ttu-id="6ea33-262">Wanneer externe communicatie van Power shell niet beschikbaar is, omdat u niet over de juiste bevoegdheden beschikt om deze te gebruiken of niet is ingeschakeld.</span><span class="sxs-lookup"><span data-stu-id="6ea33-262">When PowerShell remoting is unavailable because you don't have privileges to use it or it is not enabled.</span></span>
- <span data-ttu-id="6ea33-263">Wanneer een bepaald .NET-type nodig is voor uitvoer als invoer naar een methode of een andere opdracht.</span><span class="sxs-lookup"><span data-stu-id="6ea33-263">When a particular .NET type is needed from output as input to a method or another command.</span></span>
  <span data-ttu-id="6ea33-264">Opdrachten die gebruikmaken van externe communicatie van Power shell, verzenden gedeserialiseerd objecten in plaats van sterk getypte .NET-objecten.</span><span class="sxs-lookup"><span data-stu-id="6ea33-264">Commands running over PowerShell remoting emit deserialized objects rather than strongly-typed .NET objects.</span></span> <span data-ttu-id="6ea33-265">Dit betekent dat methode aanroepen en sterk getypeerde Api's niet werken met de uitvoer van opdrachten die worden geïmporteerd over externe communicatie.</span><span class="sxs-lookup"><span data-stu-id="6ea33-265">This means that method calls and strongly typed APIs do not work with the output of commands imported over remoting.</span></span>

## <a name="more-robust-solutions"></a><span data-ttu-id="6ea33-266">Meer robuuste oplossingen</span><span class="sxs-lookup"><span data-stu-id="6ea33-266">More robust solutions</span></span>

<span data-ttu-id="6ea33-267">De vorige oplossingen bevatten allemaal scenario's en modules die niet werken.</span><span class="sxs-lookup"><span data-stu-id="6ea33-267">The previous solutions all had scenarios and modules that don't work.</span></span> <span data-ttu-id="6ea33-268">Ze hebben echter ook relatief eenvoudig te implementeren.</span><span class="sxs-lookup"><span data-stu-id="6ea33-268">However, they also have the virtue of being relatively simple to implement correctly.</span></span> <span data-ttu-id="6ea33-269">De volgende oplossingen zijn robuuster, maar vereisen meer moeite om correct te implementeren en kunnen subtiele bugs introduceren als ze niet zorgvuldig worden geschreven.</span><span class="sxs-lookup"><span data-stu-id="6ea33-269">The following solutions are more robust, but require more effort to implement correctly and can introduce subtle bugs if not written carefully.</span></span>

### <a name="loading-through-net-core-assembly-load-contexts"></a><span data-ttu-id="6ea33-270">Contexten laden met behulp van .NET core assembly-belasting</span><span class="sxs-lookup"><span data-stu-id="6ea33-270">Loading through .NET Core Assembly Load Contexts</span></span>

<span data-ttu-id="6ea33-271">[Assembly-contexten](/dotnet/api/system.runtime.loader.assemblyloadcontext) (ALCs) als een Implementeer bare API zijn geïntroduceerd in .net Core 1,0 om de nood zaak om meerdere versies van dezelfde assembly in dezelfde runtime te laden, te verhelpen.</span><span class="sxs-lookup"><span data-stu-id="6ea33-271">[Assembly Load Contexts](/dotnet/api/system.runtime.loader.assemblyloadcontext) (ALCs) as an implementable API were introduced in .NET Core 1.0 to specifically address the need to load multiple versions of the same assembly into the same runtime.</span></span>

<span data-ttu-id="6ea33-272">Binnen .NET core en .NET 5 bieden ze de meest robuuste oplossing voor het probleem van het laden van conflicterende versies van een assembly.</span><span class="sxs-lookup"><span data-stu-id="6ea33-272">Within .NET Core and .NET 5, they offer the most robust solution to the problem of loading conflicting versions of an assembly.</span></span> <span data-ttu-id="6ea33-273">Aangepaste ALCs zijn echter niet beschikbaar in .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="6ea33-273">However, custom ALCs are not available in .NET Framework.</span></span> <span data-ttu-id="6ea33-274">Dit betekent dat deze oplossing alleen werkt in Power shell 6 en hoger.</span><span class="sxs-lookup"><span data-stu-id="6ea33-274">This means that this solution only works in PowerShell 6 and above.</span></span>

<span data-ttu-id="6ea33-275">Momenteel is het beste voor beeld van het gebruik van een ALC voor het isoleren van afhankelijkheden in Power shell in Power shell editor-Services, de taal server voor de Power shell-extensie voor Visual Studio code.</span><span class="sxs-lookup"><span data-stu-id="6ea33-275">Currently, the best example of using an ALC for dependency isolation in PowerShell is in PowerShell Editor Services, the language server for the PowerShell extension for Visual Studio Code.</span></span> <span data-ttu-id="6ea33-276">Een [ALC wordt gebruikt](https://github.com/PowerShell/PowerShellEditorServices/blob/master/src/PowerShellEditorServices.Hosting/Internal/PsesLoadContext.cs) om te voor komen dat de eigen afhankelijkheden van Power shell editor-Services conflicteren met die in Power shell-modules.</span><span class="sxs-lookup"><span data-stu-id="6ea33-276">An [ALC is used](https://github.com/PowerShell/PowerShellEditorServices/blob/master/src/PowerShellEditorServices.Hosting/Internal/PsesLoadContext.cs) to prevent PowerShell Editor Services' own dependencies from clashing with those in PowerShell modules.</span></span>

<span data-ttu-id="6ea33-277">Het implementeren van module afhankelijkheids isolatie met een ALC is conceptueel moeilijk, maar we werken met een mini maal voor beeld.</span><span class="sxs-lookup"><span data-stu-id="6ea33-277">Implementing module dependency isolation with an ALC is conceptually difficult, but we will work through a minimal example.</span></span> <span data-ttu-id="6ea33-278">Stel dat er een eenvoudige module is die alleen is bedoeld voor gebruik in Power shell 7.</span><span class="sxs-lookup"><span data-stu-id="6ea33-278">Imagine we have a simple module that is only intended to work in PowerShell 7.</span></span>
<span data-ttu-id="6ea33-279">De bron code is als volgt ingedeeld:</span><span class="sxs-lookup"><span data-stu-id="6ea33-279">The source code is organized as follows:</span></span>

```
+ AlcModule.psd1
+ src/
    + TestAlcModuleCommand.cs
    + AlcModule.csproj
```

<span data-ttu-id="6ea33-280">De cmdlet-implementatie ziet er als volgt uit:</span><span class="sxs-lookup"><span data-stu-id="6ea33-280">The cmdlet implementation looks like this:</span></span>

```csharp
using Shared.Dependency;

namespace AlcModule
{
    [Cmdlet(VerbsDiagnostic.Test, "AlcModule")]
    public class TestAlcModuleCommand : Cmdlet
    {
        protected override void EndProcessing()
        {
            // Here's where our dependency gets used
            Dependency.Use();
            // Something trivial to make our cmdlet do *something*
            WriteObject("done!");
        }
    }
}
```

<span data-ttu-id="6ea33-281">Het manifest (sterk vereenvoudigd), ziet er als volgt uit:</span><span class="sxs-lookup"><span data-stu-id="6ea33-281">The (heavily simplified) manifest, looks like this:</span></span>

```powershell
@{
    Author = 'Me'
    ModuleVersion = '0.0.1'
    RootModule = 'AlcModule.dll'
    CmdletsToExport = @('Test-AlcModule')
    PowerShellVersion = '7.0'
}
```

<span data-ttu-id="6ea33-282">En het `csproj` ziet er als volgt uit:</span><span class="sxs-lookup"><span data-stu-id="6ea33-282">And the `csproj` looks like this:</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">
  <PropertyGroup>
    <TargetFramework>netcoreapp3.1</TargetFramework>
  </PropertyGroup>
  <ItemGroup>
    <PackageReference Include="Shared.Dependency" Version="1.0.0" />
    <PackageReference Include="Microsoft.PowerShell.Sdk" Version="7.0.1" PrivateAssets="all" />
  </ItemGroup>
</Project>
```

<span data-ttu-id="6ea33-283">Bij het maken van deze module heeft de gegenereerde uitvoer de volgende indeling:</span><span class="sxs-lookup"><span data-stu-id="6ea33-283">When we build this module, the generated output has the following layout:</span></span>

```
AlcModule/
  + AlcModule.psd1
  + AlcModule.dll
  + Shared.Dependency.dll
```

<span data-ttu-id="6ea33-284">In dit voor beeld bevindt het probleem zich in de `Shared.Dependency.dll` Assembly. Dit is onze imaginaire conflicterende afhankelijkheid.</span><span class="sxs-lookup"><span data-stu-id="6ea33-284">In this example, our problem is in the `Shared.Dependency.dll` assembly, which is our imaginary conflicting dependency.</span></span> <span data-ttu-id="6ea33-285">Dit is de afhankelijkheid die we achter een ALC moeten plaatsen, zodat we de module-specifieke versie kunnen gebruiken.</span><span class="sxs-lookup"><span data-stu-id="6ea33-285">This is the dependency that we need to put behind an ALC so that we can use the module-specific version.</span></span>

<span data-ttu-id="6ea33-286">We moeten de module opnieuw inbouwen zodat:</span><span class="sxs-lookup"><span data-stu-id="6ea33-286">We need to re-engineer the module so that:</span></span>

- <span data-ttu-id="6ea33-287">Module-afhankelijkheden worden alleen in onze aangepaste ALC geladen en niet in de ALC van Power shell, zodat er geen conflict kan optreden.</span><span class="sxs-lookup"><span data-stu-id="6ea33-287">Module dependencies are only loaded into our custom ALC, and not into PowerShell's ALC, so there can be no conflict.</span></span> <span data-ttu-id="6ea33-288">Omdat we meer afhankelijkheden aan ons project toevoegen, willen we niet continu meer code toevoegen om te blijven werken.</span><span class="sxs-lookup"><span data-stu-id="6ea33-288">Moreover, as we add more dependencies to our project, we don't want to continuously add more code to keep loading working.</span></span> <span data-ttu-id="6ea33-289">In plaats daarvan willen we de algemene logica van afhankelijkheids oplossingen opnieuw gebruiken.</span><span class="sxs-lookup"><span data-stu-id="6ea33-289">Instead, we want reusable, generic dependency resolution logic.</span></span>
- <span data-ttu-id="6ea33-290">Het laden van de module werkt nog steeds normaal in Power shell.</span><span class="sxs-lookup"><span data-stu-id="6ea33-290">Loading the module still works as normal in PowerShell.</span></span> <span data-ttu-id="6ea33-291">Cmdlets en andere typen die nodig zijn voor de Power shell-module systeem, worden gedefinieerd in de eigen ALC van Power shell.</span><span class="sxs-lookup"><span data-stu-id="6ea33-291">Cmdlets and other types that the PowerShell module system needs are defined within PowerShell's own ALC.</span></span>

<span data-ttu-id="6ea33-292">Om deze twee vereisten te kunnen bepalen, moeten we onze module opsplitsen in twee assembly's:</span><span class="sxs-lookup"><span data-stu-id="6ea33-292">To mediate these two requirements, we must break up our module into two assemblies:</span></span>

- <span data-ttu-id="6ea33-293">Een cmdlets-assembly, `AlcModule.Cmdlets.dll` , die definities bevat van alle typen die het module systeem van Power shell nodig heeft om onze module correct te laden.</span><span class="sxs-lookup"><span data-stu-id="6ea33-293">A cmdlets assembly, `AlcModule.Cmdlets.dll`, that contains definitions of all the types that PowerShell's module system needs to load our module correctly.</span></span> <span data-ttu-id="6ea33-294">Dat wil zeggen dat alle implementaties van de `Cmdlet` basis klasse en de klasse die deze implementeert `IModuleAssemblyInitializer` , de gebeurtenis-handler instellen `AssemblyLoadContext.Default.Resolving` om op de juiste wijze te worden geladen `AlcModule.Engine.dll` via onze aangepaste alc.</span><span class="sxs-lookup"><span data-stu-id="6ea33-294">Namely, any implementations of the `Cmdlet` base class and the class that implements `IModuleAssemblyInitializer`, which sets up the event handler for `AssemblyLoadContext.Default.Resolving` to properly load `AlcModule.Engine.dll` through our custom ALC.</span></span> <span data-ttu-id="6ea33-295">Omdat Power shell 7 de typen die zijn gedefinieerd in assembly's die in andere ALCs zijn geladen, verbergt, moeten de typen die openbaar beschikbaar zijn voor Power shell ook hier worden gedefinieerd.</span><span class="sxs-lookup"><span data-stu-id="6ea33-295">Since PowerShell 7 deliberately hides types defined in assemblies loaded in other ALCs, any types that are meant to be publicly exposed to PowerShell must also be defined here.</span></span> <span data-ttu-id="6ea33-296">Ten slotte moet onze aangepaste ALC-definitie worden gedefinieerd in deze assembly.</span><span class="sxs-lookup"><span data-stu-id="6ea33-296">Finally, our custom ALC definition needs to be defined in this assembly.</span></span> <span data-ttu-id="6ea33-297">Zo weinig mogelijk zou er in deze assembly kunnen worden opgenomen.</span><span class="sxs-lookup"><span data-stu-id="6ea33-297">Beyond that, as little code as possible should live in this assembly.</span></span>
- <span data-ttu-id="6ea33-298">Een engine-assembly, `AlcModule.Engine.dll` waarmee de daad werkelijke implementatie van de module wordt verwerkt.</span><span class="sxs-lookup"><span data-stu-id="6ea33-298">An engine assembly, `AlcModule.Engine.dll`, that handles the actual implementation of the module.</span></span>
  <span data-ttu-id="6ea33-299">Typen van deze zijn beschikbaar in Power shell ALC, maar deze worden in eerste instantie geladen via onze aangepaste ALC.</span><span class="sxs-lookup"><span data-stu-id="6ea33-299">Types from this are available in the PowerShell ALC, but it will initially be loaded through our custom ALC.</span></span> <span data-ttu-id="6ea33-300">De afhankelijkheden worden alleen in de aangepaste ALC geladen.</span><span class="sxs-lookup"><span data-stu-id="6ea33-300">Its dependencies are only loaded into the custom ALC.</span></span> <span data-ttu-id="6ea33-301">Effectief wordt dit een _brug_ tussen de twee ALCs.</span><span class="sxs-lookup"><span data-stu-id="6ea33-301">Effectively, this becomes a _bridge_ between the two ALCs.</span></span>

<span data-ttu-id="6ea33-302">Met dit brug concept ziet onze nieuwe assembly-situatie er als volgt uit:</span><span class="sxs-lookup"><span data-stu-id="6ea33-302">Using this bridge concept, our new assembly situation looks like this:</span></span>

![Diagram dat AlcModule.Engine.dll het overbruggen van de twee ALCs](./media/resolving-dependency-conflicts/alc-diagram.jpg)

<span data-ttu-id="6ea33-304">Als u er zeker van wilt zijn dat de standaard-logica voor het afhankelijkheden van ALC de afhankelijkheden niet oplost die in de aangepaste ALC moeten worden geladen, moeten deze twee delen van de module in verschillende directory's worden gescheiden.</span><span class="sxs-lookup"><span data-stu-id="6ea33-304">To make sure the default ALC's dependency probing logic does not resolve the dependencies to be loaded into the custom ALC, we need to separate these two parts of the module in different directories.</span></span> <span data-ttu-id="6ea33-305">De nieuwe module-indeling heeft de volgende structuur:</span><span class="sxs-lookup"><span data-stu-id="6ea33-305">The new module layout has the following structure:</span></span>

```
AlcModule/
  AlcModule.Cmdlets.dll
  AlcModule.psd1
  Dependencies/
  | + AlcModule.Engine.dll
  | + Shared.Dependency.dll
```

<span data-ttu-id="6ea33-306">Om te zien hoe de implementatie verandert, beginnen we met de implementatie van `AlcModule.Engine.dll` :</span><span class="sxs-lookup"><span data-stu-id="6ea33-306">To see how the implementation changes, we'll start with the implementation of `AlcModule.Engine.dll`:</span></span>

```csharp
using Shared.Dependency;

namespace AlcModule.Engine
{
    public class AlcEngine
    {
        public static void Use()
        {
            Dependency.Use();
        }
    }
}
```

<span data-ttu-id="6ea33-307">Dit is een eenvoudige container voor de afhankelijkheid, `Shared.Dependency.dll` maar u moet er rekening mee houden als de .net API voor uw functionaliteit die door de cmdlets in de andere assembly voor Power shell wordt verpakt.</span><span class="sxs-lookup"><span data-stu-id="6ea33-307">This is a simple container for the dependency, `Shared.Dependency.dll`, but you should think of it as the .NET API for your functionality that the cmdlets in the other assembly wrap for PowerShell.</span></span>

<span data-ttu-id="6ea33-308">De cmdlet `AlcModule.Cmdlets.dll` ziet er als volgt uit:</span><span class="sxs-lookup"><span data-stu-id="6ea33-308">The cmdlet in `AlcModule.Cmdlets.dll` looks like this:</span></span>

```csharp
// Reference our module's Engine implementation here
using AlcModule.Engine;

namespace AlcModule.Cmdlets
{
    [Cmdlet(VerbsDiagnostic.Test, "AlcModule")]
    public class TestAlcModuleCommand : Cmdlet
    {
        protected override void EndProcessing()
        {
            AlcEngine.Use();
            WriteObject("done!");
        }
    }
}
```

<span data-ttu-id="6ea33-309">Als we op dit moment **AlcModule** laden en uitvoeren `Test-AlcModule` , krijgen we een `FileNotFoundException` wanneer de standaard-ALC wordt geladen `Alc.Engine.dll` om uit te voeren `EndProcessing()` .</span><span class="sxs-lookup"><span data-stu-id="6ea33-309">At this point, if we were to load **AlcModule** and run `Test-AlcModule`, we get a `FileNotFoundException` when the default ALC tries to load `Alc.Engine.dll` to run `EndProcessing()`.</span></span> <span data-ttu-id="6ea33-310">Dit is goed, omdat dit betekent dat de standaard ALC geen afhankelijkheden kan vinden die we willen verbergen.</span><span class="sxs-lookup"><span data-stu-id="6ea33-310">This is good, since it means the default ALC can't find the dependencies we want to hide.</span></span>

<span data-ttu-id="6ea33-311">Nu moeten we code toevoegen `AlcModule.Cmdlets.dll` , zodat u weet hoe u deze kunt oplossen `AlcModule.Engine.dll` .</span><span class="sxs-lookup"><span data-stu-id="6ea33-311">Now we need to add code to `AlcModule.Cmdlets.dll` so that it knows how to resolve `AlcModule.Engine.dll`.</span></span> <span data-ttu-id="6ea33-312">Eerst moeten we onze aangepaste ALC definiëren waarmee de assembly's worden omgezet in de map van de module `Dependencies` :</span><span class="sxs-lookup"><span data-stu-id="6ea33-312">First we must define our custom ALC that will resolve assemblies from our module's `Dependencies` directory:</span></span>

```csharp
namespace AlcModule.Cmdlets
{
    internal class AlcModuleAssemblyLoadContext : AssemblyLoadContext
    {
        private readonly string _dependencyDirPath;

        public AlcModuleAssemblyLoadContext(string dependencyDirPath)
        {
            _dependencyDirPath = dependencyDirPath;
        }

        protected override Assembly Load(AssemblyName assemblyName)
        {
            // We do the simple logic here of
            // looking for an assembly of the given name
            // in the configured dependency directory
            string assemblyPath = Path.Combine(
                _dependencyDirPath,
                $"{assemblyName.Name}.dll");

            // The ALC must use inherited methods to load assemblies
            // Assembly.Load*() won't work here
            return LoadFromAssemblyPath(assemblyPath);
        }
    }
}
```

<span data-ttu-id="6ea33-313">Vervolgens moeten we onze aangepaste ALC koppelen aan de standaard `Resolving` gebeurtenis alc. Dit is de ALC-versie van de `AssemblyResolve` gebeurtenis op toepassings domeinen.</span><span class="sxs-lookup"><span data-stu-id="6ea33-313">Then we need to hook up our custom ALC to the default ALC's `Resolving` event, which is the ALC version of the `AssemblyResolve` event on Application Domains.</span></span> <span data-ttu-id="6ea33-314">Deze gebeurtenis wordt geactiveerd `AlcModule.Engine.dll` wanneer deze `EndProcessing()` wordt aangeroepen.</span><span class="sxs-lookup"><span data-stu-id="6ea33-314">This event is fired to find `AlcModule.Engine.dll` when `EndProcessing()` is called.</span></span>

```csharp
namespace AlcModule.Cmdlets
{
    public class AlcModuleResolveEventHandler : IModuleAssemblyInitializer, IModuleAssemblyCleanup
    {
        // Get the path of the dependency directory.
        // In this case we find it relative to the AlcModule.Cmdlets.dll location
        private static readonly string s_dependencyDirPath = Path.GetFullPath(
            Path.Combine(
                Path.GetDirectoryName(Assembly.GetExecutingAssembly().Location),
                "Dependencies"));

        private static readonly AlcModuleAssemblyLoadContext s_dependencyAlc = new AlcModuleAssemblyLoadContext(s_dependencyDirPath);

        public void OnImport()
        {
            // Add the Resolving event handler here
            AssemblyLoadContext.Default.Resolving += ResolveAlcEngine;
        }

        public void OnRemove()
        {
          // Remove the Resolving event handler here
          AssemblyLoadContext.Default.Resolving -= ResolveAlcEngine;
        }

        private static Assembly ResolveAlcEngine(
            AssemblyLoadContext defaultAlc,
            AssemblyName assemblyToResolve)
        {
            // We only want to resolve the Alc.Engine.dll assembly here.
            // Because this will be loaded into the custom ALC,
            // all of *its* dependencies will be resolved
            // by the logic we defined for that ALC's implementation.
            //
            // Note that we are safe in our assumption that the name is enough
            // to distinguish our assembly here,
            // since it's unique to our module.
            // There should be no other AlcModule.Engine.dll on the system.
            if (!assemblyToResolve.Name.Equals("AlcModule.Engine"))
            {
                return null;
            }

            // Allow our ALC to handle the directory discovery concept
            //
            // This is where Alc.Engine.dll is loaded into our custom ALC
            // and then passed through into PowerShell's ALC,
            // becoming the bridge between both
            return s_dependencyAlc.LoadFromAssemblyName(assemblyToResolve);
        }
    }
}
```

<span data-ttu-id="6ea33-315">Bekijk met de nieuwe implementatie de volg orde van de aanroepen die optreden wanneer de module wordt geladen en `Test-AlcModule` wordt uitgevoerd:</span><span class="sxs-lookup"><span data-stu-id="6ea33-315">With the new implementation, take a look at the sequence of calls that occurs when the module is loaded and `Test-AlcModule` is run:</span></span>

![Sequentie diagram van aanroepen met behulp van de aangepaste ALC voor het laden van afhankelijkheden](./media/resolving-dependency-conflicts/alc-sequence.png)

<span data-ttu-id="6ea33-317">Enkele belang rijke punten zijn:</span><span class="sxs-lookup"><span data-stu-id="6ea33-317">Some points of interest are:</span></span>

- <span data-ttu-id="6ea33-318">De `IModuleAssemblyInitializer` wordt eerst uitgevoerd wanneer de module wordt geladen en de `Resolving` gebeurtenis wordt ingesteld.</span><span class="sxs-lookup"><span data-stu-id="6ea33-318">The `IModuleAssemblyInitializer` is run first when the module loads and sets the `Resolving` event.</span></span>
- <span data-ttu-id="6ea33-319">De afhankelijkheden worden pas geladen nadat het programma `Test-AlcModule` is uitgevoerd en de bijbehorende `EndProcessing()` methode is aangeroepen.</span><span class="sxs-lookup"><span data-stu-id="6ea33-319">We don't load the dependencies until `Test-AlcModule` is run and its `EndProcessing()` method is called.</span></span>
- <span data-ttu-id="6ea33-320">Wanneer `EndProcessing()` wordt aangeroepen, kan de standaard opdracht ALC `AlcModule.Engine.dll` de gebeurtenis niet vinden en deze wordt geactiveerd `Resolving` .</span><span class="sxs-lookup"><span data-stu-id="6ea33-320">When `EndProcessing()` is called, the default ALC fails to find `AlcModule.Engine.dll` and fires the `Resolving` event.</span></span>
- <span data-ttu-id="6ea33-321">Onze gebeurtenis-handler koppelt de aangepaste ALC aan de standaard ALC en wordt `AlcModule.Engine.dll` alleen geladen.</span><span class="sxs-lookup"><span data-stu-id="6ea33-321">Our event handler hooks up the custom ALC to the default ALC and loads `AlcModule.Engine.dll` only.</span></span>
- <span data-ttu-id="6ea33-322">Wanneer `AlcEngine.Use()` wordt aangeroepen in `AlcModule.Engine.dll` , begint de aangepaste ALC opnieuw in om op te lossen `Shared.Dependency.dll` .</span><span class="sxs-lookup"><span data-stu-id="6ea33-322">When `AlcEngine.Use()` is called within `AlcModule.Engine.dll`, the custom ALC again kicks in to resolve `Shared.Dependency.dll`.</span></span> <span data-ttu-id="6ea33-323">Met name de oplossing wordt altijd door _ons_ geladen `Shared.Dependency.dll` omdat er nooit conflicten zijn in de standaard ALC en er alleen in onze Directory wordt gezocht `Dependencies` .</span><span class="sxs-lookup"><span data-stu-id="6ea33-323">Specifically, it always loads _our_ `Shared.Dependency.dll` since it never conflicts with anything in the default ALC and only looks in our `Dependencies` directory.</span></span>

<span data-ttu-id="6ea33-324">Het samen stellen van de implementatie, onze nieuwe indeling van de bron code ziet er als volgt uit:</span><span class="sxs-lookup"><span data-stu-id="6ea33-324">Assembling the implementation, our new source code layout looks like this:</span></span>

```
+ AlcModule.psd1
+ src/
  + AlcModule.Cmdlets/
  | + AlcModule.Cmdlets.csproj
  | + TestAlcModuleCommand.cs
  | + AlcModuleAssemblyLoadContext.cs
  | + AlcModuleInitializer.cs
  |
  + AlcModule.Engine/
  | + AlcModule.Engine.csproj
  | + AlcEngine.cs
```

<span data-ttu-id="6ea33-325">AlcModule. cmdlets. csproj ziet er als volgt uit:</span><span class="sxs-lookup"><span data-stu-id="6ea33-325">AlcModule.Cmdlets.csproj looks like:</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">
  <PropertyGroup>
    <TargetFramework>netcoreapp3.1</TargetFramework>
  </PropertyGroup>
  <ItemGroup>
    <ProjectReference Include="..\AlcModule.Engine\AlcModule.Engine.csproj" />
    <PackageReference Include="Microsoft.PowerShell.Sdk" Version="7.0.1" PrivateAssets="all" />
  </ItemGroup>
</Project>
```

<span data-ttu-id="6ea33-326">AlcModule. engine. csproj ziet er als volgt uit:</span><span class="sxs-lookup"><span data-stu-id="6ea33-326">AlcModule.Engine.csproj looks like this:</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">
  <PropertyGroup>
    <TargetFramework>netcoreapp3.1</TargetFramework>
  </PropertyGroup>
  <ItemGroup>
    <PackageReference Include="Shared.Dependency" Version="1.0.0" />
  </ItemGroup>
</Project>
```

<span data-ttu-id="6ea33-327">Als we de module bouwen, is onze strategie dus:</span><span class="sxs-lookup"><span data-stu-id="6ea33-327">So, when we build the module, our strategy is:</span></span>

- <span data-ttu-id="6ea33-328">PE `AlcModule.Engine`</span><span class="sxs-lookup"><span data-stu-id="6ea33-328">Build `AlcModule.Engine`</span></span>
- <span data-ttu-id="6ea33-329">PE `AlcModule.Cmdlets`</span><span class="sxs-lookup"><span data-stu-id="6ea33-329">Build `AlcModule.Cmdlets`</span></span>
- <span data-ttu-id="6ea33-330">Kopieer alles vanuit `AlcModule.Engine` naar de `Dependencies` Directory en onthoud wat er is gekopieerd</span><span class="sxs-lookup"><span data-stu-id="6ea33-330">Copy everything from `AlcModule.Engine` into the `Dependencies` directory, and remember what we copied</span></span>
- <span data-ttu-id="6ea33-331">Kopieer alles van niet `AlcModule.Cmdlets` in `AlcModule.Engine` de map van de basis module</span><span class="sxs-lookup"><span data-stu-id="6ea33-331">Copy everything from `AlcModule.Cmdlets` that wasn't in `AlcModule.Engine` into the base module directory</span></span>

<span data-ttu-id="6ea33-332">Omdat de module-indeling hier van cruciaal belang is voor schei ding van afhankelijkheden, is dit een bouw script dat u vanuit de hoofdmap van de bron kunt gebruiken:</span><span class="sxs-lookup"><span data-stu-id="6ea33-332">Since the module layout here is so crucial to dependency separation, here's a build script to use from the source root:</span></span>

```powershell
param(
    # The .NET build configuration
    [ValidateSet('Debug', 'Release')]
    [string]
    $Configuration = 'Debug'
)

# Convenient reusable constants
$mod = "AlcModule"
$netcore = "netcoreapp3.1"
$copyExtensions = @('.dll', '.pdb')

# Source code locations
$src = "$PSScriptRoot/src"
$engineSrc = "$src/$mod.Engine"
$cmdletsSrc = "$src/$mod.Cmdlets"

# Generated output locations
$outDir = "$PSScriptRoot/out/$mod"
$outDeps = "$outDir/Dependencies"

# Build AlcModule.Engine
Push-Location $engineSrc
dotnet publish -c $Configuration
Pop-Location

# Build AlcModule.Cmdlets
Push-Location $cmdletsSrc
dotnet publish -c $Configuration
Pop-Location

# Ensure out directory exists and is clean
Remove-Item -Path $outDir -Recurse -ErrorAction Ignore
New-Item -Path $outDir -ItemType Directory
New-Item -Path $outDeps -ItemType Directory

# Copy manifest
Copy-Item -Path "$PSScriptRoot/$mod.psd1"

# Copy each Engine asset and remember it
$deps = [System.Collections.Generic.Hashtable[string]]::new()
Get-ChildItem -Path "$engineSrc/bin/$Configuration/$netcore/publish/" |
    Where-Object { $_.Extension -in $copyExtensions } |
    ForEach-Object { [void]$deps.Add($_.Name); Copy-Item -Path $_.FullName -Destination $outDeps }

# Now copy each Cmdlets asset, not taking any found in Engine
Get-ChildItem -Path "$cmdletsSrc/bin/$Configuration/$netcore/publish/" |
    Where-Object { -not $deps.Contains($_.Name) -and $_.Extension -in $copyExtensions } |
    ForEach-Object { Copy-Item -Path $_.FullName -Destination $outDir }
```

<span data-ttu-id="6ea33-333">Ten slotte hebben we een algemene manier om een assembly-laad context te gebruiken om de afhankelijkheden van de module te isoleren die gedurende een periode robuust blijven naarmate er meer afhankelijkheden worden toegevoegd.</span><span class="sxs-lookup"><span data-stu-id="6ea33-333">Finally, we have a general way to use an Assembly Load Context to isolate our module's dependencies that remains robust over time as more dependencies are added.</span></span>

<span data-ttu-id="6ea33-334">Ga naar deze [github-opslag plaats](https://github.com/rjmholt/ModuleDependencyIsolationExample)voor een meer gedetailleerd voor beeld.</span><span class="sxs-lookup"><span data-stu-id="6ea33-334">For a more detailed example, go to this [GitHub repository](https://github.com/rjmholt/ModuleDependencyIsolationExample).</span></span> <span data-ttu-id="6ea33-335">In dit voor beeld ziet u hoe u een module migreert voor gebruik van een ALC, terwijl de module in .NET Framework werkt.</span><span class="sxs-lookup"><span data-stu-id="6ea33-335">This example demonstrates how to migrate a module to use an ALC, while keeping that module working in .NET Framework.</span></span> <span data-ttu-id="6ea33-336">Ook wordt uitgelegd hoe u .NET Standard en Power shell Standard kunt gebruiken om de kern implementatie te vereenvoudigen.</span><span class="sxs-lookup"><span data-stu-id="6ea33-336">It also show how to use .NET Standard and PowerShell Standard to simplify the core implementation.</span></span>

### <a name="assembly-resolve-handler-for-side-by-side-loading-with-assemblyloadfile"></a><span data-ttu-id="6ea33-337">Assembly-afhandelings-handler voor naast elkaar laden met `Assembly.LoadFile()`</span><span class="sxs-lookup"><span data-stu-id="6ea33-337">Assembly resolve handler for side-by-side loading with `Assembly.LoadFile()`</span></span>

<span data-ttu-id="6ea33-338">Een andere, mogelijk eenvoudiger, manier om het laden van gelijktijdige assembly's te verzorgen, is door een `AssemblyResolve` gebeurtenis te koppelen aan `Assembly.LoadFile()` .</span><span class="sxs-lookup"><span data-stu-id="6ea33-338">Another, possibly simpler, way to achieve side-by-side assembly loading is to hook up an `AssemblyResolve` event to `Assembly.LoadFile()`.</span></span> <span data-ttu-id="6ea33-339">Met `Assembly.LoadFile()` kunt u het voor deel doen van de eenvoudigste oplossing voor het implementeren en werken met .net core en .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="6ea33-339">Using `Assembly.LoadFile()` has the advantage of being the simplest solution to implement and works with both .NET Core and .NET Framework.</span></span>

<span data-ttu-id="6ea33-340">Om dit weer te geven, gaan we een beknopt voor beeld bekijken van een implementatie waarbij ideeën worden gecombineerd in het voor beeld van dynamische bindings omleiding en het bovenstaande voor beeld van de assembly-belasting.</span><span class="sxs-lookup"><span data-stu-id="6ea33-340">To show this, let's take a look at a quick example of an implementation that combines ideas from our dynamic binding redirect example, and the Assembly Load Context example above.</span></span>

<span data-ttu-id="6ea33-341">We noemen deze module **LoadFileModule**, die een trivial opdracht heeft `Test-LoadFile [-Path] <path>` .</span><span class="sxs-lookup"><span data-stu-id="6ea33-341">We'll call this module **LoadFileModule**, which has a trivial command `Test-LoadFile [-Path] <path>`.</span></span> <span data-ttu-id="6ea33-342">Deze module heeft een afhankelijkheid van de `CsvHelper` Assembly (versie 15.0.5).</span><span class="sxs-lookup"><span data-stu-id="6ea33-342">This module takes a dependency on the `CsvHelper` assembly (version 15.0.5).</span></span>

<span data-ttu-id="6ea33-343">Net als bij de module ALC moeten we eerst de module splitsen in twee delen.</span><span class="sxs-lookup"><span data-stu-id="6ea33-343">As with the ALC module, we must first split up the module into two pieces.</span></span>

<span data-ttu-id="6ea33-344">Het eerste deel heeft de daad werkelijke implementatie `LoadFileModule.Engine` :</span><span class="sxs-lookup"><span data-stu-id="6ea33-344">The first part does the actual implementation, `LoadFileModule.Engine`:</span></span>

```csharp
using CsvHelper;

namespace LoadFileModule.Engine
{
    public class Runner
    {
        public void Use(string path)
        {
            // Here's where we use the CsvHelper dependency
            using (var reader = new StreamReader(path))
            using (var csvReader = new CsvReader(reader, CultureInfo.InvariantCulture))
            {
                // Imagine we do something useful here...
            }
        }
    }
}
```

<span data-ttu-id="6ea33-345">Het tweede deel is wat Power shell rechtstreeks laadt `LoadFileModule.Cmdlets` .</span><span class="sxs-lookup"><span data-stu-id="6ea33-345">The second part is what PowerShell loads directly, `LoadFileModule.Cmdlets`.</span></span> <span data-ttu-id="6ea33-346">We gebruiken een strategie die vergelijkbaar is met de module ALC, waar we afhankelijkheden in een afzonderlijke map isoleren.</span><span class="sxs-lookup"><span data-stu-id="6ea33-346">We use a strategy similar to the ALC module, where we isolate dependencies in a separate directory.</span></span> <span data-ttu-id="6ea33-347">Maar deze keer laden we alle assembly's in met een oplossings gebeurtenis in plaats van alleen `LoadFileModule.Engine.dll` .</span><span class="sxs-lookup"><span data-stu-id="6ea33-347">But this time, we load all assemblies in with a resolve event rather than just `LoadFileModule.Engine.dll`.</span></span>

```csharp
using LoadFileModule.Engine;

namespace LoadFileModule.Cmdlets
{
    // Actual cmdlet definition
    [Cmdlet(VerbsDiagnostic.Test, "LoadFile")]
    public class TestLoadFileCommand : Cmdlet
    {
        [Parameter(Mandatory = true)]
        public string Path { get; set; }

        protected override void EndProcessing()
        {
            // Here's where we use LoadFileModule.Engine
            new Runner().Use(Path);
        }
    }

    // This class controls our dependency resolution
    public class ModuleContextHandler : IModuleAssemblyInitializer, IModuleAssemblyCleanup
    {
        // We catalog our dependencies here to ensure we don't load anything else
        private static IReadOnlyDictionary<string, int> s_dependencies = new Dictionary<string, int>
        {
            { "CsvHelper", 15 },
        };

        // Set up the path to our dependency directory within the module
        private static string s_dependenciesDirPath = Path.GetFullPath(
            Path.Combine(
                Path.GetDirectoryName(Assembly.GetExecutingAssembly().Location),
                "Dependencies"));

        // This makes sure we only try to resolve dependencies when the module is loaded
        private static bool s_engineLoaded = false;

        public void OnImport()
          {
            // Set up our event when the module is loaded
            AppDomain.CurrentDomain.AssemblyResolve += HandleResolveEvent;
        }

        public void OnRemove(PSModuleInfo psModuleInfo)
        {
            // Unset the event when the module is unloaded
            AppDomain.CurrentDomain.AssemblyResolve -= HandleResolveEvent;
        }

        private static Assembly HandleResolveEvent(object sender, ResolveEventArgs args)
        {
            var asmName = new AssemblyName(args.Name);

            // First we want to know if this is the top-level assembly
            if (asmName.Name.Equals("LoadFileModule.Engine"))
            {
                s_engineLoaded = true;
                return Assembly.LoadFile(Path.Combine(s_dependenciesDirPath, "Unrelated.Engine.dll"));
            }

            // Otherwise, if that assembly has been loaded, we must try to resolve its dependencies too
            if (s_engineLoaded
                && s_dependencies.TryGetValue(asmName.Name, out int requiredMajorVersion)
                && asmName.Version.Major == requiredMajorVersion)
            {
                string asmPath = Path.Combine(s_dependenciesDirPath, $"{asmName.Name}.dll");
                return Assembly.LoadFile(asmPath);
            }

            return null;
        }
    }
}
```

<span data-ttu-id="6ea33-348">Ten slotte is de lay-out van de module ook vergelijkbaar met de module ALC:</span><span class="sxs-lookup"><span data-stu-id="6ea33-348">Finally, the layout of the module is also similar to the ALC module:</span></span>

```
LoadFileModule/
  + LoadFileModule.Cmdlets.dll
  + LoadFileModule.psd1
  + Dependencies/
  |  + LoadFileModule.Engine.dll
  |  + CsvHelper.dll
```

<span data-ttu-id="6ea33-349">Als deze structuur is geïmplementeerd, ondersteunt **LoadFileModule** nu naast andere modules met een afhankelijkheid van **CsvHelper**.</span><span class="sxs-lookup"><span data-stu-id="6ea33-349">With this structure in place, **LoadFileModule** now supports being loaded alongside other modules with a dependency on **CsvHelper**.</span></span>

<span data-ttu-id="6ea33-350">Omdat onze handler van toepassing is op **alle** `AssemblyResolve` gebeurtenissen in het toepassings domein, moeten we een aantal specifieke ontwerp opties hier maken:</span><span class="sxs-lookup"><span data-stu-id="6ea33-350">Because our handler applies to **all** `AssemblyResolve` events across the Application Domain, we need to make some specific design choices here:</span></span>

- <span data-ttu-id="6ea33-351">Om het venster te beperken waarin de gebeurtenis kan worden verstoord door andere belasting, beginnen we alleen de verwerking van algemene afhankelijkheden te verwerken nadat deze `LoadFileModule.Engine.dll` is geladen.</span><span class="sxs-lookup"><span data-stu-id="6ea33-351">To narrow the window in which our event may interfere with other loading, we only start handling general dependency loading after `LoadFileModule.Engine.dll` has been loaded.</span></span>
- <span data-ttu-id="6ea33-352">Er `LoadFileModule.Engine.dll` wordt naar de map met afhankelijkheden gepusht, zodat deze wordt geladen door een `LoadFile()` aanroep in plaats van met Power shell.</span><span class="sxs-lookup"><span data-stu-id="6ea33-352">We push `LoadFileModule.Engine.dll` out into the Dependencies directory, so that it's loaded by a `LoadFile()` call rather than by PowerShell.</span></span> <span data-ttu-id="6ea33-353">Dit betekent dat een eigen afhankelijkheids belasting altijd een `AssemblyResolve` gebeurtenis verhoogt, zelfs als een andere `CsvHelper.dll` (bijvoorbeeld) wordt geladen in Power shell.</span><span class="sxs-lookup"><span data-stu-id="6ea33-353">This means its own dependency loads always raise an `AssemblyResolve` event, even if another `CsvHelper.dll` (for example) is loaded in PowerShell.</span></span>
  <span data-ttu-id="6ea33-354">Dit geeft ons de mogelijkheid om de juiste afhankelijkheid te vinden.</span><span class="sxs-lookup"><span data-stu-id="6ea33-354">This gives us the opportunity to find the correct dependency.</span></span>
- <span data-ttu-id="6ea33-355">Omdat we alleen de specifieke afhankelijkheden voor onze module moeten omzetten, kunnen we een woorden lijst met namen en versies van afhankelijkheden in onze handler coderen.</span><span class="sxs-lookup"><span data-stu-id="6ea33-355">Since we must only resolve the specific dependencies for our module, we're forced to code a dictionary of dependency names and versions into our handler.</span></span> <span data-ttu-id="6ea33-356">In ons bijzonder geval zou u de eigenschap kunnen gebruiken `ResolveEventArgs.RequestingAssembly` om te laten zien of de `CsvHelper` module wordt aangevraagd.</span><span class="sxs-lookup"><span data-stu-id="6ea33-356">In our particular case, it would be possible to use the `ResolveEventArgs.RequestingAssembly` property to work out whether `CsvHelper` is being requested by our module.</span></span> <span data-ttu-id="6ea33-357">Dit werkt echter niet voor afhankelijkheden van afhankelijkheden. bijvoorbeeld, als `CsvHelper` er een gebeurtenis optreedt `AssemblyResolve` .</span><span class="sxs-lookup"><span data-stu-id="6ea33-357">But this doesn't work for dependencies of dependencies; for example, if `CsvHelper` itself raised an `AssemblyResolve` event.</span></span> <span data-ttu-id="6ea33-358">Er zijn andere en moeilijker manieren om dit te doen, zoals het vergelijken van aangevraagde assembly's met de meta gegevens van assembly's in de `Dependencies` map.</span><span class="sxs-lookup"><span data-stu-id="6ea33-358">There are other, harder ways to do this, such as comparing requested assemblies to the metadata of assemblies in the `Dependencies` directory.</span></span> <span data-ttu-id="6ea33-359">Maar in dit voor beeld hebben we deze controle duidelijker gemaakt om het probleem te markeren en het voor beeld te vereenvoudigen.</span><span class="sxs-lookup"><span data-stu-id="6ea33-359">But, in this example, we've made this checking more explicit to both highlight the issue and simplify the example.</span></span>

<span data-ttu-id="6ea33-360">Dit is het belangrijkste verschil tussen de `LoadFile()` strategie en de ALC-strategie: de `AssemblyResolve` gebeurtenis moet alle belastingen in het toepassings domein onderhouden, waardoor het veel moeilijker is om te zorgen dat de afhankelijkheids resolutie wordt Tangled met andere modules.</span><span class="sxs-lookup"><span data-stu-id="6ea33-360">This is the key difference between the `LoadFile()` strategy and the ALC strategy: the `AssemblyResolve` event must service all loads in the Application Domain, making it much harder to keep our dependency resolution from being tangled with other modules.</span></span> <span data-ttu-id="6ea33-361">Het ontbreken van ALCs in .NET Framework maakt deze optie echter een goed idee.</span><span class="sxs-lookup"><span data-stu-id="6ea33-361">However, the lack of ALCs in .NET Framework makes this option worth understanding.</span></span>

### <a name="custom-application-domains"></a><span data-ttu-id="6ea33-362">Aangepaste toepassings domeinen</span><span class="sxs-lookup"><span data-stu-id="6ea33-362">Custom Application Domains</span></span>

<span data-ttu-id="6ea33-363">De laatste en meest extreme optie voor het isoleren van de assembly is het gebruik van aangepaste toepassings domeinen.</span><span class="sxs-lookup"><span data-stu-id="6ea33-363">The final and most extreme option for assembly isolation is to use custom Application Domains.</span></span>
<span data-ttu-id="6ea33-364">Toepassings domeinen (gebruikt in het meervoud) zijn alleen beschikbaar in .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="6ea33-364">Application Domains (used in the plural) are only available in .NET Framework.</span></span> <span data-ttu-id="6ea33-365">Ze worden gebruikt om in-process-isolatie te bieden tussen onderdelen van een .NET-toepassing.</span><span class="sxs-lookup"><span data-stu-id="6ea33-365">They are used to provide in-process isolation between parts of a .NET application.</span></span> <span data-ttu-id="6ea33-366">Een van de toepassingen is het isoleren van assembly-belastingen van elkaar binnen hetzelfde proces.</span><span class="sxs-lookup"><span data-stu-id="6ea33-366">One of the uses is to isolate assembly loads from each other within the same process.</span></span>

<span data-ttu-id="6ea33-367">Toepassings domeinen zijn echter boundary's voor serialisatie.</span><span class="sxs-lookup"><span data-stu-id="6ea33-367">However, Application Domains are serialization boundaries.</span></span> <span data-ttu-id="6ea33-368">Er kan niet naar objecten in één toepassings domein worden verwezen en deze kunnen niet rechtstreeks worden gebruikt door objecten in een ander toepassings domein.</span><span class="sxs-lookup"><span data-stu-id="6ea33-368">Objects in one Application Domain can't be referenced and used directly by objects in another Application Domain.</span></span> <span data-ttu-id="6ea33-369">U kunt dit probleem omzeilen door de implementatie uit te voeren `MarshalByRefObject` .</span><span class="sxs-lookup"><span data-stu-id="6ea33-369">You can work around this by implementing `MarshalByRefObject`.</span></span> <span data-ttu-id="6ea33-370">Maar wanneer u de typen niet beheert, net als bij afhankelijkheden, is het niet mogelijk om hier een implementatie af te dwingen.</span><span class="sxs-lookup"><span data-stu-id="6ea33-370">But when you don't control the types, as is often the case with dependencies, it's not possible to force an implementation here.</span></span> <span data-ttu-id="6ea33-371">De enige oplossing is om grote architectuur wijzigingen te maken.</span><span class="sxs-lookup"><span data-stu-id="6ea33-371">The only solution is to make large architectural changes.</span></span> <span data-ttu-id="6ea33-372">De grens van de serialisatie heeft ook ernstige gevolgen voor de prestaties.</span><span class="sxs-lookup"><span data-stu-id="6ea33-372">The serialization boundary also has serious performance implications.</span></span>

<span data-ttu-id="6ea33-373">Omdat toepassings domeinen deze ernstige beperking hebben, gecompliceerd zijn om te implementeren en alleen werken in .NET Framework, geven we geen voor beeld van hoe u deze hier kunt gebruiken.</span><span class="sxs-lookup"><span data-stu-id="6ea33-373">Because Application Domains have this serious limitation, are complicated to implement, and only work in .NET Framework, we won't give an example of how you might use them here.</span></span> <span data-ttu-id="6ea33-374">Hoewel ze als een mogelijkheid worden vermeld, worden ze niet aanbevolen.</span><span class="sxs-lookup"><span data-stu-id="6ea33-374">While they're worth mentioning as a possibility, they're not recommended.</span></span>

<span data-ttu-id="6ea33-375">Als u geïnteresseerd bent in het gebruik van een aangepast toepassings domein, kunnen de volgende koppelingen helpen:</span><span class="sxs-lookup"><span data-stu-id="6ea33-375">If you're interested in trying to use a custom Application Domain, the following links might help:</span></span>

- [<span data-ttu-id="6ea33-376">Conceptuele documentatie over toepassings domeinen</span><span class="sxs-lookup"><span data-stu-id="6ea33-376">Conceptual documentation on Application Domains</span></span>](/dotnet/framework/app-domains/application-domains)
- [<span data-ttu-id="6ea33-377">Voor beelden voor het gebruik van toepassings domeinen</span><span class="sxs-lookup"><span data-stu-id="6ea33-377">Examples for using Application Domains</span></span>](/dotnet/framework/app-domains/use)

## <a name="solutions-for-dependency-conflicts-that-dont-work-for-powershell"></a><span data-ttu-id="6ea33-378">Oplossingen voor conflicten met afhankelijkheden die niet geschikt zijn voor Power shell</span><span class="sxs-lookup"><span data-stu-id="6ea33-378">Solutions for dependency conflicts that don't work for PowerShell</span></span>

<span data-ttu-id="6ea33-379">Tot slot gaan we een overzicht van een aantal mogelijkheden die beschikbaar zijn bij het zoeken naar .NET-afhankelijkheids conflicten in .NET die kunnen worden getoezegging, maar over het algemeen niet werken voor Power shell.</span><span class="sxs-lookup"><span data-stu-id="6ea33-379">Finally, we'll address some possibilities that come up when researching .NET dependency conflicts in .NET that can look promising, but generally won't work for PowerShell.</span></span>

<span data-ttu-id="6ea33-380">Deze oplossingen hebben het algemene thema dat ze wijzigen in implementatie configuraties voor een omgeving waar u de toepassing beheert en mogelijk de hele machine.</span><span class="sxs-lookup"><span data-stu-id="6ea33-380">These solutions have the common theme that they are changes to deployment configurations for an environment where you control the application and possibly the entire machine.</span></span> <span data-ttu-id="6ea33-381">Deze oplossingen zijn gericht op scenario's zoals webservers en andere toepassingen die worden geïmplementeerd in Server omgevingen, waarbij de omgeving bedoeld is voor het hosten van de toepassing en niet kan worden geconfigureerd door de implementatie gebruiker.</span><span class="sxs-lookup"><span data-stu-id="6ea33-381">These solutions are oriented toward scenarios like web servers and other applications deployed to server environments, where the environment is intended to host the application and is free to be configured by the deploying user.</span></span> <span data-ttu-id="6ea33-382">Ze zijn ook vaak zeer veel .NET Framework gericht, wat betekent dat ze niet werken met Power shell 6 of hoger.</span><span class="sxs-lookup"><span data-stu-id="6ea33-382">They also tend to be very much .NET Framework oriented, meaning they do not work with PowerShell 6 or above.</span></span>

<span data-ttu-id="6ea33-383">Als u weet dat uw module alleen wordt gebruikt in Windows Power shell 5,1-omgevingen waarvoor u de volledige controle hebt, zijn er mogelijk opties.</span><span class="sxs-lookup"><span data-stu-id="6ea33-383">If you know that your module is only used in Windows PowerShell 5.1 environments that you have total control over, some of these may be options.</span></span> <span data-ttu-id="6ea33-384">In **het algemeen mogen modules de status van de globale machine zoals deze niet wijzigen**.</span><span class="sxs-lookup"><span data-stu-id="6ea33-384">In general however, **modules should not modify global machine state like this**.</span></span> <span data-ttu-id="6ea33-385">Het kan configuraties verstoren die problemen veroorzaken in `powershell.exe` , andere modules of andere afhankelijke toepassingen die ervoor zorgen dat uw module op onverwachte wijze mislukt.</span><span class="sxs-lookup"><span data-stu-id="6ea33-385">It can break configurations that cause problems in `powershell.exe`, other modules, or other dependent applications that cause your module to fail in unexpected ways.</span></span>

### <a name="static-binding-redirect-with-appconfig-to-force-using-the-same-dependency-version"></a><span data-ttu-id="6ea33-386">Statische binding omleiding met app.config om te forceren met dezelfde afhankelijkheids versie</span><span class="sxs-lookup"><span data-stu-id="6ea33-386">Static binding redirect with app.config to force using the same dependency version</span></span>

<span data-ttu-id="6ea33-387">.NET Framework toepassingen kunnen gebruikmaken van een `app.config` bestand om een deel van het gedrag van de toepassing declaratief te configureren.</span><span class="sxs-lookup"><span data-stu-id="6ea33-387">.NET Framework applications can take advantage of an `app.config` file to configure some of the application's behaviors declaratively.</span></span> <span data-ttu-id="6ea33-388">Het is mogelijk om een vermelding te schrijven `app.config` die een assembly-binding configureert om assembly-belasting om te leiden naar een bepaalde versie.</span><span class="sxs-lookup"><span data-stu-id="6ea33-388">It's possible to write an `app.config` entry that configures assembly binding to redirect assembly loading to a particular version.</span></span>

<span data-ttu-id="6ea33-389">Twee problemen met dit voor Power shell zijn:</span><span class="sxs-lookup"><span data-stu-id="6ea33-389">Two issues with this for PowerShell are:</span></span>

- <span data-ttu-id="6ea33-390">.NET core biedt geen ondersteuning `app.config` , dus deze oplossing is alleen van toepassing op `powershell.exe` .</span><span class="sxs-lookup"><span data-stu-id="6ea33-390">.NET Core does not support `app.config`, so this solution only applies to `powershell.exe`.</span></span>
- <span data-ttu-id="6ea33-391">`powershell.exe` is een gedeelde toepassing die zich in de map bevindt `System32` .</span><span class="sxs-lookup"><span data-stu-id="6ea33-391">`powershell.exe` is a shared application that lives in the `System32` directory.</span></span> <span data-ttu-id="6ea33-392">Waarschijnlijk is het niet mogelijk om de inhoud van uw module op veel systemen te wijzigen.</span><span class="sxs-lookup"><span data-stu-id="6ea33-392">It's likely that your module won't be able to modify its contents on many systems.</span></span> <span data-ttu-id="6ea33-393">Zelfs als dit mogelijk is, kan het wijzigen `app.config` van een bestaande configuratie verstoren of invloed hebben op het laden van andere modules.</span><span class="sxs-lookup"><span data-stu-id="6ea33-393">Even if it can, modifying the `app.config` could break an existing configuration or affect the loading of other modules.</span></span>

### <a name="setting-codebase-with-appconfig"></a><span data-ttu-id="6ea33-394">Instellen `codebase` met app.config</span><span class="sxs-lookup"><span data-stu-id="6ea33-394">Setting `codebase` with app.config</span></span>

<span data-ttu-id="6ea33-395">Om dezelfde redenen voor het configureren `codebase` van de instelling in, `app.config` gaat u niet werken in Power shell-modules.</span><span class="sxs-lookup"><span data-stu-id="6ea33-395">For the same reasons, trying to configure the `codebase` setting in `app.config` is not going to work in PowerShell modules.</span></span>

### <a name="installing-dependencies-to-the-global-assembly-cache-gac"></a><span data-ttu-id="6ea33-396">Afhankelijkheden installeren in de GAC (globale assembly-cache)</span><span class="sxs-lookup"><span data-stu-id="6ea33-396">Installing dependencies to the Global Assembly Cache (GAC)</span></span>

<span data-ttu-id="6ea33-397">Een andere manier om conflicten met de afhankelijkheids versie op te lossen in .NET Framework is door afhankelijkheden te installeren in de GAC, zodat verschillende versies naast elkaar kunnen worden geladen vanuit de GAC.</span><span class="sxs-lookup"><span data-stu-id="6ea33-397">Another way to resolve dependency version conflicts in .NET Framework is to install dependencies to the GAC, so that different versions can be loaded side-by-side from the GAC.</span></span>

<span data-ttu-id="6ea33-398">Opnieuw, voor Power shell-modules, zijn dit de belangrijkste problemen:</span><span class="sxs-lookup"><span data-stu-id="6ea33-398">Again, for PowerShell modules, the chief issues here are:</span></span>

- <span data-ttu-id="6ea33-399">De GAC is alleen van toepassing op .NET Framework, dus u kunt dit niet doen in Power shell 6 en hoger.</span><span class="sxs-lookup"><span data-stu-id="6ea33-399">The GAC only applies to .NET Framework, so this does not help in PowerShell 6 and above.</span></span>
- <span data-ttu-id="6ea33-400">Het installeren van assembly's in de GAC is een wijziging van de status van de globale machine en kan neven effecten in andere toepassingen of andere modules veroorzaken.</span><span class="sxs-lookup"><span data-stu-id="6ea33-400">Installing assemblies to the GAC is a modification of global machine state and may cause side-effects in other applications or to other modules.</span></span> <span data-ttu-id="6ea33-401">Het kan ook lastig zijn om goed te kunnen werken, zelfs als uw module de vereiste toegangs rechten heeft.</span><span class="sxs-lookup"><span data-stu-id="6ea33-401">It may also be difficult to do correctly, even when your module has the required access privileges.</span></span> <span data-ttu-id="6ea33-402">Het verkrijgen van een probleem kan ernstige problemen met de hele machine veroorzaken in andere .NET-toepassingen.</span><span class="sxs-lookup"><span data-stu-id="6ea33-402">Getting it wrong could cause serious, machine-wide issues in other .NET applications.</span></span>

## <a name="further-reading"></a><span data-ttu-id="6ea33-403">Meer informatie</span><span class="sxs-lookup"><span data-stu-id="6ea33-403">Further reading</span></span>

<span data-ttu-id="6ea33-404">Er is nog veel meer informatie over de afhankelijkheids conflicten voor .NET-assembly-versies.</span><span class="sxs-lookup"><span data-stu-id="6ea33-404">There's plenty more to read on .NET assembly version dependency conflicts.</span></span> <span data-ttu-id="6ea33-405">Hier vindt u een aantal leuke plaatsen in de weg:</span><span class="sxs-lookup"><span data-stu-id="6ea33-405">Here are some nice jumping off points:</span></span>

- [<span data-ttu-id="6ea33-406">.NET: Assembly's in .NET</span><span class="sxs-lookup"><span data-stu-id="6ea33-406">.NET: Assemblies in .NET</span></span>](/dotnet/standard/assembly/)
- [<span data-ttu-id="6ea33-407">.NET core: het algoritme voor het laden van beheerde assembly</span><span class="sxs-lookup"><span data-stu-id="6ea33-407">.NET Core: The managed assembly loading algorithm</span></span>](/dotnet/core/dependency-loading/loading-managed)
- [<span data-ttu-id="6ea33-408">.NET core: informatie over System. runtime. Loader. AssemblyLoadContext</span><span class="sxs-lookup"><span data-stu-id="6ea33-408">.NET Core: Understanding System.Runtime.Loader.AssemblyLoadContext</span></span>](/dotnet/core/dependency-loading/understanding-assemblyloadcontext)
- [<span data-ttu-id="6ea33-409">.NET core: discussie over side-by-side-oplossingen voor het laden van assembly</span><span class="sxs-lookup"><span data-stu-id="6ea33-409">.NET Core: Discussion about side-by-side assembly loading solutions</span></span>](https://github.com/dotnet/runtime/issues/13471)
- [<span data-ttu-id="6ea33-410">.NET Framework: assembly-versies omleiden</span><span class="sxs-lookup"><span data-stu-id="6ea33-410">.NET Framework: Redirecting assembly versions</span></span>](/dotnet/framework/configure-apps/redirect-assembly-versions)
- [<span data-ttu-id="6ea33-411">.NET Framework: Aanbevolen procedures voor het laden van assembly</span><span class="sxs-lookup"><span data-stu-id="6ea33-411">.NET Framework: Best practices for assembly loading</span></span>](/dotnet/framework/deployment/best-practices-for-assembly-loading)
- [<span data-ttu-id="6ea33-412">.NET Framework: hoe de runtime assembly's opzoekt</span><span class="sxs-lookup"><span data-stu-id="6ea33-412">.NET Framework: How the runtime locates assemblies</span></span>](/dotnet/framework/deployment/how-the-runtime-locates-assemblies)
- [<span data-ttu-id="6ea33-413">.NET Framework: ophalen van assembly laden</span><span class="sxs-lookup"><span data-stu-id="6ea33-413">.NET Framework: Resolve assembly loads</span></span>](/dotnet/standard/assembly/resolve-loads)
- [<span data-ttu-id="6ea33-414">Stack overflow: assembly-binding omleiding, hoe en waarom?</span><span class="sxs-lookup"><span data-stu-id="6ea33-414">StackOverflow: Assembly binding redirect, how and why?</span></span>](https://stackoverflow.com/questions/43365736/assembly-binding-redirect-how-and-why)
- [<span data-ttu-id="6ea33-415">Power shell: discussie over het implementeren van AssemblyLoadContexts</span><span class="sxs-lookup"><span data-stu-id="6ea33-415">PowerShell: Discussion about implementing AssemblyLoadContexts</span></span>](https://github.com/PowerShell/PowerShell/issues/11571)
- [<span data-ttu-id="6ea33-416">Power shell: `Assembly.LoadFile()` wordt niet in de standaard AssemblyLoadContext geladen</span><span class="sxs-lookup"><span data-stu-id="6ea33-416">PowerShell: `Assembly.LoadFile()` doesn't load into default AssemblyLoadContext</span></span>](https://github.com/PowerShell/PowerShell/issues/12052)
- [<span data-ttu-id="6ea33-417">Rick Strahl: wanneer wordt een .NET-assembly-afhankelijkheid geladen?</span><span class="sxs-lookup"><span data-stu-id="6ea33-417">Rick Strahl: When does a .NET assembly dependency get loaded?</span></span>](https://weblog.west-wind.com/posts/2012/Nov/03/Back-to-Basics-When-does-a-NET-Assembly-Dependency-get-loaded)
- [<span data-ttu-id="6ea33-418">Tjeerd skeet: overzicht van versie beheer in .NET</span><span class="sxs-lookup"><span data-stu-id="6ea33-418">Jon Skeet: Summary of versioning in .NET</span></span>](https://codeblog.jonskeet.uk/2019/06/30/versioning-limitations-in-net/)
- [<span data-ttu-id="6ea33-419">Nate McMaster: dieper in .NET core-primitieven</span><span class="sxs-lookup"><span data-stu-id="6ea33-419">Nate McMaster: Deep dive into .NET Core primitives</span></span>](https://natemcmaster.com/blog/2017/12/21/netcore-primitives/)
