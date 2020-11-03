---
description: Hierin wordt beschreven hoe Power shell bepaalt welke opdracht moet worden uitgevoerd.
keywords: powershell,cmdlet
ms.date: 02/13/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_command_precedence?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Command_Precedence
ms.openlocfilehash: 0fc514f8e7e7894ae9da281867fd3d2fe61b89b6
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/13/2020
ms.locfileid: "93252961"
---
# <a name="about-command-precedence"></a><span data-ttu-id="618e8-104">Over opdracht prioriteit</span><span class="sxs-lookup"><span data-stu-id="618e8-104">About Command Precedence</span></span>

## <a name="short-description"></a><span data-ttu-id="618e8-105">Korte beschrijving</span><span class="sxs-lookup"><span data-stu-id="618e8-105">Short description</span></span>
<span data-ttu-id="618e8-106">Hierin wordt beschreven hoe Power shell bepaalt welke opdracht moet worden uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="618e8-106">Describes how PowerShell determines which command to run.</span></span>

## <a name="long-description"></a><span data-ttu-id="618e8-107">Lange beschrijving</span><span class="sxs-lookup"><span data-stu-id="618e8-107">Long description</span></span>

<span data-ttu-id="618e8-108">Opdracht prioriteit beschrijft hoe Power shell bepaalt welke opdracht moet worden uitgevoerd wanneer een sessie meer dan één opdracht met dezelfde naam bevat.</span><span class="sxs-lookup"><span data-stu-id="618e8-108">Command precedence describes how PowerShell determines which command to run when a session contains more than one command with the same name.</span></span> <span data-ttu-id="618e8-109">Opdrachten in een sessie kunnen worden verborgen of vervangen door opdrachten met dezelfde naam.</span><span class="sxs-lookup"><span data-stu-id="618e8-109">Commands within a session can be hidden or replaced by commands with the same name.</span></span> <span data-ttu-id="618e8-110">In dit artikel leest u hoe u verborgen opdrachten uitvoert en conflicten met opdracht namen voor komt.</span><span class="sxs-lookup"><span data-stu-id="618e8-110">This article shows you how to run hidden commands and how to avoid command-name conflicts.</span></span>

## <a name="command-precedence"></a><span data-ttu-id="618e8-111">Opdracht prioriteit</span><span class="sxs-lookup"><span data-stu-id="618e8-111">Command precedence</span></span>

<span data-ttu-id="618e8-112">Wanneer een Power shell-sessie meer dan één opdracht met dezelfde naam bevat, bepaalt Power shell welke opdracht moet worden uitgevoerd met behulp van de volgende regels.</span><span class="sxs-lookup"><span data-stu-id="618e8-112">When a PowerShell session includes more than one command that has the same name, PowerShell determines which command to run by using the following rules.</span></span>

<span data-ttu-id="618e8-113">Als u het pad naar een opdracht opgeeft, voert Power shell de opdracht uit op de locatie die is opgegeven door het pad.</span><span class="sxs-lookup"><span data-stu-id="618e8-113">If you specify the path to a command, PowerShell runs the command at the location specified by the path.</span></span>

<span data-ttu-id="618e8-114">Met de volgende opdracht wordt bijvoorbeeld het FindDocs.ps1 script uitgevoerd in de map ' C: \\ TechDocs ':</span><span class="sxs-lookup"><span data-stu-id="618e8-114">For example, the following command runs the FindDocs.ps1 script in the "C:\\TechDocs" directory:</span></span>

```
C:\TechDocs\FindDocs.ps1
```

<span data-ttu-id="618e8-115">Als beveiligings functie voert Power shell geen uitvoer bare (systeem eigen) opdrachten uit, inclusief Power shell-scripts, tenzij de opdracht zich bevindt in een pad dat wordt vermeld in de omgevings variabele PATH `$env:path` of tenzij u het pad naar het script bestand opgeeft.</span><span class="sxs-lookup"><span data-stu-id="618e8-115">As a security feature, PowerShell does not run executable (native) commands, including PowerShell scripts, unless the command is located in a path that is listed in the Path environment variable `$env:path` or unless you specify the path to the script file.</span></span>

