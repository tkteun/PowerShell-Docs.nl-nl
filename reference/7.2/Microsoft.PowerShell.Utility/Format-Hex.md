---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 08/19/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/format-hex?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Format-Hex
ms.openlocfilehash: a45e7919b5a24189ca7f50661795ff035c38a037
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 11/17/2020
ms.locfileid: "94705455"
---
# <span data-ttu-id="fb851-102">Format-Hex</span><span class="sxs-lookup"><span data-stu-id="fb851-102">Format-Hex</span></span>

## <span data-ttu-id="fb851-103">SAMENVATTING</span><span class="sxs-lookup"><span data-stu-id="fb851-103">SYNOPSIS</span></span>

<span data-ttu-id="fb851-104">Geeft een bestand of andere invoer weer als hexadecimale notatie.</span><span class="sxs-lookup"><span data-stu-id="fb851-104">Displays a file or other input as hexadecimal.</span></span>

## <span data-ttu-id="fb851-105">SYNTAXIS</span><span class="sxs-lookup"><span data-stu-id="fb851-105">SYNTAX</span></span>

### <span data-ttu-id="fb851-106">Pad</span><span class="sxs-lookup"><span data-stu-id="fb851-106">Path</span></span>

```
Format-Hex [-Path] <String[]> [-Count <Int64>] [-Offset <Int64>] [<CommonParameters>]
```

### <span data-ttu-id="fb851-107">LiteralPath</span><span class="sxs-lookup"><span data-stu-id="fb851-107">LiteralPath</span></span>

```
Format-Hex -LiteralPath <String[]> [-Count <Int64>] [-Offset <Int64>] [<CommonParameters>]
```

### <span data-ttu-id="fb851-108">ByInputObject</span><span class="sxs-lookup"><span data-stu-id="fb851-108">ByInputObject</span></span>

```
Format-Hex -InputObject <PSObject> [-Encoding <Encoding>] [-Count <Int64>] [-Offset <Int64>] [-Raw]
 [<CommonParameters>]
```

## <span data-ttu-id="fb851-109">BESCHRIJVING</span><span class="sxs-lookup"><span data-stu-id="fb851-109">DESCRIPTION</span></span>

<span data-ttu-id="fb851-110">De `Format-Hex` cmdlet geeft een bestand of andere invoer weer als hexadecimale waarden.</span><span class="sxs-lookup"><span data-stu-id="fb851-110">The `Format-Hex` cmdlet displays a file or other input as hexadecimal values.</span></span> <span data-ttu-id="fb851-111">Als u de verschuiving van een teken van de uitvoer wilt bepalen, voegt u het nummer aan de linkerkant van de rij toe aan het getal boven aan de kolom voor dat teken.</span><span class="sxs-lookup"><span data-stu-id="fb851-111">To determine the offset of a character from the output, add the number at the leftmost of the row to the number at the top of the column for that character.</span></span>

<span data-ttu-id="fb851-112">De `Format-Hex` cmdlet kan u helpen bij het bepalen van het bestands type van een beschadigd bestand of een bestand dat mogelijk geen bestands extensie heeft.</span><span class="sxs-lookup"><span data-stu-id="fb851-112">The `Format-Hex` cmdlet can help you determine the file type of a corrupted file or a file that might not have a filename extension.</span></span> <span data-ttu-id="fb851-113">U kunt deze cmdlet uitvoeren en vervolgens de hexadecimale uitvoer lezen om informatie over het bestand op te halen.</span><span class="sxs-lookup"><span data-stu-id="fb851-113">You can run this cmdlet, and then read the hexadecimal output to get file information.</span></span>

<span data-ttu-id="fb851-114">Wanneer u `Format-Hex` een bestand gebruikt, negeert de cmdlet nieuwe regel tekens en retourneert de volledige inhoud van een bestand in één teken reeks met de tekens voor de nieuwe regel.</span><span class="sxs-lookup"><span data-stu-id="fb851-114">When using `Format-Hex` on a file, the cmdlet ignores newline characters and returns the entire contents of a file in one string with the newline characters preserved.</span></span>

