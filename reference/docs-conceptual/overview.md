---
ms.date: 05/22/2020
keywords: powershell,cmdlet
title: Wat is PowerShell?
ms.openlocfilehash: 267b2938a0892c99c3a961bc7107f573df40a683
ms.sourcegitcommit: 38215ad49e237b219e62bb5a5f0eb3b6b048df1e
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 05/27/2020
ms.locfileid: "83868476"
---
# <a name="what-is-powershell"></a><span data-ttu-id="ef213-103">Wat is PowerShell?</span><span class="sxs-lookup"><span data-stu-id="ef213-103">What is PowerShell?</span></span>

<span data-ttu-id="ef213-104">Power shell is een platform voor taak automatisering en configuratie beheer voor meerdere platforms, dat bestaat uit een opdracht regel shell en script taal.</span><span class="sxs-lookup"><span data-stu-id="ef213-104">PowerShell is a cross-platform task automation and configuration management framework, consisting of a command-line shell and scripting language.</span></span> <span data-ttu-id="ef213-105">In tegens telling tot de meeste shells, die tekst accepteren en retour neren, is Power shell gebaseerd op de .NET common language runtime (CLR) en worden .NET-objecten geaccepteerd en geretourneerd.</span><span class="sxs-lookup"><span data-stu-id="ef213-105">Unlike most shells, which accept and return text, PowerShell is built on top of the .NET Common Language Runtime (CLR), and accepts and returns .NET objects.</span></span> <span data-ttu-id="ef213-106">Deze fundamentele wijziging brengt volledig nieuwe hulpprogram ma's en methoden voor automatisering in.</span><span class="sxs-lookup"><span data-stu-id="ef213-106">This fundamental change brings entirely new tools and methods for automation.</span></span>

