---
ms.date: 06/05/2017
keywords: Power shell, cmdlet
title: Met bestanden, mappen en registersleutels werken
ms.openlocfilehash: 0c8716c384827d0816e2847ff81232c14638681b
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 12/05/2019
ms.locfileid: "67030758"
---
# <a name="working-with-files-folders-and-registry-keys"></a><span data-ttu-id="81684-103">Werken met bestanden, mappen en register sleutels</span><span class="sxs-lookup"><span data-stu-id="81684-103">Working With Files, Folders and Registry Keys</span></span>

<span data-ttu-id="81684-104">Windows Power shell gebruikt het **item** van de zelfstandig naam om te verwijzen naar items die op een Windows Power Shell-station zijn gevonden.</span><span class="sxs-lookup"><span data-stu-id="81684-104">Windows PowerShell uses the noun **Item** to refer to items found on a Windows PowerShell drive.</span></span> <span data-ttu-id="81684-105">Bij de verwerking van de Windows Power shell-bestandssysteem provider kan een **item** een bestand, een map of het Windows Power Shell-station zijn.</span><span class="sxs-lookup"><span data-stu-id="81684-105">When dealing with the Windows PowerShell FileSystem provider, an **Item** might be a file, a folder, or the Windows PowerShell drive.</span></span> <span data-ttu-id="81684-106">Het weer geven en werken met deze items is een kritieke basis taak in de meeste beheer instellingen, dus we willen deze taken in detail bespreken.</span><span class="sxs-lookup"><span data-stu-id="81684-106">Listing and working with these items is a critical basic task in most administrative settings, so we want to discuss these tasks in detail.</span></span>

## <a name="enumerating-files-folders-and-registry-keys-get-childitem"></a><span data-ttu-id="81684-107">Bestanden, mappen en register sleutels opsommen (Get-Child item)</span><span class="sxs-lookup"><span data-stu-id="81684-107">Enumerating Files, Folders, and Registry Keys (Get-ChildItem)</span></span>

<span data-ttu-id="81684-108">Omdat het ophalen van een verzameling items van een bepaalde locatie een veelvoorkomende taak is, is de cmdlet **Get-Child item** specifiek ontworpen om alle items te retour neren die zijn gevonden in een container, zoals een map.</span><span class="sxs-lookup"><span data-stu-id="81684-108">Since getting a collection of items from a particular location is such a common task, the **Get-ChildItem** cmdlet is designed specifically to return all items found within a container such as a folder.</span></span>

<span data-ttu-id="81684-109">Als u alle bestanden en mappen wilt retour neren die zich rechtstreeks in de map C bevinden:\\Windows, typt u:</span><span class="sxs-lookup"><span data-stu-id="81684-109">If you want to return all files and folders that are contained directly within the folder C:\\Windows, type:</span></span>

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

<span data-ttu-id="81684-110">De vermelding lijkt op wat u ziet wanneer u de opdracht **dir** in **cmd. exe**of de **ls** -opdracht in een UNIX-opdracht shell opgeeft.</span><span class="sxs-lookup"><span data-stu-id="81684-110">The listing looks similar to what you would see when you enter the **dir** command in **Cmd.exe**, or the **ls** command in a UNIX command shell.</span></span>

<span data-ttu-id="81684-111">U kunt zeer complexe vermeldingen uitvoeren met behulp van para meters van de cmdlet **Get-Child item** .</span><span class="sxs-lookup"><span data-stu-id="81684-111">You can perform very complex listings by using parameters of the **Get-ChildItem** cmdlet.</span></span> <span data-ttu-id="81684-112">We gaan nu een paar scenario's bekijken.</span><span class="sxs-lookup"><span data-stu-id="81684-112">We will look at a few scenarios next.</span></span> <span data-ttu-id="81684-113">U kunt de syntaxis van de cmdlet **Get-Child item** zien door het volgende te typen:</span><span class="sxs-lookup"><span data-stu-id="81684-113">You can see the syntax the **Get-ChildItem** cmdlet by typing:</span></span>

```powershell
Get-Command -Name Get-ChildItem -Syntax
```

