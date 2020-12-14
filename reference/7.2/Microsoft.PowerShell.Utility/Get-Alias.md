---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/get-alias?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-Alias
ms.openlocfilehash: 7b6f639d1c5685e341260c056a1dd0a17fe9f46d
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 11/17/2020
ms.locfileid: "94705452"
---
# <span data-ttu-id="766aa-102">Get-Alias</span><span class="sxs-lookup"><span data-stu-id="766aa-102">Get-Alias</span></span>

## <span data-ttu-id="766aa-103">SAMENVATTING</span><span class="sxs-lookup"><span data-stu-id="766aa-103">SYNOPSIS</span></span>
<span data-ttu-id="766aa-104">Hiermee worden de aliassen opgehaald voor de huidige sessie.</span><span class="sxs-lookup"><span data-stu-id="766aa-104">Gets the aliases for the current session.</span></span>

## <span data-ttu-id="766aa-105">SYNTAXIS</span><span class="sxs-lookup"><span data-stu-id="766aa-105">SYNTAX</span></span>

### <span data-ttu-id="766aa-106">Standaard (standaard instelling)</span><span class="sxs-lookup"><span data-stu-id="766aa-106">Default (Default)</span></span>

```
Get-Alias [[-Name] <String[]>] [-Exclude <String[]>] [-Scope <String>] [<CommonParameters>]
```

### <span data-ttu-id="766aa-107">Definitie</span><span class="sxs-lookup"><span data-stu-id="766aa-107">Definition</span></span>

```
Get-Alias [-Exclude <String[]>] [-Scope <String>] [-Definition <String[]>] [<CommonParameters>]
```

## <span data-ttu-id="766aa-108">BESCHRIJVING</span><span class="sxs-lookup"><span data-stu-id="766aa-108">DESCRIPTION</span></span>

<span data-ttu-id="766aa-109">Met de cmdlet **Get-alias** worden de aliassen in de huidige sessie opgehaald.</span><span class="sxs-lookup"><span data-stu-id="766aa-109">The **Get-Alias** cmdlet gets the aliases in the current session.</span></span>
<span data-ttu-id="766aa-110">Dit omvat ingebouwde aliassen, aliassen die u hebt ingesteld of geïmporteerd en aliassen die u hebt toegevoegd aan uw Power shell-profiel.</span><span class="sxs-lookup"><span data-stu-id="766aa-110">This includes built-in aliases, aliases that you have set or imported, and aliases that you have added to your PowerShell profile.</span></span>

<span data-ttu-id="766aa-111">**Get-alias** gebruikt standaard een alias en retourneert de naam van de opdracht.</span><span class="sxs-lookup"><span data-stu-id="766aa-111">By default, **Get-Alias** takes an alias and returns the command name.</span></span>
<span data-ttu-id="766aa-112">Wanneer u de para meter *definitie* gebruikt, neemt **Get-alias** de naam van een opdracht en worden de aliassen ervan geretourneerd.</span><span class="sxs-lookup"><span data-stu-id="766aa-112">When you use the *Definition* parameter, **Get-Alias** takes a command name and returns its aliases.</span></span>

<span data-ttu-id="766aa-113">Vanaf Windows Power Shell 3,0 worden met **Get-alias** niet-afgebroken alias namen weer gegeven in een `<alias> -> <definition>` indeling zodat u de informatie die u nodig hebt, nog gemakkelijker kunt vinden.</span><span class="sxs-lookup"><span data-stu-id="766aa-113">Beginning in Windows PowerShell 3.0, **Get-Alias** displays non-hyphenated alias names in an `<alias> -> <definition>` format to make it even easier to find the information that you need.</span></span>

## <span data-ttu-id="766aa-114">VOORBEELDEN</span><span class="sxs-lookup"><span data-stu-id="766aa-114">EXAMPLES</span></span>

### <span data-ttu-id="766aa-115">Voor beeld 1: alle aliassen in de huidige sessie ophalen</span><span class="sxs-lookup"><span data-stu-id="766aa-115">Example 1: Get all aliases in the current session</span></span>

