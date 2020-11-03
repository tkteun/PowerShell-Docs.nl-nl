---
external help file: System.Management.Automation.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 05/13/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/add-history?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Add-History
ms.openlocfilehash: 5dfb6c4024daa0efdf25ee2453427e34552bdb4a
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/07/2020
ms.locfileid: "93250971"
---
# <span data-ttu-id="57dd6-103">Add-History</span><span class="sxs-lookup"><span data-stu-id="57dd6-103">Add-History</span></span>

## <span data-ttu-id="57dd6-104">SAMENVATTING</span><span class="sxs-lookup"><span data-stu-id="57dd6-104">SYNOPSIS</span></span>
<span data-ttu-id="57dd6-105">Hiermee worden items toegevoegd aan de sessie geschiedenis.</span><span class="sxs-lookup"><span data-stu-id="57dd6-105">Appends entries to the session history.</span></span>

## <span data-ttu-id="57dd6-106">SYNTAXIS</span><span class="sxs-lookup"><span data-stu-id="57dd6-106">SYNTAX</span></span>

```
Add-History [[-InputObject] <PSObject[]>] [-Passthru] [<CommonParameters>]
```

## <span data-ttu-id="57dd6-107">BESCHRIJVING</span><span class="sxs-lookup"><span data-stu-id="57dd6-107">DESCRIPTION</span></span>

<span data-ttu-id="57dd6-108">De `Add-History` cmdlet voegt vermeldingen toe aan het einde van de sessie geschiedenis, dat wil zeggen, de lijst met opdrachten die tijdens de huidige sessie zijn ingevoerd.</span><span class="sxs-lookup"><span data-stu-id="57dd6-108">The `Add-History` cmdlet adds entries to the end of the session history, that is, the list of commands entered during the current session.</span></span>

<span data-ttu-id="57dd6-109">De sessie geschiedenis is een lijst met opdrachten die tijdens de sessie zijn ingevoerd.</span><span class="sxs-lookup"><span data-stu-id="57dd6-109">The session history is a list of the commands entered during the session.</span></span> <span data-ttu-id="57dd6-110">De sessie geschiedenis vertegenwoordigt de volg orde van de uitvoering, de status en de begin-en eind tijd van de opdracht.</span><span class="sxs-lookup"><span data-stu-id="57dd6-110">The session history represents the order of execution, the status, and the start and end times of the command.</span></span> <span data-ttu-id="57dd6-111">Bij het invoeren van elke opdracht voegt Power shell deze toe aan de geschiedenis zodat u deze opnieuw kunt gebruiken.</span><span class="sxs-lookup"><span data-stu-id="57dd6-111">As you enter each command, PowerShell adds it to the history so that you can reuse it.</span></span> <span data-ttu-id="57dd6-112">Zie [about_History](About/about_History.md)voor meer informatie over de sessie geschiedenis.</span><span class="sxs-lookup"><span data-stu-id="57dd6-112">For more information about the session history, see [about_History](About/about_History.md).</span></span>

<span data-ttu-id="57dd6-113">De sessie geschiedenis wordt afzonderlijk beheerd vanaf de geschiedenis die wordt onderhouden door de **PSReadLine** -module.</span><span class="sxs-lookup"><span data-stu-id="57dd6-113">The session history is managed separately from the history maintained by the **PSReadLine** module.</span></span>
<span data-ttu-id="57dd6-114">Beide geschiedenissen zijn beschikbaar in sessies waarin **PSReadLine** wordt geladen.</span><span class="sxs-lookup"><span data-stu-id="57dd6-114">Both histories are available in sessions where **PSReadLine** is loaded.</span></span> <span data-ttu-id="57dd6-115">Deze cmdlet werkt alleen met de sessie geschiedenis.</span><span class="sxs-lookup"><span data-stu-id="57dd6-115">This cmdlet only works with the session history.</span></span> <span data-ttu-id="57dd6-116">Zie [about_PSReadLine](../PSReadLine/About/about_PSReadLine.md)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="57dd6-116">For more information see, [about_PSReadLine](../PSReadLine/About/about_PSReadLine.md).</span></span>

