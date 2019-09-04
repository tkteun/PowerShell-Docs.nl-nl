---
ms.date: 06/05/2017
keywords: Power shell, cmdlet
title: Met bestanden en mappen werken
ms.openlocfilehash: 743e261d2f5e8bfa39f2731fca7fea6e5678c711
ms.sourcegitcommit: 02eed65c526ef19cf952c2129f280bb5615bf0c8
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 09/03/2019
ms.locfileid: "70215532"
---
# <a name="working-with-files-and-folders"></a><span data-ttu-id="c105a-103">Met bestanden en mappen werken</span><span class="sxs-lookup"><span data-stu-id="c105a-103">Working with Files and Folders</span></span>

<span data-ttu-id="c105a-104">Het navigeren door Windows Power Shell-stations en het bewerken van de items hierop is vergelijkbaar met het bewerken van bestanden en mappen op fysieke Windows-schijf stations.</span><span class="sxs-lookup"><span data-stu-id="c105a-104">Navigating through Windows PowerShell drives and manipulating the items on them is similar to manipulating files and folders on Windows physical disk drives.</span></span> <span data-ttu-id="c105a-105">In deze sectie wordt beschreven hoe u specifieke bewerkingen voor het bewerken van bestanden en mappen kunt uitvoeren met behulp van Power shell.</span><span class="sxs-lookup"><span data-stu-id="c105a-105">This section discusses how to deal with specific file and folder manipulation tasks using PowerShell.</span></span>

## <a name="listing-all-the-files-and-folders-within-a-folder"></a><span data-ttu-id="c105a-106">Alle bestanden en mappen in een map weer geven</span><span class="sxs-lookup"><span data-stu-id="c105a-106">Listing All the Files and Folders Within a Folder</span></span>

<span data-ttu-id="c105a-107">U kunt alle items rechtstreeks in een map ophalen met behulp van **Get-Child item**.</span><span class="sxs-lookup"><span data-stu-id="c105a-107">You can get all items directly within a folder by using **Get-ChildItem**.</span></span> <span data-ttu-id="c105a-108">Voeg de optionele **Force** -para meter toe om verborgen of systeem items weer te geven.</span><span class="sxs-lookup"><span data-stu-id="c105a-108">Add the optional **Force** parameter to display hidden or system items.</span></span> <span data-ttu-id="c105a-109">Met deze opdracht wordt bijvoorbeeld de directe inhoud van Windows Power Shell-station C weer gegeven (dit is hetzelfde als de fysieke schijf met Windows C):</span><span class="sxs-lookup"><span data-stu-id="c105a-109">For example, this command displays the direct contents of Windows PowerShell Drive C (which is the same as the Windows physical drive C):</span></span>

```powershell
Get-ChildItem -Path C:\ -Force
```

<span data-ttu-id="c105a-110">De opdracht bevat alleen de items die rechtstreeks zijn opgenomen, zoals het gebruik van de **dir** opdracht van cmd. exe of **ls** in een Unix-shell.</span><span class="sxs-lookup"><span data-stu-id="c105a-110">The command lists only the directly contained items, much like using Cmd.exe's **DIR** command or **ls** in a UNIX shell.</span></span> <span data-ttu-id="c105a-111">Als u opgenomen items wilt weer geven, moet u ook de para meter **-recursief** opgeven.</span><span class="sxs-lookup"><span data-stu-id="c105a-111">In order to show contained items, you need to specify the **-Recurse** parameter as well.</span></span> <span data-ttu-id="c105a-112">(Dit kan een zeer lange tijd duren.) Alles op station C weer geven:</span><span class="sxs-lookup"><span data-stu-id="c105a-112">(This can take an extremely long time to complete.) To list everything on the C drive:</span></span>

```powershell
Get-ChildItem -Path C:\ -Force -Recurse
```

<span data-ttu-id="c105a-113">**Get-Child item** kan items filteren met de para meters **Path**, **filter**, **include**en **exclude** , maar deze zijn meestal alleen gebaseerd op naam.</span><span class="sxs-lookup"><span data-stu-id="c105a-113">**Get-ChildItem** can filter items with its **Path**, **Filter**, **Include**, and **Exclude** parameters, but those are typically based only on name.</span></span> <span data-ttu-id="c105a-114">U kunt complexe filtering op basis van andere eigenschappen van items uitvoeren met behulp van **where-object**.</span><span class="sxs-lookup"><span data-stu-id="c105a-114">You can perform complex filtering based on other properties of items by using **Where-Object**.</span></span>

