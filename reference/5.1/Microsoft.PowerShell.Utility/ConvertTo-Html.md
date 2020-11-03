---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 08/10/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/convertto-html?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: ConvertTo-Html
ms.openlocfilehash: 618308bb03f47659b8fa932ac0bb029972546755
ms.sourcegitcommit: 9a6b6714ded4edb5119f1b82a253608018ea6b98
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 08/10/2020
ms.locfileid: "93251738"
---
# <span data-ttu-id="448da-103">ConvertTo-Html</span><span class="sxs-lookup"><span data-stu-id="448da-103">ConvertTo-Html</span></span>

## <span data-ttu-id="448da-104">SAMENVATTING</span><span class="sxs-lookup"><span data-stu-id="448da-104">SYNOPSIS</span></span>
<span data-ttu-id="448da-105">Hiermee converteert u .NET-objecten naar HTML die kunnen worden weer gegeven in een webbrowser.</span><span class="sxs-lookup"><span data-stu-id="448da-105">Converts .NET objects into HTML that can be displayed in a Web browser.</span></span>

## <span data-ttu-id="448da-106">SYNTAXIS</span><span class="sxs-lookup"><span data-stu-id="448da-106">SYNTAX</span></span>

### <span data-ttu-id="448da-107">Pagina (standaard)</span><span class="sxs-lookup"><span data-stu-id="448da-107">Page (Default)</span></span>

```
ConvertTo-Html [-InputObject <PSObject>] [[-Property] <Object[]>] [[-Body] <String[]>]
 [[-Head] <String[]>] [[-Title] <String>] [-As <String>] [-CssUri <Uri>] [-PostContent <String[]>]
 [-PreContent <String[]>] [<CommonParameters>]
```

### <span data-ttu-id="448da-108">Fragment</span><span class="sxs-lookup"><span data-stu-id="448da-108">Fragment</span></span>

```
ConvertTo-Html [-InputObject <PSObject>] [[-Property] <Object[]>] [-As <String>] [-Fragment]
 [-PostContent <String[]>] [-PreContent <String[]>] [<CommonParameters>]
```

## <span data-ttu-id="448da-109">BESCHRIJVING</span><span class="sxs-lookup"><span data-stu-id="448da-109">DESCRIPTION</span></span>

<span data-ttu-id="448da-110">`ConvertTo-Html`Met de cmdlet worden .net-objecten geconverteerd naar HTML die kan worden weer gegeven in een webbrowser.</span><span class="sxs-lookup"><span data-stu-id="448da-110">The `ConvertTo-Html` cmdlet converts .NET objects into HTML that can be displayed in a Web browser.</span></span> <span data-ttu-id="448da-111">U kunt deze cmdlet gebruiken om de uitvoer van een opdracht in een webpagina weer te geven.</span><span class="sxs-lookup"><span data-stu-id="448da-111">You can use this cmdlet to display the output of a command in a Web page.</span></span>

<span data-ttu-id="448da-112">U kunt de para meters van gebruiken `ConvertTo-Html` om object eigenschappen te selecteren, om een tabel-of lijst indeling op te geven, om de titel van de HTML-pagina op te geven, tekst voor en toe te voegen voor en na het object, en om alleen het tabel-of lijst fragment op te halen in plaats van een strikte DTD-pagina.</span><span class="sxs-lookup"><span data-stu-id="448da-112">You can use the parameters of `ConvertTo-Html` to select object properties, to specify a table or list format, to specify the HTML page title, to add text before and after the object, and to return only the table or list fragment, instead of a strict DTD page.</span></span>

<span data-ttu-id="448da-113">Wanneer u meerdere objecten indient naar `ConvertTo-Html` , maakt Power shell de tabel (of lijst) op basis van de eigenschappen van het eerste object dat u verzendt.</span><span class="sxs-lookup"><span data-stu-id="448da-113">When you submit multiple objects to `ConvertTo-Html`, PowerShell creates the table (or list) based on the properties of the first object that you submit.</span></span> <span data-ttu-id="448da-114">Als de resterende objecten niet beschikken over een van de opgegeven eigenschappen, is de waarde van de eigenschap van dat object een lege cel.</span><span class="sxs-lookup"><span data-stu-id="448da-114">If the remaining objects do not have one of the specified properties, the property value of that object is an empty cell.</span></span> <span data-ttu-id="448da-115">Als de resterende objecten extra eigenschappen hebben, worden deze eigenschaps waarden niet opgenomen in het bestand.</span><span class="sxs-lookup"><span data-stu-id="448da-115">If the remaining objects have additional properties, those property values are not included in the file.</span></span>

## <span data-ttu-id="448da-116">VOORBEELDEN</span><span class="sxs-lookup"><span data-stu-id="448da-116">EXAMPLES</span></span>

