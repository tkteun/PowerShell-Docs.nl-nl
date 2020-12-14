---
description: Bestandssysteem
Locale: en-US
ms.date: 11/13/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_filesystem_provider?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Bestandssysteem provider
ms.openlocfilehash: cfe074475cc1304243dfd4b2245e4eec44c25244
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 11/17/2020
ms.locfileid: "94705786"
---
# <a name="filesystem-provider"></a><span data-ttu-id="11f9a-103">Bestandssysteem provider</span><span class="sxs-lookup"><span data-stu-id="11f9a-103">FileSystem provider</span></span>

## <a name="provider-name"></a><span data-ttu-id="11f9a-104">Provider naam</span><span class="sxs-lookup"><span data-stu-id="11f9a-104">Provider name</span></span>

<span data-ttu-id="11f9a-105">Bestandssysteem</span><span class="sxs-lookup"><span data-stu-id="11f9a-105">FileSystem</span></span>

## <a name="drives"></a><span data-ttu-id="11f9a-106">Aandrijfeenheden</span><span class="sxs-lookup"><span data-stu-id="11f9a-106">Drives</span></span>

<span data-ttu-id="11f9a-107">`C:`, `D:` ...</span><span class="sxs-lookup"><span data-stu-id="11f9a-107">`C:`, `D:` ...</span></span>

## <a name="capabilities"></a><span data-ttu-id="11f9a-108">Functies</span><span class="sxs-lookup"><span data-stu-id="11f9a-108">Capabilities</span></span>

<span data-ttu-id="11f9a-109">**Filteren**, **ShouldProcess**</span><span class="sxs-lookup"><span data-stu-id="11f9a-109">**Filter**, **ShouldProcess**</span></span>

## <a name="short-description"></a><span data-ttu-id="11f9a-110">Korte beschrijving</span><span class="sxs-lookup"><span data-stu-id="11f9a-110">Short description</span></span>

<span data-ttu-id="11f9a-111">Biedt toegang tot bestanden en mappen.</span><span class="sxs-lookup"><span data-stu-id="11f9a-111">Provides access to files and directories.</span></span>

## <a name="detailed-description"></a><span data-ttu-id="11f9a-112">Gedetailleerde beschrijving</span><span class="sxs-lookup"><span data-stu-id="11f9a-112">Detailed description</span></span>

<span data-ttu-id="11f9a-113">Met de Power shell- **bestandssysteem** provider kunt u bestanden en mappen in Power shell ophalen, toevoegen, wijzigen, wissen en verwijderen.</span><span class="sxs-lookup"><span data-stu-id="11f9a-113">The PowerShell **FileSystem** provider lets you get, add, change, clear, and delete files and directories in PowerShell.</span></span>

<span data-ttu-id="11f9a-114">De **bestandssysteem** stations zijn een hiërarchische naam ruimte die de mappen en bestanden op uw computer bevat.</span><span class="sxs-lookup"><span data-stu-id="11f9a-114">The **FileSystem** drives are a hierarchical namespace containing the directories and files on your computer.</span></span> <span data-ttu-id="11f9a-115">Een **bestandssysteem** station kan een logisch of fysiek station, een map of een toegewezen netwerk share zijn.</span><span class="sxs-lookup"><span data-stu-id="11f9a-115">A **FileSystem** drive can be a logical or physical drive, directory, or mapped network share.</span></span>

<span data-ttu-id="11f9a-116">Een station `TEMP:` met de naam wordt toegewezen aan het tijdelijke mappad van de gebruiker.</span><span class="sxs-lookup"><span data-stu-id="11f9a-116">A drive called `TEMP:` will be mapped to the user's temporary directory path.</span></span>

>[!NOTE]
> <span data-ttu-id="11f9a-117">Inhoud in het station TEMP: wordt niet automatisch verwijderd door Power shell en is de gebruiker of het besturings systeem dat u wilt beheren.</span><span class="sxs-lookup"><span data-stu-id="11f9a-117">Contents in the TEMP: drive are not automatically removed by PowerShell and is up to the user or operating system to manage.</span></span> <span data-ttu-id="11f9a-118">Deze functie is verplaatst uit experimentele functies in Power shell versie 7,0</span><span class="sxs-lookup"><span data-stu-id="11f9a-118">This Feature was moved out of experimental features in PowerShell Version 7.0</span></span>

<span data-ttu-id="11f9a-119">De **bestandssysteem** provider ondersteunt de volgende cmdlets, die in dit artikel worden besproken.</span><span class="sxs-lookup"><span data-stu-id="11f9a-119">The **FileSystem** provider supports the following cmdlets, which are covered in this article.</span></span>

- [<span data-ttu-id="11f9a-120">Get-locatie</span><span class="sxs-lookup"><span data-stu-id="11f9a-120">Get-Location</span></span>](xref:Microsoft.PowerShell.Management.Get-Location)
- [<span data-ttu-id="11f9a-121">Set-Location</span><span class="sxs-lookup"><span data-stu-id="11f9a-121">Set-Location</span></span>](xref:Microsoft.PowerShell.Management.Set-Location)
- [<span data-ttu-id="11f9a-122">Get-item</span><span class="sxs-lookup"><span data-stu-id="11f9a-122">Get-Item</span></span>](xref:Microsoft.PowerShell.Management.Get-Item)
- [<span data-ttu-id="11f9a-123">Get-Child item</span><span class="sxs-lookup"><span data-stu-id="11f9a-123">Get-ChildItem</span></span>](xref:Microsoft.PowerShell.Management.Get-ChildItem)
- [<span data-ttu-id="11f9a-124">Invoke-item</span><span class="sxs-lookup"><span data-stu-id="11f9a-124">Invoke-Item</span></span>](xref:Microsoft.PowerShell.Management.Invoke-Item)
- [<span data-ttu-id="11f9a-125">Item verplaatsen</span><span class="sxs-lookup"><span data-stu-id="11f9a-125">Move-Item</span></span>](xref:Microsoft.PowerShell.Management.Move-Item)
- [<span data-ttu-id="11f9a-126">Nieuw-item</span><span class="sxs-lookup"><span data-stu-id="11f9a-126">New-Item</span></span>](xref:Microsoft.PowerShell.Management.New-Item)
- [<span data-ttu-id="11f9a-127">Verwijderen-item</span><span class="sxs-lookup"><span data-stu-id="11f9a-127">Remove-Item</span></span>](xref:Microsoft.PowerShell.Management.Remove-Item)
- [<span data-ttu-id="11f9a-128">Get-item Property</span><span class="sxs-lookup"><span data-stu-id="11f9a-128">Get-ItemProperty</span></span>](xref:Microsoft.PowerShell.Management.Get-ItemProperty)
- [<span data-ttu-id="11f9a-129">Set-item Property</span><span class="sxs-lookup"><span data-stu-id="11f9a-129">Set-ItemProperty</span></span>](xref:Microsoft.PowerShell.Management.Set-ItemProperty)
- [<span data-ttu-id="11f9a-130">Wissen-item</span><span class="sxs-lookup"><span data-stu-id="11f9a-130">Clear-Item</span></span>](xref:Microsoft.PowerShell.Management.Clear-Item)
- [<span data-ttu-id="11f9a-131">Wissen-item Property</span><span class="sxs-lookup"><span data-stu-id="11f9a-131">Clear-ItemProperty</span></span>](xref:Microsoft.PowerShell.Management.Clear-ItemProperty)
- [<span data-ttu-id="11f9a-132">Verwijderen-item</span><span class="sxs-lookup"><span data-stu-id="11f9a-132">Remove-Item</span></span>](xref:Microsoft.PowerShell.Management.Remove-Item)
- [<span data-ttu-id="11f9a-133">Verwijderen-item Property</span><span class="sxs-lookup"><span data-stu-id="11f9a-133">Remove-ItemProperty</span></span>](xref:Microsoft.PowerShell.Management.Remove-ItemProperty)
- [<span data-ttu-id="11f9a-134">Get-ACL</span><span class="sxs-lookup"><span data-stu-id="11f9a-134">Get-Acl</span></span>](xref:Microsoft.PowerShell.Security.Get-Acl)
- [<span data-ttu-id="11f9a-135">Set-ACL</span><span class="sxs-lookup"><span data-stu-id="11f9a-135">Set-Acl</span></span>](xref:Microsoft.PowerShell.Security.Set-Acl)
- [<span data-ttu-id="11f9a-136">Get-AuthenticodeSignature</span><span class="sxs-lookup"><span data-stu-id="11f9a-136">Get-AuthenticodeSignature</span></span>](xref:Microsoft.PowerShell.Security.Get-AuthenticodeSignature)
- [<span data-ttu-id="11f9a-137">Set-AuthenticodeSignature</span><span class="sxs-lookup"><span data-stu-id="11f9a-137">Set-AuthenticodeSignature</span></span>](xref:Microsoft.PowerShell.Security.Set-AuthenticodeSignature)

## <a name="types-exposed-by-this-provider"></a><span data-ttu-id="11f9a-138">Typen die door deze provider worden weer gegeven</span><span class="sxs-lookup"><span data-stu-id="11f9a-138">Types exposed by this provider</span></span>

<span data-ttu-id="11f9a-139">De bestanden zijn exemplaren van de klasse [System. io. file info](/dotnet/api/system.io.fileinfo) .</span><span class="sxs-lookup"><span data-stu-id="11f9a-139">Files are instances of the [System.IO.FileInfo](/dotnet/api/system.io.fileinfo) class.</span></span> <span data-ttu-id="11f9a-140">Directory's zijn exemplaren van de klasse [System. io. DirectoryInfo](/dotnet/api/system.io.directoryinfo) .</span><span class="sxs-lookup"><span data-stu-id="11f9a-140">Directories are instances of the [System.IO.DirectoryInfo](/dotnet/api/system.io.directoryinfo) class.</span></span>

## <a name="navigating-the-filesystem-drives"></a><span data-ttu-id="11f9a-141">Navigeren door de bestandssysteem stations</span><span class="sxs-lookup"><span data-stu-id="11f9a-141">Navigating the FileSystem drives</span></span>

