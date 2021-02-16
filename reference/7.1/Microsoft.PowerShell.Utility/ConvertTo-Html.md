---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 08/10/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/convertto-html?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: ConvertTo-Html
ms.openlocfilehash: 1eade078765f93713da1f665e3ad6f062a1826d9
ms.sourcegitcommit: 9777152e026c47ba8d319593051416054cb62246
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 02/16/2021
ms.locfileid: "100529937"
---
# <span data-ttu-id="fcb8c-103">ConvertTo-Html</span><span class="sxs-lookup"><span data-stu-id="fcb8c-103">ConvertTo-Html</span></span>

## <span data-ttu-id="fcb8c-104">SAMENVATTING</span><span class="sxs-lookup"><span data-stu-id="fcb8c-104">SYNOPSIS</span></span>
<span data-ttu-id="fcb8c-105">Hiermee converteert u .NET-objecten naar HTML die kunnen worden weer gegeven in een webbrowser.</span><span class="sxs-lookup"><span data-stu-id="fcb8c-105">Converts .NET objects into HTML that can be displayed in a Web browser.</span></span>

## <span data-ttu-id="fcb8c-106">SYNTAXIS</span><span class="sxs-lookup"><span data-stu-id="fcb8c-106">SYNTAX</span></span>

### <span data-ttu-id="fcb8c-107">Pagina (standaard)</span><span class="sxs-lookup"><span data-stu-id="fcb8c-107">Page (Default)</span></span>

```
ConvertTo-Html [-InputObject <PSObject>] [[-Property] <Object[]>] [[-Body] <String[]>]
 [[-Head] <String[]>] [[-Title] <String>] [-As <String>] [-CssUri <Uri>] [-PostContent <String[]>]
 [-PreContent <String[]>] [-Meta <Hashtable>] [-Charset <String>] [-Transitional]
 [<CommonParameters>]
```

### <span data-ttu-id="fcb8c-108">Fragment</span><span class="sxs-lookup"><span data-stu-id="fcb8c-108">Fragment</span></span>

```
ConvertTo-Html [-InputObject <PSObject>] [[-Property] <Object[]>] [-As <String>] [-Fragment]
 [-PostContent <String[]>] [-PreContent <String[]>] [<CommonParameters>]
```

## <span data-ttu-id="fcb8c-109">BESCHRIJVING</span><span class="sxs-lookup"><span data-stu-id="fcb8c-109">DESCRIPTION</span></span>

<span data-ttu-id="fcb8c-110">`ConvertTo-Html`Met de cmdlet worden .net-objecten geconverteerd naar HTML die kan worden weer gegeven in een webbrowser.</span><span class="sxs-lookup"><span data-stu-id="fcb8c-110">The `ConvertTo-Html` cmdlet converts .NET objects into HTML that can be displayed in a Web browser.</span></span> <span data-ttu-id="fcb8c-111">U kunt deze cmdlet gebruiken om de uitvoer van een opdracht in een webpagina weer te geven.</span><span class="sxs-lookup"><span data-stu-id="fcb8c-111">You can use this cmdlet to display the output of a command in a Web page.</span></span>

<span data-ttu-id="fcb8c-112">U kunt de para meters van gebruiken `ConvertTo-Html` om object eigenschappen te selecteren, om een tabel-of lijst indeling op te geven, om de titel van de HTML-pagina op te geven, tekst voor en toe te voegen voor en na het object, en om alleen het tabel-of lijst fragment op te halen in plaats van een strikte DTD-pagina.</span><span class="sxs-lookup"><span data-stu-id="fcb8c-112">You can use the parameters of `ConvertTo-Html` to select object properties, to specify a table or list format, to specify the HTML page title, to add text before and after the object, and to return only the table or list fragment, instead of a strict DTD page.</span></span>

<span data-ttu-id="fcb8c-113">Wanneer u meerdere objecten indient naar `ConvertTo-Html` , maakt Power shell de tabel (of lijst) op basis van de eigenschappen van het eerste object dat u verzendt.</span><span class="sxs-lookup"><span data-stu-id="fcb8c-113">When you submit multiple objects to `ConvertTo-Html`, PowerShell creates the table (or list) based on the properties of the first object that you submit.</span></span> <span data-ttu-id="fcb8c-114">Als de resterende objecten niet beschikken over een van de opgegeven eigenschappen, is de waarde van de eigenschap van dat object een lege cel.</span><span class="sxs-lookup"><span data-stu-id="fcb8c-114">If the remaining objects do not have one of the specified properties, the property value of that object is an empty cell.</span></span> <span data-ttu-id="fcb8c-115">Als de resterende objecten extra eigenschappen hebben, worden deze eigenschaps waarden niet opgenomen in het bestand.</span><span class="sxs-lookup"><span data-stu-id="fcb8c-115">If the remaining objects have additional properties, those property values are not included in the file.</span></span>

## <span data-ttu-id="fcb8c-116">VOORBEELDEN</span><span class="sxs-lookup"><span data-stu-id="fcb8c-116">EXAMPLES</span></span>

### <span data-ttu-id="fcb8c-117">Voor beeld 1: een webpagina maken om de datum weer te geven</span><span class="sxs-lookup"><span data-stu-id="fcb8c-117">Example 1: Create a web page to display the date</span></span>

```powershell
ConvertTo-Html -InputObject (Get-Date)
```

<span data-ttu-id="fcb8c-118">Met deze opdracht maakt u een HTML-pagina waarop de eigenschappen van de huidige datum worden weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="fcb8c-118">This command creates an HTML page that displays the properties of the current date.</span></span> <span data-ttu-id="fcb8c-119">De para meter **input object** wordt gebruikt om de resultaten van een `Get-Date` opdracht bij de cmdlet in te dienen `ConvertTo-Html` .</span><span class="sxs-lookup"><span data-stu-id="fcb8c-119">It uses the **InputObject** parameter to submit the results of a `Get-Date` command to the `ConvertTo-Html` cmdlet.</span></span>

