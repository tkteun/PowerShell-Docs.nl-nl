---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/new-alias?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: New-Alias
ms.openlocfilehash: b004cae919c32078d7c2d79174637a0fa4130ab1
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/07/2020
ms.locfileid: "93251289"
---
# <span data-ttu-id="d8062-103">New-Alias</span><span class="sxs-lookup"><span data-stu-id="d8062-103">New-Alias</span></span>

## <span data-ttu-id="d8062-104">SAMENVATTING</span><span class="sxs-lookup"><span data-stu-id="d8062-104">SYNOPSIS</span></span>
<span data-ttu-id="d8062-105">Hiermee maakt u een nieuwe alias.</span><span class="sxs-lookup"><span data-stu-id="d8062-105">Creates a new alias.</span></span>

## <span data-ttu-id="d8062-106">SYNTAXIS</span><span class="sxs-lookup"><span data-stu-id="d8062-106">SYNTAX</span></span>

```
New-Alias [-Name] <String> [-Value] <String> [-Description <String>] [-Option <ScopedItemOptions>] [-PassThru]
 [-Scope <String>] [-Force] [-WhatIf] [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="d8062-107">BESCHRIJVING</span><span class="sxs-lookup"><span data-stu-id="d8062-107">DESCRIPTION</span></span>

<span data-ttu-id="d8062-108">Met de cmdlet **New-alias** maakt u een nieuwe alias in de huidige Power shell-sessie.</span><span class="sxs-lookup"><span data-stu-id="d8062-108">The **New-Alias** cmdlet creates a new alias in the current PowerShell session.</span></span>
<span data-ttu-id="d8062-109">Aliassen die zijn gemaakt met behulp van **New-alias** worden niet opgeslagen nadat u de sessie afsluit of Power shell sluiten.</span><span class="sxs-lookup"><span data-stu-id="d8062-109">Aliases created by using **New-Alias** are not saved after you exit the session or close PowerShell.</span></span>
<span data-ttu-id="d8062-110">U kunt de Export-Alias cmdlet gebruiken om uw alias gegevens op te slaan in een bestand.</span><span class="sxs-lookup"><span data-stu-id="d8062-110">You can use the Export-Alias cmdlet to save your alias information to a file.</span></span>
<span data-ttu-id="d8062-111">U kunt later **import-alias** gebruiken om die opgeslagen alias gegevens op te halen.</span><span class="sxs-lookup"><span data-stu-id="d8062-111">You can later use **Import-Alias** to retrieve that saved alias information.</span></span>

## <span data-ttu-id="d8062-112">VOORBEELDEN</span><span class="sxs-lookup"><span data-stu-id="d8062-112">EXAMPLES</span></span>

### <span data-ttu-id="d8062-113">Voor beeld 1: een alias maken voor een cmdlet</span><span class="sxs-lookup"><span data-stu-id="d8062-113">Example 1: Create an alias for a cmdlet</span></span>

```
PS C:\> New-Alias -Name "List" Get-ChildItem
```

<span data-ttu-id="d8062-114">Met deze opdracht maakt u een alias met de naam lijst die de Get-ChildItem-cmdlet vertegenwoordigt.</span><span class="sxs-lookup"><span data-stu-id="d8062-114">This command creates an alias named List to represent the Get-ChildItem cmdlet.</span></span>

### <span data-ttu-id="d8062-115">Voor beeld 2: een alleen-lezen-alias maken voor een cmdlet</span><span class="sxs-lookup"><span data-stu-id="d8062-115">Example 2: Create a read-only alias for a cmdlet</span></span>

```
PS C:\> New-Alias -Name "W" -Value Get-WmiObject -Description "quick wmi alias" -Option ReadOnly
PS C:\> Get-Alias -Name "W" | Format-List *
```

<span data-ttu-id="d8062-116">Met deze opdracht maakt u een alias met de naam W om de cmdlet Get-WmiObject te vertegenwoordigen.</span><span class="sxs-lookup"><span data-stu-id="d8062-116">This command creates an alias named W to represent the Get-WmiObject cmdlet.</span></span>
<span data-ttu-id="d8062-117">Er wordt een beschrijving, een snelle WMI-alias voor de alias gemaakt en deze wordt alleen-lezen.</span><span class="sxs-lookup"><span data-stu-id="d8062-117">It creates a description, quick wmi alias, for the alias and makes it read-only.</span></span>
<span data-ttu-id="d8062-118">De laatste regel van de opdracht maakt gebruik van Get-Alias om de nieuwe alias te verkrijgen en deze te Format-List om alle informatie hierover weer te geven.</span><span class="sxs-lookup"><span data-stu-id="d8062-118">The last line of the command uses Get-Alias to get the new alias and pipes it to Format-List to display all of the information about it.</span></span>

## <span data-ttu-id="d8062-119">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="d8062-119">PARAMETERS</span></span>

### <span data-ttu-id="d8062-120">-Beschrijving</span><span class="sxs-lookup"><span data-stu-id="d8062-120">-Description</span></span>

<span data-ttu-id="d8062-121">Hiermee geeft u een beschrijving van de alias.</span><span class="sxs-lookup"><span data-stu-id="d8062-121">Specifies a description of the alias.</span></span>
<span data-ttu-id="d8062-122">U kunt een wille keurige teken reeks typen.</span><span class="sxs-lookup"><span data-stu-id="d8062-122">You can type any string.</span></span>
<span data-ttu-id="d8062-123">Als de beschrijving spaties bevat, plaatst u deze tussen aanhalings tekens.</span><span class="sxs-lookup"><span data-stu-id="d8062-123">If the description includes spaces, enclose it in quotation marks.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="d8062-124">-Force</span><span class="sxs-lookup"><span data-stu-id="d8062-124">-Force</span></span>

<span data-ttu-id="d8062-125">Geeft aan dat de cmdlet als Set-Alias fungeert als de alias met de naam al bestaat.</span><span class="sxs-lookup"><span data-stu-id="d8062-125">Indicates that the cmdlet acts like Set-Alias if the alias named already exists.</span></span>

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

### <span data-ttu-id="d8062-126">-Name</span><span class="sxs-lookup"><span data-stu-id="d8062-126">-Name</span></span>

<span data-ttu-id="d8062-127">Hiermee geeft u de nieuwe alias.</span><span class="sxs-lookup"><span data-stu-id="d8062-127">Specifies the new alias.</span></span>
<span data-ttu-id="d8062-128">U kunt alle alfanumerieke tekens in een alias gebruiken, maar het eerste teken mag geen getal zijn.</span><span class="sxs-lookup"><span data-stu-id="d8062-128">You can use any alphanumeric characters in an alias, but the first character cannot be a number.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="d8062-129">-Optie</span><span class="sxs-lookup"><span data-stu-id="d8062-129">-Option</span></span>

<span data-ttu-id="d8062-130">Hiermee geeft u de waarde van de eigenschap **Options** van de alias.</span><span class="sxs-lookup"><span data-stu-id="d8062-130">Specifies the value of the **Options** property of the alias.</span></span>
<span data-ttu-id="d8062-131">Geldige waarden zijn:</span><span class="sxs-lookup"><span data-stu-id="d8062-131">Valid values are:</span></span>

- <span data-ttu-id="d8062-132">Geen: de alias heeft geen beperkingen (standaard waarde)</span><span class="sxs-lookup"><span data-stu-id="d8062-132">None: The alias has no constraints (default value)</span></span>
- <span data-ttu-id="d8062-133">ReadOnly: de alias kan worden verwijderd, maar kan niet worden gewijzigd met behulp van de para meter **Force**</span><span class="sxs-lookup"><span data-stu-id="d8062-133">ReadOnly: The alias can be deleted but cannot be changed except by using the **Force** parameter</span></span>
- <span data-ttu-id="d8062-134">Constante: de alias kan niet worden verwijderd of gewijzigd</span><span class="sxs-lookup"><span data-stu-id="d8062-134">Constant: The alias cannot be deleted or changed</span></span>
- <span data-ttu-id="d8062-135">Persoonlijk: de alias is alleen beschikbaar in het huidige bereik</span><span class="sxs-lookup"><span data-stu-id="d8062-135">Private: The alias is available only in the current scope</span></span>
- <span data-ttu-id="d8062-136">AllScope: de alias wordt gekopieerd naar een nieuwe scope die wordt gemaakt</span><span class="sxs-lookup"><span data-stu-id="d8062-136">AllScope: The alias is copied to any new scopes that are created</span></span>
- <span data-ttu-id="d8062-137">Niet opgegeven: de optie is niet opgegeven</span><span class="sxs-lookup"><span data-stu-id="d8062-137">Unspecified: The option is not specified</span></span>

<span data-ttu-id="d8062-138">Als u de eigenschap **Options** van alle aliassen in de sessie wilt weer geven, typt u `Get-Alias | Format-Table -Property Name, Options -AutoSize` .</span><span class="sxs-lookup"><span data-stu-id="d8062-138">To see the **Options** property of all aliases in the session, type `Get-Alias | Format-Table -Property Name, Options -AutoSize`.</span></span>

```yaml
Type: System.Management.Automation.ScopedItemOptions
Parameter Sets: (All)
Aliases:
Accepted values: None, ReadOnly, Constant, Private, AllScope, Unspecified

