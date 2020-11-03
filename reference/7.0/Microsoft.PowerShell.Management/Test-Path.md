---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 03/22/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/test-path?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Test-Path
ms.openlocfilehash: fcfb974a360c450f474ba97d65190b019860d8c4
ms.sourcegitcommit: de63e9481cf8024883060aae61fb02c59c2de662
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/03/2020
ms.locfileid: "93249604"
---
# <span data-ttu-id="3175d-103">Test-Path</span><span class="sxs-lookup"><span data-stu-id="3175d-103">Test-Path</span></span>

## <span data-ttu-id="3175d-104">SAMENVATTING</span><span class="sxs-lookup"><span data-stu-id="3175d-104">SYNOPSIS</span></span>
<span data-ttu-id="3175d-105">Hiermee wordt bepaald of alle elementen van een pad bestaan.</span><span class="sxs-lookup"><span data-stu-id="3175d-105">Determines whether all elements of a path exist.</span></span>

## <span data-ttu-id="3175d-106">SYNTAXIS</span><span class="sxs-lookup"><span data-stu-id="3175d-106">SYNTAX</span></span>

### <span data-ttu-id="3175d-107">Pad (standaard)</span><span class="sxs-lookup"><span data-stu-id="3175d-107">Path (Default)</span></span>

```
Test-Path [-Path] <String[]> [-Filter <String>] [-Include <String[]>] [-Exclude <String[]>]
 [-PathType <TestPathType>] [-IsValid] [-Credential <PSCredential>]
 [-OlderThan <DateTime>] [-NewerThan <DateTime>] [<CommonParameters>]
```

### <span data-ttu-id="3175d-108">LiteralPath</span><span class="sxs-lookup"><span data-stu-id="3175d-108">LiteralPath</span></span>

```
Test-Path -LiteralPath <String[]> [-Filter <String>] [-Include <String[]>] [-Exclude <String[]>]
 [-PathType <TestPathType>] [-IsValid] [-Credential <PSCredential>]
 [-OlderThan <DateTime>] [-NewerThan <DateTime>] [<CommonParameters>]
```

## <span data-ttu-id="3175d-109">BESCHRIJVING</span><span class="sxs-lookup"><span data-stu-id="3175d-109">DESCRIPTION</span></span>

<span data-ttu-id="3175d-110">De `Test-Path` cmdlet bepaalt of alle elementen van het pad bestaan.</span><span class="sxs-lookup"><span data-stu-id="3175d-110">The `Test-Path` cmdlet determines whether all elements of the path exist.</span></span> <span data-ttu-id="3175d-111">Het wordt geretourneerd `$True` als alle elementen bestaan en `$False` als deze ontbreken.</span><span class="sxs-lookup"><span data-stu-id="3175d-111">It returns `$True` if all elements exist and `$False` if any are missing.</span></span> <span data-ttu-id="3175d-112">U kunt ook zien of de syntaxis van het pad geldig is en of het pad naar een container of een Terminal-of Leaf-element leidt.</span><span class="sxs-lookup"><span data-stu-id="3175d-112">It can also tell whether the path syntax is valid and whether the path leads to a container or a terminal or leaf element.</span></span> <span data-ttu-id="3175d-113">Als de `Path` is spatie een lege teken reeks is, `$False` wordt geretourneerd.</span><span class="sxs-lookup"><span data-stu-id="3175d-113">If the `Path` is whitespace an empty string, then `$False` is returned.</span></span> <span data-ttu-id="3175d-114">Als de `Path` is `$null` , matrix van `$null` of lege matrix, wordt een niet-afsluit fout geretourneerd.</span><span class="sxs-lookup"><span data-stu-id="3175d-114">If the `Path` is `$null`, array of `$null` or empty array, a non-terminating error is returned.</span></span>

## <span data-ttu-id="3175d-115">VOORBEELDEN</span><span class="sxs-lookup"><span data-stu-id="3175d-115">EXAMPLES</span></span>

### <span data-ttu-id="3175d-116">Voor beeld 1: een pad testen</span><span class="sxs-lookup"><span data-stu-id="3175d-116">Example 1: Test a path</span></span>

```powershell
Test-Path -Path "C:\Documents and Settings\DavidC"
```

```Output
True
```

