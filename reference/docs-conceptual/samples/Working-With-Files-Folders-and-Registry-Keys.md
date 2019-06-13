---
ms.date: 06/05/2017
keywords: PowerShell-cmdlet
title: Met bestanden, mappen en registersleutels werken
ms.openlocfilehash: 0c8716c384827d0816e2847ff81232c14638681b
ms.sourcegitcommit: a6f13c16a535acea279c0ddeca72f1f0d8a8ce4c
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 06/12/2019
ms.locfileid: "67030758"
---
# <a name="working-with-files-folders-and-registry-keys"></a><span data-ttu-id="d111f-103">Werken met bestanden, mappen en registersleutels</span><span class="sxs-lookup"><span data-stu-id="d111f-103">Working With Files, Folders and Registry Keys</span></span>

<span data-ttu-id="d111f-104">Windows PowerShell maakt gebruik van het zelfstandig naamwoord **Item** om te verwijzen naar items gevonden op een Windows PowerShell-station.</span><span class="sxs-lookup"><span data-stu-id="d111f-104">Windows PowerShell uses the noun **Item** to refer to items found on a Windows PowerShell drive.</span></span> <span data-ttu-id="d111f-105">Wanneer er sprake is van het bestandssysteem van Windows PowerShell-provider, een **Item** mogelijk een bestand, een map of het Windows PowerShell-station.</span><span class="sxs-lookup"><span data-stu-id="d111f-105">When dealing with the Windows PowerShell FileSystem provider, an **Item** might be a file, a folder, or the Windows PowerShell drive.</span></span> <span data-ttu-id="d111f-106">Lijst van en werken met de volgende items is een kritieke eenvoudige taak in de meeste instellingen voor de administratieve, zodat we willen deze taken in detail bespreken.</span><span class="sxs-lookup"><span data-stu-id="d111f-106">Listing and working with these items is a critical basic task in most administrative settings, so we want to discuss these tasks in detail.</span></span>

## <a name="enumerating-files-folders-and-registry-keys-get-childitem"></a><span data-ttu-id="d111f-107">Het inventariseren van bestanden, mappen en registersleutels (Get-ChildItem)</span><span class="sxs-lookup"><span data-stu-id="d111f-107">Enumerating Files, Folders, and Registry Keys (Get-ChildItem)</span></span>

<span data-ttu-id="d111f-108">Sinds het ophalen van een verzameling items uit een bepaalde locatie is een veelvoorkomende taak, de **Get-ChildItem** cmdlet is speciaal ontworpen om te retourneren van alle items gevonden in een container, zoals een map.</span><span class="sxs-lookup"><span data-stu-id="d111f-108">Since getting a collection of items from a particular location is such a common task, the **Get-ChildItem** cmdlet is designed specifically to return all items found within a container such as a folder.</span></span>

<span data-ttu-id="d111f-109">Als u wilt retourneren van alle bestanden en mappen die zich rechtstreeks in de map C:\\Windows, type:</span><span class="sxs-lookup"><span data-stu-id="d111f-109">If you want to return all files and folders that are contained directly within the folder C:\\Windows, type:</span></span>

```
PS> Get-ChildItem -Path C:\Windows
    Directory: Microsoft.Windows PowerShell.Core\FileSystem::C:\Windows

Mode                LastWriteTime     Length Name
----                -------------     ------ ----
-a---        2006-05-16   8:10 AM          0 0.log
-a---        2005-11-29   3:16 PM         97 acc1.txt
-a---        2005-10-23  11:21 PM       3848 actsetup.log
...
```

<span data-ttu-id="d111f-110">De aanbieding lijkt op wat u zien wilt bij het invoeren van de **dir** opdracht in **Cmd.exe**, of de **ls** opdracht in een UNIX-opdrachtshell.</span><span class="sxs-lookup"><span data-stu-id="d111f-110">The listing looks similar to what you would see when you enter the **dir** command in **Cmd.exe**, or the **ls** command in a UNIX command shell.</span></span>

