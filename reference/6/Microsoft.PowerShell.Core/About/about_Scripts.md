---
description: Hierin wordt beschreven hoe u scripts in Power shell uitvoert en schrijft.
keywords: powershell,cmdlet
Locale: en-US
ms.date: 10/06/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_scripts?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Scripts
ms.openlocfilehash: 9b82f5c24397036e4560d3c8f84e7e403769c207
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/13/2020
ms.locfileid: "93252224"
---
# <a name="about-scripts"></a><span data-ttu-id="a4b5d-104">Over scripts</span><span class="sxs-lookup"><span data-stu-id="a4b5d-104">About Scripts</span></span>

## <a name="short-description"></a><span data-ttu-id="a4b5d-105">Korte beschrijving</span><span class="sxs-lookup"><span data-stu-id="a4b5d-105">Short description</span></span>
<span data-ttu-id="a4b5d-106">Hierin wordt beschreven hoe u scripts in Power shell uitvoert en schrijft.</span><span class="sxs-lookup"><span data-stu-id="a4b5d-106">Describes how to run and write scripts in PowerShell.</span></span>

## <a name="long-description"></a><span data-ttu-id="a4b5d-107">Lange beschrijving</span><span class="sxs-lookup"><span data-stu-id="a4b5d-107">Long description</span></span>

<span data-ttu-id="a4b5d-108">Een script is een bestand met tekst zonder opmaak dat een of meer Power shell-opdrachten bevat.</span><span class="sxs-lookup"><span data-stu-id="a4b5d-108">A script is a plain text file that contains one or more PowerShell commands.</span></span>
<span data-ttu-id="a4b5d-109">Power shell-scripts hebben een `.ps1` bestands extensie.</span><span class="sxs-lookup"><span data-stu-id="a4b5d-109">PowerShell scripts have a `.ps1` file extension.</span></span>

<span data-ttu-id="a4b5d-110">Het uitvoeren van een script is veel hetzelfde als het uitvoeren van een cmdlet.</span><span class="sxs-lookup"><span data-stu-id="a4b5d-110">Running a script is a lot like running a cmdlet.</span></span> <span data-ttu-id="a4b5d-111">U typt het pad en de bestands naam van het script en gebruikt para meters om gegevens in te dienen en opties in te stellen.</span><span class="sxs-lookup"><span data-stu-id="a4b5d-111">You type the path and file name of the script and use parameters to submit data and set options.</span></span> <span data-ttu-id="a4b5d-112">U kunt scripts uitvoeren op uw computer of in een externe sessie op een andere computer.</span><span class="sxs-lookup"><span data-stu-id="a4b5d-112">You can run scripts on your computer or in a remote session on a different computer.</span></span>

<span data-ttu-id="a4b5d-113">Als u een script schrijft, wordt een opdracht voor later gebruik opgeslagen en kunt u eenvoudig delen met anderen.</span><span class="sxs-lookup"><span data-stu-id="a4b5d-113">Writing a script saves a command for later use and makes it easy to share with others.</span></span> <span data-ttu-id="a4b5d-114">Het belangrijkste is dat u de opdrachten kunt uitvoeren door simpelweg het pad naar het script en de bestands naam op te geven.</span><span class="sxs-lookup"><span data-stu-id="a4b5d-114">Most importantly, it lets you run the commands simply by typing the script path and the filename.</span></span> <span data-ttu-id="a4b5d-115">Scripts kunnen zo eenvoudig zijn als één opdracht in een bestand of zo uitgebreid als een complex programma.</span><span class="sxs-lookup"><span data-stu-id="a4b5d-115">Scripts can be as simple as a single command in a file or as extensive as a complex program.</span></span>

<span data-ttu-id="a4b5d-116">Scripts hebben extra functies, zoals de `#Requires` speciale opmerking, het gebruik van para meters, ondersteuning voor gegevens secties en digitale hand tekeningen voor beveiliging.</span><span class="sxs-lookup"><span data-stu-id="a4b5d-116">Scripts have additional features, such as the `#Requires` special comment, the use of parameters, support for data sections, and digital signing for security.</span></span>
<span data-ttu-id="a4b5d-117">U kunt ook Help-onderwerpen voor scripts en voor alle functies in het script schrijven.</span><span class="sxs-lookup"><span data-stu-id="a4b5d-117">You can also write Help topics for scripts and for any functions in the script.</span></span>

## <a name="how-to-run-a-script"></a><span data-ttu-id="a4b5d-118">Een script uitvoeren</span><span class="sxs-lookup"><span data-stu-id="a4b5d-118">How to run a script</span></span>

<span data-ttu-id="a4b5d-119">Voordat u een script kunt uitvoeren in Windows, moet u het standaard beleid voor Power shell-uitvoering wijzigen.</span><span class="sxs-lookup"><span data-stu-id="a4b5d-119">Before you can run a script on Windows, you need to change the default PowerShell execution policy.</span></span> <span data-ttu-id="a4b5d-120">Uitvoerings beleid is niet van toepassing op Power shell die wordt uitgevoerd op niet-Windows-platforms.</span><span class="sxs-lookup"><span data-stu-id="a4b5d-120">Execution policy does not apply to PowerShell running on non-Windows platforms.</span></span>

<span data-ttu-id="a4b5d-121">Het standaard uitvoerings beleid, `Restricted` , voor komt dat alle scripts worden uitgevoerd, met inbegrip van scripts die u op de lokale computer schrijft.</span><span class="sxs-lookup"><span data-stu-id="a4b5d-121">The default execution policy, `Restricted`, prevents all scripts from running, including scripts that you write on the local computer.</span></span> <span data-ttu-id="a4b5d-122">Zie [about_Execution_Policies](about_Execution_Policies.md)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="a4b5d-122">For more information, see [about_Execution_Policies](about_Execution_Policies.md).</span></span>

<span data-ttu-id="a4b5d-123">Het uitvoerings beleid wordt opgeslagen in het REGI ster, dus u hoeft dit slechts één keer op elke computer te wijzigen.</span><span class="sxs-lookup"><span data-stu-id="a4b5d-123">The execution policy is saved in the registry, so you need to change it only once on each computer.</span></span>