<span data-ttu-id="3175d-117">Met deze opdracht wordt gecontroleerd of alle elementen in het pad bestaan, dat wil zeggen, de map C:, de map documenten en instellingen en de DavidC-map.</span><span class="sxs-lookup"><span data-stu-id="3175d-117">This command checks whether all elements in the path exist, that is, the C: directory, the Documents and Settings directory, and the DavidC directory.</span></span> <span data-ttu-id="3175d-118">Als er ontbreekt, wordt de cmdlet geretourneerd `$False` .</span><span class="sxs-lookup"><span data-stu-id="3175d-118">If any are missing, the cmdlet returns `$False`.</span></span>
<span data-ttu-id="3175d-119">Als dat niet het geval is, wordt geretourneerd `$True` .</span><span class="sxs-lookup"><span data-stu-id="3175d-119">Otherwise, it returns `$True`.</span></span>

### <span data-ttu-id="3175d-120">Voor beeld 2: het pad van een profiel testen</span><span class="sxs-lookup"><span data-stu-id="3175d-120">Example 2: Test the path of a profile</span></span>

```powershell
Test-Path -Path $profile
```

```Output
False
```

```powershell
Test-Path -Path $profile -IsValid
```

```Output
True
```

<span data-ttu-id="3175d-121">Met deze opdrachten wordt het pad van het Power shell-profiel getest.</span><span class="sxs-lookup"><span data-stu-id="3175d-121">These commands test the path of the PowerShell profile.</span></span>

<span data-ttu-id="3175d-122">Met de eerste opdracht wordt bepaald of alle elementen in het pad bestaan.</span><span class="sxs-lookup"><span data-stu-id="3175d-122">The first command determines whether all elements in the path exist.</span></span> <span data-ttu-id="3175d-123">Met de tweede opdracht wordt bepaald of de syntaxis van het pad juist is.</span><span class="sxs-lookup"><span data-stu-id="3175d-123">The second command determines whether the syntax of the path is correct.</span></span> <span data-ttu-id="3175d-124">In dit geval is het pad `$False` , maar de syntaxis is juist `$True` .</span><span class="sxs-lookup"><span data-stu-id="3175d-124">In this case, the path is `$False`, but the syntax is correct `$True`.</span></span> <span data-ttu-id="3175d-125">Met deze opdrachten `$profile` wordt de automatische variabele gebruikt die naar de locatie van het profiel verwijst, zelfs als het profiel niet bestaat.</span><span class="sxs-lookup"><span data-stu-id="3175d-125">These commands use `$profile`, the automatic variable that points to the location for the profile, even if the profile does not exist.</span></span>

<span data-ttu-id="3175d-126">Zie about_Automatic_Variables voor meer informatie over automatische variabelen.</span><span class="sxs-lookup"><span data-stu-id="3175d-126">For more information about automatic variables, see about_Automatic_Variables.</span></span>

### <span data-ttu-id="3175d-127">Voor beeld 3: controleren of er bestanden zijn behalve een opgegeven type</span><span class="sxs-lookup"><span data-stu-id="3175d-127">Example 3: Check whether there are any files besides a specified type</span></span>

```powershell
Test-Path -Path "C:\CAD\Commercial Buildings\*" -Exclude *.dwg
```

```Output
False
```

<span data-ttu-id="3175d-128">Met deze opdracht wordt gecontroleerd of er bestanden aanwezig zijn in de andere map voor commerciële doel einden dan. DWG-bestanden.</span><span class="sxs-lookup"><span data-stu-id="3175d-128">This command checks whether there are any files in the Commercial Buildings directory other than .dwg files.</span></span>

<span data-ttu-id="3175d-129">De opdracht gebruikt de para meter **Path** om het pad op te geven.</span><span class="sxs-lookup"><span data-stu-id="3175d-129">The command uses the **Path** parameter to specify the path.</span></span> <span data-ttu-id="3175d-130">Omdat het pad een spatie bevat, wordt het pad tussen dubbele aanhalings tekens geplaatst.</span><span class="sxs-lookup"><span data-stu-id="3175d-130">Because the path includes a space, the path is enclosed in quotation marks.</span></span> <span data-ttu-id="3175d-131">Het sterretje aan het einde van het pad geeft de inhoud van de map voor commerciële samen stellen aan.</span><span class="sxs-lookup"><span data-stu-id="3175d-131">The asterisk at the end of the path indicates the contents of the Commercial Building directory.</span></span> <span data-ttu-id="3175d-132">Met lange paden, zoals deze, typt u de eerste paar letters van het pad en vervolgens gebruikt u de TAB-toets om het pad te volt ooien.</span><span class="sxs-lookup"><span data-stu-id="3175d-132">With long paths, such as this one, type the first few letters of the path, and then use the TAB key to complete the path.</span></span>

