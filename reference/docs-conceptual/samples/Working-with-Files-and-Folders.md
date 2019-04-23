---
ms.date: 06/05/2017
keywords: PowerShell-cmdlet
title: Met bestanden en mappen werken
ms.assetid: c0ceb96b-e708-45f3-803b-d1f61a48f4c1
ms.openlocfilehash: 393e886a4945222198d9b81019250c5d5b905ad3
ms.sourcegitcommit: f4bd4e116e22c8b5bfcb61680a7c42e58b4da93e
ms.translationtype: HT
ms.contentlocale: nl-NL
ms.lasthandoff: 04/22/2019
ms.locfileid: "59984388"
---
# <a name="working-with-files-and-folders"></a><span data-ttu-id="5e423-103">Met bestanden en mappen werken</span><span class="sxs-lookup"><span data-stu-id="5e423-103">Working with Files and Folders</span></span>

<span data-ttu-id="5e423-104">Navigeren door Windows PowerShell-stations en de items op deze bewerken is vergelijkbaar met het bewerken van bestanden en mappen op de fysieke schijven Windows.</span><span class="sxs-lookup"><span data-stu-id="5e423-104">Navigating through Windows PowerShell drives and manipulating the items on them is similar to manipulating files and folders on Windows physical disk drives.</span></span> <span data-ttu-id="5e423-105">Deze sectie wordt beschreven hoe u omgaat met specifieke bestanden en mappen manipulatie taken-met behulp van PowerShell.</span><span class="sxs-lookup"><span data-stu-id="5e423-105">This section discusses how to deal with specific file and folder manipulation tasks using PowerShell.</span></span>

## <a name="listing-all-the-files-and-folders-within-a-folder"></a><span data-ttu-id="5e423-106">Lijst van alle bestanden en mappen in een map</span><span class="sxs-lookup"><span data-stu-id="5e423-106">Listing All the Files and Folders Within a Folder</span></span>

<span data-ttu-id="5e423-107">U kunt alle items rechtstreeks in een map ophalen met behulp van **Get-ChildItem**.</span><span class="sxs-lookup"><span data-stu-id="5e423-107">You can get all items directly within a folder by using **Get-ChildItem**.</span></span> <span data-ttu-id="5e423-108">Voeg de optionele **Force** parameter verborgen weergeven of items van system.</span><span class="sxs-lookup"><span data-stu-id="5e423-108">Add the optional **Force** parameter to display hidden or system items.</span></span> <span data-ttu-id="5e423-109">Deze opdracht geeft bijvoorbeeld de directe inhoud van Windows PowerShell-station C (dit is hetzelfde als de fysieke Windows-station C):</span><span class="sxs-lookup"><span data-stu-id="5e423-109">For example, this command displays the direct contents of Windows PowerShell Drive C (which is the same as the Windows physical drive C):</span></span>

```powershell
Get-ChildItem -Path C:\ -Force
```

<span data-ttu-id="5e423-110">De opdracht bevat alleen de rechtstreeks opgenomen items, net als met behulp van Cmd.exe **DIR** opdracht of **ls** in een UNIX-shell.</span><span class="sxs-lookup"><span data-stu-id="5e423-110">The command lists only the directly contained items, much like using Cmd.exe's **DIR** command or **ls** in a UNIX shell.</span></span> <span data-ttu-id="5e423-111">Als u wilt de opgenomen items weergeven, moet u opgeven de **-Recurse** ook de parameter.</span><span class="sxs-lookup"><span data-stu-id="5e423-111">In order to show contained items, you need to specify the **-Recurse** parameter as well.</span></span> <span data-ttu-id="5e423-112">(Dit kan een extreem lange tijd in beslag nemen.) Overzicht van alles op de C-station:</span><span class="sxs-lookup"><span data-stu-id="5e423-112">(This can take an extremely long time to complete.) To list everything on the C drive:</span></span>

```powershell
Get-ChildItem -Path C:\ -Force -Recurse
```

<span data-ttu-id="5e423-113">**Get-ChildItem** items kunt filteren op de **pad**, **Filter**, **opnemen**, en **uitsluiten** parameters, maar deze zijn Normaal gesproken alleen gebaseerd op de naam.</span><span class="sxs-lookup"><span data-stu-id="5e423-113">**Get-ChildItem** can filter items with its **Path**, **Filter**, **Include**, and **Exclude** parameters, but those are typically based only on name.</span></span> <span data-ttu-id="5e423-114">U kunt uitvoeren met het complex filteren op basis van andere eigenschappen van items met behulp van **Where-Object**.</span><span class="sxs-lookup"><span data-stu-id="5e423-114">You can perform complex filtering based on other properties of items by using **Where-Object**.</span></span>