```
PS C:\> Get-Alias

CommandType     Name
-----------     ----
Alias           % -> ForEach-Object
Alias           ? -> Where-Object
Alias           ac -> Add-Content
Alias           asnp -> Add-PSSnapin
Alias           cat -> Get-Content
Alias           cd -> Set-Location
Alias           chdir -> Set-Location
Alias           clc -> Clear-Content
Alias           clear -> Clear-Host
Alias           clhy -> Clear-History
...
```

<span data-ttu-id="766aa-116">Met deze opdracht worden alle aliassen in de huidige sessie opgehaald.</span><span class="sxs-lookup"><span data-stu-id="766aa-116">This command gets all aliases in the current session.</span></span>

<span data-ttu-id="766aa-117">In de uitvoer ziet u de `<alias> -> <definition>` indeling die is geïntroduceerd in Windows Power shell 3,0.</span><span class="sxs-lookup"><span data-stu-id="766aa-117">The output shows the `<alias> -> <definition>` format that was introduced in Windows PowerShell 3.0.</span></span>
<span data-ttu-id="766aa-118">Deze indeling wordt alleen gebruikt voor aliassen die geen afbreek streepjes bevatten, omdat aliassen met afbreek streepjes doorgaans voorkeurs namen voor cmdlets en functions zijn, in plaats van bijnamen.</span><span class="sxs-lookup"><span data-stu-id="766aa-118">This format is used only for aliases that do not include hyphens, because aliases with hyphens are typically preferred names for cmdlets and functions, rather than nicknames.</span></span>

### <span data-ttu-id="766aa-119">Voor beeld 2: aliassen op naam ophalen</span><span class="sxs-lookup"><span data-stu-id="766aa-119">Example 2: Get aliases by name</span></span>

```powershell
Get-Alias -Name gp*, sp* -Exclude *ps
```

<span data-ttu-id="766aa-120">Met deze opdracht worden alle aliassen opgehaald die beginnen met GP of SP, met uitzonde ring van aliassen die eindigen op PS.</span><span class="sxs-lookup"><span data-stu-id="766aa-120">This command gets all aliases that begin with gp or sp, except for aliases that end with ps.</span></span>

### <span data-ttu-id="766aa-121">Voor beeld 3: aliassen voor een cmdlet ophalen</span><span class="sxs-lookup"><span data-stu-id="766aa-121">Example 3: Get aliases for a cmdlet</span></span>

```powershell
Get-Alias -Definition Get-ChildItem
```

<span data-ttu-id="766aa-122">Met deze opdracht worden de aliassen voor de Get-ChildItem-cmdlet opgehaald.</span><span class="sxs-lookup"><span data-stu-id="766aa-122">This command gets the aliases for the Get-ChildItem cmdlet.</span></span>

<span data-ttu-id="766aa-123">Standaard haalt de **Get-alias** -cmdlet de item naam op wanneer u de alias kent.</span><span class="sxs-lookup"><span data-stu-id="766aa-123">By default, the **Get-Alias** cmdlet gets the item name when you know the alias.</span></span>
<span data-ttu-id="766aa-124">De para meter *definitie* haalt de alias op wanneer u de naam van het item kent.</span><span class="sxs-lookup"><span data-stu-id="766aa-124">The *Definition* parameter gets the alias when you know the item name.</span></span>

### <span data-ttu-id="766aa-125">Voor beeld 4: aliassen ophalen op basis van eigenschap</span><span class="sxs-lookup"><span data-stu-id="766aa-125">Example 4: Get aliases by property</span></span>

```powershell
Get-Alias | Where-Object {$_.Options -Match "ReadOnly"}
```

<span data-ttu-id="766aa-126">Met deze opdracht worden alle aliassen opgehaald waarin de waarde van de eigenschap Options alleen-lezen is.</span><span class="sxs-lookup"><span data-stu-id="766aa-126">This command gets all aliases in which the value of the Options property is ReadOnly.</span></span>
<span data-ttu-id="766aa-127">Deze opdracht biedt een snelle manier om de aliassen te vinden die zijn ingebouwd in Power shell, omdat ze de optie ReadOnly hebben.</span><span class="sxs-lookup"><span data-stu-id="766aa-127">This command provides a quick way to find the aliases that are built into PowerShell, because they have the ReadOnly option.</span></span>

