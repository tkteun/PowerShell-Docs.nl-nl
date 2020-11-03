---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 5/14/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/set-content?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Set-Content
ms.openlocfilehash: 897029cab790487f6834d021bfc447060fd39812
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/07/2020
ms.locfileid: "93250561"
---
# <span data-ttu-id="acda9-103">Set-Content</span><span class="sxs-lookup"><span data-stu-id="acda9-103">Set-Content</span></span>

## <span data-ttu-id="acda9-104">SAMENVATTING</span><span class="sxs-lookup"><span data-stu-id="acda9-104">SYNOPSIS</span></span>
<span data-ttu-id="acda9-105">Schrijft nieuwe inhoud of vervangt bestaande inhoud in een bestand.</span><span class="sxs-lookup"><span data-stu-id="acda9-105">Writes new content or replaces existing content in a file.</span></span>

## <span data-ttu-id="acda9-106">SYNTAXIS</span><span class="sxs-lookup"><span data-stu-id="acda9-106">SYNTAX</span></span>

### <span data-ttu-id="acda9-107">Pad (standaard)</span><span class="sxs-lookup"><span data-stu-id="acda9-107">Path (Default)</span></span>

```
Set-Content [-Path] <string[]> [-Value] <Object[]> [-PassThru] [-Filter <string>]
 [-Include <string[]>] [-Exclude <string[]>] [-Force] [-Credential <pscredential>] [-WhatIf]
 [-Confirm] [-UseTransaction] [-NoNewline] [-Encoding <FileSystemCmdletProviderEncoding>]
 [-Stream <string>] [<CommonParameters>]
```

### <span data-ttu-id="acda9-108">LiteralPath</span><span class="sxs-lookup"><span data-stu-id="acda9-108">LiteralPath</span></span>

```
Set-Content [-Value] <Object[]> -LiteralPath <string[]> [-PassThru] [-Filter <string>]
 [-Include <string[]>] [-Exclude <string[]>] [-Force] [-Credential <pscredential>] [-WhatIf]
 [-Confirm] [-UseTransaction] [-NoNewline] [-Encoding <FileSystemCmdletProviderEncoding>]
 [-Stream <string>] [<CommonParameters>]
```

## <span data-ttu-id="acda9-109">BESCHRIJVING</span><span class="sxs-lookup"><span data-stu-id="acda9-109">DESCRIPTION</span></span>

<span data-ttu-id="acda9-110">`Set-Content` is een cmdlet voor het verwerken van teken reeksen waarmee nieuwe inhoud wordt geschreven of de inhoud in een bestand wordt vervangen.</span><span class="sxs-lookup"><span data-stu-id="acda9-110">`Set-Content` is a string-processing cmdlet that writes new content or replaces the content in a file.</span></span> <span data-ttu-id="acda9-111">`Set-Content` vervangt de bestaande inhoud en wijkt af van de `Add-Content` cmdlet waarmee inhoud wordt toegevoegd aan een bestand.</span><span class="sxs-lookup"><span data-stu-id="acda9-111">`Set-Content` replaces the existing content and differs from the `Add-Content` cmdlet that appends content to a file.</span></span> <span data-ttu-id="acda9-112">Als u inhoud wilt verzenden naar, `Set-Content` kunt u de para meter **Value** gebruiken op de opdracht regel of inhoud verzenden via de pijp lijn.</span><span class="sxs-lookup"><span data-stu-id="acda9-112">To send content to `Set-Content` you can use the **Value** parameter on the command line or send content through the pipeline.</span></span>

<span data-ttu-id="acda9-113">Zie [Nieuw-item](New-Item.md)als u bestanden of mappen wilt maken voor de volgende voor beelden.</span><span class="sxs-lookup"><span data-stu-id="acda9-113">If you need to create files or directories for the following examples, see [New-Item](New-Item.md).</span></span>

## <span data-ttu-id="acda9-114">VOORBEELDEN</span><span class="sxs-lookup"><span data-stu-id="acda9-114">EXAMPLES</span></span>

### <span data-ttu-id="acda9-115">Voor beeld 1: de inhoud van meerdere bestanden in een map vervangen</span><span class="sxs-lookup"><span data-stu-id="acda9-115">Example 1: Replace the contents of multiple files in a directory</span></span>

<span data-ttu-id="acda9-116">In dit voor beeld wordt de inhoud voor meerdere bestanden in de huidige map vervangen.</span><span class="sxs-lookup"><span data-stu-id="acda9-116">This example replaces the content for multiple files in the current directory.</span></span>

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

