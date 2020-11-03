---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 10/18/2018
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/move-item?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Move-Item
ms.openlocfilehash: d3637825e7570e5fb0f3ff77efbc89e9d93974a3
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/07/2020
ms.locfileid: "93250600"
---
# <span data-ttu-id="75da3-103">Move-Item</span><span class="sxs-lookup"><span data-stu-id="75da3-103">Move-Item</span></span>

## <span data-ttu-id="75da3-104">SAMENVATTING</span><span class="sxs-lookup"><span data-stu-id="75da3-104">SYNOPSIS</span></span>
<span data-ttu-id="75da3-105">Hiermee verplaatst u een item van de ene locatie naar een andere.</span><span class="sxs-lookup"><span data-stu-id="75da3-105">Moves an item from one location to another.</span></span>

## <span data-ttu-id="75da3-106">SYNTAXIS</span><span class="sxs-lookup"><span data-stu-id="75da3-106">SYNTAX</span></span>

### <span data-ttu-id="75da3-107">Pad (standaard)</span><span class="sxs-lookup"><span data-stu-id="75da3-107">Path (Default)</span></span>

```
Move-Item [-Path] <String[]> [[-Destination] <String>] [-Force] [-Filter <String>] [-Include <String[]>]
 [-Exclude <String[]>] [-PassThru] [-Credential <PSCredential>] [-WhatIf] [-Confirm] [-UseTransaction]
 [<CommonParameters>]
```

### <span data-ttu-id="75da3-108">LiteralPath</span><span class="sxs-lookup"><span data-stu-id="75da3-108">LiteralPath</span></span>

```
Move-Item -LiteralPath <String[]> [[-Destination] <String>] [-Force] [-Filter <String>] [-Include <String[]>]
 [-Exclude <String[]>] [-PassThru] [-Credential <PSCredential>] [-WhatIf] [-Confirm] [-UseTransaction]
 [<CommonParameters>]
```

## <span data-ttu-id="75da3-109">BESCHRIJVING</span><span class="sxs-lookup"><span data-stu-id="75da3-109">DESCRIPTION</span></span>

<span data-ttu-id="75da3-110">`Move-Item`Met de cmdlet wordt een item, inclusief eigenschappen, inhoud en onderliggende items, verplaatst van de ene locatie naar een andere locatie.</span><span class="sxs-lookup"><span data-stu-id="75da3-110">The `Move-Item` cmdlet moves an item, including its properties, contents, and child items, from one location to another location.</span></span>
<span data-ttu-id="75da3-111">De locaties moeten door dezelfde provider worden ondersteund.</span><span class="sxs-lookup"><span data-stu-id="75da3-111">The locations must be supported by the same provider.</span></span>
<span data-ttu-id="75da3-112">Zo kunt u een bestand of submap van de ene map naar de andere verplaatsen of een registersubsleutel van de ene naar de andere sleutel verplaatsen.</span><span class="sxs-lookup"><span data-stu-id="75da3-112">For example, it can move a file or subdirectory from one directory to another or move a registry subkey from one key to another.</span></span>
<span data-ttu-id="75da3-113">Wanneer u een item verplaatst, wordt het toegevoegd aan de nieuwe locatie en verwijderd uit de oorspronkelijke locatie.</span><span class="sxs-lookup"><span data-stu-id="75da3-113">When you move an item, it is added to the new location and deleted from its original location.</span></span>

## <span data-ttu-id="75da3-114">VOORBEELDEN</span><span class="sxs-lookup"><span data-stu-id="75da3-114">EXAMPLES</span></span>

### <span data-ttu-id="75da3-115">Voor beeld 1: een bestand verplaatsen naar een andere map en de naam wijzigen</span><span class="sxs-lookup"><span data-stu-id="75da3-115">Example 1: Move a file to another directory and rename it</span></span>

