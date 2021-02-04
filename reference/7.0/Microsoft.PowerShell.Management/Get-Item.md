---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 12/18/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/get-item?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-Item
ms.openlocfilehash: e848cc8c77e1d0dff6eb1f98d56c8ed37e44a653
ms.sourcegitcommit: bf07cffb2a66dec94bf3576e197090f958701f18
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 12/19/2020
ms.locfileid: "97692815"
---
# <span data-ttu-id="7e0ce-103">Get-Item</span><span class="sxs-lookup"><span data-stu-id="7e0ce-103">Get-Item</span></span>

## <span data-ttu-id="7e0ce-104">SAMENVATTING</span><span class="sxs-lookup"><span data-stu-id="7e0ce-104">SYNOPSIS</span></span>
<span data-ttu-id="7e0ce-105">Hiermee wordt het item op de opgegeven locatie opgehaald.</span><span class="sxs-lookup"><span data-stu-id="7e0ce-105">Gets the item at the specified location.</span></span>

## <span data-ttu-id="7e0ce-106">SYNTAXIS</span><span class="sxs-lookup"><span data-stu-id="7e0ce-106">SYNTAX</span></span>

### <span data-ttu-id="7e0ce-107">Pad (standaard)</span><span class="sxs-lookup"><span data-stu-id="7e0ce-107">Path (Default)</span></span>

```
Get-Item [-Path] <String[]> [-Filter <String>] [-Include <String[]>] [-Exclude <String[]>] [-Force]
 [-Credential <PSCredential>] [-Stream <String[]>] [<CommonParameters>]
```

### <span data-ttu-id="7e0ce-108">LiteralPath</span><span class="sxs-lookup"><span data-stu-id="7e0ce-108">LiteralPath</span></span>

```
Get-Item -LiteralPath <String[]> [-Filter <String>] [-Include <String[]>] [-Exclude <String[]>]
 [-Force] [-Credential <PSCredential>] [-Stream <String[]>] [<CommonParameters>]
```

## <span data-ttu-id="7e0ce-109">BESCHRIJVING</span><span class="sxs-lookup"><span data-stu-id="7e0ce-109">DESCRIPTION</span></span>

<span data-ttu-id="7e0ce-110">`Get-Item`Met de cmdlet wordt het item op de opgegeven locatie opgehaald.</span><span class="sxs-lookup"><span data-stu-id="7e0ce-110">The `Get-Item` cmdlet gets the item at the specified location.</span></span> <span data-ttu-id="7e0ce-111">De inhoud van het item op de locatie wordt niet opgehaald, tenzij u een Joker teken ( `*` ) gebruikt om alle inhoud van het item aan te vragen.</span><span class="sxs-lookup"><span data-stu-id="7e0ce-111">It doesn't get the contents of the item at the location unless you use a wildcard character (`*`) to request all the contents of the item.</span></span>

<span data-ttu-id="7e0ce-112">Deze cmdlet wordt gebruikt door Power shell-providers om door verschillende typen gegevens archieven te navigeren.</span><span class="sxs-lookup"><span data-stu-id="7e0ce-112">This cmdlet is used by PowerShell providers to navigate through different types of data stores.</span></span>

## <span data-ttu-id="7e0ce-113">VOORBEELDEN</span><span class="sxs-lookup"><span data-stu-id="7e0ce-113">EXAMPLES</span></span>

### <span data-ttu-id="7e0ce-114">Voor beeld 1: de huidige map ophalen</span><span class="sxs-lookup"><span data-stu-id="7e0ce-114">Example 1: Get the current directory</span></span>

<span data-ttu-id="7e0ce-115">In dit voor beeld wordt de huidige map opgehaald.</span><span class="sxs-lookup"><span data-stu-id="7e0ce-115">This example gets the current directory.</span></span> <span data-ttu-id="7e0ce-116">De punt ('. ') staat voor het item op de huidige locatie (niet de inhoud).</span><span class="sxs-lookup"><span data-stu-id="7e0ce-116">The dot ('.') represents the item at the current location (not its contents).</span></span>

```powershell
Get-Item .
```

```output
Directory: C:\

Mode                LastWriteTime     Length Name
----                -------------     ------ ----
d----         7/26/2006  10:01 AM            ps-test
```