### <span data-ttu-id="fcb8c-120">Voor beeld 2: een webpagina maken voor het weer geven van Power shell-aliassen</span><span class="sxs-lookup"><span data-stu-id="fcb8c-120">Example 2: Create a web page to display PowerShell aliases</span></span>

```powershell
Get-Alias | ConvertTo-Html | Out-File aliases.htm
Invoke-Item aliases.htm
```

<span data-ttu-id="fcb8c-121">Met deze opdracht maakt u een HTML-pagina waarop de Power shell-aliassen in de huidige console worden weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="fcb8c-121">This command creates an HTML page that lists the PowerShell aliases in the current console.</span></span>

<span data-ttu-id="fcb8c-122">De opdracht gebruikt de `Get-Alias` cmdlet om de aliassen op te halen.</span><span class="sxs-lookup"><span data-stu-id="fcb8c-122">The command uses the `Get-Alias` cmdlet to get the aliases.</span></span> <span data-ttu-id="fcb8c-123">Er wordt gebruikgemaakt van de pijplijn operator ( `|` ) om de aliassen te verzenden naar de `ConvertTo-Html` cmdlet, waarmee de HTML-pagina wordt gemaakt.</span><span class="sxs-lookup"><span data-stu-id="fcb8c-123">It uses the pipeline operator (`|`) to send the aliases to the `ConvertTo-Html` cmdlet, which creates the HTML page.</span></span> <span data-ttu-id="fcb8c-124">De opdracht gebruikt ook de `Out-File` cmdlet om de HTML-code naar het `aliases.htm` bestand te verzenden.</span><span class="sxs-lookup"><span data-stu-id="fcb8c-124">The command also uses the `Out-File` cmdlet to send the HTML code to the `aliases.htm` file.</span></span>

### <span data-ttu-id="fcb8c-125">Voor beeld 3: een webpagina maken om Power shell-gebeurtenissen weer te geven</span><span class="sxs-lookup"><span data-stu-id="fcb8c-125">Example 3: Create a web page to display PowerShell events</span></span>

```powershell
Get-EventLog -LogName "Windows PowerShell" | ConvertTo-Html | Out-File pslog.htm
```

<span data-ttu-id="fcb8c-126">Met deze opdracht maakt u een HTML-pagina `pslog.htm` met de naam waarmee de gebeurtenissen in het Windows Power shell-gebeurtenis logboek op de lokale computer worden weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="fcb8c-126">This command creates an HTML page called `pslog.htm` that displays the events in the Windows PowerShell event log on the local computer.</span></span>

<span data-ttu-id="fcb8c-127">De cmdlet wordt gebruikt `Get-EventLog` om de gebeurtenissen in het Windows Power shell-logboek op te halen. vervolgens wordt de pijplijn operator ( `|` ) gebruikt om de gebeurtenissen te verzenden naar de `ConvertTo-Html` cmdlet.</span><span class="sxs-lookup"><span data-stu-id="fcb8c-127">It uses the `Get-EventLog` cmdlet to get the events in the Windows PowerShell log and then uses the pipeline operator (`|`) to send the events to the `ConvertTo-Html` cmdlet.</span></span> <span data-ttu-id="fcb8c-128">De opdracht gebruikt ook de `Out-File` cmdlet om de HTML-code naar het `pslog.htm` bestand te verzenden.</span><span class="sxs-lookup"><span data-stu-id="fcb8c-128">The command also uses the `Out-File` cmdlet to send the HTML code to the `pslog.htm` file.</span></span>

<span data-ttu-id="fcb8c-129">De opdracht gebruikt ook de `Out-File` cmdlet om de HTML-code naar het `pslog.htm` bestand te verzenden.</span><span class="sxs-lookup"><span data-stu-id="fcb8c-129">The command also uses the `Out-File` cmdlet to send the HTML code to the `pslog.htm` file.</span></span>

### <span data-ttu-id="fcb8c-130">Voor beeld 4: een webpagina maken om processen weer te geven</span><span class="sxs-lookup"><span data-stu-id="fcb8c-130">Example 4: Create a web page to display processes</span></span>

```powershell
Get-Process |
  ConvertTo-Html -Property Name, Path, Company -Title "Process Information" |
    Out-File proc.htm
Invoke-Item proc.htm
```

<span data-ttu-id="fcb8c-131">Met deze opdrachten maakt en opent u een HTML-pagina met een lijst met de naam, het pad en het bedrijf van de processen op de lokale computer.</span><span class="sxs-lookup"><span data-stu-id="fcb8c-131">These commands create and open an HTML page that lists the name, path, and company of the processes on the local computer.</span></span>

<span data-ttu-id="fcb8c-132">De eerste opdracht gebruikt de `Get-Process` cmdlet om objecten op te halen die de processen vertegenwoordigen die worden uitgevoerd op de computer.</span><span class="sxs-lookup"><span data-stu-id="fcb8c-132">The first command uses the `Get-Process` cmdlet to get objects that represent the processes running on the computer.</span></span> <span data-ttu-id="fcb8c-133">De opdracht maakt gebruik van de pijplijn operator ( `|` ) om de proces objecten naar de `ConvertTo-Html` cmdlet te verzenden.</span><span class="sxs-lookup"><span data-stu-id="fcb8c-133">The command uses the pipeline operator (`|`) to send the process objects to the `ConvertTo-Html` cmdlet.</span></span>

