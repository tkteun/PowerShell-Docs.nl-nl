---
external help file: ISE-help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: ISE
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/ise/new-isesnippet?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: New-IseSnippet
ms.openlocfilehash: 0ed1c2913fc7531574bfbdd435a002d60931d24a
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/07/2020
ms.locfileid: "93250046"
---
# <span data-ttu-id="cc4c0-103">New-IseSnippet</span><span class="sxs-lookup"><span data-stu-id="cc4c0-103">New-IseSnippet</span></span>

## <span data-ttu-id="cc4c0-104">SAMENVATTING</span><span class="sxs-lookup"><span data-stu-id="cc4c0-104">SYNOPSIS</span></span>
<span data-ttu-id="cc4c0-105">Hiermee maakt u een code fragment Windows PowerShell ISE.</span><span class="sxs-lookup"><span data-stu-id="cc4c0-105">Creates a Windows PowerShell ISE code snippet.</span></span>

## <span data-ttu-id="cc4c0-106">SYNTAXIS</span><span class="sxs-lookup"><span data-stu-id="cc4c0-106">SYNTAX</span></span>

```
New-IseSnippet [-Title] <String> [-Description] <String> [-Text] <String> [-Author <String>]
 [-CaretOffset <Int32>] [-Force] [<CommonParameters>]
```

## <span data-ttu-id="cc4c0-107">BESCHRIJVING</span><span class="sxs-lookup"><span data-stu-id="cc4c0-107">DESCRIPTION</span></span>

<span data-ttu-id="cc4c0-108">De `New-ISESnippet` cmdlet maakt een Herbruikbare tekst fragment voor Windows PowerShell ISE.</span><span class="sxs-lookup"><span data-stu-id="cc4c0-108">The `New-ISESnippet` cmdlet creates a reusable text "snippet" for Windows PowerShell ISE.</span></span> <span data-ttu-id="cc4c0-109">U kunt fragmenten gebruiken om tekst toe te voegen aan het Script venster of het opdracht venster in Windows PowerShell ISE.</span><span class="sxs-lookup"><span data-stu-id="cc4c0-109">You can use snippets to add text to the Script pane or Command pane in Windows PowerShell ISE.</span></span> <span data-ttu-id="cc4c0-110">Deze cmdlet is alleen beschikbaar in Windows PowerShell ISE.</span><span class="sxs-lookup"><span data-stu-id="cc4c0-110">This cmdlet is available only in Windows PowerShell ISE.</span></span>

<span data-ttu-id="cc4c0-111">Vanaf Windows Power Shell 3,0 bevat Windows PowerShell ISE een verzameling ingebouwde fragmenten.</span><span class="sxs-lookup"><span data-stu-id="cc4c0-111">Beginning in Windows PowerShell 3.0, Windows PowerShell ISE includes a collection of built-in snippets.</span></span> <span data-ttu-id="cc4c0-112">Met de `New-ISESnippet` cmdlet kunt u uw eigen fragmenten maken om toe te voegen aan de ingebouwde verzameling.</span><span class="sxs-lookup"><span data-stu-id="cc4c0-112">The `New-ISESnippet` cmdlet lets you create your own snippets to add to the built-in collection.</span></span> <span data-ttu-id="cc4c0-113">U kunt fragment bestanden weer geven, wijzigen, toevoegen, verwijderen en delen in Windows Power shell-modules.</span><span class="sxs-lookup"><span data-stu-id="cc4c0-113">You can view, change, add, delete, and share snippet files and include them in Windows PowerShell modules.</span></span> <span data-ttu-id="cc4c0-114">Als u fragmenten in Windows PowerShell ISE wilt zien, selecteert u in het menu **bewerken** de optie **fragmenten starten** of drukt u op <kbd>CTRL</kbd> + <kbd>J</kbd>.</span><span class="sxs-lookup"><span data-stu-id="cc4c0-114">To see snippets in Windows PowerShell ISE, from the **Edit** menu, select **Start Snippets** or press <kbd>CTRL</kbd>+<kbd>J</kbd>.</span></span>

