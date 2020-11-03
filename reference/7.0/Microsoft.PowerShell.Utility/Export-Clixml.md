---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 05/21/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/export-clixml?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Export-Clixml
ms.openlocfilehash: b75a40dc2a89dd9a170de3037c43eda39b21f3d4
ms.sourcegitcommit: de63e9481cf8024883060aae61fb02c59c2de662
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/03/2020
ms.locfileid: "93249671"
---
# <span data-ttu-id="75675-103">Export-Clixml</span><span class="sxs-lookup"><span data-stu-id="75675-103">Export-Clixml</span></span>

## <span data-ttu-id="75675-104">SAMENVATTING</span><span class="sxs-lookup"><span data-stu-id="75675-104">SYNOPSIS</span></span>
<span data-ttu-id="75675-105">Hiermee maakt u een XML-weer gave van een object of objecten en slaat u deze op in een bestand.</span><span class="sxs-lookup"><span data-stu-id="75675-105">Creates an XML-based representation of an object or objects and stores it in a file.</span></span>

## <span data-ttu-id="75675-106">SYNTAXIS</span><span class="sxs-lookup"><span data-stu-id="75675-106">SYNTAX</span></span>

### <span data-ttu-id="75675-107">ByPath (standaard)</span><span class="sxs-lookup"><span data-stu-id="75675-107">ByPath (Default)</span></span>