<span data-ttu-id="c105a-115">Met de volgende opdracht worden alle uitvoer bare bestanden in de map Program Files gevonden die voor het laatst zijn gewijzigd na 1 oktober 2005 en die kleiner zijn dan 1 MB of groter dan 10 MB:</span><span class="sxs-lookup"><span data-stu-id="c105a-115">The following command finds all executables within the Program Files folder that were last modified after October 1, 2005 and which are neither smaller than 1 megabyte nor larger than 10 megabytes:</span></span>

```powershell
Get-ChildItem -Path $env:ProgramFiles -Recurse -Include *.exe | Where-Object -FilterScript {($_.LastWriteTime -gt '2005-10-01') -and ($_.Length -ge 1mb) -and ($_.Length -le 10mb)}
```

## <a name="copying-files-and-folders"></a><span data-ttu-id="c105a-116">Kopiëren van bestanden en mappen</span><span class="sxs-lookup"><span data-stu-id="c105a-116">Copying Files and Folders</span></span>

<span data-ttu-id="c105a-117">Kopiëren is voltooid met **copy-item**.</span><span class="sxs-lookup"><span data-stu-id="c105a-117">Copying is done with **Copy-Item**.</span></span> <span data-ttu-id="c105a-118">Met de volgende opdracht maakt u een back\\-up van c: boot\\. ini naar c: boot. bak:</span><span class="sxs-lookup"><span data-stu-id="c105a-118">The following command backs up C:\\boot.ini to C:\\boot.bak:</span></span>

```powershell
Copy-Item -Path C:\boot.ini -Destination C:\boot.bak
```

<span data-ttu-id="c105a-119">Als het doel bestand al bestaat, mislukt de poging tot kopiëren.</span><span class="sxs-lookup"><span data-stu-id="c105a-119">If the destination file already exists, the copy attempt fails.</span></span> <span data-ttu-id="c105a-120">Als u een bestaande bestemming wilt overschrijven, gebruikt u de para meter **Force** :</span><span class="sxs-lookup"><span data-stu-id="c105a-120">To overwrite a pre-existing destination, use the **Force** parameter:</span></span>

```powershell
Copy-Item -Path C:\boot.ini -Destination C:\boot.bak -Force
```

<span data-ttu-id="c105a-121">Deze opdracht werkt zelfs als de bestemming alleen-lezen is.</span><span class="sxs-lookup"><span data-stu-id="c105a-121">This command works even when the destination is read-only.</span></span>

<span data-ttu-id="c105a-122">Kopiëren van mappen werkt op dezelfde manier.</span><span class="sxs-lookup"><span data-stu-id="c105a-122">Folder copying works the same way.</span></span> <span data-ttu-id="c105a-123">Met deze opdracht kopieert u de map\\c\\: Temp test1 naar de nieuwe map\\c\\: Temp DeleteMe recursief:</span><span class="sxs-lookup"><span data-stu-id="c105a-123">This command copies the folder C:\\temp\\test1 to the new folder C:\\temp\\DeleteMe recursively:</span></span>

```powershell
Copy-Item C:\temp\test1 -Recurse C:\temp\DeleteMe
```

<span data-ttu-id="c105a-124">U kunt ook een selectie van items kopiëren.</span><span class="sxs-lookup"><span data-stu-id="c105a-124">You can also copy a selection of items.</span></span> <span data-ttu-id="c105a-125">De volgende opdracht kopieert alle txt-bestanden ergens in c:\\gegevens naar c:\\tijdelijke\\tekst:</span><span class="sxs-lookup"><span data-stu-id="c105a-125">The following command copies all .txt files contained anywhere in c:\\data to c:\\temp\\text:</span></span>

```powershell
Copy-Item -Filter *.txt -Path c:\data -Recurse -Destination C:\temp\text
```

<span data-ttu-id="c105a-126">U kunt nog steeds andere hulpprogram ma's gebruiken om bestandssysteem kopieën uit te voeren.</span><span class="sxs-lookup"><span data-stu-id="c105a-126">You can still use other tools to perform file system copies.</span></span> <span data-ttu-id="c105a-127">XCOPY-, ROBOCOPY-en COM-objecten, zoals **Scripting. File System object,** werken allemaal in Windows Power shell.</span><span class="sxs-lookup"><span data-stu-id="c105a-127">XCOPY, ROBOCOPY, and COM objects, such as the **Scripting.FileSystemObject,** all work in Windows PowerShell.</span></span> <span data-ttu-id="c105a-128">U kunt bijvoorbeeld de Windows Script Host **Scripting. File System-com-** klasse gebruiken om een back-\\up te maken van c:\\boot. ini naar c: boot. bak:</span><span class="sxs-lookup"><span data-stu-id="c105a-128">For example, you can use the Windows Script Host **Scripting.FileSystem COM** class to back up C:\\boot.ini to C:\\boot.bak:</span></span>

