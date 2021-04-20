---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 04/19/2021
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/get-item?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-Item
ms.openlocfilehash: c422ac67fe991b25a62710cfa4be1538b50073d7
ms.sourcegitcommit: 2ad76cd528338f8c2cc10a84c5c56c0e25b93436
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 04/19/2021
ms.locfileid: "107730005"
---
# <span data-ttu-id="06cd0-102">Get-Item</span><span class="sxs-lookup"><span data-stu-id="06cd0-102">Get-Item</span></span>

## <span data-ttu-id="06cd0-103">SAMENVATTING</span><span class="sxs-lookup"><span data-stu-id="06cd0-103">SYNOPSIS</span></span>
<span data-ttu-id="06cd0-104">Hiermee haalt u het item op de opgegeven locatie.</span><span class="sxs-lookup"><span data-stu-id="06cd0-104">Gets the item at the specified location.</span></span>

## <span data-ttu-id="06cd0-105">SYNTAXIS</span><span class="sxs-lookup"><span data-stu-id="06cd0-105">SYNTAX</span></span>

### <span data-ttu-id="06cd0-106">Pad (standaard)</span><span class="sxs-lookup"><span data-stu-id="06cd0-106">Path (Default)</span></span>

```
Get-Item [-Path] <String[]> [-Filter <String>] [-Include <String[]>] [-Exclude <String[]>] [-Force]
 [-Credential <PSCredential>] [-Stream <String[]>] [<CommonParameters>]
```

### <span data-ttu-id="06cd0-107">LiteralPath</span><span class="sxs-lookup"><span data-stu-id="06cd0-107">LiteralPath</span></span>

```
Get-Item -LiteralPath <String[]> [-Filter <String>] [-Include <String[]>] [-Exclude <String[]>]
 [-Force] [-Credential <PSCredential>] [-Stream <String[]>] [<CommonParameters>]
```

## <span data-ttu-id="06cd0-108">BESCHRIJVING</span><span class="sxs-lookup"><span data-stu-id="06cd0-108">DESCRIPTION</span></span>

<span data-ttu-id="06cd0-109">De `Get-Item` cmdlet haalt het item op de opgegeven locatie op.</span><span class="sxs-lookup"><span data-stu-id="06cd0-109">The `Get-Item` cmdlet gets the item at the specified location.</span></span> <span data-ttu-id="06cd0-110">De inhoud van het item wordt niet op de locatie opgevraagd, tenzij u een jokerteken ( ) gebruikt om alle inhoud van het `*` item aan te vragen.</span><span class="sxs-lookup"><span data-stu-id="06cd0-110">It doesn't get the contents of the item at the location unless you use a wildcard character (`*`) to request all the contents of the item.</span></span>

<span data-ttu-id="06cd0-111">Deze cmdlet wordt gebruikt door PowerShell-providers om door verschillende typen gegevensopslag te navigeren.</span><span class="sxs-lookup"><span data-stu-id="06cd0-111">This cmdlet is used by PowerShell providers to navigate through different types of data stores.</span></span>

## <span data-ttu-id="06cd0-112">VOORBEELDEN</span><span class="sxs-lookup"><span data-stu-id="06cd0-112">EXAMPLES</span></span>

### <span data-ttu-id="06cd0-113">Voorbeeld 1: de huidige map op te halen</span><span class="sxs-lookup"><span data-stu-id="06cd0-113">Example 1: Get the current directory</span></span>

<span data-ttu-id="06cd0-114">In dit voorbeeld wordt de huidige map.</span><span class="sxs-lookup"><span data-stu-id="06cd0-114">This example gets the current directory.</span></span> <span data-ttu-id="06cd0-115">De punt ('.') vertegenwoordigt het item op de huidige locatie (niet de inhoud ervan).</span><span class="sxs-lookup"><span data-stu-id="06cd0-115">The dot ('.') represents the item at the current location (not its contents).</span></span>

```powershell
Get-Item .
```

```output
Directory: C:\

Mode                LastWriteTime     Length Name
----                -------------     ------ ----
d----         7/26/2006  10:01 AM            ps-test
```

