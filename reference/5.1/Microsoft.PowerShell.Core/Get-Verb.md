---
external help file: System.Management.Automation.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
ms.date: 09/07/2018
Module Name: Microsoft.PowerShell.Core
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/functions/get-verb?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-Verb
ms.openlocfilehash: 4474bb50c2bf3be10e72d2554190208e956f9040
ms.sourcegitcommit: 7d052985c20761fdf4c6d7ce4e04df4c551c36a3
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 08/11/2020
ms.locfileid: "93251807"
---
# <span data-ttu-id="e2397-103">Get-Verb</span><span class="sxs-lookup"><span data-stu-id="e2397-103">Get-Verb</span></span>

## <span data-ttu-id="e2397-104">SAMENVATTING</span><span class="sxs-lookup"><span data-stu-id="e2397-104">SYNOPSIS</span></span>
<span data-ttu-id="e2397-105">Hiermee worden goedgekeurde Power shell-woorden opgehaald.</span><span class="sxs-lookup"><span data-stu-id="e2397-105">Gets approved PowerShell verbs.</span></span>

## <span data-ttu-id="e2397-106">SYNTAXIS</span><span class="sxs-lookup"><span data-stu-id="e2397-106">SYNTAX</span></span>

```
Get-Verb [[-verb] <String[]>] [<CommonParameters>]
```

## <span data-ttu-id="e2397-107">BESCHRIJVING</span><span class="sxs-lookup"><span data-stu-id="e2397-107">DESCRIPTION</span></span>

<span data-ttu-id="e2397-108">De `Get-Verb` functie haalt werk woorden op die zijn goedgekeurd voor gebruik in Power shell-opdrachten.</span><span class="sxs-lookup"><span data-stu-id="e2397-108">The `Get-Verb` function gets verbs that are approved for use in PowerShell commands.</span></span>

<span data-ttu-id="e2397-109">Power shell raadt cmdlet-en functie namen aan de Verb-Noun-indeling en een goedgekeurde term toe.</span><span class="sxs-lookup"><span data-stu-id="e2397-109">PowerShell recommends cmdlet and function names have the Verb-Noun format and include an approved verb.</span></span> <span data-ttu-id="e2397-110">Met deze procedure worden opdracht namen consistent, voorspelbaar en gemakkelijker te gebruiken.</span><span class="sxs-lookup"><span data-stu-id="e2397-110">This practice makes command names more consistent, predictable, and easier to use.</span></span>

<span data-ttu-id="e2397-111">Opdrachten die gebruikmaken van niet-goedgekeurde woorden worden uitgevoerd in Power shell.</span><span class="sxs-lookup"><span data-stu-id="e2397-111">Commands that use unapproved verbs run in PowerShell.</span></span> <span data-ttu-id="e2397-112">Wanneer u echter een module importeert die een opdracht met een niet-goedgekeurde term in de naam bevat, `Import-Module` wordt er een waarschuwings bericht weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="e2397-112">However, when you import a module that includes a command with an unapproved verb in its name, the `Import-Module` command displays a warning message.</span></span>

> [!NOTE]
> <span data-ttu-id="e2397-113">De woorden lijst die `Get-Verb` wordt geretourneerd, is mogelijk niet volledig.</span><span class="sxs-lookup"><span data-stu-id="e2397-113">The verb list that `Get-Verb` returns might not be complete.</span></span> <span data-ttu-id="e2397-114">Zie [goedgekeurde werk woorden](../../docs-conceptual/developer/cmdlet/approved-verbs-for-windows-powershell-commands.md) in de Microsoft docs voor een bijgewerkte lijst met goedgekeurde Power shell-termen met beschrijvingen.</span><span class="sxs-lookup"><span data-stu-id="e2397-114">For an updated list of approved PowerShell verbs with descriptions, see [Approved Verbs](../../docs-conceptual/developer/cmdlet/approved-verbs-for-windows-powershell-commands.md) in the Microsoft Docs.</span></span>

## <span data-ttu-id="e2397-115">VOORBEELDEN</span><span class="sxs-lookup"><span data-stu-id="e2397-115">EXAMPLES</span></span>

### <span data-ttu-id="e2397-116">Voor beeld 1: een lijst met alle woorden ophalen</span><span class="sxs-lookup"><span data-stu-id="e2397-116">Example 1 - Get a list of all verbs</span></span>

```powershell
Get-Verb
```

