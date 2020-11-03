---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 04/23/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/new-item?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: New-Item
ms.openlocfilehash: b1657d369d44d575ee7bed8b76d36224ea2748f2
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/07/2020
ms.locfileid: "93250597"
---
# <span data-ttu-id="a1e96-103">New-Item</span><span class="sxs-lookup"><span data-stu-id="a1e96-103">New-Item</span></span>

## <span data-ttu-id="a1e96-104">SAMENVATTING</span><span class="sxs-lookup"><span data-stu-id="a1e96-104">SYNOPSIS</span></span>
<span data-ttu-id="a1e96-105">Hiermee maakt u een nieuw item.</span><span class="sxs-lookup"><span data-stu-id="a1e96-105">Creates a new item.</span></span>

## <span data-ttu-id="a1e96-106">SYNTAXIS</span><span class="sxs-lookup"><span data-stu-id="a1e96-106">SYNTAX</span></span>

### <span data-ttu-id="a1e96-107">padset (standaard)</span><span class="sxs-lookup"><span data-stu-id="a1e96-107">pathSet (Default)</span></span>

```
New-Item [-Path] <String[]> [-ItemType <String>] [-Value <Object>] [-Force] [-Credential <PSCredential>]
 [-WhatIf] [-Confirm] [-UseTransaction] [<CommonParameters>]
```

### <span data-ttu-id="a1e96-108">naamset</span><span class="sxs-lookup"><span data-stu-id="a1e96-108">nameSet</span></span>

```
New-Item [[-Path] <String[]>] -Name <String> [-ItemType <String>] [-Value <Object>] [-Force]
 [-Credential <PSCredential>] [-WhatIf] [-Confirm] [-UseTransaction] [<CommonParameters>]
```

## <span data-ttu-id="a1e96-109">BESCHRIJVING</span><span class="sxs-lookup"><span data-stu-id="a1e96-109">DESCRIPTION</span></span>

<span data-ttu-id="a1e96-110">De `New-Item` cmdlet maakt een nieuw item en stelt de waarde ervan in.</span><span class="sxs-lookup"><span data-stu-id="a1e96-110">The `New-Item` cmdlet creates a new item and sets its value.</span></span> <span data-ttu-id="a1e96-111">De typen items die kunnen worden gemaakt, zijn afhankelijk van de locatie van het item.</span><span class="sxs-lookup"><span data-stu-id="a1e96-111">The types of items that can be created depend on the location of the item.</span></span> <span data-ttu-id="a1e96-112">In het bestands systeem `New-Item` maakt bijvoorbeeld bestanden en mappen.</span><span class="sxs-lookup"><span data-stu-id="a1e96-112">For example, in the file system, `New-Item` creates files and folders.</span></span> <span data-ttu-id="a1e96-113">In het REGI ster worden `New-Item` register sleutels en vermeldingen gemaakt.</span><span class="sxs-lookup"><span data-stu-id="a1e96-113">In the registry, `New-Item` creates registry keys and entries.</span></span>

<span data-ttu-id="a1e96-114">`New-Item` kan ook de waarde instellen van de items die het maakt.</span><span class="sxs-lookup"><span data-stu-id="a1e96-114">`New-Item` can also set the value of the items that it creates.</span></span> <span data-ttu-id="a1e96-115">Als er bijvoorbeeld een nieuw bestand wordt gemaakt, `New-Item` kan de eerste inhoud aan het bestand worden toegevoegd.</span><span class="sxs-lookup"><span data-stu-id="a1e96-115">For example, when it creates a new file, `New-Item` can add initial content to the file.</span></span>

## <span data-ttu-id="a1e96-116">VOORBEELDEN</span><span class="sxs-lookup"><span data-stu-id="a1e96-116">EXAMPLES</span></span>

### <span data-ttu-id="a1e96-117">Voor beeld 1: een bestand in de huidige map maken</span><span class="sxs-lookup"><span data-stu-id="a1e96-117">Example 1: Create a file in the current directory</span></span>

