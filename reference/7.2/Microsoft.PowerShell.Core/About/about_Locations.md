---
description: Hierin wordt beschreven hoe u toegang krijgt tot items vanaf de werk locatie in Power shell.
Locale: en-US
ms.date: 03/15/2021
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_locations?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Locations
ms.openlocfilehash: e454fe3148ff3e7fdecb52f9fd3b6cdf583b8644
ms.sourcegitcommit: 15f759ca68d17acecab46b52250298d4f2037c4d
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 03/16/2021
ms.locfileid: "103575760"
---
# <a name="about_locations"></a><span data-ttu-id="cb4e8-103">about_Locations</span><span class="sxs-lookup"><span data-stu-id="cb4e8-103">about_Locations</span></span>

## <a name="short-description"></a><span data-ttu-id="cb4e8-104">Korte beschrijving</span><span class="sxs-lookup"><span data-stu-id="cb4e8-104">Short description</span></span>
<span data-ttu-id="cb4e8-105">Hierin wordt beschreven hoe u toegang krijgt tot items vanaf de werk locatie in Power shell.</span><span class="sxs-lookup"><span data-stu-id="cb4e8-105">Describes how to access items from the working location in PowerShell.</span></span>

## <a name="long-description"></a><span data-ttu-id="cb4e8-106">Lange beschrijving</span><span class="sxs-lookup"><span data-stu-id="cb4e8-106">Long description</span></span>

<span data-ttu-id="cb4e8-107">De huidige werk locatie is de standaard locatie waarnaar opdrachten verwijzen.</span><span class="sxs-lookup"><span data-stu-id="cb4e8-107">The current working location is the default location to which commands point.</span></span>
<span data-ttu-id="cb4e8-108">Met andere woorden, dit is de locatie die Power shell gebruikt als u geen expliciet pad opgeeft naar het item of de locatie waarop de opdracht betrekking heeft.</span><span class="sxs-lookup"><span data-stu-id="cb4e8-108">In other words, this is the location that PowerShell uses if you do not supply an explicit path to the item or location that is affected by the command.</span></span>

> [!NOTE]
> <span data-ttu-id="cb4e8-109">Power shell ondersteunt meerdere runspaces per proces.</span><span class="sxs-lookup"><span data-stu-id="cb4e8-109">PowerShell supports multiple runspaces per process.</span></span> <span data-ttu-id="cb4e8-110">Elke runs Pace heeft zijn eigen _huidige map_.</span><span class="sxs-lookup"><span data-stu-id="cb4e8-110">Each runspace has its own _current directory_.</span></span> <span data-ttu-id="cb4e8-111">Dit is niet hetzelfde als de huidige map van het proces: `[System.Environment]::CurrentDirectory` .</span><span class="sxs-lookup"><span data-stu-id="cb4e8-111">This is not the same as the current directory of the process: `[System.Environment]::CurrentDirectory`.</span></span>

<span data-ttu-id="cb4e8-112">In de meeste gevallen is de huidige werk locatie een station dat toegankelijk is via de Power shell-bestands provider en, in sommige gevallen, een map op dat station.</span><span class="sxs-lookup"><span data-stu-id="cb4e8-112">In most cases, the current working location is a drive accessed through the PowerShell FileSystem provider and, in some cases, a directory on that drive.</span></span>
<span data-ttu-id="cb4e8-113">U kunt bijvoorbeeld uw huidige werk locatie op de volgende locatie instellen:</span><span class="sxs-lookup"><span data-stu-id="cb4e8-113">For example, you might set your current working location to the following location:</span></span>

```powershell
C:\Program Files\Windows PowerShell
```

<span data-ttu-id="cb4e8-114">Als gevolg hiervan worden alle opdrachten vanaf deze locatie verwerkt, tenzij er expliciet een ander pad wordt gegeven.</span><span class="sxs-lookup"><span data-stu-id="cb4e8-114">As a result, all commands are processed from this location unless another path is explicitly provided.</span></span>

