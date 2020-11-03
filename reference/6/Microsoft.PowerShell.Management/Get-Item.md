---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 03/27/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/get-item?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-Item
ms.openlocfilehash: 8483fd374ee973256633e3711322561fc14b8ae2
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/07/2020
ms.locfileid: "93251023"
---
# <span data-ttu-id="f0eda-103">Get-Item</span><span class="sxs-lookup"><span data-stu-id="f0eda-103">Get-Item</span></span>

## <span data-ttu-id="f0eda-104">SAMENVATTING</span><span class="sxs-lookup"><span data-stu-id="f0eda-104">SYNOPSIS</span></span>
<span data-ttu-id="f0eda-105">Hiermee wordt het item op de opgegeven locatie opgehaald.</span><span class="sxs-lookup"><span data-stu-id="f0eda-105">Gets the item at the specified location.</span></span>

## <span data-ttu-id="f0eda-106">SYNTAXIS</span><span class="sxs-lookup"><span data-stu-id="f0eda-106">SYNTAX</span></span>

### <span data-ttu-id="f0eda-107">Pad (standaard)</span><span class="sxs-lookup"><span data-stu-id="f0eda-107">Path (Default)</span></span>

```
Get-Item [-Path] <String[]> [-Filter <String>] [-Include <String[]>] [-Exclude <String[]>] [-Force]
 [-Credential <PSCredential>] [-Stream <String[]>] [<CommonParameters>]
```

### <span data-ttu-id="f0eda-108">LiteralPath</span><span class="sxs-lookup"><span data-stu-id="f0eda-108">LiteralPath</span></span>

```
Get-Item -LiteralPath <String[]> [-Filter <String>] [-Include <String[]>] [-Exclude <String[]>]
 [-Force] [-Credential <PSCredential>] [-Stream <String[]>] [<CommonParameters>]
```

## <span data-ttu-id="f0eda-109">BESCHRIJVING</span><span class="sxs-lookup"><span data-stu-id="f0eda-109">DESCRIPTION</span></span>

<span data-ttu-id="f0eda-110">`Get-Item`Met de cmdlet wordt het item op de opgegeven locatie opgehaald.</span><span class="sxs-lookup"><span data-stu-id="f0eda-110">The `Get-Item` cmdlet gets the item at the specified location.</span></span> <span data-ttu-id="f0eda-111">De inhoud van het item op de locatie wordt niet opgehaald, tenzij u een Joker teken ( `*` ) gebruikt om alle inhoud van het item aan te vragen.</span><span class="sxs-lookup"><span data-stu-id="f0eda-111">It doesn't get the contents of the item at the location unless you use a wildcard character (`*`) to request all the contents of the item.</span></span>

<span data-ttu-id="f0eda-112">Deze cmdlet wordt gebruikt door Power shell-providers om door verschillende typen gegevens archieven te navigeren.</span><span class="sxs-lookup"><span data-stu-id="f0eda-112">This cmdlet is used by PowerShell providers to navigate through different types of data stores.</span></span>

## <span data-ttu-id="f0eda-113">VOORBEELDEN</span><span class="sxs-lookup"><span data-stu-id="f0eda-113">EXAMPLES</span></span>

### <span data-ttu-id="f0eda-114">Voor beeld 1: de huidige map ophalen</span><span class="sxs-lookup"><span data-stu-id="f0eda-114">Example 1: Get the current directory</span></span>

<span data-ttu-id="f0eda-115">In dit voor beeld wordt de huidige map opgehaald.</span><span class="sxs-lookup"><span data-stu-id="f0eda-115">This example gets the current directory.</span></span> <span data-ttu-id="f0eda-116">De punt ('. ') staat voor het item op de huidige locatie (niet de inhoud).</span><span class="sxs-lookup"><span data-stu-id="f0eda-116">The dot ('.') represents the item at the current location (not its contents).</span></span>