<span data-ttu-id="75da3-116">Met deze opdracht wordt het ' Test.txt-bestand van het `C:` station verplaatst naar de map ' E:\Temp ' en wordt de naam gewijzigd van ' test.txt ' in ' tst.txt '.</span><span class="sxs-lookup"><span data-stu-id="75da3-116">This command moves the "Test.txt" file from the `C:` drive to the "E:\Temp" directory and renames it from "test.txt" to "tst.txt".</span></span>

```powershell
Move-Item -Path C:\test.txt -Destination E:\Temp\tst.txt
```

### <span data-ttu-id="75da3-117">Voor beeld 2: een map en de inhoud naar een andere map verplaatsen</span><span class="sxs-lookup"><span data-stu-id="75da3-117">Example 2: Move a directory and its contents to another directory</span></span>

<span data-ttu-id="75da3-118">Met deze opdracht verplaatst u de map ' C:\Temp ' en de inhoud ervan naar de map ' C:\Logs '.</span><span class="sxs-lookup"><span data-stu-id="75da3-118">This command moves the "C:\Temp" directory and its contents to the "C:\Logs" directory.</span></span>
<span data-ttu-id="75da3-119">De map Temp en alle bijbehorende submappen en bestanden, worden weer gegeven in de map logs.</span><span class="sxs-lookup"><span data-stu-id="75da3-119">The "Temp" directory, and all of its subdirectories and files, then appear in the "Logs" directory.</span></span>

```powershell
Move-Item -Path C:\Temp -Destination C:\Logs
```

### <span data-ttu-id="75da3-120">Voor beeld 3: alle bestanden van een opgegeven extensie verplaatsen van de huidige map naar een andere map</span><span class="sxs-lookup"><span data-stu-id="75da3-120">Example 3: Move all files of a specified extension from the current directory to another directory</span></span>

<span data-ttu-id="75da3-121">Met deze opdracht worden alle tekst bestanden (\*. txt) in de huidige map (aangeduid met een punt ('. ')) verplaatst naar de map ' C:\Logs '.</span><span class="sxs-lookup"><span data-stu-id="75da3-121">This command moves all of the text files ("\*.txt") in the current directory (represented by a dot ('.')) to the "C:\Logs" directory.</span></span>

```powershell
Move-Item -Path .\*.txt -Destination C:\Logs
```

### <span data-ttu-id="75da3-122">Voor beeld 4: alle bestanden van een opgegeven extensie recursief verplaatsen vanuit de huidige map naar een andere map</span><span class="sxs-lookup"><span data-stu-id="75da3-122">Example 4: Recursively move all files of a specified extension from the current directory to another directory</span></span>

<span data-ttu-id="75da3-123">Met deze opdracht worden alle tekst bestanden van de huidige map en alle submappen, recursief, naar de map C:\TextFiles verplaatst.</span><span class="sxs-lookup"><span data-stu-id="75da3-123">This command moves all of the text files from the current directory and all subdirectories, recursively, to the "C:\TextFiles" directory.</span></span>

<span data-ttu-id="75da3-124">De opdracht gebruikt de `Get-ChildItem` cmdlet om alle onderliggende items in de huidige map op te halen (vertegenwoordigd door de punt \[ \] ) en de bijbehorende submappen met de *bestandsnaam extensie. txt. Hierbij wordt gebruikgemaakt van de para meter **recursieve** om het ophalen van recursie en de para meter include te beperken tot het ophalen van '*. txt ' bestanden.</span><span class="sxs-lookup"><span data-stu-id="75da3-124">The command uses the `Get-ChildItem` cmdlet to get all of the child items in the current directory (represented by the dot \[.\]) and its subdirectories that have a " *.txt" file name extension. It uses the **Recurse** parameter to make the retrieval recursive and the Include parameter to limit the retrieval to "*.txt" files.</span></span>

<span data-ttu-id="75da3-125">De pijplijn operator ( `|` ) verzendt de resultaten van deze opdracht naar `Move-Item` , die de tekst bestanden verplaatst naar de map ' TextFiles '.</span><span class="sxs-lookup"><span data-stu-id="75da3-125">The pipeline operator (`|`) sends the results of this command to `Move-Item`, which moves the text files to the "TextFiles" directory.</span></span>