### <span data-ttu-id="e2397-117">Voor beeld 2: een lijst met goedgekeurde woorden ophalen die beginnen met ' ongedaan maken '</span><span class="sxs-lookup"><span data-stu-id="e2397-117">Example 2 - Get a list of approved verbs that begin with "un"</span></span>

```powershell
Get-Verb un*
```

```Output
Verb                 Group
----                 -----
Undo                 Common
Unlock               Common
Unpublish            Data
Uninstall            Lifecycle
Unregister           Lifecycle
Unblock              Security
Unprotect            Security
```

### <span data-ttu-id="e2397-118">Voor beeld 3: alle goedgekeurde werk woorden ophalen in de beveiligings groep</span><span class="sxs-lookup"><span data-stu-id="e2397-118">Example 3 - Get all approved verbs in the Security group</span></span>

```powershell
Get-Verb | Where-Object Group -EQ Security
```

```Output
Verb      Group
----      -----
Block     Security
Grant     Security
Protect   Security
Revoke    Security
Unblock   Security
Unprotect Security
```

### <span data-ttu-id="e2397-119">Voor beeld 4: Hiermee vindt u alle opdrachten in een module die een niet-goedgekeurde term hebben</span><span class="sxs-lookup"><span data-stu-id="e2397-119">Example 4 - Finds all commands in a module that have unapproved verbs</span></span>

```powershell
Get-Command -Module Microsoft.PowerShell.Utility | Where-Object Verb -NotIn (Get-Verb).Verb
```

```Output
CommandType     Name            Version    Source
-----------     ----            -------    ------
Cmdlet          Sort-Object     3.1.0.0    Microsoft.PowerShell.Utility
Cmdlet          Tee-Object      3.1.0.0    Microsoft.PowerShell.Utility
```

## <span data-ttu-id="e2397-120">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="e2397-120">PARAMETERS</span></span>

### <span data-ttu-id="e2397-121">-verb</span><span class="sxs-lookup"><span data-stu-id="e2397-121">-verb</span></span>