<span data-ttu-id="a1e96-118">Met deze opdracht maakt u een tekst bestand met de naam ' testfile1.txt ' in de huidige map.</span><span class="sxs-lookup"><span data-stu-id="a1e96-118">This command creates a text file that is named "testfile1.txt" in the current directory.</span></span> <span data-ttu-id="a1e96-119">De punt ('. ') in de waarde van de para meter **Path** geeft aan dat de huidige map is.</span><span class="sxs-lookup"><span data-stu-id="a1e96-119">The dot ('.') in the value of the **Path** parameter indicates the current directory.</span></span> <span data-ttu-id="a1e96-120">De aanhalings tekens die volgen op de **waarde** para meter wordt toegevoegd aan het bestand als inhoud.</span><span class="sxs-lookup"><span data-stu-id="a1e96-120">The quoted text that follows the **Value** parameter is added to the file as content.</span></span>

```powershell
New-Item -Path . -Name "testfile1.txt" -ItemType "file" -Value "This is a text string."
```

### <span data-ttu-id="a1e96-121">Voor beeld 2: een directory maken</span><span class="sxs-lookup"><span data-stu-id="a1e96-121">Example 2: Create a directory</span></span>

<span data-ttu-id="a1e96-122">Met deze opdracht maakt u een map met de naam Logboeken in het `C:` station.</span><span class="sxs-lookup"><span data-stu-id="a1e96-122">This command creates a directory named "Logfiles" in the `C:` drive.</span></span> <span data-ttu-id="a1e96-123">De para meter **item** type geeft aan dat het nieuwe item een map is, niet een bestand of een ander bestandssysteem object.</span><span class="sxs-lookup"><span data-stu-id="a1e96-123">The **ItemType** parameter specifies that the new item is a directory, not a file or other file system object.</span></span>

```powershell
New-Item -Path "c:\" -Name "logfiles" -ItemType "directory"
```

### <span data-ttu-id="a1e96-124">Voor beeld 3: een profiel maken</span><span class="sxs-lookup"><span data-stu-id="a1e96-124">Example 3: Create a profile</span></span>

<span data-ttu-id="a1e96-125">Met deze opdracht maakt u een Power shell-profiel in het pad dat is opgegeven door de `$profile` variabele.</span><span class="sxs-lookup"><span data-stu-id="a1e96-125">This command creates a PowerShell profile in the path that is specified by the `$profile` variable.</span></span>

<span data-ttu-id="a1e96-126">U kunt profielen gebruiken om Power shell aan te passen.</span><span class="sxs-lookup"><span data-stu-id="a1e96-126">You can use profiles to customize PowerShell.</span></span> <span data-ttu-id="a1e96-127">`$profile` is een automatische (ingebouwde) variabele waarmee het pad en de bestands naam van het profiel ' CurrentUser/CurrentHost ' worden opgeslagen.</span><span class="sxs-lookup"><span data-stu-id="a1e96-127">`$profile` is an automatic (built-in) variable that stores the path and file name of the "CurrentUser/CurrentHost" profile.</span></span> <span data-ttu-id="a1e96-128">Het profiel bestaat standaard niet, hoewel in Power shell een pad en een bestands naam worden opgeslagen.</span><span class="sxs-lookup"><span data-stu-id="a1e96-128">By default, the profile does not exist, even though PowerShell stores a path and file name for it.</span></span>

<span data-ttu-id="a1e96-129">In deze opdracht vertegenwoordigt de `$profile` variabele het pad van het bestand.</span><span class="sxs-lookup"><span data-stu-id="a1e96-129">In this command, the `$profile` variable represents the path of the file.</span></span> <span data-ttu-id="a1e96-130">**Item** type-para meter geeft aan dat met de opdracht een bestand wordt gemaakt.</span><span class="sxs-lookup"><span data-stu-id="a1e96-130">**ItemType** parameter specifies that the command creates a file.</span></span> <span data-ttu-id="a1e96-131">Met de para meter **Force** kunt u een bestand in het profielpad maken, zelfs wanneer de mappen in het pad niet bestaan.</span><span class="sxs-lookup"><span data-stu-id="a1e96-131">The **Force** parameter lets you create a file in the profile path, even when the directories in the path do not exist.</span></span>

<span data-ttu-id="a1e96-132">Nadat u een profiel hebt gemaakt, kunt u aliassen, functies en scripts in het profiel invoeren om uw shell aan te passen.</span><span class="sxs-lookup"><span data-stu-id="a1e96-132">After you create a profile, you can enter aliases, functions, and scripts in the profile to customize your shell.</span></span>

