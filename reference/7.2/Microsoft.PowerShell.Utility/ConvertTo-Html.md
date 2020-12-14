---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 08/10/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/convertto-html?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: ConvertTo-Html
ms.openlocfilehash: ffe7fe7c44258435c7ec9ddd2bab9ebeb9f6c465
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 11/17/2020
ms.locfileid: "94705839"
---
# <span data-ttu-id="86bdd-102">ConvertTo-Html</span><span class="sxs-lookup"><span data-stu-id="86bdd-102">ConvertTo-Html</span></span>

## <span data-ttu-id="86bdd-103">SAMENVATTING</span><span class="sxs-lookup"><span data-stu-id="86bdd-103">SYNOPSIS</span></span>
<span data-ttu-id="86bdd-104">Hiermee converteert u .NET-objecten naar HTML die kunnen worden weer gegeven in een webbrowser.</span><span class="sxs-lookup"><span data-stu-id="86bdd-104">Converts .NET objects into HTML that can be displayed in a Web browser.</span></span>

## <span data-ttu-id="86bdd-105">SYNTAXIS</span><span class="sxs-lookup"><span data-stu-id="86bdd-105">SYNTAX</span></span>

### <span data-ttu-id="86bdd-106">Pagina (standaard)</span><span class="sxs-lookup"><span data-stu-id="86bdd-106">Page (Default)</span></span>

```
ConvertTo-Html [-InputObject <PSObject>] [[-Property] <Object[]>] [[-Body] <String[]>]
 [[-Head] <String[]>] [[-Title] <String>] [-As <String>] [-CssUri <Uri>] [-PostContent <String[]>]
 [-PreContent <String[]>] [-Meta <Hashtable>] [-Charset <String>] [-Transitional]
 [<CommonParameters>]
```

### <span data-ttu-id="86bdd-107">Fragment</span><span class="sxs-lookup"><span data-stu-id="86bdd-107">Fragment</span></span>

```
ConvertTo-Html [-InputObject <PSObject>] [[-Property] <Object[]>] [-As <String>] [-Fragment]
 [-PostContent <String[]>] [-PreContent <String[]>] [<CommonParameters>]
```

## <span data-ttu-id="86bdd-108">BESCHRIJVING</span><span class="sxs-lookup"><span data-stu-id="86bdd-108">DESCRIPTION</span></span>

<span data-ttu-id="86bdd-109">`ConvertTo-Html`Met de cmdlet worden .net-objecten geconverteerd naar HTML die kan worden weer gegeven in een webbrowser.</span><span class="sxs-lookup"><span data-stu-id="86bdd-109">The `ConvertTo-Html` cmdlet converts .NET objects into HTML that can be displayed in a Web browser.</span></span> <span data-ttu-id="86bdd-110">U kunt deze cmdlet gebruiken om de uitvoer van een opdracht in een webpagina weer te geven.</span><span class="sxs-lookup"><span data-stu-id="86bdd-110">You can use this cmdlet to display the output of a command in a Web page.</span></span>

<span data-ttu-id="86bdd-111">U kunt de para meters van gebruiken `ConvertTo-Html` om object eigenschappen te selecteren, om een tabel-of lijst indeling op te geven, om de titel van de HTML-pagina op te geven, tekst voor en toe te voegen voor en na het object, en om alleen het tabel-of lijst fragment op te halen in plaats van een strikte DTD-pagina.</span><span class="sxs-lookup"><span data-stu-id="86bdd-111">You can use the parameters of `ConvertTo-Html` to select object properties, to specify a table or list format, to specify the HTML page title, to add text before and after the object, and to return only the table or list fragment, instead of a strict DTD page.</span></span>

<span data-ttu-id="86bdd-112">Wanneer u meerdere objecten indient naar `ConvertTo-Html` , maakt Power shell de tabel (of lijst) op basis van de eigenschappen van het eerste object dat u verzendt.</span><span class="sxs-lookup"><span data-stu-id="86bdd-112">When you submit multiple objects to `ConvertTo-Html`, PowerShell creates the table (or list) based on the properties of the first object that you submit.</span></span> <span data-ttu-id="86bdd-113">Als de resterende objecten niet beschikken over een van de opgegeven eigenschappen, is de waarde van de eigenschap van dat object een lege cel.</span><span class="sxs-lookup"><span data-stu-id="86bdd-113">If the remaining objects do not have one of the specified properties, the property value of that object is an empty cell.</span></span> <span data-ttu-id="86bdd-114">Als de resterende objecten extra eigenschappen hebben, worden deze eigenschaps waarden niet opgenomen in het bestand.</span><span class="sxs-lookup"><span data-stu-id="86bdd-114">If the remaining objects have additional properties, those property values are not included in the file.</span></span>

## <span data-ttu-id="86bdd-115">VOORBEELDEN</span><span class="sxs-lookup"><span data-stu-id="86bdd-115">EXAMPLES</span></span>

### <span data-ttu-id="86bdd-116">Voor beeld 1: een webpagina maken om de datum weer te geven</span><span class="sxs-lookup"><span data-stu-id="86bdd-116">Example 1: Create a web page to display the date</span></span>

```powershell
ConvertTo-Html -InputObject (Get-Date)
```

