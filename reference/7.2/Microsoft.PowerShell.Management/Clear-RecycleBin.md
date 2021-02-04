---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 01/29/2021
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/clear-recyclebin?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Clear-RecycleBin
ms.openlocfilehash: e7ce0f2bcd1ece0bb737aea1297641c37337f3e5
ms.sourcegitcommit: 81558c2adb9d109946a027e5b96e4d24b3b13747
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 01/30/2021
ms.locfileid: "99098680"
---
# <span data-ttu-id="1bc25-102">Clear-RecycleBin</span><span class="sxs-lookup"><span data-stu-id="1bc25-102">Clear-RecycleBin</span></span>

## <span data-ttu-id="1bc25-103">SAMENVATTING</span><span class="sxs-lookup"><span data-stu-id="1bc25-103">SYNOPSIS</span></span>
<span data-ttu-id="1bc25-104">Hiermee wordt de inhoud van een prullenbak gewist.</span><span class="sxs-lookup"><span data-stu-id="1bc25-104">Clears the contents of a recycle bin.</span></span>

## <span data-ttu-id="1bc25-105">SYNTAXIS</span><span class="sxs-lookup"><span data-stu-id="1bc25-105">SYNTAX</span></span>

### <span data-ttu-id="1bc25-106">Alles</span><span class="sxs-lookup"><span data-stu-id="1bc25-106">All</span></span>

