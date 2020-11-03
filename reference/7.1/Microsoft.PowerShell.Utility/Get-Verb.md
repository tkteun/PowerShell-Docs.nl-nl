---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 09/07/2018
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/get-verb?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-Verb
ms.openlocfilehash: 27434dfbc76d26724b34fe19fd143a7c52a14e90
ms.sourcegitcommit: 7d052985c20761fdf4c6d7ce4e04df4c551c36a3
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 08/11/2020
ms.locfileid: "93251813"
---
# <span data-ttu-id="da8d9-103">Get-Verb</span><span class="sxs-lookup"><span data-stu-id="da8d9-103">Get-Verb</span></span>

## <span data-ttu-id="da8d9-104">SAMENVATTING</span><span class="sxs-lookup"><span data-stu-id="da8d9-104">SYNOPSIS</span></span>
<span data-ttu-id="da8d9-105">Hiermee worden goedgekeurde Power shell-woorden opgehaald.</span><span class="sxs-lookup"><span data-stu-id="da8d9-105">Gets approved PowerShell verbs.</span></span>

## <span data-ttu-id="da8d9-106">SYNTAXIS</span><span class="sxs-lookup"><span data-stu-id="da8d9-106">SYNTAX</span></span>

```
Get-Verb [[-Verb] <String[]>] [[-Group] <String[]>] [<CommonParameters>]
```

## <span data-ttu-id="da8d9-107">BESCHRIJVING</span><span class="sxs-lookup"><span data-stu-id="da8d9-107">DESCRIPTION</span></span>

<span data-ttu-id="da8d9-108">De `Get-Verb` functie haalt werk woorden op die zijn goedgekeurd voor gebruik in Power shell-opdrachten.</span><span class="sxs-lookup"><span data-stu-id="da8d9-108">The `Get-Verb` function gets verbs that are approved for use in PowerShell commands.</span></span>

<span data-ttu-id="da8d9-109">U wordt aangeraden de Power shell-cmdlet en functie namen de `Verb-Noun` indeling te bieden en een goedgekeurde term te bevatten.</span><span class="sxs-lookup"><span data-stu-id="da8d9-109">It is recommended that PowerShell cmdlet and function names have the `Verb-Noun` format and include an approved verb.</span></span> <span data-ttu-id="da8d9-110">Met deze procedure worden opdracht namen consistent, voorspelbaar en gemakkelijker te gebruiken.</span><span class="sxs-lookup"><span data-stu-id="da8d9-110">This practice makes command names more consistent, predictable, and easier to use.</span></span>

<span data-ttu-id="da8d9-111">Opdrachten die gebruikmaken van niet-goedgekeurde woorden, worden nog steeds uitgevoerd in Power shell.</span><span class="sxs-lookup"><span data-stu-id="da8d9-111">Commands that use unapproved verbs, still run in PowerShell.</span></span> <span data-ttu-id="da8d9-112">Wanneer u echter een module importeert die een opdracht met een niet-goedgekeurde term in de naam bevat, `Import-Module` wordt er een waarschuwings bericht weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="da8d9-112">However, when you import a module that includes a command with an unapproved verb in its name, the `Import-Module` command displays a warning message.</span></span>

> [!NOTE]
> <span data-ttu-id="da8d9-113">De woorden lijst die `Get-Verb` wordt geretourneerd, is mogelijk niet volledig.</span><span class="sxs-lookup"><span data-stu-id="da8d9-113">The verb list that `Get-Verb` returns might not be complete.</span></span> <span data-ttu-id="da8d9-114">Zie [goedgekeurde werk woorden](../../docs-conceptual/developer/cmdlet/approved-verbs-for-windows-powershell-commands.md) in de Microsoft docs voor een bijgewerkte lijst met goedgekeurde Power shell-termen met beschrijvingen.</span><span class="sxs-lookup"><span data-stu-id="da8d9-114">For an updated list of approved PowerShell verbs with descriptions, see [Approved Verbs](../../docs-conceptual/developer/cmdlet/approved-verbs-for-windows-powershell-commands.md) in the Microsoft Docs.</span></span>

## <span data-ttu-id="da8d9-115">Voorbeelden</span><span class="sxs-lookup"><span data-stu-id="da8d9-115">Examples</span></span>

### <span data-ttu-id="da8d9-116">Voor beeld 1: een lijst met alle woorden ophalen</span><span class="sxs-lookup"><span data-stu-id="da8d9-116">Example 1 - Get a list of all verbs</span></span>

```powershell
Get-Verb
```

### <span data-ttu-id="da8d9-117">Voor beeld 2: een lijst met goedgekeurde woorden ophalen die beginnen met ' ongedaan maken '</span><span class="sxs-lookup"><span data-stu-id="da8d9-117">Example 2 - Get a list of approved verbs that begin with "un"</span></span>