### <span data-ttu-id="7e0ce-117">Voor beeld 2: alle items in de huidige map ophalen</span><span class="sxs-lookup"><span data-stu-id="7e0ce-117">Example 2: Get all the items in the current directory</span></span>

<span data-ttu-id="7e0ce-118">In dit voor beeld worden alle items in de huidige map opgehaald.</span><span class="sxs-lookup"><span data-stu-id="7e0ce-118">This example gets all the items in the current directory.</span></span> <span data-ttu-id="7e0ce-119">Het Joker teken ( `*` ) vertegenwoordigt alle inhoud van het huidige item.</span><span class="sxs-lookup"><span data-stu-id="7e0ce-119">The wildcard character (`*`) represents all the contents of the current item.</span></span>

```powershell
Get-Item *
```

```output
Directory: C:\ps-test

Mode                LastWriteTime     Length Name
----                -------------     ------ ----
d----         7/26/2006   9:29 AM            Logs
d----         7/26/2006   9:26 AM            Recs
-a---         7/26/2006   9:28 AM         80 date.csv
-a---         7/26/2006  10:01 AM         30 filenoext
-a---         7/26/2006   9:30 AM      11472 process.doc
-a---         7/14/2006  10:47 AM         30 test.txt
```

### <span data-ttu-id="7e0ce-120">Voor beeld 3: de huidige map van een station ophalen</span><span class="sxs-lookup"><span data-stu-id="7e0ce-120">Example 3: Get the current directory of a drive</span></span>

<span data-ttu-id="7e0ce-121">In dit voor beeld wordt de huidige map van het `C:` station opgehaald.</span><span class="sxs-lookup"><span data-stu-id="7e0ce-121">This example gets the current directory of the `C:` drive.</span></span> <span data-ttu-id="7e0ce-122">Het opgehaalde object staat alleen voor de map en niet de inhoud ervan.</span><span class="sxs-lookup"><span data-stu-id="7e0ce-122">The object that is retrieved represents only the directory, not its contents.</span></span>

```powershell
Get-Item C:\
```

### <span data-ttu-id="7e0ce-123">Voor beeld 4: items in het opgegeven station ophalen</span><span class="sxs-lookup"><span data-stu-id="7e0ce-123">Example 4: Get items in the specified drive</span></span>

<span data-ttu-id="7e0ce-124">In dit voor beeld worden de items in het `C:` station opgehaald.</span><span class="sxs-lookup"><span data-stu-id="7e0ce-124">This example gets the items in the `C:` drive.</span></span> <span data-ttu-id="7e0ce-125">Het Joker teken ( `*` ) vertegenwoordigt alle items in de container, niet alleen de container.</span><span class="sxs-lookup"><span data-stu-id="7e0ce-125">The wildcard character (`*`) represents all the items in the container, not just the container.</span></span>

```powershell
Get-Item C:\*
```

<span data-ttu-id="7e0ce-126">Gebruik in Power shell één asterisk ( `*` ) om inhoud op te halen in plaats van de traditionele `*.*` .</span><span class="sxs-lookup"><span data-stu-id="7e0ce-126">In PowerShell, use a single asterisk (`*`) to get contents, instead of the traditional `*.*`.</span></span> <span data-ttu-id="7e0ce-127">De indeling wordt letterlijk geïnterpreteerd, waardoor `*.*` er geen mappen of bestands namen worden opgehaald zonder een punt.</span><span class="sxs-lookup"><span data-stu-id="7e0ce-127">The format is interpreted literally, so `*.*` wouldn't retrieve directories or filenames without a dot.</span></span>

### <span data-ttu-id="7e0ce-128">Voor beeld 5: een eigenschap ophalen in de opgegeven map</span><span class="sxs-lookup"><span data-stu-id="7e0ce-128">Example 5: Get a property in the specified directory</span></span>

<span data-ttu-id="7e0ce-129">In dit voor beeld wordt de eigenschap **LastAccessTime** van de `C:\Windows` Directory opgehaald.</span><span class="sxs-lookup"><span data-stu-id="7e0ce-129">This example gets the **LastAccessTime** property of the `C:\Windows` directory.</span></span> <span data-ttu-id="7e0ce-130">**LastAccessTime** is slechts één eigenschap van File System directory's.</span><span class="sxs-lookup"><span data-stu-id="7e0ce-130">**LastAccessTime** is just one property of file system directories.</span></span> <span data-ttu-id="7e0ce-131">Als u alle eigenschappen van een map wilt weer geven, typt u `(Get-Item <directory-name>) | Get-Member` .</span><span class="sxs-lookup"><span data-stu-id="7e0ce-131">To see all the properties of a directory, type `(Get-Item <directory-name>) | Get-Member`.</span></span>

