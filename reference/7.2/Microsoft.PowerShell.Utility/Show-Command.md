---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 10/29/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/show-command?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Show-Command
ms.openlocfilehash: 87bdd5a9610267b8fce9e391431d24872a77e2de
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 11/17/2020
ms.locfileid: "94705813"
---
# <span data-ttu-id="64d98-102">Show-Command</span><span class="sxs-lookup"><span data-stu-id="64d98-102">Show-Command</span></span>

## <span data-ttu-id="64d98-103">SAMENVATTING</span><span class="sxs-lookup"><span data-stu-id="64d98-103">SYNOPSIS</span></span>
<span data-ttu-id="64d98-104">Hiermee worden de Power shell-opdracht gegevens in een grafisch venster weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="64d98-104">Displays PowerShell command information in a graphical window.</span></span>

## <span data-ttu-id="64d98-105">SYNTAXIS</span><span class="sxs-lookup"><span data-stu-id="64d98-105">SYNTAX</span></span>

```
Show-Command [[-Name] <String>] [-Height <Double>] [-Width <Double>] [-NoCommonParameter]
 [-ErrorPopup] [-PassThru] [<CommonParameters>]
```

## <span data-ttu-id="64d98-106">BESCHRIJVING</span><span class="sxs-lookup"><span data-stu-id="64d98-106">DESCRIPTION</span></span>

<span data-ttu-id="64d98-107">`Show-Command`Met de cmdlet kunt u een Power shell-opdracht in een opdracht venster maken.</span><span class="sxs-lookup"><span data-stu-id="64d98-107">The `Show-Command` cmdlet lets you create a PowerShell command in a command window.</span></span> <span data-ttu-id="64d98-108">U kunt de functies van het opdracht venster gebruiken om de opdracht uit te voeren of de opdracht naar u te retour neren.</span><span class="sxs-lookup"><span data-stu-id="64d98-108">You can use the features of the command window to run the command or have it return the command to you.</span></span>

<span data-ttu-id="64d98-109">`Show-Command` is een zeer nuttig hulp programma voor onderwijs en leer.</span><span class="sxs-lookup"><span data-stu-id="64d98-109">`Show-Command` is a very useful teaching and learning tool.</span></span> <span data-ttu-id="64d98-110">`Show-Command` werkt op alle opdracht typen, inclusief cmdlets, functies, werk stromen en CIM-opdrachten.</span><span class="sxs-lookup"><span data-stu-id="64d98-110">`Show-Command` works on all command types, including cmdlets, functions, workflows and CIM commands.</span></span>

<span data-ttu-id="64d98-111">Zonder para meters `Show-Command` wordt een opdracht venster weer gegeven met een lijst met alle beschik bare opdrachten in alle geïnstalleerde modules.</span><span class="sxs-lookup"><span data-stu-id="64d98-111">Without parameters, `Show-Command` displays a command window that lists all available commands in all installed modules.</span></span> <span data-ttu-id="64d98-112">Als u de opdrachten in een module wilt zoeken, selecteert u de module in de vervolg keuzelijst modules.</span><span class="sxs-lookup"><span data-stu-id="64d98-112">To find the commands in a module, select the module from the Modules drop-down list.</span></span> <span data-ttu-id="64d98-113">Als u een opdracht wilt selecteren, klikt u op de naam van de opdracht.</span><span class="sxs-lookup"><span data-stu-id="64d98-113">To select a command, click the command name.</span></span>

