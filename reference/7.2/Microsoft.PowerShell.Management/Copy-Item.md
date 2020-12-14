---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 08/25/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/copy-item?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Copy-Item
ms.openlocfilehash: ee2d8b8a3b736a59b5af4a81710a0d29dd2238d5
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 11/17/2020
ms.locfileid: "94705743"
---
# <span data-ttu-id="fa189-102">Copy-Item</span><span class="sxs-lookup"><span data-stu-id="fa189-102">Copy-Item</span></span>

## <span data-ttu-id="fa189-103">SAMENVATTING</span><span class="sxs-lookup"><span data-stu-id="fa189-103">SYNOPSIS</span></span>
<span data-ttu-id="fa189-104">Hiermee wordt een item gekopieerd van de ene locatie naar een andere.</span><span class="sxs-lookup"><span data-stu-id="fa189-104">Copies an item from one location to another.</span></span>

## <span data-ttu-id="fa189-105">SYNTAXIS</span><span class="sxs-lookup"><span data-stu-id="fa189-105">SYNTAX</span></span>

### <span data-ttu-id="fa189-106">Pad (standaard)</span><span class="sxs-lookup"><span data-stu-id="fa189-106">Path (Default)</span></span>

```
Copy-Item [-Path] <String[]> [[-Destination] <String>] [-Container] [-Force] [-Filter <String>]
 [-Include <String[]>] [-Exclude <String[]>] [-Recurse] [-PassThru] [-Credential <PSCredential>]
 [-WhatIf] [-Confirm] [-FromSession <PSSession>] [-ToSession <PSSession>] [<CommonParameters>]
```

### <span data-ttu-id="fa189-107">LiteralPath</span><span class="sxs-lookup"><span data-stu-id="fa189-107">LiteralPath</span></span>

```
Copy-Item -LiteralPath <String[]> [[-Destination] <String>] [-Container] [-Force] [-Filter <String>]
 [-Include <String[]>] [-Exclude <String[]>] [-Recurse] [-PassThru] [-Credential <PSCredential>]
 [-WhatIf] [-Confirm] [-FromSession <PSSession>] [-ToSession <PSSession>] [<CommonParameters>]
```

## <span data-ttu-id="fa189-108">BESCHRIJVING</span><span class="sxs-lookup"><span data-stu-id="fa189-108">DESCRIPTION</span></span>

<span data-ttu-id="fa189-109">Met de `Copy-Item` cmdlet wordt een item gekopieerd van de ene locatie naar een andere locatie in dezelfde naam ruimte.</span><span class="sxs-lookup"><span data-stu-id="fa189-109">The `Copy-Item` cmdlet copies an item from one location to another location in the same namespace.</span></span>
<span data-ttu-id="fa189-110">Het kan bijvoorbeeld een bestand kopiëren naar een map, maar het bestand kan niet worden gekopieerd naar een certificaat station.</span><span class="sxs-lookup"><span data-stu-id="fa189-110">For instance, it can copy a file to a folder, but it can't copy a file to a certificate drive.</span></span>

<span data-ttu-id="fa189-111">Met deze cmdlet worden de gekopieerde items niet geknipt of verwijderd.</span><span class="sxs-lookup"><span data-stu-id="fa189-111">This cmdlet doesn't cut or delete the items being copied.</span></span> <span data-ttu-id="fa189-112">De specifieke items die de cmdlet kan kopiëren, zijn afhankelijk van de Power shell-provider die het item beschikbaar maakt.</span><span class="sxs-lookup"><span data-stu-id="fa189-112">The particular items that the cmdlet can copy depend on the PowerShell provider that exposes the item.</span></span> <span data-ttu-id="fa189-113">Zo kunnen ze bestanden en mappen in een bestandssysteem station en register sleutels en vermeldingen in het register station kopiëren.</span><span class="sxs-lookup"><span data-stu-id="fa189-113">For instance, it can copy files and directories in a file system drive and registry keys and entries in the registry drive.</span></span>

<span data-ttu-id="fa189-114">Met deze cmdlet kunt u items in dezelfde opdracht kopiëren en een andere naam geven.</span><span class="sxs-lookup"><span data-stu-id="fa189-114">This cmdlet can copy and rename items in the same command.</span></span> <span data-ttu-id="fa189-115">Als u de naam van een item wilt wijzigen, voert u de nieuwe naam in de waarde van de para meter **doel** .</span><span class="sxs-lookup"><span data-stu-id="fa189-115">To rename an item, enter the new name in the value of the **Destination** parameter.</span></span> <span data-ttu-id="fa189-116">Als u de naam van een item wilt wijzigen en dit niet wilt kopiëren, gebruikt u de `Rename-Item` cmdlet.</span><span class="sxs-lookup"><span data-stu-id="fa189-116">To rename an item and not copy it, use the `Rename-Item` cmdlet.</span></span>

## <span data-ttu-id="fa189-117">VOORBEELDEN</span><span class="sxs-lookup"><span data-stu-id="fa189-117">EXAMPLES</span></span>

### <span data-ttu-id="fa189-118">Voor beeld 1: een bestand kopiëren naar de opgegeven map</span><span class="sxs-lookup"><span data-stu-id="fa189-118">Example 1: Copy a file to the specified directory</span></span>

<span data-ttu-id="fa189-119">In dit voor beeld wordt het `mar1604.log.txt` bestand naar de `C:\Presentation` map gekopieerd.</span><span class="sxs-lookup"><span data-stu-id="fa189-119">This example copies the `mar1604.log.txt` file to the `C:\Presentation` directory.</span></span> <span data-ttu-id="fa189-120">Het oorspronkelijke bestand wordt niet verwijderd.</span><span class="sxs-lookup"><span data-stu-id="fa189-120">The original file isn't deleted.</span></span>

```powershell
Copy-Item "C:\Wabash\Logfiles\mar1604.log.txt" -Destination "C:\Presentation"
```

