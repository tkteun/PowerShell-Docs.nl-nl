---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 04/23/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/add-content?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Add-Content
ms.openlocfilehash: 903c4eb784c1bb86b66766c7dfb563f586545dc1
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/07/2020
ms.locfileid: "93250844"
---
# <span data-ttu-id="e909c-103">Add-Content</span><span class="sxs-lookup"><span data-stu-id="e909c-103">Add-Content</span></span>

## <span data-ttu-id="e909c-104">SAMENVATTING</span><span class="sxs-lookup"><span data-stu-id="e909c-104">SYNOPSIS</span></span>
<span data-ttu-id="e909c-105">Voegt inhoud toe aan de opgegeven items, zoals het toevoegen van woorden aan een bestand.</span><span class="sxs-lookup"><span data-stu-id="e909c-105">Adds content to the specified items, such as adding words to a file.</span></span>

## <span data-ttu-id="e909c-106">SYNTAXIS</span><span class="sxs-lookup"><span data-stu-id="e909c-106">SYNTAX</span></span>

### <span data-ttu-id="e909c-107">Pad (standaard)</span><span class="sxs-lookup"><span data-stu-id="e909c-107">Path (Default)</span></span>

```
Add-Content [-Path] <string[]> [-Value] <Object[]> [-PassThru] [-Filter <string>]
 [-Include <string[]>] [-Exclude <string[]>] [-Force] [-Credential <pscredential>] [-WhatIf]
 [-Confirm] [-UseTransaction] [-NoNewline] [-Encoding <FileSystemCmdletProviderEncoding>]
 [-Stream <string>] [<CommonParameters>]
```

### <span data-ttu-id="e909c-108">LiteralPath</span><span class="sxs-lookup"><span data-stu-id="e909c-108">LiteralPath</span></span>

```
Add-Content [-Value] <Object[]> -LiteralPath <string[]> [-PassThru] [-Filter <string>]
 [-Include <string[]>] [-Exclude <string[]>] [-Force] [-Credential <pscredential>] [-WhatIf]
 [-Confirm] [-UseTransaction] [-NoNewline] [-Encoding <FileSystemCmdletProviderEncoding>]
 [-Stream <string>] [<CommonParameters>]
```

## <span data-ttu-id="e909c-109">BESCHRIJVING</span><span class="sxs-lookup"><span data-stu-id="e909c-109">DESCRIPTION</span></span>

<span data-ttu-id="e909c-110">De `Add-Content` cmdlet voegt inhoud toe aan een opgegeven item of bestand.</span><span class="sxs-lookup"><span data-stu-id="e909c-110">The `Add-Content` cmdlet appends content to a specified item or file.</span></span> <span data-ttu-id="e909c-111">U kunt de inhoud opgeven door de inhoud in de opdracht te typen of door een object op te geven dat de inhoud bevat.</span><span class="sxs-lookup"><span data-stu-id="e909c-111">You can specify the content by typing the content in the command or by specifying an object that contains the content.</span></span>

<span data-ttu-id="e909c-112">Zie [Nieuw-item](New-Item.md)als u bestanden of mappen wilt maken voor de volgende voor beelden.</span><span class="sxs-lookup"><span data-stu-id="e909c-112">If you need to create files or directories for the following examples, see [New-Item](New-Item.md).</span></span>

## <span data-ttu-id="e909c-113">VOORBEELDEN</span><span class="sxs-lookup"><span data-stu-id="e909c-113">EXAMPLES</span></span>

### <span data-ttu-id="e909c-114">Voor beeld 1: een teken reeks toevoegen aan alle tekst bestanden met een uitzonde ring</span><span class="sxs-lookup"><span data-stu-id="e909c-114">Example 1: Add a string to all text files with an exception</span></span>

<span data-ttu-id="e909c-115">In dit voor beeld wordt een waarde aan tekst bestanden in de huidige map toegevoegd, maar worden bestanden uitgesloten op basis van de bestands naam.</span><span class="sxs-lookup"><span data-stu-id="e909c-115">This example appends a value to text files in the current directory but excludes files based on their file name.</span></span>

```powershell
Add-Content -Path .\*.txt -Exclude help* -Value 'End of file'
```

<span data-ttu-id="e909c-116">De `Add-Content` cmdlet gebruikt de para meter **Path** om alle txt-bestanden in de huidige map op te geven.</span><span class="sxs-lookup"><span data-stu-id="e909c-116">The `Add-Content` cmdlet uses the **Path** parameter to specify all .txt files in the current directory.</span></span> <span data-ttu-id="e909c-117">De **exclude** -para meter negeert bestands namen die overeenkomen met het opgegeven patroon.</span><span class="sxs-lookup"><span data-stu-id="e909c-117">The **Exclude** parameter ignores file names that match the specified pattern.</span></span> <span data-ttu-id="e909c-118">De **waarde** para meter geeft u de teken reeks op die naar de bestanden wordt geschreven.</span><span class="sxs-lookup"><span data-stu-id="e909c-118">The **Value** parameter specifies the text string that is written to the files.</span></span>

<span data-ttu-id="e909c-119">Gebruik [Get-content](Get-Content.md) om de inhoud van deze bestanden weer te geven.</span><span class="sxs-lookup"><span data-stu-id="e909c-119">Use [Get-Content](Get-Content.md) to display the contents of these files.</span></span>

### <span data-ttu-id="e909c-120">Voor beeld 2: een datum toevoegen aan het einde van de opgegeven bestanden</span><span class="sxs-lookup"><span data-stu-id="e909c-120">Example 2: Add a date to the end of the specified files</span></span>

<span data-ttu-id="e909c-121">In dit voor beeld wordt de datum toegevoegd aan bestanden in de huidige map en wordt de datum weer gegeven in de Power shell-console.</span><span class="sxs-lookup"><span data-stu-id="e909c-121">This example appends the date to files in the current directory and displays the date in the PowerShell console.</span></span>

