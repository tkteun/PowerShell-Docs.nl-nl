---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 03/27/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/get-item?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-Item
ms.openlocfilehash: 1498c7eb254e0d21b108c4016d8b737d5b33298d
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/07/2020
ms.locfileid: "93250797"
---
# <span data-ttu-id="b9e84-103">Get-Item</span><span class="sxs-lookup"><span data-stu-id="b9e84-103">Get-Item</span></span>

## <span data-ttu-id="b9e84-104">SAMENVATTING</span><span class="sxs-lookup"><span data-stu-id="b9e84-104">SYNOPSIS</span></span>
<span data-ttu-id="b9e84-105">Hiermee wordt het item op de opgegeven locatie opgehaald.</span><span class="sxs-lookup"><span data-stu-id="b9e84-105">Gets the item at the specified location.</span></span>

## <span data-ttu-id="b9e84-106">SYNTAXIS</span><span class="sxs-lookup"><span data-stu-id="b9e84-106">SYNTAX</span></span>

### <span data-ttu-id="b9e84-107">Pad (standaard)</span><span class="sxs-lookup"><span data-stu-id="b9e84-107">Path (Default)</span></span>

```
Get-Item [-Path] <String[]> [-Filter <String>] [-Include <String[]>] [-Exclude <String[]>] [-Force]
 [-Credential <PSCredential>] [-UseTransaction] [-Stream <String[]>] [<CommonParameters>]
```

### <span data-ttu-id="b9e84-108">LiteralPath</span><span class="sxs-lookup"><span data-stu-id="b9e84-108">LiteralPath</span></span>

```
Get-Item -LiteralPath <String[]> [-Filter <String>] [-Include <String[]>] [-Exclude <String[]>] [-Force]
 [-Credential <PSCredential>] [-UseTransaction] [-Stream <String[]>] [<CommonParameters>]
```

## <span data-ttu-id="b9e84-109">BESCHRIJVING</span><span class="sxs-lookup"><span data-stu-id="b9e84-109">DESCRIPTION</span></span>

<span data-ttu-id="b9e84-110">`Get-Item`Met de cmdlet wordt het item op de opgegeven locatie opgehaald.</span><span class="sxs-lookup"><span data-stu-id="b9e84-110">The `Get-Item` cmdlet gets the item at the specified location.</span></span> <span data-ttu-id="b9e84-111">De inhoud van het item op de locatie wordt niet opgehaald, tenzij u een Joker teken ( `*` ) gebruikt om alle inhoud van het item aan te vragen.</span><span class="sxs-lookup"><span data-stu-id="b9e84-111">It doesn't get the contents of the item at the location unless you use a wildcard character (`*`) to request all the contents of the item.</span></span>

<span data-ttu-id="b9e84-112">Deze cmdlet wordt gebruikt door Power shell-providers om door verschillende typen gegevens archieven te navigeren.</span><span class="sxs-lookup"><span data-stu-id="b9e84-112">This cmdlet is used by PowerShell providers to navigate through different types of data stores.</span></span>

## <span data-ttu-id="b9e84-113">VOORBEELDEN</span><span class="sxs-lookup"><span data-stu-id="b9e84-113">EXAMPLES</span></span>

### <span data-ttu-id="b9e84-114">Voor beeld 1: de huidige map ophalen</span><span class="sxs-lookup"><span data-stu-id="b9e84-114">Example 1: Get the current directory</span></span>

<span data-ttu-id="b9e84-115">In dit voor beeld wordt de huidige map opgehaald.</span><span class="sxs-lookup"><span data-stu-id="b9e84-115">This example gets the current directory.</span></span> <span data-ttu-id="b9e84-116">De punt ('. ') staat voor het item op de huidige locatie (niet de inhoud).</span><span class="sxs-lookup"><span data-stu-id="b9e84-116">The dot ('.') represents the item at the current location (not its contents).</span></span>

