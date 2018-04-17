---
ms.date: 06/05/2017
keywords: PowerShell-cmdlet
title: Met bestanden en mappen werken
ms.assetid: c0ceb96b-e708-45f3-803b-d1f61a48f4c1
ms.openlocfilehash: 6b1fcd438570c8708aa87e4b213f33474921d5f8
ms.sourcegitcommit: ece1794c94be4880a2af5a2605ed4721593643b6
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 04/16/2018
---
# <a name="working-with-files-and-folders"></a><span data-ttu-id="d56aa-103">Met bestanden en mappen werken</span><span class="sxs-lookup"><span data-stu-id="d56aa-103">Working with Files and Folders</span></span>

<span data-ttu-id="d56aa-104">Navigeren door Windows PowerShell-stations en bewerken van de items op deze lijkt op het manipuleren van bestanden en mappen op de fysieke schijven Windows.</span><span class="sxs-lookup"><span data-stu-id="d56aa-104">Navigating through Windows PowerShell drives and manipulating the items on them is similar to manipulating files and folders on Windows physical disk drives.</span></span> <span data-ttu-id="d56aa-105">Deze sectie wordt beschreven hoe u omgaat met specifieke bestanden en mappen manipulatie taken-met behulp van PowerShell.</span><span class="sxs-lookup"><span data-stu-id="d56aa-105">This section discusses how to deal with specific file and folder manipulation tasks using PowerShell.</span></span>

### <a name="listing-all-the-files-and-folders-within-a-folder"></a><span data-ttu-id="d56aa-106">Lijst van alle bestanden en mappen in een map</span><span class="sxs-lookup"><span data-stu-id="d56aa-106">Listing All the Files and Folders Within a Folder</span></span>

<span data-ttu-id="d56aa-107">U kunt alle items rechtstreeks in een map verkrijgen door middel van **Get-ChildItem**.</span><span class="sxs-lookup"><span data-stu-id="d56aa-107">You can get all items directly within a folder by using **Get-ChildItem**.</span></span> <span data-ttu-id="d56aa-108">Voeg de optionele **Force** parameter worden verborgen items van system.</span><span class="sxs-lookup"><span data-stu-id="d56aa-108">Add the optional **Force** parameter to display hidden or system items.</span></span> <span data-ttu-id="d56aa-109">Deze opdracht geeft bijvoorbeeld de inhoud direct van Windows PowerShell-station C (dit is hetzelfde als het fysieke Windows-station C):</span><span class="sxs-lookup"><span data-stu-id="d56aa-109">For example, this command displays the direct contents of Windows PowerShell Drive C (which is the same as the Windows physical drive C):</span></span>

```powershell
Get-ChildItem -Path C:\ -Force
```

<span data-ttu-id="d56aa-110">De opdracht bevat alleen de rechtstreeks opgenomen items, vergelijkbaar met behulp van Cmd.exe **DIR** opdracht of **ls** in een UNIX-shell.</span><span class="sxs-lookup"><span data-stu-id="d56aa-110">The command lists only the directly contained items, much like using Cmd.exe's **DIR** command or **ls** in a UNIX shell.</span></span> <span data-ttu-id="d56aa-111">Om te geven opgenomen items, moet u opgeven de **-Recurse** ook de parameter.</span><span class="sxs-lookup"><span data-stu-id="d56aa-111">In order to show contained items, you need to specify the **-Recurse** parameter as well.</span></span> <span data-ttu-id="d56aa-112">(Dit kan een zeer lange tijd in beslag nemen.) Overzicht van alles op het station C:</span><span class="sxs-lookup"><span data-stu-id="d56aa-112">(This can take an extremely long time to complete.) To list everything on the C drive:</span></span>

```powershell
Get-ChildItem -Path C:\ -Force -Recurse
```

<span data-ttu-id="d56aa-113">**Get-ChildItem** kunt items filteren met de **pad**, **Filter**, **opnemen**, en **uitsluiten** parameters, maar deze zijn Normaal gesproken alleen gebaseerd op naam.</span><span class="sxs-lookup"><span data-stu-id="d56aa-113">**Get-ChildItem** can filter items with its **Path**, **Filter**, **Include**, and **Exclude** parameters, but those are typically based only on name.</span></span> <span data-ttu-id="d56aa-114">U kunt uitvoeren complexe filteren op basis van andere eigenschappen van items door **Where-Object**.</span><span class="sxs-lookup"><span data-stu-id="d56aa-114">You can perform complex filtering based on other properties of items by using **Where-Object**.</span></span>