### <span data-ttu-id="06cd0-116">Voorbeeld 2: alle items in de huidige map op te halen</span><span class="sxs-lookup"><span data-stu-id="06cd0-116">Example 2: Get all the items in the current directory</span></span>

<span data-ttu-id="06cd0-117">In dit voorbeeld worden alle items in de huidige map.</span><span class="sxs-lookup"><span data-stu-id="06cd0-117">This example gets all the items in the current directory.</span></span> <span data-ttu-id="06cd0-118">Het jokerteken ( `*` ) vertegenwoordigt alle inhoud van het huidige item.</span><span class="sxs-lookup"><span data-stu-id="06cd0-118">The wildcard character (`*`) represents all the contents of the current item.</span></span>

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

### <span data-ttu-id="06cd0-119">Voorbeeld 3: De huidige map van een station op te halen</span><span class="sxs-lookup"><span data-stu-id="06cd0-119">Example 3: Get the current directory of a drive</span></span>

<span data-ttu-id="06cd0-120">In dit voorbeeld wordt de huidige map van het `C:` station.</span><span class="sxs-lookup"><span data-stu-id="06cd0-120">This example gets the current directory of the `C:` drive.</span></span> <span data-ttu-id="06cd0-121">Het object dat wordt opgehaald vertegenwoordigt alleen de map, niet de inhoud ervan.</span><span class="sxs-lookup"><span data-stu-id="06cd0-121">The object that is retrieved represents only the directory, not its contents.</span></span>

```powershell
Get-Item C:
```

### <span data-ttu-id="06cd0-122">Voorbeeld 4: Items in het opgegeven station op halen</span><span class="sxs-lookup"><span data-stu-id="06cd0-122">Example 4: Get items in the specified drive</span></span>

<span data-ttu-id="06cd0-123">In dit voorbeeld worden de items in het `C:` station.</span><span class="sxs-lookup"><span data-stu-id="06cd0-123">This example gets the items in the `C:` drive.</span></span> <span data-ttu-id="06cd0-124">Het jokerteken ( `*` ) vertegenwoordigt alle items in de container, niet alleen de container.</span><span class="sxs-lookup"><span data-stu-id="06cd0-124">The wildcard character (`*`) represents all the items in the container, not just the container.</span></span>

```powershell
Get-Item C:\*
```

<span data-ttu-id="06cd0-125">Gebruik in PowerShell één sterretje () om inhoud op te halen `*` in plaats van de traditionele `*.*` .</span><span class="sxs-lookup"><span data-stu-id="06cd0-125">In PowerShell, use a single asterisk (`*`) to get contents, instead of the traditional `*.*`.</span></span> <span data-ttu-id="06cd0-126">De indeling wordt letterlijk geïnterpreteerd, zodat er geen map of bestandsnaam zonder `*.*` een punt wordt opgehaald.</span><span class="sxs-lookup"><span data-stu-id="06cd0-126">The format is interpreted literally, so `*.*` wouldn't retrieve directories or filenames without a dot.</span></span>

### <span data-ttu-id="06cd0-127">Voorbeeld 5: Een eigenschap in de opgegeven map op te halen</span><span class="sxs-lookup"><span data-stu-id="06cd0-127">Example 5: Get a property in the specified directory</span></span>

<span data-ttu-id="06cd0-128">In dit voorbeeld wordt de **eigenschap LastAccessTime** van de `C:\Windows` map .</span><span class="sxs-lookup"><span data-stu-id="06cd0-128">This example gets the **LastAccessTime** property of the `C:\Windows` directory.</span></span> <span data-ttu-id="06cd0-129">**LastAccessTime** is slechts één eigenschap van bestandssysteemdirecties.</span><span class="sxs-lookup"><span data-stu-id="06cd0-129">**LastAccessTime** is just one property of file system directories.</span></span> <span data-ttu-id="06cd0-130">Als u alle eigenschappen van een map wilt zien, typt u `(Get-Item <directory-name>) | Get-Member` .</span><span class="sxs-lookup"><span data-stu-id="06cd0-130">To see all the properties of a directory, type `(Get-Item <directory-name>) | Get-Member`.</span></span>

```powershell
(Get-Item C:\Windows).LastAccessTime
```