<span data-ttu-id="3175d-133">De opdracht geeft de **exclude** -para meter op om bestanden op te geven die worden wegge laten uit de evaluatie.</span><span class="sxs-lookup"><span data-stu-id="3175d-133">The command specifies the **Exclude** parameter to specify files that will be omitted from the evaluation.</span></span>

<span data-ttu-id="3175d-134">In dit geval, omdat de map alleen DWG-bestanden bevat, is het resultaat `$False` .</span><span class="sxs-lookup"><span data-stu-id="3175d-134">In this case, because the directory contains only .dwg files, the result is `$False`.</span></span>

### <span data-ttu-id="3175d-135">Voor beeld 4: controleren op een bestand</span><span class="sxs-lookup"><span data-stu-id="3175d-135">Example 4: Check for a file</span></span>

```powershell
Test-Path -Path $profile -PathType leaf
```

```Output
True
```

<span data-ttu-id="3175d-136">Met deze opdracht wordt gecontroleerd of het pad dat is opgeslagen in de `$profile` variabele leidt naar een bestand.</span><span class="sxs-lookup"><span data-stu-id="3175d-136">This command checks whether the path stored in the `$profile` variable leads to a file.</span></span> <span data-ttu-id="3175d-137">In dit geval, omdat het Power shell-profiel een `.ps1` bestand is, retourneert de cmdlet `$True` .</span><span class="sxs-lookup"><span data-stu-id="3175d-137">In this case, because the PowerShell profile is a `.ps1` file, the cmdlet returns `$True`.</span></span>

### <span data-ttu-id="3175d-138">Voor beeld 5: paden in het REGI ster controleren</span><span class="sxs-lookup"><span data-stu-id="3175d-138">Example 5: Check paths in the Registry</span></span>

<span data-ttu-id="3175d-139">Deze opdrachten worden gebruikt `Test-Path` met de Power shell-register provider.</span><span class="sxs-lookup"><span data-stu-id="3175d-139">These commands use `Test-Path` with the PowerShell registry provider.</span></span>

<span data-ttu-id="3175d-140">Met de eerste opdracht wordt getest of het registerpad van de register sleutel **micro soft. Power shell** juist is op het systeem.</span><span class="sxs-lookup"><span data-stu-id="3175d-140">The first command tests whether the registry path of the **Microsoft.PowerShell** registry key is correct on the system.</span></span> <span data-ttu-id="3175d-141">Als Power shell correct is geïnstalleerd, retourneert de cmdlet `$True` .</span><span class="sxs-lookup"><span data-stu-id="3175d-141">If PowerShell is installed correctly, the cmdlet returns `$True`.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="3175d-142">`Test-Path` werkt niet correct met alle Power shell-providers.</span><span class="sxs-lookup"><span data-stu-id="3175d-142">`Test-Path` does not work correctly with all PowerShell providers.</span></span> <span data-ttu-id="3175d-143">U kunt bijvoorbeeld gebruiken `Test-Path` om het pad van een register sleutel te testen, maar als u dit gebruikt om het pad van een register vermelding te testen, wordt het altijd geretourneerd `$False` , zelfs als de register vermelding aanwezig is.</span><span class="sxs-lookup"><span data-stu-id="3175d-143">For example, you can use `Test-Path` to test the path of a registry key, but if you use it to test the path of a registry entry, it always returns `$False`, even if the registry entry is present.</span></span>

```powershell
Test-Path -Path "HKLM:\Software\Microsoft\PowerShell\1\ShellIds\Microsoft.PowerShell"
```

```Output
True
```

```powershell
Test-Path -Path "HKLM:\Software\Microsoft\PowerShell\1\ShellIds\Microsoft.PowerShell\ExecutionPolicy"
```

