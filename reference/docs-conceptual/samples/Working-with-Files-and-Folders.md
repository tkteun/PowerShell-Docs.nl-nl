---
ms.date: 06/05/2017
keywords: powershell,cmdlet
title: Met bestanden en mappen werken
description: In dit artikel wordt beschreven hoe u specifieke bewerkingen voor het bewerken van bestanden en mappen kunt uitvoeren met behulp van Power shell.
ms.openlocfilehash: c0c3abb082b05296daa480ac06bcbfa3a784e0c9
ms.sourcegitcommit: 9080316e3ca4f11d83067b41351531672b667b7a
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/24/2020
ms.locfileid: "92500025"
---
# <a name="working-with-files-and-folders"></a><span data-ttu-id="4f835-104">Met bestanden en mappen werken</span><span class="sxs-lookup"><span data-stu-id="4f835-104">Working with Files and Folders</span></span>

<span data-ttu-id="4f835-105">Het navigeren door Windows Power Shell-stations en het bewerken van de items hierop is vergelijkbaar met het bewerken van bestanden en mappen op fysieke Windows-schijf stations.</span><span class="sxs-lookup"><span data-stu-id="4f835-105">Navigating through Windows PowerShell drives and manipulating the items on them is similar to manipulating files and folders on Windows physical disk drives.</span></span> <span data-ttu-id="4f835-106">In dit artikel wordt beschreven hoe u specifieke bewerkingen voor het bewerken van bestanden en mappen kunt uitvoeren met behulp van Power shell.</span><span class="sxs-lookup"><span data-stu-id="4f835-106">This article discusses how to deal with specific file and folder manipulation tasks using PowerShell.</span></span>

## <a name="listing-all-the-files-and-folders-within-a-folder"></a><span data-ttu-id="4f835-107">Alle bestanden en mappen in een map weer geven</span><span class="sxs-lookup"><span data-stu-id="4f835-107">Listing All the Files and Folders Within a Folder</span></span>

<span data-ttu-id="4f835-108">U kunt alle items rechtstreeks in een map ophalen met behulp van `Get-ChildItem` .</span><span class="sxs-lookup"><span data-stu-id="4f835-108">You can get all items directly within a folder by using `Get-ChildItem`.</span></span> <span data-ttu-id="4f835-109">Voeg de optionele **Force** -para meter toe om verborgen of systeem items weer te geven.</span><span class="sxs-lookup"><span data-stu-id="4f835-109">Add the optional **Force** parameter to display hidden or system items.</span></span> <span data-ttu-id="4f835-110">Met deze opdracht wordt bijvoorbeeld de directe inhoud van Windows Power Shell-station C weer gegeven (dit is hetzelfde als de fysieke schijf met Windows C):</span><span class="sxs-lookup"><span data-stu-id="4f835-110">For example, this command displays the direct contents of Windows PowerShell Drive C (which is the same as the Windows physical drive C):</span></span>

```powershell
Get-ChildItem -Path C:\ -Force
```

<span data-ttu-id="4f835-111">Met de opdracht worden alleen de direct opgenomen items weer gegeven, net zoals de `Cmd.exe` `DIR` opdracht of `ls` in een Unix-shell.</span><span class="sxs-lookup"><span data-stu-id="4f835-111">The command lists only the directly contained items, much like using `Cmd.exe`'s `DIR` command or `ls` in a UNIX shell.</span></span> <span data-ttu-id="4f835-112">Als u opgenomen items wilt weer geven, moet u ook de `-Recurse` para meter opgeven.</span><span class="sxs-lookup"><span data-stu-id="4f835-112">In order to show contained items, you need to specify the `-Recurse` parameter as well.</span></span> <span data-ttu-id="4f835-113">(Dit kan een zeer lange tijd duren.) Alles op station C weer geven:</span><span class="sxs-lookup"><span data-stu-id="4f835-113">(This can take an extremely long time to complete.) To list everything on the C drive:</span></span>

```powershell
Get-ChildItem -Path C:\ -Force -Recurse
```

<span data-ttu-id="4f835-114">`Get-ChildItem` kan items filteren met de para meters **Path**, **filter**, **include**en **exclude** , maar deze zijn meestal alleen gebaseerd op naam.</span><span class="sxs-lookup"><span data-stu-id="4f835-114">`Get-ChildItem` can filter items with its **Path**, **Filter**, **Include**, and **Exclude** parameters, but those are typically based only on name.</span></span> <span data-ttu-id="4f835-115">U kunt complexe filtering uitvoeren op basis van andere eigenschappen van items met behulp van `Where-Object` .</span><span class="sxs-lookup"><span data-stu-id="4f835-115">You can perform complex filtering based on other properties of items by using `Where-Object`.</span></span>