<span data-ttu-id="81684-114">Deze para meters kunnen worden gecombineerd en overeenkomen om een zeer aangepaste uitvoer te krijgen.</span><span class="sxs-lookup"><span data-stu-id="81684-114">These parameters can be mixed and matched to get highly customized output.</span></span>

### <a name="listing-all-contained-items--recurse"></a><span data-ttu-id="81684-115">Alle opgenomen items weer geven (-recursief)</span><span class="sxs-lookup"><span data-stu-id="81684-115">Listing all Contained Items (-Recurse)</span></span>

<span data-ttu-id="81684-116">Als u beide items in een Windows-map en alle items in de submappen wilt weer geven, gebruikt u de para meter **recursieve** van **Get-Child item**.</span><span class="sxs-lookup"><span data-stu-id="81684-116">To see both the items inside a Windows folder and any items that are contained within the subfolders, use the **Recurse** parameter of **Get-ChildItem**.</span></span> <span data-ttu-id="81684-117">De vermelding bevat alles in de Windows-map en de items in de submappen.</span><span class="sxs-lookup"><span data-stu-id="81684-117">The listing displays everything within the Windows folder and the items in its subfolders.</span></span> <span data-ttu-id="81684-118">Bijvoorbeeld:</span><span class="sxs-lookup"><span data-stu-id="81684-118">For example:</span></span>

```
PS> Get-ChildItem -Path C:\WINDOWS -Recurse

    Directory: Microsoft.Windows PowerShell.Core\FileSystem::C:\WINDOWS
    Directory: Microsoft.Windows PowerShell.Core\FileSystem::C:\WINDOWS\AppPatch
Mode                LastWriteTime     Length Name
----                -------------     ------ ----
-a---        2004-08-04   8:00 AM    1852416 AcGenral.dll
...
```

### <a name="filtering-items-by-name--name"></a><span data-ttu-id="81684-119">Items filteren op naam (-naam)</span><span class="sxs-lookup"><span data-stu-id="81684-119">Filtering Items by Name (-Name)</span></span>

<span data-ttu-id="81684-120">Als u alleen de namen van items wilt weer geven, gebruikt u de para meter **name** van **Get-Child item**:</span><span class="sxs-lookup"><span data-stu-id="81684-120">To display only the names of items, use the **Name** parameter of **Get-Childitem**:</span></span>

```
PS> Get-ChildItem -Path C:\WINDOWS -Name
addins
AppPatch
assembly
...
```

### <a name="forcibly-listing-hidden-items--force"></a><span data-ttu-id="81684-121">Geforceerde vermelding van verborgen items (-Force)</span><span class="sxs-lookup"><span data-stu-id="81684-121">Forcibly Listing Hidden Items (-Force)</span></span>

<span data-ttu-id="81684-122">Items die normaal gesp roken onzichtbaar zijn in Verkenner of Cmd. exe worden niet weer gegeven in de uitvoer van de opdracht **Get-Child item** .</span><span class="sxs-lookup"><span data-stu-id="81684-122">Items that are normally invisible in File Explorer or Cmd.exe are not displayed in the output of a **Get-ChildItem** command.</span></span> <span data-ttu-id="81684-123">Als u verborgen items wilt weer geven, gebruikt u de para meter **Forces** van **Get-Child item**.</span><span class="sxs-lookup"><span data-stu-id="81684-123">To display hidden items, use the **Force** parameter of **Get-ChildItem**.</span></span> <span data-ttu-id="81684-124">Bijvoorbeeld:</span><span class="sxs-lookup"><span data-stu-id="81684-124">For example:</span></span>

```powershell
Get-ChildItem -Path C:\Windows -Force
```

<span data-ttu-id="81684-125">Deze para meter heeft de naam Force omdat u het normale gedrag van de opdracht **Get-Child item** kunt negeren.</span><span class="sxs-lookup"><span data-stu-id="81684-125">This parameter is named Force because you can forcibly override the normal behavior of the **Get-ChildItem** command.</span></span> <span data-ttu-id="81684-126">Force is een veelgebruikte para meter die een actie afdwingt die een cmdlet normaal gesp roken niet zou uitvoeren, hoewel er geen actie wordt uitgevoerd die de beveiliging van het systeem in de hand brengt.</span><span class="sxs-lookup"><span data-stu-id="81684-126">Force is a widely used parameter that forces an action that a cmdlet would not normally perform, although it will not perform any action that compromises the security of the system.</span></span>