<span data-ttu-id="57dd6-117">U kunt de `Get-History` cmdlet gebruiken om de opdrachten op te halen en door te geven aan `Add-History` , of u kunt de opdrachten exporteren naar een CSV-of XML-bestand, de opdrachten vervolgens importeren en het geïmporteerde bestand door geven aan `Add-History` .</span><span class="sxs-lookup"><span data-stu-id="57dd6-117">You can use the `Get-History` cmdlet to get the commands and pass them to `Add-History`, or you can export the commands to a CSV or XML file, then import the commands, and pass the imported file to `Add-History`.</span></span> <span data-ttu-id="57dd6-118">U kunt deze cmdlet gebruiken om specifieke opdrachten toe te voegen aan de geschiedenis of om één geschiedenis bestand te maken dat opdrachten uit meer dan één sessie bevat.</span><span class="sxs-lookup"><span data-stu-id="57dd6-118">You can use this cmdlet to add specific commands to the history or to create a single history file that includes commands from more than one session.</span></span>

## <span data-ttu-id="57dd6-119">VOORBEELDEN</span><span class="sxs-lookup"><span data-stu-id="57dd6-119">EXAMPLES</span></span>

### <span data-ttu-id="57dd6-120">Voor beeld 1: opdrachten toevoegen aan de geschiedenis van een andere sessie</span><span class="sxs-lookup"><span data-stu-id="57dd6-120">Example 1: Add commands to the history of a different session</span></span>

<span data-ttu-id="57dd6-121">In dit voor beeld worden de opdrachten die in één Power shell-sessie zijn getypt, toegevoegd aan de geschiedenis van een andere Power shell-sessie.</span><span class="sxs-lookup"><span data-stu-id="57dd6-121">This example add the commands typed in one PowerShell session to the history of a different PowerShell session.</span></span>

```powershell
Get-History | Export-Csv c:\testing\history.csv -IncludeTypeInformation
Import-Csv c:\testing\history.csv | Add-History
```

<span data-ttu-id="57dd6-122">De eerste opdracht haalt objecten op die de opdrachten in de geschiedenis vertegenwoordigen en exporteert deze naar het `History.csv` bestand.</span><span class="sxs-lookup"><span data-stu-id="57dd6-122">The first command gets objects representing the commands in the history and exports them to the `History.csv` file.</span></span>

<span data-ttu-id="57dd6-123">De tweede opdracht wordt op de opdracht regel van een andere sessie getypt.</span><span class="sxs-lookup"><span data-stu-id="57dd6-123">The second command is typed at the command line of a different session.</span></span> <span data-ttu-id="57dd6-124">De cmdlet wordt gebruikt `Import-Csv` om de objecten in het bestand te importeren `History.csv` .</span><span class="sxs-lookup"><span data-stu-id="57dd6-124">It uses the `Import-Csv` cmdlet to import the objects in the `History.csv` file.</span></span> <span data-ttu-id="57dd6-125">De pijplijn operator ( `|` ) geeft de objecten door aan de `Add-History` cmdlet, waarmee de objecten die de opdrachten in het bestand vertegenwoordigen, `History.csv` worden toegevoegd aan de huidige sessie geschiedenis.</span><span class="sxs-lookup"><span data-stu-id="57dd6-125">The pipeline operator (`|`) passes the objects to the `Add-History` cmdlet, which adds the objects representing the commands in the `History.csv` file to the current session history.</span></span>

### <span data-ttu-id="57dd6-126">Voor beeld 2: opdrachten importeren en uitvoeren</span><span class="sxs-lookup"><span data-stu-id="57dd6-126">Example 2: Import and run commands</span></span>

<span data-ttu-id="57dd6-127">In dit voor beeld worden opdrachten uit het `History.xml` bestand geïmporteerd, worden deze toegevoegd aan de huidige sessie geschiedenis en worden de opdrachten in de gecombineerde geschiedenis uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="57dd6-127">This example imports commands from the `History.xml` file, adds them to the current session history, and then runs the commands in the combined history.</span></span>

```powershell
Import-Clixml c:\temp\history.xml | Add-History -PassThru | ForEach-Object -Process {Invoke-History}
```

<span data-ttu-id="57dd6-128">Met de eerste opdracht wordt de `Import-Clixml` cmdlet gebruikt voor het importeren van een opdracht geschiedenis die naar het bestand is geëxporteerd `History.xml` .</span><span class="sxs-lookup"><span data-stu-id="57dd6-128">The first command uses the `Import-Clixml` cmdlet to import a command history that was exported to the `History.xml` file.</span></span> <span data-ttu-id="57dd6-129">De pijplijn operator geeft de opdrachten door aan de `Add-History` cmdlet, waarmee de opdrachten worden toegevoegd aan de huidige sessie geschiedenis.</span><span class="sxs-lookup"><span data-stu-id="57dd6-129">The pipeline operator passes the commands to the `Add-History` cmdlet, which adds the commands to the current session history.</span></span> <span data-ttu-id="57dd6-130">De **PassThru** para meter geeft de objecten weer die de toegevoegde opdrachten van de pijp lijn vertegenwoordigen.</span><span class="sxs-lookup"><span data-stu-id="57dd6-130">The **PassThru** parameter passes the objects representing the added commands down the pipeline.</span></span>

