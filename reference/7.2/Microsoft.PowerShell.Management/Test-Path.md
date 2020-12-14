---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 03/22/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/test-path?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Test-Path
ms.openlocfilehash: a79f12739643a873703b39d9d07e8b7db01dfbb4
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 11/17/2020
ms.locfileid: "94705947"
---
# <span data-ttu-id="7a91f-102">Test-Path</span><span class="sxs-lookup"><span data-stu-id="7a91f-102">Test-Path</span></span>

## <span data-ttu-id="7a91f-103">SAMENVATTING</span><span class="sxs-lookup"><span data-stu-id="7a91f-103">SYNOPSIS</span></span>
<span data-ttu-id="7a91f-104">Hiermee wordt bepaald of alle elementen van een pad bestaan.</span><span class="sxs-lookup"><span data-stu-id="7a91f-104">Determines whether all elements of a path exist.</span></span>

## <span data-ttu-id="7a91f-105">SYNTAXIS</span><span class="sxs-lookup"><span data-stu-id="7a91f-105">SYNTAX</span></span>

### <span data-ttu-id="7a91f-106">Pad (standaard)</span><span class="sxs-lookup"><span data-stu-id="7a91f-106">Path (Default)</span></span>

```
Test-Path [-Path] <String[]> [-Filter <String>] [-Include <String[]>] [-Exclude <String[]>]
 [-PathType <TestPathType>] [-IsValid] [-Credential <PSCredential>]
 [-OlderThan <DateTime>] [-NewerThan <DateTime>] [<CommonParameters>]
```

### <span data-ttu-id="7a91f-107">LiteralPath</span><span class="sxs-lookup"><span data-stu-id="7a91f-107">LiteralPath</span></span>

```
Test-Path -LiteralPath <String[]> [-Filter <String>] [-Include <String[]>] [-Exclude <String[]>]
 [-PathType <TestPathType>] [-IsValid] [-Credential <PSCredential>]
 [-OlderThan <DateTime>] [-NewerThan <DateTime>] [<CommonParameters>]
```

## <span data-ttu-id="7a91f-108">BESCHRIJVING</span><span class="sxs-lookup"><span data-stu-id="7a91f-108">DESCRIPTION</span></span>

<span data-ttu-id="7a91f-109">De `Test-Path` cmdlet bepaalt of alle elementen van het pad bestaan.</span><span class="sxs-lookup"><span data-stu-id="7a91f-109">The `Test-Path` cmdlet determines whether all elements of the path exist.</span></span> <span data-ttu-id="7a91f-110">Het wordt geretourneerd `$True` als alle elementen bestaan en `$False` als deze ontbreken.</span><span class="sxs-lookup"><span data-stu-id="7a91f-110">It returns `$True` if all elements exist and `$False` if any are missing.</span></span> <span data-ttu-id="7a91f-111">U kunt ook zien of de syntaxis van het pad geldig is en of het pad naar een container of een Terminal-of Leaf-element leidt.</span><span class="sxs-lookup"><span data-stu-id="7a91f-111">It can also tell whether the path syntax is valid and whether the path leads to a container or a terminal or leaf element.</span></span> <span data-ttu-id="7a91f-112">Als de `Path` is spatie een lege teken reeks is, `$False` wordt geretourneerd.</span><span class="sxs-lookup"><span data-stu-id="7a91f-112">If the `Path` is whitespace an empty string, then `$False` is returned.</span></span> <span data-ttu-id="7a91f-113">Als de `Path` is `$null` , matrix van `$null` of lege matrix, wordt een niet-afsluit fout geretourneerd.</span><span class="sxs-lookup"><span data-stu-id="7a91f-113">If the `Path` is `$null`, array of `$null` or empty array, a non-terminating error is returned.</span></span>

## <span data-ttu-id="7a91f-114">VOORBEELDEN</span><span class="sxs-lookup"><span data-stu-id="7a91f-114">EXAMPLES</span></span>

### <span data-ttu-id="7a91f-115">Voor beeld 1: een pad testen</span><span class="sxs-lookup"><span data-stu-id="7a91f-115">Example 1: Test a path</span></span>