## <span data-ttu-id="fb851-115">VOORBEELDEN</span><span class="sxs-lookup"><span data-stu-id="fb851-115">EXAMPLES</span></span>

### <span data-ttu-id="fb851-116">Voor beeld 1: de hexadecimale weer gave van een teken reeks ophalen</span><span class="sxs-lookup"><span data-stu-id="fb851-116">Example 1: Get the hexadecimal representation of a string</span></span>

<span data-ttu-id="fb851-117">Met deze opdracht wordt de hexadecimale waarde van een teken reeks geretourneerd.</span><span class="sxs-lookup"><span data-stu-id="fb851-117">This command returns the hexadecimal values of a string.</span></span>

```powershell
'Hello World' | Format-Hex
```

```Output
   Label: String (System.String) <2944BEC3>

          Offset Bytes                                           Ascii
                 00 01 02 03 04 05 06 07 08 09 0A 0B 0C 0D 0E 0F
          ------ ----------------------------------------------- -----
0000000000000000 48 65 6C 6C 6F 20 57 6F 72 6C 64                Hello World
```

<span data-ttu-id="fb851-118">De teken reeks **Hallo wereld** wordt via de pijp lijn naar de `Format-Hex` cmdlet verzonden.</span><span class="sxs-lookup"><span data-stu-id="fb851-118">The string **Hello World** is sent down the pipeline to the `Format-Hex` cmdlet.</span></span> <span data-ttu-id="fb851-119">De hexadecimale uitvoer van `Format-Hex` bevat de waarden van elk teken in de teken reeks.</span><span class="sxs-lookup"><span data-stu-id="fb851-119">The hexadecimal output from `Format-Hex` shows the values of each character in the string.</span></span>

### <span data-ttu-id="fb851-120">Voor beeld 2: een bestands type zoeken in hexadecimale uitvoer</span><span class="sxs-lookup"><span data-stu-id="fb851-120">Example 2: Find a file type from hexadecimal output</span></span>

<span data-ttu-id="fb851-121">In dit voor beeld wordt de hexadecimale uitvoer gebruikt om het bestands type te bepalen.</span><span class="sxs-lookup"><span data-stu-id="fb851-121">This example uses the hexadecimal output to determine the file type.</span></span> <span data-ttu-id="fb851-122">Met de cmdlet worden het volledige pad van het bestand en de hexadecimale waarden weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="fb851-122">The cmdlet displays the file's full path and the hexadecimal values.</span></span>

<span data-ttu-id="fb851-123">Als u de volgende opdracht wilt testen, maakt u een kopie van een bestaand PDF-bestand op uw lokale computer en wijzigt u de naam van het gekopieerde bestand in `File.t7f` .</span><span class="sxs-lookup"><span data-stu-id="fb851-123">To test the following command, make a copy of an existing PDF file on your local computer and rename the copied file to `File.t7f`.</span></span>

```powershell
Format-Hex -Path .\File.t7f -Count 48
```

```Output
   Label: C:\Test\File.t7f

          Offset Bytes                                           Ascii
                 00 01 02 03 04 05 06 07 08 09 0A 0B 0C 0D 0E 0F
          ------ ----------------------------------------------- -----
0000000000000000 25 50 44 46 2D 31 2E 35 0D 0A 25 B5 B5 B5 B5 0D %PDF-1.5..%????.
0000000000000010 0A 31 20 30 20 6F 62 6A 0D 0A 3C 3C 2F 54 79 70 .1 0 obj..<</Typ
0000000000000020 65 2F 43 61 74 61 6C 6F 67 2F 50 61 67 65 73 20 e/Catalog/Pages
```

