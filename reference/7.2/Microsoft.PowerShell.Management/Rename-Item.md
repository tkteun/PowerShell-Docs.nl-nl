---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 10/03/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/rename-item?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Rename-Item
ms.openlocfilehash: dec5c2c905486110e4885f29d236ab41d945fb96
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 11/17/2020
ms.locfileid: "94705876"
---
# <span data-ttu-id="08274-102">Rename-Item</span><span class="sxs-lookup"><span data-stu-id="08274-102">Rename-Item</span></span>

## <span data-ttu-id="08274-103">SAMENVATTING</span><span class="sxs-lookup"><span data-stu-id="08274-103">SYNOPSIS</span></span>
<span data-ttu-id="08274-104">De naam van een item in een Power shell-provider naam ruimte wordt gewijzigd.</span><span class="sxs-lookup"><span data-stu-id="08274-104">Renames an item in a PowerShell provider namespace.</span></span>

## <span data-ttu-id="08274-105">SYNTAXIS</span><span class="sxs-lookup"><span data-stu-id="08274-105">SYNTAX</span></span>

### <span data-ttu-id="08274-106">ByPath (standaard)</span><span class="sxs-lookup"><span data-stu-id="08274-106">ByPath (Default)</span></span>

```
Rename-Item [-Path] <String> [-NewName] <String> [-Force] [-PassThru] [-Credential <PSCredential>]
 [-WhatIf] [-Confirm]  [<CommonParameters>]
```

### <span data-ttu-id="08274-107">ByLiteralPath</span><span class="sxs-lookup"><span data-stu-id="08274-107">ByLiteralPath</span></span>

```
Rename-Item -LiteralPath <String> [-NewName] <String> [-Force] [-PassThru]
 [-Credential <PSCredential>] [-WhatIf] [-Confirm]  [<CommonParameters>]
```

## <span data-ttu-id="08274-108">BESCHRIJVING</span><span class="sxs-lookup"><span data-stu-id="08274-108">DESCRIPTION</span></span>

<span data-ttu-id="08274-109">`Rename-Item`Met de cmdlet wordt de naam van een opgegeven item gewijzigd.</span><span class="sxs-lookup"><span data-stu-id="08274-109">The `Rename-Item` cmdlet changes the name of a specified item.</span></span> <span data-ttu-id="08274-110">Deze cmdlet heeft geen invloed op de inhoud van het item waarvan de naam wordt gewijzigd.</span><span class="sxs-lookup"><span data-stu-id="08274-110">This cmdlet does not affect the content of the item being renamed.</span></span>

<span data-ttu-id="08274-111">U kunt niet gebruiken `Rename-Item` om een item te verplaatsen, bijvoorbeeld door een pad op te geven in combi natie met de nieuwe naam.</span><span class="sxs-lookup"><span data-stu-id="08274-111">You can't use `Rename-Item` to move an item, such as by specifying a path together with the new name.</span></span> <span data-ttu-id="08274-112">Als u een item wilt verplaatsen en de naam ervan wilt wijzigen, gebruikt u de `Move-Item` cmdlet.</span><span class="sxs-lookup"><span data-stu-id="08274-112">To move and rename an item, use the `Move-Item` cmdlet.</span></span>

## <span data-ttu-id="08274-113">VOORBEELDEN</span><span class="sxs-lookup"><span data-stu-id="08274-113">EXAMPLES</span></span>

### <span data-ttu-id="08274-114">Voor beeld 1: de naam van een bestand wijzigen</span><span class="sxs-lookup"><span data-stu-id="08274-114">Example 1: Rename a file</span></span>

<span data-ttu-id="08274-115">Met deze opdracht wordt de naam van het bestand gewijzigd `daily_file.txt` in `monday_file.txt` .</span><span class="sxs-lookup"><span data-stu-id="08274-115">This command renames the file `daily_file.txt` to `monday_file.txt`.</span></span>

```powershell
Rename-Item -Path "c:\logfiles\daily_file.txt" -NewName "monday_file.txt"
```

### <span data-ttu-id="08274-116">Voor beeld 2: een item een andere naam geven en verplaatsen</span><span class="sxs-lookup"><span data-stu-id="08274-116">Example 2: Rename and move an item</span></span>