### <span data-ttu-id="fa189-121">Voor beeld 2: Mapinhoud kopiëren naar een bestaande map</span><span class="sxs-lookup"><span data-stu-id="fa189-121">Example 2: Copy directory contents to an existing directory</span></span>

<span data-ttu-id="fa189-122">In dit voor beeld wordt de inhoud van de `C:\Logfiles` map gekopieerd naar de bestaande `C:\Drawings` map.</span><span class="sxs-lookup"><span data-stu-id="fa189-122">This example copies the contents of the `C:\Logfiles` directory into the existing `C:\Drawings` directory.</span></span> <span data-ttu-id="fa189-123">De `Logfiles` map wordt niet gekopieerd.</span><span class="sxs-lookup"><span data-stu-id="fa189-123">The `Logfiles` directory isn't copied.</span></span>

<span data-ttu-id="fa189-124">Als de `Logfiles` map bestanden bevat in submappen, worden deze submappen met hun bestands structuren intact gekopieerd.</span><span class="sxs-lookup"><span data-stu-id="fa189-124">If the `Logfiles` directory contains files in subdirectories, those subdirectories are copied with their file trees intact.</span></span> <span data-ttu-id="fa189-125">Standaard is de **container** parameter ingesteld op **True**, waarmee de mapstructuur wordt behouden.</span><span class="sxs-lookup"><span data-stu-id="fa189-125">By default, the **Container** parameter is set to **True**, which preserves the directory structure.</span></span>

```powershell
Copy-Item -Path "C:\Logfiles\*" -Destination "C:\Drawings" -Recurse
```

> [!NOTE]
> <span data-ttu-id="fa189-126">Als u de map wilt toevoegen aan `Logfiles` de kopie, verwijdert u de `\*` uit het **pad**.</span><span class="sxs-lookup"><span data-stu-id="fa189-126">If you need to include the `Logfiles` directory in the copy, remove the `\*` from the **Path**.</span></span>
> <span data-ttu-id="fa189-127">Bijvoorbeeld:</span><span class="sxs-lookup"><span data-stu-id="fa189-127">For example:</span></span>
>
> `Copy-Item -Path "C:\Logfiles" -Destination "C:\Drawings" -Recurse`

### <span data-ttu-id="fa189-128">Voor beeld 3: Directory en inhoud kopiëren naar een nieuwe map</span><span class="sxs-lookup"><span data-stu-id="fa189-128">Example 3: Copy directory and contents to a new directory</span></span>

<span data-ttu-id="fa189-129">In dit voor beeld wordt de inhoud van de `C:\Logfiles` Bron Directory gekopieerd en wordt een nieuwe doelmap gemaakt.</span><span class="sxs-lookup"><span data-stu-id="fa189-129">This example copies the contents of the `C:\Logfiles` source directory and creates a new destination directory.</span></span> <span data-ttu-id="fa189-130">De nieuwe doelmap `\Logs` wordt gemaakt in `C:\Drawings` .</span><span class="sxs-lookup"><span data-stu-id="fa189-130">The new destination directory, `\Logs` is created in `C:\Drawings`.</span></span>

<span data-ttu-id="fa189-131">Als u de naam van de bron directory wilt toevoegen, kopieert u deze naar een bestaande doelmap, zoals wordt weer gegeven in **voor beeld 2**.</span><span class="sxs-lookup"><span data-stu-id="fa189-131">To include the source directory's name, copy to an existing destination directory as shown in **Example 2**.</span></span> <span data-ttu-id="fa189-132">U kunt ook de nieuwe doelmap een naam hebben die overeenkomt met die van de bron directory.</span><span class="sxs-lookup"><span data-stu-id="fa189-132">Or, name the new destination directory with the same as the source directory.</span></span>

```powershell
Copy-Item -Path "C:\Logfiles" -Destination "C:\Drawings\Logs" -Recurse
```

> [!NOTE]
> <span data-ttu-id="fa189-133">Als het **pad** bevat `\*` , wordt de bestands inhoud van de map, met inbegrip van de mapstructuur structuren, gekopieerd naar de nieuwe doelmap.</span><span class="sxs-lookup"><span data-stu-id="fa189-133">If the **Path** includes `\*`, all the directory's file contents, including the subdirectory trees, are copied to the new destination directory.</span></span> <span data-ttu-id="fa189-134">Bijvoorbeeld:</span><span class="sxs-lookup"><span data-stu-id="fa189-134">For example:</span></span>
>
> `Copy-Item -Path "C:\Logfiles\*" -Destination "C:\Drawings\Logs" -Recurse`

### <span data-ttu-id="fa189-135">Voor beeld 4: een bestand kopiëren naar de opgegeven map en de naam van het bestand wijzigen</span><span class="sxs-lookup"><span data-stu-id="fa189-135">Example 4: Copy a file to the specified directory and rename the file</span></span>

<span data-ttu-id="fa189-136">In dit voor beeld wordt de `Copy-Item` cmdlet gebruikt om het `Get-Widget.ps1` script uit de `\\Server01\Share` Directory naar de map te kopiëren `\\Server12\ScriptArchive` .</span><span class="sxs-lookup"><span data-stu-id="fa189-136">This example uses the `Copy-Item` cmdlet to copy the `Get-Widget.ps1` script from the `\\Server01\Share` directory to the `\\Server12\ScriptArchive` directory.</span></span> <span data-ttu-id="fa189-137">Als onderdeel van de Kopieer bewerking wijzigt de opdracht de item naam van `Get-Widget.ps1` in `Get-Widget.ps1.txt` , zodat deze kan worden toegevoegd aan e-mail berichten.</span><span class="sxs-lookup"><span data-stu-id="fa189-137">As part of the copy operation, the command changes the item name from `Get-Widget.ps1` to `Get-Widget.ps1.txt`, so it can be attached to email messages.</span></span>

```powershell
Copy-Item "\\Server01\Share\Get-Widget.ps1" -Destination "\\Server12\ScriptArchive\Get-Widget.ps1.txt"
```

