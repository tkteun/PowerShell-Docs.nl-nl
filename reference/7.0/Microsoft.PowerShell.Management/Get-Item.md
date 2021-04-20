---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 04/19/2021
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/get-item?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-Item
ms.openlocfilehash: 33a46a9db479efbb920343508bbed74c976f10ad
ms.sourcegitcommit: 2ad76cd528338f8c2cc10a84c5c56c0e25b93436
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 04/19/2021
ms.locfileid: "107729933"
---
# <span data-ttu-id="39890-102">Get-Item</span><span class="sxs-lookup"><span data-stu-id="39890-102">Get-Item</span></span>

## <span data-ttu-id="39890-103">SAMENVATTING</span><span class="sxs-lookup"><span data-stu-id="39890-103">SYNOPSIS</span></span>
<span data-ttu-id="39890-104">Hiermee haalt u het item op de opgegeven locatie.</span><span class="sxs-lookup"><span data-stu-id="39890-104">Gets the item at the specified location.</span></span>

## <span data-ttu-id="39890-105">SYNTAXIS</span><span class="sxs-lookup"><span data-stu-id="39890-105">SYNTAX</span></span>

### <span data-ttu-id="39890-106">Pad (standaard)</span><span class="sxs-lookup"><span data-stu-id="39890-106">Path (Default)</span></span>

```
Get-Item [-Path] <String[]> [-Filter <String>] [-Include <String[]>] [-Exclude <String[]>] [-Force]
 [-Credential <PSCredential>] [-Stream <String[]>] [<CommonParameters>]
```

### <span data-ttu-id="39890-107">LiteralPath</span><span class="sxs-lookup"><span data-stu-id="39890-107">LiteralPath</span></span>

```
Get-Item -LiteralPath <String[]> [-Filter <String>] [-Include <String[]>] [-Exclude <String[]>]
 [-Force] [-Credential <PSCredential>] [-Stream <String[]>] [<CommonParameters>]
```

## <span data-ttu-id="39890-108">BESCHRIJVING</span><span class="sxs-lookup"><span data-stu-id="39890-108">DESCRIPTION</span></span>

<span data-ttu-id="39890-109">De `Get-Item` cmdlet haalt het item op de opgegeven locatie op.</span><span class="sxs-lookup"><span data-stu-id="39890-109">The `Get-Item` cmdlet gets the item at the specified location.</span></span> <span data-ttu-id="39890-110">De inhoud van het item wordt niet op de locatie opgevraagd, tenzij u een jokerteken ( ) gebruikt om alle inhoud van het `*` item aan te vragen.</span><span class="sxs-lookup"><span data-stu-id="39890-110">It doesn't get the contents of the item at the location unless you use a wildcard character (`*`) to request all the contents of the item.</span></span>

<span data-ttu-id="39890-111">Deze cmdlet wordt gebruikt door PowerShell-providers om door verschillende typen gegevensopslag te navigeren.</span><span class="sxs-lookup"><span data-stu-id="39890-111">This cmdlet is used by PowerShell providers to navigate through different types of data stores.</span></span>

## <span data-ttu-id="39890-112">VOORBEELDEN</span><span class="sxs-lookup"><span data-stu-id="39890-112">EXAMPLES</span></span>

### <span data-ttu-id="39890-113">Voorbeeld 1: De huidige map op te halen</span><span class="sxs-lookup"><span data-stu-id="39890-113">Example 1: Get the current directory</span></span>

<span data-ttu-id="39890-114">In dit voorbeeld wordt de huidige map.</span><span class="sxs-lookup"><span data-stu-id="39890-114">This example gets the current directory.</span></span> <span data-ttu-id="39890-115">De stip ('.') vertegenwoordigt het item op de huidige locatie (niet de inhoud ervan).</span><span class="sxs-lookup"><span data-stu-id="39890-115">The dot ('.') represents the item at the current location (not its contents).</span></span>

```powershell
Get-Item .
```