<span data-ttu-id="cc4c0-115">`New-ISESnippet`Met de cmdlet maakt `<Title>.Snippets.ps1xml` u een bestand in de `$home\Documents\WindowsPowerShell\Snippets` map met de titel die u opgeeft.</span><span class="sxs-lookup"><span data-stu-id="cc4c0-115">The `New-ISESnippet` cmdlet creates a `<Title>.Snippets.ps1xml` file in the `$home\Documents\WindowsPowerShell\Snippets` directory with the title that you specify.</span></span> <span data-ttu-id="cc4c0-116">Als u een fragment bestand wilt toevoegen in een module die u ontwerpt, voegt u het fragment bestand toe aan een subdirectory met fragmenten van uw module directory.</span><span class="sxs-lookup"><span data-stu-id="cc4c0-116">To include a snippet file in a module that you are authoring, add the snippet file to a Snippets subdirectory of your module directory.</span></span>

<span data-ttu-id="cc4c0-117">U kunt door de gebruiker gemaakte fragmenten niet gebruiken in een sessie waarin het uitvoerings beleid is **beperkt** of **Alles ondertekend**.</span><span class="sxs-lookup"><span data-stu-id="cc4c0-117">You cannot use user-created snippets in a session in which the execution policy is **Restricted** or **AllSigned**.</span></span>

<span data-ttu-id="cc4c0-118">Deze cmdlet is geïntroduceerd in Windows Power Shell 3,0.</span><span class="sxs-lookup"><span data-stu-id="cc4c0-118">This cmdlet was introduced in Windows PowerShell 3.0.</span></span>

## <span data-ttu-id="cc4c0-119">VOORBEELDEN</span><span class="sxs-lookup"><span data-stu-id="cc4c0-119">EXAMPLES</span></span>

### <span data-ttu-id="cc4c0-120">Voor beeld 1: een Help-fragment maken voor een Comment-Based</span><span class="sxs-lookup"><span data-stu-id="cc4c0-120">Example 1: Create a Comment-Based help snippet</span></span>

```
New-IseSnippet -Title Comment-BasedHelp -Description "A template for comment-based help." -Text "<#
    .SYNOPSIS

    .DESCRIPTION
    .PARAMETER  <Parameter-Name>
    .INPUTS
    .OUTPUTS
    .EXAMPLE
    .LINK
#>"
```

<span data-ttu-id="cc4c0-121">Met deze opdracht maakt u een Comment-BasedHelp fragment voor Windows PowerShell ISE.</span><span class="sxs-lookup"><span data-stu-id="cc4c0-121">This command creates a Comment-BasedHelp snippet for Windows PowerShell ISE.</span></span> <span data-ttu-id="cc4c0-122">Er wordt een bestand gemaakt `Comment-BasedHelp.snippets.ps1xml` met de naam in de map met fragmenten van de gebruiker `$home\Documents\WindowsPowerShell\Snippets` .</span><span class="sxs-lookup"><span data-stu-id="cc4c0-122">It creates a file named `Comment-BasedHelp.snippets.ps1xml` in the user's Snippets directory `$home\Documents\WindowsPowerShell\Snippets`.</span></span>

### <span data-ttu-id="cc4c0-123">Voor beeld 2: een verplicht fragment maken</span><span class="sxs-lookup"><span data-stu-id="cc4c0-123">Example 2: Create a mandatory snippet</span></span>

```
$M = @'
Param
(
  [parameter(Mandatory=$true)]
  [String[]]
  $<ParameterName>
)
'@

New-ISESnippet -Text $M -Title Mandatory -Description "Adds a mandatory function parameter." -Author "Patti Fuller, Fabrikam Corp." -Force
```

<span data-ttu-id="cc4c0-124">In dit voor beeld wordt een code fragment gemaakt met de naam **verplicht** voor Windows PowerShell ISE.</span><span class="sxs-lookup"><span data-stu-id="cc4c0-124">This example creates a snippet named **Mandatory** for Windows PowerShell ISE.</span></span> <span data-ttu-id="cc4c0-125">Met de eerste opdracht wordt de tekst van het fragment opgeslagen in de `$M` variabele.</span><span class="sxs-lookup"><span data-stu-id="cc4c0-125">The first command saves the snippet text in the `$M` variable.</span></span> <span data-ttu-id="cc4c0-126">De tweede opdracht gebruikt de `New-ISESnippet` cmdlet om het fragment te maken.</span><span class="sxs-lookup"><span data-stu-id="cc4c0-126">The second command uses the `New-ISESnippet` cmdlet to create the snippet.</span></span> <span data-ttu-id="cc4c0-127">De opdracht gebruikt de para meter **Force** voor het overschrijven van een vorig fragment met dezelfde naam.</span><span class="sxs-lookup"><span data-stu-id="cc4c0-127">The command uses the **Force** parameter to overwrite a previous snippet with the same name.</span></span>