<span data-ttu-id="cb4e8-115">Power shell onderhoudt de huidige werk locatie voor elk station, zelfs wanneer het station niet het huidige station is.</span><span class="sxs-lookup"><span data-stu-id="cb4e8-115">PowerShell maintains the current working location for each drive even when the drive is not the current drive.</span></span> <span data-ttu-id="cb4e8-116">Hiermee hebt u toegang tot items vanaf de huidige werk locatie door alleen naar het station van een andere locatie te verwijzen.</span><span class="sxs-lookup"><span data-stu-id="cb4e8-116">This allows you to access items from the current working location by referring only to the drive of another location.</span></span>
<span data-ttu-id="cb4e8-117">Stel bijvoorbeeld dat uw huidige werk locatie is `C:\Windows` .</span><span class="sxs-lookup"><span data-stu-id="cb4e8-117">For example, suppose that your current working location is `C:\Windows`.</span></span> <span data-ttu-id="cb4e8-118">Stel nu dat u de volgende opdracht gebruikt om de huidige werk locatie te wijzigen in HKLM: station:</span><span class="sxs-lookup"><span data-stu-id="cb4e8-118">Now, suppose you use the following command to change your current working location to the HKLM: drive:</span></span>

```powershell
Set-Location HKLM:
```

<span data-ttu-id="cb4e8-119">Hoewel uw huidige locatie nu het register station is, kunt u nog steeds toegang krijgen tot items in de `C:\Windows` map met behulp van het station C:, zoals wordt weer gegeven in het volgende voor beeld:</span><span class="sxs-lookup"><span data-stu-id="cb4e8-119">Although your current location is now the registry drive, you can still access items in the `C:\Windows` directory simply by using the C: drive, as shown in the following example:</span></span>

```powershell
Get-ChildItem C:
```

<span data-ttu-id="cb4e8-120">Power shell onthoudt dat uw huidige werk locatie voor dat station de Windows-map is, zodat er items uit die map worden opgehaald.</span><span class="sxs-lookup"><span data-stu-id="cb4e8-120">PowerShell remembers that your current working location for that drive is the Windows directory, so it retrieves items from that directory.</span></span> <span data-ttu-id="cb4e8-121">De resultaten zijn hetzelfde als u de volgende opdracht hebt uitgevoerd:</span><span class="sxs-lookup"><span data-stu-id="cb4e8-121">The results would be the same if you ran the following command:</span></span>

```powershell
Get-ChildItem C:\Windows
```

<span data-ttu-id="cb4e8-122">In Power shell kunt u de opdracht Get-Location gebruiken om de huidige werk locatie te bepalen en kunt u de Set-Location opdracht gebruiken om de huidige werk locatie in te stellen.</span><span class="sxs-lookup"><span data-stu-id="cb4e8-122">In PowerShell, you can use the Get-Location command to determine the current working location, and you can use the Set-Location command to set the current working location.</span></span> <span data-ttu-id="cb4e8-123">Met de volgende opdracht wordt bijvoorbeeld de huidige werk locatie ingesteld op de Windows-map van station C:.</span><span class="sxs-lookup"><span data-stu-id="cb4e8-123">For example, the following command sets the current working location to the Windows directory of the C: drive:</span></span>

```powershell
Set-Location c:\windows
```

<span data-ttu-id="cb4e8-124">Nadat u de huidige werk locatie hebt ingesteld, kunt u nog steeds toegang krijgen tot items vanaf andere stations door simpelweg de stationsnaam (gevolgd door een dubbele punt) op te nemen in de opdracht, zoals in het volgende voor beeld wordt weer gegeven:</span><span class="sxs-lookup"><span data-stu-id="cb4e8-124">After you set the current working location, you can still access items from other drives simply by including the drive name (followed by a colon) in the command, as shown in the following example:</span></span>

```powershell
Get-ChildItem HKLM:\software
```

<span data-ttu-id="cb4e8-125">De voorbeeld opdracht haalt een lijst met items op in de software container van de HKEY lokale machine-component in het REGI ster.</span><span class="sxs-lookup"><span data-stu-id="cb4e8-125">The example command retrieves a list of items in the Software container of the HKEY Local Machine hive in the registry.</span></span>

<span data-ttu-id="cb4e8-126">Met Power shell kunt u ook speciale tekens gebruiken om de huidige werk locatie en de bovenliggende locatie ervan te vertegenwoordigen.</span><span class="sxs-lookup"><span data-stu-id="cb4e8-126">PowerShell also allows you to use special characters to represent the current working location and its parent location.</span></span> <span data-ttu-id="cb4e8-127">Gebruik één punt om de huidige werk locatie weer te geven.</span><span class="sxs-lookup"><span data-stu-id="cb4e8-127">To represent the current working location, use a single period.</span></span> <span data-ttu-id="cb4e8-128">Gebruik twee Peri Oden om het bovenliggende item van de huidige werk locatie weer te geven.</span><span class="sxs-lookup"><span data-stu-id="cb4e8-128">To represent the parent of the current working location, use two periods.</span></span> <span data-ttu-id="cb4e8-129">In het volgende voor beeld wordt de submap System op de huidige werk locatie opgegeven:</span><span class="sxs-lookup"><span data-stu-id="cb4e8-129">For example, the following specifies the System subdirectory in the current working location:</span></span>

