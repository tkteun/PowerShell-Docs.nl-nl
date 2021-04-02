---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 03/30/2021
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/new-variable?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: New-Variable
ms.openlocfilehash: 71bb70dac3436c5293b2a34ce52e54e751786a48
ms.sourcegitcommit: 4d6ed6f7d747a9bbb3fcfcf6c981c5aa8a973a08
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 03/31/2021
ms.locfileid: "106072258"
---
# <span data-ttu-id="4e777-102">New-Variable</span><span class="sxs-lookup"><span data-stu-id="4e777-102">New-Variable</span></span>

## <span data-ttu-id="4e777-103">Samen vatting</span><span class="sxs-lookup"><span data-stu-id="4e777-103">Synopsis</span></span>
<span data-ttu-id="4e777-104">Hiermee maakt u een nieuwe variabele.</span><span class="sxs-lookup"><span data-stu-id="4e777-104">Creates a new variable.</span></span>

## <span data-ttu-id="4e777-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="4e777-105">Syntax</span></span>

```
New-Variable [-Name] <String> [[-Value] <Object>] [-Description <String>] [-Option <ScopedItemOptions>]
 [-Visibility <SessionStateEntryVisibility>] [-Force] [-PassThru] [-Scope <String>] [-WhatIf] [-Confirm]
 [<CommonParameters>]
```

## <span data-ttu-id="4e777-106">Description</span><span class="sxs-lookup"><span data-stu-id="4e777-106">Description</span></span>

<span data-ttu-id="4e777-107">De `New-Variable` cmdlet maakt een nieuwe variabele in Windows Power shell.</span><span class="sxs-lookup"><span data-stu-id="4e777-107">The `New-Variable` cmdlet creates a new variable in Windows PowerShell.</span></span> <span data-ttu-id="4e777-108">U kunt een waarde aan de variabele toewijzen tijdens het maken of de waarde toewijzen of wijzigen nadat deze is gemaakt.</span><span class="sxs-lookup"><span data-stu-id="4e777-108">You can assign a value to the variable while creating it or assign or change the value after it is created.</span></span>

<span data-ttu-id="4e777-109">U kunt de para meters van gebruiken `New-Variable` om de eigenschappen van de variabele in te stellen, het bereik van een variabele in te stellen en te bepalen of variabelen openbaar of privé zijn.</span><span class="sxs-lookup"><span data-stu-id="4e777-109">You can use the parameters of `New-Variable` to set the properties of the variable, set the scope of a variable, and determine whether variables are public or private.</span></span>

<span data-ttu-id="4e777-110">Normaal gesp roken maakt u een nieuwe variabele door de naam van de variabele en de bijbehorende waarde te typen, zoals `$Var = 3` , maar u kunt de `New-Variable` cmdlet gebruiken om de para meters te gebruiken.</span><span class="sxs-lookup"><span data-stu-id="4e777-110">Typically, you create a new variable by typing the variable name and its value, such as `$Var = 3`, but you can use the `New-Variable` cmdlet to use its parameters.</span></span>

## <span data-ttu-id="4e777-111">Voorbeelden</span><span class="sxs-lookup"><span data-stu-id="4e777-111">Examples</span></span>

### <span data-ttu-id="4e777-112">Voor beeld 1: een variabele maken</span><span class="sxs-lookup"><span data-stu-id="4e777-112">Example 1: Create a variable</span></span>

```
New-Variable days
```

<span data-ttu-id="4e777-113">Met deze opdracht maakt u een nieuwe variabele met de naam Days.</span><span class="sxs-lookup"><span data-stu-id="4e777-113">This command creates a new variable named days.</span></span> <span data-ttu-id="4e777-114">U hoeft de para meter **name** niet te typen.</span><span class="sxs-lookup"><span data-stu-id="4e777-114">You are not required to type the **Name** parameter.</span></span>

### <span data-ttu-id="4e777-115">Voor beeld 2: een variabele maken en hieraan een waarde toewijzen</span><span class="sxs-lookup"><span data-stu-id="4e777-115">Example 2: Create a variable and assign it a value</span></span>

```
New-Variable -Name "zipcode" -Value 98033
```