```powershell
Test-Path -Path "C:\Documents and Settings\DavidC"
```

```Output
True
```

<span data-ttu-id="7a91f-116">Met deze opdracht wordt gecontroleerd of alle elementen in het pad bestaan, dat wil zeggen, de map C:, de map documenten en instellingen en de DavidC-map.</span><span class="sxs-lookup"><span data-stu-id="7a91f-116">This command checks whether all elements in the path exist, that is, the C: directory, the Documents and Settings directory, and the DavidC directory.</span></span> <span data-ttu-id="7a91f-117">Als er ontbreekt, wordt de cmdlet geretourneerd `$False` .</span><span class="sxs-lookup"><span data-stu-id="7a91f-117">If any are missing, the cmdlet returns `$False`.</span></span>
<span data-ttu-id="7a91f-118">Als dat niet het geval is, wordt geretourneerd `$True` .</span><span class="sxs-lookup"><span data-stu-id="7a91f-118">Otherwise, it returns `$True`.</span></span>

### <span data-ttu-id="7a91f-119">Voor beeld 2: het pad van een profiel testen</span><span class="sxs-lookup"><span data-stu-id="7a91f-119">Example 2: Test the path of a profile</span></span>

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

<span data-ttu-id="7a91f-120">Met deze opdrachten wordt het pad van het Power shell-profiel getest.</span><span class="sxs-lookup"><span data-stu-id="7a91f-120">These commands test the path of the PowerShell profile.</span></span>

<span data-ttu-id="7a91f-121">Met de eerste opdracht wordt bepaald of alle elementen in het pad bestaan.</span><span class="sxs-lookup"><span data-stu-id="7a91f-121">The first command determines whether all elements in the path exist.</span></span> <span data-ttu-id="7a91f-122">Met de tweede opdracht wordt bepaald of de syntaxis van het pad juist is.</span><span class="sxs-lookup"><span data-stu-id="7a91f-122">The second command determines whether the syntax of the path is correct.</span></span> <span data-ttu-id="7a91f-123">In dit geval is het pad `$False` , maar de syntaxis is juist `$True` .</span><span class="sxs-lookup"><span data-stu-id="7a91f-123">In this case, the path is `$False`, but the syntax is correct `$True`.</span></span> <span data-ttu-id="7a91f-124">Met deze opdrachten `$profile` wordt de automatische variabele gebruikt die naar de locatie van het profiel verwijst, zelfs als het profiel niet bestaat.</span><span class="sxs-lookup"><span data-stu-id="7a91f-124">These commands use `$profile`, the automatic variable that points to the location for the profile, even if the profile does not exist.</span></span>

<span data-ttu-id="7a91f-125">Zie about_Automatic_Variables voor meer informatie over automatische variabelen.</span><span class="sxs-lookup"><span data-stu-id="7a91f-125">For more information about automatic variables, see about_Automatic_Variables.</span></span>

### <span data-ttu-id="7a91f-126">Voor beeld 3: controleren of er bestanden zijn behalve een opgegeven type</span><span class="sxs-lookup"><span data-stu-id="7a91f-126">Example 3: Check whether there are any files besides a specified type</span></span>

```powershell
Test-Path -Path "C:\CAD\Commercial Buildings\*" -Exclude *.dwg
```

```Output
False
```

<span data-ttu-id="7a91f-127">Met deze opdracht wordt gecontroleerd of er bestanden aanwezig zijn in de andere map voor commerciële doel einden dan. DWG-bestanden.</span><span class="sxs-lookup"><span data-stu-id="7a91f-127">This command checks whether there are any files in the Commercial Buildings directory other than .dwg files.</span></span>

