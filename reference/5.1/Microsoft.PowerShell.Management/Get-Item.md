---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 04/19/2021
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/get-item?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-Item
ms.openlocfilehash: c73031b1e93f4f834e841349069583a0690e071a
ms.sourcegitcommit: 2ad76cd528338f8c2cc10a84c5c56c0e25b93436
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 04/19/2021
ms.locfileid: "107729776"
---
# <span data-ttu-id="0cc9b-102">Get-Item</span><span class="sxs-lookup"><span data-stu-id="0cc9b-102">Get-Item</span></span>

## <span data-ttu-id="0cc9b-103">SAMENVATTING</span><span class="sxs-lookup"><span data-stu-id="0cc9b-103">SYNOPSIS</span></span>
<span data-ttu-id="0cc9b-104">Hiermee haalt u het item op de opgegeven locatie.</span><span class="sxs-lookup"><span data-stu-id="0cc9b-104">Gets the item at the specified location.</span></span>

## <span data-ttu-id="0cc9b-105">SYNTAXIS</span><span class="sxs-lookup"><span data-stu-id="0cc9b-105">SYNTAX</span></span>

### <span data-ttu-id="0cc9b-106">Pad (standaard)</span><span class="sxs-lookup"><span data-stu-id="0cc9b-106">Path (Default)</span></span>

```
Get-Item [-Path] <String[]> [-Filter <String>] [-Include <String[]>] [-Exclude <String[]>] [-Force]
 [-Credential <PSCredential>] [-UseTransaction] [-Stream <String[]>] [<CommonParameters>]
```

### <span data-ttu-id="0cc9b-107">LiteralPath</span><span class="sxs-lookup"><span data-stu-id="0cc9b-107">LiteralPath</span></span>

```
Get-Item -LiteralPath <String[]> [-Filter <String>] [-Include <String[]>] [-Exclude <String[]>] [-Force]
 [-Credential <PSCredential>] [-UseTransaction] [-Stream <String[]>] [<CommonParameters>]
```

## <span data-ttu-id="0cc9b-108">BESCHRIJVING</span><span class="sxs-lookup"><span data-stu-id="0cc9b-108">DESCRIPTION</span></span>

<span data-ttu-id="0cc9b-109">De `Get-Item` cmdlet haalt het item op de opgegeven locatie op.</span><span class="sxs-lookup"><span data-stu-id="0cc9b-109">The `Get-Item` cmdlet gets the item at the specified location.</span></span> <span data-ttu-id="0cc9b-110">De inhoud van het item wordt niet op de locatie opgevraagd, tenzij u een jokerteken ( ) gebruikt om alle inhoud van het `*` item aan te vragen.</span><span class="sxs-lookup"><span data-stu-id="0cc9b-110">It doesn't get the contents of the item at the location unless you use a wildcard character (`*`) to request all the contents of the item.</span></span>

<span data-ttu-id="0cc9b-111">Deze cmdlet wordt gebruikt door PowerShell-providers om door verschillende typen gegevensopslag te navigeren.</span><span class="sxs-lookup"><span data-stu-id="0cc9b-111">This cmdlet is used by PowerShell providers to navigate through different types of data stores.</span></span>

## <span data-ttu-id="0cc9b-112">VOORBEELDEN</span><span class="sxs-lookup"><span data-stu-id="0cc9b-112">EXAMPLES</span></span>

### <span data-ttu-id="0cc9b-113">Voorbeeld 1: De huidige map op te halen</span><span class="sxs-lookup"><span data-stu-id="0cc9b-113">Example 1: Get the current directory</span></span>

<span data-ttu-id="0cc9b-114">In dit voorbeeld wordt de huidige map.</span><span class="sxs-lookup"><span data-stu-id="0cc9b-114">This example gets the current directory.</span></span> <span data-ttu-id="0cc9b-115">De stip ('.') vertegenwoordigt het item op de huidige locatie (niet de inhoud ervan).</span><span class="sxs-lookup"><span data-stu-id="0cc9b-115">The dot ('.') represents the item at the current location (not its contents).</span></span>

