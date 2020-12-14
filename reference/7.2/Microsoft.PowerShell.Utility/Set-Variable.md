---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/set-variable?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Set-Variable
ms.openlocfilehash: 573bb0054b60e8c17b79da72ebc712c6ef5575a5
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 11/17/2020
ms.locfileid: "94706150"
---
# <span data-ttu-id="41878-102">Set-Variable</span><span class="sxs-lookup"><span data-stu-id="41878-102">Set-Variable</span></span>

## <span data-ttu-id="41878-103">SAMENVATTING</span><span class="sxs-lookup"><span data-stu-id="41878-103">SYNOPSIS</span></span>
<span data-ttu-id="41878-104">Hiermee stelt u de waarde van een variabele.</span><span class="sxs-lookup"><span data-stu-id="41878-104">Sets the value of a variable.</span></span> <span data-ttu-id="41878-105">Hiermee maakt u de variabele als er een met de aangevraagde naam niet bestaat.</span><span class="sxs-lookup"><span data-stu-id="41878-105">Creates the variable if one with the requested name does not exist.</span></span>

## <span data-ttu-id="41878-106">SYNTAXIS</span><span class="sxs-lookup"><span data-stu-id="41878-106">SYNTAX</span></span>

```
Set-Variable [-Name] <String[]> [[-Value] <Object>] [-Include <String[]>] [-Exclude <String[]>]
 [-Description <String>] [-Option <ScopedItemOptions>] [-Force] [-Visibility <SessionStateEntryVisibility>]
 [-PassThru] [-Scope <String>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="41878-107">BESCHRIJVING</span><span class="sxs-lookup"><span data-stu-id="41878-107">DESCRIPTION</span></span>

<span data-ttu-id="41878-108">De `Set-Variable` cmdlet wijst een waarde toe aan een opgegeven variabele of wijzigt de huidige waarde.</span><span class="sxs-lookup"><span data-stu-id="41878-108">The `Set-Variable` cmdlet assigns a value to a specified variable or changes the current value.</span></span> <span data-ttu-id="41878-109">Als de variabele niet bestaat, wordt deze door de cmdlet gemaakt.</span><span class="sxs-lookup"><span data-stu-id="41878-109">If the variable does not exist, the cmdlet creates it.</span></span>

## <span data-ttu-id="41878-110">VOORBEELDEN</span><span class="sxs-lookup"><span data-stu-id="41878-110">EXAMPLES</span></span>

### <span data-ttu-id="41878-111">Voor beeld 1: een variabele instellen en de waarde ervan ophalen</span><span class="sxs-lookup"><span data-stu-id="41878-111">Example 1: Set a variable and get its value</span></span>

<span data-ttu-id="41878-112">Met deze opdrachten wordt de waarde van de `$desc` variabele ingesteld op `A description` en wordt vervolgens de waarde van de variabele opgehaald.</span><span class="sxs-lookup"><span data-stu-id="41878-112">These commands set the value of the `$desc` variable to `A description`, and then gets the value of the variable.</span></span>

```powershell
Set-Variable -Name "desc" -Value "A description"
Get-Variable -Name "desc"
```

```Output
Name                           Value
----                           -----
desc                           A description
```

### <span data-ttu-id="41878-113">Voor beeld 2: een globale, alleen-lezen variabele instellen</span><span class="sxs-lookup"><span data-stu-id="41878-113">Example 2: Set a global, read-only variable</span></span>

<span data-ttu-id="41878-114">In dit voor beeld wordt een globale, alleen-lezen variabele gemaakt die alle processen op het systeem bevat. vervolgens worden alle eigenschappen van de variabele weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="41878-114">This example creates a global, read-only variable that contains all processes on the system, and then it displays all properties of the variable.</span></span>

```powershell
Set-Variable -Name "processes" -Value (Get-Process) -Option constant -Scope global -Description "All processes" -PassThru |
    Format-List -Property *