<span data-ttu-id="75da3-126">Als bestanden die worden verplaatst naar ' C:\Textfiles ' dezelfde naam hebben, `Move-Item` wordt er een fout weer gegeven en wordt de functie voortgezet, maar wordt slechts één bestand met elke naam verplaatst naar ' C:\Textfiles '.</span><span class="sxs-lookup"><span data-stu-id="75da3-126">If files that are to be moved to "C:\Textfiles" have the same name, `Move-Item` displays an error and continues, but it moves only one file with each name to "C:\Textfiles".</span></span>
<span data-ttu-id="75da3-127">De andere bestanden blijven in de oorspronkelijke mappen staan.</span><span class="sxs-lookup"><span data-stu-id="75da3-127">The other files remain in their original directories.</span></span>

<span data-ttu-id="75da3-128">Als de map ' textfiles ' (of een ander element van het doelpad) niet bestaat, mislukt de opdracht.</span><span class="sxs-lookup"><span data-stu-id="75da3-128">If the "Textfiles" directory (or any other element of the destination path) does not exist, the command fails.</span></span>
<span data-ttu-id="75da3-129">De ontbrekende map wordt niet voor u gemaakt, zelfs niet als u de para meter **Forces** gebruikt.</span><span class="sxs-lookup"><span data-stu-id="75da3-129">The missing directory is not created for you, even if you use the **Force** parameter.</span></span>
<span data-ttu-id="75da3-130">`Move-Item` Hiermee wordt het eerste item verplaatst naar een bestand met de naam ' textfiles ' en wordt er een fout weer gegeven waarin wordt uitgelegd dat het bestand al bestaat.</span><span class="sxs-lookup"><span data-stu-id="75da3-130">`Move-Item` moves the first item to a file called "Textfiles" and then displays an error explaining that the file already exists.</span></span>

<span data-ttu-id="75da3-131">Ook worden `Get-ChildItem` verborgen bestanden standaard niet verplaatst.</span><span class="sxs-lookup"><span data-stu-id="75da3-131">Also, by default, `Get-ChildItem` does not move hidden files.</span></span>
<span data-ttu-id="75da3-132">Als u verborgen bestanden wilt verplaatsen, gebruikt u de para meter **Force** with `Get-ChildItem` .</span><span class="sxs-lookup"><span data-stu-id="75da3-132">To move hidden files, use the **Force** parameter with `Get-ChildItem`.</span></span>

<span data-ttu-id="75da3-133">Opmerking: in Windows Power Shell 2,0, wanneer u de **recursieve** para meter van de `Get-ChildItem` cmdlet gebruikt, moet de waarde van de para meter **Path** een container zijn.</span><span class="sxs-lookup"><span data-stu-id="75da3-133">Note: In Windows PowerShell 2.0, when using the **Recurse** parameter of the `Get-ChildItem` cmdlet, the value of the **Path** parameter must be a container.</span></span>
<span data-ttu-id="75da3-134">Gebruik de para meter **include** om het txt-bestand met de extensie filter () op te geven `Get-ChildItem -Path .\* -Include *.txt -Recurse | Move-Item -Destination C:\TextFiles` .</span><span class="sxs-lookup"><span data-stu-id="75da3-134">Use the **Include** parameter to specify the .txt file name extension filter (`Get-ChildItem -Path .\* -Include *.txt -Recurse | Move-Item -Destination C:\TextFiles`).</span></span>

```powershell
Get-ChildItem -Path ".\*.txt" -Recurse | Move-Item -Destination "C:\TextFiles"
```

### <span data-ttu-id="75da3-135">Voor beeld 5: register sleutels en-waarden naar een andere sleutel verplaatsen</span><span class="sxs-lookup"><span data-stu-id="75da3-135">Example 5: Move registry keys and values to another key</span></span>