```powershell
Get-Item .
```

```output
Directory: C:\

Mode                LastWriteTime     Length Name
----                -------------     ------ ----
d----         7/26/2006  10:01 AM            ps-test
```

### <span data-ttu-id="f0eda-117">Voor beeld 2: alle items in de huidige map ophalen</span><span class="sxs-lookup"><span data-stu-id="f0eda-117">Example 2: Get all the items in the current directory</span></span>

<span data-ttu-id="f0eda-118">In dit voor beeld worden alle items in de huidige map opgehaald.</span><span class="sxs-lookup"><span data-stu-id="f0eda-118">This example gets all the items in the current directory.</span></span> <span data-ttu-id="f0eda-119">Het Joker teken ( `*` ) vertegenwoordigt alle inhoud van het huidige item.</span><span class="sxs-lookup"><span data-stu-id="f0eda-119">The wildcard character (`*`) represents all the contents of the current item.</span></span>

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

### <span data-ttu-id="f0eda-120">Voor beeld 3: de huidige map van een station ophalen</span><span class="sxs-lookup"><span data-stu-id="f0eda-120">Example 3: Get the current directory of a drive</span></span>

<span data-ttu-id="f0eda-121">In dit voor beeld wordt de huidige map van het `C:` station opgehaald.</span><span class="sxs-lookup"><span data-stu-id="f0eda-121">This example gets the current directory of the `C:` drive.</span></span> <span data-ttu-id="f0eda-122">Het opgehaalde object staat alleen voor de map en niet de inhoud ervan.</span><span class="sxs-lookup"><span data-stu-id="f0eda-122">The object that is retrieved represents only the directory, not its contents.</span></span>

```powershell
Get-Item C:\
```

### <span data-ttu-id="f0eda-123">Voor beeld 4: items in het opgegeven station ophalen</span><span class="sxs-lookup"><span data-stu-id="f0eda-123">Example 4: Get items in the specified drive</span></span>

<span data-ttu-id="f0eda-124">In dit voor beeld worden de items in het `C:` station opgehaald.</span><span class="sxs-lookup"><span data-stu-id="f0eda-124">This example gets the items in the `C:` drive.</span></span> <span data-ttu-id="f0eda-125">Het Joker teken ( `*` ) vertegenwoordigt alle items in de container, niet alleen de container.</span><span class="sxs-lookup"><span data-stu-id="f0eda-125">The wildcard character (`*`) represents all the items in the container, not just the container.</span></span>

```powershell
Get-Item C:\*
```

<span data-ttu-id="f0eda-126">Gebruik in Power shell één asterisk ( `*` ) om inhoud op te halen in plaats van de traditionele `*.*` .</span><span class="sxs-lookup"><span data-stu-id="f0eda-126">In PowerShell, use a single asterisk (`*`) to get contents, instead of the traditional `*.*`.</span></span> <span data-ttu-id="f0eda-127">De indeling wordt letterlijk geïnterpreteerd, waardoor `*.*` er geen mappen of bestands namen worden opgehaald zonder een punt.</span><span class="sxs-lookup"><span data-stu-id="f0eda-127">The format is interpreted literally, so `*.*` wouldn't retrieve directories or filenames without a dot.</span></span>

### <span data-ttu-id="f0eda-128">Voor beeld 5: een eigenschap ophalen in de opgegeven map</span><span class="sxs-lookup"><span data-stu-id="f0eda-128">Example 5: Get a property in the specified directory</span></span>

