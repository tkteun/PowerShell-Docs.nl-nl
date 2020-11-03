---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/new-variable?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: New-Variable
ms.openlocfilehash: 6db5d6693e7e42b5563baa3dbaebb495f97f53a6
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/07/2020
ms.locfileid: "93250392"
---
# <span data-ttu-id="9cbbd-103">New-Variable</span><span class="sxs-lookup"><span data-stu-id="9cbbd-103">New-Variable</span></span>

## <span data-ttu-id="9cbbd-104">SAMENVATTING</span><span class="sxs-lookup"><span data-stu-id="9cbbd-104">SYNOPSIS</span></span>
<span data-ttu-id="9cbbd-105">Hiermee maakt u een nieuwe variabele.</span><span class="sxs-lookup"><span data-stu-id="9cbbd-105">Creates a new variable.</span></span>

## <span data-ttu-id="9cbbd-106">SYNTAXIS</span><span class="sxs-lookup"><span data-stu-id="9cbbd-106">SYNTAX</span></span>

```
New-Variable [-Name] <String> [[-Value] <Object>] [-Description <String>] [-Option <ScopedItemOptions>]
 [-Visibility <SessionStateEntryVisibility>] [-Force] [-PassThru] [-Scope <String>] [-WhatIf] [-Confirm]
 [<CommonParameters>]
```

## <span data-ttu-id="9cbbd-107">BESCHRIJVING</span><span class="sxs-lookup"><span data-stu-id="9cbbd-107">DESCRIPTION</span></span>
<span data-ttu-id="9cbbd-108">Met de cmdlet **new-variable** maakt u een nieuwe variabele in Windows Power shell.</span><span class="sxs-lookup"><span data-stu-id="9cbbd-108">The **New-Variable** cmdlet creates a new variable in Windows PowerShell.</span></span>
<span data-ttu-id="9cbbd-109">U kunt een waarde aan de variabele toewijzen tijdens het maken of de waarde toewijzen of wijzigen nadat deze is gemaakt.</span><span class="sxs-lookup"><span data-stu-id="9cbbd-109">You can assign a value to the variable while creating it or assign or change the value after it is created.</span></span>

<span data-ttu-id="9cbbd-110">U kunt de para meters van **new-variable** gebruiken om de eigenschappen van de variabele in te stellen, het bereik van een variabele in te stellen en te bepalen of variabelen openbaar of privé zijn.</span><span class="sxs-lookup"><span data-stu-id="9cbbd-110">You can use the parameters of **New-Variable** to set the properties of the variable, set the scope of a variable, and determine whether variables are public or private.</span></span>

<span data-ttu-id="9cbbd-111">Normaal gesp roken maakt u een nieuwe variabele door de naam van de variabele en de bijbehorende waarde te typen, zoals `$Var = 3` , maar u kunt de cmdlet **new-variable** gebruiken om de para meters te gebruiken.</span><span class="sxs-lookup"><span data-stu-id="9cbbd-111">Typically, you create a new variable by typing the variable name and its value, such as `$Var = 3`, but you can use the **New-Variable** cmdlet to use its parameters.</span></span>

## <span data-ttu-id="9cbbd-112">VOORBEELDEN</span><span class="sxs-lookup"><span data-stu-id="9cbbd-112">EXAMPLES</span></span>

### <span data-ttu-id="9cbbd-113">Voor beeld 1: een variabele maken</span><span class="sxs-lookup"><span data-stu-id="9cbbd-113">Example 1: Create a variable</span></span>

```
PS C:\> New-Variable days
```

<span data-ttu-id="9cbbd-114">Met deze opdracht maakt u een nieuwe variabele met de naam Days.</span><span class="sxs-lookup"><span data-stu-id="9cbbd-114">This command creates a new variable named days.</span></span>
<span data-ttu-id="9cbbd-115">U hoeft de para meter *name* niet te typen.</span><span class="sxs-lookup"><span data-stu-id="9cbbd-115">You are not required to type the *Name* parameter.</span></span>