```powershell
Add-Content -Path .\DateTimeFile1.log, .\DateTimeFile2.log -Value (Get-Date) -PassThru
Get-Content -Path .\DateTimeFile1.log
```

<span data-ttu-id="e909c-122">De `Add-Content` cmdlet gebruikt de para meters **pad** en **waarde** om twee nieuwe bestanden in de huidige map te maken.</span><span class="sxs-lookup"><span data-stu-id="e909c-122">The `Add-Content` cmdlet uses the **Path** and **Value** parameters to create two new files in the current directory.</span></span> <span data-ttu-id="e909c-123">Met de para meter **Value** wordt de `Get-Date` cmdlet opgegeven om de datum op te halen en wordt de datum door gegeven aan `Add-Content` .</span><span class="sxs-lookup"><span data-stu-id="e909c-123">The **Value** parameter specifies the `Get-Date` cmdlet to get the date and passes the date to `Add-Content`.</span></span> <span data-ttu-id="e909c-124">De `Add-Content` cmdlet schrijft de datum naar elk bestand.</span><span class="sxs-lookup"><span data-stu-id="e909c-124">The `Add-Content` cmdlet writes the date to each file.</span></span> <span data-ttu-id="e909c-125">De para meter **PassThru** geeft een object door dat het object Date vertegenwoordigt.</span><span class="sxs-lookup"><span data-stu-id="e909c-125">The **PassThru** parameter passes an object that represents the date object.</span></span> <span data-ttu-id="e909c-126">Omdat er geen andere cmdlet is om het door gegeven object te ontvangen, wordt het weer gegeven in de Power shell-console.</span><span class="sxs-lookup"><span data-stu-id="e909c-126">Because there is no other cmdlet to receive the passed object, it is displayed in the PowerShell console.</span></span> <span data-ttu-id="e909c-127">Met de `Get-Content` cmdlet wordt het bijgewerkte bestand, DateTimeFile1. log, weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="e909c-127">The `Get-Content` cmdlet displays the updated file, DateTimeFile1.log.</span></span>

### <span data-ttu-id="e909c-128">Voor beeld 3: de inhoud van een opgegeven bestand toevoegen aan een ander bestand</span><span class="sxs-lookup"><span data-stu-id="e909c-128">Example 3: Add the contents of a specified file to another file</span></span>

<span data-ttu-id="e909c-129">In dit voor beeld wordt de inhoud van een bestand opgehaald en wordt die inhoud toegevoegd aan een ander bestand.</span><span class="sxs-lookup"><span data-stu-id="e909c-129">This example gets the content from a file and appends that content into another file.</span></span>

```powershell
Add-Content -Path .\CopyToFile.txt -Value (Get-Content -Path .\CopyFromFile.txt)
Get-Content -Path .\CopyToFile.txt
```

<span data-ttu-id="e909c-130">De `Add-Content` cmdlet gebruikt de para meter **Path** om het nieuwe bestand in de huidige map op te geven CopyToFile.txt.</span><span class="sxs-lookup"><span data-stu-id="e909c-130">The `Add-Content` cmdlet uses the **Path** parameter to specify the new file in the current directory, CopyToFile.txt.</span></span> <span data-ttu-id="e909c-131">De **waarde** para meter gebruikt de `Get-Content` cmdlet om de inhoud van het bestand CopyFromFile.txt te verkrijgen.</span><span class="sxs-lookup"><span data-stu-id="e909c-131">The **Value** parameter uses the `Get-Content` cmdlet to get the contents of the file, CopyFromFile.txt.</span></span> <span data-ttu-id="e909c-132">De haakjes rond de `Get-Content` cmdlet zorgen ervoor dat de opdracht is voltooid voordat de `Add-Content` opdracht wordt gestart.</span><span class="sxs-lookup"><span data-stu-id="e909c-132">The parentheses around the `Get-Content` cmdlet ensure that the command finishes before the `Add-Content` command begins.</span></span> <span data-ttu-id="e909c-133">De **waarde** -para meter wordt door gegeven aan `Add-Content` .</span><span class="sxs-lookup"><span data-stu-id="e909c-133">The **Value** parameter is passed to `Add-Content`.</span></span> <span data-ttu-id="e909c-134">`Add-Content`Met de cmdlet worden de gegevens toegevoegd aan het CopyToFile.txt-bestand.</span><span class="sxs-lookup"><span data-stu-id="e909c-134">The `Add-Content` cmdlet appends the data to the CopyToFile.txt file.</span></span> <span data-ttu-id="e909c-135">De `Get-Content` cmdlet geeft het bijgewerkte bestand weer CopyToFile.txt.</span><span class="sxs-lookup"><span data-stu-id="e909c-135">The `Get-Content` cmdlet displays the updated file, CopyToFile.txt.</span></span>

### <span data-ttu-id="e909c-136">Voor beeld 4: een variabele gebruiken om de inhoud van een opgegeven bestand toe te voegen aan een ander bestand</span><span class="sxs-lookup"><span data-stu-id="e909c-136">Example 4: Use a variable to add the contents of a specified file to another file</span></span>

<span data-ttu-id="e909c-137">In dit voor beeld wordt de inhoud van een bestand opgehaald en wordt de inhoud in een variabele opgeslagen.</span><span class="sxs-lookup"><span data-stu-id="e909c-137">This example gets the content from a file and stores the content in a variable.</span></span> <span data-ttu-id="e909c-138">De variabele wordt gebruikt om de inhoud toe te voegen aan een ander bestand.</span><span class="sxs-lookup"><span data-stu-id="e909c-138">The variable is used to append the content into another file.</span></span>

```powershell
$From = Get-Content -Path .\CopyFromFile.txt
Add-Content -Path .\CopyToFile.txt -Value $From
Get-Content -Path .\CopyToFile.txt
```