### <span data-ttu-id="06cd0-131">Voorbeeld 6: De inhoud van een registersleutel weergeven</span><span class="sxs-lookup"><span data-stu-id="06cd0-131">Example 6: Show the contents of a registry key</span></span>

<span data-ttu-id="06cd0-132">In dit voorbeeld ziet u de inhoud van de **Microsoft.PowerShell-registersleutel.**</span><span class="sxs-lookup"><span data-stu-id="06cd0-132">This example shows the contents of the **Microsoft.PowerShell** registry key.</span></span> <span data-ttu-id="06cd0-133">U kunt deze cmdlet gebruiken met de PowerShell-registerprovider om registersleutels en subsleutels op te halen, maar u moet de cmdlet gebruiken om de registerwaarden en -gegevens `Get-ItemProperty` op te halen.</span><span class="sxs-lookup"><span data-stu-id="06cd0-133">You can use this cmdlet with the PowerShell Registry provider to get registry keys and subkeys, but you must use the `Get-ItemProperty` cmdlet to get the registry values and data.</span></span>

```powershell
Get-Item HKLM:\Software\Microsoft\Powershell\1\Shellids\Microsoft.Powershell\
```

### <span data-ttu-id="06cd0-134">Voorbeeld 7: Items in een directory met een uitsluiting op halen</span><span class="sxs-lookup"><span data-stu-id="06cd0-134">Example 7: Get items in a directory that have an exclusion</span></span>

<span data-ttu-id="06cd0-135">In dit voorbeeld worden items in de Windows-map met namen van een punt ( ) , maar `.` niet met . `w*` Dit voorbeeld werkt alleen als het pad een jokerteken ( ) bevat om de inhoud van het `*` item op te geven.</span><span class="sxs-lookup"><span data-stu-id="06cd0-135">This example gets items in the Windows directory with names that include a dot (`.`), but don't begin with `w*`.This example works only when the path includes a wildcard character (`*`) to specify the contents of the item.</span></span>

```powershell
Get-Item C:\Windows\*.* -Exclude "w*"
```

### <span data-ttu-id="06cd0-136">Voorbeeld 8: Hardlink-informatie verkrijgen</span><span class="sxs-lookup"><span data-stu-id="06cd0-136">Example 8: Getting hardlink information</span></span>

<span data-ttu-id="06cd0-137">In PowerShell 6.2 is een alternatieve weergave toegevoegd om hardlinkgegevens op te halen.</span><span class="sxs-lookup"><span data-stu-id="06cd0-137">In PowerShell 6.2, an alternate view was added to get hardlink information.</span></span> <span data-ttu-id="06cd0-138">Als u de hardlink-informatie wilt op halen, slinkt u de uitvoer door naar `Format-Table -View childrenWithHardlink`</span><span class="sxs-lookup"><span data-stu-id="06cd0-138">To get the hardlink information, pipe the output to `Format-Table -View childrenWithHardlink`</span></span>

```powershell
Get-Item -Path C:\PathWhichIsAHardLink | Format-Table -View childrenWithHardlink
```

### <span data-ttu-id="06cd0-139">Voorbeeld 9: Uitvoer voor niet-Windows-besturingssystemen</span><span class="sxs-lookup"><span data-stu-id="06cd0-139">Example 9: Output for Non-Windows Operating Systems</span></span>

<span data-ttu-id="06cd0-140">In PowerShell 7.1 op Unix-systemen biedt de `Get-Item` cmdlet Unix-achtige uitvoer:</span><span class="sxs-lookup"><span data-stu-id="06cd0-140">In PowerShell 7.1 on Unix systems, the `Get-Item` cmdlet provides Unix-like output:</span></span>

```powershell
PS> Get-Item /Users
```

```Output
    Directory: /

UnixMode    User  Group   LastWriteTime      Size  Name
--------    ----  -----   -------------      ----  ----
drwxr-xr-x  root  admin   12/20/2019 11:46   192   Users
```

<span data-ttu-id="06cd0-141">De nieuwe eigenschappen die nu deel uitmaken van de uitvoer zijn:</span><span class="sxs-lookup"><span data-stu-id="06cd0-141">The new properties that are now part of the output are:</span></span>