<span data-ttu-id="86bdd-117">Met deze opdracht maakt u een HTML-pagina waarop de eigenschappen van de huidige datum worden weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="86bdd-117">This command creates an HTML page that displays the properties of the current date.</span></span> <span data-ttu-id="86bdd-118">De para meter **input object** wordt gebruikt om de resultaten van een `Get-Date` opdracht bij de cmdlet in te dienen `ConvertTo-Html` .</span><span class="sxs-lookup"><span data-stu-id="86bdd-118">It uses the **InputObject** parameter to submit the results of a `Get-Date` command to the `ConvertTo-Html` cmdlet.</span></span>

### <span data-ttu-id="86bdd-119">Voor beeld 2: een webpagina maken voor het weer geven van Power shell-aliassen</span><span class="sxs-lookup"><span data-stu-id="86bdd-119">Example 2: Create a web page to display PowerShell aliases</span></span>

```powershell
Get-Alias | ConvertTo-Html | Out-File aliases.htm
Invoke-Item aliases.htm
```

<span data-ttu-id="86bdd-120">Met deze opdracht maakt u een HTML-pagina waarop de Power shell-aliassen in de huidige console worden weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="86bdd-120">This command creates an HTML page that lists the PowerShell aliases in the current console.</span></span>

<span data-ttu-id="86bdd-121">De opdracht gebruikt de `Get-Alias` cmdlet om de aliassen op te halen.</span><span class="sxs-lookup"><span data-stu-id="86bdd-121">The command uses the `Get-Alias` cmdlet to get the aliases.</span></span> <span data-ttu-id="86bdd-122">Er wordt gebruikgemaakt van de pijplijn operator ( `|` ) om de aliassen te verzenden naar de `ConvertTo-Html` cmdlet, waarmee de HTML-pagina wordt gemaakt.</span><span class="sxs-lookup"><span data-stu-id="86bdd-122">It uses the pipeline operator (`|`) to send the aliases to the `ConvertTo-Html` cmdlet, which creates the HTML page.</span></span> <span data-ttu-id="86bdd-123">De opdracht gebruikt ook de `Out-File` cmdlet om de HTML-code naar het `aliases.htm` bestand te verzenden.</span><span class="sxs-lookup"><span data-stu-id="86bdd-123">The command also uses the `Out-File` cmdlet to send the HTML code to the `aliases.htm` file.</span></span>

### <span data-ttu-id="86bdd-124">Voor beeld 3: een webpagina maken om Power shell-gebeurtenissen weer te geven</span><span class="sxs-lookup"><span data-stu-id="86bdd-124">Example 3: Create a web page to display PowerShell events</span></span>

```powershell
`Get-EventLog` -LogName "Windows PowerShell" | ConvertTo-Html | Out-File pslog.htm
```

<span data-ttu-id="86bdd-125">Met deze opdracht maakt u een HTML-pagina `pslog.htm` met de naam waarmee de gebeurtenissen in het Windows Power shell-gebeurtenis logboek op de lokale computer worden weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="86bdd-125">This command creates an HTML page called `pslog.htm` that displays the events in the Windows PowerShell event log on the local computer.</span></span>

<span data-ttu-id="86bdd-126">De cmdlet wordt gebruikt `Get-EventLog` om de gebeurtenissen in het Windows Power shell-logboek op te halen. vervolgens wordt de pijplijn operator ( `|` ) gebruikt om de gebeurtenissen te verzenden naar de `ConvertTo-Html` cmdlet.</span><span class="sxs-lookup"><span data-stu-id="86bdd-126">It uses the `Get-EventLog` cmdlet to get the events in the Windows PowerShell log and then uses the pipeline operator (`|`) to send the events to the `ConvertTo-Html` cmdlet.</span></span> <span data-ttu-id="86bdd-127">De opdracht gebruikt ook de `Out-File` cmdlet om de HTML-code naar het `pslog.htm` bestand te verzenden.</span><span class="sxs-lookup"><span data-stu-id="86bdd-127">The command also uses the `Out-File` cmdlet to send the HTML code to the `pslog.htm` file.</span></span>

<span data-ttu-id="86bdd-128">De opdracht gebruikt ook de `Out-File` cmdlet om de HTML-code naar het `pslog.htm` bestand te verzenden.</span><span class="sxs-lookup"><span data-stu-id="86bdd-128">The command also uses the `Out-File` cmdlet to send the HTML code to the `pslog.htm` file.</span></span>

### <span data-ttu-id="86bdd-129">Voor beeld 4: een webpagina maken om processen weer te geven</span><span class="sxs-lookup"><span data-stu-id="86bdd-129">Example 4: Create a web page to display processes</span></span>

```powershell
Get-Process |
  ConvertTo-Html -Property Name, Path, Company -Title "Process Information" |
    Out-File proc.htm
Invoke-Item proc.htm
```

<span data-ttu-id="86bdd-130">Met deze opdrachten maakt en opent u een HTML-pagina met een lijst met de naam, het pad en het bedrijf van de processen op de lokale computer.</span><span class="sxs-lookup"><span data-stu-id="86bdd-130">These commands create and open an HTML page that lists the name, path, and company of the processes on the local computer.</span></span>

<span data-ttu-id="86bdd-131">De eerste opdracht gebruikt de `Get-Process` cmdlet om objecten op te halen die de processen vertegenwoordigen die worden uitgevoerd op de computer.</span><span class="sxs-lookup"><span data-stu-id="86bdd-131">The first command uses the `Get-Process` cmdlet to get objects that represent the processes running on the computer.</span></span> <span data-ttu-id="86bdd-132">De opdracht maakt gebruik van de pijplijn operator ( `|` ) om de proces objecten naar de `ConvertTo-Html` cmdlet te verzenden.</span><span class="sxs-lookup"><span data-stu-id="86bdd-132">The command uses the pipeline operator (`|`) to send the process objects to the `ConvertTo-Html` cmdlet.</span></span>