```output
Directory: C:\

Mode                LastWriteTime     Length Name
----                -------------     ------ ----
d----         7/26/2006  10:01 AM            ps-test
```

### <span data-ttu-id="39890-116">Voorbeeld 2: Alle items in de huidige map op te halen</span><span class="sxs-lookup"><span data-stu-id="39890-116">Example 2: Get all the items in the current directory</span></span>

<span data-ttu-id="39890-117">In dit voorbeeld worden alle items in de huidige map.</span><span class="sxs-lookup"><span data-stu-id="39890-117">This example gets all the items in the current directory.</span></span> <span data-ttu-id="39890-118">Het jokerteken ( `*` ) vertegenwoordigt alle inhoud van het huidige item.</span><span class="sxs-lookup"><span data-stu-id="39890-118">The wildcard character (`*`) represents all the contents of the current item.</span></span>

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

### <span data-ttu-id="39890-119">Voorbeeld 3: De huidige map van een station op te halen</span><span class="sxs-lookup"><span data-stu-id="39890-119">Example 3: Get the current directory of a drive</span></span>

<span data-ttu-id="39890-120">In dit voorbeeld wordt de huidige map van het `C:` station.</span><span class="sxs-lookup"><span data-stu-id="39890-120">This example gets the current directory of the `C:` drive.</span></span> <span data-ttu-id="39890-121">Het object dat wordt opgehaald, vertegenwoordigt alleen de map, niet de inhoud ervan.</span><span class="sxs-lookup"><span data-stu-id="39890-121">The object that is retrieved represents only the directory, not its contents.</span></span>

```powershell
Get-Item C:
```

### <span data-ttu-id="39890-122">Voorbeeld 4: items in het opgegeven station op te halen</span><span class="sxs-lookup"><span data-stu-id="39890-122">Example 4: Get items in the specified drive</span></span>

<span data-ttu-id="39890-123">In dit voorbeeld worden de items in het `C:` station.</span><span class="sxs-lookup"><span data-stu-id="39890-123">This example gets the items in the `C:` drive.</span></span> <span data-ttu-id="39890-124">Het jokerteken ( `*` ) vertegenwoordigt alle items in de container, niet alleen de container.</span><span class="sxs-lookup"><span data-stu-id="39890-124">The wildcard character (`*`) represents all the items in the container, not just the container.</span></span>

```powershell
Get-Item C:\*
```

<span data-ttu-id="39890-125">Gebruik in PowerShell één sterretje ( ) om inhoud op te halen `*` in plaats van de traditionele `*.*` .</span><span class="sxs-lookup"><span data-stu-id="39890-125">In PowerShell, use a single asterisk (`*`) to get contents, instead of the traditional `*.*`.</span></span> <span data-ttu-id="39890-126">De indeling wordt letterlijk geïnterpreteerd, dus zou geen map `*.*` of bestandsnaam ophalen zonder een punt.</span><span class="sxs-lookup"><span data-stu-id="39890-126">The format is interpreted literally, so `*.*` wouldn't retrieve directories or filenames without a dot.</span></span>

### <span data-ttu-id="39890-127">Voorbeeld 5: een eigenschap in de opgegeven map op te halen</span><span class="sxs-lookup"><span data-stu-id="39890-127">Example 5: Get a property in the specified directory</span></span>

<span data-ttu-id="39890-128">In dit voorbeeld wordt de **eigenschap LastAccessTime** van de `C:\Windows` map .</span><span class="sxs-lookup"><span data-stu-id="39890-128">This example gets the **LastAccessTime** property of the `C:\Windows` directory.</span></span> <span data-ttu-id="39890-129">**LastAccessTime** is slechts één eigenschap van bestandssysteemdirecties.</span><span class="sxs-lookup"><span data-stu-id="39890-129">**LastAccessTime** is just one property of file system directories.</span></span> <span data-ttu-id="39890-130">Als u alle eigenschappen van een map wilt zien, typt u `(Get-Item <directory-name>) | Get-Member` .</span><span class="sxs-lookup"><span data-stu-id="39890-130">To see all the properties of a directory, type `(Get-Item <directory-name>) | Get-Member`.</span></span>