<span data-ttu-id="acda9-117">De `Get-ChildItem` cmdlet gebruikt de para meter **Path** om de **txt** -bestanden weer te geven die beginnen met `Test*` in de huidige map.</span><span class="sxs-lookup"><span data-stu-id="acda9-117">The `Get-ChildItem` cmdlet uses the **Path** parameter to list **.txt** files that begin with `Test*` in the current directory.</span></span> <span data-ttu-id="acda9-118">De `Set-Content` cmdlet gebruikt de para meter **Path** om de bestanden op te geven `Test*.txt` .</span><span class="sxs-lookup"><span data-stu-id="acda9-118">The `Set-Content` cmdlet uses the **Path** parameter to specify the `Test*.txt` files.</span></span> <span data-ttu-id="acda9-119">De **waarde** para meter geeft de teken reeks **Hello, World** waarmee de bestaande inhoud in elk bestand wordt vervangen.</span><span class="sxs-lookup"><span data-stu-id="acda9-119">The **Value** parameter provides the text string **Hello, World** that replaces the existing content in each file.</span></span> <span data-ttu-id="acda9-120">Met de `Get-Content` cmdlet wordt de para meter **Path** gebruikt om de bestanden op te geven `Test*.txt` en wordt de inhoud van elk bestand in de Power shell-console weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="acda9-120">The `Get-Content` cmdlet uses the **Path** parameter to specify the `Test*.txt` files and displays each file's content in the PowerShell console.</span></span>

### <span data-ttu-id="acda9-121">Voor beeld 2: een nieuw bestand maken en inhoud schrijven</span><span class="sxs-lookup"><span data-stu-id="acda9-121">Example 2: Create a new file and write content</span></span>

<span data-ttu-id="acda9-122">In dit voor beeld wordt een nieuw bestand gemaakt en worden de huidige datum en tijd naar het bestand geschreven.</span><span class="sxs-lookup"><span data-stu-id="acda9-122">This example creates a new file and writes the current date and time to the file.</span></span>

```powershell
Set-Content -Path .\DateTime.txt -Value (Get-Date)
Get-Content -Path .\DateTime.txt
```

```Output
1/30/2019 09:55:08
```

<span data-ttu-id="acda9-123">`Set-Content` maakt gebruik van de para meters **pad** en **waarde** voor het maken van een nieuw bestand met de naam **DateTime.txt** in de huidige map.</span><span class="sxs-lookup"><span data-stu-id="acda9-123">`Set-Content` uses the **Path** and **Value** parameters to create a new file named **DateTime.txt** in the current directory.</span></span> <span data-ttu-id="acda9-124">De **waarde** para meter wordt gebruikt `Get-Date` om de huidige datum en tijd op te halen.</span><span class="sxs-lookup"><span data-stu-id="acda9-124">The **Value** parameter uses `Get-Date` to get the current date and time.</span></span>
<span data-ttu-id="acda9-125">`Set-Content` schrijft het **DateTime** -object naar het bestand als een teken reeks.</span><span class="sxs-lookup"><span data-stu-id="acda9-125">`Set-Content` writes the **DateTime** object to the file as a string.</span></span> <span data-ttu-id="acda9-126">De `Get-Content` cmdlet gebruikt de para meter **Path** om de inhoud van **DateTime.txt** in de Power shell-console weer te geven.</span><span class="sxs-lookup"><span data-stu-id="acda9-126">The `Get-Content` cmdlet uses the **Path** parameter to display the content of **DateTime.txt** in the PowerShell console.</span></span>

### <span data-ttu-id="acda9-127">Voor beeld 3: tekst in een bestand vervangen</span><span class="sxs-lookup"><span data-stu-id="acda9-127">Example 3: Replace text in a file</span></span>

<span data-ttu-id="acda9-128">Met deze opdracht worden alle exemplaren van Word in een bestaand bestand vervangen.</span><span class="sxs-lookup"><span data-stu-id="acda9-128">This command replaces all instances of word within an existing file.</span></span>

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

<span data-ttu-id="acda9-129">De `Get-Content` cmdlet gebruikt de para meter **Path** om het **Notice.txt** bestand in de huidige map op te geven.</span><span class="sxs-lookup"><span data-stu-id="acda9-129">The `Get-Content` cmdlet uses the **Path** parameter to specify the **Notice.txt** file in the current directory.</span></span> <span data-ttu-id="acda9-130">De `Get-Content` opdracht wordt verpakt met haakjes zodat de opdracht is voltooid voordat de pijp lijn wordt verzonden.</span><span class="sxs-lookup"><span data-stu-id="acda9-130">The `Get-Content` command is wrapped with parentheses so that the command finishes before being sent down the pipeline.</span></span>

<span data-ttu-id="acda9-131">De inhoud van het **Notice.txt** -bestand wordt naar de-cmdlet verzonden via de pijp lijn `ForEach-Object` .</span><span class="sxs-lookup"><span data-stu-id="acda9-131">The contents of the **Notice.txt** file are sent down the pipeline to the `ForEach-Object` cmdlet.</span></span>
<span data-ttu-id="acda9-132">`ForEach-Object`maakt gebruik van de automatische variabele `$_` en vervangt elke **waarschuwing** telkens **Caution** als dat zo is.</span><span class="sxs-lookup"><span data-stu-id="acda9-132">`ForEach-Object` uses the automatic variable `$_` and replaces each occurrence of **Warning** with **Caution**.</span></span> <span data-ttu-id="acda9-133">De objecten worden naar de-cmdlet verzonden via de pijp lijn `Set-Content` .</span><span class="sxs-lookup"><span data-stu-id="acda9-133">The objects are sent down the pipeline to the `Set-Content` cmdlet.</span></span> <span data-ttu-id="acda9-134">`Set-Content` gebruikt de para meter **Path** om het **Notice.txt** -bestand op te geven en de bijgewerkte inhoud naar het bestand te schrijven.</span><span class="sxs-lookup"><span data-stu-id="acda9-134">`Set-Content` uses the **Path** parameter to specify the **Notice.txt** file and writes the updated content to the file.</span></span>