<span data-ttu-id="e909c-139">`Get-Content`Met de cmdlet wordt de inhoud van CopyFromFile.txt opgehaald en wordt de inhoud in de `$From` variabele opgeslagen.</span><span class="sxs-lookup"><span data-stu-id="e909c-139">The `Get-Content` cmdlet gets the contents of CopyFromFile.txt and stores the contents in the `$From` variable.</span></span> <span data-ttu-id="e909c-140">De `Add-Content` cmdlet gebruikt de para meter **Path** om het CopyToFile.txt bestand in de huidige map op te geven.</span><span class="sxs-lookup"><span data-stu-id="e909c-140">The `Add-Content` cmdlet uses the **Path** parameter to specify the CopyToFile.txt file in the current directory.</span></span> <span data-ttu-id="e909c-141">De **waarde** para meter gebruikt de `$From` variabele en geeft de inhoud door aan `Add-Content` .</span><span class="sxs-lookup"><span data-stu-id="e909c-141">The **Value** parameter uses the `$From` variable and passes the content to `Add-Content`.</span></span> <span data-ttu-id="e909c-142">De `Add-Content` cmdlet werkt het CopyToFile.txt-bestand bij.</span><span class="sxs-lookup"><span data-stu-id="e909c-142">The `Add-Content` cmdlet updates the CopyToFile.txt file.</span></span> <span data-ttu-id="e909c-143">De `Get-Content` cmdlet geeft CopyToFile.txt weer.</span><span class="sxs-lookup"><span data-stu-id="e909c-143">The `Get-Content` cmdlet displays CopyToFile.txt.</span></span>

### <span data-ttu-id="e909c-144">Voor beeld 5: een nieuw bestand maken en inhoud kopiëren</span><span class="sxs-lookup"><span data-stu-id="e909c-144">Example 5: Create a new file and copy content</span></span>

<span data-ttu-id="e909c-145">In dit voor beeld wordt een nieuw bestand gemaakt en wordt de inhoud van een bestaand bestand gekopieerd naar het nieuwe bestand.</span><span class="sxs-lookup"><span data-stu-id="e909c-145">This example creates a new file and copies an existing file's content into the new file.</span></span>

```powershell
Add-Content -Path .\NewFile.txt -Value (Get-Content -Path .\CopyFromFile.txt)
Get-Content -Path .\NewFile.txt
```

<span data-ttu-id="e909c-146">De `Add-Content` cmdlet maakt gebruik van de para meters **pad** en **waarde** voor het maken van een nieuw bestand in de huidige map.</span><span class="sxs-lookup"><span data-stu-id="e909c-146">The `Add-Content` cmdlet uses the **Path** and **Value** parameters to create a new file in the current directory.</span></span> <span data-ttu-id="e909c-147">De **waarde** para meter gebruikt de `Get-Content` cmdlet om de inhoud van een bestaand bestand te verkrijgen CopyFromFile.txt.</span><span class="sxs-lookup"><span data-stu-id="e909c-147">The **Value** parameter uses the `Get-Content` cmdlet to get the contents of an existing file, CopyFromFile.txt.</span></span> <span data-ttu-id="e909c-148">De haakjes rond de `Get-Content` cmdlet zorgen ervoor dat de opdracht is voltooid voordat de `Add-Content` opdracht wordt gestart.</span><span class="sxs-lookup"><span data-stu-id="e909c-148">The parentheses around the `Get-Content` cmdlet ensure that the command finishes before the `Add-Content` command begins.</span></span> <span data-ttu-id="e909c-149">De **waarde** para meter geeft de inhoud door `Add-Content` waarmee het NewFile.txt bestand wordt bijgewerkt.</span><span class="sxs-lookup"><span data-stu-id="e909c-149">The **Value** parameter passes the content to `Add-Content` which updates the NewFile.txt file.</span></span> <span data-ttu-id="e909c-150">`Get-Content`Met de cmdlet wordt de inhoud van het nieuwe bestand NewFile.txt weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="e909c-150">The `Get-Content` cmdlet displays the contents of the new file, NewFile.txt.</span></span>

### <span data-ttu-id="e909c-151">Voor beeld 6: inhoud toevoegen aan een alleen-lezen bestand</span><span class="sxs-lookup"><span data-stu-id="e909c-151">Example 6: Add content to a read-only file</span></span>

<span data-ttu-id="e909c-152">Met deze opdracht wordt de waarde aan het bestand toegevoegd, zelfs als het kenmerk bestand **IsReadOnly** is ingesteld op True.</span><span class="sxs-lookup"><span data-stu-id="e909c-152">This command adds the value to the file even if the **IsReadOnly** file attribute is set to True.</span></span>
<span data-ttu-id="e909c-153">De stappen voor het maken van een alleen-lezen bestand zijn opgenomen in het voor beeld.</span><span class="sxs-lookup"><span data-stu-id="e909c-153">The steps to create a read-only file are included in the example.</span></span>

```powershell
New-Item -Path .\IsReadOnlyTextFile.txt -ItemType File
Set-ItemProperty -Path .\IsReadOnlyTextFile.txt -Name IsReadOnly -Value $True
Get-ChildItem -Path .\IsReadOnlyTextFile.txt
Add-Content -Path .\IsReadOnlyTextFile.txt -Value 'Add value to read-only text file' -Force
Get-Content -Path .\IsReadOnlyTextFile.txt
```

```Output
Mode                LastWriteTime         Length Name
----                -------------         ------ ----
-ar---        1/28/2019     13:35              0 IsReadOnlyTextFile.txt
```

