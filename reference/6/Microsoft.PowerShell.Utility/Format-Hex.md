---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 01/17/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/format-hex?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Format-Hex
ms.openlocfilehash: 64275e72f8c21942179431b3aed4a17d328aa2e9
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/07/2020
ms.locfileid: "93251117"
---
# <span data-ttu-id="fc428-103">Format-Hex</span><span class="sxs-lookup"><span data-stu-id="fc428-103">Format-Hex</span></span>

## <span data-ttu-id="fc428-104">SAMENVATTING</span><span class="sxs-lookup"><span data-stu-id="fc428-104">SYNOPSIS</span></span>

<span data-ttu-id="fc428-105">Geeft een bestand of andere invoer weer als hexadecimale notatie.</span><span class="sxs-lookup"><span data-stu-id="fc428-105">Displays a file or other input as hexadecimal.</span></span>

## <span data-ttu-id="fc428-106">SYNTAXIS</span><span class="sxs-lookup"><span data-stu-id="fc428-106">SYNTAX</span></span>

### <span data-ttu-id="fc428-107">Pad (standaard)</span><span class="sxs-lookup"><span data-stu-id="fc428-107">Path (Default)</span></span>

```
Format-Hex [-Path] <string[]> [-Count <long>] [-Offset <long>] [<CommonParameters>]
```

### <span data-ttu-id="fc428-108">LiteralPath</span><span class="sxs-lookup"><span data-stu-id="fc428-108">LiteralPath</span></span>

```
Format-Hex -LiteralPath <string[]> [-Count <long>] [-Offset <long>] [<CommonParameters>]
```

### <span data-ttu-id="fc428-109">Input object</span><span class="sxs-lookup"><span data-stu-id="fc428-109">InputObject</span></span>

```
Format-Hex -InputObject <psobject> [-Encoding <Encoding>] [-Count <long>] [-Offset <long>] [-Raw] [<CommonParameters>]
```

## <span data-ttu-id="fc428-110">BESCHRIJVING</span><span class="sxs-lookup"><span data-stu-id="fc428-110">DESCRIPTION</span></span>

<span data-ttu-id="fc428-111">De `Format-Hex` cmdlet geeft een bestand of andere invoer weer als hexadecimale waarden.</span><span class="sxs-lookup"><span data-stu-id="fc428-111">The `Format-Hex` cmdlet displays a file or other input as hexadecimal values.</span></span> <span data-ttu-id="fc428-112">Als u de verschuiving van een teken van de uitvoer wilt bepalen, voegt u het nummer aan de linkerkant van de rij toe aan het getal boven aan de kolom voor dat teken.</span><span class="sxs-lookup"><span data-stu-id="fc428-112">To determine the offset of a character from the output, add the number at the leftmost of the row to the number at the top of the column for that character.</span></span>

<span data-ttu-id="fc428-113">De `Format-Hex` cmdlet kan u helpen bij het bepalen van het bestands type van een beschadigd bestand of een bestand dat mogelijk geen bestands extensie heeft.</span><span class="sxs-lookup"><span data-stu-id="fc428-113">The `Format-Hex` cmdlet can help you determine the file type of a corrupted file or a file that might not have a filename extension.</span></span> <span data-ttu-id="fc428-114">U kunt deze cmdlet uitvoeren en vervolgens de hexadecimale uitvoer lezen om informatie over het bestand op te halen.</span><span class="sxs-lookup"><span data-stu-id="fc428-114">You can run this cmdlet, and then read the hexadecimal output to get file information.</span></span>

<span data-ttu-id="fc428-115">Wanneer u `Format-Hex` een bestand gebruikt, negeert de cmdlet nieuwe regel tekens en retourneert de volledige inhoud van een bestand in één teken reeks met de tekens voor de nieuwe regel.</span><span class="sxs-lookup"><span data-stu-id="fc428-115">When using `Format-Hex` on a file, the cmdlet ignores newline characters and returns the entire contents of a file in one string with the newline characters preserved.</span></span>

## <span data-ttu-id="fc428-116">VOORBEELDEN</span><span class="sxs-lookup"><span data-stu-id="fc428-116">EXAMPLES</span></span>

### <span data-ttu-id="fc428-117">Voor beeld 1: de hexadecimale weer gave van een teken reeks ophalen</span><span class="sxs-lookup"><span data-stu-id="fc428-117">Example 1: Get the hexadecimal representation of a string</span></span>