<span data-ttu-id="11f9a-142">De gegevens archieven van het **Bestands systeem** worden weer gegeven door logische stations op de computer toe te wijzen als Power Shell-stations.</span><span class="sxs-lookup"><span data-stu-id="11f9a-142">The **FileSystem** provider exposes its data stores by mapping any logical drives on the computer as PowerShell drives.</span></span> <span data-ttu-id="11f9a-143">Als u wilt werken met een **bestandssysteem** station, kunt u uw locatie wijzigen in een station met behulp van de stationsnaam gevolgd door een dubbele punt ( `:` ).</span><span class="sxs-lookup"><span data-stu-id="11f9a-143">To work with a **FileSystem** drive you can change your location to a drive using the drive name followed by a colon (`:`).</span></span>

```powershell
Set-Location C:
```

<span data-ttu-id="11f9a-144">U kunt ook met de **File System** provider werken vanuit elk ander Power Shell-station.</span><span class="sxs-lookup"><span data-stu-id="11f9a-144">You can also work with the **FileSystem** provider from any other PowerShell drive.</span></span> <span data-ttu-id="11f9a-145">Als u wilt verwijzen naar een bestand of map vanaf een andere locatie, gebruikt u de naam van het station ( `C:` , `D:` ,...) in het pad.</span><span class="sxs-lookup"><span data-stu-id="11f9a-145">To reference a file or directory from another location, use the drive name (`C:`, `D:`, ...) in the path.</span></span>

> [!NOTE]
> <span data-ttu-id="11f9a-146">In Power shell worden aliassen gebruikt om u een vertrouwde manier te bieden om met provider paden te werken.</span><span class="sxs-lookup"><span data-stu-id="11f9a-146">PowerShell uses aliases to allow you a familiar way to work with provider paths.</span></span> <span data-ttu-id="11f9a-147">Opdrachten zoals `dir` en `ls` zijn nu aliassen voor [Get-Child item](xref:Microsoft.PowerShell.Management.Get-ChildItem), `cd` is een alias voor [Set-Location](xref:Microsoft.PowerShell.Management.Set-Location).</span><span class="sxs-lookup"><span data-stu-id="11f9a-147">Commands such as `dir` and `ls` are now aliases for [Get-ChildItem](xref:Microsoft.PowerShell.Management.Get-ChildItem), `cd` is an alias for [Set-Location](xref:Microsoft.PowerShell.Management.Set-Location).</span></span> <span data-ttu-id="11f9a-148">en `pwd` is een alias voor [Get-location](xref:Microsoft.PowerShell.Management.Get-Location).</span><span class="sxs-lookup"><span data-stu-id="11f9a-148">and `pwd` is an alias for [Get-Location](xref:Microsoft.PowerShell.Management.Get-Location).</span></span>

## <a name="getting-files-and-directories"></a><span data-ttu-id="11f9a-149">Bestanden en mappen ophalen</span><span class="sxs-lookup"><span data-stu-id="11f9a-149">Getting files and directories</span></span>

<span data-ttu-id="11f9a-150">De `Get-ChildItem` cmdlet retourneert alle bestanden en mappen op de huidige locatie.</span><span class="sxs-lookup"><span data-stu-id="11f9a-150">The `Get-ChildItem` cmdlet returns all files and directories in the current location.</span></span> <span data-ttu-id="11f9a-151">U kunt een ander pad opgeven om te zoeken en ingebouwde para meters te gebruiken voor het filteren en beheren van de diepte van recursie.</span><span class="sxs-lookup"><span data-stu-id="11f9a-151">You can specify a different path to search and use built in parameters to filter and control the recursion depth.</span></span>

```powershell
Get-ChildItem
```

<span data-ttu-id="11f9a-152">Zie [Get-Child item](xref:Microsoft.PowerShell.Management.Get-ChildItem)voor meer informatie over het gebruik van de cmdlet.</span><span class="sxs-lookup"><span data-stu-id="11f9a-152">To read more about cmdlet usage, see [Get-ChildItem](xref:Microsoft.PowerShell.Management.Get-ChildItem).</span></span>

## <a name="copying-files-and-directories"></a><span data-ttu-id="11f9a-153">Kopiëren van bestanden en mappen</span><span class="sxs-lookup"><span data-stu-id="11f9a-153">Copying files and directories</span></span>

<span data-ttu-id="11f9a-154">De `Copy-Item` cmdlet kopieert bestanden en mappen naar een locatie die u opgeeft.</span><span class="sxs-lookup"><span data-stu-id="11f9a-154">The `Copy-Item` cmdlet copies files and directories to a location you specify.</span></span>
<span data-ttu-id="11f9a-155">Para meters zijn beschikbaar voor filteren en recursief, vergelijkbaar met `Get-ChildItem` .</span><span class="sxs-lookup"><span data-stu-id="11f9a-155">Parameters are available to filter and recurse, similar to `Get-ChildItem`.</span></span>

<span data-ttu-id="11f9a-156">Met de volgende opdracht worden alle bestanden en mappen onder het pad ' C:\Temp \" naar de map ' C:\Windows\Temp gekopieerd.</span><span class="sxs-lookup"><span data-stu-id="11f9a-156">The following command copies all of the files and directories under the path "C:\temp\" to the folder "C:\Windows\Temp".</span></span>

```powershell
Copy-Item -Path C:\temp\* -Destination C:\Windows\Temp -Recurse -File
```

<span data-ttu-id="11f9a-157">`Copy-Item` overschrijft bestanden in de doelmap zonder dat om bevestiging wordt gevraagd.</span><span class="sxs-lookup"><span data-stu-id="11f9a-157">`Copy-Item` overwrites files in the destination directory without prompting for confirmation.</span></span>

<span data-ttu-id="11f9a-158">Met deze opdracht kopieert `a.txt` u het bestand vanuit de `C:\a` map naar de `C:\a\bb` map.</span><span class="sxs-lookup"><span data-stu-id="11f9a-158">This command copies the `a.txt` file from the `C:\a` directory to the `C:\a\bb` directory.</span></span>

```powershell
Copy-Item -Path C:\a\a.txt -Destination C:\a\bb\a.txt
```

<span data-ttu-id="11f9a-159">Kopieert alle mappen en bestanden in de `C:\a` map naar de `C:\c` map.</span><span class="sxs-lookup"><span data-stu-id="11f9a-159">Copies all the directories and files in the `C:\a` directory to the `C:\c` directory.</span></span> <span data-ttu-id="11f9a-160">Als een van de mappen die u wilt kopiëren al aanwezig is in de doelmap, mislukt de opdracht tenzij u de para meter Force opgeeft.</span><span class="sxs-lookup"><span data-stu-id="11f9a-160">If any of the directories to copy already exist in the destination directory, the command will fail unless you specify the Force parameter.</span></span>

```powershell
Copy-Item -Path C:\a\* -Destination C:\c -Recurse
```

<span data-ttu-id="11f9a-161">Zie [kopiëren-item](xref:Microsoft.PowerShell.Management.Copy-Item)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="11f9a-161">For more information, see [Copy-Item](xref:Microsoft.PowerShell.Management.Copy-Item).</span></span>

## <a name="moving-files-and-directories"></a><span data-ttu-id="11f9a-162">Bestanden en mappen verplaatsen</span><span class="sxs-lookup"><span data-stu-id="11f9a-162">Moving files and directories</span></span>

<span data-ttu-id="11f9a-163">Met deze opdracht wordt het `c.txt` bestand in de `C:\a` map verplaatst naar de `C:\a\aa` map:</span><span class="sxs-lookup"><span data-stu-id="11f9a-163">This command moves the `c.txt` file in the `C:\a` directory to the `C:\a\aa` directory:</span></span>

```powershell
Move-Item -Path C:\a\c.txt -Destination C:\a\aa
```

<span data-ttu-id="11f9a-164">Met de opdracht wordt een bestaand bestand met dezelfde naam niet automatisch overschreven.</span><span class="sxs-lookup"><span data-stu-id="11f9a-164">The command will not automatically overwrite an existing file that has the same name.</span></span> <span data-ttu-id="11f9a-165">Als u wilt forceren dat de cmdlet een bestaand bestand overschrijft, geeft u de para meter Force op.</span><span class="sxs-lookup"><span data-stu-id="11f9a-165">To force the cmdlet to overwrite an existing file, specify the Force parameter.</span></span>

<span data-ttu-id="11f9a-166">U kunt een map niet verplaatsen als die map de huidige locatie is.</span><span class="sxs-lookup"><span data-stu-id="11f9a-166">You cannot move a directory when that directory is the current location.</span></span> <span data-ttu-id="11f9a-167">Wanneer u gebruikt `Move-Item` om de map op de huidige locatie te verplaatsen, ziet u deze fout.</span><span class="sxs-lookup"><span data-stu-id="11f9a-167">When you use `Move-Item` to move the directory at the current location, you see this error.</span></span>

```
C:\temp> Move-Item -Path C:\temp\ -Destination C:\Windows\Temp

Move-Item : Cannot move item because the item at 'C:\temp\' is in use.
At line:1 char:1
+ Move-Item C:\temp\ C:\temp2\
+ ~~~~~~~~~~~~~~~~~~~~~~~~~~~~
    + CategoryInfo          : InvalidOperation: (:) [Move-Item], PSInvalidOperationException
    + FullyQualifiedErrorId : InvalidOperation,Microsoft.PowerShell.Commands.MoveItemCommand
```

## <a name="managing-file-content"></a><span data-ttu-id="11f9a-168">Bestands inhoud beheren</span><span class="sxs-lookup"><span data-stu-id="11f9a-168">Managing file content</span></span>

### <a name="get-the-content-of-a-file"></a><span data-ttu-id="11f9a-169">De inhoud van een bestand ophalen</span><span class="sxs-lookup"><span data-stu-id="11f9a-169">Get the content of a file</span></span>

<span data-ttu-id="11f9a-170">Met deze opdracht wordt de inhoud van het bestand ' Test.txt ' opgehaald en weer gegeven in de-console.</span><span class="sxs-lookup"><span data-stu-id="11f9a-170">This command gets the contents of the "Test.txt" file and displays them in the console.</span></span>

```powershell
Get-Content -Path Test.txt
```