<span data-ttu-id="618e8-116">Als u een script wilt uitvoeren dat zich in de huidige map bevindt, geeft u het volledige pad op of typt u een punt `.\` om de huidige map weer te geven.</span><span class="sxs-lookup"><span data-stu-id="618e8-116">To run a script that is in the current directory, specify the full path, or type a dot `.\` to represent the current directory.</span></span>

<span data-ttu-id="618e8-117">Als u bijvoorbeeld het FindDocs.ps1-bestand in de huidige map wilt uitvoeren, typt u:</span><span class="sxs-lookup"><span data-stu-id="618e8-117">For example, to run the FindDocs.ps1 file in the current directory, type:</span></span>

```
.\FindDocs.ps1
```

### <a name="using-wildcards-in-execution"></a><span data-ttu-id="618e8-118">Joker tekens gebruiken in uitvoering</span><span class="sxs-lookup"><span data-stu-id="618e8-118">Using wildcards in execution</span></span>

<span data-ttu-id="618e8-119">U kunt joker tekens gebruiken bij het uitvoeren van de opdracht.</span><span class="sxs-lookup"><span data-stu-id="618e8-119">You may use wildcards in command execution.</span></span> <span data-ttu-id="618e8-120">Het gebruik van joker tekens wordt ook wel *globbing* genoemd.</span><span class="sxs-lookup"><span data-stu-id="618e8-120">Using wildcard characters is also known as *globbing*.</span></span>

<span data-ttu-id="618e8-121">Power Shell voert een bestand uit met een Joker teken, voordat een letterlijke overeenkomst wordt gevonden.</span><span class="sxs-lookup"><span data-stu-id="618e8-121">PowerShell executes a file that has a wildcard match, before a literal match.</span></span>

<span data-ttu-id="618e8-122">Denk bijvoorbeeld aan een map met de volgende bestanden:</span><span class="sxs-lookup"><span data-stu-id="618e8-122">For example, consider a directory with the following files:</span></span>

```
Get-ChildItem C:\temp\test


    Directory: C:\temp\test


