---
ms.date: 06/05/2017
keywords: PowerShell-cmdlet
title: Met bestanden, mappen en registersleutels werken
ms.assetid: e6cf87aa-b5f8-48d5-a75a-7cb7ecb482dc
ms.openlocfilehash: a09b127d4ba37d33cb4c0f0ce0819e645fd4b137
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 04/09/2018
---
# <a name="working-with-files-folders-and-registry-keys"></a><span data-ttu-id="a2f35-103">Werken met bestanden, mappen en registersleutels</span><span class="sxs-lookup"><span data-stu-id="a2f35-103">Working With Files, Folders and Registry Keys</span></span>

<span data-ttu-id="a2f35-104">Windows PowerShell maakt gebruik van het zelfstandig naamwoord **Item** om te verwijzen naar objecten gevonden op een Windows PowerShell-station.</span><span class="sxs-lookup"><span data-stu-id="a2f35-104">Windows PowerShell uses the noun **Item** to refer to items found on a Windows PowerShell drive.</span></span> <span data-ttu-id="a2f35-105">Het bestandssysteem van Windows PowerShell-provider betreft een **Item** mogelijk een bestand, een map of het Windows PowerShell-station.</span><span class="sxs-lookup"><span data-stu-id="a2f35-105">When dealing with the Windows PowerShell FileSystem provider, an **Item** might be a file, a folder, or the Windows PowerShell drive.</span></span> <span data-ttu-id="a2f35-106">Aanbieding van en werken met de volgende items is een kritieke basic taak in de meeste beheerinstellingen, zodat we willen deze taken in detail behandeld.</span><span class="sxs-lookup"><span data-stu-id="a2f35-106">Listing and working with these items is a critical basic task in most administrative settings, so we want to discuss these tasks in detail.</span></span>

### <a name="enumerating-files-folders-and-registry-keys-get-childitem"></a><span data-ttu-id="a2f35-107">Het inventariseren van bestanden, mappen en registersleutels (Get-ChildItem)</span><span class="sxs-lookup"><span data-stu-id="a2f35-107">Enumerating Files, Folders, and Registry Keys (Get-ChildItem)</span></span>

<span data-ttu-id="a2f35-108">Omdat een verzameling items ophalen uit een bepaalde locatie een algemene taak is, de **Get-ChildItem** cmdlet is speciaal ontworpen om te retourneren van alle items gevonden binnen een container, zoals een map.</span><span class="sxs-lookup"><span data-stu-id="a2f35-108">Since getting a collection of items from a particular location is such a common task, the **Get-ChildItem** cmdlet is designed specifically to return all items found within a container such as a folder.</span></span>

<span data-ttu-id="a2f35-109">Als u wilt retourneren van alle bestanden en mappen die zijn opgenomen in de map C: rechtstreeks\\Windows, type:</span><span class="sxs-lookup"><span data-stu-id="a2f35-109">If you want to return all files and folders that are contained directly within the folder C:\\Windows, type:</span></span>

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

<span data-ttu-id="a2f35-110">De aanbieding lijkt op wat u ziet wanneer u de **dir** opdracht in **Cmd.exe**, of de **ls** opdracht in een UNIX-opdrachtshell.</span><span class="sxs-lookup"><span data-stu-id="a2f35-110">The listing looks similar to what you would see when you enter the **dir** command in **Cmd.exe**, or the **ls** command in a UNIX command shell.</span></span>

<span data-ttu-id="a2f35-111">U kunt zeer complexe aanbiedingen uitvoeren met behulp van de parameters van de **Get-ChildItem** cmdlet.</span><span class="sxs-lookup"><span data-stu-id="a2f35-111">You can perform very complex listings by using parameters of the **Get-ChildItem** cmdlet.</span></span> <span data-ttu-id="a2f35-112">Kijken we enkele scenario's naast.</span><span class="sxs-lookup"><span data-stu-id="a2f35-112">We will look at a few scenarios next.</span></span> <span data-ttu-id="a2f35-113">Ziet u de syntaxis van de **Get-ChildItem** cmdlet door te typen:</span><span class="sxs-lookup"><span data-stu-id="a2f35-113">You can see the syntax the **Get-ChildItem** cmdlet by typing:</span></span>

```powershell
Get-Command -Name Get-ChildItem -Syntax
```