<span data-ttu-id="64d98-114">Als u het opdracht venster wilt gebruiken, selecteert u een opdracht door de naam te gebruiken of door te klikken op de naam van de opdracht in de lijst **opdrachten** .</span><span class="sxs-lookup"><span data-stu-id="64d98-114">To use the command window, select a command, either by using the Name or by clicking the command name in the **Commands** list.</span></span> <span data-ttu-id="64d98-115">Elke parameterset wordt weer gegeven op een afzonderlijk tabblad. Sterretjes geven de verplichte para meters aan.</span><span class="sxs-lookup"><span data-stu-id="64d98-115">Each parameter set is displayed on a separate tab. Asterisks indicate the mandatory parameters.</span></span> <span data-ttu-id="64d98-116">Als u waarden voor een para meter wilt invoeren, typt u de waarde in het tekstvak of selecteert u de waarde in de vervolg keuzelijst.</span><span class="sxs-lookup"><span data-stu-id="64d98-116">To enter values for a parameter, type the value in the text box or select the value from the drop-down box.</span></span> <span data-ttu-id="64d98-117">Als u een para meter switch wilt toevoegen, schakelt u het selectie vakje voor de para meter in.</span><span class="sxs-lookup"><span data-stu-id="64d98-117">To add a switch parameter, click to select the parameter check box.</span></span>

<span data-ttu-id="64d98-118">Wanneer u klaar bent, klikt u op **kopiëren** om de opdracht die u hebt gemaakt naar het klem bord te kopiëren. u kunt ook op **uitvoeren** klikken om de opdracht uit te voeren.</span><span class="sxs-lookup"><span data-stu-id="64d98-118">When you're ready, you can click **Copy** to copy the command that you've created to the clipboard or click **Run** to run the command.</span></span> <span data-ttu-id="64d98-119">U kunt ook de para meter **PassThru** gebruiken om de opdracht te retour neren naar het host-programma, zoals de Power shell-console.</span><span class="sxs-lookup"><span data-stu-id="64d98-119">You can also use the **PassThru** parameter to return the command to the host program, such as the PowerShell console.</span></span> <span data-ttu-id="64d98-120">Als u de opdracht selectie wilt annuleren en wilt terugkeren naar de weer gave waarin alle opdrachten worden weer gegeven, drukt u op CTRL en klikt u op de geselecteerde opdracht.</span><span class="sxs-lookup"><span data-stu-id="64d98-120">To cancel the command selection and return to the view that displays all commands, press Ctrl and click the selected command.</span></span>

<span data-ttu-id="64d98-121">In Power shell Integrated Scripting Environment (ISE) wordt standaard een variant van het `Show-Command` venster weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="64d98-121">In the PowerShell Integrated Scripting Environment (ISE), a variation of the `Show-Command` window is displayed by default.</span></span> <span data-ttu-id="64d98-122">Zie de Help-onderwerpen over Power shell ISE voor meer informatie over het gebruik van dit opdracht venster.</span><span class="sxs-lookup"><span data-stu-id="64d98-122">For information about using this command window, see the PowerShell ISE Help topics.</span></span>

<span data-ttu-id="64d98-123">Deze cmdlet is opnieuw geïntroduceerd in Power shell 7.</span><span class="sxs-lookup"><span data-stu-id="64d98-123">This cmdlet was reintroduced in PowerShell 7.</span></span>

<span data-ttu-id="64d98-124">Omdat deze cmdlet een gebruikers interface vereist, werkt deze niet op Windows Server Core of Windows nano server.</span><span class="sxs-lookup"><span data-stu-id="64d98-124">Because this cmdlet requires a user interface, it does not work on Windows Server Core or Windows Nano Server.</span></span> <span data-ttu-id="64d98-125">Deze cmdlet is alleen beschikbaar op Windows-systemen die ondersteuning bieden voor het Windows-bureau blad.</span><span class="sxs-lookup"><span data-stu-id="64d98-125">This cmdlet is only available on Windows systems that support the Windows Desktop.</span></span>

## <span data-ttu-id="64d98-126">VOORBEELDEN</span><span class="sxs-lookup"><span data-stu-id="64d98-126">EXAMPLES</span></span>

### <span data-ttu-id="64d98-127">Voor beeld 1: het venster opdrachten openen</span><span class="sxs-lookup"><span data-stu-id="64d98-127">Example 1: Open the Commands window</span></span>