<span data-ttu-id="57dd6-131">De opdracht gebruikt vervolgens de `ForEach-Object` cmdlet om de `Invoke-History` opdracht toe te passen op elk van de opdrachten in de gecombineerde geschiedenis.</span><span class="sxs-lookup"><span data-stu-id="57dd6-131">The command then uses the `ForEach-Object` cmdlet to apply the `Invoke-History` command to each of the commands in the combined history.</span></span> <span data-ttu-id="57dd6-132">De `Invoke-History` opdracht wordt opgemaakt als een script blok tussen accolades ( `{}` ), zoals vereist door de **proces** parameter van de `ForEach-Object` cmdlet.</span><span class="sxs-lookup"><span data-stu-id="57dd6-132">The `Invoke-History` command is formatted as a script block, enclosed in braces (`{}`), as required by the **Process** parameter of the `ForEach-Object` cmdlet.</span></span>

### <span data-ttu-id="57dd6-133">Voor beeld 3: opdrachten in de geschiedenis toevoegen aan het einde van de geschiedenis</span><span class="sxs-lookup"><span data-stu-id="57dd6-133">Example 3: Add commands in the history to the end of the history</span></span>

<span data-ttu-id="57dd6-134">In dit voor beeld worden de eerste vijf opdrachten in de geschiedenis toegevoegd aan het einde van de geschiedenis lijst.</span><span class="sxs-lookup"><span data-stu-id="57dd6-134">This example adds the first five commands in the history to the end of the history list.</span></span>

```powershell
Get-History -Id 5 -Count 5 | Add-History
```

<span data-ttu-id="57dd6-135">De `Get-History` cmdlet haalt de vijf opdrachten op die eindigen op de opdracht 5.</span><span class="sxs-lookup"><span data-stu-id="57dd6-135">The `Get-History` cmdlet gets the five commands ending in command 5.</span></span> <span data-ttu-id="57dd6-136">De pipeline-operator geeft deze door aan de `Add-History` cmdlet, waarmee deze worden toegevoegd aan de huidige geschiedenis.</span><span class="sxs-lookup"><span data-stu-id="57dd6-136">The pipeline operator passes them to the `Add-History` cmdlet, which appends them to the current history.</span></span> <span data-ttu-id="57dd6-137">De `Add-History` opdracht bevat geen para meters, maar Power shell koppelt de objecten die worden door gegeven via de pijp lijn met de para meter **input object** van `Add-History` .</span><span class="sxs-lookup"><span data-stu-id="57dd6-137">The `Add-History` command does not include any parameters, but PowerShell associates the objects passed through the pipeline with the **InputObject** parameter of `Add-History`.</span></span>

### <span data-ttu-id="57dd6-138">Voor beeld 4: opdrachten in een CSV-bestand toevoegen aan de huidige geschiedenis</span><span class="sxs-lookup"><span data-stu-id="57dd6-138">Example 4: Add commands in a .csv file to the current history</span></span>

<span data-ttu-id="57dd6-139">In dit voor beeld worden de opdrachten in het `History.csv` bestand toegevoegd aan de geschiedenis van de huidige sessie.</span><span class="sxs-lookup"><span data-stu-id="57dd6-139">This example add the commands in the `History.csv` file to the current session history.</span></span>

```powershell
$a = Import-Csv c:\testing\history.csv
Add-History -InputObject $a -PassThru
```

<span data-ttu-id="57dd6-140">De `Import-Csv` cmdlet importeert de opdrachten in het `History.csv` bestand en slaat de inhoud op in de variabele `$a` .</span><span class="sxs-lookup"><span data-stu-id="57dd6-140">The `Import-Csv` cmdlet imports the commands in the `History.csv` file and store its contents in the variable `$a`.</span></span>