<span data-ttu-id="86bdd-133">De opdracht gebruikt de para meter **Property** om drie eigenschappen te selecteren van de proces objecten die in de tabel moeten worden opgenomen.</span><span class="sxs-lookup"><span data-stu-id="86bdd-133">The command uses the **Property** parameter to select three properties of the process objects to be included in the table.</span></span> <span data-ttu-id="86bdd-134">De opdracht gebruikt de para meter **title** om een titel voor de HTML-pagina op te geven.</span><span class="sxs-lookup"><span data-stu-id="86bdd-134">The command uses the **Title** parameter to specify a title for the HTML page.</span></span> <span data-ttu-id="86bdd-135">De opdracht gebruikt ook de `Out-File` cmdlet om de resulterende HTML naar een bestand met de naam Proc.htm te verzenden.</span><span class="sxs-lookup"><span data-stu-id="86bdd-135">The command also uses the `Out-File` cmdlet to send the resulting HTML to a file named Proc.htm.</span></span>

<span data-ttu-id="86bdd-136">Met de tweede opdracht wordt de `Invoke-Item` cmdlet gebruikt om de `Proc.htm` in de standaard browser te openen.</span><span class="sxs-lookup"><span data-stu-id="86bdd-136">The second command uses the `Invoke-Item` cmdlet to open the `Proc.htm` in the default browser.</span></span>

### <span data-ttu-id="86bdd-137">Voor beeld 5: een webpagina maken voor het weer geven van service objecten</span><span class="sxs-lookup"><span data-stu-id="86bdd-137">Example 5: Create a web page to display service objects</span></span>

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

<span data-ttu-id="86bdd-138">Met deze opdracht maakt u een HTML-pagina van de service objecten die door de `Get-Service` cmdlet worden geretourneerd.</span><span class="sxs-lookup"><span data-stu-id="86bdd-138">This command creates an HTML page of the service objects that the `Get-Service` cmdlet returns.</span></span> <span data-ttu-id="86bdd-139">De opdracht gebruikt de para meter **CssUri** om een trapsgewijs opmaak model voor de HTML-pagina op te geven.</span><span class="sxs-lookup"><span data-stu-id="86bdd-139">The command uses the **CssUri** parameter to specify a cascading style sheet for the HTML page.</span></span>

<span data-ttu-id="86bdd-140">De para meter **CssUri** voegt een extra `<link rel="stylesheet" type="text/css" href="test.css">` tag toe aan de resulterende HTML.</span><span class="sxs-lookup"><span data-stu-id="86bdd-140">The **CssUri** parameter adds an additional `<link rel="stylesheet" type="text/css" href="test.css">` tag to the resulting HTML.</span></span> <span data-ttu-id="86bdd-141">Het kenmerk HREF in het label bevat de naam van het opmaak model.</span><span class="sxs-lookup"><span data-stu-id="86bdd-141">The HREF attribute in the tag contains the name of the style sheet.</span></span>

### <span data-ttu-id="86bdd-142">Voor beeld 6: een webpagina maken voor het weer geven van service objecten</span><span class="sxs-lookup"><span data-stu-id="86bdd-142">Example 6: Create a web page to display service objects</span></span>

```powershell
Get-Service | ConvertTo-Html -As LIST | Out-File services.htm
```

<span data-ttu-id="86bdd-143">Met deze opdracht maakt u een HTML-pagina van de service objecten die door de `Get-Service` cmdlet worden geretourneerd.</span><span class="sxs-lookup"><span data-stu-id="86bdd-143">This command creates an HTML page of the service objects that the `Get-Service` cmdlet returns.</span></span> <span data-ttu-id="86bdd-144">De opdracht gebruikt de **as** -para meter om een lijst indeling op te geven.</span><span class="sxs-lookup"><span data-stu-id="86bdd-144">The command uses the **As** parameter to specify a list format.</span></span> <span data-ttu-id="86bdd-145">De cmdlet `Out-File` verzendt de resulterende HTML naar het `Services.htm` bestand.</span><span class="sxs-lookup"><span data-stu-id="86bdd-145">The cmdlet `Out-File` sends the resulting HTML to the `Services.htm` file.</span></span>

### <span data-ttu-id="86bdd-146">Voor beeld 7: een webtabel maken voor de huidige datum</span><span class="sxs-lookup"><span data-stu-id="86bdd-146">Example 7: Create a web table for the current date</span></span>

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

<span data-ttu-id="86bdd-147">Met deze opdracht wordt `ConvertTo-Html` een HTML-tabel van de huidige datum gegenereerd.</span><span class="sxs-lookup"><span data-stu-id="86bdd-147">This command uses `ConvertTo-Html` to generate an HTML table of the current date.</span></span> <span data-ttu-id="86bdd-148">De opdracht gebruikt de `Get-Date` cmdlet om de huidige datum op te halen.</span><span class="sxs-lookup"><span data-stu-id="86bdd-148">The command uses the `Get-Date` cmdlet to get the current date.</span></span> <span data-ttu-id="86bdd-149">Er wordt gebruikgemaakt van een pijplijn operator (|) om de resultaten naar de cmdlet te verzenden `ConvertTo-Html` .</span><span class="sxs-lookup"><span data-stu-id="86bdd-149">It uses a pipeline operator (|) to send the results to the `ConvertTo-Html` cmdlet.</span></span>

