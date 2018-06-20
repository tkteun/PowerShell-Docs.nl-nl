---
ms.date: 06/05/2017
keywords: PowerShell-cmdlet
title: Items rechtstreeks bewerken
ms.assetid: 8cbd4867-917d-41ea-9ff0-b8e765509735
ms.openlocfilehash: 688f9194bd16793331325999c69e88df3e94c976
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 04/09/2018
ms.locfileid: "30953664"
---
# <a name="manipulating-items-directly"></a><span data-ttu-id="e4769-103">Items rechtstreeks bewerken</span><span class="sxs-lookup"><span data-stu-id="e4769-103">Manipulating Items Directly</span></span>

<span data-ttu-id="e4769-104">De elementen die u in Windows PowerShell-stations, zoals de bestanden en mappen in het bestand systeemstations en de sleutels in de Windows PowerShell register-stations ziet worden genoemd *items* in Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="e4769-104">The elements that you see in Windows PowerShell drives, such as the files and folders in the file system drives, and the registry keys in the Windows PowerShell registry drives, are called *items* in Windows PowerShell.</span></span> <span data-ttu-id="e4769-105">De cmdlets voor het werken met hen item hebben het zelfstandig naamwoord **Item** in hun naam.</span><span class="sxs-lookup"><span data-stu-id="e4769-105">The cmdlets for working with them item have the noun **Item** in their names.</span></span>

<span data-ttu-id="e4769-106">De uitvoer van de **Get-Command - zelfstandig naamwoord Item** opdracht geeft aan dat negen item Windows PowerShell-cmdlets.</span><span class="sxs-lookup"><span data-stu-id="e4769-106">The output of the **Get-Command -Noun Item** command shows that there are nine Windows PowerShell item cmdlets.</span></span>

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

### <a name="creating-new-items-new-item"></a><span data-ttu-id="e4769-107">Maken van nieuwe Items (Nieuw Item)</span><span class="sxs-lookup"><span data-stu-id="e4769-107">Creating New Items (New-Item)</span></span>

<span data-ttu-id="e4769-108">Gebruik voor het maken van een nieuw item in het bestandssysteem de **New Item** cmdlet.</span><span class="sxs-lookup"><span data-stu-id="e4769-108">To create a new item in the file system, use the **New-Item** cmdlet.</span></span> <span data-ttu-id="e4769-109">Bevatten de **pad** parameter met het pad naar het item en de **ItemType** parameter met de waarde 'file' of 'map'.</span><span class="sxs-lookup"><span data-stu-id="e4769-109">Include the **Path** parameter with path to the item, and the **ItemType** parameter with a value of "file" or "directory".</span></span>

<span data-ttu-id="e4769-110">Bijvoorbeeld, om een nieuwe map maken met de naam ' New.Directory"in C:\\Temp-directory, type:</span><span class="sxs-lookup"><span data-stu-id="e4769-110">For example, to create a new directory named "New.Directory"in the C:\\Temp directory,  type:</span></span>

```
PS> New-Item -Path c:\temp\New.Directory -ItemType Directory

    Directory: Microsoft.Windows PowerShell.Core\FileSystem::C:\temp

Mode                LastWriteTime     Length Name
----                -------------     ------ ----
d----        2006-05-18  11:29 AM            New.Directory
```

<span data-ttu-id="e4769-111">Voor het maken van een bestand, wijzig de waarde van de **ItemType** parameter 'file'.</span><span class="sxs-lookup"><span data-stu-id="e4769-111">To create a file, change the value of the **ItemType** parameter to "file".</span></span> <span data-ttu-id="e4769-112">Typ bijvoorbeeld de volgende opdracht voor het maken van een bestand met de naam 'bestand1.txt' in de map New.Directory:</span><span class="sxs-lookup"><span data-stu-id="e4769-112">For example, to create a file named "file1.txt" in the New.Directory directory, type:</span></span>

```
PS> New-Item -Path C:\temp\New.Directory\file1.txt -ItemType file

    Directory: Microsoft.Windows PowerShell.Core\FileSystem::C:\temp\New.Directory

Mode                LastWriteTime     Length Name
----                -------------     ------ ----
-a---        2006-05-18  11:44 AM          0 file1
```

