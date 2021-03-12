---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 12/12/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/join-string?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Join-String
ms.openlocfilehash: 96f4385c899a50a361fb6df55b40d1ce77225a5b
ms.sourcegitcommit: 71173a89c4f05b5283ccd1e885a780773c13fa47
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 03/12/2021
ms.locfileid: "103196303"
---
# <span data-ttu-id="e7bbb-102">Join-String</span><span class="sxs-lookup"><span data-stu-id="e7bbb-102">Join-String</span></span>

## <span data-ttu-id="e7bbb-103">SAMENVATTING</span><span class="sxs-lookup"><span data-stu-id="e7bbb-103">SYNOPSIS</span></span>
<span data-ttu-id="e7bbb-104">Hiermee worden objecten van de pijp lijn gecombineerd tot één teken reeks.</span><span class="sxs-lookup"><span data-stu-id="e7bbb-104">Combines objects from the pipeline into a single string.</span></span>

## <span data-ttu-id="e7bbb-105">SYNTAXIS</span><span class="sxs-lookup"><span data-stu-id="e7bbb-105">SYNTAX</span></span>

### <span data-ttu-id="e7bbb-106">Standaard (standaard instelling)</span><span class="sxs-lookup"><span data-stu-id="e7bbb-106">Default (Default)</span></span>

```
Join-String [[-Property] <PSPropertyExpression>] [[-Separator] <String>] [-OutputPrefix <String>]
 [-OutputSuffix <String>] [-UseCulture] [-InputObject <PSObject[]>] [<CommonParameters>]
```

### <span data-ttu-id="e7bbb-107">SingleQuote</span><span class="sxs-lookup"><span data-stu-id="e7bbb-107">SingleQuote</span></span>

```
Join-String [[-Property] <PSPropertyExpression>] [[-Separator] <String>] [-OutputPrefix <String>]
 [-OutputSuffix <String>] [-SingleQuote] [-UseCulture] [-InputObject <PSObject[]>]
 [<CommonParameters>]
```

### <span data-ttu-id="e7bbb-108">DoubleQuote</span><span class="sxs-lookup"><span data-stu-id="e7bbb-108">DoubleQuote</span></span>

```
Join-String [[-Property] <PSPropertyExpression>] [[-Separator] <String>] [-OutputPrefix <String>]
 [-OutputSuffix <String>] [-DoubleQuote] [-UseCulture] [-InputObject <PSObject[]>]
 [<CommonParameters>]
```

### <span data-ttu-id="e7bbb-109">Indeling</span><span class="sxs-lookup"><span data-stu-id="e7bbb-109">Format</span></span>

```
Join-String [[-Property] <PSPropertyExpression>] [[-Separator] <String>] [-OutputPrefix <String>]
 [-OutputSuffix <String>] [-FormatString <String>] [-UseCulture] [-InputObject <PSObject[]>]
 [<CommonParameters>]
```

## <span data-ttu-id="e7bbb-110">BESCHRIJVING</span><span class="sxs-lookup"><span data-stu-id="e7bbb-110">DESCRIPTION</span></span>

<span data-ttu-id="e7bbb-111">De `Join-String` cmdlet voegt tekst van pijplijn objecten samen tot één teken reeks.</span><span class="sxs-lookup"><span data-stu-id="e7bbb-111">The `Join-String` cmdlet joins, or combines, text from pipeline objects into a single string.</span></span>

<span data-ttu-id="e7bbb-112">Als er geen para meters zijn opgegeven, worden de pijplijn objecten geconverteerd naar een teken reeks en samengevoegd met het standaard scheidings teken `$OFS` .</span><span class="sxs-lookup"><span data-stu-id="e7bbb-112">If no parameters are specified, the pipeline objects are converted to a string and joined with the default separator `$OFS`.</span></span>

<span data-ttu-id="e7bbb-113">Als u een eigenschaps naam opgeeft, wordt de waarde van de eigenschap geconverteerd naar een teken reeks en samengevoegd in een teken reeks.</span><span class="sxs-lookup"><span data-stu-id="e7bbb-113">By specifying a property name, the property's value is converted to a string and joined into a string.</span></span>