<span data-ttu-id="4e777-116">Met deze opdracht maakt u een variabele met de naam ZipCode en wijst u deze toe aan de waarde 98033.</span><span class="sxs-lookup"><span data-stu-id="4e777-116">This command creates a variable named zipcode and assigns it the value 98033.</span></span>

### <span data-ttu-id="4e777-117">Voor beeld 3: een variabele met de optie ReadOnly maken</span><span class="sxs-lookup"><span data-stu-id="4e777-117">Example 3: Create a variable with the ReadOnly option</span></span>

```
PS C:\> New-Variable -Name Max -Value 256 -Option ReadOnly
PS C:\> New-Variable -Name max -Value 1024

New-Variable : A variable with name 'max' already exists.
At line:1 char:1
+ New-Variable -Name max -Value 1024
+ ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
    + CategoryInfo          : ResourceExists: (max:String) [New-Variable], SessionStateException
    + FullyQualifiedErrorId : VariableAlreadyExists,Microsoft.PowerShell.Commands.NewVariableCommand

PS C:\> New-Variable -Name max -Value 1024 -Force
```

<span data-ttu-id="4e777-118">In dit voor beeld ziet u hoe u de `ReadOnly` optie gebruikt `New-Variable` om een variabele te beschermen tegen overschrijven.</span><span class="sxs-lookup"><span data-stu-id="4e777-118">This example shows how to use the `ReadOnly` option of `New-Variable` to protect a variable from being overwritten.</span></span>

<span data-ttu-id="4e777-119">Met de eerste opdracht maakt u een nieuwe variabele met de naam Max en stelt u de waarde ervan in op 256.</span><span class="sxs-lookup"><span data-stu-id="4e777-119">The first command creates a new variable named Max and sets its value to 256.</span></span> <span data-ttu-id="4e777-120">Hierbij wordt de para meter **Option** gebruikt met de waarde `ReadOnly` .</span><span class="sxs-lookup"><span data-stu-id="4e777-120">It uses the **Option** parameter with a value of `ReadOnly`.</span></span>

<span data-ttu-id="4e777-121">Met de tweede opdracht wordt geprobeerd een tweede variabele met dezelfde naam te maken.</span><span class="sxs-lookup"><span data-stu-id="4e777-121">The second command tries to create a second variable with the same name.</span></span> <span data-ttu-id="4e777-122">Met deze opdracht wordt een fout geretourneerd omdat de optie alleen-lezen is ingesteld voor de variabele.</span><span class="sxs-lookup"><span data-stu-id="4e777-122">This command returns an error, because the read-only option is set on the variable.</span></span>

<span data-ttu-id="4e777-123">De derde opdracht maakt gebruik van de para meter **Force** om de alleen-lezen beveiliging voor de variabele te onderdrukken.</span><span class="sxs-lookup"><span data-stu-id="4e777-123">The third command uses the **Force** parameter to override the read-only protection on the variable.</span></span>
<span data-ttu-id="4e777-124">In dit geval wordt de opdracht voor het maken van een nieuwe variabele met dezelfde naam geslaagd.</span><span class="sxs-lookup"><span data-stu-id="4e777-124">In this case, the command to create a new variable with the same name succeeds.</span></span>

### <span data-ttu-id="4e777-125">Voor beeld 4: meerdere opties toewijzen aan een variabele</span><span class="sxs-lookup"><span data-stu-id="4e777-125">Example 4: Assign multiple options to a variable</span></span>

```powershell
New-Variable -Name 'TestVariable' -Value 'Test Value' -Option AllScope,Constant
```

<span data-ttu-id="4e777-126">In dit voor beeld wordt een variabele gemaakt en worden de `AllScope` Opties en toegewezen `Constant` zodat de variabele beschikbaar is in het huidige bereik en eventuele nieuwe scopes die zijn gemaakt en niet kunnen worden gewijzigd of verwijderd.</span><span class="sxs-lookup"><span data-stu-id="4e777-126">This example creates a variable and assigns the `AllScope` and `Constant` options so the variable will be available in the current scope and any new scopes created and cannot be changed or deleted.</span></span>