### <span data-ttu-id="fa189-138">Voor beeld 5: een bestand naar een externe computer kopiëren</span><span class="sxs-lookup"><span data-stu-id="fa189-138">Example 5: Copy a file to a remote computer</span></span>

<span data-ttu-id="fa189-139">Er wordt een sessie gemaakt met de externe computer met de naam **Server01** met de referentie van `Contoso\User01` en worden de resultaten opgeslagen in de variabele met de naam `$Session` .</span><span class="sxs-lookup"><span data-stu-id="fa189-139">A session is created to the remote computer named **Server01** with the credential of `Contoso\User01` and stores the results in the variable named `$Session`.</span></span>

<span data-ttu-id="fa189-140">De `Copy-Item` cmdlet kopieert `test.log` vanuit de `D:\Folder001` map naar de `C:\Folder001_Copy` map op de externe computer met behulp van de sessie-informatie die is opgeslagen in de `$Session` variabele.</span><span class="sxs-lookup"><span data-stu-id="fa189-140">The `Copy-Item` cmdlet copies `test.log` from the `D:\Folder001` folder to the `C:\Folder001_Copy` folder on the remote computer using the session information stored in the `$Session` variable.</span></span> <span data-ttu-id="fa189-141">Het oorspronkelijke bestand wordt niet verwijderd.</span><span class="sxs-lookup"><span data-stu-id="fa189-141">The original file isn't deleted.</span></span>

```powershell
$Session = New-PSSession -ComputerName "Server01" -Credential "Contoso\User01"
Copy-Item "D:\Folder001\test.log" -Destination "C:\Folder001_Copy\" -ToSession $Session
```

### <span data-ttu-id="fa189-142">Voor beeld 6: een map naar een externe computer kopiëren</span><span class="sxs-lookup"><span data-stu-id="fa189-142">Example 6: Copy a folder to a remote computer</span></span>

<span data-ttu-id="fa189-143">Er wordt een sessie gemaakt met de externe computer met de naam **Server01** met de referentie van `Contoso\User01` en worden de resultaten opgeslagen in de variabele met de naam `$Session` .</span><span class="sxs-lookup"><span data-stu-id="fa189-143">A session is created to the remote computer named **Server01** with the credential of `Contoso\User01` and stores the results in the variable named `$Session`.</span></span>

<span data-ttu-id="fa189-144">De `Copy-Item` cmdlet kopieert de `D:\Folder002` map naar de `C:\Folder002_Copy` map op de externe computer met behulp van de sessie-informatie die is opgeslagen in de `$Session` variabele.</span><span class="sxs-lookup"><span data-stu-id="fa189-144">The `Copy-Item` cmdlet copies the `D:\Folder002` folder to the `C:\Folder002_Copy` directory on the remote computer using the session information stored in the `$Session` variable.</span></span> <span data-ttu-id="fa189-145">Submappen of bestanden worden niet gekopieerd zonder de **recursieve** switch te gebruiken.</span><span class="sxs-lookup"><span data-stu-id="fa189-145">Any subfolders or files are not copied without using the **Recurse** switch.</span></span>
<span data-ttu-id="fa189-146">Met deze bewerking wordt de `Folder002_Copy` map gemaakt als deze nog niet bestaat.</span><span class="sxs-lookup"><span data-stu-id="fa189-146">The operation creates the `Folder002_Copy` folder if it doesn't already exist.</span></span>

```powershell
$Session = New-PSSession -ComputerName "Server02" -Credential "Contoso\User01"
Copy-Item "D:\Folder002\" -Destination "C:\Folder002_Copy\" -ToSession $Session
```

### <span data-ttu-id="fa189-147">Voor beeld 7: de volledige inhoud van een map recursief kopiëren naar een externe computer</span><span class="sxs-lookup"><span data-stu-id="fa189-147">Example 7: Recursively copy the entire contents of a folder to a remote computer</span></span>

<span data-ttu-id="fa189-148">Er wordt een sessie gemaakt met de externe computer met de naam **Server01** met de referentie van `Contoso\User01` en worden de resultaten opgeslagen in de variabele met de naam `$Session` .</span><span class="sxs-lookup"><span data-stu-id="fa189-148">A session is created to the remote computer named **Server01** with the credential of `Contoso\User01` and stores the results in the variable named `$Session`.</span></span>

<span data-ttu-id="fa189-149">`Copy-Item`Met de cmdlet wordt de volledige inhoud van de `D:\Folder003` map gekopieerd naar de `C:\Folder003_Copy` map op de externe computer met behulp van de sessie-informatie die is opgeslagen in de `$Session` variabele.</span><span class="sxs-lookup"><span data-stu-id="fa189-149">The `Copy-Item` cmdlet copies the entire contents from the `D:\Folder003` folder to the `C:\Folder003_Copy` directory on the remote computer using the session information stored in the `$Session` variable.</span></span> <span data-ttu-id="fa189-150">De submappen worden gekopieerd met hun bestands structuren.</span><span class="sxs-lookup"><span data-stu-id="fa189-150">The subfolders are copied with their file trees intact.</span></span> <span data-ttu-id="fa189-151">Met deze bewerking wordt de `Folder003_Copy` map gemaakt als deze nog niet bestaat.</span><span class="sxs-lookup"><span data-stu-id="fa189-151">The operation creates the `Folder003_Copy` folder if it doesn't already exist.</span></span>

```powershell
$Session = New-PSSession -ComputerName "Server04" -Credential "Contoso\User01"
Copy-Item "D:\Folder003\" -Destination "C:\Folder003_Copy\" -ToSession $Session -Recurse
```

### <span data-ttu-id="fa189-152">Voor beeld 8: een bestand kopiëren naar een externe computer en de naam van het bestand wijzigen</span><span class="sxs-lookup"><span data-stu-id="fa189-152">Example 8: Copy a file to a remote computer and then rename the file</span></span>

