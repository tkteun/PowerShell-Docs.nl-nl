---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 07/21/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/remove-variable?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Remove-Variable
ms.openlocfilehash: 6b9d351b5092d96d7698a28d3de63a493d566c6d
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 11/17/2020
ms.locfileid: "94706013"
---
# <span data-ttu-id="12dc7-102">Remove-Variable</span><span class="sxs-lookup"><span data-stu-id="12dc7-102">Remove-Variable</span></span>

## <span data-ttu-id="12dc7-103">SAMENVATTING</span><span class="sxs-lookup"><span data-stu-id="12dc7-103">SYNOPSIS</span></span>
<span data-ttu-id="12dc7-104">Hiermee verwijdert u een variabele en de bijbehorende waarde.</span><span class="sxs-lookup"><span data-stu-id="12dc7-104">Deletes a variable and its value.</span></span>

## <span data-ttu-id="12dc7-105">SYNTAXIS</span><span class="sxs-lookup"><span data-stu-id="12dc7-105">SYNTAX</span></span>

```
Remove-Variable [-Name] <String[]> [-Include <String[]>] [-Exclude <String[]>] [-Force] [-Scope <String>]
 [-WhatIf] [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="12dc7-106">BESCHRIJVING</span><span class="sxs-lookup"><span data-stu-id="12dc7-106">DESCRIPTION</span></span>

<span data-ttu-id="12dc7-107">De `Remove-Variable` cmdlet verwijdert een variabele en de waarde ervan uit het bereik waarin deze is gedefinieerd, zoals de huidige sessie.</span><span class="sxs-lookup"><span data-stu-id="12dc7-107">The `Remove-Variable` cmdlet deletes a variable and its value from the scope in which it is defined, such as the current session.</span></span> <span data-ttu-id="12dc7-108">U kunt deze cmdlet niet gebruiken om variabelen te verwijderen die zijn ingesteld als constanten of die eigendom zijn van het systeem.</span><span class="sxs-lookup"><span data-stu-id="12dc7-108">You cannot use this cmdlet to delete variables that are set as constants or those that are owned by the system.</span></span>

## <span data-ttu-id="12dc7-109">VOORBEELDEN</span><span class="sxs-lookup"><span data-stu-id="12dc7-109">EXAMPLES</span></span>

### <span data-ttu-id="12dc7-110">Voor beeld 1: een variabele verwijderen</span><span class="sxs-lookup"><span data-stu-id="12dc7-110">Example 1: Remove a variable</span></span>

```powershell
Remove-Variable Smp
```

<span data-ttu-id="12dc7-111">Met deze opdracht wordt de `$Smp` variabele verwijderd.</span><span class="sxs-lookup"><span data-stu-id="12dc7-111">This command deletes the `$Smp` variable.</span></span>

## <span data-ttu-id="12dc7-112">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="12dc7-112">PARAMETERS</span></span>

### <span data-ttu-id="12dc7-113">-Uitsluiten</span><span class="sxs-lookup"><span data-stu-id="12dc7-113">-Exclude</span></span>

<span data-ttu-id="12dc7-114">Hiermee geeft u een matrix van items op die met deze cmdlet worden wegge laten uit de bewerking.</span><span class="sxs-lookup"><span data-stu-id="12dc7-114">Specifies an array of items that this cmdlet omits from the operation.</span></span> <span data-ttu-id="12dc7-115">De waarde van deze para meter komt in aanmerking voor de para meter **name** .</span><span class="sxs-lookup"><span data-stu-id="12dc7-115">The value of this parameter qualifies the **Name** parameter.</span></span> <span data-ttu-id="12dc7-116">Voer een naam element of patroon in, zoals ' s \* '.</span><span class="sxs-lookup"><span data-stu-id="12dc7-116">Enter a name element or pattern, such as "s\*".</span></span> <span data-ttu-id="12dc7-117">Joker tekens zijn toegestaan.</span><span class="sxs-lookup"><span data-stu-id="12dc7-117">Wildcards are permitted.</span></span>

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

### <span data-ttu-id="12dc7-118">-Force</span><span class="sxs-lookup"><span data-stu-id="12dc7-118">-Force</span></span>

<span data-ttu-id="12dc7-119">Geeft aan dat de cmdlet een variabele verwijdert, zelfs als deze alleen-lezen is.</span><span class="sxs-lookup"><span data-stu-id="12dc7-119">Indicates that the cmdlet removes a variable even if it is read-only.</span></span> <span data-ttu-id="12dc7-120">Zelfs met de para meter **Forces** kan de cmdlet een constante niet verwijderen.</span><span class="sxs-lookup"><span data-stu-id="12dc7-120">Even using the **Force** parameter, the cmdlet cannot remove a constant.</span></span>

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

### <span data-ttu-id="12dc7-121">-Include</span><span class="sxs-lookup"><span data-stu-id="12dc7-121">-Include</span></span>

<span data-ttu-id="12dc7-122">Hiermee geeft u een matrix van items op die met deze cmdlet worden verwijderd in de bewerking.</span><span class="sxs-lookup"><span data-stu-id="12dc7-122">Specifies an array of items that this cmdlet deletes in the operation.</span></span> <span data-ttu-id="12dc7-123">De waarde van deze para meter komt in aanmerking voor de para meter **name** .</span><span class="sxs-lookup"><span data-stu-id="12dc7-123">The value of this parameter qualifies the **Name** parameter.</span></span> <span data-ttu-id="12dc7-124">Voer een naam element of patroon in, zoals s \*.</span><span class="sxs-lookup"><span data-stu-id="12dc7-124">Enter a name element or pattern, such as s\*.</span></span> <span data-ttu-id="12dc7-125">Joker tekens zijn toegestaan.</span><span class="sxs-lookup"><span data-stu-id="12dc7-125">Wildcards are permitted.</span></span>

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

### <span data-ttu-id="12dc7-126">-Name</span><span class="sxs-lookup"><span data-stu-id="12dc7-126">-Name</span></span>

<span data-ttu-id="12dc7-127">Hiermee geeft u de naam op van de variabele die moet worden verwijderd.</span><span class="sxs-lookup"><span data-stu-id="12dc7-127">Specifies the name of the variable to be removed.</span></span> <span data-ttu-id="12dc7-128">De parameter naam (**naam**) is optioneel.</span><span class="sxs-lookup"><span data-stu-id="12dc7-128">The parameter name (**Name**) is optional.</span></span>
<span data-ttu-id="12dc7-129">Joker tekens zijn toegestaan</span><span class="sxs-lookup"><span data-stu-id="12dc7-129">Wildcards are permitted</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: True
```

