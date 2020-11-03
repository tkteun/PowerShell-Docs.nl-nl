---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 10/03/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/rename-item?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Rename-Item
ms.openlocfilehash: 66a7b82b56028a4801a3aa8c93cd46460a5353ce
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/07/2020
ms.locfileid: "93250690"
---
# <span data-ttu-id="a3254-103">Rename-Item</span><span class="sxs-lookup"><span data-stu-id="a3254-103">Rename-Item</span></span>

## <span data-ttu-id="a3254-104">SAMENVATTING</span><span class="sxs-lookup"><span data-stu-id="a3254-104">SYNOPSIS</span></span>
<span data-ttu-id="a3254-105">De naam van een item in een Power shell-provider naam ruimte wordt gewijzigd.</span><span class="sxs-lookup"><span data-stu-id="a3254-105">Renames an item in a PowerShell provider namespace.</span></span>

## <span data-ttu-id="a3254-106">SYNTAXIS</span><span class="sxs-lookup"><span data-stu-id="a3254-106">SYNTAX</span></span>

### <span data-ttu-id="a3254-107">ByPath (standaard)</span><span class="sxs-lookup"><span data-stu-id="a3254-107">ByPath (Default)</span></span>

```
Rename-Item [-Path] <String> [-NewName] <String> [-Force] [-PassThru] [-Credential <PSCredential>]
 [-WhatIf] [-Confirm]  [<CommonParameters>]
```

### <span data-ttu-id="a3254-108">ByLiteralPath</span><span class="sxs-lookup"><span data-stu-id="a3254-108">ByLiteralPath</span></span>

```
Rename-Item -LiteralPath <String> [-NewName] <String> [-Force] [-PassThru]
 [-Credential <PSCredential>] [-WhatIf] [-Confirm]  [<CommonParameters>]
```

## <span data-ttu-id="a3254-109">BESCHRIJVING</span><span class="sxs-lookup"><span data-stu-id="a3254-109">DESCRIPTION</span></span>

<span data-ttu-id="a3254-110">`Rename-Item`Met de cmdlet wordt de naam van een opgegeven item gewijzigd.</span><span class="sxs-lookup"><span data-stu-id="a3254-110">The `Rename-Item` cmdlet changes the name of a specified item.</span></span> <span data-ttu-id="a3254-111">Deze cmdlet heeft geen invloed op de inhoud van het item waarvan de naam wordt gewijzigd.</span><span class="sxs-lookup"><span data-stu-id="a3254-111">This cmdlet does not affect the content of the item being renamed.</span></span>

<span data-ttu-id="a3254-112">U kunt niet gebruiken `Rename-Item` om een item te verplaatsen, bijvoorbeeld door een pad op te geven in combi natie met de nieuwe naam.</span><span class="sxs-lookup"><span data-stu-id="a3254-112">You can't use `Rename-Item` to move an item, such as by specifying a path together with the new name.</span></span> <span data-ttu-id="a3254-113">Als u een item wilt verplaatsen en de naam ervan wilt wijzigen, gebruikt u de `Move-Item` cmdlet.</span><span class="sxs-lookup"><span data-stu-id="a3254-113">To move and rename an item, use the `Move-Item` cmdlet.</span></span>

## <span data-ttu-id="a3254-114">VOORBEELDEN</span><span class="sxs-lookup"><span data-stu-id="a3254-114">EXAMPLES</span></span>

### <span data-ttu-id="a3254-115">Voor beeld 1: de naam van een bestand wijzigen</span><span class="sxs-lookup"><span data-stu-id="a3254-115">Example 1: Rename a file</span></span>

<span data-ttu-id="a3254-116">Met deze opdracht wordt de naam van het bestand gewijzigd `daily_file.txt` in `monday_file.txt` .</span><span class="sxs-lookup"><span data-stu-id="a3254-116">This command renames the file `daily_file.txt` to `monday_file.txt`.</span></span>

