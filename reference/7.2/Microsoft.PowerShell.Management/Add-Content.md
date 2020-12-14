---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 08/19/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/add-content?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Add-Content
ms.openlocfilehash: e8db2deb302ad256464ae193ac38070525f1b2c6
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 11/17/2020
ms.locfileid: "94705748"
---
# <span data-ttu-id="a3e68-102">Add-Content</span><span class="sxs-lookup"><span data-stu-id="a3e68-102">Add-Content</span></span>

## <span data-ttu-id="a3e68-103">SAMENVATTING</span><span class="sxs-lookup"><span data-stu-id="a3e68-103">SYNOPSIS</span></span>
<span data-ttu-id="a3e68-104">Voegt inhoud toe aan de opgegeven items, zoals het toevoegen van woorden aan een bestand.</span><span class="sxs-lookup"><span data-stu-id="a3e68-104">Adds content to the specified items, such as adding words to a file.</span></span>

## <span data-ttu-id="a3e68-105">SYNTAXIS</span><span class="sxs-lookup"><span data-stu-id="a3e68-105">SYNTAX</span></span>

### <span data-ttu-id="a3e68-106">Pad (standaard)</span><span class="sxs-lookup"><span data-stu-id="a3e68-106">Path (Default)</span></span>

```
Add-Content [-Path] <string[]> [-Value] <Object[]> [-PassThru] [-Filter <string>]
 [-Include <string[]>] [-Exclude <string[]>] [-Force] [-Credential <pscredential>] [-WhatIf]
 [-Confirm] [-NoNewline] [-Encoding <Encoding>] [-AsByteStream] [-Stream <string>]
 [<CommonParameters>]
```

### <span data-ttu-id="a3e68-107">LiteralPath</span><span class="sxs-lookup"><span data-stu-id="a3e68-107">LiteralPath</span></span>

```
Add-Content [-Value] <Object[]> -LiteralPath <string[]> [-PassThru] [-Filter <string>]
 [-Include <string[]>] [-Exclude <string[]>] [-Force] [-Credential <pscredential>] [-WhatIf]
 [-Confirm] [-NoNewline] [-Encoding <Encoding>] [-AsByteStream] [-Stream <string>]
 [<CommonParameters>]
```

## <span data-ttu-id="a3e68-108">BESCHRIJVING</span><span class="sxs-lookup"><span data-stu-id="a3e68-108">DESCRIPTION</span></span>

<span data-ttu-id="a3e68-109">De `Add-Content` cmdlet voegt inhoud toe aan een opgegeven item of bestand.</span><span class="sxs-lookup"><span data-stu-id="a3e68-109">The `Add-Content` cmdlet appends content to a specified item or file.</span></span> <span data-ttu-id="a3e68-110">U kunt de inhoud opgeven door de inhoud in de opdracht te typen of door een object op te geven dat de inhoud bevat.</span><span class="sxs-lookup"><span data-stu-id="a3e68-110">You can specify the content by typing the content in the command or by specifying an object that contains the content.</span></span>

<span data-ttu-id="a3e68-111">Zie [Nieuw-item](New-Item.md)als u bestanden of mappen wilt maken voor de volgende voor beelden.</span><span class="sxs-lookup"><span data-stu-id="a3e68-111">If you need to create files or directories for the following examples, see [New-Item](New-Item.md).</span></span>

## <span data-ttu-id="a3e68-112">VOORBEELDEN</span><span class="sxs-lookup"><span data-stu-id="a3e68-112">EXAMPLES</span></span>

### <span data-ttu-id="a3e68-113">Voor beeld 1: een teken reeks toevoegen aan alle tekst bestanden met een uitzonde ring</span><span class="sxs-lookup"><span data-stu-id="a3e68-113">Example 1: Add a string to all text files with an exception</span></span>

<span data-ttu-id="a3e68-114">In dit voor beeld wordt een waarde aan tekst bestanden in de huidige map toegevoegd, maar worden bestanden uitgesloten op basis van de bestands naam.</span><span class="sxs-lookup"><span data-stu-id="a3e68-114">This example appends a value to text files in the current directory but excludes files based on their file name.</span></span>

```powershell
Add-Content -Path .\*.txt -Exclude help* -Value 'End of file'
```

<span data-ttu-id="a3e68-115">De para meter **Path** geeft alle `.txt` bestanden in de huidige map op, maar de **exclude** -para meter negeert bestands namen die overeenkomen met het opgegeven patroon.</span><span class="sxs-lookup"><span data-stu-id="a3e68-115">The **Path** parameter specifies all `.txt` files in the current directory, but the **Exclude** parameter ignores file names that match the specified pattern.</span></span> <span data-ttu-id="a3e68-116">De **waarde** para meter geeft u de teken reeks op die naar de bestanden wordt geschreven.</span><span class="sxs-lookup"><span data-stu-id="a3e68-116">The **Value** parameter specifies the text string that is written to the files.</span></span>

### <span data-ttu-id="a3e68-117">Voor beeld 2: een datum toevoegen aan het einde van de opgegeven bestanden</span><span class="sxs-lookup"><span data-stu-id="a3e68-117">Example 2: Add a date to the end of the specified files</span></span>

<span data-ttu-id="a3e68-118">In dit voor beeld wordt de datum toegevoegd aan bestanden in de huidige map en wordt de datum weer gegeven in de Power shell-console.</span><span class="sxs-lookup"><span data-stu-id="a3e68-118">This example appends the date to files in the current directory and displays the date in the PowerShell console.</span></span>

```powershell
Add-Content -Path .\DateTimeFile1.log, .\DateTimeFile2.log -Value (Get-Date) -PassThru
Get-Content -Path .\DateTimeFile1.log
```

```Output
Tuesday, May 14, 2019 8:24:27 AM
Tuesday, May 14, 2019 8:24:27 AM
5/14/2019 8:24:27 AM
```