<span data-ttu-id="75da3-136">Met deze opdracht worden de register sleutels en-waarden in de register sleutel "mijn bedrijf" in "HKLM\Software" verplaatst naar de sleutel "MyNewCompany".</span><span class="sxs-lookup"><span data-stu-id="75da3-136">This command moves the registry keys and values within the "MyCompany" registry key in "HKLM\Software" to the "MyNewCompany" key.</span></span>
<span data-ttu-id="75da3-137">Het Joker teken (' \* ') geeft aan dat de inhoud van de sleutel ' mijn bedrijf ' moet worden verplaatst, niet de sleutel zelf.</span><span class="sxs-lookup"><span data-stu-id="75da3-137">The wildcard character ('\*') indicates that the contents of the "MyCompany" key should be moved, not the key itself.</span></span>
<span data-ttu-id="75da3-138">In deze opdracht worden de namen van de optionele **paden** en **doel** parameters wegge laten.</span><span class="sxs-lookup"><span data-stu-id="75da3-138">In this command, the optional **Path** and **Destination** parameter names are omitted.</span></span>

```powershell
Move-Item "HKLM:\software\mycompany\*" "HKLM:\software\mynewcompany"
```

### <span data-ttu-id="75da3-139">Voor beeld 6: een map en de inhoud ervan verplaatsen naar een submap van de opgegeven map</span><span class="sxs-lookup"><span data-stu-id="75da3-139">Example 6: Move a directory and its contents to a subdirectory of the specified directory</span></span>

<span data-ttu-id="75da3-140">Met deze opdracht wordt de map ' logs \[ Sept \` 06 \] ' (en de inhoud ervan) verplaatst naar de map ' logs \[ 2006 \] '.</span><span class="sxs-lookup"><span data-stu-id="75da3-140">This command moves the "Logs\[Sept\`06\]" directory (and its contents) into the "Logs\[2006\]" directory.</span></span>