<span data-ttu-id="a1e96-133">Zie [about_Automatic_Variables](../Microsoft.PowerShell.Core/About/about_Automatic_Variables.md) en [about_Profiles](../Microsoft.PowerShell.Core/About/about_Profiles.md)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="a1e96-133">For more information, see [about_Automatic_Variables](../Microsoft.PowerShell.Core/About/about_Automatic_Variables.md) and [about_Profiles](../Microsoft.PowerShell.Core/About/about_Profiles.md).</span></span>

```powershell
New-Item -Path $profile -ItemType "file" -Force
```

> [!NOTE]
> <span data-ttu-id="a1e96-134">Wanneer u met deze methode een bestand maakt, wordt het resulterende bestand gecodeerd als UTF-8 zonder een byte order-Mark (BOM).</span><span class="sxs-lookup"><span data-stu-id="a1e96-134">When you create a file using this method, the resulting file is encoded as UTF-8 without a byte-order-mark (BOM).</span></span>

### <span data-ttu-id="a1e96-135">Voor beeld 4: een map in een andere Directory maken</span><span class="sxs-lookup"><span data-stu-id="a1e96-135">Example 4: Create a directory in a different directory</span></span>

<span data-ttu-id="a1e96-136">In dit voor beeld wordt een nieuwe map scripts gemaakt in de map "C:\PS-Test".</span><span class="sxs-lookup"><span data-stu-id="a1e96-136">This example creates a new Scripts directory in the "C:\PS-Test" directory.</span></span>

<span data-ttu-id="a1e96-137">De naam van het nieuwe directory-item, "scripts", is opgenomen in de waarde van de para meter **Path** , in plaats van dat wordt opgegeven in de waarde **naam**.</span><span class="sxs-lookup"><span data-stu-id="a1e96-137">The name of the new directory item, "Scripts", is included in the value of **Path** parameter, instead of being specified in the value of **Name**.</span></span> <span data-ttu-id="a1e96-138">Zoals aangegeven door de syntaxis, is het opdracht formulier geldig.</span><span class="sxs-lookup"><span data-stu-id="a1e96-138">As indicated by the syntax, either command form is valid.</span></span>

```powershell
New-Item -ItemType "directory" -Path "c:\ps-test\scripts"
```

### <span data-ttu-id="a1e96-139">Voor beeld 5: meerdere bestanden maken</span><span class="sxs-lookup"><span data-stu-id="a1e96-139">Example 5: Create multiple files</span></span>

<span data-ttu-id="a1e96-140">In dit voor beeld worden bestanden gemaakt in twee verschillende directory's.</span><span class="sxs-lookup"><span data-stu-id="a1e96-140">This example creates files in two different directories.</span></span> <span data-ttu-id="a1e96-141">Omdat **Path** meerdere teken reeksen accepteert, kunt u deze gebruiken om meerdere items te maken.</span><span class="sxs-lookup"><span data-stu-id="a1e96-141">Because **Path** takes multiple strings, you can use it to create multiple items.</span></span>

```powershell
New-Item -ItemType "file" -Path "c:\ps-test\test.txt", "c:\ps-test\Logs\test.log"
```

### <span data-ttu-id="a1e96-142">Voor beeld 6: gebruik de para meter-Force om mappen opnieuw te maken</span><span class="sxs-lookup"><span data-stu-id="a1e96-142">Example 6: Use the -Force parameter to attempt to recreate folders</span></span>

<span data-ttu-id="a1e96-143">In dit voor beeld wordt een map gemaakt met een bestand in.</span><span class="sxs-lookup"><span data-stu-id="a1e96-143">This example creates a folder with a file inside.</span></span> <span data-ttu-id="a1e96-144">Vervolgens wordt geprobeerd om dezelfde map te maken met `-Force` .</span><span class="sxs-lookup"><span data-stu-id="a1e96-144">Then, attempts to create the same folder using `-Force`.</span></span> <span data-ttu-id="a1e96-145">De map wordt niet overschreven, maar er wordt gewoon het bestaande map-object geretourneerd waarbij het bestand intact is gemaakt.</span><span class="sxs-lookup"><span data-stu-id="a1e96-145">It will not overwrite the folder but simply return the existing folder object with the file created intact.</span></span>

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

### <span data-ttu-id="a1e96-146">Voor beeld 7: gebruik de para meter-Force om bestaande bestanden te overschrijven</span><span class="sxs-lookup"><span data-stu-id="a1e96-146">Example 7: Use the -Force parameter to overwrite existing files</span></span>

