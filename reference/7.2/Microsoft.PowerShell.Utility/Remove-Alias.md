---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 10/24/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/remove-alias?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Remove-Alias
ms.openlocfilehash: 0ce13bef77e9ef9647809336aed650833dab51f3
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 11/17/2020
ms.locfileid: "94704742"
---
# <span data-ttu-id="dbe50-102">Remove-Alias</span><span class="sxs-lookup"><span data-stu-id="dbe50-102">Remove-Alias</span></span>

## <span data-ttu-id="dbe50-103">SAMENVATTING</span><span class="sxs-lookup"><span data-stu-id="dbe50-103">SYNOPSIS</span></span>
<span data-ttu-id="dbe50-104">Een alias verwijderen uit de huidige sessie.</span><span class="sxs-lookup"><span data-stu-id="dbe50-104">Remove an alias from the current session.</span></span>

## <span data-ttu-id="dbe50-105">SYNTAXIS</span><span class="sxs-lookup"><span data-stu-id="dbe50-105">SYNTAX</span></span>

### <span data-ttu-id="dbe50-106">Standaard (standaard instelling)</span><span class="sxs-lookup"><span data-stu-id="dbe50-106">Default (Default)</span></span>

```
Remove-Alias [-Name] <String[]> [-Scope <String>] [-Force] [<CommonParameters>]
```

## <span data-ttu-id="dbe50-107">BESCHRIJVING</span><span class="sxs-lookup"><span data-stu-id="dbe50-107">DESCRIPTION</span></span>

<span data-ttu-id="dbe50-108">`Remove-Alias`Met de cmdlet wordt een alias uit de huidige Power shell-sessie verwijderd.</span><span class="sxs-lookup"><span data-stu-id="dbe50-108">The `Remove-Alias` cmdlet removes an alias from the current PowerShell session.</span></span> <span data-ttu-id="dbe50-109">Als u een alias waarvan de eigenschap **Option** is ingesteld op **ReadOnly** wilt verwijderen, gebruikt u de para meter **Force** .</span><span class="sxs-lookup"><span data-stu-id="dbe50-109">To remove an alias with the **Option** property set to **ReadOnly**, use the **Force** parameter.</span></span>

<span data-ttu-id="dbe50-110">De `Remove-Alias` cmdlet is geïntroduceerd in Power shell 6,0.</span><span class="sxs-lookup"><span data-stu-id="dbe50-110">The `Remove-Alias` cmdlet was introduced in PowerShell 6.0.</span></span>

## <span data-ttu-id="dbe50-111">VOORBEELDEN</span><span class="sxs-lookup"><span data-stu-id="dbe50-111">EXAMPLES</span></span>

### <span data-ttu-id="dbe50-112">Voor beeld 1: een alias verwijderen</span><span class="sxs-lookup"><span data-stu-id="dbe50-112">Example 1 - Remove an alias</span></span>

<span data-ttu-id="dbe50-113">In dit voor beeld wordt een alias `del` met de naam die de cmdlet vertegenwoordigt, verwijderd `Remove-Item` .</span><span class="sxs-lookup"><span data-stu-id="dbe50-113">This example removes an alias named `del` that represents the `Remove-Item` cmdlet.</span></span>

```powershell
Remove-Alias -Name del
```

### <span data-ttu-id="dbe50-114">Voor beeld 2: alle niet-constante aliassen verwijderen</span><span class="sxs-lookup"><span data-stu-id="dbe50-114">Example 2 - Remove all non-Constant aliases</span></span>

<span data-ttu-id="dbe50-115">In dit voor beeld worden alle aliassen verwijderd uit de huidige Power shell-sessie, met uitzonde ring van aliassen waarvan de eigenschap **Options** is ingesteld op **constant**.</span><span class="sxs-lookup"><span data-stu-id="dbe50-115">This example removes all aliases from the current PowerShell session, except for aliases with the **Options** property set to **Constant**.</span></span> <span data-ttu-id="dbe50-116">Nadat de opdracht is uitgevoerd, zijn de aliassen beschikbaar in andere Power shell-sessies of nieuwe Power shell-sessies.</span><span class="sxs-lookup"><span data-stu-id="dbe50-116">After the command is run, the aliases are available in other PowerShell sessions or new PowerShell sessions.</span></span>

```powershell
Get-Alias | Where-Object { $_.Options -NE "Constant" } | Remove-Alias -Force
```