<span data-ttu-id="fc428-118">Met deze opdracht wordt de hexadecimale waarde van een teken reeks geretourneerd.</span><span class="sxs-lookup"><span data-stu-id="fc428-118">This command returns the hexadecimal values of a string.</span></span>

```powershell
'Hello World' | Format-Hex
```

```Output
           00 01 02 03 04 05 06 07 08 09 0A 0B 0C 0D 0E 0F

00000000   48 65 6C 6C 6F 20 57 6F 72 6C 64                 Hello World
```

<span data-ttu-id="fc428-119">De teken reeks **Hallo wereld** wordt via de pijp lijn naar de `Format-Hex` cmdlet verzonden.</span><span class="sxs-lookup"><span data-stu-id="fc428-119">The string **Hello World** is sent down the pipeline to the `Format-Hex` cmdlet.</span></span> <span data-ttu-id="fc428-120">De hexadecimale uitvoer van `Format-Hex` bevat de waarden van elk teken in de teken reeks.</span><span class="sxs-lookup"><span data-stu-id="fc428-120">The hexadecimal output from `Format-Hex` shows the values of each character in the string.</span></span>

### <span data-ttu-id="fc428-121">Voor beeld 2: een bestands type zoeken in hexadecimale uitvoer</span><span class="sxs-lookup"><span data-stu-id="fc428-121">Example 2: Find a file type from hexadecimal output</span></span>

<span data-ttu-id="fc428-122">In dit voor beeld wordt de hexadecimale uitvoer gebruikt om het bestands type te bepalen.</span><span class="sxs-lookup"><span data-stu-id="fc428-122">This example uses the hexadecimal output to determine the file type.</span></span> <span data-ttu-id="fc428-123">Met de cmdlet worden het volledige pad van het bestand en de hexadecimale waarden weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="fc428-123">The cmdlet displays the file's full path and the hexadecimal values.</span></span>

<span data-ttu-id="fc428-124">Als u de volgende opdracht wilt testen, maakt u een kopie van een bestaand PDF-bestand op uw lokale computer en wijzigt u de naam van het gekopieerde bestand in `File.t7f` .</span><span class="sxs-lookup"><span data-stu-id="fc428-124">To test the following command, make a copy of an existing PDF file on your local computer and rename the copied file to `File.t7f`.</span></span>

```powershell
Format-Hex -Path .\File.t7f
```

```Output
           Path: C:\Test\File.t7f

           00 01 02 03 04 05 06 07 08 09 0A 0B 0C 0D 0E 0F

00000000   25 50 44 46 2D 31 2E 35 0D 0A 25 B5 B5 B5 B5 0D  %PDF-1.5..%????.
00000010   0A 31 20 30 20 6F 62 6A 0D 0A 3C 3C 2F 54 79 70  .1 0 obj..<</Typ
00000020   65 2F 43 61 74 61 6C 6F 67 2F 50 61 67 65 73 20  e/Catalog/Pages
```

<span data-ttu-id="fc428-125">De `Format-Hex` cmdlet gebruikt de para meter **Path** om een bestands naam op te geven in de huidige map **File. t7f**.</span><span class="sxs-lookup"><span data-stu-id="fc428-125">The `Format-Hex` cmdlet uses the **Path** parameter to specify a filename in the current directory, **File.t7f**.</span></span> <span data-ttu-id="fc428-126">De bestands extensie **. t7f** is ongebruikelijk, maar de hexadecimale uitvoer **% PDF** geeft aan dat het een PDF-bestand is.</span><span class="sxs-lookup"><span data-stu-id="fc428-126">The file extension **.t7f** is uncommon, but the hexadecimal output **%PDF** shows that it is a PDF file.</span></span>

## <span data-ttu-id="fc428-127">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="fc428-127">PARAMETERS</span></span>

### <span data-ttu-id="fc428-128">-Encoding</span><span class="sxs-lookup"><span data-stu-id="fc428-128">-Encoding</span></span>

<span data-ttu-id="fc428-129">Hiermee geeft u de code ring van de uitvoer op.</span><span class="sxs-lookup"><span data-stu-id="fc428-129">Specifies the encoding of the output.</span></span> <span data-ttu-id="fc428-130">Dit is alleen van toepassing op `[string]` invoer.</span><span class="sxs-lookup"><span data-stu-id="fc428-130">This only applies to `[string]` input.</span></span> <span data-ttu-id="fc428-131">De para meter heeft geen invloed op numerieke typen.</span><span class="sxs-lookup"><span data-stu-id="fc428-131">The parameter has no effect on numeric types.</span></span> <span data-ttu-id="fc428-132">De standaardwaarde is `utf8NoBOM`.</span><span class="sxs-lookup"><span data-stu-id="fc428-132">The default value is `utf8NoBOM`.</span></span>