```powershell
Get-Item .
```

```output
Directory: C:\

Mode                LastWriteTime     Length Name
----                -------------     ------ ----
d----         7/26/2006  10:01 AM            ps-test
```

### <span data-ttu-id="0cc9b-116">Voorbeeld 2: Alle items in de huidige map op te halen</span><span class="sxs-lookup"><span data-stu-id="0cc9b-116">Example 2: Get all the items in the current directory</span></span>

<span data-ttu-id="0cc9b-117">In dit voorbeeld worden alle items in de huidige map op basis van de lijst met items.</span><span class="sxs-lookup"><span data-stu-id="0cc9b-117">This example gets all the items in the current directory.</span></span> <span data-ttu-id="0cc9b-118">Het jokerteken ( `*` ) vertegenwoordigt alle inhoud van het huidige item.</span><span class="sxs-lookup"><span data-stu-id="0cc9b-118">The wildcard character (`*`) represents all the contents of the current item.</span></span>

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

### <span data-ttu-id="0cc9b-119">Voorbeeld 3: De huidige map van een station op te halen</span><span class="sxs-lookup"><span data-stu-id="0cc9b-119">Example 3: Get the current directory of a drive</span></span>

<span data-ttu-id="0cc9b-120">In dit voorbeeld wordt de huidige map van het `C:` station.</span><span class="sxs-lookup"><span data-stu-id="0cc9b-120">This example gets the current directory of the `C:` drive.</span></span> <span data-ttu-id="0cc9b-121">Het object dat wordt opgehaald, vertegenwoordigt alleen de map, niet de inhoud ervan.</span><span class="sxs-lookup"><span data-stu-id="0cc9b-121">The object that is retrieved represents only the directory, not its contents.</span></span>

```powershell
Get-Item C:
```

### <span data-ttu-id="0cc9b-122">Voorbeeld 4: items in het opgegeven station op te halen</span><span class="sxs-lookup"><span data-stu-id="0cc9b-122">Example 4: Get items in the specified drive</span></span>

<span data-ttu-id="0cc9b-123">In dit voorbeeld worden de items in het `C:` station.</span><span class="sxs-lookup"><span data-stu-id="0cc9b-123">This example gets the items in the `C:` drive.</span></span> <span data-ttu-id="0cc9b-124">Het jokerteken ( `*` ) vertegenwoordigt alle items in de container, niet alleen de container.</span><span class="sxs-lookup"><span data-stu-id="0cc9b-124">The wildcard character (`*`) represents all the items in the container, not just the container.</span></span>

```powershell
Get-Item C:\*
```

<span data-ttu-id="0cc9b-125">Gebruik in PowerShell één sterretje ( ) om inhoud op te halen `*` in plaats van de traditionele `*.*` .</span><span class="sxs-lookup"><span data-stu-id="0cc9b-125">In PowerShell, use a single asterisk (`*`) to get contents, instead of the traditional `*.*`.</span></span> <span data-ttu-id="0cc9b-126">De indeling wordt letterlijk geïnterpreteerd, dus zou geen map `*.*` of bestandsnaam ophalen zonder een punt.</span><span class="sxs-lookup"><span data-stu-id="0cc9b-126">The format is interpreted literally, so `*.*` wouldn't retrieve directories or filenames without a dot.</span></span>

### <span data-ttu-id="0cc9b-127">Voorbeeld 5: een eigenschap in de opgegeven map op te halen</span><span class="sxs-lookup"><span data-stu-id="0cc9b-127">Example 5: Get a property in the specified directory</span></span>