<span data-ttu-id="d111f-111">U kunt zeer complex aanbiedingen uitvoeren met behulp van parameters van de **Get-ChildItem** cmdlet.</span><span class="sxs-lookup"><span data-stu-id="d111f-111">You can perform very complex listings by using parameters of the **Get-ChildItem** cmdlet.</span></span> <span data-ttu-id="d111f-112">We kijken we enkele scenario's vervolgens.</span><span class="sxs-lookup"><span data-stu-id="d111f-112">We will look at a few scenarios next.</span></span> <span data-ttu-id="d111f-113">U kunt zien dat de syntaxis van de **Get-ChildItem** cmdlet door te typen:</span><span class="sxs-lookup"><span data-stu-id="d111f-113">You can see the syntax the **Get-ChildItem** cmdlet by typing:</span></span>

```powershell
Get-Command -Name Get-ChildItem -Syntax
```

<span data-ttu-id="d111f-114">Deze parameters kunnen worden gecombineerd en afgestemd om uitvoer op maat gemaakte te halen.</span><span class="sxs-lookup"><span data-stu-id="d111f-114">These parameters can be mixed and matched to get highly customized output.</span></span>

### <a name="listing-all-contained-items--recurse"></a><span data-ttu-id="d111f-115">Alle opgenomen objecten te bieden (-Recurse)</span><span class="sxs-lookup"><span data-stu-id="d111f-115">Listing all Contained Items (-Recurse)</span></span>

<span data-ttu-id="d111f-116">Als zowel de items in een Windows-map en alle items die zijn opgenomen in de submappen weergeven, gebruikt u de **Recurse** parameter van **Get-ChildItem**.</span><span class="sxs-lookup"><span data-stu-id="d111f-116">To see both the items inside a Windows folder and any items that are contained within the subfolders, use the **Recurse** parameter of **Get-ChildItem**.</span></span> <span data-ttu-id="d111f-117">De aanbieding wordt weergegeven dat alles in de Windows-map en de items in submappen.</span><span class="sxs-lookup"><span data-stu-id="d111f-117">The listing displays everything within the Windows folder and the items in its subfolders.</span></span> <span data-ttu-id="d111f-118">Bijvoorbeeld:</span><span class="sxs-lookup"><span data-stu-id="d111f-118">For example:</span></span>

```
PS> Get-ChildItem -Path C:\WINDOWS -Recurse

    Directory: Microsoft.Windows PowerShell.Core\FileSystem::C:\WINDOWS
    Directory: Microsoft.Windows PowerShell.Core\FileSystem::C:\WINDOWS\AppPatch
Mode                LastWriteTime     Length Name
----                -------------     ------ ----
-a---        2004-08-04   8:00 AM    1852416 AcGenral.dll
...
```

### <a name="filtering-items-by-name--name"></a><span data-ttu-id="d111f-119">Items met de naam filteren (-naam)</span><span class="sxs-lookup"><span data-stu-id="d111f-119">Filtering Items by Name (-Name)</span></span>

<span data-ttu-id="d111f-120">Als u alleen de namen van items weergeven, gebruiken de **naam** parameter van **Get-Childitem**:</span><span class="sxs-lookup"><span data-stu-id="d111f-120">To display only the names of items, use the **Name** parameter of **Get-Childitem**:</span></span>

```
PS> Get-ChildItem -Path C:\WINDOWS -Name
addins
AppPatch
assembly
...
```

### <a name="forcibly-listing-hidden-items--force"></a><span data-ttu-id="d111f-121">Geforceerd verborgen Items weergeven (-Force)</span><span class="sxs-lookup"><span data-stu-id="d111f-121">Forcibly Listing Hidden Items (-Force)</span></span>

