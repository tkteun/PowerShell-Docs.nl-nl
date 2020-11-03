---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 09/21/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/out-file?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Out-File
ms.openlocfilehash: 71602cb0621c835257f556a0a9db15bd754a3aee
ms.sourcegitcommit: d757d64ea8c8af4d92596e8fbe15f2f40d48d3ac
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 09/22/2020
ms.locfileid: "93251949"
---
# <span data-ttu-id="b55c8-103">Out-File</span><span class="sxs-lookup"><span data-stu-id="b55c8-103">Out-File</span></span>

## <span data-ttu-id="b55c8-104">SAMENVATTING</span><span class="sxs-lookup"><span data-stu-id="b55c8-104">SYNOPSIS</span></span>
<span data-ttu-id="b55c8-105">Hiermee wordt de uitvoer naar een bestand verzonden.</span><span class="sxs-lookup"><span data-stu-id="b55c8-105">Sends output to a file.</span></span>

## <span data-ttu-id="b55c8-106">SYNTAXIS</span><span class="sxs-lookup"><span data-stu-id="b55c8-106">SYNTAX</span></span>

### <span data-ttu-id="b55c8-107">ByPath (standaard)</span><span class="sxs-lookup"><span data-stu-id="b55c8-107">ByPath (Default)</span></span>