<span data-ttu-id="e909c-154">De `New-Item` cmdlet maakt gebruik van de para meters **Path** en **item** type voor het maken van het bestand IsReadOnlyTextFile.txt in de huidige map.</span><span class="sxs-lookup"><span data-stu-id="e909c-154">The `New-Item` cmdlet uses the **Path** and **ItemType** parameters to create the file IsReadOnlyTextFile.txt in the current directory.</span></span> <span data-ttu-id="e909c-155">De `Set-ItemProperty` cmdlet gebruikt de para meters **name** en **Value** om de eigenschap **IsReadOnly** van het bestand te wijzigen in True.</span><span class="sxs-lookup"><span data-stu-id="e909c-155">The `Set-ItemProperty` cmdlet uses the **Name** and **Value** parameters to change the file's **IsReadOnly** property to True.</span></span> <span data-ttu-id="e909c-156">De `Get-ChildItem` cmdlet geeft aan dat het bestand leeg is (0) en het kenmerk alleen-lezen ( `r` ) heeft.</span><span class="sxs-lookup"><span data-stu-id="e909c-156">The `Get-ChildItem` cmdlet shows the file is empty (0) and has the read-only attribute (`r`).</span></span> <span data-ttu-id="e909c-157">De `Add-Content` cmdlet gebruikt de para meter **Path** om het bestand op te geven.</span><span class="sxs-lookup"><span data-stu-id="e909c-157">The `Add-Content` cmdlet uses the **Path** parameter to specify the file.</span></span> <span data-ttu-id="e909c-158">De **waarde** para meter bevat de teken reeks die moet worden toegevoegd aan het bestand.</span><span class="sxs-lookup"><span data-stu-id="e909c-158">The **Value** parameter includes the text string to append to the file.</span></span> <span data-ttu-id="e909c-159">De para meter **Force** schrijft de tekst naar het bestand met het kenmerk alleen-lezen.</span><span class="sxs-lookup"><span data-stu-id="e909c-159">The **Force** parameter writes the text to the read-only file.</span></span> <span data-ttu-id="e909c-160">De `Get-Content` cmdlet gebruikt de para meter **Path** om de inhoud van het bestand weer te geven.</span><span class="sxs-lookup"><span data-stu-id="e909c-160">The `Get-Content` cmdlet uses the **Path** parameter to display the file's contents.</span></span>

<span data-ttu-id="e909c-161">Als u het kenmerk alleen-lezen wilt verwijderen, gebruikt u de `Set-ItemProperty` opdracht met de para meter **Value** ingesteld op `False` .</span><span class="sxs-lookup"><span data-stu-id="e909c-161">To remove the read-only attribute, use the `Set-ItemProperty` command with the **Value** parameter set to `False`.</span></span>

## <span data-ttu-id="e909c-162">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="e909c-162">PARAMETERS</span></span>

### <span data-ttu-id="e909c-163">-Confirm</span><span class="sxs-lookup"><span data-stu-id="e909c-163">-Confirm</span></span>

<span data-ttu-id="e909c-164">Hiermee wordt u gevraagd om bevestiging voordat u de cmdlet uitvoert.</span><span class="sxs-lookup"><span data-stu-id="e909c-164">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="e909c-165">-Credential</span><span class="sxs-lookup"><span data-stu-id="e909c-165">-Credential</span></span>

<span data-ttu-id="e909c-166">Hiermee geeft u een gebruikers account op dat is gemachtigd om deze actie uit te voeren.</span><span class="sxs-lookup"><span data-stu-id="e909c-166">Specifies a user account that has permission to perform this action.</span></span> <span data-ttu-id="e909c-167">Standaard is dit de huidige gebruiker.</span><span class="sxs-lookup"><span data-stu-id="e909c-167">The default is the current user.</span></span>

<span data-ttu-id="e909c-168">Typ een gebruikers naam, zoals **gebruiker01** of **Domain01\User01** , of voer een **PSCredential** -object in, zoals het account dat is gegenereerd door de `Get-Credential` cmdlet.</span><span class="sxs-lookup"><span data-stu-id="e909c-168">Type a user name, such as **User01** or **Domain01\User01** , or enter a **PSCredential** object, such as one generated by the `Get-Credential` cmdlet.</span></span> <span data-ttu-id="e909c-169">Als u een gebruikers naam typt, wordt u gevraagd een wacht woord op te vragen.</span><span class="sxs-lookup"><span data-stu-id="e909c-169">If you type a user name, you will be prompted for a password.</span></span>

> [!WARNING]
> <span data-ttu-id="e909c-170">Deze para meter wordt niet ondersteund door providers die zijn geïnstalleerd met Power shell.</span><span class="sxs-lookup"><span data-stu-id="e909c-170">This parameter is not supported by any providers installed with PowerShell.</span></span>

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

### <span data-ttu-id="e909c-171">-Encoding</span><span class="sxs-lookup"><span data-stu-id="e909c-171">-Encoding</span></span>

<span data-ttu-id="e909c-172">Hiermee geeft u het type code ring voor het doel bestand op.</span><span class="sxs-lookup"><span data-stu-id="e909c-172">Specifies the type of encoding for the target file.</span></span> <span data-ttu-id="e909c-173">De standaardwaarde is `Default`.</span><span class="sxs-lookup"><span data-stu-id="e909c-173">The default value is `Default`.</span></span>

<span data-ttu-id="e909c-174">De acceptabele waarden voor deze para meter zijn als volgt:</span><span class="sxs-lookup"><span data-stu-id="e909c-174">The acceptable values for this parameter are as follows:</span></span>