<span data-ttu-id="d111f-122">Items die normaal gesproken niet zichtbaar in Verkenner of Cmd.exe zijn worden niet weergegeven in de uitvoer van een **Get-ChildItem** opdracht.</span><span class="sxs-lookup"><span data-stu-id="d111f-122">Items that are normally invisible in File Explorer or Cmd.exe are not displayed in the output of a **Get-ChildItem** command.</span></span> <span data-ttu-id="d111f-123">Als u verborgen items weergeven, gebruiken de **Force** parameter van **Get-ChildItem**.</span><span class="sxs-lookup"><span data-stu-id="d111f-123">To display hidden items, use the **Force** parameter of **Get-ChildItem**.</span></span> <span data-ttu-id="d111f-124">Bijvoorbeeld:</span><span class="sxs-lookup"><span data-stu-id="d111f-124">For example:</span></span>

```powershell
Get-ChildItem -Path C:\Windows -Force
```

<span data-ttu-id="d111f-125">Deze parameter is met de naam Force omdat u kunt het normale gedrag van geforceerd overschrijven de **Get-ChildItem** opdracht.</span><span class="sxs-lookup"><span data-stu-id="d111f-125">This parameter is named Force because you can forcibly override the normal behavior of the **Get-ChildItem** command.</span></span> <span data-ttu-id="d111f-126">Force is een veelgebruikte parameter die ervoor zorgt een actie die een cmdlet niet normaal kunt uitvoeren, dat hoewel een actie op die de beveiliging van het systeem wordt aangetast wordt niet uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="d111f-126">Force is a widely used parameter that forces an action that a cmdlet would not normally perform, although it will not perform any action that compromises the security of the system.</span></span>

### <a name="matching-item-names-with-wildcards"></a><span data-ttu-id="d111f-127">Overeenkomende itemnamen met jokertekens</span><span class="sxs-lookup"><span data-stu-id="d111f-127">Matching Item Names with Wildcards</span></span>

<span data-ttu-id="d111f-128">**De Get-ChildItem** opdracht jokertekens in het pad van de items om weer te geven.</span><span class="sxs-lookup"><span data-stu-id="d111f-128">**The Get-ChildItem** command accepts wildcards in the path of the items to list.</span></span>

<span data-ttu-id="d111f-129">Omdat jokertekens worden verwerkt door de Windows PowerShell-engine, worden alle cmdlets die jokertekens gebruiken de dezelfde notatie en hebben hetzelfde gedrag overeenkomende.</span><span class="sxs-lookup"><span data-stu-id="d111f-129">Because wildcard matching is handled by the Windows PowerShell engine, all cmdlets that accepts wildcards use the same notation and have the same matching behavior.</span></span> <span data-ttu-id="d111f-130">De notatie van de Windows PowerShell-jokertekens bevat:</span><span class="sxs-lookup"><span data-stu-id="d111f-130">The Windows PowerShell wildcard notation includes:</span></span>

- <span data-ttu-id="d111f-131">Sterretje (\*) komt overeen met nul of meer exemplaren van een willekeurig teken.</span><span class="sxs-lookup"><span data-stu-id="d111f-131">Asterisk (\*)matches zero or more occurrences of any character.</span></span>

- <span data-ttu-id="d111f-132">Vraagteken (?) komt overeen met precies één teken.</span><span class="sxs-lookup"><span data-stu-id="d111f-132">Question mark (?) matches exactly one character.</span></span>

- <span data-ttu-id="d111f-133">Haakje openen (\[) en teken rechte haak sluiten (]) rondom een reeks tekens worden vergeleken.</span><span class="sxs-lookup"><span data-stu-id="d111f-133">Left bracket (\[) character and right bracket (]) character surround a set of characters to be matched.</span></span>

<span data-ttu-id="d111f-134">Hier volgen enkele voorbeelden van de werking van jokertekens-specificatie.</span><span class="sxs-lookup"><span data-stu-id="d111f-134">Here are some examples of how wildcard specification works.</span></span>

<span data-ttu-id="d111f-135">Zoeken naar alle bestanden in de Windows-map met het achtervoegsel **.log** en exact vijf tekens in de naam van de basis, voer de volgende opdracht:</span><span class="sxs-lookup"><span data-stu-id="d111f-135">To find all files in the Windows directory with the suffix **.log** and exactly five characters in the base name, enter the following command:</span></span>