<span data-ttu-id="f0eda-129">In dit voor beeld wordt de eigenschap **LastAccessTime** van de `C:\Windows` Directory opgehaald.</span><span class="sxs-lookup"><span data-stu-id="f0eda-129">This example gets the **LastAccessTime** property of the `C:\Windows` directory.</span></span> <span data-ttu-id="f0eda-130">**LastAccessTime** is slechts één eigenschap van File System directory's.</span><span class="sxs-lookup"><span data-stu-id="f0eda-130">**LastAccessTime** is just one property of file system directories.</span></span> <span data-ttu-id="f0eda-131">Als u alle eigenschappen van een map wilt weer geven, typt u `(Get-Item <directory-name>) | Get-Member` .</span><span class="sxs-lookup"><span data-stu-id="f0eda-131">To see all the properties of a directory, type `(Get-Item <directory-name>) | Get-Member`.</span></span>

```powershell
(Get-Item C:\Windows).LastAccessTime
```

### <span data-ttu-id="f0eda-132">Voor beeld 6: de inhoud van een register sleutel weer geven</span><span class="sxs-lookup"><span data-stu-id="f0eda-132">Example 6: Show the contents of a registry key</span></span>

<span data-ttu-id="f0eda-133">In dit voor beeld wordt de inhoud van de register sleutel **micro soft. Power shell** weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="f0eda-133">This example shows the contents of the **Microsoft.PowerShell** registry key.</span></span> <span data-ttu-id="f0eda-134">U kunt deze cmdlet gebruiken met de Power shell-register provider om register sleutels en subsleutels op te halen, maar u moet de `Get-ItemProperty` cmdlet gebruiken om de register waarden en-gegevens op te halen.</span><span class="sxs-lookup"><span data-stu-id="f0eda-134">You can use this cmdlet with the PowerShell Registry provider to get registry keys and subkeys, but you must use the `Get-ItemProperty` cmdlet to get the registry values and data.</span></span>

```powershell
Get-Item HKLM:\Software\Microsoft\Powershell\1\Shellids\Microsoft.Powershell\
```

### <span data-ttu-id="f0eda-135">Voor beeld 7: items in een directory met een uitsluiting ophalen</span><span class="sxs-lookup"><span data-stu-id="f0eda-135">Example 7: Get items in a directory that have an exclusion</span></span>

<span data-ttu-id="f0eda-136">In dit voor beeld worden items in de Windows-map met namen die een punt ( `.` ) bevatten, maar niet beginnen met `w*` . Dit voor beeld werkt alleen wanneer het pad een Joker teken ( `*` ) bevat om de inhoud van het item op te geven.</span><span class="sxs-lookup"><span data-stu-id="f0eda-136">This example gets items in the Windows directory with names that include a dot (`.`), but don't begin with `w*`.This example works only when the path includes a wildcard character (`*`) to specify the contents of the item.</span></span>

```powershell
Get-Item C:\Windows\*.* -Exclude "w*"
```

### <span data-ttu-id="f0eda-137">Voor beeld 8: koppelings gegevens ophalen</span><span class="sxs-lookup"><span data-stu-id="f0eda-137">Example 8: Getting hardlink information</span></span>

<span data-ttu-id="f0eda-138">In Power shell 6,2 is een alternatieve weer gave toegevoegd om koppelings gegevens op te halen.</span><span class="sxs-lookup"><span data-stu-id="f0eda-138">In PowerShell 6.2, an alternate view was added to get hardlink information.</span></span> <span data-ttu-id="f0eda-139">Als u de vaste gegevens wilt ophalen, pipet u de uitvoer naar `Format-Table -View childrenWithHardlink`</span><span class="sxs-lookup"><span data-stu-id="f0eda-139">To get the hardlink information, pipe the output to `Format-Table -View childrenWithHardlink`</span></span>

```powershell
Get-Item -Path C:\PathWhichIsAHardLink | Format-Table -View childrenWithHardlink
```

## <span data-ttu-id="f0eda-140">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="f0eda-140">PARAMETERS</span></span>

### <span data-ttu-id="f0eda-141">-Stream</span><span class="sxs-lookup"><span data-stu-id="f0eda-141">-Stream</span></span>