- <span data-ttu-id="e909c-175">`Ascii` Maakt gebruik van ASCII-tekenset (7-bits).</span><span class="sxs-lookup"><span data-stu-id="e909c-175">`Ascii` Uses ASCII (7-bit) character set.</span></span>
- <span data-ttu-id="e909c-176">`BigEndianUnicode` Maakt gebruik van UTF-16 met de byte volgorde big endian.</span><span class="sxs-lookup"><span data-stu-id="e909c-176">`BigEndianUnicode` Uses UTF-16 with the big-endian byte order.</span></span>
- <span data-ttu-id="e909c-177">`BigEndianUTF32` Maakt gebruik van UTF-32 met de byte volgorde big endian.</span><span class="sxs-lookup"><span data-stu-id="e909c-177">`BigEndianUTF32` Uses UTF-32 with the big-endian byte order.</span></span>
- <span data-ttu-id="e909c-178">`Byte` Codeert een reeks tekens in een reeks bytes.</span><span class="sxs-lookup"><span data-stu-id="e909c-178">`Byte` Encodes a set of characters into a sequence of bytes.</span></span>
- <span data-ttu-id="e909c-179">`Default` Gebruikt de code ring die overeenkomt met de actieve code tabel van het systeem (meestal ANSI).</span><span class="sxs-lookup"><span data-stu-id="e909c-179">`Default` Uses the encoding that corresponds to the system's active code page (usually ANSI).</span></span>
- <span data-ttu-id="e909c-180">`Oem` Gebruikt de code ring die overeenkomt met de huidige OEM-code tabel van het systeem.</span><span class="sxs-lookup"><span data-stu-id="e909c-180">`Oem` Uses the encoding that corresponds to the system's current OEM code page.</span></span>
- <span data-ttu-id="e909c-181">`String` Hetzelfde als **Unicode**.</span><span class="sxs-lookup"><span data-stu-id="e909c-181">`String` Same as **Unicode**.</span></span>
- <span data-ttu-id="e909c-182">`Unicode` Maakt gebruik van UTF-16 met de byte volgorde little endian.</span><span class="sxs-lookup"><span data-stu-id="e909c-182">`Unicode` Uses UTF-16 with the little-endian byte order.</span></span>
- <span data-ttu-id="e909c-183">`Unknown` Hetzelfde als **Unicode**.</span><span class="sxs-lookup"><span data-stu-id="e909c-183">`Unknown` Same as **Unicode**.</span></span>
- <span data-ttu-id="e909c-184">`UTF7` Maakt gebruik van UTF-7.</span><span class="sxs-lookup"><span data-stu-id="e909c-184">`UTF7` Uses UTF-7.</span></span>
- <span data-ttu-id="e909c-185">`UTF8` Maakt gebruik van UTF-8.</span><span class="sxs-lookup"><span data-stu-id="e909c-185">`UTF8` Uses UTF-8.</span></span>
- <span data-ttu-id="e909c-186">`UTF32` Maakt gebruik van UTF-32 met de byte volgorde little endian.</span><span class="sxs-lookup"><span data-stu-id="e909c-186">`UTF32` Uses UTF-32 with the little-endian byte order.</span></span>

<span data-ttu-id="e909c-187">Encoding is een dynamische para meter die de File System Provider toevoegt aan de `Add-Content` cmdlet.</span><span class="sxs-lookup"><span data-stu-id="e909c-187">Encoding is a dynamic parameter that the FileSystem provider adds to the `Add-Content` cmdlet.</span></span> <span data-ttu-id="e909c-188">Deze para meter werkt alleen op stations met een bestands systeem.</span><span class="sxs-lookup"><span data-stu-id="e909c-188">This parameter works only in file system drives.</span></span>

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

### <span data-ttu-id="e909c-189">-Uitsluiten</span><span class="sxs-lookup"><span data-stu-id="e909c-189">-Exclude</span></span>

<span data-ttu-id="e909c-190">De opgegeven items worden wegge laten.</span><span class="sxs-lookup"><span data-stu-id="e909c-190">Omits the specified items.</span></span> <span data-ttu-id="e909c-191">De waarde van deze para meter komt in aanmerking voor de para meter **Path** .</span><span class="sxs-lookup"><span data-stu-id="e909c-191">The value of this parameter qualifies the **Path** parameter.</span></span> <span data-ttu-id="e909c-192">Voer een element of patroon van een pad in, zoals **\* . txt**.</span><span class="sxs-lookup"><span data-stu-id="e909c-192">Enter a path element or pattern, such as **\*.txt**.</span></span> <span data-ttu-id="e909c-193">Joker tekens zijn toegestaan.</span><span class="sxs-lookup"><span data-stu-id="e909c-193">Wildcards are permitted.</span></span>

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

### <span data-ttu-id="e909c-194">-Filter</span><span class="sxs-lookup"><span data-stu-id="e909c-194">-Filter</span></span>

<span data-ttu-id="e909c-195">Hiermee geeft u een filter op in de indeling of taal van de provider.</span><span class="sxs-lookup"><span data-stu-id="e909c-195">Specifies a filter in the provider's format or language.</span></span> <span data-ttu-id="e909c-196">De waarde van deze para meter komt in aanmerking voor de para meter **Path** .</span><span class="sxs-lookup"><span data-stu-id="e909c-196">The value of this parameter qualifies the **Path** parameter.</span></span> <span data-ttu-id="e909c-197">De syntaxis van het filter, inclusief het gebruik van joker tekens, is afhankelijk van de provider.</span><span class="sxs-lookup"><span data-stu-id="e909c-197">The syntax of the filter, including the use of wildcards, depends on the provider.</span></span> <span data-ttu-id="e909c-198">**Filters** zijn efficiënter dan andere para meters omdat de provider filters toepast wanneer objecten worden opgehaald.</span><span class="sxs-lookup"><span data-stu-id="e909c-198">**Filters** are more efficient than other parameters because the provider applies filters when objects are retrieved.</span></span> <span data-ttu-id="e909c-199">Als dat niet het geval is, worden filters door Power shell verwerkt nadat de objecten zijn opgehaald.</span><span class="sxs-lookup"><span data-stu-id="e909c-199">Otherwise, PowerShell processes filters after the objects are retrieved.</span></span>

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

### <span data-ttu-id="e909c-200">-Force</span><span class="sxs-lookup"><span data-stu-id="e909c-200">-Force</span></span>