```powershell
Get-Verb un*
```

```Output
Verb       AliasPrefix Group     Description
----       ----------- -----     -----------
Undo       un          Common    Sets a resource to its previous state
Unlock     uk          Common    Releases a resource that was locked
Unpublish  ub          Data      Makes a resource unavailable to others
Uninstall  us          Lifecycle Removes a resource from an indicated location
Unregister ur          Lifecycle Removes the entry for a resource from a repository
Unblock    ul          Security  Removes restrictions to a resource
Unprotect  up          Security  Removes safeguards from a resource that were added to prevent it from attack or loss
```

### <span data-ttu-id="da8d9-118">Voor beeld 3: alle goedgekeurde werk woorden ophalen in de beveiligings groep</span><span class="sxs-lookup"><span data-stu-id="da8d9-118">Example 3 - Get all approved verbs in the Security group</span></span>

```powershell
Get-Verb -Group Security
```

```Output
Verb      AliasPrefix Group    Description
----      ----------- -----    -----------
Block     bl          Security Restricts access to a resource
Grant     gr          Security Allows access to a resource
Protect   pt          Security Safeguards a resource from attack or loss
Revoke    rk          Security Specifies an action that does not allow access to a resource
Unblock   ul          Security Removes restrictions to a resource
Unprotect up          Security Removes safeguards from a resource that were added to prevent it from attack or loss
```

### <span data-ttu-id="da8d9-119">Voor beeld 4: Hiermee vindt u alle opdrachten in een module die een niet-goedgekeurde term hebben</span><span class="sxs-lookup"><span data-stu-id="da8d9-119">Example 4 - Finds all commands in a module that have unapproved verbs</span></span>

```powershell
Get-Command -Module Microsoft.PowerShell.Utility | Where-Object Verb -NotIn (Get-Verb).Verb
```

```Output
CommandType     Name            Version    Source
-----------     ----            -------    ------
Cmdlet          Sort-Object     3.1.0.0    Microsoft.PowerShell.Utility
Cmdlet          Tee-Object      3.1.0.0    Microsoft.PowerShell.Utility
```

## <span data-ttu-id="da8d9-120">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="da8d9-120">PARAMETERS</span></span>

### <span data-ttu-id="da8d9-121">-Verb</span><span class="sxs-lookup"><span data-stu-id="da8d9-121">-Verb</span></span>

<span data-ttu-id="da8d9-122">Hiermee worden alleen de opgegeven termen opgehaald.</span><span class="sxs-lookup"><span data-stu-id="da8d9-122">Gets only the specified verbs.</span></span> <span data-ttu-id="da8d9-123">Voer de naam van een werk woord of een naam patroon in.</span><span class="sxs-lookup"><span data-stu-id="da8d9-123">Enter the name of a verb or a name pattern.</span></span> <span data-ttu-id="da8d9-124">Joker tekens zijn toegestaan.</span><span class="sxs-lookup"><span data-stu-id="da8d9-124">Wildcards are allowed.</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:
Accepted values: Common, Communications, Data, Diagnostic, Lifecycle, Other, Security