<span data-ttu-id="7a91f-128">De opdracht gebruikt de para meter **Path** om het pad op te geven.</span><span class="sxs-lookup"><span data-stu-id="7a91f-128">The command uses the **Path** parameter to specify the path.</span></span> <span data-ttu-id="7a91f-129">Omdat het pad een spatie bevat, wordt het pad tussen dubbele aanhalings tekens geplaatst.</span><span class="sxs-lookup"><span data-stu-id="7a91f-129">Because the path includes a space, the path is enclosed in quotation marks.</span></span> <span data-ttu-id="7a91f-130">Het sterretje aan het einde van het pad geeft de inhoud van de map voor commerciële samen stellen aan.</span><span class="sxs-lookup"><span data-stu-id="7a91f-130">The asterisk at the end of the path indicates the contents of the Commercial Building directory.</span></span> <span data-ttu-id="7a91f-131">Met lange paden, zoals deze, typt u de eerste paar letters van het pad en vervolgens gebruikt u de TAB-toets om het pad te volt ooien.</span><span class="sxs-lookup"><span data-stu-id="7a91f-131">With long paths, such as this one, type the first few letters of the path, and then use the TAB key to complete the path.</span></span>

<span data-ttu-id="7a91f-132">De opdracht geeft de **exclude** -para meter op om bestanden op te geven die worden wegge laten uit de evaluatie.</span><span class="sxs-lookup"><span data-stu-id="7a91f-132">The command specifies the **Exclude** parameter to specify files that will be omitted from the evaluation.</span></span>

<span data-ttu-id="7a91f-133">In dit geval, omdat de map alleen DWG-bestanden bevat, is het resultaat `$False` .</span><span class="sxs-lookup"><span data-stu-id="7a91f-133">In this case, because the directory contains only .dwg files, the result is `$False`.</span></span>

### <span data-ttu-id="7a91f-134">Voor beeld 4: controleren op een bestand</span><span class="sxs-lookup"><span data-stu-id="7a91f-134">Example 4: Check for a file</span></span>

```powershell
Test-Path -Path $profile -PathType leaf
```

```Output
True
```

<span data-ttu-id="7a91f-135">Met deze opdracht wordt gecontroleerd of het pad dat is opgeslagen in de `$profile` variabele leidt naar een bestand.</span><span class="sxs-lookup"><span data-stu-id="7a91f-135">This command checks whether the path stored in the `$profile` variable leads to a file.</span></span> <span data-ttu-id="7a91f-136">In dit geval, omdat het Power shell-profiel een `.ps1` bestand is, retourneert de cmdlet `$True` .</span><span class="sxs-lookup"><span data-stu-id="7a91f-136">In this case, because the PowerShell profile is a `.ps1` file, the cmdlet returns `$True`.</span></span>

### <span data-ttu-id="7a91f-137">Voor beeld 5: paden in het REGI ster controleren</span><span class="sxs-lookup"><span data-stu-id="7a91f-137">Example 5: Check paths in the Registry</span></span>

<span data-ttu-id="7a91f-138">Deze opdrachten worden gebruikt `Test-Path` met de Power shell-register provider.</span><span class="sxs-lookup"><span data-stu-id="7a91f-138">These commands use `Test-Path` with the PowerShell registry provider.</span></span>

<span data-ttu-id="7a91f-139">Met de eerste opdracht wordt getest of het registerpad van de register sleutel **micro soft. Power shell** juist is op het systeem.</span><span class="sxs-lookup"><span data-stu-id="7a91f-139">The first command tests whether the registry path of the **Microsoft.PowerShell** registry key is correct on the system.</span></span> <span data-ttu-id="7a91f-140">Als Power shell correct is geïnstalleerd, retourneert de cmdlet `$True` .</span><span class="sxs-lookup"><span data-stu-id="7a91f-140">If PowerShell is installed correctly, the cmdlet returns `$True`.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="7a91f-141">`Test-Path` werkt niet correct met alle Power shell-providers.</span><span class="sxs-lookup"><span data-stu-id="7a91f-141">`Test-Path` does not work correctly with all PowerShell providers.</span></span> <span data-ttu-id="7a91f-142">U kunt bijvoorbeeld gebruiken `Test-Path` om het pad van een register sleutel te testen, maar als u dit gebruikt om het pad van een register vermelding te testen, wordt het altijd geretourneerd `$False` , zelfs als de register vermelding aanwezig is.</span><span class="sxs-lookup"><span data-stu-id="7a91f-142">For example, you can use `Test-Path` to test the path of a registry key, but if you use it to test the path of a registry entry, it always returns `$False`, even if the registry entry is present.</span></span>

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

