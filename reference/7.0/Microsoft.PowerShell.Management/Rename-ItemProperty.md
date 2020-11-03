---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 5/14/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/rename-itemproperty?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Rename-ItemProperty
ms.openlocfilehash: d9403a2572926101a7ccab8992013b60e4fb77f4
ms.sourcegitcommit: de63e9481cf8024883060aae61fb02c59c2de662
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/03/2020
ms.locfileid: "93249675"
---
# <span data-ttu-id="a65a5-103">Rename-ItemProperty</span><span class="sxs-lookup"><span data-stu-id="a65a5-103">Rename-ItemProperty</span></span>

## <span data-ttu-id="a65a5-104">SAMENVATTING</span><span class="sxs-lookup"><span data-stu-id="a65a5-104">SYNOPSIS</span></span>
<span data-ttu-id="a65a5-105">De naam van een eigenschap van een item wordt gewijzigd.</span><span class="sxs-lookup"><span data-stu-id="a65a5-105">Renames a property of an item.</span></span>

## <span data-ttu-id="a65a5-106">SYNTAXIS</span><span class="sxs-lookup"><span data-stu-id="a65a5-106">SYNTAX</span></span>

### <span data-ttu-id="a65a5-107">Pad (standaard)</span><span class="sxs-lookup"><span data-stu-id="a65a5-107">Path (Default)</span></span>

