---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 08/19/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/get-content?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-Content
ms.openlocfilehash: 0140691bc0b01fff803f0efdf81980c621e1150d
ms.sourcegitcommit: 9a8bb1b459b5939c95e1f6d9499fcb13d01a58c4
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 08/25/2020
ms.locfileid: "93251849"
---
# <span data-ttu-id="c5c00-103">Get-Content</span><span class="sxs-lookup"><span data-stu-id="c5c00-103">Get-Content</span></span>

## <span data-ttu-id="c5c00-104">SAMENVATTING</span><span class="sxs-lookup"><span data-stu-id="c5c00-104">SYNOPSIS</span></span>
<span data-ttu-id="c5c00-105">Hiermee wordt de inhoud van het item op de opgegeven locatie opgehaald.</span><span class="sxs-lookup"><span data-stu-id="c5c00-105">Gets the content of the item at the specified location.</span></span>

## <span data-ttu-id="c5c00-106">SYNTAXIS</span><span class="sxs-lookup"><span data-stu-id="c5c00-106">SYNTAX</span></span>

### <span data-ttu-id="c5c00-107">Pad (standaard)</span><span class="sxs-lookup"><span data-stu-id="c5c00-107">Path (Default)</span></span>

```
Get-Content [-ReadCount <Int64>] [-TotalCount <Int64>] [-Tail <Int32>] [-Path] <String[]>
 [-Filter <String>] [-Include <String[]>] [-Exclude <String[]>] [-Force] [-Credential <PSCredential>]
 [-Delimiter <String>] [-Wait] [-Raw] [-Encoding <Encoding>] [-AsByteStream] [-Stream <String>]
 [<CommonParameters>]
```

### <span data-ttu-id="c5c00-108">LiteralPath</span><span class="sxs-lookup"><span data-stu-id="c5c00-108">LiteralPath</span></span>

```
Get-Content [-ReadCount <Int64>] [-TotalCount <Int64>] [-Tail <Int32>] -LiteralPath <String[]>
 [-Filter <String>] [-Include <String[]>] [-Exclude <String[]>] [-Force] [-Credential <PSCredential>]
 [-Delimiter <String>] [-Wait] [-Raw] [-Encoding <Encoding>] [-AsByteStream] [-Stream <String>]
 [<CommonParameters>]
```

## <span data-ttu-id="c5c00-109">BESCHRIJVING</span><span class="sxs-lookup"><span data-stu-id="c5c00-109">DESCRIPTION</span></span>

<span data-ttu-id="c5c00-110">`Get-Content`Met de cmdlet wordt de inhoud van het item opgehaald op de locatie die is opgegeven door het pad, zoals de tekst in een bestand of de inhoud van een functie.</span><span class="sxs-lookup"><span data-stu-id="c5c00-110">The `Get-Content` cmdlet gets the content of the item at the location specified by the path, such as the text in a file or the content of a function.</span></span> <span data-ttu-id="c5c00-111">Voor bestanden wordt de inhoud één regel tegelijk gelezen en wordt een verzameling objecten geretourneerd, die elk een regel met inhoud vertegenwoordigt.</span><span class="sxs-lookup"><span data-stu-id="c5c00-111">For files, the content is read one line at a time and returns a collection of objects, each of which represents a line of content.</span></span>

<span data-ttu-id="c5c00-112">Vanaf Power Shell 3,0 `Get-Content` kan ook een opgegeven aantal regels worden opgehaald vanaf het begin of einde van een item.</span><span class="sxs-lookup"><span data-stu-id="c5c00-112">Beginning in PowerShell 3.0, `Get-Content` can also get a specified number of lines from the beginning or end of an item.</span></span>

## <span data-ttu-id="c5c00-113">VOORBEELDEN</span><span class="sxs-lookup"><span data-stu-id="c5c00-113">EXAMPLES</span></span>

### <span data-ttu-id="c5c00-114">Voor beeld 1: de inhoud van een tekst bestand ophalen</span><span class="sxs-lookup"><span data-stu-id="c5c00-114">Example 1: Get the content of a text file</span></span>

<span data-ttu-id="c5c00-115">In dit voor beeld wordt de inhoud van een bestand in de huidige map opgehaald.</span><span class="sxs-lookup"><span data-stu-id="c5c00-115">This example gets the content of a file in the current directory.</span></span> <span data-ttu-id="c5c00-116">Het `LineNumbers.txt` bestand bevat 100 regels in de indeling. **Dit is regel X** en wordt in verschillende voor beelden gebruikt.</span><span class="sxs-lookup"><span data-stu-id="c5c00-116">The `LineNumbers.txt` file contains 100 lines in the format, **This is Line X** and is used in several examples.</span></span>

```powershell
1..100 | ForEach-Object { Add-Content -Path .\LineNumbers.txt -Value "This is line $_." }
Get-Content -Path .\LineNumbers.txt
```

```Output
This is Line 1
This is Line 2
...
This is line 99.
This is line 100.
```

<span data-ttu-id="c5c00-117">De matrix waarden 1-100 worden in de pijp lijn naar de `ForEach-Object` cmdlet verzonden.</span><span class="sxs-lookup"><span data-stu-id="c5c00-117">The array values 1-100 are sent down the pipeline to the `ForEach-Object` cmdlet.</span></span> <span data-ttu-id="c5c00-118">`ForEach-Object` maakt gebruik van een script blok met de `Add-Content` cmdlet om het bestand te maken `LineNumbers.txt` .</span><span class="sxs-lookup"><span data-stu-id="c5c00-118">`ForEach-Object` uses a script block with the `Add-Content` cmdlet to create the `LineNumbers.txt` file.</span></span> <span data-ttu-id="c5c00-119">De variabele `$_` vertegenwoordigt de matrix waarden wanneer elk object wordt verzonden naar de pijp lijn.</span><span class="sxs-lookup"><span data-stu-id="c5c00-119">The variable `$_` represents the array values as each object is sent down the pipeline.</span></span> <span data-ttu-id="c5c00-120">De `Get-Content` cmdlet gebruikt de para meter **Path** om het bestand op te geven `LineNumbers.txt` en geeft de inhoud weer in de Power shell-console.</span><span class="sxs-lookup"><span data-stu-id="c5c00-120">The `Get-Content` cmdlet uses the **Path** parameter to specify the `LineNumbers.txt` file and displays the content in the PowerShell console.</span></span>

### <span data-ttu-id="c5c00-121">Voor beeld 2: het aantal regels dat Get-Content retourneert, beperken</span><span class="sxs-lookup"><span data-stu-id="c5c00-121">Example 2: Limit the number of lines Get-Content returns</span></span>

<span data-ttu-id="c5c00-122">Met deze opdracht worden de eerste vijf regels van een bestand opgehaald.</span><span class="sxs-lookup"><span data-stu-id="c5c00-122">This command gets the first five lines of a file.</span></span> <span data-ttu-id="c5c00-123">De para meter **totalCount** wordt gebruikt voor het ophalen van de eerste vijf regels met inhoud.</span><span class="sxs-lookup"><span data-stu-id="c5c00-123">The **TotalCount** parameter is used to gets the first five lines of content.</span></span> <span data-ttu-id="c5c00-124">In dit voor beeld wordt het `LineNumbers.txt` bestand gebruikt dat in voor beeld 1 is gemaakt.</span><span class="sxs-lookup"><span data-stu-id="c5c00-124">This example uses the `LineNumbers.txt` file that was created in Example 1.</span></span>