### <span data-ttu-id="448da-117">Voor beeld 1: een webpagina maken om de datum weer te geven</span><span class="sxs-lookup"><span data-stu-id="448da-117">Example 1: Create a web page to display the date</span></span>

```powershell
ConvertTo-Html -InputObject (Get-Date)
```

<span data-ttu-id="448da-118">Met deze opdracht maakt u een HTML-pagina waarop de eigenschappen van de huidige datum worden weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="448da-118">This command creates an HTML page that displays the properties of the current date.</span></span> <span data-ttu-id="448da-119">De para meter **input object** wordt gebruikt om de resultaten van een `Get-Date` opdracht bij de cmdlet in te dienen `ConvertTo-Html` .</span><span class="sxs-lookup"><span data-stu-id="448da-119">It uses the **InputObject** parameter to submit the results of a `Get-Date` command to the `ConvertTo-Html` cmdlet.</span></span>

### <span data-ttu-id="448da-120">Voor beeld 2: een webpagina maken voor het weer geven van Power shell-aliassen</span><span class="sxs-lookup"><span data-stu-id="448da-120">Example 2: Create a web page to display PowerShell aliases</span></span>

```powershell
Get-Alias | ConvertTo-Html | Out-File aliases.htm
Invoke-Item aliases.htm
```

<span data-ttu-id="448da-121">Met deze opdracht maakt u een HTML-pagina waarop de Power shell-aliassen in de huidige console worden weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="448da-121">This command creates an HTML page that lists the PowerShell aliases in the current console.</span></span>

<span data-ttu-id="448da-122">De opdracht gebruikt de `Get-Alias` cmdlet om de aliassen op te halen.</span><span class="sxs-lookup"><span data-stu-id="448da-122">The command uses the `Get-Alias` cmdlet to get the aliases.</span></span> <span data-ttu-id="448da-123">Er wordt gebruikgemaakt van de pijplijn operator ( `|` ) om de aliassen te verzenden naar de `ConvertTo-Html` cmdlet, waarmee de HTML-pagina wordt gemaakt.</span><span class="sxs-lookup"><span data-stu-id="448da-123">It uses the pipeline operator (`|`) to send the aliases to the `ConvertTo-Html` cmdlet, which creates the HTML page.</span></span> <span data-ttu-id="448da-124">De opdracht gebruikt ook de `Out-File` cmdlet om de HTML-code naar het `aliases.htm` bestand te verzenden.</span><span class="sxs-lookup"><span data-stu-id="448da-124">The command also uses the `Out-File` cmdlet to send the HTML code to the `aliases.htm` file.</span></span>

### <span data-ttu-id="448da-125">Voor beeld 3: een webpagina maken om Power shell-gebeurtenissen weer te geven</span><span class="sxs-lookup"><span data-stu-id="448da-125">Example 3: Create a web page to display PowerShell events</span></span>

```powershell
`Get-EventLog` -LogName "Windows PowerShell" | ConvertTo-Html | Out-File pslog.htm
```

<span data-ttu-id="448da-126">Met deze opdracht maakt u een HTML-pagina `pslog.htm` met de naam waarmee de gebeurtenissen in het Windows Power shell-gebeurtenis logboek op de lokale computer worden weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="448da-126">This command creates an HTML page called `pslog.htm` that displays the events in the Windows PowerShell event log on the local computer.</span></span>

<span data-ttu-id="448da-127">De cmdlet wordt gebruikt `Get-EventLog` om de gebeurtenissen in het Windows Power shell-logboek op te halen. vervolgens wordt de pijplijn operator ( `|` ) gebruikt om de gebeurtenissen te verzenden naar de `ConvertTo-Html` cmdlet.</span><span class="sxs-lookup"><span data-stu-id="448da-127">It uses the `Get-EventLog` cmdlet to get the events in the Windows PowerShell log and then uses the pipeline operator (`|`) to send the events to the `ConvertTo-Html` cmdlet.</span></span> <span data-ttu-id="448da-128">De opdracht gebruikt ook de `Out-File` cmdlet om de HTML-code naar het `pslog.htm` bestand te verzenden.</span><span class="sxs-lookup"><span data-stu-id="448da-128">The command also uses the `Out-File` cmdlet to send the HTML code to the `pslog.htm` file.</span></span>

<span data-ttu-id="448da-129">De opdracht gebruikt ook de `Out-File` cmdlet om de HTML-code naar het `pslog.htm` bestand te verzenden.</span><span class="sxs-lookup"><span data-stu-id="448da-129">The command also uses the `Out-File` cmdlet to send the HTML code to the `pslog.htm` file.</span></span>

