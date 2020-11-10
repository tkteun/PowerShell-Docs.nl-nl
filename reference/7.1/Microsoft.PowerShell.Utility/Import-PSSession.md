---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/import-pssession?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Import-PSSession
ms.openlocfilehash: 05e2d4575be1617feb29c58acbfd9a2a68fbb607
ms.sourcegitcommit: 2c311274ce721cd1072dcf2dc077226789e21868
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 11/10/2020
ms.locfileid: "94389178"
---
# <span data-ttu-id="a8bf2-103">Import-PSSession</span><span class="sxs-lookup"><span data-stu-id="a8bf2-103">Import-PSSession</span></span>

## <span data-ttu-id="a8bf2-104">SAMENVATTING</span><span class="sxs-lookup"><span data-stu-id="a8bf2-104">SYNOPSIS</span></span>
<span data-ttu-id="a8bf2-105">Importeert opdrachten vanuit een andere sessie in de huidige sessie.</span><span class="sxs-lookup"><span data-stu-id="a8bf2-105">Imports commands from another session into the current session.</span></span>

## <span data-ttu-id="a8bf2-106">SYNTAXIS</span><span class="sxs-lookup"><span data-stu-id="a8bf2-106">SYNTAX</span></span>

```
Import-PSSession [-Prefix <String>] [-DisableNameChecking] [[-CommandName] <String[]>] [-AllowClobber]
 [-ArgumentList <Object[]>] [-CommandType <CommandTypes>] [-Module <String[]>]
 [-FullyQualifiedModule <ModuleSpecification[]>] [[-FormatTypeName] <String[]>]
 [-Certificate <X509Certificate2>] [-Session] <PSSession> [<CommonParameters>]
```

## <span data-ttu-id="a8bf2-107">BESCHRIJVING</span><span class="sxs-lookup"><span data-stu-id="a8bf2-107">DESCRIPTION</span></span>

<span data-ttu-id="a8bf2-108">`Import-PSSession`Met de cmdlet worden opdrachten, zoals cmdlets, functies en aliassen, geïmporteerd van een PSSession op een lokale of externe computer in de huidige sessie.</span><span class="sxs-lookup"><span data-stu-id="a8bf2-108">The `Import-PSSession` cmdlet imports commands , such as cmdlets, functions, and aliases, from a PSSession on a local or remote computer into the current session.</span></span> <span data-ttu-id="a8bf2-109">U kunt elke opdracht importeren die met de `Get-Command` cmdlet kan worden gevonden in de PSSession.</span><span class="sxs-lookup"><span data-stu-id="a8bf2-109">You can import any command that the `Get-Command` cmdlet can find in the PSSession.</span></span>

<span data-ttu-id="a8bf2-110">Gebruik een `Import-PSSession` opdracht voor het importeren van opdrachten uit een aangepaste shell, zoals een micro soft Exchange server shell, of vanuit een sessie met Windows Power shell-modules en-modules of andere elementen die zich niet in de huidige sessie bevinden.</span><span class="sxs-lookup"><span data-stu-id="a8bf2-110">Use an `Import-PSSession` command to import commands from a customized shell, such as a Microsoft Exchange Server shell, or from a session that includes Windows PowerShell modules and snap-ins or other elements that are not in the current session.</span></span>

<span data-ttu-id="a8bf2-111">Voor het importeren van opdrachten moet u eerst de `New-PSSession` cmdlet gebruiken om een PSSession te maken.</span><span class="sxs-lookup"><span data-stu-id="a8bf2-111">To import commands, first use the `New-PSSession` cmdlet to create a PSSession.</span></span> <span data-ttu-id="a8bf2-112">Gebruik vervolgens de `Import-PSSession` cmdlet om de opdrachten te importeren.</span><span class="sxs-lookup"><span data-stu-id="a8bf2-112">Then, use the `Import-PSSession` cmdlet to import the commands.</span></span> <span data-ttu-id="a8bf2-113">Standaard worden `Import-PSSession` alle opdrachten geïmporteerd, met uitzonde ring van opdrachten met dezelfde namen als opdrachten in de huidige sessie.</span><span class="sxs-lookup"><span data-stu-id="a8bf2-113">By default, `Import-PSSession` imports all commands except for commands that have the same names as commands in the current session.</span></span> <span data-ttu-id="a8bf2-114">Als u alle opdrachten wilt importeren, gebruikt u de para meter **AllowClobber** .</span><span class="sxs-lookup"><span data-stu-id="a8bf2-114">To import all the commands, use the **AllowClobber** parameter.</span></span>

<span data-ttu-id="a8bf2-115">U kunt geïmporteerde opdrachten op dezelfde manier gebruiken als elke opdracht in de sessie.</span><span class="sxs-lookup"><span data-stu-id="a8bf2-115">You can use imported commands just as you would use any command in the session.</span></span> <span data-ttu-id="a8bf2-116">Wanneer u een geïmporteerde opdracht gebruikt, wordt het geïmporteerde deel van de opdracht impliciet uitgevoerd in de sessie van waaruit het is geïmporteerd.</span><span class="sxs-lookup"><span data-stu-id="a8bf2-116">When you use an imported command, the imported part of the command runs implicitly in the session from which it was imported.</span></span> <span data-ttu-id="a8bf2-117">De externe bewerkingen worden echter volledig verwerkt door Windows Power shell.</span><span class="sxs-lookup"><span data-stu-id="a8bf2-117">However, the remote operations are handled entirely by Windows PowerShell.</span></span> <span data-ttu-id="a8bf2-118">U hoeft er niet eens op te letten, behalve dat u de verbinding met de andere sessie (PSSession) open moet houden.</span><span class="sxs-lookup"><span data-stu-id="a8bf2-118">You need not even be aware of them, except that you must keep the connection to the other session (PSSession) open.</span></span> <span data-ttu-id="a8bf2-119">Als u het sluit, zijn de geïmporteerde opdrachten niet meer beschikbaar.</span><span class="sxs-lookup"><span data-stu-id="a8bf2-119">If you close it, the imported commands are no longer available.</span></span>

<span data-ttu-id="a8bf2-120">Omdat geïmporteerde opdrachten mogelijk langer duren om te worden uitgevoerd dan lokale opdrachten, `Import-PSSession` voegt een **AsJob** -para meter toe aan elke geïmporteerde opdracht.</span><span class="sxs-lookup"><span data-stu-id="a8bf2-120">Because imported commands might take longer to run than local commands, `Import-PSSession` adds an **AsJob** parameter to every imported command.</span></span> <span data-ttu-id="a8bf2-121">Met deze para meter kunt u de opdracht uitvoeren als een Windows Power shell-achtergrond taak.</span><span class="sxs-lookup"><span data-stu-id="a8bf2-121">This parameter allows you to run the command as a Windows PowerShell background job.</span></span> <span data-ttu-id="a8bf2-122">Zie [About Jobs](../Microsoft.PowerShell.Core/about/about_Jobs.md) (Taken) voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="a8bf2-122">For more information, see [about_Jobs](../Microsoft.PowerShell.Core/about/about_Jobs.md).</span></span>

<span data-ttu-id="a8bf2-123">Wanneer u gebruikt `Import-PSSession` , voegt Windows Power shell de geïmporteerde opdrachten toe aan een tijdelijke module die alleen in uw sessie bestaat en wordt een object geretourneerd dat de module vertegenwoordigt.</span><span class="sxs-lookup"><span data-stu-id="a8bf2-123">When you use `Import-PSSession`, Windows PowerShell adds the imported commands to a temporary module that exists only in your session and returns an object that represents the module.</span></span> <span data-ttu-id="a8bf2-124">Als u een permanente module wilt maken die u in toekomstige sessies kunt gebruiken, gebruikt u de `Export-PSSession` cmdlet.</span><span class="sxs-lookup"><span data-stu-id="a8bf2-124">To create a persistent module that you can use in future sessions, use the `Export-PSSession` cmdlet.</span></span>

<span data-ttu-id="a8bf2-125">De `Import-PSSession` cmdlet maakt gebruik van de impliciete externe functie van Windows Power shell.</span><span class="sxs-lookup"><span data-stu-id="a8bf2-125">The `Import-PSSession` cmdlet uses the implicit remoting feature of Windows PowerShell.</span></span> <span data-ttu-id="a8bf2-126">Wanneer u opdrachten in de huidige sessie importeert, worden deze impliciet uitgevoerd in de oorspronkelijke sessie of in een vergelijk bare sessie op de oorspronkelijke computer.</span><span class="sxs-lookup"><span data-stu-id="a8bf2-126">When you import commands into the current session, they run implicitly in the original session or in a similar session on the originating computer.</span></span>

<span data-ttu-id="a8bf2-127">Vanaf Windows Power Shell 3,0 kunt u met de `Import-Module` cmdlet modules uit een externe sessie importeren in de huidige sessie.</span><span class="sxs-lookup"><span data-stu-id="a8bf2-127">Beginning in Windows PowerShell 3.0, you can use the `Import-Module` cmdlet to import modules from a remote session into the current session.</span></span> <span data-ttu-id="a8bf2-128">Deze functie maakt gebruik van impliciete externe communicatie.</span><span class="sxs-lookup"><span data-stu-id="a8bf2-128">This feature uses implicit remoting.</span></span> <span data-ttu-id="a8bf2-129">Het is gelijk aan `Import-PSSession` het gebruik van om geselecteerde modules vanuit een externe sessie te importeren in de huidige sessie.</span><span class="sxs-lookup"><span data-stu-id="a8bf2-129">It is equivalent to using `Import-PSSession` to import selected modules from a remote session into the current session.</span></span>