<span data-ttu-id="11f9a-171">U kunt de inhoud van het bestand door sluizen naar een andere cmdlet.</span><span class="sxs-lookup"><span data-stu-id="11f9a-171">You can pipe the contents of the file to another cmdlet.</span></span> <span data-ttu-id="11f9a-172">Met de volgende opdracht wordt bijvoorbeeld de inhoud van het `Test.txt` bestand gelezen en vervolgens als invoer voor de [ConvertTo-HTML-](xref:Microsoft.PowerShell.Utility.ConvertTo-Html) cmdlet geleverd:</span><span class="sxs-lookup"><span data-stu-id="11f9a-172">For example, the following command reads the contents of the `Test.txt` file and then supplies them as input to the [ConvertTo-Html](xref:Microsoft.PowerShell.Utility.ConvertTo-Html) cmdlet:</span></span>

```powershell
Get-Content -Path Test.txt | ConvertTo-Html
```

<span data-ttu-id="11f9a-173">U kunt ook de inhoud van een bestand ophalen door een voor voegsel van het pad naar de provider te krijgen met het dollar teken ( `$` ).</span><span class="sxs-lookup"><span data-stu-id="11f9a-173">You can also retrieve the content of a file by prefixing its provider path with the dollar sign (`$`).</span></span> <span data-ttu-id="11f9a-174">Het pad moet tussen accolades worden geplaatst als gevolg van beperkingen voor de naamgeving van variabelen.</span><span class="sxs-lookup"><span data-stu-id="11f9a-174">The path must be enclosed in curly braces due to variable naming restrictions.</span></span> <span data-ttu-id="11f9a-175">Zie [about_Variables](about_Variables.md)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="11f9a-175">For more information, see [about_Variables](about_Variables.md).</span></span>

```powershell
${C:\Windows\System32\Drivers\etc\hosts}
```

### <a name="add-content-to-a-file"></a><span data-ttu-id="11f9a-176">Inhoud toevoegen aan een bestand</span><span class="sxs-lookup"><span data-stu-id="11f9a-176">Add content to a file</span></span>

<span data-ttu-id="11f9a-177">Met deze opdracht wordt de teken reeks test inhoud toegevoegd aan het `Test.txt` bestand:</span><span class="sxs-lookup"><span data-stu-id="11f9a-177">This command appends the "test content" string to the `Test.txt` file:</span></span>

```powershell
Add-Content -Path test.txt -Value "test content"
```

<span data-ttu-id="11f9a-178">De bestaande inhoud in het `Test.txt` bestand wordt niet verwijderd.</span><span class="sxs-lookup"><span data-stu-id="11f9a-178">The existing content in the `Test.txt` file is not deleted.</span></span>

### <a name="replace-the-content-of-a-file"></a><span data-ttu-id="11f9a-179">De inhoud van een bestand vervangen</span><span class="sxs-lookup"><span data-stu-id="11f9a-179">Replace the content of a file</span></span>

<span data-ttu-id="11f9a-180">Met deze opdracht wordt de inhoud van het `Test.txt` bestand vervangen door de teken reeks "inhoud testen":</span><span class="sxs-lookup"><span data-stu-id="11f9a-180">This command replaces the contents of the `Test.txt` file with the "test content" string:</span></span>

```powershell
Set-Content -Path test.txt -Value "test content"
```

<span data-ttu-id="11f9a-181">De inhoud van wordt overschreven `Test.txt` .</span><span class="sxs-lookup"><span data-stu-id="11f9a-181">It overwrites the contents of `Test.txt`.</span></span> <span data-ttu-id="11f9a-182">U kunt de para meter **Value** van de cmdlet [New-item](xref:Microsoft.PowerShell.Management.New-Item) gebruiken om inhoud toe te voegen aan een bestand wanneer u het maakt.</span><span class="sxs-lookup"><span data-stu-id="11f9a-182">You can use the **Value** parameter of the [New-Item](xref:Microsoft.PowerShell.Management.New-Item) cmdlet to add content to a file when you create it.</span></span>

### <a name="loop-through-the-contents-of-a-file"></a><span data-ttu-id="11f9a-183">De inhoud van een bestand door lopen</span><span class="sxs-lookup"><span data-stu-id="11f9a-183">Loop through the contents of a file</span></span>

<span data-ttu-id="11f9a-184">De `Get-Content` cmdlet maakt standaard gebruik van het einde van de regel als scheidings teken, zodat er een bestand wordt opgehaald als een verzameling teken reeksen, waarbij elke regel als één teken reeks in het bestand wordt gebruikt.</span><span class="sxs-lookup"><span data-stu-id="11f9a-184">By default, the `Get-Content` cmdlet uses the end-of-line character as its delimiter, so it gets a file as a collection of strings, with each line as one string in the file.</span></span>

<span data-ttu-id="11f9a-185">U kunt de `-Delimiter` para meter gebruiken om een alternatief scheidings teken op te geven.</span><span class="sxs-lookup"><span data-stu-id="11f9a-185">You can use the `-Delimiter` parameter to specify an alternate delimiter.</span></span> <span data-ttu-id="11f9a-186">Als u deze instelt op de tekens waarin het einde van een sectie of het begin van de volgende sectie wordt aangegeven, kunt u het bestand in logische delen splitsen.</span><span class="sxs-lookup"><span data-stu-id="11f9a-186">If you set it to the characters that denote the end of a section or the beginning of the next section, you can split the file into logical parts.</span></span>

<span data-ttu-id="11f9a-187">Met de eerste opdracht wordt het `Employees.txt` bestand opgehaald en gesplitst in secties, die allemaal eindigen met de woorden ' einde van werknemers record ', en deze worden opgeslagen in de `$e` variabele.</span><span class="sxs-lookup"><span data-stu-id="11f9a-187">The first command gets the `Employees.txt` file and splits it into sections, each of which ends with the words "End of Employee Record" and it saves it in the `$e` variable.</span></span>

<span data-ttu-id="11f9a-188">De tweede opdracht maakt gebruik van de matrix notatie voor het ophalen van het eerste item in de verzameling in `$e` .</span><span class="sxs-lookup"><span data-stu-id="11f9a-188">The second command uses array notation to get the first item in the collection in `$e`.</span></span> <span data-ttu-id="11f9a-189">Er wordt gebruikgemaakt van een index van 0, omdat Power shell-matrices op nul zijn gebaseerd.</span><span class="sxs-lookup"><span data-stu-id="11f9a-189">It uses an index of 0, because PowerShell arrays are zero-based.</span></span>

<span data-ttu-id="11f9a-190">`Get-Content`Zie het Help-onderwerp voor de [Get-content](xref:Microsoft.PowerShell.Management.Get-Content)voor meer informatie over de cmdlet.</span><span class="sxs-lookup"><span data-stu-id="11f9a-190">For more information about `Get-Content` cmdlet, see the help topic for the [Get-Content](xref:Microsoft.PowerShell.Management.Get-Content).</span></span>

<span data-ttu-id="11f9a-191">Zie [about_Arrays](../About/about_Arrays.md)voor meer informatie over matrices.</span><span class="sxs-lookup"><span data-stu-id="11f9a-191">For more information about arrays, see [about_Arrays](../About/about_Arrays.md).</span></span>

```powershell
$e = Get-Content c:\test\employees.txt -Delimited "End Of Employee Record"
$e[0]
```

## <a name="managing-security-descriptors"></a><span data-ttu-id="11f9a-192">Security descriptors beheren</span><span class="sxs-lookup"><span data-stu-id="11f9a-192">Managing security descriptors</span></span>

### <a name="view-the-acl-for-a-file"></a><span data-ttu-id="11f9a-193">De ACL voor een bestand weer geven</span><span class="sxs-lookup"><span data-stu-id="11f9a-193">View the ACL for a file</span></span>

<span data-ttu-id="11f9a-194">Met deze opdracht wordt een [System. Security. accesscontrol. FileSecurity](/dotnet/api/system.security.accesscontrol.filesecurity) -object geretourneerd:</span><span class="sxs-lookup"><span data-stu-id="11f9a-194">This command returns a [System.Security.AccessControl.FileSecurity](/dotnet/api/system.security.accesscontrol.filesecurity) object:</span></span>

```powershell
Get-Acl -Path test.txt | Format-List -Property *
```

<span data-ttu-id="11f9a-195">Voor meer informatie over dit object pipet u de opdracht naar de cmdlet [Get-member](xref:Microsoft.PowerShell.Utility.Get-Member) .</span><span class="sxs-lookup"><span data-stu-id="11f9a-195">For more information about this object, pipe the command to the [Get-Member](xref:Microsoft.PowerShell.Utility.Get-Member) cmdlet.</span></span> <span data-ttu-id="11f9a-196">Of Zie [FileSecurity](/dotnet/api/system.security.accesscontrol.filesecurity) -klasse.</span><span class="sxs-lookup"><span data-stu-id="11f9a-196">Or, see [FileSecurity](/dotnet/api/system.security.accesscontrol.filesecurity) Class.</span></span>

### <a name="modify-the-acl-for-a-file"></a><span data-ttu-id="11f9a-197">De ACL voor een bestand wijzigen</span><span class="sxs-lookup"><span data-stu-id="11f9a-197">Modify the ACL for a file</span></span>

### <a name="create-and-set-an-acl-for-a-file"></a><span data-ttu-id="11f9a-198">Een ACL maken en instellen voor een bestand</span><span class="sxs-lookup"><span data-stu-id="11f9a-198">Create and set an ACL for a file</span></span>

## <a name="creating-files-and-directories"></a><span data-ttu-id="11f9a-199">Bestanden en mappen maken</span><span class="sxs-lookup"><span data-stu-id="11f9a-199">Creating files and directories</span></span>

### <a name="create-a-directory"></a><span data-ttu-id="11f9a-200">Een map maken</span><span class="sxs-lookup"><span data-stu-id="11f9a-200">Create a directory</span></span>

<span data-ttu-id="11f9a-201">Met deze opdracht maakt u de `logfiles` map op het `C` station:</span><span class="sxs-lookup"><span data-stu-id="11f9a-201">This command creates the `logfiles` directory on the `C` drive:</span></span>

```powershell
New-Item -Path c:\ -Name logfiles -Type directory
```

<span data-ttu-id="11f9a-202">Power shell bevat ook een `mkdir` functie (alias `md` ) die gebruikmaakt van de cmdlet [New-item](xref:Microsoft.PowerShell.Management.New-Item) om een nieuwe map te maken.</span><span class="sxs-lookup"><span data-stu-id="11f9a-202">PowerShell also includes a `mkdir` function (alias `md`) that uses the [New-Item](xref:Microsoft.PowerShell.Management.New-Item) cmdlet to create a new directory.</span></span>