<span data-ttu-id="fb851-124">De `Format-Hex` cmdlet gebruikt de para meter **Path** om een bestands naam op te geven in de huidige map `File.t7f` .</span><span class="sxs-lookup"><span data-stu-id="fb851-124">The `Format-Hex` cmdlet uses the **Path** parameter to specify a filename in the current directory, `File.t7f`.</span></span> <span data-ttu-id="fb851-125">De bestands extensie `.t7f` is ongebruikelijk, maar in de hexadecimale uitvoer `%PDF` ziet u dat het een PDF-bestand is.</span><span class="sxs-lookup"><span data-stu-id="fb851-125">The file extension `.t7f` is uncommon, but the hexadecimal output `%PDF` shows that it is a PDF file.</span></span> <span data-ttu-id="fb851-126">In dit voor beeld wordt de para meter **aantal** gebruikt om de uitvoer te beperken tot de eerste 48 bytes van het bestand.</span><span class="sxs-lookup"><span data-stu-id="fb851-126">In this example, the **Count** parameter is used to limit the output to the first 48 bytes of the file.</span></span>

### <span data-ttu-id="fb851-127">Voor beeld 3: een matrix met verschillende gegevens typen opmaken</span><span class="sxs-lookup"><span data-stu-id="fb851-127">Example 3: Format an array of different data types</span></span>

<span data-ttu-id="fb851-128">In dit voor beeld wordt een matrix van verschillende gegevens typen gebruikt om te markeren hoe `Format-Hex` deze worden verwerkt in de pijp lijn.</span><span class="sxs-lookup"><span data-stu-id="fb851-128">This example uses an array of different data types to highlight how `Format-Hex` handles them in the Pipeline.</span></span>

<span data-ttu-id="fb851-129">Elk object wordt door de pijp lijn en het proces afzonderlijk door gegeven.</span><span class="sxs-lookup"><span data-stu-id="fb851-129">It will pass each object through the Pipeline and process individually.</span></span> <span data-ttu-id="fb851-130">Als het echter numerieke gegevens is en het aangrenzende object ook numeriek is, worden ze in één uitvoer blok gegroepeerd.</span><span class="sxs-lookup"><span data-stu-id="fb851-130">However, if it's numeric data, and the adjacent object is also numeric, it will group them into a single output block.</span></span>

```powershell
'Hello world!', 1, 1138, 'foo', 'bar', 0xdeadbeef, 1gb, 0b1101011100 , $true, $false | Format-Hex
```

```Output
   Label: String (System.String) <24F1F0A3>

          Offset Bytes                                           Ascii
                 00 01 02 03 04 05 06 07 08 09 0A 0B 0C 0D 0E 0F
          ------ ----------------------------------------------- -----
0000000000000000 48 65 6C 6C 6F 20 77 6F 72 6C 64 21             Hello world!

   Label: Int32 (System.Int32) <2EB933C5>

          Offset Bytes                                           Ascii
                 00 01 02 03 04 05 06 07 08 09 0A 0B 0C 0D 0E 0F
          ------ ----------------------------------------------- -----
0000000000000000 01 00 00 00 72 04 00 00                         �   r�

   Label: String (System.String) <4078B66C>

          Offset Bytes                                           Ascii
                 00 01 02 03 04 05 06 07 08 09 0A 0B 0C 0D 0E 0F
          ------ ----------------------------------------------- -----
0000000000000000 66 6F 6F                                        foo

   Label: String (System.String) <51E4A317>

          Offset Bytes                                           Ascii
                 00 01 02 03 04 05 06 07 08 09 0A 0B 0C 0D 0E 0F
          ------ ----------------------------------------------- -----
0000000000000000 62 61 72                                        bar

   Label: Int32 (System.Int32) <5ADF167B>

          Offset Bytes                                           Ascii
                 00 01 02 03 04 05 06 07 08 09 0A 0B 0C 0D 0E 0F
          ------ ----------------------------------------------- -----
0000000000000000 EF BE AD DE 00 00 00 40 5C 03 00 00             ï¾-Þ   @\�

   Label: Boolean (System.Boolean) <7D8C4C1D>

          Offset Bytes                                           Ascii
                 00 01 02 03 04 05 06 07 08 09 0A 0B 0C 0D 0E 0F
          ------ ----------------------------------------------- -----
0000000000000000 01 00 00 00 00 00 00 00                         �
```

## <span data-ttu-id="fb851-131">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="fb851-131">PARAMETERS</span></span>