```
PS> Get-ChildItem -Path C:\Windows\?????.log

    Directory: Microsoft.Windows PowerShell.Core\FileSystem::C:\Windows
Mode                LastWriteTime     Length Name
----                -------------     ------ ----
...
-a---        2006-05-11   6:31 PM     204276 ocgen.log
-a---        2006-05-11   6:31 PM      22365 ocmsn.log
...
-a---        2005-11-11   4:55 AM         64 setup.log
-a---        2005-12-15   2:24 PM      17719 VxSDM.log
...
```

<span data-ttu-id="d111f-136">Zoeken naar alle bestanden die met de letter beginnen **x** in de Windows-map, typ:</span><span class="sxs-lookup"><span data-stu-id="d111f-136">To find all files that begin with the letter **x** in the Windows directory, type:</span></span>

```powershell
Get-ChildItem -Path C:\Windows\x*
```

<span data-ttu-id="d111f-137">Zoeken naar alle bestanden waarvan de namen met beginnen **x** of **z**, type:</span><span class="sxs-lookup"><span data-stu-id="d111f-137">To find all files whose names begin with **x** or **z**, type:</span></span>

```powershell
Get-ChildItem -Path C:\Windows\[xz]*
```

### <a name="excluding-items--exclude"></a><span data-ttu-id="d111f-138">Items uitsluiten (-uitsluiten)</span><span class="sxs-lookup"><span data-stu-id="d111f-138">Excluding Items (-Exclude)</span></span>

<span data-ttu-id="d111f-139">U kunt specifieke objecten uitsluiten met behulp van de **uitsluiten** parameter van Get-ChildItem.</span><span class="sxs-lookup"><span data-stu-id="d111f-139">You can exclude specific items by using the **Exclude** parameter of Get-ChildItem.</span></span> <span data-ttu-id="d111f-140">Hiermee kunt u complexe filteren in één instructie uitvoeren.</span><span class="sxs-lookup"><span data-stu-id="d111f-140">This lets you perform complex filtering in a single statement.</span></span>

<span data-ttu-id="d111f-141">Stel bijvoorbeeld dat u wilt het DLL-bestand van Windows Time-Service niet vinden in de map System32 en u kunt meer weet over de dll-naam, is dat het begint met de letter "W" en "32" bevat.</span><span class="sxs-lookup"><span data-stu-id="d111f-141">For example, suppose you are trying to find the Windows Time Service DLL in the System32 folder, and all you can remember about the DLL name is that it begins with "W" and has "32" in it.</span></span>

<span data-ttu-id="d111f-142">Een expressie, zoals **w\&#42; 32\&#42;. DLL-bestand** vindt u alle dll-bestanden die voldoen aan de voorwaarden, maar het kan ook de Windows 95 en 16-bits Windows-compatibiliteit dll-bestanden die zijn '95' of '16' terug in hun namen.</span><span class="sxs-lookup"><span data-stu-id="d111f-142">An expression like **w\&#42;32\&#42;.dll** will find all DLLs that satisfy the conditions, but it may also return the Windows 95 and 16-bit Windows compatibility DLLs that include "95" or "16" in their names.</span></span> <span data-ttu-id="d111f-143">U kunt weglaten bestanden die een van deze getallen in hun namen met behulp van hebben de **uitsluiten** parameter met het patroon  **\&#42;\[ 9516]\&#42;** :</span><span class="sxs-lookup"><span data-stu-id="d111f-143">You can omit files that have any of these numbers in their names by using the **Exclude** parameter with the pattern **\&#42;\[9516]\&#42;**:</span></span>