```

<span data-ttu-id="41878-115">De opdracht gebruikt de `Set-Variable` cmdlet om de variabele te maken.</span><span class="sxs-lookup"><span data-stu-id="41878-115">The command uses the `Set-Variable` cmdlet to create the variable.</span></span> <span data-ttu-id="41878-116">De para meter **PassThru** wordt gebruikt om een object te maken dat de nieuwe variabele vertegenwoordigt, en de pijplijn operator ( `|` ) wordt gebruikt om het object door te geven aan de `Format-List` cmdlet.</span><span class="sxs-lookup"><span data-stu-id="41878-116">It uses the **PassThru** parameter to create an object representing the new variable, and it uses the pipeline operator (`|`) to pass the object to the `Format-List` cmdlet.</span></span> <span data-ttu-id="41878-117">De para meter **Property** van `Format-List` met de waarde all () wordt gebruikt `*` om alle eigenschappen van de zojuist gemaakte variabele weer te geven.</span><span class="sxs-lookup"><span data-stu-id="41878-117">It uses the **Property** parameter of `Format-List` with a value of all (`*`) to display all properties of the newly created variable.</span></span>

<span data-ttu-id="41878-118">De waarde, `(Get-Process)` , wordt tussen haakjes geplaatst om ervoor te zorgen dat deze wordt uitgevoerd voordat deze wordt opgeslagen in de variabele.</span><span class="sxs-lookup"><span data-stu-id="41878-118">The value, `(Get-Process)`, is enclosed in parentheses to ensure that it is executed before being stored in the variable.</span></span> <span data-ttu-id="41878-119">Anders bevat de variabele de woorden **Get-process**.</span><span class="sxs-lookup"><span data-stu-id="41878-119">Otherwise, the variable contains the words "**Get-Process**".</span></span>

### <span data-ttu-id="41878-120">Voor beeld 3: informatie over open bare en persoonlijke variabelen</span><span class="sxs-lookup"><span data-stu-id="41878-120">Example 3: Understand public vs. private variables</span></span>

<span data-ttu-id="41878-121">In dit voor beeld ziet u hoe u de zicht baarheid van een variabele wijzigt in `Private` .</span><span class="sxs-lookup"><span data-stu-id="41878-121">This example shows how to change the visibility of a variable to `Private`.</span></span> <span data-ttu-id="41878-122">Deze variabele kan worden gelezen en gewijzigd door scripts met de vereiste machtigingen, maar is niet zichtbaar voor de gebruiker.</span><span class="sxs-lookup"><span data-stu-id="41878-122">This variable can be read and changed by scripts with the required permissions, but it is not visible to the user.</span></span>

```
PS C:\> New-Variable -Name "counter" -Visibility Public -Value 26
PS C:\> $Counter
26

PS C:\> Get-Variable c*

Name                  Value
----                  -----
Culture               en-US
ConsoleFileName
ConfirmPreference     High
CommandLineParameters {}
Counter               26

PS C:\> Set-Variable -Name "counter" -Visibility Private
PS C:\> Get-Variable c*

Name                  Value
----                  -----
Culture               en-US
ConsoleFileName
ConfirmPreference     High
CommandLineParameters {}

PS C:\> $counter
"Cannot access the variable '$counter' because it is a private variable"