<span data-ttu-id="acda9-135">Met de laatste `Get-Content` cmdlet wordt de bijgewerkte bestands inhoud weer gegeven in de Power shell-console.</span><span class="sxs-lookup"><span data-stu-id="acda9-135">The last `Get-Content` cmdlet displays the updated file content in the PowerShell console.</span></span>

### <span data-ttu-id="acda9-136">Voor beeld 4: filters gebruiken met Set-Content</span><span class="sxs-lookup"><span data-stu-id="acda9-136">Example 4: Use Filters with Set-Content</span></span>

<span data-ttu-id="acda9-137">U kunt een filter opgeven voor de `Set-Content` cmdlet.</span><span class="sxs-lookup"><span data-stu-id="acda9-137">You can specify a filter to the `Set-Content` cmdlet.</span></span> <span data-ttu-id="acda9-138">Wanneer u filters gebruikt om de para meter **Path** te kwalificeren, moet u een asterisk ( `*` ) toevoegen om de inhoud van het pad aan te geven.</span><span class="sxs-lookup"><span data-stu-id="acda9-138">When using filters to qualify the **Path** parameter, you need to include a trailing asterisk (`*`) to indicate the contents of the path.</span></span>

<span data-ttu-id="acda9-139">Met de volgende opdracht stelt u de inhoud alle `*.txt` bestanden in de `C:\Temp` map in op de **waarde** empty.</span><span class="sxs-lookup"><span data-stu-id="acda9-139">The following command set the content all `*.txt` files in the `C:\Temp` directory to the **Value** empty.</span></span>

```powershell
Set-Content -Path C:\Temp\* -Filter *.txt -Value "Empty"
```

## <span data-ttu-id="acda9-140">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="acda9-140">PARAMETERS</span></span>

### <span data-ttu-id="acda9-141">-Credential</span><span class="sxs-lookup"><span data-stu-id="acda9-141">-Credential</span></span>

> [!NOTE]
> <span data-ttu-id="acda9-142">Deze para meter wordt niet ondersteund door providers die zijn geïnstalleerd met Power shell.</span><span class="sxs-lookup"><span data-stu-id="acda9-142">This parameter is not supported by any providers installed with PowerShell.</span></span>
> <span data-ttu-id="acda9-143">Gebruik [invoke-Command](../Microsoft.PowerShell.Core/Invoke-Command.md)om een andere gebruiker te imiteren of uw referenties te verhogen wanneer u deze cmdlet uitvoert.</span><span class="sxs-lookup"><span data-stu-id="acda9-143">To impersonate another user, or elevate your credentials when running this cmdlet, use [Invoke-Command](../Microsoft.PowerShell.Core/Invoke-Command.md).</span></span>

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

### <span data-ttu-id="acda9-144">-Encoding</span><span class="sxs-lookup"><span data-stu-id="acda9-144">-Encoding</span></span>

<span data-ttu-id="acda9-145">Hiermee geeft u het type code ring voor het doel bestand op.</span><span class="sxs-lookup"><span data-stu-id="acda9-145">Specifies the type of encoding for the target file.</span></span> <span data-ttu-id="acda9-146">De standaardwaarde is `Default`.</span><span class="sxs-lookup"><span data-stu-id="acda9-146">The default value is `Default`.</span></span>

<span data-ttu-id="acda9-147">Encoding is een dynamische para meter waaraan de File System Provider toevoegt `Set-Content` .</span><span class="sxs-lookup"><span data-stu-id="acda9-147">Encoding is a dynamic parameter that the FileSystem provider adds to `Set-Content`.</span></span> <span data-ttu-id="acda9-148">Deze para meter werkt alleen op stations met een bestands systeem.</span><span class="sxs-lookup"><span data-stu-id="acda9-148">This parameter works only in file system drives.</span></span>

<span data-ttu-id="acda9-149">De acceptabele waarden voor deze para meter zijn als volgt:</span><span class="sxs-lookup"><span data-stu-id="acda9-149">The acceptable values for this parameter are as follows:</span></span>

