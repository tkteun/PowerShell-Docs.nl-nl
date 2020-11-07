---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 10/28/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/clear-recyclebin?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Clear-RecycleBin
ms.openlocfilehash: 4131232e7afb2e0a213bbe11f5da7ee3a0071a59
ms.sourcegitcommit: 177ae45034b58ead716853096b2e72e4864e6df6
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 11/07/2020
ms.locfileid: "94344300"
---
# <span data-ttu-id="113eb-103">Clear-RecycleBin</span><span class="sxs-lookup"><span data-stu-id="113eb-103">Clear-RecycleBin</span></span>

## <span data-ttu-id="113eb-104">SAMENVATTING</span><span class="sxs-lookup"><span data-stu-id="113eb-104">SYNOPSIS</span></span>
<span data-ttu-id="113eb-105">Hiermee wordt de inhoud van een prullenbak gewist.</span><span class="sxs-lookup"><span data-stu-id="113eb-105">Clears the contents of a recycle bin.</span></span>

## <span data-ttu-id="113eb-106">SYNTAXIS</span><span class="sxs-lookup"><span data-stu-id="113eb-106">SYNTAX</span></span>

### <span data-ttu-id="113eb-107">Alles</span><span class="sxs-lookup"><span data-stu-id="113eb-107">All</span></span>