PS C:\> .\use-counter.ps1
#Commands completed successfully.
```

<span data-ttu-id="41878-123">Met deze opdracht wordt aangegeven hoe u de zicht baarheid van een variabele wijzigt in persoonlijk.</span><span class="sxs-lookup"><span data-stu-id="41878-123">This command shows how to change the visibility of a variable to Private.</span></span> <span data-ttu-id="41878-124">Deze variabele kan worden gelezen en gewijzigd door scripts met de vereiste machtigingen, maar is niet zichtbaar voor de gebruiker.</span><span class="sxs-lookup"><span data-stu-id="41878-124">This variable can be read and changed by scripts with the required permissions, but it is not visible to the user.</span></span>

## <span data-ttu-id="41878-125">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="41878-125">PARAMETERS</span></span>

### <span data-ttu-id="41878-126">-Beschrijving</span><span class="sxs-lookup"><span data-stu-id="41878-126">-Description</span></span>

<span data-ttu-id="41878-127">Hiermee geeft u de beschrijving van de variabele op.</span><span class="sxs-lookup"><span data-stu-id="41878-127">Specifies the description of the variable.</span></span>

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

### <span data-ttu-id="41878-128">-Uitsluiten</span><span class="sxs-lookup"><span data-stu-id="41878-128">-Exclude</span></span>

<span data-ttu-id="41878-129">Hiermee geeft u een matrix van items op die met deze cmdlet worden uitgesloten van de bewerking.</span><span class="sxs-lookup"><span data-stu-id="41878-129">Specifies an array of items that this cmdlet excludes from the operation.</span></span> <span data-ttu-id="41878-130">De waarde van deze para meter komt in aanmerking voor de para meter **Path** .</span><span class="sxs-lookup"><span data-stu-id="41878-130">The value of this parameter qualifies the **Path** parameter.</span></span> <span data-ttu-id="41878-131">Voer een element of patroon van een pad in, zoals `*.txt` .</span><span class="sxs-lookup"><span data-stu-id="41878-131">Enter a path element or pattern, such as `*.txt`.</span></span>
<span data-ttu-id="41878-132">Joker tekens zijn toegestaan.</span><span class="sxs-lookup"><span data-stu-id="41878-132">Wildcards are permitted.</span></span>

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

### <span data-ttu-id="41878-133">-Force</span><span class="sxs-lookup"><span data-stu-id="41878-133">-Force</span></span>

<span data-ttu-id="41878-134">Hiermee kunt u een variabele met dezelfde naam maken als een bestaande alleen-lezen variabele, of de waarde van een alleen-lezen variabele wijzigen.</span><span class="sxs-lookup"><span data-stu-id="41878-134">Allows you to create a variable with the same name as an existing read-only variable, or to change the value of a read-only variable.</span></span>

<span data-ttu-id="41878-135">Standaard kunt u een variabele overschrijven, tenzij de variabele een optie waarde van `ReadOnly` of heeft `Constant` .</span><span class="sxs-lookup"><span data-stu-id="41878-135">By default, you can overwrite a variable, unless the variable has an option value of `ReadOnly` or `Constant`.</span></span> <span data-ttu-id="41878-136">Zie de para meter **Option** voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="41878-136">For more information, see the **Option** parameter.</span></span>

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

### <span data-ttu-id="41878-137">-Include</span><span class="sxs-lookup"><span data-stu-id="41878-137">-Include</span></span>

<span data-ttu-id="41878-138">Hiermee geeft u een matrix van items op die met deze cmdlet worden opgenomen in de bewerking.</span><span class="sxs-lookup"><span data-stu-id="41878-138">Specifies an array of items that this cmdlet includes in the operation.</span></span> <span data-ttu-id="41878-139">De waarde van deze para meter komt in aanmerking voor de para meter **name** .</span><span class="sxs-lookup"><span data-stu-id="41878-139">The value of this parameter qualifies the **Name** parameter.</span></span> <span data-ttu-id="41878-140">Voer een naam of naam patroon in, bijvoorbeeld `c*` .</span><span class="sxs-lookup"><span data-stu-id="41878-140">Enter a name or name pattern, such as `c*`.</span></span> <span data-ttu-id="41878-141">Joker tekens zijn toegestaan.</span><span class="sxs-lookup"><span data-stu-id="41878-141">Wildcards are permitted.</span></span>

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

### <span data-ttu-id="41878-142">-Name</span><span class="sxs-lookup"><span data-stu-id="41878-142">-Name</span></span>

<span data-ttu-id="41878-143">Hiermee geeft u de naam van de variabele.</span><span class="sxs-lookup"><span data-stu-id="41878-143">Specifies the variable name.</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="41878-144">-Optie</span><span class="sxs-lookup"><span data-stu-id="41878-144">-Option</span></span>

<span data-ttu-id="41878-145">Hiermee geeft u de waarde van de eigenschap **Options** van de variabele.</span><span class="sxs-lookup"><span data-stu-id="41878-145">Specifies the value of the **Options** property of the variable.</span></span>

<span data-ttu-id="41878-146">Geldige waarden zijn:</span><span class="sxs-lookup"><span data-stu-id="41878-146">Valid values are:</span></span>

- <span data-ttu-id="41878-147">`None`: Er worden geen opties ingesteld.</span><span class="sxs-lookup"><span data-stu-id="41878-147">`None`: Sets no options.</span></span> <span data-ttu-id="41878-148">(' Geen ' is de standaard instelling.)</span><span class="sxs-lookup"><span data-stu-id="41878-148">("None" is the default.)</span></span>
- <span data-ttu-id="41878-149">`ReadOnly`: Kan worden verwijderd.</span><span class="sxs-lookup"><span data-stu-id="41878-149">`ReadOnly`: Can be deleted.</span></span> <span data-ttu-id="41878-150">Kan niet worden gewijzigd, behalve door gebruik te maken van de para meter Forces.</span><span class="sxs-lookup"><span data-stu-id="41878-150">Cannot be changed, except by using the Force parameter.</span></span>
- <span data-ttu-id="41878-151">`Constant`: Kan niet worden verwijderd of gewijzigd.</span><span class="sxs-lookup"><span data-stu-id="41878-151">`Constant`: Cannot be deleted or changed.</span></span> <span data-ttu-id="41878-152">`Constant` is alleen geldig wanneer u een variabele maakt.</span><span class="sxs-lookup"><span data-stu-id="41878-152">`Constant` is valid only when you are creating a variable.</span></span> <span data-ttu-id="41878-153">U kunt de opties van een bestaande variabele niet wijzigen in `Constant` .</span><span class="sxs-lookup"><span data-stu-id="41878-153">You cannot change the options of an existing variable to `Constant`.</span></span>
- <span data-ttu-id="41878-154">`Private`: De variabele is alleen beschikbaar in het huidige bereik.</span><span class="sxs-lookup"><span data-stu-id="41878-154">`Private`: The variable is available only in the current scope.</span></span>
- <span data-ttu-id="41878-155">`AllScope`: De variabele wordt gekopieerd naar een nieuwe scope die wordt gemaakt.</span><span class="sxs-lookup"><span data-stu-id="41878-155">`AllScope`: The variable is copied to any new scopes that are created.</span></span>

```yaml
Type: System.Management.Automation.ScopedItemOptions
Parameter Sets: (All)
Aliases:
Accepted values: None, ReadOnly, Constant, Private, AllScope, Unspecified

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="41878-156">-PassThru</span><span class="sxs-lookup"><span data-stu-id="41878-156">-PassThru</span></span>