<span data-ttu-id="d56aa-115">De volgende opdracht wordt gezocht naar alle uitvoerbare bestanden in de map Program Files die het laatst zijn gewijzigd na 1 oktober 2005 en die niet kleiner is dan 1 MB noch groter dan 10 MB zijn:</span><span class="sxs-lookup"><span data-stu-id="d56aa-115">The following command finds all executables within the Program Files folder that were last modified after October 1, 2005 and which are neither smaller than 1 megabyte nor larger than 10 megabytes:</span></span>

```powershell
Get-ChildItem -Path $env:ProgramFiles -Recurse -Include *.exe | Where-Object -FilterScript {($_.LastWriteTime -gt '2005-10-01') -and ($_.Length -ge 1mb) -and ($_.Length -le 10mb)}
```

### <a name="copying-files-and-folders"></a><span data-ttu-id="d56aa-116">Kopiëren van bestanden en mappen</span><span class="sxs-lookup"><span data-stu-id="d56aa-116">Copying Files and Folders</span></span>

<span data-ttu-id="d56aa-117">Kopiëren is klaar met **Copy-Item**.</span><span class="sxs-lookup"><span data-stu-id="d56aa-117">Copying is done with **Copy-Item**.</span></span> <span data-ttu-id="d56aa-118">De volgende opdracht maakt een back-up C:\\boot.ini naar C:\\boot.bak:</span><span class="sxs-lookup"><span data-stu-id="d56aa-118">The following command backs up C:\\boot.ini to C:\\boot.bak:</span></span>

```powershell
Copy-Item -Path C:\boot.ini -Destination C:\boot.bak
```

<span data-ttu-id="d56aa-119">Als het doelbestand al bestaat, mislukt die poging kopiëren.</span><span class="sxs-lookup"><span data-stu-id="d56aa-119">If the destination file already exists, the copy attempt fails.</span></span> <span data-ttu-id="d56aa-120">Als u wilt een reeds bestaande bestemming overschrijven, gebruiken de **Force** parameter:</span><span class="sxs-lookup"><span data-stu-id="d56aa-120">To overwrite a pre-existing destination, use the **Force** parameter:</span></span>

```powershell
Copy-Item -Path C:\boot.ini -Destination C:\boot.bak -Force
```

<span data-ttu-id="d56aa-121">Met deze opdracht werkt zelfs wanneer het doel alleen-lezen is.</span><span class="sxs-lookup"><span data-stu-id="d56aa-121">This command works even when the destination is read-only.</span></span>

<span data-ttu-id="d56aa-122">Werkt op dezelfde manier map kopiëren.</span><span class="sxs-lookup"><span data-stu-id="d56aa-122">Folder copying works the same way.</span></span> <span data-ttu-id="d56aa-123">Deze opdracht kopieert u de map C:\\temp\\test1 naar de nieuwe map C:\\temp\\DeleteMe recursief:</span><span class="sxs-lookup"><span data-stu-id="d56aa-123">This command copies the folder C:\\temp\\test1 to the new folder C:\\temp\\DeleteMe recursively:</span></span>

```powershell
Copy-Item C:\temp\test1 -Recurse C:\temp\DeleteMe
```

<span data-ttu-id="d56aa-124">U kunt ook een selectie van items kopiëren.</span><span class="sxs-lookup"><span data-stu-id="d56aa-124">You can also copy a selection of items.</span></span> <span data-ttu-id="d56aa-125">De volgende opdracht kopieert alle txt-bestanden die zich ergens in c:\\gegevens naar c:\\temp\\tekst:</span><span class="sxs-lookup"><span data-stu-id="d56aa-125">The following command copies all .txt files contained anywhere in c:\\data to c:\\temp\\text:</span></span>

```powershell
Copy-Item -Filter *.txt -Path c:\data -Recurse -Destination C:\temp\text
```