<span data-ttu-id="dbe50-117">`Get-Alias` Hiermee worden alle aliassen in de Power shell-sessie opgehaald en worden de objecten van de pijp lijn omlaag verzonden.</span><span class="sxs-lookup"><span data-stu-id="dbe50-117">`Get-Alias` gets all the aliases in the PowerShell session and sends the objects down the pipeline.</span></span>
<span data-ttu-id="dbe50-118">`Where-Object` maakt gebruik van een script blok en de eigenschap Automatic variabele ( `$_` ) en **Options** vertegenwoordigen het huidige pijplijn object.</span><span class="sxs-lookup"><span data-stu-id="dbe50-118">`Where-Object` uses a script block, and the automatic variable (`$_`) and **Options** property represent the current pipeline object.</span></span> <span data-ttu-id="dbe50-119">De para meter **ne** (niet gelijk aan), selecteert objecten waarvoor geen **optie** waarde is ingesteld op **constant**.</span><span class="sxs-lookup"><span data-stu-id="dbe50-119">The parameter **NE** (not equal), selects objects that don't have an **Options** value set to **Constant**.</span></span> <span data-ttu-id="dbe50-120">`Remove-Alias` maakt gebruik van de para meter **Force** om aliassen te verwijderen, met inbegrip van alleen-lezen aliassen, vanuit de Power shell-sessie.</span><span class="sxs-lookup"><span data-stu-id="dbe50-120">`Remove-Alias` uses the **Force** parameter to remove aliases, including read-only aliases, from the PowerShell session.</span></span>

## <span data-ttu-id="dbe50-121">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="dbe50-121">PARAMETERS</span></span>

### <span data-ttu-id="dbe50-122">-Force</span><span class="sxs-lookup"><span data-stu-id="dbe50-122">-Force</span></span>

<span data-ttu-id="dbe50-123">Geeft aan dat de cmdlet een alias verwijdert, inclusief aliassen waarvan de eigenschap **Option** is ingesteld op **ReadOnly**.</span><span class="sxs-lookup"><span data-stu-id="dbe50-123">Indicates that the cmdlet removes an alias, including aliases with the **Option** property set to **ReadOnly**.</span></span> <span data-ttu-id="dbe50-124">Met de para meter **Force** kan een alias waarvan de eigenschap **Option** is ingesteld op **constant** niet worden verwijderd.</span><span class="sxs-lookup"><span data-stu-id="dbe50-124">The **Force** parameter can't remove an alias with an **Option** property set to **Constant**.</span></span>

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

### <span data-ttu-id="dbe50-125">-Name</span><span class="sxs-lookup"><span data-stu-id="dbe50-125">-Name</span></span>

<span data-ttu-id="dbe50-126">Hiermee geeft u de naam op van de alias die u wilt verwijderen.</span><span class="sxs-lookup"><span data-stu-id="dbe50-126">Specifies the name of the alias to remove.</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="dbe50-127">-Bereik</span><span class="sxs-lookup"><span data-stu-id="dbe50-127">-Scope</span></span>

<span data-ttu-id="dbe50-128">Alleen van invloed op de aliassen in het opgegeven bereik.</span><span class="sxs-lookup"><span data-stu-id="dbe50-128">Affects only the aliases in the specified scope.</span></span> <span data-ttu-id="dbe50-129">Het standaard bereik is **lokaal**.</span><span class="sxs-lookup"><span data-stu-id="dbe50-129">The default scope is **Local**.</span></span> <span data-ttu-id="dbe50-130">Zie [about_Scopes](../microsoft.powershell.core/about/about_scopes.md)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="dbe50-130">For more information, see [about_Scopes](../microsoft.powershell.core/about/about_scopes.md).</span></span>

<span data-ttu-id="dbe50-131">De aanvaardbare waarden voor deze parameter zijn:</span><span class="sxs-lookup"><span data-stu-id="dbe50-131">The acceptable values for this parameter are:</span></span>

- <span data-ttu-id="dbe50-132">Globaal</span><span class="sxs-lookup"><span data-stu-id="dbe50-132">Global</span></span>
- <span data-ttu-id="dbe50-133">Lokaal</span><span class="sxs-lookup"><span data-stu-id="dbe50-133">Local</span></span>
- <span data-ttu-id="dbe50-134">Script</span><span class="sxs-lookup"><span data-stu-id="dbe50-134">Script</span></span>
- <span data-ttu-id="dbe50-135">Een getal dat relatief is ten opzichte van het huidige bereik (0 tot en met het aantal bereiken, waarbij 0 het huidige bereik is en 1 de bovenliggende scope)</span><span class="sxs-lookup"><span data-stu-id="dbe50-135">A number relative to the current scope (0 through the number of scopes, where 0 is the current scope and 1 is its parent)</span></span>

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

