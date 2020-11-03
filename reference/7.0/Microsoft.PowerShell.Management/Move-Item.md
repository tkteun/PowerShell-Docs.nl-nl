---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 5/14/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/move-item?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Move-Item
ms.openlocfilehash: b331398480243bbc23059acfa9a2c0cbb344c0cc
ms.sourcegitcommit: de63e9481cf8024883060aae61fb02c59c2de662
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/03/2020
ms.locfileid: "93249459"
---
# <span data-ttu-id="d25e6-103">Move-Item</span><span class="sxs-lookup"><span data-stu-id="d25e6-103">Move-Item</span></span>

## <span data-ttu-id="d25e6-104">SAMENVATTING</span><span class="sxs-lookup"><span data-stu-id="d25e6-104">SYNOPSIS</span></span>
<span data-ttu-id="d25e6-105">Hiermee verplaatst u een item van de ene locatie naar een andere.</span><span class="sxs-lookup"><span data-stu-id="d25e6-105">Moves an item from one location to another.</span></span>

## <span data-ttu-id="d25e6-106">SYNTAXIS</span><span class="sxs-lookup"><span data-stu-id="d25e6-106">SYNTAX</span></span>

### <span data-ttu-id="d25e6-107">Pad (standaard)</span><span class="sxs-lookup"><span data-stu-id="d25e6-107">Path (Default)</span></span>