<span data-ttu-id="fc428-133">De acceptabele waarden voor deze para meter zijn als volgt:</span><span class="sxs-lookup"><span data-stu-id="fc428-133">The acceptable values for this parameter are as follows:</span></span>

- <span data-ttu-id="fc428-134">`ascii`: Gebruikt de code ring voor de ASCII-tekenset (7-bits).</span><span class="sxs-lookup"><span data-stu-id="fc428-134">`ascii`: Uses the encoding for the ASCII (7-bit) character set.</span></span>
- <span data-ttu-id="fc428-135">`bigendianunicode`: Wordt gecodeerd in UTF-16-indeling met behulp van de byte volgorde big endian.</span><span class="sxs-lookup"><span data-stu-id="fc428-135">`bigendianunicode`: Encodes in UTF-16 format using the big-endian byte order.</span></span>
- <span data-ttu-id="fc428-136">`oem`: Maakt gebruik van de standaard codering voor MS-DOS-en console Programma's.</span><span class="sxs-lookup"><span data-stu-id="fc428-136">`oem`: Uses the default encoding for MS-DOS and console programs.</span></span>
- <span data-ttu-id="fc428-137">`unicode`: Wordt gecodeerd in UTF-16-indeling met behulp van de byte volgorde little endian.</span><span class="sxs-lookup"><span data-stu-id="fc428-137">`unicode`: Encodes in UTF-16 format using the little-endian byte order.</span></span>
- <span data-ttu-id="fc428-138">`utf7`: Wordt gecodeerd in de indeling UTF-7.</span><span class="sxs-lookup"><span data-stu-id="fc428-138">`utf7`: Encodes in UTF-7 format.</span></span>
- <span data-ttu-id="fc428-139">`utf8`: Wordt gecodeerd in UTF-8-indeling.</span><span class="sxs-lookup"><span data-stu-id="fc428-139">`utf8`: Encodes in UTF-8 format.</span></span>
- <span data-ttu-id="fc428-140">`utf8BOM`: Code ring in UTF-8-indeling met byte order Mark (BOM)</span><span class="sxs-lookup"><span data-stu-id="fc428-140">`utf8BOM`: Encodes in UTF-8 format with Byte Order Mark (BOM)</span></span>
- <span data-ttu-id="fc428-141">`utf8NoBOM`: Code ring in UTF-8-indeling zonder byte order Mark (BOM)</span><span class="sxs-lookup"><span data-stu-id="fc428-141">`utf8NoBOM`: Encodes in UTF-8 format without Byte Order Mark (BOM)</span></span>
- <span data-ttu-id="fc428-142">`utf32`: Gecodeerd in UTF-32-indeling.</span><span class="sxs-lookup"><span data-stu-id="fc428-142">`utf32`: Encodes in UTF-32 format.</span></span>

<span data-ttu-id="fc428-143">Vanaf Power shell 6,2 kunnen met de para meter **Encoding** ook numerieke id's van geregistreerde code pagina's (zoals `-Encoding 1251` ) of teken reeks namen van geregistreerde code pagina's (zoals) worden toegestaan `-Encoding "windows-1251"` .</span><span class="sxs-lookup"><span data-stu-id="fc428-143">Beginning with PowerShell 6.2, the **Encoding** parameter also allows numeric IDs of registered code pages (like `-Encoding 1251`) or string names of registered code pages (like `-Encoding "windows-1251"`).</span></span> <span data-ttu-id="fc428-144">Zie de .NET-documentatie voor [code ring. code tabel](/dotnet/api/system.text.encoding.codepage?view=netcore-2.2)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="fc428-144">For more information, see the .NET documentation for [Encoding.CodePage](/dotnet/api/system.text.encoding.codepage?view=netcore-2.2).</span></span>