### <span data-ttu-id="448da-130">Voor beeld 4: een webpagina maken om processen weer te geven</span><span class="sxs-lookup"><span data-stu-id="448da-130">Example 4: Create a web page to display processes</span></span>

```powershell
Get-Process |
  ConvertTo-Html -Property Name, Path, Company -Title "Process Information" |
    Out-File proc.htm
Invoke-Item proc.htm
```

<span data-ttu-id="448da-131">Met deze opdrachten maakt en opent u een HTML-pagina met een lijst met de naam, het pad en het bedrijf van de processen op de lokale computer.</span><span class="sxs-lookup"><span data-stu-id="448da-131">These commands create and open an HTML page that lists the name, path, and company of the processes on the local computer.</span></span>

<span data-ttu-id="448da-132">De eerste opdracht gebruikt de `Get-Process` cmdlet om objecten op te halen die de processen vertegenwoordigen die worden uitgevoerd op de computer.</span><span class="sxs-lookup"><span data-stu-id="448da-132">The first command uses the `Get-Process` cmdlet to get objects that represent the processes running on the computer.</span></span> <span data-ttu-id="448da-133">De opdracht maakt gebruik van de pijplijn operator ( `|` ) om de proces objecten naar de `ConvertTo-Html` cmdlet te verzenden.</span><span class="sxs-lookup"><span data-stu-id="448da-133">The command uses the pipeline operator (`|`) to send the process objects to the `ConvertTo-Html` cmdlet.</span></span>

<span data-ttu-id="448da-134">De opdracht gebruikt de para meter **Property** om drie eigenschappen te selecteren van de proces objecten die in de tabel moeten worden opgenomen.</span><span class="sxs-lookup"><span data-stu-id="448da-134">The command uses the **Property** parameter to select three properties of the process objects to be included in the table.</span></span> <span data-ttu-id="448da-135">De opdracht gebruikt de para meter **title** om een titel voor de HTML-pagina op te geven.</span><span class="sxs-lookup"><span data-stu-id="448da-135">The command uses the **Title** parameter to specify a title for the HTML page.</span></span> <span data-ttu-id="448da-136">De opdracht gebruikt ook de `Out-File` cmdlet om de resulterende HTML naar een bestand met de naam Proc.htm te verzenden.</span><span class="sxs-lookup"><span data-stu-id="448da-136">The command also uses the `Out-File` cmdlet to send the resulting HTML to a file named Proc.htm.</span></span>

<span data-ttu-id="448da-137">Met de tweede opdracht wordt de `Invoke-Item` cmdlet gebruikt om de `Proc.htm` in de standaard browser te openen.</span><span class="sxs-lookup"><span data-stu-id="448da-137">The second command uses the `Invoke-Item` cmdlet to open the `Proc.htm` in the default browser.</span></span>

### <span data-ttu-id="448da-138">Voor beeld 5: een webpagina maken voor het weer geven van service objecten</span><span class="sxs-lookup"><span data-stu-id="448da-138">Example 5: Create a web page to display service objects</span></span>

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

<span data-ttu-id="448da-139">Met deze opdracht maakt u een HTML-pagina van de service objecten die door de `Get-Service` cmdlet worden geretourneerd.</span><span class="sxs-lookup"><span data-stu-id="448da-139">This command creates an HTML page of the service objects that the `Get-Service` cmdlet returns.</span></span> <span data-ttu-id="448da-140">De opdracht gebruikt de para meter **CssUri** om een trapsgewijs opmaak model voor de HTML-pagina op te geven.</span><span class="sxs-lookup"><span data-stu-id="448da-140">The command uses the **CssUri** parameter to specify a cascading style sheet for the HTML page.</span></span>

<span data-ttu-id="448da-141">De para meter **CssUri** voegt een extra `<link rel="stylesheet" type="text/css" href="test.css">` tag toe aan de resulterende HTML.</span><span class="sxs-lookup"><span data-stu-id="448da-141">The **CssUri** parameter adds an additional `<link rel="stylesheet" type="text/css" href="test.css">` tag to the resulting HTML.</span></span> <span data-ttu-id="448da-142">Het kenmerk HREF in het label bevat de naam van het opmaak model.</span><span class="sxs-lookup"><span data-stu-id="448da-142">The HREF attribute in the tag contains the name of the style sheet.</span></span>

### <span data-ttu-id="448da-143">Voor beeld 6: een webpagina maken voor het weer geven van service objecten</span><span class="sxs-lookup"><span data-stu-id="448da-143">Example 6: Create a web page to display service objects</span></span>

```powershell
Get-Service | ConvertTo-Html -As LIST | Out-File services.htm
```