```Output
False
```

### <span data-ttu-id="3175d-144">Voor beeld 6: testen of een bestand nieuwer is dan een opgegeven datum</span><span class="sxs-lookup"><span data-stu-id="3175d-144">Example 6: Test if a file is newer than a specified date</span></span>

<span data-ttu-id="3175d-145">Met deze opdracht wordt de dynamische para meter **NewerThan** gebruikt om te bepalen of het bestand ' PowerShell.exe ' op de computer nieuwer is dan 13 juli 2009.</span><span class="sxs-lookup"><span data-stu-id="3175d-145">This command uses the **NewerThan** dynamic parameter to determine whether the "PowerShell.exe" file on the computer is newer than "July 13, 2009".</span></span>

<span data-ttu-id="3175d-146">De para meter NewerThan werkt alleen op stations met een bestands systeem.</span><span class="sxs-lookup"><span data-stu-id="3175d-146">The NewerThan parameter works only in file system drives.</span></span>

```powershell
Test-Path $pshome\PowerShell.exe -NewerThan "July 13, 2009"
```

```Output
True
```

### <span data-ttu-id="3175d-147">Voor beeld 7: een pad testen met Null als waarde</span><span class="sxs-lookup"><span data-stu-id="3175d-147">Example 7: Test a path with null as the value</span></span>

<span data-ttu-id="3175d-148">De fout die is geretourneerd voor `null` , matrix van `null` of lege matrix is een niet-afsluit fout.</span><span class="sxs-lookup"><span data-stu-id="3175d-148">The error returned for `null`, array of `null` or empty array is a non-terminating error.</span></span> <span data-ttu-id="3175d-149">Deze kan worden onderdrukt met behulp van `-ErrorAction SilentlyContinue` .</span><span class="sxs-lookup"><span data-stu-id="3175d-149">It can be suppress by using `-ErrorAction SilentlyContinue`.</span></span> <span data-ttu-id="3175d-150">In het volgende voor beeld ziet u alle gevallen waarin de fout wordt geretourneerd `NullPathNotPermitted` .</span><span class="sxs-lookup"><span data-stu-id="3175d-150">The following example shows all cases which return the `NullPathNotPermitted` error.</span></span>

```powershell
Test-Path $null
Test-Path $null, $null
Test-Path @()
```

```Output
Test-Path : Cannot bind argument to parameter 'Path' because it is null.
At line:1 char:11
+ Test-Path $null
+           ~~~~~
    + CategoryInfo          : InvalidData: (:) [Test-Path], ParameterBindingValidationException
    + FullyQualifiedErrorId : ParameterArgumentValidationErrorNullNotAllowed,Microsoft.PowerShell.Commands.TestPathCommand
```

### <span data-ttu-id="3175d-151">Voor beeld 8: een pad testen met een spatie als waarde</span><span class="sxs-lookup"><span data-stu-id="3175d-151">Example 8: Test a path with whitespace as the value</span></span>

<span data-ttu-id="3175d-152">Wanneer een spatie of lege teken reeks wordt opgegeven voor de `-Path` para meter, wordt **False** geretourneerd.</span><span class="sxs-lookup"><span data-stu-id="3175d-152">When a whitespace or empty string is provided for the the `-Path` parameter, it returns **False**.</span></span>
<span data-ttu-id="3175d-153">In het volgende voor beeld worden spaties en lege teken reeksen weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="3175d-153">The following example show whitespace and empty string.</span></span>

```powershell
Test-Path ' '
Test-Path ''
```

```Output
False
False
```

## <span data-ttu-id="3175d-154">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="3175d-154">PARAMETERS</span></span>

### <span data-ttu-id="3175d-155">-Credential</span><span class="sxs-lookup"><span data-stu-id="3175d-155">-Credential</span></span>

> [!NOTE]
> <span data-ttu-id="3175d-156">Deze para meter wordt niet ondersteund door providers die zijn geïnstalleerd met Power shell.</span><span class="sxs-lookup"><span data-stu-id="3175d-156">This parameter is not supported by any providers installed with PowerShell.</span></span> <span data-ttu-id="3175d-157">Gebruik [invoke-Command](../Microsoft.PowerShell.Core/Invoke-Command.md)om een andere gebruiker te imiteren of uw referenties te verhogen wanneer u deze cmdlet uitvoert.</span><span class="sxs-lookup"><span data-stu-id="3175d-157">To impersonate another user, or elevate your credentials when running this cmdlet, use [Invoke-Command](../Microsoft.PowerShell.Core/Invoke-Command.md).</span></span>