```yaml
Type: Encoding
Parameter Sets: ByInputObject
Aliases:
Accepted values: ASCII, BigEndianUnicode, OEM, Unicode, UTF7, UTF8, UTF8BOM, UTF8NoBOM, UTF32

Required: False
Position: Named
Default value: UTF8NoBOM
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="fc428-145">-Input object</span><span class="sxs-lookup"><span data-stu-id="fc428-145">-InputObject</span></span>

<span data-ttu-id="fc428-146">Wordt gebruikt voor de invoer van de pijp lijn.</span><span class="sxs-lookup"><span data-stu-id="fc428-146">Used for pipeline input.</span></span> <span data-ttu-id="fc428-147">Pijplijn invoer ondersteunt alleen bepaalde scalaire typen en `[system.io.fileinfo]` instanties voor sluizen van `Get-ChildItem` .</span><span class="sxs-lookup"><span data-stu-id="fc428-147">Pipeline input supports only certain scalar types and `[system.io.fileinfo]` instances for piping from `Get-ChildItem`.</span></span>

<span data-ttu-id="fc428-148">De ondersteunde scalaire typen zijn:</span><span class="sxs-lookup"><span data-stu-id="fc428-148">The supported scalar types are:</span></span>

- <span data-ttu-id="fc428-149">`[string]`, `[char]`</span><span class="sxs-lookup"><span data-stu-id="fc428-149">`[string]`, `[char]`</span></span>
- <span data-ttu-id="fc428-150">`[byte]`, `[sbyte]`</span><span class="sxs-lookup"><span data-stu-id="fc428-150">`[byte]`, `[sbyte]`</span></span>
- <span data-ttu-id="fc428-151">`[int16]`, `[uint16]`, `[short]`, `[ushort]`</span><span class="sxs-lookup"><span data-stu-id="fc428-151">`[int16]`, `[uint16]`, `[short]`, `[ushort]`</span></span>
- <span data-ttu-id="fc428-152">`[int]`, `[uint]`, `[int32]`, `[uint32]`,</span><span class="sxs-lookup"><span data-stu-id="fc428-152">`[int]`, `[uint]`, `[int32]`, `[uint32]`,</span></span>
- <span data-ttu-id="fc428-153">`[long]`, `[ulong]`, `[int64]`, `[uint64]`</span><span class="sxs-lookup"><span data-stu-id="fc428-153">`[long]`, `[ulong]`, `[int64]`, `[uint64]`</span></span>
- <span data-ttu-id="fc428-154">`[single]`, `[float]`, `[double]`</span><span class="sxs-lookup"><span data-stu-id="fc428-154">`[single]`, `[float]`, `[double]`</span></span>

```yaml
Type: System.Management.Automation.PSObject
Parameter Sets: ByInputObject
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="fc428-155">-LiteralPath</span><span class="sxs-lookup"><span data-stu-id="fc428-155">-LiteralPath</span></span>

<span data-ttu-id="fc428-156">Hiermee geeft u het volledige pad naar een bestand.</span><span class="sxs-lookup"><span data-stu-id="fc428-156">Specifies the complete path to a file.</span></span> <span data-ttu-id="fc428-157">De waarde van **LiteralPath** wordt precies zo gebruikt als deze wordt getypt.</span><span class="sxs-lookup"><span data-stu-id="fc428-157">The value of **LiteralPath** is used exactly as it is typed.</span></span>
<span data-ttu-id="fc428-158">Deze para meter accepteert geen joker tekens.</span><span class="sxs-lookup"><span data-stu-id="fc428-158">This parameter does not accept wildcard characters.</span></span> <span data-ttu-id="fc428-159">Als u meerdere paden naar bestanden wilt opgeven, scheidt u de paden met een komma.</span><span class="sxs-lookup"><span data-stu-id="fc428-159">To specify multiple paths to files, separate the paths with a comma.</span></span> <span data-ttu-id="fc428-160">Als de para meter **LiteralPath** escape-tekens bevat, plaatst u het pad tussen enkele aanhalings tekens.</span><span class="sxs-lookup"><span data-stu-id="fc428-160">If the **LiteralPath** parameter includes escape characters, enclose the path in single quotation marks.</span></span> <span data-ttu-id="fc428-161">Power shell interpreteert geen tekens in één aanhalings teken reeks als escape-reeksen.</span><span class="sxs-lookup"><span data-stu-id="fc428-161">PowerShell does not interpret any characters in a single quoted string as escape sequences.</span></span> <span data-ttu-id="fc428-162">Zie [about_Quoting_Rules](../Microsoft.Powershell.Core/About/about_Quoting_Rules.md)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="fc428-162">For more information, see [about_Quoting_Rules](../Microsoft.Powershell.Core/About/about_Quoting_Rules.md).</span></span>