```
Out-File [-FilePath] <string> [[-Encoding] <string>] [-Append] [-Force] [-NoClobber] [-Width <int>]
 [-NoNewline] [-InputObject <psobject>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="b55c8-108">ByLiteralPath</span><span class="sxs-lookup"><span data-stu-id="b55c8-108">ByLiteralPath</span></span>

```
Out-File [[-Encoding] <string>] -LiteralPath <string> [-Append] [-Force] [-NoClobber] [-Width <int>]
 [-NoNewline] [-InputObject <psobject>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="b55c8-109">BESCHRIJVING</span><span class="sxs-lookup"><span data-stu-id="b55c8-109">DESCRIPTION</span></span>

<span data-ttu-id="b55c8-110">De `Out-File` cmdlet verzendt uitvoer naar een bestand.</span><span class="sxs-lookup"><span data-stu-id="b55c8-110">The `Out-File` cmdlet sends output to a file.</span></span> <span data-ttu-id="b55c8-111">Het gebruik van het Power shell-opmaak systeem wordt impliciet gebruikt om naar het bestand te schrijven.</span><span class="sxs-lookup"><span data-stu-id="b55c8-111">It implicitly uses PowerShell's formatting system to write to the file.</span></span> <span data-ttu-id="b55c8-112">Het bestand ontvangt dezelfde weergave representatie als de Terminal.</span><span class="sxs-lookup"><span data-stu-id="b55c8-112">The file receives the same display representation as the terminal.</span></span> <span data-ttu-id="b55c8-113">Dit betekent dat de uitvoer mogelijk niet ideaal is voor programma verwerking, tenzij alle invoer objecten teken reeksen zijn.</span><span class="sxs-lookup"><span data-stu-id="b55c8-113">This means that the output may not be ideal for programmatic processing unless all input objects are strings.</span></span>
<span data-ttu-id="b55c8-114">Wanneer u para meters voor de uitvoer wilt opgeven, gebruikt u `Out-File` in plaats van de omleidings operator ( `>` ).</span><span class="sxs-lookup"><span data-stu-id="b55c8-114">When you need to specify parameters for the output, use `Out-File` rather than the redirection operator (`>`).</span></span> <span data-ttu-id="b55c8-115">Zie [about_Redirection](../Microsoft.PowerShell.Core/About/about_Redirection.md)voor meer informatie over omleiding.</span><span class="sxs-lookup"><span data-stu-id="b55c8-115">For more information about redirection, see [about_Redirection](../Microsoft.PowerShell.Core/About/about_Redirection.md).</span></span>

## <span data-ttu-id="b55c8-116">VOORBEELDEN</span><span class="sxs-lookup"><span data-stu-id="b55c8-116">EXAMPLES</span></span>

### <span data-ttu-id="b55c8-117">Voor beeld 1: uitvoer verzenden en een bestand maken</span><span class="sxs-lookup"><span data-stu-id="b55c8-117">Example 1: Send output and create a file</span></span>

<span data-ttu-id="b55c8-118">In dit voor beeld ziet u hoe u een lijst met de processen van de lokale computer naar een bestand verzendt.</span><span class="sxs-lookup"><span data-stu-id="b55c8-118">This example shows how to send a list of the local computer's processes to a file.</span></span> <span data-ttu-id="b55c8-119">Als het bestand niet bestaat, `Out-File` maakt het bestand in het opgegeven pad.</span><span class="sxs-lookup"><span data-stu-id="b55c8-119">If the file does not exist, `Out-File` creates the file in the specified path.</span></span>

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

<span data-ttu-id="b55c8-120">De `Get-Process` cmdlet haalt een lijst op met processen die worden uitgevoerd op de lokale computer.</span><span class="sxs-lookup"><span data-stu-id="b55c8-120">The `Get-Process` cmdlet gets the list of processes running on the local computer.</span></span> <span data-ttu-id="b55c8-121">De **proces** objecten worden in de pijp lijn naar de `Out-File` cmdlet verzonden.</span><span class="sxs-lookup"><span data-stu-id="b55c8-121">The **Process** objects are sent down the pipeline to the `Out-File` cmdlet.</span></span> <span data-ttu-id="b55c8-122">`Out-File` maakt gebruik van de **filepath** para meter en maakt een bestand in de huidige map met de naam **Process.txt**.</span><span class="sxs-lookup"><span data-stu-id="b55c8-122">`Out-File` uses the **FilePath** parameter and creates a file in the current directory named **Process.txt**.</span></span> <span data-ttu-id="b55c8-123">De `Get-Content` opdracht haalt inhoud op uit het bestand en geeft deze weer in de Power shell-console.</span><span class="sxs-lookup"><span data-stu-id="b55c8-123">The `Get-Content` command gets content from the file and displays it in the PowerShell console.</span></span>

### <span data-ttu-id="b55c8-124">Voor beeld 2: voor komen dat een bestaand bestand wordt overschreven</span><span class="sxs-lookup"><span data-stu-id="b55c8-124">Example 2: Prevent an existing file from being overwritten</span></span>

<span data-ttu-id="b55c8-125">In dit voor beeld wordt voor komen dat een bestaand bestand wordt overschreven.</span><span class="sxs-lookup"><span data-stu-id="b55c8-125">This example prevents an existing file from being overwritten.</span></span> <span data-ttu-id="b55c8-126">Standaard worden `Out-File` bestaande bestanden overschreven.</span><span class="sxs-lookup"><span data-stu-id="b55c8-126">By default, `Out-File` overwrites existing files.</span></span>

```powershell
Get-Process | Out-File -FilePath .\Process.txt -NoClobber
```

```Output
Out-File : The file 'C:\Test\Process.txt' already exists.
At line:1 char:15
+ Get-Process | Out-File -FilePath .\Process.txt -NoClobber
+               ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
```

<span data-ttu-id="b55c8-127">De `Get-Process` cmdlet haalt een lijst op met processen die worden uitgevoerd op de lokale computer.</span><span class="sxs-lookup"><span data-stu-id="b55c8-127">The `Get-Process` cmdlet gets the list of processes running on the local computer.</span></span> <span data-ttu-id="b55c8-128">De **proces** objecten worden in de pijp lijn naar de `Out-File` cmdlet verzonden.</span><span class="sxs-lookup"><span data-stu-id="b55c8-128">The **Process** objects are sent down the pipeline to the `Out-File` cmdlet.</span></span> <span data-ttu-id="b55c8-129">`Out-File` maakt gebruik van de **filepath** para meter en probeert te schrijven naar een bestand in de huidige map met de naam **Process.txt**.</span><span class="sxs-lookup"><span data-stu-id="b55c8-129">`Out-File` uses the **FilePath** parameter and attempts to write to a file in the current directory named **Process.txt**.</span></span> <span data-ttu-id="b55c8-130">Met de para meter **NoClobber** wordt voor komen dat het bestand wordt overschreven en wordt een bericht weer gegeven dat het bestand al bestaat.</span><span class="sxs-lookup"><span data-stu-id="b55c8-130">The **NoClobber** parameter prevents the file from being overwritten and displays a message that the file already exists.</span></span>

### <span data-ttu-id="b55c8-131">Voor beeld 3: uitvoer naar een bestand in ASCII-indeling verzenden</span><span class="sxs-lookup"><span data-stu-id="b55c8-131">Example 3: Send output to a file in ASCII format</span></span>

<span data-ttu-id="b55c8-132">In dit voor beeld ziet u hoe uitvoer wordt gecodeerd met een specifiek coderings type.</span><span class="sxs-lookup"><span data-stu-id="b55c8-132">This example shows how to encode output with a specific encoding type.</span></span>

```powershell
$Procs = Get-Process
Out-File -FilePath .\Process.txt -InputObject $Procs -Encoding ASCII -Width 50
```

<span data-ttu-id="b55c8-133">De `Get-Process` cmdlet haalt een lijst op met processen die worden uitgevoerd op de lokale computer.</span><span class="sxs-lookup"><span data-stu-id="b55c8-133">The `Get-Process` cmdlet gets the list of processes running on the local computer.</span></span> <span data-ttu-id="b55c8-134">De **proces** objecten worden opgeslagen in de variabele `$Procs` .</span><span class="sxs-lookup"><span data-stu-id="b55c8-134">The **Process** objects are stored in the variable, `$Procs`.</span></span> <span data-ttu-id="b55c8-135">`Out-File` maakt gebruik van de **filepath** para meter en maakt een bestand in de huidige map met de naam **Process.txt**.</span><span class="sxs-lookup"><span data-stu-id="b55c8-135">`Out-File` uses the **FilePath** parameter and creates a file in the current directory named **Process.txt**.</span></span> <span data-ttu-id="b55c8-136">De **input object** para meter geeft de proces objecten door in `$Procs` de bestands **Process.txt**.</span><span class="sxs-lookup"><span data-stu-id="b55c8-136">The **InputObject** parameter passes the process objects in `$Procs` to the file **Process.txt**.</span></span> <span data-ttu-id="b55c8-137">De para meter **Encoding** converteert de uitvoer naar **ASCII** -indeling.</span><span class="sxs-lookup"><span data-stu-id="b55c8-137">The **Encoding** parameter converts the output to **ASCII** format.</span></span> <span data-ttu-id="b55c8-138">De para meter **breedte** beperkt elke regel in het bestand tot 50 tekens, waardoor sommige gegevens kunnen worden afgekapt.</span><span class="sxs-lookup"><span data-stu-id="b55c8-138">The **Width** parameter limits each line in the file to 50 characters so some data might be truncated.</span></span>

### <span data-ttu-id="b55c8-139">Voor beeld 4: een provider gebruiken en uitvoer naar een bestand verzenden</span><span class="sxs-lookup"><span data-stu-id="b55c8-139">Example 4: Use a provider and send output to a file</span></span>

<span data-ttu-id="b55c8-140">In dit voor beeld ziet u hoe u de `Out-File` cmdlet gebruikt wanneer u zich niet in een **File System** -provider station bevindt.</span><span class="sxs-lookup"><span data-stu-id="b55c8-140">This example shows how to use the `Out-File` cmdlet when you are not in a **FileSystem** provider drive.</span></span> <span data-ttu-id="b55c8-141">Gebruik de `Get-PSProvider` cmdlet om de providers op uw lokale computer weer te geven.</span><span class="sxs-lookup"><span data-stu-id="b55c8-141">Use the `Get-PSProvider` cmdlet to view the providers on your local computer.</span></span> <span data-ttu-id="b55c8-142">Zie [about_Providers](../Microsoft.Powershell.Core/About/about_Providers.md)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="b55c8-142">For more information, see [about_Providers](../Microsoft.Powershell.Core/About/about_Providers.md).</span></span>

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

<span data-ttu-id="b55c8-143">De `Set-Location` opdracht gebruikt de para meter **Path** om de huidige locatie van de register provider in te stellen `Alias:` .</span><span class="sxs-lookup"><span data-stu-id="b55c8-143">The `Set-Location` command uses the **Path** parameter to set the current location to the registry provider `Alias:`.</span></span> <span data-ttu-id="b55c8-144">Met de `Get-Location` cmdlet wordt het volledige pad voor weer gegeven `Alias:` .</span><span class="sxs-lookup"><span data-stu-id="b55c8-144">The `Get-Location` cmdlet displays the complete path for `Alias:`.</span></span>
<span data-ttu-id="b55c8-145">`Get-ChildItem` Hiermee worden objecten van de pijp lijn naar de `Out-File` cmdlet verzonden.</span><span class="sxs-lookup"><span data-stu-id="b55c8-145">`Get-ChildItem` sends objects down the pipeline to the `Out-File` cmdlet.</span></span> <span data-ttu-id="b55c8-146">`Out-File` gebruikt de **filepath** para meter om het volledige pad en de bestands naam voor de uitvoer op te geven **C:\TestDir\AliasNames.txt**.</span><span class="sxs-lookup"><span data-stu-id="b55c8-146">`Out-File` uses the **FilePath** parameter to specify the complete path and filename for the output, **C:\TestDir\AliasNames.txt**.</span></span> <span data-ttu-id="b55c8-147">Met de `Get-Content` cmdlet wordt de para meter **Path** gebruikt en wordt de inhoud van het bestand weer gegeven in de Power shell-console.</span><span class="sxs-lookup"><span data-stu-id="b55c8-147">The `Get-Content` cmdlet uses the **Path** parameter and displays the file's content in the PowerShell console.</span></span>

## <span data-ttu-id="b55c8-148">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="b55c8-148">PARAMETERS</span></span>

### <span data-ttu-id="b55c8-149">-Toevoegen</span><span class="sxs-lookup"><span data-stu-id="b55c8-149">-Append</span></span>

<span data-ttu-id="b55c8-150">Hiermee wordt de uitvoer toegevoegd aan het einde van een bestaand bestand.</span><span class="sxs-lookup"><span data-stu-id="b55c8-150">Adds the output to the end of an existing file.</span></span> <span data-ttu-id="b55c8-151">Als er geen **code ring** is opgegeven, gebruikt de cmdlet de standaard codering.</span><span class="sxs-lookup"><span data-stu-id="b55c8-151">If no **Encoding** is specified, the cmdlet uses the default encoding.</span></span> <span data-ttu-id="b55c8-152">Deze code ring komt mogelijk niet overeen met de code ring van het doel bestand.</span><span class="sxs-lookup"><span data-stu-id="b55c8-152">That encoding may not match the encoding of the target file.</span></span> <span data-ttu-id="b55c8-153">Dit is hetzelfde gedrag als de omleidings operator ( `>>` ).</span><span class="sxs-lookup"><span data-stu-id="b55c8-153">This is the same behavior as the redirection operator (`>>`).</span></span>

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

### <span data-ttu-id="b55c8-154">-Encoding</span><span class="sxs-lookup"><span data-stu-id="b55c8-154">-Encoding</span></span>

<span data-ttu-id="b55c8-155">Hiermee geeft u het type code ring voor het doel bestand op.</span><span class="sxs-lookup"><span data-stu-id="b55c8-155">Specifies the type of encoding for the target file.</span></span> <span data-ttu-id="b55c8-156">De standaardwaarde is `unicode`.</span><span class="sxs-lookup"><span data-stu-id="b55c8-156">The default value is `unicode`.</span></span>

<span data-ttu-id="b55c8-157">De acceptabele waarden voor deze para meter zijn als volgt:</span><span class="sxs-lookup"><span data-stu-id="b55c8-157">The acceptable values for this parameter are as follows:</span></span>

- <span data-ttu-id="b55c8-158">`ascii` Maakt gebruik van ASCII-tekenset (7-bits).</span><span class="sxs-lookup"><span data-stu-id="b55c8-158">`ascii` Uses ASCII (7-bit) character set.</span></span>
- <span data-ttu-id="b55c8-159">`bigendianunicode` Maakt gebruik van UTF-16 met de byte volgorde big endian.</span><span class="sxs-lookup"><span data-stu-id="b55c8-159">`bigendianunicode` Uses UTF-16 with the big-endian byte order.</span></span>
- <span data-ttu-id="b55c8-160">`default` Gebruikt de code ring die overeenkomt met de actieve code tabel van het systeem (meestal ANSI).</span><span class="sxs-lookup"><span data-stu-id="b55c8-160">`default` Uses the encoding that corresponds to the system's active code page (usually ANSI).</span></span>
- <span data-ttu-id="b55c8-161">`oem` Gebruikt de code ring die overeenkomt met de huidige OEM-code tabel van het systeem.</span><span class="sxs-lookup"><span data-stu-id="b55c8-161">`oem` Uses the encoding that corresponds to the system's current OEM code page.</span></span>
- <span data-ttu-id="b55c8-162">`string` Hetzelfde als `unicode` .</span><span class="sxs-lookup"><span data-stu-id="b55c8-162">`string` Same as `unicode`.</span></span>
- <span data-ttu-id="b55c8-163">`unicode` Maakt gebruik van UTF-16 met de byte volgorde little endian.</span><span class="sxs-lookup"><span data-stu-id="b55c8-163">`unicode` Uses UTF-16 with the little-endian byte order.</span></span>
- <span data-ttu-id="b55c8-164">`unknown` Hetzelfde als `unicode` .</span><span class="sxs-lookup"><span data-stu-id="b55c8-164">`unknown` Same as `unicode`.</span></span>
- <span data-ttu-id="b55c8-165">`utf7` Maakt gebruik van UTF-7.</span><span class="sxs-lookup"><span data-stu-id="b55c8-165">`utf7` Uses UTF-7.</span></span>
- <span data-ttu-id="b55c8-166">`utf8` Maakt gebruik van UTF-8.</span><span class="sxs-lookup"><span data-stu-id="b55c8-166">`utf8` Uses UTF-8.</span></span>
- <span data-ttu-id="b55c8-167">`utf32` Maakt gebruik van UTF-32 met de byte volgorde little endian.</span><span class="sxs-lookup"><span data-stu-id="b55c8-167">`utf32` Uses UTF-32 with the little-endian byte order.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:
Accepted values: ASCII, BigEndianUnicode, Default, OEM, String, Unicode, Unknown, UTF7, UTF8, UTF32

Required: False
Position: 1
Default value: Unicode
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="b55c8-168">-FilePath</span><span class="sxs-lookup"><span data-stu-id="b55c8-168">-FilePath</span></span>

<span data-ttu-id="b55c8-169">Hiermee geeft u het pad naar het uitvoer bestand.</span><span class="sxs-lookup"><span data-stu-id="b55c8-169">Specifies the path to the output file.</span></span>

```yaml
Type: System.String
Parameter Sets: ByPath
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="b55c8-170">-Force</span><span class="sxs-lookup"><span data-stu-id="b55c8-170">-Force</span></span>

<span data-ttu-id="b55c8-171">Onderdrukt het kenmerk alleen-lezen en overschrijft een bestaand alleen-lezen bestand.</span><span class="sxs-lookup"><span data-stu-id="b55c8-171">Overrides the read-only attribute and overwrites an existing read-only file.</span></span> <span data-ttu-id="b55c8-172">De para meter **Force** overschrijft geen beveiligings beperkingen.</span><span class="sxs-lookup"><span data-stu-id="b55c8-172">The **Force** parameter does not override security restrictions.</span></span>

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

### <span data-ttu-id="b55c8-173">-Input object</span><span class="sxs-lookup"><span data-stu-id="b55c8-173">-InputObject</span></span>

<span data-ttu-id="b55c8-174">Hiermee geeft u de objecten die naar het bestand moeten worden geschreven.</span><span class="sxs-lookup"><span data-stu-id="b55c8-174">Specifies the objects to be written to the file.</span></span> <span data-ttu-id="b55c8-175">Voer een variabele in die de objecten bevat of typ een opdracht of expressie waarmee de objecten worden opgehaald.</span><span class="sxs-lookup"><span data-stu-id="b55c8-175">Enter a variable that contains the objects or type a command or expression that gets the objects.</span></span>

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

### <span data-ttu-id="b55c8-176">-LiteralPath</span><span class="sxs-lookup"><span data-stu-id="b55c8-176">-LiteralPath</span></span>

<span data-ttu-id="b55c8-177">Hiermee geeft u het pad naar het uitvoer bestand.</span><span class="sxs-lookup"><span data-stu-id="b55c8-177">Specifies the path to the output file.</span></span> <span data-ttu-id="b55c8-178">De para meter **LiteralPath** wordt exact gebruikt als deze wordt getypt.</span><span class="sxs-lookup"><span data-stu-id="b55c8-178">The **LiteralPath** parameter is used exactly as it is typed.</span></span>
<span data-ttu-id="b55c8-179">Jokertekens worden niet geaccepteerd.</span><span class="sxs-lookup"><span data-stu-id="b55c8-179">Wildcard characters are not accepted.</span></span> <span data-ttu-id="b55c8-180">Als het pad escape tekens bevat, plaatst u het tussen enkele aanhalings tekens.</span><span class="sxs-lookup"><span data-stu-id="b55c8-180">If the path includes escape characters, enclose it in single quotation marks.</span></span> <span data-ttu-id="b55c8-181">Enkele aanhalings tekens geven aan dat Power shell geen karakters interpreteert als escape reeksen.</span><span class="sxs-lookup"><span data-stu-id="b55c8-181">Single quotation marks tell PowerShell not to interpret any characters as escape sequences.</span></span> <span data-ttu-id="b55c8-182">Zie [about_Quoting_Rules](../Microsoft.Powershell.Core/About/about_Quoting_Rules.md)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="b55c8-182">For more information, see [about_Quoting_Rules](../Microsoft.Powershell.Core/About/about_Quoting_Rules.md).</span></span>

```yaml
Type: System.String
Parameter Sets: ByLiteralPath
Aliases: PSPath

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="b55c8-183">-NoClobber</span><span class="sxs-lookup"><span data-stu-id="b55c8-183">-NoClobber</span></span>

<span data-ttu-id="b55c8-184">Met **NoClobber** wordt voor komen dat een bestaand bestand wordt overschreven en wordt een bericht weer gegeven dat het bestand al bestaat.</span><span class="sxs-lookup"><span data-stu-id="b55c8-184">**NoClobber** prevents an existing file from being overwritten and displays a message that the file already exists.</span></span> <span data-ttu-id="b55c8-185">Als een bestand bestaat in het opgegeven pad, wordt standaard `Out-File` het bestand overschreven zonder dat er een waarschuwing wordt gegeven.</span><span class="sxs-lookup"><span data-stu-id="b55c8-185">By default, if a file exists in the specified path, `Out-File` overwrites the file without warning.</span></span>

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

### <span data-ttu-id="b55c8-186">-Nieuwe regel</span><span class="sxs-lookup"><span data-stu-id="b55c8-186">-NoNewline</span></span>

<span data-ttu-id="b55c8-187">Hiermee geeft u op dat de inhoud die naar het bestand wordt geschreven, niet eindigt met een teken voor een nieuwe regel.</span><span class="sxs-lookup"><span data-stu-id="b55c8-187">Specifies that the content written to the file does not end with a newline character.</span></span> <span data-ttu-id="b55c8-188">De teken reeks representaties van de invoer objecten worden samengevoegd om de uitvoer te vormen.</span><span class="sxs-lookup"><span data-stu-id="b55c8-188">The string representations of the input objects are concatenated to form the output.</span></span> <span data-ttu-id="b55c8-189">Er worden geen spaties of nieuwe regels tussen de uitvoer teken reeksen ingevoegd.</span><span class="sxs-lookup"><span data-stu-id="b55c8-189">No spaces or newlines are inserted between the output strings.</span></span> <span data-ttu-id="b55c8-190">Er wordt geen nieuwe regel toegevoegd na de laatste uitvoer teken reeks.</span><span class="sxs-lookup"><span data-stu-id="b55c8-190">No newline is added after the last output string.</span></span>

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

### <span data-ttu-id="b55c8-191">-Breedte</span><span class="sxs-lookup"><span data-stu-id="b55c8-191">-Width</span></span>

<span data-ttu-id="b55c8-192">Hiermee geeft u het aantal tekens in elke regel van uitvoer op.</span><span class="sxs-lookup"><span data-stu-id="b55c8-192">Specifies the number of characters in each line of output.</span></span> <span data-ttu-id="b55c8-193">Eventuele extra tekens worden afgekapt, niet verpakt.</span><span class="sxs-lookup"><span data-stu-id="b55c8-193">Any additional characters are truncated, not wrapped.</span></span> <span data-ttu-id="b55c8-194">Als deze para meter niet wordt gebruikt, wordt de breedte bepaald door de kenmerken van de host.</span><span class="sxs-lookup"><span data-stu-id="b55c8-194">If this parameter is not used, the width is determined by the characteristics of the host.</span></span> <span data-ttu-id="b55c8-195">De standaard instelling voor de Power shell-console is 80 tekens.</span><span class="sxs-lookup"><span data-stu-id="b55c8-195">The default for the PowerShell console is 80 characters.</span></span>

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

### <span data-ttu-id="b55c8-196">-Confirm</span><span class="sxs-lookup"><span data-stu-id="b55c8-196">-Confirm</span></span>

<span data-ttu-id="b55c8-197">Hiermee wordt u gevraagd om bevestiging voordat u de cmdlet uitvoert.</span><span class="sxs-lookup"><span data-stu-id="b55c8-197">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="b55c8-198">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="b55c8-198">-WhatIf</span></span>

<span data-ttu-id="b55c8-199">Hiermee wordt weergegeven wat er zou gebeuren als u de cmdlet uitvoert.</span><span class="sxs-lookup"><span data-stu-id="b55c8-199">Shows what would happen if the cmdlet runs.</span></span> <span data-ttu-id="b55c8-200">De cmdlet wordt niet uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="b55c8-200">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="b55c8-201">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="b55c8-201">CommonParameters</span></span>

<span data-ttu-id="b55c8-202">Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="b55c8-202">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="b55c8-203">Zie [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="b55c8-203">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="b55c8-204">INVOER</span><span class="sxs-lookup"><span data-stu-id="b55c8-204">INPUTS</span></span>

### <span data-ttu-id="b55c8-205">System. Management. Automation. PSObject</span><span class="sxs-lookup"><span data-stu-id="b55c8-205">System.Management.Automation.PSObject</span></span>

<span data-ttu-id="b55c8-206">U kunt elk object door sluizen naar `Out-File` .</span><span class="sxs-lookup"><span data-stu-id="b55c8-206">You can pipe any object to `Out-File`.</span></span>

## <span data-ttu-id="b55c8-207">UITVOER</span><span class="sxs-lookup"><span data-stu-id="b55c8-207">OUTPUTS</span></span>

### <span data-ttu-id="b55c8-208">Geen</span><span class="sxs-lookup"><span data-stu-id="b55c8-208">None</span></span>

<span data-ttu-id="b55c8-209">`Out-File` Er wordt geen uitvoer gegenereerd.</span><span class="sxs-lookup"><span data-stu-id="b55c8-209">`Out-File` does not generate any output.</span></span>

## <span data-ttu-id="b55c8-210">OPMERKINGEN</span><span class="sxs-lookup"><span data-stu-id="b55c8-210">NOTES</span></span>

<span data-ttu-id="b55c8-211">Invoer objecten worden automatisch opgemaakt zoals ze zich in de terminal bevinden, maar u kunt een `Format-*` cmdlet gebruiken om de opmaak van de uitvoer naar het bestand expliciet te bepalen.</span><span class="sxs-lookup"><span data-stu-id="b55c8-211">Input objects are automatically formatted as they would be in the terminal, but you can use a `Format-*` cmdlet to explicitly control the formatting of the output to the file.</span></span> <span data-ttu-id="b55c8-212">bijvoorbeeld `Get-Date | Format-List | Out-File out.txt`</span><span class="sxs-lookup"><span data-stu-id="b55c8-212">For example, `Get-Date | Format-List | Out-File out.txt`</span></span>

<span data-ttu-id="b55c8-213">Als u de uitvoer van een Power shell-opdracht naar de cmdlet wilt verzenden `Out-File` , gebruikt u de pijp lijn.</span><span class="sxs-lookup"><span data-stu-id="b55c8-213">To send a PowerShell command's output to the `Out-File` cmdlet, use the pipeline.</span></span> <span data-ttu-id="b55c8-214">U kunt ook gegevens opslaan in een variabele en de para meter **input object** gebruiken om gegevens door te geven aan de `Out-File` cmdlet.</span><span class="sxs-lookup"><span data-stu-id="b55c8-214">Alternatively, you can store data in a variable and use the **InputObject** parameter to pass data to the `Out-File` cmdlet.</span></span>

<span data-ttu-id="b55c8-215">`Out-File` gegevens worden opgeslagen in een bestand, maar er worden geen uitvoer objecten naar de pijp lijn geproduceerd.</span><span class="sxs-lookup"><span data-stu-id="b55c8-215">`Out-File` saves data to a file but it does not produce any output objects to the pipeline.</span></span>

## <span data-ttu-id="b55c8-216">GERELATEERDE KOPPELINGEN</span><span class="sxs-lookup"><span data-stu-id="b55c8-216">RELATED LINKS</span></span>

[<span data-ttu-id="b55c8-217">about_Providers</span><span class="sxs-lookup"><span data-stu-id="b55c8-217">about_Providers</span></span>](../Microsoft.Powershell.Core/About/about_Providers.md)

[<span data-ttu-id="b55c8-218">about_Quoting_Rules</span><span class="sxs-lookup"><span data-stu-id="b55c8-218">about_Quoting_Rules</span></span>](../Microsoft.Powershell.Core/About/about_Quoting_Rules.md)

[<span data-ttu-id="b55c8-219">Out-standaard</span><span class="sxs-lookup"><span data-stu-id="b55c8-219">Out-Default</span></span>](../Microsoft.PowerShell.Core/Out-Default.md)

[<span data-ttu-id="b55c8-220">Out-GridView</span><span class="sxs-lookup"><span data-stu-id="b55c8-220">Out-GridView</span></span>](Out-GridView.md)

[<span data-ttu-id="b55c8-221">Out-host</span><span class="sxs-lookup"><span data-stu-id="b55c8-221">Out-Host</span></span>](../Microsoft.PowerShell.Core/Out-Host.md)

[<span data-ttu-id="b55c8-222">Out-Null</span><span class="sxs-lookup"><span data-stu-id="b55c8-222">Out-Null</span></span>](../Microsoft.PowerShell.Core/Out-Null.md)

[<span data-ttu-id="b55c8-223">Out-Printer</span><span class="sxs-lookup"><span data-stu-id="b55c8-223">Out-Printer</span></span>](Out-Printer.md)

[<span data-ttu-id="b55c8-224">Out-teken reeks</span><span class="sxs-lookup"><span data-stu-id="b55c8-224">Out-String</span></span>](Out-String.md)

[<span data-ttu-id="b55c8-225">T-object</span><span class="sxs-lookup"><span data-stu-id="b55c8-225">Tee-Object</span></span>](Tee-Object.md)