```
Move-Item [-Path] <String[]> [[-Destination] <String>] [-Force] [-Filter <String>] [-Include <String[]>]
 [-Exclude <String[]>] [-PassThru] [-Credential <PSCredential>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="d25e6-108">LiteralPath</span><span class="sxs-lookup"><span data-stu-id="d25e6-108">LiteralPath</span></span>

```
Move-Item -LiteralPath <String[]> [[-Destination] <String>] [-Force] [-Filter <String>] [-Include <String[]>]
 [-Exclude <String[]>] [-PassThru] [-Credential <PSCredential>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="d25e6-109">BESCHRIJVING</span><span class="sxs-lookup"><span data-stu-id="d25e6-109">DESCRIPTION</span></span>

<span data-ttu-id="d25e6-110">`Move-Item`Met de cmdlet wordt een item, inclusief eigenschappen, inhoud en onderliggende items, verplaatst van de ene locatie naar een andere locatie.</span><span class="sxs-lookup"><span data-stu-id="d25e6-110">The `Move-Item` cmdlet moves an item, including its properties, contents, and child items, from one location to another location.</span></span> <span data-ttu-id="d25e6-111">De locaties moeten door dezelfde provider worden ondersteund.</span><span class="sxs-lookup"><span data-stu-id="d25e6-111">The locations must be supported by the same provider.</span></span>
<span data-ttu-id="d25e6-112">Zo kunt u een bestand of submap van de ene map naar de andere verplaatsen of een registersubsleutel van de ene naar de andere sleutel verplaatsen.</span><span class="sxs-lookup"><span data-stu-id="d25e6-112">For example, it can move a file or subdirectory from one directory to another or move a registry subkey from one key to another.</span></span>
<span data-ttu-id="d25e6-113">Wanneer u een item verplaatst, wordt het toegevoegd aan de nieuwe locatie en verwijderd uit de oorspronkelijke locatie.</span><span class="sxs-lookup"><span data-stu-id="d25e6-113">When you move an item, it is added to the new location and deleted from its original location.</span></span>

## <span data-ttu-id="d25e6-114">VOORBEELDEN</span><span class="sxs-lookup"><span data-stu-id="d25e6-114">EXAMPLES</span></span>

### <span data-ttu-id="d25e6-115">Voor beeld 1: een bestand verplaatsen naar een andere map en de naam wijzigen</span><span class="sxs-lookup"><span data-stu-id="d25e6-115">Example 1: Move a file to another directory and rename it</span></span>

<span data-ttu-id="d25e6-116">Met deze opdracht `Test.txt` wordt het bestand van het `C:` station verplaatst naar de `E:\Temp` map en wordt de naam gewijzigd van `test.txt` in `tst.txt` .</span><span class="sxs-lookup"><span data-stu-id="d25e6-116">This command moves the `Test.txt` file from the `C:` drive to the `E:\Temp` directory and renames it from `test.txt` to `tst.txt`.</span></span>

```powershell
Move-Item -Path C:\test.txt -Destination E:\Temp\tst.txt
```

### <span data-ttu-id="d25e6-117">Voor beeld 2: een map en de inhoud naar een andere map verplaatsen</span><span class="sxs-lookup"><span data-stu-id="d25e6-117">Example 2: Move a directory and its contents to another directory</span></span>

<span data-ttu-id="d25e6-118">Met deze opdracht verplaatst `C:\Temp` u de map en de inhoud ervan naar de `C:\Logs` map.</span><span class="sxs-lookup"><span data-stu-id="d25e6-118">This command moves the `C:\Temp` directory and its contents to the `C:\Logs` directory.</span></span>
<span data-ttu-id="d25e6-119">De map Temp en alle bijbehorende submappen en bestanden, worden weer gegeven in de map logs.</span><span class="sxs-lookup"><span data-stu-id="d25e6-119">The "Temp" directory, and all of its subdirectories and files, then appear in the "Logs" directory.</span></span>

```powershell
Move-Item -Path C:\Temp -Destination C:\Logs
```

### <span data-ttu-id="d25e6-120">Voor beeld 3: alle bestanden van een opgegeven extensie verplaatsen van de huidige map naar een andere map</span><span class="sxs-lookup"><span data-stu-id="d25e6-120">Example 3: Move all files of a specified extension from the current directory to another directory</span></span>

<span data-ttu-id="d25e6-121">Met deze opdracht worden alle tekst bestanden ( `*.txt` ) in de huidige map (aangeduid door een punt ( `.` )) naar de `C:\Logs` map verplaatst.</span><span class="sxs-lookup"><span data-stu-id="d25e6-121">This command moves all of the text files (`*.txt`) in the current directory (represented by a dot (`.`)) to the `C:\Logs` directory.</span></span>

```powershell
Move-Item -Path .\*.txt -Destination C:\Logs
```

### <span data-ttu-id="d25e6-122">Voor beeld 4: alle bestanden van een opgegeven extensie recursief verplaatsen vanuit de huidige map naar een andere map</span><span class="sxs-lookup"><span data-stu-id="d25e6-122">Example 4: Recursively move all files of a specified extension from the current directory to another directory</span></span>

<span data-ttu-id="d25e6-123">Met deze opdracht worden alle tekst bestanden van de huidige map en alle submappen, recursief, naar de map C:\TextFiles verplaatst.</span><span class="sxs-lookup"><span data-stu-id="d25e6-123">This command moves all of the text files from the current directory and all subdirectories, recursively, to the "C:\TextFiles" directory.</span></span>

```powershell
Get-ChildItem -Path ".\*.txt" -Recurse | Move-Item -Destination "C:\TextFiles"
```

<span data-ttu-id="d25e6-124">De opdracht gebruikt de `Get-ChildItem` cmdlet om alle onderliggende items in de huidige map op te halen (vertegenwoordigd door de punt \[ \] ) en de bijbehorende submappen met de *bestandsnaam extensie. txt. Hierbij wordt gebruikgemaakt van de para meter **recursieve** om het ophalen van recursie en de para meter include te beperken tot het ophalen van '*. txt ' bestanden.</span><span class="sxs-lookup"><span data-stu-id="d25e6-124">The command uses the `Get-ChildItem` cmdlet to get all of the child items in the current directory (represented by the dot \[.\]) and its subdirectories that have a " *.txt" file name extension. It uses the **Recurse** parameter to make the retrieval recursive and the Include parameter to limit the retrieval to "*.txt" files.</span></span>

<span data-ttu-id="d25e6-125">De pijplijn operator ( `|` ) verzendt de resultaten van deze opdracht naar `Move-Item` , die de tekst bestanden verplaatst naar de map ' TextFiles '.</span><span class="sxs-lookup"><span data-stu-id="d25e6-125">The pipeline operator (`|`) sends the results of this command to `Move-Item`, which moves the text files to the "TextFiles" directory.</span></span>

<span data-ttu-id="d25e6-126">Als bestanden die worden verplaatst naar ' C:\Textfiles ' dezelfde naam hebben, `Move-Item` wordt er een fout weer gegeven en wordt de functie voortgezet, maar wordt slechts één bestand met elke naam verplaatst naar ' C:\Textfiles '.</span><span class="sxs-lookup"><span data-stu-id="d25e6-126">If files that are to be moved to "C:\Textfiles" have the same name, `Move-Item` displays an error and continues, but it moves only one file with each name to "C:\Textfiles".</span></span>
<span data-ttu-id="d25e6-127">De andere bestanden blijven in de oorspronkelijke mappen staan.</span><span class="sxs-lookup"><span data-stu-id="d25e6-127">The other files remain in their original directories.</span></span>

<span data-ttu-id="d25e6-128">Als de map ' textfiles ' (of een ander element van het doelpad) niet bestaat, mislukt de opdracht.</span><span class="sxs-lookup"><span data-stu-id="d25e6-128">If the "Textfiles" directory (or any other element of the destination path) does not exist, the command fails.</span></span>
<span data-ttu-id="d25e6-129">De ontbrekende map wordt niet voor u gemaakt, zelfs niet als u de para meter **Forces** gebruikt.</span><span class="sxs-lookup"><span data-stu-id="d25e6-129">The missing directory is not created for you, even if you use the **Force** parameter.</span></span>
<span data-ttu-id="d25e6-130">`Move-Item` Hiermee wordt het eerste item verplaatst naar een bestand met de naam ' textfiles ' en wordt er een fout weer gegeven waarin wordt uitgelegd dat het bestand al bestaat.</span><span class="sxs-lookup"><span data-stu-id="d25e6-130">`Move-Item` moves the first item to a file called "Textfiles" and then displays an error explaining that the file already exists.</span></span>

<span data-ttu-id="d25e6-131">Ook worden `Get-ChildItem` verborgen bestanden standaard niet verplaatst.</span><span class="sxs-lookup"><span data-stu-id="d25e6-131">Also, by default, `Get-ChildItem` does not move hidden files.</span></span>
<span data-ttu-id="d25e6-132">Als u verborgen bestanden wilt verplaatsen, gebruikt u de para meter **Force** with `Get-ChildItem` .</span><span class="sxs-lookup"><span data-stu-id="d25e6-132">To move hidden files, use the **Force** parameter with `Get-ChildItem`.</span></span>

> [!NOTE]
> <span data-ttu-id="d25e6-133">Bij het gebruik van de **recursieve** para meter van de cmdlet in Windows power Shell 2,0 `Get-ChildItem` moet de waarde van de para meter **Path** een container zijn.</span><span class="sxs-lookup"><span data-stu-id="d25e6-133">In Windows PowerShell 2.0, when using the **Recurse** parameter of the `Get-ChildItem` cmdlet, the value of the **Path** parameter must be a container.</span></span>
> <span data-ttu-id="d25e6-134">Gebruik de para meter **include** om het txt-bestand met de extensie filter () op te geven `Get-ChildItem -Path .\* -Include *.txt -Recurse | Move-Item -Destination C:\TextFiles` .</span><span class="sxs-lookup"><span data-stu-id="d25e6-134">Use the **Include** parameter to specify the .txt file name extension filter (`Get-ChildItem -Path .\* -Include *.txt -Recurse | Move-Item -Destination C:\TextFiles`).</span></span>

### <span data-ttu-id="d25e6-135">Voor beeld 5: register sleutels en-waarden naar een andere sleutel verplaatsen</span><span class="sxs-lookup"><span data-stu-id="d25e6-135">Example 5: Move registry keys and values to another key</span></span>

<span data-ttu-id="d25e6-136">Met deze opdracht verplaatst u de register sleutels en-waarden in de register sleutel ' mijn bedrijf ' in `HKLM\Software` naar de sleutel ' MyNewCompany '.</span><span class="sxs-lookup"><span data-stu-id="d25e6-136">This command moves the registry keys and values within the "MyCompany" registry key in `HKLM\Software` to the "MyNewCompany" key.</span></span>
<span data-ttu-id="d25e6-137">Het Joker teken ( `*` ) geeft aan dat de inhoud van de sleutel ' mijn bedrijf ' moet worden verplaatst, niet de sleutel zelf.</span><span class="sxs-lookup"><span data-stu-id="d25e6-137">The wildcard character (`*`) indicates that the contents of the "MyCompany" key should be moved, not the key itself.</span></span>
<span data-ttu-id="d25e6-138">In deze opdracht worden de namen van de optionele **paden** en **doel** parameters wegge laten.</span><span class="sxs-lookup"><span data-stu-id="d25e6-138">In this command, the optional **Path** and **Destination** parameter names are omitted.</span></span>

```powershell
Move-Item "HKLM:\software\mycompany\*" "HKLM:\software\mynewcompany"
```

### <span data-ttu-id="d25e6-139">Voor beeld 6: een map en de inhoud ervan verplaatsen naar een submap van de opgegeven map</span><span class="sxs-lookup"><span data-stu-id="d25e6-139">Example 6: Move a directory and its contents to a subdirectory of the specified directory</span></span>

<span data-ttu-id="d25e6-140">Met deze opdracht wordt de map ' logs \[ Sept \` 06 \] ' (en de inhoud ervan) verplaatst naar de map ' logs \[ 2006 \] '.</span><span class="sxs-lookup"><span data-stu-id="d25e6-140">This command moves the "Logs\[Sept\`06\]" directory (and its contents) into the "Logs\[2006\]" directory.</span></span>

```powershell
Move-Item -LiteralPath 'Logs[Sept`06]' -Destination 'Logs[2006]'
```

<span data-ttu-id="d25e6-141">De para meter **LiteralPath** wordt gebruikt in plaats van het **pad** , omdat de naam van de oorspronkelijke map links van het haakje en rechter vier Kante tekens (" \[ " en " \] ") bevat.</span><span class="sxs-lookup"><span data-stu-id="d25e6-141">The **LiteralPath** parameter is used instead of **Path** , because the original directory name includes left bracket and right bracket characters ("\[" and "\]").</span></span>
<span data-ttu-id="d25e6-142">Het pad bevindt zich ook tussen enkele aanhalings tekens (' '), zodat het apostroffen-symbool ( \` ) niet wordt geïnterpreteerd.</span><span class="sxs-lookup"><span data-stu-id="d25e6-142">The path is also enclosed in single quotation marks (' '), so that the backtick symbol (\`) is not misinterpreted.</span></span>

<span data-ttu-id="d25e6-143">Voor de para meter **Destination** is geen letterlijk pad vereist, omdat de doel variabele ook tussen enkele aanhalings tekens moet worden geplaatst, omdat deze haakjes bevat die kunnen worden geïnterpreteerd.</span><span class="sxs-lookup"><span data-stu-id="d25e6-143">The **Destination** parameter does not require a literal path, because the Destination variable also must be enclosed in single quotation marks, because it includes brackets that can be misinterpreted.</span></span>

## <span data-ttu-id="d25e6-144">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="d25e6-144">PARAMETERS</span></span>

### <span data-ttu-id="d25e6-145">-Credential</span><span class="sxs-lookup"><span data-stu-id="d25e6-145">-Credential</span></span>

> [!NOTE]
> <span data-ttu-id="d25e6-146">Deze para meter wordt niet ondersteund door providers die zijn geïnstalleerd met Power shell.</span><span class="sxs-lookup"><span data-stu-id="d25e6-146">This parameter is not supported by any providers installed with PowerShell.</span></span>
> <span data-ttu-id="d25e6-147">Gebruik [invoke-Command](../Microsoft.PowerShell.Core/Invoke-Command.md)om een andere gebruiker te imiteren of uw referenties te verhogen wanneer u deze cmdlet uitvoert.</span><span class="sxs-lookup"><span data-stu-id="d25e6-147">To impersonate another user, or elevate your credentials when running this cmdlet, use [Invoke-Command](../Microsoft.PowerShell.Core/Invoke-Command.md).</span></span>

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

### <span data-ttu-id="d25e6-148">-Bestemming</span><span class="sxs-lookup"><span data-stu-id="d25e6-148">-Destination</span></span>

<span data-ttu-id="d25e6-149">Hiermee geeft u het pad op naar de locatie waar de items worden verplaatst.</span><span class="sxs-lookup"><span data-stu-id="d25e6-149">Specifies the path to the location where the items are being moved.</span></span>
<span data-ttu-id="d25e6-150">De standaardwaarde is de huidige map.</span><span class="sxs-lookup"><span data-stu-id="d25e6-150">The default is the current directory.</span></span>
<span data-ttu-id="d25e6-151">Joker tekens zijn toegestaan, maar in het resultaat moet één locatie worden opgegeven.</span><span class="sxs-lookup"><span data-stu-id="d25e6-151">Wildcards are permitted, but the result must specify a single location.</span></span>

<span data-ttu-id="d25e6-152">Als u de naam van het item dat wordt verplaatst, wilt wijzigen, geeft u een nieuwe naam op in de waarde van de para meter **Destination** .</span><span class="sxs-lookup"><span data-stu-id="d25e6-152">To rename the item being moved, specify a new name in the value of the **Destination** parameter.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: 1
Default value: Current directory
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: True
```