```yaml
Type: System.Management.Automation.PSCredential
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="3175d-158">-Uitsluiten</span><span class="sxs-lookup"><span data-stu-id="3175d-158">-Exclude</span></span>

<span data-ttu-id="3175d-159">Hiermee geeft u de items die met deze cmdlet worden wegge laten.</span><span class="sxs-lookup"><span data-stu-id="3175d-159">Specifies items that this cmdlet omits.</span></span> <span data-ttu-id="3175d-160">De waarde van deze para meter komt in aanmerking voor de para meter **Path** .</span><span class="sxs-lookup"><span data-stu-id="3175d-160">The value of this parameter qualifies the **Path** parameter.</span></span> <span data-ttu-id="3175d-161">Voer een element of patroon van een pad in, zoals \*. txt.</span><span class="sxs-lookup"><span data-stu-id="3175d-161">Enter a path element or pattern, such as "\*.txt".</span></span> <span data-ttu-id="3175d-162">Joker tekens zijn toegestaan.</span><span class="sxs-lookup"><span data-stu-id="3175d-162">Wildcard characters are permitted.</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: True
```

### <span data-ttu-id="3175d-163">-Filter</span><span class="sxs-lookup"><span data-stu-id="3175d-163">-Filter</span></span>

<span data-ttu-id="3175d-164">Hiermee geeft u een filter op in de indeling of taal van de provider.</span><span class="sxs-lookup"><span data-stu-id="3175d-164">Specifies a filter in the format or language of the provider.</span></span> <span data-ttu-id="3175d-165">De waarde van deze para meter komt in aanmerking voor de para meter **Path** .</span><span class="sxs-lookup"><span data-stu-id="3175d-165">The value of this parameter qualifies the **Path** parameter.</span></span> <span data-ttu-id="3175d-166">De syntaxis van het filter, inclusief het gebruik van joker tekens, is afhankelijk van de provider.</span><span class="sxs-lookup"><span data-stu-id="3175d-166">The syntax of the filter, including the use of wildcard characters, depends on the provider.</span></span> <span data-ttu-id="3175d-167">Filters zijn efficiënter dan andere para meters, omdat deze door de provider worden toegepast wanneer de objecten worden opgehaald in plaats van dat Power shell de objecten heeft gefilterd nadat ze zijn opgehaald.</span><span class="sxs-lookup"><span data-stu-id="3175d-167">Filters are more efficient than other parameters, because the provider applies them when it retrieves the objects instead of having PowerShell filter the objects after they are retrieved.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: True
```

### <span data-ttu-id="3175d-168">-Include</span><span class="sxs-lookup"><span data-stu-id="3175d-168">-Include</span></span>

<span data-ttu-id="3175d-169">Hiermee geeft u de paden op die met deze cmdlet worden getest.</span><span class="sxs-lookup"><span data-stu-id="3175d-169">Specifies paths that this cmdlet tests.</span></span> <span data-ttu-id="3175d-170">De waarde van deze para meter komt in aanmerking voor de para meter **Path** .</span><span class="sxs-lookup"><span data-stu-id="3175d-170">The value of this parameter qualifies the **Path** parameter.</span></span> <span data-ttu-id="3175d-171">Voer een element of patroon van een pad in, zoals \*. txt.</span><span class="sxs-lookup"><span data-stu-id="3175d-171">Enter a path element or pattern, such as "\*.txt".</span></span> <span data-ttu-id="3175d-172">Joker tekens zijn toegestaan.</span><span class="sxs-lookup"><span data-stu-id="3175d-172">Wildcard characters are permitted.</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: True
```

### <span data-ttu-id="3175d-173">-IsValid</span><span class="sxs-lookup"><span data-stu-id="3175d-173">-IsValid</span></span>