<span data-ttu-id="4f835-116">Met de volgende opdracht worden alle uitvoer bare bestanden in de map Program Files gevonden die voor het laatst zijn gewijzigd na 1 oktober 2005 en die kleiner zijn dan 1 MB of groter dan 10 MB:</span><span class="sxs-lookup"><span data-stu-id="4f835-116">The following command finds all executables within the Program Files folder that were last modified after October 1, 2005 and which are neither smaller than 1 megabyte nor larger than 10 megabytes:</span></span>

```powershell
Get-ChildItem -Path $env:ProgramFiles -Recurse -Include *.exe | Where-Object -FilterScript {($_.LastWriteTime -gt '2005-10-01') -and ($_.Length -ge 1mb) -and ($_.Length -le 10mb)}
```

## <a name="copying-files-and-folders"></a><span data-ttu-id="4f835-117">Kopiëren van bestanden en mappen</span><span class="sxs-lookup"><span data-stu-id="4f835-117">Copying Files and Folders</span></span>

<span data-ttu-id="4f835-118">Kopiëren is voltooid met `Copy-Item` .</span><span class="sxs-lookup"><span data-stu-id="4f835-118">Copying is done with `Copy-Item`.</span></span> <span data-ttu-id="4f835-119">Met de volgende opdracht maakt u een back-up van C: \\boot.ini naar c: \\ boot. bak:</span><span class="sxs-lookup"><span data-stu-id="4f835-119">The following command backs up C:\\boot.ini to C:\\boot.bak:</span></span>

```powershell
Copy-Item -Path C:\boot.ini -Destination C:\boot.bak
```

<span data-ttu-id="4f835-120">Als het doel bestand al bestaat, mislukt de poging tot kopiëren.</span><span class="sxs-lookup"><span data-stu-id="4f835-120">If the destination file already exists, the copy attempt fails.</span></span> <span data-ttu-id="4f835-121">Als u een bestaande bestemming wilt overschrijven, gebruikt u de para meter **Force** :</span><span class="sxs-lookup"><span data-stu-id="4f835-121">To overwrite a pre-existing destination, use the **Force** parameter:</span></span>

```powershell
Copy-Item -Path C:\boot.ini -Destination C:\boot.bak -Force
```

<span data-ttu-id="4f835-122">Deze opdracht werkt zelfs als de bestemming alleen-lezen is.</span><span class="sxs-lookup"><span data-stu-id="4f835-122">This command works even when the destination is read-only.</span></span>

<span data-ttu-id="4f835-123">Kopiëren van mappen werkt op dezelfde manier.</span><span class="sxs-lookup"><span data-stu-id="4f835-123">Folder copying works the same way.</span></span> <span data-ttu-id="4f835-124">Met deze opdracht wordt de map `C:\temp\test1` recursief naar de nieuwe map gekopieerd `C:\temp\DeleteMe` :</span><span class="sxs-lookup"><span data-stu-id="4f835-124">This command copies the folder `C:\temp\test1` to the new folder `C:\temp\DeleteMe` recursively:</span></span>

```powershell
Copy-Item C:\temp\test1 -Recurse C:\temp\DeleteMe
```

<span data-ttu-id="4f835-125">U kunt ook een selectie van items kopiëren.</span><span class="sxs-lookup"><span data-stu-id="4f835-125">You can also copy a selection of items.</span></span> <span data-ttu-id="4f835-126">Met de volgende opdracht kopieert u alle txt-bestanden die zich overal in naar bevinden `C:\data` `C:\temp\text` :</span><span class="sxs-lookup"><span data-stu-id="4f835-126">The following command copies all .txt files contained anywhere in `C:\data` to `C:\temp\text`:</span></span>

```powershell
Copy-Item -Filter *.txt -Path c:\data -Recurse -Destination C:\temp\text
```

<span data-ttu-id="4f835-127">U kunt nog steeds andere hulpprogram ma's gebruiken om bestandssysteem kopieën uit te voeren.</span><span class="sxs-lookup"><span data-stu-id="4f835-127">You can still use other tools to perform file system copies.</span></span> <span data-ttu-id="4f835-128">XCOPY-, ROBOCOPY-en COM-objecten, zoals **Scripting. File System object,** werken allemaal in Windows Power shell.</span><span class="sxs-lookup"><span data-stu-id="4f835-128">XCOPY, ROBOCOPY, and COM objects, such as the **Scripting.FileSystemObject,** all work in Windows PowerShell.</span></span> <span data-ttu-id="4f835-129">U kunt bijvoorbeeld de Windows Script Host **Scripting. COM-klasse scripts** gebruiken om een back-up `C:\boot.ini` te maken naar `C:\boot.bak` :</span><span class="sxs-lookup"><span data-stu-id="4f835-129">For example, you can use the Windows Script Host **Scripting.FileSystem COM** class to back up `C:\boot.ini` to `C:\boot.bak`:</span></span>