### <span data-ttu-id="fb851-132">-Encoding</span><span class="sxs-lookup"><span data-stu-id="fb851-132">-Encoding</span></span>

<span data-ttu-id="fb851-133">Hiermee geeft u de code ring van de invoer teken reeksen.</span><span class="sxs-lookup"><span data-stu-id="fb851-133">Specifies the encoding of the input strings.</span></span> <span data-ttu-id="fb851-134">Dit is alleen van toepassing op `[string]` invoer.</span><span class="sxs-lookup"><span data-stu-id="fb851-134">This only applies to `[string]` input.</span></span> <span data-ttu-id="fb851-135">De para meter heeft geen invloed op numerieke typen.</span><span class="sxs-lookup"><span data-stu-id="fb851-135">The parameter has no effect on numeric types.</span></span> <span data-ttu-id="fb851-136">De uitvoer waarde is altijd `utf8NoBOM` .</span><span class="sxs-lookup"><span data-stu-id="fb851-136">The output value is always `utf8NoBOM`.</span></span>

<span data-ttu-id="fb851-137">De acceptabele waarden voor deze para meter zijn als volgt:</span><span class="sxs-lookup"><span data-stu-id="fb851-137">The acceptable values for this parameter are as follows:</span></span>

- <span data-ttu-id="fb851-138">`ascii`: Gebruikt de code ring voor de ASCII-tekenset (7-bits).</span><span class="sxs-lookup"><span data-stu-id="fb851-138">`ascii`: Uses the encoding for the ASCII (7-bit) character set.</span></span>
- <span data-ttu-id="fb851-139">`bigendianunicode`: Wordt gecodeerd in UTF-16-indeling met behulp van de byte volgorde big endian.</span><span class="sxs-lookup"><span data-stu-id="fb851-139">`bigendianunicode`: Encodes in UTF-16 format using the big-endian byte order.</span></span>
- <span data-ttu-id="fb851-140">`bigendianutf32`: Codeert in UTF-32-indeling met behulp van de byte volgorde big endian.</span><span class="sxs-lookup"><span data-stu-id="fb851-140">`bigendianutf32`: Encodes in UTF-32 format using the big-endian byte order.</span></span>
- <span data-ttu-id="fb851-141">`oem`: Maakt gebruik van de standaard codering voor MS-DOS-en console Programma's.</span><span class="sxs-lookup"><span data-stu-id="fb851-141">`oem`: Uses the default encoding for MS-DOS and console programs.</span></span>
- <span data-ttu-id="fb851-142">`unicode`: Wordt gecodeerd in UTF-16-indeling met behulp van de byte volgorde little endian.</span><span class="sxs-lookup"><span data-stu-id="fb851-142">`unicode`: Encodes in UTF-16 format using the little-endian byte order.</span></span>
- <span data-ttu-id="fb851-143">`utf7`: Wordt gecodeerd in de indeling UTF-7.</span><span class="sxs-lookup"><span data-stu-id="fb851-143">`utf7`: Encodes in UTF-7 format.</span></span>
- <span data-ttu-id="fb851-144">`utf8`: Wordt gecodeerd in UTF-8-indeling.</span><span class="sxs-lookup"><span data-stu-id="fb851-144">`utf8`: Encodes in UTF-8 format.</span></span>
- <span data-ttu-id="fb851-145">`utf8BOM`: Code ring in UTF-8-indeling met byte order Mark (BOM)</span><span class="sxs-lookup"><span data-stu-id="fb851-145">`utf8BOM`: Encodes in UTF-8 format with Byte Order Mark (BOM)</span></span>
- <span data-ttu-id="fb851-146">`utf8NoBOM`: Code ring in UTF-8-indeling zonder byte order Mark (BOM)</span><span class="sxs-lookup"><span data-stu-id="fb851-146">`utf8NoBOM`: Encodes in UTF-8 format without Byte Order Mark (BOM)</span></span>
- <span data-ttu-id="fb851-147">`utf32`: Gecodeerd in UTF-32-indeling.</span><span class="sxs-lookup"><span data-stu-id="fb851-147">`utf32`: Encodes in UTF-32 format.</span></span>

