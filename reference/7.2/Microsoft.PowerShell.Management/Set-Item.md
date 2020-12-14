---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 05/14/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/set-item?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Set-Item
ms.openlocfilehash: c617f4554c8e61ed6cf54b0faf0cd7d79be84595
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 11/17/2020
ms.locfileid: "94705867"
---
# <span data-ttu-id="c0cf7-102">Set-Item</span><span class="sxs-lookup"><span data-stu-id="c0cf7-102">Set-Item</span></span>

## <span data-ttu-id="c0cf7-103">SAMENVATTING</span><span class="sxs-lookup"><span data-stu-id="c0cf7-103">SYNOPSIS</span></span>
<span data-ttu-id="c0cf7-104">Wijzigt de waarde van een item in de waarde die is opgegeven in de opdracht.</span><span class="sxs-lookup"><span data-stu-id="c0cf7-104">Changes the value of an item to the value specified in the command.</span></span>

## <span data-ttu-id="c0cf7-105">SYNTAXIS</span><span class="sxs-lookup"><span data-stu-id="c0cf7-105">SYNTAX</span></span>

### <span data-ttu-id="c0cf7-106">Pad (standaard)</span><span class="sxs-lookup"><span data-stu-id="c0cf7-106">Path (Default)</span></span>

```
Set-Item [-Path] <String[]> [[-Value] <Object>] [-Force] [-PassThru] [-Filter <String>] [-Include <String[]>]
 [-Exclude <String[]>] [-Credential <PSCredential>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="c0cf7-107">LiteralPath</span><span class="sxs-lookup"><span data-stu-id="c0cf7-107">LiteralPath</span></span>

```
Set-Item -LiteralPath <String[]> [[-Value] <Object>] [-Force] [-PassThru] [-Filter <String>]
 [-Include <String[]>] [-Exclude <String[]>] [-Credential <PSCredential>]
 [-WhatIf] [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="c0cf7-108">BESCHRIJVING</span><span class="sxs-lookup"><span data-stu-id="c0cf7-108">DESCRIPTION</span></span>

<span data-ttu-id="c0cf7-109">`Set-Item`Met de cmdlet wordt de waarde van een item, zoals een variabele of register sleutel, gewijzigd in de waarde die is opgegeven in de opdracht.</span><span class="sxs-lookup"><span data-stu-id="c0cf7-109">The `Set-Item` cmdlet changes the value of an item, such as a variable or registry key, to the value specified in the command.</span></span>

## <span data-ttu-id="c0cf7-110">VOORBEELDEN</span><span class="sxs-lookup"><span data-stu-id="c0cf7-110">EXAMPLES</span></span>

### <span data-ttu-id="c0cf7-111">Voor beeld 1: een alias maken</span><span class="sxs-lookup"><span data-stu-id="c0cf7-111">Example 1: Create an alias</span></span>

<span data-ttu-id="c0cf7-112">Met deze opdracht maakt u een alias van NP voor Klad blok.</span><span class="sxs-lookup"><span data-stu-id="c0cf7-112">This command creates an alias of np for Notepad.</span></span>

```powershell
Set-Item -Path alias:np -Value "c:\windows\notepad.exe"
```

### <span data-ttu-id="c0cf7-113">Voor beeld 2: de waarde van een omgevings variabele wijzigen</span><span class="sxs-lookup"><span data-stu-id="c0cf7-113">Example 2: Change the value of an environment variable</span></span>

<span data-ttu-id="c0cf7-114">Met deze opdracht wordt de waarde van de omgevings variabele UserRole gewijzigd in Administrator.</span><span class="sxs-lookup"><span data-stu-id="c0cf7-114">This command changes the value of the UserRole environment variable to Administrator.</span></span>

```powershell
Set-Item -Path env:UserRole -Value "Administrator"
```

### <span data-ttu-id="c0cf7-115">Voor beeld 3: uw prompt functie wijzigen</span><span class="sxs-lookup"><span data-stu-id="c0cf7-115">Example 3: Modify your prompt function</span></span>

<span data-ttu-id="c0cf7-116">Met deze opdracht wordt de functie prompt zodanig gewijzigd dat de tijd voor het pad wordt weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="c0cf7-116">This command changes the prompt function so that it displays the time before the path.</span></span>

```powershell
Set-Item -Path function:prompt -Value {'PS '+ (Get-Date -Format t) + " " + (Get-Location) + '> '}
```

### <span data-ttu-id="c0cf7-117">Voor beeld 4: opties instellen voor de functie vragen</span><span class="sxs-lookup"><span data-stu-id="c0cf7-117">Example 4: Set options for your prompt function</span></span>

<span data-ttu-id="c0cf7-118">Met deze opdracht worden de opties **AllScope** en **ReadOnly** ingesteld voor de functie prompt.</span><span class="sxs-lookup"><span data-stu-id="c0cf7-118">This command sets the **AllScope** and **ReadOnly** options for the prompt function.</span></span>
<span data-ttu-id="c0cf7-119">Met deze opdracht wordt de dynamische para meter **Options** van gebruikt `Set-Item` .</span><span class="sxs-lookup"><span data-stu-id="c0cf7-119">This command uses the **Options** dynamic parameter of `Set-Item`.</span></span>
<span data-ttu-id="c0cf7-120">De para meter **Options** is `Set-Item` alleen beschikbaar wanneer u deze met de **alias** of **functie** provider gebruikt.</span><span class="sxs-lookup"><span data-stu-id="c0cf7-120">The **Options** parameter is available in `Set-Item` only when you use it with the **Alias** or **Function** provider.</span></span>

```powershell
Set-Item -Path function:prompt -Options "AllScope,ReadOnly"
```

## <span data-ttu-id="c0cf7-121">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="c0cf7-121">PARAMETERS</span></span>

### <span data-ttu-id="c0cf7-122">-Credential</span><span class="sxs-lookup"><span data-stu-id="c0cf7-122">-Credential</span></span>

> [!NOTE]
> <span data-ttu-id="c0cf7-123">Deze para meter wordt niet ondersteund door providers die zijn geïnstalleerd met Power shell.</span><span class="sxs-lookup"><span data-stu-id="c0cf7-123">This parameter is not supported by any providers installed with PowerShell.</span></span>
> <span data-ttu-id="c0cf7-124">Gebruik [invoke-Command](../Microsoft.PowerShell.Core/Invoke-Command.md)om een andere gebruiker te imiteren of uw referenties te verhogen wanneer u deze cmdlet uitvoert.</span><span class="sxs-lookup"><span data-stu-id="c0cf7-124">To impersonate another user, or elevate your credentials when running this cmdlet, use [Invoke-Command](../Microsoft.PowerShell.Core/Invoke-Command.md).</span></span>

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

### <span data-ttu-id="c0cf7-125">-Uitsluiten</span><span class="sxs-lookup"><span data-stu-id="c0cf7-125">-Exclude</span></span>

<span data-ttu-id="c0cf7-126">Hiermee geeft u als een teken reeks matrix een item of items die met deze cmdlet worden uitgesloten in de bewerking.</span><span class="sxs-lookup"><span data-stu-id="c0cf7-126">Specifies, as a string array, an item or items that this cmdlet excludes in the operation.</span></span> <span data-ttu-id="c0cf7-127">De waarde van deze para meter komt in aanmerking voor de para meter **Path** .</span><span class="sxs-lookup"><span data-stu-id="c0cf7-127">The value of this parameter qualifies the **Path** parameter.</span></span> <span data-ttu-id="c0cf7-128">Voer een element of patroon van een pad in, zoals `*.txt` .</span><span class="sxs-lookup"><span data-stu-id="c0cf7-128">Enter a path element or pattern, such as `*.txt`.</span></span> <span data-ttu-id="c0cf7-129">Joker tekens zijn toegestaan.</span><span class="sxs-lookup"><span data-stu-id="c0cf7-129">Wildcard characters are permitted.</span></span> <span data-ttu-id="c0cf7-130">De **exclude** -para meter is alleen effectief wanneer de inhoud van een item wordt opgenomen, zoals `C:\Windows\*` , waarbij het Joker teken de inhoud van de `C:\Windows` map bevat.</span><span class="sxs-lookup"><span data-stu-id="c0cf7-130">The **Exclude** parameter is effective only when the command includes the contents of an item, such as `C:\Windows\*`, where the wildcard character specifies the contents of the `C:\Windows` directory.</span></span>

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

### <span data-ttu-id="c0cf7-131">-Filter</span><span class="sxs-lookup"><span data-stu-id="c0cf7-131">-Filter</span></span>

<span data-ttu-id="c0cf7-132">Hiermee geeft u een filter op om de para meter **Path** te kwalificeren.</span><span class="sxs-lookup"><span data-stu-id="c0cf7-132">Specifies a filter to qualify the **Path** parameter.</span></span> <span data-ttu-id="c0cf7-133">De [File System](../Microsoft.PowerShell.Core/About/about_FileSystem_Provider.md) -provider is de enige geïnstalleerde Power shell-provider die het gebruik van filters ondersteunt.</span><span class="sxs-lookup"><span data-stu-id="c0cf7-133">The [FileSystem](../Microsoft.PowerShell.Core/About/about_FileSystem_Provider.md) provider is the only installed PowerShell provider that supports the use of filters.</span></span> <span data-ttu-id="c0cf7-134">U kunt de syntaxis voor de filter taal van het **Bestands systeem** in [about_Wildcards](../Microsoft.PowerShell.Core/About/about_Wildcards.md)vinden.</span><span class="sxs-lookup"><span data-stu-id="c0cf7-134">You can find the syntax for the **FileSystem** filter language in [about_Wildcards](../Microsoft.PowerShell.Core/About/about_Wildcards.md).</span></span>
<span data-ttu-id="c0cf7-135">Filters zijn efficiënter dan andere para meters, omdat deze door de provider worden toegepast wanneer de cmdlet de objecten ophaalt in plaats van dat Power shell de objecten heeft gefilterd nadat ze zijn opgehaald.</span><span class="sxs-lookup"><span data-stu-id="c0cf7-135">Filters are more efficient than other parameters, because the provider applies them when the cmdlet gets the objects rather than having PowerShell filter the objects after they are retrieved.</span></span>

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

### <span data-ttu-id="c0cf7-136">-Force</span><span class="sxs-lookup"><span data-stu-id="c0cf7-136">-Force</span></span>

<span data-ttu-id="c0cf7-137">Hiermee wordt de cmdlet gedwongen om items in te stellen die anders niet kunnen worden gewijzigd, zoals een alleen-lezen alias of variabelen.</span><span class="sxs-lookup"><span data-stu-id="c0cf7-137">Forces the cmdlet to set items that cannot otherwise be changed, such as read-only alias or variables.</span></span> <span data-ttu-id="c0cf7-138">De cmdlet kan geen constante aliassen of variabelen wijzigen.</span><span class="sxs-lookup"><span data-stu-id="c0cf7-138">The cmdlet cannot change constant aliases or variables.</span></span>
<span data-ttu-id="c0cf7-139">De implementatie varieert van provider tot provider.</span><span class="sxs-lookup"><span data-stu-id="c0cf7-139">Implementation varies from provider to provider.</span></span>
<span data-ttu-id="c0cf7-140">Zie [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="c0cf7-140">For more information, see [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md).</span></span>
<span data-ttu-id="c0cf7-141">Zelfs met behulp van de para meter *forceren* , kan de cmdlet geen beveiligings beperkingen opheffen.</span><span class="sxs-lookup"><span data-stu-id="c0cf7-141">Even using the *Force* parameter, the cmdlet cannot override security restrictions.</span></span>

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

### <span data-ttu-id="c0cf7-142">-Include</span><span class="sxs-lookup"><span data-stu-id="c0cf7-142">-Include</span></span>

<span data-ttu-id="c0cf7-143">Hiermee wordt een teken reeks matrix opgegeven, een item of items die met deze cmdlet in de bewerking zijn opgenomen.</span><span class="sxs-lookup"><span data-stu-id="c0cf7-143">Specifies, as a string array, an item or items that this cmdlet includes in the operation.</span></span> <span data-ttu-id="c0cf7-144">De waarde van deze para meter komt in aanmerking voor de para meter **Path** .</span><span class="sxs-lookup"><span data-stu-id="c0cf7-144">The value of this parameter qualifies the **Path** parameter.</span></span> <span data-ttu-id="c0cf7-145">Voer een element of patroon van een pad in, zoals `"*.txt"` .</span><span class="sxs-lookup"><span data-stu-id="c0cf7-145">Enter a path element or pattern, such as `"*.txt"`.</span></span> <span data-ttu-id="c0cf7-146">Joker tekens zijn toegestaan.</span><span class="sxs-lookup"><span data-stu-id="c0cf7-146">Wildcard characters are permitted.</span></span> <span data-ttu-id="c0cf7-147">De para meter **include** is alleen effectief wanneer de inhoud van een item wordt opgenomen, zoals `C:\Windows\*` , waarbij het Joker teken de inhoud van de `C:\Windows` map bevat.</span><span class="sxs-lookup"><span data-stu-id="c0cf7-147">The **Include** parameter is effective only when the command includes the contents of an item, such as `C:\Windows\*`, where the wildcard character specifies the contents of the `C:\Windows` directory.</span></span>

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

### <span data-ttu-id="c0cf7-148">-LiteralPath</span><span class="sxs-lookup"><span data-stu-id="c0cf7-148">-LiteralPath</span></span>

<span data-ttu-id="c0cf7-149">Hiermee geeft u een pad naar een of meer locaties.</span><span class="sxs-lookup"><span data-stu-id="c0cf7-149">Specifies a path to one or more locations.</span></span> <span data-ttu-id="c0cf7-150">De waarde van **LiteralPath** wordt precies zo gebruikt als deze wordt getypt.</span><span class="sxs-lookup"><span data-stu-id="c0cf7-150">The value of **LiteralPath** is used exactly as it is typed.</span></span> <span data-ttu-id="c0cf7-151">Geen tekens worden geïnterpreteerd als joker tekens.</span><span class="sxs-lookup"><span data-stu-id="c0cf7-151">No characters are interpreted as wildcards.</span></span> <span data-ttu-id="c0cf7-152">Als het pad escape tekens bevat, plaatst u het tussen enkele aanhalings tekens.</span><span class="sxs-lookup"><span data-stu-id="c0cf7-152">If the path includes escape characters, enclose it in single quotation marks.</span></span> <span data-ttu-id="c0cf7-153">Enkele aanhalings tekens geven aan dat Power shell geen karakters interpreteert als escape reeksen.</span><span class="sxs-lookup"><span data-stu-id="c0cf7-153">Single quotation marks tell PowerShell not to interpret any characters as escape sequences.</span></span>

<span data-ttu-id="c0cf7-154">Zie [about_Quoting_Rules](../Microsoft.Powershell.Core/About/about_Quoting_Rules.md)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="c0cf7-154">For more information, see [about_Quoting_Rules](../Microsoft.Powershell.Core/About/about_Quoting_Rules.md).</span></span>

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

### <span data-ttu-id="c0cf7-155">-PassThru</span><span class="sxs-lookup"><span data-stu-id="c0cf7-155">-PassThru</span></span>

<span data-ttu-id="c0cf7-156">Geeft een object dat het item vertegenwoordigt in de pijp lijn.</span><span class="sxs-lookup"><span data-stu-id="c0cf7-156">Passes an object that represents the item to the pipeline.</span></span>
<span data-ttu-id="c0cf7-157">Deze cmdlet genereert standaard geen uitvoer.</span><span class="sxs-lookup"><span data-stu-id="c0cf7-157">By default, this cmdlet does not generate any output.</span></span>

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

### <span data-ttu-id="c0cf7-158">-Path</span><span class="sxs-lookup"><span data-stu-id="c0cf7-158">-Path</span></span>

<span data-ttu-id="c0cf7-159">Hiermee geeft u een pad op naar de locatie van de items.</span><span class="sxs-lookup"><span data-stu-id="c0cf7-159">Specifies a path of the location of the items.</span></span>
<span data-ttu-id="c0cf7-160">Joker tekens zijn toegestaan.</span><span class="sxs-lookup"><span data-stu-id="c0cf7-160">Wildcard characters are permitted.</span></span>

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

### <span data-ttu-id="c0cf7-161">-Waarde</span><span class="sxs-lookup"><span data-stu-id="c0cf7-161">-Value</span></span>

<span data-ttu-id="c0cf7-162">Hiermee geeft u een nieuwe waarde op voor het item.</span><span class="sxs-lookup"><span data-stu-id="c0cf7-162">Specifies a new value for the item.</span></span>

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

### <span data-ttu-id="c0cf7-163">-Confirm</span><span class="sxs-lookup"><span data-stu-id="c0cf7-163">-Confirm</span></span>

<span data-ttu-id="c0cf7-164">Hiermee wordt u gevraagd om bevestiging voordat u de cmdlet uitvoert.</span><span class="sxs-lookup"><span data-stu-id="c0cf7-164">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="c0cf7-165">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="c0cf7-165">-WhatIf</span></span>

<span data-ttu-id="c0cf7-166">Hiermee wordt weergegeven wat er zou gebeuren als u de cmdlet uitvoert.</span><span class="sxs-lookup"><span data-stu-id="c0cf7-166">Shows what would happen if the cmdlet runs.</span></span>
<span data-ttu-id="c0cf7-167">De cmdlet wordt niet uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="c0cf7-167">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="c0cf7-168">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="c0cf7-168">CommonParameters</span></span>

<span data-ttu-id="c0cf7-169">Deze cmdlet biedt ondersteuning voor de algemene para meters: `-Debug` , `-ErrorAction` , `-ErrorVariable` , `-InformationAction` , `-InformationVariable` , `-OutVariable` , `-OutBuffer` , `-PipelineVariable` , `-Verbose` , `-WarningAction` en `-WarningVariable` .</span><span class="sxs-lookup"><span data-stu-id="c0cf7-169">This cmdlet supports the common parameters: `-Debug`, `-ErrorAction`, `-ErrorVariable`, `-InformationAction`, `-InformationVariable`, `-OutVariable`, `-OutBuffer`, `-PipelineVariable`, `-Verbose`, `-WarningAction`, and `-WarningVariable`.</span></span> <span data-ttu-id="c0cf7-170">Zie [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="c0cf7-170">For more information, see [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md).</span></span>

## <span data-ttu-id="c0cf7-171">INVOER</span><span class="sxs-lookup"><span data-stu-id="c0cf7-171">INPUTS</span></span>

### <span data-ttu-id="c0cf7-172">System. object</span><span class="sxs-lookup"><span data-stu-id="c0cf7-172">System.Object</span></span>

<span data-ttu-id="c0cf7-173">U kunt een object dat de nieuwe waarde van het item vertegenwoordigt door sluizen naar deze cmdlet.</span><span class="sxs-lookup"><span data-stu-id="c0cf7-173">You can pipe an object that represents the new value of the item to this cmdlet.</span></span>

## <span data-ttu-id="c0cf7-174">UITVOER</span><span class="sxs-lookup"><span data-stu-id="c0cf7-174">OUTPUTS</span></span>

### <span data-ttu-id="c0cf7-175">Geen of een object dat het nieuwe of gewijzigde item voor stelt.</span><span class="sxs-lookup"><span data-stu-id="c0cf7-175">None or an object representing the new or changed item.</span></span>

<span data-ttu-id="c0cf7-176">Met deze cmdlet wordt een object dat het item vertegenwoordigt, gegenereerd als u de para meter *PassThru* opgeeft.</span><span class="sxs-lookup"><span data-stu-id="c0cf7-176">This cmdlet generates an object that represent the item, if you specify the *PassThru* parameter.</span></span>
<span data-ttu-id="c0cf7-177">Anders wordt met deze cmdlet geen uitvoer gegenereerd.</span><span class="sxs-lookup"><span data-stu-id="c0cf7-177">Otherwise, this cmdlet does not generate any output.</span></span>

## <span data-ttu-id="c0cf7-178">OPMERKINGEN</span><span class="sxs-lookup"><span data-stu-id="c0cf7-178">NOTES</span></span>

- <span data-ttu-id="c0cf7-179">`Set-Item` wordt niet ondersteund door de Power shell-bestandssysteem provider.</span><span class="sxs-lookup"><span data-stu-id="c0cf7-179">`Set-Item` is not supported by the PowerShell FileSystem provider.</span></span> <span data-ttu-id="c0cf7-180">Als u de waarden van items in het bestands systeem wilt wijzigen, gebruikt u de `Set-Content` cmdlet.</span><span class="sxs-lookup"><span data-stu-id="c0cf7-180">To change the values of items in the file system, use the `Set-Content` cmdlet.</span></span>
- <span data-ttu-id="c0cf7-181">In de register stations, `HKLM:` en `HKCU:` worden `Set-Item` de gegevens in de (standaard) waarde van een register sleutel gewijzigd.</span><span class="sxs-lookup"><span data-stu-id="c0cf7-181">In the Registry drives, `HKLM:` and `HKCU:`, `Set-Item` changes the data in the (Default) value of a registry key.</span></span>
  - <span data-ttu-id="c0cf7-182">Gebruik de cmdlet en om de namen van register sleutels te maken en te wijzigen `New-Item` `Rename-Item` .</span><span class="sxs-lookup"><span data-stu-id="c0cf7-182">To create and change the names of registry keys, use the `New-Item` and `Rename-Item` cmdlet.</span></span>
  - <span data-ttu-id="c0cf7-183">Als u de namen en gegevens in register waarden wilt wijzigen, gebruikt u de `New-ItemProperty` `Set-ItemProperty` `Rename-ItemProperty` cmdlets, en.</span><span class="sxs-lookup"><span data-stu-id="c0cf7-183">To change the names and data in registry values, use the `New-ItemProperty`, `Set-ItemProperty`, and `Rename-ItemProperty` cmdlets.</span></span>
- <span data-ttu-id="c0cf7-184">`Set-Item` is ontworpen om te werken met de gegevens die door elke provider worden weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="c0cf7-184">`Set-Item` is designed to work with the data exposed by any provider.</span></span>
  <span data-ttu-id="c0cf7-185">Als u een lijst wilt weer geven van de providers die beschikbaar zijn in uw sessie, typt u `Get-PsProvider` .</span><span class="sxs-lookup"><span data-stu-id="c0cf7-185">To list the providers available in your session, type `Get-PsProvider`.</span></span>
  <span data-ttu-id="c0cf7-186">Zie [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="c0cf7-186">For more information, see [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md).</span></span>

## <span data-ttu-id="c0cf7-187">GERELATEERDE KOPPELINGEN</span><span class="sxs-lookup"><span data-stu-id="c0cf7-187">RELATED LINKS</span></span>

[<span data-ttu-id="c0cf7-188">Wissen-item</span><span class="sxs-lookup"><span data-stu-id="c0cf7-188">Clear-Item</span></span>](Clear-Item.md)

[<span data-ttu-id="c0cf7-189">Kopie-item</span><span class="sxs-lookup"><span data-stu-id="c0cf7-189">Copy-Item</span></span>](Copy-Item.md)

[<span data-ttu-id="c0cf7-190">Get-item</span><span class="sxs-lookup"><span data-stu-id="c0cf7-190">Get-Item</span></span>](Get-Item.md)

[<span data-ttu-id="c0cf7-191">Invoke-item</span><span class="sxs-lookup"><span data-stu-id="c0cf7-191">Invoke-Item</span></span>](Invoke-Item.md)

[<span data-ttu-id="c0cf7-192">Item verplaatsen</span><span class="sxs-lookup"><span data-stu-id="c0cf7-192">Move-Item</span></span>](Move-Item.md)

[<span data-ttu-id="c0cf7-193">Nieuw-item</span><span class="sxs-lookup"><span data-stu-id="c0cf7-193">New-Item</span></span>](New-Item.md)

[<span data-ttu-id="c0cf7-194">Verwijderen-item</span><span class="sxs-lookup"><span data-stu-id="c0cf7-194">Remove-Item</span></span>](Remove-Item.md)

[<span data-ttu-id="c0cf7-195">Naam wijzigen-item</span><span class="sxs-lookup"><span data-stu-id="c0cf7-195">Rename-Item</span></span>](Rename-Item.md)

[<span data-ttu-id="c0cf7-196">about_Providers</span><span class="sxs-lookup"><span data-stu-id="c0cf7-196">about_Providers</span></span>](../Microsoft.PowerShell.Core/About/about_Providers.md)