```powershell
(Get-Item C:\Windows).LastAccessTime
```

### <span data-ttu-id="39890-131">Voorbeeld 6: De inhoud van een registersleutel weergeven</span><span class="sxs-lookup"><span data-stu-id="39890-131">Example 6: Show the contents of a registry key</span></span>

<span data-ttu-id="39890-132">In dit voorbeeld ziet u de inhoud van de **registersleutel Microsoft.PowerShell.**</span><span class="sxs-lookup"><span data-stu-id="39890-132">This example shows the contents of the **Microsoft.PowerShell** registry key.</span></span> <span data-ttu-id="39890-133">U kunt deze cmdlet gebruiken met de PowerShell Registry-provider om registersleutels en subsleutels op te halen, maar u moet de cmdlet gebruiken om de registerwaarden en -gegevens `Get-ItemProperty` op te halen.</span><span class="sxs-lookup"><span data-stu-id="39890-133">You can use this cmdlet with the PowerShell Registry provider to get registry keys and subkeys, but you must use the `Get-ItemProperty` cmdlet to get the registry values and data.</span></span>

```powershell
Get-Item HKLM:\Software\Microsoft\Powershell\1\Shellids\Microsoft.Powershell\
```

### <span data-ttu-id="39890-134">Voorbeeld 7: Items in een map met een uitsluiting op halen</span><span class="sxs-lookup"><span data-stu-id="39890-134">Example 7: Get items in a directory that have an exclusion</span></span>

<span data-ttu-id="39890-135">In dit voorbeeld worden items in de Windows-map met namen met een punt ( `.` ) , maar niet beginnen met `w*` . Dit voorbeeld werkt alleen wanneer het pad een jokerteken ( ) bevat om de inhoud van het `*` item op te geven.</span><span class="sxs-lookup"><span data-stu-id="39890-135">This example gets items in the Windows directory with names that include a dot (`.`), but don't begin with `w*`.This example works only when the path includes a wildcard character (`*`) to specify the contents of the item.</span></span>

```powershell
Get-Item C:\Windows\*.* -Exclude "w*"
```

### <span data-ttu-id="39890-136">Voorbeeld 8: Hardlink-informatie verkrijgen</span><span class="sxs-lookup"><span data-stu-id="39890-136">Example 8: Getting hardlink information</span></span>

<span data-ttu-id="39890-137">In PowerShell 6.2 is een alternatieve weergave toegevoegd om hardlink-informatie op te halen.</span><span class="sxs-lookup"><span data-stu-id="39890-137">In PowerShell 6.2, an alternate view was added to get hardlink information.</span></span> <span data-ttu-id="39890-138">Als u de hardlink-informatie wilt op halen, slinkt u de uitvoer door naar `Format-Table -View childrenWithHardlink`</span><span class="sxs-lookup"><span data-stu-id="39890-138">To get the hardlink information, pipe the output to `Format-Table -View childrenWithHardlink`</span></span>

```powershell
Get-Item -Path C:\PathWhichIsAHardLink | Format-Table -View childrenWithHardlink
```

### <span data-ttu-id="39890-139">Voorbeeld 9: Uitvoer voor experimentele functie PSUnixFileStat</span><span class="sxs-lookup"><span data-stu-id="39890-139">Example 9: Output for experimental feature PSUnixFileStat</span></span>

<span data-ttu-id="39890-140">In PowerShell 7 op Unix-systemen biedt de experimentele functie **PSUnixFileStat** Unix-achtige uitvoer:</span><span class="sxs-lookup"><span data-stu-id="39890-140">In PowerShell 7 on Unix systems, the experimental feature **PSUnixFileStat** provides Unix-like output:</span></span>

```powershell
PS> Get-Item /Users
```

```Output
    Directory: /

UnixMode    User  Group   LastWriteTime      Size  Name
--------    ----  -----   -------------      ----  ----
drwxr-xr-x  root  admin   12/20/2019 11:46   192   Users
```