<span data-ttu-id="a1e96-147">In dit voor beeld wordt een bestand gemaakt met een waarde en wordt het bestand vervolgens opnieuw gemaakt met `-Force` .</span><span class="sxs-lookup"><span data-stu-id="a1e96-147">This example creates a file with a value and then recreates the file using `-Force`.</span></span> <span data-ttu-id="a1e96-148">Hiermee wordt het bestaande bestand overschreven, waardoor de inhoud verloren gaat, omdat u de eigenschap length kunt zien</span><span class="sxs-lookup"><span data-stu-id="a1e96-148">This overwrites The existing file and it will lose it's content as you can see by the length property</span></span>

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
> <span data-ttu-id="a1e96-149">Wanneer u gebruikt `New-Item` met de `-Force` switch om register sleutels te maken, werkt de opdracht hetzelfde als bij het overschrijven van een bestand.</span><span class="sxs-lookup"><span data-stu-id="a1e96-149">When using `New-Item` with the `-Force` switch to create registry keys, the command will behave the same as when overwriting a file.</span></span> <span data-ttu-id="a1e96-150">Als de register sleutel al bestaat, worden de sleutel en alle eigenschappen en waarden overschreven met een lege register sleutel.</span><span class="sxs-lookup"><span data-stu-id="a1e96-150">If the registry key already exists, the key and all properties and values will be overwritten with an empty registry key.</span></span>

## <span data-ttu-id="a1e96-151">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="a1e96-151">PARAMETERS</span></span>

### <span data-ttu-id="a1e96-152">-Credential</span><span class="sxs-lookup"><span data-stu-id="a1e96-152">-Credential</span></span>

> [!NOTE]
> <span data-ttu-id="a1e96-153">Deze para meter wordt niet ondersteund door providers die zijn geïnstalleerd met Power shell.</span><span class="sxs-lookup"><span data-stu-id="a1e96-153">This parameter is not supported by any providers installed with PowerShell.</span></span> <span data-ttu-id="a1e96-154">Gebruik om een andere gebruiker te imiteren of uw referenties te verhogen wanneer u deze cmdlet uitvoert `Invoke-Command` .</span><span class="sxs-lookup"><span data-stu-id="a1e96-154">To impersonate another user or elevate your credentials when running this cmdlet, use `Invoke-Command`.</span></span>

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

### <span data-ttu-id="a1e96-155">-Force</span><span class="sxs-lookup"><span data-stu-id="a1e96-155">-Force</span></span>

<span data-ttu-id="a1e96-156">Hiermee wordt de cmdlet gedwongen een item te maken dat over een bestaand alleen-lezen item schrijft.</span><span class="sxs-lookup"><span data-stu-id="a1e96-156">Forces this cmdlet to create an item that writes over an existing read-only item.</span></span> <span data-ttu-id="a1e96-157">De implementatie varieert van provider tot provider.</span><span class="sxs-lookup"><span data-stu-id="a1e96-157">Implementation varies from provider to provider.</span></span> <span data-ttu-id="a1e96-158">Zelfs met behulp van de para meter **forceren** , kan de cmdlet geen beveiligings beperkingen opheffen.</span><span class="sxs-lookup"><span data-stu-id="a1e96-158">Even using the **Force** parameter, the cmdlet cannot override security restrictions.</span></span>

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

### <span data-ttu-id="a1e96-159">-Item type</span><span class="sxs-lookup"><span data-stu-id="a1e96-159">-ItemType</span></span>

<span data-ttu-id="a1e96-160">Hiermee wordt het type provider opgegeven van het nieuwe item.</span><span class="sxs-lookup"><span data-stu-id="a1e96-160">Specifies the provider-specified type of the new item.</span></span> <span data-ttu-id="a1e96-161">De beschik bare waarden van deze para meter zijn afhankelijk van de huidige provider die u gebruikt.</span><span class="sxs-lookup"><span data-stu-id="a1e96-161">The available values of this parameter depend on the current provider you are using.</span></span>

<span data-ttu-id="a1e96-162">Als uw locatie zich in een station bevindt `FileSystem` , zijn de volgende waarden toegestaan:</span><span class="sxs-lookup"><span data-stu-id="a1e96-162">If your location is in a `FileSystem` drive, the following values are allowed:</span></span>

