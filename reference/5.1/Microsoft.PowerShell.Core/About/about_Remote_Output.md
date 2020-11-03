---
description: Hierin wordt beschreven hoe u de uitvoer van externe opdrachten kunt interpreteren en opmaken.
keywords: powershell,cmdlet
Locale: en-US
ms.date: 12/01/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_remote_output?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Remote_Output
ms.openlocfilehash: c5636a301017111adf97b6332237e737b4bf0716
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/13/2020
ms.locfileid: "93252748"
---
# <a name="about-remote-output"></a><span data-ttu-id="6470e-104">Over externe uitvoer</span><span class="sxs-lookup"><span data-stu-id="6470e-104">About Remote Output</span></span>

## <a name="short-description"></a><span data-ttu-id="6470e-105">KORTE BESCHRIJVING</span><span class="sxs-lookup"><span data-stu-id="6470e-105">SHORT DESCRIPTION</span></span>

<span data-ttu-id="6470e-106">Hierin wordt beschreven hoe u de uitvoer van externe opdrachten kunt interpreteren en opmaken.</span><span class="sxs-lookup"><span data-stu-id="6470e-106">Describes how to interpret and format the output of remote commands.</span></span>

## <a name="long-description"></a><span data-ttu-id="6470e-107">LANGE BESCHRIJVING</span><span class="sxs-lookup"><span data-stu-id="6470e-107">LONG DESCRIPTION</span></span>

<span data-ttu-id="6470e-108">De uitvoer van een opdracht die is uitgevoerd op een externe computer kan eruitzien als uitvoer van dezelfde opdracht die wordt uitgevoerd op een lokale computer, maar er zijn een aantal belang rijke verschillen.</span><span class="sxs-lookup"><span data-stu-id="6470e-108">The output of a command that was run on a remote computer might look like output of the same command run on a local computer, but there are some significant differences.</span></span>

<span data-ttu-id="6470e-109">In dit onderwerp wordt uitgelegd hoe u de uitvoer van opdrachten die op externe computers worden uitgevoerd, kunt interpreteren, opmaken en weer geven.</span><span class="sxs-lookup"><span data-stu-id="6470e-109">This topic explains how to interpret, format, and display the output of commands that are run on remote computers.</span></span>

## <a name="displaying-the-computer-name"></a><span data-ttu-id="6470e-110">DE COMPUTER NAAM WORDT WEER GEGEVEN</span><span class="sxs-lookup"><span data-stu-id="6470e-110">DISPLAYING THE COMPUTER NAME</span></span>

<span data-ttu-id="6470e-111">Wanneer u de cmdlet Invoke-Command gebruikt om een opdracht uit te voeren op een externe computer, retourneert de opdracht een object dat de naam bevat van de computer die de gegevens heeft gegenereerd.</span><span class="sxs-lookup"><span data-stu-id="6470e-111">When you use the Invoke-Command cmdlet to run a command on a remote computer, the command returns an object that includes the name of the computer that generated the data.</span></span> <span data-ttu-id="6470e-112">De naam van de externe computer wordt opgeslagen in de eigenschap PSComputerName.</span><span class="sxs-lookup"><span data-stu-id="6470e-112">The remote computer name is stored in the PSComputerName property.</span></span>

<span data-ttu-id="6470e-113">Voor veel opdrachten wordt de PSComputerName standaard weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="6470e-113">For many commands, the PSComputerName is displayed by default.</span></span> <span data-ttu-id="6470e-114">Met de volgende opdracht wordt bijvoorbeeld een Get-Culture-opdracht uitgevoerd op twee externe computers: Server01 en Server02.</span><span class="sxs-lookup"><span data-stu-id="6470e-114">For example, the following command runs a Get-Culture command on two remote computers, Server01 and Server02.</span></span> <span data-ttu-id="6470e-115">De uitvoer, die hieronder wordt weer gegeven, bevat de namen van de externe computers waarop de opdracht is uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="6470e-115">The output, which appears below, includes the names of the remote computers on which the command ran.</span></span>