### <span data-ttu-id="d25e6-153">-Uitsluiten</span><span class="sxs-lookup"><span data-stu-id="d25e6-153">-Exclude</span></span>

<span data-ttu-id="d25e6-154">Hiermee geeft u als een teken reeks matrix een item of items die met deze cmdlet worden uitgesloten in de bewerking.</span><span class="sxs-lookup"><span data-stu-id="d25e6-154">Specifies, as a string array, an item or items that this cmdlet excludes in the operation.</span></span> <span data-ttu-id="d25e6-155">De waarde van deze para meter komt in aanmerking voor de para meter **Path** .</span><span class="sxs-lookup"><span data-stu-id="d25e6-155">The value of this parameter qualifies the **Path** parameter.</span></span> <span data-ttu-id="d25e6-156">Voer een element of patroon van een pad in, zoals `*.txt` .</span><span class="sxs-lookup"><span data-stu-id="d25e6-156">Enter a path element or pattern, such as `*.txt`.</span></span> <span data-ttu-id="d25e6-157">Joker tekens zijn toegestaan.</span><span class="sxs-lookup"><span data-stu-id="d25e6-157">Wildcard characters are permitted.</span></span> <span data-ttu-id="d25e6-158">De **exclude** -para meter is alleen effectief wanneer de inhoud van een item wordt opgenomen, zoals `C:\Windows\*` , waarbij het Joker teken de inhoud van de `C:\Windows` map bevat.</span><span class="sxs-lookup"><span data-stu-id="d25e6-158">The **Exclude** parameter is effective only when the command includes the contents of an item, such as `C:\Windows\*`, where the wildcard character specifies the contents of the `C:\Windows` directory.</span></span>

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

