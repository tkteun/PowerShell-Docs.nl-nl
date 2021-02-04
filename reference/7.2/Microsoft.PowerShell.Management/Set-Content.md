---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 12/18/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/set-content?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Set-Content
ms.openlocfilehash: d85e0219c325de998c5874224a33ac4263b787a3
ms.sourcegitcommit: bf07cffb2a66dec94bf3576e197090f958701f18
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 12/19/2020
ms.locfileid: "97692963"
---
# <span data-ttu-id="2e676-102">Set-Content</span><span class="sxs-lookup"><span data-stu-id="2e676-102">Set-Content</span></span>

## <span data-ttu-id="2e676-103">SAMENVATTING</span><span class="sxs-lookup"><span data-stu-id="2e676-103">SYNOPSIS</span></span>
<span data-ttu-id="2e676-104">Schrijft nieuwe inhoud of vervangt bestaande inhoud in een bestand.</span><span class="sxs-lookup"><span data-stu-id="2e676-104">Writes new content or replaces existing content in a file.</span></span>

## <span data-ttu-id="2e676-105">SYNTAXIS</span><span class="sxs-lookup"><span data-stu-id="2e676-105">SYNTAX</span></span>

### <span data-ttu-id="2e676-106">Pad (standaard)</span><span class="sxs-lookup"><span data-stu-id="2e676-106">Path (Default)</span></span>

```
Set-Content [-Path] <string[]> [-Value] <Object[]> [-PassThru] [-Filter <string>]
 [-Include <string[]>] [-Exclude <string[]>] [-Force] [-Credential <pscredential>]
 [-WhatIf] [-Confirm] [-NoNewline] [-Encoding <Encoding>] [-AsByteStream] [-Stream <string>]
 [<CommonParameters>]
```

### <span data-ttu-id="2e676-107">LiteralPath</span><span class="sxs-lookup"><span data-stu-id="2e676-107">LiteralPath</span></span>

```
Set-Content [-Value] <Object[]> -LiteralPath <string[]> [-PassThru] [-Filter <string>]
 [-Include <string[]>] [-Exclude <string[]>] [-Force] [-Credential <pscredential>]
 [-WhatIf] [-Confirm] [-NoNewline] [-Encoding <Encoding>] [-AsByteStream] [-Stream <string>]
 [<CommonParameters>]
```

## <span data-ttu-id="2e676-108">BESCHRIJVING</span><span class="sxs-lookup"><span data-stu-id="2e676-108">DESCRIPTION</span></span>

<span data-ttu-id="2e676-109">`Set-Content` is een cmdlet voor het verwerken van teken reeksen waarmee nieuwe inhoud wordt geschreven of de inhoud in een bestand wordt vervangen.</span><span class="sxs-lookup"><span data-stu-id="2e676-109">`Set-Content` is a string-processing cmdlet that writes new content or replaces the content in a file.</span></span> <span data-ttu-id="2e676-110">`Set-Content` vervangt de bestaande inhoud en wijkt af van de `Add-Content` cmdlet waarmee inhoud wordt toegevoegd aan een bestand.</span><span class="sxs-lookup"><span data-stu-id="2e676-110">`Set-Content` replaces the existing content and differs from the `Add-Content` cmdlet that appends content to a file.</span></span> <span data-ttu-id="2e676-111">Als u inhoud wilt verzenden naar, `Set-Content` kunt u de para meter **Value** gebruiken op de opdracht regel of inhoud verzenden via de pijp lijn.</span><span class="sxs-lookup"><span data-stu-id="2e676-111">To send content to `Set-Content` you can use the **Value** parameter on the command line or send content through the pipeline.</span></span>

<span data-ttu-id="2e676-112">Zie [Nieuw-item](New-Item.md)als u bestanden of mappen wilt maken voor de volgende voor beelden.</span><span class="sxs-lookup"><span data-stu-id="2e676-112">If you need to create files or directories for the following examples, see [New-Item](New-Item.md).</span></span>

## <span data-ttu-id="2e676-113">VOORBEELDEN</span><span class="sxs-lookup"><span data-stu-id="2e676-113">EXAMPLES</span></span>

### <span data-ttu-id="2e676-114">Voor beeld 1: de inhoud van meerdere bestanden in een map vervangen</span><span class="sxs-lookup"><span data-stu-id="2e676-114">Example 1: Replace the contents of multiple files in a directory</span></span>

<span data-ttu-id="2e676-115">In dit voor beeld wordt de inhoud voor meerdere bestanden in de huidige map vervangen.</span><span class="sxs-lookup"><span data-stu-id="2e676-115">This example replaces the content for multiple files in the current directory.</span></span>

```powershell
Get-ChildItem -Path .\Test*.txt
```

```Output
Test1.txt
Test2.txt
Test3.txt
```

```powershell
Set-Content -Path .\Test*.txt -Value 'Hello, World'
Get-Content -Path .\Test*.txt
```

```Output
Hello, World
Hello, World
Hello, World
```