<span data-ttu-id="f0eda-142">Hiermee wordt de opgegeven alternatieve NTFS-bestands stroom opgehaald uit het bestand.</span><span class="sxs-lookup"><span data-stu-id="f0eda-142">Gets the specified alternate NTFS file stream from the file.</span></span> <span data-ttu-id="f0eda-143">Voer de naam van de stream in.</span><span class="sxs-lookup"><span data-stu-id="f0eda-143">Enter the stream name.</span></span> <span data-ttu-id="f0eda-144">Joker tekens worden ondersteund.</span><span class="sxs-lookup"><span data-stu-id="f0eda-144">Wildcards are supported.</span></span> <span data-ttu-id="f0eda-145">Als u alle streams wilt ophalen, gebruikt u een asterisk ( `*` ).</span><span class="sxs-lookup"><span data-stu-id="f0eda-145">To get all streams, use an asterisk (`*`).</span></span> <span data-ttu-id="f0eda-146">Deze para meter is niet geldig voor mappen.</span><span class="sxs-lookup"><span data-stu-id="f0eda-146">This parameter isn't valid on folders.</span></span>

<span data-ttu-id="f0eda-147">**Stream** is een dynamische para meter die de **File System** provider toevoegt aan de `Get-Item` cmdlet.</span><span class="sxs-lookup"><span data-stu-id="f0eda-147">**Stream** is a dynamic parameter that the **FileSystem** provider adds to the `Get-Item` cmdlet.</span></span>
<span data-ttu-id="f0eda-148">Deze para meter werkt alleen op stations met een bestands systeem.</span><span class="sxs-lookup"><span data-stu-id="f0eda-148">This parameter works only in file system drives.</span></span>

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

### <span data-ttu-id="f0eda-149">-Credential</span><span class="sxs-lookup"><span data-stu-id="f0eda-149">-Credential</span></span>

> [!NOTE]
> <span data-ttu-id="f0eda-150">Deze para meter wordt niet ondersteund door providers die zijn geïnstalleerd met Power shell.</span><span class="sxs-lookup"><span data-stu-id="f0eda-150">This parameter isn't supported by any providers installed with PowerShell.</span></span>
> <span data-ttu-id="f0eda-151">Gebruik [invoke-Command](../Microsoft.PowerShell.Core/Invoke-Command.md)om een andere gebruiker te imiteren of uw referenties te verhogen wanneer u deze cmdlet uitvoert.</span><span class="sxs-lookup"><span data-stu-id="f0eda-151">To impersonate another user, or elevate your credentials when running this cmdlet, use [Invoke-Command](../Microsoft.PowerShell.Core/Invoke-Command.md).</span></span>

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

### <span data-ttu-id="f0eda-152">-Uitsluiten</span><span class="sxs-lookup"><span data-stu-id="f0eda-152">-Exclude</span></span>

<span data-ttu-id="f0eda-153">Hiermee geeft u als een teken reeks matrix een item of items die met deze cmdlet worden uitgesloten in de bewerking.</span><span class="sxs-lookup"><span data-stu-id="f0eda-153">Specifies, as a string array, an item or items that this cmdlet excludes in the operation.</span></span> <span data-ttu-id="f0eda-154">De waarde van deze para meter komt in aanmerking voor de para meter **Path** .</span><span class="sxs-lookup"><span data-stu-id="f0eda-154">The value of this parameter qualifies the **Path** parameter.</span></span> <span data-ttu-id="f0eda-155">Voer een element of patroon van een pad in, zoals `*.txt` .</span><span class="sxs-lookup"><span data-stu-id="f0eda-155">Enter a path element or pattern, such as `*.txt`.</span></span> <span data-ttu-id="f0eda-156">Joker tekens zijn toegestaan.</span><span class="sxs-lookup"><span data-stu-id="f0eda-156">Wildcard characters are permitted.</span></span> <span data-ttu-id="f0eda-157">De **exclude** -para meter is alleen effectief wanneer de inhoud van een item wordt opgenomen, zoals `C:\Windows\*` , waarbij het Joker teken de inhoud van de `C:\Windows` map bevat.</span><span class="sxs-lookup"><span data-stu-id="f0eda-157">The **Exclude** parameter is effective only when the command includes the contents of an item, such as `C:\Windows\*`, where the wildcard character specifies the contents of the `C:\Windows` directory.</span></span>

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

