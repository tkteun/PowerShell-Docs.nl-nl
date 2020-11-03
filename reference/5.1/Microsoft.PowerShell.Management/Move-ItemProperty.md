---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 10/18/2018
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/move-itemproperty?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Move-ItemProperty
ms.openlocfilehash: 4cf883964e1ff86487bf5abca8789af62b274c8a
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/07/2020
ms.locfileid: "93250599"
---
# <span data-ttu-id="8c941-103">Move-ItemProperty</span><span class="sxs-lookup"><span data-stu-id="8c941-103">Move-ItemProperty</span></span>

## <span data-ttu-id="8c941-104">Samen vatting</span><span class="sxs-lookup"><span data-stu-id="8c941-104">Synopsis</span></span>
<span data-ttu-id="8c941-105">Verplaatst een eigenschap van de ene locatie naar een andere.</span><span class="sxs-lookup"><span data-stu-id="8c941-105">Moves a property from one location to another.</span></span>

## <span data-ttu-id="8c941-106">SYNTAXIS</span><span class="sxs-lookup"><span data-stu-id="8c941-106">SYNTAX</span></span>

### <span data-ttu-id="8c941-107">Pad (standaard)</span><span class="sxs-lookup"><span data-stu-id="8c941-107">Path (Default)</span></span>

```
Move-ItemProperty [-Path] <String[]> [-Name] <String[]> [-Destination] <String> [-PassThru] [-Force]
 [-Filter <String>] [-Include <String[]>] [-Exclude <String[]>] [-Credential <PSCredential>] [-WhatIf]
 [-Confirm] [-UseTransaction] [<CommonParameters>]
```

### <span data-ttu-id="8c941-108">LiteralPath</span><span class="sxs-lookup"><span data-stu-id="8c941-108">LiteralPath</span></span>

```
Move-ItemProperty -LiteralPath <String[]> [-Name] <String[]> [-Destination] <String> [-PassThru] [-Force]
 [-Filter <String>] [-Include <String[]>] [-Exclude <String[]>] [-Credential <PSCredential>] [-WhatIf]
 [-Confirm] [-UseTransaction] [<CommonParameters>]
```

## <span data-ttu-id="8c941-109">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="8c941-109">Description</span></span>

<span data-ttu-id="8c941-110">Met de `Move-ItemProperty` cmdlet wordt een eigenschap van een item van het ene naar het andere item verplaatst.</span><span class="sxs-lookup"><span data-stu-id="8c941-110">The `Move-ItemProperty` cmdlet moves a property of an item from one item to another item.</span></span>
<span data-ttu-id="8c941-111">Zo kan het een register vermelding van de ene register sleutel naar een andere register sleutel verplaatsen.</span><span class="sxs-lookup"><span data-stu-id="8c941-111">For instance, it can move a registry entry from one registry key to another registry key.</span></span>
<span data-ttu-id="8c941-112">Wanneer u een item eigenschap verplaatst, wordt deze toegevoegd aan de nieuwe locatie en verwijderd uit de oorspronkelijke locatie.</span><span class="sxs-lookup"><span data-stu-id="8c941-112">When you move an item property, it is added to the new location and deleted from its original location.</span></span>

## <span data-ttu-id="8c941-113">VOORBEELDEN</span><span class="sxs-lookup"><span data-stu-id="8c941-113">EXAMPLES</span></span>

### <span data-ttu-id="8c941-114">Voor beeld 1: een register waarde en de bijbehorende gegevens naar een andere sleutel verplaatsen</span><span class="sxs-lookup"><span data-stu-id="8c941-114">Example 1: Move a registry value and its data to another key</span></span>

<span data-ttu-id="8c941-115">Met deze opdracht worden de versie register waarde en de bijbehorende gegevens van de subsleutel ' Mijntoep ' verplaatst naar de subsleutel NewApp van de `HKLM\Software\MyCompany` register sleutel.</span><span class="sxs-lookup"><span data-stu-id="8c941-115">This command moves the Version registry value, and its data, from the "MyApp" subkey to the NewApp subkey of the `HKLM\Software\MyCompany` registry key.</span></span>