<span data-ttu-id="e909c-201">Onderdrukt het kenmerk alleen-lezen, zodat u inhoud kunt toevoegen aan een alleen-lezen bestand.</span><span class="sxs-lookup"><span data-stu-id="e909c-201">Overrides the read-only attribute, allowing you to add content to a read-only file.</span></span> <span data-ttu-id="e909c-202">**Forceert** bijvoorbeeld het kenmerk alleen-lezen of maakt mappen om een bestandspad te volt ooien, maar er wordt geen poging gedaan om bestands machtigingen te wijzigen.</span><span class="sxs-lookup"><span data-stu-id="e909c-202">For example, **Force** will override the read-only attribute or create directories to complete a file path, but it will not attempt to change file permissions.</span></span>

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

### <span data-ttu-id="e909c-203">-Include</span><span class="sxs-lookup"><span data-stu-id="e909c-203">-Include</span></span>

<span data-ttu-id="e909c-204">Voegt alleen de opgegeven items toe.</span><span class="sxs-lookup"><span data-stu-id="e909c-204">Adds only the specified items.</span></span> <span data-ttu-id="e909c-205">De waarde van deze para meter komt in aanmerking voor de para meter **Path** .</span><span class="sxs-lookup"><span data-stu-id="e909c-205">The value of this parameter qualifies the **Path** parameter.</span></span> <span data-ttu-id="e909c-206">Voer een element of patroon van een pad in, zoals **\* . txt**.</span><span class="sxs-lookup"><span data-stu-id="e909c-206">Enter a path element or pattern, such as **\*.txt**.</span></span> <span data-ttu-id="e909c-207">Joker tekens zijn toegestaan.</span><span class="sxs-lookup"><span data-stu-id="e909c-207">Wildcards are permitted.</span></span>

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

### <span data-ttu-id="e909c-208">-LiteralPath</span><span class="sxs-lookup"><span data-stu-id="e909c-208">-LiteralPath</span></span>

<span data-ttu-id="e909c-209">Hiermee geeft u het pad op naar de items die de extra inhoud ontvangen.</span><span class="sxs-lookup"><span data-stu-id="e909c-209">Specifies the path to the items that receive the additional content.</span></span> <span data-ttu-id="e909c-210">In tegens telling tot **Path** wordt de waarde van **LiteralPath** precies zo gebruikt als deze wordt getypt.</span><span class="sxs-lookup"><span data-stu-id="e909c-210">Unlike **Path** , the value of **LiteralPath** is used exactly as it is typed.</span></span> <span data-ttu-id="e909c-211">Geen tekens worden geïnterpreteerd als joker tekens.</span><span class="sxs-lookup"><span data-stu-id="e909c-211">No characters are interpreted as wildcards.</span></span> <span data-ttu-id="e909c-212">Als het pad escape tekens bevat, plaatst u het tussen enkele aanhalings tekens.</span><span class="sxs-lookup"><span data-stu-id="e909c-212">If the path includes escape characters, enclose it in single quotation marks.</span></span> <span data-ttu-id="e909c-213">Enkele aanhalings tekens geven aan dat Power shell geen karakters interpreteert als escape reeksen.</span><span class="sxs-lookup"><span data-stu-id="e909c-213">Single quotation marks tell PowerShell not to interpret any characters as escape sequences.</span></span>

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

### <span data-ttu-id="e909c-214">-Nieuwe regel</span><span class="sxs-lookup"><span data-stu-id="e909c-214">-NoNewline</span></span>

<span data-ttu-id="e909c-215">Geeft aan dat met deze cmdlet geen nieuwe regel wordt toegevoegd of het retour neren naar de inhoud.</span><span class="sxs-lookup"><span data-stu-id="e909c-215">Indicates that this cmdlet does not add a new line or carriage return to the content.</span></span>

<span data-ttu-id="e909c-216">De teken reeks representaties van de invoer objecten worden samengevoegd om de uitvoer te vormen.</span><span class="sxs-lookup"><span data-stu-id="e909c-216">The string representations of the input objects are concatenated to form the output.</span></span> <span data-ttu-id="e909c-217">Er worden geen spaties of nieuwe regels tussen de uitvoer teken reeksen ingevoegd.</span><span class="sxs-lookup"><span data-stu-id="e909c-217">No spaces or newlines are inserted between the output strings.</span></span> <span data-ttu-id="e909c-218">Er wordt geen nieuwe regel toegevoegd na de laatste uitvoer teken reeks.</span><span class="sxs-lookup"><span data-stu-id="e909c-218">No newline is added after the last output string.</span></span>

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

### <span data-ttu-id="e909c-219">-PassThru</span><span class="sxs-lookup"><span data-stu-id="e909c-219">-PassThru</span></span>

<span data-ttu-id="e909c-220">Retourneert een object dat de toegevoegde inhoud vertegenwoordigt.</span><span class="sxs-lookup"><span data-stu-id="e909c-220">Returns an object representing the added content.</span></span> <span data-ttu-id="e909c-221">Deze cmdlet genereert standaard geen uitvoer.</span><span class="sxs-lookup"><span data-stu-id="e909c-221">By default, this cmdlet does not generate any output.</span></span>

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

### <span data-ttu-id="e909c-222">-Path</span><span class="sxs-lookup"><span data-stu-id="e909c-222">-Path</span></span>

<span data-ttu-id="e909c-223">Hiermee geeft u het pad op naar de items die de extra inhoud ontvangen.</span><span class="sxs-lookup"><span data-stu-id="e909c-223">Specifies the path to the items that receive the additional content.</span></span> <span data-ttu-id="e909c-224">Joker tekens zijn toegestaan.</span><span class="sxs-lookup"><span data-stu-id="e909c-224">Wildcards are permitted.</span></span> <span data-ttu-id="e909c-225">Als u meerdere paden opgeeft, gebruikt u komma's om de paden van elkaar te scheiden.</span><span class="sxs-lookup"><span data-stu-id="e909c-225">If you specify multiple paths, use commas to separate the paths.</span></span>

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

### <span data-ttu-id="e909c-226">-Stream</span><span class="sxs-lookup"><span data-stu-id="e909c-226">-Stream</span></span>

