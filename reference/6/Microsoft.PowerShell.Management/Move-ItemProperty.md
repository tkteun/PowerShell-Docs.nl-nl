---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 5/14/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/move-itemproperty?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Move-ItemProperty
ms.openlocfilehash: 235991da33ae49f8d1dd9b379432963a8930ebc0
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/07/2020
ms.locfileid: "93250243"
---
# <span data-ttu-id="02b0b-103">Move-ItemProperty</span><span class="sxs-lookup"><span data-stu-id="02b0b-103">Move-ItemProperty</span></span>

## <span data-ttu-id="02b0b-104">Samen vatting</span><span class="sxs-lookup"><span data-stu-id="02b0b-104">Synopsis</span></span>
<span data-ttu-id="02b0b-105">Verplaatst een eigenschap van de ene locatie naar een andere.</span><span class="sxs-lookup"><span data-stu-id="02b0b-105">Moves a property from one location to another.</span></span>

## <span data-ttu-id="02b0b-106">SYNTAXIS</span><span class="sxs-lookup"><span data-stu-id="02b0b-106">SYNTAX</span></span>

### <span data-ttu-id="02b0b-107">Pad (standaard)</span><span class="sxs-lookup"><span data-stu-id="02b0b-107">Path (Default)</span></span>

```
Move-ItemProperty [-Path] <String[]> [-Name] <String[]> [-Destination] <String> [-PassThru] [-Force]
 [-Filter <String>] [-Include <String[]>] [-Exclude <String[]>] [-Credential <PSCredential>]
 [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="02b0b-108">LiteralPath</span><span class="sxs-lookup"><span data-stu-id="02b0b-108">LiteralPath</span></span>

```
Move-ItemProperty -LiteralPath <String[]> [-Name] <String[]> [-Destination] <String> [-PassThru] [-Force]
 [-Filter <String>] [-Include <String[]>] [-Exclude <String[]>] [-Credential <PSCredential>]
 [-WhatIf] [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="02b0b-109">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="02b0b-109">Description</span></span>

<span data-ttu-id="02b0b-110">Met de `Move-ItemProperty` cmdlet wordt een eigenschap van een item van het ene naar het andere item verplaatst.</span><span class="sxs-lookup"><span data-stu-id="02b0b-110">The `Move-ItemProperty` cmdlet moves a property of an item from one item to another item.</span></span>
<span data-ttu-id="02b0b-111">Zo kan het een register vermelding van de ene register sleutel naar een andere register sleutel verplaatsen.</span><span class="sxs-lookup"><span data-stu-id="02b0b-111">For instance, it can move a registry entry from one registry key to another registry key.</span></span>
<span data-ttu-id="02b0b-112">Wanneer u een item eigenschap verplaatst, wordt deze toegevoegd aan de nieuwe locatie en verwijderd uit de oorspronkelijke locatie.</span><span class="sxs-lookup"><span data-stu-id="02b0b-112">When you move an item property, it is added to the new location and deleted from its original location.</span></span>

## <span data-ttu-id="02b0b-113">VOORBEELDEN</span><span class="sxs-lookup"><span data-stu-id="02b0b-113">EXAMPLES</span></span>

### <span data-ttu-id="02b0b-114">Voor beeld 1: een register waarde en de bijbehorende gegevens naar een andere sleutel verplaatsen</span><span class="sxs-lookup"><span data-stu-id="02b0b-114">Example 1: Move a registry value and its data to another key</span></span>

<span data-ttu-id="02b0b-115">Met deze opdracht worden de versie register waarde en de bijbehorende gegevens van de subsleutel ' Mijntoep ' verplaatst naar de subsleutel NewApp van de `HKLM\Software\MyCompany` register sleutel.</span><span class="sxs-lookup"><span data-stu-id="02b0b-115">This command moves the Version registry value, and its data, from the "MyApp" subkey to the NewApp subkey of the `HKLM\Software\MyCompany` registry key.</span></span>

```powershell
Move-ItemProperty "HKLM:\Software\MyCompany\MyApp" -Name "Version" -Destination "HKLM:\Software\MyCompany\NewApp"
```

## <span data-ttu-id="02b0b-116">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="02b0b-116">PARAMETERS</span></span>

### <span data-ttu-id="02b0b-117">-Credential</span><span class="sxs-lookup"><span data-stu-id="02b0b-117">-Credential</span></span>

> [!NOTE]
> <span data-ttu-id="02b0b-118">Deze para meter wordt niet ondersteund door providers die zijn geïnstalleerd met Power shell.</span><span class="sxs-lookup"><span data-stu-id="02b0b-118">This parameter is not supported by any providers installed with PowerShell.</span></span>
> <span data-ttu-id="02b0b-119">Gebruik [invoke-Command](../Microsoft.PowerShell.Core/Invoke-Command.md)om een andere gebruiker te imiteren of uw referenties te verhogen wanneer u deze cmdlet uitvoert.</span><span class="sxs-lookup"><span data-stu-id="02b0b-119">To impersonate another user, or elevate your credentials when running this cmdlet, use [Invoke-Command](../Microsoft.PowerShell.Core/Invoke-Command.md).</span></span>

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

### <span data-ttu-id="02b0b-120">-Bestemming</span><span class="sxs-lookup"><span data-stu-id="02b0b-120">-Destination</span></span>

<span data-ttu-id="02b0b-121">Hiermee geeft u het pad naar de doel locatie.</span><span class="sxs-lookup"><span data-stu-id="02b0b-121">Specifies the path to the destination location.</span></span>

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

### <span data-ttu-id="02b0b-122">-Uitsluiten</span><span class="sxs-lookup"><span data-stu-id="02b0b-122">-Exclude</span></span>

<span data-ttu-id="02b0b-123">Hiermee geeft u als een teken reeks matrix een item of items die met deze cmdlet worden uitgesloten in de bewerking.</span><span class="sxs-lookup"><span data-stu-id="02b0b-123">Specifies, as a string array, an item or items that this cmdlet excludes in the operation.</span></span> <span data-ttu-id="02b0b-124">De waarde van deze para meter komt in aanmerking voor de para meter **Path** .</span><span class="sxs-lookup"><span data-stu-id="02b0b-124">The value of this parameter qualifies the **Path** parameter.</span></span> <span data-ttu-id="02b0b-125">Voer een element of patroon van een pad in, zoals `*.txt` .</span><span class="sxs-lookup"><span data-stu-id="02b0b-125">Enter a path element or pattern, such as `*.txt`.</span></span> <span data-ttu-id="02b0b-126">Joker tekens zijn toegestaan.</span><span class="sxs-lookup"><span data-stu-id="02b0b-126">Wildcard characters are permitted.</span></span> <span data-ttu-id="02b0b-127">De **exclude** -para meter is alleen effectief wanneer de inhoud van een item wordt opgenomen, zoals `C:\Windows\*` , waarbij het Joker teken de inhoud van de `C:\Windows` map bevat.</span><span class="sxs-lookup"><span data-stu-id="02b0b-127">The **Exclude** parameter is effective only when the command includes the contents of an item, such as `C:\Windows\*`, where the wildcard character specifies the contents of the `C:\Windows` directory.</span></span>

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

### <span data-ttu-id="02b0b-128">-Filter</span><span class="sxs-lookup"><span data-stu-id="02b0b-128">-Filter</span></span>

<span data-ttu-id="02b0b-129">Hiermee geeft u een filter op om de para meter **Path** te kwalificeren.</span><span class="sxs-lookup"><span data-stu-id="02b0b-129">Specifies a filter to qualify the **Path** parameter.</span></span> <span data-ttu-id="02b0b-130">De [File System](../Microsoft.PowerShell.Core/About/about_FileSystem_Provider.md) -provider is de enige geïnstalleerde Power shell-provider die het gebruik van filters ondersteunt.</span><span class="sxs-lookup"><span data-stu-id="02b0b-130">The [FileSystem](../Microsoft.PowerShell.Core/About/about_FileSystem_Provider.md) provider is the only installed PowerShell provider that supports the use of filters.</span></span> <span data-ttu-id="02b0b-131">U kunt de syntaxis voor de filter taal van het **Bestands systeem** in [about_Wildcards](../Microsoft.PowerShell.Core/About/about_Wildcards.md)vinden.</span><span class="sxs-lookup"><span data-stu-id="02b0b-131">You can find the syntax for the **FileSystem** filter language in [about_Wildcards](../Microsoft.PowerShell.Core/About/about_Wildcards.md).</span></span>
<span data-ttu-id="02b0b-132">Filters zijn efficiënter dan andere para meters, omdat deze door de provider worden toegepast wanneer de cmdlet de objecten ophaalt in plaats van dat Power shell de objecten heeft gefilterd nadat ze zijn opgehaald.</span><span class="sxs-lookup"><span data-stu-id="02b0b-132">Filters are more efficient than other parameters, because the provider applies them when the cmdlet gets the objects rather than having PowerShell filter the objects after they are retrieved.</span></span>

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

### <span data-ttu-id="02b0b-133">-Force</span><span class="sxs-lookup"><span data-stu-id="02b0b-133">-Force</span></span>

<span data-ttu-id="02b0b-134">Hiermee wordt de opdracht uitgevoerd zonder dat de gebruiker om bevestiging wordt gevraagd.</span><span class="sxs-lookup"><span data-stu-id="02b0b-134">Forces the command to run without asking for user confirmation.</span></span>
<span data-ttu-id="02b0b-135">De implementatie varieert van provider tot provider.</span><span class="sxs-lookup"><span data-stu-id="02b0b-135">Implementation varies from provider to provider.</span></span>
<span data-ttu-id="02b0b-136">Zie [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="02b0b-136">For more information, see [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md).</span></span>

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

### <span data-ttu-id="02b0b-137">-Include</span><span class="sxs-lookup"><span data-stu-id="02b0b-137">-Include</span></span>

<span data-ttu-id="02b0b-138">Hiermee wordt een teken reeks matrix opgegeven, een item of items die met deze cmdlet in de bewerking zijn opgenomen.</span><span class="sxs-lookup"><span data-stu-id="02b0b-138">Specifies, as a string array, an item or items that this cmdlet includes in the operation.</span></span> <span data-ttu-id="02b0b-139">De waarde van deze para meter komt in aanmerking voor de para meter **Path** .</span><span class="sxs-lookup"><span data-stu-id="02b0b-139">The value of this parameter qualifies the **Path** parameter.</span></span> <span data-ttu-id="02b0b-140">Voer een element of patroon van een pad in, zoals `"*.txt"` .</span><span class="sxs-lookup"><span data-stu-id="02b0b-140">Enter a path element or pattern, such as `"*.txt"`.</span></span> <span data-ttu-id="02b0b-141">Joker tekens zijn toegestaan.</span><span class="sxs-lookup"><span data-stu-id="02b0b-141">Wildcard characters are permitted.</span></span> <span data-ttu-id="02b0b-142">De para meter **include** is alleen effectief wanneer de inhoud van een item wordt opgenomen, zoals `C:\Windows\*` , waarbij het Joker teken de inhoud van de `C:\Windows` map bevat.</span><span class="sxs-lookup"><span data-stu-id="02b0b-142">The **Include** parameter is effective only when the command includes the contents of an item, such as `C:\Windows\*`, where the wildcard character specifies the contents of the `C:\Windows` directory.</span></span>

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

### <span data-ttu-id="02b0b-143">-LiteralPath</span><span class="sxs-lookup"><span data-stu-id="02b0b-143">-LiteralPath</span></span>

<span data-ttu-id="02b0b-144">Hiermee geeft u een pad naar een of meer locaties.</span><span class="sxs-lookup"><span data-stu-id="02b0b-144">Specifies a path to one or more locations.</span></span> <span data-ttu-id="02b0b-145">De waarde van **LiteralPath** wordt precies zo gebruikt als deze wordt getypt.</span><span class="sxs-lookup"><span data-stu-id="02b0b-145">The value of **LiteralPath** is used exactly as it is typed.</span></span> <span data-ttu-id="02b0b-146">Geen tekens worden geïnterpreteerd als joker tekens.</span><span class="sxs-lookup"><span data-stu-id="02b0b-146">No characters are interpreted as wildcards.</span></span> <span data-ttu-id="02b0b-147">Als het pad escape tekens bevat, plaatst u het tussen enkele aanhalings tekens.</span><span class="sxs-lookup"><span data-stu-id="02b0b-147">If the path includes escape characters, enclose it in single quotation marks.</span></span> <span data-ttu-id="02b0b-148">Enkele aanhalings tekens geven aan dat Power shell geen karakters interpreteert als escape reeksen.</span><span class="sxs-lookup"><span data-stu-id="02b0b-148">Single quotation marks tell PowerShell not to interpret any characters as escape sequences.</span></span>

<span data-ttu-id="02b0b-149">Zie [about_Quoting_Rules](../Microsoft.Powershell.Core/About/about_Quoting_Rules.md)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="02b0b-149">For more information, see [about_Quoting_Rules](../Microsoft.Powershell.Core/About/about_Quoting_Rules.md).</span></span>

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

### <span data-ttu-id="02b0b-150">-Name</span><span class="sxs-lookup"><span data-stu-id="02b0b-150">-Name</span></span>

<span data-ttu-id="02b0b-151">Hiermee geeft u de naam van de eigenschap die moet worden verplaatst.</span><span class="sxs-lookup"><span data-stu-id="02b0b-151">Specifies the name of the property to be moved.</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases: PSProperty

Required: True
Position: 2
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="02b0b-152">-PassThru</span><span class="sxs-lookup"><span data-stu-id="02b0b-152">-PassThru</span></span>

<span data-ttu-id="02b0b-153">Retourneert een object dat het item vertegenwoordigt waarmee u werkt.</span><span class="sxs-lookup"><span data-stu-id="02b0b-153">Returns an object representing the item with which you are working.</span></span>
<span data-ttu-id="02b0b-154">Deze cmdlet genereert standaard geen uitvoer.</span><span class="sxs-lookup"><span data-stu-id="02b0b-154">By default, this cmdlet does not generate any output.</span></span>

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

### <span data-ttu-id="02b0b-155">-Path</span><span class="sxs-lookup"><span data-stu-id="02b0b-155">-Path</span></span>

<span data-ttu-id="02b0b-156">Hiermee geeft u het pad op naar de huidige locatie van de eigenschap.</span><span class="sxs-lookup"><span data-stu-id="02b0b-156">Specifies the path to the current location of the property.</span></span>
<span data-ttu-id="02b0b-157">Joker tekens zijn toegestaan.</span><span class="sxs-lookup"><span data-stu-id="02b0b-157">Wildcard characters are permitted.</span></span>

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

### <span data-ttu-id="02b0b-158">-Confirm</span><span class="sxs-lookup"><span data-stu-id="02b0b-158">-Confirm</span></span>

<span data-ttu-id="02b0b-159">Hiermee wordt u gevraagd om bevestiging voordat u de cmdlet uitvoert.</span><span class="sxs-lookup"><span data-stu-id="02b0b-159">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="02b0b-160">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="02b0b-160">-WhatIf</span></span>

<span data-ttu-id="02b0b-161">Hiermee wordt weergegeven wat er zou gebeuren als u de cmdlet uitvoert.</span><span class="sxs-lookup"><span data-stu-id="02b0b-161">Shows what would happen if the cmdlet runs.</span></span>
<span data-ttu-id="02b0b-162">De cmdlet wordt niet uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="02b0b-162">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="02b0b-163">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="02b0b-163">CommonParameters</span></span>

<span data-ttu-id="02b0b-164">Deze cmdlet biedt ondersteuning voor de algemene para meters: `-Debug` , `-ErrorAction` , `-ErrorVariable` , `-InformationAction` , `-InformationVariable` , `-OutVariable` , `-OutBuffer` , `-PipelineVariable` , `-Verbose` , `-WarningAction` en `-WarningVariable` .</span><span class="sxs-lookup"><span data-stu-id="02b0b-164">This cmdlet supports the common parameters: `-Debug`, `-ErrorAction`, `-ErrorVariable`, `-InformationAction`, `-InformationVariable`, `-OutVariable`, `-OutBuffer`, `-PipelineVariable`, `-Verbose`, `-WarningAction`, and `-WarningVariable`.</span></span> <span data-ttu-id="02b0b-165">Zie [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="02b0b-165">For more information, see [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md).</span></span>

## <span data-ttu-id="02b0b-166">INVOER</span><span class="sxs-lookup"><span data-stu-id="02b0b-166">INPUTS</span></span>

### <span data-ttu-id="02b0b-167">System. String</span><span class="sxs-lookup"><span data-stu-id="02b0b-167">System.String</span></span>

<span data-ttu-id="02b0b-168">U kunt een teken reeks met een pad naar deze cmdlet door sluizen.</span><span class="sxs-lookup"><span data-stu-id="02b0b-168">You can pipe a string that contains a path to this cmdlet.</span></span>

## <span data-ttu-id="02b0b-169">UITVOER</span><span class="sxs-lookup"><span data-stu-id="02b0b-169">OUTPUTS</span></span>

### <span data-ttu-id="02b0b-170">Geen of System. Management. Automation. PSCustomObject</span><span class="sxs-lookup"><span data-stu-id="02b0b-170">None or System.Management.Automation.PSCustomObject</span></span>

<span data-ttu-id="02b0b-171">Wanneer u de para meter **PassThru** gebruikt, genereert deze cmdlet een **PSCustomObject** die de eigenschap verplaatste items vertegenwoordigt.</span><span class="sxs-lookup"><span data-stu-id="02b0b-171">When you use the **PassThru** parameter, this cmdlet generates a **PSCustomObject** representing the moved item property.</span></span> <span data-ttu-id="02b0b-172">Anders wordt met deze cmdlet geen uitvoer gegenereerd.</span><span class="sxs-lookup"><span data-stu-id="02b0b-172">Otherwise, this cmdlet does not generate any output.</span></span>

## <span data-ttu-id="02b0b-173">OPMERKINGEN</span><span class="sxs-lookup"><span data-stu-id="02b0b-173">NOTES</span></span>

<span data-ttu-id="02b0b-174">Deze cmdlet is ontworpen om te werken met de gegevens die door elke provider worden weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="02b0b-174">This cmdlet is designed to work with the data exposed by any provider.</span></span> <span data-ttu-id="02b0b-175">Als u een lijst wilt weer geven van de providers die beschikbaar zijn in uw sessie, typt u `Get-PSProvider` .</span><span class="sxs-lookup"><span data-stu-id="02b0b-175">To list the providers available in your session, type `Get-PSProvider`.</span></span> <span data-ttu-id="02b0b-176">Zie [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="02b0b-176">For more information, see [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md).</span></span>

## <span data-ttu-id="02b0b-177">GERELATEERDE KOPPELINGEN</span><span class="sxs-lookup"><span data-stu-id="02b0b-177">RELATED LINKS</span></span>

[<span data-ttu-id="02b0b-178">Wissen-item Property</span><span class="sxs-lookup"><span data-stu-id="02b0b-178">Clear-ItemProperty</span></span>](Clear-ItemProperty.md)

[<span data-ttu-id="02b0b-179">Kopiëren-item Property</span><span class="sxs-lookup"><span data-stu-id="02b0b-179">Copy-ItemProperty</span></span>](Copy-ItemProperty.md)

[<span data-ttu-id="02b0b-180">Get-item Property</span><span class="sxs-lookup"><span data-stu-id="02b0b-180">Get-ItemProperty</span></span>](Get-ItemProperty.md)

[<span data-ttu-id="02b0b-181">Nieuw-item Property</span><span class="sxs-lookup"><span data-stu-id="02b0b-181">New-ItemProperty</span></span>](New-ItemProperty.md)

[<span data-ttu-id="02b0b-182">Verwijderen-item Property</span><span class="sxs-lookup"><span data-stu-id="02b0b-182">Remove-ItemProperty</span></span>](Remove-ItemProperty.md)

[<span data-ttu-id="02b0b-183">Naam wijzigen-item Property</span><span class="sxs-lookup"><span data-stu-id="02b0b-183">Rename-ItemProperty</span></span>](Rename-ItemProperty.md)

[<span data-ttu-id="02b0b-184">Set-item Property</span><span class="sxs-lookup"><span data-stu-id="02b0b-184">Set-ItemProperty</span></span>](Set-ItemProperty.md)

[<span data-ttu-id="02b0b-185">about_Providers</span><span class="sxs-lookup"><span data-stu-id="02b0b-185">about_Providers</span></span>](../Microsoft.PowerShell.Core/About/about_Providers.md)