## <span data-ttu-id="a8bf2-130">VOORBEELDEN</span><span class="sxs-lookup"><span data-stu-id="a8bf2-130">EXAMPLES</span></span>

### <span data-ttu-id="a8bf2-131">Voor beeld 1: alle opdrachten uit een PSSession importeren</span><span class="sxs-lookup"><span data-stu-id="a8bf2-131">Example 1: Import all commands from a PSSession</span></span>

```
PS C:\> $S = New-PSSession -ComputerName Server01
PS C:\> Import-PSSession -Session $S
```

<span data-ttu-id="a8bf2-132">Met deze opdracht worden alle opdrachten van een PSSession op de Server01-computer in de huidige sessie geïmporteerd, met uitzonde ring van opdrachten met dezelfde namen als opdrachten in de huidige sessie.</span><span class="sxs-lookup"><span data-stu-id="a8bf2-132">This command imports all commands from a PSSession on the Server01 computer into the current session, except for commands that have the same names as commands in the current session.</span></span>

<span data-ttu-id="a8bf2-133">Omdat met deze opdracht de para meter **opdracht** naam niet wordt gebruikt, worden ook alle opmaak gegevens die nodig zijn voor de geïmporteerde opdrachten geïmporteerd.</span><span class="sxs-lookup"><span data-stu-id="a8bf2-133">Because this command does not use the **CommandName** parameter, it also imports all of the formatting data required for the imported commands.</span></span>

### <span data-ttu-id="a8bf2-134">Voor beeld 2: opdrachten importeren die met een specifieke teken reeks eindigen</span><span class="sxs-lookup"><span data-stu-id="a8bf2-134">Example 2: Import commands that end with a specific string</span></span>

```
PS C:\> $S = New-PSSession https://ps.testlabs.com/powershell
PS C:\> Import-PSSession -Session $S -CommandName *-test -FormatTypeName *
PS C:\> New-Test -Name Test1
PS C:\> Get-Test test1 | Run-Test
```

<span data-ttu-id="a8bf2-135">Met deze opdrachten worden de opdrachten met namen die eindigen op '-test ' van een PSSession in de lokale sessie geïmporteerd. vervolgens wordt weer gegeven hoe u een geïmporteerde cmdlet gebruikt.</span><span class="sxs-lookup"><span data-stu-id="a8bf2-135">These commands import the commands with names that end in "-test" from a PSSession into the local session, and then they show how to use an imported cmdlet.</span></span>

<span data-ttu-id="a8bf2-136">De eerste opdracht gebruikt de `New-PSSession` cmdlet om een PSSession te maken.</span><span class="sxs-lookup"><span data-stu-id="a8bf2-136">The first command uses the `New-PSSession` cmdlet to create a PSSession.</span></span> <span data-ttu-id="a8bf2-137">De PSSession wordt opgeslagen in de `$S` variabele.</span><span class="sxs-lookup"><span data-stu-id="a8bf2-137">It saves the PSSession in the `$S` variable.</span></span>

<span data-ttu-id="a8bf2-138">Met de tweede opdracht wordt de `Import-PSSession` cmdlet gebruikt voor het importeren van opdrachten uit de PSSession in `$S` de huidige sessie.</span><span class="sxs-lookup"><span data-stu-id="a8bf2-138">The second command uses the `Import-PSSession` cmdlet to import commands from the PSSession in `$S` into the current session.</span></span> <span data-ttu-id="a8bf2-139">De para meter **opdracht** naam wordt gebruikt om opdrachten op te geven met het zelfstandig naam woord test en de para meter **FormatTypeName** om de opmaak gegevens voor de test opdrachten te importeren.</span><span class="sxs-lookup"><span data-stu-id="a8bf2-139">It uses the **CommandName** parameter to specify commands with the Test noun and the **FormatTypeName** parameter to import the formatting data for the Test commands.</span></span>

<span data-ttu-id="a8bf2-140">De derde en vierde opdracht gebruiken de geïmporteerde opdrachten in de huidige sessie.</span><span class="sxs-lookup"><span data-stu-id="a8bf2-140">The third and fourth commands use the imported commands in the current session.</span></span> <span data-ttu-id="a8bf2-141">Omdat geïmporteerde opdrachten daad werkelijk aan de huidige sessie worden toegevoegd, gebruikt u de lokale syntaxis om ze uit te voeren.</span><span class="sxs-lookup"><span data-stu-id="a8bf2-141">Because imported commands are actually added to the current session, you use the local syntax to run them.</span></span> <span data-ttu-id="a8bf2-142">U hoeft de cmdlet niet te gebruiken `Invoke-Command` om een geïmporteerde opdracht uit te voeren.</span><span class="sxs-lookup"><span data-stu-id="a8bf2-142">You do not need to use the `Invoke-Command` cmdlet to run an imported command.</span></span>

### <span data-ttu-id="a8bf2-143">Voor beeld 3: cmdlets importeren uit een PSSession</span><span class="sxs-lookup"><span data-stu-id="a8bf2-143">Example 3: Import cmdlets from a PSSession</span></span>

```
PS C:\> $S1 = New-PSSession -ComputerName s1
PS C:\> $S2 = New-PSSession -ComputerName s2
PS C:\> Import-PSSession -Session s1 -Type cmdlet -Name New-Test, Get-Test -FormatTypeName *
PS C:\> Import-PSSession -Session s2 -Type Cmdlet -Name Set-Test -FormatTypeName *
PS C:\> New-Test Test1 | Set-Test -RunType Full
```

<span data-ttu-id="a8bf2-144">Dit voor beeld laat zien dat u geïmporteerde cmdlets kunt gebruiken, net zoals u lokale cmdlets zou gebruiken.</span><span class="sxs-lookup"><span data-stu-id="a8bf2-144">This example shows that you can use imported cmdlets just as you would use local cmdlets.</span></span>

<span data-ttu-id="a8bf2-145">Met deze opdrachten worden de- `New-Test` en- `Get-Test` cmdlets van een PSSession op de Server01-computer en de `Set-Test` cmdlet van een PSSession op de Server02-computer geïmporteerd.</span><span class="sxs-lookup"><span data-stu-id="a8bf2-145">These commands import the `New-Test` and `Get-Test` cmdlets from a PSSession on the Server01 computer and the `Set-Test` cmdlet from a PSSession on the Server02 computer.</span></span>

<span data-ttu-id="a8bf2-146">Hoewel de cmdlets uit verschillende PSSessions zijn geïmporteerd, kunt u zonder fouten een object van de ene naar de andere cmdlet sluizen.</span><span class="sxs-lookup"><span data-stu-id="a8bf2-146">Even though the cmdlets were imported from different PSSessions, you can pipe an object from one cmdlet to another without error.</span></span>

### <span data-ttu-id="a8bf2-147">Voor beeld 4: een geïmporteerde opdracht uitvoeren als een achtergrond taak</span><span class="sxs-lookup"><span data-stu-id="a8bf2-147">Example 4: Run an imported command as a background job</span></span>

```
PS C:\> $S = New-PSSession -ComputerName Server01
PS C:\> Import-PSSession -Session $S -CommandName *-test* -FormatTypeName *
PS C:\> $batch = New-Test -Name Batch -AsJob
PS C:\> Receive-Job $batch
```

<span data-ttu-id="a8bf2-148">In dit voor beeld ziet u hoe u een geïmporteerde opdracht als achtergrond taak uitvoert.</span><span class="sxs-lookup"><span data-stu-id="a8bf2-148">This example shows how to run an imported command as a background job.</span></span>

<span data-ttu-id="a8bf2-149">Omdat geïmporteerde opdrachten mogelijk langer duren om te worden uitgevoerd dan lokale opdrachten, `Import-PSSession` voegt een **AsJob** -para meter toe aan elke geïmporteerde opdracht.</span><span class="sxs-lookup"><span data-stu-id="a8bf2-149">Because imported commands might take longer to run than local commands, `Import-PSSession` adds an **AsJob** parameter to every imported command.</span></span> <span data-ttu-id="a8bf2-150">Met de para meter **AsJob** kunt u de opdracht uitvoeren als een achtergrond taak.</span><span class="sxs-lookup"><span data-stu-id="a8bf2-150">The **AsJob** parameter lets you run the command as a background job.</span></span>

<span data-ttu-id="a8bf2-151">Met de eerste opdracht maakt u een PSSession op de Server01-computer en slaat u het PSSession-object op in de `$S` variabele.</span><span class="sxs-lookup"><span data-stu-id="a8bf2-151">The first command creates a PSSession on the Server01 computer and saves the PSSession object in the `$S` variable.</span></span>

<span data-ttu-id="a8bf2-152">De tweede opdracht gebruikt `Import-PSSession` voor het importeren van de test-cmdlets van de PSSession in `$S` naar de huidige sessie.</span><span class="sxs-lookup"><span data-stu-id="a8bf2-152">The second command uses `Import-PSSession` to import the Test cmdlets from the PSSession in `$S` into the current session.</span></span>