<span data-ttu-id="a3e68-119">De `Add-Content` cmdlet maakt twee nieuwe bestanden in de huidige map.</span><span class="sxs-lookup"><span data-stu-id="a3e68-119">The `Add-Content` cmdlet creates two new files in the current directory.</span></span> <span data-ttu-id="a3e68-120">De **waarde** -para meter bevat de uitvoer van de `Get-Date` cmdlet.</span><span class="sxs-lookup"><span data-stu-id="a3e68-120">The **Value** parameter contains the output of the `Get-Date` cmdlet.</span></span> <span data-ttu-id="a3e68-121">De para meter **PassThru** voert de toegevoegde inhoud uit naar de pijp lijn.</span><span class="sxs-lookup"><span data-stu-id="a3e68-121">The **PassThru** parameter outputs the added contents to the pipeline.</span></span>
<span data-ttu-id="a3e68-122">Omdat er geen andere cmdlet is om de uitvoer te ontvangen, wordt deze weer gegeven in de Power shell-console.</span><span class="sxs-lookup"><span data-stu-id="a3e68-122">Because there is no other cmdlet to receive the output, it is displayed in the PowerShell console.</span></span>
<span data-ttu-id="a3e68-123">Met de `Get-Content` cmdlet wordt het bijgewerkte bestand weer gegeven, `DateTimeFile1.log` .</span><span class="sxs-lookup"><span data-stu-id="a3e68-123">The `Get-Content` cmdlet displays the updated file, `DateTimeFile1.log`.</span></span>

### <span data-ttu-id="a3e68-124">Voor beeld 3: de inhoud van een opgegeven bestand toevoegen aan een ander bestand</span><span class="sxs-lookup"><span data-stu-id="a3e68-124">Example 3: Add the contents of a specified file to another file</span></span>

<span data-ttu-id="a3e68-125">In dit voor beeld wordt de inhoud van een bestand opgehaald en wordt de inhoud in een variabele opgeslagen.</span><span class="sxs-lookup"><span data-stu-id="a3e68-125">This example gets the content from a file and stores the content in a variable.</span></span> <span data-ttu-id="a3e68-126">De variabele wordt gebruikt om de inhoud toe te voegen aan een ander bestand.</span><span class="sxs-lookup"><span data-stu-id="a3e68-126">The variable is used to append the content into another file.</span></span>

```powershell
$From = Get-Content -Path .\CopyFromFile.txt
Add-Content -Path .\CopyToFile.txt -Value $From
Get-Content -Path .\CopyToFile.txt
```

- <span data-ttu-id="a3e68-127">`Get-Content`Met de cmdlet wordt de inhoud van opgehaald `CopyFromFile.txt` en wordt de inhoud in de `$From` variabele opgeslagen.</span><span class="sxs-lookup"><span data-stu-id="a3e68-127">The `Get-Content` cmdlet gets the contents of `CopyFromFile.txt` and stores the contents in the `$From` variable.</span></span>
- <span data-ttu-id="a3e68-128">De `Add-Content` cmdlet werkt het `CopyToFile.txt` bestand bij met de inhoud van de `$From` variabele.</span><span class="sxs-lookup"><span data-stu-id="a3e68-128">The `Add-Content` cmdlet updates the `CopyToFile.txt` file using the contents of the `$From` variable.</span></span>
- <span data-ttu-id="a3e68-129">De `Get-Content` cmdlet geeft CopyToFile.txt weer.</span><span class="sxs-lookup"><span data-stu-id="a3e68-129">The `Get-Content` cmdlet displays CopyToFile.txt.</span></span>

### <span data-ttu-id="a3e68-130">Voor beeld 4: de inhoud van een opgegeven bestand toevoegen aan een ander bestand met behulp van de pijp lijn</span><span class="sxs-lookup"><span data-stu-id="a3e68-130">Example 4: Add the contents of a specified file to another file using the pipeline</span></span>

<span data-ttu-id="a3e68-131">In dit voor beeld wordt de inhoud van een bestand opgehaald en wordt deze naar de cmdlet gesluizen `Add-Content` .</span><span class="sxs-lookup"><span data-stu-id="a3e68-131">This example gets the content from a file and pipes it to the `Add-Content` cmdlet.</span></span>

```powershell
Get-Content -Path .\CopyFromFile.txt | Add-Content -Path .\CopyToFile.txt
Get-Content -Path .\CopyToFile.txt
```

<span data-ttu-id="a3e68-132">`Get-Content`Met de cmdlet wordt de inhoud van opgehaald `CopyFromFile.txt` .</span><span class="sxs-lookup"><span data-stu-id="a3e68-132">The `Get-Content` cmdlet gets the contents of `CopyFromFile.txt`.</span></span> <span data-ttu-id="a3e68-133">De resultaten worden door gegeven aan de `Add-Content` cmdlet, waarmee de wordt bijgewerkt `CopyToFile.txt` .</span><span class="sxs-lookup"><span data-stu-id="a3e68-133">The results are piped to the `Add-Content` cmdlet, which updates the `CopyToFile.txt`.</span></span>
<span data-ttu-id="a3e68-134">De laatste `Get-Content` cmdlet wordt weer gegeven `CopyToFile.txt` .</span><span class="sxs-lookup"><span data-stu-id="a3e68-134">The last `Get-Content` cmdlet displays `CopyToFile.txt`.</span></span>

### <span data-ttu-id="a3e68-135">Voor beeld 5: een nieuw bestand maken en inhoud kopiëren</span><span class="sxs-lookup"><span data-stu-id="a3e68-135">Example 5: Create a new file and copy content</span></span>

<span data-ttu-id="a3e68-136">In dit voor beeld wordt een nieuw bestand gemaakt en wordt de inhoud van een bestaand bestand gekopieerd naar het nieuwe bestand.</span><span class="sxs-lookup"><span data-stu-id="a3e68-136">This example creates a new file and copies an existing file's content into the new file.</span></span>

```powershell
Add-Content -Path .\NewFile.txt -Value (Get-Content -Path .\CopyFromFile.txt)
Get-Content -Path .\NewFile.txt
```