<span data-ttu-id="5e423-115">De volgende opdracht wordt gezocht naar alle uitvoerbare bestanden in de map Program Files die het laatst zijn gewijzigd na 1 oktober 2005 die wel en niet kleiner zijn dan 1 MB of groter is dan 10 MB:</span><span class="sxs-lookup"><span data-stu-id="5e423-115">The following command finds all executables within the Program Files folder that were last modified after October 1, 2005 and which are neither smaller than 1 megabyte nor larger than 10 megabytes:</span></span>

```powershell
Get-ChildItem -Path $env:ProgramFiles -Recurse -Include *.exe | Where-Object -FilterScript {($_.LastWriteTime -gt '2005-10-01') -and ($_.Length -ge 1mb) -and ($_.Length -le 10mb)}
```

## <a name="copying-files-and-folders"></a><span data-ttu-id="5e423-116">Kopiëren van bestanden en mappen</span><span class="sxs-lookup"><span data-stu-id="5e423-116">Copying Files and Folders</span></span>

<span data-ttu-id="5e423-117">Kopiëren is klaar met **Copy-Item**.</span><span class="sxs-lookup"><span data-stu-id="5e423-117">Copying is done with **Copy-Item**.</span></span> <span data-ttu-id="5e423-118">De volgende opdracht uit back-ups van C:\\boot.ini naar C:\\boot.bak:</span><span class="sxs-lookup"><span data-stu-id="5e423-118">The following command backs up C:\\boot.ini to C:\\boot.bak:</span></span>

```powershell
Copy-Item -Path C:\boot.ini -Destination C:\boot.bak
```

<span data-ttu-id="5e423-119">Als het doelbestand al bestaat, mislukt die poging kopiëren.</span><span class="sxs-lookup"><span data-stu-id="5e423-119">If the destination file already exists, the copy attempt fails.</span></span> <span data-ttu-id="5e423-120">Als u wilt overschrijven van een reeds bestaande bestemming, gebruikt u de **Force** parameter:</span><span class="sxs-lookup"><span data-stu-id="5e423-120">To overwrite a pre-existing destination, use the **Force** parameter:</span></span>

```powershell
Copy-Item -Path C:\boot.ini -Destination C:\boot.bak -Force
```

<span data-ttu-id="5e423-121">Met deze opdracht werkt zelfs als de bestemming alleen-lezen is.</span><span class="sxs-lookup"><span data-stu-id="5e423-121">This command works even when the destination is read-only.</span></span>

<span data-ttu-id="5e423-122">Map kopiëren werkt op dezelfde manier.</span><span class="sxs-lookup"><span data-stu-id="5e423-122">Folder copying works the same way.</span></span> <span data-ttu-id="5e423-123">Deze opdracht wordt de map C:\\temp\\test1 naar de nieuwe map C:\\temp\\DeleteMe recursief:</span><span class="sxs-lookup"><span data-stu-id="5e423-123">This command copies the folder C:\\temp\\test1 to the new folder C:\\temp\\DeleteMe recursively:</span></span>

```powershell
Copy-Item C:\temp\test1 -Recurse C:\temp\DeleteMe
```

<span data-ttu-id="5e423-124">U kunt ook een selectie van items kopiëren.</span><span class="sxs-lookup"><span data-stu-id="5e423-124">You can also copy a selection of items.</span></span> <span data-ttu-id="5e423-125">De volgende opdracht kopieert alle txt-bestanden die deel uitmaken van een willekeurige plaats c:\\gegevens naar c:\\temp\\tekst:</span><span class="sxs-lookup"><span data-stu-id="5e423-125">The following command copies all .txt files contained anywhere in c:\\data to c:\\temp\\text:</span></span>

```powershell
Copy-Item -Filter *.txt -Path c:\data -Recurse -Destination C:\temp\text
```