<span data-ttu-id="75da3-141">De para meter **LiteralPath** wordt gebruikt in plaats van het **pad** , omdat de naam van de oorspronkelijke map links van het haakje en rechter vier Kante tekens (" \[ " en " \] ") bevat.</span><span class="sxs-lookup"><span data-stu-id="75da3-141">The **LiteralPath** parameter is used instead of **Path** , because the original directory name includes left bracket and right bracket characters ("\[" and "\]").</span></span>
<span data-ttu-id="75da3-142">Het pad bevindt zich ook tussen enkele aanhalings tekens (' '), zodat het apostroffen-symbool ( \` ) niet wordt geïnterpreteerd.</span><span class="sxs-lookup"><span data-stu-id="75da3-142">The path is also enclosed in single quotation marks (' '), so that the backtick symbol (\`) is not misinterpreted.</span></span>

<span data-ttu-id="75da3-143">Voor de para meter **Destination** is geen letterlijk pad vereist, omdat de doel variabele ook tussen enkele aanhalings tekens moet worden geplaatst, omdat deze haakjes bevat die kunnen worden geïnterpreteerd.</span><span class="sxs-lookup"><span data-stu-id="75da3-143">The **Destination** parameter does not require a literal path, because the Destination variable also must be enclosed in single quotation marks, because it includes brackets that can be misinterpreted.</span></span>

```powershell
Move-Item -LiteralPath 'Logs[Sept`06]' -Destination 'Logs[2006]'
```

## <span data-ttu-id="75da3-144">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="75da3-144">PARAMETERS</span></span>

### <span data-ttu-id="75da3-145">-Credential</span><span class="sxs-lookup"><span data-stu-id="75da3-145">-Credential</span></span>

> [!NOTE]
> <span data-ttu-id="75da3-146">Deze para meter wordt niet ondersteund door providers die zijn geïnstalleerd met Power shell.</span><span class="sxs-lookup"><span data-stu-id="75da3-146">This parameter is not supported by any providers installed with PowerShell.</span></span>
> <span data-ttu-id="75da3-147">Gebruik [invoke-Command](../Microsoft.PowerShell.Core/Invoke-Command.md)om een andere gebruiker te imiteren of uw referenties te verhogen wanneer u deze cmdlet uitvoert.</span><span class="sxs-lookup"><span data-stu-id="75da3-147">To impersonate another user, or elevate your credentials when running this cmdlet, use [Invoke-Command](../Microsoft.PowerShell.Core/Invoke-Command.md).</span></span>

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

### <span data-ttu-id="75da3-148">-Bestemming</span><span class="sxs-lookup"><span data-stu-id="75da3-148">-Destination</span></span>

<span data-ttu-id="75da3-149">Hiermee geeft u het pad op naar de locatie waar de items worden verplaatst.</span><span class="sxs-lookup"><span data-stu-id="75da3-149">Specifies the path to the location where the items are being moved.</span></span>
<span data-ttu-id="75da3-150">De standaardwaarde is de huidige map.</span><span class="sxs-lookup"><span data-stu-id="75da3-150">The default is the current directory.</span></span>
<span data-ttu-id="75da3-151">Joker tekens zijn toegestaan, maar in het resultaat moet één locatie worden opgegeven.</span><span class="sxs-lookup"><span data-stu-id="75da3-151">Wildcards are permitted, but the result must specify a single location.</span></span>

<span data-ttu-id="75da3-152">Als u de naam van het item dat wordt verplaatst, wilt wijzigen, geeft u een nieuwe naam op in de waarde van de para meter **Destination** .</span><span class="sxs-lookup"><span data-stu-id="75da3-152">To rename the item being moved, specify a new name in the value of the **Destination** parameter.</span></span>

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

### <span data-ttu-id="75da3-153">-Uitsluiten</span><span class="sxs-lookup"><span data-stu-id="75da3-153">-Exclude</span></span>

<span data-ttu-id="75da3-154">Hiermee geeft u als een teken reeks matrix een item of items die met deze cmdlet worden uitgesloten van de bewerking.</span><span class="sxs-lookup"><span data-stu-id="75da3-154">Specifies, as a string array, an item or items that this cmdlet excludes from the operation.</span></span>
<span data-ttu-id="75da3-155">De waarde van deze para meter komt in aanmerking voor de para meter **Path** .</span><span class="sxs-lookup"><span data-stu-id="75da3-155">The value of this parameter qualifies the **Path** parameter.</span></span>
<span data-ttu-id="75da3-156">Voer een element of patroon van een pad in, zoals \*. txt.</span><span class="sxs-lookup"><span data-stu-id="75da3-156">Enter a path element or pattern, such as "\*.txt".</span></span>
<span data-ttu-id="75da3-157">Joker tekens zijn toegestaan.</span><span class="sxs-lookup"><span data-stu-id="75da3-157">Wildcard characters are permitted.</span></span>

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

### <span data-ttu-id="75da3-158">-Filter</span><span class="sxs-lookup"><span data-stu-id="75da3-158">-Filter</span></span>

<span data-ttu-id="75da3-159">Hiermee geeft u een filter op in de indeling of taal van de provider.</span><span class="sxs-lookup"><span data-stu-id="75da3-159">Specifies a filter in the format or language of the provider.</span></span>
<span data-ttu-id="75da3-160">De waarde van deze para meter komt in aanmerking voor de para meter **Path** .</span><span class="sxs-lookup"><span data-stu-id="75da3-160">The value of this parameter qualifies the **Path** parameter.</span></span>

<span data-ttu-id="75da3-161">De syntaxis van het filter, inclusief het gebruik van joker tekens, is afhankelijk van de provider.</span><span class="sxs-lookup"><span data-stu-id="75da3-161">The syntax of the filter, including the use of wildcard characters, depends on the provider.</span></span>
<span data-ttu-id="75da3-162">Filters zijn efficiënter dan andere para meters, omdat deze door de provider worden toegepast wanneer de cmdlet de objecten ophaalt in plaats van dat Power shell de objecten heeft gefilterd nadat ze zijn opgehaald.</span><span class="sxs-lookup"><span data-stu-id="75da3-162">Filters are more efficient than other parameters, because the provider applies them when the cmdlet gets the objects rather than having PowerShell filter the objects after they are retrieved.</span></span>

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

### <span data-ttu-id="75da3-163">-Force</span><span class="sxs-lookup"><span data-stu-id="75da3-163">-Force</span></span>

<span data-ttu-id="75da3-164">Hiermee wordt de opdracht uitgevoerd zonder dat de gebruiker om bevestiging wordt gevraagd.</span><span class="sxs-lookup"><span data-stu-id="75da3-164">Forces the command to run without asking for user confirmation.</span></span>
<span data-ttu-id="75da3-165">De implementatie varieert van provider tot provider.</span><span class="sxs-lookup"><span data-stu-id="75da3-165">Implementation varies from provider to provider.</span></span>
<span data-ttu-id="75da3-166">Zie [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="75da3-166">For more information, see [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md).</span></span>

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

### <span data-ttu-id="75da3-167">-Include</span><span class="sxs-lookup"><span data-stu-id="75da3-167">-Include</span></span>

<span data-ttu-id="75da3-168">Hiermee geeft u als een teken reeks matrix een item of items die met deze cmdlet worden verplaatst in de bewerking.</span><span class="sxs-lookup"><span data-stu-id="75da3-168">Specifies, as a string array, an item or items that this cmdlet moves in the operation.</span></span>
<span data-ttu-id="75da3-169">De waarde van deze para meter komt in aanmerking voor de para meter **Path** .</span><span class="sxs-lookup"><span data-stu-id="75da3-169">The value of this parameter qualifies the **Path** parameter.</span></span>
<span data-ttu-id="75da3-170">Voer een element of patroon van een pad in, zoals \*. txt.</span><span class="sxs-lookup"><span data-stu-id="75da3-170">Enter a path element or pattern, such as "\*.txt".</span></span>
<span data-ttu-id="75da3-171">Joker tekens zijn toegestaan.</span><span class="sxs-lookup"><span data-stu-id="75da3-171">Wildcard characters are permitted.</span></span>

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

### <span data-ttu-id="75da3-172">-LiteralPath</span><span class="sxs-lookup"><span data-stu-id="75da3-172">-LiteralPath</span></span>

<span data-ttu-id="75da3-173">Hiermee geeft u het pad op naar de huidige locatie van de items.</span><span class="sxs-lookup"><span data-stu-id="75da3-173">Specifies the path to the current location of the items.</span></span>
<span data-ttu-id="75da3-174">In tegens telling tot de para meter **Path** wordt de waarde van **LiteralPath** precies zo gebruikt als deze wordt getypt.</span><span class="sxs-lookup"><span data-stu-id="75da3-174">Unlike the **Path** parameter, the value of **LiteralPath** is used exactly as it is typed.</span></span>
<span data-ttu-id="75da3-175">Geen tekens worden geïnterpreteerd als joker tekens.</span><span class="sxs-lookup"><span data-stu-id="75da3-175">No characters are interpreted as wildcards.</span></span>
<span data-ttu-id="75da3-176">Als het pad escape tekens bevat, plaatst u het tussen enkele aanhalings tekens.</span><span class="sxs-lookup"><span data-stu-id="75da3-176">If the path includes escape characters, enclose it in single quotation marks.</span></span>
<span data-ttu-id="75da3-177">Enkele aanhalings tekens geven aan dat Power shell geen karakters interpreteert als escape reeksen.</span><span class="sxs-lookup"><span data-stu-id="75da3-177">Single quotation marks tell PowerShell not to interpret any characters as escape sequences.</span></span>

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

### <span data-ttu-id="75da3-178">-PassThru</span><span class="sxs-lookup"><span data-stu-id="75da3-178">-PassThru</span></span>

<span data-ttu-id="75da3-179">Retourneert een object dat het item vertegenwoordigt waarmee u werkt.</span><span class="sxs-lookup"><span data-stu-id="75da3-179">Returns an object representing the item with which you are working.</span></span>
<span data-ttu-id="75da3-180">Deze cmdlet genereert standaard geen uitvoer.</span><span class="sxs-lookup"><span data-stu-id="75da3-180">By default, this cmdlet does not generate any output.</span></span>

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

### <span data-ttu-id="75da3-181">-Path</span><span class="sxs-lookup"><span data-stu-id="75da3-181">-Path</span></span>

<span data-ttu-id="75da3-182">Hiermee geeft u het pad op naar de huidige locatie van de items.</span><span class="sxs-lookup"><span data-stu-id="75da3-182">Specifies the path to the current location of the items.</span></span>
<span data-ttu-id="75da3-183">De standaardwaarde is de huidige map.</span><span class="sxs-lookup"><span data-stu-id="75da3-183">The default is the current directory.</span></span>
<span data-ttu-id="75da3-184">Joker tekens zijn toegestaan.</span><span class="sxs-lookup"><span data-stu-id="75da3-184">Wildcard characters are permitted.</span></span>

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

### <span data-ttu-id="75da3-185">-UseTransaction</span><span class="sxs-lookup"><span data-stu-id="75da3-185">-UseTransaction</span></span>

<span data-ttu-id="75da3-186">Hiermee wordt de opdracht opgenomen in de actieve transactie.</span><span class="sxs-lookup"><span data-stu-id="75da3-186">Includes the command in the active transaction.</span></span>
<span data-ttu-id="75da3-187">Deze parameter is alleen geldig wanneer een transactie wordt uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="75da3-187">This parameter is valid only when a transaction is in progress.</span></span>
<span data-ttu-id="75da3-188">Zie about_Transactions voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="75da3-188">For more information, see about_Transactions.</span></span>

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

### <span data-ttu-id="75da3-189">-Confirm</span><span class="sxs-lookup"><span data-stu-id="75da3-189">-Confirm</span></span>

<span data-ttu-id="75da3-190">Hiermee wordt u gevraagd om bevestiging voordat u de cmdlet uitvoert.</span><span class="sxs-lookup"><span data-stu-id="75da3-190">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="75da3-191">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="75da3-191">-WhatIf</span></span>

<span data-ttu-id="75da3-192">Hiermee wordt weergegeven wat er zou gebeuren als u de cmdlet uitvoert.</span><span class="sxs-lookup"><span data-stu-id="75da3-192">Shows what would happen if the cmdlet runs.</span></span>
<span data-ttu-id="75da3-193">De cmdlet wordt niet uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="75da3-193">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="75da3-194">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="75da3-194">CommonParameters</span></span>

<span data-ttu-id="75da3-195">Deze cmdlet biedt ondersteuning voor de algemene para meters: `-Debug` , `-ErrorAction` , `-ErrorVariable` , `-InformationAction` , `-InformationVariable` , `-OutVariable` , `-OutBuffer` , `-PipelineVariable` , `-Verbose` , `-WarningAction` en `-WarningVariable` .</span><span class="sxs-lookup"><span data-stu-id="75da3-195">This cmdlet supports the common parameters: `-Debug`, `-ErrorAction`, `-ErrorVariable`, `-InformationAction`, `-InformationVariable`, `-OutVariable`, `-OutBuffer`, `-PipelineVariable`, `-Verbose`, `-WarningAction`, and `-WarningVariable`.</span></span> <span data-ttu-id="75da3-196">Zie [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="75da3-196">For more information, see [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md).</span></span>

## <span data-ttu-id="75da3-197">INVOER</span><span class="sxs-lookup"><span data-stu-id="75da3-197">INPUTS</span></span>

### <span data-ttu-id="75da3-198">System. String</span><span class="sxs-lookup"><span data-stu-id="75da3-198">System.String</span></span>

<span data-ttu-id="75da3-199">U kunt een teken reeks met een pad naar deze cmdlet door sluizen.</span><span class="sxs-lookup"><span data-stu-id="75da3-199">You can pipe a string that contains a path to this cmdlet.</span></span>

## <span data-ttu-id="75da3-200">UITVOER</span><span class="sxs-lookup"><span data-stu-id="75da3-200">OUTPUTS</span></span>

### <span data-ttu-id="75da3-201">Geen of een object dat het verplaatste item vertegenwoordigt.</span><span class="sxs-lookup"><span data-stu-id="75da3-201">None or an object representing the moved item.</span></span>

<span data-ttu-id="75da3-202">Wanneer u de para meter *PassThru* gebruikt, genereert deze cmdlet een object dat het verplaatste item vertegenwoordigt.</span><span class="sxs-lookup"><span data-stu-id="75da3-202">When you use the *PassThru* parameter, this cmdlet generates an object representing the moved item.</span></span>
<span data-ttu-id="75da3-203">Anders wordt met deze cmdlet geen uitvoer gegenereerd.</span><span class="sxs-lookup"><span data-stu-id="75da3-203">Otherwise, this cmdlet does not generate any output.</span></span>

## <span data-ttu-id="75da3-204">OPMERKINGEN</span><span class="sxs-lookup"><span data-stu-id="75da3-204">NOTES</span></span>

<span data-ttu-id="75da3-205">Met deze cmdlet worden bestanden verplaatst tussen de stations die worden ondersteund door dezelfde provider, maar worden mappen alleen verplaatst binnen hetzelfde station.</span><span class="sxs-lookup"><span data-stu-id="75da3-205">This cmdlet will move files between drives that are supported by the same provider, but it will move directories only within the same drive.</span></span>

<span data-ttu-id="75da3-206">Omdat een `Move-Item` opdracht de eigenschappen, inhoud en onderliggende items van een item verplaatst, zijn alle verplaatsingen standaard recursief.</span><span class="sxs-lookup"><span data-stu-id="75da3-206">Because a `Move-Item` command moves the properties, contents, and child items of an item, all moves are recursive by default.</span></span>

<span data-ttu-id="75da3-207">Deze cmdlet is ontworpen om te werken met de gegevens die door elke provider worden weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="75da3-207">This cmdlet is designed to work with the data exposed by any provider.</span></span>
<span data-ttu-id="75da3-208">Als u een lijst wilt weer geven van de providers die beschikbaar zijn in uw sessie, typt u `Get-PSProvider` .</span><span class="sxs-lookup"><span data-stu-id="75da3-208">To list the providers available in your session, type `Get-PSProvider`.</span></span>
<span data-ttu-id="75da3-209">Zie [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="75da3-209">For more information, see [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md).</span></span>

## <span data-ttu-id="75da3-210">GERELATEERDE KOPPELINGEN</span><span class="sxs-lookup"><span data-stu-id="75da3-210">RELATED LINKS</span></span>

[<span data-ttu-id="75da3-211">Wissen-item</span><span class="sxs-lookup"><span data-stu-id="75da3-211">Clear-Item</span></span>](Clear-Item.md)

[<span data-ttu-id="75da3-212">Kopie-item</span><span class="sxs-lookup"><span data-stu-id="75da3-212">Copy-Item</span></span>](Copy-Item.md)

[<span data-ttu-id="75da3-213">Get-item</span><span class="sxs-lookup"><span data-stu-id="75da3-213">Get-Item</span></span>](Get-Item.md)

[<span data-ttu-id="75da3-214">Invoke-item</span><span class="sxs-lookup"><span data-stu-id="75da3-214">Invoke-Item</span></span>](Invoke-Item.md)

[<span data-ttu-id="75da3-215">Nieuw-item</span><span class="sxs-lookup"><span data-stu-id="75da3-215">New-Item</span></span>](New-Item.md)

[<span data-ttu-id="75da3-216">Verwijderen-item</span><span class="sxs-lookup"><span data-stu-id="75da3-216">Remove-Item</span></span>](Remove-Item.md)

[<span data-ttu-id="75da3-217">Naam wijzigen-item</span><span class="sxs-lookup"><span data-stu-id="75da3-217">Rename-Item</span></span>](Rename-Item.md)

[<span data-ttu-id="75da3-218">Set-item</span><span class="sxs-lookup"><span data-stu-id="75da3-218">Set-Item</span></span>](Set-Item.md)

[<span data-ttu-id="75da3-219">about_Providers</span><span class="sxs-lookup"><span data-stu-id="75da3-219">about_Providers</span></span>](../Microsoft.PowerShell.Core/About/about_Providers.md)
