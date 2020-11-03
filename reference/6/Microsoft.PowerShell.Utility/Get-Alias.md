---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/get-alias?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-Alias
ms.openlocfilehash: 08ff101019db6baa8b84f56e862f140a028e9539
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/07/2020
ms.locfileid: "93251116"
---
# <span data-ttu-id="23084-103">Get-Alias</span><span class="sxs-lookup"><span data-stu-id="23084-103">Get-Alias</span></span>

## <span data-ttu-id="23084-104">SAMENVATTING</span><span class="sxs-lookup"><span data-stu-id="23084-104">SYNOPSIS</span></span>
<span data-ttu-id="23084-105">Hiermee worden de aliassen opgehaald voor de huidige sessie.</span><span class="sxs-lookup"><span data-stu-id="23084-105">Gets the aliases for the current session.</span></span>

## <span data-ttu-id="23084-106">SYNTAXIS</span><span class="sxs-lookup"><span data-stu-id="23084-106">SYNTAX</span></span>

### <span data-ttu-id="23084-107">Standaard (standaard instelling)</span><span class="sxs-lookup"><span data-stu-id="23084-107">Default (Default)</span></span>

```
Get-Alias [[-Name] <String[]>] [-Exclude <String[]>] [-Scope <String>] [<CommonParameters>]
```

### <span data-ttu-id="23084-108">Definitie</span><span class="sxs-lookup"><span data-stu-id="23084-108">Definition</span></span>

```
Get-Alias [-Exclude <String[]>] [-Scope <String>] [-Definition <String[]>] [<CommonParameters>]
```

## <span data-ttu-id="23084-109">BESCHRIJVING</span><span class="sxs-lookup"><span data-stu-id="23084-109">DESCRIPTION</span></span>

<span data-ttu-id="23084-110">Met de cmdlet **Get-alias** worden de aliassen in de huidige sessie opgehaald.</span><span class="sxs-lookup"><span data-stu-id="23084-110">The **Get-Alias** cmdlet gets the aliases in the current session.</span></span>
<span data-ttu-id="23084-111">Dit omvat ingebouwde aliassen, aliassen die u hebt ingesteld of geïmporteerd en aliassen die u hebt toegevoegd aan uw Power shell-profiel.</span><span class="sxs-lookup"><span data-stu-id="23084-111">This includes built-in aliases, aliases that you have set or imported, and aliases that you have added to your PowerShell profile.</span></span>

<span data-ttu-id="23084-112">**Get-alias** gebruikt standaard een alias en retourneert de naam van de opdracht.</span><span class="sxs-lookup"><span data-stu-id="23084-112">By default, **Get-Alias** takes an alias and returns the command name.</span></span>
<span data-ttu-id="23084-113">Wanneer u de para meter *definitie* gebruikt, neemt **Get-alias** de naam van een opdracht en worden de aliassen ervan geretourneerd.</span><span class="sxs-lookup"><span data-stu-id="23084-113">When you use the *Definition* parameter, **Get-Alias** takes a command name and returns its aliases.</span></span>

<span data-ttu-id="23084-114">Vanaf Windows Power Shell 3,0 worden met **Get-alias** niet-afgebroken alias namen weer gegeven in een `<alias> -> <definition>` indeling zodat u de informatie die u nodig hebt, nog gemakkelijker kunt vinden.</span><span class="sxs-lookup"><span data-stu-id="23084-114">Beginning in Windows PowerShell 3.0, **Get-Alias** displays non-hyphenated alias names in an `<alias> -> <definition>` format to make it even easier to find the information that you need.</span></span>

## <span data-ttu-id="23084-115">VOORBEELDEN</span><span class="sxs-lookup"><span data-stu-id="23084-115">EXAMPLES</span></span>

### <span data-ttu-id="23084-116">Voor beeld 1: alle aliassen in de huidige sessie ophalen</span><span class="sxs-lookup"><span data-stu-id="23084-116">Example 1: Get all aliases in the current session</span></span>

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

<span data-ttu-id="23084-117">Met deze opdracht worden alle aliassen in de huidige sessie opgehaald.</span><span class="sxs-lookup"><span data-stu-id="23084-117">This command gets all aliases in the current session.</span></span>

<span data-ttu-id="23084-118">In de uitvoer ziet u de `<alias> -> <definition>` indeling die is geïntroduceerd in Windows Power shell 3,0.</span><span class="sxs-lookup"><span data-stu-id="23084-118">The output shows the `<alias> -> <definition>` format that was introduced in Windows PowerShell 3.0.</span></span>
<span data-ttu-id="23084-119">Deze indeling wordt alleen gebruikt voor aliassen die geen afbreek streepjes bevatten, omdat aliassen met afbreek streepjes doorgaans voorkeurs namen voor cmdlets en functions zijn, in plaats van bijnamen.</span><span class="sxs-lookup"><span data-stu-id="23084-119">This format is used only for aliases that do not include hyphens, because aliases with hyphens are typically preferred names for cmdlets and functions, rather than nicknames.</span></span>