- <span data-ttu-id="acda9-150">`Ascii` Maakt gebruik van ASCII-tekenset (7-bits).</span><span class="sxs-lookup"><span data-stu-id="acda9-150">`Ascii` Uses ASCII (7-bit) character set.</span></span>
- <span data-ttu-id="acda9-151">`BigEndianUnicode` Maakt gebruik van UTF-16 met de byte volgorde big endian.</span><span class="sxs-lookup"><span data-stu-id="acda9-151">`BigEndianUnicode` Uses UTF-16 with the big-endian byte order.</span></span>
- <span data-ttu-id="acda9-152">`BigEndianUTF32` Maakt gebruik van UTF-32 met de byte volgorde big endian.</span><span class="sxs-lookup"><span data-stu-id="acda9-152">`BigEndianUTF32` Uses UTF-32 with the big-endian byte order.</span></span>
- <span data-ttu-id="acda9-153">`Byte` Codeert een reeks tekens in een reeks bytes.</span><span class="sxs-lookup"><span data-stu-id="acda9-153">`Byte` Encodes a set of characters into a sequence of bytes.</span></span>
- <span data-ttu-id="acda9-154">`Default` Gebruikt de code ring die overeenkomt met de actieve code tabel van het systeem (meestal ANSI).</span><span class="sxs-lookup"><span data-stu-id="acda9-154">`Default` Uses the encoding that corresponds to the system's active code page (usually ANSI).</span></span>
- <span data-ttu-id="acda9-155">`Oem` Gebruikt de code ring die overeenkomt met de huidige OEM-code tabel van het systeem.</span><span class="sxs-lookup"><span data-stu-id="acda9-155">`Oem` Uses the encoding that corresponds to the system's current OEM code page.</span></span>
- <span data-ttu-id="acda9-156">`String` Hetzelfde als `Unicode` .</span><span class="sxs-lookup"><span data-stu-id="acda9-156">`String` Same as `Unicode`.</span></span>
- <span data-ttu-id="acda9-157">`Unicode` Maakt gebruik van UTF-16 met de byte volgorde little endian.</span><span class="sxs-lookup"><span data-stu-id="acda9-157">`Unicode` Uses UTF-16 with the little-endian byte order.</span></span>
- <span data-ttu-id="acda9-158">`Unknown` Hetzelfde als `Unicode` .</span><span class="sxs-lookup"><span data-stu-id="acda9-158">`Unknown` Same as `Unicode`.</span></span>
- <span data-ttu-id="acda9-159">`UTF7` Maakt gebruik van UTF-7.</span><span class="sxs-lookup"><span data-stu-id="acda9-159">`UTF7` Uses UTF-7.</span></span>
- <span data-ttu-id="acda9-160">`UTF8` Maakt gebruik van UTF-8.</span><span class="sxs-lookup"><span data-stu-id="acda9-160">`UTF8` Uses UTF-8.</span></span>
- <span data-ttu-id="acda9-161">`UTF32` Maakt gebruik van UTF-32 met de byte volgorde little endian.</span><span class="sxs-lookup"><span data-stu-id="acda9-161">`UTF32` Uses UTF-32 with the little-endian byte order.</span></span>

<span data-ttu-id="acda9-162">Encoding is een dynamische para meter waaraan de File System Provider toevoegt `Set-Content` .</span><span class="sxs-lookup"><span data-stu-id="acda9-162">Encoding is a dynamic parameter that the FileSystem provider adds to `Set-Content`.</span></span> <span data-ttu-id="acda9-163">Deze para meter werkt alleen op stations met een bestands systeem.</span><span class="sxs-lookup"><span data-stu-id="acda9-163">This parameter works only in file system drives.</span></span>