### <span data-ttu-id="4e777-127">Voor beeld 5: een persoonlijke variabele maken</span><span class="sxs-lookup"><span data-stu-id="4e777-127">Example 5: Create a private variable</span></span>

```
PS C:\> New-Variable -Name counter -Visibility Private

#Effect of private variable in a module.

PS C:\> Get-Variable c*

Name                           Value
----                           -----
Culture                        en-US
ConsoleFileName
ConfirmPreference              High
CommandLineParameters          {}

PS C:\> $counter
"Cannot access the variable '$counter' because it is a private variable"
At line:1 char:1
+ $counter
+ ~~~~~~~~
    + CategoryInfo          : PermissionDenied: (counter:String) [], SessionStateException
    + FullyQualifiedErrorId : VariableIsPrivate

PS C:\> Get-Counter
Name         Value
----         -----
Counter1     3.1415
...
```

<span data-ttu-id="4e777-128">Met deze opdracht wordt het gedrag van een persoonlijke variabele in een module gedemonstreerd.</span><span class="sxs-lookup"><span data-stu-id="4e777-128">This command demonstrates the behavior of a private variable in a module.</span></span> <span data-ttu-id="4e777-129">De module bevat de `Get-Counter` cmdlet, die een persoonlijke variabele met de naam counter heeft.</span><span class="sxs-lookup"><span data-stu-id="4e777-129">The module contains the `Get-Counter` cmdlet, which has a private variable named Counter.</span></span> <span data-ttu-id="4e777-130">De opdracht gebruikt de **zichtbaarheids** parameter met de waarde privé om de variabele te maken.</span><span class="sxs-lookup"><span data-stu-id="4e777-130">The command uses the **Visibility** parameter with a value of Private to create the variable.</span></span>

<span data-ttu-id="4e777-131">De voorbeeld uitvoer toont het gedrag van een persoonlijke variabele.</span><span class="sxs-lookup"><span data-stu-id="4e777-131">The sample output shows the behavior of a private variable.</span></span> <span data-ttu-id="4e777-132">De gebruiker die de module heeft geladen kan de waarde van de item variabele niet weer geven of wijzigen, maar de teller variabele kan worden gelezen en gewijzigd door de opdrachten in de module.</span><span class="sxs-lookup"><span data-stu-id="4e777-132">The user who has loaded the module cannot view or change the value of the Counter variable, but the Counter variable can be read and changed by the commands in the module.</span></span>

### <span data-ttu-id="4e777-133">Voor beeld 6: een variabele met een spatie maken</span><span class="sxs-lookup"><span data-stu-id="4e777-133">Example 6: Create a variable with a space</span></span>

```
PS C:\> New-Variable -Name 'with space' -Value 'abc123xyz'

PS C:\> Get-Variable -Name 'with space'

Name                           Value
----                           -----
with space                     abc123xyz

PS C:\> ${with space}
abc123xyz
```

<span data-ttu-id="4e777-134">Met deze opdracht wordt gedemonstreerd dat variabelen met spaties kunnen worden gemaakt.</span><span class="sxs-lookup"><span data-stu-id="4e777-134">This command demonstrates that variables with spaces can be created.</span></span> <span data-ttu-id="4e777-135">U kunt toegang krijgen tot de variabelen met behulp van de `Get-Variable` cmdlet of rechtstreeks door een variabele met accolades te scheiden.</span><span class="sxs-lookup"><span data-stu-id="4e777-135">The variables can be accessed using the `Get-Variable` cmdlet or directly by delimiting a variable with braces.</span></span>

## <span data-ttu-id="4e777-136">Parameters</span><span class="sxs-lookup"><span data-stu-id="4e777-136">Parameters</span></span>

### <span data-ttu-id="4e777-137">-Beschrijving</span><span class="sxs-lookup"><span data-stu-id="4e777-137">-Description</span></span>

<span data-ttu-id="4e777-138">Hiermee geeft u een beschrijving van de variabele.</span><span class="sxs-lookup"><span data-stu-id="4e777-138">Specifies a description of the variable.</span></span>

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

### <span data-ttu-id="4e777-139">-Force</span><span class="sxs-lookup"><span data-stu-id="4e777-139">-Force</span></span>