```powershell
Get-Content -Path .\LineNumbers.txt -TotalCount 5
```

```Output
This is Line 1
This is Line 2
This is Line 3
This is Line 4
This is Line 5
```

### <span data-ttu-id="c5c00-125">Voor beeld 3: een specifieke regel met inhoud ophalen uit een tekst bestand</span><span class="sxs-lookup"><span data-stu-id="c5c00-125">Example 3: Get a specific line of content from a text file</span></span>

<span data-ttu-id="c5c00-126">Met deze opdracht wordt een specifiek aantal regels van een bestand opgehaald en wordt vervolgens alleen de laatste regel van die inhoud weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="c5c00-126">This command gets a specific number of lines from a file and then displays only the last line of that content.</span></span> <span data-ttu-id="c5c00-127">De para meter **totalCount** haalt de eerste 25 regels inhoud op.</span><span class="sxs-lookup"><span data-stu-id="c5c00-127">The **TotalCount** parameter gets the first 25 lines of content.</span></span> <span data-ttu-id="c5c00-128">In dit voor beeld wordt het `LineNumbers.txt` bestand gebruikt dat in voor beeld 1 is gemaakt.</span><span class="sxs-lookup"><span data-stu-id="c5c00-128">This example uses the `LineNumbers.txt` file that was created in Example 1.</span></span>

```powershell
(Get-Content -Path .\LineNumbers.txt -TotalCount 25)[-1]
```

```Output
This is Line 25
```

<span data-ttu-id="c5c00-129">De `Get-Content` opdracht wordt tussen haakjes geplaatst, zodat de opdracht is voltooid voordat u naar de volgende stap gaat.</span><span class="sxs-lookup"><span data-stu-id="c5c00-129">The `Get-Content` command is wrapped in parentheses so that the command completes before going to the next step.</span></span> <span data-ttu-id="c5c00-130">`Get-Content`retourneert een matrix met lijnen, Hiermee kunt u de index notatie toevoegen na het haakje om een specifiek regel nummer op te halen.</span><span class="sxs-lookup"><span data-stu-id="c5c00-130">`Get-Content`returns an array of lines, this allows you to add the index notation after the parenthesis to retrieve a specific line number.</span></span> <span data-ttu-id="c5c00-131">In dit geval geeft de `[-1]` index de laatste index in de geretourneerde matrix van 25 opgehaalde regels.</span><span class="sxs-lookup"><span data-stu-id="c5c00-131">In this case, the `[-1]` index specifies the last index in the returned array of 25 retrieved lines.</span></span>

### <span data-ttu-id="c5c00-132">Voor beeld 4: de laatste regel van een tekst bestand ophalen</span><span class="sxs-lookup"><span data-stu-id="c5c00-132">Example 4: Get the last line of a text file</span></span>

<span data-ttu-id="c5c00-133">Met deze opdracht wordt de eerste regel en de laatste regel van de inhoud van een bestand opgehaald.</span><span class="sxs-lookup"><span data-stu-id="c5c00-133">This command gets the first line and last line of content from a file.</span></span> <span data-ttu-id="c5c00-134">In dit voor beeld wordt het `LineNumbers.txt` bestand gebruikt dat in voor beeld 1 is gemaakt.</span><span class="sxs-lookup"><span data-stu-id="c5c00-134">This example uses the `LineNumbers.txt` file that was created in Example 1.</span></span>

```powershell
Get-Item -Path .\LineNumbers.txt | Get-Content -Tail 1
```

```Output
This is Line 100
```

<span data-ttu-id="c5c00-135">In dit voor beeld wordt de `Get-Item` cmdlet gebruikt om te demonstreren dat u bestanden in de `Get-Content` para meter kunt sluizen.</span><span class="sxs-lookup"><span data-stu-id="c5c00-135">This example uses the `Get-Item` cmdlet to demonstrate that you can pipe files into the `Get-Content` parameter.</span></span> <span data-ttu-id="c5c00-136">De para meter **staart** haalt de laatste regel van het bestand op.</span><span class="sxs-lookup"><span data-stu-id="c5c00-136">The **Tail** parameter gets the last line of the file.</span></span> <span data-ttu-id="c5c00-137">Deze methode is sneller dan alle regels op te halen en de `[-1]` index notatie te gebruiken.</span><span class="sxs-lookup"><span data-stu-id="c5c00-137">This method is faster than retrieving all of the lines and using the `[-1]` index notation.</span></span>

### <span data-ttu-id="c5c00-138">Voor beeld 5: de inhoud van een alternatieve gegevens stroom ophalen</span><span class="sxs-lookup"><span data-stu-id="c5c00-138">Example 5: Get the content of an alternate data stream</span></span>

<span data-ttu-id="c5c00-139">In dit voor beeld wordt beschreven hoe u de para meter **Stream** kunt gebruiken om de inhoud van een alternatieve gegevens stroom op te halen voor bestanden die zijn opgeslagen op een Windows NTFS volume.</span><span class="sxs-lookup"><span data-stu-id="c5c00-139">This example describes how to use the **Stream** parameter to get the content of an alternate data stream for files stored on a Windows NTFS volume.</span></span> <span data-ttu-id="c5c00-140">In dit voor beeld `Set-Content` wordt de cmdlet gebruikt voor het maken van voorbeeld inhoud in een bestand met de naam `Stream.txt` .</span><span class="sxs-lookup"><span data-stu-id="c5c00-140">In this example, the `Set-Content` cmdlet is used to create sample content in a file named `Stream.txt`.</span></span>

```powershell
Set-Content -Path .\Stream.txt -Value 'This is the content of the Stream.txt file'
# Specify a wildcard to the Stream parameter to display all streams of the recently created file.
Get-Item -Path .\Stream.txt -Stream *
```

```Output
PSPath        : Microsoft.PowerShell.Core\FileSystem::C:\Test\Stream.txt::$DATA
PSParentPath  : Microsoft.PowerShell.Core\FileSystem::C:\Test
PSChildName   : Stream.txt::$DATA
PSDrive       : C
PSProvider    : Microsoft.PowerShell.Core\FileSystem
PSIsContainer : False
FileName      : C:\Test\Stream.txt
Stream        : :$DATA
Length        : 44
```

```powershell
# Retrieve the content of the primary, or $DATA stream.
Get-Content -Path .\Stream.txt -Stream $DATA
```

```Output
This is the content of the Stream.txt file
```

```powershell
# Use the Stream parameter of Add-Content to create a new Stream containing sample content.
Add-Content -Path .\Stream.txt -Stream NewStream -Value 'Added a stream named NewStream to Stream.txt'
# Use Get-Item to verify the stream was created.
Get-Item -Path .\Stream.txt -Stream *
```