- <span data-ttu-id="a1e96-163">Bestand</span><span class="sxs-lookup"><span data-stu-id="a1e96-163">File</span></span>
- <span data-ttu-id="a1e96-164">Directory</span><span class="sxs-lookup"><span data-stu-id="a1e96-164">Directory</span></span>
- <span data-ttu-id="a1e96-165">SymbolicLink</span><span class="sxs-lookup"><span data-stu-id="a1e96-165">SymbolicLink</span></span>
- <span data-ttu-id="a1e96-166">Verbinding</span><span class="sxs-lookup"><span data-stu-id="a1e96-166">Junction</span></span>
- <span data-ttu-id="a1e96-167">Hard link</span><span class="sxs-lookup"><span data-stu-id="a1e96-167">HardLink</span></span>

<span data-ttu-id="a1e96-168">Wanneer u met deze methode een bestand maakt, wordt het resulterende bestand gecodeerd als UTF-8 zonder een byte order-Mark (BOM).</span><span class="sxs-lookup"><span data-stu-id="a1e96-168">When you create a file using this method, the resulting file is encoded as UTF-8 without a byte-order-mark (BOM).</span></span>

<span data-ttu-id="a1e96-169">`Certificate`Dit zijn de waarden die u kunt opgeven in een station:</span><span class="sxs-lookup"><span data-stu-id="a1e96-169">In a `Certificate` drive, these are the values you can specify:</span></span>

- <span data-ttu-id="a1e96-170">Certificaat provider</span><span class="sxs-lookup"><span data-stu-id="a1e96-170">Certificate Provider</span></span>
- <span data-ttu-id="a1e96-171">Certificaat</span><span class="sxs-lookup"><span data-stu-id="a1e96-171">Certificate</span></span>
- <span data-ttu-id="a1e96-172">Opslaan</span><span class="sxs-lookup"><span data-stu-id="a1e96-172">Store</span></span>
- <span data-ttu-id="a1e96-173">StoreLocation</span><span class="sxs-lookup"><span data-stu-id="a1e96-173">StoreLocation</span></span>