<span data-ttu-id="d56aa-126">U kunt nog steeds andere hulpprogramma's gebruiken om systeem te bestand kopiëren.</span><span class="sxs-lookup"><span data-stu-id="d56aa-126">You can still use other tools to perform file system copies.</span></span> <span data-ttu-id="d56aa-127">XCOPY en ROBOCOPY COM-objecten, zoals de **Scripting.FileSystemObject,** werkt met alle in Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="d56aa-127">XCOPY, ROBOCOPY, and COM objects, such as the **Scripting.FileSystemObject,** all work in Windows PowerShell.</span></span> <span data-ttu-id="d56aa-128">Bijvoorbeeld, kunt u Windows Script Host **Scripting.FileSystem COM** klasse back-up C:\\boot.ini naar C:\\boot.bak:</span><span class="sxs-lookup"><span data-stu-id="d56aa-128">For example, you can use the Windows Script Host **Scripting.FileSystem COM** class to back up C:\\boot.ini to C:\\boot.bak:</span></span>

```powershell
(New-Object -ComObject Scripting.FileSystemObject).CopyFile('C:\boot.ini', 'C:\boot.bak')
```

### <a name="creating-files-and-folders"></a><span data-ttu-id="d56aa-129">Bestanden en mappen maken</span><span class="sxs-lookup"><span data-stu-id="d56aa-129">Creating Files and Folders</span></span>

<span data-ttu-id="d56aa-130">Maken van nieuwe items werkt op dezelfde op alle Windows PowerShell-providers.</span><span class="sxs-lookup"><span data-stu-id="d56aa-130">Creating new items works the same on all Windows PowerShell providers.</span></span> <span data-ttu-id="d56aa-131">Als een Windows PowerShell-provider meer dan één type item heeft, bijvoorbeeld, het bestandssysteem Windows PowerShell-provider wordt onderscheid gemaakt tussen de mappen en bestanden, moet u het itemtype opgeven.</span><span class="sxs-lookup"><span data-stu-id="d56aa-131">If a Windows PowerShell provider has more than one type of item—for example, the FileSystem Windows PowerShell provider distinguishes between directories and files—you need to specify the item type.</span></span>

<span data-ttu-id="d56aa-132">Deze opdracht maakt u een nieuwe map C:\\temp\\nieuwe map:</span><span class="sxs-lookup"><span data-stu-id="d56aa-132">This command creates a new folder C:\\temp\\New Folder:</span></span>

```powershell
New-Item -Path 'C:\temp\New Folder' -ItemType Directory
```

<span data-ttu-id="d56aa-133">Deze opdracht maakt u een nieuwe lege bestand C:\\temp\\nieuwe map\\bestand.txt</span><span class="sxs-lookup"><span data-stu-id="d56aa-133">This command creates a new empty file C:\\temp\\New Folder\\file.txt</span></span>

```powershell
New-Item -Path 'C:\temp\New Folder\file.txt' -ItemType File
```

### <a name="removing-all-files-and-folders-within-a-folder"></a><span data-ttu-id="d56aa-134">Alle bestanden en mappen in een map verwijderen</span><span class="sxs-lookup"><span data-stu-id="d56aa-134">Removing All Files and Folders Within a Folder</span></span>

<span data-ttu-id="d56aa-135">U kunt verwijderen opgenomen items met **Item verwijderen**, maar u wordt gevraagd om te bevestigen dat de verwijzing wordt verwijderd als het item iets anders bevat.</span><span class="sxs-lookup"><span data-stu-id="d56aa-135">You can remove contained items using **Remove-Item**, but you will be prompted to confirm the removal if the item contains anything else.</span></span> <span data-ttu-id="d56aa-136">Bijvoorbeeld, als u probeert te verwijderen van de map C:\\temp\\DeleteMe die andere items bevat, Windows PowerShell wordt u gevraagd om bevestiging voordat u de map te verwijderen:</span><span class="sxs-lookup"><span data-stu-id="d56aa-136">For example, if you attempt to delete the folder C:\\temp\\DeleteMe that contains other items, Windows PowerShell prompts you for confirmation before deleting the folder:</span></span>

```
Remove-Item -Path C:\temp\DeleteMe

Confirm
The item at C:\temp\DeleteMe has children and the -recurse parameter was not
specified. If you continue, all children will be removed with the item. Are you
sure you want to continue?
[Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help
(default is "Y"):
```

<span data-ttu-id="d56aa-137">Als u niet worden gevraagd om elk item opgenomen wilt, geeft u de **Recurse** parameter:</span><span class="sxs-lookup"><span data-stu-id="d56aa-137">If you do not want to be prompted for each contained item, specify the **Recurse** parameter:</span></span>

```powershell
Remove-Item -Path C:\temp\DeleteMe -Recurse
```