<span data-ttu-id="86bdd-150">De `ConvertTo-Html` opdracht bevat de **fragment** parameter, waarmee de uitvoer wordt beperkt tot een HTML-tabel.</span><span class="sxs-lookup"><span data-stu-id="86bdd-150">The `ConvertTo-Html` command includes the **Fragment** parameter, which limits the output to an HTML table.</span></span> <span data-ttu-id="86bdd-151">Als gevolg hiervan worden de andere elementen van een HTML-pagina, zoals de `<HEAD>` `<BODY>` Tags en wegge laten.</span><span class="sxs-lookup"><span data-stu-id="86bdd-151">As a result, the other elements of an HTML page, such as the `<HEAD>` and `<BODY>` tags, are omitted.</span></span>

### <span data-ttu-id="86bdd-152">Voor beeld 8: een webpagina maken om Power shell-gebeurtenissen weer te geven</span><span class="sxs-lookup"><span data-stu-id="86bdd-152">Example 8: Create a web page to display PowerShell events</span></span>

```powershell
Get-EventLog -Log "Windows PowerShell" | ConvertTo-Html -Property id, level, task
```

<span data-ttu-id="86bdd-153">Met deze opdracht wordt de `Get-EventLog` cmdlet gebruikt om gebeurtenissen van het Windows Power shell-gebeurtenis logboek op te halen.</span><span class="sxs-lookup"><span data-stu-id="86bdd-153">This command uses the `Get-EventLog` cmdlet to get events from the Windows PowerShell event log.</span></span>

<span data-ttu-id="86bdd-154">Er wordt een pijplijn operator ( `|` ) gebruikt om de gebeurtenissen te verzenden naar de `ConvertTo-Html` cmdlet, waarmee de gebeurtenissen worden geconverteerd naar een HTML-indeling.</span><span class="sxs-lookup"><span data-stu-id="86bdd-154">It uses a pipeline operator (`|`) to send the events to the `ConvertTo-Html` cmdlet, which converts the events to HTML format.</span></span>

<span data-ttu-id="86bdd-155">De `ConvertTo-Html` opdracht gebruikt de para meter **Property** om alleen de eigenschappen **id**, **niveau** en **Task** van de gebeurtenis te selecteren.</span><span class="sxs-lookup"><span data-stu-id="86bdd-155">The `ConvertTo-Html` command uses the **Property** parameter to select only the **ID**, **Level**, and **Task** properties of the event.</span></span>

### <span data-ttu-id="86bdd-156">Voor beeld 9: een webpagina maken om opgegeven services weer te geven</span><span class="sxs-lookup"><span data-stu-id="86bdd-156">Example 9: Create a web page to display specified services</span></span>

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

<span data-ttu-id="86bdd-157">Met deze opdracht wordt een webpagina gemaakt en geopend waarop de services op de computer worden weer gegeven die beginnen met een. Het maakt gebruik van de para meters **titel**, **hoofd tekst** **, voor-en** **PostContent** van `ConvertTo-Html` om de uitvoer aan te passen.</span><span class="sxs-lookup"><span data-stu-id="86bdd-157">This command creates and opens a Web page that displays the services on the computer that begin with A. It uses the **Title**, **Body**, **PreContent**, and **PostContent** parameters of `ConvertTo-Html` to customize the output.</span></span>

<span data-ttu-id="86bdd-158">Het eerste deel van de opdracht gebruikt de `Get-Service` cmdlet om de services op de computer te verkrijgen die met een beginnen. De opdracht maakt gebruik van een pijplijn operator ( `|` ) om de resultaten naar de `ConvertTo-Html` cmdlet te verzenden.</span><span class="sxs-lookup"><span data-stu-id="86bdd-158">The first part of the command uses the `Get-Service` cmdlet to get the services on the computer that begin with A. The command uses a pipeline operator (`|`) to send the results to the `ConvertTo-Html` cmdlet.</span></span> <span data-ttu-id="86bdd-159">De opdracht gebruikt ook de `Out-File` cmdlet om de uitvoer naar het Services.htm-bestand te verzenden.</span><span class="sxs-lookup"><span data-stu-id="86bdd-159">The command also uses the `Out-File` cmdlet to send the output to the Services.htm file.</span></span>

<span data-ttu-id="86bdd-160">Een punt komma ( `;` ) eindigt de eerste opdracht en start een tweede opdracht, waarbij de `Invoke-Item` cmdlet wordt gebruikt om het bestand te openen `Services.htm` in de standaard browser.</span><span class="sxs-lookup"><span data-stu-id="86bdd-160">A semicolon (`;`) ends the first command and starts a second command, which uses the `Invoke-Item` cmdlet to open the `Services.htm` file in the default browser.</span></span>

### <span data-ttu-id="86bdd-161">Voor beeld 10: de meta-eigenschappen en charset van de HTML instellen</span><span class="sxs-lookup"><span data-stu-id="86bdd-161">Example 10: Set the Meta properties and Charset of the HTML</span></span>

```powershell
Get-Service | ConvertTo-HTML -Meta @{
  refresh=10
  author="Author's Name"
  keywords="PowerShell, HTML, ConvertTo-HTML"
} -Charset "UTF-8"
```