<span data-ttu-id="e909c-227">Hiermee geeft u een alternatieve gegevens stroom voor inhoud.</span><span class="sxs-lookup"><span data-stu-id="e909c-227">Specifies an alternative data stream for content.</span></span> <span data-ttu-id="e909c-228">Als de stroom niet bestaat, wordt deze gemaakt met deze cmdlet.</span><span class="sxs-lookup"><span data-stu-id="e909c-228">If the stream does not exist, this cmdlet creates it.</span></span> <span data-ttu-id="e909c-229">Joker tekens worden niet ondersteund.</span><span class="sxs-lookup"><span data-stu-id="e909c-229">Wildcard characters are not supported.</span></span>

<span data-ttu-id="e909c-230">**Stream** is een dynamische para meter waaraan de File System Provider toevoegt `Add-Content` .</span><span class="sxs-lookup"><span data-stu-id="e909c-230">**Stream** is a dynamic parameter that the FileSystem provider adds to `Add-Content`.</span></span> <span data-ttu-id="e909c-231">Deze para meter werkt alleen op stations met een bestands systeem.</span><span class="sxs-lookup"><span data-stu-id="e909c-231">This parameter works only in file system drives.</span></span>

<span data-ttu-id="e909c-232">U kunt de- `Add-Content` cmdlet gebruiken om de inhoud van de **zone te wijzigen. id** alternatieve gegevens stroom.</span><span class="sxs-lookup"><span data-stu-id="e909c-232">You can use the `Add-Content` cmdlet to change the content of the **Zone.Identifier** alternate data stream.</span></span> <span data-ttu-id="e909c-233">Dit wordt echter niet aangeraden als een manier om beveiligings controles te elimineren waarmee bestanden die worden gedownload van Internet, worden geblokkeerd.</span><span class="sxs-lookup"><span data-stu-id="e909c-233">However, we do not recommend this as a way to eliminate security checks that block files that are downloaded from the Internet.</span></span> <span data-ttu-id="e909c-234">Als u controleert of een gedownload bestand veilig is, gebruikt u de `Unblock-File` cmdlet.</span><span class="sxs-lookup"><span data-stu-id="e909c-234">If you verify that a downloaded file is safe, use the `Unblock-File` cmdlet.</span></span>

<span data-ttu-id="e909c-235">Deze para meter is geïntroduceerd in Power Shell 3,0.</span><span class="sxs-lookup"><span data-stu-id="e909c-235">This parameter was introduced in PowerShell 3.0.</span></span>

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

### <span data-ttu-id="e909c-236">-UseTransaction</span><span class="sxs-lookup"><span data-stu-id="e909c-236">-UseTransaction</span></span>

<span data-ttu-id="e909c-237">Hiermee wordt de opdracht opgenomen in de actieve transactie.</span><span class="sxs-lookup"><span data-stu-id="e909c-237">Includes the command in the active transaction.</span></span> <span data-ttu-id="e909c-238">Deze parameter is alleen geldig wanneer een transactie wordt uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="e909c-238">This parameter is valid only when a transaction is in progress.</span></span> <span data-ttu-id="e909c-239">Zie [about_Transactions](../Microsoft.PowerShell.Core/About/about_Transactions.md)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="e909c-239">For more information, see [about_Transactions](../Microsoft.PowerShell.Core/About/about_Transactions.md).</span></span>

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

### <span data-ttu-id="e909c-240">-Waarde</span><span class="sxs-lookup"><span data-stu-id="e909c-240">-Value</span></span>

<span data-ttu-id="e909c-241">Hiermee geeft u de inhoud moet worden toegevoegd.</span><span class="sxs-lookup"><span data-stu-id="e909c-241">Specifies the content to be added.</span></span> <span data-ttu-id="e909c-242">Typ een teken reeks tussen aanhalings tekens, zoals **deze gegevens zijn alleen voor intern gebruik** , of geef een object op dat inhoud bevat, zoals het **DateTime** -object dat `Get-Date` genereert.</span><span class="sxs-lookup"><span data-stu-id="e909c-242">Type a quoted string, such as **This data is for internal use only** , or specify an object that contains content, such as the **DateTime** object that `Get-Date` generates.</span></span>

<span data-ttu-id="e909c-243">U kunt de inhoud van een bestand niet opgeven door het bijbehorende pad te typen, omdat het pad alleen een teken reeks is.</span><span class="sxs-lookup"><span data-stu-id="e909c-243">You cannot specify the contents of a file by typing its path, because the path is just a string.</span></span>
<span data-ttu-id="e909c-244">U kunt een `Get-Content` opdracht gebruiken om de inhoud op te halen en door te geven aan de **waarde** -para meter.</span><span class="sxs-lookup"><span data-stu-id="e909c-244">You can use a `Get-Content` command to get the content and pass it to the **Value** parameter.</span></span>

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

### <span data-ttu-id="e909c-245">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="e909c-245">-WhatIf</span></span>

<span data-ttu-id="e909c-246">Hiermee wordt weergegeven wat er zou gebeuren als u de cmdlet uitvoert.</span><span class="sxs-lookup"><span data-stu-id="e909c-246">Shows what would happen if the cmdlet runs.</span></span> <span data-ttu-id="e909c-247">De cmdlet wordt niet uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="e909c-247">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="e909c-248">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="e909c-248">CommonParameters</span></span>

