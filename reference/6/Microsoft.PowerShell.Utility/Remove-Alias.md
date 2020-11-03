---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 10/24/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/remove-alias?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Remove-Alias
ms.openlocfilehash: 08ef751e0573f896c5f63737b00b55ab77ae73e3
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/07/2020
ms.locfileid: "93250957"
---
# <span data-ttu-id="6fc9d-103">Remove-Alias</span><span class="sxs-lookup"><span data-stu-id="6fc9d-103">Remove-Alias</span></span>

## <span data-ttu-id="6fc9d-104">SAMENVATTING</span><span class="sxs-lookup"><span data-stu-id="6fc9d-104">SYNOPSIS</span></span>
<span data-ttu-id="6fc9d-105">Een alias verwijderen uit de huidige sessie.</span><span class="sxs-lookup"><span data-stu-id="6fc9d-105">Remove an alias from the current session.</span></span>

## <span data-ttu-id="6fc9d-106">SYNTAXIS</span><span class="sxs-lookup"><span data-stu-id="6fc9d-106">SYNTAX</span></span>

### <span data-ttu-id="6fc9d-107">Standaard (standaard instelling)</span><span class="sxs-lookup"><span data-stu-id="6fc9d-107">Default (Default)</span></span>

```
Remove-Alias [-Name] <String[]> [-Scope <String>] [-Force] [<CommonParameters>]
```

## <span data-ttu-id="6fc9d-108">BESCHRIJVING</span><span class="sxs-lookup"><span data-stu-id="6fc9d-108">DESCRIPTION</span></span>

<span data-ttu-id="6fc9d-109">`Remove-Alias`Met de cmdlet wordt een alias uit de huidige Power shell-sessie verwijderd.</span><span class="sxs-lookup"><span data-stu-id="6fc9d-109">The `Remove-Alias` cmdlet removes an alias from the current PowerShell session.</span></span> <span data-ttu-id="6fc9d-110">Als u een alias waarvan de eigenschap **Option** is ingesteld op **ReadOnly** wilt verwijderen, gebruikt u de para meter **Force** .</span><span class="sxs-lookup"><span data-stu-id="6fc9d-110">To remove an alias with the **Option** property set to **ReadOnly** , use the **Force** parameter.</span></span>

<span data-ttu-id="6fc9d-111">De `Remove-Alias` cmdlet is geïntroduceerd in Power shell 6,0.</span><span class="sxs-lookup"><span data-stu-id="6fc9d-111">The `Remove-Alias` cmdlet was introduced in PowerShell 6.0.</span></span>

## <span data-ttu-id="6fc9d-112">VOORBEELDEN</span><span class="sxs-lookup"><span data-stu-id="6fc9d-112">EXAMPLES</span></span>

### <span data-ttu-id="6fc9d-113">Voor beeld 1: een alias verwijderen</span><span class="sxs-lookup"><span data-stu-id="6fc9d-113">Example 1 - Remove an alias</span></span>

<span data-ttu-id="6fc9d-114">In dit voor beeld wordt een alias `del` met de naam die de cmdlet vertegenwoordigt, verwijderd `Remove-Item` .</span><span class="sxs-lookup"><span data-stu-id="6fc9d-114">This example removes an alias named `del` that represents the `Remove-Item` cmdlet.</span></span>

```powershell
Remove-Alias -Name del
```

### <span data-ttu-id="6fc9d-115">Voor beeld 2: alle niet-constante aliassen verwijderen</span><span class="sxs-lookup"><span data-stu-id="6fc9d-115">Example 2 - Remove all non-Constant aliases</span></span>

<span data-ttu-id="6fc9d-116">In dit voor beeld worden alle aliassen verwijderd uit de huidige Power shell-sessie, met uitzonde ring van aliassen waarvan de eigenschap **Options** is ingesteld op **constant**.</span><span class="sxs-lookup"><span data-stu-id="6fc9d-116">This example removes all aliases from the current PowerShell session, except for aliases with the **Options** property set to **Constant**.</span></span> <span data-ttu-id="6fc9d-117">Nadat de opdracht is uitgevoerd, zijn de aliassen beschikbaar in andere Power shell-sessies of nieuwe Power shell-sessies.</span><span class="sxs-lookup"><span data-stu-id="6fc9d-117">After the command is run, the aliases are available in other PowerShell sessions or new PowerShell sessions.</span></span>

```powershell
Get-Alias | Where-Object { $_.Options -NE "Constant" } | Remove-Alias -Force
```