<span data-ttu-id="64d98-128">In dit voor beeld wordt de standaard weergave van het venster weer gegeven `Show-Command` .</span><span class="sxs-lookup"><span data-stu-id="64d98-128">This example displays the default view of the `Show-Command` window.</span></span> <span data-ttu-id="64d98-129">In het venster **opdrachten** wordt een lijst weer gegeven met alle opdrachten in alle modules die op de computer zijn geïnstalleerd.</span><span class="sxs-lookup"><span data-stu-id="64d98-129">The **Commands** window displays a list of all commands in all modules that are installed on the computer.</span></span>

```powershell
Show-Command
```

### <span data-ttu-id="64d98-130">Voor beeld 2: een cmdlet openen in het venster opdrachten</span><span class="sxs-lookup"><span data-stu-id="64d98-130">Example 2: Open a cmdlet in the Commands window</span></span>

<span data-ttu-id="64d98-131">In dit voor beeld wordt de cmdlet weer gegeven `Invoke-Command` in het **opdracht** venster.</span><span class="sxs-lookup"><span data-stu-id="64d98-131">This example display the `Invoke-Command` cmdlet in the **Command** window.</span></span> <span data-ttu-id="64d98-132">U kunt deze weer gave gebruiken om opdrachten uit te voeren `Invoke-Command` .</span><span class="sxs-lookup"><span data-stu-id="64d98-132">You can use this display to run `Invoke-Command` commands.</span></span>

```powershell
Show-Command -Name "Invoke-Command"
```

### <span data-ttu-id="64d98-133">Voor beeld 3: een cmdlet met opgegeven para meters openen</span><span class="sxs-lookup"><span data-stu-id="64d98-133">Example 3: Open a cmdlet with specified parameters</span></span>

<span data-ttu-id="64d98-134">Met deze opdracht wordt een `Show-Command` venster geopend voor de `Connect-PSSession` cmdlet.</span><span class="sxs-lookup"><span data-stu-id="64d98-134">This command opens a `Show-Command` window for the`Connect-PSSession`cmdlet.</span></span>

```powershell
Show-Command -Name "Connect-PSSession" -Height 700 -Width 1000 -ErrorPopup
```

<span data-ttu-id="64d98-135">De para meters **Height** en **width** geven de dimensie van het opdracht venster op.</span><span class="sxs-lookup"><span data-stu-id="64d98-135">The **Height** and **Width** parameters specify the dimension of the command window.</span></span> <span data-ttu-id="64d98-136">Met de para meter **ErrorPopup** wordt het venster met de fout opdracht weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="64d98-136">The **ErrorPopup** parameter displays the error command window.</span></span>

<span data-ttu-id="64d98-137">Wanneer u op **uitvoeren** klikt, `Connect-PSSession` wordt de opdracht uitgevoerd, net zoals wanneer u de `Connect-PSSession` opdracht op de opdracht regel hebt getypt.</span><span class="sxs-lookup"><span data-stu-id="64d98-137">When you click **Run**, the `Connect-PSSession` command runs, just as would if you typed the `Connect-PSSession` command at the command line.</span></span>

### <span data-ttu-id="64d98-138">Voor beeld 4: nieuwe standaard parameter waarden voor een cmdlet opgeven</span><span class="sxs-lookup"><span data-stu-id="64d98-138">Example 4: Specify new default parameter values for a cmdlet</span></span>

<span data-ttu-id="64d98-139">In dit voor beeld wordt de `$PSDefaultParameterValues` Automatische variabele gebruikt om nieuwe standaard waarden in te stellen voor de para meters **Height**, **width** en **ErrorPopup** van de `Show-Command` cmdlet.</span><span class="sxs-lookup"><span data-stu-id="64d98-139">This example uses the `$PSDefaultParameterValues` automatic variable to set new default values for the **Height**, **Width**, and **ErrorPopup** parameters of the `Show-Command` cmdlet.</span></span>

```powershell
$PSDefaultParameterValues = @{
    "Show-Command:Height" = 700
    "Show-Command:Width" = 1000
    "Show-Command:ErrorPopup" = $True
}
```