<span data-ttu-id="fb851-148">Vanaf Power shell 6,2 kunnen met de para meter **Encoding** ook numerieke id's van geregistreerde code pagina's (zoals `-Encoding 1251` ) of teken reeks namen van geregistreerde code pagina's (zoals) worden toegestaan `-Encoding "windows-1251"` .</span><span class="sxs-lookup"><span data-stu-id="fb851-148">Beginning with PowerShell 6.2, the **Encoding** parameter also allows numeric IDs of registered code pages (like `-Encoding 1251`) or string names of registered code pages (like `-Encoding "windows-1251"`).</span></span> <span data-ttu-id="fb851-149">Zie de .NET-documentatie voor [code ring. code tabel](/dotnet/api/system.text.encoding.codepage?view=netcore-2.2)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="fb851-149">For more information, see the .NET documentation for [Encoding.CodePage](/dotnet/api/system.text.encoding.codepage?view=netcore-2.2).</span></span>

> [!NOTE]
> <span data-ttu-id="fb851-150">**UTF-7** _ wordt niet meer aanbevolen om te gebruiken.</span><span class="sxs-lookup"><span data-stu-id="fb851-150">**UTF-7** _ is no longer recommended to use.</span></span> <span data-ttu-id="fb851-151">In Power shell 7,1 wordt een waarschuwing geschreven als u `utf7` de para meter _ *Encoding*\* opgeeft.</span><span class="sxs-lookup"><span data-stu-id="fb851-151">In PowerShell 7.1, a warning is written if you specify `utf7` for the _ *Encoding*\* parameter.</span></span>