<span data-ttu-id="448da-144">Met deze opdracht maakt u een HTML-pagina van de service objecten die door de `Get-Service` cmdlet worden geretourneerd.</span><span class="sxs-lookup"><span data-stu-id="448da-144">This command creates an HTML page of the service objects that the `Get-Service` cmdlet returns.</span></span> <span data-ttu-id="448da-145">De opdracht gebruikt de **as** -para meter om een lijst indeling op te geven.</span><span class="sxs-lookup"><span data-stu-id="448da-145">The command uses the **As** parameter to specify a list format.</span></span> <span data-ttu-id="448da-146">De cmdlet `Out-File` verzendt de resulterende HTML naar het `Services.htm` bestand.</span><span class="sxs-lookup"><span data-stu-id="448da-146">The cmdlet `Out-File` sends the resulting HTML to the `Services.htm` file.</span></span>

### <span data-ttu-id="448da-147">Voor beeld 7: een webtabel maken voor de huidige datum</span><span class="sxs-lookup"><span data-stu-id="448da-147">Example 7: Create a web table for the current date</span></span>

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

<span data-ttu-id="448da-148">Met deze opdracht wordt `ConvertTo-Html` een HTML-tabel van de huidige datum gegenereerd.</span><span class="sxs-lookup"><span data-stu-id="448da-148">This command uses `ConvertTo-Html` to generate an HTML table of the current date.</span></span> <span data-ttu-id="448da-149">De opdracht gebruikt de `Get-Date` cmdlet om de huidige datum op te halen.</span><span class="sxs-lookup"><span data-stu-id="448da-149">The command uses the `Get-Date` cmdlet to get the current date.</span></span> <span data-ttu-id="448da-150">Er wordt gebruikgemaakt van een pijplijn operator (|) om de resultaten naar de cmdlet te verzenden `ConvertTo-Html` .</span><span class="sxs-lookup"><span data-stu-id="448da-150">It uses a pipeline operator (|) to send the results to the `ConvertTo-Html` cmdlet.</span></span>

<span data-ttu-id="448da-151">De `ConvertTo-Html` opdracht bevat de **fragment** parameter, waarmee de uitvoer wordt beperkt tot een HTML-tabel.</span><span class="sxs-lookup"><span data-stu-id="448da-151">The `ConvertTo-Html` command includes the **Fragment** parameter, which limits the output to an HTML table.</span></span> <span data-ttu-id="448da-152">Als gevolg hiervan worden de andere elementen van een HTML-pagina, zoals de `<HEAD>` `<BODY>` Tags en wegge laten.</span><span class="sxs-lookup"><span data-stu-id="448da-152">As a result, the other elements of an HTML page, such as the `<HEAD>` and `<BODY>` tags, are omitted.</span></span>

### <span data-ttu-id="448da-153">Voor beeld 8: een webpagina maken om Power shell-gebeurtenissen weer te geven</span><span class="sxs-lookup"><span data-stu-id="448da-153">Example 8: Create a web page to display PowerShell events</span></span>

```powershell
Get-EventLog -Log "Windows PowerShell" | ConvertTo-Html -Property id, level, task
```

<span data-ttu-id="448da-154">Met deze opdracht wordt de `Get-EventLog` cmdlet gebruikt om gebeurtenissen van het Windows Power shell-gebeurtenis logboek op te halen.</span><span class="sxs-lookup"><span data-stu-id="448da-154">This command uses the `Get-EventLog` cmdlet to get events from the Windows PowerShell event log.</span></span>

<span data-ttu-id="448da-155">Er wordt een pijplijn operator ( `|` ) gebruikt om de gebeurtenissen te verzenden naar de `ConvertTo-Html` cmdlet, waarmee de gebeurtenissen worden geconverteerd naar een HTML-indeling.</span><span class="sxs-lookup"><span data-stu-id="448da-155">It uses a pipeline operator (`|`) to send the events to the `ConvertTo-Html` cmdlet, which converts the events to HTML format.</span></span>

<span data-ttu-id="448da-156">De `ConvertTo-Html` opdracht gebruikt de para meter **Property** om alleen de eigenschappen **id** , **niveau** en **Task** van de gebeurtenis te selecteren.</span><span class="sxs-lookup"><span data-stu-id="448da-156">The `ConvertTo-Html` command uses the **Property** parameter to select only the **ID** , **Level** , and **Task** properties of the event.</span></span>

### <span data-ttu-id="448da-157">Voor beeld 9: een webpagina maken om opgegeven services weer te geven</span><span class="sxs-lookup"><span data-stu-id="448da-157">Example 9: Create a web page to display specified services</span></span>

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