### <span data-ttu-id="7a91f-143">Voor beeld 6: testen of een bestand nieuwer is dan een opgegeven datum</span><span class="sxs-lookup"><span data-stu-id="7a91f-143">Example 6: Test if a file is newer than a specified date</span></span>

<span data-ttu-id="7a91f-144">Met deze opdracht wordt de dynamische para meter **NewerThan** gebruikt om te bepalen of het bestand ' PowerShell.exe ' op de computer nieuwer is dan 13 juli 2009.</span><span class="sxs-lookup"><span data-stu-id="7a91f-144">This command uses the **NewerThan** dynamic parameter to determine whether the "PowerShell.exe" file on the computer is newer than "July 13, 2009".</span></span>

<span data-ttu-id="7a91f-145">De para meter NewerThan werkt alleen op stations met een bestands systeem.</span><span class="sxs-lookup"><span data-stu-id="7a91f-145">The NewerThan parameter works only in file system drives.</span></span>

```powershell
Test-Path $pshome\PowerShell.exe -NewerThan "July 13, 2009"
```

```Output
True
```

### <span data-ttu-id="7a91f-146">Voor beeld 7: een pad testen met Null als waarde</span><span class="sxs-lookup"><span data-stu-id="7a91f-146">Example 7: Test a path with null as the value</span></span>

<span data-ttu-id="7a91f-147">De fout die is geretourneerd voor `null` , matrix van `null` of lege matrix is een niet-afsluit fout.</span><span class="sxs-lookup"><span data-stu-id="7a91f-147">The error returned for `null`, array of `null` or empty array is a non-terminating error.</span></span> <span data-ttu-id="7a91f-148">Deze kan worden onderdrukt met behulp van `-ErrorAction SilentlyContinue` .</span><span class="sxs-lookup"><span data-stu-id="7a91f-148">It can be suppress by using `-ErrorAction SilentlyContinue`.</span></span> <span data-ttu-id="7a91f-149">In het volgende voor beeld ziet u alle gevallen waarin de fout wordt geretourneerd `NullPathNotPermitted` .</span><span class="sxs-lookup"><span data-stu-id="7a91f-149">The following example shows all cases which return the `NullPathNotPermitted` error.</span></span>

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

### <span data-ttu-id="7a91f-150">Voor beeld 8: een pad testen met een spatie als waarde</span><span class="sxs-lookup"><span data-stu-id="7a91f-150">Example 8: Test a path with whitespace as the value</span></span>

<span data-ttu-id="7a91f-151">Wanneer een spatie of lege teken reeks wordt opgegeven voor de `-Path` para meter, wordt **False** geretourneerd.</span><span class="sxs-lookup"><span data-stu-id="7a91f-151">When a whitespace or empty string is provided for the the `-Path` parameter, it returns **False**.</span></span>
<span data-ttu-id="7a91f-152">In het volgende voor beeld worden spaties en lege teken reeksen weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="7a91f-152">The following example show whitespace and empty string.</span></span>

```powershell
Test-Path ' '
Test-Path ''
```

```Output
False
False
```

## <span data-ttu-id="7a91f-153">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="7a91f-153">PARAMETERS</span></span>

### <span data-ttu-id="7a91f-154">-Credential</span><span class="sxs-lookup"><span data-stu-id="7a91f-154">-Credential</span></span>

> [!NOTE]
> <span data-ttu-id="7a91f-155">Deze para meter wordt niet ondersteund door providers die zijn geïnstalleerd met Power shell.</span><span class="sxs-lookup"><span data-stu-id="7a91f-155">This parameter is not supported by any providers installed with PowerShell.</span></span> <span data-ttu-id="7a91f-156">Gebruik [invoke-Command](../Microsoft.PowerShell.Core/Invoke-Command.md)om een andere gebruiker te imiteren of uw referenties te verhogen wanneer u deze cmdlet uitvoert.</span><span class="sxs-lookup"><span data-stu-id="7a91f-156">To impersonate another user, or elevate your credentials when running this cmdlet, use [Invoke-Command](../Microsoft.PowerShell.Core/Invoke-Command.md).</span></span>

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