### <span data-ttu-id="f0eda-158">-Filter</span><span class="sxs-lookup"><span data-stu-id="f0eda-158">-Filter</span></span>

<span data-ttu-id="f0eda-159">Hiermee geeft u een filter op om de para meter **Path** te kwalificeren.</span><span class="sxs-lookup"><span data-stu-id="f0eda-159">Specifies a filter to qualify the **Path** parameter.</span></span> <span data-ttu-id="f0eda-160">De [File System](../Microsoft.PowerShell.Core/About/about_FileSystem_Provider.md) -provider is de enige geïnstalleerde Power shell-provider die filters ondersteunt.</span><span class="sxs-lookup"><span data-stu-id="f0eda-160">The [FileSystem](../Microsoft.PowerShell.Core/About/about_FileSystem_Provider.md) provider is the only installed PowerShell provider that supports filters.</span></span> <span data-ttu-id="f0eda-161">Filters zijn efficiënter dan andere para meters.</span><span class="sxs-lookup"><span data-stu-id="f0eda-161">Filters are more efficient than other parameters.</span></span> <span data-ttu-id="f0eda-162">De provider past filter toe wanneer de cmdlet de objecten ophaalt in plaats van dat Power shell de objecten heeft gefilterd nadat ze zijn opgehaald.</span><span class="sxs-lookup"><span data-stu-id="f0eda-162">The provider applies filter when the cmdlet gets the objects rather than having PowerShell filter the objects after they're retrieved.</span></span> <span data-ttu-id="f0eda-163">De filter teken reeks wordt door gegeven aan de .NET API om bestanden te inventariseren.</span><span class="sxs-lookup"><span data-stu-id="f0eda-163">The filter string is passed to the .NET API to enumerate files.</span></span> <span data-ttu-id="f0eda-164">De API ondersteunt alleen `*` en `?` joker tekens.</span><span class="sxs-lookup"><span data-stu-id="f0eda-164">The API only supports `*` and `?` wildcards.</span></span>

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

### <span data-ttu-id="f0eda-165">-Force</span><span class="sxs-lookup"><span data-stu-id="f0eda-165">-Force</span></span>