<span data-ttu-id="39890-141">De nieuwe eigenschappen die nu deel uitmaken van de uitvoer zijn:</span><span class="sxs-lookup"><span data-stu-id="39890-141">The new properties that are now part of the output are:</span></span>

- <span data-ttu-id="39890-142">**UnixMode** is de bestandsmachtigingen zoals weergegeven op een Unix-systeem</span><span class="sxs-lookup"><span data-stu-id="39890-142">**UnixMode** is the file permissions as represented on a Unix system</span></span>
- <span data-ttu-id="39890-143">**Gebruiker** is de bestandseigenaar</span><span class="sxs-lookup"><span data-stu-id="39890-143">**User** is the file owner</span></span>
- <span data-ttu-id="39890-144">**Groep** is de groepseigenaar</span><span class="sxs-lookup"><span data-stu-id="39890-144">**Group** is the group owner</span></span>
- <span data-ttu-id="39890-145">**Grootte** is de grootte van het bestand of de map zoals weergegeven op een Unix-systeem</span><span class="sxs-lookup"><span data-stu-id="39890-145">**Size** is the size of the file or directory as represented on a Unix system</span></span>

## <span data-ttu-id="39890-146">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="39890-146">PARAMETERS</span></span>

### <span data-ttu-id="39890-147">-Stream</span><span class="sxs-lookup"><span data-stu-id="39890-147">-Stream</span></span>

> [!NOTE]
> <span data-ttu-id="39890-148">Deze parameter is alleen beschikbaar in Windows.</span><span class="sxs-lookup"><span data-stu-id="39890-148">This Parameter is only available on Windows.</span></span>

<span data-ttu-id="39890-149">Hiermee haalt u de opgegeven alternatieve NTFS-bestandsstroom uit het bestand.</span><span class="sxs-lookup"><span data-stu-id="39890-149">Gets the specified alternate NTFS file stream from the file.</span></span> <span data-ttu-id="39890-150">Voer de naam van de stream in.</span><span class="sxs-lookup"><span data-stu-id="39890-150">Enter the stream name.</span></span> <span data-ttu-id="39890-151">Jokertekens worden ondersteund.</span><span class="sxs-lookup"><span data-stu-id="39890-151">Wildcards are supported.</span></span> <span data-ttu-id="39890-152">Gebruik een sterretje () om alle streams op te `*` halen.</span><span class="sxs-lookup"><span data-stu-id="39890-152">To get all streams, use an asterisk (`*`).</span></span> <span data-ttu-id="39890-153">Deze parameter is niet geldig voor mappen.</span><span class="sxs-lookup"><span data-stu-id="39890-153">This parameter isn't valid on folders.</span></span>

<span data-ttu-id="39890-154">**Stream** is een dynamische parameter die de **filesystem-provider** toevoegt aan de `Get-Item` cmdlet.</span><span class="sxs-lookup"><span data-stu-id="39890-154">**Stream** is a dynamic parameter that the **FileSystem** provider adds to the `Get-Item` cmdlet.</span></span>
<span data-ttu-id="39890-155">Deze parameter werkt alleen in bestandssysteemstations.</span><span class="sxs-lookup"><span data-stu-id="39890-155">This parameter works only in file system drives.</span></span>

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

### <span data-ttu-id="39890-156">-Credential</span><span class="sxs-lookup"><span data-stu-id="39890-156">-Credential</span></span>

> [!NOTE]
> <span data-ttu-id="39890-157">Deze parameter wordt niet ondersteund door providers die zijn geïnstalleerd met PowerShell.</span><span class="sxs-lookup"><span data-stu-id="39890-157">This parameter isn't supported by any providers installed with PowerShell.</span></span>
> <span data-ttu-id="39890-158">Als u een andere gebruiker wilt imiteren of uw referenties wilt verhogen bij het uitvoeren van deze cmdlet, gebruikt [u Invoke-Command](../Microsoft.PowerShell.Core/Invoke-Command.md).</span><span class="sxs-lookup"><span data-stu-id="39890-158">To impersonate another user, or elevate your credentials when running this cmdlet, use [Invoke-Command](../Microsoft.PowerShell.Core/Invoke-Command.md).</span></span>

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