- <span data-ttu-id="06cd0-142">**UnixMode** is de bestandsmachtigingen zoals weergegeven in een Unix-systeem</span><span class="sxs-lookup"><span data-stu-id="06cd0-142">**UnixMode** is the file permissions as represented on a Unix system</span></span>
- <span data-ttu-id="06cd0-143">**Gebruiker** is de bestandseigenaar</span><span class="sxs-lookup"><span data-stu-id="06cd0-143">**User** is the file owner</span></span>
- <span data-ttu-id="06cd0-144">**Groep** is de groepseigenaar</span><span class="sxs-lookup"><span data-stu-id="06cd0-144">**Group** is the group owner</span></span>
- <span data-ttu-id="06cd0-145">**Grootte** is de grootte van het bestand of de map zoals weergegeven op een Unix-systeem</span><span class="sxs-lookup"><span data-stu-id="06cd0-145">**Size** is the size of the file or directory as represented on a Unix system</span></span>

> [!NOTE]
> <span data-ttu-id="06cd0-146">Deze functie is verplaatst van experimenteel naar standaard in PowerShell 7.1.</span><span class="sxs-lookup"><span data-stu-id="06cd0-146">This feature was moved from experimental to mainstream in PowerShell 7.1.</span></span>

## <span data-ttu-id="06cd0-147">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="06cd0-147">PARAMETERS</span></span>

### <span data-ttu-id="06cd0-148">-Stream</span><span class="sxs-lookup"><span data-stu-id="06cd0-148">-Stream</span></span>

> [!NOTE]
> <span data-ttu-id="06cd0-149">Deze parameter is alleen beschikbaar in Windows.</span><span class="sxs-lookup"><span data-stu-id="06cd0-149">This Parameter is only available on Windows.</span></span>

<span data-ttu-id="06cd0-150">Hiermee haalt u de opgegeven alternatieve NTFS-bestandsstroom van het bestand.</span><span class="sxs-lookup"><span data-stu-id="06cd0-150">Gets the specified alternate NTFS file stream from the file.</span></span> <span data-ttu-id="06cd0-151">Voer de naam van de stream in.</span><span class="sxs-lookup"><span data-stu-id="06cd0-151">Enter the stream name.</span></span> <span data-ttu-id="06cd0-152">Jokertekens worden ondersteund.</span><span class="sxs-lookup"><span data-stu-id="06cd0-152">Wildcards are supported.</span></span> <span data-ttu-id="06cd0-153">Als u alle streams wilt op halen, gebruikt u een sterretje ( `*` ).</span><span class="sxs-lookup"><span data-stu-id="06cd0-153">To get all streams, use an asterisk (`*`).</span></span> <span data-ttu-id="06cd0-154">Deze parameter is niet geldig voor mappen.</span><span class="sxs-lookup"><span data-stu-id="06cd0-154">This parameter isn't valid on folders.</span></span>

<span data-ttu-id="06cd0-155">**Stream** is een dynamische parameter die de **filesystem-provider** toevoegt aan de `Get-Item` cmdlet.</span><span class="sxs-lookup"><span data-stu-id="06cd0-155">**Stream** is a dynamic parameter that the **FileSystem** provider adds to the `Get-Item` cmdlet.</span></span>
<span data-ttu-id="06cd0-156">Deze parameter werkt alleen in bestandssysteemstations.</span><span class="sxs-lookup"><span data-stu-id="06cd0-156">This parameter works only in file system drives.</span></span>

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

### <span data-ttu-id="06cd0-157">-Credential</span><span class="sxs-lookup"><span data-stu-id="06cd0-157">-Credential</span></span>

> [!NOTE]
> <span data-ttu-id="06cd0-158">Deze parameter wordt niet ondersteund door providers die zijn geïnstalleerd met PowerShell.</span><span class="sxs-lookup"><span data-stu-id="06cd0-158">This parameter isn't supported by any providers installed with PowerShell.</span></span>
> <span data-ttu-id="06cd0-159">Als u een andere gebruiker wilt imiteren of uw referenties wilt verhogen bij het uitvoeren van deze cmdlet, gebruikt [u Invoke-Command](../Microsoft.PowerShell.Core/Invoke-Command.md).</span><span class="sxs-lookup"><span data-stu-id="06cd0-159">To impersonate another user, or elevate your credentials when running this cmdlet, use [Invoke-Command](../Microsoft.PowerShell.Core/Invoke-Command.md).</span></span>

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