<span data-ttu-id="5e423-126">U kunt nog steeds andere hulpprogramma's gebruiken om uit te voeren bestandskopie van het systeem.</span><span class="sxs-lookup"><span data-stu-id="5e423-126">You can still use other tools to perform file system copies.</span></span> <span data-ttu-id="5e423-127">XCOPY en ROBOCOPY COM-objecten, zoals de **Scripting.FileSystemObject,** alle werken in Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="5e423-127">XCOPY, ROBOCOPY, and COM objects, such as the **Scripting.FileSystemObject,** all work in Windows PowerShell.</span></span> <span data-ttu-id="5e423-128">Bijvoorbeeld, kunt u de Windows Script Host **Scripting.FileSystem COM** klasse back-up C:\\boot.ini naar C:\\boot.bak:</span><span class="sxs-lookup"><span data-stu-id="5e423-128">For example, you can use the Windows Script Host **Scripting.FileSystem COM** class to back up C:\\boot.ini to C:\\boot.bak:</span></span>

```powershell
(New-Object -ComObject Scripting.FileSystemObject).CopyFile('C:\boot.ini', 'C:\boot.bak')
```

## <a name="creating-files-and-folders"></a><span data-ttu-id="5e423-129">Het maken van bestanden en mappen</span><span class="sxs-lookup"><span data-stu-id="5e423-129">Creating Files and Folders</span></span>

<span data-ttu-id="5e423-130">Het maken van nieuwe items werkt hetzelfde voor alle Windows PowerShell-providers.</span><span class="sxs-lookup"><span data-stu-id="5e423-130">Creating new items works the same on all Windows PowerShell providers.</span></span> <span data-ttu-id="5e423-131">Als een Windows PowerShell-provider meer dan één type item heeft, bijvoorbeeld, het bestandssysteem Windows PowerShell-provider wordt onderscheid gemaakt tussen de mappen en bestanden, moet u het itemtype opgeven.</span><span class="sxs-lookup"><span data-stu-id="5e423-131">If a Windows PowerShell provider has more than one type of item—for example, the FileSystem Windows PowerShell provider distinguishes between directories and files—you need to specify the item type.</span></span>

<span data-ttu-id="5e423-132">Deze opdracht maakt u een nieuwe map C:\\temp\\nieuwe map:</span><span class="sxs-lookup"><span data-stu-id="5e423-132">This command creates a new folder C:\\temp\\New Folder:</span></span>

```powershell
New-Item -Path 'C:\temp\New Folder' -ItemType Directory
```

<span data-ttu-id="5e423-133">Deze opdracht maakt u een nieuwe lege bestand C:\\temp\\nieuwe map\\bestand.txt</span><span class="sxs-lookup"><span data-stu-id="5e423-133">This command creates a new empty file C:\\temp\\New Folder\\file.txt</span></span>

```powershell
New-Item -Path 'C:\temp\New Folder\file.txt' -ItemType File
```

## <a name="removing-all-files-and-folders-within-a-folder"></a><span data-ttu-id="5e423-134">Alle bestanden en mappen in een map verwijderen</span><span class="sxs-lookup"><span data-stu-id="5e423-134">Removing All Files and Folders Within a Folder</span></span>

<span data-ttu-id="5e423-135">Kunt u de opgenomen items met **Remove-Item**, maar u wordt gevraagd om te bevestigen van de verwijzing wordt verwijderd als het item iets anders bevat.</span><span class="sxs-lookup"><span data-stu-id="5e423-135">You can remove contained items using **Remove-Item**, but you will be prompted to confirm the removal if the item contains anything else.</span></span> <span data-ttu-id="5e423-136">Bijvoorbeeld, als u probeert te verwijderen van de map C:\\temp\\DeleteMe met andere items, Windows PowerShell wordt u gevraagd om bevestiging voordat u verwijdert de map:</span><span class="sxs-lookup"><span data-stu-id="5e423-136">For example, if you attempt to delete the folder C:\\temp\\DeleteMe that contains other items, Windows PowerShell prompts you for confirmation before deleting the folder:</span></span>

```
Remove-Item -Path C:\temp\DeleteMe

Confirm
The item at C:\temp\DeleteMe has children and the -recurse parameter was not
specified. If you continue, all children will be removed with the item. Are you
sure you want to continue?
[Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help
(default is "Y"):
```

<span data-ttu-id="5e423-137">Als u niet elk ingesloten item worden gevraagd wilt, geeft u de **Recurse** parameter:</span><span class="sxs-lookup"><span data-stu-id="5e423-137">If you do not want to be prompted for each contained item, specify the **Recurse** parameter:</span></span>

```powershell
Remove-Item -Path C:\temp\DeleteMe -Recurse
```