<span data-ttu-id="a2f35-114">Deze parameters kunnen worden gecombineerd en worden aangepast om zeer aangepaste uitvoer te halen.</span><span class="sxs-lookup"><span data-stu-id="a2f35-114">These parameters can be mixed and matched to get highly customized output.</span></span>

#### <a name="listing-all-contained-items--recurse"></a><span data-ttu-id="a2f35-115">Lijst van alle opgenomen Items (-Recurse)</span><span class="sxs-lookup"><span data-stu-id="a2f35-115">Listing all Contained Items (-Recurse)</span></span>

<span data-ttu-id="a2f35-116">Als zowel de items in een Windows-map en alle items die deel uitmaken van de submappen wilt weergeven, gebruikt de **Recurse** parameter van **Get-ChildItem**.</span><span class="sxs-lookup"><span data-stu-id="a2f35-116">To see both the items inside a Windows folder and any items that are contained within the subfolders, use the **Recurse** parameter of **Get-ChildItem**.</span></span> <span data-ttu-id="a2f35-117">De aanbieding wordt alles weergegeven in de Windows-map en de items in de submappen ervan.</span><span class="sxs-lookup"><span data-stu-id="a2f35-117">The listing displays everything within the Windows folder and the items in its subfolders.</span></span> <span data-ttu-id="a2f35-118">Bijvoorbeeld:</span><span class="sxs-lookup"><span data-stu-id="a2f35-118">For example:</span></span>

```
PS> Get-ChildItem -Path C:\WINDOWS -Recurse

    Directory: Microsoft.Windows PowerShell.Core\FileSystem::C:\WINDOWS
    Directory: Microsoft.Windows PowerShell.Core\FileSystem::C:\WINDOWS\AppPatch
Mode                LastWriteTime     Length Name
----                -------------     ------ ----
-a---        2004-08-04   8:00 AM    1852416 AcGenral.dll
...
```

#### <a name="filtering-items-by-name--name"></a><span data-ttu-id="a2f35-119">Items met de naam filteren (-naam)</span><span class="sxs-lookup"><span data-stu-id="a2f35-119">Filtering Items by Name (-Name)</span></span>

<span data-ttu-id="a2f35-120">Alleen de namen van items weergegeven, gebruikt u de **naam** parameter van **Get-Childitem**:</span><span class="sxs-lookup"><span data-stu-id="a2f35-120">To display only the names of items, use the **Name** parameter of **Get-Childitem**:</span></span>

```
PS> Get-ChildItem -Path C:\WINDOWS -Name
addins
AppPatch
assembly
...
```

#### <a name="forcibly-listing-hidden-items--force"></a><span data-ttu-id="a2f35-121">Geforceerd verborgen Items weergeven (-Force)</span><span class="sxs-lookup"><span data-stu-id="a2f35-121">Forcibly Listing Hidden Items (-Force)</span></span>

<span data-ttu-id="a2f35-122">Items die normaal gesproken niet zichtbaar in Windows Verkenner of Cmd.exe zijn worden niet weergegeven in de uitvoer van een **Get-ChildItem** opdracht.</span><span class="sxs-lookup"><span data-stu-id="a2f35-122">Items that are normally invisible in File Explorer or Cmd.exe are not displayed in the output of a **Get-ChildItem** command.</span></span> <span data-ttu-id="a2f35-123">U verborgen items weergeven met behulp de **Force** parameter van **Get-ChildItem**.</span><span class="sxs-lookup"><span data-stu-id="a2f35-123">To display hidden items, use the **Force** parameter of **Get-ChildItem**.</span></span> <span data-ttu-id="a2f35-124">Bijvoorbeeld:</span><span class="sxs-lookup"><span data-stu-id="a2f35-124">For example:</span></span>

```powershell
Get-ChildItem -Path C:\Windows -Force
```

<span data-ttu-id="a2f35-125">Deze parameter is met de naam Force omdat kunt u de normale werking van geforceerd overschrijven de **Get-ChildItem** opdracht.</span><span class="sxs-lookup"><span data-stu-id="a2f35-125">This parameter is named Force because you can forcibly override the normal behavior of the **Get-ChildItem** command.</span></span> <span data-ttu-id="a2f35-126">Force is een veelgebruikte parameter dat ervoor zorgt een actie die een cmdlet niet normaal kunt uitvoeren, dat hoewel een actie op die de beveiliging van het systeem wordt aangetast wordt niet uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="a2f35-126">Force is a widely used parameter that forces an action that a cmdlet would not normally perform, although it will not perform any action that compromises the security of the system.</span></span>