### <span data-ttu-id="23084-120">Voor beeld 2: aliassen op naam ophalen</span><span class="sxs-lookup"><span data-stu-id="23084-120">Example 2: Get aliases by name</span></span>

```powershell
Get-Alias -Name gp*, sp* -Exclude *ps
```

<span data-ttu-id="23084-121">Met deze opdracht worden alle aliassen opgehaald die beginnen met GP of SP, met uitzonde ring van aliassen die eindigen op PS.</span><span class="sxs-lookup"><span data-stu-id="23084-121">This command gets all aliases that begin with gp or sp, except for aliases that end with ps.</span></span>

### <span data-ttu-id="23084-122">Voor beeld 3: aliassen voor een cmdlet ophalen</span><span class="sxs-lookup"><span data-stu-id="23084-122">Example 3: Get aliases for a cmdlet</span></span>

```powershell
Get-Alias -Definition Get-ChildItem
```

<span data-ttu-id="23084-123">Met deze opdracht worden de aliassen voor de Get-ChildItem-cmdlet opgehaald.</span><span class="sxs-lookup"><span data-stu-id="23084-123">This command gets the aliases for the Get-ChildItem cmdlet.</span></span>

<span data-ttu-id="23084-124">Standaard haalt de **Get-alias** -cmdlet de item naam op wanneer u de alias kent.</span><span class="sxs-lookup"><span data-stu-id="23084-124">By default, the **Get-Alias** cmdlet gets the item name when you know the alias.</span></span>
<span data-ttu-id="23084-125">De para meter *definitie* haalt de alias op wanneer u de naam van het item kent.</span><span class="sxs-lookup"><span data-stu-id="23084-125">The *Definition* parameter gets the alias when you know the item name.</span></span>

### <span data-ttu-id="23084-126">Voor beeld 4: aliassen ophalen op basis van eigenschap</span><span class="sxs-lookup"><span data-stu-id="23084-126">Example 4: Get aliases by property</span></span>

```powershell
Get-Alias | Where-Object {$_.Options -Match "ReadOnly"}
```

<span data-ttu-id="23084-127">Met deze opdracht worden alle aliassen opgehaald waarin de waarde van de eigenschap Options alleen-lezen is.</span><span class="sxs-lookup"><span data-stu-id="23084-127">This command gets all aliases in which the value of the Options property is ReadOnly.</span></span>
<span data-ttu-id="23084-128">Deze opdracht biedt een snelle manier om de aliassen te vinden die zijn ingebouwd in Power shell, omdat ze de optie ReadOnly hebben.</span><span class="sxs-lookup"><span data-stu-id="23084-128">This command provides a quick way to find the aliases that are built into PowerShell, because they have the ReadOnly option.</span></span>

<span data-ttu-id="23084-129">Opties is slechts één eigenschap van de AliasInfo-objecten die **Get-alias** krijgt.</span><span class="sxs-lookup"><span data-stu-id="23084-129">Options is just one property of the AliasInfo objects that **Get-Alias** gets.</span></span>
<span data-ttu-id="23084-130">Als u alle eigenschappen en methoden van AliasInfo-objecten wilt zoeken, typt u `Get-Alias | get-member` .</span><span class="sxs-lookup"><span data-stu-id="23084-130">To find all properties and methods of AliasInfo objects, type `Get-Alias | get-member`.</span></span>

### <span data-ttu-id="23084-131">Voor beeld 5: aliassen ophalen op naam en filteren op begin letter</span><span class="sxs-lookup"><span data-stu-id="23084-131">Example 5: Get aliases by name and filter by beginning letter</span></span>

```powershell
Get-Alias -Definition "*-PSSession" -Exclude e* -Scope Global
```

<span data-ttu-id="23084-132">In dit voor beeld worden aliassen opgehaald voor opdrachten die een naam hebben die eindigt op '-PSSession ', met uitzonde ring van die beginnen met ' e '.</span><span class="sxs-lookup"><span data-stu-id="23084-132">This example gets aliases for commands that have names that end in "-PSSession", except for those that begin with "e".</span></span>

<span data-ttu-id="23084-133">De opdracht maakt gebruik van de para meter *Scope* om de opdracht in het globale bereik toe te passen.</span><span class="sxs-lookup"><span data-stu-id="23084-133">The command uses the *Scope* parameter to apply the command in the global scope.</span></span>
<span data-ttu-id="23084-134">Dit is handig in scripts wanneer u de aliassen in de sessie wilt ophalen.</span><span class="sxs-lookup"><span data-stu-id="23084-134">This is useful in scripts when you want to get the aliases in the session.</span></span>