### <span data-ttu-id="06cd0-160">-Uitsluiten</span><span class="sxs-lookup"><span data-stu-id="06cd0-160">-Exclude</span></span>

<span data-ttu-id="06cd0-161">Hiermee geeft u als tekenreeksmatrix een item of items op die deze cmdlet uitsluit in de bewerking.</span><span class="sxs-lookup"><span data-stu-id="06cd0-161">Specifies, as a string array, an item or items that this cmdlet excludes in the operation.</span></span> <span data-ttu-id="06cd0-162">De waarde van deze parameter komt in aanmerking voor de **parameter Path.**</span><span class="sxs-lookup"><span data-stu-id="06cd0-162">The value of this parameter qualifies the **Path** parameter.</span></span> <span data-ttu-id="06cd0-163">Voer een padelement of -patroon in, zoals `*.txt` .</span><span class="sxs-lookup"><span data-stu-id="06cd0-163">Enter a path element or pattern, such as `*.txt`.</span></span> <span data-ttu-id="06cd0-164">Jokertekens zijn toegestaan.</span><span class="sxs-lookup"><span data-stu-id="06cd0-164">Wildcard characters are permitted.</span></span> <span data-ttu-id="06cd0-165">De **uitsluiten** parameter is alleen van kracht wanneer de opdracht bevat de inhoud van een item, zoals , waarbij het jokerteken geeft de inhoud `C:\Windows\*` van de `C:\Windows` map.</span><span class="sxs-lookup"><span data-stu-id="06cd0-165">The **Exclude** parameter is effective only when the command includes the contents of an item, such as `C:\Windows\*`, where the wildcard character specifies the contents of the `C:\Windows` directory.</span></span>

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

### <span data-ttu-id="06cd0-166">-Filter</span><span class="sxs-lookup"><span data-stu-id="06cd0-166">-Filter</span></span>

<span data-ttu-id="06cd0-167">Hiermee geeft u een filter op om de **padparameter te kwalificeren.**</span><span class="sxs-lookup"><span data-stu-id="06cd0-167">Specifies a filter to qualify the **Path** parameter.</span></span> <span data-ttu-id="06cd0-168">De [FileSystem-provider](../Microsoft.PowerShell.Core/About/about_FileSystem_Provider.md) is de enige geïnstalleerde PowerShell-provider die filters ondersteunt.</span><span class="sxs-lookup"><span data-stu-id="06cd0-168">The [FileSystem](../Microsoft.PowerShell.Core/About/about_FileSystem_Provider.md) provider is the only installed PowerShell provider that supports filters.</span></span> <span data-ttu-id="06cd0-169">Filters zijn efficiënter dan andere parameters.</span><span class="sxs-lookup"><span data-stu-id="06cd0-169">Filters are more efficient than other parameters.</span></span> <span data-ttu-id="06cd0-170">De provider past een filter toe wanneer de cmdlet de objecten op haalt, in plaats van dat PowerShell de objecten filtert nadat ze zijn opgehaald.</span><span class="sxs-lookup"><span data-stu-id="06cd0-170">The provider applies filter when the cmdlet gets the objects rather than having PowerShell filter the objects after they're retrieved.</span></span> <span data-ttu-id="06cd0-171">De filterreeks wordt doorgegeven aan de .NET API om bestanden op te semuleren.</span><span class="sxs-lookup"><span data-stu-id="06cd0-171">The filter string is passed to the .NET API to enumerate files.</span></span> <span data-ttu-id="06cd0-172">De API ondersteunt alleen `*` `?` jokertekens en .</span><span class="sxs-lookup"><span data-stu-id="06cd0-172">The API only supports `*` and `?` wildcards.</span></span>

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

### <span data-ttu-id="06cd0-173">-Force</span><span class="sxs-lookup"><span data-stu-id="06cd0-173">-Force</span></span>

