---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 04/07/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/remove-item?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Remove-Item
ms.openlocfilehash: 64bdbf9bbfe023c6cb909596e266201e2165e7a6
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 11/17/2020
ms.locfileid: "94705954"
---
# <span data-ttu-id="24662-102">Remove-Item</span><span class="sxs-lookup"><span data-stu-id="24662-102">Remove-Item</span></span>

## <span data-ttu-id="24662-103">SAMENVATTING</span><span class="sxs-lookup"><span data-stu-id="24662-103">SYNOPSIS</span></span>
<span data-ttu-id="24662-104">Hiermee verwijdert u de opgegeven items.</span><span class="sxs-lookup"><span data-stu-id="24662-104">Deletes the specified items.</span></span>

## <span data-ttu-id="24662-105">SYNTAXIS</span><span class="sxs-lookup"><span data-stu-id="24662-105">SYNTAX</span></span>

### <span data-ttu-id="24662-106">Pad (standaard)</span><span class="sxs-lookup"><span data-stu-id="24662-106">Path (Default)</span></span>

```
Remove-Item [-Path] <String[]> [-Filter <String>] [-Include <String[]>] [-Exclude <String[]>]
 [-Recurse] [-Force] [-Credential <PSCredential>] [-WhatIf] [-Confirm] [-Stream <String[]>]
 [<CommonParameters>]
```

### <span data-ttu-id="24662-107">LiteralPath</span><span class="sxs-lookup"><span data-stu-id="24662-107">LiteralPath</span></span>

```
Remove-Item -LiteralPath <String[]> [-Filter <String>] [-Include <String[]>] [-Exclude <String[]>]
 [-Recurse] [-Force] [-Credential <PSCredential>] [-WhatIf] [-Confirm] [-Stream <String[]>]
 [<CommonParameters>]
```

## <span data-ttu-id="24662-108">BESCHRIJVING</span><span class="sxs-lookup"><span data-stu-id="24662-108">DESCRIPTION</span></span>

<span data-ttu-id="24662-109">Met de `Remove-Item` cmdlet worden een of meer items verwijderd.</span><span class="sxs-lookup"><span data-stu-id="24662-109">The `Remove-Item` cmdlet deletes one or more items.</span></span> <span data-ttu-id="24662-110">Omdat het wordt ondersteund door veel providers, kan het veel verschillende typen items verwijderen, waaronder bestanden, mappen, register sleutels, variabelen, aliassen en functies.</span><span class="sxs-lookup"><span data-stu-id="24662-110">Because it is supported by many providers, it can delete many different types of items, including files, folders, registry keys, variables, aliases, and functions.</span></span>

## <span data-ttu-id="24662-111">VOORBEELDEN</span><span class="sxs-lookup"><span data-stu-id="24662-111">EXAMPLES</span></span>

### <span data-ttu-id="24662-112">Voor beeld 1: bestanden met de bestandsnaam extensie verwijderen</span><span class="sxs-lookup"><span data-stu-id="24662-112">Example 1: Delete files that have any file name extension</span></span>

<span data-ttu-id="24662-113">In dit voor beeld worden alle bestanden met namen die een punt ( `.` ) van de map bevatten verwijderd `C:\Test` .</span><span class="sxs-lookup"><span data-stu-id="24662-113">This example deletes all of the files that have names that include a dot (`.`) from the `C:\Test` folder.</span></span> <span data-ttu-id="24662-114">Omdat de opdracht een punt opgeeft, verwijdert de opdracht geen mappen of bestanden die geen bestandsnaam extensie hebben.</span><span class="sxs-lookup"><span data-stu-id="24662-114">Because the command specifies a dot, the command does not delete folders or files that have no file name extension.</span></span>

```powershell
Remove-Item C:\Test\*.*
```

### <span data-ttu-id="24662-115">Voor beeld 2: een aantal van de document bestanden in een map verwijderen</span><span class="sxs-lookup"><span data-stu-id="24662-115">Example 2: Delete some of the document files in a folder</span></span>

<span data-ttu-id="24662-116">In dit voor beeld worden alle bestanden die een `.doc` bestandsnaam extensie hebben en een naam die niet is inbegrepen, verwijderd uit de huidige map `*1*` .</span><span class="sxs-lookup"><span data-stu-id="24662-116">This example deletes from the current folder all files that have a `.doc` file name extension and a name that does not include `*1*`.</span></span>

```powershell
Remove-Item * -Include *.doc -Exclude *1*
```