```yaml
Type: Microsoft.PowerShell.Commands.FileSystemCmdletProviderEncoding
Parameter Sets: (All)
Aliases:
Accepted values: ASCII, BigEndianUnicode, BigEndianUTF32, Byte, Default, OEM, String, Unicode, Unknown, UTF7, UTF8, UTF32

Required: False
Position: Named
Default value: Default
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="acda9-164">-Uitsluiten</span><span class="sxs-lookup"><span data-stu-id="acda9-164">-Exclude</span></span>

<span data-ttu-id="acda9-165">Hiermee geeft u als een teken reeks matrix een item of items die met deze cmdlet worden uitgesloten in de bewerking.</span><span class="sxs-lookup"><span data-stu-id="acda9-165">Specifies, as a string array, an item or items that this cmdlet excludes in the operation.</span></span> <span data-ttu-id="acda9-166">De waarde van deze para meter komt in aanmerking voor de para meter **Path** .</span><span class="sxs-lookup"><span data-stu-id="acda9-166">The value of this parameter qualifies the **Path** parameter.</span></span> <span data-ttu-id="acda9-167">Voer een element of patroon van een pad in, zoals `*.txt` .</span><span class="sxs-lookup"><span data-stu-id="acda9-167">Enter a path element or pattern, such as `*.txt`.</span></span> <span data-ttu-id="acda9-168">Joker tekens zijn toegestaan.</span><span class="sxs-lookup"><span data-stu-id="acda9-168">Wildcard characters are permitted.</span></span> <span data-ttu-id="acda9-169">De **exclude** -para meter is alleen effectief wanneer de inhoud van een item wordt opgenomen, zoals `C:\Windows\*` , waarbij het Joker teken de inhoud van de `C:\Windows` map bevat.</span><span class="sxs-lookup"><span data-stu-id="acda9-169">The **Exclude** parameter is effective only when the command includes the contents of an item, such as `C:\Windows\*`, where the wildcard character specifies the contents of the `C:\Windows` directory.</span></span>

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

### <span data-ttu-id="acda9-170">-Filter</span><span class="sxs-lookup"><span data-stu-id="acda9-170">-Filter</span></span>

<span data-ttu-id="acda9-171">Hiermee geeft u een filter op om de para meter **Path** te kwalificeren.</span><span class="sxs-lookup"><span data-stu-id="acda9-171">Specifies a filter to qualify the **Path** parameter.</span></span> <span data-ttu-id="acda9-172">De [File System](../Microsoft.PowerShell.Core/About/about_FileSystem_Provider.md) -provider is de enige geïnstalleerde Power shell-provider die het gebruik van filters ondersteunt.</span><span class="sxs-lookup"><span data-stu-id="acda9-172">The [FileSystem](../Microsoft.PowerShell.Core/About/about_FileSystem_Provider.md) provider is the only installed PowerShell provider that supports the use of filters.</span></span> <span data-ttu-id="acda9-173">U kunt de syntaxis voor de filter taal van het **Bestands systeem** in [about_Wildcards](../Microsoft.PowerShell.Core/About/about_Wildcards.md)vinden.</span><span class="sxs-lookup"><span data-stu-id="acda9-173">You can find the syntax for the **FileSystem** filter language in [about_Wildcards](../Microsoft.PowerShell.Core/About/about_Wildcards.md).</span></span>
<span data-ttu-id="acda9-174">Filters zijn efficiënter dan andere para meters, omdat deze door de provider worden toegepast wanneer de cmdlet de objecten ophaalt in plaats van dat Power shell de objecten heeft gefilterd nadat ze zijn opgehaald.</span><span class="sxs-lookup"><span data-stu-id="acda9-174">Filters are more efficient than other parameters, because the provider applies them when the cmdlet gets the objects rather than having PowerShell filter the objects after they are retrieved.</span></span>

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

### <span data-ttu-id="acda9-175">-Force</span><span class="sxs-lookup"><span data-stu-id="acda9-175">-Force</span></span>

<span data-ttu-id="acda9-176">Hiermee wordt de cmdlet gedwongen de inhoud van een bestand in te stellen, zelfs als het bestand alleen-lezen is.</span><span class="sxs-lookup"><span data-stu-id="acda9-176">Forces the cmdlet to set the contents of a file, even if the file is read-only.</span></span> <span data-ttu-id="acda9-177">De implementatie varieert van provider tot provider.</span><span class="sxs-lookup"><span data-stu-id="acda9-177">Implementation varies from provider to provider.</span></span> <span data-ttu-id="acda9-178">Zie [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="acda9-178">For more information, see [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md).</span></span>
<span data-ttu-id="acda9-179">De para meter **Force** overschrijft geen beveiligings beperkingen.</span><span class="sxs-lookup"><span data-stu-id="acda9-179">The **Force** parameter does not override security restrictions.</span></span>

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

### <span data-ttu-id="acda9-180">-Include</span><span class="sxs-lookup"><span data-stu-id="acda9-180">-Include</span></span>

<span data-ttu-id="acda9-181">Hiermee wordt een teken reeks matrix opgegeven, een item of items die met deze cmdlet in de bewerking zijn opgenomen.</span><span class="sxs-lookup"><span data-stu-id="acda9-181">Specifies, as a string array, an item or items that this cmdlet includes in the operation.</span></span> <span data-ttu-id="acda9-182">De waarde van deze para meter komt in aanmerking voor de para meter **Path** .</span><span class="sxs-lookup"><span data-stu-id="acda9-182">The value of this parameter qualifies the **Path** parameter.</span></span> <span data-ttu-id="acda9-183">Voer een element of patroon van een pad in, zoals `"*.txt"` .</span><span class="sxs-lookup"><span data-stu-id="acda9-183">Enter a path element or pattern, such as `"*.txt"`.</span></span> <span data-ttu-id="acda9-184">Joker tekens zijn toegestaan.</span><span class="sxs-lookup"><span data-stu-id="acda9-184">Wildcard characters are permitted.</span></span> <span data-ttu-id="acda9-185">De para meter **include** is alleen effectief wanneer de inhoud van een item wordt opgenomen, zoals `C:\Windows\*` , waarbij het Joker teken de inhoud van de `C:\Windows` map bevat.</span><span class="sxs-lookup"><span data-stu-id="acda9-185">The **Include** parameter is effective only when the command includes the contents of an item, such as `C:\Windows\*`, where the wildcard character specifies the contents of the `C:\Windows` directory.</span></span>

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

### <span data-ttu-id="acda9-186">-LiteralPath</span><span class="sxs-lookup"><span data-stu-id="acda9-186">-LiteralPath</span></span>

<span data-ttu-id="acda9-187">Hiermee geeft u een pad naar een of meer locaties.</span><span class="sxs-lookup"><span data-stu-id="acda9-187">Specifies a path to one or more locations.</span></span> <span data-ttu-id="acda9-188">De waarde van **LiteralPath** wordt precies zo gebruikt als deze wordt getypt.</span><span class="sxs-lookup"><span data-stu-id="acda9-188">The value of **LiteralPath** is used exactly as it is typed.</span></span> <span data-ttu-id="acda9-189">Geen tekens worden geïnterpreteerd als joker tekens.</span><span class="sxs-lookup"><span data-stu-id="acda9-189">No characters are interpreted as wildcards.</span></span> <span data-ttu-id="acda9-190">Als het pad escape tekens bevat, plaatst u het tussen enkele aanhalings tekens.</span><span class="sxs-lookup"><span data-stu-id="acda9-190">If the path includes escape characters, enclose it in single quotation marks.</span></span> <span data-ttu-id="acda9-191">Enkele aanhalings tekens geven aan dat Power shell geen karakters interpreteert als escape reeksen.</span><span class="sxs-lookup"><span data-stu-id="acda9-191">Single quotation marks tell PowerShell not to interpret any characters as escape sequences.</span></span>

<span data-ttu-id="acda9-192">Zie [about_Quoting_Rules](../Microsoft.Powershell.Core/About/about_Quoting_Rules.md)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="acda9-192">For more information, see [about_Quoting_Rules](../Microsoft.Powershell.Core/About/about_Quoting_Rules.md).</span></span>

```yaml
Type: System.String[]
Parameter Sets: LiteralPath
Aliases: PSPath

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="acda9-193">-Nieuwe regel</span><span class="sxs-lookup"><span data-stu-id="acda9-193">-NoNewline</span></span>