```powershell
Get-Item .
```

```output
Directory: C:\

Mode                LastWriteTime     Length Name
----                -------------     ------ ----
d----         7/26/2006  10:01 AM            ps-test
```

### <span data-ttu-id="b9e84-117">Voor beeld 2: alle items in de huidige map ophalen</span><span class="sxs-lookup"><span data-stu-id="b9e84-117">Example 2: Get all the items in the current directory</span></span>

<span data-ttu-id="b9e84-118">In dit voor beeld worden alle items in de huidige map opgehaald.</span><span class="sxs-lookup"><span data-stu-id="b9e84-118">This example gets all the items in the current directory.</span></span> <span data-ttu-id="b9e84-119">Het Joker teken ( `*` ) vertegenwoordigt alle inhoud van het huidige item.</span><span class="sxs-lookup"><span data-stu-id="b9e84-119">The wildcard character (`*`) represents all the contents of the current item.</span></span>

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

### <span data-ttu-id="b9e84-120">Voor beeld 3: de huidige map van een station ophalen</span><span class="sxs-lookup"><span data-stu-id="b9e84-120">Example 3: Get the current directory of a drive</span></span>

<span data-ttu-id="b9e84-121">In dit voor beeld wordt de huidige map van het `C:` station opgehaald.</span><span class="sxs-lookup"><span data-stu-id="b9e84-121">This example gets the current directory of the `C:` drive.</span></span> <span data-ttu-id="b9e84-122">Het opgehaalde object staat alleen voor de map en niet de inhoud ervan.</span><span class="sxs-lookup"><span data-stu-id="b9e84-122">The object that is retrieved represents only the directory, not its contents.</span></span>

```powershell
Get-Item C:\
```

### <span data-ttu-id="b9e84-123">Voor beeld 4: items in het opgegeven station ophalen</span><span class="sxs-lookup"><span data-stu-id="b9e84-123">Example 4: Get items in the specified drive</span></span>

<span data-ttu-id="b9e84-124">In dit voor beeld worden de items in het `C:` station opgehaald.</span><span class="sxs-lookup"><span data-stu-id="b9e84-124">This example gets the items in the `C:` drive.</span></span> <span data-ttu-id="b9e84-125">Het Joker teken ( `*` ) vertegenwoordigt alle items in de container, niet alleen de container.</span><span class="sxs-lookup"><span data-stu-id="b9e84-125">The wildcard character (`*`) represents all the items in the container, not just the container.</span></span>

```powershell
Get-Item C:\*
```

<span data-ttu-id="b9e84-126">Gebruik in Power shell één asterisk ( `*` ) om inhoud op te halen in plaats van de traditionele `*.*` .</span><span class="sxs-lookup"><span data-stu-id="b9e84-126">In PowerShell, use a single asterisk (`*`) to get contents, instead of the traditional `*.*`.</span></span> <span data-ttu-id="b9e84-127">De indeling wordt letterlijk geïnterpreteerd, waardoor `*.*` er geen mappen of bestands namen worden opgehaald zonder een punt.</span><span class="sxs-lookup"><span data-stu-id="b9e84-127">The format is interpreted literally, so `*.*` wouldn't retrieve directories or filenames without a dot.</span></span>

### <span data-ttu-id="b9e84-128">Voor beeld 5: een eigenschap ophalen in de opgegeven map</span><span class="sxs-lookup"><span data-stu-id="b9e84-128">Example 5: Get a property in the specified directory</span></span>