Required: False
Position: Named
Default value: [System.Management.Automation.ScopedItemOptions]::None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="d8062-139">-PassThru</span><span class="sxs-lookup"><span data-stu-id="d8062-139">-PassThru</span></span>

<span data-ttu-id="d8062-140">Retourneert een object dat het item vertegenwoordigt waarmee u werkt.</span><span class="sxs-lookup"><span data-stu-id="d8062-140">Returns an object representing the item with which you are working.</span></span>
<span data-ttu-id="d8062-141">Deze cmdlet genereert standaard geen uitvoer.</span><span class="sxs-lookup"><span data-stu-id="d8062-141">By default, this cmdlet does not generate any output.</span></span>

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

### <span data-ttu-id="d8062-142">-Bereik</span><span class="sxs-lookup"><span data-stu-id="d8062-142">-Scope</span></span>

<span data-ttu-id="d8062-143">Hiermee wordt het bereik van de nieuwe alias opgegeven.</span><span class="sxs-lookup"><span data-stu-id="d8062-143">Specifies the scope of the new alias.</span></span>
<span data-ttu-id="d8062-144">De aanvaardbare waarden voor deze parameter zijn:</span><span class="sxs-lookup"><span data-stu-id="d8062-144">The acceptable values for this parameter are:</span></span>