```powershell
(Get-Item C:\Windows).LastAccessTime
```

### <span data-ttu-id="7e0ce-132">Voor beeld 6: de inhoud van een register sleutel weer geven</span><span class="sxs-lookup"><span data-stu-id="7e0ce-132">Example 6: Show the contents of a registry key</span></span>

<span data-ttu-id="7e0ce-133">In dit voor beeld wordt de inhoud van de register sleutel **micro soft. Power shell** weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="7e0ce-133">This example shows the contents of the **Microsoft.PowerShell** registry key.</span></span> <span data-ttu-id="7e0ce-134">U kunt deze cmdlet gebruiken met de Power shell-register provider om register sleutels en subsleutels op te halen, maar u moet de `Get-ItemProperty` cmdlet gebruiken om de register waarden en-gegevens op te halen.</span><span class="sxs-lookup"><span data-stu-id="7e0ce-134">You can use this cmdlet with the PowerShell Registry provider to get registry keys and subkeys, but you must use the `Get-ItemProperty` cmdlet to get the registry values and data.</span></span>

```powershell
Get-Item HKLM:\Software\Microsoft\Powershell\1\Shellids\Microsoft.Powershell\
```

### <span data-ttu-id="7e0ce-135">Voor beeld 7: items in een directory met een uitsluiting ophalen</span><span class="sxs-lookup"><span data-stu-id="7e0ce-135">Example 7: Get items in a directory that have an exclusion</span></span>

<span data-ttu-id="7e0ce-136">In dit voor beeld worden items in de Windows-map met namen die een punt ( `.` ) bevatten, maar niet beginnen met `w*` . Dit voor beeld werkt alleen wanneer het pad een Joker teken ( `*` ) bevat om de inhoud van het item op te geven.</span><span class="sxs-lookup"><span data-stu-id="7e0ce-136">This example gets items in the Windows directory with names that include a dot (`.`), but don't begin with `w*`.This example works only when the path includes a wildcard character (`*`) to specify the contents of the item.</span></span>

```powershell
Get-Item C:\Windows\*.* -Exclude "w*"
```

### <span data-ttu-id="7e0ce-137">Voor beeld 8: koppelings gegevens ophalen</span><span class="sxs-lookup"><span data-stu-id="7e0ce-137">Example 8: Getting hardlink information</span></span>

<span data-ttu-id="7e0ce-138">In Power shell 6,2 is een alternatieve weer gave toegevoegd om koppelings gegevens op te halen.</span><span class="sxs-lookup"><span data-stu-id="7e0ce-138">In PowerShell 6.2, an alternate view was added to get hardlink information.</span></span> <span data-ttu-id="7e0ce-139">Als u de vaste gegevens wilt ophalen, pipet u de uitvoer naar `Format-Table -View childrenWithHardlink`</span><span class="sxs-lookup"><span data-stu-id="7e0ce-139">To get the hardlink information, pipe the output to `Format-Table -View childrenWithHardlink`</span></span>

```powershell
Get-Item -Path C:\PathWhichIsAHardLink | Format-Table -View childrenWithHardlink
```

### <span data-ttu-id="7e0ce-140">Voor beeld 9: uitvoer voor experimentele functie PSUnixFileStat</span><span class="sxs-lookup"><span data-stu-id="7e0ce-140">Example 9: Output for experimental feature PSUnixFileStat</span></span>

<span data-ttu-id="7e0ce-141">In Power shell 7 op UNIX-systemen biedt de experimentele functie **PSUnixFileStat** UNIX-achtige uitvoer:</span><span class="sxs-lookup"><span data-stu-id="7e0ce-141">In PowerShell 7 on Unix systems, the experimental feature **PSUnixFileStat** provides Unix-like output:</span></span>

```powershell
PS> Get-Item /Users
```

```Output
    Directory: /

UnixMode    User  Group   LastWriteTime      Size  Name
--------    ----  -----   -------------      ----  ----
drwxr-xr-x  root  admin   12/20/2019 11:46   192   Users
```

