---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 04/06/2021
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/set-variable?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Set-Variable
ms.openlocfilehash: 823e9b8376489464105940856b17f3e23cf048d3
ms.sourcegitcommit: 241071803915ab7d544576b5652ac23349a86369
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 04/07/2021
ms.locfileid: "107027189"
---
# <span data-ttu-id="8b483-103">Set-Variable</span><span class="sxs-lookup"><span data-stu-id="8b483-103">Set-Variable</span></span>

## <span data-ttu-id="8b483-104">Samen vatting</span><span class="sxs-lookup"><span data-stu-id="8b483-104">Synopsis</span></span>
<span data-ttu-id="8b483-105">Hiermee stelt u de waarde van een variabele.</span><span class="sxs-lookup"><span data-stu-id="8b483-105">Sets the value of a variable.</span></span> <span data-ttu-id="8b483-106">Hiermee maakt u de variabele als er een met de aangevraagde naam niet bestaat.</span><span class="sxs-lookup"><span data-stu-id="8b483-106">Creates the variable if one with the requested name does not exist.</span></span>

## <span data-ttu-id="8b483-107">Syntax</span><span class="sxs-lookup"><span data-stu-id="8b483-107">Syntax</span></span>

```
Set-Variable [-Name] <String[]> [[-Value] <Object>] [-Include <String[]>] [-Exclude <String[]>]
 [-Description <String>] [-Option <ScopedItemOptions>] [-Force] [-Visibility <SessionStateEntryVisibility>]
 [-PassThru] [-Scope <String>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="8b483-108">Description</span><span class="sxs-lookup"><span data-stu-id="8b483-108">Description</span></span>

<span data-ttu-id="8b483-109">De `Set-Variable` cmdlet wijst een waarde toe aan een opgegeven variabele of wijzigt de huidige waarde.</span><span class="sxs-lookup"><span data-stu-id="8b483-109">The `Set-Variable` cmdlet assigns a value to a specified variable or changes the current value.</span></span> <span data-ttu-id="8b483-110">Als de variabele niet bestaat, wordt deze door de cmdlet gemaakt.</span><span class="sxs-lookup"><span data-stu-id="8b483-110">If the variable does not exist, the cmdlet creates it.</span></span>

## <span data-ttu-id="8b483-111">Voorbeelden</span><span class="sxs-lookup"><span data-stu-id="8b483-111">Examples</span></span>

### <span data-ttu-id="8b483-112">Voor beeld 1: een variabele instellen en de waarde ervan ophalen</span><span class="sxs-lookup"><span data-stu-id="8b483-112">Example 1: Set a variable and get its value</span></span>

<span data-ttu-id="8b483-113">Met deze opdrachten wordt de waarde van de `$desc` variabele ingesteld op `A description` en wordt vervolgens de waarde van de variabele opgehaald.</span><span class="sxs-lookup"><span data-stu-id="8b483-113">These commands set the value of the `$desc` variable to `A description`, and then gets the value of the variable.</span></span>

```powershell
Set-Variable -Name "desc" -Value "A description"
Get-Variable -Name "desc"
```

```Output
Name                           Value
----                           -----
desc                           A description
```

### <span data-ttu-id="8b483-114">Voor beeld 2: een globale, alleen-lezen variabele instellen</span><span class="sxs-lookup"><span data-stu-id="8b483-114">Example 2: Set a global, read-only variable</span></span>

<span data-ttu-id="8b483-115">In dit voor beeld wordt een globale, alleen-lezen variabele gemaakt die alle processen op het systeem bevat. vervolgens worden alle eigenschappen van de variabele weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="8b483-115">This example creates a global, read-only variable that contains all processes on the system, and then it displays all properties of the variable.</span></span>

```powershell
Set-Variable -Name "processes" -Value (Get-Process) -Option Constant -Scope global -Description "All processes" -PassThru |
    Format-List -Property *