### <span data-ttu-id="39890-159">-Uitsluiten</span><span class="sxs-lookup"><span data-stu-id="39890-159">-Exclude</span></span>

<span data-ttu-id="39890-160">Hiermee geeft u als tekenreeksmatrix een item of items op die door deze cmdlet worden uitgesloten in de bewerking.</span><span class="sxs-lookup"><span data-stu-id="39890-160">Specifies, as a string array, an item or items that this cmdlet excludes in the operation.</span></span> <span data-ttu-id="39890-161">De waarde van deze parameter komt in aanmerking voor de **parameter Path.**</span><span class="sxs-lookup"><span data-stu-id="39890-161">The value of this parameter qualifies the **Path** parameter.</span></span> <span data-ttu-id="39890-162">Voer een padelement of -patroon in, zoals `*.txt` .</span><span class="sxs-lookup"><span data-stu-id="39890-162">Enter a path element or pattern, such as `*.txt`.</span></span> <span data-ttu-id="39890-163">Jokertekens zijn toegestaan.</span><span class="sxs-lookup"><span data-stu-id="39890-163">Wildcard characters are permitted.</span></span> <span data-ttu-id="39890-164">De **uitsluiten** parameter is alleen van kracht wanneer de opdracht bevat de inhoud van een item, zoals , waarbij het jokerteken geeft de `C:\Windows\*` inhoud van de `C:\Windows` map.</span><span class="sxs-lookup"><span data-stu-id="39890-164">The **Exclude** parameter is effective only when the command includes the contents of an item, such as `C:\Windows\*`, where the wildcard character specifies the contents of the `C:\Windows` directory.</span></span>

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

### <span data-ttu-id="39890-165">-Filter</span><span class="sxs-lookup"><span data-stu-id="39890-165">-Filter</span></span>

<span data-ttu-id="39890-166">Hiermee geeft u een filter op om de **parameter Path te kwalificeren.**</span><span class="sxs-lookup"><span data-stu-id="39890-166">Specifies a filter to qualify the **Path** parameter.</span></span> <span data-ttu-id="39890-167">De [FileSystem-provider](../Microsoft.PowerShell.Core/About/about_FileSystem_Provider.md) is de enige geïnstalleerde PowerShell-provider die ondersteuning biedt voor filters.</span><span class="sxs-lookup"><span data-stu-id="39890-167">The [FileSystem](../Microsoft.PowerShell.Core/About/about_FileSystem_Provider.md) provider is the only installed PowerShell provider that supports filters.</span></span> <span data-ttu-id="39890-168">Filters zijn efficiënter dan andere parameters.</span><span class="sxs-lookup"><span data-stu-id="39890-168">Filters are more efficient than other parameters.</span></span> <span data-ttu-id="39890-169">De provider past een filter toe wanneer de cmdlet de objecten op haalt in plaats van powershell de objecten te laten filteren nadat deze zijn opgehaald.</span><span class="sxs-lookup"><span data-stu-id="39890-169">The provider applies filter when the cmdlet gets the objects rather than having PowerShell filter the objects after they're retrieved.</span></span> <span data-ttu-id="39890-170">De filterreeks wordt doorgegeven aan de .NET API om bestanden op te semuleren.</span><span class="sxs-lookup"><span data-stu-id="39890-170">The filter string is passed to the .NET API to enumerate files.</span></span> <span data-ttu-id="39890-171">De API ondersteunt alleen `*` `?` jokertekens en .</span><span class="sxs-lookup"><span data-stu-id="39890-171">The API only supports `*` and `?` wildcards.</span></span>

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

### <span data-ttu-id="39890-172">-Force</span><span class="sxs-lookup"><span data-stu-id="39890-172">-Force</span></span>