<span data-ttu-id="0cc9b-128">In dit voorbeeld wordt de **eigenschap LastAccessTime** van de `C:\Windows` map .</span><span class="sxs-lookup"><span data-stu-id="0cc9b-128">This example gets the **LastAccessTime** property of the `C:\Windows` directory.</span></span> <span data-ttu-id="0cc9b-129">**LastAccessTime** is slechts één eigenschap van bestandssysteemdirecties.</span><span class="sxs-lookup"><span data-stu-id="0cc9b-129">**LastAccessTime** is just one property of file system directories.</span></span> <span data-ttu-id="0cc9b-130">Als u alle eigenschappen van een map wilt zien, typt u `(Get-Item <directory-name>) | Get-Member` .</span><span class="sxs-lookup"><span data-stu-id="0cc9b-130">To see all the properties of a directory, type `(Get-Item <directory-name>) | Get-Member`.</span></span>

```powershell
(Get-Item C:\Windows).LastAccessTime
```

### <span data-ttu-id="0cc9b-131">Voorbeeld 6: De inhoud van een registersleutel weergeven</span><span class="sxs-lookup"><span data-stu-id="0cc9b-131">Example 6: Show the contents of a registry key</span></span>

<span data-ttu-id="0cc9b-132">In dit voorbeeld ziet u de inhoud van de **registersleutel Microsoft.PowerShell.**</span><span class="sxs-lookup"><span data-stu-id="0cc9b-132">This example shows the contents of the **Microsoft.PowerShell** registry key.</span></span> <span data-ttu-id="0cc9b-133">U kunt deze cmdlet gebruiken met de PowerShell Registry-provider om registersleutels en subsleutels op te halen, maar u moet de cmdlet gebruiken om de registerwaarden en -gegevens `Get-ItemProperty` op te halen.</span><span class="sxs-lookup"><span data-stu-id="0cc9b-133">You can use this cmdlet with the PowerShell Registry provider to get registry keys and subkeys, but you must use the `Get-ItemProperty` cmdlet to get the registry values and data.</span></span>

```powershell
Get-Item HKLM:\Software\Microsoft\Powershell\1\Shellids\Microsoft.Powershell\
```

### <span data-ttu-id="0cc9b-134">Voorbeeld 7: Items in een map met een uitsluiting op halen</span><span class="sxs-lookup"><span data-stu-id="0cc9b-134">Example 7: Get items in a directory that have an exclusion</span></span>

<span data-ttu-id="0cc9b-135">In dit voorbeeld worden items in de Windows-map met namen met een punt ( `.` ) , maar niet beginnen met `w*` . Dit voorbeeld werkt alleen wanneer het pad een jokerteken ( ) bevat om de inhoud van het `*` item op te geven.</span><span class="sxs-lookup"><span data-stu-id="0cc9b-135">This example gets items in the Windows directory with names that include a dot (`.`), but don't begin with `w*`.This example works only when the path includes a wildcard character (`*`) to specify the contents of the item.</span></span>

```powershell
Get-Item C:\Windows\*.* -Exclude "w*"
```

## <span data-ttu-id="0cc9b-136">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="0cc9b-136">PARAMETERS</span></span>

### <span data-ttu-id="0cc9b-137">-Stream</span><span class="sxs-lookup"><span data-stu-id="0cc9b-137">-Stream</span></span>

<span data-ttu-id="0cc9b-138">Hiermee haalt u de opgegeven alternatieve NTFS-bestandsstroom van het bestand.</span><span class="sxs-lookup"><span data-stu-id="0cc9b-138">Gets the specified alternate NTFS file stream from the file.</span></span> <span data-ttu-id="0cc9b-139">Voer de naam van de stream in.</span><span class="sxs-lookup"><span data-stu-id="0cc9b-139">Enter the stream name.</span></span> <span data-ttu-id="0cc9b-140">Jokertekens worden ondersteund.</span><span class="sxs-lookup"><span data-stu-id="0cc9b-140">Wildcards are supported.</span></span> <span data-ttu-id="0cc9b-141">Als u alle streams wilt op halen, gebruikt u een sterretje ( `*` ).</span><span class="sxs-lookup"><span data-stu-id="0cc9b-141">To get all streams, use an asterisk (`*`).</span></span> <span data-ttu-id="0cc9b-142">Deze parameter is niet geldig voor mappen.</span><span class="sxs-lookup"><span data-stu-id="0cc9b-142">This parameter isn't valid on folders.</span></span>