<span data-ttu-id="86bdd-162">Met deze opdracht wordt de HTML-code voor een webpagina gemaakt met de meta tags voor vernieuwen, auteur en tref woorden.</span><span class="sxs-lookup"><span data-stu-id="86bdd-162">This command creates the HTML for a webpage with the meta tags for refresh, author, and keywords.</span></span>
<span data-ttu-id="86bdd-163">De charset voor de pagina is ingesteld op UTF-8</span><span class="sxs-lookup"><span data-stu-id="86bdd-163">The charset for the page is set to UTF-8</span></span>

### <span data-ttu-id="86bdd-164">Voor beeld 11: de HTML instellen op XHTML-overgangs DTD</span><span class="sxs-lookup"><span data-stu-id="86bdd-164">Example 11: Set the HTML to XHTML Transitional DTD</span></span>

```powershell
Get-Service | ConvertTo-HTML -Transitional
```

<span data-ttu-id="86bdd-165">Met deze opdracht wordt het DOCTYPE van de geretourneerde HTML ingesteld op XHTML-overgangs DTD</span><span class="sxs-lookup"><span data-stu-id="86bdd-165">This command sets the DOCTYPE of the returned HTML to XHTML Transitional DTD</span></span>

## <span data-ttu-id="86bdd-166">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="86bdd-166">PARAMETERS</span></span>

### <span data-ttu-id="86bdd-167">-As</span><span class="sxs-lookup"><span data-stu-id="86bdd-167">-As</span></span>

<span data-ttu-id="86bdd-168">Bepaalt of het object wordt opgemaakt als een tabel of een lijst.</span><span class="sxs-lookup"><span data-stu-id="86bdd-168">Determines whether the object is formatted as a table or a list.</span></span> <span data-ttu-id="86bdd-169">Geldige waarden zijn **tabel** en **lijst**.</span><span class="sxs-lookup"><span data-stu-id="86bdd-169">Valid values are **Table** and **List**.</span></span> <span data-ttu-id="86bdd-170">De standaard waarde is **Table**.</span><span class="sxs-lookup"><span data-stu-id="86bdd-170">The default value is **Table**.</span></span>

<span data-ttu-id="86bdd-171">De **tabel** waarde genereert een HTML-tabel die overeenkomt met de indeling van de Power shell-tabel.</span><span class="sxs-lookup"><span data-stu-id="86bdd-171">The **Table** value generates an HTML table that resembles the PowerShell table format.</span></span> <span data-ttu-id="86bdd-172">In de rij met koppen worden de namen van eigenschappen weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="86bdd-172">The header row displays the property names.</span></span> <span data-ttu-id="86bdd-173">Elke tabelrij vertegenwoordigt een object en geeft de waarden van het object voor elke eigenschap.</span><span class="sxs-lookup"><span data-stu-id="86bdd-173">Each table row represents an object and displays the object's values for each property.</span></span>

<span data-ttu-id="86bdd-174">De **lijst** waarde genereert een HTML-tabel met twee kolommen voor elk object dat lijkt op de Power shell-lijst indeling.</span><span class="sxs-lookup"><span data-stu-id="86bdd-174">The **List** value generates a two-column HTML table for each object that resembles the PowerShell list format.</span></span> <span data-ttu-id="86bdd-175">In de eerste kolom wordt de naam van de eigenschap weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="86bdd-175">The first column displays the property name.</span></span> <span data-ttu-id="86bdd-176">De tweede kolom bevat de waarde van de eigenschap.</span><span class="sxs-lookup"><span data-stu-id="86bdd-176">The second column displays the property value.</span></span>

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

### <span data-ttu-id="86bdd-177">-Hoofd tekst</span><span class="sxs-lookup"><span data-stu-id="86bdd-177">-Body</span></span>

<span data-ttu-id="86bdd-178">Hiermee geeft u de tekst op die moet worden toegevoegd na de openings `<BODY>` code.</span><span class="sxs-lookup"><span data-stu-id="86bdd-178">Specifies the text to add after the opening `<BODY>` tag.</span></span> <span data-ttu-id="86bdd-179">Standaard is er geen tekst op die positie.</span><span class="sxs-lookup"><span data-stu-id="86bdd-179">By default, there is no text in that position.</span></span>

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

### <span data-ttu-id="86bdd-180">-Charset</span><span class="sxs-lookup"><span data-stu-id="86bdd-180">-Charset</span></span>

<span data-ttu-id="86bdd-181">Hiermee geeft u de tekst op die moet worden toegevoegd aan de openings `<charset>` code.</span><span class="sxs-lookup"><span data-stu-id="86bdd-181">Specifies text to add to the opening `<charset>` tag.</span></span> <span data-ttu-id="86bdd-182">Standaard is er geen tekst op die positie.</span><span class="sxs-lookup"><span data-stu-id="86bdd-182">By default, there is no text in that position.</span></span>

<span data-ttu-id="86bdd-183">Deze para meter is geïntroduceerd in Power shell 6,0.</span><span class="sxs-lookup"><span data-stu-id="86bdd-183">This parameter was introduced in PowerShell 6.0.</span></span>

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

### <span data-ttu-id="86bdd-184">-CssUri</span><span class="sxs-lookup"><span data-stu-id="86bdd-184">-CssUri</span></span>