<span data-ttu-id="fa189-153">Er wordt een sessie gemaakt met de externe computer met de naam **Server01** met de referentie van `Contoso\User01` en worden de resultaten opgeslagen in de variabele met de naam `$Session` .</span><span class="sxs-lookup"><span data-stu-id="fa189-153">A session is created to the remote computer named **Server01** with the credential of `Contoso\User01` and stores the results in the variable named `$Session`.</span></span>

<span data-ttu-id="fa189-154">De `Copy-Item` cmdlet kopieert `scriptingexample.ps1` vanuit de `D:\Folder004` map naar de `C:\Folder004_Copy` map op de externe computer met behulp van de sessie-informatie die is opgeslagen in de `$Session` variabele.</span><span class="sxs-lookup"><span data-stu-id="fa189-154">The `Copy-Item` cmdlet copies `scriptingexample.ps1` from the `D:\Folder004` folder to the `C:\Folder004_Copy` folder on the remote computer using the session information stored in the `$Session` variable.</span></span> <span data-ttu-id="fa189-155">Als onderdeel van de Kopieer bewerking wijzigt de opdracht de item naam van `scriptingexample.ps1` in `scriptingexample_copy.ps1` , zodat deze kan worden toegevoegd aan e-mail berichten.</span><span class="sxs-lookup"><span data-stu-id="fa189-155">As part of the copy operation, the command changes the item name from `scriptingexample.ps1` to `scriptingexample_copy.ps1`, so it can be attached to email messages.</span></span> <span data-ttu-id="fa189-156">Het oorspronkelijke bestand wordt niet verwijderd.</span><span class="sxs-lookup"><span data-stu-id="fa189-156">The original file isn't deleted.</span></span>

```powershell
$Session = New-PSSession -ComputerName "Server04" -Credential "Contoso\User01"
Copy-Item "D:\Folder004\scriptingexample.ps1" -Destination "C:\Folder004_Copy\scriptingexample_copy.ps1" -ToSession $Session
```

### <span data-ttu-id="fa189-157">Voor beeld 9: een extern bestand naar de lokale computer kopiëren</span><span class="sxs-lookup"><span data-stu-id="fa189-157">Example 9: Copy a remote file to the local computer</span></span>

<span data-ttu-id="fa189-158">Er wordt een sessie gemaakt met de externe computer met de naam **Server01** met de referentie van `Contoso\User01` en worden de resultaten opgeslagen in de variabele met de naam `$Session` .</span><span class="sxs-lookup"><span data-stu-id="fa189-158">A session is created to the remote computer named **Server01** with the credential of `Contoso\User01` and stores the results in the variable named `$Session`.</span></span>

<span data-ttu-id="fa189-159">De `Copy-Item` cmdlet kopieert `test.log` van de externe `C:\MyRemoteData\` naar de lokale `D:\MyLocalData` map met behulp van de sessie-informatie die is opgeslagen in de `$Session` variabele.</span><span class="sxs-lookup"><span data-stu-id="fa189-159">The `Copy-Item` cmdlet copies `test.log` from the remote `C:\MyRemoteData\` to the local `D:\MyLocalData` folder using the session information stored in the `$Session` variable.</span></span> <span data-ttu-id="fa189-160">Het oorspronkelijke bestand wordt niet verwijderd.</span><span class="sxs-lookup"><span data-stu-id="fa189-160">The original file isn't deleted.</span></span>

```powershell
$Session = New-PSSession -ComputerName "Server01" -Credential "Contoso\User01"
Copy-Item "C:\MyRemoteData\test.log" -Destination "D:\MyLocalData\" -FromSession $Session
```

### <span data-ttu-id="fa189-161">Voor beeld 10: de volledige inhoud van een externe map kopiëren naar de lokale computer</span><span class="sxs-lookup"><span data-stu-id="fa189-161">Example 10: Copy the entire contents of a remote folder to the local computer</span></span>

<span data-ttu-id="fa189-162">Er wordt een sessie gemaakt met de externe computer met de naam **Server01** met de referentie van `Contoso\User01` en worden de resultaten opgeslagen in de variabele met de naam `$Session` .</span><span class="sxs-lookup"><span data-stu-id="fa189-162">A session is created to the remote computer named **Server01** with the credential of `Contoso\User01` and stores the results in the variable named `$Session`.</span></span>

<span data-ttu-id="fa189-163">`Copy-Item`Met de cmdlet wordt de volledige inhoud van de externe `C:\MyRemoteData\scripts` map gekopieerd naar de lokale `D:\MyLocalData` map met behulp van de sessie-informatie die is opgeslagen in de `$Session` variabele.</span><span class="sxs-lookup"><span data-stu-id="fa189-163">The `Copy-Item` cmdlet copies the entire contents from the remote `C:\MyRemoteData\scripts` folder to the local `D:\MyLocalData` folder using the session information stored in the `$Session` variable.</span></span> <span data-ttu-id="fa189-164">Als de map scripts bestanden bevat in submappen, worden deze submappen gekopieerd met hun bestands structuren.</span><span class="sxs-lookup"><span data-stu-id="fa189-164">If the scripts folder contains files in subfolders, those subfolders are copied with their file trees intact.</span></span>

```powershell
$Session = New-PSSession -ComputerName "Server01" -Credential "Contoso\User01"
Copy-Item "C:\MyRemoteData\scripts" -Destination "D:\MyLocalData\" -FromSession $Session
```

### <span data-ttu-id="fa189-165">Voor beeld 11: de volledige inhoud van een externe map recursief kopiëren naar de lokale computer</span><span class="sxs-lookup"><span data-stu-id="fa189-165">Example 11: Recursively copy the entire contents of a remote folder to the local computer</span></span>

<span data-ttu-id="fa189-166">Er wordt een sessie gemaakt met de externe computer met de naam **Server01** met de referentie van `Contoso\User01` en worden de resultaten opgeslagen in de variabele met de naam `$Session` .</span><span class="sxs-lookup"><span data-stu-id="fa189-166">A session is created to the remote computer named **Server01** with the credential of `Contoso\User01` and stores the results in the variable named `$Session`.</span></span>

<span data-ttu-id="fa189-167">`Copy-Item`Met de cmdlet wordt de volledige inhoud van de externe `C:\MyRemoteData\scripts` map gekopieerd naar de lokale `D:\MyLocalData\scripts` map met behulp van de sessie-informatie die is opgeslagen in de `$Session` variabele.</span><span class="sxs-lookup"><span data-stu-id="fa189-167">The `Copy-Item` cmdlet copies the entire contents from the remote `C:\MyRemoteData\scripts` folder to the local `D:\MyLocalData\scripts` folder using the session information stored in the `$Session` variable.</span></span> <span data-ttu-id="fa189-168">Omdat de **recursie** -para meter wordt gebruikt, maakt de bewerking de map scripts als deze nog niet bestaat.</span><span class="sxs-lookup"><span data-stu-id="fa189-168">Because the **Recurse** parameter is used, the operation creates the scripts folder if it doesn't already exist.</span></span> <span data-ttu-id="fa189-169">Als de map scripts bestanden bevat in submappen, worden deze submappen gekopieerd met hun bestands structuren.</span><span class="sxs-lookup"><span data-stu-id="fa189-169">If the scripts folder contains files in subfolders, those subfolders are copied with their file trees intact.</span></span>

```powershell
$Session = New-PSSession -ComputerName "Server01" -Credential "Contoso\User01"
Copy-Item "C:\MyRemoteData\scripts" -Destination "D:\MyLocalData\scripts" -FromSession $Session -Recurse
```

### <span data-ttu-id="fa189-170">Voor beeld 12: recursief kopiëren van bestanden van een mapstructuur naar de huidige map</span><span class="sxs-lookup"><span data-stu-id="fa189-170">Example 12: Recursively copy files from a folder tree into the current folder</span></span>

<span data-ttu-id="fa189-171">In dit voor beeld ziet u hoe u bestanden kopieert van een mapstructuur met meerdere niveaus naar één platte map.</span><span class="sxs-lookup"><span data-stu-id="fa189-171">This example shows how to copy files from a multilevel folder structure into a single flat folder.</span></span>
<span data-ttu-id="fa189-172">De eerste drie opdrachten tonen de bestaande mappen structuur en de inhoud van twee bestanden, beide namen `file3.txt` .</span><span class="sxs-lookup"><span data-stu-id="fa189-172">The first three commands show the existing folder structure and the contents of two files, both names `file3.txt`.</span></span>

```powershell
PS C:\temp\test> (Get-ChildItem C:\temp\tree -Recurse).FullName
C:\temp\tree\subfolder
C:\temp\tree\file1.txt
C:\temp\tree\file2.txt
C:\temp\tree\file3.txt
C:\temp\tree\subfolder\file3.txt
C:\temp\tree\subfolder\file4.txt
C:\temp\tree\subfolder\file5.txt