```powershell
C:\PS> invoke-command -script {get-culture} -comp Server01, Server02

LCID  Name    DisplayName                PSComputerName
----  ----    -----------                --------------
1033  en-US   English (United States)    Server01
1033  es-AR   Spanish (Argentina)        Server02
```

<span data-ttu-id="6470e-116">U kunt de para meter HideComputerName van Invoke-Command gebruiken om de eigenschap PSComputerName te verbergen.</span><span class="sxs-lookup"><span data-stu-id="6470e-116">You can use the HideComputerName parameter of Invoke-Command to hide the PSComputerName property.</span></span> <span data-ttu-id="6470e-117">Deze para meter is bedoeld voor opdrachten voor het verzamelen van gegevens van slechts één externe computer.</span><span class="sxs-lookup"><span data-stu-id="6470e-117">This parameter is designed for commands that collect data from only one remote computer.</span></span>

<span data-ttu-id="6470e-118">Met de volgende opdracht wordt een Get-Culture-opdracht uitgevoerd op de externe computer Server01.</span><span class="sxs-lookup"><span data-stu-id="6470e-118">The following command runs a Get-Culture command on the Server01 remote computer.</span></span> <span data-ttu-id="6470e-119">De para meter HideComputerName wordt gebruikt om de eigenschap PSComputerName en gerelateerde eigenschappen te verbergen.</span><span class="sxs-lookup"><span data-stu-id="6470e-119">It uses the HideComputerName parameter to hide the PSComputerName property and related properties.</span></span>

```powershell
C:\PS> invoke-command -scr {get-culture} -comp Server01 -HideComputerName

LCID             Name             DisplayName
----             ----             -----------
1033             en-US            English (United States)
```

<span data-ttu-id="6470e-120">U kunt ook de eigenschap PSComputerName weer geven als deze niet standaard wordt weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="6470e-120">You can also display the PSComputerName property if it is not displayed by default.</span></span>

<span data-ttu-id="6470e-121">De volgende opdrachten gebruiken bijvoorbeeld de cmdlet Format-Table om de eigenschap PSComputerName toe te voegen aan de uitvoer van een externe Get-Date opdracht.</span><span class="sxs-lookup"><span data-stu-id="6470e-121">For example, the following commands use the Format-Table cmdlet to add the PSComputerName property to the output of a remote Get-Date command.</span></span>

```powershell
$dates = invoke-command -script {get-date} -computername Server01, Server02
$dates | format-table DateTime, PSComputerName -auto

DateTime                            PSComputerName
--------                            --------------
Monday, July 21, 2008 7:16:58 PM    Server01
Monday, July 21, 2008 7:16:58 PM    Server02
```

## <a name="displaying-the-machinename-property"></a><span data-ttu-id="6470e-122">DE EIGENSCHAP MACHINENAME WEER GEVEN</span><span class="sxs-lookup"><span data-stu-id="6470e-122">DISPLAYING THE MACHINENAME PROPERTY</span></span>

<span data-ttu-id="6470e-123">Verschillende cmdlets, waaronder Get-proces, Get-service en Get-EventLog, hebben een ComputerName-para meter waarmee de objecten op een externe computer worden opgehaald.</span><span class="sxs-lookup"><span data-stu-id="6470e-123">Several cmdlets, including Get-Process, Get-Service, and Get-EventLog, have a ComputerName parameter that gets the objects on a remote computer.</span></span>
<span data-ttu-id="6470e-124">Deze cmdlets gebruiken geen externe communicatie met Windows Power shell, zodat u ze zelfs kunt gebruiken op computers die niet zijn geconfigureerd voor externe toegang in Windows Power shell.</span><span class="sxs-lookup"><span data-stu-id="6470e-124">These cmdlets do not use Windows PowerShell remoting, so you can use them even on computers that are not configured for remoting in Windows PowerShell.</span></span>