<!-- removing images until we can get replacements
:::row:::
   :::column span="":::
      Windows
      [![PowerShell on Windows](media/overview/windows-desktop-660.gif)](media/overview/windows-desktop.gif#lightbox)
      [Install on Windows](install/installing-powershell-core-on-windows.md)
   :::column-end:::
   :::column span="":::
      Linux
      [![PowerShell on Linux](media/overview/linux-desktop-660.gif)](media/overview/linux-desktop.gif#lightbox)
      [Install on Linux](install/installing-powershell-core-on-linux.md)
   :::column-end:::
   :::column span="":::
      macOS
      [![PowerShell on macOS](media/overview/macos-desktop-660.gif)](media/overview/macos-desktop.gif#lightbox)
      [Install on macOS](install/installing-powershell-core-on-macos.md)
   :::column-end:::
:::row-end:::
-->

## <a name="output-is-object-based"></a><span data-ttu-id="ef213-107">Uitvoer is op objecten gebaseerd</span><span class="sxs-lookup"><span data-stu-id="ef213-107">Output is object-based</span></span>

<span data-ttu-id="ef213-108">In tegens telling tot traditionele opdracht regel interfaces, zijn Power shell-cmdlets ontworpen om objecten te verwerken.</span><span class="sxs-lookup"><span data-stu-id="ef213-108">Unlike traditional command-line interfaces, PowerShell cmdlets are designed to deal with objects.</span></span>
<span data-ttu-id="ef213-109">Een object is gestructureerde informatie die meer is dan alleen de teken reeks die wordt weer gegeven op het scherm.</span><span class="sxs-lookup"><span data-stu-id="ef213-109">An object is structured information that is more than just the string of characters appearing on the screen.</span></span> <span data-ttu-id="ef213-110">De opdracht uitvoer bevat altijd extra informatie die u kunt gebruiken als u deze nodig hebt.</span><span class="sxs-lookup"><span data-stu-id="ef213-110">Command output always carries extra information that you can use if you need it.</span></span>

<span data-ttu-id="ef213-111">Als u hulpprogram ma's voor tekst verwerking hebt gebruikt voor het verwerken van gegevens in het verleden, zult u merken dat ze anders werken wanneer ze worden gebruikt in Power shell.</span><span class="sxs-lookup"><span data-stu-id="ef213-111">If you've used text-processing tools to process data in the past, you'll find that they behave differently when used in PowerShell.</span></span> <span data-ttu-id="ef213-112">In de meeste gevallen hebt u geen hulp middelen voor tekst verwerking nodig om specifieke gegevens op te halen.</span><span class="sxs-lookup"><span data-stu-id="ef213-112">In most cases, you don't need text-processing tools to extract specific information.</span></span> <span data-ttu-id="ef213-113">U hebt rechtstreeks toegang tot delen van de gegevens met behulp van de standaard syntaxis van Power shell-objecten.</span><span class="sxs-lookup"><span data-stu-id="ef213-113">You directly access portions of the data using standard PowerShell object syntax.</span></span>

## <a name="the-command-family-is-extensible"></a><span data-ttu-id="ef213-114">De opdracht familie is uitbreidbaar</span><span class="sxs-lookup"><span data-stu-id="ef213-114">The command family is extensible</span></span>

<span data-ttu-id="ef213-115">Interfaces zoals `cmd.exe` geen manier om u de ingebouwde opdrachtset direct uit te breiden.</span><span class="sxs-lookup"><span data-stu-id="ef213-115">Interfaces such as `cmd.exe` don't provide a way for you to directly extend the built-in command set.</span></span> <span data-ttu-id="ef213-116">U kunt externe opdracht regel Programma's maken die worden uitgevoerd in `cmd.exe` .</span><span class="sxs-lookup"><span data-stu-id="ef213-116">You can create external command-line tools that run in `cmd.exe`.</span></span> <span data-ttu-id="ef213-117">Deze externe hulpprogram ma's hebben echter geen services, zoals Help-integratie.</span><span class="sxs-lookup"><span data-stu-id="ef213-117">But these external tools don't have services, such as Help integration.</span></span> <span data-ttu-id="ef213-118">`cmd.exe`niet automatisch weet dat deze externe hulpprogram ma's geldige opdrachten zijn.</span><span class="sxs-lookup"><span data-stu-id="ef213-118">`cmd.exe` doesn't automatically know that these external tools are valid commands.</span></span>

<span data-ttu-id="ef213-119">De opdrachten in Power shell worden _cmdlets_genoemd.</span><span class="sxs-lookup"><span data-stu-id="ef213-119">The commands in PowerShell are known as _cmdlets_.</span></span> <span data-ttu-id="ef213-120">U kunt elke cmdlet afzonderlijk gebruiken, maar de kracht ervan wordt gerealiseerd wanneer u deze combineert om complexe taken uit te voeren.</span><span class="sxs-lookup"><span data-stu-id="ef213-120">You can use each cmdlet separately, but their power is realized when you combine them to perform complex tasks.</span></span> <span data-ttu-id="ef213-121">Net als bij veel shells krijgt u toegang tot het bestands systeem op de computer.</span><span class="sxs-lookup"><span data-stu-id="ef213-121">Like many shells, PowerShell gives you access to the file system on the computer.</span></span> <span data-ttu-id="ef213-122">Met Power shell- _providers_ kunt u toegang krijgen tot andere gegevens archieven, zoals het REGI ster en de certificaat archieven, net zo eenvoudig als u toegang hebt tot het bestands systeem.</span><span class="sxs-lookup"><span data-stu-id="ef213-122">PowerShell _providers_ enable you to access other data stores, such as the registry and the certificate stores, as easily as you access the file system.</span></span>

<span data-ttu-id="ef213-123">U kunt uw eigen cmdlet-en functie modules maken met behulp van gecompileerde code of scripts.</span><span class="sxs-lookup"><span data-stu-id="ef213-123">You can create your own cmdlet and function modules using compiled code or scripts.</span></span> <span data-ttu-id="ef213-124">Met modules kunnen cmdlets en providers aan de shell worden toegevoegd.</span><span class="sxs-lookup"><span data-stu-id="ef213-124">Modules can add cmdlets and providers to the shell.</span></span> <span data-ttu-id="ef213-125">Power shell ondersteunt ook scripts die vergelijkbaar zijn met UNIX-shell scripts en `cmd.exe` batch-bestanden.</span><span class="sxs-lookup"><span data-stu-id="ef213-125">PowerShell also supports scripts that are analogous to UNIX shell scripts and `cmd.exe` batch files.</span></span>

## <a name="support-for-command-aliases"></a><span data-ttu-id="ef213-126">Biedt ondersteuning voor opdrachtaliassen</span><span class="sxs-lookup"><span data-stu-id="ef213-126">Support for command aliases</span></span>

<span data-ttu-id="ef213-127">Power shell ondersteunt aliassen om te verwijzen naar opdrachten op alternatieve namen.</span><span class="sxs-lookup"><span data-stu-id="ef213-127">PowerShell supports aliases to refer to commands by alternate names.</span></span> <span data-ttu-id="ef213-128">Met aliasing kunnen gebruikers ervaring hebben met andere shells om algemene opdracht namen te gebruiken die ze al kennen voor vergelijk bare bewerkingen in Power shell.</span><span class="sxs-lookup"><span data-stu-id="ef213-128">Aliasing allows users with experience in other shells to use common command names that they already know for similar operations in PowerShell.</span></span>

<span data-ttu-id="ef213-129">Met aliasing wordt een nieuwe naam gekoppeld aan een andere opdracht.</span><span class="sxs-lookup"><span data-stu-id="ef213-129">Aliasing associates a new name with another command.</span></span> <span data-ttu-id="ef213-130">Power Shell heeft bijvoorbeeld een interne functie `Clear-Host` met de naam waarmee het uitvoer venster wordt gewist.</span><span class="sxs-lookup"><span data-stu-id="ef213-130">For example, PowerShell has an internal function named `Clear-Host` that clears the output window.</span></span> <span data-ttu-id="ef213-131">U kunt ofwel de `cls` alias typen `clear` bij een opdracht prompt.</span><span class="sxs-lookup"><span data-stu-id="ef213-131">You can type either the `cls` or `clear` alias at a command prompt.</span></span> <span data-ttu-id="ef213-132">Power shell interpreteert deze aliassen en voert de `Clear-Host` functie uit.</span><span class="sxs-lookup"><span data-stu-id="ef213-132">PowerShell interprets these aliases and runs the `Clear-Host` function.</span></span>

<span data-ttu-id="ef213-133">Deze functie helpt gebruikers bij het leren van Power shell.</span><span class="sxs-lookup"><span data-stu-id="ef213-133">This feature helps users to learn PowerShell.</span></span> <span data-ttu-id="ef213-134">`cmd.exe`De meeste en UNIX-gebruikers hebben een grote aanbod opdrachten die gebruikers al op naam kennen.</span><span class="sxs-lookup"><span data-stu-id="ef213-134">First, most `cmd.exe` and Unix users have a large repertoire of commands that users already know by name.</span></span> <span data-ttu-id="ef213-135">De Power shell-equivalenten kunnen geen identieke resultaten opleveren.</span><span class="sxs-lookup"><span data-stu-id="ef213-135">The PowerShell equivalents may not produce identical results.</span></span> <span data-ttu-id="ef213-136">De resultaten zijn echter bijna genoeg dat gebruikers kunnen werken zonder de naam van de Power shell-opdracht te weten.</span><span class="sxs-lookup"><span data-stu-id="ef213-136">However, the results are close enough that users can do work without knowing the PowerShell command name.</span></span> <span data-ttu-id="ef213-137">' Spier geheugen ' is een andere belang rijke bron van frustraties bij het leren van een nieuwe opdracht shell.</span><span class="sxs-lookup"><span data-stu-id="ef213-137">"Muscle memory" is another major source of frustration when learning a new command shell.</span></span> <span data-ttu-id="ef213-138">Als u jaren hebt gebruikt `cmd.exe` , kunt u reflexively de `cls` opdracht om het scherm te wissen.</span><span class="sxs-lookup"><span data-stu-id="ef213-138">If you have used `cmd.exe` for years, you might reflexively type the `cls` command to clear the screen.</span></span> <span data-ttu-id="ef213-139">Zonder de alias voor `Clear-Host` ontvangt u een fout bericht en weet u niet wat u kunt doen om de uitvoer te wissen.</span><span class="sxs-lookup"><span data-stu-id="ef213-139">Without the alias for `Clear-Host`, you receive an error message and won't know what to do to clear the output.</span></span>

## <a name="powershell-handles-console-input-and-display"></a><span data-ttu-id="ef213-140">Power shell verwerkt console-invoer en-weer gave</span><span class="sxs-lookup"><span data-stu-id="ef213-140">PowerShell handles console input and display</span></span>

<span data-ttu-id="ef213-141">Wanneer u een opdracht typt, verwerkt Power shell de invoer van de opdracht regel altijd rechtstreeks.</span><span class="sxs-lookup"><span data-stu-id="ef213-141">When you type a command, PowerShell always processes the command-line input directly.</span></span> <span data-ttu-id="ef213-142">Power shell formatteert ook de uitvoer die op het scherm wordt weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="ef213-142">PowerShell also formats the output that you see on the screen.</span></span> <span data-ttu-id="ef213-143">Dit verschil is aanzienlijk omdat het de vereiste werk van elke cmdlet vermindert.</span><span class="sxs-lookup"><span data-stu-id="ef213-143">This difference is significant because it reduces the work required of each cmdlet.</span></span> <span data-ttu-id="ef213-144">Zo zorgt u ervoor dat u altijd op dezelfde manier kunt werken met elke cmdlet.</span><span class="sxs-lookup"><span data-stu-id="ef213-144">It ensures that you can always do things the same way with any cmdlet.</span></span> <span data-ttu-id="ef213-145">Cmdlet-ontwikkel aars hoeven geen code te schrijven voor het parseren van de opdracht regel argumenten of het format teren van de uitvoer.</span><span class="sxs-lookup"><span data-stu-id="ef213-145">Cmdlet developers don't need to write code to parse the command-line arguments or format the output.</span></span>

<span data-ttu-id="ef213-146">Traditionele opdracht regel Programma's hebben hun eigen schema's voor het aanvragen en weer geven van Help.</span><span class="sxs-lookup"><span data-stu-id="ef213-146">Traditional command-line tools have their own schemes for requesting and displaying Help.</span></span> <span data-ttu-id="ef213-147">Sommige opdracht regel Programma's gebruiken `/?` voor het activeren van de Help-weer gave; anderen gebruiken `-?` , `/H` of zelfs `//` .</span><span class="sxs-lookup"><span data-stu-id="ef213-147">Some command-line tools use `/?` to trigger the Help display; others use `-?`, `/H`, or even `//`.</span></span> <span data-ttu-id="ef213-148">De Help wordt in een GUI-venster weer gegeven, in plaats van in de-console weer te geven.</span><span class="sxs-lookup"><span data-stu-id="ef213-148">Some will display Help in a GUI window, rather than in the console display.</span></span> <span data-ttu-id="ef213-149">Als u de verkeerde para meter gebruikt, kan het hulp programma mogelijk negeren wat u hebt getypt en de uitvoering van een taak automatisch starten.</span><span class="sxs-lookup"><span data-stu-id="ef213-149">If you use the wrong parameter, the tool might ignore what you typed and begin executing a task automatically.</span></span>
<span data-ttu-id="ef213-150">Omdat Power shell de opdracht regel automatisch parseert en verwerkt, `-?` betekent de para meter altijd Help voor deze opdracht weer geven.</span><span class="sxs-lookup"><span data-stu-id="ef213-150">Since PowerShell automatically parses and processes the command line, the `-?` parameter always means "show me Help for this command".</span></span>

> [!NOTE]
> <span data-ttu-id="ef213-151">Als u een grafische toepassing uitvoert in Power shell, wordt het venster voor de toepassing geopend.</span><span class="sxs-lookup"><span data-stu-id="ef213-151">If you run a graphic application in PowerShell, the window for the application opens.</span></span>
> <span data-ttu-id="ef213-152">Power shell is alleen van toepassing op het verwerken van de opdracht regel invoer die u opgeeft of de toepassings uitvoer die wordt geretourneerd naar het console venster.</span><span class="sxs-lookup"><span data-stu-id="ef213-152">PowerShell intervenes only when processing the command-line input you supply or the application output returned to the console window.</span></span> <span data-ttu-id="ef213-153">Dit heeft geen invloed op de manier waarop de toepassing intern werkt.</span><span class="sxs-lookup"><span data-stu-id="ef213-153">It does not affect how the application works internally.</span></span>

## <a name="powershell-has-a-pipeline"></a><span data-ttu-id="ef213-154">Power Shell heeft een pijp lijn</span><span class="sxs-lookup"><span data-stu-id="ef213-154">PowerShell has a pipeline</span></span>

<span data-ttu-id="ef213-155">Pijp lijnen zijn weliswaar het meest waardevolle concept dat wordt gebruikt in opdracht regel interfaces.</span><span class="sxs-lookup"><span data-stu-id="ef213-155">Pipelines are arguably the most valuable concept used in command-line interfaces.</span></span> <span data-ttu-id="ef213-156">Wanneer u correct gebruikt, kunnen pijp lijnen de moeite van het gebruik van complexe opdrachten verminderen en is het eenvoudiger om de werk stroom te zien.</span><span class="sxs-lookup"><span data-stu-id="ef213-156">When used properly, pipelines reduce the effort of using complex commands and make it easier to see the flow of work.</span></span> <span data-ttu-id="ef213-157">Elke opdracht in een pijp lijn geeft de uitvoer, item op item, door aan de volgende opdracht.</span><span class="sxs-lookup"><span data-stu-id="ef213-157">Each command in a pipeline passes its output, item by item, to the next command.</span></span> <span data-ttu-id="ef213-158">Opdrachten hoeven niet meer dan één item tegelijk te verwerken.</span><span class="sxs-lookup"><span data-stu-id="ef213-158">Commands don't have to handle more than one item at a time.</span></span> <span data-ttu-id="ef213-159">Het resultaat is een gereduceerd Resource verbruik en de mogelijkheid om de uitvoer direct te verkrijgen.</span><span class="sxs-lookup"><span data-stu-id="ef213-159">The result is reduced resource consumption and the ability to get output immediately.</span></span>

<span data-ttu-id="ef213-160">De notatie die wordt gebruikt voor pijp lijnen, is vergelijkbaar met de notatie die wordt gebruikt in andere schalen.</span><span class="sxs-lookup"><span data-stu-id="ef213-160">The notation used for pipelines is similar to the notation used in other shells.</span></span> <span data-ttu-id="ef213-161">In eerste instantie is het mogelijk niet duidelijk hoe pijp lijnen anders zijn in Power shell.</span><span class="sxs-lookup"><span data-stu-id="ef213-161">At first glance, it may not be apparent how pipelines are different in PowerShell.</span></span> <span data-ttu-id="ef213-162">Hoewel er tekst op het scherm wordt weer gegeven, Power shell pipes-objecten, geen tekst, tussen opdrachten.</span><span class="sxs-lookup"><span data-stu-id="ef213-162">Although you see text on the screen, PowerShell pipes objects, not text, between commands.</span></span>

<span data-ttu-id="ef213-163">Als u bijvoorbeeld de `Out-Host` cmdlet gebruikt om een pagina-op-pagina weer te geven van uitvoer van een andere opdracht, ziet de uitvoer er net zo uit als de normale tekst die op het scherm wordt weer gegeven, onderverdeeld in pagina's:</span><span class="sxs-lookup"><span data-stu-id="ef213-163">For example, if you use the `Out-Host` cmdlet to force a page-by-page display of output from another command, the output looks just like the normal text displayed on the screen, broken up into pages:</span></span>

```powershell
Get-ChildItem | Out-Host -Paging
```

```Output
    Directory: /mnt/c/Git/PS-Docs/PowerShell-Docs/reference/7.0/Microsoft.PowerShell.Core

Mode                 LastWriteTime         Length Name
----                 -------------         ------ ----
d----          05/22/2020    08:30                About
-----          05/20/2020    14:36           9044 Add-History.md
-----          05/20/2020    14:36          12227 Clear-History.md
-----          05/20/2020    14:36           3566 Clear-Host.md
-----          05/20/2020    14:36          29087 Connect-PSSession.md
-----          05/20/2020    14:36           5705 Debug-Job.md
-----          05/20/2020    14:36           3515 Disable-ExperimentalFeature.md
-----          05/20/2020    14:36          25531 Disable-PSRemoting.md
-----          05/20/2020    14:36           7852 Disable-PSSessionConfiguration.md
-----          05/20/2020    14:36          25355 Disconnect-PSSession.md
-----          05/20/2020    14:36           3491 Enable-ExperimentalFeature.md
-----          05/20/2020    14:36          13310 Enable-PSRemoting.md
-----          05/20/2020    14:36           8401 Enable-PSSessionConfiguration.md
-----          05/20/2020    14:36           9531 Enter-PSHostProcess.md
...
<SPACE> next page; <CR> next line; Q quit
```

<span data-ttu-id="ef213-164">Paginering vermindert ook het CPU-gebruik omdat er `Out-Host` een volledige pagina kan worden weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="ef213-164">Paging also reduces CPU utilization because processing transfers to the `Out-Host` cmdlet when it has a complete page ready to display.</span></span> <span data-ttu-id="ef213-165">De cmdlets die voorafgaan aan de pijp lijn worden uitgevoerd, totdat de volgende pagina van uitvoer beschikbaar is.</span><span class="sxs-lookup"><span data-stu-id="ef213-165">The cmdlets that precede it in the pipeline pause execution until the next page of output is available.</span></span>

### <a name="objects-in-the-pipeline"></a><span data-ttu-id="ef213-166">Objecten in de pijp lijn</span><span class="sxs-lookup"><span data-stu-id="ef213-166">Objects in the pipeline</span></span>

<span data-ttu-id="ef213-167">Wanneer u een cmdlet in Power shell uitvoert, wordt tekst uitvoer weer gegeven, omdat het nodig is om objecten als tekst in een console venster aan te duiden.</span><span class="sxs-lookup"><span data-stu-id="ef213-167">When you run a cmdlet in PowerShell, you see text output because it is necessary to represent objects as text in a console window.</span></span> <span data-ttu-id="ef213-168">In de tekst uitvoer worden mogelijk niet alle eigenschappen weer gegeven van het object dat wordt uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="ef213-168">The text output may not display all of the properties of the object being output.</span></span>

<span data-ttu-id="ef213-169">Denk bijvoorbeeld aan de `Get-Location` cmdlet.</span><span class="sxs-lookup"><span data-stu-id="ef213-169">For example, consider the `Get-Location` cmdlet.</span></span> <span data-ttu-id="ef213-170">De tekst uitvoer is een samen vatting van informatie, niet een volledige weer gave van het object dat wordt geretourneerd door `Get-Location` .</span><span class="sxs-lookup"><span data-stu-id="ef213-170">The text output is a summary of information, not a complete representation of the object returned by `Get-Location`.</span></span> <span data-ttu-id="ef213-171">De kop in de uitvoer wordt toegevoegd door het proces waarmee de gegevens voor het scherm worden opgemaakt.</span><span class="sxs-lookup"><span data-stu-id="ef213-171">The heading in the output is added by the process that formats the data for onscreen display.</span></span>

```powershell
Get-Location
```

```Output
Path
----
C:\
```

<span data-ttu-id="ef213-172">Sluizen de uitvoer naar de `Get-Member` cmdlet geeft informatie weer over het object dat wordt geretourneerd door `Get-Location` .</span><span class="sxs-lookup"><span data-stu-id="ef213-172">Piping the output to the `Get-Member` cmdlet displays information about the object returned by `Get-Location`.</span></span>

```powershell
Get-Location | Get-Member
```

```Output
   TypeName: System.Management.Automation.PathInfo

Name         MemberType Definition
----         ---------- ----------
Equals       Method     bool Equals(System.Object obj)
GetHashCode  Method     int GetHashCode()
GetType      Method     type GetType()
ToString     Method     string ToString()
Drive        Property   System.Management.Automation.PSDriveInfo Drive {get;}
Path         Property   string Path {get;}
Provider     Property   System.Management.Automation.ProviderInfo Provider {get;}
ProviderPath Property   string ProviderPath {get;}
```

<span data-ttu-id="ef213-173">`Get-Location`retourneert een **PathInfo** -object dat het huidige pad en andere informatie bevat.</span><span class="sxs-lookup"><span data-stu-id="ef213-173">`Get-Location` returns a **PathInfo** object that contains the current path and other information.</span></span>

## <a name="built-in-help-system"></a><span data-ttu-id="ef213-174">Ingebouwd Help-systeem</span><span class="sxs-lookup"><span data-stu-id="ef213-174">Built-in help system</span></span>

<span data-ttu-id="ef213-175">Net als Unix `man` -pagina's bevat Power shell gedetailleerde Help-artikelen waarin Power shell-concepten en opdracht syntaxis worden uitgelegd.</span><span class="sxs-lookup"><span data-stu-id="ef213-175">Similar to Unix `man` pages, PowerShell includes detailed help articles that explain PowerShell concepts and command syntax.</span></span> <span data-ttu-id="ef213-176">Gebruik de cmdlet [Get-Help][] om deze artikelen weer te geven bij de opdracht prompt of Bekijk de meest recent bijgewerkte versies van deze artikelen in de Power shell-documentatie online.</span><span class="sxs-lookup"><span data-stu-id="ef213-176">Use the [Get-Help][] cmdlet to display these articles at the command prompt or view the most recently updated versions of these articles in the PowerShell documentation online.</span></span>

## <a name="next-steps"></a><span data-ttu-id="ef213-177">Volgende stappen</span><span class="sxs-lookup"><span data-stu-id="ef213-177">Next steps</span></span>

<span data-ttu-id="ef213-178">Zie de sectie **Power shell** van deze site voor meer informatie over Power shell.</span><span class="sxs-lookup"><span data-stu-id="ef213-178">To learn more about PowerShell, see the **Learning PowerShell** section of this site.</span></span>

<!-- link references -->

[Get-Help]: /powershell/module/microsoft.powershell.core/Get-Help
