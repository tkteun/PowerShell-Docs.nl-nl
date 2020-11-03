---
external help file: Microsoft.PowerShell.Utility-help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 01/17/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/format-hex?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Format-Hex
ms.openlocfilehash: 514a66ebee3827de998622a738c75d4f8e0c7279
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/07/2020
ms.locfileid: "93250450"
---
# <span data-ttu-id="f2bd1-103">Format-Hex</span><span class="sxs-lookup"><span data-stu-id="f2bd1-103">Format-Hex</span></span>

## <span data-ttu-id="f2bd1-104">SAMENVATTING</span><span class="sxs-lookup"><span data-stu-id="f2bd1-104">SYNOPSIS</span></span>

<span data-ttu-id="f2bd1-105">Geeft een bestand of andere invoer weer als hexadecimale notatie.</span><span class="sxs-lookup"><span data-stu-id="f2bd1-105">Displays a file or other input as hexadecimal.</span></span>

## <span data-ttu-id="f2bd1-106">SYNTAXIS</span><span class="sxs-lookup"><span data-stu-id="f2bd1-106">SYNTAX</span></span>

### <span data-ttu-id="f2bd1-107">Pad (standaard)</span><span class="sxs-lookup"><span data-stu-id="f2bd1-107">Path (Default)</span></span>

```
Format-Hex [-Path] <string[]> [<CommonParameters>]
```

### <span data-ttu-id="f2bd1-108">LiteralPath</span><span class="sxs-lookup"><span data-stu-id="f2bd1-108">LiteralPath</span></span>

```
Format-Hex -LiteralPath <string[]> [<CommonParameters>]
```

### <span data-ttu-id="f2bd1-109">ByInputObject</span><span class="sxs-lookup"><span data-stu-id="f2bd1-109">ByInputObject</span></span>

```
Format-Hex -InputObject <Object> [-Encoding <string>] [-Raw] [<CommonParameters>]
```

## <span data-ttu-id="f2bd1-110">BESCHRIJVING</span><span class="sxs-lookup"><span data-stu-id="f2bd1-110">DESCRIPTION</span></span>

<span data-ttu-id="f2bd1-111">De `Format-Hex` cmdlet geeft een bestand of andere invoer weer als hexadecimale waarden.</span><span class="sxs-lookup"><span data-stu-id="f2bd1-111">The `Format-Hex` cmdlet displays a file or other input as hexadecimal values.</span></span> <span data-ttu-id="f2bd1-112">Als u de verschuiving van een teken van de uitvoer wilt bepalen, voegt u het nummer aan de linkerkant van de rij toe aan het getal boven aan de kolom voor dat teken.</span><span class="sxs-lookup"><span data-stu-id="f2bd1-112">To determine the offset of a character from the output, add the number at the leftmost of the row to the number at the top of the column for that character.</span></span>

<span data-ttu-id="f2bd1-113">De `Format-Hex` cmdlet kan u helpen bij het bepalen van het bestands type van een beschadigd bestand of een bestand dat mogelijk geen bestands extensie heeft.</span><span class="sxs-lookup"><span data-stu-id="f2bd1-113">The `Format-Hex` cmdlet can help you determine the file type of a corrupted file or a file that might not have a filename extension.</span></span> <span data-ttu-id="f2bd1-114">U kunt deze cmdlet uitvoeren en vervolgens de hexadecimale uitvoer lezen om informatie over het bestand op te halen.</span><span class="sxs-lookup"><span data-stu-id="f2bd1-114">You can run this cmdlet, and then read the hexadecimal output to get file information.</span></span>

<span data-ttu-id="f2bd1-115">Wanneer u `Format-Hex` een bestand gebruikt, negeert de cmdlet nieuwe regel tekens en retourneert de volledige inhoud van een bestand in één teken reeks met de tekens voor de nieuwe regel.</span><span class="sxs-lookup"><span data-stu-id="f2bd1-115">When using `Format-Hex` on a file, the cmdlet ignores newline characters and returns the entire contents of a file in one string with the newline characters preserved.</span></span>