```yaml
Type: System.Text.Encoding
Parameter Sets: ByInputObject
Aliases:
Accepted values: ASCII, BigEndianUnicode, BigEndianUTF32, OEM, Unicode, UTF7, UTF8, UTF8BOM, UTF8NoBOM, UTF32

Required: False
Position: Named
Default value: UTF8NoBOM
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="fb851-152">-Input object</span><span class="sxs-lookup"><span data-stu-id="fb851-152">-InputObject</span></span>

<span data-ttu-id="fb851-153">Wordt gebruikt voor de invoer van de pijp lijn.</span><span class="sxs-lookup"><span data-stu-id="fb851-153">Used for pipeline input.</span></span> <span data-ttu-id="fb851-154">Pijplijn invoer ondersteunt alleen bepaalde scalaire typen en `[system.io.fileinfo]` instanties voor sluizen van `Get-ChildItem` .</span><span class="sxs-lookup"><span data-stu-id="fb851-154">Pipeline input supports only certain scalar types and `[system.io.fileinfo]` instances for piping from `Get-ChildItem`.</span></span>

<span data-ttu-id="fb851-155">De ondersteunde scalaire typen zijn:</span><span class="sxs-lookup"><span data-stu-id="fb851-155">The supported scalar types are:</span></span>

- <span data-ttu-id="fb851-156">`[string]`, `[char]`</span><span class="sxs-lookup"><span data-stu-id="fb851-156">`[string]`, `[char]`</span></span>
- <span data-ttu-id="fb851-157">`[byte]`, `[sbyte]`</span><span class="sxs-lookup"><span data-stu-id="fb851-157">`[byte]`, `[sbyte]`</span></span>
- <span data-ttu-id="fb851-158">`[int16]`, `[uint16]`, `[short]`, `[ushort]`</span><span class="sxs-lookup"><span data-stu-id="fb851-158">`[int16]`, `[uint16]`, `[short]`, `[ushort]`</span></span>
- <span data-ttu-id="fb851-159">`[int]`, `[uint]`, `[int32]`, `[uint32]`,</span><span class="sxs-lookup"><span data-stu-id="fb851-159">`[int]`, `[uint]`, `[int32]`, `[uint32]`,</span></span>
- <span data-ttu-id="fb851-160">`[long]`, `[ulong]`, `[int64]`, `[uint64]`</span><span class="sxs-lookup"><span data-stu-id="fb851-160">`[long]`, `[ulong]`, `[int64]`, `[uint64]`</span></span>
- <span data-ttu-id="fb851-161">`[single]`, `[float]`, `[double]`</span><span class="sxs-lookup"><span data-stu-id="fb851-161">`[single]`, `[float]`, `[double]`</span></span>
- `[boolean]`

<span data-ttu-id="fb851-162">Vóór Power shell 6,2 wordt `Format-Hex` een pijplijn invoer met meerdere invoer typen verwerkt door alle vergelijk bare objecten te groeperen.</span><span class="sxs-lookup"><span data-stu-id="fb851-162">Prior to PowerShell 6.2, `Format-Hex` would handle a Pipeline input with multiple input types by grouping all like objects together.</span></span> <span data-ttu-id="fb851-163">Nu wordt elk afzonderlijk object verwerkt terwijl het door de pijp lijn wordt door gegeven, waardoor objecten niet gezamenlijk worden gegroepeerd, tenzij like-objecten aaneengesloten zijn.</span><span class="sxs-lookup"><span data-stu-id="fb851-163">Now, it handles each individual object as it passes through the Pipeline and won't group objects together unless like objects are adjacent.</span></span>

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

### <span data-ttu-id="fb851-164">-LiteralPath</span><span class="sxs-lookup"><span data-stu-id="fb851-164">-LiteralPath</span></span>

<span data-ttu-id="fb851-165">Hiermee geeft u het volledige pad naar een bestand.</span><span class="sxs-lookup"><span data-stu-id="fb851-165">Specifies the complete path to a file.</span></span> <span data-ttu-id="fb851-166">De waarde van **LiteralPath** wordt precies zo gebruikt als deze wordt getypt.</span><span class="sxs-lookup"><span data-stu-id="fb851-166">The value of **LiteralPath** is used exactly as it is typed.</span></span>
<span data-ttu-id="fb851-167">Deze para meter accepteert geen joker tekens.</span><span class="sxs-lookup"><span data-stu-id="fb851-167">This parameter does not accept wildcard characters.</span></span> <span data-ttu-id="fb851-168">Als u meerdere paden naar bestanden wilt opgeven, scheidt u de paden met een komma.</span><span class="sxs-lookup"><span data-stu-id="fb851-168">To specify multiple paths to files, separate the paths with a comma.</span></span> <span data-ttu-id="fb851-169">Als de para meter **LiteralPath** escape-tekens bevat, plaatst u het pad tussen enkele aanhalings tekens.</span><span class="sxs-lookup"><span data-stu-id="fb851-169">If the **LiteralPath** parameter includes escape characters, enclose the path in single quotation marks.</span></span> <span data-ttu-id="fb851-170">Power shell interpreteert geen tekens in één aanhalings teken reeks als escape-reeksen.</span><span class="sxs-lookup"><span data-stu-id="fb851-170">PowerShell does not interpret any characters in a single quoted string as escape sequences.</span></span> <span data-ttu-id="fb851-171">Zie [about_Quoting_Rules](../Microsoft.Powershell.Core/About/about_Quoting_Rules.md)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="fb851-171">For more information, see [about_Quoting_Rules](../Microsoft.Powershell.Core/About/about_Quoting_Rules.md).</span></span>

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

### <span data-ttu-id="fb851-172">-Path</span><span class="sxs-lookup"><span data-stu-id="fb851-172">-Path</span></span>

<span data-ttu-id="fb851-173">Hiermee geeft u het pad naar de bestanden.</span><span class="sxs-lookup"><span data-stu-id="fb851-173">Specifies the path to files.</span></span> <span data-ttu-id="fb851-174">Gebruik een punt ( `.` ) om de huidige locatie op te geven.</span><span class="sxs-lookup"><span data-stu-id="fb851-174">Use a dot (`.`) to specify the current location.</span></span> <span data-ttu-id="fb851-175">Het Joker teken ( `*` ) wordt geaccepteerd en kan worden gebruikt om alle items op een locatie op te geven.</span><span class="sxs-lookup"><span data-stu-id="fb851-175">The wildcard character (`*`) is accepted and can be used to specify all the items in a location.</span></span> <span data-ttu-id="fb851-176">Als de para meter **Path** escape tekens bevat, plaatst u het pad tussen enkele aanhalings tekens.</span><span class="sxs-lookup"><span data-stu-id="fb851-176">If the **Path** parameter includes escape characters, enclose the path in single quotation marks.</span></span> <span data-ttu-id="fb851-177">Als u meerdere paden naar bestanden wilt opgeven, scheidt u de paden met een komma.</span><span class="sxs-lookup"><span data-stu-id="fb851-177">To specify multiple paths to files, separate the paths with a comma.</span></span>

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

### <span data-ttu-id="fb851-178">-RAW</span><span class="sxs-lookup"><span data-stu-id="fb851-178">-Raw</span></span>

<span data-ttu-id="fb851-179">Deze para meter heeft niets meer.</span><span class="sxs-lookup"><span data-stu-id="fb851-179">This parameter no longer does anything.</span></span> <span data-ttu-id="fb851-180">Het wordt bewaard voor compatibiliteit met scripts.</span><span class="sxs-lookup"><span data-stu-id="fb851-180">It is retained for script compatibility.</span></span>

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

### <span data-ttu-id="fb851-181">-Offset</span><span class="sxs-lookup"><span data-stu-id="fb851-181">-Offset</span></span>

<span data-ttu-id="fb851-182">Hiermee wordt het aantal bytes dat moet worden overgeslagen, opgenomen in de hexadecimale uitvoer.</span><span class="sxs-lookup"><span data-stu-id="fb851-182">This represents the number of bytes to skip from being part of the hex output.</span></span>

<span data-ttu-id="fb851-183">Deze para meter is geïntroduceerd in Power shell 6,2.</span><span class="sxs-lookup"><span data-stu-id="fb851-183">This parameter was introduced in PowerShell 6.2.</span></span>

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

### <span data-ttu-id="fb851-184">-Aantal</span><span class="sxs-lookup"><span data-stu-id="fb851-184">-Count</span></span>

<span data-ttu-id="fb851-185">Hiermee wordt het aantal bytes aangegeven dat moet worden meegenomen in de hexadecimale uitvoer.</span><span class="sxs-lookup"><span data-stu-id="fb851-185">This represents the number of bytes to include in the hex output.</span></span>

<span data-ttu-id="fb851-186">Deze para meter is geïntroduceerd in Power shell 6,2.</span><span class="sxs-lookup"><span data-stu-id="fb851-186">This parameter was introduced in PowerShell 6.2.</span></span>

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

### <span data-ttu-id="fb851-187">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="fb851-187">CommonParameters</span></span>

<span data-ttu-id="fb851-188">Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="fb851-188">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="fb851-189">Zie [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="fb851-189">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="fb851-190">INVOER</span><span class="sxs-lookup"><span data-stu-id="fb851-190">INPUTS</span></span>

### <span data-ttu-id="fb851-191">System. String</span><span class="sxs-lookup"><span data-stu-id="fb851-191">System.String</span></span>

<span data-ttu-id="fb851-192">U kunt een teken reeks door sluizen naar deze cmdlet.</span><span class="sxs-lookup"><span data-stu-id="fb851-192">You can pipe a string to this cmdlet.</span></span>

## <span data-ttu-id="fb851-193">UITVOER</span><span class="sxs-lookup"><span data-stu-id="fb851-193">OUTPUTS</span></span>

### <span data-ttu-id="fb851-194">Micro soft. Power shell. commands. ByteCollection</span><span class="sxs-lookup"><span data-stu-id="fb851-194">Microsoft.PowerShell.Commands.ByteCollection</span></span>

<span data-ttu-id="fb851-195">Met deze cmdlet wordt een **ByteCollection** geretourneerd.</span><span class="sxs-lookup"><span data-stu-id="fb851-195">This cmdlet returns a **ByteCollection**.</span></span> <span data-ttu-id="fb851-196">Dit object vertegenwoordigt een verzameling van bytes.</span><span class="sxs-lookup"><span data-stu-id="fb851-196">This object represents a collection of bytes.</span></span> <span data-ttu-id="fb851-197">Het bevat methoden die het verzamelen van bytes converteren naar een teken reeks die is opgemaakt als elke regel van uitvoer die wordt geretourneerd door `Format-Hex` .</span><span class="sxs-lookup"><span data-stu-id="fb851-197">It includes methods that convert the collection of bytes to a string formatted like each line of output returned by `Format-Hex`.</span></span> <span data-ttu-id="fb851-198">De uitvoer geeft ook de status aan van het aantal bytes dat wordt verwerkt.</span><span class="sxs-lookup"><span data-stu-id="fb851-198">The output also states they type of bytes being processed.</span></span> <span data-ttu-id="fb851-199">Als u de para meter **Path** of **LiteralPath** opgeeft, bevat het object het pad van het bestand dat elke byte bevat.</span><span class="sxs-lookup"><span data-stu-id="fb851-199">If you specify the **Path** or **LiteralPath** parameter, the object contains the path of the file that contains each byte.</span></span> <span data-ttu-id="fb851-200">Als u een teken reeks, Booleaans, geheel getal, enzovoort doorgeeft, wordt deze op de juiste wijze gelabeld.</span><span class="sxs-lookup"><span data-stu-id="fb851-200">If you pass a string, boolean, integer, etc, it will be labeled appropriately.</span></span>

## <span data-ttu-id="fb851-201">OPMERKINGEN</span><span class="sxs-lookup"><span data-stu-id="fb851-201">NOTES</span></span>

<span data-ttu-id="fb851-202">De meest rechtse kolom van uitvoer probeert de bytes weer te geven als ASCII-tekens:</span><span class="sxs-lookup"><span data-stu-id="fb851-202">The right-most column of output tries to render the bytes as ASCII characters:</span></span>

<span data-ttu-id="fb851-203">Over het algemeen wordt elke byte geïnterpreteerd als een Unicode-code punt, wat betekent dat:</span><span class="sxs-lookup"><span data-stu-id="fb851-203">Generally, each byte is interpreted as a Unicode code point, which means that:</span></span>

- <span data-ttu-id="fb851-204">Afdruk bare ASCII-tekens worden altijd correct weer gegeven</span><span class="sxs-lookup"><span data-stu-id="fb851-204">Printable ASCII characters are always rendered correctly</span></span>
- <span data-ttu-id="fb851-205">Multi-byte UTF-8 tekens worden nooit correct weer gegeven</span><span class="sxs-lookup"><span data-stu-id="fb851-205">Multi-byte UTF-8 characters never render correctly</span></span>
- <span data-ttu-id="fb851-206">UTF-16-tekens worden alleen correct weer gegeven als er een hoge byte is `NUL` .</span><span class="sxs-lookup"><span data-stu-id="fb851-206">UTF-16 characters render correctly only if their high-order byte happens be `NUL`.</span></span>

## <span data-ttu-id="fb851-207">GERELATEERDE KOPPELINGEN</span><span class="sxs-lookup"><span data-stu-id="fb851-207">RELATED LINKS</span></span>

[<span data-ttu-id="fb851-208">about_Quoting_Rules</span><span class="sxs-lookup"><span data-stu-id="fb851-208">about_Quoting_Rules</span></span>](../Microsoft.Powershell.Core/About/about_Quoting_Rules.md)

[<span data-ttu-id="fb851-209">Format-Custom</span><span class="sxs-lookup"><span data-stu-id="fb851-209">Format-Custom</span></span>](Format-Custom.md)

[<span data-ttu-id="fb851-210">Format-List</span><span class="sxs-lookup"><span data-stu-id="fb851-210">Format-List</span></span>](Format-List.md)

[<span data-ttu-id="fb851-211">Format-Table</span><span class="sxs-lookup"><span data-stu-id="fb851-211">Format-Table</span></span>](Format-Table.md)

[<span data-ttu-id="fb851-212">Format-Wide</span><span class="sxs-lookup"><span data-stu-id="fb851-212">Format-Wide</span></span>](Format-Wide.md)