<span data-ttu-id="39890-173">Geeft aan dat deze cmdlet items krijgt die anders niet toegankelijk zijn, zoals verborgen items.</span><span class="sxs-lookup"><span data-stu-id="39890-173">Indicates that this cmdlet gets items that can't otherwise be accessed, such as hidden items.</span></span>
<span data-ttu-id="39890-174">Implementatie varieert per provider.</span><span class="sxs-lookup"><span data-stu-id="39890-174">Implementation varies from provider to provider.</span></span> <span data-ttu-id="39890-175">Zie voor meer informatie [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md).</span><span class="sxs-lookup"><span data-stu-id="39890-175">For more information, see [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md).</span></span> <span data-ttu-id="39890-176">Zelfs met **de** parameter Force kan de cmdlet geen beveiligingsbeperkingen overschrijven.</span><span class="sxs-lookup"><span data-stu-id="39890-176">Even using the **Force** parameter, the cmdlet can't override security restrictions.</span></span>

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

### <span data-ttu-id="39890-177">-Include</span><span class="sxs-lookup"><span data-stu-id="39890-177">-Include</span></span>

<span data-ttu-id="39890-178">Hiermee geeft u als tekenreeksmatrix een item of items op die deze cmdlet in de bewerking bevat.</span><span class="sxs-lookup"><span data-stu-id="39890-178">Specifies, as a string array, an item or items that this cmdlet includes in the operation.</span></span> <span data-ttu-id="39890-179">De waarde van deze parameter komt in aanmerking voor de **parameter Path.**</span><span class="sxs-lookup"><span data-stu-id="39890-179">The value of this parameter qualifies the **Path** parameter.</span></span> <span data-ttu-id="39890-180">Voer een padelement of -patroon in, zoals `*.txt` .</span><span class="sxs-lookup"><span data-stu-id="39890-180">Enter a path element or pattern, such as `*.txt`.</span></span> <span data-ttu-id="39890-181">Jokertekens zijn toegestaan.</span><span class="sxs-lookup"><span data-stu-id="39890-181">Wildcard characters are permitted.</span></span> <span data-ttu-id="39890-182">De **parameter Include** is alleen van kracht wanneer de opdracht de inhoud van een item bevat, zoals , waarbij het jokerteken de inhoud van de map `C:\Windows\*` `C:\Windows` aangeeft.</span><span class="sxs-lookup"><span data-stu-id="39890-182">The **Include** parameter is effective only when the command includes the contents of an item, such as `C:\Windows\*`, where the wildcard character specifies the contents of the `C:\Windows` directory.</span></span>

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

### <span data-ttu-id="39890-183">-LiteralPath</span><span class="sxs-lookup"><span data-stu-id="39890-183">-LiteralPath</span></span>

<span data-ttu-id="39890-184">Hiermee geeft u een pad naar een of meer locaties.</span><span class="sxs-lookup"><span data-stu-id="39890-184">Specifies a path to one or more locations.</span></span> <span data-ttu-id="39890-185">De waarde **van LiteralPath** wordt precies gebruikt zoals deze is getypt.</span><span class="sxs-lookup"><span data-stu-id="39890-185">The value of **LiteralPath** is used exactly as it's typed.</span></span> <span data-ttu-id="39890-186">Er worden geen tekens geïnterpreteerd als jokertekens.</span><span class="sxs-lookup"><span data-stu-id="39890-186">No characters are interpreted as wildcards.</span></span> <span data-ttu-id="39890-187">Als het pad escape-tekens bevat, sluit u het tussen enkele aanhalingstekens.</span><span class="sxs-lookup"><span data-stu-id="39890-187">If the path includes escape characters, enclose it in single quotation marks.</span></span> <span data-ttu-id="39890-188">Enkele aanhalingstekens geven aan dat PowerShell geen tekens als escapereeksen mag interpreteren.</span><span class="sxs-lookup"><span data-stu-id="39890-188">Single quotation marks tell PowerShell not to interpret any characters as escape sequences.</span></span>