### <span data-ttu-id="7a91f-157">-Uitsluiten</span><span class="sxs-lookup"><span data-stu-id="7a91f-157">-Exclude</span></span>

<span data-ttu-id="7a91f-158">Hiermee geeft u de items die met deze cmdlet worden wegge laten.</span><span class="sxs-lookup"><span data-stu-id="7a91f-158">Specifies items that this cmdlet omits.</span></span> <span data-ttu-id="7a91f-159">De waarde van deze para meter komt in aanmerking voor de para meter **Path** .</span><span class="sxs-lookup"><span data-stu-id="7a91f-159">The value of this parameter qualifies the **Path** parameter.</span></span> <span data-ttu-id="7a91f-160">Voer een element of patroon van een pad in, zoals \*. txt.</span><span class="sxs-lookup"><span data-stu-id="7a91f-160">Enter a path element or pattern, such as "\*.txt".</span></span> <span data-ttu-id="7a91f-161">Joker tekens zijn toegestaan.</span><span class="sxs-lookup"><span data-stu-id="7a91f-161">Wildcard characters are permitted.</span></span>

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

### <span data-ttu-id="7a91f-162">-Filter</span><span class="sxs-lookup"><span data-stu-id="7a91f-162">-Filter</span></span>

<span data-ttu-id="7a91f-163">Hiermee geeft u een filter op in de indeling of taal van de provider.</span><span class="sxs-lookup"><span data-stu-id="7a91f-163">Specifies a filter in the format or language of the provider.</span></span> <span data-ttu-id="7a91f-164">De waarde van deze para meter komt in aanmerking voor de para meter **Path** .</span><span class="sxs-lookup"><span data-stu-id="7a91f-164">The value of this parameter qualifies the **Path** parameter.</span></span> <span data-ttu-id="7a91f-165">De syntaxis van het filter, inclusief het gebruik van joker tekens, is afhankelijk van de provider.</span><span class="sxs-lookup"><span data-stu-id="7a91f-165">The syntax of the filter, including the use of wildcard characters, depends on the provider.</span></span> <span data-ttu-id="7a91f-166">Filters zijn efficiënter dan andere para meters, omdat deze door de provider worden toegepast wanneer de objecten worden opgehaald in plaats van dat Power shell de objecten heeft gefilterd nadat ze zijn opgehaald.</span><span class="sxs-lookup"><span data-stu-id="7a91f-166">Filters are more efficient than other parameters, because the provider applies them when it retrieves the objects instead of having PowerShell filter the objects after they are retrieved.</span></span>

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

### <span data-ttu-id="7a91f-167">-Include</span><span class="sxs-lookup"><span data-stu-id="7a91f-167">-Include</span></span>

<span data-ttu-id="7a91f-168">Hiermee geeft u de paden op die met deze cmdlet worden getest.</span><span class="sxs-lookup"><span data-stu-id="7a91f-168">Specifies paths that this cmdlet tests.</span></span> <span data-ttu-id="7a91f-169">De waarde van deze para meter komt in aanmerking voor de para meter **Path** .</span><span class="sxs-lookup"><span data-stu-id="7a91f-169">The value of this parameter qualifies the **Path** parameter.</span></span> <span data-ttu-id="7a91f-170">Voer een element of patroon van een pad in, zoals \*. txt.</span><span class="sxs-lookup"><span data-stu-id="7a91f-170">Enter a path element or pattern, such as "\*.txt".</span></span> <span data-ttu-id="7a91f-171">Joker tekens zijn toegestaan.</span><span class="sxs-lookup"><span data-stu-id="7a91f-171">Wildcard characters are permitted.</span></span>

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

### <span data-ttu-id="7a91f-172">-IsValid</span><span class="sxs-lookup"><span data-stu-id="7a91f-172">-IsValid</span></span>