<span data-ttu-id="2e676-116">De `Get-ChildItem` cmdlet gebruikt de para meter **Path** om de **txt** -bestanden weer te geven die beginnen met `Test*` in de huidige map.</span><span class="sxs-lookup"><span data-stu-id="2e676-116">The `Get-ChildItem` cmdlet uses the **Path** parameter to list **.txt** files that begin with `Test*` in the current directory.</span></span> <span data-ttu-id="2e676-117">De `Set-Content` cmdlet gebruikt de para meter **Path** om de bestanden op te geven `Test*.txt` .</span><span class="sxs-lookup"><span data-stu-id="2e676-117">The `Set-Content` cmdlet uses the **Path** parameter to specify the `Test*.txt` files.</span></span> <span data-ttu-id="2e676-118">De **waarde** para meter geeft de teken reeks **Hello, World** waarmee de bestaande inhoud in elk bestand wordt vervangen.</span><span class="sxs-lookup"><span data-stu-id="2e676-118">The **Value** parameter provides the text string **Hello, World** that replaces the existing content in each file.</span></span> <span data-ttu-id="2e676-119">Met de `Get-Content` cmdlet wordt de para meter **Path** gebruikt om de bestanden op te geven `Test*.txt` en wordt de inhoud van elk bestand in de Power shell-console weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="2e676-119">The `Get-Content` cmdlet uses the **Path** parameter to specify the `Test*.txt` files and displays each file's content in the PowerShell console.</span></span>

### <span data-ttu-id="2e676-120">Voor beeld 2: een nieuw bestand maken en inhoud schrijven</span><span class="sxs-lookup"><span data-stu-id="2e676-120">Example 2: Create a new file and write content</span></span>

<span data-ttu-id="2e676-121">In dit voor beeld wordt een nieuw bestand gemaakt en worden de huidige datum en tijd naar het bestand geschreven.</span><span class="sxs-lookup"><span data-stu-id="2e676-121">This example creates a new file and writes the current date and time to the file.</span></span>

```powershell
Set-Content -Path .\DateTime.txt -Value (Get-Date)
Get-Content -Path .\DateTime.txt
```

```Output
1/30/2019 09:55:08
```

<span data-ttu-id="2e676-122">`Set-Content` maakt gebruik van de para meters **pad** en **waarde** voor het maken van een nieuw bestand met de naam **DateTime.txt** in de huidige map.</span><span class="sxs-lookup"><span data-stu-id="2e676-122">`Set-Content` uses the **Path** and **Value** parameters to create a new file named **DateTime.txt** in the current directory.</span></span> <span data-ttu-id="2e676-123">De **waarde** para meter wordt gebruikt `Get-Date` om de huidige datum en tijd op te halen.</span><span class="sxs-lookup"><span data-stu-id="2e676-123">The **Value** parameter uses `Get-Date` to get the current date and time.</span></span>
<span data-ttu-id="2e676-124">`Set-Content` schrijft het **DateTime** -object naar het bestand als een teken reeks.</span><span class="sxs-lookup"><span data-stu-id="2e676-124">`Set-Content` writes the **DateTime** object to the file as a string.</span></span> <span data-ttu-id="2e676-125">De `Get-Content` cmdlet gebruikt de para meter **Path** om de inhoud van **DateTime.txt** in de Power shell-console weer te geven.</span><span class="sxs-lookup"><span data-stu-id="2e676-125">The `Get-Content` cmdlet uses the **Path** parameter to display the content of **DateTime.txt** in the PowerShell console.</span></span>

### <span data-ttu-id="2e676-126">Voor beeld 3: tekst in een bestand vervangen</span><span class="sxs-lookup"><span data-stu-id="2e676-126">Example 3: Replace text in a file</span></span>

<span data-ttu-id="2e676-127">Met deze opdracht worden alle exemplaren van Word in een bestaand bestand vervangen.</span><span class="sxs-lookup"><span data-stu-id="2e676-127">This command replaces all instances of word within an existing file.</span></span>

```powershell
Get-Content -Path .\Notice.txt
```

```Output
Warning
Replace Warning with a new word.
The word Warning was replaced.
```

```powershell
(Get-Content -Path .\Notice.txt) |
    ForEach-Object {$_ -Replace 'Warning', 'Caution'} |
        Set-Content -Path .\Notice.txt
Get-Content -Path .\Notice.txt
```

```Output
Caution
Replace Caution with a new word.
The word Caution was replaced.
```

<span data-ttu-id="2e676-128">De `Get-Content` cmdlet gebruikt de para meter **Path** om het **Notice.txt** bestand in de huidige map op te geven.</span><span class="sxs-lookup"><span data-stu-id="2e676-128">The `Get-Content` cmdlet uses the **Path** parameter to specify the **Notice.txt** file in the current directory.</span></span> <span data-ttu-id="2e676-129">De `Get-Content` opdracht wordt verpakt met haakjes zodat de opdracht is voltooid voordat de pijp lijn wordt verzonden.</span><span class="sxs-lookup"><span data-stu-id="2e676-129">The `Get-Content` command is wrapped with parentheses so that the command finishes before being sent down the pipeline.</span></span>