## <span data-ttu-id="f2bd1-116">VOORBEELDEN</span><span class="sxs-lookup"><span data-stu-id="f2bd1-116">EXAMPLES</span></span>

### <span data-ttu-id="f2bd1-117">Voor beeld 1: de hexadecimale weer gave van een teken reeks ophalen</span><span class="sxs-lookup"><span data-stu-id="f2bd1-117">Example 1: Get the hexadecimal representation of a string</span></span>

<span data-ttu-id="f2bd1-118">Met deze opdracht wordt de hexadecimale waarde van een teken reeks geretourneerd.</span><span class="sxs-lookup"><span data-stu-id="f2bd1-118">This command returns the hexadecimal values of a string.</span></span>

```powershell
'Hello World' | Format-Hex
```

```Output
           00 01 02 03 04 05 06 07 08 09 0A 0B 0C 0D 0E 0F

00000000   48 65 6C 6C 6F 20 57 6F 72 6C 64                 Hello World
```

<span data-ttu-id="f2bd1-119">De teken reeks **Hallo wereld** wordt via de pijp lijn naar de `Format-Hex` cmdlet verzonden.</span><span class="sxs-lookup"><span data-stu-id="f2bd1-119">The string **Hello World** is sent down the pipeline to the `Format-Hex` cmdlet.</span></span> <span data-ttu-id="f2bd1-120">De hexadecimale uitvoer van `Format-Hex` bevat de waarden van elk teken in de teken reeks.</span><span class="sxs-lookup"><span data-stu-id="f2bd1-120">The hexadecimal output from `Format-Hex` shows the values of each character in the string.</span></span>

### <span data-ttu-id="f2bd1-121">Voor beeld 2: een bestands type zoeken in hexadecimale uitvoer</span><span class="sxs-lookup"><span data-stu-id="f2bd1-121">Example 2: Find a file type from hexadecimal output</span></span>

<span data-ttu-id="f2bd1-122">In dit voor beeld wordt de hexadecimale uitvoer gebruikt om het bestands type te bepalen.</span><span class="sxs-lookup"><span data-stu-id="f2bd1-122">This example uses the hexadecimal output to determine the file type.</span></span> <span data-ttu-id="f2bd1-123">Met de cmdlet worden het volledige pad van het bestand en de hexadecimale waarden weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="f2bd1-123">The cmdlet displays the file's full path and the hexadecimal values.</span></span>

<span data-ttu-id="f2bd1-124">Als u de volgende opdracht wilt testen, maakt u een kopie van een bestaand PDF-bestand op uw lokale computer en wijzigt u de naam van het gekopieerde bestand in **File. t7f**.</span><span class="sxs-lookup"><span data-stu-id="f2bd1-124">To test the following command, make a copy of an existing PDF file on your local computer and rename the copied file to **File.t7f**.</span></span>

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

<span data-ttu-id="f2bd1-125">De `Format-Hex` cmdlet gebruikt de para meter **Path** om een bestands naam op te geven in de huidige map `File.t7f` .</span><span class="sxs-lookup"><span data-stu-id="f2bd1-125">The `Format-Hex` cmdlet uses the **Path** parameter to specify a filename in the current directory, `File.t7f`.</span></span> <span data-ttu-id="f2bd1-126">De bestands extensie `.t7f` is ongebruikelijk, maar in de hexadecimale uitvoer `%PDF` ziet u dat het een PDF-bestand is.</span><span class="sxs-lookup"><span data-stu-id="f2bd1-126">The file extension `.t7f` is uncommon, but the hexadecimal output `%PDF` shows that it is a PDF file.</span></span>

### <span data-ttu-id="f2bd1-127">Voor beeld 3: onbewerkte hexadecimale uitvoer weer geven</span><span class="sxs-lookup"><span data-stu-id="f2bd1-127">Example 3: Display raw hexadecimal output</span></span>