### <span data-ttu-id="cc4c0-128">Voor beeld 3: een verplicht fragment uit een map naar een doelmap kopiëren</span><span class="sxs-lookup"><span data-stu-id="cc4c0-128">Example 3: Copy a mandatory snippet from a folder to a destination folder</span></span>

```
Copy-Item "$Home\Documents\WindowsPowerShell\Snippets\Mandatory.Snippets.ps1xml" -Destination "\\Server\Share"
```

<span data-ttu-id="cc4c0-129">Met deze opdracht wordt de `Copy-Item` cmdlet gebruikt om het **verplichte** fragment te kopiëren uit de map waar het `New-ISESnippet` wordt geplaatst naar de Server\Share-bestands share.</span><span class="sxs-lookup"><span data-stu-id="cc4c0-129">This command uses the `Copy-Item` cmdlet to copy the **Mandatory** snippet from the folder where `New-ISESnippet` places it to the Server\Share file share.</span></span>

## <span data-ttu-id="cc4c0-130">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="cc4c0-130">PARAMETERS</span></span>

### <span data-ttu-id="cc4c0-131">-Author</span><span class="sxs-lookup"><span data-stu-id="cc4c0-131">-Author</span></span>

<span data-ttu-id="cc4c0-132">Hiermee geeft u de auteur van het fragment.</span><span class="sxs-lookup"><span data-stu-id="cc4c0-132">Specifies the author of the snippet.</span></span> <span data-ttu-id="cc4c0-133">Het veld Auteur wordt weer gegeven in het fragment bestand, maar wordt niet weer gegeven wanneer u op de naam van het fragment in Windows PowerShell ISE klikt.</span><span class="sxs-lookup"><span data-stu-id="cc4c0-133">The author field appears in the snippet file, but it does not appear when you click the snippet name in Windows PowerShell ISE.</span></span>

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

### <span data-ttu-id="cc4c0-134">-CaretOffset</span><span class="sxs-lookup"><span data-stu-id="cc4c0-134">-CaretOffset</span></span>

<span data-ttu-id="cc4c0-135">Hiermee wordt het teken van de tekst van het fragment opgegeven waarin deze cmdlet de cursor plaatst.</span><span class="sxs-lookup"><span data-stu-id="cc4c0-135">Specifies the character of the snippet text that this cmdlet places the cursor on.</span></span> <span data-ttu-id="cc4c0-136">Voer een geheel getal in dat de positie van de cursor vertegenwoordigt en ' 1 ' staat voor het eerste teken van de tekst.</span><span class="sxs-lookup"><span data-stu-id="cc4c0-136">Enter an integer that represents the cursor position, with "1" representing the first character of text.</span></span> <span data-ttu-id="cc4c0-137">De standaard waarde, 0 (nul), plaatst de cursor direct voor het eerste teken van de tekst.</span><span class="sxs-lookup"><span data-stu-id="cc4c0-137">The default value, 0 (zero), places the cursor immediately before the first character of text.</span></span> <span data-ttu-id="cc4c0-138">Met deze para meter wordt de tekst van het fragment niet Inge sprongen.</span><span class="sxs-lookup"><span data-stu-id="cc4c0-138">This parameter does not indent the snippet text.</span></span>