<span data-ttu-id="39890-189">Zie voor meer informatie [about_Quoting_Rules](../Microsoft.Powershell.Core/About/about_Quoting_Rules.md).</span><span class="sxs-lookup"><span data-stu-id="39890-189">For more information, see [about_Quoting_Rules](../Microsoft.Powershell.Core/About/about_Quoting_Rules.md).</span></span>

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

### <span data-ttu-id="39890-190">-Path</span><span class="sxs-lookup"><span data-stu-id="39890-190">-Path</span></span>

<span data-ttu-id="39890-191">Hiermee geeft u het pad naar een item.</span><span class="sxs-lookup"><span data-stu-id="39890-191">Specifies the path to an item.</span></span> <span data-ttu-id="39890-192">Met deze cmdlet wordt het item op de opgegeven locatie opgeslagen.</span><span class="sxs-lookup"><span data-stu-id="39890-192">This cmdlet gets the item at the specified location.</span></span> <span data-ttu-id="39890-193">Jokertekens zijn toegestaan.</span><span class="sxs-lookup"><span data-stu-id="39890-193">Wildcard characters are permitted.</span></span> <span data-ttu-id="39890-194">Deze parameter is vereist, maar de parameternaam **Pad** is optioneel.</span><span class="sxs-lookup"><span data-stu-id="39890-194">This parameter is required, but the parameter name **Path** is optional.</span></span>

<span data-ttu-id="39890-195">Gebruik een punt ( `.` ) om de huidige locatie op te geven.</span><span class="sxs-lookup"><span data-stu-id="39890-195">Use a dot (`.`) to specify the current location.</span></span> <span data-ttu-id="39890-196">Gebruik het jokerteken ( `*` ) om alle items op de huidige locatie op te geven.</span><span class="sxs-lookup"><span data-stu-id="39890-196">Use the wildcard character (`*`) to specify all the items in the current location.</span></span>

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

### <span data-ttu-id="39890-197">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="39890-197">CommonParameters</span></span>