```powershell
(New-Object -ComObject Scripting.FileSystemObject).CopyFile('C:\boot.ini', 'C:\boot.bak')
```

## <a name="creating-files-and-folders"></a><span data-ttu-id="c105a-129">Bestanden en mappen maken</span><span class="sxs-lookup"><span data-stu-id="c105a-129">Creating Files and Folders</span></span>

<span data-ttu-id="c105a-130">Het maken van nieuwe items werkt hetzelfde op alle Windows Power shell-providers.</span><span class="sxs-lookup"><span data-stu-id="c105a-130">Creating new items works the same on all Windows PowerShell providers.</span></span> <span data-ttu-id="c105a-131">Als een Windows Power shell-provider meer dan één type item heeft, bijvoorbeeld het bestands systeem van de Windows Power shell-provider onderscheidt tussen mappen en bestanden, moet u het item type opgeven.</span><span class="sxs-lookup"><span data-stu-id="c105a-131">If a Windows PowerShell provider has more than one type of item—for example, the FileSystem Windows PowerShell provider distinguishes between directories and files—you need to specify the item type.</span></span>

<span data-ttu-id="c105a-132">Met deze opdracht maakt u een nieuwe map\\C\\: temp nieuwe map:</span><span class="sxs-lookup"><span data-stu-id="c105a-132">This command creates a new folder C:\\temp\\New Folder:</span></span>

```powershell
New-Item -Path 'C:\temp\New Folder' -ItemType Directory
```

<span data-ttu-id="c105a-133">Met deze opdracht maakt u een nieuw leeg bestand\\C\\: Temp\\nieuwe map bestand. txt</span><span class="sxs-lookup"><span data-stu-id="c105a-133">This command creates a new empty file C:\\temp\\New Folder\\file.txt</span></span>

```powershell
New-Item -Path 'C:\temp\New Folder\file.txt' -ItemType File
```

## <a name="removing-all-files-and-folders-within-a-folder"></a><span data-ttu-id="c105a-134">Alle bestanden en mappen in een map verwijderen</span><span class="sxs-lookup"><span data-stu-id="c105a-134">Removing All Files and Folders Within a Folder</span></span>

<span data-ttu-id="c105a-135">U kunt opgenomen items verwijderen met behulp van **Remove-item**, maar u wordt gevraagd het verwijderen te bevestigen als het item iets anders bevat.</span><span class="sxs-lookup"><span data-stu-id="c105a-135">You can remove contained items using **Remove-Item**, but you will be prompted to confirm the removal if the item contains anything else.</span></span> <span data-ttu-id="c105a-136">Als u bijvoorbeeld probeert de map C:\\Temp\\DeleteMe te verwijderen die andere items bevat, vraagt Windows Power shell u om bevestiging voordat de map wordt verwijderd:</span><span class="sxs-lookup"><span data-stu-id="c105a-136">For example, if you attempt to delete the folder C:\\temp\\DeleteMe that contains other items, Windows PowerShell prompts you for confirmation before deleting the folder:</span></span>

```
Remove-Item -Path C:\temp\DeleteMe

Confirm
The item at C:\temp\DeleteMe has children and the -recurse parameter was not
specified. If you continue, all children will be removed with the item. Are you
sure you want to continue?
[Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help
(default is "Y"):
```

<span data-ttu-id="c105a-137">Als u niet voor elk opgenomen item wilt worden gevraagd, geeft u de para meter **recursief** op:</span><span class="sxs-lookup"><span data-stu-id="c105a-137">If you do not want to be prompted for each contained item, specify the **Recurse** parameter:</span></span>

```powershell
Remove-Item -Path C:\temp\DeleteMe -Recurse
```

## <a name="mapping-a-local-folder-as-a-drive"></a><span data-ttu-id="c105a-138">Een lokale map toewijzen als een station</span><span class="sxs-lookup"><span data-stu-id="c105a-138">Mapping a Local Folder as a drive</span></span>

