---
ms.date: 06/05/2017
keywords: Power shell, cmdlet
title: Items rechtstreeks bewerken
ms.openlocfilehash: 50aed569cf6b876297abe3cf1544eba70f6279ce
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 12/05/2019
ms.locfileid: "67030127"
---
# <a name="manipulating-items-directly"></a><span data-ttu-id="84430-103">Items rechtstreeks bewerken</span><span class="sxs-lookup"><span data-stu-id="84430-103">Manipulating Items Directly</span></span>

<span data-ttu-id="84430-104">De elementen die u ziet in Windows Power Shell-stations, zoals de bestanden en mappen in de bestandssysteem stations en de register sleutels in de Windows Power shell-register stations, worden *items* genoemd in Windows Power shell.</span><span class="sxs-lookup"><span data-stu-id="84430-104">The elements that you see in Windows PowerShell drives, such as the files and folders in the file system drives, and the registry keys in the Windows PowerShell registry drives, are called *items* in Windows PowerShell.</span></span> <span data-ttu-id="84430-105">De cmdlets voor het werken met deze items hebben het zelfstandige naam **item** .</span><span class="sxs-lookup"><span data-stu-id="84430-105">The cmdlets for working with them item have the noun **Item** in their names.</span></span>

<span data-ttu-id="84430-106">De uitvoer van de opdracht **Get-opdracht-item** van het zelfstandig naam woord laat zien dat er negen Windows Power shell-cmdlets voor items zijn.</span><span class="sxs-lookup"><span data-stu-id="84430-106">The output of the **Get-Command -Noun Item** command shows that there are nine Windows PowerShell item cmdlets.</span></span>

```
PS> Get-Command -Noun Item

CommandType     Name                            Definition
-----------     ----                            ----------
Cmdlet          Clear-Item                      Clear-Item [-Path] <String[]...
Cmdlet          Copy-Item                       Copy-Item [-Path] <String[]>...
Cmdlet          Get-Item                        Get-Item [-Path] <String[]> ...
Cmdlet          Invoke-Item                     Invoke-Item [-Path] <String[...
Cmdlet          Move-Item                       Move-Item [-Path] <String[]>...
Cmdlet          New-Item                        New-Item [-Path] <String[]> ...
Cmdlet          Remove-Item                     Remove-Item [-Path] <String[...
Cmdlet          Rename-Item                     Rename-Item [-Path] <String>...
Cmdlet          Set-Item                        Set-Item [-Path] <String[]> ...
```

## <a name="creating-new-items-new-item"></a><span data-ttu-id="84430-107">Nieuwe items maken (nieuw item)</span><span class="sxs-lookup"><span data-stu-id="84430-107">Creating New Items (New-Item)</span></span>

<span data-ttu-id="84430-108">Gebruik de cmdlet **New-item** om een nieuw item in het bestands systeem te maken.</span><span class="sxs-lookup"><span data-stu-id="84430-108">To create a new item in the file system, use the **New-Item** cmdlet.</span></span> <span data-ttu-id="84430-109">Neem de para meter **Path** op met het pad naar het item en de **item** type-para meter met de waarde "file" of "directory".</span><span class="sxs-lookup"><span data-stu-id="84430-109">Include the **Path** parameter with path to the item, and the **ItemType** parameter with a value of "file" or "directory".</span></span>

<span data-ttu-id="84430-110">Als u bijvoorbeeld een nieuwe map met de naam ' New. Directory ' wilt maken in de map C:\\Temp, typt u:</span><span class="sxs-lookup"><span data-stu-id="84430-110">For example, to create a new directory named "New.Directory"in the C:\\Temp directory,  type:</span></span>

```
PS> New-Item -Path c:\temp\New.Directory -ItemType Directory

    Directory: Microsoft.Windows PowerShell.Core\FileSystem::C:\temp

Mode                LastWriteTime     Length Name
----                -------------     ------ ----
d----        2006-05-18  11:29 AM            New.Directory
```

<span data-ttu-id="84430-111">Als u een bestand wilt maken, wijzigt u de waarde van de para meter **item** type in "bestand".</span><span class="sxs-lookup"><span data-stu-id="84430-111">To create a file, change the value of the **ItemType** parameter to "file".</span></span> <span data-ttu-id="84430-112">Als u bijvoorbeeld een bestand met de naam ' bestand1. txt ' in de nieuwe map wilt maken, typt u:</span><span class="sxs-lookup"><span data-stu-id="84430-112">For example, to create a file named "file1.txt" in the New.Directory directory, type:</span></span>

