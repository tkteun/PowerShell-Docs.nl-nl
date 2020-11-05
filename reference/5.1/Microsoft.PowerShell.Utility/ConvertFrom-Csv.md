---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 12/21/2018
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/convertfrom-csv?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: ConvertFrom-Csv
ms.openlocfilehash: 483f3767af4df9e5e044ab3b46811f22b63a5723
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/07/2020
ms.locfileid: "93250481"
---
# <span data-ttu-id="1ac80-103">ConvertFrom-Csv</span><span class="sxs-lookup"><span data-stu-id="1ac80-103">ConvertFrom-Csv</span></span>

## <span data-ttu-id="1ac80-104">SAMENVATTING</span><span class="sxs-lookup"><span data-stu-id="1ac80-104">SYNOPSIS</span></span>
<span data-ttu-id="1ac80-105">Converteert object eigenschappen in CSV-indeling (door komma's gescheiden waarden) naar CSV-versies van de oorspronkelijke objecten.</span><span class="sxs-lookup"><span data-stu-id="1ac80-105">Converts object properties in comma-separated value (CSV) format into CSV versions of the original objects.</span></span>

## <span data-ttu-id="1ac80-106">SYNTAXIS</span><span class="sxs-lookup"><span data-stu-id="1ac80-106">SYNTAX</span></span>

### <span data-ttu-id="1ac80-107">Scheidings teken (standaard)</span><span class="sxs-lookup"><span data-stu-id="1ac80-107">Delimiter (Default)</span></span>

```
ConvertFrom-Csv [-InputObject] <psobject[]> [[-Delimiter] <char>] [-Header <string[]>]
 [<CommonParameters>]
```

### <span data-ttu-id="1ac80-108">UseCulture</span><span class="sxs-lookup"><span data-stu-id="1ac80-108">UseCulture</span></span>

```
ConvertFrom-Csv [-InputObject] <psobject[]> -UseCulture [-Header <string[]>] [<CommonParameters>]
```

## <span data-ttu-id="1ac80-109">BESCHRIJVING</span><span class="sxs-lookup"><span data-stu-id="1ac80-109">DESCRIPTION</span></span>

<span data-ttu-id="1ac80-110">De `ConvertFrom-Csv` cmdlet maakt objecten van teken reeksen met variabele lengte van CSV die door de `ConvertTo-Csv` cmdlet worden gegenereerd.</span><span class="sxs-lookup"><span data-stu-id="1ac80-110">The `ConvertFrom-Csv` cmdlet creates objects from CSV variable-length strings that are generated by the `ConvertTo-Csv` cmdlet.</span></span>

<span data-ttu-id="1ac80-111">U kunt de para meters van deze cmdlet gebruiken om de rij met kolom koppen op te geven, waarmee de eigenschapnamen van de resulterende objecten worden bepaald, het scheidings teken voor het item moet worden opgegeven, of deze cmdlet moet worden omgeleid om het lijst scheidings teken voor de huidige cultuur als scheidings teken te gebruiken.</span><span class="sxs-lookup"><span data-stu-id="1ac80-111">You can use the parameters of this cmdlet to specify the column header row, which determines the property names of the resulting objects, to specify the item delimiter, or to direct this cmdlet to use the list separator for the current culture as the delimiter.</span></span>

<span data-ttu-id="1ac80-112">De objecten die `ConvertFrom-Csv` worden gemaakt, zijn CSV-versies van de oorspronkelijke objecten.</span><span class="sxs-lookup"><span data-stu-id="1ac80-112">The objects that `ConvertFrom-Csv` creates are CSV versions of the original objects.</span></span> <span data-ttu-id="1ac80-113">De eigenschaps waarden van de CSV-objecten zijn teken reeks versies van de eigenschaps waarden van de oorspronkelijke objecten.</span><span class="sxs-lookup"><span data-stu-id="1ac80-113">The property values of the CSV objects are string versions of the property values of the original objects.</span></span> <span data-ttu-id="1ac80-114">De CSV-versies van de objecten hebben geen enkele methode.</span><span class="sxs-lookup"><span data-stu-id="1ac80-114">The CSV versions of the objects do not have any methods.</span></span>

<span data-ttu-id="1ac80-115">U kunt ook de `Export-Csv` `Import-Csv` cmdlets en gebruiken om objecten te converteren naar CSV-teken reeksen in een bestand (en terug).</span><span class="sxs-lookup"><span data-stu-id="1ac80-115">You can also use the `Export-Csv` and `Import-Csv` cmdlets to convert objects to CSV strings in a file (and back).</span></span> <span data-ttu-id="1ac80-116">Deze cmdlets zijn hetzelfde als de `ConvertTo-Csv` -en `ConvertFrom-Csv` -cmdlets, behalve dat ze de CSV-teken reeksen in een bestand opslaan.</span><span class="sxs-lookup"><span data-stu-id="1ac80-116">These cmdlets are the same as the `ConvertTo-Csv` and `ConvertFrom-Csv` cmdlets, except that they save the CSV strings in a file.</span></span>

## <span data-ttu-id="1ac80-117">VOORBEELDEN</span><span class="sxs-lookup"><span data-stu-id="1ac80-117">EXAMPLES</span></span>

### <span data-ttu-id="1ac80-118">Voor beeld 1: processen op de lokale computer converteren naar CSV-indeling</span><span class="sxs-lookup"><span data-stu-id="1ac80-118">Example 1: Convert processes on the local computer to CSV format</span></span>

<span data-ttu-id="1ac80-119">In dit voor beeld ziet u hoe u de processen op de lokale computer converteert naar CSV-indeling en deze vervolgens herstelt in een object formulier.</span><span class="sxs-lookup"><span data-stu-id="1ac80-119">This example shows how to convert the processes on the local computer into CSV format and then restore them to object form.</span></span>

```powershell
$P = Get-Process | ConvertTo-Csv
$P | ConvertFrom-Csv
```

<span data-ttu-id="1ac80-120">De `Get-Process` cmdlet verstuurt de processen van de pijp lijn naar `ConvertTo-Csv` .</span><span class="sxs-lookup"><span data-stu-id="1ac80-120">The `Get-Process` cmdlet sends the processes down the pipeline to `ConvertTo-Csv`.</span></span> <span data-ttu-id="1ac80-121">`ConvertTo-Csv`Met de cmdlet worden de proces objecten geconverteerd naar een reeks CSV-teken reeksen.</span><span class="sxs-lookup"><span data-stu-id="1ac80-121">The `ConvertTo-Csv` cmdlet converts the process objects to a series of CSV strings.</span></span> <span data-ttu-id="1ac80-122">De `ConvertFrom-Csv` cmdlet converteert de CSV-teken reeksen naar CSV-versies van de oorspronkelijke proces objecten.</span><span class="sxs-lookup"><span data-stu-id="1ac80-122">The `ConvertFrom-Csv` cmdlet converts the CSV strings into CSV versions of the original process objects.</span></span> <span data-ttu-id="1ac80-123">De CSV-teken reeksen worden opgeslagen in de `$P` variabele.</span><span class="sxs-lookup"><span data-stu-id="1ac80-123">The CSV strings are saved in the `$P` variable.</span></span>

### <span data-ttu-id="1ac80-124">Voor beeld 2: een gegevens object converteren naar de CSV-indeling en vervolgens naar de CSV-object indeling</span><span class="sxs-lookup"><span data-stu-id="1ac80-124">Example 2: Convert a data object to CSV format and then to CSV object format</span></span>

<span data-ttu-id="1ac80-125">In dit voor beeld ziet u hoe u een gegevens object converteert naar CSV-indeling en vervolgens naar CSV-object indeling.</span><span class="sxs-lookup"><span data-stu-id="1ac80-125">This example shows how to convert a data object to CSV format and then to CSV object format.</span></span>

```powershell
$Date = Get-Date | ConvertTo-Csv -Delimiter ';'
ConvertFrom-Csv -InputObject $Date -Delimiter ';'
```

<span data-ttu-id="1ac80-126">Met de eerste opdracht wordt `Get-Date` de huidige datum en tijd naar beneden verzonden in de pijp lijn `ConvertTo-Csv` .</span><span class="sxs-lookup"><span data-stu-id="1ac80-126">The first command uses `Get-Date` to send the current date and time down the pipeline to `ConvertTo-Csv`.</span></span> <span data-ttu-id="1ac80-127">`ConvertTo-Csv`Met de cmdlet wordt het object Date geconverteerd naar een reeks CSV-teken reeksen.</span><span class="sxs-lookup"><span data-stu-id="1ac80-127">The `ConvertTo-Csv` cmdlet converts the date object to a series of CSV strings.</span></span>
<span data-ttu-id="1ac80-128">De para meter **scheidings teken** wordt gebruikt om een punt komma als scheidings teken op te geven.</span><span class="sxs-lookup"><span data-stu-id="1ac80-128">The **Delimiter** parameter is used to specify a semicolon delimiter.</span></span> <span data-ttu-id="1ac80-129">De teken reeksen worden opgeslagen in de `$Date` variabele.</span><span class="sxs-lookup"><span data-stu-id="1ac80-129">The strings are saved in the `$Date` variable.</span></span>

### <span data-ttu-id="1ac80-130">Voor beeld 3: de para meter header gebruiken om de namen van eigenschappen te wijzigen</span><span class="sxs-lookup"><span data-stu-id="1ac80-130">Example 3: Use the header parameter to change the names of properties</span></span>

<span data-ttu-id="1ac80-131">In dit voor beeld ziet u hoe u de para meter **header** van kunt gebruiken `ConvertFrom-Csv` om de namen van eigenschappen in het resulterende geïmporteerde object te wijzigen.</span><span class="sxs-lookup"><span data-stu-id="1ac80-131">This example shows how to use the **Header** parameter of `ConvertFrom-Csv` to change the names of properties in the resulting imported object.</span></span>

```powershell
$J = Start-Job -ScriptBlock { Get-Process } | ConvertTo-Csv  -NoTypeInformation
$Header = 'State', 'MoreData', 'StatusMessage', 'Location', 'Command', 'StateInfo', 'Finished', 'InstanceId', 'Id', 'Name', 'ChildJobs', 'BeginTime', 'EndTime', 'JobType', 'Output', 'Error', 'Progress', 'Verbose', 'Debug', 'Warning', 'Information'
# Delete the default header from $J
$J = $J[1..($J.count - 1)]
$J | ConvertFrom-Csv -Header $Header
```

```Output
State         : Running
MoreData      : True
StatusMessage :
Location      : localhost
Command       : Get-Process
StateInfo     : Running
Finished      : System.Threading.ManualResetEvent
InstanceId    : a259eb63-6824-4b97-a033-305108ae1c2e
Id            : 1
Name          : Job1
ChildJobs     : System.Collections.Generic.List`1[System.Management.Automation.Job]
BeginTime     : 12/20/2018 18:59:57
EndTime       :
JobType       : BackgroundJob
Output        : System.Management.Automation.PSDataCollection`1[System.Management.Automation.PSObject]
Error         : System.Management.Automation.PSDataCollection`1[System.Management.Automation.ErrorRecord]
Progress      : System.Management.Automation.PSDataCollection`1[System.Management.Automation.ProgressRecord]
Verbose       : System.Management.Automation.PSDataCollection`1[System.Management.Automation.VerboseRecord]
Debug         : System.Management.Automation.PSDataCollection`1[System.Management.Automation.DebugRecord]
Warning       : System.Management.Automation.PSDataCollection`1[System.Management.Automation.WarningRecord]
Information   : System.Management.Automation.PSDataCollection`1[System.Management.Automation.InformationRecord]
```

<span data-ttu-id="1ac80-132">`Start-Job`Met de cmdlet wordt een achtergrond taak gestart die wordt uitgevoerd `Get-Process` .</span><span class="sxs-lookup"><span data-stu-id="1ac80-132">The `Start-Job` cmdlet starts a background job that runs `Get-Process`.</span></span> <span data-ttu-id="1ac80-133">Er wordt een taak object naar de pijp lijn verzonden naar `ConvertTo-Csv` en geconverteerd naar een CSV-teken reeks.</span><span class="sxs-lookup"><span data-stu-id="1ac80-133">A job object is sent down the pipeline to `ConvertTo-Csv` and converted to a CSV string.</span></span> <span data-ttu-id="1ac80-134">Met de para meter **NoTypeInformation** wordt de type-informatie header uit de CSV-uitvoer verwijderd en is deze optioneel in Power shell core.</span><span class="sxs-lookup"><span data-stu-id="1ac80-134">The **NoTypeInformation** parameter removes the type information header from CSV output and is optional in PowerShell Core.</span></span> <span data-ttu-id="1ac80-135">De `$Header` variabele bevat een aangepaste koptekst waarmee de volgende standaard waarden worden vervangen: **HasMoreData** , **JobStateInfo** , **PSBeginTime** , **PSEndTime** en **PSJobTypeName**.</span><span class="sxs-lookup"><span data-stu-id="1ac80-135">The `$Header` variable contains a custom header that replaces the following default values: **HasMoreData** , **JobStateInfo** , **PSBeginTime** , **PSEndTime** , and **PSJobTypeName**.</span></span> <span data-ttu-id="1ac80-136">De `$J` variabele bevat de CSV-teken reeks en wordt gebruikt om de standaard header te verwijderen.</span><span class="sxs-lookup"><span data-stu-id="1ac80-136">The `$J` variable contains the CSV string and is used to remove the default header.</span></span> <span data-ttu-id="1ac80-137">De `ConvertFrom-Csv` cmdlet converteert de CSV-teken reeks naar een **PSCustomObject** en gebruikt de para meter **header** om de variabele toe te passen `$Header` .</span><span class="sxs-lookup"><span data-stu-id="1ac80-137">The `ConvertFrom-Csv` cmdlet converts the CSV string into a **PSCustomObject** and uses the **Header** parameter to apply the `$Header` variable.</span></span>

### <span data-ttu-id="1ac80-138">Voor beeld 4: CSV-teken reeksen van service objecten converteren</span><span class="sxs-lookup"><span data-stu-id="1ac80-138">Example 4: Convert CSV strings of service objects</span></span>

<span data-ttu-id="1ac80-139">In dit voor beeld ziet u hoe u de `ConvertFrom-Csv` cmdlet gebruikt met de para meter **UseCulture** .</span><span class="sxs-lookup"><span data-stu-id="1ac80-139">This example shows how to use the `ConvertFrom-Csv` cmdlet with the **UseCulture** parameter.</span></span>

```powershell
(Get-Culture).TextInfo.ListSeparator
$Services = (Get-Service | ConvertTo-Csv)
ConvertFrom-Csv -InputObject $Services -UseCulture
```

<span data-ttu-id="1ac80-140">De `Get-Culture` cmdlet gebruikt de geneste eigenschappen **Eigenschappen** en **ListSeparator** om het standaard lijst scheidings teken van de huidige cultuur op te halen.</span><span class="sxs-lookup"><span data-stu-id="1ac80-140">The `Get-Culture` cmdlet uses the nested properties **TextInfo** and **ListSeparator** to get the current culture's default list separator.</span></span> <span data-ttu-id="1ac80-141">De `Get-Service` cmdlet verzendt service objecten naar beneden de pijp lijn naar `ConvertTo-Csv` .</span><span class="sxs-lookup"><span data-stu-id="1ac80-141">The `Get-Service` cmdlet sends service objects down the pipeline to `ConvertTo-Csv`.</span></span> <span data-ttu-id="1ac80-142">De `ConvertTo-Csv` service objecten worden geconverteerd naar een reeks CSV-teken reeksen.</span><span class="sxs-lookup"><span data-stu-id="1ac80-142">The `ConvertTo-Csv` converts the service objects to a series of CSV strings.</span></span> <span data-ttu-id="1ac80-143">De CSV-teken reeksen worden opgeslagen in de `$Services` variabele.</span><span class="sxs-lookup"><span data-stu-id="1ac80-143">The CSV strings are stored in the `$Services` variable.</span></span> <span data-ttu-id="1ac80-144">De `ConvertFrom-Csv` cmdlet gebruikt de para meter **input object** en converteert de CSV-teken reeksen uit de `$Services` variabele.</span><span class="sxs-lookup"><span data-stu-id="1ac80-144">The `ConvertFrom-Csv` cmdlet uses the **InputObject** parameter and converts the CSV strings from the `$Services` variable.</span></span> <span data-ttu-id="1ac80-145">De para meter **UseCulture** maakt gebruik van het standaard lijst scheidings teken van de huidige cultuur.</span><span class="sxs-lookup"><span data-stu-id="1ac80-145">The **UseCulture** parameter uses the current culture's default list separator.</span></span>

<span data-ttu-id="1ac80-146">Wanneer de para meter **UseCulture** wordt gebruikt, moet u ervoor zorgen dat het standaard scheidings teken van de huidige cultuur overeenkomt met het scheidings teken dat wordt gebruikt in de CSV-teken reeksen.</span><span class="sxs-lookup"><span data-stu-id="1ac80-146">When the **UseCulture** parameter is used, be sure that the current culture's default list separator matches the delimiter used in the CSV strings.</span></span> <span data-ttu-id="1ac80-147">Anders `ConvertFrom-Csv` kan er geen objecten worden gegenereerd op basis van de CSV-teken reeksen.</span><span class="sxs-lookup"><span data-stu-id="1ac80-147">Otherwise, `ConvertFrom-Csv` cannot generate objects from the CSV strings.</span></span>

## <span data-ttu-id="1ac80-148">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="1ac80-148">PARAMETERS</span></span>

### <span data-ttu-id="1ac80-149">-Scheidings teken</span><span class="sxs-lookup"><span data-stu-id="1ac80-149">-Delimiter</span></span>

<span data-ttu-id="1ac80-150">Hiermee geeft u het scheidings teken op waarmee de eigenschaps waarden in de CSV-teken reeksen worden gescheiden.</span><span class="sxs-lookup"><span data-stu-id="1ac80-150">Specifies the delimiter that separates the property values in the CSV strings.</span></span>
<span data-ttu-id="1ac80-151">De standaard waarde is een komma (,).</span><span class="sxs-lookup"><span data-stu-id="1ac80-151">The default is a comma (,).</span></span>

<span data-ttu-id="1ac80-152">Voer een teken in, bijvoorbeeld een dubbele punt (:).</span><span class="sxs-lookup"><span data-stu-id="1ac80-152">Enter a character, such as a colon (:).</span></span>
<span data-ttu-id="1ac80-153">Een punt komma (;)) opgeven plaats de invoeg toepassing tussen enkele aanhalings tekens.</span><span class="sxs-lookup"><span data-stu-id="1ac80-153">To specify a semicolon (;) enclose it in single quotation marks.</span></span>