- <span data-ttu-id="d8062-145">Globaal</span><span class="sxs-lookup"><span data-stu-id="d8062-145">Global</span></span>
- <span data-ttu-id="d8062-146">Lokaal</span><span class="sxs-lookup"><span data-stu-id="d8062-146">Local</span></span>
- <span data-ttu-id="d8062-147">Script</span><span class="sxs-lookup"><span data-stu-id="d8062-147">Script</span></span>
- <span data-ttu-id="d8062-148">Een getal dat relatief is ten opzichte van het huidige bereik (0 tot en met het aantal bereiken, waarbij 0 het huidige bereik is en 1 de bovenliggende scope).</span><span class="sxs-lookup"><span data-stu-id="d8062-148">A number relative to the current scope (0 through the number of scopes, where 0 is the current scope and 1 is its parent).</span></span>

<span data-ttu-id="d8062-149">Local is de standaard instelling.</span><span class="sxs-lookup"><span data-stu-id="d8062-149">Local is the default.</span></span>
<span data-ttu-id="d8062-150">Zie about_Scopes voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="d8062-150">For more information, see about_Scopes.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="d8062-151">-Waarde</span><span class="sxs-lookup"><span data-stu-id="d8062-151">-Value</span></span>

<span data-ttu-id="d8062-152">Hiermee geeft u de naam op van de cmdlet of het opdracht element waarvoor een alias wordt toegepast.</span><span class="sxs-lookup"><span data-stu-id="d8062-152">Specifies the name of the cmdlet or command element that is being aliased.</span></span>

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

### <span data-ttu-id="d8062-153">-Confirm</span><span class="sxs-lookup"><span data-stu-id="d8062-153">-Confirm</span></span>