<span data-ttu-id="766aa-128">Opties is slechts één eigenschap van de AliasInfo-objecten die **Get-alias** krijgt.</span><span class="sxs-lookup"><span data-stu-id="766aa-128">Options is just one property of the AliasInfo objects that **Get-Alias** gets.</span></span>
<span data-ttu-id="766aa-129">Als u alle eigenschappen en methoden van AliasInfo-objecten wilt zoeken, typt u `Get-Alias | get-member` .</span><span class="sxs-lookup"><span data-stu-id="766aa-129">To find all properties and methods of AliasInfo objects, type `Get-Alias | get-member`.</span></span>

### <span data-ttu-id="766aa-130">Voor beeld 5: aliassen ophalen op naam en filteren op begin letter</span><span class="sxs-lookup"><span data-stu-id="766aa-130">Example 5: Get aliases by name and filter by beginning letter</span></span>

```powershell
Get-Alias -Definition "*-PSSession" -Exclude e* -Scope Global
```

<span data-ttu-id="766aa-131">In dit voor beeld worden aliassen opgehaald voor opdrachten die een naam hebben die eindigt op '-PSSession ', met uitzonde ring van die beginnen met ' e '.</span><span class="sxs-lookup"><span data-stu-id="766aa-131">This example gets aliases for commands that have names that end in "-PSSession", except for those that begin with "e".</span></span>

<span data-ttu-id="766aa-132">De opdracht maakt gebruik van de para meter *Scope* om de opdracht in het globale bereik toe te passen.</span><span class="sxs-lookup"><span data-stu-id="766aa-132">The command uses the *Scope* parameter to apply the command in the global scope.</span></span>
<span data-ttu-id="766aa-133">Dit is handig in scripts wanneer u de aliassen in de sessie wilt ophalen.</span><span class="sxs-lookup"><span data-stu-id="766aa-133">This is useful in scripts when you want to get the aliases in the session.</span></span>

## <span data-ttu-id="766aa-134">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="766aa-134">PARAMETERS</span></span>

### <span data-ttu-id="766aa-135">-Definitie</span><span class="sxs-lookup"><span data-stu-id="766aa-135">-Definition</span></span>

<span data-ttu-id="766aa-136">Hiermee worden de aliassen voor het opgegeven item opgehaald.</span><span class="sxs-lookup"><span data-stu-id="766aa-136">Gets the aliases for the specified item.</span></span>
<span data-ttu-id="766aa-137">Voer de naam in van een cmdlet, een functie, een script, een bestand of een uitvoerbaar bestand.</span><span class="sxs-lookup"><span data-stu-id="766aa-137">Enter the name of a cmdlet, function, script, file, or executable file.</span></span>

<span data-ttu-id="766aa-138">Deze para meter wordt *definitie* genoemd, omdat hiermee wordt gezocht naar de naam van het item in de eigenschap definitie van het object alias.</span><span class="sxs-lookup"><span data-stu-id="766aa-138">This parameter is called *Definition*, because it searches for the item name in the Definition property of the alias object.</span></span>

```yaml
Type: System.String[]
Parameter Sets: Definition
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: True
```

### <span data-ttu-id="766aa-139">-Uitsluiten</span><span class="sxs-lookup"><span data-stu-id="766aa-139">-Exclude</span></span>

<span data-ttu-id="766aa-140">De opgegeven items worden wegge laten.</span><span class="sxs-lookup"><span data-stu-id="766aa-140">Omits the specified items.</span></span>
<span data-ttu-id="766aa-141">De waarde van deze para meter komt in aanmerking voor de naam en de definitie parameters.</span><span class="sxs-lookup"><span data-stu-id="766aa-141">The value of this parameter qualifies the Name and Definition parameters.</span></span>
<span data-ttu-id="766aa-142">Voer een naam, een definitie of een patroon in, zoals ' s \* '.</span><span class="sxs-lookup"><span data-stu-id="766aa-142">Enter a name, a definition, or a pattern, such as "s\*".</span></span>
<span data-ttu-id="766aa-143">Joker tekens zijn toegestaan.</span><span class="sxs-lookup"><span data-stu-id="766aa-143">Wildcards are permitted.</span></span>

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

