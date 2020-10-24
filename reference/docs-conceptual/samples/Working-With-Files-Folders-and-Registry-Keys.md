---
ms.date: 07/28/2020
keywords: powershell,cmdlet
title: Met bestanden, mappen en registersleutels werken
description: In dit artikel wordt beschreven hoe u met Power shell taken voor het bewerken van register sleutels behandelt.
ms.openlocfilehash: 6f653c1fb409a238aa05658e89261a12e96f6fe1
ms.sourcegitcommit: 9080316e3ca4f11d83067b41351531672b667b7a
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/24/2020
ms.locfileid: "92499974"
---
# <a name="working-with-files-folders-and-registry-keys"></a><span data-ttu-id="eacc5-104">Werken met bestanden, mappen en register sleutels</span><span class="sxs-lookup"><span data-stu-id="eacc5-104">Working With Files, Folders and Registry Keys</span></span>

<span data-ttu-id="eacc5-105">Windows Power shell gebruikt het **item** van de zelfstandig naam om te verwijzen naar items die op een Windows Power Shell-station zijn gevonden.</span><span class="sxs-lookup"><span data-stu-id="eacc5-105">Windows PowerShell uses the noun **Item** to refer to items found on a Windows PowerShell drive.</span></span>
<span data-ttu-id="eacc5-106">Bij de verwerking van de Windows Power shell-bestandssysteem provider kan een **item** een bestand, een map of het Windows Power Shell-station zijn.</span><span class="sxs-lookup"><span data-stu-id="eacc5-106">When dealing with the Windows PowerShell FileSystem provider, an **Item** might be a file, a folder, or the Windows PowerShell drive.</span></span> <span data-ttu-id="eacc5-107">Het weer geven en werken met deze items is een kritieke basis taak in de meeste beheer instellingen, dus we willen deze taken in detail bespreken.</span><span class="sxs-lookup"><span data-stu-id="eacc5-107">Listing and working with these items is a critical basic task in most administrative settings, so we want to discuss these tasks in detail.</span></span>

## <a name="enumerating-files-folders-and-registry-keys-get-childitem"></a><span data-ttu-id="eacc5-108">Bestanden, mappen en register sleutels opsommen (Get-Child item)</span><span class="sxs-lookup"><span data-stu-id="eacc5-108">Enumerating Files, Folders, and Registry Keys (Get-ChildItem)</span></span>

<span data-ttu-id="eacc5-109">Omdat het ophalen van een verzameling items van een bepaalde locatie een veelvoorkomende taak is, `Get-ChildItem` is de cmdlet speciaal ontworpen om alle items te retour neren die zijn gevonden in een container, zoals een map.</span><span class="sxs-lookup"><span data-stu-id="eacc5-109">Since getting a collection of items from a particular location is such a common task, the `Get-ChildItem` cmdlet is designed specifically to return all items found within a container such as a folder.</span></span>

<span data-ttu-id="eacc5-110">Als u alle bestanden en mappen wilt retour neren die zich rechtstreeks in de map C: Windows bevinden \\ , typt u:</span><span class="sxs-lookup"><span data-stu-id="eacc5-110">If you want to return all files and folders that are contained directly within the folder C:\\Windows, type:</span></span>

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

<span data-ttu-id="eacc5-111">De vermelding lijkt op wat u ziet wanneer u de `dir` opdracht invoert in **Cmd.exe**of de `ls` opdracht in een UNIX-opdracht shell.</span><span class="sxs-lookup"><span data-stu-id="eacc5-111">The listing looks similar to what you would see when you enter the `dir` command in **Cmd.exe**, or the `ls` command in a UNIX command shell.</span></span>

<span data-ttu-id="eacc5-112">U kunt zeer complexe vermeldingen uitvoeren met behulp van para meters van de `Get-ChildItem` cmdlet.</span><span class="sxs-lookup"><span data-stu-id="eacc5-112">You can perform very complex listings by using parameters of the `Get-ChildItem` cmdlet.</span></span> <span data-ttu-id="eacc5-113">We gaan nu een paar scenario's bekijken.</span><span class="sxs-lookup"><span data-stu-id="eacc5-113">We will look at a few scenarios next.</span></span> <span data-ttu-id="eacc5-114">U kunt de syntaxis van de `Get-ChildItem` cmdlet zien door het volgende te typen:</span><span class="sxs-lookup"><span data-stu-id="eacc5-114">You can see the syntax the `Get-ChildItem` cmdlet by typing:</span></span>

```powershell
Get-Command -Name Get-ChildItem -Syntax
```