## <span data-ttu-id="23084-135">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="23084-135">PARAMETERS</span></span>

### <span data-ttu-id="23084-136">-Definitie</span><span class="sxs-lookup"><span data-stu-id="23084-136">-Definition</span></span>

<span data-ttu-id="23084-137">Hiermee worden de aliassen voor het opgegeven item opgehaald.</span><span class="sxs-lookup"><span data-stu-id="23084-137">Gets the aliases for the specified item.</span></span>
<span data-ttu-id="23084-138">Voer de naam in van een cmdlet, een functie, een script, een bestand of een uitvoerbaar bestand.</span><span class="sxs-lookup"><span data-stu-id="23084-138">Enter the name of a cmdlet, function, script, file, or executable file.</span></span>

<span data-ttu-id="23084-139">Deze para meter wordt *definitie* genoemd, omdat hiermee wordt gezocht naar de naam van het item in de eigenschap definitie van het object alias.</span><span class="sxs-lookup"><span data-stu-id="23084-139">This parameter is called *Definition* , because it searches for the item name in the Definition property of the alias object.</span></span>

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

### <span data-ttu-id="23084-140">-Uitsluiten</span><span class="sxs-lookup"><span data-stu-id="23084-140">-Exclude</span></span>

<span data-ttu-id="23084-141">De opgegeven items worden wegge laten.</span><span class="sxs-lookup"><span data-stu-id="23084-141">Omits the specified items.</span></span>
<span data-ttu-id="23084-142">De waarde van deze para meter komt in aanmerking voor de naam en de definitie parameters.</span><span class="sxs-lookup"><span data-stu-id="23084-142">The value of this parameter qualifies the Name and Definition parameters.</span></span>
<span data-ttu-id="23084-143">Voer een naam, een definitie of een patroon in, zoals ' s \* '.</span><span class="sxs-lookup"><span data-stu-id="23084-143">Enter a name, a definition, or a pattern, such as "s\*".</span></span>
<span data-ttu-id="23084-144">Joker tekens zijn toegestaan.</span><span class="sxs-lookup"><span data-stu-id="23084-144">Wildcards are permitted.</span></span>

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

### <span data-ttu-id="23084-145">-Name</span><span class="sxs-lookup"><span data-stu-id="23084-145">-Name</span></span>

<span data-ttu-id="23084-146">Hiermee geeft u de aliassen op die met deze cmdlet worden opgehaald.</span><span class="sxs-lookup"><span data-stu-id="23084-146">Specifies the aliases that this cmdlet gets.</span></span>
<span data-ttu-id="23084-147">Joker tekens zijn toegestaan.</span><span class="sxs-lookup"><span data-stu-id="23084-147">Wildcards are permitted.</span></span>
<span data-ttu-id="23084-148">`Get-Alias`Haalt standaard alle aliassen op die zijn gedefinieerd voor de huidige sessie.</span><span class="sxs-lookup"><span data-stu-id="23084-148">By default, `Get-Alias` retrieves all aliases defined for the current session.</span></span>
<span data-ttu-id="23084-149">De parameter naam **naam** is optioneel.</span><span class="sxs-lookup"><span data-stu-id="23084-149">The parameter name **Name** is optional.</span></span>
<span data-ttu-id="23084-150">U kunt ook de namen van de aliassen door sluizen naar `Get-Alias` .</span><span class="sxs-lookup"><span data-stu-id="23084-150">You can also pipe alias names to `Get-Alias`.</span></span>

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

### <span data-ttu-id="23084-151">-Bereik</span><span class="sxs-lookup"><span data-stu-id="23084-151">-Scope</span></span>

<span data-ttu-id="23084-152">Hiermee geeft u het bereik waarvoor deze cmdlet aliassen ophaalt.</span><span class="sxs-lookup"><span data-stu-id="23084-152">Specifies the scope for which this cmdlet gets aliases.</span></span>
<span data-ttu-id="23084-153">De aanvaardbare waarden voor deze parameter zijn:</span><span class="sxs-lookup"><span data-stu-id="23084-153">The acceptable values for this parameter are:</span></span>

- <span data-ttu-id="23084-154">Globaal</span><span class="sxs-lookup"><span data-stu-id="23084-154">Global</span></span>
- <span data-ttu-id="23084-155">Lokaal</span><span class="sxs-lookup"><span data-stu-id="23084-155">Local</span></span>
- <span data-ttu-id="23084-156">Script</span><span class="sxs-lookup"><span data-stu-id="23084-156">Script</span></span>
- <span data-ttu-id="23084-157">Een getal dat relatief is ten opzichte van het huidige bereik (0 tot en met het aantal bereiken, waarbij 0 het huidige bereik is en 1 de bovenliggende scope)</span><span class="sxs-lookup"><span data-stu-id="23084-157">A number relative to the current scope (0 through the number of scopes, where 0 is the current scope and 1 is its parent)</span></span>