<span data-ttu-id="a8bf2-153">De derde opdracht maakt gebruik van de para meter **AsJob** van de geïmporteerde `New-Test` cmdlet om een `New-Test` opdracht als achtergrond taak uit te voeren.</span><span class="sxs-lookup"><span data-stu-id="a8bf2-153">The third command uses the **AsJob** parameter of the imported `New-Test` cmdlet to run a `New-Test` command as a background job.</span></span> <span data-ttu-id="a8bf2-154">Met de opdracht slaat u het taak object `New-Test` op dat in de variabele wordt geretourneerd `$batch` .</span><span class="sxs-lookup"><span data-stu-id="a8bf2-154">The command saves the job object that `New-Test` returns in the `$batch` variable.</span></span>

<span data-ttu-id="a8bf2-155">De vierde opdracht gebruikt de `Receive-Job` cmdlet om de resultaten van de taak in de variabele op te halen `$batch` .</span><span class="sxs-lookup"><span data-stu-id="a8bf2-155">The fourth command uses the `Receive-Job` cmdlet to get the results of the job in the `$batch` variable.</span></span>

### <span data-ttu-id="a8bf2-156">Voor beeld 5: cmdlets en functies importeren vanuit een Windows Power shell-module</span><span class="sxs-lookup"><span data-stu-id="a8bf2-156">Example 5: Import cmdlets and functions from a Windows PowerShell module</span></span>

```
PS C:\> $S = New-PSSession -ComputerName Server01
PS C:\> Invoke-Command -Session $S {Import-Module TestManagement}
PS C:\> Import-PSSession -Session $S -Module TestManagement
```

<span data-ttu-id="a8bf2-157">In dit voor beeld ziet u hoe u de cmdlets en functies van een Windows Power shell-module op een externe computer kunt importeren in de huidige sessie.</span><span class="sxs-lookup"><span data-stu-id="a8bf2-157">This example shows how to import the cmdlets and functions from a Windows PowerShell module on a remote computer into the current session.</span></span>

<span data-ttu-id="a8bf2-158">Met de eerste opdracht maakt u een PSSession op de Server01-computer en slaat u deze op in de `$S` variabele.</span><span class="sxs-lookup"><span data-stu-id="a8bf2-158">The first command creates a PSSession on the Server01 computer and saves it in the `$S` variable.</span></span>

<span data-ttu-id="a8bf2-159">De tweede opdracht gebruikt de `Invoke-Command` cmdlet om een opdracht uit te voeren `Import-Module` in de PSSession in `$S` .</span><span class="sxs-lookup"><span data-stu-id="a8bf2-159">The second command uses the `Invoke-Command` cmdlet to run an `Import-Module` command in the PSSession in `$S`.</span></span>

<span data-ttu-id="a8bf2-160">Normaal gesp roken wordt de module toegevoegd aan alle sessies met een `Import-Module` opdracht in een Windows Power shell-profiel, maar profielen worden niet uitgevoerd in PSSessions.</span><span class="sxs-lookup"><span data-stu-id="a8bf2-160">Typically, the module would be added to all sessions by an `Import-Module` command in a Windows PowerShell profile, but profiles are not run in PSSessions.</span></span>

<span data-ttu-id="a8bf2-161">De derde opdracht maakt gebruik van de para meter **module** van `Import-PSSession` om de cmdlets en functies in de module te importeren in de huidige sessie.</span><span class="sxs-lookup"><span data-stu-id="a8bf2-161">The third command uses the **Module** parameter of `Import-PSSession` to import the cmdlets and functions in the module into the current session.</span></span>

### <span data-ttu-id="a8bf2-162">Voor beeld 6: een module maken in een tijdelijk bestand</span><span class="sxs-lookup"><span data-stu-id="a8bf2-162">Example 6: Create a module in a temporary file</span></span>

```
PS C:\> Import-PSSession $S -CommandName Get-Date, SearchHelp -FormatTypeName * -AllowClobber

Name              : tmp_79468106-4e1d-4d90-af97-1154f9317239_tcw1zunz.ttf
Path              : C:\Users\User01\AppData\Local\Temp\tmp_79468106-4e1d-4d90-af97-1154f9317239_tcw1
zunz.ttf\tmp_79468106-4e1d-4d90-af97-1154f9317239_
tcw1zunz.ttf.psm1
Description       : Implicit remoting for http://server01.corp.fabrikam.com/wsman
Guid              : 79468106-4e1d-4d90-af97-1154f9317239
Version           : 1.0
ModuleBase        : C:\Users\User01\AppData\Local\Temp\tmp_79468106-4e1d-4d90-af97-1154f9317239_tcw1
zunz.ttf
ModuleType        : Script
PrivateData       : {ImplicitRemoting}
AccessMode        : ReadWrite
ExportedAliases   : {}
ExportedCmdlets   : {}
ExportedFunctions : {[Get-Date, Get-Date], [SearchHelp, SearchHelp]}
ExportedVariables : {}
NestedModules     : {}
```

<span data-ttu-id="a8bf2-163">Dit voor beeld laat zien dat `Import-PSSession` een module maakt in een tijdelijk bestand op schijf.</span><span class="sxs-lookup"><span data-stu-id="a8bf2-163">This example shows that `Import-PSSession` creates a module in a temporary file on disk.</span></span> <span data-ttu-id="a8bf2-164">Er wordt ook weer gegeven dat alle opdrachten worden geconverteerd naar functies voordat ze in de huidige sessie worden geïmporteerd.</span><span class="sxs-lookup"><span data-stu-id="a8bf2-164">It also shows that all commands are converted into functions before they are imported into the current session.</span></span>

<span data-ttu-id="a8bf2-165">De opdracht gebruikt de `Import-PSSession` cmdlet om een `Get-Date` cmdlet en een SearchHelp-functie te importeren in de huidige sessie.</span><span class="sxs-lookup"><span data-stu-id="a8bf2-165">The command uses the `Import-PSSession` cmdlet to import a `Get-Date` cmdlet and a SearchHelp function into the current session.</span></span>

<span data-ttu-id="a8bf2-166">De `Import-PSSession` cmdlet retourneert een **PSModuleInfo** -object dat de tijdelijke module vertegenwoordigt.</span><span class="sxs-lookup"><span data-stu-id="a8bf2-166">The `Import-PSSession` cmdlet returns a **PSModuleInfo** object that represents the temporary module.</span></span> <span data-ttu-id="a8bf2-167">De waarde van de eigenschap **Path** geeft `Import-PSSession` aan dat er een script module-bestand (. psm1) op een tijdelijke locatie is gemaakt.</span><span class="sxs-lookup"><span data-stu-id="a8bf2-167">The value of the **Path** property shows that `Import-PSSession` created a script module (.psm1) file in a temporary location.</span></span> <span data-ttu-id="a8bf2-168">De eigenschap **ExportedFunctions** geeft aan dat de `Get-Date` cmdlet en de functie SearchHelp als functies zijn geïmporteerd.</span><span class="sxs-lookup"><span data-stu-id="a8bf2-168">The **ExportedFunctions** property shows that the `Get-Date` cmdlet and the SearchHelp function were both imported as functions.</span></span>

### <span data-ttu-id="a8bf2-169">Voor beeld 7: een opdracht uitvoeren die is verborgen met een geïmporteerde opdracht</span><span class="sxs-lookup"><span data-stu-id="a8bf2-169">Example 7: Run a command that is hidden by an imported command</span></span>

```
PS C:\> Import-PSSession $S -CommandName Get-Date -FormatTypeName * -AllowClobber

PS C:\> Get-Command Get-Date -All

CommandType   Name       Definition
-----------   ----       ----------
Function      Get-Date   ...
Cmdlet        Get-Date   Get-Date [[-Date] <DateTime>] [-Year <Int32>] [-Month <Int32>]

PS C:\> Get-Date
09074

PS C:\> (Get-Command -Type Cmdlet -Name Get-Date).PSSnapin.Name
Microsoft.PowerShell.Utility

PS C:\> Microsoft.PowerShell.Utility\Get-Date
Sunday, March 15, 2009 2:08:26 PM
```

<span data-ttu-id="a8bf2-170">In dit voor beeld ziet u hoe u een opdracht uitvoert die verborgen is door een geïmporteerde opdracht.</span><span class="sxs-lookup"><span data-stu-id="a8bf2-170">This example shows how to run a command that is hidden by an imported command.</span></span>

<span data-ttu-id="a8bf2-171">Met de eerste opdracht wordt een `Get-Date` cmdlet uit de PSSession in de `$S` variabele geïmporteerd.</span><span class="sxs-lookup"><span data-stu-id="a8bf2-171">The first command imports a `Get-Date` cmdlet from the PSSession in the `$S` variable.</span></span> <span data-ttu-id="a8bf2-172">Omdat de huidige sessie een `Get-Date` cmdlet bevat, is de para meter **AllowClobber** vereist in de opdracht.</span><span class="sxs-lookup"><span data-stu-id="a8bf2-172">Because the current session includes a `Get-Date` cmdlet, the **AllowClobber** parameter is required in the command.</span></span>