<span data-ttu-id="08274-117">U kunt niet gebruiken `Rename-Item` om een item een andere naam te geven en te verplaatsen.</span><span class="sxs-lookup"><span data-stu-id="08274-117">You can't use `Rename-Item` to both rename and move an item.</span></span> <span data-ttu-id="08274-118">U kunt met name geen pad opgeven voor de waarde van de para meter **newname** , tenzij het pad identiek is aan het pad dat is opgegeven in de para meter **Path** .</span><span class="sxs-lookup"><span data-stu-id="08274-118">Specifically, you can't supply a path for the value of the **NewName** parameter, unless the path is identical to the path specified in the **Path** parameter.</span></span> <span data-ttu-id="08274-119">Anders is alleen een nieuwe naam toegestaan.</span><span class="sxs-lookup"><span data-stu-id="08274-119">Otherwise, only a new name is permitted.</span></span>

<span data-ttu-id="08274-120">In dit voor beeld wordt geprobeerd om de naam van het `project.txt` bestand in de huidige map in `old-project.txt` de map te wijzigen `D:\Archive` .</span><span class="sxs-lookup"><span data-stu-id="08274-120">This example attempts to rename the `project.txt` file in the current directory to `old-project.txt` in the `D:\Archive` directory.</span></span> <span data-ttu-id="08274-121">Het resultaat is de fout die wordt weer gegeven in de uitvoer.</span><span class="sxs-lookup"><span data-stu-id="08274-121">The result is the error shown in the output.</span></span>

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

### <span data-ttu-id="08274-122">Voor beeld 3: de naam van een register sleutel wijzigen</span><span class="sxs-lookup"><span data-stu-id="08274-122">Example 3: Rename a registry key</span></span>

<span data-ttu-id="08274-123">In dit voor beeld wordt de naam van een register sleutel gewijzigd van **adverteren** in **marketing**.</span><span class="sxs-lookup"><span data-stu-id="08274-123">This example renames a registry key from **Advertising** to **Marketing**.</span></span> <span data-ttu-id="08274-124">Wanneer de opdracht is voltooid, wordt de naam van de sleutel gewijzigd, maar de Register vermeldingen in de sleutel blijven onveranderd.</span><span class="sxs-lookup"><span data-stu-id="08274-124">When the command is complete, the key is renamed, but the registry entries in the key are unchanged.</span></span>

```powershell
Rename-Item -Path "HKLM:\Software\MyCompany\Advertising" -NewName "Marketing"
```

### <span data-ttu-id="08274-125">Voor beeld 4: de naam van meerdere bestanden wijzigen</span><span class="sxs-lookup"><span data-stu-id="08274-125">Example 4: Rename multiple files</span></span>

<span data-ttu-id="08274-126">In dit voor beeld worden de namen `*.txt` van alle bestanden in de huidige map gewijzigd in `*.log` .</span><span class="sxs-lookup"><span data-stu-id="08274-126">This example renames all the `*.txt` files in the current directory to `*.log`.</span></span>

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

<span data-ttu-id="08274-127">Met de `Get-ChildItem` cmdlet worden alle bestanden in de huidige map met een `.txt` bestands extensie opgehaald `Rename-Item` .</span><span class="sxs-lookup"><span data-stu-id="08274-127">The `Get-ChildItem` cmdlet gets all the files in the current folder that have a `.txt` file extension then pipes them to `Rename-Item`.</span></span> <span data-ttu-id="08274-128">De waarde van **newname** is een script blok dat wordt uitgevoerd voordat de waarde wordt verzonden naar de para meter **newname** .</span><span class="sxs-lookup"><span data-stu-id="08274-128">The value of **NewName** is a script block that runs before the value is submitted to the **NewName** parameter.</span></span>

<span data-ttu-id="08274-129">In het-script blok `$_` stelt de automatische variabele elk bestands object voor, zoals het via de pijp lijn naar de opdracht wordt geleverd.</span><span class="sxs-lookup"><span data-stu-id="08274-129">In the script block, the `$_` automatic variable represents each file object as it comes to the command through the pipeline.</span></span> <span data-ttu-id="08274-130">Het script blok gebruikt de `-replace` operator om de bestands extensie van elk bestand te vervangen door `.log` .</span><span class="sxs-lookup"><span data-stu-id="08274-130">The script block uses the `-replace` operator to replace the file extension of each file with `.log`.</span></span> <span data-ttu-id="08274-131">U ziet dat het vergelijken met behulp van de `-replace` operator niet hoofdletter gevoelig is.</span><span class="sxs-lookup"><span data-stu-id="08274-131">Notice that matching using the `-replace` operator is not case sensitive.</span></span>