<span data-ttu-id="0cc9b-143">**Stream** is een dynamische parameter die de **filesystem-provider** toevoegt aan de `Get-Item` cmdlet.</span><span class="sxs-lookup"><span data-stu-id="0cc9b-143">**Stream** is a dynamic parameter that the **FileSystem** provider adds to the `Get-Item` cmdlet.</span></span>
<span data-ttu-id="0cc9b-144">Deze parameter werkt alleen in bestandssysteemstations.</span><span class="sxs-lookup"><span data-stu-id="0cc9b-144">This parameter works only in file system drives.</span></span>

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

### <span data-ttu-id="0cc9b-145">-Credential</span><span class="sxs-lookup"><span data-stu-id="0cc9b-145">-Credential</span></span>

> [!NOTE]
> <span data-ttu-id="0cc9b-146">Deze parameter wordt niet ondersteund door providers die zijn geïnstalleerd met PowerShell.</span><span class="sxs-lookup"><span data-stu-id="0cc9b-146">This parameter isn't supported by any providers installed with PowerShell.</span></span>
> <span data-ttu-id="0cc9b-147">Als u een andere gebruiker wilt imiteren of uw referenties wilt verhogen bij het uitvoeren van deze cmdlet, gebruikt [u Invoke-Command](../Microsoft.PowerShell.Core/Invoke-Command.md).</span><span class="sxs-lookup"><span data-stu-id="0cc9b-147">To impersonate another user, or elevate your credentials when running this cmdlet, use [Invoke-Command](../Microsoft.PowerShell.Core/Invoke-Command.md).</span></span>

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

### <span data-ttu-id="0cc9b-148">-Uitsluiten</span><span class="sxs-lookup"><span data-stu-id="0cc9b-148">-Exclude</span></span>

<span data-ttu-id="0cc9b-149">Hiermee geeft u als een tekenreeksmatrix een item of items op die door deze cmdlet worden uitgesloten in de bewerking.</span><span class="sxs-lookup"><span data-stu-id="0cc9b-149">Specifies, as a string array, an item or items that this cmdlet excludes in the operation.</span></span> <span data-ttu-id="0cc9b-150">De waarde van deze parameter komt in aanmerking voor de **parameter Path.**</span><span class="sxs-lookup"><span data-stu-id="0cc9b-150">The value of this parameter qualifies the **Path** parameter.</span></span> <span data-ttu-id="0cc9b-151">Voer een padelement of -patroon in, zoals `*.txt` .</span><span class="sxs-lookup"><span data-stu-id="0cc9b-151">Enter a path element or pattern, such as `*.txt`.</span></span> <span data-ttu-id="0cc9b-152">Jokertekens zijn toegestaan.</span><span class="sxs-lookup"><span data-stu-id="0cc9b-152">Wildcard characters are permitted.</span></span> <span data-ttu-id="0cc9b-153">De **uitsluiten** parameter is alleen van kracht wanneer de opdracht bevat de inhoud van een item, zoals , waarbij het jokerteken geeft de `C:\Windows\*` inhoud van de `C:\Windows` map.</span><span class="sxs-lookup"><span data-stu-id="0cc9b-153">The **Exclude** parameter is effective only when the command includes the contents of an item, such as `C:\Windows\*`, where the wildcard character specifies the contents of the `C:\Windows` directory.</span></span>

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

### <span data-ttu-id="0cc9b-154">-Filter</span><span class="sxs-lookup"><span data-stu-id="0cc9b-154">-Filter</span></span>