<span data-ttu-id="a8bf2-173">Met de tweede opdracht wordt de para meter **all** van de `Get-Command` cmdlet gebruikt om alle `Get-Date` opdrachten in de huidige sessie op te halen.</span><span class="sxs-lookup"><span data-stu-id="a8bf2-173">The second command uses the **All** parameter of the `Get-Command` cmdlet to get all `Get-Date` commands in the current session.</span></span> <span data-ttu-id="a8bf2-174">De uitvoer laat zien dat de sessie de oorspronkelijke `Get-Date` cmdlet en een `Get-Date` functie bevat.</span><span class="sxs-lookup"><span data-stu-id="a8bf2-174">The output shows that the session includes the original `Get-Date` cmdlet and a `Get-Date` function.</span></span> <span data-ttu-id="a8bf2-175">De `Get-Date` functie voert de geïmporteerde `Get-Date` cmdlet uit in de PSSession in `$S` .</span><span class="sxs-lookup"><span data-stu-id="a8bf2-175">The `Get-Date` function runs the imported `Get-Date` cmdlet in the PSSession in `$S`.</span></span>

<span data-ttu-id="a8bf2-176">Met de derde opdracht wordt een `Get-Date` opdracht uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="a8bf2-176">The third command runs a `Get-Date` command.</span></span> <span data-ttu-id="a8bf2-177">Omdat functies voor rang hebben boven cmdlets, voert Windows Power shell de geïmporteerde `Get-Date` functie uit, waardoor een Juliaanse datum wordt geretourneerd.</span><span class="sxs-lookup"><span data-stu-id="a8bf2-177">Because functions take precedence over cmdlets, Windows PowerShell runs the imported `Get-Date` function, which returns a Julian date.</span></span>

<span data-ttu-id="a8bf2-178">De vierde en vijfde opdrachten laten zien hoe u een gekwalificeerde naam kunt gebruiken om een opdracht uit te voeren die verborgen is door een geïmporteerde opdracht.</span><span class="sxs-lookup"><span data-stu-id="a8bf2-178">The fourth and fifth commands show how to use a qualified name to run a command that is hidden by an imported command.</span></span>

<span data-ttu-id="a8bf2-179">Met de vierde opdracht haalt u de naam op van de Windows Power shell-module waarmee de oorspronkelijke cmdlet is toegevoegd `Get-Date` aan de huidige sessie.</span><span class="sxs-lookup"><span data-stu-id="a8bf2-179">The fourth command gets the name of the Windows PowerShell snap-in that added the original `Get-Date` cmdlet to the current session.</span></span>

<span data-ttu-id="a8bf2-180">De vijfde opdracht maakt gebruik van de met de module gekwalificeerde naam van de `Get-Date` cmdlet om een opdracht uit te voeren `Get-Date` .</span><span class="sxs-lookup"><span data-stu-id="a8bf2-180">The fifth command uses the snap-in-qualified name of the `Get-Date` cmdlet to run a `Get-Date` command.</span></span>

<span data-ttu-id="a8bf2-181">Zie [about_Command_Precedence](../Microsoft.PowerShell.Core/about/about_Command_Precedence.md)voor meer informatie over de prioriteit van opdrachten en verborgen opdrachten.</span><span class="sxs-lookup"><span data-stu-id="a8bf2-181">For more information about command precedence and hidden commands, see [about_Command_Precedence](../Microsoft.PowerShell.Core/about/about_Command_Precedence.md).</span></span>

### <span data-ttu-id="a8bf2-182">Voor beeld 8: opdrachten importeren die een specifieke teken reeks in hun namen hebben</span><span class="sxs-lookup"><span data-stu-id="a8bf2-182">Example 8: Import commands that have a specific string in their names</span></span>

```
PS C:\> Import-PSSession -Session $S -CommandName **Item** -AllowClobber
```

<span data-ttu-id="a8bf2-183">Met deze opdracht worden opdrachten geïmporteerd waarvan de naam item uit de PSSession bevat `$S` .</span><span class="sxs-lookup"><span data-stu-id="a8bf2-183">This command imports commands whose names include Item from the PSSession in `$S`.</span></span> <span data-ttu-id="a8bf2-184">Omdat de opdracht de para meter **opdrachtnaam** , maar niet de para meter **FormatTypeData** bevat, wordt alleen de opdracht geïmporteerd.</span><span class="sxs-lookup"><span data-stu-id="a8bf2-184">Because the command includes the **CommandName** parameter but not the **FormatTypeData** parameter, only the command is imported.</span></span>

<span data-ttu-id="a8bf2-185">Gebruik deze opdracht wanneer u gebruikt `Import-PSSession` om een opdracht uit te voeren op een externe computer en u beschikt al over de indelings gegevens voor de opdracht in de huidige sessie.</span><span class="sxs-lookup"><span data-stu-id="a8bf2-185">Use this command when you are using `Import-PSSession` to run a command on a remote computer and you already have the formatting data for the command in the current session.</span></span>

### <span data-ttu-id="a8bf2-186">Voor beeld 9: de module parameter gebruiken om te ontdekken welke opdrachten in de sessie zijn geïmporteerd</span><span class="sxs-lookup"><span data-stu-id="a8bf2-186">Example 9: Use the Module parameter to discover which commands were imported into the session</span></span>

```
PS C:\> $M = Import-PSSession -Session $S -CommandName *bits* -FormatTypeName *bits*
PS C:\> Get-Command -Module $M
CommandType     Name
-----------     ----
Function        Add-BitsFile
Function        Complete-BitsTransfer
Function        Get-BitsTransfer
Function        Remove-BitsTransfer
Function        Resume-BitsTransfer
Function        Set-BitsTransfer
Function        Start-BitsTransfer
Function        Suspend-BitsTransfer
```

<span data-ttu-id="a8bf2-187">Met deze opdracht wordt uitgelegd hoe u de **module** parameter van gebruikt `Get-Command` om te ontdekken welke opdrachten in de sessie zijn geïmporteerd door een `Import-PSSession` opdracht.</span><span class="sxs-lookup"><span data-stu-id="a8bf2-187">This command shows how to use the **Module** parameter of `Get-Command` to find out which commands were imported into the session by an `Import-PSSession` command.</span></span>

<span data-ttu-id="a8bf2-188">De eerste opdracht gebruikt de `Import-PSSession` cmdlet om opdrachten te importeren waarvan de naam ' bits ' bevat uit de PSSession in de `$S` variabele.</span><span class="sxs-lookup"><span data-stu-id="a8bf2-188">The first command uses the `Import-PSSession` cmdlet to import commands whose names include "bits" from the PSSession in the `$S` variable.</span></span> <span data-ttu-id="a8bf2-189">De `Import-PSSession` opdracht retourneert een tijdelijke module en de opdracht slaat de module op in de `$m` variabele.</span><span class="sxs-lookup"><span data-stu-id="a8bf2-189">The `Import-PSSession` command returns a temporary module, and the command saves the module in the `$m` variable.</span></span>

<span data-ttu-id="a8bf2-190">De tweede opdracht gebruikt de `Get-Command` cmdlet om de opdrachten op te halen die worden geëxporteerd door de module in de `$M` variabele.</span><span class="sxs-lookup"><span data-stu-id="a8bf2-190">The second command uses the `Get-Command` cmdlet to get the commands that are exported by the module in the `$M` variable.</span></span>

<span data-ttu-id="a8bf2-191">De **module** parameter heeft een teken reeks waarde die is ontworpen voor de module naam.</span><span class="sxs-lookup"><span data-stu-id="a8bf2-191">The **Module** parameter takes a string value, which is designed for the module name.</span></span> <span data-ttu-id="a8bf2-192">Wanneer u echter een module object verzendt, gebruikt Windows Power shell de **toString** -methode voor het module object, waarmee de module naam wordt geretourneerd.</span><span class="sxs-lookup"><span data-stu-id="a8bf2-192">However, when you submit a module object, Windows PowerShell uses the **ToString** method on the module object, which returns the module name.</span></span>

<span data-ttu-id="a8bf2-193">De `Get-Command` opdracht is het equivalent van `Get-Command $M.Name` '.</span><span class="sxs-lookup"><span data-stu-id="a8bf2-193">The `Get-Command` command is the equivalent of `Get-Command $M.Name`".</span></span>

## <span data-ttu-id="a8bf2-194">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="a8bf2-194">PARAMETERS</span></span>

### <span data-ttu-id="a8bf2-195">-AllowClobber</span><span class="sxs-lookup"><span data-stu-id="a8bf2-195">-AllowClobber</span></span>

<span data-ttu-id="a8bf2-196">Geeft aan dat met deze cmdlet de opgegeven opdrachten worden geïmporteerd, zelfs als ze dezelfde namen hebben als opdrachten in de huidige sessie.</span><span class="sxs-lookup"><span data-stu-id="a8bf2-196">Indicates that this cmdlet imports the specified commands, even if they have the same names as commands in the current session.</span></span>

<span data-ttu-id="a8bf2-197">Als u een opdracht importeert met dezelfde naam als een opdracht in de huidige sessie, worden de oorspronkelijke opdrachten verborgen of vervangen door de geïmporteerde opdracht.</span><span class="sxs-lookup"><span data-stu-id="a8bf2-197">If you import a command with the same name as a command in the current session, the imported command hides or replaces the original commands.</span></span> <span data-ttu-id="a8bf2-198">Zie [about_Command_Precedence](../Microsoft.PowerShell.Core/about/about_Command_Precedence.md)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="a8bf2-198">For more information, see [about_Command_Precedence](../Microsoft.PowerShell.Core/about/about_Command_Precedence.md).</span></span>