```
Export-Clixml [-Depth <Int32>] [-Path] <String> -InputObject <PSObject> [-Force] [-NoClobber]
 [-Encoding <Encoding>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="75675-108">ByLiteralPath</span><span class="sxs-lookup"><span data-stu-id="75675-108">ByLiteralPath</span></span>

```
Export-Clixml [-Depth <Int32>] -LiteralPath <String> -InputObject <PSObject> [-Force] [-NoClobber]
 [-Encoding <Encoding>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="75675-109">BESCHRIJVING</span><span class="sxs-lookup"><span data-stu-id="75675-109">DESCRIPTION</span></span>

<span data-ttu-id="75675-110">`Export-Clixml`Met de cmdlet maakt u een XML-weer gave op basis van een gemeen schappelijke taal infrastructuur (CLI) van een object of objecten en slaat u deze op in een bestand.</span><span class="sxs-lookup"><span data-stu-id="75675-110">The `Export-Clixml` cmdlet creates a Common Language Infrastructure (CLI) XML-based representation of an object or objects and stores it in a file.</span></span> <span data-ttu-id="75675-111">U kunt de cmdlet vervolgens gebruiken `Import-Clixml` om het opgeslagen object opnieuw te maken op basis van de inhoud van het bestand.</span><span class="sxs-lookup"><span data-stu-id="75675-111">You can then use the `Import-Clixml` cmdlet to recreate the saved object based on the contents of that file.</span></span>
<span data-ttu-id="75675-112">Zie [taal onafhankelijkheid](/dotnet/standard/language-independence)voor meer informatie over cli.</span><span class="sxs-lookup"><span data-stu-id="75675-112">For more information about CLI, see [Language independence](/dotnet/standard/language-independence).</span></span>

<span data-ttu-id="75675-113">Deze cmdlet is vergelijkbaar met `ConvertTo-Xml` , behalve dat `Export-Clixml` de resulterende XML in een bestand wordt opgeslagen.</span><span class="sxs-lookup"><span data-stu-id="75675-113">This cmdlet is similar to `ConvertTo-Xml`, except that `Export-Clixml` stores the resulting XML in a file.</span></span> <span data-ttu-id="75675-114">`ConvertTo-XML` retourneert de XML, zodat u deze kunt blijven verwerken in Power shell.</span><span class="sxs-lookup"><span data-stu-id="75675-114">`ConvertTo-XML` returns the XML, so you can continue to process it in PowerShell.</span></span>

<span data-ttu-id="75675-115">Een waardevol gebruik van `Export-Clixml` op Windows-computers is het exporteren van referenties en het veilig beveiligen van teken reeksen als XML.</span><span class="sxs-lookup"><span data-stu-id="75675-115">A valuable use of `Export-Clixml` on Windows computers is to export credentials and secure strings securely as XML.</span></span> <span data-ttu-id="75675-116">Zie voor beeld 3.</span><span class="sxs-lookup"><span data-stu-id="75675-116">For an example, see Example 3.</span></span>

## <span data-ttu-id="75675-117">VOORBEELDEN</span><span class="sxs-lookup"><span data-stu-id="75675-117">EXAMPLES</span></span>

### <span data-ttu-id="75675-118">Voor beeld 1: een teken reeks exporteren naar een XML-bestand</span><span class="sxs-lookup"><span data-stu-id="75675-118">Example 1: Export a string to an XML file</span></span>

<span data-ttu-id="75675-119">In dit voor beeld wordt een XML-bestand gemaakt dat wordt opgeslagen in de huidige map. Dit is een weer gave van de teken reeks **Dit is een test**.</span><span class="sxs-lookup"><span data-stu-id="75675-119">This example creates an XML file that stores in the current directory, a representation of the string **This is a test**.</span></span>

```powershell
"This is a test" | Export-Clixml -Path .\sample.xml
```

<span data-ttu-id="75675-120">De teken reeks die **Dit is, wordt een test** verzonden naar de pijp lijn.</span><span class="sxs-lookup"><span data-stu-id="75675-120">The string **This is a test** is sent down the pipeline.</span></span> <span data-ttu-id="75675-121">`Export-Clixml` maakt gebruik van de para meter **Path** voor het maken van een XML-bestand met `sample.xml` de naam in de huidige map.</span><span class="sxs-lookup"><span data-stu-id="75675-121">`Export-Clixml` uses the **Path** parameter to create an XML file named `sample.xml` in the current directory.</span></span>

### <span data-ttu-id="75675-122">Voor beeld 2: een object exporteren naar een XML-bestand</span><span class="sxs-lookup"><span data-stu-id="75675-122">Example 2: Export an object to an XML file</span></span>

<span data-ttu-id="75675-123">In dit voor beeld ziet u hoe u een object exporteert naar een XML-bestand en vervolgens een object maakt door de XML uit het bestand te importeren.</span><span class="sxs-lookup"><span data-stu-id="75675-123">This example shows how to export an object to an XML file and then create an object by importing the XML from the file.</span></span>

```powershell
Get-Acl C:\test.txt | Export-Clixml -Path .\FileACL.xml
$fileacl = Import-Clixml -Path .\FileACL.xml
```

<span data-ttu-id="75675-124">De `Get-Acl` cmdlet haalt de security descriptor van het `Test.txt` bestand op.</span><span class="sxs-lookup"><span data-stu-id="75675-124">The `Get-Acl` cmdlet gets the security descriptor of the `Test.txt` file.</span></span> <span data-ttu-id="75675-125">Het object wordt via de pijp lijn verzonden om de security descriptor aan te geven `Export-Clixml` .</span><span class="sxs-lookup"><span data-stu-id="75675-125">It sends the object down the pipeline to pass the security descriptor to `Export-Clixml`.</span></span> <span data-ttu-id="75675-126">De XML-weer gave van het object wordt opgeslagen in een bestand met de naam `FileACL.xml` .</span><span class="sxs-lookup"><span data-stu-id="75675-126">The XML-based representation of the object is stored in a file named `FileACL.xml`.</span></span>

<span data-ttu-id="75675-127">De `Import-Clixml` cmdlet maakt een object van de XML in het `FileACL.xml` bestand.</span><span class="sxs-lookup"><span data-stu-id="75675-127">The `Import-Clixml` cmdlet creates an object from the XML in the `FileACL.xml` file.</span></span> <span data-ttu-id="75675-128">Vervolgens wordt het object in de variabele opgeslagen `$fileacl` .</span><span class="sxs-lookup"><span data-stu-id="75675-128">Then, it saves the object in the `$fileacl` variable.</span></span>

### <span data-ttu-id="75675-129">Voor beeld 3: een geëxporteerd referentie object in Windows versleutelen</span><span class="sxs-lookup"><span data-stu-id="75675-129">Example 3: Encrypt an exported credential object on Windows</span></span>

<span data-ttu-id="75675-130">In dit voor beeld krijgt u een referentie die u hebt opgeslagen in de `$Credential` variabele door de `Get-Credential` cmdlet uit te voeren, kunt u de `Export-Clixml` cmdlet uitvoeren om de referentie op schijf op te slaan.</span><span class="sxs-lookup"><span data-stu-id="75675-130">In this example, given a credential that you've stored in the `$Credential` variable by running the `Get-Credential` cmdlet, you can run the `Export-Clixml` cmdlet to save the credential to disk.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="75675-131">`Export-Clixml` exporteert alleen versleutelde referenties in Windows.</span><span class="sxs-lookup"><span data-stu-id="75675-131">`Export-Clixml` only exports encrypted credentials on Windows.</span></span> <span data-ttu-id="75675-132">Op niet-Windows-besturings systemen, zoals macOS en Linux, worden referenties geëxporteerd als tekst zonder opmaak, opgeslagen als een Unicode-teken reeks.</span><span class="sxs-lookup"><span data-stu-id="75675-132">On non-Windows operating systems such as macOS and Linux, credentials are exported as a plain text stored as a Unicode character array.</span></span> <span data-ttu-id="75675-133">Dit biedt een zekere mate van uitzonde ring, maar biedt geen versleuteling.</span><span class="sxs-lookup"><span data-stu-id="75675-133">This provides some obfuscation but does not provide encryption.</span></span>

```powershell
$Credxmlpath = Join-Path (Split-Path $Profile) TestScript.ps1.credential
$Credential | Export-Clixml $Credxmlpath
$Credxmlpath = Join-Path (Split-Path $Profile) TestScript.ps1.credential
$Credential = Import-Clixml $Credxmlpath
```

<span data-ttu-id="75675-134">`Export-Clixml`Met de cmdlet worden referentie objecten versleuteld met behulp van de Windows [Data Protection-API](/previous-versions/windows/apps/hh464970(v=win.10)).</span><span class="sxs-lookup"><span data-stu-id="75675-134">The `Export-Clixml` cmdlet encrypts credential objects by using the Windows [Data Protection API](/previous-versions/windows/apps/hh464970(v=win.10)).</span></span> <span data-ttu-id="75675-135">De versleuteling zorgt ervoor dat alleen uw gebruikers account alleen op die computer de inhoud van het referentie object kan ontsleutelen.</span><span class="sxs-lookup"><span data-stu-id="75675-135">The encryption ensures that only your user account on only that computer can decrypt the contents of the credential object.</span></span>
<span data-ttu-id="75675-136">Het geëxporteerde `CLIXML` bestand kan niet worden gebruikt op een andere computer of door een andere gebruiker.</span><span class="sxs-lookup"><span data-stu-id="75675-136">The exported `CLIXML` file can't be used on a different computer or by a different user.</span></span>

<span data-ttu-id="75675-137">In het voor beeld wordt het bestand waarin de referentie is opgeslagen vertegenwoordigd door `TestScript.ps1.credential` .</span><span class="sxs-lookup"><span data-stu-id="75675-137">In the example, the file in which the credential is stored is represented by `TestScript.ps1.credential`.</span></span> <span data-ttu-id="75675-138">Vervang **TestScript** door de naam van het script waarmee u de referentie laadt.</span><span class="sxs-lookup"><span data-stu-id="75675-138">Replace **TestScript** with the name of the script with which you're loading the credential.</span></span>

<span data-ttu-id="75675-139">U stuurt het referentie object omlaag in de pijp lijn naar `Export-Clixml` en slaat het op in het pad, `$Credxmlpath` , dat u hebt opgegeven in de eerste opdracht.</span><span class="sxs-lookup"><span data-stu-id="75675-139">You send the credential object down the pipeline to `Export-Clixml`, and save it to the path, `$Credxmlpath`, that you specified in the first command.</span></span>

<span data-ttu-id="75675-140">Als u de referentie automatisch wilt importeren in uw script, voert u de laatste twee opdrachten uit.</span><span class="sxs-lookup"><span data-stu-id="75675-140">To import the credential automatically into your script, run the final two commands.</span></span> <span data-ttu-id="75675-141">Voer uit `Import-Clixml` om het beveiligde referentie object te importeren in uw script.</span><span class="sxs-lookup"><span data-stu-id="75675-141">Run `Import-Clixml` to import the secured credential object into your script.</span></span> <span data-ttu-id="75675-142">Deze import elimineert het risico dat wacht woorden met onbewerkte tekst in uw script worden weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="75675-142">This import eliminates the risk of exposing plain-text passwords in your script.</span></span>

### <span data-ttu-id="75675-143">Voor beeld 4: een referentie object exporteren in Linux of macOS</span><span class="sxs-lookup"><span data-stu-id="75675-143">Example 4: Exporting a credential object on Linux or macOS</span></span>

<span data-ttu-id="75675-144">In dit voor beeld maken we een **PSCredential** in de `$Credential` variabele met behulp van de- `Get-Credential` cmdlet.</span><span class="sxs-lookup"><span data-stu-id="75675-144">In this example, we create a **PSCredential** in the `$Credential` variable using the `Get-Credential` cmdlet.</span></span> <span data-ttu-id="75675-145">Vervolgens wordt gebruikt `Export-Clixml` om de referentie op schijf op te slaan.</span><span class="sxs-lookup"><span data-stu-id="75675-145">Then we use `Export-Clixml` to save the credential to disk.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="75675-146">`Export-Clixml` exporteert alleen versleutelde referenties in Windows.</span><span class="sxs-lookup"><span data-stu-id="75675-146">`Export-Clixml` only exports encrypted credentials on Windows.</span></span> <span data-ttu-id="75675-147">Op niet-Windows-besturings systemen, zoals macOS en Linux, worden referenties geëxporteerd als tekst zonder opmaak, opgeslagen als een Unicode-teken reeks.</span><span class="sxs-lookup"><span data-stu-id="75675-147">On non-Windows operating systems such as macOS and Linux, credentials are exported as a plain text stored as a Unicode character array.</span></span> <span data-ttu-id="75675-148">Dit biedt een zekere mate van uitzonde ring, maar biedt geen versleuteling.</span><span class="sxs-lookup"><span data-stu-id="75675-148">This provides some obfuscation but does not provide encryption.</span></span>

```powershell
PS> $Credential = Get-Credential

PowerShell credential request
Enter your credentials.
User: User1
Password for user User1: ********

PS> $Credential | Export-Clixml ./cred2.xml
PS> Get-Content ./cred2.xml

...
    <Props>
      <S N="UserName">User1</S>
      <SS N="Password">700061007300730077006f0072006400</SS>
    </Props>
...

PS> 'password' | Format-Hex -Encoding unicode

   Label: String (System.String) <52D60C91>

          Offset Bytes                                           Ascii
                 00 01 02 03 04 05 06 07 08 09 0A 0B 0C 0D 0E 0F
          ------ ----------------------------------------------- -----
0000000000000000 70 00 61 00 73 00 73 00 77 00 6F 00 72 00 64 00 p a s s w o r d
```

<span data-ttu-id="75675-149">De uitvoer van `Get-Content` in dit voor beeld is afgekapt om zich te richten op de referentie gegevens in het XML-bestand.</span><span class="sxs-lookup"><span data-stu-id="75675-149">The output of `Get-Content` in this example has been truncate to focus on the credential information in the XML file.</span></span> <span data-ttu-id="75675-150">Houd er rekening mee dat de waarde voor tekst zonder opmaak van het wacht woord wordt opgeslagen in het XML-bestand als een Unicode-teken matrix als bewezen door `Format-Hex` .</span><span class="sxs-lookup"><span data-stu-id="75675-150">Note that the plain text value of the password is stored in the XML file as a Unicode character array as proven by `Format-Hex`.</span></span> <span data-ttu-id="75675-151">Daarom is de waarde gecodeerd, maar niet versleuteld.</span><span class="sxs-lookup"><span data-stu-id="75675-151">So the value is encoded but not encrypted.</span></span>

## <span data-ttu-id="75675-152">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="75675-152">PARAMETERS</span></span>

### <span data-ttu-id="75675-153">-Confirm</span><span class="sxs-lookup"><span data-stu-id="75675-153">-Confirm</span></span>

<span data-ttu-id="75675-154">Hiermee wordt u gevraagd om bevestiging voordat u de cmdlet uitvoert.</span><span class="sxs-lookup"><span data-stu-id="75675-154">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="75675-155">-Diepte</span><span class="sxs-lookup"><span data-stu-id="75675-155">-Depth</span></span>

<span data-ttu-id="75675-156">Hiermee geeft u op hoeveel niveaus van Inge sloten objecten worden opgenomen in de XML-weer gave.</span><span class="sxs-lookup"><span data-stu-id="75675-156">Specifies how many levels of contained objects are included in the XML representation.</span></span> <span data-ttu-id="75675-157">De standaardwaarde is `2`.</span><span class="sxs-lookup"><span data-stu-id="75675-157">The default value is `2`.</span></span>

<span data-ttu-id="75675-158">De standaard waarde kan worden overschreven voor het object type in de `Types.ps1xml` bestanden.</span><span class="sxs-lookup"><span data-stu-id="75675-158">The default value can be overridden for the object type in the `Types.ps1xml` files.</span></span> <span data-ttu-id="75675-159">Zie [about_Types.ps1XML](../Microsoft.PowerShell.Core/About/about_Types.ps1xml.md)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="75675-159">For more information, see [about_Types.ps1xml](../Microsoft.PowerShell.Core/About/about_Types.ps1xml.md).</span></span>

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

### <span data-ttu-id="75675-160">-Encoding</span><span class="sxs-lookup"><span data-stu-id="75675-160">-Encoding</span></span>

<span data-ttu-id="75675-161">Hiermee geeft u het type code ring voor het doel bestand op.</span><span class="sxs-lookup"><span data-stu-id="75675-161">Specifies the type of encoding for the target file.</span></span> <span data-ttu-id="75675-162">De standaard waarde is **UTF8NoBOM**.</span><span class="sxs-lookup"><span data-stu-id="75675-162">The default value is **UTF8NoBOM**.</span></span>

<span data-ttu-id="75675-163">De acceptabele waarden voor deze para meter zijn als volgt:</span><span class="sxs-lookup"><span data-stu-id="75675-163">The acceptable values for this parameter are as follows:</span></span>

- <span data-ttu-id="75675-164">**ASCII** : gebruikt de code ring voor de ASCII-tekenset (7-bits).</span><span class="sxs-lookup"><span data-stu-id="75675-164">**ASCII** : Uses the encoding for the ASCII (7-bit) character set.</span></span>
- <span data-ttu-id="75675-165">**BigEndianUnicode** : codeert in UTF-16-indeling met behulp van de byte volgorde big endian.</span><span class="sxs-lookup"><span data-stu-id="75675-165">**BigEndianUnicode** : Encodes in UTF-16 format using the big-endian byte order.</span></span>
- <span data-ttu-id="75675-166">**OEM** : gebruikt de standaard codering voor MS-DOS-en console-Program ma's.</span><span class="sxs-lookup"><span data-stu-id="75675-166">**OEM** : Uses the default encoding for MS-DOS and console programs.</span></span>
- <span data-ttu-id="75675-167">**Unicode** : wordt gecodeerd in UTF-16-indeling met behulp van de byte volgorde little endian.</span><span class="sxs-lookup"><span data-stu-id="75675-167">**Unicode** : Encodes in UTF-16 format using the little-endian byte order.</span></span>
- <span data-ttu-id="75675-168">**UTF7** : wordt gecodeerd in de indeling UTF-7.</span><span class="sxs-lookup"><span data-stu-id="75675-168">**UTF7** : Encodes in UTF-7 format.</span></span>
- <span data-ttu-id="75675-169">**Utf8** : gecodeerd in UTF-8-indeling.</span><span class="sxs-lookup"><span data-stu-id="75675-169">**UTF8** : Encodes in UTF-8 format.</span></span>
- <span data-ttu-id="75675-170">**UTF8BOM** : coderen in UTF-8-indeling met byte order Mark (bom)</span><span class="sxs-lookup"><span data-stu-id="75675-170">**UTF8BOM** : Encodes in UTF-8 format with Byte Order Mark (BOM)</span></span>
- <span data-ttu-id="75675-171">**UTF8NoBOM** : code ring in UTF-8-indeling zonder byte order Mark (bom)</span><span class="sxs-lookup"><span data-stu-id="75675-171">**UTF8NoBOM** : Encodes in UTF-8 format without Byte Order Mark (BOM)</span></span>
- <span data-ttu-id="75675-172">**UTF32** : code ring in UTF-32-indeling.</span><span class="sxs-lookup"><span data-stu-id="75675-172">**UTF32** : Encodes in UTF-32 format.</span></span>

<span data-ttu-id="75675-173">Vanaf Power shell 6,2 kunnen met de para meter **Encoding** ook numerieke id's van geregistreerde code pagina's (zoals `-Encoding 1251` ) of teken reeks namen van geregistreerde code pagina's (zoals) worden toegestaan `-Encoding "windows-1251"` .</span><span class="sxs-lookup"><span data-stu-id="75675-173">Beginning with PowerShell 6.2, the **Encoding** parameter also allows numeric IDs of registered code pages (like `-Encoding 1251`) or string names of registered code pages (like `-Encoding "windows-1251"`).</span></span> <span data-ttu-id="75675-174">Zie de .NET-documentatie voor [code ring. code tabel](/dotnet/api/system.text.encoding.codepage?view=netcore-2.2)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="75675-174">For more information, see the .NET documentation for [Encoding.CodePage](/dotnet/api/system.text.encoding.codepage?view=netcore-2.2).</span></span>

```yaml
Type: System.Text.Encoding
Parameter Sets: (All)
Aliases:
Accepted values: ASCII, BigEndianUnicode, OEM, Unicode, UTF7, UTF8, UTF8BOM, UTF8NoBOM, UTF32

Required: False
Position: Named
Default value: UTF8NoBOM
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="75675-175">-Force</span><span class="sxs-lookup"><span data-stu-id="75675-175">-Force</span></span>

<span data-ttu-id="75675-176">Hiermee wordt de opdracht uitgevoerd zonder dat de gebruiker om bevestiging wordt gevraagd.</span><span class="sxs-lookup"><span data-stu-id="75675-176">Forces the command to run without asking for user confirmation.</span></span>

<span data-ttu-id="75675-177">Hiermee wordt de cmdlet zo nodig gewist van het alleen-lezen kenmerk van het uitvoer bestand.</span><span class="sxs-lookup"><span data-stu-id="75675-177">Causes the cmdlet to clear the read-only attribute of the output file if necessary.</span></span> <span data-ttu-id="75675-178">De cmdlet probeert het kenmerk alleen-lezen opnieuw in te stellen wanneer de opdracht is voltooid.</span><span class="sxs-lookup"><span data-stu-id="75675-178">The cmdlet will attempt to reset the read-only attribute when the command completes.</span></span>

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

### <span data-ttu-id="75675-179">-Input object</span><span class="sxs-lookup"><span data-stu-id="75675-179">-InputObject</span></span>

<span data-ttu-id="75675-180">Geeft het object aan dat moet worden geconverteerd.</span><span class="sxs-lookup"><span data-stu-id="75675-180">Specifies the object to be converted.</span></span> <span data-ttu-id="75675-181">Voer een variabele in die de objecten bevat, of typ een opdracht of expressie waarmee de objecten worden opgehaald.</span><span class="sxs-lookup"><span data-stu-id="75675-181">Enter a variable that contains the objects, or type a command or expression that gets the objects.</span></span> <span data-ttu-id="75675-182">U kunt ook objecten pipeen naar `Export-Clixml` .</span><span class="sxs-lookup"><span data-stu-id="75675-182">You can also pipe objects to `Export-Clixml`.</span></span>

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

### <span data-ttu-id="75675-183">-LiteralPath</span><span class="sxs-lookup"><span data-stu-id="75675-183">-LiteralPath</span></span>

<span data-ttu-id="75675-184">Hiermee geeft u het pad op naar het bestand waarin de XML-weer gave van het object wordt opgeslagen.</span><span class="sxs-lookup"><span data-stu-id="75675-184">Specifies the path to the file where the XML representation of the object will be stored.</span></span> <span data-ttu-id="75675-185">In tegens telling tot **Path** wordt de waarde van de para meter **LiteralPath** exact gebruikt zoals deze wordt getypt.</span><span class="sxs-lookup"><span data-stu-id="75675-185">Unlike **Path** , the value of the **LiteralPath** parameter is used exactly as it's typed.</span></span> <span data-ttu-id="75675-186">Geen tekens worden geïnterpreteerd als joker tekens.</span><span class="sxs-lookup"><span data-stu-id="75675-186">No characters are interpreted as wildcards.</span></span> <span data-ttu-id="75675-187">Als het pad escape tekens bevat, plaatst u het tussen enkele aanhalings tekens.</span><span class="sxs-lookup"><span data-stu-id="75675-187">If the path includes escape characters, enclose it in single quotation marks.</span></span> <span data-ttu-id="75675-188">Enkele aanhalings tekens geven aan dat Power shell geen karakters interpreteert als escape reeksen.</span><span class="sxs-lookup"><span data-stu-id="75675-188">Single quotation marks tell PowerShell not to interpret any characters as escape sequences.</span></span>

```yaml
Type: System.String
Parameter Sets: ByLiteralPath
Aliases: PSPath, LP

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="75675-189">-NoClobber</span><span class="sxs-lookup"><span data-stu-id="75675-189">-NoClobber</span></span>

<span data-ttu-id="75675-190">Geeft aan dat de cmdlet de inhoud van een bestaand bestand niet overschrijft.</span><span class="sxs-lookup"><span data-stu-id="75675-190">Indicates that the cmdlet doesn't overwrite the contents of an existing file.</span></span> <span data-ttu-id="75675-191">Als een bestand bestaat in het opgegeven pad, wordt standaard `Export-Clixml` het bestand overschreven zonder dat er een waarschuwing wordt gegeven.</span><span class="sxs-lookup"><span data-stu-id="75675-191">By default, if a file exists in the specified path, `Export-Clixml` overwrites the file without warning.</span></span>

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

### <span data-ttu-id="75675-192">-Path</span><span class="sxs-lookup"><span data-stu-id="75675-192">-Path</span></span>

<span data-ttu-id="75675-193">Hiermee geeft u het pad op naar het bestand waarin de XML-weer gave van het object wordt opgeslagen.</span><span class="sxs-lookup"><span data-stu-id="75675-193">Specifies the path to the file where the XML representation of the object will be stored.</span></span>

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

### <span data-ttu-id="75675-194">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="75675-194">-WhatIf</span></span>

<span data-ttu-id="75675-195">Hiermee wordt weergegeven wat er zou gebeuren als u de cmdlet uitvoert.</span><span class="sxs-lookup"><span data-stu-id="75675-195">Shows what would happen if the cmdlet runs.</span></span> <span data-ttu-id="75675-196">De cmdlet wordt niet uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="75675-196">The cmdlet isn't run.</span></span>

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

### <span data-ttu-id="75675-197">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="75675-197">CommonParameters</span></span>

<span data-ttu-id="75675-198">Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="75675-198">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="75675-199">Zie [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="75675-199">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="75675-200">INVOER</span><span class="sxs-lookup"><span data-stu-id="75675-200">INPUTS</span></span>

### <span data-ttu-id="75675-201">System. Management. Automation. PSObject</span><span class="sxs-lookup"><span data-stu-id="75675-201">System.Management.Automation.PSObject</span></span>

<span data-ttu-id="75675-202">U kunt elk object pijp lijnen naar `Export-Clixml` .</span><span class="sxs-lookup"><span data-stu-id="75675-202">You can pipeline any object to `Export-Clixml`.</span></span>

## <span data-ttu-id="75675-203">UITVOER</span><span class="sxs-lookup"><span data-stu-id="75675-203">OUTPUTS</span></span>

### <span data-ttu-id="75675-204">System. IO. file info</span><span class="sxs-lookup"><span data-stu-id="75675-204">System.IO.FileInfo</span></span>

<span data-ttu-id="75675-205">`Export-Clixml` Hiermee maakt u een bestand dat de XML bevat.</span><span class="sxs-lookup"><span data-stu-id="75675-205">`Export-Clixml` creates a file that contains the XML.</span></span>

## <span data-ttu-id="75675-206">OPMERKINGEN</span><span class="sxs-lookup"><span data-stu-id="75675-206">NOTES</span></span>

## <span data-ttu-id="75675-207">GERELATEERDE KOPPELINGEN</span><span class="sxs-lookup"><span data-stu-id="75675-207">RELATED LINKS</span></span>

[<span data-ttu-id="75675-208">ConvertTo-Html</span><span class="sxs-lookup"><span data-stu-id="75675-208">ConvertTo-Html</span></span>](ConvertTo-Html.md)

[<span data-ttu-id="75675-209">ConvertTo-Xml</span><span class="sxs-lookup"><span data-stu-id="75675-209">ConvertTo-Xml</span></span>](ConvertTo-Xml.md)

[<span data-ttu-id="75675-210">Exporteren-CSV</span><span class="sxs-lookup"><span data-stu-id="75675-210">Export-Csv</span></span>](Export-Csv.md)

[<span data-ttu-id="75675-211">Import-Clixml</span><span class="sxs-lookup"><span data-stu-id="75675-211">Import-Clixml</span></span>](Import-Clixml.md)

[<span data-ttu-id="75675-212">Pad voor samen voegen</span><span class="sxs-lookup"><span data-stu-id="75675-212">Join-Path</span></span>](../Microsoft.PowerShell.Management/Join-Path.md)

[<span data-ttu-id="75675-213">Referenties veilig opslaan op schijf</span><span class="sxs-lookup"><span data-stu-id="75675-213">Securely Store Credentials on Disk</span></span>](https://powershellcookbook.com/recipe/PukO/securely-store-credentials-on-disk)

[<span data-ttu-id="75675-214">Power shell gebruiken om referenties door te geven aan verouderde systemen</span><span class="sxs-lookup"><span data-stu-id="75675-214">Use PowerShell to Pass Credentials to Legacy Systems</span></span>](https://devblogs.microsoft.com/scripting/use-powershell-to-pass-credentials-to-legacy-systems/)

[<span data-ttu-id="75675-215">Windows. Security. Cryptography. DataProtection</span><span class="sxs-lookup"><span data-stu-id="75675-215">Windows.Security.Cryptography.DataProtection</span></span>](/uwp/api/windows.security.cryptography.dataprotection)