<span data-ttu-id="24662-117">Het Joker teken () wordt gebruikt `*` om de inhoud van de huidige map op te geven.</span><span class="sxs-lookup"><span data-stu-id="24662-117">It uses the wildcard character (`*`) to specify the contents of the current folder.</span></span> <span data-ttu-id="24662-118">Hierbij worden de para meters **opnemen** en **uitsluiten** gebruikt om de bestanden op te geven die moeten worden verwijderd.</span><span class="sxs-lookup"><span data-stu-id="24662-118">It uses the **Include** and **Exclude** parameters to specify the files to delete.</span></span>

### <span data-ttu-id="24662-119">Voor beeld 3: verborgen, alleen-lezen bestanden verwijderen</span><span class="sxs-lookup"><span data-stu-id="24662-119">Example 3: Delete hidden, read-only files</span></span>

<span data-ttu-id="24662-120">Met deze opdracht wordt een bestand verwijderd dat zowel *verborgen* als *alleen-lezen* is.</span><span class="sxs-lookup"><span data-stu-id="24662-120">This command deletes a file that is both *hidden* and *read-only*.</span></span>

```powershell
Remove-Item -Path C:\Test\hidden-RO-file.txt -Force
```

<span data-ttu-id="24662-121">De para meter **Path** wordt gebruikt om het bestand op te geven.</span><span class="sxs-lookup"><span data-stu-id="24662-121">It uses the **Path** parameter to specify the file.</span></span> <span data-ttu-id="24662-122">De para meter **Force** wordt gebruikt om deze te verwijderen.</span><span class="sxs-lookup"><span data-stu-id="24662-122">It uses the **Force** parameter to delete it.</span></span> <span data-ttu-id="24662-123">Zonder **forceren** kunt u _alleen-lezen_ of _verborgen_ bestanden verwijderen.</span><span class="sxs-lookup"><span data-stu-id="24662-123">Without **Force**, you cannot delete _read-only_ or _hidden_ files.</span></span>

### <span data-ttu-id="24662-124">Voor beeld 4: bestanden in submappen recursief verwijderen</span><span class="sxs-lookup"><span data-stu-id="24662-124">Example 4: Delete files in subfolders recursively</span></span>

<span data-ttu-id="24662-125">Met deze opdracht worden alle CSV-bestanden in de huidige map en alle submappen recursief verwijderd.</span><span class="sxs-lookup"><span data-stu-id="24662-125">This command deletes all of the CSV files in the current folder and all subfolders recursively.</span></span>

<span data-ttu-id="24662-126">Omdat de **recursieve** para meter in `Remove-Item` een bekend probleem heeft, gebruikt de opdracht in dit voor beeld `Get-ChildItem` om de gewenste bestanden op te halen. vervolgens wordt de pijplijn operator gebruikt om deze door te geven aan `Remove-Item` .</span><span class="sxs-lookup"><span data-stu-id="24662-126">Because the **Recurse** parameter in `Remove-Item` has a known issue, the command in this example uses `Get-ChildItem` to get the desired files, and then uses the pipeline operator to pass them to `Remove-Item`.</span></span>

```powershell
Get-ChildItem * -Include *.csv -Recurse | Remove-Item
```

<span data-ttu-id="24662-127">In de `Get-ChildItem` opdracht heeft **Path** de waarde ( `*` ), die de inhoud van de huidige map vertegenwoordigt.</span><span class="sxs-lookup"><span data-stu-id="24662-127">In the `Get-ChildItem` command, **Path** has a value of (`*`), which represents the contents of the current folder.</span></span> <span data-ttu-id="24662-128">Het maakt **gebruik van** het BESTANDS type CSV en maakt gebruik van **recursie** om het ophalen te recursief maken.</span><span class="sxs-lookup"><span data-stu-id="24662-128">It uses **Include** to specify the CSV file type, and it uses **Recurse** to make the retrieval recursive.</span></span> <span data-ttu-id="24662-129">Als u het bestands type opgeeft, zoals, wordt door `-Path *.csv` de cmdlet het onderwerp van de zoek opdracht geïnterpreteerd als een bestand zonder onderliggende items en mislukt het opnieuw. </span><span class="sxs-lookup"><span data-stu-id="24662-129">If you try to specify the file type the path, such as `-Path *.csv`, the cmdlet interprets the subject of the search to be a file that has no child items, and **Recurse** fails.</span></span>

### <span data-ttu-id="24662-130">Voor beeld 5: subsleutels recursief verwijderen</span><span class="sxs-lookup"><span data-stu-id="24662-130">Example 5: Delete subkeys recursively</span></span>