<span data-ttu-id="06cd0-174">Geeft aan dat met deze cmdlet items worden opgeslagen die anders niet toegankelijk zijn, zoals verborgen items.</span><span class="sxs-lookup"><span data-stu-id="06cd0-174">Indicates that this cmdlet gets items that can't otherwise be accessed, such as hidden items.</span></span>
<span data-ttu-id="06cd0-175">Implementatie varieert per provider.</span><span class="sxs-lookup"><span data-stu-id="06cd0-175">Implementation varies from provider to provider.</span></span> <span data-ttu-id="06cd0-176">Zie voor meer informatie [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md).</span><span class="sxs-lookup"><span data-stu-id="06cd0-176">For more information, see [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md).</span></span> <span data-ttu-id="06cd0-177">Zelfs met **de** parameter Force kan de cmdlet geen beveiligingsbeperkingen overschrijven.</span><span class="sxs-lookup"><span data-stu-id="06cd0-177">Even using the **Force** parameter, the cmdlet can't override security restrictions.</span></span>

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

### <span data-ttu-id="06cd0-178">-Include</span><span class="sxs-lookup"><span data-stu-id="06cd0-178">-Include</span></span>

<span data-ttu-id="06cd0-179">Hiermee geeft u als tekenreeksmatrix een item of items op die deze cmdlet in de bewerking op bevat.</span><span class="sxs-lookup"><span data-stu-id="06cd0-179">Specifies, as a string array, an item or items that this cmdlet includes in the operation.</span></span> <span data-ttu-id="06cd0-180">De waarde van deze parameter komt in aanmerking voor de **parameter Path.**</span><span class="sxs-lookup"><span data-stu-id="06cd0-180">The value of this parameter qualifies the **Path** parameter.</span></span> <span data-ttu-id="06cd0-181">Voer een padelement of -patroon in, zoals `*.txt` .</span><span class="sxs-lookup"><span data-stu-id="06cd0-181">Enter a path element or pattern, such as `*.txt`.</span></span> <span data-ttu-id="06cd0-182">Jokertekens zijn toegestaan.</span><span class="sxs-lookup"><span data-stu-id="06cd0-182">Wildcard characters are permitted.</span></span> <span data-ttu-id="06cd0-183">De **parameter Include** is alleen van kracht wanneer de opdracht de inhoud van een item bevat, zoals , waarbij het jokerteken de inhoud van de map `C:\Windows\*` `C:\Windows` specificeert.</span><span class="sxs-lookup"><span data-stu-id="06cd0-183">The **Include** parameter is effective only when the command includes the contents of an item, such as `C:\Windows\*`, where the wildcard character specifies the contents of the `C:\Windows` directory.</span></span>

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

### <span data-ttu-id="06cd0-184">-LiteralPath</span><span class="sxs-lookup"><span data-stu-id="06cd0-184">-LiteralPath</span></span>

<span data-ttu-id="06cd0-185">Hiermee geeft u een pad naar een of meer locaties.</span><span class="sxs-lookup"><span data-stu-id="06cd0-185">Specifies a path to one or more locations.</span></span> <span data-ttu-id="06cd0-186">De waarde van **LiteralPath** wordt exact gebruikt zoals deze wordt getypt.</span><span class="sxs-lookup"><span data-stu-id="06cd0-186">The value of **LiteralPath** is used exactly as it's typed.</span></span> <span data-ttu-id="06cd0-187">Er worden geen tekens geïnterpreteerd als jokertekens.</span><span class="sxs-lookup"><span data-stu-id="06cd0-187">No characters are interpreted as wildcards.</span></span> <span data-ttu-id="06cd0-188">Als het pad escape-tekens bevat, sluit u het tussen enkele aanhalingstekens.</span><span class="sxs-lookup"><span data-stu-id="06cd0-188">If the path includes escape characters, enclose it in single quotation marks.</span></span> <span data-ttu-id="06cd0-189">Enkele aanhalingstekens geven aan PowerShell door dat er geen tekens als escapereeksen moeten worden geïnterpreteerd.</span><span class="sxs-lookup"><span data-stu-id="06cd0-189">Single quotation marks tell PowerShell not to interpret any characters as escape sequences.</span></span>

