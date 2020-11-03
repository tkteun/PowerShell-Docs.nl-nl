---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 5/14/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/copy-itemproperty?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Copy-ItemProperty
ms.openlocfilehash: 9fddb6003627162094b89f738071e977cae77e99
ms.sourcegitcommit: de63e9481cf8024883060aae61fb02c59c2de662
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/03/2020
ms.locfileid: "93249383"
---
# <span data-ttu-id="c73f1-103">Copy-ItemProperty</span><span class="sxs-lookup"><span data-stu-id="c73f1-103">Copy-ItemProperty</span></span>

## <span data-ttu-id="c73f1-104">SAMENVATTING</span><span class="sxs-lookup"><span data-stu-id="c73f1-104">SYNOPSIS</span></span>
<span data-ttu-id="c73f1-105">Hiermee kopieert u een eigenschap en waarde van een opgegeven locatie naar een andere locatie.</span><span class="sxs-lookup"><span data-stu-id="c73f1-105">Copies a property and value from a specified location to another location.</span></span>

## <span data-ttu-id="c73f1-106">SYNTAXIS</span><span class="sxs-lookup"><span data-stu-id="c73f1-106">SYNTAX</span></span>

### <span data-ttu-id="c73f1-107">Pad (standaard)</span><span class="sxs-lookup"><span data-stu-id="c73f1-107">Path (Default)</span></span>