<span data-ttu-id="2e676-130">De inhoud van het **Notice.txt** -bestand wordt naar de-cmdlet verzonden via de pijp lijn `ForEach-Object` .</span><span class="sxs-lookup"><span data-stu-id="2e676-130">The contents of the **Notice.txt** file are sent down the pipeline to the `ForEach-Object` cmdlet.</span></span>
<span data-ttu-id="2e676-131">`ForEach-Object`maakt gebruik van de automatische variabele `$_` en vervangt elke **waarschuwing** telkens als dat zo is.</span><span class="sxs-lookup"><span data-stu-id="2e676-131">`ForEach-Object` uses the automatic variable `$_` and replaces each occurrence of **Warning** with **Caution**.</span></span> <span data-ttu-id="2e676-132">De objecten worden naar de-cmdlet verzonden via de pijp lijn `Set-Content` .</span><span class="sxs-lookup"><span data-stu-id="2e676-132">The objects are sent down the pipeline to the `Set-Content` cmdlet.</span></span> <span data-ttu-id="2e676-133">`Set-Content` gebruikt de para meter **Path** om het **Notice.txt** -bestand op te geven en de bijgewerkte inhoud naar het bestand te schrijven.</span><span class="sxs-lookup"><span data-stu-id="2e676-133">`Set-Content` uses the **Path** parameter to specify the **Notice.txt** file and writes the updated content to the file.</span></span>

<span data-ttu-id="2e676-134">Met de laatste `Get-Content` cmdlet wordt de bijgewerkte bestands inhoud weer gegeven in de Power shell-console.</span><span class="sxs-lookup"><span data-stu-id="2e676-134">The last `Get-Content` cmdlet displays the updated file content in the PowerShell console.</span></span>

### <span data-ttu-id="2e676-135">Voor beeld 4: filters gebruiken met Set-Content</span><span class="sxs-lookup"><span data-stu-id="2e676-135">Example 4: Use Filters with Set-Content</span></span>

<span data-ttu-id="2e676-136">U kunt een filter opgeven voor de `Set-Content` cmdlet.</span><span class="sxs-lookup"><span data-stu-id="2e676-136">You can specify a filter to the `Set-Content` cmdlet.</span></span> <span data-ttu-id="2e676-137">Wanneer u filters gebruikt om de para meter **Path** te kwalificeren, moet u een asterisk ( `*` ) toevoegen om de inhoud van het pad aan te geven.</span><span class="sxs-lookup"><span data-stu-id="2e676-137">When using filters to qualify the **Path** parameter, you need to include a trailing asterisk (`*`) to indicate the contents of the path.</span></span>

<span data-ttu-id="2e676-138">Met de volgende opdracht stelt u de inhoud alle `*.txt` bestanden in de `C:\Temp` map in op de **waarde** empty.</span><span class="sxs-lookup"><span data-stu-id="2e676-138">The following command set the content all `*.txt` files in the `C:\Temp` directory to the **Value** empty.</span></span>

```powershell
Set-Content -Path C:\Temp\* -Filter *.txt -Value "Empty"
```

## <span data-ttu-id="2e676-139">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="2e676-139">PARAMETERS</span></span>

### <span data-ttu-id="2e676-140">-AsByteStream</span><span class="sxs-lookup"><span data-stu-id="2e676-140">-AsByteStream</span></span>

<span data-ttu-id="2e676-141">Hiermee geeft u op dat de inhoud moet worden gelezen als een byte stroom.</span><span class="sxs-lookup"><span data-stu-id="2e676-141">Specifies that the content should be read as a stream of bytes.</span></span> <span data-ttu-id="2e676-142">Deze para meter is geïntroduceerd in Power shell 6,0.</span><span class="sxs-lookup"><span data-stu-id="2e676-142">This parameter was introduced in PowerShell 6.0.</span></span>

<span data-ttu-id="2e676-143">Er treedt een waarschuwing op wanneer u de para meter **AsByteStream** gebruikt met de para meter **Encoding** .</span><span class="sxs-lookup"><span data-stu-id="2e676-143">A warning occurs when you use the **AsByteStream** parameter with the **Encoding** parameter.</span></span> <span data-ttu-id="2e676-144">De para meter **AsByteStream** negeert elke code ring en de uitvoer wordt geretourneerd als een byte stroom.</span><span class="sxs-lookup"><span data-stu-id="2e676-144">The **AsByteStream** parameter ignores any encoding and the output is returned as a stream of bytes.</span></span>

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

### <span data-ttu-id="2e676-145">-Credential</span><span class="sxs-lookup"><span data-stu-id="2e676-145">-Credential</span></span>

> [!NOTE]
> <span data-ttu-id="2e676-146">Deze para meter wordt niet ondersteund door providers die zijn geïnstalleerd met Power shell.</span><span class="sxs-lookup"><span data-stu-id="2e676-146">This parameter is not supported by any providers installed with PowerShell.</span></span>
> <span data-ttu-id="2e676-147">Gebruik [invoke-Command](../Microsoft.PowerShell.Core/Invoke-Command.md)om een andere gebruiker te imiteren of uw referenties te verhogen wanneer u deze cmdlet uitvoert.</span><span class="sxs-lookup"><span data-stu-id="2e676-147">To impersonate another user, or elevate your credentials when running this cmdlet, use [Invoke-Command](../Microsoft.PowerShell.Core/Invoke-Command.md).</span></span>

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

### <span data-ttu-id="2e676-148">-Encoding</span><span class="sxs-lookup"><span data-stu-id="2e676-148">-Encoding</span></span>

