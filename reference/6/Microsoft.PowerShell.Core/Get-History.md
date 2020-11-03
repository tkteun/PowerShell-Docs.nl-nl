---
external help file: System.Management.Automation.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 10/06/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/get-history?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-History
ms.openlocfilehash: 773e7e8d61e0f6158b4501b9c0b23826cbb10820
ms.sourcegitcommit: 1695df0d241c0390cac71a7401e61198fc6ff756
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/06/2020
ms.locfileid: "93251970"
---
# <span data-ttu-id="73144-103">Get-History</span><span class="sxs-lookup"><span data-stu-id="73144-103">Get-History</span></span>

## <span data-ttu-id="73144-104">SAMENVATTING</span><span class="sxs-lookup"><span data-stu-id="73144-104">SYNOPSIS</span></span>
<span data-ttu-id="73144-105">Hiermee wordt een lijst opgehaald met de opdrachten die tijdens de huidige sessie zijn ingevoerd.</span><span class="sxs-lookup"><span data-stu-id="73144-105">Gets a list of the commands entered during the current session.</span></span>

## <span data-ttu-id="73144-106">SYNTAXIS</span><span class="sxs-lookup"><span data-stu-id="73144-106">SYNTAX</span></span>

```
Get-History [[-Id] <Int64[]>] [[-Count] <Int32>] [<CommonParameters>]
```

## <span data-ttu-id="73144-107">BESCHRIJVING</span><span class="sxs-lookup"><span data-stu-id="73144-107">DESCRIPTION</span></span>

<span data-ttu-id="73144-108">Met de `Get-History` cmdlet krijgt u de sessie geschiedenis, dat wil zeggen, de lijst met opdrachten die tijdens de huidige sessie zijn ingevoerd.</span><span class="sxs-lookup"><span data-stu-id="73144-108">The `Get-History` cmdlet gets the session history, that is, the list of commands entered during the current session.</span></span>

<span data-ttu-id="73144-109">Power shell onderhoudt automatisch een geschiedenis van elke sessie.</span><span class="sxs-lookup"><span data-stu-id="73144-109">PowerShell automatically maintains a history of each session.</span></span> <span data-ttu-id="73144-110">Het aantal vermeldingen in de sessie geschiedenis wordt bepaald door de waarde van de `$MaximumHistoryCount` Voorkeurs variabele.</span><span class="sxs-lookup"><span data-stu-id="73144-110">The number of entries in the session history is determined by the value of the `$MaximumHistoryCount` preference variable.</span></span> <span data-ttu-id="73144-111">Met ingang van Windows Power Shell 3,0 is de standaard waarde `4096` .</span><span class="sxs-lookup"><span data-stu-id="73144-111">Beginning in Windows PowerShell 3.0, the default value is `4096`.</span></span> <span data-ttu-id="73144-112">Standaard worden geschiedenis bestanden opgeslagen in de hoofdmap, maar u kunt het bestand opslaan op elke locatie.</span><span class="sxs-lookup"><span data-stu-id="73144-112">By default, history files are saved in the home directory, but you can save the file in any location.</span></span> <span data-ttu-id="73144-113">Zie [about_History](About/about_History.md)voor meer informatie over de geschiedenis functies in Power shell.</span><span class="sxs-lookup"><span data-stu-id="73144-113">For more information about the history features in PowerShell, see [about_History](About/about_History.md).</span></span>

<span data-ttu-id="73144-114">De sessie geschiedenis wordt afzonderlijk beheerd vanaf de geschiedenis die wordt onderhouden door de **PSReadLine** -module.</span><span class="sxs-lookup"><span data-stu-id="73144-114">The session history is managed separately from the history maintained by the **PSReadLine** module.</span></span>
<span data-ttu-id="73144-115">Beide geschiedenissen zijn beschikbaar in sessies waarin **PSReadLine** wordt geladen.</span><span class="sxs-lookup"><span data-stu-id="73144-115">Both histories are available in sessions where **PSReadLine** is loaded.</span></span> <span data-ttu-id="73144-116">Deze cmdlet werkt alleen met de sessie geschiedenis.</span><span class="sxs-lookup"><span data-stu-id="73144-116">This cmdlet only works with the session history.</span></span> <span data-ttu-id="73144-117">Zie [about_PSReadLine](../PSReadLine/About/about_PSReadLine.md)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="73144-117">For more information see, [about_PSReadLine](../PSReadLine/About/about_PSReadLine.md).</span></span>

## <span data-ttu-id="73144-118">VOORBEELDEN</span><span class="sxs-lookup"><span data-stu-id="73144-118">EXAMPLES</span></span>

