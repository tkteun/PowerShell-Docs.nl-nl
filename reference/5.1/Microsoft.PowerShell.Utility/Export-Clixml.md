---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 08/14/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/export-clixml?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Export-Clixml
ms.openlocfilehash: 8485591165cce0425c85d52fbd31d40614af6249
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/07/2020
ms.locfileid: "93250459"
---
# <span data-ttu-id="73d19-103">Export-Clixml</span><span class="sxs-lookup"><span data-stu-id="73d19-103">Export-Clixml</span></span>

## <span data-ttu-id="73d19-104">SAMENVATTING</span><span class="sxs-lookup"><span data-stu-id="73d19-104">SYNOPSIS</span></span>
<span data-ttu-id="73d19-105">Hiermee maakt u een XML-weer gave van een object of objecten en slaat u deze op in een bestand.</span><span class="sxs-lookup"><span data-stu-id="73d19-105">Creates an XML-based representation of an object or objects and stores it in a file.</span></span>

## <span data-ttu-id="73d19-106">SYNTAXIS</span><span class="sxs-lookup"><span data-stu-id="73d19-106">SYNTAX</span></span>

### <span data-ttu-id="73d19-107">ByPath (standaard)</span><span class="sxs-lookup"><span data-stu-id="73d19-107">ByPath (Default)</span></span>