```powershell
Rename-Item -Path "c:\logfiles\daily_file.txt" -NewName "monday_file.txt"
```

### <span data-ttu-id="a3254-117">Voor beeld 2: een item een andere naam geven en verplaatsen</span><span class="sxs-lookup"><span data-stu-id="a3254-117">Example 2: Rename and move an item</span></span>

<span data-ttu-id="a3254-118">U kunt niet gebruiken `Rename-Item` om een item een andere naam te geven en te verplaatsen.</span><span class="sxs-lookup"><span data-stu-id="a3254-118">You can't use `Rename-Item` to both rename and move an item.</span></span> <span data-ttu-id="a3254-119">U kunt met name geen pad opgeven voor de waarde van de para meter **newname** , tenzij het pad identiek is aan het pad dat is opgegeven in de para meter **Path** .</span><span class="sxs-lookup"><span data-stu-id="a3254-119">Specifically, you can't supply a path for the value of the **NewName** parameter, unless the path is identical to the path specified in the **Path** parameter.</span></span> <span data-ttu-id="a3254-120">Anders is alleen een nieuwe naam toegestaan.</span><span class="sxs-lookup"><span data-stu-id="a3254-120">Otherwise, only a new name is permitted.</span></span>

<span data-ttu-id="a3254-121">In dit voor beeld wordt geprobeerd om de naam van het `project.txt` bestand in de huidige map in `old-project.txt` de map te wijzigen `D:\Archive` .</span><span class="sxs-lookup"><span data-stu-id="a3254-121">This example attempts to rename the `project.txt` file in the current directory to `old-project.txt` in the `D:\Archive` directory.</span></span> <span data-ttu-id="a3254-122">Het resultaat is de fout die wordt weer gegeven in de uitvoer.</span><span class="sxs-lookup"><span data-stu-id="a3254-122">The result is the error shown in the output.</span></span>

```powershell
Rename-Item -Path "project.txt" -NewName "d:\archive\old-project.txt"
```

```Output
Rename-Item : can't rename because the target specified represents a path or device name.
At line:1 char:12
+ Rename-Item <<<<  -path project.txt -NewName d:\archive\old-project.txt
+ CategoryInfo          : InvalidArgument: (:) [Rename-Item], PS>  Move-Item -Path "project.txt" -De
stination "d:\archive\old-project.txt"
```

### <span data-ttu-id="a3254-123">Voor beeld 3: de naam van een register sleutel wijzigen</span><span class="sxs-lookup"><span data-stu-id="a3254-123">Example 3: Rename a registry key</span></span>

<span data-ttu-id="a3254-124">In dit voor beeld wordt de naam van een register sleutel gewijzigd van **adverteren** in **marketing**.</span><span class="sxs-lookup"><span data-stu-id="a3254-124">This example renames a registry key from **Advertising** to **Marketing**.</span></span> <span data-ttu-id="a3254-125">Wanneer de opdracht is voltooid, wordt de naam van de sleutel gewijzigd, maar de Register vermeldingen in de sleutel blijven onveranderd.</span><span class="sxs-lookup"><span data-stu-id="a3254-125">When the command is complete, the key is renamed, but the registry entries in the key are unchanged.</span></span>

```powershell
Rename-Item -Path "HKLM:\Software\MyCompany\Advertising" -NewName "Marketing"
```

### <span data-ttu-id="a3254-126">Voor beeld 4: de naam van meerdere bestanden wijzigen</span><span class="sxs-lookup"><span data-stu-id="a3254-126">Example 4: Rename multiple files</span></span>

<span data-ttu-id="a3254-127">In dit voor beeld worden de namen `*.txt` van alle bestanden in de huidige map gewijzigd in `*.log` .</span><span class="sxs-lookup"><span data-stu-id="a3254-127">This example renames all the `*.txt` files in the current directory to `*.log`.</span></span>

```powershell
Get-ChildItem *.txt
```