<span data-ttu-id="e4769-113">U kunt dezelfde techniek gebruiken voor het maken van een nieuwe registersleutel.</span><span class="sxs-lookup"><span data-stu-id="e4769-113">You can use the same technique to create a new registry key.</span></span> <span data-ttu-id="e4769-114">Er is in feite een registersleutel gemakkelijker te maken, omdat het enige itemtype in het Windows-register een sleutel is.</span><span class="sxs-lookup"><span data-stu-id="e4769-114">In fact, a registry key is easier to create because the only item type in the Windows registry is a key.</span></span> <span data-ttu-id="e4769-115">(Registervermeldingen zijn item *eigenschappen*.) Typ bijvoorbeeld de volgende opdracht voor het maken van een sleutel met de naam '_Test' in de subsleutel CurrentVersion:</span><span class="sxs-lookup"><span data-stu-id="e4769-115">(Registry entries are item *properties*.) For example, to create a key named "_Test" in the CurrentVersion subkey, type:</span></span>

```
PS> New-Item -Path HKLM:\SOFTWARE\Microsoft\Windows\CurrentVersion_Test

   Hive: Microsoft.PowerShell.Core\Registry::HKEY_LOCAL_MACHINE\SOFTWARE\Micros
oft\Windows\CurrentVersion

SKC  VC Name                           Property
---  -- ----                           --------
  0   0 _Test                          {}
```

<span data-ttu-id="e4769-116">Wanneer een registerpad te typen, zorg ervoor dat u de dubbele punt (**:**) in de Windows PowerShell-station namen, HKLM: en HKCU:.</span><span class="sxs-lookup"><span data-stu-id="e4769-116">When typing a registry path, be sure to include the colon (**:**) in the Windows PowerShell drive names, HKLM: and HKCU:.</span></span> <span data-ttu-id="e4769-117">Zonder de dubbele punt, wordt de stationsnaam van het in het pad niet herkend door Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="e4769-117">Without the colon, Windows PowerShell does not recognize the drive name in the path.</span></span>

### <a name="why-registry-values-are-not-items"></a><span data-ttu-id="e4769-118">Waarom registerwaarden niet kunnen worden Items</span><span class="sxs-lookup"><span data-stu-id="e4769-118">Why Registry Values are not Items</span></span>

<span data-ttu-id="e4769-119">Wanneer u gebruikt de **Get-ChildItem** cmdlet vinden van de items in een registersleutel, wordt nooit werkelijke registervermeldingen of de waarden weergegeven.</span><span class="sxs-lookup"><span data-stu-id="e4769-119">When you use the **Get-ChildItem** cmdlet to find the items in a registry key, you will never see actual registry entries or their values.</span></span>

<span data-ttu-id="e4769-120">Bijvoorbeeld, de registersleutel **HKEY_LOCAL_MACHINE\\Software\\Microsoft\\Windows\\CurrentVersion\\uitvoeren** bevat meestal verschillende registervermeldingen die staan voor toepassingen die worden uitgevoerd wanneer het systeem wordt gestart.</span><span class="sxs-lookup"><span data-stu-id="e4769-120">For example, the registry key **HKEY_LOCAL_MACHINE\\Software\\Microsoft\\Windows\\CurrentVersion\\Run** usually contains several registry entries that represent applications that run when the system starts.</span></span>

<span data-ttu-id="e4769-121">Wanneer u echter gebruiken **Get-ChildItem** onderliggende items in de sleutel zoekt, ziet u alleen de **voor OptionalComponents** subsleutels van de sleutel:</span><span class="sxs-lookup"><span data-stu-id="e4769-121">However, when you use **Get-ChildItem** to look for child items in the key, all you will see is the **OptionalComponents** subkey of the key:</span></span>

```
PS> Get-ChildItem HKLM:\Software\Microsoft\Windows\CurrentVersion\Run

   Hive: Microsoft.PowerShell.Core\Registry::HKEY_LOCAL_MACHINE\Software\Micros
oft\Windows\CurrentVersion\Run
SKC  VC Name                           Property
---  -- ----                           --------
  3   0 OptionalComponents             {}
```