<span data-ttu-id="3175d-174">Geeft aan dat met deze cmdlet de syntaxis van het pad wordt getest, ongeacht of de elementen van het pad bestaan.</span><span class="sxs-lookup"><span data-stu-id="3175d-174">Indicates that this cmdlet tests the syntax of the path, regardless of whether the elements of the path exist.</span></span> <span data-ttu-id="3175d-175">Met deze cmdlet wordt geretourneerd `$True` als de syntaxis van het pad geldig is en `$False` als dit niet het geval is.</span><span class="sxs-lookup"><span data-stu-id="3175d-175">This cmdlet returns `$True` if the path syntax is valid and `$False` if it is not.</span></span>

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

### <span data-ttu-id="3175d-176">-LiteralPath</span><span class="sxs-lookup"><span data-stu-id="3175d-176">-LiteralPath</span></span>

<span data-ttu-id="3175d-177">Hiermee geeft u een pad op dat moet worden getest.</span><span class="sxs-lookup"><span data-stu-id="3175d-177">Specifies a path to be tested.</span></span> <span data-ttu-id="3175d-178">In tegens telling tot **Path** wordt de waarde van de para meter **LiteralPath** exact gebruikt wanneer deze wordt getypt.</span><span class="sxs-lookup"><span data-stu-id="3175d-178">Unlike **Path** , the value of the **LiteralPath** parameter is used exactly as it is typed.</span></span> <span data-ttu-id="3175d-179">Er worden geen tekens geïnterpreteerd als joker tekens.</span><span class="sxs-lookup"><span data-stu-id="3175d-179">No characters are interpreted as wildcard characters.</span></span> <span data-ttu-id="3175d-180">Als het pad tekens bevat die kunnen worden geïnterpreteerd door Power shell als escape-teken reeksen, moet u het pad in één aanhalings teken plaatsen zodat ze niet worden geïnterpreteerd.</span><span class="sxs-lookup"><span data-stu-id="3175d-180">If the path includes characters that could be interpreted by PowerShell as escape sequences, you must enclose the path in single quote so that they won't be interpreted.</span></span>