```powershell
(New-Object -ComObject Scripting.FileSystemObject).CopyFile('C:\boot.ini', 'C:\boot.bak')
```

## <a name="creating-files-and-folders"></a><span data-ttu-id="4f835-130">Bestanden en mappen maken</span><span class="sxs-lookup"><span data-stu-id="4f835-130">Creating Files and Folders</span></span>

<span data-ttu-id="4f835-131">Het maken van nieuwe items werkt hetzelfde op alle Windows Power shell-providers.</span><span class="sxs-lookup"><span data-stu-id="4f835-131">Creating new items works the same on all Windows PowerShell providers.</span></span> <span data-ttu-id="4f835-132">Als een Windows Power shell-provider meer dan één type item heeft, bijvoorbeeld het bestands systeem van de Windows Power shell-provider onderscheidt tussen mappen en bestanden, moet u het item type opgeven.</span><span class="sxs-lookup"><span data-stu-id="4f835-132">If a Windows PowerShell provider has more than one type of item—for example, the FileSystem Windows PowerShell provider distinguishes between directories and files—you need to specify the item type.</span></span>

<span data-ttu-id="4f835-133">Met deze opdracht maakt u een nieuwe map `C:\temp\New Folder` :</span><span class="sxs-lookup"><span data-stu-id="4f835-133">This command creates a new folder `C:\temp\New Folder`:</span></span>

```powershell
New-Item -Path 'C:\temp\New Folder' -ItemType Directory
```

<span data-ttu-id="4f835-134">Met deze opdracht maakt u een nieuw leeg bestand `C:\temp\New Folder\file.txt`</span><span class="sxs-lookup"><span data-stu-id="4f835-134">This command creates a new empty file `C:\temp\New Folder\file.txt`</span></span>

```powershell
New-Item -Path 'C:\temp\New Folder\file.txt' -ItemType File
```

> [!IMPORTANT]
> <span data-ttu-id="4f835-135">Wanneer u de schakel optie **forceert** met de `New-Item` opdracht om een map te maken en de map al bestaat, wordt de map _niet_ overschreven of vervangen.</span><span class="sxs-lookup"><span data-stu-id="4f835-135">When using the **Force** switch with the `New-Item` command to create a folder, and the folder already exists, it _won't_ overwrite or replace the folder.</span></span> <span data-ttu-id="4f835-136">Er wordt gewoon het bestaande map-object geretourneerd.</span><span class="sxs-lookup"><span data-stu-id="4f835-136">It will simply return the existing folder object.</span></span> <span data-ttu-id="4f835-137">Als u echter gebruikt `New-Item -Force` voor een bestand dat al bestaat, _wordt_ het bestand volledig overschreven.</span><span class="sxs-lookup"><span data-stu-id="4f835-137">However, if you use `New-Item -Force` on a file that already exists, the file _will_ be completely overwritten.</span></span>

## <a name="removing-all-files-and-folders-within-a-folder"></a><span data-ttu-id="4f835-138">Alle bestanden en mappen in een map verwijderen</span><span class="sxs-lookup"><span data-stu-id="4f835-138">Removing All Files and Folders Within a Folder</span></span>

<span data-ttu-id="4f835-139">U kunt opgenomen items verwijderen met `Remove-Item` , maar u wordt gevraagd het verwijderen te bevestigen als het item iets anders bevat.</span><span class="sxs-lookup"><span data-stu-id="4f835-139">You can remove contained items using `Remove-Item`, but you will be prompted to confirm the removal if the item contains anything else.</span></span> <span data-ttu-id="4f835-140">Als u bijvoorbeeld probeert de map te verwijderen `C:\temp\DeleteMe` die andere items bevat, vraagt Windows Power shell u om bevestiging voordat de map wordt verwijderd:</span><span class="sxs-lookup"><span data-stu-id="4f835-140">For example, if you attempt to delete the folder `C:\temp\DeleteMe` that contains other items, Windows PowerShell prompts you for confirmation before deleting the folder:</span></span>

```
Remove-Item -Path C:\temp\DeleteMe

Confirm
The item at C:\temp\DeleteMe has children and the Recurse parameter was not
specified. If you continue, all children will be removed with the item. Are you
sure you want to continue?
[Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help
(default is "Y"):
```

<span data-ttu-id="4f835-141">Als u niet voor elk opgenomen item wilt worden gevraagd, geeft u de para meter **recursief** op:</span><span class="sxs-lookup"><span data-stu-id="4f835-141">If you do not want to be prompted for each contained item, specify the **Recurse** parameter:</span></span>

```powershell
Remove-Item -Path C:\temp\DeleteMe -Recurse
```

## <a name="mapping-a-local-folder-as-a-drive"></a><span data-ttu-id="4f835-142">Een lokale map toewijzen als een station</span><span class="sxs-lookup"><span data-stu-id="4f835-142">Mapping a Local Folder as a drive</span></span>