<span data-ttu-id="a4b5d-124">Gebruik de volgende procedure om het uitvoerings beleid te wijzigen.</span><span class="sxs-lookup"><span data-stu-id="a4b5d-124">To change the execution policy, use the following procedure.</span></span>

<span data-ttu-id="a4b5d-125">Typ in de opdrachtprompt:</span><span class="sxs-lookup"><span data-stu-id="a4b5d-125">At the command prompt, type:</span></span>

```powershell
Set-ExecutionPolicy AllSigned
```

<span data-ttu-id="a4b5d-126">of</span><span class="sxs-lookup"><span data-stu-id="a4b5d-126">or</span></span>

```powershell
Set-ExecutionPolicy RemoteSigned
```

<span data-ttu-id="a4b5d-127">De wijziging is direct van kracht.</span><span class="sxs-lookup"><span data-stu-id="a4b5d-127">The change is effective immediately.</span></span>

<span data-ttu-id="a4b5d-128">Als u een script wilt uitvoeren, typt u de volledige naam en het volledige pad naar het script bestand.</span><span class="sxs-lookup"><span data-stu-id="a4b5d-128">To run a script, type the full name and the full path to the script file.</span></span>

<span data-ttu-id="a4b5d-129">Als u bijvoorbeeld het Get-ServiceLog.ps1 script wilt uitvoeren in de map C:\Scripts, typt u:</span><span class="sxs-lookup"><span data-stu-id="a4b5d-129">For example, to run the Get-ServiceLog.ps1 script in the C:\Scripts directory, type:</span></span>

```powershell
C:\Scripts\Get-ServiceLog.ps1
```

