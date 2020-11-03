---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 10/18/2018
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/clear-itemproperty?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Clear-ItemProperty
ms.openlocfilehash: b23db6af5d34b8a6413a21fafd34fc5e19f5690a
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/07/2020
ms.locfileid: "93250831"
---
# <span data-ttu-id="a7897-103">Clear-ItemProperty</span><span class="sxs-lookup"><span data-stu-id="a7897-103">Clear-ItemProperty</span></span>

## <span data-ttu-id="a7897-104">SAMENVATTING</span><span class="sxs-lookup"><span data-stu-id="a7897-104">SYNOPSIS</span></span>
<span data-ttu-id="a7897-105">Hiermee wordt de waarde van een eigenschap gewist, maar wordt de eigenschap niet verwijderd.</span><span class="sxs-lookup"><span data-stu-id="a7897-105">Clears the value of a property but does not delete the property.</span></span>

## <span data-ttu-id="a7897-106">SYNTAXIS</span><span class="sxs-lookup"><span data-stu-id="a7897-106">SYNTAX</span></span>

### <span data-ttu-id="a7897-107">Pad (standaard)</span><span class="sxs-lookup"><span data-stu-id="a7897-107">Path (Default)</span></span>

```
Clear-ItemProperty [-Path] <String[]> [-Name] <String> [-PassThru] [-Force] [-Filter <String>]
 [-Include <String[]>] [-Exclude <String[]>] [-Credential <PSCredential>] [-WhatIf] [-Confirm]
 [-UseTransaction] [<CommonParameters>]
```

### <span data-ttu-id="a7897-108">LiteralPath</span><span class="sxs-lookup"><span data-stu-id="a7897-108">LiteralPath</span></span>

```
Clear-ItemProperty -LiteralPath <String[]> [-Name] <String> [-PassThru] [-Force] [-Filter <String>]
 [-Include <String[]>] [-Exclude <String[]>] [-Credential <PSCredential>] [-WhatIf] [-Confirm]
 [-UseTransaction] [<CommonParameters>]
```

## <span data-ttu-id="a7897-109">BESCHRIJVING</span><span class="sxs-lookup"><span data-stu-id="a7897-109">DESCRIPTION</span></span>

<span data-ttu-id="a7897-110">Met de cmdlet wordt de `Clear-ItemProperty` waarde van een eigenschap gewist, maar de eigenschap wordt niet verwijderd.</span><span class="sxs-lookup"><span data-stu-id="a7897-110">The `Clear-ItemProperty` cmdlet clears the value of a property, but it does not delete the property.</span></span>
<span data-ttu-id="a7897-111">U kunt deze cmdlet gebruiken om de gegevens uit een register waarde te verwijderen.</span><span class="sxs-lookup"><span data-stu-id="a7897-111">You can use this cmdlet to delete the data from a registry value.</span></span>

## <span data-ttu-id="a7897-112">VOORBEELDEN</span><span class="sxs-lookup"><span data-stu-id="a7897-112">EXAMPLES</span></span>

### <span data-ttu-id="a7897-113">Voor beeld 1: de waarde van de register sleutel wissen</span><span class="sxs-lookup"><span data-stu-id="a7897-113">Example 1: Clear the value of registry key</span></span>

<span data-ttu-id="a7897-114">Met deze opdracht worden de gegevens in de register waarde ' Options ' van de subsleutel ' Mijntoep ' gewist `HKEY_LOCAL_MACHINE\Software\MyCompany` .</span><span class="sxs-lookup"><span data-stu-id="a7897-114">This command clears the data in the "Options" registry value in the "MyApp" subkey of `HKEY_LOCAL_MACHINE\Software\MyCompany`.</span></span>

```powershell
Clear-ItemProperty -Path "HKLM:\Software\MyCompany\MyApp" -Name "Options"
```

## <span data-ttu-id="a7897-115">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="a7897-115">PARAMETERS</span></span>

### <span data-ttu-id="a7897-116">-Credential</span><span class="sxs-lookup"><span data-stu-id="a7897-116">-Credential</span></span>