```
Clear-RecycleBin [[-DriveLetter] <String[]>] [-Force] [-WhatIf] [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="113eb-108">BESCHRIJVING</span><span class="sxs-lookup"><span data-stu-id="113eb-108">DESCRIPTION</span></span>

<span data-ttu-id="113eb-109">De `Clear-RecycleBin` cmdlet verwijdert de inhoud van de Prullenbak van een computer.</span><span class="sxs-lookup"><span data-stu-id="113eb-109">The `Clear-RecycleBin` cmdlet deletes the content of a computer's recycle bin.</span></span> <span data-ttu-id="113eb-110">Deze actie is vergelijkbaar met het gebruik van een prullenbak van Windows **Empty**.</span><span class="sxs-lookup"><span data-stu-id="113eb-110">This action is like using Windows **Empty Recycle Bin**.</span></span>

<span data-ttu-id="113eb-111">Deze cmdlet is opnieuw toegevoegd in Power shell 7.</span><span class="sxs-lookup"><span data-stu-id="113eb-111">This cmdlet was readded in PowerShell 7.</span></span>

## <span data-ttu-id="113eb-112">VOORBEELDEN</span><span class="sxs-lookup"><span data-stu-id="113eb-112">EXAMPLES</span></span>

### <span data-ttu-id="113eb-113">1: alle prullen bakken wissen</span><span class="sxs-lookup"><span data-stu-id="113eb-113">1: Clear all recycle bins</span></span>

<span data-ttu-id="113eb-114">In dit voor beeld worden alle prullen bakken van de lokale computer gewist.</span><span class="sxs-lookup"><span data-stu-id="113eb-114">In this example, all the local computer's recycle bins are cleared.</span></span>

```powershell
Clear-RecycleBin
```

```Output
Confirm
Are you sure you want to perform this action?
Performing the operation "Clear-RecycleBin" on target "All of the contents of the Recycle Bin".
[Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "Y"):
```

<span data-ttu-id="113eb-115">`Clear-RecycleBin` Hiermee wordt de gebruiker gevraagd om te bevestigen dat alle prullen bakken op de lokale computer moeten worden gewist.</span><span class="sxs-lookup"><span data-stu-id="113eb-115">`Clear-RecycleBin` prompts the user for confirmation to clear all recycle bins on the local computer.</span></span>

### <span data-ttu-id="113eb-116">2: een opgegeven Prullenbak wissen</span><span class="sxs-lookup"><span data-stu-id="113eb-116">2: Clear a specified recycle bin</span></span>

<span data-ttu-id="113eb-117">In dit voor beeld wordt de Prullenbak voor een opgegeven stationsletter gewist.</span><span class="sxs-lookup"><span data-stu-id="113eb-117">This example clears the recycle bin for a specified drive letter.</span></span>

```powershell
Clear-RecycleBin -DriveLetter C
```

<span data-ttu-id="113eb-118">`Clear-RecycleBin` gebruikt de **stationsletter** -para meter om de Prullenbak op het **C** -volume op te geven.</span><span class="sxs-lookup"><span data-stu-id="113eb-118">`Clear-RecycleBin` uses the **DriveLetter** parameter to specify the recycle bin on the **C** volume.</span></span> <span data-ttu-id="113eb-119">De gebruiker wordt gevraagd om bevestiging om de opdracht uit te voeren.</span><span class="sxs-lookup"><span data-stu-id="113eb-119">The user is prompted for confirmation to run the command.</span></span>

### <span data-ttu-id="113eb-120">3: alle prullen bakken wissen zonder bevestiging</span><span class="sxs-lookup"><span data-stu-id="113eb-120">3: Clear all recycle bins without confirmation</span></span>

<span data-ttu-id="113eb-121">In dit voor beeld wordt niet gevraagd om bevestiging om de prullen bakken van de lokale computer te wissen.</span><span class="sxs-lookup"><span data-stu-id="113eb-121">This example doesn't prompt for confirmation to clear the local computer's recycle bins.</span></span>

```powershell
Clear-RecycleBin -Force
```

<span data-ttu-id="113eb-122">`Clear-RecycleBin` gebruikt de **Force** -para meter en vraagt de gebruiker niet om bevestiging om alle prullen bakken op de lokale computer te wissen.</span><span class="sxs-lookup"><span data-stu-id="113eb-122">`Clear-RecycleBin` uses the **Force** parameter and doesn't prompt the user for confirmation to clear all recycle bins on the local computer.</span></span>

<span data-ttu-id="113eb-123">U kunt ook vervangen `-Force` door `-Confirm:$false` .</span><span class="sxs-lookup"><span data-stu-id="113eb-123">An alternative is to replace `-Force` with `-Confirm:$false`.</span></span>

## <span data-ttu-id="113eb-124">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="113eb-124">PARAMETERS</span></span>

### <span data-ttu-id="113eb-125">-Stationsletter</span><span class="sxs-lookup"><span data-stu-id="113eb-125">-DriveLetter</span></span>

<span data-ttu-id="113eb-126">Hiermee geeft u de Prullenbak op die moet worden gewist voor één stationsletter of een reeks stationsletters.</span><span class="sxs-lookup"><span data-stu-id="113eb-126">Specifies the recycle bin to clear for a single drive letter or an array of drive letters.</span></span>

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

### <span data-ttu-id="113eb-127">-Force</span><span class="sxs-lookup"><span data-stu-id="113eb-127">-Force</span></span>

<span data-ttu-id="113eb-128">Geeft aan dat de gebruiker niet om bevestiging wordt gevraagd om een prullenbak te wissen.</span><span class="sxs-lookup"><span data-stu-id="113eb-128">Specifies that the user isn't prompted for confirmation to clear a recycle bin.</span></span>

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

### <span data-ttu-id="113eb-129">-Confirm</span><span class="sxs-lookup"><span data-stu-id="113eb-129">-Confirm</span></span>

<span data-ttu-id="113eb-130">Vraagt om bevestiging van de gebruiker voordat de cmdlet wordt uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="113eb-130">Prompts for user confirmation before running the cmdlet.</span></span> <span data-ttu-id="113eb-131">De gebruiker wordt om bevestiging gevraagd, zelfs als de para meter **confirm** niet is opgegeven.</span><span class="sxs-lookup"><span data-stu-id="113eb-131">The user is prompted for confirmation even if the **Confirm** parameter isn't specified.</span></span>

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

### <span data-ttu-id="113eb-132">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="113eb-132">-WhatIf</span></span>

<span data-ttu-id="113eb-133">Hier wordt weer gegeven wat er gebeurt als er `Clear-RecycleBin` wordt uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="113eb-133">Shows what would happen if `Clear-RecycleBin` runs.</span></span> <span data-ttu-id="113eb-134">De cmdlet wordt niet uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="113eb-134">The cmdlet isn't run.</span></span>

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

### <span data-ttu-id="113eb-135">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="113eb-135">CommonParameters</span></span>

<span data-ttu-id="113eb-136">Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="113eb-136">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="113eb-137">Zie [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="113eb-137">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="113eb-138">INVOER</span><span class="sxs-lookup"><span data-stu-id="113eb-138">INPUTS</span></span>

## <span data-ttu-id="113eb-139">UITVOER</span><span class="sxs-lookup"><span data-stu-id="113eb-139">OUTPUTS</span></span>

### <span data-ttu-id="113eb-140">Geen</span><span class="sxs-lookup"><span data-stu-id="113eb-140">None</span></span>

## <span data-ttu-id="113eb-141">OPMERKINGEN</span><span class="sxs-lookup"><span data-stu-id="113eb-141">NOTES</span></span>

<span data-ttu-id="113eb-142">Deze cmdlet is alleen beschikbaar op Windows-platforms.</span><span class="sxs-lookup"><span data-stu-id="113eb-142">This cmdlet is only available on Windows platforms.</span></span>

## <span data-ttu-id="113eb-143">GERELATEERDE KOPPELINGEN</span><span class="sxs-lookup"><span data-stu-id="113eb-143">RELATED LINKS</span></span>