<span data-ttu-id="fcb8c-134">De opdracht gebruikt de para meter **Property** om drie eigenschappen te selecteren van de proces objecten die in de tabel moeten worden opgenomen.</span><span class="sxs-lookup"><span data-stu-id="fcb8c-134">The command uses the **Property** parameter to select three properties of the process objects to be included in the table.</span></span> <span data-ttu-id="fcb8c-135">De opdracht gebruikt de para meter **title** om een titel voor de HTML-pagina op te geven.</span><span class="sxs-lookup"><span data-stu-id="fcb8c-135">The command uses the **Title** parameter to specify a title for the HTML page.</span></span> <span data-ttu-id="fcb8c-136">De opdracht gebruikt ook de `Out-File` cmdlet om de resulterende HTML naar een bestand met de naam Proc.htm te verzenden.</span><span class="sxs-lookup"><span data-stu-id="fcb8c-136">The command also uses the `Out-File` cmdlet to send the resulting HTML to a file named Proc.htm.</span></span>

<span data-ttu-id="fcb8c-137">Met de tweede opdracht wordt de `Invoke-Item` cmdlet gebruikt om de `Proc.htm` in de standaard browser te openen.</span><span class="sxs-lookup"><span data-stu-id="fcb8c-137">The second command uses the `Invoke-Item` cmdlet to open the `Proc.htm` in the default browser.</span></span>

### <span data-ttu-id="fcb8c-138">Voor beeld 5: een webpagina maken voor het weer geven van service objecten</span><span class="sxs-lookup"><span data-stu-id="fcb8c-138">Example 5: Create a web page to display service objects</span></span>

```powershell
Get-Service | ConvertTo-Html -CssUri "test.css"
```

```Output
<!DOCTYPE html PUBLIC "-//W3C//DTD XHTML 1.0 Strict//EN"  "https://www.w3.org/TR/xhtml1/DTD/xhtml1-strict.dtd">
<html>
<head>
<title>HTML TABLE</title>
<link rel="stylesheet" type="text/css" href="test.css" />
...
```

<span data-ttu-id="fcb8c-139">Met deze opdracht maakt u een HTML-pagina van de service objecten die door de `Get-Service` cmdlet worden geretourneerd.</span><span class="sxs-lookup"><span data-stu-id="fcb8c-139">This command creates an HTML page of the service objects that the `Get-Service` cmdlet returns.</span></span> <span data-ttu-id="fcb8c-140">De opdracht gebruikt de para meter **CssUri** om een trapsgewijs opmaak model voor de HTML-pagina op te geven.</span><span class="sxs-lookup"><span data-stu-id="fcb8c-140">The command uses the **CssUri** parameter to specify a cascading style sheet for the HTML page.</span></span>

<span data-ttu-id="fcb8c-141">De para meter **CssUri** voegt een extra `<link rel="stylesheet" type="text/css" href="test.css">` tag toe aan de resulterende HTML.</span><span class="sxs-lookup"><span data-stu-id="fcb8c-141">The **CssUri** parameter adds an additional `<link rel="stylesheet" type="text/css" href="test.css">` tag to the resulting HTML.</span></span> <span data-ttu-id="fcb8c-142">Het kenmerk HREF in het label bevat de naam van het opmaak model.</span><span class="sxs-lookup"><span data-stu-id="fcb8c-142">The HREF attribute in the tag contains the name of the style sheet.</span></span>

### <span data-ttu-id="fcb8c-143">Voor beeld 6: een webpagina maken voor het weer geven van service objecten</span><span class="sxs-lookup"><span data-stu-id="fcb8c-143">Example 6: Create a web page to display service objects</span></span>

```powershell
Get-Service | ConvertTo-Html -As LIST | Out-File services.htm
```

<span data-ttu-id="fcb8c-144">Met deze opdracht maakt u een HTML-pagina van de service objecten die door de `Get-Service` cmdlet worden geretourneerd.</span><span class="sxs-lookup"><span data-stu-id="fcb8c-144">This command creates an HTML page of the service objects that the `Get-Service` cmdlet returns.</span></span> <span data-ttu-id="fcb8c-145">De opdracht gebruikt de **as** -para meter om een lijst indeling op te geven.</span><span class="sxs-lookup"><span data-stu-id="fcb8c-145">The command uses the **As** parameter to specify a list format.</span></span> <span data-ttu-id="fcb8c-146">De cmdlet `Out-File` verzendt de resulterende HTML naar het `Services.htm` bestand.</span><span class="sxs-lookup"><span data-stu-id="fcb8c-146">The cmdlet `Out-File` sends the resulting HTML to the `Services.htm` file.</span></span>

### <span data-ttu-id="fcb8c-147">Voor beeld 7: een webtabel maken voor de huidige datum</span><span class="sxs-lookup"><span data-stu-id="fcb8c-147">Example 7: Create a web table for the current date</span></span>

```powershell
Get-Date | ConvertTo-Html -Fragment
```

```Output
<table>
<colgroup>...</colgroup>
<tr><th>DisplayHint</th><th>DateTime</th><th>Date</th><th>Day</th><th>DayOfWeek</th><th>DayOfYear</th><th>Hour</th>
<th>Kind</th><th>Millisecond</th><th>Minute</th><th>Month</th><th>Second</th><th>Ticks</th><th>TimeOfDay</th><th>Year</th></tr>
<tr><td>DateTime</td><td>Monday, May 05, 2008 10:40:04 AM</td><td>5/5/2008 12:00:00 AM</td><td>5</td><td>Monday</td>
<td>126</td><td>10</td><td>Local</td><td>123</td><td>40</td><td>5</td><td>4</td><td>633455808041237213</td><td>10:40:04.12
37213</td><td>2008</td></tr>
</table>
```