### <span data-ttu-id="9cbbd-116">Voor beeld 2: een variabele maken en hieraan een waarde toewijzen</span><span class="sxs-lookup"><span data-stu-id="9cbbd-116">Example 2: Create a variable and assign it a value</span></span>

```
PS C:\> New-Variable -Name "zipcode" -Value 98033
```

<span data-ttu-id="9cbbd-117">Met deze opdracht maakt u een variabele met de naam ZipCode en wijst u deze toe aan de waarde 98033.</span><span class="sxs-lookup"><span data-stu-id="9cbbd-117">This command creates a variable named zipcode and assigns it the value 98033.</span></span>

### <span data-ttu-id="9cbbd-118">Voor beeld 3: een variabele met de optie ReadOnly maken</span><span class="sxs-lookup"><span data-stu-id="9cbbd-118">Example 3: Create a variable with the ReadOnly option</span></span>

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

<span data-ttu-id="9cbbd-119">In dit voor beeld ziet u hoe u de optie ReadOnly van **new-variable** gebruikt om een variabele te beschermen tegen overschrijven.</span><span class="sxs-lookup"><span data-stu-id="9cbbd-119">This example shows how to use the ReadOnly option of **New-Variable** to protect a variable from being overwritten.</span></span>

<span data-ttu-id="9cbbd-120">Met de eerste opdracht maakt u een nieuwe variabele met de naam Max en stelt u de waarde ervan in op 256.</span><span class="sxs-lookup"><span data-stu-id="9cbbd-120">The first command creates a new variable named Max and sets its value to 256.</span></span>
<span data-ttu-id="9cbbd-121">De para meter *Option* wordt gebruikt met de waarde readonly.</span><span class="sxs-lookup"><span data-stu-id="9cbbd-121">It uses the *Option* parameter with a value of ReadOnly.</span></span>

<span data-ttu-id="9cbbd-122">Met de tweede opdracht wordt geprobeerd een tweede variabele met dezelfde naam te maken.</span><span class="sxs-lookup"><span data-stu-id="9cbbd-122">The second command tries to create a second variable with the same name.</span></span>
<span data-ttu-id="9cbbd-123">Met deze opdracht wordt een fout geretourneerd omdat de optie alleen-lezen is ingesteld voor de variabele.</span><span class="sxs-lookup"><span data-stu-id="9cbbd-123">This command returns an error, because the read-only option is set on the variable.</span></span>

<span data-ttu-id="9cbbd-124">De derde opdracht maakt gebruik van de para meter *Force* om de alleen-lezen beveiliging voor de variabele te onderdrukken.</span><span class="sxs-lookup"><span data-stu-id="9cbbd-124">The third command uses the *Force* parameter to override the read-only protection on the variable.</span></span>
<span data-ttu-id="9cbbd-125">In dit geval wordt de opdracht voor het maken van een nieuwe variabele met dezelfde naam geslaagd.</span><span class="sxs-lookup"><span data-stu-id="9cbbd-125">In this case, the command to create a new variable with the same name succeeds.</span></span>

### <span data-ttu-id="9cbbd-126">Voor beeld 4: een persoonlijke variabele maken</span><span class="sxs-lookup"><span data-stu-id="9cbbd-126">Example 4: Create a private variable</span></span>

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

<span data-ttu-id="9cbbd-127">Met deze opdracht wordt het gedrag van een persoonlijke variabele in een module gedemonstreerd.</span><span class="sxs-lookup"><span data-stu-id="9cbbd-127">This command demonstrates the behavior of a private variable in a module.</span></span>
<span data-ttu-id="9cbbd-128">De module bevat de cmdlet Get-Counter, die een persoonlijke variabele met de naam counter heeft.</span><span class="sxs-lookup"><span data-stu-id="9cbbd-128">The module contains the Get-Counter cmdlet, which has a private variable named Counter.</span></span>
<span data-ttu-id="9cbbd-129">De opdracht gebruikt de *zichtbaarheids* parameter met de waarde privé om de variabele te maken.</span><span class="sxs-lookup"><span data-stu-id="9cbbd-129">The command uses the *Visibility* parameter with a value of Private to create the variable.</span></span>