> [!NOTE]
> <span data-ttu-id="a7897-117">Deze para meter wordt niet ondersteund door providers die zijn geïnstalleerd met Power shell.</span><span class="sxs-lookup"><span data-stu-id="a7897-117">This parameter is not supported by any providers installed with PowerShell.</span></span>
> <span data-ttu-id="a7897-118">Gebruik [invoke-Command](../Microsoft.PowerShell.Core/Invoke-Command.md)om een andere gebruiker te imiteren of uw referenties te verhogen wanneer u deze cmdlet uitvoert.</span><span class="sxs-lookup"><span data-stu-id="a7897-118">To impersonate another user, or elevate your credentials when running this cmdlet, use [Invoke-Command](../Microsoft.PowerShell.Core/Invoke-Command.md).</span></span>

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

### <span data-ttu-id="a7897-119">-Uitsluiten</span><span class="sxs-lookup"><span data-stu-id="a7897-119">-Exclude</span></span>

<span data-ttu-id="a7897-120">Hiermee geeft u als een teken reeks matrix een item of items die met deze cmdlet worden uitgesloten in de bewerking.</span><span class="sxs-lookup"><span data-stu-id="a7897-120">Specifies, as a string array, an item or items that this cmdlet excludes in the operation.</span></span> <span data-ttu-id="a7897-121">De waarde van deze para meter komt in aanmerking voor de para meter **Path** .</span><span class="sxs-lookup"><span data-stu-id="a7897-121">The value of this parameter qualifies the **Path** parameter.</span></span> <span data-ttu-id="a7897-122">Voer een element of patroon van een pad in, zoals `*.txt` .</span><span class="sxs-lookup"><span data-stu-id="a7897-122">Enter a path element or pattern, such as `*.txt`.</span></span> <span data-ttu-id="a7897-123">Joker tekens zijn toegestaan.</span><span class="sxs-lookup"><span data-stu-id="a7897-123">Wildcard characters are permitted.</span></span> <span data-ttu-id="a7897-124">De **exclude** -para meter is alleen effectief wanneer de inhoud van een item wordt opgenomen, zoals `C:\Windows\*` , waarbij het Joker teken de inhoud van de `C:\Windows` map bevat.</span><span class="sxs-lookup"><span data-stu-id="a7897-124">The **Exclude** parameter is effective only when the command includes the contents of an item, such as `C:\Windows\*`, where the wildcard character specifies the contents of the `C:\Windows` directory.</span></span>

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

### <span data-ttu-id="a7897-125">-Filter</span><span class="sxs-lookup"><span data-stu-id="a7897-125">-Filter</span></span>

<span data-ttu-id="a7897-126">Hiermee geeft u een filter op om de para meter **Path** te kwalificeren.</span><span class="sxs-lookup"><span data-stu-id="a7897-126">Specifies a filter to qualify the **Path** parameter.</span></span> <span data-ttu-id="a7897-127">De [File System](../Microsoft.PowerShell.Core/About/about_FileSystem_Provider.md) -provider is de enige geïnstalleerde Power shell-provider die het gebruik van filters ondersteunt.</span><span class="sxs-lookup"><span data-stu-id="a7897-127">The [FileSystem](../Microsoft.PowerShell.Core/About/about_FileSystem_Provider.md) provider is the only installed PowerShell provider that supports the use of filters.</span></span> <span data-ttu-id="a7897-128">U kunt de syntaxis voor de filter taal van het **Bestands systeem** in [about_Wildcards](../Microsoft.PowerShell.Core/About/about_Wildcards.md)vinden.</span><span class="sxs-lookup"><span data-stu-id="a7897-128">You can find the syntax for the **FileSystem** filter language in [about_Wildcards](../Microsoft.PowerShell.Core/About/about_Wildcards.md).</span></span>
<span data-ttu-id="a7897-129">Filters zijn efficiënter dan andere para meters, omdat deze door de provider worden toegepast wanneer de cmdlet de objecten ophaalt in plaats van dat Power shell de objecten heeft gefilterd nadat ze zijn opgehaald.</span><span class="sxs-lookup"><span data-stu-id="a7897-129">Filters are more efficient than other parameters, because the provider applies them when the cmdlet gets the objects rather than having PowerShell filter the objects after they are retrieved.</span></span>

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

### <span data-ttu-id="a7897-130">-Force</span><span class="sxs-lookup"><span data-stu-id="a7897-130">-Force</span></span>