<span data-ttu-id="fcb8c-148">Met deze opdracht wordt `ConvertTo-Html` een HTML-tabel van de huidige datum gegenereerd.</span><span class="sxs-lookup"><span data-stu-id="fcb8c-148">This command uses `ConvertTo-Html` to generate an HTML table of the current date.</span></span> <span data-ttu-id="fcb8c-149">De opdracht gebruikt de `Get-Date` cmdlet om de huidige datum op te halen.</span><span class="sxs-lookup"><span data-stu-id="fcb8c-149">The command uses the `Get-Date` cmdlet to get the current date.</span></span> <span data-ttu-id="fcb8c-150">Er wordt gebruikgemaakt van een pijplijn operator (|) om de resultaten naar de cmdlet te verzenden `ConvertTo-Html` .</span><span class="sxs-lookup"><span data-stu-id="fcb8c-150">It uses a pipeline operator (|) to send the results to the `ConvertTo-Html` cmdlet.</span></span>

<span data-ttu-id="fcb8c-151">De `ConvertTo-Html` opdracht bevat de **fragment** parameter, waarmee de uitvoer wordt beperkt tot een HTML-tabel.</span><span class="sxs-lookup"><span data-stu-id="fcb8c-151">The `ConvertTo-Html` command includes the **Fragment** parameter, which limits the output to an HTML table.</span></span> <span data-ttu-id="fcb8c-152">Als gevolg hiervan worden de andere elementen van een HTML-pagina, zoals de `<HEAD>` `<BODY>` Tags en wegge laten.</span><span class="sxs-lookup"><span data-stu-id="fcb8c-152">As a result, the other elements of an HTML page, such as the `<HEAD>` and `<BODY>` tags, are omitted.</span></span>

### <span data-ttu-id="fcb8c-153">Voor beeld 8: een webpagina maken om Power shell-gebeurtenissen weer te geven</span><span class="sxs-lookup"><span data-stu-id="fcb8c-153">Example 8: Create a web page to display PowerShell events</span></span>

```powershell
Get-EventLog -Log "Windows PowerShell" | ConvertTo-Html -Property id, level, task
```

<span data-ttu-id="fcb8c-154">Met deze opdracht wordt de `Get-EventLog` cmdlet gebruikt om gebeurtenissen van het Windows Power shell-gebeurtenis logboek op te halen.</span><span class="sxs-lookup"><span data-stu-id="fcb8c-154">This command uses the `Get-EventLog` cmdlet to get events from the Windows PowerShell event log.</span></span>

<span data-ttu-id="fcb8c-155">Er wordt een pijplijn operator ( `|` ) gebruikt om de gebeurtenissen te verzenden naar de `ConvertTo-Html` cmdlet, waarmee de gebeurtenissen worden geconverteerd naar een HTML-indeling.</span><span class="sxs-lookup"><span data-stu-id="fcb8c-155">It uses a pipeline operator (`|`) to send the events to the `ConvertTo-Html` cmdlet, which converts the events to HTML format.</span></span>

<span data-ttu-id="fcb8c-156">De `ConvertTo-Html` opdracht gebruikt de para meter **Property** om alleen de eigenschappen **id**, **niveau** en **Task** van de gebeurtenis te selecteren.</span><span class="sxs-lookup"><span data-stu-id="fcb8c-156">The `ConvertTo-Html` command uses the **Property** parameter to select only the **ID**, **Level**, and **Task** properties of the event.</span></span>

### <span data-ttu-id="fcb8c-157">Voor beeld 9: een webpagina maken om opgegeven services weer te geven</span><span class="sxs-lookup"><span data-stu-id="fcb8c-157">Example 9: Create a web page to display specified services</span></span>

```powershell
$htmlParams = @{
  Title = "Windows Services: Server01"
  Body = Get-Date
  PreContent = "<P>Generated by Corporate IT</P>"
  PostContent = "For details, contact Corporate IT."
}
Get-Service A* |
  ConvertTo-Html @htmlParams |
    Out-File Services.htm
Invoke-Item Services.htm
```

<span data-ttu-id="fcb8c-158">Met deze opdracht wordt een webpagina gemaakt en geopend waarop de services op de computer worden weer gegeven die beginnen met een. Het maakt gebruik van de para meters **titel**, **hoofd tekst** **, voor-en** **PostContent** van `ConvertTo-Html` om de uitvoer aan te passen.</span><span class="sxs-lookup"><span data-stu-id="fcb8c-158">This command creates and opens a Web page that displays the services on the computer that begin with A. It uses the **Title**, **Body**, **PreContent**, and **PostContent** parameters of `ConvertTo-Html` to customize the output.</span></span>

<span data-ttu-id="fcb8c-159">Het eerste deel van de opdracht gebruikt de `Get-Service` cmdlet om de services op de computer te verkrijgen die met een beginnen. De opdracht maakt gebruik van een pijplijn operator ( `|` ) om de resultaten naar de `ConvertTo-Html` cmdlet te verzenden.</span><span class="sxs-lookup"><span data-stu-id="fcb8c-159">The first part of the command uses the `Get-Service` cmdlet to get the services on the computer that begin with A. The command uses a pipeline operator (`|`) to send the results to the `ConvertTo-Html` cmdlet.</span></span> <span data-ttu-id="fcb8c-160">De opdracht gebruikt ook de `Out-File` cmdlet om de uitvoer naar het Services.htm-bestand te verzenden.</span><span class="sxs-lookup"><span data-stu-id="fcb8c-160">The command also uses the `Out-File` cmdlet to send the output to the Services.htm file.</span></span>

<span data-ttu-id="fcb8c-161">Een punt komma ( `;` ) eindigt de eerste opdracht en start een tweede opdracht, waarbij de `Invoke-Item` cmdlet wordt gebruikt om het bestand te openen `Services.htm` in de standaard browser.</span><span class="sxs-lookup"><span data-stu-id="fcb8c-161">A semicolon (`;`) ends the first command and starts a second command, which uses the `Invoke-Item` cmdlet to open the `Services.htm` file in the default browser.</span></span>