```Output
PSPath        : Microsoft.PowerShell.Core\FileSystem::C:\Test\Stream.txt::$DATA
PSParentPath  : Microsoft.PowerShell.Core\FileSystem::C:\Test
PSChildName   : Stream.txt::$DATA
PSDrive       : C
PSProvider    : Microsoft.PowerShell.Core\FileSystem
PSIsContainer : False
FileName      : C:\Test\Stream.txt
Stream        : :$DATA
Length        : 44

PSPath        : Microsoft.PowerShell.Core\FileSystem::C:\Test\Stream.txt:NewStream
PSParentPath  : Microsoft.PowerShell.Core\FileSystem::C:\Test
PSChildName   : Stream.txt:NewStream
PSDrive       : C
PSProvider    : Microsoft.PowerShell.Core\FileSystem
PSIsContainer : False
FileName      : C:\Test\Stream.txt
Stream        : NewStream
Length        : 46
```

```powershell
# Retrieve the content of your newly created Stream.
Get-Content -Path .\Stream.txt -Stream NewStream
```

```Output
Added a stream named NewStream to Stream.txt
```

<span data-ttu-id="c5c00-141">De **Stream** -para meter is een dynamische para meter van de [File System Provider](../microsoft.powershell.core/about/about_filesystem_provider.md#stream-systemstring).</span><span class="sxs-lookup"><span data-stu-id="c5c00-141">The **Stream** parameter is a dynamic parameter of the [FileSystem provider](../microsoft.powershell.core/about/about_filesystem_provider.md#stream-systemstring).</span></span>
<span data-ttu-id="c5c00-142">Standaard worden `Get-Content` alleen gegevens opgehaald uit de primaire of `$DATA` Stream.</span><span class="sxs-lookup"><span data-stu-id="c5c00-142">By default `Get-Content` only retrieves data from the primary, or `$DATA` stream.</span></span> <span data-ttu-id="c5c00-143">**Stromen** kunnen worden gebruikt voor het opslaan van verborgen gegevens zoals kenmerken, beveiligings instellingen of andere gegevens.</span><span class="sxs-lookup"><span data-stu-id="c5c00-143">**Streams** can be used to store hidden data such as attributes, security settings, or other data.</span></span>

### <span data-ttu-id="c5c00-144">Voor beeld 6: onbewerkte inhoud ophalen</span><span class="sxs-lookup"><span data-stu-id="c5c00-144">Example 6: Get raw content</span></span>

<span data-ttu-id="c5c00-145">Met de opdrachten in dit voor beeld wordt de inhoud van een bestand als één teken reeks opgehaald, in plaats van een matrix met teken reeksen.</span><span class="sxs-lookup"><span data-stu-id="c5c00-145">The commands in this example get the contents of a file as one string, instead of an array of strings.</span></span> <span data-ttu-id="c5c00-146">Standaard wordt, zonder de **onbewerkte** dynamische para meter, de inhoud geretourneerd als een matrix met teken reeksen die zijn gescheiden door een nieuwe regel.</span><span class="sxs-lookup"><span data-stu-id="c5c00-146">By default, without the **Raw** dynamic parameter, content is returned as an array of newline-delimited strings.</span></span> <span data-ttu-id="c5c00-147">In dit voor beeld wordt het `LineNumbers.txt` bestand gebruikt dat in het voor beeld is gemaakt</span><span class="sxs-lookup"><span data-stu-id="c5c00-147">This example uses the `LineNumbers.txt` file that was created in Example</span></span>
1.

```powershell
$raw = Get-Content -Path .\LineNumbers.txt -Raw
$lines = Get-Content -Path .\LineNumbers.txt
Write-Host "Raw contains $($raw.Count) lines."
Write-Host "Lines contains $($lines.Count) lines."
```

```Output
Raw contains 1 lines.
Lines contains 100 lines.
```

### <span data-ttu-id="c5c00-148">Voor beeld 7: filters gebruiken met Get-Content</span><span class="sxs-lookup"><span data-stu-id="c5c00-148">Example 7: Use Filters with Get-Content</span></span>

<span data-ttu-id="c5c00-149">U kunt een filter opgeven voor de `Get-Content` cmdlet.</span><span class="sxs-lookup"><span data-stu-id="c5c00-149">You can specify a filter to the `Get-Content` cmdlet.</span></span> <span data-ttu-id="c5c00-150">Wanneer u filters gebruikt om de para meter **Path** te kwalificeren, moet u een asterisk ( `*` ) toevoegen om de inhoud van het pad aan te geven.</span><span class="sxs-lookup"><span data-stu-id="c5c00-150">When using filters to qualify the **Path** parameter, you need to include a trailing asterisk (`*`) to indicate the contents of the path.</span></span>

<span data-ttu-id="c5c00-151">Met de volgende opdracht wordt de inhoud van alle `*.log` bestanden in de `C:\Temp` map opgehaald.</span><span class="sxs-lookup"><span data-stu-id="c5c00-151">The following command gets the content of all `*.log` files in the `C:\Temp` directory.</span></span>

```powershell
Get-Content -Path C:\Temp\* -Filter *.log
```

### <span data-ttu-id="c5c00-152">Voor beeld 8: de bestands inhoud als een byte matrix ophalen</span><span class="sxs-lookup"><span data-stu-id="c5c00-152">Example 8: Get file contents as a byte array</span></span>

<span data-ttu-id="c5c00-153">In dit voor beeld ziet u hoe u de inhoud van een bestand als `[byte[]]` één object kunt ophalen.</span><span class="sxs-lookup"><span data-stu-id="c5c00-153">This example demonstrates how to get the contents of a file as a `[byte[]]` as a single object.</span></span>

```powershell
$byteArray = Get-Content -Path C:\temp\test.txt -AsByteStream -Raw
Get-Member -InputObject $bytearray
```

```Output
   TypeName: System.Byte[]

Name           MemberType            Definition
----           ----------            ----------
Count          AliasProperty         Count = Length
Add            Method                int IList.Add(System.Object value)
```

<span data-ttu-id="c5c00-154">De eerste opdracht gebruikt de para meter **AsByteStream** om de stroom van bytes uit het bestand op te halen.</span><span class="sxs-lookup"><span data-stu-id="c5c00-154">The first command uses the **AsByteStream** parameter to get the stream of bytes from the file.</span></span>
<span data-ttu-id="c5c00-155">De **onbewerkte** para meter zorgt ervoor dat de bytes worden geretourneerd als een `[System.Byte[]]` .</span><span class="sxs-lookup"><span data-stu-id="c5c00-155">The **Raw** parameter ensures that the bytes are returned as a `[System.Byte[]]`.</span></span> <span data-ttu-id="c5c00-156">Als de **onbewerkte** para meter ontbreekt, is de geretourneerde waarde een stroom van bytes, die wordt geïnterpreteerd door Power shell als `[System.Object[]]` .</span><span class="sxs-lookup"><span data-stu-id="c5c00-156">If the **Raw** parameter was absent, the return value is a stream of bytes, which is interpreted by PowerShell as `[System.Object[]]`.</span></span>

## <span data-ttu-id="c5c00-157">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="c5c00-157">PARAMETERS</span></span>

### <span data-ttu-id="c5c00-158">-Path</span><span class="sxs-lookup"><span data-stu-id="c5c00-158">-Path</span></span>

<span data-ttu-id="c5c00-159">Hiermee geeft u het pad op naar een item waarmee `Get-Content` de inhoud wordt opgehaald.</span><span class="sxs-lookup"><span data-stu-id="c5c00-159">Specifies the path to an item where `Get-Content` gets the content.</span></span> <span data-ttu-id="c5c00-160">Joker tekens zijn toegestaan.</span><span class="sxs-lookup"><span data-stu-id="c5c00-160">Wildcard characters are permitted.</span></span> <span data-ttu-id="c5c00-161">De paden moeten paden naar items zijn en niet naar containers.</span><span class="sxs-lookup"><span data-stu-id="c5c00-161">The paths must be paths to items, not to containers.</span></span> <span data-ttu-id="c5c00-162">U moet bijvoorbeeld een pad naar een of meer bestanden opgeven, niet een pad naar een map.</span><span class="sxs-lookup"><span data-stu-id="c5c00-162">For example, you must specify a path to one or more files, not a path to a directory.</span></span>

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

### <span data-ttu-id="c5c00-163">-LiteralPath</span><span class="sxs-lookup"><span data-stu-id="c5c00-163">-LiteralPath</span></span>

<span data-ttu-id="c5c00-164">Hiermee geeft u een pad naar een of meer locaties.</span><span class="sxs-lookup"><span data-stu-id="c5c00-164">Specifies a path to one or more locations.</span></span> <span data-ttu-id="c5c00-165">De waarde van **LiteralPath** wordt precies zo gebruikt als deze wordt getypt.</span><span class="sxs-lookup"><span data-stu-id="c5c00-165">The value of **LiteralPath** is used exactly as it is typed.</span></span> <span data-ttu-id="c5c00-166">Geen tekens worden geïnterpreteerd als joker tekens.</span><span class="sxs-lookup"><span data-stu-id="c5c00-166">No characters are interpreted as wildcards.</span></span> <span data-ttu-id="c5c00-167">Als het pad escape tekens bevat, plaatst u het tussen enkele aanhalings tekens.</span><span class="sxs-lookup"><span data-stu-id="c5c00-167">If the path includes escape characters, enclose it in single quotation marks.</span></span> <span data-ttu-id="c5c00-168">Enkele aanhalings tekens geven aan dat Power shell geen karakters interpreteert als escape reeksen.</span><span class="sxs-lookup"><span data-stu-id="c5c00-168">Single quotation marks tell PowerShell not to interpret any characters as escape sequences.</span></span>

<span data-ttu-id="c5c00-169">Zie [about_Quoting_Rules](../Microsoft.Powershell.Core/About/about_Quoting_Rules.md)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="c5c00-169">For more information, see [about_Quoting_Rules](../Microsoft.Powershell.Core/About/about_Quoting_Rules.md).</span></span>

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

### <span data-ttu-id="c5c00-170">-ReadCount</span><span class="sxs-lookup"><span data-stu-id="c5c00-170">-ReadCount</span></span>

<span data-ttu-id="c5c00-171">Hiermee geeft u op hoeveel regels met inhoud per keer via de pijp lijn worden verzonden.</span><span class="sxs-lookup"><span data-stu-id="c5c00-171">Specifies how many lines of content are sent through the pipeline at a time.</span></span> <span data-ttu-id="c5c00-172">De standaardwaarde is 1.</span><span class="sxs-lookup"><span data-stu-id="c5c00-172">The default value is 1.</span></span>
<span data-ttu-id="c5c00-173">Met de waarde 0 (nul) wordt alle inhoud in één keer verzonden.</span><span class="sxs-lookup"><span data-stu-id="c5c00-173">A value of 0 (zero) sends all of the content at one time.</span></span>

<span data-ttu-id="c5c00-174">Met deze para meter wordt de weer gegeven inhoud niet gewijzigd, maar dit is van invloed op de tijd die nodig is om de inhoud weer te geven.</span><span class="sxs-lookup"><span data-stu-id="c5c00-174">This parameter does not change the content displayed, but it does affect the time it takes to display the content.</span></span> <span data-ttu-id="c5c00-175">Als de waarde van **ReadCount** toeneemt, wordt de tijd die nodig is om de eerste regel te retour neren, maar wordt de totale tijd van de bewerking afgenomen.</span><span class="sxs-lookup"><span data-stu-id="c5c00-175">As the value of **ReadCount** increases, the time it takes to return the first line increases, but the total time for the operation decreases.</span></span> <span data-ttu-id="c5c00-176">Dit kan een merkbaar verschil in grote items vormen.</span><span class="sxs-lookup"><span data-stu-id="c5c00-176">This can make a perceptible difference in large items.</span></span>

```yaml
Type: System.Int64
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: 1
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="c5c00-177">-TotalCount</span><span class="sxs-lookup"><span data-stu-id="c5c00-177">-TotalCount</span></span>

<span data-ttu-id="c5c00-178">Hiermee geeft u het aantal regels vanaf het begin van een bestand of een ander item op.</span><span class="sxs-lookup"><span data-stu-id="c5c00-178">Specifies the number of lines from the beginning of a file or other item.</span></span> <span data-ttu-id="c5c00-179">De standaard waarde is-1 (alle regels).</span><span class="sxs-lookup"><span data-stu-id="c5c00-179">The default is -1 (all lines).</span></span>

<span data-ttu-id="c5c00-180">U kunt de naam van de **totalCount** of de aliassen van de para meter, **First** of **Head** gebruiken.</span><span class="sxs-lookup"><span data-stu-id="c5c00-180">You can use the **TotalCount** parameter name or its aliases, **First** or **Head**.</span></span>

```yaml
Type: System.Int64
Parameter Sets: (All)
Aliases: First, Head

Required: False
Position: Named
Default value: -1
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="c5c00-181">-Staart</span><span class="sxs-lookup"><span data-stu-id="c5c00-181">-Tail</span></span>

<span data-ttu-id="c5c00-182">Hiermee wordt het aantal regels van het einde van een bestand of een ander item opgegeven.</span><span class="sxs-lookup"><span data-stu-id="c5c00-182">Specifies the number of lines from the end of a file or other item.</span></span> <span data-ttu-id="c5c00-183">U kunt de naam van de para meter van de **staart** of de bijbehorende alias als **laatste** gebruiken.</span><span class="sxs-lookup"><span data-stu-id="c5c00-183">You can use the **Tail** parameter name or its alias, **Last**.</span></span> <span data-ttu-id="c5c00-184">Deze para meter is geïntroduceerd in Power Shell 3,0.</span><span class="sxs-lookup"><span data-stu-id="c5c00-184">This parameter was introduced in PowerShell 3.0.</span></span>

```yaml
Type: System.Int32
Parameter Sets: (All)
Aliases: Last

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="c5c00-185">-Filter</span><span class="sxs-lookup"><span data-stu-id="c5c00-185">-Filter</span></span>

<span data-ttu-id="c5c00-186">Hiermee geeft u een filter op om de para meter **Path** te kwalificeren.</span><span class="sxs-lookup"><span data-stu-id="c5c00-186">Specifies a filter to qualify the **Path** parameter.</span></span> <span data-ttu-id="c5c00-187">De [File System](../Microsoft.PowerShell.Core/About/about_FileSystem_Provider.md) -provider is de enige geïnstalleerde Power shell-provider die het gebruik van filters ondersteunt.</span><span class="sxs-lookup"><span data-stu-id="c5c00-187">The [FileSystem](../Microsoft.PowerShell.Core/About/about_FileSystem_Provider.md) provider is the only installed PowerShell provider that supports the use of filters.</span></span> <span data-ttu-id="c5c00-188">U kunt de syntaxis voor de filter taal van het **Bestands systeem** in [about_Wildcards](../Microsoft.PowerShell.Core/About/about_Wildcards.md)vinden.</span><span class="sxs-lookup"><span data-stu-id="c5c00-188">You can find the syntax for the **FileSystem** filter language in [about_Wildcards](../Microsoft.PowerShell.Core/About/about_Wildcards.md).</span></span>
<span data-ttu-id="c5c00-189">Filters zijn efficiënter dan andere para meters, omdat deze door de provider worden toegepast wanneer de cmdlet de objecten ophaalt in plaats van dat Power shell de objecten heeft gefilterd nadat ze zijn opgehaald.</span><span class="sxs-lookup"><span data-stu-id="c5c00-189">Filters are more efficient than other parameters, because the provider applies them when the cmdlet gets the objects rather than having PowerShell filter the objects after they are retrieved.</span></span>

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

### <span data-ttu-id="c5c00-190">-Include</span><span class="sxs-lookup"><span data-stu-id="c5c00-190">-Include</span></span>

<span data-ttu-id="c5c00-191">Hiermee wordt een teken reeks matrix opgegeven, een item of items die met deze cmdlet in de bewerking zijn opgenomen.</span><span class="sxs-lookup"><span data-stu-id="c5c00-191">Specifies, as a string array, an item or items that this cmdlet includes in the operation.</span></span> <span data-ttu-id="c5c00-192">De waarde van deze para meter komt in aanmerking voor de para meter **Path** .</span><span class="sxs-lookup"><span data-stu-id="c5c00-192">The value of this parameter qualifies the **Path** parameter.</span></span> <span data-ttu-id="c5c00-193">Voer een element of patroon van een pad in, zoals `"*.txt"` .</span><span class="sxs-lookup"><span data-stu-id="c5c00-193">Enter a path element or pattern, such as `"*.txt"`.</span></span> <span data-ttu-id="c5c00-194">Joker tekens zijn toegestaan.</span><span class="sxs-lookup"><span data-stu-id="c5c00-194">Wildcard characters are permitted.</span></span> <span data-ttu-id="c5c00-195">De para meter **include** is alleen effectief wanneer de inhoud van een item wordt opgenomen, zoals `C:\Windows\*` , waarbij het Joker teken de inhoud van de `C:\Windows` map bevat.</span><span class="sxs-lookup"><span data-stu-id="c5c00-195">The **Include** parameter is effective only when the command includes the contents of an item, such as `C:\Windows\*`, where the wildcard character specifies the contents of the `C:\Windows` directory.</span></span>

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

### <span data-ttu-id="c5c00-196">-Uitsluiten</span><span class="sxs-lookup"><span data-stu-id="c5c00-196">-Exclude</span></span>

<span data-ttu-id="c5c00-197">Hiermee geeft u als een teken reeks matrix een item of items die met deze cmdlet worden uitgesloten in de bewerking.</span><span class="sxs-lookup"><span data-stu-id="c5c00-197">Specifies, as a string array, an item or items that this cmdlet excludes in the operation.</span></span>
<span data-ttu-id="c5c00-198">De waarde van deze para meter komt in aanmerking voor de para meter **Path** .</span><span class="sxs-lookup"><span data-stu-id="c5c00-198">The value of this parameter qualifies the **Path** parameter.</span></span>

<span data-ttu-id="c5c00-199">Voer een element of patroon van een pad in, zoals `*.txt` .</span><span class="sxs-lookup"><span data-stu-id="c5c00-199">Enter a path element or pattern, such as `*.txt`.</span></span>
<span data-ttu-id="c5c00-200">Joker tekens zijn toegestaan.</span><span class="sxs-lookup"><span data-stu-id="c5c00-200">Wildcard characters are permitted.</span></span>

<span data-ttu-id="c5c00-201">De **exclude** -para meter is alleen effectief wanneer de inhoud van een item wordt opgenomen, zoals `C:\Windows\*` , waarbij het Joker teken de inhoud van de `C:\Windows` map bevat.</span><span class="sxs-lookup"><span data-stu-id="c5c00-201">The **Exclude** parameter is effective only when the command includes the contents of an item, such as `C:\Windows\*`, where the wildcard character specifies the contents of the `C:\Windows` directory.</span></span>

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

### <span data-ttu-id="c5c00-202">-Force</span><span class="sxs-lookup"><span data-stu-id="c5c00-202">-Force</span></span>

<span data-ttu-id="c5c00-203">**Force** overschrijft een alleen-lezen kenmerk of maakt mappen om een bestandspad te volt ooien.</span><span class="sxs-lookup"><span data-stu-id="c5c00-203">**Force** will override a read-only attribute or create directories to complete a file path.</span></span> <span data-ttu-id="c5c00-204">De para meter **Forces** probeert geen bestands machtigingen te wijzigen of beveiligings beperkingen te negeren.</span><span class="sxs-lookup"><span data-stu-id="c5c00-204">The **Force** parameter does not attempt to change file permissions or override security restrictions.</span></span>

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

### <span data-ttu-id="c5c00-205">-Credential</span><span class="sxs-lookup"><span data-stu-id="c5c00-205">-Credential</span></span>

> [!NOTE]
> <span data-ttu-id="c5c00-206">Deze para meter wordt niet ondersteund door providers die zijn geïnstalleerd met Power shell.</span><span class="sxs-lookup"><span data-stu-id="c5c00-206">This parameter is not supported by any providers installed with PowerShell.</span></span>
> <span data-ttu-id="c5c00-207">Gebruik [invoke-Command](../Microsoft.PowerShell.Core/Invoke-Command.md)om een andere gebruiker te imiteren of uw referenties te verhogen wanneer u deze cmdlet uitvoert.</span><span class="sxs-lookup"><span data-stu-id="c5c00-207">To impersonate another user, or elevate your credentials when running this cmdlet, use [Invoke-Command](../Microsoft.PowerShell.Core/Invoke-Command.md).</span></span>

```yaml
Type: System.Management.Automation.PSCredential
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: Current user
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="c5c00-208">-Scheidings teken</span><span class="sxs-lookup"><span data-stu-id="c5c00-208">-Delimiter</span></span>

<span data-ttu-id="c5c00-209">Hiermee geeft u het scheidings teken `Get-Content` op dat wordt gebruikt om het bestand in objecten te verdelen terwijl het wordt gelezen.</span><span class="sxs-lookup"><span data-stu-id="c5c00-209">Specifies the delimiter that `Get-Content` uses to divide the file into objects while it reads.</span></span> <span data-ttu-id="c5c00-210">De standaard waarde is `\n` , het einde van de regel.</span><span class="sxs-lookup"><span data-stu-id="c5c00-210">The default is `\n`, the end-of-line character.</span></span> <span data-ttu-id="c5c00-211">Bij het lezen van een tekst bestand `Get-Content` retourneert een verzameling teken reeks objecten, die allemaal eindigen met een einde van een regel.</span><span class="sxs-lookup"><span data-stu-id="c5c00-211">When reading a text file, `Get-Content` returns a collection of string objects, each of which ends with an end-of-line character.</span></span> <span data-ttu-id="c5c00-212">Wanneer u een scheidings teken opgeeft dat niet voor komt in het bestand, `Get-Content` retourneert het hele bestand als één undelimited-object.</span><span class="sxs-lookup"><span data-stu-id="c5c00-212">When you enter a delimiter that does not exist in the file, `Get-Content` returns the entire file as a single, undelimited object.</span></span>

<span data-ttu-id="c5c00-213">U kunt deze para meter gebruiken om een groot bestand te splitsen in kleinere bestanden door een bestands scheidings teken op te geven als scheidings teken.</span><span class="sxs-lookup"><span data-stu-id="c5c00-213">You can use this parameter to split a large file into smaller files by specifying a file separator, as the delimiter.</span></span> <span data-ttu-id="c5c00-214">Het scheidings teken wordt bewaard (niet verwijderd) en wordt het laatste item in elk bestands gedeelte.</span><span class="sxs-lookup"><span data-stu-id="c5c00-214">The delimiter is preserved (not discarded) and becomes the last item in each file section.</span></span>

<span data-ttu-id="c5c00-215">**Scheidings teken** is een dynamische para meter die de **File System** provider toevoegt aan de `Get-Content` cmdlet.</span><span class="sxs-lookup"><span data-stu-id="c5c00-215">**Delimiter** is a dynamic parameter that the **FileSystem** provider adds to the `Get-Content` cmdlet.</span></span> <span data-ttu-id="c5c00-216">Deze para meter werkt alleen op stations met een bestands systeem.</span><span class="sxs-lookup"><span data-stu-id="c5c00-216">This parameter works only in file system drives.</span></span>

> [!NOTE]
> <span data-ttu-id="c5c00-217">Wanneer de waarde van de para meter voor het **scheidings** teken leeg is, wordt er op dit moment `Get-Content` niets geretourneerd.</span><span class="sxs-lookup"><span data-stu-id="c5c00-217">Currently, when the value of the **Delimiter** parameter is an empty string, `Get-Content` does not return anything.</span></span> <span data-ttu-id="c5c00-218">Dit is een bekend probleem.</span><span class="sxs-lookup"><span data-stu-id="c5c00-218">This is a known issue.</span></span> <span data-ttu-id="c5c00-219">Als u `Get-Content` wilt forceren om het hele bestand als een enkele, undelimited teken reeks te retour neren.</span><span class="sxs-lookup"><span data-stu-id="c5c00-219">To force `Get-Content` to return the entire file as a single, undelimited string.</span></span> <span data-ttu-id="c5c00-220">Voer een waarde in die niet voor komt in het bestand.</span><span class="sxs-lookup"><span data-stu-id="c5c00-220">Enter a value that does not exist in the file.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: End-of-line character
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="c5c00-221">-Wachten</span><span class="sxs-lookup"><span data-stu-id="c5c00-221">-Wait</span></span>

<span data-ttu-id="c5c00-222">Hiermee blijft het bestand geopend nadat alle bestaande regels zijn uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="c5c00-222">Keeps the file open after all existing lines have been output.</span></span> <span data-ttu-id="c5c00-223">Tijdens het wachten wordt `Get-Content` het bestand na elke seconde gecontroleerd en worden er nieuwe regels uitgevoerd, indien aanwezig.</span><span class="sxs-lookup"><span data-stu-id="c5c00-223">While waiting, `Get-Content` checks the file once each second and outputs new lines if present.</span></span> <span data-ttu-id="c5c00-224">U kunt de **wacht tijd** onderbreken door op **CTRL + C** te drukken.</span><span class="sxs-lookup"><span data-stu-id="c5c00-224">You can interrupt **Wait** by pressing **CTRL+C**.</span></span> <span data-ttu-id="c5c00-225">De wacht tijd eindigt ook als het bestand wordt verwijderd. in dat geval wordt een niet-afsluit fout gerapporteerd.</span><span class="sxs-lookup"><span data-stu-id="c5c00-225">Waiting also ends if the file gets deleted, in which case a non-terminating error is reported.</span></span>

<span data-ttu-id="c5c00-226">**Wait** is een dynamische para meter die de File System Provider toevoegt aan de `Get-Content` cmdlet.</span><span class="sxs-lookup"><span data-stu-id="c5c00-226">**Wait** is a dynamic parameter that the FileSystem provider adds to the `Get-Content` cmdlet.</span></span> <span data-ttu-id="c5c00-227">Deze para meter werkt alleen op stations met een bestands systeem.</span><span class="sxs-lookup"><span data-stu-id="c5c00-227">This parameter works only in file system drives.</span></span> <span data-ttu-id="c5c00-228">**Wait** kan niet worden gecombineerd met **RAW**.</span><span class="sxs-lookup"><span data-stu-id="c5c00-228">**Wait** cannot be combined with **Raw**.</span></span>

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

### <span data-ttu-id="c5c00-229">-RAW</span><span class="sxs-lookup"><span data-stu-id="c5c00-229">-Raw</span></span>

<span data-ttu-id="c5c00-230">Hiermee worden tekens voor nieuwe regels genegeerd en wordt de volledige inhoud van een bestand in één teken reeks geretourneerd, waarbij de nieuwe voors worden bewaard.</span><span class="sxs-lookup"><span data-stu-id="c5c00-230">Ignores newline characters and returns the entire contents of a file in one string with the newlines preserved.</span></span> <span data-ttu-id="c5c00-231">Standaard worden nieuwe regels in een bestand gebruikt als scheidings tekens om de invoer te scheiden in een matrix met teken reeksen.</span><span class="sxs-lookup"><span data-stu-id="c5c00-231">By default, newline characters in a file are used as delimiters to separate the input into an array of strings.</span></span> <span data-ttu-id="c5c00-232">Deze para meter is geïntroduceerd in Power Shell 3,0.</span><span class="sxs-lookup"><span data-stu-id="c5c00-232">This parameter was introduced in PowerShell 3.0.</span></span>

<span data-ttu-id="c5c00-233">**RAW** is een dynamische para meter die de **File System** provider toevoegt aan de `Get-Content` cmdlet deze para meter werkt alleen in bestandssysteem stations.</span><span class="sxs-lookup"><span data-stu-id="c5c00-233">**Raw** is a dynamic parameter that the **FileSystem** provider adds to the `Get-Content` cmdlet This parameter works only in file system drives.</span></span>

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

### <span data-ttu-id="c5c00-234">-Encoding</span><span class="sxs-lookup"><span data-stu-id="c5c00-234">-Encoding</span></span>

<span data-ttu-id="c5c00-235">Hiermee geeft u het type code ring voor het doel bestand op.</span><span class="sxs-lookup"><span data-stu-id="c5c00-235">Specifies the type of encoding for the target file.</span></span> <span data-ttu-id="c5c00-236">De standaardwaarde is `utf8NoBOM`.</span><span class="sxs-lookup"><span data-stu-id="c5c00-236">The default value is `utf8NoBOM`.</span></span>

<span data-ttu-id="c5c00-237">De acceptabele waarden voor deze para meter zijn als volgt:</span><span class="sxs-lookup"><span data-stu-id="c5c00-237">The acceptable values for this parameter are as follows:</span></span>

- <span data-ttu-id="c5c00-238">`ascii`: Gebruikt de code ring voor de ASCII-tekenset (7-bits).</span><span class="sxs-lookup"><span data-stu-id="c5c00-238">`ascii`: Uses the encoding for the ASCII (7-bit) character set.</span></span>
- <span data-ttu-id="c5c00-239">`bigendianunicode`: Wordt gecodeerd in UTF-16-indeling met behulp van de byte volgorde big endian.</span><span class="sxs-lookup"><span data-stu-id="c5c00-239">`bigendianunicode`: Encodes in UTF-16 format using the big-endian byte order.</span></span>
- <span data-ttu-id="c5c00-240">`bigendianutf32`: Codeert in UTF-32-indeling met behulp van de byte volgorde big endian.</span><span class="sxs-lookup"><span data-stu-id="c5c00-240">`bigendianutf32`: Encodes in UTF-32 format using the big-endian byte order.</span></span>
- <span data-ttu-id="c5c00-241">`oem`: Maakt gebruik van de standaard codering voor MS-DOS-en console Programma's.</span><span class="sxs-lookup"><span data-stu-id="c5c00-241">`oem`: Uses the default encoding for MS-DOS and console programs.</span></span>
- <span data-ttu-id="c5c00-242">`unicode`: Wordt gecodeerd in UTF-16-indeling met behulp van de byte volgorde little endian.</span><span class="sxs-lookup"><span data-stu-id="c5c00-242">`unicode`: Encodes in UTF-16 format using the little-endian byte order.</span></span>
- <span data-ttu-id="c5c00-243">`utf7`: Wordt gecodeerd in de indeling UTF-7.</span><span class="sxs-lookup"><span data-stu-id="c5c00-243">`utf7`: Encodes in UTF-7 format.</span></span>
- <span data-ttu-id="c5c00-244">`utf8`: Wordt gecodeerd in UTF-8-indeling.</span><span class="sxs-lookup"><span data-stu-id="c5c00-244">`utf8`: Encodes in UTF-8 format.</span></span>
- <span data-ttu-id="c5c00-245">`utf8BOM`: Code ring in UTF-8-indeling met byte order Mark (BOM)</span><span class="sxs-lookup"><span data-stu-id="c5c00-245">`utf8BOM`: Encodes in UTF-8 format with Byte Order Mark (BOM)</span></span>
- <span data-ttu-id="c5c00-246">`utf8NoBOM`: Code ring in UTF-8-indeling zonder byte order Mark (BOM)</span><span class="sxs-lookup"><span data-stu-id="c5c00-246">`utf8NoBOM`: Encodes in UTF-8 format without Byte Order Mark (BOM)</span></span>
- <span data-ttu-id="c5c00-247">`utf32`: Gecodeerd in UTF-32-indeling.</span><span class="sxs-lookup"><span data-stu-id="c5c00-247">`utf32`: Encodes in UTF-32 format.</span></span>

<span data-ttu-id="c5c00-248">Encoding is een dynamische para meter die de **File System** provider toevoegt aan de `Get-Content` cmdlet.</span><span class="sxs-lookup"><span data-stu-id="c5c00-248">Encoding is a dynamic parameter that the **FileSystem** provider adds to the `Get-Content` cmdlet.</span></span>
<span data-ttu-id="c5c00-249">Deze para meter is alleen beschikbaar in bestandssysteem stations.</span><span class="sxs-lookup"><span data-stu-id="c5c00-249">This parameter is available only in file system drives.</span></span>

<span data-ttu-id="c5c00-250">Bij het lezen van en schrijven naar binaire bestanden gebruikt u de para meter **AsByteStream** en de waarde 0 voor de para meter **ReadCount** .</span><span class="sxs-lookup"><span data-stu-id="c5c00-250">When reading from and writing to binary files, use the **AsByteStream** parameter and a value of 0 for the **ReadCount** parameter.</span></span> <span data-ttu-id="c5c00-251">Met een **ReadCount** -waarde van 0 wordt het hele bestand in één Lees bewerking gelezen.</span><span class="sxs-lookup"><span data-stu-id="c5c00-251">A **ReadCount** value of 0 reads the entire file in a single read operation.</span></span> <span data-ttu-id="c5c00-252">De standaard waarde voor **ReadCount** , 1, leest één byte per Lees bewerking en converteert elke byte naar een afzonderlijk object, waardoor fouten optreden wanneer u de- `Set-Content` cmdlet gebruikt om de bytes naar een bestand te schrijven, tenzij u de para meter **AsByteStream** gebruikt.</span><span class="sxs-lookup"><span data-stu-id="c5c00-252">The default **ReadCount** value, 1, reads one byte in each read operation and converts each byte into a separate object, which causes errors when you use the `Set-Content` cmdlet to write the bytes to a file unless you use **AsByteStream** parameter.</span></span>

<span data-ttu-id="c5c00-253">Vanaf Power shell 6,2 kunnen met de para meter **Encoding** ook numerieke id's van geregistreerde code pagina's (zoals `-Encoding 1251` ) of teken reeks namen van geregistreerde code pagina's (zoals) worden toegestaan `-Encoding "windows-1251"` .</span><span class="sxs-lookup"><span data-stu-id="c5c00-253">Beginning with PowerShell 6.2, the **Encoding** parameter also allows numeric IDs of registered code pages (like `-Encoding 1251`) or string names of registered code pages (like `-Encoding "windows-1251"`).</span></span> <span data-ttu-id="c5c00-254">Zie de .NET-documentatie voor [code ring. code tabel](/dotnet/api/system.text.encoding.codepage?view=netcore-2.2)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="c5c00-254">For more information, see the .NET documentation for [Encoding.CodePage](/dotnet/api/system.text.encoding.codepage?view=netcore-2.2).</span></span>

> [!NOTE]
> <span data-ttu-id="c5c00-255">**UTF-7** \* wordt niet meer aanbevolen voor gebruik.</span><span class="sxs-lookup"><span data-stu-id="c5c00-255">**UTF-7** \* is no longer recommended to use.</span></span> <span data-ttu-id="c5c00-256">In Power shell 7,1 wordt een waarschuwing geschreven als u `utf7` voor de para meter **Encoding** opgeeft.</span><span class="sxs-lookup"><span data-stu-id="c5c00-256">In PowerShell 7.1, a warning is written if you specify `utf7` for the **Encoding** parameter.</span></span>

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

### <span data-ttu-id="c5c00-257">-Stream</span><span class="sxs-lookup"><span data-stu-id="c5c00-257">-Stream</span></span>

<span data-ttu-id="c5c00-258">Hiermee wordt de inhoud van de opgegeven alternatieve NTFS-bestands stroom opgehaald uit het bestand.</span><span class="sxs-lookup"><span data-stu-id="c5c00-258">Gets the contents of the specified alternate NTFS file stream from the file.</span></span> <span data-ttu-id="c5c00-259">Voer de naam van de stream in.</span><span class="sxs-lookup"><span data-stu-id="c5c00-259">Enter the stream name.</span></span>
<span data-ttu-id="c5c00-260">Jokertekens worden niet ondersteund.</span><span class="sxs-lookup"><span data-stu-id="c5c00-260">Wildcards are not supported.</span></span>

<span data-ttu-id="c5c00-261">**Stream** is een dynamische para meter die de **File System** provider toevoegt aan de `Get-Content` cmdlet.</span><span class="sxs-lookup"><span data-stu-id="c5c00-261">**Stream** is a dynamic parameter that the **FileSystem** provider adds to the `Get-Content` cmdlet.</span></span>
<span data-ttu-id="c5c00-262">Deze para meter werkt alleen in bestandssysteem stations op Windows-systemen.</span><span class="sxs-lookup"><span data-stu-id="c5c00-262">This parameter works only in file system drives on Windows systems.</span></span> <span data-ttu-id="c5c00-263">Deze para meter is geïntroduceerd in Windows Power Shell 3,0.</span><span class="sxs-lookup"><span data-stu-id="c5c00-263">This parameter was introduced in Windows PowerShell 3.0.</span></span>

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

### <span data-ttu-id="c5c00-264">-AsByteStream</span><span class="sxs-lookup"><span data-stu-id="c5c00-264">-AsByteStream</span></span>

<span data-ttu-id="c5c00-265">Hiermee geeft u op dat de inhoud moet worden gelezen als een byte stroom.</span><span class="sxs-lookup"><span data-stu-id="c5c00-265">Specifies that the content should be read as a stream of bytes.</span></span> <span data-ttu-id="c5c00-266">De para meter **AsByteStream** is geïntroduceerd in Windows power shell 6,0.</span><span class="sxs-lookup"><span data-stu-id="c5c00-266">The **AsByteStream** parameter was introduced in Windows PowerShell 6.0.</span></span>

<span data-ttu-id="c5c00-267">Er treedt een waarschuwing op wanneer u de para meter **AsByteStream** gebruikt met de para meter **Encoding** .</span><span class="sxs-lookup"><span data-stu-id="c5c00-267">A warning occurs when you use the **AsByteStream** parameter with the **Encoding** parameter.</span></span> <span data-ttu-id="c5c00-268">De para meter **AsByteStream** negeert elke code ring en de uitvoer wordt geretourneerd als een byte stroom.</span><span class="sxs-lookup"><span data-stu-id="c5c00-268">The **AsByteStream** parameter ignores any encoding and the output is returned as a stream of bytes.</span></span>

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

### <span data-ttu-id="c5c00-269">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="c5c00-269">CommonParameters</span></span>

<span data-ttu-id="c5c00-270">Deze cmdlet biedt ondersteuning voor de algemene para meters: `-Debug` , `-ErrorAction` , `-ErrorVariable` , `-InformationAction` , `-InformationVariable` , `-OutVariable` , `-OutBuffer` , `-PipelineVariable` , `-Verbose` , `-WarningAction` en `-WarningVariable` .</span><span class="sxs-lookup"><span data-stu-id="c5c00-270">This cmdlet supports the common parameters: `-Debug`, `-ErrorAction`, `-ErrorVariable`, `-InformationAction`, `-InformationVariable`, `-OutVariable`, `-OutBuffer`, `-PipelineVariable`, `-Verbose`, `-WarningAction`, and `-WarningVariable`.</span></span> <span data-ttu-id="c5c00-271">Zie [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="c5c00-271">For more information, see [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md).</span></span>

## <span data-ttu-id="c5c00-272">INVOER</span><span class="sxs-lookup"><span data-stu-id="c5c00-272">INPUTS</span></span>

### <span data-ttu-id="c5c00-273">Systeem. Int64, System. string [], System. Management. Automation. PSCredential</span><span class="sxs-lookup"><span data-stu-id="c5c00-273">System.Int64, System.String[], System.Management.Automation.PSCredential</span></span>

<span data-ttu-id="c5c00-274">U kunt het lees aantal, het totale aantal, de paden of de referenties door sluizen naar `Get-Content` .</span><span class="sxs-lookup"><span data-stu-id="c5c00-274">You can pipe the read count, total count, paths, or credentials to `Get-Content`.</span></span>

## <span data-ttu-id="c5c00-275">UITVOER</span><span class="sxs-lookup"><span data-stu-id="c5c00-275">OUTPUTS</span></span>

### <span data-ttu-id="c5c00-276">System. byte, System. String</span><span class="sxs-lookup"><span data-stu-id="c5c00-276">System.Byte, System.String</span></span>

<span data-ttu-id="c5c00-277">`Get-Content` retourneert teken reeksen of bytes.</span><span class="sxs-lookup"><span data-stu-id="c5c00-277">`Get-Content` returns strings or bytes.</span></span> <span data-ttu-id="c5c00-278">Het uitvoer type is afhankelijk van het type inhoud dat u opgeeft als invoer.</span><span class="sxs-lookup"><span data-stu-id="c5c00-278">The output type depends upon the type of content that you specify as input.</span></span>

## <span data-ttu-id="c5c00-279">OPMERKINGEN</span><span class="sxs-lookup"><span data-stu-id="c5c00-279">NOTES</span></span>

<span data-ttu-id="c5c00-280">De `Get-Content` cmdlet is ontworpen om te werken met de gegevens die door elke provider worden weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="c5c00-280">The `Get-Content` cmdlet is designed to work with the data exposed by any provider.</span></span> <span data-ttu-id="c5c00-281">Gebruik de cmdlet om de providers in uw sessie op te halen `Get-PSProvider` .</span><span class="sxs-lookup"><span data-stu-id="c5c00-281">To get the providers in your session, use the `Get-PSProvider` cmdlet.</span></span> <span data-ttu-id="c5c00-282">Zie [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="c5c00-282">For more information, see [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md).</span></span>

## <span data-ttu-id="c5c00-283">GERELATEERDE KOPPELINGEN</span><span class="sxs-lookup"><span data-stu-id="c5c00-283">RELATED LINKS</span></span>

[<span data-ttu-id="c5c00-284">about_Automatic_Variables</span><span class="sxs-lookup"><span data-stu-id="c5c00-284">about_Automatic_Variables</span></span>](../Microsoft.PowerShell.Core/About/about_Automatic_Variables.md)

[<span data-ttu-id="c5c00-285">about_Providers</span><span class="sxs-lookup"><span data-stu-id="c5c00-285">about_Providers</span></span>](../Microsoft.PowerShell.Core/About/about_Providers.md)

[<span data-ttu-id="c5c00-286">Add-content</span><span class="sxs-lookup"><span data-stu-id="c5c00-286">Add-Content</span></span>](Add-Content.md)

[<span data-ttu-id="c5c00-287">Wissen-inhoud</span><span class="sxs-lookup"><span data-stu-id="c5c00-287">Clear-Content</span></span>](Clear-Content.md)

[<span data-ttu-id="c5c00-288">ForEach-object</span><span class="sxs-lookup"><span data-stu-id="c5c00-288">ForEach-Object</span></span>](../Microsoft.PowerShell.Core/ForEach-Object.md)

[<span data-ttu-id="c5c00-289">Get-PSProvider</span><span class="sxs-lookup"><span data-stu-id="c5c00-289">Get-PSProvider</span></span>](Get-PSProvider.md)

[<span data-ttu-id="c5c00-290">Set-Content</span><span class="sxs-lookup"><span data-stu-id="c5c00-290">Set-Content</span></span>](Set-Content.md)