PS C:\temp\test> Get-Content C:\temp\tree\file3.txt
This is file3.txt in the root folder

PS C:\temp\test> Get-Content C:\temp\tree\subfolder\file3.txt
This is file3.txt in the subfolder

PS C:\temp\test> Copy-Item -Path C:\temp\tree -Filter *.txt -Recurse -Container:$false
PS C:\temp\test> (Get-ChildItem . -Recurse).FullName
C:\temp\test\subfolder
C:\temp\test\file1.txt
C:\temp\test\file2.txt
C:\temp\test\file3.txt
C:\temp\test\file4.txt
C:\temp\test\file5.txt

PS C:\temp\test> Get-Content .\file3.txt
This is file3.txt in the subfolder
```

<span data-ttu-id="fa189-173">`Copy-Item`Voor de cmdlet is de **container** parameter ingesteld op `$false` .</span><span class="sxs-lookup"><span data-stu-id="fa189-173">The `Copy-Item` cmdlet has the **Container** parameter set to `$false`.</span></span> <span data-ttu-id="fa189-174">Dit zorgt ervoor dat de inhoud van de bronmap wordt gekopieerd, maar behoudt de mappen structuur niet.</span><span class="sxs-lookup"><span data-stu-id="fa189-174">This causes the contents of the source folder to be copied but does not preserve the folder structure.</span></span> <span data-ttu-id="fa189-175">U ziet dat bestanden met dezelfde naam worden overschreven in de doelmap.</span><span class="sxs-lookup"><span data-stu-id="fa189-175">Notice that files with the same name are overwritten in the destination folder.</span></span>

## <span data-ttu-id="fa189-176">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="fa189-176">PARAMETERS</span></span>

### <span data-ttu-id="fa189-177">-Confirm</span><span class="sxs-lookup"><span data-stu-id="fa189-177">-Confirm</span></span>

<span data-ttu-id="fa189-178">Hiermee wordt u gevraagd om bevestiging voordat u de cmdlet uitvoert.</span><span class="sxs-lookup"><span data-stu-id="fa189-178">Prompts you for confirmation before running the cmdlet.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: cf

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="fa189-179">-Container</span><span class="sxs-lookup"><span data-stu-id="fa189-179">-Container</span></span>

<span data-ttu-id="fa189-180">Geeft aan dat met deze cmdlet container objecten worden bewaard tijdens de Kopieer bewerking.</span><span class="sxs-lookup"><span data-stu-id="fa189-180">Indicates that this cmdlet preserves container objects during the copy operation.</span></span> <span data-ttu-id="fa189-181">Standaard is de **container** parameter ingesteld op **True**.</span><span class="sxs-lookup"><span data-stu-id="fa189-181">By default, the **Container** parameter is set to **True**.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: True
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="fa189-182">-Credential</span><span class="sxs-lookup"><span data-stu-id="fa189-182">-Credential</span></span>

> [!NOTE]
> <span data-ttu-id="fa189-183">Deze para meter wordt niet ondersteund door providers die zijn geïnstalleerd met Power shell.</span><span class="sxs-lookup"><span data-stu-id="fa189-183">This parameter is not supported by any providers installed with PowerShell.</span></span>
> <span data-ttu-id="fa189-184">Gebruik [invoke-Command](../Microsoft.PowerShell.Core/Invoke-Command.md)om een andere gebruiker te imiteren of uw referenties te verhogen wanneer u deze cmdlet uitvoert.</span><span class="sxs-lookup"><span data-stu-id="fa189-184">To impersonate another user, or elevate your credentials when running this cmdlet, use [Invoke-Command](../Microsoft.PowerShell.Core/Invoke-Command.md).</span></span>

```yaml
Type: System.Management.Automation.PSCredential
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: Current user
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="fa189-185">-Bestemming</span><span class="sxs-lookup"><span data-stu-id="fa189-185">-Destination</span></span>

