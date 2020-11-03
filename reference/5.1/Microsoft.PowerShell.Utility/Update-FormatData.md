---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/update-formatdata?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Update-FormatData
ms.openlocfilehash: 41a49ccd185cdc1ebf5c6f748833ee3f4218784b
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/07/2020
ms.locfileid: "93250354"
---
# <span data-ttu-id="2bd15-103">Update-FormatData</span><span class="sxs-lookup"><span data-stu-id="2bd15-103">Update-FormatData</span></span>

## <span data-ttu-id="2bd15-104">SAMENVATTING</span><span class="sxs-lookup"><span data-stu-id="2bd15-104">SYNOPSIS</span></span>
<span data-ttu-id="2bd15-105">Hiermee werkt u de opmaak gegevens in de huidige sessie bij.</span><span class="sxs-lookup"><span data-stu-id="2bd15-105">Updates the formatting data in the current session.</span></span>

## <span data-ttu-id="2bd15-106">SYNTAXIS</span><span class="sxs-lookup"><span data-stu-id="2bd15-106">SYNTAX</span></span>

```
Update-FormatData [[-AppendPath] <String[]>] [-PrependPath <String[]>] [-WhatIf] [-Confirm]
 [<CommonParameters>]
```

## <span data-ttu-id="2bd15-107">BESCHRIJVING</span><span class="sxs-lookup"><span data-stu-id="2bd15-107">DESCRIPTION</span></span>

<span data-ttu-id="2bd15-108">`Update-FormatData`Met de cmdlet worden de opmaak gegevens opnieuw geladen van indelings bestanden in de huidige sessie.</span><span class="sxs-lookup"><span data-stu-id="2bd15-108">The `Update-FormatData` cmdlet reloads the formatting data from formatting files into the current session.</span></span> <span data-ttu-id="2bd15-109">Met deze cmdlet kunt u de opmaak gegevens bijwerken zonder Power shell opnieuw te starten.</span><span class="sxs-lookup"><span data-stu-id="2bd15-109">This cmdlet lets you update the formatting data without restarting PowerShell.</span></span>

<span data-ttu-id="2bd15-110">Zonder para meters worden `Update-FormatData` de indelings bestanden die eerder zijn geladen, opnieuw geladen.</span><span class="sxs-lookup"><span data-stu-id="2bd15-110">Without parameters, `Update-FormatData` reloads the formatting files that it loaded previously.</span></span>
<span data-ttu-id="2bd15-111">U kunt de para meters van gebruiken `Update-FormatData` om nieuwe indelings bestanden toe te voegen aan de sessie.</span><span class="sxs-lookup"><span data-stu-id="2bd15-111">You can use the parameters of `Update-FormatData` to add new formatting files to the session.</span></span>

<span data-ttu-id="2bd15-112">Indelings bestanden zijn tekst bestanden in XML-indeling met de `format.ps1xml` bestandsnaam extensie.</span><span class="sxs-lookup"><span data-stu-id="2bd15-112">Formatting files are text files in XML format with the `format.ps1xml` file name extension.</span></span> <span data-ttu-id="2bd15-113">De indelings gegevens in de bestanden definiëren de weer gave van Microsoft .NET Framework-objecten in de sessie.</span><span class="sxs-lookup"><span data-stu-id="2bd15-113">The formatting data in the files defines the display of Microsoft .NET Framework objects in the session.</span></span>

<span data-ttu-id="2bd15-114">Als Windows Power shell wordt gestart, worden de gegevens uit de indelings bestanden in de installatie directory van Power shell ( `$pshome` ) geladen in de sessie.</span><span class="sxs-lookup"><span data-stu-id="2bd15-114">When Windows PowerShell starts, it loads the format data from the formatting files in the PowerShell installation directory (`$pshome`) into the session.</span></span> <span data-ttu-id="2bd15-115">U kunt gebruiken `Update-FormatData` om de opmaak gegevens opnieuw te laden in de huidige sessie zonder Power shell opnieuw te starten.</span><span class="sxs-lookup"><span data-stu-id="2bd15-115">You can use `Update-FormatData` to reload the formatting data into the current session without restarting PowerShell.</span></span> <span data-ttu-id="2bd15-116">Dit is handig wanneer u een opmaak bestand hebt toegevoegd of gewijzigd, maar de sessie niet wilt onderbreken.</span><span class="sxs-lookup"><span data-stu-id="2bd15-116">This is useful when you have added or changed a formatting file, but do not want to interrupt the session.</span></span>