<span data-ttu-id="4e777-140">Geeft aan dat de cmdlet een variabele met dezelfde naam maakt als een bestaande alleen-lezen variabele.</span><span class="sxs-lookup"><span data-stu-id="4e777-140">Indicates that the cmdlet creates a variable with the same name as an existing read-only variable.</span></span>

<span data-ttu-id="4e777-141">Standaard kunt u een variabele overschrijven, tenzij de variabele een optie waarde van of heeft `ReadOnly` `Constant` .</span><span class="sxs-lookup"><span data-stu-id="4e777-141">By default, you can overwrite a variable unless the variable has an option value of `ReadOnly` or `Constant`.</span></span> <span data-ttu-id="4e777-142">Zie de para meter **Option** voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="4e777-142">For more information, see the **Option** parameter.</span></span>

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

### <span data-ttu-id="4e777-143">-Name</span><span class="sxs-lookup"><span data-stu-id="4e777-143">-Name</span></span>

<span data-ttu-id="4e777-144">Hiermee geeft u een naam op voor de nieuwe variabele.</span><span class="sxs-lookup"><span data-stu-id="4e777-144">Specifies a name for the new variable.</span></span>

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

### <span data-ttu-id="4e777-145">-Optie</span><span class="sxs-lookup"><span data-stu-id="4e777-145">-Option</span></span>

<span data-ttu-id="4e777-146">Hiermee geeft u de waarde van de eigenschap **Options** van de variabele.</span><span class="sxs-lookup"><span data-stu-id="4e777-146">Specifies the value of the **Options** property of the variable.</span></span> <span data-ttu-id="4e777-147">De aanvaardbare waarden voor deze parameter zijn:</span><span class="sxs-lookup"><span data-stu-id="4e777-147">The acceptable values for this parameter are:</span></span>

- <span data-ttu-id="4e777-148">`None` -Geen opties instellen.</span><span class="sxs-lookup"><span data-stu-id="4e777-148">`None` - Sets no options.</span></span> <span data-ttu-id="4e777-149">`None` is de standaardwaarde.</span><span class="sxs-lookup"><span data-stu-id="4e777-149">`None` is the default.</span></span>
- <span data-ttu-id="4e777-150">`ReadOnly` -Kan worden verwijderd.</span><span class="sxs-lookup"><span data-stu-id="4e777-150">`ReadOnly` - Can be deleted.</span></span> <span data-ttu-id="4e777-151">Kan niet worden gewijzigd, behalve door gebruik te maken van de para meter **Forces** .</span><span class="sxs-lookup"><span data-stu-id="4e777-151">Cannot be changed, except by using the **Force** parameter.</span></span>
- <span data-ttu-id="4e777-152">`Private` -De variabele is alleen beschikbaar in de huidige scope.</span><span class="sxs-lookup"><span data-stu-id="4e777-152">`Private` - The variable is available only in the current scope.</span></span>
- <span data-ttu-id="4e777-153">`AllScope` -De variabele wordt gekopieerd naar een nieuwe scope die wordt gemaakt.</span><span class="sxs-lookup"><span data-stu-id="4e777-153">`AllScope` - The variable is copied to any new scopes that are created.</span></span>
- <span data-ttu-id="4e777-154">`Constant` -Kan niet worden verwijderd of gewijzigd.</span><span class="sxs-lookup"><span data-stu-id="4e777-154">`Constant` - Cannot be deleted or changed.</span></span> <span data-ttu-id="4e777-155">`Constant` is alleen geldig wanneer u een variabele maakt.</span><span class="sxs-lookup"><span data-stu-id="4e777-155">`Constant` is valid only when you are creating a variable.</span></span> <span data-ttu-id="4e777-156">U kunt de opties van een bestaande variabele niet wijzigen in `Constant` .</span><span class="sxs-lookup"><span data-stu-id="4e777-156">You cannot change the options of an existing variable to `Constant`.</span></span>