```yaml
Type: System.String[]
Parameter Sets: LiteralPath
Aliases: PSPath, LP

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="3175d-181">-NewerThan</span><span class="sxs-lookup"><span data-stu-id="3175d-181">-NewerThan</span></span>

<span data-ttu-id="3175d-182">Geef een tijd op als een **DateTime** -object.</span><span class="sxs-lookup"><span data-stu-id="3175d-182">Specify a time as a **DateTime** object.</span></span>

```yaml
Type: System.Nullable`1[System.DateTime]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="3175d-183">-OlderThan</span><span class="sxs-lookup"><span data-stu-id="3175d-183">-OlderThan</span></span>

<span data-ttu-id="3175d-184">Geef een tijd op als een **DateTime** -object.</span><span class="sxs-lookup"><span data-stu-id="3175d-184">Specify a time as a **DateTime** object.</span></span>

```yaml
Type: System.Nullable`1[System.DateTime]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="3175d-185">-Path</span><span class="sxs-lookup"><span data-stu-id="3175d-185">-Path</span></span>

<span data-ttu-id="3175d-186">Hiermee geeft u een pad op dat moet worden getest.</span><span class="sxs-lookup"><span data-stu-id="3175d-186">Specifies a path to be tested.</span></span> <span data-ttu-id="3175d-187">Joker tekens zijn toegestaan.</span><span class="sxs-lookup"><span data-stu-id="3175d-187">Wildcard characters are permitted.</span></span> <span data-ttu-id="3175d-188">Als het pad spaties bevat, plaatst u het tussen aanhalings tekens.</span><span class="sxs-lookup"><span data-stu-id="3175d-188">If the path includes spaces, enclose it in quotation marks.</span></span>

```yaml
Type: System.String[]
Parameter Sets: Path
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: True
```

### <span data-ttu-id="3175d-189">-PathType</span><span class="sxs-lookup"><span data-stu-id="3175d-189">-PathType</span></span>

<span data-ttu-id="3175d-190">Hiermee geeft u het type van het laatste element in het pad op.</span><span class="sxs-lookup"><span data-stu-id="3175d-190">Specifies the type of the final element in the path.</span></span> <span data-ttu-id="3175d-191">Met deze cmdlet wordt geretourneerd `$True` als het element van het opgegeven type is en `$False` als dit niet het geval is.</span><span class="sxs-lookup"><span data-stu-id="3175d-191">This cmdlet returns `$True` if the element is of the specified type and `$False` if it is not.</span></span> <span data-ttu-id="3175d-192">De aanvaardbare waarden voor deze parameter zijn:</span><span class="sxs-lookup"><span data-stu-id="3175d-192">The acceptable values for this parameter are:</span></span>

- <span data-ttu-id="3175d-193">Verpakking.</span><span class="sxs-lookup"><span data-stu-id="3175d-193">Container.</span></span>
  <span data-ttu-id="3175d-194">Een element met andere elementen, zoals een map of register sleutel.</span><span class="sxs-lookup"><span data-stu-id="3175d-194">An element that contains other elements, such as a directory or registry key.</span></span>
- <span data-ttu-id="3175d-195">Vertakking.</span><span class="sxs-lookup"><span data-stu-id="3175d-195">Leaf.</span></span>
  <span data-ttu-id="3175d-196">Een element dat geen andere elementen bevat, zoals een bestand.</span><span class="sxs-lookup"><span data-stu-id="3175d-196">An element that does not contain other elements, such as a file.</span></span>
- <span data-ttu-id="3175d-197">Iedere.</span><span class="sxs-lookup"><span data-stu-id="3175d-197">Any.</span></span>
  <span data-ttu-id="3175d-198">Ofwel een container of een Leaf.</span><span class="sxs-lookup"><span data-stu-id="3175d-198">Either a container or a leaf.</span></span>

<span data-ttu-id="3175d-199">Hiermee wordt aangegeven of het laatste element in het pad van een bepaald type is.</span><span class="sxs-lookup"><span data-stu-id="3175d-199">Tells whether the final element in the path is of a particular type.</span></span>

> [!CAUTION]
>
> <span data-ttu-id="3175d-200">Tot en met de Power shell-versie 6.1.2, wanneer de opties **IsValid** en **PathType** samen worden opgegeven, wordt `Test-Path` de schakel optie **PathType** door de cmdlet genegeerd en wordt alleen het pad van de syntactisch gevalideerd zonder het padtype te valideren.</span><span class="sxs-lookup"><span data-stu-id="3175d-200">Up to PowerShell version 6.1.2, when the **IsValid** and **PathType** switches are specified together, the `Test-Path` cmdlet ignores the **PathType** switch and only validates the syntactic path without validating the path type.</span></span>
>
> <span data-ttu-id="3175d-201">Op basis van het [probleem #8607](https://github.com/PowerShell/PowerShell/issues/8607), kan het oplossen van dit gedrag een belang rijke wijziging in een toekomstige versie zijn, waarbij de functies **IsValid** en **PathType** deel uitmaken van afzonderlijke parameter sets, en dus niet gezamenlijk kunnen worden gebruikt om deze Verwar ring te voor komen.</span><span class="sxs-lookup"><span data-stu-id="3175d-201">According to [issue #8607](https://github.com/PowerShell/PowerShell/issues/8607), fixing this behavior may be a breaking change in a future version, where the **IsValid** and **PathType** switches belong to separate parameter sets, and thus, cannot be used together avoiding this confusion.</span></span>

```yaml
Type: Microsoft.PowerShell.Commands.TestPathType
Parameter Sets: (All)
Aliases: Type
Accepted values: Any, Container, Leaf

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="3175d-202">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="3175d-202">CommonParameters</span></span>