<span data-ttu-id="eacc5-115">Deze para meters kunnen worden gecombineerd en overeenkomen om een zeer aangepaste uitvoer te krijgen.</span><span class="sxs-lookup"><span data-stu-id="eacc5-115">These parameters can be mixed and matched to get highly customized output.</span></span>

### <a name="listing-all-contained-items--recurse"></a><span data-ttu-id="eacc5-116">Alle opgenomen items weer geven (-recursief)</span><span class="sxs-lookup"><span data-stu-id="eacc5-116">Listing all Contained Items (-Recurse)</span></span>

<span data-ttu-id="eacc5-117">Als u beide items in een Windows-map en alle items in de submappen wilt zien, gebruikt u de para meter **recursieve** van `Get-ChildItem` .</span><span class="sxs-lookup"><span data-stu-id="eacc5-117">To see both the items inside a Windows folder and any items that are contained within the subfolders, use the **Recurse** parameter of `Get-ChildItem`.</span></span> <span data-ttu-id="eacc5-118">De vermelding bevat alles in de Windows-map en de items in de submappen.</span><span class="sxs-lookup"><span data-stu-id="eacc5-118">The listing displays everything within the Windows folder and the items in its subfolders.</span></span> <span data-ttu-id="eacc5-119">Bijvoorbeeld:</span><span class="sxs-lookup"><span data-stu-id="eacc5-119">For example:</span></span>

```
PS> Get-ChildItem -Path C:\WINDOWS -Recurse

    Directory: Microsoft.Windows PowerShell.Core\FileSystem::C:\WINDOWS
    Directory: Microsoft.Windows PowerShell.Core\FileSystem::C:\WINDOWS\AppPatch
Mode                LastWriteTime     Length Name
----                -------------     ------ ----
-a---        2004-08-04   8:00 AM    1852416 AcGenral.dll
...
```

### <a name="filtering-items-by-name--name"></a><span data-ttu-id="eacc5-120">Items filteren op naam (-naam)</span><span class="sxs-lookup"><span data-stu-id="eacc5-120">Filtering Items by Name (-Name)</span></span>

<span data-ttu-id="eacc5-121">Als u alleen de namen van items wilt weer geven, gebruikt u de para meter **name** van `Get-Childitem` :</span><span class="sxs-lookup"><span data-stu-id="eacc5-121">To display only the names of items, use the **Name** parameter of `Get-Childitem`:</span></span>

```
PS> Get-ChildItem -Path C:\WINDOWS -Name
addins
AppPatch
assembly
...
```

### <a name="forcibly-listing-hidden-items--force"></a><span data-ttu-id="eacc5-122">Geforceerde vermelding van verborgen items (-Force)</span><span class="sxs-lookup"><span data-stu-id="eacc5-122">Forcibly Listing Hidden Items (-Force)</span></span>

<span data-ttu-id="eacc5-123">Items die normaal gesp roken onzichtbaar zijn in bestanden Verkenner of Cmd.exe worden niet weer gegeven in de uitvoer van een `Get-ChildItem` opdracht.</span><span class="sxs-lookup"><span data-stu-id="eacc5-123">Items that are normally invisible in File Explorer or Cmd.exe are not displayed in the output of a `Get-ChildItem` command.</span></span> <span data-ttu-id="eacc5-124">Als u verborgen items wilt weer geven, gebruikt u de para meter **Force** van `Get-ChildItem` .</span><span class="sxs-lookup"><span data-stu-id="eacc5-124">To display hidden items, use the **Force** parameter of `Get-ChildItem`.</span></span>
<span data-ttu-id="eacc5-125">Bijvoorbeeld:</span><span class="sxs-lookup"><span data-stu-id="eacc5-125">For example:</span></span>

```powershell
Get-ChildItem -Path C:\Windows -Force
```

<span data-ttu-id="eacc5-126">Deze para meter heeft de naam Force omdat u het normale gedrag van de opdracht kunt negeren `Get-ChildItem` .</span><span class="sxs-lookup"><span data-stu-id="eacc5-126">This parameter is named Force because you can forcibly override the normal behavior of the `Get-ChildItem` command.</span></span> <span data-ttu-id="eacc5-127">Force is een veelgebruikte para meter die een actie afdwingt die een cmdlet normaal gesp roken niet zou uitvoeren, hoewel er geen actie wordt uitgevoerd die de beveiliging van het systeem in de hand brengt.</span><span class="sxs-lookup"><span data-stu-id="eacc5-127">Force is a widely used parameter that forces an action that a cmdlet would not normally perform, although it will not perform any action that compromises the security of the system.</span></span>