## <span data-ttu-id="08274-132">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="08274-132">PARAMETERS</span></span>

### <span data-ttu-id="08274-133">-Credential</span><span class="sxs-lookup"><span data-stu-id="08274-133">-Credential</span></span>

> [!NOTE]
> <span data-ttu-id="08274-134">Deze para meter wordt niet ondersteund door providers die zijn geïnstalleerd met Power shell.</span><span class="sxs-lookup"><span data-stu-id="08274-134">This parameter is not supported by any providers installed with PowerShell.</span></span> <span data-ttu-id="08274-135">Gebruik [invoke-Command](../Microsoft.PowerShell.Core/Invoke-Command.md)om een andere gebruiker te imiteren of uw referenties te verhogen wanneer u deze cmdlet uitvoert.</span><span class="sxs-lookup"><span data-stu-id="08274-135">To impersonate another user, or elevate your credentials when running this cmdlet, use [Invoke-Command](../Microsoft.PowerShell.Core/Invoke-Command.md).</span></span>

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

### <span data-ttu-id="08274-136">-Force</span><span class="sxs-lookup"><span data-stu-id="08274-136">-Force</span></span>

<span data-ttu-id="08274-137">Hiermee wordt de naam van items die niet kunnen worden gewijzigd, zoals verborgen of alleen-lezen bestanden of alleen-lezen-aliassen of-variabelen, door de cmdlet geforceerd.</span><span class="sxs-lookup"><span data-stu-id="08274-137">Forces the cmdlet to rename items that can't otherwise be changed, such as hidden or read-only files or read-only aliases or variables.</span></span> <span data-ttu-id="08274-138">De cmdlet kan geen constante aliassen of variabelen wijzigen.</span><span class="sxs-lookup"><span data-stu-id="08274-138">The cmdlet can't change constant aliases or variables.</span></span>
<span data-ttu-id="08274-139">De implementatie varieert van provider tot provider.</span><span class="sxs-lookup"><span data-stu-id="08274-139">Implementation varies from provider to provider.</span></span> <span data-ttu-id="08274-140">Zie [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="08274-140">For more information, see [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md).</span></span>

<span data-ttu-id="08274-141">Zelfs met behulp van de para meter **forceren** , kunnen de cmdlet geen beveiligings beperkingen opheffen.</span><span class="sxs-lookup"><span data-stu-id="08274-141">Even using the **Force** parameter, the cmdlet can't override security restrictions.</span></span>

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

### <span data-ttu-id="08274-142">-LiteralPath</span><span class="sxs-lookup"><span data-stu-id="08274-142">-LiteralPath</span></span>

<span data-ttu-id="08274-143">Hiermee geeft u een pad naar een of meer locaties.</span><span class="sxs-lookup"><span data-stu-id="08274-143">Specifies a path to one or more locations.</span></span> <span data-ttu-id="08274-144">De waarde van **LiteralPath** wordt precies zo gebruikt als deze wordt getypt.</span><span class="sxs-lookup"><span data-stu-id="08274-144">The value of **LiteralPath** is used exactly as it is typed.</span></span> <span data-ttu-id="08274-145">Geen tekens worden geïnterpreteerd als joker tekens.</span><span class="sxs-lookup"><span data-stu-id="08274-145">No characters are interpreted as wildcards.</span></span> <span data-ttu-id="08274-146">Als het pad escape tekens bevat, plaatst u het tussen enkele aanhalings tekens.</span><span class="sxs-lookup"><span data-stu-id="08274-146">If the path includes escape characters, enclose it in single quotation marks.</span></span> <span data-ttu-id="08274-147">Enkele aanhalings tekens geven aan dat Power shell geen karakters interpreteert als escape reeksen.</span><span class="sxs-lookup"><span data-stu-id="08274-147">Single quotation marks tell PowerShell not to interpret any characters as escape sequences.</span></span>

<span data-ttu-id="08274-148">Zie [about_Quoting_Rules](../Microsoft.Powershell.Core/About/about_Quoting_Rules.md)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="08274-148">For more information, see [about_Quoting_Rules](../Microsoft.Powershell.Core/About/about_Quoting_Rules.md).</span></span>

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

### <span data-ttu-id="08274-149">-NewName</span><span class="sxs-lookup"><span data-stu-id="08274-149">-NewName</span></span>

<span data-ttu-id="08274-150">Hiermee geeft u de nieuwe naam van het item.</span><span class="sxs-lookup"><span data-stu-id="08274-150">Specifies the new name of the item.</span></span> <span data-ttu-id="08274-151">Voer alleen een naam in, geen pad en naam.</span><span class="sxs-lookup"><span data-stu-id="08274-151">Enter only a name, not a path and name.</span></span> <span data-ttu-id="08274-152">Als u een pad opgeeft dat verschilt van het pad dat is opgegeven in de para meter **Path** , wordt `Rename-Item` een fout gegenereerd.</span><span class="sxs-lookup"><span data-stu-id="08274-152">If you enter a path that differs from the path that is specified in the **Path** parameter, `Rename-Item` generates an error.</span></span>
<span data-ttu-id="08274-153">Gebruik om een item een andere naam te geven en te verplaatsen `Move-Item` .</span><span class="sxs-lookup"><span data-stu-id="08274-153">To rename and move an item, use `Move-Item`.</span></span>

<span data-ttu-id="08274-154">U kunt geen joker tekens gebruiken in de waarde van de para meter **newname** .</span><span class="sxs-lookup"><span data-stu-id="08274-154">You can't use wildcard characters in the value of the **NewName** parameter.</span></span> <span data-ttu-id="08274-155">Als u een naam voor meerdere bestanden wilt opgeven, gebruikt u de operator **replace** in een reguliere expressie.</span><span class="sxs-lookup"><span data-stu-id="08274-155">To specify a name for multiple files, use the **Replace** operator in a regular expression.</span></span> <span data-ttu-id="08274-156">Zie [about_Comparison_Operators](../Microsoft.PowerShell.Core/About/about_Comparison_Operators.md)voor meer informatie over de operator vervangen.</span><span class="sxs-lookup"><span data-stu-id="08274-156">For more information about the Replace operator, see [about_Comparison_Operators](../Microsoft.PowerShell.Core/About/about_Comparison_Operators.md).</span></span>

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

### <span data-ttu-id="08274-157">-PassThru</span><span class="sxs-lookup"><span data-stu-id="08274-157">-PassThru</span></span>

<span data-ttu-id="08274-158">Retourneert een object dat het item voor de pijp lijn vertegenwoordigt.</span><span class="sxs-lookup"><span data-stu-id="08274-158">Returns an object that represents the item to the pipeline.</span></span> <span data-ttu-id="08274-159">Deze cmdlet genereert standaard geen uitvoer.</span><span class="sxs-lookup"><span data-stu-id="08274-159">By default, this cmdlet does not generate any output.</span></span>

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

### <span data-ttu-id="08274-160">-Path</span><span class="sxs-lookup"><span data-stu-id="08274-160">-Path</span></span>

<span data-ttu-id="08274-161">Hiermee geeft u het pad op van het item waarvan u de naam wilt wijzigen.</span><span class="sxs-lookup"><span data-stu-id="08274-161">Specifies the path of the item to rename.</span></span>

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

### <span data-ttu-id="08274-162">-Confirm</span><span class="sxs-lookup"><span data-stu-id="08274-162">-Confirm</span></span>

<span data-ttu-id="08274-163">Hiermee wordt u gevraagd om bevestiging voordat u de cmdlet uitvoert.</span><span class="sxs-lookup"><span data-stu-id="08274-163">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="08274-164">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="08274-164">-WhatIf</span></span>

<span data-ttu-id="08274-165">Hiermee wordt weergegeven wat er zou gebeuren als u de cmdlet uitvoert.</span><span class="sxs-lookup"><span data-stu-id="08274-165">Shows what would happen if the cmdlet runs.</span></span>
<span data-ttu-id="08274-166">De cmdlet wordt niet uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="08274-166">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="08274-167">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="08274-167">CommonParameters</span></span>

<span data-ttu-id="08274-168">Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="08274-168">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="08274-169">Zie [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="08274-169">For more information, see [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md).</span></span>

## <span data-ttu-id="08274-170">INVOER</span><span class="sxs-lookup"><span data-stu-id="08274-170">INPUTS</span></span>

### <span data-ttu-id="08274-171">System. String</span><span class="sxs-lookup"><span data-stu-id="08274-171">System.String</span></span>

<span data-ttu-id="08274-172">U kunt een teken reeks met een pad naar deze cmdlet door sluizen.</span><span class="sxs-lookup"><span data-stu-id="08274-172">You can pipe a string that contains a path to this cmdlet.</span></span>

## <span data-ttu-id="08274-173">UITVOER</span><span class="sxs-lookup"><span data-stu-id="08274-173">OUTPUTS</span></span>

### <span data-ttu-id="08274-174">Geen of een object dat het hernoemde item vertegenwoordigt.</span><span class="sxs-lookup"><span data-stu-id="08274-174">None or an object that represents the renamed item.</span></span>

<span data-ttu-id="08274-175">Met deze cmdlet wordt een object gegenereerd dat het hernoemde item vertegenwoordigt, als u de para meter **PassThru** opgeeft.</span><span class="sxs-lookup"><span data-stu-id="08274-175">This cmdlet generates an object that represents the renamed item, if you specify the **PassThru** parameter.</span></span> <span data-ttu-id="08274-176">Anders wordt met deze cmdlet geen uitvoer gegenereerd.</span><span class="sxs-lookup"><span data-stu-id="08274-176">Otherwise, this cmdlet does not generate any output.</span></span>

## <span data-ttu-id="08274-177">OPMERKINGEN</span><span class="sxs-lookup"><span data-stu-id="08274-177">NOTES</span></span>

<span data-ttu-id="08274-178">`Rename-Item` is ontworpen om te werken met de gegevens die door elke provider worden weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="08274-178">`Rename-Item` is designed to work with the data exposed by any provider.</span></span> <span data-ttu-id="08274-179">Als u een lijst wilt weer geven van de providers die beschikbaar zijn in uw sessie, typt u `Get-PsProvider` .</span><span class="sxs-lookup"><span data-stu-id="08274-179">To list the providers available in your session, type `Get-PsProvider`.</span></span> <span data-ttu-id="08274-180">Zie [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="08274-180">For more information, see [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md).</span></span>

## <span data-ttu-id="08274-181">GERELATEERDE KOPPELINGEN</span><span class="sxs-lookup"><span data-stu-id="08274-181">RELATED LINKS</span></span>

[<span data-ttu-id="08274-182">Wissen-item</span><span class="sxs-lookup"><span data-stu-id="08274-182">Clear-Item</span></span>](Clear-Item.md)

[<span data-ttu-id="08274-183">Kopie-item</span><span class="sxs-lookup"><span data-stu-id="08274-183">Copy-Item</span></span>](Copy-Item.md)

[<span data-ttu-id="08274-184">Get-Child item</span><span class="sxs-lookup"><span data-stu-id="08274-184">Get-ChildItem</span></span>](Get-ChildItem.md)

[<span data-ttu-id="08274-185">Get-item</span><span class="sxs-lookup"><span data-stu-id="08274-185">Get-Item</span></span>](Get-Item.md)

[<span data-ttu-id="08274-186">Invoke-item</span><span class="sxs-lookup"><span data-stu-id="08274-186">Invoke-Item</span></span>](Invoke-Item.md)

[<span data-ttu-id="08274-187">Item verplaatsen</span><span class="sxs-lookup"><span data-stu-id="08274-187">Move-Item</span></span>](Move-Item.md)

[<span data-ttu-id="08274-188">Nieuw-item</span><span class="sxs-lookup"><span data-stu-id="08274-188">New-Item</span></span>](New-Item.md)

[<span data-ttu-id="08274-189">Verwijderen-item</span><span class="sxs-lookup"><span data-stu-id="08274-189">Remove-Item</span></span>](Remove-Item.md)

[<span data-ttu-id="08274-190">Naam wijzigen-item Property</span><span class="sxs-lookup"><span data-stu-id="08274-190">Rename-ItemProperty</span></span>](Rename-ItemProperty.md)

[<span data-ttu-id="08274-191">Set-item</span><span class="sxs-lookup"><span data-stu-id="08274-191">Set-Item</span></span>](Set-Item.md)

[<span data-ttu-id="08274-192">about_Providers</span><span class="sxs-lookup"><span data-stu-id="08274-192">about_Providers</span></span>](../Microsoft.PowerShell.Core/About/about_Providers.md)

