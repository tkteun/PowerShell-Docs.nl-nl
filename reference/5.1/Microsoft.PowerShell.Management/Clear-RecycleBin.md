---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 01/29/2021
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/clear-recyclebin?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Clear-RecycleBin
ms.openlocfilehash: f59cc9ff4e6d1b6579292c84f440bbbdd156b65c
ms.sourcegitcommit: 81558c2adb9d109946a027e5b96e4d24b3b13747
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 01/30/2021
ms.locfileid: "99098560"
---
# <span data-ttu-id="7a5b8-102">Clear-RecycleBin</span><span class="sxs-lookup"><span data-stu-id="7a5b8-102">Clear-RecycleBin</span></span>

## <span data-ttu-id="7a5b8-103">SAMENVATTING</span><span class="sxs-lookup"><span data-stu-id="7a5b8-103">SYNOPSIS</span></span>
<span data-ttu-id="7a5b8-104">Hiermee wordt de inhoud van een prullenbak gewist.</span><span class="sxs-lookup"><span data-stu-id="7a5b8-104">Clears the contents of a recycle bin.</span></span>

## <span data-ttu-id="7a5b8-105">SYNTAXIS</span><span class="sxs-lookup"><span data-stu-id="7a5b8-105">SYNTAX</span></span>

### <span data-ttu-id="7a5b8-106">Alles</span><span class="sxs-lookup"><span data-stu-id="7a5b8-106">All</span></span>