## <a name="mapping-a-local-folder-as-a-windows-accessible-drive"></a><span data-ttu-id="5e423-138">Toewijzing van een lokale map als een toegankelijke Windows-station</span><span class="sxs-lookup"><span data-stu-id="5e423-138">Mapping a Local Folder as a Windows Accessible Drive</span></span>

<span data-ttu-id="5e423-139">U kunt ook een lokale map toewijzen met behulp van de **subst** opdracht.</span><span class="sxs-lookup"><span data-stu-id="5e423-139">You can also map a local folder, using the **subst** command.</span></span> <span data-ttu-id="5e423-140">De volgende opdracht maakt een lokaal station die p: geroot in de lokale map Program Files:</span><span class="sxs-lookup"><span data-stu-id="5e423-140">The following command creates a local drive P: rooted in the local Program Files directory:</span></span>

```powershell
subst p: $env:programfiles
```

<span data-ttu-id="5e423-141">Net als bij stations, de stations die zijn toegewezen in met behulp van Windows PowerShell **subst** zijn direct zichtbaar zijn voor de Windows PowerShell-shell.</span><span class="sxs-lookup"><span data-stu-id="5e423-141">Just as with network drives, drives mapped within Windows PowerShell using **subst** are immediately visible to the Windows PowerShell shell.</span></span>

## <a name="reading-a-text-file-into-an-array"></a><span data-ttu-id="5e423-142">Een tekstbestand lezen in een matrix</span><span class="sxs-lookup"><span data-stu-id="5e423-142">Reading a Text File into an Array</span></span>

<span data-ttu-id="5e423-143">Een van de meest voorkomende opslagindelingen voor tekstgegevens zich in een bestand met afzonderlijke regels behandeld als afzonderlijke gegevenselementen.</span><span class="sxs-lookup"><span data-stu-id="5e423-143">One of the more common storage formats for text data is in a file with separate lines treated as distinct data elements.</span></span> <span data-ttu-id="5e423-144">De **Get-inhoud** cmdlet kan worden gebruikt om een volledige bestand in één stap te lezen, zoals hier wordt weergegeven:</span><span class="sxs-lookup"><span data-stu-id="5e423-144">The **Get-Content** cmdlet can be used to read an entire file in one step, as shown here:</span></span>

```
PS> Get-Content -Path C:\boot.ini
[boot loader]
timeout=5
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional"
 /noexecute=AlwaysOff /fastdetect
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS=" Microsoft Windows XP Professional
with Data Execution Prevention" /noexecute=optin /fastdetect
```

<span data-ttu-id="5e423-145">**Get-inhoud** al behandelt de gegevens lezen uit het bestand als een matrix, met één element per regel van de inhoud van bestand.</span><span class="sxs-lookup"><span data-stu-id="5e423-145">**Get-Content** already treats the data read from the file as an array, with one element per line of file content.</span></span> <span data-ttu-id="5e423-146">U kunt dit bevestigen door het controleren van de **lengte** van de geretourneerde inhoud:</span><span class="sxs-lookup"><span data-stu-id="5e423-146">You can confirm this by checking the **Length** of the returned content:</span></span>

```
PS> (Get-Content -Path C:\boot.ini).Length
6
```

<span data-ttu-id="5e423-147">Met deze opdracht is vooral nuttig zijn voor het ophalen van lijsten met gegevens in Windows PowerShell direct.</span><span class="sxs-lookup"><span data-stu-id="5e423-147">This command is most useful for getting lists of information into Windows PowerShell directly.</span></span> <span data-ttu-id="5e423-148">U kunt bijvoorbeeld een lijst van computernamen of IP-adressen opslaan in een bestand C:\\temp\\domainMembers.txt, met een naam op elke regel van het bestand.</span><span class="sxs-lookup"><span data-stu-id="5e423-148">For example, you might store a list of computer names or IP addresses in a file C:\\temp\\domainMembers.txt, with one name on each line of the file.</span></span> <span data-ttu-id="5e423-149">U kunt **Get-inhoud** voor het ophalen van inhoud van het bestand en plaats u ze in de variabele **$Computers**:</span><span class="sxs-lookup"><span data-stu-id="5e423-149">You can use **Get-Content** to retrieve the file contents and put them in the variable **$Computers**:</span></span>

```powershell
$Computers = Get-Content -Path C:\temp\DomainMembers.txt
```

<span data-ttu-id="5e423-150">**$Computers** is nu een matrix met de naam van een computer in elk element.</span><span class="sxs-lookup"><span data-stu-id="5e423-150">**$Computers** is now an array containing a computer name in each element.</span></span>