### <span data-ttu-id="d25e6-159">-Filter</span><span class="sxs-lookup"><span data-stu-id="d25e6-159">-Filter</span></span>

<span data-ttu-id="d25e6-160">Hiermee geeft u een filter op om de para meter **Path** te kwalificeren.</span><span class="sxs-lookup"><span data-stu-id="d25e6-160">Specifies a filter to qualify the **Path** parameter.</span></span> <span data-ttu-id="d25e6-161">De [File System](../Microsoft.PowerShell.Core/About/about_FileSystem_Provider.md) -provider is de enige geïnstalleerde Power shell-provider die het gebruik van filters ondersteunt.</span><span class="sxs-lookup"><span data-stu-id="d25e6-161">The [FileSystem](../Microsoft.PowerShell.Core/About/about_FileSystem_Provider.md) provider is the only installed PowerShell provider that supports the use of filters.</span></span> <span data-ttu-id="d25e6-162">U kunt de syntaxis voor de filter taal van het **Bestands systeem** in [about_Wildcards](../Microsoft.PowerShell.Core/About/about_Wildcards.md)vinden.</span><span class="sxs-lookup"><span data-stu-id="d25e6-162">You can find the syntax for the **FileSystem** filter language in [about_Wildcards](../Microsoft.PowerShell.Core/About/about_Wildcards.md).</span></span>
<span data-ttu-id="d25e6-163">Filters zijn efficiënter dan andere para meters, omdat deze door de provider worden toegepast wanneer de cmdlet de objecten ophaalt in plaats van dat Power shell de objecten heeft gefilterd nadat ze zijn opgehaald.</span><span class="sxs-lookup"><span data-stu-id="d25e6-163">Filters are more efficient than other parameters, because the provider applies them when the cmdlet gets the objects rather than having PowerShell filter the objects after they are retrieved.</span></span>

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