<span data-ttu-id="a4b5d-130">Als u een script wilt uitvoeren in de huidige map, typt u het pad naar de huidige map of gebruikt u een punt om de huidige map weer te geven, gevolgd door een pad naar een back slash ( `.\` ).</span><span class="sxs-lookup"><span data-stu-id="a4b5d-130">To run a script in the current directory, type the path to the current directory, or use a dot to represent the current directory, followed by a path backslash (`.\`).</span></span>

<span data-ttu-id="a4b5d-131">Als u bijvoorbeeld het ServicesLog.ps1 script wilt uitvoeren in de lokale map, typt u:</span><span class="sxs-lookup"><span data-stu-id="a4b5d-131">For example, to run the ServicesLog.ps1 script in the local directory, type:</span></span>

```powershell
.\Get-ServiceLog.ps1
```

<span data-ttu-id="a4b5d-132">Als het script para meters heeft, typt u de para meters en parameter waarden na de script bestandsnaam.</span><span class="sxs-lookup"><span data-stu-id="a4b5d-132">If the script has parameters, type the parameters and parameter values after the script filename.</span></span>

<span data-ttu-id="a4b5d-133">De volgende opdracht gebruikt bijvoorbeeld de para meter ServiceName van het Get-ServiceLog script om een logboek van de WinRM-service activiteit aan te vragen.</span><span class="sxs-lookup"><span data-stu-id="a4b5d-133">For example, the following command uses the ServiceName parameter of the Get-ServiceLog script to request a log of WinRM service activity.</span></span>

```powershell
.\Get-ServiceLog.ps1 -ServiceName WinRM
```

<span data-ttu-id="a4b5d-134">Als beveiligings functie voert Power shell geen scripts uit wanneer u dubbelklikt op het script pictogram in Verkenner of wanneer u de script naam typt zonder een volledig pad, zelfs wanneer het script zich in de huidige map bevindt.</span><span class="sxs-lookup"><span data-stu-id="a4b5d-134">As a security feature, PowerShell does not run scripts when you double-click the script icon in File Explorer or when you type the script name without a full path, even when the script is in the current directory.</span></span> <span data-ttu-id="a4b5d-135">Zie [about_Command_Precedence](about_Command_Precedence.md)voor meer informatie over het uitvoeren van opdrachten en scripts in Power shell.</span><span class="sxs-lookup"><span data-stu-id="a4b5d-135">For more information about running commands and scripts in PowerShell, see [about_Command_Precedence](about_Command_Precedence.md).</span></span>

### <a name="run-with-powershell"></a><span data-ttu-id="a4b5d-136">Uitvoeren met Power shell</span><span class="sxs-lookup"><span data-stu-id="a4b5d-136">Run with PowerShell</span></span>

<span data-ttu-id="a4b5d-137">Vanaf Power Shell 3,0 kunt u scripts uitvoeren vanuit Verkenner.</span><span class="sxs-lookup"><span data-stu-id="a4b5d-137">Beginning in PowerShell 3.0, you can run scripts from File Explorer.</span></span>

<span data-ttu-id="a4b5d-138">De functie ' uitvoeren met Power shell ' gebruiken:</span><span class="sxs-lookup"><span data-stu-id="a4b5d-138">To use the "Run with PowerShell" feature:</span></span>

<span data-ttu-id="a4b5d-139">Voer de Verkenner uit, klik met de rechter muisknop op het script bestands naam en selecteer uitvoeren met Power shell.</span><span class="sxs-lookup"><span data-stu-id="a4b5d-139">Run File Explorer, right-click the script filename and then select "Run with PowerShell".</span></span>

<span data-ttu-id="a4b5d-140">De functie ' uitvoeren met Power shell ' is ontworpen voor het uitvoeren van scripts waarvoor geen vereiste para meters zijn en die geen uitvoer retour neren naar de opdracht prompt.</span><span class="sxs-lookup"><span data-stu-id="a4b5d-140">The "Run with PowerShell" feature is designed to run scripts that do not have required parameters and do not return output to the command prompt.</span></span>

<span data-ttu-id="a4b5d-141">Zie [about_Run_With_PowerShell](about_Run_With_PowerShell.md)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="a4b5d-141">For more information, see [about_Run_With_PowerShell](about_Run_With_PowerShell.md).</span></span>

### <a name="running-scripts-on-other-computers"></a><span data-ttu-id="a4b5d-142">Scripts uitvoeren op andere computers</span><span class="sxs-lookup"><span data-stu-id="a4b5d-142">Running scripts on other computers</span></span>

<span data-ttu-id="a4b5d-143">Als u een script wilt uitvoeren op een of meer externe computers, gebruikt u de para meter **filepath** van de `Invoke-Command` cmdlet.</span><span class="sxs-lookup"><span data-stu-id="a4b5d-143">To run a script on one or more remote computers, use the **FilePath** parameter of the `Invoke-Command` cmdlet.</span></span>

<span data-ttu-id="a4b5d-144">Voer het pad en de bestands naam van het script in als de waarde van de **filepath** -para meter.</span><span class="sxs-lookup"><span data-stu-id="a4b5d-144">Enter the path and filename of the script as the value of the **FilePath** parameter.</span></span> <span data-ttu-id="a4b5d-145">Het script moet zich bevinden op de lokale computer of in een map waartoe de lokale computer toegang heeft.</span><span class="sxs-lookup"><span data-stu-id="a4b5d-145">The script must reside on the local computer or in a directory that the local computer can access.</span></span>

<span data-ttu-id="a4b5d-146">Met de volgende opdracht wordt het `Get-ServiceLog.ps1` script uitgevoerd op de externe computers met de naam Server01 en Server02.</span><span class="sxs-lookup"><span data-stu-id="a4b5d-146">The following command runs the `Get-ServiceLog.ps1` script on the remote computers named Server01 and Server02.</span></span>

```powershell
Invoke-Command -ComputerName Server01,Server02 -FilePath `
  C:\Scripts\Get-ServiceLog.ps1
```

## <a name="get-help-for-scripts"></a><span data-ttu-id="a4b5d-147">Hulp vragen voor scripts</span><span class="sxs-lookup"><span data-stu-id="a4b5d-147">Get help for scripts</span></span>

<span data-ttu-id="a4b5d-148">Met de cmdlet Get-Help worden de Help-onderwerpen voor scripts en voor cmdlets en andere typen opdrachten opgehaald.</span><span class="sxs-lookup"><span data-stu-id="a4b5d-148">The Get-Help cmdlet gets the help topics for scripts as well as for cmdlets and other types of commands.</span></span> <span data-ttu-id="a4b5d-149">Als u het Help-onderwerp voor een script wilt ophalen, typt u `Get-Help` gevolgd door het pad en de bestands naam van het script.</span><span class="sxs-lookup"><span data-stu-id="a4b5d-149">To get the help topic for a script, type `Get-Help` followed by the path and filename of the script.</span></span> <span data-ttu-id="a4b5d-150">Als het scriptpad zich in uw `Path` omgevings variabele bevindt, kunt u het pad weglaten.</span><span class="sxs-lookup"><span data-stu-id="a4b5d-150">If the script path is in your `Path` environment variable, you can omit the path.</span></span>

<span data-ttu-id="a4b5d-151">Als u bijvoorbeeld hulp wilt krijgen voor het ServicesLog.ps1 script, typt u:</span><span class="sxs-lookup"><span data-stu-id="a4b5d-151">For example, to get help for the ServicesLog.ps1 script, type:</span></span>

```powershell
get-help C:\admin\scripts\ServicesLog.ps1
```

## <a name="how-to-write-a-script"></a><span data-ttu-id="a4b5d-152">Een script schrijven</span><span class="sxs-lookup"><span data-stu-id="a4b5d-152">How to write a script</span></span>

<span data-ttu-id="a4b5d-153">Een script kan een wille keurige geldige Power shell-opdracht bevatten, waaronder afzonderlijke opdrachten, opdrachten die gebruikmaken van de pijp lijn, functies en besturings structuren zoals if-instructies en for-lussen.</span><span class="sxs-lookup"><span data-stu-id="a4b5d-153">A script can contain any valid PowerShell commands, including single commands, commands that use the pipeline, functions, and control structures such as If statements and For loops.</span></span>

<span data-ttu-id="a4b5d-154">Als u een script wilt schrijven, opent u een nieuw bestand in een tekst editor, typt u de opdrachten en slaat u deze op in een bestand met een geldige bestands naam met de `.ps1` bestands extensie.</span><span class="sxs-lookup"><span data-stu-id="a4b5d-154">To write a script, open a new file in a text editor, type the commands, and save them in a file with a valid filename with the `.ps1` file extension.</span></span>

<span data-ttu-id="a4b5d-155">Het volgende voor beeld is een eenvoudig script waarmee de services worden opgehaald die worden uitgevoerd op het huidige systeem en worden opgeslagen in een logboek bestand.</span><span class="sxs-lookup"><span data-stu-id="a4b5d-155">The following example is a simple script that gets the services that are running on the current system and saves them to a log file.</span></span> <span data-ttu-id="a4b5d-156">De naam van het logboek bestand wordt gemaakt op basis van de huidige datum.</span><span class="sxs-lookup"><span data-stu-id="a4b5d-156">The log filename is created from the current date.</span></span>

```powershell
$date = (get-date).dayofyear
get-service | out-file "$date.log"
```

<span data-ttu-id="a4b5d-157">Als u dit script wilt maken, opent u een tekst editor of een script editor, typt u deze opdrachten en slaat u deze op in een bestand met de naam `ServiceLog.ps1` .</span><span class="sxs-lookup"><span data-stu-id="a4b5d-157">To create this script, open a text editor or a script editor, type these commands, and then save them in a file named `ServiceLog.ps1`.</span></span>

### <a name="parameters-in-scripts"></a><span data-ttu-id="a4b5d-158">Para meters in scripts</span><span class="sxs-lookup"><span data-stu-id="a4b5d-158">Parameters in scripts</span></span>

<span data-ttu-id="a4b5d-159">Als u para meters wilt definiëren in een script, gebruikt u een parameter instructie.</span><span class="sxs-lookup"><span data-stu-id="a4b5d-159">To define parameters in a script, use a Param statement.</span></span> <span data-ttu-id="a4b5d-160">De `Param` instructie moet de eerste instructie in een script zijn, met uitzonde ring van opmerkingen en `#Require` instructies.</span><span class="sxs-lookup"><span data-stu-id="a4b5d-160">The `Param` statement must be the first statement in a script, except for comments and any `#Require` statements.</span></span>

<span data-ttu-id="a4b5d-161">Script parameters werken als functie parameters.</span><span class="sxs-lookup"><span data-stu-id="a4b5d-161">Script parameters work like function parameters.</span></span> <span data-ttu-id="a4b5d-162">De parameter waarden zijn beschikbaar voor alle opdrachten in het script.</span><span class="sxs-lookup"><span data-stu-id="a4b5d-162">The parameter values are available to all of the commands in the script.</span></span> <span data-ttu-id="a4b5d-163">Alle functies van functie parameters, met inbegrip van het parameter kenmerk en de benoemde argumenten, zijn ook geldig in scripts.</span><span class="sxs-lookup"><span data-stu-id="a4b5d-163">All of the features of function parameters, including the Parameter attribute and its named arguments, are also valid in scripts.</span></span>

<span data-ttu-id="a4b5d-164">Wanneer het script wordt uitgevoerd, typen script gebruikers de para meters na de script naam.</span><span class="sxs-lookup"><span data-stu-id="a4b5d-164">When running the script, script users type the parameters after the script name.</span></span>

<span data-ttu-id="a4b5d-165">In het volgende voor beeld ziet u een `Test-Remote.ps1` script met de para meter **ComputerName** .</span><span class="sxs-lookup"><span data-stu-id="a4b5d-165">The following example shows a `Test-Remote.ps1` script that has a **ComputerName** parameter.</span></span> <span data-ttu-id="a4b5d-166">Beide script functies hebben toegang tot de waarde van de para meter **ComputerName** .</span><span class="sxs-lookup"><span data-stu-id="a4b5d-166">Both of the script functions can access the **ComputerName** parameter value.</span></span>

```powershell
param ($ComputerName = $(throw "ComputerName parameter is required."))

function CanPing {
   $error.clear()
   $tmp = test-connection $computername -erroraction SilentlyContinue

   if (!$?)
       {write-host "Ping failed: $ComputerName."; return $false}
   else
       {write-host "Ping succeeded: $ComputerName"; return $true}
}

function CanRemote {
    $s = new-pssession $computername -erroraction SilentlyContinue

    if ($s -is [System.Management.Automation.Runspaces.PSSession])
        {write-host "Remote test succeeded: $ComputerName."}
    else
        {write-host "Remote test failed: $ComputerName."}
}

if (CanPing $computername) {CanRemote $computername}
```

<span data-ttu-id="a4b5d-167">Als u dit script wilt uitvoeren, typt u de parameter naam achter de script naam.</span><span class="sxs-lookup"><span data-stu-id="a4b5d-167">To run this script, type the parameter name after the script name.</span></span> <span data-ttu-id="a4b5d-168">Bijvoorbeeld:</span><span class="sxs-lookup"><span data-stu-id="a4b5d-168">For example:</span></span>

```powershell
C:\PS> .\test-remote.ps1 -computername Server01

Ping succeeded: Server01
Remote test failed: Server01
```

<span data-ttu-id="a4b5d-169">Zie [about_Functions](about_Functions.md) en [about_Functions_Advanced_Parameters](about_Functions_Advanced_Parameters.md)voor meer informatie over de parameter instructie en de functie parameters.</span><span class="sxs-lookup"><span data-stu-id="a4b5d-169">For more information about the Param statement and the function parameters, see [about_Functions](about_Functions.md) and [about_Functions_Advanced_Parameters](about_Functions_Advanced_Parameters.md).</span></span>

### <a name="writing-help-for-scripts"></a><span data-ttu-id="a4b5d-170">Help voor scripts schrijven</span><span class="sxs-lookup"><span data-stu-id="a4b5d-170">Writing help for scripts</span></span>

<span data-ttu-id="a4b5d-171">U kunt een Help-onderwerp voor een script schrijven met behulp van een van de volgende twee methoden:</span><span class="sxs-lookup"><span data-stu-id="a4b5d-171">You can write a help topic for a script by using either of the two following methods:</span></span>

- <span data-ttu-id="a4b5d-172">Help voor scripts Comment-Based</span><span class="sxs-lookup"><span data-stu-id="a4b5d-172">Comment-Based Help for Scripts</span></span>

  <span data-ttu-id="a4b5d-173">Maak een Help-onderwerp met behulp van speciale tref woorden in de opmerkingen.</span><span class="sxs-lookup"><span data-stu-id="a4b5d-173">Create a Help topic by using special keywords in the comments.</span></span> <span data-ttu-id="a4b5d-174">Als u op opmerkingen gebaseerde hulp voor een script wilt maken, moeten de opmerkingen aan het begin of einde van het script bestand worden geplaatst.</span><span class="sxs-lookup"><span data-stu-id="a4b5d-174">To create comment-based Help for a script, the comments must be placed at the beginning or end of the script file.</span></span> <span data-ttu-id="a4b5d-175">Zie [about_Comment_Based_Help](about_Comment_Based_Help.md)voor meer informatie over op opmerkingen gebaseerde Help.</span><span class="sxs-lookup"><span data-stu-id="a4b5d-175">For more information about comment-based Help, see [about_Comment_Based_Help](about_Comment_Based_Help.md).</span></span>

- <span data-ttu-id="a4b5d-176">Help voor scripts XML-Based</span><span class="sxs-lookup"><span data-stu-id="a4b5d-176">XML-Based Help  for Scripts</span></span>

  <span data-ttu-id="a4b5d-177">Maak een Help-onderwerp op basis van XML, zoals het type dat doorgaans voor cmdlets wordt gemaakt.</span><span class="sxs-lookup"><span data-stu-id="a4b5d-177">Create an XML-based Help topic, such as the type that is typically created for cmdlets.</span></span> <span data-ttu-id="a4b5d-178">Help op basis van XML is vereist als u Help-onderwerpen in meerdere talen vertaalt.</span><span class="sxs-lookup"><span data-stu-id="a4b5d-178">XML-based Help is required if you are translating Help topics into multiple languages.</span></span>

<span data-ttu-id="a4b5d-179">Als u het script wilt koppelen aan het Help-onderwerp op basis van XML, gebruikt u de. ExternalHelp Help opmerking over tref woord.</span><span class="sxs-lookup"><span data-stu-id="a4b5d-179">To associate the script with the XML-based Help topic, use the .ExternalHelp Help comment keyword.</span></span> <span data-ttu-id="a4b5d-180">Zie [about_Comment_Based_Help](about_Comment_Based_Help.md)voor meer informatie over het sleutel woord ExternalHelp.</span><span class="sxs-lookup"><span data-stu-id="a4b5d-180">For more information about the ExternalHelp keyword, see [about_Comment_Based_Help](about_Comment_Based_Help.md).</span></span> <span data-ttu-id="a4b5d-181">Zie [instructies voor het schrijven van cmdlets](/powershell/scripting/developer/help/writing-help-for-windows-powershell-cmdlets)voor meer informatie over Help op basis van XML.</span><span class="sxs-lookup"><span data-stu-id="a4b5d-181">For more information about XML-based help, see [How to Write Cmdlet Help](/powershell/scripting/developer/help/writing-help-for-windows-powershell-cmdlets).</span></span>

### <a name="returning-an-exit-value"></a><span data-ttu-id="a4b5d-182">Een eind waarde Retour neren</span><span class="sxs-lookup"><span data-stu-id="a4b5d-182">Returning an exit value</span></span>

<span data-ttu-id="a4b5d-183">Scripts retour neren standaard geen afsluit status wanneer het script eindigt.</span><span class="sxs-lookup"><span data-stu-id="a4b5d-183">By default, scripts do not return an exit status when the script ends.</span></span> <span data-ttu-id="a4b5d-184">U moet de `exit` instructie gebruiken om een afsluit code uit een script te retour neren.</span><span class="sxs-lookup"><span data-stu-id="a4b5d-184">You must use the `exit` statement to return an exit code from a script.</span></span> <span data-ttu-id="a4b5d-185">De `exit` instructie retourneert standaard `0` .</span><span class="sxs-lookup"><span data-stu-id="a4b5d-185">By default, the `exit` statement returns `0`.</span></span> <span data-ttu-id="a4b5d-186">U kunt een numerieke waarde opgeven om een andere afsluit status te retour neren.</span><span class="sxs-lookup"><span data-stu-id="a4b5d-186">You can provide a numeric value to return a different exit status.</span></span> <span data-ttu-id="a4b5d-187">Een afsluit code die niet gelijk is aan nul, geeft meestal een fout aan.</span><span class="sxs-lookup"><span data-stu-id="a4b5d-187">A nonzero exit code typically signals a failure.</span></span>

<span data-ttu-id="a4b5d-188">In Windows is een wille keurig getal tussen `[int]::MinValue` en `[int]::MaxValue` toegestaan.</span><span class="sxs-lookup"><span data-stu-id="a4b5d-188">On Windows, any number between `[int]::MinValue` and `[int]::MaxValue` is allowed.</span></span>

<span data-ttu-id="a4b5d-189">Op UNIX zijn alleen positieve getallen tussen `[byte]::MinValue` (0) en `[byte]::MaxValue` (255) toegestaan.</span><span class="sxs-lookup"><span data-stu-id="a4b5d-189">On Unix, only positive numbers between `[byte]::MinValue` (0) and `[byte]::MaxValue` (255) are allowed.</span></span> <span data-ttu-id="a4b5d-190">Een negatief getal in het bereik `-1` tot en met `-255` wordt automatisch omgezet in een positief getal door het toe te voegen</span><span class="sxs-lookup"><span data-stu-id="a4b5d-190">A negative number in the range of `-1` through `-255` is automatically translated into a positive number by adding</span></span>
256. <span data-ttu-id="a4b5d-191">Bijvoorbeeld, `-2` wordt omgezet naar `254` .</span><span class="sxs-lookup"><span data-stu-id="a4b5d-191">For example, `-2` is transformed to `254`.</span></span>

<span data-ttu-id="a4b5d-192">In Power shell `exit` stelt de instructie de waarde van de `$LASTEXITCODE` variabele in.</span><span class="sxs-lookup"><span data-stu-id="a4b5d-192">In PowerShell, the `exit` statement sets the value of the `$LASTEXITCODE` variable.</span></span> <span data-ttu-id="a4b5d-193">In de Windows-opdracht shell (cmd.exe) wordt met de instructie Exit de waarde van de `%ERRORLEVEL%` omgevings variabele ingesteld.</span><span class="sxs-lookup"><span data-stu-id="a4b5d-193">In the Windows Command Shell (cmd.exe), the exit statement sets the value of the `%ERRORLEVEL%` environment variable.</span></span>

<span data-ttu-id="a4b5d-194">Elk argument dat niet-numeriek of buiten het platformspecifieke bereik valt, wordt vertaald naar de waarde van `0` .</span><span class="sxs-lookup"><span data-stu-id="a4b5d-194">Any argument that is non-numeric or outside the platform-specific range is translated to the value of `0`.</span></span>

## <a name="script-scope-and-dot-sourcing"></a><span data-ttu-id="a4b5d-195">Script bereik en punt sourcing</span><span class="sxs-lookup"><span data-stu-id="a4b5d-195">Script scope and dot sourcing</span></span>

<span data-ttu-id="a4b5d-196">Elk script wordt uitgevoerd in een eigen bereik.</span><span class="sxs-lookup"><span data-stu-id="a4b5d-196">Each script runs in its own scope.</span></span> <span data-ttu-id="a4b5d-197">De functies, variabelen, aliassen en stations die in het script zijn gemaakt, bestaan alleen in het script bereik.</span><span class="sxs-lookup"><span data-stu-id="a4b5d-197">The functions, variables, aliases, and drives that are created in the script exist only in the script scope.</span></span> <span data-ttu-id="a4b5d-198">U hebt geen toegang tot deze items of de waarden daarvan in het bereik waarin het script wordt uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="a4b5d-198">You cannot access these items or their values in the scope in which the script runs.</span></span>

<span data-ttu-id="a4b5d-199">Als u een script wilt uitvoeren in een ander bereik, kunt u een bereik opgeven, zoals globaal of lokaal, of u kunt het script een punt bron geven.</span><span class="sxs-lookup"><span data-stu-id="a4b5d-199">To run a script in a different scope, you can specify a scope, such as Global or Local, or you can dot source the script.</span></span>

<span data-ttu-id="a4b5d-200">Met de functie dot sourcing kunt u een script uitvoeren in het huidige bereik in plaats van in het script bereik.</span><span class="sxs-lookup"><span data-stu-id="a4b5d-200">The dot sourcing feature lets you run a script in the current scope instead of in the script scope.</span></span> <span data-ttu-id="a4b5d-201">Wanneer u een script uitvoert dat een dot-bron heeft, worden de opdrachten in het script uitgevoerd alsof u deze hebt getypt bij de opdracht prompt.</span><span class="sxs-lookup"><span data-stu-id="a4b5d-201">When you run a script that is dot sourced, the commands in the script run as though you had typed them at the command prompt.</span></span> <span data-ttu-id="a4b5d-202">De functies, variabelen, aliassen en stations die het script maakt, worden gemaakt in het bereik waarin u werkt.</span><span class="sxs-lookup"><span data-stu-id="a4b5d-202">The functions, variables, aliases, and drives that the script creates are created in the scope in which you are working.</span></span> <span data-ttu-id="a4b5d-203">Nadat het script is uitgevoerd, kunt u de gemaakte items gebruiken en toegang krijgen tot hun waarden in uw sessie.</span><span class="sxs-lookup"><span data-stu-id="a4b5d-203">After the script runs, you can use the created items and access their values in your session.</span></span>

<span data-ttu-id="a4b5d-204">Als u een script wilt maken van een punt, typt u een punt (.) en een spatie vóór het scriptpad.</span><span class="sxs-lookup"><span data-stu-id="a4b5d-204">To dot source a script, type a dot (.) and a space before the script path.</span></span>

<span data-ttu-id="a4b5d-205">Bijvoorbeeld:</span><span class="sxs-lookup"><span data-stu-id="a4b5d-205">For example:</span></span>

```powershell
. C:\scripts\UtilityFunctions.ps1
```

<span data-ttu-id="a4b5d-206">of</span><span class="sxs-lookup"><span data-stu-id="a4b5d-206">or</span></span>

```powershell
. .\UtilityFunctions.ps1
```

<span data-ttu-id="a4b5d-207">Nadat het `UtilityFunctions.ps1` script is uitgevoerd, worden de functies en variabelen die het script maakt, toegevoegd aan het huidige bereik.</span><span class="sxs-lookup"><span data-stu-id="a4b5d-207">After the `UtilityFunctions.ps1` script runs, the functions and variables that the script creates are added to the current scope.</span></span>

<span data-ttu-id="a4b5d-208">Het `UtilityFunctions.ps1` script maakt bijvoorbeeld de `New-Profile` functie en de `$ProfileName` variabele.</span><span class="sxs-lookup"><span data-stu-id="a4b5d-208">For example, the `UtilityFunctions.ps1` script creates the `New-Profile` function and the `$ProfileName` variable.</span></span>

```powershell
#In UtilityFunctions.ps1

function New-Profile
{
  Write-Host "Running New-Profile function"
  $profileName = split-path $profile -leaf

  if (test-path $profile)
    {write-error "Profile $profileName already exists on this computer."}
  else
    {new-item -type file -path $profile -force }
}
```

<span data-ttu-id="a4b5d-209">Als u het `UtilityFunctions.ps1` script uitvoert in een eigen script bereik, `New-Profile` bestaan de functie en de `$ProfileName` variabele alleen tijdens het uitvoeren van het script.</span><span class="sxs-lookup"><span data-stu-id="a4b5d-209">If you run the `UtilityFunctions.ps1` script in its own script scope, the `New-Profile` function and the `$ProfileName` variable exist only while the script is running.</span></span> <span data-ttu-id="a4b5d-210">Wanneer het script wordt afgesloten, worden de functie en de variabele verwijderd, zoals in het volgende voor beeld wordt weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="a4b5d-210">When the script exits, the function and variable are removed, as shown in the following example.</span></span>

```powershell
C:\PS> .\UtilityFunctions.ps1

C:\PS> New-Profile
The term 'new-profile' is not recognized as a cmdlet, function, operable
program, or script file. Verify the term and try again.
At line:1 char:12
+ new-profile <<<<
   + CategoryInfo          : ObjectNotFound: (new-profile:String) [],
   + FullyQualifiedErrorId : CommandNotFoundException

C:\PS> $profileName
C:\PS>
```

<span data-ttu-id="a4b5d-211">Wanneer u het script naar een punt bron en uitvoert, maakt het script de `New-Profile` functie en de `$ProfileName` variabele in uw sessie in uw bereik.</span><span class="sxs-lookup"><span data-stu-id="a4b5d-211">When you dot source the script and run it, the script creates the `New-Profile` function and the `$ProfileName` variable in your session in your scope.</span></span> <span data-ttu-id="a4b5d-212">Nadat het script is uitgevoerd, kunt u de `New-Profile` functie gebruiken in uw sessie, zoals wordt weer gegeven in het volgende voor beeld.</span><span class="sxs-lookup"><span data-stu-id="a4b5d-212">After the script runs, you can use the `New-Profile` function in your session, as shown in the following example.</span></span>

```powershell
C:\PS> . .\UtilityFunctions.ps1

C:\PS> New-Profile

    Directory: C:\Users\juneb\Documents\WindowsPowerShell

    Mode    LastWriteTime     Length Name
    ----    -------------     ------ ----
    -a---   1/14/2009 3:08 PM      0 Microsoft.PowerShellISE_profile.ps1

C:\PS> $profileName
Microsoft.PowerShellISE_profile.ps1
```

<span data-ttu-id="a4b5d-213">Zie about_Scopes voor meer informatie over het bereik.</span><span class="sxs-lookup"><span data-stu-id="a4b5d-213">For more information about scope, see about_Scopes.</span></span>

## <a name="scripts-in-modules"></a><span data-ttu-id="a4b5d-214">Scripts in modules</span><span class="sxs-lookup"><span data-stu-id="a4b5d-214">Scripts in modules</span></span>

<span data-ttu-id="a4b5d-215">Een module is een set gerelateerde Power shell-resources die kunnen worden gedistribueerd als een eenheid.</span><span class="sxs-lookup"><span data-stu-id="a4b5d-215">A module is a set of related PowerShell resources that can be distributed as a unit.</span></span> <span data-ttu-id="a4b5d-216">U kunt modules gebruiken om uw scripts, functies en andere resources te organiseren.</span><span class="sxs-lookup"><span data-stu-id="a4b5d-216">You can use modules to organize your scripts, functions, and other resources.</span></span> <span data-ttu-id="a4b5d-217">U kunt ook modules gebruiken om uw code naar anderen te distribueren en om code op te halen uit betrouw bare bronnen.</span><span class="sxs-lookup"><span data-stu-id="a4b5d-217">You can also use modules to distribute your code to others, and to get code from trusted sources.</span></span>

<span data-ttu-id="a4b5d-218">U kunt scripts in uw modules insluiten of u kunt een script module maken. Dit is een module die geheel of voornamelijk uit een script en ondersteunende bronnen bestaat.</span><span class="sxs-lookup"><span data-stu-id="a4b5d-218">You can include scripts in your modules, or you can create a script module, which is a module that consists entirely or primarily of a script and supporting resources.</span></span> <span data-ttu-id="a4b5d-219">Een script module is slechts een script met de bestands extensie. psm1.</span><span class="sxs-lookup"><span data-stu-id="a4b5d-219">A script module is just a script with a .psm1 file extension.</span></span>

<span data-ttu-id="a4b5d-220">Zie [about_Modules](about_Modules.md)voor meer informatie over modules.</span><span class="sxs-lookup"><span data-stu-id="a4b5d-220">For more information about modules, see [about_Modules](about_Modules.md).</span></span>

## <a name="other-script-features"></a><span data-ttu-id="a4b5d-221">Andere script functies</span><span class="sxs-lookup"><span data-stu-id="a4b5d-221">Other script features</span></span>

<span data-ttu-id="a4b5d-222">Power Shell heeft veel nuttige functies die u in scripts kunt gebruiken.</span><span class="sxs-lookup"><span data-stu-id="a4b5d-222">PowerShell has many useful features that you can use in scripts.</span></span>

- <span data-ttu-id="a4b5d-223">`#Requires` -U kunt een `#Requires` instructie gebruiken om te voor komen dat een script wordt uitgevoerd zonder opgegeven modules of modules en een opgegeven versie van Power shell.</span><span class="sxs-lookup"><span data-stu-id="a4b5d-223">`#Requires` - You can use a `#Requires` statement to prevent a script from running without specified modules or snap-ins and a specified version of PowerShell.</span></span> <span data-ttu-id="a4b5d-224">Zie about_Requires voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="a4b5d-224">For more information, see about_Requires.</span></span>

- <span data-ttu-id="a4b5d-225">`$PSCommandPath` -Bevat het volledige pad en de naam van het script dat wordt uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="a4b5d-225">`$PSCommandPath` - Contains the full path and name of the script that is being run.</span></span> <span data-ttu-id="a4b5d-226">Deze para meter is geldig in alle scripts.</span><span class="sxs-lookup"><span data-stu-id="a4b5d-226">This parameter is valid in all scripts.</span></span> <span data-ttu-id="a4b5d-227">Deze automatische variabele wordt geïntroduceerd in Power Shell 3,0.</span><span class="sxs-lookup"><span data-stu-id="a4b5d-227">This automatic variable is introduced in PowerShell 3.0.</span></span>

- <span data-ttu-id="a4b5d-228">`$PSScriptRoot` -Bevat de map van waaruit een script wordt uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="a4b5d-228">`$PSScriptRoot` - Contains the directory from which a script is being run.</span></span> <span data-ttu-id="a4b5d-229">In Power Shell 2,0 is deze variabele alleen geldig in script modules ( `.psm1` ).</span><span class="sxs-lookup"><span data-stu-id="a4b5d-229">In PowerShell 2.0, this variable is valid only in script modules (`.psm1`).</span></span>
  <span data-ttu-id="a4b5d-230">Vanaf Power Shell 3,0 is deze in alle scripts geldig.</span><span class="sxs-lookup"><span data-stu-id="a4b5d-230">Beginning in PowerShell 3.0, it is valid in all scripts.</span></span>

- <span data-ttu-id="a4b5d-231">`$MyInvocation` -De `$MyInvocation` Automatische variabele bevat informatie over het huidige script, met inbegrip van informatie over hoe het is gestart of geactiveerd.</span><span class="sxs-lookup"><span data-stu-id="a4b5d-231">`$MyInvocation` - The `$MyInvocation` automatic variable contains information about the current script, including information about how it was started or "invoked."</span></span> <span data-ttu-id="a4b5d-232">U kunt deze variabele en de bijbehorende eigenschappen gebruiken om informatie over het script op te halen terwijl deze wordt uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="a4b5d-232">You can use this variable and its properties to get information about the script while it is running.</span></span> <span data-ttu-id="a4b5d-233">Bijvoorbeeld, de `$MyInvocation` . De variabele MyCommand. path bevat het pad en de bestands naam van het script.</span><span class="sxs-lookup"><span data-stu-id="a4b5d-233">For example, the `$MyInvocation`.MyCommand.Path variable contains the path and filename of the script.</span></span> <span data-ttu-id="a4b5d-234">`$MyInvocation`. De regel bevat de opdracht waarmee het script is gestart, inclusief alle para meters en waarden.</span><span class="sxs-lookup"><span data-stu-id="a4b5d-234">`$MyInvocation`.Line contains the command that started the script, including all parameters and values.</span></span>

  <span data-ttu-id="a4b5d-235">Vanaf Power Shell 3,0 `$MyInvocation` heeft twee nieuwe eigenschappen die informatie geven over het script dat het huidige script heeft aangeroepen of aangeroepen.</span><span class="sxs-lookup"><span data-stu-id="a4b5d-235">Beginning in PowerShell 3.0, `$MyInvocation` has two new properties that provide information about the script that called or invoked the current script.</span></span> <span data-ttu-id="a4b5d-236">De waarden van deze eigenschappen worden alleen ingevuld wanneer de aanroepende of aanroeper een script is.</span><span class="sxs-lookup"><span data-stu-id="a4b5d-236">The values of these properties are populated only when the invoker or caller is a script.</span></span>

  - <span data-ttu-id="a4b5d-237">**PSCommandPath** bevat het volledige pad en de naam van het script dat het huidige script heeft aangeroepen of aangeroepen.</span><span class="sxs-lookup"><span data-stu-id="a4b5d-237">**PSCommandPath** contains the full path and name of the script that called or invoked the current script.</span></span>

  - <span data-ttu-id="a4b5d-238">**PSScriptRoot** bevat de map van het script dat het huidige script heeft aangeroepen of aangeroepen.</span><span class="sxs-lookup"><span data-stu-id="a4b5d-238">**PSScriptRoot** contains the directory of the script that called or invoked the current script.</span></span>

  <span data-ttu-id="a4b5d-239">In tegens telling tot de `$PSCommandPath` en `$PSScriptRoot` automatische variabelen, die informatie bevatten over het huidige script, bevatten de eigenschappen **PSCommandPath** en **PSScriptRoot** van de `$MyInvocation` variabele informatie over het script dat het huidige script aanroept.</span><span class="sxs-lookup"><span data-stu-id="a4b5d-239">Unlike the `$PSCommandPath` and `$PSScriptRoot` automatic variables, which contain information about the current script, the **PSCommandPath** and **PSScriptRoot** properties of the `$MyInvocation` variable contain information about the script that called the current script.</span></span>

- <span data-ttu-id="a4b5d-240">Gegevens secties: u kunt het `Data` sleutel woord gebruiken om gegevens te scheiden van logica in scripts.</span><span class="sxs-lookup"><span data-stu-id="a4b5d-240">Data sections - You can use the `Data` keyword to separate data from logic in scripts.</span></span> <span data-ttu-id="a4b5d-241">Gegevens secties kunnen de lokalisatie ook gemakkelijker maken.</span><span class="sxs-lookup"><span data-stu-id="a4b5d-241">Data sections can also make localization easier.</span></span> <span data-ttu-id="a4b5d-242">Zie [about_Data_Sections](about_Data_Sections.md) en [about_Script_Internationalization](about_Script_Internationalization.md)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="a4b5d-242">For more information, see [about_Data_Sections](about_Data_Sections.md) and [about_Script_Internationalization](about_Script_Internationalization.md).</span></span>

- <span data-ttu-id="a4b5d-243">Script ondertekening: u kunt een digitale hand tekening aan een script toevoegen.</span><span class="sxs-lookup"><span data-stu-id="a4b5d-243">Script Signing - You can add a digital signature to a script.</span></span> <span data-ttu-id="a4b5d-244">Afhankelijk van het uitvoerings beleid kunt u digitale hand tekeningen gebruiken om de uitvoering van scripts te beperken die onveilige opdrachten kunnen bevatten.</span><span class="sxs-lookup"><span data-stu-id="a4b5d-244">Depending on the execution policy, you can use digital signatures to restrict the running of scripts that could include unsafe commands.</span></span> <span data-ttu-id="a4b5d-245">Zie [about_Execution_Policies](about_Execution_Policies.md) en [about_Signing](about_Signing.md)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="a4b5d-245">For more information, see [about_Execution_Policies](about_Execution_Policies.md) and [about_Signing](about_Signing.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="a4b5d-246">Zie ook</span><span class="sxs-lookup"><span data-stu-id="a4b5d-246">See also</span></span>

[<span data-ttu-id="a4b5d-247">about_Command_Precedence</span><span class="sxs-lookup"><span data-stu-id="a4b5d-247">about_Command_Precedence</span></span>](about_Command_Precedence.md)

[<span data-ttu-id="a4b5d-248">about_Comment_Based_Help</span><span class="sxs-lookup"><span data-stu-id="a4b5d-248">about_Comment_Based_Help</span></span>](about_Comment_Based_Help.md)

[<span data-ttu-id="a4b5d-249">about_Execution_Policies</span><span class="sxs-lookup"><span data-stu-id="a4b5d-249">about_Execution_Policies</span></span>](about_Execution_Policies.md)

[<span data-ttu-id="a4b5d-250">about_Functions</span><span class="sxs-lookup"><span data-stu-id="a4b5d-250">about_Functions</span></span>](about_Functions.md)

[<span data-ttu-id="a4b5d-251">about_Modules</span><span class="sxs-lookup"><span data-stu-id="a4b5d-251">about_Modules</span></span>](about_Modules.md)

[<span data-ttu-id="a4b5d-252">about_Profiles</span><span class="sxs-lookup"><span data-stu-id="a4b5d-252">about_Profiles</span></span>](about_Profiles.md)

[<span data-ttu-id="a4b5d-253">about_Requires</span><span class="sxs-lookup"><span data-stu-id="a4b5d-253">about_Requires</span></span>](about_Requires.md)

[<span data-ttu-id="a4b5d-254">about_Run_With_PowerShell</span><span class="sxs-lookup"><span data-stu-id="a4b5d-254">about_Run_With_PowerShell</span></span>](about_Run_With_PowerShell.md)

[<span data-ttu-id="a4b5d-255">about_Scopes</span><span class="sxs-lookup"><span data-stu-id="a4b5d-255">about_Scopes</span></span>](about_Scopes.md)

[<span data-ttu-id="a4b5d-256">about_Script_Blocks</span><span class="sxs-lookup"><span data-stu-id="a4b5d-256">about_Script_Blocks</span></span>](about_Script_Blocks.md)

[<span data-ttu-id="a4b5d-257">about_Signing</span><span class="sxs-lookup"><span data-stu-id="a4b5d-257">about_Signing</span></span>](about_Signing.md)

[<span data-ttu-id="a4b5d-258">Invoke-opdracht</span><span class="sxs-lookup"><span data-stu-id="a4b5d-258">Invoke-Command</span></span>](xref:Microsoft.PowerShell.Core.Invoke-Command)