<span data-ttu-id="86bdd-185">Hiermee geeft u de URI (Uniform Resource Identifier) van het trapsgewijze opmaak model (CSS) op dat wordt toegepast op het HTML-bestand.</span><span class="sxs-lookup"><span data-stu-id="86bdd-185">Specifies the Uniform Resource Identifier (URI) of the cascading style sheet (CSS) that is applied to the HTML file.</span></span> <span data-ttu-id="86bdd-186">De URI wordt opgenomen in een koppeling naar een opmaak model in de uitvoer.</span><span class="sxs-lookup"><span data-stu-id="86bdd-186">The URI is included in a style sheet link in the output.</span></span>

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

### <span data-ttu-id="86bdd-187">-Fragment</span><span class="sxs-lookup"><span data-stu-id="86bdd-187">-Fragment</span></span>

<span data-ttu-id="86bdd-188">Genereert alleen een HTML-tabel.</span><span class="sxs-lookup"><span data-stu-id="86bdd-188">Generates only an HTML table.</span></span> <span data-ttu-id="86bdd-189">De tags HTML, HEAD, TITLE en BODY worden wegge laten.</span><span class="sxs-lookup"><span data-stu-id="86bdd-189">The HTML, HEAD, TITLE, and BODY tags are omitted.</span></span>

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

### <span data-ttu-id="86bdd-190">-Head</span><span class="sxs-lookup"><span data-stu-id="86bdd-190">-Head</span></span>

<span data-ttu-id="86bdd-191">Hiermee geeft u de inhoud van de `<HEAD>` tag.</span><span class="sxs-lookup"><span data-stu-id="86bdd-191">Specifies the content of the `<HEAD>` tag.</span></span> <span data-ttu-id="86bdd-192">De standaardwaarde is `<title\>HTML TABLE</title>`.</span><span class="sxs-lookup"><span data-stu-id="86bdd-192">The default is `<title\>HTML TABLE</title>`.</span></span> <span data-ttu-id="86bdd-193">Als u de para meter **Head** gebruikt, wordt de para meter **title** genegeerd.</span><span class="sxs-lookup"><span data-stu-id="86bdd-193">If you use the **Head** parameter, the **Title** parameter is ignored.</span></span>

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

### <span data-ttu-id="86bdd-194">-Input object</span><span class="sxs-lookup"><span data-stu-id="86bdd-194">-InputObject</span></span>

<span data-ttu-id="86bdd-195">Hiermee geeft u de objecten op die in HTML moeten worden weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="86bdd-195">Specifies the objects to be represented in HTML.</span></span> <span data-ttu-id="86bdd-196">Voer een variabele in die de objecten bevat of typ een opdracht of expressie waarmee de objecten worden opgehaald.</span><span class="sxs-lookup"><span data-stu-id="86bdd-196">Enter a variable that contains the objects or type a command or expression that gets the objects.</span></span>

<span data-ttu-id="86bdd-197">Als u deze para meter gebruikt voor het indienen van meerdere objecten, zoals alle services op een computer, `ConvertTo-Html` wordt een tabel gemaakt waarin de eigenschappen van een verzameling of een matrix met objecten worden weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="86bdd-197">If you use this parameter to submit multiple objects, such as all of the services on a computer, `ConvertTo-Html` creates a table that displays the properties of a collection or of an array of objects.</span></span> <span data-ttu-id="86bdd-198">Als u een tabel van de afzonderlijke objecten wilt maken, gebruikt u de pijplijn operator om de objecten naar te sluizen `ConvertTo-Html` .</span><span class="sxs-lookup"><span data-stu-id="86bdd-198">To create a table of the individual objects, use the pipeline operator to pipe the objects to `ConvertTo-Html`.</span></span>

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

### <span data-ttu-id="86bdd-199">-Meta</span><span class="sxs-lookup"><span data-stu-id="86bdd-199">-Meta</span></span>

<span data-ttu-id="86bdd-200">Hiermee geeft u de tekst op die moet worden toegevoegd aan de openings `<meta>` code.</span><span class="sxs-lookup"><span data-stu-id="86bdd-200">Specifies text to add to the opening `<meta>` tag.</span></span> <span data-ttu-id="86bdd-201">Standaard is er geen tekst op die positie.</span><span class="sxs-lookup"><span data-stu-id="86bdd-201">By default, there is no text in that position.</span></span>

<span data-ttu-id="86bdd-202">Deze para meter is geïntroduceerd in Power shell 6,0.</span><span class="sxs-lookup"><span data-stu-id="86bdd-202">This parameter was introduced in PowerShell 6.0.</span></span>

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

### <span data-ttu-id="86bdd-203">-PostContent</span><span class="sxs-lookup"><span data-stu-id="86bdd-203">-PostContent</span></span>

<span data-ttu-id="86bdd-204">Geeft aan dat er tekst moet worden toegevoegd na de afsluitende `</TABLE>` tag.</span><span class="sxs-lookup"><span data-stu-id="86bdd-204">Specifies text to add after the closing `</TABLE>` tag.</span></span> <span data-ttu-id="86bdd-205">Standaard is er geen tekst op die positie.</span><span class="sxs-lookup"><span data-stu-id="86bdd-205">By default, there is no text in that position.</span></span>

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

### <span data-ttu-id="86bdd-206">-Precontent</span><span class="sxs-lookup"><span data-stu-id="86bdd-206">-PreContent</span></span>

