---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 05/14/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/move-item?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Move-Item
ms.openlocfilehash: a47c017371fe5fe87618c11551cd1ecba76d5c60
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 11/17/2020
ms.locfileid: "94706041"
---
# <span data-ttu-id="6d771-102">Move-Item</span><span class="sxs-lookup"><span data-stu-id="6d771-102">Move-Item</span></span>

## <span data-ttu-id="6d771-103">SAMENVATTING</span><span class="sxs-lookup"><span data-stu-id="6d771-103">SYNOPSIS</span></span>
<span data-ttu-id="6d771-104">Hiermee verplaatst u een item van de ene locatie naar een andere.</span><span class="sxs-lookup"><span data-stu-id="6d771-104">Moves an item from one location to another.</span></span>

## <span data-ttu-id="6d771-105">SYNTAXIS</span><span class="sxs-lookup"><span data-stu-id="6d771-105">SYNTAX</span></span>

### <span data-ttu-id="6d771-106">Pad (standaard)</span><span class="sxs-lookup"><span data-stu-id="6d771-106">Path (Default)</span></span>

```
Move-Item [-Path] <String[]> [[-Destination] <String>] [-Force] [-Filter <String>] [-Include <String[]>]
 [-Exclude <String[]>] [-PassThru] [-Credential <PSCredential>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="6d771-107">LiteralPath</span><span class="sxs-lookup"><span data-stu-id="6d771-107">LiteralPath</span></span>

```
Move-Item -LiteralPath <String[]> [[-Destination] <String>] [-Force] [-Filter <String>] [-Include <String[]>]
 [-Exclude <String[]>] [-PassThru] [-Credential <PSCredential>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="6d771-108">BESCHRIJVING</span><span class="sxs-lookup"><span data-stu-id="6d771-108">DESCRIPTION</span></span>

<span data-ttu-id="6d771-109">`Move-Item`Met de cmdlet wordt een item, inclusief eigenschappen, inhoud en onderliggende items, verplaatst van de ene locatie naar een andere locatie.</span><span class="sxs-lookup"><span data-stu-id="6d771-109">The `Move-Item` cmdlet moves an item, including its properties, contents, and child items, from one location to another location.</span></span> <span data-ttu-id="6d771-110">De locaties moeten door dezelfde provider worden ondersteund.</span><span class="sxs-lookup"><span data-stu-id="6d771-110">The locations must be supported by the same provider.</span></span>
<span data-ttu-id="6d771-111">Zo kunt u een bestand of submap van de ene map naar de andere verplaatsen of een registersubsleutel van de ene naar de andere sleutel verplaatsen.</span><span class="sxs-lookup"><span data-stu-id="6d771-111">For example, it can move a file or subdirectory from one directory to another or move a registry subkey from one key to another.</span></span>
<span data-ttu-id="6d771-112">Wanneer u een item verplaatst, wordt het toegevoegd aan de nieuwe locatie en verwijderd uit de oorspronkelijke locatie.</span><span class="sxs-lookup"><span data-stu-id="6d771-112">When you move an item, it is added to the new location and deleted from its original location.</span></span>

## <span data-ttu-id="6d771-113">VOORBEELDEN</span><span class="sxs-lookup"><span data-stu-id="6d771-113">EXAMPLES</span></span>

### <span data-ttu-id="6d771-114">Voor beeld 1: een bestand verplaatsen naar een andere map en de naam wijzigen</span><span class="sxs-lookup"><span data-stu-id="6d771-114">Example 1: Move a file to another directory and rename it</span></span>

<span data-ttu-id="6d771-115">Met deze opdracht `Test.txt` wordt het bestand van het `C:` station verplaatst naar de `E:\Temp` map en wordt de naam gewijzigd van `test.txt` in `tst.txt` .</span><span class="sxs-lookup"><span data-stu-id="6d771-115">This command moves the `Test.txt` file from the `C:` drive to the `E:\Temp` directory and renames it from `test.txt` to `tst.txt`.</span></span>

```powershell
Move-Item -Path C:\test.txt -Destination E:\Temp\tst.txt
```

### <span data-ttu-id="6d771-116">Voor beeld 2: een map en de inhoud naar een andere map verplaatsen</span><span class="sxs-lookup"><span data-stu-id="6d771-116">Example 2: Move a directory and its contents to another directory</span></span>

<span data-ttu-id="6d771-117">Met deze opdracht verplaatst `C:\Temp` u de map en de inhoud ervan naar de `C:\Logs` map.</span><span class="sxs-lookup"><span data-stu-id="6d771-117">This command moves the `C:\Temp` directory and its contents to the `C:\Logs` directory.</span></span>
<span data-ttu-id="6d771-118">De map Temp en alle bijbehorende submappen en bestanden, worden weer gegeven in de map logs.</span><span class="sxs-lookup"><span data-stu-id="6d771-118">The "Temp" directory, and all of its subdirectories and files, then appear in the "Logs" directory.</span></span>

```powershell
Move-Item -Path C:\Temp -Destination C:\Logs
```

### <span data-ttu-id="6d771-119">Voor beeld 3: alle bestanden van een opgegeven extensie verplaatsen van de huidige map naar een andere map</span><span class="sxs-lookup"><span data-stu-id="6d771-119">Example 3: Move all files of a specified extension from the current directory to another directory</span></span>

<span data-ttu-id="6d771-120">Met deze opdracht worden alle tekst bestanden ( `*.txt` ) in de huidige map (aangeduid door een punt ( `.` )) naar de `C:\Logs` map verplaatst.</span><span class="sxs-lookup"><span data-stu-id="6d771-120">This command moves all of the text files (`*.txt`) in the current directory (represented by a dot (`.`)) to the `C:\Logs` directory.</span></span>

```powershell
Move-Item -Path .\*.txt -Destination C:\Logs
```

### <span data-ttu-id="6d771-121">Voor beeld 4: alle bestanden van een opgegeven extensie recursief verplaatsen vanuit de huidige map naar een andere map</span><span class="sxs-lookup"><span data-stu-id="6d771-121">Example 4: Recursively move all files of a specified extension from the current directory to another directory</span></span>

<span data-ttu-id="6d771-122">Met deze opdracht worden alle tekst bestanden van de huidige map en alle submappen, recursief, naar de map C:\TextFiles verplaatst.</span><span class="sxs-lookup"><span data-stu-id="6d771-122">This command moves all of the text files from the current directory and all subdirectories, recursively, to the "C:\TextFiles" directory.</span></span>

```powershell
Get-ChildItem -Path ".\*.txt" -Recurse | Move-Item -Destination "C:\TextFiles"
```

<span data-ttu-id="6d771-123">De opdracht gebruikt de `Get-ChildItem` cmdlet om alle onderliggende items in de huidige map op te halen (vertegenwoordigd door de punt \[ \] ) en de bijbehorende submappen met de *bestandsnaam extensie. txt. Hierbij wordt gebruikgemaakt van de para meter **recursieve** om het ophalen van recursie en de para meter include te beperken tot het ophalen van '*. txt ' bestanden.</span><span class="sxs-lookup"><span data-stu-id="6d771-123">The command uses the `Get-ChildItem` cmdlet to get all of the child items in the current directory (represented by the dot \[.\]) and its subdirectories that have a "*.txt" file name extension. It uses the **Recurse** parameter to make the retrieval recursive and the Include parameter to limit the retrieval to "*.txt" files.</span></span>

<span data-ttu-id="6d771-124">De pijplijn operator ( `|` ) verzendt de resultaten van deze opdracht naar `Move-Item` , die de tekst bestanden verplaatst naar de map ' TextFiles '.</span><span class="sxs-lookup"><span data-stu-id="6d771-124">The pipeline operator (`|`) sends the results of this command to `Move-Item`, which moves the text files to the "TextFiles" directory.</span></span>

<span data-ttu-id="6d771-125">Als bestanden die worden verplaatst naar ' C:\Textfiles ' dezelfde naam hebben, `Move-Item` wordt er een fout weer gegeven en wordt de functie voortgezet, maar wordt slechts één bestand met elke naam verplaatst naar ' C:\Textfiles '.</span><span class="sxs-lookup"><span data-stu-id="6d771-125">If files that are to be moved to "C:\Textfiles" have the same name, `Move-Item` displays an error and continues, but it moves only one file with each name to "C:\Textfiles".</span></span>
<span data-ttu-id="6d771-126">De andere bestanden blijven in de oorspronkelijke mappen staan.</span><span class="sxs-lookup"><span data-stu-id="6d771-126">The other files remain in their original directories.</span></span>

<span data-ttu-id="6d771-127">Als de map ' textfiles ' (of een ander element van het doelpad) niet bestaat, mislukt de opdracht.</span><span class="sxs-lookup"><span data-stu-id="6d771-127">If the "Textfiles" directory (or any other element of the destination path) does not exist, the command fails.</span></span>
<span data-ttu-id="6d771-128">De ontbrekende map wordt niet voor u gemaakt, zelfs niet als u de para meter **Forces** gebruikt.</span><span class="sxs-lookup"><span data-stu-id="6d771-128">The missing directory is not created for you, even if you use the **Force** parameter.</span></span>
<span data-ttu-id="6d771-129">`Move-Item` Hiermee wordt het eerste item verplaatst naar een bestand met de naam ' textfiles ' en wordt er een fout weer gegeven waarin wordt uitgelegd dat het bestand al bestaat.</span><span class="sxs-lookup"><span data-stu-id="6d771-129">`Move-Item` moves the first item to a file called "Textfiles" and then displays an error explaining that the file already exists.</span></span>

<span data-ttu-id="6d771-130">Ook worden `Get-ChildItem` verborgen bestanden standaard niet verplaatst.</span><span class="sxs-lookup"><span data-stu-id="6d771-130">Also, by default, `Get-ChildItem` does not move hidden files.</span></span>
<span data-ttu-id="6d771-131">Als u verborgen bestanden wilt verplaatsen, gebruikt u de para meter **Force** with `Get-ChildItem` .</span><span class="sxs-lookup"><span data-stu-id="6d771-131">To move hidden files, use the **Force** parameter with `Get-ChildItem`.</span></span>

> [!NOTE]
> <span data-ttu-id="6d771-132">Bij het gebruik van de **recursieve** para meter van de cmdlet in Windows power Shell 2,0 `Get-ChildItem` moet de waarde van de para meter **Path** een container zijn.</span><span class="sxs-lookup"><span data-stu-id="6d771-132">In Windows PowerShell 2.0, when using the **Recurse** parameter of the `Get-ChildItem` cmdlet, the value of the **Path** parameter must be a container.</span></span>
> <span data-ttu-id="6d771-133">Gebruik de para meter **include** om het txt-bestand met de extensie filter () op te geven `Get-ChildItem -Path .\* -Include *.txt -Recurse | Move-Item -Destination C:\TextFiles` .</span><span class="sxs-lookup"><span data-stu-id="6d771-133">Use the **Include** parameter to specify the .txt file name extension filter (`Get-ChildItem -Path .\* -Include *.txt -Recurse | Move-Item -Destination C:\TextFiles`).</span></span>

### <span data-ttu-id="6d771-134">Voor beeld 5: register sleutels en-waarden naar een andere sleutel verplaatsen</span><span class="sxs-lookup"><span data-stu-id="6d771-134">Example 5: Move registry keys and values to another key</span></span>

<span data-ttu-id="6d771-135">Met deze opdracht verplaatst u de register sleutels en-waarden in de register sleutel ' mijn bedrijf ' in `HKLM\Software` naar de sleutel ' MyNewCompany '.</span><span class="sxs-lookup"><span data-stu-id="6d771-135">This command moves the registry keys and values within the "MyCompany" registry key in `HKLM\Software` to the "MyNewCompany" key.</span></span>
<span data-ttu-id="6d771-136">Het Joker teken ( `*` ) geeft aan dat de inhoud van de sleutel ' mijn bedrijf ' moet worden verplaatst, niet de sleutel zelf.</span><span class="sxs-lookup"><span data-stu-id="6d771-136">The wildcard character (`*`) indicates that the contents of the "MyCompany" key should be moved, not the key itself.</span></span>
<span data-ttu-id="6d771-137">In deze opdracht worden de namen van de optionele **paden** en **doel** parameters wegge laten.</span><span class="sxs-lookup"><span data-stu-id="6d771-137">In this command, the optional **Path** and **Destination** parameter names are omitted.</span></span>

```powershell
Move-Item "HKLM:\software\mycompany\*" "HKLM:\software\mynewcompany"
```

### <span data-ttu-id="6d771-138">Voor beeld 6: een map en de inhoud ervan verplaatsen naar een submap van de opgegeven map</span><span class="sxs-lookup"><span data-stu-id="6d771-138">Example 6: Move a directory and its contents to a subdirectory of the specified directory</span></span>

<span data-ttu-id="6d771-139">Met deze opdracht wordt de map ' logs \[ Sept \` 06 \] ' (en de inhoud ervan) verplaatst naar de map ' logs \[ 2006 \] '.</span><span class="sxs-lookup"><span data-stu-id="6d771-139">This command moves the "Logs\[Sept\`06\]" directory (and its contents) into the "Logs\[2006\]" directory.</span></span>

```powershell
Move-Item -LiteralPath 'Logs[Sept`06]' -Destination 'Logs[2006]'
```

<span data-ttu-id="6d771-140">De para meter **LiteralPath** wordt gebruikt in plaats van het **pad**, omdat de naam van de oorspronkelijke map links van het haakje en rechter vier Kante tekens (" \[ " en " \] ") bevat.</span><span class="sxs-lookup"><span data-stu-id="6d771-140">The **LiteralPath** parameter is used instead of **Path**, because the original directory name includes left bracket and right bracket characters ("\[" and "\]").</span></span>
<span data-ttu-id="6d771-141">Het pad bevindt zich ook tussen enkele aanhalings tekens (' '), zodat het apostroffen-symbool ( \` ) niet wordt geïnterpreteerd.</span><span class="sxs-lookup"><span data-stu-id="6d771-141">The path is also enclosed in single quotation marks (' '), so that the backtick symbol (\`) is not misinterpreted.</span></span>

<span data-ttu-id="6d771-142">Voor de para meter **Destination** is geen letterlijk pad vereist, omdat de doel variabele ook tussen enkele aanhalings tekens moet worden geplaatst, omdat deze haakjes bevat die kunnen worden geïnterpreteerd.</span><span class="sxs-lookup"><span data-stu-id="6d771-142">The **Destination** parameter does not require a literal path, because the Destination variable also must be enclosed in single quotation marks, because it includes brackets that can be misinterpreted.</span></span>

## <span data-ttu-id="6d771-143">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="6d771-143">PARAMETERS</span></span>

### <span data-ttu-id="6d771-144">-Credential</span><span class="sxs-lookup"><span data-stu-id="6d771-144">-Credential</span></span>

> [!NOTE]
> <span data-ttu-id="6d771-145">Deze para meter wordt niet ondersteund door providers die zijn geïnstalleerd met Power shell.</span><span class="sxs-lookup"><span data-stu-id="6d771-145">This parameter is not supported by any providers installed with PowerShell.</span></span>
> <span data-ttu-id="6d771-146">Gebruik [invoke-Command](../Microsoft.PowerShell.Core/Invoke-Command.md)om een andere gebruiker te imiteren of uw referenties te verhogen wanneer u deze cmdlet uitvoert.</span><span class="sxs-lookup"><span data-stu-id="6d771-146">To impersonate another user, or elevate your credentials when running this cmdlet, use [Invoke-Command](../Microsoft.PowerShell.Core/Invoke-Command.md).</span></span>

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

### <span data-ttu-id="6d771-147">-Bestemming</span><span class="sxs-lookup"><span data-stu-id="6d771-147">-Destination</span></span>

<span data-ttu-id="6d771-148">Hiermee geeft u het pad op naar de locatie waar de items worden verplaatst.</span><span class="sxs-lookup"><span data-stu-id="6d771-148">Specifies the path to the location where the items are being moved.</span></span>
<span data-ttu-id="6d771-149">De standaardwaarde is de huidige map.</span><span class="sxs-lookup"><span data-stu-id="6d771-149">The default is the current directory.</span></span>
<span data-ttu-id="6d771-150">Joker tekens zijn toegestaan, maar in het resultaat moet één locatie worden opgegeven.</span><span class="sxs-lookup"><span data-stu-id="6d771-150">Wildcards are permitted, but the result must specify a single location.</span></span>

<span data-ttu-id="6d771-151">Als u de naam van het item dat wordt verplaatst, wilt wijzigen, geeft u een nieuwe naam op in de waarde van de para meter **Destination** .</span><span class="sxs-lookup"><span data-stu-id="6d771-151">To rename the item being moved, specify a new name in the value of the **Destination** parameter.</span></span>

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

### <span data-ttu-id="6d771-152">-Uitsluiten</span><span class="sxs-lookup"><span data-stu-id="6d771-152">-Exclude</span></span>

<span data-ttu-id="6d771-153">Hiermee geeft u als een teken reeks matrix een item of items die met deze cmdlet worden uitgesloten in de bewerking.</span><span class="sxs-lookup"><span data-stu-id="6d771-153">Specifies, as a string array, an item or items that this cmdlet excludes in the operation.</span></span> <span data-ttu-id="6d771-154">De waarde van deze para meter komt in aanmerking voor de para meter **Path** .</span><span class="sxs-lookup"><span data-stu-id="6d771-154">The value of this parameter qualifies the **Path** parameter.</span></span> <span data-ttu-id="6d771-155">Voer een element of patroon van een pad in, zoals `*.txt` .</span><span class="sxs-lookup"><span data-stu-id="6d771-155">Enter a path element or pattern, such as `*.txt`.</span></span> <span data-ttu-id="6d771-156">Joker tekens zijn toegestaan.</span><span class="sxs-lookup"><span data-stu-id="6d771-156">Wildcard characters are permitted.</span></span> <span data-ttu-id="6d771-157">De **exclude** -para meter is alleen effectief wanneer de inhoud van een item wordt opgenomen, zoals `C:\Windows\*` , waarbij het Joker teken de inhoud van de `C:\Windows` map bevat.</span><span class="sxs-lookup"><span data-stu-id="6d771-157">The **Exclude** parameter is effective only when the command includes the contents of an item, such as `C:\Windows\*`, where the wildcard character specifies the contents of the `C:\Windows` directory.</span></span>

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

### <span data-ttu-id="6d771-158">-Filter</span><span class="sxs-lookup"><span data-stu-id="6d771-158">-Filter</span></span>

<span data-ttu-id="6d771-159">Hiermee geeft u een filter op om de para meter **Path** te kwalificeren.</span><span class="sxs-lookup"><span data-stu-id="6d771-159">Specifies a filter to qualify the **Path** parameter.</span></span> <span data-ttu-id="6d771-160">De [File System](../Microsoft.PowerShell.Core/About/about_FileSystem_Provider.md) -provider is de enige geïnstalleerde Power shell-provider die het gebruik van filters ondersteunt.</span><span class="sxs-lookup"><span data-stu-id="6d771-160">The [FileSystem](../Microsoft.PowerShell.Core/About/about_FileSystem_Provider.md) provider is the only installed PowerShell provider that supports the use of filters.</span></span> <span data-ttu-id="6d771-161">U kunt de syntaxis voor de filter taal van het **Bestands systeem** in [about_Wildcards](../Microsoft.PowerShell.Core/About/about_Wildcards.md)vinden.</span><span class="sxs-lookup"><span data-stu-id="6d771-161">You can find the syntax for the **FileSystem** filter language in [about_Wildcards](../Microsoft.PowerShell.Core/About/about_Wildcards.md).</span></span>
<span data-ttu-id="6d771-162">Filters zijn efficiënter dan andere para meters, omdat deze door de provider worden toegepast wanneer de cmdlet de objecten ophaalt in plaats van dat Power shell de objecten heeft gefilterd nadat ze zijn opgehaald.</span><span class="sxs-lookup"><span data-stu-id="6d771-162">Filters are more efficient than other parameters, because the provider applies them when the cmdlet gets the objects rather than having PowerShell filter the objects after they are retrieved.</span></span>

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

### <span data-ttu-id="6d771-163">-Force</span><span class="sxs-lookup"><span data-stu-id="6d771-163">-Force</span></span>

<span data-ttu-id="6d771-164">Hiermee wordt de opdracht uitgevoerd zonder dat de gebruiker om bevestiging wordt gevraagd.</span><span class="sxs-lookup"><span data-stu-id="6d771-164">Forces the command to run without asking for user confirmation.</span></span>
<span data-ttu-id="6d771-165">De implementatie varieert van provider tot provider.</span><span class="sxs-lookup"><span data-stu-id="6d771-165">Implementation varies from provider to provider.</span></span>
<span data-ttu-id="6d771-166">Zie [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="6d771-166">For more information, see [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md).</span></span>

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

### <span data-ttu-id="6d771-167">-Include</span><span class="sxs-lookup"><span data-stu-id="6d771-167">-Include</span></span>

<span data-ttu-id="6d771-168">Hiermee wordt een teken reeks matrix opgegeven, een item of items die met deze cmdlet in de bewerking zijn opgenomen.</span><span class="sxs-lookup"><span data-stu-id="6d771-168">Specifies, as a string array, an item or items that this cmdlet includes in the operation.</span></span> <span data-ttu-id="6d771-169">De waarde van deze para meter komt in aanmerking voor de para meter **Path** .</span><span class="sxs-lookup"><span data-stu-id="6d771-169">The value of this parameter qualifies the **Path** parameter.</span></span> <span data-ttu-id="6d771-170">Voer een element of patroon van een pad in, zoals `"*.txt"` .</span><span class="sxs-lookup"><span data-stu-id="6d771-170">Enter a path element or pattern, such as `"*.txt"`.</span></span> <span data-ttu-id="6d771-171">Joker tekens zijn toegestaan.</span><span class="sxs-lookup"><span data-stu-id="6d771-171">Wildcard characters are permitted.</span></span> <span data-ttu-id="6d771-172">De para meter **include** is alleen effectief wanneer de inhoud van een item wordt opgenomen, zoals `C:\Windows\*` , waarbij het Joker teken de inhoud van de `C:\Windows` map bevat.</span><span class="sxs-lookup"><span data-stu-id="6d771-172">The **Include** parameter is effective only when the command includes the contents of an item, such as `C:\Windows\*`, where the wildcard character specifies the contents of the `C:\Windows` directory.</span></span>

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

### <span data-ttu-id="6d771-173">-LiteralPath</span><span class="sxs-lookup"><span data-stu-id="6d771-173">-LiteralPath</span></span>

<span data-ttu-id="6d771-174">Hiermee geeft u een pad naar een of meer locaties.</span><span class="sxs-lookup"><span data-stu-id="6d771-174">Specifies a path to one or more locations.</span></span> <span data-ttu-id="6d771-175">De waarde van **LiteralPath** wordt precies zo gebruikt als deze wordt getypt.</span><span class="sxs-lookup"><span data-stu-id="6d771-175">The value of **LiteralPath** is used exactly as it is typed.</span></span> <span data-ttu-id="6d771-176">Geen tekens worden geïnterpreteerd als joker tekens.</span><span class="sxs-lookup"><span data-stu-id="6d771-176">No characters are interpreted as wildcards.</span></span> <span data-ttu-id="6d771-177">Als het pad escape tekens bevat, plaatst u het tussen enkele aanhalings tekens.</span><span class="sxs-lookup"><span data-stu-id="6d771-177">If the path includes escape characters, enclose it in single quotation marks.</span></span> <span data-ttu-id="6d771-178">Enkele aanhalings tekens geven aan dat Power shell geen karakters interpreteert als escape reeksen.</span><span class="sxs-lookup"><span data-stu-id="6d771-178">Single quotation marks tell PowerShell not to interpret any characters as escape sequences.</span></span>

<span data-ttu-id="6d771-179">Zie [about_Quoting_Rules](../Microsoft.Powershell.Core/About/about_Quoting_Rules.md)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="6d771-179">For more information, see [about_Quoting_Rules](../Microsoft.Powershell.Core/About/about_Quoting_Rules.md).</span></span>

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

### <span data-ttu-id="6d771-180">-PassThru</span><span class="sxs-lookup"><span data-stu-id="6d771-180">-PassThru</span></span>

<span data-ttu-id="6d771-181">Retourneert een object dat het item vertegenwoordigt waarmee u werkt.</span><span class="sxs-lookup"><span data-stu-id="6d771-181">Returns an object representing the item with which you are working.</span></span>
<span data-ttu-id="6d771-182">Deze cmdlet genereert standaard geen uitvoer.</span><span class="sxs-lookup"><span data-stu-id="6d771-182">By default, this cmdlet does not generate any output.</span></span>

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

### <span data-ttu-id="6d771-183">-Path</span><span class="sxs-lookup"><span data-stu-id="6d771-183">-Path</span></span>

<span data-ttu-id="6d771-184">Hiermee geeft u het pad op naar de huidige locatie van de items.</span><span class="sxs-lookup"><span data-stu-id="6d771-184">Specifies the path to the current location of the items.</span></span>
<span data-ttu-id="6d771-185">De standaardwaarde is de huidige map.</span><span class="sxs-lookup"><span data-stu-id="6d771-185">The default is the current directory.</span></span>
<span data-ttu-id="6d771-186">Joker tekens zijn toegestaan.</span><span class="sxs-lookup"><span data-stu-id="6d771-186">Wildcard characters are permitted.</span></span>

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

### <span data-ttu-id="6d771-187">-Confirm</span><span class="sxs-lookup"><span data-stu-id="6d771-187">-Confirm</span></span>

<span data-ttu-id="6d771-188">Hiermee wordt u gevraagd om bevestiging voordat u de cmdlet uitvoert.</span><span class="sxs-lookup"><span data-stu-id="6d771-188">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="6d771-189">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="6d771-189">-WhatIf</span></span>

<span data-ttu-id="6d771-190">Hiermee wordt weergegeven wat er zou gebeuren als u de cmdlet uitvoert.</span><span class="sxs-lookup"><span data-stu-id="6d771-190">Shows what would happen if the cmdlet runs.</span></span>
<span data-ttu-id="6d771-191">De cmdlet wordt niet uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="6d771-191">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="6d771-192">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="6d771-192">CommonParameters</span></span>

<span data-ttu-id="6d771-193">Deze cmdlet biedt ondersteuning voor de algemene para meters: `-Debug` , `-ErrorAction` , `-ErrorVariable` , `-InformationAction` , `-InformationVariable` , `-OutVariable` , `-OutBuffer` , `-PipelineVariable` , `-Verbose` , `-WarningAction` en `-WarningVariable` .</span><span class="sxs-lookup"><span data-stu-id="6d771-193">This cmdlet supports the common parameters: `-Debug`, `-ErrorAction`, `-ErrorVariable`, `-InformationAction`, `-InformationVariable`, `-OutVariable`, `-OutBuffer`, `-PipelineVariable`, `-Verbose`, `-WarningAction`, and `-WarningVariable`.</span></span> <span data-ttu-id="6d771-194">Zie [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="6d771-194">For more information, see [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md).</span></span>

## <span data-ttu-id="6d771-195">INVOER</span><span class="sxs-lookup"><span data-stu-id="6d771-195">INPUTS</span></span>

### <span data-ttu-id="6d771-196">System. String</span><span class="sxs-lookup"><span data-stu-id="6d771-196">System.String</span></span>

<span data-ttu-id="6d771-197">U kunt een teken reeks met een pad naar deze cmdlet door sluizen.</span><span class="sxs-lookup"><span data-stu-id="6d771-197">You can pipe a string that contains a path to this cmdlet.</span></span>

## <span data-ttu-id="6d771-198">UITVOER</span><span class="sxs-lookup"><span data-stu-id="6d771-198">OUTPUTS</span></span>

### <span data-ttu-id="6d771-199">Geen of een object dat het verplaatste item vertegenwoordigt</span><span class="sxs-lookup"><span data-stu-id="6d771-199">None or an object representing the moved item</span></span>

<span data-ttu-id="6d771-200">Wanneer u de para meter *PassThru* gebruikt, genereert deze cmdlet een object dat het verplaatste item vertegenwoordigt.</span><span class="sxs-lookup"><span data-stu-id="6d771-200">When you use the *PassThru* parameter, this cmdlet generates an object representing the moved item.</span></span>
<span data-ttu-id="6d771-201">Anders wordt met deze cmdlet geen uitvoer gegenereerd.</span><span class="sxs-lookup"><span data-stu-id="6d771-201">Otherwise, this cmdlet does not generate any output.</span></span>

## <span data-ttu-id="6d771-202">OPMERKINGEN</span><span class="sxs-lookup"><span data-stu-id="6d771-202">NOTES</span></span>

- <span data-ttu-id="6d771-203">Met deze cmdlet worden bestanden verplaatst tussen de stations die worden ondersteund door dezelfde provider, maar worden mappen alleen verplaatst binnen hetzelfde station.</span><span class="sxs-lookup"><span data-stu-id="6d771-203">This cmdlet will move files between drives that are supported by the same provider, but it will move directories only within the same drive.</span></span>
- <span data-ttu-id="6d771-204">Omdat een `Move-Item` opdracht de eigenschappen, inhoud en onderliggende items van een item verplaatst, zijn alle verplaatsingen standaard recursief.</span><span class="sxs-lookup"><span data-stu-id="6d771-204">Because a `Move-Item` command moves the properties, contents, and child items of an item, all moves are recursive by default.</span></span>
- <span data-ttu-id="6d771-205">Deze cmdlet is ontworpen om te werken met de gegevens die door elke provider worden weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="6d771-205">This cmdlet is designed to work with the data exposed by any provider.</span></span>
  <span data-ttu-id="6d771-206">Als u een lijst wilt weer geven van de providers die beschikbaar zijn in uw sessie, typt u `Get-PSProvider` .</span><span class="sxs-lookup"><span data-stu-id="6d771-206">To list the providers available in your session, type `Get-PSProvider`.</span></span>
  <span data-ttu-id="6d771-207">Zie [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="6d771-207">For more information, see [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md).</span></span>

## <span data-ttu-id="6d771-208">GERELATEERDE KOPPELINGEN</span><span class="sxs-lookup"><span data-stu-id="6d771-208">RELATED LINKS</span></span>

[<span data-ttu-id="6d771-209">Wissen-item</span><span class="sxs-lookup"><span data-stu-id="6d771-209">Clear-Item</span></span>](Clear-Item.md)

[<span data-ttu-id="6d771-210">Kopie-item</span><span class="sxs-lookup"><span data-stu-id="6d771-210">Copy-Item</span></span>](Copy-Item.md)

[<span data-ttu-id="6d771-211">Get-item</span><span class="sxs-lookup"><span data-stu-id="6d771-211">Get-Item</span></span>](Get-Item.md)

[<span data-ttu-id="6d771-212">Invoke-item</span><span class="sxs-lookup"><span data-stu-id="6d771-212">Invoke-Item</span></span>](Invoke-Item.md)

[<span data-ttu-id="6d771-213">Nieuw-item</span><span class="sxs-lookup"><span data-stu-id="6d771-213">New-Item</span></span>](New-Item.md)

[<span data-ttu-id="6d771-214">Verwijderen-item</span><span class="sxs-lookup"><span data-stu-id="6d771-214">Remove-Item</span></span>](Remove-Item.md)

[<span data-ttu-id="6d771-215">Naam wijzigen-item</span><span class="sxs-lookup"><span data-stu-id="6d771-215">Rename-Item</span></span>](Rename-Item.md)

[<span data-ttu-id="6d771-216">Set-item</span><span class="sxs-lookup"><span data-stu-id="6d771-216">Set-Item</span></span>](Set-Item.md)

[<span data-ttu-id="6d771-217">about_Providers</span><span class="sxs-lookup"><span data-stu-id="6d771-217">about_Providers</span></span>](../Microsoft.PowerShell.Core/About/about_Providers.md)