### <span data-ttu-id="fcb8c-162">Voor beeld 10: de meta-eigenschappen en charset van de HTML instellen</span><span class="sxs-lookup"><span data-stu-id="fcb8c-162">Example 10: Set the Meta properties and Charset of the HTML</span></span>

```powershell
Get-Service | ConvertTo-HTML -Meta @{
  refresh=10
  author="Author's Name"
  keywords="PowerShell, HTML, ConvertTo-HTML"
} -Charset "UTF-8"
```

<span data-ttu-id="fcb8c-163">Met deze opdracht wordt de HTML-code voor een webpagina gemaakt met de meta tags voor vernieuwen, auteur en tref woorden.</span><span class="sxs-lookup"><span data-stu-id="fcb8c-163">This command creates the HTML for a webpage with the meta tags for refresh, author, and keywords.</span></span>
<span data-ttu-id="fcb8c-164">De charset voor de pagina is ingesteld op UTF-8</span><span class="sxs-lookup"><span data-stu-id="fcb8c-164">The charset for the page is set to UTF-8</span></span>

### <span data-ttu-id="fcb8c-165">Voor beeld 11: de HTML instellen op XHTML-overgangs DTD</span><span class="sxs-lookup"><span data-stu-id="fcb8c-165">Example 11: Set the HTML to XHTML Transitional DTD</span></span>

```powershell
Get-Service | ConvertTo-HTML -Transitional
```

<span data-ttu-id="fcb8c-166">Met deze opdracht wordt het DOCTYPE van de geretourneerde HTML ingesteld op XHTML-overgangs DTD</span><span class="sxs-lookup"><span data-stu-id="fcb8c-166">This command sets the DOCTYPE of the returned HTML to XHTML Transitional DTD</span></span>

## <span data-ttu-id="fcb8c-167">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="fcb8c-167">PARAMETERS</span></span>

### <span data-ttu-id="fcb8c-168">-As</span><span class="sxs-lookup"><span data-stu-id="fcb8c-168">-As</span></span>

<span data-ttu-id="fcb8c-169">Bepaalt of het object wordt opgemaakt als een tabel of een lijst.</span><span class="sxs-lookup"><span data-stu-id="fcb8c-169">Determines whether the object is formatted as a table or a list.</span></span> <span data-ttu-id="fcb8c-170">Geldige waarden zijn **tabel** en **lijst**.</span><span class="sxs-lookup"><span data-stu-id="fcb8c-170">Valid values are **Table** and **List**.</span></span> <span data-ttu-id="fcb8c-171">De standaard waarde is **Table**.</span><span class="sxs-lookup"><span data-stu-id="fcb8c-171">The default value is **Table**.</span></span>

<span data-ttu-id="fcb8c-172">De **tabel** waarde genereert een HTML-tabel die overeenkomt met de indeling van de Power shell-tabel.</span><span class="sxs-lookup"><span data-stu-id="fcb8c-172">The **Table** value generates an HTML table that resembles the PowerShell table format.</span></span> <span data-ttu-id="fcb8c-173">In de rij met koppen worden de namen van eigenschappen weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="fcb8c-173">The header row displays the property names.</span></span> <span data-ttu-id="fcb8c-174">Elke tabelrij vertegenwoordigt een object en geeft de waarden van het object voor elke eigenschap.</span><span class="sxs-lookup"><span data-stu-id="fcb8c-174">Each table row represents an object and displays the object's values for each property.</span></span>

<span data-ttu-id="fcb8c-175">De **lijst** waarde genereert een HTML-tabel met twee kolommen voor elk object dat lijkt op de Power shell-lijst indeling.</span><span class="sxs-lookup"><span data-stu-id="fcb8c-175">The **List** value generates a two-column HTML table for each object that resembles the PowerShell list format.</span></span> <span data-ttu-id="fcb8c-176">In de eerste kolom wordt de naam van de eigenschap weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="fcb8c-176">The first column displays the property name.</span></span> <span data-ttu-id="fcb8c-177">De tweede kolom bevat de waarde van de eigenschap.</span><span class="sxs-lookup"><span data-stu-id="fcb8c-177">The second column displays the property value.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:
Accepted values: Table, List

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="fcb8c-178">-Hoofd tekst</span><span class="sxs-lookup"><span data-stu-id="fcb8c-178">-Body</span></span>

<span data-ttu-id="fcb8c-179">Hiermee geeft u de tekst op die moet worden toegevoegd na de openings `<BODY>` code.</span><span class="sxs-lookup"><span data-stu-id="fcb8c-179">Specifies the text to add after the opening `<BODY>` tag.</span></span> <span data-ttu-id="fcb8c-180">Standaard is er geen tekst op die positie.</span><span class="sxs-lookup"><span data-stu-id="fcb8c-180">By default, there is no text in that position.</span></span>

```yaml
Type: System.String[]
Parameter Sets: Page
Aliases:

Required: False
Position: 3
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="fcb8c-181">-Charset</span><span class="sxs-lookup"><span data-stu-id="fcb8c-181">-Charset</span></span>

<span data-ttu-id="fcb8c-182">Hiermee geeft u de tekst op die moet worden toegevoegd aan de openings `<charset>` code.</span><span class="sxs-lookup"><span data-stu-id="fcb8c-182">Specifies text to add to the opening `<charset>` tag.</span></span> <span data-ttu-id="fcb8c-183">Standaard is er geen tekst op die positie.</span><span class="sxs-lookup"><span data-stu-id="fcb8c-183">By default, there is no text in that position.</span></span>

<span data-ttu-id="fcb8c-184">Deze para meter is geïntroduceerd in Power shell 6,0.</span><span class="sxs-lookup"><span data-stu-id="fcb8c-184">This parameter was introduced in PowerShell 6.0.</span></span>

```yaml
Type: System.String
Parameter Sets: Page
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="fcb8c-185">-CssUri</span><span class="sxs-lookup"><span data-stu-id="fcb8c-185">-CssUri</span></span>