<span data-ttu-id="4e777-157">Deze waarden worden gedefinieerd als inventarisatie op basis van een vlag.</span><span class="sxs-lookup"><span data-stu-id="4e777-157">These values are defined as a flag-based enumeration.</span></span> <span data-ttu-id="4e777-158">U kunt meerdere waarden combi neren om meerdere vlaggen in te stellen met behulp van deze para meter.</span><span class="sxs-lookup"><span data-stu-id="4e777-158">You can combine multiple values together to set multiple flags using this parameter.</span></span> <span data-ttu-id="4e777-159">De waarden kunnen worden door gegeven aan de para meter **Option** als een matrix met waarden of als een door komma's gescheiden teken reeks van die waarden.</span><span class="sxs-lookup"><span data-stu-id="4e777-159">The values can be passed to the **Option** parameter as an array of values or as a comma-separated string of those values.</span></span> <span data-ttu-id="4e777-160">Met de cmdlet worden de waarden gecombineerd met behulp van een binaire waarde of bewerking.</span><span class="sxs-lookup"><span data-stu-id="4e777-160">The cmdlet will combine the values using a binary-OR operation.</span></span> <span data-ttu-id="4e777-161">Het door geven van waarden als een matrix is de eenvoudigste optie. Daarnaast kunt u met behulp van de waarden van het tabblad volt ooien.</span><span class="sxs-lookup"><span data-stu-id="4e777-161">Passing values as an array is the simplest option and also allows you to use tab-completion on the values.</span></span>

<span data-ttu-id="4e777-162">Als u de eigenschap Options van alle variabelen in de sessie wilt weer geven, typt u `Get-Variable | Format-Table -Property name, options -AutoSize` .</span><span class="sxs-lookup"><span data-stu-id="4e777-162">To see the Options property of all variables in the session, type `Get-Variable | Format-Table -Property name, options -AutoSize`.</span></span>

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

### <span data-ttu-id="4e777-163">-PassThru</span><span class="sxs-lookup"><span data-stu-id="4e777-163">-PassThru</span></span>

<span data-ttu-id="4e777-164">Retourneert een object dat het item vertegenwoordigt waarmee u werkt.</span><span class="sxs-lookup"><span data-stu-id="4e777-164">Returns an object representing the item with which you are working.</span></span> <span data-ttu-id="4e777-165">Deze cmdlet genereert standaard geen uitvoer.</span><span class="sxs-lookup"><span data-stu-id="4e777-165">By default, this cmdlet does not generate any output.</span></span>

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

### <span data-ttu-id="4e777-166">-Bereik</span><span class="sxs-lookup"><span data-stu-id="4e777-166">-Scope</span></span>

<span data-ttu-id="4e777-167">Hiermee wordt het bereik van de nieuwe variabele opgegeven.</span><span class="sxs-lookup"><span data-stu-id="4e777-167">Specifies the scope of the new variable.</span></span> <span data-ttu-id="4e777-168">De aanvaardbare waarden voor deze parameter zijn:</span><span class="sxs-lookup"><span data-stu-id="4e777-168">The acceptable values for this parameter are:</span></span>

- <span data-ttu-id="4e777-169">`Global` -Variabelen die in het globale bereik zijn gemaakt, zijn overal toegankelijk in een Power Shell-proces.</span><span class="sxs-lookup"><span data-stu-id="4e777-169">`Global` - Variables created in the global scope are accessible everywhere in a PowerShell process.</span></span>
- <span data-ttu-id="4e777-170">`Local` -Het lokale bereik verwijst naar het huidige bereik. Dit kan elk bereik zijn, afhankelijk van de context.</span><span class="sxs-lookup"><span data-stu-id="4e777-170">`Local` - The local scope refers to the current scope, this can be any scope depending on the context.</span></span>
- <span data-ttu-id="4e777-171">`Script` -Variabelen die in het script bereik zijn gemaakt, zijn alleen toegankelijk in het script bestand of de module waarin ze zijn gemaakt.</span><span class="sxs-lookup"><span data-stu-id="4e777-171">`Script` - Variables created in the script scope are accessible only within the script file or module they are created in.</span></span>
- <span data-ttu-id="4e777-172">`Private` -Variabelen die in het persoonlijke bereik zijn gemaakt, zijn niet toegankelijk buiten het bereik waarin ze zich bevinden.</span><span class="sxs-lookup"><span data-stu-id="4e777-172">`Private` - Variables created in the private scope cannot be accessed outside the scope they exist in.</span></span> <span data-ttu-id="4e777-173">U kunt een privé bereik gebruiken om een persoonlijke versie van een item met dezelfde naam in een ander bereik te maken.</span><span class="sxs-lookup"><span data-stu-id="4e777-173">You can use private scope to create a private version of an item with the same name in another scope.</span></span>
- <span data-ttu-id="4e777-174">Een getal dat relatief is ten opzichte van het huidige bereik (0 tot en met het aantal bereiken, waarbij 0 het huidige bereik is, 1 de bovenliggende Scope, 2 het bovenliggende bereik, enzovoort).</span><span class="sxs-lookup"><span data-stu-id="4e777-174">A number relative to the current scope (0 through the number of scopes, where 0 is the current scope, 1 is its parent, 2 the parent of the parent scope, and so on).</span></span> <span data-ttu-id="4e777-175">Negatieve getallen kunnen niet worden gebruikt.</span><span class="sxs-lookup"><span data-stu-id="4e777-175">Negative numbers cannot be used.</span></span>