- <span data-ttu-id="a3e68-137">De `Add-Content` cmdlet maakt gebruik van de para meters **pad** en **waarde** voor het maken van een nieuw bestand in de huidige map.</span><span class="sxs-lookup"><span data-stu-id="a3e68-137">The `Add-Content` cmdlet uses the **Path** and **Value** parameters to create a new file in the current directory.</span></span>
- <span data-ttu-id="a3e68-138">Met de `Get-Content` cmdlet wordt de inhoud van een bestaand bestand opgehaald `CopyFromFile.txt` en door gegeven aan de **waarde** -para meter.</span><span class="sxs-lookup"><span data-stu-id="a3e68-138">The `Get-Content` cmdlet gets the contents of an existing file, `CopyFromFile.txt` and passes it to the **Value** parameter.</span></span> <span data-ttu-id="a3e68-139">De haakjes rond de `Get-Content` cmdlet zorgen ervoor dat de opdracht is voltooid voordat de `Add-Content` opdracht wordt gestart.</span><span class="sxs-lookup"><span data-stu-id="a3e68-139">The parentheses around the `Get-Content` cmdlet ensure that the command finishes before the `Add-Content` command begins.</span></span>
- <span data-ttu-id="a3e68-140">`Get-Content`Met de cmdlet wordt de inhoud van het nieuwe bestand weer gegeven `NewFile.txt` .</span><span class="sxs-lookup"><span data-stu-id="a3e68-140">The `Get-Content` cmdlet displays the contents of the new file, `NewFile.txt`.</span></span>

### <span data-ttu-id="a3e68-141">Voor beeld 6: inhoud toevoegen aan een alleen-lezen bestand</span><span class="sxs-lookup"><span data-stu-id="a3e68-141">Example 6: Add content to a read-only file</span></span>

<span data-ttu-id="a3e68-142">Met deze opdracht wordt een waarde aan het bestand toegevoegd, zelfs als het kenmerk bestand **IsReadOnly** is ingesteld op **True**.</span><span class="sxs-lookup"><span data-stu-id="a3e68-142">This command adds a value to the file even if the **IsReadOnly** file attribute is set to **True**.</span></span>
<span data-ttu-id="a3e68-143">De stappen voor het maken van een alleen-lezen bestand zijn opgenomen in het voor beeld.</span><span class="sxs-lookup"><span data-stu-id="a3e68-143">The steps to create a read-only file are included in the example.</span></span>

```powershell
New-Item -Path .\IsReadOnlyTextFile.txt -ItemType File
Set-ItemProperty -Path .\IsReadOnlyTextFile.txt -Name IsReadOnly -Value $True
Get-ChildItem -Path .\IsReadOnlyTextFile.txt
Add-Content -Path .\IsReadOnlyTextFile.txt -Value 'Add value to read-only text file' -Force
Get-Content -Path .\IsReadOnlyTextFile.txt
```

```Output
Mode                LastWriteTime         Length Name
----                -------------         ------ ----
-ar--         1/28/2019     13:35              0 IsReadOnlyTextFile.txt
```

- <span data-ttu-id="a3e68-144">De `New-Item` cmdlet gebruikt de para meter **Path** en **item** type om het bestand `IsReadOnlyTextFile.txt` in de huidige map te maken.</span><span class="sxs-lookup"><span data-stu-id="a3e68-144">The `New-Item` cmdlet uses the **Path** and **ItemType** parameters to create the file `IsReadOnlyTextFile.txt` in the current directory.</span></span>
- <span data-ttu-id="a3e68-145">De `Set-ItemProperty` cmdlet gebruikt de para meters **name** en **Value** om de eigenschap **IsReadOnly** van het bestand te wijzigen in True.</span><span class="sxs-lookup"><span data-stu-id="a3e68-145">The `Set-ItemProperty` cmdlet uses the **Name** and **Value** parameters to change the file's **IsReadOnly** property to True.</span></span>
- <span data-ttu-id="a3e68-146">De `Get-ChildItem` cmdlet geeft aan dat het bestand leeg is (0) en het kenmerk alleen-lezen ( `r` ) heeft.</span><span class="sxs-lookup"><span data-stu-id="a3e68-146">The `Get-ChildItem` cmdlet shows the file is empty (0) and has the read-only attribute (`r`).</span></span>
- <span data-ttu-id="a3e68-147">De `Add-Content` cmdlet gebruikt de para meter **Path** om het bestand op te geven.</span><span class="sxs-lookup"><span data-stu-id="a3e68-147">The `Add-Content` cmdlet uses the **Path** parameter to specify the file.</span></span> <span data-ttu-id="a3e68-148">De **waarde** para meter bevat de teken reeks die moet worden toegevoegd aan het bestand.</span><span class="sxs-lookup"><span data-stu-id="a3e68-148">The **Value** parameter includes the text string to append to the file.</span></span> <span data-ttu-id="a3e68-149">De para meter **Force** schrijft de tekst naar het bestand met het kenmerk alleen-lezen.</span><span class="sxs-lookup"><span data-stu-id="a3e68-149">The **Force** parameter writes the text to the read-only file.</span></span>
- <span data-ttu-id="a3e68-150">De `Get-Content` cmdlet gebruikt de para meter **Path** om de inhoud van het bestand weer te geven.</span><span class="sxs-lookup"><span data-stu-id="a3e68-150">The `Get-Content` cmdlet uses the **Path** parameter to display the file's contents.</span></span>

<span data-ttu-id="a3e68-151">Als u het kenmerk alleen-lezen wilt verwijderen, gebruikt u de `Set-ItemProperty` opdracht met de para meter **Value** ingesteld op `False` .</span><span class="sxs-lookup"><span data-stu-id="a3e68-151">To remove the read-only attribute, use the `Set-ItemProperty` command with the **Value** parameter set to `False`.</span></span>

### <span data-ttu-id="a3e68-152">Voor beeld 7: filters gebruiken met Add-Content</span><span class="sxs-lookup"><span data-stu-id="a3e68-152">Example 7: Use Filters with Add-Content</span></span>

<span data-ttu-id="a3e68-153">U kunt een filter opgeven voor de `Add-Content` cmdlet.</span><span class="sxs-lookup"><span data-stu-id="a3e68-153">You can specify a filter to the `Add-Content` cmdlet.</span></span> <span data-ttu-id="a3e68-154">Wanneer u filters gebruikt om de para meter **Path** te kwalificeren, moet u een asterisk ( `*` ) toevoegen om de inhoud van het pad aan te geven.</span><span class="sxs-lookup"><span data-stu-id="a3e68-154">When using filters to qualify the **Path** parameter, you need to include a trailing asterisk (`*`) to indicate the contents of the path.</span></span>