<span data-ttu-id="6fc9d-118">`Get-Alias` Hiermee worden alle aliassen in de Power shell-sessie opgehaald en worden de objecten van de pijp lijn omlaag verzonden.</span><span class="sxs-lookup"><span data-stu-id="6fc9d-118">`Get-Alias` gets all the aliases in the PowerShell session and sends the objects down the pipeline.</span></span>
<span data-ttu-id="6fc9d-119">`Where-Object` maakt gebruik van een script blok en de eigenschap Automatic variabele ( `$_` ) en **Options** vertegenwoordigen het huidige pijplijn object.</span><span class="sxs-lookup"><span data-stu-id="6fc9d-119">`Where-Object` uses a script block, and the automatic variable (`$_`) and **Options** property represent the current pipeline object.</span></span> <span data-ttu-id="6fc9d-120">De para meter **ne** (niet gelijk aan), selecteert objecten waarvoor geen **optie** waarde is ingesteld op **constant**.</span><span class="sxs-lookup"><span data-stu-id="6fc9d-120">The parameter **NE** (not equal), selects objects that don't have an **Options** value set to **Constant**.</span></span> <span data-ttu-id="6fc9d-121">`Remove-Alias` maakt gebruik van de para meter **Force** om aliassen te verwijderen, met inbegrip van alleen-lezen aliassen, vanuit de Power shell-sessie.</span><span class="sxs-lookup"><span data-stu-id="6fc9d-121">`Remove-Alias` uses the **Force** parameter to remove aliases, including read-only aliases, from the PowerShell session.</span></span>

## <span data-ttu-id="6fc9d-122">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="6fc9d-122">PARAMETERS</span></span>

### <span data-ttu-id="6fc9d-123">-Force</span><span class="sxs-lookup"><span data-stu-id="6fc9d-123">-Force</span></span>

<span data-ttu-id="6fc9d-124">Geeft aan dat de cmdlet een alias verwijdert, inclusief aliassen waarvan de eigenschap **Option** is ingesteld op **ReadOnly**.</span><span class="sxs-lookup"><span data-stu-id="6fc9d-124">Indicates that the cmdlet removes an alias, including aliases with the **Option** property set to **ReadOnly**.</span></span> <span data-ttu-id="6fc9d-125">Met de para meter **Force** kan een alias waarvan de eigenschap **Option** is ingesteld op **constant** niet worden verwijderd.</span><span class="sxs-lookup"><span data-stu-id="6fc9d-125">The **Force** parameter can't remove an alias with an **Option** property set to **Constant**.</span></span>

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

### <span data-ttu-id="6fc9d-126">-Name</span><span class="sxs-lookup"><span data-stu-id="6fc9d-126">-Name</span></span>

<span data-ttu-id="6fc9d-127">Hiermee geeft u de naam op van de alias die u wilt verwijderen.</span><span class="sxs-lookup"><span data-stu-id="6fc9d-127">Specifies the name of the alias to remove.</span></span>

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

### <span data-ttu-id="6fc9d-128">-Bereik</span><span class="sxs-lookup"><span data-stu-id="6fc9d-128">-Scope</span></span>

<span data-ttu-id="6fc9d-129">Alleen van invloed op de aliassen in het opgegeven bereik.</span><span class="sxs-lookup"><span data-stu-id="6fc9d-129">Affects only the aliases in the specified scope.</span></span> <span data-ttu-id="6fc9d-130">Het standaard bereik is **lokaal**.</span><span class="sxs-lookup"><span data-stu-id="6fc9d-130">The default scope is **Local**.</span></span> <span data-ttu-id="6fc9d-131">Zie [about_Scopes](../microsoft.powershell.core/about/about_scopes.md)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="6fc9d-131">For more information, see [about_Scopes](../microsoft.powershell.core/about/about_scopes.md).</span></span>

<span data-ttu-id="6fc9d-132">De aanvaardbare waarden voor deze parameter zijn:</span><span class="sxs-lookup"><span data-stu-id="6fc9d-132">The acceptable values for this parameter are:</span></span>

- <span data-ttu-id="6fc9d-133">Globaal</span><span class="sxs-lookup"><span data-stu-id="6fc9d-133">Global</span></span>
- <span data-ttu-id="6fc9d-134">Lokaal</span><span class="sxs-lookup"><span data-stu-id="6fc9d-134">Local</span></span>
- <span data-ttu-id="6fc9d-135">Script</span><span class="sxs-lookup"><span data-stu-id="6fc9d-135">Script</span></span>
- <span data-ttu-id="6fc9d-136">Een getal dat relatief is ten opzichte van het huidige bereik (0 tot en met het aantal bereiken, waarbij 0 het huidige bereik is en 1 de bovenliggende scope)</span><span class="sxs-lookup"><span data-stu-id="6fc9d-136">A number relative to the current scope (0 through the number of scopes, where 0 is the current scope and 1 is its parent)</span></span>

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