<span data-ttu-id="fcb8c-186">Hiermee geeft u de URI (Uniform Resource Identifier) van het trapsgewijze opmaak model (CSS) op dat wordt toegepast op het HTML-bestand.</span><span class="sxs-lookup"><span data-stu-id="fcb8c-186">Specifies the Uniform Resource Identifier (URI) of the cascading style sheet (CSS) that is applied to the HTML file.</span></span> <span data-ttu-id="fcb8c-187">De URI wordt opgenomen in een koppeling naar een opmaak model in de uitvoer.</span><span class="sxs-lookup"><span data-stu-id="fcb8c-187">The URI is included in a style sheet link in the output.</span></span>

```yaml
Type: System.Uri
Parameter Sets: Page
Aliases: cu, uri

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="fcb8c-188">-Fragment</span><span class="sxs-lookup"><span data-stu-id="fcb8c-188">-Fragment</span></span>

<span data-ttu-id="fcb8c-189">Genereert alleen een HTML-tabel.</span><span class="sxs-lookup"><span data-stu-id="fcb8c-189">Generates only an HTML table.</span></span> <span data-ttu-id="fcb8c-190">De tags HTML, HEAD, TITLE en BODY worden wegge laten.</span><span class="sxs-lookup"><span data-stu-id="fcb8c-190">The HTML, HEAD, TITLE, and BODY tags are omitted.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: Fragment
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="fcb8c-191">-Head</span><span class="sxs-lookup"><span data-stu-id="fcb8c-191">-Head</span></span>

<span data-ttu-id="fcb8c-192">Hiermee geeft u de inhoud van de `<HEAD>` tag.</span><span class="sxs-lookup"><span data-stu-id="fcb8c-192">Specifies the content of the `<HEAD>` tag.</span></span> <span data-ttu-id="fcb8c-193">De standaardwaarde is `<title\>HTML TABLE</title>`.</span><span class="sxs-lookup"><span data-stu-id="fcb8c-193">The default is `<title\>HTML TABLE</title>`.</span></span> <span data-ttu-id="fcb8c-194">Als u de para meter **Head** gebruikt, wordt de para meter **title** genegeerd.</span><span class="sxs-lookup"><span data-stu-id="fcb8c-194">If you use the **Head** parameter, the **Title** parameter is ignored.</span></span>

```yaml
Type: System.String[]
Parameter Sets: Page
Aliases:

Required: False
Position: 1
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="fcb8c-195">-Input object</span><span class="sxs-lookup"><span data-stu-id="fcb8c-195">-InputObject</span></span>

<span data-ttu-id="fcb8c-196">Hiermee geeft u de objecten op die in HTML moeten worden weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="fcb8c-196">Specifies the objects to be represented in HTML.</span></span> <span data-ttu-id="fcb8c-197">Voer een variabele in die de objecten bevat of typ een opdracht of expressie waarmee de objecten worden opgehaald.</span><span class="sxs-lookup"><span data-stu-id="fcb8c-197">Enter a variable that contains the objects or type a command or expression that gets the objects.</span></span>

<span data-ttu-id="fcb8c-198">Als u deze para meter gebruikt voor het indienen van meerdere objecten, zoals alle services op een computer, `ConvertTo-Html` wordt een tabel gemaakt waarin de eigenschappen van een verzameling of een matrix met objecten worden weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="fcb8c-198">If you use this parameter to submit multiple objects, such as all of the services on a computer, `ConvertTo-Html` creates a table that displays the properties of a collection or of an array of objects.</span></span> <span data-ttu-id="fcb8c-199">Als u een tabel van de afzonderlijke objecten wilt maken, gebruikt u de pijplijn operator om de objecten naar te sluizen `ConvertTo-Html` .</span><span class="sxs-lookup"><span data-stu-id="fcb8c-199">To create a table of the individual objects, use the pipeline operator to pipe the objects to `ConvertTo-Html`.</span></span>

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

### <span data-ttu-id="fcb8c-200">-Meta</span><span class="sxs-lookup"><span data-stu-id="fcb8c-200">-Meta</span></span>

<span data-ttu-id="fcb8c-201">Hiermee geeft u de tekst op die moet worden toegevoegd aan de openings `<meta>` code.</span><span class="sxs-lookup"><span data-stu-id="fcb8c-201">Specifies text to add to the opening `<meta>` tag.</span></span> <span data-ttu-id="fcb8c-202">Standaard is er geen tekst op die positie.</span><span class="sxs-lookup"><span data-stu-id="fcb8c-202">By default, there is no text in that position.</span></span>

<span data-ttu-id="fcb8c-203">Deze para meter is geïntroduceerd in Power shell 6,0.</span><span class="sxs-lookup"><span data-stu-id="fcb8c-203">This parameter was introduced in PowerShell 6.0.</span></span>