<span data-ttu-id="e4769-122">Hoewel het normaal zou handig om te behandelen registervermeldingen als items zijn, kunt u een pad naar een register-item kan niet opgeven op een manier die ervoor zorgt dat deze uniek is.</span><span class="sxs-lookup"><span data-stu-id="e4769-122">Although it would be convenient to treat registry entries as items, you cannot specify a path to a registry entry in a way that ensures that it is unique.</span></span> <span data-ttu-id="e4769-123">De notatie van het pad wordt geen onderscheid gemaakt tussen de registersubsleutel met de naam **uitvoeren** en de **(standaard)** register-item in de **uitvoeren** subsleutel.</span><span class="sxs-lookup"><span data-stu-id="e4769-123">The path notation does not distinguish between the registry subkey named **Run** and the **(Default)** registry entry in the **Run** subkey.</span></span> <span data-ttu-id="e4769-124">Bovendien, omdat de namen van vermeldingen register mag het backslash-teken (**\\**), als regsitry vermeldingen items, zou u kan de notatie van het pad niet gebruiken om te onderscheiden van een registervermelding met de naam  **Windows\\CurrentVersion\\uitvoeren** uit de subsleutel dat in dat pad bevindt zich.</span><span class="sxs-lookup"><span data-stu-id="e4769-124">Furthermore, because registry entry names can contain the backslash character (**\\**), if regsitry entries were items, then you could not use the path notation to distinguish a registry entry named **Windows\\CurrentVersion\\Run** from the subkey that is located in that path.</span></span>

### <a name="renaming-existing-items-rename-item"></a><span data-ttu-id="e4769-125">Naam van bestaande Items (Rename-Item) wijzigen</span><span class="sxs-lookup"><span data-stu-id="e4769-125">Renaming Existing Items (Rename-Item)</span></span>

<span data-ttu-id="e4769-126">De naam van een bestand of map wijzigen, gebruikt u de **Rename-Item** cmdlet.</span><span class="sxs-lookup"><span data-stu-id="e4769-126">To change the name of a file or folder, use the **Rename-Item** cmdlet.</span></span> <span data-ttu-id="e4769-127">De volgende opdracht wordt de naam van de **Bestand1.txt** van het bestand in **fileOne.txt**.</span><span class="sxs-lookup"><span data-stu-id="e4769-127">The following command changes the name of the **file1.txt** file to **fileOne.txt**.</span></span>

```powershell
Rename-Item -Path C:\temp\New.Directory\file1.txt fileOne.txt
```

<span data-ttu-id="e4769-128">De **Rename-Item** cmdlet kan de naam van een bestand of map wijzigen, maar het kan een item niet verplaatsen.</span><span class="sxs-lookup"><span data-stu-id="e4769-128">The **Rename-Item** cmdlet can change the name of a file or a folder, but it cannot move an item.</span></span> <span data-ttu-id="e4769-129">De volgende opdracht mislukt, omdat deze probeert het bestand van de map New.Directory verplaatsen naar de map Temp.</span><span class="sxs-lookup"><span data-stu-id="e4769-129">The following command fails because it attempts to move the file from the New.Directory directory to the Temp directory.</span></span>

```
PS> Rename-Item -Path C:\temp\New.Directory\fileOne.txt c:\temp\fileOne.txt
Rename-Item : Cannot rename because the target specified is not a path.
At line:1 char:12
+ Rename-Item  <<<< -Path C:\temp\New.Directory\fileOne c:\temp\fileOne.txt
```

### <a name="moving-items-move-item"></a><span data-ttu-id="e4769-130">Verplaatsen van Items (Item verplaatsen)</span><span class="sxs-lookup"><span data-stu-id="e4769-130">Moving Items (Move-Item)</span></span>

<span data-ttu-id="e4769-131">Als u een bestand of map, gebruikt u de **Item verplaatsen** cmdlet.</span><span class="sxs-lookup"><span data-stu-id="e4769-131">To move a file or folder, use the **Move-Item** cmdlet.</span></span>

<span data-ttu-id="e4769-132">Bijvoorbeeld de map New.Directory in de volgende opdracht wordt verplaatst van de C:\\tijdelijke map naar de hoofdmap van station C:.</span><span class="sxs-lookup"><span data-stu-id="e4769-132">For example, the following command moves the New.Directory directory from the C:\\temp directory to the root of the C: drive.</span></span> <span data-ttu-id="e4769-133">Om te verifiëren dat het item is verplaatst, omvatten de **PassThru** parameter van de **Item verplaatsen** cmdlet.</span><span class="sxs-lookup"><span data-stu-id="e4769-133">To verify that the item was moved, include the **PassThru** parameter of the **Move-Item** cmdlet.</span></span> <span data-ttu-id="e4769-134">Zonder **Passthru**, wordt de **Item verplaatsen** cmdlet geeft geen resultaten weer.</span><span class="sxs-lookup"><span data-stu-id="e4769-134">Without **Passthru**, the **Move-Item** cmdlet does not display any results.</span></span>