```
Rename-ItemProperty [-Path] <String> [-Name] <String> [-NewName] <String> [-PassThru] [-Force]
 [-Filter <String>] [-Include <String[]>] [-Exclude <String[]>] [-Credential <PSCredential>]
 [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="a65a5-108">LiteralPath</span><span class="sxs-lookup"><span data-stu-id="a65a5-108">LiteralPath</span></span>

```
Rename-ItemProperty -LiteralPath <String> [-Name] <String> [-NewName] <String> [-PassThru] [-Force]
 [-Filter <String>] [-Include <String[]>] [-Exclude <String[]>] [-Credential <PSCredential>]
 [-WhatIf] [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="a65a5-109">BESCHRIJVING</span><span class="sxs-lookup"><span data-stu-id="a65a5-109">DESCRIPTION</span></span>

<span data-ttu-id="a65a5-110">De `Rename-ItemProperty` cmdlet wijzigt de naam van een opgegeven item eigenschap.</span><span class="sxs-lookup"><span data-stu-id="a65a5-110">The `Rename-ItemProperty` cmdlet changes the name of a specified item property.</span></span>
<span data-ttu-id="a65a5-111">De waarde van de eigenschap is niet gewijzigd.</span><span class="sxs-lookup"><span data-stu-id="a65a5-111">The value of the property is not changed.</span></span>
<span data-ttu-id="a65a5-112">U kunt bijvoorbeeld gebruiken `Rename-ItemProperty` om de naam van een register vermelding te wijzigen.</span><span class="sxs-lookup"><span data-stu-id="a65a5-112">For example, you can use `Rename-ItemProperty` to change the name of a registry entry.</span></span>

## <span data-ttu-id="a65a5-113">VOORBEELDEN</span><span class="sxs-lookup"><span data-stu-id="a65a5-113">EXAMPLES</span></span>

### <span data-ttu-id="a65a5-114">Voor beeld 1: de naam van een register vermelding wijzigen</span><span class="sxs-lookup"><span data-stu-id="a65a5-114">Example 1: Rename a registry entry</span></span>

<span data-ttu-id="a65a5-115">Met deze opdracht wordt de naam van de configuratie register vermelding die is opgenomen in de sleutel, gewijzigd in `HKEY_LOCAL_MACHINE\Software\SmpApplication` ' oldconfig '.</span><span class="sxs-lookup"><span data-stu-id="a65a5-115">This command renames the config registry entry that is contained in the `HKEY_LOCAL_MACHINE\Software\SmpApplication` key to "oldconfig".</span></span>

```powershell
Rename-ItemProperty -Path HKLM:\Software\SmpApplication -Name config -NewName oldconfig
```

## <span data-ttu-id="a65a5-116">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="a65a5-116">PARAMETERS</span></span>

### <span data-ttu-id="a65a5-117">-Credential</span><span class="sxs-lookup"><span data-stu-id="a65a5-117">-Credential</span></span>

> [!NOTE]
> <span data-ttu-id="a65a5-118">Deze para meter wordt niet ondersteund door providers die zijn geïnstalleerd met Power shell.</span><span class="sxs-lookup"><span data-stu-id="a65a5-118">This parameter is not supported by any providers installed with PowerShell.</span></span>
> <span data-ttu-id="a65a5-119">Gebruik [invoke-Command](../Microsoft.PowerShell.Core/Invoke-Command.md)om een andere gebruiker te imiteren of uw referenties te verhogen wanneer u deze cmdlet uitvoert.</span><span class="sxs-lookup"><span data-stu-id="a65a5-119">To impersonate another user, or elevate your credentials when running this cmdlet, use [Invoke-Command](../Microsoft.PowerShell.Core/Invoke-Command.md).</span></span>

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

### <span data-ttu-id="a65a5-120">-Uitsluiten</span><span class="sxs-lookup"><span data-stu-id="a65a5-120">-Exclude</span></span>

<span data-ttu-id="a65a5-121">Hiermee geeft u als een teken reeks matrix een item of items die met deze cmdlet worden uitgesloten in de bewerking.</span><span class="sxs-lookup"><span data-stu-id="a65a5-121">Specifies, as a string array, an item or items that this cmdlet excludes in the operation.</span></span> <span data-ttu-id="a65a5-122">De waarde van deze para meter komt in aanmerking voor de para meter **Path** .</span><span class="sxs-lookup"><span data-stu-id="a65a5-122">The value of this parameter qualifies the **Path** parameter.</span></span> <span data-ttu-id="a65a5-123">Voer een element of patroon van een pad in, zoals `*.txt` .</span><span class="sxs-lookup"><span data-stu-id="a65a5-123">Enter a path element or pattern, such as `*.txt`.</span></span> <span data-ttu-id="a65a5-124">Joker tekens zijn toegestaan.</span><span class="sxs-lookup"><span data-stu-id="a65a5-124">Wildcard characters are permitted.</span></span> <span data-ttu-id="a65a5-125">De **exclude** -para meter is alleen effectief wanneer de inhoud van een item wordt opgenomen, zoals `C:\Windows\*` , waarbij het Joker teken de inhoud van de `C:\Windows` map bevat.</span><span class="sxs-lookup"><span data-stu-id="a65a5-125">The **Exclude** parameter is effective only when the command includes the contents of an item, such as `C:\Windows\*`, where the wildcard character specifies the contents of the `C:\Windows` directory.</span></span>

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

### <span data-ttu-id="a65a5-126">-Filter</span><span class="sxs-lookup"><span data-stu-id="a65a5-126">-Filter</span></span>

<span data-ttu-id="a65a5-127">Hiermee geeft u een filter op om de para meter **Path** te kwalificeren.</span><span class="sxs-lookup"><span data-stu-id="a65a5-127">Specifies a filter to qualify the **Path** parameter.</span></span> <span data-ttu-id="a65a5-128">De [File System](../Microsoft.PowerShell.Core/About/about_FileSystem_Provider.md) -provider is de enige geïnstalleerde Power shell-provider die het gebruik van filters ondersteunt.</span><span class="sxs-lookup"><span data-stu-id="a65a5-128">The [FileSystem](../Microsoft.PowerShell.Core/About/about_FileSystem_Provider.md) provider is the only installed PowerShell provider that supports the use of filters.</span></span> <span data-ttu-id="a65a5-129">U kunt de syntaxis voor de filter taal van het **Bestands systeem** in [about_Wildcards](../Microsoft.PowerShell.Core/About/about_Wildcards.md)vinden.</span><span class="sxs-lookup"><span data-stu-id="a65a5-129">You can find the syntax for the **FileSystem** filter language in [about_Wildcards](../Microsoft.PowerShell.Core/About/about_Wildcards.md).</span></span>
<span data-ttu-id="a65a5-130">Filters zijn efficiënter dan andere para meters, omdat deze door de provider worden toegepast wanneer de cmdlet de objecten ophaalt in plaats van dat Power shell de objecten heeft gefilterd nadat ze zijn opgehaald.</span><span class="sxs-lookup"><span data-stu-id="a65a5-130">Filters are more efficient than other parameters, because the provider applies them when the cmdlet gets the objects rather than having PowerShell filter the objects after they are retrieved.</span></span>

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

### <span data-ttu-id="a65a5-131">-Force</span><span class="sxs-lookup"><span data-stu-id="a65a5-131">-Force</span></span>

<span data-ttu-id="a65a5-132">Hiermee wordt de naam van een eigenschap van een object dat niet kan worden geopend door de gebruiker, door de cmdlet afgedwongen.</span><span class="sxs-lookup"><span data-stu-id="a65a5-132">Forces the cmdlet to rename a property of an object that cannot otherwise be accessed by the user.</span></span>
<span data-ttu-id="a65a5-133">De implementatie varieert van provider tot provider.</span><span class="sxs-lookup"><span data-stu-id="a65a5-133">Implementation varies from provider to provider.</span></span>
<span data-ttu-id="a65a5-134">Zie [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="a65a5-134">For more information, see [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md).</span></span>

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

### <span data-ttu-id="a65a5-135">-Include</span><span class="sxs-lookup"><span data-stu-id="a65a5-135">-Include</span></span>

<span data-ttu-id="a65a5-136">Hiermee wordt een teken reeks matrix opgegeven, een item of items die met deze cmdlet in de bewerking zijn opgenomen.</span><span class="sxs-lookup"><span data-stu-id="a65a5-136">Specifies, as a string array, an item or items that this cmdlet includes in the operation.</span></span> <span data-ttu-id="a65a5-137">De waarde van deze para meter komt in aanmerking voor de para meter **Path** .</span><span class="sxs-lookup"><span data-stu-id="a65a5-137">The value of this parameter qualifies the **Path** parameter.</span></span> <span data-ttu-id="a65a5-138">Voer een element of patroon van een pad in, zoals `"*.txt"` .</span><span class="sxs-lookup"><span data-stu-id="a65a5-138">Enter a path element or pattern, such as `"*.txt"`.</span></span> <span data-ttu-id="a65a5-139">Joker tekens zijn toegestaan.</span><span class="sxs-lookup"><span data-stu-id="a65a5-139">Wildcard characters are permitted.</span></span> <span data-ttu-id="a65a5-140">De para meter **include** is alleen effectief wanneer de inhoud van een item wordt opgenomen, zoals `C:\Windows\*` , waarbij het Joker teken de inhoud van de `C:\Windows` map bevat.</span><span class="sxs-lookup"><span data-stu-id="a65a5-140">The **Include** parameter is effective only when the command includes the contents of an item, such as `C:\Windows\*`, where the wildcard character specifies the contents of the `C:\Windows` directory.</span></span>

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

### <span data-ttu-id="a65a5-141">-LiteralPath</span><span class="sxs-lookup"><span data-stu-id="a65a5-141">-LiteralPath</span></span>

<span data-ttu-id="a65a5-142">Hiermee geeft u een pad naar een of meer locaties.</span><span class="sxs-lookup"><span data-stu-id="a65a5-142">Specifies a path to one or more locations.</span></span> <span data-ttu-id="a65a5-143">De waarde van **LiteralPath** wordt precies zo gebruikt als deze wordt getypt.</span><span class="sxs-lookup"><span data-stu-id="a65a5-143">The value of **LiteralPath** is used exactly as it is typed.</span></span> <span data-ttu-id="a65a5-144">Geen tekens worden geïnterpreteerd als joker tekens.</span><span class="sxs-lookup"><span data-stu-id="a65a5-144">No characters are interpreted as wildcards.</span></span> <span data-ttu-id="a65a5-145">Als het pad escape tekens bevat, plaatst u het tussen enkele aanhalings tekens.</span><span class="sxs-lookup"><span data-stu-id="a65a5-145">If the path includes escape characters, enclose it in single quotation marks.</span></span> <span data-ttu-id="a65a5-146">Enkele aanhalings tekens geven aan dat Power shell geen karakters interpreteert als escape reeksen.</span><span class="sxs-lookup"><span data-stu-id="a65a5-146">Single quotation marks tell PowerShell not to interpret any characters as escape sequences.</span></span>

<span data-ttu-id="a65a5-147">Zie [about_Quoting_Rules](../Microsoft.Powershell.Core/About/about_Quoting_Rules.md)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="a65a5-147">For more information, see [about_Quoting_Rules](../Microsoft.Powershell.Core/About/about_Quoting_Rules.md).</span></span>

```yaml
Type: System.String
Parameter Sets: LiteralPath
Aliases: PSPath, LP

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="a65a5-148">-Name</span><span class="sxs-lookup"><span data-stu-id="a65a5-148">-Name</span></span>

<span data-ttu-id="a65a5-149">Hiermee geeft u de huidige naam op van de eigenschap waarvan de naam moet worden gewijzigd.</span><span class="sxs-lookup"><span data-stu-id="a65a5-149">Specifies the current name of the property to rename.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases: PSProperty

Required: True
Position: 1
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="a65a5-150">-NewName</span><span class="sxs-lookup"><span data-stu-id="a65a5-150">-NewName</span></span>

<span data-ttu-id="a65a5-151">Hiermee geeft u de nieuwe naam voor de eigenschap op.</span><span class="sxs-lookup"><span data-stu-id="a65a5-151">Specifies the new name for the property.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: True
Position: 2
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="a65a5-152">-PassThru</span><span class="sxs-lookup"><span data-stu-id="a65a5-152">-PassThru</span></span>

<span data-ttu-id="a65a5-153">Retourneert een object dat de eigenschap item vertegenwoordigt.</span><span class="sxs-lookup"><span data-stu-id="a65a5-153">Returns an object that represents the item property.</span></span>
<span data-ttu-id="a65a5-154">Deze cmdlet genereert standaard geen uitvoer.</span><span class="sxs-lookup"><span data-stu-id="a65a5-154">By default, this cmdlet does not generate any output.</span></span>

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

### <span data-ttu-id="a65a5-155">-Path</span><span class="sxs-lookup"><span data-stu-id="a65a5-155">-Path</span></span>

<span data-ttu-id="a65a5-156">Hiermee geeft u het pad op van het item waarvan u de naam wilt wijzigen.</span><span class="sxs-lookup"><span data-stu-id="a65a5-156">Specifies the path of the item to rename.</span></span>
<span data-ttu-id="a65a5-157">Joker tekens zijn toegestaan.</span><span class="sxs-lookup"><span data-stu-id="a65a5-157">Wildcard characters are permitted.</span></span>

```yaml
Type: System.String
Parameter Sets: Path
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: True
```

### <span data-ttu-id="a65a5-158">-Confirm</span><span class="sxs-lookup"><span data-stu-id="a65a5-158">-Confirm</span></span>

<span data-ttu-id="a65a5-159">Hiermee wordt u gevraagd om bevestiging voordat u de cmdlet uitvoert.</span><span class="sxs-lookup"><span data-stu-id="a65a5-159">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="a65a5-160">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="a65a5-160">-WhatIf</span></span>

<span data-ttu-id="a65a5-161">Hiermee wordt weergegeven wat er zou gebeuren als u de cmdlet uitvoert.</span><span class="sxs-lookup"><span data-stu-id="a65a5-161">Shows what would happen if the cmdlet runs.</span></span>
<span data-ttu-id="a65a5-162">De cmdlet wordt niet uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="a65a5-162">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="a65a5-163">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="a65a5-163">CommonParameters</span></span>

<span data-ttu-id="a65a5-164">Deze cmdlet biedt ondersteuning voor de algemene para meters: `-Debug` , `-ErrorAction` , `-ErrorVariable` , `-InformationAction` , `-InformationVariable` , `-OutVariable` , `-OutBuffer` , `-PipelineVariable` , `-Verbose` , `-WarningAction` en `-WarningVariable` .</span><span class="sxs-lookup"><span data-stu-id="a65a5-164">This cmdlet supports the common parameters: `-Debug`, `-ErrorAction`, `-ErrorVariable`, `-InformationAction`, `-InformationVariable`, `-OutVariable`, `-OutBuffer`, `-PipelineVariable`, `-Verbose`, `-WarningAction`, and `-WarningVariable`.</span></span> <span data-ttu-id="a65a5-165">Zie [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="a65a5-165">For more information, see [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md).</span></span>

## <span data-ttu-id="a65a5-166">INVOER</span><span class="sxs-lookup"><span data-stu-id="a65a5-166">INPUTS</span></span>

### <span data-ttu-id="a65a5-167">System. String</span><span class="sxs-lookup"><span data-stu-id="a65a5-167">System.String</span></span>

<span data-ttu-id="a65a5-168">U kunt een teken reeks die een pad bevat, maar geen letterlijk pad, naar deze cmdlet pipet.</span><span class="sxs-lookup"><span data-stu-id="a65a5-168">You can pipe a string that contains a path, but not a literal path, to this cmdlet.</span></span>

## <span data-ttu-id="a65a5-169">UITVOER</span><span class="sxs-lookup"><span data-stu-id="a65a5-169">OUTPUTS</span></span>

### <span data-ttu-id="a65a5-170">Geen, System. Management. Automation. PSCustomObject</span><span class="sxs-lookup"><span data-stu-id="a65a5-170">None, System.Management.Automation.PSCustomObject</span></span>

<span data-ttu-id="a65a5-171">Met deze cmdlet wordt een **PSCustomObject** gegenereerd die de eigenschap item met een andere naam vertegenwoordigt als u de para meter **PassThru** opgeeft.</span><span class="sxs-lookup"><span data-stu-id="a65a5-171">This cmdlet generates a **PSCustomObject** that represents the renamed item property, if you specify the **PassThru** parameter.</span></span> <span data-ttu-id="a65a5-172">Anders wordt met deze cmdlet geen uitvoer gegenereerd.</span><span class="sxs-lookup"><span data-stu-id="a65a5-172">Otherwise, this cmdlet does not generate any output.</span></span>

## <span data-ttu-id="a65a5-173">OPMERKINGEN</span><span class="sxs-lookup"><span data-stu-id="a65a5-173">NOTES</span></span>

<span data-ttu-id="a65a5-174">`Remove-ItemProperty` is ontworpen om te werken met de gegevens die door elke provider worden weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="a65a5-174">`Remove-ItemProperty` is designed to work with the data exposed by any provider.</span></span> <span data-ttu-id="a65a5-175">Als u een lijst wilt weer geven van de providers die beschikbaar zijn in uw sessie, typt u `Get-PSProvider` .</span><span class="sxs-lookup"><span data-stu-id="a65a5-175">To list the providers available in your session, type `Get-PSProvider`.</span></span> <span data-ttu-id="a65a5-176">Zie [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="a65a5-176">For more information, see [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md).</span></span>

## <span data-ttu-id="a65a5-177">GERELATEERDE KOPPELINGEN</span><span class="sxs-lookup"><span data-stu-id="a65a5-177">RELATED LINKS</span></span>

[<span data-ttu-id="a65a5-178">Wissen-item Property</span><span class="sxs-lookup"><span data-stu-id="a65a5-178">Clear-ItemProperty</span></span>](Clear-ItemProperty.md)

[<span data-ttu-id="a65a5-179">Kopiëren-item Property</span><span class="sxs-lookup"><span data-stu-id="a65a5-179">Copy-ItemProperty</span></span>](Copy-ItemProperty.md)

[<span data-ttu-id="a65a5-180">Get-item Property</span><span class="sxs-lookup"><span data-stu-id="a65a5-180">Get-ItemProperty</span></span>](Get-ItemProperty.md)

[<span data-ttu-id="a65a5-181">Verplaatsen-item Property</span><span class="sxs-lookup"><span data-stu-id="a65a5-181">Move-ItemProperty</span></span>](Move-ItemProperty.md)

[<span data-ttu-id="a65a5-182">Nieuw-item Property</span><span class="sxs-lookup"><span data-stu-id="a65a5-182">New-ItemProperty</span></span>](New-ItemProperty.md)

[<span data-ttu-id="a65a5-183">Verwijderen-item Property</span><span class="sxs-lookup"><span data-stu-id="a65a5-183">Remove-ItemProperty</span></span>](Remove-ItemProperty.md)

[<span data-ttu-id="a65a5-184">Naam wijzigen-item</span><span class="sxs-lookup"><span data-stu-id="a65a5-184">Rename-Item</span></span>](Rename-Item.md)

[<span data-ttu-id="a65a5-185">Set-item Property</span><span class="sxs-lookup"><span data-stu-id="a65a5-185">Set-ItemProperty</span></span>](Set-ItemProperty.md)

[<span data-ttu-id="a65a5-186">about_Providers</span><span class="sxs-lookup"><span data-stu-id="a65a5-186">about_Providers</span></span>](../Microsoft.PowerShell.Core/About/about_Providers.md)