```yaml
Type: System.String[]
Parameter Sets: LiteralPath
Aliases: PSPath, LP

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="fc428-163">-Path</span><span class="sxs-lookup"><span data-stu-id="fc428-163">-Path</span></span>

<span data-ttu-id="fc428-164">Hiermee geeft u het pad naar de bestanden.</span><span class="sxs-lookup"><span data-stu-id="fc428-164">Specifies the path to files.</span></span> <span data-ttu-id="fc428-165">Gebruik een punt ( `.` ) om de huidige locatie op te geven.</span><span class="sxs-lookup"><span data-stu-id="fc428-165">Use a dot (`.`) to specify the current location.</span></span> <span data-ttu-id="fc428-166">Het Joker teken ( `*` ) wordt geaccepteerd en kan worden gebruikt om alle items op een locatie op te geven.</span><span class="sxs-lookup"><span data-stu-id="fc428-166">The wildcard character (`*`) is accepted and can be used to specify all the items in a location.</span></span> <span data-ttu-id="fc428-167">Als de para meter **Path** escape tekens bevat, plaatst u het pad tussen enkele aanhalings tekens.</span><span class="sxs-lookup"><span data-stu-id="fc428-167">If the **Path** parameter includes escape characters, enclose the path in single quotation marks.</span></span> <span data-ttu-id="fc428-168">Als u meerdere paden naar bestanden wilt opgeven, scheidt u de paden met een komma.</span><span class="sxs-lookup"><span data-stu-id="fc428-168">To specify multiple paths to files, separate the paths with a comma.</span></span>

```yaml
Type: System.String[]
Parameter Sets: Path
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: True
```

### <span data-ttu-id="fc428-169">-RAW</span><span class="sxs-lookup"><span data-stu-id="fc428-169">-Raw</span></span>

<span data-ttu-id="fc428-170">Deze para meter heeft niets meer.</span><span class="sxs-lookup"><span data-stu-id="fc428-170">This parameter no longer does anything.</span></span> <span data-ttu-id="fc428-171">Het wordt bewaard voor compatibiliteit met scripts.</span><span class="sxs-lookup"><span data-stu-id="fc428-171">It is retained for script compatibility.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: ByInputObject
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="fc428-172">-Offset</span><span class="sxs-lookup"><span data-stu-id="fc428-172">-Offset</span></span>

<span data-ttu-id="fc428-173">Hiermee wordt het aantal bytes dat moet worden overgeslagen, opgenomen in de hexadecimale uitvoer.</span><span class="sxs-lookup"><span data-stu-id="fc428-173">This represents the number of bytes to skip from being part of the hex output.</span></span>

<span data-ttu-id="fc428-174">Deze para meter is geïntroduceerd in Power shell 6,2.</span><span class="sxs-lookup"><span data-stu-id="fc428-174">This parameter was introduced in PowerShell 6.2.</span></span>

```yaml
Type: System.Int64
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: 0
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="fc428-175">-Aantal</span><span class="sxs-lookup"><span data-stu-id="fc428-175">-Count</span></span>

<span data-ttu-id="fc428-176">Hiermee wordt het aantal bytes aangegeven dat moet worden meegenomen in de hexadecimale uitvoer.</span><span class="sxs-lookup"><span data-stu-id="fc428-176">This represents the number of bytes to include in the hex output.</span></span>

<span data-ttu-id="fc428-177">Deze para meter is geïntroduceerd in Power shell 6,2.</span><span class="sxs-lookup"><span data-stu-id="fc428-177">This parameter was introduced in PowerShell 6.2.</span></span>