<span data-ttu-id="06cd0-190">Zie voor meer informatie [about_Quoting_Rules](../Microsoft.Powershell.Core/About/about_Quoting_Rules.md).</span><span class="sxs-lookup"><span data-stu-id="06cd0-190">For more information, see [about_Quoting_Rules](../Microsoft.Powershell.Core/About/about_Quoting_Rules.md).</span></span>

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

### <span data-ttu-id="06cd0-191">-Path</span><span class="sxs-lookup"><span data-stu-id="06cd0-191">-Path</span></span>

<span data-ttu-id="06cd0-192">Hiermee geeft u het pad naar een item.</span><span class="sxs-lookup"><span data-stu-id="06cd0-192">Specifies the path to an item.</span></span> <span data-ttu-id="06cd0-193">Met deze cmdlet wordt het item op de opgegeven locatie opgeslagen.</span><span class="sxs-lookup"><span data-stu-id="06cd0-193">This cmdlet gets the item at the specified location.</span></span> <span data-ttu-id="06cd0-194">Jokertekens zijn toegestaan.</span><span class="sxs-lookup"><span data-stu-id="06cd0-194">Wildcard characters are permitted.</span></span> <span data-ttu-id="06cd0-195">Deze parameter is vereist, maar de parameternaam **Pad** is optioneel.</span><span class="sxs-lookup"><span data-stu-id="06cd0-195">This parameter is required, but the parameter name **Path** is optional.</span></span>

<span data-ttu-id="06cd0-196">Gebruik een punt ( `.` ) om de huidige locatie op te geven.</span><span class="sxs-lookup"><span data-stu-id="06cd0-196">Use a dot (`.`) to specify the current location.</span></span> <span data-ttu-id="06cd0-197">Gebruik het jokerteken ( `*` ) om alle items op de huidige locatie op te geven.</span><span class="sxs-lookup"><span data-stu-id="06cd0-197">Use the wildcard character (`*`) to specify all the items in the current location.</span></span>

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

### <span data-ttu-id="06cd0-198">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="06cd0-198">CommonParameters</span></span>

