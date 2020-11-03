---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 07/21/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/remove-variable?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Remove-Variable
ms.openlocfilehash: e6bbb1415a29b8dc3ef916ecc6c3e8bc6754583d
ms.sourcegitcommit: 84fcc90bd018ab76ac4e964d53e7c9c2b5a7b6c6
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/23/2020
ms.locfileid: "93251655"
---
# <span data-ttu-id="d88de-103">Remove-Variable</span><span class="sxs-lookup"><span data-stu-id="d88de-103">Remove-Variable</span></span>

## <span data-ttu-id="d88de-104">SAMENVATTING</span><span class="sxs-lookup"><span data-stu-id="d88de-104">SYNOPSIS</span></span>
<span data-ttu-id="d88de-105">Hiermee verwijdert u een variabele en de bijbehorende waarde.</span><span class="sxs-lookup"><span data-stu-id="d88de-105">Deletes a variable and its value.</span></span>

## <span data-ttu-id="d88de-106">SYNTAXIS</span><span class="sxs-lookup"><span data-stu-id="d88de-106">SYNTAX</span></span>

```
Remove-Variable [-Name] <String[]> [-Include <String[]>] [-Exclude <String[]>] [-Force] [-Scope <String>]
 [-WhatIf] [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="d88de-107">BESCHRIJVING</span><span class="sxs-lookup"><span data-stu-id="d88de-107">DESCRIPTION</span></span>

<span data-ttu-id="d88de-108">De `Remove-Variable` cmdlet verwijdert een variabele en de waarde ervan uit het bereik waarin deze is gedefinieerd, zoals de huidige sessie.</span><span class="sxs-lookup"><span data-stu-id="d88de-108">The `Remove-Variable` cmdlet deletes a variable and its value from the scope in which it is defined, such as the current session.</span></span> <span data-ttu-id="d88de-109">U kunt deze cmdlet niet gebruiken om variabelen te verwijderen die zijn ingesteld als constanten of die eigendom zijn van het systeem.</span><span class="sxs-lookup"><span data-stu-id="d88de-109">You cannot use this cmdlet to delete variables that are set as constants or those that are owned by the system.</span></span>

## <span data-ttu-id="d88de-110">VOORBEELDEN</span><span class="sxs-lookup"><span data-stu-id="d88de-110">EXAMPLES</span></span>

### <span data-ttu-id="d88de-111">Voor beeld 1: een variabele verwijderen</span><span class="sxs-lookup"><span data-stu-id="d88de-111">Example 1: Remove a variable</span></span>

```powershell
Remove-Variable Smp
```

<span data-ttu-id="d88de-112">Met deze opdracht wordt de `$Smp` variabele verwijderd.</span><span class="sxs-lookup"><span data-stu-id="d88de-112">This command deletes the `$Smp` variable.</span></span>

## <span data-ttu-id="d88de-113">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="d88de-113">PARAMETERS</span></span>

### <span data-ttu-id="d88de-114">-Uitsluiten</span><span class="sxs-lookup"><span data-stu-id="d88de-114">-Exclude</span></span>

<span data-ttu-id="d88de-115">Hiermee geeft u een matrix van items op die met deze cmdlet worden wegge laten uit de bewerking.</span><span class="sxs-lookup"><span data-stu-id="d88de-115">Specifies an array of items that this cmdlet omits from the operation.</span></span> <span data-ttu-id="d88de-116">De waarde van deze para meter komt in aanmerking voor de para meter **name** .</span><span class="sxs-lookup"><span data-stu-id="d88de-116">The value of this parameter qualifies the **Name** parameter.</span></span> <span data-ttu-id="d88de-117">Voer een naam element of patroon in, zoals ' s \* '.</span><span class="sxs-lookup"><span data-stu-id="d88de-117">Enter a name element or pattern, such as "s\*".</span></span> <span data-ttu-id="d88de-118">Joker tekens zijn toegestaan.</span><span class="sxs-lookup"><span data-stu-id="d88de-118">Wildcards are permitted.</span></span>

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

### <span data-ttu-id="d88de-119">-Force</span><span class="sxs-lookup"><span data-stu-id="d88de-119">-Force</span></span>

<span data-ttu-id="d88de-120">Geeft aan dat de cmdlet een variabele verwijdert, zelfs als deze alleen-lezen is.</span><span class="sxs-lookup"><span data-stu-id="d88de-120">Indicates that the cmdlet removes a variable even if it is read-only.</span></span> <span data-ttu-id="d88de-121">Zelfs met de para meter **Forces** kan de cmdlet een constante niet verwijderen.</span><span class="sxs-lookup"><span data-stu-id="d88de-121">Even using the **Force** parameter, the cmdlet cannot remove a constant.</span></span>

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

### <span data-ttu-id="d88de-122">-Include</span><span class="sxs-lookup"><span data-stu-id="d88de-122">-Include</span></span>

<span data-ttu-id="d88de-123">Hiermee geeft u een matrix van items op die met deze cmdlet worden verwijderd in de bewerking.</span><span class="sxs-lookup"><span data-stu-id="d88de-123">Specifies an array of items that this cmdlet deletes in the operation.</span></span> <span data-ttu-id="d88de-124">De waarde van deze para meter komt in aanmerking voor de para meter **name** .</span><span class="sxs-lookup"><span data-stu-id="d88de-124">The value of this parameter qualifies the **Name** parameter.</span></span> <span data-ttu-id="d88de-125">Voer een naam element of patroon in, zoals s \*.</span><span class="sxs-lookup"><span data-stu-id="d88de-125">Enter a name element or pattern, such as s\*.</span></span> <span data-ttu-id="d88de-126">Joker tekens zijn toegestaan.</span><span class="sxs-lookup"><span data-stu-id="d88de-126">Wildcards are permitted.</span></span>

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

### <span data-ttu-id="d88de-127">-Name</span><span class="sxs-lookup"><span data-stu-id="d88de-127">-Name</span></span>

<span data-ttu-id="d88de-128">Hiermee geeft u de naam op van de variabele die moet worden verwijderd.</span><span class="sxs-lookup"><span data-stu-id="d88de-128">Specifies the name of the variable to be removed.</span></span> <span data-ttu-id="d88de-129">De parameter naam ( **naam** ) is optioneel.</span><span class="sxs-lookup"><span data-stu-id="d88de-129">The parameter name ( **Name** ) is optional.</span></span>
<span data-ttu-id="d88de-130">Joker tekens zijn toegestaan</span><span class="sxs-lookup"><span data-stu-id="d88de-130">Wildcards are permitted</span></span>

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

### <span data-ttu-id="d88de-131">-Bereik</span><span class="sxs-lookup"><span data-stu-id="d88de-131">-Scope</span></span>

<span data-ttu-id="d88de-132">Hiermee worden alleen de variabelen in het opgegeven bereik opgehaald.</span><span class="sxs-lookup"><span data-stu-id="d88de-132">Gets only the variables in the specified scope.</span></span> <span data-ttu-id="d88de-133">De aanvaardbare waarden voor deze parameter zijn:</span><span class="sxs-lookup"><span data-stu-id="d88de-133">The acceptable values for this parameter are:</span></span>

- <span data-ttu-id="d88de-134">Globaal</span><span class="sxs-lookup"><span data-stu-id="d88de-134">Global</span></span>
- <span data-ttu-id="d88de-135">Lokaal</span><span class="sxs-lookup"><span data-stu-id="d88de-135">Local</span></span>
- <span data-ttu-id="d88de-136">Script</span><span class="sxs-lookup"><span data-stu-id="d88de-136">Script</span></span>
- <span data-ttu-id="d88de-137">Een getal dat relatief is ten opzichte van het huidige bereik (0 tot en met het aantal bereiken, waarbij 0 het huidige bereik is en 1 de bovenliggende scope)</span><span class="sxs-lookup"><span data-stu-id="d88de-137">A number relative to the current scope (0 through the number of scopes, where 0 is the current scope and 1 is its parent)</span></span>

<span data-ttu-id="d88de-138">Local is de standaard instelling.</span><span class="sxs-lookup"><span data-stu-id="d88de-138">Local is the default.</span></span> <span data-ttu-id="d88de-139">Zie [about_Scopes](../Microsoft.PowerShell.Core/About/about_Scopes.md)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="d88de-139">For more information, see [about_Scopes](../Microsoft.PowerShell.Core/About/about_Scopes.md).</span></span>

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

### <span data-ttu-id="d88de-140">-Confirm</span><span class="sxs-lookup"><span data-stu-id="d88de-140">-Confirm</span></span>

<span data-ttu-id="d88de-141">Hiermee wordt u gevraagd om bevestiging voordat u de cmdlet uitvoert.</span><span class="sxs-lookup"><span data-stu-id="d88de-141">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="d88de-142">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="d88de-142">-WhatIf</span></span>

<span data-ttu-id="d88de-143">Hiermee wordt weergegeven wat er zou gebeuren als u de cmdlet uitvoert.</span><span class="sxs-lookup"><span data-stu-id="d88de-143">Shows what would happen if the cmdlet runs.</span></span> <span data-ttu-id="d88de-144">De cmdlet wordt niet uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="d88de-144">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="d88de-145">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="d88de-145">CommonParameters</span></span>

<span data-ttu-id="d88de-146">Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="d88de-146">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="d88de-147">Zie [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="d88de-147">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="d88de-148">INVOER</span><span class="sxs-lookup"><span data-stu-id="d88de-148">INPUTS</span></span>

### <span data-ttu-id="d88de-149">System. Management. Automation. PSVariable</span><span class="sxs-lookup"><span data-stu-id="d88de-149">System.Management.Automation.PSVariable</span></span>

<span data-ttu-id="d88de-150">U kunt een variabel object door sluizen naar `Remove-Variable` .</span><span class="sxs-lookup"><span data-stu-id="d88de-150">You can pipe a variable object to `Remove-Variable`.</span></span>

## <span data-ttu-id="d88de-151">UITVOER</span><span class="sxs-lookup"><span data-stu-id="d88de-151">OUTPUTS</span></span>

### <span data-ttu-id="d88de-152">Geen</span><span class="sxs-lookup"><span data-stu-id="d88de-152">None</span></span>

<span data-ttu-id="d88de-153">Met deze cmdlet wordt geen uitvoer geretourneerd.</span><span class="sxs-lookup"><span data-stu-id="d88de-153">This cmdlet does not return any output.</span></span>

## <span data-ttu-id="d88de-154">OPMERKINGEN</span><span class="sxs-lookup"><span data-stu-id="d88de-154">NOTES</span></span>

- <span data-ttu-id="d88de-155">Wijzigingen zijn alleen van invloed op het huidige bereik, zoals een sessie.</span><span class="sxs-lookup"><span data-stu-id="d88de-155">Changes affect only the current scope, such as a session.</span></span> <span data-ttu-id="d88de-156">Als u een variabele uit alle sessies wilt verwijderen, voegt `Remove-Variable` u een opdracht toe aan uw Power shell-profiel.</span><span class="sxs-lookup"><span data-stu-id="d88de-156">To delete a variable from all sessions, add a `Remove-Variable` command to your PowerShell profile.</span></span>

- <span data-ttu-id="d88de-157">U kunt ook verwijzen naar `Remove-Variable` de ingebouwde alias `rv` .</span><span class="sxs-lookup"><span data-stu-id="d88de-157">You can also refer to `Remove-Variable` by its built-in alias, `rv`.</span></span> <span data-ttu-id="d88de-158">Zie [about_Aliases](../Microsoft.PowerShell.Core/About/about_Aliases.md)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="d88de-158">For more information, see [about_Aliases](../Microsoft.PowerShell.Core/About/about_Aliases.md).</span></span>

## <span data-ttu-id="d88de-159">GERELATEERDE KOPPELINGEN</span><span class="sxs-lookup"><span data-stu-id="d88de-159">RELATED LINKS</span></span>

[<span data-ttu-id="d88de-160">Clear-variabele</span><span class="sxs-lookup"><span data-stu-id="d88de-160">Clear-Variable</span></span>](Clear-Variable.md)

[<span data-ttu-id="d88de-161">Get-variabele</span><span class="sxs-lookup"><span data-stu-id="d88de-161">Get-Variable</span></span>](Get-Variable.md)

[<span data-ttu-id="d88de-162">Nieuwe variabele</span><span class="sxs-lookup"><span data-stu-id="d88de-162">New-Variable</span></span>](New-Variable.md)

[<span data-ttu-id="d88de-163">Set-variabele</span><span class="sxs-lookup"><span data-stu-id="d88de-163">Set-Variable</span></span>](Set-Variable.md)