```
PS> New-Item -Path C:\temp\New.Directory\file1.txt -ItemType file

    Directory: Microsoft.Windows PowerShell.Core\FileSystem::C:\temp\New.Directory

Mode                LastWriteTime     Length Name
----                -------------     ------ ----
-a---        2006-05-18  11:44 AM          0 file1
```

<span data-ttu-id="84430-113">U kunt dezelfde techniek gebruiken om een nieuwe register sleutel te maken.</span><span class="sxs-lookup"><span data-stu-id="84430-113">You can use the same technique to create a new registry key.</span></span> <span data-ttu-id="84430-114">Een register sleutel is eigenlijk eenvoudiger te maken, omdat het enige item type in het Windows-REGI ster een sleutel is.</span><span class="sxs-lookup"><span data-stu-id="84430-114">In fact, a registry key is easier to create because the only item type in the Windows registry is a key.</span></span> <span data-ttu-id="84430-115">(Register vermeldingen zijn item *Eigenschappen*.) Als u bijvoorbeeld een sleutel met de naam ' _Test ' wilt maken in de subsleutel CurrentVersion, typt u:</span><span class="sxs-lookup"><span data-stu-id="84430-115">(Registry entries are item *properties*.) For example, to create a key named "_Test" in the CurrentVersion subkey, type:</span></span>

```
PS> New-Item -Path HKLM:\SOFTWARE\Microsoft\Windows\CurrentVersion_Test

   Hive: Microsoft.PowerShell.Core\Registry::HKEY_LOCAL_MACHINE\SOFTWARE\Micros
oft\Windows\CurrentVersion

SKC  VC Name                           Property
---  -- ----                           --------
  0   0 _Test                          {}
```

<span data-ttu-id="84430-116">Wanneer u een registerpad typt, moet u de dubbele punt ( **:** ) in de namen van Windows Power Shell-stations, HKLM: en HKCU: toevoegen.</span><span class="sxs-lookup"><span data-stu-id="84430-116">When typing a registry path, be sure to include the colon (**:**) in the Windows PowerShell drive names, HKLM: and HKCU:.</span></span> <span data-ttu-id="84430-117">Zonder de dubbele punt herkent Windows Power shell de naam van het station niet in het pad.</span><span class="sxs-lookup"><span data-stu-id="84430-117">Without the colon, Windows PowerShell does not recognize the drive name in the path.</span></span>

## <a name="why-registry-values-are-not-items"></a><span data-ttu-id="84430-118">Waarom register waarden geen items zijn</span><span class="sxs-lookup"><span data-stu-id="84430-118">Why Registry Values are not Items</span></span>

<span data-ttu-id="84430-119">Wanneer u de cmdlet **Get-Child item** gebruikt om de items in een register sleutel te vinden, zult u nooit de werkelijke Register vermeldingen of hun waarden zien.</span><span class="sxs-lookup"><span data-stu-id="84430-119">When you use the **Get-ChildItem** cmdlet to find the items in a registry key, you will never see actual registry entries or their values.</span></span>

<span data-ttu-id="84430-120">De register sleutel **HKEY_LOCAL_MACHINE\\Software\\micro soft\\Windows\\CurrentVersion\\run** bevat doorgaans diverse register vermeldingen die toepassingen vertegenwoordigen die worden uitgevoerd wanneer het systeem wordt gestart.</span><span class="sxs-lookup"><span data-stu-id="84430-120">For example, the registry key **HKEY_LOCAL_MACHINE\\Software\\Microsoft\\Windows\\CurrentVersion\\Run** usually contains several registry entries that represent applications that run when the system starts.</span></span>

<span data-ttu-id="84430-121">Als u echter **Get-Child item** gebruikt om te zoeken naar onderliggende items in de sleutel, ziet u de subsleutel **OptionalComponents** van de sleutel:</span><span class="sxs-lookup"><span data-stu-id="84430-121">However, when you use **Get-ChildItem** to look for child items in the key, all you will see is the **OptionalComponents** subkey of the key:</span></span>

```
PS> Get-ChildItem HKLM:\Software\Microsoft\Windows\CurrentVersion\Run

   Hive: Microsoft.PowerShell.Core\Registry::HKEY_LOCAL_MACHINE\Software\Micros
oft\Windows\CurrentVersion\Run
SKC  VC Name                           Property
---  -- ----                           --------
  3   0 OptionalComponents             {}
```