<span data-ttu-id="86bdd-207">Hiermee geeft u de tekst die moet worden toegevoegd voor de openings `<TABLE>` code.</span><span class="sxs-lookup"><span data-stu-id="86bdd-207">Specifies text to add before the opening `<TABLE>` tag.</span></span> <span data-ttu-id="86bdd-208">Standaard is er geen tekst op die positie.</span><span class="sxs-lookup"><span data-stu-id="86bdd-208">By default, there is no text in that position.</span></span>

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

### <span data-ttu-id="86bdd-209">-Eigenschap</span><span class="sxs-lookup"><span data-stu-id="86bdd-209">-Property</span></span>

<span data-ttu-id="86bdd-210">Bevat de opgegeven eigenschappen van de objecten in de HTML.</span><span class="sxs-lookup"><span data-stu-id="86bdd-210">Includes the specified properties of the objects in the HTML.</span></span> <span data-ttu-id="86bdd-211">De waarde van de **eigenschaps** parameter kan een nieuwe berekende eigenschap zijn.</span><span class="sxs-lookup"><span data-stu-id="86bdd-211">The value of the **Property** parameter can be a new calculated property.</span></span> <span data-ttu-id="86bdd-212">De berekende eigenschap kan een script blok of een hash-tabel zijn.</span><span class="sxs-lookup"><span data-stu-id="86bdd-212">The calculated property can be a script block or a hash table.</span></span> <span data-ttu-id="86bdd-213">Geldige sleutel-waardeparen zijn:</span><span class="sxs-lookup"><span data-stu-id="86bdd-213">Valid key-value pairs are:</span></span>

- <span data-ttu-id="86bdd-214">Naam (of label): `<string>` (toegevoegd in Power shell 6. x)</span><span class="sxs-lookup"><span data-stu-id="86bdd-214">Name (or label) - `<string>` (added in PowerShell 6.x)</span></span>
- <span data-ttu-id="86bdd-215">Expressie- `<string>` of `<script block>`</span><span class="sxs-lookup"><span data-stu-id="86bdd-215">Expression - `<string>` or `<script block>`</span></span>
- <span data-ttu-id="86bdd-216">Tring `<string>`</span><span class="sxs-lookup"><span data-stu-id="86bdd-216">FormatString - `<string>`</span></span>
- <span data-ttu-id="86bdd-217">Breedte: `<int32>` moet groter zijn dan `0`</span><span class="sxs-lookup"><span data-stu-id="86bdd-217">Width - `<int32>` - must be greater than `0`</span></span>
- <span data-ttu-id="86bdd-218">Uitlijning-waarde kan `Left` , `Center` of `Right`</span><span class="sxs-lookup"><span data-stu-id="86bdd-218">Alignment - value can be `Left`, `Center`, or `Right`</span></span>

<span data-ttu-id="86bdd-219">Zie [about_Calculated_Properties](../Microsoft.PowerShell.Core/About/about_Calculated_Properties.md)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="86bdd-219">For more information, see [about_Calculated_Properties](../Microsoft.PowerShell.Core/About/about_Calculated_Properties.md).</span></span>

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

### <span data-ttu-id="86bdd-220">-Titel</span><span class="sxs-lookup"><span data-stu-id="86bdd-220">-Title</span></span>

<span data-ttu-id="86bdd-221">Hiermee geeft u een titel voor het HTML-bestand, dat wil zeggen, de tekst die wordt weer gegeven tussen de `<TITLE>` Tags.</span><span class="sxs-lookup"><span data-stu-id="86bdd-221">Specifies a title for the HTML file, that is, the text that appears between the `<TITLE>` tags.</span></span>

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

### <span data-ttu-id="86bdd-222">-Overgang</span><span class="sxs-lookup"><span data-stu-id="86bdd-222">-Transitional</span></span>

<span data-ttu-id="86bdd-223">Wijzigt het **DOCTYPE** - **overgangs DTD**, het standaard **DOCTYPE** is **XHTML Strict DTD**.</span><span class="sxs-lookup"><span data-stu-id="86bdd-223">Changes the **DOCTYPE** to **XHTML Transitional DTD**, Default **DOCTYPE** is **XHTML Strict DTD**.</span></span>

<span data-ttu-id="86bdd-224">Deze para meter is geïntroduceerd in Power shell 6,0.</span><span class="sxs-lookup"><span data-stu-id="86bdd-224">This parameter was introduced in PowerShell 6.0.</span></span>

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

### <span data-ttu-id="86bdd-225">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="86bdd-225">CommonParameters</span></span>