<span data-ttu-id="7a91f-173">Geeft aan dat met deze cmdlet de syntaxis van het pad wordt getest, ongeacht of de elementen van het pad bestaan.</span><span class="sxs-lookup"><span data-stu-id="7a91f-173">Indicates that this cmdlet tests the syntax of the path, regardless of whether the elements of the path exist.</span></span> <span data-ttu-id="7a91f-174">Met deze cmdlet wordt geretourneerd `$True` als de syntaxis van het pad geldig is en `$False` als dit niet het geval is.</span><span class="sxs-lookup"><span data-stu-id="7a91f-174">This cmdlet returns `$True` if the path syntax is valid and `$False` if it is not.</span></span>

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

### <span data-ttu-id="7a91f-175">-LiteralPath</span><span class="sxs-lookup"><span data-stu-id="7a91f-175">-LiteralPath</span></span>

<span data-ttu-id="7a91f-176">Hiermee geeft u een pad op dat moet worden getest.</span><span class="sxs-lookup"><span data-stu-id="7a91f-176">Specifies a path to be tested.</span></span> <span data-ttu-id="7a91f-177">In tegens telling tot **Path** wordt de waarde van de para meter **LiteralPath** exact gebruikt wanneer deze wordt getypt.</span><span class="sxs-lookup"><span data-stu-id="7a91f-177">Unlike **Path**, the value of the **LiteralPath** parameter is used exactly as it is typed.</span></span> <span data-ttu-id="7a91f-178">Er worden geen tekens geïnterpreteerd als joker tekens.</span><span class="sxs-lookup"><span data-stu-id="7a91f-178">No characters are interpreted as wildcard characters.</span></span> <span data-ttu-id="7a91f-179">Als het pad tekens bevat die kunnen worden geïnterpreteerd door Power shell als escape-teken reeksen, moet u het pad in één aanhalings teken plaatsen zodat ze niet worden geïnterpreteerd.</span><span class="sxs-lookup"><span data-stu-id="7a91f-179">If the path includes characters that could be interpreted by PowerShell as escape sequences, you must enclose the path in single quote so that they won't be interpreted.</span></span>

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

### <span data-ttu-id="7a91f-180">-NewerThan</span><span class="sxs-lookup"><span data-stu-id="7a91f-180">-NewerThan</span></span>

<span data-ttu-id="7a91f-181">Geef een tijd op als een **DateTime** -object.</span><span class="sxs-lookup"><span data-stu-id="7a91f-181">Specify a time as a **DateTime** object.</span></span>

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

### <span data-ttu-id="7a91f-182">-OlderThan</span><span class="sxs-lookup"><span data-stu-id="7a91f-182">-OlderThan</span></span>

<span data-ttu-id="7a91f-183">Geef een tijd op als een **DateTime** -object.</span><span class="sxs-lookup"><span data-stu-id="7a91f-183">Specify a time as a **DateTime** object.</span></span>

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

### <span data-ttu-id="7a91f-184">-Path</span><span class="sxs-lookup"><span data-stu-id="7a91f-184">-Path</span></span>

<span data-ttu-id="7a91f-185">Hiermee geeft u een pad op dat moet worden getest.</span><span class="sxs-lookup"><span data-stu-id="7a91f-185">Specifies a path to be tested.</span></span> <span data-ttu-id="7a91f-186">Joker tekens zijn toegestaan.</span><span class="sxs-lookup"><span data-stu-id="7a91f-186">Wildcard characters are permitted.</span></span> <span data-ttu-id="7a91f-187">Als het pad spaties bevat, plaatst u het tussen aanhalings tekens.</span><span class="sxs-lookup"><span data-stu-id="7a91f-187">If the path includes spaces, enclose it in quotation marks.</span></span>

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

### <span data-ttu-id="7a91f-188">-PathType</span><span class="sxs-lookup"><span data-stu-id="7a91f-188">-PathType</span></span>

<span data-ttu-id="7a91f-189">Hiermee geeft u het type van het laatste element in het pad op.</span><span class="sxs-lookup"><span data-stu-id="7a91f-189">Specifies the type of the final element in the path.</span></span> <span data-ttu-id="7a91f-190">Met deze cmdlet wordt geretourneerd `$True` als het element van het opgegeven type is en `$False` als dit niet het geval is.</span><span class="sxs-lookup"><span data-stu-id="7a91f-190">This cmdlet returns `$True` if the element is of the specified type and `$False` if it is not.</span></span> <span data-ttu-id="7a91f-191">De aanvaardbare waarden voor deze parameter zijn:</span><span class="sxs-lookup"><span data-stu-id="7a91f-191">The acceptable values for this parameter are:</span></span>