<span data-ttu-id="a3e68-155">Met de volgende opdracht wordt het woord ' gereed ' toegevoegd aan de inhoud van alle `*.txt` bestanden in de `C:\Temp` map.</span><span class="sxs-lookup"><span data-stu-id="a3e68-155">The following command adds the word "Done" the content of all `*.txt` files in the `C:\Temp` directory.</span></span>

```powershell
Add-Content -Path C:\Temp\* -Filter *.txt -Value "Done"
```

## <span data-ttu-id="a3e68-156">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="a3e68-156">PARAMETERS</span></span>

### <span data-ttu-id="a3e68-157">-AsByteStream</span><span class="sxs-lookup"><span data-stu-id="a3e68-157">-AsByteStream</span></span>

<span data-ttu-id="a3e68-158">Hiermee geeft u op dat de inhoud moet worden gelezen als een byte stroom.</span><span class="sxs-lookup"><span data-stu-id="a3e68-158">Specifies that the content should be read as a stream of bytes.</span></span> <span data-ttu-id="a3e68-159">Deze para meter is geïntroduceerd in Power shell 6,0.</span><span class="sxs-lookup"><span data-stu-id="a3e68-159">This parameter was introduced in PowerShell 6.0.</span></span>

<span data-ttu-id="a3e68-160">Er treedt een waarschuwing op wanneer u de para meter **AsByteStream** gebruikt met de para meter **Encoding** .</span><span class="sxs-lookup"><span data-stu-id="a3e68-160">A warning occurs when you use the **AsByteStream** parameter with the **Encoding** parameter.</span></span> <span data-ttu-id="a3e68-161">De para meter **AsByteStream** negeert elke code ring en de uitvoer wordt geretourneerd als een byte stroom.</span><span class="sxs-lookup"><span data-stu-id="a3e68-161">The **AsByteStream** parameter ignores any encoding and the output is returned as a stream of bytes.</span></span>

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

### <span data-ttu-id="a3e68-162">-Credential</span><span class="sxs-lookup"><span data-stu-id="a3e68-162">-Credential</span></span>

> [!NOTE]
> <span data-ttu-id="a3e68-163">Deze para meter wordt niet ondersteund door providers die zijn geïnstalleerd met Power shell.</span><span class="sxs-lookup"><span data-stu-id="a3e68-163">This parameter is not supported by any providers installed with PowerShell.</span></span>
> <span data-ttu-id="a3e68-164">Gebruik [invoke-Command](../Microsoft.PowerShell.Core/Invoke-Command.md)om een andere gebruiker te imiteren of uw referenties te verhogen wanneer u deze cmdlet uitvoert.</span><span class="sxs-lookup"><span data-stu-id="a3e68-164">To impersonate another user, or elevate your credentials when running this cmdlet, use [Invoke-Command](../Microsoft.PowerShell.Core/Invoke-Command.md).</span></span>

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

### <span data-ttu-id="a3e68-165">-Encoding</span><span class="sxs-lookup"><span data-stu-id="a3e68-165">-Encoding</span></span>

<span data-ttu-id="a3e68-166">Hiermee geeft u het type code ring voor het doel bestand op.</span><span class="sxs-lookup"><span data-stu-id="a3e68-166">Specifies the type of encoding for the target file.</span></span> <span data-ttu-id="a3e68-167">De standaardwaarde is `utf8NoBOM`.</span><span class="sxs-lookup"><span data-stu-id="a3e68-167">The default value is `utf8NoBOM`.</span></span>

<span data-ttu-id="a3e68-168">Encoding is een dynamische para meter die de File System Provider toevoegt aan de `Add-Content` cmdlet.</span><span class="sxs-lookup"><span data-stu-id="a3e68-168">Encoding is a dynamic parameter that the FileSystem provider adds to the `Add-Content` cmdlet.</span></span> <span data-ttu-id="a3e68-169">Deze para meter werkt alleen op stations met een bestands systeem.</span><span class="sxs-lookup"><span data-stu-id="a3e68-169">This parameter works only in file system drives.</span></span>

<span data-ttu-id="a3e68-170">De acceptabele waarden voor deze para meter zijn als volgt:</span><span class="sxs-lookup"><span data-stu-id="a3e68-170">The acceptable values for this parameter are as follows:</span></span>

- <span data-ttu-id="a3e68-171">`ascii`: Gebruikt de code ring voor de ASCII-tekenset (7-bits).</span><span class="sxs-lookup"><span data-stu-id="a3e68-171">`ascii`: Uses the encoding for the ASCII (7-bit) character set.</span></span>
- <span data-ttu-id="a3e68-172">`bigendianunicode`: Wordt gecodeerd in UTF-16-indeling met behulp van de byte volgorde big endian.</span><span class="sxs-lookup"><span data-stu-id="a3e68-172">`bigendianunicode`: Encodes in UTF-16 format using the big-endian byte order.</span></span>
- <span data-ttu-id="a3e68-173">`bigendianutf32`: Codeert in UTF-32-indeling met behulp van de byte volgorde big endian.</span><span class="sxs-lookup"><span data-stu-id="a3e68-173">`bigendianutf32`: Encodes in UTF-32 format using the big-endian byte order.</span></span>
- <span data-ttu-id="a3e68-174">`oem`: Maakt gebruik van de standaard codering voor MS-DOS-en console Programma's.</span><span class="sxs-lookup"><span data-stu-id="a3e68-174">`oem`: Uses the default encoding for MS-DOS and console programs.</span></span>
- <span data-ttu-id="a3e68-175">`unicode`: Wordt gecodeerd in UTF-16-indeling met behulp van de byte volgorde little endian.</span><span class="sxs-lookup"><span data-stu-id="a3e68-175">`unicode`: Encodes in UTF-16 format using the little-endian byte order.</span></span>
- <span data-ttu-id="a3e68-176">`utf7`: Wordt gecodeerd in de indeling UTF-7.</span><span class="sxs-lookup"><span data-stu-id="a3e68-176">`utf7`: Encodes in UTF-7 format.</span></span>
- <span data-ttu-id="a3e68-177">`utf8`: Wordt gecodeerd in UTF-8-indeling.</span><span class="sxs-lookup"><span data-stu-id="a3e68-177">`utf8`: Encodes in UTF-8 format.</span></span>
- <span data-ttu-id="a3e68-178">`utf8BOM`: Code ring in UTF-8-indeling met byte order Mark (BOM)</span><span class="sxs-lookup"><span data-stu-id="a3e68-178">`utf8BOM`: Encodes in UTF-8 format with Byte Order Mark (BOM)</span></span>
- <span data-ttu-id="a3e68-179">`utf8NoBOM`: Code ring in UTF-8-indeling zonder byte order Mark (BOM)</span><span class="sxs-lookup"><span data-stu-id="a3e68-179">`utf8NoBOM`: Encodes in UTF-8 format without Byte Order Mark (BOM)</span></span>
- <span data-ttu-id="a3e68-180">`utf32`: Gecodeerd in UTF-32-indeling.</span><span class="sxs-lookup"><span data-stu-id="a3e68-180">`utf32`: Encodes in UTF-32 format.</span></span>