### <span data-ttu-id="766aa-144">-Name</span><span class="sxs-lookup"><span data-stu-id="766aa-144">-Name</span></span>

<span data-ttu-id="766aa-145">Hiermee geeft u de aliassen op die met deze cmdlet worden opgehaald.</span><span class="sxs-lookup"><span data-stu-id="766aa-145">Specifies the aliases that this cmdlet gets.</span></span>
<span data-ttu-id="766aa-146">Joker tekens zijn toegestaan.</span><span class="sxs-lookup"><span data-stu-id="766aa-146">Wildcards are permitted.</span></span>
<span data-ttu-id="766aa-147">`Get-Alias`Haalt standaard alle aliassen op die zijn gedefinieerd voor de huidige sessie.</span><span class="sxs-lookup"><span data-stu-id="766aa-147">By default, `Get-Alias` retrieves all aliases defined for the current session.</span></span>
<span data-ttu-id="766aa-148">De parameter naam **naam** is optioneel.</span><span class="sxs-lookup"><span data-stu-id="766aa-148">The parameter name **Name** is optional.</span></span>
<span data-ttu-id="766aa-149">U kunt ook de namen van de aliassen door sluizen naar `Get-Alias` .</span><span class="sxs-lookup"><span data-stu-id="766aa-149">You can also pipe alias names to `Get-Alias`.</span></span>

```yaml
Type: System.String[]
Parameter Sets: Default
Aliases:

Required: False
Position: 0
Default value: All aliases
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: True
```

### <span data-ttu-id="766aa-150">-Bereik</span><span class="sxs-lookup"><span data-stu-id="766aa-150">-Scope</span></span>

<span data-ttu-id="766aa-151">Hiermee geeft u het bereik waarvoor deze cmdlet aliassen ophaalt.</span><span class="sxs-lookup"><span data-stu-id="766aa-151">Specifies the scope for which this cmdlet gets aliases.</span></span>
<span data-ttu-id="766aa-152">De aanvaardbare waarden voor deze parameter zijn:</span><span class="sxs-lookup"><span data-stu-id="766aa-152">The acceptable values for this parameter are:</span></span>

- <span data-ttu-id="766aa-153">Globaal</span><span class="sxs-lookup"><span data-stu-id="766aa-153">Global</span></span>
- <span data-ttu-id="766aa-154">Lokaal</span><span class="sxs-lookup"><span data-stu-id="766aa-154">Local</span></span>
- <span data-ttu-id="766aa-155">Script</span><span class="sxs-lookup"><span data-stu-id="766aa-155">Script</span></span>
- <span data-ttu-id="766aa-156">Een getal dat relatief is ten opzichte van het huidige bereik (0 tot en met het aantal bereiken, waarbij 0 het huidige bereik is en 1 de bovenliggende scope)</span><span class="sxs-lookup"><span data-stu-id="766aa-156">A number relative to the current scope (0 through the number of scopes, where 0 is the current scope and 1 is its parent)</span></span>

<span data-ttu-id="766aa-157">Local is de standaard instelling.</span><span class="sxs-lookup"><span data-stu-id="766aa-157">Local is the default.</span></span>
<span data-ttu-id="766aa-158">Zie about_Scopes voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="766aa-158">For more information, see about_Scopes.</span></span>

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

### <span data-ttu-id="766aa-159">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="766aa-159">CommonParameters</span></span>

