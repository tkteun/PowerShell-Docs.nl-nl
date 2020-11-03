---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 5/14/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/clear-itemproperty?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Clear-ItemProperty
ms.openlocfilehash: f112b2bda543b50e0077df6778fc4eacfb3add9c
ms.sourcegitcommit: de63e9481cf8024883060aae61fb02c59c2de662
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/03/2020
ms.locfileid: "93249739"
---
# <span data-ttu-id="32aed-103">Clear-ItemProperty</span><span class="sxs-lookup"><span data-stu-id="32aed-103">Clear-ItemProperty</span></span>

## <span data-ttu-id="32aed-104">SAMENVATTING</span><span class="sxs-lookup"><span data-stu-id="32aed-104">SYNOPSIS</span></span>
<span data-ttu-id="32aed-105">Hiermee wordt de waarde van een eigenschap gewist, maar wordt de eigenschap niet verwijderd.</span><span class="sxs-lookup"><span data-stu-id="32aed-105">Clears the value of a property but does not delete the property.</span></span>

## <span data-ttu-id="32aed-106">SYNTAXIS</span><span class="sxs-lookup"><span data-stu-id="32aed-106">SYNTAX</span></span>

### <span data-ttu-id="32aed-107">Pad (standaard)</span><span class="sxs-lookup"><span data-stu-id="32aed-107">Path (Default)</span></span>