```
PS> Move-Item -Path C:\temp\New.Directory -Destination C:\ -PassThru

    Directory: Microsoft.Windows PowerShell.Core\FileSystem::C:\

Mode                LastWriteTime     Length Name
----                -------------     ------ ----
d----        2006-05-18  12:14 PM            New.Directory
```

### <a name="copying-items-copy-item"></a><span data-ttu-id="e4769-135">Kopiëren van Items (Copy-Item)</span><span class="sxs-lookup"><span data-stu-id="e4769-135">Copying Items (Copy-Item)</span></span>

<span data-ttu-id="e4769-136">Als u bekend met de kopieerbewerkingen in andere houders bent, vindt u mogelijk het gedrag van de **Copy-Item** cmdlet in Windows PowerShell om te worden ongebruikelijke.</span><span class="sxs-lookup"><span data-stu-id="e4769-136">If you are familiar with the copy operations in other shells, you might find the behavior of the **Copy-Item** cmdlet in Windows PowerShell to be unusual.</span></span> <span data-ttu-id="e4769-137">Wanneer u een item van de ene locatie naar een andere kopieert, kopieert Copy-Item niet de inhoud ervan standaard.</span><span class="sxs-lookup"><span data-stu-id="e4769-137">When you copy an item from one location to another, Copy-Item does not copy its contents by default.</span></span>

<span data-ttu-id="e4769-138">Bijvoorbeeld, als u kopieert de **New.Directory** map uit het station C: naar station C:\\tijdelijke map, de opdracht is geslaagd, maar de bestanden in de map New.Directory zijn niet gekopieerd.</span><span class="sxs-lookup"><span data-stu-id="e4769-138">For example, if you copy the **New.Directory** directory from the C: drive to the C:\\temp directory, the command succeeds, but the files in the New.Directory directory are not copied.</span></span>

```powershell
Copy-Item -Path C:\New.Directory -Destination C:\temp
```

<span data-ttu-id="e4769-139">Als u de inhoud van weergeven **C:\\temp\\New.Directory**, vindt u bevat geen bestanden:</span><span class="sxs-lookup"><span data-stu-id="e4769-139">If you display the contents of **C:\\temp\\New.Directory**, you will find that it contains no files:</span></span>

```
PS> Get-ChildItem -Path C:\temp\New.Directory
PS>
```

<span data-ttu-id="e4769-140">Waarom heeft niet de **Copy-Item** cmdlet Kopieer de inhoud naar de nieuwe locatie?</span><span class="sxs-lookup"><span data-stu-id="e4769-140">Why doesn't the **Copy-Item** cmdlet copy the contents to the new location?</span></span>

<span data-ttu-id="e4769-141">De **Copy-Item** cmdlet is ontworpen om te worden algemene; het is niet alleen voor het kopiëren van bestanden en mappen.</span><span class="sxs-lookup"><span data-stu-id="e4769-141">The **Copy-Item** cmdlet was designed to be generic; it is not just for copying files and folders.</span></span> <span data-ttu-id="e4769-142">Bovendien zelfs bij het kopiëren van bestanden en mappen, raadzaam om alleen de container en niet de items erin te kopiëren.</span><span class="sxs-lookup"><span data-stu-id="e4769-142">Also, even when copying files and folders, you might want to copy only the container and not the items within it.</span></span>

<span data-ttu-id="e4769-143">Alle van de inhoud van een map wilt kopiëren, omvatten de **Recurse** parameter van de **Copy-Item** cmdlet in de opdracht.</span><span class="sxs-lookup"><span data-stu-id="e4769-143">To copy all of the contents of a folder, include the **Recurse** parameter of the **Copy-Item** cmdlet in the command.</span></span> <span data-ttu-id="e4769-144">Als u de map zonder de inhoud al hebt gekopieerd, voegt u de **Force** parameter, zodat u kunt de lege map overschrijven.</span><span class="sxs-lookup"><span data-stu-id="e4769-144">If you have already copied the directory without its contents, add the **Force** parameter, which allows you to overwrite the empty folder.</span></span>

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

### <a name="deleting-items-remove-item"></a><span data-ttu-id="e4769-145">Verwijderen van Items (Item verwijderen)</span><span class="sxs-lookup"><span data-stu-id="e4769-145">Deleting Items (Remove-Item)</span></span>