```powershell
Move-ItemProperty "HKLM:\Software\MyCompany\MyApp" -Name "Version" -Destination "HKLM:\Software\MyCompany\NewApp"
```

## <span data-ttu-id="8c941-116">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="8c941-116">PARAMETERS</span></span>

### <span data-ttu-id="8c941-117">-Credential</span><span class="sxs-lookup"><span data-stu-id="8c941-117">-Credential</span></span>

> [!NOTE]
> <span data-ttu-id="8c941-118">Deze para meter wordt niet ondersteund door providers die zijn geïnstalleerd met Power shell.</span><span class="sxs-lookup"><span data-stu-id="8c941-118">This parameter is not supported by any providers installed with PowerShell.</span></span>
> <span data-ttu-id="8c941-119">Gebruik [invoke-Command](../Microsoft.PowerShell.Core/Invoke-Command.md)om een andere gebruiker te imiteren of uw referenties te verhogen wanneer u deze cmdlet uitvoert.</span><span class="sxs-lookup"><span data-stu-id="8c941-119">To impersonate another user, or elevate your credentials when running this cmdlet, use [Invoke-Command](../Microsoft.PowerShell.Core/Invoke-Command.md).</span></span>

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

### <span data-ttu-id="8c941-120">-Bestemming</span><span class="sxs-lookup"><span data-stu-id="8c941-120">-Destination</span></span>

<span data-ttu-id="8c941-121">Hiermee geeft u het pad naar de doel locatie.</span><span class="sxs-lookup"><span data-stu-id="8c941-121">Specifies the path to the destination location.</span></span>

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

### <span data-ttu-id="8c941-122">-Uitsluiten</span><span class="sxs-lookup"><span data-stu-id="8c941-122">-Exclude</span></span>

<span data-ttu-id="8c941-123">Hiermee geeft u als een teken reeks matrix een eigenschap of eigenschap op die met deze cmdlet wordt uitgesloten van de bewerking.</span><span class="sxs-lookup"><span data-stu-id="8c941-123">Specifies, as a string array, a property or property that this cmdlet excludes from the operation.</span></span>
<span data-ttu-id="8c941-124">De waarde van deze para meter komt in aanmerking voor de para meter **Path** .</span><span class="sxs-lookup"><span data-stu-id="8c941-124">The value of this parameter qualifies the **Path** parameter.</span></span>
<span data-ttu-id="8c941-125">Voer een element of patroon van een pad in, zoals \*. txt.</span><span class="sxs-lookup"><span data-stu-id="8c941-125">Enter a path element or pattern, such as "\*.txt".</span></span>
<span data-ttu-id="8c941-126">Joker tekens zijn toegestaan.</span><span class="sxs-lookup"><span data-stu-id="8c941-126">Wildcard characters are permitted.</span></span>

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

### <span data-ttu-id="8c941-127">-Filter</span><span class="sxs-lookup"><span data-stu-id="8c941-127">-Filter</span></span>

<span data-ttu-id="8c941-128">Hiermee geeft u een filter op in de indeling of taal van de provider.</span><span class="sxs-lookup"><span data-stu-id="8c941-128">Specifies a filter in the format or language of the provider.</span></span>
<span data-ttu-id="8c941-129">De waarde van deze para meter komt in aanmerking voor de para meter **Path** .</span><span class="sxs-lookup"><span data-stu-id="8c941-129">The value of this parameter qualifies the **Path** parameter.</span></span>

<span data-ttu-id="8c941-130">De syntaxis van het filter, inclusief het gebruik van joker tekens, is afhankelijk van de provider.</span><span class="sxs-lookup"><span data-stu-id="8c941-130">The syntax of the filter, including the use of wildcard characters, depends on the provider.</span></span>
<span data-ttu-id="8c941-131">Filters zijn efficiënter dan andere para meters, omdat deze door de provider worden toegepast wanneer de cmdlet de objecten ophaalt in plaats van dat Power shell de objecten heeft gefilterd nadat ze zijn opgehaald.</span><span class="sxs-lookup"><span data-stu-id="8c941-131">Filters are more efficient than other parameters, because the provider applies them when the cmdlet gets the objects rather than having PowerShell filter the objects after they are retrieved.</span></span>

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