<span data-ttu-id="64d98-140">Wanneer u nu een `Show-Command` opdracht uitvoert, worden de nieuwe standaard waarden automatisch toegepast.</span><span class="sxs-lookup"><span data-stu-id="64d98-140">Now when you run a `Show-Command` command, the new defaults are applied automatically.</span></span> <span data-ttu-id="64d98-141">Als u deze standaard waarden in elke Power shell-sessie wilt gebruiken, voegt u de `$PSDefaultParameterValues` variabele toe aan uw Power shell-profiel.</span><span class="sxs-lookup"><span data-stu-id="64d98-141">To use these default values in every PowerShell session, add the `$PSDefaultParameterValues` variable to your PowerShell profile.</span></span> <span data-ttu-id="64d98-142">Zie [about_Profiles](../Microsoft.PowerShell.Core/About/about_Profiles.md) en [about_Parameters_Default_Values](../Microsoft.PowerShell.Core/About/about_Parameters_Default_Values.md)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="64d98-142">For more information, see [about_Profiles](../Microsoft.PowerShell.Core/About/about_Profiles.md) and [about_Parameters_Default_Values](../Microsoft.PowerShell.Core/About/about_Parameters_Default_Values.md).</span></span>

### <span data-ttu-id="64d98-143">Voor beeld 5: uitvoer naar een raster weergave verzenden</span><span class="sxs-lookup"><span data-stu-id="64d98-143">Example 5: Send output to a grid view</span></span>

<span data-ttu-id="64d98-144">Met deze opdracht wordt aangegeven hoe u `Show-Command` de `Out-GridView` cmdlets en samen gebruikt.</span><span class="sxs-lookup"><span data-stu-id="64d98-144">This command shows how to use the `Show-Command` and `Out-GridView` cmdlets together.</span></span>

```powershell
Show-Command Get-ChildItem | Out-GridView
```

<span data-ttu-id="64d98-145">De opdracht gebruikt de `Show-Command` cmdlet voor het openen van een opdracht venster voor de `Get-ChildItem` cmdlet.</span><span class="sxs-lookup"><span data-stu-id="64d98-145">The command uses the `Show-Command` cmdlet to open a command window for the`Get-ChildItem`cmdlet.</span></span>
<span data-ttu-id="64d98-146">Wanneer u op de knop **uitvoeren** klikt, `Get-ChildItem` wordt de opdracht uitgevoerd en wordt uitvoer gegenereerd.</span><span class="sxs-lookup"><span data-stu-id="64d98-146">When you click the **Run** button, the `Get-ChildItem` command runs and generates output.</span></span> <span data-ttu-id="64d98-147">De pijplijn operator (|) verzendt de uitvoer van de `Get-ChildItem` opdracht naar de `Out-GridView` cmdlet, waarmee de `Get-ChildItem` uitvoer in een interactief venster wordt weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="64d98-147">The pipeline operator ( | ) sends the output of the `Get-ChildItem` command to the `Out-GridView` cmdlet, which displays the `Get-ChildItem` output in an interactive window.</span></span>

### <span data-ttu-id="64d98-148">Voor beeld 6: een opdracht weer geven die u in het venster opdrachten hebt gemaakt</span><span class="sxs-lookup"><span data-stu-id="64d98-148">Example 6: Display a command that you create in the Commands window</span></span>

<span data-ttu-id="64d98-149">In dit voor beeld wordt de opdracht weer gegeven die u in het venster hebt gemaakt `Show-Command` .</span><span class="sxs-lookup"><span data-stu-id="64d98-149">This example shows the command that you created in the `Show-Command` window.</span></span> <span data-ttu-id="64d98-150">De opdracht maakt gebruik van de para meter **PassThru** , waarmee de `Show-Command` resultaten in een teken reeks worden geretourneerd.</span><span class="sxs-lookup"><span data-stu-id="64d98-150">The command uses the **PassThru** parameter, which returns the `Show-Command` results in a string.</span></span>

```powershell
Show-Command -PassThru
```

```Output
Get-EventLog -LogName "Windows PowerShell" -Newest 5
```