<span data-ttu-id="e7bbb-114">In plaats van een eigenschaps naam kan een script blok worden gebruikt.</span><span class="sxs-lookup"><span data-stu-id="e7bbb-114">Instead of a property name, a script block can be used.</span></span> <span data-ttu-id="e7bbb-115">Het resultaat van het script blok wordt geconverteerd naar een teken reeks voordat deze is gekoppeld aan het formulier resultaat.</span><span class="sxs-lookup"><span data-stu-id="e7bbb-115">The script block's result is converted to a string before it's joined to form the result.</span></span> <span data-ttu-id="e7bbb-116">De tekst van de eigenschap van een object kan worden gecombineerd of het resultaat van het object dat is geconverteerd naar een teken reeks.</span><span class="sxs-lookup"><span data-stu-id="e7bbb-116">It can either combine the text of an object's property or the result of the object that was converted to a string.</span></span>

<span data-ttu-id="e7bbb-117">Deze cmdlet is geïntroduceerd in Power shell 6,2.</span><span class="sxs-lookup"><span data-stu-id="e7bbb-117">This cmdlet was introduced in PowerShell 6.2.</span></span>

## <span data-ttu-id="e7bbb-118">VOORBEELDEN</span><span class="sxs-lookup"><span data-stu-id="e7bbb-118">EXAMPLES</span></span>

### <span data-ttu-id="e7bbb-119">Voor beeld 1: mapnamen toevoegen</span><span class="sxs-lookup"><span data-stu-id="e7bbb-119">Example 1: Join directory names</span></span>

<!-- markdownlint-disable MD038 -->
<span data-ttu-id="e7bbb-120">In dit voor beeld worden mapnamen toegevoegd, wordt de uitvoer tussen dubbele aanhalings tekens geplaatst en worden de mapnamen gescheiden door een komma en een spatie ( `, ` ).</span><span class="sxs-lookup"><span data-stu-id="e7bbb-120">This example joins directory names, wraps the output in double-quotes, and separates the directory names with a comma and space (`, `).</span></span> <span data-ttu-id="e7bbb-121">De uitvoer is een teken reeks object.</span><span class="sxs-lookup"><span data-stu-id="e7bbb-121">The output is a string object.</span></span>

```powershell
Get-ChildItem -Directory C:\ | Join-String -Property Name -DoubleQuote -Separator ', '
```

```Output
"PerfLogs", "Program Files", "Program Files (x86)", "Users", "Windows"
```