```yaml
Type: System.Collections.Hashtable
Parameter Sets: Page
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="fcb8c-204">-PostContent</span><span class="sxs-lookup"><span data-stu-id="fcb8c-204">-PostContent</span></span>

<span data-ttu-id="fcb8c-205">Geeft aan dat er tekst moet worden toegevoegd na de afsluitende `</TABLE>` tag.</span><span class="sxs-lookup"><span data-stu-id="fcb8c-205">Specifies text to add after the closing `</TABLE>` tag.</span></span> <span data-ttu-id="fcb8c-206">Standaard is er geen tekst op die positie.</span><span class="sxs-lookup"><span data-stu-id="fcb8c-206">By default, there is no text in that position.</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="fcb8c-207">-Precontent</span><span class="sxs-lookup"><span data-stu-id="fcb8c-207">-PreContent</span></span>

<span data-ttu-id="fcb8c-208">Hiermee geeft u de tekst die moet worden toegevoegd voor de openings `<TABLE>` code.</span><span class="sxs-lookup"><span data-stu-id="fcb8c-208">Specifies text to add before the opening `<TABLE>` tag.</span></span> <span data-ttu-id="fcb8c-209">Standaard is er geen tekst op die positie.</span><span class="sxs-lookup"><span data-stu-id="fcb8c-209">By default, there is no text in that position.</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="fcb8c-210">-Eigenschap</span><span class="sxs-lookup"><span data-stu-id="fcb8c-210">-Property</span></span>

<span data-ttu-id="fcb8c-211">Bevat de opgegeven eigenschappen van de objecten in de HTML.</span><span class="sxs-lookup"><span data-stu-id="fcb8c-211">Includes the specified properties of the objects in the HTML.</span></span> <span data-ttu-id="fcb8c-212">De waarde van de **eigenschaps** parameter kan een nieuwe berekende eigenschap zijn.</span><span class="sxs-lookup"><span data-stu-id="fcb8c-212">The value of the **Property** parameter can be a new calculated property.</span></span> <span data-ttu-id="fcb8c-213">De berekende eigenschap kan een script blok of een hash-tabel zijn.</span><span class="sxs-lookup"><span data-stu-id="fcb8c-213">The calculated property can be a script block or a hash table.</span></span> <span data-ttu-id="fcb8c-214">Geldige sleutel-waardeparen zijn:</span><span class="sxs-lookup"><span data-stu-id="fcb8c-214">Valid key-value pairs are:</span></span>

- <span data-ttu-id="fcb8c-215">Naam (of label): `<string>` (toegevoegd in Power shell 6. x)</span><span class="sxs-lookup"><span data-stu-id="fcb8c-215">Name (or label) - `<string>` (added in PowerShell 6.x)</span></span>
- <span data-ttu-id="fcb8c-216">Expressie- `<string>` of `<script block>`</span><span class="sxs-lookup"><span data-stu-id="fcb8c-216">Expression - `<string>` or `<script block>`</span></span>
- <span data-ttu-id="fcb8c-217">Tring `<string>`</span><span class="sxs-lookup"><span data-stu-id="fcb8c-217">FormatString - `<string>`</span></span>
- <span data-ttu-id="fcb8c-218">Breedte: `<int32>` moet groter zijn dan `0`</span><span class="sxs-lookup"><span data-stu-id="fcb8c-218">Width - `<int32>` - must be greater than `0`</span></span>
- <span data-ttu-id="fcb8c-219">Uitlijning-waarde kan `Left` , `Center` of `Right`</span><span class="sxs-lookup"><span data-stu-id="fcb8c-219">Alignment - value can be `Left`, `Center`, or `Right`</span></span>

<span data-ttu-id="fcb8c-220">Zie [about_Calculated_Properties](../Microsoft.PowerShell.Core/About/about_Calculated_Properties.md)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="fcb8c-220">For more information, see [about_Calculated_Properties](../Microsoft.PowerShell.Core/About/about_Calculated_Properties.md).</span></span>

```yaml
Type: System.Object[]
Parameter Sets: (All)
Aliases:

Required: False
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="fcb8c-221">-Titel</span><span class="sxs-lookup"><span data-stu-id="fcb8c-221">-Title</span></span>

<span data-ttu-id="fcb8c-222">Hiermee geeft u een titel voor het HTML-bestand, dat wil zeggen, de tekst die wordt weer gegeven tussen de `<TITLE>` Tags.</span><span class="sxs-lookup"><span data-stu-id="fcb8c-222">Specifies a title for the HTML file, that is, the text that appears between the `<TITLE>` tags.</span></span>