<span data-ttu-id="448da-158">Met deze opdracht wordt een webpagina gemaakt en geopend waarop de services op de computer worden weer gegeven die beginnen met een. Het maakt gebruik van de para meters **titel** , **hoofd tekst** **, voor-en** **PostContent** van `ConvertTo-Html` om de uitvoer aan te passen.</span><span class="sxs-lookup"><span data-stu-id="448da-158">This command creates and opens a Web page that displays the services on the computer that begin with A. It uses the **Title** , **Body** , **PreContent** , and **PostContent** parameters of `ConvertTo-Html` to customize the output.</span></span>

<span data-ttu-id="448da-159">Het eerste deel van de opdracht gebruikt de `Get-Service` cmdlet om de services op de computer te verkrijgen die met een beginnen. De opdracht maakt gebruik van een pijplijn operator ( `|` ) om de resultaten naar de `ConvertTo-Html` cmdlet te verzenden.</span><span class="sxs-lookup"><span data-stu-id="448da-159">The first part of the command uses the `Get-Service` cmdlet to get the services on the computer that begin with A. The command uses a pipeline operator (`|`) to send the results to the `ConvertTo-Html` cmdlet.</span></span> <span data-ttu-id="448da-160">De opdracht gebruikt ook de `Out-File` cmdlet om de uitvoer naar het Services.htm-bestand te verzenden.</span><span class="sxs-lookup"><span data-stu-id="448da-160">The command also uses the `Out-File` cmdlet to send the output to the Services.htm file.</span></span>

<span data-ttu-id="448da-161">Een punt komma ( `;` ) eindigt de eerste opdracht en start een tweede opdracht, waarbij de `Invoke-Item` cmdlet wordt gebruikt om het bestand te openen `Services.htm` in de standaard browser.</span><span class="sxs-lookup"><span data-stu-id="448da-161">A semicolon (`;`) ends the first command and starts a second command, which uses the `Invoke-Item` cmdlet to open the `Services.htm` file in the default browser.</span></span>

## <span data-ttu-id="448da-162">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="448da-162">PARAMETERS</span></span>

### <span data-ttu-id="448da-163">-As</span><span class="sxs-lookup"><span data-stu-id="448da-163">-As</span></span>

<span data-ttu-id="448da-164">Bepaalt of het object wordt opgemaakt als een tabel of een lijst.</span><span class="sxs-lookup"><span data-stu-id="448da-164">Determines whether the object is formatted as a table or a list.</span></span> <span data-ttu-id="448da-165">Geldige waarden zijn **tabel** en **lijst**.</span><span class="sxs-lookup"><span data-stu-id="448da-165">Valid values are **Table** and **List**.</span></span> <span data-ttu-id="448da-166">De standaard waarde is **Table**.</span><span class="sxs-lookup"><span data-stu-id="448da-166">The default value is **Table**.</span></span>

<span data-ttu-id="448da-167">De **tabel** waarde genereert een HTML-tabel die overeenkomt met de indeling van de Power shell-tabel.</span><span class="sxs-lookup"><span data-stu-id="448da-167">The **Table** value generates an HTML table that resembles the PowerShell table format.</span></span> <span data-ttu-id="448da-168">In de rij met koppen worden de namen van eigenschappen weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="448da-168">The header row displays the property names.</span></span> <span data-ttu-id="448da-169">Elke tabelrij vertegenwoordigt een object en geeft de waarden van het object voor elke eigenschap.</span><span class="sxs-lookup"><span data-stu-id="448da-169">Each table row represents an object and displays the object's values for each property.</span></span>

<span data-ttu-id="448da-170">De **lijst** waarde genereert een HTML-tabel met twee kolommen voor elk object dat lijkt op de Power shell-lijst indeling.</span><span class="sxs-lookup"><span data-stu-id="448da-170">The **List** value generates a two-column HTML table for each object that resembles the PowerShell list format.</span></span> <span data-ttu-id="448da-171">In de eerste kolom wordt de naam van de eigenschap weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="448da-171">The first column displays the property name.</span></span> <span data-ttu-id="448da-172">De tweede kolom bevat de waarde van de eigenschap.</span><span class="sxs-lookup"><span data-stu-id="448da-172">The second column displays the property value.</span></span>

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

### <span data-ttu-id="448da-173">-Hoofd tekst</span><span class="sxs-lookup"><span data-stu-id="448da-173">-Body</span></span>

<span data-ttu-id="448da-174">Hiermee geeft u de tekst op die moet worden toegevoegd na de openings `<BODY>` code.</span><span class="sxs-lookup"><span data-stu-id="448da-174">Specifies the text to add after the opening `<BODY>` tag.</span></span> <span data-ttu-id="448da-175">Standaard is er geen tekst op die positie.</span><span class="sxs-lookup"><span data-stu-id="448da-175">By default, there is no text in that position.</span></span>

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