<span data-ttu-id="766aa-160">Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="766aa-160">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="766aa-161">Zie [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="766aa-161">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="766aa-162">INVOER</span><span class="sxs-lookup"><span data-stu-id="766aa-162">INPUTS</span></span>

### <span data-ttu-id="766aa-163">System. String</span><span class="sxs-lookup"><span data-stu-id="766aa-163">System.String</span></span>

<span data-ttu-id="766aa-164">U kunt de namen van de aliassen van een sluis naar **Get-alias**.</span><span class="sxs-lookup"><span data-stu-id="766aa-164">You can pipe alias names to **Get-Alias**.</span></span>

## <span data-ttu-id="766aa-165">UITVOER</span><span class="sxs-lookup"><span data-stu-id="766aa-165">OUTPUTS</span></span>

### <span data-ttu-id="766aa-166">System. Management. Automation. AliasInfo</span><span class="sxs-lookup"><span data-stu-id="766aa-166">System.Management.Automation.AliasInfo</span></span>

<span data-ttu-id="766aa-167">**Get-alias** retourneert een object dat staat voor elke alias.</span><span class="sxs-lookup"><span data-stu-id="766aa-167">**Get-Alias** returns an object that represents each alias.</span></span>
<span data-ttu-id="766aa-168">**Get-alias** retourneert hetzelfde object voor elke alias, maar Power shell gebruikt een op een pijl gebaseerde indeling om de namen van niet-afgebroken aliassen weer te geven.</span><span class="sxs-lookup"><span data-stu-id="766aa-168">**Get-Alias** returns the same object for every alias, but PowerShell uses an arrow-based format to display the names of non-hyphenated aliases.</span></span>

## <span data-ttu-id="766aa-169">OPMERKINGEN</span><span class="sxs-lookup"><span data-stu-id="766aa-169">NOTES</span></span>

- <span data-ttu-id="766aa-170">Als u een nieuwe alias wilt maken, gebruikt u Set-Alias of New alias.</span><span class="sxs-lookup"><span data-stu-id="766aa-170">To create a new alias, use Set-Alias or New-Alias.</span></span> <span data-ttu-id="766aa-171">Als u een alias wilt verwijderen, gebruikt u Remove-item.</span><span class="sxs-lookup"><span data-stu-id="766aa-171">To delete an alias, use Remove-Item.</span></span>
- <span data-ttu-id="766aa-172">De op de pijl gebaseerde alias naam indeling wordt niet gebruikt voor aliassen die een koppel teken bevatten.</span><span class="sxs-lookup"><span data-stu-id="766aa-172">The arrow-based alias name format is not used for aliases that include a hyphen.</span></span> <span data-ttu-id="766aa-173">Dit zijn waarschijnlijk de voorkeurs vervangende namen voor cmdlets en functions, in plaats van gebruikelijke afkortingen of bijnamen.</span><span class="sxs-lookup"><span data-stu-id="766aa-173">These are likely to be preferred substitute names for cmdlets and functions, instead of typical abbreviations or nicknames.</span></span>

## <span data-ttu-id="766aa-174">GERELATEERDE KOPPELINGEN</span><span class="sxs-lookup"><span data-stu-id="766aa-174">RELATED LINKS</span></span>

[<span data-ttu-id="766aa-175">Exporteren-alias</span><span class="sxs-lookup"><span data-stu-id="766aa-175">Export-Alias</span></span>](Export-Alias.md)

[<span data-ttu-id="766aa-176">Import-alias</span><span class="sxs-lookup"><span data-stu-id="766aa-176">Import-Alias</span></span>](Import-Alias.md)

[<span data-ttu-id="766aa-177">Nieuwe alias</span><span class="sxs-lookup"><span data-stu-id="766aa-177">New-Alias</span></span>](New-Alias.md)

[<span data-ttu-id="766aa-178">Set-alias</span><span class="sxs-lookup"><span data-stu-id="766aa-178">Set-Alias</span></span>](Set-Alias.md)

[<span data-ttu-id="766aa-179">Alias provider</span><span class="sxs-lookup"><span data-stu-id="766aa-179">Alias Provider</span></span>](../Microsoft.PowerShell.Core/About/about_Alias_Provider.md)

[<span data-ttu-id="766aa-180">about_Aliases</span><span class="sxs-lookup"><span data-stu-id="766aa-180">about_Aliases</span></span>](../Microsoft.PowerShell.Core/About/about_Aliases.md)