<span data-ttu-id="41878-157">Retourneert een object dat de nieuwe variabele vertegenwoordigt.</span><span class="sxs-lookup"><span data-stu-id="41878-157">Returns an object representing the new variable.</span></span> <span data-ttu-id="41878-158">Deze cmdlet genereert standaard geen uitvoer.</span><span class="sxs-lookup"><span data-stu-id="41878-158">By default, this cmdlet does not generate any output.</span></span>

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

### <span data-ttu-id="41878-159">-Bereik</span><span class="sxs-lookup"><span data-stu-id="41878-159">-Scope</span></span>

<span data-ttu-id="41878-160">Hiermee wordt het bereik van de variabele opgegeven. De acceptabele waarden voor deze para meter zijn:</span><span class="sxs-lookup"><span data-stu-id="41878-160">Specifies the scope of the variable.The acceptable values for this parameter are:</span></span>

- <span data-ttu-id="41878-161">Globaal</span><span class="sxs-lookup"><span data-stu-id="41878-161">Global</span></span>
- <span data-ttu-id="41878-162">Lokaal</span><span class="sxs-lookup"><span data-stu-id="41878-162">Local</span></span>
- <span data-ttu-id="41878-163">Script</span><span class="sxs-lookup"><span data-stu-id="41878-163">Script</span></span>
- <span data-ttu-id="41878-164">Privé</span><span class="sxs-lookup"><span data-stu-id="41878-164">Private</span></span>
- <span data-ttu-id="41878-165">Een getal dat relatief is ten opzichte van het huidige bereik (0 tot en met het aantal bereiken, waarbij 0 het huidige bereik is en 1 de bovenliggende scope).</span><span class="sxs-lookup"><span data-stu-id="41878-165">A number relative to the current scope (0 through the number of scopes, where 0 is the current scope and 1 is its parent).</span></span>