Mode                LastWriteTime         Length Name
----                -------------         ------ ----
-a----        5/20/2019   2:29 PM             28 a.ps1
-a----        5/20/2019   2:29 PM             28 [a1].ps1
```

<span data-ttu-id="618e8-123">Beide script bestanden hebben dezelfde inhoud: `$MyInvocation.MyCommand.Path` .</span><span class="sxs-lookup"><span data-stu-id="618e8-123">Both script files have the same content: `$MyInvocation.MyCommand.Path`.</span></span>
<span data-ttu-id="618e8-124">Met deze opdracht wordt de naam van het script weer gegeven dat wordt aangeroepen.</span><span class="sxs-lookup"><span data-stu-id="618e8-124">This command displays the name of the script that is invoked.</span></span>

<span data-ttu-id="618e8-125">Wanneer u uitvoert `[a1].ps1` , wordt het bestand `a.ps1` uitgevoerd, zelfs als het bestand `[a1].ps1` een letterlijke overeenkomst is.</span><span class="sxs-lookup"><span data-stu-id="618e8-125">When you run `[a1].ps1`, the file `a.ps1` is executed even though the file `[a1].ps1` is a literal match.</span></span>

```powershell
C:\temp\test\[a1].ps1
```

```Output
C:\temp\test\a.ps1
```

<span data-ttu-id="618e8-126">We gaan nu het `a.ps1` bestand verwijderen en proberen het opnieuw uit te voeren.</span><span class="sxs-lookup"><span data-stu-id="618e8-126">Now let's delete the `a.ps1` file and attempt to run it again.</span></span>

```powershell
Remove-Item C:\temp\test\a.ps1
C:\temp\test\[a1].ps1
```

```Output
C:\temp\test\[a1].ps1
```

<span data-ttu-id="618e8-127">U kunt in de uitvoer zien dat `[a1].ps1` deze keer wordt uitgevoerd omdat de letterlijke overeenkomst het enige bestand is dat overeenkomt met het Joker teken.</span><span class="sxs-lookup"><span data-stu-id="618e8-127">You can see from the output that `[a1].ps1` runs this time because the literal match is the only file match for that wildcard pattern.</span></span>

<span data-ttu-id="618e8-128">Zie [about_Wildcards](about_Wildcards.md)voor meer informatie over het gebruik van joker tekens in Power shell.</span><span class="sxs-lookup"><span data-stu-id="618e8-128">For more information about how PowerShell uses wildcards, see [about_Wildcards](about_Wildcards.md).</span></span>

> [!NOTE]
> <span data-ttu-id="618e8-129">Als u de zoek opdracht wilt beperken tot een relatief pad, moet u een voor voegsel van de script naam met het `.\` pad opgeven.</span><span class="sxs-lookup"><span data-stu-id="618e8-129">To limit the search to a relative path, you must prefix the script name with the `.\` path.</span></span> <span data-ttu-id="618e8-130">Hiermee beperkt u de Zoek opdrachten naar bestanden in het relatieve pad.</span><span class="sxs-lookup"><span data-stu-id="618e8-130">This limits the search for commands to files in that relative path.</span></span> <span data-ttu-id="618e8-131">Zonder dit voor voegsel kan de andere Power shell-syntaxis conflicteren en zijn er weinig garanties dat het bestand wordt gevonden.</span><span class="sxs-lookup"><span data-stu-id="618e8-131">Without this prefix, other PowerShell syntax may conflict and there are few guarantees that the file will be found.</span></span>

<span data-ttu-id="618e8-132">Als u geen pad opgeeft, maakt Power shell gebruik van de volgende volg orde van prioriteit wanneer opdrachten worden uitgevoerd voor alle items die in de huidige sessie worden geladen:</span><span class="sxs-lookup"><span data-stu-id="618e8-132">If you do not specify a path, PowerShell uses the following precedence order when it runs commands for all items loaded in the current session:</span></span>

  1. <span data-ttu-id="618e8-133">Alias</span><span class="sxs-lookup"><span data-stu-id="618e8-133">Alias</span></span>
  2. <span data-ttu-id="618e8-134">Functie</span><span class="sxs-lookup"><span data-stu-id="618e8-134">Function</span></span>
  3. <span data-ttu-id="618e8-135">Cmdlet</span><span class="sxs-lookup"><span data-stu-id="618e8-135">Cmdlet</span></span>
  4. <span data-ttu-id="618e8-136">Externe uitvoer bare bestanden (Program ma's en niet-Power shell-scripts)</span><span class="sxs-lookup"><span data-stu-id="618e8-136">External executable files (programs and non-PowerShell scripts)</span></span>

<span data-ttu-id="618e8-137">Als u ' Help ' typt, zoekt Power shell eerst naar een alias met de naam `help` , vervolgens een functie `Help` met de naam en ten slotte een cmdlet met de naam `Help` .</span><span class="sxs-lookup"><span data-stu-id="618e8-137">Therefore, if you type "help", PowerShell first looks for an alias named `help`, then a function named `Help`, and finally a cmdlet named `Help`.</span></span> <span data-ttu-id="618e8-138">Het eerste item dat wordt gevonden, wordt uitgevoerd `help` .</span><span class="sxs-lookup"><span data-stu-id="618e8-138">It runs the first `help` item that it finds.</span></span>

<span data-ttu-id="618e8-139">Als uw sessie bijvoorbeeld een cmdlet bevat en een functie met `Get-Map` de naam, wanneer u typt `Get-Map` , voert Power shell de functie uit.</span><span class="sxs-lookup"><span data-stu-id="618e8-139">For example, if your session contains a cmdlet and a function, both named `Get-Map`, when you type `Get-Map`, PowerShell runs the function.</span></span>

> [!NOTE]
> <span data-ttu-id="618e8-140">Dit is alleen van toepassing op geladen opdrachten.</span><span class="sxs-lookup"><span data-stu-id="618e8-140">This only applies to loaded commands.</span></span> <span data-ttu-id="618e8-141">Als er een `build` uitvoerbaar bestand en een alias `build` voor een functie met de naam van `Invoke-Build` binnen een module die niet in de huidige sessie is geladen, voert Power shell het `build` uitvoer bare bestand uit.</span><span class="sxs-lookup"><span data-stu-id="618e8-141">If there is a `build` executable and an Alias `build` for a function with the name of `Invoke-Build` inside a module that is not loaded into the current session, PowerShell runs the `build` executable instead.</span></span> <span data-ttu-id="618e8-142">Modules worden niet automatisch geladen als het externe uitvoer bare bestand in dit geval wordt gevonden.</span><span class="sxs-lookup"><span data-stu-id="618e8-142">It does not auto-load modules if it finds the external executable in this case.</span></span> <span data-ttu-id="618e8-143">Het is alleen wanneer er geen extern uitvoerbaar bestand wordt gevonden dat een alias, functie of cmdlet met de opgegeven naam wordt aangeroepen, waardoor automatisch laden van de module wordt geactiveerd.</span><span class="sxs-lookup"><span data-stu-id="618e8-143">It is only when no external executable is found that an alias, function, or cmdlet with the given name is invoked, thereby triggering auto-loading of its module.</span></span>

<span data-ttu-id="618e8-144">Wanneer de sessie items van hetzelfde type bevat die dezelfde naam hebben, voert Power shell het nieuwere item uit.</span><span class="sxs-lookup"><span data-stu-id="618e8-144">When the session contains items of the same type that have the same name, PowerShell runs the newer item.</span></span>

<span data-ttu-id="618e8-145">Als u bijvoorbeeld een andere `Get-Date` cmdlet uit een module importeert terwijl u typt `Get-Date` , voert Power shell de geïmporteerde versie uit via de systeem eigen.</span><span class="sxs-lookup"><span data-stu-id="618e8-145">For example, if you import another `Get-Date` cmdlet from a module, when you type `Get-Date`, PowerShell runs the imported version over the native one.</span></span>

## <a name="hidden-and-replaced-items"></a><span data-ttu-id="618e8-146">Verborgen en vervangen items</span><span class="sxs-lookup"><span data-stu-id="618e8-146">Hidden and replaced items</span></span>

<span data-ttu-id="618e8-147">Als gevolg van deze regels kunnen items worden vervangen of verborgen door items met dezelfde naam.</span><span class="sxs-lookup"><span data-stu-id="618e8-147">As a result of these rules, items can be replaced or hidden by items with the same name.</span></span>

<span data-ttu-id="618e8-148">Items zijn "verborgen" of "schaduw" als u nog steeds toegang hebt tot het oorspronkelijke item, bijvoorbeeld door de naam van het item te kwalificeren met een module of module naam.</span><span class="sxs-lookup"><span data-stu-id="618e8-148">Items are "hidden" or "shadowed" if you can still access the original item, such as by qualifying the item name with a module or snap-in name.</span></span>

<span data-ttu-id="618e8-149">Als u bijvoorbeeld een functie importeert die dezelfde naam heeft als een cmdlet in de sessie, wordt de cmdlet verborgen (maar niet vervangen) omdat deze is geïmporteerd uit een module of module.</span><span class="sxs-lookup"><span data-stu-id="618e8-149">For example, if you import a function that has the same name as a cmdlet in the session, the cmdlet is hidden (but not replaced) because it was imported from a snap-in or module.</span></span>

<span data-ttu-id="618e8-150">Items zijn "vervangen" of "overschreven" als u het oorspronkelijke item niet meer kunt openen.</span><span class="sxs-lookup"><span data-stu-id="618e8-150">Items are "replaced" or "overwritten" if you can no longer access the original item.</span></span>

<span data-ttu-id="618e8-151">Als u bijvoorbeeld een variabele importeert die dezelfde naam heeft als een variabele in de sessie, wordt de oorspronkelijke variabele vervangen en is deze niet meer toegankelijk.</span><span class="sxs-lookup"><span data-stu-id="618e8-151">For example, if you import a variable that has the same name as a variable in the session, the original variable is replaced and is no longer accessible.</span></span>
<span data-ttu-id="618e8-152">U kunt een variabele met een module naam niet kwalificeren.</span><span class="sxs-lookup"><span data-stu-id="618e8-152">You cannot qualify a variable with a module name.</span></span>

<span data-ttu-id="618e8-153">Als u een functie typt op de opdracht regel en vervolgens een functie importeert die dezelfde naam heeft, wordt de oorspronkelijke functie vervangen en is deze niet meer toegankelijk.</span><span class="sxs-lookup"><span data-stu-id="618e8-153">Also, if you type a function at the command line and then import a function with the same name, the original function is replaced and is no longer accessible.</span></span>

### <a name="finding-hidden-commands"></a><span data-ttu-id="618e8-154">Verborgen opdrachten zoeken</span><span class="sxs-lookup"><span data-stu-id="618e8-154">Finding hidden commands</span></span>

<span data-ttu-id="618e8-155">Met de para meter **all** van de cmdlet [Get-opdracht](xref:Microsoft.PowerShell.Core.Get-Command) worden alle opdrachten met de opgegeven naam opgehaald, zelfs als ze worden verborgen of vervangen.</span><span class="sxs-lookup"><span data-stu-id="618e8-155">The **All** parameter of the [Get-Command](xref:Microsoft.PowerShell.Core.Get-Command) cmdlet gets all commands with the specified name, even if they are hidden or replaced.</span></span> <span data-ttu-id="618e8-156">Vanaf Power Shell 3,0 worden standaard `Get-Command` alleen de opdrachten opgehaald die worden uitgevoerd wanneer u de naam van de opdracht typt.</span><span class="sxs-lookup"><span data-stu-id="618e8-156">Beginning in PowerShell 3.0, by default, `Get-Command` gets only the commands that run when you type the command name.</span></span>

<span data-ttu-id="618e8-157">In de volgende voor beelden bevat de sessie een `Get-Date` functie en een [Get-date-](xref:Microsoft.PowerShell.Utility.Get-Date) cmdlet.</span><span class="sxs-lookup"><span data-stu-id="618e8-157">In the following examples, the session includes a `Get-Date` function and a [Get-Date](xref:Microsoft.PowerShell.Utility.Get-Date) cmdlet.</span></span>

<span data-ttu-id="618e8-158">De volgende opdracht wordt de `Get-Date` opdracht die wordt uitgevoerd wanneer u typt `Get-Date` .</span><span class="sxs-lookup"><span data-stu-id="618e8-158">The following command gets the `Get-Date` command that runs when you type `Get-Date`.</span></span>

```powershell
Get-Command Get-Date
```

```output
CommandType     Name                      ModuleName
-----------     ----                      ----------
Function        Get-Date
```

<span data-ttu-id="618e8-159">De volgende opdracht gebruikt de **alle** para meters om alle opdrachten op te halen `Get-Date` .</span><span class="sxs-lookup"><span data-stu-id="618e8-159">The following command uses the **All** parameter to get all `Get-Date` commands.</span></span>

```powershell
Get-Command Get-Date -All
```

```output
CommandType     Name                      ModuleName
-----------     ----                      ----------
Function        Get-Date
Cmdlet          Get-Date                  Microsoft.PowerShell.Utility
```

### <a name="running-hidden-commands"></a><span data-ttu-id="618e8-160">Verborgen opdrachten uitvoeren</span><span class="sxs-lookup"><span data-stu-id="618e8-160">Running hidden commands</span></span>

<span data-ttu-id="618e8-161">U kunt bepaalde opdrachten uitvoeren door item eigenschappen op te geven die de opdracht onderscheiden van andere opdrachten die dezelfde naam kunnen hebben.</span><span class="sxs-lookup"><span data-stu-id="618e8-161">You can run particular commands by specifying item properties that distinguish the command from other commands that might have the same name.</span></span> <span data-ttu-id="618e8-162">U kunt deze methode gebruiken om elke opdracht uit te voeren, maar dit is vooral handig voor het uitvoeren van verborgen opdrachten.</span><span class="sxs-lookup"><span data-stu-id="618e8-162">You can use this method to run any command, but it is especially useful for running hidden commands.</span></span>

#### <a name="qualified-names"></a><span data-ttu-id="618e8-163">Gekwalificeerde namen</span><span class="sxs-lookup"><span data-stu-id="618e8-163">Qualified names</span></span>

<span data-ttu-id="618e8-164">Met de module-gekwalificeerde naam van een cmdlet kunt u opdrachten uitvoeren die zijn verborgen door een item met dezelfde naam.</span><span class="sxs-lookup"><span data-stu-id="618e8-164">Using the module-qualified name of a cmdlet allows you to run commands hidden by an item with the same name.</span></span> <span data-ttu-id="618e8-165">U kunt de cmdlet bijvoorbeeld uitvoeren `Get-Date` door deze te kwalificeren met de module naam **micro soft. Power shell. Utility**.</span><span class="sxs-lookup"><span data-stu-id="618e8-165">For example, you can run the `Get-Date` cmdlet by qualifying it with its module name **Microsoft.PowerShell.Utility**.</span></span>

<span data-ttu-id="618e8-166">Gebruik deze voorkeurs methode voor het schrijven van scripts die u wilt distribueren.</span><span class="sxs-lookup"><span data-stu-id="618e8-166">Use this preferred method when writing scripts that you intend to distribute.</span></span> <span data-ttu-id="618e8-167">U kunt niet voors pellen welke opdrachten mogelijk aanwezig zijn in de sessie waarin het script wordt uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="618e8-167">You cannot predict which commands might be present in the session in which the script runs.</span></span>

```powershell
New-Alias -Name "Get-Date" -Value "Get-ChildItem"
Microsoft.PowerShell.Utility\Get-Date
```

```output
Tuesday, September 4, 2018 8:17:25 AM
```

<span data-ttu-id="618e8-168">Als u een `New-Map` opdracht wilt uitvoeren die is toegevoegd door de `MapFunctions` module, gebruikt u de module-gekwalificeerde naam:</span><span class="sxs-lookup"><span data-stu-id="618e8-168">To run a `New-Map` command that was added by the `MapFunctions` module, use its module-qualified name:</span></span>

```powershell
MapFunctions\New-Map
```

<span data-ttu-id="618e8-169">Gebruik de eigenschap PropertyName van opdrachten om **de module te** vinden van waaruit een opdracht is geïmporteerd.</span><span class="sxs-lookup"><span data-stu-id="618e8-169">To find the module from which a command was imported, use the **ModuleName** property of commands.</span></span>

```
(Get-Command <command-name>).ModuleName
```

<span data-ttu-id="618e8-170">Als u bijvoorbeeld de bron van de cmdlet wilt zoeken `Get-Date` , typt u:</span><span class="sxs-lookup"><span data-stu-id="618e8-170">For example, to find the source of the `Get-Date` cmdlet, type:</span></span>

```powershell
(Get-Command Get-Date).ModuleName
```

```output
Microsoft.PowerShell.Utility
```

> [!NOTE]
> <span data-ttu-id="618e8-171">U kunt geen variabelen of aliassen kwalificeren.</span><span class="sxs-lookup"><span data-stu-id="618e8-171">You cannot qualify variables or aliases.</span></span>

#### <a name="call-operator"></a><span data-ttu-id="618e8-172">Aanroep operator</span><span class="sxs-lookup"><span data-stu-id="618e8-172">Call operator</span></span>

<span data-ttu-id="618e8-173">U kunt ook de `Call` operator gebruiken `&` om verborgen opdrachten uit te voeren door deze te combi neren met een aanroep naar [Get-Child item](xref:Microsoft.PowerShell.Management.Get-ChildItem) (de alias is ' dir ') `Get-Command` of [Get-module](xref:Microsoft.PowerShell.Core.Get-Module).</span><span class="sxs-lookup"><span data-stu-id="618e8-173">You can also use the `Call` operator `&` to run hidden commands by combining it with a call to [Get-ChildItem](xref:Microsoft.PowerShell.Management.Get-ChildItem) (the alias is "dir"), `Get-Command` or [Get-Module](xref:Microsoft.PowerShell.Core.Get-Module).</span></span>

<span data-ttu-id="618e8-174">De aanroep operator voert teken reeksen en script blokken uit in een onderliggend bereik.</span><span class="sxs-lookup"><span data-stu-id="618e8-174">The call operator executes strings and script blocks in a child scope.</span></span> <span data-ttu-id="618e8-175">Zie [about_Operators](about_Operators.md)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="618e8-175">For more information, see [about_Operators](about_Operators.md).</span></span>

<span data-ttu-id="618e8-176">Als u bijvoorbeeld een functie hebt `Map` met de naam die is verborgen met een alias met `Map` de naam, gebruikt u de volgende opdracht om de functie uit te voeren.</span><span class="sxs-lookup"><span data-stu-id="618e8-176">For example, if you have a function named `Map` that is hidden by an alias named `Map`, use the following command to run the function.</span></span>

```powershell
&(Get-Command -Name Map -CommandType Function)
```

<span data-ttu-id="618e8-177">of</span><span class="sxs-lookup"><span data-stu-id="618e8-177">or</span></span>

```powershell
&(dir Function:\map)
```

<span data-ttu-id="618e8-178">U kunt ook uw verborgen opdracht opslaan in een variabele, zodat u deze eenvoudiger kunt uitvoeren.</span><span class="sxs-lookup"><span data-stu-id="618e8-178">You can also save your hidden command in a variable to make it easier to run.</span></span>

<span data-ttu-id="618e8-179">Met de volgende opdracht wordt bijvoorbeeld de `Map` functie in de `$myMap` variabele opgeslagen en vervolgens de `Call` operator gebruikt om deze uit te voeren.</span><span class="sxs-lookup"><span data-stu-id="618e8-179">For example, the following command saves the `Map` function in the `$myMap` variable and then uses the `Call` operator to run it.</span></span>

```powershell
$myMap = (Get-Command -Name map -CommandType function)
&($myMap)
```

### <a name="replaced-items"></a><span data-ttu-id="618e8-180">Vervangen items</span><span class="sxs-lookup"><span data-stu-id="618e8-180">Replaced items</span></span>

<span data-ttu-id="618e8-181">Er is een vervangend item die u niet meer kunt openen.</span><span class="sxs-lookup"><span data-stu-id="618e8-181">A "replaced" item is one that you can no longer access.</span></span> <span data-ttu-id="618e8-182">U kunt items vervangen door items met dezelfde naam te importeren uit een module of module.</span><span class="sxs-lookup"><span data-stu-id="618e8-182">You can replace items by importing items of the same name from a module or snap-in.</span></span>

<span data-ttu-id="618e8-183">Als u bijvoorbeeld een `Get-Map` functie in uw sessie typt en u een functie importeert `Get-Map` , wordt de oorspronkelijke functie vervangen.</span><span class="sxs-lookup"><span data-stu-id="618e8-183">For example, if you type a `Get-Map` function in your session, and you import a function called `Get-Map`, it replaces the original function.</span></span> <span data-ttu-id="618e8-184">U kunt deze niet ophalen in de huidige sessie.</span><span class="sxs-lookup"><span data-stu-id="618e8-184">You cannot retrieve it in the current session.</span></span>

<span data-ttu-id="618e8-185">Variabelen en aliassen kunnen niet worden verborgen omdat u geen aanroep operator of gekwalificeerde naam kunt gebruiken om ze uit te voeren.</span><span class="sxs-lookup"><span data-stu-id="618e8-185">Variables and aliases cannot be hidden because you cannot use a call operator or a qualified name to run them.</span></span> <span data-ttu-id="618e8-186">Wanneer u variabelen en aliassen uit een module of module importeert, vervangen deze variabelen in de sessie met dezelfde naam.</span><span class="sxs-lookup"><span data-stu-id="618e8-186">When you import variables and aliases from a module or snap-in, they replace variables in the session with the same name.</span></span>

### <a name="avoiding-name-conflicts"></a><span data-ttu-id="618e8-187">Naam conflicten vermijden</span><span class="sxs-lookup"><span data-stu-id="618e8-187">Avoiding name conflicts</span></span>

<span data-ttu-id="618e8-188">De beste manier om conflicten met opdracht namen te beheren is om te voor komen dat.</span><span class="sxs-lookup"><span data-stu-id="618e8-188">The best way to manage command name conflicts is to prevent them.</span></span> <span data-ttu-id="618e8-189">Gebruik een unieke naam wanneer u uw opdrachten een naam geef.</span><span class="sxs-lookup"><span data-stu-id="618e8-189">When you name your commands, use a unique name.</span></span> <span data-ttu-id="618e8-190">U kunt bijvoorbeeld uw initialen of bedrijfs naam acroniem toevoegen aan de uitvoeringen in de opdrachten.</span><span class="sxs-lookup"><span data-stu-id="618e8-190">For example, add your initials or company name acronym to the nouns in your commands.</span></span>

<span data-ttu-id="618e8-191">Wanneer u vanuit een Power shell-module of vanuit een andere sessie opdrachten in uw sessie importeert, gebruikt u ook de `Prefix` para meter van de [import-module](xref:Microsoft.PowerShell.Core.Import-Module) of</span><span class="sxs-lookup"><span data-stu-id="618e8-191">Also, when you import commands into your session from a PowerShell module or from another session, use the `Prefix` parameter of the [Import-Module](xref:Microsoft.PowerShell.Core.Import-Module) or</span></span>

<span data-ttu-id="618e8-192">De cmdlet [import-PSSession](xref:Microsoft.PowerShell.Utility.Import-PSSession) om een voor voegsel toe te voegen aan de naam woorden in de namen van opdrachten.</span><span class="sxs-lookup"><span data-stu-id="618e8-192">[Import-PSSession](xref:Microsoft.PowerShell.Utility.Import-PSSession) cmdlet to add a prefix to the nouns in the names of commands.</span></span>

<span data-ttu-id="618e8-193">Met de volgende opdracht wordt bijvoorbeeld een conflict voor komen met de `Get-Date` `Set-Date` cmdlets en die bij Power shell worden geleverd bij het importeren van de `DateFunctions` module.</span><span class="sxs-lookup"><span data-stu-id="618e8-193">For example, the following command avoids any conflict with the `Get-Date` and `Set-Date` cmdlets that come with PowerShell when you import the `DateFunctions` module.</span></span>

```powershell
Import-Module -Name DateFunctions -Prefix ZZ
```

<span data-ttu-id="618e8-194">Zie en hieronder voor meer `Import-Module` informatie `Import-PSSession` .</span><span class="sxs-lookup"><span data-stu-id="618e8-194">For more information, see `Import-Module` and `Import-PSSession` below.</span></span>

## <a name="see-also"></a><span data-ttu-id="618e8-195">Zie ook</span><span class="sxs-lookup"><span data-stu-id="618e8-195">See also</span></span>

- [<span data-ttu-id="618e8-196">about_Path_Syntax</span><span class="sxs-lookup"><span data-stu-id="618e8-196">about_Path_Syntax</span></span>](about_Path_Syntax.md)
- [<span data-ttu-id="618e8-197">about_Aliases</span><span class="sxs-lookup"><span data-stu-id="618e8-197">about_Aliases</span></span>](about_Aliases.md)
- [<span data-ttu-id="618e8-198">about_Functions</span><span class="sxs-lookup"><span data-stu-id="618e8-198">about_Functions</span></span>](about_Functions.md)
- [<span data-ttu-id="618e8-199">Alias provider</span><span class="sxs-lookup"><span data-stu-id="618e8-199">Alias-Provider</span></span>](../../Microsoft.PowerShell.Core/About/about_Alias_Provider.md)
- [<span data-ttu-id="618e8-200">Functie-provider</span><span class="sxs-lookup"><span data-stu-id="618e8-200">Function-Provider</span></span>](../../Microsoft.PowerShell.Core/About/about_Function_Provider.md)
- [<span data-ttu-id="618e8-201">Get-Command</span><span class="sxs-lookup"><span data-stu-id="618e8-201">Get-Command</span></span>](xref:Microsoft.PowerShell.Core.Get-Command)
- [<span data-ttu-id="618e8-202">Import-module</span><span class="sxs-lookup"><span data-stu-id="618e8-202">Import-Module</span></span>](xref:Microsoft.PowerShell.Core.Import-Module)
- [<span data-ttu-id="618e8-203">Import-PSSession</span><span class="sxs-lookup"><span data-stu-id="618e8-203">Import-PSSession</span></span>](xref:Microsoft.PowerShell.Utility.Import-PSSession)

