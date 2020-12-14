---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/clear-variable?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Clear-Variable
ms.openlocfilehash: 0381b48097f75d3195a82a67225cd8d6759e7433
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 11/17/2020
ms.locfileid: "94705601"
---
# <span data-ttu-id="34a9d-102">Clear-Variable</span><span class="sxs-lookup"><span data-stu-id="34a9d-102">Clear-Variable</span></span>

## <span data-ttu-id="34a9d-103">SAMENVATTING</span><span class="sxs-lookup"><span data-stu-id="34a9d-103">SYNOPSIS</span></span>
<span data-ttu-id="34a9d-104">Hiermee verwijdert u de waarde van een variabele.</span><span class="sxs-lookup"><span data-stu-id="34a9d-104">Deletes the value of a variable.</span></span>

## <span data-ttu-id="34a9d-105">SYNTAXIS</span><span class="sxs-lookup"><span data-stu-id="34a9d-105">SYNTAX</span></span>

```
Clear-Variable [-Name] <String[]> [-Include <String[]>] [-Exclude <String[]>] [-Force] [-PassThru]
 [-Scope <String>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="34a9d-106">BESCHRIJVING</span><span class="sxs-lookup"><span data-stu-id="34a9d-106">DESCRIPTION</span></span>

<span data-ttu-id="34a9d-107">Met de cmdlet **Clear-variable** worden de gegevens verwijderd die zijn opgeslagen in een variabele, maar wordt de variabele niet verwijderd.</span><span class="sxs-lookup"><span data-stu-id="34a9d-107">The **Clear-Variable** cmdlet deletes the data stored in a variable, but it does not delete the variable.</span></span>
<span data-ttu-id="34a9d-108">Als gevolg hiervan is de waarde van de variabele NULL (leeg).</span><span class="sxs-lookup"><span data-stu-id="34a9d-108">As a result, the value of the variable is NULL (empty).</span></span>
<span data-ttu-id="34a9d-109">Als de variabele een opgegeven gegevens-of object type heeft, behoudt deze cmdlet het type van het object dat is opgeslagen in de variabele.</span><span class="sxs-lookup"><span data-stu-id="34a9d-109">If the variable has a specified data or object type, this cmdlet preserves the type of the object stored in the variable.</span></span>

## <span data-ttu-id="34a9d-110">VOORBEELDEN</span><span class="sxs-lookup"><span data-stu-id="34a9d-110">EXAMPLES</span></span>

### <span data-ttu-id="34a9d-111">Voor beeld 1: de waarde van globale variabelen verwijderen die beginnen met een zoek reeks</span><span class="sxs-lookup"><span data-stu-id="34a9d-111">Example 1: Remove the value of global variables that begin with a search string</span></span>

```
PS C:\> Clear-Variable my* -Scope Global
```

<span data-ttu-id="34a9d-112">Met deze opdracht wordt de waarde van globale variabelen verwijderd die namen hebben die met mijn beginnen.</span><span class="sxs-lookup"><span data-stu-id="34a9d-112">This command removes the value of global variables that have names that begin with my.</span></span>

### <span data-ttu-id="34a9d-113">Voor beeld 2: een variabele in een onderliggend bereik wissen, maar niet het bovenliggende bereik</span><span class="sxs-lookup"><span data-stu-id="34a9d-113">Example 2: Clear a variable in a child scope but not the parent scope</span></span>

```
PS C:\> $a=3
PS C:\> &{ Clear-Variable a }
PS C:\> $a
3
```

<span data-ttu-id="34a9d-114">Deze opdrachten laten zien dat het wissen van een variabele in een onderliggend bereik de waarde in het bovenliggende bereik niet wist.</span><span class="sxs-lookup"><span data-stu-id="34a9d-114">These commands demonstrate that clearing a variable in a child scope does not clear the value in the parent scope.</span></span>
<span data-ttu-id="34a9d-115">Met de eerste opdracht wordt de waarde van de variabele $A ingesteld op 3.</span><span class="sxs-lookup"><span data-stu-id="34a9d-115">The first command sets the value of the variable $A to 3.</span></span>
<span data-ttu-id="34a9d-116">Met de tweede opdracht wordt de operator Invoke (&) gebruikt voor het uitvoeren van de opdracht voor het **wissen van variabelen** in een nieuwe scope.</span><span class="sxs-lookup"><span data-stu-id="34a9d-116">The second command uses the invoke operator (&) to run the **Clear-Variable** command in a new scope.</span></span>
<span data-ttu-id="34a9d-117">De variabele wordt in het onderliggende bereik gewist (hoewel deze niet bestaat), maar wordt niet gewist in het lokale bereik.</span><span class="sxs-lookup"><span data-stu-id="34a9d-117">The variable is cleared in the child scope (although it did not exist), but it is not cleared in the local scope.</span></span>
<span data-ttu-id="34a9d-118">De derde opdracht, waarmee de waarde van $A wordt opgehaald, geeft aan dat de waarde 3 niet van invloed is.</span><span class="sxs-lookup"><span data-stu-id="34a9d-118">The third command, which gets the value of $A, shows that the value 3 is unaffected.</span></span>

### <span data-ttu-id="34a9d-119">Voor beeld 3: de waarde van de opgegeven variabele verwijderen</span><span class="sxs-lookup"><span data-stu-id="34a9d-119">Example 3: Delete the value of the specified variable</span></span>

```
PS C:\> Clear-Variable -Name "Processes"
```

<span data-ttu-id="34a9d-120">Met deze opdracht wordt de waarde van de variabele met de naam processs verwijderd.</span><span class="sxs-lookup"><span data-stu-id="34a9d-120">This command deletes the value of the variable named Processes.</span></span>
<span data-ttu-id="34a9d-121">Nadat de-cmdlet de bewerking heeft voltooid, bestaat de variabele met de naam processen nog steeds, maar is de waarde Null.</span><span class="sxs-lookup"><span data-stu-id="34a9d-121">After the cmdlet completes the operation, the variable named Processes still exists, but the value is null.</span></span>

## <span data-ttu-id="34a9d-122">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="34a9d-122">PARAMETERS</span></span>

### <span data-ttu-id="34a9d-123">-Uitsluiten</span><span class="sxs-lookup"><span data-stu-id="34a9d-123">-Exclude</span></span>

<span data-ttu-id="34a9d-124">Hiermee wordt een matrix opgegeven met items die met deze cmdlet worden wegge laten in de bewerking.</span><span class="sxs-lookup"><span data-stu-id="34a9d-124">Specifies an array of items that this cmdlet omits in the operation.</span></span>
<span data-ttu-id="34a9d-125">De waarde van deze para meter komt in aanmerking voor de para meter *name* .</span><span class="sxs-lookup"><span data-stu-id="34a9d-125">The value of this parameter qualifies the *Name* parameter.</span></span>
<span data-ttu-id="34a9d-126">Voer een naam element of patroon in, zoals ' s \* '.</span><span class="sxs-lookup"><span data-stu-id="34a9d-126">Enter a name element or pattern, such as "s\*".</span></span>
<span data-ttu-id="34a9d-127">Joker tekens zijn toegestaan.</span><span class="sxs-lookup"><span data-stu-id="34a9d-127">Wildcards are permitted.</span></span>

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

### <span data-ttu-id="34a9d-128">-Force</span><span class="sxs-lookup"><span data-stu-id="34a9d-128">-Force</span></span>

<span data-ttu-id="34a9d-129">Hiermee kan de cmdlet een variabele wissen, zelfs als deze alleen-lezen is.</span><span class="sxs-lookup"><span data-stu-id="34a9d-129">Allows the cmdlet to clear a variable even if it is read-only.</span></span>
<span data-ttu-id="34a9d-130">Zelfs met de para meter Forces kan de cmdlet geen constanten wissen.</span><span class="sxs-lookup"><span data-stu-id="34a9d-130">Even using the Force parameter, the cmdlet cannot clear constants.</span></span>

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

### <span data-ttu-id="34a9d-131">-Include</span><span class="sxs-lookup"><span data-stu-id="34a9d-131">-Include</span></span>

<span data-ttu-id="34a9d-132">Hiermee geeft u een matrix van items op die met deze cmdlet worden opgenomen in de bewerking.</span><span class="sxs-lookup"><span data-stu-id="34a9d-132">Specifies an array of items that this cmdlet includes in the operation.</span></span>
<span data-ttu-id="34a9d-133">De waarde van deze para meter komt in aanmerking voor de para meter *name* .</span><span class="sxs-lookup"><span data-stu-id="34a9d-133">The value of this parameter qualifies the *Name* parameter.</span></span>
<span data-ttu-id="34a9d-134">Voer een naam element of patroon in, zoals ' s \* '.</span><span class="sxs-lookup"><span data-stu-id="34a9d-134">Enter a name element or pattern, such as "s\*".</span></span>
<span data-ttu-id="34a9d-135">Joker tekens zijn toegestaan.</span><span class="sxs-lookup"><span data-stu-id="34a9d-135">Wildcards are permitted.</span></span>

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

### <span data-ttu-id="34a9d-136">-Name</span><span class="sxs-lookup"><span data-stu-id="34a9d-136">-Name</span></span>

<span data-ttu-id="34a9d-137">Hiermee geeft u de naam van de variabele die moet worden gewist.</span><span class="sxs-lookup"><span data-stu-id="34a9d-137">Specifies the name of the variable to be cleared.</span></span>
<span data-ttu-id="34a9d-138">Joker tekens zijn toegestaan.</span><span class="sxs-lookup"><span data-stu-id="34a9d-138">Wildcards are permitted.</span></span>
<span data-ttu-id="34a9d-139">Deze para meter is vereist, maar de parameter naam ("naam") is optioneel.</span><span class="sxs-lookup"><span data-stu-id="34a9d-139">This parameter is required, but the parameter name ("Name") is optional.</span></span>

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

### <span data-ttu-id="34a9d-140">-PassThru</span><span class="sxs-lookup"><span data-stu-id="34a9d-140">-PassThru</span></span>

<span data-ttu-id="34a9d-141">Retourneert een object dat het item vertegenwoordigt waarmee u werkt.</span><span class="sxs-lookup"><span data-stu-id="34a9d-141">Returns an object representing the item with which you are working.</span></span>
<span data-ttu-id="34a9d-142">Deze cmdlet genereert standaard geen uitvoer.</span><span class="sxs-lookup"><span data-stu-id="34a9d-142">By default, this cmdlet does not generate any output.</span></span>

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

### <span data-ttu-id="34a9d-143">-Bereik</span><span class="sxs-lookup"><span data-stu-id="34a9d-143">-Scope</span></span>

<span data-ttu-id="34a9d-144">Hiermee geeft u het bereik op waarin deze alias geldig is.</span><span class="sxs-lookup"><span data-stu-id="34a9d-144">Specifies the scope in which this alias is valid.</span></span>

<span data-ttu-id="34a9d-145">De aanvaardbare waarden voor deze parameter zijn:</span><span class="sxs-lookup"><span data-stu-id="34a9d-145">The acceptable values for this parameter are:</span></span>

- <span data-ttu-id="34a9d-146">Globaal</span><span class="sxs-lookup"><span data-stu-id="34a9d-146">Global</span></span>
- <span data-ttu-id="34a9d-147">Lokaal</span><span class="sxs-lookup"><span data-stu-id="34a9d-147">Local</span></span>
- <span data-ttu-id="34a9d-148">Script</span><span class="sxs-lookup"><span data-stu-id="34a9d-148">Script</span></span>

<span data-ttu-id="34a9d-149">U kunt ook een getal dat relatief is ten opzichte van het huidige bereik (0 tot en met het aantal bereiken), waarbij 0 het huidige bereik is en 1 de bovenliggende Scope.</span><span class="sxs-lookup"><span data-stu-id="34a9d-149">You can also use a number relative to the current scope (0 through the number of scopes, where 0 is the current scope and 1 is its parent).</span></span>
<span data-ttu-id="34a9d-150">Local is de standaard instelling.</span><span class="sxs-lookup"><span data-stu-id="34a9d-150">Local is the default.</span></span>
<span data-ttu-id="34a9d-151">Zie about_Scopes voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="34a9d-151">For more information, see about_Scopes.</span></span>

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

### <span data-ttu-id="34a9d-152">-Confirm</span><span class="sxs-lookup"><span data-stu-id="34a9d-152">-Confirm</span></span>

<span data-ttu-id="34a9d-153">Hiermee wordt u gevraagd om bevestiging voordat u de cmdlet uitvoert.</span><span class="sxs-lookup"><span data-stu-id="34a9d-153">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="34a9d-154">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="34a9d-154">-WhatIf</span></span>

<span data-ttu-id="34a9d-155">Hiermee wordt weergegeven wat er zou gebeuren als u de cmdlet uitvoert.</span><span class="sxs-lookup"><span data-stu-id="34a9d-155">Shows what would happen if the cmdlet runs.</span></span>
<span data-ttu-id="34a9d-156">De cmdlet wordt niet uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="34a9d-156">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="34a9d-157">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="34a9d-157">CommonParameters</span></span>

<span data-ttu-id="34a9d-158">Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="34a9d-158">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="34a9d-159">Zie [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="34a9d-159">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="34a9d-160">INVOER</span><span class="sxs-lookup"><span data-stu-id="34a9d-160">INPUTS</span></span>

### <span data-ttu-id="34a9d-161">Geen</span><span class="sxs-lookup"><span data-stu-id="34a9d-161">None</span></span>

<span data-ttu-id="34a9d-162">U kunt geen objecten naar deze cmdlet pipeen.</span><span class="sxs-lookup"><span data-stu-id="34a9d-162">You cannot pipe objects to this cmdlet.</span></span>

## <span data-ttu-id="34a9d-163">UITVOER</span><span class="sxs-lookup"><span data-stu-id="34a9d-163">OUTPUTS</span></span>

### <span data-ttu-id="34a9d-164">Geen of System. Management. Automation. PSVariable</span><span class="sxs-lookup"><span data-stu-id="34a9d-164">None or System.Management.Automation.PSVariable</span></span>

<span data-ttu-id="34a9d-165">Wanneer u de para meter *PassThru* gebruikt, genereert deze cmdlet een **System. Management. Automation. PSVariable** -object dat de gewiste variabele vertegenwoordigt.</span><span class="sxs-lookup"><span data-stu-id="34a9d-165">When you use the *PassThru* parameter, this cmdlet generates a **System.Management.Automation.PSVariable** object representing the cleared variable.</span></span>
<span data-ttu-id="34a9d-166">Anders wordt met deze cmdlet geen uitvoer gegenereerd.</span><span class="sxs-lookup"><span data-stu-id="34a9d-166">Otherwise, this cmdlet does not generate any output.</span></span>

## <span data-ttu-id="34a9d-167">OPMERKINGEN</span><span class="sxs-lookup"><span data-stu-id="34a9d-167">NOTES</span></span>

* <span data-ttu-id="34a9d-168">Als u een variabele wilt verwijderen, samen met de bijbehorende waarde, gebruikt u Remove-Variable of verwijderen.</span><span class="sxs-lookup"><span data-stu-id="34a9d-168">To delete a variable, along with its value, use Remove-Variable or Remove-Item.</span></span>

  <span data-ttu-id="34a9d-169">Met deze cmdlet worden de waarden van variabelen die zijn ingesteld als constanten of het eigendom van het systeem, zelfs niet verwijderd als u de para meter *Forces* gebruikt.</span><span class="sxs-lookup"><span data-stu-id="34a9d-169">This cmdlet does not delete the values of variables that are set as constants or owned by the system, even if you use the *Force* parameter.</span></span>

  <span data-ttu-id="34a9d-170">Als de variabele die u wist niet bestaat, heeft de cmdlet geen effect.</span><span class="sxs-lookup"><span data-stu-id="34a9d-170">If the variable that you are clearing does not exist, the cmdlet has no effect.</span></span>
<span data-ttu-id="34a9d-171">Er wordt geen variabele met een null-waarde gemaakt.</span><span class="sxs-lookup"><span data-stu-id="34a9d-171">It does not create a variable with a null value.</span></span>

  <span data-ttu-id="34a9d-172">U kunt ook verwijzen naar een **duidelijke variabele** met de ingebouwde alias CLV.</span><span class="sxs-lookup"><span data-stu-id="34a9d-172">You can also refer to **Clear-Variable** by its built-in alias, clv.</span></span>
<span data-ttu-id="34a9d-173">Zie about_Aliases voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="34a9d-173">For more information, see about_Aliases.</span></span>

*

## <span data-ttu-id="34a9d-174">GERELATEERDE KOPPELINGEN</span><span class="sxs-lookup"><span data-stu-id="34a9d-174">RELATED LINKS</span></span>

[<span data-ttu-id="34a9d-175">Get-variabele</span><span class="sxs-lookup"><span data-stu-id="34a9d-175">Get-Variable</span></span>](Get-Variable.md)

[<span data-ttu-id="34a9d-176">Nieuwe variabele</span><span class="sxs-lookup"><span data-stu-id="34a9d-176">New-Variable</span></span>](New-Variable.md)

[<span data-ttu-id="34a9d-177">Remove-variabele</span><span class="sxs-lookup"><span data-stu-id="34a9d-177">Remove-Variable</span></span>](Remove-Variable.md)

[<span data-ttu-id="34a9d-178">Set-variabele</span><span class="sxs-lookup"><span data-stu-id="34a9d-178">Set-Variable</span></span>](Set-Variable.md)