### <a name="matching-item-names-with-wildcards"></a><span data-ttu-id="81684-127">Overeenkomende item namen met Joker tekens</span><span class="sxs-lookup"><span data-stu-id="81684-127">Matching Item Names with Wildcards</span></span>

<span data-ttu-id="81684-128">**De opdracht Get-Child item** accepteert joker tekens in het pad van de items die moeten worden weer geven.</span><span class="sxs-lookup"><span data-stu-id="81684-128">**The Get-ChildItem** command accepts wildcards in the path of the items to list.</span></span>

<span data-ttu-id="81684-129">Omdat het vergelijken van het Joker teken wordt verwerkt door de Windows Power shell-engine, gebruiken alle cmdlets die joker tekens accepteren, dezelfde notatie en hebben hetzelfde overeenkomstige gedrag.</span><span class="sxs-lookup"><span data-stu-id="81684-129">Because wildcard matching is handled by the Windows PowerShell engine, all cmdlets that accepts wildcards use the same notation and have the same matching behavior.</span></span> <span data-ttu-id="81684-130">De Windows Power shell-Joker teken notatie bevat:</span><span class="sxs-lookup"><span data-stu-id="81684-130">The Windows PowerShell wildcard notation includes:</span></span>

- <span data-ttu-id="81684-131">Asterisk (\*) komt overeen met nul of meer exemplaren van elk wille keurig teken.</span><span class="sxs-lookup"><span data-stu-id="81684-131">Asterisk (\*)matches zero or more occurrences of any character.</span></span>

- <span data-ttu-id="81684-132">Vraag teken (?) komt overeen met één teken.</span><span class="sxs-lookup"><span data-stu-id="81684-132">Question mark (?) matches exactly one character.</span></span>

- <span data-ttu-id="81684-133">Teken voor haakje links (\[) en haakje (]) rond een reeks tekens die moeten worden vergeleken.</span><span class="sxs-lookup"><span data-stu-id="81684-133">Left bracket (\[) character and right bracket (]) character surround a set of characters to be matched.</span></span>

<span data-ttu-id="81684-134">Hier volgen enkele voor beelden van de werking van joker tekens.</span><span class="sxs-lookup"><span data-stu-id="81684-134">Here are some examples of how wildcard specification works.</span></span>

<span data-ttu-id="81684-135">Als u alle bestanden in de Windows-map wilt zoeken met het achtervoegsel **. log** en precies vijf tekens in de basis naam, voert u de volgende opdracht in:</span><span class="sxs-lookup"><span data-stu-id="81684-135">To find all files in the Windows directory with the suffix **.log** and exactly five characters in the base name, enter the following command:</span></span>

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

<span data-ttu-id="81684-136">Als u alle bestanden wilt vinden die beginnen met de letter **x** in de map Windows, typt u:</span><span class="sxs-lookup"><span data-stu-id="81684-136">To find all files that begin with the letter **x** in the Windows directory, type:</span></span>

```powershell
Get-ChildItem -Path C:\Windows\x*
```

<span data-ttu-id="81684-137">Als u wilt zoeken naar alle bestanden waarvan de naam begint met **x** of **z**, typt u:</span><span class="sxs-lookup"><span data-stu-id="81684-137">To find all files whose names begin with **x** or **z**, type:</span></span>

```powershell
Get-ChildItem -Path C:\Windows\[xz]*
```

### <a name="excluding-items--exclude"></a><span data-ttu-id="81684-138">Uitsluiten van items (-uitsluiten)</span><span class="sxs-lookup"><span data-stu-id="81684-138">Excluding Items (-Exclude)</span></span>

<span data-ttu-id="81684-139">U kunt specifieke items uitsluiten met behulp van de **exclude** -para meter van Get-Child item.</span><span class="sxs-lookup"><span data-stu-id="81684-139">You can exclude specific items by using the **Exclude** parameter of Get-ChildItem.</span></span> <span data-ttu-id="81684-140">Zo kunt u complexe filters uitvoeren in één instructie.</span><span class="sxs-lookup"><span data-stu-id="81684-140">This lets you perform complex filtering in a single statement.</span></span>