<span data-ttu-id="2bd15-117">Zie [about_Format.ps1XML](../Microsoft.PowerShell.Core/About/about_Format.ps1xml.md)voor meer informatie over het format teren van bestanden in Power shell.</span><span class="sxs-lookup"><span data-stu-id="2bd15-117">For more information about formatting files in PowerShell, see [about_Format.ps1xml](../Microsoft.PowerShell.Core/About/about_Format.ps1xml.md).</span></span>

## <span data-ttu-id="2bd15-118">VOORBEELDEN</span><span class="sxs-lookup"><span data-stu-id="2bd15-118">EXAMPLES</span></span>

### <span data-ttu-id="2bd15-119">Voor beeld 1: eerder geladen indelings bestanden opnieuw laden</span><span class="sxs-lookup"><span data-stu-id="2bd15-119">Example 1: Reload previously loaded formatting files</span></span>

```powershell
Update-FormatData
```

<span data-ttu-id="2bd15-120">Met deze opdracht worden de indelings bestanden die eerder zijn geladen, opnieuw geladen.</span><span class="sxs-lookup"><span data-stu-id="2bd15-120">This command reloads the formatting files that it loaded previously.</span></span>

### <span data-ttu-id="2bd15-121">Voor beeld 2: indelings bestanden en tracerings-en logboek bestanden opnieuw laden</span><span class="sxs-lookup"><span data-stu-id="2bd15-121">Example 2: Reload formatting files and trace and log formatting files</span></span>

```powershell
Update-FormatData -AppendPath "trace.format.ps1xml, log.format.ps1xml"
```

<span data-ttu-id="2bd15-122">Met deze opdracht worden de indelings bestanden opnieuw geladen in de sessie, met inbegrip van twee nieuwe bestanden, Trace.format.ps1XML-en Log.format.ps1XML-bestand.</span><span class="sxs-lookup"><span data-stu-id="2bd15-122">This command reloads the formatting files into the session, including two new files, Trace.format.ps1xml and Log.format.ps1xml.</span></span>

<span data-ttu-id="2bd15-123">Omdat de opdracht gebruikmaakt van de para meter **AppendPath** , worden de opmaak gegevens in de nieuwe bestanden geladen na het format teren van de gegevens uit de ingebouwde bestanden.</span><span class="sxs-lookup"><span data-stu-id="2bd15-123">Because the command uses the **AppendPath** parameter, the formatting data in the new files is loaded after the formatting data from the built-in files.</span></span>

<span data-ttu-id="2bd15-124">De para meter **AppendPath** wordt gebruikt omdat de nieuwe bestanden opmaak gegevens bevatten voor objecten waarnaar niet wordt verwezen in de ingebouwde bestanden.</span><span class="sxs-lookup"><span data-stu-id="2bd15-124">The **AppendPath** parameter is used because the new files contain formatting data for objects that are not referenced in the built-in files.</span></span>

### <span data-ttu-id="2bd15-125">Voor beeld 3: een opmaak bestand bewerken en opnieuw laden</span><span class="sxs-lookup"><span data-stu-id="2bd15-125">Example 3: Edit a formatting file and reload it</span></span>

```powershell
Update-FormatData -PrependPath "c:\test\NewFiles.format.ps1xml"

# Edit the NewFiles.format.ps1 file.

Update-FormatData
```

<span data-ttu-id="2bd15-126">In dit voor beeld ziet u hoe u een opmaak bestand opnieuw kunt laden nadat u het hebt bewerkt.</span><span class="sxs-lookup"><span data-stu-id="2bd15-126">This example shows how to reload a formatting file after you have edited it.</span></span>

<span data-ttu-id="2bd15-127">Met de eerste opdracht wordt het NewFiles.format.ps1XML-bestand aan de sessie toegevoegd.</span><span class="sxs-lookup"><span data-stu-id="2bd15-127">The first command adds the NewFiles.format.ps1xml file to the session.</span></span> <span data-ttu-id="2bd15-128">De para meter **PrependPath** wordt gebruikt omdat het bestand opmaak gegevens bevat voor objecten waarnaar wordt verwezen in de ingebouwde bestanden.</span><span class="sxs-lookup"><span data-stu-id="2bd15-128">It uses the **PrependPath** parameter because the file contains formatting data for objects that are referenced in the built-in files.</span></span>