<span data-ttu-id="e7bbb-122">`Get-ChildItem` gebruikt de **Directory** -para meter om alle mapnamen voor het station op te halen `C:\` .</span><span class="sxs-lookup"><span data-stu-id="e7bbb-122">`Get-ChildItem` uses the **Directory** parameter to get all the directory names for the `C:\` drive.</span></span>
<span data-ttu-id="e7bbb-123">De objecten worden naar beneden verzonden in de pijp lijn `Join-String` .</span><span class="sxs-lookup"><span data-stu-id="e7bbb-123">The objects are sent down the pipeline to `Join-String`.</span></span> <span data-ttu-id="e7bbb-124">De **eigenschap** para meter geeft de mapnamen aan.</span><span class="sxs-lookup"><span data-stu-id="e7bbb-124">The **Property** parameter specifies the directory names.</span></span> <span data-ttu-id="e7bbb-125">De **doublequote** para meter plaatst de mapnamen met dubbele aanhalings tekens.</span><span class="sxs-lookup"><span data-stu-id="e7bbb-125">The **DoubleQuote** parameter wraps the directory names with double-quote marks.</span></span>
<span data-ttu-id="e7bbb-126">De **scheidings** parameter geeft aan dat er een komma en spatie ( `, ` ) worden gebruikt om de mapnamen van elkaar te scheiden.</span><span class="sxs-lookup"><span data-stu-id="e7bbb-126">The **Separator** parameter specifies to use a comma and space (`, `) to separate the directory names.</span></span>

<span data-ttu-id="e7bbb-127">De `Get-ChildItem` objecten zijn **System. io. DirectoryInfo** en `Join-String` converteren de objecten naar **System. String**.</span><span class="sxs-lookup"><span data-stu-id="e7bbb-127">The `Get-ChildItem` objects are **System.IO.DirectoryInfo** and `Join-String` converts the objects to **System.String**.</span></span>

### <span data-ttu-id="e7bbb-128">Voor beeld 2: een eigenschaps subtekenreeks gebruiken om lid te worden van mapnamen</span><span class="sxs-lookup"><span data-stu-id="e7bbb-128">Example 2: Use a property substring to join directory names</span></span>

<span data-ttu-id="e7bbb-129">In dit voor beeld wordt een subtekenreeks methode gebruikt om de eerste vier letters van mapnamen op te halen, wordt de uitvoer in enkele aanhalings tekens geplaatst en worden de mapnamen gescheiden met een punt komma ( `;` ).</span><span class="sxs-lookup"><span data-stu-id="e7bbb-129">This example uses a substring method to get the first four letters of directory names, wraps the output in single-quotes, and separates the directory names with a semicolon (`;`).</span></span>

```powershell
Get-ChildItem -Directory C:\ | Join-String -Property {$_.Name.SubString(0,4)} -SingleQuote -Separator ';'
```

```Output
'Perf';'Prog';'Prog';'User';'Wind'
```

<span data-ttu-id="e7bbb-130">`Get-ChildItem` gebruikt de **Directory** -para meter om alle mapnamen voor het station op te halen `C:\` .</span><span class="sxs-lookup"><span data-stu-id="e7bbb-130">`Get-ChildItem` uses the **Directory** parameter to get all the directory names for the `C:\` drive.</span></span>
<span data-ttu-id="e7bbb-131">De objecten worden naar beneden verzonden in de pijp lijn `Join-String` .</span><span class="sxs-lookup"><span data-stu-id="e7bbb-131">The objects are sent down the pipeline to `Join-String`.</span></span>

<span data-ttu-id="e7bbb-132">De **eigenschap** para meter script Block gebruikt automatische variabele ( `$_` ) om de eigenschap **name** van elk object te specificeren.</span><span class="sxs-lookup"><span data-stu-id="e7bbb-132">The **Property** parameter script block uses automatic variable (`$_`) to specify each object's **Name** property substring.</span></span> <span data-ttu-id="e7bbb-133">De subtekenreeks haalt de eerste vier letters van elke mapnaam op.</span><span class="sxs-lookup"><span data-stu-id="e7bbb-133">The substring gets the first four letters of each directory name.</span></span> <span data-ttu-id="e7bbb-134">De subtekenreeks geeft de begin-en eind positie van het teken aan.</span><span class="sxs-lookup"><span data-stu-id="e7bbb-134">The substring specifies the character start and end positions.</span></span> <span data-ttu-id="e7bbb-135">Met de para meter **SingleQuote** worden de mapnamen met enkele aanhalings tekens gepakt.</span><span class="sxs-lookup"><span data-stu-id="e7bbb-135">The **SingleQuote** parameter wraps the directory names with single-quote marks.</span></span> <span data-ttu-id="e7bbb-136">De **scheidings** parameter geeft aan dat er een punt komma ( `;` ) moet worden gebruikt om de mapnamen van elkaar te scheiden.</span><span class="sxs-lookup"><span data-stu-id="e7bbb-136">The **Separator** parameter specifies to use a semicolon (`;`) to separate the directory names.</span></span>

<span data-ttu-id="e7bbb-137">Zie [about_Automatic_Variables](../microsoft.powershell.core/about/about_automatic_variables.md) en [subtekenreeks voor](/dotnet/api/system.string.substring)meer informatie over automatische variabelen en subtekenreeksen.</span><span class="sxs-lookup"><span data-stu-id="e7bbb-137">For more information about automatic variables and substrings, see [about_Automatic_Variables](../microsoft.powershell.core/about/about_automatic_variables.md) and [Substring](/dotnet/api/system.string.substring).</span></span>

### <span data-ttu-id="e7bbb-138">Voor beeld 3: samenvoegings uitvoer op een afzonderlijke regel weer geven</span><span class="sxs-lookup"><span data-stu-id="e7bbb-138">Example 3: Display join output on a separate line</span></span>

<span data-ttu-id="e7bbb-139">In dit voor beeld worden service namen gekoppeld aan elke service op een afzonderlijke regel en Inge sprongen door een tabblad.</span><span class="sxs-lookup"><span data-stu-id="e7bbb-139">This example joins service names with each service on a separate line and indented by a tab.</span></span>

```powershell
Get-Service -Name se* | Join-String -Property Name -Separator "`r`n`t" -OutputPrefix "Services:`n`t"
```

```Output
Services:
    seclogon
    SecurityHealthService
    SEMgrSvc
    SENS
    Sense
    SensorDataService
    SensorService
    SensrSvc
    SessionEnv