<span data-ttu-id="4e777-176">`Local` is het standaard bereik wanneer de para meter bereik niet is opgegeven.</span><span class="sxs-lookup"><span data-stu-id="4e777-176">`Local` is the default scope when the scope parameter is not specified.</span></span>

<span data-ttu-id="4e777-177">Zie [about_Scopes](../Microsoft.PowerShell.Core/About/about_Scopes.md)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="4e777-177">For more information, see [about_Scopes](../Microsoft.PowerShell.Core/About/about_Scopes.md).</span></span>

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

### <span data-ttu-id="4e777-178">-Waarde</span><span class="sxs-lookup"><span data-stu-id="4e777-178">-Value</span></span>

<span data-ttu-id="4e777-179">Hiermee geeft u de begin waarde van de variabele.</span><span class="sxs-lookup"><span data-stu-id="4e777-179">Specifies the initial value of the variable.</span></span>

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

### <span data-ttu-id="4e777-180">-Zicht baarheid</span><span class="sxs-lookup"><span data-stu-id="4e777-180">-Visibility</span></span>

<span data-ttu-id="4e777-181">Hiermee wordt bepaald of de variabele zichtbaar is buiten de sessie waarin deze is gemaakt.</span><span class="sxs-lookup"><span data-stu-id="4e777-181">Determines whether the variable is visible outside of the session in which it was created.</span></span> <span data-ttu-id="4e777-182">Deze para meter is ontworpen voor gebruik in scripts en opdrachten die aan andere gebruikers worden geleverd.</span><span class="sxs-lookup"><span data-stu-id="4e777-182">This parameter is designed for use in scripts and commands that will be delivered to other users.</span></span> <span data-ttu-id="4e777-183">De aanvaardbare waarden voor deze parameter zijn:</span><span class="sxs-lookup"><span data-stu-id="4e777-183">The acceptable values for this parameter are:</span></span>

- <span data-ttu-id="4e777-184">`Public` -De variabele is zichtbaar.</span><span class="sxs-lookup"><span data-stu-id="4e777-184">`Public` - The variable is visible.</span></span> <span data-ttu-id="4e777-185">`Public` is de standaardwaarde.</span><span class="sxs-lookup"><span data-stu-id="4e777-185">`Public` is the default.</span></span>
- <span data-ttu-id="4e777-186">`Private` -De variabele is niet zichtbaar.</span><span class="sxs-lookup"><span data-stu-id="4e777-186">`Private` - The variable is not visible.</span></span>

<span data-ttu-id="4e777-187">Wanneer een variabele privé is, wordt deze niet weer gegeven in lijst met variabelen, zoals die worden geretourneerd door `Get-Variable` , of in de weer gaven van het `Variable:` station.</span><span class="sxs-lookup"><span data-stu-id="4e777-187">When a variable is private, it does not appear in lists of variables, such as those returned by `Get-Variable`, or in displays of the `Variable:` drive.</span></span> <span data-ttu-id="4e777-188">Opdrachten om de waarde van een persoonlijke variabele te lezen of te wijzigen, retour neren een fout.</span><span class="sxs-lookup"><span data-stu-id="4e777-188">Commands to read or change the value of a private variable return an error.</span></span> <span data-ttu-id="4e777-189">De gebruiker kan echter opdrachten uitvoeren die een persoonlijke variabele gebruiken als de opdrachten zijn geschreven in de sessie waarin de variabele is gedefinieerd.</span><span class="sxs-lookup"><span data-stu-id="4e777-189">However, the user can run commands that use a private variable if the commands were written in the session in which the variable was defined.</span></span>

