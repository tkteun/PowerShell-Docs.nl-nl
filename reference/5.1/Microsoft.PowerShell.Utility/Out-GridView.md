---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 10/28/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/out-gridview?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Out-GridView
ms.openlocfilehash: 473571aa73d9b9331545b80cb5949e7a83c26eff
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/07/2020
ms.locfileid: "93250391"
---
# <span data-ttu-id="27c59-103">Out-GridView</span><span class="sxs-lookup"><span data-stu-id="27c59-103">Out-GridView</span></span>

## <span data-ttu-id="27c59-104">SAMENVATTING</span><span class="sxs-lookup"><span data-stu-id="27c59-104">SYNOPSIS</span></span>
<span data-ttu-id="27c59-105">Hiermee wordt de uitvoer naar een interactieve tabel in een afzonderlijk venster verzonden.</span><span class="sxs-lookup"><span data-stu-id="27c59-105">Sends output to an interactive table in a separate window.</span></span>

## <span data-ttu-id="27c59-106">SYNTAXIS</span><span class="sxs-lookup"><span data-stu-id="27c59-106">SYNTAX</span></span>

### <span data-ttu-id="27c59-107">PassThru (standaard)</span><span class="sxs-lookup"><span data-stu-id="27c59-107">PassThru (Default)</span></span>

```
Out-GridView [-InputObject <PSObject>] [-Title <String>] [-PassThru] [<CommonParameters>]
```

### <span data-ttu-id="27c59-108">Wait</span><span class="sxs-lookup"><span data-stu-id="27c59-108">Wait</span></span>

```
Out-GridView [-InputObject <PSObject>] [-Title <String>] [-Wait] [<CommonParameters>]
```

### <span data-ttu-id="27c59-109">OutputMode</span><span class="sxs-lookup"><span data-stu-id="27c59-109">OutputMode</span></span>

```
Out-GridView [-InputObject <PSObject>] [-Title <String>] [-OutputMode <OutputModeOption>]
 [<CommonParameters>]
```

## <span data-ttu-id="27c59-110">BESCHRIJVING</span><span class="sxs-lookup"><span data-stu-id="27c59-110">DESCRIPTION</span></span>

<span data-ttu-id="27c59-111">De `Out-GridView` cmdlet verzendt de uitvoer van een opdracht naar een raster weergave venster waarin de uitvoer in een interactieve tabel wordt weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="27c59-111">The `Out-GridView` cmdlet sends the output from a command to a grid view window where the output is displayed in an interactive table.</span></span>

<span data-ttu-id="27c59-112">Omdat deze cmdlet een gebruikers interface vereist, werkt deze niet op Windows Server Core of Windows nano server.</span><span class="sxs-lookup"><span data-stu-id="27c59-112">Because this cmdlet requires a user interface, it does not work on Windows Server Core or Windows Nano Server.</span></span>

<span data-ttu-id="27c59-113">U kunt de volgende functies van de tabel gebruiken om uw gegevens te controleren:</span><span class="sxs-lookup"><span data-stu-id="27c59-113">You can use the following features of the table to examine your data:</span></span>

- <span data-ttu-id="27c59-114">Kolommen verbergen, weer geven en opnieuw ordenen</span><span class="sxs-lookup"><span data-stu-id="27c59-114">Hide, Show, and Reorder Columns</span></span>
- <span data-ttu-id="27c59-115">Rijen sorteren</span><span class="sxs-lookup"><span data-stu-id="27c59-115">Sort rows</span></span>
- <span data-ttu-id="27c59-116">Snelfilter</span><span class="sxs-lookup"><span data-stu-id="27c59-116">Quick Filter</span></span>
- <span data-ttu-id="27c59-117">Criteria filter toevoegen</span><span class="sxs-lookup"><span data-stu-id="27c59-117">Add Criteria Filter</span></span>
- <span data-ttu-id="27c59-118">Kopiëren en plakken</span><span class="sxs-lookup"><span data-stu-id="27c59-118">Copy and paste</span></span>