### <a name="create-a-file"></a><span data-ttu-id="11f9a-203">Een bestand maken</span><span class="sxs-lookup"><span data-stu-id="11f9a-203">Create a file</span></span>

<span data-ttu-id="11f9a-204">Met deze opdracht maakt `log2.txt` u het bestand in de `C:\logfiles` map en voegt u vervolgens de teken reeks "test logboek" toe aan het bestand:</span><span class="sxs-lookup"><span data-stu-id="11f9a-204">This command creates the `log2.txt` file in the `C:\logfiles` directory and then adds the "test log" string to the file:</span></span>

```powershell
New-Item -Path c:\logfiles -Name log2.txt -Type file
```

### <a name="create-a-file-with-content"></a><span data-ttu-id="11f9a-205">Een bestand met inhoud maken</span><span class="sxs-lookup"><span data-stu-id="11f9a-205">Create a file with content</span></span>

<span data-ttu-id="11f9a-206">Hiermee maakt u een bestand `log2.txt` met de naam in de `C:\logfiles` map en voegt u de teken reeks ' test logboek ' toe aan het bestand.</span><span class="sxs-lookup"><span data-stu-id="11f9a-206">Creates a file called `log2.txt` in the `C:\logfiles` directory and adds the string "test log" to the file.</span></span>

```powershell
New-Item -Path c:\logfiles -Name log2.txt -Type file -Value "test log"
```

## <a name="renaming-files-and-directories"></a><span data-ttu-id="11f9a-207">Naam wijzigen van bestanden en mappen</span><span class="sxs-lookup"><span data-stu-id="11f9a-207">Renaming files and directories</span></span>

### <a name="rename-a-file"></a><span data-ttu-id="11f9a-208">De naam van een bestand wijzigen</span><span class="sxs-lookup"><span data-stu-id="11f9a-208">Rename a file</span></span>

<span data-ttu-id="11f9a-209">Met deze opdracht wordt de naam `a.txt` van het bestand in de map gewijzigd in `C:\a` `b.txt` :</span><span class="sxs-lookup"><span data-stu-id="11f9a-209">This command renames the `a.txt` file in the `C:\a` directory to `b.txt`:</span></span>

```powershell
Rename-Item -Path c:\a\a.txt -NewName b.txt
```

### <a name="rename-a-directory"></a><span data-ttu-id="11f9a-210">De naam van een map wijzigen</span><span class="sxs-lookup"><span data-stu-id="11f9a-210">Rename a directory</span></span>

<span data-ttu-id="11f9a-211">Met deze opdracht wordt de naam van de `C:\a\cc` map gewijzigd in `C:\a\dd` :</span><span class="sxs-lookup"><span data-stu-id="11f9a-211">This command renames the `C:\a\cc` directory to `C:\a\dd`:</span></span>

```powershell
Rename-Item -Path c:\a\cc -NewName dd
```

## <a name="deleting-files-and-directories"></a><span data-ttu-id="11f9a-212">Bestanden en mappen verwijderen</span><span class="sxs-lookup"><span data-stu-id="11f9a-212">Deleting files and directories</span></span>

### <a name="delete-a-file"></a><span data-ttu-id="11f9a-213">Een bestand verwijderen</span><span class="sxs-lookup"><span data-stu-id="11f9a-213">Delete a file</span></span>

<span data-ttu-id="11f9a-214">Met deze opdracht wordt het `Test.txt` bestand in de huidige map verwijderd:</span><span class="sxs-lookup"><span data-stu-id="11f9a-214">This command deletes the `Test.txt` file in the current directory:</span></span>

```powershell
Remove-Item -Path test.txt
```

### <a name="delete-files-using-wildcards"></a><span data-ttu-id="11f9a-215">Bestanden verwijderen met Joker tekens</span><span class="sxs-lookup"><span data-stu-id="11f9a-215">Delete files using wildcards</span></span>

<span data-ttu-id="11f9a-216">Met deze opdracht worden alle bestanden in de huidige map met de `.xml` bestandsnaam extensie verwijderd:</span><span class="sxs-lookup"><span data-stu-id="11f9a-216">This command deletes all the files in the current directory that have the `.xml` file name extension:</span></span>

```powershell
Remove-Item -Path *.xml
```

## <a name="starting-a-program-by-invoking-an-associated-file"></a><span data-ttu-id="11f9a-217">Een programma starten door een gekoppeld bestand aan te roepen</span><span class="sxs-lookup"><span data-stu-id="11f9a-217">Starting a program by invoking an associated file</span></span>

### <a name="invoke-a-file"></a><span data-ttu-id="11f9a-218">Een bestand aanroepen</span><span class="sxs-lookup"><span data-stu-id="11f9a-218">Invoke a file</span></span>

<span data-ttu-id="11f9a-219">Met de eerste opdracht wordt de cmdlet [Get-service](xref:Microsoft.PowerShell.Management.Get-Service) gebruikt om informatie over lokale services op te halen.</span><span class="sxs-lookup"><span data-stu-id="11f9a-219">The first command uses the [Get-Service](xref:Microsoft.PowerShell.Management.Get-Service) cmdlet to get information about local services.</span></span>

<span data-ttu-id="11f9a-220">Het pipet de gegevens naar de cmdlet [export-csv](xref:Microsoft.PowerShell.Utility.Export-Csv) en slaat die informatie vervolgens op in het `Services.csv` bestand.</span><span class="sxs-lookup"><span data-stu-id="11f9a-220">It pipes the information to the [Export-Csv](xref:Microsoft.PowerShell.Utility.Export-Csv) cmdlet and then stores that information in the `Services.csv` file.</span></span>

<span data-ttu-id="11f9a-221">Met de tweede opdracht wordt [invoke-item](xref:Microsoft.PowerShell.Management.Invoke-Item) gebruikt om het bestand te openen `services.csv` in het programma dat is gekoppeld aan de `.csv` extensie:</span><span class="sxs-lookup"><span data-stu-id="11f9a-221">The second command uses [Invoke-Item](xref:Microsoft.PowerShell.Management.Invoke-Item) to open the `services.csv` file in the program associated with the `.csv` extension:</span></span>

```powershell
Get-Service | Export-Csv -Path services.csv
Invoke-Item -Path services.csv
```

## <a name="getting-files-and-folders-with-specified-attributes"></a><span data-ttu-id="11f9a-222">Bestanden en mappen met opgegeven kenmerken ophalen</span><span class="sxs-lookup"><span data-stu-id="11f9a-222">Getting files and folders with specified attributes</span></span>

### <a name="get-system-files"></a><span data-ttu-id="11f9a-223">Systeem bestanden ophalen</span><span class="sxs-lookup"><span data-stu-id="11f9a-223">Get System files</span></span>

<span data-ttu-id="11f9a-224">Met deze opdracht worden systeem bestanden in de huidige map en de submappen ervan opgehaald.</span><span class="sxs-lookup"><span data-stu-id="11f9a-224">This command gets system files in the current directory and its subdirectories.</span></span>