<span data-ttu-id="a3e68-181">Vanaf Power shell 6,2 kunnen met de para meter **Encoding** ook numerieke id's van geregistreerde code pagina's (zoals `-Encoding 1251` ) of teken reeks namen van geregistreerde code pagina's (zoals) worden toegestaan `-Encoding "windows-1251"` .</span><span class="sxs-lookup"><span data-stu-id="a3e68-181">Beginning with PowerShell 6.2, the **Encoding** parameter also allows numeric IDs of registered code pages (like `-Encoding 1251`) or string names of registered code pages (like `-Encoding "windows-1251"`).</span></span> <span data-ttu-id="a3e68-182">Zie de .NET-documentatie voor [code ring. code tabel](/dotnet/api/system.text.encoding.codepage?view=netcore-2.2)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="a3e68-182">For more information, see the .NET documentation for [Encoding.CodePage](/dotnet/api/system.text.encoding.codepage?view=netcore-2.2).</span></span>

> [!NOTE]
> <span data-ttu-id="a3e68-183">**UTF-7** _ wordt niet meer aanbevolen om te gebruiken.</span><span class="sxs-lookup"><span data-stu-id="a3e68-183">**UTF-7** _ is no longer recommended to use.</span></span> <span data-ttu-id="a3e68-184">In Power shell 7,1 wordt een waarschuwing geschreven als u `utf7` de para meter _ *Encoding*\* opgeeft.</span><span class="sxs-lookup"><span data-stu-id="a3e68-184">In PowerShell 7.1, a warning is written if you specify `utf7` for the _ *Encoding*\* parameter.</span></span>