<span data-ttu-id="41878-166">Local is de standaard instelling.</span><span class="sxs-lookup"><span data-stu-id="41878-166">Local is the default.</span></span>

<span data-ttu-id="41878-167">Zie [about_Scopes](../Microsoft.PowerShell.Core/About/about_scopes.md)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="41878-167">For more information, see [about_Scopes](../Microsoft.PowerShell.Core/About/about_scopes.md).</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: Local
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="41878-168">-Waarde</span><span class="sxs-lookup"><span data-stu-id="41878-168">-Value</span></span>

<span data-ttu-id="41878-169">Hiermee geeft u de waarde van de variabele.</span><span class="sxs-lookup"><span data-stu-id="41878-169">Specifies the value of the variable.</span></span>

```yaml
Type: System.Object
Parameter Sets: (All)
Aliases:

Required: False
Position: 1
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="41878-170">-Zicht baarheid</span><span class="sxs-lookup"><span data-stu-id="41878-170">-Visibility</span></span>

<span data-ttu-id="41878-171">Hiermee wordt bepaald of de variabele zichtbaar is buiten de sessie waarin deze is gemaakt.</span><span class="sxs-lookup"><span data-stu-id="41878-171">Determines whether the variable is visible outside of the session in which it was created.</span></span> <span data-ttu-id="41878-172">Deze para meter is ontworpen voor gebruik in scripts en opdrachten die aan andere gebruikers worden geleverd.</span><span class="sxs-lookup"><span data-stu-id="41878-172">This parameter is designed for use in scripts and commands that will be delivered to other users.</span></span>

<span data-ttu-id="41878-173">Geldige waarden zijn:</span><span class="sxs-lookup"><span data-stu-id="41878-173">Valid values are:</span></span>

- <span data-ttu-id="41878-174">Openbaar: de variabele is zichtbaar.</span><span class="sxs-lookup"><span data-stu-id="41878-174">Public:  The variable is visible.</span></span> <span data-ttu-id="41878-175">(' Openbaar ' is de standaard instelling.)</span><span class="sxs-lookup"><span data-stu-id="41878-175">("Public" is the default.)</span></span>
- <span data-ttu-id="41878-176">Persoonlijk: de variabele is niet zichtbaar.</span><span class="sxs-lookup"><span data-stu-id="41878-176">Private: The variable is not visible.</span></span>

<span data-ttu-id="41878-177">Wanneer een variabele privé is, wordt deze niet weer gegeven in lijst met variabelen, zoals die worden geretourneerd door `Get-Variable` , of in de weer gaven van de **variabele:** station.</span><span class="sxs-lookup"><span data-stu-id="41878-177">When a variable is private, it does not appear in lists of variables, such as those returned by `Get-Variable`, or in displays of the **Variable:** drive.</span></span> <span data-ttu-id="41878-178">Opdrachten om de waarde van een persoonlijke variabele te lezen of te wijzigen, retour neren een fout.</span><span class="sxs-lookup"><span data-stu-id="41878-178">Commands to read or change the value of a private variable return an error.</span></span> <span data-ttu-id="41878-179">De gebruiker kan echter opdrachten uitvoeren die een persoonlijke variabele gebruiken als de opdrachten zijn geschreven in de sessie waarin de variabele is gedefinieerd.</span><span class="sxs-lookup"><span data-stu-id="41878-179">However, the user can run commands that use a private variable if the commands were written in the session in which the variable was defined.</span></span>

```yaml
Type: System.Management.Automation.SessionStateEntryVisibility
Parameter Sets: (All)
Aliases:
Accepted values: Public, Private