```
PS> Get-ChildItem -Path C:\WINDOWS\System32\w*32*.dll -Exclude *[9516]*

Directory: Microsoft.PowerShell.Core\FileSystem::C:\WINDOWS\System32
Mode                LastWriteTime     Length Name
----                -------------     ------ ----
-a---        2004-08-04   8:00 AM     174592 w32time.dll
-a---        2004-08-04   8:00 AM      22016 w32topl.dll
-a---        2004-08-04   8:00 AM     101888 win32spl.dll
-a---        2004-08-04   8:00 AM     172032 wldap32.dll
-a---        2004-08-04   8:00 AM     264192 wow32.dll
-a---        2004-08-04   8:00 AM      82944 ws2_32.dll
-a---        2004-08-04   8:00 AM      42496 wsnmp32.dll
-a---        2004-08-04   8:00 AM      22528 wsock32.dll
-a---        2004-08-04   8:00 AM      18432 wtsapi32.dll
```

### <a name="mixing-get-childitem-parameters"></a><span data-ttu-id="d111f-144">Met een combinatie van Parameters voor Get-ChildItem</span><span class="sxs-lookup"><span data-stu-id="d111f-144">Mixing Get-ChildItem Parameters</span></span>

<span data-ttu-id="d111f-145">U kunt meerdere van de parameters van de **Get-ChildItem** cmdlet in dezelfde opdracht.</span><span class="sxs-lookup"><span data-stu-id="d111f-145">You can use several of the parameters of the **Get-ChildItem** cmdlet in the same command.</span></span> <span data-ttu-id="d111f-146">Voordat u parameters combineren, moet u dat u bekend bent met jokertekens.</span><span class="sxs-lookup"><span data-stu-id="d111f-146">Before you mix parameters, be sure that you understand wildcard matching.</span></span> <span data-ttu-id="d111f-147">De volgende opdracht retourneert bijvoorbeeld geen resultaten:</span><span class="sxs-lookup"><span data-stu-id="d111f-147">For example, the following command returns no results:</span></span>

```powershell
Get-ChildItem -Path C:\Windows\*.dll -Recurse -Exclude [a-y]*.dll
```

<span data-ttu-id="d111f-148">Er zijn geen resultaten, zelfs als er zijn twee dll-bestanden die met de letter 'z' in de Windows-map beginnen.</span><span class="sxs-lookup"><span data-stu-id="d111f-148">There are no results, even though there are two DLLs that begin with the letter "z" in the Windows folder.</span></span>

<span data-ttu-id="d111f-149">Er zijn geen resultaten geretourneerd omdat we het jokerteken is opgegeven als onderdeel van het pad.</span><span class="sxs-lookup"><span data-stu-id="d111f-149">No results were returned because we specified the wildcard as part of the path.</span></span> <span data-ttu-id="d111f-150">Hoewel de opdracht recursieve, is de **Get-ChildItem** cmdlet beperkt de items die zich in de Windows-map met namen die eindigen op '.dll'.</span><span class="sxs-lookup"><span data-stu-id="d111f-150">Even though the command was recursive, the **Get-ChildItem** cmdlet restricted the items to those that are in the Windows folder with names ending with ".dll".</span></span>

<span data-ttu-id="d111f-151">Als u wilt een recursieve zoekopdracht voor bestanden waarvan de namen overeenkomen met een speciale patroon opgeven, gebruikt u de **-opnemen** parameter.</span><span class="sxs-lookup"><span data-stu-id="d111f-151">To specify a recursive search for files whose names match a special pattern, use the **-Include** parameter.</span></span>

```
PS> Get-ChildItem -Path C:\Windows -Include *.dll -Recurse -Exclude [a-y]*.dll

    Directory: Microsoft.Windows PowerShell.Core\FileSystem::C:\Windows\System32\Setup

Mode                LastWriteTime     Length Name
----                -------------     ------ ----
-a---        2004-08-04   8:00 AM       8261 zoneoc.dll

    Directory: Microsoft.Windows PowerShell.Core\FileSystem::C:\Windows\System32

Mode                LastWriteTime     Length Name
----                -------------     ------ ----
-a---        2004-08-04   8:00 AM     337920 zipfldr.dll
```