<span data-ttu-id="6470e-125">De objecten die met deze cmdlets worden opgehaald, bevatten de naam van de externe computer in de eigenschap MachineName.</span><span class="sxs-lookup"><span data-stu-id="6470e-125">The objects that these cmdlets return store the name of the remote computer in the MachineName property.</span></span> <span data-ttu-id="6470e-126">(Deze objecten hebben geen eigenschap PSComputerName.)</span><span class="sxs-lookup"><span data-stu-id="6470e-126">(These objects do not have a PSComputerName property.)</span></span>

<span data-ttu-id="6470e-127">Met deze opdracht wordt bijvoorbeeld het Power Shell-proces op de externe computers Server01 en Server02.</span><span class="sxs-lookup"><span data-stu-id="6470e-127">For example, this command gets the PowerShell process on the Server01 and Server02 remote computers.</span></span> <span data-ttu-id="6470e-128">De standaard weergave bevat niet de eigenschap MachineName.</span><span class="sxs-lookup"><span data-stu-id="6470e-128">The default display does not include the MachineName property.</span></span>

```powershell
C:\PS> get-process PowerShell -computername server01, server02

Handles  NPM(K)    PM(K)      WS(K) VM(M)   CPU(s)     Id ProcessName
-------  ------    -----      ----- -----   ------     -- -----------
920      38    97524     114504   575     9.66   2648 PowerShell
194       6    24256      32384   142            3020 PowerShell
352      27    63472      63520   577     3.84   4796 PowerShell
```

<span data-ttu-id="6470e-129">U kunt de cmdlet Format-Table gebruiken om de eigenschap MachineName van de proces objecten weer te geven.</span><span class="sxs-lookup"><span data-stu-id="6470e-129">You can use the Format-Table cmdlet to display the MachineName property of the process objects.</span></span>

<span data-ttu-id="6470e-130">Met de volgende opdracht worden bijvoorbeeld de processen opgeslagen in de variabele $p en vervolgens een pijplijn operator (|) gebruikt om de processen in $p naar de Format-Table opdracht te verzenden.</span><span class="sxs-lookup"><span data-stu-id="6470e-130">For example, the following command saves the processes in the $p variable and then uses a pipeline operator (|) to send the processes in $p to the Format-Table command.</span></span> <span data-ttu-id="6470e-131">De opdracht gebruikt de eigenschaps parameter van Format-Table om de eigenschap MachineName op te geven in de weer gave.</span><span class="sxs-lookup"><span data-stu-id="6470e-131">The command uses the Property parameter of Format-Table to include the MachineName property in the display.</span></span>

```powershell
C:\PS> $p = get-process PowerShell -comp Server01, Server02
C:\PS> $P | format-table -property ID, ProcessName, MachineName -auto

Id ProcessName MachineName
-- ----------- -----------
2648 PowerShell  Server02
3020 PowerShell  Server01
4796 PowerShell  Server02
```

<span data-ttu-id="6470e-132">Met de volgende complexe opdracht wordt de eigenschap MachineName toegevoegd aan de standaard proces weergave.</span><span class="sxs-lookup"><span data-stu-id="6470e-132">The following more complex command adds the MachineName property to the default process display.</span></span> <span data-ttu-id="6470e-133">Hash-tabellen worden gebruikt om berekende eigenschappen op te geven.</span><span class="sxs-lookup"><span data-stu-id="6470e-133">It uses hash tables to specify calculated properties.</span></span> <span data-ttu-id="6470e-134">Gelukkig hoeft u deze niet te begrijpen om het te gebruiken.</span><span class="sxs-lookup"><span data-stu-id="6470e-134">Fortunately, you do not have to understand it to use it.</span></span>