```
Clear-ItemProperty [-Path] <String[]> [-Name] <String> [-PassThru] [-Force] [-Filter <String>]
 [-Include <String[]>] [-Exclude <String[]>] [-Credential <PSCredential>]
 [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="32aed-108">LiteralPath</span><span class="sxs-lookup"><span data-stu-id="32aed-108">LiteralPath</span></span>

```
Clear-ItemProperty -LiteralPath <String[]> [-Name] <String> [-PassThru] [-Force] [-Filter <String>]
 [-Include <String[]>] [-Exclude <String[]>] [-Credential <PSCredential>]
 [-WhatIf] [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="32aed-109">BESCHRIJVING</span><span class="sxs-lookup"><span data-stu-id="32aed-109">DESCRIPTION</span></span>

<span data-ttu-id="32aed-110">Met de cmdlet wordt de `Clear-ItemProperty` waarde van een eigenschap gewist, maar de eigenschap wordt niet verwijderd.</span><span class="sxs-lookup"><span data-stu-id="32aed-110">The `Clear-ItemProperty` cmdlet clears the value of a property, but it does not delete the property.</span></span>
<span data-ttu-id="32aed-111">U kunt deze cmdlet gebruiken om de gegevens uit een register waarde te verwijderen.</span><span class="sxs-lookup"><span data-stu-id="32aed-111">You can use this cmdlet to delete the data from a registry value.</span></span>

## <span data-ttu-id="32aed-112">VOORBEELDEN</span><span class="sxs-lookup"><span data-stu-id="32aed-112">EXAMPLES</span></span>

### <span data-ttu-id="32aed-113">Voor beeld 1: de waarde van de register sleutel wissen</span><span class="sxs-lookup"><span data-stu-id="32aed-113">Example 1: Clear the value of registry key</span></span>

<span data-ttu-id="32aed-114">Met deze opdracht worden de gegevens in de register waarde ' Options ' van de subsleutel ' Mijntoep ' gewist `HKEY_LOCAL_MACHINE\Software\MyCompany` .</span><span class="sxs-lookup"><span data-stu-id="32aed-114">This command clears the data in the "Options" registry value in the "MyApp" subkey of `HKEY_LOCAL_MACHINE\Software\MyCompany`.</span></span>

```powershell
Clear-ItemProperty -Path "HKLM:\Software\MyCompany\MyApp" -Name "Options"
```

## <span data-ttu-id="32aed-115">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="32aed-115">PARAMETERS</span></span>

### <span data-ttu-id="32aed-116">-Credential</span><span class="sxs-lookup"><span data-stu-id="32aed-116">-Credential</span></span>

> [!NOTE]
> <span data-ttu-id="32aed-117">Deze para meter wordt niet ondersteund door providers die zijn geïnstalleerd met Power shell.</span><span class="sxs-lookup"><span data-stu-id="32aed-117">This parameter is not supported by any providers installed with PowerShell.</span></span>
> <span data-ttu-id="32aed-118">Gebruik [invoke-Command](../Microsoft.PowerShell.Core/Invoke-Command.md)om een andere gebruiker te imiteren of uw referenties te verhogen wanneer u deze cmdlet uitvoert.</span><span class="sxs-lookup"><span data-stu-id="32aed-118">To impersonate another user, or elevate your credentials when running this cmdlet, use [Invoke-Command](../Microsoft.PowerShell.Core/Invoke-Command.md).</span></span>

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

### <span data-ttu-id="32aed-119">-Uitsluiten</span><span class="sxs-lookup"><span data-stu-id="32aed-119">-Exclude</span></span>

<span data-ttu-id="32aed-120">Hiermee geeft u als een teken reeks matrix een item of items die met deze cmdlet worden uitgesloten in de bewerking.</span><span class="sxs-lookup"><span data-stu-id="32aed-120">Specifies, as a string array, an item or items that this cmdlet excludes in the operation.</span></span> <span data-ttu-id="32aed-121">De waarde van deze para meter komt in aanmerking voor de para meter **Path** .</span><span class="sxs-lookup"><span data-stu-id="32aed-121">The value of this parameter qualifies the **Path** parameter.</span></span> <span data-ttu-id="32aed-122">Voer een element of patroon van een pad in, zoals `*.txt` .</span><span class="sxs-lookup"><span data-stu-id="32aed-122">Enter a path element or pattern, such as `*.txt`.</span></span> <span data-ttu-id="32aed-123">Joker tekens zijn toegestaan.</span><span class="sxs-lookup"><span data-stu-id="32aed-123">Wildcard characters are permitted.</span></span> <span data-ttu-id="32aed-124">De **exclude** -para meter is alleen effectief wanneer de inhoud van een item wordt opgenomen, zoals `C:\Windows\*` , waarbij het Joker teken de inhoud van de `C:\Windows` map bevat.</span><span class="sxs-lookup"><span data-stu-id="32aed-124">The **Exclude** parameter is effective only when the command includes the contents of an item, such as `C:\Windows\*`, where the wildcard character specifies the contents of the `C:\Windows` directory.</span></span>

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

### <span data-ttu-id="32aed-125">-Filter</span><span class="sxs-lookup"><span data-stu-id="32aed-125">-Filter</span></span>

<span data-ttu-id="32aed-126">Hiermee geeft u een filter op om de para meter **Path** te kwalificeren.</span><span class="sxs-lookup"><span data-stu-id="32aed-126">Specifies a filter to qualify the **Path** parameter.</span></span> <span data-ttu-id="32aed-127">De [File System](../Microsoft.PowerShell.Core/About/about_FileSystem_Provider.md) -provider is de enige geïnstalleerde Power shell-provider die het gebruik van filters ondersteunt.</span><span class="sxs-lookup"><span data-stu-id="32aed-127">The [FileSystem](../Microsoft.PowerShell.Core/About/about_FileSystem_Provider.md) provider is the only installed PowerShell provider that supports the use of filters.</span></span> <span data-ttu-id="32aed-128">U kunt de syntaxis voor de filter taal van het **Bestands systeem** in [about_Wildcards](../Microsoft.PowerShell.Core/About/about_Wildcards.md)vinden.</span><span class="sxs-lookup"><span data-stu-id="32aed-128">You can find the syntax for the **FileSystem** filter language in [about_Wildcards](../Microsoft.PowerShell.Core/About/about_Wildcards.md).</span></span>
<span data-ttu-id="32aed-129">Filters zijn efficiënter dan andere para meters, omdat deze door de provider worden toegepast wanneer de cmdlet de objecten ophaalt in plaats van dat Power shell de objecten heeft gefilterd nadat ze zijn opgehaald.</span><span class="sxs-lookup"><span data-stu-id="32aed-129">Filters are more efficient than other parameters, because the provider applies them when the cmdlet gets the objects rather than having PowerShell filter the objects after they are retrieved.</span></span>

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

### <span data-ttu-id="32aed-130">-Force</span><span class="sxs-lookup"><span data-stu-id="32aed-130">-Force</span></span>

<span data-ttu-id="32aed-131">Geeft aan dat deze cmdlet eigenschappen van items verwijdert die niet kunnen worden geopend door de gebruiker.</span><span class="sxs-lookup"><span data-stu-id="32aed-131">Indicates that this cmdlet deletes properties from items that cannot otherwise be accessed by the user.</span></span> <span data-ttu-id="32aed-132">De implementatie varieert van provider tot provider.</span><span class="sxs-lookup"><span data-stu-id="32aed-132">Implementation varies from provider to provider.</span></span>
<span data-ttu-id="32aed-133">Zie [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="32aed-133">For more information, see [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md).</span></span>

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

### <span data-ttu-id="32aed-134">-Include</span><span class="sxs-lookup"><span data-stu-id="32aed-134">-Include</span></span>

<span data-ttu-id="32aed-135">Hiermee wordt een teken reeks matrix opgegeven, een item of items die met deze cmdlet in de bewerking zijn opgenomen.</span><span class="sxs-lookup"><span data-stu-id="32aed-135">Specifies, as a string array, an item or items that this cmdlet includes in the operation.</span></span> <span data-ttu-id="32aed-136">De waarde van deze para meter komt in aanmerking voor de para meter **Path** .</span><span class="sxs-lookup"><span data-stu-id="32aed-136">The value of this parameter qualifies the **Path** parameter.</span></span> <span data-ttu-id="32aed-137">Voer een element of patroon van een pad in, zoals `"*.txt"` .</span><span class="sxs-lookup"><span data-stu-id="32aed-137">Enter a path element or pattern, such as `"*.txt"`.</span></span> <span data-ttu-id="32aed-138">Joker tekens zijn toegestaan.</span><span class="sxs-lookup"><span data-stu-id="32aed-138">Wildcard characters are permitted.</span></span> <span data-ttu-id="32aed-139">De para meter **include** is alleen effectief wanneer de inhoud van een item wordt opgenomen, zoals `C:\Windows\*` , waarbij het Joker teken de inhoud van de `C:\Windows` map bevat.</span><span class="sxs-lookup"><span data-stu-id="32aed-139">The **Include** parameter is effective only when the command includes the contents of an item, such as `C:\Windows\*`, where the wildcard character specifies the contents of the `C:\Windows` directory.</span></span>

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

### <span data-ttu-id="32aed-140">-LiteralPath</span><span class="sxs-lookup"><span data-stu-id="32aed-140">-LiteralPath</span></span>

<span data-ttu-id="32aed-141">Hiermee geeft u een pad naar een of meer locaties.</span><span class="sxs-lookup"><span data-stu-id="32aed-141">Specifies a path to one or more locations.</span></span> <span data-ttu-id="32aed-142">De waarde van **LiteralPath** wordt precies zo gebruikt als deze wordt getypt.</span><span class="sxs-lookup"><span data-stu-id="32aed-142">The value of **LiteralPath** is used exactly as it is typed.</span></span> <span data-ttu-id="32aed-143">Geen tekens worden geïnterpreteerd als joker tekens.</span><span class="sxs-lookup"><span data-stu-id="32aed-143">No characters are interpreted as wildcards.</span></span> <span data-ttu-id="32aed-144">Als het pad escape tekens bevat, plaatst u het tussen enkele aanhalings tekens.</span><span class="sxs-lookup"><span data-stu-id="32aed-144">If the path includes escape characters, enclose it in single quotation marks.</span></span> <span data-ttu-id="32aed-145">Enkele aanhalings tekens geven aan dat Power shell geen karakters interpreteert als escape reeksen.</span><span class="sxs-lookup"><span data-stu-id="32aed-145">Single quotation marks tell PowerShell not to interpret any characters as escape sequences.</span></span>

<span data-ttu-id="32aed-146">Zie [about_Quoting_Rules](../Microsoft.Powershell.Core/About/about_Quoting_Rules.md)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="32aed-146">For more information, see [about_Quoting_Rules](../Microsoft.Powershell.Core/About/about_Quoting_Rules.md).</span></span>

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

### <span data-ttu-id="32aed-147">-Name</span><span class="sxs-lookup"><span data-stu-id="32aed-147">-Name</span></span>

<span data-ttu-id="32aed-148">Hiermee geeft u de naam op van de eigenschap die moet worden gewist, zoals de naam van een register waarde.</span><span class="sxs-lookup"><span data-stu-id="32aed-148">Specifies the name of the property to be cleared, such as the name of a registry value.</span></span>
<span data-ttu-id="32aed-149">Joker tekens zijn toegestaan.</span><span class="sxs-lookup"><span data-stu-id="32aed-149">Wildcard characters are permitted.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: True
Position: 1
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: True
```

### <span data-ttu-id="32aed-150">-PassThru</span><span class="sxs-lookup"><span data-stu-id="32aed-150">-PassThru</span></span>

<span data-ttu-id="32aed-151">Retourneert een object dat het item vertegenwoordigt waarmee u werkt.</span><span class="sxs-lookup"><span data-stu-id="32aed-151">Returns an object representing the item with which you are working.</span></span>
<span data-ttu-id="32aed-152">Deze cmdlet genereert standaard geen uitvoer.</span><span class="sxs-lookup"><span data-stu-id="32aed-152">By default, this cmdlet does not generate any output.</span></span>

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

### <span data-ttu-id="32aed-153">-Path</span><span class="sxs-lookup"><span data-stu-id="32aed-153">-Path</span></span>

<span data-ttu-id="32aed-154">Hiermee geeft u het pad op naar de eigenschap die wordt gewist.</span><span class="sxs-lookup"><span data-stu-id="32aed-154">Specifies the path to the property being cleared.</span></span>
<span data-ttu-id="32aed-155">Joker tekens zijn toegestaan.</span><span class="sxs-lookup"><span data-stu-id="32aed-155">Wildcard characters are permitted.</span></span>

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

### <span data-ttu-id="32aed-156">-Confirm</span><span class="sxs-lookup"><span data-stu-id="32aed-156">-Confirm</span></span>

<span data-ttu-id="32aed-157">Hiermee wordt u gevraagd om bevestiging voordat u de cmdlet uitvoert.</span><span class="sxs-lookup"><span data-stu-id="32aed-157">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="32aed-158">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="32aed-158">-WhatIf</span></span>

<span data-ttu-id="32aed-159">Hiermee wordt weergegeven wat er zou gebeuren als u de cmdlet uitvoert.</span><span class="sxs-lookup"><span data-stu-id="32aed-159">Shows what would happen if the cmdlet runs.</span></span>
<span data-ttu-id="32aed-160">De cmdlet wordt niet uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="32aed-160">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="32aed-161">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="32aed-161">CommonParameters</span></span>

<span data-ttu-id="32aed-162">Deze cmdlet biedt ondersteuning voor de algemene para meters: `-Debug` , `-ErrorAction` , `-ErrorVariable` , `-InformationAction` , `-InformationVariable` , `-OutVariable` , `-OutBuffer` , `-PipelineVariable` , `-Verbose` , `-WarningAction` en `-WarningVariable` .</span><span class="sxs-lookup"><span data-stu-id="32aed-162">This cmdlet supports the common parameters: `-Debug`, `-ErrorAction`, `-ErrorVariable`, `-InformationAction`, `-InformationVariable`, `-OutVariable`, `-OutBuffer`, `-PipelineVariable`, `-Verbose`, `-WarningAction`, and `-WarningVariable`.</span></span> <span data-ttu-id="32aed-163">Zie [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="32aed-163">For more information, see [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md).</span></span>

## <span data-ttu-id="32aed-164">INVOER</span><span class="sxs-lookup"><span data-stu-id="32aed-164">INPUTS</span></span>

### <span data-ttu-id="32aed-165">System. String</span><span class="sxs-lookup"><span data-stu-id="32aed-165">System.String</span></span>

<span data-ttu-id="32aed-166">U kunt een padtekenreeks door sluizen naar deze cmdlet.</span><span class="sxs-lookup"><span data-stu-id="32aed-166">You can pipe a path string to this cmdlet.</span></span>

## <span data-ttu-id="32aed-167">UITVOER</span><span class="sxs-lookup"><span data-stu-id="32aed-167">OUTPUTS</span></span>

### <span data-ttu-id="32aed-168">Geen of System. Management. Automation. PSCustomObject</span><span class="sxs-lookup"><span data-stu-id="32aed-168">None or System.Management.Automation.PSCustomObject</span></span>

<span data-ttu-id="32aed-169">Wanneer u de para meter **PassThru** gebruikt, wordt `Clear-ItemProperty` een **PSCustomObject** -object gegenereerd dat de eigenschap voor de gewiste items vertegenwoordigt.</span><span class="sxs-lookup"><span data-stu-id="32aed-169">When you use the **PassThru** parameter, `Clear-ItemProperty` generates a **PSCustomObject** object that represents the cleared item property.</span></span> <span data-ttu-id="32aed-170">Anders wordt met deze cmdlet geen uitvoer gegenereerd.</span><span class="sxs-lookup"><span data-stu-id="32aed-170">Otherwise, this cmdlet does not generate any output.</span></span>

## <span data-ttu-id="32aed-171">OPMERKINGEN</span><span class="sxs-lookup"><span data-stu-id="32aed-171">NOTES</span></span>

- <span data-ttu-id="32aed-172">U kunt gebruiken `Clear-ItemProperty` om de gegevens in register waarden te verwijderen zonder de waarde te verwijderen.</span><span class="sxs-lookup"><span data-stu-id="32aed-172">You can use `Clear-ItemProperty` to delete the data in registry values without deleting the value.</span></span>
  <span data-ttu-id="32aed-173">Als het gegevens type van de waarde binary of DWORD is, wordt met het wissen van de gegevens de waarde ingesteld op nul.</span><span class="sxs-lookup"><span data-stu-id="32aed-173">If the data type of the value is Binary or DWORD, clearing the data sets the value to zero.</span></span>
  <span data-ttu-id="32aed-174">Anders is de waarde leeg.</span><span class="sxs-lookup"><span data-stu-id="32aed-174">Otherwise, the value is empty.</span></span>
- <span data-ttu-id="32aed-175">De `Clear-ItemProperty` cmdlet is ontworpen om te werken met de gegevens die door elke provider worden weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="32aed-175">The `Clear-ItemProperty` cmdlet is designed to work with the data exposed by any provider.</span></span> <span data-ttu-id="32aed-176">Als u een lijst wilt weer geven van de providers die beschikbaar zijn in uw sessie, typt u `Get-PSProvider` .</span><span class="sxs-lookup"><span data-stu-id="32aed-176">To list the providers available in your session, type `Get-PSProvider`.</span></span> <span data-ttu-id="32aed-177">Zie [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="32aed-177">For more information, see [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md).</span></span>

## <span data-ttu-id="32aed-178">GERELATEERDE KOPPELINGEN</span><span class="sxs-lookup"><span data-stu-id="32aed-178">RELATED LINKS</span></span>

[<span data-ttu-id="32aed-179">Kopiëren-item Property</span><span class="sxs-lookup"><span data-stu-id="32aed-179">Copy-ItemProperty</span></span>](Copy-ItemProperty.md)

[<span data-ttu-id="32aed-180">Get-item Property</span><span class="sxs-lookup"><span data-stu-id="32aed-180">Get-ItemProperty</span></span>](Get-ItemProperty.md)

[<span data-ttu-id="32aed-181">Verplaatsen-item Property</span><span class="sxs-lookup"><span data-stu-id="32aed-181">Move-ItemProperty</span></span>](Move-ItemProperty.md)

[<span data-ttu-id="32aed-182">Nieuw-item Property</span><span class="sxs-lookup"><span data-stu-id="32aed-182">New-ItemProperty</span></span>](New-ItemProperty.md)

[<span data-ttu-id="32aed-183">Naam wijzigen-item Property</span><span class="sxs-lookup"><span data-stu-id="32aed-183">Rename-ItemProperty</span></span>](Rename-ItemProperty.md)

[<span data-ttu-id="32aed-184">about_Providers</span><span class="sxs-lookup"><span data-stu-id="32aed-184">about_Providers</span></span>](../Microsoft.PowerShell.Core/About/about_Providers.md)