```

<span data-ttu-id="8b483-116">De opdracht gebruikt de `Set-Variable` cmdlet om de variabele te maken.</span><span class="sxs-lookup"><span data-stu-id="8b483-116">The command uses the `Set-Variable` cmdlet to create the variable.</span></span> <span data-ttu-id="8b483-117">De para meter **PassThru** wordt gebruikt om een object te maken dat de nieuwe variabele vertegenwoordigt, en de pijplijn operator ( `|` ) wordt gebruikt om het object door te geven aan de `Format-List` cmdlet.</span><span class="sxs-lookup"><span data-stu-id="8b483-117">It uses the **PassThru** parameter to create an object representing the new variable, and it uses the pipeline operator (`|`) to pass the object to the `Format-List` cmdlet.</span></span> <span data-ttu-id="8b483-118">De para meter **Property** van `Format-List` met de waarde all () wordt gebruikt `*` om alle eigenschappen van de zojuist gemaakte variabele weer te geven.</span><span class="sxs-lookup"><span data-stu-id="8b483-118">It uses the **Property** parameter of `Format-List` with a value of all (`*`) to display all properties of the newly created variable.</span></span>

<span data-ttu-id="8b483-119">De waarde, `(Get-Process)` , wordt tussen haakjes geplaatst om ervoor te zorgen dat deze wordt uitgevoerd voordat deze wordt opgeslagen in de variabele.</span><span class="sxs-lookup"><span data-stu-id="8b483-119">The value, `(Get-Process)`, is enclosed in parentheses to ensure that it is executed before being stored in the variable.</span></span> <span data-ttu-id="8b483-120">Anders bevat de variabele de woorden **Get-process**.</span><span class="sxs-lookup"><span data-stu-id="8b483-120">Otherwise, the variable contains the words "**Get-Process**".</span></span>

### <span data-ttu-id="8b483-121">Voor beeld 3: informatie over open bare en persoonlijke variabelen</span><span class="sxs-lookup"><span data-stu-id="8b483-121">Example 3: Understand public vs. private variables</span></span>

<span data-ttu-id="8b483-122">In dit voor beeld ziet u hoe u de zicht baarheid van een variabele wijzigt in `Private` .</span><span class="sxs-lookup"><span data-stu-id="8b483-122">This example shows how to change the visibility of a variable to `Private`.</span></span> <span data-ttu-id="8b483-123">Deze variabele kan worden gelezen en gewijzigd door scripts met de vereiste machtigingen, maar is niet zichtbaar voor de gebruiker.</span><span class="sxs-lookup"><span data-stu-id="8b483-123">This variable can be read and changed by scripts with the required permissions, but it is not visible to the user.</span></span>

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

<span data-ttu-id="8b483-124">Met deze opdracht wordt aangegeven hoe u de zicht baarheid van een variabele wijzigt in persoonlijk.</span><span class="sxs-lookup"><span data-stu-id="8b483-124">This command shows how to change the visibility of a variable to Private.</span></span> <span data-ttu-id="8b483-125">Deze variabele kan worden gelezen en gewijzigd door scripts met de vereiste machtigingen, maar is niet zichtbaar voor de gebruiker.</span><span class="sxs-lookup"><span data-stu-id="8b483-125">This variable can be read and changed by scripts with the required permissions, but it is not visible to the user.</span></span>

## <span data-ttu-id="8b483-126">Parameters</span><span class="sxs-lookup"><span data-stu-id="8b483-126">Parameters</span></span>

### <span data-ttu-id="8b483-127">-Beschrijving</span><span class="sxs-lookup"><span data-stu-id="8b483-127">-Description</span></span>

<span data-ttu-id="8b483-128">Hiermee geeft u de beschrijving van de variabele op.</span><span class="sxs-lookup"><span data-stu-id="8b483-128">Specifies the description of the variable.</span></span>

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

### <span data-ttu-id="8b483-129">-Uitsluiten</span><span class="sxs-lookup"><span data-stu-id="8b483-129">-Exclude</span></span>

<span data-ttu-id="8b483-130">Hiermee geeft u een matrix van items op die met deze cmdlet worden uitgesloten van de bewerking.</span><span class="sxs-lookup"><span data-stu-id="8b483-130">Specifies an array of items that this cmdlet excludes from the operation.</span></span> <span data-ttu-id="8b483-131">De waarde van deze para meter komt in aanmerking voor de para meter **Path** .</span><span class="sxs-lookup"><span data-stu-id="8b483-131">The value of this parameter qualifies the **Path** parameter.</span></span> <span data-ttu-id="8b483-132">Voer een element of patroon van een pad in, zoals `*.txt` .</span><span class="sxs-lookup"><span data-stu-id="8b483-132">Enter a path element or pattern, such as `*.txt`.</span></span>
<span data-ttu-id="8b483-133">Joker tekens zijn toegestaan.</span><span class="sxs-lookup"><span data-stu-id="8b483-133">Wildcards are permitted.</span></span>

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

### <span data-ttu-id="8b483-134">-Force</span><span class="sxs-lookup"><span data-stu-id="8b483-134">-Force</span></span>

<span data-ttu-id="8b483-135">Hiermee kunt u een variabele met dezelfde naam maken als een bestaande alleen-lezen variabele, of de waarde van een alleen-lezen variabele wijzigen.</span><span class="sxs-lookup"><span data-stu-id="8b483-135">Allows you to create a variable with the same name as an existing read-only variable, or to change the value of a read-only variable.</span></span>

<span data-ttu-id="8b483-136">Standaard kunt u een variabele overschrijven, tenzij de variabele een optie waarde van `ReadOnly` of heeft `Constant` .</span><span class="sxs-lookup"><span data-stu-id="8b483-136">By default, you can overwrite a variable, unless the variable has an option value of `ReadOnly` or `Constant`.</span></span> <span data-ttu-id="8b483-137">Zie de para meter **Option** voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="8b483-137">For more information, see the **Option** parameter.</span></span>

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

### <span data-ttu-id="8b483-138">-Include</span><span class="sxs-lookup"><span data-stu-id="8b483-138">-Include</span></span>

<span data-ttu-id="8b483-139">Hiermee geeft u een matrix van items op die met deze cmdlet worden opgenomen in de bewerking.</span><span class="sxs-lookup"><span data-stu-id="8b483-139">Specifies an array of items that this cmdlet includes in the operation.</span></span> <span data-ttu-id="8b483-140">De waarde van deze para meter komt in aanmerking voor de para meter **name** .</span><span class="sxs-lookup"><span data-stu-id="8b483-140">The value of this parameter qualifies the **Name** parameter.</span></span> <span data-ttu-id="8b483-141">Voer een naam of naam patroon in, bijvoorbeeld `c*` .</span><span class="sxs-lookup"><span data-stu-id="8b483-141">Enter a name or name pattern, such as `c*`.</span></span> <span data-ttu-id="8b483-142">Joker tekens zijn toegestaan.</span><span class="sxs-lookup"><span data-stu-id="8b483-142">Wildcards are permitted.</span></span>

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

### <span data-ttu-id="8b483-143">-Name</span><span class="sxs-lookup"><span data-stu-id="8b483-143">-Name</span></span>

<span data-ttu-id="8b483-144">Hiermee geeft u de naam van de variabele.</span><span class="sxs-lookup"><span data-stu-id="8b483-144">Specifies the variable name.</span></span>

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

### <span data-ttu-id="8b483-145">-Optie</span><span class="sxs-lookup"><span data-stu-id="8b483-145">-Option</span></span>

<span data-ttu-id="8b483-146">Hiermee geeft u de waarde van de eigenschap **Options** van de variabele.</span><span class="sxs-lookup"><span data-stu-id="8b483-146">Specifies the value of the **Options** property of the variable.</span></span>

<span data-ttu-id="8b483-147">Geldige waarden zijn:</span><span class="sxs-lookup"><span data-stu-id="8b483-147">Valid values are:</span></span>

- <span data-ttu-id="8b483-148">`None`: Er worden geen opties ingesteld.</span><span class="sxs-lookup"><span data-stu-id="8b483-148">`None`: Sets no options.</span></span> <span data-ttu-id="8b483-149">( `None` is de standaard instelling.)</span><span class="sxs-lookup"><span data-stu-id="8b483-149">(`None` is the default.)</span></span>
- <span data-ttu-id="8b483-150">`ReadOnly`: Kan worden verwijderd.</span><span class="sxs-lookup"><span data-stu-id="8b483-150">`ReadOnly`: Can be deleted.</span></span> <span data-ttu-id="8b483-151">Kan niet worden gewijzigd, behalve door gebruik te maken van de para meter Forces.</span><span class="sxs-lookup"><span data-stu-id="8b483-151">Cannot be changed, except by using the Force parameter.</span></span>
- <span data-ttu-id="8b483-152">`Constant`: Kan niet worden verwijderd of gewijzigd.</span><span class="sxs-lookup"><span data-stu-id="8b483-152">`Constant`: Cannot be deleted or changed.</span></span> <span data-ttu-id="8b483-153">`Constant` is alleen geldig wanneer u een variabele maakt.</span><span class="sxs-lookup"><span data-stu-id="8b483-153">`Constant` is valid only when you are creating a variable.</span></span> <span data-ttu-id="8b483-154">U kunt de opties van een bestaande variabele niet wijzigen in `Constant` .</span><span class="sxs-lookup"><span data-stu-id="8b483-154">You cannot change the options of an existing variable to `Constant`.</span></span>
- <span data-ttu-id="8b483-155">`Private`: De variabele is alleen beschikbaar in het huidige bereik.</span><span class="sxs-lookup"><span data-stu-id="8b483-155">`Private`: The variable is available only in the current scope.</span></span>
- <span data-ttu-id="8b483-156">`AllScope`: De variabele wordt gekopieerd naar een nieuwe scope die wordt gemaakt.</span><span class="sxs-lookup"><span data-stu-id="8b483-156">`AllScope`: The variable is copied to any new scopes that are created.</span></span>

<span data-ttu-id="8b483-157">Deze waarden worden gedefinieerd als inventarisatie op basis van een vlag.</span><span class="sxs-lookup"><span data-stu-id="8b483-157">These values are defined as a flag-based enumeration.</span></span> <span data-ttu-id="8b483-158">U kunt meerdere waarden combi neren om meerdere vlaggen in te stellen met behulp van deze para meter.</span><span class="sxs-lookup"><span data-stu-id="8b483-158">You can combine multiple values together to set multiple flags using this parameter.</span></span> <span data-ttu-id="8b483-159">De waarden kunnen worden door gegeven aan de para meter **Option** als een matrix met waarden of als een door komma's gescheiden teken reeks van die waarden.</span><span class="sxs-lookup"><span data-stu-id="8b483-159">The values can be passed to the **Option** parameter as an array of values or as a comma-separated string of those values.</span></span> <span data-ttu-id="8b483-160">Met de cmdlet worden de waarden gecombineerd met behulp van een binaire waarde of bewerking.</span><span class="sxs-lookup"><span data-stu-id="8b483-160">The cmdlet will combine the values using a binary-OR operation.</span></span> <span data-ttu-id="8b483-161">Het door geven van waarden als een matrix is de eenvoudigste optie. Daarnaast kunt u met behulp van de waarden van het tabblad volt ooien.</span><span class="sxs-lookup"><span data-stu-id="8b483-161">Passing values as an array is the simplest option and also allows you to use tab-completion on the values.</span></span>

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

### <span data-ttu-id="8b483-162">-PassThru</span><span class="sxs-lookup"><span data-stu-id="8b483-162">-PassThru</span></span>

<span data-ttu-id="8b483-163">Retourneert een object dat de nieuwe variabele vertegenwoordigt.</span><span class="sxs-lookup"><span data-stu-id="8b483-163">Returns an object representing the new variable.</span></span> <span data-ttu-id="8b483-164">Deze cmdlet genereert standaard geen uitvoer.</span><span class="sxs-lookup"><span data-stu-id="8b483-164">By default, this cmdlet does not generate any output.</span></span>

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

### <span data-ttu-id="8b483-165">-Bereik</span><span class="sxs-lookup"><span data-stu-id="8b483-165">-Scope</span></span>

<span data-ttu-id="8b483-166">Hiermee wordt het bereik van de variabele opgegeven. De acceptabele waarden voor deze para meter zijn:</span><span class="sxs-lookup"><span data-stu-id="8b483-166">Specifies the scope of the variable.The acceptable values for this parameter are:</span></span>

- `Global`
- `Local`
- `Script`
- `Private`
- <span data-ttu-id="8b483-167">Een getal dat relatief is ten opzichte van het huidige bereik (0 tot en met het aantal bereiken, waarbij 0 het huidige bereik is en 1 de bovenliggende scope).</span><span class="sxs-lookup"><span data-stu-id="8b483-167">A number relative to the current scope (0 through the number of scopes, where 0 is the current scope and 1 is its parent).</span></span>

<span data-ttu-id="8b483-168">`Local` is de standaardwaarde.</span><span class="sxs-lookup"><span data-stu-id="8b483-168">`Local` is the default.</span></span>

<span data-ttu-id="8b483-169">Zie [about_Scopes](../Microsoft.PowerShell.Core/About/about_scopes.md)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="8b483-169">For more information, see [about_Scopes](../Microsoft.PowerShell.Core/About/about_scopes.md).</span></span>

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

### <span data-ttu-id="8b483-170">-Waarde</span><span class="sxs-lookup"><span data-stu-id="8b483-170">-Value</span></span>

<span data-ttu-id="8b483-171">Hiermee geeft u de waarde van de variabele.</span><span class="sxs-lookup"><span data-stu-id="8b483-171">Specifies the value of the variable.</span></span>

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

### <span data-ttu-id="8b483-172">-Zicht baarheid</span><span class="sxs-lookup"><span data-stu-id="8b483-172">-Visibility</span></span>

<span data-ttu-id="8b483-173">Hiermee wordt bepaald of de variabele zichtbaar is buiten de sessie waarin deze is gemaakt.</span><span class="sxs-lookup"><span data-stu-id="8b483-173">Determines whether the variable is visible outside of the session in which it was created.</span></span> <span data-ttu-id="8b483-174">Deze para meter is ontworpen voor gebruik in scripts en opdrachten die aan andere gebruikers worden geleverd.</span><span class="sxs-lookup"><span data-stu-id="8b483-174">This parameter is designed for use in scripts and commands that will be delivered to other users.</span></span>

<span data-ttu-id="8b483-175">Geldige waarden zijn:</span><span class="sxs-lookup"><span data-stu-id="8b483-175">Valid values are:</span></span>

- <span data-ttu-id="8b483-176">`Public`: De variabele is zichtbaar.</span><span class="sxs-lookup"><span data-stu-id="8b483-176">`Public`:  The variable is visible.</span></span> <span data-ttu-id="8b483-177">( `Public` is de standaard instelling.)</span><span class="sxs-lookup"><span data-stu-id="8b483-177">(`Public` is the default.)</span></span>
- <span data-ttu-id="8b483-178">`Private`: De variabele is niet zichtbaar.</span><span class="sxs-lookup"><span data-stu-id="8b483-178">`Private`: The variable is not visible.</span></span>

<span data-ttu-id="8b483-179">Wanneer een variabele privé is, wordt deze niet weer gegeven in lijst met variabelen, zoals die worden geretourneerd door `Get-Variable` , of in de weer gaven van de **variabele:** station.</span><span class="sxs-lookup"><span data-stu-id="8b483-179">When a variable is private, it does not appear in lists of variables, such as those returned by `Get-Variable`, or in displays of the **Variable:** drive.</span></span> <span data-ttu-id="8b483-180">Opdrachten om de waarde van een persoonlijke variabele te lezen of te wijzigen, retour neren een fout.</span><span class="sxs-lookup"><span data-stu-id="8b483-180">Commands to read or change the value of a private variable return an error.</span></span> <span data-ttu-id="8b483-181">De gebruiker kan echter opdrachten uitvoeren die een persoonlijke variabele gebruiken als de opdrachten zijn geschreven in de sessie waarin de variabele is gedefinieerd.</span><span class="sxs-lookup"><span data-stu-id="8b483-181">However, the user can run commands that use a private variable if the commands were written in the session in which the variable was defined.</span></span>

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

### <span data-ttu-id="8b483-182">-Confirm</span><span class="sxs-lookup"><span data-stu-id="8b483-182">-Confirm</span></span>

<span data-ttu-id="8b483-183">Hiermee wordt u gevraagd om bevestiging voordat u de cmdlet uitvoert.</span><span class="sxs-lookup"><span data-stu-id="8b483-183">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="8b483-184">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="8b483-184">-WhatIf</span></span>

<span data-ttu-id="8b483-185">Hiermee wordt weergegeven wat er zou gebeuren als u de cmdlet uitvoert.</span><span class="sxs-lookup"><span data-stu-id="8b483-185">Shows what would happen if the cmdlet runs.</span></span> <span data-ttu-id="8b483-186">De cmdlet wordt niet uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="8b483-186">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="8b483-187">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="8b483-187">CommonParameters</span></span>

<span data-ttu-id="8b483-188">Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="8b483-188">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="8b483-189">Zie [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="8b483-189">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="8b483-190">Invoerwaarden</span><span class="sxs-lookup"><span data-stu-id="8b483-190">Inputs</span></span>

### <span data-ttu-id="8b483-191">System. object</span><span class="sxs-lookup"><span data-stu-id="8b483-191">System.Object</span></span>

<span data-ttu-id="8b483-192">U kunt een object dat de waarde van de variabele vertegenwoordigt, door sluizen naar `Set-Variable` .</span><span class="sxs-lookup"><span data-stu-id="8b483-192">You can pipe an object that represents the value of the variable to `Set-Variable`.</span></span>

## <span data-ttu-id="8b483-193">Uitvoerwaarden</span><span class="sxs-lookup"><span data-stu-id="8b483-193">Outputs</span></span>

### <span data-ttu-id="8b483-194">Geen of System. Management. Automation. PSVariable</span><span class="sxs-lookup"><span data-stu-id="8b483-194">None or System.Management.Automation.PSVariable</span></span>

<span data-ttu-id="8b483-195">Wanneer u de para meter **PassThru** gebruikt, `Set-Variable` genereert een **System. Management. Automation. PSVariable** -object dat de nieuwe of gewijzigde variabele vertegenwoordigt.</span><span class="sxs-lookup"><span data-stu-id="8b483-195">When you use the **PassThru** parameter, `Set-Variable` generates a **System.Management.Automation.PSVariable** object representing the new or changed variable.</span></span>
<span data-ttu-id="8b483-196">Anders wordt met deze cmdlet geen uitvoer gegenereerd.</span><span class="sxs-lookup"><span data-stu-id="8b483-196">Otherwise, this cmdlet does not generate any output.</span></span>

## <span data-ttu-id="8b483-197">Notities</span><span class="sxs-lookup"><span data-stu-id="8b483-197">Notes</span></span>

## <span data-ttu-id="8b483-198">Verwante koppelingen</span><span class="sxs-lookup"><span data-stu-id="8b483-198">Related Links</span></span>

[<span data-ttu-id="8b483-199">Clear-variabele</span><span class="sxs-lookup"><span data-stu-id="8b483-199">Clear-Variable</span></span>](Clear-Variable.md)

[<span data-ttu-id="8b483-200">Get-variabele</span><span class="sxs-lookup"><span data-stu-id="8b483-200">Get-Variable</span></span>](Get-Variable.md)

[<span data-ttu-id="8b483-201">Nieuwe variabele</span><span class="sxs-lookup"><span data-stu-id="8b483-201">New-Variable</span></span>](New-Variable.md)

[<span data-ttu-id="8b483-202">Remove-variabele</span><span class="sxs-lookup"><span data-stu-id="8b483-202">Remove-Variable</span></span>](Remove-Variable.md)