<span data-ttu-id="fa189-186">Hiermee geeft u het pad naar de nieuwe locatie.</span><span class="sxs-lookup"><span data-stu-id="fa189-186">Specifies the path to the new location.</span></span> <span data-ttu-id="fa189-187">De standaardwaarde is de huidige map.</span><span class="sxs-lookup"><span data-stu-id="fa189-187">The default is the current directory.</span></span>

<span data-ttu-id="fa189-188">Als u de naam van het item dat wordt gekopieerd, wilt wijzigen, geeft u een nieuwe naam op in de waarde van de para meter **Destination** .</span><span class="sxs-lookup"><span data-stu-id="fa189-188">To rename the item being copied, specify a new name in the value of the **Destination** parameter.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: 1
Default value: Current directory
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="fa189-189">-Uitsluiten</span><span class="sxs-lookup"><span data-stu-id="fa189-189">-Exclude</span></span>

<span data-ttu-id="fa189-190">Hiermee geeft u als een teken reeks matrix een item of items die met deze cmdlet worden uitgesloten in de bewerking.</span><span class="sxs-lookup"><span data-stu-id="fa189-190">Specifies, as a string array, an item or items that this cmdlet excludes in the operation.</span></span> <span data-ttu-id="fa189-191">De waarde van deze para meter komt in aanmerking voor de para meter **Path** .</span><span class="sxs-lookup"><span data-stu-id="fa189-191">The value of this parameter qualifies the **Path** parameter.</span></span> <span data-ttu-id="fa189-192">Voer een element of patroon van een pad in, zoals `*.txt` .</span><span class="sxs-lookup"><span data-stu-id="fa189-192">Enter a path element or pattern, such as `*.txt`.</span></span> <span data-ttu-id="fa189-193">Joker tekens zijn toegestaan.</span><span class="sxs-lookup"><span data-stu-id="fa189-193">Wildcard characters are permitted.</span></span> <span data-ttu-id="fa189-194">De **exclude** -para meter is alleen effectief wanneer de inhoud van een item wordt opgenomen, zoals `C:\Windows\*` , waarbij het Joker teken de inhoud van de `C:\Windows` map bevat.</span><span class="sxs-lookup"><span data-stu-id="fa189-194">The **Exclude** parameter is effective only when the command includes the contents of an item, such as `C:\Windows\*`, where the wildcard character specifies the contents of the `C:\Windows` directory.</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: True
```

### <span data-ttu-id="fa189-195">-Filter</span><span class="sxs-lookup"><span data-stu-id="fa189-195">-Filter</span></span>

<span data-ttu-id="fa189-196">Hiermee geeft u een filter op om de para meter **Path** te kwalificeren.</span><span class="sxs-lookup"><span data-stu-id="fa189-196">Specifies a filter to qualify the **Path** parameter.</span></span> <span data-ttu-id="fa189-197">De [File System](../Microsoft.PowerShell.Core/About/about_FileSystem_Provider.md) -provider is de enige geïnstalleerde Power shell-provider die het gebruik van filters ondersteunt.</span><span class="sxs-lookup"><span data-stu-id="fa189-197">The [FileSystem](../Microsoft.PowerShell.Core/About/about_FileSystem_Provider.md) provider is the only installed PowerShell provider that supports the use of filters.</span></span> <span data-ttu-id="fa189-198">U kunt de syntaxis voor de filter taal van het **Bestands systeem** in [about_Wildcards](../Microsoft.PowerShell.Core/About/about_Wildcards.md)vinden.</span><span class="sxs-lookup"><span data-stu-id="fa189-198">You can find the syntax for the **FileSystem** filter language in [about_Wildcards](../Microsoft.PowerShell.Core/About/about_Wildcards.md).</span></span>
<span data-ttu-id="fa189-199">Filters zijn efficiënter dan andere para meters, omdat deze door de provider worden toegepast wanneer de cmdlet de objecten ophaalt in plaats van dat Power shell de objecten heeft gefilterd nadat ze zijn opgehaald.</span><span class="sxs-lookup"><span data-stu-id="fa189-199">Filters are more efficient than other parameters, because the provider applies them when the cmdlet gets the objects rather than having PowerShell filter the objects after they're retrieved.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: True
```

### <span data-ttu-id="fa189-200">-Force</span><span class="sxs-lookup"><span data-stu-id="fa189-200">-Force</span></span>

<span data-ttu-id="fa189-201">Geeft aan dat deze cmdlet items kopieert die anders niet kunnen worden gewijzigd, zoals het kopiëren over een alleen-lezen bestand of alias.</span><span class="sxs-lookup"><span data-stu-id="fa189-201">Indicates that this cmdlet copies items that can't otherwise be changed, such as copying over a read-only file or alias.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="fa189-202">-FromSession</span><span class="sxs-lookup"><span data-stu-id="fa189-202">-FromSession</span></span>

<span data-ttu-id="fa189-203">Hiermee geeft u het **PSSession** -object op waaruit een extern bestand wordt gekopieerd.</span><span class="sxs-lookup"><span data-stu-id="fa189-203">Specifies the **PSSession** object from which a remote file is being copied.</span></span> <span data-ttu-id="fa189-204">Wanneer u deze para meter gebruikt, verwijzen de para meters **Path** en **LiteralPath** naar het lokale pad op de externe computer.</span><span class="sxs-lookup"><span data-stu-id="fa189-204">When you use this parameter, the **Path** and **LiteralPath** parameters refer to the local path on the remote machine.</span></span>