```yaml
Type: System.Int32
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: 0
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="cc4c0-139">-Beschrijving</span><span class="sxs-lookup"><span data-stu-id="cc4c0-139">-Description</span></span>

<span data-ttu-id="cc4c0-140">Hiermee geeft u een beschrijving van het fragment op.</span><span class="sxs-lookup"><span data-stu-id="cc4c0-140">Specifies a description of the snippet.</span></span> <span data-ttu-id="cc4c0-141">De waarde van de beschrijving wordt weer gegeven wanneer u op de naam van het fragment in Windows PowerShell ISE klikt.</span><span class="sxs-lookup"><span data-stu-id="cc4c0-141">The description value appears when you click the snippet name in Windows PowerShell ISE.</span></span> <span data-ttu-id="cc4c0-142">Deze parameter is vereist.</span><span class="sxs-lookup"><span data-stu-id="cc4c0-142">This parameter is required.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: True
Position: 2
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="cc4c0-143">-Force</span><span class="sxs-lookup"><span data-stu-id="cc4c0-143">-Force</span></span>

<span data-ttu-id="cc4c0-144">Geeft aan dat met deze cmdlet fragment bestanden met dezelfde naam op dezelfde locatie worden overschreven.</span><span class="sxs-lookup"><span data-stu-id="cc4c0-144">Indicates that this cmdlet overwrites snippet files with the same name in the same location.</span></span> <span data-ttu-id="cc4c0-145">Standaard worden `New-ISESnippet` bestanden niet overschreven.</span><span class="sxs-lookup"><span data-stu-id="cc4c0-145">By default, `New-ISESnippet` does not overwrite files.</span></span>

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

### <span data-ttu-id="cc4c0-146">-Tekst</span><span class="sxs-lookup"><span data-stu-id="cc4c0-146">-Text</span></span>

<span data-ttu-id="cc4c0-147">Hiermee geeft u de tekst waarde op die wordt toegevoegd wanneer u het fragment selecteert.</span><span class="sxs-lookup"><span data-stu-id="cc4c0-147">Specifies the text value that is added when you select the snippet.</span></span> <span data-ttu-id="cc4c0-148">De tekst van het fragment wordt weer gegeven wanneer u op de naam van het fragment in Windows PowerShell ISE klikt.</span><span class="sxs-lookup"><span data-stu-id="cc4c0-148">The snippet text appears when you click the snippet name in Windows PowerShell ISE.</span></span> <span data-ttu-id="cc4c0-149">Deze parameter is vereist.</span><span class="sxs-lookup"><span data-stu-id="cc4c0-149">This parameter is required.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: True
Position: 3
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="cc4c0-150">-Titel</span><span class="sxs-lookup"><span data-stu-id="cc4c0-150">-Title</span></span>

<span data-ttu-id="cc4c0-151">Hiermee geeft u een titel of naam voor het fragment op.</span><span class="sxs-lookup"><span data-stu-id="cc4c0-151">Specifies a title or name for the snippet.</span></span> <span data-ttu-id="cc4c0-152">De titel heeft ook de naam van het fragment bestand.</span><span class="sxs-lookup"><span data-stu-id="cc4c0-152">The title also names the snippet file.</span></span> <span data-ttu-id="cc4c0-153">Deze parameter is vereist.</span><span class="sxs-lookup"><span data-stu-id="cc4c0-153">This parameter is required.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: True
Position: 1
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="cc4c0-154">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="cc4c0-154">CommonParameters</span></span>

<span data-ttu-id="cc4c0-155">Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="cc4c0-155">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="cc4c0-156">Zie [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="cc4c0-156">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="cc4c0-157">INVOER</span><span class="sxs-lookup"><span data-stu-id="cc4c0-157">INPUTS</span></span>

### <span data-ttu-id="cc4c0-158">Geen</span><span class="sxs-lookup"><span data-stu-id="cc4c0-158">None</span></span>

<span data-ttu-id="cc4c0-159">Deze cmdlet neemt geen invoer van de pijp lijn.</span><span class="sxs-lookup"><span data-stu-id="cc4c0-159">This cmdlet does not take input from the pipeline.</span></span>

## <span data-ttu-id="cc4c0-160">UITVOER</span><span class="sxs-lookup"><span data-stu-id="cc4c0-160">OUTPUTS</span></span>

### <span data-ttu-id="cc4c0-161">Geen</span><span class="sxs-lookup"><span data-stu-id="cc4c0-161">None</span></span>

<span data-ttu-id="cc4c0-162">Met deze cmdlet wordt geen uitvoer gegenereerd.</span><span class="sxs-lookup"><span data-stu-id="cc4c0-162">This cmdlet does not generate any output.</span></span>

## <span data-ttu-id="cc4c0-163">OPMERKINGEN</span><span class="sxs-lookup"><span data-stu-id="cc4c0-163">NOTES</span></span>

<span data-ttu-id="cc4c0-164">`New-IseSnippet` slaat nieuwe door de gebruiker gemaakte fragmenten op in niet-ondertekende. ps1xml-bestanden.</span><span class="sxs-lookup"><span data-stu-id="cc4c0-164">`New-IseSnippet` stores new user-created snippets in unsigned .ps1xml files.</span></span> <span data-ttu-id="cc4c0-165">Windows Power shell kan deze niet toevoegen aan een sessie waarin het uitvoerings beleid **Alles ondertekend** of **beperkt** is.</span><span class="sxs-lookup"><span data-stu-id="cc4c0-165">As such, Windows PowerShell cannot add them to a session in which the execution policy is **AllSigned** or **Restricted**.</span></span> <span data-ttu-id="cc4c0-166">In een **beperkte** of **Alles ondertekende** sessie kunt u niet-ondertekende door de gebruiker gemaakte fragmenten maken, ophalen en importeren, maar u kunt ze niet gebruiken in de sessie.</span><span class="sxs-lookup"><span data-stu-id="cc4c0-166">In a **Restricted** or **AllSigned** session, you can create, get, and import unsigned user-created snippets, but you cannot use them in the session.</span></span>

<span data-ttu-id="cc4c0-167">Als u de `New-IseSnippet` cmdlet in een **beperkte** of **Alles ondertekend** -sessie gebruikt, wordt het fragment gemaakt, maar er wordt een fout bericht weer gegeven wanneer Windows Power shell het zojuist gemaakte fragment aan de sessie probeert toe te voegen.</span><span class="sxs-lookup"><span data-stu-id="cc4c0-167">If you use the `New-IseSnippet` cmdlet in a **Restricted** or **AllSigned** session, the snippet is created, but an error message appears when Windows PowerShell tries to add the newly created snippet to the session.</span></span> <span data-ttu-id="cc4c0-168">Als u het nieuwe fragment (en andere niet-ondertekende door de gebruiker gemaakte fragmenten) wilt gebruiken, wijzigt u het uitvoerings beleid en start u Windows PowerShell ISE opnieuw.</span><span class="sxs-lookup"><span data-stu-id="cc4c0-168">To use the new snippet (and other unsigned user-created snippets), change the execution policy, and then restart Windows PowerShell ISE.</span></span>

<span data-ttu-id="cc4c0-169">Zie about_Execution_Policies voor meer informatie over het uitvoerings beleid van Windows Power shell.</span><span class="sxs-lookup"><span data-stu-id="cc4c0-169">For more information about Windows PowerShell execution policies, see about_Execution_Policies.</span></span>

- <span data-ttu-id="cc4c0-170">Bewerk het fragment bestand als u een fragment wilt wijzigen.</span><span class="sxs-lookup"><span data-stu-id="cc4c0-170">To change a snippet, edit the snippet file.</span></span> <span data-ttu-id="cc4c0-171">U kunt fragment bestanden bewerken in het Script venster van Windows PowerShell ISE.</span><span class="sxs-lookup"><span data-stu-id="cc4c0-171">You can edit snippet files in the Script pane of Windows PowerShell ISE.</span></span>
- <span data-ttu-id="cc4c0-172">Als u een toegevoegd fragment wilt verwijderen, verwijdert u het fragment bestand.</span><span class="sxs-lookup"><span data-stu-id="cc4c0-172">To delete a snippet that you added, delete the snippet file.</span></span>
- <span data-ttu-id="cc4c0-173">Het is niet mogelijk om een ingebouwd fragment te verwijderen, maar u kunt alle ingebouwde fragmenten verbergen met behulp van de $psise. Opties. ShowDefaultSnippets = $false "opdracht.</span><span class="sxs-lookup"><span data-stu-id="cc4c0-173">You cannot delete a built-in snippet, but you can hide all built-in snippets by using the "$psise.Options.ShowDefaultSnippets=$false" command.</span></span>
- <span data-ttu-id="cc4c0-174">U kunt een fragment maken dat dezelfde naam heeft als een ingebouwd fragment.</span><span class="sxs-lookup"><span data-stu-id="cc4c0-174">You can create a snippet that has the same name as a built-in snippet.</span></span> <span data-ttu-id="cc4c0-175">Beide fragmenten worden weer gegeven in het menu fragment in Windows PowerShell ISE.</span><span class="sxs-lookup"><span data-stu-id="cc4c0-175">Both snippets appear in the snippet menu in Windows PowerShell ISE.</span></span>

## <span data-ttu-id="cc4c0-176">GERELATEERDE KOPPELINGEN</span><span class="sxs-lookup"><span data-stu-id="cc4c0-176">RELATED LINKS</span></span>

[<span data-ttu-id="cc4c0-177">Get-IseSnippet</span><span class="sxs-lookup"><span data-stu-id="cc4c0-177">Get-IseSnippet</span></span>](Get-IseSnippet.md)

[<span data-ttu-id="cc4c0-178">Import-IseSnippet</span><span class="sxs-lookup"><span data-stu-id="cc4c0-178">Import-IseSnippet</span></span>](Import-IseSnippet.md)