<span data-ttu-id="e909c-249">Deze cmdlet biedt ondersteuning voor de algemene para meters: `-Debug` , `-ErrorAction` , `-ErrorVariable` , `-InformationAction` , `-InformationVariable` , `-OutVariable` , `-OutBuffer` , `-PipelineVariable` , `-Verbose` , `-WarningAction` en `-WarningVariable` .</span><span class="sxs-lookup"><span data-stu-id="e909c-249">This cmdlet supports the common parameters: `-Debug`, `-ErrorAction`, `-ErrorVariable`, `-InformationAction`, `-InformationVariable`, `-OutVariable`, `-OutBuffer`, `-PipelineVariable`, `-Verbose`, `-WarningAction`, and `-WarningVariable`.</span></span> <span data-ttu-id="e909c-250">Zie [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="e909c-250">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="e909c-251">INVOER</span><span class="sxs-lookup"><span data-stu-id="e909c-251">INPUTS</span></span>

### <span data-ttu-id="e909c-252">System. object, System. Management. Automation. PSCredential</span><span class="sxs-lookup"><span data-stu-id="e909c-252">System.Object, System.Management.Automation.PSCredential</span></span>

<span data-ttu-id="e909c-253">U kunt waarden, paden of referenties door sluizen naar `Set-Content` .</span><span class="sxs-lookup"><span data-stu-id="e909c-253">You can pipe values, paths, or credentials to `Set-Content`.</span></span>

## <span data-ttu-id="e909c-254">UITVOER</span><span class="sxs-lookup"><span data-stu-id="e909c-254">OUTPUTS</span></span>

### <span data-ttu-id="e909c-255">Geen of System. String</span><span class="sxs-lookup"><span data-stu-id="e909c-255">None or System.String</span></span>

<span data-ttu-id="e909c-256">Wanneer u de para meter **PassThru** gebruikt, `Add-Content` genereert een **System. String** -object dat de inhoud vertegenwoordigt.</span><span class="sxs-lookup"><span data-stu-id="e909c-256">When you use the **PassThru** parameter, `Add-Content` generates a **System.String** object that represents the content.</span></span> <span data-ttu-id="e909c-257">Anders wordt met deze cmdlet geen uitvoer gegenereerd.</span><span class="sxs-lookup"><span data-stu-id="e909c-257">Otherwise, this cmdlet does not generate any output.</span></span>

## <span data-ttu-id="e909c-258">OPMERKINGEN</span><span class="sxs-lookup"><span data-stu-id="e909c-258">NOTES</span></span>

<span data-ttu-id="e909c-259">Wanneer u een object pipet naar `Add-Content` , wordt het object geconverteerd naar een teken reeks voordat het aan het item wordt toegevoegd.</span><span class="sxs-lookup"><span data-stu-id="e909c-259">When you pipe an object to `Add-Content`, the object is converted to a string before it is added to the item.</span></span> <span data-ttu-id="e909c-260">Het object type bepaalt de teken reeks notatie, maar de notatie kan afwijken van de standaard weergave van het object.</span><span class="sxs-lookup"><span data-stu-id="e909c-260">The object type determines the string format, but the format might be different than the default display of the object.</span></span> <span data-ttu-id="e909c-261">Als u de teken reeks indeling wilt beheren, gebruikt u de opmaak parameters van de verzenden-cmdlet.</span><span class="sxs-lookup"><span data-stu-id="e909c-261">To control the string format, use the formatting parameters of the sending cmdlet.</span></span>

<span data-ttu-id="e909c-262">U kunt ook verwijzen naar `Add-Content` de ingebouwde alias `ac` .</span><span class="sxs-lookup"><span data-stu-id="e909c-262">You can also refer to `Add-Content` by its built-in alias, `ac`.</span></span> <span data-ttu-id="e909c-263">Zie [about_Aliases](../Microsoft.PowerShell.Core/About/about_Aliases.md)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="e909c-263">For more information, see [about_Aliases](../Microsoft.PowerShell.Core/About/about_Aliases.md).</span></span>

<span data-ttu-id="e909c-264">De `Add-Content` cmdlet is ontworpen om te werken met de gegevens die door elke provider worden weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="e909c-264">The `Add-Content` cmdlet is designed to work with the data exposed by any provider.</span></span> <span data-ttu-id="e909c-265">Als u een lijst wilt weer geven van de providers die beschikbaar zijn in uw sessie, typt u `Get-PSProvider` .</span><span class="sxs-lookup"><span data-stu-id="e909c-265">To list the providers available in your session, type `Get-PSProvider`.</span></span> <span data-ttu-id="e909c-266">Zie [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="e909c-266">For more information, see [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md).</span></span>

## <span data-ttu-id="e909c-267">GERELATEERDE KOPPELINGEN</span><span class="sxs-lookup"><span data-stu-id="e909c-267">RELATED LINKS</span></span>

[<span data-ttu-id="e909c-268">about_Aliases</span><span class="sxs-lookup"><span data-stu-id="e909c-268">about_Aliases</span></span>](../Microsoft.PowerShell.Core/About/about_Aliases.md)

[<span data-ttu-id="e909c-269">about_Providers</span><span class="sxs-lookup"><span data-stu-id="e909c-269">about_Providers</span></span>](../Microsoft.PowerShell.Core/About/about_Providers.md)

[<span data-ttu-id="e909c-270">about_Transactions</span><span class="sxs-lookup"><span data-stu-id="e909c-270">about_Transactions</span></span>](../Microsoft.PowerShell.Core/About/about_Transactions.md)

[<span data-ttu-id="e909c-271">Wissen-inhoud</span><span class="sxs-lookup"><span data-stu-id="e909c-271">Clear-Content</span></span>](Clear-Content.md)

[<span data-ttu-id="e909c-272">Get-Content</span><span class="sxs-lookup"><span data-stu-id="e909c-272">Get-Content</span></span>](Get-Content.md)

[<span data-ttu-id="e909c-273">Get-item</span><span class="sxs-lookup"><span data-stu-id="e909c-273">Get-Item</span></span>](Get-Item.md)

[<span data-ttu-id="e909c-274">Nieuw-item</span><span class="sxs-lookup"><span data-stu-id="e909c-274">New-Item</span></span>](New-Item.md)

[<span data-ttu-id="e909c-275">Set-Content</span><span class="sxs-lookup"><span data-stu-id="e909c-275">Set-Content</span></span>](Set-Content.md)