<span data-ttu-id="24662-131">Met deze opdracht worden de register sleutel ' OldApp ' en alle bijbehorende subsleutels en waarden verwijderd.</span><span class="sxs-lookup"><span data-stu-id="24662-131">This command deletes the "OldApp" registry key and all its subkeys and values.</span></span> <span data-ttu-id="24662-132">`Remove-Item`De code wordt gebruikt om de sleutel te verwijderen.</span><span class="sxs-lookup"><span data-stu-id="24662-132">It uses `Remove-Item` to remove the key.</span></span> <span data-ttu-id="24662-133">Het pad is opgegeven, maar de optionele parameter naam (**pad**) wordt wegge laten.</span><span class="sxs-lookup"><span data-stu-id="24662-133">The path is specified, but the optional parameter name (**Path**) is omitted.</span></span>

<span data-ttu-id="24662-134">Met de **recursieve** para meter wordt alle inhoud van de sleutel ' OldApp ' recursief verwijderd.</span><span class="sxs-lookup"><span data-stu-id="24662-134">The **Recurse** parameter deletes all of the contents of the "OldApp" key recursively.</span></span> <span data-ttu-id="24662-135">Als de sleutel subsleutels bevat en u de para meter **recursief** weglaat, wordt u gevraagd om te bevestigen dat u de inhoud van de sleutel wilt verwijderen.</span><span class="sxs-lookup"><span data-stu-id="24662-135">If the key contains subkeys and you omit the **Recurse** parameter, you are prompted to confirm that you want to delete the contents of the key.</span></span>

```powershell
Remove-Item HKLM:\Software\MyCompany\OldApp -Recurse
```

### <span data-ttu-id="24662-136">Voor beeld 6: bestanden met speciale tekens verwijderen</span><span class="sxs-lookup"><span data-stu-id="24662-136">Example 6: Deleting files with special characters</span></span>

<span data-ttu-id="24662-137">In het volgende voor beeld ziet u hoe u bestanden verwijdert die speciale tekens bevatten, zoals haakjes of haakjes.</span><span class="sxs-lookup"><span data-stu-id="24662-137">The following example shows how to delete files that contain special characters like brackets or parentheses.</span></span>

```powershell
Get-ChildItem
```

```Output
    Directory: C:\temp\Downloads

Mode                LastWriteTime         Length Name
----                -------------         ------ ----
-a---          6/1/2018  12:19 PM           1362 myFile.txt
-a---          6/1/2018  12:30 PM           1132 myFile[1].txt
-a---          6/1/2018  12:19 PM           1283 myFile[2].txt
-a---          6/1/2018  12:19 PM           1432 myFile[3].txt

```