<span data-ttu-id="23084-158">Local is de standaard instelling.</span><span class="sxs-lookup"><span data-stu-id="23084-158">Local is the default.</span></span>
<span data-ttu-id="23084-159">Zie about_Scopes voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="23084-159">For more information, see about_Scopes.</span></span>

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

### <span data-ttu-id="23084-160">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="23084-160">CommonParameters</span></span>

<span data-ttu-id="23084-161">Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="23084-161">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="23084-162">Zie [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="23084-162">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="23084-163">INVOER</span><span class="sxs-lookup"><span data-stu-id="23084-163">INPUTS</span></span>

### <span data-ttu-id="23084-164">System. String</span><span class="sxs-lookup"><span data-stu-id="23084-164">System.String</span></span>

<span data-ttu-id="23084-165">U kunt de namen van de aliassen van een sluis naar **Get-alias**.</span><span class="sxs-lookup"><span data-stu-id="23084-165">You can pipe alias names to **Get-Alias**.</span></span>

## <span data-ttu-id="23084-166">UITVOER</span><span class="sxs-lookup"><span data-stu-id="23084-166">OUTPUTS</span></span>

### <span data-ttu-id="23084-167">System. Management. Automation. AliasInfo</span><span class="sxs-lookup"><span data-stu-id="23084-167">System.Management.Automation.AliasInfo</span></span>

<span data-ttu-id="23084-168">**Get-alias** retourneert een object dat staat voor elke alias.</span><span class="sxs-lookup"><span data-stu-id="23084-168">**Get-Alias** returns an object that represents each alias.</span></span>
<span data-ttu-id="23084-169">**Get-alias** retourneert hetzelfde object voor elke alias, maar Power shell gebruikt een op een pijl gebaseerde indeling om de namen van niet-afgebroken aliassen weer te geven.</span><span class="sxs-lookup"><span data-stu-id="23084-169">**Get-Alias** returns the same object for every alias, but PowerShell uses an arrow-based format to display the names of non-hyphenated aliases.</span></span>

## <span data-ttu-id="23084-170">OPMERKINGEN</span><span class="sxs-lookup"><span data-stu-id="23084-170">NOTES</span></span>

- <span data-ttu-id="23084-171">Als u een nieuwe alias wilt maken, gebruikt u Set-Alias of New alias.</span><span class="sxs-lookup"><span data-stu-id="23084-171">To create a new alias, use Set-Alias or New-Alias.</span></span> <span data-ttu-id="23084-172">Als u een alias wilt verwijderen, gebruikt u Remove-item.</span><span class="sxs-lookup"><span data-stu-id="23084-172">To delete an alias, use Remove-Item.</span></span>
- <span data-ttu-id="23084-173">De op de pijl gebaseerde alias naam indeling wordt niet gebruikt voor aliassen die een koppel teken bevatten.</span><span class="sxs-lookup"><span data-stu-id="23084-173">The arrow-based alias name format is not used for aliases that include a hyphen.</span></span> <span data-ttu-id="23084-174">Dit zijn waarschijnlijk de voorkeurs vervangende namen voor cmdlets en functions, in plaats van gebruikelijke afkortingen of bijnamen.</span><span class="sxs-lookup"><span data-stu-id="23084-174">These are likely to be preferred substitute names for cmdlets and functions, instead of typical abbreviations or nicknames.</span></span>

## <span data-ttu-id="23084-175">GERELATEERDE KOPPELINGEN</span><span class="sxs-lookup"><span data-stu-id="23084-175">RELATED LINKS</span></span>

[<span data-ttu-id="23084-176">Exporteren-alias</span><span class="sxs-lookup"><span data-stu-id="23084-176">Export-Alias</span></span>](Export-Alias.md)

[<span data-ttu-id="23084-177">Import-alias</span><span class="sxs-lookup"><span data-stu-id="23084-177">Import-Alias</span></span>](Import-Alias.md)

[<span data-ttu-id="23084-178">Nieuwe alias</span><span class="sxs-lookup"><span data-stu-id="23084-178">New-Alias</span></span>](New-Alias.md)

[<span data-ttu-id="23084-179">Set-alias</span><span class="sxs-lookup"><span data-stu-id="23084-179">Set-Alias</span></span>](Set-Alias.md)

[<span data-ttu-id="23084-180">Alias provider</span><span class="sxs-lookup"><span data-stu-id="23084-180">Alias Provider</span></span>](../Microsoft.PowerShell.Core/About/about_Alias_Provider.md)

[<span data-ttu-id="23084-181">about_Aliases</span><span class="sxs-lookup"><span data-stu-id="23084-181">about_Aliases</span></span>](../Microsoft.PowerShell.Core/About/about_Aliases.md)