<span data-ttu-id="64d98-151">Als u bijvoorbeeld het `Show-Command` venster gebruikt om een opdracht te maken `Get-EventLog` die de vijf nieuwste gebeurtenissen in het gebeurtenis logboek van Windows Power shell ophaalt en vervolgens op **OK** klikt, retourneert de opdracht de hierboven weer gegeven uitvoer.</span><span class="sxs-lookup"><span data-stu-id="64d98-151">For example, if you use the `Show-Command` window to create a `Get-EventLog` command that gets the five newest events in the Windows PowerShell event log, and then click **OK**, the command returns the output shown above.</span></span> <span data-ttu-id="64d98-152">Het weer geven van de opdracht teken reeks helpt u bij het leren van Power shell.</span><span class="sxs-lookup"><span data-stu-id="64d98-152">Viewing the command string helps you learn PowerShell.</span></span>

### <span data-ttu-id="64d98-153">Voor beeld 7: een opdracht opslaan in een variabele</span><span class="sxs-lookup"><span data-stu-id="64d98-153">Example 7: Save a command to a variable</span></span>

<span data-ttu-id="64d98-154">In dit voor beeld ziet u hoe u de opdracht teken reeks uitvoert die wordt weer gegeven wanneer u de para meter **PassThru** van de `Show-Command` cmdlet gebruikt.</span><span class="sxs-lookup"><span data-stu-id="64d98-154">This example shows how to run the command string that you get when you use the **PassThru** parameter of the `Show-Command` cmdlet.</span></span> <span data-ttu-id="64d98-155">Met deze strategie kunt u de opdracht zien en gebruiken.</span><span class="sxs-lookup"><span data-stu-id="64d98-155">This strategy lets you see the command and use it.</span></span>

```powershell
$C = Show-Command -PassThru
$C
Invoke-Expression $C
```

```Output
Get-EventLog -LogName "PowerShell" -Newest 5

Index Time          EntryType   Source                 InstanceID Message
----- ----          ---------   ------                 ---------- -------
11520 Dec 16 16:37  Information Windows PowerShell            400 Engine state is changed from None to Available...
11519 Dec 16 16:37  Information Windows PowerShell            600 Provider "Variable" is Started. ...
11518 Dec 16 16:37  Information Windows PowerShell            600 Provider "Registry" is Started. ...
11517 Dec 16 16:37  Information Windows PowerShell            600 Provider "Function" is Started. ...
11516 Dec 16 16:37  Information Windows PowerShell            600 Provider "FileSystem" is Started. ...
```

<span data-ttu-id="64d98-156">Met de eerste opdracht wordt de para meter **PassThru** van de `Show-Command` cmdlet gebruikt en worden de resultaten van de opdracht in de `$C` variabele opgeslagen.</span><span class="sxs-lookup"><span data-stu-id="64d98-156">The first command uses the **PassThru** parameter of the `Show-Command` cmdlet and saves the results of the command in the `$C` variable.</span></span> <span data-ttu-id="64d98-157">In dit geval gebruiken we het `Show-Command` venster om een opdracht te maken `Get-EventLog` waarmee de vijf nieuwste gebeurtenissen in het gebeurtenis logboek van Windows Power shell worden opgehaald.</span><span class="sxs-lookup"><span data-stu-id="64d98-157">In this case, we use the `Show-Command` window to create a `Get-EventLog` command that gets the five newest events in the Windows PowerShell event log.</span></span> <span data-ttu-id="64d98-158">Wanneer u op **OK** klikt, `Show-Command` wordt de opdracht teken reeks geretourneerd die is opgeslagen in de `$C` variabele.</span><span class="sxs-lookup"><span data-stu-id="64d98-158">When you click **OK**, `Show-Command` returns the command string, which is saved in the `$C` variable.</span></span>

### <span data-ttu-id="64d98-159">Voor beeld 8: de uitvoer van een opdracht opslaan in een variabele</span><span class="sxs-lookup"><span data-stu-id="64d98-159">Example 8: Save the output of a command to a variable</span></span>