- <span data-ttu-id="7a91f-192">Verpakking.</span><span class="sxs-lookup"><span data-stu-id="7a91f-192">Container.</span></span>
  <span data-ttu-id="7a91f-193">Een element met andere elementen, zoals een map of register sleutel.</span><span class="sxs-lookup"><span data-stu-id="7a91f-193">An element that contains other elements, such as a directory or registry key.</span></span>
- <span data-ttu-id="7a91f-194">Vertakking.</span><span class="sxs-lookup"><span data-stu-id="7a91f-194">Leaf.</span></span>
  <span data-ttu-id="7a91f-195">Een element dat geen andere elementen bevat, zoals een bestand.</span><span class="sxs-lookup"><span data-stu-id="7a91f-195">An element that does not contain other elements, such as a file.</span></span>
- <span data-ttu-id="7a91f-196">Iedere.</span><span class="sxs-lookup"><span data-stu-id="7a91f-196">Any.</span></span>
  <span data-ttu-id="7a91f-197">Ofwel een container of een Leaf.</span><span class="sxs-lookup"><span data-stu-id="7a91f-197">Either a container or a leaf.</span></span>

<span data-ttu-id="7a91f-198">Hiermee wordt aangegeven of het laatste element in het pad van een bepaald type is.</span><span class="sxs-lookup"><span data-stu-id="7a91f-198">Tells whether the final element in the path is of a particular type.</span></span>

