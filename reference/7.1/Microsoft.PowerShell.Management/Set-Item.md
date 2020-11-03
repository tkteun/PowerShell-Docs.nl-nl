---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 5/14/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/set-item?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Set-Item
ms.openlocfilehash: 5fbdb8345f0d8a1e83a40dbbad2e26fd89960f1d
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/07/2020
ms.locfileid: "93249995"
---
# <span data-ttu-id="7ef8d-103">Set-Item</span><span class="sxs-lookup"><span data-stu-id="7ef8d-103">Set-Item</span></span>

## <span data-ttu-id="7ef8d-104">SAMENVATTING</span><span class="sxs-lookup"><span data-stu-id="7ef8d-104">SYNOPSIS</span></span>
<span data-ttu-id="7ef8d-105">Wijzigt de waarde van een item in de waarde die is opgegeven in de opdracht.</span><span class="sxs-lookup"><span data-stu-id="7ef8d-105">Changes the value of an item to the value specified in the command.</span></span>

## <span data-ttu-id="7ef8d-106">SYNTAXIS</span><span class="sxs-lookup"><span data-stu-id="7ef8d-106">SYNTAX</span></span>

### <span data-ttu-id="7ef8d-107">Pad (standaard)</span><span class="sxs-lookup"><span data-stu-id="7ef8d-107">Path (Default)</span></span>