<span data-ttu-id="81684-141">Stel dat u de Windows Time-service-DLL wilt vinden in de map System32 en dat u meer weet over de DLL-naam dat deze begint met ' W ' en dat deze ' 32 ' bevat.</span><span class="sxs-lookup"><span data-stu-id="81684-141">For example, suppose you are trying to find the Windows Time Service DLL in the System32 folder, and all you can remember about the DLL name is that it begins with "W" and has "32" in it.</span></span>

<span data-ttu-id="81684-142">Een expressie zoals **w\&#42; 32\&#42;. het dll** -bestand bevat alle dll-bestanden die voldoen aan de voor waarden, maar deze kunnen ook de Windows-compatibiliteits-dll's (95 en 16-bits) retour neren die "95" of "16" in hun namen bevatten.</span><span class="sxs-lookup"><span data-stu-id="81684-142">An expression like **w\&#42;32\&#42;.dll** will find all DLLs that satisfy the conditions, but it may also return the Windows 95 and 16-bit Windows compatibility DLLs that include "95" or "16" in their names.</span></span> <span data-ttu-id="81684-143">U kunt bestanden met een van deze getallen in hun namen weglaten met de **exclude** -para meter met het patroon **\&#42;\[9516]\&#42;** :</span><span class="sxs-lookup"><span data-stu-id="81684-143">You can omit files that have any of these numbers in their names by using the **Exclude** parameter with the pattern **\&#42;\[9516]\&#42;**:</span></span>

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

### <a name="mixing-get-childitem-parameters"></a><span data-ttu-id="81684-144">Get-Child item-para meters combi neren</span><span class="sxs-lookup"><span data-stu-id="81684-144">Mixing Get-ChildItem Parameters</span></span>

<span data-ttu-id="81684-145">U kunt verschillende para meters van de cmdlet **Get-Child item** in dezelfde opdracht gebruiken.</span><span class="sxs-lookup"><span data-stu-id="81684-145">You can use several of the parameters of the **Get-ChildItem** cmdlet in the same command.</span></span> <span data-ttu-id="81684-146">Voordat u para meters gaat mengen, moet u ervoor zorgen dat u begrijpt dat er joker tekens overeenkomen.</span><span class="sxs-lookup"><span data-stu-id="81684-146">Before you mix parameters, be sure that you understand wildcard matching.</span></span> <span data-ttu-id="81684-147">De volgende opdracht retourneert bijvoorbeeld geen resultaten:</span><span class="sxs-lookup"><span data-stu-id="81684-147">For example, the following command returns no results:</span></span>

```powershell
Get-ChildItem -Path C:\Windows\*.dll -Recurse -Exclude [a-y]*.dll
```

<span data-ttu-id="81684-148">Er zijn geen resultaten, hoewel er twee Dll's zijn die beginnen met de letter ' z ' in de map Windows.</span><span class="sxs-lookup"><span data-stu-id="81684-148">There are no results, even though there are two DLLs that begin with the letter "z" in the Windows folder.</span></span>

<span data-ttu-id="81684-149">Er zijn geen resultaten geretourneerd omdat het Joker teken is opgegeven als onderdeel van het pad.</span><span class="sxs-lookup"><span data-stu-id="81684-149">No results were returned because we specified the wildcard as part of the path.</span></span> <span data-ttu-id="81684-150">Hoewel de opdracht recursief is, heeft de cmdlet **Get-Child item** de items beperkt tot die in de Windows-map met namen die eindigen op '. dll '.</span><span class="sxs-lookup"><span data-stu-id="81684-150">Even though the command was recursive, the **Get-ChildItem** cmdlet restricted the items to those that are in the Windows folder with names ending with ".dll".</span></span>

<span data-ttu-id="81684-151">Als u een recursieve zoek opdracht wilt opgeven voor bestanden waarvan de namen overeenkomen met een speciaal patroon, gebruikt u de para meter **-include** .</span><span class="sxs-lookup"><span data-stu-id="81684-151">To specify a recursive search for files whose names match a special pattern, use the **-Include** parameter.</span></span>

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