<span data-ttu-id="a8bf2-199">`Import-PSSession`Opdrachten die dezelfde naam hebben als opdrachten in de huidige sessie, worden standaard niet geïmporteerd.</span><span class="sxs-lookup"><span data-stu-id="a8bf2-199">By default, `Import-PSSession` does not import commands that have the same name as commands in the current session.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="a8bf2-200">-Argument List</span><span class="sxs-lookup"><span data-stu-id="a8bf2-200">-ArgumentList</span></span>

<span data-ttu-id="a8bf2-201">Hiermee geeft u een matrix met opdrachten op die het resultaat zijn van het gebruik van de opgegeven argumenten (parameter waarden).</span><span class="sxs-lookup"><span data-stu-id="a8bf2-201">Specifies an array of commands that results from using the specified arguments (parameter values).</span></span>

<span data-ttu-id="a8bf2-202">Om bijvoorbeeld de variant van de `Get-Item` opdracht in het certificaat te importeren (CERT:) in het PSSession-station in `$S` , typt u `Import-PSSession -Session $S -Command Get-Item -ArgumentList cert:` .</span><span class="sxs-lookup"><span data-stu-id="a8bf2-202">For instance, to import the variant of the `Get-Item` command in the certificate (Cert:) drive in the PSSession in `$S`, type `Import-PSSession -Session $S -Command Get-Item -ArgumentList cert:`.</span></span>

```yaml
Type: System.Object[]
Parameter Sets: (All)
Aliases: Args

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="a8bf2-203">-Certificaat</span><span class="sxs-lookup"><span data-stu-id="a8bf2-203">-Certificate</span></span>

<span data-ttu-id="a8bf2-204">Hiermee geeft u het client certificaat op dat wordt gebruikt voor het ondertekenen van de indelings bestanden (\* .Format.ps1XML) of script module bestanden (. psm1) in de tijdelijke module die `Import-PSSession` wordt gemaakt.</span><span class="sxs-lookup"><span data-stu-id="a8bf2-204">Specifies the client certificate that is used to sign the format files (\*.Format.ps1xml) or script module files (.psm1) in the temporary module that `Import-PSSession` creates.</span></span>

<span data-ttu-id="a8bf2-205">Voer een variabele in die een certificaat of een opdracht of expressie bevat waarmee het certificaat wordt opgehaald.</span><span class="sxs-lookup"><span data-stu-id="a8bf2-205">Enter a variable that contains a certificate or a command or expression that gets the certificate.</span></span>

<span data-ttu-id="a8bf2-206">Als u een certificaat wilt zoeken, gebruikt u de `Get-PfxCertificate` cmdlet of gebruikt u de `Get-ChildItem` cmdlet in het certificaat (CERT:) stationsletter.</span><span class="sxs-lookup"><span data-stu-id="a8bf2-206">To find a certificate, use the `Get-PfxCertificate` cmdlet or use the `Get-ChildItem` cmdlet in the Certificate (Cert:) drive.</span></span> <span data-ttu-id="a8bf2-207">Als het certificaat ongeldig is of niet voldoende autoriteit heeft, mislukt de opdracht.</span><span class="sxs-lookup"><span data-stu-id="a8bf2-207">If the certificate is not valid or does not have sufficient authority, the command fails.</span></span>

```yaml
Type: System.Security.Cryptography.X509Certificates.X509Certificate2
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="a8bf2-208">-Opdrachtnaam</span><span class="sxs-lookup"><span data-stu-id="a8bf2-208">-CommandName</span></span>

<span data-ttu-id="a8bf2-209">Geeft opdrachten met de opgegeven namen of naam patronen.</span><span class="sxs-lookup"><span data-stu-id="a8bf2-209">Specifies commands with the specified names or name patterns.</span></span> <span data-ttu-id="a8bf2-210">Joker tekens zijn toegestaan.</span><span class="sxs-lookup"><span data-stu-id="a8bf2-210">Wildcards are permitted.</span></span> <span data-ttu-id="a8bf2-211">Gebruik de **naam** van de **opdracht** of de alias.</span><span class="sxs-lookup"><span data-stu-id="a8bf2-211">Use **CommandName** or its alias, **Name**.</span></span>

<span data-ttu-id="a8bf2-212">Standaard worden `Import-PSSession` alle opdrachten uit de sessie geïmporteerd, met uitzonde ring van opdrachten die dezelfde namen hebben als opdrachten in de huidige sessie.</span><span class="sxs-lookup"><span data-stu-id="a8bf2-212">By default, `Import-PSSession` imports all commands from the session, except for commands that have the same names as commands in the current session.</span></span> <span data-ttu-id="a8bf2-213">Zo voor komt u dat geïmporteerde opdrachten opdrachten in de sessie verbergen of vervangen.</span><span class="sxs-lookup"><span data-stu-id="a8bf2-213">This prevents imported commands from hiding or replacing commands in the session.</span></span> <span data-ttu-id="a8bf2-214">Gebruik de para meter **AllowClobber** als u alle opdrachten wilt importeren, zelfs op die andere opdrachten.</span><span class="sxs-lookup"><span data-stu-id="a8bf2-214">To import all commands, even those that hide or replace other commands, use the **AllowClobber** parameter.</span></span>

<span data-ttu-id="a8bf2-215">Als u de para meter **opdrachtnaam** gebruikt, worden de opmaak bestanden voor de opdrachten niet geïmporteerd, tenzij u de para meter **FormatTypeName** gebruikt.</span><span class="sxs-lookup"><span data-stu-id="a8bf2-215">If you use the **CommandName** parameter, the formatting files for the commands are not imported unless you use the **FormatTypeName** parameter.</span></span> <span data-ttu-id="a8bf2-216">Ook als u de para meter **FormatTypeName** gebruikt, worden er geen opdrachten geïmporteerd, tenzij u de para meter **opdrachtnaam** gebruikt.</span><span class="sxs-lookup"><span data-stu-id="a8bf2-216">Similarly, if you use the **FormatTypeName** parameter, no commands are imported unless you use the **CommandName** parameter.</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases: Name

Required: False
Position: 2
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="a8bf2-217">-CommandType</span><span class="sxs-lookup"><span data-stu-id="a8bf2-217">-CommandType</span></span>

<span data-ttu-id="a8bf2-218">Hiermee wordt het type opdracht objecten opgegeven.</span><span class="sxs-lookup"><span data-stu-id="a8bf2-218">Specifies the type of command objects.</span></span> <span data-ttu-id="a8bf2-219">De standaard waarde is cmdlet.</span><span class="sxs-lookup"><span data-stu-id="a8bf2-219">The default value is Cmdlet.</span></span> <span data-ttu-id="a8bf2-220">Gebruik **CommandType** of de alias, **Typ**.</span><span class="sxs-lookup"><span data-stu-id="a8bf2-220">Use **CommandType** or its alias, **Type**.</span></span> <span data-ttu-id="a8bf2-221">De aanvaardbare waarden voor deze parameter zijn:</span><span class="sxs-lookup"><span data-stu-id="a8bf2-221">The acceptable values for this parameter are:</span></span>

- <span data-ttu-id="a8bf2-222">Toe.</span><span class="sxs-lookup"><span data-stu-id="a8bf2-222">Alias.</span></span> <span data-ttu-id="a8bf2-223">De Windows Power shell-aliassen in de externe sessie.</span><span class="sxs-lookup"><span data-stu-id="a8bf2-223">The Windows PowerShell aliases in the remote session.</span></span>
- <span data-ttu-id="a8bf2-224">Hele.</span><span class="sxs-lookup"><span data-stu-id="a8bf2-224">All.</span></span> <span data-ttu-id="a8bf2-225">De cmdlets en functies in de externe sessie.</span><span class="sxs-lookup"><span data-stu-id="a8bf2-225">The cmdlets and functions in the remote session.</span></span>
- <span data-ttu-id="a8bf2-226">Modules.</span><span class="sxs-lookup"><span data-stu-id="a8bf2-226">Application.</span></span> <span data-ttu-id="a8bf2-227">Alle bestanden met uitzonde ring van Windows-PowerShell bestanden in de paden die worden vermeld in de Path-omgevings variabele ( `$env:path` ) in de externe sessie, inclusief. txt,. exe en. dll-bestanden.</span><span class="sxs-lookup"><span data-stu-id="a8bf2-227">All the files other than Windows-PowerShell files in the paths that are listed in the Path environment variable (`$env:path`) in the remote session, including .txt, .exe, and .dll files.</span></span>
- <span data-ttu-id="a8bf2-228">Cmdlet.</span><span class="sxs-lookup"><span data-stu-id="a8bf2-228">Cmdlet.</span></span> <span data-ttu-id="a8bf2-229">De cmdlets in de externe sessie.</span><span class="sxs-lookup"><span data-stu-id="a8bf2-229">The cmdlets in the remote session.</span></span> <span data-ttu-id="a8bf2-230">' Cmdlet ' is de standaard waarde.</span><span class="sxs-lookup"><span data-stu-id="a8bf2-230">"Cmdlet" is the default.</span></span>
- <span data-ttu-id="a8bf2-231">ExternalScript.</span><span class="sxs-lookup"><span data-stu-id="a8bf2-231">ExternalScript.</span></span> <span data-ttu-id="a8bf2-232">De. ps1-bestanden in de paden die worden weer gegeven in de omgevings variabele PATH ( `$env:path` ) in de externe sessie.</span><span class="sxs-lookup"><span data-stu-id="a8bf2-232">The .ps1 files in the paths listed in the Path environment variable (`$env:path`) in the remote session.</span></span>
- <span data-ttu-id="a8bf2-233">Filter en functie.</span><span class="sxs-lookup"><span data-stu-id="a8bf2-233">Filter and Function.</span></span> <span data-ttu-id="a8bf2-234">De Windows Power shell-functies in de externe sessie.</span><span class="sxs-lookup"><span data-stu-id="a8bf2-234">The Windows PowerShell functions in the remote session.</span></span>
- <span data-ttu-id="a8bf2-235">Schriften.</span><span class="sxs-lookup"><span data-stu-id="a8bf2-235">Script.</span></span> <span data-ttu-id="a8bf2-236">De script blokken in de externe sessie.</span><span class="sxs-lookup"><span data-stu-id="a8bf2-236">The script blocks in the remote session.</span></span>