<span data-ttu-id="acda9-194">De teken reeks representaties van de invoer objecten worden samengevoegd om de uitvoer te vormen.</span><span class="sxs-lookup"><span data-stu-id="acda9-194">The string representations of the input objects are concatenated to form the output.</span></span> <span data-ttu-id="acda9-195">Er worden geen spaties of nieuwe regels tussen de uitvoer teken reeksen ingevoegd.</span><span class="sxs-lookup"><span data-stu-id="acda9-195">No spaces or newlines are inserted between the output strings.</span></span> <span data-ttu-id="acda9-196">Er wordt geen nieuwe regel toegevoegd na de laatste uitvoer teken reeks.</span><span class="sxs-lookup"><span data-stu-id="acda9-196">No newline is added after the last output string.</span></span>

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

### <span data-ttu-id="acda9-197">-PassThru</span><span class="sxs-lookup"><span data-stu-id="acda9-197">-PassThru</span></span>

<span data-ttu-id="acda9-198">Retourneert een object dat de inhoud vertegenwoordigt.</span><span class="sxs-lookup"><span data-stu-id="acda9-198">Returns an object that represents the content.</span></span> <span data-ttu-id="acda9-199">Deze cmdlet genereert standaard geen uitvoer.</span><span class="sxs-lookup"><span data-stu-id="acda9-199">By default, this cmdlet does not generate any output.</span></span>

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

### <span data-ttu-id="acda9-200">-Path</span><span class="sxs-lookup"><span data-stu-id="acda9-200">-Path</span></span>

<span data-ttu-id="acda9-201">Hiermee geeft u het pad op van het item dat de inhoud ontvangt.</span><span class="sxs-lookup"><span data-stu-id="acda9-201">Specifies the path of the item that receives the content.</span></span>
<span data-ttu-id="acda9-202">Joker tekens zijn toegestaan.</span><span class="sxs-lookup"><span data-stu-id="acda9-202">Wildcard characters are permitted.</span></span>

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

### <span data-ttu-id="acda9-203">-Stream</span><span class="sxs-lookup"><span data-stu-id="acda9-203">-Stream</span></span>

<span data-ttu-id="acda9-204">Hiermee geeft u een alternatieve gegevens stroom voor inhoud.</span><span class="sxs-lookup"><span data-stu-id="acda9-204">Specifies an alternative data stream for content.</span></span> <span data-ttu-id="acda9-205">Als de stroom niet bestaat, wordt deze gemaakt met deze cmdlet.</span><span class="sxs-lookup"><span data-stu-id="acda9-205">If the stream does not exist, this cmdlet creates it.</span></span> <span data-ttu-id="acda9-206">Joker tekens worden niet ondersteund.</span><span class="sxs-lookup"><span data-stu-id="acda9-206">Wildcard characters are not supported.</span></span>

<span data-ttu-id="acda9-207">**Stream** is een dynamische para meter waaraan de **File System** provider toevoegt `Set-Content` .</span><span class="sxs-lookup"><span data-stu-id="acda9-207">**Stream** is a dynamic parameter that the **FileSystem** provider adds to `Set-Content`.</span></span> <span data-ttu-id="acda9-208">Deze para meter werkt alleen op stations met een bestands systeem.</span><span class="sxs-lookup"><span data-stu-id="acda9-208">This parameter works only in file system drives.</span></span>