### <a name="matching-item-names-with-wildcards"></a><span data-ttu-id="eacc5-128">Overeenkomende item namen met Joker tekens</span><span class="sxs-lookup"><span data-stu-id="eacc5-128">Matching Item Names with Wildcards</span></span>

<span data-ttu-id="eacc5-129">De `Get-ChildItem` opdracht accepteert joker tekens in het pad van de items die moeten worden weer geven.</span><span class="sxs-lookup"><span data-stu-id="eacc5-129">The `Get-ChildItem` command accepts wildcards in the path of the items to list.</span></span>

<span data-ttu-id="eacc5-130">Omdat het vergelijken van het Joker teken wordt verwerkt door de Windows Power shell-engine, gebruiken alle cmdlets die joker tekens accepteren, dezelfde notatie en hebben hetzelfde overeenkomstige gedrag.</span><span class="sxs-lookup"><span data-stu-id="eacc5-130">Because wildcard matching is handled by the Windows PowerShell engine, all cmdlets that accepts wildcards use the same notation and have the same matching behavior.</span></span> <span data-ttu-id="eacc5-131">De Windows Power shell-Joker teken notatie bevat:</span><span class="sxs-lookup"><span data-stu-id="eacc5-131">The Windows PowerShell wildcard notation includes:</span></span>

- <span data-ttu-id="eacc5-132">Sterretje ( `*` ) komt overeen met nul of meer exemplaren van elk wille keurig teken.</span><span class="sxs-lookup"><span data-stu-id="eacc5-132">Asterisk (`*`) matches zero or more occurrences of any character.</span></span>

- <span data-ttu-id="eacc5-133">Vraag teken ( `?` ) komt overeen met één teken.</span><span class="sxs-lookup"><span data-stu-id="eacc5-133">Question mark (`?`) matches exactly one character.</span></span>

- <span data-ttu-id="eacc5-134">Teken voor vier Kante haakjes ( `[` ) en rechter haakje ( `]` ) rond een reeks tekens die moeten worden vergeleken.</span><span class="sxs-lookup"><span data-stu-id="eacc5-134">Left bracket (`[`) character and right bracket (`]`) character surround a set of characters to be matched.</span></span>

<span data-ttu-id="eacc5-135">Hier volgen enkele voor beelden van de werking van joker tekens.</span><span class="sxs-lookup"><span data-stu-id="eacc5-135">Here are some examples of how wildcard specification works.</span></span>

<span data-ttu-id="eacc5-136">Voer de volgende opdracht in om alle bestanden in de Windows-map met het achtervoegsel `.log` en exact vijf tekens in de basis naam op te zoeken:</span><span class="sxs-lookup"><span data-stu-id="eacc5-136">To find all files in the Windows directory with the suffix `.log` and exactly five characters in the base name, enter the following command:</span></span>

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

<span data-ttu-id="eacc5-137">Als u alle bestanden wilt vinden die beginnen met de letter `x` in de Windows-map, typt u:</span><span class="sxs-lookup"><span data-stu-id="eacc5-137">To find all files that begin with the letter `x` in the Windows directory, type:</span></span>

```powershell
Get-ChildItem -Path C:\Windows\x*
```

<span data-ttu-id="eacc5-138">Als u wilt zoeken naar alle bestanden waarvan de naam begint met ' x ' of ' z ', typt u:</span><span class="sxs-lookup"><span data-stu-id="eacc5-138">To find all files whose names begin with "x" or "z", type:</span></span>

```powershell
Get-ChildItem -Path C:\Windows\[xz]*
```

<span data-ttu-id="eacc5-139">Zie [about_Wildcards](/powershell/module/microsoft.powershell.core/about/about_wildcards)voor meer informatie over joker tekens.</span><span class="sxs-lookup"><span data-stu-id="eacc5-139">For more information about wildcards, see [about_Wildcards](/powershell/module/microsoft.powershell.core/about/about_wildcards).</span></span>

### <a name="excluding-items--exclude"></a><span data-ttu-id="eacc5-140">Uitsluiten van items (-uitsluiten)</span><span class="sxs-lookup"><span data-stu-id="eacc5-140">Excluding Items (-Exclude)</span></span>

<span data-ttu-id="eacc5-141">U kunt specifieke items uitsluiten met behulp van de **exclude** -para meter van `Get-ChildItem` .</span><span class="sxs-lookup"><span data-stu-id="eacc5-141">You can exclude specific items by using the **Exclude** parameter of `Get-ChildItem`.</span></span> <span data-ttu-id="eacc5-142">Zo kunt u complexe filters uitvoeren in één instructie.</span><span class="sxs-lookup"><span data-stu-id="eacc5-142">This lets you perform complex filtering in a single statement.</span></span>