Required: False
Position: 1
Default value: All groups
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: True
```

### <span data-ttu-id="da8d9-125">-Group</span><span class="sxs-lookup"><span data-stu-id="da8d9-125">-Group</span></span>

<span data-ttu-id="da8d9-126">Hiermee worden alleen de opgegeven groepen opgehaald.</span><span class="sxs-lookup"><span data-stu-id="da8d9-126">Gets only the specified groups.</span></span> <span data-ttu-id="da8d9-127">Voer de naam van een groep in.</span><span class="sxs-lookup"><span data-stu-id="da8d9-127">Enter the name of a group.</span></span> <span data-ttu-id="da8d9-128">Joker tekens zijn niet toegestaan.</span><span class="sxs-lookup"><span data-stu-id="da8d9-128">Wildcards are not allowed.</span></span>

<span data-ttu-id="da8d9-129">Deze para meter is geïntroduceerd in Power shell 6,0.</span><span class="sxs-lookup"><span data-stu-id="da8d9-129">This parameter was introduced in PowerShell 6.0.</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: 0
Default value: All verbs
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="da8d9-130">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="da8d9-130">CommonParameters</span></span>

<span data-ttu-id="da8d9-131">Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="da8d9-131">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="da8d9-132">Zie [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="da8d9-132">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="da8d9-133">INVOER</span><span class="sxs-lookup"><span data-stu-id="da8d9-133">INPUTS</span></span>

### <span data-ttu-id="da8d9-134">Geen</span><span class="sxs-lookup"><span data-stu-id="da8d9-134">None</span></span>

## <span data-ttu-id="da8d9-135">UITVOER</span><span class="sxs-lookup"><span data-stu-id="da8d9-135">OUTPUTS</span></span>

### <span data-ttu-id="da8d9-136">System. Management. Automation. VerbInfo</span><span class="sxs-lookup"><span data-stu-id="da8d9-136">System.Management.Automation.VerbInfo</span></span>

## <span data-ttu-id="da8d9-137">OPMERKINGEN</span><span class="sxs-lookup"><span data-stu-id="da8d9-137">NOTES</span></span>

<span data-ttu-id="da8d9-138">Power shell-werk woorden worden toegewezen aan een groep op basis van het meest voorkomende gebruik.</span><span class="sxs-lookup"><span data-stu-id="da8d9-138">PowerShell verbs are assigned to a group based on their most common use.</span></span> <span data-ttu-id="da8d9-139">De groepen zijn ontworpen om de werk woorden gemakkelijk te vinden en te vergelijken, en om het gebruik ervan te beperken.</span><span class="sxs-lookup"><span data-stu-id="da8d9-139">The groups are designed to make the verbs easy to find and compare, not to restrict their use.</span></span> <span data-ttu-id="da8d9-140">U kunt elk goedgekeurd werk woord voor elk type opdracht gebruiken.</span><span class="sxs-lookup"><span data-stu-id="da8d9-140">You can use any approved verb for any type of command.</span></span>

<span data-ttu-id="da8d9-141">Elke Power shell-term wordt toegewezen aan een van de volgende groepen.</span><span class="sxs-lookup"><span data-stu-id="da8d9-141">Each PowerShell verb is assigned to one of the following groups.</span></span>

- <span data-ttu-id="da8d9-142">Algemeen: Definieer algemene acties die van toepassing kunnen zijn op bijna elke cmdlet, zoals toevoegen.</span><span class="sxs-lookup"><span data-stu-id="da8d9-142">Common: Define generic actions that can apply to almost any cmdlet, such as Add.</span></span>
- <span data-ttu-id="da8d9-143">Communicatie: acties definiëren die van toepassing zijn op de communicatie, zoals verbinding maken.</span><span class="sxs-lookup"><span data-stu-id="da8d9-143">Communications: Define actions that apply to communications, such as Connect.</span></span>
- <span data-ttu-id="da8d9-144">Gegevens: acties definiëren die van toepassing zijn op de verwerking van gegevens, zoals back-up.</span><span class="sxs-lookup"><span data-stu-id="da8d9-144">Data: Define actions that apply to data handling, such as Backup.</span></span>
- <span data-ttu-id="da8d9-145">Diagnose: acties definiëren die van toepassing zijn op diagnostische gegevens, zoals fout opsporing.</span><span class="sxs-lookup"><span data-stu-id="da8d9-145">Diagnostic: Define actions that apply to diagnostics, such as Debug.</span></span>
- <span data-ttu-id="da8d9-146">Levenscyclus: Definieer acties die van toepassing zijn op de levens cyclus van een cmdlet, zoals voltooid.</span><span class="sxs-lookup"><span data-stu-id="da8d9-146">Lifecycle: Define actions that apply to the lifecycle of a cmdlet, such as Complete.</span></span>
- <span data-ttu-id="da8d9-147">Beveiliging: Definieer acties die van toepassing zijn op de beveiliging, zoals intrekken.</span><span class="sxs-lookup"><span data-stu-id="da8d9-147">Security: Define actions that apply to security, such as Revoke.</span></span>
- <span data-ttu-id="da8d9-148">Overige: andere typen acties definiëren.</span><span class="sxs-lookup"><span data-stu-id="da8d9-148">Other: Define other types of actions.</span></span>

<span data-ttu-id="da8d9-149">Sommige cmdlets die zijn geïnstalleerd met Power shell, zoals `Tee-Object` en `Where-Object` , gebruiken niet-goedgekeurde werk woorden.</span><span class="sxs-lookup"><span data-stu-id="da8d9-149">Some of the cmdlets that are installed with PowerShell, such as `Tee-Object` and `Where-Object`, use unapproved verbs.</span></span> <span data-ttu-id="da8d9-150">Deze cmdlets zijn historische uitzonde ringen en hun werk woorden worden als **gereserveerd** geclassificeerd.</span><span class="sxs-lookup"><span data-stu-id="da8d9-150">These cmdlets are historic exceptions and their verbs are classified as **reserved**.</span></span>

## <span data-ttu-id="da8d9-151">GERELATEERDE KOPPELINGEN</span><span class="sxs-lookup"><span data-stu-id="da8d9-151">RELATED LINKS</span></span>

[<span data-ttu-id="da8d9-152">Import-module</span><span class="sxs-lookup"><span data-stu-id="da8d9-152">Import-Module</span></span>](../microsoft.powershell.core/import-module.md)