<span data-ttu-id="7e0ce-142">De nieuwe eigenschappen die nu deel uitmaken van de uitvoer zijn:</span><span class="sxs-lookup"><span data-stu-id="7e0ce-142">The new properties that are now part of the output are:</span></span>

- <span data-ttu-id="7e0ce-143">**UnixMode** is de bestands machtigingen die worden weer gegeven op een UNIX-systeem</span><span class="sxs-lookup"><span data-stu-id="7e0ce-143">**UnixMode** is the file permissions as represented on a Unix system</span></span>
- <span data-ttu-id="7e0ce-144">De **gebruiker** is de bestands eigenaar</span><span class="sxs-lookup"><span data-stu-id="7e0ce-144">**User** is the file owner</span></span>
- <span data-ttu-id="7e0ce-145">**Groep** is de eigenaar van de groep</span><span class="sxs-lookup"><span data-stu-id="7e0ce-145">**Group** is the group owner</span></span>
- <span data-ttu-id="7e0ce-146">**Grootte** is de grootte van het bestand of de map zoals deze wordt weer gegeven op een UNIX-systeem</span><span class="sxs-lookup"><span data-stu-id="7e0ce-146">**Size** is the size of the file or directory as represented on a Unix system</span></span>

## <span data-ttu-id="7e0ce-147">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="7e0ce-147">PARAMETERS</span></span>

### <span data-ttu-id="7e0ce-148">-Stream</span><span class="sxs-lookup"><span data-stu-id="7e0ce-148">-Stream</span></span>

> [!NOTE]
> <span data-ttu-id="7e0ce-149">Deze para meter is alleen beschikbaar in Windows.</span><span class="sxs-lookup"><span data-stu-id="7e0ce-149">This Parameter is only available on Windows.</span></span>

<span data-ttu-id="7e0ce-150">Hiermee wordt de opgegeven alternatieve NTFS-bestands stroom opgehaald uit het bestand.</span><span class="sxs-lookup"><span data-stu-id="7e0ce-150">Gets the specified alternate NTFS file stream from the file.</span></span> <span data-ttu-id="7e0ce-151">Voer de naam van de stream in.</span><span class="sxs-lookup"><span data-stu-id="7e0ce-151">Enter the stream name.</span></span> <span data-ttu-id="7e0ce-152">Joker tekens worden ondersteund.</span><span class="sxs-lookup"><span data-stu-id="7e0ce-152">Wildcards are supported.</span></span> <span data-ttu-id="7e0ce-153">Als u alle streams wilt ophalen, gebruikt u een asterisk ( `*` ).</span><span class="sxs-lookup"><span data-stu-id="7e0ce-153">To get all streams, use an asterisk (`*`).</span></span> <span data-ttu-id="7e0ce-154">Deze para meter is niet geldig voor mappen.</span><span class="sxs-lookup"><span data-stu-id="7e0ce-154">This parameter isn't valid on folders.</span></span>