```yaml
Type: System.Int64
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: Int64.MaxValue
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="fc428-178">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="fc428-178">CommonParameters</span></span>

<span data-ttu-id="fc428-179">Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="fc428-179">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="fc428-180">Zie [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="fc428-180">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="fc428-181">INVOER</span><span class="sxs-lookup"><span data-stu-id="fc428-181">INPUTS</span></span>

### <span data-ttu-id="fc428-182">System. String</span><span class="sxs-lookup"><span data-stu-id="fc428-182">System.String</span></span>

<span data-ttu-id="fc428-183">U kunt een teken reeks door sluizen naar deze cmdlet.</span><span class="sxs-lookup"><span data-stu-id="fc428-183">You can pipe a string to this cmdlet.</span></span>

## <span data-ttu-id="fc428-184">UITVOER</span><span class="sxs-lookup"><span data-stu-id="fc428-184">OUTPUTS</span></span>

### <span data-ttu-id="fc428-185">Micro soft. Power shell. commands. ByteCollection</span><span class="sxs-lookup"><span data-stu-id="fc428-185">Microsoft.PowerShell.Commands.ByteCollection</span></span>

<span data-ttu-id="fc428-186">Met deze cmdlet wordt een **ByteCollection** geretourneerd.</span><span class="sxs-lookup"><span data-stu-id="fc428-186">This cmdlet returns a **ByteCollection**.</span></span> <span data-ttu-id="fc428-187">Dit object vertegenwoordigt een verzameling van bytes.</span><span class="sxs-lookup"><span data-stu-id="fc428-187">This object represents a collection of bytes.</span></span> <span data-ttu-id="fc428-188">Het bevat methoden die het verzamelen van bytes converteren naar een teken reeks die is opgemaakt als elke regel van uitvoer die wordt geretourneerd door `Format-Hex` .</span><span class="sxs-lookup"><span data-stu-id="fc428-188">It includes methods that convert the collection of bytes to a string formatted like each line of output returned by `Format-Hex`.</span></span> <span data-ttu-id="fc428-189">Als u de para meter **Path** of **LiteralPath** opgeeft, bevat het object ook het pad van het bestand dat elke byte bevat.</span><span class="sxs-lookup"><span data-stu-id="fc428-189">If you specify the **Path** or **LiteralPath** parameter, the object also contains the path of the file that contains each byte.</span></span>

## <span data-ttu-id="fc428-190">OPMERKINGEN</span><span class="sxs-lookup"><span data-stu-id="fc428-190">NOTES</span></span>

<span data-ttu-id="fc428-191">De meest rechtse kolom van uitvoer probeert de bytes weer te geven als ASCII-tekens:</span><span class="sxs-lookup"><span data-stu-id="fc428-191">The right-most column of output tries to render the bytes as ASCII characters:</span></span>

<span data-ttu-id="fc428-192">Over het algemeen wordt elke byte geïnterpreteerd als een Unicode-code punt, wat betekent dat:</span><span class="sxs-lookup"><span data-stu-id="fc428-192">Generally, each byte is interpreted as a Unicode code point, which means that:</span></span>

- <span data-ttu-id="fc428-193">Afdruk bare ASCII-tekens worden altijd correct weer gegeven</span><span class="sxs-lookup"><span data-stu-id="fc428-193">Printable ASCII characters are always rendered correctly</span></span>
- <span data-ttu-id="fc428-194">Multi-byte UTF-8 tekens worden nooit correct weer gegeven</span><span class="sxs-lookup"><span data-stu-id="fc428-194">Multi-byte UTF-8 characters never render correctly</span></span>
- <span data-ttu-id="fc428-195">UTF-16-tekens worden alleen correct weer gegeven als er een hoge byte is `NUL` .</span><span class="sxs-lookup"><span data-stu-id="fc428-195">UTF-16 characters render correctly only if their high-order byte happens be `NUL`.</span></span>

## <span data-ttu-id="fc428-196">GERELATEERDE KOPPELINGEN</span><span class="sxs-lookup"><span data-stu-id="fc428-196">RELATED LINKS</span></span>

[<span data-ttu-id="fc428-197">about_Quoting_Rules</span><span class="sxs-lookup"><span data-stu-id="fc428-197">about_Quoting_Rules</span></span>](../Microsoft.Powershell.Core/About/about_Quoting_Rules.md)

[<span data-ttu-id="fc428-198">Format-Custom</span><span class="sxs-lookup"><span data-stu-id="fc428-198">Format-Custom</span></span>](Format-Custom.md)

[<span data-ttu-id="fc428-199">Format-List</span><span class="sxs-lookup"><span data-stu-id="fc428-199">Format-List</span></span>](Format-List.md)

[<span data-ttu-id="fc428-200">Format-Table</span><span class="sxs-lookup"><span data-stu-id="fc428-200">Format-Table</span></span>](Format-Table.md)

[<span data-ttu-id="fc428-201">Format-Wide</span><span class="sxs-lookup"><span data-stu-id="fc428-201">Format-Wide</span></span>](Format-Wide.md)