<span data-ttu-id="1ac80-154">Als u in het bestand een ander teken dan het teken voor de werkelijke waarde opgeeft, `ConvertFrom-Csv` kan de objecten niet maken op basis van de CSV-teken reeksen en worden de CSV-teken reeksen geretourneerd.</span><span class="sxs-lookup"><span data-stu-id="1ac80-154">If you specify a character other than the actual string delimiter in the file, `ConvertFrom-Csv` cannot create the objects from the CSV strings and will return the CSV strings.</span></span>

```yaml
Type: System.Char
Parameter Sets: Delimiter
Aliases:

Required: False
Position: 1
Default value: comma (,)
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="1ac80-155">-Header</span><span class="sxs-lookup"><span data-stu-id="1ac80-155">-Header</span></span>

<span data-ttu-id="1ac80-156">Hiermee wordt een rij met een alternatieve kolom koppen opgegeven voor de geïmporteerde teken reeks.</span><span class="sxs-lookup"><span data-stu-id="1ac80-156">Specifies an alternate column header row for the imported string.</span></span> <span data-ttu-id="1ac80-157">De kolomkop bepaalt de eigenschapnamen van de objecten die zijn gemaakt door `ConvertFrom-Csv` .</span><span class="sxs-lookup"><span data-stu-id="1ac80-157">The column header determines the property names of the objects created by `ConvertFrom-Csv`.</span></span>

<span data-ttu-id="1ac80-158">Voer kolom koppen in als een door komma's gescheiden lijst.</span><span class="sxs-lookup"><span data-stu-id="1ac80-158">Enter column headers as a comma-separated list.</span></span> <span data-ttu-id="1ac80-159">Plaats de teken reeks van de header niet tussen aanhalings tekens.</span><span class="sxs-lookup"><span data-stu-id="1ac80-159">Do not enclose the header string in quotation marks.</span></span> <span data-ttu-id="1ac80-160">Plaats elke kolomkop tussen enkele aanhalings tekens.</span><span class="sxs-lookup"><span data-stu-id="1ac80-160">Enclose each column header in single quotation marks.</span></span>

<span data-ttu-id="1ac80-161">Als u minder kolom koppen opgeeft dan er gegevens kolommen zijn, worden de resterende gegevens kolommen verwijderd.</span><span class="sxs-lookup"><span data-stu-id="1ac80-161">If you enter fewer column headers than there are data columns, the remaining data columns are discarded.</span></span> <span data-ttu-id="1ac80-162">Als u meer kolom koppen opgeeft dan er gegevens kolommen zijn, worden de aanvullende kolom koppen gemaakt met lege gegevens kolommen.</span><span class="sxs-lookup"><span data-stu-id="1ac80-162">If you enter more column headers than there are data columns, the additional column headers are created with empty data columns.</span></span>

<span data-ttu-id="1ac80-163">Wanneer u de para meter **header** gebruikt, laat u de teken reeks voor de kolomkop weg uit de CSV-teken reeksen.</span><span class="sxs-lookup"><span data-stu-id="1ac80-163">When using the **Header** parameter, omit the column header string from the CSV strings.</span></span> <span data-ttu-id="1ac80-164">Anders wordt met deze cmdlet een extra object gemaakt op basis van de items in de rij met koppen.</span><span class="sxs-lookup"><span data-stu-id="1ac80-164">Otherwise, this cmdlet creates an extra object from the items in the header row.</span></span>

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

### <span data-ttu-id="1ac80-165">-Input object</span><span class="sxs-lookup"><span data-stu-id="1ac80-165">-InputObject</span></span>

<span data-ttu-id="1ac80-166">Hiermee geeft u de CSV-teken reeksen op die moeten worden geconverteerd naar objecten.</span><span class="sxs-lookup"><span data-stu-id="1ac80-166">Specifies the CSV strings to be converted to objects.</span></span> <span data-ttu-id="1ac80-167">Voer een variabele in die de CSV-teken reeksen bevat of typ een opdracht of expressie waarmee de CSV-teken reeksen worden opgehaald.</span><span class="sxs-lookup"><span data-stu-id="1ac80-167">Enter a variable that contains the CSV strings or type a command or expression that gets the CSV strings.</span></span> <span data-ttu-id="1ac80-168">U kunt ook de CSV-teken reeksen door sluizen naar `ConvertFrom-Csv` .</span><span class="sxs-lookup"><span data-stu-id="1ac80-168">You can also pipe the CSV strings to `ConvertFrom-Csv`.</span></span>

```yaml
Type: System.Management.Automation.PSObject[]
Parameter Sets: (All)
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="1ac80-169">-UseCulture</span><span class="sxs-lookup"><span data-stu-id="1ac80-169">-UseCulture</span></span>