### <a name="mapping-a-local-folder-as-a-windows-accessible-drive"></a><span data-ttu-id="d56aa-138">Toewijzing van een lokale map als Windows toegankelijk station</span><span class="sxs-lookup"><span data-stu-id="d56aa-138">Mapping a Local Folder as a Windows Accessible Drive</span></span>

<span data-ttu-id="d56aa-139">U kunt ook een lokale map toewijzen met behulp van de **subst** opdracht.</span><span class="sxs-lookup"><span data-stu-id="d56aa-139">You can also map a local folder, using the **subst** command.</span></span> <span data-ttu-id="d56aa-140">De volgende opdracht maakt een lokaal station die p: geroot in de lokale map Program Files:</span><span class="sxs-lookup"><span data-stu-id="d56aa-140">The following command creates a local drive P: rooted in the local Program Files directory:</span></span>

```powershell
subst p: $env:programfiles
```

<span data-ttu-id="d56aa-141">Net als bij netwerkstations, de stations die zijn toegewezen binnen met behulp van Windows PowerShell **subst** zijn direct zichtbaar voor de Windows PowerShell-shell.</span><span class="sxs-lookup"><span data-stu-id="d56aa-141">Just as with network drives, drives mapped within Windows PowerShell using **subst** are immediately visible to the Windows PowerShell shell.</span></span>

### <a name="reading-a-text-file-into-an-array"></a><span data-ttu-id="d56aa-142">Een tekstbestand lezen in een matrix</span><span class="sxs-lookup"><span data-stu-id="d56aa-142">Reading a Text File into an Array</span></span>

<span data-ttu-id="d56aa-143">Een van de meest voorkomende opslagindelingen voor tekstgegevens is in een bestand met afzonderlijke regels behandeld als verschillende gegevenselementen.</span><span class="sxs-lookup"><span data-stu-id="d56aa-143">One of the more common storage formats for text data is in a file with separate lines treated as distinct data elements.</span></span> <span data-ttu-id="d56aa-144">De **Get-inhoud** cmdlet kan worden gebruikt om te lezen van een volledig bestand mogelijk in één stap, zoals hier wordt weergegeven:</span><span class="sxs-lookup"><span data-stu-id="d56aa-144">The **Get-Content** cmdlet can be used to read an entire file in one step, as shown here:</span></span>

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

<span data-ttu-id="d56aa-145">**Get-inhoud** al behandelt de gegevens lezen uit het bestand als een matrix met één element per regel van de inhoud van bestand.</span><span class="sxs-lookup"><span data-stu-id="d56aa-145">**Get-Content** already treats the data read from the file as an array, with one element per line of file content.</span></span> <span data-ttu-id="d56aa-146">U kunt dit bevestigen door het controleren van de **lengte** van de geretourneerde inhoud:</span><span class="sxs-lookup"><span data-stu-id="d56aa-146">You can confirm this by checking the **Length** of the returned content:</span></span>

```
PS> (Get-Content -Path C:\boot.ini).Length
6
```

<span data-ttu-id="d56aa-147">Met deze opdracht is vooral handig voor het rechtstreeks ophalen van de lijsten met gegevens in Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="d56aa-147">This command is most useful for getting lists of information into Windows PowerShell directly.</span></span> <span data-ttu-id="d56aa-148">Bijvoorbeeld, u een lijst met computernamen of IP-adressen mogelijk opslaan in een bestand C:\\temp\\domainMembers.txt met een naam op elke regel van het bestand.</span><span class="sxs-lookup"><span data-stu-id="d56aa-148">For example, you might store a list of computer names or IP addresses in a file C:\\temp\\domainMembers.txt, with one name on each line of the file.</span></span> <span data-ttu-id="d56aa-149">U kunt **Get-inhoud** inhoud van het bestand ophalen en plaatsen in de variabele **$Computers**:</span><span class="sxs-lookup"><span data-stu-id="d56aa-149">You can use **Get-Content** to retrieve the file contents and put them in the variable **$Computers**:</span></span>

```powershell
$Computers = Get-Content -Path C:\temp\DomainMembers.txt
```

<span data-ttu-id="d56aa-150">**$Computers** is nu een matrix met de naam van een computer in elk element.</span><span class="sxs-lookup"><span data-stu-id="d56aa-150">**$Computers** is now an array containing a computer name in each element.</span></span>