<span data-ttu-id="eacc5-143">Stel dat u de Windows Time-service-DLL wilt vinden in de map **System32** en dat u meer weet over de DLL-naam dat deze begint met ' W ' en dat deze ' 32 ' bevat.</span><span class="sxs-lookup"><span data-stu-id="eacc5-143">For example, suppose you are trying to find the Windows Time Service DLL in the **System32** folder, and all you can remember about the DLL name is that it begins with "W" and has "32" in it.</span></span>

<span data-ttu-id="eacc5-144">Een expressie Like `w*32*.dll` bevat alle dll's die voldoen aan de voor waarden, maar u wilt mogelijk de bestanden verder uitfilteren en Win32-bestanden weglaten.</span><span class="sxs-lookup"><span data-stu-id="eacc5-144">An expression like `w*32*.dll` will find all DLLs that satisfy the conditions, but you may want to further filter out the files and omit any win32 files.</span></span> <span data-ttu-id="eacc5-145">U kunt deze bestanden weglaten met de para meter **exclude** met het patroon `win*` :</span><span class="sxs-lookup"><span data-stu-id="eacc5-145">You can omit these files by using the **Exclude** parameter with the pattern `win*`:</span></span>

```
PS> Get-ChildItem -Path C:\WINDOWS\System32\w*32*.dll -Exclude win*

    Directory: C:\WINDOWS\System32

Mode                 LastWriteTime         Length Name
----                 -------------         ------ ----
-a---           3/18/2019  9:43 PM         495616 w32time.dll
-a---           3/18/2019  9:44 PM          35328 w32topl.dll
-a---           1/24/2020  5:44 PM         401920 Wldap32.dll
-a---          10/10/2019  5:40 PM         442704 ws2_32.dll
-a---           3/18/2019  9:44 PM          66048 wsnmp32.dll
-a---           3/18/2019  9:44 PM          18944 wsock32.dll
-a---           3/18/2019  9:44 PM          64792 wtsapi32.dll
```

### <a name="mixing-get-childitem-parameters"></a><span data-ttu-id="eacc5-146">Get-ChildItem-para meters combi neren</span><span class="sxs-lookup"><span data-stu-id="eacc5-146">Mixing Get-ChildItem Parameters</span></span>

<span data-ttu-id="eacc5-147">U kunt verschillende para meters van de `Get-ChildItem` cmdlet gebruiken in dezelfde opdracht.</span><span class="sxs-lookup"><span data-stu-id="eacc5-147">You can use several of the parameters of the `Get-ChildItem` cmdlet in the same command.</span></span> <span data-ttu-id="eacc5-148">Voordat u para meters gaat mengen, moet u ervoor zorgen dat u begrijpt dat er joker tekens overeenkomen.</span><span class="sxs-lookup"><span data-stu-id="eacc5-148">Before you mix parameters, be sure that you understand wildcard matching.</span></span> <span data-ttu-id="eacc5-149">De volgende opdracht retourneert bijvoorbeeld geen resultaten:</span><span class="sxs-lookup"><span data-stu-id="eacc5-149">For example, the following command returns no results:</span></span>

```powershell
Get-ChildItem -Path C:\Windows\*.dll -Recurse -Exclude [a-y]*.dll
```

<span data-ttu-id="eacc5-150">Er zijn geen resultaten, hoewel er twee Dll's zijn die beginnen met de letter ' z ' in de map Windows.</span><span class="sxs-lookup"><span data-stu-id="eacc5-150">There are no results, even though there are two DLLs that begin with the letter "z" in the Windows folder.</span></span>

<span data-ttu-id="eacc5-151">Er zijn geen resultaten geretourneerd omdat het Joker teken is opgegeven als onderdeel van het pad.</span><span class="sxs-lookup"><span data-stu-id="eacc5-151">No results were returned because we specified the wildcard as part of the path.</span></span> <span data-ttu-id="eacc5-152">Hoewel de opdracht recursief was, `Get-ChildItem` beperkt de cmdlet de items in de Windows-map met namen die eindigen op `.dll` .</span><span class="sxs-lookup"><span data-stu-id="eacc5-152">Even though the command was recursive, the `Get-ChildItem` cmdlet restricted the items to those that are in the Windows folder with names ending with `.dll`.</span></span>

<span data-ttu-id="eacc5-153">Als u een recursieve zoek opdracht wilt opgeven voor bestanden waarvan de namen overeenkomen met een speciaal patroon, gebruikt u de para meter **include** .</span><span class="sxs-lookup"><span data-stu-id="eacc5-153">To specify a recursive search for files whose names match a special pattern, use the **Include** parameter.</span></span>

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