<span data-ttu-id="a1e96-174">Zie [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="a1e96-174">For more information see [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md).</span></span>

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

### <span data-ttu-id="a1e96-175">-Name</span><span class="sxs-lookup"><span data-stu-id="a1e96-175">-Name</span></span>

<span data-ttu-id="a1e96-176">Hiermee geeft u de naam van het nieuwe item.</span><span class="sxs-lookup"><span data-stu-id="a1e96-176">Specifies the name of the new item.</span></span> <span data-ttu-id="a1e96-177">U kunt de naam van het nieuwe item in de waarde van de para meter **name** of **Path** opgeven, en u kunt het pad van het nieuwe item opgeven in de **naam** of de waarde van het **pad** .</span><span class="sxs-lookup"><span data-stu-id="a1e96-177">You can specify the name of the new item in the **Name** or **Path** parameter value, and you can specify the path of the new item in **Name** or **Path** value.</span></span> <span data-ttu-id="a1e96-178">Namen van items die worden door gegeven met de para meter **name** , worden gemaakt ten opzichte van de waarde van de para meter **Path** .</span><span class="sxs-lookup"><span data-stu-id="a1e96-178">Items names passed using the **Name** parameter are created relative to the value of the **Path** parameter.</span></span>

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

### <span data-ttu-id="a1e96-179">-Path</span><span class="sxs-lookup"><span data-stu-id="a1e96-179">-Path</span></span>

<span data-ttu-id="a1e96-180">Hiermee geeft u het pad van de locatie van het nieuwe item.</span><span class="sxs-lookup"><span data-stu-id="a1e96-180">Specifies the path of the location of the new item.</span></span> <span data-ttu-id="a1e96-181">De standaard waarde is de huidige locatie wanneer het **pad** wordt wegge laten.</span><span class="sxs-lookup"><span data-stu-id="a1e96-181">The default is the current location when **Path** is omitted.</span></span> <span data-ttu-id="a1e96-182">U kunt de naam van het nieuwe item opgeven in de **naam** of het **pad** op te geven.</span><span class="sxs-lookup"><span data-stu-id="a1e96-182">You can specify the name of the new item in **Name** , or include it in **Path**.</span></span> <span data-ttu-id="a1e96-183">Namen van items die worden door gegeven met de para meter **name** , worden gemaakt ten opzichte van de waarde van de para meter **Path** .</span><span class="sxs-lookup"><span data-stu-id="a1e96-183">Items names passed using the **Name** parameter are created relative to the value of the **Path** parameter.</span></span>

<span data-ttu-id="a1e96-184">Voor deze cmdlet werkt de para meter **Path** als de **LiteralPath** -para meter van andere cmdlets.</span><span class="sxs-lookup"><span data-stu-id="a1e96-184">For this cmdlet, the **Path** parameter works like the **LiteralPath** parameter of other cmdlets.</span></span>
<span data-ttu-id="a1e96-185">Joker tekens worden niet geïnterpreteerd.</span><span class="sxs-lookup"><span data-stu-id="a1e96-185">Wildcard characters are not interpreted.</span></span> <span data-ttu-id="a1e96-186">Alle tekens worden door gegeven aan de provider van de locatie.</span><span class="sxs-lookup"><span data-stu-id="a1e96-186">All characters are passed to the location's provider.</span></span> <span data-ttu-id="a1e96-187">De provider biedt mogelijk geen ondersteuning voor alle tekens.</span><span class="sxs-lookup"><span data-stu-id="a1e96-187">The provider may not support all characters.</span></span> <span data-ttu-id="a1e96-188">U kunt bijvoorbeeld geen bestands naam maken die een asterisk ()- `*` teken bevat.</span><span class="sxs-lookup"><span data-stu-id="a1e96-188">For example, you cannot create a filename that contains an asterisk (`*`) character.</span></span>

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

### <span data-ttu-id="a1e96-189">-UseTransaction</span><span class="sxs-lookup"><span data-stu-id="a1e96-189">-UseTransaction</span></span>

<span data-ttu-id="a1e96-190">Hiermee wordt de opdracht opgenomen in de actieve transactie.</span><span class="sxs-lookup"><span data-stu-id="a1e96-190">Includes the command in the active transaction.</span></span> <span data-ttu-id="a1e96-191">Deze parameter is alleen geldig wanneer een transactie wordt uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="a1e96-191">This parameter is valid only when a transaction is in progress.</span></span> <span data-ttu-id="a1e96-192">Zie [about_Transactions](../Microsoft.PowerShell.Core/About/about_Transactions.md)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="a1e96-192">For more information, see [about_Transactions](../Microsoft.PowerShell.Core/About/about_Transactions.md).</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: usetx

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="a1e96-193">-Waarde</span><span class="sxs-lookup"><span data-stu-id="a1e96-193">-Value</span></span>

<span data-ttu-id="a1e96-194">Hiermee geeft u de waarde van het nieuwe item op.</span><span class="sxs-lookup"><span data-stu-id="a1e96-194">Specifies the value of the new item.</span></span> <span data-ttu-id="a1e96-195">U kunt ook een waarde door sluizen naar `New-Item` .</span><span class="sxs-lookup"><span data-stu-id="a1e96-195">You can also pipe a value to `New-Item`.</span></span>

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

### <span data-ttu-id="a1e96-196">-Confirm</span><span class="sxs-lookup"><span data-stu-id="a1e96-196">-Confirm</span></span>

<span data-ttu-id="a1e96-197">Hiermee wordt u gevraagd om bevestiging voordat u de cmdlet uitvoert.</span><span class="sxs-lookup"><span data-stu-id="a1e96-197">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="a1e96-198">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="a1e96-198">-WhatIf</span></span>

<span data-ttu-id="a1e96-199">Hiermee wordt weergegeven wat er zou gebeuren als u de cmdlet uitvoert.</span><span class="sxs-lookup"><span data-stu-id="a1e96-199">Shows what would happen if the cmdlet runs.</span></span>
<span data-ttu-id="a1e96-200">De cmdlet wordt niet uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="a1e96-200">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="a1e96-201">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="a1e96-201">CommonParameters</span></span>

<span data-ttu-id="a1e96-202">Deze cmdlet biedt ondersteuning voor de algemene para meters: `-Debug` , `-ErrorAction` , `-ErrorVariable` , `-InformationAction` , `-InformationVariable` , `-OutVariable` , `-OutBuffer` , `-PipelineVariable` , `-Verbose` , `-WarningAction` en `-WarningVariable` .</span><span class="sxs-lookup"><span data-stu-id="a1e96-202">This cmdlet supports the common parameters: `-Debug`, `-ErrorAction`, `-ErrorVariable`, `-InformationAction`, `-InformationVariable`, `-OutVariable`, `-OutBuffer`, `-PipelineVariable`, `-Verbose`, `-WarningAction`, and `-WarningVariable`.</span></span> <span data-ttu-id="a1e96-203">Zie [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="a1e96-203">For more information, see [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md).</span></span>

## <span data-ttu-id="a1e96-204">INVOER</span><span class="sxs-lookup"><span data-stu-id="a1e96-204">INPUTS</span></span>

### <span data-ttu-id="a1e96-205">System. object</span><span class="sxs-lookup"><span data-stu-id="a1e96-205">System.Object</span></span>

<span data-ttu-id="a1e96-206">U kunt een waarde voor het nieuwe item door sluizen naar deze cmdlet.</span><span class="sxs-lookup"><span data-stu-id="a1e96-206">You can pipe a value for the new item to this cmdlet.</span></span>

## <span data-ttu-id="a1e96-207">UITVOER</span><span class="sxs-lookup"><span data-stu-id="a1e96-207">OUTPUTS</span></span>

### <span data-ttu-id="a1e96-208">System. object</span><span class="sxs-lookup"><span data-stu-id="a1e96-208">System.Object</span></span>

<span data-ttu-id="a1e96-209">Met deze cmdlet wordt het item geretourneerd dat wordt gemaakt.</span><span class="sxs-lookup"><span data-stu-id="a1e96-209">This cmdlet returns the item that it creates.</span></span>

## <span data-ttu-id="a1e96-210">OPMERKINGEN</span><span class="sxs-lookup"><span data-stu-id="a1e96-210">NOTES</span></span>

<span data-ttu-id="a1e96-211">`New-Item` is ontworpen om te werken met de gegevens die door elke provider worden weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="a1e96-211">`New-Item` is designed to work with the data exposed by any provider.</span></span> <span data-ttu-id="a1e96-212">Als u een lijst wilt weer geven van de providers die beschikbaar zijn in uw sessie, typt u `Get-PsProvider` .</span><span class="sxs-lookup"><span data-stu-id="a1e96-212">To list the providers available in your session, type `Get-PsProvider`.</span></span> <span data-ttu-id="a1e96-213">Zie [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="a1e96-213">For more information, see [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md).</span></span>

## <span data-ttu-id="a1e96-214">GERELATEERDE KOPPELINGEN</span><span class="sxs-lookup"><span data-stu-id="a1e96-214">RELATED LINKS</span></span>

[<span data-ttu-id="a1e96-215">Wissen-item</span><span class="sxs-lookup"><span data-stu-id="a1e96-215">Clear-Item</span></span>](Clear-Item.md)

[<span data-ttu-id="a1e96-216">Kopie-item</span><span class="sxs-lookup"><span data-stu-id="a1e96-216">Copy-Item</span></span>](Copy-Item.md)

[<span data-ttu-id="a1e96-217">Get-item</span><span class="sxs-lookup"><span data-stu-id="a1e96-217">Get-Item</span></span>](Get-Item.md)

[<span data-ttu-id="a1e96-218">Invoke-item</span><span class="sxs-lookup"><span data-stu-id="a1e96-218">Invoke-Item</span></span>](Invoke-Item.md)

[<span data-ttu-id="a1e96-219">Item verplaatsen</span><span class="sxs-lookup"><span data-stu-id="a1e96-219">Move-Item</span></span>](Move-Item.md)

[<span data-ttu-id="a1e96-220">Verwijderen-item</span><span class="sxs-lookup"><span data-stu-id="a1e96-220">Remove-Item</span></span>](Remove-Item.md)

[<span data-ttu-id="a1e96-221">Naam wijzigen-item</span><span class="sxs-lookup"><span data-stu-id="a1e96-221">Rename-Item</span></span>](Rename-Item.md)

[<span data-ttu-id="a1e96-222">Set-item</span><span class="sxs-lookup"><span data-stu-id="a1e96-222">Set-Item</span></span>](Set-Item.md)

[<span data-ttu-id="a1e96-223">about_Providers</span><span class="sxs-lookup"><span data-stu-id="a1e96-223">about_Providers</span></span>](../Microsoft.PowerShell.Core/About/about_Providers.md)