### <span data-ttu-id="dbe50-136">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="dbe50-136">CommonParameters</span></span>

<span data-ttu-id="dbe50-137">Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="dbe50-137">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="dbe50-138">Zie [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="dbe50-138">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="dbe50-139">INVOER</span><span class="sxs-lookup"><span data-stu-id="dbe50-139">INPUTS</span></span>

### <span data-ttu-id="dbe50-140">System.String[]</span><span class="sxs-lookup"><span data-stu-id="dbe50-140">System.String[]</span></span>

<span data-ttu-id="dbe50-141">U kunt een alias object door sluizen om **-alias te verwijderen**.</span><span class="sxs-lookup"><span data-stu-id="dbe50-141">You can pipe an alias object to **Remove-Alias**.</span></span>

## <span data-ttu-id="dbe50-142">UITVOER</span><span class="sxs-lookup"><span data-stu-id="dbe50-142">OUTPUTS</span></span>

### <span data-ttu-id="dbe50-143">Geen</span><span class="sxs-lookup"><span data-stu-id="dbe50-143">None</span></span>

<span data-ttu-id="dbe50-144">Met deze cmdlet wordt geen uitvoer geretourneerd.</span><span class="sxs-lookup"><span data-stu-id="dbe50-144">This cmdlet doesn't return any output.</span></span>

## <span data-ttu-id="dbe50-145">OPMERKINGEN</span><span class="sxs-lookup"><span data-stu-id="dbe50-145">NOTES</span></span>

<span data-ttu-id="dbe50-146">De wijzigingen zijn alleen van invloed op de huidige scope.</span><span class="sxs-lookup"><span data-stu-id="dbe50-146">Changes only affect the current scope.</span></span> <span data-ttu-id="dbe50-147">Als u een alias van alle sessies wilt verwijderen, voegt u een **Verwijder-alias** opdracht toe aan uw Power shell-profiel.</span><span class="sxs-lookup"><span data-stu-id="dbe50-147">To remove an alias from all sessions, add a **Remove-Alias** command to your PowerShell profile.</span></span>

<span data-ttu-id="dbe50-148">Zie [about_Aliases](../microsoft.powershell.core/about/about_aliases.md)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="dbe50-148">For more information, see [about_Aliases](../microsoft.powershell.core/about/about_aliases.md).</span></span>

## <span data-ttu-id="dbe50-149">GERELATEERDE KOPPELINGEN</span><span class="sxs-lookup"><span data-stu-id="dbe50-149">RELATED LINKS</span></span>

[<span data-ttu-id="dbe50-150">about_Automatic_Variables</span><span class="sxs-lookup"><span data-stu-id="dbe50-150">about_Automatic_Variables</span></span>](../Microsoft.PowerShell.Core/About/about_Automatic_Variables.md)

[<span data-ttu-id="dbe50-151">Exporteren-alias</span><span class="sxs-lookup"><span data-stu-id="dbe50-151">Export-Alias</span></span>](Export-Alias.md)

[<span data-ttu-id="dbe50-152">Get-alias</span><span class="sxs-lookup"><span data-stu-id="dbe50-152">Get-Alias</span></span>](Get-Alias.md)

[<span data-ttu-id="dbe50-153">Import-alias</span><span class="sxs-lookup"><span data-stu-id="dbe50-153">Import-Alias</span></span>](Import-Alias.md)

[<span data-ttu-id="dbe50-154">Nieuwe alias</span><span class="sxs-lookup"><span data-stu-id="dbe50-154">New-Alias</span></span>](New-Alias.md)

[<span data-ttu-id="dbe50-155">Set-alias</span><span class="sxs-lookup"><span data-stu-id="dbe50-155">Set-Alias</span></span>](Set-Alias.md)

[<span data-ttu-id="dbe50-156">Where-object</span><span class="sxs-lookup"><span data-stu-id="dbe50-156">Where-Object</span></span>](../Microsoft.PowerShell.Core/Where-Object.md)