```
Set-Item [-Path] <String[]> [[-Value] <Object>] [-Force] [-PassThru] [-Filter <String>] [-Include <String[]>]
 [-Exclude <String[]>] [-Credential <PSCredential>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="7ef8d-108">LiteralPath</span><span class="sxs-lookup"><span data-stu-id="7ef8d-108">LiteralPath</span></span>

```
Set-Item -LiteralPath <String[]> [[-Value] <Object>] [-Force] [-PassThru] [-Filter <String>]
 [-Include <String[]>] [-Exclude <String[]>] [-Credential <PSCredential>]
 [-WhatIf] [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="7ef8d-109">BESCHRIJVING</span><span class="sxs-lookup"><span data-stu-id="7ef8d-109">DESCRIPTION</span></span>

<span data-ttu-id="7ef8d-110">`Set-Item`Met de cmdlet wordt de waarde van een item, zoals een variabele of register sleutel, gewijzigd in de waarde die is opgegeven in de opdracht.</span><span class="sxs-lookup"><span data-stu-id="7ef8d-110">The `Set-Item` cmdlet changes the value of an item, such as a variable or registry key, to the value specified in the command.</span></span>

## <span data-ttu-id="7ef8d-111">VOORBEELDEN</span><span class="sxs-lookup"><span data-stu-id="7ef8d-111">EXAMPLES</span></span>

### <span data-ttu-id="7ef8d-112">Voor beeld 1: een alias maken</span><span class="sxs-lookup"><span data-stu-id="7ef8d-112">Example 1: Create an alias</span></span>

<span data-ttu-id="7ef8d-113">Met deze opdracht maakt u een alias van NP voor Klad blok.</span><span class="sxs-lookup"><span data-stu-id="7ef8d-113">This command creates an alias of np for Notepad.</span></span>

```powershell
Set-Item -Path alias:np -Value "c:\windows\notepad.exe"
```

### <span data-ttu-id="7ef8d-114">Voor beeld 2: de waarde van een omgevings variabele wijzigen</span><span class="sxs-lookup"><span data-stu-id="7ef8d-114">Example 2: Change the value of an environment variable</span></span>

<span data-ttu-id="7ef8d-115">Met deze opdracht wordt de waarde van de omgevings variabele UserRole gewijzigd in Administrator.</span><span class="sxs-lookup"><span data-stu-id="7ef8d-115">This command changes the value of the UserRole environment variable to Administrator.</span></span>

```powershell
Set-Item -Path env:UserRole -Value "Administrator"
```

### <span data-ttu-id="7ef8d-116">Voor beeld 3: uw prompt functie wijzigen</span><span class="sxs-lookup"><span data-stu-id="7ef8d-116">Example 3: Modify your prompt function</span></span>

<span data-ttu-id="7ef8d-117">Met deze opdracht wordt de functie prompt zodanig gewijzigd dat de tijd voor het pad wordt weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="7ef8d-117">This command changes the prompt function so that it displays the time before the path.</span></span>

```powershell
Set-Item -Path function:prompt -Value {'PS '+ (Get-Date -Format t) + " " + (Get-Location) + '> '}
```

### <span data-ttu-id="7ef8d-118">Voor beeld 4: opties instellen voor de functie vragen</span><span class="sxs-lookup"><span data-stu-id="7ef8d-118">Example 4: Set options for your prompt function</span></span>

<span data-ttu-id="7ef8d-119">Met deze opdracht worden de opties **AllScope** en **ReadOnly** ingesteld voor de functie prompt.</span><span class="sxs-lookup"><span data-stu-id="7ef8d-119">This command sets the **AllScope** and **ReadOnly** options for the prompt function.</span></span>
<span data-ttu-id="7ef8d-120">Met deze opdracht wordt de dynamische para meter **Options** van gebruikt `Set-Item` .</span><span class="sxs-lookup"><span data-stu-id="7ef8d-120">This command uses the **Options** dynamic parameter of `Set-Item`.</span></span>
<span data-ttu-id="7ef8d-121">De para meter **Options** is `Set-Item` alleen beschikbaar wanneer u deze met de **alias** of **functie** provider gebruikt.</span><span class="sxs-lookup"><span data-stu-id="7ef8d-121">The **Options** parameter is available in `Set-Item` only when you use it with the **Alias** or **Function** provider.</span></span>

```powershell
Set-Item -Path function:prompt -Options "AllScope,ReadOnly"
```

## <span data-ttu-id="7ef8d-122">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="7ef8d-122">PARAMETERS</span></span>

### <span data-ttu-id="7ef8d-123">-Credential</span><span class="sxs-lookup"><span data-stu-id="7ef8d-123">-Credential</span></span>

> [!NOTE]
> <span data-ttu-id="7ef8d-124">Deze para meter wordt niet ondersteund door providers die zijn geïnstalleerd met Power shell.</span><span class="sxs-lookup"><span data-stu-id="7ef8d-124">This parameter is not supported by any providers installed with PowerShell.</span></span>
> <span data-ttu-id="7ef8d-125">Gebruik [invoke-Command](../Microsoft.PowerShell.Core/Invoke-Command.md)om een andere gebruiker te imiteren of uw referenties te verhogen wanneer u deze cmdlet uitvoert.</span><span class="sxs-lookup"><span data-stu-id="7ef8d-125">To impersonate another user, or elevate your credentials when running this cmdlet, use [Invoke-Command](../Microsoft.PowerShell.Core/Invoke-Command.md).</span></span>

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

### <span data-ttu-id="7ef8d-126">-Uitsluiten</span><span class="sxs-lookup"><span data-stu-id="7ef8d-126">-Exclude</span></span>

<span data-ttu-id="7ef8d-127">Hiermee geeft u als een teken reeks matrix een item of items die met deze cmdlet worden uitgesloten in de bewerking.</span><span class="sxs-lookup"><span data-stu-id="7ef8d-127">Specifies, as a string array, an item or items that this cmdlet excludes in the operation.</span></span> <span data-ttu-id="7ef8d-128">De waarde van deze para meter komt in aanmerking voor de para meter **Path** .</span><span class="sxs-lookup"><span data-stu-id="7ef8d-128">The value of this parameter qualifies the **Path** parameter.</span></span> <span data-ttu-id="7ef8d-129">Voer een element of patroon van een pad in, zoals `*.txt` .</span><span class="sxs-lookup"><span data-stu-id="7ef8d-129">Enter a path element or pattern, such as `*.txt`.</span></span> <span data-ttu-id="7ef8d-130">Joker tekens zijn toegestaan.</span><span class="sxs-lookup"><span data-stu-id="7ef8d-130">Wildcard characters are permitted.</span></span> <span data-ttu-id="7ef8d-131">De **exclude** -para meter is alleen effectief wanneer de inhoud van een item wordt opgenomen, zoals `C:\Windows\*` , waarbij het Joker teken de inhoud van de `C:\Windows` map bevat.</span><span class="sxs-lookup"><span data-stu-id="7ef8d-131">The **Exclude** parameter is effective only when the command includes the contents of an item, such as `C:\Windows\*`, where the wildcard character specifies the contents of the `C:\Windows` directory.</span></span>

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

### <span data-ttu-id="7ef8d-132">-Filter</span><span class="sxs-lookup"><span data-stu-id="7ef8d-132">-Filter</span></span>

<span data-ttu-id="7ef8d-133">Hiermee geeft u een filter op om de para meter **Path** te kwalificeren.</span><span class="sxs-lookup"><span data-stu-id="7ef8d-133">Specifies a filter to qualify the **Path** parameter.</span></span> <span data-ttu-id="7ef8d-134">De [File System](../Microsoft.PowerShell.Core/About/about_FileSystem_Provider.md) -provider is de enige geïnstalleerde Power shell-provider die het gebruik van filters ondersteunt.</span><span class="sxs-lookup"><span data-stu-id="7ef8d-134">The [FileSystem](../Microsoft.PowerShell.Core/About/about_FileSystem_Provider.md) provider is the only installed PowerShell provider that supports the use of filters.</span></span> <span data-ttu-id="7ef8d-135">U kunt de syntaxis voor de filter taal van het **Bestands systeem** in [about_Wildcards](../Microsoft.PowerShell.Core/About/about_Wildcards.md)vinden.</span><span class="sxs-lookup"><span data-stu-id="7ef8d-135">You can find the syntax for the **FileSystem** filter language in [about_Wildcards](../Microsoft.PowerShell.Core/About/about_Wildcards.md).</span></span>
<span data-ttu-id="7ef8d-136">Filters zijn efficiënter dan andere para meters, omdat deze door de provider worden toegepast wanneer de cmdlet de objecten ophaalt in plaats van dat Power shell de objecten heeft gefilterd nadat ze zijn opgehaald.</span><span class="sxs-lookup"><span data-stu-id="7ef8d-136">Filters are more efficient than other parameters, because the provider applies them when the cmdlet gets the objects rather than having PowerShell filter the objects after they are retrieved.</span></span>

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

### <span data-ttu-id="7ef8d-137">-Force</span><span class="sxs-lookup"><span data-stu-id="7ef8d-137">-Force</span></span>

<span data-ttu-id="7ef8d-138">Hiermee wordt de cmdlet gedwongen om items in te stellen die anders niet kunnen worden gewijzigd, zoals een alleen-lezen alias of variabelen.</span><span class="sxs-lookup"><span data-stu-id="7ef8d-138">Forces the cmdlet to set items that cannot otherwise be changed, such as read-only alias or variables.</span></span> <span data-ttu-id="7ef8d-139">De cmdlet kan geen constante aliassen of variabelen wijzigen.</span><span class="sxs-lookup"><span data-stu-id="7ef8d-139">The cmdlet cannot change constant aliases or variables.</span></span>
<span data-ttu-id="7ef8d-140">De implementatie varieert van provider tot provider.</span><span class="sxs-lookup"><span data-stu-id="7ef8d-140">Implementation varies from provider to provider.</span></span>
<span data-ttu-id="7ef8d-141">Zie [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="7ef8d-141">For more information, see [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md).</span></span>
<span data-ttu-id="7ef8d-142">Zelfs met behulp van de para meter *forceren* , kan de cmdlet geen beveiligings beperkingen opheffen.</span><span class="sxs-lookup"><span data-stu-id="7ef8d-142">Even using the *Force* parameter, the cmdlet cannot override security restrictions.</span></span>

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

### <span data-ttu-id="7ef8d-143">-Include</span><span class="sxs-lookup"><span data-stu-id="7ef8d-143">-Include</span></span>

<span data-ttu-id="7ef8d-144">Hiermee wordt een teken reeks matrix opgegeven, een item of items die met deze cmdlet in de bewerking zijn opgenomen.</span><span class="sxs-lookup"><span data-stu-id="7ef8d-144">Specifies, as a string array, an item or items that this cmdlet includes in the operation.</span></span> <span data-ttu-id="7ef8d-145">De waarde van deze para meter komt in aanmerking voor de para meter **Path** .</span><span class="sxs-lookup"><span data-stu-id="7ef8d-145">The value of this parameter qualifies the **Path** parameter.</span></span> <span data-ttu-id="7ef8d-146">Voer een element of patroon van een pad in, zoals `"*.txt"` .</span><span class="sxs-lookup"><span data-stu-id="7ef8d-146">Enter a path element or pattern, such as `"*.txt"`.</span></span> <span data-ttu-id="7ef8d-147">Joker tekens zijn toegestaan.</span><span class="sxs-lookup"><span data-stu-id="7ef8d-147">Wildcard characters are permitted.</span></span> <span data-ttu-id="7ef8d-148">De para meter **include** is alleen effectief wanneer de inhoud van een item wordt opgenomen, zoals `C:\Windows\*` , waarbij het Joker teken de inhoud van de `C:\Windows` map bevat.</span><span class="sxs-lookup"><span data-stu-id="7ef8d-148">The **Include** parameter is effective only when the command includes the contents of an item, such as `C:\Windows\*`, where the wildcard character specifies the contents of the `C:\Windows` directory.</span></span>

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

### <span data-ttu-id="7ef8d-149">-LiteralPath</span><span class="sxs-lookup"><span data-stu-id="7ef8d-149">-LiteralPath</span></span>

<span data-ttu-id="7ef8d-150">Hiermee geeft u een pad naar een of meer locaties.</span><span class="sxs-lookup"><span data-stu-id="7ef8d-150">Specifies a path to one or more locations.</span></span> <span data-ttu-id="7ef8d-151">De waarde van **LiteralPath** wordt precies zo gebruikt als deze wordt getypt.</span><span class="sxs-lookup"><span data-stu-id="7ef8d-151">The value of **LiteralPath** is used exactly as it is typed.</span></span> <span data-ttu-id="7ef8d-152">Geen tekens worden geïnterpreteerd als joker tekens.</span><span class="sxs-lookup"><span data-stu-id="7ef8d-152">No characters are interpreted as wildcards.</span></span> <span data-ttu-id="7ef8d-153">Als het pad escape tekens bevat, plaatst u het tussen enkele aanhalings tekens.</span><span class="sxs-lookup"><span data-stu-id="7ef8d-153">If the path includes escape characters, enclose it in single quotation marks.</span></span> <span data-ttu-id="7ef8d-154">Enkele aanhalings tekens geven aan dat Power shell geen karakters interpreteert als escape reeksen.</span><span class="sxs-lookup"><span data-stu-id="7ef8d-154">Single quotation marks tell PowerShell not to interpret any characters as escape sequences.</span></span>

<span data-ttu-id="7ef8d-155">Zie [about_Quoting_Rules](../Microsoft.Powershell.Core/About/about_Quoting_Rules.md)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="7ef8d-155">For more information, see [about_Quoting_Rules](../Microsoft.Powershell.Core/About/about_Quoting_Rules.md).</span></span>

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

### <span data-ttu-id="7ef8d-156">-PassThru</span><span class="sxs-lookup"><span data-stu-id="7ef8d-156">-PassThru</span></span>

<span data-ttu-id="7ef8d-157">Geeft een object dat het item vertegenwoordigt in de pijp lijn.</span><span class="sxs-lookup"><span data-stu-id="7ef8d-157">Passes an object that represents the item to the pipeline.</span></span>
<span data-ttu-id="7ef8d-158">Deze cmdlet genereert standaard geen uitvoer.</span><span class="sxs-lookup"><span data-stu-id="7ef8d-158">By default, this cmdlet does not generate any output.</span></span>

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

### <span data-ttu-id="7ef8d-159">-Path</span><span class="sxs-lookup"><span data-stu-id="7ef8d-159">-Path</span></span>

<span data-ttu-id="7ef8d-160">Hiermee geeft u een pad op naar de locatie van de items.</span><span class="sxs-lookup"><span data-stu-id="7ef8d-160">Specifies a path of the location of the items.</span></span>
<span data-ttu-id="7ef8d-161">Joker tekens zijn toegestaan.</span><span class="sxs-lookup"><span data-stu-id="7ef8d-161">Wildcard characters are permitted.</span></span>

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

### <span data-ttu-id="7ef8d-162">-Waarde</span><span class="sxs-lookup"><span data-stu-id="7ef8d-162">-Value</span></span>

<span data-ttu-id="7ef8d-163">Hiermee geeft u een nieuwe waarde op voor het item.</span><span class="sxs-lookup"><span data-stu-id="7ef8d-163">Specifies a new value for the item.</span></span>

```yaml
Type: System.Object
Parameter Sets: (All)
Aliases:

Required: False
Position: 1
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="7ef8d-164">-Confirm</span><span class="sxs-lookup"><span data-stu-id="7ef8d-164">-Confirm</span></span>

<span data-ttu-id="7ef8d-165">Hiermee wordt u gevraagd om bevestiging voordat u de cmdlet uitvoert.</span><span class="sxs-lookup"><span data-stu-id="7ef8d-165">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="7ef8d-166">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="7ef8d-166">-WhatIf</span></span>

<span data-ttu-id="7ef8d-167">Hiermee wordt weergegeven wat er zou gebeuren als u de cmdlet uitvoert.</span><span class="sxs-lookup"><span data-stu-id="7ef8d-167">Shows what would happen if the cmdlet runs.</span></span>
<span data-ttu-id="7ef8d-168">De cmdlet wordt niet uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="7ef8d-168">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="7ef8d-169">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="7ef8d-169">CommonParameters</span></span>

<span data-ttu-id="7ef8d-170">Deze cmdlet biedt ondersteuning voor de algemene para meters: `-Debug` , `-ErrorAction` , `-ErrorVariable` , `-InformationAction` , `-InformationVariable` , `-OutVariable` , `-OutBuffer` , `-PipelineVariable` , `-Verbose` , `-WarningAction` en `-WarningVariable` .</span><span class="sxs-lookup"><span data-stu-id="7ef8d-170">This cmdlet supports the common parameters: `-Debug`, `-ErrorAction`, `-ErrorVariable`, `-InformationAction`, `-InformationVariable`, `-OutVariable`, `-OutBuffer`, `-PipelineVariable`, `-Verbose`, `-WarningAction`, and `-WarningVariable`.</span></span> <span data-ttu-id="7ef8d-171">Zie [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="7ef8d-171">For more information, see [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md).</span></span>

## <span data-ttu-id="7ef8d-172">INVOER</span><span class="sxs-lookup"><span data-stu-id="7ef8d-172">INPUTS</span></span>

### <span data-ttu-id="7ef8d-173">System. object</span><span class="sxs-lookup"><span data-stu-id="7ef8d-173">System.Object</span></span>

<span data-ttu-id="7ef8d-174">U kunt een object dat de nieuwe waarde van het item vertegenwoordigt door sluizen naar deze cmdlet.</span><span class="sxs-lookup"><span data-stu-id="7ef8d-174">You can pipe an object that represents the new value of the item to this cmdlet.</span></span>

## <span data-ttu-id="7ef8d-175">UITVOER</span><span class="sxs-lookup"><span data-stu-id="7ef8d-175">OUTPUTS</span></span>

### <span data-ttu-id="7ef8d-176">Geen of een object dat het nieuwe of gewijzigde item voor stelt.</span><span class="sxs-lookup"><span data-stu-id="7ef8d-176">None or an object representing the new or changed item.</span></span>

<span data-ttu-id="7ef8d-177">Met deze cmdlet wordt een object dat het item vertegenwoordigt, gegenereerd als u de para meter *PassThru* opgeeft.</span><span class="sxs-lookup"><span data-stu-id="7ef8d-177">This cmdlet generates an object that represent the item, if you specify the *PassThru* parameter.</span></span>
<span data-ttu-id="7ef8d-178">Anders wordt met deze cmdlet geen uitvoer gegenereerd.</span><span class="sxs-lookup"><span data-stu-id="7ef8d-178">Otherwise, this cmdlet does not generate any output.</span></span>

## <span data-ttu-id="7ef8d-179">OPMERKINGEN</span><span class="sxs-lookup"><span data-stu-id="7ef8d-179">NOTES</span></span>

- <span data-ttu-id="7ef8d-180">`Set-Item` wordt niet ondersteund door de Power shell-bestandssysteem provider.</span><span class="sxs-lookup"><span data-stu-id="7ef8d-180">`Set-Item` is not supported by the PowerShell FileSystem provider.</span></span> <span data-ttu-id="7ef8d-181">Als u de waarden van items in het bestands systeem wilt wijzigen, gebruikt u de `Set-Content` cmdlet.</span><span class="sxs-lookup"><span data-stu-id="7ef8d-181">To change the values of items in the file system, use the `Set-Content` cmdlet.</span></span>
- <span data-ttu-id="7ef8d-182">In de register stations, `HKLM:` en `HKCU:` worden `Set-Item` de gegevens in de (standaard) waarde van een register sleutel gewijzigd.</span><span class="sxs-lookup"><span data-stu-id="7ef8d-182">In the Registry drives, `HKLM:` and `HKCU:`, `Set-Item` changes the data in the (Default) value of a registry key.</span></span>
  - <span data-ttu-id="7ef8d-183">Gebruik de cmdlet en om de namen van register sleutels te maken en te wijzigen `New-Item` `Rename-Item` .</span><span class="sxs-lookup"><span data-stu-id="7ef8d-183">To create and change the names of registry keys, use the `New-Item` and `Rename-Item` cmdlet.</span></span>
  - <span data-ttu-id="7ef8d-184">Als u de namen en gegevens in register waarden wilt wijzigen, gebruikt u de `New-ItemProperty` `Set-ItemProperty` `Rename-ItemProperty` cmdlets, en.</span><span class="sxs-lookup"><span data-stu-id="7ef8d-184">To change the names and data in registry values, use the `New-ItemProperty`, `Set-ItemProperty`, and `Rename-ItemProperty` cmdlets.</span></span>
- <span data-ttu-id="7ef8d-185">`Set-Item` is ontworpen om te werken met de gegevens die door elke provider worden weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="7ef8d-185">`Set-Item` is designed to work with the data exposed by any provider.</span></span>
  <span data-ttu-id="7ef8d-186">Als u een lijst wilt weer geven van de providers die beschikbaar zijn in uw sessie, typt u `Get-PsProvider` .</span><span class="sxs-lookup"><span data-stu-id="7ef8d-186">To list the providers available in your session, type `Get-PsProvider`.</span></span>
  <span data-ttu-id="7ef8d-187">Zie [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="7ef8d-187">For more information, see [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md).</span></span>

## <span data-ttu-id="7ef8d-188">GERELATEERDE KOPPELINGEN</span><span class="sxs-lookup"><span data-stu-id="7ef8d-188">RELATED LINKS</span></span>

[<span data-ttu-id="7ef8d-189">Wissen-item</span><span class="sxs-lookup"><span data-stu-id="7ef8d-189">Clear-Item</span></span>](Clear-Item.md)

[<span data-ttu-id="7ef8d-190">Kopie-item</span><span class="sxs-lookup"><span data-stu-id="7ef8d-190">Copy-Item</span></span>](Copy-Item.md)

[<span data-ttu-id="7ef8d-191">Get-item</span><span class="sxs-lookup"><span data-stu-id="7ef8d-191">Get-Item</span></span>](Get-Item.md)

[<span data-ttu-id="7ef8d-192">Invoke-item</span><span class="sxs-lookup"><span data-stu-id="7ef8d-192">Invoke-Item</span></span>](Invoke-Item.md)

[<span data-ttu-id="7ef8d-193">Item verplaatsen</span><span class="sxs-lookup"><span data-stu-id="7ef8d-193">Move-Item</span></span>](Move-Item.md)

[<span data-ttu-id="7ef8d-194">Nieuw-item</span><span class="sxs-lookup"><span data-stu-id="7ef8d-194">New-Item</span></span>](New-Item.md)

[<span data-ttu-id="7ef8d-195">Verwijderen-item</span><span class="sxs-lookup"><span data-stu-id="7ef8d-195">Remove-Item</span></span>](Remove-Item.md)

[<span data-ttu-id="7ef8d-196">Naam wijzigen-item</span><span class="sxs-lookup"><span data-stu-id="7ef8d-196">Rename-Item</span></span>](Rename-Item.md)

[<span data-ttu-id="7ef8d-197">about_Providers</span><span class="sxs-lookup"><span data-stu-id="7ef8d-197">about_Providers</span></span>](../Microsoft.PowerShell.Core/About/about_Providers.md)