Required: False
Position: Named
Default value: Public
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="41878-180">-Confirm</span><span class="sxs-lookup"><span data-stu-id="41878-180">-Confirm</span></span>

<span data-ttu-id="41878-181">Hiermee wordt u gevraagd om bevestiging voordat u de cmdlet uitvoert.</span><span class="sxs-lookup"><span data-stu-id="41878-181">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="41878-182">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="41878-182">-WhatIf</span></span>

<span data-ttu-id="41878-183">Hiermee wordt weergegeven wat er zou gebeuren als u de cmdlet uitvoert.</span><span class="sxs-lookup"><span data-stu-id="41878-183">Shows what would happen if the cmdlet runs.</span></span> <span data-ttu-id="41878-184">De cmdlet wordt niet uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="41878-184">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="41878-185">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="41878-185">CommonParameters</span></span>

<span data-ttu-id="41878-186">Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="41878-186">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="41878-187">Zie [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="41878-187">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="41878-188">INVOER</span><span class="sxs-lookup"><span data-stu-id="41878-188">INPUTS</span></span>

### <span data-ttu-id="41878-189">System. object</span><span class="sxs-lookup"><span data-stu-id="41878-189">System.Object</span></span>

<span data-ttu-id="41878-190">U kunt een object dat de waarde van de variabele vertegenwoordigt, door sluizen naar `Set-Variable` .</span><span class="sxs-lookup"><span data-stu-id="41878-190">You can pipe an object that represents the value of the variable to `Set-Variable`.</span></span>

## <span data-ttu-id="41878-191">UITVOER</span><span class="sxs-lookup"><span data-stu-id="41878-191">OUTPUTS</span></span>

### <span data-ttu-id="41878-192">Geen of System. Management. Automation. PSVariable</span><span class="sxs-lookup"><span data-stu-id="41878-192">None or System.Management.Automation.PSVariable</span></span>

<span data-ttu-id="41878-193">Wanneer u de para meter **PassThru** gebruikt, `Set-Variable` genereert een **System. Management. Automation. PSVariable** -object dat de nieuwe of gewijzigde variabele vertegenwoordigt.</span><span class="sxs-lookup"><span data-stu-id="41878-193">When you use the **PassThru** parameter, `Set-Variable` generates a **System.Management.Automation.PSVariable** object representing the new or changed variable.</span></span>
<span data-ttu-id="41878-194">Anders wordt met deze cmdlet geen uitvoer gegenereerd.</span><span class="sxs-lookup"><span data-stu-id="41878-194">Otherwise, this cmdlet does not generate any output.</span></span>

## <span data-ttu-id="41878-195">OPMERKINGEN</span><span class="sxs-lookup"><span data-stu-id="41878-195">NOTES</span></span>

## <span data-ttu-id="41878-196">GERELATEERDE KOPPELINGEN</span><span class="sxs-lookup"><span data-stu-id="41878-196">RELATED LINKS</span></span>

[<span data-ttu-id="41878-197">Clear-variabele</span><span class="sxs-lookup"><span data-stu-id="41878-197">Clear-Variable</span></span>](Clear-Variable.md)

[<span data-ttu-id="41878-198">Get-variabele</span><span class="sxs-lookup"><span data-stu-id="41878-198">Get-Variable</span></span>](Get-Variable.md)

[<span data-ttu-id="41878-199">Nieuwe variabele</span><span class="sxs-lookup"><span data-stu-id="41878-199">New-Variable</span></span>](New-Variable.md)

[<span data-ttu-id="41878-200">Remove-variabele</span><span class="sxs-lookup"><span data-stu-id="41878-200">Remove-Variable</span></span>](Remove-Variable.md)