```yaml
Type: System.Management.Automation.CommandTypes
Parameter Sets: (All)
Aliases: Type
Accepted values: Alias, Function, Filter, Cmdlet, ExternalScript, Application, Script, Workflow, Configuration, All

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="a8bf2-237">-DisableNameChecking</span><span class="sxs-lookup"><span data-stu-id="a8bf2-237">-DisableNameChecking</span></span>

<span data-ttu-id="a8bf2-238">Geeft aan dat deze cmdlet het bericht onderdrukt dat u waarschuwt wanneer u een cmdlet of functie importeert waarvan de naam een niet-goedgekeurde term of een verboden teken bevat.</span><span class="sxs-lookup"><span data-stu-id="a8bf2-238">Indicates that this cmdlet suppresses the message that warns you when you import a cmdlet or function whose name includes an unapproved verb or a prohibited character.</span></span>

<span data-ttu-id="a8bf2-239">Als een module die u importeert cmdlets of functies met een niet-goedgekeurde term in hun namen, wordt standaard het volgende waarschuwings bericht weer gegeven:</span><span class="sxs-lookup"><span data-stu-id="a8bf2-239">By default, when a module that you import exports cmdlets or functions that have unapproved verbs in their names, the Windows PowerShell displays the following warning message:</span></span>

<span data-ttu-id="a8bf2-240">"Waarschuwing: Sommige geïmporteerde opdracht namen bevatten niet-goedgekeurde werk woorden, waardoor ze minder kunnen worden gedetecteerd.</span><span class="sxs-lookup"><span data-stu-id="a8bf2-240">"WARNING: Some imported command names include unapproved verbs which might make them less discoverable.</span></span> <span data-ttu-id="a8bf2-241">Gebruik de para meter uitgebreid voor meer details of type `Get-Verb` om de lijst met goedgekeurde woorden weer te geven. "</span><span class="sxs-lookup"><span data-stu-id="a8bf2-241">Use the Verbose parameter for more detail or type `Get-Verb` to see the list of approved verbs."</span></span>

<span data-ttu-id="a8bf2-242">Dit bericht wordt alleen een waarschuwing gegeven.</span><span class="sxs-lookup"><span data-stu-id="a8bf2-242">This message is only a warning.</span></span> <span data-ttu-id="a8bf2-243">De volledige module is nog steeds geïmporteerd, met inbegrip van de niet-conforme opdrachten.</span><span class="sxs-lookup"><span data-stu-id="a8bf2-243">The complete module is still imported, including the non-conforming commands.</span></span> <span data-ttu-id="a8bf2-244">Hoewel het bericht wordt weer gegeven voor module gebruikers, moet het naam probleem worden opgelost door de module auteur.</span><span class="sxs-lookup"><span data-stu-id="a8bf2-244">Although the message is displayed to module users, the naming problem should be fixed by the module author.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="a8bf2-245">-FormatTypeName</span><span class="sxs-lookup"><span data-stu-id="a8bf2-245">-FormatTypeName</span></span>

<span data-ttu-id="a8bf2-246">Hiermee geeft u opmaak instructies op voor de opgegeven Microsoft .NET Framework typen.</span><span class="sxs-lookup"><span data-stu-id="a8bf2-246">Specifies formatting instructions for the specified Microsoft .NET Framework types.</span></span>
<span data-ttu-id="a8bf2-247">Voer de type namen in.</span><span class="sxs-lookup"><span data-stu-id="a8bf2-247">Enter the type names.</span></span>
<span data-ttu-id="a8bf2-248">Joker tekens zijn toegestaan.</span><span class="sxs-lookup"><span data-stu-id="a8bf2-248">Wildcards are permitted.</span></span>

<span data-ttu-id="a8bf2-249">De waarde van deze para meter moet de naam van een type zijn dat wordt geretourneerd door een `Get-FormatData` opdracht in de sessie van waaruit de opdrachten worden geïmporteerd.</span><span class="sxs-lookup"><span data-stu-id="a8bf2-249">The value of this parameter must be the name of a type that is returned by a `Get-FormatData` command in the session from which the commands are being imported.</span></span> <span data-ttu-id="a8bf2-250">Als u alle opmaak gegevens in de externe sessie wilt ophalen, typt u `*` .</span><span class="sxs-lookup"><span data-stu-id="a8bf2-250">To get all of the formatting data in the remote session, type `*`.</span></span>

<span data-ttu-id="a8bf2-251">Als de opdracht geen **opdracht** naam of para meter **FormatTypeName** bevat, worden `Import-PSSession` in de externe sessie opmaak instructies geïmporteerd voor alle .NET Framework typen die door een opdracht worden geretourneerd `Get-FormatData` .</span><span class="sxs-lookup"><span data-stu-id="a8bf2-251">If the command does not include either the **CommandName** or **FormatTypeName** parameter, `Import-PSSession` imports formatting instructions for all .NET Framework types returned by a `Get-FormatData` command in the remote session.</span></span>

<span data-ttu-id="a8bf2-252">Als u de para meter **FormatTypeName** gebruikt, worden er geen opdrachten geïmporteerd, tenzij u de para meter **opdrachtnaam** gebruikt.</span><span class="sxs-lookup"><span data-stu-id="a8bf2-252">If you use the **FormatTypeName** parameter, no commands are imported unless you use the **CommandName** parameter.</span></span>

<span data-ttu-id="a8bf2-253">Ook als u de para meter **opdrachtnaam** gebruikt, worden de opmaak bestanden voor de opdrachten niet geïmporteerd, tenzij u de para meter **FormatTypeName** gebruikt.</span><span class="sxs-lookup"><span data-stu-id="a8bf2-253">Similarly, if you use the **CommandName** parameter, the formatting files for the commands are not imported unless you use the **FormatTypeName** parameter.</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: 3
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="a8bf2-254">-FullyQualifiedModule</span><span class="sxs-lookup"><span data-stu-id="a8bf2-254">-FullyQualifiedModule</span></span>

<span data-ttu-id="a8bf2-255">Hiermee geeft u modules op met namen die zijn opgegeven in de vorm van **ModuleSpecification** -objecten (zoals beschreven in de sectie opmerkingen van [ModuleSpecification-constructor (hashtabel)](/dotnet/api/microsoft.powershell.commands.modulespecification.-ctor#Microsoft_PowerShell_Commands_ModuleSpecification__ctor_System_Collections_Hashtable_) in de Power shell-SDK.</span><span class="sxs-lookup"><span data-stu-id="a8bf2-255">Specifies modules with names that are specified in the form of **ModuleSpecification** objects (described in the Remarks section of [ModuleSpecification Constructor (Hashtable)](/dotnet/api/microsoft.powershell.commands.modulespecification.-ctor#Microsoft_PowerShell_Commands_ModuleSpecification__ctor_System_Collections_Hashtable_) in the PowerShell SDK.</span></span> <span data-ttu-id="a8bf2-256">De para meter **FullyQualifiedModule** accepteert bijvoorbeeld een module naam die is opgegeven in de indeling:</span><span class="sxs-lookup"><span data-stu-id="a8bf2-256">For example, the **FullyQualifiedModule** parameter accepts a module name that is specified in the format:</span></span>

- <span data-ttu-id="a8bf2-257">`@{ModuleName = "modulename"; ModuleVersion = "version_number"}` of</span><span class="sxs-lookup"><span data-stu-id="a8bf2-257">`@{ModuleName = "modulename"; ModuleVersion = "version_number"}` or</span></span>
- <span data-ttu-id="a8bf2-258">`@{ModuleName = "modulename"; ModuleVersion = "version_number"; Guid = "GUID"}`.</span><span class="sxs-lookup"><span data-stu-id="a8bf2-258">`@{ModuleName = "modulename"; ModuleVersion = "version_number"; Guid = "GUID"}`.</span></span>

<span data-ttu-id="a8bf2-259">**Module** naam en **ModuleVersion** zijn vereist, maar **GUID** is optioneel.</span><span class="sxs-lookup"><span data-stu-id="a8bf2-259">**ModuleName** and **ModuleVersion** are required, but **Guid** is optional.</span></span>

<span data-ttu-id="a8bf2-260">U kunt de para meter **FullyQualifiedModule** niet opgeven in dezelfde opdracht als een **module** parameter.</span><span class="sxs-lookup"><span data-stu-id="a8bf2-260">You cannot specify the **FullyQualifiedModule** parameter in the same command as a **Module** parameter.</span></span> <span data-ttu-id="a8bf2-261">De twee para meters sluiten elkaar wederzijds uit.</span><span class="sxs-lookup"><span data-stu-id="a8bf2-261">The two parameters are mutually exclusive.</span></span>

```yaml
Type: Microsoft.PowerShell.Commands.ModuleSpecification[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="a8bf2-262">-Module</span><span class="sxs-lookup"><span data-stu-id="a8bf2-262">-Module</span></span>

<span data-ttu-id="a8bf2-263">Hiermee wordt een matrix met opdrachten in de Windows Power shell-module en-modules opgegeven.</span><span class="sxs-lookup"><span data-stu-id="a8bf2-263">Specifies and array of commands in the Windows PowerShell snap-ins and modules.</span></span> <span data-ttu-id="a8bf2-264">Voer de module-en module namen in.</span><span class="sxs-lookup"><span data-stu-id="a8bf2-264">Enter the snap-in and module names.</span></span> <span data-ttu-id="a8bf2-265">Joker tekens zijn niet toegestaan.</span><span class="sxs-lookup"><span data-stu-id="a8bf2-265">Wildcards are not permitted.</span></span>

<span data-ttu-id="a8bf2-266">`Import-PSSession` kan geen providers importeren vanuit een module.</span><span class="sxs-lookup"><span data-stu-id="a8bf2-266">`Import-PSSession` cannot import providers from a snap-in.</span></span>

<span data-ttu-id="a8bf2-267">Zie [about_PSSnapins](/powershell/module/Microsoft.PowerShell.Core/About/about_PSSnapins) en [about_Modules](../Microsoft.PowerShell.Core/About/about_Modules.md)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="a8bf2-267">For more information, see [about_PSSnapins](/powershell/module/Microsoft.PowerShell.Core/About/about_PSSnapins) and [about_Modules](../Microsoft.PowerShell.Core/About/about_Modules.md).</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases: PSSnapin

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="a8bf2-268">-Voor voegsel</span><span class="sxs-lookup"><span data-stu-id="a8bf2-268">-Prefix</span></span>

<span data-ttu-id="a8bf2-269">Hiermee geeft u een voor voegsel op voor de zelfstandige naam woorden in de namen van geïmporteerde opdrachten.</span><span class="sxs-lookup"><span data-stu-id="a8bf2-269">Specifies a prefix to the nouns in the names of imported commands.</span></span>

<span data-ttu-id="a8bf2-270">Gebruik deze para meter om naam conflicten te voor komen die zich kunnen voordoen wanneer verschillende opdrachten in de sessie dezelfde naam hebben.</span><span class="sxs-lookup"><span data-stu-id="a8bf2-270">Use this parameter to avoid name conflicts that might occur when different commands in the session have the same name.</span></span>

<span data-ttu-id="a8bf2-271">Als u bijvoorbeeld het voor voegsel extern opgeeft en vervolgens een cmdlet importeert `Get-Date` , wordt de cmdlet bekend in de sessie als `Get-RemoteDate` en wordt deze niet verward met de oorspronkelijke `Get-Date` cmdlet.</span><span class="sxs-lookup"><span data-stu-id="a8bf2-271">For instance, if you specify the prefix Remote and then import a `Get-Date` cmdlet, the cmdlet is known in the session as `Get-RemoteDate`, and it is not confused with the original `Get-Date` cmdlet.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="a8bf2-272">-Sessie</span><span class="sxs-lookup"><span data-stu-id="a8bf2-272">-Session</span></span>

<span data-ttu-id="a8bf2-273">Hiermee geeft u de **PSSession** op van waaruit de cmdlets worden geïmporteerd.</span><span class="sxs-lookup"><span data-stu-id="a8bf2-273">Specifies the **PSSession** from which the cmdlets are imported.</span></span> <span data-ttu-id="a8bf2-274">Voer een variabele in die een sessie object bevat of een opdracht waarmee een sessie object wordt opgehaald, zoals een `New-PSSession` of- `Get-PSSession` opdracht.</span><span class="sxs-lookup"><span data-stu-id="a8bf2-274">Enter a variable that contains a session object or a command that gets a session object, such as a `New-PSSession` or `Get-PSSession` command.</span></span> <span data-ttu-id="a8bf2-275">U kunt slechts één sessie opgeven.</span><span class="sxs-lookup"><span data-stu-id="a8bf2-275">You can specify only one session.</span></span> <span data-ttu-id="a8bf2-276">Deze parameter is vereist.</span><span class="sxs-lookup"><span data-stu-id="a8bf2-276">This parameter is required.</span></span>

```yaml
Type: System.Management.Automation.Runspaces.PSSession
Parameter Sets: (All)
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="a8bf2-277">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="a8bf2-277">CommonParameters</span></span>

<span data-ttu-id="a8bf2-278">Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="a8bf2-278">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="a8bf2-279">Zie [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="a8bf2-279">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="a8bf2-280">INVOER</span><span class="sxs-lookup"><span data-stu-id="a8bf2-280">INPUTS</span></span>

### <span data-ttu-id="a8bf2-281">Geen</span><span class="sxs-lookup"><span data-stu-id="a8bf2-281">None</span></span>

<span data-ttu-id="a8bf2-282">U kunt geen objecten naar deze cmdlet pipeen.</span><span class="sxs-lookup"><span data-stu-id="a8bf2-282">You cannot pipe objects to this cmdlet.</span></span>

## <span data-ttu-id="a8bf2-283">UITVOER</span><span class="sxs-lookup"><span data-stu-id="a8bf2-283">OUTPUTS</span></span>

### <span data-ttu-id="a8bf2-284">System. Management. Automation. PSModuleInfo</span><span class="sxs-lookup"><span data-stu-id="a8bf2-284">System.Management.Automation.PSModuleInfo</span></span>

<span data-ttu-id="a8bf2-285">`Import-PSSession` retourneert hetzelfde module-object dat `New-Module` en `Get-Module` cmdlets retour neren.</span><span class="sxs-lookup"><span data-stu-id="a8bf2-285">`Import-PSSession` returns the same module object that `New-Module` and `Get-Module` cmdlets return.</span></span>
<span data-ttu-id="a8bf2-286">De geïmporteerde module is echter tijdelijk en bestaat alleen in de huidige sessie.</span><span class="sxs-lookup"><span data-stu-id="a8bf2-286">However, the imported module is temporary and exists only in the current session.</span></span> <span data-ttu-id="a8bf2-287">Als u een permanente module op schijf wilt maken, gebruikt u de `Export-PSSession` cmdlet.</span><span class="sxs-lookup"><span data-stu-id="a8bf2-287">To create a permanent module on disk, use the `Export-PSSession` cmdlet.</span></span>

## <span data-ttu-id="a8bf2-288">OPMERKINGEN</span><span class="sxs-lookup"><span data-stu-id="a8bf2-288">NOTES</span></span>

- <span data-ttu-id="a8bf2-289">`Import-PSSession` is afhankelijk van de externe infra structuur van Power shell.</span><span class="sxs-lookup"><span data-stu-id="a8bf2-289">`Import-PSSession` relies on the  PowerShell remoting infrastructure.</span></span> <span data-ttu-id="a8bf2-290">Als u deze cmdlet wilt gebruiken, moet de computer zijn geconfigureerd voor WS-Management externe communicatie.</span><span class="sxs-lookup"><span data-stu-id="a8bf2-290">To use this cmdlet, the computer must be configured for WS-Management remoting.</span></span> <span data-ttu-id="a8bf2-291">Zie [about_Remote](../Microsoft.PowerShell.Core/about/about_Remote.md) en [about_Remote_Requirements](../Microsoft.PowerShell.Core/about/about_Remote_Requirements.md)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="a8bf2-291">For more information, see [about_Remote](../Microsoft.PowerShell.Core/about/about_Remote.md) and [about_Remote_Requirements](../Microsoft.PowerShell.Core/about/about_Remote_Requirements.md).</span></span>
- <span data-ttu-id="a8bf2-292">`Import-PSSession` variabelen of Power shell-providers worden niet geïmporteerd.</span><span class="sxs-lookup"><span data-stu-id="a8bf2-292">`Import-PSSession` does not import variables or  PowerShell providers.</span></span>
- <span data-ttu-id="a8bf2-293">Wanneer u opdrachten importeert die dezelfde namen hebben als opdrachten in de huidige sessie, kunnen de geïmporteerde opdrachten aliassen, functies en cmdlets in de sessie verbergen en kunnen de functies en variabelen in de sessie worden vervangen.</span><span class="sxs-lookup"><span data-stu-id="a8bf2-293">When you import commands that have the same names as commands in the current session, the imported commands can hide aliases, functions, and cmdlets in the session and they can replace functions and variables in the session.</span></span> <span data-ttu-id="a8bf2-294">Gebruik de para meter **voor voegsel** om naam conflicten te voor komen.</span><span class="sxs-lookup"><span data-stu-id="a8bf2-294">To prevent name conflicts, use the **Prefix** parameter.</span></span> <span data-ttu-id="a8bf2-295">Zie [about_Command_Precedence](../Microsoft.PowerShell.Core/about/about_Command_Precedence.md)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="a8bf2-295">For more information, see [about_Command_Precedence](../Microsoft.PowerShell.Core/about/about_Command_Precedence.md).</span></span>
- <span data-ttu-id="a8bf2-296">`Import-PSSession` Hiermee worden alle opdrachten geconverteerd naar functies voordat deze worden geïmporteerd.</span><span class="sxs-lookup"><span data-stu-id="a8bf2-296">`Import-PSSession` converts all commands into functions before it imports them.</span></span> <span data-ttu-id="a8bf2-297">Als gevolg hiervan werken geïmporteerde opdrachten een beetje anders dan wanneer ze hun oorspronkelijke opdracht type behouden.</span><span class="sxs-lookup"><span data-stu-id="a8bf2-297">As a result, imported commands behave a bit differently than they would if they retained their original command type.</span></span> <span data-ttu-id="a8bf2-298">Als u bijvoorbeeld een cmdlet uit een PSSession importeert en vervolgens een cmdlet met dezelfde naam uit een module of module importeert, wordt de cmdlet die wordt geïmporteerd uit de PSSession altijd standaard uitgevoerd, omdat functies voor rang hebben boven cmdlets.</span><span class="sxs-lookup"><span data-stu-id="a8bf2-298">For example, if you import a cmdlet from a PSSession and then import a cmdlet with the same name from a module or snap-in, the cmdlet that is imported from the PSSession always runs by default because functions take precedence over cmdlets.</span></span> <span data-ttu-id="a8bf2-299">Als u daarentegen een alias importeert in een sessie met een alias met dezelfde naam, wordt de oorspronkelijke alias altijd gebruikt, omdat aliassen voor rang hebben op functies.</span><span class="sxs-lookup"><span data-stu-id="a8bf2-299">Conversely, if you import an alias into a session that has an alias with the same name, the original alias is always used, because aliases take precedence over functions.</span></span> <span data-ttu-id="a8bf2-300">Zie [about_Command_Precedence](../Microsoft.PowerShell.Core/about/about_Command_Precedence.md)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="a8bf2-300">For more information, see [about_Command_Precedence](../Microsoft.PowerShell.Core/about/about_Command_Precedence.md).</span></span>
- <span data-ttu-id="a8bf2-301">`Import-PSSession` gebruikt de `Write-Progress` cmdlet om de voortgang van de opdracht weer te geven.</span><span class="sxs-lookup"><span data-stu-id="a8bf2-301">`Import-PSSession` uses the `Write-Progress` cmdlet to display the progress of the command.</span></span> <span data-ttu-id="a8bf2-302">Mogelijk wordt de voortgangs balk weer geven terwijl de opdracht wordt uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="a8bf2-302">You might see the progress bar while the command is running.</span></span>
- <span data-ttu-id="a8bf2-303">Voor het zoeken naar de te importeren opdrachten `Import-PSSession` gebruikt u de `Invoke-Command` cmdlet om een opdracht uit te voeren `Get-Command` in de PSSession.</span><span class="sxs-lookup"><span data-stu-id="a8bf2-303">To find the commands to import, `Import-PSSession` uses the `Invoke-Command` cmdlet to run a `Get-Command` command in the PSSession.</span></span> <span data-ttu-id="a8bf2-304">De-cmdlet wordt gebruikt om de opmaak gegevens voor de opdrachten op te halen `Get-FormatData` .</span><span class="sxs-lookup"><span data-stu-id="a8bf2-304">To get formatting data for the commands, it uses the `Get-FormatData` cmdlet.</span></span> <span data-ttu-id="a8bf2-305">U ziet mogelijk fout berichten van deze cmdlets wanneer u een `Import-PSSession` opdracht uitvoert.</span><span class="sxs-lookup"><span data-stu-id="a8bf2-305">You might see error messages from these cmdlets when you run an `Import-PSSession` command.</span></span> <span data-ttu-id="a8bf2-306">Daarnaast `Import-PSSession` kunnen geen opdrachten worden geïmporteerd van een PSSession die geen-,-, `Get-Command` `Get-FormatData` `Select-Object` -en- `Get-Help` cmdlets bevat.</span><span class="sxs-lookup"><span data-stu-id="a8bf2-306">Also, `Import-PSSession` cannot import commands from a PSSession that does not include the `Get-Command`, `Get-FormatData`, `Select-Object`, and `Get-Help` cmdlets.</span></span>
- <span data-ttu-id="a8bf2-307">Geïmporteerde opdrachten hebben dezelfde beperkingen als andere externe opdrachten, waaronder het niet mogelijk is om een programma te starten met een gebruikers interface, zoals Klad blok.</span><span class="sxs-lookup"><span data-stu-id="a8bf2-307">Imported commands have the same limitations as other remote commands, including the inability to start a program with a user interface, such as Notepad.</span></span>
- <span data-ttu-id="a8bf2-308">Omdat Windows Power shell-profielen niet worden uitgevoerd in PSSessions, zijn de opdrachten die een profiel aan een sessie toevoegt, niet beschikbaar voor `Import-PSSession` .</span><span class="sxs-lookup"><span data-stu-id="a8bf2-308">Because Windows PowerShell profiles are not run in PSSessions, the commands that a profile adds to a session are not available to `Import-PSSession`.</span></span> <span data-ttu-id="a8bf2-309">Als u opdrachten uit een profiel wilt importeren, gebruikt u een `Invoke-Command` opdracht om het profiel hand matig uit te voeren in de PSSession voordat u opdrachten importeert.</span><span class="sxs-lookup"><span data-stu-id="a8bf2-309">To import commands from a profile, use an `Invoke-Command` command to run the profile in the PSSession manually before importing commands.</span></span>
- <span data-ttu-id="a8bf2-310">De tijdelijke module die `Import-PSSession` maakt, kan een opmaak bestand bevatten, zelfs als de opdracht geen indelings gegevens importeert.</span><span class="sxs-lookup"><span data-stu-id="a8bf2-310">The temporary module that `Import-PSSession` creates might include a formatting file, even if the command does not import formatting data.</span></span> <span data-ttu-id="a8bf2-311">Als de opdracht geen indelings gegevens importeert, bevatten indelings bestanden die worden gemaakt geen opmaak gegevens.</span><span class="sxs-lookup"><span data-stu-id="a8bf2-311">If the command does not import formatting data, any formatting files that are created will not contain formatting data.</span></span>
- <span data-ttu-id="a8bf2-312">`Import-PSSession`Het uitvoerings beleid in de huidige sessie mag niet worden beperkt of alles ondertekend, omdat de tijdelijke module die wordt gemaakt, niet- `Import-PSSession` ondertekende script bestanden bevat die niet zijn toegestaan door dit beleid.</span><span class="sxs-lookup"><span data-stu-id="a8bf2-312">To use `Import-PSSession`, the execution policy in the current session cannot be Restricted or AllSigned, because the temporary module that `Import-PSSession` creates contains unsigned script files that are prohibited by these policies.</span></span> <span data-ttu-id="a8bf2-313">Als u wilt gebruiken `Import-PSSession` zonder het uitvoerings beleid voor de lokale computer te wijzigen, gebruikt u de para meter **bereik** van `Set-ExecutionPolicy` om een minder beperkend uitvoerings beleid in te stellen voor één proces.</span><span class="sxs-lookup"><span data-stu-id="a8bf2-313">To use `Import-PSSession` without changing the execution policy for the local computer, use the **Scope** parameter of `Set-ExecutionPolicy` to set a less restrictive execution policy for a single process.</span></span>
- <span data-ttu-id="a8bf2-314">In Windows Power Shell 2,0 zijn Help-onderwerpen voor opdrachten die vanuit een andere sessie worden geïmporteerd niet het voor voegsel dat u toewijst met behulp van de para meter **prefix** .</span><span class="sxs-lookup"><span data-stu-id="a8bf2-314">In Windows PowerShell 2.0, help topics for commands that are imported from another session do not include the prefix that you assign by using the **Prefix** parameter.</span></span> <span data-ttu-id="a8bf2-315">Als u hulp nodig hebt bij een geïmporteerde opdracht in Windows Power Shell 2,0, gebruikt u de oorspronkelijke (niet-voor-vaste) opdracht naam.</span><span class="sxs-lookup"><span data-stu-id="a8bf2-315">To get help for an imported command in Windows PowerShell 2.0, use the original (non-prefixed) command name.</span></span>

## <span data-ttu-id="a8bf2-316">GERELATEERDE KOPPELINGEN</span><span class="sxs-lookup"><span data-stu-id="a8bf2-316">RELATED LINKS</span></span>

[<span data-ttu-id="a8bf2-317">Exporteren-PSSession</span><span class="sxs-lookup"><span data-stu-id="a8bf2-317">Export-PSSession</span></span>](Export-PSSession.md)