<span data-ttu-id="86bdd-226">Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="86bdd-226">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="86bdd-227">Zie [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="86bdd-227">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="86bdd-228">INVOER</span><span class="sxs-lookup"><span data-stu-id="86bdd-228">INPUTS</span></span>

### <span data-ttu-id="86bdd-229">System. Management. Automation. PSObject</span><span class="sxs-lookup"><span data-stu-id="86bdd-229">System.Management.Automation.PSObject</span></span>

<span data-ttu-id="86bdd-230">U kunt elk .NET-object door sluizen naar `ConvertTo-Html` .</span><span class="sxs-lookup"><span data-stu-id="86bdd-230">You can pipe any .NET object to `ConvertTo-Html`.</span></span>

## <span data-ttu-id="86bdd-231">UITVOER</span><span class="sxs-lookup"><span data-stu-id="86bdd-231">OUTPUTS</span></span>

### <span data-ttu-id="86bdd-232">Systeem. teken reeks of System.Xml.Xmldocument</span><span class="sxs-lookup"><span data-stu-id="86bdd-232">System.String or System.Xml.XmlDocument</span></span>

<span data-ttu-id="86bdd-233">`ConvertTo-Html` retourneert reeksen van teken reeksen waaruit een geldige HTML bestaat.</span><span class="sxs-lookup"><span data-stu-id="86bdd-233">`ConvertTo-Html` returns series of strings that comprise valid HTML.</span></span>

## <span data-ttu-id="86bdd-234">OPMERKINGEN</span><span class="sxs-lookup"><span data-stu-id="86bdd-234">NOTES</span></span>

<span data-ttu-id="86bdd-235">Als u deze cmdlet wilt gebruiken, pipet u een of meer objecten aan de cmdlet of gebruikt u de para meter **input object** om het object op te geven.</span><span class="sxs-lookup"><span data-stu-id="86bdd-235">To use this cmdlet, pipe one or more objects to the cmdlet or use the **InputObject** parameter to specify the object.</span></span> <span data-ttu-id="86bdd-236">Wanneer de invoer uit meerdere objecten bestaat, is de uitvoer van deze twee methoden heel anders.</span><span class="sxs-lookup"><span data-stu-id="86bdd-236">When the input consists of multiple objects, the output of these two methods is quite different.</span></span>

- <span data-ttu-id="86bdd-237">Wanneer u meerdere objecten naar een cmdlet Pipet, verzendt Power shell de objecten per keer naar de cmdlet.</span><span class="sxs-lookup"><span data-stu-id="86bdd-237">When you pipe multiple objects to a cmdlet, PowerShell sends the objects to the cmdlet one at a time.</span></span> <span data-ttu-id="86bdd-238">Als gevolg hiervan `ConvertTo-Html` wordt een tabel gemaakt waarin de afzonderlijke objecten worden weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="86bdd-238">As a result, `ConvertTo-Html` creates a table that displays the individual objects.</span></span> <span data-ttu-id="86bdd-239">Als u bijvoorbeeld de processen op een computer wilt `ConvertTo-Html` door sluizen, worden in de resulterende tabel alle processen weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="86bdd-239">For example, if you pipe the processes on a computer to `ConvertTo-Html`, the resulting table displays all of the processes.</span></span>

- <span data-ttu-id="86bdd-240">Wanneer u de para meter **input object** gebruikt voor het verzenden van meerdere objecten, `ConvertTo-Html` ontvangt deze objecten als een verzameling of als een matrix.</span><span class="sxs-lookup"><span data-stu-id="86bdd-240">When you use the **InputObject** parameter to submit multiple objects, `ConvertTo-Html` receives these objects as a collection or as an array.</span></span> <span data-ttu-id="86bdd-241">Als gevolg hiervan wordt een tabel gemaakt waarin de matrix en de bijbehorende eigenschappen worden weer gegeven, niet de items in de matrix.</span><span class="sxs-lookup"><span data-stu-id="86bdd-241">As a result, it creates a table that displays the array and its properties, not the items in the array.</span></span> <span data-ttu-id="86bdd-242">Als u bijvoorbeeld **input object** gebruikt om de processen op een computer in te dienen `ConvertTo-Html` , worden in de resulterende tabel een object matrix en de bijbehorende eigenschappen weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="86bdd-242">For example, if you use **InputObject** to submit the processes on a computer to `ConvertTo-Html`, the resulting table displays an object array and its properties.</span></span>

  <span data-ttu-id="86bdd-243">Om te voldoen aan de XHTML Strict DTD, wordt de DOCTYPE-tag dienovereenkomstig gewijzigd:</span><span class="sxs-lookup"><span data-stu-id="86bdd-243">To comply with the XHTML Strict DTD, the DOCTYPE tag is modified accordingly:</span></span>

   `<!DOCTYPE html PUBLIC "-//W3C//DTD XHTML 1.0 Strict//EN"   "https://www.w3.org/TR/xhtml1/DTD/xhtml1-strict.dtd"\>`

## <span data-ttu-id="86bdd-244">GERELATEERDE KOPPELINGEN</span><span class="sxs-lookup"><span data-stu-id="86bdd-244">RELATED LINKS</span></span>

[<span data-ttu-id="86bdd-245">about_Calculated_Properties</span><span class="sxs-lookup"><span data-stu-id="86bdd-245">about_Calculated_Properties</span></span>](../Microsoft.PowerShell.Core/About/about_Calculated_Properties.md)

[<span data-ttu-id="86bdd-246">ConvertTo-Csv</span><span class="sxs-lookup"><span data-stu-id="86bdd-246">ConvertTo-Csv</span></span>](ConvertTo-Csv.md)

[<span data-ttu-id="86bdd-247">ConvertTo-Json</span><span class="sxs-lookup"><span data-stu-id="86bdd-247">ConvertTo-Json</span></span>](ConvertTo-Json.md)

[<span data-ttu-id="86bdd-248">ConvertTo-Xml</span><span class="sxs-lookup"><span data-stu-id="86bdd-248">ConvertTo-Xml</span></span>](ConvertTo-Xml.md)

[<span data-ttu-id="86bdd-249">Exporteren-Clixml</span><span class="sxs-lookup"><span data-stu-id="86bdd-249">Export-Clixml</span></span>](Export-Clixml.md)

[<span data-ttu-id="86bdd-250">Import-Clixml</span><span class="sxs-lookup"><span data-stu-id="86bdd-250">Import-Clixml</span></span>](Import-Clixml.md)