```yaml
Type: System.Text.Encoding
Parameter Sets: (All)
Aliases:
Accepted values: ASCII, BigEndianUnicode, BigEndianUTF32, OEM, Unicode, UTF7, UTF8, UTF8BOM, UTF8NoBOM, UTF32

Required: False
Position: Named
Default value: UTF8NoBOM
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="a3e68-185">-Uitsluiten</span><span class="sxs-lookup"><span data-stu-id="a3e68-185">-Exclude</span></span>

<span data-ttu-id="a3e68-186">Hiermee geeft u als een teken reeks matrix een item of items die met deze cmdlet worden uitgesloten in de bewerking.</span><span class="sxs-lookup"><span data-stu-id="a3e68-186">Specifies, as a string array, an item or items that this cmdlet excludes in the operation.</span></span> <span data-ttu-id="a3e68-187">De waarde van deze para meter komt in aanmerking voor de para meter **Path** .</span><span class="sxs-lookup"><span data-stu-id="a3e68-187">The value of this parameter qualifies the **Path** parameter.</span></span> <span data-ttu-id="a3e68-188">Voer een element of patroon van een pad in, zoals `*.txt` .</span><span class="sxs-lookup"><span data-stu-id="a3e68-188">Enter a path element or pattern, such as `*.txt`.</span></span> <span data-ttu-id="a3e68-189">Joker tekens zijn toegestaan.</span><span class="sxs-lookup"><span data-stu-id="a3e68-189">Wildcard characters are permitted.</span></span> <span data-ttu-id="a3e68-190">De **exclude** -para meter is alleen effectief wanneer de inhoud van een item wordt opgenomen, zoals `C:\Windows\*` , waarbij het Joker teken de inhoud van de `C:\Windows` map bevat.</span><span class="sxs-lookup"><span data-stu-id="a3e68-190">The **Exclude** parameter is effective only when the command includes the contents of an item, such as `C:\Windows\*`, where the wildcard character specifies the contents of the `C:\Windows` directory.</span></span>

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

### <span data-ttu-id="a3e68-191">-Filter</span><span class="sxs-lookup"><span data-stu-id="a3e68-191">-Filter</span></span>

<span data-ttu-id="a3e68-192">Hiermee geeft u een filter op om de para meter **Path** te kwalificeren.</span><span class="sxs-lookup"><span data-stu-id="a3e68-192">Specifies a filter to qualify the **Path** parameter.</span></span> <span data-ttu-id="a3e68-193">De [File System](../Microsoft.PowerShell.Core/About/about_FileSystem_Provider.md) -provider is de enige geïnstalleerde Power shell-provider die het gebruik van filters ondersteunt.</span><span class="sxs-lookup"><span data-stu-id="a3e68-193">The [FileSystem](../Microsoft.PowerShell.Core/About/about_FileSystem_Provider.md) provider is the only installed PowerShell provider that supports the use of filters.</span></span> <span data-ttu-id="a3e68-194">U kunt de syntaxis voor de filter taal van het **Bestands systeem** in [about_Wildcards](../Microsoft.PowerShell.Core/About/about_Wildcards.md)vinden.</span><span class="sxs-lookup"><span data-stu-id="a3e68-194">You can find the syntax for the **FileSystem** filter language in [about_Wildcards](../Microsoft.PowerShell.Core/About/about_Wildcards.md).</span></span>
<span data-ttu-id="a3e68-195">Filters zijn efficiënter dan andere para meters, omdat deze door de provider worden toegepast wanneer de cmdlet de objecten ophaalt in plaats van dat Power shell de objecten heeft gefilterd nadat ze zijn opgehaald.</span><span class="sxs-lookup"><span data-stu-id="a3e68-195">Filters are more efficient than other parameters, because the provider applies them when the cmdlet gets the objects rather than having PowerShell filter the objects after they are retrieved.</span></span>

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

### <span data-ttu-id="a3e68-196">-Force</span><span class="sxs-lookup"><span data-stu-id="a3e68-196">-Force</span></span>

<span data-ttu-id="a3e68-197">Onderdrukt het kenmerk alleen-lezen, zodat u inhoud kunt toevoegen aan een alleen-lezen bestand.</span><span class="sxs-lookup"><span data-stu-id="a3e68-197">Overrides the read-only attribute, allowing you to add content to a read-only file.</span></span> <span data-ttu-id="a3e68-198">**Forceert** bijvoorbeeld het kenmerk alleen-lezen of maakt mappen om een bestandspad te volt ooien, maar er wordt geen poging gedaan om bestands machtigingen te wijzigen.</span><span class="sxs-lookup"><span data-stu-id="a3e68-198">For example, **Force** will override the read-only attribute or create directories to complete a file path, but it will not attempt to change file permissions.</span></span>

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

### <span data-ttu-id="a3e68-199">-Include</span><span class="sxs-lookup"><span data-stu-id="a3e68-199">-Include</span></span>

<span data-ttu-id="a3e68-200">Hiermee wordt een teken reeks matrix opgegeven, een item of items die met deze cmdlet in de bewerking zijn opgenomen.</span><span class="sxs-lookup"><span data-stu-id="a3e68-200">Specifies, as a string array, an item or items that this cmdlet includes in the operation.</span></span> <span data-ttu-id="a3e68-201">De waarde van deze para meter komt in aanmerking voor de para meter **Path** .</span><span class="sxs-lookup"><span data-stu-id="a3e68-201">The value of this parameter qualifies the **Path** parameter.</span></span> <span data-ttu-id="a3e68-202">Voer een element of patroon van een pad in, zoals `"*.txt"` .</span><span class="sxs-lookup"><span data-stu-id="a3e68-202">Enter a path element or pattern, such as `"*.txt"`.</span></span> <span data-ttu-id="a3e68-203">Joker tekens zijn toegestaan.</span><span class="sxs-lookup"><span data-stu-id="a3e68-203">Wildcard characters are permitted.</span></span> <span data-ttu-id="a3e68-204">De para meter **include** is alleen effectief wanneer de inhoud van een item wordt opgenomen, zoals `C:\Windows\*` , waarbij het Joker teken de inhoud van de `C:\Windows` map bevat.</span><span class="sxs-lookup"><span data-stu-id="a3e68-204">The **Include** parameter is effective only when the command includes the contents of an item, such as `C:\Windows\*`, where the wildcard character specifies the contents of the `C:\Windows` directory.</span></span>

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

### <span data-ttu-id="a3e68-205">-LiteralPath</span><span class="sxs-lookup"><span data-stu-id="a3e68-205">-LiteralPath</span></span>

<span data-ttu-id="a3e68-206">Hiermee geeft u een pad naar een of meer locaties.</span><span class="sxs-lookup"><span data-stu-id="a3e68-206">Specifies a path to one or more locations.</span></span> <span data-ttu-id="a3e68-207">De waarde van **LiteralPath** wordt precies zo gebruikt als deze wordt getypt.</span><span class="sxs-lookup"><span data-stu-id="a3e68-207">The value of **LiteralPath** is used exactly as it is typed.</span></span> <span data-ttu-id="a3e68-208">Geen tekens worden geïnterpreteerd als joker tekens.</span><span class="sxs-lookup"><span data-stu-id="a3e68-208">No characters are interpreted as wildcards.</span></span> <span data-ttu-id="a3e68-209">Als het pad escape tekens bevat, plaatst u het tussen enkele aanhalings tekens.</span><span class="sxs-lookup"><span data-stu-id="a3e68-209">If the path includes escape characters, enclose it in single quotation marks.</span></span> <span data-ttu-id="a3e68-210">Enkele aanhalings tekens geven aan dat Power shell geen karakters interpreteert als escape reeksen.</span><span class="sxs-lookup"><span data-stu-id="a3e68-210">Single quotation marks tell PowerShell not to interpret any characters as escape sequences.</span></span>

<span data-ttu-id="a3e68-211">Zie [about_Quoting_Rules](../Microsoft.Powershell.Core/About/about_Quoting_Rules.md)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="a3e68-211">For more information, see [about_Quoting_Rules](../Microsoft.Powershell.Core/About/about_Quoting_Rules.md).</span></span>

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

### <span data-ttu-id="a3e68-212">-Nieuwe regel</span><span class="sxs-lookup"><span data-stu-id="a3e68-212">-NoNewline</span></span>

<span data-ttu-id="a3e68-213">Geeft aan dat met deze cmdlet geen nieuwe regel wordt toegevoegd of het retour neren naar de inhoud.</span><span class="sxs-lookup"><span data-stu-id="a3e68-213">Indicates that this cmdlet does not add a new line or carriage return to the content.</span></span>

<span data-ttu-id="a3e68-214">De teken reeks representaties van de invoer objecten worden samengevoegd om de uitvoer te vormen.</span><span class="sxs-lookup"><span data-stu-id="a3e68-214">The string representations of the input objects are concatenated to form the output.</span></span> <span data-ttu-id="a3e68-215">Er worden geen spaties of nieuwe regels tussen de uitvoer teken reeksen ingevoegd.</span><span class="sxs-lookup"><span data-stu-id="a3e68-215">No spaces or newlines are inserted between the output strings.</span></span> <span data-ttu-id="a3e68-216">Er wordt geen nieuwe regel toegevoegd na de laatste uitvoer teken reeks.</span><span class="sxs-lookup"><span data-stu-id="a3e68-216">No newline is added after the last output string.</span></span>

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

### <span data-ttu-id="a3e68-217">-PassThru</span><span class="sxs-lookup"><span data-stu-id="a3e68-217">-PassThru</span></span>

<span data-ttu-id="a3e68-218">Retourneert een object dat de toegevoegde inhoud vertegenwoordigt.</span><span class="sxs-lookup"><span data-stu-id="a3e68-218">Returns an object representing the added content.</span></span> <span data-ttu-id="a3e68-219">Deze cmdlet genereert standaard geen uitvoer.</span><span class="sxs-lookup"><span data-stu-id="a3e68-219">By default, this cmdlet does not generate any output.</span></span>

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

### <span data-ttu-id="a3e68-220">-Path</span><span class="sxs-lookup"><span data-stu-id="a3e68-220">-Path</span></span>

<span data-ttu-id="a3e68-221">Hiermee geeft u het pad op naar de items die de extra inhoud ontvangen.</span><span class="sxs-lookup"><span data-stu-id="a3e68-221">Specifies the path to the items that receive the additional content.</span></span>
<span data-ttu-id="a3e68-222">Joker tekens zijn toegestaan.</span><span class="sxs-lookup"><span data-stu-id="a3e68-222">Wildcard characters are permitted.</span></span>
<span data-ttu-id="a3e68-223">De paden moeten paden naar items zijn en niet naar containers.</span><span class="sxs-lookup"><span data-stu-id="a3e68-223">The paths must be paths to items, not to containers.</span></span>
<span data-ttu-id="a3e68-224">U moet bijvoorbeeld een pad naar een of meer bestanden opgeven, niet een pad naar een map.</span><span class="sxs-lookup"><span data-stu-id="a3e68-224">For example, you must specify a path to one or more files, not a path to a directory.</span></span>
<span data-ttu-id="a3e68-225">Als u meerdere paden opgeeft, gebruikt u komma's om de paden van elkaar te scheiden.</span><span class="sxs-lookup"><span data-stu-id="a3e68-225">If you specify multiple paths, use commas to separate the paths.</span></span>

```yaml
Type: System.String[]
Parameter Sets: Path
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: True
```

### <span data-ttu-id="a3e68-226">-Stream</span><span class="sxs-lookup"><span data-stu-id="a3e68-226">-Stream</span></span>

<span data-ttu-id="a3e68-227">Hiermee geeft u een alternatieve gegevens stroom voor inhoud.</span><span class="sxs-lookup"><span data-stu-id="a3e68-227">Specifies an alternative data stream for content.</span></span> <span data-ttu-id="a3e68-228">Als de stroom niet bestaat, wordt deze gemaakt met deze cmdlet.</span><span class="sxs-lookup"><span data-stu-id="a3e68-228">If the stream does not exist, this cmdlet creates it.</span></span> <span data-ttu-id="a3e68-229">Joker tekens worden niet ondersteund.</span><span class="sxs-lookup"><span data-stu-id="a3e68-229">Wildcard characters are not supported.</span></span>

<span data-ttu-id="a3e68-230">**Stream** is een dynamische para meter waaraan de File System Provider toevoegt `Add-Content` .</span><span class="sxs-lookup"><span data-stu-id="a3e68-230">**Stream** is a dynamic parameter that the FileSystem provider adds to `Add-Content`.</span></span> <span data-ttu-id="a3e68-231">Deze para meter werkt alleen op stations met een bestands systeem.</span><span class="sxs-lookup"><span data-stu-id="a3e68-231">This parameter works only in file system drives.</span></span>

<span data-ttu-id="a3e68-232">U kunt de- `Add-Content` cmdlet gebruiken om de inhoud van de **zone te wijzigen. id** alternatieve gegevens stroom.</span><span class="sxs-lookup"><span data-stu-id="a3e68-232">You can use the `Add-Content` cmdlet to change the content of the **Zone.Identifier** alternate data stream.</span></span> <span data-ttu-id="a3e68-233">Dit wordt echter niet aangeraden als een manier om beveiligings controles te elimineren waarmee bestanden die worden gedownload van Internet, worden geblokkeerd.</span><span class="sxs-lookup"><span data-stu-id="a3e68-233">However, we do not recommend this as a way to eliminate security checks that block files that are downloaded from the Internet.</span></span> <span data-ttu-id="a3e68-234">Als u controleert of een gedownload bestand veilig is, gebruikt u de `Unblock-File` cmdlet.</span><span class="sxs-lookup"><span data-stu-id="a3e68-234">If you verify that a downloaded file is safe, use the `Unblock-File` cmdlet.</span></span>

<span data-ttu-id="a3e68-235">Deze para meter is geïntroduceerd in Power Shell 3,0.</span><span class="sxs-lookup"><span data-stu-id="a3e68-235">This parameter was introduced in PowerShell 3.0.</span></span>

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

### <span data-ttu-id="a3e68-236">-Waarde</span><span class="sxs-lookup"><span data-stu-id="a3e68-236">-Value</span></span>

<span data-ttu-id="a3e68-237">Hiermee geeft u de inhoud moet worden toegevoegd.</span><span class="sxs-lookup"><span data-stu-id="a3e68-237">Specifies the content to be added.</span></span> <span data-ttu-id="a3e68-238">Typ een teken reeks tussen aanhalings tekens, zoals **deze gegevens zijn alleen voor intern gebruik**, of geef een object op dat inhoud bevat, zoals het **DateTime** -object dat `Get-Date` genereert.</span><span class="sxs-lookup"><span data-stu-id="a3e68-238">Type a quoted string, such as **This data is for internal use only**, or specify an object that contains content, such as the **DateTime** object that `Get-Date` generates.</span></span>

<span data-ttu-id="a3e68-239">U kunt de inhoud van een bestand niet opgeven door het bijbehorende pad te typen, omdat het pad alleen een teken reeks is.</span><span class="sxs-lookup"><span data-stu-id="a3e68-239">You cannot specify the contents of a file by typing its path, because the path is just a string.</span></span>
<span data-ttu-id="a3e68-240">U kunt een `Get-Content` opdracht gebruiken om de inhoud op te halen en door te geven aan de **waarde** -para meter.</span><span class="sxs-lookup"><span data-stu-id="a3e68-240">You can use a `Get-Content` command to get the content and pass it to the **Value** parameter.</span></span>

```yaml
Type: System.Object[]
Parameter Sets: (All)
Aliases:

Required: True
Position: 1
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="a3e68-241">-Confirm</span><span class="sxs-lookup"><span data-stu-id="a3e68-241">-Confirm</span></span>

<span data-ttu-id="a3e68-242">Hiermee wordt u gevraagd om bevestiging voordat u de cmdlet uitvoert.</span><span class="sxs-lookup"><span data-stu-id="a3e68-242">Prompts you for confirmation before running the cmdlet.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: cf

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="a3e68-243">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="a3e68-243">-WhatIf</span></span>

<span data-ttu-id="a3e68-244">Hiermee wordt weergegeven wat er zou gebeuren als u de cmdlet uitvoert.</span><span class="sxs-lookup"><span data-stu-id="a3e68-244">Shows what would happen if the cmdlet runs.</span></span> <span data-ttu-id="a3e68-245">De cmdlet wordt niet uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="a3e68-245">The cmdlet is not run.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: wi

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="a3e68-246">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="a3e68-246">CommonParameters</span></span>
<span data-ttu-id="a3e68-247">Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="a3e68-247">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="a3e68-248">Zie [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="a3e68-248">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="a3e68-249">INVOER</span><span class="sxs-lookup"><span data-stu-id="a3e68-249">INPUTS</span></span>

### <span data-ttu-id="a3e68-250">System. object, System. Management. Automation. PSCredential</span><span class="sxs-lookup"><span data-stu-id="a3e68-250">System.Object, System.Management.Automation.PSCredential</span></span>

<span data-ttu-id="a3e68-251">U kunt waarden, paden of referenties door sluizen naar `Set-Content` .</span><span class="sxs-lookup"><span data-stu-id="a3e68-251">You can pipe values, paths, or credentials to `Set-Content`.</span></span>

## <span data-ttu-id="a3e68-252">UITVOER</span><span class="sxs-lookup"><span data-stu-id="a3e68-252">OUTPUTS</span></span>

### <span data-ttu-id="a3e68-253">Geen of System. String</span><span class="sxs-lookup"><span data-stu-id="a3e68-253">None or System.String</span></span>

<span data-ttu-id="a3e68-254">Wanneer u de para meter **PassThru** gebruikt, `Add-Content` genereert een **System. String** -object dat de inhoud vertegenwoordigt.</span><span class="sxs-lookup"><span data-stu-id="a3e68-254">When you use the **PassThru** parameter, `Add-Content` generates a **System.String** object that represents the content.</span></span> <span data-ttu-id="a3e68-255">Anders wordt met deze cmdlet geen uitvoer gegenereerd.</span><span class="sxs-lookup"><span data-stu-id="a3e68-255">Otherwise, this cmdlet does not generate any output.</span></span>

## <span data-ttu-id="a3e68-256">OPMERKINGEN</span><span class="sxs-lookup"><span data-stu-id="a3e68-256">NOTES</span></span>

- <span data-ttu-id="a3e68-257">Wanneer u een object pipet naar `Add-Content` , wordt het object geconverteerd naar een teken reeks voordat het aan het item wordt toegevoegd.</span><span class="sxs-lookup"><span data-stu-id="a3e68-257">When you pipe an object to `Add-Content`, the object is converted to a string before it is added to the item.</span></span> <span data-ttu-id="a3e68-258">Het object type bepaalt de teken reeks notatie, maar de notatie kan afwijken van de standaard weergave van het object.</span><span class="sxs-lookup"><span data-stu-id="a3e68-258">The object type determines the string format, but the format might be different than the default display of the object.</span></span> <span data-ttu-id="a3e68-259">Als u de teken reeks indeling wilt beheren, gebruikt u de opmaak parameters van de verzenden-cmdlet.</span><span class="sxs-lookup"><span data-stu-id="a3e68-259">To control the string format, use the formatting parameters of the sending cmdlet.</span></span>
- <span data-ttu-id="a3e68-260">U kunt ook verwijzen naar `Add-Content` de ingebouwde alias `ac` .</span><span class="sxs-lookup"><span data-stu-id="a3e68-260">You can also refer to `Add-Content` by its built-in alias, `ac`.</span></span> <span data-ttu-id="a3e68-261">Zie [about_Aliases](../Microsoft.PowerShell.Core/About/about_Aliases.md)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="a3e68-261">For more information, see [about_Aliases](../Microsoft.PowerShell.Core/About/about_Aliases.md).</span></span>
- <span data-ttu-id="a3e68-262">De `Add-Content` cmdlet is ontworpen om te werken met de gegevens die door elke provider worden weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="a3e68-262">The `Add-Content` cmdlet is designed to work with the data exposed by any provider.</span></span> <span data-ttu-id="a3e68-263">Als u een lijst wilt weer geven van de providers die beschikbaar zijn in uw sessie, typt u `Get-PSProvider` .</span><span class="sxs-lookup"><span data-stu-id="a3e68-263">To list the providers available in your session, type `Get-PSProvider`.</span></span> <span data-ttu-id="a3e68-264">Zie [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="a3e68-264">For more information, see [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md).</span></span>

## <span data-ttu-id="a3e68-265">GERELATEERDE KOPPELINGEN</span><span class="sxs-lookup"><span data-stu-id="a3e68-265">RELATED LINKS</span></span>

[<span data-ttu-id="a3e68-266">about_Aliases</span><span class="sxs-lookup"><span data-stu-id="a3e68-266">about_Aliases</span></span>](../Microsoft.PowerShell.Core/About/about_Aliases.md)

[<span data-ttu-id="a3e68-267">about_Providers</span><span class="sxs-lookup"><span data-stu-id="a3e68-267">about_Providers</span></span>](../Microsoft.PowerShell.Core/About/about_Providers.md)

[<span data-ttu-id="a3e68-268">Wissen-inhoud</span><span class="sxs-lookup"><span data-stu-id="a3e68-268">Clear-Content</span></span>](Clear-Content.md)

[<span data-ttu-id="a3e68-269">Get-Content</span><span class="sxs-lookup"><span data-stu-id="a3e68-269">Get-Content</span></span>](Get-Content.md)

[<span data-ttu-id="a3e68-270">Get-item</span><span class="sxs-lookup"><span data-stu-id="a3e68-270">Get-Item</span></span>](Get-Item.md)

[<span data-ttu-id="a3e68-271">Nieuw-item</span><span class="sxs-lookup"><span data-stu-id="a3e68-271">New-Item</span></span>](New-Item.md)

[<span data-ttu-id="a3e68-272">Set-Content</span><span class="sxs-lookup"><span data-stu-id="a3e68-272">Set-Content</span></span>](Set-Content.md)