<span data-ttu-id="0cc9b-155">Hiermee geeft u een filter op om de **padparameter te kwalificeren.**</span><span class="sxs-lookup"><span data-stu-id="0cc9b-155">Specifies a filter to qualify the **Path** parameter.</span></span> <span data-ttu-id="0cc9b-156">De [FileSystem-provider](../Microsoft.PowerShell.Core/About/about_FileSystem_Provider.md) is de enige geïnstalleerde PowerShell-provider die filters ondersteunt.</span><span class="sxs-lookup"><span data-stu-id="0cc9b-156">The [FileSystem](../Microsoft.PowerShell.Core/About/about_FileSystem_Provider.md) provider is the only installed PowerShell provider that supports filters.</span></span> <span data-ttu-id="0cc9b-157">Filters zijn efficiënter dan andere parameters.</span><span class="sxs-lookup"><span data-stu-id="0cc9b-157">Filters are more efficient than other parameters.</span></span> <span data-ttu-id="0cc9b-158">De provider past een filter toe wanneer de cmdlet de objecten op haalt, in plaats van dat PowerShell de objecten filtert nadat ze zijn opgehaald.</span><span class="sxs-lookup"><span data-stu-id="0cc9b-158">The provider applies filter when the cmdlet gets the objects rather than having PowerShell filter the objects after they're retrieved.</span></span> <span data-ttu-id="0cc9b-159">De filterreeks wordt doorgegeven aan de .NET API om bestanden op te semuleren.</span><span class="sxs-lookup"><span data-stu-id="0cc9b-159">The filter string is passed to the .NET API to enumerate files.</span></span> <span data-ttu-id="0cc9b-160">De API ondersteunt alleen `*` `?` jokertekens en .</span><span class="sxs-lookup"><span data-stu-id="0cc9b-160">The API only supports `*` and `?` wildcards.</span></span>

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

### <span data-ttu-id="0cc9b-161">-Force</span><span class="sxs-lookup"><span data-stu-id="0cc9b-161">-Force</span></span>

<span data-ttu-id="0cc9b-162">Geeft aan dat met deze cmdlet items worden opgeslagen die anders niet toegankelijk zijn, zoals verborgen items.</span><span class="sxs-lookup"><span data-stu-id="0cc9b-162">Indicates that this cmdlet gets items that can't otherwise be accessed, such as hidden items.</span></span>
<span data-ttu-id="0cc9b-163">Implementatie varieert per provider.</span><span class="sxs-lookup"><span data-stu-id="0cc9b-163">Implementation varies from provider to provider.</span></span> <span data-ttu-id="0cc9b-164">Zie voor meer informatie [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md).</span><span class="sxs-lookup"><span data-stu-id="0cc9b-164">For more information, see [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md).</span></span> <span data-ttu-id="0cc9b-165">Zelfs met **de** parameter Force kan de cmdlet geen beveiligingsbeperkingen overschrijven.</span><span class="sxs-lookup"><span data-stu-id="0cc9b-165">Even using the **Force** parameter, the cmdlet can't override security restrictions.</span></span>

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

### <span data-ttu-id="0cc9b-166">-Include</span><span class="sxs-lookup"><span data-stu-id="0cc9b-166">-Include</span></span>

<span data-ttu-id="0cc9b-167">Hiermee geeft u als tekenreeksmatrix een item of items op die deze cmdlet in de bewerking op bevat.</span><span class="sxs-lookup"><span data-stu-id="0cc9b-167">Specifies, as a string array, an item or items that this cmdlet includes in the operation.</span></span> <span data-ttu-id="0cc9b-168">De waarde van deze parameter komt in aanmerking voor de **parameter Path.**</span><span class="sxs-lookup"><span data-stu-id="0cc9b-168">The value of this parameter qualifies the **Path** parameter.</span></span> <span data-ttu-id="0cc9b-169">Voer een padelement of -patroon in, zoals `*.txt` .</span><span class="sxs-lookup"><span data-stu-id="0cc9b-169">Enter a path element or pattern, such as `*.txt`.</span></span> <span data-ttu-id="0cc9b-170">Jokertekens zijn toegestaan.</span><span class="sxs-lookup"><span data-stu-id="0cc9b-170">Wildcard characters are permitted.</span></span> <span data-ttu-id="0cc9b-171">De **parameter Include** is alleen van kracht wanneer de opdracht de inhoud van een item bevat, zoals , waarbij het jokerteken de inhoud van de map `C:\Windows\*` `C:\Windows` aangeeft.</span><span class="sxs-lookup"><span data-stu-id="0cc9b-171">The **Include** parameter is effective only when the command includes the contents of an item, such as `C:\Windows\*`, where the wildcard character specifies the contents of the `C:\Windows` directory.</span></span>

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