<span data-ttu-id="9cbbd-130">De voorbeeld uitvoer toont het gedrag van een persoonlijke variabele.</span><span class="sxs-lookup"><span data-stu-id="9cbbd-130">The sample output shows the behavior of a private variable.</span></span>
<span data-ttu-id="9cbbd-131">De gebruiker die de module heeft geladen kan de waarde van de item variabele niet weer geven of wijzigen, maar de teller variabele kan worden gelezen en gewijzigd door de opdrachten in de module.</span><span class="sxs-lookup"><span data-stu-id="9cbbd-131">The user who has loaded the module cannot view or change the value of the Counter variable, but the Counter variable can be read and changed by the commands in the module.</span></span>

### <span data-ttu-id="9cbbd-132">Voor beeld 5: een variabele met een spatie maken</span><span class="sxs-lookup"><span data-stu-id="9cbbd-132">Example 5: Create a variable with a space</span></span>

```
PS C:\> New-Variable -Name 'with space' -Value 'abc123xyz'

PS C:\> Get-Variable -Name 'with space'

Name                           Value
----                           -----
with space                     abc123xyz

PS C:\> ${with space}
abc123xyz
```

<span data-ttu-id="9cbbd-133">Met deze opdracht wordt gedemonstreerd dat variabelen met spaties kunnen worden gemaakt.</span><span class="sxs-lookup"><span data-stu-id="9cbbd-133">This command demonstrates that variables with spaces can be created.</span></span>
<span data-ttu-id="9cbbd-134">De variabelen zijn toegankelijk met de cmdlet **Get-variable** of rechtstreeks door een variabele met accolades te scheiden.</span><span class="sxs-lookup"><span data-stu-id="9cbbd-134">The variables can be accessed using the **Get-Variable** cmdlet or directly by delimiting a variable with braces.</span></span>

## <span data-ttu-id="9cbbd-135">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="9cbbd-135">PARAMETERS</span></span>

### <span data-ttu-id="9cbbd-136">-Beschrijving</span><span class="sxs-lookup"><span data-stu-id="9cbbd-136">-Description</span></span>
<span data-ttu-id="9cbbd-137">Hiermee geeft u een beschrijving van de variabele.</span><span class="sxs-lookup"><span data-stu-id="9cbbd-137">Specifies a description of the variable.</span></span>

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

### <span data-ttu-id="9cbbd-138">-Force</span><span class="sxs-lookup"><span data-stu-id="9cbbd-138">-Force</span></span>
<span data-ttu-id="9cbbd-139">Geeft aan dat de cmdlet een variabele met dezelfde naam maakt als een bestaande alleen-lezen variabele.</span><span class="sxs-lookup"><span data-stu-id="9cbbd-139">Indicates that the cmdlet creates a variable with the same name as an existing read-only variable.</span></span>

<span data-ttu-id="9cbbd-140">Standaard kunt u een variabele overschrijven, tenzij de variabele een optie waarde ReadOnly of constant heeft.</span><span class="sxs-lookup"><span data-stu-id="9cbbd-140">By default, you can overwrite a variable unless the variable has an option value of ReadOnly or Constant.</span></span>
<span data-ttu-id="9cbbd-141">Zie de para meter *Option* voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="9cbbd-141">For more information, see the *Option* parameter.</span></span>

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

### <span data-ttu-id="9cbbd-142">-Name</span><span class="sxs-lookup"><span data-stu-id="9cbbd-142">-Name</span></span>
<span data-ttu-id="9cbbd-143">Hiermee geeft u een naam op voor de nieuwe variabele.</span><span class="sxs-lookup"><span data-stu-id="9cbbd-143">Specifies a name for the new variable.</span></span>

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