<span data-ttu-id="57dd6-141">De tweede opdracht gebruikt de `Add-History` cmdlet om de opdrachten toe te voegen `History.csv` aan de huidige sessie geschiedenis.</span><span class="sxs-lookup"><span data-stu-id="57dd6-141">The second command uses the `Add-History` cmdlet to add the commands from `History.csv` to the current session history.</span></span> <span data-ttu-id="57dd6-142">De para meter **input object** wordt gebruikt om de `$a` variabele en de para meter **PassThru** op te geven om een object te genereren dat wordt weer gegeven op de opdracht regel.</span><span class="sxs-lookup"><span data-stu-id="57dd6-142">It uses the **InputObject** parameter to specify the `$a` variable and the **PassThru** parameter to generate an object to display at the command line.</span></span> <span data-ttu-id="57dd6-143">Zonder de para meter **PassThru** wordt door de `Add-History` cmdlet geen uitvoer gegenereerd.</span><span class="sxs-lookup"><span data-stu-id="57dd6-143">Without the **PassThru** parameter, the `Add-History` cmdlet does not generate any output.</span></span>

### <span data-ttu-id="57dd6-144">Voor beeld 5: opdrachten in een XML-bestand toevoegen aan de huidige geschiedenis</span><span class="sxs-lookup"><span data-stu-id="57dd6-144">Example 5: Add commands in an .xml file to the current history</span></span>

<span data-ttu-id="57dd6-145">In dit voor beeld worden de opdrachten in het `history.xml` bestand toegevoegd aan de huidige sessie geschiedenis.</span><span class="sxs-lookup"><span data-stu-id="57dd6-145">This example adds the commands in the `history.xml` file to the current session history.</span></span>

```powershell
Add-History -InputObject (Import-Clixml c:\temp\history.xml)
```

<span data-ttu-id="57dd6-146">De **input object** para meter geeft de resultaten van de opdracht tussen haakjes naar de `Add-History` cmdlet.</span><span class="sxs-lookup"><span data-stu-id="57dd6-146">The **InputObject** parameter passes the results of the command in parentheses to the `Add-History` cmdlet.</span></span> <span data-ttu-id="57dd6-147">De opdracht tussen haakjes, die als eerste wordt uitgevoerd, importeert het `history.xml` bestand in Power shell.</span><span class="sxs-lookup"><span data-stu-id="57dd6-147">The command in parentheses, which is executed first, imports the `history.xml` file into PowerShell.</span></span> <span data-ttu-id="57dd6-148">De `Add-History` cmdlet voegt vervolgens de opdrachten in het bestand toe aan de sessie geschiedenis.</span><span class="sxs-lookup"><span data-stu-id="57dd6-148">The `Add-History` cmdlet then adds the commands in the file to the session history.</span></span>

## <span data-ttu-id="57dd6-149">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="57dd6-149">PARAMETERS</span></span>

### <span data-ttu-id="57dd6-150">-Input object</span><span class="sxs-lookup"><span data-stu-id="57dd6-150">-InputObject</span></span>

<span data-ttu-id="57dd6-151">Hiermee geeft u een matrix op met vermeldingen die aan de geschiedenis moeten worden toegevoegd als **HistoryInfo** -object aan de sessie geschiedenis.</span><span class="sxs-lookup"><span data-stu-id="57dd6-151">Specifies an array of entries to add to the history as **HistoryInfo** object to the session history.</span></span>
<span data-ttu-id="57dd6-152">U kunt deze para meter gebruiken om een **HistoryInfo** -object in te dienen, zoals de waarden die door de `Get-History` -, `Import-Clixml` -of-cmdlets worden geretourneerd `Import-Csv` `Add-History` .</span><span class="sxs-lookup"><span data-stu-id="57dd6-152">You can use this parameter to submit a **HistoryInfo** object, such as the ones that are returned by the `Get-History`, `Import-Clixml`, or `Import-Csv` cmdlets, to `Add-History`.</span></span>