<span data-ttu-id="84430-122">Hoewel het handig is om Register vermeldingen als items te behandelen, kunt u geen pad naar een register vermelding opgeven op een manier die ervoor zorgt dat deze uniek is.</span><span class="sxs-lookup"><span data-stu-id="84430-122">Although it would be convenient to treat registry entries as items, you cannot specify a path to a registry entry in a way that ensures that it is unique.</span></span> <span data-ttu-id="84430-123">De pad-notatie maakt geen onderscheid tussen de registersubsleutel **Run** en de **(standaard)** register vermelding in de **Run** -subsleutel.</span><span class="sxs-lookup"><span data-stu-id="84430-123">The path notation does not distinguish between the registry subkey named **Run** and the **(Default)** registry entry in the **Run** subkey.</span></span> <span data-ttu-id="84430-124">Omdat Register vermeldingen echter de back slash-teken ( **\\** ) kunnen bevatten, kunt u, als register items items zijn, de pad-notatie niet gebruiken om onderscheid te maken tussen een register vermelding met de naam **Windows\\CurrentVersion\\worden uitgevoerd** vanuit de subsleutel die zich in dat pad bevindt.</span><span class="sxs-lookup"><span data-stu-id="84430-124">Furthermore, because registry entry names can contain the backslash character (**\\**), if registry entries were items, then you could not use the path notation to distinguish a registry entry named **Windows\\CurrentVersion\\Run** from the subkey that is located in that path.</span></span>

## <a name="renaming-existing-items-rename-item"></a><span data-ttu-id="84430-125">De naam van bestaande items wijzigen (naam wijzigen-item)</span><span class="sxs-lookup"><span data-stu-id="84430-125">Renaming Existing Items (Rename-Item)</span></span>

<span data-ttu-id="84430-126">Als u de naam van een bestand of map wilt wijzigen, gebruikt u de cmdlet **Rename-item** .</span><span class="sxs-lookup"><span data-stu-id="84430-126">To change the name of a file or folder, use the **Rename-Item** cmdlet.</span></span> <span data-ttu-id="84430-127">Met de volgende opdracht wordt de naam van het bestand **bestand1. txt** gewijzigd in **fileOne. txt**.</span><span class="sxs-lookup"><span data-stu-id="84430-127">The following command changes the name of the **file1.txt** file to **fileOne.txt**.</span></span>

```powershell
Rename-Item -Path C:\temp\New.Directory\file1.txt fileOne.txt
```

<span data-ttu-id="84430-128">De cmdlet **Rename-item** kan de naam van een bestand of map wijzigen, maar een item kan niet worden verplaatst.</span><span class="sxs-lookup"><span data-stu-id="84430-128">The **Rename-Item** cmdlet can change the name of a file or a folder, but it cannot move an item.</span></span> <span data-ttu-id="84430-129">De volgende opdracht mislukt omdat er wordt geprobeerd het bestand te verplaatsen van de nieuwe map. Directory naar de map Temp.</span><span class="sxs-lookup"><span data-stu-id="84430-129">The following command fails because it attempts to move the file from the New.Directory directory to the Temp directory.</span></span>

```
PS> Rename-Item -Path C:\temp\New.Directory\fileOne.txt c:\temp\fileOne.txt
Rename-Item : Cannot rename because the target specified is not a path.
At line:1 char:12
+ Rename-Item  <<<< -Path C:\temp\New.Directory\fileOne c:\temp\fileOne.txt
```

## <a name="moving-items-move-item"></a><span data-ttu-id="84430-130">Items verplaatsen (verplaatsen-item)</span><span class="sxs-lookup"><span data-stu-id="84430-130">Moving Items (Move-Item)</span></span>

<span data-ttu-id="84430-131">Als u een bestand of map wilt verplaatsen, gebruikt u de cmdlet **Move-item** .</span><span class="sxs-lookup"><span data-stu-id="84430-131">To move a file or folder, use the **Move-Item** cmdlet.</span></span>

<span data-ttu-id="84430-132">Met de volgende opdracht wordt bijvoorbeeld de nieuwe Directory Directory verplaatst van de map C:\\Temp naar de hoofdmap van station C:.</span><span class="sxs-lookup"><span data-stu-id="84430-132">For example, the following command moves the New.Directory directory from the C:\\temp directory to the root of the C: drive.</span></span> <span data-ttu-id="84430-133">Als u wilt controleren of het item is verplaatst, neemt u de para meter **PassThru** van de cmdlet **Move-item** op.</span><span class="sxs-lookup"><span data-stu-id="84430-133">To verify that the item was moved, include the **PassThru** parameter of the **Move-Item** cmdlet.</span></span> <span data-ttu-id="84430-134">Zonder **PassThru**worden met de cmdlet **Move-item** geen resultaten weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="84430-134">Without **Passthru**, the **Move-Item** cmdlet does not display any results.</span></span>