<span data-ttu-id="2e676-149">Hiermee geeft u het type code ring voor het doel bestand op.</span><span class="sxs-lookup"><span data-stu-id="2e676-149">Specifies the type of encoding for the target file.</span></span> <span data-ttu-id="2e676-150">De standaardwaarde is `utf8NoBOM`.</span><span class="sxs-lookup"><span data-stu-id="2e676-150">The default value is `utf8NoBOM`.</span></span>

<span data-ttu-id="2e676-151">Encoding is een dynamische para meter waaraan de File System Provider toevoegt `Set-Content` .</span><span class="sxs-lookup"><span data-stu-id="2e676-151">Encoding is a dynamic parameter that the FileSystem provider adds to `Set-Content`.</span></span> <span data-ttu-id="2e676-152">Deze para meter werkt alleen op stations met een bestands systeem.</span><span class="sxs-lookup"><span data-stu-id="2e676-152">This parameter works only in file system drives.</span></span>

<span data-ttu-id="2e676-153">De acceptabele waarden voor deze para meter zijn als volgt:</span><span class="sxs-lookup"><span data-stu-id="2e676-153">The acceptable values for this parameter are as follows:</span></span>

- <span data-ttu-id="2e676-154">`ascii`: Gebruikt de code ring voor de ASCII-tekenset (7-bits).</span><span class="sxs-lookup"><span data-stu-id="2e676-154">`ascii`: Uses the encoding for the ASCII (7-bit) character set.</span></span>
- <span data-ttu-id="2e676-155">`bigendianunicode`: Wordt gecodeerd in UTF-16-indeling met behulp van de byte volgorde big endian.</span><span class="sxs-lookup"><span data-stu-id="2e676-155">`bigendianunicode`: Encodes in UTF-16 format using the big-endian byte order.</span></span>
- <span data-ttu-id="2e676-156">`bigendianutf32`: Codeert in UTF-32-indeling met behulp van de byte volgorde big endian.</span><span class="sxs-lookup"><span data-stu-id="2e676-156">`bigendianutf32`: Encodes in UTF-32 format using the big-endian byte order.</span></span>
- <span data-ttu-id="2e676-157">`oem`: Maakt gebruik van de standaard codering voor MS-DOS-en console Programma's.</span><span class="sxs-lookup"><span data-stu-id="2e676-157">`oem`: Uses the default encoding for MS-DOS and console programs.</span></span>
- <span data-ttu-id="2e676-158">`unicode`: Wordt gecodeerd in UTF-16-indeling met behulp van de byte volgorde little endian.</span><span class="sxs-lookup"><span data-stu-id="2e676-158">`unicode`: Encodes in UTF-16 format using the little-endian byte order.</span></span>
- <span data-ttu-id="2e676-159">`utf7`: Wordt gecodeerd in de indeling UTF-7.</span><span class="sxs-lookup"><span data-stu-id="2e676-159">`utf7`: Encodes in UTF-7 format.</span></span>
- <span data-ttu-id="2e676-160">`utf8`: Wordt gecodeerd in UTF-8-indeling.</span><span class="sxs-lookup"><span data-stu-id="2e676-160">`utf8`: Encodes in UTF-8 format.</span></span>
- <span data-ttu-id="2e676-161">`utf8BOM`: Code ring in UTF-8-indeling met byte order Mark (BOM)</span><span class="sxs-lookup"><span data-stu-id="2e676-161">`utf8BOM`: Encodes in UTF-8 format with Byte Order Mark (BOM)</span></span>
- <span data-ttu-id="2e676-162">`utf8NoBOM`: Code ring in UTF-8-indeling zonder byte order Mark (BOM)</span><span class="sxs-lookup"><span data-stu-id="2e676-162">`utf8NoBOM`: Encodes in UTF-8 format without Byte Order Mark (BOM)</span></span>
- <span data-ttu-id="2e676-163">`utf32`: Gecodeerd in UTF-32-indeling.</span><span class="sxs-lookup"><span data-stu-id="2e676-163">`utf32`: Encodes in UTF-32 format.</span></span>

<span data-ttu-id="2e676-164">Vanaf Power shell 6,2 kunnen met de para meter **Encoding** ook numerieke id's van geregistreerde code pagina's (zoals `-Encoding 1251` ) of teken reeks namen van geregistreerde code pagina's (zoals) worden toegestaan `-Encoding "windows-1251"` .</span><span class="sxs-lookup"><span data-stu-id="2e676-164">Beginning with PowerShell 6.2, the **Encoding** parameter also allows numeric IDs of registered code pages (like `-Encoding 1251`) or string names of registered code pages (like `-Encoding "windows-1251"`).</span></span> <span data-ttu-id="2e676-165">Zie de .NET-documentatie voor [code ring. code tabel](/dotnet/api/system.text.encoding.codepage?view=netcore-2.2)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="2e676-165">For more information, see the .NET documentation for [Encoding.CodePage](/dotnet/api/system.text.encoding.codepage?view=netcore-2.2).</span></span>