```yaml
Type: System.Management.Automation.PSObject[]
Parameter Sets: (All)
Aliases:

Required: False
Position: 0
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="57dd6-153">-PassThru</span><span class="sxs-lookup"><span data-stu-id="57dd6-153">-Passthru</span></span>

<span data-ttu-id="57dd6-154">Geeft aan dat deze cmdlet een **HistoryInfo** -object voor elk geschiedenis item retourneert.</span><span class="sxs-lookup"><span data-stu-id="57dd6-154">Indicates that this cmdlet returns a **HistoryInfo** object for each history entry.</span></span> <span data-ttu-id="57dd6-155">Deze cmdlet genereert standaard geen uitvoer.</span><span class="sxs-lookup"><span data-stu-id="57dd6-155">By default, this cmdlet does not generate any output.</span></span>

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

### <span data-ttu-id="57dd6-156">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="57dd6-156">CommonParameters</span></span>

<span data-ttu-id="57dd6-157">Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="57dd6-157">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="57dd6-158">Zie [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="57dd6-158">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="57dd6-159">INVOER</span><span class="sxs-lookup"><span data-stu-id="57dd6-159">INPUTS</span></span>

### <span data-ttu-id="57dd6-160">Micro soft. Power shell. commands. HistoryInfo</span><span class="sxs-lookup"><span data-stu-id="57dd6-160">Microsoft.PowerShell.Commands.HistoryInfo</span></span>

<span data-ttu-id="57dd6-161">U kunt een **HistoryInfo** -object door sluizen naar deze cmdlet.</span><span class="sxs-lookup"><span data-stu-id="57dd6-161">You can pipe a **HistoryInfo** object to this cmdlet.</span></span>

## <span data-ttu-id="57dd6-162">UITVOER</span><span class="sxs-lookup"><span data-stu-id="57dd6-162">OUTPUTS</span></span>

### <span data-ttu-id="57dd6-163">Geen of Microsoft. Power shell. commands. HistoryInfo</span><span class="sxs-lookup"><span data-stu-id="57dd6-163">None or Microsoft.PowerShell.Commands.HistoryInfo</span></span>

<span data-ttu-id="57dd6-164">Met deze cmdlet wordt een **HistoryInfo** -object geretourneerd als u de para meter **PassThru** opgeeft.</span><span class="sxs-lookup"><span data-stu-id="57dd6-164">This cmdlet returns a **HistoryInfo** object if you specify the **PassThru** parameter.</span></span> <span data-ttu-id="57dd6-165">Anders wordt met deze cmdlet geen uitvoer gegenereerd.</span><span class="sxs-lookup"><span data-stu-id="57dd6-165">Otherwise, this cmdlet does not generate any output.</span></span>

## <span data-ttu-id="57dd6-166">OPMERKINGEN</span><span class="sxs-lookup"><span data-stu-id="57dd6-166">NOTES</span></span>

<span data-ttu-id="57dd6-167">De sessie geschiedenis is een lijst met de opdrachten die tijdens de sessie worden ingevoerd samen met de ID.</span><span class="sxs-lookup"><span data-stu-id="57dd6-167">The session history is a list of the commands entered during the session together with the ID.</span></span> <span data-ttu-id="57dd6-168">De sessie geschiedenis vertegenwoordigt de volg orde van de uitvoering, de status en de begin-en eind tijd van de opdracht.</span><span class="sxs-lookup"><span data-stu-id="57dd6-168">The session history represents the order of execution, the status, and the start and end times of the command.</span></span> <span data-ttu-id="57dd6-169">Bij het invoeren van elke opdracht voegt Power shell deze toe aan de geschiedenis zodat u deze opnieuw kunt gebruiken.</span><span class="sxs-lookup"><span data-stu-id="57dd6-169">As you enter each command, PowerShell adds it to the history so that you can reuse it.</span></span> <span data-ttu-id="57dd6-170">Zie [about_History](About/about_History.md)voor meer informatie over de sessie geschiedenis.</span><span class="sxs-lookup"><span data-stu-id="57dd6-170">For more information about the session history, see [about_History](About/about_History.md).</span></span>

<span data-ttu-id="57dd6-171">Als u de opdrachten die u aan de geschiedenis wilt toevoegen wilt opgeven, gebruikt u de para meter **input object** .</span><span class="sxs-lookup"><span data-stu-id="57dd6-171">To specify the commands to add to the history, use the **InputObject** parameter.</span></span> <span data-ttu-id="57dd6-172">De `Add-History` opdracht accepteert alleen **HistoryInfo** -objecten, zoals die voor elke opdracht door de cmdlet worden geretourneerd `Get-History` .</span><span class="sxs-lookup"><span data-stu-id="57dd6-172">The `Add-History` command accepts only **HistoryInfo** objects, such as those returned for each command by the `Get-History` cmdlet.</span></span> <span data-ttu-id="57dd6-173">U kunt het pad en de bestands naam of een lijst met opdrachten niet door geven.</span><span class="sxs-lookup"><span data-stu-id="57dd6-173">You cannot pass it a path and file name or a list of commands.</span></span>

<span data-ttu-id="57dd6-174">U kunt de para meter **input object** gebruiken om een bestand met **HistoryInfo** -objecten door te geven aan `Add-History` .</span><span class="sxs-lookup"><span data-stu-id="57dd6-174">You can use the **InputObject** parameter to pass a file of **HistoryInfo** objects to `Add-History`.</span></span> <span data-ttu-id="57dd6-175">Als u dit wilt doen, exporteert u de resultaten van een `Get-History` opdracht naar een bestand met behulp van de- `Export-Csv` of- `Export-Clixml` cmdlet en importeert u vervolgens het bestand met behulp van de- `Import-Csv` of- `Import-Clixml` cmdlets.</span><span class="sxs-lookup"><span data-stu-id="57dd6-175">To do so, export the results of a `Get-History` command to a file by using the `Export-Csv` or `Export-Clixml` cmdlet and then import the file by using the `Import-Csv` or `Import-Clixml` cmdlets.</span></span> <span data-ttu-id="57dd6-176">U kunt het bestand met geïmporteerde **HistoryInfo** -objecten vervolgens door geven aan de `Add-History` hand van een pijp lijn of een variabele.</span><span class="sxs-lookup"><span data-stu-id="57dd6-176">You can then pass the file of imported **HistoryInfo** objects to `Add-History` through a pipeline or in a variable.</span></span> <span data-ttu-id="57dd6-177">Zie de voor beelden voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="57dd6-177">For more information, see the examples.</span></span>

<span data-ttu-id="57dd6-178">Het bestand met **HistoryInfo** -objecten dat u doorgeeft aan de `Add-History` cmdlet moet het type gegevens, de kolom koppen en alle eigenschappen van de **HistoryInfo** -objecten bevatten.</span><span class="sxs-lookup"><span data-stu-id="57dd6-178">The file of **HistoryInfo** objects that you pass to the `Add-History` cmdlet must include the type information, column headings, and all of the properties of the **HistoryInfo** objects.</span></span> <span data-ttu-id="57dd6-179">Als u van plan bent om de objecten weer aan te geven, moet u `Add-History` niet de para meter **NoTypeInformation** van de `Export-Csv` cmdlet gebruiken en de type gegevens, kolom koppen of andere velden in het bestand niet verwijderen.</span><span class="sxs-lookup"><span data-stu-id="57dd6-179">If you intend to pass the objects back to `Add-History`, do not use the **NoTypeInformation** parameter of the `Export-Csv` cmdlet and do not delete the type information, column headings, or any fields in the file.</span></span>

<span data-ttu-id="57dd6-180">Als u de sessie geschiedenis wilt wijzigen, exporteert u de sessie naar een CSV-of XML-bestand, wijzigt u het bestand, importeert u het bestand en gebruikt u dit om het toe `Add-History` te voegen aan de huidige sessie geschiedenis.</span><span class="sxs-lookup"><span data-stu-id="57dd6-180">To modify the session history, export the session to a CSV or XML file, modify the file, import the file, and use `Add-History` to append it to the current session history.</span></span>

## <span data-ttu-id="57dd6-181">GERELATEERDE KOPPELINGEN</span><span class="sxs-lookup"><span data-stu-id="57dd6-181">RELATED LINKS</span></span>

[<span data-ttu-id="57dd6-182">Wissen-geschiedenis</span><span class="sxs-lookup"><span data-stu-id="57dd6-182">Clear-History</span></span>](Clear-History.md)

[<span data-ttu-id="57dd6-183">Get-geschiedenis</span><span class="sxs-lookup"><span data-stu-id="57dd6-183">Get-History</span></span>](Get-History.md)

[<span data-ttu-id="57dd6-184">Invoke-geschiedenis</span><span class="sxs-lookup"><span data-stu-id="57dd6-184">Invoke-History</span></span>](Invoke-History.md)

[<span data-ttu-id="57dd6-185">about_PSReadLine</span><span class="sxs-lookup"><span data-stu-id="57dd6-185">about_PSReadLine</span></span>](../PSReadLine/About/about_PSReadLine.md)

[<span data-ttu-id="57dd6-186">Get-PSReadLineOption</span><span class="sxs-lookup"><span data-stu-id="57dd6-186">Get-PSReadLineOption</span></span>](/powershell/module/psreadline/get-psreadlineoption)

[<span data-ttu-id="57dd6-187">Set-PSReadLineOption</span><span class="sxs-lookup"><span data-stu-id="57dd6-187">Set-PSReadLineOption</span></span>](/powershell/module/psreadline/set-psreadlineoption)