```powershell
Get-ChildItem | Where-Object Name -Like '*`[*'
```

```Output
    Directory: C:\temp\Downloads

Mode                LastWriteTime         Length Name
----                -------------         ------ ----
-a---          6/1/2018  12:30 PM           1132 myFile[1].txt
-a---          6/1/2018  12:19 PM           1283 myFile[2].txt
-a---          6/1/2018  12:19 PM           1432 myFile[3].txt

```

```powershell
Get-ChildItem | Where-Object Name -Like '*`[*' | ForEach-Object { Remove-Item -LiteralPath $_.Name }
Get-ChildItem
```

```Output
    Directory: C:\temp\Downloads

Mode                LastWriteTime         Length Name
----                -------------         ------ ----
-a---          6/1/2018  12:19 PM           1362 myFile.txt
```

### <span data-ttu-id="24662-138">Voor beeld 7: een alternatieve gegevens stroom verwijderen</span><span class="sxs-lookup"><span data-stu-id="24662-138">Example 7: Remove an alternate data stream</span></span>

<span data-ttu-id="24662-139">Dit voor beeld laat zien hoe u de dynamische **Stream** -para meter van de cmdlet kunt gebruiken `Remove-Item` om een alternatieve gegevens stroom te verwijderen.</span><span class="sxs-lookup"><span data-stu-id="24662-139">This example shows how to use the **Stream** dynamic parameter of the `Remove-Item` cmdlet to delete an alternate data stream.</span></span> <span data-ttu-id="24662-140">De stream-para meter is geïntroduceerd in Windows Power Shell 3,0.</span><span class="sxs-lookup"><span data-stu-id="24662-140">The stream parameter is introduced in Windows PowerShell 3.0.</span></span>

```powershell
Get-Item C:\Test\Copy-Script.ps1 -Stream Zone.Identifier
```

```Output
   FileName: \\C:\Test\Copy-Script.ps1

Stream                   Length
------                   ------
Zone.Identifier              26

```

```powershell
Remove-Item C:\Test\Copy-Script.ps1 -Stream Zone.Identifier
Get-Item C:\Test\Copy-Script.ps1 -Stream Zone.Identifier
```

```Output
Get-Item : Could not open alternate data stream 'Zone.Identifier' of file 'C:\Test\Copy-Script.ps1'.
At line:1 char:1
+ Get-Item 'C:\Test\Copy-Script.ps1' -Stream Zone.Identifier
+ [!INCLUDE[]()][!INCLUDE[]()][!INCLUDE[]()][!INCLUDE[]()][!INCLUDE[]()]~~
    + CategoryInfo          : ObjectNotFound: (C:\Test\Copy-Script.ps1:String) [Get-Item], FileNotFoundE
   xception
    + FullyQualifiedErrorId : AlternateDataStreamNotFound,Microsoft.PowerShell.Commands.GetItemCommand

```

<span data-ttu-id="24662-141">De **Stream** -para meter `Get-Item` haalt de **zone. id** -stroom van het `Copy-Script.ps1` bestand op.</span><span class="sxs-lookup"><span data-stu-id="24662-141">The **Stream** parameter `Get-Item` gets the **Zone.Identifier** stream of the `Copy-Script.ps1` file.</span></span> <span data-ttu-id="24662-142">`Remove-Item` maakt gebruik van de para meter **Stream** om de **zone. id** -stroom van het bestand te verwijderen.</span><span class="sxs-lookup"><span data-stu-id="24662-142">`Remove-Item` uses the **Stream** parameter to remove the **Zone.Identifier** stream of the file.</span></span> <span data-ttu-id="24662-143">Ten slotte `Get-Item` ziet de cmdlet dat de **zone. id** -stroom is verwijderd.</span><span class="sxs-lookup"><span data-stu-id="24662-143">Finally, the `Get-Item` cmdlet shows that the **Zone.Identifier** stream was deleted.</span></span>

## <span data-ttu-id="24662-144">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="24662-144">PARAMETERS</span></span>

### <span data-ttu-id="24662-145">-Credential</span><span class="sxs-lookup"><span data-stu-id="24662-145">-Credential</span></span>

> [!NOTE]
> <span data-ttu-id="24662-146">Deze para meter wordt niet ondersteund door providers die zijn geïnstalleerd met Power shell.</span><span class="sxs-lookup"><span data-stu-id="24662-146">This parameter is not supported by any providers installed with PowerShell.</span></span>
> <span data-ttu-id="24662-147">Gebruik [invoke-Command](../Microsoft.PowerShell.Core/Invoke-Command.md)om een andere gebruiker te imiteren of uw referenties te verhogen wanneer u deze cmdlet uitvoert.</span><span class="sxs-lookup"><span data-stu-id="24662-147">To impersonate another user, or elevate your credentials when running this cmdlet, use [Invoke-Command](../Microsoft.PowerShell.Core/Invoke-Command.md).</span></span>

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

### <span data-ttu-id="24662-148">-Uitsluiten</span><span class="sxs-lookup"><span data-stu-id="24662-148">-Exclude</span></span>

<span data-ttu-id="24662-149">Hiermee geeft u als een teken reeks matrix een item of items die met deze cmdlet worden uitgesloten in de bewerking.</span><span class="sxs-lookup"><span data-stu-id="24662-149">Specifies, as a string array, an item or items that this cmdlet excludes in the operation.</span></span> <span data-ttu-id="24662-150">De waarde van deze para meter komt in aanmerking voor de para meter **Path** .</span><span class="sxs-lookup"><span data-stu-id="24662-150">The value of this parameter qualifies the **Path** parameter.</span></span> <span data-ttu-id="24662-151">Voer een element of patroon van een pad in, zoals `*.txt` .</span><span class="sxs-lookup"><span data-stu-id="24662-151">Enter a path element or pattern, such as `*.txt`.</span></span> <span data-ttu-id="24662-152">Joker tekens zijn toegestaan.</span><span class="sxs-lookup"><span data-stu-id="24662-152">Wildcard characters are permitted.</span></span> <span data-ttu-id="24662-153">De **exclude** -para meter is alleen effectief wanneer de inhoud van een item wordt opgenomen, zoals `C:\Windows\*` , waarbij het Joker teken de inhoud van de `C:\Windows` map bevat.</span><span class="sxs-lookup"><span data-stu-id="24662-153">The **Exclude** parameter is effective only when the command includes the contents of an item, such as `C:\Windows\*`, where the wildcard character specifies the contents of the `C:\Windows` directory.</span></span>

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

### <span data-ttu-id="24662-154">-Filter</span><span class="sxs-lookup"><span data-stu-id="24662-154">-Filter</span></span>

<span data-ttu-id="24662-155">Hiermee geeft u een filter op om de para meter **Path** te kwalificeren.</span><span class="sxs-lookup"><span data-stu-id="24662-155">Specifies a filter to qualify the **Path** parameter.</span></span> <span data-ttu-id="24662-156">De [File System](../Microsoft.PowerShell.Core/About/about_FileSystem_Provider.md) -provider is de enige geïnstalleerde Power shell-provider die het gebruik van filters ondersteunt.</span><span class="sxs-lookup"><span data-stu-id="24662-156">The [FileSystem](../Microsoft.PowerShell.Core/About/about_FileSystem_Provider.md) provider is the only installed PowerShell provider that supports the use of filters.</span></span> <span data-ttu-id="24662-157">U kunt de syntaxis voor de filter taal van het **Bestands systeem** in [about_Wildcards](../Microsoft.PowerShell.Core/About/about_Wildcards.md)vinden.</span><span class="sxs-lookup"><span data-stu-id="24662-157">You can find the syntax for the **FileSystem** filter language in [about_Wildcards](../Microsoft.PowerShell.Core/About/about_Wildcards.md).</span></span>
<span data-ttu-id="24662-158">Filters zijn efficiënter dan andere para meters, omdat deze door de provider worden toegepast wanneer de cmdlet de objecten ophaalt in plaats van dat Power shell de objecten heeft gefilterd nadat ze zijn opgehaald.</span><span class="sxs-lookup"><span data-stu-id="24662-158">Filters are more efficient than other parameters, because the provider applies them when the cmdlet gets the objects rather than having PowerShell filter the objects after they are retrieved.</span></span>

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

### <span data-ttu-id="24662-159">-Force</span><span class="sxs-lookup"><span data-stu-id="24662-159">-Force</span></span>

<span data-ttu-id="24662-160">Hiermee wordt de cmdlet gedwongen om items te verwijderen die anders niet kunnen worden gewijzigd, zoals verborgen of alleen-lezen bestanden of alleen-lezen-aliassen of-variabelen.</span><span class="sxs-lookup"><span data-stu-id="24662-160">Forces the cmdlet to remove items that cannot otherwise be changed, such as hidden or read-only files or read-only aliases or variables.</span></span> <span data-ttu-id="24662-161">De cmdlet kan geen constante aliassen of variabelen verwijderen.</span><span class="sxs-lookup"><span data-stu-id="24662-161">The cmdlet cannot remove constant aliases or variables.</span></span>
<span data-ttu-id="24662-162">De implementatie varieert van provider tot provider.</span><span class="sxs-lookup"><span data-stu-id="24662-162">Implementation varies from provider to provider.</span></span> <span data-ttu-id="24662-163">Zie [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="24662-163">For more information, see [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md).</span></span> <span data-ttu-id="24662-164">Zelfs met behulp van de para meter **forceren** , kan de cmdlet geen beveiligings beperkingen opheffen.</span><span class="sxs-lookup"><span data-stu-id="24662-164">Even using the **Force** parameter, the cmdlet cannot override security restrictions.</span></span>

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

### <span data-ttu-id="24662-165">-Include</span><span class="sxs-lookup"><span data-stu-id="24662-165">-Include</span></span>

<span data-ttu-id="24662-166">Hiermee wordt een teken reeks matrix opgegeven, een item of items die met deze cmdlet in de bewerking zijn opgenomen.</span><span class="sxs-lookup"><span data-stu-id="24662-166">Specifies, as a string array, an item or items that this cmdlet includes in the operation.</span></span> <span data-ttu-id="24662-167">De waarde van deze para meter komt in aanmerking voor de para meter **Path** .</span><span class="sxs-lookup"><span data-stu-id="24662-167">The value of this parameter qualifies the **Path** parameter.</span></span> <span data-ttu-id="24662-168">Voer een element of patroon van een pad in, zoals `"*.txt"` .</span><span class="sxs-lookup"><span data-stu-id="24662-168">Enter a path element or pattern, such as `"*.txt"`.</span></span> <span data-ttu-id="24662-169">Joker tekens zijn toegestaan.</span><span class="sxs-lookup"><span data-stu-id="24662-169">Wildcard characters are permitted.</span></span> <span data-ttu-id="24662-170">De para meter **include** is alleen effectief wanneer de inhoud van een item wordt opgenomen, zoals `C:\Windows\*` , waarbij het Joker teken de inhoud van de `C:\Windows` map bevat.</span><span class="sxs-lookup"><span data-stu-id="24662-170">The **Include** parameter is effective only when the command includes the contents of an item, such as `C:\Windows\*`, where the wildcard character specifies the contents of the `C:\Windows` directory.</span></span>

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

### <span data-ttu-id="24662-171">-LiteralPath</span><span class="sxs-lookup"><span data-stu-id="24662-171">-LiteralPath</span></span>

<span data-ttu-id="24662-172">Hiermee geeft u een pad naar een of meer locaties.</span><span class="sxs-lookup"><span data-stu-id="24662-172">Specifies a path to one or more locations.</span></span> <span data-ttu-id="24662-173">De waarde van **LiteralPath** wordt precies zo gebruikt als deze wordt getypt.</span><span class="sxs-lookup"><span data-stu-id="24662-173">The value of **LiteralPath** is used exactly as it is typed.</span></span> <span data-ttu-id="24662-174">Geen tekens worden geïnterpreteerd als joker tekens.</span><span class="sxs-lookup"><span data-stu-id="24662-174">No characters are interpreted as wildcards.</span></span> <span data-ttu-id="24662-175">Als het pad escape tekens bevat, plaatst u het tussen enkele aanhalings tekens.</span><span class="sxs-lookup"><span data-stu-id="24662-175">If the path includes escape characters, enclose it in single quotation marks.</span></span> <span data-ttu-id="24662-176">Enkele aanhalings tekens geven aan dat Power shell geen karakters interpreteert als escape reeksen.</span><span class="sxs-lookup"><span data-stu-id="24662-176">Single quotation marks tell PowerShell not to interpret any characters as escape sequences.</span></span>

<span data-ttu-id="24662-177">Zie [about_Quoting_Rules](../Microsoft.Powershell.Core/About/about_Quoting_Rules.md)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="24662-177">For more information, see [about_Quoting_Rules](../Microsoft.Powershell.Core/About/about_Quoting_Rules.md).</span></span>

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

### <span data-ttu-id="24662-178">-Path</span><span class="sxs-lookup"><span data-stu-id="24662-178">-Path</span></span>

<span data-ttu-id="24662-179">Hiermee geeft u een pad op van de items die worden verwijderd.</span><span class="sxs-lookup"><span data-stu-id="24662-179">Specifies a path of the items being removed.</span></span>
<span data-ttu-id="24662-180">Joker tekens zijn toegestaan.</span><span class="sxs-lookup"><span data-stu-id="24662-180">Wildcard characters are permitted.</span></span>

```yaml
Type: System.String[]
Parameter Sets: Path
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: True
```

### <span data-ttu-id="24662-181">-Recursief</span><span class="sxs-lookup"><span data-stu-id="24662-181">-Recurse</span></span>

<span data-ttu-id="24662-182">Geeft aan dat met deze cmdlet de items in de opgegeven locaties en alle onderliggende items van de locaties worden verwijderd.</span><span class="sxs-lookup"><span data-stu-id="24662-182">Indicates that this cmdlet deletes the items in the specified locations and in all child items of the locations.</span></span>

<span data-ttu-id="24662-183">Als deze wordt gebruikt in combi natie met de para meter **include** , kunnen de **recursieve** para meter niet alle submappen of alle onderliggende items verwijderen.</span><span class="sxs-lookup"><span data-stu-id="24662-183">When it is used with the **Include** parameter, the **Recurse** parameter might not delete all subfolders or all child items.</span></span> <span data-ttu-id="24662-184">Dit is een bekend probleem.</span><span class="sxs-lookup"><span data-stu-id="24662-184">This is a known issue.</span></span> <span data-ttu-id="24662-185">Als tijdelijke oplossing kunt u de resultaten van de `Get-ChildItem -Recurse` opdracht Afdrukken naar `Remove-Item` , zoals beschreven in ' voor beeld 4 ' in dit onderwerp.</span><span class="sxs-lookup"><span data-stu-id="24662-185">As a workaround, try piping results of the `Get-ChildItem -Recurse` command to `Remove-Item`, as described in "Example 4" in this topic.</span></span>

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

### <span data-ttu-id="24662-186">-Stream</span><span class="sxs-lookup"><span data-stu-id="24662-186">-Stream</span></span>

<span data-ttu-id="24662-187">De **Stream** -para meter is een dynamische para meter waaraan de File System Provider toevoegt `Remove-Item` .</span><span class="sxs-lookup"><span data-stu-id="24662-187">The **Stream** parameter is a dynamic parameter that the FileSystem provider adds to `Remove-Item`.</span></span>
<span data-ttu-id="24662-188">Deze para meter werkt alleen op stations met een bestands systeem.</span><span class="sxs-lookup"><span data-stu-id="24662-188">This parameter works only in file system drives.</span></span>

<span data-ttu-id="24662-189">U kunt gebruiken `Remove-Item` om een alternatieve gegevens stroom te verwijderen.</span><span class="sxs-lookup"><span data-stu-id="24662-189">You can use `Remove-Item` to delete an alternative data stream.</span></span> <span data-ttu-id="24662-190">Het is echter niet de aanbevolen manier om beveiligings controles te elimineren waarmee bestanden die worden gedownload van Internet, worden geblokkeerd.</span><span class="sxs-lookup"><span data-stu-id="24662-190">However, it is not the recommended way to eliminate security checks that block files that are downloaded from the Internet.</span></span> <span data-ttu-id="24662-191">Als u controleert of een gedownload bestand veilig is, gebruikt u de `Unblock-File` cmdlet.</span><span class="sxs-lookup"><span data-stu-id="24662-191">If you verify that a downloaded file is safe, use the `Unblock-File` cmdlet.</span></span>

<span data-ttu-id="24662-192">Deze para meter is geïntroduceerd in Windows Power Shell 3,0.</span><span class="sxs-lookup"><span data-stu-id="24662-192">This parameter was introduced in Windows PowerShell 3.0.</span></span>

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

### <span data-ttu-id="24662-193">-Confirm</span><span class="sxs-lookup"><span data-stu-id="24662-193">-Confirm</span></span>

<span data-ttu-id="24662-194">Hiermee wordt u gevraagd om bevestiging voordat u de cmdlet uitvoert.</span><span class="sxs-lookup"><span data-stu-id="24662-194">Prompts you for confirmation before running the cmdlet.</span></span> <span data-ttu-id="24662-195">Raadpleeg voor meer informatie de volgende artikelen:</span><span class="sxs-lookup"><span data-stu-id="24662-195">For more information, see the following articles:</span></span>

- [<span data-ttu-id="24662-196">about_Preference_Variables</span><span class="sxs-lookup"><span data-stu-id="24662-196">about_Preference_Variables</span></span>](../microsoft.powershell.core/about/about_preference_variables.md#confirmpreference)
- [<span data-ttu-id="24662-197">about_Functions_CmdletBindingAttribute</span><span class="sxs-lookup"><span data-stu-id="24662-197">about_Functions_CmdletBindingAttribute</span></span>](../microsoft.powershell.core/about/about_functions_cmdletbindingattribute.md?#confirmimpact)

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

### <span data-ttu-id="24662-198">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="24662-198">-WhatIf</span></span>

<span data-ttu-id="24662-199">Hiermee wordt weergegeven wat er zou gebeuren als u de cmdlet uitvoert.</span><span class="sxs-lookup"><span data-stu-id="24662-199">Shows what would happen if the cmdlet runs.</span></span> <span data-ttu-id="24662-200">De cmdlet wordt niet uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="24662-200">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="24662-201">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="24662-201">CommonParameters</span></span>

<span data-ttu-id="24662-202">Deze cmdlet biedt ondersteuning voor de algemene para meters: `-Debug` , `-ErrorAction` , `-ErrorVariable` , `-InformationAction` , `-InformationVariable` , `-OutVariable` , `-OutBuffer` , `-PipelineVariable` , `-Verbose` , `-WarningAction` en `-WarningVariable` .</span><span class="sxs-lookup"><span data-stu-id="24662-202">This cmdlet supports the common parameters: `-Debug`, `-ErrorAction`, `-ErrorVariable`, `-InformationAction`, `-InformationVariable`, `-OutVariable`, `-OutBuffer`, `-PipelineVariable`, `-Verbose`, `-WarningAction`, and `-WarningVariable`.</span></span> <span data-ttu-id="24662-203">Zie [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="24662-203">For more information, see [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md).</span></span>

## <span data-ttu-id="24662-204">INVOER</span><span class="sxs-lookup"><span data-stu-id="24662-204">INPUTS</span></span>

### <span data-ttu-id="24662-205">System. String</span><span class="sxs-lookup"><span data-stu-id="24662-205">System.String</span></span>

<span data-ttu-id="24662-206">U kunt een teken reeks die een pad bevat, maar geen letterlijk pad, naar deze cmdlet pipet.</span><span class="sxs-lookup"><span data-stu-id="24662-206">You can pipe a string that contains a path, but not a literal path, to this cmdlet.</span></span>

## <span data-ttu-id="24662-207">UITVOER</span><span class="sxs-lookup"><span data-stu-id="24662-207">OUTPUTS</span></span>

### <span data-ttu-id="24662-208">Geen</span><span class="sxs-lookup"><span data-stu-id="24662-208">None</span></span>

<span data-ttu-id="24662-209">Met deze cmdlet wordt geen uitvoer geretourneerd.</span><span class="sxs-lookup"><span data-stu-id="24662-209">This cmdlet does not return any output.</span></span>

## <span data-ttu-id="24662-210">OPMERKINGEN</span><span class="sxs-lookup"><span data-stu-id="24662-210">NOTES</span></span>

<span data-ttu-id="24662-211">De `Remove-Item` cmdlet is ontworpen om te werken met de gegevens die door elke provider worden weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="24662-211">The `Remove-Item` cmdlet is designed to work with the data exposed by any provider.</span></span> <span data-ttu-id="24662-212">Als u een lijst wilt weer geven van de providers die beschikbaar zijn in uw sessie, typt u `Get-PsProvider` .</span><span class="sxs-lookup"><span data-stu-id="24662-212">To list the providers available in your session, type `Get-PsProvider`.</span></span> <span data-ttu-id="24662-213">Zie [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="24662-213">For more information, see [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md).</span></span>

<span data-ttu-id="24662-214">Wanneer u probeert een map te verwijderen die items bevat zonder de para meter **recursieve** te gebruiken, wordt door de cmdlet om bevestiging gevraagd.</span><span class="sxs-lookup"><span data-stu-id="24662-214">When you try to delete a folder that contains items without using the **Recurse** parameter, the cmdlet prompts for confirmation.</span></span> <span data-ttu-id="24662-215">Met behulp van `-Confirm:$false` wordt de prompt niet onderdrukt.</span><span class="sxs-lookup"><span data-stu-id="24662-215">Using `-Confirm:$false` does not suppress the prompt.</span></span> <span data-ttu-id="24662-216">Dit is standaard.</span><span class="sxs-lookup"><span data-stu-id="24662-216">This is by design.</span></span>

## <span data-ttu-id="24662-217">GERELATEERDE KOPPELINGEN</span><span class="sxs-lookup"><span data-stu-id="24662-217">RELATED LINKS</span></span>

[<span data-ttu-id="24662-218">Wissen-item</span><span class="sxs-lookup"><span data-stu-id="24662-218">Clear-Item</span></span>](Clear-Item.md)

[<span data-ttu-id="24662-219">Kopie-item</span><span class="sxs-lookup"><span data-stu-id="24662-219">Copy-Item</span></span>](Copy-Item.md)

[<span data-ttu-id="24662-220">Get-item</span><span class="sxs-lookup"><span data-stu-id="24662-220">Get-Item</span></span>](Get-Item.md)

[<span data-ttu-id="24662-221">Invoke-item</span><span class="sxs-lookup"><span data-stu-id="24662-221">Invoke-Item</span></span>](Invoke-Item.md)

[<span data-ttu-id="24662-222">Item verplaatsen</span><span class="sxs-lookup"><span data-stu-id="24662-222">Move-Item</span></span>](Move-Item.md)

[<span data-ttu-id="24662-223">Nieuw-item</span><span class="sxs-lookup"><span data-stu-id="24662-223">New-Item</span></span>](New-Item.md)

[<span data-ttu-id="24662-224">Verwijderen-item Property</span><span class="sxs-lookup"><span data-stu-id="24662-224">Remove-ItemProperty</span></span>](Remove-ItemProperty.md)

[<span data-ttu-id="24662-225">Naam wijzigen-item</span><span class="sxs-lookup"><span data-stu-id="24662-225">Rename-Item</span></span>](Rename-Item.md)

[<span data-ttu-id="24662-226">Set-item</span><span class="sxs-lookup"><span data-stu-id="24662-226">Set-Item</span></span>](Set-Item.md)

[<span data-ttu-id="24662-227">about_Providers</span><span class="sxs-lookup"><span data-stu-id="24662-227">about_Providers</span></span>](../Microsoft.PowerShell.Core/About/about_Providers.md)

[<span data-ttu-id="24662-228">about_Preference_Variables</span><span class="sxs-lookup"><span data-stu-id="24662-228">about_Preference_Variables</span></span>](../microsoft.powershell.core/about/about_preference_variables.md#confirmpreference)

[<span data-ttu-id="24662-229">about_Functions_CmdletBindingAttribute</span><span class="sxs-lookup"><span data-stu-id="24662-229">about_Functions_CmdletBindingAttribute</span></span>](../microsoft.powershell.core/about/about_functions_cmdletbindingattribute.md?#confirmimpact)