<span data-ttu-id="a7897-131">Geeft aan dat deze cmdlet eigenschappen van items verwijdert die niet kunnen worden geopend door de gebruiker.</span><span class="sxs-lookup"><span data-stu-id="a7897-131">Indicates that this cmdlet deletes properties from items that cannot otherwise be accessed by the user.</span></span> <span data-ttu-id="a7897-132">De implementatie varieert van provider tot provider.</span><span class="sxs-lookup"><span data-stu-id="a7897-132">Implementation varies from provider to provider.</span></span>
<span data-ttu-id="a7897-133">Zie [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="a7897-133">For more information, see [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md).</span></span>

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

### <span data-ttu-id="a7897-134">-Include</span><span class="sxs-lookup"><span data-stu-id="a7897-134">-Include</span></span>

<span data-ttu-id="a7897-135">Hiermee wordt een teken reeks matrix opgegeven, een item of items die met deze cmdlet in de bewerking zijn opgenomen.</span><span class="sxs-lookup"><span data-stu-id="a7897-135">Specifies, as a string array, an item or items that this cmdlet includes in the operation.</span></span> <span data-ttu-id="a7897-136">De waarde van deze para meter komt in aanmerking voor de para meter **Path** .</span><span class="sxs-lookup"><span data-stu-id="a7897-136">The value of this parameter qualifies the **Path** parameter.</span></span> <span data-ttu-id="a7897-137">Voer een element of patroon van een pad in, zoals `"*.txt"` .</span><span class="sxs-lookup"><span data-stu-id="a7897-137">Enter a path element or pattern, such as `"*.txt"`.</span></span> <span data-ttu-id="a7897-138">Joker tekens zijn toegestaan.</span><span class="sxs-lookup"><span data-stu-id="a7897-138">Wildcard characters are permitted.</span></span> <span data-ttu-id="a7897-139">De para meter **include** is alleen effectief wanneer de inhoud van een item wordt opgenomen, zoals `C:\Windows\*` , waarbij het Joker teken de inhoud van de `C:\Windows` map bevat.</span><span class="sxs-lookup"><span data-stu-id="a7897-139">The **Include** parameter is effective only when the command includes the contents of an item, such as `C:\Windows\*`, where the wildcard character specifies the contents of the `C:\Windows` directory.</span></span>

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

### <span data-ttu-id="a7897-140">-LiteralPath</span><span class="sxs-lookup"><span data-stu-id="a7897-140">-LiteralPath</span></span>

<span data-ttu-id="a7897-141">Hiermee geeft u een pad naar een of meer locaties.</span><span class="sxs-lookup"><span data-stu-id="a7897-141">Specifies a path to one or more locations.</span></span> <span data-ttu-id="a7897-142">De waarde van **LiteralPath** wordt precies zo gebruikt als deze wordt getypt.</span><span class="sxs-lookup"><span data-stu-id="a7897-142">The value of **LiteralPath** is used exactly as it is typed.</span></span> <span data-ttu-id="a7897-143">Geen tekens worden geïnterpreteerd als joker tekens.</span><span class="sxs-lookup"><span data-stu-id="a7897-143">No characters are interpreted as wildcards.</span></span> <span data-ttu-id="a7897-144">Als het pad escape tekens bevat, plaatst u het tussen enkele aanhalings tekens.</span><span class="sxs-lookup"><span data-stu-id="a7897-144">If the path includes escape characters, enclose it in single quotation marks.</span></span> <span data-ttu-id="a7897-145">Enkele aanhalings tekens geven aan dat Power shell geen karakters interpreteert als escape reeksen.</span><span class="sxs-lookup"><span data-stu-id="a7897-145">Single quotation marks tell PowerShell not to interpret any characters as escape sequences.</span></span>

<span data-ttu-id="a7897-146">Zie [about_Quoting_Rules](../Microsoft.Powershell.Core/About/about_Quoting_Rules.md)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="a7897-146">For more information, see [about_Quoting_Rules](../Microsoft.Powershell.Core/About/about_Quoting_Rules.md).</span></span>

```yaml
Type: System.String[]
Parameter Sets: LiteralPath
Aliases: PSPath

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="a7897-147">-Name</span><span class="sxs-lookup"><span data-stu-id="a7897-147">-Name</span></span>

<span data-ttu-id="a7897-148">Hiermee geeft u de naam op van de eigenschap die moet worden gewist, zoals de naam van een register waarde.</span><span class="sxs-lookup"><span data-stu-id="a7897-148">Specifies the name of the property to be cleared, such as the name of a registry value.</span></span>
<span data-ttu-id="a7897-149">Joker tekens zijn toegestaan.</span><span class="sxs-lookup"><span data-stu-id="a7897-149">Wildcard characters are permitted.</span></span>

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

### <span data-ttu-id="a7897-150">-PassThru</span><span class="sxs-lookup"><span data-stu-id="a7897-150">-PassThru</span></span>

<span data-ttu-id="a7897-151">Retourneert een object dat het item vertegenwoordigt waarmee u werkt.</span><span class="sxs-lookup"><span data-stu-id="a7897-151">Returns an object representing the item with which you are working.</span></span>
<span data-ttu-id="a7897-152">Deze cmdlet genereert standaard geen uitvoer.</span><span class="sxs-lookup"><span data-stu-id="a7897-152">By default, this cmdlet does not generate any output.</span></span>

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

### <span data-ttu-id="a7897-153">-Path</span><span class="sxs-lookup"><span data-stu-id="a7897-153">-Path</span></span>

<span data-ttu-id="a7897-154">Hiermee geeft u het pad op naar de eigenschap die wordt gewist.</span><span class="sxs-lookup"><span data-stu-id="a7897-154">Specifies the path to the property being cleared.</span></span>
<span data-ttu-id="a7897-155">Joker tekens zijn toegestaan.</span><span class="sxs-lookup"><span data-stu-id="a7897-155">Wildcard characters are permitted.</span></span>

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

### <span data-ttu-id="a7897-156">-UseTransaction</span><span class="sxs-lookup"><span data-stu-id="a7897-156">-UseTransaction</span></span>

<span data-ttu-id="a7897-157">Hiermee wordt de opdracht opgenomen in de actieve transactie.</span><span class="sxs-lookup"><span data-stu-id="a7897-157">Includes the command in the active transaction.</span></span>
<span data-ttu-id="a7897-158">Deze parameter is alleen geldig wanneer een transactie wordt uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="a7897-158">This parameter is valid only when a transaction is in progress.</span></span>
<span data-ttu-id="a7897-159">Zie about_Transactions voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="a7897-159">For more information, see about_Transactions.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: usetx

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="a7897-160">-Confirm</span><span class="sxs-lookup"><span data-stu-id="a7897-160">-Confirm</span></span>

<span data-ttu-id="a7897-161">Hiermee wordt u gevraagd om bevestiging voordat u de cmdlet uitvoert.</span><span class="sxs-lookup"><span data-stu-id="a7897-161">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="a7897-162">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="a7897-162">-WhatIf</span></span>

<span data-ttu-id="a7897-163">Hiermee wordt weergegeven wat er zou gebeuren als u de cmdlet uitvoert.</span><span class="sxs-lookup"><span data-stu-id="a7897-163">Shows what would happen if the cmdlet runs.</span></span>
<span data-ttu-id="a7897-164">De cmdlet wordt niet uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="a7897-164">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="a7897-165">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="a7897-165">CommonParameters</span></span>

<span data-ttu-id="a7897-166">Deze cmdlet biedt ondersteuning voor de algemene para meters: `-Debug` , `-ErrorAction` , `-ErrorVariable` , `-InformationAction` , `-InformationVariable` , `-OutVariable` , `-OutBuffer` , `-PipelineVariable` , `-Verbose` , `-WarningAction` en `-WarningVariable` .</span><span class="sxs-lookup"><span data-stu-id="a7897-166">This cmdlet supports the common parameters: `-Debug`, `-ErrorAction`, `-ErrorVariable`, `-InformationAction`, `-InformationVariable`, `-OutVariable`, `-OutBuffer`, `-PipelineVariable`, `-Verbose`, `-WarningAction`, and `-WarningVariable`.</span></span> <span data-ttu-id="a7897-167">Zie [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="a7897-167">For more information, see [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md).</span></span>

## <span data-ttu-id="a7897-168">INVOER</span><span class="sxs-lookup"><span data-stu-id="a7897-168">INPUTS</span></span>

### <span data-ttu-id="a7897-169">System. String</span><span class="sxs-lookup"><span data-stu-id="a7897-169">System.String</span></span>

<span data-ttu-id="a7897-170">U kunt een padtekenreeks door sluizen naar deze cmdlet.</span><span class="sxs-lookup"><span data-stu-id="a7897-170">You can pipe a path string to this cmdlet.</span></span>

## <span data-ttu-id="a7897-171">UITVOER</span><span class="sxs-lookup"><span data-stu-id="a7897-171">OUTPUTS</span></span>

### <span data-ttu-id="a7897-172">Geen of System. Management. Automation. PSCustomObject</span><span class="sxs-lookup"><span data-stu-id="a7897-172">None or System.Management.Automation.PSCustomObject</span></span>

<span data-ttu-id="a7897-173">Wanneer u de para meter *PassThru* gebruikt, wordt `Clear-ItemProperty` een **PSCustomObject** -object gegenereerd dat de eigenschap voor de gewiste items vertegenwoordigt.</span><span class="sxs-lookup"><span data-stu-id="a7897-173">When you use the *PassThru* parameter, `Clear-ItemProperty` generates a **PSCustomObject** object that represents the cleared item property.</span></span>
<span data-ttu-id="a7897-174">Anders wordt met deze cmdlet geen uitvoer gegenereerd.</span><span class="sxs-lookup"><span data-stu-id="a7897-174">Otherwise, this cmdlet does not generate any output.</span></span>

## <span data-ttu-id="a7897-175">OPMERKINGEN</span><span class="sxs-lookup"><span data-stu-id="a7897-175">NOTES</span></span>

<span data-ttu-id="a7897-176">U kunt gebruiken `Clear-ItemProperty` om de gegevens in register waarden te verwijderen zonder de waarde te verwijderen.</span><span class="sxs-lookup"><span data-stu-id="a7897-176">You can use `Clear-ItemProperty` to delete the data in registry values without deleting the value.</span></span> <span data-ttu-id="a7897-177">Als het gegevens type van de waarde binary of DWORD is, wordt met het wissen van de gegevens de waarde ingesteld op nul.</span><span class="sxs-lookup"><span data-stu-id="a7897-177">If the data type of the value is Binary or DWORD, clearing the data sets the value to zero.</span></span> <span data-ttu-id="a7897-178">Anders is de waarde leeg.</span><span class="sxs-lookup"><span data-stu-id="a7897-178">Otherwise, the value is empty.</span></span>

<span data-ttu-id="a7897-179">De `Clear-ItemProperty` cmdlet is ontworpen om te werken met de gegevens die door elke provider worden weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="a7897-179">The `Clear-ItemProperty` cmdlet is designed to work with the data exposed by any provider.</span></span> <span data-ttu-id="a7897-180">Als u een lijst wilt weer geven van de providers die beschikbaar zijn in uw sessie, typt u `Get-PSProvider` .</span><span class="sxs-lookup"><span data-stu-id="a7897-180">To list the providers available in your session, type `Get-PSProvider`.</span></span> <span data-ttu-id="a7897-181">Zie about_Providers voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="a7897-181">For more information, see about_Providers.</span></span>

## <span data-ttu-id="a7897-182">GERELATEERDE KOPPELINGEN</span><span class="sxs-lookup"><span data-stu-id="a7897-182">RELATED LINKS</span></span>

[<span data-ttu-id="a7897-183">Kopiëren-item Property</span><span class="sxs-lookup"><span data-stu-id="a7897-183">Copy-ItemProperty</span></span>](Copy-ItemProperty.md)

[<span data-ttu-id="a7897-184">Get-item Property</span><span class="sxs-lookup"><span data-stu-id="a7897-184">Get-ItemProperty</span></span>](Get-ItemProperty.md)

[<span data-ttu-id="a7897-185">Verplaatsen-item Property</span><span class="sxs-lookup"><span data-stu-id="a7897-185">Move-ItemProperty</span></span>](Move-ItemProperty.md)

[<span data-ttu-id="a7897-186">Nieuw-item Property</span><span class="sxs-lookup"><span data-stu-id="a7897-186">New-ItemProperty</span></span>](New-ItemProperty.md)

[<span data-ttu-id="a7897-187">Naam wijzigen-item Property</span><span class="sxs-lookup"><span data-stu-id="a7897-187">Rename-ItemProperty</span></span>](Rename-ItemProperty.md)

[<span data-ttu-id="a7897-188">about_Providers</span><span class="sxs-lookup"><span data-stu-id="a7897-188">about_Providers</span></span>](../Microsoft.PowerShell.Core/About/about_Providers.md)