<span data-ttu-id="acda9-209">U kunt de- `Set-Content` cmdlet gebruiken om de inhoud van de **zone te wijzigen. id** alternatieve gegevens stroom.</span><span class="sxs-lookup"><span data-stu-id="acda9-209">You can use the `Set-Content` cmdlet to change the content of the **Zone.Identifier** alternate data stream.</span></span> <span data-ttu-id="acda9-210">Dit wordt echter niet aangeraden als een manier om beveiligings controles te elimineren waarmee bestanden die worden gedownload van Internet, worden geblokkeerd.</span><span class="sxs-lookup"><span data-stu-id="acda9-210">However, we do not recommend this as a way to eliminate security checks that block files that are downloaded from the Internet.</span></span> <span data-ttu-id="acda9-211">Als u controleert of een gedownload bestand veilig is, gebruikt u de `Unblock-File` cmdlet.</span><span class="sxs-lookup"><span data-stu-id="acda9-211">If you verify that a downloaded file is safe, use the `Unblock-File` cmdlet.</span></span>

<span data-ttu-id="acda9-212">Deze para meter is geïntroduceerd in Power Shell 3,0.</span><span class="sxs-lookup"><span data-stu-id="acda9-212">This parameter was introduced in PowerShell 3.0.</span></span>

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

### <span data-ttu-id="acda9-213">-UseTransaction</span><span class="sxs-lookup"><span data-stu-id="acda9-213">-UseTransaction</span></span>

<span data-ttu-id="acda9-214">Hiermee wordt de opdracht opgenomen in de actieve transactie.</span><span class="sxs-lookup"><span data-stu-id="acda9-214">Includes the command in the active transaction.</span></span> <span data-ttu-id="acda9-215">Deze parameter is alleen geldig wanneer een transactie wordt uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="acda9-215">This parameter is valid only when a transaction is in progress.</span></span> <span data-ttu-id="acda9-216">Zie [about_Transactions](../Microsoft.PowerShell.Core/About/about_Transactions.md)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="acda9-216">For more information, see [about_Transactions](../Microsoft.PowerShell.Core/About/about_Transactions.md).</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: usetx

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="acda9-217">-Waarde</span><span class="sxs-lookup"><span data-stu-id="acda9-217">-Value</span></span>

<span data-ttu-id="acda9-218">Hiermee geeft u de nieuwe inhoud voor het item.</span><span class="sxs-lookup"><span data-stu-id="acda9-218">Specifies the new content for the item.</span></span>

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

### <span data-ttu-id="acda9-219">-Confirm</span><span class="sxs-lookup"><span data-stu-id="acda9-219">-Confirm</span></span>

<span data-ttu-id="acda9-220">Hiermee wordt u gevraagd om bevestiging voordat u de cmdlet uitvoert.</span><span class="sxs-lookup"><span data-stu-id="acda9-220">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="acda9-221">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="acda9-221">-WhatIf</span></span>

<span data-ttu-id="acda9-222">Hiermee wordt weergegeven wat er zou gebeuren als u de cmdlet uitvoert.</span><span class="sxs-lookup"><span data-stu-id="acda9-222">Shows what would happen if the cmdlet runs.</span></span> <span data-ttu-id="acda9-223">De cmdlet wordt niet uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="acda9-223">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="acda9-224">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="acda9-224">CommonParameters</span></span>