<span data-ttu-id="11f9a-225">De `-File` para meter wordt gebruikt voor het ophalen van alleen bestanden (niet directory's) en de `-System` para meter om alleen items met het kenmerk systeem op te halen.</span><span class="sxs-lookup"><span data-stu-id="11f9a-225">It uses the `-File` parameter to get only files (not directories) and the `-System` parameter to get only items with the "system" attribute.</span></span>

<span data-ttu-id="11f9a-226">De `-Recurse` para meter wordt gebruikt voor het ophalen van de items in de huidige map en alle submappen.</span><span class="sxs-lookup"><span data-stu-id="11f9a-226">It uses the `-Recurse` parameter to get the items in the current directory and all subdirectories.</span></span>

```powershell
Get-ChildItem -File -System -Recurse
```

### <a name="get-hidden-files"></a><span data-ttu-id="11f9a-227">Verborgen bestanden ophalen</span><span class="sxs-lookup"><span data-stu-id="11f9a-227">Get Hidden files</span></span>

<span data-ttu-id="11f9a-228">Met deze opdracht worden alle bestanden met inbegrip van verborgen bestanden in de huidige map opgehaald.</span><span class="sxs-lookup"><span data-stu-id="11f9a-228">This command gets all files, including hidden files, in the current directory.</span></span>

<span data-ttu-id="11f9a-229">Hierbij wordt gebruikgemaakt van de para meter **Attributes** met twee waarden, `!Directory+Hidden` , die verborgen bestanden ophalen en `!Directory` , waarmee alle andere bestanden worden opgehaald.</span><span class="sxs-lookup"><span data-stu-id="11f9a-229">It uses the **Attributes** parameter with two values, `!Directory+Hidden`, which gets hidden files, and `!Directory`, which gets all other files.</span></span>

```powershell
Get-ChildItem -Attributes !Directory,!Directory+Hidden
```

<span data-ttu-id="11f9a-230">`dir -att !d,!d+h` is het equivalent van deze opdracht.</span><span class="sxs-lookup"><span data-stu-id="11f9a-230">`dir -att !d,!d+h` is the equivalent of this command.</span></span>

### <a name="get-compressed-and-encrypted-files"></a><span data-ttu-id="11f9a-231">Gecomprimeerde en versleutelde bestanden ophalen</span><span class="sxs-lookup"><span data-stu-id="11f9a-231">Get Compressed and Encrypted files</span></span>

<span data-ttu-id="11f9a-232">Met deze opdracht worden bestanden in de huidige map opgehaald die zijn gecomprimeerd of versleuteld zijn.</span><span class="sxs-lookup"><span data-stu-id="11f9a-232">This command gets files in the current directory that are either compressed or encrypted.</span></span>

<span data-ttu-id="11f9a-233">De `-Attributes` para meter wordt gebruikt met twee waarden `Compressed` en `Encrypted` .</span><span class="sxs-lookup"><span data-stu-id="11f9a-233">It uses the `-Attributes` parameter with two values, `Compressed` and `Encrypted`.</span></span> <span data-ttu-id="11f9a-234">De waarden worden gescheiden door een komma `,` die de operator or vertegenwoordigt.</span><span class="sxs-lookup"><span data-stu-id="11f9a-234">The values are separated by a comma `,` which represents the "OR" operator.</span></span>

```powershell
Get-ChildItem -Attributes Compressed,Encrypted
```

## <a name="dynamic-parameters"></a><span data-ttu-id="11f9a-235">Dynamische parameters</span><span class="sxs-lookup"><span data-stu-id="11f9a-235">Dynamic parameters</span></span>

<span data-ttu-id="11f9a-236">Dynamische para meters zijn cmdlet-para meters die worden toegevoegd door een Power shell-provider en zijn alleen beschikbaar wanneer de cmdlet wordt gebruikt in het station waarvoor de provider is ingeschakeld.</span><span class="sxs-lookup"><span data-stu-id="11f9a-236">Dynamic parameters are cmdlet parameters that are added by a PowerShell provider and are available only when the cmdlet is being used in the provider-enabled drive.</span></span>

### <a name="encoding-microsoftpowershellcommandsfilesystemcmdletproviderencoding"></a><span data-ttu-id="11f9a-237">Gecodeerd \<Microsoft.PowerShell.Commands.FileSystemCmdletProviderEncoding\></span><span class="sxs-lookup"><span data-stu-id="11f9a-237">Encoding \<Microsoft.PowerShell.Commands.FileSystemCmdletProviderEncoding\></span></span>

<span data-ttu-id="11f9a-238">Hiermee geeft u de bestands codering.</span><span class="sxs-lookup"><span data-stu-id="11f9a-238">Specifies the file encoding.</span></span> <span data-ttu-id="11f9a-239">De standaard waarde is ASCII.</span><span class="sxs-lookup"><span data-stu-id="11f9a-239">The default is ASCII.</span></span>

- <span data-ttu-id="11f9a-240">**ASCII**: gebruikt de code ring voor de ASCII-tekenset (7-bits).</span><span class="sxs-lookup"><span data-stu-id="11f9a-240">**ASCII**:  Uses the encoding for the ASCII (7-bit) character set.</span></span>
- <span data-ttu-id="11f9a-241">**BigEndianUnicode**: codeert in UTF-16-indeling met behulp van de byte volgorde big endian.</span><span class="sxs-lookup"><span data-stu-id="11f9a-241">**BigEndianUnicode**:  Encodes in UTF-16 format using the big-endian byte order.</span></span>
- <span data-ttu-id="11f9a-242">**Teken reeks**: maakt gebruik van het coderings type voor een teken reeks.</span><span class="sxs-lookup"><span data-stu-id="11f9a-242">**String**:  Uses the encoding type for a string.</span></span>
- <span data-ttu-id="11f9a-243">**Unicode**: wordt gecodeerd in UTF-16-indeling met behulp van de byte volgorde little endian.</span><span class="sxs-lookup"><span data-stu-id="11f9a-243">**Unicode**:  Encodes in UTF-16 format using the little-endian byte order.</span></span>
- <span data-ttu-id="11f9a-244">**UTF7**: wordt gecodeerd in de indeling UTF-7.</span><span class="sxs-lookup"><span data-stu-id="11f9a-244">**UTF7**:   Encodes in UTF-7 format.</span></span>
- <span data-ttu-id="11f9a-245">**Utf8**: gecodeerd in UTF-8-indeling.</span><span class="sxs-lookup"><span data-stu-id="11f9a-245">**UTF8**:  Encodes in UTF-8 format.</span></span>
- <span data-ttu-id="11f9a-246">**UTF8BOM**: coderen in UTF-8-indeling met byte order Mark (bom)</span><span class="sxs-lookup"><span data-stu-id="11f9a-246">**UTF8BOM**: Encodes in UTF-8 format with Byte Order Mark (BOM)</span></span>
- <span data-ttu-id="11f9a-247">**UF8NOBOM**: code ring in UTF-8-indeling zonder byte order Mark (bom)</span><span class="sxs-lookup"><span data-stu-id="11f9a-247">**UF8NOBOM**: Encodes in UTF-8 format without Byte Order Mark (BOM)</span></span>
- <span data-ttu-id="11f9a-248">**UTF32**: code ring in UTF-32-indeling.</span><span class="sxs-lookup"><span data-stu-id="11f9a-248">**UTF32**:  Encodes in UTF-32 format.</span></span>
- <span data-ttu-id="11f9a-249">**Standaard**: Codeer in de standaard pagina met geïnstalleerde codes.</span><span class="sxs-lookup"><span data-stu-id="11f9a-249">**Default**: Encodes in the default installed code page.</span></span>
- <span data-ttu-id="11f9a-250">**OEM**: gebruikt de standaard codering voor MS-DOS-en console-Program ma's.</span><span class="sxs-lookup"><span data-stu-id="11f9a-250">**OEM**: Uses the default encoding for MS-DOS and console programs.</span></span>
- <span data-ttu-id="11f9a-251">**Onbekend**: het coderings type is onbekend of ongeldig.</span><span class="sxs-lookup"><span data-stu-id="11f9a-251">**Unknown**:  The encoding type is unknown or invalid.</span></span> <span data-ttu-id="11f9a-252">De gegevens kunnen worden behandeld als binair.</span><span class="sxs-lookup"><span data-stu-id="11f9a-252">The data can be treated as binary.</span></span>

#### <a name="cmdlets-supported"></a><span data-ttu-id="11f9a-253">Ondersteunde cmdlets</span><span class="sxs-lookup"><span data-stu-id="11f9a-253">Cmdlets supported</span></span>

- [<span data-ttu-id="11f9a-254">Add-content</span><span class="sxs-lookup"><span data-stu-id="11f9a-254">Add-Content</span></span>](xref:Microsoft.PowerShell.Management.Add-Content)
- [<span data-ttu-id="11f9a-255">Get-Content</span><span class="sxs-lookup"><span data-stu-id="11f9a-255">Get-Content</span></span>](xref:Microsoft.PowerShell.Management.Get-Content)
- [<span data-ttu-id="11f9a-256">Set-Content</span><span class="sxs-lookup"><span data-stu-id="11f9a-256">Set-Content</span></span>](xref:Microsoft.PowerShell.Management.Set-Content)

### <a name="delimiter-systemstring"></a><span data-ttu-id="11f9a-257">Vorm \<System.String\></span><span class="sxs-lookup"><span data-stu-id="11f9a-257">Delimiter \<System.String\></span></span>

<span data-ttu-id="11f9a-258">Hiermee geeft u het scheidings teken op dat wordt gebruikt om het bestand in objecten te verdelen terwijl [het wordt gelezen](xref:Microsoft.PowerShell.Management.Get-Content) .</span><span class="sxs-lookup"><span data-stu-id="11f9a-258">Specifies the delimiter that [Get-Content](xref:Microsoft.PowerShell.Management.Get-Content) uses to divide the file into objects while it reads.</span></span>

<span data-ttu-id="11f9a-259">De standaard waarde is `\n` , het einde van de regel.</span><span class="sxs-lookup"><span data-stu-id="11f9a-259">The default is `\n`, the end-of-line character.</span></span>

<span data-ttu-id="11f9a-260">Bij het lezen van een tekst bestand wordt met [Get-content](xref:Microsoft.PowerShell.Management.Get-Content) een verzameling teken reeks objecten geretourneerd, die elk eindigen op het scheidings teken.</span><span class="sxs-lookup"><span data-stu-id="11f9a-260">When reading a text file, [Get-Content](xref:Microsoft.PowerShell.Management.Get-Content) returns a collection of string objects, each of which ends with the delimiter character.</span></span>

<span data-ttu-id="11f9a-261">Als u een scheidings teken opgeeft dat niet in het bestand voor komt, [Get-content](xref:Microsoft.PowerShell.Management.Get-Content) retourneert het hele bestand als een enkel, niet-gescheiden object.</span><span class="sxs-lookup"><span data-stu-id="11f9a-261">Entering a delimiter that does not exist in the file, [Get-Content](xref:Microsoft.PowerShell.Management.Get-Content) returns the entire file as a single, un-delimited object.</span></span>

<span data-ttu-id="11f9a-262">U kunt deze para meter gebruiken om een groot bestand te splitsen in kleinere bestanden door een bestands scheidings teken, zoals ' einde van het voor beeld ', op te geven als scheidings teken.</span><span class="sxs-lookup"><span data-stu-id="11f9a-262">You can use this parameter to split a large file into smaller files by specifying a file separator, such as "End of Example", as the delimiter.</span></span> <span data-ttu-id="11f9a-263">Het scheidings teken wordt bewaard (niet verwijderd) en wordt het laatste item in elk bestands gedeelte.</span><span class="sxs-lookup"><span data-stu-id="11f9a-263">The delimiter is preserved (not discarded) and becomes the last item in each file section.</span></span>

> [!NOTE]
> <span data-ttu-id="11f9a-264">Wanneer de waarde van de para meter op dit moment `-Delimiter` een lege teken reeks is, retourneert [Get-content](xref:Microsoft.PowerShell.Management.Get-Content) niets.</span><span class="sxs-lookup"><span data-stu-id="11f9a-264">Currently, when the value of the `-Delimiter` parameter is an empty string, [Get-Content](xref:Microsoft.PowerShell.Management.Get-Content) does not return anything.</span></span>
> <span data-ttu-id="11f9a-265">Dit is een bekend probleem.</span><span class="sxs-lookup"><span data-stu-id="11f9a-265">This is a known issue.</span></span> <span data-ttu-id="11f9a-266">Om [Get-content](xref:Microsoft.PowerShell.Management.Get-Content) af te dwingen om het hele bestand als één undelimited teken reeks te retour neren, voert u een waarde in die niet voor komt in het bestand.</span><span class="sxs-lookup"><span data-stu-id="11f9a-266">To force [Get-Content](xref:Microsoft.PowerShell.Management.Get-Content) to return the entire file as a single, undelimited string, enter a value that does not exist in the file.</span></span>

#### <a name="cmdlets-supported"></a><span data-ttu-id="11f9a-267">Ondersteunde cmdlets</span><span class="sxs-lookup"><span data-stu-id="11f9a-267">Cmdlets supported</span></span>

- [<span data-ttu-id="11f9a-268">Get-Content</span><span class="sxs-lookup"><span data-stu-id="11f9a-268">Get-Content</span></span>](xref:Microsoft.PowerShell.Management.Get-Content)

### <a name="wait-systemmanagementautomationswitchparameter"></a><span data-ttu-id="11f9a-269">Bewerking \<System.Management.Automation.SwitchParameter\></span><span class="sxs-lookup"><span data-stu-id="11f9a-269">Wait \<System.Management.Automation.SwitchParameter\></span></span>

<span data-ttu-id="11f9a-270">Er wordt gewacht tot de inhoud aan het bestand is toegevoegd.</span><span class="sxs-lookup"><span data-stu-id="11f9a-270">Waits for content to be appended to the file.</span></span> <span data-ttu-id="11f9a-271">Als er inhoud wordt toegevoegd, wordt de toegevoegde inhoud geretourneerd.</span><span class="sxs-lookup"><span data-stu-id="11f9a-271">If content is appended, it returns the appended content.</span></span> <span data-ttu-id="11f9a-272">Als de inhoud is gewijzigd, wordt het hele bestand geretourneerd.</span><span class="sxs-lookup"><span data-stu-id="11f9a-272">If the content has changed, it returns the entire file.</span></span>

<span data-ttu-id="11f9a-273">Als er wordt gewacht, controleert de [Get-content](xref:Microsoft.PowerShell.Management.Get-Content) het bestand eenmaal per seconde totdat u het onderbreekt, bijvoorbeeld door op CTRL + C te drukken.</span><span class="sxs-lookup"><span data-stu-id="11f9a-273">When waiting, [Get-Content](xref:Microsoft.PowerShell.Management.Get-Content) checks the file once each second until you interrupt it, such as by pressing CTRL+C.</span></span>

#### <a name="cmdlets-supported"></a><span data-ttu-id="11f9a-274">Ondersteunde cmdlets</span><span class="sxs-lookup"><span data-stu-id="11f9a-274">Cmdlets supported</span></span>

- [<span data-ttu-id="11f9a-275">Get-Content</span><span class="sxs-lookup"><span data-stu-id="11f9a-275">Get-Content</span></span>](xref:Microsoft.PowerShell.Management.Get-Content)

### <a name="attributes-flagsexpression"></a><span data-ttu-id="11f9a-276">Eigenschappen \<FlagsExpression\></span><span class="sxs-lookup"><span data-stu-id="11f9a-276">Attributes \<FlagsExpression\></span></span>

<span data-ttu-id="11f9a-277">Hiermee worden bestanden en mappen opgehaald met de opgegeven kenmerken.</span><span class="sxs-lookup"><span data-stu-id="11f9a-277">Gets files and folders with the specified attributes.</span></span> <span data-ttu-id="11f9a-278">Deze para meter ondersteunt alle kenmerken en geeft u de mogelijkheid om complexe combi Naties van kenmerken op te geven.</span><span class="sxs-lookup"><span data-stu-id="11f9a-278">This parameter supports all attributes and lets you specify complex combinations of attributes.</span></span>

<span data-ttu-id="11f9a-279">De `-Attributes` para meter is geïntroduceerd in Windows Power shell 3,0.</span><span class="sxs-lookup"><span data-stu-id="11f9a-279">The `-Attributes` parameter was introduced in Windows PowerShell 3.0.</span></span>

<span data-ttu-id="11f9a-280">De `-Attributes` para meter ondersteunt de volgende kenmerken:</span><span class="sxs-lookup"><span data-stu-id="11f9a-280">The `-Attributes` parameter supports the following attributes:</span></span>

- <span data-ttu-id="11f9a-281">**Archiveren**</span><span class="sxs-lookup"><span data-stu-id="11f9a-281">**Archive**</span></span>
- <span data-ttu-id="11f9a-282">**Gecomprimeerd**</span><span class="sxs-lookup"><span data-stu-id="11f9a-282">**Compressed**</span></span>
- <span data-ttu-id="11f9a-283">**Apparaat**</span><span class="sxs-lookup"><span data-stu-id="11f9a-283">**Device**</span></span>
- <span data-ttu-id="11f9a-284">**Directory**</span><span class="sxs-lookup"><span data-stu-id="11f9a-284">**Directory**</span></span>
- <span data-ttu-id="11f9a-285">**Versleuteld**</span><span class="sxs-lookup"><span data-stu-id="11f9a-285">**Encrypted**</span></span>
- <span data-ttu-id="11f9a-286">**Verborgen**</span><span class="sxs-lookup"><span data-stu-id="11f9a-286">**Hidden**</span></span>
- <span data-ttu-id="11f9a-287">**Normaal**</span><span class="sxs-lookup"><span data-stu-id="11f9a-287">**Normal**</span></span>
- <span data-ttu-id="11f9a-288">**NotContentIndexed**</span><span class="sxs-lookup"><span data-stu-id="11f9a-288">**NotContentIndexed**</span></span>
- <span data-ttu-id="11f9a-289">**Offline**</span><span class="sxs-lookup"><span data-stu-id="11f9a-289">**Offline**</span></span>
- <span data-ttu-id="11f9a-290">**Kenmerk**</span><span class="sxs-lookup"><span data-stu-id="11f9a-290">**ReadOnly**</span></span>
- <span data-ttu-id="11f9a-291">**ReparsePoint**</span><span class="sxs-lookup"><span data-stu-id="11f9a-291">**ReparsePoint**</span></span>
- <span data-ttu-id="11f9a-292">**SparseFile**</span><span class="sxs-lookup"><span data-stu-id="11f9a-292">**SparseFile**</span></span>
- <span data-ttu-id="11f9a-293">**Systeem**</span><span class="sxs-lookup"><span data-stu-id="11f9a-293">**System**</span></span>
- <span data-ttu-id="11f9a-294">**Tijdelijk**</span><span class="sxs-lookup"><span data-stu-id="11f9a-294">**Temporary**</span></span>

<span data-ttu-id="11f9a-295">Zie de [FileAttributes](/dotnet/api/system.io.fileattributes) -inventarisatie voor een beschrijving van deze kenmerken.</span><span class="sxs-lookup"><span data-stu-id="11f9a-295">For a description of these attributes, see the [FileAttributes](/dotnet/api/system.io.fileattributes) enumeration.</span></span>

<span data-ttu-id="11f9a-296">Gebruik de volgende Opera tors om kenmerken te combi neren.</span><span class="sxs-lookup"><span data-stu-id="11f9a-296">Use the following operators to combine attributes.</span></span>

- <span data-ttu-id="11f9a-297">`!` -NIET</span><span class="sxs-lookup"><span data-stu-id="11f9a-297">`!` - NOT</span></span>
- <span data-ttu-id="11f9a-298">`+` -EN</span><span class="sxs-lookup"><span data-stu-id="11f9a-298">`+` - AND</span></span>
- <span data-ttu-id="11f9a-299">`,` -OF</span><span class="sxs-lookup"><span data-stu-id="11f9a-299">`,` - OR</span></span>

<span data-ttu-id="11f9a-300">Er zijn geen spaties toegestaan tussen een operator en het bijbehorende kenmerk.</span><span class="sxs-lookup"><span data-stu-id="11f9a-300">No spaces are permitted between an operator and its attribute.</span></span> <span data-ttu-id="11f9a-301">Spaties zijn echter toegestaan vóór komma's.</span><span class="sxs-lookup"><span data-stu-id="11f9a-301">However, spaces are permitted before commas.</span></span>

#### <a name="cmdlets-supported"></a><span data-ttu-id="11f9a-302">Ondersteunde cmdlets</span><span class="sxs-lookup"><span data-stu-id="11f9a-302">Cmdlets supported</span></span>

- [<span data-ttu-id="11f9a-303">Get-Child item</span><span class="sxs-lookup"><span data-stu-id="11f9a-303">Get-ChildItem</span></span>](xref:Microsoft.PowerShell.Management.Get-ChildItem)

### <a name="directory-systemmanagementautomationswitchparameter"></a><span data-ttu-id="11f9a-304">Uitvoermap \<System.Management.Automation.SwitchParameter\></span><span class="sxs-lookup"><span data-stu-id="11f9a-304">Directory \<System.Management.Automation.SwitchParameter\></span></span>

<span data-ttu-id="11f9a-305">Haalt mappen (mappen) op.</span><span class="sxs-lookup"><span data-stu-id="11f9a-305">Gets directories (folders).</span></span>

<span data-ttu-id="11f9a-306">De `-Directory` para meter is geïntroduceerd in Windows Power shell 3,0.</span><span class="sxs-lookup"><span data-stu-id="11f9a-306">The `-Directory` parameter was introduced in Windows PowerShell 3.0.</span></span>

<span data-ttu-id="11f9a-307">Als u alleen mappen wilt ophalen, gebruikt u de `-Directory` para meter en laat u de `-File` para meter weg.</span><span class="sxs-lookup"><span data-stu-id="11f9a-307">To get only directories, use the `-Directory` parameter and omit the `-File` parameter.</span></span> <span data-ttu-id="11f9a-308">Als u directory's wilt uitsluiten, gebruikt u de `-File` para meter en laat u de `-Directory` para meter weg of gebruikt u de `-Attributes` para meter.</span><span class="sxs-lookup"><span data-stu-id="11f9a-308">To exclude directories, use the `-File` parameter and omit the `-Directory` parameter, or use the `-Attributes` parameter.</span></span>

#### <a name="cmdlets-supported"></a><span data-ttu-id="11f9a-309">Ondersteunde cmdlets</span><span class="sxs-lookup"><span data-stu-id="11f9a-309">Cmdlets supported</span></span>

- [<span data-ttu-id="11f9a-310">Get-Child item</span><span class="sxs-lookup"><span data-stu-id="11f9a-310">Get-ChildItem</span></span>](xref:Microsoft.PowerShell.Management.Get-ChildItem)

### <a name="file-systemmanagementautomationswitchparameter"></a><span data-ttu-id="11f9a-311">Profiler \<System.Management.Automation.SwitchParameter\></span><span class="sxs-lookup"><span data-stu-id="11f9a-311">File \<System.Management.Automation.SwitchParameter\></span></span>

<span data-ttu-id="11f9a-312">Haalt bestanden op.</span><span class="sxs-lookup"><span data-stu-id="11f9a-312">Gets files.</span></span>

<span data-ttu-id="11f9a-313">De `-File` para meter is geïntroduceerd in Windows Power shell 3,0.</span><span class="sxs-lookup"><span data-stu-id="11f9a-313">The `-File` parameter was introduced in Windows PowerShell 3.0.</span></span>

<span data-ttu-id="11f9a-314">Als u alleen bestanden wilt ophalen, gebruikt u de `-File` para meter en laat u de `-Directory` para meter weg.</span><span class="sxs-lookup"><span data-stu-id="11f9a-314">To get only files, use the `-File` parameter and omit the `-Directory` parameter.</span></span> <span data-ttu-id="11f9a-315">Als u bestanden wilt uitsluiten, gebruikt u de `-Directory` para meter en laat u de `-File` para meter weg of gebruikt u de `-Attributes` para meter.</span><span class="sxs-lookup"><span data-stu-id="11f9a-315">To exclude files, use the `-Directory` parameter and omit the `-File` parameter, or use the `-Attributes` parameter.</span></span>

#### <a name="cmdlets-supported"></a><span data-ttu-id="11f9a-316">Ondersteunde cmdlets</span><span class="sxs-lookup"><span data-stu-id="11f9a-316">Cmdlets supported</span></span>

- [<span data-ttu-id="11f9a-317">Get-Child item</span><span class="sxs-lookup"><span data-stu-id="11f9a-317">Get-ChildItem</span></span>](xref:Microsoft.PowerShell.Management.Get-ChildItem)

### <a name="hidden-systemmanagementautomationswitchparameter"></a><span data-ttu-id="11f9a-318">Zit \<System.Management.Automation.SwitchParameter\></span><span class="sxs-lookup"><span data-stu-id="11f9a-318">Hidden \<System.Management.Automation.SwitchParameter\></span></span>

<span data-ttu-id="11f9a-319">Hiermee worden alleen verborgen bestanden en mappen (mappen) opgehaald.</span><span class="sxs-lookup"><span data-stu-id="11f9a-319">Gets only hidden files and directories (folders).</span></span> <span data-ttu-id="11f9a-320">[Get-Child item](xref:Microsoft.PowerShell.Management.Get-ChildItem) haalt standaard alleen niet-verborgen items op.</span><span class="sxs-lookup"><span data-stu-id="11f9a-320">By default, [Get-ChildItem](xref:Microsoft.PowerShell.Management.Get-ChildItem) gets only non-hidden items.</span></span>

<span data-ttu-id="11f9a-321">De `-Hidden` para meter is geïntroduceerd in Windows Power shell 3,0.</span><span class="sxs-lookup"><span data-stu-id="11f9a-321">The `-Hidden` parameter was introduced in Windows PowerShell 3.0.</span></span>

<span data-ttu-id="11f9a-322">Als u alleen verborgen items wilt ophalen, gebruikt u de `-Hidden` para meter, de `h` `ah` aliassen of de **verborgen** waarde van de `-Attributes` para meter.</span><span class="sxs-lookup"><span data-stu-id="11f9a-322">To get only hidden items, use the `-Hidden` parameter, its `h` or `ah` aliases, or the **Hidden** value of the `-Attributes` parameter.</span></span> <span data-ttu-id="11f9a-323">Als u verborgen items wilt uitsluiten, laat u de `-Hidden` para meter weg of gebruikt u de `-Attributes` para meter.</span><span class="sxs-lookup"><span data-stu-id="11f9a-323">To exclude hidden items, omit the `-Hidden` parameter or use the `-Attributes` parameter.</span></span>

#### <a name="cmdlets-supported"></a><span data-ttu-id="11f9a-324">Ondersteunde cmdlets</span><span class="sxs-lookup"><span data-stu-id="11f9a-324">Cmdlets supported</span></span>

- [<span data-ttu-id="11f9a-325">Get-Child item</span><span class="sxs-lookup"><span data-stu-id="11f9a-325">Get-ChildItem</span></span>](xref:Microsoft.PowerShell.Management.Get-ChildItem)

### <a name="readonly-systemmanagementautomationswitchparameter"></a><span data-ttu-id="11f9a-326">Kenmerk \<System.Management.Automation.SwitchParameter\></span><span class="sxs-lookup"><span data-stu-id="11f9a-326">ReadOnly \<System.Management.Automation.SwitchParameter\></span></span>

<span data-ttu-id="11f9a-327">Hiermee worden alleen alleen-lezen bestanden en mappen (mappen) opgehaald.</span><span class="sxs-lookup"><span data-stu-id="11f9a-327">Gets only read-only files and directories (folders).</span></span>

<span data-ttu-id="11f9a-328">De `-ReadOnly` para meter is geïntroduceerd in Windows Power shell 3,0.</span><span class="sxs-lookup"><span data-stu-id="11f9a-328">The `-ReadOnly` parameter was introduced in Windows PowerShell 3.0.</span></span>

<span data-ttu-id="11f9a-329">Als u alleen-lezen items wilt ophalen, gebruikt u de `-ReadOnly` para meter, de `ar` alias of de **ReadOnly** -waarde van de `-Attributes` para meter.</span><span class="sxs-lookup"><span data-stu-id="11f9a-329">To get only read-only items, use the `-ReadOnly` parameter, its `ar` alias, or the **ReadOnly** value of the `-Attributes` parameter.</span></span> <span data-ttu-id="11f9a-330">Als u alleen-lezen items wilt uitsluiten, gebruikt u de `-Attributes` para meter.</span><span class="sxs-lookup"><span data-stu-id="11f9a-330">To exclude read-only items, use the `-Attributes` parameter.</span></span>

#### <a name="cmdlets-supported"></a><span data-ttu-id="11f9a-331">Ondersteunde cmdlets</span><span class="sxs-lookup"><span data-stu-id="11f9a-331">Cmdlets supported</span></span>

- [<span data-ttu-id="11f9a-332">Get-Child item</span><span class="sxs-lookup"><span data-stu-id="11f9a-332">Get-ChildItem</span></span>](xref:Microsoft.PowerShell.Management.Get-ChildItem)

### <a name="system-systemmanagementautomationswitchparameter"></a><span data-ttu-id="11f9a-333">Opgehaald \<System.Management.Automation.SwitchParameter\></span><span class="sxs-lookup"><span data-stu-id="11f9a-333">System \<System.Management.Automation.SwitchParameter\></span></span>

<span data-ttu-id="11f9a-334">Hiermee worden alleen systeem bestanden en mappen (mappen) opgehaald.</span><span class="sxs-lookup"><span data-stu-id="11f9a-334">Gets only system files and directories (folders).</span></span>

<span data-ttu-id="11f9a-335">De `-System` para meter is geïntroduceerd in Windows Power shell 3,0.</span><span class="sxs-lookup"><span data-stu-id="11f9a-335">The `-System` parameter was introduced in Windows PowerShell 3.0.</span></span>

<span data-ttu-id="11f9a-336">Als u alleen systeem bestanden en-mappen wilt ophalen, gebruikt u de `-System` para meter, de `as` alias of de **systeem** waarde van de `-Attributes` para meter.</span><span class="sxs-lookup"><span data-stu-id="11f9a-336">To get only system files and folders, use the `-System` parameter, its `as` alias, or the **System** value of the `-Attributes` parameter.</span></span> <span data-ttu-id="11f9a-337">Gebruik de para meter om systeem bestanden en-mappen uit te sluiten `-Attributes` .</span><span class="sxs-lookup"><span data-stu-id="11f9a-337">To exclude system files and folders, use the `-Attributes` parameter.</span></span>

#### <a name="cmdlets-supported"></a><span data-ttu-id="11f9a-338">Ondersteunde cmdlets</span><span class="sxs-lookup"><span data-stu-id="11f9a-338">Cmdlets supported</span></span>

- [<span data-ttu-id="11f9a-339">Get-Child item</span><span class="sxs-lookup"><span data-stu-id="11f9a-339">Get-ChildItem</span></span>](xref:Microsoft.PowerShell.Management.Get-ChildItem)

### <a name="newerthan-systemdatetime"></a><span data-ttu-id="11f9a-340">NewerThan \<System.DateTime\></span><span class="sxs-lookup"><span data-stu-id="11f9a-340">NewerThan \<System.DateTime\></span></span>

<span data-ttu-id="11f9a-341">Retourneert `$True` wanneer de `LastWriteTime` waarde van een bestand groter is dan de opgegeven datum.</span><span class="sxs-lookup"><span data-stu-id="11f9a-341">Returns `$True` when the `LastWriteTime` value of a file is greater than the specified date.</span></span> <span data-ttu-id="11f9a-342">Als dat niet het geval is, wordt geretourneerd `$False` .</span><span class="sxs-lookup"><span data-stu-id="11f9a-342">Otherwise, it returns `$False`.</span></span>

<span data-ttu-id="11f9a-343">Voer een [DateTime](/dotnet/api/system.datetime) -object in, zoals een dat de cmdlet [Get-date](xref:Microsoft.PowerShell.Utility.Get-Date) retourneert, of een teken reeks die kan worden geconverteerd naar een [DateTime](/dotnet/api/system.datetime) -object, zoals `"August 10, 2011 2:00 PM"` .</span><span class="sxs-lookup"><span data-stu-id="11f9a-343">Enter a [DateTime](/dotnet/api/system.datetime) object, such as one that the [Get-Date](xref:Microsoft.PowerShell.Utility.Get-Date) cmdlet returns, or a string that can be converted to a [DateTime](/dotnet/api/system.datetime) object, such as `"August 10, 2011 2:00 PM"`.</span></span>

#### <a name="cmdlets-supported"></a><span data-ttu-id="11f9a-344">Ondersteunde cmdlets</span><span class="sxs-lookup"><span data-stu-id="11f9a-344">Cmdlets supported</span></span>

- [<span data-ttu-id="11f9a-345">Test-pad</span><span class="sxs-lookup"><span data-stu-id="11f9a-345">Test-Path</span></span>](xref:Microsoft.PowerShell.Management.Test-Path)

### <a name="olderthan-systemdatetime"></a><span data-ttu-id="11f9a-346">OlderThan \<System.DateTime\></span><span class="sxs-lookup"><span data-stu-id="11f9a-346">OlderThan \<System.DateTime\></span></span>

<span data-ttu-id="11f9a-347">Retourneert `$True` wanneer de `LastWriteTime` waarde van een bestand kleiner is dan de opgegeven datum.</span><span class="sxs-lookup"><span data-stu-id="11f9a-347">Returns `$True` when the `LastWriteTime` value of a file is less than the specified date.</span></span> <span data-ttu-id="11f9a-348">Als dat niet het geval is, wordt geretourneerd `$False` .</span><span class="sxs-lookup"><span data-stu-id="11f9a-348">Otherwise, it returns `$False`.</span></span>

<span data-ttu-id="11f9a-349">Voer een [DateTime](/dotnet/api/system.datetime) -object in, zoals een dat de cmdlet [Get-date](xref:Microsoft.PowerShell.Utility.Get-Date) retourneert, of een teken reeks die kan worden geconverteerd naar een [DateTime](/dotnet/api/system.datetime) -object, zoals `"August 10, 2011 2:00 PM"` .</span><span class="sxs-lookup"><span data-stu-id="11f9a-349">Enter a [DateTime](/dotnet/api/system.datetime) object, such as one that the [Get-Date](xref:Microsoft.PowerShell.Utility.Get-Date) cmdlet returns, or a string that can be converted to a [DateTime](/dotnet/api/system.datetime) object, such as `"August 10, 2011 2:00 PM"`.</span></span>

#### <a name="cmdlets-supported"></a><span data-ttu-id="11f9a-350">Ondersteunde cmdlets</span><span class="sxs-lookup"><span data-stu-id="11f9a-350">Cmdlets supported</span></span>

- [<span data-ttu-id="11f9a-351">Test-pad</span><span class="sxs-lookup"><span data-stu-id="11f9a-351">Test-Path</span></span>](xref:Microsoft.PowerShell.Management.Test-Path)

### <a name="stream-systemstring"></a><span data-ttu-id="11f9a-352">Bitsnelheid \<System.String\></span><span class="sxs-lookup"><span data-stu-id="11f9a-352">Stream \<System.String\></span></span>

<span data-ttu-id="11f9a-353">Hiermee beheert u alternatieve gegevens stromen.</span><span class="sxs-lookup"><span data-stu-id="11f9a-353">Manages alternate data streams.</span></span> <span data-ttu-id="11f9a-354">Voer de naam van de stream in.</span><span class="sxs-lookup"><span data-stu-id="11f9a-354">Enter the stream name.</span></span> <span data-ttu-id="11f9a-355">Joker tekens zijn alleen toegestaan in opdrachten [Get-item](xref:Microsoft.PowerShell.Management.Get-Item) for en [Remove item](xref:Microsoft.PowerShell.Management.Remove-Item) in een bestandssysteem station.</span><span class="sxs-lookup"><span data-stu-id="11f9a-355">Wildcards are permitted only in [Get-Item](xref:Microsoft.PowerShell.Management.Get-Item) for and [Remove-Item](xref:Microsoft.PowerShell.Management.Remove-Item) commands in a file system drive.</span></span>

#### <a name="cmdlets-supported"></a><span data-ttu-id="11f9a-356">Ondersteunde cmdlets</span><span class="sxs-lookup"><span data-stu-id="11f9a-356">Cmdlets supported</span></span>

- [<span data-ttu-id="11f9a-357">Add-content</span><span class="sxs-lookup"><span data-stu-id="11f9a-357">Add-Content</span></span>](xref:Microsoft.PowerShell.Management.Add-Content)
- [<span data-ttu-id="11f9a-358">Wissen-inhoud</span><span class="sxs-lookup"><span data-stu-id="11f9a-358">Clear-Content</span></span>](xref:Microsoft.PowerShell.Management.Clear-Content)
- [<span data-ttu-id="11f9a-359">Get-item</span><span class="sxs-lookup"><span data-stu-id="11f9a-359">Get-Item</span></span>](xref:Microsoft.PowerShell.Management.Get-Item)
- [<span data-ttu-id="11f9a-360">Get-Content</span><span class="sxs-lookup"><span data-stu-id="11f9a-360">Get-Content</span></span>](xref:Microsoft.PowerShell.Management.Get-Content)
- [<span data-ttu-id="11f9a-361">Verwijderen-item</span><span class="sxs-lookup"><span data-stu-id="11f9a-361">Remove-Item</span></span>](xref:Microsoft.PowerShell.Management.Remove-Item)
- [<span data-ttu-id="11f9a-362">Set-Content</span><span class="sxs-lookup"><span data-stu-id="11f9a-362">Set-Content</span></span>](xref:Microsoft.PowerShell.Management.Set-Content)

### <a name="raw-switchparameter"></a><span data-ttu-id="11f9a-363">Uitgang \<SwitchParameter\></span><span class="sxs-lookup"><span data-stu-id="11f9a-363">Raw \<SwitchParameter\></span></span>

<span data-ttu-id="11f9a-364">Hiermee worden de tekens voor nieuwe regels genegeerd.</span><span class="sxs-lookup"><span data-stu-id="11f9a-364">Ignores newline characters.</span></span> <span data-ttu-id="11f9a-365">Retourneert inhoud als één item.</span><span class="sxs-lookup"><span data-stu-id="11f9a-365">Returns contents as a single item.</span></span>

#### <a name="cmdlets-supported"></a><span data-ttu-id="11f9a-366">Ondersteunde cmdlets</span><span class="sxs-lookup"><span data-stu-id="11f9a-366">Cmdlets supported</span></span>

- [<span data-ttu-id="11f9a-367">Get-Content</span><span class="sxs-lookup"><span data-stu-id="11f9a-367">Get-Content</span></span>](xref:Microsoft.PowerShell.Management.Get-Content)

### <a name="itemtype-string"></a><span data-ttu-id="11f9a-368">Item type \<String\></span><span class="sxs-lookup"><span data-stu-id="11f9a-368">ItemType \<String\></span></span>

<span data-ttu-id="11f9a-369">Met deze para meter kunt u de Tye opgeven van het item dat moet worden gemaakt met `New-Item`</span><span class="sxs-lookup"><span data-stu-id="11f9a-369">This parameter allows you to specify the tye of item to create with `New-Item`</span></span>

<span data-ttu-id="11f9a-370">De beschik bare waarden van deze para meter zijn afhankelijk van de huidige provider die u gebruikt.</span><span class="sxs-lookup"><span data-stu-id="11f9a-370">The available values of this parameter depend on the current provider you are using.</span></span>

<span data-ttu-id="11f9a-371">In een `FileSystem` station zijn de volgende waarden toegestaan:</span><span class="sxs-lookup"><span data-stu-id="11f9a-371">In a `FileSystem` drive, the following values are allowed:</span></span>

- <span data-ttu-id="11f9a-372">Bestand</span><span class="sxs-lookup"><span data-stu-id="11f9a-372">File</span></span>
- <span data-ttu-id="11f9a-373">Directory</span><span class="sxs-lookup"><span data-stu-id="11f9a-373">Directory</span></span>
- <span data-ttu-id="11f9a-374">SymbolicLink</span><span class="sxs-lookup"><span data-stu-id="11f9a-374">SymbolicLink</span></span>
- <span data-ttu-id="11f9a-375">Verbinding</span><span class="sxs-lookup"><span data-stu-id="11f9a-375">Junction</span></span>
- <span data-ttu-id="11f9a-376">Hard link</span><span class="sxs-lookup"><span data-stu-id="11f9a-376">HardLink</span></span>

### <a name="cmdlets-supported"></a><span data-ttu-id="11f9a-377">Ondersteunde cmdlets</span><span class="sxs-lookup"><span data-stu-id="11f9a-377">Cmdlets supported</span></span>

- [<span data-ttu-id="11f9a-378">Nieuw-item</span><span class="sxs-lookup"><span data-stu-id="11f9a-378">New-Item</span></span>](xref:Microsoft.PowerShell.Management.New-Item)

## <a name="using-the-pipeline"></a><span data-ttu-id="11f9a-379">De pijp lijn gebruiken</span><span class="sxs-lookup"><span data-stu-id="11f9a-379">Using the pipeline</span></span>

<span data-ttu-id="11f9a-380">Provider-cmdlets accepteren de invoer van de pijp lijn.</span><span class="sxs-lookup"><span data-stu-id="11f9a-380">Provider cmdlets accept pipeline input.</span></span> <span data-ttu-id="11f9a-381">U kunt de pijp lijn gebruiken om de taak te vereenvoudigen door provider gegevens van de ene cmdlet naar een andere provider-cmdlet te verzenden.</span><span class="sxs-lookup"><span data-stu-id="11f9a-381">You can use the pipeline to simplify task by sending provider data from one cmdlet to another provider cmdlet.</span></span>
<span data-ttu-id="11f9a-382">Zie de cmdlet-verwijzingen die in dit artikel worden vermeld voor meer informatie over het gebruik van de pijp lijn met provider-cmdlets.</span><span class="sxs-lookup"><span data-stu-id="11f9a-382">To read more about how to use the pipeline with provider cmdlets, see the cmdlet references provided throughout this article.</span></span>

## <a name="getting-help"></a><span data-ttu-id="11f9a-383">Ondersteuning vragen</span><span class="sxs-lookup"><span data-stu-id="11f9a-383">Getting help</span></span>

<span data-ttu-id="11f9a-384">Vanaf Windows Power Shell 3,0 kunt u aangepaste Help-onderwerpen voor provider-cmdlets krijgen waarin wordt uitgelegd hoe deze cmdlets zich gedragen in een bestandssysteem station.</span><span class="sxs-lookup"><span data-stu-id="11f9a-384">Beginning in Windows PowerShell 3.0, you can get customized help topics for provider cmdlets that explain how those cmdlets behave in a file system drive.</span></span>

<span data-ttu-id="11f9a-385">Als u de Help-onderwerpen wilt ophalen die zijn aangepast voor het bestandssysteem station, voert u de opdracht [Get-Help](xref:Microsoft.PowerShell.Core.Get-Help) uit in een bestandssysteem station of gebruikt `-Path` u de para meter [Get-Help](xref:Microsoft.PowerShell.Core.Get-Help) om een bestandssysteem station op te geven.</span><span class="sxs-lookup"><span data-stu-id="11f9a-385">To get the help topics that are customized for the file system drive, run a [Get-Help](xref:Microsoft.PowerShell.Core.Get-Help) command in a file system drive or use the `-Path` parameter of [Get-Help](xref:Microsoft.PowerShell.Core.Get-Help) to specify a file system drive.</span></span>

```powershell
Get-Help Get-ChildItem
```

```powershell
Get-Help Get-ChildItem -Path c:
```

## <a name="see-also"></a><span data-ttu-id="11f9a-386">Zie ook</span><span class="sxs-lookup"><span data-stu-id="11f9a-386">See also</span></span>

[<span data-ttu-id="11f9a-387">about_Providers</span><span class="sxs-lookup"><span data-stu-id="11f9a-387">about_Providers</span></span>](../About/about_Providers.md)