<span data-ttu-id="27c59-119">Zie de sectie [opmerkingen](#notes) van dit artikel voor volledige instructies.</span><span class="sxs-lookup"><span data-stu-id="27c59-119">For full instructions, see the [Notes](#notes) section of this article.</span></span>

## <span data-ttu-id="27c59-120">VOORBEELDEN</span><span class="sxs-lookup"><span data-stu-id="27c59-120">EXAMPLES</span></span>

### <span data-ttu-id="27c59-121">Voor beeld 1: uitvoer processen naar een raster weergave</span><span class="sxs-lookup"><span data-stu-id="27c59-121">Example 1: Output processes to a grid view</span></span>

<span data-ttu-id="27c59-122">In dit voor beeld worden de processen opgehaald die worden uitgevoerd op de lokale computer en verzonden naar een raster weergave venster.</span><span class="sxs-lookup"><span data-stu-id="27c59-122">This example gets the processes running on the local computer and sends them to a grid view window.</span></span>

```powershell
Get-Process | Out-GridView
```

### <span data-ttu-id="27c59-123">Voor beeld 2: een variabele gebruiken om processen uit te voeren naar een raster weergave</span><span class="sxs-lookup"><span data-stu-id="27c59-123">Example 2: Use a variable to output processes to a grid view</span></span>

<span data-ttu-id="27c59-124">In dit voor beeld worden ook de processen opgehaald die worden uitgevoerd op de lokale computer en verzonden naar een raster weergave venster.</span><span class="sxs-lookup"><span data-stu-id="27c59-124">This example also gets the processes running on the local computer and sends them to a grid view window.</span></span>

```powershell
$P = Get-Process
$P | Out-GridView
```

<span data-ttu-id="27c59-125">De uitvoer van de `Get-Process` cmdlet wordt opgeslagen in de `$P` variabele.</span><span class="sxs-lookup"><span data-stu-id="27c59-125">The output of the `Get-Process` cmdlet is saved in the `$P` variable.</span></span> <span data-ttu-id="27c59-126">Vervolgens `$P` wordt de pipet naar `Out-GridView` .</span><span class="sxs-lookup"><span data-stu-id="27c59-126">Then, `$P` is piped to `Out-GridView`.</span></span>

### <span data-ttu-id="27c59-127">Voor beeld 3: een geselecteerde eigenschap weer geven in een raster weergave</span><span class="sxs-lookup"><span data-stu-id="27c59-127">Example 3: Display a selected properties in a grid view</span></span>

<span data-ttu-id="27c59-128">In dit voor beeld worden geselecteerde eigenschappen van de actieve processen weer gegeven in een raster weergave.</span><span class="sxs-lookup"><span data-stu-id="27c59-128">This example displays selected properties of the running processes in a grid view.</span></span>

```powershell
Get-Process | Select-Object -Property Name, WorkingSet, PeakWorkingSet |
  Sort-Object -Property WorkingSet -Descending | Out-GridView
```

<span data-ttu-id="27c59-129">De uitvoer van `Get-Process` wordt piped om `Select-Object` de eigenschappen **name** , **workingset** en **PeakWorkingSet** te selecteren.</span><span class="sxs-lookup"><span data-stu-id="27c59-129">The output of `Get-Process` is piped to `Select-Object` to select the **Name** , **WorkingSet** , and **PeakWorkingSet** properties.</span></span> <span data-ttu-id="27c59-130">Een andere pijplijn operator verzendt de gefilterde objecten naar de `Sort-Object` cmdlet om ze in aflopende volg orde te sorteren op basis van de waarde van de eigenschap **workingset** .</span><span class="sxs-lookup"><span data-stu-id="27c59-130">Another pipeline operator sends the filtered objects to the `Sort-Object` cmdlet to sort them in descending order by the value of the **WorkingSet** property.</span></span>
<span data-ttu-id="27c59-131">Vervolgens worden de gesorteerde resultaten gepiped naar `Out-GridView` .</span><span class="sxs-lookup"><span data-stu-id="27c59-131">Then, the sorted results are piped to `Out-GridView`.</span></span> <span data-ttu-id="27c59-132">U kunt nu de functies van de raster weergave gebruiken om de gegevens te zoeken, te sorteren en te filteren.</span><span class="sxs-lookup"><span data-stu-id="27c59-132">You can now use the features of the grid view to search, sort, and filter the data.</span></span>

### <span data-ttu-id="27c59-133">Voor beeld 4: uitvoer opslaan in een variabele en vervolgens een raster weergave uitvoeren</span><span class="sxs-lookup"><span data-stu-id="27c59-133">Example 4: Save output to a variable, and then output a grid view</span></span>

<span data-ttu-id="27c59-134">In dit voor beeld wordt de cmdlet-uitvoer in een variabele opgeslagen en vervolgens verzonden naar `Out-GridView` .</span><span class="sxs-lookup"><span data-stu-id="27c59-134">This example saves cmdlet output in a variable then sends it to `Out-GridView`.</span></span>

```powershell
($A = Get-ChildItem -Path $PSHOME -Recurse) | Out-GridView
```

<span data-ttu-id="27c59-135">`Get-ChildItem` Hiermee worden alle bestanden in de installatie directory van Power shell en de bijbehorende submappen met de `$PSHOME` Automatische variabele opgehaald.</span><span class="sxs-lookup"><span data-stu-id="27c59-135">`Get-ChildItem` gets all the files in the PowerShell installation directory and its subdirectories using the the `$PSHOME` automatic variable.</span></span> <span data-ttu-id="27c59-136">De volg orde van de bewerkingen wordt door de haakjes in de opdracht ingesteld.</span><span class="sxs-lookup"><span data-stu-id="27c59-136">The parentheses in the command establish the order of operations.</span></span> <span data-ttu-id="27c59-137">Als gevolg hiervan wordt de uitvoer van de `Get-ChildItem` opdracht opgeslagen in de `$A` variabele voordat deze wordt verzonden naar `Out-GridView` .</span><span class="sxs-lookup"><span data-stu-id="27c59-137">As a result, the output from the `Get-ChildItem` command is saved in the `$A` variable before it is sent to `Out-GridView`.</span></span>

### <span data-ttu-id="27c59-138">Voor beeld 5: uitvoer processen voor een opgegeven computer naar een raster weergave</span><span class="sxs-lookup"><span data-stu-id="27c59-138">Example 5: Output processes for a specified computer to a grid view</span></span>

<span data-ttu-id="27c59-139">In dit voor beeld worden de processen weer gegeven die worden uitgevoerd op de Server01-computer in een raster weergave venster.</span><span class="sxs-lookup"><span data-stu-id="27c59-139">This example displays the processes that are running on the Server01 computer in a grid view window.</span></span>

```powershell
Get-Process -ComputerName "Server01" | ogv -Title "Processes - Server01"
```

<span data-ttu-id="27c59-140">De examle gebruikt `ogv` , de alias voor de `Out-GridView` cmdlet.</span><span class="sxs-lookup"><span data-stu-id="27c59-140">The examle uses `ogv`, which is the alias for the `Out-GridView` cmdlet.</span></span> <span data-ttu-id="27c59-141">De **title** para meter geeft de venster titel aan.</span><span class="sxs-lookup"><span data-stu-id="27c59-141">The **Title** parameter specifies the window title.</span></span>

### <span data-ttu-id="27c59-142">Voor beeld 6: uitvoer gegevens van externe computers naar een raster weergave</span><span class="sxs-lookup"><span data-stu-id="27c59-142">Example 6: Output data from remote computers to a grid view</span></span>

<span data-ttu-id="27c59-143">In dit voor beeld ziet u hoe gegevens worden verzonden die zijn verzameld van externe computers naar `Out-GridView` .</span><span class="sxs-lookup"><span data-stu-id="27c59-143">This example shows how to send data collected from remote computers to `Out-GridView`.</span></span>

```powershell
Invoke-Command -ComputerName S1, S2, S3 -ScriptBlock {Get-Culture} | Out-GridView
```

<span data-ttu-id="27c59-144">`Invoke-Command` wordt uitgevoerd `Get-Culture` op drie externe computers.</span><span class="sxs-lookup"><span data-stu-id="27c59-144">`Invoke-Command` runs `Get-Culture` on three remote computers.</span></span> <span data-ttu-id="27c59-145">De resulterende gegevens worden gepiped naar `Out-GridView` .</span><span class="sxs-lookup"><span data-stu-id="27c59-145">The resulting data is piped to `Out-GridView`.</span></span> <span data-ttu-id="27c59-146">U ziet dat het script blok dat wordt uitgevoerd op de externe computer, de `Out-GridView` opdracht niet bevat.</span><span class="sxs-lookup"><span data-stu-id="27c59-146">Notice that the script block that runs on the remote computer does not include the `Out-GridView` command.</span></span> <span data-ttu-id="27c59-147">Als dat het geval is, mislukt de opdracht wanneer er is geprobeerd een raster weergave venster te openen op elke externe computer.</span><span class="sxs-lookup"><span data-stu-id="27c59-147">If it did, the command would fail when it tried to open a grid view window on each of the remote computers.</span></span>

### <span data-ttu-id="27c59-148">Voor beeld 7: meerdere items door geven via `Out-GridView`</span><span class="sxs-lookup"><span data-stu-id="27c59-148">Example 7: Pass multiple items through `Out-GridView`</span></span>

<span data-ttu-id="27c59-149">In dit voor beeld kunt u meerdere processen selecteren in het `Out-GridView` venster.</span><span class="sxs-lookup"><span data-stu-id="27c59-149">This example lets you select multiple processes from the `Out-GridView` window.</span></span> <span data-ttu-id="27c59-150">De processen die u selecteert, worden door gegeven aan de `Export-Csv` opdracht en naar het `ProcessLog.csv` bestand geschreven.</span><span class="sxs-lookup"><span data-stu-id="27c59-150">The processes that you select are passed to the `Export-Csv` command and written to the `ProcessLog.csv` file.</span></span>

```powershell
Get-Process | Out-GridView -PassThru | Export-Csv -Path .\ProcessLog.csv
```

<span data-ttu-id="27c59-151">Met de para meter **PassThru** van `Out-GridView` kunt u meerdere items naar beneden verplaatsen in de pijp lijn.</span><span class="sxs-lookup"><span data-stu-id="27c59-151">The **PassThru** parameter of `Out-GridView` lets you send multiple items down the pipeline.</span></span> <span data-ttu-id="27c59-152">De para meter **PassThru** is gelijk aan het gebruik van de **Meervoudige** waarde van de para meter **OutputMode** .</span><span class="sxs-lookup"><span data-stu-id="27c59-152">The **PassThru** parameter is equivalent to using the **Multiple** value of the **OutputMode** parameter.</span></span>

### <span data-ttu-id="27c59-153">Voor beeld 8: een Windows-snelkoppeling maken naar `Out-GridView`</span><span class="sxs-lookup"><span data-stu-id="27c59-153">Example 8: Create a Windows shortcut to `Out-GridView`</span></span>

<span data-ttu-id="27c59-154">In dit voor beeld ziet u hoe u de **wait** -para meter van gebruikt `Out-GridView` om een Windows-snelkoppeling naar het venster te maken `Out-GridView` .</span><span class="sxs-lookup"><span data-stu-id="27c59-154">This example shows how to use the **Wait** parameter of `Out-GridView` to create a Windows shortcut to the `Out-GridView` window.</span></span>

```powershell
pwsh -Command "Get-Service | Out-GridView -Wait"
```

<span data-ttu-id="27c59-155">Deze opdracht regel kan worden gebruikt in een Windows-snelkoppeling.</span><span class="sxs-lookup"><span data-stu-id="27c59-155">This command line can be used in a Windows shortcut.</span></span> <span data-ttu-id="27c59-156">Zonder de **wait** -para meter wordt Power shell afgesloten zodra het `Out-GridView` venster is geopend, waardoor het `Out-GridView` venster bijna onmiddellijk wordt gesloten.</span><span class="sxs-lookup"><span data-stu-id="27c59-156">Without the **Wait** parameter, PowerShell would exit as soon as the `Out-GridView` window opened, which would close the `Out-GridView` window almost immediately.</span></span>

## <span data-ttu-id="27c59-157">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="27c59-157">PARAMETERS</span></span>

### <span data-ttu-id="27c59-158">-Input object</span><span class="sxs-lookup"><span data-stu-id="27c59-158">-InputObject</span></span>

<span data-ttu-id="27c59-159">Hiermee geeft u het object op dat door de cmdlet wordt geaccepteerd als invoer voor `Out-GridView` .</span><span class="sxs-lookup"><span data-stu-id="27c59-159">Specifies object that the cmdlet accepts as input for `Out-GridView`.</span></span>

<span data-ttu-id="27c59-160">Wanneer u de para meter **input object** gebruikt voor het verzenden van een verzameling objecten naar `Out-GridView` , `Out-GridView` behandelt de verzameling als één verzamelings object en wordt één rij met de verzameling weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="27c59-160">When you use the **InputObject** parameter to send a collection of objects to `Out-GridView`, `Out-GridView` treats the collection as one collection object, and it displays one row that represents the collection.</span></span> <span data-ttu-id="27c59-161">Als u wilt dat elk object in de verzameling wordt weer gegeven, gebruikt u een pijplijn operator (|) om objecten te verzenden naar `Out-GridView` .</span><span class="sxs-lookup"><span data-stu-id="27c59-161">To display the each object in the collection, use a pipeline operator (|) to send objects to `Out-GridView`.</span></span>

```yaml
Type: System.Management.Automation.PSObject
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="27c59-162">-OutputMode</span><span class="sxs-lookup"><span data-stu-id="27c59-162">-OutputMode</span></span>

<span data-ttu-id="27c59-163">Hiermee geeft u de items op die het interactieve venster de pijp lijn als invoer naar andere opdrachten verzendt.</span><span class="sxs-lookup"><span data-stu-id="27c59-163">Specifies the items that the interactive window sends down the pipeline as input to other commands.</span></span>
<span data-ttu-id="27c59-164">Deze cmdlet genereert standaard geen uitvoer.</span><span class="sxs-lookup"><span data-stu-id="27c59-164">By default, this cmdlet does not generate any output.</span></span> <span data-ttu-id="27c59-165">Als u items vanuit het interactieve venster omlaag wilt verzenden, klikt u om de items te selecteren en klikt u vervolgens op OK.</span><span class="sxs-lookup"><span data-stu-id="27c59-165">To send items from the interactive window down the pipeline, click to select the items and then click OK.</span></span>

<span data-ttu-id="27c59-166">De waarden van deze para meter bepalen hoeveel items u naar beneden kunt verzenden in de pijp lijn.</span><span class="sxs-lookup"><span data-stu-id="27c59-166">The values of this parameter determine how many items you can send down the pipeline.</span></span>

- <span data-ttu-id="27c59-167">Geen.</span><span class="sxs-lookup"><span data-stu-id="27c59-167">None.</span></span>  <span data-ttu-id="27c59-168">Geen items.</span><span class="sxs-lookup"><span data-stu-id="27c59-168">No items.</span></span> <span data-ttu-id="27c59-169">Dit is de standaardwaarde.</span><span class="sxs-lookup"><span data-stu-id="27c59-169">This is the default value.</span></span>
- <span data-ttu-id="27c59-170">Afzonderlijke.</span><span class="sxs-lookup"><span data-stu-id="27c59-170">Single.</span></span> <span data-ttu-id="27c59-171">Nul items of één item.</span><span class="sxs-lookup"><span data-stu-id="27c59-171">Zero items or one item.</span></span> <span data-ttu-id="27c59-172">Gebruik deze waarde wanneer de volgende opdracht slechts één invoer object kan aannemen.</span><span class="sxs-lookup"><span data-stu-id="27c59-172">Use this value when the next command can take only one input object.</span></span>
- <span data-ttu-id="27c59-173">Vermenigvuldig.</span><span class="sxs-lookup"><span data-stu-id="27c59-173">Multiple.</span></span> <span data-ttu-id="27c59-174">Nul, één of veel items.</span><span class="sxs-lookup"><span data-stu-id="27c59-174">Zero, one, or many items.</span></span> <span data-ttu-id="27c59-175">Gebruik deze waarde wanneer de volgende opdracht meerdere invoer objecten kan hebben.</span><span class="sxs-lookup"><span data-stu-id="27c59-175">Use this value when the next command can take multiple input objects.</span></span> <span data-ttu-id="27c59-176">Deze waarde is gelijk aan de **PassThru** -para meter.</span><span class="sxs-lookup"><span data-stu-id="27c59-176">This value is equivalent to the **Passthru** parameter.</span></span>

<span data-ttu-id="27c59-177">Deze para meter is geïntroduceerd in Windows Power Shell 3,0.</span><span class="sxs-lookup"><span data-stu-id="27c59-177">This parameter was introduced in Windows PowerShell 3.0.</span></span>

```yaml
Type: Microsoft.PowerShell.Commands.OutputModeOption
Parameter Sets: OutputMode
Aliases:
Accepted values: None, Single, Multiple

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="27c59-178">-PassThru</span><span class="sxs-lookup"><span data-stu-id="27c59-178">-PassThru</span></span>

<span data-ttu-id="27c59-179">Geeft aan dat de cmdlet items van het interactieve venster omlaag verzendt als invoer naar andere opdrachten.</span><span class="sxs-lookup"><span data-stu-id="27c59-179">Indicates that the cmdlet sends items from the interactive window down the pipeline as input to other commands.</span></span> <span data-ttu-id="27c59-180">Deze cmdlet genereert standaard geen uitvoer.</span><span class="sxs-lookup"><span data-stu-id="27c59-180">By default, this cmdlet does not generate any output.</span></span> <span data-ttu-id="27c59-181">Deze para meter is gelijk aan het gebruik van de **Meervoudige** waarde van de para meter **OutputMode** .</span><span class="sxs-lookup"><span data-stu-id="27c59-181">This parameter is equivalent to using the **Multiple** value of the **OutputMode** parameter.</span></span>

<span data-ttu-id="27c59-182">Als u items vanuit het interactieve venster omlaag wilt verzenden, klikt u om de items te selecteren en klikt u vervolgens op OK.</span><span class="sxs-lookup"><span data-stu-id="27c59-182">To send items from the interactive window down the pipeline, click to select the items and then click OK.</span></span> <span data-ttu-id="27c59-183">Shift-klikken en Ctrl-klikken worden ondersteund.</span><span class="sxs-lookup"><span data-stu-id="27c59-183">Shift-click and Ctrl-click are supported.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: PassThru
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="27c59-184">-Titel</span><span class="sxs-lookup"><span data-stu-id="27c59-184">-Title</span></span>

<span data-ttu-id="27c59-185">Hiermee geeft u de tekst op die wordt weer gegeven in de titel balk van het `Out-GridView` venster.</span><span class="sxs-lookup"><span data-stu-id="27c59-185">Specifies the text that appears in the title bar of the `Out-GridView` window.</span></span> <span data-ttu-id="27c59-186">De titel balk geeft standaard de opdracht weer die aanroept `Out-GridView` .</span><span class="sxs-lookup"><span data-stu-id="27c59-186">By default, the title bar displays the command that invokes `Out-GridView`.</span></span>

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

### <span data-ttu-id="27c59-187">-Wachten</span><span class="sxs-lookup"><span data-stu-id="27c59-187">-Wait</span></span>

<span data-ttu-id="27c59-188">Geeft aan dat de cmdlet de opdracht prompt onderdrukt en voor komt dat Windows Power shell wordt afgesloten totdat het `Out-GridView` venster is gesloten.</span><span class="sxs-lookup"><span data-stu-id="27c59-188">Indicates that the cmdlet suppresses the command prompt and prevents Windows PowerShell from closing until the `Out-GridView` window is closed.</span></span> <span data-ttu-id="27c59-189">De opdracht prompt wordt standaard weer gegeven wanneer het `Out-GridView` venster wordt geopend.</span><span class="sxs-lookup"><span data-stu-id="27c59-189">By default, the command prompt returns when the `Out-GridView` window opens.</span></span>

<span data-ttu-id="27c59-190">Met deze functie kunt u de `Out-GridView` cmdlets in Windows-snelkoppelingen gebruiken.</span><span class="sxs-lookup"><span data-stu-id="27c59-190">This feature lets you use the `Out-GridView` cmdlets in Windows shortcuts.</span></span> <span data-ttu-id="27c59-191">Wanneer `Out-GridView` wordt gebruikt in een snelkoppeling zonder de para meter **wait** , `Out-GridView` wordt het venster alleen weer gegeven voordat Power shell wordt gesloten.</span><span class="sxs-lookup"><span data-stu-id="27c59-191">When `Out-GridView` is used in a shortcut without the **Wait** parameter, the `Out-GridView` window appears only momentarily before PowerShell closes.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: Wait
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="27c59-192">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="27c59-192">CommonParameters</span></span>

<span data-ttu-id="27c59-193">Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="27c59-193">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="27c59-194">Zie [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="27c59-194">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="27c59-195">INVOER</span><span class="sxs-lookup"><span data-stu-id="27c59-195">INPUTS</span></span>

### <span data-ttu-id="27c59-196">System. Management. Automation. PSObject</span><span class="sxs-lookup"><span data-stu-id="27c59-196">System.Management.Automation.PSObject</span></span>

<span data-ttu-id="27c59-197">U kunt elk object verzenden naar deze cmdlet.</span><span class="sxs-lookup"><span data-stu-id="27c59-197">You can send any object to this cmdlet.</span></span>

## <span data-ttu-id="27c59-198">UITVOER</span><span class="sxs-lookup"><span data-stu-id="27c59-198">OUTPUTS</span></span>

### <span data-ttu-id="27c59-199">Geen</span><span class="sxs-lookup"><span data-stu-id="27c59-199">None</span></span>

<span data-ttu-id="27c59-200">Normaal gesp roken worden `Out-GridView` er geen objecten geretourneerd.</span><span class="sxs-lookup"><span data-stu-id="27c59-200">Normally, `Out-GridView` does not return any objects.</span></span> <span data-ttu-id="27c59-201">Wanneer u de para meter **PassThru** gebruikt, worden de objecten die de geselecteerde rijen vertegenwoordigen, geretourneerd naar de pijp lijn.</span><span class="sxs-lookup"><span data-stu-id="27c59-201">When using the **PassThru** parameter, the objects representing the selected rows are returned to the pipeline.</span></span>

## <span data-ttu-id="27c59-202">OPMERKINGEN</span><span class="sxs-lookup"><span data-stu-id="27c59-202">NOTES</span></span>

<span data-ttu-id="27c59-203">U kunt een externe opdracht niet gebruiken om een raster weergave venster op een andere computer te openen.</span><span class="sxs-lookup"><span data-stu-id="27c59-203">You cannot use a remote command to open a grid view window on another computer.</span></span>

<span data-ttu-id="27c59-204">De uitvoer van de opdracht die u verzendt `Out-GridView` , kan niet worden geformatteerd met de `Format` cmdlets, zoals `Format-Table` of `Format-Wide` cmdlets.</span><span class="sxs-lookup"><span data-stu-id="27c59-204">The command output that you send to `Out-GridView` cannot be formatted using the `Format` cmdlets, such as `Format-Table` or `Format-Wide` cmdlets.</span></span> <span data-ttu-id="27c59-205">Gebruik de cmdlet om eigenschappen te selecteren `Select-Object` .</span><span class="sxs-lookup"><span data-stu-id="27c59-205">To select properties, use the `Select-Object` cmdlet.</span></span>

<span data-ttu-id="27c59-206">Gedeserialiseerd uitvoer van externe opdrachten wordt mogelijk niet juist opgemaakt in het raster weergave venster.</span><span class="sxs-lookup"><span data-stu-id="27c59-206">Deserialized output from remote commands might not be formatted correctly in the grid view window.</span></span>

<span data-ttu-id="27c59-207">**Sneltoetsen voor**`Out-GridView`</span><span class="sxs-lookup"><span data-stu-id="27c59-207">**Keyboard Shortcuts for** `Out-GridView`</span></span>

|              <span data-ttu-id="27c59-208">Gebruik deze sleutel:</span><span class="sxs-lookup"><span data-stu-id="27c59-208">Use this key:</span></span>              |                                   <span data-ttu-id="27c59-209">Om deze actie uit te voeren:</span><span class="sxs-lookup"><span data-stu-id="27c59-209">To perform this action:</span></span>                                    |
| --------------------------------------- | -------------------------------------------------------------------------------------------- |
| <span data-ttu-id="27c59-210"><kbd>Tabbesturingselement</kbd></span><span class="sxs-lookup"><span data-stu-id="27c59-210"><kbd>Tab</kbd></span></span>                          | <span data-ttu-id="27c59-211">Verplaatst de cursor van het vak **filter** naar het menu **criteria toevoegen** aan de tabel en terug.</span><span class="sxs-lookup"><span data-stu-id="27c59-211">Moves the cursor from the **Filter** box to the **Add criteria** menu to the table and back.</span></span> |
| <span data-ttu-id="27c59-212"><kbd>Pijl-omhoog</kbd></span><span class="sxs-lookup"><span data-stu-id="27c59-212"><kbd>UpArrow</kbd></span></span>                      | <span data-ttu-id="27c59-213">Eén rij omhoog gaan.</span><span class="sxs-lookup"><span data-stu-id="27c59-213">Move up one row.</span></span> <span data-ttu-id="27c59-214">Verplaatst naar de kolom koppen van de eerste rij met gegevens.</span><span class="sxs-lookup"><span data-stu-id="27c59-214">Moves to column headers from first row of data.</span></span>                             |
| <span data-ttu-id="27c59-215"><kbd>DownArrow</kbd></span><span class="sxs-lookup"><span data-stu-id="27c59-215"><kbd>DownArrow</kbd></span></span>                    | <span data-ttu-id="27c59-216">Eén rij omlaag.</span><span class="sxs-lookup"><span data-stu-id="27c59-216">Move down one row.</span></span>                                                                           |
| <span data-ttu-id="27c59-217"><kbd>LeftArrow</kbd></span><span class="sxs-lookup"><span data-stu-id="27c59-217"><kbd>LeftArrow</kbd></span></span>                    | <span data-ttu-id="27c59-218">Ga in de rij met kolom koppen naar links en één kolom.</span><span class="sxs-lookup"><span data-stu-id="27c59-218">In column header row, move left one column.</span></span>                                                  |
| <span data-ttu-id="27c59-219"><kbd>RightArrow</kbd></span><span class="sxs-lookup"><span data-stu-id="27c59-219"><kbd>RightArrow</kbd></span></span>                   | <span data-ttu-id="27c59-220">Ga in de rij met kolom koppen naar de rechter kolom.</span><span class="sxs-lookup"><span data-stu-id="27c59-220">In column header row, move right one column.</span></span>                                                 |
| <span data-ttu-id="27c59-221"><kbd>ContextMenuKey</kbd></span><span class="sxs-lookup"><span data-stu-id="27c59-221"><kbd>ContextMenuKey</kbd></span></span>               | <span data-ttu-id="27c59-222">In rij met kolom koppen wordt de optie kolommen selecteren weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="27c59-222">In column header row, displays the Select Columns option.</span></span>                                    |
| <span data-ttu-id="27c59-223"><kbd>Enter</kbd> of <kbd>spatie balk</kbd></span><span class="sxs-lookup"><span data-stu-id="27c59-223"><kbd>Enter</kbd> or <kbd>Spacebar</kbd></span></span> | <span data-ttu-id="27c59-224">Sorteer kolom gegevens in rij met kolom koppen (wissel knop A-Z, Z-A).</span><span class="sxs-lookup"><span data-stu-id="27c59-224">In column header row, sort column data (toggle A-Z, Z-A).</span></span>                                    |

<span data-ttu-id="27c59-225">**De functies van het grid-weergave venster gebruiken**</span><span class="sxs-lookup"><span data-stu-id="27c59-225">**How to Use the Grid View Window Features**</span></span>

<span data-ttu-id="27c59-226">**Een kolom weer geven of verbergen:**</span><span class="sxs-lookup"><span data-stu-id="27c59-226">**To hide or show a column:**</span></span>

1. <span data-ttu-id="27c59-227">Klik met de rechter muisknop op een kolomkop en klik op **kolommen selecteren**.</span><span class="sxs-lookup"><span data-stu-id="27c59-227">Right-click any column header and click **Select Columns**.</span></span>
2. <span data-ttu-id="27c59-228">Gebruik in het dialoog venster **kolommen selecteren** de pijl toetsen om de kolommen tussen de geselecteerde kolommen te verplaatsen naar de vakken beschik bare kolommen.</span><span class="sxs-lookup"><span data-stu-id="27c59-228">In the **Select Columns** dialog box, use the arrow keys to move the columns between the Selected columns to the Available columns boxes.</span></span> <span data-ttu-id="27c59-229">Alleen kolommen in het vak **kolommen selecteren** worden weer gegeven in het raster weergave venster.</span><span class="sxs-lookup"><span data-stu-id="27c59-229">Only columns in the **Select Columns** box appear in the grid view window.</span></span>

<span data-ttu-id="27c59-230">**Volg orde van kolommen wijzigen:**</span><span class="sxs-lookup"><span data-stu-id="27c59-230">**To reorder columns:**</span></span>

<span data-ttu-id="27c59-231">U kunt kolommen naar de gewenste locatie slepen en neerzetten.</span><span class="sxs-lookup"><span data-stu-id="27c59-231">You can drag and drop columns into the desired location.</span></span> <span data-ttu-id="27c59-232">U kunt ook de volgende stappen uitvoeren:</span><span class="sxs-lookup"><span data-stu-id="27c59-232">Or use the following steps:</span></span>

1. <span data-ttu-id="27c59-233">Klik met de rechter muisknop op een kolomkop en klik op **kolommen selecteren**.</span><span class="sxs-lookup"><span data-stu-id="27c59-233">Right-click any column header and click **Select Columns**.</span></span>
2. <span data-ttu-id="27c59-234">Gebruik in het dialoog venster **kolommen selecteren** de knoppen **omhoog** en **omlaag** om de volg orde van de kolommen te wijzigen.</span><span class="sxs-lookup"><span data-stu-id="27c59-234">In the **Select Columns** dialog box, use the **Move up** and **Move down** buttons to reorder the columns.</span></span> <span data-ttu-id="27c59-235">De kolommen boven aan de lijst worden links van de kolommen aan de onderkant van de lijst weer gegeven in het raster weergave venster.</span><span class="sxs-lookup"><span data-stu-id="27c59-235">Columns at the top of the list appear to the left of columns at the bottom of the list in the grid view window.</span></span>

<span data-ttu-id="27c59-236">**Tabel gegevens sorteren**</span><span class="sxs-lookup"><span data-stu-id="27c59-236">**How to Sort Table Data**</span></span>

- <span data-ttu-id="27c59-237">Als u de gegevens wilt sorteren, klikt u op een kolomkop.</span><span class="sxs-lookup"><span data-stu-id="27c59-237">To sort the data, click a column header.</span></span>
- <span data-ttu-id="27c59-238">Als u de sorteer volgorde wilt wijzigen, klikt u nogmaals op de kolomkop.</span><span class="sxs-lookup"><span data-stu-id="27c59-238">To change the sort order, click the column header again.</span></span> <span data-ttu-id="27c59-239">Telkens wanneer u op dezelfde koptekst klikt, wisselt de sorteer volgorde tussen oplopend naar aflopende volg orde.</span><span class="sxs-lookup"><span data-stu-id="27c59-239">Each time you click the same header, the sort order toggles between ascending to descending order.</span></span> <span data-ttu-id="27c59-240">De huidige volg orde wordt aangegeven door een drie hoek in de kolomkop.</span><span class="sxs-lookup"><span data-stu-id="27c59-240">The current order is indicated by a triangle in the column header.</span></span>

<span data-ttu-id="27c59-241">**Tabel gegevens selecteren**</span><span class="sxs-lookup"><span data-stu-id="27c59-241">**How to Select Table Data**</span></span>

- <span data-ttu-id="27c59-242">Als u een rij wilt selecteren, selecteert u de rij of gebruikt u de pijl-omhoog of omlaag om naar de rij te navigeren.</span><span class="sxs-lookup"><span data-stu-id="27c59-242">To select a row, select the row or use the up or down arrow to navigate to the row.</span></span>
- <span data-ttu-id="27c59-243">Als u alle rijen wilt selecteren (met uitzonde ring van de veldnamenrij), drukt u op <kbd>CTRL</kbd> + <kbd>A</kbd>.</span><span class="sxs-lookup"><span data-stu-id="27c59-243">To select all rows (except for the header row), press <kbd>CTRL</kbd>+<kbd>A</kbd>.</span></span>
- <span data-ttu-id="27c59-244">Als u opeenvolgende rijen wilt selecteren, houdt u de <kbd>SHIFT</kbd> -toets ingedrukt en klikt u op de rijen of met de pijl toetsen.</span><span class="sxs-lookup"><span data-stu-id="27c59-244">To select consecutive rows, press and hold the <kbd>SHIFT</kbd> key while clicking the rows or using the arrow keys.</span></span>
- <span data-ttu-id="27c59-245">Als u niet-opeenvolgende rijen wilt selecteren, drukt u op de toets <kbd>CTRL</kbd> en klikt u op om een rij aan de selectie toe te voegen.</span><span class="sxs-lookup"><span data-stu-id="27c59-245">To select nonconsecutive rows, press the <kbd>CTRL</kbd> key and click to add a row to the selection.</span></span>
- <span data-ttu-id="27c59-246">U kunt geen kolommen selecteren en u kunt niet de gehele rij van de kolom kolomkop selecteren.</span><span class="sxs-lookup"><span data-stu-id="27c59-246">You cannot select columns, and you cannot select the entire column header row.</span></span>

<span data-ttu-id="27c59-247">**Rijen kopiëren**</span><span class="sxs-lookup"><span data-stu-id="27c59-247">**How to Copy Rows**</span></span>

- <span data-ttu-id="27c59-248">Als u een of meer rijen uit de tabel wilt kopiëren, selecteert u de rijen en drukt u vervolgens op CTRL + C.</span><span class="sxs-lookup"><span data-stu-id="27c59-248">To copy one or more rows from the table, select the rows and then press CTRL+C.</span></span>

  <span data-ttu-id="27c59-249">U kunt de gegevens in elk tekst-of spreadsheet programma plakken.</span><span class="sxs-lookup"><span data-stu-id="27c59-249">You can paste the data into any text or spreadsheet program.</span></span> <span data-ttu-id="27c59-250">U kunt geen kolommen of delen van rijen kopiëren en u kunt de rij met kolom koppen niet kopiëren.</span><span class="sxs-lookup"><span data-stu-id="27c59-250">You cannot copy columns or parts of rows and you cannot copy the column header row.</span></span>

<span data-ttu-id="27c59-251">**Zoeken in de tabel (snel filter)**</span><span class="sxs-lookup"><span data-stu-id="27c59-251">**How to Search in the Table (Quick Filter)**</span></span>

<span data-ttu-id="27c59-252">In het vak filteren kunt u gegevens in de tabel zoeken.</span><span class="sxs-lookup"><span data-stu-id="27c59-252">Use the Filter box to search for data in the table.</span></span> <span data-ttu-id="27c59-253">Wanneer u in het vak typt, worden alleen items die de getypte tekst bevatten, weer gegeven in de tabel.</span><span class="sxs-lookup"><span data-stu-id="27c59-253">When you type in the box, only items that include the typed text appear in the table.</span></span>

- <span data-ttu-id="27c59-254">Zoeken naar tekst.</span><span class="sxs-lookup"><span data-stu-id="27c59-254">Search for text.</span></span> <span data-ttu-id="27c59-255">Als u wilt zoeken naar tekst in de tabel, typt u in het vak Filter de tekst die u wilt zoeken.</span><span class="sxs-lookup"><span data-stu-id="27c59-255">To search for text in the table, in the Filter box, type the text to find.</span></span>
- <span data-ttu-id="27c59-256">Zoek naar meerdere woorden.</span><span class="sxs-lookup"><span data-stu-id="27c59-256">Search for multiple words.</span></span> <span data-ttu-id="27c59-257">Als u wilt zoeken naar meerdere woorden in de tabel, typt u de woorden gescheiden door spaties.</span><span class="sxs-lookup"><span data-stu-id="27c59-257">To search for multiple words in the table, type the words separated by spaces.</span></span> <span data-ttu-id="27c59-258">`Out-GridView` geeft rijen weer die alle woorden (logische en) bevatten.</span><span class="sxs-lookup"><span data-stu-id="27c59-258">`Out-GridView` displays rows that include all the words (logical AND).</span></span>
- <span data-ttu-id="27c59-259">Zoeken naar letterlijke woord groepen.</span><span class="sxs-lookup"><span data-stu-id="27c59-259">Search for literal phrases.</span></span> <span data-ttu-id="27c59-260">Als u wilt zoeken naar woord groepen die spaties of speciale tekens bevatten, plaatst u de tekst tussen aanhalings tekens.</span><span class="sxs-lookup"><span data-stu-id="27c59-260">To search for phrases that include spaces or special characters, enclose the phrase in quotation marks.</span></span> <span data-ttu-id="27c59-261">`Out-GridView` geeft rijen weer die een exacte overeenkomst voor de woord groep bevatten.</span><span class="sxs-lookup"><span data-stu-id="27c59-261">`Out-GridView` displays rows that include an exact match for the phrase.</span></span>
- <span data-ttu-id="27c59-262">Zoeken in kolommen.</span><span class="sxs-lookup"><span data-stu-id="27c59-262">Search in columns.</span></span> <span data-ttu-id="27c59-263">Als u tekst in een of meer kolommen wilt zoeken, gebruikt u de volgende indeling:</span><span class="sxs-lookup"><span data-stu-id="27c59-263">To search for text in one or more columns, use the following format:</span></span>

  `<column>:<text> [<column>:<text>] ...`

  <span data-ttu-id="27c59-264">Als u bijvoorbeeld ' net ' wilt vinden in de kolom **DisplayName** , typt u in het vak **filter** :</span><span class="sxs-lookup"><span data-stu-id="27c59-264">For example, to find "Net" in the **DisplayName** column, in the **Filter** box, type:</span></span>

  `displayname:net`

  <span data-ttu-id="27c59-265">Als u rijen met ' net ' wilt zoeken in de kolommen **DisplayName** en **name** , typt u in het vak **filter** :</span><span class="sxs-lookup"><span data-stu-id="27c59-265">To find rows with "Net" in the **DisplayName** and **Name** columns, in the **Filter** box, type:</span></span>

  `displayname:net name:net`

- <span data-ttu-id="27c59-266">Schakel de zoek opdracht uit.</span><span class="sxs-lookup"><span data-stu-id="27c59-266">Turn off search.</span></span> <span data-ttu-id="27c59-267">Als u de hele tabel opnieuw wilt weer geven, klikt u op de rode X knop in de rechter bovenhoek van het vak **filter** of verwijdert u de tekst uit het vak **filter** .</span><span class="sxs-lookup"><span data-stu-id="27c59-267">To display the entire table again, click the red X button in the top right corner of the **Filter** box or delete the text from the **Filter** box.</span></span>

<span data-ttu-id="27c59-268">**Criteria gebruiken om de tabel te filteren**</span><span class="sxs-lookup"><span data-stu-id="27c59-268">**Use Criteria to Filter the Table**</span></span>

<span data-ttu-id="27c59-269">U kunt regels of criteria gebruiken om te bepalen welke items in de tabel worden weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="27c59-269">You can use rules or criteria to determine which items are displayed in the table.</span></span> <span data-ttu-id="27c59-270">Items worden alleen weer gegeven wanneer ze voldoen aan de criteria die u hebt ingesteld.</span><span class="sxs-lookup"><span data-stu-id="27c59-270">Items appear only when they satisfy all the criteria that you establish.</span></span> <span data-ttu-id="27c59-271">De beschik bare criteria worden bepaald door de eigenschappen van de objecten die worden weer gegeven in het raster weergave venster en de .NET Framework typen van die eigenschappen.</span><span class="sxs-lookup"><span data-stu-id="27c59-271">The available criteria are determined by the properties of the objects displayed in the grid view window and the .NET Framework types of those properties.</span></span>

<span data-ttu-id="27c59-272">Elk criterium heeft de volgende indeling:</span><span class="sxs-lookup"><span data-stu-id="27c59-272">Each criterion has the following format:</span></span>

`<column> <operator> <value>`

<span data-ttu-id="27c59-273">De criteria voor verschillende eigenschappen zijn verbonden door **en**.</span><span class="sxs-lookup"><span data-stu-id="27c59-273">Criteria for different properties are connected by **AND**.</span></span> <span data-ttu-id="27c59-274">De criteria voor dezelfde eigenschap zijn verbonden door **of**.</span><span class="sxs-lookup"><span data-stu-id="27c59-274">Criteria for the same property are connected by **OR**.</span></span> <span data-ttu-id="27c59-275">U kunt de logische connectors niet wijzigen.</span><span class="sxs-lookup"><span data-stu-id="27c59-275">You cannot change the logical connectors.</span></span>

<span data-ttu-id="27c59-276">De criteria zijn alleen van invloed op de weer gave.</span><span class="sxs-lookup"><span data-stu-id="27c59-276">The criteria only affects the display.</span></span> <span data-ttu-id="27c59-277">Er worden geen items uit de tabel verwijderd.</span><span class="sxs-lookup"><span data-stu-id="27c59-277">It does not delete items from the table.</span></span>

<span data-ttu-id="27c59-278">**Criteria toevoegen**</span><span class="sxs-lookup"><span data-stu-id="27c59-278">**How to Add Criteria**</span></span>

1. <span data-ttu-id="27c59-279">Als u de menu knop **criteria toevoegen** wilt weer geven, klikt u op de Uitvouw pijl in de rechter bovenhoek van het venster.</span><span class="sxs-lookup"><span data-stu-id="27c59-279">To display the **Add criteria** menu button, in the upper right corner of the window, click the Expand arrow.</span></span>
2. <span data-ttu-id="27c59-280">Klik op de menu knop **criteria toevoegen** .</span><span class="sxs-lookup"><span data-stu-id="27c59-280">Click the **Add Criteria** menu button.</span></span>
3. <span data-ttu-id="27c59-281">Klik om kolommen (eigenschappen) te selecteren.</span><span class="sxs-lookup"><span data-stu-id="27c59-281">Click to select columns (properties).</span></span> <span data-ttu-id="27c59-282">U kunt een of meer eigenschappen selecteren.</span><span class="sxs-lookup"><span data-stu-id="27c59-282">You can select one or many properties.</span></span>
4. <span data-ttu-id="27c59-283">Wanneer u klaar bent met het selecteren van eigenschappen, klikt u op de knop **toevoegen** .</span><span class="sxs-lookup"><span data-stu-id="27c59-283">When you are finished selecting properties, click the **Add** button.</span></span>
5. <span data-ttu-id="27c59-284">Klik op **Annuleren** om de toevoegingen te annuleren.</span><span class="sxs-lookup"><span data-stu-id="27c59-284">To cancel the additions, click **Cancel**.</span></span>
6. <span data-ttu-id="27c59-285">Klik opnieuw op de knop **criteria toevoegen** om meer criteria toe te voegen.</span><span class="sxs-lookup"><span data-stu-id="27c59-285">To add more criteria, click the **Add Criteria** button again.</span></span>

<span data-ttu-id="27c59-286">**Een criterium bewerken**</span><span class="sxs-lookup"><span data-stu-id="27c59-286">**How to Edit a Criterion**</span></span>

- <span data-ttu-id="27c59-287">Als u een operator wilt wijzigen, klikt u op de waarde Blue operator en selecteert u vervolgens een andere operator in de vervolg keuzelijst.</span><span class="sxs-lookup"><span data-stu-id="27c59-287">To change an operator, click the blue operator value, and then select a different operator from the drop-down list.</span></span>
- <span data-ttu-id="27c59-288">Typ een waarde in het vak waarde om een waarde in te voeren of te wijzigen.</span><span class="sxs-lookup"><span data-stu-id="27c59-288">To enter or change a value, type a value in the value box.</span></span> <span data-ttu-id="27c59-289">Als u een ongeldige waarde opgeeft, wordt er een rond X-pictogram weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="27c59-289">If you enter a value that is not valid, a circular X icon appears.</span></span> <span data-ttu-id="27c59-290">Als u deze wilt verwijderen, wijzigt u de waarde.</span><span class="sxs-lookup"><span data-stu-id="27c59-290">To remove it, change the value.</span></span>
- <span data-ttu-id="27c59-291">Als u een **or** -instructie wilt maken, voegt u een criterium met dezelfde eigenschap toe.</span><span class="sxs-lookup"><span data-stu-id="27c59-291">To create an **OR** statement, add a criteria with the same property.</span></span>

<span data-ttu-id="27c59-292">**Criteria verwijderen**</span><span class="sxs-lookup"><span data-stu-id="27c59-292">**How to Delete Criteria**</span></span>

- <span data-ttu-id="27c59-293">Als u geselecteerde criteria wilt verwijderen, klikt u op de rode X naast elk criterium.</span><span class="sxs-lookup"><span data-stu-id="27c59-293">To delete selected criteria, click the red X beside each criterion.</span></span>
- <span data-ttu-id="27c59-294">Als u alle criteria wilt verwijderen, klikt u op de knop **Alles wissen** .</span><span class="sxs-lookup"><span data-stu-id="27c59-294">To delete all criteria, click the **Clear All** button.</span></span>

## <span data-ttu-id="27c59-295">GERELATEERDE KOPPELINGEN</span><span class="sxs-lookup"><span data-stu-id="27c59-295">RELATED LINKS</span></span>

[<span data-ttu-id="27c59-296">Out-file</span><span class="sxs-lookup"><span data-stu-id="27c59-296">Out-File</span></span>](Out-File.md)

[<span data-ttu-id="27c59-297">Out-Printer</span><span class="sxs-lookup"><span data-stu-id="27c59-297">Out-Printer</span></span>](Out-Printer.md)

[<span data-ttu-id="27c59-298">Out-teken reeks</span><span class="sxs-lookup"><span data-stu-id="27c59-298">Out-String</span></span>](Out-String.md)