### <span data-ttu-id="9cbbd-144">-Optie</span><span class="sxs-lookup"><span data-stu-id="9cbbd-144">-Option</span></span>
<span data-ttu-id="9cbbd-145">Hiermee geeft u de waarde van de eigenschap **Options** van de variabele. De acceptabele waarden voor deze para meter zijn:</span><span class="sxs-lookup"><span data-stu-id="9cbbd-145">Specifies the value of the **Options** property of the variable.The acceptable values for this parameter are:</span></span>

- <span data-ttu-id="9cbbd-146">Geen.</span><span class="sxs-lookup"><span data-stu-id="9cbbd-146">None.</span></span>
<span data-ttu-id="9cbbd-147">Hiermee stelt u geen opties in.</span><span class="sxs-lookup"><span data-stu-id="9cbbd-147">Sets no options.</span></span>
<span data-ttu-id="9cbbd-148">(Geen is de standaard instelling.)</span><span class="sxs-lookup"><span data-stu-id="9cbbd-148">(None is the default.)</span></span>
- <span data-ttu-id="9cbbd-149">Kenmerk.</span><span class="sxs-lookup"><span data-stu-id="9cbbd-149">ReadOnly.</span></span>
<span data-ttu-id="9cbbd-150">Kan worden verwijderd.</span><span class="sxs-lookup"><span data-stu-id="9cbbd-150">Can be deleted.</span></span>
<span data-ttu-id="9cbbd-151">Kan niet worden gewijzigd, behalve door gebruik te maken van de para meter *Forces* .</span><span class="sxs-lookup"><span data-stu-id="9cbbd-151">Cannot be changed, except by using the *Force* parameter.</span></span>
- <span data-ttu-id="9cbbd-152">Eigen.</span><span class="sxs-lookup"><span data-stu-id="9cbbd-152">Private.</span></span>
<span data-ttu-id="9cbbd-153">De variabele is alleen beschikbaar in het huidige bereik.</span><span class="sxs-lookup"><span data-stu-id="9cbbd-153">The variable is available only in the current scope.</span></span>
- <span data-ttu-id="9cbbd-154">AllScope.</span><span class="sxs-lookup"><span data-stu-id="9cbbd-154">AllScope.</span></span>
<span data-ttu-id="9cbbd-155">De variabele wordt gekopieerd naar nieuwe bereiken die worden gemaakt.</span><span class="sxs-lookup"><span data-stu-id="9cbbd-155">The variable is copied to any new scopes that are created.</span></span>
- <span data-ttu-id="9cbbd-156">Constant hoog.</span><span class="sxs-lookup"><span data-stu-id="9cbbd-156">Constant.</span></span>
<span data-ttu-id="9cbbd-157">Kan niet worden verwijderd of gewijzigd.</span><span class="sxs-lookup"><span data-stu-id="9cbbd-157">Cannot be deleted or changed.</span></span>
<span data-ttu-id="9cbbd-158">Constante is alleen geldig wanneer u een variabele maakt.</span><span class="sxs-lookup"><span data-stu-id="9cbbd-158">Constant is valid only when you are creating a variable.</span></span>
<span data-ttu-id="9cbbd-159">U kunt de opties van een bestaande variabele niet wijzigen in constante.</span><span class="sxs-lookup"><span data-stu-id="9cbbd-159">You cannot change the options of an existing variable to Constant.</span></span>

<span data-ttu-id="9cbbd-160">Als u de eigenschap **Options** van alle variabelen in de sessie wilt weer geven, typt u `Get-Variable | Format-Table -Property name, options -autosize` .</span><span class="sxs-lookup"><span data-stu-id="9cbbd-160">To see the **Options** property of all variables in the session, type `Get-Variable | Format-Table -Property name, options -autosize`.</span></span>

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