```yaml
Type: System.Management.Automation.Runspaces.PSSession
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="fa189-205">-Include</span><span class="sxs-lookup"><span data-stu-id="fa189-205">-Include</span></span>

<span data-ttu-id="fa189-206">Hiermee wordt een teken reeks matrix opgegeven, een item of items die met deze cmdlet in de bewerking zijn opgenomen.</span><span class="sxs-lookup"><span data-stu-id="fa189-206">Specifies, as a string array, an item or items that this cmdlet includes in the operation.</span></span> <span data-ttu-id="fa189-207">De waarde van deze para meter komt in aanmerking voor de para meter **Path** .</span><span class="sxs-lookup"><span data-stu-id="fa189-207">The value of this parameter qualifies the **Path** parameter.</span></span> <span data-ttu-id="fa189-208">Voer een element of patroon van een pad in, zoals `"*.txt"` .</span><span class="sxs-lookup"><span data-stu-id="fa189-208">Enter a path element or pattern, such as `"*.txt"`.</span></span> <span data-ttu-id="fa189-209">Joker tekens zijn toegestaan.</span><span class="sxs-lookup"><span data-stu-id="fa189-209">Wildcard characters are permitted.</span></span> <span data-ttu-id="fa189-210">De para meter **include** is alleen effectief wanneer de inhoud van een item wordt opgenomen, zoals `C:\Windows\*` , waarbij het Joker teken de inhoud van de `C:\Windows` map bevat.</span><span class="sxs-lookup"><span data-stu-id="fa189-210">The **Include** parameter is effective only when the command includes the contents of an item, such as `C:\Windows\*`, where the wildcard character specifies the contents of the `C:\Windows` directory.</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: True
```

### <span data-ttu-id="fa189-211">-LiteralPath</span><span class="sxs-lookup"><span data-stu-id="fa189-211">-LiteralPath</span></span>

<span data-ttu-id="fa189-212">Hiermee geeft u een pad naar een of meer locaties.</span><span class="sxs-lookup"><span data-stu-id="fa189-212">Specifies a path to one or more locations.</span></span> <span data-ttu-id="fa189-213">De waarde van **LiteralPath** wordt precies zo gebruikt als deze wordt getypt.</span><span class="sxs-lookup"><span data-stu-id="fa189-213">The value of **LiteralPath** is used exactly as it's typed.</span></span> <span data-ttu-id="fa189-214">Geen tekens worden geïnterpreteerd als joker tekens.</span><span class="sxs-lookup"><span data-stu-id="fa189-214">No characters are interpreted as wildcards.</span></span> <span data-ttu-id="fa189-215">Als het pad escape tekens bevat, plaatst u het tussen enkele aanhalings tekens.</span><span class="sxs-lookup"><span data-stu-id="fa189-215">If the path includes escape characters, enclose it in single quotation marks.</span></span> <span data-ttu-id="fa189-216">Enkele aanhalings tekens geven aan dat Power shell geen karakters interpreteert als escape reeksen.</span><span class="sxs-lookup"><span data-stu-id="fa189-216">Single quotation marks tell PowerShell not to interpret any characters as escape sequences.</span></span>

<span data-ttu-id="fa189-217">Zie [about_Quoting_Rules](../Microsoft.Powershell.Core/About/about_Quoting_Rules.md)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="fa189-217">For more information, see [about_Quoting_Rules](../Microsoft.Powershell.Core/About/about_Quoting_Rules.md).</span></span>

```yaml
Type: System.String[]
Parameter Sets: LiteralPath
Aliases: PSPath, LP

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="fa189-218">-PassThru</span><span class="sxs-lookup"><span data-stu-id="fa189-218">-PassThru</span></span>

<span data-ttu-id="fa189-219">Retourneert een object dat het item vertegenwoordigt waarmee u werkt.</span><span class="sxs-lookup"><span data-stu-id="fa189-219">Returns an object that represents the item with which you're working.</span></span> <span data-ttu-id="fa189-220">Deze cmdlet genereert standaard geen uitvoer.</span><span class="sxs-lookup"><span data-stu-id="fa189-220">By default, this cmdlet doesn't generate any output.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="fa189-221">-Path</span><span class="sxs-lookup"><span data-stu-id="fa189-221">-Path</span></span>

<span data-ttu-id="fa189-222">Hiermee wordt een teken reeks matrix opgegeven, het pad naar de items die moeten worden gekopieerd.</span><span class="sxs-lookup"><span data-stu-id="fa189-222">Specifies, as a string array, the path to the items to copy.</span></span> <span data-ttu-id="fa189-223">Joker tekens zijn toegestaan.</span><span class="sxs-lookup"><span data-stu-id="fa189-223">Wildcard characters are permitted.</span></span>

```yaml
Type: System.String[]
Parameter Sets: Path
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: True
```

### <span data-ttu-id="fa189-224">-Recursief</span><span class="sxs-lookup"><span data-stu-id="fa189-224">-Recurse</span></span>

<span data-ttu-id="fa189-225">Geeft aan dat deze cmdlet een recursieve kopie doet.</span><span class="sxs-lookup"><span data-stu-id="fa189-225">Indicates that this cmdlet does a recursive copy.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="fa189-226">-ToSession</span><span class="sxs-lookup"><span data-stu-id="fa189-226">-ToSession</span></span>

<span data-ttu-id="fa189-227">Hiermee geeft u het **PSSession** -object op waarnaar een extern bestand wordt gekopieerd.</span><span class="sxs-lookup"><span data-stu-id="fa189-227">Specifies the **PSSession** object to which a remote file is being copied.</span></span> <span data-ttu-id="fa189-228">Wanneer u deze para meter gebruikt, verwijst de para meter **Destination** naar het lokale pad op de externe computer.</span><span class="sxs-lookup"><span data-stu-id="fa189-228">When you use this parameter, the **Destination** parameter refers to the local path on the remote machine.</span></span>

```yaml
Type: System.Management.Automation.Runspaces.PSSession
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="fa189-229">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="fa189-229">-WhatIf</span></span>