### <span data-ttu-id="73144-119">Voor beeld 1: de sessie geschiedenis ophalen</span><span class="sxs-lookup"><span data-stu-id="73144-119">Example 1: Get the session history</span></span>

<span data-ttu-id="73144-120">In dit voor beeld worden de vermeldingen in de sessie geschiedenis opgehaald.</span><span class="sxs-lookup"><span data-stu-id="73144-120">This example gets the entries in the session history.</span></span> <span data-ttu-id="73144-121">De standaard weergave toont elke opdracht en de bijbehorende ID, die de volg orde aangeeft waarin ze zijn uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="73144-121">The default display shows each command and its ID, which indicates the order in which they ran.</span></span>

```powershell
Get-History
```

### <span data-ttu-id="73144-122">Voor beeld 2: gegevens ophalen die een teken reeks bevatten</span><span class="sxs-lookup"><span data-stu-id="73144-122">Example 2: Get entries that include a string</span></span>

<span data-ttu-id="73144-123">In dit voor beeld worden gegevens in de opdracht geschiedenis met de teken reeks service opgehaald.</span><span class="sxs-lookup"><span data-stu-id="73144-123">This example gets entries in the command history that include the string service.</span></span> <span data-ttu-id="73144-124">Met de eerste opdracht worden alle vermeldingen in de sessie geschiedenis opgehaald.</span><span class="sxs-lookup"><span data-stu-id="73144-124">The first command gets all entries in the session history.</span></span> <span data-ttu-id="73144-125">De pijplijn operator ( `|` ) geeft de resultaten door aan de `Where-Object` cmdlet, waarmee alleen de opdrachten worden geselecteerd die service bevatten.</span><span class="sxs-lookup"><span data-stu-id="73144-125">The pipeline operator (`|`) passes the results to the `Where-Object` cmdlet, which selects only the commands that include service.</span></span>

```powershell
Get-History | Where-Object {$_.CommandLine -like "*Service*"}
```

### <span data-ttu-id="73144-126">Voor beeld 3: geschiedenis vermeldingen naar een specifieke ID exporteren</span><span class="sxs-lookup"><span data-stu-id="73144-126">Example 3: Export history entries up to a specific ID</span></span>

<span data-ttu-id="73144-127">In dit voor beeld worden de vijf meest recente geschiedenis vermeldingen opgehaald die eindigen op entry 7.</span><span class="sxs-lookup"><span data-stu-id="73144-127">This example gets the five most recent history entries ending with entry 7.</span></span> <span data-ttu-id="73144-128">Met de pijplijn operator wordt het resultaat door gegeven aan de `Export-Csv` cmdlet, die de geschiedenis opmaakt als tekst met scheidings tekens en opslaat in het History.csv bestand.</span><span class="sxs-lookup"><span data-stu-id="73144-128">The pipeline operator passes the result to the `Export-Csv` cmdlet, which formats the history as comma-separated text and saves it in the History.csv file.</span></span> <span data-ttu-id="73144-129">Het bestand bevat de gegevens die worden weer gegeven wanneer u de geschiedenis opmaakt als een lijst.</span><span class="sxs-lookup"><span data-stu-id="73144-129">The file includes the data that is displayed when you format the history as a list.</span></span> <span data-ttu-id="73144-130">Dit omvat de status en de begin-en eind tijd van de opdracht.</span><span class="sxs-lookup"><span data-stu-id="73144-130">This includes the status and start and end times of the command.</span></span>

```powershell
Get-History -ID 7 -Count 5 | Export-Csv History.csv
```

### <span data-ttu-id="73144-131">Voor beeld 4: de meest recente opdracht weer geven</span><span class="sxs-lookup"><span data-stu-id="73144-131">Example 4: Display the most recent command</span></span>

<span data-ttu-id="73144-132">In dit voor beeld wordt de laatste opdracht in de opdracht geschiedenis opgehaald.</span><span class="sxs-lookup"><span data-stu-id="73144-132">This example gets the last command in the command history.</span></span> <span data-ttu-id="73144-133">De laatste opdracht is de laatst ingevoerde opdracht.</span><span class="sxs-lookup"><span data-stu-id="73144-133">The last command is the most recently entered command.</span></span> <span data-ttu-id="73144-134">Met deze opdracht wordt de para meter **aantal** gebruikt om slechts één opdracht weer te geven.</span><span class="sxs-lookup"><span data-stu-id="73144-134">This command uses the **Count** parameter to display just one command.</span></span> <span data-ttu-id="73144-135">Standaard worden `Get-History` de meest recente opdrachten opgehaald.</span><span class="sxs-lookup"><span data-stu-id="73144-135">By default, `Get-History` gets the most recent commands.</span></span> <span data-ttu-id="73144-136">Deze opdracht kan worden afgekort tot ' h-c 1 ' en heeft hetzelfde effect als het drukken op de pijl toets.</span><span class="sxs-lookup"><span data-stu-id="73144-136">This command can be abbreviated to "h -c 1" and is equivalent to pressing the up-arrow key.</span></span>