<span data-ttu-id="39890-198">Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="39890-198">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="39890-199">Zie voor meer informatie [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="39890-199">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="39890-200">INVOER</span><span class="sxs-lookup"><span data-stu-id="39890-200">INPUTS</span></span>

### <span data-ttu-id="39890-201">System.String</span><span class="sxs-lookup"><span data-stu-id="39890-201">System.String</span></span>

<span data-ttu-id="39890-202">U kunt een tekenreeks met een pad naar deze cmdlet doorspijpen.</span><span class="sxs-lookup"><span data-stu-id="39890-202">You can pipe a string that contains a path to this cmdlet.</span></span>

## <span data-ttu-id="39890-203">UITVOER</span><span class="sxs-lookup"><span data-stu-id="39890-203">OUTPUTS</span></span>

### <span data-ttu-id="39890-204">System.Object</span><span class="sxs-lookup"><span data-stu-id="39890-204">System.Object</span></span>

<span data-ttu-id="39890-205">Deze cmdlet retourneert de objecten die deze krijgt.</span><span class="sxs-lookup"><span data-stu-id="39890-205">This cmdlet returns the objects that it gets.</span></span> <span data-ttu-id="39890-206">Het type wordt bepaald door het type objecten in het pad.</span><span class="sxs-lookup"><span data-stu-id="39890-206">The type is determined by the type of objects in the path.</span></span>

## <span data-ttu-id="39890-207">OPMERKINGEN</span><span class="sxs-lookup"><span data-stu-id="39890-207">NOTES</span></span>

<span data-ttu-id="39890-208">Deze cmdlet heeft geen **Recurse-parameter,** omdat alleen een item wordt ontvangen, niet de inhoud ervan.</span><span class="sxs-lookup"><span data-stu-id="39890-208">This cmdlet does not have a **Recurse** parameter, because it gets only an item, not its contents.</span></span>
<span data-ttu-id="39890-209">Gebruik om de inhoud van een item recursief op te `Get-ChildItem` halen.</span><span class="sxs-lookup"><span data-stu-id="39890-209">To get the contents of an item recursively, use `Get-ChildItem`.</span></span>

<span data-ttu-id="39890-210">Als u door het register wilt navigeren, gebruikt u deze cmdlet om registersleutels op te halen en de om `Get-ItemProperty` registerwaarden en -gegevens op te halen.</span><span class="sxs-lookup"><span data-stu-id="39890-210">To navigate through the registry, use this cmdlet to get registry keys and the `Get-ItemProperty` to get registry values and data.</span></span> <span data-ttu-id="39890-211">De registerwaarden worden beschouwd als eigenschappen van de registersleutel.</span><span class="sxs-lookup"><span data-stu-id="39890-211">The registry values are considered to be properties of the registry key.</span></span>

<span data-ttu-id="39890-212">Deze cmdlet is ontworpen om te werken met de gegevens die beschikbaar worden gemaakt door elke provider.</span><span class="sxs-lookup"><span data-stu-id="39890-212">This cmdlet is designed to work with the data exposed by any provider.</span></span> <span data-ttu-id="39890-213">Typ om de providers weer te geven die beschikbaar zijn in uw `Get-PsProvider` sessie.</span><span class="sxs-lookup"><span data-stu-id="39890-213">To list the providers available in your session, type `Get-PsProvider`.</span></span> <span data-ttu-id="39890-214">Zie voor meer informatie [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md).</span><span class="sxs-lookup"><span data-stu-id="39890-214">For more information, see [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md).</span></span>

## <span data-ttu-id="39890-215">GERELATEERDE KOPPELINGEN</span><span class="sxs-lookup"><span data-stu-id="39890-215">RELATED LINKS</span></span>

[<span data-ttu-id="39890-216">Clear-Item</span><span class="sxs-lookup"><span data-stu-id="39890-216">Clear-Item</span></span>](Clear-Item.md)

[<span data-ttu-id="39890-217">Copy-Item</span><span class="sxs-lookup"><span data-stu-id="39890-217">Copy-Item</span></span>](Copy-Item.md)

[<span data-ttu-id="39890-218">Invoke-Item</span><span class="sxs-lookup"><span data-stu-id="39890-218">Invoke-Item</span></span>](Invoke-Item.md)

[<span data-ttu-id="39890-219">Item verplaatsen</span><span class="sxs-lookup"><span data-stu-id="39890-219">Move-Item</span></span>](Move-Item.md)

[<span data-ttu-id="39890-220">Nieuw item</span><span class="sxs-lookup"><span data-stu-id="39890-220">New-Item</span></span>](New-Item.md)

[<span data-ttu-id="39890-221">Item verwijderen</span><span class="sxs-lookup"><span data-stu-id="39890-221">Remove-Item</span></span>](Remove-Item.md)

[<span data-ttu-id="39890-222">Rename-Item</span><span class="sxs-lookup"><span data-stu-id="39890-222">Rename-Item</span></span>](Rename-Item.md)

[<span data-ttu-id="39890-223">Set-Item</span><span class="sxs-lookup"><span data-stu-id="39890-223">Set-Item</span></span>](Set-Item.md)

[<span data-ttu-id="39890-224">Get-ChildItem</span><span class="sxs-lookup"><span data-stu-id="39890-224">Get-ChildItem</span></span>](Get-ChildItem.md)

[<span data-ttu-id="39890-225">Get-ItemProperty</span><span class="sxs-lookup"><span data-stu-id="39890-225">Get-ItemProperty</span></span>](Get-ItemProperty.md)

[<span data-ttu-id="39890-226">Get-PSProvider</span><span class="sxs-lookup"><span data-stu-id="39890-226">Get-PSProvider</span></span>](Get-PSProvider.md)

[<span data-ttu-id="39890-227">about_Providers</span><span class="sxs-lookup"><span data-stu-id="39890-227">about_Providers</span></span>](../Microsoft.PowerShell.Core/About/about_Providers.md)