```powershell
Get-ChildItem .\system
```

<span data-ttu-id="cb4e8-130">Als de huidige werk locatie is `C:\Windows` , retourneert deze opdracht een lijst met alle items in `C:\Windows\System` .</span><span class="sxs-lookup"><span data-stu-id="cb4e8-130">If the current working location is `C:\Windows`, this command returns a list of all the items in `C:\Windows\System`.</span></span> <span data-ttu-id="cb4e8-131">Als u echter twee Peri Oden gebruikt, wordt de bovenliggende map van de huidige werkmap gebruikt, zoals wordt weer gegeven in het volgende voor beeld:</span><span class="sxs-lookup"><span data-stu-id="cb4e8-131">However, if you use two periods, the parent directory of the current working directory is used, as shown in the following example:</span></span>

```powershell
Get-ChildItem ..\"program files"
```

<span data-ttu-id="cb4e8-132">In dit geval behandelt Power shell de twee Peri Oden als station C:, zodat de opdracht alle items in de map ophaalt `C:\Program Files` .</span><span class="sxs-lookup"><span data-stu-id="cb4e8-132">In this case, PowerShell treats the two periods as the C: drive, so the command retrieves all the items in the `C:\Program Files` directory.</span></span>

<span data-ttu-id="cb4e8-133">Een pad dat begint met een slash identificeert een pad van de hoofdmap van het huidige station.</span><span class="sxs-lookup"><span data-stu-id="cb4e8-133">A path beginning with a slash identifies a path from the root of the current drive.</span></span> <span data-ttu-id="cb4e8-134">Als uw huidige werk locatie bijvoorbeeld is `C:\Program Files\PowerShell` , is de hoofdmap van uw station C. Daarom worden met de volgende opdracht alle items in de `C:\Windows` map weer gegeven:</span><span class="sxs-lookup"><span data-stu-id="cb4e8-134">For example, if your current working location is `C:\Program Files\PowerShell`, the root of your drive is C. Therefore, the following command lists all items in the `C:\Windows` directory:</span></span>

```powershell
Get-ChildItem \windows
```

<span data-ttu-id="cb4e8-135">Als u geen pad opgeeft dat begint met een stationsnaam, slash of periode bij het opgeven van de naam van een container of item, wordt ervan uitgegaan dat de container of het item zich op de huidige werk locatie bevindt.</span><span class="sxs-lookup"><span data-stu-id="cb4e8-135">If you do not specify a path beginning with a drive name, slash, or period when supplying the name of a container or item, the container or item is assumed to be located in the current working location.</span></span> <span data-ttu-id="cb4e8-136">Als uw huidige werk locatie bijvoorbeeld is `C:\Windows` , retourneert de volgende opdracht alle items in de `C:\Windows\System` map:</span><span class="sxs-lookup"><span data-stu-id="cb4e8-136">For example, if your current working location is `C:\Windows`, the following command returns all the items in the `C:\Windows\System` directory:</span></span>

```powershell
Get-ChildItem system
```

<span data-ttu-id="cb4e8-137">Als u een bestands naam opgeeft in plaats van een mapnaam, retourneert Power shell Details over dat bestand (ervan uitgaande dat het bestand zich op de huidige werk locatie bevindt).</span><span class="sxs-lookup"><span data-stu-id="cb4e8-137">If you specify a file name rather than a directory name, PowerShell returns details about that file (assuming that file is located in the current working location).</span></span>

## <a name="see-also"></a><span data-ttu-id="cb4e8-138">Zie ook</span><span class="sxs-lookup"><span data-stu-id="cb4e8-138">See also</span></span>

[<span data-ttu-id="cb4e8-139">Set-Location</span><span class="sxs-lookup"><span data-stu-id="cb4e8-139">Set-Location</span></span>](xref:Microsoft.PowerShell.Management.Set-Location)

[<span data-ttu-id="cb4e8-140">about_Providers</span><span class="sxs-lookup"><span data-stu-id="cb4e8-140">about_Providers</span></span>](about_Providers.md)

[<span data-ttu-id="cb4e8-141">about_Path_Syntax</span><span class="sxs-lookup"><span data-stu-id="cb4e8-141">about_Path_Syntax</span></span>](about_Path_Syntax.md)