```
PS> Move-Item -Path C:\temp\New.Directory -Destination C:\ -PassThru

    Directory: Microsoft.Windows PowerShell.Core\FileSystem::C:\

Mode                LastWriteTime     Length Name
----                -------------     ------ ----
d----        2006-05-18  12:14 PM            New.Directory
```

## <a name="copying-items-copy-item"></a><span data-ttu-id="84430-135">Items kopiëren (kopiëren-item)</span><span class="sxs-lookup"><span data-stu-id="84430-135">Copying Items (Copy-Item)</span></span>

<span data-ttu-id="84430-136">Als u bekend bent met de Kopieer bewerkingen in andere shells, kunt u het gedrag van de cmdlet **copy-item** in Windows Power shell ongebruikelijk vinden.</span><span class="sxs-lookup"><span data-stu-id="84430-136">If you are familiar with the copy operations in other shells, you might find the behavior of the **Copy-Item** cmdlet in Windows PowerShell to be unusual.</span></span> <span data-ttu-id="84430-137">Wanneer u een item van de ene locatie naar een andere kopieert, wordt de inhoud niet standaard gekopieerd.</span><span class="sxs-lookup"><span data-stu-id="84430-137">When you copy an item from one location to another, Copy-Item does not copy its contents by default.</span></span>

<span data-ttu-id="84430-138">Als u bijvoorbeeld de map **New. Directory** van station c: kopieert naar de map c:\\Temp, is de opdracht geslaagd, maar de bestanden in de nieuwe directory-map worden niet gekopieerd.</span><span class="sxs-lookup"><span data-stu-id="84430-138">For example, if you copy the **New.Directory** directory from the C: drive to the C:\\temp directory, the command succeeds, but the files in the New.Directory directory are not copied.</span></span>

```powershell
Copy-Item -Path C:\New.Directory -Destination C:\temp
```

<span data-ttu-id="84430-139">Als u de inhoud van **C:\\temp\\New. Directory**weergeeft, ziet u dat deze geen bestanden bevat:</span><span class="sxs-lookup"><span data-stu-id="84430-139">If you display the contents of **C:\\temp\\New.Directory**, you will find that it contains no files:</span></span>

```
PS> Get-ChildItem -Path C:\temp\New.Directory
PS>
```

<span data-ttu-id="84430-140">Waarom kopieert de cmdlet **copy-item** de inhoud niet naar de nieuwe locatie?</span><span class="sxs-lookup"><span data-stu-id="84430-140">Why doesn't the **Copy-Item** cmdlet copy the contents to the new location?</span></span>

<span data-ttu-id="84430-141">De cmdlet **copy-item** is ontworpen als algemeen; het is niet alleen bedoeld voor het kopiëren van bestanden en mappen.</span><span class="sxs-lookup"><span data-stu-id="84430-141">The **Copy-Item** cmdlet was designed to be generic; it is not just for copying files and folders.</span></span> <span data-ttu-id="84430-142">Ook als u bestanden en mappen kopieert, wilt u misschien alleen de container kopiëren en niet de items hierin.</span><span class="sxs-lookup"><span data-stu-id="84430-142">Also, even when copying files and folders, you might want to copy only the container and not the items within it.</span></span>

<span data-ttu-id="84430-143">Als u alle inhoud van een map wilt kopiëren, neemt u de para meter **recursieve** van de cmdlet **copy-item** op in de opdracht.</span><span class="sxs-lookup"><span data-stu-id="84430-143">To copy all of the contents of a folder, include the **Recurse** parameter of the **Copy-Item** cmdlet in the command.</span></span> <span data-ttu-id="84430-144">Als u de map al hebt gekopieerd zonder de inhoud, voegt u de para meter **Force** toe, waarmee u de lege map kunt overschrijven.</span><span class="sxs-lookup"><span data-stu-id="84430-144">If you have already copied the directory without its contents, add the **Force** parameter, which allows you to overwrite the empty folder.</span></span>

```
PS> Copy-Item -Path C:\New.Directory -Destination C:\temp -Recurse -Force -Passthru

    Directory: Microsoft.Windows PowerShell.Core\FileSystem::C:\temp

Mode                LastWriteTime     Length Name
----                -------------     ------ ----
d----        2006-05-18   1:53 PM            New.Directory

    Directory: Microsoft.Windows PowerShell.Core\FileSystem::C:\temp\New.Directory

Mode                LastWriteTime     Length Name
----                -------------     ------ ----
-a---        2006-05-18  11:44 AM          0 file1
```