### <span data-ttu-id="6fc9d-137">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="6fc9d-137">CommonParameters</span></span>

<span data-ttu-id="6fc9d-138">Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="6fc9d-138">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="6fc9d-139">Zie [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="6fc9d-139">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="6fc9d-140">INVOER</span><span class="sxs-lookup"><span data-stu-id="6fc9d-140">INPUTS</span></span>

### <span data-ttu-id="6fc9d-141">System.String[]</span><span class="sxs-lookup"><span data-stu-id="6fc9d-141">System.String[]</span></span>

<span data-ttu-id="6fc9d-142">U kunt een alias object door sluizen om **-alias te verwijderen**.</span><span class="sxs-lookup"><span data-stu-id="6fc9d-142">You can pipe an alias object to **Remove-Alias**.</span></span>

## <span data-ttu-id="6fc9d-143">UITVOER</span><span class="sxs-lookup"><span data-stu-id="6fc9d-143">OUTPUTS</span></span>

### <span data-ttu-id="6fc9d-144">Geen</span><span class="sxs-lookup"><span data-stu-id="6fc9d-144">None</span></span>

<span data-ttu-id="6fc9d-145">Met deze cmdlet wordt geen uitvoer geretourneerd.</span><span class="sxs-lookup"><span data-stu-id="6fc9d-145">This cmdlet doesn't return any output.</span></span>

## <span data-ttu-id="6fc9d-146">OPMERKINGEN</span><span class="sxs-lookup"><span data-stu-id="6fc9d-146">NOTES</span></span>

<span data-ttu-id="6fc9d-147">De wijzigingen zijn alleen van invloed op de huidige scope.</span><span class="sxs-lookup"><span data-stu-id="6fc9d-147">Changes only affect the current scope.</span></span> <span data-ttu-id="6fc9d-148">Als u een alias van alle sessies wilt verwijderen, voegt u een **Verwijder-alias** opdracht toe aan uw Power shell-profiel.</span><span class="sxs-lookup"><span data-stu-id="6fc9d-148">To remove an alias from all sessions, add a **Remove-Alias** command to your PowerShell profile.</span></span>

<span data-ttu-id="6fc9d-149">Zie [about_Aliases](../microsoft.powershell.core/about/about_aliases.md)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="6fc9d-149">For more information, see [about_Aliases](../microsoft.powershell.core/about/about_aliases.md).</span></span>

## <span data-ttu-id="6fc9d-150">GERELATEERDE KOPPELINGEN</span><span class="sxs-lookup"><span data-stu-id="6fc9d-150">RELATED LINKS</span></span>

[<span data-ttu-id="6fc9d-151">about_Automatic_Variables</span><span class="sxs-lookup"><span data-stu-id="6fc9d-151">about_Automatic_Variables</span></span>](../Microsoft.PowerShell.Core/About/about_Automatic_Variables.md)

[<span data-ttu-id="6fc9d-152">Exporteren-alias</span><span class="sxs-lookup"><span data-stu-id="6fc9d-152">Export-Alias</span></span>](Export-Alias.md)

[<span data-ttu-id="6fc9d-153">Get-alias</span><span class="sxs-lookup"><span data-stu-id="6fc9d-153">Get-Alias</span></span>](Get-Alias.md)

[<span data-ttu-id="6fc9d-154">Import-alias</span><span class="sxs-lookup"><span data-stu-id="6fc9d-154">Import-Alias</span></span>](Import-Alias.md)

[<span data-ttu-id="6fc9d-155">Nieuwe alias</span><span class="sxs-lookup"><span data-stu-id="6fc9d-155">New-Alias</span></span>](New-Alias.md)

[<span data-ttu-id="6fc9d-156">Set-alias</span><span class="sxs-lookup"><span data-stu-id="6fc9d-156">Set-Alias</span></span>](Set-Alias.md)

[<span data-ttu-id="6fc9d-157">Where-object</span><span class="sxs-lookup"><span data-stu-id="6fc9d-157">Where-Object</span></span>](../Microsoft.PowerShell.Core/Where-Object.md)