### <span data-ttu-id="9cbbd-161">-PassThru</span><span class="sxs-lookup"><span data-stu-id="9cbbd-161">-PassThru</span></span>
<span data-ttu-id="9cbbd-162">Retourneert een object dat het item vertegenwoordigt waarmee u werkt.</span><span class="sxs-lookup"><span data-stu-id="9cbbd-162">Returns an object representing the item with which you are working.</span></span>
<span data-ttu-id="9cbbd-163">Deze cmdlet genereert standaard geen uitvoer.</span><span class="sxs-lookup"><span data-stu-id="9cbbd-163">By default, this cmdlet does not generate any output.</span></span>

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

### <span data-ttu-id="9cbbd-164">-Bereik</span><span class="sxs-lookup"><span data-stu-id="9cbbd-164">-Scope</span></span>
<span data-ttu-id="9cbbd-165">Hiermee wordt het bereik van de nieuwe variabele opgegeven.</span><span class="sxs-lookup"><span data-stu-id="9cbbd-165">Specifies the scope of the new variable.</span></span>
<span data-ttu-id="9cbbd-166">De aanvaardbare waarden voor deze parameter zijn:</span><span class="sxs-lookup"><span data-stu-id="9cbbd-166">The acceptable values for this parameter are:</span></span>

- <span data-ttu-id="9cbbd-167">Internationaal.</span><span class="sxs-lookup"><span data-stu-id="9cbbd-167">Global.</span></span>
<span data-ttu-id="9cbbd-168">Variabelen die in het globale bereik zijn gemaakt, zijn overal toegankelijk in een Power Shell-proces.</span><span class="sxs-lookup"><span data-stu-id="9cbbd-168">Variables created in the global scope are accessible everywhere in a PowerShell process.</span></span>
- <span data-ttu-id="9cbbd-169">Lokale.</span><span class="sxs-lookup"><span data-stu-id="9cbbd-169">Local.</span></span>
<span data-ttu-id="9cbbd-170">Het lokale bereik verwijst naar het huidige bereik. Dit kan elk bereik zijn, afhankelijk van de context.</span><span class="sxs-lookup"><span data-stu-id="9cbbd-170">The local scope refers to the current scope, this can be any scope depending on the context.</span></span>
- <span data-ttu-id="9cbbd-171">Schriften.</span><span class="sxs-lookup"><span data-stu-id="9cbbd-171">Script.</span></span>
<span data-ttu-id="9cbbd-172">Variabelen die in het script bereik zijn gemaakt, zijn alleen toegankelijk in het script bestand of de module waarin ze zijn gemaakt.</span><span class="sxs-lookup"><span data-stu-id="9cbbd-172">Variables created in the script scope are accessible only within the script file or module they are created in.</span></span>
- <span data-ttu-id="9cbbd-173">Eigen.</span><span class="sxs-lookup"><span data-stu-id="9cbbd-173">Private.</span></span>
<span data-ttu-id="9cbbd-174">Variabelen die in het persoonlijke bereik zijn gemaakt, zijn niet toegankelijk buiten het bereik waarin ze zich bevinden.</span><span class="sxs-lookup"><span data-stu-id="9cbbd-174">Variables created in the private scope cannot be accessed outside the scope they exist in.</span></span>
<span data-ttu-id="9cbbd-175">U kunt een privé bereik gebruiken om een persoonlijke versie van een item met dezelfde naam in een ander bereik te maken.</span><span class="sxs-lookup"><span data-stu-id="9cbbd-175">You can use private scope to create a private version of an item with the same name in another scope.</span></span>
- <span data-ttu-id="9cbbd-176">Een getal dat relatief is ten opzichte van het huidige bereik (0 tot en met het aantal bereiken, waarbij 0 het huidige bereik is, 1 de bovenliggende Scope, 2 het bovenliggende bereik, enzovoort).</span><span class="sxs-lookup"><span data-stu-id="9cbbd-176">A number relative to the current scope (0 through the number of scopes, where 0 is the current scope, 1 is its parent, 2 the parent of the parent scope, and so on).</span></span>
<span data-ttu-id="9cbbd-177">Negatieve getallen kunnen niet worden gebruikt.</span><span class="sxs-lookup"><span data-stu-id="9cbbd-177">Negative numbers cannot be used.</span></span>