```powershell
Get-History -Count 1
```

### <span data-ttu-id="73144-137">Voor beeld 5: alle eigenschappen van de vermeldingen in de geschiedenis weer geven</span><span class="sxs-lookup"><span data-stu-id="73144-137">Example 5: Display all the properties of the entries in the history</span></span>

<span data-ttu-id="73144-138">In dit voor beeld worden alle eigenschappen van vermeldingen in de sessie geschiedenis weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="73144-138">This example displays all of the properties of entries in the session history.</span></span> <span data-ttu-id="73144-139">De pijplijn operator geeft de resultaten van een `Get-History` opdracht door aan de `Format-List` cmdlet, waarin alle eigenschappen van elk geschiedenis item worden weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="73144-139">The pipeline operator passes the results of a `Get-History` command to the `Format-List` cmdlet, which displays all of the properties of each history entry.</span></span> <span data-ttu-id="73144-140">Dit omvat de ID, de status en de begin-en eind tijd van de opdracht.</span><span class="sxs-lookup"><span data-stu-id="73144-140">This includes the ID, status, and start and end times of the command.</span></span>

```powershell
Get-History | Format-List -Property *
```

## <span data-ttu-id="73144-141">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="73144-141">PARAMETERS</span></span>

### <span data-ttu-id="73144-142">-Aantal</span><span class="sxs-lookup"><span data-stu-id="73144-142">-Count</span></span>

<span data-ttu-id="73144-143">Hiermee geeft u het aantal van de meest recente geschiedenis vermeldingen op die met deze cmdlet worden opgehaald.</span><span class="sxs-lookup"><span data-stu-id="73144-143">Specifies the number of the most recent history entries that this cmdlet gets.</span></span> <span data-ttu-id="73144-144">Met standaard `Get-History` haalt alle vermeldingen in de sessie geschiedenis.</span><span class="sxs-lookup"><span data-stu-id="73144-144">By, default, `Get-History` gets all entries in the session history.</span></span> <span data-ttu-id="73144-145">Als u de para meters **Count** en **id** in een opdracht gebruikt, wordt de weer gave beëindigd met de opdracht die is opgegeven door de **id-** para meter.</span><span class="sxs-lookup"><span data-stu-id="73144-145">If you use both the **Count** and **Id** parameters in a command, the display ends with the command that is specified by the **Id** parameter.</span></span>

<span data-ttu-id="73144-146">In Windows Power Shell 2,0 worden standaard `Get-History` de 32 meest recente vermeldingen opgehaald.</span><span class="sxs-lookup"><span data-stu-id="73144-146">In Windows PowerShell 2.0, by default, `Get-History` gets the 32 most recent entries.</span></span>

```yaml
Type: System.Int32
Parameter Sets: (All)
Aliases:

Required: False
Position: 1
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="73144-147">-Id</span><span class="sxs-lookup"><span data-stu-id="73144-147">-Id</span></span>

<span data-ttu-id="73144-148">Hiermee geeft u een matrix met de Id's van vermeldingen in de sessie geschiedenis.</span><span class="sxs-lookup"><span data-stu-id="73144-148">Specifies an array of the IDs of entries in the session history.</span></span> <span data-ttu-id="73144-149">`Get-History` Hiermee worden alleen opgegeven vermeldingen opgehaald.</span><span class="sxs-lookup"><span data-stu-id="73144-149">`Get-History` gets only specified entries.</span></span> <span data-ttu-id="73144-150">Als u de para meters **id** en **aantal** in een opdracht gebruikt, worden `Get-History` de meest recente vermeldingen opgehaald die eindigen op de vermelding die is opgegeven door de **id-** para meter.</span><span class="sxs-lookup"><span data-stu-id="73144-150">If you use both the **Id** and **Count** parameters in a command, `Get-History` gets the most recent entries ending with the entry specified by the **Id** parameter.</span></span>

```yaml
Type: System.Int64[]
Parameter Sets: (All)
Aliases:

Required: False
Position: 0
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="73144-151">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="73144-151">CommonParameters</span></span>