### <span data-ttu-id="12dc7-130">-Bereik</span><span class="sxs-lookup"><span data-stu-id="12dc7-130">-Scope</span></span>

<span data-ttu-id="12dc7-131">Hiermee worden alleen de variabelen in het opgegeven bereik opgehaald.</span><span class="sxs-lookup"><span data-stu-id="12dc7-131">Gets only the variables in the specified scope.</span></span> <span data-ttu-id="12dc7-132">De aanvaardbare waarden voor deze parameter zijn:</span><span class="sxs-lookup"><span data-stu-id="12dc7-132">The acceptable values for this parameter are:</span></span>

- <span data-ttu-id="12dc7-133">Globaal</span><span class="sxs-lookup"><span data-stu-id="12dc7-133">Global</span></span>
- <span data-ttu-id="12dc7-134">Lokaal</span><span class="sxs-lookup"><span data-stu-id="12dc7-134">Local</span></span>
- <span data-ttu-id="12dc7-135">Script</span><span class="sxs-lookup"><span data-stu-id="12dc7-135">Script</span></span>
- <span data-ttu-id="12dc7-136">Een getal dat relatief is ten opzichte van het huidige bereik (0 tot en met het aantal bereiken, waarbij 0 het huidige bereik is en 1 de bovenliggende scope)</span><span class="sxs-lookup"><span data-stu-id="12dc7-136">A number relative to the current scope (0 through the number of scopes, where 0 is the current scope and 1 is its parent)</span></span>

<span data-ttu-id="12dc7-137">Local is de standaard instelling.</span><span class="sxs-lookup"><span data-stu-id="12dc7-137">Local is the default.</span></span> <span data-ttu-id="12dc7-138">Zie [about_Scopes](../Microsoft.PowerShell.Core/About/about_Scopes.md)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="12dc7-138">For more information, see [about_Scopes](../Microsoft.PowerShell.Core/About/about_Scopes.md).</span></span>

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

### <span data-ttu-id="12dc7-139">-Confirm</span><span class="sxs-lookup"><span data-stu-id="12dc7-139">-Confirm</span></span>