> [!NOTE]
> <span data-ttu-id="2e676-166">**UTF-7** _ wordt niet meer aanbevolen om te gebruiken.</span><span class="sxs-lookup"><span data-stu-id="2e676-166">**UTF-7** _ is no longer recommended to use.</span></span> <span data-ttu-id="2e676-167">In Power shell 7,1 wordt een waarschuwing geschreven als u `utf7` de para meter _ *Encoding*\* opgeeft.</span><span class="sxs-lookup"><span data-stu-id="2e676-167">In PowerShell 7.1, a warning is written if you specify `utf7` for the _ *Encoding*\* parameter.</span></span>

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

### <span data-ttu-id="2e676-168">-Uitsluiten</span><span class="sxs-lookup"><span data-stu-id="2e676-168">-Exclude</span></span>

<span data-ttu-id="2e676-169">Hiermee geeft u als een teken reeks matrix een item of items die met deze cmdlet worden uitgesloten in de bewerking.</span><span class="sxs-lookup"><span data-stu-id="2e676-169">Specifies, as a string array, an item or items that this cmdlet excludes in the operation.</span></span> <span data-ttu-id="2e676-170">De waarde van deze para meter komt in aanmerking voor de para meter **Path** .</span><span class="sxs-lookup"><span data-stu-id="2e676-170">The value of this parameter qualifies the **Path** parameter.</span></span> <span data-ttu-id="2e676-171">Voer een element of patroon van een pad in, zoals `*.txt` .</span><span class="sxs-lookup"><span data-stu-id="2e676-171">Enter a path element or pattern, such as `*.txt`.</span></span> <span data-ttu-id="2e676-172">Joker tekens zijn toegestaan.</span><span class="sxs-lookup"><span data-stu-id="2e676-172">Wildcard characters are permitted.</span></span> <span data-ttu-id="2e676-173">De **exclude** -para meter is alleen effectief wanneer de inhoud van een item wordt opgenomen, zoals `C:\Windows\*` , waarbij het Joker teken de inhoud van de `C:\Windows` map bevat.</span><span class="sxs-lookup"><span data-stu-id="2e676-173">The **Exclude** parameter is effective only when the command includes the contents of an item, such as `C:\Windows\*`, where the wildcard character specifies the contents of the `C:\Windows` directory.</span></span>

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

### <span data-ttu-id="2e676-174">-Filter</span><span class="sxs-lookup"><span data-stu-id="2e676-174">-Filter</span></span>

<span data-ttu-id="2e676-175">Hiermee geeft u een filter op om de para meter **Path** te kwalificeren.</span><span class="sxs-lookup"><span data-stu-id="2e676-175">Specifies a filter to qualify the **Path** parameter.</span></span> <span data-ttu-id="2e676-176">De [File System](../Microsoft.PowerShell.Core/About/about_FileSystem_Provider.md) -provider is de enige geïnstalleerde Power shell-provider die het gebruik van filters ondersteunt.</span><span class="sxs-lookup"><span data-stu-id="2e676-176">The [FileSystem](../Microsoft.PowerShell.Core/About/about_FileSystem_Provider.md) provider is the only installed PowerShell provider that supports the use of filters.</span></span> <span data-ttu-id="2e676-177">U kunt de syntaxis voor de filter taal van het **Bestands systeem** in [about_Wildcards](../Microsoft.PowerShell.Core/About/about_Wildcards.md)vinden.</span><span class="sxs-lookup"><span data-stu-id="2e676-177">You can find the syntax for the **FileSystem** filter language in [about_Wildcards](../Microsoft.PowerShell.Core/About/about_Wildcards.md).</span></span>
<span data-ttu-id="2e676-178">Filters zijn efficiënter dan andere para meters, omdat deze door de provider worden toegepast wanneer de cmdlet de objecten ophaalt in plaats van dat Power shell de objecten heeft gefilterd nadat ze zijn opgehaald.</span><span class="sxs-lookup"><span data-stu-id="2e676-178">Filters are more efficient than other parameters, because the provider applies them when the cmdlet gets the objects rather than having PowerShell filter the objects after they are retrieved.</span></span>

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

### <span data-ttu-id="2e676-179">-Force</span><span class="sxs-lookup"><span data-stu-id="2e676-179">-Force</span></span>