```yaml
Type: System.Management.Automation.SessionStateEntryVisibility
Parameter Sets: (All)
Aliases:
Accepted values: Public, Private

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="4e777-190">-Confirm</span><span class="sxs-lookup"><span data-stu-id="4e777-190">-Confirm</span></span>

<span data-ttu-id="4e777-191">Hiermee wordt u gevraagd om bevestiging voordat u de cmdlet uitvoert.</span><span class="sxs-lookup"><span data-stu-id="4e777-191">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="4e777-192">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="4e777-192">-WhatIf</span></span>

<span data-ttu-id="4e777-193">Hiermee wordt weergegeven wat er zou gebeuren als u de cmdlet uitvoert.</span><span class="sxs-lookup"><span data-stu-id="4e777-193">Shows what would happen if the cmdlet runs.</span></span> <span data-ttu-id="4e777-194">De cmdlet wordt niet uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="4e777-194">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="4e777-195">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="4e777-195">CommonParameters</span></span>

<span data-ttu-id="4e777-196">Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="4e777-196">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="4e777-197">Zie [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="4e777-197">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="4e777-198">Invoerwaarden</span><span class="sxs-lookup"><span data-stu-id="4e777-198">Inputs</span></span>

### <span data-ttu-id="4e777-199">System. object</span><span class="sxs-lookup"><span data-stu-id="4e777-199">System.Object</span></span>

<span data-ttu-id="4e777-200">U kunt een waarde door sluizen naar `New-Variable` .</span><span class="sxs-lookup"><span data-stu-id="4e777-200">You can pipe a value to `New-Variable`.</span></span>

## <span data-ttu-id="4e777-201">Uitvoerwaarden</span><span class="sxs-lookup"><span data-stu-id="4e777-201">Outputs</span></span>

### <span data-ttu-id="4e777-202">Geen of System. Management. Automation. PSVariable</span><span class="sxs-lookup"><span data-stu-id="4e777-202">None or System.Management.Automation.PSVariable</span></span>

<span data-ttu-id="4e777-203">Wanneer u de para meter **PassThru** gebruikt, `New-Variable` genereert een **System. Management. Automation. PSVariable** -object dat de nieuwe variabele vertegenwoordigt.</span><span class="sxs-lookup"><span data-stu-id="4e777-203">When you use the **PassThru** parameter, `New-Variable` generates a **System.Management.Automation.PSVariable** object representing the new variable.</span></span> <span data-ttu-id="4e777-204">Anders wordt met deze cmdlet geen uitvoer gegenereerd.</span><span class="sxs-lookup"><span data-stu-id="4e777-204">Otherwise, this cmdlet does not generate any output.</span></span>

## <span data-ttu-id="4e777-205">Notities</span><span class="sxs-lookup"><span data-stu-id="4e777-205">Notes</span></span>

## <span data-ttu-id="4e777-206">Verwante koppelingen</span><span class="sxs-lookup"><span data-stu-id="4e777-206">Related Links</span></span>

[<span data-ttu-id="4e777-207">Clear-variabele</span><span class="sxs-lookup"><span data-stu-id="4e777-207">Clear-Variable</span></span>](Clear-Variable.md)

[<span data-ttu-id="4e777-208">Get-variabele</span><span class="sxs-lookup"><span data-stu-id="4e777-208">Get-Variable</span></span>](Get-Variable.md)

[<span data-ttu-id="4e777-209">Remove-variabele</span><span class="sxs-lookup"><span data-stu-id="4e777-209">Remove-Variable</span></span>](Remove-Variable.md)

[<span data-ttu-id="4e777-210">Set-variabele</span><span class="sxs-lookup"><span data-stu-id="4e777-210">Set-Variable</span></span>](Set-Variable.md)
