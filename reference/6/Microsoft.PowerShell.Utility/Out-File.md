---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 09/21/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/out-file?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Out-File
ms.openlocfilehash: f3cd58bffde8bcb6dab488a9e40e69d7435133e4
ms.sourcegitcommit: d757d64ea8c8af4d92596e8fbe15f2f40d48d3ac
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 09/22/2020
ms.locfileid: "93251947"
---
# <span data-ttu-id="4c22f-103">Out-File</span><span class="sxs-lookup"><span data-stu-id="4c22f-103">Out-File</span></span>

## <span data-ttu-id="4c22f-104">SAMENVATTING</span><span class="sxs-lookup"><span data-stu-id="4c22f-104">SYNOPSIS</span></span>
<span data-ttu-id="4c22f-105">Hiermee wordt de uitvoer naar een bestand verzonden.</span><span class="sxs-lookup"><span data-stu-id="4c22f-105">Sends output to a file.</span></span>

## <span data-ttu-id="4c22f-106">SYNTAXIS</span><span class="sxs-lookup"><span data-stu-id="4c22f-106">SYNTAX</span></span>

### <span data-ttu-id="4c22f-107">ByPath (standaard)</span><span class="sxs-lookup"><span data-stu-id="4c22f-107">ByPath (Default)</span></span>