```Output
    Directory: C:\temp\files

Mode                LastWriteTime         Length Name
----                -------------         ------ ----
-a----        10/3/2019   7:47 AM           2918 Friday.TXT
-a----        10/3/2019   7:46 AM           2918 Monday.Txt
-a----        10/3/2019   7:47 AM           2918 Wednesday.txt
```

```powershell
Get-ChildItem *.txt | Rename-Item -NewName { $_.Name -replace '.txt','.log' }
Get-ChildItem *.log
```

```Output
    Directory: C:\temp\files

Mode                LastWriteTime         Length Name
----                -------------         ------ ----
-a----        10/3/2019   7:47 AM           2918 Friday.log
-a----        10/3/2019   7:46 AM           2918 Monday.log
-a----        10/3/2019   7:47 AM           2918 Wednesday.log
```

<span data-ttu-id="a3254-128">Met de `Get-ChildItem` cmdlet worden alle bestanden in de huidige map met een `.txt` bestands extensie opgehaald `Rename-Item` .</span><span class="sxs-lookup"><span data-stu-id="a3254-128">The `Get-ChildItem` cmdlet gets all the files in the current folder that have a `.txt` file extension then pipes them to `Rename-Item`.</span></span> <span data-ttu-id="a3254-129">De waarde van **newname** is een script blok dat wordt uitgevoerd voordat de waarde wordt verzonden naar de para meter **newname** .</span><span class="sxs-lookup"><span data-stu-id="a3254-129">The value of **NewName** is a script block that runs before the value is submitted to the **NewName** parameter.</span></span>

<span data-ttu-id="a3254-130">In het-script blok `$_` stelt de automatische variabele elk bestands object voor, zoals het via de pijp lijn naar de opdracht wordt geleverd.</span><span class="sxs-lookup"><span data-stu-id="a3254-130">In the script block, the `$_` automatic variable represents each file object as it comes to the command through the pipeline.</span></span> <span data-ttu-id="a3254-131">Het script blok gebruikt de `-replace` operator om de bestands extensie van elk bestand te vervangen door `.log` .</span><span class="sxs-lookup"><span data-stu-id="a3254-131">The script block uses the `-replace` operator to replace the file extension of each file with `.log`.</span></span> <span data-ttu-id="a3254-132">U ziet dat het vergelijken met behulp van de `-replace` operator niet hoofdletter gevoelig is.</span><span class="sxs-lookup"><span data-stu-id="a3254-132">Notice that matching using the `-replace` operator is not case sensitive.</span></span>

## <span data-ttu-id="a3254-133">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="a3254-133">PARAMETERS</span></span>

### <span data-ttu-id="a3254-134">-Credential</span><span class="sxs-lookup"><span data-stu-id="a3254-134">-Credential</span></span>

> [!NOTE]
> <span data-ttu-id="a3254-135">Deze para meter wordt niet ondersteund door providers die zijn geïnstalleerd met Power shell.</span><span class="sxs-lookup"><span data-stu-id="a3254-135">This parameter is not supported by any providers installed with PowerShell.</span></span> <span data-ttu-id="a3254-136">Gebruik [invoke-Command](../Microsoft.PowerShell.Core/Invoke-Command.md)om een andere gebruiker te imiteren of uw referenties te verhogen wanneer u deze cmdlet uitvoert.</span><span class="sxs-lookup"><span data-stu-id="a3254-136">To impersonate another user, or elevate your credentials when running this cmdlet, use [Invoke-Command](../Microsoft.PowerShell.Core/Invoke-Command.md).</span></span>

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

### <span data-ttu-id="a3254-137">-Force</span><span class="sxs-lookup"><span data-stu-id="a3254-137">-Force</span></span>