## <a name="deleting-items-remove-item"></a><span data-ttu-id="84430-145">Items verwijderen (verwijderen-item)</span><span class="sxs-lookup"><span data-stu-id="84430-145">Deleting Items (Remove-Item)</span></span>

<span data-ttu-id="84430-146">Als u bestanden en mappen wilt verwijderen, gebruikt u de cmdlet **Remove-item** .</span><span class="sxs-lookup"><span data-stu-id="84430-146">To delete files and folders, use the **Remove-Item** cmdlet.</span></span> <span data-ttu-id="84430-147">Windows Power shell-cmdlets, zoals **Remove-item**, die aanzienlijke, onherstelbare wijzigingen kunnen aanbrengen, worden vaak gevraagd om bevestiging wanneer u de opdrachten opgeeft.</span><span class="sxs-lookup"><span data-stu-id="84430-147">Windows PowerShell cmdlets, such as **Remove-Item**, that can make significant, irreversible changes will often prompt for confirmation when you enter its commands.</span></span> <span data-ttu-id="84430-148">Als u bijvoorbeeld probeert de **nieuwe map.** map te verwijderen, wordt u gevraagd om de opdracht te bevestigen, omdat de map bestanden bevat:</span><span class="sxs-lookup"><span data-stu-id="84430-148">For example, if you try to remove the **New.Directory** folder, you will be prompted to confirm the command, because the folder contains files:</span></span>

```
PS> Remove-Item C:\New.Directory

Confirm
The item at C:\temp\New.Directory has children and the -recurse parameter was not
specified. If you continue, all children will be removed with the item. Are you
 sure you want to continue?
[Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help
(default is "Y"):
```

<span data-ttu-id="84430-149">Omdat **Ja** de standaard reactie is, kunt u de map en de bijbehorende bestanden verwijderen door op **Enter** te drukken.</span><span class="sxs-lookup"><span data-stu-id="84430-149">Because **Yes** is the default response, to delete the folder and its files, press the **Enter** key.</span></span> <span data-ttu-id="84430-150">Als u de map wilt verwijderen zonder te bevestigen, gebruikt u de para meter **-recursief** .</span><span class="sxs-lookup"><span data-stu-id="84430-150">To remove the folder without confirming, use the **-Recurse** parameter.</span></span>

```powershell
Remove-Item C:\temp\New.Directory -Recurse
```

## <a name="executing-items-invoke-item"></a><span data-ttu-id="84430-151">Items uitvoeren (invoke-item)</span><span class="sxs-lookup"><span data-stu-id="84430-151">Executing Items (Invoke-Item)</span></span>

<span data-ttu-id="84430-152">Windows Power shell gebruikt de cmdlet **invoke-item** om een standaard actie uit te voeren voor een bestand of map.</span><span class="sxs-lookup"><span data-stu-id="84430-152">Windows PowerShell uses the **Invoke-Item** cmdlet to perform a default action for a file or folder.</span></span> <span data-ttu-id="84430-153">Deze standaard actie wordt bepaald door de standaard toepassings-handler in het REGI ster. het effect is hetzelfde als wanneer u dubbelklikt op het item in Verkenner.</span><span class="sxs-lookup"><span data-stu-id="84430-153">This default action is determined by the default application handler in the registry; the effect is the same as if you double-click the item in File Explorer.</span></span>

<span data-ttu-id="84430-154">Stel bijvoorbeeld dat u de volgende opdracht uitvoert:</span><span class="sxs-lookup"><span data-stu-id="84430-154">For example, suppose you run the following command:</span></span>

```powershell
Invoke-Item C:\WINDOWS
```

<span data-ttu-id="84430-155">Een Verkenner-venster dat zich bevindt in C:\\Windows wordt weer gegeven, net zoals als u op de map C:\\Windows hebt gedubbelklikt.</span><span class="sxs-lookup"><span data-stu-id="84430-155">An Explorer window that is located in C:\\Windows appears, just as if you had double-clicked the C:\\Windows folder.</span></span>

<span data-ttu-id="84430-156">Als u het bestand **boot. ini** aanroept op een systeem vóór Windows Vista:</span><span class="sxs-lookup"><span data-stu-id="84430-156">If you invoke the **Boot.ini** file on a system prior to Windows Vista:</span></span>

```powershell
Invoke-Item C:\boot.ini
```

<span data-ttu-id="84430-157">Als het ini-bestands type is gekoppeld aan Klad blok, wordt het bestand Boot. ini geopend in Klad blok.</span><span class="sxs-lookup"><span data-stu-id="84430-157">If the .ini file type is associated with Notepad, the boot.ini file opens in Notepad.</span></span>