<span data-ttu-id="b9e84-129">In dit voor beeld wordt de eigenschap **LastAccessTime** van de `C:\Windows` Directory opgehaald.</span><span class="sxs-lookup"><span data-stu-id="b9e84-129">This example gets the **LastAccessTime** property of the `C:\Windows` directory.</span></span> <span data-ttu-id="b9e84-130">**LastAccessTime** is slechts één eigenschap van File System directory's.</span><span class="sxs-lookup"><span data-stu-id="b9e84-130">**LastAccessTime** is just one property of file system directories.</span></span> <span data-ttu-id="b9e84-131">Als u alle eigenschappen van een map wilt weer geven, typt u `(Get-Item <directory-name>) | Get-Member` .</span><span class="sxs-lookup"><span data-stu-id="b9e84-131">To see all the properties of a directory, type `(Get-Item <directory-name>) | Get-Member`.</span></span>

```powershell
(Get-Item C:\Windows).LastAccessTime
```

### <span data-ttu-id="b9e84-132">Voor beeld 6: de inhoud van een register sleutel weer geven</span><span class="sxs-lookup"><span data-stu-id="b9e84-132">Example 6: Show the contents of a registry key</span></span>

<span data-ttu-id="b9e84-133">In dit voor beeld wordt de inhoud van de register sleutel **micro soft. Power shell** weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="b9e84-133">This example shows the contents of the **Microsoft.PowerShell** registry key.</span></span> <span data-ttu-id="b9e84-134">U kunt deze cmdlet gebruiken met de Power shell-register provider om register sleutels en subsleutels op te halen, maar u moet de `Get-ItemProperty` cmdlet gebruiken om de register waarden en-gegevens op te halen.</span><span class="sxs-lookup"><span data-stu-id="b9e84-134">You can use this cmdlet with the PowerShell Registry provider to get registry keys and subkeys, but you must use the `Get-ItemProperty` cmdlet to get the registry values and data.</span></span>

```powershell
Get-Item HKLM:\Software\Microsoft\Powershell\1\Shellids\Microsoft.Powershell\
```

### <span data-ttu-id="b9e84-135">Voor beeld 7: items in een directory met een uitsluiting ophalen</span><span class="sxs-lookup"><span data-stu-id="b9e84-135">Example 7: Get items in a directory that have an exclusion</span></span>

<span data-ttu-id="b9e84-136">In dit voor beeld worden items in de Windows-map met namen die een punt ( `.` ) bevatten, maar niet beginnen met `w*` . Dit voor beeld werkt alleen wanneer het pad een Joker teken ( `*` ) bevat om de inhoud van het item op te geven.</span><span class="sxs-lookup"><span data-stu-id="b9e84-136">This example gets items in the Windows directory with names that include a dot (`.`), but don't begin with `w*`.This example works only when the path includes a wildcard character (`*`) to specify the contents of the item.</span></span>

```powershell
Get-Item C:\Windows\*.* -Exclude "w*"
```

## <span data-ttu-id="b9e84-137">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="b9e84-137">PARAMETERS</span></span>

### <span data-ttu-id="b9e84-138">-Stream</span><span class="sxs-lookup"><span data-stu-id="b9e84-138">-Stream</span></span>

<span data-ttu-id="b9e84-139">Hiermee wordt de opgegeven alternatieve NTFS-bestands stroom opgehaald uit het bestand.</span><span class="sxs-lookup"><span data-stu-id="b9e84-139">Gets the specified alternate NTFS file stream from the file.</span></span> <span data-ttu-id="b9e84-140">Voer de naam van de stream in.</span><span class="sxs-lookup"><span data-stu-id="b9e84-140">Enter the stream name.</span></span> <span data-ttu-id="b9e84-141">Joker tekens worden ondersteund.</span><span class="sxs-lookup"><span data-stu-id="b9e84-141">Wildcards are supported.</span></span> <span data-ttu-id="b9e84-142">Als u alle streams wilt ophalen, gebruikt u een asterisk ( `*` ).</span><span class="sxs-lookup"><span data-stu-id="b9e84-142">To get all streams, use an asterisk (`*`).</span></span> <span data-ttu-id="b9e84-143">Deze para meter is niet geldig voor mappen.</span><span class="sxs-lookup"><span data-stu-id="b9e84-143">This parameter isn't valid on folders.</span></span>