<span data-ttu-id="9cbbd-178">Local is het standaard bereik wanneer de para meter bereik niet is opgegeven.</span><span class="sxs-lookup"><span data-stu-id="9cbbd-178">Local is the default scope when the scope parameter is not specified.</span></span>

<span data-ttu-id="9cbbd-179">Zie about_Scopes voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="9cbbd-179">For more information, see about_Scopes.</span></span>

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

### <span data-ttu-id="9cbbd-180">-Waarde</span><span class="sxs-lookup"><span data-stu-id="9cbbd-180">-Value</span></span>
<span data-ttu-id="9cbbd-181">Hiermee geeft u de begin waarde van de variabele.</span><span class="sxs-lookup"><span data-stu-id="9cbbd-181">Specifies the initial value of the variable.</span></span>

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

### <span data-ttu-id="9cbbd-182">-Zicht baarheid</span><span class="sxs-lookup"><span data-stu-id="9cbbd-182">-Visibility</span></span>
<span data-ttu-id="9cbbd-183">Hiermee wordt bepaald of de variabele zichtbaar is buiten de sessie waarin deze is gemaakt.</span><span class="sxs-lookup"><span data-stu-id="9cbbd-183">Determines whether the variable is visible outside of the session in which it was created.</span></span>
<span data-ttu-id="9cbbd-184">Deze para meter is ontworpen voor gebruik in scripts en opdrachten die aan andere gebruikers worden geleverd.</span><span class="sxs-lookup"><span data-stu-id="9cbbd-184">This parameter is designed for  use in scripts and commands that will be delivered to other users.</span></span>
<span data-ttu-id="9cbbd-185">De aanvaardbare waarden voor deze parameter zijn:</span><span class="sxs-lookup"><span data-stu-id="9cbbd-185">The acceptable values for this parameter are:</span></span>

- <span data-ttu-id="9cbbd-186">Open.</span><span class="sxs-lookup"><span data-stu-id="9cbbd-186">Public.</span></span>
<span data-ttu-id="9cbbd-187">De variabele is zichtbaar.</span><span class="sxs-lookup"><span data-stu-id="9cbbd-187">The variable is visible.</span></span>
<span data-ttu-id="9cbbd-188">(Openbaar is de standaard instelling.)</span><span class="sxs-lookup"><span data-stu-id="9cbbd-188">(Public is the default.)</span></span>
- <span data-ttu-id="9cbbd-189">Eigen.</span><span class="sxs-lookup"><span data-stu-id="9cbbd-189">Private.</span></span>
<span data-ttu-id="9cbbd-190">De variabele is niet zichtbaar.</span><span class="sxs-lookup"><span data-stu-id="9cbbd-190">The variable is not visible.</span></span>

<span data-ttu-id="9cbbd-191">Wanneer een variabele privé is, wordt deze niet weer gegeven in lijst met variabelen, zoals die worden geretourneerd door Get-variable of in weer gaven van de variabele: station.</span><span class="sxs-lookup"><span data-stu-id="9cbbd-191">When a variable is private, it does not appear in lists of variables, such as those returned by Get-Variable, or in displays of the Variable: drive.</span></span>
<span data-ttu-id="9cbbd-192">Opdrachten om de waarde van een persoonlijke variabele te lezen of te wijzigen, retour neren een fout.</span><span class="sxs-lookup"><span data-stu-id="9cbbd-192">Commands to read or change the value of a private variable return an error.</span></span>
<span data-ttu-id="9cbbd-193">De gebruiker kan echter opdrachten uitvoeren die een persoonlijke variabele gebruiken als de opdrachten zijn geschreven in de sessie waarin de variabele is gedefinieerd.</span><span class="sxs-lookup"><span data-stu-id="9cbbd-193">However, the user can run commands that use a private variable if the commands were written in the session in which the variable was defined.</span></span>

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