```yaml
Type: System.String
Parameter Sets: Page
Aliases:

Required: False
Position: 2
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="fcb8c-223">-Overgang</span><span class="sxs-lookup"><span data-stu-id="fcb8c-223">-Transitional</span></span>

<span data-ttu-id="fcb8c-224">Wijzigt het **DOCTYPE** - **overgangs DTD**, het standaard **DOCTYPE** is **XHTML Strict DTD**.</span><span class="sxs-lookup"><span data-stu-id="fcb8c-224">Changes the **DOCTYPE** to **XHTML Transitional DTD**, Default **DOCTYPE** is **XHTML Strict DTD**.</span></span>

<span data-ttu-id="fcb8c-225">Deze para meter is geïntroduceerd in Power shell 6,0.</span><span class="sxs-lookup"><span data-stu-id="fcb8c-225">This parameter was introduced in PowerShell 6.0.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: Page
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="fcb8c-226">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="fcb8c-226">CommonParameters</span></span>

<span data-ttu-id="fcb8c-227">Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="fcb8c-227">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="fcb8c-228">Zie [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="fcb8c-228">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="fcb8c-229">INVOER</span><span class="sxs-lookup"><span data-stu-id="fcb8c-229">INPUTS</span></span>

### <span data-ttu-id="fcb8c-230">System. Management. Automation. PSObject</span><span class="sxs-lookup"><span data-stu-id="fcb8c-230">System.Management.Automation.PSObject</span></span>

<span data-ttu-id="fcb8c-231">U kunt elk .NET-object door sluizen naar `ConvertTo-Html` .</span><span class="sxs-lookup"><span data-stu-id="fcb8c-231">You can pipe any .NET object to `ConvertTo-Html`.</span></span>

## <span data-ttu-id="fcb8c-232">UITVOER</span><span class="sxs-lookup"><span data-stu-id="fcb8c-232">OUTPUTS</span></span>

### <span data-ttu-id="fcb8c-233">Systeem. teken reeks of System.Xml.Xmldocument</span><span class="sxs-lookup"><span data-stu-id="fcb8c-233">System.String or System.Xml.XmlDocument</span></span>

<span data-ttu-id="fcb8c-234">`ConvertTo-Html` retourneert reeksen van teken reeksen waaruit een geldige HTML bestaat.</span><span class="sxs-lookup"><span data-stu-id="fcb8c-234">`ConvertTo-Html` returns series of strings that comprise valid HTML.</span></span>

## <span data-ttu-id="fcb8c-235">OPMERKINGEN</span><span class="sxs-lookup"><span data-stu-id="fcb8c-235">NOTES</span></span>

<span data-ttu-id="fcb8c-236">Als u deze cmdlet wilt gebruiken, pipet u een of meer objecten aan de cmdlet of gebruikt u de para meter **input object** om het object op te geven.</span><span class="sxs-lookup"><span data-stu-id="fcb8c-236">To use this cmdlet, pipe one or more objects to the cmdlet or use the **InputObject** parameter to specify the object.</span></span> <span data-ttu-id="fcb8c-237">Wanneer de invoer uit meerdere objecten bestaat, is de uitvoer van deze twee methoden heel anders.</span><span class="sxs-lookup"><span data-stu-id="fcb8c-237">When the input consists of multiple objects, the output of these two methods is quite different.</span></span>

- <span data-ttu-id="fcb8c-238">Wanneer u meerdere objecten naar een cmdlet Pipet, verzendt Power shell de objecten per keer naar de cmdlet.</span><span class="sxs-lookup"><span data-stu-id="fcb8c-238">When you pipe multiple objects to a cmdlet, PowerShell sends the objects to the cmdlet one at a time.</span></span> <span data-ttu-id="fcb8c-239">Als gevolg hiervan `ConvertTo-Html` wordt een tabel gemaakt waarin de afzonderlijke objecten worden weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="fcb8c-239">As a result, `ConvertTo-Html` creates a table that displays the individual objects.</span></span> <span data-ttu-id="fcb8c-240">Als u bijvoorbeeld de processen op een computer wilt `ConvertTo-Html` door sluizen, worden in de resulterende tabel alle processen weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="fcb8c-240">For example, if you pipe the processes on a computer to `ConvertTo-Html`, the resulting table displays all of the processes.</span></span>

- <span data-ttu-id="fcb8c-241">Wanneer u de para meter **input object** gebruikt voor het verzenden van meerdere objecten, `ConvertTo-Html` ontvangt deze objecten als een verzameling of als een matrix.</span><span class="sxs-lookup"><span data-stu-id="fcb8c-241">When you use the **InputObject** parameter to submit multiple objects, `ConvertTo-Html` receives these objects as a collection or as an array.</span></span> <span data-ttu-id="fcb8c-242">Als gevolg hiervan wordt een tabel gemaakt waarin de matrix en de bijbehorende eigenschappen worden weer gegeven, niet de items in de matrix.</span><span class="sxs-lookup"><span data-stu-id="fcb8c-242">As a result, it creates a table that displays the array and its properties, not the items in the array.</span></span> <span data-ttu-id="fcb8c-243">Als u bijvoorbeeld **input object** gebruikt om de processen op een computer in te dienen `ConvertTo-Html` , worden in de resulterende tabel een object matrix en de bijbehorende eigenschappen weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="fcb8c-243">For example, if you use **InputObject** to submit the processes on a computer to `ConvertTo-Html`, the resulting table displays an object array and its properties.</span></span>

  <span data-ttu-id="fcb8c-244">Om te voldoen aan de XHTML Strict DTD, wordt de DOCTYPE-tag dienovereenkomstig gewijzigd:</span><span class="sxs-lookup"><span data-stu-id="fcb8c-244">To comply with the XHTML Strict DTD, the DOCTYPE tag is modified accordingly:</span></span>

   `<!DOCTYPE html PUBLIC "-//W3C//DTD XHTML 1.0 Strict//EN"   "https://www.w3.org/TR/xhtml1/DTD/xhtml1-strict.dtd"\>`

## <span data-ttu-id="fcb8c-245">GERELATEERDE KOPPELINGEN</span><span class="sxs-lookup"><span data-stu-id="fcb8c-245">RELATED LINKS</span></span>

[<span data-ttu-id="fcb8c-246">about_Calculated_Properties</span><span class="sxs-lookup"><span data-stu-id="fcb8c-246">about_Calculated_Properties</span></span>](../Microsoft.PowerShell.Core/About/about_Calculated_Properties.md)

[<span data-ttu-id="fcb8c-247">ConvertTo-Csv</span><span class="sxs-lookup"><span data-stu-id="fcb8c-247">ConvertTo-Csv</span></span>](ConvertTo-Csv.md)

[<span data-ttu-id="fcb8c-248">ConvertTo-Json</span><span class="sxs-lookup"><span data-stu-id="fcb8c-248">ConvertTo-Json</span></span>](ConvertTo-Json.md)

[<span data-ttu-id="fcb8c-249">ConvertTo-Xml</span><span class="sxs-lookup"><span data-stu-id="fcb8c-249">ConvertTo-Xml</span></span>](ConvertTo-Xml.md)

[<span data-ttu-id="fcb8c-250">Exporteren-Clixml</span><span class="sxs-lookup"><span data-stu-id="fcb8c-250">Export-Clixml</span></span>](Export-Clixml.md)

[<span data-ttu-id="fcb8c-251">Import-Clixml</span><span class="sxs-lookup"><span data-stu-id="fcb8c-251">Import-Clixml</span></span>](Import-Clixml.md)