<span data-ttu-id="6470e-135">(Houd er rekening mee dat de apostroffen ['] het voortzettings teken is.)</span><span class="sxs-lookup"><span data-stu-id="6470e-135">(Note that the backtick [\`] is the continuation character.)</span></span>

```powershell
C:\PS> $p = get-process PowerShell -comp Server01, Server02

C:\PS> $p | format-table -property Handles, `
@{Label="NPM(K)";Expression={int}}, `
@{Label="PM(K)";Expression={int}}, `
@{Label="WS(K)";Expression={int}}, `
@{Label="VM(M)";Expression={int}}, `
@{Label="CPU(s)";Expression={if ($.CPU -ne $()){ $.CPU.ToString("N")}}}, `
Id, ProcessName, MachineName -auto

Handles NPM(K) PM(K)  WS(K) VM(M) CPU(s)   Id ProcessName MachineName
------- ------ -----  ----- ----- ------   -- ----------- -----------
920     38 97560 114532   576        2648 PowerShell  Server02
192      6 24132  32028   140        3020 PowerShell  Server01
438     26 48436  59132   565        4796 PowerShell  Server02

```

## <a name="deserialized-objects"></a><span data-ttu-id="6470e-136">GEDESERIALISEERD OBJECTEN</span><span class="sxs-lookup"><span data-stu-id="6470e-136">DESERIALIZED OBJECTS</span></span>

<span data-ttu-id="6470e-137">Wanneer u externe opdrachten uitvoert die uitvoer genereren, wordt de uitvoer van de opdracht naar de lokale computer verzonden via het netwerk.</span><span class="sxs-lookup"><span data-stu-id="6470e-137">When you run remote commands that generate output, the command output is transmitted across the network back to the local computer.</span></span>

<span data-ttu-id="6470e-138">Omdat de meeste Live Microsoft .NET Framework-objecten (zoals de objecten die Windows Power shell-cmdlets retour neren) niet via het netwerk kunnen worden verzonden, zijn de live-objecten ' geserialiseerd '.</span><span class="sxs-lookup"><span data-stu-id="6470e-138">Because most live Microsoft .NET Framework objects (such as the objects that Windows PowerShell cmdlets return) cannot be transmitted over the network, the live objects are "serialized".</span></span> <span data-ttu-id="6470e-139">Met andere woorden, de live-objecten worden geconverteerd naar XML-representaties van het object en de bijbehorende eigenschappen.</span><span class="sxs-lookup"><span data-stu-id="6470e-139">In other words, the live objects are converted into XML representations of the object and its properties.</span></span> <span data-ttu-id="6470e-140">Vervolgens wordt het geserialiseerde XML-object via het netwerk verzonden.</span><span class="sxs-lookup"><span data-stu-id="6470e-140">Then, the XML-based serialized object is transmitted across the network.</span></span>

<span data-ttu-id="6470e-141">Op de lokale computer ontvangt Windows Power shell het geserializeerde XML-object en wordt het ' gedeserialiseerd ' door het XML-object te converteren naar een standaard .NET Framework-object.</span><span class="sxs-lookup"><span data-stu-id="6470e-141">On the local computer, Windows PowerShell receives the XML-based serialized object and "deserializes" it by converting the XML-based object into a standard .NET Framework object.</span></span>

<span data-ttu-id="6470e-142">Het gedeserialiseerd object is echter geen live-object.</span><span class="sxs-lookup"><span data-stu-id="6470e-142">However, the deserialized object is not a live object.</span></span> <span data-ttu-id="6470e-143">Het is een moment opname van het object op het moment dat het is geserialiseerd en bevat eigenschappen, maar geen methoden.</span><span class="sxs-lookup"><span data-stu-id="6470e-143">It is a snapshot of the object at the time that it was serialized, and it includes properties but no methods.</span></span> <span data-ttu-id="6470e-144">U kunt deze objecten gebruiken en beheren in Windows Power shell, zoals het door geven in pijp lijnen, het weer geven van geselecteerde eigenschappen en het format teren ervan.</span><span class="sxs-lookup"><span data-stu-id="6470e-144">You can use and manage these objects in Windows PowerShell, including passing them in pipelines, displaying selected properties, and formatting them.</span></span>

<span data-ttu-id="6470e-145">De meeste gedeserialiseerd objecten worden automatisch opgemaakt voor weer gave door vermeldingen in de XML-bestanden van Types.ps1XML of Format.ps1.</span><span class="sxs-lookup"><span data-stu-id="6470e-145">Most deserialized objects are automatically formatted for display by entries in the Types.ps1xml or Format.ps1xml files.</span></span> <span data-ttu-id="6470e-146">Het is echter mogelijk dat de lokale computer geen indelings bestanden heeft voor alle gedeserialiseerd objecten die op een externe computer zijn gegenereerd.</span><span class="sxs-lookup"><span data-stu-id="6470e-146">However, the local computer might not have formatting files for all of the deserialized objects that were generated on a remote computer.</span></span> <span data-ttu-id="6470e-147">Wanneer objecten niet zijn opgemaakt, worden alle eigenschappen van elk object weer gegeven in de-console in een lijst met stromen.</span><span class="sxs-lookup"><span data-stu-id="6470e-147">When objects are not formatted, all of the properties of each object appear in the console in a streaming list.</span></span>

<span data-ttu-id="6470e-148">Wanneer objecten niet automatisch worden opgemaakt, kunt u de opmaak-cmdlets, zoals Format-Table of opmaak lijst, gebruiken om de geselecteerde eigenschappen in te delen en weer te geven.</span><span class="sxs-lookup"><span data-stu-id="6470e-148">When objects are not formatted automatically, you can use the formatting cmdlets, such as Format-Table or Format-List, to format and display selected properties.</span></span> <span data-ttu-id="6470e-149">U kunt ook de cmdlet Out-GridView gebruiken om de objecten in een tabel weer te geven.</span><span class="sxs-lookup"><span data-stu-id="6470e-149">Or, you can use the Out-GridView cmdlet to display the objects in a table.</span></span>

<span data-ttu-id="6470e-150">Als u een opdracht uitvoert op een externe computer die cmdlets gebruikt die u niet op uw lokale computer hebt, zijn de objecten die de opdracht retourneert mogelijk niet correct ingedeeld omdat u niet beschikt over de indeling van de bestanden voor die objecten op uw computer.</span><span class="sxs-lookup"><span data-stu-id="6470e-150">Also, if you run a command on a remote computer that uses cmdlets that you do not have on your local computer, the objects that the command returns might not be formatted properly because you do not have the formatting files for those objects on your computer.</span></span> <span data-ttu-id="6470e-151">Gebruik de cmdlets Get-FormatData en Export-FormatData om gegevens op te halen van een andere computer.</span><span class="sxs-lookup"><span data-stu-id="6470e-151">To get formatting data from another computer, use the Get-FormatData and Export-FormatData cmdlets.</span></span>

<span data-ttu-id="6470e-152">Sommige object typen, zoals DirectoryInfo-objecten en GUID'S, worden weer omgezet in live-objecten wanneer ze worden ontvangen.</span><span class="sxs-lookup"><span data-stu-id="6470e-152">Some object types, such as DirectoryInfo objects and GUIDs, are converted back into live objects when they are received.</span></span> <span data-ttu-id="6470e-153">Voor deze objecten is geen speciale verwerking of opmaak vereist.</span><span class="sxs-lookup"><span data-stu-id="6470e-153">These objects do not need any special handling or formatting.</span></span>

## <a name="ordering-the-results"></a><span data-ttu-id="6470e-154">DE RESULTATEN BEST ELLEN</span><span class="sxs-lookup"><span data-stu-id="6470e-154">ORDERING THE RESULTS</span></span>

<span data-ttu-id="6470e-155">De volg orde van de computer namen in de para meter ComputerName van cmdlets bepaalt de volg orde waarin Windows Power shell verbinding maakt met de externe computers.</span><span class="sxs-lookup"><span data-stu-id="6470e-155">The order of the computer names in the ComputerName parameter of cmdlets determines the order in which Windows PowerShell connects to the remote computers.</span></span> <span data-ttu-id="6470e-156">De resultaten worden echter weer gegeven in de volg orde waarin de lokale computer deze ontvangt. Dit kan een andere volg orde zijn.</span><span class="sxs-lookup"><span data-stu-id="6470e-156">However, the results appear in the order in which the local computer receives them, which might be a different order.</span></span>

<span data-ttu-id="6470e-157">Gebruik de cmdlet Sort-Object om de volg orde van de resultaten te wijzigen.</span><span class="sxs-lookup"><span data-stu-id="6470e-157">To change the order of the results, use the Sort-Object cmdlet.</span></span> <span data-ttu-id="6470e-158">U kunt sorteren op de eigenschap PSComputerName of MachineName.</span><span class="sxs-lookup"><span data-stu-id="6470e-158">You can sort on the PSComputerName or MachineName property.</span></span> <span data-ttu-id="6470e-159">U kunt ook sorteren op een andere eigenschap van het object, zodat de resultaten van verschillende computers worden omgevallen.</span><span class="sxs-lookup"><span data-stu-id="6470e-159">You can also sort on another property of the object so that the results from different computers are interspersed.</span></span>

## <a name="see-also"></a><span data-ttu-id="6470e-160">ZIE OOK</span><span class="sxs-lookup"><span data-stu-id="6470e-160">SEE ALSO</span></span>

[<span data-ttu-id="6470e-161">about_Remote</span><span class="sxs-lookup"><span data-stu-id="6470e-161">about_Remote</span></span>](about_Remote.md)

[<span data-ttu-id="6470e-162">about_Remote_Variables</span><span class="sxs-lookup"><span data-stu-id="6470e-162">about_Remote_Variables</span></span>](about_Remote_Variables.md)

[<span data-ttu-id="6470e-163">Format-Table</span><span class="sxs-lookup"><span data-stu-id="6470e-163">Format-Table</span></span>](xref:Microsoft.PowerShell.Utility.Format-Table)

[<span data-ttu-id="6470e-164">Get-EventLog</span><span class="sxs-lookup"><span data-stu-id="6470e-164">Get-EventLog</span></span>](xref:Microsoft.PowerShell.Management.Get-EventLog)

[<span data-ttu-id="6470e-165">Get-Process</span><span class="sxs-lookup"><span data-stu-id="6470e-165">Get-Process</span></span>](xref:Microsoft.PowerShell.Management.Get-Process)

[<span data-ttu-id="6470e-166">Get-Service</span><span class="sxs-lookup"><span data-stu-id="6470e-166">Get-Service</span></span>](xref:Microsoft.PowerShell.Management.Get-Service)

[<span data-ttu-id="6470e-167">Get-WmiObject</span><span class="sxs-lookup"><span data-stu-id="6470e-167">Get-WmiObject</span></span>](xref:Microsoft.PowerShell.Management.Get-WmiObject)

[<span data-ttu-id="6470e-168">Invoke-opdracht</span><span class="sxs-lookup"><span data-stu-id="6470e-168">Invoke-Command</span></span>](xref:Microsoft.PowerShell.Core.Invoke-Command)

[<span data-ttu-id="6470e-169">Out-GridView</span><span class="sxs-lookup"><span data-stu-id="6470e-169">Out-GridView</span></span>](xref:Microsoft.PowerShell.Utility.Out-GridView)

[<span data-ttu-id="6470e-170">Select-Object</span><span class="sxs-lookup"><span data-stu-id="6470e-170">Select-Object</span></span>](xref:Microsoft.PowerShell.Utility.Select-Object)