### <span data-ttu-id="0cc9b-172">-LiteralPath</span><span class="sxs-lookup"><span data-stu-id="0cc9b-172">-LiteralPath</span></span>

<span data-ttu-id="0cc9b-173">Hiermee geeft u een pad naar een of meer locaties.</span><span class="sxs-lookup"><span data-stu-id="0cc9b-173">Specifies a path to one or more locations.</span></span> <span data-ttu-id="0cc9b-174">De waarde **van LiteralPath** wordt precies gebruikt zoals deze is getypt.</span><span class="sxs-lookup"><span data-stu-id="0cc9b-174">The value of **LiteralPath** is used exactly as it's typed.</span></span> <span data-ttu-id="0cc9b-175">Er worden geen tekens geïnterpreteerd als jokertekens.</span><span class="sxs-lookup"><span data-stu-id="0cc9b-175">No characters are interpreted as wildcards.</span></span> <span data-ttu-id="0cc9b-176">Als het pad escape-tekens bevat, sluit u het tussen enkele aanhalingstekens.</span><span class="sxs-lookup"><span data-stu-id="0cc9b-176">If the path includes escape characters, enclose it in single quotation marks.</span></span> <span data-ttu-id="0cc9b-177">Enkele aanhalingstekens geven aan PowerShell door dat er geen tekens als escapereeksen moeten worden geïnterpreteerd.</span><span class="sxs-lookup"><span data-stu-id="0cc9b-177">Single quotation marks tell PowerShell not to interpret any characters as escape sequences.</span></span>

<span data-ttu-id="0cc9b-178">Zie voor meer informatie [about_Quoting_Rules](../Microsoft.Powershell.Core/About/about_Quoting_Rules.md).</span><span class="sxs-lookup"><span data-stu-id="0cc9b-178">For more information, see [about_Quoting_Rules](../Microsoft.Powershell.Core/About/about_Quoting_Rules.md).</span></span>

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

### <span data-ttu-id="0cc9b-179">-Path</span><span class="sxs-lookup"><span data-stu-id="0cc9b-179">-Path</span></span>

<span data-ttu-id="0cc9b-180">Hiermee geeft u het pad naar een item.</span><span class="sxs-lookup"><span data-stu-id="0cc9b-180">Specifies the path to an item.</span></span> <span data-ttu-id="0cc9b-181">Met deze cmdlet wordt het item op de opgegeven locatie opgeslagen.</span><span class="sxs-lookup"><span data-stu-id="0cc9b-181">This cmdlet gets the item at the specified location.</span></span> <span data-ttu-id="0cc9b-182">Jokertekens zijn toegestaan.</span><span class="sxs-lookup"><span data-stu-id="0cc9b-182">Wildcard characters are permitted.</span></span> <span data-ttu-id="0cc9b-183">Deze parameter is vereist, maar de parameternaam **Pad** is optioneel.</span><span class="sxs-lookup"><span data-stu-id="0cc9b-183">This parameter is required, but the parameter name **Path** is optional.</span></span>