<span data-ttu-id="73144-152">Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="73144-152">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="73144-153">Zie [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="73144-153">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="73144-154">INVOER</span><span class="sxs-lookup"><span data-stu-id="73144-154">INPUTS</span></span>

### <span data-ttu-id="73144-155">System. Int64</span><span class="sxs-lookup"><span data-stu-id="73144-155">System.Int64</span></span>

<span data-ttu-id="73144-156">U kunt een geschiedenis-ID door sluizen naar deze cmdlet.</span><span class="sxs-lookup"><span data-stu-id="73144-156">You can pipe a history ID to this cmdlet.</span></span>

## <span data-ttu-id="73144-157">UITVOER</span><span class="sxs-lookup"><span data-stu-id="73144-157">OUTPUTS</span></span>

### <span data-ttu-id="73144-158">Micro soft. Power shell. commands. HistoryInfo</span><span class="sxs-lookup"><span data-stu-id="73144-158">Microsoft.PowerShell.Commands.HistoryInfo</span></span>

<span data-ttu-id="73144-159">Met deze cmdlet wordt een geschiedenis object geretourneerd voor elk geschiedenis item dat wordt opgehaald.</span><span class="sxs-lookup"><span data-stu-id="73144-159">This cmdlet returns a history object for each history item that it gets.</span></span>

## <span data-ttu-id="73144-160">OPMERKINGEN</span><span class="sxs-lookup"><span data-stu-id="73144-160">NOTES</span></span>

<span data-ttu-id="73144-161">De sessie geschiedenis is een lijst met opdrachten die tijdens de sessie zijn ingevoerd.</span><span class="sxs-lookup"><span data-stu-id="73144-161">The session history is a list of the commands entered during the session.</span></span> <span data-ttu-id="73144-162">De sessie geschiedenis vertegenwoordigt de uitvoerings volgorde, de status en de begin-en eind tijd van de opdracht.</span><span class="sxs-lookup"><span data-stu-id="73144-162">The session history represents the run order, the status, and the start and end times of the command.</span></span> <span data-ttu-id="73144-163">Bij het invoeren van elke opdracht voegt Power shell deze toe aan de geschiedenis zodat u deze opnieuw kunt gebruiken.</span><span class="sxs-lookup"><span data-stu-id="73144-163">As you enter each command, PowerShell adds it to the history so that you can reuse it.</span></span> <span data-ttu-id="73144-164">Zie [about_History](About/about_History.md)voor meer informatie over de opdracht geschiedenis.</span><span class="sxs-lookup"><span data-stu-id="73144-164">For more information about the command history, see [about_History](About/about_History.md).</span></span>

<span data-ttu-id="73144-165">Vanaf Windows Power Shell 3,0 is de standaard waarde van de `$MaximumHistoryCount` Voorkeurs variabele `4096` .</span><span class="sxs-lookup"><span data-stu-id="73144-165">Starting in Windows PowerShell 3.0, the default value of the `$MaximumHistoryCount` preference variable is `4096`.</span></span> <span data-ttu-id="73144-166">In Windows Power Shell 2,0 is de standaard waarde `64` .</span><span class="sxs-lookup"><span data-stu-id="73144-166">In Windows PowerShell 2.0, the default value is `64`.</span></span> <span data-ttu-id="73144-167">Zie about_Preference_Variables voor meer informatie over de `$MaximumHistoryCount` variabele [about_Preference_Variables](About/about_Preference_Variables.md).</span><span class="sxs-lookup"><span data-stu-id="73144-167">For more information about the `$MaximumHistoryCount` variable, see [about_Preference_Variables](About/about_Preference_Variables.md).</span></span>

## <span data-ttu-id="73144-168">GERELATEERDE KOPPELINGEN</span><span class="sxs-lookup"><span data-stu-id="73144-168">RELATED LINKS</span></span>

[<span data-ttu-id="73144-169">Toevoegen-geschiedenis</span><span class="sxs-lookup"><span data-stu-id="73144-169">Add-History</span></span>](Add-History.md)

[<span data-ttu-id="73144-170">Wissen-geschiedenis</span><span class="sxs-lookup"><span data-stu-id="73144-170">Clear-History</span></span>](Clear-History.md)

[<span data-ttu-id="73144-171">Invoke-geschiedenis</span><span class="sxs-lookup"><span data-stu-id="73144-171">Invoke-History</span></span>](Invoke-History.md)

[<span data-ttu-id="73144-172">about_History</span><span class="sxs-lookup"><span data-stu-id="73144-172">about_History</span></span>](About/about_History.md)