<span data-ttu-id="e4769-146">Als u wilt verwijderen van bestanden en mappen, gebruiken de **Item verwijderen** cmdlet.</span><span class="sxs-lookup"><span data-stu-id="e4769-146">To delete files and folders, use the **Remove-Item** cmdlet.</span></span> <span data-ttu-id="e4769-147">Windows PowerShell-cmdlets, zoals **Item verwijderen**, die significante kunt maken, niet ongedaan worden gemaakt wijzigingen vaak om bevestiging wordt gevraagd wanneer u de opdrachten invoert.</span><span class="sxs-lookup"><span data-stu-id="e4769-147">Windows PowerShell cmdlets, such as **Remove-Item**, that can make significant, irreversible changes will often prompt for confirmation when you enter its commands.</span></span> <span data-ttu-id="e4769-148">Bijvoorbeeld, als u probeert te verwijderen de **New.Directory** map, wordt u gevraagd om te bevestigen dat de opdracht, omdat de map bestanden bevat:</span><span class="sxs-lookup"><span data-stu-id="e4769-148">For example, if you try to remove the **New.Directory** folder, you will be prompted to confirm the command, because the folder contains files:</span></span>

```
PS> Remove-Item C:\New.Directory

Confirm
The item at C:\temp\New.Directory has children and the -recurse parameter was not
specified. If you continue, all children will be removed with the item. Are you
 sure you want to continue?
[Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help
(default is "Y"):
```

<span data-ttu-id="e4769-149">Omdat **Ja** is het standaardantwoord verwijderen van de map en de bijbehorende bestanden, drukt u op de **Enter** sleutel.</span><span class="sxs-lookup"><span data-stu-id="e4769-149">Because **Yes** is the default response, to delete the folder and its files, press the **Enter** key.</span></span> <span data-ttu-id="e4769-150">U kunt de map zonder bevestiging verwijderen met de **-Recurse** parameter.</span><span class="sxs-lookup"><span data-stu-id="e4769-150">To remove the folder without confirming, use the **-Recurse** parameter.</span></span>

```powershell
Remove-Item C:\temp\New.Directory -Recurse
```

### <a name="executing-items-invoke-item"></a><span data-ttu-id="e4769-151">Uitvoeren van Items (Invoke-Item)</span><span class="sxs-lookup"><span data-stu-id="e4769-151">Executing Items (Invoke-Item)</span></span>

<span data-ttu-id="e4769-152">Windows PowerShell maakt gebruik van de **Invoke-Item** cmdlet een standaardactie uitvoeren voor een bestand of map.</span><span class="sxs-lookup"><span data-stu-id="e4769-152">Windows PowerShell uses the **Invoke-Item** cmdlet to perform a default action for a file or folder.</span></span> <span data-ttu-id="e4769-153">Deze standaardactie wordt bepaald door de handler standaard toepassing in het register. het effect is hetzelfde als wanneer u dubbelklikt op het item in Windows Verkenner.</span><span class="sxs-lookup"><span data-stu-id="e4769-153">This default action is determined by the default application handler in the registry; the effect is the same as if you double-click the item in File Explorer.</span></span>

<span data-ttu-id="e4769-154">Stel bijvoorbeeld dat u de volgende opdracht uitvoeren:</span><span class="sxs-lookup"><span data-stu-id="e4769-154">For example, suppose you run the following command:</span></span>

```powershell
Invoke-Item C:\WINDOWS
```

<span data-ttu-id="e4769-155">Een Explorer-venster dat in C: bevindt zich\\Windows wordt weergegeven, net als de C: had dubbelklikken\\Windows-map.</span><span class="sxs-lookup"><span data-stu-id="e4769-155">An Explorer window that is located in C:\\Windows appears, just as if you had double-clicked the C:\\Windows folder.</span></span>

<span data-ttu-id="e4769-156">Als u de **Boot.ini** bestand op een systeem ouder dan Windows Vista:</span><span class="sxs-lookup"><span data-stu-id="e4769-156">If you invoke the **Boot.ini** file on a system prior to Windows Vista:</span></span>

```powershell
Invoke-Item C:\boot.ini
```

<span data-ttu-id="e4769-157">Als het type INI-bestand gekoppeld aan Kladblok is, is het boot.ini-bestand wordt geopend in Kladblok.</span><span class="sxs-lookup"><span data-stu-id="e4769-157">If the .ini file type is associated with Notepad, the boot.ini file opens in Notepad.</span></span>