<span data-ttu-id="0cc9b-184">Gebruik een punt ( `.` ) om de huidige locatie op te geven.</span><span class="sxs-lookup"><span data-stu-id="0cc9b-184">Use a dot (`.`) to specify the current location.</span></span> <span data-ttu-id="0cc9b-185">Gebruik het jokerteken ( `*` ) om alle items op de huidige locatie op te geven.</span><span class="sxs-lookup"><span data-stu-id="0cc9b-185">Use the wildcard character (`*`) to specify all the items in the current location.</span></span>

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

### <span data-ttu-id="0cc9b-186">-UseTransaction</span><span class="sxs-lookup"><span data-stu-id="0cc9b-186">-UseTransaction</span></span>

<span data-ttu-id="0cc9b-187">Hiermee wordt de opdracht opgenomen in de actieve transactie.</span><span class="sxs-lookup"><span data-stu-id="0cc9b-187">Includes the command in the active transaction.</span></span> <span data-ttu-id="0cc9b-188">Deze parameter is alleen geldig wanneer een transactie wordt uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="0cc9b-188">This parameter is valid only when a transaction is in progress.</span></span> <span data-ttu-id="0cc9b-189">Zie voor meer informatie [about_Transactions.](../Microsoft.PowerShell.Core/About/about_Transactions.md)</span><span class="sxs-lookup"><span data-stu-id="0cc9b-189">For more information, see [about_Transactions](../Microsoft.PowerShell.Core/About/about_Transactions.md).</span></span>

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

### <span data-ttu-id="0cc9b-190">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="0cc9b-190">CommonParameters</span></span>