<span data-ttu-id="64d98-160">In dit voor beeld wordt de para meter **ErrorPopup** gebruikt om de uitvoer van een opdracht in een variabele op te slaan.</span><span class="sxs-lookup"><span data-stu-id="64d98-160">This example uses the **ErrorPopup** parameter to save the output of a command in a variable.</span></span>

```powershell
$P = Show-Command Get-Process -ErrorPopup
$P
```

```Output
Handles  NPM(K)    PM(K)      WS(K) VM(M)   CPU(s)     Id ProcessName
-------  ------    -----      ----- -----   ------     -- -----------
    473      33    94096     112532   709     2.06   4492 powershell
```

<span data-ttu-id="64d98-161">Naast het weer geven van fouten in een venster retourneert **ErrorPopup** de opdracht uitvoer naar de huidige opdracht, in plaats van een nieuwe opdracht te maken.</span><span class="sxs-lookup"><span data-stu-id="64d98-161">In addition to displaying errors in a window, **ErrorPopup** returns command output to the current command, instead of creating a new command.</span></span> <span data-ttu-id="64d98-162">Wanneer u deze opdracht uitvoert, `Show-Command` wordt het venster geopend.</span><span class="sxs-lookup"><span data-stu-id="64d98-162">When you run this command, the `Show-Command` window opens.</span></span> <span data-ttu-id="64d98-163">U kunt de venster functies gebruiken om parameter waarden in te stellen.</span><span class="sxs-lookup"><span data-stu-id="64d98-163">You can use the window features to set parameter values.</span></span> <span data-ttu-id="64d98-164">Als u de opdracht wilt uitvoeren, klikt u op de knop **uitvoeren** in het `Show-Command` venster.</span><span class="sxs-lookup"><span data-stu-id="64d98-164">To run the command, click the **Run** button in the `Show-Command` window.</span></span>

## <span data-ttu-id="64d98-165">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="64d98-165">PARAMETERS</span></span>

### <span data-ttu-id="64d98-166">-ErrorPopup</span><span class="sxs-lookup"><span data-stu-id="64d98-166">-ErrorPopup</span></span>

<span data-ttu-id="64d98-167">Geeft aan dat de cmdlet fouten weergeeft in een pop-upvenster, naast de weer gave op de opdracht regel.</span><span class="sxs-lookup"><span data-stu-id="64d98-167">Indicates that the cmdlet displays errors in a pop-up window, in addition to displaying them at the command line.</span></span> <span data-ttu-id="64d98-168">Wanneer een opdracht die in een venster wordt uitgevoerd, standaard `Show-Command` een fout genereert, wordt de fout alleen weer gegeven op de opdracht regel.</span><span class="sxs-lookup"><span data-stu-id="64d98-168">By default, when a command that is run in a `Show-Command` window generates an error, the error is displayed only at the command line.</span></span>

<span data-ttu-id="64d98-169">Wanneer u de opdracht uitvoert (met behulp van de knop **uitvoeren** in het `Show-Command` venster), retourneert de para meter **ErrorPopup** de opdracht resultaten naar de huidige opdracht, in plaats van de opdracht uit te voeren en de uitvoer te retour neren naar een nieuwe opdracht.</span><span class="sxs-lookup"><span data-stu-id="64d98-169">Also, when you run the command (by using the **Run** button in the `Show-Command` window), the **ErrorPopup** parameter returns the command results to the current command, instead of running the command and returning its output to a new command.</span></span> <span data-ttu-id="64d98-170">U kunt deze functie gebruiken om de opdracht resultaten in een variabele op te slaan.</span><span class="sxs-lookup"><span data-stu-id="64d98-170">You can use this feature to save the command results in a variable.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="64d98-171">-Hoogte</span><span class="sxs-lookup"><span data-stu-id="64d98-171">-Height</span></span>