<span data-ttu-id="1ac80-170">Maakt gebruik van het lijst scheidings teken voor de huidige cultuur als item scheidings teken.</span><span class="sxs-lookup"><span data-stu-id="1ac80-170">Uses the list separator for the current culture as the item delimiter.</span></span> <span data-ttu-id="1ac80-171">Als u het lijst scheidings teken voor een cultuur wilt zoeken, gebruikt u de volgende opdracht: `(Get-Culture).TextInfo.ListSeparator` .</span><span class="sxs-lookup"><span data-stu-id="1ac80-171">To find the list separator for a culture, use the following command: `(Get-Culture).TextInfo.ListSeparator`.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: UseCulture
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="1ac80-172">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="1ac80-172">CommonParameters</span></span>

<span data-ttu-id="1ac80-173">Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="1ac80-173">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="1ac80-174">Zie [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="1ac80-174">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="1ac80-175">INVOER</span><span class="sxs-lookup"><span data-stu-id="1ac80-175">INPUTS</span></span>

### <span data-ttu-id="1ac80-176">System. String</span><span class="sxs-lookup"><span data-stu-id="1ac80-176">System.String</span></span>

<span data-ttu-id="1ac80-177">U kunt CSV-teken reeksen door sluizen naar deze cmdlet.</span><span class="sxs-lookup"><span data-stu-id="1ac80-177">You can pipe CSV strings to this cmdlet.</span></span>

## <span data-ttu-id="1ac80-178">UITVOER</span><span class="sxs-lookup"><span data-stu-id="1ac80-178">OUTPUTS</span></span>

### <span data-ttu-id="1ac80-179">System. Management. Automation. PSObject</span><span class="sxs-lookup"><span data-stu-id="1ac80-179">System.Management.Automation.PSObject</span></span>

<span data-ttu-id="1ac80-180">Deze cmdlet retourneert de objecten die worden beschreven door de eigenschappen in de CSV-teken reeksen.</span><span class="sxs-lookup"><span data-stu-id="1ac80-180">This cmdlet returns the objects described by the properties in the CSV strings.</span></span>

## <span data-ttu-id="1ac80-181">OPMERKINGEN</span><span class="sxs-lookup"><span data-stu-id="1ac80-181">NOTES</span></span>

<span data-ttu-id="1ac80-182">Omdat de geïmporteerde objecten CSV-versies zijn van het object type, worden ze niet herkend en opgemaakt door de Power shell-type-indelings vermeldingen die de niet-CSV-versies van het object type Format teren.</span><span class="sxs-lookup"><span data-stu-id="1ac80-182">Because the imported objects are CSV versions of the object type, they are not recognized and formatted by the PowerShell type formatting entries that format the non-CSV versions of the object type.</span></span>

<span data-ttu-id="1ac80-183">In CSV-indeling wordt elk object vertegenwoordigd door een door komma's gescheiden lijst van de eigenschaps waarden van het object.</span><span class="sxs-lookup"><span data-stu-id="1ac80-183">In CSV format, each object is represented by a comma-separated list of the property values of the object.</span></span> <span data-ttu-id="1ac80-184">De eigenschaps waarden worden geconverteerd naar teken reeksen (door de methode **toString ()** van het object te gebruiken), zodat ze worden vertegenwoordigd door de naam van de eigenschaps waarde.</span><span class="sxs-lookup"><span data-stu-id="1ac80-184">The property values are converted to strings (by using the **ToString()** method of the object), so they are represented by the name of the property value.</span></span> <span data-ttu-id="1ac80-185">Met deze cmdlet worden niet de methoden van het object geëxporteerd.</span><span class="sxs-lookup"><span data-stu-id="1ac80-185">This cmdlet does not export the methods of the object.</span></span>

## <span data-ttu-id="1ac80-186">GERELATEERDE KOPPELINGEN</span><span class="sxs-lookup"><span data-stu-id="1ac80-186">RELATED LINKS</span></span>

[<span data-ttu-id="1ac80-187">ConvertTo-Csv</span><span class="sxs-lookup"><span data-stu-id="1ac80-187">ConvertTo-Csv</span></span>](ConvertTo-Csv.md)

[<span data-ttu-id="1ac80-188">Exporteren-CSV</span><span class="sxs-lookup"><span data-stu-id="1ac80-188">Export-Csv</span></span>](Export-Csv.md)

[<span data-ttu-id="1ac80-189">Import-Csv</span><span class="sxs-lookup"><span data-stu-id="1ac80-189">Import-Csv</span></span>](Import-Csv.md)