<span data-ttu-id="f2bd1-128">Standaard `Format-Hex` kiest u voor een compacte uitvoer van numerieke gegevens typen: single-byte of dubbel-byte reeksen worden gebruikt als de waarde klein genoeg is.</span><span class="sxs-lookup"><span data-stu-id="f2bd1-128">By default `Format-Hex` opts for compact output of numeric data types: single-byte or double-byte sequences are used if the value is small enough.</span></span> <span data-ttu-id="f2bd1-129">Met de para meter **RAW** wordt dit gedrag gedeactiveerd.</span><span class="sxs-lookup"><span data-stu-id="f2bd1-129">The **Raw** parameter deactivates this behavior.</span></span>

```
PS> 1,2,3,1000 | Format-Hex

           Path:

           00 01 02 03 04 05 06 07 08 09 0A 0B 0C 0D 0E 0F

00000000   01 02 03 E8 03                                   ...è.


PS> 1,2,3,1000 | Format-Hex -Raw

           Path:

           00 01 02 03 04 05 06 07 08 09 0A 0B 0C 0D 0E 0F

00000000   01 00 00 00 02 00 00 00 03 00 00 00 E8 03 00 00  ............è...
```

<span data-ttu-id="f2bd1-130">Let op het verschil in uitvoer.</span><span class="sxs-lookup"><span data-stu-id="f2bd1-130">Notice the difference in output.</span></span> <span data-ttu-id="f2bd1-131">De **onbewerkte** para meter geeft de getallen weer als 4-byte waarden, True voor hun **Int32** -typen.</span><span class="sxs-lookup"><span data-stu-id="f2bd1-131">The **Raw** parameter displays the numbers as 4-byte values, true to their **Int32** types.</span></span>

## <span data-ttu-id="f2bd1-132">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="f2bd1-132">PARAMETERS</span></span>

### <span data-ttu-id="f2bd1-133">-Encoding</span><span class="sxs-lookup"><span data-stu-id="f2bd1-133">-Encoding</span></span>

<span data-ttu-id="f2bd1-134">Hiermee geeft u de code ring van de uitvoer op.</span><span class="sxs-lookup"><span data-stu-id="f2bd1-134">Specifies the encoding of the output.</span></span> <span data-ttu-id="f2bd1-135">Dit is alleen van toepassing op `[string]` invoer.</span><span class="sxs-lookup"><span data-stu-id="f2bd1-135">This only applies to `[string]` input.</span></span> <span data-ttu-id="f2bd1-136">De para meter heeft geen invloed op numerieke typen.</span><span class="sxs-lookup"><span data-stu-id="f2bd1-136">The parameter has no effect on numeric types.</span></span> <span data-ttu-id="f2bd1-137">De standaardwaarde is `ASCII`.</span><span class="sxs-lookup"><span data-stu-id="f2bd1-137">The default value is `ASCII`.</span></span>

<span data-ttu-id="f2bd1-138">De acceptabele waarden voor deze para meter zijn als volgt:</span><span class="sxs-lookup"><span data-stu-id="f2bd1-138">The acceptable values for this parameter are as follows:</span></span>

- <span data-ttu-id="f2bd1-139">`Ascii` Maakt gebruik van ASCII-tekenset (7-bits).</span><span class="sxs-lookup"><span data-stu-id="f2bd1-139">`Ascii` Uses ASCII (7-bit) character set.</span></span>
- <span data-ttu-id="f2bd1-140">`BigEndianUnicode` Maakt gebruik van UTF-16 met de byte volgorde big endian.</span><span class="sxs-lookup"><span data-stu-id="f2bd1-140">`BigEndianUnicode` Uses UTF-16 with the big-endian byte order.</span></span>
- <span data-ttu-id="f2bd1-141">`Unicode` Maakt gebruik van UTF-16 met de byte volgorde little endian.</span><span class="sxs-lookup"><span data-stu-id="f2bd1-141">`Unicode` Uses UTF-16 with the little-endian byte order.</span></span>
- <span data-ttu-id="f2bd1-142">`UTF7` Maakt gebruik van UTF-7.</span><span class="sxs-lookup"><span data-stu-id="f2bd1-142">`UTF7` Uses UTF-7.</span></span>
- <span data-ttu-id="f2bd1-143">`UTF8` Maakt gebruik van UTF-8.</span><span class="sxs-lookup"><span data-stu-id="f2bd1-143">`UTF8` Uses UTF-8.</span></span>
- <span data-ttu-id="f2bd1-144">`UTF32` Maakt gebruik van UTF-32 met de byte volgorde little endian.</span><span class="sxs-lookup"><span data-stu-id="f2bd1-144">`UTF32` Uses UTF-32 with the little-endian byte order.</span></span>