```
Out-File [-FilePath] <string> [[-Encoding] <Encoding>] [-Append] [-Force] [-NoClobber]
 [-Width <int>] [-NoNewline] [-InputObject <psobject>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="4c22f-108">ByLiteralPath</span><span class="sxs-lookup"><span data-stu-id="4c22f-108">ByLiteralPath</span></span>

```
Out-File [[-Encoding] <Encoding>] -LiteralPath <string> [-Append] [-Force] [-NoClobber]
 [-Width <int>] [-NoNewline] [-InputObject <psobject>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="4c22f-109">BESCHRIJVING</span><span class="sxs-lookup"><span data-stu-id="4c22f-109">DESCRIPTION</span></span>

<span data-ttu-id="4c22f-110">De `Out-File` cmdlet verzendt uitvoer naar een bestand.</span><span class="sxs-lookup"><span data-stu-id="4c22f-110">The `Out-File` cmdlet sends output to a file.</span></span> <span data-ttu-id="4c22f-111">Het gebruik van het Power shell-opmaak systeem wordt impliciet gebruikt om naar het bestand te schrijven.</span><span class="sxs-lookup"><span data-stu-id="4c22f-111">It implicitly uses PowerShell's formatting system to write to the file.</span></span> <span data-ttu-id="4c22f-112">Het bestand ontvangt dezelfde weergave representatie als de Terminal.</span><span class="sxs-lookup"><span data-stu-id="4c22f-112">The file receives the same display representation as the terminal.</span></span> <span data-ttu-id="4c22f-113">Dit betekent dat de uitvoer mogelijk niet ideaal is voor programma verwerking, tenzij alle invoer objecten teken reeksen zijn.</span><span class="sxs-lookup"><span data-stu-id="4c22f-113">This means that the output may not be ideal for programmatic processing unless all input objects are strings.</span></span>
<span data-ttu-id="4c22f-114">Wanneer u para meters voor de uitvoer wilt opgeven, gebruikt u `Out-File` in plaats van de omleidings operator ( `>` ).</span><span class="sxs-lookup"><span data-stu-id="4c22f-114">When you need to specify parameters for the output, use `Out-File` rather than the redirection operator (`>`).</span></span> <span data-ttu-id="4c22f-115">Zie [about_Redirection](../Microsoft.PowerShell.Core/About/about_Redirection.md)voor meer informatie over omleiding.</span><span class="sxs-lookup"><span data-stu-id="4c22f-115">For more information about redirection, see [about_Redirection](../Microsoft.PowerShell.Core/About/about_Redirection.md).</span></span>

## <span data-ttu-id="4c22f-116">VOORBEELDEN</span><span class="sxs-lookup"><span data-stu-id="4c22f-116">EXAMPLES</span></span>

### <span data-ttu-id="4c22f-117">Voor beeld 1: uitvoer verzenden en een bestand maken</span><span class="sxs-lookup"><span data-stu-id="4c22f-117">Example 1: Send output and create a file</span></span>

<span data-ttu-id="4c22f-118">In dit voor beeld ziet u hoe u een lijst met de processen van de lokale computer naar een bestand verzendt.</span><span class="sxs-lookup"><span data-stu-id="4c22f-118">This example shows how to send a list of the local computer's processes to a file.</span></span> <span data-ttu-id="4c22f-119">Als het bestand niet bestaat, `Out-File` maakt het bestand in het opgegeven pad.</span><span class="sxs-lookup"><span data-stu-id="4c22f-119">If the file does not exist, `Out-File` creates the file in the specified path.</span></span>

```powershell
Get-Process | Out-File -FilePath .\Process.txt
Get-Content -Path .\Process.txt
```

```Output
 NPM(K)    PM(M)      WS(M)     CPU(s)      Id  SI ProcessName
 ------    -----      -----     ------      --  -- -----------
     29    22.39      35.40      10.98   42764   9 Application
     53    99.04     113.96       0.00   32664   0 CcmExec
     27    96.62     112.43     113.00   17720   9 Code
```

<span data-ttu-id="4c22f-120">De `Get-Process` cmdlet haalt een lijst op met processen die worden uitgevoerd op de lokale computer.</span><span class="sxs-lookup"><span data-stu-id="4c22f-120">The `Get-Process` cmdlet gets the list of processes running on the local computer.</span></span> <span data-ttu-id="4c22f-121">De **proces** objecten worden in de pijp lijn naar de `Out-File` cmdlet verzonden.</span><span class="sxs-lookup"><span data-stu-id="4c22f-121">The **Process** objects are sent down the pipeline to the `Out-File` cmdlet.</span></span> <span data-ttu-id="4c22f-122">`Out-File` maakt gebruik van de **filepath** para meter en maakt een bestand in de huidige map met de naam **Process.txt**.</span><span class="sxs-lookup"><span data-stu-id="4c22f-122">`Out-File` uses the **FilePath** parameter and creates a file in the current directory named **Process.txt**.</span></span> <span data-ttu-id="4c22f-123">De `Get-Content` opdracht haalt inhoud op uit het bestand en geeft deze weer in de Power shell-console.</span><span class="sxs-lookup"><span data-stu-id="4c22f-123">The `Get-Content` command gets content from the file and displays it in the PowerShell console.</span></span>

### <span data-ttu-id="4c22f-124">Voor beeld 2: voor komen dat een bestaand bestand wordt overschreven</span><span class="sxs-lookup"><span data-stu-id="4c22f-124">Example 2: Prevent an existing file from being overwritten</span></span>

<span data-ttu-id="4c22f-125">In dit voor beeld wordt voor komen dat een bestaand bestand wordt overschreven.</span><span class="sxs-lookup"><span data-stu-id="4c22f-125">This example prevents an existing file from being overwritten.</span></span> <span data-ttu-id="4c22f-126">Standaard worden `Out-File` bestaande bestanden overschreven.</span><span class="sxs-lookup"><span data-stu-id="4c22f-126">By default, `Out-File` overwrites existing files.</span></span>

```powershell
Get-Process | Out-File -FilePath .\Process.txt -NoClobber
```

```Output
Out-File : The file 'C:\Test\Process.txt' already exists.
At line:1 char:15
+ Get-Process | Out-File -FilePath .\Process.txt -NoClobber
+               ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
```

<span data-ttu-id="4c22f-127">De `Get-Process` cmdlet haalt een lijst op met processen die worden uitgevoerd op de lokale computer.</span><span class="sxs-lookup"><span data-stu-id="4c22f-127">The `Get-Process` cmdlet gets the list of processes running on the local computer.</span></span> <span data-ttu-id="4c22f-128">De **proces** objecten worden in de pijp lijn naar de `Out-File` cmdlet verzonden.</span><span class="sxs-lookup"><span data-stu-id="4c22f-128">The **Process** objects are sent down the pipeline to the `Out-File` cmdlet.</span></span> <span data-ttu-id="4c22f-129">`Out-File` maakt gebruik van de **filepath** para meter en probeert te schrijven naar een bestand in de huidige map met de naam **Process.txt**.</span><span class="sxs-lookup"><span data-stu-id="4c22f-129">`Out-File` uses the **FilePath** parameter and attempts to write to a file in the current directory named **Process.txt**.</span></span> <span data-ttu-id="4c22f-130">Met de para meter **NoClobber** wordt voor komen dat het bestand wordt overschreven en wordt een bericht weer gegeven dat het bestand al bestaat.</span><span class="sxs-lookup"><span data-stu-id="4c22f-130">The **NoClobber** parameter prevents the file from being overwritten and displays a message that the file already exists.</span></span>

### <span data-ttu-id="4c22f-131">Voor beeld 3: uitvoer naar een bestand in ASCII-indeling verzenden</span><span class="sxs-lookup"><span data-stu-id="4c22f-131">Example 3: Send output to a file in ASCII format</span></span>

<span data-ttu-id="4c22f-132">In dit voor beeld ziet u hoe uitvoer wordt gecodeerd met een specifiek coderings type.</span><span class="sxs-lookup"><span data-stu-id="4c22f-132">This example shows how to encode output with a specific encoding type.</span></span>

```powershell
$Procs = Get-Process
Out-File -FilePath .\Process.txt -InputObject $Procs -Encoding ASCII -Width 50
```

<span data-ttu-id="4c22f-133">De `Get-Process` cmdlet haalt een lijst op met processen die worden uitgevoerd op de lokale computer.</span><span class="sxs-lookup"><span data-stu-id="4c22f-133">The `Get-Process` cmdlet gets the list of processes running on the local computer.</span></span> <span data-ttu-id="4c22f-134">De **proces** objecten worden opgeslagen in de variabele `$Procs` .</span><span class="sxs-lookup"><span data-stu-id="4c22f-134">The **Process** objects are stored in the variable, `$Procs`.</span></span> <span data-ttu-id="4c22f-135">`Out-File` maakt gebruik van de **filepath** para meter en maakt een bestand in de huidige map met de naam **Process.txt**.</span><span class="sxs-lookup"><span data-stu-id="4c22f-135">`Out-File` uses the **FilePath** parameter and creates a file in the current directory named **Process.txt**.</span></span> <span data-ttu-id="4c22f-136">De **input object** para meter geeft de proces objecten door in `$Procs` de bestands **Process.txt**.</span><span class="sxs-lookup"><span data-stu-id="4c22f-136">The **InputObject** parameter passes the process objects in `$Procs` to the file **Process.txt**.</span></span> <span data-ttu-id="4c22f-137">De para meter **Encoding** converteert de uitvoer naar **ASCII** -indeling.</span><span class="sxs-lookup"><span data-stu-id="4c22f-137">The **Encoding** parameter converts the output to **ASCII** format.</span></span> <span data-ttu-id="4c22f-138">De para meter **breedte** beperkt elke regel in het bestand tot 50 tekens, waardoor sommige gegevens kunnen worden afgekapt.</span><span class="sxs-lookup"><span data-stu-id="4c22f-138">The **Width** parameter limits each line in the file to 50 characters so some data might be truncated.</span></span>

### <span data-ttu-id="4c22f-139">Voor beeld 4: een provider gebruiken en uitvoer naar een bestand verzenden</span><span class="sxs-lookup"><span data-stu-id="4c22f-139">Example 4: Use a provider and send output to a file</span></span>

<span data-ttu-id="4c22f-140">In dit voor beeld ziet u hoe u de `Out-File` cmdlet gebruikt wanneer u zich niet in een **File System** -provider station bevindt.</span><span class="sxs-lookup"><span data-stu-id="4c22f-140">This example shows how to use the `Out-File` cmdlet when you are not in a **FileSystem** provider drive.</span></span> <span data-ttu-id="4c22f-141">Gebruik de `Get-PSProvider` cmdlet om de providers op uw lokale computer weer te geven.</span><span class="sxs-lookup"><span data-stu-id="4c22f-141">Use the `Get-PSProvider` cmdlet to view the providers on your local computer.</span></span> <span data-ttu-id="4c22f-142">Zie [about_Providers](../Microsoft.Powershell.Core/About/about_Providers.md)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="4c22f-142">For more information, see [about_Providers](../Microsoft.Powershell.Core/About/about_Providers.md).</span></span>

```
PS> Set-Location -Path Alias:

PS> Get-Location

Path
----
Alias:\

PS> Get-ChildItem | Out-File -FilePath C:\TestDir\AliasNames.txt

PS> Get-Content -Path C:\TestDir\AliasNames.txt

CommandType     Name
-----------     ----
Alias           % -> ForEach-Object
Alias           ? -> Where-Object
Alias           ac -> Add-Content
Alias           cat -> Get-Content
```

<span data-ttu-id="4c22f-143">De `Set-Location` opdracht gebruikt de para meter **Path** om de huidige locatie van de register provider in te stellen `Alias:` .</span><span class="sxs-lookup"><span data-stu-id="4c22f-143">The `Set-Location` command uses the **Path** parameter to set the current location to the registry provider `Alias:`.</span></span> <span data-ttu-id="4c22f-144">Met de `Get-Location` cmdlet wordt het volledige pad voor weer gegeven `Alias:` .</span><span class="sxs-lookup"><span data-stu-id="4c22f-144">The `Get-Location` cmdlet displays the complete path for `Alias:`.</span></span>
<span data-ttu-id="4c22f-145">`Get-ChildItem` Hiermee worden objecten van de pijp lijn naar de `Out-File` cmdlet verzonden.</span><span class="sxs-lookup"><span data-stu-id="4c22f-145">`Get-ChildItem` sends objects down the pipeline to the `Out-File` cmdlet.</span></span> <span data-ttu-id="4c22f-146">`Out-File` gebruikt de **filepath** para meter om het volledige pad en de bestands naam voor de uitvoer op te geven **C:\TestDir\AliasNames.txt**.</span><span class="sxs-lookup"><span data-stu-id="4c22f-146">`Out-File` uses the **FilePath** parameter to specify the complete path and filename for the output, **C:\TestDir\AliasNames.txt**.</span></span> <span data-ttu-id="4c22f-147">Met de `Get-Content` cmdlet wordt de para meter **Path** gebruikt en wordt de inhoud van het bestand weer gegeven in de Power shell-console.</span><span class="sxs-lookup"><span data-stu-id="4c22f-147">The `Get-Content` cmdlet uses the **Path** parameter and displays the file's content in the PowerShell console.</span></span>

## <span data-ttu-id="4c22f-148">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="4c22f-148">PARAMETERS</span></span>

### <span data-ttu-id="4c22f-149">-Toevoegen</span><span class="sxs-lookup"><span data-stu-id="4c22f-149">-Append</span></span>

<span data-ttu-id="4c22f-150">Hiermee wordt de uitvoer toegevoegd aan het einde van een bestaand bestand.</span><span class="sxs-lookup"><span data-stu-id="4c22f-150">Adds the output to the end of an existing file.</span></span>

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

### <span data-ttu-id="4c22f-151">-Encoding</span><span class="sxs-lookup"><span data-stu-id="4c22f-151">-Encoding</span></span>

<span data-ttu-id="4c22f-152">Hiermee geeft u het type code ring voor het doel bestand op.</span><span class="sxs-lookup"><span data-stu-id="4c22f-152">Specifies the type of encoding for the target file.</span></span> <span data-ttu-id="4c22f-153">De standaardwaarde is `utf8NoBOM`.</span><span class="sxs-lookup"><span data-stu-id="4c22f-153">The default value is `utf8NoBOM`.</span></span>

<span data-ttu-id="4c22f-154">De acceptabele waarden voor deze para meter zijn als volgt:</span><span class="sxs-lookup"><span data-stu-id="4c22f-154">The acceptable values for this parameter are as follows:</span></span>

- <span data-ttu-id="4c22f-155">`ascii`: Gebruikt de code ring voor de ASCII-tekenset (7-bits).</span><span class="sxs-lookup"><span data-stu-id="4c22f-155">`ascii`: Uses the encoding for the ASCII (7-bit) character set.</span></span>
- <span data-ttu-id="4c22f-156">`bigendianunicode`: Wordt gecodeerd in UTF-16-indeling met behulp van de byte volgorde big endian.</span><span class="sxs-lookup"><span data-stu-id="4c22f-156">`bigendianunicode`: Encodes in UTF-16 format using the big-endian byte order.</span></span>
- <span data-ttu-id="4c22f-157">`oem`: Maakt gebruik van de standaard codering voor MS-DOS-en console Programma's.</span><span class="sxs-lookup"><span data-stu-id="4c22f-157">`oem`: Uses the default encoding for MS-DOS and console programs.</span></span>
- <span data-ttu-id="4c22f-158">`unicode`: Wordt gecodeerd in UTF-16-indeling met behulp van de byte volgorde little endian.</span><span class="sxs-lookup"><span data-stu-id="4c22f-158">`unicode`: Encodes in UTF-16 format using the little-endian byte order.</span></span>
- <span data-ttu-id="4c22f-159">`utf7`: Wordt gecodeerd in de indeling UTF-7.</span><span class="sxs-lookup"><span data-stu-id="4c22f-159">`utf7`: Encodes in UTF-7 format.</span></span>
- <span data-ttu-id="4c22f-160">`utf8`: Wordt gecodeerd in UTF-8-indeling.</span><span class="sxs-lookup"><span data-stu-id="4c22f-160">`utf8`: Encodes in UTF-8 format.</span></span>
- <span data-ttu-id="4c22f-161">`utf8BOM`: Code ring in UTF-8-indeling met byte order Mark (BOM)</span><span class="sxs-lookup"><span data-stu-id="4c22f-161">`utf8BOM`: Encodes in UTF-8 format with Byte Order Mark (BOM)</span></span>
- <span data-ttu-id="4c22f-162">`utf8NoBOM`: Code ring in UTF-8-indeling zonder byte order Mark (BOM)</span><span class="sxs-lookup"><span data-stu-id="4c22f-162">`utf8NoBOM`: Encodes in UTF-8 format without Byte Order Mark (BOM)</span></span>
- <span data-ttu-id="4c22f-163">`utf32`: Gecodeerd in UTF-32-indeling.</span><span class="sxs-lookup"><span data-stu-id="4c22f-163">`utf32`: Encodes in UTF-32 format.</span></span>

<span data-ttu-id="4c22f-164">Vanaf Power shell 6,2 kunnen met de para meter **Encoding** ook numerieke id's van geregistreerde code pagina's (zoals `-Encoding 1251` ) of teken reeks namen van geregistreerde code pagina's (zoals) worden toegestaan `-Encoding "windows-1251"` .</span><span class="sxs-lookup"><span data-stu-id="4c22f-164">Beginning with PowerShell 6.2, the **Encoding** parameter also allows numeric IDs of registered code pages (like `-Encoding 1251`) or string names of registered code pages (like `-Encoding "windows-1251"`).</span></span> <span data-ttu-id="4c22f-165">Zie de .NET-documentatie voor [code ring. code tabel](/dotnet/api/system.text.encoding.codepage?view=netcore-2.2)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="4c22f-165">For more information, see the .NET documentation for [Encoding.CodePage](/dotnet/api/system.text.encoding.codepage?view=netcore-2.2).</span></span>

```yaml
Type: System.Text.Encoding
Parameter Sets: (All)
Aliases:
Accepted values: ASCII, BigEndianUnicode, OEM, Unicode, UTF7, UTF8, UTF8BOM, UTF8NoBOM, UTF32

Required: False
Position: 1
Default value: UTF8NoBOM
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="4c22f-166">-FilePath</span><span class="sxs-lookup"><span data-stu-id="4c22f-166">-FilePath</span></span>

<span data-ttu-id="4c22f-167">Hiermee geeft u het pad naar het uitvoer bestand.</span><span class="sxs-lookup"><span data-stu-id="4c22f-167">Specifies the path to the output file.</span></span>

```yaml
Type: System.String
Parameter Sets: ByPath
Aliases: Path

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="4c22f-168">-Force</span><span class="sxs-lookup"><span data-stu-id="4c22f-168">-Force</span></span>

<span data-ttu-id="4c22f-169">Onderdrukt het kenmerk alleen-lezen en overschrijft een bestaand alleen-lezen bestand.</span><span class="sxs-lookup"><span data-stu-id="4c22f-169">Overrides the read-only attribute and overwrites an existing read-only file.</span></span> <span data-ttu-id="4c22f-170">De para meter **Force** overschrijft geen beveiligings beperkingen.</span><span class="sxs-lookup"><span data-stu-id="4c22f-170">The **Force** parameter does not override security restrictions.</span></span>

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

### <span data-ttu-id="4c22f-171">-Input object</span><span class="sxs-lookup"><span data-stu-id="4c22f-171">-InputObject</span></span>

<span data-ttu-id="4c22f-172">Hiermee geeft u de objecten die naar het bestand moeten worden geschreven.</span><span class="sxs-lookup"><span data-stu-id="4c22f-172">Specifies the objects to be written to the file.</span></span> <span data-ttu-id="4c22f-173">Voer een variabele in die de objecten bevat of typ een opdracht of expressie waarmee de objecten worden opgehaald.</span><span class="sxs-lookup"><span data-stu-id="4c22f-173">Enter a variable that contains the objects or type a command or expression that gets the objects.</span></span>

```yaml
Type: System.Management.Automation.PSObject
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="4c22f-174">-LiteralPath</span><span class="sxs-lookup"><span data-stu-id="4c22f-174">-LiteralPath</span></span>

<span data-ttu-id="4c22f-175">Hiermee geeft u het pad naar het uitvoer bestand.</span><span class="sxs-lookup"><span data-stu-id="4c22f-175">Specifies the path to the output file.</span></span> <span data-ttu-id="4c22f-176">De para meter **LiteralPath** wordt exact gebruikt als deze wordt getypt.</span><span class="sxs-lookup"><span data-stu-id="4c22f-176">The **LiteralPath** parameter is used exactly as it is typed.</span></span>
<span data-ttu-id="4c22f-177">Jokertekens worden niet geaccepteerd.</span><span class="sxs-lookup"><span data-stu-id="4c22f-177">Wildcard characters are not accepted.</span></span> <span data-ttu-id="4c22f-178">Als het pad escape tekens bevat, plaatst u het tussen enkele aanhalings tekens.</span><span class="sxs-lookup"><span data-stu-id="4c22f-178">If the path includes escape characters, enclose it in single quotation marks.</span></span> <span data-ttu-id="4c22f-179">Enkele aanhalings tekens geven aan dat Power shell geen karakters interpreteert als escape reeksen.</span><span class="sxs-lookup"><span data-stu-id="4c22f-179">Single quotation marks tell PowerShell not to interpret any characters as escape sequences.</span></span> <span data-ttu-id="4c22f-180">Zie [about_Quoting_Rules](../Microsoft.Powershell.Core/About/about_Quoting_Rules.md)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="4c22f-180">For more information, see [about_Quoting_Rules](../Microsoft.Powershell.Core/About/about_Quoting_Rules.md).</span></span>

```yaml
Type: System.String
Parameter Sets: ByLiteralPath
Aliases: PSPath, LP

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="4c22f-181">-NoClobber</span><span class="sxs-lookup"><span data-stu-id="4c22f-181">-NoClobber</span></span>

<span data-ttu-id="4c22f-182">Met **NoClobber** wordt voor komen dat een bestaand bestand wordt overschreven en wordt een bericht weer gegeven dat het bestand al bestaat.</span><span class="sxs-lookup"><span data-stu-id="4c22f-182">**NoClobber** prevents an existing file from being overwritten and displays a message that the file already exists.</span></span> <span data-ttu-id="4c22f-183">Als een bestand bestaat in het opgegeven pad, wordt standaard `Out-File` het bestand overschreven zonder dat er een waarschuwing wordt gegeven.</span><span class="sxs-lookup"><span data-stu-id="4c22f-183">By default, if a file exists in the specified path, `Out-File` overwrites the file without warning.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: NoOverwrite

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="4c22f-184">-Nieuwe regel</span><span class="sxs-lookup"><span data-stu-id="4c22f-184">-NoNewline</span></span>

<span data-ttu-id="4c22f-185">Hiermee geeft u op dat de inhoud die naar het bestand wordt geschreven, niet eindigt met een teken voor een nieuwe regel.</span><span class="sxs-lookup"><span data-stu-id="4c22f-185">Specifies that the content written to the file does not end with a newline character.</span></span> <span data-ttu-id="4c22f-186">De teken reeks representaties van de invoer objecten worden samengevoegd om de uitvoer te vormen.</span><span class="sxs-lookup"><span data-stu-id="4c22f-186">The string representations of the input objects are concatenated to form the output.</span></span> <span data-ttu-id="4c22f-187">Er worden geen spaties of nieuwe regels tussen de uitvoer teken reeksen ingevoegd.</span><span class="sxs-lookup"><span data-stu-id="4c22f-187">No spaces or newlines are inserted between the output strings.</span></span> <span data-ttu-id="4c22f-188">Er wordt geen nieuwe regel toegevoegd na de laatste uitvoer teken reeks.</span><span class="sxs-lookup"><span data-stu-id="4c22f-188">No newline is added after the last output string.</span></span>

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

### <span data-ttu-id="4c22f-189">-Breedte</span><span class="sxs-lookup"><span data-stu-id="4c22f-189">-Width</span></span>

<span data-ttu-id="4c22f-190">Hiermee geeft u het aantal tekens in elke regel van uitvoer op.</span><span class="sxs-lookup"><span data-stu-id="4c22f-190">Specifies the number of characters in each line of output.</span></span> <span data-ttu-id="4c22f-191">Eventuele extra tekens worden afgekapt, niet verpakt.</span><span class="sxs-lookup"><span data-stu-id="4c22f-191">Any additional characters are truncated, not wrapped.</span></span> <span data-ttu-id="4c22f-192">Als deze para meter niet wordt gebruikt, wordt de breedte bepaald door de kenmerken van de host.</span><span class="sxs-lookup"><span data-stu-id="4c22f-192">If this parameter is not used, the width is determined by the characteristics of the host.</span></span> <span data-ttu-id="4c22f-193">De standaard instelling voor de Power shell-console is 80 tekens.</span><span class="sxs-lookup"><span data-stu-id="4c22f-193">The default for the PowerShell console is 80 characters.</span></span>

```yaml
Type: System.Int32
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="4c22f-194">-Confirm</span><span class="sxs-lookup"><span data-stu-id="4c22f-194">-Confirm</span></span>

<span data-ttu-id="4c22f-195">Hiermee wordt u gevraagd om bevestiging voordat u de cmdlet uitvoert.</span><span class="sxs-lookup"><span data-stu-id="4c22f-195">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="4c22f-196">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="4c22f-196">-WhatIf</span></span>

<span data-ttu-id="4c22f-197">Hiermee wordt weergegeven wat er zou gebeuren als u de cmdlet uitvoert.</span><span class="sxs-lookup"><span data-stu-id="4c22f-197">Shows what would happen if the cmdlet runs.</span></span> <span data-ttu-id="4c22f-198">De cmdlet wordt niet uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="4c22f-198">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="4c22f-199">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="4c22f-199">CommonParameters</span></span>

<span data-ttu-id="4c22f-200">Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="4c22f-200">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="4c22f-201">Zie [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="4c22f-201">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="4c22f-202">INVOER</span><span class="sxs-lookup"><span data-stu-id="4c22f-202">INPUTS</span></span>

### <span data-ttu-id="4c22f-203">System. Management. Automation. PSObject</span><span class="sxs-lookup"><span data-stu-id="4c22f-203">System.Management.Automation.PSObject</span></span>

<span data-ttu-id="4c22f-204">U kunt elk object door sluizen naar `Out-File` .</span><span class="sxs-lookup"><span data-stu-id="4c22f-204">You can pipe any object to `Out-File`.</span></span>

## <span data-ttu-id="4c22f-205">UITVOER</span><span class="sxs-lookup"><span data-stu-id="4c22f-205">OUTPUTS</span></span>

### <span data-ttu-id="4c22f-206">Geen</span><span class="sxs-lookup"><span data-stu-id="4c22f-206">None</span></span>

<span data-ttu-id="4c22f-207">`Out-File` Er wordt geen uitvoer gegenereerd.</span><span class="sxs-lookup"><span data-stu-id="4c22f-207">`Out-File` does not generate any output.</span></span>

## <span data-ttu-id="4c22f-208">OPMERKINGEN</span><span class="sxs-lookup"><span data-stu-id="4c22f-208">NOTES</span></span>

<span data-ttu-id="4c22f-209">Invoer objecten worden automatisch opgemaakt zoals ze zich in de terminal bevinden, maar u kunt een `Format-*` cmdlet gebruiken om de opmaak van de uitvoer naar het bestand expliciet te bepalen.</span><span class="sxs-lookup"><span data-stu-id="4c22f-209">Input objects are automatically formatted as they would be in the terminal, but you can use a `Format-*` cmdlet to explicitly control the formatting of the output to the file.</span></span> <span data-ttu-id="4c22f-210">bijvoorbeeld `Get-Date | Format-List | Out-File out.txt`</span><span class="sxs-lookup"><span data-stu-id="4c22f-210">For example, `Get-Date | Format-List | Out-File out.txt`</span></span>

<span data-ttu-id="4c22f-211">Als u de uitvoer van een Power shell-opdracht naar de cmdlet wilt verzenden `Out-File` , gebruikt u de pijp lijn.</span><span class="sxs-lookup"><span data-stu-id="4c22f-211">To send a PowerShell command's output to the `Out-File` cmdlet, use the pipeline.</span></span> <span data-ttu-id="4c22f-212">U kunt ook gegevens opslaan in een variabele en de para meter **input object** gebruiken om gegevens door te geven aan de `Out-File` cmdlet.</span><span class="sxs-lookup"><span data-stu-id="4c22f-212">Alternatively, you can store data in a variable and use the **InputObject** parameter to pass data to the `Out-File` cmdlet.</span></span>

<span data-ttu-id="4c22f-213">`Out-File` gegevens worden opgeslagen in een bestand, maar er worden geen uitvoer objecten naar de pijp lijn geproduceerd.</span><span class="sxs-lookup"><span data-stu-id="4c22f-213">`Out-File` saves data to a file but it does not produce any output objects to the pipeline.</span></span>

## <span data-ttu-id="4c22f-214">GERELATEERDE KOPPELINGEN</span><span class="sxs-lookup"><span data-stu-id="4c22f-214">RELATED LINKS</span></span>

[<span data-ttu-id="4c22f-215">about_Providers</span><span class="sxs-lookup"><span data-stu-id="4c22f-215">about_Providers</span></span>](../Microsoft.Powershell.Core/About/about_Providers.md)

[<span data-ttu-id="4c22f-216">about_Quoting_Rules</span><span class="sxs-lookup"><span data-stu-id="4c22f-216">about_Quoting_Rules</span></span>](../Microsoft.Powershell.Core/About/about_Quoting_Rules.md)

[<span data-ttu-id="4c22f-217">Out-standaard</span><span class="sxs-lookup"><span data-stu-id="4c22f-217">Out-Default</span></span>](../Microsoft.PowerShell.Core/Out-Default.md)

[<span data-ttu-id="4c22f-218">Out-host</span><span class="sxs-lookup"><span data-stu-id="4c22f-218">Out-Host</span></span>](../Microsoft.PowerShell.Core/Out-Host.md)

[<span data-ttu-id="4c22f-219">Out-Null</span><span class="sxs-lookup"><span data-stu-id="4c22f-219">Out-Null</span></span>](../Microsoft.PowerShell.Core/Out-Null.md)

[<span data-ttu-id="4c22f-220">Out-teken reeks</span><span class="sxs-lookup"><span data-stu-id="4c22f-220">Out-String</span></span>](Out-String.md)

[<span data-ttu-id="4c22f-221">T-object</span><span class="sxs-lookup"><span data-stu-id="4c22f-221">Tee-Object</span></span>](Tee-Object.md)