<span data-ttu-id="d8062-154">Hiermee wordt u gevraagd om bevestiging voordat u de cmdlet uitvoert.</span><span class="sxs-lookup"><span data-stu-id="d8062-154">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="d8062-155">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="d8062-155">-WhatIf</span></span>

<span data-ttu-id="d8062-156">Hiermee wordt weergegeven wat er zou gebeuren als u de cmdlet uitvoert.</span><span class="sxs-lookup"><span data-stu-id="d8062-156">Shows what would happen if the cmdlet runs.</span></span>
<span data-ttu-id="d8062-157">De cmdlet wordt niet uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="d8062-157">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="d8062-158">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="d8062-158">CommonParameters</span></span>

<span data-ttu-id="d8062-159">Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="d8062-159">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="d8062-160">Zie [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="d8062-160">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="d8062-161">INVOER</span><span class="sxs-lookup"><span data-stu-id="d8062-161">INPUTS</span></span>

### <span data-ttu-id="d8062-162">Geen</span><span class="sxs-lookup"><span data-stu-id="d8062-162">None</span></span>

<span data-ttu-id="d8062-163">U kunt geen invoer van een pipe naar deze cmdlet.</span><span class="sxs-lookup"><span data-stu-id="d8062-163">You cannot pipe input to this cmdlet.</span></span>

## <span data-ttu-id="d8062-164">UITVOER</span><span class="sxs-lookup"><span data-stu-id="d8062-164">OUTPUTS</span></span>

### <span data-ttu-id="d8062-165">Geen of System. Management. Automation. AliasInfo</span><span class="sxs-lookup"><span data-stu-id="d8062-165">None or System.Management.Automation.AliasInfo</span></span>

<span data-ttu-id="d8062-166">Wanneer u de para meter *PassThru* gebruikt, genereert **New-alias** een **System. Management. Automation. AliasInfo** -object dat de nieuwe alias vertegenwoordigt.</span><span class="sxs-lookup"><span data-stu-id="d8062-166">When you use the *Passthru* parameter, **New-Alias** generates a **System.Management.Automation.AliasInfo** object representing the new alias.</span></span>
<span data-ttu-id="d8062-167">Anders wordt met deze cmdlet geen uitvoer gegenereerd.</span><span class="sxs-lookup"><span data-stu-id="d8062-167">Otherwise, this cmdlet does not generate any output.</span></span>

## <span data-ttu-id="d8062-168">OPMERKINGEN</span><span class="sxs-lookup"><span data-stu-id="d8062-168">NOTES</span></span>

* <span data-ttu-id="d8062-169">Als u een nieuwe alias wilt maken, gebruikt u `Set-Alias` of `New-Alias` .</span><span class="sxs-lookup"><span data-stu-id="d8062-169">To create a new alias, use `Set-Alias` or `New-Alias`.</span></span> <span data-ttu-id="d8062-170">Als u een alias wilt wijzigen, gebruikt u `Set-Alias` .</span><span class="sxs-lookup"><span data-stu-id="d8062-170">To change an alias, use `Set-Alias`.</span></span> <span data-ttu-id="d8062-171">Als u een alias wilt verwijderen, gebruikt u `Remove-Item` .</span><span class="sxs-lookup"><span data-stu-id="d8062-171">To delete an alias, use `Remove-Item`.</span></span>

## <span data-ttu-id="d8062-172">GERELATEERDE KOPPELINGEN</span><span class="sxs-lookup"><span data-stu-id="d8062-172">RELATED LINKS</span></span>

[<span data-ttu-id="d8062-173">Exporteren-alias</span><span class="sxs-lookup"><span data-stu-id="d8062-173">Export-Alias</span></span>](Export-Alias.md)

[<span data-ttu-id="d8062-174">Get-alias</span><span class="sxs-lookup"><span data-stu-id="d8062-174">Get-Alias</span></span>](Get-Alias.md)

[<span data-ttu-id="d8062-175">Import-alias</span><span class="sxs-lookup"><span data-stu-id="d8062-175">Import-Alias</span></span>](Import-Alias.md)

[<span data-ttu-id="d8062-176">Set-alias</span><span class="sxs-lookup"><span data-stu-id="d8062-176">Set-Alias</span></span>](Set-Alias.md)