```
Clear-RecycleBin [[-DriveLetter] <String[]>] [-Force] [-WhatIf] [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="7a5b8-107">BESCHRIJVING</span><span class="sxs-lookup"><span data-stu-id="7a5b8-107">DESCRIPTION</span></span>

<span data-ttu-id="7a5b8-108">De `Clear-RecycleBin` cmdlet verwijdert de inhoud van de Prullenbak van een computer.</span><span class="sxs-lookup"><span data-stu-id="7a5b8-108">The `Clear-RecycleBin` cmdlet deletes the content of a computer's recycle bin.</span></span> <span data-ttu-id="7a5b8-109">Deze actie is vergelijkbaar met het gebruik van een prullenbak van Windows **Empty**.</span><span class="sxs-lookup"><span data-stu-id="7a5b8-109">This action is like using Windows **Empty Recycle Bin**.</span></span>

## <span data-ttu-id="7a5b8-110">VOORBEELDEN</span><span class="sxs-lookup"><span data-stu-id="7a5b8-110">EXAMPLES</span></span>

### <span data-ttu-id="7a5b8-111">1: alle prullen bakken wissen</span><span class="sxs-lookup"><span data-stu-id="7a5b8-111">1: Clear all recycle bins</span></span>

<span data-ttu-id="7a5b8-112">In dit voor beeld worden alle prullen bakken van de lokale computer gewist.</span><span class="sxs-lookup"><span data-stu-id="7a5b8-112">In this example, all the local computer's recycle bins are cleared.</span></span>

```powershell
Clear-RecycleBin
```

```Output
Confirm
Are you sure you want to perform this action?
Performing the operation "Clear-RecycleBin" on target "All of the contents of the Recycle Bin".
[Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "Y"):
```

<span data-ttu-id="7a5b8-113">`Clear-RecycleBin` Hiermee wordt de gebruiker gevraagd om te bevestigen dat alle prullen bakken op de lokale computer moeten worden gewist.</span><span class="sxs-lookup"><span data-stu-id="7a5b8-113">`Clear-RecycleBin` prompts the user for confirmation to clear all recycle bins on the local computer.</span></span>

### <span data-ttu-id="7a5b8-114">2: een opgegeven Prullenbak wissen</span><span class="sxs-lookup"><span data-stu-id="7a5b8-114">2: Clear a specified recycle bin</span></span>

<span data-ttu-id="7a5b8-115">In dit voor beeld wordt de Prullenbak voor een opgegeven stationsletter gewist.</span><span class="sxs-lookup"><span data-stu-id="7a5b8-115">This example clears the recycle bin for a specified drive letter.</span></span>

```powershell
Clear-RecycleBin -DriveLetter C
```

<span data-ttu-id="7a5b8-116">`Clear-RecycleBin` gebruikt de **stationsletter** -para meter om de Prullenbak op het **C** -volume op te geven.</span><span class="sxs-lookup"><span data-stu-id="7a5b8-116">`Clear-RecycleBin` uses the **DriveLetter** parameter to specify the recycle bin on the **C** volume.</span></span> <span data-ttu-id="7a5b8-117">De gebruiker wordt gevraagd om bevestiging om de opdracht uit te voeren.</span><span class="sxs-lookup"><span data-stu-id="7a5b8-117">The user is prompted for confirmation to run the command.</span></span>

### <span data-ttu-id="7a5b8-118">3: alle prullen bakken wissen zonder bevestiging</span><span class="sxs-lookup"><span data-stu-id="7a5b8-118">3: Clear all recycle bins without confirmation</span></span>

<span data-ttu-id="7a5b8-119">In dit voor beeld wordt niet gevraagd om bevestiging om de prullen bakken van de lokale computer te wissen.</span><span class="sxs-lookup"><span data-stu-id="7a5b8-119">This example doesn't prompt for confirmation to clear the local computer's recycle bins.</span></span>

```powershell
Clear-RecycleBin -Force
```

<span data-ttu-id="7a5b8-120">`Clear-RecycleBin` gebruikt de **Force** -para meter en vraagt de gebruiker niet om bevestiging om alle prullen bakken op de lokale computer te wissen.</span><span class="sxs-lookup"><span data-stu-id="7a5b8-120">`Clear-RecycleBin` uses the **Force** parameter and doesn't prompt the user for confirmation to clear all recycle bins on the local computer.</span></span>

<span data-ttu-id="7a5b8-121">U kunt ook vervangen `-Force` door `-Confirm:$false` .</span><span class="sxs-lookup"><span data-stu-id="7a5b8-121">An alternative is to replace `-Force` with `-Confirm:$false`.</span></span>

## <span data-ttu-id="7a5b8-122">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="7a5b8-122">PARAMETERS</span></span>

### <span data-ttu-id="7a5b8-123">-Stationsletter</span><span class="sxs-lookup"><span data-stu-id="7a5b8-123">-DriveLetter</span></span>

<span data-ttu-id="7a5b8-124">Hiermee geeft u de Prullenbak op die moet worden gewist voor één stationsletter of een reeks stationsletters.</span><span class="sxs-lookup"><span data-stu-id="7a5b8-124">Specifies the recycle bin to clear for a single drive letter or an array of drive letters.</span></span>

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

### <span data-ttu-id="7a5b8-125">-Force</span><span class="sxs-lookup"><span data-stu-id="7a5b8-125">-Force</span></span>

<span data-ttu-id="7a5b8-126">Geeft aan dat de gebruiker niet om bevestiging wordt gevraagd om een prullenbak te wissen.</span><span class="sxs-lookup"><span data-stu-id="7a5b8-126">Specifies that the user isn't prompted for confirmation to clear a recycle bin.</span></span> <span data-ttu-id="7a5b8-127">De para meter **Force** onderdrukt ook de para meters **WhatIf** en **confirm** .</span><span class="sxs-lookup"><span data-stu-id="7a5b8-127">The **Force** parameter also overrides the **WhatIf** and **Confirm** parameters.</span></span>

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

### <span data-ttu-id="7a5b8-128">-Confirm</span><span class="sxs-lookup"><span data-stu-id="7a5b8-128">-Confirm</span></span>

<span data-ttu-id="7a5b8-129">Vraagt om bevestiging van de gebruiker voordat de cmdlet wordt uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="7a5b8-129">Prompts for user confirmation before running the cmdlet.</span></span> <span data-ttu-id="7a5b8-130">De gebruiker wordt om bevestiging gevraagd, zelfs als de para meter **confirm** niet is opgegeven.</span><span class="sxs-lookup"><span data-stu-id="7a5b8-130">The user is prompted for confirmation even if the **Confirm** parameter isn't specified.</span></span>

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

### <span data-ttu-id="7a5b8-131">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="7a5b8-131">-WhatIf</span></span>

<span data-ttu-id="7a5b8-132">Hier wordt weer gegeven wat er gebeurt als er `Clear-RecycleBin` wordt uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="7a5b8-132">Shows what would happen if `Clear-RecycleBin` runs.</span></span> <span data-ttu-id="7a5b8-133">De cmdlet wordt niet uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="7a5b8-133">The cmdlet isn't run.</span></span>

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

### <span data-ttu-id="7a5b8-134">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="7a5b8-134">CommonParameters</span></span>

<span data-ttu-id="7a5b8-135">Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="7a5b8-135">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="7a5b8-136">Zie [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="7a5b8-136">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="7a5b8-137">INVOER</span><span class="sxs-lookup"><span data-stu-id="7a5b8-137">INPUTS</span></span>

## <span data-ttu-id="7a5b8-138">UITVOER</span><span class="sxs-lookup"><span data-stu-id="7a5b8-138">OUTPUTS</span></span>

### <span data-ttu-id="7a5b8-139">Geen</span><span class="sxs-lookup"><span data-stu-id="7a5b8-139">None</span></span>

## <span data-ttu-id="7a5b8-140">OPMERKINGEN</span><span class="sxs-lookup"><span data-stu-id="7a5b8-140">NOTES</span></span>

## <span data-ttu-id="7a5b8-141">GERELATEERDE KOPPELINGEN</span><span class="sxs-lookup"><span data-stu-id="7a5b8-141">RELATED LINKS</span></span>