<span data-ttu-id="b9e84-144">**Stream** is een dynamische para meter die de **File System** provider toevoegt aan de `Get-Item` cmdlet.</span><span class="sxs-lookup"><span data-stu-id="b9e84-144">**Stream** is a dynamic parameter that the **FileSystem** provider adds to the `Get-Item` cmdlet.</span></span>
<span data-ttu-id="b9e84-145">Deze para meter werkt alleen op stations met een bestands systeem.</span><span class="sxs-lookup"><span data-stu-id="b9e84-145">This parameter works only in file system drives.</span></span>

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

### <span data-ttu-id="b9e84-146">-Credential</span><span class="sxs-lookup"><span data-stu-id="b9e84-146">-Credential</span></span>

> [!NOTE]
> <span data-ttu-id="b9e84-147">Deze para meter wordt niet ondersteund door providers die zijn geïnstalleerd met Power shell.</span><span class="sxs-lookup"><span data-stu-id="b9e84-147">This parameter isn't supported by any providers installed with PowerShell.</span></span>
> <span data-ttu-id="b9e84-148">Gebruik [invoke-Command](../Microsoft.PowerShell.Core/Invoke-Command.md)om een andere gebruiker te imiteren of uw referenties te verhogen wanneer u deze cmdlet uitvoert.</span><span class="sxs-lookup"><span data-stu-id="b9e84-148">To impersonate another user, or elevate your credentials when running this cmdlet, use [Invoke-Command](../Microsoft.PowerShell.Core/Invoke-Command.md).</span></span>

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

### <span data-ttu-id="b9e84-149">-Uitsluiten</span><span class="sxs-lookup"><span data-stu-id="b9e84-149">-Exclude</span></span>

<span data-ttu-id="b9e84-150">Hiermee geeft u als een teken reeks matrix een item of items die met deze cmdlet worden uitgesloten in de bewerking.</span><span class="sxs-lookup"><span data-stu-id="b9e84-150">Specifies, as a string array, an item or items that this cmdlet excludes in the operation.</span></span> <span data-ttu-id="b9e84-151">De waarde van deze para meter komt in aanmerking voor de para meter **Path** .</span><span class="sxs-lookup"><span data-stu-id="b9e84-151">The value of this parameter qualifies the **Path** parameter.</span></span> <span data-ttu-id="b9e84-152">Voer een element of patroon van een pad in, zoals `*.txt` .</span><span class="sxs-lookup"><span data-stu-id="b9e84-152">Enter a path element or pattern, such as `*.txt`.</span></span> <span data-ttu-id="b9e84-153">Joker tekens zijn toegestaan.</span><span class="sxs-lookup"><span data-stu-id="b9e84-153">Wildcard characters are permitted.</span></span> <span data-ttu-id="b9e84-154">De **exclude** -para meter is alleen effectief wanneer de inhoud van een item wordt opgenomen, zoals `C:\Windows\*` , waarbij het Joker teken de inhoud van de `C:\Windows` map bevat.</span><span class="sxs-lookup"><span data-stu-id="b9e84-154">The **Exclude** parameter is effective only when the command includes the contents of an item, such as `C:\Windows\*`, where the wildcard character specifies the contents of the `C:\Windows` directory.</span></span>

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

### <span data-ttu-id="b9e84-155">-Filter</span><span class="sxs-lookup"><span data-stu-id="b9e84-155">-Filter</span></span>