<span data-ttu-id="2bd15-129">Nadat u het XML-bestand NewFiles.format.ps1hebt toegevoegd en het in deze sessies hebt getest, bewerkt de auteur het bestand.</span><span class="sxs-lookup"><span data-stu-id="2bd15-129">After adding the NewFiles.format.ps1xml file and testing it in these sessions, the author edits the file.</span></span>

<span data-ttu-id="2bd15-130">De tweede opdracht gebruikt de `Update-FormatData` cmdlet om de indelings bestanden opnieuw te laden.</span><span class="sxs-lookup"><span data-stu-id="2bd15-130">The second command uses the `Update-FormatData` cmdlet to reload the formatting files.</span></span> <span data-ttu-id="2bd15-131">Omdat het XML-bestand van de NewFiles.format.ps1eerder is geladen, wordt `Update-FormatData` het automatisch opnieuw geladen zonder para meters te gebruiken.</span><span class="sxs-lookup"><span data-stu-id="2bd15-131">Because the NewFiles.format.ps1xml file was previously loaded, `Update-FormatData` automatically reloads it without using parameters.</span></span>

## <span data-ttu-id="2bd15-132">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="2bd15-132">PARAMETERS</span></span>

### <span data-ttu-id="2bd15-133">-AppendPath</span><span class="sxs-lookup"><span data-stu-id="2bd15-133">-AppendPath</span></span>

<span data-ttu-id="2bd15-134">Hiermee geeft u indelings bestanden die met deze cmdlet worden toegevoegd aan de sessie.</span><span class="sxs-lookup"><span data-stu-id="2bd15-134">Specifies formatting files that this cmdlet adds to the session.</span></span> <span data-ttu-id="2bd15-135">De bestanden worden geladen nadat Power shell de ingebouwde opmaak bestanden heeft geladen.</span><span class="sxs-lookup"><span data-stu-id="2bd15-135">The files are loaded after PowerShell loads the built-in formatting files.</span></span>

<span data-ttu-id="2bd15-136">Bij het format teren van .NET-objecten gebruikt Windows Power shell de eerste opmaak definitie die wordt gevonden voor elk .NET-type.</span><span class="sxs-lookup"><span data-stu-id="2bd15-136">When formatting .NET objects,Windows PowerShell uses the first formatting definition that it finds for each .NET type.</span></span> <span data-ttu-id="2bd15-137">Als u de para meter **AppendPath** gebruikt, doorzoekt Windows Power shell de gegevens van de ingebouwde bestanden voordat deze de opmaak gegevens detecteert die u toevoegt.</span><span class="sxs-lookup"><span data-stu-id="2bd15-137">If you use the **AppendPath** parameter, Windows PowerShell searches the data from the built-in files before it encounters the formatting data that you are adding.</span></span>

<span data-ttu-id="2bd15-138">Gebruik deze para meter om een bestand toe te voegen waarmee een .NET-object wordt opgemaakt waarnaar niet wordt verwezen in de ingebouwde opmaak bestanden.</span><span class="sxs-lookup"><span data-stu-id="2bd15-138">Use this parameter to add a file that formats a .NET object that is not referenced in the built-in formatting files.</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases: PSPath, Path

Required: False
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="2bd15-139">-PrependPath</span><span class="sxs-lookup"><span data-stu-id="2bd15-139">-PrependPath</span></span>

<span data-ttu-id="2bd15-140">Hiermee geeft u indelings bestanden die met deze cmdlet worden toegevoegd aan de sessie.</span><span class="sxs-lookup"><span data-stu-id="2bd15-140">Specifies formatting files that this cmdlet adds to the session.</span></span> <span data-ttu-id="2bd15-141">De bestanden worden geladen voordat Power shell de ingebouwde indelings bestanden laadt.</span><span class="sxs-lookup"><span data-stu-id="2bd15-141">The files are loaded before PowerShell loads the built-in formatting files.</span></span>

<span data-ttu-id="2bd15-142">Bij het format teren van .NET-objecten gebruikt Windows Power shell de eerste opmaak definitie die wordt gevonden voor elk .NET-type.</span><span class="sxs-lookup"><span data-stu-id="2bd15-142">When formatting .NET objects, Windows PowerShell uses the first formatting definition that it finds for each .NET type.</span></span> <span data-ttu-id="2bd15-143">Als u de para meter **PrependPath** gebruikt, doorzoekt Windows Power shell de gegevens van de bestanden die u toevoegt voordat de opmaak gegevens van de ingebouwde bestanden worden gevonden.</span><span class="sxs-lookup"><span data-stu-id="2bd15-143">If you use the **PrependPath** parameter, Windows PowerShell searches the data from the files that you are adding before it encounters the formatting data from the built-in files.</span></span>