<span data-ttu-id="06cd0-199">Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="06cd0-199">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="06cd0-200">Zie voor meer informatie [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="06cd0-200">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="06cd0-201">INVOER</span><span class="sxs-lookup"><span data-stu-id="06cd0-201">INPUTS</span></span>

### <span data-ttu-id="06cd0-202">System.String</span><span class="sxs-lookup"><span data-stu-id="06cd0-202">System.String</span></span>

<span data-ttu-id="06cd0-203">U kunt een tekenreeks die een pad naar deze cmdlet bevat doorseen.</span><span class="sxs-lookup"><span data-stu-id="06cd0-203">You can pipe a string that contains a path to this cmdlet.</span></span>

## <span data-ttu-id="06cd0-204">UITVOER</span><span class="sxs-lookup"><span data-stu-id="06cd0-204">OUTPUTS</span></span>

### <span data-ttu-id="06cd0-205">System.Object</span><span class="sxs-lookup"><span data-stu-id="06cd0-205">System.Object</span></span>

<span data-ttu-id="06cd0-206">Deze cmdlet retourneert de objecten die deze krijgt.</span><span class="sxs-lookup"><span data-stu-id="06cd0-206">This cmdlet returns the objects that it gets.</span></span> <span data-ttu-id="06cd0-207">Het type wordt bepaald door het type objecten in het pad.</span><span class="sxs-lookup"><span data-stu-id="06cd0-207">The type is determined by the type of objects in the path.</span></span>

## <span data-ttu-id="06cd0-208">OPMERKINGEN</span><span class="sxs-lookup"><span data-stu-id="06cd0-208">NOTES</span></span>

<span data-ttu-id="06cd0-209">Deze cmdlet heeft geen **Recurse-parameter,** omdat deze alleen een item krijgt, niet de inhoud ervan.</span><span class="sxs-lookup"><span data-stu-id="06cd0-209">This cmdlet does not have a **Recurse** parameter, because it gets only an item, not its contents.</span></span>
<span data-ttu-id="06cd0-210">Gebruik om de inhoud van een item recursief op te `Get-ChildItem` halen.</span><span class="sxs-lookup"><span data-stu-id="06cd0-210">To get the contents of an item recursively, use `Get-ChildItem`.</span></span>

<span data-ttu-id="06cd0-211">Als u door het register wilt navigeren, gebruikt u deze cmdlet om registersleutels op te halen en de om `Get-ItemProperty` registerwaarden en -gegevens op te halen.</span><span class="sxs-lookup"><span data-stu-id="06cd0-211">To navigate through the registry, use this cmdlet to get registry keys and the `Get-ItemProperty` to get registry values and data.</span></span> <span data-ttu-id="06cd0-212">De registerwaarden worden beschouwd als eigenschappen van de registersleutel.</span><span class="sxs-lookup"><span data-stu-id="06cd0-212">The registry values are considered to be properties of the registry key.</span></span>

<span data-ttu-id="06cd0-213">Deze cmdlet is ontworpen om te werken met de gegevens die beschikbaar worden gemaakt door elke provider.</span><span class="sxs-lookup"><span data-stu-id="06cd0-213">This cmdlet is designed to work with the data exposed by any provider.</span></span> <span data-ttu-id="06cd0-214">Typ om de providers weer te geven die beschikbaar zijn in uw `Get-PsProvider` sessie.</span><span class="sxs-lookup"><span data-stu-id="06cd0-214">To list the providers available in your session, type `Get-PsProvider`.</span></span> <span data-ttu-id="06cd0-215">Zie voor meer informatie [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md).</span><span class="sxs-lookup"><span data-stu-id="06cd0-215">For more information, see [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md).</span></span>

## <span data-ttu-id="06cd0-216">GERELATEERDE KOPPELINGEN</span><span class="sxs-lookup"><span data-stu-id="06cd0-216">RELATED LINKS</span></span>

[<span data-ttu-id="06cd0-217">Clear-Item</span><span class="sxs-lookup"><span data-stu-id="06cd0-217">Clear-Item</span></span>](Clear-Item.md)

[<span data-ttu-id="06cd0-218">Kopieeritem</span><span class="sxs-lookup"><span data-stu-id="06cd0-218">Copy-Item</span></span>](Copy-Item.md)

[<span data-ttu-id="06cd0-219">Invoke-Item</span><span class="sxs-lookup"><span data-stu-id="06cd0-219">Invoke-Item</span></span>](Invoke-Item.md)

[<span data-ttu-id="06cd0-220">Item verplaatsen</span><span class="sxs-lookup"><span data-stu-id="06cd0-220">Move-Item</span></span>](Move-Item.md)

[<span data-ttu-id="06cd0-221">Nieuw item</span><span class="sxs-lookup"><span data-stu-id="06cd0-221">New-Item</span></span>](New-Item.md)

[<span data-ttu-id="06cd0-222">Item verwijderen</span><span class="sxs-lookup"><span data-stu-id="06cd0-222">Remove-Item</span></span>](Remove-Item.md)

[<span data-ttu-id="06cd0-223">Rename-Item</span><span class="sxs-lookup"><span data-stu-id="06cd0-223">Rename-Item</span></span>](Rename-Item.md)

[<span data-ttu-id="06cd0-224">Set-Item</span><span class="sxs-lookup"><span data-stu-id="06cd0-224">Set-Item</span></span>](Set-Item.md)

[<span data-ttu-id="06cd0-225">Get-ChildItem</span><span class="sxs-lookup"><span data-stu-id="06cd0-225">Get-ChildItem</span></span>](Get-ChildItem.md)

[<span data-ttu-id="06cd0-226">Get-ItemProperty</span><span class="sxs-lookup"><span data-stu-id="06cd0-226">Get-ItemProperty</span></span>](Get-ItemProperty.md)

[<span data-ttu-id="06cd0-227">Get-PSProvider</span><span class="sxs-lookup"><span data-stu-id="06cd0-227">Get-PSProvider</span></span>](Get-PSProvider.md)

[<span data-ttu-id="06cd0-228">about_Providers</span><span class="sxs-lookup"><span data-stu-id="06cd0-228">about_Providers</span></span>](../Microsoft.PowerShell.Core/About/about_Providers.md)