<span data-ttu-id="c105a-139">U kunt ook een lokale map toewijzen met behulp van de opdracht **New-PSDrive** .</span><span class="sxs-lookup"><span data-stu-id="c105a-139">You can also map a local folder, using the **New-PSDrive** command.</span></span> <span data-ttu-id="c105a-140">Met de volgende opdracht maakt u een lokaal station P: geroot in de lokale map Program Files, alleen zichtbaar vanuit de Power shell-sessie:</span><span class="sxs-lookup"><span data-stu-id="c105a-140">The following command creates a local drive P: rooted in the local Program Files directory, visible only from the PowerShell session:</span></span>

```powershell
New-PSDrive -Name P -Root $env:ProgramFiles -PSProvider FileSystem
```

<span data-ttu-id="c105a-141">Net als bij netwerk stations zijn stations die zijn toegewezen in Windows Power shell, direct zichtbaar voor de Windows Power shell-shell.</span><span class="sxs-lookup"><span data-stu-id="c105a-141">Just as with network drives, drives mapped within Windows PowerShell are immediately visible to the Windows PowerShell shell.</span></span>
<span data-ttu-id="c105a-142">Voor het maken van een toegewezen station dat zichtbaar is vanuit Verkenner, is de para meter **persistent** .</span><span class="sxs-lookup"><span data-stu-id="c105a-142">In order to create a mapped drive visible from File Explorer, the parameter **-Persist** is needed.</span></span> <span data-ttu-id="c105a-143">Er kunnen echter alleen externe paden worden gebruikt met persistent.</span><span class="sxs-lookup"><span data-stu-id="c105a-143">However, only remote paths can be used with Persist.</span></span>


## <a name="reading-a-text-file-into-an-array"></a><span data-ttu-id="c105a-144">Een tekst bestand in een matrix lezen</span><span class="sxs-lookup"><span data-stu-id="c105a-144">Reading a Text File into an Array</span></span>

<span data-ttu-id="c105a-145">Een van de meest voorkomende opslag indelingen voor tekst gegevens bevindt zich in een bestand met afzonderlijke regels behandeld als afzonderlijke gegevens elementen.</span><span class="sxs-lookup"><span data-stu-id="c105a-145">One of the more common storage formats for text data is in a file with separate lines treated as distinct data elements.</span></span> <span data-ttu-id="c105a-146">De cmdlet **Get-content** kan worden gebruikt om een volledig bestand in één stap te lezen, zoals hier wordt weer gegeven:</span><span class="sxs-lookup"><span data-stu-id="c105a-146">The **Get-Content** cmdlet can be used to read an entire file in one step, as shown here:</span></span>

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

<span data-ttu-id="c105a-147">**Get-content** behandelt al de gegevens die uit het bestand zijn gelezen als een matrix, met één element per regel van het bestand.</span><span class="sxs-lookup"><span data-stu-id="c105a-147">**Get-Content** already treats the data read from the file as an array, with one element per line of file content.</span></span> <span data-ttu-id="c105a-148">U kunt dit controleren door de **lengte** van de geretourneerde inhoud te controleren:</span><span class="sxs-lookup"><span data-stu-id="c105a-148">You can confirm this by checking the **Length** of the returned content:</span></span>

```
PS> (Get-Content -Path C:\boot.ini).Length
6
```

<span data-ttu-id="c105a-149">Deze opdracht is vooral handig voor het rechtstreeks ophalen van lijsten met gegevens in Windows Power shell.</span><span class="sxs-lookup"><span data-stu-id="c105a-149">This command is most useful for getting lists of information into Windows PowerShell directly.</span></span> <span data-ttu-id="c105a-150">U kunt bijvoorbeeld een lijst met computer namen of IP-adressen opslaan in een bestand C:\\Temp\\domainMembers. txt, met één naam op elke regel van het bestand.</span><span class="sxs-lookup"><span data-stu-id="c105a-150">For example, you might store a list of computer names or IP addresses in a file C:\\temp\\domainMembers.txt, with one name on each line of the file.</span></span> <span data-ttu-id="c105a-151">U kunt **Get-content** gebruiken om de bestands inhoud op te halen en deze in de variabele **$computers**te plaatsen:</span><span class="sxs-lookup"><span data-stu-id="c105a-151">You can use **Get-Content** to retrieve the file contents and put them in the variable **$Computers**:</span></span>

```powershell
$Computers = Get-Content -Path C:\temp\DomainMembers.txt
```

<span data-ttu-id="c105a-152">**$Computers** is nu een matrix met een computer naam in elk-element.</span><span class="sxs-lookup"><span data-stu-id="c105a-152">**$Computers** is now an array containing a computer name in each element.</span></span>