> [!CAUTION]
>
> <span data-ttu-id="7a91f-199">Tot en met de Power shell-versie 6.1.2, wanneer de opties **IsValid** en **PathType** samen worden opgegeven, wordt `Test-Path` de schakel optie **PathType** door de cmdlet genegeerd en wordt alleen het pad van de syntactisch gevalideerd zonder het padtype te valideren.</span><span class="sxs-lookup"><span data-stu-id="7a91f-199">Up to PowerShell version 6.1.2, when the **IsValid** and **PathType** switches are specified together, the `Test-Path` cmdlet ignores the **PathType** switch and only validates the syntactic path without validating the path type.</span></span>
>
> <span data-ttu-id="7a91f-200">Op basis van het [probleem #8607](https://github.com/PowerShell/PowerShell/issues/8607), kan het oplossen van dit gedrag een belang rijke wijziging in een toekomstige versie zijn, waarbij de functies **IsValid** en **PathType** deel uitmaken van afzonderlijke parameter sets, en dus niet gezamenlijk kunnen worden gebruikt om deze Verwar ring te voor komen.</span><span class="sxs-lookup"><span data-stu-id="7a91f-200">According to [issue #8607](https://github.com/PowerShell/PowerShell/issues/8607), fixing this behavior may be a breaking change in a future version, where the **IsValid** and **PathType** switches belong to separate parameter sets, and thus, cannot be used together avoiding this confusion.</span></span>

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

### <span data-ttu-id="7a91f-201">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="7a91f-201">CommonParameters</span></span>

<span data-ttu-id="7a91f-202">Deze cmdlet biedt ondersteuning voor de algemene para meters: `-Debug` , `-ErrorAction` , `-ErrorVariable` , `-InformationAction` , `-InformationVariable` , `-OutVariable` , `-OutBuffer` , `-PipelineVariable` , `-Verbose` , `-WarningAction` en `-WarningVariable` .</span><span class="sxs-lookup"><span data-stu-id="7a91f-202">This cmdlet supports the common parameters: `-Debug`, `-ErrorAction`, `-ErrorVariable`, `-InformationAction`, `-InformationVariable`, `-OutVariable`, `-OutBuffer`, `-PipelineVariable`, `-Verbose`, `-WarningAction`, and `-WarningVariable`.</span></span> <span data-ttu-id="7a91f-203">Zie [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="7a91f-203">For more information, see [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md).</span></span>

## <span data-ttu-id="7a91f-204">INVOER</span><span class="sxs-lookup"><span data-stu-id="7a91f-204">INPUTS</span></span>

### <span data-ttu-id="7a91f-205">System. String</span><span class="sxs-lookup"><span data-stu-id="7a91f-205">System.String</span></span>

<span data-ttu-id="7a91f-206">U kunt een teken reeks die een pad bevat, maar geen letterlijk pad, naar deze cmdlet pipet.</span><span class="sxs-lookup"><span data-stu-id="7a91f-206">You can pipe a string that contains a path, but not a literal path, to this cmdlet.</span></span>

## <span data-ttu-id="7a91f-207">UITVOER</span><span class="sxs-lookup"><span data-stu-id="7a91f-207">OUTPUTS</span></span>

### <span data-ttu-id="7a91f-208">System. Boolean</span><span class="sxs-lookup"><span data-stu-id="7a91f-208">System.Boolean</span></span>

<span data-ttu-id="7a91f-209">De cmdlet retourneert een **Booleaanse** waarde.</span><span class="sxs-lookup"><span data-stu-id="7a91f-209">The cmdlet returns a **Boolean** value.</span></span>

## <span data-ttu-id="7a91f-210">OPMERKINGEN</span><span class="sxs-lookup"><span data-stu-id="7a91f-210">NOTES</span></span>

<span data-ttu-id="7a91f-211">De cmdlets die het **pad naar** de tijdelijke naam (de **pad** -cmdlets) bevatten, werken met padnamen en retour neren de namen in een beknopt formaat dat alle Power shell-providers kunnen interpreteren.</span><span class="sxs-lookup"><span data-stu-id="7a91f-211">The cmdlets that contain the **Path** noun (the **Path** cmdlets) work with path names and return the names in a concise format that all PowerShell providers can interpret.</span></span> <span data-ttu-id="7a91f-212">Ze zijn ontworpen voor gebruik in Program ma's en scripts waarvoor u de volledige of gedeeltelijke naam van een pad wilt weer geven in een bepaalde indeling.</span><span class="sxs-lookup"><span data-stu-id="7a91f-212">They are designed for use in programs and scripts where you want to display all or part of a path name in a particular format.</span></span>
<span data-ttu-id="7a91f-213">Gebruik deze zoals u **mapnaam**, **Normpath**, **realpath**, **join's** of andere pad-werkers zou gebruiken.</span><span class="sxs-lookup"><span data-stu-id="7a91f-213">Use them as you would use **Dirname**, **Normpath**, **Realpath**, **Join**, or other path manipulators.</span></span>

<span data-ttu-id="7a91f-214">De `Test-Path` is ontworpen om te werken met de gegevens die door elke provider worden weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="7a91f-214">The `Test-Path` is designed to work with the data exposed by any provider.</span></span> <span data-ttu-id="7a91f-215">Als u een lijst wilt weer geven van de providers die beschikbaar zijn in uw sessie, typt u `Get-PSProvider` .</span><span class="sxs-lookup"><span data-stu-id="7a91f-215">To list the providers available in your session, type `Get-PSProvider`.</span></span> <span data-ttu-id="7a91f-216">Zie [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="7a91f-216">For more information, see [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md).</span></span>

## <span data-ttu-id="7a91f-217">GERELATEERDE KOPPELINGEN</span><span class="sxs-lookup"><span data-stu-id="7a91f-217">RELATED LINKS</span></span>

[<span data-ttu-id="7a91f-218">Convert-pad</span><span class="sxs-lookup"><span data-stu-id="7a91f-218">Convert-Path</span></span>](Convert-Path.md)

[<span data-ttu-id="7a91f-219">Pad voor samen voegen</span><span class="sxs-lookup"><span data-stu-id="7a91f-219">Join-Path</span></span>](Join-Path.md)

[<span data-ttu-id="7a91f-220">Oplossen-pad</span><span class="sxs-lookup"><span data-stu-id="7a91f-220">Resolve-Path</span></span>](Resolve-Path.md)

[<span data-ttu-id="7a91f-221">Split-pad</span><span class="sxs-lookup"><span data-stu-id="7a91f-221">Split-Path</span></span>](Split-Path.md)