<span data-ttu-id="0cc9b-191">Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="0cc9b-191">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="0cc9b-192">Zie voor meer informatie [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="0cc9b-192">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="0cc9b-193">INVOER</span><span class="sxs-lookup"><span data-stu-id="0cc9b-193">INPUTS</span></span>

### <span data-ttu-id="0cc9b-194">System.String</span><span class="sxs-lookup"><span data-stu-id="0cc9b-194">System.String</span></span>

<span data-ttu-id="0cc9b-195">U kunt een tekenreeks met een pad naar deze cmdlet doorspijpen.</span><span class="sxs-lookup"><span data-stu-id="0cc9b-195">You can pipe a string that contains a path to this cmdlet.</span></span>

## <span data-ttu-id="0cc9b-196">UITVOER</span><span class="sxs-lookup"><span data-stu-id="0cc9b-196">OUTPUTS</span></span>

### <span data-ttu-id="0cc9b-197">System.Object</span><span class="sxs-lookup"><span data-stu-id="0cc9b-197">System.Object</span></span>

<span data-ttu-id="0cc9b-198">Deze cmdlet retourneert de objecten die deze krijgt.</span><span class="sxs-lookup"><span data-stu-id="0cc9b-198">This cmdlet returns the objects that it gets.</span></span> <span data-ttu-id="0cc9b-199">Het type wordt bepaald door het type objecten in het pad.</span><span class="sxs-lookup"><span data-stu-id="0cc9b-199">The type is determined by the type of objects in the path.</span></span>

## <span data-ttu-id="0cc9b-200">OPMERKINGEN</span><span class="sxs-lookup"><span data-stu-id="0cc9b-200">NOTES</span></span>

<span data-ttu-id="0cc9b-201">Deze cmdlet heeft geen **Recurse-parameter,** omdat deze alleen een item krijgt, niet de inhoud ervan.</span><span class="sxs-lookup"><span data-stu-id="0cc9b-201">This cmdlet does not have a **Recurse** parameter, because it gets only an item, not its contents.</span></span>
<span data-ttu-id="0cc9b-202">Gebruik om de inhoud van een item recursief op te `Get-ChildItem` halen.</span><span class="sxs-lookup"><span data-stu-id="0cc9b-202">To get the contents of an item recursively, use `Get-ChildItem`.</span></span>

<span data-ttu-id="0cc9b-203">Als u door het register wilt navigeren, gebruikt u deze cmdlet om registersleutels op te halen en de om `Get-ItemProperty` registerwaarden en -gegevens op te halen.</span><span class="sxs-lookup"><span data-stu-id="0cc9b-203">To navigate through the registry, use this cmdlet to get registry keys and the `Get-ItemProperty` to get registry values and data.</span></span> <span data-ttu-id="0cc9b-204">De registerwaarden worden beschouwd als eigenschappen van de registersleutel.</span><span class="sxs-lookup"><span data-stu-id="0cc9b-204">The registry values are considered to be properties of the registry key.</span></span>

<span data-ttu-id="0cc9b-205">Deze cmdlet is ontworpen om te werken met de gegevens die beschikbaar worden gemaakt door elke provider.</span><span class="sxs-lookup"><span data-stu-id="0cc9b-205">This cmdlet is designed to work with the data exposed by any provider.</span></span> <span data-ttu-id="0cc9b-206">Typ om de providers weer te geven die beschikbaar zijn in uw `Get-PsProvider` sessie.</span><span class="sxs-lookup"><span data-stu-id="0cc9b-206">To list the providers available in your session, type `Get-PsProvider`.</span></span> <span data-ttu-id="0cc9b-207">Zie voor meer informatie [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md).</span><span class="sxs-lookup"><span data-stu-id="0cc9b-207">For more information, see [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md).</span></span>

## <span data-ttu-id="0cc9b-208">GERELATEERDE KOPPELINGEN</span><span class="sxs-lookup"><span data-stu-id="0cc9b-208">RELATED LINKS</span></span>

[<span data-ttu-id="0cc9b-209">Clear-Item</span><span class="sxs-lookup"><span data-stu-id="0cc9b-209">Clear-Item</span></span>](Clear-Item.md)

[<span data-ttu-id="0cc9b-210">Copy-Item</span><span class="sxs-lookup"><span data-stu-id="0cc9b-210">Copy-Item</span></span>](Copy-Item.md)

[<span data-ttu-id="0cc9b-211">Invoke-Item</span><span class="sxs-lookup"><span data-stu-id="0cc9b-211">Invoke-Item</span></span>](Invoke-Item.md)

[<span data-ttu-id="0cc9b-212">Item verplaatsen</span><span class="sxs-lookup"><span data-stu-id="0cc9b-212">Move-Item</span></span>](Move-Item.md)

[<span data-ttu-id="0cc9b-213">Nieuw item</span><span class="sxs-lookup"><span data-stu-id="0cc9b-213">New-Item</span></span>](New-Item.md)

[<span data-ttu-id="0cc9b-214">Item verwijderen</span><span class="sxs-lookup"><span data-stu-id="0cc9b-214">Remove-Item</span></span>](Remove-Item.md)

[<span data-ttu-id="0cc9b-215">Rename-Item</span><span class="sxs-lookup"><span data-stu-id="0cc9b-215">Rename-Item</span></span>](Rename-Item.md)

[<span data-ttu-id="0cc9b-216">Set-Item</span><span class="sxs-lookup"><span data-stu-id="0cc9b-216">Set-Item</span></span>](Set-Item.md)

[<span data-ttu-id="0cc9b-217">Get-ChildItem</span><span class="sxs-lookup"><span data-stu-id="0cc9b-217">Get-ChildItem</span></span>](Get-ChildItem.md)

[<span data-ttu-id="0cc9b-218">Get-ItemProperty</span><span class="sxs-lookup"><span data-stu-id="0cc9b-218">Get-ItemProperty</span></span>](Get-ItemProperty.md)

[<span data-ttu-id="0cc9b-219">Get-PSProvider</span><span class="sxs-lookup"><span data-stu-id="0cc9b-219">Get-PSProvider</span></span>](Get-PSProvider.md)

[<span data-ttu-id="0cc9b-220">about_Providers</span><span class="sxs-lookup"><span data-stu-id="0cc9b-220">about_Providers</span></span>](../Microsoft.PowerShell.Core/About/about_Providers.md)