<span data-ttu-id="64d98-172">Geeft de hoogte van het `Show-Command` venster in pixels.</span><span class="sxs-lookup"><span data-stu-id="64d98-172">Specifies the height of the `Show-Command` window in pixels.</span></span> <span data-ttu-id="64d98-173">Voer een waarde in tussen 300 en het aantal pixels in de scherm resolutie.</span><span class="sxs-lookup"><span data-stu-id="64d98-173">Enter a value between 300 and the number of pixels in the screen resolution.</span></span> <span data-ttu-id="64d98-174">Als de waarde te groot is om het opdracht venster weer te geven op het scherm, wordt `Show-Command` er een fout gegenereerd.</span><span class="sxs-lookup"><span data-stu-id="64d98-174">If the value is too large to display the command window on the screen, `Show-Command` generates an error.</span></span> <span data-ttu-id="64d98-175">De standaard hoogte is 600 pixels.</span><span class="sxs-lookup"><span data-stu-id="64d98-175">The default height is 600 pixels.</span></span> <span data-ttu-id="64d98-176">Voor een `Show-Command` opdracht die de para meter **name** bevat, is de standaard hoogte 300 pixels.</span><span class="sxs-lookup"><span data-stu-id="64d98-176">For a `Show-Command` command that includes the **Name** parameter, the default height is 300 pixels.</span></span>

```yaml
Type: System.Double
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="64d98-177">-Name</span><span class="sxs-lookup"><span data-stu-id="64d98-177">-Name</span></span>

<span data-ttu-id="64d98-178">Hiermee wordt een opdracht venster voor de opgegeven opdracht weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="64d98-178">Displays a command window for the specified command.</span></span> <span data-ttu-id="64d98-179">Voer de naam van één opdracht in, zoals de naam van een cmdlet, functie of CIM-opdracht.</span><span class="sxs-lookup"><span data-stu-id="64d98-179">Enter the name of one command, such as the name of a cmdlet, function, or CIM command.</span></span> <span data-ttu-id="64d98-180">Als u deze para meter weglaat, `Show-Command` wordt een opdracht venster weer gegeven met een lijst met alle Power shell-opdrachten in alle modules die op de computer zijn geïnstalleerd.</span><span class="sxs-lookup"><span data-stu-id="64d98-180">If you omit this parameter, `Show-Command` displays a command window that lists all of the PowerShell commands in all modules installed on the computer.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases: CommandName

Required: False
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="64d98-181">-NoCommonParameter</span><span class="sxs-lookup"><span data-stu-id="64d98-181">-NoCommonParameter</span></span>

<span data-ttu-id="64d98-182">Geeft aan dat deze cmdlet de sectie common para meters van de opdracht weergave weglaat.</span><span class="sxs-lookup"><span data-stu-id="64d98-182">Indicates that this cmdlet omits the Common Parameters section of the command display.</span></span> <span data-ttu-id="64d98-183">Standaard worden de algemene para meters weer gegeven in een uitbreidbaar gedeelte onder aan het opdracht venster.</span><span class="sxs-lookup"><span data-stu-id="64d98-183">By default, the Common Parameters appear in an expandable section at the bottom of the command window.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="64d98-184">-PassThru</span><span class="sxs-lookup"><span data-stu-id="64d98-184">-PassThru</span></span>

<span data-ttu-id="64d98-185">Retourneert een object dat het item vertegenwoordigt waarmee u werkt.</span><span class="sxs-lookup"><span data-stu-id="64d98-185">Returns an object representing the item with which you are working.</span></span> <span data-ttu-id="64d98-186">Deze cmdlet genereert standaard geen uitvoer.</span><span class="sxs-lookup"><span data-stu-id="64d98-186">By default, this cmdlet does not generate any output.</span></span> <span data-ttu-id="64d98-187">Als u de opdracht teken reeks wilt uitvoeren, kopieert en plakt u deze bij de opdracht prompt of slaat u deze op in een variabele en gebruikt `Invoke-Expression` u de cmdlet om de teken reeks in de variabele uit te voeren.</span><span class="sxs-lookup"><span data-stu-id="64d98-187">To run the command string, copy and paste it at the command prompt or save it in a variable and use the `Invoke-Expression` cmdlet to run the string in the variable.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="64d98-188">-Breedte</span><span class="sxs-lookup"><span data-stu-id="64d98-188">-Width</span></span>

<span data-ttu-id="64d98-189">Geeft de breedte van het `Show-Command` venster in pixels aan.</span><span class="sxs-lookup"><span data-stu-id="64d98-189">Specifies the width of the `Show-Command` window in pixels.</span></span> <span data-ttu-id="64d98-190">Voer een waarde in tussen 300 en het aantal pixels in de scherm resolutie.</span><span class="sxs-lookup"><span data-stu-id="64d98-190">Enter a value between 300 and the number of pixels in the screen resolution.</span></span> <span data-ttu-id="64d98-191">Als de waarde te groot is om het opdracht venster weer te geven op het scherm, wordt `Show-Command` er een fout gegenereerd.</span><span class="sxs-lookup"><span data-stu-id="64d98-191">If the value is too large to display the command window on the screen, `Show-Command` generates an error.</span></span> <span data-ttu-id="64d98-192">De standaard breedte is 300 pixels.</span><span class="sxs-lookup"><span data-stu-id="64d98-192">The default width is 300 pixels.</span></span>

```yaml
Type: System.Double
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="64d98-193">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="64d98-193">CommonParameters</span></span>