### <span data-ttu-id="8c941-132">-Force</span><span class="sxs-lookup"><span data-stu-id="8c941-132">-Force</span></span>

<span data-ttu-id="8c941-133">Hiermee wordt de opdracht uitgevoerd zonder dat de gebruiker om bevestiging wordt gevraagd.</span><span class="sxs-lookup"><span data-stu-id="8c941-133">Forces the command to run without asking for user confirmation.</span></span>
<span data-ttu-id="8c941-134">De implementatie varieert van provider tot provider.</span><span class="sxs-lookup"><span data-stu-id="8c941-134">Implementation varies from provider to provider.</span></span>
<span data-ttu-id="8c941-135">Zie [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="8c941-135">For more information, see [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md).</span></span>

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

### <span data-ttu-id="8c941-136">-Include</span><span class="sxs-lookup"><span data-stu-id="8c941-136">-Include</span></span>

<span data-ttu-id="8c941-137">Hiermee geeft u als een teken reeks matrix een eigenschap of eigenschap op die met deze cmdlet in de bewerking wordt opgenomen.</span><span class="sxs-lookup"><span data-stu-id="8c941-137">Specifies, as a string array, a property or property that this cmdlet includes in the operation.</span></span>
<span data-ttu-id="8c941-138">De waarde van deze para meter komt in aanmerking voor de para meter **Path** .</span><span class="sxs-lookup"><span data-stu-id="8c941-138">The value of this parameter qualifies the **Path** parameter.</span></span>
<span data-ttu-id="8c941-139">Voer een element of patroon van een pad in, zoals \*. txt.</span><span class="sxs-lookup"><span data-stu-id="8c941-139">Enter a path element or pattern, such as "\*.txt".</span></span>
<span data-ttu-id="8c941-140">Joker tekens zijn toegestaan.</span><span class="sxs-lookup"><span data-stu-id="8c941-140">Wildcard characters are permitted.</span></span>

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

### <span data-ttu-id="8c941-141">-LiteralPath</span><span class="sxs-lookup"><span data-stu-id="8c941-141">-LiteralPath</span></span>

<span data-ttu-id="8c941-142">Hiermee geeft u het pad op naar de huidige locatie van de eigenschap.</span><span class="sxs-lookup"><span data-stu-id="8c941-142">Specifies the path to the current location of the property.</span></span>
<span data-ttu-id="8c941-143">In tegens telling tot de para meter **Path** wordt de waarde van **LiteralPath** precies zo gebruikt als deze wordt getypt.</span><span class="sxs-lookup"><span data-stu-id="8c941-143">Unlike the **Path** parameter, the value of **LiteralPath** is used exactly as it is typed.</span></span>
<span data-ttu-id="8c941-144">Geen tekens worden geïnterpreteerd als joker tekens.</span><span class="sxs-lookup"><span data-stu-id="8c941-144">No characters are interpreted as wildcards.</span></span>
<span data-ttu-id="8c941-145">Als het pad escape tekens bevat, plaatst u het tussen enkele aanhalings tekens.</span><span class="sxs-lookup"><span data-stu-id="8c941-145">If the path includes escape characters, enclose it in single quotation marks.</span></span>
<span data-ttu-id="8c941-146">Enkele aanhalings tekens geven aan dat Power shell geen karakters interpreteert als escape reeksen.</span><span class="sxs-lookup"><span data-stu-id="8c941-146">Single quotation marks tell PowerShell not to interpret any characters as escape sequences.</span></span>

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

### <span data-ttu-id="8c941-147">-Name</span><span class="sxs-lookup"><span data-stu-id="8c941-147">-Name</span></span>

<span data-ttu-id="8c941-148">Hiermee geeft u de naam van de eigenschap die moet worden verplaatst.</span><span class="sxs-lookup"><span data-stu-id="8c941-148">Specifies the name of the property to be moved.</span></span>

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

### <span data-ttu-id="8c941-149">-PassThru</span><span class="sxs-lookup"><span data-stu-id="8c941-149">-PassThru</span></span>

<span data-ttu-id="8c941-150">Retourneert een object dat het item vertegenwoordigt waarmee u werkt.</span><span class="sxs-lookup"><span data-stu-id="8c941-150">Returns an object representing the item with which you are working.</span></span>
<span data-ttu-id="8c941-151">Deze cmdlet genereert standaard geen uitvoer.</span><span class="sxs-lookup"><span data-stu-id="8c941-151">By default, this cmdlet does not generate any output.</span></span>

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

### <span data-ttu-id="8c941-152">-Path</span><span class="sxs-lookup"><span data-stu-id="8c941-152">-Path</span></span>

<span data-ttu-id="8c941-153">Hiermee geeft u het pad op naar de huidige locatie van de eigenschap.</span><span class="sxs-lookup"><span data-stu-id="8c941-153">Specifies the path to the current location of the property.</span></span>
<span data-ttu-id="8c941-154">Joker tekens zijn toegestaan.</span><span class="sxs-lookup"><span data-stu-id="8c941-154">Wildcard characters are permitted.</span></span>

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

### <span data-ttu-id="8c941-155">-UseTransaction</span><span class="sxs-lookup"><span data-stu-id="8c941-155">-UseTransaction</span></span>

<span data-ttu-id="8c941-156">Hiermee wordt de opdracht opgenomen in de actieve transactie.</span><span class="sxs-lookup"><span data-stu-id="8c941-156">Includes the command in the active transaction.</span></span>
<span data-ttu-id="8c941-157">Deze parameter is alleen geldig wanneer een transactie wordt uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="8c941-157">This parameter is valid only when a transaction is in progress.</span></span>
<span data-ttu-id="8c941-158">Zie about_Transactions voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="8c941-158">For more information, see about_Transactions.</span></span>

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

### <span data-ttu-id="8c941-159">-Confirm</span><span class="sxs-lookup"><span data-stu-id="8c941-159">-Confirm</span></span>

<span data-ttu-id="8c941-160">Hiermee wordt u gevraagd om bevestiging voordat u de cmdlet uitvoert.</span><span class="sxs-lookup"><span data-stu-id="8c941-160">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="8c941-161">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="8c941-161">-WhatIf</span></span>

<span data-ttu-id="8c941-162">Hiermee wordt weergegeven wat er zou gebeuren als u de cmdlet uitvoert.</span><span class="sxs-lookup"><span data-stu-id="8c941-162">Shows what would happen if the cmdlet runs.</span></span>
<span data-ttu-id="8c941-163">De cmdlet wordt niet uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="8c941-163">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="8c941-164">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="8c941-164">CommonParameters</span></span>

<span data-ttu-id="8c941-165">Deze cmdlet biedt ondersteuning voor de algemene para meters: `-Debug` , `-ErrorAction` , `-ErrorVariable` , `-InformationAction` , `-InformationVariable` , `-OutVariable` , `-OutBuffer` , `-PipelineVariable` , `-Verbose` , `-WarningAction` en `-WarningVariable` .</span><span class="sxs-lookup"><span data-stu-id="8c941-165">This cmdlet supports the common parameters: `-Debug`, `-ErrorAction`, `-ErrorVariable`, `-InformationAction`, `-InformationVariable`, `-OutVariable`, `-OutBuffer`, `-PipelineVariable`, `-Verbose`, `-WarningAction`, and `-WarningVariable`.</span></span> <span data-ttu-id="8c941-166">Zie [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="8c941-166">For more information, see [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md).</span></span>

## <span data-ttu-id="8c941-167">INVOER</span><span class="sxs-lookup"><span data-stu-id="8c941-167">INPUTS</span></span>

### <span data-ttu-id="8c941-168">System. String</span><span class="sxs-lookup"><span data-stu-id="8c941-168">System.String</span></span>

<span data-ttu-id="8c941-169">U kunt een teken reeks met een pad naar deze cmdlet door sluizen.</span><span class="sxs-lookup"><span data-stu-id="8c941-169">You can pipe a string that contains a path to this cmdlet.</span></span>

## <span data-ttu-id="8c941-170">UITVOER</span><span class="sxs-lookup"><span data-stu-id="8c941-170">OUTPUTS</span></span>

### <span data-ttu-id="8c941-171">Geen of System. Management. Automation. PSCustomObject</span><span class="sxs-lookup"><span data-stu-id="8c941-171">None or System.Management.Automation.PSCustomObject</span></span>

<span data-ttu-id="8c941-172">Wanneer u de para meter **PassThru** gebruikt, genereert deze cmdlet een **PSCustomObject** die de eigenschap verplaatste items vertegenwoordigt.</span><span class="sxs-lookup"><span data-stu-id="8c941-172">When you use the **PassThru** parameter, this cmdlet generates a **PSCustomObject** representing the moved item property.</span></span>
<span data-ttu-id="8c941-173">Anders wordt met deze cmdlet geen uitvoer gegenereerd.</span><span class="sxs-lookup"><span data-stu-id="8c941-173">Otherwise, this cmdlet does not generate any output.</span></span>

## <span data-ttu-id="8c941-174">OPMERKINGEN</span><span class="sxs-lookup"><span data-stu-id="8c941-174">NOTES</span></span>

<span data-ttu-id="8c941-175">Deze cmdlet is ontworpen om te werken met de gegevens die door elke provider worden weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="8c941-175">This cmdlet is designed to work with the data exposed by any provider.</span></span> <span data-ttu-id="8c941-176">Als u een lijst wilt weer geven van de providers die beschikbaar zijn in uw sessie, typt u `Get-PSProvider` .</span><span class="sxs-lookup"><span data-stu-id="8c941-176">To list the providers available in your session, type `Get-PSProvider`.</span></span> <span data-ttu-id="8c941-177">Zie [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="8c941-177">For more information, see [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md).</span></span>

## <span data-ttu-id="8c941-178">GERELATEERDE KOPPELINGEN</span><span class="sxs-lookup"><span data-stu-id="8c941-178">RELATED LINKS</span></span>

[<span data-ttu-id="8c941-179">Wissen-item Property</span><span class="sxs-lookup"><span data-stu-id="8c941-179">Clear-ItemProperty</span></span>](Clear-ItemProperty.md)

[<span data-ttu-id="8c941-180">Kopiëren-item Property</span><span class="sxs-lookup"><span data-stu-id="8c941-180">Copy-ItemProperty</span></span>](Copy-ItemProperty.md)

[<span data-ttu-id="8c941-181">Get-item Property</span><span class="sxs-lookup"><span data-stu-id="8c941-181">Get-ItemProperty</span></span>](Get-ItemProperty.md)

[<span data-ttu-id="8c941-182">Nieuw-item Property</span><span class="sxs-lookup"><span data-stu-id="8c941-182">New-ItemProperty</span></span>](New-ItemProperty.md)

[<span data-ttu-id="8c941-183">Verwijderen-item Property</span><span class="sxs-lookup"><span data-stu-id="8c941-183">Remove-ItemProperty</span></span>](Remove-ItemProperty.md)

[<span data-ttu-id="8c941-184">Naam wijzigen-item Property</span><span class="sxs-lookup"><span data-stu-id="8c941-184">Rename-ItemProperty</span></span>](Rename-ItemProperty.md)

[<span data-ttu-id="8c941-185">Set-item Property</span><span class="sxs-lookup"><span data-stu-id="8c941-185">Set-ItemProperty</span></span>](Set-ItemProperty.md)

[<span data-ttu-id="8c941-186">about_Providers</span><span class="sxs-lookup"><span data-stu-id="8c941-186">about_Providers</span></span>](../Microsoft.PowerShell.Core/About/about_Providers.md)