#### <a name="matching-item-names-with-wildcards"></a><span data-ttu-id="a2f35-127">Overeenkomende itemnamen met jokertekens</span><span class="sxs-lookup"><span data-stu-id="a2f35-127">Matching Item Names with Wildcards</span></span>

<span data-ttu-id="a2f35-128">**De Get-ChildItem** opdracht accepteert jokertekens in het pad van de items om weer te geven.</span><span class="sxs-lookup"><span data-stu-id="a2f35-128">**The Get-ChildItem** command accepts wildcards in the path of the items to list.</span></span>

<span data-ttu-id="a2f35-129">Omdat met jokertekens worden verwerkt door de Windows PowerShell-engine, alle cmdlets die jokertekens accepteert de dezelfde notatie hebben en hetzelfde gedrag overeenkomende hebt.</span><span class="sxs-lookup"><span data-stu-id="a2f35-129">Because wildcard matching is handled by the Windows PowerShell engine, all cmdlets that accepts wildcards use the same notation and have the same matching behavior.</span></span> <span data-ttu-id="a2f35-130">De Windows PowerShell-notatie hebben jokertekens bevat:</span><span class="sxs-lookup"><span data-stu-id="a2f35-130">The Windows PowerShell wildcard notation includes:</span></span>

- <span data-ttu-id="a2f35-131">Sterretje (\*) komt overeen met nul of meer exemplaren van een willekeurig teken.</span><span class="sxs-lookup"><span data-stu-id="a2f35-131">Asterisk (\*)matches zero or more occurrences of any character.</span></span>

- <span data-ttu-id="a2f35-132">Vraagteken (?) komt overeen met precies één teken.</span><span class="sxs-lookup"><span data-stu-id="a2f35-132">Question mark (?) matches exactly one character.</span></span>

- <span data-ttu-id="a2f35-133">Vierkante linkerhaak (\[) en vierkante rechterhaak (]) teken rond een reeks tekens worden vergeleken.</span><span class="sxs-lookup"><span data-stu-id="a2f35-133">Left bracket (\[) character and right bracket (]) character surround a set of characters to be matched.</span></span>

<span data-ttu-id="a2f35-134">Hier volgen enkele voorbeelden van de werking van de specificatie van het jokerteken.</span><span class="sxs-lookup"><span data-stu-id="a2f35-134">Here are some examples of how wildcard specification works.</span></span>

<span data-ttu-id="a2f35-135">Als u alle bestanden in de Windows-map met het achtervoegsel **.log** en exact vijf tekens in de basisnaam, voer de volgende opdracht:</span><span class="sxs-lookup"><span data-stu-id="a2f35-135">To find all files in the Windows directory with the suffix **.log** and exactly five characters in the base name, enter the following command:</span></span>

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

<span data-ttu-id="a2f35-136">Als u alle bestanden die met de letter beginnen **x** Typ in de Windows-map:</span><span class="sxs-lookup"><span data-stu-id="a2f35-136">To find all files that begin with the letter **x** in the Windows directory, type:</span></span>

```powershell
Get-ChildItem -Path C:\Windows\x*
```

<span data-ttu-id="a2f35-137">Als u alle bestanden waarvan de naam met begint **x** of **z**, type:</span><span class="sxs-lookup"><span data-stu-id="a2f35-137">To find all files whose names begin with **x** or **z**, type:</span></span>

```powershell
Get-ChildItem -Path C:\Windows\[xz]*
```

#### <a name="excluding-items--exclude"></a><span data-ttu-id="a2f35-138">Items uitsluiten (-uitsluiten)</span><span class="sxs-lookup"><span data-stu-id="a2f35-138">Excluding Items (-Exclude)</span></span>

<span data-ttu-id="a2f35-139">U kunt specifieke items uitsluiten door de **uitsluiten** parameter van Get-ChildItem.</span><span class="sxs-lookup"><span data-stu-id="a2f35-139">You can exclude specific items by using the **Exclude** parameter of Get-ChildItem.</span></span> <span data-ttu-id="a2f35-140">Hiermee kunt u complexe filteren in één instructie uitvoeren.</span><span class="sxs-lookup"><span data-stu-id="a2f35-140">This lets you perform complex filtering in a single statement.</span></span>