<span data-ttu-id="64d98-194">Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="64d98-194">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="64d98-195">Zie [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="64d98-195">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="64d98-196">INVOER</span><span class="sxs-lookup"><span data-stu-id="64d98-196">INPUTS</span></span>

### <span data-ttu-id="64d98-197">Geen</span><span class="sxs-lookup"><span data-stu-id="64d98-197">None</span></span>

<span data-ttu-id="64d98-198">U kunt geen pipe invoer naar `Show-Command` .</span><span class="sxs-lookup"><span data-stu-id="64d98-198">You cannot pipe input to `Show-Command`.</span></span>

## <span data-ttu-id="64d98-199">UITVOER</span><span class="sxs-lookup"><span data-stu-id="64d98-199">OUTPUTS</span></span>

### <span data-ttu-id="64d98-200">Geen, System. String, System. object</span><span class="sxs-lookup"><span data-stu-id="64d98-200">None, System.String, System.Object</span></span>

<span data-ttu-id="64d98-201">Wanneer u de para meter **PassThru** gebruikt, `Show-Command` wordt een opdracht reeks geretourneerd.</span><span class="sxs-lookup"><span data-stu-id="64d98-201">When you use the **PassThru** parameter, `Show-Command` returns a command string.</span></span> <span data-ttu-id="64d98-202">Wanneer u de para meter **ErrorPopup** gebruikt, `Show-Command` wordt de uitvoer van de opdracht (een wille keurig object) geretourneerd.</span><span class="sxs-lookup"><span data-stu-id="64d98-202">When you use the **ErrorPopup** parameter, `Show-Command` returns the command output (any object).</span></span> <span data-ttu-id="64d98-203">Anders `Show-Command` wordt er geen uitvoer gegenereerd.</span><span class="sxs-lookup"><span data-stu-id="64d98-203">Otherwise, `Show-Command` does not generate any output.</span></span>

## <span data-ttu-id="64d98-204">OPMERKINGEN</span><span class="sxs-lookup"><span data-stu-id="64d98-204">NOTES</span></span>

<span data-ttu-id="64d98-205">Deze cmdlet is alleen beschikbaar op Windows-platforms.</span><span class="sxs-lookup"><span data-stu-id="64d98-205">This cmdlet is only available on Windows platforms.</span></span>

<span data-ttu-id="64d98-206">`Show-Command` werkt niet in externe sessies.</span><span class="sxs-lookup"><span data-stu-id="64d98-206">`Show-Command` does not work in remote sessions.</span></span>

## <span data-ttu-id="64d98-207">GERELATEERDE KOPPELINGEN</span><span class="sxs-lookup"><span data-stu-id="64d98-207">RELATED LINKS</span></span>