<span data-ttu-id="b9e84-156">Hiermee geeft u een filter op om de para meter **Path** te kwalificeren.</span><span class="sxs-lookup"><span data-stu-id="b9e84-156">Specifies a filter to qualify the **Path** parameter.</span></span> <span data-ttu-id="b9e84-157">De [File System](../Microsoft.PowerShell.Core/About/about_FileSystem_Provider.md) -provider is de enige geïnstalleerde Power shell-provider die filters ondersteunt.</span><span class="sxs-lookup"><span data-stu-id="b9e84-157">The [FileSystem](../Microsoft.PowerShell.Core/About/about_FileSystem_Provider.md) provider is the only installed PowerShell provider that supports filters.</span></span> <span data-ttu-id="b9e84-158">Filters zijn efficiënter dan andere para meters.</span><span class="sxs-lookup"><span data-stu-id="b9e84-158">Filters are more efficient than other parameters.</span></span> <span data-ttu-id="b9e84-159">De provider past filter toe wanneer de cmdlet de objecten ophaalt in plaats van dat Power shell de objecten heeft gefilterd nadat ze zijn opgehaald.</span><span class="sxs-lookup"><span data-stu-id="b9e84-159">The provider applies filter when the cmdlet gets the objects rather than having PowerShell filter the objects after they're retrieved.</span></span> <span data-ttu-id="b9e84-160">De filter teken reeks wordt door gegeven aan de .NET API om bestanden te inventariseren.</span><span class="sxs-lookup"><span data-stu-id="b9e84-160">The filter string is passed to the .NET API to enumerate files.</span></span> <span data-ttu-id="b9e84-161">De API ondersteunt alleen `*` en `?` joker tekens.</span><span class="sxs-lookup"><span data-stu-id="b9e84-161">The API only supports `*` and `?` wildcards.</span></span>

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

### <span data-ttu-id="b9e84-162">-Force</span><span class="sxs-lookup"><span data-stu-id="b9e84-162">-Force</span></span>

