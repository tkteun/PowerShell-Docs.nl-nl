---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/clear-variable?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Clear-Variable
ms.openlocfilehash: c696fb0f9d95548d80e772809c6f83e86f1581f6
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/07/2020
ms.locfileid: "93250482"
---
# <span data-ttu-id="7c0cc-103">Clear-Variable</span><span class="sxs-lookup"><span data-stu-id="7c0cc-103">Clear-Variable</span></span>

## <span data-ttu-id="7c0cc-104">SAMENVATTING</span><span class="sxs-lookup"><span data-stu-id="7c0cc-104">SYNOPSIS</span></span>
<span data-ttu-id="7c0cc-105">Hiermee verwijdert u de waarde van een variabele.</span><span class="sxs-lookup"><span data-stu-id="7c0cc-105">Deletes the value of a variable.</span></span>

## <span data-ttu-id="7c0cc-106">SYNTAXIS</span><span class="sxs-lookup"><span data-stu-id="7c0cc-106">SYNTAX</span></span>

```
Clear-Variable [-Name] <String[]> [-Include <String[]>] [-Exclude <String[]>] [-Force] [-PassThru]
 [-Scope <String>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="7c0cc-107">BESCHRIJVING</span><span class="sxs-lookup"><span data-stu-id="7c0cc-107">DESCRIPTION</span></span>

<span data-ttu-id="7c0cc-108">Met de cmdlet **Clear-variable** worden de gegevens verwijderd die zijn opgeslagen in een variabele, maar wordt de variabele niet verwijderd.</span><span class="sxs-lookup"><span data-stu-id="7c0cc-108">The **Clear-Variable** cmdlet deletes the data stored in a variable, but it does not delete the variable.</span></span>
<span data-ttu-id="7c0cc-109">Als gevolg hiervan is de waarde van de variabele NULL (leeg).</span><span class="sxs-lookup"><span data-stu-id="7c0cc-109">As a result, the value of the variable is NULL (empty).</span></span>
<span data-ttu-id="7c0cc-110">Als de variabele een opgegeven gegevens-of object type heeft, behoudt deze cmdlet het type van het object dat is opgeslagen in de variabele.</span><span class="sxs-lookup"><span data-stu-id="7c0cc-110">If the variable has a specified data or object type, this cmdlet preserves the type of the object stored in the variable.</span></span>

## <span data-ttu-id="7c0cc-111">VOORBEELDEN</span><span class="sxs-lookup"><span data-stu-id="7c0cc-111">EXAMPLES</span></span>

### <span data-ttu-id="7c0cc-112">Voor beeld 1: de waarde van globale variabelen verwijderen die beginnen met een zoek reeks</span><span class="sxs-lookup"><span data-stu-id="7c0cc-112">Example 1: Remove the value of global variables that begin with a search string</span></span>

```
PS C:\> Clear-Variable my* -Scope Global
```

<span data-ttu-id="7c0cc-113">Met deze opdracht wordt de waarde van globale variabelen verwijderd die namen hebben die met mijn beginnen.</span><span class="sxs-lookup"><span data-stu-id="7c0cc-113">This command removes the value of global variables that have names that begin with my.</span></span>

### <span data-ttu-id="7c0cc-114">Voor beeld 2: een variabele in een onderliggend bereik wissen, maar niet het bovenliggende bereik</span><span class="sxs-lookup"><span data-stu-id="7c0cc-114">Example 2: Clear a variable in a child scope but not the parent scope</span></span>

```
PS C:\> $a=3
PS C:\> &{ Clear-Variable a }
PS C:\> $a
3
```

<span data-ttu-id="7c0cc-115">Deze opdrachten laten zien dat het wissen van een variabele in een onderliggend bereik de waarde in het bovenliggende bereik niet wist.</span><span class="sxs-lookup"><span data-stu-id="7c0cc-115">These commands demonstrate that clearing a variable in a child scope does not clear the value in the parent scope.</span></span>
<span data-ttu-id="7c0cc-116">Met de eerste opdracht wordt de waarde van de variabele $A ingesteld op 3.</span><span class="sxs-lookup"><span data-stu-id="7c0cc-116">The first command sets the value of the variable $A to 3.</span></span>
<span data-ttu-id="7c0cc-117">Met de tweede opdracht wordt de operator Invoke (&) gebruikt voor het uitvoeren van de opdracht voor het **wissen van variabelen** in een nieuwe scope.</span><span class="sxs-lookup"><span data-stu-id="7c0cc-117">The second command uses the invoke operator (&) to run the **Clear-Variable** command in a new scope.</span></span>
<span data-ttu-id="7c0cc-118">De variabele wordt in het onderliggende bereik gewist (hoewel deze niet bestaat), maar wordt niet gewist in het lokale bereik.</span><span class="sxs-lookup"><span data-stu-id="7c0cc-118">The variable is cleared in the child scope (although it did not exist), but it is not cleared in the local scope.</span></span>
<span data-ttu-id="7c0cc-119">De derde opdracht, waarmee de waarde van $A wordt opgehaald, geeft aan dat de waarde 3 niet van invloed is.</span><span class="sxs-lookup"><span data-stu-id="7c0cc-119">The third command, which gets the value of $A, shows that the value 3 is unaffected.</span></span>

### <span data-ttu-id="7c0cc-120">Voor beeld 3: de waarde van de opgegeven variabele verwijderen</span><span class="sxs-lookup"><span data-stu-id="7c0cc-120">Example 3: Delete the value of the specified variable</span></span>

```
PS C:\> Clear-Variable -Name "Processes"
```

<span data-ttu-id="7c0cc-121">Met deze opdracht wordt de waarde van de variabele met de naam processs verwijderd.</span><span class="sxs-lookup"><span data-stu-id="7c0cc-121">This command deletes the value of the variable named Processes.</span></span>
<span data-ttu-id="7c0cc-122">Nadat de-cmdlet de bewerking heeft voltooid, bestaat de variabele met de naam processen nog steeds, maar is de waarde Null.</span><span class="sxs-lookup"><span data-stu-id="7c0cc-122">After the cmdlet completes the operation, the variable named Processes still exists, but the value is null.</span></span>

## <span data-ttu-id="7c0cc-123">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="7c0cc-123">PARAMETERS</span></span>

### <span data-ttu-id="7c0cc-124">-Uitsluiten</span><span class="sxs-lookup"><span data-stu-id="7c0cc-124">-Exclude</span></span>

<span data-ttu-id="7c0cc-125">Hiermee wordt een matrix opgegeven met items die met deze cmdlet worden wegge laten in de bewerking.</span><span class="sxs-lookup"><span data-stu-id="7c0cc-125">Specifies an array of items that this cmdlet omits in the operation.</span></span>
<span data-ttu-id="7c0cc-126">De waarde van deze para meter komt in aanmerking voor de para meter *name* .</span><span class="sxs-lookup"><span data-stu-id="7c0cc-126">The value of this parameter qualifies the *Name* parameter.</span></span>
<span data-ttu-id="7c0cc-127">Voer een naam element of patroon in, zoals ' s \* '.</span><span class="sxs-lookup"><span data-stu-id="7c0cc-127">Enter a name element or pattern, such as "s\*".</span></span>
<span data-ttu-id="7c0cc-128">Joker tekens zijn toegestaan.</span><span class="sxs-lookup"><span data-stu-id="7c0cc-128">Wildcards are permitted.</span></span>

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

### <span data-ttu-id="7c0cc-129">-Force</span><span class="sxs-lookup"><span data-stu-id="7c0cc-129">-Force</span></span>

<span data-ttu-id="7c0cc-130">Hiermee kan de cmdlet een variabele wissen, zelfs als deze alleen-lezen is.</span><span class="sxs-lookup"><span data-stu-id="7c0cc-130">Allows the cmdlet to clear a variable even if it is read-only.</span></span>
<span data-ttu-id="7c0cc-131">Zelfs met de para meter Forces kan de cmdlet geen constanten wissen.</span><span class="sxs-lookup"><span data-stu-id="7c0cc-131">Even using the Force parameter, the cmdlet cannot clear constants.</span></span>

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

### <span data-ttu-id="7c0cc-132">-Include</span><span class="sxs-lookup"><span data-stu-id="7c0cc-132">-Include</span></span>

<span data-ttu-id="7c0cc-133">Hiermee geeft u een matrix van items op die met deze cmdlet worden opgenomen in de bewerking.</span><span class="sxs-lookup"><span data-stu-id="7c0cc-133">Specifies an array of items that this cmdlet includes in the operation.</span></span>
<span data-ttu-id="7c0cc-134">De waarde van deze para meter komt in aanmerking voor de para meter *name* .</span><span class="sxs-lookup"><span data-stu-id="7c0cc-134">The value of this parameter qualifies the *Name* parameter.</span></span>
<span data-ttu-id="7c0cc-135">Voer een naam element of patroon in, zoals ' s \* '.</span><span class="sxs-lookup"><span data-stu-id="7c0cc-135">Enter a name element or pattern, such as "s\*".</span></span>
<span data-ttu-id="7c0cc-136">Joker tekens zijn toegestaan.</span><span class="sxs-lookup"><span data-stu-id="7c0cc-136">Wildcards are permitted.</span></span>

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

### <span data-ttu-id="7c0cc-137">-Name</span><span class="sxs-lookup"><span data-stu-id="7c0cc-137">-Name</span></span>

<span data-ttu-id="7c0cc-138">Hiermee geeft u de naam van de variabele die moet worden gewist.</span><span class="sxs-lookup"><span data-stu-id="7c0cc-138">Specifies the name of the variable to be cleared.</span></span>
<span data-ttu-id="7c0cc-139">Joker tekens zijn toegestaan.</span><span class="sxs-lookup"><span data-stu-id="7c0cc-139">Wildcards are permitted.</span></span>
<span data-ttu-id="7c0cc-140">Deze para meter is vereist, maar de parameter naam ("naam") is optioneel.</span><span class="sxs-lookup"><span data-stu-id="7c0cc-140">This parameter is required, but the parameter name ("Name") is optional.</span></span>

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

### <span data-ttu-id="7c0cc-141">-PassThru</span><span class="sxs-lookup"><span data-stu-id="7c0cc-141">-PassThru</span></span>

<span data-ttu-id="7c0cc-142">Retourneert een object dat het item vertegenwoordigt waarmee u werkt.</span><span class="sxs-lookup"><span data-stu-id="7c0cc-142">Returns an object representing the item with which you are working.</span></span>
<span data-ttu-id="7c0cc-143">Deze cmdlet genereert standaard geen uitvoer.</span><span class="sxs-lookup"><span data-stu-id="7c0cc-143">By default, this cmdlet does not generate any output.</span></span>

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

### <span data-ttu-id="7c0cc-144">-Bereik</span><span class="sxs-lookup"><span data-stu-id="7c0cc-144">-Scope</span></span>

<span data-ttu-id="7c0cc-145">Hiermee geeft u het bereik op waarin deze alias geldig is.</span><span class="sxs-lookup"><span data-stu-id="7c0cc-145">Specifies the scope in which this alias is valid.</span></span>

<span data-ttu-id="7c0cc-146">De aanvaardbare waarden voor deze parameter zijn:</span><span class="sxs-lookup"><span data-stu-id="7c0cc-146">The acceptable values for this parameter are:</span></span>

- <span data-ttu-id="7c0cc-147">Globaal</span><span class="sxs-lookup"><span data-stu-id="7c0cc-147">Global</span></span>
- <span data-ttu-id="7c0cc-148">Lokaal</span><span class="sxs-lookup"><span data-stu-id="7c0cc-148">Local</span></span>
- <span data-ttu-id="7c0cc-149">Script</span><span class="sxs-lookup"><span data-stu-id="7c0cc-149">Script</span></span>

<span data-ttu-id="7c0cc-150">U kunt ook een getal dat relatief is ten opzichte van het huidige bereik (0 tot en met het aantal bereiken), waarbij 0 het huidige bereik is en 1 de bovenliggende Scope.</span><span class="sxs-lookup"><span data-stu-id="7c0cc-150">You can also use a number relative to the current scope (0 through the number of scopes, where 0 is the current scope and 1 is its parent).</span></span>
<span data-ttu-id="7c0cc-151">Local is de standaard instelling.</span><span class="sxs-lookup"><span data-stu-id="7c0cc-151">Local is the default.</span></span>
<span data-ttu-id="7c0cc-152">Zie about_Scopes voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="7c0cc-152">For more information, see about_Scopes.</span></span>

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

### <span data-ttu-id="7c0cc-153">-Confirm</span><span class="sxs-lookup"><span data-stu-id="7c0cc-153">-Confirm</span></span>

<span data-ttu-id="7c0cc-154">Hiermee wordt u gevraagd om bevestiging voordat u de cmdlet uitvoert.</span><span class="sxs-lookup"><span data-stu-id="7c0cc-154">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="7c0cc-155">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="7c0cc-155">-WhatIf</span></span>

<span data-ttu-id="7c0cc-156">Hiermee wordt weergegeven wat er zou gebeuren als u de cmdlet uitvoert.</span><span class="sxs-lookup"><span data-stu-id="7c0cc-156">Shows what would happen if the cmdlet runs.</span></span>
<span data-ttu-id="7c0cc-157">De cmdlet wordt niet uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="7c0cc-157">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="7c0cc-158">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="7c0cc-158">CommonParameters</span></span>

<span data-ttu-id="7c0cc-159">Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="7c0cc-159">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="7c0cc-160">Zie [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="7c0cc-160">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="7c0cc-161">INVOER</span><span class="sxs-lookup"><span data-stu-id="7c0cc-161">INPUTS</span></span>

### <span data-ttu-id="7c0cc-162">Geen</span><span class="sxs-lookup"><span data-stu-id="7c0cc-162">None</span></span>

<span data-ttu-id="7c0cc-163">U kunt geen objecten naar deze cmdlet pipeen.</span><span class="sxs-lookup"><span data-stu-id="7c0cc-163">You cannot pipe objects to this cmdlet.</span></span>

## <span data-ttu-id="7c0cc-164">UITVOER</span><span class="sxs-lookup"><span data-stu-id="7c0cc-164">OUTPUTS</span></span>

### <span data-ttu-id="7c0cc-165">Geen of System. Management. Automation. PSVariable</span><span class="sxs-lookup"><span data-stu-id="7c0cc-165">None or System.Management.Automation.PSVariable</span></span>

<span data-ttu-id="7c0cc-166">Wanneer u de para meter *PassThru* gebruikt, genereert deze cmdlet een **System. Management. Automation. PSVariable** -object dat de gewiste variabele vertegenwoordigt.</span><span class="sxs-lookup"><span data-stu-id="7c0cc-166">When you use the *PassThru* parameter, this cmdlet generates a **System.Management.Automation.PSVariable** object representing the cleared variable.</span></span>
<span data-ttu-id="7c0cc-167">Anders wordt met deze cmdlet geen uitvoer gegenereerd.</span><span class="sxs-lookup"><span data-stu-id="7c0cc-167">Otherwise, this cmdlet does not generate any output.</span></span>

## <span data-ttu-id="7c0cc-168">OPMERKINGEN</span><span class="sxs-lookup"><span data-stu-id="7c0cc-168">NOTES</span></span>

* <span data-ttu-id="7c0cc-169">Als u een variabele wilt verwijderen, samen met de bijbehorende waarde, gebruikt u Remove-Variable of verwijderen.</span><span class="sxs-lookup"><span data-stu-id="7c0cc-169">To delete a variable, along with its value, use Remove-Variable or Remove-Item.</span></span>

  <span data-ttu-id="7c0cc-170">Met deze cmdlet worden de waarden van variabelen die zijn ingesteld als constanten of het eigendom van het systeem, zelfs niet verwijderd als u de para meter *Forces* gebruikt.</span><span class="sxs-lookup"><span data-stu-id="7c0cc-170">This cmdlet does not delete the values of variables that are set as constants or owned by the system, even if you use the *Force* parameter.</span></span>

  <span data-ttu-id="7c0cc-171">Als de variabele die u wist niet bestaat, heeft de cmdlet geen effect.</span><span class="sxs-lookup"><span data-stu-id="7c0cc-171">If the variable that you are clearing does not exist, the cmdlet has no effect.</span></span>
<span data-ttu-id="7c0cc-172">Er wordt geen variabele met een null-waarde gemaakt.</span><span class="sxs-lookup"><span data-stu-id="7c0cc-172">It does not create a variable with a null value.</span></span>

  <span data-ttu-id="7c0cc-173">U kunt ook verwijzen naar een **duidelijke variabele** met de ingebouwde alias CLV.</span><span class="sxs-lookup"><span data-stu-id="7c0cc-173">You can also refer to **Clear-Variable** by its built-in alias, clv.</span></span>
<span data-ttu-id="7c0cc-174">Zie about_Aliases voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="7c0cc-174">For more information, see about_Aliases.</span></span>

*

## <span data-ttu-id="7c0cc-175">GERELATEERDE KOPPELINGEN</span><span class="sxs-lookup"><span data-stu-id="7c0cc-175">RELATED LINKS</span></span>

[<span data-ttu-id="7c0cc-176">Get-variabele</span><span class="sxs-lookup"><span data-stu-id="7c0cc-176">Get-Variable</span></span>](Get-Variable.md)

[<span data-ttu-id="7c0cc-177">Nieuwe variabele</span><span class="sxs-lookup"><span data-stu-id="7c0cc-177">New-Variable</span></span>](New-Variable.md)

[<span data-ttu-id="7c0cc-178">Remove-variabele</span><span class="sxs-lookup"><span data-stu-id="7c0cc-178">Remove-Variable</span></span>](Remove-Variable.md)

[<span data-ttu-id="7c0cc-179">Set-variabele</span><span class="sxs-lookup"><span data-stu-id="7c0cc-179">Set-Variable</span></span>](Set-Variable.md)