<span data-ttu-id="2e676-180">Hiermee wordt de cmdlet gedwongen de inhoud van een bestand in te stellen, zelfs als het bestand alleen-lezen is.</span><span class="sxs-lookup"><span data-stu-id="2e676-180">Forces the cmdlet to set the contents of a file, even if the file is read-only.</span></span> <span data-ttu-id="2e676-181">De implementatie varieert van provider tot provider.</span><span class="sxs-lookup"><span data-stu-id="2e676-181">Implementation varies from provider to provider.</span></span> <span data-ttu-id="2e676-182">Zie [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="2e676-182">For more information, see [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md).</span></span>
<span data-ttu-id="2e676-183">De para meter **Force** overschrijft geen beveiligings beperkingen.</span><span class="sxs-lookup"><span data-stu-id="2e676-183">The **Force** parameter does not override security restrictions.</span></span>

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

### <span data-ttu-id="2e676-184">-Include</span><span class="sxs-lookup"><span data-stu-id="2e676-184">-Include</span></span>

<span data-ttu-id="2e676-185">Hiermee wordt een teken reeks matrix opgegeven, een item of items die met deze cmdlet in de bewerking zijn opgenomen.</span><span class="sxs-lookup"><span data-stu-id="2e676-185">Specifies, as a string array, an item or items that this cmdlet includes in the operation.</span></span> <span data-ttu-id="2e676-186">De waarde van deze para meter komt in aanmerking voor de para meter **Path** .</span><span class="sxs-lookup"><span data-stu-id="2e676-186">The value of this parameter qualifies the **Path** parameter.</span></span> <span data-ttu-id="2e676-187">Voer een element of patroon van een pad in, zoals `"*.txt"` .</span><span class="sxs-lookup"><span data-stu-id="2e676-187">Enter a path element or pattern, such as `"*.txt"`.</span></span> <span data-ttu-id="2e676-188">Joker tekens zijn toegestaan.</span><span class="sxs-lookup"><span data-stu-id="2e676-188">Wildcard characters are permitted.</span></span> <span data-ttu-id="2e676-189">De para meter **include** is alleen effectief wanneer de inhoud van een item wordt opgenomen, zoals `C:\Windows\*` , waarbij het Joker teken de inhoud van de `C:\Windows` map bevat.</span><span class="sxs-lookup"><span data-stu-id="2e676-189">The **Include** parameter is effective only when the command includes the contents of an item, such as `C:\Windows\*`, where the wildcard character specifies the contents of the `C:\Windows` directory.</span></span>

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

### <span data-ttu-id="2e676-190">-LiteralPath</span><span class="sxs-lookup"><span data-stu-id="2e676-190">-LiteralPath</span></span>

<span data-ttu-id="2e676-191">Hiermee geeft u een pad naar een of meer locaties.</span><span class="sxs-lookup"><span data-stu-id="2e676-191">Specifies a path to one or more locations.</span></span> <span data-ttu-id="2e676-192">De waarde van **LiteralPath** wordt precies zo gebruikt als deze wordt getypt.</span><span class="sxs-lookup"><span data-stu-id="2e676-192">The value of **LiteralPath** is used exactly as it is typed.</span></span> <span data-ttu-id="2e676-193">Geen tekens worden geïnterpreteerd als joker tekens.</span><span class="sxs-lookup"><span data-stu-id="2e676-193">No characters are interpreted as wildcards.</span></span> <span data-ttu-id="2e676-194">Als het pad escape tekens bevat, plaatst u het tussen enkele aanhalings tekens.</span><span class="sxs-lookup"><span data-stu-id="2e676-194">If the path includes escape characters, enclose it in single quotation marks.</span></span> <span data-ttu-id="2e676-195">Enkele aanhalings tekens geven aan dat Power shell geen karakters interpreteert als escape reeksen.</span><span class="sxs-lookup"><span data-stu-id="2e676-195">Single quotation marks tell PowerShell not to interpret any characters as escape sequences.</span></span>

<span data-ttu-id="2e676-196">Zie [about_Quoting_Rules](../Microsoft.Powershell.Core/About/about_Quoting_Rules.md)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="2e676-196">For more information, see [about_Quoting_Rules](../Microsoft.Powershell.Core/About/about_Quoting_Rules.md).</span></span>

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

### <span data-ttu-id="2e676-197">-Nieuwe regel</span><span class="sxs-lookup"><span data-stu-id="2e676-197">-NoNewline</span></span>

<span data-ttu-id="2e676-198">De teken reeks representaties van de invoer objecten worden samengevoegd om de uitvoer te vormen.</span><span class="sxs-lookup"><span data-stu-id="2e676-198">The string representations of the input objects are concatenated to form the output.</span></span> <span data-ttu-id="2e676-199">Er worden geen spaties of nieuwe regels tussen de uitvoer teken reeksen ingevoegd.</span><span class="sxs-lookup"><span data-stu-id="2e676-199">No spaces or newlines are inserted between the output strings.</span></span> <span data-ttu-id="2e676-200">Er wordt geen nieuwe regel toegevoegd na de laatste uitvoer teken reeks.</span><span class="sxs-lookup"><span data-stu-id="2e676-200">No newline is added after the last output string.</span></span>

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

### <span data-ttu-id="2e676-201">-PassThru</span><span class="sxs-lookup"><span data-stu-id="2e676-201">-PassThru</span></span>

<span data-ttu-id="2e676-202">Retourneert een object dat de inhoud vertegenwoordigt.</span><span class="sxs-lookup"><span data-stu-id="2e676-202">Returns an object that represents the content.</span></span> <span data-ttu-id="2e676-203">Deze cmdlet genereert standaard geen uitvoer.</span><span class="sxs-lookup"><span data-stu-id="2e676-203">By default, this cmdlet does not generate any output.</span></span>

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

### <span data-ttu-id="2e676-204">-Path</span><span class="sxs-lookup"><span data-stu-id="2e676-204">-Path</span></span>

<span data-ttu-id="2e676-205">Hiermee geeft u het pad op van het item dat de inhoud ontvangt.</span><span class="sxs-lookup"><span data-stu-id="2e676-205">Specifies the path of the item that receives the content.</span></span>
<span data-ttu-id="2e676-206">Joker tekens zijn toegestaan.</span><span class="sxs-lookup"><span data-stu-id="2e676-206">Wildcard characters are permitted.</span></span>

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

### <span data-ttu-id="2e676-207">-Stream</span><span class="sxs-lookup"><span data-stu-id="2e676-207">-Stream</span></span>

> [!NOTE]
> <span data-ttu-id="2e676-208">Deze para meter is alleen beschikbaar in Windows.</span><span class="sxs-lookup"><span data-stu-id="2e676-208">This Parameter is only available on Windows.</span></span>

<span data-ttu-id="2e676-209">Hiermee geeft u een alternatieve gegevens stroom voor inhoud.</span><span class="sxs-lookup"><span data-stu-id="2e676-209">Specifies an alternative data stream for content.</span></span> <span data-ttu-id="2e676-210">Als de stroom niet bestaat, wordt deze gemaakt met deze cmdlet.</span><span class="sxs-lookup"><span data-stu-id="2e676-210">If the stream does not exist, this cmdlet creates it.</span></span> <span data-ttu-id="2e676-211">Joker tekens worden niet ondersteund.</span><span class="sxs-lookup"><span data-stu-id="2e676-211">Wildcard characters are not supported.</span></span>

<span data-ttu-id="2e676-212">**Stream** is een dynamische para meter waaraan de **File System** provider toevoegt `Set-Content` .</span><span class="sxs-lookup"><span data-stu-id="2e676-212">**Stream** is a dynamic parameter that the **FileSystem** provider adds to `Set-Content`.</span></span> <span data-ttu-id="2e676-213">Deze para meter werkt alleen op stations met een bestands systeem.</span><span class="sxs-lookup"><span data-stu-id="2e676-213">This parameter works only in file system drives.</span></span>

<span data-ttu-id="2e676-214">U kunt de `Set-Content` cmdlet gebruiken om de inhoud van een alternatieve gegevens stroom te maken of bij te werken, zoals `Zone.Identifier` .</span><span class="sxs-lookup"><span data-stu-id="2e676-214">You can use the `Set-Content` cmdlet to create or update the content of any alternate data stream, such as `Zone.Identifier`.</span></span> <span data-ttu-id="2e676-215">Dit wordt echter niet aangeraden als een manier om beveiligings controles te elimineren waarmee bestanden die worden gedownload van Internet, worden geblokkeerd.</span><span class="sxs-lookup"><span data-stu-id="2e676-215">However, we do not recommend this as a way to eliminate security checks that block files that are downloaded from the Internet.</span></span> <span data-ttu-id="2e676-216">Als u controleert of een gedownload bestand veilig is, gebruikt u de `Unblock-File` cmdlet.</span><span class="sxs-lookup"><span data-stu-id="2e676-216">If you verify that a downloaded file is safe, use the `Unblock-File` cmdlet.</span></span>

<span data-ttu-id="2e676-217">Deze para meter is geïntroduceerd in Power Shell 3,0.</span><span class="sxs-lookup"><span data-stu-id="2e676-217">This parameter was introduced in PowerShell 3.0.</span></span> <span data-ttu-id="2e676-218">Vanaf Power shell 7,2 `Set-Content` kan de inhoud van alternatieve gegevens stromen van mappen en bestanden instellen.</span><span class="sxs-lookup"><span data-stu-id="2e676-218">As of PowerShell 7.2, `Set-Content` can set the content of alternative data streams from directories as well as files.</span></span>

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

### <span data-ttu-id="2e676-219">-Waarde</span><span class="sxs-lookup"><span data-stu-id="2e676-219">-Value</span></span>

<span data-ttu-id="2e676-220">Hiermee geeft u de nieuwe inhoud voor het item.</span><span class="sxs-lookup"><span data-stu-id="2e676-220">Specifies the new content for the item.</span></span>

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

### <span data-ttu-id="2e676-221">-Confirm</span><span class="sxs-lookup"><span data-stu-id="2e676-221">-Confirm</span></span>

<span data-ttu-id="2e676-222">Hiermee wordt u gevraagd om bevestiging voordat u de cmdlet uitvoert.</span><span class="sxs-lookup"><span data-stu-id="2e676-222">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="2e676-223">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="2e676-223">-WhatIf</span></span>

<span data-ttu-id="2e676-224">Hiermee wordt weergegeven wat er zou gebeuren als u de cmdlet uitvoert.</span><span class="sxs-lookup"><span data-stu-id="2e676-224">Shows what would happen if the cmdlet runs.</span></span> <span data-ttu-id="2e676-225">De cmdlet wordt niet uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="2e676-225">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="2e676-226">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="2e676-226">CommonParameters</span></span>

<span data-ttu-id="2e676-227">Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="2e676-227">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="2e676-228">Zie [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="2e676-228">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="2e676-229">INVOER</span><span class="sxs-lookup"><span data-stu-id="2e676-229">INPUTS</span></span>

### <span data-ttu-id="2e676-230">System. object</span><span class="sxs-lookup"><span data-stu-id="2e676-230">System.Object</span></span>

<span data-ttu-id="2e676-231">U kunt een object dat de nieuwe waarde voor het item bevat, door sluizen naar `Set-Content` .</span><span class="sxs-lookup"><span data-stu-id="2e676-231">You can pipe an object that contains the new value for the item to `Set-Content`.</span></span>

## <span data-ttu-id="2e676-232">UITVOER</span><span class="sxs-lookup"><span data-stu-id="2e676-232">OUTPUTS</span></span>

### <span data-ttu-id="2e676-233">Geen of System. String</span><span class="sxs-lookup"><span data-stu-id="2e676-233">None or System.String</span></span>

<span data-ttu-id="2e676-234">Wanneer u de para meter **PassThru** gebruikt, `Set-Content` genereert een **System. String** -object dat de inhoud vertegenwoordigt.</span><span class="sxs-lookup"><span data-stu-id="2e676-234">When you use the **PassThru** parameter, `Set-Content` generates a **System.String** object that represents the content.</span></span> <span data-ttu-id="2e676-235">Anders wordt met deze cmdlet geen uitvoer gegenereerd.</span><span class="sxs-lookup"><span data-stu-id="2e676-235">Otherwise, this cmdlet does not generate any output.</span></span>

## <span data-ttu-id="2e676-236">OPMERKINGEN</span><span class="sxs-lookup"><span data-stu-id="2e676-236">NOTES</span></span>

- <span data-ttu-id="2e676-237">U kunt ook verwijzen naar `Set-Content` de ingebouwde alias `sc` .</span><span class="sxs-lookup"><span data-stu-id="2e676-237">You can also refer to `Set-Content` by its built-in alias, `sc`.</span></span>
  <span data-ttu-id="2e676-238">Zie [about_Aliases](../Microsoft.PowerShell.Core/About/about_Aliases.md)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="2e676-238">For more information, see [about_Aliases](../Microsoft.PowerShell.Core/About/about_Aliases.md).</span></span>
- <span data-ttu-id="2e676-239">`Set-Content` is ontworpen voor het verwerken van teken reeksen.</span><span class="sxs-lookup"><span data-stu-id="2e676-239">`Set-Content` is designed for string processing.</span></span> <span data-ttu-id="2e676-240">Als u niet-teken reeks objecten naar `Set-Content` een teken reeks in het pipet zet, wordt het object geconverteerd naar een String voordat het wordt geschreven.</span><span class="sxs-lookup"><span data-stu-id="2e676-240">If you pipe non-string objects to `Set-Content`, it converts the object to a string before writing it.</span></span> <span data-ttu-id="2e676-241">Als u objecten naar bestanden wilt schrijven, gebruikt u `Out-File` .</span><span class="sxs-lookup"><span data-stu-id="2e676-241">To write objects to files, use `Out-File`.</span></span>
- <span data-ttu-id="2e676-242">De `Set-Content` cmdlet is ontworpen om te werken met de gegevens die door elke provider worden weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="2e676-242">The `Set-Content` cmdlet is designed to work with the data exposed by any provider.</span></span> <span data-ttu-id="2e676-243">Als u een lijst wilt weer geven van de providers die beschikbaar zijn in uw sessie, typt u `Get-PsProvider` .</span><span class="sxs-lookup"><span data-stu-id="2e676-243">To list the providers available in your session, type `Get-PsProvider`.</span></span> <span data-ttu-id="2e676-244">Zie [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="2e676-244">For more information, see [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md).</span></span>

## <span data-ttu-id="2e676-245">GERELATEERDE KOPPELINGEN</span><span class="sxs-lookup"><span data-stu-id="2e676-245">RELATED LINKS</span></span>

[<span data-ttu-id="2e676-246">about_Aliases</span><span class="sxs-lookup"><span data-stu-id="2e676-246">about_Aliases</span></span>](../Microsoft.PowerShell.Core/About/about_Aliases.md)

[<span data-ttu-id="2e676-247">about_Automatic_Variables. MD</span><span class="sxs-lookup"><span data-stu-id="2e676-247">about_Automatic_Variables.md</span></span>](../Microsoft.PowerShell.Core/About/about_Automatic_Variables.md)

[<span data-ttu-id="2e676-248">about_Providers</span><span class="sxs-lookup"><span data-stu-id="2e676-248">about_Providers</span></span>](../Microsoft.PowerShell.Core/About/about_Providers.md)

[<span data-ttu-id="2e676-249">Add-content</span><span class="sxs-lookup"><span data-stu-id="2e676-249">Add-Content</span></span>](Add-Content.md)

[<span data-ttu-id="2e676-250">Wissen-inhoud</span><span class="sxs-lookup"><span data-stu-id="2e676-250">Clear-Content</span></span>](Clear-Content.md)

[<span data-ttu-id="2e676-251">Get-Child item</span><span class="sxs-lookup"><span data-stu-id="2e676-251">Get-ChildItem</span></span>](Get-ChildItem.md)

[<span data-ttu-id="2e676-252">Get-Content</span><span class="sxs-lookup"><span data-stu-id="2e676-252">Get-Content</span></span>](Get-Content.md)

[<span data-ttu-id="2e676-253">ForEach-object</span><span class="sxs-lookup"><span data-stu-id="2e676-253">ForEach-Object</span></span>](../Microsoft.PowerShell.Core/ForEach-Object.md)

[<span data-ttu-id="2e676-254">Nieuw-item</span><span class="sxs-lookup"><span data-stu-id="2e676-254">New-Item</span></span>](New-Item.md)