<span data-ttu-id="4f835-143">U kunt ook een lokale map toewijzen met behulp van de `New-PSDrive` opdracht.</span><span class="sxs-lookup"><span data-stu-id="4f835-143">You can also map a local folder, using the `New-PSDrive` command.</span></span> <span data-ttu-id="4f835-144">Met de volgende opdracht maakt u een lokaal station `P:` in de map lokaal programma bestanden, alleen zichtbaar vanuit de Power shell-sessie:</span><span class="sxs-lookup"><span data-stu-id="4f835-144">The following command creates a local drive `P:` rooted in the local Program Files directory, visible only from the PowerShell session:</span></span>

```powershell
New-PSDrive -Name P -Root $env:ProgramFiles -PSProvider FileSystem
```

<span data-ttu-id="4f835-145">Net als bij netwerk stations zijn stations die zijn toegewezen in Windows Power shell, direct zichtbaar voor de Windows Power shell-shell.</span><span class="sxs-lookup"><span data-stu-id="4f835-145">Just as with network drives, drives mapped within Windows PowerShell are immediately visible to the Windows PowerShell shell.</span></span> <span data-ttu-id="4f835-146">Als u een toegewezen station zichtbaar wilt maken vanuit Verkenner, is de para meter `-Persist` vereist.</span><span class="sxs-lookup"><span data-stu-id="4f835-146">In order to create a mapped drive visible from File Explorer, the parameter `-Persist` is needed.</span></span> <span data-ttu-id="4f835-147">Er kunnen echter alleen externe paden worden gebruikt met persistent.</span><span class="sxs-lookup"><span data-stu-id="4f835-147">However, only remote paths can be used with Persist.</span></span>

## <a name="reading-a-text-file-into-an-array"></a><span data-ttu-id="4f835-148">Een tekst bestand in een matrix lezen</span><span class="sxs-lookup"><span data-stu-id="4f835-148">Reading a Text File into an Array</span></span>

<span data-ttu-id="4f835-149">Een van de meest voorkomende opslag indelingen voor tekst gegevens bevindt zich in een bestand met afzonderlijke regels behandeld als afzonderlijke gegevens elementen.</span><span class="sxs-lookup"><span data-stu-id="4f835-149">One of the more common storage formats for text data is in a file with separate lines treated as distinct data elements.</span></span> <span data-ttu-id="4f835-150">De `Get-Content` cmdlet kan worden gebruikt om een volledig bestand in één stap te lezen, zoals hier wordt weer gegeven:</span><span class="sxs-lookup"><span data-stu-id="4f835-150">The `Get-Content` cmdlet can be used to read an entire file in one step, as shown here:</span></span>

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

<span data-ttu-id="4f835-151">`Get-Content` behandelt de gegevens die uit het bestand zijn gelezen, al als een matrix, met één element per regel bestands inhoud.</span><span class="sxs-lookup"><span data-stu-id="4f835-151">`Get-Content` already treats the data read from the file as an array, with one element per line of file content.</span></span> <span data-ttu-id="4f835-152">U kunt dit controleren door de **lengte** van de geretourneerde inhoud te controleren:</span><span class="sxs-lookup"><span data-stu-id="4f835-152">You can confirm this by checking the **Length** of the returned content:</span></span>

```
PS> (Get-Content -Path C:\boot.ini).Length
6
```

<span data-ttu-id="4f835-153">Deze opdracht is vooral handig voor het rechtstreeks ophalen van lijsten met gegevens in Windows Power shell.</span><span class="sxs-lookup"><span data-stu-id="4f835-153">This command is most useful for getting lists of information into Windows PowerShell directly.</span></span> <span data-ttu-id="4f835-154">U kunt bijvoorbeeld een lijst met computer namen of IP-adressen opslaan in een bestand `C:\temp\domainMembers.txt` met één naam op elke regel van het bestand.</span><span class="sxs-lookup"><span data-stu-id="4f835-154">For example, you might store a list of computer names or IP addresses in a file `C:\temp\domainMembers.txt`, with one name on each line of the file.</span></span> <span data-ttu-id="4f835-155">U kunt gebruiken `Get-Content` om de bestands inhoud op te halen en deze in de variabele te plaatsen `$Computers` :</span><span class="sxs-lookup"><span data-stu-id="4f835-155">You can use `Get-Content` to retrieve the file contents and put them in the variable `$Computers`:</span></span>

```powershell
$Computers = Get-Content -Path C:\temp\DomainMembers.txt
```

<span data-ttu-id="4f835-156">`$Computers` is nu een matrix met een computer naam in elk-element.</span><span class="sxs-lookup"><span data-stu-id="4f835-156">`$Computers` is now an array containing a computer name in each element.</span></span>