<span data-ttu-id="f2bd1-145">Niet-ASCII-tekens in de invoer worden uitgevoerd als letterlijke `?` tekens als gevolg van gegevens verlies.</span><span class="sxs-lookup"><span data-stu-id="f2bd1-145">Non-ASCII characters in the input are output as literal `?` characters resulting in a loss of information.</span></span>

```yaml
Type: System.String
Parameter Sets: ByInputObject
Aliases:
Accepted values: ASCII, BigEndianUnicode, Unicode, UTF7, UTF8, UTF32

Required: False
Position: Named
Default value: ASCII
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="f2bd1-146">-Input object</span><span class="sxs-lookup"><span data-stu-id="f2bd1-146">-InputObject</span></span>

<span data-ttu-id="f2bd1-147">Wordt gebruikt voor de invoer van de pijp lijn.</span><span class="sxs-lookup"><span data-stu-id="f2bd1-147">Used for pipeline input.</span></span> <span data-ttu-id="f2bd1-148">Pijplijn invoer ondersteunt alleen bepaalde scalaire typen en `[system.io.fileinfo]` instanties voor sluizen van `Get-ChildItem` .</span><span class="sxs-lookup"><span data-stu-id="f2bd1-148">Pipeline input supports only certain scalar types and `[system.io.fileinfo]` instances for piping from `Get-ChildItem`.</span></span>

<span data-ttu-id="f2bd1-149">De ondersteunde scalaire typen zijn:</span><span class="sxs-lookup"><span data-stu-id="f2bd1-149">The supported scalar types are:</span></span>

- `[string]`
- `[byte]`
- <span data-ttu-id="f2bd1-150">`[int]`, `[int32]`</span><span class="sxs-lookup"><span data-stu-id="f2bd1-150">`[int]`, `[int32]`</span></span>
- <span data-ttu-id="f2bd1-151">`[long]`, `[int64]`</span><span class="sxs-lookup"><span data-stu-id="f2bd1-151">`[long]`, `[int64]`</span></span>

```yaml
Type: System.Object
Parameter Sets: ByInputObject
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="f2bd1-152">-LiteralPath</span><span class="sxs-lookup"><span data-stu-id="f2bd1-152">-LiteralPath</span></span>

<span data-ttu-id="f2bd1-153">Hiermee geeft u het volledige pad naar een bestand.</span><span class="sxs-lookup"><span data-stu-id="f2bd1-153">Specifies the complete path to a file.</span></span> <span data-ttu-id="f2bd1-154">De waarde van **LiteralPath** wordt precies zo gebruikt als deze wordt getypt.</span><span class="sxs-lookup"><span data-stu-id="f2bd1-154">The value of **LiteralPath** is used exactly as it is typed.</span></span>
<span data-ttu-id="f2bd1-155">Deze para meter accepteert geen joker tekens.</span><span class="sxs-lookup"><span data-stu-id="f2bd1-155">This parameter does not accept wildcard characters.</span></span> <span data-ttu-id="f2bd1-156">Als u meerdere paden naar bestanden wilt opgeven, scheidt u de paden met een komma.</span><span class="sxs-lookup"><span data-stu-id="f2bd1-156">To specify multiple paths to files, separate the paths with a comma.</span></span> <span data-ttu-id="f2bd1-157">Als de para meter **LiteralPath** escape-tekens bevat, plaatst u het pad tussen enkele aanhalings tekens.</span><span class="sxs-lookup"><span data-stu-id="f2bd1-157">If the **LiteralPath** parameter includes escape characters, enclose the path in single quotation marks.</span></span> <span data-ttu-id="f2bd1-158">Power shell interpreteert geen tekens in één aanhalings teken reeks als escape-reeksen.</span><span class="sxs-lookup"><span data-stu-id="f2bd1-158">PowerShell does not interpret any characters in a single quoted string as escape sequences.</span></span> <span data-ttu-id="f2bd1-159">Zie [about_Quoting_Rules](../Microsoft.Powershell.Core/About/about_Quoting_Rules.md)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="f2bd1-159">For more information, see [about_Quoting_Rules](../Microsoft.Powershell.Core/About/about_Quoting_Rules.md).</span></span>