<span data-ttu-id="12dc7-140">Hiermee wordt u gevraagd om bevestiging voordat u de cmdlet uitvoert.</span><span class="sxs-lookup"><span data-stu-id="12dc7-140">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="12dc7-141">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="12dc7-141">-WhatIf</span></span>

<span data-ttu-id="12dc7-142">Hiermee wordt weergegeven wat er zou gebeuren als u de cmdlet uitvoert.</span><span class="sxs-lookup"><span data-stu-id="12dc7-142">Shows what would happen if the cmdlet runs.</span></span> <span data-ttu-id="12dc7-143">De cmdlet wordt niet uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="12dc7-143">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="12dc7-144">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="12dc7-144">CommonParameters</span></span>

<span data-ttu-id="12dc7-145">Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="12dc7-145">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="12dc7-146">Zie [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="12dc7-146">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="12dc7-147">INVOER</span><span class="sxs-lookup"><span data-stu-id="12dc7-147">INPUTS</span></span>

### <span data-ttu-id="12dc7-148">System. Management. Automation. PSVariable</span><span class="sxs-lookup"><span data-stu-id="12dc7-148">System.Management.Automation.PSVariable</span></span>

<span data-ttu-id="12dc7-149">U kunt een variabel object door sluizen naar `Remove-Variable` .</span><span class="sxs-lookup"><span data-stu-id="12dc7-149">You can pipe a variable object to `Remove-Variable`.</span></span>

## <span data-ttu-id="12dc7-150">UITVOER</span><span class="sxs-lookup"><span data-stu-id="12dc7-150">OUTPUTS</span></span>

### <span data-ttu-id="12dc7-151">Geen</span><span class="sxs-lookup"><span data-stu-id="12dc7-151">None</span></span>

<span data-ttu-id="12dc7-152">Met deze cmdlet wordt geen uitvoer geretourneerd.</span><span class="sxs-lookup"><span data-stu-id="12dc7-152">This cmdlet does not return any output.</span></span>

## <span data-ttu-id="12dc7-153">OPMERKINGEN</span><span class="sxs-lookup"><span data-stu-id="12dc7-153">NOTES</span></span>

- <span data-ttu-id="12dc7-154">Wijzigingen zijn alleen van invloed op het huidige bereik, zoals een sessie.</span><span class="sxs-lookup"><span data-stu-id="12dc7-154">Changes affect only the current scope, such as a session.</span></span> <span data-ttu-id="12dc7-155">Als u een variabele uit alle sessies wilt verwijderen, voegt `Remove-Variable` u een opdracht toe aan uw Power shell-profiel.</span><span class="sxs-lookup"><span data-stu-id="12dc7-155">To delete a variable from all sessions, add a `Remove-Variable` command to your PowerShell profile.</span></span>

- <span data-ttu-id="12dc7-156">U kunt ook verwijzen naar `Remove-Variable` de ingebouwde alias `rv` .</span><span class="sxs-lookup"><span data-stu-id="12dc7-156">You can also refer to `Remove-Variable` by its built-in alias, `rv`.</span></span> <span data-ttu-id="12dc7-157">Zie [about_Aliases](../Microsoft.PowerShell.Core/About/about_Aliases.md)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="12dc7-157">For more information, see [about_Aliases](../Microsoft.PowerShell.Core/About/about_Aliases.md).</span></span>

## <span data-ttu-id="12dc7-158">GERELATEERDE KOPPELINGEN</span><span class="sxs-lookup"><span data-stu-id="12dc7-158">RELATED LINKS</span></span>

[<span data-ttu-id="12dc7-159">Clear-variabele</span><span class="sxs-lookup"><span data-stu-id="12dc7-159">Clear-Variable</span></span>](Clear-Variable.md)

[<span data-ttu-id="12dc7-160">Get-variabele</span><span class="sxs-lookup"><span data-stu-id="12dc7-160">Get-Variable</span></span>](Get-Variable.md)

[<span data-ttu-id="12dc7-161">Nieuwe variabele</span><span class="sxs-lookup"><span data-stu-id="12dc7-161">New-Variable</span></span>](New-Variable.md)

[<span data-ttu-id="12dc7-162">Set-variabele</span><span class="sxs-lookup"><span data-stu-id="12dc7-162">Set-Variable</span></span>](Set-Variable.md)