### <span data-ttu-id="d25e6-164">-Force</span><span class="sxs-lookup"><span data-stu-id="d25e6-164">-Force</span></span>

<span data-ttu-id="d25e6-165">Hiermee wordt de opdracht uitgevoerd zonder dat de gebruiker om bevestiging wordt gevraagd.</span><span class="sxs-lookup"><span data-stu-id="d25e6-165">Forces the command to run without asking for user confirmation.</span></span>
<span data-ttu-id="d25e6-166">De implementatie varieert van provider tot provider.</span><span class="sxs-lookup"><span data-stu-id="d25e6-166">Implementation varies from provider to provider.</span></span>
<span data-ttu-id="d25e6-167">Zie [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="d25e6-167">For more information, see [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md).</span></span>

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

### <span data-ttu-id="d25e6-168">-Include</span><span class="sxs-lookup"><span data-stu-id="d25e6-168">-Include</span></span>

<span data-ttu-id="d25e6-169">Hiermee wordt een teken reeks matrix opgegeven, een item of items die met deze cmdlet in de bewerking zijn opgenomen.</span><span class="sxs-lookup"><span data-stu-id="d25e6-169">Specifies, as a string array, an item or items that this cmdlet includes in the operation.</span></span> <span data-ttu-id="d25e6-170">De waarde van deze para meter komt in aanmerking voor de para meter **Path** .</span><span class="sxs-lookup"><span data-stu-id="d25e6-170">The value of this parameter qualifies the **Path** parameter.</span></span> <span data-ttu-id="d25e6-171">Voer een element of patroon van een pad in, zoals `"*.txt"` .</span><span class="sxs-lookup"><span data-stu-id="d25e6-171">Enter a path element or pattern, such as `"*.txt"`.</span></span> <span data-ttu-id="d25e6-172">Joker tekens zijn toegestaan.</span><span class="sxs-lookup"><span data-stu-id="d25e6-172">Wildcard characters are permitted.</span></span> <span data-ttu-id="d25e6-173">De para meter **include** is alleen effectief wanneer de inhoud van een item wordt opgenomen, zoals `C:\Windows\*` , waarbij het Joker teken de inhoud van de `C:\Windows` map bevat.</span><span class="sxs-lookup"><span data-stu-id="d25e6-173">The **Include** parameter is effective only when the command includes the contents of an item, such as `C:\Windows\*`, where the wildcard character specifies the contents of the `C:\Windows` directory.</span></span>

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

### <span data-ttu-id="d25e6-174">-LiteralPath</span><span class="sxs-lookup"><span data-stu-id="d25e6-174">-LiteralPath</span></span>

<span data-ttu-id="d25e6-175">Hiermee geeft u een pad naar een of meer locaties.</span><span class="sxs-lookup"><span data-stu-id="d25e6-175">Specifies a path to one or more locations.</span></span> <span data-ttu-id="d25e6-176">De waarde van **LiteralPath** wordt precies zo gebruikt als deze wordt getypt.</span><span class="sxs-lookup"><span data-stu-id="d25e6-176">The value of **LiteralPath** is used exactly as it is typed.</span></span> <span data-ttu-id="d25e6-177">Geen tekens worden geïnterpreteerd als joker tekens.</span><span class="sxs-lookup"><span data-stu-id="d25e6-177">No characters are interpreted as wildcards.</span></span> <span data-ttu-id="d25e6-178">Als het pad escape tekens bevat, plaatst u het tussen enkele aanhalings tekens.</span><span class="sxs-lookup"><span data-stu-id="d25e6-178">If the path includes escape characters, enclose it in single quotation marks.</span></span> <span data-ttu-id="d25e6-179">Enkele aanhalings tekens geven aan dat Power shell geen karakters interpreteert als escape reeksen.</span><span class="sxs-lookup"><span data-stu-id="d25e6-179">Single quotation marks tell PowerShell not to interpret any characters as escape sequences.</span></span>

<span data-ttu-id="d25e6-180">Zie [about_Quoting_Rules](../Microsoft.Powershell.Core/About/about_Quoting_Rules.md)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="d25e6-180">For more information, see [about_Quoting_Rules](../Microsoft.Powershell.Core/About/about_Quoting_Rules.md).</span></span>

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

### <span data-ttu-id="d25e6-181">-PassThru</span><span class="sxs-lookup"><span data-stu-id="d25e6-181">-PassThru</span></span>

<span data-ttu-id="d25e6-182">Retourneert een object dat het item vertegenwoordigt waarmee u werkt.</span><span class="sxs-lookup"><span data-stu-id="d25e6-182">Returns an object representing the item with which you are working.</span></span>
<span data-ttu-id="d25e6-183">Deze cmdlet genereert standaard geen uitvoer.</span><span class="sxs-lookup"><span data-stu-id="d25e6-183">By default, this cmdlet does not generate any output.</span></span>

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

### <span data-ttu-id="d25e6-184">-Path</span><span class="sxs-lookup"><span data-stu-id="d25e6-184">-Path</span></span>

<span data-ttu-id="d25e6-185">Hiermee geeft u het pad op naar de huidige locatie van de items.</span><span class="sxs-lookup"><span data-stu-id="d25e6-185">Specifies the path to the current location of the items.</span></span>
<span data-ttu-id="d25e6-186">De standaardwaarde is de huidige map.</span><span class="sxs-lookup"><span data-stu-id="d25e6-186">The default is the current directory.</span></span>
<span data-ttu-id="d25e6-187">Joker tekens zijn toegestaan.</span><span class="sxs-lookup"><span data-stu-id="d25e6-187">Wildcard characters are permitted.</span></span>

```yaml
Type: System.String[]
Parameter Sets: Path
Aliases:

Required: True
Position: 0
Default value: Current directory
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: True
```

### <span data-ttu-id="d25e6-188">-Confirm</span><span class="sxs-lookup"><span data-stu-id="d25e6-188">-Confirm</span></span>

<span data-ttu-id="d25e6-189">Hiermee wordt u gevraagd om bevestiging voordat u de cmdlet uitvoert.</span><span class="sxs-lookup"><span data-stu-id="d25e6-189">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="d25e6-190">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="d25e6-190">-WhatIf</span></span>

<span data-ttu-id="d25e6-191">Hiermee wordt weergegeven wat er zou gebeuren als u de cmdlet uitvoert.</span><span class="sxs-lookup"><span data-stu-id="d25e6-191">Shows what would happen if the cmdlet runs.</span></span>
<span data-ttu-id="d25e6-192">De cmdlet wordt niet uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="d25e6-192">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="d25e6-193">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="d25e6-193">CommonParameters</span></span>

<span data-ttu-id="d25e6-194">Deze cmdlet biedt ondersteuning voor de algemene para meters: `-Debug` , `-ErrorAction` , `-ErrorVariable` , `-InformationAction` , `-InformationVariable` , `-OutVariable` , `-OutBuffer` , `-PipelineVariable` , `-Verbose` , `-WarningAction` en `-WarningVariable` .</span><span class="sxs-lookup"><span data-stu-id="d25e6-194">This cmdlet supports the common parameters: `-Debug`, `-ErrorAction`, `-ErrorVariable`, `-InformationAction`, `-InformationVariable`, `-OutVariable`, `-OutBuffer`, `-PipelineVariable`, `-Verbose`, `-WarningAction`, and `-WarningVariable`.</span></span> <span data-ttu-id="d25e6-195">Zie [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="d25e6-195">For more information, see [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md).</span></span>

## <span data-ttu-id="d25e6-196">INVOER</span><span class="sxs-lookup"><span data-stu-id="d25e6-196">INPUTS</span></span>

### <span data-ttu-id="d25e6-197">System. String</span><span class="sxs-lookup"><span data-stu-id="d25e6-197">System.String</span></span>

<span data-ttu-id="d25e6-198">U kunt een teken reeks met een pad naar deze cmdlet door sluizen.</span><span class="sxs-lookup"><span data-stu-id="d25e6-198">You can pipe a string that contains a path to this cmdlet.</span></span>

## <span data-ttu-id="d25e6-199">UITVOER</span><span class="sxs-lookup"><span data-stu-id="d25e6-199">OUTPUTS</span></span>

### <span data-ttu-id="d25e6-200">Geen of een object dat het verplaatste item vertegenwoordigt</span><span class="sxs-lookup"><span data-stu-id="d25e6-200">None or an object representing the moved item</span></span>

<span data-ttu-id="d25e6-201">Wanneer u de para meter *PassThru* gebruikt, genereert deze cmdlet een object dat het verplaatste item vertegenwoordigt.</span><span class="sxs-lookup"><span data-stu-id="d25e6-201">When you use the *PassThru* parameter, this cmdlet generates an object representing the moved item.</span></span>
<span data-ttu-id="d25e6-202">Anders wordt met deze cmdlet geen uitvoer gegenereerd.</span><span class="sxs-lookup"><span data-stu-id="d25e6-202">Otherwise, this cmdlet does not generate any output.</span></span>

## <span data-ttu-id="d25e6-203">OPMERKINGEN</span><span class="sxs-lookup"><span data-stu-id="d25e6-203">NOTES</span></span>

- <span data-ttu-id="d25e6-204">Met deze cmdlet worden bestanden verplaatst tussen de stations die worden ondersteund door dezelfde provider, maar worden mappen alleen verplaatst binnen hetzelfde station.</span><span class="sxs-lookup"><span data-stu-id="d25e6-204">This cmdlet will move files between drives that are supported by the same provider, but it will move directories only within the same drive.</span></span>
- <span data-ttu-id="d25e6-205">Omdat een `Move-Item` opdracht de eigenschappen, inhoud en onderliggende items van een item verplaatst, zijn alle verplaatsingen standaard recursief.</span><span class="sxs-lookup"><span data-stu-id="d25e6-205">Because a `Move-Item` command moves the properties, contents, and child items of an item, all moves are recursive by default.</span></span>
- <span data-ttu-id="d25e6-206">Deze cmdlet is ontworpen om te werken met de gegevens die door elke provider worden weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="d25e6-206">This cmdlet is designed to work with the data exposed by any provider.</span></span>
  <span data-ttu-id="d25e6-207">Als u een lijst wilt weer geven van de providers die beschikbaar zijn in uw sessie, typt u `Get-PSProvider` .</span><span class="sxs-lookup"><span data-stu-id="d25e6-207">To list the providers available in your session, type `Get-PSProvider`.</span></span>
  <span data-ttu-id="d25e6-208">Zie [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="d25e6-208">For more information, see [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md).</span></span>

## <span data-ttu-id="d25e6-209">GERELATEERDE KOPPELINGEN</span><span class="sxs-lookup"><span data-stu-id="d25e6-209">RELATED LINKS</span></span>

[<span data-ttu-id="d25e6-210">Wissen-item</span><span class="sxs-lookup"><span data-stu-id="d25e6-210">Clear-Item</span></span>](Clear-Item.md)

[<span data-ttu-id="d25e6-211">Kopie-item</span><span class="sxs-lookup"><span data-stu-id="d25e6-211">Copy-Item</span></span>](Copy-Item.md)

[<span data-ttu-id="d25e6-212">Get-item</span><span class="sxs-lookup"><span data-stu-id="d25e6-212">Get-Item</span></span>](Get-Item.md)

[<span data-ttu-id="d25e6-213">Invoke-item</span><span class="sxs-lookup"><span data-stu-id="d25e6-213">Invoke-Item</span></span>](Invoke-Item.md)

[<span data-ttu-id="d25e6-214">Nieuw-item</span><span class="sxs-lookup"><span data-stu-id="d25e6-214">New-Item</span></span>](New-Item.md)

[<span data-ttu-id="d25e6-215">Verwijderen-item</span><span class="sxs-lookup"><span data-stu-id="d25e6-215">Remove-Item</span></span>](Remove-Item.md)

[<span data-ttu-id="d25e6-216">Naam wijzigen-item</span><span class="sxs-lookup"><span data-stu-id="d25e6-216">Rename-Item</span></span>](Rename-Item.md)

[<span data-ttu-id="d25e6-217">Set-item</span><span class="sxs-lookup"><span data-stu-id="d25e6-217">Set-Item</span></span>](Set-Item.md)

[<span data-ttu-id="d25e6-218">about_Providers</span><span class="sxs-lookup"><span data-stu-id="d25e6-218">about_Providers</span></span>](../Microsoft.PowerShell.Core/About/about_Providers.md)