<span data-ttu-id="f0eda-166">Geeft aan dat met deze cmdlet items worden opgehaald die niet kunnen worden geopend, zoals verborgen items.</span><span class="sxs-lookup"><span data-stu-id="f0eda-166">Indicates that this cmdlet gets items that can't otherwise be accessed, such as hidden items.</span></span>
<span data-ttu-id="f0eda-167">De implementatie varieert van provider tot provider.</span><span class="sxs-lookup"><span data-stu-id="f0eda-167">Implementation varies from provider to provider.</span></span> <span data-ttu-id="f0eda-168">Zie [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="f0eda-168">For more information, see [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md).</span></span> <span data-ttu-id="f0eda-169">Zelfs met behulp van de para meter **forceren** , kunnen de cmdlet geen beveiligings beperkingen opheffen.</span><span class="sxs-lookup"><span data-stu-id="f0eda-169">Even using the **Force** parameter, the cmdlet can't override security restrictions.</span></span>

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

### <span data-ttu-id="f0eda-170">-Include</span><span class="sxs-lookup"><span data-stu-id="f0eda-170">-Include</span></span>

<span data-ttu-id="f0eda-171">Hiermee wordt een teken reeks matrix opgegeven, een item of items die met deze cmdlet in de bewerking zijn opgenomen.</span><span class="sxs-lookup"><span data-stu-id="f0eda-171">Specifies, as a string array, an item or items that this cmdlet includes in the operation.</span></span> <span data-ttu-id="f0eda-172">De waarde van deze para meter komt in aanmerking voor de para meter **Path** .</span><span class="sxs-lookup"><span data-stu-id="f0eda-172">The value of this parameter qualifies the **Path** parameter.</span></span> <span data-ttu-id="f0eda-173">Voer een element of patroon van een pad in, zoals `*.txt` .</span><span class="sxs-lookup"><span data-stu-id="f0eda-173">Enter a path element or pattern, such as `*.txt`.</span></span> <span data-ttu-id="f0eda-174">Joker tekens zijn toegestaan.</span><span class="sxs-lookup"><span data-stu-id="f0eda-174">Wildcard characters are permitted.</span></span> <span data-ttu-id="f0eda-175">De para meter **include** is alleen effectief wanneer de inhoud van een item wordt opgenomen, zoals `C:\Windows\*` , waarbij het Joker teken de inhoud van de `C:\Windows` map bevat.</span><span class="sxs-lookup"><span data-stu-id="f0eda-175">The **Include** parameter is effective only when the command includes the contents of an item, such as `C:\Windows\*`, where the wildcard character specifies the contents of the `C:\Windows` directory.</span></span>

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

### <span data-ttu-id="f0eda-176">-LiteralPath</span><span class="sxs-lookup"><span data-stu-id="f0eda-176">-LiteralPath</span></span>

<span data-ttu-id="f0eda-177">Hiermee geeft u een pad naar een of meer locaties.</span><span class="sxs-lookup"><span data-stu-id="f0eda-177">Specifies a path to one or more locations.</span></span> <span data-ttu-id="f0eda-178">De waarde van **LiteralPath** wordt precies zo gebruikt als deze wordt getypt.</span><span class="sxs-lookup"><span data-stu-id="f0eda-178">The value of **LiteralPath** is used exactly as it's typed.</span></span> <span data-ttu-id="f0eda-179">Geen tekens worden geïnterpreteerd als joker tekens.</span><span class="sxs-lookup"><span data-stu-id="f0eda-179">No characters are interpreted as wildcards.</span></span> <span data-ttu-id="f0eda-180">Als het pad escape tekens bevat, plaatst u het tussen enkele aanhalings tekens.</span><span class="sxs-lookup"><span data-stu-id="f0eda-180">If the path includes escape characters, enclose it in single quotation marks.</span></span> <span data-ttu-id="f0eda-181">Enkele aanhalings tekens geven aan dat Power shell geen karakters interpreteert als escape reeksen.</span><span class="sxs-lookup"><span data-stu-id="f0eda-181">Single quotation marks tell PowerShell not to interpret any characters as escape sequences.</span></span>

<span data-ttu-id="f0eda-182">Zie [about_Quoting_Rules](../Microsoft.Powershell.Core/About/about_Quoting_Rules.md)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="f0eda-182">For more information, see [about_Quoting_Rules](../Microsoft.Powershell.Core/About/about_Quoting_Rules.md).</span></span>

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

### <span data-ttu-id="f0eda-183">-Path</span><span class="sxs-lookup"><span data-stu-id="f0eda-183">-Path</span></span>

<span data-ttu-id="f0eda-184">Hiermee geeft u het pad naar een item.</span><span class="sxs-lookup"><span data-stu-id="f0eda-184">Specifies the path to an item.</span></span> <span data-ttu-id="f0eda-185">Met deze cmdlet wordt het item op de opgegeven locatie opgehaald.</span><span class="sxs-lookup"><span data-stu-id="f0eda-185">This cmdlet gets the item at the specified location.</span></span> <span data-ttu-id="f0eda-186">Joker tekens zijn toegestaan.</span><span class="sxs-lookup"><span data-stu-id="f0eda-186">Wildcard characters are permitted.</span></span> <span data-ttu-id="f0eda-187">Deze para meter is vereist, maar het **pad naar** de parameter naam is optioneel.</span><span class="sxs-lookup"><span data-stu-id="f0eda-187">This parameter is required, but the parameter name **Path** is optional.</span></span>

<span data-ttu-id="f0eda-188">Gebruik een punt ( `.` ) om de huidige locatie op te geven.</span><span class="sxs-lookup"><span data-stu-id="f0eda-188">Use a dot (`.`) to specify the current location.</span></span> <span data-ttu-id="f0eda-189">Gebruik het Joker teken ( `*` ) om alle items op de huidige locatie op te geven.</span><span class="sxs-lookup"><span data-stu-id="f0eda-189">Use the wildcard character (`*`) to specify all the items in the current location.</span></span>

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

### <span data-ttu-id="f0eda-190">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="f0eda-190">CommonParameters</span></span>

<span data-ttu-id="f0eda-191">Deze cmdlet biedt ondersteuning voor de algemene para meters: `-Debug` , `-ErrorAction` , `-ErrorVariable` , `-InformationAction` , `-InformationVariable` , `-OutVariable` , `-OutBuffer` , `-PipelineVariable` , `-Verbose` , `-WarningAction` en `-WarningVariable` .</span><span class="sxs-lookup"><span data-stu-id="f0eda-191">This cmdlet supports the common parameters: `-Debug`, `-ErrorAction`, `-ErrorVariable`, `-InformationAction`, `-InformationVariable`, `-OutVariable`, `-OutBuffer`, `-PipelineVariable`, `-Verbose`, `-WarningAction`, and `-WarningVariable`.</span></span> <span data-ttu-id="f0eda-192">Zie [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="f0eda-192">For more information, see [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md).</span></span>

## <span data-ttu-id="f0eda-193">INVOER</span><span class="sxs-lookup"><span data-stu-id="f0eda-193">INPUTS</span></span>

### <span data-ttu-id="f0eda-194">System. String</span><span class="sxs-lookup"><span data-stu-id="f0eda-194">System.String</span></span>

<span data-ttu-id="f0eda-195">U kunt een teken reeks met een pad naar deze cmdlet door sluizen.</span><span class="sxs-lookup"><span data-stu-id="f0eda-195">You can pipe a string that contains a path to this cmdlet.</span></span>

## <span data-ttu-id="f0eda-196">UITVOER</span><span class="sxs-lookup"><span data-stu-id="f0eda-196">OUTPUTS</span></span>

### <span data-ttu-id="f0eda-197">System. object</span><span class="sxs-lookup"><span data-stu-id="f0eda-197">System.Object</span></span>

<span data-ttu-id="f0eda-198">Deze cmdlet retourneert de objecten die worden opgehaald.</span><span class="sxs-lookup"><span data-stu-id="f0eda-198">This cmdlet returns the objects that it gets.</span></span> <span data-ttu-id="f0eda-199">Het type wordt bepaald door het type objecten in het pad.</span><span class="sxs-lookup"><span data-stu-id="f0eda-199">The type is determined by the type of objects in the path.</span></span>

## <span data-ttu-id="f0eda-200">OPMERKINGEN</span><span class="sxs-lookup"><span data-stu-id="f0eda-200">NOTES</span></span>

<span data-ttu-id="f0eda-201">Deze cmdlet heeft geen **recursieve** para meter, omdat alleen een item wordt opgehaald, niet de inhoud ervan.</span><span class="sxs-lookup"><span data-stu-id="f0eda-201">This cmdlet does not have a **Recurse** parameter, because it gets only an item, not its contents.</span></span>
<span data-ttu-id="f0eda-202">Als u de inhoud van een item recursief wilt ophalen, gebruikt u `Get-ChildItem` .</span><span class="sxs-lookup"><span data-stu-id="f0eda-202">To get the contents of an item recursively, use `Get-ChildItem`.</span></span>

<span data-ttu-id="f0eda-203">Als u door het REGI ster wilt navigeren, gebruikt u deze cmdlet voor het ophalen van register sleutels en de `Get-ItemProperty` om register waarden en-gegevens op te halen.</span><span class="sxs-lookup"><span data-stu-id="f0eda-203">To navigate through the registry, use this cmdlet to get registry keys and the `Get-ItemProperty` to get registry values and data.</span></span> <span data-ttu-id="f0eda-204">De register waarden worden beschouwd als eigenschappen van de register sleutel.</span><span class="sxs-lookup"><span data-stu-id="f0eda-204">The registry values are considered to be properties of the registry key.</span></span>
  
<span data-ttu-id="f0eda-205">Deze cmdlet is ontworpen om te werken met de gegevens die door elke provider worden weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="f0eda-205">This cmdlet is designed to work with the data exposed by any provider.</span></span> <span data-ttu-id="f0eda-206">Als u een lijst wilt weer geven van de providers die beschikbaar zijn in uw sessie, typt u `Get-PsProvider` .</span><span class="sxs-lookup"><span data-stu-id="f0eda-206">To list the providers available in your session, type `Get-PsProvider`.</span></span> <span data-ttu-id="f0eda-207">Zie [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="f0eda-207">For more information, see [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md).</span></span>

## <span data-ttu-id="f0eda-208">GERELATEERDE KOPPELINGEN</span><span class="sxs-lookup"><span data-stu-id="f0eda-208">RELATED LINKS</span></span>

[<span data-ttu-id="f0eda-209">Wissen-item</span><span class="sxs-lookup"><span data-stu-id="f0eda-209">Clear-Item</span></span>](Clear-Item.md)

[<span data-ttu-id="f0eda-210">Kopie-item</span><span class="sxs-lookup"><span data-stu-id="f0eda-210">Copy-Item</span></span>](Copy-Item.md)

[<span data-ttu-id="f0eda-211">Invoke-item</span><span class="sxs-lookup"><span data-stu-id="f0eda-211">Invoke-Item</span></span>](Invoke-Item.md)

[<span data-ttu-id="f0eda-212">Item verplaatsen</span><span class="sxs-lookup"><span data-stu-id="f0eda-212">Move-Item</span></span>](Move-Item.md)

[<span data-ttu-id="f0eda-213">Nieuw-item</span><span class="sxs-lookup"><span data-stu-id="f0eda-213">New-Item</span></span>](New-Item.md)

[<span data-ttu-id="f0eda-214">Verwijderen-item</span><span class="sxs-lookup"><span data-stu-id="f0eda-214">Remove-Item</span></span>](Remove-Item.md)

[<span data-ttu-id="f0eda-215">Naam wijzigen-item</span><span class="sxs-lookup"><span data-stu-id="f0eda-215">Rename-Item</span></span>](Rename-Item.md)

[<span data-ttu-id="f0eda-216">Set-item</span><span class="sxs-lookup"><span data-stu-id="f0eda-216">Set-Item</span></span>](Set-Item.md)

[<span data-ttu-id="f0eda-217">Get-Child item</span><span class="sxs-lookup"><span data-stu-id="f0eda-217">Get-ChildItem</span></span>](Get-ChildItem.md)

[<span data-ttu-id="f0eda-218">Get-item Property</span><span class="sxs-lookup"><span data-stu-id="f0eda-218">Get-ItemProperty</span></span>](Get-ItemProperty.md)

[<span data-ttu-id="f0eda-219">Get-PSProvider</span><span class="sxs-lookup"><span data-stu-id="f0eda-219">Get-PSProvider</span></span>](Get-PSProvider.md)

[<span data-ttu-id="f0eda-220">about_Providers</span><span class="sxs-lookup"><span data-stu-id="f0eda-220">about_Providers</span></span>](../Microsoft.PowerShell.Core/About/about_Providers.md)