<span data-ttu-id="3175d-203">Deze cmdlet biedt ondersteuning voor de algemene para meters: `-Debug` , `-ErrorAction` , `-ErrorVariable` , `-InformationAction` , `-InformationVariable` , `-OutVariable` , `-OutBuffer` , `-PipelineVariable` , `-Verbose` , `-WarningAction` en `-WarningVariable` .</span><span class="sxs-lookup"><span data-stu-id="3175d-203">This cmdlet supports the common parameters: `-Debug`, `-ErrorAction`, `-ErrorVariable`, `-InformationAction`, `-InformationVariable`, `-OutVariable`, `-OutBuffer`, `-PipelineVariable`, `-Verbose`, `-WarningAction`, and `-WarningVariable`.</span></span> <span data-ttu-id="3175d-204">Zie [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="3175d-204">For more information, see [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md).</span></span>

## <span data-ttu-id="3175d-205">INVOER</span><span class="sxs-lookup"><span data-stu-id="3175d-205">INPUTS</span></span>

### <span data-ttu-id="3175d-206">System. String</span><span class="sxs-lookup"><span data-stu-id="3175d-206">System.String</span></span>

<span data-ttu-id="3175d-207">U kunt een teken reeks die een pad bevat, maar geen letterlijk pad, naar deze cmdlet pipet.</span><span class="sxs-lookup"><span data-stu-id="3175d-207">You can pipe a string that contains a path, but not a literal path, to this cmdlet.</span></span>

## <span data-ttu-id="3175d-208">UITVOER</span><span class="sxs-lookup"><span data-stu-id="3175d-208">OUTPUTS</span></span>

### <span data-ttu-id="3175d-209">System. Boolean</span><span class="sxs-lookup"><span data-stu-id="3175d-209">System.Boolean</span></span>

<span data-ttu-id="3175d-210">De cmdlet retourneert een **Booleaanse** waarde.</span><span class="sxs-lookup"><span data-stu-id="3175d-210">The cmdlet returns a **Boolean** value.</span></span>

## <span data-ttu-id="3175d-211">OPMERKINGEN</span><span class="sxs-lookup"><span data-stu-id="3175d-211">NOTES</span></span>

<span data-ttu-id="3175d-212">De cmdlets die het **pad naar** de tijdelijke naam (de **pad** -cmdlets) bevatten, werken met padnamen en retour neren de namen in een beknopt formaat dat alle Power shell-providers kunnen interpreteren.</span><span class="sxs-lookup"><span data-stu-id="3175d-212">The cmdlets that contain the **Path** noun (the **Path** cmdlets) work with path names and return the names in a concise format that all PowerShell providers can interpret.</span></span> <span data-ttu-id="3175d-213">Ze zijn ontworpen voor gebruik in Program ma's en scripts waarvoor u de volledige of gedeeltelijke naam van een pad wilt weer geven in een bepaalde indeling.</span><span class="sxs-lookup"><span data-stu-id="3175d-213">They are designed for use in programs and scripts where you want to display all or part of a path name in a particular format.</span></span>
<span data-ttu-id="3175d-214">Gebruik deze zoals u **mapnaam** , **Normpath** , **realpath** , **join's** of andere pad-werkers zou gebruiken.</span><span class="sxs-lookup"><span data-stu-id="3175d-214">Use them as you would use **Dirname** , **Normpath** , **Realpath** , **Join** , or other path manipulators.</span></span>

<span data-ttu-id="3175d-215">De `Test-Path` is ontworpen om te werken met de gegevens die door elke provider worden weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="3175d-215">The `Test-Path` is designed to work with the data exposed by any provider.</span></span> <span data-ttu-id="3175d-216">Als u een lijst wilt weer geven van de providers die beschikbaar zijn in uw sessie, typt u `Get-PSProvider` .</span><span class="sxs-lookup"><span data-stu-id="3175d-216">To list the providers available in your session, type `Get-PSProvider`.</span></span> <span data-ttu-id="3175d-217">Zie [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="3175d-217">For more information, see [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md).</span></span>

## <span data-ttu-id="3175d-218">GERELATEERDE KOPPELINGEN</span><span class="sxs-lookup"><span data-stu-id="3175d-218">RELATED LINKS</span></span>

[<span data-ttu-id="3175d-219">Convert-pad</span><span class="sxs-lookup"><span data-stu-id="3175d-219">Convert-Path</span></span>](Convert-Path.md)

[<span data-ttu-id="3175d-220">Pad voor samen voegen</span><span class="sxs-lookup"><span data-stu-id="3175d-220">Join-Path</span></span>](Join-Path.md)

[<span data-ttu-id="3175d-221">Oplossen-pad</span><span class="sxs-lookup"><span data-stu-id="3175d-221">Resolve-Path</span></span>](Resolve-Path.md)

[<span data-ttu-id="3175d-222">Split-pad</span><span class="sxs-lookup"><span data-stu-id="3175d-222">Split-Path</span></span>](Split-Path.md)