```
Export-Clixml [-Path] <String> -InputObject <PSObject> [-Depth <Int32>] [-Force] [-NoClobber]
 [-Encoding <String>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="73d19-108">ByLiteralPath</span><span class="sxs-lookup"><span data-stu-id="73d19-108">ByLiteralPath</span></span>

```
Export-Clixml -LiteralPath <String> -InputObject <PSObject> [-Depth <Int32>] [-Force] [-NoClobber]
 [-Encoding <String>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="73d19-109">BESCHRIJVING</span><span class="sxs-lookup"><span data-stu-id="73d19-109">DESCRIPTION</span></span>

<span data-ttu-id="73d19-110">`Export-Clixml`Met de cmdlet maakt u een XML-weer gave op basis van een gemeen schappelijke taal infrastructuur (CLI) van een object of objecten en slaat u deze op in een bestand.</span><span class="sxs-lookup"><span data-stu-id="73d19-110">The `Export-Clixml` cmdlet creates a Common Language Infrastructure (CLI) XML-based representation of an object or objects and stores it in a file.</span></span> <span data-ttu-id="73d19-111">U kunt de cmdlet vervolgens gebruiken `Import-Clixml` om het opgeslagen object opnieuw te maken op basis van de inhoud van het bestand.</span><span class="sxs-lookup"><span data-stu-id="73d19-111">You can then use the `Import-Clixml` cmdlet to recreate the saved object based on the contents of that file.</span></span>
<span data-ttu-id="73d19-112">Zie [taal onafhankelijkheid](/dotnet/standard/language-independence)voor meer informatie over cli.</span><span class="sxs-lookup"><span data-stu-id="73d19-112">For more information about CLI, see [Language independence](/dotnet/standard/language-independence).</span></span>

<span data-ttu-id="73d19-113">Deze cmdlet is vergelijkbaar met `ConvertTo-Xml` , behalve dat `Export-Clixml` de resulterende XML in een bestand wordt opgeslagen.</span><span class="sxs-lookup"><span data-stu-id="73d19-113">This cmdlet is similar to `ConvertTo-Xml`, except that `Export-Clixml` stores the resulting XML in a file.</span></span> <span data-ttu-id="73d19-114">`ConvertTo-XML` retourneert de XML, zodat u deze kunt blijven verwerken in Power shell.</span><span class="sxs-lookup"><span data-stu-id="73d19-114">`ConvertTo-XML` returns the XML, so you can continue to process it in PowerShell.</span></span>

<span data-ttu-id="73d19-115">Een waardevol gebruik van `Export-Clixml` op Windows-computers is het exporteren van referenties en het veilig beveiligen van teken reeksen als XML.</span><span class="sxs-lookup"><span data-stu-id="73d19-115">A valuable use of `Export-Clixml` on Windows computers is to export credentials and secure strings securely as XML.</span></span> <span data-ttu-id="73d19-116">Zie voor beeld 3.</span><span class="sxs-lookup"><span data-stu-id="73d19-116">For an example, see Example 3.</span></span>

## <span data-ttu-id="73d19-117">VOORBEELDEN</span><span class="sxs-lookup"><span data-stu-id="73d19-117">EXAMPLES</span></span>

### <span data-ttu-id="73d19-118">Voor beeld 1: een teken reeks exporteren naar een XML-bestand</span><span class="sxs-lookup"><span data-stu-id="73d19-118">Example 1: Export a string to an XML file</span></span>

<span data-ttu-id="73d19-119">In dit voor beeld wordt een XML-bestand gemaakt dat wordt opgeslagen in de huidige map. Dit is een weer gave van de teken reeks **Dit is een test**.</span><span class="sxs-lookup"><span data-stu-id="73d19-119">This example creates an XML file that stores in the current directory, a representation of the string **This is a test**.</span></span>

```powershell
"This is a test" | Export-Clixml -Path .\sample.xml
```

<span data-ttu-id="73d19-120">De teken reeks die **Dit is, wordt een test** verzonden naar de pijp lijn.</span><span class="sxs-lookup"><span data-stu-id="73d19-120">The string **This is a test** is sent down the pipeline.</span></span> <span data-ttu-id="73d19-121">`Export-Clixml` maakt gebruik van de para meter **Path** voor het maken van een XML-bestand met `sample.xml` de naam in de huidige map.</span><span class="sxs-lookup"><span data-stu-id="73d19-121">`Export-Clixml` uses the **Path** parameter to create an XML file named `sample.xml` in the current directory.</span></span>

### <span data-ttu-id="73d19-122">Voor beeld 2: een object exporteren naar een XML-bestand</span><span class="sxs-lookup"><span data-stu-id="73d19-122">Example 2: Export an object to an XML file</span></span>

<span data-ttu-id="73d19-123">In dit voor beeld ziet u hoe u een object exporteert naar een XML-bestand en vervolgens een object maakt door de XML uit het bestand te importeren.</span><span class="sxs-lookup"><span data-stu-id="73d19-123">This example shows how to export an object to an XML file and then create an object by importing the XML from the file.</span></span>

```powershell
Get-Acl C:\test.txt | Export-Clixml -Path .\FileACL.xml
$fileacl = Import-Clixml -Path .\FileACL.xml
```

<span data-ttu-id="73d19-124">De `Get-Acl` cmdlet haalt de security descriptor van het `Test.txt` bestand op.</span><span class="sxs-lookup"><span data-stu-id="73d19-124">The `Get-Acl` cmdlet gets the security descriptor of the `Test.txt` file.</span></span> <span data-ttu-id="73d19-125">Het object wordt via de pijp lijn verzonden om de security descriptor aan te geven `Export-Clixml` .</span><span class="sxs-lookup"><span data-stu-id="73d19-125">It sends the object down the pipeline to pass the security descriptor to `Export-Clixml`.</span></span> <span data-ttu-id="73d19-126">De XML-weer gave van het object wordt opgeslagen in een bestand met de naam `FileACL.xml` .</span><span class="sxs-lookup"><span data-stu-id="73d19-126">The XML-based representation of the object is stored in a file named `FileACL.xml`.</span></span>

<span data-ttu-id="73d19-127">De `Import-Clixml` cmdlet maakt een object van de XML in het `FileACL.xml` bestand.</span><span class="sxs-lookup"><span data-stu-id="73d19-127">The `Import-Clixml` cmdlet creates an object from the XML in the `FileACL.xml` file.</span></span> <span data-ttu-id="73d19-128">Vervolgens wordt het object in de variabele opgeslagen `$fileacl` .</span><span class="sxs-lookup"><span data-stu-id="73d19-128">Then, it saves the object in the `$fileacl` variable.</span></span>

### <span data-ttu-id="73d19-129">Voor beeld 3: een geëxporteerd referentie object versleutelen</span><span class="sxs-lookup"><span data-stu-id="73d19-129">Example 3: Encrypt an exported credential object</span></span>

<span data-ttu-id="73d19-130">In dit voor beeld krijgt u een referentie die u hebt opgeslagen in de `$Credential` variabele door de `Get-Credential` cmdlet uit te voeren, kunt u de `Export-Clixml` cmdlet uitvoeren om de referentie op schijf op te slaan.</span><span class="sxs-lookup"><span data-stu-id="73d19-130">In this example, given a credential that you've stored in the `$Credential` variable by running the `Get-Credential` cmdlet, you can run the `Export-Clixml` cmdlet to save the credential to disk.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="73d19-131">`Export-Clixml` exporteert alleen versleutelde referenties in Windows.</span><span class="sxs-lookup"><span data-stu-id="73d19-131">`Export-Clixml` only exports encrypted credentials on Windows.</span></span> <span data-ttu-id="73d19-132">Op niet-Windows-besturings systemen, zoals macOS en Linux, worden referenties geëxporteerd als tekst zonder opmaak.</span><span class="sxs-lookup"><span data-stu-id="73d19-132">On non-Windows operating systems such as macOS and Linux, credentials are exported in plain text.</span></span>

```powershell
$Credxmlpath = Join-Path (Split-Path $Profile) TestScript.ps1.credential
$Credential | Export-Clixml $Credxmlpath
$Credxmlpath = Join-Path (Split-Path $Profile) TestScript.ps1.credential
$Credential = Import-Clixml $Credxmlpath
```

<span data-ttu-id="73d19-133">`Export-Clixml`Met de cmdlet worden referentie objecten versleuteld met behulp van de Windows [Data Protection-API](/previous-versions/windows/apps/hh464970(v=win.10)).</span><span class="sxs-lookup"><span data-stu-id="73d19-133">The `Export-Clixml` cmdlet encrypts credential objects by using the Windows [Data Protection API](/previous-versions/windows/apps/hh464970(v=win.10)).</span></span>
<span data-ttu-id="73d19-134">De versleuteling zorgt ervoor dat alleen uw gebruikers account alleen op die computer de inhoud van het referentie object kan ontsleutelen.</span><span class="sxs-lookup"><span data-stu-id="73d19-134">The encryption ensures that only your user account on only that computer can decrypt the contents of the credential object.</span></span> <span data-ttu-id="73d19-135">Het geëxporteerde `CLIXML` bestand kan niet worden gebruikt op een andere computer of door een andere gebruiker.</span><span class="sxs-lookup"><span data-stu-id="73d19-135">The exported `CLIXML` file can't be used on a different computer or by a different user.</span></span>

<span data-ttu-id="73d19-136">In het voor beeld wordt het bestand waarin de referentie is opgeslagen vertegenwoordigd door `TestScript.ps1.credential` .</span><span class="sxs-lookup"><span data-stu-id="73d19-136">In the example, the file in which the credential is stored is represented by `TestScript.ps1.credential`.</span></span> <span data-ttu-id="73d19-137">Vervang **TestScript** door de naam van het script waarmee u de referentie laadt.</span><span class="sxs-lookup"><span data-stu-id="73d19-137">Replace **TestScript** with the name of the script with which you're loading the credential.</span></span>

<span data-ttu-id="73d19-138">U stuurt het referentie object omlaag in de pijp lijn naar `Export-Clixml` en slaat het op in het pad, `$Credxmlpath` , dat u hebt opgegeven in de eerste opdracht.</span><span class="sxs-lookup"><span data-stu-id="73d19-138">You send the credential object down the pipeline to `Export-Clixml`, and save it to the path, `$Credxmlpath`, that you specified in the first command.</span></span>

<span data-ttu-id="73d19-139">Als u de referentie automatisch wilt importeren in uw script, voert u de laatste twee opdrachten uit.</span><span class="sxs-lookup"><span data-stu-id="73d19-139">To import the credential automatically into your script, run the final two commands.</span></span> <span data-ttu-id="73d19-140">Voer uit `Import-Clixml` om het beveiligde referentie object te importeren in uw script.</span><span class="sxs-lookup"><span data-stu-id="73d19-140">Run `Import-Clixml` to import the secured credential object into your script.</span></span> <span data-ttu-id="73d19-141">Deze import elimineert het risico dat wacht woorden met onbewerkte tekst in uw script worden weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="73d19-141">This import eliminates the risk of exposing plain-text passwords in your script.</span></span>

## <span data-ttu-id="73d19-142">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="73d19-142">PARAMETERS</span></span>

### <span data-ttu-id="73d19-143">-Confirm</span><span class="sxs-lookup"><span data-stu-id="73d19-143">-Confirm</span></span>

<span data-ttu-id="73d19-144">Hiermee wordt u gevraagd om bevestiging voordat u de cmdlet uitvoert.</span><span class="sxs-lookup"><span data-stu-id="73d19-144">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="73d19-145">-Diepte</span><span class="sxs-lookup"><span data-stu-id="73d19-145">-Depth</span></span>

<span data-ttu-id="73d19-146">Hiermee geeft u op hoeveel niveaus van Inge sloten objecten worden opgenomen in de XML-weer gave.</span><span class="sxs-lookup"><span data-stu-id="73d19-146">Specifies how many levels of contained objects are included in the XML representation.</span></span> <span data-ttu-id="73d19-147">De standaardwaarde is `2`.</span><span class="sxs-lookup"><span data-stu-id="73d19-147">The default value is `2`.</span></span>

<span data-ttu-id="73d19-148">De standaard waarde kan worden overschreven voor het object type in de `Types.ps1xml` bestanden.</span><span class="sxs-lookup"><span data-stu-id="73d19-148">The default value can be overridden for the object type in the `Types.ps1xml` files.</span></span> <span data-ttu-id="73d19-149">Zie [about_Types.ps1XML](../Microsoft.PowerShell.Core/About/about_Types.ps1xml.md)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="73d19-149">For more information, see [about_Types.ps1xml](../Microsoft.PowerShell.Core/About/about_Types.ps1xml.md).</span></span>

```yaml
Type: System.Int32
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: 2
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="73d19-150">-Encoding</span><span class="sxs-lookup"><span data-stu-id="73d19-150">-Encoding</span></span>

<span data-ttu-id="73d19-151">Hiermee geeft u het type code ring voor het doel bestand op.</span><span class="sxs-lookup"><span data-stu-id="73d19-151">Specifies the type of encoding for the target file.</span></span> <span data-ttu-id="73d19-152">De standaard waarde is **Unicode**.</span><span class="sxs-lookup"><span data-stu-id="73d19-152">The default value is **Unicode**.</span></span>

<span data-ttu-id="73d19-153">De acceptabele waarden voor deze para meter zijn als volgt:</span><span class="sxs-lookup"><span data-stu-id="73d19-153">The acceptable values for this parameter are as follows:</span></span>

- <span data-ttu-id="73d19-154">`ASCII` Maakt gebruik van ASCII-tekenset (7-bits).</span><span class="sxs-lookup"><span data-stu-id="73d19-154">`ASCII` Uses ASCII (7-bit) character set.</span></span>
- <span data-ttu-id="73d19-155">`BigEndianUnicode` Maakt gebruik van UTF-16 met de byte volgorde big endian.</span><span class="sxs-lookup"><span data-stu-id="73d19-155">`BigEndianUnicode` Uses UTF-16 with the big-endian byte order.</span></span>
- <span data-ttu-id="73d19-156">`Default` Gebruikt de code ring die overeenkomt met de actieve code tabel van het systeem (meestal ANSI).</span><span class="sxs-lookup"><span data-stu-id="73d19-156">`Default` Uses the encoding that corresponds to the system's active code page (usually ANSI).</span></span>
- <span data-ttu-id="73d19-157">`OEM` Gebruikt de code ring die overeenkomt met de huidige OEM-code tabel van het systeem.</span><span class="sxs-lookup"><span data-stu-id="73d19-157">`OEM` Uses the encoding that corresponds to the system's current OEM code page.</span></span>
- <span data-ttu-id="73d19-158">`Unicode` Maakt gebruik van UTF-16 met de byte volgorde little endian.</span><span class="sxs-lookup"><span data-stu-id="73d19-158">`Unicode` Uses UTF-16 with the little-endian byte order.</span></span>
- <span data-ttu-id="73d19-159">`UTF7` Maakt gebruik van UTF-7.</span><span class="sxs-lookup"><span data-stu-id="73d19-159">`UTF7` Uses UTF-7.</span></span>
- <span data-ttu-id="73d19-160">`UTF8` Maakt gebruik van UTF-8.</span><span class="sxs-lookup"><span data-stu-id="73d19-160">`UTF8` Uses UTF-8.</span></span>
- <span data-ttu-id="73d19-161">`UTF32` Maakt gebruik van UTF-32 met de byte volgorde little endian.</span><span class="sxs-lookup"><span data-stu-id="73d19-161">`UTF32` Uses UTF-32 with the little-endian byte order.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:
Accepted values: ASCII, BigEndianUnicode, Default, OEM, Unicode, UTF7, UTF8, UTF32

Required: False
Position: Named
Default value: Unicode
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="73d19-162">-Force</span><span class="sxs-lookup"><span data-stu-id="73d19-162">-Force</span></span>

<span data-ttu-id="73d19-163">Hiermee wordt de opdracht uitgevoerd zonder dat de gebruiker om bevestiging wordt gevraagd.</span><span class="sxs-lookup"><span data-stu-id="73d19-163">Forces the command to run without asking for user confirmation.</span></span>

<span data-ttu-id="73d19-164">Hiermee wordt de cmdlet zo nodig gewist van het alleen-lezen kenmerk van het uitvoer bestand.</span><span class="sxs-lookup"><span data-stu-id="73d19-164">Causes the cmdlet to clear the read-only attribute of the output file if necessary.</span></span> <span data-ttu-id="73d19-165">De cmdlet probeert het kenmerk alleen-lezen opnieuw in te stellen wanneer de opdracht is voltooid.</span><span class="sxs-lookup"><span data-stu-id="73d19-165">The cmdlet will attempt to reset the read-only attribute when the command completes.</span></span>

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

### <span data-ttu-id="73d19-166">-Input object</span><span class="sxs-lookup"><span data-stu-id="73d19-166">-InputObject</span></span>

<span data-ttu-id="73d19-167">Geeft het object aan dat moet worden geconverteerd.</span><span class="sxs-lookup"><span data-stu-id="73d19-167">Specifies the object to be converted.</span></span> <span data-ttu-id="73d19-168">Voer een variabele in die de objecten bevat, of typ een opdracht of expressie waarmee de objecten worden opgehaald.</span><span class="sxs-lookup"><span data-stu-id="73d19-168">Enter a variable that contains the objects, or type a command or expression that gets the objects.</span></span> <span data-ttu-id="73d19-169">U kunt ook objecten pipeen naar `Export-Clixml` .</span><span class="sxs-lookup"><span data-stu-id="73d19-169">You can also pipe objects to `Export-Clixml`.</span></span>

```yaml
Type: System.Management.Automation.PSObject
Parameter Sets: (All)
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="73d19-170">-LiteralPath</span><span class="sxs-lookup"><span data-stu-id="73d19-170">-LiteralPath</span></span>

<span data-ttu-id="73d19-171">Hiermee geeft u het pad op naar het bestand waarin de XML-weer gave van het object wordt opgeslagen.</span><span class="sxs-lookup"><span data-stu-id="73d19-171">Specifies the path to the file where the XML representation of the object will be stored.</span></span> <span data-ttu-id="73d19-172">In tegens telling tot **Path** wordt de waarde van de para meter **LiteralPath** exact gebruikt zoals deze wordt getypt.</span><span class="sxs-lookup"><span data-stu-id="73d19-172">Unlike **Path** , the value of the **LiteralPath** parameter is used exactly as it's typed.</span></span> <span data-ttu-id="73d19-173">Geen tekens worden geïnterpreteerd als joker tekens.</span><span class="sxs-lookup"><span data-stu-id="73d19-173">No characters are interpreted as wildcards.</span></span> <span data-ttu-id="73d19-174">Als het pad escape tekens bevat, plaatst u het tussen enkele aanhalings tekens.</span><span class="sxs-lookup"><span data-stu-id="73d19-174">If the path includes escape characters, enclose it in single quotation marks.</span></span> <span data-ttu-id="73d19-175">Enkele aanhalings tekens geven aan dat Power shell geen karakters interpreteert als escape reeksen.</span><span class="sxs-lookup"><span data-stu-id="73d19-175">Single quotation marks tell PowerShell not to interpret any characters as escape sequences.</span></span>

```yaml
Type: System.String
Parameter Sets: ByLiteralPath
Aliases: PSPath

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="73d19-176">-NoClobber</span><span class="sxs-lookup"><span data-stu-id="73d19-176">-NoClobber</span></span>

<span data-ttu-id="73d19-177">Geeft aan dat de cmdlet de inhoud van een bestaand bestand niet overschrijft.</span><span class="sxs-lookup"><span data-stu-id="73d19-177">Indicates that the cmdlet doesn't overwrite the contents of an existing file.</span></span> <span data-ttu-id="73d19-178">Als een bestand bestaat in het opgegeven pad, wordt standaard `Export-Clixml` het bestand overschreven zonder dat er een waarschuwing wordt gegeven.</span><span class="sxs-lookup"><span data-stu-id="73d19-178">By default, if a file exists in the specified path, `Export-Clixml` overwrites the file without warning.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: NoOverwrite

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="73d19-179">-Path</span><span class="sxs-lookup"><span data-stu-id="73d19-179">-Path</span></span>

<span data-ttu-id="73d19-180">Hiermee geeft u het pad op naar het bestand waarin de XML-weer gave van het object wordt opgeslagen.</span><span class="sxs-lookup"><span data-stu-id="73d19-180">Specifies the path to the file where the XML representation of the object will be stored.</span></span>

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

### <span data-ttu-id="73d19-181">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="73d19-181">-WhatIf</span></span>

<span data-ttu-id="73d19-182">Hiermee wordt weergegeven wat er zou gebeuren als u de cmdlet uitvoert.</span><span class="sxs-lookup"><span data-stu-id="73d19-182">Shows what would happen if the cmdlet runs.</span></span> <span data-ttu-id="73d19-183">De cmdlet wordt niet uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="73d19-183">The cmdlet isn't run.</span></span>

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

### <span data-ttu-id="73d19-184">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="73d19-184">CommonParameters</span></span>

<span data-ttu-id="73d19-185">Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="73d19-185">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="73d19-186">Zie [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="73d19-186">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="73d19-187">INVOER</span><span class="sxs-lookup"><span data-stu-id="73d19-187">INPUTS</span></span>

### <span data-ttu-id="73d19-188">System. Management. Automation. PSObject</span><span class="sxs-lookup"><span data-stu-id="73d19-188">System.Management.Automation.PSObject</span></span>

<span data-ttu-id="73d19-189">U kunt elk object pijp lijnen naar `Export-Clixml` .</span><span class="sxs-lookup"><span data-stu-id="73d19-189">You can pipeline any object to `Export-Clixml`.</span></span>

## <span data-ttu-id="73d19-190">UITVOER</span><span class="sxs-lookup"><span data-stu-id="73d19-190">OUTPUTS</span></span>

### <span data-ttu-id="73d19-191">System. IO. file info</span><span class="sxs-lookup"><span data-stu-id="73d19-191">System.IO.FileInfo</span></span>

<span data-ttu-id="73d19-192">`Export-Clixml` Hiermee maakt u een bestand dat de XML bevat.</span><span class="sxs-lookup"><span data-stu-id="73d19-192">`Export-Clixml` creates a file that contains the XML.</span></span>

## <span data-ttu-id="73d19-193">OPMERKINGEN</span><span class="sxs-lookup"><span data-stu-id="73d19-193">NOTES</span></span>

## <span data-ttu-id="73d19-194">GERELATEERDE KOPPELINGEN</span><span class="sxs-lookup"><span data-stu-id="73d19-194">RELATED LINKS</span></span>

[<span data-ttu-id="73d19-195">ConvertTo-Html</span><span class="sxs-lookup"><span data-stu-id="73d19-195">ConvertTo-Html</span></span>](ConvertTo-Html.md)

[<span data-ttu-id="73d19-196">ConvertTo-Xml</span><span class="sxs-lookup"><span data-stu-id="73d19-196">ConvertTo-Xml</span></span>](ConvertTo-Xml.md)

[<span data-ttu-id="73d19-197">Exporteren-CSV</span><span class="sxs-lookup"><span data-stu-id="73d19-197">Export-Csv</span></span>](Export-Csv.md)

[<span data-ttu-id="73d19-198">Import-Clixml</span><span class="sxs-lookup"><span data-stu-id="73d19-198">Import-Clixml</span></span>](Import-Clixml.md)

[<span data-ttu-id="73d19-199">Pad voor samen voegen</span><span class="sxs-lookup"><span data-stu-id="73d19-199">Join-Path</span></span>](../Microsoft.PowerShell.Management/Join-Path.md)

[<span data-ttu-id="73d19-200">Referenties veilig opslaan op schijf</span><span class="sxs-lookup"><span data-stu-id="73d19-200">Securely Store Credentials on Disk</span></span>](https://powershellcookbook.com/recipe/PukO/securely-store-credentials-on-disk)

[<span data-ttu-id="73d19-201">Power shell gebruiken om referenties door te geven aan verouderde systemen</span><span class="sxs-lookup"><span data-stu-id="73d19-201">Use PowerShell to Pass Credentials to Legacy Systems</span></span>](https://devblogs.microsoft.com/scripting/use-powershell-to-pass-credentials-to-legacy-systems/)

[<span data-ttu-id="73d19-202">Windows. Security. Cryptography. DataProtection</span><span class="sxs-lookup"><span data-stu-id="73d19-202">Windows.Security.Cryptography.DataProtection</span></span>](/uwp/api/windows.security.cryptography.dataprotection)