<span data-ttu-id="b9e84-163">Geeft aan dat met deze cmdlet items worden opgehaald die niet kunnen worden geopend, zoals verborgen items.</span><span class="sxs-lookup"><span data-stu-id="b9e84-163">Indicates that this cmdlet gets items that can't otherwise be accessed, such as hidden items.</span></span>
<span data-ttu-id="b9e84-164">De implementatie varieert van provider tot provider.</span><span class="sxs-lookup"><span data-stu-id="b9e84-164">Implementation varies from provider to provider.</span></span> <span data-ttu-id="b9e84-165">Zie [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="b9e84-165">For more information, see [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md).</span></span> <span data-ttu-id="b9e84-166">Zelfs met behulp van de para meter **forceren** , kunnen de cmdlet geen beveiligings beperkingen opheffen.</span><span class="sxs-lookup"><span data-stu-id="b9e84-166">Even using the **Force** parameter, the cmdlet can't override security restrictions.</span></span>

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

### <span data-ttu-id="b9e84-167">-Include</span><span class="sxs-lookup"><span data-stu-id="b9e84-167">-Include</span></span>

<span data-ttu-id="b9e84-168">Hiermee wordt een teken reeks matrix opgegeven, een item of items die met deze cmdlet in de bewerking zijn opgenomen.</span><span class="sxs-lookup"><span data-stu-id="b9e84-168">Specifies, as a string array, an item or items that this cmdlet includes in the operation.</span></span> <span data-ttu-id="b9e84-169">De waarde van deze para meter komt in aanmerking voor de para meter **Path** .</span><span class="sxs-lookup"><span data-stu-id="b9e84-169">The value of this parameter qualifies the **Path** parameter.</span></span> <span data-ttu-id="b9e84-170">Voer een element of patroon van een pad in, zoals `*.txt` .</span><span class="sxs-lookup"><span data-stu-id="b9e84-170">Enter a path element or pattern, such as `*.txt`.</span></span> <span data-ttu-id="b9e84-171">Joker tekens zijn toegestaan.</span><span class="sxs-lookup"><span data-stu-id="b9e84-171">Wildcard characters are permitted.</span></span> <span data-ttu-id="b9e84-172">De para meter **include** is alleen effectief wanneer de inhoud van een item wordt opgenomen, zoals `C:\Windows\*` , waarbij het Joker teken de inhoud van de `C:\Windows` map bevat.</span><span class="sxs-lookup"><span data-stu-id="b9e84-172">The **Include** parameter is effective only when the command includes the contents of an item, such as `C:\Windows\*`, where the wildcard character specifies the contents of the `C:\Windows` directory.</span></span>

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

### <span data-ttu-id="b9e84-173">-LiteralPath</span><span class="sxs-lookup"><span data-stu-id="b9e84-173">-LiteralPath</span></span>

<span data-ttu-id="b9e84-174">Hiermee geeft u een pad naar een of meer locaties.</span><span class="sxs-lookup"><span data-stu-id="b9e84-174">Specifies a path to one or more locations.</span></span> <span data-ttu-id="b9e84-175">De waarde van **LiteralPath** wordt precies zo gebruikt als deze wordt getypt.</span><span class="sxs-lookup"><span data-stu-id="b9e84-175">The value of **LiteralPath** is used exactly as it's typed.</span></span> <span data-ttu-id="b9e84-176">Geen tekens worden geïnterpreteerd als joker tekens.</span><span class="sxs-lookup"><span data-stu-id="b9e84-176">No characters are interpreted as wildcards.</span></span> <span data-ttu-id="b9e84-177">Als het pad escape tekens bevat, plaatst u het tussen enkele aanhalings tekens.</span><span class="sxs-lookup"><span data-stu-id="b9e84-177">If the path includes escape characters, enclose it in single quotation marks.</span></span> <span data-ttu-id="b9e84-178">Enkele aanhalings tekens geven aan dat Power shell geen karakters interpreteert als escape reeksen.</span><span class="sxs-lookup"><span data-stu-id="b9e84-178">Single quotation marks tell PowerShell not to interpret any characters as escape sequences.</span></span>

<span data-ttu-id="b9e84-179">Zie [about_Quoting_Rules](../Microsoft.Powershell.Core/About/about_Quoting_Rules.md)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="b9e84-179">For more information, see [about_Quoting_Rules](../Microsoft.Powershell.Core/About/about_Quoting_Rules.md).</span></span>

```yaml
Type: System.String[]
Parameter Sets: LiteralPath
Aliases: PSPath

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="b9e84-180">-Path</span><span class="sxs-lookup"><span data-stu-id="b9e84-180">-Path</span></span>

<span data-ttu-id="b9e84-181">Hiermee geeft u het pad naar een item.</span><span class="sxs-lookup"><span data-stu-id="b9e84-181">Specifies the path to an item.</span></span> <span data-ttu-id="b9e84-182">Met deze cmdlet wordt het item op de opgegeven locatie opgehaald.</span><span class="sxs-lookup"><span data-stu-id="b9e84-182">This cmdlet gets the item at the specified location.</span></span> <span data-ttu-id="b9e84-183">Joker tekens zijn toegestaan.</span><span class="sxs-lookup"><span data-stu-id="b9e84-183">Wildcard characters are permitted.</span></span> <span data-ttu-id="b9e84-184">Deze para meter is vereist, maar het **pad naar** de parameter naam is optioneel.</span><span class="sxs-lookup"><span data-stu-id="b9e84-184">This parameter is required, but the parameter name **Path** is optional.</span></span>

<span data-ttu-id="b9e84-185">Gebruik een punt ( `.` ) om de huidige locatie op te geven.</span><span class="sxs-lookup"><span data-stu-id="b9e84-185">Use a dot (`.`) to specify the current location.</span></span> <span data-ttu-id="b9e84-186">Gebruik het Joker teken ( `*` ) om alle items op de huidige locatie op te geven.</span><span class="sxs-lookup"><span data-stu-id="b9e84-186">Use the wildcard character (`*`) to specify all the items in the current location.</span></span>

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

### <span data-ttu-id="b9e84-187">-UseTransaction</span><span class="sxs-lookup"><span data-stu-id="b9e84-187">-UseTransaction</span></span>

<span data-ttu-id="b9e84-188">Hiermee wordt de opdracht opgenomen in de actieve transactie.</span><span class="sxs-lookup"><span data-stu-id="b9e84-188">Includes the command in the active transaction.</span></span>
<span data-ttu-id="b9e84-189">Deze parameter is alleen geldig wanneer een transactie wordt uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="b9e84-189">This parameter is valid only when a transaction is in progress.</span></span>
<span data-ttu-id="b9e84-190">Zie [about_Transactions](../Microsoft.PowerShell.Core/About/about_Transactions.md)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="b9e84-190">For more information, see [about_Transactions](../Microsoft.PowerShell.Core/About/about_Transactions.md).</span></span>

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

### <span data-ttu-id="b9e84-191">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="b9e84-191">CommonParameters</span></span>

<span data-ttu-id="b9e84-192">Deze cmdlet biedt ondersteuning voor de algemene para meters: `-Debug` , `-ErrorAction` , `-ErrorVariable` , `-InformationAction` , `-InformationVariable` , `-OutVariable` , `-OutBuffer` , `-PipelineVariable` , `-Verbose` , `-WarningAction` en `-WarningVariable` .</span><span class="sxs-lookup"><span data-stu-id="b9e84-192">This cmdlet supports the common parameters: `-Debug`, `-ErrorAction`, `-ErrorVariable`, `-InformationAction`, `-InformationVariable`, `-OutVariable`, `-OutBuffer`, `-PipelineVariable`, `-Verbose`, `-WarningAction`, and `-WarningVariable`.</span></span> <span data-ttu-id="b9e84-193">Zie [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="b9e84-193">For more information, see [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md).</span></span>

## <span data-ttu-id="b9e84-194">INVOER</span><span class="sxs-lookup"><span data-stu-id="b9e84-194">INPUTS</span></span>

### <span data-ttu-id="b9e84-195">System. String</span><span class="sxs-lookup"><span data-stu-id="b9e84-195">System.String</span></span>

<span data-ttu-id="b9e84-196">U kunt een teken reeks met een pad naar deze cmdlet door sluizen.</span><span class="sxs-lookup"><span data-stu-id="b9e84-196">You can pipe a string that contains a path to this cmdlet.</span></span>

## <span data-ttu-id="b9e84-197">UITVOER</span><span class="sxs-lookup"><span data-stu-id="b9e84-197">OUTPUTS</span></span>

### <span data-ttu-id="b9e84-198">System. object</span><span class="sxs-lookup"><span data-stu-id="b9e84-198">System.Object</span></span>

<span data-ttu-id="b9e84-199">Deze cmdlet retourneert de objecten die worden opgehaald.</span><span class="sxs-lookup"><span data-stu-id="b9e84-199">This cmdlet returns the objects that it gets.</span></span> <span data-ttu-id="b9e84-200">Het type wordt bepaald door het type objecten in het pad.</span><span class="sxs-lookup"><span data-stu-id="b9e84-200">The type is determined by the type of objects in the path.</span></span>

## <span data-ttu-id="b9e84-201">OPMERKINGEN</span><span class="sxs-lookup"><span data-stu-id="b9e84-201">NOTES</span></span>

<span data-ttu-id="b9e84-202">Deze cmdlet heeft geen **recursieve** para meter, omdat alleen een item wordt opgehaald, niet de inhoud ervan.</span><span class="sxs-lookup"><span data-stu-id="b9e84-202">This cmdlet does not have a **Recurse** parameter, because it gets only an item, not its contents.</span></span>
<span data-ttu-id="b9e84-203">Als u de inhoud van een item recursief wilt ophalen, gebruikt u `Get-ChildItem` .</span><span class="sxs-lookup"><span data-stu-id="b9e84-203">To get the contents of an item recursively, use `Get-ChildItem`.</span></span>

<span data-ttu-id="b9e84-204">Als u door het REGI ster wilt navigeren, gebruikt u deze cmdlet voor het ophalen van register sleutels en de `Get-ItemProperty` om register waarden en-gegevens op te halen.</span><span class="sxs-lookup"><span data-stu-id="b9e84-204">To navigate through the registry, use this cmdlet to get registry keys and the `Get-ItemProperty` to get registry values and data.</span></span> <span data-ttu-id="b9e84-205">De register waarden worden beschouwd als eigenschappen van de register sleutel.</span><span class="sxs-lookup"><span data-stu-id="b9e84-205">The registry values are considered to be properties of the registry key.</span></span>

<span data-ttu-id="b9e84-206">Deze cmdlet is ontworpen om te werken met de gegevens die door elke provider worden weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="b9e84-206">This cmdlet is designed to work with the data exposed by any provider.</span></span> <span data-ttu-id="b9e84-207">Als u een lijst wilt weer geven van de providers die beschikbaar zijn in uw sessie, typt u `Get-PsProvider` .</span><span class="sxs-lookup"><span data-stu-id="b9e84-207">To list the providers available in your session, type `Get-PsProvider`.</span></span> <span data-ttu-id="b9e84-208">Zie [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="b9e84-208">For more information, see [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md).</span></span>

## <span data-ttu-id="b9e84-209">GERELATEERDE KOPPELINGEN</span><span class="sxs-lookup"><span data-stu-id="b9e84-209">RELATED LINKS</span></span>

[<span data-ttu-id="b9e84-210">Wissen-item</span><span class="sxs-lookup"><span data-stu-id="b9e84-210">Clear-Item</span></span>](Clear-Item.md)

[<span data-ttu-id="b9e84-211">Kopie-item</span><span class="sxs-lookup"><span data-stu-id="b9e84-211">Copy-Item</span></span>](Copy-Item.md)

[<span data-ttu-id="b9e84-212">Invoke-item</span><span class="sxs-lookup"><span data-stu-id="b9e84-212">Invoke-Item</span></span>](Invoke-Item.md)

[<span data-ttu-id="b9e84-213">Item verplaatsen</span><span class="sxs-lookup"><span data-stu-id="b9e84-213">Move-Item</span></span>](Move-Item.md)

[<span data-ttu-id="b9e84-214">Nieuw-item</span><span class="sxs-lookup"><span data-stu-id="b9e84-214">New-Item</span></span>](New-Item.md)

[<span data-ttu-id="b9e84-215">Verwijderen-item</span><span class="sxs-lookup"><span data-stu-id="b9e84-215">Remove-Item</span></span>](Remove-Item.md)

[<span data-ttu-id="b9e84-216">Naam wijzigen-item</span><span class="sxs-lookup"><span data-stu-id="b9e84-216">Rename-Item</span></span>](Rename-Item.md)

[<span data-ttu-id="b9e84-217">Set-item</span><span class="sxs-lookup"><span data-stu-id="b9e84-217">Set-Item</span></span>](Set-Item.md)

[<span data-ttu-id="b9e84-218">Get-Child item</span><span class="sxs-lookup"><span data-stu-id="b9e84-218">Get-ChildItem</span></span>](Get-ChildItem.md)

[<span data-ttu-id="b9e84-219">Get-item Property</span><span class="sxs-lookup"><span data-stu-id="b9e84-219">Get-ItemProperty</span></span>](Get-ItemProperty.md)

[<span data-ttu-id="b9e84-220">Get-PSProvider</span><span class="sxs-lookup"><span data-stu-id="b9e84-220">Get-PSProvider</span></span>](Get-PSProvider.md)

[<span data-ttu-id="b9e84-221">about_Providers</span><span class="sxs-lookup"><span data-stu-id="b9e84-221">about_Providers</span></span>](../Microsoft.PowerShell.Core/About/about_Providers.md)