### <span data-ttu-id="448da-176">-CssUri</span><span class="sxs-lookup"><span data-stu-id="448da-176">-CssUri</span></span>

<span data-ttu-id="448da-177">Hiermee geeft u de URI (Uniform Resource Identifier) van het trapsgewijze opmaak model (CSS) op dat wordt toegepast op het HTML-bestand.</span><span class="sxs-lookup"><span data-stu-id="448da-177">Specifies the Uniform Resource Identifier (URI) of the cascading style sheet (CSS) that is applied to the HTML file.</span></span> <span data-ttu-id="448da-178">De URI wordt opgenomen in een koppeling naar een opmaak model in de uitvoer.</span><span class="sxs-lookup"><span data-stu-id="448da-178">The URI is included in a style sheet link in the output.</span></span>

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

### <span data-ttu-id="448da-179">-Fragment</span><span class="sxs-lookup"><span data-stu-id="448da-179">-Fragment</span></span>

<span data-ttu-id="448da-180">Genereert alleen een HTML-tabel.</span><span class="sxs-lookup"><span data-stu-id="448da-180">Generates only an HTML table.</span></span> <span data-ttu-id="448da-181">De tags HTML, HEAD, TITLE en BODY worden wegge laten.</span><span class="sxs-lookup"><span data-stu-id="448da-181">The HTML, HEAD, TITLE, and BODY tags are omitted.</span></span>

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

### <span data-ttu-id="448da-182">-Head</span><span class="sxs-lookup"><span data-stu-id="448da-182">-Head</span></span>

<span data-ttu-id="448da-183">Hiermee geeft u de inhoud van de `<HEAD>` tag.</span><span class="sxs-lookup"><span data-stu-id="448da-183">Specifies the content of the `<HEAD>` tag.</span></span> <span data-ttu-id="448da-184">De standaardwaarde is `<title\>HTML TABLE</title>`.</span><span class="sxs-lookup"><span data-stu-id="448da-184">The default is `<title\>HTML TABLE</title>`.</span></span> <span data-ttu-id="448da-185">Als u de para meter **Head** gebruikt, wordt de para meter **title** genegeerd.</span><span class="sxs-lookup"><span data-stu-id="448da-185">If you use the **Head** parameter, the **Title** parameter is ignored.</span></span>

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

### <span data-ttu-id="448da-186">-Input object</span><span class="sxs-lookup"><span data-stu-id="448da-186">-InputObject</span></span>

<span data-ttu-id="448da-187">Hiermee geeft u de objecten op die in HTML moeten worden weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="448da-187">Specifies the objects to be represented in HTML.</span></span> <span data-ttu-id="448da-188">Voer een variabele in die de objecten bevat of typ een opdracht of expressie waarmee de objecten worden opgehaald.</span><span class="sxs-lookup"><span data-stu-id="448da-188">Enter a variable that contains the objects or type a command or expression that gets the objects.</span></span>

<span data-ttu-id="448da-189">Als u deze para meter gebruikt voor het indienen van meerdere objecten, zoals alle services op een computer, `ConvertTo-Html` wordt een tabel gemaakt waarin de eigenschappen van een verzameling of een matrix met objecten worden weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="448da-189">If you use this parameter to submit multiple objects, such as all of the services on a computer, `ConvertTo-Html` creates a table that displays the properties of a collection or of an array of objects.</span></span> <span data-ttu-id="448da-190">Als u een tabel van de afzonderlijke objecten wilt maken, gebruikt u de pijplijn operator om de objecten naar te sluizen `ConvertTo-Html` .</span><span class="sxs-lookup"><span data-stu-id="448da-190">To create a table of the individual objects, use the pipeline operator to pipe the objects to `ConvertTo-Html`.</span></span>

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

### <span data-ttu-id="448da-191">-PostContent</span><span class="sxs-lookup"><span data-stu-id="448da-191">-PostContent</span></span>

<span data-ttu-id="448da-192">Geeft aan dat er tekst moet worden toegevoegd na de afsluitende `</TABLE>` tag.</span><span class="sxs-lookup"><span data-stu-id="448da-192">Specifies text to add after the closing `</TABLE>` tag.</span></span> <span data-ttu-id="448da-193">Standaard is er geen tekst op die positie.</span><span class="sxs-lookup"><span data-stu-id="448da-193">By default, there is no text in that position.</span></span>

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

### <span data-ttu-id="448da-194">-Precontent</span><span class="sxs-lookup"><span data-stu-id="448da-194">-PreContent</span></span>

