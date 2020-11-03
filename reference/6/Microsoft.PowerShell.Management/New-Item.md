---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 06/18/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/new-item?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: New-Item
ms.openlocfilehash: 09ed5697299ea2a9f516597df9de44ac714350ed
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/07/2020
ms.locfileid: "93250237"
---
# <span data-ttu-id="8fa1c-103">New-Item</span><span class="sxs-lookup"><span data-stu-id="8fa1c-103">New-Item</span></span>

## <span data-ttu-id="8fa1c-104">SAMENVATTING</span><span class="sxs-lookup"><span data-stu-id="8fa1c-104">SYNOPSIS</span></span>
<span data-ttu-id="8fa1c-105">Hiermee maakt u een nieuw item.</span><span class="sxs-lookup"><span data-stu-id="8fa1c-105">Creates a new item.</span></span>

## <span data-ttu-id="8fa1c-106">SYNTAXIS</span><span class="sxs-lookup"><span data-stu-id="8fa1c-106">SYNTAX</span></span>

### <span data-ttu-id="8fa1c-107">padset (standaard)</span><span class="sxs-lookup"><span data-stu-id="8fa1c-107">pathSet (Default)</span></span>

```
New-Item [-Path] <String[]> [-ItemType <String>] [-Value <Object>] [-Force] [-Credential <PSCredential>]
 [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="8fa1c-108">naamset</span><span class="sxs-lookup"><span data-stu-id="8fa1c-108">nameSet</span></span>

```
New-Item [[-Path] <String[]>] -Name <String> [-ItemType <String>] [-Value <Object>] [-Force]
 [-Credential <PSCredential>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="8fa1c-109">BESCHRIJVING</span><span class="sxs-lookup"><span data-stu-id="8fa1c-109">DESCRIPTION</span></span>

<span data-ttu-id="8fa1c-110">De `New-Item` cmdlet maakt een nieuw item en stelt de waarde ervan in.</span><span class="sxs-lookup"><span data-stu-id="8fa1c-110">The `New-Item` cmdlet creates a new item and sets its value.</span></span> <span data-ttu-id="8fa1c-111">De typen items die kunnen worden gemaakt, zijn afhankelijk van de locatie van het item.</span><span class="sxs-lookup"><span data-stu-id="8fa1c-111">The types of items that can be created depend on the location of the item.</span></span> <span data-ttu-id="8fa1c-112">In het bestands systeem `New-Item` maakt bijvoorbeeld bestanden en mappen.</span><span class="sxs-lookup"><span data-stu-id="8fa1c-112">For example, in the file system, `New-Item` creates files and folders.</span></span> <span data-ttu-id="8fa1c-113">In het REGI ster worden `New-Item` register sleutels en vermeldingen gemaakt.</span><span class="sxs-lookup"><span data-stu-id="8fa1c-113">In the registry, `New-Item` creates registry keys and entries.</span></span>

<span data-ttu-id="8fa1c-114">`New-Item` kan ook de waarde instellen van de items die het maakt.</span><span class="sxs-lookup"><span data-stu-id="8fa1c-114">`New-Item` can also set the value of the items that it creates.</span></span> <span data-ttu-id="8fa1c-115">Als er bijvoorbeeld een nieuw bestand wordt gemaakt, `New-Item` kan de eerste inhoud aan het bestand worden toegevoegd.</span><span class="sxs-lookup"><span data-stu-id="8fa1c-115">For example, when it creates a new file, `New-Item` can add initial content to the file.</span></span>

## <span data-ttu-id="8fa1c-116">VOORBEELDEN</span><span class="sxs-lookup"><span data-stu-id="8fa1c-116">EXAMPLES</span></span>

### <span data-ttu-id="8fa1c-117">Voor beeld 1: een bestand in de huidige map maken</span><span class="sxs-lookup"><span data-stu-id="8fa1c-117">Example 1: Create a file in the current directory</span></span>

<span data-ttu-id="8fa1c-118">Met deze opdracht maakt u een tekst bestand met de naam ' testfile1.txt ' in de huidige map.</span><span class="sxs-lookup"><span data-stu-id="8fa1c-118">This command creates a text file that is named "testfile1.txt" in the current directory.</span></span> <span data-ttu-id="8fa1c-119">De punt ('. ') in de waarde van de para meter **Path** geeft aan dat de huidige map is.</span><span class="sxs-lookup"><span data-stu-id="8fa1c-119">The dot ('.') in the value of the **Path** parameter indicates the current directory.</span></span> <span data-ttu-id="8fa1c-120">De aanhalings tekens die volgen op de **waarde** para meter wordt toegevoegd aan het bestand als inhoud.</span><span class="sxs-lookup"><span data-stu-id="8fa1c-120">The quoted text that follows the **Value** parameter is added to the file as content.</span></span>

```powershell
New-Item -Path . -Name "testfile1.txt" -ItemType "file" -Value "This is a text string."
```

### <span data-ttu-id="8fa1c-121">Voor beeld 2: een directory maken</span><span class="sxs-lookup"><span data-stu-id="8fa1c-121">Example 2: Create a directory</span></span>

<span data-ttu-id="8fa1c-122">Met deze opdracht maakt u een map met de naam Logboeken in het `C:` station.</span><span class="sxs-lookup"><span data-stu-id="8fa1c-122">This command creates a directory named "Logfiles" in the `C:` drive.</span></span> <span data-ttu-id="8fa1c-123">De para meter **item** type geeft aan dat het nieuwe item een map is, niet een bestand of een ander bestandssysteem object.</span><span class="sxs-lookup"><span data-stu-id="8fa1c-123">The **ItemType** parameter specifies that the new item is a directory, not a file or other file system object.</span></span>

```powershell
New-Item -Path "c:\" -Name "logfiles" -ItemType "directory"
```

### <span data-ttu-id="8fa1c-124">Voor beeld 3: een profiel maken</span><span class="sxs-lookup"><span data-stu-id="8fa1c-124">Example 3: Create a profile</span></span>

<span data-ttu-id="8fa1c-125">Met deze opdracht maakt u een Power shell-profiel in het pad dat is opgegeven door de `$profile` variabele.</span><span class="sxs-lookup"><span data-stu-id="8fa1c-125">This command creates a PowerShell profile in the path that is specified by the `$profile` variable.</span></span>

<span data-ttu-id="8fa1c-126">U kunt profielen gebruiken om Power shell aan te passen.</span><span class="sxs-lookup"><span data-stu-id="8fa1c-126">You can use profiles to customize PowerShell.</span></span> <span data-ttu-id="8fa1c-127">`$profile` is een automatische (ingebouwde) variabele waarmee het pad en de bestands naam van het profiel ' CurrentUser/CurrentHost ' worden opgeslagen.</span><span class="sxs-lookup"><span data-stu-id="8fa1c-127">`$profile` is an automatic (built-in) variable that stores the path and file name of the "CurrentUser/CurrentHost" profile.</span></span> <span data-ttu-id="8fa1c-128">Het profiel bestaat standaard niet, hoewel in Power shell een pad en een bestands naam worden opgeslagen.</span><span class="sxs-lookup"><span data-stu-id="8fa1c-128">By default, the profile does not exist, even though PowerShell stores a path and file name for it.</span></span>

<span data-ttu-id="8fa1c-129">In deze opdracht vertegenwoordigt de `$profile` variabele het pad van het bestand.</span><span class="sxs-lookup"><span data-stu-id="8fa1c-129">In this command, the `$profile` variable represents the path of the file.</span></span> <span data-ttu-id="8fa1c-130">**Item** type-para meter geeft aan dat met de opdracht een bestand wordt gemaakt.</span><span class="sxs-lookup"><span data-stu-id="8fa1c-130">**ItemType** parameter specifies that the command creates a file.</span></span> <span data-ttu-id="8fa1c-131">Met de para meter **Force** kunt u een bestand in het profielpad maken, zelfs wanneer de mappen in het pad niet bestaan.</span><span class="sxs-lookup"><span data-stu-id="8fa1c-131">The **Force** parameter lets you create a file in the profile path, even when the directories in the path do not exist.</span></span>

<span data-ttu-id="8fa1c-132">Nadat u een profiel hebt gemaakt, kunt u aliassen, functies en scripts in het profiel invoeren om uw shell aan te passen.</span><span class="sxs-lookup"><span data-stu-id="8fa1c-132">After you create a profile, you can enter aliases, functions, and scripts in the profile to customize your shell.</span></span>

<span data-ttu-id="8fa1c-133">Zie [about_Automatic_Variables](../Microsoft.PowerShell.Core/About/about_Automatic_Variables.md) en [about_Profiles](../Microsoft.PowerShell.Core/About/about_Profiles.md)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="8fa1c-133">For more information, see [about_Automatic_Variables](../Microsoft.PowerShell.Core/About/about_Automatic_Variables.md) and [about_Profiles](../Microsoft.PowerShell.Core/About/about_Profiles.md).</span></span>

```powershell
New-Item -Path $profile -ItemType "file" -Force
```

### <span data-ttu-id="8fa1c-134">Voor beeld 4: een map in een andere Directory maken</span><span class="sxs-lookup"><span data-stu-id="8fa1c-134">Example 4: Create a directory in a different directory</span></span>

<span data-ttu-id="8fa1c-135">In dit voor beeld wordt een nieuwe map scripts gemaakt in de map "C:\PS-Test".</span><span class="sxs-lookup"><span data-stu-id="8fa1c-135">This example creates a new Scripts directory in the "C:\PS-Test" directory.</span></span>

<span data-ttu-id="8fa1c-136">De naam van het nieuwe directory-item, "scripts", is opgenomen in de waarde van de para meter **Path** , in plaats van dat wordt opgegeven in de waarde **naam**.</span><span class="sxs-lookup"><span data-stu-id="8fa1c-136">The name of the new directory item, "Scripts", is included in the value of **Path** parameter, instead of being specified in the value of **Name**.</span></span> <span data-ttu-id="8fa1c-137">Zoals aangegeven door de syntaxis, is het opdracht formulier geldig.</span><span class="sxs-lookup"><span data-stu-id="8fa1c-137">As indicated by the syntax, either command form is valid.</span></span>

```powershell
New-Item -ItemType "directory" -Path "c:\ps-test\scripts"
```

### <span data-ttu-id="8fa1c-138">Voor beeld 5: meerdere bestanden maken</span><span class="sxs-lookup"><span data-stu-id="8fa1c-138">Example 5: Create multiple files</span></span>

<span data-ttu-id="8fa1c-139">In dit voor beeld worden bestanden gemaakt in twee verschillende directory's.</span><span class="sxs-lookup"><span data-stu-id="8fa1c-139">This example creates files in two different directories.</span></span> <span data-ttu-id="8fa1c-140">Omdat **Path** meerdere teken reeksen accepteert, kunt u deze gebruiken om meerdere items te maken.</span><span class="sxs-lookup"><span data-stu-id="8fa1c-140">Because **Path** takes multiple strings, you can use it to create multiple items.</span></span>

```powershell
New-Item -ItemType "file" -Path "c:\ps-test\test.txt", "c:\ps-test\Logs\test.log"
```

### <span data-ttu-id="8fa1c-141">Voor beeld 6: Joker tekens gebruiken om bestanden in meerdere mappen te maken</span><span class="sxs-lookup"><span data-stu-id="8fa1c-141">Example 6: Use wildcards to create files in multiple directories</span></span>

<span data-ttu-id="8fa1c-142">De `New-Item` cmdlet ondersteunt joker tekens in de para meter **Path** .</span><span class="sxs-lookup"><span data-stu-id="8fa1c-142">The `New-Item` cmdlet supports wildcards in the **Path** parameter.</span></span> <span data-ttu-id="8fa1c-143">Met de volgende opdracht maakt u een `temp.txt` bestand in alle directory's die zijn opgegeven met de joker tekens in de para meter **Path** .</span><span class="sxs-lookup"><span data-stu-id="8fa1c-143">The following command creates a `temp.txt` file in all of the directories specified by the wildcards in the **Path** parameter.</span></span>

```powershell
Get-ChildItem -Path C:\Temp\
```

```Output
    Directory:  C:\Temp

Mode                LastWriteTime     Length Name
----                -------------     ------ ----
d-----        5/15/2019   6:45 AM        1   One
d-----        5/15/2019   6:45 AM        1   Two
d-----        5/15/2019   6:45 AM        1   Three
```

```powershell
New-Item -Path * -Name temp.txt -ItemType File | Select-Object FullName
```

```Output
FullName
--------
C:\Temp\One\temp.txt
C:\Temp\Three\temp.txt
C:\Temp\Two\temp.txt
```

<span data-ttu-id="8fa1c-144">Met de `Get-ChildItem` cmdlet worden drie mappen in de map weer gegeven `C:\Temp` .</span><span class="sxs-lookup"><span data-stu-id="8fa1c-144">The `Get-ChildItem` cmdlet shows three directories under the `C:\Temp` directory.</span></span> <span data-ttu-id="8fa1c-145">Joker tekens gebruiken met de `New-Item` cmdlet maakt u een `temp.txt` bestand in alle directory's onder de huidige map.</span><span class="sxs-lookup"><span data-stu-id="8fa1c-145">Using wildcards the `New-Item` cmdlet creates a `temp.txt` file in all of the directories under the current directory.</span></span> <span data-ttu-id="8fa1c-146">De `New-Item` cmdlet voert de items uit die u hebt gemaakt, waarnaar wordt gepiped om `Select-Object` de paden van de zojuist gemaakte bestanden te controleren.</span><span class="sxs-lookup"><span data-stu-id="8fa1c-146">The `New-Item` cmdlet outputs the items you created, which is piped to `Select-Object` to verify the paths of the newly created files.</span></span>

### <span data-ttu-id="8fa1c-147">Voor beeld 7: een symbolische koppeling naar een bestand of map maken</span><span class="sxs-lookup"><span data-stu-id="8fa1c-147">Example 7: Create a symbolic link to a file or folder</span></span>

<span data-ttu-id="8fa1c-148">In dit voor beeld wordt een symbolische koppeling gemaakt naar het Notice.txt-bestand in de huidige map.</span><span class="sxs-lookup"><span data-stu-id="8fa1c-148">This example creates a symbolic link to the Notice.txt file in the current folder.</span></span>

```powershell
$link = New-Item -ItemType SymbolicLink -Path .\link -Target .\Notice.txt
$link | Select-Object LinkType, Target
```

```Output
LinkType     Target
--------     ------
SymbolicLink {.\Notice.txt}
```

<span data-ttu-id="8fa1c-149">In dit voor beeld is **target** een alias voor de **waarde** -para meter.</span><span class="sxs-lookup"><span data-stu-id="8fa1c-149">In this example, **Target** is an alias for the **Value** parameter.</span></span> <span data-ttu-id="8fa1c-150">Het doel van de symbolische koppeling kan een relatief pad zijn.</span><span class="sxs-lookup"><span data-stu-id="8fa1c-150">The target of the symbolic link can be a relative path.</span></span> <span data-ttu-id="8fa1c-151">Vóór Power shell v 6.2 moet het doel een volledig pad zijn.</span><span class="sxs-lookup"><span data-stu-id="8fa1c-151">Prior to PowerShell v6.2, the target must be a fully-qualified path.</span></span>

> [!CAUTION]
> <span data-ttu-id="8fa1c-152">Als u een **SymbolicLink** maakt in een map in Windows, moet u een volledig gekwalificeerde pad gebruiken.</span><span class="sxs-lookup"><span data-stu-id="8fa1c-152">If you are creating a **SymbolicLink** to a folder on Windows, you must use a fully-qualified path.</span></span> <span data-ttu-id="8fa1c-153">Als u een relatief pad gebruikt, wordt de koppeling gemaakt als een koppeling naar een bestands type in plaats van een koppeling naar een directory-type.</span><span class="sxs-lookup"><span data-stu-id="8fa1c-153">If you use a relative path, the link is created as a file-type link instead of a directory-type link.</span></span>

### <span data-ttu-id="8fa1c-154">Voor beeld 8: gebruik de para meter-Force om mappen opnieuw te maken</span><span class="sxs-lookup"><span data-stu-id="8fa1c-154">Example 8: Use the -Force parameter to attempt to recreate folders</span></span>

<span data-ttu-id="8fa1c-155">In dit voor beeld wordt een map gemaakt met een bestand in.</span><span class="sxs-lookup"><span data-stu-id="8fa1c-155">This example creates a folder with a file inside.</span></span> <span data-ttu-id="8fa1c-156">Vervolgens wordt geprobeerd om dezelfde map te maken met `-Force` .</span><span class="sxs-lookup"><span data-stu-id="8fa1c-156">Then, attempts to create the same folder using `-Force`.</span></span> <span data-ttu-id="8fa1c-157">De map wordt niet overschreven, maar er wordt gewoon het bestaande map-object geretourneerd waarbij het bestand intact is gemaakt.</span><span class="sxs-lookup"><span data-stu-id="8fa1c-157">It will not overwrite the folder but simply return the existing folder object with the file created intact.</span></span>

```powershell
PS> New-Item -Path .\TestFolder -ItemType Directory
PS> New-Item -Path .\TestFolder\TestFile.txt -ItemType File

PS> New-Item -Path .\TestFolder -ItemType Directory -Force

    Directory: C:\
Mode                LastWriteTime         Length Name
----                -------------         ------ ----
d-----         5/1/2020   8:03 AM                TestFolder

PS> Get-ChildItem .\TestFolder\

    Directory: C:\TestFolder
Mode                LastWriteTime         Length Name
----                -------------         ------ ----
-a----         5/1/2020   8:03 AM              0 TestFile.txt
```

### <span data-ttu-id="8fa1c-158">Voor beeld 9: de para meter-Force gebruiken om bestaande bestanden te overschrijven</span><span class="sxs-lookup"><span data-stu-id="8fa1c-158">Example 9: Use the -Force parameter to overwrite existing files</span></span>

<span data-ttu-id="8fa1c-159">In dit voor beeld wordt een bestand gemaakt met een waarde en wordt het bestand vervolgens opnieuw gemaakt met `-Force` .</span><span class="sxs-lookup"><span data-stu-id="8fa1c-159">This example creates a file with a value and then recreates the file using `-Force`.</span></span> <span data-ttu-id="8fa1c-160">Hiermee wordt het bestaande bestand overschreven, waardoor de inhoud verloren gaat, omdat u de eigenschap length kunt zien</span><span class="sxs-lookup"><span data-stu-id="8fa1c-160">This overwrites The existing file and it will lose it's content as you can see by the length property</span></span>

```powershell
PS> New-Item ./TestFile.txt -ItemType File -Value 'This is just a test file'

    Directory: C:\Source\Test
Mode                LastWriteTime         Length Name
----                -------------         ------ ----
-a----         5/1/2020   8:32 AM             24 TestFile.txt

New-Item ./TestFile.txt -ItemType File -Force

    Directory: C:\Source\Test
Mode                LastWriteTime         Length Name
----                -------------         ------ ----
-a----         5/1/2020   8:32 AM              0 TestFile.txt
```

> [!NOTE]
> <span data-ttu-id="8fa1c-161">Wanneer u gebruikt `New-Item` met de `-Force` switch om register sleutels te maken, werkt de opdracht hetzelfde als bij het overschrijven van een bestand.</span><span class="sxs-lookup"><span data-stu-id="8fa1c-161">When using `New-Item` with the `-Force` switch to create registry keys, the command will behave the same as when overwriting a file.</span></span> <span data-ttu-id="8fa1c-162">Als de register sleutel al bestaat, worden de sleutel en alle eigenschappen en waarden overschreven met een lege register sleutel.</span><span class="sxs-lookup"><span data-stu-id="8fa1c-162">If the registry key already exists, the key and all properties and values will be overwritten with an empty registry key.</span></span>

## <span data-ttu-id="8fa1c-163">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="8fa1c-163">PARAMETERS</span></span>

### <span data-ttu-id="8fa1c-164">-Credential</span><span class="sxs-lookup"><span data-stu-id="8fa1c-164">-Credential</span></span>

> [!NOTE]
> <span data-ttu-id="8fa1c-165">Deze para meter wordt niet ondersteund door providers die zijn geïnstalleerd met Power shell.</span><span class="sxs-lookup"><span data-stu-id="8fa1c-165">This parameter is not supported by any providers installed with PowerShell.</span></span> <span data-ttu-id="8fa1c-166">Gebruik om een andere gebruiker te imiteren of uw referenties te verhogen wanneer u deze cmdlet uitvoert `Invoke-Command` .</span><span class="sxs-lookup"><span data-stu-id="8fa1c-166">To impersonate another user or elevate your credentials when running this cmdlet, use `Invoke-Command`.</span></span>

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

### <span data-ttu-id="8fa1c-167">-Force</span><span class="sxs-lookup"><span data-stu-id="8fa1c-167">-Force</span></span>

<span data-ttu-id="8fa1c-168">Hiermee wordt de cmdlet gedwongen een item te maken dat over een bestaand alleen-lezen item schrijft.</span><span class="sxs-lookup"><span data-stu-id="8fa1c-168">Forces this cmdlet to create an item that writes over an existing read-only item.</span></span> <span data-ttu-id="8fa1c-169">De implementatie varieert van provider tot provider.</span><span class="sxs-lookup"><span data-stu-id="8fa1c-169">Implementation varies from provider to provider.</span></span> <span data-ttu-id="8fa1c-170">Zelfs met behulp van de para meter **forceren** , kan de cmdlet geen beveiligings beperkingen opheffen.</span><span class="sxs-lookup"><span data-stu-id="8fa1c-170">Even using the **Force** parameter, the cmdlet cannot override security restrictions.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="8fa1c-171">-Item type</span><span class="sxs-lookup"><span data-stu-id="8fa1c-171">-ItemType</span></span>

<span data-ttu-id="8fa1c-172">Hiermee wordt het type provider opgegeven van het nieuwe item.</span><span class="sxs-lookup"><span data-stu-id="8fa1c-172">Specifies the provider-specified type of the new item.</span></span> <span data-ttu-id="8fa1c-173">De beschik bare waarden van deze para meter zijn afhankelijk van de huidige provider die u gebruikt.</span><span class="sxs-lookup"><span data-stu-id="8fa1c-173">The available values of this parameter depend on the current provider you are using.</span></span>

<span data-ttu-id="8fa1c-174">Als uw locatie zich in een station bevindt `FileSystem` , zijn de volgende waarden toegestaan:</span><span class="sxs-lookup"><span data-stu-id="8fa1c-174">If your location is in a `FileSystem` drive, the following values are allowed:</span></span>

- <span data-ttu-id="8fa1c-175">Bestand</span><span class="sxs-lookup"><span data-stu-id="8fa1c-175">File</span></span>
- <span data-ttu-id="8fa1c-176">Directory</span><span class="sxs-lookup"><span data-stu-id="8fa1c-176">Directory</span></span>
- <span data-ttu-id="8fa1c-177">SymbolicLink</span><span class="sxs-lookup"><span data-stu-id="8fa1c-177">SymbolicLink</span></span>
- <span data-ttu-id="8fa1c-178">Verbinding</span><span class="sxs-lookup"><span data-stu-id="8fa1c-178">Junction</span></span>
- <span data-ttu-id="8fa1c-179">Hard link</span><span class="sxs-lookup"><span data-stu-id="8fa1c-179">HardLink</span></span>

> [!NOTE]
> <span data-ttu-id="8fa1c-180">Het maken `SymbolicLink` van een type in Windows vereist uitbrei ding als beheerder.</span><span class="sxs-lookup"><span data-stu-id="8fa1c-180">Creating a `SymbolicLink` type on Windows requires elevation as administrator.</span></span> <span data-ttu-id="8fa1c-181">Windows 10 (build 14972 of nieuwer) waarvoor de ontwikkelaars modus is ingeschakeld, vereist echter niet langer de benodigde uitbrei ding voor het maken van symbolische koppelingen.</span><span class="sxs-lookup"><span data-stu-id="8fa1c-181">However, Windows 10 (build 14972 or newer) with Developer Mode enabled no longer requires elevation creating symbolic links.</span></span>

<span data-ttu-id="8fa1c-182">`Certificate`Dit zijn de waarden die u kunt opgeven in een station:</span><span class="sxs-lookup"><span data-stu-id="8fa1c-182">In a `Certificate` drive, these are the values you can specify:</span></span>

- <span data-ttu-id="8fa1c-183">Certificaat provider</span><span class="sxs-lookup"><span data-stu-id="8fa1c-183">Certificate Provider</span></span>
- <span data-ttu-id="8fa1c-184">Certificaat</span><span class="sxs-lookup"><span data-stu-id="8fa1c-184">Certificate</span></span>
- <span data-ttu-id="8fa1c-185">Opslaan</span><span class="sxs-lookup"><span data-stu-id="8fa1c-185">Store</span></span>
- <span data-ttu-id="8fa1c-186">StoreLocation</span><span class="sxs-lookup"><span data-stu-id="8fa1c-186">StoreLocation</span></span>

<span data-ttu-id="8fa1c-187">Zie [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="8fa1c-187">For more information see [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md).</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases: Type

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="8fa1c-188">-Name</span><span class="sxs-lookup"><span data-stu-id="8fa1c-188">-Name</span></span>

<span data-ttu-id="8fa1c-189">Hiermee geeft u de naam van het nieuwe item.</span><span class="sxs-lookup"><span data-stu-id="8fa1c-189">Specifies the name of the new item.</span></span> <span data-ttu-id="8fa1c-190">U kunt de naam van het nieuwe item in de waarde van de para meter **name** of **Path** opgeven, en u kunt het pad van het nieuwe item opgeven in de **naam** of de waarde van het **pad** .</span><span class="sxs-lookup"><span data-stu-id="8fa1c-190">You can specify the name of the new item in the **Name** or **Path** parameter value, and you can specify the path of the new item in **Name** or **Path** value.</span></span> <span data-ttu-id="8fa1c-191">Namen van items die worden door gegeven met de para meter **name** , worden gemaakt ten opzichte van de waarde van de para meter **Path** .</span><span class="sxs-lookup"><span data-stu-id="8fa1c-191">Items names passed using the **Name** parameter are created relative to the value of the **Path** parameter.</span></span>

```yaml
Type: System.String
Parameter Sets: nameSet
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="8fa1c-192">-Path</span><span class="sxs-lookup"><span data-stu-id="8fa1c-192">-Path</span></span>

<span data-ttu-id="8fa1c-193">Hiermee geeft u het pad van de locatie van het nieuwe item.</span><span class="sxs-lookup"><span data-stu-id="8fa1c-193">Specifies the path of the location of the new item.</span></span> <span data-ttu-id="8fa1c-194">De standaard waarde is de huidige locatie wanneer het **pad** wordt wegge laten.</span><span class="sxs-lookup"><span data-stu-id="8fa1c-194">The default is the current location when **Path** is omitted.</span></span> <span data-ttu-id="8fa1c-195">U kunt de naam van het nieuwe item opgeven in de **naam** of het **pad** op te geven.</span><span class="sxs-lookup"><span data-stu-id="8fa1c-195">You can specify the name of the new item in **Name** , or include it in **Path**.</span></span> <span data-ttu-id="8fa1c-196">Namen van items die worden door gegeven met de para meter **name** , worden gemaakt ten opzichte van de waarde van de para meter **Path** .</span><span class="sxs-lookup"><span data-stu-id="8fa1c-196">Items names passed using the **Name** parameter are created relative to the value of the **Path** parameter.</span></span>

<span data-ttu-id="8fa1c-197">Voor deze cmdlet werkt de para meter **Path** als de **LiteralPath** -para meter van andere cmdlets.</span><span class="sxs-lookup"><span data-stu-id="8fa1c-197">For this cmdlet, the **Path** parameter works like the **LiteralPath** parameter of other cmdlets.</span></span>
<span data-ttu-id="8fa1c-198">Joker tekens worden niet geïnterpreteerd.</span><span class="sxs-lookup"><span data-stu-id="8fa1c-198">Wildcard characters are not interpreted.</span></span> <span data-ttu-id="8fa1c-199">Alle tekens worden door gegeven aan de provider van de locatie.</span><span class="sxs-lookup"><span data-stu-id="8fa1c-199">All characters are passed to the location's provider.</span></span> <span data-ttu-id="8fa1c-200">De provider biedt mogelijk geen ondersteuning voor alle tekens.</span><span class="sxs-lookup"><span data-stu-id="8fa1c-200">The provider may not support all characters.</span></span> <span data-ttu-id="8fa1c-201">U kunt bijvoorbeeld geen bestands naam maken die een asterisk ()- `*` teken bevat.</span><span class="sxs-lookup"><span data-stu-id="8fa1c-201">For example, you cannot create a filename that contains an asterisk (`*`) character.</span></span>

```yaml
Type: System.String[]
Parameter Sets: pathSet, nameSet
Aliases:

Required: True (pathSet), False (nameSet)
Position: 0
Default value: Current location
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="8fa1c-202">-Waarde</span><span class="sxs-lookup"><span data-stu-id="8fa1c-202">-Value</span></span>

<span data-ttu-id="8fa1c-203">Hiermee geeft u de waarde van het nieuwe item op.</span><span class="sxs-lookup"><span data-stu-id="8fa1c-203">Specifies the value of the new item.</span></span> <span data-ttu-id="8fa1c-204">U kunt ook een waarde door sluizen naar `New-Item` .</span><span class="sxs-lookup"><span data-stu-id="8fa1c-204">You can also pipe a value to `New-Item`.</span></span>

```yaml
Type: System.Object
Parameter Sets: (All)
Aliases: Target

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="8fa1c-205">-Confirm</span><span class="sxs-lookup"><span data-stu-id="8fa1c-205">-Confirm</span></span>

<span data-ttu-id="8fa1c-206">Hiermee wordt u gevraagd om bevestiging voordat u de cmdlet uitvoert.</span><span class="sxs-lookup"><span data-stu-id="8fa1c-206">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="8fa1c-207">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="8fa1c-207">-WhatIf</span></span>

<span data-ttu-id="8fa1c-208">Hiermee wordt weergegeven wat er zou gebeuren als u de cmdlet uitvoert.</span><span class="sxs-lookup"><span data-stu-id="8fa1c-208">Shows what would happen if the cmdlet runs.</span></span>
<span data-ttu-id="8fa1c-209">De cmdlet wordt niet uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="8fa1c-209">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="8fa1c-210">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="8fa1c-210">CommonParameters</span></span>

<span data-ttu-id="8fa1c-211">Deze cmdlet biedt ondersteuning voor de algemene para meters: `-Debug` , `-ErrorAction` , `-ErrorVariable` , `-InformationAction` , `-InformationVariable` , `-OutVariable` , `-OutBuffer` , `-PipelineVariable` , `-Verbose` , `-WarningAction` en `-WarningVariable` .</span><span class="sxs-lookup"><span data-stu-id="8fa1c-211">This cmdlet supports the common parameters: `-Debug`, `-ErrorAction`, `-ErrorVariable`, `-InformationAction`, `-InformationVariable`, `-OutVariable`, `-OutBuffer`, `-PipelineVariable`, `-Verbose`, `-WarningAction`, and `-WarningVariable`.</span></span> <span data-ttu-id="8fa1c-212">Zie [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="8fa1c-212">For more information, see [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md).</span></span>

## <span data-ttu-id="8fa1c-213">INVOER</span><span class="sxs-lookup"><span data-stu-id="8fa1c-213">INPUTS</span></span>

### <span data-ttu-id="8fa1c-214">System. object</span><span class="sxs-lookup"><span data-stu-id="8fa1c-214">System.Object</span></span>

<span data-ttu-id="8fa1c-215">U kunt een waarde voor het nieuwe item door sluizen naar deze cmdlet.</span><span class="sxs-lookup"><span data-stu-id="8fa1c-215">You can pipe a value for the new item to this cmdlet.</span></span>

## <span data-ttu-id="8fa1c-216">UITVOER</span><span class="sxs-lookup"><span data-stu-id="8fa1c-216">OUTPUTS</span></span>

### <span data-ttu-id="8fa1c-217">System. object</span><span class="sxs-lookup"><span data-stu-id="8fa1c-217">System.Object</span></span>

<span data-ttu-id="8fa1c-218">Met deze cmdlet wordt het item geretourneerd dat wordt gemaakt.</span><span class="sxs-lookup"><span data-stu-id="8fa1c-218">This cmdlet returns the item that it creates.</span></span>

## <span data-ttu-id="8fa1c-219">OPMERKINGEN</span><span class="sxs-lookup"><span data-stu-id="8fa1c-219">NOTES</span></span>

<span data-ttu-id="8fa1c-220">`New-Item` is ontworpen om te werken met de gegevens die door elke provider worden weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="8fa1c-220">`New-Item` is designed to work with the data exposed by any provider.</span></span> <span data-ttu-id="8fa1c-221">Als u een lijst wilt weer geven van de providers die beschikbaar zijn in uw sessie, typt u `Get-PsProvider` .</span><span class="sxs-lookup"><span data-stu-id="8fa1c-221">To list the providers available in your session, type `Get-PsProvider`.</span></span> <span data-ttu-id="8fa1c-222">Zie [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="8fa1c-222">For more information, see [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md).</span></span>

## <span data-ttu-id="8fa1c-223">GERELATEERDE KOPPELINGEN</span><span class="sxs-lookup"><span data-stu-id="8fa1c-223">RELATED LINKS</span></span>

[<span data-ttu-id="8fa1c-224">Wissen-item</span><span class="sxs-lookup"><span data-stu-id="8fa1c-224">Clear-Item</span></span>](Clear-Item.md)

[<span data-ttu-id="8fa1c-225">Kopie-item</span><span class="sxs-lookup"><span data-stu-id="8fa1c-225">Copy-Item</span></span>](Copy-Item.md)

[<span data-ttu-id="8fa1c-226">Get-item</span><span class="sxs-lookup"><span data-stu-id="8fa1c-226">Get-Item</span></span>](Get-Item.md)

[<span data-ttu-id="8fa1c-227">Invoke-item</span><span class="sxs-lookup"><span data-stu-id="8fa1c-227">Invoke-Item</span></span>](Invoke-Item.md)

[<span data-ttu-id="8fa1c-228">Item verplaatsen</span><span class="sxs-lookup"><span data-stu-id="8fa1c-228">Move-Item</span></span>](Move-Item.md)

[<span data-ttu-id="8fa1c-229">Verwijderen-item</span><span class="sxs-lookup"><span data-stu-id="8fa1c-229">Remove-Item</span></span>](Remove-Item.md)

[<span data-ttu-id="8fa1c-230">Naam wijzigen-item</span><span class="sxs-lookup"><span data-stu-id="8fa1c-230">Rename-Item</span></span>](Rename-Item.md)

[<span data-ttu-id="8fa1c-231">Set-item</span><span class="sxs-lookup"><span data-stu-id="8fa1c-231">Set-Item</span></span>](Set-Item.md)

[<span data-ttu-id="8fa1c-232">about_Providers</span><span class="sxs-lookup"><span data-stu-id="8fa1c-232">about_Providers</span></span>](../Microsoft.PowerShell.Core/About/about_Providers.md)