<span data-ttu-id="fa189-230">Hiermee wordt weergegeven wat er zou gebeuren als u de cmdlet uitvoert.</span><span class="sxs-lookup"><span data-stu-id="fa189-230">Shows what would happen if the cmdlet runs.</span></span> <span data-ttu-id="fa189-231">De cmdlet wordt niet uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="fa189-231">The cmdlet isn't run.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: wi

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="fa189-232">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="fa189-232">CommonParameters</span></span>

<span data-ttu-id="fa189-233">Deze cmdlet biedt ondersteuning voor de algemene para meters: `-Debug` , `-ErrorAction` , `-ErrorVariable` , `-InformationAction` , `-InformationVariable` , `-OutVariable` , `-OutBuffer` , `-PipelineVariable` , `-Verbose` , `-WarningAction` en `-WarningVariable` .</span><span class="sxs-lookup"><span data-stu-id="fa189-233">This cmdlet supports the common parameters: `-Debug`, `-ErrorAction`, `-ErrorVariable`, `-InformationAction`, `-InformationVariable`, `-OutVariable`, `-OutBuffer`, `-PipelineVariable`, `-Verbose`, `-WarningAction`, and `-WarningVariable`.</span></span> <span data-ttu-id="fa189-234">Zie [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="fa189-234">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="fa189-235">INVOER</span><span class="sxs-lookup"><span data-stu-id="fa189-235">INPUTS</span></span>

### <span data-ttu-id="fa189-236">System. String</span><span class="sxs-lookup"><span data-stu-id="fa189-236">System.String</span></span>

<span data-ttu-id="fa189-237">U kunt een teken reeks met een pad naar deze cmdlet door sluizen.</span><span class="sxs-lookup"><span data-stu-id="fa189-237">You can pipe a string that contains a path to this cmdlet.</span></span>

## <span data-ttu-id="fa189-238">UITVOER</span><span class="sxs-lookup"><span data-stu-id="fa189-238">OUTPUTS</span></span>

### <span data-ttu-id="fa189-239">Geen of een object dat het gekopieerde item vertegenwoordigt</span><span class="sxs-lookup"><span data-stu-id="fa189-239">None or an object representing the copied item</span></span>

<span data-ttu-id="fa189-240">Wanneer u de para meter **PassThru** gebruikt, retourneert deze cmdlet een object dat staat voor het gekopieerde item.</span><span class="sxs-lookup"><span data-stu-id="fa189-240">When you use the **PassThru** parameter, this cmdlet returns an object that represents the copied item.</span></span> <span data-ttu-id="fa189-241">Anders wordt met deze cmdlet geen uitvoer gegenereerd.</span><span class="sxs-lookup"><span data-stu-id="fa189-241">Otherwise, this cmdlet doesn't generate any output.</span></span>

## <span data-ttu-id="fa189-242">OPMERKINGEN</span><span class="sxs-lookup"><span data-stu-id="fa189-242">NOTES</span></span>

<span data-ttu-id="fa189-243">Deze cmdlet is ontworpen om te werken met de gegevens die door elke provider worden weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="fa189-243">This cmdlet is designed to work with the data exposed by any provider.</span></span> <span data-ttu-id="fa189-244">Als u een lijst wilt weer geven van de providers die beschikbaar zijn in uw sessie, typt u `Get-PSProvider` .</span><span class="sxs-lookup"><span data-stu-id="fa189-244">To list the providers available in your session, type `Get-PSProvider`.</span></span> <span data-ttu-id="fa189-245">Zie [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="fa189-245">For more information, see [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md).</span></span>

## <span data-ttu-id="fa189-246">GERELATEERDE KOPPELINGEN</span><span class="sxs-lookup"><span data-stu-id="fa189-246">RELATED LINKS</span></span>

[<span data-ttu-id="fa189-247">about_Providers</span><span class="sxs-lookup"><span data-stu-id="fa189-247">about_Providers</span></span>](../Microsoft.PowerShell.Core/About/about_Providers.md)

[<span data-ttu-id="fa189-248">Wissen-item</span><span class="sxs-lookup"><span data-stu-id="fa189-248">Clear-Item</span></span>](Clear-Item.md)

[<span data-ttu-id="fa189-249">Get-item</span><span class="sxs-lookup"><span data-stu-id="fa189-249">Get-Item</span></span>](Get-Item.md)

[<span data-ttu-id="fa189-250">Get-PSProvider</span><span class="sxs-lookup"><span data-stu-id="fa189-250">Get-PSProvider</span></span>](Get-PSProvider.md)

[<span data-ttu-id="fa189-251">Invoke-item</span><span class="sxs-lookup"><span data-stu-id="fa189-251">Invoke-Item</span></span>](Invoke-Item.md)

[<span data-ttu-id="fa189-252">Item verplaatsen</span><span class="sxs-lookup"><span data-stu-id="fa189-252">Move-Item</span></span>](Move-Item.md)

[<span data-ttu-id="fa189-253">Nieuw-item</span><span class="sxs-lookup"><span data-stu-id="fa189-253">New-Item</span></span>](New-Item.md)

[<span data-ttu-id="fa189-254">Verwijderen-item</span><span class="sxs-lookup"><span data-stu-id="fa189-254">Remove-Item</span></span>](Remove-Item.md)

[<span data-ttu-id="fa189-255">Naam wijzigen-item</span><span class="sxs-lookup"><span data-stu-id="fa189-255">Rename-Item</span></span>](Rename-Item.md)

[<span data-ttu-id="fa189-256">Set-item</span><span class="sxs-lookup"><span data-stu-id="fa189-256">Set-Item</span></span>](Set-Item.md)