```
Copy-ItemProperty [-Path] <String[]> [-Name] <String> [-Destination] <String> [-PassThru] [-Force]
 [-Filter <String>] [-Include <String[]>] [-Exclude <String[]>] [-Credential <PSCredential>]
 [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="c73f1-108">LiteralPath</span><span class="sxs-lookup"><span data-stu-id="c73f1-108">LiteralPath</span></span>

```
Copy-ItemProperty -LiteralPath <String[]> [-Name] <String> [-Destination] <String> [-PassThru] [-Force]
 [-Filter <String>] [-Include <String[]>] [-Exclude <String[]>] [-Credential <PSCredential>]
 [-WhatIf] [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="c73f1-109">BESCHRIJVING</span><span class="sxs-lookup"><span data-stu-id="c73f1-109">DESCRIPTION</span></span>

<span data-ttu-id="c73f1-110">`Copy-ItemProperty`Met de cmdlet worden een eigenschap en waarde van een opgegeven locatie naar een andere locatie gekopieerd.</span><span class="sxs-lookup"><span data-stu-id="c73f1-110">The `Copy-ItemProperty` cmdlet copies a property and value from a specified location to another location.</span></span>
<span data-ttu-id="c73f1-111">U kunt deze cmdlet bijvoorbeeld gebruiken om een of meer Register vermeldingen van een register sleutel naar een andere register sleutel te kopiëren.</span><span class="sxs-lookup"><span data-stu-id="c73f1-111">For instance, you can use this cmdlet to copy one or more registry entries from one registry key to another registry key.</span></span>

## <span data-ttu-id="c73f1-112">VOORBEELDEN</span><span class="sxs-lookup"><span data-stu-id="c73f1-112">EXAMPLES</span></span>

### <span data-ttu-id="c73f1-113">Voor beeld 1: een eigenschap van een register sleutel naar een andere register sleutel kopiëren</span><span class="sxs-lookup"><span data-stu-id="c73f1-113">Example 1: Copy a property from a registry key to another registry key</span></span>

<span data-ttu-id="c73f1-114">Met deze opdracht wordt de eigenschap met de naam ' MyProperty ' gekopieerd van de register sleutel ' mijn toepassing ' naar de register sleutel ' MyApplicationRev2 '.</span><span class="sxs-lookup"><span data-stu-id="c73f1-114">This command copies the property named "MyProperty" from the "MyApplication" registry key to the "MyApplicationRev2" registry key.</span></span>

```powershell
Copy-ItemProperty -Path "MyApplication" -Destination "HKLM:\Software\MyApplicationRev2" -Name "MyProperty"
```

## <span data-ttu-id="c73f1-115">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="c73f1-115">PARAMETERS</span></span>

### <span data-ttu-id="c73f1-116">-Credential</span><span class="sxs-lookup"><span data-stu-id="c73f1-116">-Credential</span></span>

> [!NOTE]
> <span data-ttu-id="c73f1-117">Deze para meter wordt niet ondersteund door providers die zijn geïnstalleerd met Power shell.</span><span class="sxs-lookup"><span data-stu-id="c73f1-117">This parameter is not supported by any providers installed with PowerShell.</span></span>
> <span data-ttu-id="c73f1-118">Gebruik [invoke-Command](../Microsoft.PowerShell.Core/Invoke-Command.md)om een andere gebruiker te imiteren of uw referenties te verhogen wanneer u deze cmdlet uitvoert.</span><span class="sxs-lookup"><span data-stu-id="c73f1-118">To impersonate another user, or elevate your credentials when running this cmdlet, use [Invoke-Command](../Microsoft.PowerShell.Core/Invoke-Command.md).</span></span>

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

### <span data-ttu-id="c73f1-119">-Bestemming</span><span class="sxs-lookup"><span data-stu-id="c73f1-119">-Destination</span></span>

<span data-ttu-id="c73f1-120">Hiermee geeft u het pad naar de doel locatie.</span><span class="sxs-lookup"><span data-stu-id="c73f1-120">Specifies the path to the destination location.</span></span>

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

### <span data-ttu-id="c73f1-121">-Uitsluiten</span><span class="sxs-lookup"><span data-stu-id="c73f1-121">-Exclude</span></span>

<span data-ttu-id="c73f1-122">Hiermee geeft u als een teken reeks matrix een item of items die met deze cmdlet worden uitgesloten in de bewerking.</span><span class="sxs-lookup"><span data-stu-id="c73f1-122">Specifies, as a string array, an item or items that this cmdlet excludes in the operation.</span></span> <span data-ttu-id="c73f1-123">De waarde van deze para meter komt in aanmerking voor de para meter **Path** .</span><span class="sxs-lookup"><span data-stu-id="c73f1-123">The value of this parameter qualifies the **Path** parameter.</span></span> <span data-ttu-id="c73f1-124">Voer een element of patroon van een pad in, zoals `*.txt` .</span><span class="sxs-lookup"><span data-stu-id="c73f1-124">Enter a path element or pattern, such as `*.txt`.</span></span> <span data-ttu-id="c73f1-125">Joker tekens zijn toegestaan.</span><span class="sxs-lookup"><span data-stu-id="c73f1-125">Wildcard characters are permitted.</span></span> <span data-ttu-id="c73f1-126">De **exclude** -para meter is alleen effectief wanneer de inhoud van een item wordt opgenomen, zoals `C:\Windows\*` , waarbij het Joker teken de inhoud van de `C:\Windows` map bevat.</span><span class="sxs-lookup"><span data-stu-id="c73f1-126">The **Exclude** parameter is effective only when the command includes the contents of an item, such as `C:\Windows\*`, where the wildcard character specifies the contents of the `C:\Windows` directory.</span></span>

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

### <span data-ttu-id="c73f1-127">-Filter</span><span class="sxs-lookup"><span data-stu-id="c73f1-127">-Filter</span></span>

<span data-ttu-id="c73f1-128">Hiermee geeft u een filter op om de para meter **Path** te kwalificeren.</span><span class="sxs-lookup"><span data-stu-id="c73f1-128">Specifies a filter to qualify the **Path** parameter.</span></span> <span data-ttu-id="c73f1-129">De [File System](../Microsoft.PowerShell.Core/About/about_FileSystem_Provider.md) -provider is de enige geïnstalleerde Power shell-provider die het gebruik van filters ondersteunt.</span><span class="sxs-lookup"><span data-stu-id="c73f1-129">The [FileSystem](../Microsoft.PowerShell.Core/About/about_FileSystem_Provider.md) provider is the only installed PowerShell provider that supports the use of filters.</span></span> <span data-ttu-id="c73f1-130">U kunt de syntaxis voor de filter taal van het **Bestands systeem** in [about_Wildcards](../Microsoft.PowerShell.Core/About/about_Wildcards.md)vinden.</span><span class="sxs-lookup"><span data-stu-id="c73f1-130">You can find the syntax for the **FileSystem** filter language in [about_Wildcards](../Microsoft.PowerShell.Core/About/about_Wildcards.md).</span></span>
<span data-ttu-id="c73f1-131">Filters zijn efficiënter dan andere para meters, omdat deze door de provider worden toegepast wanneer de cmdlet de objecten ophaalt in plaats van dat Power shell de objecten heeft gefilterd nadat ze zijn opgehaald.</span><span class="sxs-lookup"><span data-stu-id="c73f1-131">Filters are more efficient than other parameters, because the provider applies them when the cmdlet gets the objects rather than having PowerShell filter the objects after they are retrieved.</span></span>

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

### <span data-ttu-id="c73f1-132">-Force</span><span class="sxs-lookup"><span data-stu-id="c73f1-132">-Force</span></span>

<span data-ttu-id="c73f1-133">Hiermee wordt de opdracht uitgevoerd zonder dat de gebruiker om bevestiging wordt gevraagd.</span><span class="sxs-lookup"><span data-stu-id="c73f1-133">Forces the command to run without asking for user confirmation.</span></span>
<span data-ttu-id="c73f1-134">De implementatie varieert van provider tot provider.</span><span class="sxs-lookup"><span data-stu-id="c73f1-134">Implementation varies from provider to provider.</span></span>

<span data-ttu-id="c73f1-135">Zie [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="c73f1-135">For more information, see [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md).</span></span>

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

### <span data-ttu-id="c73f1-136">-Include</span><span class="sxs-lookup"><span data-stu-id="c73f1-136">-Include</span></span>

<span data-ttu-id="c73f1-137">Hiermee wordt een teken reeks matrix opgegeven, een item of items die met deze cmdlet in de bewerking zijn opgenomen.</span><span class="sxs-lookup"><span data-stu-id="c73f1-137">Specifies, as a string array, an item or items that this cmdlet includes in the operation.</span></span> <span data-ttu-id="c73f1-138">De waarde van deze para meter komt in aanmerking voor de para meter **Path** .</span><span class="sxs-lookup"><span data-stu-id="c73f1-138">The value of this parameter qualifies the **Path** parameter.</span></span> <span data-ttu-id="c73f1-139">Voer een element of patroon van een pad in, zoals `"*.txt"` .</span><span class="sxs-lookup"><span data-stu-id="c73f1-139">Enter a path element or pattern, such as `"*.txt"`.</span></span> <span data-ttu-id="c73f1-140">Joker tekens zijn toegestaan.</span><span class="sxs-lookup"><span data-stu-id="c73f1-140">Wildcard characters are permitted.</span></span> <span data-ttu-id="c73f1-141">De para meter **include** is alleen effectief wanneer de inhoud van een item wordt opgenomen, zoals `C:\Windows\*` , waarbij het Joker teken de inhoud van de `C:\Windows` map bevat.</span><span class="sxs-lookup"><span data-stu-id="c73f1-141">The **Include** parameter is effective only when the command includes the contents of an item, such as `C:\Windows\*`, where the wildcard character specifies the contents of the `C:\Windows` directory.</span></span>

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

### <span data-ttu-id="c73f1-142">-LiteralPath</span><span class="sxs-lookup"><span data-stu-id="c73f1-142">-LiteralPath</span></span>

<span data-ttu-id="c73f1-143">Hiermee geeft u een pad naar een of meer locaties.</span><span class="sxs-lookup"><span data-stu-id="c73f1-143">Specifies a path to one or more locations.</span></span> <span data-ttu-id="c73f1-144">De waarde van **LiteralPath** wordt precies zo gebruikt als deze wordt getypt.</span><span class="sxs-lookup"><span data-stu-id="c73f1-144">The value of **LiteralPath** is used exactly as it is typed.</span></span> <span data-ttu-id="c73f1-145">Geen tekens worden geïnterpreteerd als joker tekens.</span><span class="sxs-lookup"><span data-stu-id="c73f1-145">No characters are interpreted as wildcards.</span></span> <span data-ttu-id="c73f1-146">Als het pad escape tekens bevat, plaatst u het tussen enkele aanhalings tekens.</span><span class="sxs-lookup"><span data-stu-id="c73f1-146">If the path includes escape characters, enclose it in single quotation marks.</span></span> <span data-ttu-id="c73f1-147">Enkele aanhalings tekens geven aan dat Power shell geen karakters interpreteert als escape reeksen.</span><span class="sxs-lookup"><span data-stu-id="c73f1-147">Single quotation marks tell PowerShell not to interpret any characters as escape sequences.</span></span>

<span data-ttu-id="c73f1-148">Zie [about_Quoting_Rules](../Microsoft.Powershell.Core/About/about_Quoting_Rules.md)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="c73f1-148">For more information, see [about_Quoting_Rules](../Microsoft.Powershell.Core/About/about_Quoting_Rules.md).</span></span>

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

### <span data-ttu-id="c73f1-149">-Name</span><span class="sxs-lookup"><span data-stu-id="c73f1-149">-Name</span></span>

<span data-ttu-id="c73f1-150">Hiermee geeft u de naam op van de eigenschap die moet worden gekopieerd.</span><span class="sxs-lookup"><span data-stu-id="c73f1-150">Specifies the name of the property to be copied.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases: PSProperty

Required: True
Position: 2
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="c73f1-151">-PassThru</span><span class="sxs-lookup"><span data-stu-id="c73f1-151">-PassThru</span></span>

<span data-ttu-id="c73f1-152">Retourneert een object dat het item vertegenwoordigt waarmee u werkt.</span><span class="sxs-lookup"><span data-stu-id="c73f1-152">Returns an object representing the item with which you are working.</span></span>
<span data-ttu-id="c73f1-153">Deze cmdlet genereert standaard geen uitvoer.</span><span class="sxs-lookup"><span data-stu-id="c73f1-153">By default, this cmdlet does not generate any output.</span></span>

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

### <span data-ttu-id="c73f1-154">-Path</span><span class="sxs-lookup"><span data-stu-id="c73f1-154">-Path</span></span>

<span data-ttu-id="c73f1-155">Geeft als een teken reeks matrix het pad naar de eigenschap die moet worden gekopieerd.</span><span class="sxs-lookup"><span data-stu-id="c73f1-155">Specifies, as a string array, the path to the property to be copied.</span></span>
<span data-ttu-id="c73f1-156">Joker tekens zijn toegestaan.</span><span class="sxs-lookup"><span data-stu-id="c73f1-156">Wildcard characters are permitted.</span></span>

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

### <span data-ttu-id="c73f1-157">-Confirm</span><span class="sxs-lookup"><span data-stu-id="c73f1-157">-Confirm</span></span>

<span data-ttu-id="c73f1-158">Hiermee wordt u gevraagd om bevestiging voordat u de cmdlet uitvoert.</span><span class="sxs-lookup"><span data-stu-id="c73f1-158">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="c73f1-159">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="c73f1-159">-WhatIf</span></span>

<span data-ttu-id="c73f1-160">Hiermee wordt weergegeven wat er zou gebeuren als u de cmdlet uitvoert.</span><span class="sxs-lookup"><span data-stu-id="c73f1-160">Shows what would happen if the cmdlet runs.</span></span>
<span data-ttu-id="c73f1-161">De cmdlet wordt niet uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="c73f1-161">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="c73f1-162">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="c73f1-162">CommonParameters</span></span>

<span data-ttu-id="c73f1-163">Deze cmdlet biedt ondersteuning voor de algemene para meters: `-Debug` , `-ErrorAction` , `-ErrorVariable` , `-InformationAction` , `-InformationVariable` , `-OutVariable` , `-OutBuffer` , `-PipelineVariable` , `-Verbose` , `-WarningAction` en `-WarningVariable` .</span><span class="sxs-lookup"><span data-stu-id="c73f1-163">This cmdlet supports the common parameters: `-Debug`, `-ErrorAction`, `-ErrorVariable`, `-InformationAction`, `-InformationVariable`, `-OutVariable`, `-OutBuffer`, `-PipelineVariable`, `-Verbose`, `-WarningAction`, and `-WarningVariable`.</span></span> <span data-ttu-id="c73f1-164">Zie [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="c73f1-164">For more information, see [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md).</span></span>

## <span data-ttu-id="c73f1-165">INVOER</span><span class="sxs-lookup"><span data-stu-id="c73f1-165">INPUTS</span></span>

### <span data-ttu-id="c73f1-166">System. String</span><span class="sxs-lookup"><span data-stu-id="c73f1-166">System.String</span></span>

<span data-ttu-id="c73f1-167">U kunt een teken reeks met een pad naar deze cmdlet door sluizen.</span><span class="sxs-lookup"><span data-stu-id="c73f1-167">You can pipe a string that contains a path to this cmdlet.</span></span>

## <span data-ttu-id="c73f1-168">UITVOER</span><span class="sxs-lookup"><span data-stu-id="c73f1-168">OUTPUTS</span></span>

### <span data-ttu-id="c73f1-169">Geen of System. Management. Automation. PSCustomObject</span><span class="sxs-lookup"><span data-stu-id="c73f1-169">None or System.Management.Automation.PSCustomObject</span></span>

<span data-ttu-id="c73f1-170">Wanneer u de para meter **PassThru** gebruikt, genereert deze cmdlet een **PsCustomObject** die de eigenschap van het gekopieerde item weergeeft.</span><span class="sxs-lookup"><span data-stu-id="c73f1-170">When you use the **Passthru** parameter, this cmdlet generates a **PsCustomObject** representing the copied item property.</span></span> <span data-ttu-id="c73f1-171">Anders wordt met deze cmdlet geen uitvoer gegenereerd.</span><span class="sxs-lookup"><span data-stu-id="c73f1-171">Otherwise, this cmdlet does not generate any output.</span></span>

## <span data-ttu-id="c73f1-172">OPMERKINGEN</span><span class="sxs-lookup"><span data-stu-id="c73f1-172">NOTES</span></span>

<span data-ttu-id="c73f1-173">Deze cmdlet is ontworpen om te werken met de gegevens die door elke provider worden weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="c73f1-173">This cmdlet is designed to work with the data exposed by any provider.</span></span> <span data-ttu-id="c73f1-174">Als u een lijst wilt weer geven van de providers die beschikbaar zijn in uw sessie, typt u `Get-PSProvider` .</span><span class="sxs-lookup"><span data-stu-id="c73f1-174">To list the providers available in your session, type `Get-PSProvider`.</span></span> <span data-ttu-id="c73f1-175">Zie [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="c73f1-175">For more information, see [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md).</span></span>

## <span data-ttu-id="c73f1-176">GERELATEERDE KOPPELINGEN</span><span class="sxs-lookup"><span data-stu-id="c73f1-176">RELATED LINKS</span></span>

[<span data-ttu-id="c73f1-177">Wissen-item Property</span><span class="sxs-lookup"><span data-stu-id="c73f1-177">Clear-ItemProperty</span></span>](Clear-ItemProperty.md)

[<span data-ttu-id="c73f1-178">Get-item Property</span><span class="sxs-lookup"><span data-stu-id="c73f1-178">Get-ItemProperty</span></span>](Get-ItemProperty.md)

[<span data-ttu-id="c73f1-179">Verplaatsen-item Property</span><span class="sxs-lookup"><span data-stu-id="c73f1-179">Move-ItemProperty</span></span>](Move-ItemProperty.md)

[<span data-ttu-id="c73f1-180">Nieuw-item Property</span><span class="sxs-lookup"><span data-stu-id="c73f1-180">New-ItemProperty</span></span>](New-ItemProperty.md)

[<span data-ttu-id="c73f1-181">Naam wijzigen-item Property</span><span class="sxs-lookup"><span data-stu-id="c73f1-181">Rename-ItemProperty</span></span>](Rename-ItemProperty.md)

[<span data-ttu-id="c73f1-182">Set-item Property</span><span class="sxs-lookup"><span data-stu-id="c73f1-182">Set-ItemProperty</span></span>](Set-ItemProperty.md)

[<span data-ttu-id="c73f1-183">Get-PSProvider</span><span class="sxs-lookup"><span data-stu-id="c73f1-183">Get-PSProvider</span></span>](Get-PSProvider.md)

[<span data-ttu-id="c73f1-184">about_Providers</span><span class="sxs-lookup"><span data-stu-id="c73f1-184">about_Providers</span></span>](../Microsoft.PowerShell.Core/About/about_Providers.md)