<span data-ttu-id="448da-195">Hiermee geeft u de tekst die moet worden toegevoegd voor de openings `<TABLE>` code.</span><span class="sxs-lookup"><span data-stu-id="448da-195">Specifies text to add before the opening `<TABLE>` tag.</span></span> <span data-ttu-id="448da-196">Standaard is er geen tekst op die positie.</span><span class="sxs-lookup"><span data-stu-id="448da-196">By default, there is no text in that position.</span></span>

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

### <span data-ttu-id="448da-197">-Eigenschap</span><span class="sxs-lookup"><span data-stu-id="448da-197">-Property</span></span>

<span data-ttu-id="448da-198">Bevat de opgegeven eigenschappen van de objecten in de HTML.</span><span class="sxs-lookup"><span data-stu-id="448da-198">Includes the specified properties of the objects in the HTML.</span></span> <span data-ttu-id="448da-199">De waarde van de **eigenschaps** parameter kan een nieuwe berekende eigenschap zijn.</span><span class="sxs-lookup"><span data-stu-id="448da-199">The value of the **Property** parameter can be a new calculated property.</span></span> <span data-ttu-id="448da-200">De berekende eigenschap kan een script blok of een hash-tabel zijn.</span><span class="sxs-lookup"><span data-stu-id="448da-200">The calculated property can be a script block or a hash table.</span></span> <span data-ttu-id="448da-201">Geldige sleutel-waardeparen zijn:</span><span class="sxs-lookup"><span data-stu-id="448da-201">Valid key-value pairs are:</span></span>

- <span data-ttu-id="448da-202">Expressie- `<string>` of `<script block>`</span><span class="sxs-lookup"><span data-stu-id="448da-202">Expression - `<string>` or `<script block>`</span></span>
- <span data-ttu-id="448da-203">Tring `<string>`</span><span class="sxs-lookup"><span data-stu-id="448da-203">FormatString - `<string>`</span></span>
- <span data-ttu-id="448da-204">Breedte: `<int32>` moet groter zijn dan `0`</span><span class="sxs-lookup"><span data-stu-id="448da-204">Width - `<int32>` - must be greater than `0`</span></span>
- <span data-ttu-id="448da-205">Uitlijning-waarde kan `Left` , `Center` of `Right`</span><span class="sxs-lookup"><span data-stu-id="448da-205">Alignment - value can be `Left`, `Center`, or `Right`</span></span>

<span data-ttu-id="448da-206">Zie [about_Calculated_Properties](../Microsoft.PowerShell.Core/About/about_Calculated_Properties.md)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="448da-206">For more information, see [about_Calculated_Properties](../Microsoft.PowerShell.Core/About/about_Calculated_Properties.md).</span></span>

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

### <span data-ttu-id="448da-207">-Titel</span><span class="sxs-lookup"><span data-stu-id="448da-207">-Title</span></span>

<span data-ttu-id="448da-208">Hiermee geeft u een titel voor het HTML-bestand, dat wil zeggen, de tekst die wordt weer gegeven tussen de `<TITLE>` Tags.</span><span class="sxs-lookup"><span data-stu-id="448da-208">Specifies a title for the HTML file, that is, the text that appears between the `<TITLE>` tags.</span></span>

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

### <span data-ttu-id="448da-209">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="448da-209">CommonParameters</span></span>