### <span data-ttu-id="9cbbd-194">-Confirm</span><span class="sxs-lookup"><span data-stu-id="9cbbd-194">-Confirm</span></span>
<span data-ttu-id="9cbbd-195">Hiermee wordt u gevraagd om bevestiging voordat u de cmdlet uitvoert.</span><span class="sxs-lookup"><span data-stu-id="9cbbd-195">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="9cbbd-196">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="9cbbd-196">-WhatIf</span></span>
<span data-ttu-id="9cbbd-197">Hiermee wordt weergegeven wat er zou gebeuren als u de cmdlet uitvoert.</span><span class="sxs-lookup"><span data-stu-id="9cbbd-197">Shows what would happen if the cmdlet runs.</span></span>
<span data-ttu-id="9cbbd-198">De cmdlet wordt niet uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="9cbbd-198">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="9cbbd-199">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="9cbbd-199">CommonParameters</span></span>
<span data-ttu-id="9cbbd-200">Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="9cbbd-200">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="9cbbd-201">Zie [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="9cbbd-201">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="9cbbd-202">INVOER</span><span class="sxs-lookup"><span data-stu-id="9cbbd-202">INPUTS</span></span>

### <span data-ttu-id="9cbbd-203">System. object</span><span class="sxs-lookup"><span data-stu-id="9cbbd-203">System.Object</span></span>
<span data-ttu-id="9cbbd-204">U kunt een waarde door sluizen naar een **nieuwe variabele**.</span><span class="sxs-lookup"><span data-stu-id="9cbbd-204">You can pipe a value to **New-Variable**.</span></span>

## <span data-ttu-id="9cbbd-205">UITVOER</span><span class="sxs-lookup"><span data-stu-id="9cbbd-205">OUTPUTS</span></span>

### <span data-ttu-id="9cbbd-206">Geen of System. Management. Automation. PSVariable</span><span class="sxs-lookup"><span data-stu-id="9cbbd-206">None or System.Management.Automation.PSVariable</span></span>
<span data-ttu-id="9cbbd-207">Wanneer u de para meter *PassThru* gebruikt, genereert **new-variable** een **System. Management. Automation. PSVariable** -object dat de nieuwe variabele vertegenwoordigt.</span><span class="sxs-lookup"><span data-stu-id="9cbbd-207">When you use the *PassThru* parameter, **New-Variable** generates a **System.Management.Automation.PSVariable** object representing the new variable.</span></span>
<span data-ttu-id="9cbbd-208">Anders wordt met deze cmdlet geen uitvoer gegenereerd.</span><span class="sxs-lookup"><span data-stu-id="9cbbd-208">Otherwise, this cmdlet does not generate any output.</span></span>

## <span data-ttu-id="9cbbd-209">OPMERKINGEN</span><span class="sxs-lookup"><span data-stu-id="9cbbd-209">NOTES</span></span>

## <span data-ttu-id="9cbbd-210">GERELATEERDE KOPPELINGEN</span><span class="sxs-lookup"><span data-stu-id="9cbbd-210">RELATED LINKS</span></span>

[<span data-ttu-id="9cbbd-211">Clear-variabele</span><span class="sxs-lookup"><span data-stu-id="9cbbd-211">Clear-Variable</span></span>](Clear-Variable.md)

[<span data-ttu-id="9cbbd-212">Get-variabele</span><span class="sxs-lookup"><span data-stu-id="9cbbd-212">Get-Variable</span></span>](Get-Variable.md)

[<span data-ttu-id="9cbbd-213">Remove-variabele</span><span class="sxs-lookup"><span data-stu-id="9cbbd-213">Remove-Variable</span></span>](Remove-Variable.md)

[<span data-ttu-id="9cbbd-214">Set-variabele</span><span class="sxs-lookup"><span data-stu-id="9cbbd-214">Set-Variable</span></span>](Set-Variable.md)