```yaml
Type: System.String[]
Parameter Sets: LiteralPath
Aliases: PSPath

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="f2bd1-160">-Path</span><span class="sxs-lookup"><span data-stu-id="f2bd1-160">-Path</span></span>

<span data-ttu-id="f2bd1-161">Hiermee geeft u het pad naar de bestanden.</span><span class="sxs-lookup"><span data-stu-id="f2bd1-161">Specifies the path to files.</span></span> <span data-ttu-id="f2bd1-162">Gebruik een punt ( `.` ) om de huidige locatie op te geven.</span><span class="sxs-lookup"><span data-stu-id="f2bd1-162">Use a dot (`.`) to specify the current location.</span></span> <span data-ttu-id="f2bd1-163">Het Joker teken ( `*` ) wordt geaccepteerd en kan worden gebruikt om alle items op een locatie op te geven.</span><span class="sxs-lookup"><span data-stu-id="f2bd1-163">The wildcard character (`*`) is accepted and can be used to specify all the items in a location.</span></span> <span data-ttu-id="f2bd1-164">Als de para meter **Path** escape tekens bevat, plaatst u het pad tussen enkele aanhalings tekens.</span><span class="sxs-lookup"><span data-stu-id="f2bd1-164">If the **Path** parameter includes escape characters, enclose the path in single quotation marks.</span></span> <span data-ttu-id="f2bd1-165">Als u meerdere paden naar bestanden wilt opgeven, scheidt u de paden met een komma.</span><span class="sxs-lookup"><span data-stu-id="f2bd1-165">To specify multiple paths to files, separate the paths with a comma.</span></span>

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

### <span data-ttu-id="f2bd1-166">-RAW</span><span class="sxs-lookup"><span data-stu-id="f2bd1-166">-Raw</span></span>

<span data-ttu-id="f2bd1-167">Standaard `Format-Hex` kiest u voor een compacte uitvoer van numerieke gegevens typen: single-byte of dubbel-byte reeksen worden gebruikt als de waarde klein genoeg is.</span><span class="sxs-lookup"><span data-stu-id="f2bd1-167">By default `Format-Hex` opts for compact output of numeric data types: single-byte or double-byte sequences are used if the value is small enough.</span></span> <span data-ttu-id="f2bd1-168">Met de para meter **RAW** wordt dit gedrag gedeactiveerd.</span><span class="sxs-lookup"><span data-stu-id="f2bd1-168">The **Raw** parameter deactivates this behavior.</span></span>

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

### <span data-ttu-id="f2bd1-169">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="f2bd1-169">CommonParameters</span></span>

<span data-ttu-id="f2bd1-170">Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="f2bd1-170">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="f2bd1-171">Zie [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="f2bd1-171">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="f2bd1-172">INVOER</span><span class="sxs-lookup"><span data-stu-id="f2bd1-172">INPUTS</span></span>

### <span data-ttu-id="f2bd1-173">System. String</span><span class="sxs-lookup"><span data-stu-id="f2bd1-173">System.String</span></span>

<span data-ttu-id="f2bd1-174">U kunt een teken reeks door sluizen naar deze cmdlet.</span><span class="sxs-lookup"><span data-stu-id="f2bd1-174">You can pipe a string to this cmdlet.</span></span>

## <span data-ttu-id="f2bd1-175">UITVOER</span><span class="sxs-lookup"><span data-stu-id="f2bd1-175">OUTPUTS</span></span>

### <span data-ttu-id="f2bd1-176">Micro soft. Power shell. commands. ByteCollection</span><span class="sxs-lookup"><span data-stu-id="f2bd1-176">Microsoft.PowerShell.Commands.ByteCollection</span></span>

<span data-ttu-id="f2bd1-177">Met deze cmdlet wordt een **ByteCollection** geretourneerd.</span><span class="sxs-lookup"><span data-stu-id="f2bd1-177">This cmdlet returns a **ByteCollection**.</span></span> <span data-ttu-id="f2bd1-178">Dit object vertegenwoordigt een verzameling van bytes.</span><span class="sxs-lookup"><span data-stu-id="f2bd1-178">This object represents a collection of bytes.</span></span> <span data-ttu-id="f2bd1-179">Het bevat methoden die het verzamelen van bytes converteren naar een teken reeks die is opgemaakt als elke regel van uitvoer die wordt geretourneerd door `Format-Hex` .</span><span class="sxs-lookup"><span data-stu-id="f2bd1-179">It includes methods that convert the collection of bytes to a string formatted like each line of output returned by `Format-Hex`.</span></span> <span data-ttu-id="f2bd1-180">Als u de para meter **Path** of **LiteralPath** opgeeft, bevat het object ook het pad van het bestand dat elke byte bevat.</span><span class="sxs-lookup"><span data-stu-id="f2bd1-180">If you specify the **Path** or **LiteralPath** parameter, the object also contains the path of the file that contains each byte.</span></span>

## <span data-ttu-id="f2bd1-181">OPMERKINGEN</span><span class="sxs-lookup"><span data-stu-id="f2bd1-181">NOTES</span></span>

<span data-ttu-id="f2bd1-182">De meest rechtse kolom van uitvoer probeert de bytes als tekens weer te geven:</span><span class="sxs-lookup"><span data-stu-id="f2bd1-182">The right-most column of output tries to render the bytes as characters:</span></span>

<span data-ttu-id="f2bd1-183">Over het algemeen wordt elke byte geïnterpreteerd als een Unicode-code punt, wat betekent dat:</span><span class="sxs-lookup"><span data-stu-id="f2bd1-183">Generally, each byte is interpreted as a Unicode code point, which means that:</span></span>

- <span data-ttu-id="f2bd1-184">Afdruk bare ASCII-tekens worden altijd correct weer gegeven</span><span class="sxs-lookup"><span data-stu-id="f2bd1-184">Printable ASCII characters are always rendered correctly</span></span>
- <span data-ttu-id="f2bd1-185">Multi-byte UTF-8 tekens worden nooit correct weer gegeven</span><span class="sxs-lookup"><span data-stu-id="f2bd1-185">Multi-byte UTF-8 characters never render correctly</span></span>
- <span data-ttu-id="f2bd1-186">UTF-16-tekens worden alleen correct weer gegeven als er een hoge byte is `NUL` .</span><span class="sxs-lookup"><span data-stu-id="f2bd1-186">UTF-16 characters render correctly only if their high-order byte happens be `NUL`.</span></span>

## <span data-ttu-id="f2bd1-187">GERELATEERDE KOPPELINGEN</span><span class="sxs-lookup"><span data-stu-id="f2bd1-187">RELATED LINKS</span></span>

[<span data-ttu-id="f2bd1-188">about_Quoting_Rules</span><span class="sxs-lookup"><span data-stu-id="f2bd1-188">about_Quoting_Rules</span></span>](../Microsoft.Powershell.Core/About/about_Quoting_Rules.md)

[<span data-ttu-id="f2bd1-189">Format-Custom</span><span class="sxs-lookup"><span data-stu-id="f2bd1-189">Format-Custom</span></span>](Format-Custom.md)

[<span data-ttu-id="f2bd1-190">Format-List</span><span class="sxs-lookup"><span data-stu-id="f2bd1-190">Format-List</span></span>](Format-List.md)

[<span data-ttu-id="f2bd1-191">Format-Table</span><span class="sxs-lookup"><span data-stu-id="f2bd1-191">Format-Table</span></span>](Format-Table.md)

[<span data-ttu-id="f2bd1-192">Format-Wide</span><span class="sxs-lookup"><span data-stu-id="f2bd1-192">Format-Wide</span></span>](Format-Wide.md)