<span data-ttu-id="a3254-138">Hiermee wordt de naam van items die niet kunnen worden gewijzigd, zoals verborgen of alleen-lezen bestanden of alleen-lezen-aliassen of-variabelen, door de cmdlet geforceerd.</span><span class="sxs-lookup"><span data-stu-id="a3254-138">Forces the cmdlet to rename items that can't otherwise be changed, such as hidden or read-only files or read-only aliases or variables.</span></span> <span data-ttu-id="a3254-139">De cmdlet kan geen constante aliassen of variabelen wijzigen.</span><span class="sxs-lookup"><span data-stu-id="a3254-139">The cmdlet can't change constant aliases or variables.</span></span>
<span data-ttu-id="a3254-140">De implementatie varieert van provider tot provider.</span><span class="sxs-lookup"><span data-stu-id="a3254-140">Implementation varies from provider to provider.</span></span> <span data-ttu-id="a3254-141">Zie [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="a3254-141">For more information, see [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md).</span></span>

<span data-ttu-id="a3254-142">Zelfs met behulp van de para meter **forceren** , kunnen de cmdlet geen beveiligings beperkingen opheffen.</span><span class="sxs-lookup"><span data-stu-id="a3254-142">Even using the **Force** parameter, the cmdlet can't override security restrictions.</span></span>

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

### <span data-ttu-id="a3254-143">-LiteralPath</span><span class="sxs-lookup"><span data-stu-id="a3254-143">-LiteralPath</span></span>

<span data-ttu-id="a3254-144">Hiermee geeft u een pad naar een of meer locaties.</span><span class="sxs-lookup"><span data-stu-id="a3254-144">Specifies a path to one or more locations.</span></span> <span data-ttu-id="a3254-145">De waarde van **LiteralPath** wordt precies zo gebruikt als deze wordt getypt.</span><span class="sxs-lookup"><span data-stu-id="a3254-145">The value of **LiteralPath** is used exactly as it is typed.</span></span> <span data-ttu-id="a3254-146">Geen tekens worden geïnterpreteerd als joker tekens.</span><span class="sxs-lookup"><span data-stu-id="a3254-146">No characters are interpreted as wildcards.</span></span> <span data-ttu-id="a3254-147">Als het pad escape tekens bevat, plaatst u het tussen enkele aanhalings tekens.</span><span class="sxs-lookup"><span data-stu-id="a3254-147">If the path includes escape characters, enclose it in single quotation marks.</span></span> <span data-ttu-id="a3254-148">Enkele aanhalings tekens geven aan dat Power shell geen karakters interpreteert als escape reeksen.</span><span class="sxs-lookup"><span data-stu-id="a3254-148">Single quotation marks tell PowerShell not to interpret any characters as escape sequences.</span></span>

<span data-ttu-id="a3254-149">Zie [about_Quoting_Rules](../Microsoft.Powershell.Core/About/about_Quoting_Rules.md)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="a3254-149">For more information, see [about_Quoting_Rules](../Microsoft.Powershell.Core/About/about_Quoting_Rules.md).</span></span>

```yaml
Type: System.String
Parameter Sets: ByLiteralPath
Aliases: PSPath, LP

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="a3254-150">-NewName</span><span class="sxs-lookup"><span data-stu-id="a3254-150">-NewName</span></span>

<span data-ttu-id="a3254-151">Hiermee geeft u de nieuwe naam van het item.</span><span class="sxs-lookup"><span data-stu-id="a3254-151">Specifies the new name of the item.</span></span> <span data-ttu-id="a3254-152">Voer alleen een naam in, geen pad en naam.</span><span class="sxs-lookup"><span data-stu-id="a3254-152">Enter only a name, not a path and name.</span></span> <span data-ttu-id="a3254-153">Als u een pad opgeeft dat verschilt van het pad dat is opgegeven in de para meter **Path** , wordt `Rename-Item` een fout gegenereerd.</span><span class="sxs-lookup"><span data-stu-id="a3254-153">If you enter a path that differs from the path that is specified in the **Path** parameter, `Rename-Item` generates an error.</span></span>
<span data-ttu-id="a3254-154">Gebruik om een item een andere naam te geven en te verplaatsen `Move-Item` .</span><span class="sxs-lookup"><span data-stu-id="a3254-154">To rename and move an item, use `Move-Item`.</span></span>

<span data-ttu-id="a3254-155">U kunt geen joker tekens gebruiken in de waarde van de para meter **newname** .</span><span class="sxs-lookup"><span data-stu-id="a3254-155">You can't use wildcard characters in the value of the **NewName** parameter.</span></span> <span data-ttu-id="a3254-156">Als u een naam voor meerdere bestanden wilt opgeven, gebruikt u de operator **replace** in een reguliere expressie.</span><span class="sxs-lookup"><span data-stu-id="a3254-156">To specify a name for multiple files, use the **Replace** operator in a regular expression.</span></span> <span data-ttu-id="a3254-157">Zie [about_Comparison_Operators](../Microsoft.PowerShell.Core/About/about_Comparison_Operators.md)voor meer informatie over de operator vervangen.</span><span class="sxs-lookup"><span data-stu-id="a3254-157">For more information about the Replace operator, see [about_Comparison_Operators](../Microsoft.PowerShell.Core/About/about_Comparison_Operators.md).</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: True
Position: 1
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="a3254-158">-PassThru</span><span class="sxs-lookup"><span data-stu-id="a3254-158">-PassThru</span></span>

<span data-ttu-id="a3254-159">Retourneert een object dat het item voor de pijp lijn vertegenwoordigt.</span><span class="sxs-lookup"><span data-stu-id="a3254-159">Returns an object that represents the item to the pipeline.</span></span> <span data-ttu-id="a3254-160">Deze cmdlet genereert standaard geen uitvoer.</span><span class="sxs-lookup"><span data-stu-id="a3254-160">By default, this cmdlet does not generate any output.</span></span>

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

### <span data-ttu-id="a3254-161">-Path</span><span class="sxs-lookup"><span data-stu-id="a3254-161">-Path</span></span>

<span data-ttu-id="a3254-162">Hiermee geeft u het pad op van het item waarvan u de naam wilt wijzigen.</span><span class="sxs-lookup"><span data-stu-id="a3254-162">Specifies the path of the item to rename.</span></span>

```yaml
Type: System.String
Parameter Sets: ByPath
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="a3254-163">-Confirm</span><span class="sxs-lookup"><span data-stu-id="a3254-163">-Confirm</span></span>

<span data-ttu-id="a3254-164">Hiermee wordt u gevraagd om bevestiging voordat u de cmdlet uitvoert.</span><span class="sxs-lookup"><span data-stu-id="a3254-164">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="a3254-165">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="a3254-165">-WhatIf</span></span>

<span data-ttu-id="a3254-166">Hiermee wordt weergegeven wat er zou gebeuren als u de cmdlet uitvoert.</span><span class="sxs-lookup"><span data-stu-id="a3254-166">Shows what would happen if the cmdlet runs.</span></span>
<span data-ttu-id="a3254-167">De cmdlet wordt niet uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="a3254-167">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="a3254-168">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="a3254-168">CommonParameters</span></span>

<span data-ttu-id="a3254-169">Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="a3254-169">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="a3254-170">Zie [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="a3254-170">For more information, see [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md).</span></span>

## <span data-ttu-id="a3254-171">INVOER</span><span class="sxs-lookup"><span data-stu-id="a3254-171">INPUTS</span></span>

### <span data-ttu-id="a3254-172">System. String</span><span class="sxs-lookup"><span data-stu-id="a3254-172">System.String</span></span>

<span data-ttu-id="a3254-173">U kunt een teken reeks met een pad naar deze cmdlet door sluizen.</span><span class="sxs-lookup"><span data-stu-id="a3254-173">You can pipe a string that contains a path to this cmdlet.</span></span>

## <span data-ttu-id="a3254-174">UITVOER</span><span class="sxs-lookup"><span data-stu-id="a3254-174">OUTPUTS</span></span>

### <span data-ttu-id="a3254-175">Geen of een object dat het hernoemde item vertegenwoordigt.</span><span class="sxs-lookup"><span data-stu-id="a3254-175">None or an object that represents the renamed item.</span></span>

<span data-ttu-id="a3254-176">Met deze cmdlet wordt een object gegenereerd dat het hernoemde item vertegenwoordigt, als u de para meter **PassThru** opgeeft.</span><span class="sxs-lookup"><span data-stu-id="a3254-176">This cmdlet generates an object that represents the renamed item, if you specify the **PassThru** parameter.</span></span> <span data-ttu-id="a3254-177">Anders wordt met deze cmdlet geen uitvoer gegenereerd.</span><span class="sxs-lookup"><span data-stu-id="a3254-177">Otherwise, this cmdlet does not generate any output.</span></span>

## <span data-ttu-id="a3254-178">OPMERKINGEN</span><span class="sxs-lookup"><span data-stu-id="a3254-178">NOTES</span></span>

<span data-ttu-id="a3254-179">`Rename-Item` is ontworpen om te werken met de gegevens die door elke provider worden weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="a3254-179">`Rename-Item` is designed to work with the data exposed by any provider.</span></span> <span data-ttu-id="a3254-180">Als u een lijst wilt weer geven van de providers die beschikbaar zijn in uw sessie, typt u `Get-PsProvider` .</span><span class="sxs-lookup"><span data-stu-id="a3254-180">To list the providers available in your session, type `Get-PsProvider`.</span></span> <span data-ttu-id="a3254-181">Zie [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="a3254-181">For more information, see [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md).</span></span>

## <span data-ttu-id="a3254-182">GERELATEERDE KOPPELINGEN</span><span class="sxs-lookup"><span data-stu-id="a3254-182">RELATED LINKS</span></span>

[<span data-ttu-id="a3254-183">Wissen-item</span><span class="sxs-lookup"><span data-stu-id="a3254-183">Clear-Item</span></span>](Clear-Item.md)

[<span data-ttu-id="a3254-184">Kopie-item</span><span class="sxs-lookup"><span data-stu-id="a3254-184">Copy-Item</span></span>](Copy-Item.md)

[<span data-ttu-id="a3254-185">Get-Child item</span><span class="sxs-lookup"><span data-stu-id="a3254-185">Get-ChildItem</span></span>](Get-ChildItem.md)

[<span data-ttu-id="a3254-186">Get-item</span><span class="sxs-lookup"><span data-stu-id="a3254-186">Get-Item</span></span>](Get-Item.md)

[<span data-ttu-id="a3254-187">Invoke-item</span><span class="sxs-lookup"><span data-stu-id="a3254-187">Invoke-Item</span></span>](Invoke-Item.md)

[<span data-ttu-id="a3254-188">Item verplaatsen</span><span class="sxs-lookup"><span data-stu-id="a3254-188">Move-Item</span></span>](Move-Item.md)

[<span data-ttu-id="a3254-189">Nieuw-item</span><span class="sxs-lookup"><span data-stu-id="a3254-189">New-Item</span></span>](New-Item.md)

[<span data-ttu-id="a3254-190">Verwijderen-item</span><span class="sxs-lookup"><span data-stu-id="a3254-190">Remove-Item</span></span>](Remove-Item.md)

[<span data-ttu-id="a3254-191">Naam wijzigen-item Property</span><span class="sxs-lookup"><span data-stu-id="a3254-191">Rename-ItemProperty</span></span>](Rename-ItemProperty.md)

[<span data-ttu-id="a3254-192">Set-item</span><span class="sxs-lookup"><span data-stu-id="a3254-192">Set-Item</span></span>](Set-Item.md)

[<span data-ttu-id="a3254-193">about_Providers</span><span class="sxs-lookup"><span data-stu-id="a3254-193">about_Providers</span></span>](../Microsoft.PowerShell.Core/About/about_Providers.md)