<span data-ttu-id="448da-210">Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="448da-210">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="448da-211">Zie [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="448da-211">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="448da-212">INVOER</span><span class="sxs-lookup"><span data-stu-id="448da-212">INPUTS</span></span>

### <span data-ttu-id="448da-213">System. Management. Automation. PSObject</span><span class="sxs-lookup"><span data-stu-id="448da-213">System.Management.Automation.PSObject</span></span>

<span data-ttu-id="448da-214">U kunt elk .NET-object door sluizen naar `ConvertTo-Html` .</span><span class="sxs-lookup"><span data-stu-id="448da-214">You can pipe any .NET object to `ConvertTo-Html`.</span></span>

## <span data-ttu-id="448da-215">UITVOER</span><span class="sxs-lookup"><span data-stu-id="448da-215">OUTPUTS</span></span>

### <span data-ttu-id="448da-216">Systeem. teken reeks of System.Xml.Xmldocument</span><span class="sxs-lookup"><span data-stu-id="448da-216">System.String or System.Xml.XmlDocument</span></span>

<span data-ttu-id="448da-217">`ConvertTo-Html` retourneert reeksen van teken reeksen waaruit een geldige HTML bestaat.</span><span class="sxs-lookup"><span data-stu-id="448da-217">`ConvertTo-Html` returns series of strings that comprise valid HTML.</span></span>

## <span data-ttu-id="448da-218">OPMERKINGEN</span><span class="sxs-lookup"><span data-stu-id="448da-218">NOTES</span></span>

<span data-ttu-id="448da-219">Als u deze cmdlet wilt gebruiken, pipet u een of meer objecten aan de cmdlet of gebruikt u de para meter **input object** om het object op te geven.</span><span class="sxs-lookup"><span data-stu-id="448da-219">To use this cmdlet, pipe one or more objects to the cmdlet or use the **InputObject** parameter to specify the object.</span></span> <span data-ttu-id="448da-220">Wanneer de invoer uit meerdere objecten bestaat, is de uitvoer van deze twee methoden heel anders.</span><span class="sxs-lookup"><span data-stu-id="448da-220">When the input consists of multiple objects, the output of these two methods is quite different.</span></span>

- <span data-ttu-id="448da-221">Wanneer u meerdere objecten naar een cmdlet Pipet, verzendt Power shell de objecten per keer naar de cmdlet.</span><span class="sxs-lookup"><span data-stu-id="448da-221">When you pipe multiple objects to a cmdlet, PowerShell sends the objects to the cmdlet one at a time.</span></span> <span data-ttu-id="448da-222">Als gevolg hiervan `ConvertTo-Html` wordt een tabel gemaakt waarin de afzonderlijke objecten worden weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="448da-222">As a result, `ConvertTo-Html` creates a table that displays the individual objects.</span></span> <span data-ttu-id="448da-223">Als u bijvoorbeeld de processen op een computer wilt `ConvertTo-Html` door sluizen, worden in de resulterende tabel alle processen weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="448da-223">For example, if you pipe the processes on a computer to `ConvertTo-Html`, the resulting table displays all of the processes.</span></span>

- <span data-ttu-id="448da-224">Wanneer u de para meter **input object** gebruikt voor het verzenden van meerdere objecten, `ConvertTo-Html` ontvangt deze objecten als een verzameling of als een matrix.</span><span class="sxs-lookup"><span data-stu-id="448da-224">When you use the **InputObject** parameter to submit multiple objects, `ConvertTo-Html` receives these objects as a collection or as an array.</span></span> <span data-ttu-id="448da-225">Als gevolg hiervan wordt een tabel gemaakt waarin de matrix en de bijbehorende eigenschappen worden weer gegeven, niet de items in de matrix.</span><span class="sxs-lookup"><span data-stu-id="448da-225">As a result, it creates a table that displays the array and its properties, not the items in the array.</span></span> <span data-ttu-id="448da-226">Als u bijvoorbeeld **input object** gebruikt om de processen op een computer in te dienen `ConvertTo-Html` , worden in de resulterende tabel een object matrix en de bijbehorende eigenschappen weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="448da-226">For example, if you use **InputObject** to submit the processes on a computer to `ConvertTo-Html`, the resulting table displays an object array and its properties.</span></span>

  <span data-ttu-id="448da-227">Om te voldoen aan de XHTML Strict DTD, wordt de DOCTYPE-tag dienovereenkomstig gewijzigd:</span><span class="sxs-lookup"><span data-stu-id="448da-227">To comply with the XHTML Strict DTD, the DOCTYPE tag is modified accordingly:</span></span>

   `<!DOCTYPE html PUBLIC "-//W3C//DTD XHTML 1.0 Strict//EN"   "https://www.w3.org/TR/xhtml1/DTD/xhtml1-strict.dtd"\>`

## <span data-ttu-id="448da-228">GERELATEERDE KOPPELINGEN</span><span class="sxs-lookup"><span data-stu-id="448da-228">RELATED LINKS</span></span>

[<span data-ttu-id="448da-229">about_Calculated_Properties</span><span class="sxs-lookup"><span data-stu-id="448da-229">about_Calculated_Properties</span></span>](../Microsoft.PowerShell.Core/About/about_Calculated_Properties.md)

[<span data-ttu-id="448da-230">ConvertTo-Csv</span><span class="sxs-lookup"><span data-stu-id="448da-230">ConvertTo-Csv</span></span>](ConvertTo-Csv.md)

[<span data-ttu-id="448da-231">ConvertTo-Json</span><span class="sxs-lookup"><span data-stu-id="448da-231">ConvertTo-Json</span></span>](ConvertTo-Json.md)

[<span data-ttu-id="448da-232">ConvertTo-Xml</span><span class="sxs-lookup"><span data-stu-id="448da-232">ConvertTo-Xml</span></span>](ConvertTo-Xml.md)

[<span data-ttu-id="448da-233">Exporteren-Clixml</span><span class="sxs-lookup"><span data-stu-id="448da-233">Export-Clixml</span></span>](Export-Clixml.md)

[<span data-ttu-id="448da-234">Import-Clixml</span><span class="sxs-lookup"><span data-stu-id="448da-234">Import-Clixml</span></span>](Import-Clixml.md)