<span data-ttu-id="7e0ce-155">**Stream** is een dynamische para meter die de **File System** provider toevoegt aan de `Get-Item` cmdlet.</span><span class="sxs-lookup"><span data-stu-id="7e0ce-155">**Stream** is a dynamic parameter that the **FileSystem** provider adds to the `Get-Item` cmdlet.</span></span>
<span data-ttu-id="7e0ce-156">Deze para meter werkt alleen op stations met een bestands systeem.</span><span class="sxs-lookup"><span data-stu-id="7e0ce-156">This parameter works only in file system drives.</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: No alternate file streams
Accept pipeline input: False
Accept wildcard characters: True
```

### <span data-ttu-id="7e0ce-157">-Credential</span><span class="sxs-lookup"><span data-stu-id="7e0ce-157">-Credential</span></span>

> [!NOTE]
> <span data-ttu-id="7e0ce-158">Deze para meter wordt niet ondersteund door providers die zijn geïnstalleerd met Power shell.</span><span class="sxs-lookup"><span data-stu-id="7e0ce-158">This parameter isn't supported by any providers installed with PowerShell.</span></span>
> <span data-ttu-id="7e0ce-159">Gebruik [invoke-Command](../Microsoft.PowerShell.Core/Invoke-Command.md)om een andere gebruiker te imiteren of uw referenties te verhogen wanneer u deze cmdlet uitvoert.</span><span class="sxs-lookup"><span data-stu-id="7e0ce-159">To impersonate another user, or elevate your credentials when running this cmdlet, use [Invoke-Command](../Microsoft.PowerShell.Core/Invoke-Command.md).</span></span>

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

### <span data-ttu-id="7e0ce-160">-Uitsluiten</span><span class="sxs-lookup"><span data-stu-id="7e0ce-160">-Exclude</span></span>

<span data-ttu-id="7e0ce-161">Hiermee geeft u als een teken reeks matrix een item of items die met deze cmdlet worden uitgesloten in de bewerking.</span><span class="sxs-lookup"><span data-stu-id="7e0ce-161">Specifies, as a string array, an item or items that this cmdlet excludes in the operation.</span></span> <span data-ttu-id="7e0ce-162">De waarde van deze para meter komt in aanmerking voor de para meter **Path** .</span><span class="sxs-lookup"><span data-stu-id="7e0ce-162">The value of this parameter qualifies the **Path** parameter.</span></span> <span data-ttu-id="7e0ce-163">Voer een element of patroon van een pad in, zoals `*.txt` .</span><span class="sxs-lookup"><span data-stu-id="7e0ce-163">Enter a path element or pattern, such as `*.txt`.</span></span> <span data-ttu-id="7e0ce-164">Joker tekens zijn toegestaan.</span><span class="sxs-lookup"><span data-stu-id="7e0ce-164">Wildcard characters are permitted.</span></span> <span data-ttu-id="7e0ce-165">De **exclude** -para meter is alleen effectief wanneer de inhoud van een item wordt opgenomen, zoals `C:\Windows\*` , waarbij het Joker teken de inhoud van de `C:\Windows` map bevat.</span><span class="sxs-lookup"><span data-stu-id="7e0ce-165">The **Exclude** parameter is effective only when the command includes the contents of an item, such as `C:\Windows\*`, where the wildcard character specifies the contents of the `C:\Windows` directory.</span></span>

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

### <span data-ttu-id="7e0ce-166">-Filter</span><span class="sxs-lookup"><span data-stu-id="7e0ce-166">-Filter</span></span>

<span data-ttu-id="7e0ce-167">Hiermee geeft u een filter op om de para meter **Path** te kwalificeren.</span><span class="sxs-lookup"><span data-stu-id="7e0ce-167">Specifies a filter to qualify the **Path** parameter.</span></span> <span data-ttu-id="7e0ce-168">De [File System](../Microsoft.PowerShell.Core/About/about_FileSystem_Provider.md) -provider is de enige geïnstalleerde Power shell-provider die filters ondersteunt.</span><span class="sxs-lookup"><span data-stu-id="7e0ce-168">The [FileSystem](../Microsoft.PowerShell.Core/About/about_FileSystem_Provider.md) provider is the only installed PowerShell provider that supports filters.</span></span> <span data-ttu-id="7e0ce-169">Filters zijn efficiënter dan andere para meters.</span><span class="sxs-lookup"><span data-stu-id="7e0ce-169">Filters are more efficient than other parameters.</span></span> <span data-ttu-id="7e0ce-170">De provider past filter toe wanneer de cmdlet de objecten ophaalt in plaats van dat Power shell de objecten heeft gefilterd nadat ze zijn opgehaald.</span><span class="sxs-lookup"><span data-stu-id="7e0ce-170">The provider applies filter when the cmdlet gets the objects rather than having PowerShell filter the objects after they're retrieved.</span></span> <span data-ttu-id="7e0ce-171">De filter teken reeks wordt door gegeven aan de .NET API om bestanden te inventariseren.</span><span class="sxs-lookup"><span data-stu-id="7e0ce-171">The filter string is passed to the .NET API to enumerate files.</span></span> <span data-ttu-id="7e0ce-172">De API ondersteunt alleen `*` en `?` joker tekens.</span><span class="sxs-lookup"><span data-stu-id="7e0ce-172">The API only supports `*` and `?` wildcards.</span></span>

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

### <span data-ttu-id="7e0ce-173">-Force</span><span class="sxs-lookup"><span data-stu-id="7e0ce-173">-Force</span></span>

<span data-ttu-id="7e0ce-174">Geeft aan dat met deze cmdlet items worden opgehaald die niet kunnen worden geopend, zoals verborgen items.</span><span class="sxs-lookup"><span data-stu-id="7e0ce-174">Indicates that this cmdlet gets items that can't otherwise be accessed, such as hidden items.</span></span>
<span data-ttu-id="7e0ce-175">De implementatie varieert van provider tot provider.</span><span class="sxs-lookup"><span data-stu-id="7e0ce-175">Implementation varies from provider to provider.</span></span> <span data-ttu-id="7e0ce-176">Zie [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="7e0ce-176">For more information, see [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md).</span></span> <span data-ttu-id="7e0ce-177">Zelfs met behulp van de para meter **forceren** , kunnen de cmdlet geen beveiligings beperkingen opheffen.</span><span class="sxs-lookup"><span data-stu-id="7e0ce-177">Even using the **Force** parameter, the cmdlet can't override security restrictions.</span></span>

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

### <span data-ttu-id="7e0ce-178">-Include</span><span class="sxs-lookup"><span data-stu-id="7e0ce-178">-Include</span></span>

<span data-ttu-id="7e0ce-179">Hiermee wordt een teken reeks matrix opgegeven, een item of items die met deze cmdlet in de bewerking zijn opgenomen.</span><span class="sxs-lookup"><span data-stu-id="7e0ce-179">Specifies, as a string array, an item or items that this cmdlet includes in the operation.</span></span> <span data-ttu-id="7e0ce-180">De waarde van deze para meter komt in aanmerking voor de para meter **Path** .</span><span class="sxs-lookup"><span data-stu-id="7e0ce-180">The value of this parameter qualifies the **Path** parameter.</span></span> <span data-ttu-id="7e0ce-181">Voer een element of patroon van een pad in, zoals `*.txt` .</span><span class="sxs-lookup"><span data-stu-id="7e0ce-181">Enter a path element or pattern, such as `*.txt`.</span></span> <span data-ttu-id="7e0ce-182">Joker tekens zijn toegestaan.</span><span class="sxs-lookup"><span data-stu-id="7e0ce-182">Wildcard characters are permitted.</span></span> <span data-ttu-id="7e0ce-183">De para meter **include** is alleen effectief wanneer de inhoud van een item wordt opgenomen, zoals `C:\Windows\*` , waarbij het Joker teken de inhoud van de `C:\Windows` map bevat.</span><span class="sxs-lookup"><span data-stu-id="7e0ce-183">The **Include** parameter is effective only when the command includes the contents of an item, such as `C:\Windows\*`, where the wildcard character specifies the contents of the `C:\Windows` directory.</span></span>

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

### <span data-ttu-id="7e0ce-184">-LiteralPath</span><span class="sxs-lookup"><span data-stu-id="7e0ce-184">-LiteralPath</span></span>

<span data-ttu-id="7e0ce-185">Hiermee geeft u een pad naar een of meer locaties.</span><span class="sxs-lookup"><span data-stu-id="7e0ce-185">Specifies a path to one or more locations.</span></span> <span data-ttu-id="7e0ce-186">De waarde van **LiteralPath** wordt precies zo gebruikt als deze wordt getypt.</span><span class="sxs-lookup"><span data-stu-id="7e0ce-186">The value of **LiteralPath** is used exactly as it's typed.</span></span> <span data-ttu-id="7e0ce-187">Geen tekens worden geïnterpreteerd als joker tekens.</span><span class="sxs-lookup"><span data-stu-id="7e0ce-187">No characters are interpreted as wildcards.</span></span> <span data-ttu-id="7e0ce-188">Als het pad escape tekens bevat, plaatst u het tussen enkele aanhalings tekens.</span><span class="sxs-lookup"><span data-stu-id="7e0ce-188">If the path includes escape characters, enclose it in single quotation marks.</span></span> <span data-ttu-id="7e0ce-189">Enkele aanhalings tekens geven aan dat Power shell geen karakters interpreteert als escape reeksen.</span><span class="sxs-lookup"><span data-stu-id="7e0ce-189">Single quotation marks tell PowerShell not to interpret any characters as escape sequences.</span></span>

<span data-ttu-id="7e0ce-190">Zie [about_Quoting_Rules](../Microsoft.Powershell.Core/About/about_Quoting_Rules.md)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="7e0ce-190">For more information, see [about_Quoting_Rules](../Microsoft.Powershell.Core/About/about_Quoting_Rules.md).</span></span>

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

### <span data-ttu-id="7e0ce-191">-Path</span><span class="sxs-lookup"><span data-stu-id="7e0ce-191">-Path</span></span>

<span data-ttu-id="7e0ce-192">Hiermee geeft u het pad naar een item.</span><span class="sxs-lookup"><span data-stu-id="7e0ce-192">Specifies the path to an item.</span></span> <span data-ttu-id="7e0ce-193">Met deze cmdlet wordt het item op de opgegeven locatie opgehaald.</span><span class="sxs-lookup"><span data-stu-id="7e0ce-193">This cmdlet gets the item at the specified location.</span></span> <span data-ttu-id="7e0ce-194">Joker tekens zijn toegestaan.</span><span class="sxs-lookup"><span data-stu-id="7e0ce-194">Wildcard characters are permitted.</span></span> <span data-ttu-id="7e0ce-195">Deze para meter is vereist, maar het **pad naar** de parameter naam is optioneel.</span><span class="sxs-lookup"><span data-stu-id="7e0ce-195">This parameter is required, but the parameter name **Path** is optional.</span></span>

<span data-ttu-id="7e0ce-196">Gebruik een punt ( `.` ) om de huidige locatie op te geven.</span><span class="sxs-lookup"><span data-stu-id="7e0ce-196">Use a dot (`.`) to specify the current location.</span></span> <span data-ttu-id="7e0ce-197">Gebruik het Joker teken ( `*` ) om alle items op de huidige locatie op te geven.</span><span class="sxs-lookup"><span data-stu-id="7e0ce-197">Use the wildcard character (`*`) to specify all the items in the current location.</span></span>

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

### <span data-ttu-id="7e0ce-198">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="7e0ce-198">CommonParameters</span></span>

<span data-ttu-id="7e0ce-199">Deze cmdlet biedt ondersteuning voor de algemene para meters: `-Debug` , `-ErrorAction` , `-ErrorVariable` , `-InformationAction` , `-InformationVariable` , `-OutVariable` , `-OutBuffer` , `-PipelineVariable` , `-Verbose` , `-WarningAction` en `-WarningVariable` .</span><span class="sxs-lookup"><span data-stu-id="7e0ce-199">This cmdlet supports the common parameters: `-Debug`, `-ErrorAction`, `-ErrorVariable`, `-InformationAction`, `-InformationVariable`, `-OutVariable`, `-OutBuffer`, `-PipelineVariable`, `-Verbose`, `-WarningAction`, and `-WarningVariable`.</span></span> <span data-ttu-id="7e0ce-200">Zie [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="7e0ce-200">For more information, see [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md).</span></span>

## <span data-ttu-id="7e0ce-201">INVOER</span><span class="sxs-lookup"><span data-stu-id="7e0ce-201">INPUTS</span></span>

### <span data-ttu-id="7e0ce-202">System. String</span><span class="sxs-lookup"><span data-stu-id="7e0ce-202">System.String</span></span>

<span data-ttu-id="7e0ce-203">U kunt een teken reeks met een pad naar deze cmdlet door sluizen.</span><span class="sxs-lookup"><span data-stu-id="7e0ce-203">You can pipe a string that contains a path to this cmdlet.</span></span>

## <span data-ttu-id="7e0ce-204">UITVOER</span><span class="sxs-lookup"><span data-stu-id="7e0ce-204">OUTPUTS</span></span>

### <span data-ttu-id="7e0ce-205">System. object</span><span class="sxs-lookup"><span data-stu-id="7e0ce-205">System.Object</span></span>

<span data-ttu-id="7e0ce-206">Deze cmdlet retourneert de objecten die worden opgehaald.</span><span class="sxs-lookup"><span data-stu-id="7e0ce-206">This cmdlet returns the objects that it gets.</span></span> <span data-ttu-id="7e0ce-207">Het type wordt bepaald door het type objecten in het pad.</span><span class="sxs-lookup"><span data-stu-id="7e0ce-207">The type is determined by the type of objects in the path.</span></span>

## <span data-ttu-id="7e0ce-208">OPMERKINGEN</span><span class="sxs-lookup"><span data-stu-id="7e0ce-208">NOTES</span></span>

<span data-ttu-id="7e0ce-209">Deze cmdlet heeft geen **recursieve** para meter, omdat alleen een item wordt opgehaald, niet de inhoud ervan.</span><span class="sxs-lookup"><span data-stu-id="7e0ce-209">This cmdlet does not have a **Recurse** parameter, because it gets only an item, not its contents.</span></span>
<span data-ttu-id="7e0ce-210">Als u de inhoud van een item recursief wilt ophalen, gebruikt u `Get-ChildItem` .</span><span class="sxs-lookup"><span data-stu-id="7e0ce-210">To get the contents of an item recursively, use `Get-ChildItem`.</span></span>

<span data-ttu-id="7e0ce-211">Als u door het REGI ster wilt navigeren, gebruikt u deze cmdlet voor het ophalen van register sleutels en de `Get-ItemProperty` om register waarden en-gegevens op te halen.</span><span class="sxs-lookup"><span data-stu-id="7e0ce-211">To navigate through the registry, use this cmdlet to get registry keys and the `Get-ItemProperty` to get registry values and data.</span></span> <span data-ttu-id="7e0ce-212">De register waarden worden beschouwd als eigenschappen van de register sleutel.</span><span class="sxs-lookup"><span data-stu-id="7e0ce-212">The registry values are considered to be properties of the registry key.</span></span>

<span data-ttu-id="7e0ce-213">Deze cmdlet is ontworpen om te werken met de gegevens die door elke provider worden weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="7e0ce-213">This cmdlet is designed to work with the data exposed by any provider.</span></span> <span data-ttu-id="7e0ce-214">Als u een lijst wilt weer geven van de providers die beschikbaar zijn in uw sessie, typt u `Get-PsProvider` .</span><span class="sxs-lookup"><span data-stu-id="7e0ce-214">To list the providers available in your session, type `Get-PsProvider`.</span></span> <span data-ttu-id="7e0ce-215">Zie [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="7e0ce-215">For more information, see [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md).</span></span>

## <span data-ttu-id="7e0ce-216">GERELATEERDE KOPPELINGEN</span><span class="sxs-lookup"><span data-stu-id="7e0ce-216">RELATED LINKS</span></span>

[<span data-ttu-id="7e0ce-217">Wissen-item</span><span class="sxs-lookup"><span data-stu-id="7e0ce-217">Clear-Item</span></span>](Clear-Item.md)

[<span data-ttu-id="7e0ce-218">Kopie-item</span><span class="sxs-lookup"><span data-stu-id="7e0ce-218">Copy-Item</span></span>](Copy-Item.md)

[<span data-ttu-id="7e0ce-219">Invoke-item</span><span class="sxs-lookup"><span data-stu-id="7e0ce-219">Invoke-Item</span></span>](Invoke-Item.md)

[<span data-ttu-id="7e0ce-220">Item verplaatsen</span><span class="sxs-lookup"><span data-stu-id="7e0ce-220">Move-Item</span></span>](Move-Item.md)

[<span data-ttu-id="7e0ce-221">Nieuw-item</span><span class="sxs-lookup"><span data-stu-id="7e0ce-221">New-Item</span></span>](New-Item.md)

[<span data-ttu-id="7e0ce-222">Verwijderen-item</span><span class="sxs-lookup"><span data-stu-id="7e0ce-222">Remove-Item</span></span>](Remove-Item.md)

[<span data-ttu-id="7e0ce-223">Naam wijzigen-item</span><span class="sxs-lookup"><span data-stu-id="7e0ce-223">Rename-Item</span></span>](Rename-Item.md)

[<span data-ttu-id="7e0ce-224">Set-item</span><span class="sxs-lookup"><span data-stu-id="7e0ce-224">Set-Item</span></span>](Set-Item.md)

[<span data-ttu-id="7e0ce-225">Get-Child item</span><span class="sxs-lookup"><span data-stu-id="7e0ce-225">Get-ChildItem</span></span>](Get-ChildItem.md)

[<span data-ttu-id="7e0ce-226">Get-item Property</span><span class="sxs-lookup"><span data-stu-id="7e0ce-226">Get-ItemProperty</span></span>](Get-ItemProperty.md)

[<span data-ttu-id="7e0ce-227">Get-PSProvider</span><span class="sxs-lookup"><span data-stu-id="7e0ce-227">Get-PSProvider</span></span>](Get-PSProvider.md)

[<span data-ttu-id="7e0ce-228">about_Providers</span><span class="sxs-lookup"><span data-stu-id="7e0ce-228">about_Providers</span></span>](../Microsoft.PowerShell.Core/About/about_Providers.md)