<span data-ttu-id="2bd15-144">Gebruik deze para meter om een bestand toe te voegen waarmee een .NET-object wordt opgemaakt waarnaar ook wordt verwezen in de ingebouwde opmaak bestanden.</span><span class="sxs-lookup"><span data-stu-id="2bd15-144">Use this parameter to add a file that formats a .NET object that is also referenced in the built-in formatting files.</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="2bd15-145">-Confirm</span><span class="sxs-lookup"><span data-stu-id="2bd15-145">-Confirm</span></span>

<span data-ttu-id="2bd15-146">Hiermee wordt u gevraagd om bevestiging voordat u de cmdlet uitvoert.</span><span class="sxs-lookup"><span data-stu-id="2bd15-146">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="2bd15-147">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="2bd15-147">-WhatIf</span></span>

<span data-ttu-id="2bd15-148">Hiermee wordt weergegeven wat er zou gebeuren als u de cmdlet uitvoert.</span><span class="sxs-lookup"><span data-stu-id="2bd15-148">Shows what would happen if the cmdlet runs.</span></span>
<span data-ttu-id="2bd15-149">De cmdlet wordt niet uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="2bd15-149">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="2bd15-150">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="2bd15-150">CommonParameters</span></span>

<span data-ttu-id="2bd15-151">Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="2bd15-151">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="2bd15-152">Zie [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="2bd15-152">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="2bd15-153">INVOER</span><span class="sxs-lookup"><span data-stu-id="2bd15-153">INPUTS</span></span>

### <span data-ttu-id="2bd15-154">System. String</span><span class="sxs-lookup"><span data-stu-id="2bd15-154">System.String</span></span>

<span data-ttu-id="2bd15-155">U kunt een teken reeks die het pad toevoegen bevat door sluizen naar `Update-FormatData` .</span><span class="sxs-lookup"><span data-stu-id="2bd15-155">You can pipe a string that contains the append path to `Update-FormatData`.</span></span>

## <span data-ttu-id="2bd15-156">UITVOER</span><span class="sxs-lookup"><span data-stu-id="2bd15-156">OUTPUTS</span></span>

### <span data-ttu-id="2bd15-157">Geen</span><span class="sxs-lookup"><span data-stu-id="2bd15-157">None</span></span>

<span data-ttu-id="2bd15-158">De cmdlet retourneert geen uitvoer.</span><span class="sxs-lookup"><span data-stu-id="2bd15-158">The cmdlet does not return any output.</span></span>

## <span data-ttu-id="2bd15-159">OPMERKINGEN</span><span class="sxs-lookup"><span data-stu-id="2bd15-159">NOTES</span></span>

- <span data-ttu-id="2bd15-160">`Update-FormatData` werkt ook de opmaak gegevens bij voor opdrachten in de sessie die uit modules zijn geïmporteerd.</span><span class="sxs-lookup"><span data-stu-id="2bd15-160">`Update-FormatData` also updates the formatting data for commands in the session that were imported from modules.</span></span> <span data-ttu-id="2bd15-161">Als het opmaak bestand voor een module wordt gewijzigd, kunt u een `Update-FormatData` opdracht uitvoeren om de opmaak gegevens voor geïmporteerde opdrachten bij te werken.</span><span class="sxs-lookup"><span data-stu-id="2bd15-161">If the formatting file for a module changes, you can run an `Update-FormatData` command to update the formatting data for imported commands.</span></span> <span data-ttu-id="2bd15-162">U hoeft de module niet opnieuw te importeren.</span><span class="sxs-lookup"><span data-stu-id="2bd15-162">You do not need to import the module again.</span></span>

## <span data-ttu-id="2bd15-163">GERELATEERDE KOPPELINGEN</span><span class="sxs-lookup"><span data-stu-id="2bd15-163">RELATED LINKS</span></span>

[<span data-ttu-id="2bd15-164">Get-FormatData</span><span class="sxs-lookup"><span data-stu-id="2bd15-164">Get-FormatData</span></span>](Get-FormatData.md)

[<span data-ttu-id="2bd15-165">Exporteren-FormatData</span><span class="sxs-lookup"><span data-stu-id="2bd15-165">Export-FormatData</span></span>](Export-FormatData.md)