<span data-ttu-id="e2397-122">Hiermee worden alleen de opgegeven termen opgehaald.</span><span class="sxs-lookup"><span data-stu-id="e2397-122">Gets only the specified verbs.</span></span>
<span data-ttu-id="e2397-123">Voer de naam van een werk woord of een naam patroon in.</span><span class="sxs-lookup"><span data-stu-id="e2397-123">Enter the name of a verb or a name pattern.</span></span>
<span data-ttu-id="e2397-124">Joker tekens zijn toegestaan.</span><span class="sxs-lookup"><span data-stu-id="e2397-124">Wildcards are allowed.</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: 1
Default value: All verbs
Accept pipeline input: True (ByValue)
Accept wildcard characters: True
```

## <span data-ttu-id="e2397-125">INVOER</span><span class="sxs-lookup"><span data-stu-id="e2397-125">INPUTS</span></span>

### <span data-ttu-id="e2397-126">Geen</span><span class="sxs-lookup"><span data-stu-id="e2397-126">None</span></span>

## <span data-ttu-id="e2397-127">UITVOER</span><span class="sxs-lookup"><span data-stu-id="e2397-127">OUTPUTS</span></span>

### <span data-ttu-id="e2397-128">Geselecteerd. Microsoft. Power shell. commands. MemberDefinition</span><span class="sxs-lookup"><span data-stu-id="e2397-128">Selected.Microsoft.PowerShell.Commands.MemberDefinition</span></span>

## <span data-ttu-id="e2397-129">OPMERKINGEN</span><span class="sxs-lookup"><span data-stu-id="e2397-129">NOTES</span></span>

<span data-ttu-id="e2397-130">`Get-Verb` retourneert een gewijzigde versie van een micro soft. Power shell. commands. MemberDefinition-object.</span><span class="sxs-lookup"><span data-stu-id="e2397-130">`Get-Verb` returns a modified version of a Microsoft.PowerShell.Commands.MemberDefinition object.</span></span>
<span data-ttu-id="e2397-131">Het object heeft niet de standaard eigenschappen van een MemberDefinition-object.</span><span class="sxs-lookup"><span data-stu-id="e2397-131">The object does not have the standard properties of a MemberDefinition object.</span></span> <span data-ttu-id="e2397-132">In plaats daarvan heeft het verb-en Group-eigenschappen.</span><span class="sxs-lookup"><span data-stu-id="e2397-132">Instead it has Verb and Group properties.</span></span> <span data-ttu-id="e2397-133">De eigenschap verb bevat een teken reeks met de naam van de bewerking.</span><span class="sxs-lookup"><span data-stu-id="e2397-133">The Verb property contains a string with the verb name.</span></span> <span data-ttu-id="e2397-134">De eigenschap Group bevat een teken reeks met de groep verb.</span><span class="sxs-lookup"><span data-stu-id="e2397-134">The Group property contains a string with the verb group.</span></span>

<span data-ttu-id="e2397-135">Power shell-werk woorden worden toegewezen aan een groep op basis van het meest voorkomende gebruik.</span><span class="sxs-lookup"><span data-stu-id="e2397-135">PowerShell verbs are assigned to a group based on their most common use.</span></span> <span data-ttu-id="e2397-136">De groepen zijn ontworpen om de werk woorden gemakkelijk te vinden en te vergelijken, en om het gebruik ervan te beperken.</span><span class="sxs-lookup"><span data-stu-id="e2397-136">The groups are designed to make the verbs easy to find and compare, not to restrict their use.</span></span> <span data-ttu-id="e2397-137">U kunt elk goedgekeurd werk woord voor elk type opdracht gebruiken.</span><span class="sxs-lookup"><span data-stu-id="e2397-137">You can use any approved verb for any type of command.</span></span>

<span data-ttu-id="e2397-138">Elke Power shell-term wordt toegewezen aan een van de volgende groepen.</span><span class="sxs-lookup"><span data-stu-id="e2397-138">Each PowerShell verb is assigned to one of the following groups.</span></span>

- <span data-ttu-id="e2397-139">Algemeen: Definieer algemene acties die van toepassing kunnen zijn op bijna elke cmdlet, zoals toevoegen.</span><span class="sxs-lookup"><span data-stu-id="e2397-139">Common: Define generic actions that can apply to almost any cmdlet, such as Add.</span></span>
- <span data-ttu-id="e2397-140">Communicatie: acties definiëren die van toepassing zijn op de communicatie, zoals verbinding maken.</span><span class="sxs-lookup"><span data-stu-id="e2397-140">Communications:  Define actions that apply to communications, such as Connect.</span></span>
- <span data-ttu-id="e2397-141">Gegevens: acties definiëren die van toepassing zijn op de verwerking van gegevens, zoals back-up.</span><span class="sxs-lookup"><span data-stu-id="e2397-141">Data:  Define actions that apply to data handling, such as Backup.</span></span>
- <span data-ttu-id="e2397-142">Diagnose: acties definiëren die van toepassing zijn op diagnostische gegevens, zoals fout opsporing.</span><span class="sxs-lookup"><span data-stu-id="e2397-142">Diagnostic: Define actions that apply to diagnostics, such as Debug.</span></span>
- <span data-ttu-id="e2397-143">Levenscyclus: Definieer acties die van toepassing zijn op de levens cyclus van een cmdlet, zoals voltooid.</span><span class="sxs-lookup"><span data-stu-id="e2397-143">Lifecycle: Define actions that apply to the lifecycle of a cmdlet, such as Complete.</span></span>
- <span data-ttu-id="e2397-144">Beveiliging: Definieer acties die van toepassing zijn op de beveiliging, zoals intrekken.</span><span class="sxs-lookup"><span data-stu-id="e2397-144">Security: Define actions that apply to security, such as Revoke.</span></span>
- <span data-ttu-id="e2397-145">Overige: andere typen acties definiëren.</span><span class="sxs-lookup"><span data-stu-id="e2397-145">Other: Define other types of actions.</span></span>

<span data-ttu-id="e2397-146">Sommige cmdlets die zijn geïnstalleerd met Power shell, zoals `Tee-Object` en `Where-Object` , gebruiken niet-goedgekeurde werk woorden.</span><span class="sxs-lookup"><span data-stu-id="e2397-146">Some of the cmdlets that are installed with PowerShell, such as `Tee-Object` and `Where-Object`, use unapproved verbs.</span></span> <span data-ttu-id="e2397-147">Deze cmdlets zijn historische uitzonde ringen en hun werk woorden worden als **gereserveerd** geclassificeerd.</span><span class="sxs-lookup"><span data-stu-id="e2397-147">These cmdlets are historic exceptions and their verbs are classified as **reserved**.</span></span>

## <span data-ttu-id="e2397-148">GERELATEERDE KOPPELINGEN</span><span class="sxs-lookup"><span data-stu-id="e2397-148">RELATED LINKS</span></span>

[<span data-ttu-id="e2397-149">Import-module</span><span class="sxs-lookup"><span data-stu-id="e2397-149">Import-Module</span></span>](import-module.md)