```

<span data-ttu-id="e7bbb-140">`Get-Service` maakt gebruik van de para meter **name** om services op te geven die beginnen met `se*` .</span><span class="sxs-lookup"><span data-stu-id="e7bbb-140">`Get-Service` uses the **Name** parameter with to specify services that begin with `se*`.</span></span> <span data-ttu-id="e7bbb-141">Het sterretje ( `*` ) is een Joker teken voor elk wille keurig teken.</span><span class="sxs-lookup"><span data-stu-id="e7bbb-141">The asterisk (`*`) is a wildcard for any character.</span></span>

<span data-ttu-id="e7bbb-142">De objecten worden naar beneden verzonden met `Join-String` behulp van de para meter **Property** om de service namen op te geven.</span><span class="sxs-lookup"><span data-stu-id="e7bbb-142">The objects are sent down the pipeline to `Join-String` that uses the **Property** parameter to specify the service names.</span></span> <span data-ttu-id="e7bbb-143">De **scheidings** parameter geeft drie speciale tekens op die een regel terugloop ( `` `r `` ), nieuwe regel ( `` `n `` ) en tab ( `` `t `` ) vertegenwoordigen.</span><span class="sxs-lookup"><span data-stu-id="e7bbb-143">The **Separator** parameter specifies three special characters that represent a carriage return (`` `r ``), newline (`` `n ``), and tab (`` `t ``).</span></span> <span data-ttu-id="e7bbb-144">De **OutputPrefix** voegt een label **Services in:** met een nieuwe regel en een tabblad voor de eerste uitvoer regel.</span><span class="sxs-lookup"><span data-stu-id="e7bbb-144">The **OutputPrefix** inserts a label **Services:** with a new line and tab before the first line of output.</span></span>

<span data-ttu-id="e7bbb-145">Zie [about_Special_Characters](..//microsoft.powershell.core/about/about_special_characters.md)voor meer informatie over speciale tekens.</span><span class="sxs-lookup"><span data-stu-id="e7bbb-145">For more information about special characters, see [about_Special_Characters](..//microsoft.powershell.core/about/about_special_characters.md).</span></span>

### <span data-ttu-id="e7bbb-146">Voor beeld 4: een klassedefinitie maken op basis van een object</span><span class="sxs-lookup"><span data-stu-id="e7bbb-146">Example 4: Create a class definition from an object</span></span>

<span data-ttu-id="e7bbb-147">In dit voor beeld wordt een Power shell-klassen definitie gegenereerd met behulp van een bestaand object als sjabloon.</span><span class="sxs-lookup"><span data-stu-id="e7bbb-147">This example generates a PowerShell class definition using an existing object as a template.</span></span>

<span data-ttu-id="e7bbb-148">Dit code voorbeeld maakt gebruik van splatting om de lengte van de regel te verkleinen en de Lees baarheid te verbeteren.</span><span class="sxs-lookup"><span data-stu-id="e7bbb-148">This code sample uses splatting to reduce the line length and improve readability.</span></span> <span data-ttu-id="e7bbb-149">Zie [about_Splatting](../Microsoft.PowerShell.Core/About/about_Splatting.md)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="e7bbb-149">For more information, see [about_Splatting](../Microsoft.PowerShell.Core/About/about_Splatting.md).</span></span>

```powershell
$obj = [pscustomobject] @{Name = "Joe"; Age = 42}
$parms = @{
  Property = "Name"
  FormatString = '  ${0}'
  OutputPrefix = "class {`n"
  OutputSuffix = "`n}`n"
  Separator = "`n"
}
$obj.PSObject.Properties | Join-String @parms
```

```Output
class {
  $Name
  $Age
}
```

## <span data-ttu-id="e7bbb-150">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="e7bbb-150">PARAMETERS</span></span>

### <span data-ttu-id="e7bbb-151">-DoubleQuote</span><span class="sxs-lookup"><span data-stu-id="e7bbb-151">-DoubleQuote</span></span>

<span data-ttu-id="e7bbb-152">Plaatst de teken reeks waarde van elk pijplijn object in dubbele aanhalings tekens.</span><span class="sxs-lookup"><span data-stu-id="e7bbb-152">Wraps the string value of each pipeline object in double-quotes.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: DoubleQuote
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="e7bbb-153">-Formats Tring</span><span class="sxs-lookup"><span data-stu-id="e7bbb-153">-FormatString</span></span>

<span data-ttu-id="e7bbb-154">Een indelings teken reeks die opgeeft hoe elk item moet worden opgemaakt.</span><span class="sxs-lookup"><span data-stu-id="e7bbb-154">A format string that specifies how each item should be formatted.</span></span>

```yaml
Type: System.String
Parameter Sets: Format
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="e7bbb-155">-Input object</span><span class="sxs-lookup"><span data-stu-id="e7bbb-155">-InputObject</span></span>

<span data-ttu-id="e7bbb-156">Hiermee geeft u de tekst op die moet worden gekoppeld.</span><span class="sxs-lookup"><span data-stu-id="e7bbb-156">Specifies the text to be joined.</span></span> <span data-ttu-id="e7bbb-157">Voer een variabele in die de tekst bevat of typ een opdracht of expressie waarmee de objecten worden opgehaald die moeten worden toegevoegd aan teken reeksen.</span><span class="sxs-lookup"><span data-stu-id="e7bbb-157">Enter a variable that contains the text, or type a command or expression that gets the objects to join into strings.</span></span>

```yaml
Type: System.Management.Automation.PSObject[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="e7bbb-158">-OutputPrefix</span><span class="sxs-lookup"><span data-stu-id="e7bbb-158">-OutputPrefix</span></span>

<span data-ttu-id="e7bbb-159">Tekst die wordt ingevoegd vóór de uitvoer teken reeks.</span><span class="sxs-lookup"><span data-stu-id="e7bbb-159">Text that's inserted before the output string.</span></span> <span data-ttu-id="e7bbb-160">De teken reeks kan speciale tekens bevatten, zoals Carriage Return ( `` `r `` ), nieuwe regel ( `` `n `` ) en tab ( `` `t `` ).</span><span class="sxs-lookup"><span data-stu-id="e7bbb-160">The string can contain special characters such as carriage return (`` `r ``), newline (`` `n ``), and tab (`` `t ``).</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases: op

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="e7bbb-161">-OutputSuffix</span><span class="sxs-lookup"><span data-stu-id="e7bbb-161">-OutputSuffix</span></span>

<span data-ttu-id="e7bbb-162">Tekst die wordt toegevoegd aan de uitvoer teken reeks.</span><span class="sxs-lookup"><span data-stu-id="e7bbb-162">Text that's appended to the output string.</span></span> <span data-ttu-id="e7bbb-163">De teken reeks kan speciale tekens bevatten, zoals Carriage Return ( `` `r `` ), nieuwe regel ( `` `n `` ) en tab ( `` `t `` ).</span><span class="sxs-lookup"><span data-stu-id="e7bbb-163">The string can contain special characters such as carriage return (`` `r ``), newline (`` `n ``), and tab (`` `t ``).</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases: os

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="e7bbb-164">-Eigenschap</span><span class="sxs-lookup"><span data-stu-id="e7bbb-164">-Property</span></span>

<span data-ttu-id="e7bbb-165">De naam van een eigenschap, of een eigenschaps expressie, waarmee het pijplijn object naar tekst wordt geprojecteerd.</span><span class="sxs-lookup"><span data-stu-id="e7bbb-165">The name of a property, or a property expression, that will project the pipeline object to text.</span></span>

```yaml
Type: Microsoft.PowerShell.Commands.PSPropertyExpression
Parameter Sets: (All)
Aliases:

Required: False
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="e7bbb-166">-Scheidings teken</span><span class="sxs-lookup"><span data-stu-id="e7bbb-166">-Separator</span></span>

<span data-ttu-id="e7bbb-167">Tekst of tekens, zoals een komma of punt komma, die tussen de tekst voor elk pijplijn object wordt ingevoegd.</span><span class="sxs-lookup"><span data-stu-id="e7bbb-167">Text or characters such as a comma or semicolon that's inserted between the text for each pipeline object.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: 1
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="e7bbb-168">-SingleQuote</span><span class="sxs-lookup"><span data-stu-id="e7bbb-168">-SingleQuote</span></span>

<span data-ttu-id="e7bbb-169">Plaatst de teken reeks waarde van elk pijplijn object tussen enkele aanhalings tekens.</span><span class="sxs-lookup"><span data-stu-id="e7bbb-169">Wraps the string value of each pipeline object in single quotes.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: SingleQuote
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="e7bbb-170">-UseCulture</span><span class="sxs-lookup"><span data-stu-id="e7bbb-170">-UseCulture</span></span>

<span data-ttu-id="e7bbb-171">Maakt gebruik van het lijst scheidings teken voor de huidige cultuur als item scheidings teken.</span><span class="sxs-lookup"><span data-stu-id="e7bbb-171">Uses the list separator for the current culture as the item delimiter.</span></span> <span data-ttu-id="e7bbb-172">Als u het lijst scheidings teken voor een cultuur wilt zoeken, gebruikt u de volgende opdracht: `(Get-Culture).TextInfo.ListSeparator` .</span><span class="sxs-lookup"><span data-stu-id="e7bbb-172">To find the list separator for a culture, use the following command: `(Get-Culture).TextInfo.ListSeparator`.</span></span>

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

### <span data-ttu-id="e7bbb-173">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="e7bbb-173">CommonParameters</span></span>

<span data-ttu-id="e7bbb-174">Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="e7bbb-174">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="e7bbb-175">Zie [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="e7bbb-175">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="e7bbb-176">INVOER</span><span class="sxs-lookup"><span data-stu-id="e7bbb-176">INPUTS</span></span>

### <span data-ttu-id="e7bbb-177">System. Management. Automation. PSObject</span><span class="sxs-lookup"><span data-stu-id="e7bbb-177">System.Management.Automation.PSObject</span></span>

## <span data-ttu-id="e7bbb-178">UITVOER</span><span class="sxs-lookup"><span data-stu-id="e7bbb-178">OUTPUTS</span></span>

### <span data-ttu-id="e7bbb-179">System. String</span><span class="sxs-lookup"><span data-stu-id="e7bbb-179">System.String</span></span>

## <span data-ttu-id="e7bbb-180">OPMERKINGEN</span><span class="sxs-lookup"><span data-stu-id="e7bbb-180">NOTES</span></span>

## <span data-ttu-id="e7bbb-181">GERELATEERDE KOPPELINGEN</span><span class="sxs-lookup"><span data-stu-id="e7bbb-181">RELATED LINKS</span></span>

[<span data-ttu-id="e7bbb-182">about_Automatic_Variables</span><span class="sxs-lookup"><span data-stu-id="e7bbb-182">about_Automatic_Variables</span></span>](../microsoft.powershell.core/about/about_automatic_variables.md)

[<span data-ttu-id="e7bbb-183">about_Special_Characters</span><span class="sxs-lookup"><span data-stu-id="e7bbb-183">about_Special_Characters</span></span>](..//microsoft.powershell.core/about/about_special_characters.md)

[<span data-ttu-id="e7bbb-184">Subtekenreeks</span><span class="sxs-lookup"><span data-stu-id="e7bbb-184">Substring</span></span>](/dotnet/api/system.string.substring)