<span data-ttu-id="a2f35-141">Stel dat u wilt zoeken naar het DLL-bestand van Windows Time-Service in de map System32 en alle makkelijk te onthouden over de naam van het DLL-bestand is dat het begint met de letter "W" en '32' bevat.</span><span class="sxs-lookup"><span data-stu-id="a2f35-141">For example, suppose you are trying to find the Windows Time Service DLL in the System32 folder, and all you can remember about the DLL name is that it begins with "W" and has "32" in it.</span></span>

<span data-ttu-id="a2f35-142">Een expressie, zoals **w\&#42; 32\&#42;. DLL-bestand** vindt u alle dll-bestanden die voldoen aan de voorwaarden, maar er kan ook de Windows 95 en 16-bits Windows compatibiliteit dll-bestanden met '95' of '16' geretourneerd in hun naam.</span><span class="sxs-lookup"><span data-stu-id="a2f35-142">An expression like **w\&#42;32\&#42;.dll** will find all DLLs that satisfy the conditions, but it may also return the Windows 95 and 16-bit Windows compatibility DLLs that include "95" or "16" in their names.</span></span> <span data-ttu-id="a2f35-143">U kunt bestanden met een van deze getallen in hun namen met behulp van weglaten de **uitsluiten** parameter met het patroon  **\&#42;\[ 9516]\&#42;**:</span><span class="sxs-lookup"><span data-stu-id="a2f35-143">You can omit files that have any of these numbers in their names by using the **Exclude** parameter with the pattern **\&#42;\[9516]\&#42;**:</span></span>

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

#### <a name="mixing-get-childitem-parameters"></a><span data-ttu-id="a2f35-144">De combinatie van Parameters voor Get-ChildItem</span><span class="sxs-lookup"><span data-stu-id="a2f35-144">Mixing Get-ChildItem Parameters</span></span>

<span data-ttu-id="a2f35-145">U kunt verschillende van de parameters van de **Get-ChildItem** cmdlet in dezelfde opdracht.</span><span class="sxs-lookup"><span data-stu-id="a2f35-145">You can use several of the parameters of the **Get-ChildItem** cmdlet in the same command.</span></span> <span data-ttu-id="a2f35-146">Voordat u parameters mengen, moet u dat u bekend met jokertekens bent.</span><span class="sxs-lookup"><span data-stu-id="a2f35-146">Before you mix parameters, be sure that you understand wildcard matching.</span></span> <span data-ttu-id="a2f35-147">De volgende opdracht wordt bijvoorbeeld geen resultaten oplevert:</span><span class="sxs-lookup"><span data-stu-id="a2f35-147">For example, the following command returns no results:</span></span>

```powershell
Get-ChildItem -Path C:\Windows\*.dll -Recurse -Exclude [a-y]*.dll
```

<span data-ttu-id="a2f35-148">Er zijn geen resultaten, zelfs als er zijn twee dll's die met de letter "z" in de Windows-map beginnen.</span><span class="sxs-lookup"><span data-stu-id="a2f35-148">There are no results, even though there are two DLLs that begin with the letter "z" in the Windows folder.</span></span>

<span data-ttu-id="a2f35-149">Er zijn geen resultaten geretourneerd omdat we het jokerteken als deel van het pad opgegeven.</span><span class="sxs-lookup"><span data-stu-id="a2f35-149">No results were returned because we specified the wildcard as part of the path.</span></span> <span data-ttu-id="a2f35-150">Hoewel de opdracht recursieve, is de **Get-ChildItem** cmdlet de items beperkt tot apparaten die in de Windows-map met namen die eindigen op '.dll'.</span><span class="sxs-lookup"><span data-stu-id="a2f35-150">Even though the command was recursive, the **Get-ChildItem** cmdlet restricted the items to those that are in the Windows folder with names ending with ".dll".</span></span>

<span data-ttu-id="a2f35-151">Een recursieve zoekopdracht voor bestanden waarvan de namen overeenkomen met een speciale patroon gebruikt u de **-omvatten** parameter.</span><span class="sxs-lookup"><span data-stu-id="a2f35-151">To specify a recursive search for files whose names match a special pattern, use the **-Include** parameter.</span></span>

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