<span data-ttu-id="acda9-225">Deze cmdlet biedt ondersteuning voor de algemene para meters: `-Debug` , `-ErrorAction` , `-ErrorVariable` , `-InformationAction` , `-InformationVariable` , `-OutVariable` , `-OutBuffer` , `-PipelineVariable` , `-Verbose` , `-WarningAction` en `-WarningVariable` .</span><span class="sxs-lookup"><span data-stu-id="acda9-225">This cmdlet supports the common parameters: `-Debug`, `-ErrorAction`, `-ErrorVariable`, `-InformationAction`, `-InformationVariable`, `-OutVariable`, `-OutBuffer`, `-PipelineVariable`, `-Verbose`, `-WarningAction`, and `-WarningVariable`.</span></span>
<span data-ttu-id="acda9-226">Zie [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="acda9-226">For more information, see [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md).</span></span>

## <span data-ttu-id="acda9-227">INVOER</span><span class="sxs-lookup"><span data-stu-id="acda9-227">INPUTS</span></span>

### <span data-ttu-id="acda9-228">System. object</span><span class="sxs-lookup"><span data-stu-id="acda9-228">System.Object</span></span>

<span data-ttu-id="acda9-229">U kunt een object dat de nieuwe waarde voor het item bevat, door sluizen naar `Set-Content` .</span><span class="sxs-lookup"><span data-stu-id="acda9-229">You can pipe an object that contains the new value for the item to `Set-Content`.</span></span>

## <span data-ttu-id="acda9-230">UITVOER</span><span class="sxs-lookup"><span data-stu-id="acda9-230">OUTPUTS</span></span>

### <span data-ttu-id="acda9-231">Geen of System. String</span><span class="sxs-lookup"><span data-stu-id="acda9-231">None or System.String</span></span>

<span data-ttu-id="acda9-232">Wanneer u de para meter **PassThru** gebruikt, `Set-Content` genereert een **System. String** -object dat de inhoud vertegenwoordigt.</span><span class="sxs-lookup"><span data-stu-id="acda9-232">When you use the **PassThru** parameter, `Set-Content` generates a **System.String** object that represents the content.</span></span> <span data-ttu-id="acda9-233">Anders wordt met deze cmdlet geen uitvoer gegenereerd.</span><span class="sxs-lookup"><span data-stu-id="acda9-233">Otherwise, this cmdlet does not generate any output.</span></span>

## <span data-ttu-id="acda9-234">OPMERKINGEN</span><span class="sxs-lookup"><span data-stu-id="acda9-234">NOTES</span></span>

- <span data-ttu-id="acda9-235">U kunt ook verwijzen naar `Set-Content` de ingebouwde alias `sc` .</span><span class="sxs-lookup"><span data-stu-id="acda9-235">You can also refer to `Set-Content` by its built-in alias, `sc`.</span></span>
  <span data-ttu-id="acda9-236">Zie [about_Aliases](../Microsoft.PowerShell.Core/About/about_Aliases.md)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="acda9-236">For more information, see [about_Aliases](../Microsoft.PowerShell.Core/About/about_Aliases.md).</span></span>
- <span data-ttu-id="acda9-237">`Set-Content` is ontworpen voor het verwerken van teken reeksen.</span><span class="sxs-lookup"><span data-stu-id="acda9-237">`Set-Content` is designed for string processing.</span></span> <span data-ttu-id="acda9-238">Als u niet-teken reeks objecten naar `Set-Content` een teken reeks in het pipet zet, wordt het object geconverteerd naar een String voordat het wordt geschreven.</span><span class="sxs-lookup"><span data-stu-id="acda9-238">If you pipe non-string objects to `Set-Content`, it converts the object to a string before writing it.</span></span> <span data-ttu-id="acda9-239">Als u objecten naar bestanden wilt schrijven, gebruikt u `Out-File` .</span><span class="sxs-lookup"><span data-stu-id="acda9-239">To write objects to files, use `Out-File`.</span></span>
- <span data-ttu-id="acda9-240">De `Set-Content` cmdlet is ontworpen om te werken met de gegevens die door elke provider worden weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="acda9-240">The `Set-Content` cmdlet is designed to work with the data exposed by any provider.</span></span> <span data-ttu-id="acda9-241">Als u een lijst wilt weer geven van de providers die beschikbaar zijn in uw sessie, typt u `Get-PsProvider` .</span><span class="sxs-lookup"><span data-stu-id="acda9-241">To list the providers available in your session, type `Get-PsProvider`.</span></span> <span data-ttu-id="acda9-242">Zie [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="acda9-242">For more information, see [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md).</span></span>

## <span data-ttu-id="acda9-243">GERELATEERDE KOPPELINGEN</span><span class="sxs-lookup"><span data-stu-id="acda9-243">RELATED LINKS</span></span>

[<span data-ttu-id="acda9-244">about_Aliases</span><span class="sxs-lookup"><span data-stu-id="acda9-244">about_Aliases</span></span>](../Microsoft.PowerShell.Core/About/about_Aliases.md)

[<span data-ttu-id="acda9-245">about_Automatic_Variables. MD</span><span class="sxs-lookup"><span data-stu-id="acda9-245">about_Automatic_Variables.md</span></span>](../Microsoft.PowerShell.Core/About/about_Automatic_Variables.md)

[<span data-ttu-id="acda9-246">about_Providers</span><span class="sxs-lookup"><span data-stu-id="acda9-246">about_Providers</span></span>](../Microsoft.PowerShell.Core/About/about_Providers.md)

[<span data-ttu-id="acda9-247">about_Transactions</span><span class="sxs-lookup"><span data-stu-id="acda9-247">about_Transactions</span></span>](../Microsoft.PowerShell.Core/About/about_Transactions.md)

[<span data-ttu-id="acda9-248">Add-content</span><span class="sxs-lookup"><span data-stu-id="acda9-248">Add-Content</span></span>](Add-Content.md)

[<span data-ttu-id="acda9-249">Wissen-inhoud</span><span class="sxs-lookup"><span data-stu-id="acda9-249">Clear-Content</span></span>](Clear-Content.md)

[<span data-ttu-id="acda9-250">Get-Child item</span><span class="sxs-lookup"><span data-stu-id="acda9-250">Get-ChildItem</span></span>](Get-ChildItem.md)

[<span data-ttu-id="acda9-251">Get-Content</span><span class="sxs-lookup"><span data-stu-id="acda9-251">Get-Content</span></span>](Get-Content.md)

[<span data-ttu-id="acda9-252">ForEach-object</span><span class="sxs-lookup"><span data-stu-id="acda9-252">ForEach-Object</span></span>](../Microsoft.PowerShell.Core/ForEach-Object.md)

[<span data-ttu-id="acda9-253">Nieuw-item</span><span class="sxs-lookup"><span data-stu-id="acda9-253">New-Item</span></span>](New-Item.md)