```
Clear-RecycleBin [[-DriveLetter] <String[]>] [-Force] [-WhatIf] [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="1bc25-107">BESCHRIJVING</span><span class="sxs-lookup"><span data-stu-id="1bc25-107">DESCRIPTION</span></span>

<span data-ttu-id="1bc25-108">De `Clear-RecycleBin` cmdlet verwijdert de inhoud van de Prullenbak van een computer.</span><span class="sxs-lookup"><span data-stu-id="1bc25-108">The `Clear-RecycleBin` cmdlet deletes the content of a computer's recycle bin.</span></span> <span data-ttu-id="1bc25-109">Deze actie is vergelijkbaar met het gebruik van een prullenbak van Windows **Empty**.</span><span class="sxs-lookup"><span data-stu-id="1bc25-109">This action is like using Windows **Empty Recycle Bin**.</span></span>

<span data-ttu-id="1bc25-110">Deze cmdlet is opnieuw toegevoegd in Power shell 7.</span><span class="sxs-lookup"><span data-stu-id="1bc25-110">This cmdlet was readded in PowerShell 7.</span></span>

## <span data-ttu-id="1bc25-111">VOORBEELDEN</span><span class="sxs-lookup"><span data-stu-id="1bc25-111">EXAMPLES</span></span>

### <span data-ttu-id="1bc25-112">1: alle prullen bakken wissen</span><span class="sxs-lookup"><span data-stu-id="1bc25-112">1: Clear all recycle bins</span></span>

<span data-ttu-id="1bc25-113">In dit voor beeld worden alle prullen bakken van de lokale computer gewist.</span><span class="sxs-lookup"><span data-stu-id="1bc25-113">In this example, all the local computer's recycle bins are cleared.</span></span>

```powershell
Clear-RecycleBin
```

```Output
Confirm
Are you sure you want to perform this action?
Performing the operation "Clear-RecycleBin" on target "All of the contents of the Recycle Bin".
[Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "Y"):
```

<span data-ttu-id="1bc25-114">`Clear-RecycleBin` Hiermee wordt de gebruiker gevraagd om te bevestigen dat alle prullen bakken op de lokale computer moeten worden gewist.</span><span class="sxs-lookup"><span data-stu-id="1bc25-114">`Clear-RecycleBin` prompts the user for confirmation to clear all recycle bins on the local computer.</span></span>

### <span data-ttu-id="1bc25-115">2: een opgegeven Prullenbak wissen</span><span class="sxs-lookup"><span data-stu-id="1bc25-115">2: Clear a specified recycle bin</span></span>

<span data-ttu-id="1bc25-116">In dit voor beeld wordt de Prullenbak voor een opgegeven stationsletter gewist.</span><span class="sxs-lookup"><span data-stu-id="1bc25-116">This example clears the recycle bin for a specified drive letter.</span></span>

```powershell
Clear-RecycleBin -DriveLetter C
```

<span data-ttu-id="1bc25-117">`Clear-RecycleBin` gebruikt de **stationsletter** -para meter om de Prullenbak op het **C** -volume op te geven.</span><span class="sxs-lookup"><span data-stu-id="1bc25-117">`Clear-RecycleBin` uses the **DriveLetter** parameter to specify the recycle bin on the **C** volume.</span></span> <span data-ttu-id="1bc25-118">De gebruiker wordt gevraagd om bevestiging om de opdracht uit te voeren.</span><span class="sxs-lookup"><span data-stu-id="1bc25-118">The user is prompted for confirmation to run the command.</span></span>

### <span data-ttu-id="1bc25-119">3: alle prullen bakken wissen zonder bevestiging</span><span class="sxs-lookup"><span data-stu-id="1bc25-119">3: Clear all recycle bins without confirmation</span></span>

<span data-ttu-id="1bc25-120">In dit voor beeld wordt niet gevraagd om bevestiging om de prullen bakken van de lokale computer te wissen.</span><span class="sxs-lookup"><span data-stu-id="1bc25-120">This example doesn't prompt for confirmation to clear the local computer's recycle bins.</span></span>

```powershell
Clear-RecycleBin -Force
```

<span data-ttu-id="1bc25-121">`Clear-RecycleBin` gebruikt de **Force** -para meter en vraagt de gebruiker niet om bevestiging om alle prullen bakken op de lokale computer te wissen.</span><span class="sxs-lookup"><span data-stu-id="1bc25-121">`Clear-RecycleBin` uses the **Force** parameter and doesn't prompt the user for confirmation to clear all recycle bins on the local computer.</span></span>

<span data-ttu-id="1bc25-122">U kunt ook vervangen `-Force` door `-Confirm:$false` .</span><span class="sxs-lookup"><span data-stu-id="1bc25-122">An alternative is to replace `-Force` with `-Confirm:$false`.</span></span>

## <span data-ttu-id="1bc25-123">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="1bc25-123">PARAMETERS</span></span>

### <span data-ttu-id="1bc25-124">-Stationsletter</span><span class="sxs-lookup"><span data-stu-id="1bc25-124">-DriveLetter</span></span>

<span data-ttu-id="1bc25-125">Hiermee geeft u de Prullenbak op die moet worden gewist voor één stationsletter of een reeks stationsletters.</span><span class="sxs-lookup"><span data-stu-id="1bc25-125">Specifies the recycle bin to clear for a single drive letter or an array of drive letters.</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="1bc25-126">-Force</span><span class="sxs-lookup"><span data-stu-id="1bc25-126">-Force</span></span>

<span data-ttu-id="1bc25-127">Geeft aan dat de gebruiker niet om bevestiging wordt gevraagd om een prullenbak te wissen.</span><span class="sxs-lookup"><span data-stu-id="1bc25-127">Specifies that the user isn't prompted for confirmation to clear a recycle bin.</span></span> <span data-ttu-id="1bc25-128">De para meter **Force** onderdrukt ook de para meters **WhatIf** en **confirm** .</span><span class="sxs-lookup"><span data-stu-id="1bc25-128">The **Force** parameter also overrides the **WhatIf** and **Confirm** parameters.</span></span>

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

### <span data-ttu-id="1bc25-129">-Confirm</span><span class="sxs-lookup"><span data-stu-id="1bc25-129">-Confirm</span></span>

<span data-ttu-id="1bc25-130">Vraagt om bevestiging van de gebruiker voordat de cmdlet wordt uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="1bc25-130">Prompts for user confirmation before running the cmdlet.</span></span> <span data-ttu-id="1bc25-131">De gebruiker wordt om bevestiging gevraagd, zelfs als de para meter **confirm** niet is opgegeven.</span><span class="sxs-lookup"><span data-stu-id="1bc25-131">The user is prompted for confirmation even if the **Confirm** parameter isn't specified.</span></span>

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

### <span data-ttu-id="1bc25-132">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="1bc25-132">-WhatIf</span></span>

<span data-ttu-id="1bc25-133">Hier wordt weer gegeven wat er gebeurt als er `Clear-RecycleBin` wordt uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="1bc25-133">Shows what would happen if `Clear-RecycleBin` runs.</span></span> <span data-ttu-id="1bc25-134">De cmdlet wordt niet uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="1bc25-134">The cmdlet isn't run.</span></span>

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

### <span data-ttu-id="1bc25-135">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="1bc25-135">CommonParameters</span></span>

<span data-ttu-id="1bc25-136">Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="1bc25-136">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="1bc25-137">Zie [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="1bc25-137">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="1bc25-138">INVOER</span><span class="sxs-lookup"><span data-stu-id="1bc25-138">INPUTS</span></span>

## <span data-ttu-id="1bc25-139">UITVOER</span><span class="sxs-lookup"><span data-stu-id="1bc25-139">OUTPUTS</span></span>

### <span data-ttu-id="1bc25-140">Geen</span><span class="sxs-lookup"><span data-stu-id="1bc25-140">None</span></span>

## <span data-ttu-id="1bc25-141">OPMERKINGEN</span><span class="sxs-lookup"><span data-stu-id="1bc25-141">NOTES</span></span>

<span data-ttu-id="1bc25-142">Deze cmdlet is alleen beschikbaar op Windows-platforms.</span><span class="sxs-lookup"><span data-stu-id="1bc25-142">This cmdlet is only available on Windows platforms.</span></span>

## <span data-ttu-id="1bc25-143">GERELATEERDE KOPPELINGEN</span><span class="sxs-lookup"><span data-stu-id="1bc25-143">RELATED LINKS</span></span>
